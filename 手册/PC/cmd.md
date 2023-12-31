## 设置

### [激活administrator账户](https://jingyan.baidu.com/article/8065f87f454d97233124989f.html)

```
net user administrator /active:yes
```

### [创建系统账户](https://jingyan.baidu.com/article/76a7e409b6ab26bd3b6e15c7.html)

1. 执行命令：

```
net user abcdef 123456 /add
```

其中 `abcdef` 为用户名，`123456` 为密码

2. 给新建的账号管理员权限：

```
net localgroup administrators abcdef /add
```

### [设置休眠选项](https://jingyan.baidu.com/article/54b6b9c0fc2d0b2d593b4764.html)

1. 右键开始菜单，选择命令提示符（管理员）

2. 输入命令：
```
powercfg /a
```

3. 如果休眠未打开，继续输入命令：
```
powercfg -h on
```

### [查询系统变量](https://blog.csdn.net/Maxiao1204/article/details/122545615)

可以用CMD的`SET`命令查看现有的系统变量，“="前的部分用%括起来即可：


系统变量 | 路径
-|-
%USERPROFILE% | C:\Users\用户名
%SystemRoot% | C:\WINDOWS
%SystemDrive% | C:
%APPDATA% | C:\Users\用户名\AppData\Roaming
%LOCALAPPDATA% | C:\Users\用户名\AppData\Local
%windir% | C:\WINDOWS
%ProgramData% | C:\ProgramData
%ProgramFiles% | C:\Program Files
%ProgramFiles(x86)% | C:\Program Files (x86)

### [查询电脑型号](https://zhidao.baidu.com/question/689570728537300852.html)

方法一：

1. 运行快捷键`Win + R`，输入`dxdiag`后回车。
2. 选择【系统】选项卡，查看型号。

方法二：

1. 运行快捷键`Win + R`，输入`cmd`后回车。
2. 输入`systeminfo`后回车，查看型号。

### [电脑双开微信](https://jingyan.baidu.com/article/eb9f7b6d8eeea1c79264e80c.html)

右键微信查看属性，复制目标地址

