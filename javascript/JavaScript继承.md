# JavaScript 继承

javascript 发展历史

1. 借鉴了c的语法 new
1. 借鉴了java的数据类型和内存回收 Number Date String 
1. 借鉴了schema的函数作为一等公民 function
1. 借鉴了Self语言的原型继承。prototype
    
new使他看起来像是面向对象，但是这是假象，new的内部还是基于原型实现的。

>什么是继承？
>为什么要继承？
>面向对象和基于对象的语言的区别？
>



###一：理解 new 运算符

	function A1(){
		this.name ="A1";	
	}
	
	var a1 = new A1();
	aa1 = A1();
	
	alert(a1 instanceof A1); //true
	alert(aa1); //undefined;

从上面的程序了解 new A1() 和直接A1()返回结果不同，为什么？

这个就需要了解new的执行过程。

	1.创建一个对象obj
	2.设置obj的__proto__指向构造函数的prototype
	3.把构造函数的this指向obj，并调用构造函数
	4.如果构造函数有返回值,则返回构造函数的返回值，否则返回刚才创建的对象。

如下代码

	function newClass(cls,args){  
		//1.创建一个对象obj
	    var obj = {};  
		//2.设置obj的__proto__指向构造函数的prototype
	    obj.__proto__ = cls.prototype;  
		//3.把构造函数的this指向obj，并调用构造函数
	    cls.apply(obj,args||[]);  
		//4：如果构造函数有返回值,则返回构造函数的返回值，否则返回刚才创建的对象。
		if(cls()){
			return cls();
		}
	    return obj;  
	};  
	
	//测试

	function A1(){	
	}
	
	var a1 = new A1();
	alert(a1 instanceof A1); //true

	var a2 = newClass(A1);
	alert(a2 instanceof A1); //true

	function A2(){
		return {};	
	}
	
	var aa1 = new A2();
	alert(a1 instanceof A2); //false

	var aa2 = newClass(A2);
	alert(a2 instanceof A2); //false
	//因为A2有返回值，所以直接返回一个空对象，这个空对象的__proto__指向了根对象，没有指向
	//A2的prototype属性，所以aa1 和aa2 都不是A2的实例

	
###二：理解prototype 属性

	function Human(){
			
	}
	Human.prototype.age = 20;

	var h1 = new Human();
	var h2 = new Human();

	console.log(h1.age);
	console.log(h2.age);
	
	Human.prototype.age = 30;
	
	console.log(h1.age);
	console.log(h2.age);
	
	//结果
	20
	20
	30
	30
	//1.prototype从字面理解为【原型类型】
	//2.构造函数都包含原型类型，保证生成的对象都能够找到自己的类型。
	//3.new的过程中，设置__proto__指向构造函数的原型引用。
	//4：所以对原型的更改会影响到所有对象。

###三：理解Object.create


	//根据传入的原型对象创建新对象

	Object.create= function(o){
		function F(){};
		F.prototype = o;
		return new F();
	}