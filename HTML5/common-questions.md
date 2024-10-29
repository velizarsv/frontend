<details>
  <summary>
 What Happens When You Enter a Web Address in the Browser?
  </summary>

When you enter a URL in your browser, a sequence of events is triggered to retrieve and display the requested webpage. Here’s a breakdown of each step:

## 1. DNS Lookup
   - The browser first checks its cache and the system’s DNS cache to find the IP address associated with the domain. If not found locally, it contacts a **DNS server** to translate the domain name (e.g., `example.com`) into an IP address (e.g., `192.0.2.1`), which servers use for communication.

## 2. Establishing a Connection
   - Using the IP address, the browser initiates a **TCP (Transmission Control Protocol)** connection with the server. For secure sites (HTTPS), a **TLS (Transport Layer Security)** handshake occurs to encrypt the communication.

## 3. Sending an HTTP Request
   - The browser sends an **HTTP or HTTPS request** to the server. This request includes headers with information about the browser type, accepted languages, cookies, and more. If there’s form data or other input, it’s included in this request.

## 4. Server Processing and Response
   - The server processes the request, possibly querying databases or APIs if it’s a dynamic page, and returns an **HTTP response** containing:
      - **Status code** (e.g., 200 for success, 404 for not found)
      - **Headers** with additional info
      - **Body** containing the HTML, CSS, and potentially JavaScript for the webpage

## 5. Rendering the Page
   - The browser receives the HTML and begins **parsing** it, creating a **DOM (Document Object Model)**.
   - **CSS and JavaScript** files are fetched and applied to style the DOM and add interactivity.
   - **Render Tree Construction**: The browser combines the DOM and CSSOM (CSS Object Model) into a Render Tree, which includes only visible elements.
   - **Layout and Painting**: The browser calculates positions and sizes (layout) and paints pixels onto the screen.

## 6. Executing JavaScript
   - JavaScript files are executed as they load, modifying the DOM as needed. For async data fetching (e.g., API calls), these requests are made, and any new data is applied to the page in real-time.

## 7. Loading Additional Resources
   - Images, videos, and other linked resources are fetched and displayed. Depending on their load times, they may appear after the main content.

## 8. Final Page Render
   - Once all resources and scripts load, the page is fully rendered, though additional background tasks may continue.

This complex sequence involves protocols, data exchanges, and rendering processes to ensure the page appears and functions accurately.
</details>
<details>
  <summary> 
     How the HTML Page is Rendered   
  </summary>
Rendering an HTML page involves multiple steps performed by the browser to transform HTML, CSS, and JavaScript into a visual page that users can interact with. Here’s a breakdown of this process:

## 1. Loading

- The browser sends an HTTP request for the webpage.
- The server responds with the HTML document and any linked resources, such as CSS, JavaScript files, and images.

## 2. Parsing

- **HTML Parsing**: The browser reads the HTML file from top to bottom, creating a **Document Object Model (DOM)** tree that represents the structure of the page.
- **CSS Parsing**: The browser fetches and parses CSS files to create the **CSS Object Model (CSSOM)**, which defines styling rules for each DOM element.
- **JavaScript Parsing and Execution**: If there are JavaScript files or inline scripts, the browser stops HTML parsing to fetch, parse, and execute them (unless they’re deferred or asynchronous). JavaScript can manipulate both the DOM and CSSOM, modifying elements and styles dynamically.

## 3. Render Tree Construction

- The DOM and CSSOM trees are combined to form a **Render Tree**, which includes only visible elements. Nodes with `display: none` do not appear in this tree. Each Render Tree node has details on how to display the corresponding DOM node.

## 4. Layout (Reflow)

- The browser calculates the exact position and size of each visible element based on the Render Tree, viewport dimensions, and styling rules. This stage, known as **layout** or **reflow**, involves assigning specific coordinates to each element.

## 5. Painting

- The browser traverses the Render Tree to **paint** each node onto the screen. It fills in pixels based on styles, colors, borders, text, and images specified in the CSS and HTML.

## 6. Compositing

- Modern browsers use multiple layers to manage complex layouts efficiently. Layers are composited, meaning if there are animations or interactions, only the affected layers need to be repainted, reducing rendering load.

---

### Example: Server-Side Rendering (SSR) in Next.js

In frameworks like **Next.js** with Server-Side Rendering (SSR), the server sends a fully rendered HTML document to the browser, improving load times and SEO. The HTML is generated on the server, so the browser can start rendering the page immediately without waiting for JavaScript to complete.
</details>

