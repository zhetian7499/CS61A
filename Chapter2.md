## Syntax

### 字符串和列表的区别

<img src="../../AppData/Roaming/Typora/typora-user-images/image-20220122164829336.png" alt="image-20220122164829336" style="zoom:50%;" />

**Comment**: 考虑字符串的特殊性，有时候需要检索字符串中的单词



### 奇怪的列表

```python
>>> [ ]+[1,2,3]      #列表的合并
[1, 2, 3]
>>> [ ]+[ [1,2,3] ]    #列表成为一个元素，实现二维列表     或者可以看做 “] 和 [" 被抵消
[ [1, 2, 3] ]
```



### 奇怪的sum

```python
>>>sum( [ [1], [2,3], [4] ], [ ] )
[1, 2, 3, 4]
>>>sum( [ [1] ], [ ] )
[1]
>>>sum( [ [ [1] ], [2] ], [ ] )
[ [1], 2 ]
```

![image-20220123190633306](../../AppData/Roaming/Typora/typora-user-images/image-20220123190633306.png)



### 奇怪的append和extend

```python
>>> s1=[1,2,3]
>>> s2=s1
>>> s1 is s2
True
>>> s2.extend([5,6])
>>> s1
[1, 2, 3, 5, 6]
>>> s2
[1, 2, 3, 5, 6]
>>> s1.append([-1,0,1])
>>> s1
[1, 2, 3, 5, 6, [-1, 0, 1]]
>>> s2
[1, 2, 3, 5, 6, [-1, 0, 1]]
>>> s3=s2[:]
>>> s3
[1, 2, 3, 5, 6, [-1, 0, 1]]
>>> s3.insert(3, s2.pop(3))
>>> s3
[1, 2, 3, 5, 5, 6, [-1, 0, 1]]
>>> s2
[1, 2, 3, 6, [-1, 0, 1]]
>>> s1
[1, 2, 3, 6, [-1, 0, 1]]
>>> s1[4]
[-1, 0, 1]
>>> s1[:3]
[1, 2, 3]
>>> s1[4].append(2)
>>> s1
[1, 2, 3, 6, [-1, 0, 1, 2]]
```

**Comment**: append是把括号里的元素加入列表。entend是把括号里的列表和原列表拼接。

**Eg**:

![image-20220126153117067](../../AppData/Roaming/Typora/typora-user-images/image-20220126153117067.png)

```python
#初始状态
p = [2, 3]
q = [4, [p]]
mystery(_________________, ________________________)
def mystery(p, q):
 p[1].extend(q)
 q.append(p[1:])
p = [2, 3]
q = [4, [p]]
mystery(q, p)
```



### 奇怪的默认参数值——default argument value

```python
>>> def f(s=[ ]):
...  		s.append(5)
...  		return len(s)
>>> f( )
1
>>> print(id(s))
1607004860352
>>> f( )
2
>>> print(id(s))
1607004860352
```

> A default argument value, when you define a function, is part of that function value, not generate a new everytime you call the function.

### List  Comprehensions

```python
>>> [i**2 for i in [1, 2, 3, 4] if i % 2 == 0]
[4, 16]
```

转化成 for 格式

```python
>>> lst = []
>>> for i in [1, 2, 3, 4]:
...     if i % 2 == 0:
...         lst = lst + [i**2]
>>> lst
[4, 16]
```



### List Slicing

```python
lst=[6, 5, 4, 3, 2, 1, 0]
>>> lst[::-1]   # Make a reversed copy of the entire list
[0, 1, 2, 3, 4, 5, 6]
>>> lst[::2]  # Skip every other; step size defaults to 1 otherwise
[6, 4, 2, 0]
```



### Iterable

对list、tuple、dict、等类型的数据使用for...in...的循环语法从其中依次拿到数据进行使用，这样的过程称为遍历，也叫迭代。

