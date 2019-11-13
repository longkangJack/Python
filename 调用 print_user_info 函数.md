1.2 字符串

1、基本介绍

单引号 ' '或者双引号 " " 都可以，再或者 ''' ''' 三个引号，其中三个引号被用于过于长段的文字或者是说明，只要是三引号不完你就可以随意换行写下文字。

①字符串直接能相加，如：

```
str1 = 'hi'
str2 = 'hello'
print(str1 + str2)123
```

运行结果：

hi jaybo1

②字符串相乘，如：

string = 'bang!'
total = string * 3 12

打印 total 结果：

bang!bang!bang!

2、字符串的分片与索引

字符串可以通过 string[x] 的方式进行索引、分片。

字符串的分片实际可以看作是从字符串中找出来你要截取的东西，复制出来一小段你要的长度，存储在另一个地方，而不会对字符串这个源文件改动。分片获得的每个字符串可以看作是原字符串的一个副本。

先看下面这段代码：



name = 'My name is Mike'
print(name[0])
'M'
print(name[-4])
'M'
print(name[11:14]) # from 11th to 14th, 14th one is excluded
'Mik'
print(name[11:15]) # from 11th to 15th, 15th one is excluded
'Mike'
print(name[5:])
'me is Mike'
print(name[:5])
'My na'12345678910111213

如果感到困惑话，可以对照如下表格理解和分析：
两边分别代表着字符串的分割从哪里开始，并到哪里结束。

  以name[11:14]为例，截取的编号从第11个字符开始，到位置为14但不包含第14个字符结束。而像name[5:]这样的写法代表着从编号为5的字符到结束的字符串分片。相反，name[:5]则代表着从编号为0的字符开始到编号为5但包含第5个字符分片。可能容易搞混，可以想象成第一种是从5到最后面，程序员懒得数有多少个所以就省略地写，第二种是从最前面到5，同样懒得写0，所以就写成了[:5]。
3、字符串的方法 


replace 方法：第一个参数表示被替代部分，第二个参数表示替代成怎样的字符串。
字符串填空，如：

