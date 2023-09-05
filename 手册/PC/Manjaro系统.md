## 分区

### boot

只在启动和内核升级的时候用到，为引导程序预留空间。使用UEFI引导需要至少512M空间，文件系统选`FAT32`，指定为`/boot/efi`。

### 根分区

目录树的顶层，主文件系统挂载和其他文件系统挂靠的地方。所有文件和目录都在根目录 / 下，即使它们实际上存储在其他的物理设备上。根文件系统中的内容必须足以启动、恢复、修复系统。

### usr

相当于win系统下的`Program Files`，根据安装的软件数量，会产生非常明显的增长。至少要有15~20G，建议设置为50G以上，以便存储操作系统和必要的软件包。

### opt

一般用于存放第三方应用程序，对于大多数用户而言，不需要单独设置，除非你确实需要安装一些较大的第三方应用程序。

### home

包含用户定义的配置文件、缓存、应用程序数据和媒体文件。如果你计划存储大量文件和媒体，则需要更大的空间。

### swap

提供的硬盘空间作为虚拟内存使用，通常为交换分区分配两倍内存大小的空间。

### var

包含缓存、一些临时文件以及日志文件，因此读写频繁。将它独立出来可以避免由于大量日志写入造成的磁盘空间耗尽等问题，保留缓存的包也提供了软件包降级的能力，因此非常有用。

会随着新软件的安装、系统的升级而增长，分配8~12G是比较合适的取值，具体取值取决于安装的软件数量。在磁盘空间不足的时候，可以安全地清理这个目录。


## 安装

### [驱动](https://zhuanlan.zhihu.com/p/114296129)

开机界面将drive改成nonfree，系统会自动安装适配NVIDIA驱动。

## 设置

### [镜像源](https://zhuanlan.zhihu.com/p/334808120)

