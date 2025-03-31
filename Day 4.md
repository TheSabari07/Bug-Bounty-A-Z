# DOM-Based XSS Explained

---

**Refer and practice labs on PortSwigger:**  
[PortSwigger XSS Labs](https://portswigger.net/web-security/cross-site-scripting)  


## What is DOM-Based XSS?

DOM-Based XSS (Document Object Model-Based Cross-Site Scripting) is a type of XSS where the attack happens entirely on the client side, within the browser. The malicious script manipulates the DOM without any server-side processing.

### Example:
```html
<script>
    var userInput = location.hash.substring(1);
    document.getElementById("output").innerHTML = userInput;
</script>
```
If an attacker tricks a user into visiting:
```
http://example.com/#<script>alert('XSS')</script>
```
The JavaScript will execute because `innerHTML` is used, leading to XSS.

---

## Difference Between `innerHTML` and `textContent`

| Property      | Description | Vulnerability Risk |
|--------------|-------------|--------------------|
| `innerHTML`  | Parses HTML and inserts it into the DOM. | High (can execute scripts) |
| `textContent` | Treats content as plain text. | Low (does not execute scripts) |

### Example:
```html
<div id="example"></div>
<script>
    var unsafeInput = "<script>alert('XSS')</script>";
    document.getElementById("example").innerHTML = unsafeInput; // Executes script
    document.getElementById("example").textContent = unsafeInput; // Displays as text
</script>
```

---

## What is DOM Invader?

DOM Invader is a tool in Burp Suite that helps security researchers identify and exploit DOM-based XSS vulnerabilities.

**Key Features:**
- Monitors JavaScript functions that modify the DOM.
- Finds unsafe `innerHTML` assignments.
- Automates XSS payload testing.

---

## What is a Custom Tag?

A custom tag is an HTML element that is not part of standard HTML but can be defined using JavaScript.

### Example:
```html
<custom-element></custom-element>
<script>
    class CustomElement extends HTMLElement {
        connectedCallback() {
            this.innerHTML = "<p>Custom tag content</p>";
        }
    }
    customElements.define('custom-element', CustomElement);
</script>
```

---

## Why `<body%20>` Instead of `<body>`?

`%20` is URL encoding for a space. In some XSS payloads, attackers use `<body%20>` to bypass security filters that strictly check for `<body>`.

---

## Why Encoding is Important?

Encoding converts special characters into a safe format to prevent script execution.

| Character | HTML Encoding |
|-----------|--------------|
| `<`       | `&lt;`       |
| `>`       | `&gt;`       |
| `"`       | `&quot;`     |
| `'`       | `&#39;`      |

Without encoding, user input could be interpreted as code instead of text.

### Example:
```html
<input value="<script>alert(1)</script>">
```
If not encoded, this will execute JavaScript. Encoding it as `&lt;script&gt;alert(1)&lt;/script&gt;` prevents execution.

---

## XSS in HTML Tag Attributes

Attackers can inject malicious scripts inside HTML attributes such as `onerror`, `onmouseover`, or `href`.

### Example:
```html
<img src="invalid.jpg" onerror="alert('XSS')">
```
Here, when the image fails to load, the script executes.

### Mitigation:
- Use **Content Security Policy (CSP)**.
- Validate and sanitize input.
- Avoid `innerHTML` when inserting user data.

---

```
