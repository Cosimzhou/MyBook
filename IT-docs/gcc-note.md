GCC Note
========
# **gcc 选项**

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -c          | 只编译不链接  |
| -dD         | 输出define指令，不包括宏  |
| -dI         | 输出include指令  |
| -dM         | 输出define指令，  |
| -dN         | 输出define指令的变量，不包括预编译宏  |
| -dU         | 输出define和undef指令，  |
| -E          | 只预编译，不做其他处理  |
| -fPIC       | 表示编译为位置独立的代码，不用此选项的话编译后的代码是位置相关的所以动态载入时是通过代码拷贝的方式来满足不同进程的需要，而不能达到真正代码段共享的目的。  |
| -g          | 在可执行程序的标准调试信息  |
| -I[path]    | 头文件路径  |
| -l[lib]     | 链接文件  |
| -L[path]    | 链接文件路径  |
| -march=xx   | 指定CPU架构  |
| -o file     | 指定输出文件  |
| -shared     | 该选项指定生成动态连接库（让连接器生成T类型的导出符号表，有时候也生成弱连接W类型的导出符号），不用该标志外部程序无法连接。相当于一个可执行文件  |
| -S          | 只是编译不汇编，生成汇编代码  |
| -v          | 打印编译器内部编译过程的命令行信息和编译错误  |
| -Wa,xxx     | 汇编选项  |
| -Wl,@file    | 链接参数文件  |
| -Wl,xxx     | 链接选项，见ld的选项  |
| -Wp,xxx     | 预处理选项  |
| -x language | 指定语言  |

gcc -v # 查看gcc默认的include路径

```
/usr/lib/gcc/x86_64-linux-gnu/<version>/include/*   # 路径，gcc 自带的include
```


gcc -E -dD -xc /dev/null

优化级别

1. gcc中指定优化级别的参数有：-O0、-O1、-O2、-O3、-Og、-Os、-Ofast。
2. 在编译时，如果没有指定上面的任何优化参数，则默认为 -O0，即没有优化。
3. 参数 -O1、-O2、-O3 中，随着数字变大，代码的优化程度也越高，不过这在某种意义上来说，也是以牺牲程序的可调试性为代价的。
4. 参数 -Og 是在 -O1 的基础上，去掉了那些影响调试的优化，所以如果最终是为了调试程序，可以使用这个参数。不过光有这个参数也是不行的，这个参数只是告诉编译器，编译后的代码不要影响调试，但调试信息的生成还是靠 -g 参数的。
5. 参数 -Os 是在 -O2 的基础上，去掉了那些会导致最终可执行程序增大的优化，如果想要更小的可执行程序，可选择这个参数。
6. 参数 -Ofast 是在 -O3 的基础上，添加了一些非常规优化，这些优化是通过打破一些国际标准（比如一些数学函数的实现标准）来实现的，所以一般不推荐使用该参数。
7. 如果想知道上面的优化参数具体做了哪些优化，可以使用`gcc -Q --help=optimizers`命令来查询，比如下面是查询 -O3 参数开启了哪些优化：

```bash
$ gcc -Q --help=optimizers -O3

 ...
 -fassociative-math       [disabled]
 -fassume-phsa          [enabled]
 ...
```

```
gcc -fPIC -c func.c -o func.o
gcc -shared func.o -o libfunc.so

gcc -shared -o c.so -Wl,--whole-archive a.a b.a -Wl,--no-whole-archive
```

`gcc -shared -o c.so -Wl,--rpath=$XX_PATH`

# **g++**

与gcc相同的cpp编译器

`g++ -E -dD -xc++ /dev/null > a`

# **ar**

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -x  | 抽取所有obj文件 |
| -p  | 打印指定obj文件内容，eg: `ar -p file.a xxx.o` |
| -r  | 添加或替换obj文件 |
| -t  | 列出obj文件 |
| -d  | 删除obj文件 |
| -M  | 读取MRI脚本： `ar -M <libaz.mri` |

