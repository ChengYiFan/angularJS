这是Angular.js入门练习的demos。此demo版本为Angular 1。

Angular JS 是一个JavaScript框架，通过指令扩展了HTML，且通过表达式绑定数据到HTML。

## 对AngularJS的初步认识
1. 扩展HTML添加动态特性，因此我们可以轻松地构建现代web应用程序。
1. 以你想要的方式使用。
1. 带你回到HTML
1. 声明方法
1. 简单
1. 通过双向数据绑定消除DOM操作，任何时候当模型改变时视图都会得到更新，反之亦然。
1. 你可以用它来构建单页Web应用程序。当你构建如路由，Ajax调用，数据绑定，缓存，历史记录和DOM操作这类的SPA应用时，会有很多的挑战。
1. AngularJS使用客户端模板，它传递模板和数据到浏览器，然后在浏览器端组装。服务器的角色变成了只提供模板的静态资源和提供模板所需要的数据。

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

##### 使用orderBy过滤器

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo09/index-orderBy.html)

排序显示，可以使用orderBy过滤器：
```html
<table>
	<tr ng-repeat="x in names | orderBy : 'Country'">
		<td>{{x.Name}}</td>
		<td>{{x.Country}}</td>
	</tr>
</table>
```

##### 使用uppercase过滤器

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo09/index-uppercase.html)

使用uppercase过滤器转换为大小写：
```html
<table>
	<tr ng-repeat="x in names">
		<td>{{x.Name}}</td>
		<td>{{x.Country | uppercase}}</td>
	</tr>
</table>
```

##### 显示序号($index)

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo09/index-$index.html)

表格显示序号可以在<td>中添加 $index:
```html
<table>
	<tr ng-repeat="x in names">
		<td>{{ $index + 1 }}</td>
		<td>{{x.Name}}</td>
		<td>{{x.City}}</td>
		<td>{{x.Country}}</td>
	</tr>
</table>
```
##### 使用 $even 和 $odd

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo09/index-even.html)
```html
<table>
	<tr ng-repeat="x in names">
		<td ng-if="$odd" style="background-color:#f1f1f1">{{ x.Name }}</td>
		<td ng-if="$even">{{ x.Name }}</td>
		<td ng-if="$odd" style="background-color:#f1f1f1">{{ x.Country }}</td>
		<td ng-if="$even">{{ x.Country }}</td>
	</tr>
</table>
```

## demo10: HTML DOM

AngularJS 为 HTML DOM元素的属性提供了绑定应用数据的指令。

##### 使用 ng-disabled 指令

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo10/index-ng-disabled.html)

```html
<div ng-app="" ng-init="mySwitch=true">
	<p>
		<button ng-disabled="mySwitch">点我!</button>
	</p>

	<p>
		<input type="checkbox" ng-model="mySwitch">按钮
	</p>

	<p>
		{{ mySwitch }}
	</p>
</div>
```
ng-disabled指令绑定应用程序数据"mySwitch" 到 HTML的 disabled属性。ng-model指令绑定"mySwitch"到HTML input checkbox元素的内容（value）。如果mySwitch 为 true,按钮将不可用。如果mySwitch为false,按钮则可用。

##### 使用 ng-show 指令

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo10/index-ng-show.html)

ng-show指令根据value的值来显示（隐藏）HTML元素。你也可以使用表达式来计算布尔值（true或fasle）。

```html
<div ng-app="" ng-init="hour=13">
	<p ng-show="true">我是可见的。</p>
	<p ng-show="false">我是不可见的。</p>
	<p ng-show="hour > 10">我是可见的。</p>
	<p ng-hide="true">我是不可见的。。。。</p>
	<p ng-hide="false">我是可见的。。。。</p>
</div>
```

##### 使用 ng-hide 指令

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo10/index-ng-hide.html)

ng-hide指令用于隐藏或显示HTML元素

```html
<div ng-app="">
	<p ng-hide="true">我是不可见的。</p>
	<p ng-hide="false">我是可见的。</p>
</div>
```

## demo11: AngularJS 事件 有自己的HTML事件指令

##### 使用 ng-click 指令

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo11/index.html)

