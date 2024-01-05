### [获取Cookie](https://zhuanlan.zhihu.com/p/616919265?utm_id=0)

1. 打开 GLaDOS [签到页面](https://glados.rocks/console/checkin)
2. 打开浏览器「开发者工具」(快捷键 F12 或 Ctrl+Shift+I), 切换到「网络 Network」标签页
3. 找到名字为 `status` 这一行, 点击打开详情, 在「请求头 Request」找到 Cookie, 格式类似 `koa:sess=xxxxxx; koa:sess.sig=xxxxxx`