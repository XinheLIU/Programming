## System Design Steps

* Scenario
  * functionalities, requests
  * current users/API/QPS/DAU/features
* Service
  * split to applications/modules/service
  * server
    * QPS
      * web server
      * single point failure
      * web server cluster
* Storage
  * database, SQL, NOSQL, File system
    * data relations, schema
  * Persistency 
  * Cache
* Scale
  * sharding
  * optimize
  * edge case

## Service-Oriented Design and Architecture

Service-oriented architecture\(SOA\) focuses on how to build, use and combine services. Instead of creating large software suites that do everything, service-oriented architecture reaches software goals by building and using services, designing an architecture that supports their use.

Two most common use case

* Web service. 
  * trade-off: existing service must be balanced against qualities of service\( out of control of developers\)
    * response time, supportability, availability
* large organization
  * service used by different departments \(interfaces\)
  * trade-off: outsourcing or in-house

#### Service Principles

* Modular and Loosely coupled
  * requests and pass back
* Composable
* Platform and Language-independent
  * communications use standard protocols\( eg. XML File or HTTP requests\)
* Self-Describing
  * should describe how to interact with it
  * Web Service Description Language**\(WSDL\)**
* Self-Advertising
  * Universal Description, Discovery and Integration**\(UDDI\)** standards





