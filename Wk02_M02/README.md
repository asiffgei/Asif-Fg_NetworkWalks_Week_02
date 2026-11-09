# GHDB Dork-Based Reconnaissance Assignment

## Overview
This repository documents the use of Google Hacking Database (GHDB) dorks to perform
footprinting and open-source discovery through search engines only, without direct
interaction with any target system. Two exercises are covered:

1. Identifying categories of exposed/misconfigured devices indexed via search engines
2. Locating freely available, legally downloadable PDF resources using dork techniques

## Background
GHDB is a curated collection of search queries ("dorks") that combine standard search
operators in ways that surface content unintentionally exposed by misconfigured web
servers — open directories, default device interfaces, login pages, and public files.
It is maintained and hosted at exploit-db.com and is used by security researchers to
locate and responsibly report these exposures.

## Methodology
- All discovery was performed passively via Google search operators (`intitle:`,
  `inurl:`, `filetype:`, `site:`, boolean operators)
- No direct connection, login attempt, or interaction was made with any system beyond
  what a standard search result/page load represents
- Dorks were sourced from GHDB categories and adapted/combined for the assignment scope
- Screenshots were captured of search results and, where applicable, publicly
  accessible landing pages

## Task 1: Exposed Device Discovery (Methodology)
This task explores the class of GHDB dorks (e.g. `intitle:"webcamXP" inurl:8080`,
`intitle:"Device(IP CAMERA)"`) used to surface internet-facing devices with
default or no authentication. 

[Document the dork *patterns* and categories here, with screenshots of search
result pages. Avoid publishing a working-access table of real third-party
devices — see note below.]

**Responsible handling note:** Live, unsecured camera feeds belonging to third
parties should not be published as "verified working" targets in coursework or
public repos, even when discovered via legitimate open-source search. If your
assignment requires per-target documentation, consider using exploit-db's own
sample GHDB entries as citations rather than screenshots proving live access.

## Task 2: Freely Downloadable Mathematics eBooks
| No. | Link | Dork Used |
|-----|------|-----------|
| 1   | ...  | `intitle:"index of" "Core Books" mathematics filetype:pdf` |
| 2   | ...  | `intitle:"index of" "mathematic-set" filetype:pdf` |
...

(Insert your full 10-entry table + screenshots here)

## Tools & Operators Used
| Operator | Purpose |
|----------|---------|
| `intitle:` | Matches text in the page title (e.g. directory listing names) |
| `inurl:` | Matches text in the URL path |
| `filetype:` | Restricts results to a specific file extension |
| `site:` | Restricts results to a specific domain |
| `-inurl:(htm\|html)` | Excludes rendered HTML pages to isolate raw directory indexes |

## Ethical & Legal Notes
- All searches were conducted passively through Google; no exploitation,
  authentication bypass, or unauthorized access occurred
- Findings are documented for educational purposes under [course/program name]
- This repository does not publish credentials, exploit code, or working access
  paths to third-party private systems

## Author
Asif — Cyber404 Academy / [internship or course name]
