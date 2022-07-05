# ** go build**

通过go build加上要编译的Go源文件名，我们即可得到一个可执行文件，默认情况下这个文件的名字为源文件名字去掉.go后缀。

```
$ go build hellogo.go
$ ls
hellogo* hellogo.go
```

当然我们也 可以通过-o选项来指定其他名字：

```
$ go build -o myfirstgo hellogo.go
$ ls
myfirstgo* hellogo.go
```

如果我们在go-examples目录下直接执行go build命令，后面不带文件名，我们将得到一个与目录名同名的可执行文件：


```
$ go build
$ ls
go-examples* hellogo.go
```

交差编译：

```
env CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build
```



# **go mod**

```
go mod init $modname
```



# **go install**

与build命令相比，install命令在编译源码后还会将可执行文件或库文件安装到约定的目录下。

```
go install <uri>  #等价于下面的两条命令

go build -o <binname> [<](http://git.xiaojukeji.com/geomining/OrderRouteTask/cmd)uri>
mv   <binname> $GOPATH/bin
```

- go install编译出的可执行文件以其所在目录名(DIR)命名
- go install将可执行文件安装到与src同级别的bin目录下，bin目录由go install自动创建
- go install将可执行文件依赖的各种package编译后，放在与src同级别的pkg目录下.

# **go get**

等同于从指定的URL下载源码到$GOPATH/src下，并执行go install URL包名。

# **go run**

```
$ go run path/filename.go
```

# **go test**

执行单元测试，

```
$ go test -v --run Test____ <package path> --count=1
$ go test -c -covermode=count -o main.test
$ ./main.test -systemTest -test.coverprofile coverage.cov
$ go tool cover -html=./coverage.cov -o coverage.html
```

# **go tool**

```bash
$ go tool cover -html=./coverage.cov -o coverage.html
```

# **go generate**

```golang
//go:generate go run github.com/deepmap/oapi-codegen/cmd/oapi-codegen --package map_delivery -o map_delivery.gen.go map_delivery.yaml
```



# **go embed**
```
//go:embed database_changelog.yml
var databaseMigrations []byte
```

# **go env**

打印go的环境变量。

# **go doc**

```bash
$ go doc # 生成文档文本
```

```
package example // import "example"

func NewGenerator(
  caller lib.Caller,
  timeoutNs time.Duration,
  lps uint32,
  durationNs time.Duration,
  resultCh chan *lib.CallResult) (lib.Generator, error)
```

```
$ go doc -u example.Generator # 生成某个函数、结构等符号的文档文本
```

# **godoc**

```
$ godoc -http=:8080 -index # 在本机开启Go文档Web服务器，端口为9090
$ godoc -q fmt #查询fmt，列出所有对fmt的引用
```

# **go tool pprof**

# **go tool cgo**


```
// #cgo CFLAGS: -DPNG_DEBUG=1
// #cgo linux CFLAGS: -DLINUX=1
// #cgo LDFLAGS: -lpng
// #include <png.h>

import "C"

C.printf(…)
```

# **go tool vet**

命令go vet是一个用于检查Go语言源码中静态错误的简单工具。与大多数Go命令一样，go vet命令可以接受-n标记和-x标记。-n标记用于只打印流程中执行的命令而不真正执行它们。-x用于打印并执行。

go 1.11版本新增了 GOPROXY 环境变量，go get会根据这个环境变量来决定去哪里取引入库的代码

