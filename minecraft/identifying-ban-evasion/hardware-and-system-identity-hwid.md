---
icon: fingerprint
---

# Hardware and System Identity (HWID)

When a player connects to a server, they aren't just sending their username. They are connecting with a physical machine made of specific components. Just like a human fingerprint, a computer has a digital fingerprint composed of the unique serial numbers of its parts. This is the **Hardware ID (HWID)**.

HWID analysis is the most definitive way to link two accounts. If Account A was banned, and Account B connects with the exact same motherboard serial number and disk ID, they are the same person.

{% hint style="danger" %}
**Prerequisite: The Manual Record**

It is crucial to understand that **Minecraft servers do not automatically see a player's HWID** when they join, unlike IPs. This data is not sent over the network connection.

Therefore, HWID matching is only possible if **a staff member has previously screenshared the banned player** and recorded their hardware serials.

* **If the banned player was never screenshared**, you have no baseline data to compare against.
* **If they were screenshared**, the HWID data (collected manually or via a tool like Echo) should be stored in your staff database/logs.
{% endhint %}

#### Understanding HWID

A "Hardware ID" isn't a single number. It is a composite signature derived from several components. The most common identifiers used for manual verification are:

* **Disk Serial Number:** The unique factory serial of the Hard Drive or SSD.
* **MAC Address:** The unique network identifier of the Network Interface Card (NIC).
* **Motherboard Serial:** The serial number embedded in the BIOS/UEFI of the motherboard.
* **GPU UUID:** A unique identifier for the graphics card.

#### Detecting HWID Matches

The process relies on comparing the machine in front of you with the records from a past screenshare.

1. **Retrieve the Current HWID:** Use a tool or command during the current screenshare to get the machine's identifiers.
   * **Command Line:** `wmic diskdrive get serialnumber` (for disk), `getmac` (for MAC address), `wmic baseboard get serialnumber` (for motherboard).
   * **SS Tools:** Tools like **Echo** are designed for this. When you run Echo on the player's PC, it generates a unique HWID signature and checks its own database to see if that specific PC has been scanned before.
2. **Compare with Past Records:** Look up the banned account in your staff logs or the SS tool's history. Do the numbers match the ones recorded during the previous ban?
   * **Match:** Positive identification. It is the same computer.
   * **No Match:** They might be on a different PC, or they might be spoofing.
