# Built-in Types

### Atomic Types

* void
* int\(4bytes\), short, long, long long, unsigned\(4\), unsigned long
* bool\(?bytes\)
  * cast: False is 0 or NULL, other True
* floating
  * single\(4\), double\(8\)
* char\(1\)
  * **array of char** is "**C style strings**" - String literals \(constants\) are stored in this form
    * C-style string is \*char type, put when output, output value \(cast to void\* to see address\)
    * strcpy\(cstr, &lt;literal&gt;\)
* **pointer** - &lt;Type&gt;\* p : stores address, content be extracted by \* operator
  * right-to-left rule
* array &lt;Type&gt; array name\[N\]
  * can be nested \(inside-out rule\)
  * stored in ascending contiguous memory location
    * a == &a\[0\]
    * int \*p\(a\); // p == a == &a\[0\]
    * a\[N\] = \*\(a+N\)
  * name stores the** address **of the first element
    * no boundary check
  * pass an array as function argument, the parameter is actually a **pointer**
    * ```cpp
      int a[4] // a == &a[0]
      int *p(a) // p == a == &a[0]
      a[N] == *(a+N)
          == *(p+N)
          == p[N]
      // the same
      void foo(int a[4], int sz)
      void foo(int a[], int sz)
      void foo(int *a, int sz)
      // pointer an array
      int (*p1)[2] // pointer-to-array-of-2-int
      int *p2[2] // array-of-2-pointer-to-int
      ```

**reference\(&\)**

* reference is an alias that cannot be re-assigned
  * cannot be re-assigned
  * cannot assigned to NULL
  * address cannot be taken
  * no arithmetic 

**function pointer**

&lt;return type&gt; \(\*p\_func\) \(&lt;parameter list&gt;\) - point to address of functions

### Built-in Functions

* Sizeof\(\) - memory size

### Automatic Type Reference

[auto ](https://en.cppreference.com/w/cpp/language/auto)in C++

* must do with initilization
* not in class initialization \(no auto class data member\)
* always gives value, no reference type
* can do with \*, &, const, volatile, 

[decltype](https://en.cppreference.com/w/cpp/language/decltype)

```cpp
int x = 0;          // 整型变量

decltype(x)     x1;      // 推导为int，x1是int
decltype(x)&    x2 = x;    // 推导为int，x2是int&，引用必须赋值
decltype(x)*    x3;      // 推导为int，x3是int*
decltype(&x)    x4;      // 推导为int*，x4是int*
decltype(&x)*   x5;      // 推导为int*，x5是int**
decltype(x2)    x6 = x2;  // 推导为int&，x6是int&，引用必须赋值


// C ++ 14


using int_ptr = decltype(&x);    // int *
using int_ref = decltype(x)&;    // int &
```

Use with [using](https://en.cppreference.com/w/cpp/language/type_alias) and [typedef](https://en.cppreference.com/w/cpp/language/typedef)

```cpp
// UNIX信号函数的原型，看着就让人晕，你能手写出函数指针吗？
void (*signal(int signo, void (*func)(int)))(int)

// 使用decltype可以轻松得到函数指针类型
using sig_func_ptr_t = decltype(&signal) ;
```

Class cannot use "auto" can use "decltype"

```cpp
class DemoClass final
{
public:
    using set_type      = std::set<int>;  // 集合类型别名
private:
    set_type      m_set;                   // 使用别名定义成员变量

    // 使用decltype计算表达式的类型，定义别名
    using iter_type = decltype(m_set.begin());

    iter_type     m_pos;                   // 类型别名定义成员变量
};
```

## Type Casts

* C-Style type casts
  * \(&lt;type\_declaration&gt;expression\)
  * depend on complier, very unsafe
* C++ function-like type conversion
  * double\(2\), bool\(3.14\)
  * still not safe, but at least expressed in a function
* **Named typed conversions**
  * const\_cast&lt;T&gt;: alters constness of an expr
  * static\_cast&lt;T&gt; : conversion among pointer types
  * reinterpret\_cast&lt;T&gt;:conversion of non-pointers to pointers
  * dynamic\_cast&lt;T&gt;: handles conversion of base class pointer to derived class pinters
