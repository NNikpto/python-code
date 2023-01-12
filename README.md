# python-code
python基础学习时的注意笔记
基础语法

1.注释

# 单行注释

'''
多行注释
'''
2.变量有没有类型?

没有，字符串变量表示变量存储了字符串而不是表示变量就是字符串。

3.类型转换

int(x)  # x转整数

float(x)  # x转浮点数

str(x) # x转字符串

4.标识符（python大小写敏感）

是用户在编程的时候所使用的一系列名字，用于给变量、类、方法等命名。

关键字不能做标识符：

False、True、None、and、as、assert、break、class、continue、def、del、elif、else、except、、finally、for、from、global、if、import、in、is、lambda、nonlocal、not、or、pass、raise、return、try、while、with、yield

5.运算符


6.字符串

定义

字符串格式化1（str1）
精度控制语法是：m.n的形式控制，如%5d、 %5.2f、%.2f，其中m和.n均可省略

字符串格式化2（如str2，注意那个f）
这种方式：不理会类型、不做精度控制。适合对精度没有要求的时候快速使用。

name = "张三"
age = 25
salary = 300000.0
str1 = "姓名:%s,年龄:%d,工资:%.2f" % (name, age, salary)
str2 = f"姓名:{name},年龄:{age},工资:{salary}"
print(str1 +'\n'+ str2)
结果

姓名:张三,年龄:25,工资:300000.00
姓名:张三,年龄:25,工资:300000.0
7.表达式

name = "张三"
age = 25
salary = 300000.0
aveSalary = salary/12
print(f"姓名:{name},年龄:{age},工资:{salary}")
print("%s的月工资:%.2f" % (name, aveSalary))
结果

姓名:张三,年龄:25,工资:300000.0

张三的月工资:25000.00

8.数据输入输出

input()，注意获取的是字符串；print()，输出。

name = input("name:")
age = input("age:")  # input获取的是字符串
age = int(age)  # 类型转换
salary = 300000.0
aveSalary = salary/12
print(f"姓名:{name},年龄:{age},工资:{salary}")
print("%s的月工资:%.2f" % (name, aveSalary))
结果

name:李四
age:28
姓名:李四,年龄:28,工资:300000.0
李四的月工资:25000.00
9.条件语句

if elif ... else

# 三次机会猜数字例子
import random
num = random.randint(1, 10)

for i in range(0, 3):
    inputNum = input("输入你猜的数字：")
    inputNum = int(inputNum)
    if inputNum == num:
        print("恭喜你，猜对了！")
        exit()
    elif inputNum > num:
        print(f"{inputNum}大了")
    else:
        print(f"{inputNum}小了")
print("很遗憾，没有机会了，答案是：", num)
10.循环语句

while循环语句，for循环语句。

两者能完成的功能基本差不多,但仍有一些区别:

while循环的循环条件是自定义的，自行控制循环条件；

for循环是一种”轮询”机制，是对一批内容（严格说是序列类型的内容：字符串、列表、元组等）进行逐个处理，只能被动取出数据处理。

'''
输出乘法表（while的例子）
'''

i = 1
while i <= 9:
    j = 1
    while j <= i:
        # \t:制表符；end=''的作用：输出不换行
        print(f"{j}*{i}={j*i}\t", end='')
        j += 1
    print()  # 输出一个换行
    i += 1
结果

1*1=1   
1*2=2  2*2=4  
1*3=3  2*3=6  3*3=9  
1*4=4  2*4=8  3*4=12 4*4=16 
1*5=5  2*5=10 3*5=15 4*5=20 5*5=25 
1*6=6  2*6=12 3*6=18 4*6=24 5*6=30 6*6=36 
1*7=7  2*7=14 3*7=21 4*7=28 5*7=35 6*7=42 7*7=49 
1*8=8  2*8=16 3*8=24 4*8=32 5*8=40 6*8=48 7*8=56 8*8=64 
1*9=9  2*9=18 3*9=27 4*9=36 5*9=45 6*9=54 7*9=63 8*9=72 9*9=81 
for的例子：数有几个a

