Makefile note
=============

# make 参数

可以用 make 的参数来盖过 Makefile 里，用变数所指定的参数。例：

make CFLAGS="-g -O2"

您可以使用 override 来避免在 Makefile 里的变量的值被 make 的参数所取代。例：

override CFLAGS = -Wall -g

可以在 make 后指定要重新建立的 target。例：

make clean

以上会执行 Makefile 中的 clean 区段。


# 内部变量

|  选项  | 含义          |
| ------ | ------------- |
|  `$<`  | 代表第一个依赖的值。 |
|  `$^`  | 代表所有依赖的值。 |
|  `$+`  | 代表所有依赖的值(不去重的结果)。 |
|  `$?`  | 代表已被更新的依赖的值。也就是依赖中，比 targets 还新的值。 |
|  `$@`  | 代表 targets 的值。 |
|  `$*`  | 代表 targets 所指定的文件名，但不包含扩展名。 |


下例可帮助理解变量的含义：

```bash
print.o: foo1.c foo2.c foo3.c
	@echo "\$$?" $?
	@echo "\$$@" $@
	@echo "\$$*" $*
	@echo "\$$^" $^
	@echo "\$$<" $<
	@echo "\$$+" $+
	touch print.o

foo3.c: foo.c
	@echo $$RANDOM > $@

.PHONY: foo3.c
```

输出结果如下：
```
$? foo3.c
$@ print.o
$* print
$^ foo1.c foo2.c foo3.c
$< foo1.c
$+ foo1.c foo2.c foo3.c foo1.c
touch print.o
```

`$(VAR:<pat1>=<pat2>)`  替换

# 函数

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  if            | `$(if <condition>, <then>, <else>)` |
|  foreach       | `$(foreach <iter>, <list split by space>, <command>)` |
|  filter        | `$(filter <pattern1, 2, 3...>, <text>)` |
|  filter-out    | `$(filter-out <pattern1, 2, 3...>, <text>)` |
|  addprefix     | `$(addprefix <prefix>, <name1, 2, 3...>)` |
|  addsuffix     | `$(addsuffix <suffix>, <name1, 2, 3...>)` |
|  wildcard      | `$(wildcard <pattern1, 2, 3...>)` |
|  call          | `$(call <expression>, <param1>, <param2>, ...)` |
|  patsubst      | `$(patsubst <pattern_from>, <pattern_to>, <text>)` |
|  subst         | `$(subst <pattern_from>, <pattern_to>, <text>)` |
|  shell         | `$(shell <command_and_arguments>)` |

```makefile
listfile = $(filter $(if $(2), $(addprefix %.,$(2)),%), $(wildcard $(addsuffix $(SLASH)*, $(1))))
list_cc = $(call listfile, src, c cpp)
```

宏定义，与shell不同，**赋值号前后必须加空格**, 如：MACRO = value
":="与"="的区别是，":="赋值的变量是依执行顺序展开的，而"="则是以最后一次赋值展开
?= 条件赋值
+= 追加赋值

#Makefile




#Makefile
a.out : sub1.o sub2.o
            cc -o a.out sub1.o sub2.o
#suffix rule (.c->.o)
 .c.o:
        cc -c $<
sub1.o : header.h        #不是依存于.c，而是依存于.o
sub1.o : header.h

• 单独make会执行第一个目标进行构建
• 变量与bash不同，需要用括号括起，如：$(var)
• .PHONY 不需要依赖的目标，即依赖未发生变化时也会被执行
• .PHONY 建议写在其依赖的目标前面

ifeq / ifneq ($(var), TRUE)
    …
else
 ...
endif



Makefile 语法简介

注释同shell，以 # 开头


define  x
……
endef


1.SOURCE = $(wildcard *.c) //返回值为当前目录下所有.c源文件列表
$(wildcard PATTERN)
函数名称：获取匹配模式文件名函数-wildcard函数功能：列出当前目录下所有符合模式“PATTERN”格式的文件名。
返回值：空格分割的、存在当前目录下的所有符合模式“PATTERN”的文件名。函数说明：“PATTERN”使用shell可识别的通配符，包括“?”（单字符）、“*”（多字符）等。示例：
$(wildcard *.c)返回值为当前目录下所有.c源文件列表。
 $(patsubst PATTERN,REPLACEMENT,TEXT) 函数名称：模式替换函数—patsubst。

