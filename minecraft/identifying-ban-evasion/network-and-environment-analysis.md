---
icon: wifi
---

# Network and Environment Analysis

If a player's files are clean and their HWID doesn't match, there is still one place they might slip up: their network footprint and the environment they are playing in. Evaders often use tools to mask their location or hide their entire operating system.

#### IP Analysis and VPNs

Changing an IP address is the easiest way to evade a basic IP ban. Players use Virtual Private Networks (VPNs) to route their traffic through a different server, appearing to be in a different city or country.

**Detection:**

* **Process List:** Check **System Informer** or Task Manager for known VPN processes (e.g., `NordVPN.exe`, `ExpressVPN.exe`, `openvpn.exe`).
* **Network Adapters:** Open "Network Connections" in Windows. A VPN often installs a virtual network adapter (e.g., "TAP-Windows Adapter"). If one is active, they are likely using a VPN.
* **Active Connections:** Use `netstat` or the "Network" tab in System Informer. If all game traffic is going to a single IP that belongs to a hosting provider rather than the game server directly, it's being routed through a VPN/Proxy.

{% hint style="info" %}
**Context on IP Bans** Remember that most residential internet connections have **Dynamic IPs**, which change automatically every few days or weeks. A different IP address alone does not prove a player is a different person. However, using a VPN _during_ a screenshare to hide their true IP is a major red flag.
{% endhint %}
