# 第一天0810
## 第一节 Arithmetic and Vaeiables
```
print("Hello, world!")
```
```
#：注释
```
In the next question, and in most of the exercises in this course, you will have the option to uncomment to view hints and solutions. Once you feel comfortable with uncommenting, continue to the next question.
```
# Uncomment to get a hint
q3.hint()

# Uncomment to view solution
q3.solution()

# DO NOT REMOVE: Check your answer
q3.check()
```
在代码这个界面的所有变量都可以使用，不局限于一个cell里面
```
# Number of total passengers
total = len(titanic_data)
print(total)

# Number of passengers who survived
survived = (titanic_data.Survived == 1).sum()
print(survived)

# Number of passengers under 18
minors = (titanic_data.Age < 18).sum()
print(minors)
```
# 第二天250811
## 第二节 Function
a **header** and **body**
![[Pasted image 20250811110421.png]]

### Header

defines the name of the function and its argument(s)
- begins with `def`
-  the function name
- the argument
- The **argument** is the name of the variable that will be used as input to the function
- the parentheses enclosing the function argument(s) must be followed by a colon `:`
### Body
 the work that the function does
 -  indented  four spaces（ushing the space bar four times；hitting the "Tab" button once
 - takes the argument as input
 - creates a new variable
 - **return statement**，the function's output
### How to run (or "call") a function
 **Note**: When we casually refer to the `add_three()` function in this tutorial, we use empty closing parentheses after the function name.（通俗表示的方法）
### Naming functions
use only lowercase letters, with words separated by underscores instead of spaces.
#### Variable "scope"
变量作用域
报错：NameError: name 'pay_aftertax' is not defined
global scope
local scope
### Functions with multiple arguments
 add more arguments inside the parentheses in the function head and separate them with a comma
 小数表示： .22（奇奇怪怪
###  Functions with no arguments
### 练习
```python
return round(num, 2)
```
把num保留两位小数
num may be negative
- `ndigits=-1` 表示四舍五入到最接近的 **10**，
- `ndigits=-2` 表示四舍五入到最接近的 **100**，
- `ndigits=-3` 表示四舍五入到最接近的 **1000**，依此类推。
默认参数
```python
def to_smash(total_candies, n_friends=3):
    return total_candies % n_friends
```
快捷键 ctrl+/切换注释状态
# 第三天250813
## 第三节 Data Types
make sure that the actions match the data types that we have
### Integers
 positive，negative，without any fractional part
### Floats
  with fractional parts，fraction
  round:四舍五入
 `1.` (or `1.0`, `1.00`, etc) will be recognized as a float.
### Booleans
 `True` or `False`
 `z_one` is set to a boolean with value `True`
 别把位移符号跟大于小于搞混了
### Strings
 collection of characters
 get the length of a string with ：`len()`
 empty string
 If we have a string that is convertible to a float, we can use `float()`.
 This won't always work! For instance, we can convert `"10.43430"` and `"3"` to floats, but we  cannot convert `"Hello, Python!"` to a float.
 add two strings：
```
new_string = "abc" + "def"
```
 can multiply a string by an integer：
```
 newest_string = "abc" * 3
 abcabcabc
```
cannot multiply a string by a float，not possible to do subtraction or division with two strings
### 练习
boolean型乘以其他数据类型，保留原有数据类型不变，true=1，false=0。
当bool类型进行加减运算时，就是用0，1来计算，比如，true+true=2
bool型怎么取反: **not bool**
# 第四天250814
## 第四节 Conditions and Conditional Statements
### Conditions
 statements that are either `True` or `False`
```
 print(2 > 3)
```
![[Pasted image 20250814203632.png]]
### Conditional statements
the condition evaluates to `True`, then a certain block of code is executed
### "if" statements
 indentation
### "if ... else" statements
### "if ... elif ... else" statements
 "elif" (which is short for "else if")
### Example - Calculations
 use conditional statements to perform different calculations.
### Example - Multiple "elif" statements
there's no limit to the number of "elif" statements you can use
# 第五天250816
## 第五节 Intro to Lists
 holding your data, such as lists, sets, dictionaries, and tuples. In this tutorial
 o create a list, you need to use square brackets (`[`, `]`) and separate each item with a comma.
 more easily：
 - get an item at a specified position (first, second, third, etc),
- check the number of items, and
- add and remove items.
### Length
 `len(name)`
### Indexing
 zero-based indexing
 **Side Note**:（补充说明）
`print()` to print multiple items，To print multiple things in Python with a single command
### Slicing
- to pull the first `x` entries, you use `[:x]`, and
- to pull the last `y` entries, you use `[-y:]`.
 it returns a new, shortened list.
### Removing items 
列表名字.remove(“元素”)
### Adding items
列表名字.append(“元素”)，添加到末尾
### Lists are not just for strings
 including booleans, integers, and floats
 You can also get the minimum with `min(列表名字)` and the maximum with `max(列表名字)`.
 To add every item in the list, use `sum(列表名字)`.
 We can also do similar calculations with slices of the list：eg:sum(hardcover_sales[:5]
### 练习
注意切片方向，
 `num_customers[7:]`，这实际上是从第 8 天开始到结尾的所有数据（索引 7 及以后）
 `num_customers[:7]`，这是取前 7 天的数据
 `num_customers[-7:]`，`-7` 表示从倒数第 7 个元素开始到结尾，正好是最后 7 天的数据
列表切片的规则是 `[起始索引:结束索引]`，省略起始索引表示从开头开始，省略结束索引表示到结尾结束。负数索引表示从列表末尾开始计数。
所以正确的切片方式是：
- 前 n 个元素：`[:n]`
- 后 n 个元素：`[-n:]`
string转化为列表： `.split()`
```
eg: print(flowers.split(","))
```
 create a list based on the values in another list. In this question
```
 test_ratings = [1, 2, 3, 4, 5]
 
 test_liked = [i>=4 for i in test_ratings]
 print(test_liked)
 
 [False, False, False, True, True]
```
- `for i in test_ratings`：遍历 `test_ratings` 列表中的每个元素，变量 `i` 依次代表每个元素的值。
- `i >= 4`：对每个元素 `i` 进行判断，检查它是否大于或等于 4。如果是，结果为 `True`；否则为 `False`。
语法规则：**列表推导式（List Comprehension）** 语法
```python
[表达式 for 变量 in 可迭代对象]
```
- **执行顺序**：先遍历 “可迭代对象”（如列表、字符串等）中的每个元素，将元素赋值给 “变量”，再对变量执行 “表达式” 操作，最后将所有结果收集成一个新列表。
列表推导式还可以添加条件判断，语法为：
```python
[表达式 for 变量 in 可迭代对象 if 条件]
```
条件成立才保留，再通过前一个表达式
例题答案的小巧思：
![[Pasted image 20250816213720.png]]
前一年是 “当前年份” 的上一个位置，索引比最后一个元素小 1
(n-1) - yrs_ago = n - yrs_ago - 1
