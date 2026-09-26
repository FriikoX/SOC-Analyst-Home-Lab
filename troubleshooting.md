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
