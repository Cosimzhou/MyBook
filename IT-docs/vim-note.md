vim Note
========

# 跳转
[[           函数开始处
]]           下一函数的开始处
{、}         上、下一段

\#、\*        转向上一个、下一个符
\`         转回跳出的标记
%          括号匹配
g]         跳到定义处（代码级）
gd         跳到定义处（文件级）
gf         打开光标处的文件
gg         光标转至文件顶
G          光标转至文件尾

"# 书签
mx            添加书签x
\`x           跳转到书签x
'x            跳转到书签x 行首
:marks     显示书签
\`"       到退出之前最后一次编辑的位置
\`[       到先前改变或者复制文本的第一个字符
\`]       到先前改变或复制文本的最后一个字符
\`<       到先前选择可视化区域的第一行
\`>       到先前选择可视化区域的最后一行
\`.       到最后一次光标的位置
\`^       到最后一次插入模式停止的光标所在位置

:122                 #转到122行
vim +n 文档名     #打开文档后，定位第n行

<C-[>    ESC，命令模式
<C-o>    光标跳回上次位置
<C-i>    光标跳往下次位置
<C-]>    跳入标记的定义

<C-y>、<C-e>    向上、下滚屏
<C-u>、<C-d>    向上、下跳半屏
<C-b>、<C-f>    向上、下跳一屏

"# 滚屏
zz        当前行滚到屏幕中央
zt        当前行滚到屏幕顶部
zb        当前行滚到屏幕底部
zl        屏幕向右移动几个字符（nzl）
zh        屏幕向左移动几个字符（nzh）
zL        屏幕向右滚动
zH        屏幕向左滚动
ze        屏幕滚动到最右
zs        屏幕滚动到最左



# 折叠
zc       折叠
zC       对所在范围内所有嵌套的折叠点进行折叠
zo       展开折叠
zO       对所在范围内所有嵌套的折叠点展开
[z       到当前打开的折叠的开始处。
]z       到当前打开的折叠的末尾处。
zj       向下移动。到达下一个折叠的开始处。关闭的折叠也被计入。
zk       向上移动到前一折叠的结束处。关闭的折叠也被计入。
zm       全部折叠
zr       打开全部折叠

set fdm=xxx
|       |          |
|-------|----------|
|manual |手工定义折叠|
|indent |更多的缩进表示更高级别的折叠|
|expr   |用表达式来定义折叠|
|syntax |用语法高亮来定义折叠|
|diff   |对没有更改的文本进行折叠|
|marker |对文中的标志折叠|



:ta var        列出代码

=~#   正则匹配


map xx. #显示映射内容


# 寄存器
查看所有寄存器值：:reg
查看指定寄存器值：:reg "{register name}

:delete c       #剪切内容到c寄存器
:put c          #将c粘贴到当前位置

调取寄存器值
NORMAL Mode：   "{register name}
COMMAND MODE：  <C-r>+"寄存器名称 （输入<C-r>后VIM会自动打出"寄存器引用符号。
INSERT MODE：   <C-r>+寄存器名称（无需输入寄存器引用符号"）

未命名寄存器           ""
10个数字命名寄存器     "0 to "9
小删除寄存器           "-
26个字母命名寄存器     "a to "z or "A to "Z
选择删除寄存器         "\*, "+ and "~


4个只读寄存器          ":, "., "% and "#
四个只读寄存器
".     #之前插入的文本
"%     #当前文件路径
":     #之前执行的命令
"#     #轮换文件，之前打开的文件
"=     #计算结果
"/     #之前搜索的内容
""     #匿名寄存器
"\_     #黑洞

系统
"+
"\*




# 宏录制
qa 操作序列 q, @a, @@
qa 把你的操作记录在寄存器 a。
于是 @a 会replay被录制的宏。
@@ 是一个快捷键用来replay最新录制的宏。


# 选择
v            选择
V            行选择
<C-v>        矩形选择
gv           恢复上次选区


# 输入模式
a            在光标位置后开始接收输入。
A            在行尾后开始接收输入。
i            在光标位置前开始接收输入。
I            在行首后开始接收输入。
o            在光标所在行之后开辟一个新的空行，并开始接收输入。
O            在光标所在行之前开辟一个新的空行，并开始接收输入。
c            删除n并编辑
C            删除行，并编辑
s            删除字符并开始输入
S            删除行，并开始输入

# 删除/剪切
dw           删除之后的词
diw          删除整词
dd           剪切当前行
ndd          n表示大于1的数字，剪切n行
dw           从光标处剪切至一个单子/单词的末尾，包括空格
de           从光标处剪切至一个单子/单词的末尾，不包括空格
d$           从当前光标剪切到行末
D            从当前光标剪切到行末
d0           从当前光标位置（不包括光标位置）剪切之行首
d3l          从光标位置（包括光标位置）向右剪切3个字符
d5G          将当前行（包括当前行）至第5行（不包括它）剪切
d3B          从当前光标位置（不包括光标位置）反向剪切3个单词
dH           剪切从当前行至所显示屏幕顶行的全部行
dM           剪切从当前行至命令M所指定行的全部行
dL           剪切从当前行至所显示屏幕底的全部行


cnw[word]    将n个word改变为word
cc           改变整行
C$           改变到行尾

# 复制粘贴
:命令行<C-r>"                #从vim中拷贝字符串到:命令行
:命令行<C-r>+或者<C-r>\*     #从系统剪贴板拷贝字符串到:命令行：
:命令行<C-R><C-W>            #命令行补齐
3yy                          #复制3行
yy                           #复制一行
yw                           #复制一词
yiw                          #复制完整一词

p            #在此粘贴
P            #在些之前粘贴



# 窗口切换控制
:Ve         新窗口浏览文件:Vexplore
:Ex         窗口浏览文件:Explore
:sp            多窗口开文件:split
:vs            多窗口开文件:vsplit

:tabnew [++opt选项] [+cmd] 文件            建立对指定文件新的tab
:tabc       关闭当前的tab
:tabo       关闭所有其他的tab
:tabs       查看所有打开的tab
:tabp       前一个
:tabn       后一个
:tabm i     tab移动到第i位（0开始）
:tabm +i    tab向后移动I位
:tabm +i    tab向后移动i位

标准模式下：
gt , gT 可以直接在tab之间切换。

<C-w><C-r>     窗口位置交换
<C-w>n+     窗口增大n
<C-w>n-    窗口减小n

<C-w>n<     窗口增大n
<C-w>n>    窗口减小n


# 编辑
<、>         缩进
J                合并下一行
gJ           无空格的合并行
:e!            文档复原
<C-r>     重做
u             撤销

<C-p>    代码补全

<C-a>    数据增加
<C-x>    数据减小


## 大小写转换
gU    转大写
gu     转小写
~       翻转
g~w    翻转整词


# 替换
:1,$s/x/y/g                                           #指定行间替换
:s/x/y/                                                  #单行替换
:%s……                                               #全域替换
:%s@X@\=line('.')                                 #将X换为行号
:%s@X@\=printf("%03d", line('.'))        #将X换为格式化后的行号
:%s/keyword/&/gn                               #统计keyword的出现次数

## 替换换行：
:%s/\n/;\n/g        #结果总是出错
:%s/\n/;\r/g        #解决方案

\#字符串查找时，”\n” 是换行，”\r” 是回车，也就是经常会看到的 ^M（备注-1）。
\#字符串替换时，”\r” 是换行，’\n” 是空字符（0×00）。

### 清除所有 ^M 的替换命令
:%s/CTRL+V CTRL+M//g
就是 Control 键+V，然后再 Control 键 + M，就变成了 ^M，然后替换为空就可以了。



# @查找
向下查找模式：   /
向上查找模式：   ?
n     下一个匹配的模式
N     上一个匹配的模式
‘\*’可以查找当前光标下的word（完全符合），‘g\*’则部分符合，以#代替\*表示向后（上）找
^I     Tab (输入<C-V>+<C-I>)
^M     单字换行"\n" (输入<C-V>+<C-M>)

# @全局命令
全局(global)显示命令，就是用 :g＋正则表达式
:g/{pattern}/{cmd}     全局找到匹配的,然后对这些行执行命令{cmd}
:v/{pattern}/{cmd}     与g相反。对全局中，匹配不到正则的这些行执行命令{cmd}
:g/{pattern1}/,/{pattern2}/{cmd}     全局找到匹配的1,2中间的内容,然后对这些行执行命令{cmd}
:g/{pattern}/v/{notpattern}/{cmd}     全局找到匹配但确不会匹配notpattern的内容,然后对这些行执行命令{cmd}

```
:g!/^dd/d                                        删除不含字符串'dd'开头的行
:g/^/exec 's/^/'.strpart(line('.').' ', 0, 4)    在行首插入行号
:g/fred/,/joe/d                                  not line based (very powerfull)
:g/fred/t$                                       拷贝行，从fred到文件末尾(EOF)
:g/\<fred\>/                                     显示所有能够为单词fred所匹配的行
:g/<input\|<form/p                               或者 要用\|
:g/^$/,/./-j                                     压缩空行(多行空行合并为一行)
:g/^/m0                                          按行翻转文章 (m = move)
:g/<pattern>/z#.5|echo '=========='              漂亮的显示
:g/<pattern>/z#.5                                显示内容，还有行号
:g/^/pu _                                        把文中空行扩增一倍 (pu = put),原来两行间有一个空行，现在变成2个
:g/^\s*$/d                                       空行(空格也包含)删除.
:v/./.,/./-1join                                 压缩空行(多行空行合并为一行)
:v/^dd/d                                         同上,译释：v == g!，就是不匹配！
```

d   删除
p   粘贴
m   移动
j   合并行
t
z   上下文

@缓存命令
:ls          列出
:bn          打开下一个缓存文件
:bp          打开上一个缓存文件
:b1~n        打开指定编号的缓存文件
:bfirst
:blast
:sb1         新窗口打开1号缓存
:bd          关闭缓存文件，文件被移至表外
:bp|bd#      关闭缓存文件不关闭窗口
:buffers     列出缓存列表
:buffers!    列出所有缓存列表（包括表外缓存文件）
:bwipe       清理表外缓存

缓存标识及含义
u 列表外缓冲区 | unlisted-buffer|。
% 当前缓冲区。
# 轮换缓冲区。
a 激活缓冲区，缓冲区被加载且显示。
h 隐藏缓冲区，缓冲区被加载但不显示。
= 只读缓冲区。
- 不可改缓冲区， 'modifiable' 选项不置位。
+ 已修改缓冲区。


@显示行号
:e 文档名 打开文档，此方式可以在编辑一个文档的同时打开另外一个文档
:set nu #显示行号(number)
:set nu rnu #显示相对行号(number)
:set vb #(visual bell)

@二进制编辑
vim -b -c "set noeol" xxxx    #可以避免在文件尾追加换行符
vim -b xxxx
:%!xxd
:%!xxd -r  #退出二进制编辑后保存
:wq


@键说明
:h key-notation
<C-.>        Ctrl+.
<S-.>         shift-key
<M-.>         alt-key or meta-key
<A-.>         same as <M-...>
<D-.>         command-key (Macintosh only)
<cr>         carry return
<leader>    引导键，如下可定义：let mapleader=","
<silent>    不回显

~/.vimrc
syntax on
set tabstop=4
set wrap! #换行/不换行切换


@添加新语法高亮
在下列路径加入高亮脚本，如golang，下列两路径中添加go.vim
~/.vim/syntax       # 添加语法高亮描述
~/.vim/ftdetect     # 添加文件类型检测文件


@vimdiff
vimdiff file1 file2 #垂直对比
vimdiff -O file1 file2 #垂直对比
vimdiff -o file1 file2 #水平切分对比

# vimdiff 的特有快捷键
dp        # 将diff推至对面去
do        # 将diff从对面拉到此文件中
]c        # 下一处diff
[c        # 上一处diff

:diffupdate # 重新扫描



# vimscript


expand（{expr} [,{nosuf} [, {list}]]） expand()

 扩展{expr}里的通配符和下列关键字。
 'wildgnorecase' 此处适用。

 如果给出{list}且为TRUE,返回列表。否则返回的是字符串，且如果返回多个匹配，以<NL>字符分隔[备注：5.0版本适用空格。但是文件名如果也包含空格就会有问题]。
 如果扩展失败，返回空字符串。如果{expr}以'%','#'或'<'开始，不返回不存在的文件名。详见下。
 如果{expr}以'%'、‘#’、或‘<’开始，类似于cmdline-special变量的方式扩展，扩宝相关的修饰符。这里是一个简短的小结：

 % 当前文件名
 # 交换文件名
 #n 交换文件名n
 <cfile> 光标所在的文件名（其实就是光标所在的一个字符串的名）
 <afile> 自动命令文件名（当expand在自动命令中执行的时候，扩展为自动命令所在的文件的文件名）
 <abuf> 自动命令的缓冲区号（当expand在指定命令中执行的时候，扩展为自动命令的缓冲区号）
 <amatch> 自动命令匹配的名字（绝对路径下的文件名）
 <sfile> 脚本文件名或者函数名（在脚本中扩展为脚本文件名，在函数中，扩展为函数名）
 <slnum> 脚本文件的行号（当expand（‘<slnum>’）在某一行，就扩展为那一行的行号）
 <cword> 扩展为光标所在的单词
 <cWORD> 扩展为光标所在的字符串（比cword扩展的更多）
 <client> 最近收到的消息的值

修饰符：
 :p 扩展为完整的路径
 :h 去掉最后一个部分
 :t 只保留最后一个部分
 :r 根部（去掉扩展名）
 :e 只有扩展名


@变量
set     设置常量，其“=”后不可带空格
let     变量赋值，或可变常量let &var=xxx
&var     是引用常量选项


@作用域前缀
b: 缓冲区级作用域
w: 窗口级作用域
t: 标签页级作用域
g: 全局变量
l: 函数内局部变量
s: vim脚本文件级作用域
a: 函数参数 （a:0 为 '...'变长参数的长度，a:1第一个，a:2第二个…… ）
v: Vim专用的全局变量


@数据类型
首先是数据类型，Vimscript提供下面9种基本数据类型：

| 选项 [options] | 含义    |
| -------------- | ------- |
| Number:        | 32位带符号整数. 如果支持+num64，就是64位带符号整数。支持十六进制，二进制和八进制。|
| Float:         | 浮点数。只有编译时支持+float才有。|
| String:        | 字符串。|
| List:          | 有序列表。|
| Dictionary:    | 哈希表。|
| Funcref:       | 函数引用。|
| Job:           | 任务相关|
| Channel:       | 通道相关|
| 特殊值         | v:false v:true v:none v:null v:val |
一个变量的类型可以通过type()函数查看。

@数字和字符串
在Vimscript中，字符串和数字之间会进行自动转换。我们看下官方的几个例子：
String "456" --> Number 456
String "6bar" --> Number 6
String "foo" --> Number 0
String "0xf1" --> Number 241
String "0100" --> Number 64
String "0b101" --> Number 5
String "-8" --> Number -8
String "+8" --> Number 0
"foo"被转换成0，和"+8"被转换成0这两条case要特殊注意。
使用str2nr函数来做显示转换。因为str2nr默认是10进制的。
echo str2nr("0100") 的值为100.

@真值和假值
在Vimscript中，0表示假值，其余数值均表示真值。假值也可以用v:false表示，真值为v:true.

比如"foo"的值为假，因为"foo"转换成整数的值是0.

@列表类型
Vimscript的列表可以混杂各种元素。如：
:let b:list1 = [1, 4.1e+3, "Hello",[1,2]]
列表可以用下标访问。比如b:list1[0].
列表的下标从0开始计数。而[-1]表示最后一个元素。

如果要给列表元素一个不存在时的默认值的话，可以使用get()函数。如：
 :echo get(mylist, idx)
 :echo get(mylist, idx, "NONE")
两个列表可以通过+号来连接成一个列表：
 :let longlist = mylist + [5, 6]
 :let mylist += [7, 8]

@子列表
Vimscript取子列表跟其它脚本语言很像,用[起始位置:结束位置]来进行切片。
 :let shortlist = mylist[2:-1] " get List [3, "four"]
如果是从第一个元素开始，或者到最后一个元素结束，都可以省略：
 :let endlist = mylist[2:] " from item 2 to the end: [3, "four"]
 :let shortlist = mylist[2:2] " List with one item: [3]
 :let otherlist = mylist[:] " make a copy of the List
如果越界了，也不会产生错误，到最后一个元素结束了就是了么。
 :let mylist = [0, 1, 2, 3]
 :echo mylist[2:8] " result: [2, 3]
列表的赋值和拷贝
如果将一个列表赋给另一个变量，不会复制列表，只是传递引用。
如果想要复制一份列表的话，需要使用copy函数。如：
 :let aa = [[1, 'a'], 2, 3]
 :let bb = copy(aa)
 :call add(aa, 4)
 :let aa[0][1] = 'aaa'
 :echo aa
 [[1, aaa], 2, 3, 4]
 :echo bb
 [[1, aaa], 2, 3]
但是请注意，copy只是浅copy，如果有子列表，是只复制引用的。如果真的要大搬家，需要使用deepcopy()函数。

@列表的比较
is: 比较两个变量是否引用同一列表
==：比较两个列表的值是否相等
另外需要注意的是，对于变量，会自动将字符串转成数字，但是对于列表中的元素，没有这种自动转换。
 echo 4 == "4" # 1
 echo [4] == ["4"] # 0
列表的多变量赋值
如果要引用列表中的值，可以同时将其赋给多个变量。如：
 :let [var1, var2; rest] = mylist
等价于：
 :let var1 = mylist[0]
 :let var2 = mylist[1]
 :let rest = mylist[2:]
这个对于函数返回值之类的是个利好。

@列表的修改
对于可以定位的值，直接通过:let赋值的方式修改。
对于插入，添加，删除等，使用相关函数来进行操作：
 :call insert(list, 'a') " prepend item 'a'
 :call insert(list, 'a', 3) " insert item 'a' before list[3]
 :call add(list, "new") " append String item
 :call add(list, [1, 2]) " append a List as one new item
 :call extend(list, [1, 2]) " extend the list with two more items
 :let i = remove(list, 3) " remove item 3
 :let l = remove(list, 3, -1) " remove items 3 to last item
 :call filter(list, 'v:val !~ "x"') " remove items with an 'x'
列表还可以排序、反转和排重：
 :call sort(list) " sort a list alphabetically
 :call reverse(list) " reverse the order of items
 :call uniq(sort(list)) " sort and remove duplicates

使用for循环来处理列表
for循环是处理列表的最简用手段：
 :for item in mylist
 : call Doit(item)
 :endfor
for循环支持解构式的赋值：
 :for [i, j; rest] in listlist
 : call Doit(i, j)
 : if !empty(rest)
 : echo "remainder: " . string(rest)
 : endif
 :endfor

@列表常用函数
empty函数：判空
len函数：计算列表元素个数
max函数：求列表最大元素
min函数：求列表最小元素
count函数：计算元素在列表中出现的次数
index函数：求元素第一次出现的位置
split函数：将字符串拆分成列表
join函数：将列表连接成一个字符串

@字典（与js对象类似）
Vimscript的字典功能，其实就是哈希表。如：
 :let mydict = {1: 'one', 2: 'two', 3: 'three'}
 :let emptydict = {}
访问字典可以使用[]：
 :let val = mydict["one"]
 :let mydict["four"] = 4
在没有歧义的情况下，也可以使用.：
 :let val = mydict.one
 :let mydict.four = 4

@字典遍历
可以通过遍历keys列表和values列表的方式来遍历字典。如：
 :for key in keys(mydict)
 : echo key . ': ' . mydict[key]
 :endfor
 :for v in values(mydict)
 : echo "value: " . v
 :endfor
还可以遍历前先排一次序：
 :for key in sort(keys(mydict))
也可以将key和value打包在一起，使用item函数遍历：
 :for [key, value] in items(mydict)
 : echo key . ': ' . value
 :endfor

字典的复制
字典的复制也同样要使用copy和deepcopy函数。

字典的增删改查
字典的修改和增加都很简单，直接赋值就是了：
 :let dict[4] = "four"
 :let dict['one'] = item



@字符串处理函数（utf-8 编码）
函数	说明
nr2char()	将 utf-8 编码值转为对应字符
char2nr()	得到字符的 utf-8 编码值，或得到字符串首字符的 utf-8 编码值
str2nr()	将字符串转为整数
str2float()	将字符串转为浮点数
printf()	使用 % 格式化字符串，用法类似 C语言
escape({string}, {chars})	在 {string} 里用反斜杠 \ 转义 {chars} 里的字符
fnameescape()	转义特殊字符以适于 vim 命令，主要用于转义文件名参数
shellescape()	转义特殊字符以适于 shell 命令
tolower()	将字符串转为小写
toupper()	将字符串转为大写
tr({src}, {fromstr}, {tostr})	按 一 一 对应的方式转换字符串。也就是说，{fromstr} 的第一个字符被翻译成 {tostr} 的第一个字符，依此类推。和 unix 命令 tr 完全相同。例如 :tr(‘hello there’, ‘ht’, ‘HT’) 返回 ‘Hello THere’
expand()	将特殊关键字 %（当前文件名）、#（轮换文件名）和 <cword>（光标所在的单词）等展开
repeat({expr}, {count})	将字符串 {expr} 重复 {count} 次串接生成长字符串
eval()	将字符串当作表达式来计算，并返回结果
@列表或字典处理函数
列表或字典处理函数	说明
len()	返回列表或字典元素个数
empty()	检查列表或字典是否为空，空则返回数值 1，否则返回 0
extend()	在列表后附加另一个列表，或从一个字典增加元素到另一个字典。用 + 操作符连接两个列表将生成一个新列表。
remove()	删除列表里一或多个元素，或删除字典某个键的元素
count()	计算列表或字典里某值的出现次数
列表处理函数
insert()	在列表某处插入元素
add()	在列表后附加元素
match()	返回能匹配成功的元素索引
sort()	给列表排序
字典处理函数
has_key()	检查某键是否出现在字典里
keys()	得到字典的键列表
items()	得到字典的键-值组对的列表
@浮点数运算和逻辑运算
浮点数运算	说明
float2nr()	把浮点数转换为整数
abs()	取绝对值 （也适用于整数）
round()	四舍五入，最后保留一位小数
trunc()	删除小数点后的值
pow()	求幂
sqrt()	开平方
sin()等	三角函数
逻辑运算
and()	按位与
invert()	按位取反
or()	按位或
xor()	按位异或
@文件和目录相关函数
文件和目录相关函数	说明
finddir({name}[, {path}[, {count}]])	在路径 {path} 里查找目录 {name}，支持向下和向上的递归目录搜索，返回第一个找到的目录路径。如果找到的目录路径在当前目录之下，返回相对路径，否则，返回完整路径。如果省略 {path}，使用选项 &path 代替。如果给出可选的 {count}，寻找 {path} 里 {name} 第 {count} 次出现，而不是第一次。如果 {count} 为负，返回所有的匹配组成的列表。
findfile({name}[, {path}[, {count}]])	类似于 finddir()，不过寻找文件而不是目录。
resolve()	解析链接实际文件名
simplify()	简化文件名路径
pathshorten()	缩写文件名的中间路径（取首字母）
fnamemodify({fname}, {mods})	从文件名 {fname} 中获取其目录、全路径名、后缀名等相关名字的字符串（通过 {mods}）。修饰符 {mods} 以冒号开头接一个单字符，表示不同意义，可多个拼接使用，但必须按如下顺序给出
修饰符	注意：环境变量不能用于 {fname}，需要先用 expand() 扩展。
:p	文件完整路径名
:~	路径名缩减为基于主目录的相对路径。若文件不在主目录下，则文件名不会被改变。
:.	路径名缩减为基于当前目录的相对路径。若文件不在当前目录下，则文件名不会被改变。
:h	父目录名（文件名头部，除去文件名的最后一部分以及路径分隔符），不能与 :e、:r 或 :t 一起使用。
:t	文件名的尾部（文件名的最后一部分，纯文件名）。必须在 :r 或 :e 之前。
:r	文件名的根部 （除去最后的扩展名）。如果只有扩展名（文件名以’.’开始，例如’.vimrc’），则不会被删除。可以重复使用，以删除多个扩展名（最后一个先被删除）。
:e	扩展名（即文件名后缀）。只有单独使用时才有意义。如果没有扩展名，那结果为空。如果文件名只是一个扩展名（以’.’开始的文件名），则结果为空。可以重复使用来包含更多的扩展名。如果没有足够的扩展名（但是至少有一个），那么就尽可能多的包含。
executable()	检查是否存在可执行文件
exepath()	返回可执行程序的完整路径
filereadable()	检查文件是否可读
filewriteable()	检查文件是否可写
getcwd()	获取当前工作目录名
getfperm()	返回文件权限（类 rwxrw-rw- 字符串）
getfsize()	返回文件字节大小（目录返回 0，找不到文件返回 -1，文件过大，超出了 vim 的数值的范围，返回 -2）
getftype()	返回文件类型的描述（普通文件 file，目录 dir，符号链接 link 等）
readfile({fname} [, {binary} [, {max}]])	读文件 {fname} 至一个字符串列表，文件每行一项。如果 {binary} 包含 b，使用二进制模式，如果给出 {max}，指定读入的最大行数。
writefile({list}, {fname} [, {flags}])	将字符串列表 {list} 写入文件 {fname}，每项一行文本。如果 {flags} 包含 b，使用二进制模式，如果 {flags} 包含 a，使用附加模式。
isdirectory()	检查目录是否存在
@系统命令和时间函数
系统命令和时间函数	说明
system({expr} [, {input}])	执行外部系统命令 {expr}，结果为字符串形式返回。如果给出 {input} 且为字符串，该字符串被写到文件里，并传给外部系统命令作为标准输入。此外，vim 的命令行中，可用 :! 叹号开头，调用外部系统命令。
systemlist({expr} [, {input}])	和 system() 相同，但返回由行组成的列表。输出的工作方式和 readfile() 带 {binary} 参数设为 b 相同。
localtime()	返回当前时间，以 1970 年 01 月 01 日开始的秒数计算。
strftime({format} [, {time}])	返回字符串，即经过 {format} 字符串的格式转换的日期和时间。使用给定的 {time}，如果没有给出时间，使用当前时间。可以接受的 {format} 取决于你的系统。可用时间格式 {format} 与 C语言的同名标准函数相同，如 strftime(‘%Y-%m-%d’) 将返回类似 2019-03-02 的字符串。
reltime([{start} [, {end}]])	返回更精确的时间，具体格式与系统有关，可用来计算命令或函数执行的时间。没有参数，返回当前时间。带一个参数 {start}，返回从开始时刻 {start} 到现在所经过的时间。带两个参数，返回 {start} 和 {end} 之间跨越的时间。{start} 和 {end} 参数必须是 reltime() 返回的值。


量词
本文下面使用的元字符都是 magic模式(除了$ . * ^ 之外其他元字符都要加反斜杠)下的,在very magic模式下,只需要将\\去掉即可.

vim	意义
\*	匹配0个或多个(匹配优先)
\+	匹配1个或多个(匹配优先)
\?或\=	0个或1个(匹配优先)，\?不能在 ? 命令（逆向查找）中使用
\{n,m}	匹配n个到m个(匹配优先),如\d{1, 3}可以匹配1到3个数字,类似11, 1, 333
\{n,}	最少n个(匹配优先)
\{,m}	最多m个(匹配优先)
\{n}
恰好n个
在这里,有些东西需要说明一下,那就是上面的用于限定数量的元字符不单单可以用于字符,同时也可以用于模式,举个例子,下面的模式:

\(123\)\{2} 可以匹配123123.

一些常用的元字符
magic (\m)：除了$ . * ^ 之外其他元字符都要加反斜杠。
nomagic (\M)：除了 $ ^ 之外其他元字符都要加反斜杠。
very magic(\v)：任何元字符都不用加反斜杠
very nomagic(\V)：任何元字符都必须加反斜杠

例如：
/\m.\* # 查找任意字符串
/\M.* # 查找字符串 .* （点号后面跟个星号）
/\v(a.c){3}$ # 查找行尾的abcaccadc
/\m(a.c){3}$ # 查找行尾的(abc){3}
/\M(a.c){3}$ # 查找行尾的(a.c){3}
/\V(a.c){3}$ # 查找任意位置的(a.c){3}$


元字符	说明
.	匹配任意一个字符,如p\*p可以匹配字符串pep, pip或者pcp
[abc]	匹配方括号中的任意一个字符。可以使用-表示字符范围
[a-z0-9]	匹配小写字母和阿拉伯数字
[^abc]	在方括号内开头使用^符号，表示匹配除方括号中字符之外的任意字符
\d	匹配阿拉伯数字，等同于[0-9]
\D	匹配阿拉伯数字之外的任意字符，等同于[^0-9]
\x	匹配十六进制数字，等同于[0-9A-Fa-f]
\w	匹配单词字母，等同于[0-9A-Za-z_]
\W	匹配单词字母之外的任意字符，等同于[^0-9A-Za-z_]
\t	匹配<TAB>字符
\s	匹配空白字符，等同于[ \t]
\S	匹配非空白字符，等同于[^ \t]
\a	所有的字母字符. 等同于[a-zA-Z]
\l	小写字母[a-z]
\L	非小写字母[^a-z]
\u	大写字母 [A-Z]
\U	非大写字幕[^A-Z]
表示位置的符号
位置元字符	含义
$	匹配行尾,如here:$只会匹配出位于一行结尾的here:.
^	匹配行首,如^Part只会匹配出位于一行开头的Part.
\< \>	会匹配出以某些字符开头的(\<)或结尾(\>)的单词.\<ac只会匹配出以ac开头的单词,如action,而ac>/只会匹配出以ac结尾的单词,如maniac.\<action\>会匹配出action这个单词.单词的开头和结尾,是用标点符号或空格来分隔的.
替换变量
在正规表达式中使用 \( 和 \) 符号括起正规表达式，即可在后面使用\1、\2等变量来访问 \( 和 \) 中的内容。这种形式实际上是将\(与\)中的模式保存到了特殊的空间(称之为"保留缓冲区").这种方法可以保存任意一行中的9个模式.

举个例子,对于下面的模式:

\(That\) or \(this\)
会将That存放到缓冲区1中,而将this保存到保留缓冲区2中,这些保留的模式在以后可以用\1到\9的序列重新排列,例如,如果要将That or this改成this or That,可以键入:

:%s/\(That\) or \(this\)/\2 or \1/
也可以实现在搜索或者替换字符串时使用\n表示法:

:%s\(abcd\)\1/alphabet-soup/
可以将abcdabcd替换为alphabet-soup.这里需要特别注意一下,\0表示我们所匹配的所有内容.

非贪婪匹配
非贪婪匹配也是正则表达式中一个非常强大的特性,我这里稍微来记录一下vim中非贪婪匹配的语法.

.*          贪婪模式

\{-}     懒惰模式

假设我有这样一段文本:

map<wstring, wstring> grammarTokens = {
    {L"_LPAR", L"\\("},
    {L"_RPAR", L"\\)"},
    {L"_LBRA", L"\\["},
    {L"_RBRA", L"\\]"},
    {L"OP", L"[+?]"},
    {L"_COLON", L":"},      // 冒号
    {L"_OR", L"\\|"},
    {L"_DOT", L"\\."},
    {L"RULE", L"!?[_?]?[a-z][_a-z0-9]*"},  // 用于表示普通的规则
    {L"TOKEN", L"_?[A-Z][_A-Z0-9]*"},
    {L"REGEXP", L"/(?!/)(\\/|\\\\|[^/\n])*?/i?"},
    {L"_NL", L"(\r?\n)+\s*"},
    {L"WS", L"[\t]+"},
    {L"COMMENT", L"//[^\n]*"},
    {L"_TO", L"-->"},
    {L"_IGNORE", L"%ignore"},
    {L"_IMPORT", L"%import"}
};
上面的这段c++代码片段实际上是存在错误的,要将所有的字符都变成这样wstring(L"xxxx"),才能消除错误,所以,我们想到了,正则表达式正好可以用来干这个事情.

最开始的时候,我使用的是这种语法:

:%s/\(L".*"\)/wstring(\1)/g
结果很有意思:

map<wstring, wstring> grammarTokens = {
    {wstring(L"_LPAR", L"\\(")},
    {wstring(L"_RPAR", L"\\)")},
    {wstring(L"_LBRA", L"\\[")},
    {wstring(L"_RBRA", L"\\]")},
    {wstring(L"OP", L"[+?]")},
    {wstring(L"_COLON", L":")},     // 冒号
    {wstring(L"_OR", L"\\|")},
    {wstring(L"_DOT", L"\\.")},
    {wstring(L"RULE", L"!?[_?]?[a-z][_a-z0-9]*")},  // 用于表示普通的规则
    {wstring(L"TOKEN", L"_?[A-Z][_A-Z0-9]*")},
    {wstring(L"REGEXP", L"/(?!/)(\\/|\\\\|[^/\n])*?/i?")},
    {wstring(L"_NL", L"(\r?\n)+\s*")},
    {wstring(L"WS", L"[\t]+")},
    {wstring(L"COMMENT", L"//[^\n]*")},
    {wstring(L"_TO", L"-->")},
    {wstring(L"_IGNORE", L"%ignore")},
    {wstring(L"_IMPORT", L"%import")}
};
这个显然是超乎我们预期的,原因在于正则表达式中.*是贪婪匹配,什么意思呢,也就是说,这个表达式会一直向前匹配,匹配尽可能多的文本.
 以{L"_LPAR", L"\\("}这一行为例,用\(L".*"\)来进行匹配的时候,L匹配L, "匹配",然后.可以匹配任意的字符,*代表重复零次或者多次,因此,这里匹配了_LPAR,虽然下一个"可以和正则式的"相匹配,如果此时停下来,是完全合理的,但是所谓的贪婪,就体现在了这里,我要一直尝试,一定要匹配更多的字符,所以继续前进,.*匹配了_LPAR",L"\\(,一直到下一个",正则表达式发现如果我继续用.*来匹配掉"的话,那么在这一行,我的匹配会失败,所以不能继续了,所以用正则表达式中的"匹配",匹配成功.

你可能会疑问,为什么.*不匹配到下一行,下下行,我只能说,vim的正则表达式是一行一行进行匹配的.

所以人们为了避免这种情况,提出了一个非贪婪匹配的概念,核心是,匹配尽可能少的字符.

所以在这里,我们要将其替换为非贪婪匹配,非贪婪匹配的语法很奇葩,是这样的\{-},我们要将前面的.*变成.\{-},所以命令变成了:

:%s/\(L".\{-}"\)/wstring(\1)/g
或者使用very magic模式,也可以达到同样的效果:

:%s/(L.{-})/wstring(\1)/g
结果非常漂亮:

map<wstring, wstring> grammarTokens = {
    {wstring(L"_LPAR"), wstring(L"\\(")},
    {wstring(L"_RPAR"), wstring(L"\\)")},
    {wstring(L"_LBRA"), wstring(L"\\[")},
    {wstring(L"_RBRA"), wstring(L"\\]")},
    {wstring(L"OP"), wstring(L"[+?]")},
    {wstring(L"_COLON"), wstring(L":")},        // 冒号
    {wstring(L"_OR"), wstring(L"\\|")},
    {wstring(L"_DOT"), wstring(L"\\.")},
    {wstring(L"RULE"), wstring(L"!?[_?]?[a-z][_a-z0-9]*")},  // 用于表示普通的规则
    {wstring(L"TOKEN"), wstring(L"_?[A-Z][_A-Z0-9]*")},
    {wstring(L"REGEXP"), wstring(L"/(?!/)(\\/|\\\\|[^/\n])*?/i?")},
    {wstring(L"_NL"), wstring(L"(\r?\n)+\s*")},
    {wstring(L"WS"), wstring(L"[\t]+")},
    {wstring(L"COMMENT"), wstring(L"//[^\n]*")},
    {wstring(L"_TO"), wstring(L"-->")},
    {wstring(L"_IGNORE"), wstring(L"%ignore")},
    {wstring(L"_IMPORT"), wstring(L"%import")}
};
错误消除.

环视,或者说正向预查,反向预查
在各种常用工具对比中，我看到vim是支持计数的，而且似乎大部分常用的正则元字符都与perl兼容，比如\s,\d,\D,\w,\W, < >。但vim不支持\b，即单词边界。另外，vim中比较麻烦的是它似乎支持的是BRE（基本正则表达式，posix定义的），BRE中所有括号都不是元字符，因为作为元字符的是\(,\{。比如vim中匹配连续3个9，你得用9\{3\}，原来我一直以为不支持，但我还是觉得麻烦了一点，grep默认也是使用的这种BRE 。

与perl相比，vim将(?换成了\@，并且这个符号应该跟在匹配模式的后边。下面是一组对比:

vim	Perl	意义	例子
\@=	(?=	顺序环视	查找后面是sql的my： /my\(sql\)\@=
\@!	(?!	顺序否定环视	查找后面不是sql的my： /my\(sql\)\@!
\@<=	(?<=	逆序环视	查找前面是my的sql： /\(my\)\@<=sql
\@<!	(?<!	逆序否定环视	查找前面不是my的sql： /\(my\)\@<!sql
\@>	(?>	固化分组
\%(atom\)	(?:	非捕获型括号(此分组不捕获，可以理解为不算在分组信息中)	:%s/\%(my\)sql\(ok\)/\1这个命令会将mysqlok替换为 ok ，由于my为捕获在分组中，故组中\1 为ok。
正如前面所说的,如果使用very magic模式的话,这些命令都将大大简化,因为我们可以省略掉大量的转义字符,以:%s/\%(my\)sql\(ok\)/\1为例,它可以替换成%s/\v%(my)sql(ok)/\1,是不是清晰很多了呢.




"/*========================================*\
"               常用指令收集
"\==========================================/
"   系统时间
"   :map <F7> a<C-R>=strftime("%c")<CR><esc>
"   :s/__date__/\=strftime("%c")/

"/*---------------------------------------*\
"               基础命令
"/*---------------------------------------*\
"   ctrl+q              可以联合复制，粘贴，替换用 行操作
"   ctrl+w+j ctrl+w+k (:bn :bp :bd)

"   '.                  它移动光标到上一次的修改行
"   `.                  它移动光标到上一次的修改点
"   .                   重复上次命令
"   <C-O> :             依次沿着你的跳转记录向回跳 (从最近的一次开始)
"   <C-I> :             依次沿着你的跳转记录向前跳
"   ju(mps) :           列出你跳转的足迹
"   :history :          列出历史命令记录
"   :his c :            命令行命令历史
"   :his s :            搜索命令历史
"   q/ :                搜索命令历史的窗口
"   q: :                命令行命令历史的窗口
"   g ctrl+g            计算文件字符
"   {,}                 前进至上一段落前进至后一段落
"   gg,G(2G)            文件首
"   gd dw gf ga(进制转化)
"   gg=G 全篇自动缩进 , =G 单行缩进

