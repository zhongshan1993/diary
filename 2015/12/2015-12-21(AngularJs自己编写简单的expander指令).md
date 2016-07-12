# AngularJs自己编写简单的expander指令 #

[查看DEMO](http://zhongshan1993.github.io/myDemo/AngularJs/expanderSimple/) 

## ExpanderSimple.html ##

```
<!DOCTYPE html>
<html ng-app="ExpanderModule">
<head>
    <meta charset="UTF-8">
    <title>自己编写指令 - 最简单的expander指令</title>
    <link rel="stylesheet" href="ExpanderSimple.css">
    <script src="bower_components/angular/angular.js"></script>
    <script src="ExpanderSimple.js"></script>
</head>
<body>
    <div ng-controller="SomeController">
        <expander class="expander" expander-title="title">
            {{text}}
        </expander> 
    </div>
</body>
</html> 
```

## ExpanderSimple.js ##

```
var expanderModule = angular.module('ExpanderModule', []);

expanderModule.directive('expander', function() {
    return {
        restrict: 'AE',
        replace: true,
        transclude: true,
        scope: {
            title: '=expanderTitle'
        },
        template: '<div>'
                + '<div class="title" ng-click="toggle()">{{title}}</div>'
                + '<div class="body" ng-show="showMe" ng-transclude></div>'
                + '<div>',
        link: function(scope, element, attrs) {
            scope.showMe = false;
            scope.toggle = function() {
                scope.showMe = !scope.showMe;
            }
        }
    }
});
expanderModule.controller('SomeController', ['$scope', function($scope){
    $scope.title = "点击展开";
    $scope.text = "这里是内部内容。"
}]);

```

 