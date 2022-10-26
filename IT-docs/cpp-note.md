C++ notes
=========

```
  BoostMultiPolygon reduced_multi_polygon;
  // Reduce to smallest number of polys
  boost::geometry::union_(
      multi_polygon_, BoostPolygon(), reduced_multi_polygon);
  std::string polygon_wkb_str;
  boost::geometry::write_wkb(
      reduced_multi_polygon, std::back_inserter(polygon_wkb_str));
```

# Glog & GFlags

```
-logtostderr 1
-alsologtostderr
GLOG_v=2

gflags::ParseCommandLineFlags(&argc, &argv, true);
google::InitGoogleLogging(argv[0]);

LOG(INFO)<<"";
VLOG(2)<<"";



DEFINE_string(var, defval, hint)
DEFINE_int32(var, defval, hint)
DEFINE_int64(var, defval, hint)
DEFINE_float(var, defval, hint)
DEFINE_double(var, defval, hint)
DEFINE_bool(var, defval, hint)

DECLARE_string(var)
DECLARE_int32(var)
DECLARE_int64(var)
DECLARE_float(var)
DECLARE_double(var)
DECLARE_bool(var)
```



# C++11
* auto (The auto keyword)
* `char16_t` 和 `char32_t`，还有支持这两类型的新字面值
* constexpr
* decltype
* 默认说明符 (default specifier)
* 委托构造函数 (Delegating constructing)
* delete 关键字 (delete)
* Enum 类 (Enum)
* 外部模板
* Lambda 表达式 (Lambda) 和 Lambda 表达式捕获 (captures)
* long long int (long long int)
* 移动构造函数和移动赋值 (Move Constructors and move assignment)
* noexcept 说明符 (noexcept)
* nullptr (nullptr)
* override 和 final 说明符 (override and final specifiers)
* 基于范围的 for 语句 (for-each)
* 右值引用 (R-value references)
* `static_cast`
* `std::initializer_list`
* 尾随返回类型语法 (trailing return type)   // template <class Container> auto begin (Container& cont) -> decltype (cont.begin());
* 类型别名 (Type aliases)
* typedef 可以对泛型类使用
* 标准初始化 (Uniform Initialization)
* 用户定义的字面值
* 可变模板
>> 可以被正确的解释为关闭泛型对象
同时，在 C++ 的标准库中添加了以下新类以便于使用：

更好的支持多线程和本地线程存储功能
Hash 表
随机数的生成 (Random number generation)
引用封装(Object slicing)
正则表达式
`std::auto_ptr` 已被弃用
`std::tuple` 被添加 (Return values by value)
`std::unique_ptr` 智能指针被添加

# C++14
* 聚合成员初始化 (Aggregate member initialization)
* 二进制字面值 (Binary literals)
* `[[deprecated]]` 属性
* 数字分隔符 (Digit Separator)
* 函数返回类型推测 (auto)
* 通用 Lambda 表达式 (Lambda)
* 简单的constexpr 功能
* 变量泛型
* `std::make_unique`

# C++17
* `__has_include` 预处理说明符，用于检查可选的头文件是否可用
* if 语句可以在编译时进行解译
* 可以在 if 和 switch 语句中进行初始值预设
* inline 变量
* Fold 表达式
* 嵌套命名空间可以被定义为 namespace X::Y 形式
* 移除了 `std::auto_ptr` 和其他不推荐的类型
* `static_cast` 不再需要诊断文本消息参数
* `std::any`
* `std::byte`
* `std::filesystem`
* `std::optional`
* `std::shared_ptr`可以用来管理 C-类型数组，但是`std::make_shared`不可以创建对应 std::shared_ptr
* `std::size`
* `std::string_view`
* 结构化绑定声明
* 构造函数的泛型推测
* Trigraphs 被移除
* typename 可以在泛型参数中使用
* UTF-8 字符字面值


`static_assert`     无须运行的断言，编译期的检查

# 指向成员函数的指针

```
typedef void (class_name::*function_type_name)(args) const;     //定义函数指错类型
function_type_name    pfunc_;      //声明成员变量

pfunc_ = &class_name::function_name;     //为函数赋值

(this->*pfunc_)(args...);     //调用函数
```


# TLS
```
static boost::thread_specific_ptr<bool> tls;
tls.get()
```

