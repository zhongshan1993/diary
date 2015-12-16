# AngularJs指令与指令之间的交互 # 

## Directive&Directive.html ##

```
<!DOCTYPE html>
<html ng-app="MyModule">
<head>
    <meta charset="UTF-8">
    <title>指令和指令之间的交互</title>
    <link rel="stylesheet" href="bower_components/bootstrap/dist/css/bootstrap.css">
</head>
<body>
    <div class="row">
        <div class="col-md-3">
            <superman strength>动感超人——力量</superman>
        </div>
    </div>
    <div class="row">
        <div class="col-md-3">
            <superman strength speed>动感超人2——力量+敏捷</superman>
        </div>
    </div>
    <div class="row">
        <div class="col-md-3">
            <superman strength speed light>动感超人3——力量+敏捷+发光</superman>
        </div>
    </div>
    <!-- 引用angular.js -->
    <script src="bower_components/angular/angular.js"></script>
    <script src="Directive&Directive.js"></script>

</body>
</html> 

```

## Directive&Directive.js ##

```

var myModule = angular.module("MyModule", []);

// 指令
myModule.directive("superman", function() {
    return {
        scope: {},
        restrict: 'AE',
        controller: function($scope) {
            $scope.abilities = [];
            this.addStrength = function() {
                $scope.abilities.push("strength");
            };
            this.addSpeed = function() {
                $scope.abilities.push("speed");
            };
            this.addLight = function() {
                $scope.abilities.push("light");
            };
        },
        link: function(scope, element, attrs) {
            element.addClass('btn btn-primary');
            element.bind('mouseenter',function() {
                console.log(scope.abilities);
            });
        }
    }
});



myModule.directive('strength', function() {
    return {
        require: '^superman',
        link: function(scope, element, attrs, supermanCtrl) {
            supermanCtrl.addStrength();
        }
    }
});
myModule.directive('speed', function() {
    return {
        require: '^superman',
        link: function(scope, element, attrs, supermanCtrl) {
            supermanCtrl.addSpeed();
        }
    }
});
myModule.directive('light', function() {
    return {
        require: '^superman',
        link: function(scope, element, attrs, supermanCtrl) {
            supermanCtrl.addLight();
        }
    }
});

```