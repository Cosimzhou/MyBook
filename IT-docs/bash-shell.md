Bash基础及Linux命令
===================

# 入门级命令

## **cal**

  查看日历等时间信息。

## **cat**

  打印文件内容

  -n  显示行号
  -   从stdin读入

eg:
```
cat >file <<EOF
....
EOF
```

## **cd**

更改当前目录，目录需要x权限

| 选项         | 含义                |
| ------------ | ------------------- |
| `-   `       | 返回上一个目录 (~-) |
| `.   `       | 当前目录 (~+)       |
| `..  `       | 返回上一级目录      |
| `~   `       | 返回主目录          |

## **cp**

   复制文件、目录

| 选项 [options]      | 含义                      |
| ------------------- | ------------------------- |
| `-a               ` | 复制并尽量保存全部属性    |
| `-f               ` | 强行覆盖目标文件          |
| `-i               ` | 覆盖时交互提示            |
| `-r               ` | 复制目录                  |
| `-n               ` | 不覆盖对象，存在即跳过    |
| `-l               ` | 仅建立硬链接，不复制      |
| `-L               ` | 追踪链接复制              |
| `-P               ` | 不追踪链接                |
| `--attributes-only` | 只复制属性                |

## **date**

显示日期，格式输出时间。 eg: `date +"%Y-%m-%d" -d "-1 day"`

-d 日期描述，默认是“now”

+后跟代表格式的字符串

@表示时间戳

```
date -R -d @1438617600
date +%s  # 输出：1438617600
date -d "2015-08-04 00:00:00" +%s  # 输出：1438617600
date -d @1438617600 "+%Y-%m-%d"  # 输出：2015-08-04
date -d "2 months ago" '+%Y-%m'
```


## **echo**

  打印内容  eg: echo $?

| 选项 [options] | 含义   |
| -------------- | ------ |
| -e | 允许控制输出 |
| -n | 输出不换行 |

## **ls**

   列出目录中的内容，eg：`ls -lhtr | grep "G "`

| 选项 [options] | 含义                  |
| -------------- | --------------------- |
|  -a  | 列出所有文件内容 （包括隐藏文件） |
|  -A  | 列出包括隐藏文件的文件，但不包含. 和.. |
|  -F  | 列出符号信息(见下表) |
|  -l  | 列出属性内容 |
|  -t  | 按修改时间新旧排序 |
|  -S  | 按大小排序 |
|  -X  | 按扩展名排序 |
|  -v  | 按版本排序 |
|  -U  | 按目录存储顺序 |
|  -r  | 倒序输出 |

| 符号 | 涵义                                           |
| ---- | ---------------------------------------------- |
| *    | 表示具有可执行权限的普通文件                   |
| /    | 表示目录                                       |
| =    | 表示sockets套接字                              |
| >    | 就是本次需要询问的内容，代表的意思:means door. |
| @    | 表示符号链接                                   |
| │    | 表示管道                                       |

```
ls -d */
```

## **help**
  查看Linux内置命令的帮助，比如cd命令。

  Bash Only

## **man**
查看命令帮助，命令的词典，更复杂的还有info，但不常用。
帮助

-f

## **mkdir**

   创建目录

   -p 安全创建（如果目录存在也不会报错）

## **mv**

  移动或更名

## **nl**

   带行号的显示文件内容

## **rm**

   删除目标文件或目录

   -r 删除目录中的内容

   -f 强行删除

## **watch**

周期性的执行给定的命令，默认值大概2秒，并将命令的输出以全屏方式显示。

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -n  |  指定周期，单位秒 |

## **wc**

统计字词行数

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -l  |  统计行数 |
| -c  | 统计字符数 |
| -w  | 统计词数 |

## **whatis**

==> man -f

------

# 进阶级命令

## **alias**

    设置\别名，alias <name>   #显示别名

    alias <name>=‘<alias>’     #设置别名

    清除别名：unalias <name>

## **at**

指定时间执行一行，eg: `at shutdown 4pm + 3 days # 3天后的下午4点执行 shutdown`

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -m  | 执行后，发送邮件 |
| -r  | 删除任务 |

related: atq (定时队列)，atrm（清除定时任务）

相关文件：

```
/var/spool/at
/var/spool/at/spool
/proc/loadavg
/var/run/utmp
/etc/at.allow
/etc/at.deny
```

## **awk**

   pattern {action} action默认为{print} $1,2…0为成条

| 选项[options]| 含义    |
| ------------ | ------- |
| `NF        ` | 字段数（记录内） |
| `FS        ` | 分隔符 |
| `OFS       ` |  输出分隔符 |

   详细见后续awk篇

e.g. :

`awk 'BEGIN{a=0;b=0}{a+=$1;b+=$2}END{print a,b}'`

## **bc**

   命令行科学计算器。 浮点计算表达式

   echo "7/5+2" | bc

## **bg**

将挂起的任务放到后台继续执行，又见 **fg**

## **chgrp**

   更改文件用户组，eg：`chgrp root file`

## **chmod**

   更改文件系统的目标权限，eg：`chmod 755 file `

   -R  递归其子目录下的所有内容

## **chown**

   更改属主，eg：`chown user:group file `

   -R  递归其子目录下的所有内容


## **comm**

列表集合的交并差

```
comm -23 <(sort file1) <(sort file2)   #file1 比file2多出的部分
comm -13 <(sort file1) <(sort file2)   #file1 比file2缺少的部分
comm -12 <(sort file1) <(sort file2)   #file1 和file2共有的部分
```

## **command**

在系统中查找命令是否存在

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -p  | 在标准PATH变量下找，保证在各发行版中通用 |
|  -v  | 打印 `type' builtin |
|  -V  | 打印 详细信息 |


## **crontab**

  计划任务

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -e            | 编辑计划任务  |

```
# 分 时　 日　 月　 周　 命令
*　　*　　*　　*　　*　　command
```


* 第1列表示分钟1～59 每分钟用`*`或者 `*/1`表示
* 第2列表示小时1～23（0表示0点）
* 第3列表示日期1～31
* 第4列表示月份1～12
* 第5列标识号星期0～6（0表示星期天）
* 第6列要运行的命令

eg：
```
# 每月最后一天执行
59 23 28-31 * * [[ "$(date --date=tomorrow +%d)" == "01" ]] && $COMMAND
```

## **curl**

  发起网络请求

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -o | 设置输出的文件（可用于下载文件）|
| -O | 设置到URL结尾的文件名（可用于下载文件）|
| -H | 设置http头 |
| -F | 表单请求|
| -X | 请求方式POST、GET【默认】|
| -d, --data, --data-ascii | 指定请求提交的文本内容 |
| --data-binary | 指定请求提交的二进制内容 |
| --data-raw | 指定请求提交的内容（不转译‘@’） |
| --data-urlencode | 指定请求提交的内容 |


| 内部格式 | 含义          |
| -------------- | ------------- |
| content | 内容本身,不包含‘=’的‘@’ |
| =content| 内容本身,不包含前导的‘=’ |
| name=content| 字段名加内容 |
| @filename| 将文件内容提交 |
| name@filename | 字段名加文本内容 |


e.g: `curl -H "Content-type: application/json" -X POST -d "$data" $url #POST请求 `

e.g: `curl -F "name=Joe Smith" -F "email=joe@labstack.com" http://localhost:1323/save`

## **cut**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -b |  按字节数进行切割 |
|  -c |  以字符为主，指定字符序列 |
|  -d |  指定定界符，默认为Tab |
|  -f |  以字段为主，指定字段号 |

## **dd**


| 选项 [options] | 含义                                            |
| -------------- | ----------------------------------------------- |
| if=file        | 输入文件(或设备名称)。                          |
| of=file        | 输出文件(或设备名称)。                          |
| ibs=bytes      | 一次读取bytes字节，即读入缓冲区的字节数。       |
| skip=blocks    | 跳过读入缓冲区开头的ibs x blocks块。             |
| obs=bytes      | 一次写入bytes字节，即写 入缓冲区的字节数。      |
| bs=bytes       | 同时设置读/写缓冲区的字节数(等于设置obs和obs)。 |
| cbs=bytes      | 一次转换bytes字节。                             |
| count=blocks   | 只拷贝输入的blocks块。                          |
| conv=ASCII     | 把EBCDIC码转换为ASCII码。                       |
| iflags=FLAGS   | 输入FLAGS                                       |
| oflags=FLAGS   | 输出FLAGS                                       |

conv encode

| 选项 [options] | 含义          |
| -------------- | ------------- |
| ebcdic         | 把ASCII码转换为EBCDIC码。|
| ibm            | 把ASCII码转换为alternate EBCDIC码。|
| blick          | 把变动位转换成固定字符。|
| ublock         | 把固定们转换成变动位|
| ucase          | 把字母由小写变为大写。|
| lcase          | 把字母由大写变为小写。|
| notrunc        | 不截短输出文件。|
| swab           | 交换每一对输入字节。|
| noerror        | 出错时不停止处理。|
| sync           | 把每个输入记录的大小都调到ibs的大小(用ibs填充)。|


flags

| 选项 [options] | 含义                                            |
| -------------- | ----------------------------------------------- |
| append         | append mode (makes sense only for output; conv=notrunc suggested) |
| direct         | use direct I/O for data |
| directory      | 写目录否则失败 |
| dsync          | use synchronized I/O for data |
| sync           | likewise, but also for metadata |
| fullblock      | accumulate full blocks of input (iflag only) |
| nonblock       | 非块 I/O |
| noatime        | 不更新访问时间 |
| nocache        | Request to drop cache. See also oflag=sync |
| noctty         | do not assign controlling terminal from file |
| nofollow       | 不跟入符号链接 |
| count bytes    | 将'count=N'以byte为单位 (iflag only) |
| skip bytes     | 将'skip=N'以byte为单位 (iflag only) |
| seek bytes     | 将'seek=N'以byte为单位 (oflag only) |


   fdformat命令

先用dd做一个全是零的1440KB的文件

```
dd if=/dev/zero of=main.img bs=512 count=2880
```

   然后再用dd把编译好的二进制文件写进去，为了不改变镜像剩下的部分，加上conv=notrunc选项：

```
dd if=main.bin of=main.img conv=notrunc
```



   备份、还原硬盘主引导记录

```
dd if=/dev/hda of=/disk.mbr bs=512 count=1
dd if=/disk.mbr of=/dev/hda bs=512 count=1
```

## **df**

  统计文件系统可用大小

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -h           | 可读部分大小  |
|   -T           | 显示文件系统类型  |

```
df -Th|grep /mnt
```

## **diff**

   比较两个文本文件的区别，与patch结合，可将区别更新至源文件

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -c n         |  n            |

## **dirs**

   列出路径历史栈

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -c | 清理路径栈 |
|  -v | 清晰打印内容 |

## **disown**

对后台任务忽略HUP信号，jobs列出后台任务

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -h | 忽略hup信号，eg: `disown -h %1` |
| -r | 运行中的后台任务 |
| -a | 所有的后台任务 |

## **dmesg**

显示开机信息，kernel会将开机信息存储在ring buffer中。
若是开机时来不及查看信息，可利用dmesg来查看。开机信息亦保存在/var/log目录中，名称为dmesg的文件里。

时间戳转时间：

```
date -d "1970-01-01 UTC `echo "$(date +%s)-$(cut -f 1 -d' ' /proc/uptime)+38592444.056245"|bc` seconds"
```

## **dstat**

系统资源统计

-nf 网卡收发包统计

Linux Only

## **du**

  统计目录的大小，eg：du -d 1 -Hh

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -d | 最大深度 |
|  -h | 可读部分大小 |

## **ed**

自带的文本编辑器

| 常用命令 | 含义          |
| -------- | ------------- |
|  a   | 追加内容 |
|  c   | 修改当前行 |
|  d   | 删除当前行 |
|  h   | 显示错误原因 |
|  n   | 显示当前行及行号 |
|  m   | 移动行，eg: 3m6 |
|  p   | 打印当前行 |
|  q   | 退出 |
|  t   | 复制x行到y处，eg: 4t2 |
|  w   | 保存文件 |
|  /   |  搜索模式，eg: /search |

## **env**

显示环境变量

-u, --unset=NAME   删除变量

## **exec**


## **expect**