# 容器迭代输出
```
std::copy(vec.begin(), vec.end(), std::ostream_iterator<int>(std::cout, " "));
std::cout<<std::endl;

// Join
std::string reselt = std::accumulate(strs.begin(), strs.end(), std::string(),
[](const std::string& a, const std::string& b) -> std::string {
    return a + (a.length() > 0 ? "," : "") + b;
});
```

# 删除
```
auto it = std::find(vec.begin(), vec.end(), 4);
it = vec.erase(it);

it = std::remove_if(vec.begin(), vec.end(), [](int a)->bool{return a%2;});
vec.resize(std::distance(vec.begin(), it);
```

# 原地构造
```
new(ptr) Class(args...);
```

# 右值引用
```
int && ref;   //在构造、拷贝时可以进行与左值区分，方便提升效率

std::declval<T>()     //返回 T 类型的右值引用，不区分其是否可被创建
```

# std的新类型
```
std::numeric_limits<int>::min()

std::initializer_list<T> //可用于初始化
a = {1, 1, 1};

std::thread t = std::thread([=](){....});
std::mutex m;
std::condition_variable cv;

std::this_thread::sleep_for(std::chrono::milliseconds(1));

std::chrono::steady_clock::time_point tp1 = std::chrono::steady_clock::now();
std::chrono::steady_clock::time_point tp2 = std::chrono::steady_clock::now();
//秒
double dr_s = std::chrono::duration<double>(tp2 - tp1).count();
//毫秒级
double dr_ms = std::chrono::duration<double, std::milli>(tp2 - tp1).count();
```

# 条件变量
条件变量常配合锁使用，锁的作用是在条件变量进入前对其进行互斥保护的
```
std::mutex mutex;
std::condition_variable cv;
// 条件变量与临界区有关，用来获取和释放一个锁，因此通常会和mutex联用。
std::unique_lock lock(mutex);
// 此处会释放lock，然后在cv上等待，直到其它线程通过cv.notify_xxx来唤醒当前线程，cv被唤醒后会再次对lock进行上锁，然后wait函数才会返回。
// wait返回后可以安全的使用mutex保护的临界区内的数据。此时mutex仍为上锁状态
cv.wait(lock)

std::unique_lock lock(mutex);
// 所有等待在cv变量上的线程都会被唤醒。但直到lock释放了mutex，被唤醒的线程才会从wait返回。
cv.notify_all() //lock
```


# 模板特化：
```
template <class T>
int compare(const T &left, const T&right) {
    std::cout <<"in template<class T>..." <<std::endl;
    return (left - right);
}

template < >
int compare<const char*>(const char* left, const char* right) {
    std::cout <<"in special template< >..." <<std::endl;
    return strcmp(left, right);
}
```


mutable     修饰允许在const函数中被修改的成员变量（前置）
override     这是用于标志重载的函数，而不是定义的虚函数，该函数必须重载，否则报错(后置)
final           用于禁止继承或重载，eg: class A final: public AA {...};


class A {
  A()=delete;     // 禁止构造
  ~A()=delete;   // 禁止析构
  A(const A&)=delete;     // 禁止拷贝
  A& operate=(const A&) = delete;     // 禁止拷贝

  operator int() {return 0;}    // 转为基本类型的运算符重载
};



# 类型推导：
```
decltype(exp) a = xxx;    // exp可以是一个表达式，a的类型与表达式相同
auto a = xxx;    // a 的类型与xxx 相同，可加 const 或 引用 进行类同转换为相应类型
```

# 闭包：
```
capture method: by value和by reference
[=](int a) -> int {
    return a;
}

[&](int a) -> int {
    return a;
}

std::function<void(int)> f =[](int a) {};
```



# 随机引擎
```
std::default_random_engine generator;
std::uniform_int_distribution<int> distribution(1,6);
int dice_roll = distribution(generator);
```

# std namespace STL
```
<numeric>
accumulate(iterator_begin, iterator_end, init_val);
adjacent_difference(iterator_begin, iterator_end, iterator_output);
inner_product(iterator_begin, iterator_end, iterator_begin_other);
partial_sum(iterator_begin, iterator_end, iterator_begin_output);
iota(iterator_output_begin, iterator_output_end, init_val);
```

