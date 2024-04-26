# 2.3 Web Server Fingerprinting

## Web Server Fingerprinting

A **web server fingerprint** is essentially a unique identifier or signature of a web server's software, configuration, and sometimes even its hardware characteristics. It's like a digital footprint that can reveal details about the server's underlying technology stack, such as the operating system, web server software (e.g., Apache, Nginx), version numbers, installed modules, and other relevant information.

Web server fingerprints can be obtained through various means, including:

1. **HTTP Headers**: Web servers often include specific headers in their HTTP responses that can reveal information about the server software and its version. For example, the "Server" header typically discloses the name and version of the server software being used.
2. **Error Pages**: The format and content of error pages (e.g., 404 Not Found) can sometimes provide clues about the web server software and its version.
3. **Response Behavior**: Certain behaviors or responses from the server can also be indicative of the server type and version. For example, the way the server handles certain requests or supports specific features may help identify it.
4. **Banner Grabbing**: This involves directly connecting to the server and analyzing the banners or initial responses it provides, which often contain information about the server software and version.

We can use following methods and tool to do a Web Server Fingerprint:

### Nmap

{% content-ref url="https://app.gitbook.com/s/iS3hadq7jVFgSa8k5wRA/practical-ethical-hacker-notes/tools/nmap" %}
[Nmap](https://app.gitbook.com/s/iS3hadq7jVFgSa8k5wRA/practical-ethical-hacker-notes/tools/nmap)
{% endcontent-ref %}

We can use Nmap for first scanning on all ports with the flag: `-p0-`

```bash
sudo nmap -p0- sV <Target> -oG nmap/port
```

After it, we can use searchsploit to discover potential exploit and search nmap script and eventually grep for detailed results

```bash
ls -al /usr/share/nmap/scripts/ | grep -e "apache"
```

<div align="left">

<figure><img src="../../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

</div>

And e.g. use http-enum to discover port 80

```bash
sudo nmap -sV -p 80 —script=http-enum <target>
```



<table><thead><tr><th width="154.99999999999997">command</th><th>result</th></tr></thead><tbody><tr><td>--open</td><td>only open ports</td></tr><tr><td>sC</td><td>run default scripts</td></tr><tr><td>sV</td><td>enumerate versions</td></tr><tr><td>-p0-</td><td>search all ports [0 - 65535]</td></tr><tr><td>--min-rate</td><td>minimun packet sent for second</td></tr><tr><td>vvv</td><td>more verbosity</td></tr></tbody></table>

### Burp Suite

* Intercept request
* Forward request
* See WebServer value into response

<figure><img src="../../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

### Metasploit

We can use a metasploit module called http\_version to retrieve info regarding webserver

* use scannet/http/http\_version
* set rhosts \<target>
* run

### Curl

Curl displays source code content (passive method)

* curl http://\<target>&#x20;

### Discovering specific folders with Brute Force tools

Or try to discover information regarding folders presents only in determinated webserver such as cgi-bin (Apache) and HttpClient (IIS). We can research folder using brute force tools like as: dirb, gobuster, wefuzz.

## Web Server Scanning with Nikto

A great tool that help us for Web Server Scanning is [Nikto](https://github.com/sullo/nikto), that permit us to:

* Find SQL injection, XSS, and other common vulnerabilities
* Identify installed software (via headers, favicons, and files)
* Guess subdomains
* Includes support for SSL (HTTPS) websites
* Saves reports in plain text, XML, HTML or CSV
* “Fish” for content on web servers
* Report unusual headers
* Check for server configuration items like multiple index files, HTTP server options, and so on
* Has full HTTP proxy support
* Guess credentials for authorization (including many default username/password combinations)
* Is configured with a template engine to easily customize reports
* Exports to Metasploit

{% content-ref url="https://app.gitbook.com/s/iS3hadq7jVFgSa8k5wRA/practical-ethical-hacker-notes/tools/nikto" %}
[Nikto](https://app.gitbook.com/s/iS3hadq7jVFgSa8k5wRA/practical-ethical-hacker-notes/tools/nikto)
{% endcontent-ref %}

{% embed url="https://github.com/sullo/nikto" %}

## Automated Web Recon With OWASP Amass

{% embed url="https://github.com/owasp-amass/amass" %}

The [**OWASP Amass Project**](https://owasp.org/www-project-amass/) performs network mapping of attack surfaces and external asset discovery using open source information gathering and active reconnaissance techniques.

**Information Gathering Techniques Used:**

<table><thead><tr><th width="141">Technique</th><th>Data Sources</th></tr></thead><tbody><tr><td>APIs</td><td>360PassiveDNS, Ahrefs, AnubisDB, BeVigil, BinaryEdge, BufferOver, BuiltWith, C99, Chaos, CIRCL, DNSDB, DNSRepo, Deepinfo, Detectify, FOFA, FullHunt, GitHub, GitLab, GrepApp, Greynoise, HackerTarget, Hunter, IntelX, LeakIX, Maltiverse, Mnemonic, Netlas, Pastebin, PassiveTotal, PentestTools, Pulsedive, Quake, SOCRadar, Searchcode, Shodan, Spamhaus, Sublist3rAPI, SubdomainCenter, ThreatBook, ThreatMiner, URLScan, VirusTotal, Yandex, ZETAlytics, ZoomEye</td></tr><tr><td>Certificates</td><td>Active pulls (optional), Censys, CertCentral, CertSpotter, Crtsh, Digitorus, FacebookCT</td></tr><tr><td>DNS</td><td>Brute forcing, Reverse DNS sweeping, NSEC zone walking, Zone transfers, FQDN alterations/permutations, FQDN Similarity-based Guessing</td></tr><tr><td>Routing</td><td>ASNLookup, BGPTools, BGPView, BigDataCloud, IPdata, IPinfo, RADb, Robtex, ShadowServer, TeamCymru</td></tr><tr><td>Scraping</td><td>AbuseIPDB, Ask, Baidu, Bing, CSP Header, DNSDumpster, DNSHistory, DNSSpy, DuckDuckGo, Gists, Google, HackerOne, HyperStat, PKey, RapidDNS, Riddler, Searx, SiteDossier, Yahoo</td></tr><tr><td>Web Archives</td><td>Arquivo, CommonCrawl, HAW, PublicWWW, UKWebArchive, Wayback</td></tr><tr><td>WHOIS</td><td>AlienVault, AskDNS, DNSlytics, ONYPHE, SecurityTrails, SpyOnWeb, WhoisXMLAPI</td></tr></tbody></table>

**Perform automatic scan**

```bash
amass enum -d zonetransfer.me
amass enum -passive -d zonetransfer.me
amass enum -passive -d zonetransfer.me -src -ip -brute -dir /home/kali/Desktop/ZTME_Brute/
```

