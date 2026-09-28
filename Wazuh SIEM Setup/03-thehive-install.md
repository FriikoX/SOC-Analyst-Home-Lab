# 03 - TheHive (Case management software)
## What I did
I installed TheHive onto an existing Ubuntu 22.04 LTS
## VM specs
- OS: Ubuntu 22.04 LTS jammy
- RAM: 16384 MB
- CPUs: 4
- Disk: 50 GB

Those are the minimum required requirements for installing and running TheHive

## TheHive installation
I will be using TheHive for my case management and log entries, later on
connecting it with Shuffle so it can register logs through windows' telemetry and the wazuh agent that is installed on the my windows vm.

##Networking
The VM runs on a VirtualBox NAT Network, shared with the Windows endpoint and Wazuh SIEM so that the three machines can communicate. 
The dashboard is accessed from the host via port forwarding to `https://localhost:9000`.

#Issues along the way
Ran into a few setup problems before getting a clean install and a
working login. Full details in [troubleshooting.md](../troubleshooting.md):
- Netplan syntax & Indentation
- Unreachable Repository URL


## Result
Cassandra, Elasticsearch and TheHive are successfuly installed on the VMs, and ready to get to work!

**TheHive dashboard, already logged in, ready to work!
<img width="1918" height="1026" alt="TheHive dashboard" src="https://github.com/user-attachments/assets/74abfac0-df76-4889-ab0e-5225446b226f" />