"  ci[ 删除一对 [] 中的所有字符并进入插入模式
"  ci( 删除一对 () 中的所有字符并进入插入模式
"  ci< 删除一对 <> 中的所有字符并进入插入模式
"  ci{ 删除一对 {} 中的所有字符并进入插入模式
"  cit 删除一对 HTML/XML 的标签内部的所有字符并进入插入模式
"  ci” ci’ ci` 删除一对引号字符 (” 或 ‘ 或 `) 中所有字符并进入插入模式
"
"  vi[ 选择一对 [] 中的所有字符
"  vi( 选择一对 () 中的所有字符
"  vi< 选择一对 <> 中的所有字符
"  vi{ 选择一对 {} 中的所有字符
"  vit 选择一对 HTML/XML 的标签内部的所有字符
"  vi” vi’ vi` 选择一对引号字符 (” 或 ‘ 或 `) 中所有字符

"   crl+] 函数原型处 crl+t 回 ( ctags )
"   ctl+p 自动补全( 编辑状态 )
"   :X 加密保存( 要输入密码 )
"   ? /         (N n)
"   f(F,t) 查找字符
"   w(e) 移动光标到下一个单词.
"   5fx 表示查找光标后第 5 个 x 字符.
"   5w(e) 移动光标到下五个单词.

