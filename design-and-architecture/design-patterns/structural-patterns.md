### Structural Patterns

Structural patternsdescribe how objects are connected to each other. Focus on the interaction with system - layout, composition and relationship

#### Facade Pattern

* Provide a simple interface for client to interact with subsystem
* provide a point to interact the system through interface
* combine implementations of one or more classes and wrapped by the facade class
  * Design the interface
  * Implement the interface with one or more classes 
  * Create the facade class and wrap the classes that implemented the interface
  * Use the facade to access subsystem
* ![](/assets/Facade.png)
* Encapsulating the complexity of a subsystem behind a unifying wrapper
* clients do not have to manage the subsystem on their own

#### Adapter - "wrapper" 

* content - interface - adaptee
* facilitate the communication between to systems
  * a client class- class that wants to use sub system or third party libaray
  * adaptee -class that is behind third party library or external system
  * an adapter class - sits between
  * target interface - used by client to send a request
  * ![](/assets/Adapter.png)
* steps
  * Design target interface
  * Implement target interface with adapter class
  * Send the request from the client to the adapter using target interface
* wrap the adaptee and exposes a target interface
* Indirectly change the adaptee's interface
* Reuse existing adaptee

#### Composite Pattern

* to compose nested structures of objects and deal with classes ffor these objects uniformly
* ![](/assets/Composite.png)
* composite class and leaf class share the same interface, the form a tree structure, the main object is the root
* steps
  * Design the interface
  * implement composite, usually has a collection of objects
  * implement the leaf classes
* Enforce polymorphism across each class through implementing an interface
* using recursive composition

#### Proxy Pattern

* allows \(al lightweight\) proxy to represent a real object. A proxy can perform same tasks as the original object, but may delegate requests to the original object to achieve them.
* proxy wraps the real subject class
  * to act as a virtual proxy. Used when a proxy is used in place of a real subject class that is resources intensive to instantiate. \(web pages and graphic editors\)
  * to act as a protection proxy. Use to control access to the real class
  * This is when a class is local and the real subject class exits remotely. eg. Google doc
* ![](/assets/Proxy.png)
* steps
  * design the subject interface
  * implement the real subject class
  * implement the proxy class

#### Decorator Pattern - "wrapper"

* allows additional behaviors or responsibilities to be dynamically attached to an object, through the use of aggregation to combine behaviors at run time.
* Behaviors can be added in stack
* ![](/assets/Decorator.png)
* steps
  * Design the component Interface
  * Implement the interface with your base concrete component class
  * implement the interface with the abstract decorator class
  * Inherit from abstract decorator and implement the component interface with concrete decorator classes
* aggregation let us to create a stack of objects.
* Each of decorator object in the stack is aggreagated in a one-to-one relationship with the object below the stack
* recursively invoke behaviors down and hehaviors execute upwards. 



