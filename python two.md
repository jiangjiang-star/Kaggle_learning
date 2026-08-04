# 第一天11.3
```python
color = "blue"
```
双引号字符串的定义
```python
area = pi * radius ** 2
```
表示幂运算
```python
help(print)
```
可以通过help（）来看到函数的定义和使用，和keil的转到定义处有点像
```python
print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.#special
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream.
```
## Defining functions
```python
def least_difference(a, b, c):
    diff1 = abs(a - b)
    diff2 = abs(b - c)
    diff3 = abs(a - c)
    return min(diff1, diff2, diff3)
```
return:asses the value on the right hand side to the calling context
## 编写字符串文档
！？

## python小要点
Python allows us to define such functions. The result of calling them is the special value `None`.
```python
print(1, 2, 3, sep=' < ')
#1 < 2 < 3
```
![[Pasted image 20251103133936.png]]
```python
def mod_5(x):
    """Return the remainder of x after dividing by 5"""
    return x % 5

print(
    'Which number is biggest?',
    max(100, 51, 14),
    'Which number is the biggest modulo 5?',
    max(100, 51, 14, key=mod_5),#key的妙用
    sep='\n',
)
"""
Which number is biggest?
100
Which number is the biggest modulo 5?
14
"""
```
## 函数
```python
round()
round(num, 2)#四舍五入到两位小数
min()
max()
print()
help()
abs()
```

## Booleans  and conditionals.