注意：for a in name 中 变量a 是循环中的临时变量，作用域在循环内，如需访问在循环外定义此变量

name = "zhangsan is a boy"
count = 0
for a in name:
    if a == 'a': 
        count += 1
print(f"有{count}个a")
结果：有3个a

continue 和 break

continue关键字：中断本次循环，直接进入下一次循环

break：结束循环

11.函数

定义
def 函数名(传入参数):
    函数体
    return 返回值

# 注意：1. 先定义函数，后调用函数。
       2. 参数不需要，可以省略；
          返回值不需要，可以省略。
形参和实参

返回值

None返回值
None是类型'NoneType'的字面量，用于表示:空的、无意义的；
函数如何返回None：不使用return语句即返回None；主动return None
使用场景：函数返回值；if判断相当于False；变量定义
函数说明文档（多行注释解释函数）
def count_a(name):
    """
    :param name:待测字符串
    :return: 字符串中a的个数
    """

    count = 0
    for a in name:
        if a == 'a':
            count += 1
    return count

str = "ZhangSan is a boy"
num = count_a(str)
print(f"有{num}个a")
变量在函数的作用域

函数进阶一（第七章）
函数有4中常见参数使用方式:(参数还可以是一个函数)

1. 位置参数：

根据参数位置来传递参数

2. 关键字参数

通过“键=值”形式传递参数，可以不限参数顺序。可以和位置参数混用，位置参数需在前。

3. 缺省参数

不传递参数值时会使用默认的参数值

默认值的参数必须定义在最后

4. 不定长参数（可变参数）

位置不定长传递以*号标记一个形式参数，以元组的形式接受参数，一般命名为args。

关键字不定长传递以**号标记一个形式参数，以字典的形式接受参数，一般命名为kwargs。

"""
函数进阶之传参
"""
def getBeauty(name, residence, age=14):
    print(f"{name}住在大观园的{residence}，今年{age}岁，亭亭玉立。")
# 1. 按照位置一一传参
getBeauty('黛玉', '潇湘馆', 12)
# 2. 关键字参数
getBeauty(name='宝钗', age=13, residence='怡红院')
# 3. 缺省参数（函数定义时，参数有默认值，只能在最后）
getBeauty('探春', '秋爽斋')
# 4. 不定长参数

def test1(*args):
    print(args)

def test2(**kwargs):
    print(kwargs)

test1('黛玉', '潇湘馆', 12)
test2(name='宝钗', age=13, residence='怡红院')
结果:

黛玉住在大观园的潇湘馆，今年12岁，亭亭玉立。

宝钗住在大观园的怡红院，今年13岁，亭亭玉立。

探春住在大观园的秋爽斋，今年14岁，亭亭玉立。

('黛玉', '潇湘馆', 12)

{'name': '宝钗', 'age': 13, 'residence': '怡红院'}

函数进阶二（第七章第四节）---匿名函数

数据容器

1.概要

1.什么是数据容器?

一种可以存储多个元素的Python数据类型

2. Python有哪些数据容器?

list(列表)、tuple(元组)、 str(字符串)、 set(集合)、 dict(字典)。

它们各有特点，但都满足可容纳多个元素的特性。

2.list(列表)

1.定义

myList = ["贾宝玉", "林黛玉", "薛宝钗", 1, 2, 3]
print(myList)
myList[-1] = "王熙凤"
print(myList[-1])
print(myList[2])
# 遍历
# for name in myList:
#    print("姓名：", name)
结果

['贾宝玉', '林黛玉', '薛宝钗', 1, 2, 3]

王熙凤

薛宝钗


2.一些操作


3.tuple(元组)

1.定义：

a_tuple = ("贾宝玉", "林黛玉", "薛宝钗", 1, 2)

