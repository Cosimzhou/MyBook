Python note
===========


# §语法糖
## 拆包
```
>>> a, *b = 1,2,3
>>> a, b
1, [2, 3]
>>> a, *b, c = 1,2,3,4,5
>>> a, b, c
1, [2, 3, 4], 5
```

## 数据结构推导
```
set = {i*2 for i in set1}
dict = {k:2*k for k in range(5)}
array = [v*5 for v in range(10)]
```

## 复制列表
```
>>> nums[::]
```

## 复制反转列表
```
>>> nums[::-1]    # 注意区别nums.reverse()
```

## 合并字典
```
>>> z = {**dict1, **dict2} # dict3.update(dict1); dict3.update(dict2) = only python3
```

## 生成器
```
>>> (i**2 for i in range(5))
<generator object <genexpr> at 0x10881e518>
```

## 使用yield from
```
def dup(n):
    for i in range(n):
    yield from [i, i]

for i in dup(3):
    print(i)
```

## for…else
```
for item in container:
  if search_something(item):
    process(item) # Found it!
    break
else:
  # Didn't find anything..
  #没有被break的完整循环
  not_found_in_container()
```

# 默认字典 defaultdict
```
>>> from collections import defaultdict
>>> d = defaultdict(list)
>>> d["nums"]
```

# §利用property制作对象的属性
```
class C:
　def __init__(self):
　　self.__x=None
　@property
　def x(self):
　　return self.__x
　@x.setter
　def x(self,value):
　　self.__x=value
　@x.deleter
　def x(self):
　　del self.__x
　#同一属性的三个函数名要相同哦。。
```

# §装饰器
```
def deco(func):
    def    wrapper(*args, **kwargs):
        pass    #TODO
        func (*args, **kwargs)
        pass    #TODO
    return    wrapper    ##

@deco
@deco1
def    func(a,b,c):
    pass
#装饰器的执行顺序是栈式的，FILO
```

类装饰器：
```
class C:
    @staticmethod
    def aa(f):
        def wrapper(*args,**kwargs):
            return f(*args,**kwargs)
        return wrapper
class B():
    @C.aa
    def test(self):
        print "aaa"

b = B()
b.test()
```

# §基本数据结构

```
import heapq
heapq. heappush(arr, val)
         heappop(arr)
heapify(arr)
merge(arr1,arr2)


from collections import Counter, defaultdict
points_dict = Counter("google")
# points_dict： {'o': 2, 'g': 2, 'e': 1, 'l': 1}
```

```
import queue

q = queue.Queue()
q.put(1)
q.put(3)
while not q.empty():
  print(q.get())
# output: 1, 3
```



python3 -m http.server
python -m SimpleHTTPServer

python -m pip --version
python -m pip install xxxx # pip install xxxx



# §系统操作
shutil.copy(src, dest)
shutil.copytree(src, dest)

os.getenv()        #读取环境变量
os.putenv()        #设置环境变量
os.getcwd()     #得到当前工作目录，即当前Python脚本工作的目录路径
os.system(cmd)    #运行系统命令
os.popen(cmd)    #运行系统命令并将标准输出的结果返回
os.startfile(file)    #用系统方式打开文件(WIN)
subprocess.call(["open", "/Users/cosim/tmp/service.png"]) #用系统方式打开文件(POSIX)
os.listdir(dir)        #返回指定目录下的所有文件和目录名
os.rename(old, new)    #重命名
os.remove(file)      #函数用来删除一个文件
os.removedirs()     #删除多个目录
os.mkdir(path)        #创建单个目录
os.makedirs(r"c:\python\test")        #创建多级目录
os.chmod(file)        #修改文件权限与时间戳
os.exit()            #终止当前进程
os.stat(file)        #统计文件信息

