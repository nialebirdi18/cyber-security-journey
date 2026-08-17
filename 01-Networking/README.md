# Networking

This folder contains a practical, hands-on networking learning path for cybersecurity. Use these headings as a checklist: add notes, diagrams, worked examples, and lab exercises under each section.

## Overview

Networking is a fundamental skill for cybersecurity — it lets you understand how systems communicate, inspect traffic for anomalies, and design detections. Start with concepts, then practice with packet captures, scanning, and small lab topologies.

## OSI Model & TCP/IP Stack

- Brief explanation of each layer and responsibilities
- Common protocols per layer and how attacks map to layers
- How to map network evidence (packets/logs) to OSI layers

## Subnetting & CIDR

- How to calculate network, broadcast, and host ranges from CIDR
- Quick reference:
  - /24 = 256 addresses (254 hosts)
  - /25 = 128 addresses (126 hosts)
  - /16 = 65,536 addresses (65,534 hosts)
- Example exercises (add answers in notes.md):
  - Given 192.168.10.130/26 — network, broadcast, host range?
  - Divide 10.0.0.0/24 into four equal subnets (what prefixes?)

## Common Protocols & Ports

- DNS (53), HTTP (80), HTTPS (443), SSH (22), RDP (3389), SMB (445), LDAP (389/636), DHCP (67/68)
- What to look for in packet captures (e.g., DNS exfiltration, suspicious TLS fingerprints)

## TCP vs UDP

- TCP: connection-oriented, three-way handshake, sequence numbers, reliable
- UDP: connectionless, used for DNS, streaming, less overhead
- Implications for detection and packet analysis

## Routing, Switching & VLANs

- ARP basics and common ARP-related attacks
- MAC address tables and switch behavior
- VLAN tagging (802.1Q) and common misconfigurations (VLAN hopping)

## NAT / PAT / DMZ

- Purpose and typical deployment patterns
- How NAT affects forensic analysis and logging

## Packet Capture & Wireshark

- How to capture traffic: tcpdump, tshark, Wireshark
- Useful display filters examples:
  - ip.addr == 10.0.0.5
  - tcp.port == 445
  - dns.qry.name contains "example"
- Follow TCP stream, Analyze -> Conversations, and identify TLS handshakes

## Tools & Commands

Linux / macOS:
- ip addr show
- ip route
- ss -tuln
- sudo tcpdump -i any -w /tmp/capture.pcap
- tshark -r capture.pcap -Y "http && ip.src==192.168.1.10"

Windows:
- ipconfig /all
- route print
- netstat -ano
- Use Wireshark (Npcap) for privileged captures

Scanning & analysis:
- nmap -sS -sC -sV -O target
- Zeek/Bro and Suricata for network monitoring

## Recommended Labs

1. Packet capture basics
   - Setup: two VMs (client/server) on a host-only network
   - Generate HTTP and DNS traffic, capture with tcpdump, analyze in Wireshark
   - Tasks: filter DNS, follow TCP stream, identify certificate exchanges

2. Subnetting practice
   - Create networks with different CIDR masks and calculate ranges

3. Port scanning & service fingerprinting
   - Use nmap to identify services, versions, and map results to CVEs

4. IDS/Detection exercise
   - Run Suricata or Snort in the lab, craft traffic that triggers rules, and tune alerts

## Cheatsheet (quick reference)
- Capture: sudo tcpdump -i any -w capture.pcap
- Filter: tcpdump -r capture.pcap "port 53"
- Wireshark display filters: http, dns, ip.addr==1.2.3.4, tcp.port==22

## Example file structure for this folder
- notes.md — detailed notes and diagrams
- labs/ — lab exercises (lab1.md, lab2.md)
- captures/ — example PCAP files
- cheatsheets.md — printable quick references

## Resources
- "Computer Networking: A Top-Down Approach" — Kurose & Ross
- Wireshark documentation & sample captures: https://www.wireshark.org
- Practical subnetting guides and online calculators

## Next steps
- Add `notes.md` with worked subnetting problems and diagrams
- Add `labs/` with at least one step-by-step packet-capture lab and expected outputs
- Add a small pcap to `captures/` for practice and an answer key in labs
