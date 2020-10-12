# Java

- [Java](#java)
  - [Basic Grammar](#basic-grammar)
    - [Primitive Data Types](#primitive-data-types)
      - [Operators](#operators)
      - [Control flow](#control-flow)
    - [Input/Output](#inputoutput)
    - [Reference Data Types \(inherited from Object）-Array, Class, Interface](#reference-data-types-inherited-from-object-array-class-interface)
      - [Auto boxing and Unboxing](#auto-boxing-and-unboxing)
    - [Variable Scopes](#variable-scopes)
    - [Naming Conventions](#naming-conventions)
  - [Class and Basic OOP](#class-and-basic-oop)
    - [Inheritance](#inheritance)
      - [Reference, Instance and Class](#reference-instance-and-class)
      - [Composition](#composition)
      - [Inner Class](#inner-class)
    - [Polymorphism](#polymorphism)
      - [Interface](#interface)
      - [Abstract Class](#abstract-class)
      - [Static](#static)
    - [Java Generic Class](#java-generic-class)
    - [Package](#package)
      - [Access Modifier: Public, Protected, Private](#access-modifier-public-protected-private)
  - [Learning Resources](#learning-resources)
  
## Basic Grammar

### Primitive Data Types

- byte, short, int, long\(L\) \(eg. 5000L\)
- float\(f\), double\(d\)
- char
- boolean

#### Operators

- \- can be used as string\(Java is smart, string + float can figure out\)
- ++,--,+=,
- ?:, &&, \|\| 
- &gt;&gt;,&lt;&lt;,&gt;&gt;&gt;\(unsigned right shift\)

#### Control flow

- for \(like c\), while, do while
- if, switch...break...default

### Input/Output

- system.out.println\(\)
- Scanner Class \( scanner = new Scanner\)
  - hasNextInt\(\), nextInt\(\),nextLine\(\) 

### Reference Data Types \(inherited from Object）-Array, Class, Interface

- string
- Array: &lt;type&gt;\[\] name;
  - Collection&lt;?&gt;\[\] name: array of collection of unknown type
  - length: public field
  - clone method
- List: an interface \(Linked List abstract data type\)
  - ArrayList -dynamic arra
    - findItem\(\), searchItem\(\)
    - add\(\), remove\(\)
    - set\(,\), get\(,\)
    - indexOf\(\)
    - clear\(\)
- Iterator
  - Container.iterator\(\) returns an iterator
  - hasNext\(\)
  - Next\(\)
  - remove\(\)

#### Auto boxing and Unboxing

- deal with the direct assignment between Object variables and Primitive Variables
  - Integer a = b : Integer a = Integer.ValueOf\(b\)
  - int b = a, a is Integer : Int b = a.intValue\(\) 

### Variable Scopes

- Look inside closing blocks inside out {} 
- most local one shadow the others
- inner class private ones are visible to outer class, vice versa
- Look for variables upchain to super class 

### Naming Conventions

- CamelCase
- CONSTANTs are uppercases
- Package
  - always lower case
  - Use internet domain name reverse, as prefix of packages name
    - Replacements Switch.supplier.com -&gt;com.supplier.\_switch \(invalid characteristics are placed by underscore\)
- Type Parameters
  - E - Element
  - K - Key
  - T - Type
    - S, U, V - ... more types 
  - V - Value

## Class and Basic OOP

- methods - member functions
  - methods overloading
  - setters, getters 
  - static main\(\) - called by Java Virtual Machine\(JVM\) starts the program 
- fields - data members 
- new - keyword calls the constructor 
- this - refer to the class itself
- constructor - the same name function as class
- static method - common operations shared by all instances 
  - no access to instance methods\(other member functions\) or fields\(data members\) or this
  - usually for common operation without using data
- static member variable: shared by all instances

### Inheritance

- A extends B
- super - refer to the parent class
  - super-parent constructor
- @override: override parent class methods
  - constructors and private methods cannot be inherited/overriden

#### Reference, Instance and Class

- new creates instances
- assignment is by reference

#### Composition

- has-a relationship
- member class - class uses another class as member

#### Inner Class

- In-memory class declared inside another class
- must instantiate the outer class first
  - &lt;Outer&gt; a = new Outer\(\); &lt;Outer&gt;.&lt;inner&gt; = a.new inner\(\);

### Polymorphism

- Assign an child class object to a parent/interface variable

#### Interface

- Interface
  - no non-static fields
  - declaration\(signature\) of functions - no implementations
- A implements B: requires A to implement all the methods in B
- form a contract between the class and the outside world, the contract is enforced by complier at the build time
  - separate "what" and "how" \(eg. Collections API, JDBC API\)
- all methods are automatically public and abstract
- Since Java8, interfaces can contain default methods

#### Abstract Class

- Cannot be Instantiated 
- Contains Methods without Implementation
  - can define public, protected, private concrete methods
- Can contain non-static fields
- Can extend only one parent class, but implements multiple interfaces
- Child class \(Inherited from Abstract Class\) should implement abstract methods/be an abstract class
- Used to
  - Share code among closely related classes
  - Children share common methods in a protected/private scope
  - provide default methods that may/may not be overriden
- final - cannot be overwritten by children

#### Static

- Static field/method/block/nested class: shared by all instances of a certain class
- can be involved with out instantiating the object, static methods should not contain non-static data memebers
- Improve memory efficiency

### Java Generic Class

- Type variable: unqualified identifier
- Generic class/interface/method: contains any type variable
- A constructor can be declared generic \(with a type variable\), independent of the class
- Type wildcards &lt;?&gt;: stands for an unknown type: any methods or arguments passed to members should be c child of the unknown type
  - List&lt;?&gt; would be parent of List&lt;String&gt;, List&lt;Integer&gt; ... \(All concrete types\)

### Package

- Bundles classes together and creates name scope
- Import &lt;package&gt; , \- is a wildcard

#### Access Modifier: Public, Protected, Private

- Public: accessible to current class, current package, parent and children class, other pacakges
- Protected: not accessible to other packages
- Friendly: not accessible to parent, children and other packages
- Private: only accessible in current class, not accessible in current pacakage

## Learning Resources

- Core Java Volume I - Fundamentals \(10th Edition\)
- SPRING IN ACTION:COVERS SPRING 3.0
- SPRING BOOT IN ACTION
- Effective Java
- Java Concurrency in Practice \([Brian Goetz](https://book.douban.com/search/Brian Goetz) / [Tim Peierls](https://book.douban.com/search/Tim Peierls) / [Joshua Bloch](https://book.douban.com/search/Joshua Bloch) / [Joseph Bowbeer](https://book.douban.com/search/Joseph Bowbeer) / [David Holmes](https://book.douban.com/search/David Holmes) / [Doug Lea](https://book.douban.com/search/Doug Lea)\)
- Java Performance: The Definitive Guide, Scott Oaks
- 深入理解Java虚拟机（第2版）周志明

Spring

- 精通Spring 4.x