print(a_tuple)
结果

('贾宝玉', '林黛玉', '薛宝钗', 1, 2)

2.元组的特点：

可以容纳多个数据；
可以容纳不同类型的数据( 混装)
数据是有序存储的(下标索引)
允许重复数据存在
不可以修改(增加或删除元素等)
支持for循环
多数特性和list一致,不同点在于不可修改的特性。

3.常用方法

﻿
第一阶段-第六章-07-元组的定义和操作 P68 - 08:51
元组常用操作
﻿

4.string(字符串)

1.作为数据容器，字符串有如下特点:

只可以存储字符串
长度任意(取决于内存大小)
支持下标索引
允许重复字符串存在
不可以修改(增加或删除元素等)
支持for循环
2.常用方法


例子：strip()和split()演示

a = "  \n张三\n李四  \n"
b = a.strip()  # 删除字符串头尾的空格和换行,返回字符串，
# b:'张三\n李四', a还是a
c = a.split()  # 以空格和\n为分隔符，分割字符串,返回list
# c:['张三', '李四']
例子：分割字符串

my_str = "itheima itcast boxuegu"
numIT = my_str.count("it")  # 数字符串中"it"的数量
new_my_str = my_str.replace(" ", "|")  # 替换空格为|
str_list = new_my_str.split("|")  # 分割字符串

print(f"字符串{my_str}中有{numIT}个it字符")
print(f"字符串{my_str}中空格替换|后的新字符串：{new_my_str}")
print(f"新字符串{new_my_str}中按照|分割后的列表是：{str_list}")

"""
结果：
字符串itheima itcast boxuegu中有2个it字符
字符串itheima itcast boxuegu中空格替换|后的新字符串：itheima|itcast|boxuegu
新字符串itheima|itcast|boxuegu中按照|分割后的列表是：['itheima', 'itcast', 'boxuegu']
"""
5.序列

1.什么是序列?

内容连续、有序，支持下标索引的一类数据容器，（列表、元组、字符串）

2.序列如何做切片

heima = "你好好学习，你天天向上，加油！"
new_heima = heima[12:2:-1] # '加，上向天天你，习学'
序列[起始:结束:步长]

起始可以省略，省略从头开始
结束可以省略，省略到尾结束
步长可以省略，省略步长为1 (可以为负数，表示倒序执行)
"""
序列切片，得到”上向天天“
"""

heima = "你好好学习，你天天向上，加油！"
# 分割出 你天天向上
heima = heima.split("，")[1]  # 得到中间的字符串
# 倒序字符串
new_heima = heima[::-1]  # 倒叙切片：上向天天你
new_heima = new_heima.replace("你", "")  # 替换你为空：上向天天
print(new_heima)  # 输出 上向天天
6.集合（set）

1.集合有如下特点:

可以容纳多个数据
可以容纳不同类型的数据(混装)
数据是无序存储的(不支持下标索引)
不允许重复数据存在
可以修改(增加或删除元素等)
支持for循环，不支持while
2.定义

"""
集合练习：信息去重
"""

my_list = ["贾宝玉", "林黛玉", "王熙凤", "贾宝玉", "林黛玉", "王熙凤", "XiFeng", "DaiYu", "XiFeng", "DaiYu"]
my_set = set()
# my_set = {}  # 定义的是字典，不是集合
for beauty in my_list:
    my_set.add(beauty)
print(f"列表{my_list}存入集合后的结果{my_set}")

"""
结果
列表['贾宝玉', '林黛玉', '王熙凤', '贾宝玉', '林黛玉', '王熙凤', 'XiFeng', 'DaiYu', 'XiFeng', 'DaiYu']存入集合后的结果{'王熙凤', 'DaiYu', '贾宝玉', 'XiFeng', '林黛玉'}
"""
3.常用操作

﻿
第一阶段-第六章-12-集合的定义和操作 P73 - 22:34
字典常用操作
﻿

7.字典（dict）