"   b 移动光标到上一个单词.
"   0 移动光标到本行最开头.
"   ^ 移动光标到本行最开头的字符处.
"   $ 移动光标到本行结尾处.
"   H 移动光标到屏幕的首行.
"   M 移动光标到屏幕的中间一行.
"   L 移动光标到屏幕的尾行.

"   c-f (即 ctrl 键与 f 键一同按下)
"   c-b (即 ctrl 键与 b 键一同按下) 翻页
"   c-d (下半页) c-u(上半页) c-e (一行滚动)
"   zz 让光标所在的行居屏幕中央
"   zt 让光标所在的行居屏幕最上一行
"   zb 让光标所在的行居屏幕最下一行


"   在 vi 中 y 表示拷贝, d 表示删除, p 表示粘贴. 其中拷贝与删除是与光标移动命令
"   yw 表示拷贝从当前光标到光标所在单词结尾的内容.
"   dw 表示删除从当前光标到光标所在单词结尾的内容.
"   y0 表示拷贝从当前光标到光标所在行首的内容.
"   d0 表示删除从当前光标到光标所在行首的内容.
"   y$(Y) 表示拷贝从当前光标到光标所在行尾的内容.
"   d$(D) 表示删除从当前光标到光标所在行尾的内容.
"   yfa 表示拷贝从当前光标到光标后面的第一个a字符之间的内容.
"   dfa 表示删除从当前光标到光标后面的第一个a字符之间的内容.
"   s(S),a(A),x(X),D
"   yy 表示拷贝光标所在行.
"   dd 表示删除光标所在行.

