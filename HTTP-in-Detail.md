# HTTP in Detail TryHackMe Room Writeup

## What is HTTP?

HTTP (HyperText Transfer Protocol) is the protocol used for communication between web browsers and web servers. It defines how requests are sent from a client and how responses are returned from a server.

Common data transferred through HTTP includes:

- HTML pages
- Images
- Videos
- CSS files
- JavaScript files

HTTP operates on port 80 by default and does not encrypt data during transmission.

## What is HTTPS?

HTTPS (HyperText Transfer Protocol Secure) is the secure version of HTTP. It uses TLS/SSL encryption to protect data exchanged between clients and servers.

HTTPS provides:

- Confidentiality through encryption
- Integrity by preventing data modification
- Authentication through digital certificates

HTTPS operates on port 443 by default.

## HTTP vs HTTPS

| HTTP | HTTPS |
|--------|--------|
| Unencrypted | Encrypted |
| Port 80 | Port 443 |
| Less secure | More secure |
| No certificate validation | Uses SSL/TLS certificates |

## Key Takeaways
- HTTP is the foundation of web communication.
- HTTPS secures web traffic using encryption.
- Modern websites should use HTTPS to protect user data and verify website authenticity.

## URLs, HTTP Requests, and Responses

### What is a URL?

A URL (Uniform Resource Locator) specifies how and where a resource on the internet can be accessed. It provides the browser with the information needed to locate web pages, images, videos, and other content.

### Components of a URL

- **Scheme** – Protocol used for communication (e.g., HTTP, HTTPS, FTP).
- **User Information** – Optional username and password for authentication.
- **Host** – Domain name or IP address of the server.
- **Port** – Communication port (typically 80 for HTTP and 443 for HTTPS).
- **Path** – Location of the requested resource on the server.
- **Query String** – Additional data passed to the server (e.g., `?id=1`).
- **Fragment** – References a specific section within a webpage (e.g., `#section1`).

<img width="805" height="216" alt="image" src="https://github.com/user-attachments/assets/a1c968c1-090a-4451-a8fc-cd01691eea54" />

### HTTP Requests

An HTTP request is sent by a client (browser) to a web server to request resources.

A request typically contains:
- An HTTP method (e.g., GET)
- The requested resource path
- The HTTP version
- Headers containing additional information such as the target host, browser type, and referring page

Example request information:
- **Host** identifies the website being requested.
- **User-Agent** identifies the client application.
- **Referer** indicates the page that directed the user to the resource.

<img width="457" height="242" alt="image" src="https://github.com/user-attachments/assets/434a1e0e-21f3-41b5-a1fe-80796df1c5a4" />

### HTTP Responses

An HTTP response is returned by the server and contains the requested resource along with metadata.

A response typically includes:
- HTTP version
- Status code (e.g., 200 OK)
- Server information
- Date and time
- Content type
- Content length
- Response body containing the requested content

Example response information:
- **HTTP Protocol Version Number that the web server is using** 
- **Web server software and version number** 
- **Current date, time and timezone** 
<img width="432" height="520" alt="image" src="https://github.com/user-attachments/assets/2a7bc517-6b7b-45c8-b881-d53d4b89310f" />

### Key Takeaways

- URLs tell browsers how to locate and access resources on the internet.
- HTTP requests are sent from clients to servers to retrieve resources.
- HTTP responses contain status information and the requested content.
- Headers provide additional information that helps clients and servers communicate effectively.

## HTTP Methods

HTTP methods define the action a client wants to perform when communicating with a web server. Different methods are used depending on whether data is being retrieved, created, updated, or deleted.

### GET
Used to request and retrieve data from a web server.  
It does not modify any data on the server.

### POST
Used to send data to a web server, often to create a new resource or submit form data.

### PUT
Used to update existing data on a web server or create a resource if it does not already exist.

### DELETE
Used to remove a resource or record from a web server.

## Key Takeaway
- GET retrieves data  
- POST sends new data  
- PUT updates existing data  
- DELETE removes data  

These methods form the basis of how clients interact with web applications and APIs.

## HTTP Status Codes

When a server responds to an HTTP request, the first line includes a **status code**. This code tells the client whether the request was successful or if an error occurred.

