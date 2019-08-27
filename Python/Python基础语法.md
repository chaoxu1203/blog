# Python基础语法

http://cs231n.github.io/python-numpy-tutorial/

https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014318650247930b1b21d7d3c64fe38c4b5a80d4469ad7000

Python是动态语言。

这种变量本身类型不固定的语言称之为*动态语言*，与之对应的是*静态语言*。静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错 



## 数据类型

### 变量

变量名必须是大小写英文、数字和`_`的组合，且不能用数字开头 。

等号`=`是赋值语句，可以把任意数据类型赋值给变量，同一个变量可以反复赋值，而且可以是不同类型的变量 （由于是动态语言）。

### 数据类型转换

`int(x)`可以将x转换为int型，`str(x)`可以将x转换为string型，还有float等。其他类型转换同理。

### 输入

使用 `input()`可以从终端获取输入，获得的类型是str。

### 空值

空值是Python里一个特殊的值，用`None`表示。 

### 除法

在Python中，有两种除法，一种除法是`/`：

```
>>> 9 / 3
3.0
```

`/`除法计算结果是浮点数，即使是两个整数恰好整除，结果也是浮点数。

还有一种除法是`//`，称为地板除，两个整数的除法仍然是整数：

```
>>> 10 // 3
3
```

也称为取整除。

## 条件控制

### 循环

Python支持break、continue等控制语句。

## 编码

### 中文显示

当源代码中包含中文的时候，就需要指定保存为UTF-8编码：

```python
# -*- coding: utf-8 -*-
```

### 字符编码

把Unicode编码转化为“可变长编码”的`UTF-8`编码。UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，常用的英文字母被编码成1个字节，汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节。如果你要传输的文本包含大量英文字符，用UTF-8编码就能节省空间。UTF-8编码有一个额外的好处，就是ASCII编码实际上可以被看成是UTF-8编码的一部分。

### 格式化

在Python中，采用的格式化方式和C语言是一致的，用`%`实现，举例如下：

```python
>>> 'Hello, %s' % 'world'
'Hello, world'
>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
'Hi, Michael, you have $1000000.'
```

如果只有一个`%`，括号可以省略。 

如果你不太确定变量是什么类型，`%s`永远起作用，它会把任何数据类型转换为字符串 

## String

String是不可变数据类型

## List

List是可变有序数据类型

### 多类型支持

```python
xs = [3, 1, 2]    # Create a list
xs[2] = 'foo'     # Lists can contain elements of different types
print(xs)         # Prints "[3, 1, 'foo']"
xs.append('bar')  # Add a new element to the end of the list
print(xs)         # Prints "[3, 1, 'foo', 'bar']"
x = xs.pop()      # Remove and return the last element of the list
print(x, xs)      # Prints "bar [3, 1, 'foo']"
```

### 切片

```python
nums = list(range(5))     # range is a built-in function that creates a list of integers
print(nums)               # Prints "[0, 1, 2, 3, 4]"
nums[2:4] = [8, 9]        # Assign a new sublist to a slice
print(nums)               # Prints "[0, 1, 8, 9, 4]"
```

### 循环

```python
animals = ['cat', 'dog', 'monkey']
for animal in animals:
    print(animal)
# Prints "cat", "dog", "monkey", each on its own line.

# 内建的enumerate函数可以同时列举下标和值
animals = ['cat', 'dog', 'monkey']
for idx, animal in enumerate(animals):
    print('#%d: %s' % (idx + 1, animal))
# Prints "#1: cat", "#2: dog", "#3: monkey", each on its own line
```

### 高级操作

```python
nums = [0, 1, 2, 3, 4]
squares = [x ** 2 for x in nums]
print(squares)   # Prints [0, 1, 4, 9, 16]


nums = [0, 1, 2, 3, 4]
even_squares = [x ** 2 for x in nums if x % 2 == 0]
print(even_squares)  # Prints "[0, 4, 16]"
```

## Dictionaries

可变数据类型

### 基本

```python
d = {'cat': 'cute', 'dog': 'furry'}  # Create a new dictionary with some data
print(d['cat'])       # Get an entry from a dictionary; prints "cute"
print('cat' in d)     # Check if a dictionary has a given key; prints "True"
d['fish'] = 'wet'     # Set an entry in a dictionary
print(d['fish'])      # Prints "wet"
# print(d['monkey'])  # KeyError: 'monkey' not a key of d
print(d.get('monkey', 'N/A'))  # Get an element with a default; prints "N/A"
print(d.get('fish', 'N/A'))    # Get an element with a default; prints "wet"
del d['fish']         # Remove an element from a dictionary
print(d.get('fish', 'N/A')) # "fish" is no longer a key; prints "N/A"
```

