# 4️⃣ 4 - Cross-Site Scripting (XSS)

### Topics

> 1. [ XSS Anatomy](4.1-xss-anatomy.md)
> 2. [Reflected XSS](4.2-reflected-xss.md)
> 3. [Stored XSS](4.3-stored-xss.md)
> 4. [DOM-Based XSS](4.4-dom-based-xss.md)
> 5. [Identifying & Exploiting XSS with XSSer](4.5-identifying-and-exploiting-xss-with-xsser.md)

{% embed url="https://owasp.org/www-community/attacks/xss/" %}

## Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) constitutes a client-side web vulnerability enabling attackers to embed malicious scripts into web pages.

This vulnerability often arises from inadequate input sanitization/validation within web applications.

Attackers exploit XSS vulnerabilities to insert harmful code into web applications. Given that XSS is a client-side vulnerability, these scripts execute within the victim's browser.

XSS vulnerabilities impact web applications deficient in input validation and reliant on client-side scripting languages such as JavaScript, Flash, CSS, etc.

### Web Basics

* ​[Web Application Basics](https://attackdefense.com/listing?labtype=webapp-web-app-basics\&subtype=webapp-web-app-basics-getting-started)​
* ​[Web Apps Tools of Trade](https://attackdefense.com/listing?labtype=webapp-tools-of-trade\&subtype=webapp-tools-of-trade-getting-started)

{% content-ref url="https://app.gitbook.com/s/iS3hadq7jVFgSa8k5wRA/practical-ethical-hacker-notes/main-contents/14-hacking-web-apps" %}
[14 - Hacking Web Apps](https://app.gitbook.com/s/iS3hadq7jVFgSa8k5wRA/practical-ethical-hacker-notes/main-contents/14-hacking-web-apps)
{% endcontent-ref %}

### Practise

🔬 There are many vulnerable testing web apps like:

* ​[Juice Shop - Kali Install](https://www.kali.org/tools/juice-shop/)​
* ​[DVWA - Kali Install](https://www.kali.org/tools/dvwa/)​
* ​[bWAPP](http://www.itsecgames.com/)​
* ​[Mutillidae II](https://github.com/webpwnized/mutillidae)

<details>

<summary>DVWA</summary>

**The Damn Vulnerable Web Application (DVWA)** is a web application built with PHP and MySQL intentionally designed to be susceptible to security vulnerabilities. Its primary purpose is to serve as a resource for security professionals to assess their skills and tools within a legal context. Additionally, it aids web developers in gaining a deeper understanding of the processes involved in securing web applications and facilitates learning about web application security for both students and teachers in a controlled classroom setting.

DVWA is designed to provide a platform for practicing various common web vulnerabilities at different difficulty levels, all presented through a simple and user-friendly interface. It's important to note that there are deliberate both documented and undocumented vulnerabilities within the software, encouraging users to explore and identify as many issues as possible.

</details>

{% embed url="https://github.com/digininja/DVWA" %}
DVWA
{% endembed %}

{% embed url="https://portswigger.net/web-security/cross-site-scripting/cheat-sheet" %}

#### DVWA - My Writeups

{% content-ref url="https://app.gitbook.com/s/rRWtuMw6xkkeDjZfkcWC/dvwa" %}
[DVWA](https://app.gitbook.com/s/rRWtuMw6xkkeDjZfkcWC/dvwa)
{% endcontent-ref %}

#### Theory and Lab platform

{% embed url="https://portswigger.net/web-security/all-labs" %}
Web Burp Suite Security Academy
{% endembed %}

> #### ❗ Disclaimer
>
> **Never use tools and techniques on real IP addresses, hosts or networks without proper     authorization!**
>
> ❗_**Never run these techniques on un-authorized addresses**_