设置期待终端反馈并自动交互

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -f            | 执行expect脚本文件 |
|  -c            | 执行命令   |

```
set variable "'$variable'" #
set v_password [lindex $argv 0] #从命令行读参数
spawn $cmd #执行一条命令
expect "*Verification code*" { #期待反馈的内容，可以是正则表达式
	send "$verification_code\r"
}
send ".....\r" #输入....并回车
interact #交回控制权
```

## **expr**

   计算表达式

## **fg**

将后台任务提至前台

## **find**

   查找目标

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -type  | 查找的目标类型，f为文件、d为目录、l为连接 |
|  -name  | 目标的名称 |
|  -user  | 用户名称 |
|  -atime |  访问时间，时间单位支持wdhms五种，支持+-号表示大于、小于 |
|  -ctime |  创建时间 |
|  -mtime |  修改时间 |
|  -empty |  空的目标 |
|  -depth |  搜索深度限制 |
|  -exec  | 执行命令，例如：cp '{}' <path> ';' |

e.g:

```
   find . -type f -name *.jpg -atime +100
   find ./ -name '*.a' -exec cp '{}' <path> ';'
```

## **fmt**

| 选项 [options] | 含义    |
| -------------- | ------- |
| `-s    ` | 切割长行  |
| `-w n  ` | 设置行宽限制 |

## **fold**

     按行宽自动换行

| 变量           | 含义          |
| -------------- | ------------- |
|     -b   | 字节数 |
|     -s   | 空白 |
|     -w   | 设置行宽 |

## **getconf**

   `getconf LONG_BIT`   # 是否为64位机器

   `PAGESIZE` # 页大小

## **getopt**

```
getopt -o v: --long headers:,libs:,cc:,cxx:,with-glog,with-thrift,nodebugsymbols -- "$@"
```

## **grep**

| 选项  | 含义          |
| ----- | ------------- |
| -A n | 显示下文n行 |
| -B n | 显示上文n行 |
| -C n | 显示上下文n行 |
| -a | 强制作为文本进行匹配 |
| -c | 只输出匹配行的计数 |
| -m n | 对单个文件只显示n条记录 |
| -n | 显示行号 |
| -H | 显示文件名称 |
| -I | 忽略二进制文件 |
| -v | 剔除匹配的行 |
| -s | 避开二进制文本进行递归 |
| -r | 递归目录的匹配内容 |
| -o | 只输出匹配的内容，注意，不要使用单个\*匹配 |
| -q | 静默执行 |
| -E | 扩展正则内容匹配（同 -P） |

  eg:

多个模式的筛选，**| 要加转译**
```
grep "aaa\|bbbb\|ccc" file        #筛选多个关键字

grep -v 'aaa\|bbb\|ccc' file        #排除多个关键字
```

```
#提取文件中正则匹配的内容
grep -Eo \@\"[^\"]*\.png\" file

#将工程中用到过的.png文件列出，保存到pnglist里
grep -r \.png\" . | grep -Eo \@\"[^\"]*\.png\" | sort | uniq >~/pnglist

grep -rl sdmap . | xargs sed -i "s/sdmap/amap/g"

# 查找指定目录下中有某字符串的文件
grep -Irn "hello,world!" ./

# 查找多行匹配
grep -Pzo '(?s)COPY.*?\\\.' db-dump.sql
```

## **head**

打印文件前部

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -q | 隐藏文件名 |
| -v | 显示文件名 |
| -c<字节> | 显示字节数 |
| -n<行数> | 显示的行数，同“-<行数>” |

## **hexdump**


| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -C  |   单字HEX+字符显示 |
|  -v  |   不对重复空行进行省略 |
|  -c  | |

## **history**

查看历史命令

$HISTCONTROL=ignoredups

## **hostname**

查看当前主机名


## **iconv**

转换文件的编码格式。

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -f <encoding> | 指定来源编码 |
|  -t <encoding> | 指定来源编码  |
|  -l  | 列出支持的编码 |
|  -o <filename> | 指定输出文件 |
|  -c  | 忽略不能识别的字符 |

* /usr/lib/gconv
* /usr/lib/gconv/gconv-modules
* /usr/lib/gconv/gconv-modules.cache


## **install**

   复制并设置属性，eg: `install src1 src2 src3... dest-dir`

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -m xxx | 设置属性 |
|  -T  | 目标文件名，而不是目标目录名 |
|  -t <dir> | 后面是目标文件的目录 |
|  -d | 后面的参数均为目录，并按名称和属性创建这些目录 |


## **ipcs**

  列出ipc(进程间通讯)信息

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -m   | 共享内存 |
|  -q   | 消息队列 |
|  -s   | 信号量 |
|  -c   | 创建者 |
|  -p   | 进程号 |
|  -u   | uid |
|  -t   | 时间 |

## **ipcmk**

   创建ipc对象

## **ipcrm**

   删除ipc对象，大写的option指的是key，小写的是id

## **iptables**

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -j   | 动作 DROP、RETURN、ACCEPT |
| -t   | 指定表 |
| -i   | 指定网络接口，如：lo、eth0 |
| -p   | 指定协议，如：tcp、udp、udplite、 icmp、 icmpv6,esp、 ah、 sctp、mh、all |
| -s   | 指定源地址，如：24、127.0.0.1、255.255.255.0、!192.168.199.113、localhost |
| -d   | 指定目的地址 |
| -m   | |
| -L   | 列出链内规则 |
| -A   | 添加规则 |
| -D   | 删除规则 |
| -N   | 添加新链 |
| -X   | 删除自定义链。未指定链名时，删除所有自定义链 |

eg: `iptables -A INPUT 1 -s $IPADRESS -j DROP`

| 表       | 说明                                                         | 链                                                           |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| nat      | 对用于建立新连接包，会来查询此表                             | PREROUTING (包接入时就对些更改), OUTPUT (路由前修改，只对本地生成的包生效), and POSTROUTING (包发出时进行更改). kernel 3.7 后才支持 IPv6 NAT |
| filter   | 默认表(若无-t选项时使用此表)                                 | INPUT (包的目的是本地sockets), FORWARD (经由转发的包), OUTPUT(本地生成的包). |
| raw      | 用于配置豁免被 连合NOTRACK目标的 接连追踪。它会注册高优的网络过滤钩子，并会在ip\_conntrack或其它iptable规则之前被调用 | PREROUTING (通过所有网络接口抵达的包), OUTPUT (本地进程生成的包) |
| mangle   | 用于指定包的改造方式的表                                     | PREROUTING (路由前修改，只对外来包生效), OUTPUT (路由前修改，只对本地生成的包生效)、 INPUT (进入路由时，修改包), FORWARD (路由时，修改包), POSTROUTING (即将发出时，修改包).后三条在kernel 2.4.18之后才支持 |
| security | 强制访问控制(MAC)网络规则, 如那些打开了SECMARK和CONNSECMARK的目标. MAC由Linux 安全模块实现，如SELinux.  security表会在filter表后被调用, 从而保证filter表中的自由访问控制(DAC)规则在MAC规则前生效 | INPUT (进入路由时，修改包), OUTPUT (本地生成的包), and FORWARD (经由转发的包) |

## **jobs**

列出后台任务

| 选项  | 含义          |
| ----- | ------------- |
| -l | 列出任务的进程id |
| -p | 列出pid |
| -n | 列出运行状态 |
| -r | 列出运行中的任务 |
| -s | 列出停止中的任务 |

## **join**

按两个文件的相同字段合并。

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -t | 指定输入和输出的分隔符 |
|  -1 | file1 -2 file2 取file1的第一段和file2的第二段 |
|  -o | file field |

## **kill**

杀死进程

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -l            | 列出所有支持的信号 |

eg:

```
kill 123 #123为要杀死的进程的pid
kill 0 #杀死同所有进程，常用于脚本中
```

常用的信号如下：

| value | symbol | comment                           |
| ----- | ------ | --------------------------------- |
| 1     | HUP    | hang up                           |
| 2     | INT    | interrupt                         |
| 3     | QUIT   | quit                              |
| 6     | ABRT   | abort, core dump                  |
| 9     | KILL   | non-catchable, non-ignorable kill |
| 14    | ALRM   | alarm clock                       |
| 15    | TERM   | software termination signal       |

| value | symbol | comment      |
| ----- | ------ | ------------ |
| 18    | CONT   | continue run |
| 19    | STOP   | stop running |

        killall  #按名称kill 进程

   pkill -f fff  #按全名字kill进程

## **last**

输出登录系统的记录

     reboot 系统历史启动的时间

## **less**

对文件或其它输出进行分页显示

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -b <缓冲区大小> | 设置缓冲区的大小 |
| -e | 当文件显示结束后，自动离开 |
| -f | 强迫打开特殊文件，例如外围设备代号、目录和二进制文件 |
| -g | 只标志最后搜索的关键词 |
| -i | 忽略搜索时的大小写 |
| -m | 显示类似more命令的百分比 |
| -N | 显示每行的行号 |
| -o <文件名> |  将less 输出的内容在指定文件中保存起来 |
| -Q | 不使用警告音 |
| -s | 显示连续空行为一行 |
| -S | 行过长时间将超出部分舍弃 |
| -x <数字> | 将“tab”键显示为规定的数字空格 |

| 交互按键 | 含义          |
| -------------- | ------------- |
| /字符串 | 向下搜索“字符串”的功能 |
| ?字符串 | 向上搜索“字符串”的功能 |
| n | 重复前一个搜索（与 / 或 ? 有关） |
| N | 反向重复前一个搜索（与 / 或 ? 有关） |
| b |  向后翻一页 |
| d |  向后翻半页 |
| h |  显示帮助界面 |
| Q |  退出less 命令 |
| u |  向前滚动半页 |
| y |  向前滚动一行 |
| 空格键 | 滚动一行 |
| 回车键 | 滚动一页 |
| [pagedown] | 向下翻动一页 |
| [pageup] |  向上翻动一页 |

只要一个文件夹下的文件的被写入，那么这个文件夹的访问时间就会更新。但像less这样的只读打开的话，文件和文件夹都不会改变访问时间

## **ln**

   建立符号连接

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -s  | 建立软链 eg: ln -s 目标 链接符号 |
|  -f | 更新符号对象 |
|  -n | 不对符号目标进行解析追踪 |

   `ln -sfn ff symlink   #更新符号连接`

## **locate**

   文件定位，从locatedb中进行搜索，`/var/lib/mlocate/mlocate.db` ，使用updatedb更新库。

## **lsof**

列出当前系统打开文件

-i tcp:8080 #列出占用8080端口的进程

## **lsblk**

列出当前块文件（存储盘）

## **lsb\_release**

   cat /etc/os-release

## **mesg**

     设置当前终端的写权限，即是否让其他用户向本终端发信息。将mesg设置y时，其他用户可利用write命令将信息直接显示在您的屏幕上。

     mesg   y   #允许

     mesg   n   #不允许

## **mkfifo**

     创建一个管道

   一个用于桥接的例子：
```
  mkfifo recvpipe sendpipe
  recvpipe &
  sendpipe &
  nc -4 -l $3 > recvpipe < sendpipe &
  import_pid=$!
  nc -4 $1 $2 < recvpipe > sendpipe &
  export_pid=$!
  wait $export_pid
  kill $import_pid
  rm -f sendpipe recvpipe
```

## **mktemp**

     创建一个临时路径


## **more**

   对文件或其它输出进行分页显示，按任意键下一页

## **mount**

   挂载

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -o            | 指定编码      |
|  -t            | 指定文件系统  |

umount 卸载


```
# 挂载
#linux目标机
sudo mount <host>:/opt/userfilebase /opt/userfilebase

#windows目标机
sudo mount //<host>/Share \
           -o iocharset=utf8,username=<user>,password=<passwd> \
           /mnt/crawlfilebase

# 将/var/tmp绑定到/tmp
mount -o rw,noexec,nosuid,nodev,bind /tmp /var/tmp
```


## **nano**

   一种文本编辑器，建议使用vim

   <C-X>   退出