1. 测试国内镜像源的速度
```shell
sudo pacman-mirrors -i -c China -m rank
```
![](https://pic1.zhimg.com/80/v2-76bbdcb3c6369fa2e95c68b980e85984_720w.webp)
2. 选择一个延迟最低的镜像源
3. 更新软件库
```shell
sudo pacman -Syy
```

### 每天更新系统

```shell
sudo pacman -Syu
```

### [设置全局变量](https://www.php.cn/faq/512100.html)

修改`etc/profile`文件，路径之间的分隔符号是`:`，复制文件夹粘贴到：

```
exprot PATH=文件夹路径
```

### [备份快照](https://zhuanlan.zhihu.com/p/346602946)

打开TimeShift，RSYNC为增量备份，记住备份文件存储的位置

### [密码错误锁定](https://blog.csdn.net/qq_37284020/article/details/112206977)

1. 修改文件`/etc/security/faillock.conf `
2. 取消`deny`前的#注释，修改为0
```shell
deny = 0
```

## 软件

### [输入法](https://blog.csdn.net/qq_37284020/article/details/111357358)

1. 打开manjaro hello - application - Extended language support
2. 勾选第一个Fcitx（即小企鹅输入法，可以通过安装引擎支持多种输入法），再点UPDATE SYSTEM
![language support](https://img-blog.csdnimg.cn/20201218130855905.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3Mjg0MDIw,size_16,color_FFFFFF,t_70)

### [WPS](https://blog.csdn.net/aw77520/article/details/130086237)

1. 先安装基础软件
```shell
sudo pacman -S base-devel
```
2. 再安装WPS
```shell
yay -S wps-office-cn wps-office-mui-zh-cn ttf-wps-fonts
```

### VPN

clash Windows版
```shell
yay -S clash-for-windows-bin
```

### [微信](https://blog.51cto.com/u_14415843/2493987)

1. 官方版
```shell
yay -S wechat-uos
```
2. electronic-wechat（已停止维护）
```shell
yay -S eletronic-wechat
```
3. deepinwine-wechat
```shell
yay -S deepin-wine-wechat
```
在跑完之前，替换掉PKGBUILD中WeChatSetup-3.9.0.28.exe的md5sum值为正确值。安装成功后关闭微信设置中的自动更新。

```shell
md5sum /home/用户名/.cache/yay/deepin-wine-wechat/WeChatSetup-3.9.0.28.exe
```

### 浏览器

edge稳定版
```shell
yay -S --noconfirm microsoft-edge-dev-bin
```

### [音乐](https://zhuanlan.zhihu.com/p/428537709)

1. 网易云音乐
```shell
sudo pacman -S netease-cloud-music
```
2. 第三方网易云
```shell
yay -S yesplaymuisic
```

### [OCR](https://www.jianshu.com/p/2d0e7c41ccee)

1. 安装引擎
```shell
sudo pacman -S tesseract-data-chi_sim
```
2. 安装OCRFeeder
```shell
sudo pacman -S ocrfeeder
```
3. 修改引擎语言的 `zh:chi-sim` 改为 `zh:chi_sim`
4. 也可以删除其他所有语言，只保留 `zh:chi_sim,en:eng`
```
af:afr,ar:ara,az:aze,be:bel,bn:ben,bg:bul,ca:cat,cs:cse,zh:chi_sim,chr:chr,da:dan,de:deu,el:ell,en:eng,et:est,eu:eus,fi:fin,fr:fra,gl:glg,he:heb,hi:hin,hr:hrv,hu:hun,id:ind,is:isl,it:ita,ja:jpn,kn:kan,ko:kor,lv:lav,lt:lit,ml:mal,mk:mkd,mt:mlt,ms:msa,nl:nld,no:nor,pl:pol,pt:por,ro:ron,ru:rus,sk:slk,sl:slv,es:spa,sq:sqi,sr:srp,sw:swa,sv:swe,ta:tam,te:tel,tl:tgl,th:tha,tr:tur,uk:ukr,vi:vie
```

### 远程控制

todesk
```shell
yay -S todesk-bin
```

### 包管理

#### [应用商店](https://www.jianshu.com/p/a4d54fc6d288)

1. 可更换软件源
![更换软件源](/img/pc/更换软件源.png)
2. 可开启AUR源
![开启AUR源](/img/pc/开启AUR源.png)

#### pacman

1. 安装软件
```shell
sudo pacman -S [包名]
```
2. 搜索软件，支持模糊搜索
```shell
pamac search [包名]
```
3. 清理缓存和无用的软件库
```shell
pacman -Sc
```

#### yay

AUR助手，有些时候官方仓库没有你想要的软件，就需要通过yay来安装。

```shell
sudo pacman -S yay
```
1. 安装
```shell
yay -S [包名]
```
2. 卸载
```shell
yay -R [包名]
```
3. 搜索
```shell
yay -Ss [关键词]
```

#### paru

可以用一行命令清除系统上所有不需要的包依赖项，安装来自aur的包时可查看对应的PKGBUILD文件。
```shell
sudo pacman -S paru
```

#### AppImage

1. 可以安装`AppImageLauncher`来简化Appimage包的管理
2. 给软件包设置可执行权限，直接打开即可
```shell
chmod u+x [包名].AppImage
```
3. 如果因为缺少依赖而不能运行，可以到命令行的报错信息里找到提示
```shell
./[包名].AppImage
```

#### [debtap](https://zhuanlan.zhihu.com/p/83335242)

1. 安装，一路选未安装即可
```shell
yay -S debtap
```
2. 更新
```shell
sudo debtap -u
```
3. 安装deb包
```shell
sudo debtap [包名].deb
```
4. 提示输入包名，以及license。包名随意，license可以填GPL
5. 安装生成的压缩包
```shell
sudo pacman -U [包名].tar.xz
```

#### rpm

需要安装rpmextract
```shell
sudo pacman -S rpmextract
```

#### [octopi](https://zhuanlan.zhihu.com/p/410715534)

arch版的新立得，支持pacman，以及可选的AUR helper。当需要一次性安装或卸载若干个软件，但对包名模棱两可的时候，octopi完整的终端整合，对排查安装中的错误非常有用。


