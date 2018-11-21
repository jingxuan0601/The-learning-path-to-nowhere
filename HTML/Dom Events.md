# 事件的冒泡和捕捉
#### 事件的绑定方式
```element.onclick = function() {}```
```element.addEventListener('click', function(e) {}, useCapture)```
#### 冒泡和捕捉的区别
冒泡： useCapture = true, e.eventPhase == Event.BUBBLING_PHASE
捕捉： useCapture = false, e.eventPhase == Event.CAPTURING_PHASE 
#### 事件处理的顺序
- 捕捉： 从document开始，由上至下
- 冒泡： 从触发元素开始，由下至上
- dom事件流： 捕捉 -> 冒泡
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
#### 终止事件流
```e.stopPropagation()```
如果在捕捉阶段终止，将会跳过未处理的捕捉， 以及目标和冒泡