```html
<div ng-app="myApp" ng-controller="myCtrl">
	<button ng-click="count=count+1">点我！</button>
	<p>{{count}}</p>
</div>
<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope){
		$scope.count = 0;
	});
</script>
```

##### 通过定义事件函数来隐藏和显示HTML元素

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo11/index-function.html)

```html
<div ng-app="myApp" ng-controller="personCtrl">
	<button ng-click="toggle()">隐藏/显示</button>
	<p ng-hide="myVar">
		名：<input type="text" ng-model="firstName"><br>
		姓：<input type="text" ng-model="lastName"><br><br>
		姓名：{{firstName + " " + lastName}}
	</p>
</div>
<script>
	var app = angular.module('myApp',[]);
	app.controller('personCtrl',function($scope){
		$scope.firstName = 'John';
		$scope.lastName = 'Doe';
		$scope.myVar =  false;
		$scope.toggle = function(){
			$scope.myVar = !$scope.myVar;
		}
	});
</script>
```
应用解析：
- 第一部分personCtrl与控制器章节类似。应用有一个默认属性：$scope.myVar = false;
- ng-hide 指令设置<p>元素及两个输入域是否可见，根据myVar的值(true 或 false)来设置是否可见。
- toggle() 函数用于切换myVar变量的值(true 和 false)。
- ng-hide = "true"让元素不可见。

## demo12: AngularJS 表单

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo12/index.html)

AngularJS 表单时输入控件的集合。

```html
<div ng-app="myApp" ng-controller="formCtrl">
	<form action="" novalidate>
		First Name:<br>
		<input type="text" ng-model="user.firstName"><br>
		Last Name: <br>
		<input type="text" ng-model="user.lastName"> <br><br>
		<button ng-click="reset()">重置</button>
	</form>
	<p>form= {{user}}</p>
	<p>master = {{master}}</p>
</div>

<script>
	var app = angular.module('myApp',[]);
	app.controller('formCtrl',function($scope){
		$scope.master = {firstName:"John",lastName:"Doe"};
		$scope{
			$scope.user = angular.copy($scope.master);
		};
		$scope.reset();
	})
</script>
```

实例解析

- ng-app指令定义了AngularJS应用。
- ng-controller指令定义了应用控制器。
- ng-model指令绑定了两个input元素到模型的user对象。
- formCtrl 函数设置了master对象的初始值，并定义了reset（）方法。
- reset()方法设置了user对象等于master对象。
- ng-click指令调用了reset()方法，且在点击按钮时调用。
- novalidate 属性在应用中不是必须的，但是你需要在AngularJS 表单中使用，用于重写标准的HTML5验证。

## demo13: AngularJS 输入验证

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo13/index.html)

AngularJS表单和控件可以验证输入的数据，并对用户输入的非法数据进行警告（客户端的验证不能确保用户输入数据的安全，所以服务端的数据验证也是必须的。）

```html
<form action="" ng-app="myApp" ng-controller="validateCtrl" name="myForm" novalidate>
	<p>用户名：<br>
		<input type="text" name="user" ng-model="user" required>
		<span ng-show="myForm.user.$dirty && myForm.user.$invalid" style="color:red">
			<span ng-show="myForm.user.$error.required">用户名是必须的。</span>
		</span>
	</p>

	<p>
		邮箱：<br>
		<input type="email" name="email" ng-model="email" required>
		<span ng-show="myForm.email.$dirty && myForm.email.$invalid" style="color:red">
			<span ng-show="myForm.email.$error.required">邮箱是必须的。</span>
			<span ng-show="myForm.email.$error.email">非法的邮箱。</span>
		</span>
	</p>
	
	<p>
		<input type="submit" ng-disabled="myForm.user.$dirty && myForm.user.&invalid || myForm.email.$dirty && myForm.email.$invalid">
	</p>

</form>
<script>
	var app = angular.module('myApp',[]);
	app.controller('validateCtrl', function($scope){
		$scope.user = 'John Doe';
		$scope.email = 'John doe@gamil.com';
	});
</script>
```

HTML表单属性novalidate用于禁用浏览器默认的验证。

实例解析

