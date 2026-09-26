# 02 - Wazuh Server Install (Ubuntu)

## What I did
Created an Ubuntu 22.04 Server VM in VirtualBox (8 GB RAM, 4 CPUs,
60 GB disk) to act as the Wazuh server.

Installed Wazuh 4.7 (all-in-one: indexer, manager, filebeat, and
dashboard) using the official install script:

​```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
​```

## Networking
The VM runs on a VirtualBox NAT Network, shared with the Windows
endpoint so the two machines can communicate. The dashboard is
accessed from the host via port forwarding to `https://localhost:8443`.

## Issues along the way
Ran into a few setup problems before getting a clean install and a
working login. Full details in [troubleshooting.md](../troubleshooting.md):
- Unattended VM installation causing login/version issues
- Disk-full error during the dashboard install (LVM misconfiguration)
- Admin password rejected due to Wazuh's character requirements
- Dashboard unreachable from the host browser (NAT networking)

## Result
Installation completed successfully. All components (indexer, manager,
filebeat, dashboard) are running, and the dashboard is accessible.

**Console output confirming a successful install:**
<img width="791" height="688" alt="Successful-Installation-Console" src="https://github.com/user-attachments/assets/f14f576d-a7d4-4168-9d24-e93eb2537bd6" />


**Wazuh dashboard, logged in and ready:**
<img width="1919" height="1032" alt="Successful-Installation-Interface" src="https://github.com/user-attachments/assets/72e1c657-7ff5-4817-b43f-a3e24b1913da" />

The dashboard currently shows 0 agents, since no endpoints have been
connected yet. Next step: install the Wazuh agent on the Windows VM
and connect it to this manager.