HTTP status codes are grouped into five categories:

### 1xx - Informational
These codes indicate that the request has been received and the client should continue sending data.  
They are rarely used in modern web applications.

### 2xx - Success
These codes indicate that the request was successfully processed.

### 3xx - Redirection
These codes indicate that the client must take additional action, such as being redirected to another page or resource.

### 4xx - Client Errors
These codes indicate that there is an error in the client’s request (e.g., bad syntax, missing data, or lack of permission).

### 5xx - Server Errors
These codes indicate that the server failed to process a valid request due to an internal issue.

---

## Common HTTP Status Codes

### 200 - OK
The request was successful, and the server returned the expected response.

### 201 - Created
A new resource was successfully created (e.g., user account or blog post).

### 301 - Moved Permanently
The resource has been permanently moved to a new URL.

### 302 - Found
The resource has temporarily moved to a different URL.

### 400 - Bad Request
The server could not understand the request due to missing or incorrect data.

### 401 - Unauthorized
Authentication is required to access this resource.

### 403 - Forbidden
The client does not have permission to access the resource, even if authenticated.

### 404 - Not Found
The requested resource does not exist on the server.

### 405 - Method Not Allowed
The HTTP method used is not supported for this resource.

### 500 - Internal Server Error
The server encountered an unexpected condition that prevented it from fulfilling the request.

## HTTP Headers

HTTP headers are additional pieces of information sent with HTTP requests and responses. They help the client and server communicate effectively.

Although headers are not strictly required, most web communication depends on them to properly load and interact with websites.

---

## Common Request Headers (Client → Server)

These headers are sent from the client (browser) to the server.

### Host
Specifies the domain name of the website being requested.  
This is important because a single server may host multiple websites.

### User-Agent
Identifies the client browser and version.  
Servers use this information to optimize how content is displayed.

### Content-Length
Indicates the size of the request body being sent to the server (e.g., form data).

### Accept-Encoding
Tells the server which compression methods the client supports (e.g., gzip), allowing faster data transfer.

### Cookie
Sends stored data back to the server to maintain session information (e.g., login state).

---

## Common Response Headers (Server → Client)

These headers are sent from the server back to the client after processing a request.

### Set-Cookie
Used by the server to store data on the client’s browser, which will be sent back in future requests.

### Cache-Control
Defines how long a response can be stored in the browser cache before being requested again.

### Content-Type
Specifies the type of data being returned (e.g., HTML, JSON, images, PDF).  
This helps the browser correctly process the response.

### Content-Encoding
Indicates the compression method used to reduce the size of the response data.

---
## Key Takeaway
HTTP headers provide essential metadata that controls how requests and responses are handled, enabling features like authentication, caching, compression, and content formatting.

### 503 - Service Unavailable
The server is temporarily unable to handle the request due to overload or maintenance.

---
## Key Takeaway
HTTP status codes help the client understand the result of a request, whether it was successful, redirected, or failed due to client or server issues.

## Cookies in HTTP

Cookies are small pieces of data stored on your computer by a web browser. They are used to maintain information between HTTP requests.

---

## How Cookies Work

1. A web server sends a cookie using the `Set-Cookie` header.
2. The browser stores the cookie locally.
3. On every subsequent request to the same server, the browser sends the cookie back.

This allows the server to recognize the client across multiple requests.

---

## Why Cookies Are Used

HTTP is a **stateless protocol**, meaning it does not remember previous requests. Cookies solve this limitation by storing session-related information.

Cookies are commonly used for:

- User authentication (keeping users logged in)
- Personal preferences (language, theme, settings)
- Tracking user activity (e.g., whether a user has visited before)
- Session management

---

## Example Concept

When you log into a website:

- The server sends a session cookie after login
- Your browser stores it
- Each request you make includes that cookie
- The server uses it to recognize you without asking you to log in again

<img width="825" height="832" alt="image" src="https://github.com/user-attachments/assets/309f36b5-58cc-474c-bf91-023b53e04375" />

---
## Key Takeaway
Cookies allow websites to maintain state in an otherwise stateless HTTP system by storing small pieces of data on the client side and sending them back with each request.