## **nc**

   监听、连接TCP或UDP端口：nc <host> <port> #client connection

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -l <port> | 监听端口，nc -l <port> # server listen |
| -p <port> | 服务端口 |
| -z <host> |   报告端口状况，e.g.   nc -z <host> 80-800 |
| -4  |  IPv4 |
| -6  |  IPv6 |
| -k  |  在监听模式中接受多个连接 |
| -s <IP>  |  冒用本地IP -s 10.0.0.28 |
| -x  | 代理地址： |

   e.g.
```
nc -l 12345 < file
nc <host> 12345 >file
mkfifo pp; nc -4 -l $port <pp | tee $req_record_file | nc $srv_host $srv_port | tee $resp_record_file > pp # 做一个管道桥接
{ printf 'HTTP/1.0 200 OK\r\nContent-Length: %d\r\n\r\n' "$(wc -c < file)"; cat file; } | nc -l 8080 # 一次性的http server
```

## **netstat**

     网络状态信息

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -a   | (all)显示所有选项，默认不显示LISTEN相关 |
|  -t   | (tcp)仅显示tcp相关选项 |
|  -u   | (udp)仅显示udp相关选项 |
|  -n   | 拒绝显示别名，能显示数字的全部转化成数字。 |
|  -l   | 仅列出有在 Listen (监听) 的服務状态 |
|  -p   | 显示建立相关链接的程序名 |
|  -r   | 显示路由信息，路由表 |
|  -e   | 显示扩展信息，例如uid等 |
|  -s   | (sort)按各个协议进行统计 |
|  -c   | 每隔一个固定时间，执行该netstat命令。 |

## **nl**

   带行号的输出文本文件内容

## **nice**

     调整后台进程的nice值，nice值的取值范围在`-20~19`

| 选项  | 含义    |
| ----- | ------- |
|  -n   | 以指定的nice值运行程序，eg:  `nice -n 19 echo hello world` |

## **nohup**

  使用户退出后依然运行，输出内容后到nohup.txt，便于调试

  eg: `nohup $cmd >> default.out 2>&1 &`

## **nslookup**

域名查询，eg: `nslookup www.cosimzhou.com`

## **od**

     以八进制等形式输出文件

| 选项 [options] | 含义          |
| -------------- | ------------- |
|    -A          | 起始地址      |
|    -t          | 设置格式，x1 16进制单字节 |

## **paste**

     按行拼接多个流


| 选项 [options] | 含义          |
| -------------- | ------------- |
|    -d          | 指定分隔符    |

## **patch**

   将diff应用到上源文件上去

## **perf**

程序的性能分析工具

perf list 列出可分析的指标

perf stat 列出执行程序的性能统计，`perf stat ./program`

perf record 记录执行程序的性能统计，`perf record ./program`

perf report 查看程序的性能统计

Linux Only

## **perl**

     执行perl脚本

     perl -pi -e 's///g' 文件内替换

## **popd**

   与 pushd 配合使用，将dirs中的目录进行出栈并使用

## **printf**

   与c语言的printf的函数相似

## **ps**

列出进程信息，process status

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -a  |   全部内容，同-e  |
|  -f  |    全格式列出进程信息  |
|  -u  |  |
|  -x  |   列出无tty的进程  |
|  -o  |    指定输出字段格式，可选字段名：args, cmd, comm, command, fname, ucmd, ucomm, lstart, bsdstart, start  |

eg: ps -ef|grep defunct #列出僵尸进程

ps -eo pid,lstart,etime | grep 5176

| 状态 | 描述                                            |
| ---- | ----------------------------------------------- |
|   D  | 不可中断的休眠（通常表示该进程正在进行I/O动作） |
|   R  | 正在执行中                                      |
|   S  | 休眠状态                                        |
|   T  | 暂停执行                                        |
|   W  | 没有足够的内存分页可分配                        |
|   <  | 高优先顺序的进程                                |
|   N  | 低优先顺序的进程                                |
|   L  | 有内存分页分配并锁在内存内（即时系统或定制I/O） |

## **pstree**

展示进程树

Linux Only

## **pushd**

   像dirs中的路径进行备份，入栈

```
   pushd <path>   # oldcwd=`pwd`; cd <path>
   # do something in <path>
   popd            # cd $oldcwd
```

## **pwd**

当前目录路径

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -L   |  当前目录的逻辑路径 |
|  -P   |  解析全部符号连接后的路径 |

## **python**

执行python脚本

`python -c "print 'hello world!'"`

## **read**

读变量，默认会存入REPLY中，eg：read a; echo $a

bash 与 zsh 表现不同

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -p msg  | 显示提示，eg: read -p "please press any key" |
|  -t  | 计时，若干秒后自动跳过，eg: read -t 5 #只等待5秒 |
|  -n num  | 限制输入字符数，eg: read -n1 #只需要一个字符 |
|  -s  | 默读，输入不显示在屏幕上 |


## **readlink**


| 选项 [options] | 含义    |
| -------------- | ------- |
| -f |   |

## **rev**

     翻转内容，行内按字节完全翻转，按行见"tac"

## **rcp**

     类似scp

## **renice**

   修改进行nice值， 见nice

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -n   | priority |
|  -g   | group name |
|  -u   | user name |
|  -p   | pid |

## **rsync**

```
rsync -av src-dir dest-dir/   #拷贝src-dir文件夹
rsync -av src-dir/ dest-dir/   #拷贝src-dir文件夹下的内容
```

## **runlevel**

   显示运行级别

## **scp**

   远程复制文件。eg: scp test user@remotehost

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -P port       | 端口号，与ssh的-p不同，是大写的 |

## **screen**

新建一个会话窗口

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -dmS <*session name>* | 创建一个会话并指定名字 |
| -list  |列出所有会话 |
| -r <*session name>*  |重连会话 |

## **sed**

类似命令: `perl -pi -e 's/:/\n/g'`

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -f  | 附加一个带有运行参数的sed文本文件 |
| -n  | 表示隐藏默认输出内容 |

eg:

```
sed -n '50,100p' file # 指定行输出
sed ':x;N;s/\n/,/;b x'
sed 'H;$!d;g;s/\n\n/;/g'    #将连续的两个换行替换成';'，$!
sed 'H;$!d;g;s/\n\n/;/g;s/\n//g;s/;/\n/g;s/:/: /g;s/v/v /g;s/file/file /g'  #可以进行组合替换
sed 's/\(..\)/\\\x\1/g'
```

| 命令 | 解释  |
|----|-------|
| b x|跳转到标签|
| D |清空模式空间中开端至\n的内容，放弃之后的命令，对剩余模式空间重新执行sed|
| d |清空模式空间，放弃之后的命令，重头执行|
| s |替换指定字符|
| g |将当前保持空间中内容覆盖至模式空间|
| G |将当前保持空间中的内容追加至模式空间|
| h |将当前模式空间中内容覆盖至保持空间|
| H |将当前模式空间中的内容追加至保持空间|
| N |模式区追加, 下一行合并到模式空间，但是两行之间依然含有\n换行符，如果命令未执行成功（并非跳过：前端条件不匹配），则放弃之后任何命令，并对新读取的内容，重头执行sed|
| n |跳过此行|
| p |打印模式空间内容|
| P |打印模式空间内容，追加到默认输出之前|
| x |将保持空间和模式空间内容互换|
| :x |是一个标签x|
| y |用于字符转换，eg: `sed 'y/his/HIS/' aaa #sed 's/\b[a-z]\b/\u&/g' ddd`|
| r file	| 从file中读行 |
| t label	| if分支，从最后一行开始，条件一旦满足或者T，t命令，将导致分支到带有标号的命令处，或者到脚本的末尾 |
| T label	| 错误分支，从最后一行开始，一旦发生错误或者T，t命令，将导致分支到带有标号的命令处，或者到脚本的末尾 |
| w file	| 写并追加模板块到file末尾 |
| W file	| 写并追加模板块的第一行到file末尾 |
| !	| 表示后面的命令对所有没有被选定的行发生作用 |
| =	| 打印当前行号 |
| #	| 把注释扩展到第一个换行符以前 |



1、sed执行模板=sed '模式{命令1;命令2}'

即逐行读入模式空间，执行命令，最后输出打印出来

正则范围制定需要加转译：\{n,m\}

e.g: sed -e '1,/^exit$/d' file #删除从1到exit的内容

## **service**

启动、停止、重新启动和关闭系统服务，还可以显示所有系统服务的当前状态。

```
service --status-all
service mysql status
```

## **seq**

生成数字序列

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -f  | 指定格式，如%05g |
|  -w  | 指定宽度补全，就是宽度相等，不足的前面补 0 |
|  -s  | 指定分隔符，默认为换行 |

  eg:

```
seq 0 n  #生成0~n
seq n #生成1~n
```

## **set**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -e            | 出错时退出 |
|  -x            | 执行时输出命令内容 |
|  -u            | 遇到未定义的变量 |
|  -E            | 脚本中捕捉某些信号 |
|  -v            | 显示输入值 |
|  -o <attrib>   | 设置指定属性，不指定时显示状态 |

+/- 关闭或打开

| 属性               | 含义          |
| ------------------ | ------------- |
| allexport          | set -a, 导出所有变量  |
| braceexpand        |  |
| emacs              |  |
| errexit            | set -e |
| errtrace           |  |
| functrace          |  |
| hashall            |  |
| histexpand         |  |
| history            | 记录历史 |
| ignoreeof          |  |
| interactive-comments|  |
| keyword            |  |
| monitor            |  |
| noclobber          | 不允许覆盖 |
| noexec             | set -n, 不执行，仅读取命令 |
| noglob             | 停止 wildcard 功能 |
| nolog              |  |
| notify             |  |
| nounset            |  |
| onecmd             | 一次性终端（执行一个命令后自动退出） |
| physical           |  |
| pipefail           | 管道中任意失败即失败 |
| posix              |  |
| privileged         |  |
| verbose            |  |
| vi                 |  |
| xtrace             |  |

## **setsid**

用一个新的会话来运行程序

## **sftp**

进入ftp方式传输文件，eg: sftp username@host

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -o             | ssh参数，如Port=8080 |

进入命令行后，put 文件，get 文件

## **sort**

| 参数选项 | 解释  |
|----|------------|
| -b | 忽略开头空白 |
| -c | 查是否已排序 |
| -d | 仅考虑文字数字、空白（字典序） |
| -g | 浮点数排序 |
| -f | 不区分大小写 |
| -i | 忽略非打印字符 |
| -o | 指定输出文件 |
| -k | 定义排序字段 |
| -m | |
| -n | 整数方式 |
| -r | 倒置，即降序 |
| -t | char 分隔符 |
| -u | 保留唯一记录，去重 |
| --stable | 稳定排序 |

## **source**

可继承环境变量的执行shell脚本

## **split**

切分文件

| 参数选项 | 解释  |
|----|------------|
| -a n | 后缀位数，默认为2 |
| -b n| 单片大小，单位字节 |
| -n form| |
| -u | 输出时不进行缓冲 |

## **ss**

socket统计

Linux Only

## **ssh**

   登录远程机，eg：ssh username@hostip

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -p  | 端口号 |
| -N  | 登录后不执行命令 |
| -T  | 验证是否部署公钥 |
| -o <attribute>=<value> | |

   在`~/.ssh/authorized_keys`下可以导入`id_rsa.pub`，实现互信，免密登录。
```
git proxy: ~/.ssh/config

Host gitlab.xxx.com
HostName gitlab.xxx.com
Port 29418
ProxyCommand nc -v -xlocalhost:7070 %h %p
#ProxyJump localhost:7070
```


   配置文件位置：`/etc/ssh/sshd_config`

```
ssh -o TCPKeepAlive=yes -o ServerAliveInterval=300 xx@xxx.com  #避免超时管道断裂
ssh -v -N -D 0.0.0.0:7070 user@address
```
e.g.: **@互信**

```
ssh-keygen -t rsa
scp ~/.ssh/id_rsa.pub <user>@<host>:~
ssh <user>@<host>
cat id_rsa.pub >> ~/.ssh/authenized_keys
```

## **stat**

   显示文件属性信息

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -f            | 显示文件系统  |
|  -L            | 跟随符号连接  |

## **su**

   切换用户，后带用户名

## **sudo**

使用root权限运行命令，后带命令

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -i  |  登录同--login |
|  -u  | <user> 切换用户 |
|  -S  | 在stdin流中带入密码，不需要用户输入 |
|  -s  | 切换为root账户 |