os.path.join(.....) #文件路径拼接
os.path.exists(spath)    #是否存在
os.path.isfile(spath)            #是否是文件
os.path.isdir(spath)            #是否是目录
os.path.isabs(spath)        #是否是绝对路径
os.path.split(spath)        #返回一个路径的目录名和文件名: eg os.path.split('/home/swaroop/byte/code/poem.txt') 结果：('/home/swaroop/byte/code', 'poem.txt')
os.path.splitext(spath)        #分离扩展名：（“前面的部分”，“后缀”）
os.path.dirname(spath)        #获取路径名：去掉spath中的文件名
os.path.basename(spath)        #获取文件名：去掉spath中的前端路径。文件时仅文件名；目录时仅目录名
os.path.getsize(filename)     #获取文件大小
os.path.expanduser(pathname)    #展开’~’路径
os.linesep        #给出当前平台使用的行终止符: Windows使用'\r\n'，Linux使用'\n'而Mac使用'\r'
os.name         #指示你正在使用的平台： 对于Windows，它是'nt'，而对于Linux/Unix用户，它是'posix'

# 目录遍历
```
for parent, dirnames, filenames in os.walk(rootdir):
  for d in dirnames:
    pass
  for f in filenames:
    pass
```


# §内置函数

| 选项 [options] | 含义          |
| -------------- | ------------- |
| `all(iter)`                   | 全部为true，返回true |
| `any(iter)`                   | 任何一个为true，返回true |
| `zip(a,b) `                   | 压缩 |
| `zip(*a)`                     | 解压 |
| `id(obj)`                     | 变量指针 |
| `enumerate()`                 | 遍历数组，为元素增加下标 |
| `slice(s,e,i)`                | 切片范围 |
| `hash(v)`                     | 哈希值 |
| `globals()`                   | 全局名字字典 |
| `locals()`                    | 本地名字字典 |
| `callable(v)`                 | 是否可被调用 |
| `hasattr(obj, 'attr')`        | 对象是否拥有属性，(性能比较差) |
| `getattr(obj, 'attr', [def])` | 获取对象的属性，不存在的属性会抛异常 |
| `setattr(a, 'bar', 5)`        |  |

| 选项 [options] | 含义          |
| -------------- | ------------- |
| `unichr(97)` | |
| `unicode('')` | |
| `type(1)` | |
| `divmod(8, 2)` | |
| `cmp(a, b)` | |
| `open('test.txt')` | |
| `isinstance(A(), A)` | |
| `issubclass(B, A)` | |
| `reduce(lambda x, y: x+y, [1,2,3,4,5])` | |
| `map(lambda x, y: x + y, [1, 3, 5, 7, 9], [2, 4, 6, 8, 10])` | |
| `filter(is_odd, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])` | |

| 选项 [options] | 含义          |
| -------------- | ------------- |
| `set('google')` |  |
| `frozenset(range(10))` |  |
| `dict()` |  |
| `tuple({1:2, 3:4})` |  |
| `list(aTuple)` |  |

`basestring()` 方法是 str 和 unicode 的超类（父类），也是抽象类，因此不能被调用和实例化，但可以被用来判断一个对象是否为 str 或者 unicode 的实例，isinstance(obj, basestring) 等价于 isinstance(obj, (str, unicode))。

# §引包及包的安装

将固定的包路径加入`*.pth`文件中

# 显示python的路径
```bash
python -c "import os; print os.__file__"
python -c "import sys; print sys.executable"    = which python
python -c "from distutils.sysconfig import get_python_lib; print get_python_lib()"
```

# 离线安装
```bash
pip install numpy-1.15.0-cp27-cp27mu-manylinux1_x86_64.whl
```

#安装至指定目录
```bash
pip install --install-option="--prefix=绝对路径" packageName
```

# §文件的读写

## CSV & JSON

import csv

### 序号方式读写CSV
```
with open('some.csv', 'rb') as f:        # 采用b的方式处理可以省去很多问题
    for row in csv.reader(f):
        # do something with row, such as row[0],row[1]

with open('some.csv', 'wb') as f:      # 采用b的方式处理可以省去很多问题
    csv.writer(f).writerows(someiterable)
```

### 字典方式读写CSV
```
with open('names.csv') as csvfile:
    for row in csv.DictReader(csvfile):
        print(row['first_name'], row['last_name'])

with open('names.csv', 'w') as csvfile:
    fieldnames = ['first_name', 'last_name']
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

    writer.writeheader()
    writer.writerow({'first_name': 'Baked', 'last_name': 'Beans'})
    writer.writerow({'first_name': 'Lovely', 'last_name': 'Spam'})
    writer.writerow({'first_name': 'Wonderful', 'last_name': 'Spam’})
```

