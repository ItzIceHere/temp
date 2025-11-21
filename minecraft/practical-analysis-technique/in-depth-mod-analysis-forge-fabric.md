---
icon: puzzle-piece
---

# In-depth Mod Analysis (Forge/Fabric)

The `mods` folder is where legitimate enhancements and malicious cheats are most often found, sometimes disguised to look like one another. A methodical, forensic examination of this folder and its contents is therefore one of the most critical skills a ScreenSharer must master.

This guide provides a multi-phased approach, moving from high-level checks down to definitive, granular proof.

**Prerequisite:** You must have already located the **correct and active `mods` folder** using the methods from the previous pages. All analysis must be performed in this verified directory.

***

#### Phase 1: Initial Folder Triage

Before you even double-click a single file, the `mods` folder itself can provide crucial evidence.

*   **Check the "Date Modified" Timestamp:** This is your first and one of your most powerful checks. Examine the "Date modified" timestamp of the `mods` folder in File Explorer.



{% hint style="danger" %}
**Critical Red Flag: Recent Modification**\
If this timestamp is very recent, especially if it falls just moments before the screenshare, it is an **extremely strong indicator of tampering**. This suggests that files were recently added, removed, or replaced in an attempt to hide evidence. Many servers consider this a direct, bannable offense for evidence manipulation
{% endhint %}

***

#### Phase 2: Detailed Analysis of Mod Files (`.jar`)

Now, we dive into the individual `.jar` files. Scrutinize **every single one**.

**1. Identify Loaded Mods (The "File in Use" Test)**

While the game is running, you can quickly determine which mods are actively loaded by the JVM.

* **Procedure:** Attempt to move each `.jar` file from the `mods` folder to another location (like the Desktop).
* **Result:** Files that **cannot be moved** because of a "file in use" error are currently locked and loaded by the `javaw.exe` process. Files that move freely were not loaded in the current session (or have been "unloaded" via a bypass). Take note of the active mods.

**2. Analyze File Size (The "Weight" Check)**

This is a quick heuristic to spot anomalies. Experienced ScreenSharers develop a feel for the typical file sizes of common mods.

* **Red Flag:** A file size that is **significantly larger or smaller** than the known standard for that specific mod and version is highly suspicious and requires immediate deeper investigation.
* **Example:** A standard Togglesneak mod for version 1.8.9 is typically around 24-30 KB. Finding a `Togglesneak.jar` that is 70 KB is a major red flag.

**3. Analyze Content (Decompilation)**

This is where you look "under the hood." Use a Java decompiler like **Luyten** or **Recaf** to inspect the code of any suspicious mods.

* **What to Look For:**
  * **Suspicious Names:** Look for class or package names that scream "cheat" (e.g., `autoclicker`, `reach`, `killaura`, `selfdestruct`).
  * **Obfuscation:** This is an almost certain sign of a cheat. Obfuscation is the intentional scrambling of code to hide its true purpose. It is easily recognizable by:
    * Meaningless, single-letter class and method names (e.g., `a.class`, `b()`).
    * Long, random-looking, or nonsensical names.

{% hint style="danger" %}
**Obfuscation is a Bannable Offense**

Because it is impossible to quickly and safely verify the function of obfuscated code during a screenshare, the vast majority of competitive servers have a zero-tolerance policy. They consider the presence of an obfuscated mod to be a bannable offense on its own.
{% endhint %}

**4. Verify Integrity (The Hash Check)**

This is the **definitive, scientific method** to prove a file has been tampered with. It works even on files that look legitimate by name and size, like a fake OptiFine.

* **Procedure:**
  1. Use a tool like **HashMyFiles** to calculate the **SHA256 hash** of the player's `.jar` file.
  2. Find the **official SHA256 hash** for the **exact same version** of that mod from a **trusted source** (the developer's official website, CurseForge, or Modrinth).
  3. Compare the two hashes.

{% hint style="success" %}
**Conclusive Proof of Tampering**

If the hashes **do not match**, you have undeniable, conclusive proof that the player's file is not the official version and has been modified.
{% endhint %}

***

#### Phase 3: Detecting "Unloaded" Mods (Memory Analysis)

This technique is used to find mods that were loaded at game start but were then deleted or moved to evade detection. Traces of these mods can still linger in the game's memory.

* **Procedure:**
  1. Open **System Informer** as an administrator.
  2. Target the `javaw.exe` process for Minecraft. Right-click -> `Properties` -> `Memory` -> `Strings`.
  3. In the filter, select `Contains (case-insensitive)` and paste the **full path of the active `mods` folder**.
  4. The results will show the paths of `.jar` files that have been referenced by the game in the current session.
  5. **Compare** this list from memory with the files currently on the disk in the `mods` folder.

{% hint style="danger" %}
**The "Ghost" Mod: Evidence of Evasion**

If you find the path to a mod in the memory strings, but that `.jar` file is **no longer physically present** in the `mods` folder, you have found strong evidence of an "unload" bypass. The player likely removed the file mid-session to hide it.
{% endhint %}

***

#### Bonus: Automated Analysis (HabibiModAnalyzer)

To speed up the integrity verification process, especially the hash checks, you can use the **HabibiModAnalyzer** PowerShell script.

* **Functionality:** It automates the process of comparing the hashes of the mods in the player's folder against the trusted Modrinth database, quickly flagging any tampered files.
*   **Execution Command (Run in PowerShell as Admin):**

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass; Invoke-Expression (Invoke-RestMethod https://raw.githubusercontent.com/HadronCollision/PowershellScripts/refs/heads/main/HabibiModAnalyzer.ps1)
    ```
