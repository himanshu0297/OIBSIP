# Basic Network Scanning with Nmap

## Objective
To perform a basic network scan using Nmap and identify open ports and services.

## Tools Used
- Nmap
- Windows Command Prompt

## Commands Used
ipconfig

nmap 192.168.1.8

nmap -sV 192.168.1.8

nmap -O 192.168.1.8

## Scan Results
Open Ports:
- 135/tcp - Microsoft RPC
- 139/tcp - NetBIOS
- 445/tcp - Microsoft-DS
- 5432/tcp - PostgreSQL

Operating System:
- Microsoft Windows 11

## Conclusion
Successfully scanned the local machine using Nmap and identified open ports, services, and the operating system.