常用操作


例子

"""
字典例子：涨工资，升职
"""
daGuanYuan = {'贾宝玉': {'住处': '怡红院', '月钱': 8000, '级别': 5},
              '林黛玉': {'住处': '潇湘馆', '月钱': 6000, '级别': 5},
              '薛宝钗': {'住处': '蘅芜院', '月钱': 5000, '级别': 4},
              '袭人': {'住处': '怡红院', '月钱': 900, '级别': 2},
              '晴雯': {'住处': '怡红院', '月钱': 900, '级别': 2}}
for beauty in daGuanYuan:
    # 找出大丫头们，给她们涨工资，升级
    if daGuanYuan[beauty]['级别'] == 2:
        daGuanYuan[beauty]['级别'] += 1
        daGuanYuan[beauty]['月钱'] += 1000

print(daGuanYuan)
8.总结


基于各类数据容器的特点，它们的应用场景如下:

列表: 一批数据，可修改、可重复的存储场景
元组: 一批数据，不可修改、可重复的存储场景
字符串:一串字符串的存储场景
集合:一批数据，去重存储场景
字典: 一批数据,可用Key检索Value的存储场景
通用操作


python文件操作

1.文件的编码

是一种规则集合，记录了内容与二进制间互换的逻辑，常用的时UTF-8.

2.文件操作

文件读取

﻿
第一阶段-第八章-02-文件的读取操作 P86 - 26:22
文件读取汇总
﻿

"""
open(file,mode,encoding)例子：数文件中某字符串个数
"""

# coding=utf-8

f = open("红楼梦.txt", 'r', encoding='UTF-8')

# hongLou = f.read()  # 读取文件全部信息,返回字符串
# count1 = hongLou.count("怡红院")
# print(f"方法一：文件《红楼梦.txt》中有{count1}个怡红院")

lines = f.readlines()  # 获取文件全部内容，返回list，每行是list的一个元素
count2 = 0
for line in lines:
    # print(line.strip())  # strip删除字符串中头尾的空格和换行
    names = line.split()  # 以空格和\n为分隔符，分割字符串,返回list
    for name in names:
        if name == "怡红院":
            count2 += 1

print(f"方法二：文件《红楼梦.txt》中有{count2}个怡红院")

f.close()
文件写入和追加
	1.写入文件使用open函数的"w"模式；

	追加写入文件使用open函数的"a"模式。

	2.写入和追加的方法一样，有:

write(), 写入内容
flush(), 刷新内容到硬盘中
	3.注意事项:

w/a模式，文件不存在，会创建新文件；
w模式，文件存在，会清空原有内容；a模式则会在原有内容后追加写入；
close()方法,带有flush()方法的功能
f1 = open("红楼梦1.txt", "w", encoding="UTF-8")  # utf8防乱码
f1.write("石头记")
f1.close()

f1 = open("红楼梦1.txt", "a", encoding="UTF-8")
f1.write("\n木石前盟")
f1.close()
文件：红楼梦1.txt

石头记
木石前盟
备份文件的例子

fileName = "金陵十二钗.txt"
# 备份文件名
new_fileName = "金陵十二钗.txt.bak"
# 读取文件
with open(fileName, 'r', encoding='utf-8') as f:
    jinChai = f.readlines()
out_file = open(new_fileName, 'w', encoding='utf-8')
# 写入备份文件
for line in jinChai:
    # 又副册的数据丢弃
    if line.split()[1] == "又副册":
        break
    out_file.write(line)

out_file.close()
文件：金陵十二钗.txt

