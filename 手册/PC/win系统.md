## 配件

### [蓝牙耳机密码一般是多少](https://zhidao.baidu.com/question/1699862006096294508.html)

一般是：0000、1234、1111、8888，可根据蓝牙说明书上指示的PIN密码连接。

## 故障

### [电脑插耳机显示未连接](https://zhidao.baidu.com/question/1438846100763617259/answer/3774885728)

从控制面板中查找并打开`Realtek高清晰音频管理器`，勾选`禁用前面板插孔检测`

### [快速访问无法取消固定](https://blog.csdn.net/chenqiyuan_0707/article/details/123611256)

1. `Win+R`打开以下路径:
```
%APPDATA%\Microsoft\Windows\Recent\AutomaticDestinations
```
2. 删除或者重命名文件`f01b4d95cf55d32a.automaticDestinations-ms`

### [WINDOW 活动窗口不能显示到最前端](https://blog.csdn.net/a_small_mouse/article/details/48752765)

1. 打开注册表，找到`HKEY_CURRENT_USER\Control Panel\Desktop`
2. `Foreground Flash Count`的key恢复到默认值3
3. `Foreground Lock timeout`的key恢复到默认值200000
4. 重启应用程序或操作系统


---

## 账户

### [无法更改为本地账户](https://jingyan.baidu.com/article/ed2a5d1f381fd848f7be172b.html)

1. 运行`Regedit`，打开注册表编辑器

2. 展开`HKEY_LOCAL_MACHINE`选项，展开`SAM`选项，右键点击`选择权限`

3. 点击`Administrators`，权限勾选`完全控制`

4. F5刷新，本来为空的SAM下面出现了节点,定位到`Domains/Account/Users/Names/Administrator`，根据实际的值定位到User中的`000001F4`文件夹

5. 删除下图中的五个项，然后重启电脑

