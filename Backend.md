# Backend Development
Sometimes called the server side, the backend of your application manages your web application's overall functionality. When your user interacts with the frontend, the interaction sends a request to the backend in HTTP format. The backend processes the request and returns a response.

When your backend processes a request, it usually interacts with the following:
- Database servers to retrieve or modify relevant data
- Microservices that perform a subset of the tasks your user requested
- Third-party APIs to gather additional information or perform additional functions
# Port
A port in computing is a communication endpoint used for sending and receiving data between devices, processes, or applications.

# Route
Routes define the endpoints your backend exposes. Each route corresponds to a specific URL and HTTP method (like GET, POST, PUT, DELETE).
* Routing refers to determining how an application responds to a client request to a particular endpoint, which is a URI (or path) and a specific HTTP request method (GET, POST, and so on).
# Controller
Controllers contain the logic of what to do when a route is hit — like fetching from DB, updating, or sending back a response.

# Middleware
Middleware are functions that run before the controller — they can modify the request/response, validate data, check auth, etc.

# Model
Models define how your data looks and interacts with the database (usually MongoDB with Mongoose in Node).

# Access Token
Grants short-term access to protected resources (APIs, routes).

# Referesh Token
Used to get a new Access Token when it expires.

# Secure cookies
A cookie (also known as a web cookie or browser cookie) is a small piece of data a server sends to a user's web browser. The browser may store cookies, create new cookies, modify existing ones, and send them back to the same server with later requests.

# Mongodb
## What is ORM?
ORM is Object Relational Mapping, basically a technique to query or perform CRUD (Create, Read, Update, Delete) operations to the database, mainly RDBMS (Relational Databases), using an object-oriented paradigm.

* With the help of ORM, you don’t actually need to use SQL at all. You can directly interact with the database and perform queries in the same language you are using for your back-end code!

## What is ODM?
ODM is Object Document Mapping. It is like an ORM for non-relational databases or distributed databases such as MongoDB, i.e., mapping an object model and NoSQL database (document databases, graph database, etc.).


# Http crash course
metadata-key value pair sent along request and response
* request-headers-> client
* response-headers-> server
* representational-headers-> encoding/compression
* payload-headers-> data

# Http methods
* GET
* POST
* PUT
* DELETE 
* TRACE
* PATCH
* OPTIONS

# Http status  
* 1xx information
* 2xx success
* 3xx redirection
* 4xx client errors
* 5xx server errors



# Nodejs
nodejs is wrapper around javascript v8 engine.


# Express

Express is a routing and middleware web framework that has minimal functionality of its own: An Express application is essentially a series of middleware function calls.

## Routing
the routing methods can have more than one callback function as arguments. With multiple callback functions, it is important to provide next as an argument to the callback function and then call next() within the body of the function to hand off control to the next callback.

### app.route()
You can create chainable route handlers for a route path by using app.route().ecause the path is specified at a single location, creating modular routes is helpful, as is reducing redundancy and typos. 

```javascript
app.route('/book')
  .get((req, res) => {
    res.send('Get a random book')
  })
  .post((req, res) => {
    res.send('Add a book')
  })
  .put((req, res) => {
    res.send('Update the book')
  })
```

### express router
Use the express.Router class to create modular, mountable route handlers. A Router instance is a complete middleware and routing system; for this reason, it is often referred to as a “mini-app”.
```javascript
const express = require('express')
const router = express.Router()

// middleware that is specific to this router
const timeLog = (req, res, next) => {
  console.log('Time: ', Date.now())
  next()
}
router.use(timeLog)

// define the home page route
router.get('/', (req, res) => {
  res.send('Birds home page')
})
// define the about route
router.get('/about', (req, res) => {
  res.send('About birds')
})

module.exports = router
```

## middleware
Middleware functions are functions that have access to the request object (req), the response object (res), and the next function in the application’s request-response cycle.
* The next function is a function in the Express router which, when invoked, executes the middleware succeeding the current middleware.
Middleware functions can perform the following tasks:
    * Execute any code.
    * Make changes to the request and the response objects.
    * End the request-response cycle.
    * Call the next middleware in the stack.
If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.

