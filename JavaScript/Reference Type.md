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
