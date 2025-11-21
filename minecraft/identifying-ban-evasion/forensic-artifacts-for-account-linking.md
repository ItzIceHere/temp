---
icon: file-user
---

# Forensic Artifacts for Account Linking

When a player logs into Minecraft, the game client creates a record of that session. Even if a player logs out and switches to a new "clean" account, traces of their previous identities often remain buried in the game's configuration files and logs. These are the "digital fingerprints" we are looking for.

#### The "Digital Fingerprints" of Accounts

Game launchers need to remember who you are so you don't have to type your password every time. They store this data in specific JSON configuration files. Finding a banned username or UUID inside one of these files is often the "smoking gun" of ban evasion.

**Where to Look:**

1. **Official Launcher:**
   * **Path:** `%appdata%\.minecraft\`
   * **File:** `launcher_accounts.json` (or sometimes `launcher_profiles.json` in older versions).
   * **What to do:** Open this file with a text editor (Notepad). It lists every account currently or recently logged into the official launcher. Look for names of known banned players.
2. **Lunar Client:**
   * **Path:** `%users%\.lunarclient\settings\game\`
   * **File:** `accounts.json`
   * **What to do:** This file contains the credentials and UUIDs for every account added to Lunar. It is a primary target for finding alts.
3. **Badlion Client:**
   * **Path:** `%appdata%\Badlion Client\` (or within its specific config folders)
   * **File:** Look for JSON files related to user profiles or configurations. Badlion's structure changes, but searching for "user" or "profile" strings within its directory often yields results.
4. **Custom/Other Launchers (MultiMC, Feather, etc.):**
   * **Strategy:** Navigate to the launcher's root directory. Use the search bar to find files named `accounts.json`, `users.json`, or `profile`. Open them and inspect for usernames.

***

#### Log Files and History

Minecraft keeps detailed logs of everything that happens during the game, including the chat and the login process.

1. **The `logs` Folder:**
   * Located in `%appdata%\.minecraft\logs\` (or the logs folder of the custom client).
   * **`latest.log`:** Shows the current session. Useful to see which account launched the game right now.
   * **Archived Logs (`.gz` files):** These are compressed backups of past sessions. They are a history book. By opening these (using 7-Zip or WinRAR), you can see chat logs from weeks or months ago. If you find a log where the player is chatting as "BannedUser123," you have established a link.
2. **Automating the Search:** Manually reading hundreds of logs is impossible. Use a tool to do the work for you.
   * **Search Everything:** Open Everything and point it to the player's `.minecraft` folder. Search for `content:"BannedName"`. This will instantly list any text file or log that contains that specific username.
   * **PowerShell Scripts:** Specialized scripts, like the **Red Lotus Alt Account Finder**, can scan an entire directory tree for specific strings (like "user": "name") to pull out every account name saved in config files.

{% hint style="success" %}
**The "User" String**

If you don't know the name of the banned account you are looking for, you can search for the generic string `"user"` or `"username"` inside the config files. This will reveal _all_ accounts associated with that launcher, allowing you to check them against your ban list.
{% endhint %}
