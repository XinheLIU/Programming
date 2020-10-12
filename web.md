### The Web

#### History of the Web

Internet - Static Web Page\(HTML\)-Dynamic Web Pages\(Application/Server Code generated HTML\)-Web Application\(general user interfaces\)-Web Services

### Protocol

#### HTTP - hypertext transfer protocol

* Server-Client relationship
  * server: a program responds the request of the user
  * Router: the Gate Keeper program to send inside requests out
* an \_**application layer **protocol - \_specifies the format user request the server and server returns to users
* **Hypertext **\(text and multimedia\) is a document embedded with **hyperlinks**
* **Universal Resource Identifiers\(URIs\) **are addresses used to identify resources. Universal Resource Locators\(URLs\) are a subset of URIs.
* https - secure for encrypted website
* send request _method\(e.g. POST/GET\) request-target HTTP/1.1_ : combine with hostname line, it can specify a resource.

  * **GET **requests a representation of the specified resource. Note that GET should not be used for operations that cause side-effects, such as using it for taking actions in web applications. One reason for this is that GET may be used arbitrarily by robots or crawlers, which should not need to consider the side effects that a request should caused

    * Get can be cached, stored in the history and bookmarked

  * **POST **submits data to be processed \(e.g., from an HTML form\) to the identified resource. The data is included in the body of the request. This may result in the creation of a new resource or the updates of existing resources or both

    * POST can never be cached or stored, not remain in history

* Code

  * success: 200
  * redirection: 301, 302
  * client error:401, 403, 404
  * server error: 500

#### TCP/IP

* TCP - transmission commit protocol : 
  * allow for reliable, ordered, connections oriented communication. 
  * marks transimission \(eg. all pieces are sent or need to be resent\)
    * eg. 80 - SSH : secure shell, 443: encrypted web, 200:okay 
    * port number: every program/utility/service has a port number, combined with IP address, it uniquely identifies every program on the internet
      * 21: FTP-file transfer 
      * 25: SMTP
      * 53:  DNS
      * 80: HTTP\(web browsing\)
      * 443: HTTPS \(secure web browsing\) 
    * guarantee delivery of packets by transmitting and keeping information on how many packets to be expected in what order - whether need to request again
    * drop packet
* IP - unique web-location: from 32-bit\(IPv4\) to 128-bit\(IPv6\): location of computer/ web server etc. 
  * represented in 4 8-bits decimal numbers w:x:y:z or 8 hexadecimal numbers \(may omit the zeros by::\) s:t:u:v:w:x:y:z
  * private IP address to share
  * send all data in packets \(eg. email, FTP file transfer\) 
* Access Points: router\(or router, modem, switch\) - allows data on your local network to be processed through a single IP\(IPv4\)
  * routing \(via IP\)- store "where to go" information in a routing table \(for shortest path\) 
  * re-routing : around the traffic jam \(IP is a_ connectless_ protocol\)
* DHCP Server - Dynamic Host Configuration Protocal server to assign IP to devices
* DNS Server- Domain Name System to translate ip to human-memorable names\(host\) 
  * work as aggregators, large servers\(eg. google\) pool smaller set of DNSs together
* TCP/IP Process: TCP breaks into piece -&gt; add TCP layer --&gt; add IP layer -&gt; receive, take out the IP layer -&gt; take out TCP layer, place into correct order, whether need to resend

* Application layer protocals

  * FTP - file transfer protocol
  * SMTP - simple mail transfer
  * DDS - data distribution service
  * RDDP - Remote Desktop 
  * XMPP

* Linux visit - curl

  * http-server -p

### Technologies

#### HTML

* a Mark-up language \(hyper-text markup language - no logic, only text\)
* tags
  * &lt;b&gt;,&lt;/b&gt; : bold, &lt;i&gt;,&lt;/i&gt; : italic, &lt;u&gt;,&lt;/u&gt; : underline
  * &lt;hX&gt;, &lt;/hX&gt;: X level header, &lt;p&gt;,&lt;/p&gt; : paragrph
  * &lt;table&gt;&lt;/table&gt;: table
    * &lt;tr&gt;&lt;/tr&gt;: demarcate begining and end of row within table
    * &lt;td&gt;&lt;/td&gt;: emarcate begining and end of a column within a row within table 
  * &lt;form&gt;&lt;/form&gt; emarcate begining and end of row within table, &lt;div&gt;&lt;/div&gt;: demarcate begining and end of HTML page division, &lt;input name=X, type = Y/&gt; : field in the HTML form, X is a unique identifier, Y is data type.
  * &lt;a herf=X&gt;&lt;/a&gt;: hyperlink, &lt;img src = X.../&gt; image
  * &lt;!DOCTYPE html&gt;: specify to HTML5 \(version\)
    * first line
  * &lt;body&gt;&lt;/body&gt;, &lt;div&gt;&lt;/div&gt;
  * &lt;link&gt; link CSS files
  * &lt;script&gt; Link JavaScript scripts