### and or not
先后顺序：Python 在计算表达式时，会遵循运算符的优先级。`and` 的优先级高于 `or`，`not` 的优先级又高于 `and`。
运算符：
[6. Expressions — Python 3.14.0 documentation](https://docs.python.org/3/reference/expressions.html#operator-precedence)

Booleans are most useful when combined with _conditional statements_, using the keywords `if`, `elif`, and `else`.

We've seen `int()`, which turns things into ints, and `float()`, which turns things into floats, so you might not be surprised to hear that Python has a `bool()` function which turns things into bools.

```python
print(bool(1)) # all numbers are treated as true, except 0
print(bool(0))
print(bool("asf")) # all strings are treated as true, except the empty string ""
print(bool(""))
```
```python
True
False
True
False
```

 If the value of the expression `number < 0` is `True`, then we return `True`. If it's `False`, then we return `False`
 ```python
 def exactly_one_sauce(ketchup, mustard, onion):
    """Return whether the customer wants either ketchup or mustard, but not both.
    (You may be familiar with this operation under the name "exclusive or")
    """
    return  (ketchup and not mustard) or (mustard and not ketchup)
    pass

# Check your answer
q5.c.check()
 ```
 ```python
 def exactly_one_topping(ketchup, mustard, onion):
    """Return whether the customer wants exactly one of the three available toppings
    on their hot dog.
    """
    return (ketchup and not mustard and not onion) or (mustard and not ketchup and not onion) or (onion and not mustard and not ketchup)
    return (int(ketchup) + int(mustard) + int(onion)) == 1
    return (ketchup + mustard + onion) == 1
    pass

# Check your answer
q6.check()
 ```

三种方式，最主要是后两种方式非常简洁，需要学会使用
## 列表
primes = [2, 3, 5, 7]
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
hands = [
    ['J', 'Q', 'K'],
    ['2', '2', '2'],
    ['6', 'A', 'K'], # (Comma after the last element is optional)
]
my_favourite_things = [32, 'raindrops on roses', help]
### Indexing
You can access individual list elements with square brackets.
planets[0]
你可以使用方括号访问列表中的单个元素
Elements at the end of the list can be accessed with negative numbers, starting from -1:
planets[-1]
### Slicing
planets[0:3]（不包含索引3）
The starting and ending indices are both optional. If I leave out the start index, it's assumed to be 0.
planets[:3]（不包含索引3）
If I leave out the end index, it's assumed to be the length of the list.
planets[3:]
We can also use negative indices when slicing:（不包含最后一个元素，-1元素）
planets[1:-1]
包含左边不包含右边，这个包含最后一个元素
planets[-3:]
### Changing lists[¶](https://www.kaggle.com/code/colinmorris/lists#Changing-lists)
planets[3] = 'Malacandra'
### List functions[¶](https://www.kaggle.com/code/colinmorris/lists#List-functions)
```python
len(planets)
sorted(planets):# The planets sorted in alphabetical order按字母顺序排序
sum(primes)
max(primes)
```
### Interlude: objects[¶](https://www.kaggle.com/code/colinmorris/lists#Interlude:-objects)
到目前为止，我已经多次使用了“对象”（object）这个术语——你可能甚至听说过“Python 中万物皆对象”。这是什么意思？
简而言之，对象会随身携带一些东西。你可以使用 Python 的点号语法（dot syntax）来访问这些东西。
例如，Python 中的数字带有一个名为 `imag` 的关联变量，它表示该数字的虚部。（除非你在做一些非常奇怪的数学运算，否则你可能永远都用不到这个。）
```python
c = 12 + 3j
print(c.imag)#3.0
```
对象所携带的东西也可能包含函数。附属于对象的函数被称为**方法**。（附属于对象的非函数类事物，例如 `imag`，则被称为**属性**。）
例如，数字有一个名为 `bit_length` 的方法。同样，我们使用点号语法来访问它：
```python
x.bit_length()
help(x.bit_length)
>>> bin(37)
    '0b100101'
>>> (37).bit_length()
    6
```
# 第二天1105
### List methods[¶](https://www.kaggle.com/code/colinmorris/lists#List-methods)
`list.append` modifies a list by adding an item to the end:
```python
# Pluto is a planet darn it!
planets.append('Pluto')
```
`append` is a method carried around by _all_ objects of type list, not just `planets`, so we also could have called `help(list.append)`. However, if we try to call `help(append)`, Python will complain that no variable exists called "append". The "append" name only exists within lists - it doesn't exist as a standalone name like builtin functions such as `max` or `len`.
`list.pop` removes and returns the last element of a list:
```python
planets.pop()

Out:'Pluto'
```
#### Searching lists[¶](https://www.kaggle.com/code/colinmorris/lists#Searching-lists)
注意index返回的是索引，实际上排在第三个，索引为2
```python
planets.index('Earth')

Out:2
```
To avoid unpleasant surprises like this, we can use the `in` operator to determine whether a list contains a particular value:
```python
# Is Earth a planet?
"Earth" in planets

True
```
 we can call `help()` on the object itself,注意，列表要创建后，具体列表名字才能使用help
```python
help(planets)
```
### Tuples[¶](https://www.kaggle.com/code/colinmorris/lists#Tuples)
Tuples are almost exactly the same as lists. They differ in just two ways.
**1:** The syntax for creating them uses parentheses instead of square brackets
```python
t = (1, 2, 3)
t = 1, 2, 3  # 等价于上面的写法
t
```
这行代码创建了一个**元组（tuple）**。在 Python 中，用逗号分隔的值会自动被解释为元组，即使没有括号。
所以 `t = 1, 2, 3` 等价于 `t = (1, 2, 3)`。
**2:** They cannot be modified (they are _immutable_).
```python
t[0] = 100
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
/tmp/ipykernel_19/816329950.py in <module>
----> 1 t[0] = 100

TypeError: 'tuple' object does not support item assignment

```
Tuples are often used for functions that have multiple return values.
```python
x = 0.125
x.as_integer_ratio()

numerator, denominator = x.as_integer_ratio()
print(numerator / denominator)
```
Finally we have some insight into the classic Stupid Python Trick™ for swapping two variables!
```python
a = 1
b = 0
a, b = b, a
print(a, b)
```
列表里面还是列表的调用方式
```python
teams[-1][1]
```
判断列表的长度
```python
d = [1, 2, 3][1:]

The expression is the same as the list `[2, 3]`, which has length 2.
```
一题多解
# 5. 🌶️[](https://kkb-production.jupyter-proxy.kaggle.net/static/assets/jupyterlab-v4/jupyterlab-index-2fa5cfaf7d5c40d310e1.html?session=eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJpc3MiOiJrYWdnbGUiLCJhdWQiOiJjbGllbnQiLCJzdWIiOiJqaWFuZ2ppYW5nMTIzMTIzIiwibmJ0IjoiMjAyNS0xMS0wNVQwOTo1MToyMC4zNTEyMTM4WiIsImlhdCI6IjIwMjUtMTEtMDVUMDk6NTE6MjAuMzUxMjEzOFoiLCJqdGkiOiJjYjVlMDM1Mi1kNmRmLTQ0N2QtOTZmNi02MGVjZDczN2ZhYTgiLCJleHAiOiIyMDI1LTEyLTA1VDA5OjUxOjIwLjM1MTIxMzhaIiwidWlkIjoyNDgyNzM1MCwiZGlzcGxheU5hbWUiOiJqaWFuZ2ppYW5nMTIzNDU2IiwiZW1haWwiOiIxNzkwNDc0ODE3QHFxLmNvbSIsInRpZXIiOiJjb250cmlidXRvciIsInZlcmlmaWVkIjp0cnVlLCJwcm9maWxlVXJsIjoiL2ppYW5namlhbmcxMjMxMjMiLCJ0aHVtYm5haWxVcmwiOiJodHRwczovL3N0b3JhZ2UuZ29vZ2xlYXBpcy5jb20va2FnZ2xlLWF2YXRhcnMvdGh1bWJuYWlscy9kZWZhdWx0LXRodW1iLnBuZyIsImZmIjpbIkJlbmNobWFya09wZW5HcmFwaCIsIktlcm5lbHNPcGVuSW5Db2xhYkxvY2FsVXJsIiwiTWV0YXN0b3JlQ2hlY2tBZ2dyZWdhdGVGaWxlSGFzaGVzIiwiVXNlckxpY2Vuc2VBZ3JlZW1lbnRTdGFsZW5lc3NUcmFja2luZyIsIlN0c0Rvd25sb2FkIiwiS2VybmVsc1BheVRvU2NhbGUiLCJCZW5jaG1hcmtPdXRwdXRJbXByb3ZlbWVudHMiLCJUYXNrU2hhcmVWaWFSb2xlcyIsIkZlYXR1cmVkTW9kZWxzU2hlbGYiLCJEYXRhc2V0UG9sYXJzRGF0YUxvYWRlciIsIkJlbmNobWFya1NvY2lhbFNoYXJpbmciLCJLZXJuZWxzU2V0dGluZ3NUYWIiLCJSZXF1aXJlUGVyc29uYVZlcmlmaWNhdGlvbkZvclRwdSIsIktlcm5lbHNGaXJlYmFzZVByb3h5IiwiS2VybmVsc0djc1VwbG9hZFByb3h5IiwiS2VybmVsc0ZpcmViYXNlTG9uZ1BvbGxpbmciLCJLZXJuZWxzRHJhZnRVcGxvYWRCbG9iIiwiS2VybmVsc1NhdmVDZWxsT3V0cHV0IiwiRnJvbnRlbmRFcnJvclJlcG9ydGluZyIsIkFsbG93Rm9ydW1BdHRhY2htZW50cyIsIlRlcm1zT2ZTZXJ2aWNlQmFubmVyIiwiRGF0YXNldFVwbG9hZGVyRHVwbGljYXRlRGV0ZWN0aW9uIl0sImZmZCI6eyJNb2RlbElkc0FsbG93SW5mZXJlbmNlIjoiIiwiTW9kZWxJbmZlcmVuY2VQYXJhbWV0ZXJzIjoieyBcIm1heF90b2tlbnNcIjogMTI4LCBcInRlbXBlcmF0dXJlXCI6IDAuNCwgXCJ0b3Bfa1wiOiA1IH0iLCJTcG90bGlnaHRDb21tdW5pdHlDb21wZXRpdGlvbiI6IjEwNTg3NCwxMDEwMzksMTEzMTU1LDEwMzQzMiwxMTM2NjQiLCJGZWF0dXJlZEJlbmNobWFya3MiOiIxMzcsMTYsODYsMTM0IiwiR2V0dGluZ1N0YXJ0ZWRDb21wZXRpdGlvbnMiOiIzMTM2LDU0MDcsODY1MTgsMzQzNzciLCJHYW1lQXJlbmFSZWFzb25pbmdUZXh0U3BlZWQiOiIyIiwiU3RzTWluRmlsZXMiOiIxMjUwMDAiLCJTdHNNaW5HYiI6IjEiLCJHYW1lQXJlbmFSZWFzb25pbmdTdGVwRHVyYXRpb24iOiIyMDAwIiwiUGVyc29uYWxCZW5jaG1hcmtzUHJpb3JpdHlUYXNrSWRzIjoiMTA2LDIyOSwxMDUsMjI3LDExMCwyMjgsMTE2LDIzMCwxNzMsMjMyLDE3NSwyMzksMjY0LDI0OSwyNDciLCJDbGllbnRScGNSYXRlTGltaXRRcHMiOiI0MCIsIkNsaWVudFJwY1JhdGVMaW1pdFFwbSI6IjUwMCIsIkFkZEZlYXR1cmVGbGFnc1RvUGFnZUxvYWRUYWciOiJkaXNhYmxlZCIsIktlcm5lbEVkaXRvckF1dG9zYXZlVGhyb3R0bGVNcyI6IjMwMDAwIiwiS2VybmVsc0w0R3B1Q29tcHMiOiI4NjAyMyw4NDc5NSw4ODkyNSw5MTQ5NiIsIkVuYWJsZUNkbkNhY2hlIjoiIiwiSHR0cEdldEVuYWJsZWRScGNzIjoiIiwiRmVhdHVyZWRDb21tdW5pdHlDb21wZXRpdGlvbnMiOiI2MDA5NSw1NDAwMCw1NzE2Myw4MDg3NCw4MTc4Niw4MTcwNCw4MjYxMSw4NTIxMCIsIkVtZXJnZW5jeUFsZXJ0QmFubmVyIjoiIiwiQ29tcGV0aXRpb25NZXRyaWNUaW1lb3V0TWludXRlcyI6IjMwIiwiR2FtZUFyZW5hRmVhdHVyZWRMZWFkZXJib2FyZEJlbmNobWFya1ZlcnNpb25zIjoiNzIiLCJDZG5DYWNoZURpc2FibGVkUnBjcyI6IiIsIkRhdGFzZXRzU2VuZFBlbmRpbmdTdWdnZXN0aW9uc1JlbWluZGVyc0JhdGNoU2l6ZSI6IjEwMCIsIkdhbWVBcmVuYUJlbmNobWFya1ZlcnNpb25zIjoiNzIsMTYxLDEyOSIsIktlcm5lbHNQYXlUb1NjYWxlUHJvUGx1c0dwdUhvdXJzIjoiMzAiLCJLZXJuZWxzUGF5VG9TY2FsZVByb0dwdUhvdXJzIjoiMTUiLCJFbWVyZ2VuY3lBbGVydEJhbm5lckZvclVzZXJQcm9maWxlIjoiIiwiS2VybmVsc0gxMDBDb21wcyI6IiJ9LCJwaWQiOiJrYWdnbGUtMTYxNjA3Iiwic3ZjIjoid2ViLWZlIiwic2RhayI6IkFJemFTeUE0ZU5xVWRSUnNrSnNDWldWei1xTDY1NVhhNUpFTXJlRSIsImJsZCI6Ijk0ZDljMmM0MjE2MjJjNDRmN2Q3ZDA2MTVhNjI1ODRlOWYxNDMyODcifQ.&lsp=true#5.-%F0%9F%8C%B6%EF%B8%8F)

We're using lists to record people who attended our party and what order they arrived in. For example, the following list represents a party with 7 guests, in which Adela showed up first and Ford was the last to arrive:

```
party_attendees = ['Adela', 'Fleda', 'Owen', 'May', 'Mona', 'Gilbert', 'Ford']
```

A guest is considered 'fashionably late' if they arrived after at least half of the party's guests. However, they must not be the very last guest (that's taking it too far). In the above example, Mona and Gilbert are the only guests who were fashionably late.

