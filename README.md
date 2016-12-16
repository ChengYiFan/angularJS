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

## Demo06: 过滤器

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo06/index.html)

AngularJS过滤器可用于转换数据。

* currency格式化数字为货币格式；
* filter从数组项中选择一个子集；
* lowercase格式化字符串为小写；
* orderBy根据某个表达式排列数组；
* uppercase格式化字符串为大写。

```html
<div ng-app="myApp" ng-controller="personCtrl">
	<p>姓名为{{ lastName |uppercase }}</p>
	<br>
	<input type="number" ng-model="quantity"> <br>
	<input type="number" ng-model="price"> <br>
	<p>总价 = {{(quantity*price) | currency}}</p>
</div>
<script>
	var app = angular.module('myApp', []);
	app.controller('personCtrl', function($scope){
		$scope.lastName = 'lily';
		$scope.quantity = 1;
		$scope.price = 9.99;
	});
</script>
```

## demo07: 服务(Service)

在AngularJS 中，服务是一个函数或对象，可在你的AngularJS应用中使用。AngularJS内建了30多个服务。

##### $location服务，它可以返回当前页面的URL地址。
[source](https://github.com/ChengYiFan/angularJS/tree/master/demo07/index.html)

```html
<script>
	var app = angular.module('myApp', []);
	app.controller('', function($scope, $location){
		$scope.myUrl = $location.absUrl();
	});
</script>
```
注意$location服务是作为一个参数传递到controller中。如果要使用它，需要在controller中定义。

##### $http 服务
[source](https://github.com/ChengYiFan/angularJS/tree/master/demo07/index-http.html)

$http 是 AngularJS应用中最常用的服务。服务向服务器发送请求，应用响应服务器传送过来的数据。

```html
<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope,$http){
		$http.get("welcome.html").then(function(response){
			$scope.myWelcome = response.data;
		});
	});
</script>
```
##### $timeout 服务

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo07/index-timeout.html)

AngularJS $timeout 服务对应了 JS window.setTimeout函数。
```html
<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope,$timeout){
		$scope.myHeader = "Hello World!";
		$timeout(function(){
			$scope.myHeader = "How are you today?";
		},2000);
	});
</script>
```

##### $interval 服务

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo07/index-interval.html)

AngularJS $interval 服务对应了 JS window.setInterval函数。
```html
<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope,$interval){
		$scope.theTime = new Date().toLocaleTimeString();
		$interval(function(){
			$scope.theTime = new Date().toLocaleTimeString();
		},1000);
	});
</script>
```

##### 创建自定义服务

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo07/self-definition-func-service.html)

可以创建访问自定义服务，链接到你的模块中，例如创建名为hexafy的访问：
```html
<script>
var app = angular.module('myApp',[]);
app.service('hexafy',function(){
	this.myFunc = function(x){
		return x.toString(16);
	}
});
</script>
```
要使用访问自定义服务，需要在定义过滤器的时候独立添加。使用自定义的服务hexafy将一个数字转换为16进制数：
```html
<script>
app.controller('myCtrl',function($scope,hexafy){
	$scope.hex = hexafy.myFunc(255);
})
</script>
```

##### 在过滤器中，使用自定义服务

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo07/filter-service.html)

当你创建了自定义服务，并连接到你的应用上后，你可以在控制器，指令，过滤器或其他服务中使用它。在过滤器myFormat中使用服务hexafy:

```html
<script>
app.filter('myFormat',['hexafy',function(hexafy){
	return function(x){
		return hexafy.myFunc(x);
	};
}]);
</script>
```

## demo08: 选择框(Select)

AngularJS 可以使用数组或对象创建一个下拉列表选项。

##### 使用ng-options 创建选择框

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo08/ng-options-select.html)

在 AngularJS中我们可以使用ng-option指令来创建一个下拉列表，列表项通过对象和数组循环输出，如下示例：

```html
<div ng-app="myApp" ng-controller="myCtrl">
	<select name="" id="" ng-model="selectedName" ng-options="x for x in names">		
	</select>
</div>
<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope){
		$scope.names = ['Google','Runoob','Taobao'];
	});
</script>
```

该实例演示了使用ng-options指令来创建下拉列表，选中的值是一个对象。

##### 我们也可以使用ng-repeat指令来创建下拉列表：

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo08/ng-repeat-select.html)
```html
<div ng-app="myApp" ng-controller="myCtrl">
	<select name="" id="">
		<option value="" ng-repeat="x in names">{{x}}</option>
	</select>
</div>
<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope){
		$scope.names = ['google','runoob','taobao'];
	});
</script>
```

ng-repeat指令是通过数组来循环HTML代码来创建下拉列表，但ng-options指令更适合创建下拉列表，它有以下优势：使用ng-options的选项的一个对象，ng-repeat是一个字符串。

##### 使用对象作为数据源创建下拉列表

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo08/obj-ng-options.html)

```html
<div ng-app="myApp" ng-controller="myCtrl">
	<p>选择的网站是：</p>
	<select name="" id="" ng-model="selectedSite" ng-options="x for (x,y) in sites">	
	</select>
	<h1>你选择的值是：{{selectedSite}}</h1>
</div>

<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope){
		$scope.sites = {
			site01: "Google",
			site02: "Runoob",
			site03: "Taobao"
		};
	});
</script>
```
使用对象作为数据源, x 为键(key), y 为值(value)。

## demo09: 表格(Table)

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo09/index.html)

ng-repeat 指令可以完美的显示表格。
```html
<div ng-app="myApp" ng-controller="customersCtrl">
	<table>
		<thead>
			<tr>
				<th>姓名</th>
				<th>城市</th>
				<th>区</th>
			</tr>
		</thead>
		<tbody>
			<tr ng-repeat="x in names">
				<td>{{x.Name}}</td>
				<td>{{x.City}}</td>
				<td>{{x.Country}}</td>
			</tr>
		</tbody>
	</table>
</div>
<script>
	var app = angular.module('myApp',[]);
	app.controller('customersCtrl',function($scope, $http){
		$http.get('customers.json').success(function(response){
			$scope.names = response.records;
		});
	});
</script>
```
