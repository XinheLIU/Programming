When user submits a request:

request -&gt; Web server -&gt; HTTP server -&gt; Web Application Framework -&gt; returns web page

* Web Application Framework/Web Framework
  * Common ones
    * Django
    * Flask
    * Spring, node.js, Ruby on Rails
  * functions
    * parse requests
    * find modules, functions
    * interaction with database
      * ORM - Object Relational-Mapping
    * renders webpage to user
* HTTP Server
  * PHP
* Web Server
  * Common ones
    * Apache
    * Uwsgi
    * Ngmx, Gunicorn
  * data 
    * Structured data
      * JSON, HTML
    * unstructured data
      * HTTP
* Firewall
* Load Balancer 

HTTP

* Domain
* IP Address
* URL
* DNS

Web

* Cookie 
  * CSRF Token
* Session

Java injection attack, SQL injection attack

Web Technologies

* Web Protocols
  * TCP/IP
  * HTTP
    * HTTP Codes
* Web Service

Object-Database-model

SQL injection attach

Web Framework

Http Server

Apache,

Ngmx

Gunicorn

uwsgi

node.js, spring, Django, Ruby on Rallis

IP Address

URL

Domain

Layers

* Data Tier\(store, maintain, manage\)
* Application Tier\(ensure function and service are performed\)
  * static web page does not have an application layer
* Presentation Tier
  * Web Server Layer\( obtains requests, returns to browser\)
  * Web Browser Layer\(top most\)

![](/assets/ServiceView.png)

### HTTP

#### HTTP Requests  and HTTP Responses

* request line
  * request method
    * GET - retrieves the resources given by the URI provided in the request line.
      * url encoded
    * POST - add or modify resources according to the message body of the request, submit data 
      * url encoded
      * server will decide the resource location
    * PUT
      * takes the information provided in the body of the request, and creates or updates a resource at the location specified in the URI of the request
      * URI specified in request dictates to the server the identity and location of the enclosed resource
      * server sends HTML in request body, browser requests
* headers
  * mandatory: host \(IP address for the host\) and accept\(what content the client will accept\)
* blank line
* message body\(optional\)
  * HTML, JSON, encoded parameters

#### Server Response

* status line
  * status code
* headers
  * can be optional
* blank-line
* message body\(optional\)

HTTP limits the characters used in URIs, request queries and bodies to be ASCII.

* Unsafe characters often replaced with a "%" sign
* "&" to join parameter value pairs

#### HTTP Stateless

* Relationship between requests is not preserved



