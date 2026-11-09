# Footprinting and Reconnaissance with Kali Linux Tools

**Week 2 – Module 1 Task (WK2-M1)**

| | |
|---|---|
| **Target domain** | `networkwalks.com` |
| **Prepared by** | `<Asif Fg>` |
| **Internship / Program** | `<Cyber Internship B084>` |
| **Submitted to** | `<Waqas Karim CCIE>` |
| **Date performed** | 09 November 2026 |
| **Platform** | Kali Linux |

---

## Table of Contents

1. [Scope and Authorization](#1-scope-and-authorization)
2. [Objective](#2-objective)
3. [Tools Used](#3-tools-used)
4. [Task 1 – WHOIS (Domain Registration)](#task-1--whois-domain-registration-details)
5. [Task 2 – WhatWeb (Technology Fingerprinting)](#task-2--whatweb-web-technology-fingerprinting)
6. [Task 3 – nslookup (DNS Resolution)](#task-3--nslookup-domain-to-ip-resolution)
7. [Task 4 – curl -I (HTTP Headers)](#task-4--curl--i-http-response-headers)
8. [Task 5 – wafw00f (WAF Detection)](#task-5--wafw00f-web-application-firewall-detection)
9. [Task 6 – dnsrecon (DNS Enumeration)](#task-6--dnsrecon-dns-record-enumeration)
10. [Summary of Findings](#summary-of-findings)
11. [Conclusion](#conclusion)

---

## 1. Scope and Authorization

This assessment was carried out **with explicit authorization** to perform testing on the target below.

| Item | Detail |
|---|---|
| **Authorized target** | `networkwalks.com` |
| **Authorized by** | `<Name / Organization granting permission>` |
| **Testing type** | Passive and light active reconnaissance only |
| **Out of scope** | Exploitation, brute-forcing, denial-of-service, or any access to non-public data |

All commands were limited to information-gathering and generated minimal traffic (for example, `wafw00f` sent only 2 requests).

---

## 2. Objective

To gather publicly available information about the target and understand its external footprint, including:

- Domain registration and ownership details
- Web technologies and server software in use
- IP address and DNS configuration
- HTTP response headers and security posture
- Presence of a Web Application Firewall (WAF)
- Full DNS record set (SOA, NS, MX, A, TXT, SRV)

---

## 3. Tools Used

| # | Tool | Purpose |
|---|------|---------|
| 1 | `whois` | Domain registration details |
| 2 | `whatweb` | Web technology fingerprinting |
| 3 | `nslookup` | Resolve domain to IP address |
| 4 | `curl -I` | Read HTTP response headers |
| 5 | `wafw00f` | Detect Web Application Firewall |
| 6 | `dnsrecon` | Enumerate DNS records |

---

## Task 1 – WHOIS (Domain Registration Details)

**Objective:** Find domain registration details.

**Command**

```bash
whois networkwalks.com
```

**Screenshot**

![Task 1 - whois](screenshots/task1-whois.png)

**Output (key records)**

> The long legal / terms-of-use notices printed by the WHOIS servers are omitted here for readability. They are visible in the screenshot.

```text
Domain Name: NETWORKWALKS.COM
Registry Domain ID: 2452319255_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.godaddy.com
Registrar URL: http://www.godaddy.com
Updated Date: 2025-11-12T10:08:43Z
Creation Date: 2019-11-06T22:51:46Z
Registry Expiry Date: 2027-11-06T22:51:46Z
Registrar: GoDaddy.com, LLC
Registrar IANA ID: 146
Registrar Abuse Contact Email: abuse@godaddy.com
Registrar Abuse Contact Phone: 480-624-2505
Domain Status: clientDeleteProhibited
Domain Status: clientRenewProhibited
Domain Status: clientTransferProhibited
Domain Status: clientUpdateProhibited
Name Server: NS6135.HOSTGATOR.COM
Name Server: NS6136.HOSTGATOR.COM
DNSSEC: unsigned
```

Registrar-level record (GoDaddy):

```text
Registrant Name: Registration Private
Registrant Organization: Domains By Proxy, LLC
Registrant Street: 100 S. Mill Ave, Suite 1600
Registrant City: Tempe
Registrant State/Province: Arizona
Registrant Postal Code: 85281
Registrant Country: US
Registrant Email: https://www.godaddy.com/whois/results.aspx?domain=networkwalks.com&action=contactDomainOwner
Name Server: NS6135.HOSTGATOR.COM
Name Server: NS6136.HOSTGATOR.COM
Name Server: NS29.DOMAINCONTROL.COM
Name Server: NS30.DOMAINCONTROL.COM
DNSSEC: unsigned
```

**Key Findings**

- Registered through **GoDaddy.com, LLC** (IANA ID 146).
- Created on **2019-11-06**, expires on **2027-11-06**; last updated **2025-11-12**.
- Registrant details are hidden behind a privacy service (**Domains By Proxy, LLC**).
- All four `client*Prohibited` locks are set, which helps protect against unauthorized transfer or deletion.
- Name servers are listed at **HostGator**, and the registrar record also lists GoDaddy (`DOMAINCONTROL.COM`) name servers.
- **DNSSEC is unsigned**, so DNS responses are not cryptographically validated.

---

## Task 2 – WhatWeb (Web Technology Fingerprinting)

**Objective:** Fingerprint the web technologies used by the site.

**Command**

```bash
whatweb networkwalks.com
```

**Screenshot**

![Task 2 - whatweb](screenshots/task2-whatweb.png)

**Output**

```text
http://networkwalks.com [301 Moved Permanently] Apache, Cookies[__wpdm_client], Country[UNITED STATES][US], HTTPServer[Apache], HttpOnly[__wpdm_client], IP[192.232.216.135], RedirectLocation[https://networkwalks.com/], UncommonHeaders[permissions-policy,x-redirect-by,upgrade,referrer-policy,x-endurance-cache-level,x-nginx-cache]

https://networkwalks.com [200 OK] Apache, Bootstrap[7.1.4], Cookies[__wpdm_client], Country[UNITED STATES][US], Email[info@networkwalks.com], Frame, Google-Tag-Manager, HTML5, HTTPServer[Apache], HttpOnly[__wpdm_client], IP[192.232.216.135], JQuery[3.7.1], MetaGenerator[WordPress 7.1.4,WordPress Download Manager 3.3.76], Open-Graph-Protocol[website], Script[4684NR-IPIB&amp;pidnVar2=50511&amp;prtVar2=7&amp;scvVar2=12,application/json,application/ld+json,module,speculationrules,text/javascript], Title[Networkwalks Academy], UncommonHeaders[permissions-policy,link,upgrade,referrer-policy,x-endurance-cache-level,x-nginx-cache], WordPress[7.1.4]

https://networkwalks.com/ [200 OK] Apache, Bootstrap[7.1.4], Country[UNITED STATES][US], Email[info@networkwalks.com], Frame, Google-Tag-Manager, HTML5, HTTPServer[Apache], IP[192.232.216.135], JQuery[3.7.1], MetaGenerator[WordPress 7.1.4,WordPress Download Manager 3.3.76], Open-Graph-Protocol[website], Script[4684NR-IPIB&amp;pidnVar2=50511&amp;prtVar2=7&amp;scvVar2=12,application/json,application/ld+json,module,speculationrules,text/javascript], Title[Networkwalks Academy], UncommonHeaders[permissions-policy,link,upgrade,referrer-policy,x-endurance-cache-level,x-nginx-cache], WordPress[7.1.4]
```

**Key Findings**

| Attribute | Value |
|---|---|
| Web server | Apache |
| CMS | WordPress 7.1.4 |
| Plugin | WordPress Download Manager 3.3.76 |
| JavaScript library | jQuery 3.7.1 |
| Analytics / tags | Google Tag Manager |
| Site title | Networkwalks Academy |
| Server IP | 192.232.216.135 (United States) |
| Public contact email | info@networkwalks.com |
| Cookie | `__wpdm_client` (flagged `HttpOnly`) |

- HTTP requests are redirected with a **301** to HTTPS.
- The `Bootstrap[7.1.4]` result matches the WordPress version string, so it is most likely a WhatWeb misdetection and should be verified manually.

---

## Task 3 – nslookup (Domain to IP Resolution)

**Objective:** Resolve the domain to its IP address.

**Command**

```bash
nslookup networkwalks.com
```

**Screenshot**

![Task 3 - nslookup](screenshots/task3-nslookup.png)

**Output**

```text
Server:         192.168.100.1
Address:        192.168.100.1#53

Non-authoritative answer:
Name:   networkwalks.com
Address: 192.232.216.135
```

**Key Findings**

- `networkwalks.com` resolves to **192.232.216.135**, which matches the IP reported by WhatWeb.
- The answer is **non-authoritative**, meaning it came from the local resolver (`192.168.100.1`) rather than directly from the domain's name servers.

---

## Task 4 – curl -I (HTTP Response Headers)

**Objective:** Read the HTTP response headers.

**Command**

```bash
curl -I https://networkwalks.com
```

**Screenshot**

![Task 4 - curl headers](screenshots/task4-curl.png)

**Output**

```text
HTTP/2 200
permissions-policy: private-state-token-redemption=(self "https://www.google.com" "https://www.gstatic.com" "https://recaptcha.net" "https://challenges.cloudflare.com" "https://hcaptcha.com"), private-state-token-issuance=(self "https://www.google.com" "https://www.gstatic.com" "https://recaptcha.net" "https://challenges.cloudflare.com" "https://hcaptcha.com")
link: <https://networkwalks.com/wp-json/>; rel="https://api.w.org/", <https://networkwalks.com/wp-json/wp/v2/pages/53>; rel="alternate"; title="JSON"; type="application/json", <https://networkwalks.com/>; rel=shortlink
set-cookie: __wpdm_client=b8526e9cdca14a645083c9f16f84fdf7; path=/; domain=networkwalks.com; secure; HttpOnly
referrer-policy: no-referrer-when-downgrade
x-endurance-cache-level: 0
x-nginx-cache: WordPress
content-type: text/html; charset=UTF-8
date: Mon, 09 Nov 2026 05:56:45 GMT
server: Apache
```

**Key Findings**

- The site responds over **HTTP/2** with status **200 OK**.
- `server: Apache` is disclosed in the headers.
- `x-nginx-cache` and `x-endurance-cache-level` indicate a **caching layer** in front of WordPress.
- The `link` header exposes the **WordPress REST API** endpoint (`/wp-json/`).
- The cookie is set with `Secure` and `HttpOnly` flags, which is good practice.
- A `permissions-policy` header is present.
- In this response, `Strict-Transport-Security`, `Content-Security-Policy`, `X-Frame-Options` and `X-Content-Type-Options` headers were **not observed**.

---

## Task 5 – wafw00f (Web Application Firewall Detection)

**Objective:** Detect whether a WAF protects the site.

**Command**

```bash
wafw00f networkwalks.com
```

**Screenshot**

![Task 5 - wafw00f](screenshots/task5-wafw00f.png)

**Output**

```text
                   ______
                  /      \
                 (  Woof! )
                  \  ____/                      )
                  ,,                           ) (_
             .-. -    _______                 ( |__|
            ()``; |==|_______)                .)|__|
            / ('        /|\                  (  |__|
        (  /  )        / | \                  . |__|
         \(_)_))      /  |  \                   |__|

                    ~ WAFW00F : v2.4.2 ~
    The Web Application Firewall Fingerprinting Toolkit

[*] Checking https://networkwalks.com
[+] The site https://networkwalks.com is behind ModSecurity (SpiderLabs) WAF.
[~] Number of requests: 2
```

**Key Findings**

- The site is protected by **ModSecurity (SpiderLabs)**, an open-source WAF.
- Detection required only **2 requests**.
- A WAF is expected to filter common web attacks such as SQL injection and XSS, so any later testing should account for it.

---

## Task 6 – dnsrecon (DNS Record Enumeration)

**Objective:** Enumerate all DNS records for the domain.

**Command**

```bash
dnsrecon -d networkwalks.com
```

**Screenshot**

![Task 6 - dnsrecon](screenshots/task6-dnsrecon.png)

**Output**

```text
2026-11-09T01:02:56.081066-0500 INFO Starting enumeration for domain: networkwalks.com
2026-11-09T01:02:56.082070-0500 INFO std: Performing General Enumeration against: networkwalks.com...
2026-11-09T01:02:56.622582-0500 ERROR No answer for DNSSEC query for networkwalks.com
2026-11-09T01:02:56.945685-0500 INFO     SOA ns6135.hostgator.com 50.87.144.87
2026-11-09T01:02:57.003456-0500 INFO     NS ns6135.hostgator.com 50.87.144.87
2026-11-09T01:02:57.555113-0500 INFO     Bind Version for 50.87.144.87 "9.16.23-RH"
2026-11-09T01:02:57.555280-0500 INFO     NS ns6136.hostgator.com 192.232.216.131
2026-11-09T01:02:58.067332-0500 INFO     Bind Version for 192.232.216.131 "9.16.23-RH"
2026-11-09T01:02:58.884648-0500 INFO     MX mail.networkwalks.com 192.232.216.135
2026-11-09T01:02:59.143407-0500 INFO     A networkwalks.com 192.232.216.135
2026-11-09T01:02:59.937719-0500 INFO     TXT networkwalks.com v=spf1 +a +mx +ip4:50.87.144.87 +include:websitewelcome.com ~all
2026-11-09T01:02:59.938006-0500 INFO     TXT networkwalks.com google-site-verification=rr04eRmqHoWY3XemnizDNVK4q75X-Ij-mjgEeg-UsYI
2026-11-09T01:03:00.729846-0500 INFO Enumerating SRV Records
2026-11-09T01:03:04.967827-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.204.15 443
2026-11-09T01:03:04.968598-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.203.15 443
2026-11-09T01:03:04.969068-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.203.11 443
2026-11-09T01:03:04.969375-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.204.11 443
2026-11-09T01:03:04.969641-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.203.9 443
2026-11-09T01:03:04.970006-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.204.14 443
2026-11-09T01:03:04.971103-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.204.9 443
2026-11-09T01:03:04.972065-0500 INFO     SRV _autodiscover._tcp.networkwalks.com cpanelemaildiscovery.cpanel.net 184.94.203.14 443
2026-11-09T01:03:04.978145-0500 INFO 8 Records Found
2026-11-09T01:03:04.978529-0500 INFO Completed enumeration for domain: networkwalks.com
```

**Key Findings**

| Record | Value |
|---|---|
| SOA / NS | `ns6135.hostgator.com` (50.87.144.87), `ns6136.hostgator.com` (192.232.216.131) |
| A | `networkwalks.com` → 192.232.216.135 |
| MX | `mail.networkwalks.com` → 192.232.216.135 |
| TXT (SPF) | `v=spf1 +a +mx +ip4:50.87.144.87 +include:websitewelcome.com ~all` |
| TXT (verification) | Google site verification token |
| SRV | 8 `_autodiscover._tcp` records pointing to cPanel email discovery |

- The name servers disclose their **BIND version (9.16.23-RH)**, which is unnecessary information disclosure.
- The mail server and web server share the **same IP address** (192.232.216.135).
- The SPF record ends in `~all` (**soft fail**), which is weaker than a hard fail (`-all`).
- The DNSSEC query returned no answer, consistent with the `DNSSEC: unsigned` result from WHOIS.

---

## Summary of Findings

| Area | Finding |
|---|---|
| Registrar | GoDaddy.com, LLC (privacy-protected via Domains By Proxy) |
| Domain age | Created 2019-11-06, expires 2027-11-06 |
| Hosting / DNS | HostGator name servers; IP 192.232.216.135 |
| Web stack | Apache, WordPress 7.1.4, WP Download Manager 3.3.76, jQuery 3.7.1 |
| WAF | ModSecurity (SpiderLabs) |
| Transport | HTTP redirects to HTTPS; HTTP/2 supported |
| Email | MX at `mail.networkwalks.com`; SPF uses soft fail (`~all`) |
| DNSSEC | Not enabled |

**Observations worth reviewing**

1. Server software, CMS and plugin versions are visible to anyone, which makes targeted lookups easier.
2. BIND version is disclosed by the name servers.
3. Common security headers (HSTS, CSP, X-Frame-Options, X-Content-Type-Options) were not seen in the response.
4. SPF uses soft fail and DNSSEC is not enabled.
5. The WordPress REST API endpoint is advertised in the response headers.

---

## Conclusion

Using six standard Kali Linux tools, this exercise built a clear picture of the external footprint of `networkwalks.com`: who registered it, where it is hosted, which technologies it runs, how its DNS is configured, and that it sits behind a ModSecurity WAF. No exploitation was attempted. The findings above would be the starting point for deeper, in-scope testing.

---

## Disclaimer

This report was created for educational purposes as part of an internship assignment. Testing was performed only on the authorized target. Do not run these tools against systems you do not own or have explicit written permission to test.

---

## Repository Structure

```text
.
├── README.md
└── screenshots/
    ├── task1-whois.png
    ├── task2-whatweb.png
    ├── task3-nslookup.png
    ├── task4-curl.png
    ├── task5-wafw00f.png
    └── task6-dnsrecon.png
```
