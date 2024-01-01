## [文件结构](https://yingyongge.com/bw354t19V1.html)

1. WordPress安装文件：通常包含在"wordpress"文件夹中
2. wp-admin文件夹：用于管理WordPress后台
3. wp-content文件夹：包含WordPress的主题、插件和媒体文件等
4. wp-includes文件夹：包含WordPress核心的PHP文件
5. 文章的内容和元数据：保存在数据库中

## 故障

### [上传的文件大小超过php.ini限制](https://dl.dp0.com/921.html)

1. 进入站点的根文件夹 - 创建`php.ini`文件

![](https://pic3.zhimg.com/v2-d47493590bcbf017b82cfbb0ae2b403e_b.jpg)

2. 添加以下代码：

```
upload_max_filesize = 512M
post_max_size = 512M
memory_limit = 512M
```

3. 如果不起作用，编辑`.htaccess`文件，添加以下代码：

```
php_value upload_max_filesize 512M
php_value post_max_size 512M
php_value memory_limit 512M
```

![](https://pic3.zhimg.com/v2-6b31c8b67eb974526d1c56077aded8b2_b.jpg)

## 插件

### [Wordfence](https://www.zhihu.com/question/22864602/answer/85488065)

安全防御插件，可限制密码尝试次数防止暴力破解，可为你的 WordPress 增加 WAF 功能，查看实时访问。只要尝试 3 次错误密码，IP 会直接被屏蔽掉。

### [UpdraftPlus](https://www.zhihu.com/question/22864602/answer/3119973321)

允许对网站进行完整的备份并快速恢复，将其存储在多个云存储选项上，包括Google Drive、Dropbox和Amazon S3。只适用于小型网站和较新版本的WordPress网站，也可能会使网站过载。

### [WPvivid](https://www.wpdaxue.com/wpvivid-backup.html)

可以自动或手动备份网站文件和数据库，只需单击一下，即可将WordPress网站移至新域名。

### [Litespeed cache](https://zhuanlan.zhihu.com/p/647126005)

常规 - 生成域密钥 - 等待几分钟后刷新 - Link to QUIC.cloud - 注册QUIC.cloud账号

@[LittleModesty](https://www.zhihu.com/question/361191216/answer/989181663)：

LSCache(LightSpeed Cache)需要服务器层面的软件支持。WP Rocket需要付费使用，W3 Total Cache虽然免费但设置繁琐，WP Super Cache性能不好但设置最为简单......

![性能对比](https://pic1.zhimg.com/v2-dd12c2342fd8190cfaeb1e5eeb3d32d5_r.jpg?source=1def8aca)

### [WP Super Cache](https://zhuanlan.zhihu.com/p/603725081)

为了取代繁琐的WordPress PHP代码，它通过产生静态HTML文件并提供这些文件以加快加载时间来有效地运作。WP Super Cache的简单设置是一个主要优势，您可以简单地启用缓存功能，让插件完成剩下的工作，或者您可以利用更多的高级功能。

### [Wp Fastest Cache](https://zhuanlan.zhihu.com/p/612620500)

如果许多访问者来到该网站，那么系统会使用大量的RAM和CPU，因此页面需要时间来加载。W3缓存插件会生成一个静态缓存文件，因此您的服务器不会一次又一次地使用RAM和CPU。