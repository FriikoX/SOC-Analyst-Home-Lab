# SOC Home Lab: Wazuh, Sysmon, TheHive & Shuffle

A virtual lab for practicing security monitoring, alert triage, and incident
investigation, built with open-source tools.

## Goal
Hello, my name is Alexander!
Thank you for the attention you're giving me by reading this README file, and frankly, here I will be
documenting my progress, and therefore, building experience, one step at a time.
I am an aspiring cybersecurity professional who acquired CompTIA's Network+ certification, currently going
through CompTIA's Security+ course, and I'm actively seeking job opportunities. 
This project is where I build hands-on experience with log collection, detection, investigation, and documenting
incidents the way an analyst would for a client. Let's begin!

## Lab Architecture
All machines run as virtual machines in VirtualBox on a Windows host.

| VM | Role | Status |
|---|---|---|
| Windows 11 | Monitored endpoint (Sysmon + Wazuh agent) | Created |
| Ubuntu Server | Wazuh server (manager, indexer, dashboard) | Created |
| Ubuntu Server | TheHive + Shuffle | Created/ToBeDone |
| Kali Linux | Attack simulation | Planned |


## Tools
- **VirtualBox**: virtualization
- **Wazuh**: SIEM / log analysis and alerting
- **Sysmon**: detailed endpoint telemetry on Windows
- **TheHive**: case management
- **Shuffle**: SOAR / alert automation

## Progress
- [x] VirtualBox installed
- [x] Windows 11 VM created
- [x] Wazuh server installed (Ubuntu)
- [x] Sysmon installed on Windows VM
- [x] Wazuh agent connected to server
- [x] First attack scenario and investigation
- [ ] TheHive and Shuffle integration

## Investigations
[Check out investigations!](/Investigations/investigations.md)

## Lessons Learned & Troubleshooting
See [Troubleshooting Solutions](troubleshooting.md) for issues I encountered
and how I resolved them.

## About Me
Cybersecurity student at the University of Telecommunications and Posts.

LinkedIn: <your LinkedIn link> https://www.linkedin.com/in/alexander-penchev-b136a0412/