林黛玉 正册
薛宝钗 正册
贾元春 正册
贾迎春 正册
贾探春 正册
贾惜春 正册
贾巧姐 正册
史湘云 正册
妙玉 正册
王熙凤 正册
李纨 正册
秦可卿 正册
香菱 副册
薛宝琴 副册
尤二姐 副册
尤三姐 副册
邢岫烟 副册
李纹 副册
李绮 副册
夏金桂 副册
秋桐 副册
小红 副册
龄官 副册
娇杏 副册
晴雯 又副册
袭人 又副册
平儿 又副册
鸳鸯 又副册
紫鹃 又副册
莺儿 又副册
玉钏 又副册
金钏 又副册
彩云 又副册
司棋 又副册
芳官 又副册
麝月 又副册
文件：金陵十二钗.txt.bak

林黛玉 正册
薛宝钗 正册
贾元春 正册
贾迎春 正册
贾探春 正册
贾惜春 正册
贾巧姐 正册
史湘云 正册
妙玉 正册
王熙凤 正册
李纨 正册
秦可卿 正册
香菱 副册
薛宝琴 副册
尤二姐 副册
尤三姐 副册
邢岫烟 副册
李纹 副册
李绮 副册
夏金桂 副册
秋桐 副册
小红 副册
龄官 副册
娇杏 副册
第九章--异常（bug）

1.异常及其捕获方式


"""
异常捕获
"""

file_name = "红楼梦1.txt"
# 打开一个不存在的文件
# 1. 出现异常，执行except中的语句,捕获所有异常
try:
    f = open(file_name, 'r', encoding='utf-8')
except Exception as e:
    # 如果出现异常，则执行以下语句，而不是停止程序
    print(e)
    f = open(file_name, 'w', encoding='utf-8')

# 2. 捕获指定异常
try:
    1/0
except ZeroDivisionError as e:
    print("除数不能是0")
    print(e)


# 3. 捕获指定多个异常
# else和finally可选
try:
    print(1/1)
except (ZeroDivisionError, NameError) as e:
    print("除数不能是0")
    print(e)
else:
    print("没有异常执行else语句内容")
finally:
    print("有没有异常都执行finally的内容")
    f.close()
异常捕获2,---异常的传递性

"""
异常捕获2,---异常的传递性
"""

def readTxt(file_name):
    f = open(file_name, 'r', encoding='utf-8')
    for name in f:
        print(name)

file_name = "红楼梦1.txt"
# 打开一个不存在的文件
try:
    readTxt(file_name)
except Exception as e:
    # 如果出现异常，则执行以下语句，而不是停止程序
    print(e)
2.python模块

1.什么是模块?

模块就是一个Python代码文件，内含类、函数、变量等，我们可以导入进行使用。

2.如何导入模块

[from 模块名] import [模块|类|变量| 函数|*] [as 别名]

3.注意事项:

from可以省略，直接import即可
as别名可以省略
通过”.”来确定层级关系
模块的导入一般写在代码文件的开头位置
4.自定义模块


__all__变量可以控制import * 时哪些功能可以被导入
用法：__all__ = ['fun1','fun2']
例子：__main__

"""
自定义模块 day4_bug.py
"""

def readTxt(file_name):
    f = open(file_name, 'r', encoding='utf-8')
    for name in f:
        print(name, end='')

# 没有main，在调用时执行了
file_name = "红楼梦.txt"
readTxt(file_name)


# __main__保证在该模块被引用的时候，不执行main中的部分。
# pycharm快捷键：输入 main 可直接跳出 if __name__ == '__main__':
if __name__ == '__main__':
    file_name = "红楼梦1.txt"
    readTxt(file_name)
引用该模块

"""
自定义模块的调用
"""

from day4_bug import readTxt
readTxt("../day03/红楼梦.txt")
运行结果：调用了文件中没有被__main__包围的内容，所以输出了红楼梦.txt的内容

红楼梦.txt文件的内容如下：
王熙凤
贾宝玉
贾琏
贾政
贾敏
../day03/红楼梦.txt文件的内容如下：
贾宝玉 住处 怡红院 月钱 8000
林黛玉 住处 潇湘馆 月钱 6000
薛宝钗 住处 蘅芜院 月钱 5000
袭人 住处 怡红院 月钱 900
晴雯 住处 怡红院 月钱 900
3.python包


