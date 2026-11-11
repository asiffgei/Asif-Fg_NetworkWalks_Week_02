# Network Host Discovery Using Zenmap (Nmap)

## Project Overview
This practical lab demonstrates how to perform local network host discovery using **Zenmap**, the graphical user interface for Nmap, on a Windows PC.

The objective was to identify active devices on a local area network (LAN), collect their IP and MAC addresses, count live hosts, and generate a network topology report in PDF format.

## Objectives
- Install Zenmap on Windows from the official website.
- Identify the local IP address and LAN subnet.
- Perform a Ping Scan to discover live hosts.
- Count the number of active hosts on the subnet.
- Identify the IP addresses of discovered hosts.
- Identify the MAC addresses of discovered hosts.
- Generate and save the network topology in PDF format.

## Lab Environment

| Component | Details |
|---|---|
| Operating System | Windows |
| Tool | Zenmap (Nmap GUI) |
| Scanning Technique | Ping Scan |
| Network IP | `192.168.100.3` |
| Subnet Mask | `255.255.255.0` |
| Network Subnet | `192.168.100.0/24` |
| Default Gateway | `192.168.100.1` |

## Tasks Performed

### Task 1: Download and Install Zenmap
Downloaded and installed Zenmap on the Windows PC using the official Nmap website.

Official Website: https://nmap.org/

### Task 2: Find Local IP Address and LAN Subnet
Used Windows Command Prompt and the `ipconfig` command to identify the local network configuration.

### Task 3: Discover Live Hosts
Opened Zenmap, entered the local LAN subnet, selected the Ping Scan profile, and initiated the scan.

**Nmap Command:**
```bash
nmap -sn 192.168.100.0/24
```

### Task 4, 5 & 6: Analyze Live Hosts
Recorded the following information from the scan results:
- Total number of live hosts.
- IP addresses of discovered devices.
- MAC addresses of discovered devices.

Detailed results are available in the `host-discovery-results.txt` file.

### Task 7: Generate Network Topology
Generated the network topology using Zenmap and exported/saved the topology report in PDF format.

## Project Screenshots

The following screenshots document the practical implementation:

1. `01-network-configuration.png` – Local IP and subnet configuration.
2. `02-zenmap-ping-scan.png` – Zenmap Ping Scan and discovered hosts.
3. `03-network-topology.png` – Network topology visualization.

## Project Files

```text
Zenmap-Network-Discovery/
│
├── README.md
│
├── screenshots/
│   ├── 01-network-configuration.png
│   ├── 02-zenmap-ping-scan.png
│   └── 03-network-topology.png
│
├── host-discovery-results.txt
│
└── network-topology.pdf
```

## Key Learning Outcomes
- Understanding IPv4 addressing and subnetting.
- Identifying devices connected to a local network.
- Understanding host discovery techniques.
- Working with Zenmap and Nmap.
- Reading IP and MAC address information.
- Visualizing network topology.
- Documenting practical cybersecurity lab results.

## Conclusion
Successfully completed a local network host discovery exercise using Zenmap. Identified active hosts within the local `/24` subnet, documented their IP and MAC addresses, and generated a network topology report.

This practical exercise strengthened my understanding of network reconnaissance and basic network administration.

## Author
**Asif Fg**  
Cybersecurity Learner | Founder & CEO, Cyber404 Academy

## Disclaimer
This practical exercise was performed on my own local network for educational purposes. Network scanning should only be conducted on networks for which you have explicit authorization.
