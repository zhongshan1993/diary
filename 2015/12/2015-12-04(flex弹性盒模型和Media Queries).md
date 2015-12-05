# flex弹性盒模型和Media Queries #

[查看响应式DEMO](http://zhongshan1993.github.io/myDemo/css3Comprehensive/media-queries and flex.html)
## 伸缩性flex ##

```
flex：none | <' flex-grow '> <' flex-shrink >'? || <' flex-basis '> 
```

`flex-grow`: 扩展比例，默认值1
`flex-shrink`: 收缩比例，默认值1
`flex-basis`: 伸缩基准值
如果缩写`「flex: 1」`, 则其计算值为`「1 1 0%」`
如果缩写`「flex: auto」`, 则其计算值为`「1 1 auto」`
如果`「flex: none」`, 则其计算值为`「0 0 auto」`


## flex-flow定义了伸缩容器的主轴和侧轴  ##

```
flex-flow：<' flex-direction '> || <' flex-wrap '>
```

默认值: `row nowrap`。

`flex-direction`: 定义弹性盒子元素的排列方向。`row|row-reverse|column|column-reverse`

`flex-wrap`: 控制flex容器是单行还是多行。`nowrap|wrap|wrap-reverse`

## 响应式布局 Media Queries ##

`@media all and (min-width)`   所有最小水平屏幕宽度为800像素的屏幕应用规则

`@media and (min-width)`   同上

`@media (not min-width:800px)`   当最小宽度不是800像素时会应用下列CSS规则

