## Web Service

* Enterprise Application Integration\(EAI\) system is an enterprise-level solution for integration problems in integrated systems. It uses middleware
  * It is unable to solve B2B issues
* Web Service implemented for interactions between businesses. 
* It uses the following technologies
  * Web Infrastructure\(TCP/IP to HTTP\)
  * Invoking\(SOAP\)
  * Describing\(WSDL\)
  * Publishing and Discovery\(UDDI\)
  * Composition\(WS-BPEL\)

### SOAP

Web service uses XML messages for communication between service requesters and service providers. The request-response messaging pattern is the basis of all interactions between web services and the software uses those services.

* The XML document is identified as a SOAP message by the envelope. 
* SOAP must have a body contains information that the service provider need to determine which service to provide and service's input.
* Two Styles
  * Document Style SOAP: structured document. Type determined by the type of the document
  * RPC Style SOAPL body of the message is similar to a method-call, consists of an operation and input paramters. 
* Sent using HTTP POST or SMTP
* ![](/assets/SOAP.png)
* Messaging Patterns
  * Request-Response\(Synchronous\) can use HTTP
  * Solicit-Response. Provider makes a request to the requester\(Synchronous\)
  * One-Way: no response needed\(Asynchronous\)
  * Notification: Service Notifies the Requester\(Asynchronous\)
  * 

### Web Service Description Language\(WSDL\)

* Help the SOAP messages find services, and understand how to interact with services, including parameters. WSDL can be read by potential requesters. 
* Include how to structure a request, input needed, data the service will output and the location where the service requester will send SOAP messages, the transport protocol it will be sent on and more.
* WSDL helps to generate code to interface with the service directly-binding
* Most important part of WSDL 2.0 include
  * Types \(define abstract data types in XML\)
  * Interfaces \(order of operations can be described by message types\)
  * Bindings. Determines how SOAP message is translated into XML. 
    * Interfaces are abstract
    * specify between document type of RPC Type
    * specify transfer protocols
  * Service
    * Assign interface and bindings to endpoints or ports. These are located with URIs

### Universal Description, Discovery and Integration\(UDDI\)

Managed by OASIS, a protocol for publishing and discovery, and not a necessary component of implementing web services, it is not tied to a specific registry. If the binding is known, discovery is not needed.

* Allows services providers to publish services to a uDDI registry
* requesters can search elements of WSDL description
* ![](/assets/UDDI.png)
* Publishing
  * Needs service provider, service itself, various technical descriptions
  * URI is assigned to the service by UDDI registry
* Information contained
  * White pages: business name, short desctiption and unique business identification code
  * Yellow Pages: hierarchical information about the business
  * Green Pages: Technical Details of how to use the service
* Information has four data structures
  * business entity: like White Page
  * business Service Like Yellow Page
  * binding Template: included in Green Page
  * tModel: flexible data structure can be nested to provide various meanings: Included in Green Page
  * ![](/assets/UDDI Types.png)
* Dynamic Binding
  * can be highly dynamic
  * more challenging to descriptions and requesters\(Cannot see the error\)
  * binding becomes a design decision

### BEPL

* WS includes are various standards build on the foundational standards of SOAP, WSDL and UDDI for web services. The standards usually have the prefix WS.
* WS-BEPL\( Business Process Execution Language\) facilitates service composition as it allows developers to combine exisiting services into new, composite services. 
* Web services are not usually compiled and run in the same physical location like objects,
* Composing Services involves invoking services in a certain order and handling exceptions that may arise. 
* A composite service could be like a "script" uses other services according to some pre-determined order.
* ![](/assets/BEPL.png)
* difficult because the interface can be not standardized
* Easy because can be accessed in similar ways
* BEPL allows to combine basic services as a new service and supports logic like if-els

Apart form compositin, web services are also associates with coordination. **Coordination** is when a process coordinates the activities of two or more services. Composition is distinguished from coordination because it exposes the collection of actions as another service.

