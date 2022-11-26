Gdb note
========

**命令目录**

b break，设断点，后跟**行号(+/-行号)**或**函数**，后可加文件名行号、if等，eg: b main.cpp:8 if x=10 && y=10

   tb tbreak，临时断点，只断一次

   rb rbreak，正则断点，通过正则表达确定断点函数


| 断点表达     | 含义          |
| ------------ | ------------- |
| src.c:lineno |  |
| src.c:func   |  |
| 0xN          |  |
| +/-lineno    |  |



watch watchpoint，内存断点

watch <expr>

| 断点表达     | 含义          |
| ------------ | ------------- |
| *0x0.... |  |
| *ptr   |  |
| ptr          |  |

| 内存断点类型   | 含义          |
| -------------- | ------------- |
| watch <expr>   | 改变就停止    |
| rwatch <expr>  | 读取就停止    |
| awatch <expr>  | 访问就停止    |

catch syscall <no> 对系统调用下断点，调用号见 #/usr/include/asm/unistd_64.h or unistd_32.h

   如: catch一个exception，assert，signal，fork甚至syscall

   tcatch, 临时catch点

| event 事件                    | 含 义                                                        |
| :---------------------------- | :----------------------------------------------------------- |
| throw [exception]             | 当程序中抛出 exception 指定类型异常时，程序停止执行。如果不指定异常类型（即省略 exception），则表示只要程序发生异常，程序就停止执行。 |
| catch [exception]             | 当程序中捕获到 exception 异常时，程序停止执行。exception 参数也可以省略，表示无论程序中捕获到哪种异常，程序都暂停执行。 |
| load [regexp] unload [regexp] | 其中，regexp 表示目标动态库的名称，load 命令表示当 regexp 动态库加载时程序停止执行；unload 命令表示当 regexp 动态库被卸载时，程序暂停执行。regexp 参数也可以省略，此时只要程序中某一动态库被加载或卸载，程序就会暂停执行。 |



trace tracepoint，轨迹点，

checkpoint 进程快照，执行后生成一个快照点

   restart xxx; checkpoint no

\#断点保存

save breakpoints file #保存断点

save tracepoint file #保存trace点

source file #加载断点

gdb cmd -x file #启动时加载断点

类似的还有

save tracepoints file

save gdb-index



bt backtrace，列出调用栈，列出n层栈

c continue，继续从断下位置执行

d delete，删除断点，eg: d breakpoint 1

f frame，n是一个从0开始的整数，是栈中的层编号。比如：frame 0，表示栈顶，frame 1，表示栈的第二层。

i info，列出信息：

i args: 查看当前桢中的参数;

i break: 查看断点,也作：i b ;

i checkpoint:

i catch: 查看当前桢中的异常处理器;

i locals: 查看当前桢中的局部变量;

i reg: 查看寄存器的值，也作：i r ;

i stack: 也作: i s， =bt;

i threads:列出线程，也作：i thr

i sharedlibrary: 列出so

i signals: 显示信息

i os:

Type Description
cpus Listing of all cpus/cores on the system
files Listing of all file descriptors
modules Listing of all loaded kernel modules
msg Listing of all message queues
processes Listing of all processes
procgroups Listing of all process groups
semaphores Listing of all semaphores
shm Listing of all shared-memory regions
sockets Listing of all internet-domain sockets
threads Listing of all threads



l list可列出代码[附带行数,函数名]

n next，单步执行，ni 指令级单步执行

s step，单步步入，si 指令级单步步入

set step-mode on 打开step-mode模式，于是，在进行单步跟踪时，程序不会因为没有debug信息而不停住。这个参数有很利于查看机器码。

p print，打印变量的值

p/f f可用于指定格式：

| 格式 | 说明                                        |
| ---- | ------------------------------------------- |
| x    | 显示为十六进制数                            |
| d    | 显示为十进制数                              |
| u    | 显示为无符号十进制数                        |
| o    | 显示为八进制数                              |
| t    | 显示为二进制数                              |
| a    | 显示为地址                                  |
| c    | 显示为字符（ASCII）                         |
| f    | 显示为浮点小数                              |
| s    | 显示为字符串                                |
| i    | 显示为机器语言（仅在显示内存的x命令中可用） |

