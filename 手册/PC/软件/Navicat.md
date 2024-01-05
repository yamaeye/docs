## 基础
### [navicat怎么导入sql文件](https://blog.csdn.net/ma286388309/article/details/129262620)

选择要执行sql脚本的数据库 - 右键 - 运行SQL文件

### [在 Navicat 中执行数据库范围搜索](https://www.navicat.com.cn/company/aboutus/blog/302-%E5728-navicat-%E4E2D%E6267%E884C%E6570%E636E%E5E93%E8303%E56F4%E641C%E7D22)

工具 - 在数据库或模式中查找 - 双击“查找结果”窗格中的项目 - 新打开的查询编辑器中只包含匹配的行

![](https://www.navicat.com.cn/link/Blog/Image/2017/20171206/find_in_db_data_results.jpg)

## 报错

### [2006 - MySQL server has gone away](https://blog.csdn.net/qq_34528297/article/details/88384452)

用Navicat 在本地运行一个比较大的 .sql 文件时报错：

```
[Err] 2006 - MySQL server has gone away
```

因为navica本身做了限制 所以导致报错。

1. 工具 - 服务器监控 - mysql 
2. 选择 `变量` ，找到 `max_allowed_packect` ，修改它的值即可。