These are my notes on **API and Web Service Introduction** by Nate Ross at [udemy.com](https://www.udemy.com/api-and-web-service-introduction/learn/v4/overview).

### Section 2: API

#### What is an API?

**An API is where you tell a program you don't own to run.**

A stands for application, P for programming, and I for interface.

You can think of an API conversely. The interface (I) is where you tell a program (P) to run in an application (A).

A simple example of this is Google. The browser or webpage is the interface. The program is the search function. The application is Google.

When referring to APIs, people usually mean ones that exist where the server is located.

An example of this is using Google maps in your own website. You did not write the Google maps program. Google did. But by using the Google maps API, you can use their program in your own applications.

These kinds of APIs are created because they are not expensive or difficult to make. The second is because accessing these APIs are platform independent. You can use Python, a browser, or another method to use an API.

If an API has a "sandbox" mode on an applications' website, you can test an applications' API and practice using it.

#### API Details

3 things happen in every API transaction.

1. A request is made for something to be done.

2. A program is run to complete that request.

3. The program sends back a response.

A simple example of this is searching for a term on Google.

Typing the term and pressing search sends a request to Google to search for the term, then return those results in the form of a web page.

In more detail, the url is the interface that makes the request to the Google computer where the search program exists. `www.google.com` means Google computer. The program is located in a folder in the Google computer called "/search." The folder is appended to the end of the url, like `www.google.com/search`. The search term is added in the form of a parameter. The start of parameters is `?`. The first parameter is `q` for query. If we search for tuna, the url looks like this: `www.google.com/search?q=tuna`. Typing that in the browser will show results for "tuna."

A more complex and proper example of an API is using eBay's Order API. This is not their web page, but a set of functions and methods that let you make orders through their order program. You can test it on in sandbox mode at `www.apix.sandbox.ebay.com`.

#### API Mashup

This is not a real term, but one used by the course instructor to explain a concept. "API Mashup" is when you use several APIs to make your own API. An example of this would be a travel website using the APIs of several airline companies to find the flight and price availability for the flight you search for. Using several APIs can be powerful.

### Section 3: Web Service

#### What is a Web Service?

**A web service is an API that uses the internet.** Not all APIs use the web.

Web services use:
- XML or JSON to format data over the internet
- REST, SOAP, or XML/RPC protocols to transfer that data

### Section 4: Introduction to HTTP

HTTP stands for Hyptertext Transfer Protocol. 

Regular text does nothing. An example is www.google.com. Hypertext means text that can go to somewhere else. Your browser will automatically add http// or https// in front of the regular text.

HTTP has four parts.

1) Start line - starts the program and tells it what to do

2) Headers - provides additional information other than the start line

3) Blank line - nothing

4) Body - where you send information

Only the start line is mandatory. Both requests and responses are done with HTTP.

Here are some things that are included or happen in the four different parts of HTTP at a glance. These will be discussed in detail in later sections.

|HTTP|REQUEST|RESPONSE|
|:-:|:-:|:-:|
|START LINE|http version, method, folders & params|http version, status code|
|HEADERS|host url, token|cookies|
|BLANK LINE|   |   |
|BODY|username, pw|HTML page|   |

You can add as many or as few lines to the headers section as you want.

#### HTTP Start Line

Let's examine what the start line includes for both a HTTP request and HTTP response.

||Request|Response|
|:-:|:-:|:-:|
|Name|Start Line, Request Line|Start Line, Response Line, Status Line|
|HTTP Version|HTTP/1.1|HTTP/1.1|
|Method|GET, POST, PUT, DELETE, etc.|No|
|API Program Folder Location|Yes (example: /search)|No|
|Parameters|Yes (example: ?q=tuna)|No|
|Status Code|No|Yes(example: 200 OK)|
|Format|Method(space)API Program Folder Location+Parameters(space)HTTP Version|HTTP Version + Status Code|
|Example|GET /search?q=tuna HTTP/1.1|HTTP/1.1 200 OK|

**Idempotence** is an important HTTP concept. It means you can do something as many time as you want and the result stays the same. It is an action that is safe to repeat.

It's important to know what API methods are idempotent.

|Method|Idempotent? (safe to repeat)|
|:-:|:-:|
|GET|Yes|
|POST|No|
|PUT|Yes|
|DELETE|Yes|

