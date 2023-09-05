## 快捷键

### 怎样快速删除空行

1. `Ctrl+H`：调出替换界面。
2. `Alt+R`：切换到正则表达式模式
3. 用`\n\n`替换`\n`，全部替换即可。

> 来源：  
> [Visual Studio Code快速删除空行及几个常用快捷键总结](https://www.cnblogs.com/wenzhongxiang/p/10367568.html)

---

## [错误：operation not permitted](https://blog.csdn.net/yunchong_zhao/article/details/108052919)

我是要删除文件夹代码 如果这个文件夹中的 某些文件正在被其他的项目引用着

而且那个项目还是运行中 那么就会报错 不许这样操作

删除之前 先把运行的代码关闭了 再次运行就可以了


---

### VS Code 无法写入文件

提示：operation not permitted

1. 根目录 –> 右键 –> 属性 –> 安全 –> 编辑

2. 选择用户user，选中完全控制，再应用

> 来源：  
> [EOERM: operation not permitted](https://blog.csdn.net/whileqq/article/details/116130784)

---

### [EPERM Operation not permitted](https://stackoverflow.com/questions/60908817/visual-studio-code-eperm-operation-not-permitted/64370599)

#### 方法一
<!-- {docsify-ignore} -->
You should first go your current user "C:\Users\your_user_name" directory.

Then click the "Hidden Items" checkbox.（显示隐藏文件）

After you will see the ".vscode" folder.（找到这个文件夹）

Last thing to do is deleting it and reopen the VS Code.（谨慎删除）


#### 方法二
<!-- {docsify-ignore} -->
Right click the shortcut of VSCode.（右键快捷方式）

Go to properties.（属性）

Compatibility tab.（兼容性）

Check "Run this program as an administrator"（以管理员身份运行）

Restart and re-run your command.

Come back to Stack Overflow and mark an answer as accepted. It's been over a year.


---

### [vscode.dev打开设置同步时出错，没有可用的身份验证提供程序](https://blog.csdn.net/LeoForBest/article/details/125456390)

添加hosts记录：

```
13.107.213.46
 vscode.dev
```
重新打开vscode.dev，登录即可开启同步功能。