## **sleep**

   挂起n秒，eg: `sleep $n`

## **ssh-keygen**

   生成ssh公私钥对

   -t 指定算法，eg: `ssh-keygen -t rsa`

```
sh-keygen -f ~/.ssh/known_hosts -R <host_name> # remove expired authorized key for old host
```

## **strings**

  查看二进制文件中的字符串

   od 八进制或十六进制显示文件内容

   dd

## **stty**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -a            | 显示所有信息 |
|  cols N        | 设置终端有N列 |
|  rows N        | 设置终端有N行 |
|  size          | 显示行列尺寸 |
|  -echo         | 不显示键入内容 |
|  -ctlecho      | 将控制字符输出成'^X'形式 |

## **sysctl**

 对系统参数进行读写的工具

```
sysctl -w net.ipv4.ip_forward=1
sysctl kern.maxfiles=5000
```

## **systemctl**

   在`/etc/init.d/`或`/etc/systemd/system/*.service`文件启动服务

/etc/rc.local

service ini文件：
```
[Unit]
Description=
After=

[Service]
User=
Restart=always
ExecStart=
LimitCORE=0
StandardOutput=null
StandardError=null
Environment="LD_LIBRARY_PATH=..."

[Install]
WantedBy=multi-user.target
```


## **systemd**

## **tac**

   按行倒序输出，是cat的倒序记录

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -s           |  指定分隔符   |

## **tail**

显示文件末尾部分

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -f   | 循环读取 |
|  -F   | 循环读取指定文件名（而非指定文件，即使文件更名也会自动切换到新文件里去  ） |
|  -q   | 不显示处理信息 |
|  -v   | 显示详细的处理信息 |
|  -c <数目> | 显示的字节数 |
|  -c +<行数>  | 从数目开始，直到结尾 |
|  -n <行数>  | 显示行数 |
|  -n +<行数>  | 从数目开始，直到结尾 |
|  --pid=PID  | 与-f合用,表示在进程ID,PID死掉之后结束. |
|  -q, --quiet, --silent  | 从不输出给出文件名的首部 |
|  -s, --sleep-interval=S  | 与-f合用,表示在每次反复的间隔休眠S秒 |

## **tar**

  打包、解包目录

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -C  | 指定目标路径，可用于省略或替换路径 |
|  -r   | 追加文件，只适用于无压缩的tar球，gz的tar可以先gunzip成tar，更新后再gzip回来 |
|  --delete  | 删除文件 |
|  -t  | 列出文件 |

  eg: `tar -zcvf /tmp/etc.tar.gz /etc`

  注意：tar 文件夹在后，tar包在前


| 选项 [options] | 含义          |
| -------------- | ------------- |
| -a | 按后缀自动选择解压方式 |
| -I <cmd> | 指定压缩程序|
| --no-auto-compress | 不自动选择解压 |
| -j | 以 bzip2方式压缩 |
| -J | 以 xz方式压缩 |
| -z | 以 gzip方式压缩 |
| -Z | 以 compress方式压缩 |
| --lzip | 以lzip方式压缩   |
| --lzma | 以lzma方式压缩 |
| --lzop | 以lzop方式压缩 |

## **tee**

管道复制传递，eg: `echo "dfasdf" | tee -a log` #向log中写入的同时还会在stdout输出

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -a | 向文件追加 |
|  -i | 忽略中断 |

## **telnet**

   测试端口是否打开, 退出使用：`ctrl+] 回车`



## **time**

  计算命令耗时

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -p             | 以秒为单位显示 |

  eg: time -p `sleep 5` #`sleep 5`为待计算时间的命令，可不带``号

## **top**

   查看进程运行情况

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -p <pid>     | 查看指定进程  |


| 选项 [options] | 含义          |
| -------------- | ------------- |
|  Z,B,E,e | Global: 'Z' colors; 'B' bold; 'E'/'e' summary/task memory scale |
|  l,t,m |  Toggle Summary: 'l' load avg; 't' task/cpu stats; 'm' memory info |
|  0,1,2,3,I |  Toggle: '0' zeros; '1/2/3' cpus or numa node views; 'I' Irix mode |
|  f,F,X |  Fields: 'f'/'F' add/remove/order/sort; 'X' increase fixed-width |
|  L,&,<,> | Locate: 'L'/'&' find/again; Move sort column: '<'/'>' left/right |
|  R,H,V,J | Toggle: 'R' Sort; 'H' Threads; 'V' Forest view; 'J' Num justify |
|  c,i,S,j | Toggle: 'c' Cmd name/line; 'i' Idle; 'S' Time; 'j' Str justify |
|  x,y | Toggle highlights: 'x' sort field; 'y' running tasks |
|  z,b | Toggle: 'z' color/mono; 'b' bold/reverse (only if 'x' or 'y') |
|  u,U,o,O | Filter by: 'u'/'U' effective/any user; 'o'/'O' other criteria |
|  n,#,^O | Set: 'n'/'#' max tasks displayed; Show: Ctrl+'O' other filter(s) |
|  C,... |   Toggle scroll coordinates msg for: up,down,left,right,home,end |
|  k,r |  Manipulate tasks: 'k' kill; 'r' renice |
|  d or s |  Set update interval |
|  W,Y |  Write configuration file 'W'; Inspect other output 'Y' |
|  q |  Quit |

## **touch**

  更新目标，可用于创建新文件

   touch a.txt

## **tput**

设置或查询终端信息

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -T           | 设置信息 |
|   cols         | |
|   lines        | |
|   bold         | 粗体字 |
|   setb         | 设置背景色 |
|   setf         | 设置前景色 |
|   cup w h      | 移动光标到(w,h) |
|   longname     | 名称 |
|   smul         | 设置下划线开始 |
|   rmul         | 设置下划线结束 |
|   ed           | 删除 |

## **tr**

  替换字符

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -c           | 补集          |
|   -d           | 去除字符      |

可以用于换行符的替换，如行的拆分和合并
 eg: `echo $PATH | tr ':' '\n' | grep -v "^/home" | tr '\n' ':' `

 eg: `tr '[:upper:]' '[:lower:]'` #转小写

## **trap**

   消息陷阱，消息触发时，执行指定的命令func

   e.g.: `trap func SIGINT`

 trap func SIGINT

## **tty**

打印终端符号

```
$ tty
/dev/tty1     #
/dev/pts/7    #
```

## **ulimit**


| 选项 | 含义                                                     | 例子                                                         |
| ---- | -------------------------------------------------------- | ------------------------------------------------------------ |
| -H   | 设置硬资源限制，一旦设置不能增加。                       | ulimit -Hs 64；限制硬资源，线程栈大小为 64K。               |
| -S   | 设置软资源限制，设置后可以增加，但是不能超过硬资源设置。 | ulimit -Sn 32；限制软资源，32 个文件描述符。                |
| -a   | 显示当前所有的 limit 信息。                              | ulimit -a；显示当前所有的 limit 信息。                      |
| -c   | 最大的 core 文件的大小， 以 blocks 为单位。              | ulimit -c unlimited； 对生成的 core 文件的大小不进行限制。  |
| -d   | 进程最大的数据段的大小，以 Kbytes 为单位。               | ulimit -d unlimited；对进程的数据段大小不进行限制。          |
| -f   | 进程可以创建文件的最大值，以 blocks 为单位。             | ulimit -f 2048；限制进程可以创建的最大文件大小为 2048 blocks。 |
| -l   | 最大可加锁内存大小，以 Kbytes 为单位。                   | ulimit -l 32；限制最大可加锁内存大小为 32 Kbytes。          |
| -m   | 最大内存大小，以 Kbytes 为单位。                         | ulimit -m unlimited；对最大内存不进行限制。                 |
| -n   | 可以打开最大文件描述符的数量。                           | ulimit -n 128；限制最大可以使用 128 个文件描述符。          |
| -p   | 管道缓冲区的大小，以 Kbytes 为单位。                     | ulimit -p 512；限制管道缓冲区的大小为 512 Kbytes。          |
| -s   | 线程栈大小，以 Kbytes 为单位。                           | ulimit -s 512；限制线程栈的大小为 512 Kbytes。              |
| -t   | 最大的 CPU 占用时间，以秒为单位。                        | ulimit -t unlimited；对最大的 CPU 占用时间不进行限制。      |
| -u   | 用户最大可用的进程数。                                   | ulimit -u 64；限制用户最多可以使用 64 个进程。              |
| -v   | 进程最大可用的虚拟内存，以 Kbytes 为单位。               | ulimit -v 200000；限制最大可用的虚拟内存为 200000 Kbytes。  |

## **uname**

输出系统名称、版本

| 选项 [options] | 含义 |
| -------------- | ---- |
| -a |  输出全部内容|
| -m |   输出机器架构|
| -r |     内核版本|
| -p |     cpu 信息|

tar.xz

## **uniq**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -c     |   重复次数   |
|  -d     |   仅显示重复的行   |
|  -u     |   不显示重复的行   |

## **uptime**

显示系统运行时间及负载。

23:51:26 up21:31, 1 user, load average: 30.02, 26.43, 19.0212

该命令可以大致的看出计算机的整体负载情况，load average后的数字分别表示计算机在1min、5min、15min内的平均负载。

## **pr**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -cn  | 生产n列 |
|  -f  | 分页符 |
|  -h  | 设置页标题 |
|  -ln  | 生产n行 |
|  -on  | 输出n个空白 |
|  -t  | 无标题 |
|  -wn  | 每行限n个字 |

## **uuidgen**

生成UUID

## **visudo**

编辑/etc/sudoers，添加sudo权限。注意：千万不要用vi /etc/sudoers

## **w**

谁在登录并且他们在干嘛？

## **wait**

   等待后台任务结束，如果没有指定任务号，则等待所有任务结束

   e.g.: `wait %2 %3`

## **what**

   显示文件哪些存在

## **which**

   显示命令位置，按环境变量PATH路径查找。


## **who**

   显示当前登录的用户

| 选项 [options] | 含义          |
| -------------- | ------------- |
|   -b      | 查看最后一次系统启动的时间 |
|   -t      | 查看当前系统运行时间 |

## **whoami**

   显示当前登录的用户名,相当于执行命令: `id -un`

## **wget**

发起网络请求

| 选项 [options] | 含义                                                     |
| -------------- | -------------------------------------------------------- |
| -nH --no-host-directories| 不建立与url中主机对目录 |
| -nd --no-directories| 不建立与url对应结构的目录 |
| -m --mirror| 无限递归 |
| -r --recursive| 递归目录 |
| --cut-dirs=number |  建立与url对应除去前number级目录的路径结构 |
| --limit-rate=80m |   限制下载速度 |
| --post-data=data |   发送post请求 |
| --post-file=file |    post 上传文件 |
| --save-cookies filename | 保存cookie |
| --load-cookies filename |  加载cookie |
| --ftp-user=guest |  ftp协议下载，指定用户名 |
| --ftp-password=xxx |  ftp协议下载，指定密码 |

e.g:

```
wget --post-data="$data" POST $url #POST请求
wget --output-document=/dev/null $url #不保存
wget -m -r -nd -nH --limit-rate=80m --cut-dirs=6 --ftp-user=guest --ftp-password=xxx ftp://map-datamining-compile01.ys/home/xiaoju/user/duhuanming/release.fps/data_map/traffic_control.2018126
wget -nH -nd --limit-rate=80m --ftp-user=guest --ftp-password=xxx ftp://….. #下载文件
```

## **whereis**

查找（可执行的）文件在什么位置，按环境变量PATH路径查找。

| 选项 [options] | 含义                                                     |
| -------------- | -------------------------------------------------------- |
| -b | 定位可执行文件。 |
| -m | 定位帮助文件。 |
| -s | 定位源代码文件。 |
| -u | 搜索默认路径下除可执行文件、源代码文件、帮助文件以外的其它文件。 |
| -B | 指定搜索可执行文件的路径。 |
| -M | 指定搜索帮助文件的路径。 |
| -S | 指定搜索源代码文件的路径。 |

## **write**

     向其它终端发送消息，参数为logname和终端名，进入聊天模式

     write cosim 1

## **xargs**

-i  {}  eg: xargs -i echo {}

