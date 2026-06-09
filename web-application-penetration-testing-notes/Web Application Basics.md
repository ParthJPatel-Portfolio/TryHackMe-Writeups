# Web Application Basics TryHackMe Writeup

## Summary

This room introduced the fundamental concepts of web applications and how they operate within a web browser. It covered the structure and purpose of URLs, the communication process between clients and servers through HTTP requests and responses, and the various HTTP request methods used to interact with web resources. The room also explored common HTTP response status codes and the role of HTTP headers in web communication, including their importance in security and application functionality.

---

## Front-End Components

### What is HTML?

HTML (HyperText Markup Language) is the foundation of a web page. It provides the structure and content that a browser displays to users.

HTML is used to define:
- Headings and paragraphs  
- Images and videos  
- Hyperlinks  
- Forms and input fields  

Without HTML, a web page would have no structure or content.

---

### What is CSS?

CSS (Cascading Style Sheets) is used to control the appearance and layout of a web page.

CSS is responsible for:
- Colors and themes  
- Fonts and text styling  
- Spacing and positioning  
- Page layouts and responsiveness  

Without CSS, web pages would appear plain and unformatted.

---

### What is JavaScript?

JavaScript (JS) is a programming language that adds interactivity and dynamic behavior to web applications.

JavaScript enables:
- User interaction and event handling  
- Dynamic content updates  
- Form validation  
- Interactive menus and animations  

JavaScript allows web pages to respond to user actions without requiring a full page reload.

---

## Back-End Components

### What is a Database?

A database is used to store, retrieve, and manage information required by a web application.

Databases commonly store:
- User accounts  
- Password hashes  
- User preferences  
- Application data and records  

Databases allow web applications to maintain and access persistent information.

---

### What is Web Infrastructure?

Web infrastructure consists of the systems and services that support a web application behind the scenes.

Infrastructure typically includes:
- Web servers  
- Application servers  
- Storage systems  
- Networking devices  
- Supporting software and services  

These components process requests and deliver content to users.

---

### What is a Web Application Firewall (WAF)?

A Web Application Firewall (WAF) is a security layer that monitors and filters HTTP traffic before it reaches the web server.

A WAF helps:
- Block malicious requests  
- Protect against common web attacks  
- Reduce exposure to vulnerabilities  
- Improve overall application security  

A WAF acts as a protective barrier between users and the web application.

---

## Key Takeaway

A web application consists of Front End components (HTML, CSS, JavaScript) that users interact with directly and Back End components (Databases, Infrastructure, WAFs) that process data, support functionality, and provide security behind the scenes.

---

# Uniform Resource Locator (URL)

## What is a URL?

A Uniform Resource Locator (URL) is a web address used to access resources on the internet such as webpages, images, videos, and other content. It tells the browser exactly where to go and how to retrieve the requested resource.

---

## Anatomy of a URL

A URL is made up of several components, each serving a specific purpose in locating and accessing web resources.

---

### Scheme

The scheme defines the protocol used to access the resource, such as HTTP or HTTPS. HTTPS is the secure version, using encryption (TLS/SSL) to protect data in transit and is the preferred standard for secure communication.

---

### User

Some URLs may include a username for authentication purposes, although this is rarely used today due to security risks. Including credentials directly in a URL can expose sensitive information.

---

### Host / Domain

The domain identifies the website being accessed. It must be unique and is registered through domain registrars. From a security perspective, attackers may use similar-looking domains (typosquatting) to trick users into visiting malicious sites.

---

### Port

The port specifies which service on the server the request should connect to. Common ports include 80 for HTTP and 443 for HTTPS. It acts like a communication endpoint on the server.

---

### Path

The path points to a specific resource or page on the server. It helps direct the browser to the exact location of the requested content and should be properly secured to prevent unauthorized access.

---

### Query String

The query string begins with `?` and is used to send data to the server, such as search terms or form inputs. Since it can be modified by users, it must be validated to prevent injection attacks.

---

