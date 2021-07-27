[TOC]



# `Python3` 基础语法

## 编码

默认情况下，`Python 3` 源码文件以 `UTF-8` 编码。 也可以在首行代码中为源码文件指定不同的编码：

```python
# -*- coding: GBK -*-
```

上述定义允许在源文件中使用 `GBK` 字符集中的字符编码，对应适合语言为中文。

## 标识符

- 第一个字符必须是字母表中字母或下划线 **_** 。
- 标识符的其他的部分由字母、数字和下划线组成。
- 标识符对大小写敏感。

在 `Python 3` 中，可以用中文作为变量名，非 `ASCII` 标识符也是允许的。

## python保留字

保留字即关键字，不能把它们用作任何标识符名称。`Python` 的标准库提供了一个 `keyword` 模块，可以输出当前版本的所有关键字：

```python
import keyword
print(keyword.kwlist)
#==》['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

## 行与缩进

`python` 使用缩进来表示代码块，不需要使用大括号 `{}` 。

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。

```python
# 同一个代码块的语句必须包含相同的缩进空格数
if 1 + 1 == 2:
    print("1 + 1 = 2")
else:
    print("1 + 1 != 2")
#==》1 + 1 = 2
```

## 多行语句

`Python` 通常是一行写完一条语句，但如果语句很长，使用反斜杠 `\` 来实现多行语句。

```python
# 使用反斜杠 \ 来实现多行语句。
three = 1 + \
        1 + \
        1
print(three)
#==》3
```

在 `[]`, `{}`, 或 `()` 中的多行语句，不需要使用反斜杠 `\`。

```python
# 在 [], {}, 或 () 中的多行语句，不需要使用反斜杠
numbers = [0, 1, 2, 3, 4,
           5, 6, 7, 8, 9]
print(numbers)
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## 同一行显示多条语句

`Python` 可以在同一行中使用多条语句，语句之间使用分号 `;` 分割。

```python
# 在同一行中使用多条语句，语句之间使用分号 ; 分割。
print(1 + 1); print(2 + 2); print(3 + 3)
#==》2
#==》4
#==》6
```

## `input` 输入和`print` 输出

`input` 将输入数据作为字符串赋值给变量

`print` 默认输出是换行的，如果要实现不换行需要在变量末尾加上 `end=" "`

```python
# input输入
name1 = input()
#《==tom
name2 = input()
#《==jerry
print(name1.title() + " and " + name2.title())
#==》Tom and Jerry
```

## 判断语句

### `in` 和 `not in` 

```python
# in 和 not in
letters = ("a", "b", "c", "d", "e", "f", "g")
print("a" in letters)
print("h" not in letters)
#==》True
#==》True
```

### `if` 语句

`if` 条件判断语句 `1:`
    条件判断语句 `1` 为真，执行语句 `1`
`elif` 条件判断语句 `2:`
    条件判断语句 `1` 为假，条件判断语句 `2`为真，执行语句 `2`
`else:`
    上述条件判断为假，执行语句 `3`

```python
# if判断语句
if 1 + 1 == 2:
    print("1 + 1 == 2")
#==》1 + 1 == 2
```

#### 条件与：`and` 

```python
# and
number = int(input())
#《==5
if number > 0 and number < 10:
    print(f"0 < {number} < 10")
#==》0 < 5 < 10
```

#### 条件或：`or` 

```python
# or
number = int(input())
#《==20
if number < 0 or number > 10:
    print(f"0 > {number} or {number} > 10")
#==》0 > 20 or 20 > 10
```

### 三目运算符 `? : `

条件语句 `?` 条件为真 `:` 条件为假

```python
# if判断语句
1 + 1 == 2 ? print("1 + 1 == 2") : print("1 + 1 != 2")
#==》1 + 1 == 2
```

## `range()` 函数

`range(起始, 结束, 步长)`
步长默认为 `1` ，可省略：`range(起始, 结束)`
起始默认为 `0` ，步长省略时可省略：`range(结束)`
起始和步长都可省略，结束不可省略：`range(结束)`
起始与结束区间为：左闭右开区间，即： `[起始, 结束)` （无特殊说明默认此范围）

```python
# range()函数
for i in range(1, 10, 1):
    print(i, end=" ")
print("\n")
for i in range(1, 10, 2):
    print(i, end=" ")
print("\n")
for i in range(10):
    print(i, end=" ")
#==》1 2 3 4 5 6 7 8 9 
#==》
#==》1 3 5 7 9 
#==》
#==》0 1 2 3 4 5 6 7 8 9 
```