Complete the function below which takes a list of party attendees as well as a person, and tells us whether that person is fashionably late.

```python
def fashionably_late(arrivals, name):
    """Given an ordered list of arrivals to the party and a name, return whether the guest with that
    name was fashionably late.
    """
    num=len(arrivals)
    if num/2>num//2:
        num2=num//2+1
    else:
        num2=num//2
    l2=arrivals[num2:-1]
    return (name in l2)
    pass

# Check your answer
q5.check()
```

```python
def fashionably_late(arrivals, name):
    order = arrivals.index(name)
    return order >= len(arrivals) / 2 and order != len(arrivals) - 1
```
## Loops and List Comprehensions
### Loops[¶](https://www.kaggle.com/code/colinmorris/loops-and-list-comprehensions#Loops)
Loops are a way to repeatedly execute some code.
```python
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
    print(planet, end=' ') # print all on same line
```
for 循环指定了：

- 要使用的变量名（在本例中是 `planet`）
- 要遍历的值的集合（在本例中是 `planets`）

你使用单词 **`in`** 将它们连接在一起。

`in` 右侧的对象可以是**任何支持迭代的对象**。基本上，只要某个对象可以被看作是一组东西，你很可能就能对它进行循环遍历。除了列表之外，我们还可以遍历元组的元素：
```python
multiplicands = (2, 2, 2, 3, 3, 5)
product = 1
for mult in multiplicands:
    product = product * mult
product
```
 loop through each character in a string:
 ```python
 s = 'steganograpHy is the practicE of conceaLing a file, message, image, or video within another fiLe, message, image, Or video.'
msg = ''
# print all the uppercase letters in s, one at a time
for char in s:
    if char.isupper():
        print(char, end='')

out:HELLO
 ```

