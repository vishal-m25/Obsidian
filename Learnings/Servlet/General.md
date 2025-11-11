
## Web application Architecture
- Describes how the components of the web application interact with eachother to process request, store data, and deliver response to users through web.

```pgsql
User (Browser)  →  Internet  →  Web Server  →  Application Server  →  Database
```

### Components
- Client
- Webserver
	- receives HTTP requests
	- decides where to send the request for processing
	- Ex: Apache, NGINX
- Application server
	- Contains business logic
	- processes request , communicates with database
	- Ex: Java, Python, Node.js, PHP
- Database server

### Types
| Architecture               | Description                                 | Example                               |
| -------------------------- | ------------------------------------------- | ------------------------------------- |
| **1-Tier**                 | UI, Logic, and Data on one system           | Local desktop software                |
| **2-Tier**                 | Client + Server DB                          | Small office apps                     |
| **3-Tier (Most Common)**   | Client + App Server + Database              | E-commerce, banking                   |
| **N-Tier / Microservices** | Logic split into small independent services | Large scalable apps (Netflix, Amazon) |

## keywords

### URL (Uniform Resource Locater)
- An address used to access a resource on the internet
- `https` → protocol
- `www.google.com` → domain name (server location
- `/search` → resource path
- `?q=java` → query parameter

### HTTP (HyperText Transfer Protocol)
- ==**Communication protocol**== 
- Used between browser and web server
- Works on port 80
- Uses request and response format

### Port Number
- It is used to identify a particular service running on a server.

### Server
- A computer/program that stores resources respond to client requests
- Types
	- Application server (contains logic and works dynamically)
		- Tomcat, GlassFish
	- Web server (delivers static content)
		- Apache, NGINX

### Container
- In java, it is a runtime environment that manages
	- servlet lifecycle
	- request/response
	- security, resource management

### Servlet
- A java class that handles HTTP requests and generates response
- Used to implement server-side logic
- ==**`doGet()`**== and ==**`doPost()`**== method logic are written


### JSP (JavaServer Pages)
- Used to cerate dynamic webpages which can embed java code inside HTML
- Mainly used for view/ UI layer
- Internally it gets converted to servlet when executed


### JSTL (JavaServer Pages Standard Tag library)
- Collection of pre-defined tags in JSP used to replace java code in JSP pages
```jsp
<c:forEach var="item" items="${productList}">
   ${item.name}
</c:forEach>
```


## Container 
- A runtime environment that manages servlets and JSPs
- It implements the servlet API
- Servlet containers
	- Apache Tomcat
	- jetty
	- GlassFish
	- IBM WebSphere
	- Oracke WebLogic

|Responsibility|Explanation|
|---|---|
|**1. Lifecycle Management**|Creates, initializes (`init()`), calls (`service()`), and destroys (`destroy()`) servlets.|
|**2. Request Handling**|Receives HTTP requests → maps them to correct servlet → generates response back to client.|
|**3. Multithreading**|Creates **new threads** for multiple requests → improves performance.|
|**4. Security**|Handles authentication, authorization, SSL, session management.|
|**5. Resource Management**|Connection pooling, memory, garbage collection support.|

| Pros                                                                      |
| ------------------------------------------------------------------------- |
| Developers focus on logic; container handles heavy internals.             |
| No manual creation or destruction of servlet objects.                     |
| Efficiently handles multiple users simultaneously.                        |
| Provides session management, authentication, role-based access.           |
| Can handle increasing number of requests by managing threads efficiently. |

| Cons                                                              |
| ----------------------------------------------------------------- |
| Extra processing layers add slight latency vs bare metal servers. |
| Understanding configuration, deployment, and mappings takes time. |
| Must configure container (Tomcat/JBoss/etc.) correctly.           |
| Primarily designed for Java-based applications only.              |
