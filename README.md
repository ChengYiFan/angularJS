这是Angular.js入门练习的demos。此demo版本为Angular 1。

Angular JS 是一个JavaScript框架，通过指令扩展了HTML，且通过表达式绑定数据到HTML。

## Angular JS 扩展了HTML
- AngularJS 通过 ng-directives 扩展了 HTML。
- ng-app 指令定义一个 AngularJS 应用程序。
- ng-model 指令把元素值（比如输入域的值）绑定到应用程序。
- ng-bind 指令把应用程序数据绑定到 HTML 视图。

## 使用案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>angularJS-controller</title>
	<script src="js/angular-1.4.6-min.js"></script>
</head>
<body>
	<p>尝试修改以下表单</p>
	<div ng-app="myApp" ng-controller="myCtrl">
		名：<input type="text" ng-model="firstName">
		姓：<input type="text" ng-model="lastName">
		<br/>
		姓名：{{firstName+ " "+ lastName}}
	</div>
	<script>
		var app = angular.module('myApp',[]);
		app.controller('myCtrl',function($scope){
			$scope.firstName = 'John';
			$scope.lastName = 'Doe';
		})
	</script>
	
</body>
</html>
```
* Angular JS 模块(Module) 定义了Angular JS应用
* Angular JS 控制器(controller) 用于控制 Angular JS 应用
* ng-app 指令定义了应用
* ng-controller定义了控制器