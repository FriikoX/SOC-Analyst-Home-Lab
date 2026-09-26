# 01 - VirtualBox and Windows VM (Endpoint)

## What I did
Installed VirtualBox and created a Windows 11 VM to act as the
monitored endpoint for this lab.

## VM specs
- OS: Windows 11
- RAM: 6144 MB
- CPUs: 2
- Disk: 40 GB

Resources were kept modest on this VM to leave more RAM and CPU
available for the Wazuh server VM, since the endpoint doesn't need

much to run Sysmon and (later) the Wazuh agent.

## Sysmon installation
Installed Sysmon (Sysinternals) to generate detailed telemetry
(process creation, network connections, and more) that a default
Windows install doesn't log on its own.

Used [Olaf Hartong's Sysmon-modular configuration](https://github.com/olafhartong/sysmon-modular)
as the base configuration.

Verified Sysmon was logging correctly via:
Event Viewer → Applications and Services Logs → Microsoft →
Windows → Sysmon → Operational

## Result
Sysmon is installed and actively logging events locally on the VM.
<img width="1021" height="770" alt="Sysmon-EventViewer-Operational" src="https://github.com/user-attachments/assets/ef8dabf9-aa64-4b80-b460-fd830a934e1d" />

## Next steps
- Put this VM on the same NAT Network as the Wazuh server VM
- Install the Wazuh agent and connect it to the manager
- Confirm Sysmon events are forwarded and visible in the Wazuh dashboard
