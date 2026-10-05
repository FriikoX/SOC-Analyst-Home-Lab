# Investigation 01: Credential Dumping with Mimikatz (T1003)

## Summary
Simulated a credential dumping attack using Mimikatz on the Windows
endpoint, wrote a custom Wazuh detection rule to catch it, and mapped
the resulting alert to MITRE ATT&CK technique T1003 (OS Credential
Dumping).

## MITRE ATT&CK Mapping
- **Tactic:** Credential Access
- **Technique:** [T1003 - OS Credential Dumping](https://attack.mitre.org/techniques/T1003/)

## What I did
1. Executed `mimikatz.exe` on the Windows 11 VM (isolated lab
   environment, no network access to anything beyond the lab).
2. Sysmon captured the process execution and related events.
3. Wrote a custom Wazuh rule to detect Mimikatz execution based on ``originalFileName``.
4. Confirmed the alert fired correctly in the Wazuh dashboard.

## Detection Logic
​```xml
  <rule id="100002" level="15">
    <if_group>sysmon_event1</if_group>
    <field name="win.eventdata.originalFileName" type="pcre2">(?i)mimikatz\.exe</field>
    <description>Mimikatz usage detected</description>
    <mitre>
      <id>T1003</id>
    </mitre>
  </rule>
​```

**What the rule matches on:**
Custom rule briefly explained, is written so that it can detect and register the alert as ID 100002, as severity
level 15, it's field name is made as ``originalFileName`` so that even if the attacker changes the name to bypass alert firing and rules,
it still detects it because the original file name that was downloaded was **"mimikatz.exe"**. Description is self-explanatory, and then
I mapped the attack to MITRE ATT&CK id T1003 which stands for **credentials dumping**.

## Evidence

**Sysmon event showing Mimikatz execution:**
<img width="615" height="596" alt="Screenshot_6" src="https://github.com/user-attachments/assets/ad6c5f59-ad01-4b45-bf83-87b8eb6f90e2" />


**Wazuh alert triggered:**
<img width="1871" height="64" alt="Screenshot_5" src="https://github.com/user-attachments/assets/2ae328cc-f89f-49d5-b044-7704660e693c" />



## Incident Summary (client-style)
> A credential dumping attempt was detected on host 10.0.2.4 at
> 2026-10-05T16:26:47.516Z. The process `mimikatz.exe` was observed executing,
> consistent with MITRE ATT&CK technique T1003 (OS Credential
> Dumping). Recommend isolating the host, resetting credentials for
> any accounts active on the system at the time, and reviewing for
> lateral movement.

## Lessons Learned
I'd recommend the user/client to be careful what they're downloading and where they're downloading it from. As well as updating their system
to the latest patches and updates available, and making sure that they're not clicking on suspicious URLs or any URL they are unfamiliar with.