"   5yy 表示拷贝光标以下 5 行.
"   5dd 表示删除光标以下 5 行.
"   y2fa 表示拷贝从当前光标到光标后面的第二个a字符之间的内容.
"   :12,24y 表示拷贝第12行到第24行之间的内容.
"   :12,y 表示拷贝第12行到光标所在行之间的内容.
"   :,24y 表示拷贝光标所在行到第24行之间的内容. 删除类似.
"   TAB 就是制表符, 单独拿出来做一节是因为这个东西确实很有用.
"   << 输入此命令则光标所在行向左移动一个 tab.
"   >> 输入此命令则光标所在行向右移动一个 tab.
"   5>> 输入此命令则光标后 5 行向右移动一个 tab.
"   :5>>(>>>) :>>(>>>)5
"   :12,14> 此命令将12行到14行的数据都向右移动一个 tab.
"   :12,14>> 此命令将12行到14行的数据都向右移动两个 tab.
"   >>   Indent line by shiftwidth spaces
"   <<   De-indent line by shiftwidth spaces
"   5>>  Indent 5 lines
"   5==  Re-indent 5 lines
"
"   >%   Increase indent of a braced or bracketed block (place cursor on brace first)
"   =%   Reindent a braced or bracketed block (cursor on brace)
"   <%   Decrease indent of a braced or bracketed block (cursor on brace)
"   ]p   Paste text, aligning indentation with surroundings
"
"   =i{  Re-indent the 'inner block', i.e. the contents of the block
"   =a{  Re-indent 'a block', i.e. block and containing braces
"   =2a{ Re-indent '2 blocks', i.e. this block and containing block
"
"   >i{  Increase inner block indent
"   <i{  Decrease inner block indent
"   :set shiftwidth=4 设置自动缩进 4 个空格, 当然要设自动缩进先.
"   :set sts=4 即设置 softtabstop 为 4. 输入 tab 后就跳了 4 格.
"   :set tabstop=4 实际的 tab 即为 4 个空格, 而不是缺省的 8 个.
"   :set expandtab 在输入 tab 后, vim 用恰当的空格来填充这个 tab.
"   :g/^/exec 's/^/'.strpart(line('.').' ', 0, 4) 在行首插入行号
"   set ai 设置自动缩进
"   5ia<esc> 重复插入5个a字符

