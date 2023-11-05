## [安装 Docker Desktop](https://jingyan.baidu.com/article/3aed632e13039231108091fe.html)

1. 打开控制面板，找到“`程序和功能`”，点击“`启用或关闭Windows功能`”。

2. 确保“`Hyper-V`”和“适用于`Linux的Windows子系统`”选中安装

3. 进入系统后打开`任务管理器`，切换到`性能选项卡`中，确保电脑BIOS中`虚拟化：已开启`

![虚拟化](https://exp-picture.cdn.bcebos.com/031231632385e0363240ad5eb8e039723c035a68.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_auto%2Fquality%2Cq_80)

---

### [WIN10家庭版找不到Hyper-V](https://blog.csdn.net/brazor/article/details/123727758)

1. 首先要确定电脑是否支持 `Hyper-V` 功能。

打开 `Windows PowerShell`，输入 `systeminfo` 命令：

可以看到出现了很多处理器的信息，最末尾有个 `Hyper-V 要求`，如果四个全是 “是”，则表示支持 `Hyper-V` 功能。

![Hyper-V 要求](https://img-blog.csdnimg.cn/6e1706ec6be64abe839fd59c07d3c64b.png)

2. 新建一个文本文档，文件名自取，将以下代码复制进文档中，将文档后缀 `.txt` 改成 `.cmd`。

```
pushd "%~dp0"
 
dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
 
for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
 
del hyper-v.txt
 
Dism /online /enable-feature /featurename:Microsoft-Hyper-V-All /LimitAccess /ALL
```

3. `以管理员身份`运行这个文件，等待程序运行结束，重启后生效，之后就可以在 “`启用或关闭Windows功能`” 中看到 `Hyper-V` 选项。

---

### [如何将docker默认的安装位置从C盘改为D盘？](https://www.cnblogs.com/renguanyu/p/15201827.html)

执行命令：

```
mklink /j "C:\ProgramData\Docker" "D:\ProgramData\Docker"
mklink /j "C:\ProgramData\DockerDesktop" "D:\ProgramData\DockerDesktop"
mklink /j "C:\Program Files\Docker" "D:\Program Files\Docker"
mklink /j "C:\Users\xxx\AppData\Local\Docker" "D:\Users\xxx\AppData\Local\Docker"
```

通过mklink创建的快捷方式，点进去看路径还是在c盘，但是实际上并不会占用c盘的存储空间。

如果安装失败，需要清除C盘相关文件。

win10中的`dockerImages`会保存在`C:\Users\xxx\AppData\Local\Docker`

---

### [限制WSL2可访问的硬件资源](https://blog.csdn.net/u014175785/article/details/118184494)

>有时候我们使用WSL2只是作为一个终端窗口使用，并不会使用太多CPU或内存，但由于Linux内核的内存管理机制，它会尽量缓存一些已经读取过的文件页，在很长一段时间内是不会释放的。并且这部分文件页也不会被Windows回收，导致WSL2占用过多内存，而Windows反而没有内存可用的情况。  

1. `Win+R` 输入 `%UserProfile%` 进入用户文件夹，通常是`C:\Users<$username>\`

2. 创建`.wslconfig`文件，输入以下内容：

```
[wsl2]
memory=4GB
processors=5
localhostForwarding=true
```

processors：限制CPU核心数（当前电脑的处理器数量可以通过 `wmic` 指令获取）

memory：可使用的内存总大小（会体现在/proc/meminfo等节点上）

swap：交换空间的总大小（会体现在/proc/meminfo等节点上）

LocalhostForwarding : 允许本地通过 `localhost` 访问wsl，默认就是开启

3. 重启 `lxss manager` (即wsl服务)

```
net stop LxssManager
net start LxssManager
```

---

### [配置镜像服务](https://blog.csdn.net/xiaoliizi/article/details/118438413)

1. 注册一个 `dockerhub` 账号 和 `国内云厂商` 容器服务

账号本身不影响 `Docker Desktop` 启动 ，但是还是建议体验一下容器镜像服务。

容器镜像管理的方式类似`git代码`，可以把自己后续学习其他技术的过程中 ，搭建好的镜像提交到云端，做备份用。也方便共享。

下面几个镜像服务提供商，个人版本都是免费的。不过主推还是国内的镜像服务，传输速度快一点。

[阿里云镜像服务](https://www.aliyun.com/product/acr)

[腾讯云镜像服务](https://cloud.tencent.com/document/product/1141)

[dockerhub](https://hub.docker.com/)

2. 配置镜像加速器

以[阿里云](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)为例，免费开通账号，获取自己专属的加速器地址

3. 修改`config.json` 文件中的字段：`RegistryMirror`

一般在`docker`的安装目录下，可以用`everything`搜索一下，将镜像源配置进去。

![RegistryMirror](https://mpt.135editor.com/mmbiz_png/sCibEfmAGicvhC5iaNUeDdjCjibpeAmV49KBw7Cktpxib2DKhtvlZu5pMjENXyul3IaTc7vLuNwBk3x8pDQX52pz98g/640?wx_fmt=png)

3. 配置代理

如果你使用的镜像服务是国内的，那么提交、下载镜像的时候又不应该走代理，所以需要在代理上额外配置一下：

如：使用阿里云镜像的代理配置

```
localhost,127.0.0.1,*.aliyuncs.com
```

![阿里云镜像的代理配置](https://img-blog.csdnimg.cn/20210703230104617.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW9saWl6aQ==,size_16,color_FFFFFF,t_70)

---

### [拉取镜像](https://mp.weixin.qq.com/s/bmvELL89wtOqJuZjyv6bJw)

1. 查询镜像

查看当前`centos镜像`有哪些：

```
dockersearch centos
```

仅搜索星级大于3的镜像：

```
docker search--automated -s 3 centos
```

2. 拉取镜像

拉取最新`的centos镜像`：

```
docker pull centos
```

3. 取别名

从最基本的镜像到最后真正部署完成的镜像需要经过很多步骤，这里我们可以给镜像取一个V1别名：

```
docker tagcentos mycentos_V1_init
```

4. 查看镜像列表

```
dockerimages
```

---

### 上传镜像

1. 在[阿里云](https://cr.console.aliyun.com/cn-hangzhou/instances/repositories)申请仓库
 
2. 在docker上登录镜像服务器

```
docker login--username=登录阿里云的邮箱账号 registry.cn-hangzhou.aliyuncs.com
```

3. 给镜像取别名

```
docker tag [ImageId] registry.cn-hangzhou.aliyuncs.com/你自己的镜像仓库地址:mycentos_V5_SSH
```

4. 推送镜像后，在仓库---> 镜像版本即可查看自己的镜像

```
docker push registry.cn-hangzhou.aliyuncs.com/你自己的镜像仓库地址:mycentos_V3_SSH
```

5. 获取镜像

```
docker pull registry.cn-hangzhou.aliyuncs.com/你自己的镜像仓库地址:mycentos_V3_SSH
```

### 




## 配置容器参数

@[乐意李](https://mp.weixin.qq.com/s?__biz=MzkzMjE3MzMzNw==&mid=2247484705&idx=1&sn=44051505f8c18bbcbc680c5d48323787&chksm=c25e8657f5290f411d17063d8bf68c35ec4a02ed430b9f2e769d73a7f598c84af40547d98642&scene=178&cur_album_id=2893630619191214084#rd)：

可以从docker库的源地址查看原作者的相关文档，找到`docker run`开头的部分或`yml`配置，快速查看相关的命令和参数。

网络大部分`bridge`即可，少部分docker必须配置`host`。

### 存储空间

```
-v $PWD/ql:/ql/data \
```

- `-v`代表后面是需要配置的路径。
- `:`之前的`$PWD/ql`是自定义设定的内部路径，选择自己创建的文件或者文件夹即可。
- `:`后面的`/ql/data`需要完整复制，对应容器存储的装载路径。
- 最后面的`\`不要一并复制进参数框里。

### 端口设置

```
-p '8096:8096' \
-p '8920:8920' \
-p '1900:1900/udp' \
-p '7359:7359/udp' \
```

- `-p`代表后面是需要配置的端口号。
- `:`之前的`8096`是自定义的本地端口号，不能填写如`80/443`这种会被屏蔽的端口号；不能填写其他docker用过的端口号，否则无法启动；也可以什么都不填写，让系统自动配置。
- `:`后面的`8096`需要完整复制，对应映射容器内部的端口号，不能改动。
- `/udp`代表需要填写的端口类型为`udp`，默认不写则选择`tcp`。

### 环境变量

```
-e UID=0 \
-e GID=0 \
-e GIDLIST=0 \
-e TZ="Asia/Shanghai" \
-e HTTP_PROXY="http://你的代理IP:你的代理端口/" \
```

- `-e`代表后面是需要配置的环境变量。
- `=`之前的`TZ`是环境变量的名字，必须保留大小写字母的严格复制，不能做任何改动。
- `=`后面的`Asia/Shangha`对应环境变量下的值，绝大多数情况下都是严格复制，极少部分可以根据实际情况配置适合自己使用的值。
- `"`只是提示，实际在配置过程中，是不需要复制进去的。

## 镜像推荐

### 域名解析：DDNSgo


镜像名称：`jeessy/ddns-go`

```bash
docker run -d --name ddns-go --restart=always --net=host -v /opt/ddns-go:/root jeessy/ddns-go
```

端口号：9876

支持的域名服务商：Alidns(阿里云)、Dnspod(腾讯云)、Cloudflare 华为云、Callback 百度云、Porkbun、GoDaddy、Google Domain

>**来源：**
>[绿联NAS私有云部署DDNS-GO实现域名访问](https://mp.weixin.qq.com/s?__biz=MzkzMjE3MzMzNw==&mid=2247488261&idx=1&sn=24fa0ab5c32eb354569d45d3875aa6b3&chksm=c25e9073f52919655b09f53cdc0305f3e95acc0366fea3e95390fce3efee1bfb1d807778cbc2&scene=178&cur_album_id=2893630619191214084#rd)

### 宝塔

镜像名称：`kangkang223/baota`

网络：host 模式

挂载目录：
- `/www/wwwlogs` -- 网站日志
- `/www/wwwroot` -- 网站根目录
- `/www/backup` -- 宝塔自动备份文件

首次安装请访问： [http://内网ip:8888/f185ef31](http://8.8.8.8:8888/f185ef31)

- username: kangkang
- password: kangkang

已集成如下服务：

- redis
- mysql 5.7
- php 7.4 8.0
- nginx 1.2
- 常用插件
- npm nodejs

>**来源：**
>[绿联私有云安装宝塔教程 (qq.com)](https://mp.weixin.qq.com/s?__biz=MzkzMjE3MzMzNw==&mid=2247488049&idx=1&sn=765db15b0d4bb68ce9f8cfc2340e8030&chksm=c25e9147f5291851d3467ccc9f237ce5324105f2126894162d46b239c77b1bd23e093b14d3b7&scene=178&cur_album_id=2893630619191214084#rd)

### 开发用的镜像

镜像名称：[smiecj/docker-centos](https://github.com/smiecj/docker-centos)

里面安装了一些开发语言的基本环境（如 java）。语言下载的依赖（如 maven、gopath）都统一放在 `/home/path` 目录下，安装的组件都放在 `/home/modules` 下。

镜像下载和启动方式：

```
# dockerfiles 中添加项目中的 Dockerfile 文件
docker build dockerfiles/
docker run -e "ROOT_PWD=设定root密码" --name centos_dev -d --privileged -p 设定本地ssh端口:22 mzsmieli/centos_dev
```

`ROOT_PWD` 可以设置 root 登录密码，也可以不设置，默认密码参考`init-system.sh`脚本中的定义

`-p` 后面可以自行设置暴露的 ssh 端口，容器成功启动后，可通过该端口访问容器内部

启动成功后，就可以进行自由的开发了。如果需要在容器内部编写代码，这里再推荐 `vscode + ssh + 本地免密登录配置`的开发模式。修改之后，在容器内部代码变更可以立刻生效，也可以在 vscode 中直接通过 命令行 执行操作。

### 可直接通过 ssh 连接的镜像：[jdeathe/centos-ssh](https://github.com/jdeathe/centos-ssh)

除了启动命令的学习，这个仓库提供的`Dockefile`是直接在`centos原生镜像`基础上改的。

从`Dockerfile`中也能看到非常多标准化的操作，想要学习`centos原生镜像初始化细节`的可以从这个项目的`Dockerfile`中了解更多细节。

```
docker pull jdeathe/centos-ssh

docker run -d --env "SSH_PASSWORD_AUTHENTICATION=true" --env "SSH_USER=centos" --env "SSH_USER_PASSWORD=test123" --name ssh.1 -p 30022:22 jdeathe/centos-ssh
```