## 循环语句

### `while` 循环

`while` 条件语句:
    循环语句

```python
# while循环
i = 0
while i < 10:
    print(i, end=" ")
    i += 1
#==》0 1 2 3 4 5 6 7 8 9 
```

#### while 循环使用 else 语句

如果 while 后面的条件语句为 false 时，则执行 else 的语句块。

```python
count = 0
while count < 5:
   print (count, " 小于 5")
   count = count + 1
else:
   print (count, " 大于或等于 5")
#==》0  小于 5
#==》1  小于 5
#==》2  小于 5
#==》3  小于 5
#==》4  小于 5
#==》5  大于或等于 5
```

### `for` 循环

`for` 变量  `in`  可迭代对象 `:`

​    循环语句

```python
# for循环
for i in range(10):
    print(i, end=" ")
#==》0 1 2 3 4 5 6 7 8 9 
```

## `break` 语句

`break` 跳出当前循环，并结束循环

## `continue` 语句

`continue` 跳出当前循环，继续下一次循环

## `import` 与 `from...import`

在 `python` 用 `import` 或者 `from...import` 来导入相应的模块。

将整个模块 `module` 导入，格式为： `import module` 

从某个模块中导入某个函数，格式为： `from module import function` 

从某个模块中导入多个函数，格式为： `from module import function 1, function 2, function 3` 

将某个模块中的全部函数导入，格式为： `from module import *` 

给模块起别名，格式为：`import module as m` 

# 变量和简单的数据类型

## 变量

```Python
name = "张三"
print(name)
#==》张三
```

`name` 就是一个变量，他可以被赋值为`张三`，也可以被赋值为`李四`

### 注意

1. 变量名只能包含字母、数字和下划线。非法命名：`@name`
2. 变量名不能以数字开头。非法命名：`123name`
3. 变量名不能包含空格。非法命名：`na me`
4. 不能将Python中的关键字和函数名作为变量名。非法命名：`print`

### 变量是标签：

变量通常被描述为可用于储存值的盒子。

具体含义为：变量通常作为 `hash` 的 `key` ，指向一片内存空间，空间内存放着变量的数据即 `hash` 的 `value` 。

## 字符串

### 字符串

字符串就是一系列字符，在Python中，用引号括起的都是字符串，其中引号可以是单引号：`''` ，也可以是双引号：`""` ，在引号内包含引号时，通常以单双交替的形式使用。

```python
message = "双引号包含‘单引号’"
print(message)
#==》双引号包含‘单引号’
```

### 使用方法对字符串进行操作

#### `.title()` 方法：将字符串首字母大写

```python
# 使用title方法，首字母大写
message = "using title"
print(message.title())
#==》Using Title
```

#### `.upper()` 方法：将字符串转换为大写

```python
# 使用upper方法，将字符串全部转换为大写
message = "using upper"
print(message.upper())
#==》USING UPPER
```

#### `.lower()` 方法：将字符串全部转换为小写

```Python
# 使用lower方法，将字符串全部转换为小写
message = "using lower"
print(message.lower())
#==》using lower
```

### `str.format()` 的基本使用

早期版本）括号及其里面的字符 (称作格式化字段) 将会被 `format()` 中的参数替换。

```python
Python3.5或更早版本：
message_1 = "using upper"
message_2 = "using lower"
message="{} and {}".format(message_1,message_2)
print(message)
#==》USING UPPER and using lower
```

最新版本）要在字符串中插入变量的值，可在前引号前加上字母 f 再将要插入的变量放在花括号内。

```python
# 在字符串中使用变量
message_1 = "using upper"
message_2 = "using lower"
message = f"{message_1.upper()} and {message_2.lower()}"
print(message)
print(f"{message_1.upper()} and {message_2.lower()}")
#==》USING UPPER and using lower
#==》USING UPPER and using lower
```

#### 括号中使用数字

在括号中的数字用于指向传入对象在 `format()` 中的位置

#### 括号中使用参数

在括号中使用了关键字参数，那么它们的值会指向使用该名字的参数。

#### 括号中数字 + 参数

位置及关键字参数可以任意的结合

#### 使用函数进行转换

`!a` (使用 `ascii()` )，`!s` (使用 `str()` ) 和 `!r` (使用 `repr()` ) 可以用于在格式化某个值之前对其进行转换

#### 可选项 `:` 和格式标识符可以跟着字段名

