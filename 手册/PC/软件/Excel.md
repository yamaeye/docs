
### 公式

#### [Vlookup函数](https://www.zhihu.com/tardis/bd/art/535042769?source_id=1001)

```
=VLOOKUP(lookup_value,table_array,col_index_num,range_lookup)
```

- `lookup_value`：要查找的值，可输入数值、引用或文本字符串
- `table_array`：要查找的区域，可输入类型为“数据表区域”
- `col_index_num`：返回数据在查找区域的第几列数，一般输入正整数
- `range_lookup`：“模糊匹配/精确匹配”，可填TRUE/FALSE（或不填）

```
输入公式：=VLOOKUP(G2,A:C,3,0)
```

- `G2`：要查找的内容  
- `A:C`：查找区域，注意查找区域的首列要包含查找的内容  
- `3`：要返回的结果在查找区域的第3列  
- `0`：精确查找

![](https://pic1.zhimg.com/v2-f9cbe40c53b89875d91aff754e023aa4_r.jpg)

#### [LOOKUP 函数](https://www.feishu.cn/hc/zh-CN/articles/658075027297-lookup-%E5%87%BD%E6%95%B0)

```
=LOOKUP(搜索键值, 搜索范围 | 搜索结果数组, [结果范围])
```

- `搜索键值`: 要在行或列中搜索的值。需要先对原始数据进行升序排列 。
- `搜索范围 | 搜索结果数组`: 选择要搜索的范围。
- `结果范围`（可选）: 返回结果的范围，此范围必须仅为单行或单列。

```
=LOOKUP(A8,A8:B12,B8:B12)、=LOOKUP(A8,A8:A12,B8:B12)、=LOOKUP(A8,A8:B12)
```

![](https://p1-hera.feishucdn.com/tos-cn-i-jbbdkfciu3/3695a92b64c14f829cf97074aa8ef5a4~tplv-jbbdkfciu3-image:0:0.image)

#### [公式参数不自动变化](https://jingyan.baidu.com/article/19020a0a2ea81b139c28424b.html)

在参数的行号和列号前加`$`，如`=$A$2+B1`。

#### [身份证转年龄](https://zhidao.baidu.com/question/464663474577496285.html)

1. 出生日期公式：=--TEXT(MID(选身份证格,7,8),"0-00-00")
2. 生日转年龄公式：=DATEDIF(选生日格子,TODAY(),"y")

### 操作

#### [批量填充序号](https://jingyan.baidu.com/article/f7ff0bfcc7ef1b6f27bb1354.html)

1. 输入起始序号。
2. 选中需要填充的区域，点击`开始 - 行和列 - 填充`。
3. 默认选择列，等差序列，步长值1，点击确定即可。

#### [行转列](https://www.knowbaike.com/excel/3744.html)

1. 复制行内容
2. 选择性粘贴 - 转置

#### [冻结窗格](https://jingyan.baidu.com/article/915fc41485f89310384b2023.html)

1. 点击要设置冻结窗格的单元格。
2. 点击右侧的【开始 - 冻结窗格】按钮。
3. 下拉菜单的第一项会自动冻结至单元格所在的【行与列】。
4. 如果只需要冻结行/列，可选择“冻结至第N行/列”。