@
是一个和数组有关的操作符，在后面会有更详细的说明。
::
指定一个在文件或是一个函数中的变量。
{<type>} <addr>
表示一个指向内存地址的类型为type的一个对象。

q quit，退出

r run，重新运行，可以追加参数，eg: r ...

t thread，切换至线程，eg: t 12

**thread apply all bt** #打印所有线程的调用栈，all还可以换作线程号范围

trace, 设置轨迹点

tstart 开始轨迹录制

tstop 停止轨迹录制

tstatus 显示当前追迹数据状态

tfind 选择一个轨迹帧

return: 强制函数返回。可以指定返回值
finish 执行到当前函数返回

until 执行到当前循环完成。可简写为u

set var x=10 改变当前变量x的值。也可以这样用：set {int}0x83040 = 10把内存地址0x83040的值强制转换为int并赋值为10
jump使当前执行的程序跳转到某一行，或者跳转到某个地址。由于只会使程序跳转而不会改变栈值，因此若跳出函数到另外的地方 会导致return出错。另外，熟悉汇编的人都知道，程序运行时，有一个寄存器用于保存当前代码所在的内存地址。所以，jump命令也就是改变了这个寄存器中的值。于是，你可以使用“set $pc”来更改跳转执行的地址。如： set $pc = 0x485

attach 吸附指定PID的进程，attach 1234

detach 断开吸附

disassem $pc 反汇编当前函数。简写为：disas $pc

finish 执行完当前函数

\# 端口调试

gdbserver <gdb-IP>:<port> <bin>

$ gdb

target remote <remote-IP>:<port>



<C-c> 用于调试时暂停程序

<C-z> 用于挂起程序

# 远程调试
## 串口调试

运行端
```
gdbserver <gdb-IP>:<port> <bin> /dev/ttyS0
```
调试端
```
$ gdb
set remotedevice /dev/ttyS0 # 这里设置串口1
set remote baud 9600 # 这里设置串口波特率
set debug remote 1 #可选
target remote /dev/ttyS0
```



generate-core-file 手动core dump，也作：gcore

~/.gdbinit # gdb的配置文件

Core Dump（吐核）配置

默认路径：/cores/

`/proc/sys/kernel/core_pattern`

| 格式符号 | 说明                                     |
| -------- | ---------------------------------------- |
| %%       | %字符本身                                |
| %p       | 被转储进程的进程ID(PID)                  |
| %u       | 被转储进程的真是用户ID(UID)              |
| %g       | 被转储进程的真是组(GID)                  |
| %s       | 引发转储的信号编号                       |
| %t       | 转储时间，unix时间戳                     |
| %h       | 主机名                                   |
| %e       | 可执行文件的名称                         |
| %c       | core的大小上限(内核版本2.6.24以后可使用) |

e.g. :

```
|/usr/local/bin/core_filter -p %p -e %e -t %t -s 102400
```

注意前面的“|”表示通过前面的程序计算core的文件名

设置core大小上限：

ulimit -c 0

ulimit -c 1000

-c 指定修改core文件的大小，1000指定了core文件大小。也可以对core文件的大小不做限制，如：

ulimit -c unlimited

# 加载core文件

```
gdb <exec file> core.<pid>
(gdb) where
```

# 连接代码

```
set substitute-path <origin-path> <dest-path>
show substitute-path   #绝对路径
dir <root-path>  #相对路径
set auto-load safe-path <root-path/prefix>
```

\#

```
set args ..... # 设置启动参数
set environment variable=.... # 设置环境变量

unset ...
```

```
(gdb) info signals
Signal Stop Print Pass to program Description
SIGHUP Yes Yes Yes Hangup
SIGINT Yes Yes No Interrupt
SIGQUIT Yes Yes Yes Quit
SIGILL Yes Yes Yes Illegal instruction
SIGTRAP Yes Yes No Trace/breakpoint trap
SIGABRT Yes Yes Yes Aborted
SIGEMT Yes Yes Yes Emulation trap
SIGFPE Yes Yes Yes Arithmetic exception
SIGKILL Yes Yes Yes Killed
```
其中各列的含义分别为：
Signal：各个信号的名称；
Stop：当信号发生时，是否终止程序执行。Yes 表示终止，No 表示当信号发生时程序认可继续执行；
Print：当信号发生时，是否要求 GDB 打印出一条提示信息。Yes 表示打印，No 表示不打印；
Pass：当信号发生时，该信号是否对程序可见。Yes 表示程序可以捕捉到该信息，No 表示程序不会捕捉到该信息；
Description：对信号所表示含义的简单描述。

