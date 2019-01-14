### Object   
```var obj = new Object();```    
```var obj = {key: value};```   

### Array  
```var arr = new Array(length);```  
```var arr = Array(length);``` 省略new   
```var arr = [1, 2]```  

#####length  
可以通过length属性来增加或删除数组元素  

#####检测数组   
```arr instanceof Array```  
```Array.isArray(arr)```  

#####Stack  
Array + push(增加到数组末尾) ＋ pop(从数组末尾删除)  

#####Queue  
Array + push + shift(从数组开头删除) 

#####数组排序  
```sort((val1, val2) => return val2 - val1);```  
```reverse();```倒排  

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