![目标地址](https://exp-picture.cdn.bcebos.com/8974c38a59de450783f73ec75e413a8ca708854c.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)

记事本中输入：

start "" 刚刚复制的地址 （复制两行），如：

```
start ""
"E:\WeChat\WeChat.exe"
start ""
"E:\WeChat\WeChat.exe"
```

保存文件并重命名为`双开微信.bat`

![双开微信.bat](https://exp-picture.cdn.bcebos.com/274e9635dd8a59de4ff18eb6b370d5413b8c844c.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)

如果微信已经打开了，需要先关掉，再双击打开这个脚本。

两个微信登录框是重叠在一起的，把上面的登录框挪开就可以看到两个登录框了。

## 文件

### [批量修改文件后缀](https://blog.csdn.net/qq_58956184/article/details/122384496)

1. 在需要批量修改后缀的文件所在文件夹内新建一个文本文档。

2. 在文档内输入：

```
ren *.txt *.xml
```

`.txt`：修改后缀前的文件格式。

`.xml`：修改后缀后的文件格式。

`*`前有一个`空格`。


3. 保存文本文档，并将其后缀改为`.bat`，双击运行该文本文档即可。


### [批量修改文件权限](https://www.cuanjibang.com/zjjc/85204.html)

命令提示符（管理员）：

```
icacls "E:\文件夹路径\*.*" /grant Everyone:(F)
```

F：代表最高权限（完全控制）

用户组：Everyone、SYSTEM等


### [强制删除文件夹](https://baijiahao.baidu.com/s?id=1613359113025994635&wfr=spider&for=pc)

删除文件夹时提示`错误 0x80070091：目录不是空的。`

在同一目录下，新建一个文本文档，更改扩展名为`.bat`，双击运行：

```
rmdir 文件夹名称.\/s
```

### [使用mklink命令给C盘软件搬家](https://baijiahao.baidu.com/s?id=1722716051189739192&wfr=spider&for=pc)

一般软件都会默认安装在C盘，很多软件还会在C盘“用户”等目录中存储大量数据，导致C盘剩余空间越来越少。

要想腾出一部分C盘空间，就需要把不常用程序的安装目录或数据目录迁移到其它盘。直接移动过去肯定不行，因为程序会找不到文件。

想要解决这个问题，就要用到`mklink`（创建符号链接）命令了，命令需要在`cmd`（命令提示符）中使用，需要`管理员权限`。

<img src="https://yamaeye.github.io/docs/img/pc/命令格式.jpg" alt="命令格式" width=500>
当路径中间有空格时，需要将整个路径加引号。

`NTFSLinksView`：查看系统中的符号链接和目录联接。windows很多地方都使用Junction（目录联接），例如“开始菜单”、“我的文档”等。

#### 符号链接

对文件创建符号链接：

```
mklink link target
```

对目录创建符号链接：

```
mklink /d link target
```

当软件访问符号链接时，实际上是在访问该符号链接所指向的文件(夹)。目录符号链接和文件符号链接之间的区别只是一个代表目录，一个代表文件。

假设某软件安装路径为`c:\program files\app`，将原app目录整个移动到`d:\program\`下面，然后在`c:\program files\`下面建立符号链接：

```
mklink /d "c:\program files\app" d:\program\app
```

文件符号链接显示的类型是文件快捷方式，目录符号链接显示的类型是目录快捷方式，符号链接本身不占空间。

符号链接可以在资源管理器中直接删除，或通过rmdir命令删除，不会影响原文件（夹），但del命令则会把目标文件（夹）删除。

符号链接还可以连接远程路径：

```
mklink /D D:\link \\123.123.0.1\D$\target
```

#### 目录联接

```
mklink /j link target
```

目录联接只能应用于目录，不能用于文件。创建目录联接时目标目录可以不存在。

目录联接只能用于本地，不能指向远程目标路径。

##### 区别

###### 1. 符号链接可以指向远程，目录联接只能指向本地

由于符号链接是客户端解析的，所以本地文件系统上的符号链接可以指向远程文件系统。

例如符号链接`c:\MyNetworkShare`可以指向网络上的`\\Server\Share`。

而我们不能创建一个目录联接`c:\MyNetworkShare`指向另一台计算机`\\Server\Share`，因为目录联接的目标必须是本地的。

###### 2. 远程访问时，目录联接在服务器处理，符号链接在客户端处理

假设您在一台`名为A的计算机`上放置一个目录联接`c:\myjunction`和一个目录符号链接`c:\mysymlink`，都指向`c:\target`。

使用A时，您不会发现它们之间有很大的区别。但是，如果您使用的是另一台名为B的计算机，则：

目录联接`\\A\c$\myjunction`将指向`\\A\c$\target`

但是符号链接`\\A\c$\mysymlink`将指向`\\B\c$\target`

默认情况下，系统不支持远程计算机上的符号链接，因此在大多数情况下，第二个示例实际上会导致“找不到文件”或“由于符号链接类型被禁用而无法使用符号链接。”

###### 3. 对剪切操作有不同表现

例如，新建`目录a`，在`目录a`下面新建文件`a.txt`，然后创建一个`目录联接b`指向`目录a`，通过`目录联接b`可以正常访问到文件`a.txt`。

接着将`目录联接b`剪切到其它地方，发现`目录a`和`目录联接b`还在原来的地方，但是打开却发现`a.txt`不见了，被剪切到了`新位置的目录b`中，也就是说**对目录联接的剪切操作会影响原来的文件**。

而符号链接的剪切操作仅仅是针对这个符号链接，并不会影响目标。如果符号链接创建时使用的目标路径是绝对路径，该剪切也不会影响其链接关系。

###### 权限

创建符号链接需要特殊权限，而创建目录联接仅需要访问文件系统。

#### 硬链接

只能对文件创建硬链接，不能应用于目录。

```
mklink /h link target
```

例如在D盘根目录下新建文本“a.txt”，然后输入以下命令创建到“a.txt”的硬链接“b.txt”：

```
mklink /h d:\b.txt d:\a.txt
```

“b.txt”与“a.txt”占用同样大小的空间，但其实硬链接只是给文件创建了另一个访问入口，它们指向的是硬盘中的同一区域，因此无论访问哪个内容都是一样的；

编辑任何一个另一个也会跟着变化；删除其中一个，另外一个不受影响；两个都删除，才是真的删除。

---