# AngularJs操作CSS样式 #

[查看DEMO](http://zhongshan1993.github.io/myDemo/AngularJs/handleCSSStyle/index.html) 


## index.html ##

```
<!DOCTYPE html>
<html ng-app="MyCSSModule">
<head>
    <meta charset="UTF-8">
    <title>Angular 操作CSS样式</title>
    <link rel="stylesheet" href="NgClass.css">
</head>
<body>
    <div ng-controller="HeaderController">
        <div ng-class="{error: isError, warning: isWarning}">{{messageText}}</div>
        <button ng-click="showError()">Simulate Error</button>
        <button ng-click="showWarning()">Simulate Warning</button>
    </div>
    <script src="http://libs.useso.com/js/angular.js/1.3.0-beta.9/angular.min.js"></script>
    <script src="NgClass.js"></script>
</body>
</html>

```


## NgClass.css ##

```
.error {
    background-color: #00ff00;
}
.warning {
    background-color: #ff0000;
}
```

## NgClass.js ##


```

var myCSSModule = angular.module('MyCSSModule', []);

myCSSModule.controller('HeaderController', ['$scope', function($scope){
    $scope.isError = false;
    $scope.isWarning = false;
    $scope.showError = function() {
        $scope.messageText = "This is a error";
        $scope.isError = true;
        $scope.isWarning = false;
    }
    $scope.showWarning = function() {
        $scope.messageText = "Just a Warining, please carry on!";
        $scope.isError = false;
        $scope.isWarning = true;
    }
}])


```   