## **xxd**

   hexdump或反转

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -r    | 将hex内容转为二进制内容 |
|  -p    | 不依赖行号的转换 |

```
# read 1 byte at offset 40C
bhex=$(xxd -seek $((16#40C)) -l 1 -ps A.bin -)
# delete 3 least significant bits
bdec=$(($((16#$bhex)) & $((2#11111000))))
cp A.bin B.bin
# write 1 byte back at offset 40C
printf "00040c: %02x" $bdec | xxd -r - B.bin
```

```
echo '0103000000014240'|xxd -r -p
```


## **yes**

   重复输入字符串，默认为‘y’

------------------------
# 权限及组相关命令

## **useradd**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -c  | 加上备注文字，备注文字保存在passwd的备注栏中。　|
|  -d  | 指定用户登入时的启始目录。|
|  -D  | 变更预设值。|
|  -e  | 指定账号的有效期限，缺省表示永久有效。|
|  -f  | 指定在密码过期后多少天即关闭该账号。|
|  -g  | 指定用户所属的群组。|
|  -G  | 指定用户所属的附加群组。|
|  -m  | 自动建立用户的登入目录。|
|  -M  | 不要自动建立用户的登入目录。|
|  -n  | 取消建立以用户名称为名的群组。|
|  -r  | 建立系统账号。|
|  -s  | 指定用户登入后所使用的shell。|
|  -u  | 指定用户ID号。|

/etc/passwd 为用户列表

## **userdel**

删除用户：userdel [-r][用户帐号]

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -f             | 删除用户登入目录以及目录中所有文件。|

## **usermod**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -c<备注>  |  修改用户帐号的备注文字； |
|  -d<登入目录>  |  修改用户登入时的目录； |
|  -e<有效期限>  |  修改帐号的有效期限； |
|  -f<缓冲天数>  |  修改在密码过期后多少天即关闭该帐号； |
|  -g<群组>  |  修改用户所属的群组； |
|  -G<群组>  |  修改用户所属的附加群组； |
|  -l<帐号名称>  |  修改用户帐号名称； |
|  -L  |  锁定用户密码，使密码无效； |
|  -s  |  修改用户登入后所使用的shell； |
|  -u  |  修改用户ID； |
|  -U  |  解除密码锁定。 |

gpasswd -a USER group

## **groupadd**

命令可以创建一个新的用户组，其最基本用法为： `groupadd <groupname>`

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -g <gid> | 指定新建用户组的GID，该GID必须唯一，不能和其他用户组的GID重复 |
| -o | 一般与-g选项同时使用，表示新用户组的GID可以与系统已有用户组的GID相同 |

## **groupdel**

命令用于删除一个已存在的用户组，其用法为：`groupdel  <groupname>`


## **groups**

查询用户所在的组 eg: `groups <user>`


## **newgrp**

主要用于在多个用户组之间进行切换，语法格式  `newgrp <用户组>`

newgrp指令类似login指令，当它是以相同的帐号，另一个群组名称，再次登入系统。欲使用newgrp指令切换群组，您必须是该群组的用户，否则将无法登入指定的群组。

## **passwd**

修改密码，用法如下：

```
passwd <username>
(current) UNIX password: <old password>
Enter new UNIX password: <new password>
Retype new UNIX password: <comfirm password>
```

---------------------
# 包管理相关命令

## **apt-get**

| 选项 [options] | 含义          |
| -------------- | ------------- |
| list       | 列出已安装的软件 |
| search     | 搜索软件 |
| source     | apt软件源的管理 |
| install    | 下载并安装 |
| download   | 只下载安装包，而不进行安装 |
| autoremove | 自动卸载不被依赖的软件 |
| remove     | 卸载软件 |
| purge      | 卸载软件并删除配置文件 |
| update     | 更新软件源的可用接入点 |
| upgrade    | 升级 |

## **apt-cache**

   policy <pkg> 帮助调试个性偏好文件的问题

   madison <pkg> 模仿输出

## **apt-file**

   list 列出匹配文件

   find 同search

   search <pattern>

   show <package>

## **apt-key**

   add filename 0

 del keyid d

   export keyid 0

 adv --keyserver keyserver.ubuntu.com --recv-keys ABF5BD827BD9BF62

## **add-apt-repository**

```
apt-get download $(apt-cache depends --recurse --no-recommends --no-suggests --no-conflicts --no-breaks --no-replaces --no-enhances nginx=1.16.0-1~xenial | grep -v i386| grep "^\w" | sort -u)
```

## **dpkg**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -L <package>  | 列出安装内容 |
|  -i <deb>      | 安装包 |

## **rpm**

管理rpm包的命令。

## **yum**

自动化简单化地管理rpm包的命令。
   list

   install

   uninstall

   upgrade


## **update-alternatives**

| 选项 [options] | 含义    |
| -------------- | ------- |
| `--install link name path priority` | |
| `--config name`  | |
| `--set name path`  | |
| `--remove name path`  | |
| `--all`  | |
| `--list name`  | |
| `--query name`  | |
| `--display name`  | |
| `--auto name`  | |

/etc/alternatives

----------------
## **dmesg**

   查看系统日志

日志示例：

```
[1880957.563400]Outofmemory:Killprocess18694(perl)score246orsacrificechild
[1880957.563408]Killedprocess18694(perl)total-vm:1972392kB,anon-rss:1953348kB,file-rss:0kB
[2320864.954447]TCP:PossibleSYNfloodingonport7001.Droppingrequest.CheckSNMPcounters.123456
```

打印内核环形缓存区中的内容，可以用来查看一些错误；

上面的例子中，显示进程18694 因引内存越界被kill掉以及TCP request被丢弃的错误。通过dmesg可以快速判断是否有导致系统性能异常的问题。

## **fdisk**

分区命令

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -l             | 查看所有存储介质 |

eg：fdisk /dev/vdb1    #m 打印帮助

## **mkfs**

创建文件系统

| 选项 [options] | 含义          |
| -------------- | ------------- |
| -t format | 分区为format的文件系统 |

eg: mkfs -t ext3 /dev/vdb1

== mkfs.ext3 /dev/vdb1

## **swapon/swapoff**

## **mkswap**

## **nmap**
网络扫描命令。

-sTU localhost  #扫描端口号


## **lsmod**

   列出linux内核模块

## **modinfo**

   列出模块的信息

## **modprobe**

   添加或删除内核模块

## **insmod**

   安装内核模块

## **rmmod**



------

**特殊用途命令**

## **g++**

  g++ -c xxx.cpp -o xxx.o

  g++ xxx.o -o xxx

## **gcc**

## **ld**

   -l<lib> 需要注意链接顺序，

     以库a,b,c中，b与c之间循环依赖的情况下命令应为：ld xx.o -la -lb -lc -lb

     gcc xx.o -la -lb -lc -lb

     或者使用-Wl,--start-group/-Wl,--end-group 进行标识

     -Wl,--start-group -la -lb- -lc -Wl,--end-group

   -l:<lib> 库的文件名为<lib>，而不是lib<lib>.a的形式

## **ldconfig**

   对so建立必要的符号连接，并配置/etc/ld.so.conf等，方便ld定位so

   -p   打印安装的lib

## **ldd**

     查看依赖库

## **ltrace**

命令会跟踪进程的库函数调用,它会显现出哪个库函数被调用。

## **nm**

   查看库中的符号

   -u   示

## **objdump**

反编译

-S 反编译文件

## **pkg-config**

在`PKG_CONFIG_PATH`下的pc文件中读取编译参数

## **pstack**

   gstack

## **strace**

用于诊断、调试Linux用户空间跟踪器。我们用它来监控用户空间进程和内核的交互，比如系统调用、信号传递、进程状态变更等。


## **strip**

-x

## **ar**


pvchange -- Change attributes of a Physical Volume.

pvck -- Check Physical Volume metadata.

pvcreate -- Initialize a disk or partition for use by LVM.

pvdisplay -- Display attributes of a Physical Volume.

pvmove -- Move Physical Extents.

pvremove -- Remove a Physical Volume.

pvresize -- Resize a disk or partition in use by LVM2.

pvs -- Report information about Physical Volumes.

pvscan -- Scan all disks for Physical Volumes.

vgcfgbackup -- Backup Volume Group descriptor area.

vgcfgrestore -- Restore Volume Group descriptor area.

vgchange -- Change attributes of a Volume Group.

vgck -- Check Volume Group metadata.

vgconvert -- Convert Volume Group metadata format.

vgcreate -- Create a Volume Group.

vgdisplay -- Display attributes of Volume Groups.

vgexport -- Make volume Groups unknown to the system.

vgextend -- Add Physical Volumes to a Volume Group.

vgimport -- Make exported Volume Groups known to the system.

vgimportclone -- Import and rename duplicated Volume Group (e.g. a hardware snapshot).

vgmerge -- Merge two Volume Groups.

vgmknodes -- Recreate Volume Group directory and Logical Volume special files

vgreduce -- Reduce a Volume Group by removing one or more Physical Volumes.

vgremove -- Remove a Volume Group.

vgrename -- Rename a Volume Group.

vgs -- Report information about Volume Groups.

vgscan -- Scan all disks for Volume Groups and rebuild caches.

vgsplit -- Split a Volume Group into two, moving any logical volumes from one Volume Group to another by moving entire Physical Volumes.

lvchange -- Change attributes of a Logical Volume.

lvconvert -- Convert a Logical Volume from linear to mirror or snapshot.

lvcreate -- Create a Logical Volume in an existing Volume Group.

lvdisplay -- Display attributes of a Logical Volume.

lvextend -- Extend the size of a Logical Volume.

lvmchange -- Change attributes of the Logical Volume Manager.

lvmdiskscan -- Scan for all devices visible to LVM2.

lvmdump -- Create lvm2 information dumps for diagnostic purposes.

lvreduce -- Reduce the size of a Logical Volume.

lvremove -- Remove a Logical Volume.

lvrename -- Rename a Logical Volume.

lvresize -- Resize a Logical Volume.

lvs -- Report information about Logical Volumes.

lvscan -- Scan (all disks) for Logical Volumes.

## **notify-send**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -u level | low/normal/critical |
|  -i icon_path | |

```
sudo -u zhichaozhou DISPLAY=:0 \
     DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus \
     notify-send 'data transfer succeeded' 'message content body'
```

------

# **重要系统路径**

| 路径           | 含义          |
| -------------- | ------------- |
| `/dev/null`      | 空桶、黑洞 |
| `/dev/zero`      | 零桶、生成零的白洞 |
| `/dev/random`    | 源源不断的随机源、白噪洞 |
| `/etc/hosts`     | |
| `/etc/fstab`     | 磁盘文件表信息 |
| `/tmp`           | 临时文件，重启后会清理或10天后清理|
| `/var/log/messages` | 系统日志 |
| `/var/tmp`       | 30天后清理的临时文件|
| `/var/log`       | |


cgroups

| 路径                                                         | 含义          |
| ------------------------------------------------------------ | ------------- |
| `/sys/fs/cgroup/cpu/$group/cpu.cfs_period_us`                  | cpu 时间 |
| `/sys/fs/cgroup/cpu/$group/cpu.cfs_quota_us`                   | 使用限制， -1表示不限制 |
| `/sys/fs/cgroup/cpu/$group/cgroup.procs`                       | 向其写0，加入当前进程；向其写PID，该PID的所有线程会立即加入此cgroup|
| `/sys/fs/cgroup/cpu/$group/tasks`                              | 线程id( 一般而言，主线程的TID会与该进程的PID相同，子线程TID会大于PID)|
| `/sys/fs/cgroup/memory/$group/memory.limit_in_bytes`           | 内存使用总数上限|
| `/sys/fs/cgroup/memory/$group/memory.oom_control`              | 关闭oom，`oom_kill_disable 1`|
| `/sys/fs/cgroup/blkio/$group/blkio.throttle.read_bps_device`   | 磁盘读速上限|
| `/sys/fs/cgroup/blkio/$group/blkio.throttle.write_bps_device`  | 磁盘写速上限|

/proc

