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
| Ubuntu Server | Wazuh server (manager, indexer, dashboard) | Planned |
| Ubuntu Server | TheHive + Shuffle | Planned |
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
- [ ] Wazuh server installed (Ubuntu)
- [ ] Sysmon installed on Windows VM
- [ ] Wazuh agent connected to server
- [ ] TheHive and Shuffle integration
- [ ] First attack scenario and investigation

## Investigations
_Links to each scenario write-up will be added here as I complete them._

## Lessons Learned & Troubleshooting
_Problems I ran into and how I solved them will be added here._

**1** _During installing the Wazuh SIEM server on my Ubuntu VM, I ran into a problem where
the ubuntu's guided LVM partitioning only allocated half the disk to the root volume by default.
As we know, Wazuh requires 50 GB Storage at least for 1-25 agents, working on logs that are stored on the said server.
I managed to fix it by extending the logical volume with lvextend and resize2fs instead of reinstalling.._

## About Me
Cybersecurity student at the University of Telecommunications and Posts.

LinkedIn: <your LinkedIn link> https://www.linkedin.com/in/alexander-penchev-b136a0412/