- AngularJS ng-model 指令用于绑定输入元素到模型中
- 模型对象有两个属性： user和email。
- 我们使用了ng-show指令，color:red在邮件是$dirty或$invalid才显示。

* $dirty  表示表单有填写记录
* $valid  字段内容合法的
* $invalid 字段内容是非法的
* $pristine 表单没有填写记录

## demo14: AngularJS API（Application Programming Interface应用程序编程接口。）

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo14/index.html)

AngularJS 全局API用于执行常见任务的Javascript函数集合，如：

* 比较对象
* 迭代对象
* 转换对象

全局API函数使用angular对象进行访问。

以下列出了一些通用的API函数：

* angular.lowercase() 转换字符串为小写
* angular.uppercase() 转换字符串为大写
* angular.isString()  判断给定的对象是否为字符串，如果是返回true。
* angular.isNumber()  判断给定的对象是否为数字，如果是返回true。

```html
<div ng-app="myApp" ng-controller="myCtrl">
	<p>{{x1}}</p>
	<p>{{x2}}</p>
	<p>{{x3}}</p>
	<p>{{x4}}</p>
	<p>{{x5}}</p>
	<p>{{x6}}</p>
</div>
<script>
	var app = angular.module('myApp',[]);
	app.controller('myCtrl',function($scope){
		$scope.x1 = 'JOHN';
		$scope.x2 = angular.lowercase($scope.x1);
		$scope.x3 = "cynthia";
		$scope.x4 = angular.uppercase($scope.x3);
		$scope.x5 = angular.isString($scope.x1);
		$scope.x6 = angular.isNumber($scope.x3);
	})
</script>
```
## demo15: AngularJS Bootstrap

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo15/index.html)

你可以在你的AngularJS应用中加入Twitter Bootstrap,你可以在你的<head>元素中添加如下代码：
```html
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap.min.css">
```
如果站点在国内，建议使用百度静态资源库Bootstrap，代码如下：
```html
<link rel="stylesheet" href="//apps.bdimg.com/libs/bootstrap/3.3.4/css/bootstrap.min.css">
```

以下是一个完整的HTML实例，使用了AngularJS指令和Bootstrap类。
```html
<body ng-app="myApp" ng-controller="userCtrl">
	<!-- AngularJS 的首选样式表是Twitter Bootstrap -->
	<div class="container">
		<h3>Users</h3>
		<table class="table table-striped">
			<thead>
				<tr>
					<th>编辑</th>
					<th>名</th>
					<th>姓</th>
				</tr>
			</thead>
			<tbody>
				<tr ng-repeat="user in users">
					<td>
						<button class="btn" ng-click="editUser(user.id)">
							<span class="glyphicon glyphicon-pencil">编辑</span>
						</button>
					</td>
					<td>{{user.fName}}</td>
					<td>{{user.lName}}</td>
				</tr>
			</tbody>
		</table>
		<hr>
		<button class="btn btn-success" ng-click="editUser('new')">
			<span class="glyphicon glyphicon-user">创建新用户</span>
		</button>
		<hr>

		<h3 ng-show="edit">创建新用户：</h3>
		<h3 ng-hide="edit">编辑用户：</h3>

		<form action="" class="form-horizontal">
			<div class="form-group">
				<label for="" class="col-sm-2 control-label">名:</label>
				<div class="col-sm-10">
					<input type="text" ng-model="fName" ng-disabled="!edit" placeholder="名">
				</div>
			</div>
			<div class="form-group">
				<label for="" class="col-sm-2 control-label">姓:</label>
				<div class="col-sm-10">
					<input type="text" ng-model="lName" ng-disabled="!edit" placeholder="姓">
				</div>
			</div>
			<div class="form-group">
				<label for="" class="col-sm-2 control-label">密码:</label>
				<div class="col-sm-10">
					<input type="password" ng-model="passw1" placeholder="密码">
				</div>
			</div>
			<div class="form-group">
				<label for="" class="col-sm-2 control-label">重复密码:</label>
				<div class="col-sm-10">
					<input type="password" ng-model="passw2" placeholder="重复密码">
				</div>
			</div>
		</form>
		<hr>
		<button class="btn btn-success" ng-disabled="error || incomplete">
			<span class="glyphicon glyphicon-save">保存修改</span>
		</button>
	</div>

	<script src="myUsers.js"></script>
</body>
```
JavaScript代码解析

