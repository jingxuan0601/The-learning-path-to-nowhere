###默认参数  
尾参数  
length返回非默认参数的个数```(fucntion(a, b, c = 5){}).length === 2;```

###解构赋值  
```
function foo({x, y = 5} = {}){
	//解构赋值默认值5+函数参数默认值{}	
}
```  

###rest参数  
尾参数  
```
function add(...values) {
	let sum = 0;
	for (var val of values) {
		sum += val;
	}

	return sum;
}

add(2, 5, 3); //10

const sortNumbers = (...numbers) => numbers.sort();
function sorNumbers() {
	return Array.prototype.slice.call(arguments).sort();
}
```

###箭头函数
this在箭头函数中始终指向定义时所在的对象。而普通函数的this可变，指向使用时所在的对象