These are my notes on **API and Web Service Introduction** by Nate Ross at [udemy.com](https://www.udemy.com/api-and-web-service-introduction/learn/v4/overview).

### Section 2: API

#### What is an API?

**An API is where you tell a program you don't own to run.**

A stands for application, P for programming, and I for interface.

You can think of an API conversely. The interface (I) is where you tell a program (P) to run in an application (A).

A simple example of this is Google. The browser or webpage is the interface. The program is the search function. The application is Google.

When referring to APIs, people usually mean ones that exist where the server is located.

An example of this is using Google maps in your own website. You did not write the Google maps program. Google did. But by using the Google maps API, you can use their program in your own applications.

These kinds of APIs are created because they are not expensive or difficult to make. The second is because accessing these APIs are platform independent. You can use Python, or browser, or another method to use an API.

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

HTTP headers provide required information about the request or response, or about the object sent in the mssage body. These are different kinds of headers for requests or responses.

You can see a list of header fields on [Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields). Some commons ones include:

- Host. The domain name of the server, like www.google.com
- Accept-Language. - List of acceptable languages for response. 'de' would return responses in German.
- Cache-Control. Determines whether or not an object may be cachedand for how long.

#### HTTP Blank Line

The purpose of the blank line is to show where the headers finish and where the body begins.