例子


第10-12章--可视化图

1.json数据格式


2.PyEcharts包


在线文档：https://pyecharts.org/#/zh-cn/intro


例子


第二阶段第一章--面向对象

1.类的定义


2.面向对象编程

面向对象编程就是，使用对象进行编程。

即，设计类，基于类创建对象，并使用对象来完成具体的工作。

3.一些内置方法


4.私有成员、封装


5.继承--单继承、多继承


复写父类成员方法、属性

6.类型注解

在代码中写数据的类型


方法的注解


Union类型的联合类型注解


7.多态


例子数据分析案例


第二阶段第二章--SQL

1.SQL基础

1. SQL语言是什么？有什么作用？

SQL：结构化查询语言，用于操作数据库，通用于绝大多数的数据库软件

2. SQL的特征：

大小写不敏感
需以;号结尾
支持单行、多行注释
	单行注释： -- 注释内容（--后面一定要有一个空格）
	单行注释：# 注释内容（# 后面可以不加空格，推荐加上）
	多行注释：/* 注释内容 */
3. SQL语言的分类

数据定义：DDL（Data Definition Language）库的创建删除、表的创建删除等create、drop、show
数据操纵：DML（Data Manipulation Language）新增、修改、删除数据等
数据控制：DCL（Data Control Language）新增、删除用户、密码修改、权限管理等
数据查询：DQL（Data Query Language）基于需求查询和计算数据
2.DDL--库、表管理

第三阶段：大数据相关技术pySpark

1.简介

Spark是Apache基金会旗下的顶级开源项目，用于对海量数据进行大规模分布式计算。大数据开发中的核心技术。

PySpark是Spark的Python实现，是Spark为Python开发者提供的编程入口，用于以Python代码完成Spark任务的开发。

PySpark不仅可以作为Python第三方库使用，也可以将程序提交的Spark集群环境中，调度大规模集群进行执行。

2.安装

在”CMD”命令提示符程序内，输入：

pip install pyspark

或使用国内代理镜像网站（清华大学源）

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pyspark

3.PySpark的编程模型

PySpark的功能都是从SparkContext对象作为开始的。换句话说，SparkContext类对象，是PySpark编程中一切功能的入口。

获取对象的方法：

# 1. 导包
from pyspark import SparkConf, SparkContext
# 2. 创建SparkConf对象
my_conf = SparkConf().setMaster('local[*]').setAppName('test_spark_app')
# 3. 基于SparkConf对象创建SparkContext对象
sc = SparkContext(conf=my_conf)
# 4. 打印PySpark的运行版本
print(sc.version)
# 5. 停止PySpark程序
sc.stop()
PySpark的编程，主要分为如下三大步骤：

数据输入：通过SparkContext完成数据读取
数据计算：读取到的数据转换为RDD对象，调用RDD的成员方法完成计算
数据输出：调用RDD的数据输出相关成员方法，将结果输出到list、元组、字典、文本文件、数据库等

4.PySpark的编程模型1--数据输入

1. RDD对象是什么？为什么要使用它？

RDD对象称之为分布式弹性数据集，是PySpark中数据计算的载体，它可以：

提供数据存储
提供数据计算的各类方法，方法的返回值依旧是RDD
所以可以实现RDD迭代计算
2. 如何输入数据到Spark（即得到RDD对象）

支持两种数据类型：python数据容器、读取文件

通过SparkContext的parallelize成员方法，将Python数据容器转换为RDD对象
通过SparkContext的textFile成员方法，读取文本文件得到RDD对象
# 1. 导包
from pyspark import SparkConf, SparkContext
# 2. 创建SparkConf对象
my_conf = SparkConf().setMaster('local[*]').setAppName('test_spark_app')
# 3. 基于SparkConf对象创建SparkContext对象
sc = SparkContext(conf=my_conf)
# 4.1 Python数据容器（list、tuple、set、dict、str）转RDD对象
rdd1 = sc.parallelize([1,2,3,4])
rdd2 = sc.parallelize((1,2,3,4))
rdd3 = sc.parallelize({1,2,4,5})
rdd4 = sc.parallelize("zhangsan")

