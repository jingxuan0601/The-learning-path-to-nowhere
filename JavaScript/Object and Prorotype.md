### Reference Type  
```  
var value = "25";
var number = Number(value); //保存基本类型的值
alert(typeof number); // number
var obj = new Number(value);  // 保存number的实例
alert(typeof obj) // Object
```  
基本类型和引用类型的区别  
typeof 基本类型 // boolean  
typeof 引用类型 // object
instanceof 基本类型 // false  
instanceof引用类型  //true  

### Object  
```instanceof``` 检测对象的类型  

### Prototype
```Person.prototype.constructor === Person```   
```__proto__```   
```isPrototypeOf: Person.protptype.isPrototypeOf(Person1) === true```  
```getPrototypeOf: Object.getPrototypeOf(person1) === Person.prototype```  
```delete person1.name```delete property from object  
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




