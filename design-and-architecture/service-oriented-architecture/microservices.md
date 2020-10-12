* Micro-services is a kind of variation of SOA. But on an application scale rather than an enterprise scale.
* The** microservice architectural style **is a way of composing microservices to produce complex applicaions. 
* In microservices, some SOA principles have been refined to better support application scale systems.
* A microservice is a process that is responsible for performing a single independent task. A microservice typically is built to perform a specific business capability. 
* The compose together to provide overall functionality of an application.
* REST interfaces are used to keep communication between microservices stateles
* Each microservice has a well-defined interface or API that informs other microservices how it can be used and communciated with
  * Communication is generally done through standards and protocols such as HTTP or XML

##### Advantages

* Independent of implementation of each microservice.
  * each can use language, frameworkds, and architectures best suited to the service. 
  * can use new technologies without making an application-wide commitment
* Microservices makes applications easier to scale
  * A particular microservice can esaily be scaled by replication.
  * If there are multiple copies of the same microservices, the multiple requests to the oringinal one can be handled in parallel
* Microservices make applications more resilient to failure.
  * one instance fail, other instances continue to function
* Can be scaled independently
  * have loose coupling. This allows them to be scaled independently, which is important because not all microservices within an application need to scale at the same rate
* Microservices offer modular maintenance
  * one microservice at a time
* Can be developed quickly, and deployed and maintained by a small, independent team

**Disadvantages**

* centralized management of all microservices will be required to coordinate all the microservices
  * An application made up of microservices is a distributed system through asynchronous communication, must have some central method for management
* Transactions may span multiple microservices
  * Database will likely to be distributed over multiple microservices, so transactions may span multiple microservices. 
* Testing is complex
  * Test conditions change
  * difficult to reproduce bugs about complex interactions between microservices
* All microservices in the application must be robust to handle failures of other miscroservice
  * system must be able to cope with microservice failures

### Usage

* Wide range of applications 
  * one exceptions is for older, monolithic applications that reply on pre-compiled binaries 
* Need to consider the amount of communication that will be required between microservices in an application
  * depending on the application, it might be useful to track the interactions \(though it is stateless\)











