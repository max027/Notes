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


    
