# Troubleshooting Log

## Issue: Wazuh dashboard install failed with disk-full error
**Cause:** Ubuntu's guided LVM setup only allocated 29 GB of a 58 GB
partition to the root logical volume, leaving the rest unused.

**Fix:**
​```bash
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
​```

## Issue: Could not log into Ubuntu after install (root/root rejected)
**Cause:** VirtualBox's Unattended Installation form was left with
default/incorrect values, so no valid user account was created.

**Fix:** Disabled unattended installation and completed Ubuntu's
manual installer, setting a proper username and password on the
Profile setup screen.

## Issue: Wazuh dashboard rejected the admin password reset
**Cause:** Wazuh requires a symbol from a specific set (`. * + ? -`),
not any symbol.

**Fix:** Reset the password using the built-in tool with a compliant
password:
​```bash
sudo /usr/share/wazuh-indexer/plugins/opensearch-security/tools/wazuh-passwords-tool.sh -u admin -p 'YourPassword'
​```

## Issue: Dashboard unreachable from host browser (ERR_CONNECTION_TIMED_OUT)
**Cause:** The Ubuntu VM's NAT Network IP isn't directly reachable
from the host by default.

**Fix:** Added a port forwarding rule (host port 8443 → guest port
443) via VirtualBox's NAT Network Manager, then accessed the
dashboard at `https://localhost:8443`.

## Issue: Netplan syntax & Indentation 
**Cause:** Running `netplan apply` threw invalid YAML errors (`inconsistent indentation`, `Invalid YAML: aliases are not supported`).

**Fix:** Completely reset the Netplan configuration to ensure clean YAML structure:
   ```bash
   sudo rm /etc/netplan/00-installer-config.yaml
   sudo nano /etc/netplan/00-installer-config.yaml
```

## Issue: Unreachable Repository URL
**Cause:** `eb.strangebee.com` is a dedicated APT package repository endpoint intended for automated package managers (`apt`/`gpg`), not a human-facing web interface.

**Fix:** Switched execution to StrangeBee’s automated installation handler script, which directly fetches necessary keys and configures repository sources programmatically.

## Issue: WazuhSvc synchronization and setup errors
**What happened:** When I was setting up the Wazuh agent from the Windows VM, I couldn't really download and setup the whole process through the PowerShell

**Fix:** While I couldn't understand as to why that was happening, I managed to find a solution by downloading it manually through the GUI, and I ended connecting it as an agent successfully.


## Issue: Issues with cassandra and user logon in TheHive

**Cause:** Cassandra wasn't receiving appropriate queries and was not having an established link with TheHive.

**Fix:** While I was configuring the configuration files of both cassandra and thehive, I forgot to specify which node and data base to be used.
And since I'm using only 1 node, I managed to set it as a ``single-node`` setting, and I also set the datacenter to use ``datacenter-1``.