2.OBJS = $(patsubst %.c,%.o,$(SOURCE)) //把字串$(SOURCE)中以.c结尾的单词替换成以.o结尾的字符。函数的返回结果是.O的文件
$(patsubst PATTERN,REPLACEMENT,TEXT)
函数名称：模式替换函数—patsubst。
函数功能：搜索“TEXT”中以空格分开的单词，将符合模式“PATTERN”替换为“REPLACEMENT”。参数“PATTERN”中可以使用模式通配符“%” 来代表一个单词中的若干字符。如果参数“REPLACEMENT”中也包含一个“%”，那么“REPLACEMENT”中的“%”将是“PATTERN”中的那个“%”所代表的字符串。
在“PATTERN”和“REPLACEMENT”中，只有第一个“%”被作为模式字符来处理，之后出现的不再作模式字符（作为一个字符）。在参数中如果需要将第一个出现的“%”作为字符本身而不作为模式字符时，可使用反斜杠“\”进行转义处理（转义处理的机制和使用静态模式的转义一致)
 返回值：替换后的新字符串。 函数说明：参数“TEXT”单词之间的多个空格在处理时被合并为一个空格，并忽略前导和结尾空格。 示例：
 $(patsubst %.c,%.o,x.c bar.c) 把字串“x.c bar.c”中以.c结尾的单词替换成以.o结尾的字符。函数的返回结果是“x.o bar.o”

3.CROSS_COMPILE = //交叉编译变量
4.CXX = gcc //gcc为C语言编译器、g++为c++编译器
5.CFLAGS += -D__DEBUG__ //+= 向后添加有空格。增加调试信息D_DEBUG_
6.CLFAGS += -Wall //增加警告信息
7.LDFLAGS += -lm //增加链接到math库
8.all:bts //指定执行一个由伪目标定义的若干条命令或者一个空目标文件all 作为Makefile的顶层目标，一般此目标作为默认的终极目标。
9.bts:$(OBJS) //bits是终极目标它依赖于所有的.o文件
10.$(CROSS_COMPILE)$(CXX) -Wall $(LDFLAGS) -o $@ $^
//根据实际的编译器选择变量-o $@：生成目标文件的完整名称
$^:依赖所有的依赖$(OBJS)

11..PHONY:clean
clean:
rm -f *.o *.d bts //定义伪目标删除所有的.o .d 和生成的执行目标。
所有的.d文件依赖于同名的.c文件。.d文件里包含了.c所依赖的头文件信息
将一个目标声明为伪目标的方法是将它作为特殊目标.PHONY”的依赖。.PHONY : clean 这样目标“clean”就被声明为一个伪目标，无论在当前目录下是否存在“clean”这个文件。我们输入“make clean”之后。“rm”命令都会被执行。而且，当一个目标被声明为伪目标后，make在执行此规则时不会去试图去查找隐含规则来创建它。这样也提高了make的执行效率，同时也不用担心由于目标和文件名重名而使我们的期望失败。在书写伪目标规则时，首先需要声明目标是一个伪目标，之后才是伪目标的规则定义。目标“clean”的完整书写格式应该如下： .PHONY: clean
clean:
 rm *.o temp

12.include $(SOURCE:.c=.d) //删除临时文件:在 Makefile 中书写一个伪目标“depend”的规则来定义自动产生依赖关系文件的命令。输入“make depend”将生成一个称为“depend”的文件，其中包含了所有源文件的依赖规则描述。Makefile中使用“include”指示符包含这个文件。Makefile中对当前目录下.d文件处理可以参考如下： sources = foo.c bar.c sinclude $(sources:.c=.d) 例子中，变量“sources”定义了当前目录下的需要编译的源文件。变量引用置换“$(sources : .c=.d)”的功能是根据变量“source”指定的.c文件自动产生对应的.d文件，并在当前Makefile文件中包含这些.d文件。

13.%.o:%.c
$(CROSS_COMPILE)$(CXX) -Wall $(CFLAGS) -c $< -o $@
//模式规则的格式为： %.o : %.c ; COMMAND...
此规则描述了一个.o文件如何由对应的.c文件创建。
首先看编译.c文件到.o文件的隐含模式规则：
 %.o : %.c
$(CC) -c $(CFLAGS) $(CPPFLAGS) $< -o $@ 规则的命令行中使用了自动化变量“$<”和“$@”，其中自动化变量“$<”代表规则的依赖，“$@”代表规则的目标。此规则在执行时，命令行中的自动化变量将根据实际的目标和依赖文件取对应值

14.%.d: %.c
@set -e; rm -f $@; \
$(CXX) -MM $(CFLAGS) $< > $@.; \
sed 's,$*\.o[ :]*,\1.o $@ : ,g' < $@. > $@; \
rm -f $@.
//自动生成每一个.c文件对应的.d文件.此规则的含义是：所有的.d文件依赖于同名的.c文件。


§ 在惯例上，Makefile 内部使用的变量名称使用小写；而使用者很可能从命令行自行另外指定数值的变量，像是 CFLAGS，则是使用大写。

在 Makefile 中，可利用 $(MACRO) 或 ${MACRO} 来存取已定义的变量。例：