### Fragment

The fragment begins with `#` and directs the browser to a specific section within a webpage. Although it is not sent to the server, it can still be manipulated by users and should be handled carefully in client-side logic.

---

## Summary

A URL is composed of multiple parts that work together to locate and retrieve web resources. Understanding each component—scheme, user, domain, port, path, query string, and fragment—is essential for navigating the web, building web applications, and identifying potential security risks such as malicious domains or injection attacks.

---
## HTTP Messages

## What are HTTP Messages?

HTTP messages are packets of data exchanged between a client (user/browser) and a web server. They define how communication happens in web applications by carrying requests from the client and responses from the server.

There are two main types of HTTP messages:

- **HTTP Requests** – Sent by the client to ask the server to perform an action or retrieve data.
- **HTTP Responses** – Sent by the server in reply to a client’s request.

These messages form the foundation of client-server communication on the web.

---

## Structure of an HTTP Message

Each HTTP message follows a standard format to ensure proper communication between the client and server.

---

### Start Line

The start line is the first part of an HTTP message.

- In a request: it includes the HTTP method (e.g., GET, POST) and the target URL.
- In a response: it includes the HTTP version and a status code (e.g., 200 OK).

It defines what the message is and how it should be processed.

---

### Headers

Headers are key-value pairs that provide additional information about the request or response.

They can include:

- Content type (e.g., HTML, JSON)
- Authentication information
- Browser or server metadata
- Security-related instructions

Headers help control how the message is interpreted and processed.

---

### Empty Line

The empty line separates the headers from the body of the message.

It acts as a delimiter that tells the system where metadata ends and actual content begins. Without it, the message structure would be invalid.

---

### Body

The body contains the actual data being transferred.

- In requests: it may include form data or user input.
- In responses: it contains the requested resource, such as HTML pages or API data.
- Some requests (like GET) may not include a body.

---

## Why HTTP Messages Matter

Understanding HTTP messages is important because they:

- Define how web applications communicate between client and server
- Help developers debug and troubleshoot web issues
- Play a key role in web security (handling sensitive data and preventing attacks)
- Ensure proper structure and reliable data exchange across the web

---

## Summary

HTTP messages are the core mechanism that allows web applications to function correctly and securely. They structure all communication between clients and servers using a consistent format of start line, headers, and body.

---

## HTTP Request Lines and Methods

## What is an HTTP Request?

An HTTP request is a message sent by a client (user/browser) to a web server in order to interact with a web application. It is usually the first step in client-server communication and determines what action the server should perform.

A typical HTTP request includes the method, URL path, and HTTP version, along with additional headers that provide extra context about the request.

---

## Request Line

The request line (also called the start line) is the first part of an HTTP request. It tells the server what action is being requested and includes three components:

- HTTP Method (e.g., GET, POST)  
- URL Path (e.g., /login)  
- HTTP Version (e.g., HTTP/1.1)  


---

## HTTP Methods

HTTP methods define the action the client wants the server to perform on a resource.

### GET
Used to retrieve data from the server without modifying it. Sensitive data should never be exposed in GET requests, as it may appear in URLs or logs.

### POST
Used to send data to the server, often for creating or updating resources. Input should always be validated to prevent attacks such as SQL injection or XSS.

### PUT
Used to replace or update an existing resource on the server. Proper authorization checks are required to ensure only permitted users can modify data.

### DELETE
Used to remove a resource from the server. Authorization must be enforced to prevent unauthorized deletions.

---

## Other HTTP Methods

### PATCH
Used to partially update a resource. Input validation is important to maintain data consistency.

### HEAD
Similar to GET but only returns headers, not the response body. Useful for checking metadata.

### OPTIONS
Returns the HTTP methods supported by a resource. Helps clients understand available actions.

### TRACE
Used for debugging by echoing the request back. Often disabled due to security risks.

### CONNECT
Establishes a secure tunnel, commonly used for HTTPS connections.

---

## URL Path

