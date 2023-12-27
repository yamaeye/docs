## 报错

### [npm install 安装报错](https://blog.csdn.net/weixin_38292069/article/details/85005443)

```
this is a problem related to network connectivity
```

将代理置为空即可：

```
npm config set proxy null 
```

## 配置

### [切换阿里镜像](https://www.cnblogs.com/bmxxfvlog/p/16362334.html)

```
npm config set registry https://registry.npmmirror.com/
```

### [如何更新npm](https://blog.csdn.net/weixin_44222492/article/details/99637027)

```shell
npm install npm@latest -g
```

###### 更新全局包

```shell
npm update -g
```