* Attributes
  * action
  * enctype
  * mthod GET?POST
* Image and Unicode

#### CSS - Cascading Style Sheets

* stylesheet language used to describe the presentation of a document written in HTML or XML
* Library : Bootstrap
* ```css
  body   /* selector */
  {
      /*declaration*/

      background-color: blue; 
  }
  ```
* common properties
  * border: style color width
  * background-color: \[keyword \| \# &lt;6-digit hex&gt;\]
  * color: \[keyword \| \#&lt;6-digit hex&gt;\]
  * font-size \[absolute size\|relative size\]
  * font-family: \[font name \|generic name\]
  * text-align: \[left\|right \|center\|justify\]
* selector
  * tag selector: apply to all elements with a given HTML tag
  * ID selector: \# will apply only to an HTML tag with a unique identifier
* Useful Library - **BootStrap**

#### JSON\( JavaScript Object Notation\)

* Store and Transport data, easily convert to javascript objects \(vice versa\)
* key, value pairs
* ```json
  “students”:[
             {“firstName”:”John”,
              “lastName”:”Smith”,
              “Age”:”15”
              “favouriteColour”:”Red”
             },
             {“firstName”:”Donna”,
              “lastName”:”Doe”,
              “Age”:”14”
              “favouriteColour”:”Green”
             },
             {“firstName”:”Thomas”,
              “lastName”:”Oliver”,
              “Age”:”12”
              “favouriteColour”:”Purple”
  }, ] 
  }
  // a Json Array
  ```

### Java Script

* run on the client side
  * Python, PHP runs on the server side
* including with HTML\(&lt;script&gt; tag\)
  * event &lt;button onclick = "&lt;func&gt;&gt;&lt;/button&gt;
* **event**
* a response to user intraction
  * .onsubmit
* **event handlers **- which are callback functions that response to HTML events
* Document Object Model**\(DOM\) **- contains the entire webpage
  * object can contain various fields, even those with other objects
  * properties can be reset/called easily
    * innerHTML: hold HTML inside a set of tags
    * nodeName: name of an HTML or element attribute
    * id: id attribute in HTML
    * parentNode: reference to level up node
    * childNodes: array of references to children
    * attributes: An array of attributes of an HTML element
    * style: encapsulating the CSS/HTML styling of an element
  * methods
    * getElementById\(&lt;id&gt;\)
    * getElementByTagName\(&lt;tag&gt;\)
    * appendChild\(&lt;node&gt;\): add the given node to DOM below this point
    * remove\(&lt;node&gt;\): Remove the specific child node from DOM
* JSON
* Ajax\( Asynchronous Javascript and XML\) - dynamically allocate a webpage

  * XMLHTTPRequest - make use of this speical JS object
    * readystate Porperty: change from 0 to 4
    * status: will be 200 when successful
    * onreadystatechange: define an onreadystatechange behavior for it - function will run when request is complete
  * make asynchronous request using open\(\) to define the method and use send\(\) to send it \(slightly different in JQuery\)

##### Basic Grammar

* if else if else switch ?:
* for \(key in Obj\) {}
* function keyword
  * anonymous functions
* Arrays - viable length \[\]
  * pop, size, push, shift
* Objects {name: value, ... }
  * Obj\[name\] to access
  * .map\(lambda\):
* String
  * * append

#### JQuery

* Most popular JavaScript library - called by "$" 
  * $\(&lt;id&gt;\).&lt;property name&gt;\(&lt;before&gt;&lt;after&gt;\)
* based on the DOM model - provide shorter/simply alternative to use

### Flask

* **web framework**, abstrcts the minutia of Python,s syntax and provides helper functions \(others like Django, Pyramid\)
* from flask Import Flask, app = Flask\(\_\_name\_\_\)
* data can be passed in via URLs, akin to HTTP GET, via HTML forms, as with HTTP POST
* use decorator\(app.route\) to associate a particular function with a particular URL
* useful functions
  * url\_for\(\)
  * redirect\(\)
  * session\(\)
  * render\_template\(\)
* export FLASK_APP = application.py, export FLASK\_DEBUG = 1, flask run_
* Jinjia
  * Python Template Engine



