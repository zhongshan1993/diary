# AngularJs指令的compile与link #

## 加载阶段 ##

- 加载angular.js，找到ng-app，确定应用的边界

## 编译阶段 ##

- 遍历DOM，找到所有指令
- 根据指令代码中的template、replace、transclude转换DOM结构
- 如果存在compile函数则调用

## 链接阶段 ##

- 对每一条指令运行link函数
- link函数一般用来操作DOM、绑定事件监听器 