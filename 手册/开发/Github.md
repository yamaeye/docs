## [git 提交步骤](https://blog.csdn.net/gongqinglin/article/details/79752398)

1. git init：`初始化仓库`

2. git add .(文件name)：`添加文件到本地仓库`

3. git commit -m "first commit"：`添加文件描述信息`

4. git remote add origin https://github.com/用户名/仓库名.git ：`链接远程仓库，创建主分支`

5. git pull origin master --allow-unrelated-histories：`把本地仓库的变化连接到远程仓库主分支`

6. git push -u origin master：`把本地仓库的文件推送到远程仓库`

---

## [生成/添加SSH公钥](https://gitee.com/help/articles/4181#article-header0)

```
ssh-keygen -t rsa -C "youremail@example.com"
```

换成自己的邮件地址，回车三次，即可生成。

查看并复制C盘用户主目录里 `~/.ssh/id_rsa.pub` 文件内容，粘贴到个人设置的SSH Keys。

---

## [host](https://github.com/ButterAndButterfly/GithubHost)

复制到host文件中：

[https://github.com/ButterAndButterfly/GithubHost/releases/download/v1/host.txt](https://github.com/ButterAndButterfly/GithubHost/releases/download/v1/host.txt)

[https://hub.fastgit.xyz/ButterAndButterfly/GithubHost/releases/download/v1/host.txt](https://hub.fastgit.xyz/ButterAndButterfly/GithubHost/releases/download/v1/host.txt)

## [jsdelivr加速CDN](https://www.cnblogs.com/yu-du-chen/p/12109065.html)


1. 首先需要创建 releases

2. 记住tag对应的版本号

3. 随便进入到一个文件，看一下地址名

4. 把想加速的文件地址改成jsdelivr版本：


```
https://cdn.jsdelivr.net/gh/用户名/仓库名@版本号/文件地址
```
比如：

```
https://github.com/yuDuChen/yuduchen/blob/v1.5.6/layui/layui.js
https://cdn.jsdelivr.net/gh/yuDuChen/yuduchen@v1.5.6/layui/layui.js
```

---

## 报错

### [推送失败](https://www.liaoxuefeng.com/discuss/969956160874304/1277343677018304)

```
fatal: Could not read from remote repository. Please make sure you have the correct access rights and the repository exists.
```

廖老师是通过 `git@github.com:michaelliao/learngit.git` 关联的，在win7和win10上测试推送时都不能成功，`https`的才可以。


如果已经用git@关联，则可以在`.git`目录下的`config文`件中，把 `url =` 后面的内容改为`https`类型的即可。

### [撤销上次推送并改正](https://blog.csdn.net/CCC_122/article/details/105890703)

1. 撤回commit提交，不会删除本地文件。想撤回两次commit，也可以使用`HEAD~2`
```
git reset --soft HEAD^
```
2. 撤销全部add的文件
```
git reset
```
3. 修改文件后，重新提交正确内容
```
git add .
git commit -m
```
4. 强制推送
```
git push --force
```

### [回退到指定版本](https://www.freesion.com/article/4316264352/#_8)
```
git reset --hard <哈希值> //哈希值即为commit后面的那串字符
git push -f -u origin master 
```

### [SSL错误](https://blog.csdn.net/bblood307/article/details/120307064)

```
fatal: unable to access ‘https://github.com/…’: OpenSSL SSL_read: Connection was reset, error 10054
```

一般是这是因为服务器的SSL证书没有经过第三方机构的签署，所以才报错。

解除ssl验证后，再次git即可：

```
git config --global http.sslVerify "false"
```

### [Not a git repository](https://www.cnblogs.com/X-knight/p/9557642.html)


```
fatal: Not a git repository (or any of the parent directories): .git
```

提示说没有`.git`这样一个目录，解决办法如下：

在命令行敲入`git init`回车之后，再重新执行添加文件的命令即可。


### [提交代码时发生冲突](https://blog.csdn.net/qq_32963841/article/details/107332157)

```
fatal: Exiting because of an unresolved conflict.
```

1. 先查看状态

```
git status
```

2. 找到并处理冲突文件后，重新push

### [untracked files（未监控）](https://blog.csdn.net/lemonxiaoxiao/article/details/123877161)

```
untracked files:
(use "git add <file>..." to include in what will be commited)
bash.exe.stackdump
sh.exe.stackdump
```

删除 untracked files即可：


```
git clean -f
```

### [提示：This key is not known by any other names](https://www.cnblogs.com/dhjy/p/15918890.html)

```
The authenticity of host 'github.com (20.205.243.166)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
```

原因是：新生成的密钥，在ssh目录下少了一个known_hosts文件，本来密钥文件应该是三个，现在是两个，便报了这样的错误，此时选择yes并回车便可，同时生成了缺少了的known_hosts文件。