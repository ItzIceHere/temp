---
icon: scale-balanced
---

# Documentation and Policy

Finding an alt account is useless if you cannot prove it. Ban evasion is often a circumstantial charge, meaning you are building a case based on connections rather than a single "cheat found" message. Because of this, your documentation must be flawless.

#### The Burden of Proof

You must be able to answer the question: **"How do you know it's him?"**

Subjective feelings are not evidence.

* ❌ "He bridges just like Player X."
* ❌ "He has the same voice."
* ❌ "He joined right after Player X got banned."

These are _leads_, not proofs. To issue a ban, you need **technical links**:

* ✅ "His `launcher_accounts.json` file contains the UUID of Banned Player X."
* ✅ "The HWID collected by Echo matches the HWID logged in the ban report for Player X."
* ✅ "We found a log file where he logs into the server using Player X's account."

#### Documenting the Link

When writing your ban report, you must explicitly state the connection. Do not just write "Ban Evasion." Write the evidence chain.

**Example Report Format:**

> **Suspect:** NewPlayer123 **linked To:** BannedPlayer\_OG (Banned for Cheating on \[Date])
>
> **Evidence of Link:**
>
> 1. **File Artifact:** Found `BannedPlayer_OG` username saved in `.lunarclient/settings/game/accounts.json`. (Attach a Screenshot proof or recording)
> 2. **HWID Match:** Echo scan shows a `HWID Match` which to the previous scan made to `BannedPlayer_OG`. (Attach a Screenshot proof, recording or add the scan link)

By presenting a clear, evidence-based link, you protect yourself from appeals and ensure the ban is justified.
