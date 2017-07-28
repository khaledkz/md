 - [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item


def foo():
    if not bar:
       
        
        
     I think you should use an
    

 



 ## **What is node js** 
 ###   A JavaScript runtime environment running Google Chrome’s V8 engine*
 
 ### Runs over the command line  
 
 ### Designed for high concurrency
  #### Without threads or new processes
 ### Never blocks, not even for I/O
 
 ### Uses the CommonJS framework
   Making it a little closer to a real OO language
  
  
  
## Concurrency: The Event Loop
 
 ### Instead of threads Node uses an event loop with a stack
 
 ### Alleviates overhead of context switching
 
 
 
 
 
 
 ## Event Loop Example 
 
 ### Request for “index.html” comes in
 ### Stack unwinds and ev_loop goes to sleep
 ### File loads from disk and is sent to the client


 ### Non Blocking I/O

### Servers do nothing but I/O
### Scripts waiting on I/O requests degrades performance
### To avoid blocking, Node makes use of the event driven nature of JS by attaching callbacks to I/O requests
### Scripts waiting on I/O waste no space because they get popped off the stack when their non-I/O related code finishes executing


I/O Example


### Consistancy 

### Use of JS on both the client and server-side should remove need to “context switch”
### Client-side JS makes heavy use of the DOM, no access to files/databases
### Server-side JS deals mostly in files/databases, no DOM
### JS Dom project for Node works for simple tasks, but not much else


 
## Node Js VS Apache

1. It's fast
1. It can handle tons of concurrent requests
1. It's written in JavaScript (which means you can use the same code server side and client side)

Platform | Number of request per second
------------ | -------------
PHP ( via Apache) | 3187,27
Static ( via Apache ) | 2966,51
Node.js |  5569,30


`<addr>` element here instead.
 return True
