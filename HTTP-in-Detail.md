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