print(rdd1.collect())
print(rdd2.collect())
print(rdd3.collect())
print(rdd4.collect())

'''
输出结果
[1, 2, 3, 4]
[1, 2, 3, 4]
[1, 2, 4, 5]
['z', 'h', 'a', 'n', 'g', 's', 'a', 'n']
'''
# 4.2 读取文件转RDD对象
rdd_file = sc.textFile('../day04/红楼梦.txt')
print(rdd_file.collect())

'''
输出结果：
['贾宝玉 住处 怡红院 月钱 8000']
'''
# 5. 停止PySpark程序
sc.stop()
5.PySpark的编程模型2--数据计算

map算子（成员方法）：参数是一个函数（该函数可以用lambda写），通过这个函数定义的规则逐个处理RDD中的元素，返回一个新的RDD。
flatMap算子：参数也是一个函数，功能：先对RDD执行map操作，然后解除一层嵌套。
reduceByKey算子：参数也是一个函数（func:(V,V)->V，该函数要求两个类型相同的参数，一个与传入类型相同的返回值），功能：针对的是KV型RDD，自动按照key分组，然后根据func中的聚合逻辑，完成组内数据的聚合操作，返回聚合后的RDD。
filter算子：参数是一个函数（func:(T)->bool），功能：函数对RDD数据逐个处理，得到True的保留至返回值的RDD中。
distinct算子：无参，功能：RDD去重
sortBy算子：参数是一个函数（func:(T)->U，告知需要对那个数据进行排序即可）ascending 参数（True升序，False降序）, numPartitions参数（用多少分区排序），功能：按照func排序


# 注意会报错找不到python解释器路径，下两行给他指出python的路径

import os

os.environ['PYSPARK_PYTHON'] = 'D:/12824/anaconda3/python.exe'

# 1. 导包
from pyspark import SparkConf, SparkContext
# 注意会报错找不到python解释器路径，下两行给他指出了python的路径
import os
os.environ['PYSPARK_PYTHON'] = 'D:/12824/anaconda3/python.exe'


def map_func(data):
    return data * 10


# 2. 创建SparkConf对象
my_conf = SparkConf().setMaster('local[*]').setAppName('test_spark_app')
# 3. 基于SparkConf对象创建SparkContext对象
sc = SparkContext(conf=my_conf)
# 4.1 map算子（成员方法）
# 参数是一个函数，通过这个函数定义的规则逐个处理RDD中的元素，返回一个新的RDD。
rdd1 = sc.parallelize([1, 2, 3, 4])
new_rdd1 = rdd1.map(map_func)
print(new_rdd1.collect())  # [10, 20, 30, 40]
# 4.2 flatMap算子, 比map多了个解除嵌套操作。
lst2 = [[1, 2], [4, 6], [6, 3]]
rdd2 = sc.parallelize(lst2)
print(rdd2.flatMap(lambda a: a*2).collect())  # [1, 2, 1, 2, 4, 6, 4, 6, 6, 3, 6, 3]
# reduceByKey算子：参数也是一个函数（func:(V,V)->V，该函数要求两个类型相同的参数，一个与传入类型相同的返回值），功能：针对的是KV型RDD，自动按照key分组，然后根据func中的聚合逻辑，完成组内数据的聚合操作，返回聚合后的RDD。
rdd3 = [('小明', 50), ('小明', 40), ('小明', 50), ('林黛玉', 100), ('林黛玉', 100), ('林黛玉', 100)]
rdd_reduceByKey = sc.parallelize(rdd3).reduceByKey(lambda a, b: a+b)
print(rdd_reduceByKey.collect())  # [('林黛玉', 300), ('小明', 140)]
# 4. filter算子：参数是一个函数（func:(T)->bool），功能：函数对RDD数据逐个处理，得到True的保留至返回值的RDD中。
rdd4 = sc.parallelize([1, 2, 3, 4, 5])
rdd_filter = rdd4.filter(lambda num: num % 2 == 0)
print(rdd_filter.collect())  # [2, 4]
# 5. distinct算子：无参，功能：RDD去重
rdd5 = sc.parallelize([1, 2, 1, 2, 5])
rdd_distinct = rdd5.distinct()
print(rdd_distinct.collect())  # [1, 2, 5]
# sortBy算子：参数是一个函数（func:(T)->U，告知需要对那个数据进行排序即可）ascending 参数（True升序，False降序）, numPartitions参数（用多少分区排序），功能：按照func排序
rdd6 = sc.parallelize([('小明', 50), ('小明', 40), ('小明', 50), ('林黛玉', 100), ('林黛玉', 100), ('林黛玉', 100)])
rdd_sortBy = rdd6.sortBy(lambda a: a[1], ascending=False, numPartitions=1)  # 按照a的第二列排序，降序，全局排序
print(rdd_sortBy.collect())  # [ ('林黛玉', 100), ('林黛玉', 100), ('林黛玉', 100), ('小明', 50), ('小明', 50), ('小明', 40)]
# 5. 停止PySpark程序
sc.stop()
综合案例

