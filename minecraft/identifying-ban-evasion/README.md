---
icon: user-police
---

# Identifying Ban Evasion

So far, we have focused on finding unauthorized _software_. Now, we shift our focus to finding unauthorized _people_.

**Ban Evasion** is the act of a previously punished player returning to the server to circumvent their penalty. It is a persistent challenge in competitive communities. A player who cheats, gets banned, and immediately returns on a new account undermines the entire moderation system.

Detecting ban evasion is fundamentally different from detecting cheats. You aren't looking for a `killaura` module or an injected DLL. You are looking for **links**. Your goal is to find a digital thread that connects the "new" player sitting in front of you to an "old" identity that is currently banned.

This section will guide you through the forensic methods used to uncover these hidden identities.

#### Defining the Methods of Evasion

To catch an evader, you must understand how they hide. Evasion typically falls into one of three categories:

1. **The "Alt" Account:** The most common method. The player buys or obtains a fresh Minecraft account. They rely on the hope that you won't notice they are the same person playing from the same computer.
2. **Identity Spoofing (HWID/IP):** More advanced evaders know that servers track their IP address and Hardware ID (HWID). They use VPNs to change their IP and "Spoofers" to fake their computer's serial numbers, trying to look like a completely different machine.

***

#### The Core Strategy: Connecting the Dots

A ban evasion investigation is a puzzle. Rarely will you find a single file that says "I am BannedPlayer123." Instead, you build a case by connecting multiple data points.

We will use a methodology based on **Forensic Link Analysis**:

* **File Artifacts:** We will search for configuration files and logs where the game client carelessly saves a history of every account ever logged in.
* **System Fingerprints:** We will look at the unique hardware signatures of the computer to see if they match a known banned profile.
* **Network Footprint:** We will analyze connection data to expose the use of VPNs or proxies used to mask their location.

{% hint style="warning" %}
**The Burden of Proof**

Suspicion is not enough. You cannot ban a player for evasion just because they "play like" a banned user or have a similar voice. You must find concrete, technical evidence that links their current session to a banned identity.
{% endhint %}
