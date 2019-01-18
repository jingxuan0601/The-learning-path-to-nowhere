# 解构赋值  
###数组的解构赋值  
```let [a, b, c] = [1, 2, 3];```  
```let [headr, ...tail] = [1, 2, 3, 4]; //header = 1, tail = [2, 3, 4]```  
```let [x, y, ...z] = [1]; //x = 1, y = undefined, z = []```  

###不完全解构   
```let [x, y] = [1, 2, 3]; //x = 1, y = 2```  
```let [a, [b],  d] = [1, [2, 3], 4]; // a = 1, b = [2], c = 4```  

###默认值  
只有undefined会让默认值生效  
```let [x, y = 'b'] = ['a', undefined]; //x = 'a', y = 'b'```  
```let [x, y = 'b'] = ['a', null]; //x = 'a', y = null```  

###对象的解构赋值  
```let { foo, bar } = { foo: "aaa", bar: "bbb" };``` 

###字符串的解构赋值  
```const [a, b, c, d, e] = 'hello';```  

###函数参数的解构赋值  
```[[1, 2], [3, 4]].map(([a, b]) => a + b);```  

# 数组的扩展运算  
```array.push(...items)```  
