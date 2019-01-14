###创建对象的模式   
####factory   
```
	function createPerson(name, age, job) {
		var o = new Object();
		o.name = name;
		o.age = age;
		o.job = job;
		o.sayName = function() {
			alert(this.name);
		};
		return o;
	}
	var person1 = createPerson(...);
```

####constructor pattern  
``` 
	function Person(name, age, job) {
		...
		o.sayName = function() {
			alert(this.name);
		};
	}
	var person1 = new Person(...);
```  
problem: 以sayName function为例，每个实例（person1, person2）上都有sayName方法的实例，且他们不是指向同一个sayName   
改进：   
```
	function Person(...) {
		this.sayName = sayName;
	}
	function sayName() {
		alert(this.name);
	}
```  
problem: 尽管现在sayName定义在全局上，其scope并不全局，而只能为Person的object所用。且假如有多个这样的需求，将会有很多个这样的全局方法。  

####prototype pattern  
```  
	function Person() {
	}
	Person.prototype.name = "";
	person.prototype.sayName = function() {
		alert(this.name);
	};
	var person1 = new Person();
```  
每个prototype属性是一个指针  
```Person.prototype.constructor === Person```    
```__proto__```   
```isPrototypeOf: Person.protptype.isPrototypeOf(Person1) === true```  
```getPrototypeOf: Object.getPrototypeOf(person1) === Person.prototype```  
```delete person1.name```delete property from object

#####区分object上的property和prototype上的property  
```hasOwnProperty: person1.hasOwnProperty("name")``` 判断property存在于object还是prototype，true-存在object上，false-存在prototype上  
```in: property in object``` 只要能从object上访问到property就返回true，因此无论property在object上还是prototype上都返回true。 因此hasOwnproperty和in结合起来可以判断property在object上还是object上  
```for property in object```枚举object和prototype上的properties  
```Object.keys(), Object.getPropertyNames()```  
```  
function Person() {}
# 使用对象字面量重写prototype时，constructor不再指向Person，而指向新对象的construcot属性，which is Object
Person.prototype = {
	...
	constructor: Person #重设constructor会将enumerable成true
}
Object.defineProperty(Person.prototype, "constructor", {
	enumerable: false, 
	value: Person
});

```    
```
var person1 = new Person();
Person.prototype.name = ""; # 在person1的声明后面修改prototype，person1仍能获取新的属性
Person.protytype = {}; # 但如果重写了prototypt,person1.prototype仍然指向原来的prototypt
```   

#####constructor + prototype  
reference type的property放在Object上，用constructor初始化，不在实例之间共享。其他property放在prototype上  
```
	function Person(...) {
		this.friends = [...];
	}
	Person.prototype = {
		constructor: Person,
		sayName: function() {
			alert(this.name);
		};
	}
```   
 
#####dynamic prototype pattern
把所有信息都封装在构造函数中，通过检测某个方法是否有效来决定是否把方法声明在prototype上  
```
	function Person(...) {
		...
		if (typeof this.sayName != "function") {
			Person.prototype.sayName = function() {
				alert(this.name);
			};
		}
	}
```