### 循环

```python
d = {'person': 2, 'cat': 4, 'spider': 8}
for animal in d:
    legs = d[animal]
    print('A %s has %d legs' % (animal, legs))
# Prints "A person has 2 legs", "A cat has 4 legs", "A spider has 8 legs"

# 同时获取key和value
d = {'person': 2, 'cat': 4, 'spider': 8}
for animal, legs in d.items():
    print('A %s has %d legs' % (animal, legs))
# Prints "A person has 2 legs", "A cat has 4 legs", "A spider has 8 legs"
```

## Sets

可变数据类型

### 基础

```python
animals = {'cat', 'dog'}
print('cat' in animals)   # Check if an element is in a set; prints "True"
print('fish' in animals)  # prints "False"
animals.add('fish')       # Add an element to a set
print('fish' in animals)  # Prints "True"
print(len(animals))       # Number of elements in a set; prints "3"
animals.add('cat')        # Adding an element that is already in the set does nothing
print(len(animals))       # Prints "3"
animals.remove('cat')     # Remove an element from a set
print(len(animals))       # Prints "2"
```

### 高级创建方法

```python
from math import sqrt
nums = {int(sqrt(x)) for x in range(30)}
print(nums)  # Prints "{0, 1, 2, 3, 4, 5}"
```

## Tuples

不可变数据类型，可以用于字典的key

```python
d = {(x, x + 1): x for x in range(10)}  # Create a dictionary with tuple keys
t = (5, 6)        # Create a tuple
print(type(t))    # Prints "<class 'tuple'>"
print(d[t])       # Prints "5"
print(d[(1, 2)])  # Prints "1"
```

## 函数

### 定义

```python
def sign(x):
    if x > 0:
        return 'positive'
    elif x < 0:
        return 'negative'
    else:
        return 'zero'

for x in [-1, 0, 1]:
    print(sign(x))
# Prints "negative", "zero", "positive"
```

### 返回多个值

Python函数支持返回多个值：

```python
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
```

返回多个值其实就是一个tuple .

函数执行完毕也没有`return`语句时，自动`return None` .

### 参数检查

如果有必要，可以先对参数的数据类型做检查：

```python
def my_abs(x):
    if not isinstance(x, (int, float)):
        raise TypeError('bad operand type')
    if x >= 0:
        return x
    else:
        return -x
```

### 函数的参数

#### 位置参数

根据位置传入的参数。

#### 默认参数

支持函数定义默认参数。默认参数有默认值。

定义默认参数要牢记一点：默认参数必须指向不变对象（比如None、str）！因为前一次函数调用时对默认参数的更改，会遗留到下一次调用。

#### 可变参数

可变是指参数的个数可变。可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。

可变参数就是传入的参数个数是可变的：

```python
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum

>>> calc(1, 2)
5
>>> calc()
0
```

如果已经有一个list或者tuple，可以这样调用可变参数 ：

```python
>>> nums = [1, 2, 3]
>>> calc(*nums)
14
```

`*nums`表示把`nums`这个list的所有元素作为可变参数传进去。 

#### 关键字参数

关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。请看示例： 

```python
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)
```

函数`person`除了必选参数`name`和`age`外，还接受关键字参数`kw`。在调用该函数时，可以只传入必选参数：

```python
>>> person('Michael', 30)
name: Michael age: 30 other: {}
```

也可以传入任意个数的关键字参数：

```python
>>> person('Bob', 35, city='Beijing')
name: Bob age: 35 other: {'city': 'Beijing'}
>>> person('Adam', 45, gender='M', job='Engineer')
name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}
```

和可变参数类似，也可以先组装出一个dict，然后把该dict转换为关键字参数传进去： 

```python
>>> extra = {'city': 'Beijing', 'job': 'Engineer'}
>>> person('Jack', 24, **extra)
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
```

#### 命名关键字参数

命名关键字参数是指在传值时必须指定参数的名称。

如果要限制关键字参数的名字，就可以用命名关键字参数，例如，只接收`city`和`job`作为关键字参数。这种方式定义的函数如下：

```python
def person(name, age, *, city, job):
    print(name, age, city, job)
```

和关键字参数`**kw`不同，命名关键字参数需要一个特殊分隔符`*`，`*`后面的参数被视为命名关键字参数。

调用方式如下：

```
>>> person('Jack', 24, city='Beijing', job='Engineer')
Jack 24 Beijing Engineer
```