## JSON
### 文本版本Json
```
import json
Obj = json.loads('{}')
txt = json.dumps(obj,  separators=(',', ':')) # 无分隔的空格
```
### 文件版本Json
```
obj=json.load(pFile)
json.dump(obj, pFile)
```

## PDF

```
from PyPDF2 import PdfFileReader, PdfFileWriter

pdf_input = PdfFileReader(open('pdf路径', 'rb'))     #获取一个pdf对象
page_count = pdf_input.getNumPages()                 #获取pdf页数
page = pdf_input.getPage(3)                          #获取pdf第四页的内容
page['/Contents']

pdf_output = PdfFileWriter()                         #获取一个pdfWriter对象
pdf_output.addPage(page)                             # 将一个PageObject加入到PdfFileWriter中

pdf_output.write(open('新pdf路径','wb'))             #把新pdf保存
```



# §格式化时间
datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')

# §正则表达
```
ptn = re.compile('/@([a-z]+)@')
m = ptn.match(word) #从开头匹配
print m.groups()[0]
m = ptn.search(sentence) #全句匹配
print m.groups()[0]
```

# § runtime
```
def _cmd(): #可以打印当前函数的名称
  return sys._getframe(1).f_code.co_name

sys._getframe(1).f_globals

class A:pass
a=A()
A.__name__ # = "A"
a.__class__.__name__ # = "A"
```

# §多线程
import threading
#首先导入threading 模块，这是使用多线程的前提。
t = threading.Thread(target=func, args=(,))
t.setDaemon(True)
t.start()

# 真多线程并行处理
import multiprocess
t = multiprocess.Process(target=func, args=(,))
t.start()
t.join()

# §互斥锁
mutex=threading.Lock()
mutex.acquire([blocking])    #里面可以加blocking(等待的时间)或者不加，不加就会一直等待（堵塞）
mutex.release()

threading.RLock() #可重入锁


# §读写二进制
```
bytes=struct.pack('5s6sif',a,b,c,d)
a,b,c,d=struct.unpack('5s6sif',bytes)
```
format列表，ctype表示可以与python中的类型一一对应。

| Format | C Type | Python | 字节数 |
| ------ | ------ | ------ | ------ |
| x | pad byte | no value | 1 |
| c | char | string of length 1 | 1 |
| b | signed char | integer | 1 |
| B | unsigned char | integer | 1 |
| ? | Bool | bool | 1 |
| h | short | integer | 2 |
| H | unsigned short | integer | 2 |
| i | int | integer | 4 |
| I | unsigned int | integer or long | 4 |
| l | long | integer | 4 |
| L | unsigned long | long | 4 |
| q | long long | long | 8 |
| Q | unsigned long long | long | 8 |
| f | float  | float | 4 |
| d | double |  float | 8 |
| s | char[] |  string | 1 |
| p | char[] |  string | 1 |
| P | void * |  long | |

最后一个可以用来表示指针类型的，占4个字节
为了同c中的结构体交换数据，还要考虑有的c或c++编译器使用了字节对齐，通常是以4个字节为单位的32位系统，故而还提供了

| Character | Byte order | Size and alignment |
| --------- | ---------- | ------------------ |
| @ | native | native            凑够4个字节|
| = | native | standard        按原字节数|
| < | little-endian | standard        按原字节数|
| > | big-endian | standard       按原字节数|
| ! |  network (= big-endian) | standard       按原字节数|






# §用变量名替换
```
def varlist():
  locals = sys._getframe(1).f_locals
  globals = sys._getframe(1).f_globals
  locals.update(globals)
  return locals
print "$(variablename)s ..." % varlist()
```

# §类型判断
```
if type([]) in [dict, tuple, list, string]:     # type([]) is list  or  type([]) == list:
    print 'good'
if  isinstance([], list):
    print ‘good'

type([]) := <type 'list'>
type(()) := <type 'tuple'>
type('') := <type 'str'>
type({}) := <type 'dict'>
type(1) := <type 'int'>
type(1.) := <type 'float'>
type(set()) := <type 'set'>
type(a) := <type 'classobj’>
type(u'') := <type 'unicode'>
```


