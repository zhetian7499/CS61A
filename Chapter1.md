#### 1.2.6![image-20220114162954909](Chapter1.assets/image-20220114162954909.png)

print 是一个none pure function

> **Non-pure functions.** In addition to returning a value, applying a non-pure function can generate *side effects*, which make some change to the state of the interpreter or computer. A common side effect is to generate additional output beyond the return value, using the `print` function.

**Ex**

![img](Chapter1.assets/function_print.png)

So 

> **Pure functions.** Functions have some input (their arguments) and return some output (the result of applying them). The built-in function



#### 1.3.7 Operator

```python
>>> from operator import truediv, floordiv
>>> truediv(5, 4)
1.25
>>> floordiv(5, 4)
1
```

#### 1.5.4 Boolean

and 和 or，左右两者都为真/假时，输出右边

**Ex**:

```python
>>> 13 and True
True
>>>0 or False
False
>>>False or 0
0
>>> True and 0      
0
>>> True and False
False
>>> 0 and True
0
>>> 1 and 3 and 6 and 10 and 15
15
>>> -1 and 1 > 0
```



**Textbook**

Python 还包括**布尔运算符** `and`、`or`和`not`。这些运算符用于组合和操作布尔值。

- `not`返回以下表达式的相反布尔值，并且总是返回`True`or `False`。
- `and`按顺序计算表达式并在达到第一个假值时停止计算（短路），然后返回它。如果所有值都计算为真值，则返回最后一个值。
- `or`按顺序计算表达式并在第一个真值处短路并返回它。如果所有值的计算结果都是假值，则返回最后一个值。

例如：

```
>>> not None
True
>>> not True
False
>>> -1 and 0 and 1
0
>>> False or 9999 or 1/0
9999
```

#### 1.6.7 Lambda Expression

#### ![image-20220115104244302](../../AppData/Roaming/Typora/typora-user-images/image-20220115104244302.png)

#### 1.6.4 Function as Returned Values

**Ex1**

```python
def make_adder(n):
    """Return a function that takes one argument K and returns K + N.
    >>> add_three = make_adder(3)
    >>> add_three(4)
    7
    """
    def adder(k):
        return k + n
    return adder

make_adder(2000)(20)  # currying：transformation from function(f, g) to function(f)(g)
```

![img](https://pic3.zhimg.com/v2-7df82807c3996057858f616ea66e926a_b.jpg)



**Ex2**

```python
def make_adder(n):
    def adder(k):
        return k + n
    return adder
​
def square(x):
    return x * x
​
def triple(x):
    return 3 * x
​
def compose1(f, g):
    def h(x):
        return f(g(x))
    return h
​
squiple = compose1(square, triple)
squiple(5)
>>> 225
​
tripare = compose1(triple, square)
tripare(5)
>>> 75
​
squadder = compose1(square, make_adder(2))
squadder(3)
>>> 25
​
compose1(square, make_adder(2))(3) //与squadder(3)等价
>>> 25
```



**Ex3**

import from "Hog" project

![image-20220117205803761](../../AppData/Roaming/Typora/typora-user-images/image-20220117205803761.png)

**comment**：关键在于 f 要返回了一个描述当前 leader 的对象。而这个对象又可以进一步用来比较。最终给出的解决方案是：返回一个函数，这个函数的参数是 leader ，并把比较函数 say 包含了进去，使得 say 可以引用 leader 。

另外的理解：每次f比较好两个数，然后把这两个数据更新到自己的函数参数（可以看作返回了一个announce，也可以看作返回了一个say，只不过say借了announce的一个壳，利用了它的参数）