如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符`*`了：

```
def person(name, age, *args, city, job):
    print(name, age, args, city, job)
```

命名关键字参数必须传入参数名，这和位置参数不同。如果没有传入参数名，调用将报错 。

#### 参数组合

在Python中定义函数，可以用必选参数、默认参数、可变参数、关键字参数和命名关键字参数，这5种参数都可以组合使用。但是请注意，参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。 

## Classes

### 定义

```python
class Student(object):

    def __init__(self, name, score):
        self.name = name
        self.score = score

    def print_score(self):
        print('%s: %s' % (self.name, self.score))
        
>>> bart = Student('Bart Simpson', 59)
>>> bart.name
'Bart Simpson'
```

### 访问限制

#### 私有变量

如果要让内部属性不被外部访问，可以把属性的名称前加上两个下划线__，在Python中，实例的变量名如果以__开头，就变成了一个私有变量（private），只有内部可以访问，外部不能访问：

```python
class Student(object):

    def __init__(self, name, score):
        self.__name = name
        self.__score = score

    def print_score(self):
        print('%s: %s' % (self.__name, self.__score))
```

双下划线开头的实例变量是不是一定不能从外部访问呢？其实也不是。不能直接访问`__name`是因为Python解释器对外把`__name`变量改成了`_Student__name`，所以，仍然可以通过`_Student__name`来访问`__name`变量 

最后注意下面的这种*错误写法* ：

```python
>>> bart = Student('Bart Simpson', 59)
>>> bart.get_name()
'Bart Simpson'
>>> bart.__name = 'New Name' # 设置__name变量！
>>> bart.__name
'New Name'
```

表面上看，外部代码“成功”地设置了`__name`变量，但实际上这个`__name`变量和class内部的`__name`变量*不是*一个变量！内部的`__name`变量已经被Python解释器自动改成了`_Student__name`，而外部代码给`bart`新增了一个`__name`变量。 

可以使用get方法和set方法获取和设置私有变量。

### 内置函数获取对象信息

只有在不知道对象信息的时候，我们才会去使用内置函数获取对象信息 。

#### len()

在`len()`函数内部，它自动去调用该对象的`__len__()`方法 .

我们自己写的类，如果也想用`len(myObj)`的话，就自己为类实现一个`__len__()`方法 .

#### dir()

如果要获得一个对象的所有属性和方法，可以使用`dir()`函数 。

#### isinstance()

判断对象的继承关系，使用isinstance()函数：

```python
>>> isinstance(h, Dog)
True
```

能用`type()`判断的基本类型也可以用`isinstance()`判断 

#### getattr()、setattr()以及hasattr()

使用`getattr()`、`setattr()`以及`hasattr()`，我们可以直接操作一个对象的状态 ：

可以测试该对象的属性：

```python
>>> class MyObject(object):
...     def __init__(self):
...         self.x = 9
...     def power(self):
...         return self.x * self.x
...
>>> obj = MyObject()

>>> hasattr(obj, 'x') # 有属性'x'吗？
True
>>> obj.x
9
>>> hasattr(obj, 'y') # 有属性'y'吗？
False
>>> setattr(obj, 'y', 19) # 设置一个属性'y'
>>> hasattr(obj, 'y') # 有属性'y'吗？
True
>>> getattr(obj, 'y') # 获取属性'y'
19
>>> obj.y # 获取属性'y'
19
```

也可以获得对象的方法：

```python
>>> hasattr(obj, 'power') # 有属性'power'吗？
True
>>> getattr(obj, 'power') # 获取属性'power'
<bound method MyObject.power of <__main__.MyObject object at 0x10077a6a0>>
>>> fn = getattr(obj, 'power') # 获取属性'power'并赋值到变量fn
>>> fn # fn指向obj.power
<bound method MyObject.power of <__main__.MyObject object at 0x10077a6a0>>
>>> fn() # 调用fn()与调用obj.power()是一样的
81
```

使用场景：在不确定对象是否有某个属性的时候，有想要读取属性的值，可以使用这几个函数提前判断，然后读取。

### 实例属性和类属性

由于Python是动态语言，根据类创建的实例可以任意绑定属性。

给实例绑定属性的方法是通过实例变量，或者通过`self`变量：

```python
class Student(object):
    def __init__(self, name):
        self.name = name

s = Student('Bob')
s.score = 90
```

不要对实例属性和类属性使用相同的名字，因为相同名称的实例属性将屏蔽掉类属性，但是当删除实例属性后，再使用相同的名称，访问到的将是类属性。 

