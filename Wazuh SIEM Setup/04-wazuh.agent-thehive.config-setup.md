# 04 - Wazuh agent connection and TheHive configuration

## What I did
I configured TheHive, checked if every host was properly configured and connected altogether.
Gave permissions to cassandra and elasticsearch to have access to the directory of TheHive, that
way they can edit/remove/add anything if needed.

## Networking
Thanks to the certification CompTIA Network+, I already had an idea as to how the
networking and the connections will look, so I had no issues addressing every IP, every port
to its service, etc.

## Issues along the way
This time I really didn't experience that many issues, so I will document the only one
I received here:
- I couldn't start the WazuhSvc which allows me to use my Windows VM as an agent.
Solution: Since I couldn't start it through powershell, I simply entered ``%TEMP%`` through the ``Win + R``
and removed it, then downloaded it from there, and then it worked.

## Result
**Setup installed and configured successfully.** (TheHive is configured and setup correctly with networking configuration. Windows VM connected correctly and is active as an Agent in the dashboard of Wazuh.)



**Wazuh dashboard, Wazuh Agent active and ready:**
<img width="1917" height="947" alt="Screenshot_1" src="https://github.com/user-attachments/assets/a2aa0c6f-dbd6-4d7b-aa4a-dcc728205866" />
