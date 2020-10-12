### Compiling

* Procedure: Source code—compiler \(Assembly Code\)— Machine Code\( 01s\) \(eg. C program\)
  * preprocessing \( to translation unit\)
  * assembling
  * compiling \(to obj\)
  * linking \( link with libraries, to executable files\)
* Branches
  * structured programming\(FORTRAN, COBOL, C, Pascal\)
    * "goto" argument
  * modular programming\(C, Pascal\)
  * object-based programming\(CLU from MIT\)
  * object-oriented programming\(SmallTalk, C++, Java, C\#, Python\)
  * generic programming\(many algorithms and containers implemented - C++ STL, java generics\)
  * constraint/logic programming\(prolog\)
  * functional programming\(haskell\)
* Compilers
  * gcc, g++
  * clang\(for C\)
* IDE - Integrated Developer Environment

### Common Concepts

* FILE - starts with specific hexadecimal numbers \(different file headers and info headers\)
  * graph-bmp,JEPG, PNG
    * color - 1 bit color to 32-bit color \(per pixel\) RGB color code
* FILE System 
  * FAT - 512 bytes block
* wrapper

### **Programming Language Design**

* Three criteria
  * Correctness
  * Coding style \(check by lint\)
  * Design

### Programming Paradigm

* **Imperative Paradigm**: Break up large programs into **subroutines. Global Data**\(locate in one place, accessible to one program\) is used to optimized performance
* * COBOL, Fortran
* **Procedure Programming:** introduce local variables \(subroutine and procedure's own variables\). Support abstract data type. \(defined by programmer, not built into the language\), this is a grouping of related information that is denoted with a type.organize information in a meaningful way.
  * Algol 68, Pascal
* **Modular Languages**: provided means to organize programs into separate files, allow developers to create multiple but unique copies of abstract data types.  \(eg. in , library, and header file\)
  * C,  Modula-2
* **Object-Oriented Programming**: allow inheritance of abstract data types. Structure programs around ABD called classes. \(methods + data\). 
  * C++, Java

### Functional Programming

Functional Programming is treating function like an object/data

* data type: form domain to range
* definition
* name/ address

Design/Style requirement for Functional programming:

* Pure : f\(x\) = f\(y\) for x=y in domain
* Side-effect free: operation on function object not cause variables other than return values change\)

#### 



