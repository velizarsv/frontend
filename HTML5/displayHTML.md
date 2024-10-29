# How the HTML Page is Rendered

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

