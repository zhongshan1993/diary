# AngularJs操作CSS简单运用 #

**这几天来爸妈这里检查身体，哎，身心俱疲~**

**index.html**

```
<!DOCTYPE html>
<html ng-app="MyCSSModule">
<head>
    <meta charset="UTF-8">
    <title>Angular 操作CSS</title>
    <link rel="stylesheet" href="page.css">
</head>
<body>
    <div ng-controller="CSSCtrl">
        <p class="text-{{color}}">测试CSS样式</p>
        <button ng-click="setGreen()">绿色</button>
    </div>
    <script src="http://libs.useso.com/js/angular.js/1.3.0-beta.9/angular.min.js"></script>
    <script src="css.js"></script>
</body>
</html>

```

**page.css**

```
.text-green {
    color: #00ff00;
}
.text-red {
    color: #ff0000;
}
```

**css.js**

```
var myCSSModule = angular.module('MyCSSModule', []);

myCSSModule.controller('CSSCtrl', ['$scope', function($scope){
    $scope.color = 'red';
    $scope.setGreen = function() {
        $scope.color = "green";
    }
}])
```