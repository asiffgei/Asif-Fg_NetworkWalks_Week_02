# theHarvester OSINT Practical Assignment

## Project Overview

This project demonstrates passive Open-Source Intelligence (OSINT) gathering using theHarvester tool in Kali Linux.

The objective is to discover publicly available email addresses, subdomains, hostnames, and IP addresses associated with the target organization.

**Target Domain:** `microsoft.com`

## Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux |
| Tool | theHarvester |
| Version | 4.11.1 |
| Target | microsoft.com |
| Methodology | Passive OSINT |

---

## Task 1: Email and Subdomain Discovery Using Baidu

**Objective:** Find email addresses and subdomains associated with microsoft.com using Baidu with a result limit of 1000.

### Command

```bash
theHarvester -d microsoft.com -l 1000 -b baidu
```

### Results

| Finding | Count |
|---|---:|
| Email Addresses | 0 |
| Hosts | 2 |
| IP Addresses | 0 |
| People | 0 |

### Discovered Hosts

1. learn.microsoft.com
2. spf-c.microsoft.com

### Analysis

Baidu returned two hostnames associated with the target domain. No email addresses or IP addresses were returned during this search.

---

## Task 2: Email and Subdomain Discovery Using All Sources

**Objective:** Gather publicly available information using all supported theHarvester sources with a result limit of 50.

### Command

```bash
theHarvester -d microsoft.com -l 50 -b all
```

### Results

| Finding | Count |
|---|---:|
| Email Addresses | 3 |
| Hosts Reported | 864 |
| IP Addresses | 12 |
| People | 0 |

### Discovered Email Addresses

1. dotnet-docker-bot@microsoft.com
2. opencode@microsoft.com
3. secure@microsoft.com

### Sample Discovered Hosts

1. account.microsoft.com
2. azure.microsoft.com
3. careers.microsoft.com
4. blogs.microsoft.com
5. learn.microsoft.com
6. admin.microsoft.com
7. api.microsoft.com

### Analysis

The combined search returned three email addresses, 864 reported host entries, and 12 IP addresses.

Some data providers required API keys, while others encountered connectivity or processing errors. Therefore, the results represent the information returned by the successfully responding sources.

The reported host count should not be interpreted as a count of unique or verified live subdomains.

---

## Tools Used

- Kali Linux
- theHarvester 4.11.1
- Baidu
- Public OSINT data sources

## Conclusion

This practical demonstrated how theHarvester can be used for passive reconnaissance and information gathering.

In Task 1, Baidu returned two hosts and no email addresses.

In Task 2, the combined sources returned three email addresses, 864 host entries, and 12 IP addresses.

The exercise provided practical experience in domain footprinting, email discovery, subdomain enumeration, and OSINT analysis.

## Disclaimer

This assignment is intended for educational purposes and authorized OSINT research. The investigation used publicly available information and did not involve exploitation or unauthorized access.

## Author

**Asif Fg**

Cybersecurity Learner | OSINT Enthusiast