把可以通过for...in...这类语句迭代读取一条数据供我们使用的对象称之为**可迭代对象（Iterable）**

```python
>>> from collections import Iterable
>>> isinstance('abc',Iterable)#str是否可迭代
True
>>> isinstance([1,2,3],Iterable)#list是否可迭代
True
>>> isinstance(123,Iterable)#整数是否可迭代
False
```



### Function-min 关键字比较，返回整体

![image-20220124200112496](../../AppData/Roaming/Typora/typora-user-images/image-20220124200112496.png)



### 很好用的zip函数  import from Cat Project

```python
>>> sofar = ['how', 'are', 'you']
>>> prompt = ['how', 'are', 'you', 'doing', 'today']
	n = 0
    for t, r in zip(sofar, prompt):
        n += (t == r)
        if t!=r:
            break 
```

**Comment**: zip可以把两个列表转化为元组。上面的例子：[ ('how','how'),('are','are'),('you','you'),('doing'),('today') ]。这样可以很方便比较。



### append函数

```python
time=[ ]
time.append(3)=[3]
#otherwise  
time += [3]
```



### yield

![image-20220126215246989](../../AppData/Roaming/Typora/typora-user-images/image-20220126215246989.png)

![image-20220126215413992](../../AppData/Roaming/Typora/typora-user-images/image-20220126215413992.png)



### yield with return statement

![image-20220128133744429](../../AppData/Roaming/Typora/typora-user-images/image-20220128133744429.png)



## Abstraction Barriers

import from: http://composingprograms.com/pages/22-data-abstraction.html#:~:text=2.2.3%C2%A0%C2%A0%C2%A0Abstraction%20Barriers

![image-20220125145739262](../../AppData/Roaming/Typora/typora-user-images/image-20220125145739262.png)

**Comment**：直接传入参数 x,y。构造放在函数内部。这样如果更改构造方式，add_rational不受影响

同理，select也要放在函数内部。



## Tree

**Eg**： tree(3, [tree(1), tree(2, [tree(1), tree(1)])])

branches = [tree(1), tree(2, [tree(1), tree(1)])]

tree(label,branches)

plz get used to it, like 

```python
branches = [totals_tree(end(f(m))) for f in [left, right]]
return tree( sum( [label(b) for b in branches] ), branches)
```

 especially sum( [label(b) for b in branches])

## String Representations

**str**

对应着`print`函数打印的方法，目的是方便人类阅读

**repr**

对应着`interative python`中打印的方法，目的是方便程序阅读

```python
class Lamb:
     species_name = "Lamb"
     scientific_name = "Ovis aries"
     def __init__(self, name):
     	self.name = name
     def __str__(self):
     	return "Lamb named " + self.name
>>> str(lil)
'Lamb named Lil lamb'
>>> print(lil)
Lamb named Lil lamb
>>> repr(lil)
'<__main__.Lamb object at 0x000002535EFB6350>'
>>> lil
<__main__.Lamb object at 0x000002535EFB6350>
```



```python
class A:
     def __init__(self, x):
         self.x = x
     def __repr__(self):
         return self.x
			def __str__(self):
         return self.x * 2
class B:
     def __init__(self):
         print('boo!')
         self.a = []
     def add_a(self, a):
         self.a.append(a)
     def __repr__(self):
         print(len(self.a))
         ret = ''
         for a in self.a:
             ret += str(a)
         return ret
    
 >>> A('one')
one
>>> print(A('one'))
oneone
>>> repr(A('two'))
'two'
>>> b = B()
boo!
>>> b.add_a(A('a'))
>>> b.add_a(A('b'))
>>> b
2
aabb
```

自行实现`str`与`repr`方法：

```python
def repr(x):
    # 因为是class attribute     
    return type(x).__repr__(x)

def str(x):
    t = type(x)
    if hasattr(t, '__str__'):
        return t.__str__(x)
    else:
        return repr(x)
```