"""
需求:复制以上内容到文件中，使用Spark读取文件进行计算:
1. 各个城市销售额排名,从大到小
2. 全部城市,有哪些商品类别在售卖
3. 北京市有哪些商品类别在售卖
"""
import json

from pyspark import SparkConf, SparkContext

my_conf = SparkConf().setMaster('local[*]').setAppName('my_second_app')
sc = SparkContext(conf=my_conf)

sellData = sc.textFile("销售文件.txt")
# 数据处理，数据每行不是一个数据
sellData = sellData.flatMap(lambda s: s.split('|'))
# json数据转字典
sellData = sellData.map(lambda s: json.loads(s))
# 1. 获得各个城市销售额排名
#  1.1. 取出城市和销售额数据
sellData_city = sellData.map(lambda s: (s['areaName'], int(s['money'])))
#  1.2， 求和
sellData_city = sellData_city.reduceByKey(lambda a, b: a+b)
#  1.3. 排序
sellData_city = sellData_city.sortBy(lambda s: s[1], False, 1)
print(sellData_city.collect())

# 2. 全部城市,有哪些商品类别在售卖
all_category = sellData.map(lambda s: s['category']).distinct()
print(all_category.collect())
# 3. 北京市有哪些商品类别在售卖
#   3.2 筛选出北京的数据，在取出类别，在去重
beijing_category = sellData.filter(lambda s: s[0] == "北京").map(lambda s: s['category']).distinct()
print(beijing_category.collect())
6.PySpark的编程模型3--数据输出

输出为python对象

输出到文件(要下载hadoop包，配置它)

.......
rdd1 = sc.parallelize([1, 2, 3, 4])
new_rdd1 = rdd1.map(map_func)
print(new_rdd1.take(2), new_rdd1.count())  # [10, 20] 4
print(new_rdd1.collect())  # [10, 20, 30, 40]
......
rdd1 = sc.parallelize([1, 2, 3, 4], numSlices=1)
rdd1.saveAsTextFile("rdd.txt")







pycharm小技巧：

1、显示方法参数
bar = Bar()  # 光标在引用成员的括号处时，按alt+p显示方法的参数
2、多行一起编辑
self.date = date
self.order_id = order_id
self.money = money
self.province = province
# 按住alt点每一行，可以一起输入self.
3、shift+alt+上\下 : 向上\下移动当前代码行 作者：路过海面滑翔的风 https://www.bilibili.com/read/cv19862434?spm_id_from=333.999.0.0 出处：bilibili
