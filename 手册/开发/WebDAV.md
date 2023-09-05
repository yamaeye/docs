
### [Windows开启服务](https://juejin.cn/post/6939309167974809614)

1. 计算机管理 - 服务和应用程序 - 服务，启动`WebClient`
2. 此电脑 - 映射网络驱动器，文件夹填写服务商地址，比如坚果云https://dav.jianguoyun.com/dav/
3. 弹出登录验证界面，输入API令牌密码

### OneDrive

1. 打开[OneDrive](https://onedrive.live.com/)
2. 复制地址栏中`cid=`后面的`Customer ID`
3. 目录路径为：`https://d.docs.live.net/cid字段/ `
4. 用户名密码即账号密码

### [InfiniCLOUD](https://www.zhihu.com/question/45557170/answer/2982597765)

1. 注册[InfiniCLOUD](https://infini-cloud.net/en/)，推荐码：A8UB9
2. turn on app connection，得到WebDAV地址，保存ID和密码
3. 可能会收到删除账户的邮件，需要定期登录网站

### [Koofr](https://wzfou.com/koofr/)

1. 登录[koofr](https://app.koofr.net/)
2. password下方找到APP password
3. 起名后generate生成密钥
4. 目录路径填写`https://app.koofr.net/dav/`

### [Alist](https://blog.csdn.net/qq_27386899/article/details/127451571)

将网盘及本地硬盘映射到网络端的软件，支持多种存储的目录文件列表程序，支持 web 浏览与 webdav。

1. win10[下载](https://github.com/alist-org/alist/releases)386版本以及[脚本](https://www.aliyundrive.com/s/DHPMhRtKUzY/folder/63e0961eae317bd4d4d945cda69dbb00f9837fb7)，终端输入
```
.\alist.exe server
```
2. 复制首次运行出现的初始密码
3. 默认监听5244端口，打开`http://127.0.0.1:5244`
4. 点击网页下方的管理，用户名为`admin` , 密码为刚才终端中显示的密码，可在个人资料中修改
5. 从[存储](https://alist.nn.ci/zh/guide/drivers/common.html)中选择驱动

### [自建WebDAV服务器](https://www.zhihu.com/question/300348253/answer/2902699017)

1. 控制面板 - 程序和功能 - 启用或关闭Windows功能
2. 在Internet Information Services（IIS）中勾选“IIS管理控制台”、“Windows身份验证”“基本身份验证”、“管理服务”、“WebDAV发布”和“目录浏览”

![IIS](https://pic1.zhimg.com/50/v2-9135a9ca16fece25793cd96931d9a122_720w.jpg?source=1940ef5c)

3. “Windows管理工具”中找到“IIS管理器”并打开
4. 右键网站 - 添加网站
5. 起名，选择物理路径，设置端口号

![webdav网站](https://pic1.zhimg.com/50/v2-e36f1783dc85ff8111f98cfe6794a9ca_720w.jpg?source=1940ef5c)

6. webdav站点 - WebDAV创作规则 - 启用创作规则 - 添加创作规则，全选三项权限
7. webdav站点 - 身份验证 -启用基本身份验证 - 禁用匿名和Windows身份验证
8. webdav站点 - 目录浏览 - 启用
9. 右键webdav站点 - 重新启动
10. 浏览器输入并访问：`http://127.0.0.1:8090/`，可设置内网穿透
11. 可使用WebDAV客户端Raidrive