# 常量修饰
```
const T& var; T const& var;  //是相同的效果，即引用的对象是常量，不可修改
T& const var;  // const 多余，表示引用本身不可修改，而引用只能在初始化时赋值，之后不能再指向其它对象。所以不写const效果相同。
const T* var; T const* var;  //是相同的效果，即指针指向的对象是常量，不可修改
T* const var; // 指针不可指向其它对象
```


# 智能指针
```
boost::shared_ptr<parent>

auto_ptr           # 控制权交接可能会发生异常
scope_ptr         # 控制权管理更严格的auto_ptr
shared_ptr
weak_ptr         #shared_ptr可赋值给weak_ptr, weak_ptr.lock()可赋值给shared_ptr
unique_ptr     # 禁止复制、赋值。可以std::move
```

要求：
```
unique_ptr要求类型完整，必须定义完全，不可以仅做声明
make_shared需要对应类型的构造为公用
```

成员引用变量
不能有默认构造函数，必须提供构造函数
构造函数的形参必须为引用类型
初始化必须在成员初始化链表内完成

```
str = std::to_string(num)

double stod(string, *idx)
float stof(string, *idx)
int stoi(string, *idx)
```

# Printf format
```
printf("%.*g", 15, 8.15);
```

# GCC __builtin_
`__builtin_ffs(x)` 返回x中最后一个为1的位是从后向前的第几位，奇数返回1。
`__builtin_popcount(x)` x中1的个数。
`__builtin_ctz(x)` x末尾0的个数。x=0时结果未定义。
`__builtin_clz(x)` x前导0的个数。x=0时结果未定义。(32bit)
`__builtin_parity(x)` x中1的奇偶性。
`__builtin_return_address(n)` 当前函数的第n级调用者的地址，有些体系结构只实现了n=0
`__builtin_bswap16 (uint16_t x)` 按字节翻转x，返回翻转后的结果。
`__builtin_bswap32 (uint32_t x)` 按字节翻转x，返回翻转后的结果。
`__builtin_constant_p (exp)` 判断exp是否在编译时就可以确定其为常量，常量返回1，否则返回0
`__builtin_types_compatible_p(type1, type2)` 判断type1和type2是否类型相同。该函数不区分const/volatile这样的修饰符
`__builtin_expect (long exp, long c)` 引导gcc进行条件分支预测。exp的值极可能为c
`__builtin_prefetch (const void *addr, int allow_write, int time_level)` 它通过对数据手工预取的方法，在使用地址addr的值之前就将其放到cache中，减少了读取延迟，从而提高了性能，但该函数也需要 CPU 的支持。该函数可接受三个参数，第一个参数addr是要预取的数据的地址，第二个参数可设置为0或1（1表示我对地址addr要进行写操作，0表示要进行读操作），第三个参数可取0-3（0表示不用关心时间局部性，取完addr的值之后便不用留在cache中，而1、2、3表示时间局部性逐渐增强）。


# 名字规则

nm 名字表   命名规则：Name mangling

`_Z` 开头，`N` 表套叠(nested)符号，  `K` 常量函数，`V`  虚表，
`I`  类型信息， `S` 类型信息名

`E` 为参数分隔，`Ev` 为无参函数，以`E`结尾表示为对象变量
类后`C`为构造，`D`为析构，后有编号
`I`为模板实现

`R` 引用






| 字符 |   类型              |
| ---- | ------------------- |
| `j`  | `unsigned int`      |
| `l`  | `long`              |
| `h`  | `unsigned char`     |
| `w`  | `wchar_t`           |
| `e`  | `long double`       |
| `t`  | `unsigned short`    |
| `y`  | `unsigned long long`|
| `o`  | `unsigned __int128 `|
| `a`  | `signed char`       |
| `s`  | `short`             |
| `d`  | `double`            |
| `f`  | `float`             |
| `g`  | `__float128`        |
| `h`  | `unsigned char`     |
| `z`  | `...`               |
| `x`  | `long long`         |
| `c`  | `char`              |
| `v`  | `void`              |
| `b`  | `bool`              |
| `n`  | `__int128`          |
| `m`  | `unsigned long`     |

## Demangling

```bash
c++filt  _ZNK3MapI10StringName3RefI8GDScriptE10ComparatorIS0_E16DefaultAllocatorE3hasERKS0_      # bash
```

```c++
char *demangled_name = abi::__cxa_demangle(mangled_name, NULL, NULL, &status);        //abi
```
