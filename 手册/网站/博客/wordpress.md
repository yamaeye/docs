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