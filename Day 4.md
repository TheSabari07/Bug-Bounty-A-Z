# DOM-Based XSS Explained

---

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
