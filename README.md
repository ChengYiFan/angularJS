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
	<script src="../js/angular-1.4.6-min.js"></script>
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

## Demo01: Angular JS 表达式

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo01/index.html)

表达式写在双大括号内：{{expression}}。作用是把数据绑定到HTML,这与ng-bind指令有异曲同工之妙。\<br>
Angular JS 将在表达式书写的位置“输出”数据。

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>angularJS-expression</title>
	<script src="../js/angular-1.4.6-min.js"></script>
</head>
<body>
	<div ng-app="" ng-init="cost=5;num=2">
		<p>我的第一个表达式：{{5 + 5}}</p>
		<p>总价：{{cost * num}}</p>
	</div>
</body>
</html>
```
类似于JavaScript表达式，Angular JS表达式可以包含字母，操作符，变量。

## Demo02: 创建自定义指令

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo02/index.html)

```html
<body ng-app="myApp">
	<runoob-directive></runoob-directive>
	<script>
		var app = angular.module("myApp", []);
		app.directive("runoobDirective", function() {
    		return {
        		template : "<h1>自定义指令!</h1>"
    		};
		});
	</script>
</body>
```
Angular JS指令用于扩展HMTL属性，带有前缀ng-。除了自定义指令，常用的有以下几种：
* ng-app指令初始化一个AngularJS应用程序
* ng-init指令初始化应用程序数据
* ng-model指令把元素值（比如输入域的值）绑定到应用程序。
* ng-repeat指令会重复一个HTML元素，用在一个对象数组上。

AngularJS完美支持数据库的CRUD（增加create、读取read、更新Update、删除Delete)应用程序。

## Demo03: ng-model指令

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo03/index.html)

ng-model指令 用于绑定应用程序数据到HTML控制器(input,select,textarea)的值。

```html
<div ng-app="myApp" ng-controller="myCtrl">
	名字：<input type="text" ng-model="name">
</div>
<script>
	var app = angular.module("myApp", []);
	app.controller("myCtrl", function($scope) {
		$scope.name = "Cynthia";
	});
</script>
```
ng-model指令 可以将输入域的值与AngularJS创建的变量绑定。

## Demo04: Scope(作用域)

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo04/index.html)

AngularJS应用组成如下：
* View（视图），即HTML。
* Model(模型)，当前视图中可用的数据。
* Controller(控制器)，即JavaScript函数，可以添加或修改属性。

Scope是模型，带有属性和方法，可以在视图和控制器中使用。Scope(作用域)是应用在HTML（视图）和JavaScript（控制器）之间的纽带。Scope是一个对象，有可用的方法和属性。Scope可应用在视图和控制器上。当你在AngularJS创建控制器时，你可以将$scope对象当作一个参数传递。

```html
<div ng-app="myApp" ng-controller="myCtrl">
	<h1>{{lastname}} 家族成员：</h1>
	<ul>
		<li>{{x in names}} {{lastname}}</li>
	</ul>
</div>
<script>
	var app = angular.module("myApp", []);
	app.controller("myCtrl", function($scope,$rootScope) {
		$scope.names = ["Cynthia", "Tobias", "Linus"];
		$rootScope.lastname = "Refsnes";
	});
</script>
```
在创建控制器时，你可以将$scope对象当作一个参数传递，视图（HTML）可以获取这些属性。视图中，你不需要添加$scope前缀，只需要添加属性名即可。

在大型项目中，HTML DOM中有多个作用域，这时你就需要知道你使用的scope对应的作用域是哪一个。

所有的应用都有一个$rootScope，它可以作用在ng-app指令包含的所有HTML元素中。用rootScope定义的值，可以在各个controller中使用。

## Demo05: 控制器

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo05/index.html)

ng-controller指令定义了应用程序控制器。控制器是JavaScript对象，由标准的JavaScirpt对象的构造函数创建。

```html
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
```

