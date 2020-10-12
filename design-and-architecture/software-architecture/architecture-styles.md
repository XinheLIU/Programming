### Language-Based Systems

The programming paradigm of the language selected to implement the system will affect the architectural style of that system.

#### O**bject-oriented architectural style**

One example would be **object-oriented architectural style. **It reflects OO principles\(e.g. Abstraction, Encapsulation, Decomposition, Generalization\) and Design Patterns \(Creational, Structural, Behavioral\)

* System can be broken down to **abstract data types.**
* Objects interact through methods. 
* The overall object-oriented architectural style determined by classes within the system

#### **Main Program and Subroutine **

Another example would be **Main Program and Subroutine \(C\). I**t is more suitable for systems centralized around **computation.**

* Main program calls sub-routines by procedure calls
* calls are nested
* data are stored as variables
* each sub-routine has own local variables
* promotes modularity and function reuse

### Repository-Based Systems

#### Data-Centric Software Architecture

To Solve

* State of component is temporary while the component is running. 
* Component may not need all the data stored in files
* There needs to be a way to communicate the state of components

The architecture

* allows data to be stored and shared between multiple components. 
* increate maintainability, reusability, scalability of the system. 

The core of the system has two types of components

* **Central Data**: Component used to store and serve data across all components that connect to it
* **Data accessors**: Components that are connect to the central data component. The data accessors make queries and transactions against the information stored in the data bas
* ![](/assets/Data-Centric-System.png)
* Central Data is often stored in a database. Database ensure several data qualities 
  * **Data integrity**: Ensure that data is accurate and consistent over its lifespan
  * **Data Persistence**: A database ensures that data will live on after a process has been terminated. 
* Data base can be relational \(SQL\) or non-SQL. The management and optimization of queries and transactions can be automated by a** data management system\(DBMS\). **
* Data accessors has the abilities
  * share a set of data and operate independently
  * communicate with the data base. Do not need to know about each other
  * Query and get data
  * Save and Change data
* benefits
  * increased data integrity, data backup and data restoration
  * reduced overhead for data transfer between data accessor
  * can be easily scaled up. \(data accessors are independent\)
  * central data live on a separate server, allows easier management information
* drawbacks
  * Heavily reliant on the central data component. 
  * New data accessors need to build around existing data schema. accessors depends on the central component
  * It is difficult to change the existing data schema

### Layered Systems

* Layer is a collection of components that work together towards a common purpose
* Each layer only interact with components in its own layer or adjacent layers
* Allow separation of concerns, many layered system is split into "presentation", "logic" and "data" layers
* advantages
  * user can perform complex tasks without needing to understand the layers below
  * different layers have different levels of authorization or privilege. eg. Top-level "user space" cannot have authority to allocate system resources or communicate with hardware. This **sandboxing **provides security and reliability to the kernel
  * designs will be more loosely coupled. \(Principle of Least Knowledge\)
* Overhead must be balanced against the **separation of concerns gained. **
  * If most communications passing through the layers. the design may need to be relaxed.
  * pass-through sometimes are allowed
  * 3-D or more complicated structures sometimes happen

eg. a Computer Operating System

![](/assets/Computer-OS.png)

#### Client-Serve n-Tier

n-Tier or multitier architectures are related to layered architectures.Tiersrefer to components that are typically on different physical machines.

The number of tiers in an n-Tier architecture can vary, although three-tier and four-tier architectures are common

*  The relationship between two adjacent tiers in an n-Tier architecture is often a **client/server** relationship. In a client/server relationship, one program \(the **server**\) provides services such as storing information in a database or performing computation tasks upon request from another program \(the **client**\). This communication is known as the **request-response**.
* **Client-host** and **server-host** refer to machines that host client software and server software respectively.
* **Request-response** relationships can be **synchronous** or **asynchronous**.
* Limiting client/server relationships to request/response messaging patterns allows for systems that can be scaled more easily by adding clients.
*  Clients and servers are extensible, because as long as a server receives a message it knows, it will respond. The source of the message is not important to the server, so many clients can be added as needed.

You could also build a three-tier architecture, where a tier is inserted between the database and end users. 

* This tier is often referred to as a **middle layer**, a business layer, or an application layer—its name depends on its main responsibility. The middle layer will be a client of the database, and a server for the client application software on the end users’ devices. 
* Middle tiers help determine how or when data can be changed, and in what ways. Having a middle layer allows client application software to be thinner, as it can be focused on presentation only. This makes it easier to maintain.

* potential drawbacks :
  * It requires extra resources to manage the client/server relationships. If more tiers are added, there are more machines or processes to manage, with different communication protocols. This makes a system more complex, and therefore more difficult to change and maintain.
  * A server acts as a central point of failure. Systems may have backups or mirrors, but it can take time to switch to these backups and recover the server. Redundant servers are possible but add complexity.
* The advantages 
  * n-Tier architecture is very scalable. Clients can continue to be added as long as a server can handle all the requests it receives in a reasonable time.
  * Centralization of functionality allow for data to reside on one machine but to be accessible by any machine on the same network.
  * n-Tier architecture supports separation of concerns. Middle layers can take the role of managing application logic and accessing the database directly. Adding tiers can further allow for loose coupling and levels of abstraction, making a system that is easier to change and extend.
  * Centralization of computing power allows client machines to require less processing power. Companies can thus offer processing power as a service, which is more practical and cost effective.

