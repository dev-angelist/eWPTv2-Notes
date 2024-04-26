# 2.1.1 DNS Recon

## DNSRecon

[DNSRecon](https://www.kali.org/tools/dnsrecon/) is a Python script that provides the ability to perform:

* Check all NS Records for Zone Transfers.
* Enumerate General DNS Records for a given Domain (MX, SOA, NS, A, AAAA, SPF and TXT).
* Perform common SRV Record Enumeration.
* Top Level Domain (TLD) Expansion.
* Check for Wildcard Resolution.
* Brute Force subdomain and host A and AAAA records given a domain and a wordlist.
* Perform a PTR Record lookup for a given IP Range or CIDR.
* Check a DNS Server Cached records for A, AAAA and CNAME
* Records provided a list of host records in a text file to check.
* Enumerate Hosts and Subdomains using Google.

#### Command Examples

Scan a domain and save the results to a SQLite database:

```
# dnsrecon --domain example.com --db path/to/database.sqlite
```

Scan a domain, specifying the nameserver and performing a zone transfer:

```
# dnsrecon --domain example.com --name_server nameserver.example.com --type axfr
```

Scan a domain, using a brute-force attack and a dictionary of subdomains and hostnames:

```
# dnsrecon --domain example.com --dictionary path/to/dictionary.txt --type brt
```

Scan a domain, performing a reverse lookup of IP ranges from the SPF record and saving the results to a JSON file:

```
# dnsrecon --domain example.com -s --json
```

Scan a domain, performing a Google enumeration and saving the results to a CSV file:

```
# dnsrecon --domain example.com -g --csv
```

Scan a domain, performing DNS cache snooping:

```
# dnsrecon --domain example.com --type snoop --name_server nameserver.example.com --dictionary path/to/dictionary.txt
```

Scan a domain, performing zone walking:

```
# dnsrecon --domain example.com --type zonewalk
```

### DNSdumpster

[DNSdumpster](https://dnsdumpster.com/) is a domain research tool that can discover hosts related to a domain. Finding visible hosts from the attackers perspective is an important part of the security assessment process.

No brute force subdomain enumeration is used as is common in dns recon tools that enumerate subdomains. We use open source intelligence resources to query for related domain data. It is then compiled into an actionable resource for both attackers and defenders of Internet facing systems.

More than a simple DNS lookup this tool will discover those hard to find sub-domains and web hosts. The search relies on data from our crawls of the Alexa Top 1 Million sites, Search Engines, Common Crawl, Certificate Transparency, Max Mind, Team Cymru, Shodan and scans.io.
