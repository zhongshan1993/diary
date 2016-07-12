# AngularJs实现双向绑定 #

[查看DEMO](http://zhongshan1993.github.io/myDemo/AngularJs/dataBind/)

AngularJS可以通过ng-model实现双向绑定，在表单场景中，省去了使用jQuery时必须手动收集每个字段的繁琐，这一功能尤为出色。

以下为一个小DEMO

**index.html**

```
<!DOCTYPE html>
<html ng-app="UserInfoModule">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <link rel="stylesheet" href="bower_components/bootstrap/dist/css/bootstrap.min.css">
</head>

<body>
    <div class="panel panel-primary">
        <div class="panel-heading">
            <div class="panel-title">双向数据绑定</div>
        </div>
        <div class="panel-body">
            <div class="row">
                <div class="col-md-12">
                    <form action="" class="form-horizontal" role="form" ng-controller="UserInfoCtrl">
                        <div class="form-group">
                            <label class="col-md-2 control-label">
                                邮箱： 
                            </label>
                            <div class="col-md-10">
                                <input type="email" class="form-control" placeholder="推荐使用126邮箱" ng-model="userInfo.email">
                            </div>
                        </div>
                        <div class="form-group">
                            <label class="col-md-2 control-label">
                                密码：
                            </label>
                            <div class="col-md-10">
                                <input type="password" class="form-control" placeholder="只能是数字、字母、下划线" ng-model="userInfo.password">
                            </div>
                        </div>
                        <div class="form-group">
                            <div class="col-md-offset-2 col-md-10">
                                <div class="checkbox">
                                    <label>
                                        <input type="checkbox" ng-model="userInfo.autoLogin">自动登录
                                    </label>
                                </div>
                            </div>
                        </div>
                        <div class="form-group">
                            <div class="col-md-offset-2 col-md-10">
                                <button class="btn btn-default" ng-click="getFormData()">获取Form表单的值</button>
                                <button class="btn btn-default" ng-click="setFormData()">设置Form表单的值</button>
                                <button class="btn btn-default" ng-click="resetFormData()">重置Form表单的值</button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
    <script src="http://libs.useso.com/js/angular.js/1.3.0-beta.9/angular.min.js"></script>
    <script src="form.js"></script>
</body>

</html>
```


**form.js**

```
var userInfoModule = angular.module('UserInfoModule', []);

userInfoModule.controller('UserInfoCtrl', ['$scope', function($scope) {
    $scope.userInfo = {
        email: '19943848@qq.com',
        password: '12455',
        autoLogin: true
    }
    $scope.getFormData = function() {
        console.log($scope.userInfo);
    }
    $scope.setFormData = function() {
        $scope.userInfo = {
            email: 'zhongshan@124.com',
            password: 'aaaaaaaa',
            autoLogin: false
        }
    }
    $scope.resetFormData = function() {
        $scope.userInfo = {
            email: '19943848@qq.com',
            password: '12455',
            autoLogin: true
        }
    }
}])
```

