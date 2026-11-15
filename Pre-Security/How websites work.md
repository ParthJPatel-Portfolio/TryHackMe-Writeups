# TryHackMe: How Websites Work

| | |
|---|---|
| **Room** | [How Websites Work](https://tryhackme.com/room/howwebsiteswork) |
| **Platform** | TryHackMe |
| **Pathway** | Pre Security – How the Web Works |
| **Focus** | Web Fundamentals, HTML, JavaScript, Web Application Security |

---

## 1. How Websites Work

Websites operate through communication between a **client** (web browser) and a **web server**. When a user visits a website, the browser sends a request to the server, which processes it and returns the resources the browser needs to display the page.

A website has two main components:

- **Front End (Client-Side):** The part users see and interact with in their browser, including layouts, text, images, buttons, and interactive elements.
- **Back End (Server-Side):** The part responsible for processing requests, handling application logic, communicating with databases, and returning responses to clients.

> Understanding the difference between client-side and server-side functionality is important when identifying potential web application vulnerabilities.

---

## 2. HTML (HyperText Markup Language)

HTML provides the structure and content of a webpage. It uses elements (commonly called tags) to tell the browser how different pieces of content should be displayed.

| Element | Purpose |
|---|---|
| `<html>` | Defines the root of an HTML document |
| `<head>` | Contains metadata and information about the page |
| `<title>` | Sets the page title shown in the browser tab |
| `<body>` | Contains the visible content of the page |
| `<h1>` | Defines a main heading |
| `<p>` | Defines a paragraph |
| `<img>` | Embeds an image into the page |

### Practical Exercise

The room provided an interactive HTML editor where I modified page elements and watched the changes render in the browser.

**Tasks completed:**

1. Rendered HTML content to see how browsers interpret HTML elements.
2. Fixed a broken image reference so the missing image displayed.
3. Added another image using an `<img>` tag and its `src` attribute.

```html
<img src="img/dog-1.png">
```
<img width="946" height="876" alt="image" src="https://github.com/user-attachments/assets/dc36cf7f-3ff5-4ed7-91b4-c1f86c35e1d1" />


**Key takeaway:** HTML controls the structure of a webpage. Knowing its elements makes it easier to inspect page content and spot improperly exposed information.

---

## 3. JavaScript

JavaScript adds functionality and interactivity to websites. Where HTML defines structure, JavaScript lets pages respond to user actions and update content dynamically.

JavaScript can be included directly in HTML using `<script>` tags, or loaded from an external `.js` file.

### Practical Exercise

The room introduced **DOM manipulation**. The Document Object Model (DOM) lets scripts access and modify HTML elements.

This code selects the element with the ID `demo` and changes its content:

```javascript
document.getElementById("demo").innerHTML = "Hack the Planet";
```

I also explored event handling using a button with an `onclick` attribute:

```html
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>
    Click Me!
</button>
```

When the button is clicked, the JavaScript runs and updates the page dynamically.

<img width="960" height="522" alt="image" src="https://github.com/user-attachments/assets/ed2ad1ca-facc-4bc3-bd97-279e86fd15b3" />


**Key takeaway:** JavaScript enables dynamic page behavior. Understanding how scripts interact with HTML elements is useful when investigating client-side vulnerabilities.

---

## 4. Sensitive Data Exposure

Sensitive Data Exposure happens when a website unintentionally reveals confidential information to users. Data embedded in front-end source code can be accessible even if it is never visibly displayed on the page.

**Common examples:**

- Hardcoded usernames and passwords
- API keys and authentication tokens
- Hidden administrative links
- Internal comments containing sensitive information
- Configuration details exposed through front-end files

### Practical Exercise

The room provided a page with a login form. Instead of interacting with the form, I inspected the underlying HTML using the browser's **View Page Source** feature (`Ctrl+U`).

This revealed a password embedded directly in the page source.

**Security takeaway:** Anything placed in client-side HTML or JavaScript should never be considered secret. Credentials and authentication logic must be handled securely on the server side.

---

## 5. HTML Injection

HTML Injection is a vulnerability that occurs when an application accepts user input and inserts it into a webpage without properly validating or sanitizing it. An attacker can inject HTML elements into the page, changing how content is displayed or introducing malicious links.

### Practical Exercise

The room provided a page with a text input field that displayed whatever was submitted. I tested how the application handled HTML by submitting:

```html
<h1>
    <a href="http://hacker.com">Click Here</a>
</h1>
```

Instead of treating the input as plain text, the page interpreted it as HTML and rendered a clickable hyperlink. This shows how unfiltered user input can alter page content.

### Prevention

Developers should:

- Validate user input before processing it.
- Sanitize input where appropriate.
- Encode output so user-provided content is treated as text, not executable HTML.
- Use safe DOM methods such as `textContent` instead of inserting untrusted input via `innerHTML`.

**Security takeaway:** Never trust user input. Improper handling of user-controlled content can lead to HTML injection and potentially more serious issues like Cross-Site Scripting (XSS).

---

## 6. Key Takeaways

| Concept | What I Learned |
|---|---|
| Front End | Client-side components rendered by the browser |
| Back End | Server-side processing and application logic |
| HTML | Structures webpage content and elements |
| JavaScript | Adds interactivity and dynamically modifies pages |
| DOM | Lets JavaScript access and modify HTML elements |
| Sensitive Data Exposure | Finding confidential information exposed in source code |
| HTML Injection | Risks associated with unfiltered user input |

---

## 7. Relevance to Cybersecurity

Understanding how websites work is a foundation for web application security and penetration testing. The exercises showed why it matters to:

- Inspect page source code
- Understand client-side scripts
- Test how applications process user input

These fundamentals are a starting point for exploring more advanced topics, including Cross-Site Scripting (XSS), injection attacks, authentication weaknesses, and insecure application configurations.