```
create libaz.a
addlib libabc.a
addlib libxyz.a
save
end
```

# **as**

汇编语言的编译器

|          |      nasm     |     as          |
| -------- | ------------- | --------------- |
| 注释     | `;`           | `#`             |
| 赋值     | `Mov ax, 0 ; dest <- src` | `Mov 0, ax # src -> dest` |
| 内存取值 | `[100]      ` | `100          ` |
|          | `[es:100]   ` | `%es:100      ` |
|          | `[eax]      ` | `(%eax)       ` |
|          | `[eax+ebx]  ` | `(%eax,%ebx)  ` |
|          | `[ecx+ebx*2]` | `(%ecx,%ebx,2)` |
|          | `[ebx*2]    ` | `(,%ebx,2)    ` |
|          | `[eax-10]   ` | `-10(%eax)    ` |
|          | `[ds:ebp-10]` | `%ds:-10(%ebp)` |
| 调用、跳转 | `jmp near [100]` | `jmp *100`       |
|          | `call near [100]`  | `call *100    `  |
|          | `jmp near eax   `  | `jmp *%eax    `  |
|          | `call near ecx  `  | `jmp *%ecx    `  |
|          | `jmp near [eax] `  | `jmp *(%eax)  `  |
|          | `call near [ebx]`  | `call *(%ebx) `  |
|          | `jmp far [100]  `  | `ljmp *100    `  |
|          | `call far [100] `  | `lcall *100   `  |
|          | `jmp far [eax]  `  | `ljmp *(%eax) `  |
|          | `call far [ebx] `  | `lcall *(%ebx)`  |
|          | `retn           `  | `ret          `  |
|          | `retf           `  | `lret         `  |
|          | `retf 0x100     `  | `lret $0x100  `  |


```
nasm xxx.asm -o xxxx.bin -l xxxx.lst     #xxxx.lst 输出对应表
ndisasm -o0x7c00 sss.bin   #反编译
```

# **c++filt**

名字正规化

# **elfedit**

# **gcov**

一个用于进行覆盖率测试的工具

1. 编译时添加选项：`-fprofile-arcs -ftest-coverage`，或者`--coverage`
2. 链接时添加选项：`-lgcov`
3. 编译后会生成`.gcno`，执行`gcov $EXEBIN_NAME`, 会将`xxx.gcno` 转为`xxx.gcov`

`__gcov_flush();`
.gcda的gcov data文件

有一个web辅助工具叫做lcov，需要自行安装。
用lcov生成一个output.info文件
```
lcov -b ./ -d ./ --gcov-tool /usr/bin/gcov -c -o output.info
```

然后用genhtml生成web页面：
```
genhtml -o gcovdir/ output.info
```

# **gprof**

性能分析工具

# **ld**

将obj或库文件连接为可执行二进制

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -L  | 库路径 |
| -l namespec  | 库命名，`:namespec` 为全名，无冒号的为`libnamespec.a` |

e.g.:
```
ld object.o -L<gcc>/lib64 **-lstdc++ -lc -lgcc_s -lc -m** -o target.out
```

`__dso_handle` 一般是因为没有stdc++或没有iostream等导致的。

# **ldd**

列出动态库依赖

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -u  | 未用的直接依赖 |
| -d  | 数据重定位 |
| -r  | 函数重定位 |

# **ldconfig**

   对so建立必要的符号连接，并配置`/etc/ld.so.conf`等，方便ld定位so

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -C cache     | 使用指定的cache,而非默认的`/etc/ld.so.cache` |
|   -f file      | 使用指定的config,而非默认的`/etc/ld.so.conf` |
|   -l           | 为指定的lib创建链接 |
|   -p           | 打印安装的lib |

# **libtool**

```
libtool --mode=link cc -static -o libaz.la libabc.la libxyz.la
```



# **make**

   按当前目录的Makefile执行构建活动