# §遍历属性
```
def config2dict(cfg):
   config={}
   for key in cfg.__dict__:
       config[key] = cfg.__dict__[key]
   return config
```


__slots__
用于限定类成员内容；当类的成员变量与slots中的变量同名时，该变量为只读常量

# §可重载的运算符
基本定制
C.__init__(self[, arg1, ...]) 构造器（带一些可选的参数）
C.__new__(self[, arg1, ...]) 构造器（带一些可选的参数）；通常用在设置不变数据类型的子类
C.__del__(self) 解构器
C.__str__(self) 可打印的字符输出；内建str()及print 语句
C.__repr__(self) 运行时的字符串输出；内建repr() ‘‘ 和 操作符
C.__unicode__(self)b Unicode 字符串输出；内建unicode()
C.__call__(self, *args) 表示可调用的实例
C.__nonzero__(self) 为object 定义False 值；内建bool() （从2.2 版开始）
C.__len__(self)  长度（可用于类）；内建len()

对象值比较
C.__cmp__(self, obj) 对象比较；内建cmp()
C.__lt__(self, obj) and 小于/小于或等于；对应<及<=操作符
C.__le__(self,obj)
C.__gt__(self, obj) and 大于/大于或等于；对应>及>=操作符
C.__ge__(self,obj)
C.__eq__(self, obj) and 等于/不等于；对应==,!=及<>操作符
C.__ne__(self,obj)

属性操作
C.__getattr__(self, attr) 获取属性；内建getattr()；仅当属性没有找到时调用
C.__setattr__(self, attr, val) 设置属性
C.__delattr__(self, attr) 删除属性
C.__getattribute__(self, attr) 获取属性；内建getattr()；总是被调用
C.__get__(self, attr) （描述符）获取属性
C.__set__(self, attr, val) （描述符）设置属性
C.__delete__(self, attr) （描述符）删除属性

数值及二进制
C.__add__(self, obj) 加；+操作符
C.__sub__(self, obj) 减；-操作符
C.__mul__(self, obj) 乘；*操作符
C.__div__(self, obj) 除；/操作符
C.__truediv__(self, obj) True 除；/操作符
C.__floordiv__(self, obj) Floor 除；//操作符
C.__mod__(self, obj) 取模/取余；%操作符
C.__divmod__(self, obj) 除和取模；内建divmod()
C.__pow__(self, obj[, mod]) 乘幂；内建pow();**操作符
C.__lshift__(self, obj) 左移位；<<操作符

二进制
C.__rshift__(self, obj) 右移；>>操作符
C.__and__(self, obj) 按位与；&操作符
C.__or__(self, obj) 按位或；|操作符
C.__xor__(self, obj) 按位与或；^操作符
一元
C.__neg__(self) 一元负
C.__pos__(self) 一元正
C.__abs__(self) 绝对值；内建abs()
C.__invert__(self) 按位求反；~操作符

数值转换
C.__complex__(self, com) 转为complex(复数);内建complex()
C.__int__(self) 转为int;内建int()
C.__long__(self) 转为long；内建long()
C.__float__(self) 转为float；内建float()

其他
C.__oct__(self) 八进制表示；内建oct()
C.__hex__(self) 十六进制表示；内建hex()
C.__coerce__(self, num) 压缩成同样的数值类型；内建coerce()
C.__index__(self)g 在有必要时,压缩可选的数值类型为整型（比如：用于切片索引等等

序列
C.__len__(self) 序列中项的数目
C.__getitem__(self, ind) 得到单个序列元素
C.__setitem__(self, ind,val) 设置单个序列元素
C.__delitem__(self, ind) 删除单个序列元素

C.__getslice__(self, ind1,ind2) 得到序列片断
C.__setslice__(self, i1, i2,val) 设置序列片断
C.__delslice__(self, ind1,ind2) 删除序列片断
C.__contains__(self, val) f 测试序列成员；内建in 关键字
C.__*add__(self,obj) 串连；+操作符
C.__*mul__(self,obj) 重复；*操作符
C.__iter__(self) 创建迭代类；内建iter()

