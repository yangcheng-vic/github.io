
# 课程介绍

## 课程大纲

> [](http://naotu.baidu.com/file/5bcd79bc4f1eaf83f96d1ad23baab345?token=d22135c63546f5ee)

![课程大纲](./media/xmind.png)

## 学习目标

- 理解面向对象开发思想
- 掌握 JavaScript 面向对象开发相关模式
- 掌握在 JavaScript 中使用正则表达式

## 案例演示

[贪吃蛇案例](./snake/index.html)

## 学习资源

- JavaScript 高级程序设计（第三版）
  + 前端的红宝书
  + 建议每一个前端都完整的看一遍
- JavaScript面向对象编程指南（第2版）
- JavaScript面向对象精要
- JavaScript 权威指南
- JavaScript 语言精粹
- 你不知道的 JavaScript

---

# 基本概念复习

> 由于 JavaScript 高级还是针对 JavaScript 语言本身的一个进阶学习，所以在开始之前我们先对以前所学过的 JavaScript 相关知识点做一个快速复习总结。
>

## 基础复习

+ 变量
  + 定义变量的语法
    + 只能是字母、数字、`_`、`$`组成，且不能以数字开头
    + 区分大小写
    + 不能是关键字和保留字
+ 数据类型
  + 基本数据类型
    + string
    + number
    + boolean
    + undefined
    + null
  + 复杂数据类型
    + Object
    + Function
    + Array
    + Date
    + 基本包装类型：Number、String、Boolean
+ 类型检测
  + typeof(基本数据类型)
  + instanceof(复杂数据类型)
+ 类型转换
  + 转换成字符串类型
  + 转换成数值类型
  + 转换成布尔类型
+ 运算符
  + 算术运算符：`+ - * / % ++ --`
  + 赋值运算符：`= += -= *= /= %=`
  + 一元运算符：`++ --`
  + 比较运算符：`== === != >= <=`
  + 逻辑运算符：`&& || !`
+ 流程控制语句
  + 分支语句；
    + if..else
    + switch..case
  + 循环语句：
    + while循环
    + do..while循环
    + for循环
    + for..in循环
    + break与continue
+ 数组
  + 索引和长度
  + 赋值与取值
  + 遍历
+ 函数
  + 声明与调用
  + 参数与返回值
  + 预解析
  + 作用域
  + 匿名函数
  + 回调函数
  + 自调用函数
+ 对象
  + 对象的定义
  + 赋值与取值
  + 遍历
+ 内置对象
  + Array
  + Math
  + Date
  + String
  + Number
  + Boolean
  + auguments

## typeof关键字

`typeof`操作符返回一个**字符串**,返回的是操作数的类型

+ `typeof 基本类型`返回的是字符串
+ `typeof 对象` 返回的是object


+ `typeof 函数` 返回的是function
+ `typeof null` 返回的object


## 逻辑中断

&&：从左到右的顺序进行判断，如果发现某个操作数的逻辑判断是false，那么就不用继续判断了。

```javascript
function animate(fn){
  fn();//如果直接调用fn，当参数fn没有传递时会报错。
  fn && fn();//如果fn的逻辑判断是true，那么才会执行第二个操作数，即fn();
}
```



||：从左到右的顺序进行判断，如果发现某个操作数的逻辑是true，那么就不用继续判断了。

```javascript
//如果能够通过window.pageYOffset获取到值，那么就不用继续往后获取了，如果获取不到，那么就通过html标签的scrollTop去获取，否则就通过body的scrollTop去获取。
var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0;
```

## 比较运算符

==运算符只比值，不比类型（类型会发生隐式转换）

===运算符，既比值，也比类型

==比较运算符的转换规则：

```javascript
1. NaN不等于任何值,包括NaN本身
2. null不等于任何值，除了null和undefined
3. undefined不等于任何值，除了undefined和null
4. 如果操作符两边有数字，那么两边都转换成数字进行比较。
5. 如果操作符两边有布尔类型，那么两边都转换成数值进行比较。
6. 如果操作符有字符串，那么两边都转换成字符串比较。
7. 如果两边都是对象，那么直接比地址（引用）。
```

## 值类型与引用类型

值类型：简单类型，变量在存储的时候，存储的是值本身。

引用类型：复杂类型，变量在存储的时候，存储的是对象的地址。

+ 值类型与引用类型（画图说明）

```javascript
var num = 10;

var obj = {
  name:"zs",
  age:18
}

var people = {
  name:"zs",
  age:18,
  car:{
    brand:"forever",
    color:"green"
  }
}
```

+ 值类型与引用类型赋值特征（画图说明）

值类型赋值的时候，把值进行赋值

引用类型赋值的时候，赋值的是地址。

```javascript
var num1 = 10;
var num2 = num1;
num2 = 99;
console.log(num1);
console.log(num2);

var obj1 = {
  name:"zs",
  age:18
}
var obj2 = obj1;
obj2.name = "ls";
console.log(obj1.name);
console.log(obj2.name);
```

+ 值类型与引用类型参数传递（画图说明）

```javascript
var num = 10;
function fn(a) {
  //var a = num;
  a = 99;
  console.log(a);
}
fn(num);  //  
console.log(num);


var obj = {
  name:"zs",
  age:18
}
function fn(a) {
  //var a = obj;
  a.name = "ls";
  console.log(a.name);
}
fn(obj);
console.log(obj.name);
```

## 浅拷贝与深拷贝

> 深拷贝与浅拷贝只针对于复杂数据类型。

推荐资源：[javaScript中浅拷贝和深拷贝的实现](https://github.com/wengjq/Blog/issues/3)

浅拷贝：将对象中的各个属性依次进行复制，浅拷贝只复制了一层对象的属性。如果对象属性中还有对象，那么赋值的仅仅是地址。还是会相互影响。

深拷贝：将对象中的各个属性一次进行复制，深拷贝会递归赋值所有层对象的属性。如果对象属性中还有对象，会继续拷贝，这样拷贝出来的对象完全独立。

```javascript
function cloneObj(obj) {
  //如果不是对象，不拷贝
  if (typeof obj !== "object") {
    return;
  }
  var temp = {};
  for (var k in obj) {
    //如果对象的属性是复杂类型，递归复制
    //如果对象的属性是简单类型，直接复制
    temp[k] = typeof obj[k] === "object" ? cloneObj(obj[k]) : obj[k];

  }
  return temp;
}
```

---

# 面向对象编程

<img src="./media/mxdxkf.png" width="400" alt="">

## 基本概念

### 什么是对象？

> Everything is object （万物皆对象）

<img src="./media/20160823024542444.jpg" alt="">

对象到底是什么，我们可以从两次层次来理解。

**(1) 对象是单个事物的抽象。**

一本书、一辆汽车、一个人都可以是对象，一个数据库、一张网页、一个与远程服务器的连接也可以是对象。当实物被抽象成对象，实物之间的关系就变成了对象之间的关系，从而就可以模拟现实情况，针对对象进行编程。

**(2)对象是无序属性的集合，其属性可以包含基本值、对象或者函数**

每个对象都是基于一个引用类型创建的，这些类型可以是系统内置的原生类型，也可以是开发人员自定义的类型。

### 什么是面向对象？

面向对象编程 —— Object Oriented Programming，简称 OOP ，是一种编程开发思想。
它将真实世界各种复杂的关系，抽象为一个个对象，然后由对象之间的分工与合作，完成对真实世界的模拟。

在面向对象程序开发思想中，每一个对象都是功能中心，具有明确分工，可以完成接受信息、处理数据、发出信息等任务。
因此，面向对象编程具有灵活、代码可复用、高度模块化等特点，容易维护和开发，比起由一系列函数或指令组成的传统的过程式编程（procedural programming），更适合多人合作的大型软件项目。

面向对象与面向过程：

- 面向过程就是亲历亲为，事无巨细，面面俱到，步步紧跟，有条不紊，面向过程是解决问题的一种思维方式，关注点在于解决问题的过程。
- 面向对象就是找一个对象，指挥得结果，解决问题的思维方式，关注点在解决问题的对象上。
- 面向对象将执行者转变成指挥者
- 面向对象不是面向过程的替代，而是面向过程的封装

面向对象的特性：

- 封装性
  - 将功能的具体实现，全部封装到对象的内部，外界使用对象时，只需要关注对象提供的方法如何使用，而不需要关心对象对象的内部具体实现，这就是封装。
- 继承性
  - 在js中，继承的概念很简单，一个对象没有的一些属性和方法，另外一个对象有，拿过来用，就实现了继承。
  - **注意：在其他语言里面，继承是类与类之间的关系，在js中，是对象与对象之间的关系。**
- [多态性]
  - 多态是在强类型的语言中才有的。js是弱类型语言，所以JS不支持多态。

## 创建对象的方式

### 内置构造函数创建

我们可以直接通过 `new Object()` 创建：

```javascript
//在js中，对象有动态特性，可以随时的给一个对象增加属性或者删除属性。
var person = new Object()
person.name = 'Jack'
person.age = 18

person.sayName = function () {
  console.log(this.name)
}
```
缺点：麻烦，每个属性都需要添加。

### 对象字面量创建

```javascript
var person = {
  name: 'Jack',
  age: 18,
  sayName: function () {
    console.log(this.name)
  }
}
```
缺点：如果要批量生成多个对象，应该怎么办?代码很冗余

### 简单改进：工厂函数

我们可以写一个函数，解决代码重复问题：

```javascript
function createPerson (name, age) {
  return {
    name: name,
    age: age,
    sayName: function () {
      console.log(this.name)
    }
  }
}
```
然后生成实例对象：

```javascript
var p1 = createPerson('Jack', 18)
var p2 = createPerson('Mike', 18)
```
缺点：但却没有解决对象识别的问题，创建出来的对象都是Object类型的。

### 继续改进：构造函数

构造函数是一个函数，用于实例化对象，需要配合new操作符使用。

```javascript
function Person (name, age) {
  this.name = name
  this.age = age
  this.sayName = function () {
    console.log(this.name)
  }
}

var p1 = new Person('Jack', 18)
p1.sayName() // => Jack

var p2 = new Person('Mike', 23)
p2.sayName() // => Mike
```

而要创建 `Person` 实例，则必须使用 `new` 操作符。
以这种方式调用构造函数会经历以下 4 个步骤：

1. 创建一个新对象
2. 将构造函数的作用域赋给新对象（因此 this 就指向了这个新对象）
3. 执行构造函数中的代码
4. 返回新对象



构造函数的作用：实例化对象

new的作用：创建对象，调用构造函数，返回对象。

**构造函数需要配合new操作符使用才有意义，构造函数首字母都需要大写**

### 构造函数的缺点

使用构造函数带来的最大的好处就是创建对象更方便了，但是其本身也存在一个浪费内存的问题：

```javascript
function Person (name, age) {
  this.name = name
  this.age = age
  this.type = 'human'
  this.sayHello = function () {
    console.log('hello ' + this.name)
  }
}

var p1 = new Person('lpz', 18)
var p2 = new Person('Jack', 16)
console.log(p1.sayHello === p2.sayHello) // => false
```


解决方案：

```javascript
function sayHello = function () {
  console.log('hello ' + this.name)
}

function Person (name, age) {
  this.name = name
  this.age = age
  this.type = 'human'
  this.sayHello = sayHello
}

var p1 = new Person('lpz', 18)
var p2 = new Person('Jack', 16)

console.log(p1.sayHello === p2.sayHello) // => true
```
缺点：会暴漏很多的函数，容易造成全局变量污染。



## 原型

### 原型基本概念

Javascript 规定，每一个构造函数都有一个 `prototype` 属性，指向另一个对象。
这个对象的所有属性和方法，都会被构造函数的实例继承。

这也就意味着，我们可以把所有对象实例需要共享的属性和方法直接定义在 `prototype` 对象上。

```javascript
function Person (name, age) {
  this.name = name
  this.age = age
}

console.log(Person.prototype)

Person.prototype.type = 'human'

Person.prototype.sayName = function () {
  console.log(this.name)
}

var p1 = new Person(...)
var p2 = new Person(...)

console.log(p1.sayName === p2.sayName) // => true
```

这时所有实例的 `type` 属性和 `sayName()` 方法，
其实都是同一个内存地址，指向 `prototype` 对象，因此就提高了运行效率。

### 构造函数、实例、原型三者之间的关系

构造函数：构造函数就是一个函数，配合new可以新建对象。

实例：通过构造函数实例化出来的对象我们把它叫做构造函数的实例。一个构造函数可以有很多实例。

原型：每一个构造函数都有一个属性`prototype`,这个属性就叫做原型属性。通过构造函数创建出来的实例能够直接使用原型上的属性和方法。

<img src="./media/构造函数-实例-原型之间的关系.png" alt="">

思考：内置对象中，有很多的方法，这些方法存在哪里？

### `__proto__`

通过构造函数创建的对象，自带一个`__proro__`属性，这个属性指向了构造函数的prototype属性，也就是原型对象。

获取原型对象：

+ 通过`构造函数.prototype`可以获取
+ 通过`实例.__proto__`可以获取（隐式原型）
+ 它们指向了同一个对象`构造函数.prototype === 实例.__proto__`



**注意：`__proto__`是浏览器的一个隐藏（私有）属性，早期的IE浏览器不支持，不要去修改它，如果要修改原型中的内容，使用构造函数.prototype去修改**

### constructor属性

默认情况下，原型对象中值包含了一个属性：constructor，constructor属性指向了当前的构造函数。

![sanjiao](media\sanjiao.png)

## 原型链

### 属性查找原则

如果是获取操作

1. 会先在自身上查找，如果没有
2. 则根据`__proto__`对应的原型去找，如果没有
3. 一直找到`Object.prototyp`，如果没有，那就找不到了。

如果是修改操作：

只会修改对象自身的属性，如果自身没有这个属性，那么就会添加这个属性，并不会修改原型中的属性。

### 原型链概念

任何一个对象，都有原型对象，原型对象本身又是一个对象，所以原型对象也有自己的原型对象，这样一环扣一环就形成了一个链式结构，我们把这个链式结构称为：原型链。

绘制对象的原型链结构：

```javascript
//1. var p = new Person();
//2. var o = new Object();
//3. var arr = new Array();
//4. var date = new Date();
//5. Math
//6. 查看一个div的原型链结构
```

总结：Object.prototype是原型链的尽头，Object.prototype的原型是null。

![](media/proto.png)





### Object.prototype成员介绍

+ hasOwnProperty

`hasOwnProperty()` 方法会返回一个布尔值，指示对象是否具有指定的属性作为自身（不继承）属性。

```javascript
var obj = {
  name:"zs"
}
//判断name属性是不是obj自己提供（非继承）的
console.log(obj.hasOwnProperty("name"));//true
console.log(obj.hasOwnProperty("toString"));//false
```

思考：hasOwnProperty与in的区别？

in操作符：如果属性不是自己提供的，是从原型上继承来的，也会返回true

hasOwnProperty: 该属性必须是自己提供，才返回true，否则返回false。

```javascript
for..in的优化
```



+ isPrototypeOf

`isPrototypeOf()` 方法用于测试一个对象是否存在于另一个对象的原型链上。

```javascript
//判断A对象爱是否在B对象的原型链上。
//返回值：true，在原型链上    false：不在原型链上。
A.isPrototetypeOf(B);
```

+ propertyIsEnumerable

`propertyIsEnumerable()` 方法返回一个布尔值，表明指定的属性名是否是当前对象可枚举的自身属性。

```javascript
//1. 判断这个属性能不能被遍历(必须是自己的属性）。
obj.propertyIsEnumerable(prop);
```

+ toLocaleString/toString

`toString()` 方法返回一个表示该对象的字符串。格式：[object Object],内置对象都重写了toString方法。

`toLocaleString()` 方法返回一个该对象的字符串表示。该方法主要用于被本地化相关对象覆盖。



+ valueOf

`valueOf()` 方法返回指定对象的原始值。

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf

### instanceof运算符

`instanceof` **运算符**用来测试一个对象在其原型链中是否存在一个构造函数的 `prototype` 属性。作用和isPrototypeOf类似

语法： 实例对象 instanceof 构造函数

返回值：检测构造函数的prototype属性是否在实例对象的原型链上。

+ A.isPrototypeOf(B)  判断A是否在B的原型链上                          A： 是一个原型对象
+ B instanceof A         判断A的prototype是否在B的原型链上     A：是一个构造函数

面试题：

```javascript
function Person(){

}

var p = new  Person();
console.log(p instanceof Person);

//需要画图
Person.prototype = {};
var p1 = new Person();
console.log(p instanceof Person);
console.log(p1 instanceof Person);
```

---

# 案例：贪吃蛇

---

# 继承

> 继承：子承父业

在js中的继承概念非常简单，拿来主义：一个对象自己没有的属性和方法，另一个对象有，拿过来使用，就实现了继承。

继承的目的：让一个对象可以使用另一个对象的属性和方法。

## 混入式继承（mixin）

```javascript
function extend (obj1, obj2){
  for(var k in obj2){
    obj1[k] = obj2[k];
  }
}
```

## 原型式继承

一个对象可以访问构造函数的原型中的属性和方法，那么如果想要让一个对象增加某些属性和方法，只需要把这些属性和方法放到原型对象中即可。这样就实现了继承。

+ 直接给原型增加属性和方法
+ 原型替换（注意：constructor）
+ mixin+原型


## 经典继承

ES5中新增了一个方法`Object.create()`,方法会使用指定的原型对象及其属性去创建一个新的对象。

```javascript
//参数：proto 一个对象
//返回值：obj 新对象，新对象的原型就是proto
var obj = Object.create(proto);
console.log(obj);
```

---



# 函数进阶

## 定义函数（三种）

### 函数声明

```javascript
function fn(){
  
}
```

### 函数表达式

```javascript
var fn = function() {
  
}
```

函数声明与函数表达式的区别：

+ 函数声明会提升，因此可以先调用，后声明
+ 函数表达式只会将函数名提升，所以只能在赋值后调用函数。

### 构造函数Function

```javascript
//函数也是对象，可以new出来。
//var fn = function(){}
var fn = new Function();

//语法：new Function(arg1,arg2,arg3..,body);
// 前面可以定义任意多个形参，最后一个参数是代码体。
// 所有的参数都是字符串类型。
var fn = new Function("alert(1111)");
fn();

var fn1 = new Function("a1", "a2", "alert(a1+a2)");
fn1(1,2);
```



特殊技巧：可以将一个字符串转换为代码执行。与eval类似

```javascript
var str = "var num = 1; num++; alert(num)";
var fn = new Function(str);
fn();


//直接把字符串当成js代码执行
eval(str);
```



eval的使用：

+ 执行字符串代码
+ 将json字符串转换成JS对象

注意：eval函数的功能非常的强大，但是实际使用的情况并不多。

- eval形式的代码难以阅读
- eval形式的代码无法打断点，因为本质还是还是一个字符串
- 在浏览器端执行任意的 JavaScript会带来潜在的安全风险，恶意的JavaScript代码可能会破坏应用



## 完整版原型链

只要是函数，就有prototype属性

只要是对象，就有`__proto__属性`

函数也是对象，因此函数既有prototype属性，又有`__proto__`属性。

所有的函数都是Function的实例，因此 `函数.__proro__ === Function.prototype`

![](media/function.png)

完整版原型链结构

```javascript
function Person(){

}
var p = new Person();
```

![](media/all.png)

## Function.prototype成员介绍

+ name：用于获取函数的名字
+ length属性：用于获取形参的个数
+ arguments：用于获取实参列表。
+ caller:废弃了，用于获取当前在函数是在哪个函数中调用的。如果在全局中被调用，返回null

## 作用域与作用域链

### 全局作用域与函数作用域

> 作用域：变量起作用的区域

全局作用域：变量在script标签内，函数外定义

函数作用域：变量在函数内部定义

在js中，除了全局作用域，只有函数能够产生作用域，每一个函数内部声明的变量和函数，对于外部来说都是透明的。

```javascript
var num = 11;//全局变量
function fn(){
  var num2 = 22;//局部变量
  console.log(num);
  console.log(num2);
}
```

### 词法作用域

词法作用域：它决定了一个变量（标识符）在哪里和如何被查找。

编程语言中，作用域规则主要分为两种类型：

+ 动态作用域
+ 词法作用域（静态作用域）

js采用的是词法作用域规则：

词法作用域也叫静态作用域，变量在声明的时候，它的作用域就定下来来了，与运行时无关。变量的作用域只跟函数的声明有关，与函数的调用无关。

```javascript
var num = 123;
function f1() {
  console.log(f1);
}

function f2(){
  var num = 456;
  f1();
}

f2();//打印啥？
```

词法作用域的查找规则：

1. 先在函数内找局部变量，包括形参。
2. 如果找不到，去定义该函数的作用域中寻找（与函数的调用无关）
3. 以此类推，直到全局作用域。

### 预解析

js代码执行分为两个步骤：

1. 预解析（提升）
2. 代码一行一行执行

预解析阶段：javascript解析器会把所有的变量声明和函数声明提升到当前作用域的最顶部。对于`var a = 11;`这么一条语句，其实会分为两部分：`var a;`和` a =11;`，其中`var a;`会被提升。

提升规则：

+ 提升以作用域为单位。


+ 优先提升函数function，然后才提升变量var。
+ 重复的var提升会被忽略。
+ 重复的function声明会被覆盖。

**推荐：不要在一个作用域内重复的声明相同的变量和函数**

```javascript
//1----------------------
function foo() {
  var num = 123;
  console.log(num);
}
foo();
console.log(num);

//2--------------------
var scope = "global";
function foo() {
  console.log(scope); 
  var scope = "local";
  console.log(scope); 
}
foo();

//3-------------
if ("a" in window) {
  var a = 10;
}
alert(a);

//4---------
var foo = 1;
function bar() {
  if (!foo) {
    var foo = 10;
  }
  alert(foo); 
}
bar();
```

### 作用域链

## call apply bind

## 递归函数

## 函数闭包

# 正则表达式

## 创建正则表达式

## 元字符

## 正则匹配

## 正则替换

## 正则提取

