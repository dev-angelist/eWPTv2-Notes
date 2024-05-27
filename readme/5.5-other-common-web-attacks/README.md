# 6️⃣ 6 - ​Common Attacks

## Other Common Web Attacks

### Topics

> 1. [HTTP Attacks](6.1-http-attacks/)
> 2. [Session Attacks](5.5.1-session-attacks.md)
> 3. [CSRF](5.5.2-csrf.md)
> 4. [File and Resource Attacks](5.5.3-file-and-resource-attacks.md)

in addition to SQLi and XSS, there are several other common web attacks that malicious actors may use to exploit vulnerabilities in web applications. Here are a few notable ones:

1. **HTTP Method Tampering:** is a type of security vulnerability that can be exploited in web apps, that occurs when an attacker manipulates the HTTP request method used to  interact with a web server.
2. **Cross-Site Request Forgery (CSRF):** CSRF attacks trick users into unknowingly submitting a web request on a site where they are authenticated. This can lead to actions being performed on the user's behalf without their consent.
3. **Cross-Site Script Inclusion (XSSI):** XSSI attacks involve an attacker including external scripts in a web page, often exploiting misconfigurations in the application's content security policy.
4. **Clickjacking:** Clickjacking involves hiding malicious actions behind a legitimate-looking interface. Users unknowingly interact with the hidden elements, allowing attackers to perform actions on their behalf.
5. **Security Misconfigurations:** Improperly configured security settings, such as default passwords or unnecessary services running, can expose vulnerabilities that attackers exploit.
6. **File Inclusion Attacks:** This includes Local File Inclusion (LFI) and Remote File Inclusion (RFI). LFI occurs when an attacker can include files on a server through the web browser. RFI occurs when an attacker can include remote files, often from a malicious server.
7. **Command Injection:** Attackers can inject malicious commands into input fields that are then executed by the application. This can lead to unauthorized access or other malicious activities.
8. **XML External Entity (XXE) Attacks:** XXE attacks exploit vulnerabilities in XML processors by injecting malicious XML content. This can lead to disclosure of internal files or denial of service.
9. **Server-Side Request Forgery (SSRF):** SSRF attacks involve tricking a server into making unintended requests, often to internal resources, which can lead to unauthorized access or data exposure.
10. **Brute Force Attacks:** Attackers attempt to gain access to user accounts by systematically trying all possible combinations of usernames and passwords.
11. **Session Hijacking and Session Fixation:** Session hijacking involves stealing a user's session token to gain unauthorized access. Session fixation involves setting a user's session token, often through phishing, to hijack their session later.

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
> * **Never use tools and techniques on real IP addresses, hosts or networks without proper authorization!**
