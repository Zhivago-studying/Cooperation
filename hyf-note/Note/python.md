# python
## 基础语法

1. **注释**

```python
# 单行注释  

"""多行注释
   多行注释
   多行注释""" 

# TODO:  待完成注释
```

2.  **基操**  

```print()```  
```input()```  #只能获取字符串，需要强转为所需类型

3. **强转**  

```int()``` 强转int  
```float()``` 强转float  
```str()``` 强转str  

4. **运算符**  
```\\```除法取整  
```**``` 幂运算

5. **字符串**
```python
"字符串"+"字符串"+字符串变量 # 字符串拼接，不能和数字拼接  
"字符串 %s , %d, %m.nf" %(变量名, 变量名,变量名) # n表示精确到小数点后几位    
print(f"字符串{变量名}") #直接插入字符串或数字
```

6. **判断**
```python
if 条件:
    语句,为真时执行
elif 条件:
    语句,为真时执行
else :
    语句,为假时执行
```

7. **循环**
```python
while 条件:
    语句
    break #跳出循环

for 变量 in 列表:
    语句
    continue #跳出本次循环

for 变量 in range(开始, 结束, 步长):
    语句
```

8. **函数**
```python
def 函数名(参数,参数):    #参数不需要指定类型
    函数体
    return 返回值        #可以没有返回值，即返回None  
```

9. **列表**
```python
list = ["hyf",99,TRUE,[1,hh]]   #定义
list[0]
list.append(元素) #添加
list.remove(元素) #删除
del list[下标] #删除
list.extend(列表) #将列表元素添加到列表中
list.insert(下标,元素) #在指定位置插入元素
a = list.pop(下标) #取出指定位置的元素,原list中删除
list.sort() #排序
list.clear() #清空
list.count(元素) #统计元素个数
list.index(元素) #查找元素位置
len(list) #获取长度
```

10. **元组**
```python
tuple = ()  #小括号定义
#其他的跟那个列表一样
```

11. **字符串**
```python
str = "字符串"
str2 = str.replace("原字符","新字符") #将原字符串中所有目标字符替换为指定字符
list = str.split("分割字符") #将字符串以分割字符分割成列表,不含分割字符
str = str.strip(字符串) #去除字符串首尾空格或换行符，或指定字符串中的所有字符
```

12. **序列切片**
```python
# 列表 元组 字符串 都叫序列
list = [1,2,3,4,5,6,7,8,9]
list2 = list[1:5:2] #切片，从1到5，不包含5,步长为2
#切片不改变数据类型
```

13. **集合**

```python
# 无序，不重复
set = {1,2,3,4,5,6,7,8,9}
set.add(元素)
set.remove(元素)
set3 = set1.difference(set2) #取到set1和set2的对称差集
set3 = set1.difference_update(set2) #取set1\set2的集合
set3 = set1.union(set2) #取到set1和set2的并集
```

14.  **字典**

```python
dict = {"key1": "value1", "key2": "value2"} #定义,左键右值，是键到值的映射，访问以键作下标
dict.keys() #获取全部的key
for key in dict:   #遍历字典
```

15.  **数据容器通用操作**

```python
len(container)#获取容器长度
container.clear() #清空容器
container.max() container.min() #获取最大值和最小值
#关键字强转容器类型
sorted(container,[reverse = True]) #排序,true为倒序,并转成列表类型
```

16.  **函数多返回值的接收**
```python
def func(): 
    return a,b  #返回多个值
x, y = func() #多个变量分别接收
```

17.  **函数传参**
```python
func(name = "hyf",age = 3) #键值对传参，不用管顺序，若有位置参数，必须在前面
def func(name,age = 3) #默认参数必须在最后
def func(*args) #可变参数，可接受多个参数，以元组形式接收
def func(**kwargs) #可变关键字参数，可接受多个参数，以字典形式接收，传入键值对
```

18. **函数作为参数**
```python
def func(computer): #定义一个函数，参数为函数，即运算逻辑
    return computer(1,2) #函数的运算数据是确定的
def add(a,b):     #定义运算逻辑
    return a+b
print(func(add)) #调用函数，传入函数名

def func(lambda x,y:x+y)  # lambda 匿名函数，一次性使用
```

19. **文件读取操作**
```python
f = open("文件路径","r") #打开文件，r为只读，w为写，a为追加，b为二进制，t为文本，默认为文本.其中w会覆盖原文件，a会在文件末尾追加内容。
f.read(n) #读取全部内容,若有n，则读取n个字符
f.readline() #读取一行
f.readlines() #读取全部内容，以行为单位，列表形式返回
for i in f:  # 遍历每一行
f.close()  #关闭文件

with open("文件路径","r") as f: #with语句自动关闭文件
```

20. **文件写入操作**
```python
f = open("文件路径","w")
f.write("写入内容") #内容写入内存
f.flush() #刷新内存，写入文件(磁盘)，当f.close()关闭文件时，也会刷新内存
```