city = input("write the name of city:"")
url = "http://apistore.baidu.com/mri.../weather?citypiny={}.format(city)12


4、问题

问题1：



num = 1
string = '1'
print(num + string)123

上面代码将出错？

解释：整数型不能和字符串直接相加。可以先把该字符串转为整数型，再相加，即 int(string) 



num = 1
string = '1'
print(num + int(string))123



二、函数

举些你可能已经使用过的函数例子：



判断数据类型：type(str) 
字符串类型数据转为整数型：int(str)
...123

通过观察规律不难发现，Python 中所谓的使用函数就是把你要处理的对象放到一个名字后面的括号就可以了。简单的来说，函数就是这么使用，可以往里面塞东西得到处理结果。这样的函数在 Python 中还有这些：



以 Python3.5 版本为例，一个有 68 个这样的函数，它们被称为内建函数。这里內建的是指这些函数为安装好了 Python 就可以使用。



2.1 函数格式

定义函数的格式：



其中，def 和 return 为关键字。

注意： 函数缩进后面的语句被称为是语句块，缩进是为了表名语句的逻辑与从属关系。缩进这个问题不能忽视，否则会导致代码无法成功运行，这里需要特别注意。



2.2 函数参数

①位置参数，举例，看代码：



def trapezoid_area(base_up, base_down, height):
    return 1/2 * (base_up + base_down) * height12

接下来我们开始调用该函数：



trapezoid_area(1,2,3)1

不难看出，填入的参数1，2，3分别对应着参数 base_up，base_down 和 height。这种传入参数的方式被称作为位置参数。

②关键词参数：在函数调用的时候，将每个参数名称后面赋予一个我们想要传入的值，如调用 fun1 函数时候：fun1(a=1, b=2, c=3)。

看下图：




第一行的函数参数按照反序传入，因为是关键词参数，所以并不影响函数正常运作；
第二行的函数参数反序传入，但是到了第三个却变成了位置函数，遗憾的是这种方式是错误的语法，因为如果按照位置来传入，最后一个应该是参数 height 的位置。但是前面 height 已经按照名称传入了值3，所以是冲突的。
第三行的函数参数正序传入，前两个是以关键字的方式传入，最后一个以位置参数传入，但是位置参数不能再关键词参数后面，所以是错误的。
第四行的函数参数正序传入，前两个是以位置的方式传入，最后一个以关键字参数传入，这个函数是可以正常运行的。


③不定长参数

有时我们在设计函数接口的时候，可会需要可变长的参数。也就是说，我们事先无法确定传入的参数个数。

Python 提供了一种元组的方式来接受没有直接定义的参数。这种方式在参数前边加星号 * 。如果在函数调用时没有指定参数，它就是一个空元组。我们也可以不向函数传递未命名的变量。例如：



def print_user_info( name ,  age  , sex = '男' , * hobby):
    # 打印用户信息
    print('昵称：{}'.format(name) , end = ' ')
    print('年龄：{}'.format(age) , end = ' ')
    print('性别：{}'.format(sex) ,end = ' ' )
    print('爱好：{}'.format(hobby))
    return;

# 调用 print_user_info 函数
print_user_info( '小明' , 25, '男', '打篮球','打羽毛球','跑步')12345678910

输出的结果：



昵称：小明 年龄：25 性别：男 爱好：('打篮球', '打羽毛球', '跑步')1

通过输出的结果可以知道，* hobby 是可变参数，且 hobby 其实就是一个 tuple （元祖）。

可变长参数也支持关键参数，没有被定义的关键参数会被放到一个字典里。这种方式即是在参数前边加 **，更改上面的示例如下：



def print_user_info( name ,  age  , sex = '男' , ** hobby ):
    # 打印用户信息
    print('昵称：{}'.format(name) , end = ' ')
    print('年龄：{}'.format(age) , end = ' ')
    print('性别：{}'.format(sex) ,end = ' ' )
    print('爱好：{}'.format(hobby))
    return;

# 调用 print_user_info 函数
print_user_info( name = '小明' , age = 25 , sex = '男', hobby = ('打篮球','打羽毛球','跑步'))12345678910

输出的结果：



昵称：小明 年龄：24 性别：男 爱好：{'hobby': ('打篮球', '打羽毛球', '跑步')}1

通过对比上面的例子和这个例子，可以知道，* hobby 是可变参数，且 hobby 其实就是一个 tuple （元祖），** hobby是关键字参数，且 hobby 就是一个 dict （字典）。

④ 只接受关键字参数

关键字参数使用起来简单，不容易参数出错，那么有些时候，我们定义的函数希望某些参数强制使用关键字参数传递，这时候该怎么办呢？将强制关键字参数放到某个*参数或者单个*后面就能达到这种效果,比如：



def print_user_info( name , *, age, sex = '男' ):
    # 打印用户信息
    print('昵称：{}'.format(name) , end = ' ')
    print('年龄：{}'.format(age) , end = ' ')
    print('性别：{}'.format(sex))
    return;

# 调用 print_user_info 函数
print_user_info( name = '小明' ,age = 25 , sex = '男' )

# 这种写法会报错，因为 age ，sex 这两个参数强制使用关键字参数
#print_user_info( '小明' , 25 , '男' )
print_user_info('小明',age='22',sex='男')12345678910111213

通过例子可以看，如果 age , sex 不适用关键字参数是会报错的。



2.3 匿名函数

有没有想过定义一个很短的回调函数，但又不想用 def 的形式去写一个那么长的函数，那么有没有快捷方式呢？

——答案是有的。 
Python 使用 lambda 来创建匿名函数，也就是不再使用 def 语句这样标准的形式定义一个函数。

匿名函数主要有以下特点：


lambda 只是一个表达式，函数体比 def 简单很多。
lambda 的主体是一个表达式，而不是一个代码块。仅仅能在 lambda 表达式中封装有限的逻辑进去。
lambda 函数拥有自己的命名空间，且不能访问自有参数列表之外或全局命名空间里的参数。


基本语法：lambda [arg1 [,arg2,.....argn]]:expression

示例：



sum = lambda num1 , num2 : num1 + num2;
print( sum( 1 , 2 ) )12

输出的结果： 3

注意：尽管 lambda 表达式允许你定义简单函数，但是它的使用是有限制的。 你只能指定单个表达式，它的值就是最后的返回值。也就是说不能包含其他的语言特性了， 包括多个语句、条件表达式、迭代以及异常处理等等。 

匿名函数中，有一个特别需要注意的问题，比如，把上面的例子改一下：



num2 = 100
sum1 = lambda num1 : num1 + num2 ;

num2 = 10000
sum2 = lambda num1 : num1 + num2 ;

print( sum1( 1 ) )
print( sum2( 1 ) )12345678

你会认为输出什么呢？第一个输出是 101，第二个是 10001，结果不是的，输出的结果是这样：



10001
1000112

这主要在于 lambda 表达式中的 num2 是一个自由变量，在运行时绑定值，而不是定义时就绑定，这跟函数的默认值参数定义是不同的。所以建议还是遇到这种情况还是使用第一种解法。



三、循环与判断



3.1 布尔表达式和判断

Python 中的布尔类型值：True 和 Flase  其中，注意这两个都是首字母大写。

但凡能够产生一个布尔值的表达式为布尔表达式：



1 > 2 # False
1 < 2 <3 # True
42 != '42' # True
'Name' == 'name' # False
'M' in 'Magic' # True
number = 12
number is 12 # True1234567


  注1：不同类型的对象不能使用<、>、<=、=>进行比较，却可以使用==和!=。

  注2：浮点类型和整数类型虽然是不同类型，但不影响比较运算。还有，不等于!= 可以写作<> 。


话说，布尔类型可以比较吗？如：True > Flase，回答是可以的，Ture 和 Flase 对于计算机就像是 1 和 0 一样，所以结果是真，即True。



3.2 条件控制

定义格式：



用一句话该结构作用：如果…条件是成立的，就做…；反之，就做…


  所谓条件成立，指的是返回值为True的布尔表达式。 




3.3 循环

①for 循环



把 for 循环所的事情概括成一句话就是：于…其中的每一个元素，做…事情。 

打印九九乘法表：



for i in range(1, 10):
    for j in range(1, i+1):
        print('{}x{}={}\t'.format(i, j, i*j), end='')
    print()1234

运行结果：



1x1=1
2x1=2   2x2=4
3x1=3   3x2=6   3x3=9
4x1=4   4x2=8   4x3=12  4x4=16
5x1=5   5x2=10  5x3=15  5x4=20  5x5=25
6x1=6   6x2=12  6x3=18  6x4=24  6x5=30  6x6=36
7x1=7   7x2=14  7x3=21  7x4=28  7x5=35  7x6=42  7x7=49
8x1=8   8x2=16  8x3=24  8x4=32  8x5=40  8x6=48  8x7=56  8x8=64
9x1=9   9x2=18  9x3=27  9x4=36  9x5=45  9x6=54  9x7=63  9x8=72  9x9=81123456789

②while 循环 



总结：只要…条件一成立，就一直做…

在循环过程中，可以使用 break 跳过循环，使用 continue 跳过该次循环。

在 Python 的 while 循环中，可以使用 else 语句，while … else 在循环条件为 false 时执行 else 语句块。如：



count = 0
while count < 3:
   print (count)
   count = count + 1
else:
   print (count)123456

运行结果：



0
1
2
31234

有 while … else 语句，当然也有 for … else 语句，for 中的语句和普通的没有区别，else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行，while … else 也是一样。如：



for num in range(10,20):  # 迭代 10 到 20 之间的数字
   for i in range(2,num): # 根据因子迭代
      if num%i == 0:      # 确定第一个因子
         j=num/i          # 计算第二个因子
         print ('%d 是一个合数' % num)
         break            # 跳出当前循环
   else:                  # 循环的 else 部分
      print ('%d 是一个质数' % num)12345678

运行结果：



10 是一个合数
11 是一个质数
12 是一个合数
13 是一个质数
14 是一个合数
15 是一个合数
16 是一个合数
17 是一个质数
18 是一个合数
19 是一个质数12345678910



四、数据结构

Python 有四种数据结构，分别是：列表、字典、元组、集合。我们先从整体上认识一下这四种数据结构：



list = [val1,val2,val3,val4] #列表
dict = {key1:val1,key2:val2} #字典
tuple = (val1,val2,val3,val4) #元组
set = {val1,val2,val3,val4} #集合1234



4.1 列表（List）


列表中的每个元素都是可变的；
列表中的元素是有序的，也就是说每个元素都有一个位置；
列表中可以容纳 Python 中的任何对象。如下：

all_in_list = [
   1, #整数
   1.0, #浮点数
   'a word', #字符串
   print(1), #函数
   True, #布尔值
   [1,2], #列表中套列表
   (1,2), #元祖
   {'key':'value'} #字典
]12345678910


另外，对于数据的操作，最常见的为增删改查。在此就省略了，网上找下相应函数练习下即可。



4.2 字典（Dict）


字典中数据必须是以键值对的形式出现的；
逻辑上讲，键是不能重复的；
字典中的键（key）是不可变的，也就是无法修改的，而值（value）是可变的，可修改的，可以是任何对象。

下面是个例子：

NASDAQ_code = {
   'BIDU':'Baidu',
   'SINA':'Sina',
   'YOKU':'Youku'
}12345


一个字典中键与值并不能脱离对方而存在，如果你写成了 {'BIDU':} 会引发一个语法错误：invalid syntax。

如果试着将一个可变（mutable）的元素作为 key 来构建字典，比如列表：key_test = {[]:'a Test'} ，则会报一个错：unhashable type:'list'。

同时字典中的键值不会重复，即便你这么做，相同的键值也只能出现一次：a = {'key':123,'key':123} 。

增删改查操作，在此省略了。

备注：


列表中用来添加多个元素的方法为extend，在字典中添加多个元素的方法为update()  
字典是不能切片的，即这样的写法是错误的：chart[1:4]  




4.3 元组（Tuple）

元组可以理解为一个稳固版的列表，因为元组是不可以修改的，因此在列表中的存在的方法均不可以使用在元组上，但是元组是可以被查看索引的，方式和列表一样。



letters = ('a, 'b', 'c', 'd')
letters[0]12

相关的操作找代码练习下即可。



4.4 集合（Set）

集合则更接近数学上集合的概念。每一个集合中是的元素是无序的、不重复的任意对象，我们可以通过集合去判断数据的从属关系，有时还可以通过集合把数据结构中重复的元素减掉。

集合不能被切片也不能被索引，除了做集合运算之外，集合元素可以被添加还有删除：



a_set = {1,2,3,4}
a_set.add(5)
a_set.discard(5)123



4.5 数据结构的一些技巧



4.5.1 多重循环

如下：



代码演示：



for a, b in zip(num, str):
    print(b, 'is', a)12



4.5.2 推导式

列表推导式的用法很好理解，可以简单地看成两部分。如下图：




  红色虚线后面的是我们熟悉的 for 循环的表达式，而虚线前面的可以认为是我们想要放在列表中的元素。


代码演示：



a = []
for i in range(1, 11):
    a.append(i)123

可以换成列表解析的方式来写：



b = [i for in i range(1, 11)]1

列表解析式不仅方便，并且在执行效率上要远远胜过前者。



五、类的理解



5.1 类的介绍

类的定义：



class CocaCola:
    formula = ['caffeine','sugar','water','soda']12

使用 class 来定义一个类，就如同创建函数时使用的 def 定义一个函数一样简单。如上你可以看到定义了名为 CocaCola 的类，接着在缩进的地方有一个装载着列表的变量的 formula，这个在类里面定义的变量就是类的变量，而类的变量有一个专有的术语，我们称之为类的属性。

类的属性：


类变量
方法


①类的实例化：



coke_for_me = CocaCola()
coke_for_you = CocaCola()12

②类变量属性的引用：CocaCola.formula、coke_for_me.formula

类方法的使用：



class CocaCola:
    formula = ['caffeine','sugar','water','soda']
    def drink(self):
        print('Energy!')
coke = CocaCola()
coke.drink()123456

结果：



Energy!1



5.2 self

我想很多人会有关注到这个奇怪的地方——似乎没有派上任何用场的self参数。我们来说明下原理，其实很简单，我们修改下上面的代码：



class CocaCola:
    formula = ['caffeine','sugar','water','soda']
    def drink(coke):    # 把self改为coke
        print('Energy!')
coke = CocaCola()
coke.drink()123456

结果：



Energy!1

怎么样，有些头绪了吧！这个参数其实就是被创建的实例本身。也就是将一个个对象作为参数放入函数括号内，再进一步说，一旦一个类被实例化，那么我们其实可以使用和与我们使用函数相似的方式：



coke = CocaCola
coke.drink() == CocaCola.drink(coke) #左右两边的写法完全一致12

被实例化的对象会被编译器默默地传入后面方法的括号中，作为第一个参数。上面两个方法是一样的，但我们更多地会写成前面那种形式。其实self这个参数名称是可以随意修改的（编译器并不会因此而报错）。

和函数一样，类的方法也能有属于自己的参数，如下：



class CocaCola:
    formula = ['caffeine','sugar','water','soda']
    def drink(self,how_much):

    if how_much == 'a sip':
        print('Cool~')
    elif how_much == 'whole bottle’:
        print('Headache!')
ice_coke = CocaCola()
ice_coke.drink('a sip')12345678910

结果：



Cool~1



5.3 魔术方法

Python 的类中存在一些方法，被称为「魔术方法」，_init_()就是其中之一。



class CocaCola():
    formula = ['caffeine','sugar','water','soda']
    def __init__(self):
        self.local_logo = '可口可乐'
    def drink(self): 
        print('Energy!')
coke = CocaCola()
print(coke.local_logo)12345678

作用：在创建实例之前，它做了很多事情。说直白点，意味着即使你在创建实例的时候不去引用 init_() 方法，其中的语句也会先被自动的执行。这给类的使用提供了极大的灵活性。 



class CocaCola:
    formula = ['caffeine','sugar','water','soda']
    def __init__(self,logo_name):
        self.local_logo = logo_name
    def drink(self):
        print('Energy!')
coke = CocaCola('ݢݗݢԔ')
coke.local_logo
>>> 可口可乐123456789

有过面向对象编程经验很好理解了，也就是很多面向对象语言中的「构造函数」。



5.4 类的继承

如下代码：



class CaffeineFree(CocaCola):
    caffeine = 0
    ingredients = [
        'High Fructose Corn Syrup',
        'Carbonated Water',
        'Phosphoric Acid',
        'Natural Flavors',
        'Caramel Color',
    ]
coke_a = CaffeineFree('Cocacola-FREE')
coke_a.drink()1234567891011

表示 CaffeineFree 继承了 CocaCola 类。

类中的变量和方法可以被子类继承，但如需有特殊的改动也可以进行覆盖。 

Q1：类属性如果被重新赋值，是否会影响到类属性的引用？



class TestA():
    attr = 1
obj_a = TestA()

TestA.attr = 24
print(obj_a.attr)

>>> 结果：2412345678


  A1：会影响。


Q2：实例属性如果被重新赋值，是否会影响到类属性的引用？



class TestA:
    attr = 1
obj_a = TestA()
obj_b = TestA()

obj_a.attr = 42
print(obj_b.attr)

>>> 结果：1123456789


  A2：不会影响。


Q3：类属性实例属性具有相同的名称，那么.后面引用的将会是什么？



class TestA():
    attr =1
    def __init__(self):
        self.attr = 24

obj_a = TestA()

print(obj_a.attr)

>>> 结果：2412345678910


  A3：类属性赋值后的值。


总结：如图所示，Python 中属性的引用机制是自外而内的，当你创建了一个实例之后，准备开始引用属性，这时候编译器会先搜索该实例是否拥有该属性，如果有，则引用；如果没有，将搜索这个实例所属的类是否有这个属性，如果有，则引用，没有那就只能报错了。
