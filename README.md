# linux-privilege-escalation-lab8
TryHackMe linprivesc — Linux Privilege Escalation Lab | Kernel Exploit, SUID, Sudo, Cron, NFS, PATH, Capabilities | 100% Room Completed | All 9 Flags Captured

# 🐧 Linux Privilege Escalation Lab — TryHackMe linprivesc

**Student:** Uliya Fatima | **ID:** 232098  
**Lab:** Lab 7 — Post Exploitation (Part 1)  
**Platform:** TryHackMe — linprivesc Room  
**Date:** April 27, 2026  
**Completion:** ✅ 100% — All Tasks Completed

🔗 [TryHackMe Room](https://tryhackme.com/room/linprivesc)

---

## 🖥️ Lab Environment

| Field | Details |
|-------|---------|
| Attack Machine | Kali Linux |
| Platform | TryHackMe (linprivesc) |
| Initial Access | Low-privilege user (karen / leonard) |
| Goal | Escalate to ROOT on each machine |

---

## 📋 Attack Techniques Covered

| # | Task | Machine | Method | Result |
|---|------|---------|--------|--------|
| 1 | Kernel Exploit | LineKernel | CVE-2015-1328 (overlayfs) | ✅ ROOT |
| 2 | Sudo Misconfiguration | LinPrivEscSUDO | GTFOBins (nano/find) | ✅ ROOT |
| 3 | SUID Binaries | LinPrivEscSUID | base64 SUID read | ✅ ROOT |
| 4 | Capabilities | LinPrivEscCAPA | cap_setuid via view | ✅ ROOT |
| 5 | Cron Jobs | LinPrivEscCRON | Writable cron script → reverse shell | ✅ ROOT |
| 6 | PATH Variable | LinPrivEscPATH3 | Fake binary injection | ✅ ROOT |
| 7 | NFS | LinPrivEscNFS | no_root_squash SUID shell | ✅ ROOT |
| 8 | Final Challenge | Linux Privesc Challenge | base64 SUID + sudo find | ✅ ROOT |

---

## 🚩 All Flags Captured

| Task | Flag |
|------|------|
| Kernel Exploit | THM-28392872729920 |
| Sudo Misconfiguration | THM-402028394 |
| SUID Binaries | THM-3847834 |
| Capabilities | THM-9349843 |
| Cron Jobs | THM-383000283 |
| PATH Variable | THM-736628929 |
| NFS | THM-89384012 |
| Final Challenge Flag1 | THM-42828719920544 |
| Final Challenge Flag2 | THM-168824782390238 |

---

## 🔑 Cracked Passwords

| User | Method | Password |
|------|--------|---------|
| user2 | John + rockyou.txt | Password1 |
| matt | John + rockyou.txt | 123456 |
| missy | John + rockyou.txt | Password1 |

---

## 🛠️ Tools Used

- **Metasploit / searchsploit** — Exploit discovery
- **John the Ripper** — Password cracking
- **GTFOBins** — Binary exploitation reference
- **Netcat** — Reverse shell listener
- **GCC** — Compiling C exploits on target
- **Kali Linux** — Attack machine

---

## 📚 Key Takeaways

- Outdated kernels (3.13.0-24) exploitable via CVE-2015-1328 (overlayfs local privilege escalation)
- Sudo NOPASSWD on `nano`, `find`, `less` = instant privilege escalation via GTFOBins
- SUID on `base64` allows reading `/etc/shadow` without root
- Linux capabilities (`cap_setuid`) on `vim`/`view` = root shell via Python one-liner
- Writable cron scripts running as root = reverse shell escalation
- NFS shares with `no_root_squash` = SUID shell attack from attacker machine
- **Enumeration is everything** — always run: `sudo -l`, `find / -perm -4000`, `getcap -r /`, `cat /etc/crontab`

---

## ⚠️ Disclaimer

All activities were performed on **TryHackMe's intentionally vulnerable lab machines** for educational purposes only. No real systems were targeted.
