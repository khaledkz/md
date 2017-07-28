

## **What is node js** 
 ####   A JavaScript runtime environment running Google Chrome’s V8 engine*
 
 Node.js is the leading tool for creating server applications in JavaScript, the world’s most popular programming language. Offering the functionality of both a web server and an application server, Node.js is now considered a key tool for all kinds of microservices‑based development and delivery. 
 
 Node.js is single‑threaded and uses nonblocking I/O, allowing it to scale and support tens of thousands of concurrent operations. It shares these architectural characteristics
 
 Runs over the command line  
 
  Designed for high concurrency
   Without threads or new processes
  Never blocks, not even for I/O
 
  Uses the CommonJS framework
   Making it a little closer to a real OO language
  
  
  
## Concurrency: The Event Loop
 
  Instead of threads Node uses an event loop with a stack
 
  Alleviates overhead of context switching
 
 
 
 
 
 
 ## Event Loop Example 
 
   Request for “index.html” comes in
   Stack unwinds and ev_loop goes to sleep
   File loads from disk and is sent to the client


 ### Non Blocking I/O

  Servers do nothing but I/O
  Scripts waiting on I/O requests degrades performance
   To avoid blocking, Node makes use of the event driven nature of JS by attaching callbacks to I/O requests
  Scripts waiting on I/O waste no space because they get popped off the stack when their non-I/O related code finishes executing


I/O Example


### Consistancy 

  Use of JS on both the client and server-side should remove need to “context switch”
  Client-side JS makes heavy use of the DOM, no access to files/databases
  Server-side JS deals mostly in files/databases, no DOM
 JS Dom project for Node works for simple tasks, but not much else


 
## Node Js VS Apache

1. It's fast
1. It can handle tons of concurrent requests
1. It's written in JavaScript (which means you can use the same code server side and client side)

Platform | Number of request per second
------------ | -------------
PHP ( via Apache) | 3187,27
Static ( via Apache ) | 2966,51
Node.js |  5569,30


#### Node.js is a great tool for creating and running application logic that produces the core, variable content for your web page. But it’s not so great for serving static content – images and JavaScript files, for example – or load balancing across multiple servers.

##### To get the most out of Node.js, you need to cache static content, to proxy and load balance among multiple application servers, and to manage port contention between clients, Node.js, and helpers, such as servers running Socket.IO. NGINX can be used for all of these purposes, making it a great tool for Node.js performance tuning.


1. Implement a reverse proxy server
1. Cache static files
1. Load balance traffic across multiple servers
1. Proxy WebSocket connections
1. Implement SSL/TLS and HTTP/2


## 1 – Implement a Reverse Proxy Server

We at NGINX, Inc. are always a bit horrified when we see application servers directly exposed to incoming Internet traffic, used at the core of high‑performance sites. This includes many WordPress‑based sites, for example, as well as Node.js sites.

Node.js, to a greater extent than most application servers, is designed for scalability, and its web server side can handle a lot of Internet traffic reasonably well. But web serving is not the raison d’etre for Node.js – not what it was really built to do.

If you have a high‑traffic site, the first step in increasing application performance is to put a reverse proxy server in front of your Node.js server. This protects the Node.js server from direct exposure to Internet traffic and allows you a great deal of flexibility in using multiple application servers, in load balancing across the servers, and in caching content.

There are specific advantages to using NGINX as a Node.js reverse proxy server, including:

Simplifying privilege handling and port assignments
More efficiently serving static images (see next tip)
Managing Node.js crashes successfully
Mitigating DoS attacks




##  2 – Cache Static Files

As usage of a Node.js‑based site grows, the server will start to show the strain. There are two things you want to do at this point:

Get the most out of the Node.js server
Make it easy to add application servers and load balance among them
This is actually easy to do. Begin by implementing NGINX as a reverse proxy server, as described in the previous tip. This makes it easy to implement caching, load balancing (when you have multiple Node.js servers), and more.


##  3 – Implement a Node.js Load Balancer

The real key to high – that is, nearly unlimited – performance for Node.js applications is to run multiple application servers and balance loads across all of them.

Node.js load balancing can be particularly tricky because Node.js enables a high level of interaction between JavaScript code running in the web browser and JavaScript code running on the Node.js application server, with JSON objects as the medium of data exchange. This implies that a given client session runs continually on a specific application server, and session persistence is inherently difficult to achieve with multiple application servers.


##  4 – Proxy WebSocket Connections

HTTP, in all versions, is designed for “pull” communications, where the client requests files from the server. WebSocket is a tool to enable “push” and “push/pull” communications, where the server can proactively send files that the client hasn’t requested.

The WebSocket protocol makes it easier to support more robust interaction between client and server while reducing the amount of data transferred and minimizing latency. When needed, a full‑duplex connection, with client and server both initiating and receiving requests as needed, is achievable.

WebSocket protocol has a robust JavaScript interface and as such is a natural fit for Node.js as the application server – and, for web applications with moderate transaction volumes, as the web server as well. When transaction volumes rise, it makes sense to insert NGINX between clients and the Node.js web server, using NGINX or NGINX Plus to cache static files and to load balance among multiple application servers.


##  5 – Implement SSL/TLS and HTTP/2


More and more sites are using SSL/TLS to secure all user interaction on the site. It’s your decision whether and when to make this move, but if and when you do, NGINX supports the transition in two ways:

1-You can terminate an SSL/TLS connection to the client in NGINX, once you’ve set up NGINX as a reverse proxy. The Node.js server sends and receives unencrypted requests and content back and forth with the NGINX reverse proxy server.

2-Early indications are that using HTTP/2, the new version of the HTTP protocol, may largely or completely offset the performance penalty that is otherwise imposed by the use of SSL/TLS. NGINX supports HTTP/2 and you can terminate HTTP/2 along with SSL/TLS, again eliminating any need for changes in the Node.js application server(s).

 
