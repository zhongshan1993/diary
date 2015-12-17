# AngularJs指令的独立scope # 

## index.html ## 

```
<!DOCTYPE html>
<html ng-app="MyModule">
<head>
    <meta charset="UTF-8">
    <title>独立的scope</title>
    <link rel="stylesheet" href="bower_components/bootstrap/dist/css/bootstrap.css">
</head>
<body>
    <hello></hello>
    <hello></hello>
    <hello></hello>
    <hello></hello>
    <script src="bower_components/angular/angular.js"></script>
    <script src="app.js"></script>
</body>
</html>
```

## app.js ## 

```
var myModule = angular.module('MyModule', []);

myModule.directive("hello", function() {
    return {
        restrict: 'AE',
        template: '<div><input type="text" ng-model="userName"/>{{userName}}</div>',
        replace: true
    }
});
```

在上述的示例中，会得到如下图所示的结果

![](http://7xksst.com1.z0.glb.clouddn.com/QQ截图20151217154542.png)

这样，`<hello>`指令之间相互制约，根本无法使用，解决方法是引入独立作用域

## app.js ## 

```
var myModule = angular.module('MyModule', []);

myModule.directive("hello", function() {
    return {
        restrict: 'AE',
        scope: {},  // 创建独立的scope，指令间互不影响
        template: '<div><input type="text" ng-model="userName"/>{{userName}}</div>',
        replace: true
    }
});
```