#### 在 `:` 后传入一个整数, 可以保证该域至少有这么多的宽度

### Python 字符串格式化

`Python` 支持格式化字符串的输出 。尽管这样可能会用到非常复杂的表达式，但最基本的用法是将一个值插入到一个有字符串格式符 `%s` 的字符串中。

在 `Python` 中，字符串格式化使用与 `C` 中 `printf` 函数一样的语法。

`python` 字符串格式化符号:

| 符  号 | 描述                                    |
| :----- | :-------------------------------------- |
| `%c`   | 格式化字符及其ASCII码                   |
| `%s`   | 格式化字符串                            |
| `%d`   | 格式化整数                              |
| `%u`   | 格式化无符号整型                        |
| `%o`   | 格式化无符号八进制数                    |
| `%x`   | 格式化无符号十六进制数                  |
| `%X`   | 格式化无符号十六进制数（大写）          |
| `%f`   | 格式化浮点数字，可指定小数点后的精度    |
| `%e`   | 用科学计数法格式化浮点数                |
| `%E`   | 作用同 `%e ` ，用科学计数法格式化浮点数 |
| `%g`   | `%f` 和`%e` 的简写                      |
| `%G`   | `%F` 和 `%E` 的简写                     |
| `%p`   | 用十六进制数格式化变量的地址            |

格式化操作符辅助指令

| 符号    | 功能                                                         |
| :------ | :----------------------------------------------------------- |
| `*`     | 定义宽度或者小数点精度                                       |
| `-`     | 用做左对齐                                                   |
| `+`     | 在正数前面显示加号 `( + )`                                   |
| `<sp>`  | 在正数前面显示空格                                           |
| `#`     | 在八进制数前面显示零 `('0')`，在十六进制前面显示 `'0x'` 或者`'0X'` (取决于用的是 `'x'` 还是 `'X'` ) |
| `0`     | 显示的数字前面填充 `'0'` 而不是默认的空格                    |
| `%`     | `'%%'` 输出一个单一的`'%'`                                   |
| `(var)` | 映射变量(字典参数)                                           |
| `m.n.`  | `m` 是显示的最小总宽度, `n` 是小数点后的位数(如果可用的话)   |

### Python字符串运算符

下表实例变量 a 值为字符串 "Hello"，b 变量值为 "Python"：

| 操作符 | 描述                                                         | 实例                             |
| :----- | :----------------------------------------------------------- | :------------------------------- |
| +      | 字符串连接                                                   | `a + b` 输出结果： `HelloPython` |
| *      | 重复输出字符串                                               | `a*2` 输出结果：`HelloHello`     |
| []     | 通过索引获取字符串中字符                                     | `a[1]` 输出结果 `e`              |
| [ : ]  | 截取字符串中的一部分，遵循左闭右开原则，`str[0:2]` 是不包含第 3 个字符的。 | a[1:4] 输出结果 `ell`            |
| in     | 成员运算符 - 如果字符串中包含给定的字符返回 `True`           | '`H' in a`  输出结果 `True`      |
| not in | 成员运算符 - 如果字符串中不包含给定的字符返回 `True`         | `'M' not in a` 输出结果 `True`   |
| r/R    | 原始字符串 - 原始字符串：所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 原始字符串除在字符串的第一个引号前加上字母 `r`（可以大小写）以外，与普通字符串有着几乎完全相同的语法。 | `print( r'\n' ) print( R'\n' )`  |
| %      | 格式字符串                                                   | 请看上一节内容。                 |

### 使用 `\t` 和 `\n` 添加空白

```python
#使用制表符或换行符来添加空白
print("Python")
print("\tPython")
print("\nPython")
#==》Python
#==》	Python
#==》
#==》Python
```

### 删除空白

#### `.rstrip()` 方法：删除末尾空白

```python
#使用rstrip方法删除末尾空白
message = "Python "
print(message)
print(message.rstrip())
#==》Python 
#==》Python
```

#### `.lstrip()` 方法：删除开头空白

```python
#使用lstrip方法删除末尾空白
message = " Python"
print(message)
print(message.lstrip())
#==》 Python
#==》Python
```

#### `.strip()` 方法：删除空白

```python
#使用strip方法删除空白
message = " Python "
print(message)
print(message.strip())
#==》 Python 
#==》Python
```

## 数

### 运算符：

| 运算 | 运算符 |
| ---- | ------ |
| 加   | +      |
| 减   | -      |
| 乘   | *      |
| 除   | /      |
| 取余 | %      |
| 整除 | //     |
| 幂   | **     |
| 自加 | ++     |
| 自减 | --     |

### 数中的下划线

使用下划线将数字分组使其更清晰易读。

```python
# 使用下划线将数字分组使其更清晰易读
Number = 10_000_000_000
print(Number)
#==》10000000000
```

### 同时给多个变量赋值

Python将按顺序将每个值赋给对应的变量，只要变量和值的个数相同，Python就能正确地关联起来。

```python
# 同时给多个变量赋值
x, y, z = 0, 0, 0
print(x, y, z)
#==》0 0 0
```

## 注释

### 如何写注释

```python
# 如何编写注释

