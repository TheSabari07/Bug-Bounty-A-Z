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