#### range()[¶](https://www.kaggle.com/code/colinmorris/loops-and-list-comprehensions#range\(\))

`range()` is a function that returns a sequence of numbers. It turns out to be very useful for writing loops.
For example, if we want to repeat some action 5 times:
```python
for i in range(5):
    print("Doing important work. i =", i)

out:
Doing important work. i = 0
Doing important work. i = 1
Doing important work. i = 2
Doing important work. i = 3
Doing important work. i = 4
```

### `while` loops[¶](https://www.kaggle.com/code/colinmorris/loops-and-list-comprehensions#while-loops)
```python
i = 0
while i < 10:
    print(i, end=' ')
    i += 1 # increase the value of i by 1

out:0 1 2 3 4 5 6 7 8 9
```
### List comprehensions[¶](https://www.kaggle.com/code/colinmorris/loops-and-list-comprehensions#List-comprehensions)
列表+循环
```python
squares = [n**2 for n in range(10)]
squares

out:[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

等价于：
squares = []
for n in range(10):
    squares.append(n**2)
squares
```
# 第三天1109
做题的时候看不懂英语太难崩了，理解不了题意，根本无从下手。不过有点欣慰的是，现在的一些基础内容，是一起有在c学习到的，万般苦头都不白吃~~
```python
Remember that `return` causes a function to exit immediately. So our original implementation always ran for just one iteration. We can only return `False` if we've looked at every element of the list (and confirmed that none of them are lucky). Though we can return early if the answer is `True`:

```python
def has_lucky_number(nums):
    for num in nums:
        if num % 7 == 0:
            return True
    # We've exhausted the list without finding a lucky number
    return False