The URL path specifies the exact resource being requested from the server.

Example:  
`/api/users/123` refers to a specific user resource.

Attackers may attempt to manipulate URL paths to exploit vulnerabilities, so it is important to:

- Validate all incoming paths  
- Sanitize input to prevent injection attacks  
- Restrict access to sensitive resources through proper authorization  

---

## HTTP Version

The HTTP version defines the protocol used for communication between the client and server.

- **HTTP/0.9 (1991):** Basic version supporting only GET requests  
- **HTTP/1.0 (1996):** Introduced headers and improved content handling  
- **HTTP/1.1 (1997):** Added persistent connections and better caching (still widely used)  
- **HTTP/2 (2015):** Improved performance with multiplexing and header compression  
- **HTTP/3 (2022):** Uses QUIC protocol for faster and more secure communication  

Although HTTP/1.1 is still common, HTTP/2 and HTTP/3 provide better performance and security and are increasingly being adopted.

---

## Summary

HTTP requests are messages sent from a client to a server that define what action should be performed on a resource. They consist of a request line, headers, and optional body, and use different HTTP methods such as GET, POST, PUT, and DELETE.

Understanding HTTP requests is essential for web development and cybersecurity, as they are a primary entry point for interacting with web applications and can be exploited if not properly secured.

# HTTP Request Headers & Body

## What are Request Headers?

Request headers are used to send additional information from the client to the web server. They help the server understand how to process the request and provide context about the client, browser, or data being sent.

---

## Common Request Headers

### Host
Example: `Host: tryhackme.com`  
Specifies the domain name of the server the request is targeting.

### User-Agent
Example: `User-Agent: Mozilla/5.0`  
Identifies the client browser and operating system making the request.

### Referer
Example: `Referer: https://www.google.com/`  
Indicates the previous page or source that led to the current request.

### Cookie
Example: `Cookie: user_type=student; room=introtowebapplication`  
Stores data set by the server and sent back by the client on subsequent requests.

### Content-Type
Example: `Content-Type: application/json`  
Defines the format of the data being sent in the request body.

---

## What is the Request Body?

The request body contains data sent from the client to the server, typically used in methods like POST and PUT. The format depends on the `Content-Type` header.

Common formats include URL Encoded data, Form Data, JSON, and XML.

---

## URL Encoded Data (application/x-www-form-urlencoded)

This format sends data as key-value pairs separated by `&`.

**Example:**
name=Aleksandra&age=27&country=US


- Data is stored in `key=value` pairs  
- Multiple values are separated using `&`  
- Special characters are percent-encoded  

---

## Form Data (multipart/form-data)

Used when sending multiple data parts, especially file uploads.

- Data is split into sections using a boundary string  
- Each part includes its own headers  
- Supports binary data such as images and files  

**Example:**
Content-Disposition: form-data; name="profile_pic"; filename="image.jpg"


---

## JSON (application/json)

JSON is a lightweight format used for structured data exchange.

- Data is stored in key-value pairs  
- Uses curly braces `{ }`  
- Fields are separated by commas

## Summary:
Request headers provide important metadata about an HTTP request, such as the client type, server target, and data format. The request body carries the actual data being sent to the server and can be formatted in several ways including URL encoded, multipart form data, JSON, and XML.

Understanding both headers and body formats is essential for working with web applications and identifying how data is transmitted and processed.

# HTTP Response: Status Line and Status Codes
## What is an HTTP Response?

An HTTP response is sent by a web server back to the client after receiving a request. It indicates whether the request was successful or if an error occurred, and it provides the requested data or an explanation of what went wrong.

Each response includes a **status line**, which contains the HTTP version, a status code, and a reason phrase.

---

## Status Line

The status line is the first line in an HTTP response and includes three key components:

- **HTTP Version** – The version of the HTTP protocol being used  
- **Status Code** – A three-digit number that indicates the result of the request  
- **Reason Phrase** – A short human-readable message describing the status code  

---

## Status Codes and Reason Phrases

