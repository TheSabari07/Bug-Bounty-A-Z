# **Day 1 of Bug Bounty - Understanding HTTP & AJAX**


---

## **1. HTTP (Hypertext Transfer Protocol)**

HTTP is the foundation of communication between web servers and clients. It is **stateless**, meaning each request is independent, and the server does not retain past interactions.

### **Why is HTTP Stateless?**

| Reason | Explanation |
| --- | --- |
| **Scalability** | Servers don't need to track user sessions, making them efficient. |
| **Simplified Communication** | Each request is **self-contained**. |
| **Load Balancing** | Requests can be handled by different servers independently. |

### **How Do Websites Maintain State?**

| Method | Description |
| --- | --- |
| **Cookies** | Small pieces of data stored in the browser. |
| **Session IDs** | Unique identifiers linking requests. |
| **JWT (JSON Web Tokens)** | Token-based authentication. |

---

## **2. HTTPS (Hypertext Transfer Protocol Secure)**

HTTPS = **HTTP + Security (SSL/TLS encryption)**

| Feature | Benefit |
| --- | --- |
| **Encryption (SSL/TLS)** | Protects data from eavesdropping. |
| **Data Integrity** | Prevents modification of data in transit. |
| **Authentication** | Verifies website identity using SSL certificates. |

---

## **3. AJAX (Asynchronous JavaScript and XML)**

AJAX allows web pages to fetch/send data **without reloading** the page.

### **How AJAX Works**

1. JavaScript makes an **HTTP request** (GET/POST) to a server.
2. The server processes the request and responds with data (usually JSON/XML).
3. JavaScript updates the webpage **without a full refresh**.

---

## **4. HTTP Methods**

| Method | Action |
| --- | --- |
| **GET** | Retrieve data |
| **POST** | Create data |
| **PUT** | Replace data |
| **PATCH** | Modify data |
| **DELETE** | Remove data |
| **HEAD** | Retrieve headers only |
| **OPTIONS** | Discover methods |
| **TRACE** | Debugging |

---

## **5. HTTP Header Fields**

### **Request Headers (Client → Server)**

| Header | Description | Example |
| --- | --- | --- |
| **Host** | Target server | `Host: example.com` |
| **User-Agent** | Browser info | `User-Agent: Mozilla/5.0` |
| **Accept** | Expected response type | `Accept: application/json` |
| **Content-Type** | Data format in request body | `Content-Type: application/json` |
| **Authorization** | Authentication token | `Authorization: Bearer <token>` |
| **Cookie** | User session data | `Cookie: session=xyz123` |
| **Referer** | Previous page URL | `Referer: <https://google.com`> |
| **Origin** | Request origin (CORS) | `Origin: <https://example.com`> |

### **Response Headers (Server → Client)**

| Header | Description | Example |
| --- | --- | --- |
| **Content-Type** | Format of response | `Content-Type: text/html` |
| **Set-Cookie** | Stores session info | `Set-Cookie: session=xyz123` |
| **Cache-Control** | Caching rules | `Cache-Control: no-cache` |
| **Location** | Redirect URL | `Location: <https://new-site.com`> |
| **Server** | Server type | `Server: Apache/2.4.41` |
| **X-Frame-Options** | Clickjacking protection | `X-Frame-Options: DENY` |
| **Strict-Transport-Security (HSTS)** | Enforce HTTPS | `Strict-Transport-Security: max-age=31536000; includeSubDomains` |

---

## **6. HTTP Status Codes**

### **1xx – Informational**

| Code | Meaning |
| --- | --- |
| **100** | Continue |
| **101** | Switching Protocols |

### **2xx – Success**

| Code | Meaning |
| --- | --- |
| **200** | OK |
| **201** | Created |
| **204** | No Content |

### **3xx – Redirection**

| Code | Meaning |
| --- | --- |
| **301** | Moved Permanently |
| **302** | Found (Temporary Redirect) |
| **304** | Not Modified |

### **4xx – Client Errors**

| Code | Meaning |
| --- | --- |
| **400** | Bad Request |
| **401** | Unauthorized |
| **403** | Forbidden |
| **404** | Not Found |
| **405** | Method Not Allowed |
| **429** | Too Many Requests |

### **5xx – Server Errors**

| Code | Meaning |
| --- | --- |
| **500** | Internal Server Error |
| **502** | Bad Gateway |
| **503** | Service Unavailable |
| **504** | Gateway Timeout |

---

## **7. HTTP/2 & HTTP/3 – Next-Gen Web Performance**

### **HTTP/2 (2015 – Faster & Efficient)**

| Feature | Benefit |
| --- | --- |
| **Multiplexing** | Multiple requests/responses are sent simultaneously. |
| **Header Compression (HPACK)** | Reduces the size of HTTP headers. |
| **Server Push** | Server sends resources before the client requests them. |
| **Binary Protocol** | Uses binary format for efficiency. |
| **More Secure** | Enforces HTTPS. |

### **HTTP/3 (2022 – Faster, Uses QUIC)**

| Feature | Benefit |
| --- | --- |
| **Uses QUIC Instead of TCP** | Reduces latency and improves stability. |
| **0-RTT Handshakes** | Faster initial connections. |
| **No Head-of-Line Blocking** | Eliminates request queueing issues. |
| **Always Encrypted (TLS 1.3)** | Ensures high security. |

### **HTTP Evolution**

| HTTP Version | Transport Layer |
| --- | --- |
| **HTTP/1.1** | TCP |
| **HTTP/2** | TCP (with Multiplexing) |
| **HTTP/3** | QUIC (UDP-based) |

---

## **Conclusion**

- **HTTP is stateless**, requiring mechanisms like cookies, sessions, and JWTs to maintain user data.
- **HTTPS encrypts communication** using SSL/TLS.
- **AJAX enables dynamic content updates** without full page reloads.
- **HTTP/2 & HTTP/3 improve web performance** with multiplexing and QUIC.
- **Understanding HTTP headers and status codes** is crucial for security and bug bounty research.

> ref : https://youtu.be/iYM2zFP3Zn0?si=UP5sfZF7_jcJPwtz
---