```

Here's a one-line version using a list comprehension with Python's `any` function (you can read about what it does by calling `help(any)`):
```python
def has_lucky_number(nums):
    return any([num % 7 == 0 for num in nums])
```
- `[num % 7 == 0 for num in nums]` 会生成一个布尔值列表，例如 `[False, True, False]`。
- `any()` 函数会检查这个列表中**是否存在至少一个 `True`**，如果有就返回 `True`，否则返回 `False`

如果追求效率（尤其在处理大数据时），更推荐使用**生成器表达式**：
```python
def has_lucky_number(nums):
    return any(num % 7 == 0 for num in nums)  # 没有方括号 → 生成器，惰性求值
```
这样 `any()` 一旦遇到第一个满足条件的元素就会停止，不会浪费内存或时间。

一题多解
```python
def elementwise_greater_than(L, thresh):
    """Return a list with the same length as L, where the value at index i is 
    True if L[i] is greater than thresh, and False otherwise.
    
    >>> elementwise_greater_than([1, 2, 3, 4], 2)
    [False, False, True, True]
    x=0
    for n in L:
        if n>thresh:
            L[x]=True
        else:
            L[x]=False
        x=x+1
    return L
    """
    #注意函数的写法range and round
    for n in range(len(L)):
        if L[n]>thresh:
            L[n]=True
        else:
            L[n]=False
    return L
    pass
    

def elementwise_greater_than(L, thresh):
    res = []
    for ele in L:
        res.append(ele > thresh)
    return res

def elementwise_greater_than(L, thresh):
    return [ele > thresh for ele in L]
```

 res.append(ele > thresh)：
判断 ele > thresh，结果是 True 或 False，
然后把这个布尔值添加到 res 列表末尾
return [ele > thresh for ele in L]：
- `for ele in L`：遍历 `L` 中的每个元素
- `ele > thresh`：对每个 `ele` 计算布尔值
- 外层的 `[ ... ]`：自动收集所有结果，组成新列表
- 对 `L` 中的每个 `ele`，计算 `ele > thresh`，把所有结果放进一个新列表里。
第三题也有点难度，自己想，可能不容易想到简单方法
第四题一题多解
```python
payouts = [play_slot_machine()-1 for i in range(n_runs)] 
avg_payout = sum(payouts) / n_runs

def estimate_average_slot_payout(n_runs):
    """Run the slot machine n_runs times and return the average net profit per run.
    Example calls (note that return value is nondeterministic!):
    >>> estimate_average_slot_payout(1)
    -1
    >>> estimate_average_slot_payout(1)
    0.5
    """
    all_mon=0
    for i in range(n_runs):
        all_mon+=play_slot_machine()-1
    return all_mon/n_runs

