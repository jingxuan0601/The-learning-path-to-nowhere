## Events

#### 冒泡和捕捉的区别
冒泡： useCapture = true, e.eventPhase == Event.BUBBLING_PHASE   
捕捉： useCapture = false, e.eventPhase == Event.CAPTURING_PHASE   

#### 事件流的顺序    
捕获capturing阶段（从上到下，不包括target） ->  event target（其实是bubbling阶段的一部分） ->  冒泡bubbling  

#### 终止事件流  
```e.stopPropagation()```    
如果在捕捉阶段终止，将会跳过未处理的捕捉， 以及目标和冒泡  

#### 事件的绑定方式
```element.onclick = function() {}```   
```element.addEventListener('click', function(e) {}, useCapture)```  
- handler里的this === target element.this === e.target.this  

##### addEventListner, removeEventListener  
- removeEventListener的第三个boolean参数： true- capturing, false- bubbling  
- 同一元素上既有冒泡又有捕捉，按照代码顺序  
```  
<div id="div1">
	<div id="div2"></div>
</div>

div1.addEventListener("click", function() {...}, false); 
div2.addEventListener("click", function() {...}, true); // catch event
div2.addEventListener("click", function() {...}, false); // bubble event
// 处理顺序： div2 catch -> div2 bubble -> div1
```  
- add和remove时传入的参数应该相同，所以匿名函数不可以被remove  
```  
button.addEventListener("click", function() {
	alert(this.id);
});
button.removeEventListener("click", function() {
	alert(this.id); 
}, false); // doesn't work
``` 

#### Event Type
- load, DomContentLoaded(dom tree is ready, before external sources load), unload, beforeunload(confirmation dialog..)  
- mouse event
  - coordinator  
    - clientX, clientY- 浏览器view下的坐标  
    - pageX, pageY- 页面坐标， ```e.pageX === e.clientX + (document.body.scrollLeft)```  
    - screenX, screenY- 整个屏幕下的坐标
- key  
  - 修改键  
    - e.shiftKey
    - e.ctrlKey
    - e.altKey
    - e.metaKey
  - keydown -> keypress -> keyup, keypress(键入有效字符的时候触发)  
  - e.keyCode, e.charCode, e.textInput, e.inputMethod  

#### Dangling event handler
- 用dom操作移除element后，垃圾回收其handler, eg: 
```
<div id="div">
	<input type="button" value="Click Me" id="button"></input>
</div>
document.getElementById('button').onclick = function() {   // usually used to disable double click  
	button.onclick = null; // 在删除element之前垃圾回收它的event handler
	document.getElementById('div').innerHTML = "Processing..." // set div's innerHTML to remove button  
};
```  
- 在onunload里移除所有的event handler


