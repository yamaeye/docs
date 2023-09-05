#### [批量填充序号](https://jingyan.baidu.com/article/f7ff0bfcc7ef1b6f27bb1354.html)

1. 输入起始序号。
2. 选中需要填充的区域，点击`开始 - 行和列 - 填充`。
3. 默认选择列，等差序列，步长值1，点击确定即可。

#### [行转列](https://www.knowbaike.com/excel/3744.html)

1. 复制行内容
2. 选择性粘贴 - 转置

#### [公式参数不自动变化](https://jingyan.baidu.com/article/19020a0a2ea81b139c28424b.html)

在参数的行号和列号前加`$`，如`=$A$2+B1`。

#### [冻结窗格](https://jingyan.baidu.com/article/915fc41485f89310384b2023.html)

1. 点击要设置冻结窗格的单元格。
2. 点击右侧的【开始 - 冻结窗格】按钮。
3. 下拉菜单的第一项会自动冻结至单元格所在的【行与列】。
4. 如果只需要冻结行/列，可选择“冻结至第N行/列”。

#### [身份证转年龄](https://zhidao.baidu.com/question/464663474577496285.html)

1. 出生日期公式：=--TEXT(MID(选身份证格,7,8),"0-00-00")
2. 生日转年龄公式：=DATEDIF(选生日格子,TODAY(),"y")