```
## Strings and Dictionaries
单引号和双引号对于字符串的定义是相同的
```python
x = 'Pluto is a planet'
y = "Pluto is a planet"
x == y
```
如果字符串中包含单引号（例如表示撇号），使用双引号会很方便。
同样地，如果你用单引号将字符串括起来，就可以轻松创建包含双引号的字符串。
fix this by "escaping" the single quote with a backslash
当字符串**同时包含单引号和双引号**时，才真正需要转义或使用三引号（`'''` 或 `"""`）。
```python
'Pluto\'s a planet!'
```
![[Pasted image 20251109110648.png]]
Python 的三引号（triple quote）字符串语法允许我们**直接包含换行符**（即只需在键盘上按 Enter 键，而无需使用特殊的 `\n` 转义序列）。
```python
message = """Hello, this is a multi-line string in Python."""
等价于
message = "Hello,\nthis is a multi-line\nstring in Python."
```
print相关
```python
print("hello")
print("world")
print("hello", end='')
print("pluto", end='')

out：
hello
world
hellopluto
```
Almost everything we've seen that we can do to a list, we can also do to a string.
例如切片，负号索引，省略
Yes, we can even loop over them
[char+'! ' for char in planet]->['P! ', 'l! ', 'u! ', 't! ', 'o! ']
**==They are immutable. We can't modify them.==**
### String methods[¶](https://www.kaggle.com/code/colinmorris/strings-and-dictionaries#String-methods)
```python
claim.upper()#所有字母大写
claim.lower()#所有字母小写
# Searching for the first index of a substring
claim.index('plan')#在字符串变量 `claim` 中查找子字符串 `'plan'` 第一次出现的位置（索引）
claim.startswith(planet)#检查字符串 `claim` 是否以变量 `planet` 的值开头
#- 返回 `True` 如果 `claim` 的开头部分与 `planet` 完全匹配；
#- 否则返回 `False`。
#- 比较是**区分大小写**的。

```
#### Going between strings and lists: `.split()` and `.join()`[¶](https://www.kaggle.com/code/colinmorris/strings-and-dictionaries#Going-between-strings-and-lists:-.split\(\)-and-.join\(\))
`str.split()` 将一个字符串拆分成一个由更小字符串组成的列表，默认以**空白字符**（如空格、制表符、换行符等）作为分隔符。
```python
datestr = '1956-01-31'
year, month, day = datestr.split('-')
```
`str.join()`它将一个字符串列表“缝合”成一个长字符串，并以调用该方法的字符串作为分隔符
```python
'/'.join([month, day, year])

'01/31/1956'

' 👏 '.join([word.upper() for word in words])

'PLUTO 👏 IS 👏 A 👏 PLANET!'
```
#### Building strings with `.format()`[¶](https://www.kaggle.com/code/colinmorris/strings-and-dictionaries#Building-strings-with-.format\(\))
`+` 运算符来连接字符串,但是**Python 不允许直接把字符串和非字符串类型相加**。
```python
planet + ", you'll always be the " + str(position) + "th planet to me."

"{}, you'll always be the {}th planet to me.".format(planet, position)

"{} weighs about {:.2} kilograms ({:.3%} of Earth's mass). It is home to {:,} Plutonians.".format(
    planet, pluto_mass, pluto_mass / earth_mass, population,
)

out:
"Pluto weighs about 1.3e+22 kilograms (0.218% of Earth's mass). It is home to 52,910,390 Plutonians."
```
### Dictionaries[¶](https://www.kaggle.com/code/colinmorris/strings-and-dictionaries/tutorial#Dictionaries)
mapping keys to values.
```python
numbers = {'one':1, 'two':2, 'three':3}
numbers['one']

out:1
```
```python
numbers['eleven'] = 11
numbers

out:{'one': 1, 'two': 2, 'three': 3, 'eleven': 11}
```
这个是列表转换为字典，注意
```python
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
planet_to_initial = {planet: planet[0] for planet in planets}

out:{'Mercury': 'M',
 'Venus': 'V',
 'Earth': 'E',
 'Mars': 'M',
 'Jupiter': 'J',
 'Saturn': 'S',
 'Uranus': 'U',
 'Neptune': 'N'}
```
Python 中**字典推导式**（dictionary comprehension）的基本语法是：

```python
{key_expression: value_expression for item in iterable}
```

- `key_expression`：决定字典的**键**（key）
- `value_expression`：决定字典的**值**（value）
- `for item in iterable`：遍历一个可迭代对象（比如列表）
A for loop over a dictionary will loop over its keys
```python
for k in numbers:
    print("{} = {}".format(k, numbers[k]))

out:
one = Pluto
two = 2
three = 3
eleven = 11
```
We can access a collection of all the keys or all the values with `dict.keys()` and `dict.values()`
Get all the initials, sort them alphabetically, and put them in a space-separated string.
```python
' '.join(sorted(planet_to_initial.values()))

'E J M M N S U V'
```
The very useful `dict.items()` method lets us iterate over the keys and values of a dictionary simultaneously. (In Python jargon, an **item** refers to a key, value pair)
```python
for planet, initial in planet_to_initial.items():
    print("{} begins with \"{}\"".format(planet.rjust(10), initial))

out:
Mercury begins with "M"
     Venus begins with "V"
     Earth begins with "E"
      Mars begins with "M"
   Jupiter begins with "J"
    Saturn begins with "S"
    Uranus begins with "U"
   Neptune begins with "N"
```
planet.rjust(10)
`planet.rjust(10)` 是 Python 中字符串的一个方法调用，用于**右对齐**字符串，并在左侧填充空格，使整个字符串总长度为 10 个字符。
- `rjust` 是 **"right justify"**（右对齐）的缩写。
- 语法：`str.rjust(width[, fillchar])`
    - `width`：目标总宽度（这里是 `10`）。
    - `fillchar`（可选）：用于填充的字符，默认是空格 `' '`。
# 第四天 1203
**operator overloading**：运算符重载
```python
print(dir(math))

output:['__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'pi', 'pow', 'radians', 'remainder', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc']

math.pi
math.log(32, 2)
help(math.log)
```
alias:
```python
import math as mt
mt.pi
```
引入某个部分：
`import * 会让模块中的所有变量可直接调用（无任何点号前缀）。`但是问题在于，两个库如果都有这个函数，怎么办？报错呗
```python
from math import *

from math import log, pi
from numpy import asarray
```
在每个模块中引入需要的内容就够了
Submodules：
```python
rolls = numpy.random.randint(low=1, high=6, size=10)
```
## 除了基础的一些数据类型，不同的模块还会引入不同的数据类型
三大工具，帮助上手陌生对象
1.**`type()`** (what is this thing?)
```python
type(rolls)

numpy.ndarray
```
**2: `dir()`** (what can I do with it?)
```python
print(dir(rolls))

['T', '__abs__', '__add__', '__and__', '__array__', '__array_finalize__', '__array_function__', '__array_interface__', '__array_prepare__', '__array_priority__', '__array_struct__', '__array_ufunc__', '__array_wrap__', '__bool__', '__class__', '__complex__', '__contains__', '__copy__', '__deepcopy__', '__delattr__', '__delitem__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__iadd__', '__iand__', '__ifloordiv__', '__ilshift__', '__imatmul__', '__imod__', '__imul__', '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__ior__', '__ipow__', '__irshift__', '__isub__', '__iter__', '__itruediv__', '__ixor__', '__le__', '__len__', '__lshift__', '__lt__', '__matmul__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rlshift__', '__rmatmul__', '__rmod__', '__rmul__', '__ror__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__', '__setitem__', '__setstate__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__xor__', 'all', 'any', 'argmax', 'argmin', 'argpartition', 'argsort', 'astype', 'base', 'byteswap', 'choose', 'clip', 'compress', 'conj', 'conjugate', 'copy', 'ctypes', 'cumprod', 'cumsum', 'data', 'diagonal', 'dot', 'dtype', 'dump', 'dumps', 'fill', 'flags', 'flat', 'flatten', 'getfield', 'imag', 'item', 'itemset', 'itemsize', 'max', 'mean', 'min', 'nbytes', 'ndim', 'newbyteorder', 'nonzero', 'partition', 'prod', 'ptp', 'put', 'ravel', 'real', 'repeat', 'reshape', 'resize', 'round', 'searchsorted', 'setfield', 'setflags', 'shape', 'size', 'sort', 'squeeze', 'std', 'strides', 'sum', 'swapaxes', 'take', 'tobytes', 'tofile', 'tolist', 'tostring', 'trace', 'transpose', 'var', 'view']
```
**3: `help()`** (tell me more)
## operator overloading
`列表（list）的设计者规定：不允许列表与数字进行加法运算。而 numpy 数组（array）的设计者则采用了不同的思路——将数字与数组中的每个元素分别相加。`
```python
rolls + 10
array([13, 14, 13, 14, 15, 15, 12, 11, 13, 13])

# At which indices are the dice less than or equal to 3?
rolls <= 3
array([ True, False,  True, False, False, False,  True,  True,  True,
        True])

array([ True, False,  True, False, False, False,  True,  True,  True,
        True])
output:xlist = [[1, 2, 3], [2, 4, 6]]
x =
[[1 2 3]
 [2 4 6]]
 
# Get the last element of the second row of our numpy array
x[1,-1]
6
```

```python

import tensorflow as tf
# Create two constants, each with value 1
a = tf.constant(1)
b = tf.constant(1)
# Add them together to get...
a + b
```
TensorFlow 1.x 的核心设计是「计算图机制」，核心逻辑分两步：

1. **构建计算图**：代码 `a = tf.constant(1)`、`b = tf.constant(1)`、`a + b` 仅在 “绘制计算图”—— 定义了 “两个常量节点” 和 “一个加法运算节点”，以及它们之间的连接关系，但**没有执行任何计算**；
2. **执行计算图**：必须通过 `tf.Session()` 会话的 `run()` 方法，才能触发运算并获取实际值。
### ！！！双划线什么意思
1. `当 Python 开发者想要定义运算符作用于自定义类型时的行为时，会通过实现「特殊方法」来实现——这些方法的名称以两个下划线开头、两个下划线结尾，例如 __lt__、__setattr__ 或 __contains__。通常来说，遵循这种双下划线格式的名称对 Python 而言都具有特殊意义。`
2. `举个例子，表达式 x in [1, 2, 3] 实际上是在底层调用了列表的 __contains__ 方法。它等价于（颜值低得多的）[1, 2, 3].__contains__(x)。`

## 绘制图表
用 Python 的 matplotlib 库绘制图表
```PYTHON
# Import the jimmy_slots submodule,从 `learntools.python` 模块中，导入 `jimmy_slots` 子模块
from learntools.python import jimmy_slots
# Call the get_graph() function to get Jimmy's graph,调用 `jimmy_slots` 子模块中的 `get_graph()` 函数，将返回的图表对象赋值给变量 `graph`
graph = jimmy_slots.get_graph()
graph
```

```python
def prettify_graph(graph):
    """Modify the given graph according to Jimmy's requests: add a title, make the y-axis
    start at 0, label the y-axis. (And, if you're feeling ambitious, format the tick marks
    as dollar amounts using the "$" symbol.)
    """
    graph.set_title("Results of 500 slot machine pulls")
    # Complete steps 2 and 3 here
    graph.set_ylim(ymin=0)
    graph.set_ylabel("Balance")
    # help(graph.set_ylim)

graph = jimmy_slots.get_graph()
prettify_graph(graph)
graph
```
 format the numbers on the y-axis so they look like dollar amounts? e.g. $200 instead of just 200.
```python
# An array of the values displayed on the y-axis (150, 175, 200, etc.)
ticks = graph.get_yticks()
```
获取 y 轴上显示的所有数值（如 150、175、200 等），存储到变量 `ticks` 中
1. **`graph.get_yticks()` 功能**：
    
    `get_yticks()` 是 `AxesSubplot` 对象的方法，返回一个 numpy 数组，包含 y 轴上所有 “主刻度” 的原始数值（不是显示的文本，是底层数字）。
    
    示例返回：`array([ 0., 50., 100., 150., 200., 250.])`（假设 y 轴从 0 到 250，每 50 一个刻度）。
2. **变量 `ticks` 的本质**：
    
    是数值型数组（元素是 float 或 int），后续需要把这些数字转换成 “$+ 数字” 的字符串格式。
```python
# Format those values into strings beginning with dollar sign
new_labels = ['${}'.format(int(amt)) for amt in ticks]
```
将这些数值格式化为以美元符号（$）开头的字符串，存储到 `new_labels` 中
```python
# Set the new labels
graph.set_yticklabels(new_labels)
```
将 y 轴的原始刻度标签，替换为 `new_labels` 中的美元格式字符串
## 第二题第三题都好难，需要写代码的思维
我已经没有这个技能了，如果可以的话，每天加一个代码题，leecode
 ```python
 def blackjack_hand_greater_than(hand_1, hand_2):
    """
    Return True if hand_1 beats hand_2, and False otherwise.
    
    In order for hand_1 to beat hand_2 the following must be true:
    - The total of hand_1 must not exceed 21
    - The total of hand_1 must exceed the total of hand_2 OR hand_2's total must exceed 21
    
    Hands are represented as a list of cards. Each card is represented by a string.
    
    When adding up a hand's total, cards with numbers count for that many points. Face
    cards ('J', 'Q', and 'K') are worth 10 points. 'A' can count for 1 or 11.
    
    When determining a hand's total, you should try to count aces in the way that 
    maximizes the hand's total without going over 21. e.g. the total of ['A', 'A', '9'] is 21,
    the total of ['A', 'A', '9', '3'] is 14.
    
    Examples:
    >>> blackjack_hand_greater_than(['K'], ['3', '4'])
    True
    >>> blackjack_hand_greater_than(['K'], ['10'])
    False
    >>> blackjack_hand_greater_than(['K', 'K', '2'], ['3'])
    False
    """
     # 计算hand_1的点数
    sum1 = 0
    aces_count1 = 0
    
    for card in hand_1:
        if card in ['J', 'Q', 'K']:
            sum1 += 10
        elif card == 'A':
            aces_count1 += 1
        else:
            sum1 += int(card)
    
    # 先假设所有Ace都是1点
    sum1 += aces_count1
    
    # 尝试将Ace从1点变为11点，但不超过21
    for _ in range(aces_count1):
        if sum1 + 10 <= 21:
            sum1 += 10
    
    # 计算hand_2的点数
    sum2 = 0
    aces_count2 = 0
    
    for card in hand_2:
        if card in ['J', 'Q', 'K']:
            sum2 += 10
        elif card == 'A':
            aces_count2 += 1
        else:
            sum2 += int(card)
    
    # 先假设所有Ace都是1点
    sum2 += aces_count2
    
    # 尝试将Ace从1点变为11点，但不超过21
    for _ in range(aces_count2):
        if sum2 + 10 <= 21:
            sum2 += 10
    
    # 检查hand_1是否获胜
    # hand_1必须不超过21，并且：
    # 1. hand_1点数大于hand_2，或者
    # 2. hand_2超过21
    if sum1 > 21:
        return False  # hand_1超过21，直接输
    
    return sum1 <= 21 and (sum1 > sum2 or sum2 > 21)

# Check your answer
q3.check()
 ```


























# 小技巧
- 带 `__xxx__` 的方法（如 `__len__`）是 Python 内部用的。你写 `len(planets)` 时，Python 实际调用了 `planets.__len__()`，但你**永远不需要自己写 `__len__()`**。
- 在 Jupyter Notebook 或 Python 交互环境中，输入 `list.` 然后按 **Tab 键**，会自动列出所有可用方法。
- 想知道某个方法怎么用？用 `help()`
-  **`self` 代表“当前这个对象自己”。**
当你调用一个方法时，Python 会自动把**调用该方法的那个对象**作为第一个参数传进去，这个参数的名字就叫 `self`。
```python
planets.append('Jupiter')

list.append(planets, 'Jupiter')
```
|只有**类中的方法**才有 `self`。普通函数没有。
```python
class Dog: 
	def bark(self): 
		print("Woof! I am a dog.")
my_dog = Dog() 
my_dog.bark() # 输出: Woof! I am a dog. # 输出: Woof! I am a dog.
```

