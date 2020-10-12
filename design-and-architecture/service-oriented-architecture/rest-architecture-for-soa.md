## Representational State Transfer \(REST\)

REST is used in distributed applications by using HTTP to send messages to communicate between components.

In REST, the communication is resource-based. The message are sent as representations of resources. **Resources** can by any pieces of information that are self-contained. This can include documents, images, object representations, etc.

### REST Restraints

* Client-Server Architecture
  * allows REST applications to be highly scalable and allows the client and server development to occur independently
* REST is a layered system
  * can consist multiple architectural layers of software or hardware called by the client and server. These can be used to improve performance, translate messages, manage traffic
  * improves reusability of REST web services because layers can be added and removed based on the needed services of client
* Interactions must be **stateless**
  * server does not save information about the current client client or previous requests
  * all information the server needs to respond contains in the request
  * improves the performance of web service
  * trade-off is a significant constraint on how server and client communicate
* Clients can cache responses
  * depending on what information the servers add to the response to label it cacheable or non-cacheable.
  * reduce the same requests for same resource
* There must be a uniform interface for communication between client and server
  * Use Common HTTP methods: 
    * **GET **
    * **POST - create**
    * **PUT - update**
    * **DELETE**
  * format of input and output in HTTP Headers
  * resources must be identified in the request with a specific URI
  * The representations of resources are uniform. 
    * Resources has specific headers, and written in specific ways: XML, JSON, simple text
    * Parameters can be passed in XML, URL, etc

### Best Practices for RESTFul API Design

* Use only nouns for URI
* Get methods should not alter state of resource
* Use plural nouns for a URI
* Use sub-resources for relationships between resources
* Use HTTP headers to specify input/output format
  * Content-Type: defines the format of the message
  * Accept: Defines a list of acceptable formats that can come as a response
* Provide users with filtering and paging for collections
  * help users sort through large data sets. 
  * allowing parameters to be passed in after the question mark symbol
* Versions the API
* Provide proper HTTP status codes



