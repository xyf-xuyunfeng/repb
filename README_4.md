## 流行框架第二天

## 反馈
  - 可否先给课程大纲？ 
  
  - 有需要联网的，可不可以提前说一下，让我们先下载。
    + postman : 可以帮助我们发请求。
 
  - 上课老师的声音有点不清楚 - 爱谁谁

  - 关于代码出错
    -  

  - 双向数据绑定是什么？求解
    + 解： 这个我们昨天没有讲？
    + ng-model

  - 执行原理
  - 控制器


## 点名回答问题
  - ng-app:入口.只会解析ng-app所在标签及其他子标签。
  - ng-click:注册点击事件.
  - ng-model:获取文本框的值,与文本框的值进行了绑定。
  - ng-init:初始数据模型。
  - ng-controller:指定一个控制器来管理页面的数据模型。
  - MVC Model,View,Controller

### Angular VS jQuery
  - jquery: 库
      - 封装了一些常用的方法，我们主动的去调用它

  - angular:
      - 提高一些规则或者模式。
      - 我们按照这种规则去写代码。
      - 框架自动帮助执行相应的操作.

  - 插件就是在框架或者库的基础上扩展了一些功能.

  思想上:
    jquery: 提高了dom操作的效率。
    NG : 不提倡dom操作，不是没有dom操作，它底层也一定是操作dom。
      - 即使要操作dom也不要使用jquery（尽量不要操作）,angular单独提供了
      一个轻量的jquery, angular.element() ,也叫做jqLite
  
 
### 复习并总结Angular开发流程

  - 0.下载包:npm /bower /手动下载,jspm,nuget,cdn(扩展)
  - 1.引包，引入angular.js文件
  - 2.在html中加上ng-app，表示我们ng-app所在标签及其子标签需要被angular管理
  - 3.在js中创建一个模块`angular.module('mApp',[]);`,写完成之后需要在ng-app属性值上加上这个名字`ng-app="myApp"`
  - 4.在js中创建控制器,`app.controller('demeControler',function($scope){})`,
   写守之后需要在页面加上ng-controller指令，指定一个名字，就是我们的控制器的名字.
  - 5.初始化数据模型的值,$scope,ng-model,{{}},ng-click等等配合使用。
  - 6.建模()
  - 7.写一些其他的代码()。


### 复习MVC
- MVC是一种设计思想,它是约定了程序的结构应该是怎么,不是设计模式。
- 每一个组成原件都会有一个明确的职责。
- 提高代码的结构和可维护性(代码的执行效率肯定是不会提高的，10行代码，会分到10个不同的方法。);

### 双向数据绑定
   - 指的是文本框的值改变会导致数据数据模型值的改变($scope的属性)
     数据模型的值的改变会导致页面文本框的值的改变，这种相互影响的关系，我们称之为双向数据绑定(双边数据绑定)
   - ng-model 
    + ng-model是写在value值的这些标签上，不能够写在span这些标签。

### 单向数据绑定
  - 如果，表达式的值，只能由数据模型的值的改变，导致表达式值的改变，表达在页面输出的值不能改变，所以不能够反过来改变数据模型的值。


### $scope

- 视图和控制器之间的数据桥梁
- 用于在视图和控制器之间传递数据
- 用来暴露数据模型（数据，行为）

![$scope](./scope.png)

### ViewModel
  - MVVM 
    + M Model
    + V View
    + VM(ViewModel) ，在angular中指的就是$scope
    + 提到MVVM就要想到双向数据绑定

- $scope 实际上就是MVVM中所谓的VM（视图模型）
- 正是因为$scope在Angular中大量使用甚至盖过了C（控制器）的概念，所以很多人（包括我）把Angular称之为MVVM框架
- 这一点倒是无所谓，具体看怎么用罢

### 表达式
{{name}}

## 模块

### 模块的创建

### 模块的划分式

#### 1.根据项目中具体的功能去划分模块
  - 一个功能就是一个模块，模块中需要使用的文件都放在一个文件夹中。

#### 2.根据具体的文件功能的类型去划分模块
  - app.controller,新建文件夹controllers ,所有的控制器都放在这里
  - app.directive, 所有的自定义指令都放到一个文件夹中。
  - ...;

## 控制器的创建方式

### 传统的方式创建控制器(不推荐使用这种方式)
  - angular会将全局的函数当作控制器来使用，使用的方式就是我们之前一样
  - 我们不再需要创建模块了。

