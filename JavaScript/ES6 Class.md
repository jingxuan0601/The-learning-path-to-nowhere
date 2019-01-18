###Class语法糖  
类的所有方法都定义在类的prototype上
实例属性都定义在实例的prototype上

###static方法 
1. 静态方法直接在类上调用```Foo.baz()```
2. 静态方法可以和非静态方法重名
3. 父类的静态方法可以被子类继承
```
class Foo {
	static bar() {
		this.baz();
	}

	static baz() {
		console.log("hello");
	}
	baz() { //静态方法可以和非静态方法重名
		console.log("hello");
	}
}
Foo.baz(); // 'hello' 在类上直接调用静态方法
var foo = new Foo(); foo.baz(); // error: 在类的实例上调用静态方法报错

Class ChildFoo extends Foo() {
	static baz() {
		return super.baz() + ', too'; //子类继承父类的静态方法，用super调用父类的静态方法
	}
}
```  

###私有方法   
```
class widget {
	foo(baz) {
		bar.call(this, baz);
	}
}
function bar(baz) { //移出模块
	return this.snaf = baz; 
}
```

###Class继承  
1. 子类的constructor必须调用super.constructor, 因为ES6的继承机制是先将父类实例对象的属性和方法放到this上，再用子类的构造函数修改this  
2. Object.getPrototypeOf从子类获取父类```Object.getPrototypeOf(ColorPoint) === Point```    
 
####Super     
super作为函数调用，代表父类的构造函数，但this指向子类。在子类的constructor中执行  
super作为对象，  
	在普通方法中指向父类的原型对象，super调用父类的方法时方法内部的this指向当前子类的实例  
	在静态方法中指向父类而不是父类的原型对象。this指向子类
	不能通过super调用父类实例的方法和属性。

