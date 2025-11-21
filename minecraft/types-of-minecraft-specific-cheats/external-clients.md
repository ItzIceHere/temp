---
icon: user-secret
---

# External Clients

External clients are a distinct category of cheats that operate on a simple but effective principle: **stay outside the game**. Unlike ghost or injection clients that modify or enter the game's process, an external client runs as a completely separate, standalone application.

#### Definition and Mechanism

An external client is typically a single executable file (`.exe`) that the user runs alongside Minecraft. It does **not** inject any code (like a `.dll`) into the `javaw.exe` process.

Instead, it interacts with the game from a distance, using standard Windows API functions to:

1. **Read Game Memory (`ReadProcessMemory`):** The cheat reads information directly from `javaw.exe`'s memory space to gather game-state data. For example, it might read player coordinates for an ESP (Extra Sensory Perception) or radar, or monitor a player's health.
2. **Write Game Memory (`WriteProcessMemory`):** In some cases, an external client might write to the game's memory to change values, though this is less common for simple cheats.
3. **Simulate Input:** Many external clients, like triggerbots or autoclickers, simply read pixel data from the screen and then simulate mouse clicks at the operating system level when a certain condition is met (e.g., when the crosshair is over an enemy).

Because all the malicious code is running within the external client's own process, the `javaw.exe` process itself remains internally "clean" and unmodified.

***

#### Why Bypassers Use Them

The primary advantage of an external client is its ability to evade detection methods that are focused on the game process itself.

* **Immunity to Game Memory Scans:** This is the key benefit. If a ScreenSharer's entire strategy is to search the memory of `javaw.exe` for cheat strings, they will find **absolutely nothing**. The cheat's code simply isn't there.
* **Independence and Simplicity:** External clients can be started and stopped at any time, completely independently of the game's launch cycle. For some types of cheats, they can also be simpler to develop than a fully-featured internal client.

***

#### Key Indicators for Detection

Since the cheat is not inside the game, the investigation must shift its focus. Your goal is no longer to find a modification _in_ Minecraft, but to find a completely separate, unauthorized program running on the system.

The detection strategy mirrors that of finding any other malicious executable on Windows. It involves two fundamental steps:

**Step 1: Prove "In-Instance" Execution**

First, you must prove that a suspicious, standalone executable file was run during the relevant timeframe. This requires applying the **standard forensic techniques for program execution** to the entire system, not just the game process.

Your search for evidence will rely on the core Windows artifacts that track application launches, such as:

* **Execution Logs:** Prefetch, BAM, and SRUM.
* **File System History:** USN Journal.
* **Memory of System Processes:** `csrss.exe`, `dps`, etc.

The goal is to find timestamped proof that an unknown or unsigned `.exe` was executed while the player was in-game.

***

**Step 2: Prove the File is a Cheat**

Once you have identified a suspicious executable that was run in-instance, you must prove that it is malicious. This is achieved through **static analysis** of the file itself.

You need to analyze the file's structure, code, and behavior using specialized tools to understand its true purpose. This involves:

* **Analyzing its structure and properties** with tools like **Detect It Easy (DiE)** to identify packers, obfuscators, or suspicious imports.
* **Leveraging online analysis platforms** like **VirusTotal** to check the file's hash against known threats and review its behavioral analysis reports.