"/ --------------------------------------- \
"               替换命令
"/ --------------------------------------- \
"   替换文字 2009-02-34 ----> 2009-02-34 00:00:00
"   :%s/\(\d\{4\}-\d\{2\}-\d\{2\}\)/\1 00:00:00/g

"  :%s/^/heaser/     在每一行头部添加header
"  :%s/$/ender/     在每一行尾部添加ender

"   :s/aa/bb/g              将光标所在行出现的所有包含 aa 的字符串中的 aa 替换为 bb
"   :s/\/bb/g               将光标所在行出现的所有 aa 替换为 bb, 仅替换 aa 这个单词
"   :%s/aa/bb/g             将文档中出现的所有包含 aa 的字符串中的 aa 替换为 bb
"   :12,23s/aa/bb/g         将从12行到23行中出现的所有包含 aa 的字符串中的 aa 替换为 bb
"   :12,23s/^/#/            将从12行到23行的行首加入 # 字符
"   :%s/fred/joe/igc            一个常见的替换命令，修饰符igc和perl中一样意思
"   s/dick/joe/igc则        对于这些满足条件的行进行替换

"   :g/^\s*$/d              空行(空格也不包含)删除.
"   :%s/\r//g               删除DOS方式的回车^M
"   :%s/ *$//               删除行尾空白(%s/\s*$//g)
"   :g!/^dd/d               删除不含字符串'dd'开头的行
"   :v/^dd/d                同上,译释：v == g!，就是不匹配！
"   :v/./.,/./-1join        压缩空行(多行空行合并为一行)
"   :g/^$/,/./-j            压缩空行(多行空行合并为一行)
"   :g/^/pu _               把文中空行扩增一倍 (pu = put),原来两行间有一个空行，现在变成2个
"   :g/^/m0                 按行翻转文章 (m = move)
"   :g/fred/,/joe/d         not line based (very powerfull)
"   :g/<input\|<form/p      或者 要用\|
"   :g/fred/t$              拷贝行，从fred到文件末尾(EOF)