(gdb) signal SIGCONT # 发SIGCONT信号

\# layout 模式

layout

layout cmd

layout src

layout asm

layout regs

layout split

<c-x>a     #退出

focus cmd/src/asm/regs/next/prev

refresh     #刷新窗口

update     #更新位置

winheight name +/- line   #调整各个窗口的高度，增加或减少几行

# gdbinit
.gdbinit
```
define cls
  shell clear
end
document cls
  Clears the screen with a simple command.
end

define ascii_char
  set $_c=*(unsigned char *)($arg0)
  if ( $_c < 0x20 || $_c > 0x7E )
    printf "."
  else
    printf "%c", $_c
  end
end
document ascii_char
  Print the ASCII value of arg0 or '.' if value is unprintable
end
```


**归类总结**

**0.转储功能(core dump)：**

  **(1).开启转储功能：**首先用 >ulimit -c 查看是否开启转储功能，如果命令返回不是0则已经开启，否则就是未开启。>ulimit -c unlimited 命令可以开启转储功能。也可以用 >ulimit -c 1024来设定转储文件的大小。



  **(2).设定转储文件生成地址：**编辑/etc/sysctl.conf文件，在文件最后加入下列两行：

​    kernel.core_pattern = /var/core/%t-%e-%p.core

​    kernel.core_uses_pid = 0

  然后将文件保存起来，保存完成之后执行：>sysctl -p命令（注意：执行这个命令需要root权限。）。此时执行一个会当机的程序，会在/var/core/文件夹下面生成转储文件（例如：1432378356-a.out-4821.core）。上面设定的文件名是有固定格式的，core_pattern中设定的就是文件保存目录和文件的名字格式。其中%t是转储时的unix时间戳，%e是当前执行的文件名，%p是crash进程的PID。格式符说明如下：

| 格式符号 | 说明                                              |
| -------- | ------------------------------------------------- |
| %%       | %字符本身                                         |
| %p       | 被转储进程的进程ID(PID)                           |
| %u       | 被转储进程的用户ID(UID)                           |
| %g       | 被转储进程的组(GID)                               |
| %s       | 引发转储的信号编号                                |
| %t       | 转储时间，unix时间戳(从1970年1月1日0时开始的秒数) |
| %h       | 主机名                                            |
| %e       | 可执行文件的名称                                  |
| %c       | 转储文件的大小上限(内核版本2.6.24以后可使用)      |

  **(3).转储文件的压缩：**通过在/etc/sysctl.conf文件的core_pattern中加入压缩脚本以及管道命令，可以对生成的转储文件进行压缩。首先在/etc/sysctl.conf文件中加入下列两行（如果已经存在则修改成下面的形式）：

​    kernel.core_pattern = |/usr/localsbin/zipsh %t %e %p

​    kernel.core_uses_pid = 0

  保存文件，然后执行：>sysctl -p命令。

  /usr/local/sbin/zipsh文件的内容如下：

```bash
#!/bin/sh

exec gzip - > /var/core/$1-$2-$3.core.gz
```

  这样的话，以后都会在/var/core下生成压缩的转储文件。

**1.基本信息查看：**

  **(1).栈信息：**不管是操作转储文件还是用GDB设置断点进行调试，都可以输入(GDB)bt打印栈内容进行查看。一般的当机BUG，看下当机的位置，然后看下源代码基本就可以解决了。但是很多情况下简单的(GDB)bt还查不到问题，这时候就要涉及到比较复杂的操作。下面罗列了一些对栈的操作：

​    (GDB) bt：显示所有栈帧。

​    (GDB) bt 10：显示前面10个栈帧。

​    (GDB) bt -10：显示后面10个栈帧。

​    (GDB) bt full：显示栈帧以及局部变量。

​    (GDB) bt full 10：显示前面10个栈帧以及局部变量。

​    (GDB) bt full -10：显示后面10个栈帧以及局部变量。