targets = foo
$(targets): common.h
    gcc -o $(targets) foo.c

效果等同：

foo: common.h
    gcc -o foo foo.c

注意到，make 会将整个 Makefile 展开后，再决定变数的值。也就是说，变量的值将会是整个 Mackfile 中最后被指定的值。例：



注意到在上例中使用了 $$，让 '$' 能传到 Shell 中。
在 target 里另外指定变量的值，可以在 target 里另外指定变量的值。例：

foo = abc

all: foo = xyz
all:
        echo $(foo)
        # 此时，foo 的值为 xyz

以下的语法提供了和上例相同的功能：

all: override foo = xyz

all: export foo = xyz

make 也可以存取环境变量。例：

all:
    @echo $(CFLAGS)

在上例中，虽然在 Makefile 里虽然没有指定 CFLAGS 的值，但 make 会试图以环境变量来代出 CFLAGS 的值。

可搭配 wildcard 指令在变量里展开 * ? [...] 等通配符。例：

objects=$(wildcard *.o)

规则：（Rule）

指示 make 如何进行编译。

主要语法：

target: dependencies
<Tab>Commands

或

target: dependencies; Commands
<Tab>Commands

Rule 指示了 make 如何建立 target；及何时要重新建立 target。

target：所要建立的档案
dependencies：相依项目。make 会据此决定是否要重新编译 target。
Commands：建立 target 的指令。

在 Makefile 里并没有限定 Rule 的先后顺序。但默认上，make 会参考 all 这个目标项目，并依据它的 dependencies 来决定要建立哪些项目。若没有 all 项目，则会采用 Makefile 里的第一个项目。

target：（目标项目）

这个项目所要建立的档案，必须以 : 结尾。例：

foo.o: common.h
    gcc -c foo.c

其中，foo.o 是这个项目要建立的档案；common.h 是相依性的项目/档案；而 gcc -c foo.c 则为要产生这个项目所要执行的指令。

make 在编译时，若发现 target 比较新，也就是 dependencies 都比 target 旧，那么将不会重新建立 target，如此可以避免不必要的编译动作。

若该项目并非档案，则为 fake 项目。如此一来将不会建立 target 档案。但为了避免 make 有时会无去判断 target 是否为档案或 fake 项目，建议利用 .PHONY 来指定该项目为 fake 项目。例：

.PHONY: clean
clean:
    rm *.o

在上例中，若不使用 .PHONY 来指定 clean 为 fake 项目的话，若目录中同时存在了一个名为 clean 的档案，则 clean 这个项目将被视为要建立 clean 这个档案，但 clean 这个项目却又没有任何的 dependencies，也因此，clean 项目将永远被视为 up-to-date，永远不会被执行。

因为利用了 .PHONY 来指定 clean 为 fake 项目，所以 make 不会去检查目录中是否存在了一个名为 clean 的档案。如此也可以提升 make 的执行效率。

其它类以 .PHONY 的语法请参考：

GNU `make': 4.9 Special Built-in Target Names

另外，如果某个非 fake 项目里的 dependencies 包含了 fake 项目的话，因为 make 一定会执行 fake 项目，这样一来，这个非 fake 项目一定也会被执行。这可能不是理想的做法。

dependencies：（相依性项目，以空白间隔）

dependencies 是指定在建立 target 之前，必须先检查的项目。可以不指定。例：

foo.o: common.h
    gcc -c foo.c

上例中是指：检查 common.h。如果它的建立日期比 foo.o 新，就执行 gcc -c foo.c 来重新产生 foo.o。也就是说，可以依需求建立 dependencies，即使它和 target 一点关系也没有。

相依性项目可以是 Makefile 中其它的 target。也因此，在建立该 target 之前，它会先检查在 dependencies 里所指定的所有 target。

Commands：（即为要执行的 Shell 指令）

必须以 <Tab> 开头。使用 Shell Script 语法。在 Makefile 里，只要以 <Tab> 开头都将会被视为 Shell Script 执行。

每条法则必须写在同一行。每条 Command 会启动一个新的 Shell，预设为 /bin/sh。若执行完某条 Command 但传回了错误值，make 就会中断执行。

因为每条 Command 会启动一个新的 Shell，所以有时执行的指令必须写在同一行，像是使用 if 来进行条件判断，此时可以用 ; 来分隔指令。例：

all:
    if [ -f foo ];
        then rm foo;
    fi

而以下是错误示范：

all:
    cd subdir; $(MAKE)

这时因为 make 只会检查最后一个指令的传回值，所以在以上指令中，即使 subdir 不存在，但 make 并不会因而中断执行，并会继续执行 $(MAKE) 指令，而产生了不可预期的结果。

为了避免这个问题，可以利用 && 来检查其中某个指令是否成功执行，再决定是否执行下个指令。例：

all:
    cd subdir && $(MAKE)

特别字符：

@：不要显示执行的指令。

-：表示即使该行指令出错，也不会中断执行。

例：

.PHONY: clean
clean:
    @echo "Clean..."
    -rm *.o

因为 make 会一行一行将正在执行的 Commands 显示在屏幕上，但您可以利用 @ 来暂时关闭这个功能。

而 make 只要遇到任何错误就会中断执行。但像是在进行 clean 时，也许根本没有任何档案可以 clean，因而 rm 会传回错误值，因而导致 make 中断执行。我们可以利用 - 来关闭错误中断功能，让 make 不会因而中断。

隐性法则：

在上例中的：

foo.o: common.h
    gcc -c foo.c

由于产生 foo.o 的指令就是 gcc -c foo.c，因此在 Makefile 里可以将其简化为：

foo.o: common.h

此时 make 会依据 target 的扩展名来猜测该如何编译 target。如此可以让 Makefile 更为简洁。

您可以利用【空白指令】来避免 make 依据隐性法则而进行编译。例：

foo.o: common.h
<Tab>


内部函数：

您可以在 Makefile 使用 make 所支持的一些内部函数。详情请参考：

GNU `make': 8 Functions for Transforming Text

