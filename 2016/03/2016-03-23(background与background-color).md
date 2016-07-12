# background与background-color #

今天做小demo的时候，遇到了这样一个问题：要实现一个按钮，按钮中间有一个小的向左的icon，类似于“<”，同时这个按钮的其他区域背景为白色。

于是这样写：

```
.left-button {
    backgroud-color: #fff;
    background: url(../img/left-button-icon.png) no-repeat center center;
}
```

这样写，背景图片是生效了，但是白色背景却没有出来，思考了一下，是因为`background`这个综合属性覆盖了之前的单一属性`background-color`，于是将两个属性调换顺序，OK！

```
.left-button {
    background: url(../img/left-button-icon.png) no-repeat center center;
    backgroud-color: #fff;
}
```