​    (GDB) frame <栈帧编号>：进入指定的栈帧中，然后可以查看当前栈帧中的局部变量，以及栈帧内容等信息。

​    (GDB) info frame <栈帧编号>：可以查看指定栈帧的详细信息。

​    (GDB) up：进入上层栈帧。

​    (GDB) down：进入下层栈帧。



  **(2).变量：**调试BUG过程中查看变量信息是很有帮助的操作，查看方式如下：

​    (GDB) p <变量名>



  **(3).寄存器：**对于调试来说寄存器中的值也很重要，可以查看到当前正在执行的指令的地址等。具体操作罗列如下：

​    (GDB) info reg：显示所有寄存器。可以简写为：i r。如果要查看具体的寄存器可以这样：i $ebx

​    (GDB) p $eax：显示eax寄存器内容。

​    (GDB) p/c $eax：用字符显示eax寄存器内容，反斜杠后面的是显示格式，可使用的格式见下表：该表在显示内存内容的x命令中也是通用的。

| 格式 | 说明                                        |
| ---- | ------------------------------------------- |
| x    | 显示为十六进制数                            |
| d    | 显示为十进制数                              |
| u    | 显示为无符号十进制数                        |
| o    | 显示为八进制数                              |
| t    | 显示为二进制数                              |
| a    | 显示为地址                                  |
| c    | 显示为字符（ASCII）                         |
| f    | 显示为浮点小数                              |
| s    | 显示为字符串                                |
| i    | 显示为机器语言（仅在显示内存的x命令中可用） |

  **(4).内存：**可以查看具体内存地址中的内容，比如：目前执行的汇编指令，以及栈中内容等。

​    (GDB) x $pc：显示程序指针指向位置的内容。

​    (GDB) x/i $pc：显示程序当前位置的汇编指令。

​    (GDB) x/10i $pc：显示程序当前位置开始往后的10条汇编指令。

​    (GDB) disassem $pc：反汇编当前函数。简写为：disas $pc。



**2.调试：**

  **(1).断点：**调试程序中，设置断点进行调试是最方便有效的手段，因此学会如果灵活设置断点是调试的基本功。：

​    **A.设置断点：**

​      (GDB) break <函数名>：对当前正在执行的文件中的指定函数设置断点。可简写为：(GDB) b <函数名>

​      (GDB) break <行号>：对当前正在执行的文件中的特定行设置断点。可简写为：(GDB) b <行号>

​      (GDB) break <文件名：行号>：对指定文件的指定行设置断点。最常用的设置断点方式。可简写为：(GDB) b <文件名：行号>

​      (GDB) break <文件名：函数名>：对指定文件的指定函数设置断点。C++类中的方法似乎不好使。可简写为：(GDB) b <文件名：函数名>

​      (GDB) break <+/-偏移量>：当前指令行+/-偏移量出设置断点。可简写为：b <+/-偏移量>

​      (GDB) break <*地址>：指定地址处设置断点。可简写为：b <*地址>

​    **B.查看、删除断点：**

​      (GDB) info break ：显示所有断点以及监视点。可简写为：(GDB) i b

​      (GDB) delete <编号>：删除编号指向的断点或者监视点。可简写为：(GDB) d <编号>

​      (GDB) clear <行号>：删除改行的断点。

​      (GDB) clear <文件名：行号>：删除改行的断点。

​    **C.设置无效、有效断点：**

​      (GDB) disable <断点编号> ： 当前断点设置为无效。

​      (GDB) enable <断点编号>：当前断点设置为有效。

​

  **(2).监视点：**可以监视某个变量，在变量被访问或者被修改时程序会在当前点进入断点。删除，查看监视点的方式与断点相同。设置监视点方式如下：

​    (GDB) watch <表达式>：表达式发生变化时暂停。

​    (GDB) awatch <表达式>：表达式访问或者改变时暂停。

​    (GDB) rwatch <表达式>：表达式被访问时暂停。



  **(3).条件断点：**在调试程序过程中，有时候我们只想在某个条件下停止程序，然后进行单步调试，而条件断点就是为此而设计。下面是条件断点的操作方式：

​    (GDB) b <断点> if <条件表达式> : 例如：b main.cpp:8 if x=10 && y=10

