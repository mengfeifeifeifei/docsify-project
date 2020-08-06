> 1.
## input
`input()返回的值是字符串，如果要进行比较，需要先int(x)转化一下再进行比较`

`print('hello,world', '123456')  结果 hello world 123456 .   逗号转化为空格`

`用户输入字符 input()   在交互模式下  >>> name = input() 输入字符之后，值存放到变量name中，此时输入name查看变量你内容`

`name = input('请输入名称')   输入zhang, 执行print('hello',name)  结果 hello zhang`

`python采用缩进方式，注释以#开头，大小写敏感`

## 数据变量和类型

`能够直接处理的数据类型 ： 整数、浮点数、字符串，如果在字符串内部想使用''和"",使用转义符\来标识`
```python
' I\'m \"OK\" '
  输出
  I'm "OK"
```
```
>>> print('I\'m learning\npython')     \n换行符
I'm learning
python
print('\\\n\\')      \ 需要转义符 \\ 来表示
\
\
```
`r''表示''内部的字符串默认不转义`
```python
>>> print('\\\t\\')
\   \
>>> priny(r'\\\t\\')
\\\t\\
```
`当有多个换行时，\n不好阅读时，可以用 '''...''' 来换行`
```python
>>> print('''ceshi1
...ceshi2
..."ceshi3"''')
```
## 变量：
`动态语言(变量本身类型不固定的语言)、静态语言(在定义时必须指定变量类型，如果赋值类型不匹配，就报错)`
```java
// java(静态语言)
int a = 123;    
a = 'ABC';   // 错误，不能把字符串赋值给整形变量
// python(动态语言)
a = 123  //整数
a = 'ABC'  // 变量a变为字符串 
```
## 格式化
`%运算符是格式化字符串的， %s表示用字符串替换， %d表示用整数替换，%f浮点数替换，%x十六进制整数替换，如果只有一个%?，括号可以省略`
```python
>>> 'Hello, %s' % 'world'
'Hello,world'
>>> 'Hi, %s, you have $%d' % ('mmmmmm'，100000)
'Hi,mmmmmm,you have $100000'
```

`%s 代表字符串的意思，也可以代表任何， %d 代表整数 当不知道使用什么的时候可以使用%s代替`
```python
>>> 'Hello,%s' % 'world'     
'Hello,world'
>>> 'Hi,%s, you have $%d' % ('MMMM',10000)    
'Hi,MMMM,you have $10000'
```
`和1的意义一样，写法不同，从{0},{1}...  {2:.1f}保留小数点后一位  {0:02d}是向前两位 例如8 变成08的意思`
```python
>>> 'Hello,{0}, my name is {1},score{2:.1f}' .format('zhang',123,89.5555541)
'Hello,zhang, my name is 123,score89.6'
>>> 'Hi,today{0:02d}月{1:02d}日' .format (8,5)
'Hi,today08月05日'
```
`.2f代表小数点后保留两位，  f''写法 r:.1f是小数点后保留一位`
```python
>>> r = (85-72)/72*100
print('提升了 %.2f %%' % r)       
print(f'提升了{r:.1f}%')         
```
## List
> 列表

**classmates = ['1','zhang','sunny'];  这就是一个list（有序集合）**

**len()函数获取元素个数  通过索引取值calssmates[0] 取最后一个元素classmates[2]或classmates[-1]**

> 追加元素

**追加元素默认到末尾 classmates.append('test')  追加到指定的位置 classmates.insert(1,'yes')**

**此时元素为[1,'yse','zhang','sunny','test']**

**删除元素 classmates.pop(i)， i为索引位置，当没有时，默认删除元素末尾**

> 修改元素

**直接赋值即可 classmates[1] = 'xxxxx';**

## touple
> 元祖(类似于list，但是初始化之后不能修改)

**classmates = ('111','222','333') 现在这个touple不能改变，取元素按照list方式 classmates[0]，但是不能修改，不能添加**

**定义一个元素的touple时，定义方法： t=(1,) 逗号必须要加 不然就会认为定义的1这个数**

**t = ('a','b',['1','2'])  t[2][0] = 'x' t[2][1] = 'y'  此时touple变为 ('a','b',['x','y']) 这个时候是可以改变的，因为变得不是touple的元素，变得是list的元素，它不可以指向其他的list**

## 条件判断
> if 

```python
if <条件判断1>:
    <执行1>
else if <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
```

## 循环
**range(1,101) 生成的是从1-100的一个数组 也可以这样写range(101)这是从0到100的数组**

**1.for x in range(101)  2.sum = 0 n=99 while n > 0 :xxxxxxx**

**break语句可以在循环过程中直接退出循环，continue跳过本次循环，开始下一轮循环，必须配合if语句使用**

## 函数
**定义函数的默认参数时，默认参数必须指向不便对象**

**调用app_end() 返回['END']，第二次调用返回['END','END'],依次类推。因为[]为可变，相当于改变了L指向的值。**
```python
def app_end(L = []):
    L.append('END')
    return L
```
**所以改为不变对象**
```python
def app_end(L=None):
    if L is None:
        L = []
    L.append('END')
    return L
```
> 可变参数

**可变参数在参数前加一个星号，可以传入任意参数，包括0个参数，传值也可以 同样也可以把传入的参数定义为可变参数传入 num = [1,2,3,4] calc(*num)**

```python
def calc(*number):
    sum = 0
    for n in number:
        sum = sum + n*n
    return sum
```
> 关键字参数

**关键字参数允许传入0或者任意个含参数名的参数，在函数内部自动组装为一个dict**

**调用 person('xxxx',18,xingbie='man')**

`a={'a':'x','b':'xx','c':'xxx','d':'xxxx'}  person('zhang',20,**a) 可以这样传值`
```python
def person(name,age,**sex):
    print('name:',name,'age:',age,'sex:',sex)
```
> 命名关键字参数

**限制关键字参数的名字，只接受city和job作为关键字参数('city':'xxxx','job':'xxxx')**
```python
def person(name,age,*,city,job):
    print(name,age,city,job)
```