21. **异常捕获**
```python
##异常有传递性，可以在函数调用的顶层捕获，也可以在函数内部捕获
try: 
    语句 #可能发生异常的语句
except: #捕获所有异常,或者用 except Exception as e: 
    语句 #异常处理语句
else: #没有异常时执行
    语句 
finally:  #无论是否发生异常都会执行
    语句

except 异常类型 as e: #捕获特定类型异常，作为异常对象e
    语句
 
except (异常类型1,异常类型2) as e: #捕获多个异常类型
```

22. **导入模块**
```python
import 模块名 #导入模块
模块名.函数名() #调用函数
from 模块名 import 函数名 #导入模块中的函数
from 模块名 import * #导入模块中的所有函数
import 模块名 as 别名 #导入模块，并给模块起别名
from 模块名 import * #导入模块中的所有函数(“所有”由__all__决定)
```

23. **__main__之作用**
```python
if __name__ == "__main__": #当模块被直接运行时，__name__为__main__,当模块被导入时，__name__为模块名
__all__ = ["函数名1","函数名2"] #__all__定义模块中包含的函数，导入模块时，只导入__all__中定义的函数,在模块中定义，是一个列表。不过可以手动导入
```

24. **包 Package**
```python
# 有__init__.py文件的文件夹，就叫包，里面很多模块,__init__.py文件可以不写，但必须存在
import 包名.模块名 #导入包中的模块,一般不直接导入包
```

## 面向对象的编程
1. **类**
```python
class 类名:
    属性 = None
    def 方法名(self, 参数):  #必须有self 参数，但调用时不用传，self 代表当前对象
    def __init__(self,参数): #构造方法，在创建对象时自动调用,一般直接把属性给赋上
```

2. **魔术方法**
```python
class 类名:
    def __str__(self): #返回打印对象或转字符串输出的内容
    def __lt__(self,other): #定义对象比较的方法，le带等号，eq比相等，其他一样
        return self.属性 < other.属性  #一般只比较小于
```

3. **私有属性**
```python
class 类名:
    __属性 = None #私有属性,只能在类内部访问
    def __方法名(self): #私有方法，只能在类内部访问
```

4. **继承**
```python
class 类名(父类): #继承父类,父类中的属性和方法都可以直接使用
class 类名(父类1,父类2): #继承多个父类,左边优先级高
# pass 占位符，表示空语句，不做任何事情，一般用在需要执行语句的位置，但不执行任何操作
#复写父类属性方法，可以覆盖父类中的
父类名.成员变量
父类名.成员方法(self)  #子类中调用已被复写的父类方法
super().成员变量 
super().成员方法() #调用父类方法，不用带self
```

5. **变量类型的注释**
```python
var_1 : int = 1 #变量类型注释
stu : Student = Student()
list_1 : list = [1,2,3] #或详细注释 list_1 : list[int] = [1,2,3]
tuple_1 : tuple = (1,2,'a',True) #或详细注释 tuple_1 : tuple[int,int,str,bool] = (1,2,'a',True)
dict_1 : dict = {'a':1,'b':2} #或详细注释 dict_1 : dict[str,int] = {'a':1,'b':2}
def func(a:int,b:str)->float: #函数参数及返回值类型注释

##法二
var_1 = 1 # type : int
stu = Student() # type : Student
list_1 = [1,2,3] # type : list[int]

##法三
from typing import Union  #导入Union联合类型 
list_1 : list[Union[int,str]] = [1,2,'a'] #在Union中选一个
dict_1 : dict[str,Union[int,str]] = {'a':1,'b':'a'}
```

6. **抽象类与多态**
```python
class 抽象类名: #抽象类，不能实例化，只能被继承
    def 方法名(self): #抽象方法，子类必须实现
        pass

class 子类名(抽象类名): #子类必须复写实现抽象类中的抽象方法
    def 方法名(self): #复写抽象方法

def 函数名(参数:抽象类名): #函数形参为抽象类名，但实际传入子类对象
```

7. **装饰器**
```python 
#装饰器后面紧跟的函数，即被装饰
@classmethod #类方法，不需要实例化，直接通过类名调用
```

8. **迭代器、生成器**
```python
#作用是节省内存，当需要生成大量数据时，使用生成器，生成器是一个特殊的迭代器，可以生成序列，但生成器函数中不能使用return语句，只能使用yield语句
def countdown(n):
    while n > 0:
        yield n
        n -= 1
 
# 创建生成器对象
generator = countdown(5)
 
# 通过迭代生成器获取值
print(next(generator))  # 输出: 5
print(next(generator))  # 输出: 4
print(next(generator))  # 输出: 3
 
# 使用 for 循环迭代生成器
for value in generator:
    print(value)  # 输出: 2 1
