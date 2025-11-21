---
icon: microchip
---

# Mouse Macros

In the context of Minecraft screensharing, a **mouse macro** is an automated sequence of instructions, primarily clicks, assigned to a single button press. Its purpose is to simulate rapid-fire clicking, effectively turning a mouse button into a high-speed autoclicker. These macros can be stored in two distinct ways, each requiring a different detection strategy.

#### 1. Software-Based Macros (Stored on the PC)

These macros are defined within the manufacturer's software, and their configurations are saved in files on the computer. For the macro to work, the mouse software typically needs to be running in the background.

**Why Bypassers Use Them:**

They are easy to create, highly customizable, and can be enabled or disabled on the fly through software profiles.

**Detection Strategy:**

Detection involves a forensic analysis of the mouse software's configuration files and a direct inspection of its graphical interface.

**A. Inspect the Software GUI:** This is the most direct method. Open the mouse's official software (e.g., Logitech G HUB, Razer Synapse, Roccat Swarm, SteelSeries GG) and navigate to the macro editor and button assignment sections. Look for any macros assigned to mouse buttons that contain rapid sequences of left or right clicks with minimal delays.

**B. Analyze Configuration Files:** The most critical forensic step is to examine the software's configuration files.

* **First, check the "Date modified" timestamp** of the relevant files or folders. A modification time that is very recent or just before the screenshare is a major red flag, suggesting that macros were recently created, edited, or deleted.
* **Second, inspect the contents.** Below are the known file locations for major brands. Look for files with extensions like `.xml`, `.json`, `.ini`, or `.db` and search their contents for keywords like "macro," "click," "delay," or button assignments.
  * **Logitech:**
    * **Logitech G HUB (Newer):** `%localappdata%\LGHUB\` (Check `settings.db` with a SQLite browser)
    * **Logitech Gaming Software (Older):** `%localappdata%\Logitech\Logitech Gaming Software\` (Check `settings.json`)
  * **Razer:**
    * **Synapse 3:** `C:\ProgramData\Razer\Synapse3\Accounts\` and `%localappdata%\Razer\Synapse3\Log\`. (Note: Synapse 3 configurations can be complex and cloud-synced; checking the GUI is often more effective).
  * **SteelSeries:**
    * `%localappdata%\steelseries-engine-3-client\Local Storage\leveldb\` (Requires a LevelDB viewer for full analysis).
  * **Roccat:**
    * `%appdata%\ROCCAT\SWARM\macro\` (Look for `custom_macro_list.xml` or `macro_list.dat`).
  * **Red Dragon:**
    * `%homepath%\Documents\M### Gaming Mouse\MacroDB\` (The `M###` varies by model).
  * **Glorious / YanPol / Ajazz (Often use similar software):**
    * `%appdata%\BY-COMBO2\` (Look for a `Mac` subfolder).
  * **Corsair (iCUE):**
    * `%appdata%\Corsair\CUE\` (Check `Config.cuecfg` and search inside for keywords like `RecMouseCLicksEnable`).
  * **Bloody:**
    * `C:\Program Files (x86)\Bloody7\Bloody7\Data\Mouse\English\ScriptsMacros\GunLib\` (Check for `.amc2` files).
  * **Cooler Master:**
    * `%localappdata%\CoolerMaster` or `%appdata%\CoolerMaster`.
  * **Asus (ROG Armoury):**
    * `%USERPROFILE%\Documents\ASUS\ROG Armoury\Macro`.
  * **Krom (Kolt model):**
    * `%localappdata%\VirtualStore\Program Files (x86)\KROM KOLT\Config\` (Look for `sequence.dat`).
  * **Ayax (Noganet):**
    * `C:\Program Files\AYAX GamingMouse\` (Look for `record.ini`).
  * **BlackWeb:**
    * `C:\Blackweb Gaming AP\config\` (Look for files with `.MA32AIY` extension).

***

#### 2. On-Board Macros (Stored on the Mouse)

These are the stealthiest form of macros. The sequence is programmed using the software but then saved directly to the **mouse's internal memory chip**. This allows the macro to function perfectly even if the software is completely closed or uninstalled.

**Why Bypassers Use Them:**

They leave no running software process to be detected. The input signals come directly from the hardware, making them appear as legitimate clicks to the operating system.

**Detection Strategy:**

Since there are no files to find, detection relies entirely on testing the mouse's **real-time behavior**.

**A. Identify the Mouse Model:** This is a **critical first step**. You must know the exact model to understand its default button layout. Ask the player, check Windows device settings, or use `USBDeview`.

**B. The Mouse Button Test:**

1. Use a reliable online button testing website (e.g., `cpstest.org/mouse-test`) that can recognize extra buttons.
2. Instruct the player to press **every single physical button** on their mouse, one at a time.
3. **Look for a mismatch.** The key indicator is when the physical button pressed does not match the button registered by the website. For example, the player presses a physical side button ("Forward"), but the website registers a "Left Click." This indicates the side button has been reprogrammed in the hardware to trigger a click macro.

**C. The Two-Test Protocol (MANDATORY):** This entire test must be performed **twice**.

* **Test 1: Software OPEN:** Conduct the first full button test while the mouse's proprietary software is running.
* **Test 2: Software CLOSED:** Completely terminate the mouse's software from the Task Manager and system tray, then repeat the entire button test.

{% hint style="danger" %}
**Why Two Tests are Crucial**

Some mice are designed to prioritize the settings from the running software over the profiles stored on-board. A macro stored in the mouse's memory might be overridden and disabled while the software is open. It may only become active—and thus detectable—when the software is closed and the mouse reverts to its internal profile. **Skipping the second test can cause you to miss on-board macros.**
{% endhint %}