映射
C.__len__(self) mapping 中的项的数目
C.__hash__(self) 散列(hash)函数值
C.__getitem__(self,key) 得到给定键(key)的值
C.__setitem__(self,key,val) 设置给定键(key)的值
C.__delitem__(self,key) 删除给定键(key)的值
C.__missing__(self,key) 给定键如果不存在字典中，则提供一个默认值

以双下划线：“__”开头的变量是私有的，不允许外部访问，但以双下划线：“__”结尾的解除私有，可以被外部访问

__all__ = [‘’…]    #模块白名单
__dict__             #类对象名字表
__slots__            #类对象名字槽，类对象一但被创建就，结构就不可修改
__name__         #被执行引入时的名称


# §利用socket发送请求
import socket


特征
TCP
socket默认初始
需要通过accept/connect构造connection对象
通过connection对象调用send/recv方法实现收发数据
UDP
socket默认初始参数socket.AF_INET, socket.SOCK_DGRAM
直接通过socket对象使用sendto/recvfrom实现收发数据
Server
通过bind绑定IP和端口
首先使用recv*进行接收数据
Client
首先使用send*进行发送数据



示例：
Ip_port = ('127.0.0.1', 31500)


Server
Client
TCP
s = socket.socket()
s.bind(ip_port)
s.listen(10)                # queue length
conn = sk.accept()
conn.recv(1024)         # buffer length
s.close()
s = socket.socket()
conn = s.connect(ip_port)
conn.send(msg)
s.close()
UDP
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.bind(Ip_port)

data, addr = s.recvfrom(2048)    # buffer length
if not data: print "client has exist"
s.close()
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.sendto(msg, Ip_port)
s.close()


# UDP Server
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.bind(Ip_port)

data, addr = s.recvfrom(2048)    # buffer length
if not data: print "client has exist"
s.close()

#------------------------
# UDP client
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.sendto(msg, Ip_port)
s.close()


#----------------------------------------------------------------------
# TCP server
sk = socket.socket()
sk.bind(ip_port)
sk.listen(10)         # queue length
conn = sk.accept()
conn.recv(1024)    # buffer length
sk.close()

#------------------------
# TCP client
sk = socket.socket()
conn = sk.connect(ip_port)
conn.send(msg)
sk.close()






# §流
sys.stdout
sys.stdin
sys.stderr

# §遍历字典
dict={"a":"apple","b":"banana","o":"orange"}

print "##########dict######################"
for i in dict:
     print "dict[%s]=" % i,dict[i]

print "###########items#####################"
for (k,v) in dict.items():
     print "dict[%s]=" % k,v

print "###########iteritems#################"
for k,v in dict.iteritems():
     print "dict[%s]=" % k,v

print "###########iterkeys,itervalues#######"
for k,v in zip(dict.iterkeys(),dict.itervalues()):
     print "dict[%s]=" % k,v

# §占位符格式
3.800000E+01 %08E
38.000000 %08F
00000038 %08G
00000026 %08X
             & %08c
00000038 %08d
3.800000e+01 %08e
38.000000 %08f
00000038 %08g
00000038 %08i
00000046 %08o
            38 %08r
            38 %08s
00000038 %08u
00000026 %08x


# §柯里化
柯里化：参数分步喂给式
def curry(fn, k=None):
    k = k or fn.__code__.co_argcount
    def p(*a):
        l = len(a)
        if l == k:
            return fn(*a)
        elif l < k:
            return curry(lambda *b: fn(*(a + b)), k - l)
        elif l > k:
            raise TypeError('too many arguments', a)
    return p


@curry
def fun(x, y, z):
    return x + y + z


print(fun(1)(2)(3))
print(fun(1, 2)(3))
print(fun(1, 2, 3))
print(fun(1))
print(fun(1, 2))
print(fun(1, 2)(3))
print(fun(1, 2, 3))



# §Python简单的文件操作
file_object = open('thefile.txt')
try:
    all_the_text = file_object.read( )
finally:
    file_object.close( )
2.读文件
#读文本文件
input = open('data', 'r')   #第二个参数默认为r
input = open('data', 'rb')
#读取所有内容
file_object = open('thefile.txt')
try:
     all_the_text = file_object.read( )
