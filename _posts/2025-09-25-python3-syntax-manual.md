---
layout: post
title: Pythonh3 语法速查手册
feature-img: "assets/img/feature-img/python-banner.png"
thumbnail: "assets/img/thumbnails/feature-img/python-banner.png"
author: think-coding
categories: Syntax
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
l = [ i for i in items if i > 0 ]   # lambda 表达式直接赋值list
```

# 11. 字典
```python
new_dict = { key:value for item in list }
new_dict = { key:value for (key:value) in dict.items() if test }
```

# 12. random模块 - 伪随机数
```python
import random
print(random.choice(fruits))
print(random.randint(0, 4))
```

# 13. 循环
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

# 14. 函数
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

# 15. 注释
```python
# 单行注释
"""
我是一个
多行注释
"""
```

# 16. pandas
```python
import pandas
data_frame = pandas.DataFrame(dict)

for (key,value) in data_frame.items():
    print(key, value)
```

# 17. class
1. 定义类
```python
class Abc:
    def __init__(self, name): # 定义初始化属性
        self.name = "abc"
    pass
```

2. 继承
```python
class Animal(): # 基础类
    def __init__(self):
        self.num_eyes = 2

    def breath(self):
        print("Inhale, exhale.")

class Fish(Animal): # 子类
    def __init__(self):
        super().__init__()  # 继承父类的属性和初始化，避免被遗漏
    
    def swim(self):
        print("moving in water.")
```

# 18. turtle(画笔工具)
1. 常规使用方法
```python
from turtle import Turtle, Screen

tim = Turtle()    # 初始化画笔
tim.shape("turtle")   # 定义画笔形状
tim.color("coral")    # 定义画笔颜色
tim.forward(100)  # 前进100个像素
tom = Turtle("square")  # 初始化方形画笔

screen = Screen()    # 初始化画布
screen.setup(width=500, height=400) # 设置窗口大小
screen.bgcolor("black") # 设置背景色
print(screen.canvheight) # 输出画布高度
screen.exitonclick() # 点击后退出
```

2.  画虚线
```python
for _ in range(15):
    tim.forward(10)
    tim.penup()
    tim.forward(10)
    tim.pendown()
```

3. 画多边形
```python
def draw_shape(num_sides, length):
    angle = 360 / num_sides
    for _ in range(num_sides):
        tim.forward(length)
        tim.right(angle)
```

4. 随机漫步
```python
import turtle as t
import random

tim = t.Turtle()

def random_color():
    r = random.randint(0, 255)
    g = random.randint(0, 255)
    b = random.randint(0, 255)
    color = (r, g, b)
    return color

direction = [0, 90, 180, 270]
tim.pensize(15)
time.speed("fastest")

for _ in range(200):
    tim.color(random_color())
    tim.forward(30)
    tim.setheading(random.choice(direction))
```

5. 画点
```python
tim.dot(20, random.color())
```

6. 监听按键执行函数
```python
screen.listen()
screen.onkey(key="space", fun=move_forwards)
```

7. 输入框
```python
user_bet = screen.textinput(title="make your bet", prompt="Which turtle will win the race? Enter a color: ")
```

8. 动画效果(实时更新画笔位置)
```python
tim.update()
```

# 19. prettytable(美化表格)
```python
from prettytable import PrettyTable

table = PrettyTable()
table.add_column("name", ["Pikechu", "Squirtle", "Charmander"]) # 添加列和数据
table.add_column("type", ["Electric", "Water", "Fire"])

table.align = "l"   # 左对齐 c-居中 r-右对齐
print(table)
```

# 20. heroes
```python
import heroes
print(heroes.gen()) # 随机生成英雄名字
```

# 21. 虚拟环境
```python
python3 -m venv ~/venv
```

# 22. colorgram(提取图片的色彩RGB数据)
```python
import colorgram

rgb_colors = []
colors = = colorgram.extract('image.jpg', 30)   # 30种颜色
for color in colors:
    r = color.rgb.r
    g = color.rgb.g
    b = color.rgb.b
    new_color = (r, g, b)
    rgb_colors.append(new_color)

print(rgb_colors)
```

# 23. 