* $scope.fName  模型变量（用户名）
* $scope.IName  模型变量（用户姓）
* $scope.passw1 模型变量（用户密码 1）
* $scope.passw2 模型变量（用户密码 2）
* $scope.users  模型变量（用户的数组）
* $scope.edit   当用户点击创建用户时设置为true
* $scope.error  如果passw1不等于passw2设置为true
* $scope.incomplete  如果每个字段都为空(length = 0)设置为true
* $scope.editUser 设置模型变量
* $scope.watch 监控模型变量
* $scope.test 验证模型变量的错误和完整性

## demo16: AngularJS 动画

AngularJS 提供了动画效果，可以配合CSS使用。
AngularJS 使用动画需要引入 angular-animate.min.js 库。
动画是通过改变HTML元素产生的动态变化效果。

```html
<script src="http://cdn.static.runoob.com/libs/angular.js/1.4.6/angular-animate.min.js"></script>
```
还需在应用中使用模型 ngAnimate:
```html
<body ng-app="ngAnimate">
```
##### 勾选复选框隐藏DIV动画：

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo16/index.html)

```html
<body ng-app="ngAnimate">
	<h1>隐藏IDV：
		<input type="checkbox" ng-model="myCheck">
	</h1>
	<div ng-hide="myCheck"></div>
</body>
```
######  ngAnimate做了什么？

ngAnimate模型可以添加或移除class。

ngAnimate模型并不能使HTML元素产生动画，但是ngAnimate会监测事件，类似隐藏显示HTML元素，如果事件发生ngAnimate就会使用预定义的class来设置HTML元素的动画。

AngularJS添加/移除class的指令：

* ng-show
* ng-hide
* ng-class
* ng-view
* ng-include
* ng-repeat
* ng-if
* ng-switch

ng-show和ng-hide指令用于添加或移除ng-hide class的值。其他指令会在进入DOM时添加ng-enter类，移除DOM会添加ng-leave属性。

当HTML元素位置改变时，ng-repeat指令同样可以添加ng-move类。

此外，在动画完成后，HTML元素的类集合将被移除。例如：ng-hide指令会添加一下类：

* ng-animate
* ng-hide-animate
* ng-hide-add(如果元素将被隐藏)
* ng-hide-remove(如果元素将显示)
* ng-hide-add-active(如果元素将隐藏)
* ng-hide-remove-active(如果元素将显示)


## demo17: angularJS 依赖注入

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo17/index.html)

##### 什么是依赖注入

wiki上的解释：依赖注入（Dependency Injection,简称DI）是一种软件设计模式，在这种模式下，一个或更多的依赖（或服务）被注入（或者通过引用传递）到一个独立的对象（或客户端）中，然后成为了该客户端状态的一部分。

该模式分离了客户端依赖本身行为的创建，这使得程序设计变得松耦合，并遵循了依赖反转和单一职责原则。与服务定位器模式形成直接对比的是，它允许客户端了解客户端如何使用该系统找到依赖。

```
一句话---没事你不要来找我，有事我会去找你。
```

AngularJS 提供很好的依赖注入机制。以下5个核心组件用来作为依赖注入：
* value  是一个简单的javascript对象，用于向控制器传递值（配置阶段）
* factory 是一个函数用于返回值。在service和controller需要时创建。通常我们使用factory函数来计算或返回值。
* service
* provider AngularJS中通过provider创建一个service、factory等（配置阶段）。Provider中提供了一个factory方法get(),它用于返回value/service/factory。
* constant（常量）用来在配置阶段传递数值，注意这个常量在配置阶段是不可用的。

