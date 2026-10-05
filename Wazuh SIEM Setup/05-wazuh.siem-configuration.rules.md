# 05 - Configuration of Wazuh

## What I did
In this step I configured Wazuh through the dashboard, created a different index pattern, created a custom rule
and MITRE ATT&CK mapped my first security alert.

## Ossec-agent configuration
I changed wazuh ossec-agent to be getting alerts and events directly from sysmon, since sysmon is configured and ready
to register, ingest and generate alerts/events into the windows event viewer and operational log page.

## Logs configuration
Since Wazuh is by default setting no-all-logs policy, so that it doesn't log everything that is happening on the agent's
device. While that is practical, I am not a professional organization, and my idea is to, frankly, explore what Wazuh
has, how it works, what can be detected, how it looks, and further investigate an alert/event.
<img width="823" height="599" alt="Screenshot_3" src="https://github.com/user-attachments/assets/566e75eb-2c59-4496-9a9c-1ad5c5fbd91d" />

## Different index patttern
As we know, tidiness is key, and we all love to tidy up our places so that everything is at its place accordingly. That's
what index patterns are used for, they are practically the idea of making sure we do not get confused with something 
completely irrelevant, maybe a good example will be an alert that has happened yesterday, but today something similar
happened, to ease up the work of the Analyst (in this case, me), I've setup an index pattern that differentiates the timestamp
of that attack, if it happened today it will be marked as today's date, if it's marked tomorrow, it'll have its own seperate
place to stay at, making it easy for the analyst to work on it and investigate it.

<img width="695" height="590" alt="Screenshot_2" src="https://github.com/user-attachments/assets/83a7c5c3-a6b8-475b-b715-3f80c572ec39" />


## Custom rule creation
I simply configured a rule which detects specifically the attack that I tested today, that is mapped to 
``T1003 MITRE ATT&CK`` **- credential dumping**, this is my first mapping to MITRE ATT&CK, which is great because now
I can proudly say that I have an experience mapping something to MITRE ATT&CK! I also adjusted some case sensitivity for the value
which was originally looking for any type of ``scripts.exe``, I changed it to look for the value ``mimikatz.exe`` which is actually
what type of an alert and attack I was investigating today.
<img width="1806" height="500" alt="Screenshot_4" src="https://github.com/user-attachments/assets/c129d640-8a71-4241-8c3b-a89341938dd7" />

## Issues along the way
Unfortunately, today there were no issues, which is disappointing because I can't really demonstrate troubleshooting solutions
but I can say that there were some tips and tricks I used for this siem

## Tips and tricks

- Originally I couldn't configure the ``ossec-agent.conf`` file because of admin rights, so I opened it through powershell using the ``cd`` and **""**``{path.of.file}``**""**, from there I was having full
administrative rights of the notepad file.
- I also ran the ``mimikatz.exe`` file through powershell, because It originally did not want to register through sysmon or wazuh.

## My first alert/event!

I am glad to announce that I officially received my first event and alert into the Wazuh SIEM dashboard! 
From there on I could see literally anything, it was so interesting, I can't wait to see what else can be generated!