"   :%norm jdd              隔行删除,译释：%指明是对所有行进行操作,norm指出后面是normal模式的指令,j是下移一行，dd是删除行

"   :'a,'bg/fred/s/dick/joe/igc   ('a,'b指定一个范围：mark a ~ mark b)
"   g//用一个正则表达式指出了进行操作的行必须可以被fred匹配,g//是一个全局显示命令

"   /joe/e                  光标停留在匹配单词最后一个字母处
"   /joe/e+1                光标停留在匹配单词最后一个字母的下一个字母处
"   /joe/s                  光标停留在匹配单词第一个字母处
"   /^joe.*fred.*bill/      标准正则表达式
"   /^[A-J]\+/              找一个以A~J中一个字母重复两次或以上开头的行
"   /forum\(\_.\)*pent      多行匹配
"   /fred\_s*joe/i          中间可以有任何空白，包括换行符\n
"   /fred\|joe              匹配FRED或JOE
"   /\<fred\>/i             匹配fred,fred必须是一个独立的单词，而不是子串
"   /\<\d\d\d\d\>           匹配4个数字 \<\d\{4}\>

"   列，替换所有在第三列中的str1
"   :%s:\(\(\w\+\s\+\)\{2}\)str1:\1str2:
"   交换第一列和最后一列 (共4列)
"   :%s:\(\w\+\)\(.*\s\+\)\(\w\+\)$:\3\2\1:

