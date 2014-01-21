#Javascript对象和函数

Javascript 中有两个很重要的概念 对象和函数。

##一.对象
> *  对象是javascript的根本。最基本的对象是Object对象。
> *  可以通过 new Object() 或者{} 创建。

### 1. 根对象
通过 new Object 或者{}创建的对象是根对象 Object 的子对象，它的__proto__属性指向了根的Object 对象。
根Object 对象的特点
>1：根对象没有__proto__属性，因为他是最根部，没有父亲。
>2：他包含了javascript 最基本的几个函数，valueof tostring 等函数。

 
1.2.	Array 对象
Array 对象常用的对象，他包含几个数组常用的方法，array对象有一个__proto__指向Object ，说明Array 是Object 的子对象。
 

1.3.	函数对象
函数也是一种对象，创建函数 可以直接
function fun1(){}
也可以 
new Function();
函数对象根对象是 function Empty 
 根函数的__proto__ 指向了根对象Object。
 根函数 没有 prototype 属性，这个属性的用户在函数中会讲。
 
1.4.	通过__proto__属性来记录对象的继承关系。
2.	函数
前面说了 函数也是一种对象，函数是一种特殊的对象，但是函数有特点： 函数可以运行，返回结果，也可以创建新对象。
Javascript 的函数分两种，非构造函数，构造函数


特点	非构造函数	构造函数
能够创建对象	不能	能
是否包含prototype	不包含	包含

2.1.	非构造函数
非构造函数：不能使用new 关键字，不能创建新的对象。
非构造函数都是系统内置函数，开发人员创建的函数构造函数。
系统内置的非构造函数，例如array的concat 方法，object 的tostring方法都是非构造函数。
 

非构造函数的特点
1：不包含prototype 属性
2：不能使用 new 关键字
根函数对象function Empty 也是非构造函数。

2.2.	构造函数

构造函数都有一个特点：都包含 prototype 属性。

2.2.1.	为什么构造函数都有prototype？
	因为构造函数是用于创建新对象，创建的新对象上的__proto__ 属性需要保存父对象的引用，
所以构造函数通过prototype 属性来保存父对象的信息，当创建新对象的时候，把创建的对象的__proto__ 属性 指向 构造函数的prototype。

var obj = new Object();
console.log(obj.__proto__ === Object.prototype);

 
Obj的__proto 
 
2.3.	系统内置构造函数
2.3.1.	Object
对象
2.3.2.	Function
函数
2.3.3.	Date
日期
2.3.4.	RegExp
正则表达式

2.4.	自定义函数
开发人员自定义的函数全部都是构造函数。
开发人员可以自定义函数，通过Function构造函数。
var People = function(){};
var p1= new People();


