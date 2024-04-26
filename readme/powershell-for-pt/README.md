# 3️⃣ 3 - Web Proxies

### Topics

> 1. &#x20;[Burp Suite](3.1.md)
> 2. [OWASP ZAP](3.1-1.md)

## What is a Web Proxy?

A web proxy, also known as an interception proxy, serves to capture, analyze, and alter requests and responses passing between an HTTP client and a server.

Intercepting HTTP/HTTPS traffic allows penetration testers to scrutinize and understand the behavior and functionalities of web applications.

Proxies stand as essential tools in conducting web application penetration tests, evolving into indispensable allies in the assessment and testing of web applications.

Penetration testers rely on web proxies to intercept, analyze, and modify HTTP requests before they reach the web server.

Web proxies commonly function by intercepting traffic from the client browser, accomplished by configuring the browser to route all traffic through the preferred web proxy.

The main goals of intercepting requests and responses are to:

* Analyze the behavior and functionality of web applications.
* Map out the structure of the web application, such as its sitemap.
* Identify vulnerabilities and misconfigurations in web applications.
* Assess and launch attacks against web applications.

Among the most prevalent and relied-upon web proxies in use today are:

* [Burp Suite](3.1.md)
* [OWASP ZAP](3.1-1.md)

### Web Proxy vs Web Proxy Servers

Distinguishing between web proxies and proxy servers is crucial:

* A web proxy intercepts, analyzes, or modifies HTTP/HTTPS requests between a client and server, exemplified by tools like Burp Suite or OWASP ZAP.
* On the other hand, a web proxy server handles internet traffic proxying, filtering specific data, and optimizing bandwidth, as seen in applications like Squid Proxy.

> #### ❗ Disclaimer
>
> * **Never use tools and techniques on real IP addresses, hosts or networks without proper authorization!**
