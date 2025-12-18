## Python判断语句

- 布尔类型（bool），表达现实生活中的逻辑，即真和假，字面量True， False，布尔类型不仅可以自行定义同时也可以通过计算得来。

> 变量名称 = 布尔类型字面量

- 比较运算符

![1763046916185](image/Note/1763046916185.png)

- 布尔表达式练习

![1763047150997](image/Note/1763047150997.png)

- if语句

  ```python
  if 要判断的条件: #注意冒号
      条件成立时要做的事
  ```
- if-else语句

  ```python
  if 要判断的条件: 
      条件成立时要做的事
  else:
      条件不成立要做的事
  ```
- if-elif-else语句

  ```python
  if 条件1: 
      条件1成立时要做的事
  elif 条件2:
      条件2成立时要做的事
  ...
  else:
      条件不成立要做的事
  ```

判断是互斥并且有顺序的，else省略不写时等同3个独立if判断

- 判断语句的嵌套
  - 解决满足前置条件后进行二次判断的多层判断需求，通过缩进决定语句的层次关系

```python
if 条件1:
    满足条件1 do sth
    if 条件2:
	满足条件2 do sth 
```

## Python循环语句

- while循环

  ```python
  while 条件:
      条件满足 do sth
  ```
- while循环的嵌套

  ```python-repl
  while 条件1:
      条件1满足 do sth
      ...
      while 条件2:
  	条件2满足 do sth

  ```
- 九九乘法表

  ```python
  # 初始化行和列的变量
  i = 1
  j = 1

  # 外层循环控制行数
  while i < 10:
  # 内层循环控制列数
      while j < (i + 1):
          # 打印乘法表的一项，并用制表符隔开
          print(f"{j}*{i}={j*i}\t", end="")
          j += 1
      # 换行
      print()
      # 行数加1
      i += 1
      # 重置列数
      j = 1
  ```
- 注意判断条件书写避免出现死循环
- for循环

  - while循环的循环条件是自定义的，自行控制循环条件
    for循环是一种”轮询”机制，是对一批内容进行”逐个处理"
  - 与while循环不同，for循环是无法定义循环条件的，所以理论上将Python的for循环无法构建无限循环（被处理的数据集不可能无限大）

  ```python
  for 临时变量 in 待处理的数据集(序列):
      循环满足条件时执行的代码
  ```
- for遍历字符串

```python
name = "lishuaishuai"
for x in name:
    print(x)
```

- range语句

  - for语法中的待处理数据集，严格来说，称之为: **序列类型**
  - **序列类型**其内容可以一个个依次取出的一种类型，包括:字符串，列表，元组
  - range语句获得一个简单的数字序列，配合for循环使用
    ```python
    range(num1, num2, step) #类比字符串切片，左闭右开区间，参数可省略
    ```
- for循环的变量作用域

  - 如果在for循环外部访问临时变量:实际上是可以访问到的在编程规范(软要求)上，是不允许、不建议这么做的

```python
for i in range(5):
    print(i) # 临时变量，在编程规范上，作用范围(作用域)，只限定在for循环内部
print(i) #规范上不允许，实际上可以
```

```python
i = 0 #正确做法，提前定义，符合规范
for i in range(5):
    print(i)
print(i)
```

- for循环的嵌套

  ```python
  for 临时变量 in待处理数据集(序列):
      循环满足条件应做的事情1
      循环满足条件应做的事情2
      循环满足条件应做的事情N
      for 临时变量 in 待处理数据集(序列):
  	循环满足条件应做的事情1
  	循环满足条件应做的事情2
  	循环满足条件应做的事情N
  ```
- 打印九九乘法表

  ```python
  for i in range(1, 10)
      for j in range(1, i+1):
  	print(f"{j} * {i} = {j * i}\t", end='')
      print()
  ```
- 循环中断break和continue

  - Python提供continue和break关键字
    用以对循环进行**临时跳过**和**直接结束**
  - continue关键字用于:中断本次循环，直接进入下一次循环
  - continue可以用于:for循环和while循环，效果一致
  - 在嵌套循环中，continue关键字只可以控制它所在的循环临时中断
  - ```python
    for i in range(1, 100):
        语句1
        continue
        语句2
    ```

```python
for i in range(1, 100):
    语句1
    for j in range(1, 100):
        语句2
	continue
	语句3
    语句4
```

- break
  > break关键字同样只可以控制:它所在的循环结束
  >

```python
for i in range(1, 100):
    语句1
    for j in range(1, 100):
        语句2
	continue
	语句3
    语句4
```

## Python函数

- 函数:是组织好的，可重复使用的，用来实现特定功能的代码段。函数目的，为了得到一个针对特定需求、可供重复利用的代码段提高程序的**复用性**，减少重复性代码,提高开发效率

```python
str1 = "python"
str2 = "phenomenon"
str3 = "culture"
def my_len(data):
    count = 0
    for i in data:
	count += 1
    print(f"字符串{data}的长度是{count}")
my_len(str1)
my_len(str2)
my_len(str3)
```

- 定义和调用语法

  ```python
  # 函数定义，先定义后使用
  def 函数名([传入参数]):
      # 传入参数和返回值可省略
      函数体
      [return 返回值]
  # 函数调用
  函数名(参数)
  ```
- 函数的参数

  - 传入参数：在函数进行计算的时候，接受外部(调用时)提供的数据。
    - 函数定义中运算的参数称为，形式参数(形参)，参数之间使用逗号进行分隔
    - 函数调用中传入的参数称之为:实际参数(实参)，表示函数执行时真正使用的参数值，传入的时候，按照顺序传入数据，使用逗号分隔
    - 传入参数的数量是不受限制的，可以不使用参数，也可以仅使用任意N个参数

```python
def add(x, y):
    result = x + y
    print(f"{x} + {y} 的结果是 {result}")

add(5, 6)
```

- 函数返回值

  - 就是程序中函数完成事情后，最后给调用者的结果
  - 函数体在遇到return后就结束了，所以写在return后的代码不会执行。
    ```python
    def add(x, y):
        result = x + y
        return result

    r = add(5, 6)
    ```
  - None类型
    - 如果函数没有使用return语句返回数据，那么函数有返回值吗?实际上是有的
      ```python
      def say_hello():
          print("Hello...")
      # 使用变量接收say_he11o函数的返回值
      result=say_hell0()
      # 打印返回值
      print(result)
      #结果None
      # 打印返回值类型
      print(type(resu1t))
      #结果<class'NoneType'>
      ```
    - Python中有一个特殊的字面量:None，其类型是<class'NoneType'>无返回值的函数，实际上就是返回了None这个字面量
    - None可以主动使用return返回，效果等同于不写return语句:
    - None作为一个特殊的字面量，用于表示:空、无意义
      - 函数无返回值
      - if判断中，None等同于False
        ```python
        def check_age(age):
            if age > 18:
            return "sUcCEss"
        return None
        result = check_age(5)
        if not result:
            print("未成年，不可进入")
        ```
      - 一般用于在函数中主动返回None，配合if判断做相关处理
      - 定义变量，但暂时不需要变量有具体值，可以用None来代替
- 函数说明文档(Pycharm)

  ```python
  def func(x，y):
  """
  函数说明
  :param x: 形参x的说明
  :param y: 形参y的说明
  :return: 返回值的说明
  """
  函数体
  return 返回值
  ```

  给函数添加说明文档，辅助理解函数的作用，通过多行注释的形式，对函数进行说明解释
- 函数嵌套调用

  所谓函数嵌套调用指的是一个函数里面又调用了另外一个函数

  如果函数A中，调用了另外一个函数B，那么先把函数B中的任务都执行完毕之后才会回到上次函数A执行的位置

  ```python
  def func_b():
      print("---2---")
  def func_a():
      print("---1---")
      func_b()
      print("---3---")
  # 调用函数func_a
  func _a()
  ```
- 变量作用域

  主要分为两类:局部变量和全局变量

  - 局部变量，是定义在函数体内部的变量，即只在函数体内部生效，在函数体内部临时保存变量，函数执行完成，变量就被销毁
  - 全局变量，指的是在函数体内、外都能生效的变量
- global关键字，使用 global关键子可以在的数内部声明变量为全局变量

  ```python-repl
  num = 100

  def testA():
      print(num)

  def testB():
      #global 关键字声明a是全局变量
      global num
      num = 200
      print(num)


  testA()
  testB()
  print(f"全局变量num:{num}")
  ```

## Python数据容器

- 数据容器

  一种可以容纳多份数据的数据类型，容纳的每一份数据称为元素。每一个元素，可以是**任意类型**的数据，如字符串、数字、布尔等

  ![1763115556999](image/Note/1763115556999.png)
- 五类数据容器：列表(list)、元组(tuple)、字符串(str)、集合(set)、字典(dict)
- 列表(list)

  - 定义

    ```python
    # 字面量
    [元素1，元素2，元素3，元素4，...]
    # 定义变量
    变量名称 =[元素1，元素2，元素3，元素4，
    ...
    # 定义空列表
    变量名称 =[]
    变量名称 = 1ist()
    ```
  - 以[]作为标识, 列表内每一个元素之间用，逗号隔开
  - 注意:列表可以一次存储多个数据，且可为不同的数据类型，支持嵌套

    ```python
    my_list = [[1, 2, 3], [4, 5, 6]]
    print(my_list)
    ```
  - 列表的下标索引
    从前向后的方向，编号从0开始递增
    从后向前的方向，编号从-1开始递减

    ![1763116195765](image/Note/1763116195765.png)

    ```
    #语法:列表[下标索引]
    name_list =['Tom','Lily','Rose']
    print(name_list[0])#结果:Tom
    print(name_1ist[1])#结果:Li1y
    print(name_list[2])#结果:Rose
    ```
  - 嵌套列表的下标索引

    ![1763116381115](image/Note/1763116381115.png)

    ```python
    my_list = [[1, 2, 3], [4, 5, 6]]
    print(my_list[1][2])
    ```
  - 列表的常用操作(列表的方法)
    在Python中，如果将函数定义为class(类)的成员，那么函数会称之为:方法

    ```python
    def add(x, y):
        #函数
        return x + y

    class Student:
        #方法
        def add(self, x, y):
            return x + y
    # 方法和函数功能一样，有传入参数，有返回值，只是方法的使用格式不同
    num = add(1, 2)
    stu = Student()
    num = stu.add(1, 2)
    ```

    - 查找元素下标

      - 功能:查找指定元素在列表的下标，如果找不到，报错ValueError

        ```python
        列表.index(元素)
        ```

        index就是列表对象(变量)内置的方法(函数)
    - 插入元素

      ```python
      列表.insert(下标,元素)
      # 在指定的下标位置，插入指定的元素
      my_1ist=[1，2，3]
      my_list.insert(1,"python")
      print(my_list)
      #结果:[1，"python"，3，4]
      ```
    - 追加元素

      ```python
      列表.append(元素)
      # 将指定元素，追加到列表的尾部
      my_1ist =[1，2，3]
      my_1ist.append(4)
      print(my_1ist)
      # 结果:[1，2，3，4]
      my_list=[1，2，3]
      my_1ist.append([4，5，6])
      print(my_list)
      #结果:[1, 2, 3, 4, 5, 6]
      ```

      ```python
      列表.extend(其它数据容器)
      # 将其它数据容器的内容取出，依次追加到列表尾部
      my_1ist=[1，2，3]
      my_1ist.extend([4，5，6])
      print(my_1ist)#结果:[1，2，3，4，5，6]
      ```
    - 删除元素

      - 下标删除

      ```python
      del 列表[下标]
      列表.pop(下标)
      my_1ist=[1，2，3]
      # 方式1
      de1 my_1ist[0]
      print(my_1ist) # 结果:[2，3]
      # 方式2
      my_1ist.pop(0)
      print(mylist)# 结果:[2，3]
      ```

      - 内容删除

      ```python
      列表.remove(元素)
      # 删除某元素在列表中的第一个匹配项
      my_1ist=[1, 2, 3, 2, 3]
      my_list.remove(2)
      print(my_1ist) #结果:[1, 3, 2, 3]
      ```

      - 清空列表

        ```
        列表.clear()
        my_1ist=[1，2，3]
        my_1ist.clear()
        print(my_1ist) # 结果:[]

        ```
    - 统计元素个数

      ```python
      列表.count(元素)
      my_1ist =[1，1，1，2，3]
      print(my_1ist.count(1)) #结果:3
      ```
    - 统计列表中全部的元素数量

      ```
      len(列表)
      ```

    ![1763117993841](image/Note/1763117993841.png)
  - ...需要的时候，随时查阅资料即可。

    列表特点：可以容纳多个元素（上限2^63-1个元素），可以容纳不同类型的元素(混装)，数据是有序存储的(有下标序号)，允许重复数据存在，可以修改(增加或删除元素等)
- 列表的遍历 - while循环

  ```python
  index = 0
  while index < len(列表):
      元素=列表[index]
      对元素进行处理
      index += 1
  ```
