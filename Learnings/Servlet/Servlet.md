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
	- Attributes to pass data between filters, servlets, etc..
	- Dispatcher for server-side routing

### HTTPServlerResponse
- Outgoing HTTP response
- Container uses it to convert output into raw HTTP
- It provides
	- body to write response
	- set status code
	- set response headers
	- redirect the response
	- cookie management




| Redirect                                                                                                                                                                                   | Request Dispatch                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| to navigate from one resource to another(from servlet to JSP, servlet, ...)                                                                                                                | to navigate from one resource to another(from servlet to JSP, servlet, ...)<br>                                             |
| when servlet sends a 302 HTTP  response to browser with location,<br>then a new HTTP request is created to the location.<br>thus now it has 2 request and 2 response with their own-cycle. | The server internally forwards the request to another resource. <br>Everything is handled inside one request response cycle |
| Best for external resources                                                                                                                                                                | Browser URL does not change                                                                                                 |
|                                                                                                                                                                                            | Happens fully inside server memory                                                                                          |
| when redirecting to another domain                                                                                                                                                         | returning a view (JSP) after processing a request                                                                           |
| Avoiding on re-submission on browser refresh                                                                                                                                               | changing resource inside the same app                                                                                       |

### Web.xml
- The deployment descriptor for a java web application
- It tells servlet container how to:
	- map URLs to servlets
	- configure initialization parameters
	- define filters, listeners and welcome page
	- control app behavior without touching code
### URL mapping
- Each servlet has  
	- a name
	- class implementation
	- one or more URL patterns
- When a request hits the server, the container
	- reads the URL path
	- matches it to a pattern
	- instantiates or reuses the mapped servlet class
	- calls its service() -> doGet()/doPost()


## Servlet types

### By protocol
#### Generic servlet
- An abstract class
- Implements servlet and ServletConfig
- Helps in creating servlets that can handle any type of protocol
- ==rarely used today==

#### HTTP servlet
- It extends GenericServlet
- Provides methods specifically for HTTP requests.



### By role in application

#### Controller servlet
- It is responsible for receiving request , interacting with business logic and deciding which view shod be displayed next.

#### Utility/ Filter Servlets
- Technically a HTTPServlet Used purely for background processing before or after the main controller executes.
- This function is often handled by filter class for tasks like logging, authentication, compression, character encoding.


## Servlet config
- An interface used by web container to pass initialization information to a specific servlet during its initialization phase.
	- It allows a developer to define servlet-specific initialization parameters externally ( in web.xml ) for each and every unique servlet.
- **External Configuration (Decoupling)**
	- It decouples configuration values from the Java code. If a parameter needs to change (e.g., the name of a log file, the number of database connections for that specific servlet), you only need to update the web.xml file and redeploy, not recompile the Java class.

-  **Setting Servlet-Specific Parameters**
	- It provides a way to assign unique, distinct parameter values to different Servlets, even if they share the same class file.
		Example: You have two Servlets using the same EmailSenderServlet class, but one needs to use support@company.com and the other needs to use sales@company.com as its sender address. You would define a unique initialization parameter for each one.
- It can be used to programmatically get the logical name assigned to the Servlet instance in the deployment descriptor.


## Servlet content
- It is often used to refer to the ServletContext object
- It can store any type of object
**ServletContext**
- It is an interface that defines a set of methods a servlet uses to communicate with its servlet container and reset of the application.
- **Single instance**
	- only one object of ServletContent is created by the web container when deployed.
	- it is shared among all servlets, JSP,... For a common ground for sharing
- **Sharing**
	- an object can be stored the Servlet content for some other to access
	- setAttribute(), getAttribute(), removeAttribute() 
- **container communication and resource access**
	- provides utility methods to interact with server environment
		- log()
		- getRealPath()
		- RequestDispatcher
		- getServerinfo()



| **Feature**       | **ServletContext**                                         | **ServletConfig**                                                 |
| ----------------- | ---------------------------------------------------------- | ----------------------------------------------------------------- |
| **Scope**         | **Application-wide** (Global)                              | **Servlet-specific** (Local)                                      |
| **Instance**      | **One** per web application                                | **One** per servlet instance                                      |
| **Purpose**       | Share resources and information across **all** components. | Pass **initialization parameters** to a single, specific servlet. |
| **`web.xml` Tag** | `<context-param>` (inside `<web-app>`)                     | `<init-param>` (inside `<servlet>`)                               |

|Feature|`<init-param>`|`<context-param>`|
|---|---|---|
|Scope|Single servlet|Whole app|
|Access via|`ServletConfig`|`ServletContext`|
|Lifetime|Servlet’s lifetime|App lifetime|
|Sharing|Not shared|Shared across servlets|
|Common usage|Local settings (per servlet)|Global config values|

## Events and Listeners

## Events
- These are signals the container sends when something changes in the we app's lifecycle
- These are handles by listeners

|Event Type|Triggered When|Listener Interface|
|---|---|---|
|**Context Lifecycle Events**|App starts / stops|`ServletContextListener`|
|**Context Attribute Events**|Attributes added/removed in `ServletContext`|`ServletContextAttributeListener`|
|**Session Lifecycle Events**|Session created/destroyed|`HttpSessionListener`|
|**Session Attribute Events**|Attributes added/removed in session|`HttpSessionAttributeListener`|
|**Request Lifecycle Events**|New HTTP request received or completed|`ServletRequestListener`|
|**Request Attribute Events**|Attributes added/removed in request|`ServletRequestAttributeListener`|
### Listener
- A listener class is defined as an implementation of a listener interface.

| Listener                          | Monitors                     | Typical Usage              |
| --------------------------------- | ---------------------------- | -------------------------- |
| `ServletContextListener`          | App start/stop               | Init resources, clean up   |
| `ServletContextAttributeListener` | App-level attribute changes  | Debugging, dynamic configs |
| `HttpSessionListener`             | Session create/destroy       | Track users, cleanup       |
| `HttpSessionAttributeListener`    | Session attribute add/remove | Audit session data         |
| `ServletRequestListener`          | Request lifecycle            | Logging, tracing           |
| `ServletRequestAttributeListener` | Request attribute changes    | Debugging, filters         |






## Cookies 
Small client-side storage
It is about 4KB
For a single website there can be20-180 cookies that can be stored
- HTTP is stateless, server does not remember who you are between requests
- It is a small piece of data stored in the user's browser
- When a servlet sends a response it can send a cookie, from then the browser automatically sends that cookie back on every future request to the same domain
- Good for only small data
- It is visible to users 
- Can be disabled in browser
- Since it is sent with every request  it increases bandwidth.

Cookie storage
- When a set-cookie header is found in the response
- Browser
	- creates a file under the bowser and store as attribute int its own local storage


## Session 
Server side state management
- A session lives on server and holds data tied to a specific user
- The browser holds the session id in a cookie and sends it in every request. 
- It is secure and ideal for authentication
- Transparent to client
- But consumes server memory for each user
- Hard to maintain in distributed systems
- Hijacking is possible if session id is not protected
