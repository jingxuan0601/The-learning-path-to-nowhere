### String     
```str.title()``` 每个单词的首字母大写     
```str.upper()```     
```str.lower()```     
```str.rstrip()``` 删除字符串左边开始的空白     
```str.lstrip()``` 删除右边结尾的空白     
```str.strip()``` 删除两头的空白     
     
```3 ** 2``` 平方     
```str(num)``` 数字转成字符串     
```int(str)``` 字符串转成数字     
```3 / 2``` 整数相除得到省略小数位的整数，只有包含浮点的除法才得到浮点     

### Array     
```arr.append()``` 将元素加到列表的结尾     
```arr.insert(index, element)``` 插入元素     
```del arr[index]``` 删除某个位置的元素     
```arr.pop()``` 删除列表结尾的元素     
```pop(index)``` 删除某个位置的元素， 返回删除的该元素（与del的区别）     
```arr.remove(value)``` 删除第一个值为value的元素     
```arr.sort()``` 按字母顺序排列     
```arr.sort(reverse=True)``` 倒序排列     
```sorted(arr)``` 返回顺序的数组，但并不改变数组本身     
```arr.reverse()``` 反转数组     
```list(range(startIndex, endIndex, step))``` 返回range内的数字数组     
```min(arr)``` 找到数组的最小值     
```max(arr)```     
```do something for value in arr``` 列表解析     
```ele in arr``` 特定值是否在列表中     
```for ele in arr:``` 遍历，不要忘了最后的冒号     
```arr[inclusiveStartIndex``` : exclusiveEndIndex] 数组切片     
```a = arr[:]``` 复制列表     
```if arr``` 判断列表是否为空     

### 元组 - 不可修改元组的元素     
```dimensions = (d1, d2)``` 列表用方括号，元组用圆括号表示     

```and``` &&     
```or``` ||     

### Dictionary     
```dic = {key: value}```     
```del dic['key']```     
```for key, value in dic.item()：``` 遍历字典     
```for key in dic.keys()：```  or  for key in dict     
```for key in sorted(dict.keys())：```  顺序遍历所有键     
```for value in dict.values()：```     
```for value in set(dict.values())：``` 遍历所有不重复的值     

### if
```
if
elif 
elif 
else   
# 当if判断超过两个，用elif。执行第一个符合判断的语句并跳过剩下的判断     
# else可以省略，只用elif     
# 如果要执行所有符合条件的语句，不用elif，而用多个独立的if语句     
```

```input("message")``` 中止程序等待用户输入    
### while     
```while ...:```     

### Function     
```
def func():     
	"""comments"""    
	...
func()     
```     
```
def func(para1, para2=val): # 参数默认值， 等号左右不要有空格  
	...     
func(para1 = val1, para2=val2) # 关键字实参， 等号左右不要有空格        
```     
```   
def func(*paras) # 接受任意数量的参数
	for para in paras
		...
```   
···   
def func(para1, para2, **paras)  # 接受任意数量的键值对参数
	for key, value in paras.items()  
		...  
func(val1, val2, key1 = val3, key2 = val4)  
```  
```   
import module_name  # 引入模块module_name.py
module_name.func()  
```  
```    
from module_name import func1, func2 # 引入模块中的特定函数   
func1() 
```
``` 
import module_name as mn
from modlue_name import func1 as f1 # 当前模块有名字冲突时给模块和函数重命名   
```
``` from module_name import * ``` 导入模块中所有函数   

### Class   
```
class c():
	#  每当创建新实例时，python都会自动运行__init__   
	def __init__(self, para)： # self是指向实力本身的引用，让实例能够访问类中的属性和方法
	# 属性必须声明
	# 如果没有参数赋值，属性必须在_inti()里初始化     
```
##### 继承   
```   
class Father():
class Child(Father):  
	def __init__(self, para)： 
		super().__init__(para)
```   
``` from modeul_name import class_name ``` 导入类    
``` from collections impor OrderedDict``` 导入python标准库    