```html
<div ng-app = "mainApp" ng-controller = "CalcController">
 <p>输入一个数字: <input type = "number" ng-model = "number" /></p>
 <button ng-click = "square()">X<sup>2</sup></button>
 <p>结果: {{result}}</p>
</div>


<script>
 var mainApp = angular.module("mainApp", []);
 
 mainApp.config(function($provide) {
    $provide.provider('MathService', function() {
       this.$get = function() {
          var factory = {};
          
          factory.multiply = function(a, b) {
             return a * b;
          }
          return factory;
       };
    });
 });
	
 mainApp.value("defaultInput", 5);
 
 mainApp.factory('MathService', function() {
    var factory = {};
    
    factory.multiply = function(a, b) {
       return a * b;
    }
    return factory;
 });
 
 mainApp.service('CalcService', function(MathService){
    this.square = function(a) {
       return MathService.multiply(a,a);
    }
 });
 
 mainApp.controller('CalcController', function($scope, CalcService, defaultInput) {
    $scope.number = defaultInput;
    $scope.result = CalcService.square($scope.number);

    $scope.square = function() {
       $scope.result = CalcService.square($scope.number);
    }
 });
	
</script>
```

## demo18: angularJS 路由

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo18/index.html)

angularJS 路由允许我们通过不同的URL访问不同的内容。
通过AngularJS可以实现多视图的单页Web应用（single page web application, SPA)。
通常我们的URL形式为http://runoob.com/first/page，但在单页Web应用中 AngularJS 通过 # + 标记 实现，例如：

```
http://runoob.com/#/first
http://runoob.com/#/second
http://runoob.com/#/third
```
当我们点击以上的任意一个链接时，向服务端请求的地址都是一样的（http://runoob.com/）。因为#号之后的内容在向服务端请求时会被浏览器忽略掉。所以我们就需要在客户端实现#号后面内容的功能实现。AngularJS路由就通过# + 标记帮助我们区分不同的逻辑页面并将不同的页面绑定到对应的控制器上。

```html
<body ng-app="routingDemoApp">
	<h2>AngularJS路由应用</h2>
	<ul>
		<li><a href="#/">首页</a></li>
		<li><a href="#/computers">电脑</a></li>
		<li><a href="#/printers">打印机</a></li>
		<li><a href="#/blabla">其他</a></li>
	</ul>
	<div ng-view>
		
	</div>
	<script src="http://apps.bdimg.com/libs/angular-route/1.3.13/angular-route.js"></script>
	<script>
	    angular.module('routingDemoApp',['ngRoute'])
	    .config(['$routeProvider', function($routeProvider){
	        $routeProvider
	        .when('/',{template:'这是首页页面'})
	        .when('/computers',{template:'这是电脑分类页面'})
	        .when('/printers',{template:'这是打印机页面'})
	        .otherwise({redirectTo:'/'});
	    }]);
	</script>
</body>
```

## demo19: angularJS 简单应用-我的笔记

[source](https://github.com/ChengYiFan/angularJS/tree/master/demo19/index.html)

```html
<body ng-app="myNoteApp" ng-controller="myNoteCtrl">
	<h2>我的笔记</h2>
	<textarea name="" id="" cols="40" rows="10" ng-model="message"></textarea>
	<p>
		<button ng-click="save()">保存</button>
		<button ng-click="clear()">清除</button>
	</p>
	<p>剩余可输入字符个数: <span ng-bind="left()"></span></p>
	<script src="myNoteApp.js"></script>
	<script src="myNoteCtrl.js"></script>
</body>
```

##### AngularJS 应用架构

以上实例是一个完整的AngularJS单页Web应用(single page web application,SPA)。
<html>元素包含了AngularJS应用(ng-appp=)。
<div>元素定义了AngularJS控制器的作用域(ng-controller=)。
在一个应用可以有很多控制器。
应用文件(my...App.js)定义了应用模型代码。
一个或多个控制器文件(my...Ctrl.js)定义了控制器代码。

##### 总结-它是如何工作的呢？
ng-app 指令位于应用的根元素下。
对于单页Web应用(single page web application,SPA),应用的根通常为<html>元素。
一个或多个ng-controller指令定义了应用的控制器。每个控制器有他自己的作用域：：定义的HTML元素。
AngularJS在HTML DOMContentLoaded 事件中自动开始。如果找到ng-app指令，AngularJS载入指令中的模块，并将ng-app作为应用的根进行编译。应用的根可以是整个页面，或者页面的一小部分，如果是一小部分会更快编译和执行。
