## Reflected XSS

> [!info]- __Reflected XSS__
> Reflected XSS is the simplest variety of cross-site scripting. It arises when an application receives data in an HTTP request and includes that data within the immediate response in an unsafe way.

**Method 1**
- [ ] Place a random alphanumeric string in any input field (e.g., location.search)
- [ ] search in repose about this string 
- [ ] identify context
- [ ] try to inject XXS manual

**Method 2**
- [ ] search for input field
- [ ] Try all tags using intruder
- [ ] Try all events inside allowed tags

**Method 3** *valid with php*
- [ ] used four tools (paramspider, KXSS, GXSS, dalfox )

**Method 4**
```
echo example.com | gau | gf xss | uro | Gxss | kxss | tee xss_output.txt
cat xss_output.txt | grep -oP '^URL: \K\S+' | sed 's/=.*/=/' | sort -u > final.txt
```
- [ ] **Loxs Tool**
## Stored XSS
> [!info]-  __Stored XSS__
> Stored cross-site scripting (also known as second-order or persistent XSS) arises when an application receives data from an untrusted source and includes that data within its later HTTP responses in an unsafe way.



## DOM-based XSS

> [!info]- __DOM-based XSS__
> DOM-based XSS vulnerabilities usually arise when JavaScript takes data from an attacker-controllable source, such as the URL, and passes it to a sink that supports dynamic code execution, such as `eval()` or `innerHTML`.



### Testing HTML sinks
- [ ] Place a random alphanumeric string in the source (e.g., location.search)
- [ ] Use DevTools to search the DOM for the string
- [ ] Identify where the string appears in the DOM
- [ ] Determine the context (e.g., inside attribute, tag, script)
- [ ] Modify input to attempt breaking the context
- [ ] Check how the browser encodes the input
- [ ] Evaluate if XSS is possible


## XSS Context

### XSS between HTML tags
## Exploiting XSS vulnerabilities

1. Exploiting XSS to steal cookies
2. Exploiting XSS to capture passwords
3. Exploiting XSS to bypass CSRF protections

## Tools 
1. Xsstrike
2. dalfox
3. lazyxss
## Common sources

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



## Payload

```html
y%0D%0A%0D%0A%3Cimg+src%3Dcopyparty+onerror%3Dalert(1)%3E


<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100">
  <circle cx="50" cy="50" r="40" fill="red" onmouseover="fetch('/profile/delete')"/>
</svg>

<a href="java$Tab;script&colon;alert(1)">Click Me</a>



```