# 这里是用 "#" 标识的注释

'''
这里是使用三个单引号标识的多行注释
'''

"""
这里是使用三个双引号标识的多行注释
"""
```

# 列表简介

## 列表

> 列表是由一系列按特定顺序排列的元素组成。你可以创建包含字母表中所有字母、数字 0 ~ 9 的列表，也可以将任何东西加入列表中，列表中的元素之间没有任何关系。列表通常包含多个元素。

### 列表

在Python中，用方括号 `[ ]` 表示列表，并用逗号分割其中的元素。

```python
# 列表
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers)
#==》[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 访问列表

列表是有序集合，因此要访问列表任意元素，只需要将该元素的位置（索引）告诉 `Python` 即可。

```python
# 访问列表元素
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers[0])
#==》1
```

当请求获取列表元素时，`Python` 只返回该元素，而不包括方括号。

### 索引从 `0` 开始而不是从 `1` 开始

与大多数编程语言相同，在Python中列表的索引是从 `0` 开始的，而不是从 `1` 开始的。

```python
# 索引从 0 开始而不是从 1 开始
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers[0])
print(numbers[1])
#==》1
#==》2
```

Python为访问列表元素提供了一种特殊的语法，即负数索引。通过将索引指定为 `-1` ，可让 `Python` 返回最后一个列表元素，并依次递推。

```python
# 负数索引
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers[8])
print(numbers[-1])
#==》9
#==》9
```

### 添加元素

#### `.append()` 方法：在列表末尾添加元素

```python
# 添加列表元素
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8]
print(numbers)
numbers.append(9)
print(numbers)
#==>numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8]
#==>numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### `.insert()` 方法：在列表中间插入元素

```python
# 插入列表元素 .insert(索引, 值)
numbers = [0, 1, 2, 3, 4, 6, 7, 8, 9]
print(numbers)
numbers.insert(5, 5)
print(numbers)
#==>[0, 1, 2, 3, 4, 6, 7, 8, 9]
#==>[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 删除元素

#### 使用 `del` 语句删除任意位置元素

```python
# del删除元素
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers)
del numbers[9]
print(numbers)
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8]
```

#### `.pop()` 方法：删除任意位置元素，并能够接着使用

```python
# 使用方法pop()删除元素
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers)
popped_numbers = numbers.pop(9)
print(popped_numbers)
print(numbers)
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
#==》9
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8]
```

#### `.remove()` 方法： 根据值删除元素

```Python
# 根据值删除元素 .remove(value)
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(numbers)
numbers.remove(9)
print(numbers)
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8]
```

### 修改元素

```python
# 修改列表元素
numbers = [0, 1, 2, 3, 4, 6, 6, 7, 8, 9]
print(numbers)
numbers[5] = 5
print(numbers)
#==》[0, 1, 2, 3, 4, 6, 6, 7, 8, 9]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 遍历链表

```python
# 遍历列表
numbers = list(range(10))
# 方式一：
for i in range(10):
    print(numbers[i], end=" ")
# 方式二：
for i in numbers:
    print(i, end=" ")
#==》0 1 2 3 4 5 6 7 8 9 
#==》0 1 2 3 4 5 6 7 8 9 
```

## 操作列表

### `.sort()` 方法：对列表永久排序

```python
# 使用方法sort()对列表永久排序
numbers = [1, 2, 3, 6, 5, 4, 7, 8, 9, 0]
print(numbers)
numbers.sort()
print(numbers)
#==》[1, 2, 3, 6, 5, 4, 7, 8, 9, 0]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 使用函数 `sorted()` 对列表临时排序

函数 `sorted()` 能够按特定顺序将列表元素进行排序，而不改变原列表中的顺序

