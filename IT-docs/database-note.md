# SQLite

sqlite3 linux（centos）一般会自带

.help #帮助
.open xxx.db
.table #列出所有表
.header on #显示表头
.schema <table name> #显示该表创建语句
.read xxx.sql
select * from sqlite_master where type="table"; #列出所有表结构
select * from sqlite_master where type="table" and name="<table name>"; #列出名叫<table name>的表结构



-------------
#     MySQL





mysql -h<host> -P<port> -u<user> -p<password>
mysql>
?         (\?) Synonym for `help'.
clear     (\c) Clear the current input statement.
connect   (\r) Reconnect to the server. Optional arguments are db and host.
delimiter (\d) Set statement delimiter.
edit      (\e) Edit command with $EDITOR.
ego       (\G) Send command to mysql server, display result vertically.
exit      (\q) Exit mysql. Same as quit.
go        (\g) Send command to mysql server.
help      (\h) Display this help.
nopager   (\n) Disable pager, print to stdout.
notee     (\t) Don't write into outfile.
pager     (\P) Set PAGER [to_pager]. Print the query results via PAGER.
print     (\p) Print current command.
prompt    (\R) Change your mysql prompt.
quit      (\q) Quit mysql.
rehash    (\#) Rebuild completion hash.
source    (\.) Execute an SQL script file. Takes a file name as an argument.
status    (\s) Get status information from the server.
system    (\!) Execute a system shell command.
tee       (\T) Set outfile [to_outfile]. Append everything into given outfile.
use       (\u) Use another database. Takes database name as argument.
charset   (\C) Switch to another charset. Might be needed for processing binlog with multi-byte charsets.
warnings  (\W) Show warnings after every statement.
nowarning (\w) Don't show warnings after every statement.
resetconnection(\x) Clean session context.

show tables;

mysqldump

-- dump some query result
mysqldump -u<user> -p<password> -h<host> <database> [<tablename>] a -w "sql statement where" --lock-all-tables > <file>

-- dump special table
mysqldump -u<user> -p<password> -h<host> <database> <table>

-------------
# Postgres

| 命令            |  描述                                                                |
| --------------- | -------------------------------------------------------------------- |
| \d [table]      | 列出数据库中的表，或（如果声明了）表 table 的列/字段．如果表名是用统配符 （“*”）声明的，列出所有表和表的列/字段信息． |
| \da             | 列出所有可用聚集． |
| \dd object      | 列出 pg_description 里对声明的对象的描述，对象可以是一个表，表中的列/字段，类型，操作符或聚集．小技巧：并非所有对象在 pg_description 里有描述．此后期命令在快速获取 Postgres 内部特性时很有用． |
| \df             | 列出函数． |
| \di             | 只列出索引． |
| \do             | 只列出操作符． |
| \ds             | 只列出序列． |
| \dS             | 列出系统表和索引． |
| \dt             | 只列出非系统表． |
| \dT             | 列出类型． |
| \e [filename]   | 编辑当前查询缓冲或文件 filename 的内容． |
| \E [filename]   | 编辑当前查询缓冲或文件 filename 的内容并且在编辑结束后执行之． |
| \f [separator]  | 设置域分隔符．缺省是单个空白． |
| \g [filename/command] | 将当前查询输入缓冲送给后端并且（可选的）将输出放到 filename 或通过管道将输出送给一个分离的Unix shell 用以执行 command． |
| \h [command]          | 给出声明的 SQL 命令的语法帮助．如果 command 不是一个定义的 SQL 命令（或在 psql 里没有文档），或没有声明 command ，这时 psql将列出可获得帮助的所有命令的列表．如果命令 command 是一个通配符（“*”），则给出所有 SQL 命令的语法帮助． |
| \H                   | 切换 HTML3 输出．等效于 -H 命令行选项． |
| \i filename | 从文件 filename 中读取查询到输入缓冲． |
| \l                  | 列出服务器上所有数据库． |
| \m                  | 切换老式监视器样的表输出，这时表周围有边界字符包围着．这是标准 SQL 输出．缺省时，psql 只包括列/字段间的分隔符． |
| \o [filename/command] | 将后面的查询结果输出到文件 filename 或通过管道将后面结果输出到一个独立的Unix shell 里执行 command．如果没有声明参数，将查询结果输出到 stdout． |
| \p                    | 打印当前查询缓冲区． |
| \q                    | 退出 psql 程序． |
| \r                    | 重置（清空）查询缓冲区． |
| \s [filename]       | 将命令行历史打印出或是存放到 filename．如果省略 filename ，将不会把后继的命令存放到历史文件中．此选项只有在 psql 配置成使用输入行时才有效． |
| \t                    | 切换输出的列/字段名的信息头和行记数脚注（缺省是开）． |
| \T table_options      | 允许你在使用HTML 3.0 格式输出时声明放在表 table ... 中的标记选项．例如，border 将给你的表以边框．这必须和 \H 后期命令一起使用． |
| \x                    | 切换扩展行格式．当打开时，每一行将在左边打印列/字段名而在右边打印列/字段值．这对于那些不能在一行输出的超长行是很有用的．HTML 行输出模式也支持这个标记． |
| \w filename           | 将当前查询缓冲区输出到文件 filename． |
| \z                    | 生成一个带有正确 ACL（赋予/禁止 权限）的数据库中所有表的输出列表． |
| \! [command]        | 回到一个独立的Unix shell或执行一个Unix 命令 command． |
| \?                    | 获得关于反斜杠 (“\”) 命令的帮助． |
| \c[onnect] [数据库名/-[用户名称]]|     联接到新的数据库 (当前为 "test") |
| \cd [目录名]          | 改变当前的工作目录 |
| \copyright            | 显示 PostgreSQL 用法和发布信息 |
| \encoding [编码]      |  显示或设置客户端编码 |
| \h [名字]             | SQL 命令的语法帮助, 用 * 可以看所有命令的帮助 |
| \q                    | 退出 psql |
| \set [名字 [值]]      | 设置内部变量, 如果没有参数就列出所有 |
| \timing               | 查询计时开关切换 (目前是 关闭) |
| \unset 名字           | 取消(删除)内部变量 |
| \! [命令]             | 在 shell 里执行命令或者开始一个交互的 shell |




| 参数            |  描述                                                                |
| --------------- | -------------------------------------------------------------------- |
| -c, --command=COMMAND  |  run only single command (SQL or internal) and exit |
| -d, --dbname=DBNAME    |  database name to connect to (default: "$USER") |
| -f, --file=FILENAME    |  execute commands from file, then exit |
| -l, --list             |  list available databases, then exit |
| -v, --set=, --variable=NAME=VALUE | set psql variable NAME to VALUE (e.g., -v ON_ERROR_STOP=1) |
| -V, --version          | output version information, then exit |
| -X, --no-psqlrc        | do not read startup file (~/.psqlrc) |
| -1 ("one"), --single-transaction | execute as a single transaction (if non-interactive) |
| -?, --help[=options]   |  show this help, then exit |
| --help=commands        |  list backslash commands, then exit |
| --help=variables       |  list special variables, then exit |
| -a, --echo-all          |  echo all input from script |
| -b, --echo-errors       |  echo failed commands |
| -e, --echo-queries      |  echo commands sent to server |
| -E, --echo-hidden       |  display queries that internal commands generate |
| -L, --log-file=FILENAME |  send session log to file |
| -n, --no-readline       |  disable enhanced command line editing (readline) |
| -o, --output=FILENAME   |  send query results to file (or │pipe) |
| -q, --quiet             |  run quietly (no messages, only query output) |
| -s, --single-step       |  single-step mode (confirm each query) |
| -S, --single-line       |  single-line mode (end of line terminates SQL command) |
| -A, --no-align          | unaligned table output mode |
| -F, --field-separator=STRING | field separator for unaligned output (default: "│") |
| -H, --html              | HTML table output mode |
| -P, --pset=VAR[=ARG]    | set printing option VAR to ARG (see \pset command) |
| -R, --record-separator=STRING | record separator for unaligned output (default: newline) |
| -t, --tuples-only       | print rows only |
| -T, --table-attr=TEXT   | set HTML table tag attributes (e.g., width, border) |
| -x, --expanded          | turn on expanded table output |
| -z, --field-separator-zero | set field separator for unaligned output to zero byte |
| -0, --record-separator-zero| set record separator for unaligned output to zero byte |
| -h, --host=HOSTNAME     | database server host or socket directory (default: "/var/run/postgresql") |
| -p, --port=PORT         | database server port (default: "5432") |
| -U, --username=USERNAME | database user name (default: "$USER") |
| -w, --no-password       | never prompt for password |
| -W, --password          | force password prompt (should happen automatically) |

