>作者：[老麦](https://laomai.org/48.html)

此方法来自[Hugo官方文档](https://gohugo.io/itools/search)中的[hugofastsearch](https://gist.github.com/cmod/5410eae147e4318164258742dd053993)，是[Github Gist for Fuse.js integration](https://gist.github.com/eddiewebb/735feb48f50f0ddd65ae5606a1cb41ae)的改进版。

由[荒野無燈](https://ttys3.dev/post/hugo-fast-search/)做了一些微调，允许通过点击页面空白处隐藏搜索框，而不是只能按Esc。

##### 1. 添加`index.json`文件到`layouts/_default`

内容为：

```js
{{- $.Scratch.Add "index" slice -}}
{{- range .Site.RegularPages -}}

{{- $.Scratch.Add "index" (dict "title" .Title "tags" .Params.tags "categories" .Params.categories "contents" .Plain "permalink" .Permalink "date" .Date "section" .Section) -}}
{{- end -}}
{{- $.Scratch.Get "index" | jsonify -}}
```
##### 2. `config.toml`增加配置：

```
[outputs]

home = ["HTML", "RSS", "JSON"]
```
##### 3. 在`/static/js/`添加`fastsearch.js`和`fuse.min.js`

`fuse.min.js`官方下载地址：https://github.com/krisk/Fuse/releases 。

`fastsearch.js`内容如下：

```js
var fuse; // holds our search engine
var fuseIndex;
var searchVisible = false; 
var firstRun = true; // allow us to delay loading json data unless search activated
var list = document.getElementById('searchResults'); // targets the <ul>
var first = list.firstChild; // first child of search list
var last = list.lastChild; // last child of search list
var maininput = document.getElementById('searchInput'); // input box for search
var resultsAvailable = false; // Did we get any search results?

// ==========================================
// The main keyboard event listener running the show
//
document.addEventListener('keydown', function(event) {

// CMD-/ to show / hide Search

if (event.altKey && event.which === 191) {// Load json search index if first time invoking search// Means we don't load json unless searches are going to happen; keep user payload small unless neededdoSearch(event)

}

// Allow ESC (27) to close search box

if (event.keyCode == 27) {

if (searchVisible) {document.getElementById("fastSearch").style.visibility = "hidden";document.activeElement.blur();searchVisible = false;

}

}

// DOWN (40) arrow

if (event.keyCode == 40) {

if (searchVisible && resultsAvailable) {console.log("down");event.preventDefault(); // stop window from scrollingif ( document.activeElement == maininput) { first.focus(); } // if the currently focused element is the main input --> focus the first <li>else if ( document.activeElement == last ) { last.focus(); } // if we're at the bottom, stay thereelse { document.activeElement.parentElement.nextSibling.firstElementChild.focus(); } // otherwise select the next search result

}

}

// UP (38) arrow

if (event.keyCode == 38) {

if (searchVisible && resultsAvailable) {event.preventDefault(); // stop window from scrollingif ( document.activeElement == maininput) { maininput.focus(); } // If we're in the input box, do nothingelse if ( document.activeElement == first) { maininput.focus(); } // If we're at the first item, go to input boxelse { document.activeElement.parentElement.previousSibling.firstElementChild.focus(); } // Otherwise, select the search result above the current active one

}

}
});

// ==========================================
// execute search as each character is typed
//
document.getElementById("searchInput").onkeyup = function(e) { 

executeSearch(this.value);
}

document.querySelector("body").onclick = function(e) { 

if (e.target.tagName === 'BODY' || e.target.tagName === 'DIV') {
hideSearch()

}
}

document.querySelector("#search-btn").onclick = function(e) { 

doSearch(e)
}

function doSearch(e) {

e.stopPropagation();

if (firstRun) {
loadSearch() // loads our json data and builds fuse.js search index
firstRun = false // let's never do this again

}

// Toggle visibility of search box

if (!searchVisible) {
showSearch() // search visible

}

else {
hideSearch()
}
}

function hideSearch() {

document.getElementById("fastSearch").style.visibility = "hidden" // hide search box

document.activeElement.blur() // remove focus from search box 

searchVisible = false
}

function showSearch() {

document.getElementById("fastSearch").style.visibility = "visible" // show search box

document.getElementById("searchInput").focus() // put focus in input box so you can just start typing

searchVisible = true
}

// ==========================================
// fetch some json without jquery
//
function fetchJSONFile(path, callback) {

var httpRequest = new XMLHttpRequest();

httpRequest.onreadystatechange = function() {

if (httpRequest.readyState === 4) {if (httpRequest.status === 200) {
var data = JSON.parse(httpRequest.responseText);

if (callback) callback(data);}

}

};

httpRequest.open('GET', path);

httpRequest.send(); 
}

// ==========================================
// load our search index, only executed once
// on first call of search box (CMD-/)
//
function loadSearch() { 

console.log('loadSearch()')

fetchJSONFile('/index.json', function(data){var options = { // fuse.js options; check fuse.js website for detailsshouldSort: true,location: 0,distance: 100,threshold: 0.4,minMatchCharLength: 2,keys: [
'permalink',
'title',
'tags',
'contents'
]

};

// Create the Fuse index

fuseIndex = Fuse.createIndex(options.keys, data)

fuse = new Fuse(data, options, fuseIndex); // build the index from the json file

});
}

// ==========================================
// using the index we loaded on CMD-/, run 
// a search query (for "term") every time a letter is typed
// in the search box
//
function executeSearch(term) {

let results = fuse.search(term); // the actual query being run using fuse.js

let searchitems = ''; // our results bucket

if (results.length === 0) { // no results based on what was typed into the input box

resultsAvailable = false;

searchitems = '';

} else { // build our html

// console.log(results)

permalinks = [];

numLimit = 5;

for (let item in results) { // only show first 5 results
if (item > numLimit) {

break;
}
if (permalinks.includes(results[item].item.permalink)) {

continue;
}

//
 console.log('item: %d, title: %s', item, results[item].item.title)searchitems = searchitems + '<li><a href="' + results[item].item.permalink + '" tabindex="0">' + '<span class="title">' + results[item].item.title + '</span></a></li>';permalinks.push(results[item].item.permalink);

}

resultsAvailable = true;

}

document.getElementById("searchResults").innerHTML = searchitems;

if (results.length > 0) {

first = list.firstChild.firstElementChild; // first result container — used for checking against keyboard up/down location

last = list.lastChild.firstElementChild; // last result container — used for checking against keyboard up/down location

}
}
```

##### 4. 添加搜索框HTML代码到主题。

因为每个主题可能存在差异，所以请根据自己实际的情况做出相应的更改。

1. 1. 可以添加到`baseof`或者`footer`模板；或选择将代码添加到页头的菜单栏后面，就是添加到`/layouts/partials/header.html`：

```HTML
<li class="menu-item">
<a id="search-btn" style="display: inline-block;" href="javascript:void(0);">
<i class="iconfont">
{{ partial "svg/search.svg" }}
</i>
</a>
<div id="fastSearch">
<input id="searchInput" tabindex="0">
<ul id="searchResults">
</ul>
</div>
</li>
```

>li标签是继承主题，i标签是因为调用了图标。

1. 2. 如果主题有专门引用js的模板`/layouts/partials/scripts.html`，就可以在此添加引用：

```HTML
<!-- Fastsearch -->
<script src="/js/fuse.min.js"></script>
<script src="/js/fastsearch.js"></script>
```

2. 比如`terminal`主题内置了额外的`footer`支持，可以通过添加`layouts/partials/extended_footer.html`来对footer增加内容。
3. 如果主题没有额外的支持，也可以复制当前主题目录下的`baseof.html`模板到`layouts/_default/baseof.html`，然后在最后附加内容：

```HTML
<a id="search-btn" style="display: inline-block;" href="javascript:void(0);">
<span class="icon-search">捜索</span>
</a>
<div id="fastSearch">
<input id="searchInput" tabindex="0">
<ul id="searchResults">
</ul>
</div>
<script src="/js/fuse.min.js"></script> <!-- download and copy over fuse.min.js file from fusejs.io -->
<script src="/js/fastsearch.js"></script>
```

##### 5. 添加CSS样式

尽量选择对应的模板来添加样式，比如是在`header`里修改的，就直接选择在`/assets/sass/_partial/_header.scss`添加CSS样式。

比如`terminal`主题内置了额外的header支持，可以通过添加`layouts/partials/extended_header.html`来对`header`增加内容。

如果主题没有模板CSS，就直接在主题的主CSS上添加，通常是`style.css`或`main.css`，这个因情况而异。

如果样式跟当前的主题不是很合，可以自行稍作调整。添加内容如下：

```CSS

#fastSearch {

visibility: hidden;

position: absolute;

right: 10px;

top: 10px;

display: inline-block;

width: 320px;

margin: 0 10px 0 0;

padding: 0;

}

#fastSearch input {

padding: 4px;

width: 100%;

height: 31px;

font-size: 1.6em;

color: #222129;

font-weight: bold;

background-color: #ffa86a;

border-radius: 3px 3px 0px 0px;

border: none;

outline: none;

text-align: left;

display: inline-block;

}

#searchResults li {

list-style: none;

margin-left: 0em;

background-color: #333;

border-bottom: 1px dotted #000;

}

#searchResults li .title {

font-size: 1.1em;

margin: 0;

display: inline-block;

}

#searchResults {

visibility: inherit;

display: inline-block;

width: 320px;

margin: 0;

max-height: calc(100vh - 120px);

overflow: hidden;

}

#searchResults a {

text-decoration: none !important;

padding: 10px;

display: inline-block;

width: 100%;

}

#searchResults a:hover, #searchResults a:focus {

outline: 0;

background-color: #666;

color: #fff;

}

#search-btn {

position: absolute;

top: 10px;

right: 20px;

font-size: 24px;

}

@media (max-width:683px) {

#fastSearch, #search-btn {top: 64px;

}

}
```