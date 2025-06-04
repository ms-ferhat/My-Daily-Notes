## Reflected XSS

> [!info]- __Reflected XSS__
> Reflected XSS is the simplest variety of cross-site scripting. It arises when an application receives data in an HTTP request and includes that data within the immediate response in an unsafe way.


## Stored XSS
> [!info]-  __Stored XSS__
> Stored cross-site scripting (also known as second-order or persistent XSS) arises when an application receives data from an untrusted source and includes that data within its later HTTP responses in an unsafe way.


## DOM-based XSS

> [!info]- __DOM-based XSS__
> DOM-based XSS vulnerabilities usually arise when JavaScript takes data from an attacker-controllable source, such as the URL, and passes it to a sink that supports dynamic code execution, such as `eval()` or `innerHTML`.

### Common sources

The following are typical sources that can be used to exploit a variety of taint-flow vulnerabilities:

```html
document.URL
document.documentURI
document.URLUnencoded
document.baseURI
location
document.cookie
document.referrer
window.name
history.pushState
history.replaceState
localStorage
sessionStorage
IndexedDB (mozIndexedDB, webkitIndexedDB, msIndexedDB)
Database
```

### Testing HTML sinks
- [ ] Place a random alphanumeric string in the source (e.g., location.search)
- [ ] Use DevTools to search the DOM for the string
- [ ] Identify where the string appears in the DOM
- [ ] Determine the context (e.g., inside attribute, tag, script)
- [ ] Modify input to attempt breaking the context
- [ ] Check how the browser encodes the input
- [ ] Evaluate if XSS is possible

## How to find XSS
- [ ] search for input field
- [ ] Try all tags using intruder
- [ ] Try all events inside allowed tags

## Exploiting XSS vulnerabilities

The traditional way to prove that you've found a cross-site scripting vulnerability is to create a popup using the `alert()` function.

**Other Exploiting could be:**
1. Exploiting XSS to steal cookies
2. Exploiting XSS to capture passwords
3. Exploiting XSS to bypass CSRF protections