HTTP status codes are grouped into five categories based on the type of response:

### 1xx – Informational Responses
These indicate that the server has received part of the request and is waiting for the rest.  
Example: The request is still in progress.

---

### 2xx – Successful Responses
These codes mean the request was successfully processed.  
Example: Data was retrieved or an action was completed successfully.

---

### 3xx – Redirection Messages
These indicate that the requested resource has moved to a different location.  
The response may include a new URL for redirection.

---

### 4xx – Client Error Responses
These indicate that there is an issue with the request made by the client.  
Common causes include incorrect URLs, missing authentication, or invalid input.

---

### 5xx – Server Error Responses
These indicate that the server failed to process a valid request.  
These errors are typically caused by issues on the server side.

---

## Common HTTP Status Codes

### 100 (Continue)
The server has received the initial part of the request and is waiting for the rest.

### 200 (OK)
The request was successful, and the server returned the requested resource.

### 301 (Moved Permanently)
The requested resource has been permanently moved to a new URL.

### 404 (Not Found)
The server cannot find the requested resource at the given URL.

### 500 (Internal Server Error)
The server encountered an unexpected error while processing the request.

---

## Summary

HTTP responses are used by servers to communicate the outcome of a client’s request. The status line contains the HTTP version, status code, and reason phrase, while status codes are grouped into five categories (1xx–5xx) that describe informational, successful, redirect, client error, and server error responses.

Understanding these codes is essential for debugging web applications and identifying where issues occur in client-server communication.

# HTTP Response: Headers and Body

## What are Response Headers?

HTTP response headers are key-value pairs sent by the web server along with the response. They provide important metadata about the response and tell the client (usually a browser) how to process and display the returned data.

---

## Required Response Headers

### Date
Example: `Date: Fri, 23 Aug 2024 10:43:21 GMT`  
Indicates the exact date and time the response was generated by the server. This helps with logging and debugging.

---

### Content-Type
Example: `Content-Type: text/html; charset=utf-8`  
Specifies the type of content being returned (such as HTML, JSON, or images) and the character encoding used to properly display it in the browser.

---

### Server
Example: `Server: nginx`  
Identifies the web server software handling the request. While useful for debugging, it can expose server information, so it is often hidden or modified for security reasons.

---

## Other Common Response Headers

### Set-Cookie
Example: `Set-Cookie: sessionId=38af1337es7a8`  
Sends cookies from the server to the client, which are stored and included in future requests.

For security, cookies should use:
- **HttpOnly** → prevents JavaScript access  
- **Secure** → ensures transmission only over HTTPS  

---

### Cache-Control
Example: `Cache-Control: max-age=600`  
Controls how long a response can be cached by the client before requesting fresh data from the server. It can also prevent caching of sensitive data using `no-cache`.

---

### Location
Example: `Location: /index.html`  
Used in redirection responses (3xx status codes) to specify the new location of a resource. This header must be validated to prevent open redirect vulnerabilities.

---

## Response Body

The response body contains the actual data returned by the server, such as:

- HTML pages  
- JSON data  
- Images or files  

To protect against security issues like Cross-Site Scripting (XSS), any user-generated content included in the response should be properly sanitized and escaped before being sent to the client.

---

## Summary

HTTP response headers provide essential information about how the server’s response should be handled, including content type, caching rules, cookies, and redirection instructions. The response body contains the actual data being delivered. Proper handling of headers and body content is critical for both functionality and web application security.

# Security Headers

## What are Security Headers?

HTTP security headers are special response headers that help improve the security of web applications. They provide protections against common attacks such as Cross-Site Scripting (XSS), clickjacking, MIME-type sniffing, and information leakage.

---

## Content-Security-Policy (CSP)

The Content-Security-Policy header helps prevent attacks like XSS by controlling which sources are allowed to load content in a web application.

It defines rules for different types of content such as scripts, styles, and default resources.