### 使用@property

Python内置的`@property`装饰器负责把一个方法变成属性调用的：

```python
class Student(object):

    @property
    def birth(self):
        return self._birth

    @birth.setter
    def birth(self, value):
        self._birth = value

    @property
    def age(self):
        return 2015 - self._birth
```

上面的`birth`是可读写属性，而`age`就是一个只读属性 。

`@property`广泛应用在类的定义中，可以让代码简短，同时保证对参数进行必要的检查。 

### 多继承

Python支持多继承。

在设计类的继承关系时，为了保持清晰的继承关系，主线都是单一继承下来的 。如果需要“混入”额外的功能，通过多重继承就可以实现。这些额外的功能在Python多继承中称为`MixIn` 。

```python
class Dog(Mammal, RunnableMixIn, CarnivorousMixIn):
    pass
```

### 定制类

#### `__str__()`方法

`__str__()`方法 可以定制`print`对象时的返回的字符串：

```python
>>> class Student(object):
...     def __init__(self, name):
...         self.name = name
...     def __str__(self):
...         return 'Student object (name: %s)' % self.name
...
>>> print(Student('Michael'))
Student object (name: Michael)
```

直接输出对象，不使用`print`的时候，调用的是`__repr__()`方法，可以再次定义`__repr__()`方法。通常`__str__()`和`__repr__()`代码都是一样的，所以，有个偷懒的写法： 

```python
class Student(object):
    def __init__(self, name):
        self.name = name
    def __str__(self):
        return 'Student object (name=%s)' % self.name
    __repr__ = __str__
```

#### `__iter__()`方法

在类中实现`__iter__()`方法 和`__next__()`方法 ，就可以使得类支持`for ... in`循环 操作。

`__iter__()`方法返回一个迭代对象，然后，Python的for循环就会不断调用该迭代对象的`__next__()`方法拿到循环的下一个值，直到遇到`StopIteration`错误时退出循环。 

```python
class Fib(object):
    def __init__(self):
        self.a, self.b = 0, 1 # 初始化两个计数器a，b

    def __iter__(self):
        return self # 实例本身就是迭代对象，故返回自己

    def __next__(self):
        self.a, self.b = self.b, self.a + self.b # 计算下一个值
        if self.a > 100000: # 退出循环的条件
            raise StopIteration()
        return self.a # 返回下一个值
```

#### `__getitem__()`方法

实现`__getitem__()`方法 ，可以让类像list那样按照下标取出元素。

#### `__getattr__()`方法 

当调用不存在的属性时，Python解释器会试图调用`__getattr__(self, 'score')`来尝试获得属性 ：

```python
>>> s = Student()
>>> s.name
'Michael'
>>> s.score
99
```

#### `__call__()`方法 

该方法在如下情况下会被调用(在对象被当成方法调用时)：

```python
class Student(object):
    def __init__(self, name):
        self.name = name

    def __call__(self):
        print('My name is %s.' % self.name)

>>> s = Student('Michael')
>>> s() # self参数不要传入
My name is Michael.
```

`__call__()`还可以定义参数。对实例进行直接调用就好比对一个函数进行调用一样。

### 使用枚举类

从`Enum`派生出自定义类：

```python
from enum import Enum, unique

@unique
class Weekday(Enum):
    Sun = 0 # Sun的value被设定为0
    Mon = 1
    Tue = 2
    Wed = 3
    Thu = 4
    Fri = 5
    Sat = 6
```

`@unique`装饰器可以帮助我们检查保证没有重复值。

## python对象销毁(垃圾回收)

Python 使用了引用计数这一简单技术来跟踪和回收垃圾。 

当对象被创建时， 就创建了一个引用计数， 当这个对象不再需要时， 也就是说， 这个对象的引用计数变为0 时， 它被垃圾回收。但是回收不是"立即"的， 由解释器在适当的时机，将垃圾对象占用的内存空间回收。 

## 错误和调试

### 异常处理

Python使用`try...except...finally...`的错误处理机制 。

该机制可以跨域多层调用捕获异常。

如果错误没有被捕获，它就会一直往上抛，最后被Python解释器捕获，打印一个错误信息，然后程序退出。 

Python内置的`logging`模块可以非常容易地记录错误信息：

```python
import logging

def main():
    try:
        bar('0')
    except Exception as e:
        logging.exception(e)

main()
print('END')
```

还可以使用raise语句抛出异常。

### 调试

#### 断言

凡是用`print()`来辅助查看的地方，都可以用断言（assert）来替代：

