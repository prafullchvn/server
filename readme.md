# http server

This package can be used to create the server to listen to incoming requests.

## Installation

`npm install --save https://github.com/prafullchvn/server.git`


## Usage

### **startServer**

In order to use this package, you need to import the createServer method.

`const {startServer} = require('server');`

**Syntax of startServer**

`startServer(port,router[,directory])`

### **Router**

It is class which is used to create router for server. Basically this maps each route to its own handler. This class also provides method to add handler and middleware. You can add default handler if none of the handler are able to handle route.

It is suggested to add default function for 404 error and to handle the static files or other resources served from rooDir.

 Each handler takes 3 parameters, `request`, `response` and `next`. Here request and response are object. next is method which can be used to call the next handler if current handler can not execute the request. *next is not available to middleware handlers*

Syntax 

`const router = new Router()`

Method

- **Add Middleware**

  Add the middleware handler. These handler will be executed before any request to server is handled.

  *Syntax*
  
  `addMiddleware(handler)`
  
  *Input*

  handler : \<function\>

  *Output*

  undefined

- Register get route

  You can register the handler for route to handle GET request using this method. This method takes list of handlers.

  *Syntax*
  
  `get(handlers)`


- Register post route

  You can register the handler for route to handle POST request using this method. This method takes list of handlers.

  *Syntax*
  
  `post(handlers)`
  

- Add default handler

  These function will be executed if none of the route is able to handle the current request.

  **Syntax**

  `addDefaultHandler(handler)`


### Response

  Response entity have following method to send the various types of response.
  All of these methods take the string or buffer as input.

- res.send(content)

  This method is used to send the plain text input. 

- res.sendHTML(htmlCod)

  This method is used to send the html content as response.

- res.sendFile(fileContent)

  This method is used to send the fileContent of various types of file like images, audios as response.

Set the status code

You can set the status code of response explicitly. 

`response.statusCode = statusCode`

Add the header

You can add the header to response

`response.addHeader(field, value)`