finally:
     file_object.close( )
#读固定字节
file_object = open('abinfile', 'rb')
try:
    while True:
         chunk = file_object.read(100)
         if not chunk:
               break
         do_something_with(chunk)
finally:
    file_object.close( )
#读每行
list_of_all_the_lines = file_object.readlines( )
#如果文件是文本文件，还可以直接遍历文件对象获取每行：
for line in file_object:
     process line
3.写文件
写文本文件
output = open('data', 'w')
output = open('data', 'wb')
output = open('data', 'w+')
写数据
file_object = open('thefile.txt', 'w')
file_object.write(all_the_text)
file_object.close( )
写入多行
file_object.writelines(list_of_text_strings)
注意，调用writelines写入多行在性能上会比使用write一次性写入要高。
在处理日志文件的时候，常常会遇到这样的情况：日志文件巨大，不可能一次性把整个文件读入到内存中进行处理，例如需要在一台物理内存为 2GB 的机器上处理一个 2GB 的日志文件，我们可能希望每次只处理其中 200MB 的内容。
在 Python 中，内置的 File 对象直接提供了一个 readlines(sizehint) 函数来完成这样的事情。以下面的代码为例：
file = open('test.log', 'r')sizehint = 209715200 # 200Mposition = 0lines = file.readlines(sizehint)while not file.tell() - position < 0: position = file.tell() lines = file.readlines(sizehint)
每次调用 readlines(sizehint) 函数，会返回大约 200MB 的数据，而且所返回的必然都是完整的行数据，大多数情况下，返回的数据的字节数会稍微比 sizehint 指定的值大一点（除最后一次调用 readlines(sizehint) 函数的时候）。通常情况下，Python 会自动将用户指定的 sizehint 的值调整成内部缓存大小的整数倍。
file在python是一个特殊的类型，它用于在python程序中对外部的文件进行操作。在python中一切都是对象，file也不例外，file有file的方法和属性。下面先来看如何创建一个file对象：

file(name[, mode[, buffering]])
file()函数用于创建一个file对象，它有一个别名叫open()，可能更形象一些，它们是内置函数。来看看它的参数。它参数都是以字符串的形式传递的。name是文件的名字。
mode是打开的模式，可选的值为r w a U，分别代表读（默认） 写 添加支持各种换行符的模式。用w或a模式打开文件的话，如果文件不存在，那么就自动创建。此外，用w模式打开一个已经存在的文件时，原有文件的内容会被清空，因为一开始文件的操作的标记是在文件的开头的，这时候进行写操作，无疑会把原有的内容给抹掉。由于历史的原因，换行符在不同的系统中有不同模式，比如在 unix中是一个\n，而在windows中是‘\r\n’，用U模式打开文件，就是支持所有的换行模式，也就说‘\r’ '\n' '\r\n'都可表示换行，会有一个tuple用来存贮这个文件中用到过的换行符。不过，虽说换行有多种模式，读到python中统一用\n代替。在模式字符的后面，还可以加上+ b t这两种标识，分别表示可以对文件同时进行读写操作和用二进制模式、文本模式（默认）打开文件。
buffering如果为0表示不进行缓冲;如果为1表示进行“行缓冲“;如果是一个大于1的数表示缓冲区的大小，应该是以字节为单位的。
file对象有自己的属性和方法。先来看看file的属性。
closed #标记文件是否已经关闭，由close()改写
encoding #文件编码
mode #打开模式
name #文件名
newlines #文件中用到的换行模式，是一个tuple
softspace #boolean型，一般为0，据说用于print
file的读写方法：
F.read([size]) #size为读取的长度，以byte为单位
F.readline([size]) #读一行，如果定义了size，有可能返回的只是一行的一部分
F.readlines([size]) #把文件每一行作为一个list的一个成员，并返回这个list。其实它的内部是通过循环调用readline()来实现的。如果提供size参数，size是表示读取内容的总长，也就是说可能只读到文件的一部分。
F.write(str) #把str写到文件中，write()并不会在str后加上一个换行符
F.writelines(seq) #把seq的内容全部写到文件中。这个函数也只是忠实地写入，不会在每行后面加上任何东西。
file的其他方法：
F.close() #关闭文件。python会在一个文件不用后自动关闭文件，不过这一功能没有保证，最好还是养成自己关闭的习惯。如果一个文件在关闭后还对其进行操作会产生ValueError
F.flush() #把缓冲区的内容写入硬盘
F.fileno() #返回一个长整型的”文件标签“
F.isatty() #文件是否是一个终端设备文件（unix系统中的）
F.tell() #返回文件操作标记的当前位置，以文件的开头为原点
F.next() #返回下一行，并将文件操作标记位移到下一行。把一个file用于for ... in file这样的语句时，就是调用next()函数来实现遍历的。
F.seek(offset[,whence]) #将文件打操作标记移到offset的位置。这个offset一般是相对于文件的开头来计算的，一般为正数。但如果提供了whence参数就不一定了，whence可以为0表示从头开始计算，1表示以当前位置为原点计算，2表示以文件末尾为原点进行计算。需要注意，如果文件以a或a+的模式打开，每次进行写操作时，文件操作标记会自动返回到文件末尾。
F.truncate([size]) #把文件裁成规定的大小，默认的是裁到当前文件操作标记的位置。如果size比文件的大小还要大，依据系统的不同可能是不改变文件，也可能是用0把文件补到相应的大小，也可能是以一些随机的内容加上去。



