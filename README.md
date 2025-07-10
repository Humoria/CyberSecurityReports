# 🕵️‍♂️ TryHackMe - Agent Sudo Walkthrough

This repository contains my personal write-up for the **Agent Sudo** room on [TryHackMe](https://tryhackme.com/). The challenge involves enumerating a target machine, exploiting a hidden backdoor, and escalating privileges to retrieve the root flag. The room teaches essential penetration testing techniques including service enumeration, decoding hidden messages, exploiting sudo misconfigurations, and privilege escalation.

---

## 🧠 Room Overview

**Room Name**: Agent Sudo  
**Platform**: TryHackMe  
**Difficulty**: Easy-Medium  
**Category**: Offensive Security / Capture The Flag  
**IP Address**: *(Dynamic IP - changes per instance)*

---

## 🛠️ Tools & Techniques Used

- `nmap` – Network enumeration  
- `gobuster` – Directory brute forcing  
- `hydra` – Password brute forcing  
- `john` – Cracking password hashes  
- `strings` – Analyzing binaries  
- `base64` / `rot13` / steganography – Decoding hidden messages  
- `sudo -l` – Sudo misconfiguration check  
- Linux privilege escalation using `sudo`  

---

## 🧭 Walkthrough Summary

### 1. **Initial Enumeration**
```bash
nmap -sC -sV -Pn <target-ip>
Found open ports: 22 (SSH), 80 (HTTP)
```

### 2. Web Enumeration
Accessed the web interface, found clues related to secret agents.

Used gobuster to find hidden directories:

```bash

gobuster dir -u http://<target-ip> -w /usr/share/wordlists/dirb/common.txt

```

### 3. Found Hidden Hints
Discovered base64-encoded messages.

Decoded and followed hints to identify usernames/passwords.

### 4. SSH Access
Cracked a password hash using john or bruteforce via hydra.

Gained initial access via SSH as a low-privileged user.

### 5. Privilege Escalation
Used sudo -l and found that the user can run a script or binary with elevated privileges.

Reverse-engineered the binary or abused misconfigured permissions to escalate to root.

### 6. Capture the Flags
user.txt and root.txt were successfully captured.

## 🏁 Flags
✅ user.txt: [REDACTED]

✅ root.txt: [REDACTED]

## 📚 Lessons Learned
Always enumerate all possible entry points (directories, usernames).

Pay attention to small hints or encoded data.

Privilege escalation often comes from misconfigured sudo rules.

Always check your permissions and environment variables.

## 📁 Disclaimer
This write-up is for educational purposes only. All activities were conducted in a legal lab environment provided by TryHackMe. Do not attempt unauthorized access on any real systems.

## 📌 Author
Marco Albert
