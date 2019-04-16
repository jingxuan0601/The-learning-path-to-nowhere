- 报错的时候终止js文件的生成： 在tsconfig.json中配置 noEmitOnError

- void  
表示没有任何返回值的函数  
```  
function alertName(): void {
    alert('My name is Tom');
}
```  
只能将它赋值为 undefined 和 null  
```  
let unusable: void = undefined;
```  

- any 
在复制过程中允许改变类型  
```  
let myFavoriteNumber: any = 'seven';
myFavoriteNumber = 7;
```  
声明时未指明类型被认为是any类型 
```  
let something;
something = 'seven';
something = 7;
```

- Union Types  
```  
let myFavoriteNumber: string | number;
myFavoriteNumber = 'seven';
myFavoriteNumber = 7;
```  
不确定一个联合类型的变量到底是哪个类型的时候, 只能访问联合类型的所有类型里共有的属性或方法  
```  
function getLength(something: string | number): number {
    return something.length; // length 不是 string 和 number 的共有属性，所以会报错。
    return something.toString(); 
}
```  