### 面向对象的方式创建控制器

  ```html
    <!-- 这里直接在控制器名后加上 as 关键字 ，关键字后面加上一个名字，就表示我们angular new出来的控制器第二个参数的function对象 -->
    <div ng-controller="demoController as obj">
          {{name}}
          {{obj.age}}
          {{obj.name}}
        </div>
        <script src="node_modules/angular/angular.js"></script>
        <script>
          // 1.创建模块
          var app = angular.module('myApp',[]);

          // 2.创建控制器
          // 在这里 ，我们可以把第二个参数的function当作构造函数来使用
          app.controller('demoController',function($scope){
              this.age=18;

              $scope.name="小明";
          })
        </script>
  ```

### 安全的创建控制器的方式
- 原因：angular在控制器的回调函数中是通过参数名来传递参数的。
- 通过将第二个参数改为数据组：数据的最后一个参数还是原来的fucntion,数据前的参数是我们想要anuglar传递的参数的字符串形式，fucntion里的参数需要与数组前面的元素一对应。

`app.controller('demoController',['$scope','$log',function($scope,$log){}])`

- 以不便的东西来应对变化的东西.


### 依赖注入的原理
- 核心是toString()
- 获取函数形参的方式
  + 通过function的toString()可以得到它的形参。


### angular常用指令

- 在 AngularJS 中将前缀为 ng- 这种属性称之为指令，其作用就是为 DOM 元素调用方法、定义行为绑定数据等
- 简单说：当一个 Angular 应用启动，Angular 就会遍历 DOM 树来解析 HTML，根据指令不同，完成不同操作。
  
  - ng-bind指令:可以用来解决表达式闪烁问题，其实是利用了浏览器不会显示属性的特性。
    + 示例:`<div ng-bind="name"></div>`
    + 是把对应的数据模型显示到所在标签的innerHTML位置.
    +　必须是双标签才能够使用ng-bind指令。
  
  - ng-cloak指令：也可以用来解决表达式闪烁问题，它是利用了angular在解析表达式之后会移除页面上所有ng-cloak的样式的特性，我们在一开始让这个类样式的display为none;
    + 示例: `<div class="ng-cloak">{{name}}</div>`
    + 这个指令是写在class属性值位置。

  - ng-repeat指令：用来渲染数据列表，渲染数组，可以根据数据内容遍历输出指令所在元素。不是只可以加是li标签上，加在其他元素上都可以。
    + 示例: <ul><li ng-repeat="item in data">{{item.name}}</li></ul>
    + 这里ng-repeat使用的是类似于forin语法，这里的item是相当于一个变量，data是数据模型。
  
  - ng-class指令：用来操作样式式,相当于从一个对象是取一个属性值,一次只能取到一个样式.
    + 示例：<ul><li  ng-repeat="item in data" ng-class="{'A':'red','B':'grenn'}[item.salary]"></li></ul>
    + ng-class不是只能和ng-repeat配合，在其他元素上也能够使用。
    + 这里相当于从多种样式中选择一个。

  - ng-class指令: 从多个中选择多个?
    + 示例:<ul><li ng-class="{'red':true,'txt':true}"></li></ul>
    + 当ng-class对的属性值这个对象的属性值为true时，对应的属性名就会被当作class样式名添加到class属性中。
  
  - ng-show指令,表示当前元素是否显示。当它的值为true时，会显示当前元素，为false时会隐藏当前元素。
  - ng-hide指令，功能与ng-show相反。
  - ng-if 指令与ng-show功能类似，只不过，不它值为true时，会显示当前元素，为false时会移除当前元素。

  - ng-switch :可以类比成switch case

### 其他常用指令
- ng-checked:
  + 单选/复选是否选中,ng-model双向数据绑定，ng-checked是单向
- ng-selected：// 单向
  + 是否选中
- ng-disabled：
  + 是否禁用
- ng-readonly:
  + 是否只读

### 常用事件指令

不同于以上的功能性指令，Angular还定义了一些用于和事件绑定的指令：

- ng-blur：//失去焦点事件
- ng-focus：// 获取焦点事件 
- ng-change：// 文本值改变事件
- ng-copy：// 复制事件
- ng-click：// 单击事件  ng-click="add()"
- ng-dblclick：//双击事件 
- ng-submit: // 表单提交

### 指令的标准使用方式
data-ng-xxx,在使用angular指令时，只需要在原先的指令前加上data-前缀。
x-



### CDN (扩展)
  - 1.减轻带宽压力
  - 2.能够根据不用地区由不同的服务器返回数据
  - 3.利用浏览器对静态资源缓存的策略。
  http://cdn.code.baidu.com/
  http://www.bootcdn.cn/

  https://github.com/Wox-launcher/Wox/releases
  http://www.getwox.com

  https://pan.baidu.com/s/1mhN0boc#path=%252FWox-v1.3.183
    + 这个地址里的都要安装(除了everything,只要安装一个)