注意选项中的路径配置，一定要用绝对路径

[详见makefile-note.md](./makefile-note.md)

# **nm**

```
nm <object file | executable file | library file>
```

列表出目标文件中的函数名

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -s  | 列出索引 |
| -u  | 未定义的符号 |

|      |                        |
| ---- | ---------------------- |
| b    | bss                    |
| d    | data段                 |
| g    | 初始化的数据段小对象   |
| r    | 只读                   |
| s    | 未初始化的数据段小对象 |
| t    | 代码段                 |
| u    | 未定义的对象           |
| p    | 栈段                   |
| N    | 调试信息               |

# **objcopy**

复制转换obj文件

e.g. `objcopy src.o dest.o`

# **objdump**

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -d,-S  | 将所有包含指令的段反汇编 |
| -h     | 打印主要段的信息 |
| -x     | 打印更多的详细信息 |
| -s     | 将所有段的内容以16进制方式打印出来 |
| -t     | 查看所有的符号以及他们所在段 |



# **pkg-config**

显示已安装包的meta信息。
它会在`/usr/lib/pkgconfig/`下和`$PKG_CONFIG_PATH`的`xxxx.pc`文件中寻找对应包，并列出信息

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  --libs        |  显示ld的选项 |
|  --cflags      |  显示编译的include选项 |

```
pkg-config --libs --cflags opencv
```

向用户向程序提供相应库的路径、版本号等信息的程序



# **readelf**

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -a       | 查看全部详情 |
| -h       | 查看.o文件的文件头详细信息 |
| -S       | 显示.o文件中的所有段,即查看段表 |
| size     | 查看.o文件中各个段所占大小 |
| --relocs | 查看reloction信息，可用于判断是否增加-fPIC标识 |

e.g: `readelf --relocs foo.o | egrep '(GOT|PLT|JU?MP_SLOT)'`

# **strip**

   --strip-unneeded   去除名字表



# **gdb**

   [详见gdb](./gdb-note.md)

# **addr2line**

# **ranlib**

为存档文件进行索引

| 选项 [options] | 含义          |
| -------------- | ------------- |
| @<file>         |  Read options from <file> |
| --plugin <name> |  Load the specified plugin |
| -D              |  Use zero for symbol map timestamp (default) |
| -U              |  Use an actual symbol map timestamp |
| -t              |  Update the archive's symbol map timestamp |
| -h --help       |  Print this help message |
| -v --version    |  Print version information |


# **otool** **(mac)**

```
otool [-arch arch_type] [-fahlLDtdorSTMRIHGvVcXmqQjCP] [-mcpu=arg] [--version] <object file> ...
```

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -a | print the archive header |
| -B | force Thumb disassembly (ARM objects only) |
| -c | print argument strings of a core file |
| -C | print linker optimization hints |
| -D | print shared library id name |
| -d | print the data section |
| -f | print the fat headers |
| -G | print the data in code table |
| -h | print the mach header |
| -H | print the two-level hints table |
| -I | print the indirect symbol table |
| -j | print opcode bytes |
| -L | print shared libraries used |
| -l | print the load commands |
| -mcpu=arg | use 'arg' as the cpu for disassembly  |
| -m | don't use archive(member) syntax |
| -M | print the module table of a dynamic shared library |
| -o | print the Objective-C segment |
| -P | print the info plist section as strings |
| -p <routine name> | start dissassemble from routine name |
| -q | use llvm's disassembler (the default) |
| -Q | use otool(1)'s disassembler |
| -R | print the reference table of a dynamic shared library |
| -r | print the relocation entries |
| -S | print the table of contents of a library |
| -s <segname> <sectname> | print contents of section |
| -T | print the table of contents of a dynamic shared library |
| -t | print the text section (disassemble with -v) |
| -V | print disassembled operands symbolically |
| -v | print verbosely (symbolically) when possible |
| -X | print no leading addresses or headers |