```python
def foo(s):
    n = int(s)
    assert n != 0, 'n is zero!'
    return 10 / n

def main():
    foo('0')
```

`assert`的意思是，表达式`n != 0`应该是`True`，否则，根据程序运行的逻辑，后面的代码肯定会出错。

启动Python解释器时可以用`-O`参数来关闭`assert` ：

```python
$ python -O err.py
```

关闭后，你可以把所有的`assert`语句当成`pass`来看。 

#### logging

把`print()`替换为`logging`是第3种方式，和`assert`比，`logging`不会抛出错误，而且可以输出到文件 。

日志输出级别可以配置：

```python
import logging
logging.basicConfig(level=logging.INFO)
```

#### 单步调试pdb

启动Python的调试器pdb，让程序以单步方式运行，可以随时查看运行状态 

启动方式：

```python
$ python -m pdb err.py
> /Users/michael/Github/learn-python3/samples/debug/err.py(2)<module>()
-> s = '0'
```

输入命令`l`来查看代码。

输入命令`n`可以单步执行代码 。

任何时候都可以输入命令`p 变量名`来查看变量 。

输入命令`q`结束调试，退出程序 。

#### 断点调试

`import pdb`，在可能出错的地方放一个`pdb.set_trace()`，就可以设置一个断点：

```python
# err.py
import pdb

s = '0'
n = int(s)
pdb.set_trace() # 运行到这里会自动暂停
print(10 / n)
```

用命令`p`查看变量，或者用命令`c`继续运行 。

## 函数式编程

### 高阶函数

#### map和reduce

`map()`函数接收两个参数，一个是函数，一个是`Iterable`，`map`将传入的函数依次作用到序列的每个元素，并把结果作为新的`Iterator`返回 .

比如：

```python
>>> def f(x):
...     return x * x
...
>>> r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
>>> list(r)
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```

`map()`作为高阶函数，事实上它把运算规则抽象了。

再看`reduce`的用法。`reduce`把一个函数作用在一个序列`[x1, x2, x3, ...]`上，这个函数必须接收两个参数，`reduce`把结果继续和序列的下一个元素做累积计算，其效果就是：

```python
reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)
```

比方说对一个序列求和，就可以用`reduce`实现：

```python
>>> from functools import reduce
>>> def add(x, y):
...     return x + y
...
>>> reduce(add, [1, 3, 5, 7, 9])
25
```

整理成一个`str2int`的函数就是：

```python
from functools import reduce

DIGITS = {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}

def str2int(s):
    def fn(x, y):
        return x * 10 + y
    def char2num(s):
        return DIGITS[s]
    return reduce(fn, map(char2num, s))
```

#### filter

和`map()`类似，`filter()`也接收一个函数和一个序列。和`map()`不同的是，`filter()`把传入的函数依次作用于每个元素，然后根据返回值是`True`还是`False`决定保留还是丢弃该元素。

例如，在一个list中，删掉偶数，只保留奇数，可以这么写：

```python
def is_odd(n):
    return n % 2 == 1

list(filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15]))
```

#### sorted

Python内置的`sorted()`函数就可以对list进行排序：

```python
>>> sorted([36, 5, -12, 9, -21])
[-21, -12, 5, 9, 36]
```

可以设置key来按照元素的映射排序。

可以通过设置`reverse=True`来反向排序。

### 返回函数

返回函数的函数是一个闭包。

### 匿名函数

关键字`lambda`表示匿名函数 

### 装饰器

在函数调用前后自动打印日志，但又不希望修改`now()`函数的定义，这种在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。 

本质上，decorator就是一个返回函数的高阶函数。所以，我们要定义一个能打印日志的decorator，可以定义如下：

```python
def log(func):
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper
```

我们要借助Python的@语法，把decorator置于函数的定义处：

```
@log
def now():
    print('2015-3-25')
```

调用`now()`函数，不仅会运行`now()`函数本身，还会在运行`now()`函数前打印一行日志

### 偏函数

`functools.partial`就是帮助我们创建一个偏函数的，不需要我们自己定义`int2()`，可以直接使用下面的代码创建一个新的函数`int2`：

```python
>>> import functools
>>> int2 = functools.partial(int, base=2)
>>> int2('1000000')
64
>>> int2('1010101')
85
```

所以，简单总结`functools.partial`的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。

## 文件IO

### 以UTF-8编码写入中文字符

```python
import codecs

f = codecs.open('1234.txt', 'w', encoding='utf-8')
f.write(u'hello,utf')
f.close()
```





























































