- 列表的遍历 - for循环

  ```python
  fon 临时变量 in 数据容器:
      对临时变量进行处理
  ```
- 元组（tuple）

  - 元组定义

    - 注意:元组只有一个数据，这个数据后面要添加逗号,不写逗号非元组类型

      ```python
      # 定义元组字面量
      (元素，元素，.....元素)
      # 定义元组变量
      变量名称=(元素，元素，.....,元素)
      # 定义空元组
      变量名称=()
      变量名称=tuple()
      ```
    - 元组也支持嵌套
  - 元组相关操作

    ![1763119602973](image/Note/1763119602973.png)

    ```python
    # 根据下标(索引)取出数据
    t1=(1，2，'he11o’)
    print(t1[2])# 结果:’he11o’
    # 根据index()，查找特定元素的第一个匹配项
    t1=(1，2，'he11o’，3，4，'he11o')
    print(tl.index('he11o’))#结果: 2

    #统计某个数据在元组内出现的次数
    t1=(1，2,'he11o’，3，4，'he11o')
    print(t1.count('he11o’))#结果:2

    # 统计元组内的元素个数
    t1=(1，2，3)
    print(len(t1)) # 结果 3
    ```
  - 不可以修改元组的内容，否则会直接报错;
  - 可以修改元组内的1ist的内容(修改元素、增加、删除、反转等)
  - tuple多数特性和list一致，不同点在于不可修改的特性。
- 字符串（str）

  - 不可否认的是，字符串同样也是数据容器的一员。同元组一样，字符串是一个**无法修改**的数据容器。（Read only）
    因此：修改指定下标的字符，移除特定下标的字符，追加字符等无法完成。必须要做只能得到一个新字符串

    常用助记：
    字符串索引，查找索引，统计字符，字符串长度（读字符串）

    字符串替换，字符串规整(得到新字符串， 去除的是在规整字符串里的字符)

    字符串拆分（得到列表）

    ![1763119932811](image/Note/1763119932811.png)
  - 123python321.strip("123")
- 数据容器的切片操作

  序列：内容连续、有序，可使用下标索引的一类数据容器列表、元组、字符串，均可以可以视为序列。

  - 切片：序列可以切片，从一个序列中，取出一个子序列
    - 语法: 序列[起始下标:结束下标:步长]
      - 起始下标，从何处开始，留空从头开始
      - 结束下标（不含），表示何处结束，留空截取到结尾
      - 步长，依次取元素的间隔

        - 1，一个个取
        - 2，跳过一个取
        - N，跳过N-1个元素取
        - 负数表示反向取（此时起始下标/结束下标也要反向标记，倒过来）
      - 切片操作不会影响序列本身（元组，字符串read only）

        ```python
        my_tuple = (0 ,1, 2, 3, 4, 5, 6)
        r1 = my_tuple[1:4]
        r2 = my_tuple[:]
        r3 = my_tuple[::2]
        r4 = my_tuple[3:1:-1]

        ```
- 集合

  - 对内容做去重处理，列表，元组，字符串不方便
  - 集合，内容无序，元素无重复
  - 定义

    ```python
    #定义集合字面量
    {元素,元素, 元素, ......}
    # 定义集合变量
    变量名称={元素，元素，...元素}
    # 定义空集合
    变量名称 = set()
    ```
  - 由于无序，不支持下标访问，但支持修改，集合不是序列
  - 集合修改操作

    - 添加新元素
      - 语法:集合.add(元素)
    - 移除元素
      - 语法:集合.remove(元素)
    - 随机取出一个元素
      - 语法:集合.pop()
    - 清空集合
      - 语法:集合.clear()
    - 取两个集合的差集
      - 语法:集合1.difference(集合2)
      - 功能：取出集合1和集合2的差集(1里有2里没有)
      - 结果：得到一个新集合，集合1和集合2不变

        ```python
        set1={1，2，3
        set2={1，5，6}
        set3=setl.difference(set2)
        print(set3) # 结果:{2，3}
        print(set1) #结果:{1，2，3}不变
        print(set2) # 结果:{1，5，6}不变
        ```
    - 消除2个集合的差集
      - 语法:集合1.difference_update(集合2)
      - 功能:对比集合1和集合2，在集合1内，删除和集合2相同的元素
      - 结果：集合1被修改，集合2不变

        ```python
        set1={1，2，3}
        set2={1，5，6}
        set1.difference_update(set2)
        print(set1)
        print(set2)
        结果:{2，3}
        结果:{1，5，6}
        ```
    - 2个集合合并
      - 语法:集合1.union(集合2)
      - 功能：将集合1和集合2组合成新集合
      - 结果：得到新集合，集合1和集合2不变

        ```python
        set1={1，2，3}
        set2 ={1，5，6}
        set3=setl.union(set2)
        print(set3)
        print(set1)
        print(set2)
        结果:{1，2，3，5，6}，新集合
        结果:{1，2，3}，set1不变
        结果:{1，5，6}，set2不变
        ```
      - 统计集合元素数量 len()函数
      - 集合的遍历，不支持下标索引，不能用while循环，使用for循环
  - ![1763133618523](image/Note/1763133618523.png)
- 字典/映射(dict)

  - 字典的定义

    - 字典的定义{}，存储的元素是键值对

      ```python
      # 定义字典字面量
      {key: value, key: value,...,key:value}
      # 定义字典变量
      my_dict ={key:value,key:value,...,key:value}
      # 定义空字典
      my_dict ={}
      my_dict = dict()
      ```
    - 字典的key是不可以重复的，key相同只会保留一个（最后），覆盖
    - 字典数据的获取
  - - 字典同集合一样，不可以使用下标索引，但是字典可以通过key值来获取对应的value
    - 语法:字典[key]

      ```python
      stu_score ={"王力鸿":99，"周杰轮":88，"林俊节”:77]
      print(stu_score["王力鸿”])
      print(stu_score["周杰轮"])
      print(stu_score["林俊节”])
      ```
    - 定义嵌套字典

      - 字典的Key和Value可以是任意数据类型(Key不可为字典)，表明字典是可以嵌套的
      - ![1763134234552](image/Note/1763134234552.png)

        ```python
        stu_score_dict={"王力鸿":{"语文":77,"数学":66,"英语":33},"周杰轮":{"语文":88,"数学":86,"英语":55},"林俊节":{"语文":99,"数学":96,"英语":66}}
        ```
  - 字典常用操作

    - 新增元素

      - 语法:字典[key]=value
      - 结果:字典被修改，新增了元素

        ```python
        stu_score={
        "王力鸿":77,
        "周杰轮":88,
        "林俊节":99
        }
        #新增，张学油的考试成情
        stu_score['张学油"]=66
        print(stu_score)
        ["王力鸿":77，"周杰轮":88, "林俊节”:99, "张学油”:66]
        ```
    - 更新元素

      - 语法:字典[key]=value
      - 结果，字典被修改，元素被更新

        ```python
        stu_score={
        "王力鸿":77,
        "周杰轮":88,
        "林俊节":99
        }
        #新增，张学油的考试成情
        stu_score['王力鸿"]=100
        print(stu_score)
        ["王力鸿":100，"周杰轮":88, "林俊节”:99]
        ```
    - 删除元素

      - 语法: 字典.pop(key)
      - 结果:获得指定Key的Value，同时字典被修改，指定Key的数据被删除
    - 清空元素

      - 语法:字典.clear()
      - 结果:字典被修改，元素被清空
    - 获取全部的key

      - 语法:字典.keys()
      - 结果:得到字典中的全部Key
    - 遍历字典

      ```python
      keys = my_dict.keys()
      for key in keys:
          print(f"字典key是{}")
          print(f"字典的value是{my_dict[key]}")
      ```

      ```python
      for key in my_dict:
          print(f"字典key是{key}")
          print(f"字典的value是{my_dict[key]}")
      ```

      字典不支持索引，不能使用while循环
    - 统计字典内的元素个数 语法:len(字典)
    - ![1763135450556](image/Note/1763135450556.png)
- 容器类型总结

  - 容器分类

  ![1763135508561](image/Note/1763135508561.png)

  - 容器特点对比

    ![1763135589356](image/Note/1763135589356.png)
  - 应用场景

    ![1763135634026](image/Note/1763135634026.png)
- 字符串通用操作

  - 遍历，5类数据容器都支持for循环遍历，列表，元组，字符串支持while循环，字典，集合不支持
  - 数据容器的通用统计功能
    - 统计容器的元素个数len(容器)
    - 统计容器的最大元素max(容器)
    - 统计容器的最小元素min(容器)
  - 容器通用转换功能
    - 给定容器转列表list(容器)
    - 给定容器转字符串str(容器)
    - 给定容器转元组tuple(容器)
    - 给定容器转集合set(容器)
  - 容器通用排序功能
    - sorted(容器， [reverse=True]), 将给定容器进行排序

  ---

  ## Python 函数进阶
- 函数多返回值

  - 如果一个函数要有多个返回值
  - 语法

    ```python-repl
    def 函数名([参数]):
        return 返回值1, 返回值2
    变量1, 变量2 =  函数名([参数])
    ```
  - 注意：按照返回值的顺序，写对应顺序的多个变量接收即可，变量之间用逗号隔开，支持不同类型的数据return
  - 示例

    ```python
    def test_return()
        return 1, 2, 3
    x, y , z = return()
    ```
- 函数多种传参方式

  - 位置参数

    - 调用函数时根据函数定义的参数位置来传递参数
    - 语法：

      ```python
      def 函数名(形参列表):
          函数体
      函数名(位置参数列表)
      # 位置参数：根据函数定义时的参数位置传递的参数
      ```
    - 示例:

      ```
      def user_info(name, age, gender):
          print(f'姓名{name}, 年龄{age}, 性别{gender}')
      user_info('Tom', 20, 男)
      ```
    - 注意:传递的参数和定义的参数的顺序及个数必须一致
  - 关键字参数

    - 函数调用时通过“键=值”形式传递参数.
    - 作用：可以让函数更加清晰、容易使用，同时也清除了参数的顺序需求
    - 示例：

      ```python
      def user_info(name, age, gender):
          print(f'姓名{name}, 年龄{age}, 性别{gender}')

      # 关键字传参
      user_info(name = '小明', age = 20, gender = '男')
      # 可以不按照固定顺序
      user_info(age = 20, gender = '男', name = '小明')
      # 可以和位置参数混用,注意位置参数必须在前，且匹配参数顺序
      user_info('小明', age = 20, gender = '男')
      ```
    - 注意：函数调用时，如果有位置参数时，位置参数必须在关键字参数的前面，关键字参数之间不存在先后顺序
    - 语法:

      ```python
      def 函数名(形参列表):
          函数体
      函数名([位置参数列表],关键字参数列表)
      # 关键字参数:通过"键=值"方式传参
      ```
  - 缺省参数

    - 缺省参数也叫默认参数，用于定义函数，为参数提供默认值，调用函数时可不传该默认参数的值.
    - 作用:当调用函数时没有传递参数，就会使用默认是用缺省参数对应的值.
    - 示例:

      ```python
      def user_info(name, age, gender='男'):
          print(f'姓名{name}, 年龄{age}, 性别{gender}')

      user_info('TOM', 20)
      user_info('ROSE', 18, '女')
      ```
    - 默认的参数必须**写到形参列表最后面**
    - 注意: 所有位置参数必须出现在默认参数前，包括函数定义和调用
  - 不定长参数

    不定长参数也叫可变参数.用于不确定调用的时候会传递多少个参数(不传参也可以)的场景.

    - 作用：当调用函数时不确定参数个数时，可以使用不定长参数
    - 分类：位置传递的不定长参数，关键字传递的不定长参数
    - 位置传递的不定长参数

      - 示例:

        ```python
        def user_info(*args):
            print(args)
        # ('TOM', )
        user_info('TOM')
        # ('TOM', 18)
        user_info('TOM', 18)
        ```
      - 注意: 传进的所有参数都会被args变量收集，它会根据传进参数的位置合并为一个元组(tuple)，args是元组类型，这就是位置传递的不定长参数
    - 关键字传递的不定长参数

      - 示例：

        ```python
        def user_info(**kwargs):
            print(kwargs)

        # {'name': 'TOM', 'age': 18, 'id': 110}
        user_info(name='TOM', age=18, id=110)


        ```

        参数一定是“键=值”形式，所有的“键=值”都会被kwargs接受，同时会根据“键=值”组成字典.
      - args,kwargs只是定义不定长参数的默认惯例，并不是强制性的，没有特殊需求，一般都这么写，这两种参数都是数量不受限，形式受限
