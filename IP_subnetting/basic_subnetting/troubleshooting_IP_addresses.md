# Troubleshooting IP Addresses

This demo shows how to troubleshoot common IP addressing issues in a small network.

---

## 1. Verify IP Configuration
On Windows:
ipconfig /all

On Linux/macOS:
ifconfig
# or
ip addr show


Check:

IP address

Subnet mask

Default gateway

DNS servers

2. Common Issues and Fixes
Issue A: Wrong Subnet Mask

Symptom: Host cannot reach another PC in the same network.

Example:

PC1: 192.168.1.10 /24

PC2: 192.168.1.20 /16 ❌ (wrong mask)

Fix: Set PC2 mask to /24 (255.255.255.0).

Issue B: Wrong Default Gateway

Symptom: Can ping local PCs, but not outside the LAN.

Example:

PC1 Gateway: 192.168.1.1 (correct)

PC2 Gateway: 192.168.2.1 ❌

Fix: Correct gateway to match router’s LAN IP.

Issue C: Duplicate IP Address

Symptom: Network warning: IP address conflict detected.

Verification:

arp -a


Fix: Change one of the conflicting IPs or set device to DHCP.

Issue D: APIPA Address

Symptom: PC shows 169.254.x.x address.

Cause: DHCP server not reachable.

Fix:

Check DHCP server/router.

Release/renew IP:

ipconfig /release
ipconfig /renew

3. Useful Commands
ping <ip>           # test connectivity
tracert <ip>        # trace route in Windows
traceroute <ip>     # trace route in Linux
arp -a              # check MAC-IP mapping
nslookup <domain>   # test DNS


✅ With these steps, most IP addressing issues can be identified and resolved.