其中，[https://goproxy.io](https://goproxy.io/) 是一个goproxy.io这个开源项目提供的公开代理服务。

export GOPROXY=[https://goproxy.io](https://goproxy.io/)

------

	"github.com/jessevdk/go-flags"
  "github.com/golang-migrate/migrate"



------

# **入门时的助记**

* 没有三目运算符，前自增/减。自增减不返回数值
* 类型定义在后，返回值在后
* ^ 可用作单目运算符，表示取反，同C语言的：~
* defer 推迟一句，进入defer栈

_ 可用作点位符


chan的有buffer和无buffer的区别：写满后写入阻塞

空读阻塞、写满阻塞

switch、select的case是不需要加break的

类型转换： 基本型：`int32(varname)` 接口型：`varname.(*interface{})`

```
var data []byte = []byte(str)
var str string = string(data[:])
resp, _ := http.Get(url)
buf, _ := ioutil.ReadAll(resp.Body)
str := string(buf)
```

itoa //在const 中模拟enum

类型使用：

```
var maps map[string]int64 //string为键，int64为值
var array = [...]uint{0, 9, 2, 5, 4, 31}
```

```
// 方法
func (iPhone IPhone) call() int {
  fmt.Println("I am iPhone, I can call you!")
  return 0
}

type father struct {
  name string
}

type laowang struct {
  surname string
}

type son struct {
  father //继承
  laowang //继承
  play string
}
```

interface 做为前中后参数是，须为

var (
  a int
  ch chan int
)

ch <- a // will go on, if not set; otherwise wait <- ch

a <- ch // will wait until ch <- ed


sync

```
sync.Mutex

Lock()
Unlock()

sync.RWMutex
Lock() //写锁
Unlock() //解写锁
RLock() //读锁
RUnlock()//解读锁

sync.Pool

this.New = func()interface{}{return xxx;}

Get()
Put()
```


```
type _type_name_ struct {
  ......
}

var xxx _type_name_
var xxx _type_name_{}
var xxx _type_name_{.......}

xxx := _type_name_{}
xxx := _type_name_{......}
```

Array 是定长的，如[3]bool{true, true, false}

Slice 是变长的，定义是没有长度定义如[]bool{true, true, false}

nil 是可以len(),cap(), append(s, 0)的

append(slice, slice...)// ...表示解为分立的单个参数的调用

\#a=append(a,xx)



range 是用于遍历Slice/Array，

  channel until it has been closed

map[key_type]value_type

delete(m, key)  #影响m

select、switch 可以不加break，但加上会跟不加一致。要跳出外层的循环，可以用break label

**方法接受器是指针还是对象的区别**：

- 对象接收器在调用时会产生一个新对象，比较适合不对原始对象进行修改的情况，比如C++中后const的成员函数
- 指针接收器会直接对指向的对象进行操作，比较适合原本内容变动的操作

对于接口函数的实现，指针接收器只能使用指针对接口的赋值，而对象接收器则指针、对象均可。

------

# **Go高性能写法**

字符串拼接：

```
bb := new(bytes.Buffer)
bb.WriteString(str1)
bb.WriteString(str2)
bb.String() // or bb.Bytes()
```

池：

```
var BufferPool = sync.Pool{
  New: func() interface{} {
    return new(bytes.Buffer)
  }
}

bb := BufferPool.Get().(*bytes.Buffer)

// use bb
BufferPool.Put(bb) // put bb back after using
```


# **实例**

// 图形

```golang
package main

import (
 "bytes"
 "github.com/blushft/go-diagrams/diagram"
 "github.com/blushft/go-diagrams/nodes/gcp"
 "io/ioutil"
 "log"
 "os"
 "os/exec"
)

func main() {
 d, err := diagram.New(diagram.Filename("app"), diagram.Label("App"), diagram.Direction("LR"))
 if err != nil {
   log.Fatal(err)
 }

 dns := gcp.Network.Dns(diagram.NodeLabel("DNS"))
 lb := gcp.Network.LoadBalancing(diagram.NodeLabel("NLB"))
 cache := gcp.Database.Memorystore(diagram.NodeLabel("Cache"))
 db := gcp.Database.Sql(diagram.NodeLabel("Database"))

 dc := diagram.NewGroup("GCP")
   dc.NewGroup("services").
   Label("Service Layer").
   Add(
     gcp.Compute.ComputeEngine(diagram.NodeLabel("Server 1")),
     gcp.Compute.ComputeEngine(diagram.NodeLabel("Server 2")),
     gcp.Compute.ComputeEngine(diagram.NodeLabel("Server 3")),
   ).
   ConnectAllFrom(lb.ID(), diagram.Forward()).
   ConnectAllTo(cache.ID(), diagram.Forward())

 dc.NewGroup("data").Label("Data Layer").Add(cache, db).Connect(cache, db)

 d.Connect(dns, lb, diagram.Forward()).Group(dc)

 if err := d.Render(); err != nil {
   log.Fatal(err)
 }

 os.Chdir("go-diagrams")
 log.Println("changed")
 cmd := exec.Command("dot", "-Tpng", "app.dot")

 var sout bytes.Buffer
 cmd.Stdout = &sout
 if err = cmd.Run(); err != nil {
   log.Fatal(err)
 }

 if err = ioutil.WriteFile("app.png", sout.Bytes(), 0666); err != nil {
   log.Fatal("Writefile Error =", err)
 }

 cmd = exec.Command("xdg-open", "app.png")
 if err = cmd.Run(); err != nil {
   log.Fatal(err)
 }
}
```
