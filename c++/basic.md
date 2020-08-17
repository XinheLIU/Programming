# C++ Basics

- [C++ Basics](#c-basics)
  - [Basic Grammars](#basic-grammars)
  - [Function](#function)
    - [**Functions**](#functions)
    - [Function Pointers](#function-pointers)
    - [Lambda](#lambda)
  - [Input/Output](#inputoutput)
    - [Common Input output Functions](#common-input-output-functions)
      - [C-style input output](#c-style-input-output)
      - [C++ standard input output stream](#c-standard-input-output-stream)
        - [I/O manipulators](#io-manipulators)
  - [File](#file)
  - [Syntactic Sugar](#syntactic-sugar)
  - [C ++ Memory Model](#c--memory-model)
    - [Variable Lifetime and Variable Scope](#variable-lifetime-and-variable-scope)
    - [Memory Management in C++](#memory-management-in-c)
  - [C++ 11 Smart Pointers](#c-11-smart-pointers)
  - [Inline](#inline)
  - [Running C++](#running-c)
    - [Preprocessor Directives](#preprocessor-directives)
      - [namespace](#namespace)
    - [C++ Compliers](#c-compliers)
      - [GNU G++](#gnu-g)
      - [attribute](#attribute)
      - [static\_assert](#static_assert)
      - [noexcept](#noexcept)
  - [Coding Style](#coding-style)
  - [Debugging](#debugging)
    - [Tips](#tips)
    - [Exceptions](#exceptions)

## Basic Grammars

Initialization \(strong type\)

```cpp
int i1;
int i2 = 2;
int i3(4) // C style
int i4{4} // C++ style
```

Control Structures

* if then else if else
* swith case break default
* for \(\) {}  
  * break
  * continue
* range for loop - for \( \*iter: container\) {}
* while\(\){}
* do{} while\(\)

Operators

* Arithmetic
* boolean
* **Pointer **Operation
  * & - address of, \* get the content of \(address\)
* Precedence
  * \*s++, ++ has higher precedence, but evaluated later

Main\(\) Function

* int main\(int argc, char\* argv\[\]\)
* argc - command line variables count
* argv - user input

## Function

### **Functions**

* **declaration**
  * &lt;return type&gt; &lt;function name&gt; \(&lt;type and number of parameters- no need for names&gt;\)
  * **multiple declarations** is okay, but one definition
* **Function overload **- same name, different parameter types is treated differently
* call-by-value and call-by-reference
  * call-by-value: create new variables in new addresses \(copy of the pass-ins\)
    * pass in pointers to change the variable outside 
  
      ```cpp
      void swap(int *p1, int *p2)
      {
          int temp(*p1);
          *p1 = *p2; *p2 = temp;
      }

      int main()
      {
          int i3(3), i5(5); // c++ 09 syle
          swap(&i3,i5)
      }
      ```

  * call-by-reference \( see data types\)
    * &a = b : alias of b
* all functions are global\(equal level\)
  * function cannot be defined inside functions
* function is operated by function pointers
  * function is not a type, function pointer is

### Function Pointers

point to the memory location of a function

```cpp
void my_square(int x)           // 定义一个函数
{
    cout << x*x << endl;       // 函数的具体内容
}

auto pfunc = &my_square;       // 只能用指针去操作函数，指针不是函数
(*pfunc)(3);                    // 可以用*访问函数
pfunc(3);                       // 也可以直接调用函数指针
```

### Lambda

Since C++ 11

* \[\] - **lambda introducer**
* it has life cycle and local scope \(inside other functions\)
  * can be nested
* can get external variables \(= to get by value, & to get by reference\) \(upvalue\)
  * use shared\_ptr to subscribe for longer term
* work like a **closure**
* **std::function** can store functions and lambda and be called
* type hint -&gt; can be used

```cpp
int x = 33;               // 一个外部变量

auto f1 = [=]()           // lambda表达式，用“=”按值捕获
{
    //x += 10;            // x只读，不允许修改
};

auto f2 = [&]()         // lambda表达式，用“&”按引用捕获
{
    x += 10;            // x是引用，可以修改
};

auto f3 = [=, &x]()       // lambda表达式，用“&”按引用捕获x，其他的按值捕获
{
    x += 20;              // x是引用，可以修改
};


class DemoLambda final
{
private:
    int x = 0;
public:
    auto print()  -> void            // 返回一个lambda表达式供外部使用, type hint
    {
        return [this]()      // 显式捕获this指针
        {
            cout << "member = " << x << endl;
        };
    }
};
```

* can effectively support functional programming

```cpp
auto a = [](int x)      // a函数执行一个功能
            {...} 
auto b = [](double x)    // b函数执行一个功能
            {...}
auto c = [](string str)  // c函数执行一个功能
            {...}

auto f = [](...)        // f函数执行一个功能
            {...}

return f(a, b, c)            // f调用a/b/c运算得到结果

// defined inside a function
auto f2 = []()                 // 定义一个lambda表达式
{
    cout << "lambda f2" << endl;

    auto f3 = [](int x)         // 嵌套定义lambda表达式
    {
        return x*x;
    };// lambda f3              // 使用注释显式说明表达式结束

    cout << f3(10) << endl;
};  // lambda f2               // 使用注释显式说明表达式结束
```

unnamed lambda

```cpp
vector<int> v = {3, 1, 8, 5, 0};     // 标准容器

cout << *find_if(begin(v), end(v),   // 标准库里的查找算法
            [](int x)                // 匿名lambda表达式，不需要auto赋值
            {
                return x >= 5;        // 用做算法的谓词判断条件 
            }                        // lambda表达式结束
        )
     << endl;                        // 语句执行完，lambda表达式就不存在了
```

---

## Input/Output

### Common Input output Functions

* stdin, stdout - output to terminal window
* stderr - error message to terminal 
* input/output stream
* input/output buffer 

#### C-style input output

* printf\(\)
  * %c,%s - char and string
  * d,i - integer
  * u, o- unsigned integer
  * f,e,a,g - double
  * p - pointer
  * frpintf\(\): to a file sprintf\(\): to a string 
* scanf\(\)

#### C++ standard input output stream

\# include &lt;iostream&gt;

* ostream
  * cout
  * ofstream -
* istream
  * cin
* ifstream
  * getline\(fin, line\)
* sstream - string stream

##### I/O manipulators

\# include&lt;iomanip&gt;

* boolalpha - use true false over 1 0
* setw\(n\) - next output field width
* fixed - fixed point, no exponent
* setprecision\(n\) 

---

## File

* file pointer \*FILE
* \*fopen\(&lt;file name&gt;, &lt;operation&gt;\)
  * r- read, w-write, a-append
* fclose\(&lt;ptr&gt;\),fgetc\(&lt;read ptr&gt;\),fputc\(char, &lt;write ptr&gt;\)
* size\_t fread\(&lt;buffer&gt;, &lt;size&gt;, &lt;qty&gt;, &lt;read ptr&gt;\): returns how many units we have successfully read,fwrite\(\)
* fprintf\(\) \(string\)
* fseek\(\), ftell\(\)
* feof\(\)
* ferror\(\) 

---

## Syntactic Sugar

* ++, +=, --
  * object ++ : add one after it is been used \(post-increment\) \(eg. display string \*s ++ : ++ has higher precedence but evaluated later\)
  * ++ object: add one before \(pre-increment\)
* array name is a pointer variable ; a\[n\] is a pointer variable

---

## C ++ Memory Model

* memory divided into 4 areas
  1. Code - executable code, fixed size
  2. **Static data** - fixed size data not move
     1. constants \( const var, string literals\)
     2. cout, cin
     3. global static data \(**"static" **key word - suggest to store variable in static data - it will be only initilized once**\)**
        1. variables storage class could be** static **or** automatic**
  3. **Stack** - local automatic/temporary variables \(dynamic, change size\)
     1. a **stack frame**/**activation record** is automatically created when main\(\) is called
     2. call stack frame / function frame are created when a function is called, the top frame is the active one, it stores:
        1. parameter variables
        2. local auto/temp variables
        3. return value
        4. miscellaneous bookkeeping details
  4. **Heap** - dynamically allocated area\(dynamic, change size\)
* C-Style memory allocaiton
  * malloc\(size\_t n\): allocate n bytes of memory
  * calloc\(size\_t num, size\_t size\): allocate and set to zero
  * realloc\(\): reallocate memory
  * free\(var\): free the variable
* when program is running
  1. code is loaded 
  2. static variables, in and output streams, top-level\(global\) static data loaded 
  3. main\(\) is called 
  4. everything gone after main returns

### Variable Lifetime and Variable Scope

* static and global variable are created at the begin of the program or at the initialization point
* use **global** to declare a global variable, use **extern **to declare again in another file
* local auto variables is created when the outside function is called and deleted when the function is returned
* **scope** is the part where a variable is visible or accessible by name
* local variables **scope** is from declaration to the end of its block, parameter variables' scope is the body of the function
  * except within nested block where **reusing its name will cover the outside variable scope**


### Memory Management in C++

Memory allocate on heap

* new 
  * T \*p = new T{initialization};
  * T \*p = new T\[n\] {initialization}
* delete
  * delete p;
  * delete \[\] p;

RAII memory model \(Resource Acquisition is Initialization\)

---

## C++ 11 Smart Pointers

mimic the pointer with extra features to simplify the usage and resource management

* shared\_ptr
* unique\_ptr
* weak\_ptr

```cpp
unique_ptr<int> ptr1(new int(10));      // int智能指针
assert(*ptr1 == 10);                     // 可以使用*取内容
assert(ptr1 != nullptr);                // 可以判断是否为空指针

unique_ptr<string> ptr2(new string("hello"));  // string智能指针
assert(*ptr2 == "hello");                // 可以使用*取内容
assert(ptr2->size() == 5);               // 可以使用->调用成员函数


ptr1++;                        // 导致编译错误
ptr2 += 2;                     // 导致编译错误


unique_ptr<int> ptr3;                // 未初始化智能指针
*ptr3 = 42 ;                         // 错误！操作了空指针



auto ptr3 = make_unique<int>(42);               // 工厂函数创建智能指针
assert(ptr3 && *ptr3 == 42);

auto ptr4 = make_unique<string>("god of war");  // 工厂函数创建智能指针
assert(!ptr4->empty());


auto ptr1 = make_unique<int>(42);    // 工厂函数创建智能指针
assert(ptr1 && *ptr1 == 42);         // 此时智能指针有效

auto ptr2 = std::move(ptr1);         // 使用move()转移所有权
assert(!ptr1 && ptr2);               // ptr1变成了空指针
```

shared\_ptr

* has reference count
* downside: has uncertainty when it destruct pointers
  * cause blockage
* cyclic reference

```cpp
auto ptr1 = make_shared<int>(42);    // 工厂函数创建智能指针
assert(ptr1 && ptr1.unique() );     // 此时智能指针有效且唯一

auto ptr2 = ptr1;                  // 直接拷贝赋值，不需要使用move()
assert(ptr1 && ptr2);              // 此时两个智能指针均有效

assert(ptr1 == ptr2);             // shared_ptr可以直接比较

// 两个智能指针均不唯一，且引用计数为2
assert(!ptr1.unique() && ptr1.use_count() == 2); 
assert(!ptr2.unique() && ptr2.use_count() == 2);
```

weak\_ptr

* does not increase reference count
  * has the correct reference count in case of circular reference

```cpp
class Node final
{
public:
    using this_type     = Node;

    // 注意这里，别名改用weak_ptr
    using shared_type   = std::weak_ptr<this_type>;
public:
    shared_type     next;    // 因为用了别名，所以代码不需要改动
};

auto n1 = make_shared<Node>();  // 工厂函数创建智能指针
auto n2 = make_shared<Node>();  // 工厂函数创建智能指针

n1->next = n2;             // 两个节点互指，形成了循环引用
n2->next = n1;

assert(n1.use_count() == 1);    // 因为使用了weak_ptr，引用计数为1
assert(n2.use_count() == 1);   // 打破循环引用，不会导致内存泄漏

if (!n1->next.expired()) {     // 检查指针是否有效
    auto ptr = n1->next.lock();  // lock()获取shared_ptr
    assert(ptr == n2);
}
```

## Inline

C++ provides an inline functions to reduce the function call overhead. Inline function is a function that is expanded in line when it is called. When the inline function is called whole code of the inline function gets inserted or substituted at the point of inline function call.

* Static member function and recursive functions cannot be fully inline
* function fully defined in class definition are implicitly inline

---

## Running C++

### Preprocessor Directives

commands sent to the preprocessor

* \#-blank line
* \# include - to include a library, file or header
* \# define - define a **manifest const \(macro\)**
  * symbolic variable - normal variable
  * symbolic constant - defined by const
  * macro functions
* \#undef - cancel the \#define
* \#if \#elif \#else 
  * \# ifdef/ifndef \#endif - do** macro guards**
    * alternative **\#pragma once**

predefined macros

```cpp
#ifdef __cplusplus                      // 定义了这个宏就是在用C++编译
    extern "C" {                        // 函数按照C的方式去处理
#endif
    void a_c_function(int a);
#ifdef __cplusplus                      // 检查是否是C++编译
    }                                   // extern "C" 结束
#endif

#if __cplusplus >= 201402                // 检查C++标准的版本号
    cout << "c++14 or later" << endl;    // 201402就是C++14
#elif __cplusplus >= 201103              // 检查C++标准的版本号
    cout << "c++11 or before" << endl;   // 201103是C++11
#else   // __cplusplus < 201103          // 199711是C++98
#   error "c++ is too old"               // 太低则预处理报错
#endif  // __cplusplus >= 201402         // 预处理语句结束

// by interpretors

g++ -E -dM - < /dev/null

#define __GNUC__ 5
#define __unix__ 1
#define __x86_64__ 1
#define __UINT64_MAX__ 0xffffffffffffffffUL
...
```

safely disable codes

```cpp
#if 0          // 0即禁用下面的代码，1则是启用
  ...          // 任意的代码
#endif         // 预处理结束

#if 1          // 1启用代码，用来强调下面代码的必要性
  ...          // 任意的代码
#endif         // 预处理结束
```

C++ 17 introduces \_\__has\_include _

C++ 20 has "module"

Boost has boost.preprocessor

#### namespace

* std is the name space by C++ standard lib 
  * usually standard to use

### C++ Compliers

#### GNU G++

* g++ &lt;source&gt;: compile and run source file
  * -o &lt;output&gt;

#### attribute

[attribute](https://en.cppreference.com/w/cpp/language/attributes)

* noreturn
* carries\_dependency

C++ 14

* \[\[deprecated\(\)\]\]

C++ 17/20

* unused
* constructor
* destructor
* always inline
* hot
* fallthroughly
* likely

#### static\_assert

[static\_assert](https://en.cppreference.com/w/cpp/language/static_assert)

```cpp
static_assert(
  sizeof(long) >= 8, "must run on x64");

static_assert(
  sizeof(int)  == 4, "int must be 32bit");

  # find empty pointer


char* p = nullptr;
static_assert(p == nullptr, "some error.");  // 错误用法


// 假设T是一个模板参数，即template<typename T>

static_assert(
  is_integral<T>::value, "int");

static_assert(
  is_pointer<T>::value, "ptr");

static_assert(
  is_default_constructible<T>::value, "constructible");
```

#### noexcept

promise no exception throw \(compiler not able to catch, cause crash/core dump if throwing\)

```cpp
void func_maybe_noexcept() noexcept          // 声明绝不会抛出异常
{
    throw "Oh My God";                    // 但也可以抛出异常
}
```

---

## Coding Style

* No **go to**
* more reference less pointer
* avoid global varible
* using const
* comment
  
---

## Debugging

* Compiling error
* Link error
* Runtime error
* Logic Error

### Tips

* Catch and warning
* check recent changes
* review call stack and variable values \(dependencies\)
* hard bugs:
  * make the bug repeatable
  * divide the code into pieces
  * add print or throw
  * add self checking and assertion
  * study statistical value of bugs
  * check maro-defined functions
* Unrepeatable bugs
  * check log
  * check variable initailzations
  * check memory allocation and overflow
  * check if the pointers to NULL before deletion
* Last resort
  * single step tracking
  * explain to a rubber duck
  * check environment
  * MSDN, google, stackoverflow

### Exceptions

[std::exception](https://en.cppreference.com/w/cpp/error/exception)

* bad\_alloc
* runtime\_error
  * range\_error
  * overflow\_error
* logic\_error
  * invalid\_argument
  * length\_error
* bad\_cast

Try .. catch

* no "finally" to make sure code will always run

```cpp
class my_exception : public std::runtime_error
{
public:
    using this_type     = my_exception;        // 给自己起个别名
    using super_type    = std::runtime_error;  // 给父类也起个别名
public:
    my_exception(const char* msg):            // 构造函数
        super_type(msg)                      // 别名也可以用于构造
    {}  

    my_exception() = default;                // 默认构造函数
   ~my_exception() = default;                // 默认析构函数
private:
    int code = 0;                            // 其他的内部私有数据
};


[[noreturn]]                      // 属性标签
void raise(const char* msg)      // 函数封装throw，没有返回值
{
    throw my_exception(msg);     // 抛出异常，也可以有更多的逻辑
}


try
{
    raise("error occured");     // 函数封装throw，抛出异常
}
catch(const exception& e)      // const &捕获异常，可以用基类
{
    cout << e.what() << endl;  // what()是exception的虚函数
}

// function try
void some_function()
try                          // 函数名之后直接写try块
{
    ...
}
catch(...)                   // catch块与函数体同级并列
{
    ...
}
```

To use exceptions

* one end of the spectrum is never use it like C \(rely on error code\)
* the other end is to use for all
* in between is good
  * stack unwind has cost

noexpect\(C++11\)

* crash or core dump directly in cases of failing
* noexcept\(condition\)
* beneficial to add on all constructors
* need to add on desctructors