- 匿名函数

  - 函数作为参数传递

    在前面的函数学习中，我们一直使用的函数，都是接受数据（数字，字符串，字典、列表、元组等）作为参数传入，其实，我们学习的函数本身，也可以作为参数传入另一个函数内。

    - 示例:

      ```python
      # 函数体中待计算的数据是确定的，但是计算数据的逻辑（怎样计算）是不确定的
      # 普通函数是数据的传入，这种写法是逻辑的传入
      def test_func(compute):
          result = compute(1, 2) # 函数的调用
          print(result)


      def compute(x, y):
          return x + y

      test_func(compute) # 结果：3
      ```

      代码解析：

      在此代码中，函数compute，作为参数，传入了test_func函数中进行使用

      - test_func需要一个函数作为参数传入，这个函数需要接收2个数字进行计算，计算逻辑由这个被传入函数决定
      - compute函数接收2个数字对其进行计算，compute函数作为参数，传递给了test_func函数使用
      - 最终，在test_func函数内部，由传入的compute函数，完成了对数字的计算操作
    - 这是**计算逻辑的传递**，而非数据的传递，如上述代码所示，不仅仅是简单的加减乘除，**任何逻辑**都可以自行定义并作为函数传入
    - 传入类型是 `<class 'function'>`
  - lambda匿名函数

    - 掌握使用lambda关键字定义匿名函数的语法
    - 函数的定义

      - def关键字，可以定义带有名称的函数，有名称的函数，可以基于名称**重复使用**。
      - lambda关键字，可以定义匿名函数(无名称)，无名称的匿名函数，只可**临时使用一次**。
    - 匿名函数定义语法:

      ```python
      lambda 传入参数: 函数体(一行代码)
      # lambda 是关键字，表示定义匿名函数,
      # 传入参数表示匿名函数的形式参数。如: x, y表示接收2个形式参数
      # 函数体，就是函数的执行逻辑上，注意：只能写一行，无法写多行代码
      # 注意没有函数名
      ```
    - lambda匿名函数示例（与上面代码等价）

      ```python
      def test_func(compute):
          result = compute(1, 2)
          print(result)

      test_func(lambda x, y: x + y) #结果：3
      # 定义lambda匿名函数作为传入参数
      ```

      使用def和使用lambda，定义的函数功能完全一致，只是lambda关键字定义的函数是匿名的，无法二次使用
    - 只要你的代码可以一行搞定，建议使用lambda匿名函数（实际上还是很常用的）

  ## Python 文件操作