```python
# 使用函数sorted()对列表临时排序
numbers = [1, 2, 3, 6, 5, 4, 7, 8, 9, 0]
print(numbers)
numbers_sorted = sorted(numbers)
print(numbers)
print(numbers_sorted)
print(sorted(numbers))
#==》[1, 2, 3, 6, 5, 4, 7, 8, 9, 0]
#==》[1, 2, 3, 6, 5, 4, 7, 8, 9, 0]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### `.reverse()` 方法：倒序打印列表

方法 `reverse()` 永久性地修改列表元素的排列顺序。

```python
# 使用方法reverse()对列表倒序
numbers = [1, 2, 3, 6, 5, 4, 7, 8, 9, 0]
print(numbers)

#排序
numbers.sort()
numbers_sorted = sorted(numbers)

#倒序
numbers.reverse()
numbers_sorted.reverse()

#打印
print(numbers)
print(numbers_sorted)
#==》[1, 2, 3, 6, 5, 4, 7, 8, 9, 0]
#==》[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
#==》[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

### 使用函数 `len()` 获取列表长度

```python
# 使用函数len()获取列表长度
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
length = len(numbers)
print(length)
#==》10
```

### 使用函数 `max()` 获取列表最大值

```python
#使用函数 `max()` 获取列表最大值
numbers = list(range(10))
print(max(numbers))
#==》9
```

### 使用函数 `min()` 获取列表最小值

```python
#使用函数 `min()` 获取列表最小值
numbers = list(range(10))
print(min(numbers))
#==》0
```

### 使用函数 `sum()` 获取列表数字和

```python
#使用函数 `sum()` 获取列表数字和
numbers = list(range(10))
print(sum(numbers))
#==》45
```

## 列表解析

列表解析将 `for` 循环和创建新元素的代码合并成一行，并自动附加新元素。

`列表标签名 = [变量名 for 变量名 in 可迭代对象]` 

```python
# 列表解析
numbers = [i**2 for i in range(10)]
print(numbers)
#==》[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

## 列表切片

### 创建切片

要创建切片，须指定起始和结束的索引。

未指定起始索引默认从列表第一个元素开始，未指定结束索引默认到列表最后一个元素结束。

注意范围是：`[起始索引, 结束索引)` 

```python
# 列表切片
numbers = list(range(10))
print(numbers[1:5])
print(numbers[:5])
print(numbers[5:])
#==》[1, 2, 3, 4]
#==》[0, 1, 2, 3, 4]
#==》[5, 6, 7, 8, 9]
```

### 使用切片复制列表

```python
# 使用切片复制链表
numbers = list(range(10))
numbers_copy = numbers[:]
print(numbers)
print(numbers_copy)
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

注意：使用切片复制的列表于原列表的地址不相同，通过直接赋值的方式复制链表只是将原列表的地址进行拷贝。

# 元组

## 定义元组

`Python` 的元组与列表类似，不同之处在于元组的元素不能修改。

元组使用小括号，列表使用方括号。

```python
# 定义元组
letters = ("a", "b", "c", "d", "e", "f", "g")
print(letters)
print(letters[0])
#==》('a', 'b', 'c', 'd', 'e', 'f', 'g')
#==》a
```

## 遍历元组

```python
# 遍历元组
letters = ("a", "b", "c", "d", "e", "f", "g")
for i in letters:
    print(i)
#==》a
#==》b
#==》c
#==》d
#==》e
#==》f
#==》g
```

### 修改元组变量

虽然不能修改元组的元素，但可以给储存元组的变量赋值。因此，如果要修改元组，可重新定义整个元组。

```python
# 修改元组变量
letters = ("a", "b", "c", "d", "e", "f", "g")
print(letters)
letters = ("h", "i", "j", "k", "l", "m", "n")
print(letters)
#==》('a', 'b', 'c', 'd', 'e', 'f', 'g')
#==》('h', 'i', 'j', 'k', 'l', 'm', 'n')
```

# 字典

在 `python` 中，字典是一系列键值对，每个键都与一个值相关联，可以使用键来访问相关联的值。与键相关联的值可以是数、字符串、列表、字典或任意 `python` 对象。

## 使用字典

### 创建字典

在 `python` 中，字典用放在花括号 `{}` 中的一系列键值对表示。

```python
# 创建字典
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
print(ASCII)
#==》{'a': 97, 'b': 98, 'c': 99, 'd': 100}
```

### 访问字典

要获取与键相关联的值，可依次指定字典名和放在方括号内的键。

