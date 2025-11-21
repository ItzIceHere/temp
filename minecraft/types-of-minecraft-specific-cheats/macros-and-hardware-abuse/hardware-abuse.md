---
icon: hourglass-clock
---

# Hardware Abuse

This is a subtle but powerful form of gaining an unfair advantage that blurs the line between hardware features and outright cheating. It doesn't involve automated software, but rather the intentional exploitation of a mouse's physical and firmware-level characteristics.

#### Definition and Mechanism

**Debounce time** is a tiny, built-in delay (measured in milliseconds) in a mouse's firmware. Its legitimate purpose is to prevent a single physical click from being accidentally registered as multiple clicks. This is necessary because the mechanical components inside a mouse switch can physically "bounce" for a moment upon contact. A standard debounce time (e.g., 8-10ms) filters out these unintended bounces.

**Mouse Abuse** occurs when a player combines a mouse with an **artificially low or adjustable debounce time** (often configurable in software to values below 10ms, sometimes 0-4ms) with specific physical clicking techniques like **drag clicking** or **butterfly clicking**. These techniques are designed to make the switch vibrate rapidly.

* On a normal mouse, the debounce filter ignores these vibrations.
* On a low-debounce mouse, these vibrations are registered as dozens of separate clicks, leading to impossibly high Clicks-Per-Second (CPS) rates (20-60+).

***

#### Why It's Considered Cheating in some servers

Because manipulating debounce time provides a direct, **hardware-based advantage** that allows for click speeds physically unattainable on standard equipment, many competitive servers have rules that explicitly ban setting a debounce time below a certain threshold (most commonly **10ms**).

***

#### Detection Strategy

The detection process involves identifying the player's mouse and checking its software for debounce settings.

1. **Identify the Mouse Model:** First, determine what mouse the player is using, as not all models have adjustable debounce.
2. **Inspect the Software GUI:** If the mouse's software supports it, this is the most direct proof. Open the software and look for a setting explicitly labeled **"Debounce Time,"** "Click Response," or a similar term. A value set below the server's allowed threshold is a direct rule violation.
3. **Examine Configuration Files:** The debounce setting is often stored in the same configuration files as macros. Check the modification times and search the contents for keywords like "debounce," "db\_time," or "click\_latency."
4. **Special Cases (Known Abusable Hardware):** Some mouse brands are infamous in the community for having inherently low or faulty debounce times, regardless of software settings.
   * **Roccat & Bloody:** Many models from these brands are known to have effective debounce times well below 10ms, even if a software slider appears to be set higher.
   * **Mad Catz:** Certain older models were built with virtually no debounce filter at all, making them easily abusable.
