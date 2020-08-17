## C Struct

* struct{fields\(vars\)}: access by . 
* -&gt; operator = \(\*\). \(dereference and get\)
* typedef&lt;old name&gt; &lt;new name&gt;: create a re-written name
  * typedef struct {} var\_t : declare a variable
* a bunch of variables together, but not OOP

---

# Class

#### Basic Components

* Member Functions\(Methods\)
* Data Memeber\(Attributes\)
* Scope\(Encapsulation\)
  * Public: data can be accessed by other classes \(usually member functions\)
  * Private: data cannot be accessed outside the class \(usually data members\)
  * **Protected**: public to all derived classes and friends but private to outside code
  * try not to use 
    * functions fine, data fine in **abstract class**
* Friend

#### Key Members

* Constructor

  * Initialization list
    * usually pass in base class constructor 
  * multiple constructors

    * **default constructor **- no arguments
      * put into "private" to prevent default construction
    * **copy constructor** \(pass in a const reference\)
      * called every type the object is passed by value
      * ```cpp
        ClassName( const ClassName &other)
        ClassName( ClassName& other)
        ClassName( volatile const ClassName &other)
        ClassName( volatile ClassName& other)
        ```
    * **move constructor **\(C++ 11\)

      * [**right value**](https://eli.thegreenplace.net/2011/12/15/understanding-lvalues-and-rvalues-in-c-and-c/)** \(temp values\)**

        * rvalue reference and lvalue reference
        * ```cpp
          void process_value(int& i) { 
           std::cout << "LValue processed: " << i << std::endl; 
          } 

          void process_value(int&& i) { 
           std::cout << "RValue processed: " << i << std::endl; 
          } 

          void forward_value(int&& i) { 
           process_value(i); 
          } 

          int main() { 
           int a = 0; 
           process_value(a); 
           process_value(1); 
           forward_value(2); 
          } 

          /*
          LValue processed: 0 
          RValue processed: 1 
          LValue processed: 2
          */
          ```
        * std::move
          * use left value as right value to improve performance

      * **move **semantics

        * move rather then copy, no object creation cost
        * ```cpp
          MyString(MyString&& str) { 
             std::cout << "Move Constructor is called! source: " << str._data << std::endl; 
             _len = str._len; 
             _data = str._data; 
             str._len = 0; 
             str._data = NULL; 
          }
          ```

      * perfect forwarding
        * forward all types \(const, lvalue, rvalue\) perfectly when forward parameters

* operator overloading \(=\)

  * &lt;return type&gt; operator symbol \(&lt;parameter\_list&gt;\)
  * **move =** \(C++ 11\)
    * ```cpp
      MyString& operator=(MyString&& str) { 
         std::cout << "Move Assignment is called! source: " << str._data << std::endl; 
         if (this != &str) { 
           _len = str._len; 
           _data = str._data; 
           str._len = 0; 
           str._data = NULL; 
         } 
         return *this; 
      }
      ```

* Destructor\(~\)
  * **only one**
* **This** pointer - points to the current object

#### Examples

```
class DemoClass final 
{
public:
    DemoClass(const DemoClass&) = delete;              // 禁止拷贝构造
    DemoClass& operator=(const DemoClass&) = delete;  // 禁止拷贝赋值
};
```

```
class DemoClass final 
{
public:
    explicit DemoClass(const string_type& str)  // 显式单参构造函数
    { ... }

    explicit operator bool()                  // 显式转型为bool
    { ... }
};
```

#### C++ 11 Features

Delegating

```cpp
class DemoDelegating final
{
private:
    int a;                              // 成员变量
public:
    DemoDelegating(int x) : a(x)        // 基本的构造函数
    {}  

    DemoDelegating() :                 // 无参数的构造函数
        DemoDelegating(0)               // 给出默认值，委托给第一个构造函数
    {}  

    DemoDelegating(const string& s) : // 字符串参数构造函数
        DemoDelegating(stoi(s))        // 转换成整数，再委托给第一个构造函数
    {}  
};
```

In class member initializer -

```cpp
class DemoInit final                  // 有很多成员变量的类
{
private:
    int                 a = 0;        // 整数成员，赋值初始化
    string              s = "hello";  // 字符串成员，赋值初始化
    vector<int>         v{1, 2, 3};   // 容器成员，使用花括号的初始化列表
public:
    DemoInit() = default;             // 默认构造函数
   ~DemoInit() = default;             // 默认析构函数
public:
    DemoInit(int x) : a(x) {}         // 可以单独初始化成员，其他用默认值
};
```

type alias

```cpp
class DemoClass final
{
public:
    using this_type         = DemoClass;          // 给自己也起个别名
    using kafka_conf_type   = KafkaConfig;        // 外部类起别名

public:
    using string_type   = std::string;            // 字符串类型别名
    using uint32_type   = uint32_t;              // 整数类型别名

    using set_type      = std::set<int>;          // 集合类型别名
    using vector_type   = std::vector<std::string>;// 容器类型别名

private:
    string_type     m_name  = "tom";              // 使用类型别名声明变量
    uint32_type     m_age   = 23;                  // 使用类型别名声明变量
    set_type        m_books;                      // 使用类型别名声明变量

private:
    kafka_conf_type m_conf;                       // 使用类型别名声明变量
};
```

Explicit default \(C++11\)

* = default
* = delete: explicitly forbid

#### Inheritance

* Inheritance and Derived Class \( Class A: Public &lt;Class B&gt;\)
  * Pointer to base class can be assigned to derived class address
  * **Virtual Function **:_ virtual_ keyword
    * check function definition at run/time \(**polymorphism**\) 
      * every class with a virtual function has a _vtbl \(vee-table\)_, a table of pointers to class-specific functions, an ultra-private member is added at the beginning of each class to look up in the table
      * can force call one of the functions by using scope \(Base::Func\(\)\)
  * "Private Inheritance": _Class A:&lt;Class B&gt;_ - all B's member will be A's private Member, **not a real inheritance \(**A is not a kind of B\)
  * override \(C++11\) explicitly indicative the function overrides it
* Abstract Class
  * at lease one **pure virtual function:** virtual &lt;type&gt; func\(\) = 0;
  * almost always require a** virtual destructor \(make sure derived class destructor is called when delete is done in a base class pointer\)**
  * implemented by **vtbl** table

## Using Objects

### const

prevent data to be altered in anyway

* const &lt;type&gt; variable - make a read-only copy/variable 
  * cannot be changed after initialization
* const T &a - reference to a const 
  * cannot be changed
  * can only call const members
* const T\*p{&a} - **pointer to a read-only variable**
  * or T const \*p{&a}
  * can only call const members
* T \*const p - **constant pointer**
  * cannot change the variable by **de-referencing**
  * variable self is changable
* const &lt;type&gt; func\(\) {}
  * the function returns a const
* &lt;type&gt; memfunc\(\) const {} 
  * **const member function**, the function cannot change the object\(read-only\)
  * cannot change object via \*this pointer
* const &lt;type&gt; datamem: 
  * **constant data member,** the data member is fixed after initialization

const\_cast : typecast to const

many functions have two versions \(eg. front\(\), at\(\) in vector\), compiler will call const ones on const objects

### mutable

* Modifiable member in const objects
* unlock const

```cpp
class DemoClass final
{
private:
    mutable mutex_type  m_mutex;    // mutable成员变量
public:
    void save_data() const          // const成员函数
    {
        // do someting with m_mutex
    }
};
```

### static

* **Static Variable**
  * Give instruction to store the data in static area \(initialized once\)
  * cause variale to be hidden within a local code file\(file local\)
  * cause top-level function to be hidden in a file
* **Static Member**
  * cause data members and member functions to belong to the class as a whole
  * there is no const static member function - because no \*this pointer for static member function

### explicit

explicit Classname\(&lt;parameters&gt;\) - explicit constructor prevent complier to do type conversion for the class

### volatile

* A volatile specifier is a hint to a compiler that an object may change its value in ways not specified by the language so that **aggressive optimizations** must be avoided.
* Get value every time

### C++ 11

* constexpr 
  * real compiling level const

## Template

define a family of functions/struct/classes \(instancies\)

template&lt;Typename T&gt;

&lt;return\__type&gt; function\_name\(&lt;parameter\_list&gt;\)_

Template&lt;Class T&gt;

&lt;return\__type&gt; function\_name\(&lt;parameter\_list&gt;\)_