```python
# 访问字典
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
print(ASCII['a'])
#==》
```

### 添加键值对

字典是一种动态结构，可随时添加键值对。

添加键值对时，可依次指定字典名、用方括号括起的键和相关联的值。

```python
# 添加键值对
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
print(ASCII)
ASCII['e'] = 101
print(ASCII)
#==》{'a': 97, 'b': 98, 'c': 99, 'd': 100, 'e': 101}
```

### 修改字典中的值

要修改字典中的值，可依次指定字典名、用方括号括起的键，将新值重新赋值给该键即可。

```python
# 修改字典中的值
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100, 'e': 102}
print(ASCII)
ASCII['e'] = 101
print(ASCII)
#==》{'a': 97, 'b': 98, 'c': 99, 'd': 100, 'e': 102}
#==》{'a': 97, 'b': 98, 'c': 99, 'd': 100, 'e': 101}
```

### 删除键值对

使用 `del` 语句彻底删除键值对

```python
# 删除键值对
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100, 'e': 101}
print(ASCII)
del ASCII['e']
print(ASCII)
#==》{'a': 97, 'b': 98, 'c': 99, 'd': 100, 'e': 101}
#==》{'a': 97, 'b': 98, 'c': 99, 'd': 100}
```

### 遍历字典

#### 遍历键值对

`for 变量1(key), 变量2(value) in 字典名.items()` 

```python
# 遍历键值对
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
for key, value in ASCII.items():
    print(f"{key} : {value}")
#==》a : 97
#==》b : 98
#==》c : 99
#==》d : 100
```

#### 遍历键

```python
# 遍历键
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
for key in ASCII:  # 隐式
    print(key)
for key in ASCII.keys():  # 显式
    print(key)
#==》a
#==》b
#==》c
#==》d
#==》a
#==》b
#==》c
#==》d
```

### 遍历值

```python
# 遍历值
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
for value in ASCII.values():
    print(value)
#==》97
#==》98
#==》99
#==》100
```

## 操作字典

### `.get()` 方法 ：访问值

使用 `get()` 来访问值，当指定键不存在时返回一个默认值，避免错误。

方法 `get()` 的第一个参数用于指定键，第二个从参数为指定键不存在时返回的默认值（可省略）。

```python
# 使用 get() 来访问值
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
print(ASCII.get('e',"指定键不存在"))
print(ASCII.get('e'))
#==》指定键不存在
#==》None
```

### `.items()` 方法：返回键值对列表

```python
# 返回键值对列表
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
for key, value in ASCII.items():
    print(f"{key} : {value}")
#==》a : 97
#==》b : 98
#==》c : 99
#==》d : 100
```

### `.keys()` 方法：返回键列表

```python
# 返回键列表
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
for key in ASCII.keys():  # 显式
    print(key)
#==》a
#==》b
#==》c
#==》d
```

### `.values()` 方法：返回值列表

```python
# 返回值列表
ASCII = {'a': 97, 'b': 98, 'c': 99, 'd': 100}
for value in ASCII.values():
    print(value)
#==》97
#==》98
#==》99
#==》100
```

# 函数

## 定义函数

`def` 函数名 (形参) :

```python
# 定义函数
def UserPrint():
    print("Hello User !")

    
# 调用函数
UserPrint()
#==>Hello User !
```

**注意：** 先定义再调用

## 形参实参

形参：函数完成工作所需要的的信息

实参：调用函数时传递给函数的信息

```python
# 形参：username
def UserPrint(username):
    print(f"Hello, {username}!")


# 实参：User
User = "Tom and Jerry"
UserPrint(User)
#==》Hello, Tom and Jerry!
```

### 位置实参

位置实参：函数调用中的每个实参都关联到函数定义中的一个形参

```python
# 位置实参
def UserPrint(user1, user2):
    print(f"Hello, {user1} and {user2}!")


UserPrint("Tom", "Jerry")
```

### 关键字实参

关键字实参：传递给函数的名称值对，直接在实参中将名称和值关联起来

```python
# 关键字实参
def UserPrint(user1, user2):
    print(f"Hello, {user1} and {user2}!")


UserPrint(user2="Jerry", user1="Tom")
#==》Hello, Tom and Jerry!
```

### 默认值

默认值：在调用函数中给形参提供实参时，`python` 将使用指定的实参值，否则，将使用形参的默认值

```python
# 默认值
def UserPrint(user1, user2="Jerry"):
    print(f"Hello, {user1} and {user2}!")


UserPrint("Tom")
#==》Hello, Tom and Jerry!
```

