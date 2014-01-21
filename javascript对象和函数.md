#Javascript对象和函数

Javascript 中有两个很重要的概念 对象和函数。

##1.对象
1. 对象是javascript的根本。最基本的对象是Object对象。
1. 可以通过 new Object() 或者{} 创建。


###1.1 根对象
通过 new Object 或者{}创建的对象是根对象 Object 的子对象，它的__proto__属性指向了根的Object 对象。

1. 根对象没有__proto__属性，因为他是最根部，没有父亲。
1. 他包含了javascript 最基本的几个函数，valueof tostring 等函数。

![javascript 根对象](/image/object_function/object.png)

###1.2  Array 对象
1. Array 对象常用的对象，他包含几个数组常用的方法
1. array对象有一个__proto__指向Object ，说明Array 是Object 的子对象。

![javascript 根对象](/image/object_function/array.png)

###1.3.	函数对象
1. 函数也是一种对象，创建函数 可以直接function fun1(){}也可以 new Function();
1. 函数对象根对象是 function Empty 
1. 根函数的__proto__ 指向了根对象Object。
1. 根函数 没有 prototype 属性，这个属性的用户在函数中会讲。
 
![javascript 根对象](/image/object_function/function.png)

###1.4.总结

1. javascript 不是面向对象的语言，而是基于对象的语言。
1. **对象之间通过__proto__属性来记录对象的继承关系**。
1. 关于是否需要维护这样的关系，有很多争论，这里不表。


##2.函数
1. 前面说了 函数也是一种对象，函数是一种特殊的对象，
2. Javascript 的函数分两种，非构造函数，构造函数

### 2.1非构造函数
1. 不能使用new 关键字，不能创建新的对象。不包含prototype 属性
2. 非构造函数都是系统内置函数，开发人员创建的函数构造函数。
3. 系统内置的非构造函数 例如array的concat 方法，object 的tostring方法都是非构造函数。根函数对象function Empty 也是非构造函数。

如图所示：
1. 数组的concat 函数是非构造函数，没有prototype属性，
2. concat函数的父对象Empty 函数也是非构造函数，也没有prototype属性

![javascript 根对象](/image/object_function/nonconctructor.png)

###2.2构造函数

####2.2.1	构造函数都包含prototype属性
1. 因为构造函数是用于创建新对象，创建的新对象上的__proto__ 属性需要保存父对象的引用，
2. 构造函数通过prototype 属性来保存父对象的信息。
3. 当创建新对象的时候，把创建的对象的__proto__ 属性 指向 构造函数的prototype。

    var obj = new Object();
    console.log(obj.__proto__ === Object.prototype);//true
 
####2.2.2	系统内置构造函数
- Object
- Function
- Date
- RegExp

####2.2.3	自定义函数
1. 开发人员自定义的函数全部都是构造函数。
1. 开发人员可以自定义函数，通过Function构造函数。

    var People = function(){};
    var p1= new People();


