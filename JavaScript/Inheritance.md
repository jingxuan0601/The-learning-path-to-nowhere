####依靠原型链实现继承  
``` 
	function SuperType()｛
		this.property = true;
	}
	SuperType.prototype.getSuperValue = function {
		return this.property;
	};
	function SubType() {
		this.subProperty = false;
	}
	SubType.prototype = new SuperType(); //将一个类型的实例指向另一个构造函数的原型
	SubType.prototype.getSubValue = function() {
		return this.subProperty;
	}
	var instance = new SubType();
	alert(instance.getSuperValue()); //return true;
	alert(instance.getSubType()); //return false;
```  

#####instanceof
```
	alert(instance instanceof Object); //true
	alert(instance instanceof SuperType); //true
	alert(instance instanceof SubType); //true
```    

#####isPrototypeOf
```
	alert(Object.prototype.isPrototypeOf(instance)); //true
	alert(SuperType.prototype.isPrototypeOf(instance)); //true
	alert(SubType.prototype.isPrototypeOf(instance)); //true
```   

#####单纯依靠原型链实现继承的问题
1. reference property:
``` 
	function SuperType() {
		this.colors = [...];
	}
	function SubType() {}
	SubType.prototype = new SuperType(); //SubType的原型指向SuperType的实例，因此reference type的colors在SubType.prototype上被所有SubType的实例共享了
``` 
2. 不能向超类型的构造函数传递参数

####constructor stealing + prototype
```
	function SuperType(name) {
		this.name = name;
		this.colors = [];
	}
	SuperType.prototype.sayName = function(){
		alert(this.name);
	};
	function SubType() {
		//1. 传递参数
		//2. call()/apply()调用SuperType的constructor,从而继承SuperType实例上的property
		SuperType.call(this, name) ;
	}
	SubType.prototype = new SuperType(); //继承原型链上的方法，从而实现方法重用
``` 

#####原型式继承  Object.create()
``` 
var person = {
	name="Nocholas",
	friends=['Shelby', "court", "Van"];
};
var anotherPerson = Object.create(person); //以person为原型创建了对象实例。因此friends在这些对象实例中共享
anotherPerson.friends.push("Rob");
var yetAnotherPerson = Object.create(person);
anotherPerson.friends.push("Barble");
alert(person.friends)； //'Shelby', "court", "Van"，"Rob"，"Barble"
```