### Key Directives
- `default-src 'self'` → Only allow content from the same domain  
- `script-src` → Defines allowed sources for JavaScript files  
- `style-src` → Defines allowed sources for CSS files  

CSP reduces the risk of malicious code being injected from external sources.

---

## Strict-Transport-Security (HSTS)

The HSTS header forces browsers to always use HTTPS when communicating with a website, improving transport security.

### Directives
- `max-age` → Sets how long (in seconds) the browser should enforce HTTPS  
- `includeSubDomains` → Applies the rule to all subdomains  
- `preload` → Allows inclusion in browser preload lists for enforced HTTPS from first visit  

HSTS helps prevent downgrade attacks and ensures encrypted communication.

---

## X-Content-Type-Options

This header prevents browsers from guessing the content type (MIME sniffing), which can be exploited in attacks.

### Directive
- `nosniff` → Forces the browser to strictly follow the declared Content-Type  

This helps avoid security risks caused by incorrect content interpretation.

---

## Referrer-Policy

The Referrer-Policy header controls how much information is shared in the HTTP Referer header when navigating between websites.

### Key Policies
- `no-referrer` → Sends no referrer information at all  
- `same-origin` → Sends referrer only for same-site requests  
- `strict-origin` → Sends only the origin when switching HTTPS sites  
- `strict-origin-when-cross-origin` → Sends full URL for same-origin requests but limits data for cross-origin requests  

This header helps reduce information leakage when users click external links.

---
# Key Findings – Web Application Basics TryHackMe

This set of notes covers the foundational structure and communication flow of modern web applications, focusing on how browsers and servers interact securely and efficiently.

### 1. Web Applications Have Two Main Sides
- **Front End**: Built with HTML, CSS, and JavaScript to handle structure, design, and interactivity in the browser
- **Back End**: Includes databases, infrastructure, and security controls (like WAFs) that process requests and manage data

### 2. URLs Define How Resources Are Accessed
A URL is made up of multiple components (scheme, domain, path, query, etc.) that together determine how and where a resource is retrieved. Each part can introduce security risks if not properly validated.

### 3. HTTP Is the Core Communication Protocol
Web communication relies on HTTP messages:
- **Requests** (client → server)
- **Responses** (server → client)

These messages follow a structured format (start line, headers, body) that ensures consistent communication.

### 4. HTTP Methods Control Actions
Different methods define intent:
- GET retrieves data
- POST sends data
- PUT updates resources
- DELETE removes resources

Improper handling of methods can lead to authorization and data security issues.

### 5. Headers Carry Critical Metadata
Headers provide context about requests and responses, including:
- Client/browser info
- Content type
- Cookies and sessions
- Server behavior instructions

They are essential for both functionality and security.

### 6. Status Codes Indicate Request Outcomes
HTTP status codes are grouped into:
- 1xx: Informational
- 2xx: Success
- 3xx: Redirection
- 4xx: Client errors
- 5xx: Server errors

These are key for debugging and identifying failure points in web applications.

### 7. Data Formats Vary in Requests
Request bodies can use different formats:
- URL-encoded
- Multipart form data
- JSON
- XML

Each format has different use cases and security considerations.

### 8. Security Headers Strengthen Web Protection
Security headers reduce exposure to common attacks:
- **CSP** limits where content can load from (prevents XSS)
- **HSTS** forces HTTPS usage
- **X-Content-Type-Options** prevents MIME sniffing
- **Referrer-Policy** controls information leakage

### Overall Insight
Web applications rely on structured communication between clients and servers using HTTP. Security, functionality, and data integrity depend heavily on properly implemented requests, responses, and headers. Understanding this layer is essential for both web development and cybersecurity analysis.

## Summary

Security headers provide an important layer of protection for web applications. CSP restricts where content can be loaded from, HSTS enforces HTTPS connections, X-Content-Type-Options prevents MIME sniffing, and Referrer-Policy controls how much browsing information is shared between sites.

Together, these headers help reduce exposure to common web attacks and improve overall application security.
