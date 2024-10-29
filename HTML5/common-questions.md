<details>
  <summary>
# What Happens When You Enter a Web Address in the Browser?
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