"   全局(global)显示命令，就是用 :g＋正则表达式
"   译释： :g/{pattern}/{cmd} 就是全局找到匹配的,然后对这些行执行命令{cmd}
"   :g/\<fred\>/                                显示所有能够为单词fred所匹配的行
"   :g/<pattern>/z#.5                           显示内容，还有行号
"   :g/<pattern>/z#.5|echo '=========='         漂亮的显示

"/ --------------------------------------- \
"           多文档操作 (基础)
"/ --------------------------------------- \
"    用 :ls! 可以显示出当前所有的buffer
"   :bn                 跳转到下一个buffer
"   :bp                 跳转到上一个buffer
"   :wn                 存盘当前文件并跳转到下一个
"   :wp                 存盘当前文件并跳转到上一个
"   :bd                 把这个文件从buffer列表中做掉
"   :b 3                跳到第3个buffer
"   :b main             跳到一个名字中包含main的buffer

"/ --------------------------------------- \
"           列复制
"/ --------------------------------------- \
"   译注：@#%&^#*^%#$!
"   :%s= [^ ]\+$=&&= : 复制最后一列
"   :%s= \f\+$=&&= : 一样的功能
"   :%s= \S\+$=&& : ft,还是一样
"   反向引用，或称记忆
"   :s/\(.*\):\(.*\)/\2 : \1/ : 颠倒用:分割的两个字段
"   :%s/^\(.*\)\n\1/\1$/ : 删除重复行
"   非贪婪匹配，\{-}
"   :%s/^.\{-}pdf/new.pdf/ : 只是删除第一个pdf
"   跨越可能的多行
"   :%s/<!--\_.\{-}-->// : 又是删除多行注释（咦？为什么要说「又」呢？）
"   :help /\{-} : 看看关于 非贪婪数量符 的帮助
"   :s/fred/<c-r>a/g : 替换fred成register a中的内容，呵呵
"   写在一行里的复杂命令
"   :%s/\f\+\.gif\>/\r&\r/g | v/\.gif$/d | %s/gif/jpg/
"   译注：就是用 | 管道啦

"/ --------------------------------------- \
"           大小写转换
"/ --------------------------------------- \
"   g~~ : 行翻转
"   vEU : 字大写(广义字)
"   vE~ : 字翻转(广义字)
"   ~   将光标下的字母改变大小写
"   3~  将下3个字母改变其大小写
"   g~w 字翻转
"   U   将可视模式下的字母全改成大写字母
"   gUU 将当前行的字母改成大写
"   u   将可视模式下的字母全改成小写
"   guu 将当前行的字母全改成小写
"   gUw 将光标下的单词改成大写。
"   guw 将光标下的单词改成小写。


"   文件浏览
"   :Ex : 开启目录浏览器，注意首字母E是大写的
"   :Sex : 在一个分割的窗口中开启目录浏览器
"   :ls : 显示当前buffer的情况
"   :cd .. : 进入父目录
"   :pwd
"   :args : 显示目前打开的文件
"   :lcd %:p:h : 更改到当前文件所在的目录
"    译释：lcd是紧紧改变当前窗口的工作路径，% 是代表当前文件的文件名,
"    加上 :p扩展成全名（就是带了路径），加上 :h析取出路径
