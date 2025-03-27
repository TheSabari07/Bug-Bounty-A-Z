# Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) is a security vulnerability where an attacker injects malicious scripts into a website. These scripts are executed in the browser of a user, leading to various security risks such as data theft, session hijacking, or defacing a website.

## Is JavaScript Only Used for XSS?

No, JavaScript is the primary language used for XSS attacks because browsers execute JavaScript. However, attackers can also use other languages like HTML, Flash, or even VBScript (in older browsers) to exploit vulnerabilities.

---

## Causes and Implications of XSS

| Cause                          | Implication                                         |
|--------------------------------|-----------------------------------------------------|
| Unsanitized user input         | Attackers can inject malicious scripts             |
| Improper HTML escaping         | Scripts can execute within web pages              |
| Flawed content security policy | Attackers can bypass security measures            |
| Session cookie exposure        | Attackers can hijack user sessions                |
| DOM-based script execution     | Users can be tricked into running harmful scripts |

---

## What is Reflected XSS?

Reflected XSS is a type of attack where malicious scripts are injected into a website’s URL or input fields, and the website reflects this input back to the user without proper validation. The script runs in the user’s browser when they visit a specially crafted URL or click a malicious link.

### Example of Reflected XSS

```
https://example.com/search?q=<script>alert('XSS Attack')</script>
```

If the website does not properly handle user input, the script will execute in the victim’s browser when they open the link.

---

## Impact of Reflected XSS

- **Session Hijacking**: Attackers can steal session cookies and impersonate users.
- **Phishing Attacks**: Fake login pages can be injected to steal credentials.
- **Browser Exploits**: Attackers can run harmful scripts in the user’s browser.
- **Data Theft**: Sensitive information can be extracted from web pages.
- **Website Defacement**: Attackers can modify webpage content.

---

## How to Find and Test for Reflected XSS Vulnerabilities

### 1. Manual Testing
- Insert basic payloads into input fields or URLs: `<script>alert('XSS')</script>`
- Check if the input is reflected in the page without sanitization.
- Try different variations like `" onmouseover="alert(1)` for event-based execution.

### 2. Automated Testing
- Use tools like **Burp Suite**, **OWASP ZAP**, or **XSS Hunter** to scan for vulnerabilities.
- Run **Google Dorking** queries like:
  ```
  site:example.com inurl:"search?q="
  ```

### 3. Inspect Browser Response
- Open the developer console (`F12` in most browsers).
- Check if the input is included in the HTML source without proper encoding.

### 4. Bypass Filters
- Use obfuscation techniques:
  ```
  <img src=x onerror=alert('XSS')>
  ```
- Encode payloads in URL encoding or Base64.

---


### Stored XSS

Stored XSS (Persistent XSS) occurs when malicious scripts are permanently stored on a target server and served to users who access the affected page.

---
**Entry Points** (Where malicious input is injected):
- Comment sections
- User profile fields
- Forum posts
- Blog entries
- Message boards

**Exit Points** (Where the malicious script executes):
- A web page displaying stored content
- A profile page showing user details
- A forum post or blog entry with injected scripts
- Any place where stored input is dynamically rendered in the browser
---

### DOM-Based XSS

DOM-Based XSS occurs when the vulnerability exists within the client-side JavaScript execution and does not involve direct server interaction.

| **Aspect**        | **Stored XSS**                      | **DOM-Based XSS**                 |
|------------------|--------------------------------|---------------------------------|
| Execution Point  | Server-side stored content     | Client-side JavaScript execution |
| Data Flow       | Injected into database, retrieved, and executed | Modified directly in the DOM by JavaScript |
| Common Sources  | User input stored in the database | `document.URL`, `document.referrer`, `window.location` |
| Mitigation      | Input validation, output encoding, Content Security Policy (CSP) | Proper JavaScript handling, avoiding direct `innerHTML`, using safer APIs like `textContent` |

---



## Conclusion
Reflected XSS is a serious vulnerability that can lead to session hijacking, data theft, and other attacks. Proper input validation, escaping output, and implementing Content Security Policy (CSP) are necessary to prevent XSS vulnerabilities.

---

**Security Tip:** Always sanitize and validate user inputs to prevent XSS attacks.