| 路径                            | 含义          |
| ------------------------------- | ------------- |
| `/proc/sys/kernel/core_pattern` | 系统core dump文件的名称格式  |
| `/proc/sys/kernel/latencytop`   | 打开latency性能统计  |
| `/proc/cpuinfo`                 | 记录CPU信息  |
| `/proc/meminfo`                 | 记录内存信息  |
| `/proc/swaps`                   | 记录交换区信息  |
| `/proc/net/tcp`                 | 当前的tcp连接信息  |
| `/proc/net/protocols`           | 支持的网络协议  |
| `/proc/${pid}/`                 |  |
| `/proc/${pid}/auxv`             | 传递给进程的ELF解释器信息  |
| `/proc/${pid}/cwd`              | 进程的当前路径  |
| `/proc/${pid}/cmdline`          | 启动命令行  |
| `/proc/${pid}/comm`             | 进程名  |
| `/proc/${pid}/environ`          | 启动环境变量  |
| `/proc/${pid}/limits`           | 进程的ulimit限制  |
| `/proc/${pid}/latency`          | 显示哪些代码造成的延时比较大，依赖`/proc/sys/kernel/latencytop` 为1  |
| `/proc/${pid}/maps`             | 进程的内存区域映射信息，字段含义：address，perms，offset，dev，inode，pathname  |
| `/proc/${pid}/cgroup`           |  |
| `/proc/${pid}/exe`              | binary 的符号连接  |
| `/proc/${pid}/io`               | 读写字节统计  |
| `/proc/${pid}/syscall`          | 在用的系统调用  |
| `/proc/${pid}/stack`            | 内核调用栈  |
| `/proc/${pid}/loginuid`         | 启动用户的登录id  |
| `/proc/${pid}/task/`            | 进程下的线程id  |
| `/proc/${pid}/wchan`            |wait时的内核态函数内容，可以用于反调试  |
| `/proc/${pid}/net/tcp`          | 当前的tcp连接信息  |
| `/proc/${pid}/statm`            | 进程所占用内存大小的统计信息，字段信息如下  |

1. 进程占用的总的内存；
2. 进程当前时刻占用的物理内存；
3. 同其它进程共享的内存；
4. 进程的代码段；
5. 共享库（从2.6版本起，这个值为0）；
6. 进程的堆栈；
7. dirty pages（从2.6版本起，这个值为0）


**文件解读**

**/proc/net/tcp sample data.tar**

sl   序号

local_address   本地IP地址(网络序)，端口号(本地主机序)的十六进制表达

rem_address   远端IP地址(网络序)，端口号(本地主机序)的十六进制表达

st   套接字状态，不同状态的数值表示如下：

| 数值 | 字值 | 状态              | 数值 | 字值 | 状态             |
| ---- | ---- | ----------------- | ---- | ---- | ---------------- |
| 1    | 01   | `TCP_ESTABLISHED` | 7    | 07   | `TCP_CLOSE`      |
| 2    | 02   | `TCP_SYN_SENT`    | 8    | 08   | `TCP_CLOSE_WAIT` |
| 3    | 03   | `TCP_SYN_RECV`    | 9    | 09   | `TCP_LAST_ACK`   |
| 4    | 04   | `TCP_FIN_WAIT1`   | 10   | 0A   | `TCP_LISTEN`     |
| 5    | 05   | `TCP_FIN_WAIT2`   | 11   | 0B   | `TCP_CLOSING`    |
| 6    | 06   | `TCP_TIME_WAIT`   |      |      |                  |

Tx_queue 发送队列数据长度，

Rx_queue 状态为01，表示接收队列队列中有数据，状态为0A，表示已完成连接的队列长度

Tr tm->when  定时器类型，如果为0，表示没有启动定时器。为1表示是重传定时器；为2表示连接定时器，FIN_WAIT_2定时器或TCP保活定时器；为3表示TIME_WAIT定时器；为4表示持续定时器。冒号后面为超时时间，单位是jiffies。例如：00:00000000

retrnsmt   超时重试次数

uid   用户id

timeout   持续定时器或保活定时器周期性发送出去但未被确认的TCP段数目，在收到ACK之后清零

inode   套接字对应的inode

\*   sock结构体的引用数

\*   sock结构实例的地址

\*   RTO，单位是clock_t

\*   用来计算延时确认的估值

\*   快速确认和是否启用的标志位的掩码

\*   当前的拥塞窗口大小

\*   如果是慢启动，显示其阈值，否则为-1

------

# **shell变量**

| 变量           | 含义          |
| -------------- | ------------- |
| `$?`  |  上一个命令退出的状态 |
| `$@`  | 参数列表 |
| `$#`   | 参数列表的长度 |
| `$$`  |  shell的pid，在脚本中可用于获取脚本运行进程的pid |
| `$0`   | shell的名称 |
| `$!`  |  上一个后台命令编号 |
| `$ENV` |  |
| `$HOME` |  主目录路径 |
| `$PWD`  | 当前目录 |
| `$IFS`  |  系统分隔符 |
| `$PATH` |  系统变量路径 |
| `$PPID` |  父进程pid |
| `$PS1`  |  命令提示符格式 |
| `$PS2`  |  命令提示符分隔号 |
| `$PS4` | |
| `$BASH` | Bash Shell的全路径 |
| `$BASH_SOURCE` | Bash脚本参数 |
| `$CDPATH` | 用于快速进入某个目录。 |
| `$HISTSIZE` | 历史记录数 |
| `$LOGNAME`  |当前用户的登录名 |
| `$HOSTNAME`  |指主机的名称 |
| `$SHELL`  |当前用户Shell类型 |
| `$LANGUGE`  |语言相关的环境变量，多语言可以修改此环境变量 |
| `$MAIL`  |当前用户的邮件存放目录 |
| `$LANG`  |  语言环境 |
| `$LC_ALL` | |
| `$LC_CTYPE` |  语言符号及其分类 |
| `$LC_NUMERIC` |   数字显示格式 |
| `$LC_COLLATE`|  比较和排序习惯 |
| `$LC_TIME` | 时间显示格式 |
| `$LC_MONETARY` | 货币单位 |
| `$LC_MESSAGE` | 信息主要是提示信息,错误信息,状态信息,标题,标签,按钮和菜单等 |
| `$LC_NAME`   | 姓名书写方式 |
| `$LC_ADDRESS` | 地址书写方式 |
| `$LC_TELEPHONE` | 电话号码书写方式 |
| `$LC_MEASUREMENT` | 度量衡表达方式 |
| `$LC_PAPER` | 默认纸张尺寸大小 |
| `$LC_IDENTIFICATION` | 对locale自身包含信息的概述 |
| `$RANDOM`  | 随机数 |
| `$LINENO`  | 刚执行的行号 |
| `$NLSPATH` |  应用程序搜索消息目录的目录路径 |
| `${n:def}` | n<1时，同$n |


变量处理

| 变量                           | 含义          |   备注             |
| ------------------------------ | ------------- | ------------------ |
| `${var:-val}`                  | 当var未赋值时，用val的值替换var | |
| `${var:=val}`                  | 当var未赋值时，用val的值赋值替换var | |
| `${var:+val}`                  | 当var赋值时，用val的值替换var | |
| `${var:?val}`                  | 当var未赋值时，用val的值替换var并报错误 | |
| `${#var}`                      | 获得var的长度 | |
| `${var:n}`                     | 从n起始的串 | |
| `${var:n:l}`                   | 从n起始，长度为l的串 | |
| `${var/pattern/replacement}`   | var 中第一个pattern 模式替换为 replacement | |
| `${var//pattern/replacement}`  | var中所有 pattern 模式全部替换为 replacment | |
| `${var#prefix}`                | 懒惰地去掉var的prefix前缀部分 | |
| `${var##prefix}`               | 贪心地去掉var的prefix前缀部分 | |
| `${var%suffix}`                | 懒惰地去掉var的suffix后缀部分 | |
| `${var%%suffix}`               | 贪心地去掉var的suffix后缀部分 | |
| `${var#*※}`                    | 去掉var的第一个※左面的部分 | |
| `${var%%※*}`                   | 去掉var的第一个※右面的部分 | |
| `${var##*※}`                   | 去掉var的最后一个※左面的部分 | |
| `${var%※*}`                    | 去掉var的最后一个※右面的部分 | |
| `${var^pattern}`               | 将pattern匹配的部分首字母大写 | Bash Only |
| `${var^^pattern}`              | 将pattern匹配的部分全部字母大写 | Bash Only |
| `${var,pattern}`               | 将pattern匹配的部分首字母小写 | Bash Only |
| `${var,,pattern}`              | 将pattern匹配的部分全部字母小写 | Bash Only |
| `${var@Q}`                     | 将var以单引号括起 | Bash Only |

注：**抹除**以▢为分隔的字符串一个字符串，其可以为一个较长的子串，`*`代表被**抹除**的部分
`${var#*▢}`    去掉最左面一个▢及其左面的部分      `${var##*▢}` 去掉最右面一个▢及其左面的部分
`${var%%▢*}` 去掉最左面一个▢及其右面的部分      `${var%▢*}`  去掉最右面一个▢及其右面的部分

**记忆方法**：`#(3) $(4) %(5)`，去左面的部分用#，因为它在键盘上在`$`的左面，同样`*`也在▢的左面。而双左或双右只需一个，否则就要两个

${!i} 遍历i从 1…$#


变量数值计算

```
  i=`expr $i + 1`;
  # let i+=1;
  # ((i++));
  # i=$[$i+1];
  # i=$(( $i + 1 ))
```

全局环境变量设置文件：`/etc/profile`、`/etc/bashrc`。

用户环境变量设置文件：`~/.bash_profile`、`~/.bashrc`。

读取顺序：① `/etc/profile`、② `~/.bash_profile`、③ `~/.bashrc`、④ `/etc/bashrc`。

| 环境变量不透出  | 环境变量透出  |      |
| --------------- | ------------- | ---- |
| `sh a.sh`       | `. a.sh`      |      |
| `bash a.sh`     | `source a.sh` |      |
| `./a.sh`        |               |      |


**#注意，这些变量不宜用于脚本中**

| 选项       |  含义                         |
| ---------- | ----------------------------- |
| `!!      ` | 上一条输入的命令              |
| `!^      ` | 上一条命令的第一个参数        |
| `!$      ` | 上一条命令的最后一个参数      |
| `!str    ` | 之前最近一条以’str’开头的命令 |
| `!?str?  ` | 之前最近一条包含’str’的命令   |
| `!n      ` | history中第n条命令            |
| `!-n     ` | history中最后n条命令          |

------

# **正则表达式**

|      |                  |      |                                            |
| ---- | ---------------- | ---- | ------------------------------------------ |
| `^`  | 行首             | `$`  | 行尾                                       |
| `[]` | 集合 eg:`[^a-z]` | `{}` | 次数范围 eg:`\{2,5\}`                      |
| `.`  | 任意个字         | `*`  | 若干前一个字符 eg:`000*` （代表两个0以上） |
| `.*` | 任意串           |      |                                            |


## **扩展表达式**

|      |                     |      |                                    |
| ---- | ------------------- | ---- | ---------------------------------- |
| `+`  | 一个或多个重复的    | `?`  | 零个或一个                         |
| `│`  | 或                  | `()` | 小组,后面可跟`+?*` eg: `g(|a|oo)d` |

|      |               |      |                 |
| ---- | ------------- | ---- | --------------- |
| `\d` | `[0-9]`       | `\D` | `[^0-9]`        |
| `\w` | `[a-zA-Z0-9]` | `\W` | `[^a-zA-Z0-9]`  |
| `\s` | `[\t\n\r\f]`  | `\S` | `[^\t\n\r\f]`   |

[[ '待匹配字符串' =~ 正则表达式 ]] #注意：要使用双方括号，[[ ]] 以及里面的空格

| 选项 [options]         | 含义         |
| ---------------------- | ------------ |
| `$BASH_REMATCH`        | 匹配到的内容 |
| `${BASH_REMATCH[0]}`   | 匹配到的子串 |

------

# **管道和重定向**

