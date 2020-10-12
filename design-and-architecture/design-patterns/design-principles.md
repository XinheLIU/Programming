### Design Principles

#### Liskov Substitution Principle

* A Subclass can replace a superclass, if and only if, the subclass does not change the functionality of the superclass
* If a subclass replaces a super class, but replaces all the superclass behaviors with something totally different, then inheritance is being misused. 

#### Open/Closed Principle

* open for extension
  * open by inheritance
  * declare in abstract and do polymorphism
* close for change
  * all attributes and behaviors are encapsulated and proven to be stable to the system
  * changes should mostly happen in design and analysis of the system

#### Dependency Inversion Principle

* High level modules should depend on high level generalizations and not low level details
* client classes independent of low level functionality \(depend on abstract class or interface\)
* ![](/assets/DependencyInversion.png)

#### Composing Objects Principle

* classes should achieve code reuse through aggregation rather than inheritance
* examples like composite pattern and decorator pattern
* composing objects provide the system with more flexibility and allows dynamic change to behaviors at run time
* ![](/assets/ComposingObjects.png)

#### Interface Segregation Principle

* Tackles dependency issue so that you will not be forced to generalize everything into one interface
* The class should not be forced to depend on methods it does not use. Any classes that implement an interface should not have "dummy" implementations of any methods defined in the interfaces. 
* Large interfaces should be split into smaller ones in a way that it can still describe separate functionalities of the system

#### Principle of List Knowledge\(Law of Demeter\)

* classes should know about and interact with as few other classes as possible
* set of rules provide guideline as to what kind of method calls a particular method can make
* An object should call other methods if they are: \(local object\)
  * Encapsulated within the same object
  * Encapsulated within an object that is in the parameters of M
  * Encapsulated within an object that is instantiated inside M
  * Encapsulated with an object that is referenced in an instance variable of the class of M
* Or reach out by a Returned Object, must be of the same type as:
  * Those declared in the method parameter
  * Declared and instantiated locally
  * Declared in instance variable of the class that encapsulates the method
* a method should not be allowed to access another method by "**reaching through"** an object 

### Anti-Patterns \(Code Smells\)

* Comments
  * no comments
  * too many comments can be a "deodorant" for bad smelling code
  * as a "reminder" to change other places
  * type casting - may indicating using a wrong language
  * appropriate comments are very Useful in API documentation
* Duplicate Code
  * D.R.Y - don't repeat yourself
* Long Method
  * definitions of long varies
* Long Class
  * God Class, Blob Class, Black hole class
  * difficult and time consuming to fix/maintain, comments needed
* Data Class
  * class with only data but behaviors
* Data Clump
  * data appear together should be grouped together as well
* Long Parameter List
  * may break encapsulation - needs to look into the class
  * fix with parameter objects
* Divergent Class
  * have to change class in many different ways for different reasons
  * class should have only one specific purpose
  * responsibilities should be broken for large class \(related to Long Class smell\)
* Shotgun Surgery
  * one change needs to touch many classes
  * sometimes not avoidable
* Feature Envy
  * one class is interested in the feature of another class
  * they should be put together
* Inappropriate Intimacy
  * closely coupled classes
  * sometimes cycles are good
* Message Chains
  * multiple calls in a long chain, potentially violate the Law of  Demeter
  * sometimes appropriate if follows the Law of Demeter
* Primitive Obsession
  * use too many built-in types
  * non-OO thinking, less separation
* Switch Statements
  * switch may indicates one change in many places
  * sometimes can be good
* Speculative Generality
  * should perform just in Time Design,  should not generalize not used features
* Refused Bequest
  * Subclass inherits something by does not need it. 
  * Sometimes indicates the abusive use of inheritance



