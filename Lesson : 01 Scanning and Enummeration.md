অবশ্যই! নিচে আমি **Ethical Hacking-এর Scanning & Enumeration** ধাপটি **বেসিক থেকে অ্যাডভান্স পর্যন্ত ধাপে ধাপে** বিস্তারিতভাবে ব্যাখ্যা করছি—যাতে আপনি হাতে-কলমে ও পেশাদারভাবে বিষয়টি আয়ত্ত করতে পারেন।

---

# 🧭 Scanning & Enumeration: Full Roadmap (Basic to Advanced)

## ✅ **Phase Overview**

🔹 **Scanning** = টার্গেটের ওপেন পোর্ট, সার্ভিস, ও ভার্সন চিহ্নিত করা
🔹 **Enumeration** = ওই সার্ভিস বা সিস্টেমের ভিতরের তথ্য সংগ্রহ (Users, Shares, Policies)

---

## 🧱 **Part 1: Scanning – বেসিক পর্যায়**

### 📌 1.1: Types of Scanning

| Scanning Type             | কাজ                                 |
| ------------------------- | ----------------------------------- |
| 🔸 Port Scanning          | কোন কোন পোর্ট ওপেন আছে              |
| 🔸 Network Scanning       | কোন কোন ডিভাইস/হোস্ট নেটওয়ার্কে আছে |
| 🔸 Service Scanning       | কোন সার্ভিস চলছে, ভার্সন কত         |
| 🔸 Vulnerability Scanning | সার্ভিসে কোন দুর্বলতা আছে কিনা      |

---

### 🛠️ 1.2: Basic Scanning Tools & Commands

#### ✅ Nmap (Network Mapper)

| কাজ                         | কমান্ড                       |
| --------------------------- | ---------------------------- |
| Ping Scan (live host check) | `nmap -sn 192.168.0.0/24`    |
| Port Scan                   | `nmap -p 1-1000 192.168.0.1` |
| Service Detection           | `nmap -sV 192.168.0.1`       |
| OS Detection                | `nmap -O 192.168.0.1`        |
| Aggressive Scan             | `nmap -A 192.168.0.1`        |

#### ✅ Netdiscover (LAN Scan)

```bash
netdiscover
```

#### ✅ Masscan (Fastest Port Scanner)

```bash
masscan 192.168.0.0/24 -p0-65535
```

---

## 🧱 **Part 2: Enumeration – বেসিক থেকে মিড-লেভেল**

### 📌 2.1: Common Enumeration Targets

| টার্গেট        | উদাহরণ                   |
| -------------- | ------------------------ |
| OS             | Windows, Linux           |
| User Accounts  | Admin, Guests            |
| Network Shares | Public, Finance          |
| Services       | SMB, SNMP, FTP, LDAP     |
| Policies       | Password length, lockout |

---

### 🛠️ 2.2: Enumeration Tools & Commands

#### ✅ Windows Enumeration (SMB, RPC)

| টুল          | কমান্ড                         |
| ------------ | ------------------------------ |
| `enum4linux` | `enum4linux -a 192.168.0.1`    |
| `smbclient`  | `smbclient -L \\\\192.168.0.1` |
| `rpcclient`  | `rpcclient -U "" 192.168.0.1`  |
| `nbtscan`    | `nbtscan 192.168.0.1`          |

#### ✅ SNMP Enumeration

```bash
snmpwalk -v2c -c public 192.168.0.1
```

#### ✅ LDAP Enumeration (AD Servers)

```bash
ldapsearch -x -h 192.168.0.1 -b "dc=example,dc=com"
```

#### ✅ FTP Anonymous Login Test

```bash
ftp 192.168.0.1
```

---

## 🔐 **Part 3: Advanced Enumeration Techniques**

### 📌 3.1: Vulnerability-focused Scanning

#### ✅ Nikto (Web Vulnerability Scanner)

```bash
nikto -h http://192.168.0.1
```

#### ✅ Nessus / OpenVAS (GUI)

* Comprehensive vulnerability scan
* CVE-based exploit suggestion

---

### 📌 3.2: Web App Enumeration (OWASP)

| টুল                 | কাজ                            |
| ------------------- | ------------------------------ |
| `gobuster` / `dirb` | Hidden directories enumeration |
| `whatweb`           | Web tech detect                |
| `wpscan`            | WordPress enumeration          |

---

## 🧪 রিয়েল-লাইফ স্কেনারিও

1. **Penetration Test শুরু করার সময়**

   * `nmap -sV -A` দিয়ে টার্গেট সার্ভিস বের করেন
   * এরপর `enum4linux`, `smbclient`, `snmpwalk` দিয়ে ভিতরের ইউজার/শেয়ার তথ্য বের করেন

2. **Web Server এ পরীক্ষা**

   * `nikto` দিয়ে vulnerabilities চেক করেন
   * `gobuster` দিয়ে hidden admin panel খুঁজেন

---

## 📁 রিপোর্টে যা থাকে:

```markdown
## Target: 192.168.0.10
- Open Ports: 21, 22, 80, 445
- OS: Windows Server 2012
- SMB Shares: public, confidential
- Users: Administrator, John, Guest
- SNMP Info: sysName=target-server
- Web Tech: Apache 2.4.41, PHP 7.3
```

---

## 🧠 Mnemonic Shortcut:

> **SCAN ME WISELY**

S = Scan
C = Check Ports
A = Aggressive Scan
N = Nmap
M = Masscan
E = Enumeration
W = Windows Info
I = Internal Shares
S = SNMP/LDAP
L = List Users
Y = Your Report

---

## 📌 কেন এটা প্রয়োজনীয়?

* 🎯 Exploitation-এর প্রথম দরজা খুলে দেয়
* 🛡️ Defender হিসাবে নিজেই জানতে পারবেন কোথায় দুর্বলতা
* 🧠 Real-world Red Team, CTF, বা Bug Bounty তে সফলতার চাবিকাঠি

---

## ✅ উপসংহার

🔓 Scanning & Enumeration না জানলে আপনি Ethical Hacking শুরুই করতে পারবেন না। এটি Footprinting-এর পর সবচেয়ে গুরুত্বপূর্ণ ধাপ।

