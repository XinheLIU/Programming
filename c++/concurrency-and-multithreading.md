# Parallel Programming C++

## Multi-threading 

### Thread

* C++, each function is a a thread
* main thread is main\(\)

### Multi-threading Programming basics

* Basic pricinple: use const(read, not write)

#### Call Once

* initialize only once
* once\_flag
* call\_once
* only call once
  
  ```cpp
    static std::once_flag flag;        // 全局的初始化标志

    auto f = []()                // 在线程里运行的lambda表达式
    {   
        std::call_once(flag,      // 仅一次调用，注意要传flag
            [](){                // 匿名lambda，初始化函数，只会执行一次
                cout << "only once" << endl;
            }                  // 匿名lambda结束
        );                     // 在线程里运行的lambda表达式结束
    };

    thread t1(f);            // 启动两个线程，运行函数f
    thread t2(f);
    ```

Thread Local Storage

* thread\_local variable

   ```cpp

    thread_local int n = 0;        // 线程局部存储变量

    auto f = [&](int x)           // 在线程里运行的lambda表达式，捕获引用
    {
        n += x;                   // 使用线程局部变量，互不影响
        cout << n;                // 输出，验证结果
    };  

    thread t1(f, 10);           // 启动两个线程，运行函数f
    thread t2(f, 20);
    ```

#### Atomic variables and operations

* works only on basic types
* forbid copy constructor \(use {}\)
* supports atomic operatios
  * store
  * load
  * fetch\_add
  * fetch\_sub
  * compare\__exchange\__weak/compare_\_exchange\_strong_

```cpp

using atomic_bool = std::atomic<bool>;    // 原子化的bool
using atomic_int  = std::atomic<int>;      // 原子化的int
using atomic_long = std::atomic<long>;    // 原子化的long

atomic_int  x {0};          // 初始化，不能用=
atomic_long y {1000L};      // 初始化，只能用圆括号或者花括号

assert(++x == 1);           // 自增运算

y += 200;                   // 加法运算
assert(y < 2000);           // 比较运算 
```

### Standard tools

Boost.lock\_free

Multi-threading

* standard libaray
  * mutex
  * lock\_guard
  * condition\_variable
  * premise
* [Thread](http://www.cplusplus.com/reference/thread/thread/)
  * std::this\_thread
  * yield\(\)
  * get\_id\(\)
  * sleep\_for\(\)
  * sleep\_until\(\)

 ```cpp

  static atomic_flag flag {false};    // 原子化的标志量
  static atomic_int  n;               // 原子化的int

  auto f = [&]()              // 在线程里运行的lambda表达式，捕获引用
  {
      auto value = flag.test_and_set();  // TAS检查原子标志量

      if (value) {
          cout << "flag has been set." << endl;
      } else {
          cout << "set flag by " <<
              this_thread::get_id() << endl;  // 输出线程id
      }

      n += 100;                    // 原子变量加法运算

      this_thread::sleep_for(      // 线程睡眠
          n.load() * 10ms);        // 使用时间字面量
      cout << n << endl;
  };                        // 在线程里运行的lambda表达式结束

  thread t1(f);                // 启动两个线程，运行函数f
  thread t2(f);

  t1.join();                   // 等待线程结束
  t2.join();
  ```

#### Async

* async\(\)
* return the type \(future\)
  * can only be get once
  * must assign \(otherwise will block\)

```cpp

auto task = [](auto x)                  // 在线程里运行的lambda表达式
{
    this_thread::sleep_for( x * 1ms);  // 线程睡眠
    cout << "sleep for " << x << endl;
    return x;
};

auto f = std::async(task, 10);         // 启动一个异步任务
f.wait();                              // 等待任务完成

assert(f.valid());                    // 确实已经完成了任务
cout << f.get() << endl;              // 获取任务的执行结果
```
