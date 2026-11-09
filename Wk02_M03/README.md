# Maltego OSINT Assignment: Domain to Email Discovery

## Project Overview

This project demonstrates the use of **Maltego Graph Desktop** on a Windows computer to perform Open-Source Intelligence (OSINT) investigation on an authorized organizational domain.

The objective is to identify publicly available email addresses associated with the target domain and visualize the relationship between the domain and discovered email entities.

## Tasks

### Task 1: Download and Install Maltego

- Downloaded Maltego from its official website.
- Installed Maltego on a Windows computer.
- Launched Maltego Graph Desktop.
- Logged in and configured the application.

**Software:** Maltego Graph Desktop 4.14.0  
**Operating System:** Windows 11

### Task 2: Email Address Discovery

**Target Organization Domain:** `networkwalks.com`

Steps performed:

1. Opened Maltego Graph Desktop.
2. Created a new graph.
3. Added a Domain entity.
4. Entered the target domain `networkwalks.com`.
5. Selected the available email discovery transform.
6. Executed the transform.
7. Examined the resulting entities and relationships.
8. Identified the publicly available email entity displayed in the graph.

### Results

The investigation graph displays the following relationship:

| Entity Type | Identified Information |
|---|---|
| Domain | networkwalks.com |
| Email Address | info@networkwalks.com |

**Result:** One email address is displayed in the investigation graph.

### Graph Visualization

The Maltego graph demonstrates the relationship between the target domain and its associated email entity.

![Maltego Domain to Email Graph](Screenshots/04-Email-Discovery-Graph.png)

### Tools Used

- Maltego Graph Desktop 4.14.0
- Windows 11
- Maltego Transform Library

## Conclusion

This assignment demonstrates how Maltego can be used for domain-based OSINT investigation and visual representation of relationships between internet domains and publicly available email information.

The investigation successfully produced a graph containing the target domain and an associated email entity.

**Note:** This investigation was conducted for educational purposes and within the scope of authorized OSINT research. The identified address represents the result observed during this investigation, not a guarantee that it is the organization's only email address.

## Author

**Asif Fg**  
Cybersecurity Learner | OSINT Enthusiast