条件判断：

可以在 Makefile 中使用以下的条件判断语法。但由于它们不是 rule，所以不可以 <Tab> 开头；但其后要执行的指令则必须以 <Tab> 开头，make 才会视其为 Shell 指令。

ifeq：（检查 value1, value2 是否相等）

ifeq (value1, value2)
    ...
else
    ...
endif

ifneq：（提供和 ifeq 相反的功能）

ifneq (value1, value2)
    ...
else
    ...
endif

ifdef：（检查 variable 变量是否为空的）

ifdef variable
    ...
else
    ...
endif


ifndef：（提供和 ifdef 相反的功能）

ifdef variable
    ...
else
    ....
endif

引入文件：

将外部档案引入 Makefile 中。可以视为直接在此将该档案全数插入 Makefile 中。

例：

include foo.in

将 foo.in 的内容全数引入 Makefile 里。

可以同时引入多个档案、使用变量 $(MACRO) 或是使用通配符（* ? 或 [...]）。例：

include foo.in common*.in $(MAKEINCS)

子目录：

如果该项目有多个目录，且每一个目录中都有 Makefile，则利用以下指令来进入子目录并进行编译：

cd dir;$(MAKE)



### Example 1

```Makefile
SUBDIRS = dir1 dir2 dir3
all:
  for i in $(SUBDIRS); do
    (cd $$i; make);
  done

clean:
  for i in $(SUBDIRS); do
    (cd $$i; make clean);
  done

install:
  for i in $(SUBDIRS); do
    (cd $$i; make install);
  done
```

### Example 2

```Makefile
HOME_PATH:=/Users/cosim
PROXY_FILE:=route_broker_proxy.thrift
ITS_THRIFT_PATH:=$(HOME_PATH)/workspace/route-broker-go/src/route-broker/vendor/its-thrift/src
ITS_OUTPUT_PATH:=$(HOME_PATH)/workspace/its-thrift-gen/py
sys = $(uname)


all: clean prepare build tideup
.PHONY: all

clean:
  @echo "clean its"
  rm -rf its

prepare:
  @echo "prepare"
  cp $(PROXY_FILE) $(ITS_THRIFT_PATH)
  @echo ""

build:
  @echo "build idl in python"
ifeq ($(sys), Linux)
  src-thrift.sh
else
  build-idl.sh
endif
  @echo "output idl source"
  cp -r $(ITS_OUTPUT_PATH) ./its

tideup:
  @echo "tideup"
  rm $(ITS_THRIFT_PATH)/$(PROXY_FILE)
```


### Example 3
```Makefile
CFLAGS:=-I/usr/local/include/qt -fPIC
LINKOPT:=-Wl,-no-as-needed
LIBS:=-L/usr/lib -lQt5Widgets -lQt5Core -lstdc++ -lc -lQt5Gui -lm -lgcc_s
BUILD_DIR:=build

%.o: %.cc prepare
 gcc $(CFLAGS) -c $< -o $(BUILD_DIR)/$@

SRCS := $(wildcard *.cc)
OBJS := $(SRCS:%.cc=%.o)

run: main
 cd $(BUILD_DIR) && ./main

main: $(OBJS)
 cd $(BUILD_DIR) && gcc -o main $(LINKOPT) $(LIBS) $^

prepare:
 mkdir -p $(BUILD_DIR)

clean:
 rm -rf $(BUILD_DIR)
```


