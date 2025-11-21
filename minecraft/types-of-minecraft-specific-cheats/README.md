---
icon: crosshairs
---

# Types of  Minecraft-specific cheats

To effectively detect cheats, we must first understand what we're looking for. Not all cheats are created equal; they operate using different mechanisms, interact with the game in different ways, and, most importantly, leave behind different forensic footprints.

Understanding these categories is not just an academic exercise. It is the key to a targeted and efficient investigation. Knowing the likely category of cheat helps you decide where to focus your efforts: should you be meticulously examining the `.minecraft` folder, analyzing the memory of `javaw.exe`, or hunting for a suspicious process running elsewhere on the system?

This page introduces the main categories of cheats that we will be targeting. The following sub-pages will break down each type in detail, covering their mechanisms and, most importantly, the specific techniques used to detect them.

{% hint style="info" %}
**A Note on Terminology**

The definitions for terms like "Ghost Client" and "Injection Client" have evolved over the years and are not always used consistently across the community.

For the purpose of this guide, we will use these terms as practical conventions to help us classify cheats based on their operational behavior. The goal is to provide a clear framework that allows us to communicate and analyze effectively.
{% endhint %}

***

#### The Main Categories of Cheats

Our investigation will focus on identifying cheats that fall into one of four primary categories:

* **Ghost Clients** These cheats operate from **inside the game's own files**. They are often packaged as modified game versions, mods (`.jar` files), or even altered game libraries. Their evidence is typically found within the `.minecraft` folder and the game's process memory.
* **Injection Clients** These cheats are **injected into the game process from an external source**. They usually consist of an injector (`.exe`) that loads a malicious library (`.dll`) into the running `javaw.exe` process. Detection requires finding both the external files and the traces of the injection in memory.
* **External Clients** These cheats operate as **completely separate applications**. They interact with the game by reading and writing to its memory from the outside, without injecting code directly into the `javaw.exe` process. They leave minimal traces _inside_ the game's memory, so detection focuses on finding the external cheat program itself.
* **Autoclickers & Macros** These tools **simulate user input** at the operating system level. They can range from simple scripts to sophisticated hardware features. They often have minimal to no direct interaction with the `javaw.exe` process, requiring a different set of detection techniques focused on system-wide activity and hardware analysis.