Calling the PUT method multiple times can have different results by creating new resources.

#### HTTP Headers

HTTP headers provide required information about the request or response, or about the object sent in the message body. These are different kinds of headers for requests or responses.

You can see a list of header fields on [Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields). Some commons ones include:

- Host. The domain name of the server, like www.google.com
- Accept-Language. - List of acceptable languages for response. 'de' would return responses in German.
- Cache-Control. Determines whether or not an object may be cached and for how long.

#### HTTP Blank Line

The purpose of the blank line is to show where the headers finish and where the body begins.

#### HTTP Body

The body is what contains content. It can be an image, an HTML web page, a video, data, etc. It can be content you're sending to an API if you're making a request or it can be content that comes from an API in a reponse.

The Content-Type header determines what type of content is being sent or received in the body.

Here are some different [content types](https://en.wikipedia.org/wiki/Media_type):

- application/javascript
- application/json
- application/xml
- application/pdf
- application/ld+json
- text/css
- text/html
- text/xml
- text/csv
- image/png
- image/jpeg
- image/gif

They are organized by a type then a subtype like this: `type "/" [tree "."] subtype ["+" suffix] *[";" parameter]`.

JSON and XML are two content types for sending or receiving data through APIs.

### XML

XML stands for e**X**tensible **M*arkup **L**anguage.

It is a content type. The HTTP header line is `Content-Type: application/xml`.

XML holds data sent to or received from the API. The XML is in the body.

XML is similar to HTML in that they both use tags <>. However, the XML is "extensible" in that you can customize the tags to say whatever you want. For example, "button" in HTML will create a clickable button with default CSS styles, while "button" in XML just means a tag with the value of "button." You cannot change the semantic value of an HTML tag, but you can with XML.

Here is some example XML for a hypothetical pizza company's API. They require data in the form of XML.

```xml
<Pizza>
  <Size>Small</Size>
  <Toppings>
    <Topping>Onions</Topping>
    <Topping>Mushrooms</Topping>
  </Toppings>
</Pizza>
```

If you save this as an XML file you can load it and view it in your browser. You will see the markup above with an informational header `<?xml version = "1.0"?>`.

XML was created by the [World Wide Web Consortium](https://www.w3.org/), more commonly knows as W3.

There are sub-standards of XML. One is XPath, which lets you focus on a particular part of XML. For example, the toppings in the pizza XML. XQuery is similar. They are not commonly used. XML Schema, or XSD, tells you how your XML should be structured.

XSD is important for security. If you do not follow the guidelines set by XSD you will receive an error message. Here's an example:

```xsd
<?xml version="1.0"?>
<xs:schema xmlns:xs="https://www.w3.org/2001/XMLSchema">
  
  <xs:element name="brightstar">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="name" type="xs:string"/>
        <xs:element name="magnitude" type="xs:decimal"/>
        <xs:element name="distance" type="xs:integer"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

The XML Schema above shows that the first tag should be "brightstar," complexType means those elements should be nested in "brightstar", sequence means those nested elements should be in that order, and type means the info in those XML tags must be those types.

### JSON

JSON stands for **J**ava**S**cript **O**bject **N**otation.

It holds data like XML. It is the object data structure of JavaScript. The header line is `Content-Type: application/json`. JSON goes in the HTTP body.

It uses "key" : "value" pairs (example "Size" : "Small"). Douglas Crockford created JSON.

A JSON version of the XML pizza above looks like this:

```json
{ "Pizza" : [
  {"Size" : "Small",
   "Toppings" : ["Onions", "Mushrooms"]
  }
]}
```

JSON is much more widely used because it's easier to write and the data is more lightweight. JSON also has a schema like XML but you do not really need to deal with it to use JSON.

Here's a quick comparison between XML and JSON.

||XML|JSON|
|:-:|:-:|:-:|
|Powerful|Yes|No|
|Simple|No|Yes|
|Developed|1997|2001|
|Popularity|Down|Up|

JSON is powerful but XML is more powerful due to it's tag customizability and use of things like schemas. JSON is much simpler however. JSON is much more popular and becoming more popular.

It may not be necessary to know how to deal with XML, but it's important to know about it and the differences between XML and JSON.

### What is SOAP and REST?

SOAP and REST are ways to form the HTTP request and response. REST is being used much more than SOAP. REST is much simpler.

### What is SOAP?

SOAP stands for **S**imple **O**bject **A**ccess **P**rotocol. "Simple" is a bit of a misnomer and subjective. The "Object" that is being accessed is a web service/API. "Protocol" means rules/ways to do something. So SOAP is a way to access a web service by following certain rules to form the HTTP request/response.

Every web services that uses SOAP uses a WSDL (**W**eb **S**ervices **D**escription **L**anguage). It is an XML-based language that describes the functionality offered by a web service. It also shows the relevant XML syntax to use the web service.

A SOAP HTTP request is formed as follows:

1) Start line - POST WSDL HTTP Version. The "POST" is not actually used, it is just a placeholder. The WSDL is the WSDL location.
2) Header line - Content-Type: text/xml.
3) Blank line
4) Body - XML envelope formed using WSDL.

SOAP was created by W3C.

### What is REST?

REST is the modern way of accessing a web service by following certain rules to form the HTTP request/response. While SOAP does not use any API methods (it has POST as a placeholder), you can use any for REST. For example, GET, POST, PUT, and DELETE. 

REST can leverages _caches_. A cache is a temporary, local storage of web documents such as HTML pages and images. Using the GET method in REST will check if the data you want matches the data you already have. If it does it will use the web files in your cache and reduce server lag.

REST is _stateless_. "Stateless" in this context means the state of the server you are interacting with in your API request. If the server is not running (the state of not running), the REST API request will wait until the server is, complete the API request, and then send back the response. SOAP in comparison will not do this.

REST stands for **RE**presentation **S**tate **T**ransfer.

If you make a GET request, you are not actually getting the data in the server back, but a copy of it (a representation of the state of the data).

REST is easier to work with than SOAP with because you don't have to follow a WSDL and you can tell the program what to do with a simple method (GET, POST, etc.). REST can also send data in any format while SOAP must use XML. Thus REST is more flexible and the preferred modern way of creating or consuming APIs.

### OAuth Introduction

These are three topics to understand in regards to web service security.

1) HTTPS

HTTPS is a HTTP protocol that is encrypted. The "S" stands for "secure." Anything with sensitive information should always be done with HTTPS, such as online payments.

2) Authorization Server vs Resource Server

A server is a program which manages access to a service in a network. It is **not** a computer. A server exists on a computer. Multiple servers can exist on the same computer. Sometimes multiple instances of the same server exists on the same computer for performance reasons (i.e. reducing server lag).

An authorization server checks to see if you're allowed to run the program you request. It is specifically made for security. If the authorization is made the request is sent to the resource server, which runs the requested program.

An example of this is ordering a product on ebay. First you make an order on your browser which is sent over HTTPS. The request is first sent to the authorization server, then to the resource server which does the ordering.

It's also possible for the request to go to the resource server first, which then checks the authorization server before running any programs.

Sometimes the authorization server and resource server exist on different computers.

3) Permissions

Permissions is a way for programs/applications to make API requests for you.

An example would be the Google Maps app asking for permission to access your phone's location, then using that info to make an API call to a directions program on a Google computer.

It is important that the app only accesses your location and no other info. This limited access is called _scope_, in this case the phone's location.

**OAuth** is a way to give someone else permission to do something, or "delegated access." In the example above, the Google Maps app will ask your phone for the authority to access your phone, and your phone will then ask the user for permission. OAuth will allow limited access by asking for only permission to access the phone's location instead of all of the phone's information. Through OAuth, an access token is granted to Google Maps and an API call is made for directions. Google Maps can continuously use this same token for future API calls.

OAuth has two versions. 1.0 came out in 2007 and 2.0 came out in 2012. 1.0 is deprecated and everyone uses 2.0.

There are five ways to do OAuth which are called OAuth flows.

1) **Authorization Code/Access Token - like in the example above, authorization for something is granted via a code.**

2) **Refresh Token - when another token is granted when the previously granted token expires**

3) Implicit Grant - this is insecure because it is done on the front end and people can intercept it

4) Resource Owner - this can be used when you own the API

5) Client Credentials - this is used machine to machine

You will like only use OAuth methods 1 and 2.