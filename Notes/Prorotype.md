### prototype + constructor实现继承  
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
##### hasOwnproperty + in区分object上的property和prototype上的property  
```hasOwnProperty: person1.hasOwnProperty("name")``` true- on object，false-on prototype   
```in: property in object``` true- on object or on prototype   

