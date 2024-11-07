<details>
<summary> When you enter a web address (URL) and press Enter.
  the **HTTP flow** describes the detailed steps from the client (browser) to the server and back again. Here’s how this process unfolds:
</summary>
  
### 1. **DNS Lookup**
   - The browser first translates the human-readable domain (e.g., `example.com`) into an IP address through **DNS (Domain Name System)**.
   - This involves sending a DNS request, often to a DNS server configured by your ISP or a custom DNS like Google’s or Cloudflare’s.
   - Once the DNS server responds with the IP address of the target server, the browser moves to establish a connection with that server.

### 2. **TCP Connection and TLS Handshake (for HTTPS)**
   - The browser establishes a **TCP (Transmission Control Protocol)** connection with the server using the IP address and port (80 for HTTP, 443 for HTTPS).
   - If it’s an HTTPS connection, an additional **TLS (Transport Layer Security) handshake** occurs to encrypt the communication:
     - The client and server exchange security certificates and negotiate an encryption method.
     - Once completed, this handshake ensures a secure channel for data exchange.

### 3. **HTTP Request**
   - With the connection established, the browser sends an **HTTP request** to the server. This request includes:
     - **HTTP Method**: e.g., `GET` (to retrieve data), `POST` (to send data), or others like `PUT`, `DELETE`, etc.
     - **Request Headers**: Contains information such as the browser type, accepted response format, cookies, authorization tokens, etc.
     - **Request Path**: The specific path on the server requested (e.g., `/about`).
     - **Optional Payload**: Data is sent with requests like `POST`, `PUT`, or `PATCH` in the request body.

   Example HTTP request:
   ```http
   GET /about HTTP/1.1
   Host: example.com
   User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36
   Accept: text/html
   ```

### 4. **Server Processing**
   - The server receives the HTTP request, processes it, and determines the appropriate response. This can involve:
     - **Static Content**: The server retrieves static files (HTML, CSS, JavaScript, images) from the filesystem.
     - **Dynamic Content**: For dynamic content, the server may query a database or process the request through server-side scripts (like PHP, Node.js, or Python).
   - The server prepares an **HTTP response** based on the request and the server’s processing.

### 5. **HTTP Response**
   - The server sends an **HTTP response** back to the browser, which includes:
     - **Status Code**: Indicates the request’s result (e.g., `200 OK`, `404 Not Found`, `500 Internal Server Error`).
     - **Response Headers**: Additional metadata, such as `Content-Type`, `Content-Length`, and `Cache-Control`.
     - **Response Body**: Contains the requested data, such as HTML, JSON, images, or files.

   Example HTTP response:
   ```http
   HTTP/1.1 200 OK
   Content-Type: text/html; charset=UTF-8
   Content-Length: 3456
   Cache-Control: max-age=3600

   <!DOCTYPE html>
   <html>
     <head>
       <title>Example Page</title>
     </head>
     <body>
       <h1>Welcome to Example.com!</h1>
     </body>
   </html>
   ```

### 6. **Rendering in the Browser**
   - The browser receives the HTML, CSS, and JavaScript files and begins **parsing and rendering** the page:
     - It creates a **DOM (Document Object Model)** from the HTML.
     - It constructs the **CSSOM (CSS Object Model)** from the CSS files.
     - It combines the DOM and CSSOM to build a **Render Tree**.
   - JavaScript files are loaded, parsed, and executed to make the page interactive.

### 7. **Handling Additional Requests**
   - The browser continues to make additional **HTTP requests** to the server as needed:
     - **CSS, JavaScript, and Image Files**: These are requested separately as specified in the HTML document.
     - **AJAX or Fetch API Calls**: JavaScript may trigger asynchronous HTTP requests to retrieve more data without reloading the page.

### 8. **Final Rendering and User Interaction**
   - Once all resources are loaded, parsed, and rendered, the user can fully interact with the page.
   - Any further interactions, such as clicking links or submitting forms, repeat the HTTP flow as new requests to the server.

### Summary

The HTTP flow when you enter a URL involves:
1. **DNS Lookup** to get the server’s IP.
2. **Connection Establishment** through TCP and TLS (for HTTPS).
3. **Sending an HTTP Request** with a method, headers, and optional payload.
4. **Server Processing** and generation of an HTTP response.
5. **Receiving and Rendering the Response** in the browser, potentially leading to further requests.
6. 

This entire process happens in fractions of a second, resulting in a smooth and seamless web browsing experience.
</details>
<details>
<summary> What are HTTP headers?
</summary>
</details>
<details>
<summary> Manage memory: cookies, browser memory, session memory
</summary>
</details>
<details>
<summary> Speed optimisation process
</summary>
</details>
<details>
<summary> HTTP authorisation
</summary>
</details>
<details>
<summary> summary
</summary>
  1. What happens when enter the web addres? HTTP flow...
2. What are headers?
3. Manage memory, cookies, browser memory, session memory
4. Speed optimisation process
5. Did you cotribute to the team with someting significant
6. How mange conflicts in team
7. Have you had any disagreements with your management and how did you resolve them? // Did you had some disageement with yours menagement and how you resolved them //
8. HTTP authorisation
9. Difference between angular and react
10. Did you used Cypress ot Cucumber for testing
</details>
