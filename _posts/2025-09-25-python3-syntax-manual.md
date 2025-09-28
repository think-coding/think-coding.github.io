---
layout: post
title: Pythonh3 语法速查手册
feature-img: "assets/img/feature-img/python-banner.png"
thumbnail: "assets/img/thumbnails/feature-img/python-banner.png"
author: think-coding
categories: Document
tags: [python3, syntax]
---

python3 作为一款开发效率高、自然语言的开发语言广泛应用于各个领域。
俗话说：好记性不如烂笔头，有时长时间不用的语法会突然想不起来，翻阅资料很浪费时间，所以整理一篇速查手册备用。

# 1. 输出字符串
```python
print("Hello world!")
print("Hello" + " " + "world!")
print("Hello" + input("What's your name?") + "!")

name = "david"
print("name: " + name)
# 输出 只会输出字符串和变量的组合
name: david

print("name: ", name)
# 输出 , 和 name 之间的空格也会被输出
name:  david

print("name: {}".format(name))
print(f"name: {name}")
print("length: " + str(123) )
print("length: " + str(len(name)) )

```

# 2. 变量 & 赋值
```python
name = "David"
age = 20
age += 10   # 30
```

# 3. 内置函数
```python
# 字符长度
len("David")
# 数据类型
type("abc")
type(123)
type(3.1415926)
type(True)
# 类型转换
int()
float()
str()
bool()
# 求和
sum(1, 2, 3)    # 6
# 平均值
avg(1, 2, 3)    # 2
# 四舍五入
round(3.1415)   # 3
round(3.1415, 2)    # 3.14
# 范围  0<= & <10
range(0, 10)
# 大小写转换
"abc".upper()   # ABC
"aBC".lower()   # abc
# 去除空格
" s ff dgd   ".strip()  # "s ff dgd"
# 拆分字符串
"2025-09-25T10:30:30".split("T")    # ["2025-09-25", "10:30:30"]
# 字符串替换
"hello wrold".replace("wro", "321")     # 'hello 321ld'
```

# 4. 数据类型
```python
# 列表
[1, 2, 3, 4, 5]
# 元组
(1, 2, 3, 4, 5)
# 字典
{"index": 1, "value": "abc"}
# 布尔
True
False
```

# 5. 算数运算符
```python
123 + 456
456 - 123
123 * 456
8 / 2
5 // 2  # 整除
2 ** 3  # 2^3, 次方, 幂
7 % 4   # 3
```

# 6. 条件运算符
```python
<
>
<=
>=
<>
!=
```

# 7. 逻辑运算符
```python
if a == 1 and b == 2:
    print("ok")

if a == 1 or b == 2:
    print("ok")

if not a:
    print("ok")
```

# 8. 条件判断
```python
if condition:
    do this
else:
    do this

if condition1:
    do this
elif condition2:
    do this
elif ...:
    do this
else:
    do this

```

# 9. 偶数 & 奇数
```python
if x % 2 == 0:
    print("even")
else:
    print("odd")
```

# 10. 列表
```python
fruits = ["Cherry", "Apple", "Pear"]
fruits[0]   # Cherry
fruits[-1]  # Pear
len(fruits) # 3
fruits.join(" ")    # Cherry Apple Pear
fruits.append("Melon")  # ["Cherry", "Apple", "Pear", "Melon"]
fruits.remove("Apple")  # ["Cherry", "Pear", "Melon"]
fruits.pop()    # # ["Cherry", "Pear"]
new_list.extend(fruits)   # 将 fruits 追加到  new_list 末尾
```

# 11. random模块 - 伪随机数
```python
import random
print(random.choice(fruits))
print(random.randint(0, 4))
```

# 12. 循环
```python
for item in list_of_items:
    # do some thing for each item

for i in range(0, 10):
    print(i)    # 0 ... 9

while True:
    do this

flag = 1
while flag:
    do this
    if condition:
        flag = 0
```

# 13. 函数
```python
def func():
    do this

def func():
    do this
    return True

def func(a):
    print(a)

def func(a, b, c=0):    # func(a=1, b=-2)
    if a + b < c:
        print(a + b)

def func(*args):
    print(args)

def func(**kargs):  # func({"name": bob, "age": 20})
    print(bob['age'])
```

# 14. 注释
```python
# 单行注释
"""
我是一个
多行注释
"""
```
