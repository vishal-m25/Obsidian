- It is a java class
- Runs on server and handles HTTP request and response
- All servlets must implement ==**`Servlet`**== interface, which has lifecycle methods
- ==**`HttpServlet`**== provides functions like ==**`doGet()`**== and ==**`doPost()`**==


## Lifecycle
- The lifecycle is controller by the container it is deployed in.

When a request is mapped to a servlet 
- If instance does not exist
	- Loads servlet class
	- creates an instance.
	- initialize the instance
- Then container invokes the service method , passing the request and response object

With the help of listener objects the state of the servlet can be monitored.

## Web container
It is a server runtime that
- Listens for HTTP requests
- Converts them into java objects
- Maps the request to the correct servlet
- Invokes servlet code

### working
- Starts a HTTP listener
- Uses thread pool to handle request (has a acceptor thread that receives tasks and insert into queue)
- Parses HTTP request and converted into HttpServletRequest object (Initially in received as stream)
- Applies filter chain (authentication filter, logging filter, CORS filter)
- Dispatches to the correct servlet
- Manages servlet lifecycle
- Formats result into HTTP response and sends to client.


### HTTPServletRequest
- Created by container for each request
- It provides 
	- request data (URL, Method, Headers, cookies, body)
	- Session management (access or create new session objects), maintains state across multiple requests.
	- A

## Listener class
- A listener class is defined as an implementation of a listener interface.

|Object|Event|Listener Interface and Event Class|
|:--|:--|:--|
|Web context|Initialization and destruction|`javax.servlet.ServletContextListener` and `ServletContextEvent`|
|Web context|Attribute added, removed, or replaced|`javax.servlet.ServletContextAttributeListener` and `ServletContextAttributeEvent`|
|Session|Creation, invalidation, activation, passivation, and timeout|`javax.servlet.http.HttpSessionListener`, `javax.servlet.http.HttpSessionActivationListener`, and `HttpSessionEvent`|
|Session|Attribute added, removed, or replaced|`javax.servlet.http.HttpSessionAttributeListener` and `HttpSessionBindingEvent`|
|Request|A servlet request has started being processed by web components|`javax.servlet.ServletRequestListener` and `ServletRequestEvent`|
|Request|Attribute added, removed, or replaced|`javax.servlet.ServletRequestAttributeListener` and `ServletRequestAttributeEvent`|

