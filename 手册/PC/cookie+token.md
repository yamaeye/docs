### [阿里云盘refresh_token](https://github.com/yaoysyao/Auto_checkin_release/blob/master/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E.md)

- 控制台粘贴

```
JSON.parse(localStorage.token).refresh_token
```

- 也可以到开发者工具 - Application - Local Storage 中的 token 字段中找到。

### [GlaDos获取Cookie](https://zhuanlan.zhihu.com/p/616919265?utm_id=0)

1. 打开 GLaDOS [签到页面](https://glados.rocks/console/checkin)
2. 打开浏览器「开发者工具」(快捷键 F12 或 Ctrl+Shift+I)，切换到「网络 Network」标签页
3. 找到名字为 `status` 这一行, 点击打开详情, 在「请求头 Request」找到 Cookie, 格式类似 `koa:sess=xxxxxx; koa:sess.sig=xxxxxx`