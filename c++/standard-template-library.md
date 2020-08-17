# [Standard Template Library](https://en.wikipedia.org/wiki/Standard_Template_Library)

## [Containers](http://www.cplusplus.com/reference/stl/)

* Container saves value\(copy\) of objects, not references, to optimize this
  * use move semantics to optimize
  * [emplace](https://en.cppreference.com/w/cpp/container/vector/emplace_back) operators
  * if needs to use pointer, use smart pointers to avoid memory problem \(pointers won't be collected when containers are destructed\)

    ```cpp
    Point p;                        // 一个拷贝成本很高的对象

    v.push_back(p);                // 存储对象，拷贝构造，成本很高
    v.push_back(std::move(p));    // 定义转移构造后就可以转移存储，降低成本
    v.emplace_back(...);            // 直接在容器里构造元素，不需要拷贝或者转移
    ```

### Sequence Types

* array
  * immutable
* vector
  * dynamic memory allocation: x2 of current size \(aggressive\)
* deque
  * emplace\_\_front, emplace\_\_back
  * dynamic allocation by N steps
* list
  * double linked list
  * dynamic allocation by N steps
* forward\_list
  * singly linked list

### Ordered Types

* Usually re-black trees
* need to overload &lt; or define compare functions

```cpp
bool operator<(const Point& a, const Point& b)
{
    return a.x < b.x;            // 自定义比较运算
}

set<Point> s;                    // 现在就可以正确地放入有序容器
s.emplace(7);
s.emplace(3);

set<int> s = {7, 3, 9};           // 定义集合并初始化3个元素

for(auto& x : s) {                // 范围循环输出元素
    cout << x << ",";              // 从小到大排序，3,7,9
}

auto comp = [](auto a, auto b)  // lambda
{
    return a > b;                // 定义大于关系
};  

set<int, decltype(comp)> gs(comp)  // 使用decltype得到lambda的类型

std::copy(begin(s), end(s),          // 拷贝算法，拷贝数据
          inserter(gs, gs.end()));  // 使用插入迭代器

for(auto& x : gs) {                // 范围循环输出元素
    cout << x << ",";                // 从大到小排序，9,7,3
}
```

### Unordered Types

Hash maps usually

* Key must be hashable
* == is defined or overloaded

```cpp
auto hasher = [](const auto& p)    // 定义一个lambda表达式
{
    return std::hash<int>()(p.x);  // 调用标准hash函数对象计算
};

unordered_set<Point, decltype(hasher)> s(10, hasher);

s.emplace(7);
s.emplace(3);
```

### Container Adapters

different interfaces on top of containers

* stack
* queue
* priority\_queue

## Iterator

[iterators](http://www.cplusplus.com/reference/iterator/) in C++

* distance\(\)
* advance\(\)
* next\(\)/prev\(\)

## Algorithms

[Algorithms in C++](https://en.cppreference.com/w/cpp/algorithm)

Common examples

* for\_each
  
   ```cpp

    vector<int> v = {3,5,1,7,10};   // vector容器

    for(const auto& x : v) {        // range for循环
        cout << x << ",";
    }

    auto print = [](const auto& x)  // 定义一个lambda表达式
    {
        cout << x << ",";
    };
    for_each(cbegin(v), cend(v), print);// for_each算法

    for_each(                      // for_each算法，内部定义lambda表达式
        cbegin(v), cend(v),        // 获取常量迭代器
        [](const auto& x)          // 匿名lambda表达式
        {
            cout << x << ",";
        }
    );
    ```

* Sorting - work on containers with random access
  * stable\_sort
  * partial\_sort \(TopN\)
  * nth\_element
    * BestN
    * Median, Percentile
  * partition
  * minmax\_element
* Search
  * binary\_search
  * lower\__bound, upper\_bound_
  * find -&gt; returns iterator
