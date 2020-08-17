# String

## Memebers

* size
* substr\(&lt;start&gt;,&lt;size&gt;\)
* find
* erase
* insert
* max\_size
* c\_str(), data()
  * cast to **C-style String*
  

basic\_string

* Template type basic\_string to support different char types 
* C is single byte char type, not support unicode
* C++ has different types
  
  * ```cpp
    using string = std::basic_string<char>;  // string is a type alias
    using wstring = std::basic_string<wchar_t>; // C++ 98
    using u16string = std::basic_string<char16_t>; // C++ 20
    using u32string = std::basic_string<char32_t>;
    ```

* wstring is rarely used, in most cases not deal with Unicode, string encoding with C++
* UTF-8 is compatible with single byte char

String type

* **immutable** type, not container \(not vector&lt;char&gt;\)
* postfix "s" since C++ 14

  * ```cpp
    using namespace std::literals::string_literals;  //必须打开名字空间

    auto str = "std string"s;      // 后缀s，表示是标准字符串，直接类型推导

    assert("time"s.size() == 4);   // 标准字符串可以直接调用成员函数
    ```

* Raw string literal \(C++11\)

  * ```cpp
    auto str1 = R"(char""'')";    // 原样输出：char""''
    auto str2 = R"(\r\n\t\")";    // 原样输出：\r\n\t\"
    auto str3 = R"(\\\$)";        // 原样输出：\\\$
    auto str4 = "\\\\\\$";         // 转义后输出：\\\$
    auto str5 = R"==(R"(xxx)")==";// 原样输出：R"(xxx)"
    ```

    * \(, \) is added 16-bit delimiters

* type conversions \(C++ 11\)

  * ```cpp
    assert(stoi("42") == 42);          // int
    assert(stol("253") == 253L);       // long
    assert(stod("2.0") == 2.0);
    assert(to_string(1984) == "1984");
    // C String
    c_str("hi")
    data("hi")
    ```

  * c_str() has '\0' at the end 
  * Boost libaray has **lexical_cast** to do conversion
* [string\_view](https://en.cppreference.com/w/cpp/string/basic_string_view) \(C++ 17\)

  * keeps only pointer and length
  * shallow copy and mutable

* char8\_t \(C++20\)
  * unsigned char for UTF-8
  * u8string, u8 \(C++20\)
* c\_string\(\) vs data\(\)
  * c\_string\(\) will add '\0'

## Regular Expressions

[Regular expressions](https://www.pcre.org/)

in C++

work with std::regex

* regex\_match\(\)
* regex\_search\(\)
* regex\_replace\(\)

```cpp
auto make_regex = [](const auto& txt)    // 生产正则表达式
{
    return std::regex(txt);
};

auto make_match = []()                  // 生产正则匹配结果
{
    return std::smatch();
};

auto str = "neir:automata"s;          // 待匹配的字符串
auto reg = 
    make_regex(R"(^(\w+)\:(\w+)$)");  // 原始字符串定义正则表达式
auto what = make_match();             // 准备获取匹配的结果
```

* basic_regex, match_results renders differently for char* and and string (with cmatch, smatch, etc)

Thrid party libaries like PCRE, Hyperscan, libsregex