| 选项      | 含义          |
| --------- | ------------- |
| `<`       | 输入          |
| `<(xx)`   | 执行xx后的结果作为输入 |
| `>`       | 输出          |
| `<>`      | 中转对换，前后均接流、文件，e.g: `sed s/del/les/g file 1<>file #在文件中把del替换成les` |
| `>>`      | 追加          |
| `>│`      | 强制覆盖      |
| `│`       | 连接          |
| `<<`      | 标志标准输入的结束符，可以用于交互式命令的脚本编写 |
| `-<<`     | 同`<<`，但开头的tab会被去除 |
| `>&-`     | 表示将标准输出关闭 |
| `n>&-`    | 表示将n号输出关闭 |
| `n>&m`    | 表示将n号输出复制到m号 |
| `&>file`  | 标准输出、错误定向到文件 |
| `<&-`     | 表示关闭标准输入（键盘） |
| `n<&-`    | 表示将n号输入关闭 |
| `n<&m`    | 表示将m号输入复制到n号 |

```
sftp <user>@<host> << EOF
put file
.....
quit
EOF
```

流的优先级：先准备错误、输出，就绪后接入输出


| 选项 [options] | 含义          |
| -------------- | ------------- |
| /dev/fd/0      | 输入流，即从输入流读取 |
| /dev/fd/1      | 输出流，即向输出流写入 |
| /dev/fd/2      | 错误流，即从错误流写入 |

e.g.:

```
cat txt0 | sort | comm /dev/fd/0 <(cat txt1|sort)
= comm <(cat txt0|sort) <(cat txt|sort)
```

------

# **BASH脚本**

## 数组操作

### 1. 使用[]操作符

```
array[0]='zrong'
array[1]='jacky'
```

### 2. 使用()直接赋值

```
array=('zrong' 'jacky')
 # 或
array=([0]='zrong' [1]='jacky')
```


```
array=(`cat 'names.txt'`)      # 将每一行读取为数组的一个元素
echo ${#a[@]}                  # Len(a)
echo ${a[n]}                   # a[n-1], Start from 1
echo ${a[ * ]}                 # All (string form)
unset a[1]
echo ${a[@]:n:m}               # 从n到m的子数组
echo ${a[@]/3/100}
echo ${a[@]#※}                 # 删除开头的模式(懒惰匹配)
echo ${a[@]##※}                # 删除开头的模式(贪婪匹配)
echo ${a[@]/※/str1}            # 替换一次
echo ${a[@]//※/str1}           # 替换全部
newarr=(${a[@]} ${b[@]})       # merge array
array[0]='zrong'
array[1]='jacky'
```

## 条件判断

1）判断表达式

| 表达式                 | 含义          |
| ---------------------- | ------------- |
| `if test (expr)`       | |
| `if test !expr`        | |
| `test expr1 -a expr2`  | 两个表达式都为真 |
| `test expr1 -o expr2`  | 两个表达式有一个为真 |

2）判断字符串

| 表达式            | 含义          |
| ----------------- | ------------- |
| `test -n str`     | 字符串的长度非零 |
| `test -z str`     | 字符串的长度为零 |
| `test str1=str2`  | 字符串相等 |
| `test str1!=str2` |  字符串不等 |

3）判断整数

| 表达式               | 含义          |
| -------------------- | ------------- |
| `test num1 -eq num2` | 整数相等 |
| `test num1 -ge num2` | 整数1大于等于整数2 |
| `test num1 -gt num2` | 整数1大于整数2 |
| `test num1 -le num2` | 整数1小于等于整数2 |
| `test num1 -lt num2` | 整数1小于整数2 |
| `test num1 -ne num2` | 整数1不等于整数2 |

4）判断文件

| 表达式                 | 含义                              |
| ---------------------- | --------------------------------- |
| `test File1 -ef File2` | 两个文件具有同样的设备号和i结点号 |
| `test File1 -nt File2` | 文件1比文件2 新                   |
| `test File1 -ot File2` | 文件1比文件2 旧                   |
| `test -b File`         | 文件存在并且是块设备文件          |
| `test -c File`         | 文件存在并且是字符设备文件        |
| `test -d File`         | 文件存在并且是目录                |
| `test -e File`         | 文件存在                          |
| `test -f File`         | 文件存在并且是正规文件            |
| `test -g File`         | 文件存在并且是设置了组ID          |
| `test -G File`         | 文件存在并且属于有效组ID          |
| `test -h File`         | 文件存在并且是一个符号链接（同-L）|
| `test -k File`         | 文件存在并且设置了sticky位        |
| `test -b File`         | 文件存在并且是块设备文件          |
| `test -L File`         | 文件存在并且是一个符号链接（同-h）|
| `test -o File`         | 文件存在并且属于有效用户ID        |
| `test -p File`         | 文件存在并且是一个命名管道        |
| `test -r File`         | 文件存在并且可读                  |
| `test -S File`         | 文件存在并且是一个套接字          |
| `test -t FD`           | 文件描述符是在一个终端打开的      |
| `test -u File`         | 文件存在且设置了它的set-user-id位 |
| `test -w File`         | 文件存在并且可写                  |
| `test -x File`         | 文件存在并且可执行                |

---------

# **awk**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  -F            | 分隔符        |

awk的运行方式

1.命令行方式

   awk [-F field-separator] 'commands' input-file(s)

   其中，commands 是真正awk命令，[-F域分隔符]是可选的。 input-file(s) 是待处理的文件。

   在awk中，文件的每一行中，由域分隔符分开的每一项称为一个域。通常，在不指名-F域分隔符的情况下，默认的域分隔符是空格。

2.shell脚本方式

   将所有的awk命令插入一个文件，并使awk程序可执行，然后awk命令解释器作为脚本的首行，一遍通过键入脚本名称来调用。

   相当于shell脚本首行的：#!/bin/sh

   可以换成：#!/bin/awk 或 #!/usr/bin/awk -f

3.将所有的awk命令插入一个单独文件，然后调用：

   awk -f awk-script-file input-file(s)

   其中，-f选项加载awk-script-file中的awk脚本，input-file(s)跟上面的是一样的。

| 选项 [options] | 含义          |
| -------------- | ------------- |
| ARGC       | 命令行参数个数 |
| ARGV       | 命令行参数排列 |
| ENVIRON     | 支持队列中系统环境变量的使用 |
| FILENAME    |  awk浏览的文件名 |
| FNR       | 浏览文件的记录数 |
| FS        | 设置输入域分隔符，等价于命令行 -F选项 |
| NF        | 浏览记录的域的个数 |
| NR        | 已读的记录数 |
| OFS       | 输出域分隔符 |
| ORS       | 输出记录分隔符 |
| RS        | 控制记录分隔符 |
| BEGIN{}   | 在处理文件之前使用 |
| pattern   |  相当于一个if判断，满足条件的才会执行下面的action |
| {action}  |  在文件的每行上使用 |
| END{}   |  在处理文件结束后使用 |
| print   |  同shell的echo |
| printf  |  同C语言的printf |
| gsub(r,s) | 在整个$0中用s替代r |
| gsub(r,s,t) | 在整个t中用s替代r |
| index(s,t)  |返回s中字符串t的第一位置 |
| length(s) | 返回s长度 |
| match(s,r) | 测试s是否包含匹配r的字符串 |
| split(s,a,fs) | 在fs上将s分成序列a |
| sprint(fmt,exp) | 返回经fmt格式化后的exp |
| sub(r,s) | 用$0中最左边最长的子串代替s |
| substr(s,p) | 返回字符串s中从p开始的后缀部分 |
| substr(s,p,n) | 返回字符串s中从p开始长度为n的后缀部分 详细说明一下各个函数的使用方法。 |
| gensub(a,b,c[,d]) |全局替换，匹配正则a， 用b替换，c为指定替换目标是第几次匹配，d为指定替换目标是哪个域如$1,$2，若无d指$0，返回值为target替换后内容(未替换还是返回 target原内容)，与sub、gsub不同的是，target内容替换后不改变。 |
| gensub(/123/,"x",1,$1)| 替换$1中 第一次匹配到的123为字符x，返回值为$1替换后的内容，且$1的内容并没有改变 |
| gensub(/a(.\*)b/,"\\1",1) |返回值为匹配正则第1对()内的内容 |
| gensub(/a(.\*)b(.\*)c/,"\\2",1)| 返回值为匹配正则第2对()内的内容 |

```
awk '{if($0~/aaa/ && $0!~/bbb/)next}{print $0}'
sed '/aaa/{/bbb/{p};d}'


lsmod|awk 'BEGIN{print "digraph A {";print "rankdir=\"BT\""}{split($4,a,/,/);for(i=1;i<=length(a);i++) {print $1,"->",a[i],";"}}END{print "}"}'|dot -T svg -o /tmp/a.svg


lsmod|awk 'BEGIN{delete c[0]}{split($4,a,/,/);for(i=1;i<=length(a);i++){c[length(c)+1]=sprintf("%s -> %s;",$1,a[i])}}END{print "digraph A {";print "rankdir=\"BT\";";n=asort(c);for(i=1;i<n;i++){print c[i]} print "}"}'|dot -T svg -o /tmp/a.svg
```

------

# **系统信号**

| 选项 [options] | 含义          |
| -------------- | ------------- |
|  Ctrl-C  | 程序中断 |
|  Ctrl-D  | 登录退出 |
|  Ctrl-Z  | 程序挂起 |
|  Ctrl-\  | 手动吐核 |
|  Ctrl-U  | kill     |

可见stty -a

erase = ^?; kill = ^U; start = ^Q; stop = ^S; rprnt = ^R; werase = ^W; lnext = ^V; discard = ^O

------

# **终端控制**

颜色特效控制：

```
printf "\033[1;33m Hello World. \033[0m \n";
```

颜色如下(xx为颜色代码):

| 选项 [options] | 含义          |
| -------------- | ------------- |
| none           | "\033[0m"  |
| color          | "\033[0;xxm"  |
| dark color     | "\033[1;xxm"  |

颜色代码表：

|背景颜色 | 字颜色 | 颜色 |
|---------|--------|------|
|  40     |  30    | 黑   |
|  41     |  31    | 红   |
|  42     |  32    | 绿   |
|  43     |  33    | 黄   |
|  44     |  34    | 蓝   |
|  45     |  35    | 紫   |
|  46     |  36    | 深绿 |
|  47     |  37    | 白色 |

输出特效格式控制：