1、去空格及特殊符号
s.strip().lstrip().rstrip(',')

2、复制字符串
#strcpy(sStr1,sStr2)
sStr1 = 'strcpy'
sStr2 = sStr1
sStr1 = 'strcpy2'
print sStr2

3、连接字符串
#strcat(sStr1,sStr2)
sStr1 = 'strcat'
sStr2 = 'append'
sStr1 += sStr2
print sStr1

4、查找字符
#strchr(sStr1,sStr2)
# < 0 为未找到
sStr1 = 'strchr'
sStr2 = 's'
nPos = sStr1.index(sStr2)
print nPos

5、比较字符串
#strcmp(sStr1,sStr2)
sStr1 = 'strchr'
sStr2 = 'strch'
print cmp(sStr1,sStr2)

6、扫描字符串是否包含指定的字符
#strspn(sStr1,sStr2)
sStr1 = '12345678'
sStr2 = '456'
#sStr1 and chars both in sStr1 and sStr2
print len(sStr1 and sStr2)

7、字符串长度
#strlen(sStr1)
sStr1 = 'strlen'
print len(sStr1)

8、将字符串中的大小写转换
S.lower() #小写
S.upper() #大写
S.swapcase() #大小写互换
S.capitalize() #首字母大写
String.capwords(S) #这是模块中的方法。它把S用split()函数分开，然后用capitalize()把首字母变成大写，最后用join()合并到一起
#实例：
#strlwr(sStr1)
sStr1 = 'JCstrlwr'
sStr1 = sStr1.upper()
#sStr1 = sStr1.lower()
print sStr1

9、追加指定长度的字符串
#strncat(sStr1,sStr2,n)
sStr1 = '12345'
sStr2 = 'abcdef'
n = 3
sStr1 += sStr2[0:n]
print sStr1

10、字符串指定长度比较
#strncmp(sStr1,sStr2,n)
sStr1 = '12345'
sStr2 = '123bc'
n = 3
print cmp(sStr1[0:n],sStr2[0:n])

11、复制指定长度的字符
#strncpy(sStr1,sStr2,n)
sStr1 = ''
sStr2 = '12345'
n = 3
sStr1 = sStr2[0:n]
print sStr1

12、将字符串前n个字符替换为指定的字符
#strnset(sStr1,ch,n)
sStr1 = '12345'
ch = 'r'
n = 3
sStr1 = n * ch + sStr1[3:]
print sStr1

13、扫描字符串
#strpbrk(sStr1,sStr2)
sStr1 = 'cekjgdklab'
sStr2 = 'gka'
nPos = -1
for c in sStr1:
    if c in sStr2:
        nPos = sStr1.index(c)
        break
print nPos