- 文件编码
  [UTF-8介绍](https://zhuanlan.zhihu.com/p/137875615)

  - 编码技术：即翻译的规则，记录了如何将内容翻译成二进制，以及如何将二进制翻译回可识别内容。

    - ASCII码(American Standard Code for Information Interchange)美国信息互换标准代码,基于拉丁字母的字符编码，共收录了 128 个字符（最高位0），用一个字节就可以存储，它等同于国际标准 ISO/IEC 646。(单字节编码,字符数等于它占用的字节数)

      ![img](https://file+.vscode-resource.vscode-cdn.net/e%3A/Python%20Project/Python%20Hard%20Way/image/Note/1763045917202.png)
    - 从左到右转换就是解码 （decode），从右到左就是编码 （encode）。
    - 多字节编码

      如果想匹配多于256个字符的语言，一个字节显然不够，用两个字节的话，16比特，可以编码65536个字符，[BIG-5](https://zhida.zhihu.com/search?content_id=118770755&content_type=Article&match_order=1&q=BIG-5&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NjM5NDk1MTgsInEiOiJCSUctNSIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjExODc3MDc1NSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.V5jfRBvRL34XWXfbSZUF1mQAFeZgBcXdk85gYGObs9U&zhida_source=entity)就是一个双字节编码方式，它包括大多数中文繁体字，[GB18030](https://link.zhihu.com/?target=http%3A//en.wikipedia.org/wiki/GB18030) 则包括繁体和简体。每种语言可能都有他们的编码体系，用着不同的字节，对于人和机器来说，这样都很容易混乱。
    - 统一编码Unicode
      [Unicode和UTF-8](https://www.bilibili.com/video/BV14Ns8eEERu/?spm_id_from=333.337.search-card.all.click&vd_source=eb6308b852b20e70ebbcf364f69b1de8)

      对于一些语言单字节编码不够，所以采用双字节，双字节也不够的时候可以采用三字节，甚至四字节，字节是不是越多越好呢？并不是，因为字节用的越多，那些用单字节就能表示的字符会增加很多个0， 浪费很多容量。

      - Unicode其实不是一种编码， 而是定义了一个表， 表中为世界上每种语言中的每个字符设定了统一并且唯一的码位 （code point），以满足跨语言、跨平台进行文本转换的要求。在表示一个Unicode的字符时，通常会用“U+”然后紧接着一组十六进制的数字来表示这一个字符。
      - Unicode 有多套编码规则UTF-8, UTF-16, UTF-32
        - UTF-8:一种变长的编码规则，对英文跟ASCII一样单字节，非英文，使用2-4个字节表示

          ![1763777625045](https://file+.vscode-resource.vscode-cdn.net/e%3A/Python%20Project/Python%20Hard%20Way/image/Note/1763777625045.png)
        - 乱码：

          ![1763777671217](https://file+.vscode-resource.vscode-cdn.net/e%3A/Python%20Project/Python%20Hard%20Way/image/Note/1763777671217.png)
  - UTF-8是目前全球通用的编码格式，除非有特殊需求，否则一律UTF-8

    ![1763778026789](image/Note/1763778026789.png)
- 文件的读取
  文件操作步骤 打开文件-》读写文件 -》关闭文件
  可以只打开和关闭文件的，不进行任何读写操作

  - open()打开函数：可以打开一个已经存在的文件，或者创建一个新文件
  - 语法：

    ```python-repl
    open(name, mode,encoding)
    # name:是要打开的目标文件名的字符串(可以包含文件所在的具体路径)。
    # mode:设置打开文件的模式(访问模式):只读、写入、追加等。
    # encoding:编码格式(推荐使用UTF-8)
    ```

    示例:

    ```python
    f = open('python.txt', 'r', encoding = 'UTF-8')
    # 注意encoding 参数的位置并不是第三位，所以使用关键字参数直接指定，不能使用位置参数
    ```

    注意：此时的 f 是 open 函数的文件对象，对象是Python中一种特殊的数据类型，拥有属性和方法，可以使用对象,属性或对象,方法对其进行访问，后续面向对象课程会给大家进行详细的介绍。类型是 `<class '_io.TextIOWrapper'>`
    mode常用的三种基础访问模式

    ![1763778694282](image/Note/1763778694282.png)
  - read()方法

    ```python
    文件对象.read(num)
    # num表示要从文件中读取的数据的长度(单位是字节)，如果没有传入num，那么就表示读取文件中所有的数据。
    ```
  - readlines()方法:
    readlines可以按照行的方式把整个文件中的内容进行一次性读取，并且返回的是一个列表(list)，其中每一行的数据为一个元素。

    ```python
    f = open('python.txt')
    content = f.readlines()
    # ['hello world\n', 'abcdefg\n', 'aaa\n', 'bbb\n', 'ccc']
    print(content)

    # 关闭文件
    f.close()
    ```
  - readline()方法：一次读取一行

    ```python
    f= open('python.txt')
    content = f.readline()
    print(f'第一行:{content}’)
    content = f.readline()
    print(f'第二行:{content}')
    # 关闭文件
    f.close()
    ```

    文件读取的时候是有一个小指针的，指示当前已经读取到哪个地方了，文件对象open()之后，在close()之前每次调用方法，会续接上一次读取的位置
  - for循环读取文件行

    ```python
    for line in open("python.txt", "r"):
        print(line)
    #每一个line临时变量，就记录了文件的一行数据
    ```
  - close()关闭文件对象

    ```python
    f = open("python.txt","r")
    f.close()
    # 最后通过close，关闭文件对象，也就是关闭对文件的占用
    # 如果不调用close,同时程序没有停止运行，那么这个文件将一直被Python程序占用
    ```
  - with open 语法

    ```python
    with open("python.txt", "r") as f:
         f.readlines()
    # 通过在with open的语句块中对文件进行操作
    # 可以在操作完成后自动关闭close文件，避免遗忘掉close方法
    ```
  - 操作汇总

    ![1763779702414](image/Note/1763779702414.png)
- 文件的写入

  ![1763780250226](image/Note/1763780250226.png)

  ```python
  文件对象.write(内容)
  # 文件对象以w mode打开
  ```

  示例：

  ```python
  #1.打开文件
  f = open('python.txt', 'w')
  #2.文件写入内存
  f.write('hello world')
  #3.内容刷新，内存中积攒的内容写入外存
  f.flush()
  # close关闭，会自动flush,带有flush方法的功能
  f.close()
  ```

  - 注意:

    - 直接调用write，内容并未真正写入文件，而是会积攒在程序的内存中，称之为缓冲区
    - 当调用flush的时候，内容会真正写入文件
    - 这样做是避免频繁的操作硬盘，导致效率下降(攒一堆，一次性写磁盘)
  - w mode 打开文件的特点：文件不存在的时候会创建文件，文件存在会把内容清空，然后写入
- 文件的追加
  示例:

  ```python
  #1.打开文件
  f = open('python.txt', 'a')

  #2.文件写入内存
  f.write('hello world')
  #3.内容刷新，内存中积攒的内容写入外存
  f.flush()
  # close关闭，会自动flush,带有flush方法的功能
  f.close()
  ```

  a mode，文件不存在会创建文件,文件存在会在最后，追加写入文件

  ---

  ## Python 异常，模块与包
- 异常：运行过程中的错误，当检测到一个错误时，Python解释器就无法继续执行了，反而出现了一些错误的提示，这就是所谓的“异常”，也就是BUG

  - BUG名称的由来：早期计算机采用大量继电器工作，马克二型计算机就是这样的。1945年9月9日，下午三点，马克二型计算机无法正常工作了，技术人员试了很多办法，最后定位到第70号继电器出错。负责人哈珀观察这个出错的继电器，发现一只飞蛾躺在中间，已经被继电器打死。她小心地用摄子将蛾子夹出来，用透明胶布帖到“事件记录本”中，并注明“第一个发现虫子的实例。”自此之后，引发软件失效的缺陷，便被称为Bug。
  - 以'r'方式打开一个不存在的文件 FileNotFoundError
- 捕获异常

  异常出现后一般有两种情况

  - 整个程序因为一个BUG停止运行
  - 对BUG进行提醒，整个程序继续运行（需要对异常进行捕获）
  - 捕获异常的作用：提前假设某处会出现异常，做好提前准备，当真的出现异常的时候，可以有后续手段。
- 捕获常规异常

  - 基本语法：

    ```python
    try:
        可能发生错误的代码
    except:
        如果出现异常执行的代码
    ```
  - 示例：

    ```python
    try:
        f = open('linux.txt', 'r')
    except:
        print("出现异常了，因为文件不存在，将open的模式改为w")
        f = open('linux.txt', 'w')
    ```
- 捕获指定异常

  - 基本语法：

  ```python
  try:
      print(name)
  except NameError as e: # e 错误信息
      print('name变量名称未定义错误')
  ```

  - 如果尝试执行的代码的异常类型和要捕获的异常类型不一致，则无法捕获异常。
  - 一般try下方只放一行尝试执行的代码。
- 捕获多个异常
- 当捕获多个异常时，可以把要捕获的异常类型的名字放到except 后，并使用元组的方式进行书写。

  ```python
  try:
      print(1/0)
  except (NameError, ZeroDivisionError) as e:
      print('除0错误或变量未定义错误')
  ```

  捕获全部异常的另一种写法

  ```python
  try:
      print(1/0)
  except Exception as e:
      print('出现异常了')
  ```
- 异常else

  else表示的是如果没有异常要执行的代码,else是可选的

  ```python
  try:
      print(1)
  except Exception as e:
      print(e)
  else:
      print("没有异常的时候执行的代码')
  ```
- 异常的finally

  - finally表示的是无论是否异常都要执行的代码，例如关闭文件。

    ```python
    try:
        f= open('test.txt', 'r')
    except Exception as e:
        f= open('test.txt', 'w')
    else:
        print('没有异常")
    finally:
        f.close()
    ```
- 异常的传递

  异常是具有传递性的

  当函数func01中发生异常，并且没有捕获处理这个异常的时候，异常会传递到函数func02，当func02也没有捕获处理这个异常的时候main函数会捕获这个异常，这就是异常的传递性

  ![1763787987521](image/Note/1763787987521.png)

  当所有函数都没有捕获异常的时候，程序就会报错
- Python 模块

  - Python 模块(Module)，是一个 Python 文件，以.py 结尾。模块能定义函数，类和变量，模块里也能包含可执行的代码。
  - 模块的作用: python中有很多各种不同的模块，每一个模块都可以帮助我们快速的实现一些功能，比如实现和时间相关的功能就可以使用time模块我们可以认为一个模块就是一个工具包，每一个工具包中都有各种不同的工具供我们使用进而实现各种不同的功能.
  - 模块的导入方式

    ```python
    [from 模块名] import[模块 | 类 | 变量 | 函数 | *][as 别名]
    ```
  - 常用导入方式：

    - import 模块名
    - from 模块名 import 类、变量、方法等
    - from 模块名 import *
    - import 模块名 as 别名
    - from 模块名 import 功能名 as 别名
  - import 模块名

    - 基本语法

      ```python
      import 模块名
      import 模块名1, 模块名2
      模块名.功能名()
      ```
    - 案例：导入time模块

      ```python
      # 导入时间模块
      import time

      print("开始")
      #让程序睡眠1秒(阻塞)
      time.sleep(1)
      print("结束")
      ```
  - from 模块名import 功能名

    - 基本语法:

      ```python
      from 模块名 import 功能名
      功能名()
      ```
    - 案例:导入time模块中的sleep方法

      ```python
      #导入时间模块中的sleep方法
      from time import sleep
      print("开始”)
      #让程序睡眠1秒(阻塞)
      sleep(1)
      print("结束”)
      ```
    - from 模块名 import *

      - 基本语法:

        ```python
        from 模块名 import *
        功能名()
        ```
      - 案例:导入time模块中所有的方法

        ```python

        # 导入时间模块中所有的方法

        from time import *
        print("开始”)
        #让程序睡眠1秒(阻塞)
        sleep(1)
        print("结束")
        ```
    - as定义别名

      基本语法

      ```python
      # 模块定义别名
      import 模块名 as 别名
      # 功能定义别名
      from 模块名 import 功能 as 别名
      ```

      案例

      ```python
      # 模块别名
      import time as tt
      tt.sleep(2)
      print('hello')
      ```

      ```python
      #功能别名
      from time import sleep as sl
      sl(2)
      print('hello')
      ```
  - 自定义模块

    Python中已经实现了很多的模块，不过有时候需要一些个性化的模块，可以通过自定义模块实现，也就是自己制作一个模块

    - 只需要新建python文件然后自定义函数
    - 模块名即文件名，自定义模块名要符合标识符命名规则
    - 当导入多个模块且模块内有同名功能的时候，当调用这个同名功能的时候，调用到的是后面导入的 模块的功能
    - 在实际开发中，当开发人员编写完模块后，为了让模块能够在项目中达到想要的效果，这个开发人员会自行在py文件中添加测试信息
    - 为了不执行测试调用需要使用到__main__变量

      ```python
      def test(a, b):
          print(a + b)

      if __name__ == '__main__':
          test(1, 2)
      ```

      当在另一个文件中导入该模块时，`__name`__就不是 `__main__`判断不成立，不执行后面测试代码
    - `__all__` 如果一个模块文件中有 `__all__` 变量， 当使用 `from xxx import *` 导入时，只能导入这个列表中的元素,是一个列表

      ```python
      __all__ = ['test_A']

      def test_a():
          print('testA')

      def test_B():
          print('testB)
      ```

      ```python
      from xxx import *

      # 只能使用test_A
      ```
  - Python包

    如果Python模块太多了，就可能导致一定的混乱，该如何管理这些模块？-- 通过Python包的功能

    - 从物理上看，包就是一个文件夹，在该文件夹下包含了一个 ` __init__`.py 文件，该文件夹可用于包含多个模块文件
    - 从逻辑上看，包的本质依然是模块

      ![1763790011719](image/Note/1763790011719.png)
    - 作用：当我们的模块文件越来越多时,包可以帮而我们管理这些模块，包的作用就是包含多个模块，但包的本质依然是模块
    - 文件夹+`__init__`.py文件 = 包
    - 在包里写文件
    - 导入包
      方式一

      ```python
      import 包名.模块名
      包名.模块名.目标
      ```

      方式二
      注意:必须在 `_init_.py`文件中添加 `_all_=[]`，控制允许导入的模块列表

      ```
      from 包名 import *
      模块名.目标
      ```
  - 安装第三方包

    - 我们知道，包可以包含一堆的Python模块，而每个模块又内含许多的功能所以，我们可以认为:一个包，就是一堆同类型功能的集合体。
    - 在Python程序的生态中，有许多非常多的第三方包(非Python官方)，可以极大的帮助我们提高开发效率，如:科学计算中常用的:numpy包,数据分析中常用的:pandas包,大数据计算中常用的:pyspark、apache-flink包,图形可视化常用的:matplotlib、pyecharts,人工智能常用的:tensorflow.
    - 内置工具pip

      ```python-repl
      pip install 包名称
      pip install -i https://pypi.tuna.tsinghua.edu.cn/simple 包名称
      ```

## Python面向对象编程

### 定义类

方法：当一个函数被定义在类中，这个函数被定义为方法

方法的命名：一般使用大驼峰命名法

`__init__`方法：初始化方法，给当前正在创建的实例对象添加属性

`__init__`参数: 当前正在创建的实例对象(self),其他自定义参数

`__init__`方法调用时机：当编写代码调用Person实例的时候，Python自动调用__init__

```python
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender
```

### 创建实例

如果直接打印实例，看不到实例属性

```python
print(p1)
print(p2)
# <__main__.Person object at 0x000002A8FCF6BB30>
# <__main__.Person object at 0x000002A8FCF99C70>
```

通过成员语法可以访问或修改实例身上的属性

```python
print(p1.name)
print(p1.age)
print(p1.gender)
print('-' * 20)
print(p2.name)
print(p2.age)
print(p2.gender)
print('-' * 20)
p1.name = '阿三'
print(p1.name)
```

```plaintext
张三
18
男
--------------------
李四
22
女
--------------------
阿三
```

通过 实例.__dict__ 可以查看实例身上的所有属性

```python
print(p1.__dict__)
print(p2.__dict__)
# {'name': '张三', 'age': 18, 'gender': '男'}
# {'name': '李四', 'age': 22, 'gender': '女'}
```

实例创建完成后，依然可以通过实例.属性名 = 值 去给实例追加属性

```python
p1.address = 'sdfmu'
print(p1.__dict__)
# {'name': '张三', 'age': 18, 'gender': '男', 'address': 'sdfmu'}
```

通过type函数，可以查看某个实例对象，是由哪个类创建出来的

```python
print(type(p1))
print(type(p2))
# <class '__main__.Person'>
# <class '__main__.Person'>
```

### 自定义方法

自定义方法的作用：给实例添加行为

自定义方法的参数：调用自定义方法的实例对象(self),其他参数

**自定义方法只有一份，保存在类身上，所有Person类的实例方法，都可以调用speak方法**

```python
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender
    def speak(self, msg):
        print(f'我叫{self.name}, 年龄是{self.age}, 性别是{self.gender}, 我想说{msg}')
```

### 实例属性

通过【实例.属性名 = 值】给实例添加的属性，就叫做，实例属性

**实例属性只能通过实例访问，不能通过类方法**

每个实例都有自己独一份的实例属性，各个实例之间是互不干扰的

```python
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender
```

### 类属性

类属性的定义：跟类方法缩进相同的属性，**类属性是保存在类身上的**

**类属性可以通过类访问，也可以通过实例访问**

类属性的作用：类属性通常用于保存公共数据，使用公共数据对实例属性进行合法性检查

**注意，进行实例.属性名 = 值操作时，只会对实例自身的属性起作用，不会影响类属性**

```python
class Person:
    max_age = 120
    planet = '地球'
    def __init__(self, name, age, gender):
        # 给实例添加属性
        self.name = name
        self.gender = gender
        if age <= Person.max_age:
            self.age = age
        else:
            print(f'年龄超出范围，已将年龄设置为最大值{Person.max_age}')
            self.age = Person.max_age

p1.planet = '火星'
print(Person.__dict__)
print(p1.__dict__)
print(p2.__dict__)
print(p1.planet)
print(p2.planet)
'''
{'__module__': '__main__', 'max_age': 120, 'planet': '地球', '__init__': <function Person.__init__ at 0x00000231261AF740>, '__dict__': <attribute '__dict__' of 'Person' objects>, '__weakref__': <attribute '__weakref__' of 'Person' objects>, '__doc__': None}
{'name': '张三', 'gender': '男', 'age': 18, 'planet': '火星'}
{'name': '李四', 'gender': '女', 'age': 22}
火星
地球
'''
```

### 实例方法

主要供实例调用的自定义方法，给实例添加行为的方法叫做实例方法

**实例方法保存在类身上**

**注：通过类取调用实例方法,能调用，但是不推荐**

```python
class Person:
    # 初始化方法（给实例添加属性）
    def __init__(self, name, age, gender):
        # 给实例添加属性
        self.name = name
        self.age = age
        self.gender = gender

    # 下面的speak方法，run方法，都保存在类身上，但他们主要时供实例调用，所以他们都叫实例方法
    def speak(self, msg):
        print(f'我叫{self.name}, 年龄是{self.age}, 性别是{self.gender}, 我想说{msg}')

    # 自定义方法(给实例添加行为)
    def run(self, distance):
        print(f'{self.name}疯狂的奔跑了{distance}米')
```

### 类方法

使用**@classmethod**装饰器 装饰过的方法，叫做类方法，类方法保存在类上

类方法有一个参数叫做cls，表示当前类本身，因为该参数，所以类方法可以访问类属性

类方法的作用：**用于实现与类相关的逻辑，比如操作类级别的信息，一些工厂方法(创建实例的类方法) 设计模式**

**类方法，也能通过实例调用到，但是非常不推荐**

```python
class Person:
    # 类属性
    max_age = 120
    planet = '地球'
    # 初始化方法（给实例添加属性）
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

    def speak(self, msg):
        print(f'我叫{self.name}, 年龄是{self.age}, 性别是{self.gender}, 我想说{msg}')

    def run(self, distance):
        print(f'{self.name}疯狂的奔跑了{distance}米')

    # 操作类级别的信息
    @classmethod
    def change_planet(cls, value):
        cls.planet = value

    #create工厂方法
    @classmethod
    def create(cls, info_str):
        # 从info_str中获取到有效信息
        name, year, gender = info_str.split('-')
        current_year = datetime.now().year
        age = current_year - int(year)
        # 创建并返回一个实例对象
        return cls(name, age, gender)
```

### 静态方法

使用@staticmethod 装饰的方法叫做静态方法，**静态方法也是保存在类里的，静态方法需要通过类调用**

静态方法只是单纯的定义在类中，它不会收到self,cls参数，它收到的参数都是自定义参数

由于静态方法没有收到：self,cls参数，所以其内部不会访问类和实例相关的内容

静态方法的作用：静态方法通常用于定义，**与类相关的工具方法**

**注意：通过实例也能调用到静态方法，但是不推荐**

```python
from datetime import datetime
class Person:
    # 初始化方法（给实例添加属性）
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

    # 该方法用于判断人是否成年 
    @staticmethod
    def is_adult(year):
        # 获取当前的年份
        current_year = datetime.now().year
        # 计算年龄
        age = current_year - year
        # 返回结果
        return age >= 18

    # 该方法用于遮盖身份证号
    @staticmethod
    def mask_idcard(idcard):
        return idcard[:6] + '********' +idcard[-4:]
```

### 继承

类继承语法，将继承的类放到类名后的括号里

子类中调用父类的方法，查找方法的顺序 **实例 =》创造该实例的类 =》该类的父类**

在子类中，有两种方式去调用父类的初始化方法，来实现对继承属性的初始化操作

方式1,使用super()方法调用父类的 `__init__`方法

方式2,使用类名调用父类的 `__init__`方法

子类独有的属性，需要自己手动完成初始化

```python
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

    def speak(self, msg):
        print(f'我叫{self.name}, 年龄是{self.age}, 性别是{self.gender}, 我想说{msg}')

# 定义一个Student类(子类，派生类)，继承自Person类(父类，超类，派生类)
class Student(Person):
    def __init__(self, name, age, gender, stu_id, grade):
        # 方式1
        super().__init__(name, age, gender)
        # 方式2
        # Person.__init__(self, name, age, gender)
        # 子类独有的属性，需要自己手动完成初始化
        self.stu_id = stu_id
        self.grade = grade

    def study(self):
        print(f'我叫{self.name}, 我在努力学习，争取做到{self.grade}年级的前十名')
```

### 重写

指在子类中定义了一个**与父类中相同的方法**，那么子类中的方法就会**覆盖父类的方法**

```python
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

    def speak(self, msg):
        print(f'我叫{self.name}, 年龄是{self.age}, 性别是{self.gender}, 我想说{msg}')

# 定义一个Student类，继承自Person类
class Student(Person):
    def __init__(self, name, age, gender, stu_id, grade):
        super().__init__(name, age, gender)
        self.stu_id = stu_id
        self.grade = grade

    def speak(self, msg):
        super().speak(msg)
        print(f'我是学生, 我的学号是{self.stu_id}, 我正在读{self.grade}, 我想说：{msg}')

s1 = Student('李华', 12, '男', '2025001', '初二')
s1.speak('好好学习')
```

### 两个常用方法（内置方法）

方法1：isinstance(instance, Class), 作用：判断某个对象是否为指定类或其子类的实例

方法2：issubclass(Class1, Class2), 作用：判断某个类是否是另一个类的子类

```python
# 两个常用方法
# 定义一个Person类
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

    def speak(self, msg):
        print(f'我叫{self.name}, 年龄是{self.age}, 性别是{self.gender}, 我想说{msg}')

# 定义一个Student类，继承自Person类
class Student(Person):
    def __init__(self, name, age, gender, stu_id, grade):
        super().__init__(name, age, gender)
        self.stu_id = stu_id
        self.grade = grade


p1 = Person('张三', 18, '男')
s1 = Student('李华', 12, '男', '2025001', '初二')
print(isinstance(s1, Student))
print(isinstance(p1, Person))
print(isinstance(s1, Person))
print(isinstance(p1, Student))
print('-' * 20)
print(issubclass(Student, Person))
print(issubclass(Person, Student))
'''
True
True
True
False
--------------------
True
False
'''
```

### 多重继承

概念:多重继承指一个类同时继承多个父类，从而拥有多个父类的属性和方法。

```python
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

    def speak(self):
        print(f'我叫{self.name}, 年龄是{self.age}, 性别是{self.gender}')

class Worker:
    def __init__(self, company):
        self.company = company
  
    def do_work(self):
        print(f'我在{self.company}做兼职')

class Student(Person, Worker):
    def __init__(self, name, age, gender, company, stu_id, grade):
        Person.__init__(self, name, age, gender)
        Worker.__init__(self, company)
        self.stu_id = stu_id
        self.grade = grade

    def study(self):
        print(f'我在努力的学习,争取做{self.grade}年级的前十名')


s1 = Student('张三', 18, '男' , '麦当劳', '2025001' ,'初二')
print(s1.__dict__)
s1.speak()
s1.do_work()
s1.study()
```

类的__mro__属性：用于记录属性和方法的查找顺序（Method Resolution Order）,object内置类是所有类的父类

通过实例去查找属性或方法时，会先在实例自身查找，如果没有该方法，就按照__mro__记录的顺序去进行查找, **方法查找顺序由继承顺序决定**

### 三种访问权限

public 公有属性：作用域：**当前类中，子类中，类外部**，都可以访问 (最常用，不用任何修改)

protected 保护属性：作用域：**当前类中，子类中**，都可以访问，类外部不可以访问，（_开头的实例属性）

在类外强制访问【受保护的属性】也能够访问到，但是十分不推荐

private 私有属性，作用域：**只能在当前类中访问**，（__开头的实例属性），类外强制访问【私有属性】，报错 底层通过重命名的方式将属性隐藏

```python
class Person:
    def __init__(self, name, age, idcard):
        self.name = name 
        self._age = age  
        self.__idcard = idcard 

    def speak(self):
        print(f'我叫:{self.name}, 年龄:{self._age}, 身份证:{self.__idcard}')

class Student(Person):
    def hello(self):
        print(f'我是学生({self.name}-{self._age}-{self.__idcard})')
```

# getter与setter方法

使用@property装饰器注册私有或者保护属性的getter方法，当使用成员变量语法访问该私有或保护属性时，getter方法被自动调用

使用@变量名.setter装饰器注册私有或保护属性的setter方法，当使用赋值语法修改该私有或保护语法时，setter方法被自动调用

```python
class Person:
    def __init__(self, name, age, idcard):
        self.name = name 
        self._age = age  
        self.__idcard = idcard

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value <= 120:
            self._age = value
        else:
            print('年龄非法，修改失败')
   
    @property
    def idcard(self):
        return self.__idcard[:6] + '********' + self.__idcard[-4:]
  

    @idcard.setter
    def idcard(self, value):
        print('抱歉身份证号码不允许修改，若修改请联系管理员')
p1 = Person('张三', 18, '110101199001011234')
print(p1.name)
print(p1.age)
p1.age = 99
print(p1.age)
p1.age = 121
print(p1.idcard)
p1.idcard = '123456789012345678'
```

### 魔法方法（魔术方法）

概念：以__xxx__命名的特殊方法(双下划线开头和结尾)

特点:不需要我们手动调用，我们只要准备好这些方法，Python会在特定场景下，去自动调用。

```python
class Person:
    def __init__(self, name, age, idcard):
        self.name = name 
        self.age = age  
        self.gender = gender

    # 当执行print(Person的实例对象) 或str(Person的实例对象)时调用
    def __str__(self):
        return f'{self.name} - {self.age} - {self.gender}'
  
    # 执行len(Person的实例对象)的时候调用
    def __len__(self):
        return len(p1.__dict__)
  
    # 执行Person实例对象1 < Person实例对象2 调用
    def __lt__(self, other):
        return self.age < other.age
  
    # 执行Person实例对象1 > Person实例对象2 调用
    def __gt__(self, other):
        return self.age > other.age
  
    # 执行Person实例对象1 == Person实例对象2 调用
    def __eq__(self, other):
        return self.__dict__ == self.__dict__
  
    # 访问不存在的属性 调用
    def __getattr__(self, item):
        return f'您访问的{item}属性不存在'
  
p1 = Person('张三', 18, '男')
```

### object 类

Python 中，所有的类都继承了object 类，即:object类是所有类的顶层父类。

因为 object 是所有类的父类，所以 Python 中的所有对象，都间接是 object 类的实例。

所有对象都继承了object类所提供的各种属性和方法，从而保证每个对象都具有统一的基本能力

### 多态

概念:同一个方法名，在不同的对象上调用时，能呈现出不同的行为。

Python中支持的多态类型：标准多态、鸭子多态

类型注解语法 变量名:类型名

#### 标准多态

```python
class Animal:
    def speak(self):
        print('动物正在发出声音')

class Dog(Animal):
    def speak(self):
        print('汪汪汪')

class Cat(Animal):
    def speak(self):
        print('喵喵喵')

class Pig:
    def speak(self):
        print('哼哼哼')
# 继承关系，方法重写，类型注解写父类的类型 => 标准多态
def make_sound(animal:Animal): # 类型注解
    # 多态的体现
    animal.speak()

# 创建实例对象
a1 = Animal()
d1 = Dog()
c1 = Cat()
p1 = Pig()

make_sound(a1)
make_sound(d1)
make_sound(c1)
```

#### 鸭子多态

核心理念:如果一个东西看起来像鸭子，叫起来也像鸭子，那它就是鸭子。

鸭子类型是一种编程风格，它不检査对象的类型，只关注对象能否“做某件事”(是否有对应的方法)

```python
class Dog:
    def speak(self):
        print('汪汪汪')

class Cat:
    def speak(self):
        print('喵喵喵')

class Pig:
    def speak(self):
        print('哼哼哼')

class Fish:
    def speak(self):
        print('咕噜噜')

def make_sound(animal):
    animal.speak()


d1 = Dog()
c1 = Cat()
p1 = Pig()
f1 = Fish()

make_sound(d1)
make_sound(c1)
make_sound(p1)
make_sound(f1)
```

### 抽象类

一种不能直接实例化的类，它通常作为“规范”，让子类去继承，并实现其中定义的【抽象方法】

某个类一旦继承了ABC类，那么MustRun类

```python
from abc import ABC, abstractmethod

class MustRun(ABC):
    @abstractmethod
    def run(self):
        pass


class Person(MustRun):
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender
    def run(self):
        print(f'我叫{self.name},我在run')


p1 = Person('张三', 18, '男')
p1.run()
# 抽象类不能直接实例化

```

## Python 高阶技巧

### 闭包

案例：实现atm机功能

```python
account_amount = 0 # 账户余额
def atm(num, deposit=True):
    global account_amount
    if deposit:
    	account_amount += num
    	print(f"存款:+{num}，账户余额:{account_amount}")
    else:
    	account_amount -= numprint(f"取款:-{num}，账户余额:{account_amount}")
atm(300)
atm(300)
atm(100, False)
```

![1765069652274](image/Note/1765069652274.png)

通过全局变量account_amount来记录账户余额，在功能实现方面没问题，但是存在**全局变量被修改的风险**

#### 简单闭包语法

```python
def outer(logo):
	def inner(msg):
		print(f"<{logo}>{msg}<logo>")
	return inner
return inner
fn1 = outer("h1")
fn1("大家好啊, 我是标题1")

fn1 = outer("a")
fn1("大家好啊, 我是超链接")
```

![1765068688490](image/Note/1765068688490.png)

分析：调用outer返回的是inner函数对象fn1,这个fn1可以接收参数msg,但是fn1的参数logo已经固定为h1了

闭包：让内部函数依赖一个外部变量

能否让内部函数inner修改外部变量logo的值呢？

### nonlocal装饰器

需要使用nonlocal关键字修饰外部函数的变量才可在内部函数中修改外部函数的变量值

```python
def outer(num1):

    def inner(num2):
        nonlocal num1
        num1 += num2
        print(num1)
    return inner

fn = outer(10)
fn(10)
fn(10)
fn(10)
```

使用闭包实现atm案例

```python
def account_create(initial_amount = 0):
  
    def atm(num, deposit=True):
        nonlocal initial_amount
        if deposit:
            initial_amount += num
            print(f'存钱：{num}, 当前账户余额{initial_amount}')
        else:
            initial_amount -= num
            print(f'取钱：{num}, 当前账户余额{initial_amount}')
    return atm

atm = account_create()
atm(300)
atm(300)
atm(100, False)
```

    闭包使得无需定义全局变量即可实现通过函数，持续的访问、修改某个值闭包使用的变量的所用于在函数内**，作用域封闭**，**难以被错误的调用修改。**但由于内部函数持续引用外部函数的值,所以会导致这一部分内存空间不被释放,一直占用内存（缺点）

## 装饰器

装饰器其实也是一种闭包，其功能就是在**不破坏目标函数原有的代码和功能的前提下,为目标函数增加新功能**。

需求：在sleep函数前面增加我要睡觉了，在函数后面增加我睡着了（使用装饰器实现）

```python
def sleep():
    import random
    import time
    print("睡眠中...")
    time.sleep(random.randint(1,5))

sleep()
```

### 装饰器的闭包写法(一般写法)

思路：定义一个闭包函数，在闭包函数内部，完成执行目标函数，并完成功能的添加。

```python
def outer(func):
    def inner():
        print("我要睡觉了...")
        func()
        print("我睡醒了...")
    return inner

def sleep():
    import random
    import time
    print("睡眠中...")
    time.sleep(random.randint(1,5))

fn = outer(sleep)
fn()
```

调用方式比较麻烦且不够由于优雅

### 装饰器的语法糖写法(快捷写法)

使用@outer,定义在目标函数sleep()上，这种写法本质上**就是把sleep作为参数传递给outer函数**

调用sleep本质上还是调用inner

```python
def outer(func):
    def inner():
        print("我要睡觉了...")
        func()
        print("我睡醒了...")
    return inner

@outer
def sleep():
    import random
    import time
    print("睡眠中...")
    time.sleep(random.randint(1,5))

sleep()
```

**总结：装饰器就是使用创建一个闭包函数,在闭包函数内调用目标函数。可以达到不改动目标函数的同时，增加额外的功能。**

### 设计模式

设计模式：设计模式是一种编程套路，可以极大的方便程序的开发。最常见、最经典的设计模式，就是我们所学习的面向对象(oop)。

除了面向对象外,在编程中也有很多既定的套路可以方便开发:

**单例、工厂**模式

建造者、责任链、状态、备忘录、解释器、访问者、观察者、中介、模板、代理模式

#### 单例模式

```python
class Tool:
    pass

t1 = Tool()
t2 = Tool()
print(t1)
print(t2)
```

![1765071279390](image/Note/1765071279390.png)

创建类的实例后，就可以得到一个完整的、独立的类对象。通过print语句可以看出,它们的内存地址是不相同的,即t1和t2是完全独立的两个对象

某些场景下，我们需要一个类**无论获取多少次类对象，都仅仅提供一个具体的实例用以节省创建类对象的开销和内存开销**

比如某些工具类，仅需要1个实例，即可在各处使用,这就是单例模式想要实现的效果

单例模式(Singleton Pattern)是一种常用的软件设计模式,该模式的主要目的是确保某一个类只有一个实例存在。在整个系统中，某个类只能出现一个实例时,单例对象就能派上用场。

    定义：保证一个类只有一个实例,并提供一个访问它的全局访问点

    适用场景:当一个类只能有一个实例,而客户可以从一个众所周知的访问点访问它时。

##### 单例的实现模式

在一个文件中

```python
# mytest.py
class StrTools:
    pass

str_tool = StrTools()
```

另一个文件中导入对象

```python
from mytest import str_tool

s1 = str_tool
s2 = str_tool
print(s1)
print(s2)
```

输出：（id())函数可以给出对象id）

![1765072007228](image/Note/1765072007228.png)

#### 工厂模式

    当需要大量创建一个类的实例的时候，可以使用工厂模式。即，**从原生的使用类的构造去创建对象的形式迁移到基于工厂提供的方法去创建对象的形式**。

```python
class Person:
    pass

class Worker(Person):
    pass

class Student(Person):
    pass

class Teacher(Person):
    pass

class Factory:
    def get_person(self, p_type):
        if p_type == 'w':
            return Worker()
        elif p_type == 's':
            return  Student()
        else:
            return Teacher()
  
factory = Factory()
worker = factory.get_person('w')
stu = factory.get_person('s')
teacher = factory.get_person('t')
```

这样做的好处：

- **大批量创建对象的时候有统一的入口，易于代码维护**
- **当发生修改，仅修改工厂类的创建方法即可，调整生产线**
- 符合现实世界的模式，即由工厂来制作产品(对象)

## Python并发编程

### 问题引入

#### 为什么要引入并发编程?

场景1:一个网络爬虫，按顺序爬取花了1小时，采用并发下载减少到20分钟!

场景2:一个APP应用，优化前每次打开页面需要3秒，采用异步并发提升到每次200毫秒;

由此可得：**引入并发，就是为了提升程序运行速度**

#### 有哪些程序提速的方法？

- threading模块的多线程开发
- multiprocessing模块，实现多核多CPU的并行执行

![1765078470513](image/Note/1765078470513.png)

#### Python对并发编程的支持

- 多线程:threading，利用CPU和IO可以同时执行的原理，让CPU不会干巴巴等待IO完成
- 多进程:multiprocessing，利用多核CPU的能力，真正的并行执行任务
- 异步IO:asyncio，在单线程利用CPU和IO同时执行的原理，实现函数粒度异步执行
- 使用Lock对资源加锁，防止冲突访问
- 使用Queue实现不同线程/进程之间的数据通信，实现生产者-消费者模式
- 使用线程池Pool/进程池Po0l，简化线程/进程的任务提交、等待结束、获取结果
- 使用subprocess启动外部程序的进程，并进行输入输出交互

### 进程，线程的概念

现代操作系统比如Mac OS,UNIX,Linux,Windows等,都是支持多任务的分时操作系统。**操作系统中可以运行多个进程，即多任务运行**
进程:就是一个程序,运行在系统之上,那么便称之这个程序为一个运行进程,并分配进程ID方便系统管理。**一个进程内可以运行多个线程，即多线程运行**
线程:线程是归属于进程的,一个进程可以开启多个线程,执行不同的工作,是进程的实际工作最小单位。

### 进程的内存隔离和线程的内存共享

进程之间是内存隔离的，即不同的进程拥有各自的内存空间。
线程之间是内存共享的,线程是属于进程的,一个进程内的多个线程之间是共享这个进程所拥有的内存空间的。
![1765074830219](image/Note/1765074830219.png)

### 并发

并发(concurrency):指在同一时刻只能有一条指令执行，但多个进程指令被快速的轮换执行，使得在宏观上具有多个进程同时执行的效果，但在微观上并不是同时执行的，只是把时间分成若干段，使多个进程快速交替的执行。并发是指一个处理器同时处理多个任务

### 并行

并行：指的是同一时间做不同的工作。进程之间就是并行执行的,操作系统可以同时运行很多进程。指在同一时刻，有多条指令在多个处理器上同时执行。

除了进程外,线程其实也是可以并行执行的。即一个程序在同一时间做两件乃至多件不同的事情，就称为，**多线程并行执行**。

**并发是逻辑上的同时发生(simultaneous)，而并行是物理上的同时发生**

### Python并发编程的三种方式

多线程Thread,多进程Process,多协程Coroutine

#### 什么是CPU密集型计算、I0密集型计算?

##### CPU-bound

    CPU密集型也叫计算密集型，是指I/O在很短的时间就可以完成，CPU需要大量的计算和处理，特点是CPU占用率相当高。例如:压缩解压缩、加密解密、正则表达式搜索

##### I/O-bound

    IO密集型指的是系统运作大部分的状况是CPU在等I/O(硬盘/内存)的读/写操作，CPU占用率仍然较低。例如:文件处理程序、网络爬虫程序、读写数据库程序

#### 多线程、多进程、多协程的对比

一个进程中可以启动N个线程，一个线程中可以启动N个协程

##### 多进程 Process(multiprocessing)

优点:可以利用多核CPU并行运算（只有多进程可以）

缺点:占用资源最多、可启动数目比线程少适用于:CPU密集型计算

##### 多线程 Thread (threading)

优点:相比进程，更轻量级、占用资源少。

缺点:
相比进程:多线程只能并发执行，不能利用多CPU(GIL,全局解释器锁)

相比协程:启动数目有限制，占用内存资源，有线程切换开销

适用于:IO密集犁计算、同时运行的任务数目要求不多

##### 多协程 Coroutine(asyncio )

优点:内存开销最少、启动协程数量最多

缺点:支持的库有限制代码实现复杂(aionttp vs requests )
适用于:IO密集型计算需要超多任务运行、但有现成库支持的场景

#### 怎样根据任务选择对应技术?

![1765083450262](image/Note/1765083450262.png)

#### 全局解释器锁GIL--Python速度慢的头号嫌疑犯

##### Python速度慢的两大原因？

    相比C/C++/JAVA，python确实慢，-些特殊场景下，Python比C++慢100~200倍。由于速度慢的原因，很多公司的基础架构代码依然用C/C++开发比如各大公司阿里/腾讯/快手的推荐引擎、搜索引擎、存储引擎等底层对性能要求高的模块

![1765083651259](image/Note/1765083651259.png)   ![1765083672623](image/Note/1765083672623.png)

##### GIL是什么?

    全局解释器锁(英语:Global Interpreter Lock，缩写GIL)是计算机程序设计语言解释器用于同步线程的一种机制，它使得任何时刻仅有一个线程在执行。即便在多核心处理器上，使用 GIL 的解释器也只允许同一时间执行一个线程。

    ![1765083758506](image/Note/1765083758506.png)

[图片来源](http://www.dabeaz.com/python/UnderstandingGIL.pdf)

    由于GIL的存在，即使电脑有多核CPU，单个时刻也只能使用1个，相比并发加速的C++/JAVA所以慢。

##### 为什么有GIL这个东西?

    简而言之:Python设计初期，为了规避并发问题引入了GIL，现在**想去除却去不掉了**!引入目的是为了解决多线程之间数据完整性和状态同步问题。

**原因详解：**

    Python中对象的管理，是使用引用计数器进行的，引用数为0则释放对象，不加锁可能导致引用计数器功能发生混乱
	开始:线程A和线程B都引用了对象obj，obj.ref_num=2，假设线程A和B都想撤销对obj的引用

![1765084561666](image/Note/1765084561666.png)

GIL确实有好处，简化了Python对共享资源的管理

##### 怎样规避GIL带来的限制?

1. 多线程 threading 机制依然是有用的，用于IO密集型计算。因为在 I/O(read,write,send,recv,etc.)期间，线程会释放GIL，实现CPU和IO的并行因此多线程用于IO密集型计算依然可以大幅提升速度但是多线程用于CPU密集型计算时，只会更加拖慢速度。
2. 使用multiprocessing 的多进程机制实现并行计算、利用多核CPU优势为了应对GIL的问题，Python提供了multiprocessing。

#### threading模块

绝大多数编程语言,都允许多线程编程，Pyhton也不例外。Python的多线程可以通过threading模块来实现。

语法：

```python
import threading

thread_obj = threading.Thread([group [, target [, name[, args[, kwargs]]]]])
- group:暂时无用，未来功能的预留参数
- target: 执行的目标任务名
- args: 以元组方式给执行任务传参
- kwargs: 以字典方式给执行任务传参
- name: 线程名，一般不用设置

# 启动线程，让线程开始工作
thread_obj.start()
```

需求：同时执行两个函数，一边写代码，一边摸鱼

```python
import time
import threading

def code():
    while True:
        print("我在写代码...")
        time.sleep(1)

def relax():
    while True:
        print("我在摸鱼...")
        time.sleep(1)

if __name__ == "__main__":
    # 创建写代码线程
    code_thread = threading.Thread(target=code)
    # 创建摸鱼线程
    relax_thread = threading.Thread(target=relax)

    #让线程启动
    code_thread.start()
    relax_thread.start()
```

**传参**可以通过args参数通过元组(按参数顺序)的方式传参或使用kwargs参数用字典的形式传参

```python
import time
import threading

def code(msg):
    while True:
        print(f"我在{msg}...")
        time.sleep(1)

def relax(msg):
    while True:
        print(f"我在{msg}...")
        time.sleep(1)



if __name__ == "__main__":
    # 创建写代码线程
    code_thread = threading.Thread(target=code, args=("写python",))
    # 创建摸鱼线程
    relax_thread = threading.Thread(target=relax, kwargs={"msg":"发呆"})

    #让线程启动
    code_thread.start()
    relax_thread.start()
```

## Python数据分析

### ipython

> 简介

> IPython是python的一个交互式shell，它比默认的"python shell"更方便，支持变量自动补全，自动缩进，支持 bash shell 命令，内置了许多强大的功能和函数。ipython会让我们以一种更高的效率来使用python，同时它也是利用Python进行科学计算和交互可视化的一个最佳的平台

IPython 是基于BSD 开源的，并且IPython为交互式计算提供了一个丰富的架构

- 强大的交互式shell
- 供jupyter notebook使用的jupyter内核
- 交互式的数据可视化工具
- 灵活、可嵌入的解释器
- 易于使用，高性能的并行计算工具

> ipython 安装

```powershell
pip install ipython
ipython --version
ipython
quit 或 exit
```

![1765978972510](image/Note/1765978972510.png)

> ipython使用技巧

- Tab键自动补全

  在shell中输入表达式时，按下Tab键可将当前命名空间中任何与已输入的字符串相匹配的变量(对象、函数等)显示出来![1765979208410](image/Note/1765979208410.png)
- 内省

  当某对象的信息不是很明确时，可以在变量的前面或后面加上问号(?)，有关该对象的一些通用信息就会显示出来

![1765979297672](image/Note/1765979297672.png)

- 中断正在执行的代码

  在代码执行过程中，只要按下Ctrl + C，就会引发一个KeyboardInterrupt,除了一些特殊的情况以外，绝大部分Python程序会立即停止执行
- 键盘常用快捷键

| 快捷键       | 作用                             |
| ------------ | -------------------------------- |
| Ctrl+P 或 ↑ | 后向搜索命令                     |
| Ctrl+N 或 ↓ | 前向搜索命令                     |
| Ctrl+R       | 按行读取反向历史搜索（部分匹配） |
| Ctrl+Shift+V | 从剪切板粘贴文本                 |
| Ctrl+A       | 将光标移动到行首                 |
| Ctrl+E       | 将光标移动到行尾                 |
| Ctrl+K       | 删除从光标开始至行尾的文本       |
| Ctrl+U       | 清除从光标开始至行首的文本       |
| Ctrl+F       | 将光标向前移动一个字符           |
| Ctrl+B       | 将光标向后移动一个字符           |
| Ctrl+L       | 清屏                             |

> 魔术命令

IPython之所以比默认的“Python shell”交互性更强、使用更方便，是因为IPython中包含很多使用方便的魔术命令

- %run

  作用:运行Python程序

```shell
%run 路径+Python文件名称
```

    ![1765980119958](image/Note/1765980119958.png) ![1765980158187](image/Note/1765980158187.png)

- %time
  作用:一次执行代码的总体时间，其结果是会变的，为了得到更为精确的结果，需要使用魔术函数%timeit

  ![1765980778991](image/Note/1765980778991.png)
- %timeit

  作用:可快速测量代码运行时间，相同的命令会在一个循环中多次执行，多次运行时长的平均值作为该命令的最终评估时长

  ![1765980827611](image/Note/1765980827611.png)

  参数：-r选项控制执行循环的次数，-n选项可以控制命令在单次循环中执行的次数

  ![1765980918248](image/Note/1765980918248.png)
- %paste

  作用:将剪切板中复制的代码直接粘贴到IPython中并自动执行

  ![1765981136914](image/Note/1765981136914.png)![1765981207136](image/Note/1765981207136.png)
- cpaste

  作用:与%paste命令类似，也是粘贴文本，但有所不同的是%cpaste命令在输入后会出现提示信息。提示信息的意思是可不断粘贴代码到IPython中，直到输入"“并回车或使用Ctr1+D结束粘贴。在需粘贴的代码量比较大时，可实现代码的分步粘贴，粘贴完成可手动结束，且不用担心代码被提前执行，极大方便了操作者
- %reset

  作用:删除interactive命名空间中全部的变量名(interactive命名空间是存储Python变量和名称的空间)

  ![1765981461494](image/Note/1765981461494.png)
- %xdel

  作用:删除单个变量的引用

  ```shell
  %xdel 变量名
  ```

  ![1765981388629](image/Note/1765981388629.png)
- %hist

  作用：查看历史的命令
- %pylab

  作用:可使NumPy和Matplotlib中的科学计算功能生效，这些功能被称为基于向量和矩阵的高效操作、交互可视化特性。它能够让开发人员在控制台进行交互式计算和动态绘图
- %logstart

  作用:开启IPython日志

  ```shell
  %logstart [logname[logmodel]]
  ```

  | 参数     | 说明         |
  | -------- | ------------ |
  | logname  | 日志保存路径 |
  | logmodel | 日志模式     |

| 日志模式的值 | 说明                                         |
| ------------ | -------------------------------------------- |
| over         | 若存在 log，则直接覆盖之前的 log             |
| backup       | 默认模式，若存在 log 则直接将之前的 log 备份 |
| append       | 在之前 log 中追加                            |
| rotate       | 回滚                                         |

- %magic

  作用:查看魔术命令，可直接显示所有魔术命令的详细文档
  退出:q
- %pdb

  作用:在异常点启动调试器，接下来就能在调试模式下访问所有的本地变量和整个栈回溯，可使用u和d来向上和向下访问栈，使用q退出调试器。在调试器中输入?可查看所有可用命令
- %debug

  作用:从最新的异常跟踪的底部进入交互调试器
- %quickref

  作用:显示IPython的快速参考

> ipython执行shell命令

```shell
!shell命令
```

还可以接收命令的返回值

```shell
变量=!shell命令
```

![1765983292275](image/Note/1765983292275.png)

### jupyter

> 简介

    Jupyter Notebook是一个交互式的Web应用程序，便于创建和共享文学化程序文档，支持实时代码，数学方程，可视化和markdown

    用途包括:数据清理和转换，数值模拟，统计建模，机器学习等，是数据分析常用的应用程序，运行方法只需在使用的文件夹下输入命令jupyter notebook即可

> 组成部分

- 网页应用

  网页应用即基于网页形式的、结合了编写说明文档、数学公式、交互计算和其他富媒体形式的工具。简言之，网页应用是可以实现各种功能的工具
- 文档

  即Jupyter Notebook中所有交互计算、编写说明文档、数学公式、图片以及其他富媒体形式的输入和输出，都是以文档的形式体现的

  这些文档是保存为后缀名为 `.ipynb`的JSON格式文件，不仅便于版本控制，也方便与他人共享

  文档还可以导出为:HTML、LaTeX、PDF等格式

> 主要特点

- 编程时具有语法高亮、缩进、tab补全的功能
- 可直接通过浏览器运行代码，同时在代码块下方展示运行结果
- 以富媒体格式展示计算结果。富媒体格式包括:HTML，LaTeX，PNG，SVG等
- 对代码编写说明文档或语句时，支持Markdown语法
- 支持使用LaTeX编写数学性说明

> 安装

```shell
pip install jupyter
```

### anaconda

### numpy

> 简介

NumPy(Numerical Python)是 Python 语言的一个扩展程序库，支持大量的维度数组与矩阵运算，此外也针对数组运算提供大量的数学函数库


NumPy 的前身 Numeric 最早是由 Jim Hugunin 与其它协作者共同开发，2005 年，Travis Oliphant 在 Numeric 中结合了另一个同性质的程序库 Numarray 的特色，并加入了其它扩展而开发了 NumPy。NumPy为开放源代码并且由许多协作者共同维护开发

> 作用

NumPy 是一个运行速度非常快的数学库，主要用于数组计算

> 包含

- 一个强大的N维数组对象 ndarray
- 广播功能函数
- 整合 C/C++/Fortran 代码的工具
- 线性代数、傅里叶变换、随机数生成等功能

> 优势

- 对于同样的数值计算任务，使用numpy要比直接编写Python代码便捷的多
- numpy中的数组的存储效率和输入输出性能均远远优于Python中等价的基本数据结构，且其能够提升性能是与数组中的元素成比例的
- 其底层算法在设计时就有着优异的性能，这使numpy的大部分代码都是用C语言写的,得numpy比纯Python代码高效得多

> 应用

NumPy 通常与 SciPy(Scientific Python)和 Matplotlib(绘图库)一起使用，这种组合广泛用于替代 MatLab，是一个强大的科学计算环境，有助于我们通过 Python 学习数据科学或者机器学习

> SciPy

是一个开源的 Python 算法库和数学工具包

包含的模块有最优化、线性代数、积分、插值、特殊函数、快速傅里叶变换、信号处理和图像处理、常微分方程求解和其他科学与工程中常用的计算

> Matplotlib

是 Python 编程语言及其数值数学扩展包 NumPy 的可视化操作界面。它为利用通用的图形用户界面工具包，如 Tkinter,wxPython,Qt或 GTK+ 向应用程序嵌入式绘图提供了应用程序接口(API)

> 安装

```shell
pip install numpy
conda install numpy
```

### Ndarray对象简介

> 介绍

- NumPy 最重要的一个特点是其 N 维数组对象 ndarray，它是一系列同类型数据的集合，以0下标为开始进行集合中元素的索引
- ndarray 对象是用于存放同类型元素的多维数组
- ndarray 中的每个元素在内存中都有相同存储大小的区域

> 组成

![1766023111779](image/Note/1766023111779.png)

- 一个指向数据(内存或内存映射文件中的一块数据)的指针
- 数据类型或 dtype，描述在数组中的固定大小值的格子
- 一个表示数组形状(shape)的元组，表示各维度大小的元组
- 一个跨度元组(stride)，其中的整数指的是为了前进到当前维度下一个元素需要"跨过"的字节数

> numpy数据类型

numpy 支持的数据类型比 Python 内置的类型要多很多，基本上可以和C语言的数据类型对应上，其中部分类型对应为 Python 内置的类型
numpy 的数值类型实际上是 dtype 对象的实例，并对应唯一的字符，包括 np.bool_,np.int32,np.float32


| 类型       | 说明                                                                       |
| ---------- | -------------------------------------------------------------------------- |
| bool_      | 布尔型数据类型（True 或者 False）                                          |
| int_       | 默认的整数类型（类似于 C 语言中的 long，int32 或 int64）                   |
| intc       | 与 C 的 int 类型一样，一般是 int32 或 int64                                |
| intp       | 用于索引的整数类型（类似于 C 的 ssize_t，一般情况下仍然是 int32 或 int64） |
| int8       | 字节（-128 to 127）                                                        |
| int16      | 整数（-32768 to 32767）                                                    |
| int32      | 整数（-2147483648 to 2147483647）                                          |
| int64      | 整数（-9223372036854775808 to 9223372036854775807）                        |
| uint8      | 无符号整数（0 to 255）                                                     |
| uint16     | 无符号整数（0 to 65535）                                                   |
| uint32     | 无符号整数（0 to 4294967295）                                              |
| uint64     | 无符号整数（0 to 18446744073709551615）                                    |
| float      | float64 类型的简写                                                         |
| float16    | 半精度浮点数，包括：1 个符号位，5 个指数位，10 个尾数位                    |
| float32    | 单精度浮点数，包括：1 个符号位，8 个指数位，23 个尾数位                    |
| float64    | 双精度浮点数，包括：1 个符号位，11 个指数位，52 个尾数位                   |
| complex    | complex128 类型的简写，即 128 位复数                                       |
| complex64  | 复数，表示双 32 位浮点数（实数部分和虚数部分）                             |
| complex128 | 复数，表示双 64 位浮点数（实数部分和虚数部分）                             |

每个内建类型都有一个唯一定义它的字符代码

| 字符代码 | 含义                  |
| -------- | --------------------- |
| b        | 布尔型                |
| i        | （有符号）整型        |
| u        | 无符号整型            |
| f        | 浮点型                |
| c        | 复数浮点型            |
| m        | timedelta（时间间隔） |
| M        | datetime（日期时间）  |
| O        | （Python）对象        |
| S, a     | （byte-）字符串       |
| U        | Unicode               |
| V        | 原始数据（void）      |

> 数据类型对象dtype

数据类型对象是用来描述与数组对应的内存区域如何使用，这依赖如下几个方面:

- 数据的类型(整数，浮点数或者 Python 对象)
- 数据的大小(例如，整数使用多少个字节存储)
- 数据的字节顺序(小端法或大端法)【通过对数据类型预先设定"<"或">"来决定的。<"意味着小端法(最小值存储在最小的地址，即低位组放在最前面)。">"意味着大端法(最重要的字节存储在最小的地址，即高位组放在最前面)】
- 在结构化类型的情况下，字段的名称、每个字段的数据类型和每个字段所取的内存块的部分
- 如果数据类型是子数组，它的形状和数据类型

> 创建数据类型对象

原型：

```python
numpy.dtype(object, align, copy)
```

| 参数   | 说明                                                        |
| ------ | ----------------------------------------------------------- |
| object | 要转换为的数据类型对象                                      |
| align  | 如果为 true，填充字段使其类似 C 的结构体                    |
| copy   | 复制 dtype 对象，如果为 false，则是对内置数据类型对象的引用 |

- 基本使用

```python
import numpy as np
dt = np.dtype(np.int32)
print(dt)
print(type(dt))
```

### 创建Ndarray数组对象

> 说明

numpy默认ndarray的所有元素的类型是相同的,这一点与Python中的list不同如果传进来的列表中包含不同的类型，则统一为同一类型，优先级:str>float>int

> array()函数

原型

```python
numpy.array(object, dtype = None, copy = True, order = None, subok = False, ndmin = 0)
```

作用：创建Ndarray数组对象


| 参数   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| object | 数组或嵌套的数列                                             |
| dtype  | 数组元素的数据类型，可选                                     |
| copy   | 对象是否需要复制，可选                                       |
| order  | 创建数组的样式，C 为行方向，F 为列方向，A 为任意方向（默认） |
| subok  | 默认返回一个与基类类型一致的数组                             |
| ndmin  | 指定生成数组的最小维度                                       |

- array()创建一维数组

```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5])
print(arr)
print(type(arr))
```

> asarray()函数

原型：

```python
numpy.asarray(a, dtype = None, order = None)
```

作用:类似 numpy.array，但 numpy.asarray 只有三个参数，比 numpy.array 少两个

| 参数  | 说明                                                                               |
| ----- | ---------------------------------------------------------------------------------- |
| data  | 任意形式的输入参数，可以是列表、列表的元组、元组、元组的元组、元组的列表、多维数组 |
| dtype | 数据类型，可选                                                                     |
| order | 可选，有 "C" 和 "F" 两个选项，分别代表行优先和列优先，在计算机内存中存储元素的顺序 |

```python
import numpy as np
x = [1,2,3,4,5]
arr = np.asarray(x)
print(arr)
```

> empty()函数

原型：

```python
numpy.empty(shape, dtype = float, order = 'C)
```

作用:创建一个指定形状(shape)、数据类型(dtype)且未初始化的数组


| 参数  | 说明                                                                         |
| ----- | ---------------------------------------------------------------------------- |
| shape | 数组形状                                                                     |
| dtype | 数据类型，可选                                                               |
| order | 有 "C" 和 "F" 两个选项，分别代表行优先和列优先，在计算机内存中存储元素的顺序 |

```python
import numpy as np
arr = np.empty([3, 2], dtype=int)
#数组元素为随机值，因为它们未初始化arr
print(arr)
```

> zeros()函数

原型：

```python
numpy.zeros(shape, dtype=float, order='C')
```

作用:创建指定大小的数组，数组元素以0来填充

| 参数  | 说明                                                |
| ----- | --------------------------------------------------- |
| shape | 数组形状                                            |
| dtype | 数据类型，可选                                      |
| order | "C" 用于 C 的行数组，或者 "F" 用于 FORTRAN 的列数组 |

```python
import numpy as np
arr = np.zeros(5)
print(arr)
```

```python
import numpy as np
arr = np.zeros([3,2])
print(arr)
```

> ones()函数

原型

```python
numpy.ones(shape, dtype=None, order='C')
```

作用:创建指定形状的数组，数组元素以1来填充

| 参数  | 说明                                                |
| ----- | --------------------------------------------------- |
| shape | 数组形状                                            |
| dtype | 数据类型，可选                                      |
| order | "C" 用于 C 的行数组，或者 "F" 用于 FORTRAN 的列数组 |

```python
import numpy as np
arr = np.ones(5)
print(arr)
```

```python
import numpy as np
arr = np.ones([3,2])
print(arr)
```

> full()函数

原型：

```python
numpy.full(shape, fill_value, dtype=None, order = 'C')
```

作用:创建指定形状的数组，数组元素以 fil_value 来填充

| 参数       | 说明                                                |
| ---------- | --------------------------------------------------- |
| shape      | 数组形状                                            |
| fill_value | 填充的数据                                          |
| dtype      | 数据类型，可选                                      |
| order      | "C" 用于 C 的行数组，或者 "F" 用于 FORTRAN 的列数组 |

```python
import numpy as np
arr = np.full(5, fill_value=1024)
print(arr)
```

```python
import numpy as np
arr = np.full([3,2], fill_value=1024)
print(arr)
```

> eye()函数

原型：

```python
numpy.eye(N, M=None, k=0, dtype=float, order='C')
```

作用:对角线为1其他的位置为0

| 参数  | 说明                                                |
| ----- | --------------------------------------------------- |
| N     | 行数量                                              |
| M     | 列数量，默认等于行数量，可选                        |
| dtype | 数据类型，可选                                      |
| order | "C" 用于 C 的行数组，或者 "F" 用于 FORTRAN 的列数组 |

```python
import numpy as np
arr = np.eye(10, dtype=int)
print(arr)
```

> arange()函数

原型

```python
numpy.arange(start, stop, step, dtype)
```

作用:创建数值范围并返回 ndarray 对象，根据start 与 stop 指定的范围以及 step 设定的步长，生成一个 ndarray

| 参数  | 说明                                                          |
| ----- | ------------------------------------------------------------- |
| start | 起始值，默认为 0                                              |
| stop  | 终止值（不包含）                                              |
| step  | 步长，默认为 1                                                |
| dtype | 返回 ndarray 的数据类型，如果没有提供，则会使用输入数据的类型 |

```python
import numpy as np
arr = np.arange(1, 11, 1)
print(arr)
```

> frombuffer()函数

原型：

```python
numpy.frombuffer(buffer, dtype=float, count=-1, offdet=0)
```

作用:用于实现动态数组，接受 buffer 输入参数，以流的形式读入转化成ndarray对象

| 参数   | 说明                                    |
| ------ | --------------------------------------- |
| buffer | 可以是任意对象，会以流的形式读入        |
| dtype  | 返回数组的数据类型，可选                |
| count  | 读取的数据数量，默认为 -1，读取所有数据 |
| offset | 读取的起始位置，默认为 0                |

注意:buffer 是字符串的时候，Python3 默认 str 是 Unicode 类型，所以要转成bytestring在原 str前加上b

```python
import numpy as np
x = b'I am a good man'
arr = np.frombuffer(x, dtype='S1')
print(arr)
```

> fromiter()函数

原型：

```python
numpy.fromiter(iterable, dtype, count=-1)
```

作用:从可迭代对象中建立 ndarray 对象，返回一维数组

| 参数     | 说明                                    |
| -------- | --------------------------------------- |
| iterable | 可迭代对象                              |
| dtype    | 返回数组的数据类型，可选                |
| count    | 读取的数据数量，默认为 -1，读取所有数据 |

```python
import numpy as np
x = [1,2,3,4,5]
z = iter(x)
arr = np.fromiter(z, dtype='f')
print(arr)
```

> linspace()函数

原型：

```python
numpy.linspace(start, stop, num=50, endpoint=True, retstep=Flse,dtype=None)
```

作用:创建一个一维数组，数组是一个等差数列构成的

| 参数     | 说明                                                        |
| -------- | ----------------------------------------------------------- |
| start    | 序列的起始值                                                |
| stop     | 序列的终止值，如果 endpoint 为 true，该值包含于数列中       |
| num      | 要生成的等步长的样本数量，默认为 50                         |
| endpoint | 该值为 true 时，数列中包含 stop 值，反之不包含，默认是 true |
| retstep  | 如果为 true，生成的数组中会显示间距，反之不显示             |
| dtype    | ndarray 的数据类型                                          |

```python
import numpy as np
arr = np.linspace(1, 10, 10, dtype='i4')
print(arr)
```

> logspace()函数

原型：

```python
numpy.logspace(start, stop, num=50, endpoint=True, base=10.0, dtype=None)
```

作用：创建一个等比数列

| 参数     | 说明                                                                |
| -------- | ------------------------------------------------------------------- |
| start    | 序列的起始值为：base**start                                         |
| stop     | 序列的终止值为：base**stop。如果 endpoint 为 true，该值包含于数列中 |
| num      | 要生成的等步长的样本数量，默认为 50                                 |
| endpoint | 该值为 true 时，数列中包含 stop 值，反之不包含，默认是 true         |
| base     | 对数 log 的底数，默认是 10                                          |
| dtype    | ndarray 的数据类型                                                  |

```python
import numpy as np
arr = np.logspace(1.0, 2.0, 10)
print(arr)
```

> random.rand()

原型：`rand(d0, d1, ..., dn)`

作用:生成[0,1)之间的随机数

- 生成0到1之间的随机数

```python
import numpy as np
arr = np.random.rand()
print(arr)
```

- 生成一个有3个元素的一位数组，元素值在0到1之间

```python
import numpy as np
arr = np.random.rand(3)
print(arr)
```

- 生成一个二维数组，元素值在0到1之间

```python
import numpy as np
arr = np.random.rand(3,2)
print(arr)
```

- 生成一个三维数组，元素值在0到1之间

```python
import numpy as np
arr = np.random.rand(3,2,2)
print(arr)
```

> random.random()

原型：`random(size=None)`

作用：生成[0,1)之间的随机数

| 参数 | 说明     |
| ---- | -------- |
| size | 元素个数 |

- 生成0到1之间的随机数

```python
import numpy as np
arr = np.random.random()
print(arr)
```

- 生成一个有3个元素的一维数组，元素值在0到1之间,不可以传两个参数

```python
import numpy as np
arr = np.random.random(3)
print(arr)
```

> random.randint()

原型:`randint(low, high=None, size=None, dtype='1')`

作用：生成随机数

| 参数  | 说明         |
| ----- | ------------ |
| low   | 包含的下限   |
| high  | 不包含的上限 |
| size  | 元素个数     |
| dtype | 元素类型     |

> random.randn()

原型:`randn(d0, d1,...dn)`

作用:返回一个或一组样本，具有标准正态分布

标准正态分布:又称为u分布，是以0为均值、以1为标准差的正态分布，记为N(0，1)

```python
import numpy as np
arr = np.random.randn()
print(arr)
```

```python
import numpy as np
arr = np.random.randn(2,4)
print(arr)
```

```python
import numpy as np
arr = np.random.randn(4,3,2)
print(arr)
```

> random.normal()

原型：`normal(loc=0.0, scale=1.0, size=None)`

作用：生成高斯分布的概率密度随机数

| 参数  | 说明                                                                             |
| ----- | -------------------------------------------------------------------------------- |
| loc   | 浮点型，此概率分布的均值（对应整个分布的中心 centre）                            |
| scale | 浮点型，此概率分布的标准差（对应分布的宽度，scale 越大越矮胖，scale 越小越瘦高） |
| size  | 输出的 shape，默认为 None，仅输出一个值                                          |

```python
import numpy as np
arr = np.random.normal(loc=1, scale=2, size=5)
print(arr)
```

### numpy数组与Python中列表的对比

> 效率对比

```python
li = []
for i in range(1000000):
	li.append(random.random())
```

> Python中列表

```python
import random
import time
t1 = time.time()
ret = sum(li)
t2 = time.time()
print("耗时:%f"%(t2-t1))
print(ret)
```

> numpy数组

```python
import numpy as np
n = np.array(li)
t1 = time.time()
ret = np.sum(n)
t2 = time.time()
print("耗时:%f"%(t2-t1))
print(ret)
```

### Ndarray数组属性

NumPy数组的维数称为秩(rank)，一维数组的秩为1，二维数组的秩为2，以此类推

在 NumPy中，每一个线性的数组称为是一个轴(axis)，也就是维度(dimensions)。比如说，二维数组相当于是两个一维数组，其中第一个一维数组中每个元素又是一个一维数组。所以一维数组就是 NumPy 中的轴(axis)，第一个轴相当于是底层数组，第二个轴是底层数组里的数组。而轴的数量一一秩，就是数组的维数

很多时候可以声明 axis。axis=0，表示沿着第0轴进行操作，即对每一列进行操作;axis=1，表示沿着第1轴进行操作，即对每一行进行操作

> 常用属性

| 属性     | 说明                                                                                 |
| -------- | ------------------------------------------------------------------------------------ |
| ndim     | 秩，即轴的数量或维度的数量                                                           |
| shape    | 数组的维度，对于矩阵，n 行 m 列                                                      |
| size     | 数组元素的总个数，相当于 `.shape` 中 n×m 的值                                     |
| dtype    | `ndarray` 对象的元素类型                                                           |
| itemsize | `ndarray` 对象中每个元素的大小，以字节为单位                                       |
| flags    | `ndarray` 对象的内存信息                                                           |
| real     | `ndarray` 元素的实部                                                               |
| imag     | `ndarray` 元素的虚部                                                               |
| data     | 包含实际数组元素的缓冲区，由于一般通过数组的索引获取元素，所以通常不需要使用这个属性 |

> ndim

```python
import numpy as np
arr = np.arange(24)
print(arr)
print(arr.ndim)
# 调整维数
li = arr.reshape(2,3,4)
print(li)
print(li,ndim)
```

> shape

表示数组的维度，返回一个元组，这个元组的长度就是维度的数目，即ndim 属性(秩)。比如，一个二维数组，其维度表示“行数“和“列数"

- 得到维度

```python
import numpy as np
arr = np.array([[1,2,3],[4,5,6]])
print(arr)
print(arr.shape)
```

- 调整数组大小

```python
import numpy as np
arr = np.array([[1,2,3], [4,5,6]])
arr.shape = (3,2)
print(arr)
print(arr.shape)
```

> size

```python
import numpy as np
arr = np.array([[1,2,3],[4,5,6]])
print(arr)
print(arr.size)
```

> dtype

```python
import numpy as np
arr = np.array([[1,2,3],[4,5,6]])
print(arr)
print(arr.dtype)
```

> itemsize

以字节的形式返回数组中每一个元素的大小

```python
import numpy as np
arr1 = np.array([1,2,3,4,5], dtype='i1')
print(arr1)
```

> flags

返回 ndarray 对象的内存信息

| 值               | 说明                                                                   |
| ---------------- | ---------------------------------------------------------------------- |
| C_CONTIGUOUS (C) | 数据是在一个单一的 C 风格的连续段中                                    |
| F_CONTIGUOUS (F) | 数据是在一个单一的 Fortran 风格的连续段中                              |
| OWNDATA (O)      | 数组拥有它所使用的内存或从另一个对象中借用它                           |
| WRITEABLE (W)    | 数据区域可以被写入，将该值设置为 False 则数据为只读                    |
| ALIGNED (A)      | 数据和所有元素都适当地对齐到硬件上                                     |
| UPDATEIFCOPY (U) | 这个数组是其它数组的一个副本，当这个数组被释放时，原数组的内容将被更新 |

```python
import numpy as np
arr = np.array([1,2,3,4,5])
print(arr)
print(arr.flags)
```

> 切片和索引

ndarray对象的内容可以通过索引或切片来访问和修改，与Python中list 的切片操作一样

ndarray 数组可以基于0-n的下标进行索引，切片对象可以通过内置的 slice 函数，并设置start,stop及step 参数从原数组中切割出一个新数组

```python
import numpy as np
arr = np.arange(10)
print(arr[1])
# 从索引2开始到索引7停止，间隔为2
s = slice(2,7,2)
print(arr)
print(arr[s])
```

可以通过冒号分隔切片参数 start:stop:step 来进行切片操作

```python
import numpy as np
arr = np.arange(10)
# 从索引2开始到索引7停止，间隔为2
arr2 = arr[2:7:2]
print(arr)
print(arr2)
```

> 冒号:的解释

- 如果只放置一个参数，如[2]，将返回与该索引相对应的单个元素。如果为[2:]，表示从该索引开始以后的所有项都将被提取。如果使用了两个参数，如[2:7]，那么则提取两个索引(不包括停止索引)之间的项

```python
import numpy as np
arr = np.arange(10)
arr2 = arr[5]
print(arr)
print(arr2)
```

```python
import numpy as np
arr = np.arange(10)
arr2 = arr[2:]
print(arr)
print(arr2)
```

```python
import numpy as np
arr = np.arange(10)
arr2 = arr[2:6]
print(arr)
print(arr2)
```

多维数组同样适用上述索引提取方法

```python
import numpy as np
arr = np.array([1,2,3],[4,5,6],[7,8,9],[10,11,12],[13,14,15])
arr2 = arr[2]
print(arr)
print("\n")
print(arr2)
```

```python
import numpy as np
arr = np.array([1,2,3],[4,5,6],[7,8,9],[10,11,12],[13,14,15])
arr2 = arr[2:]
print(arr)
print("\n")
print(arr2)
```

```python
import numpy as np
arr = np.array([1,2,3],[4,5,6],[7,8,9],[10,11,12],[13,14,15])
arr2 = arr[2:3]
print(arr)
print("\n")
print(arr2)
```

切片还可以包括省略号…，使选择元组的长度与数组的维度相同。如果在行位置使用省略号，它将返回包含行中元素的 ndarray

```python
import numpy as np
arr = np.array([[1,2,3],[4,5,6],[7,8,9],[10,11,12],[13,14,15]])
print(arr)
print("-----------")
print(arr[...,1])
print("-----------")
print(arr[1,...])
print("-----------")
print(arr[...,1:])
```
