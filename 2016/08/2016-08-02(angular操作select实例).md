# angular操作select实例 #

	<!DOCTYPE html>
	<html lang="en" ng-app="myApp">
	<head>
		<meta charset="UTF-8">
		<script src="angular.js"></script>
	</head>
	<body>
		<div ng-controller="MyCtrl">
			<select ng-disabled="isDisabled" ng-model="current_option" 
					ng-options="option.value as option.key for option in option_array"></select>
		</div>
		<script>
			var app = angular.module('myApp', []);
			app.controller('MyCtrl', ['$scope', function($scope){
				$scope.option_array = [
					{
						key: 'hello',
						value: '1'
					},
					{
						key: 'world',
						value: '2'
					}
				];
				$scope.current_option = $scope.option_array[1].value;		
			}]);
	
		</script>
	</body>
	</html>