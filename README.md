# NETWORKWALKS-MOHANAKRISHNA-B0XX-WK3-PM1-PM2-PASSWORD-CRACKING

A hands-on walkthrough of a password-protected PDF cracking exercise completed as part of the **Networkwalks Cyber Security training program**. This lab demonstrates a dictionary attack against a PDF file's password hash — first using an online hash-extraction tool and Networkwalks' interactive attack simulator to build intuition, then repeating the crack with the real **John the Ripper (Johnny GUI)** tool.

> ⚠️ **Disclaimer:** This exercise was performed in a controlled training lab on files provided for educational purposes by Networkwalks. Password cracking should only ever be performed on systems/files you own or are explicitly authorized to test.

---

## 🧠 Overview

The goal of the lab was to understand how dictionary attacks work against password-protected documents:

1. Extract a crackable hash from a password-protected PDF.
2. Run a dictionary (wordlist) attack against the hash.
3. Recover the plaintext password and use it to unlock the PDF.
4. Validate the same recovered passwords using John the Ripper's GUI front-end, **Johnny**.
5. Capture the lab completion flags.

This mirrors exactly what a real security tester does when auditing document/password security — the same core idea used by tools like `pdf2john.py` + `john`/`hashcat`.

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Online HashCrack (pdf2john converter) | Extracts the `$pdf$...` crackable hash from a password-protected PDF |
| Networkwalks Dictionary Attack Lab (interactive browser simulator) | Visualizes how a wordlist attack tries candidate passwords against a hash |
| **John the Ripper** — Johnny GUI | Runs the actual offline dictionary attack against the extracted PDF hash |

---

## 🔎 Step 1 — Extract the PDF Hash

The password-protected PDF was uploaded to an online `pdf2john` converter to extract its hash in JtR-crackable format (`$pdf$...`).

![PDF hash extraction](images/01-pdf2john-hash-extraction.png)

The tool uses `pdf2john` from JohnTheRipper under the hood to parse the PDF's encryption dictionary and output a hash string that `john` or `hashcat` can attack directly.

---

## ⚔️ Step 2 — Dictionary Attack Simulation (Networkwalks Lab)

Before running the real tool, the Networkwalks **Dictionary Attack Lab** was used to simulate the attack: each word from a wordlist is hashed and compared against the target `$pdf$` hash until a match is found.

**Target file #1** — cracked after 91/100 attempts:

![Dictionary attack lab — password1 cracked](images/02-dictionary-attack-lab-password1.png)

**Recovered password:** `password1`

**Target file #2** — cracked after 35/100 attempts:

![Dictionary attack lab — 1qaz2wsx cracked](images/03-dictionary-attack-lab-1qaz2wsx.png)

**Recovered password:** `1qaz2wsx`

Both results illustrate why weak, predictable passwords (common words, keyboard-walk patterns like `1qaz2wsx`) fall almost immediately to a basic wordlist attack.

---

## 🖥️ Step 3 — Cracking with John the Ripper (Johnny GUI)

The same hashes were then loaded into **Johnny**, the graphical front-end for John the Ripper, to perform the real dictionary attack and confirm the results.

**Password file 1 cracked:**

![Johnny GUI — password1 cracked](images/04-johnny-gui-password1-cracked.png)

**Password file 2 cracked:**

![Johnny GUI — 1qaz2wsx cracked](images/05-johnny-gui-1qaz2wsx-cracked.png)

Both recovered plaintext passwords matched the results from the simulator, confirming the attack methodology.

---

## 🚩 Flags Captured

Completing each stage of the lab unlocked a flag as proof of completion:

![Flag 1 — cybersecurity flag captured](images/07-flag-cybersecurity-captured.png)
