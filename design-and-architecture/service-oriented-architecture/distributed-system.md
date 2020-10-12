## Parallel Computing Basics

* [Message Queue](https://en.wikipedia.org/wiki/Message_queue)
  * RabbitMQ, ZeroMQ, Redis, Kafka



## Middleware

In recent years, the rapid growth of the Internet and the falling costs of cloud services have given rise to innovative web services, such as Google Docs, PayPal, and Amazon. Private networks now facilitate client-server communications, even for internal company services.

Clients are not as powerful as servers and they work in heterogenous environments. They communicate with the help of **Middleware**

Middleware is a type of architecture used to facilitate communications of services available and requests for these services between two applications that are operating on environmentally different systems.

* Expected mode of operation is network connectivity
  * legacy systems are redesigned to utilize network connectivities
* Distributed Comptuing 
  * an architecture which computers on a network is able to communicate and coordinate their actions by passing messages through a network
  * enabled developers to design tiered architectures with each layer focusing on specific aspects of the overall systems. Clients and servers can be designed to be specialized and hardware developers are able to create software environments and machine architectures that enhance the specialized characteristics.
* need for middleware to be more sophisticated, or for existing middleware to be extensible
  ![](/assets/Middleware.png)

### Remote Procedure Call\(RPC\)

* Basis for middleware system used for certain web services. 
* Allows client to invoke a procedure in the server
* client and server
  * on separate machines
  * or has different virtual instance
* initial design has
  * client
  * server
  * interface definition language\(IDL\), which is the language client and server communicates 
* includes name and directory services and binding methods to allow client to connect to various servers
* client stub
  * establishing the connection with server by binding
  * formatting the data to a standardized message structure \(eg. XML\)
  * sending the procedure call
  * receiving server stub response
* server stub
* stubs are compiled and linked directly to the client or server component. Calls act like local procedure call because the client stub is in the same address space
* when client components run in different environments than the server, it is possible to create more complete server stubs
* interface headers
  * collection of code templates and references that are used to define what procedures are available at comile time. These files are used in the development of the client and server components
  * basic types
    * procedure registration: tells client what available on the server side
    * procedure call: the actual procedure that is being invoked on the server
    * procedure call by broadcast: procedures invoked by broadcast
* ![](/assets/RPC.png)
* procedure
  * client component invokes the procedure 
  * client stub **marshalls **the parameters \(to a standardized format\)
  * message sent to server \(using the **binding** information given\)
    * static binding: hard coded binding information. \(not allow server redundancy, always connect to a specific one, not run if server offline\)
    * dynamic binding: add another layer to tiered structure, Keeping track of which server bounded and change the binding information if servers change
      * client stub be responsible for static binding with dynamic binding layer
  * server stub receives and **unmarshalls** the message. Arguments convert back
  * server components executes the procedure and returns the result to the stub
  * return result to client stub
  * client stub received and processes the result
* Synchronous vs **Asynchronous** RPCs
  * synchronous will cause **blocking**, the client perform another task till the server returns a result
  * asynchronous behaviors add more complexity to the system because how the system allocates resources for various pending tasks needs to be managed.

### Object Brokers

Evolvement of the PRC with object oriented programming

* Most common one is Common Object Request Broker Architecture\(**CORBA**\), a set of standards/guidelines outline what should be included in the object brokers
  * ensures developers are not restricted to language or system
  * object are distributed among a network of computers/addresses
* Components
  * **object request broker:** provides object interoperability to client and server. object must declare its interfaces before it can be accessed by a client or server through the broker. Broker is responsible for **marshalling and unmarshalling** all the method calls that it receives. Allows client or server to be modified without affecting the other
  * **CORBA services** are services provided by the middleware "to" the object being used by the client and server. Services provided vary and may include functions related to object security. CORBA object are accessible through the CORBA standardized API.
  * **CORBA facilities** provide servers at an application level. These are high-level functions such as document management.
  * ![](/assets/CORBA.png)
* It extends the RPC architecture:
  * IDL is enhanced over IDL in an RPC based system, because IDL is capable of supporting inheritance and polymorphism
  * All object interfaces must be declared in the IDL in order to be presented to the client
  * Corba IDL has a standardized mapping to multiple object-oriented languages
  * Corba IDL Complier is responsible for constructing the client stub and server skeleton. \(They have similar functionality to their RPC counterparts.\)
  * client needs to know the server IDL in order for the two to communicate. 
  * ![](/assets/CORBA-RPC.png)
* Static and Dynamic Interoperability
  * Static binding: occurs when client stub is created. The service that is used is handled by the IDL. 
  * Dynamic binding: no need to generate a stub, instead two components
    * **Interface Repository**: used to store the IDL defintions of "all" the objects being served by a broker
    * **Dynamic Invocation Interface**: Provides all the necessary operations that a client needs for browsing the interface repository, and dynamiccally constructing methods beased on what it discovers. Two ways to discover methods
      * the **naming service** allows the client to reterieve object using the "name" of the interface that it needs
      * the **trading service** let client search objects based on object attributes. 
  * naming convention must be implemented. 
* Benefits
  * Object-Oriented Distributed Computing
  * Objects are independent of addresses and they called by reference
  * variety of options in regards to data. Data can be strongly and dynamically typed. Can also be marshalled into binary form or compressed in order to reduce the size of the data that is sent
  * provides standards for optimization by allowing developers to manage threds and network connectivity settings
* Criticism
  * depend on implementing CORBA standards correctly
  * location transparency: Even if objects interact exist in the same physical or virtual address space, they are still treated as if they were in different spaces. 