​    (GDB) condition <断点编号>：删除该断点的条件。

​    (GDB) condition <断点编号> <条件表达式>：修改断点条件。例如：condition 1 x=10 && y=10

​

  **(4).断点命令：**每次断点发生时候，想要查看的变量很多时，如果每个变量都手动print则需要浪费很多时间。断点命令可以在断点发生时批量执行GDB命令。下面是断点命令的设置方式：

​    (GDB) commands <断点编号>

​    (GDB) >print x

​    (GDB) >print y

​    (GDB) >end

​    首先输入GDB命令commands <断点编号>然后回车，这时候会出现>提示符。出现>提示符后可以输入断点发生时需要执行的GDB命令，每行一条，全部输入完成后输入end结束断点命令。

​

  **(5).反复执行：**单步执行时如果进入了你不关心的函数，你想立即跳出函数；或者进入了大循环中，你想立即循环。下面的命令可以帮到你：

​    (GDB) ignore <断点编号> <次数>：忽略N次断点。

​    (GDB) c N： 执行N次指令，会忽略断点。

​    (GDB) s/stepi/n/nexti N：往后执行N行，不会忽略断点。

​    (GDB) finish：执行完当前函数后停止，不会忽略断点。

​    (GDB) until：执行完当前循环后停止，不会忽略断点。

​    (GDB) until <地址>：执行到指定地址停止。

​

  **(6).设置变量值：**对变量的值进行控制，可以更快的调试自己的程序。下面就是设置变量值的方法：

​     (GDB) set variable <变量> = <表达式>：将变量的值设定为指定表达式的值。例如 set variable x=10



**3.调试多线程程序：**

  **(1).调试守护者进程：**守护者进程在启动好子进程后，会自动关闭主进程，如果没有设定监控模式的话，ＧＤＢ会提示断开与进程的链接。所以必须设定监控对象，设置方式如下：

​    (GDB) set follow-fork-mode child/parent

------

**附：golang版本gdb - dlv**

`dlv exec ./exefile`

安装：`go get github.com/derekparker/delve/cmd/dlv`

使用方式及命令与gdb基本相同，命令如下：

| 选项 [options] | 含义          |
| -------------- | ------------- |
| args                          | Print function arguments. |
| break (alias: b)              | Sets a breakpoint. |
| breakpoints (alias: bp)       | Print out info for active breakpoints. |
| call                          | Resumes process, injecting a function call (EXPERIMENTAL!!!) |
| clear                         | Deletes breakpoint. |
| clearall                      | Deletes multiple breakpoints. |
| condition (alias: cond)       | Set breakpoint condition. |
| config                        | Changes configuration parameters. |
| continue (alias: c)           | Run until breakpoint or program termination. |
| deferred                      | Executes command in the context of a deferred call. |
| disassemble (alias: disass)   | Disassembler. |
| down                          | Move the current frame down. |
| edit (alias: ed)              | Open where you are in $DELVE_EDITOR or $EDITOR |
| exit (alias: quit | q)        | Exit the debugger. |
| frame                         | Set the current frame, or execute command on a different frame. |
| funcs                         | Print list of functions. |
| goroutine                     | Shows or changes current goroutine |
| goroutines                    | List program goroutines. |
| help (alias: h)               | Prints the help message. |
| list (alias: ls | l)          | Show source code. |
| locals                        | Print local variables. |
| next (alias: n)               | Step over to next source line. |
| on                            | Executes a command when a breakpoint is hit. |
| print (alias: p)              | Evaluate an expression. |
| regs                          | Print contents of CPU registers. |
| restart (alias: r)            | Restart process. |
| set                           | Changes the value of a variable. |
| source                        | Executes a file containing a list of delve commands |
| sources                       | Print list of source files. |
| stack (alias: bt)             | Print stack trace. |
| step (alias: s)               | Single step through program. |
| step-instruction (alias: si)  | Single step a single cpu instruction. |
| stepout                       | Step out of the current function. |
| thread (alias: tr)            | Switch to the specified thread. |
| threads                       | Print out info for every traced thread. |
| trace (alias: t)              | Set tracepoint. |
| types                         | Print list of types |
| up                            | Move the current frame up. |
| vars                          | Print package variables. |
| whatis                        | Prints type of an expression. |
