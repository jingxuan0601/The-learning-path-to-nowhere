每个函数对象都是Function类型的实例，而函数名实际上是指向函数对象的指针    
### 函数的定义  
#### 函数声明  
```  
function func(para1, para2) {
	...
}  
```  
#### 函数表达式  
```  
var func = function(para1, para2) {
	...
};
```   
#### 函数声明和函数表达式的区别  
compiler会先通过function declaration hoisting把所有的函数声明提升到代码顶部，先读取函数声明，使其在任何执行代码之前可以使用。而函数表达式必须等到compiler执行到它所在行才会被释放执行。     
```   
alert(func(1, 2));
function func(para1, para2) { //函数声明尽管在alert之后，仍然可以保证alert顺利执行。但如果替换成函数表达式就会发生错误 
	...
}
```   

### arguments, this, callee   
#### arguments   
类数组对象，包含传入函数的所有参数   
#### arguments.callee  
指针，指向拥有arguments对象的函数
```   
function factorial(num) {
	if (num <= 1) {
		return 1;
	}
	 else {
	 	return num * factorial(num - 1); // 函数和factorial这个函数指针是紧密耦合的，假如factorial指向了另一个函数，原来这个函数的执行将会受到影响。
	 	return num * arguments.callee(num - 1); // 用 argument.callee解除耦合，保证不论引用函数时使用的什么名字，都能完成正确的递归调用  
	 }
}
```   
#### this   
this指向函数的执行环境对象   
#### this.caller   
调用当前函数的函数引用  
```   
function outer() {
	inner();
}

function inner() {
	alert(arguments.callee.caller) 
}

outer() //打印outer函数的源代码  
```   
### 函数的其他属性和方法  
#### length  
表示函数希望接受的命名参数的个数  
#### prototype   
不可枚举，不可用for-in  
#### apply(), call()  
设置函数体内this对象的值，扩充函数赖以生存的作用域  
apply和call传入的第一个参数都是this  
区别：apply的第二个参数是参数数组，可以是arguments,也可以是Array的实例；而call必须明确的传入每一个参数   
```   
function sum(num1, num2) {
	return nums1 + num2;
}

function callSum(num1, num2) {
	return sum.apply(this, arguments);
	return sum.apply(this, [num1, num2]);
	return sum.call(this, num1, num2);
}
```   
```   
window.color = "red";
var o = {color: "blue"};
function sayColor() {
	alert(this.color);
}

sayColor();  // red
sayColor().call(this) // red, this is window
sayColor().call(window) //red
sayColor().call(o) // blue, 使用apply()或者call()来扩充作用域最大的好处是对象和方法直接不需要有任何的耦合关系   

o.sayColor = sayColor();
o.sayColor() // blue, 如果不用call()，就只能先把sayColor()放入对象o中，然后再通过o来调用它的sayColor()   
```   
#### bind()  
创建一个函数的实例，其this值会被绑定到传给bind()函数的的值  
```  
var objectSayColor = sayColor.bind(o);
objectSayColor(); //blue, this is o
```