![](https://exp-picture.cdn.bcebos.com/de9bfa3b3b8602212722a9e0d8bbf82065fb72cf.jpg)

6. 登录名还是微软账户的名字，还是用之前的密码登录

7. 右键点击【此电脑】管理，然后找到【用户和组】-【用户】，找到Administrator，把全名去掉，然后应用。

8. 右键点击Administrator账户，设置新的密码，该账户就是本地账户了
---

## 运行

### 设置开机自启动

1. win+R输入`shell:startup`
2. 将快捷方式放入启动文件夹中

## 设置

### [开启剪贴板历史纪录](https://jingyan.baidu.com/article/59703552d7e094cec107401a.html)

1. 进入【开始】-【设置】-【系统】-【剪贴板】

2. 打开【剪贴板历史记录】

3. 按`win+V`快捷键

---

[开启SSH](https://zhuanlan.zhihu.com/p/391373172)

1. 设置 - 更新和安全 - 开发者选项 ，打开“开发人员模式”
2. 设置 - 应用 -可选功能，确保已经装好OpenSSH服务器，默认安装OpenSSH客户端。
3. cmd命令行中输入`ssh`。

### [开启Telnet](https://blog.51cto.com/yangshaoping/3334091)

1. 控制面板 - 程序和功能 - 打开或者关闭windows功能
2. 勾选Telnet客户端

### [如何设置定时开关机](https://baijiahao.baidu.com/s?id=1774442223573157971&wfr=spider&for=pc)

1. 控制面板 - 计划任务
2. 创建基本任务 - 触发器（开机/关机时间）
3. 开机可选启动程序
4. 关机在启动程序中输入cmd指令（`/s`表示关机，/h`表示休眠，`/f`表示强制关闭未响应的程序，`/t 0`表示立即关机）
```
shutdown /s /f /t 0
```


### [手机无法投屏到电脑](jianshu.com(https://www.jianshu.com/p/15f58e253cf5)

1. 网络 - 属性 - 媒体流式处理选项 - 启用
2. 防火墙：允许应用通过防火墙
3. 更改设置 - 允许其他应用
![更改设置-允许其他应用](https://upload-images.jianshu.io/upload_images/26032240-38f109b3fcc93c9c.png?imageMogr2/auto-orient/strip|imageView2/2/w/1116/format/webp)
4. 任务管理器 - 连接进程 - 右键打开文件所在位置
5. 浏览 - 粘贴路径 - 添加
![RuntimeBroker + PPI Receiver](https://upload-images.jianshu.io/upload_images/26032240-e31896ab6f44995a.png?imageMogr2/auto-orient/strip|imageView2/2/w/779/format/webp)
6. 重启电脑

---

### [国内外常用公共NTP网络时间同步服务器地址](https://blog.csdn.net/weixin_42588262/article/details/82501488)

1. [NTP Pool Project](https://www.ntppool.org/zh/)

一个以时间服务器的大虚拟集群为上百万的客户端提供可靠的、易用的网络时间协议（NTP）服务的项目。

NTP池正在为世界各地成百上千万的系统提供服务，它是绝大多数主流Linux发行版和许多网络设备的默认“时间服务器”。


Internet空间服务器|pool.ntp.org
-|-
洲际空间服务器（亚洲）|asia.pool.ntp.org
国家服务器（中国）|cn.pool.ntp.org

2. 政府 / 组织

[中国科学院国家授时中心](http://www.ntsc.ac.cn/)|ntp.ntsc.ac.cn
-|-
[中国计量科学研究院](https://www.nim.ac.cn/)|ntp1.nim.ac.cn
[中国计量科学研究院](https://www.nim.ac.cn/)|ntp2.nim.ac.cn
[香港天文台](https://www.hko.gov.hk/sc/nts/ntime.htm)|stdtime.gov.hk
香港天文台 - IPv6|time.hko.hk
[澳门地球物理暨气象局](https://www.smg.gov.mo/zh/subpage/224/page/178)|time.smg.gov.mo
[韩国标准科学研究院](https://www.kriss.re.kr/)|time.kriss.re.kr
[日本国立信息通信技术研究所](http://jjy.nict.go.jp/tsp/PubNtp/index.html)|ntp.nict.jp
[日本国立天文台 水沢](http://www.miz.nao.ac.jp/)|s2csntp.miz.nao.ac.jp
[美国国家标准技术研究所](https://www.nist.gov/pml/time-and-frequency-division/services/internet-time-service-its)|time.nist.gov
[印度科学与工业研究理事会](http://www.nplindia.in/)|time.nplindia.org
[菲律宾科学技术部](http://bagong.pagasa.dost.gov.ph/)|ntp.pagasa.dost.gov.ph
[泰国国家电子与计算机技术中心](https://www.nectec.or.th/en/)|clock.nectec.or.th
[泰国皇家海军水文部](http://www.time2.navy.mi.th/)|time.navy.mi.th
[欧洲IP网络资源协调中心](https://labs.ripe.net/author/philip_homburg/ntp-measurements-with-ripe-atlas/)|ntp.atlas.ripe.net

3. 高校

[清华大学](https://tuna.moe/help/ntp/)|ntp.tuna.tsinghua.edu.cn
-|-
[中国科学技术大学](http://hmli.ustc.edu.cn/doc/linux/google-authenticator/)|time.ustc.edu.cn
上海交通大学|ntp.sjtu.edu.cn
[复旦大学](http://www.ecampus.fudan.edu.cn/2266/list.htm)|ntp.fudan.edu.cn
[东北大学](http://ntp.neu.edu.cn/)|ntp.neu.edu.cn
[上海大学](http://www.its.shu.edu.cn/sytplb/jcfw/wlsz.htm)|ntp.shu.edu.cn
[南京大学](https://itsc.nju.edu.cn/21613/listm.htm)|ntp.nju.edu.cn
北京邮电大学|time.bupt.edu.cn
集美大学|time.jmu.edu.cn
[同济大学](http://nic.tongji.edu.cn.https.jxutcmtsg.proxy.jxutcm.edu.cn/sjfw/list.htm)|ntp.tongji.edu.cn
[大连东软信息学院](https://www.neusoft.edu.cn/)|ntp.neusoft.edu.cn
[东京大学](https://www.u-tokyo.ac.jp/)|ntp.nc.u-tokyo.ac.jp
[京都大学](http://www.iimc.kyoto-u.ac.jp/en/services/kuins/kuins/use/ntp.html)|ntp.kuins.kyoto-u.ac.jp
[东北大学（日本）](https://www.tains.tohoku.ac.jp/contents/information/server-info.html)|ntp.tohoku.ac.jp

4. 企业

[阿里巴巴公共系统服务](https://developer.aliyun.com/mirror)|ntp.aliyun.com
-|-
[腾讯](https://cloud.tencent.com/document/product/213/30392)|ntp.tencent.com
微软|time.windows.com
苹果|time.apple.com
苹果（亚洲）|time.asia.apple.com
苹果（欧洲）|time.euro.apple.com
[日本网络交换中心JPNAP运营者](https://www.mfeed.ad.jp/ntp/detail.html)|ntp.jst.mfeed.ad.jp

5. 支持IPv6

Cloudflare|time.cloudflare.com
-|-
[莫斯科网络交换](http://support.ntp.org/bin/view/Servers/PublicTimeServer000766)|ntp.ix.ru
[高通](http://izatcloud.net/)|time.izatcloud.net
[高通](http://www.gpsonextra.net/)|time.gpsonextra.net
[飓风电气](https://www.he.net/adm/ntp.html)|clock.sjc.he.net
飓风电气|clock.fmt.he.net
飓风电气|clock.nyc.he.net

6. 中国大陆无法使用

[谷歌](https://developers.google.com/time)|time.google.com
-|-
[Facebook](https://engineering.fb.com/2020/03/18/production-engineering/ntp-service/)|time.facebook.com
[台湾国家时间与频率标准实验室](https://www.stdtime.gov.tw/)|tick.stdtime.gov.tw
台湾国家时间与频率标准实验室|tock.stdtime.gov.tw
台湾国家时间与频率标准实验室|time.stdtime.gov.tw
台湾国家时间与频率标准实验室|clock.stdtime.gov.tw
台湾国家时间与频率标准实验室|watch.stdtime.gov.tw

---

## 应用商店

### [Windows10 LTSB/LTSC 企业版安装应用商店](https://geekbusy.com/278.html)

1. 打开离线安装包下载的网站：https://store.rg-adguard.net
2. 左侧多选框，选择搜索方式为：`PackageFamilyName`
3. 中间输入应用商店的搜索关键字`Microsoft.WindowsStore_8wekyb3d8bbwe`
4. 右侧✔点击进行搜索操作
6. 以x64为为例，`Ctrl+F`分别搜索`x64__8wekyb3d8bbwe.appx``8wekyb3d8bbwe.appxbundle`
7. 需要下载5个应用程序，前四个下载文件拓展名为`.appx`的，最后一个下载文件拓展名`.appxbundle`的（`appxbundle`的下载最后一个）

![100000000431.png](https://yamaeye.github.io/docs/img/pc/Microsoft.WindowsStore_8wekyb3d8bbwe.jpg)

8. 将下载的5个文件放到一个文件夹中，在文件夹中按住`shift键`，右键选择`在此处打开PowerShell窗口`
9. 在PowerShell中输入`Add-AppxPackage *`进行安装，此操作将自动将4个appx和1个appxbundle进行安装
---

## 共享

### [设置局域网内共享文件夹](https://jingyan.baidu.com/article/48b558e3322cad3e38c09adb.html)

1. 右键点击想分享的文件夹，选择`属性`。

2. 点击顶部的`共享`标签，再点击下方的`共享`按钮。

<img src="https://exp-picture.cdn.bcebos.com/3ac71c214f5793562899d197effb960b302170b9.jpg" alt="共享文件夹" width=400>
3. 输入`everyone`，点击`添加`。

<img src="https://yamaeye.github.io/docs/img/pc/共享用户.png" alt="共享用户" width=500>
4. 权限级别勾选`读取/写入`，再点击下方`共享`。

<img src="https://exp-picture.cdn.bcebos.com/18aebc5f0c14c27b6a94233f2a46b7b1eff939ad.jpg" alt="读取/写入" width=500>
5. 回到文件夹属性的`共享`标签下，复制以`\\`开头的整行`网络路径`，发送给想访问该文件夹的另一台电脑。

<img src="https://exp-picture.cdn.bcebos.com/c255efc595ee41c146c7a6eb8d88912ca4ca9b78.jpg" alt="网络路径" width=400>
6. 继续点击属性窗口下方的`网络和共享中心`。

<img src="https://exp-picture.cdn.bcebos.com/f9617afb960b312185432d14dee983aee9d76db9.jpg" alt="网络和共享中心" width=400>
7. 在`专用`中，勾选`启用网络发现`和`启用文件和打印机共享`

<img src="https://exp-picture.cdn.bcebos.com/04201aa355e983ae6cf5709d68efe078153169b9.jpg" alt="网络和共享中心-专用" width=500>
8. 在`来宾或公用`中，勾选`启用网络发现`和`启用文件和打印机共享`

<img src="https://exp-picture.cdn.bcebos.com/05e24be983aee8d7dc08ca586b781431deb666b9.jpg" alt="网络和共享中心-来宾或公用" width=500>
9. 在`所有网络`中，勾选`启用共享以便…`、`使用128位加密帮助…`以及`无密码保护的共享`，而后点击`保存更改`

<img src="https://exp-picture.cdn.bcebos.com/82eff6d7592ae3ef675a3d8654b6326c566664b9.jpg" alt="网络和共享中心-所有网络" width=500>
10. 在同一局域网下的另一台电脑上，打开`此电脑`窗口，点击上方的`添加一个网络位置`选项。

<img src="https://yamaeye.github.io/docs/img/pc/添加网络位置.png" alt="添加网络位置" width=500>
11. 点击下一步后，在`指定网站的位置`中，粘贴从第5步：共享文件夹复制的`网络路径`，之后继续下一步即可。

[映射网络驱动盘：开机不需输入密码](https://www.cnblogs.com/duanjt/p/5362159.html)

将记事本后缀名修改为`.bat`，保存到启动文件夹：

```
net use z: \\172.23.88.107\wifi系统发布 /user:administrator 123456
```

- `z:`：映射的盘符是z盘
- `\\172.23.88.107\wifi系统发布` ：对方（服务器电脑）的共享路径
- `administrator` ：对方电脑上的某个合法用户；
- `123456` ：对方用户的密码。

### [基于SMB的媒体共享](https://www.bilibili.com/read/cv15349964)

1. 开启Windows文件夹自带的局域网分享功能， `启用或关闭Windows功能`中勾选： `SMB 1.0/CIFS 文件共享支持` 与 `SMB 直通`

2. 打开`网络和共享中心`—`高级共享设置`—`专用`、`所有网络`

<img src="https://yamaeye.github.io/docs/img/pc/专用.jpg" alt="专用" width=500><br/>

<img src="https://yamaeye.github.io/docs/img/pc/所有网络.jpg" alt="所有网络" width=500>
3. 右键文件夹属性，设置分享。

4. 查看本机IP地址。

5. 下载支持SMB局域网共享功能的视频播放器，安卓端：`nPlayer`，IOS端：`zFuse`。

6. 安卓端：选择网络，点击右上角+，选择`SMB/CIFS`，进入配置界面填写主机（第4步的局域网IP），输入用户名与密码，其余都可以空着。

7. IOS端：选择`我的设备`—`SMB`，填写IP、用户名、密码。

---

### [获取移动公网ipv6地址](https://zhuanlan.zhihu.com/p/429408820)

电脑直连光猫的情况下，电脑可以直接获取IPV6地址。

路由器连接光猫的情况下，需要将光猫改为桥接，路由器才可以获取IPV6地址，并且，分配给其他设备的也是公网地址。

1. 登录路由器管理界面。

移动默认的超级账户：

```
用户名：CMCCAdmin
密码： aDm8H%MdA
```

各个品牌路由器获取超级密码方式不一样，根据 `型号+超密获取` 搜索一下。

2. 记录原拨号设置的信息：

```
用户名
密码（可以联系客服电话直接重置密码）
VLAN id
```

<img src="https://pic3.zhimg.com/v2-3b031508d57646d8b7a87db1ba1fde72_r.jpg" alt="原拨号设置" width=500> 

3. 新建wan并保存。

<img src="https://pic3.zhimg.com/v2-66942ff42404274dc697021c9493c47e_r.jpg" alt="新建wan设置" width=500> 

连接模式 | 改为桥接
---------|------------------
dhcp服务器 | 默认开启
VLAN id | 用原拨号连接中的id
LAN端口绑定 | 绑定第一个端口，默认第一个端口为千兆端口
SSID | 一般关闭光猫的无线功能，这里可不选
使能 | 这里钩上之后，需要关闭原拨号连接的这个选项

4. 关闭光猫上的`ipv6防火墙`，才可以ping通和访问ipv6地址。

<img src="https://pic2.zhimg.com/v2-f5c02bc62400c18dce9e0f3cf04356c9_r.jpg" alt="关闭ipv6防火墙" width=500> 

5. 路由器上网方式`PPPoE`，填入用户名和密码。ipv6选择native。

![PPPoE](https://i0.hdslb.com/bfs/article/5b60d475f70142ff10ee731e7ffa726222bdd6f1.png@1256w_1494h_!web-article-pic.webp)

![native](https://i0.hdslb.com/bfs/article/a449f41a954ef508ce8aa35dbbd985a825063332.png@1256w_1304h_!web-article-pic.webp)

6. [验证IPV6地址是否为公网IP。](https://www.test-ipv6.com/)

cmd输入以下两个命令：

```
ipconfig
curl https://6.ipw.cn
```

得到的ipv6地址一致，则证明电脑已经有了公网IPV6地址。

7. 远程控制需要在`系统属性`中勾选`允许远程连接到此计算机`+`仅允许运行使用网络级别身份验证的远程桌面的计算机连接`。

<img src="https://pic2.zhimg.com/v2-d5db06d95b4f7f2f20cc289c25206785_r.jpg" alt="远程标签" width=350> 

在windows自带的远程控制中输入`IPV6地址`即可连接。

8. 文件共享格式：中间用-隔开，地址后要加入`.https://ipv6-literal.net`

```
\\ipv6地址.ipv6-literal.net
\\fe80-6d80-75d6-107e-5723.ipv6-literal.net
```

访问本机的ipv6地址，可以用：

```
\\0--1.ipv6-literal.net
```

来测试本机的ipv6资源