| 选项 [options] | 含义          |
| -------------- | ------------- |
| \033[0m        | 关闭所有属性 |
| \033[1m        | 设置高亮度 |
| \033[4m        | 下划线 |
| \033[5m        | 闪烁 |
| \033[7m        | 反显 |
| \033[8m        | 消隐 |
| \033[30m  --  \033[37m  | 设置前景色 |
| \033[40m  --  \033[47m  | 设置背景色 |

光标位置等的格式控制：

| 选项 [options] | 含义          |
| -------------- | ------------- |
| \033[nA    | 光标上移n行 |
| \033[nB    | 光标下移n行 |
| \033[nC    | 光标右移n行 |
| \033[nD    | 光标左移n行 |
| \033[y;xH   | 设置光标位置 |
| \033[2J    | 清屏 |
| \033[K    | 清除从光标到行尾的内容 |
| \033[s    | 保存光标位置 |
| \033[u    | 恢复光标位置 |
| \033[?25l  | 隐藏光标 |
| \033[?25h  | 显示光标 |

------

# **系统日志**

syslog日志服务：

1、守护进程：syslog

2、端口：514

3、配置文件:/etc/syslog.conf

4、常见日志文件:

| 选项 [options]         | 含义          |
| ---------------------- | ------------- |
| /var/log/dmesg         | 内核引导信息日志 |
| /var/log/message       | 标准系统错误信息日志 |
| /var/log/maillog       | 邮件系统信息日志 |
| /var/log/cron          | 计划任务日志 |
| /var/log/secure        | 安全信息日志 |
| /etc/apt/sources.list  | ubuntu/debian apt-get 源列表 |
| /etc/dphys-swapfile    | debian swap 配置 |

------

# **Examples**


## **@进制转换**

```
$((16#40C))
$((2#110101))
$((n#xxx)) n~(2,36)
echo "obase=64;123456"|bc
```


## **＠创建用户**

```
mkdir /home/<user>
useradd -d /home/<user> -s /bin/bash <user>
passwd <user>  #设置密码
visudo  #添加sudo权限
chown <user>:<user> /home/<user>
chmod 775 /home/<user>
#su <user>  #测试用户
```

## **＠修改swap大小**

```
swapoff -a
dd if=/dev/zero of=/home/swap bs=1024 count=2048000
mkswap /home/swap
swapon /home/swap
#echo "/home/swap swap swap defaults 0 0" >>/etc/fstab
```

## **@for 循环**

```
for i in `seq 10`; do
   echo $i
done

for i in ~/doc/ ; do
   echo $i
done

for ((i=0; i<10; i++)) {
  echo $i
}
```

循环写法

单行命令：do前done前要有分号

多行写法：do换行再写，for后可不带分号

## **@if 判断**

```
if [ -n "jjjjj" ]; then
   echo "not empty"
elif [ -z "a" ]; then
   echo impossible
else
   echo empty
fi
```

条件写法

单行命令：then前elif前else前要有分号

多行写法：then换行再写，for后可不带分号

## **@case 分支**

```
case a in
"1")
  echo "it is 1"
  ;;
"2"|"3*") echo "it is 2 or it starts with 3";;
"*")
  ;;
esac
```

\#分支写法

`case $var in 0) ;; *) ;; esac`

\#将当前目录下所有的文件中的$1模式，替换为$2

```
find . -type f | perl -ne 'chomp;print "\"$_\"\n" if -T $_' | xargs perl -pi -e "s/$1/$2/g"
```

## **@计算表达式**

```
square() {
   let "res = ($1 * $1 + 1) * 3"
   return $res
}


square 8
echo $?
```

## **@添加新管理员用户**

```
mkdir /home/<username>
useradd <username> -d /home/<username>
usermod <username> -G <group>
passwd <username>
# <password>
# <password>
visudo
# <username>  ALL=(ALL:ALL) ALL
chown /home/<username> <username>:<group>
```

## **@按行读取文件**

```
# method 1 (按分隔符读文件)
while read line; do
  echo $line
done < $filename

# method 2 (按行读取文件)
cat $filename | while read line; do
  echo $line
done

awk '{print $1,$2}' gbk-ext.txt|while read l; do echo $l;done|head
<?f8 a1?>
<?f8 b8?>
<?f8 ba?>
<?a6 ec?>
<?aa a5?>
<?aa ad?>
<?aa b2?>
<?aa ce?>
<?ab e7?>
<?ab e9?>


# method 3 (按分隔符读文件)
for line in `cat filename` #$(<file)
do
  echo $line
done

for l in `awk '{print $1,$2}' gbk-ext.txt`;do echo $l;done|head
<?f8
a1?>
<?f8
b8?>
<?f8
ba?>
<?a6
ec?>
<?aa
a5?>

```

总结：以 `< $filename` 的方式读取的文件是以分隔符，cat是以行来读的

按行分段读取文件，分隔符为$IFS

`cat a | while read a b c d; do echo \"$a\" \"$b\" \"$c\" \"$d\"; done`

## **@自输密码的脚本：**

```
function remoterun(){
  spawn /usr/bin/ssh $1 #root@10.99.0.245
  expect "*password:"
  send "$2\r"
  expect "*~$"
  send "$3\r"  #"cd /root"
  expect "*~$"
  send "exit\r"
  expect eof
}
```

## **@免密码sudo**

echo "password" | sudo -S $command

\# 或在 /etc/**sudoers** 的结尾添加如下一行（注意用 sudo visudo 编辑）：

<username> ALL=(ALL) NOPASSWD:ALL


## **@auto mount Network file system**

```
sudo apt install nfs-kernel-server
sudo mkdir /mnt/myshareddir
sudo chown nobody:nogroup /mnt/myshareddir #no-one is owner
sudo chmod 777 /mnt/myshareddir #everyone can modify files

# All the directives below use the options rw,
#     which enables both read and write, sync, which writes changes
#     to disk before allowing users to access the modified file, and
#     no_subtree_check, which means NFS doesn’t check if each subdirectory
#     is accessible to the user.
cat > /etc/exports <<EOF
/mnt/myshareddir {clientIP}(rw,sync,no_subtree_check)
/mnt/myshareddir {clientIP-1}(rw,sync,no_subtree_check){clientIP-2}(...){clientIP-3}(...)
/mnt/myshareddir {subnetIP}/{subnetMask}(rw,sync,no_subtree_check)
EOF

sudo exportfs -a #making the file share available
sudo systemctl restart nfs-kernel-server #restarting the NFS kernel
```

\* linux

```
sudo apt-get install autofs
echo "/- /etc/auto.nfs" | sudo tee -a /etc/auto.master
echo "/mnt/data -fstype=nfs,intr 10.12.1.100:/mnt/data" | sudo tee -a /etc/auto.nfs
sudo systemctl restart autofs
```

\* mac

```
sudo mkdir -p /mnt/data
echo "/- auto_nfs -nobrowse,nosuid" | sudo tee -a /etc/auto_master
echo "/mnt/data -fstype=nfs,rsize=65536,wsize=65536,intr,hard,tcp,rdirplus,readahead=128 nfs://10.12.1.100:/mnt/data" | sudo tee -a /etc/auto_nfs
sudo automount -cv
```


## **@打开socket(bash Only)**

```
exec 8<>/dev/tcp/127.0.0.1/11211       #使用文件描述符8以<>(<读>写)方式，打开127.0.0.1的tcp11211端口
ls -l /proc/self/fd                    #查看打开的连接8
echo -e "stats" >&8                    #向socket写入数据
cat <&8                                #从socket读入数据
exec 8<&-                              #关闭socket读
exec 8>&-                              #关闭socket写
```

## **@将静态库编为动态库**

ar -x abc.a

gcc -shared -o abc.so a.o b.o c.o

## **@Linux文件夹打包命令**

| 文件类型       | 使用的命令            | 解包                                 | 打包/压缩                      | comment             |
| -------------- | --------------------- | ------------------------------------ | ------------------------------ | ------------------- |
| `.bz2/.bz`     | `bunzip2/bzip2`       | `bunzip2 bzip2 -d`                   | `bzip2 -z`                     |                     |
| `.gz`          | `gunzip/gzip`         | `gunzip gzip -d`                     | `gzip`                         |                     |
| `.rar`         | `rar`                 | `rar e `                             | `rar a`                        |                     |
| `.tar`         | `tar`                 | `tar -xvf  <tarfile> <directory>`    | `tar -cvf`                     | tar是打包，不是压缩 |
| `.tar.bz2`     | `tar`                 | `tar -jxvf <bzfile> <directory>`     | `tar -jcvf`                    |                     |
| `.tar.gz/.tgz` | `tar`                 | `tar -zxvf <tgzfile> -C <directory>` | `tar -zcvf xx.tgz xxx/`        |                     |
| `.tar.Z`       | `tar`                 | `tar -Zxvf <Zfile> <directory>`      | `tar -Zcvf <Zfile>`            |                     |
| `.Z`           | `uncompress/compress` | `uncompress`                         | `compress`                     |                     |
| `.zip`         | `unzip/zip`           | `unzip [-d <dir>] <zipfile>`         | `zip -r <zipfile> <directory>` |                     |
| `.xz`          | `xz`                  | `xz -d file`                         | `xz -z -k file`                |                     |
| `.7z`          | `7zzs`                | `7zzs x <file.7z>`                   | `7zzs a <file.7z> <files...>`  | [7zzs下载](https://www.7-zip.org/a/7z2201-linux-x64.tar.xz)  |
| `.deb`         | `ar`                  | `ar -x <target>`                     | ``                             |                     |

```
tar.xz tar -xvf
gzip xxx.tar # xxx.tar.gz
gunzip xxx.tar.gz # xxx.tar
```

```bash
# uncompress zlib compressed data
printf "\x1f\x8b\x08\x00\x00\x00\x00\x00" |cat - <zlib-compressed-file> |gzip -dc

# uncompress gzip compressed data
gzip -dc file
```


下载deb文件：

```
apt-get download $PACKAGE && apt-cache depends -i $PACKAGE|awk '/Depends:/ {print $2}' | xargs apt-get download
```

tar 文件夹在后，tar包在前

六种无损数据压缩算法：

Brotli、Deflate、Zopfli、LZMA、LZHAM、Bzip2 、snappy

# --i--
获取 gpg 公钥
 sudo gpg --keyserver keyserver.ubuntu.com --recv-keys 467B942D3A79BD29
重复执行多次不会改变，也不影响 (幂等)

导出公钥，加入到 apt 信任密钥
 sudo gpg --export --armor 467B942D3A79BD29 | sudo apt-key add -
 sudo apt update

**索引**

线上查询及帮助命令(2个)

help：查看Linux内置命令的帮助，比如cd命令。

文件和目录操作命令(18个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| rmdir | 全拼remove empty directories，功能是删除空目录 |
| tree | 功能是以树形结构显示目录下的内容 |
| basename | 显示文件名或目录名 |
| dirname | 显示文件或目录路径 |
| chattr | 改变文件的扩展属性 |
| lsattr | 查看文件扩展属性 |
| file | 显示文件的类型 |
| md5sum | 计算和校验文件的MD5值 |

查看文件及内容处理命令(21个)
| 选项 [options] | 含义    |
| -------------- | ------- |
| iconv | 转换文件的编码格式 |
| dos2unix | 将DOS格式文件转换成UNIX格式 |


信息显示命令(11个)

free：查看系统内存。


用户管理命令(10个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| useradd | 添加用户 |
| usermod | 修改系统已经存在的用户属性 |
| userdel | 删除用户 |
| groupadd | 添加用户组 |
| passwd | 修改用户密码 |
| chage | 修改用户密码有效期限 |
| id | 查看用户的uid,gid及归属的用户组 |



基础网络操作命令(11个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| ping | 测试主机之间网络的连通性 |
| route | 显示和设置linux系统的路由表 |
| ifconfig | 查看、配置、启用或禁用网络接口的命令 |
| ifup | 启动网卡 |
| ifdown | 关闭网卡 |


深入网络操作命令(9个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| mail | 发送和接收邮件 |
| mutt | 邮件管理命令 |
| dig | 查找DNS解析过程 |
| host | 查询DNS的命令 |
| traceroute | 追踪数据传输路由状况 |
| tcpdump | 命令行的抓包工具 |

有关磁盘与文件系统的命令(16个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| fsck | 检查并修复Linux文件系统 |
| dumpe2fs | 导出ext2/ext3/ext4文件系统信息 |
| dumpe | xt2/3/4文件系统备份工具 |
| fdisk | 磁盘分区命令，适用于2TB以下磁盘分区 |
| parted | 磁盘分区命令，没有磁盘大小限制，常用于2TB以下磁盘分区 |
| partprobe | 更新内核的硬盘分区表信息 |
| e2fsck | 检查ext2/ext3/ext4类型文件系统 |
| mkswap | 创建Linux交换分区 |
| swapon | 启用交换分区 |
| swapoff | 关闭交换分区 |
| sync | 将内存缓冲区内的数据写入磁盘 |
| resize2fs | 调整ext2/ext3/ext4文件系统大小 |

系统权限及用户授权相关命令(4个)

umask：显示或设置权限掩码。

查看系统用户登陆信息的命令(7个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| lastlog | 显示系统中所有用户最近一次登录信息 |
| users | 显示当前登录系统的所有用户的用户列表 |
| finger | 查找并显示用户信息 |

内置命令及其它(19个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| clear | 清除屏幕，简称清屏 |
| eject | 弹出光驱 |
| exec | 调用并执行指令的命令 |
| export | 设置或者显示环境变量 |
| unset | 删除变量或函数 |
| type | 用于判断另外一个命令是否是内置命令 |

系统管理与性能监视命令(9个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| chkconfig | 管理Linux系统开机启动项 |
| vmstat | 虚拟内存统计 |
| mpstat | 显示各个可用CPU的状态统计 |
| iostat | 统计系统IO |
| sar | 全面地获取系统的CPU、运行队列、磁盘 I/O、分页(交换区)、内存、 CPU中断和网络等性能数据 |

关机/重启/注销和查看系统信息的命令(6个)

| 选项 [options] | 含义    |
| -------------- | ------- |
| shutdown | 关机 |
| halt | 关机 |
| poweroff | 关闭电源 |
| logout | 退出当前登录的Shell |
| exit | 退出当前登录的Shell |

进程管理相关命令(15个)

pgrep：查找匹配条件的进程。

init：切换运行级别。