### Interpreter-Based Systems

Interpreter-based systems allow end users to write s**cripts, macros, or rules** that access, compose, and run the basic features of those systems in new and dynamic ways. Interpreters can run scripts and macros. 

* Scripts are often used for automating common tasks, such as scheduling tasks, performing repetitive actions, and composing complex tasks that invoke other commands.
*  Macros are an evolution of scripts that became popular with the introduction of graphical user interfaces. A macro records keyboard and mouse inputs, so they may be executed later.
* Interpreter-based systems encourage end users to implement their own customizations.

advantages

* In particular, interpreters make systems more **portable**, so they can work on platforms that the interpreter supports.
* It provides users with flexible and portable functionality that can be applicable in a variety of commercial systems.
* abstracting away platform details

disadvantages

* Interpreters can be slow.
* Basic implementations spend little time analyzing the source code and use a line-by-line translate and execute strategy. This is a trade-off: it may be faster and more flexible for developers and end users to use an interpreted language, but slower for computers to execute interpreted code.

### Data flow Systems

**Data flow systems** involve a series of transformation on sets of data. Data is transformed from one form into another using different types of operations.

**pipe and filter architectural style**, a specific type of data flow architecture.

A pipe and filter architectural style has independent entities called **filters**, which perform transformations on data input they receive, and **pipes**, which serve as connectors for the stream of data being transformed.

![](/assets/Data-flow1.png)  
![](/assets/Data-flow2.png)

Advantages to using the pipe and filter architecture include:

* Loose and flexible coupling of components. In particular, this applies to filters. Each filter runs independently of other filters, which allows the easy addition of new filters, of moving filters around, or of changing individual filters in a system. 
* Filters can be treated as black boxes. Users of the system do not need to know the inner workings of each filter.
* Reusability. Each filter can be called and used over and over again with different inputs. Filters can be repeatedly used in many different applications for different purposes

Disadvantages to using the pipe and filter architecture include:

* Reduced performance due to excessive overheads in filters. Each filter must receive input, parse that input into some data structure, perform transformations, and send data out. If every filter must do this, it is a lot of overhead, and the performance of the system will be affected as more and more filters are added.
* Filters may get overloaded with massive amounts of data to process. If one filter is working to process large amounts of data, other filters may be waiting for inputs.
* This architecture cannot be used for interactive applications. Applications that require rapid responses will not find this architecture suitable, as data transfers and transformations take time depending on the amount of data being transmitted.

### Implicit Invocation Systems

In **implicit invocation systems**, functions are not in direct communication with each other. The **event-based architectural style** is one design for such a system. This style derives from the event-driven programming paradigm.

#### Event Based

This style derives from the event-driven programming paradigm.

In event-based architectural styles, the fundamental elements in the system are **events**. Events are both indicators of change in the system and triggers to functions. Events can be signals, user inputs, messages, or data from other functions or programs.

Under the event-driven programming paradigm, functions take the form of event generators and even consumers. Event generators send events, and event consumers receive and process these events. A function can be both an event generator and an event consumer.

* In the event-based architectural style, functions are not explicitly called. Instead, event consumers are based on events sent from event generators. Event-based functions experience **implicit invocation**, where communication between functions is mediated by an **event bus**. An event bus is the connector between all event generators and consumers in the system.
* When the event bus detects an event, it distributes the event to all appropriate **event consumers**. The event bus is a critical part of the system. The observer design pattern actually manifests the event- based architectural style.
* When designing your system, it is important to take into account that indirect communication between functions may not be as efficient as explicit function invocation.
* This asynchronous design may increase efficiency of the system, but it can also result in race conditions. Race conditions mean that the correct behaviours of functions is sensitive to timing or order, so shared data may not be updated correctly.
* Functions can be coordinated for access to shared data through a **semaphore**. A semaphore is a variable or abstract data type that toggles between two values, available and unavailable, and that is used to control access to shared data. Available indicates that the shared data is not in use, and unavailable indicates that the shared data is in use by a function.
* If an object is not globally accessible and its state is changed by an event consumer, then some indication must be sent back to the event bus before the function ends. Event consumers can thus be aware of the state change to that event.
* n event-based architectural styles, events and functions do not behave in a predictable way. There is no guarantee of exactly when an event will be handled, how long it will take to handle, or when an event generator will emit an event. Control flow is thus based on which events occur during its execution and in what order
* Event-based architecture styles are well suited to interactive applications. Graphical user interface applications that rely on user input and distributed systems that interact with other programs are prime candidates for this style.

### Process Control Systems

#### **Feedback Loops**

A **feedback loop** is one of the most basic forms of process control. It has four basic components: a sensor, a controller, an actuator, and the process itself. The sensor monitors some kind of important information. The controller is the logic of the system. The actuator is the physical method of manipulating the process. The process is what is trying to be controlled.

The frequency, or how often the loop runs, depends on the desired level of control and the sensitivity of the system. For example, room temperature changes slower compared to other processes, so it is not necessary or useful to have a high frequency, such as every microsecond.

#### **Feedforward** control

**Feedforward** control occurs in systems with processes in series. Information from an upstream process can be used to control a downstream process. Feedforward control requires a good model of how process response and deals with unknown events. These systems are often used in conjunction with feedback loops. （eg, flood control system\)

#### MAPE-K structure

MAPE-K structure, which has four major steps: monitor, analyze, plan, and execute.