14、翻转字符串
#strrev(sStr1)
sStr1 = 'abcdefg'
sStr1 = sStr1[::-1]
print sStr1

15、查找字符串
#strstr(sStr1,sStr2)
sStr1 = 'abcdefg'
sStr2 = 'cde'
print sStr1.find(sStr2)

16、分割字符串
#strtok(sStr1,sStr2)
sStr1 = 'ab,cde,fgh,ijk'
sStr2 = ','
sStr1 = sStr1[sStr1.find(sStr2) + 1:]
print sStr1
#或者
s = 'ab,cde,fgh,ijk'
print(s.split(','))

17、连接字符串
delimiter = ','
mylist = ['Brazil', 'Russia', 'India', 'China']
print delimiter.join(mylist)

18、PHP 中 addslashes 的实现
def addslashes(s):
    d = {'"':'\\"', "'":"\\'", "\0":"\\\0", "\\":"\\\\"}
    return ''.join(d.get(c, c) for c in s)

s = "John 'Johny' Doe (a.k.a. \"Super Joe\")\\\0"
print s
print addslashes(s)

19、只显示字母与数字
def OnlyCharNum(s,oth=''):
    s2 = s.lower();
    fomart = 'abcdefghijklmnopqrstuvwxyz0123456789'
    for c in s2:
        if not c in fomart:
            s = s.replace(c,'');
    return s;

print(OnlyStr("a000 aa-b"))

20、截取字符串
str = '0123456789′
print str[0:3] #截取第一位到第三位的字符
print str[:] #截取字符串的全部字符
print str[6:] #截取第七个字符到结尾
print str[:-3] #截取从头开始到倒数第三个字符之前
print str[2] #截取第三个字符
print str[-1] #截取倒数第一个字符
print str[::-1] #创造一个与原字符串顺序相反的字符串
print str[-3:-1] #截取倒数第三位与倒数第一位之前的字符
print str[-3:] #截取倒数第三位到结尾
print str[:-5:-3] #逆序截取，具体啥意思没搞明白？

21、字符串在输出时的对齐
S.ljust(width,[fillchar])
#输出width个字符，S左对齐，不足部分用fillchar填充，默认的为空格。
S.rjust(width,[fillchar]) #右对齐
S.center(width, [fillchar]) #中间对齐
S.zfill(width) #把S变成width长，并在右对齐，不足部分用0补足

22、字符串中的搜索和替换
S.find(substr, [start, [end]])
#返回S中出现substr的第一个字母的标号，如果S中没有substr则返回-1。start和end作用就相当于在S[start:end]中搜索
S.index(substr, [start, [end]])
#与find()相同，只是在S中没有substr时，会返回一个运行时错误
S.rfind(substr, [start, [end]])
#返回S中最后出现的substr的第一个字母的标号，如果S中没有substr则返回-1，也就是说从右边算起的第一次出现的substr的首字母标号
S.rindex(substr, [start, [end]])
S.count(substr, [start, [end]]) #计算substr在S中出现的次数
S.replace(oldstr, newstr, [count])
#把S中的oldstar替换为newstr，count为替换次数。这是替换的通用形式，还有一些函数进行特殊字符的替换
S.strip([chars])
#把S中前后chars中有的字符全部去掉，可以理解为把S前后chars替换为None
S.lstrip([chars])
S.rstrip([chars])
S.expandtabs([tabsize])
#把S中的tab字符替换没空格，每个tab替换为tabsize个空格，默认是8个

23、字符串的分割和组合
S.split([sep, [maxsplit]])
#以sep为分隔符，把S分成一个list。maxsplit表示分割的次数。默认的分割符为空白字符
S.rsplit([sep, [maxsplit]])
S.splitlines([keepends])
#把S按照行分割符分为一个list，keepends是一个bool值，如果为真每行后而会保留行分割符。





###################################################
##
##	Python
##
pip install opencv-python numpy matplotlib pytorch

第三方神包：
PIL
numpy
matpoltlib
scipy
pypdf2
pytesseract

pip list
pip install -r requirements.txt
pip freeze > requirements.txt
pip install <package>==<version>
pip install <package> >= <version>,<<version> --force-reinstall

import pysnooper
#@pysnooper.snoop()



