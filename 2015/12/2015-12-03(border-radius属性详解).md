# border-radius详解 # 

[查看demo](http://zhongshan1993.github.io/myDemo/css3Comprehensive/border-radius.html)

`border-radius`：如果"/"反斜杠符存在，"/"前面的值是设置元素圆角的水平方向半径，"/"后面的值是设置元素圆角的垂直方向的半径；

另外四个值是按照`top-left`、`top-right`、`bottom-right`、`bottom-left`顺序来设置的。

- `border-radius`：设置三个值，第一个值设置`top-left`，第二个值设置`top-right`和`bottom-left`，第三个值设置`bottom-right`
- `border-radius`：设置两个值，`top-left`等于 `bottom-right`，并且取第一个值；`top-right`等于`bottom-left`，并且取第二个值
- `border-radius`：水平半径 / 垂直半径（60px 40px 30px 20px）/ (30px 20px 10px 5px)：每个数值分别为上右下左的方向值

`border-radius`: 左上角水平圆角半径大小，右上角水平圆角半径大小 ，右下角水平圆角半径大小 ，左下角水平圆角半径大小 / 左上角垂直圆角半径大小 ，右上角垂直圆角半径大小 ，右下角垂直圆角半径大小 ，左下角垂直圆角半径大小;