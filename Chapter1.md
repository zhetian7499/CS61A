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
>>> True and 0      //0是False，输出0
0
>>> True and False
False
>>> 0 and True
0
>>> 1 and 3 and 6 and 10 and 15
15
>>> -1 and 1 > 0
```