## 返回值

```python
# return返回值
def UserPrint(user1, user2):
    return f"Hello, {user1} and {user2}!"


# 接收返回值
user = UserPrint("Tom", "Jerry")
print(user)
#==》Hello, Tom and Jerry!
```

## 传递实参

### 传递可修改的列表

```python
# 传递可修改列表
def delLastNumbers(nums):
    del nums[9]


numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
delLastNumbers(numbers)
print(numbers)
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8]
```

### 传递不可修改的列表

为解决函数内的修改会影响原列表的问题，可向函数传递列表的副本，这样，函数所做的任何修改都只影响副本。

```python
# 传递不可修改的列表
def delLastNumbers(nums):
    del nums[9]
    return nums


numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
delNums = delLastNumbers(numbers[:])
print(delNums)
print(numbers)
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8]
#==》[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 传递任意数量的实参

使用 `*` 创建一个空元组，并将接收到的值都封装在这个元组中

```python
# 传递任意数量的实参
def printNumbers(*nums):
    print(nums)


printNumbers(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
#==》(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```

### 传递任意数量的关键字实参

使用 `**` 创建一个空字典，并将接收到的键值都封装在这个字典中

```python
# 传递任意数量的关键字实参
def printDic(**dic):
    print(dic)


printDic(number=1, letter='a')
#==》{'number': 1, 'letter': 'a'}
```

# 类

- **类(Class):** 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
- **方法：**类中定义的函数。
- **属性：**类中定义的变量。
- **数据成员：**类变量或者实例变量用于处理类及其实例对象的相关的数据。
- **方法重写：**如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖`(override)`，也称为方法的重写。
- **局部变量：**定义在方法中的变量，只作用于当前实例的类。
- **实例变量：**在类的声明中，属性是用变量来表示的，这种变量就称为实例变量，实例变量就是一个用 `self` 修饰的变量。
- **继承：**即一个派生类`(derived class)`继承基类`(base class)` 的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。
- **实例化：**创建一个类的实例，类的具体对象。
- **对象：**通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

## 创建类

```python
# 定义类
class ClassName:
    print("This is a class")
#This is a class
```

## 创建实例

```
# 创建矩形实例
class Rectangle:
    def __init__(self, length, width):
        print(f"初始化一个长为：{length}, 宽为：{width} 的矩形")
        self.length = length
        self.width = width


square = Rectangle(10, 10)
#==》初始化一个长为：10, 宽为：10 的矩形
```

## 类操作

### 访问属性

```python
# 访问属性
class Rectangle:
    def __init__(self, length, width):
        print(f"初始化一个长为：{length}, 宽为：{width} 的矩形")
        self.length = length
        self.width = width


square = Rectangle(10, 10)
print(f"正方形的长是：{square.length} 宽是：{square.width}")
#==》初始化一个长为：10, 宽为：10 的矩形
#==》正方形的长是：10 宽是：10
```

### 调用方法

```python
# 调用方法
class Rectangle:
    def __init__(self, length, width):
        self.length = length
        self.width = width

    def printRectangle(self):
        print(f"矩形的长是：{self.length} 宽是：{self.width}")


square = Rectangle(10, 10)
square.printRectangle()
#==》矩形的长是：10 宽是：10
```

### 设置默认值

```python
# 设置默认值
class Rectangle:
    def __init__(self):
        self.length = 0
        self.width = 0

    def printRectangle(self):
        print(f"矩形的长是：{self.length} 宽是：{self.width}")


r_0 = Rectangle()
r_0.printRectangle()
#==》矩形的长是：0 宽是：0
```

### 修改属性值

#### 直接修改属性值

```python
# 直接修改属性值
class Rectangle:
    def __init__(self):
        self.length = 0
        self.width = 0

    def printRectangle(self):
        print(f"矩形的长是：{self.length} 宽是：{self.width}")


rect = Rectangle()
rect.length = 20
rect.width = 10
rect.printRectangle()
#==》
```

#### 通过方法修改属性值

```python
# 通过方法修改属性值
class Rectangle:
    def __init__(self):
        self.length = 0
        self.width = 0

    def modifyRectangle(self, length, width):
        self.length = length
        self.width = width

    def printRectangle(self):
        print(f"矩形的长是：{self.length} 宽是：{self.width}")


rect = Rectangle()
rect.modifyRectangle(20, 10)
rect.printRectangle()
#==》矩形的长是：20 宽是：10
```

## 类继承

### 继承

创建子类时，父类必须包含在当前文件中，且为与子类前面，子类包含父类 `__init__()` 方法中定义的所有属性。

```Python
# 继承
class Rectangle:
    def __init__(self):
        self.length = 0
        self.width = 0

    def printRectangle(self):
        print(f"矩形的长是：{self.length} 宽是：{self.width}")


class Square(Rectangle):
    def __init__(self, edge):
        super().__init__()
        self.length = self.width = self.edge = edge

    def printEdge(self):
        print(f"正方形的边长是：{self.edge}")


square = Square(10)
square.printEdge()

#==》正方形的边长是：10
```

### `super()` 函数

`super()` 是一个特殊的函数，用于调用父类的方法。

```Python
# super() 函数
class Rectangle:
    def __init__(self):
        self.length = 0
        self.width = 0

    def printRectangle(self):
        print(f"矩形的长是：{self.length} 宽是：{self.width}")


class Square(Rectangle):
    def __init__(self, edge):
        super().__init__()
        self.length = self.width = self.edge = edge

    def printEdge(self):
        print(f"正方形的边长是：{self.edge}")
        super().printRectangle()


square = Square(10)
square.printEdge()
#==》正方形的边长是：10
#==》矩形的长是：10 宽是：10
```

### 重写

```python
# 重写
class Rectangle:
    def __init__(self):
        self.length = 0
        self.width = 0

    def printEdge(self):
        print(f"矩形的长是：{self.length} 宽是：{self.width}")


class Square(Rectangle):
    def __init__(self, edge):
        super().__init__()
        self.length = self.width = self.edge = edge

    def printEdge(self):
        print(f"正方形的边长是：{self.edge}")


square = Square(10)
square.printEdge()
#==》正方形的边长是：10
```

## 类方法

### `__init__` ：构造函数，在生成对象时调用

类中的函数称为方法，方法 `__init__()` 是一个特殊的方法，每当创建一个实例时，都会默认运行它。

在这个方法定义中，形参 `self` 必不可少，而且必须位于其他形参前面。`self` 是指向实例本身的引用，让实例能够访问类中的属性和方法。 

```python
# 方法 __init__ :构造函数
class Rectangle:
    def __init__(self, length, width):
        print(f"初始化一个长为：{length}, 宽为：{width} 的矩形")
        self.length = length
        self.width = width


square = Rectangle(10, 10)
#==》初始化一个长为：10, 宽为：10 的矩形
```

### `__del__` ：析构函数，释放对象时使用

### `__repr__`：打印，转换

### `__setitem__` ：按照索引赋值

### `__getitem__` ：按照索引获取值

### `__len__` ：获得长度

### `__cmp__` ：比较运算

### `__call__` ：函数调用

### `__add__` ：加运算

### `__sub__` ：减运算

### `__mul__` ：乘运算

### `__truediv__` ：除运算

### `__mod__` ：求余运算

### `__pow__` ：乘方

# 文件

## 写入文件

读取模式：`r` 

写入模式：`w` 

附加模式：`a` 

读写模式：`r+` 

```python
import codecs

# 写入文件, 默认GBK, 不需要导入模块
filename = 'Test.txt'
with open(filename, 'w') as file_object:
    file_object.write("这是一个测试文件")

# 写入文件, 以utf-8
filename = 'Test.txt'
with codecs.open(filename, 'w', 'utf8') as file_object:
    file_object.write("这是一个测试文件")
#Test.txt==》这是一个测试文件
```

## 读取文件

### 全部读取

```python
import codecs

# 读取文件, 默认GBK, 不需要导入模块
#filename = 'Test.txt'
#with open(filename) as file_object:
#    contents = file_object.read()
#print(contents)

# 读取文件, 以utf-8
filename = 'Test.txt'
with codecs.open(filename, 'r', 'utf-8') as file_object:
    contents = file_object.read()
print(contents)
#==》这是一个测试文件
```

### 逐行读取

#### 常规读取

```python
# 逐行读取文件, 默认GBK, 不需要导入模块
filename = 'Test.txt'
with open(filename) as file_object:
    for line in file_object:
        print(line)
#==》这是一个测试文件
```

#### `.readlines()` 方法：

```python
# .readlines()方法: 从文件中读取每一行, 并储存在一个列表中
filename = 'Test.txt'
with open(filename) as file_object:
    lines = file_object.readlines()

print(lines)
#==》['这是一个测试文件']
```