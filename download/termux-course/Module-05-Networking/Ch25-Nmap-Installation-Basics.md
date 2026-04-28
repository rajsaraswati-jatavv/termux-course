# Chapter 25: Nmap Installation & Basics

> **Module:** 5 - Networking  
> **Chapter:** 25 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐ Beginner  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed Nmap introduction and scan types |
| Installation Guide | Step-by-step Termux installation |
| Commands Reference | 25+ Nmap commands |
| Practice Exercises | Hands-on scanning labs |
| Troubleshooting | Common Nmap issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 25
Title: Nmap Installation & Basics | Network Scanning Tutorial | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon T3rmuxk1ng, aur aaj ek bahut important chapter hai -
Chapter 25: Nmap Installation & Basics!

Agar aap ethical hacking, penetration testing, ya network security mein 
interest rakhte ho, to Nmap aapke liye sabse important tool hai. Ye 
network scanner hai - world ka sabse powerful aur popular scanner.

Aaj hum seekhenge:
- Nmap kya hai aur kyun use karte hain
- Termux mein Nmap kaise install karte hain
- Basic scan types - TCP, SYN, UDP scans
- Port specification techniques
- Version aur OS detection
- Output formats save karna
- Timing templates
- 25+ practical Nmap commands

Chaliye shuru karte hain!

Play button dabaiye, like karein, subscribe karein - notification bell ke saath.

---

[SECTION 1: WHAT IS NMAP? - 0:50 to 4:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle sawal - Nmap kya hai?

Nmap ka full form hai "Network Mapper". Ye ek free, open-source network 
scanning tool hai jo Gordon Lyon (Fyodor) ne banaya tha 1997 mein.

Nmap ka primary kaam hai:
- Network discovery - Network mein kaun-kaun se devices hain
- Port scanning - Kisan ke ports open hain
- Service detection - Kaun si services chal rahi hain
- OS detection - Operating system kya hai
- Vulnerability detection - Security weaknesses

SIMPLE WORDS MAIN SAMJHEIN:

Imagine karein aap ek building ke bahar khade ho. Aapko andar jana hai, 
lekin pata nahi:
- Kitne darwaze hain (ports)
- Kaun sa darwaza khula hai (open ports)
- Andar kaun rehta hai (services)
- Building ka design kya hai (OS)

Nmap exactly ye kaam karta hai - network ki mapping karta hai!

WHY NMAP IS IMPORTANT:

┌─────────────────────────────────────────────────────────────────────────┐
│                    NMAP - NETWORK SECURITY SCANNER                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  🎯 USE CASES:                                                          │
│  ├── Network Inventory - Sab devices ki list                            │
│  ├── Security Auditing - Vulnerabilities dhundhna                       │
│  ├── Penetration Testing - Attack surface mapping                       │
│  ├── Firewall Testing - Rules check karna                               │
│  ├── Host Monitoring - Device status track karna                        │
│  └── Service Detection - Running services identify karna                │
│                                                                          │
│  🏆 WHY NMAP IS #1:                                                     │
│  ├── Free and Open Source                                               │
│  ├── Available on ALL platforms                                         │
│  ├── Extremely powerful and flexible                                    │
│  ├── 25+ years of development                                           │
│  ├── Used by security professionals worldwide                           │
│  ├── 600+ NSE scripts for advanced scanning                             │
│  └── Industry standard tool                                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Nmap ko seekhna har security professional ke liye MUST hai!

---

[SECTION 2: PORT SCANNING FUNDAMENTALS - 4:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Nmap seekhne se pehle, ports ke baare mein samajhna zaruri hai.

WHAT ARE PORTS?

Computer pe 0-65535 ports hote hain. Ye virtual endpoints hain jahan 
se network communication hoti hai.

Think of ports as doors in a building:
- Total 65536 darwaze (0-65535)
- Kuch khule hain, kuch band hain
- Har darwaze se alag service milti hai

PORT CATEGORIES:

┌─────────────────────────────────────────────────────────────────────────┐
│                         PORT CATEGORIES                                  │
├────────────────┬────────────────────────────────────────────────────────┤
│ Port Range     │ Description / Common Services                        │
├────────────────┼────────────────────────────────────────────────────────┤
│ 0-1023         │ WELL-KNOWN PORTS (System Ports)                     │
│                │ 20-21: FTP (File Transfer)                          │
│                │ 22: SSH (Secure Shell)                              │
│                │ 23: Telnet                                          │
│                │ 25: SMTP (Email)                                    │
│                │ 53: DNS (Domain Name)                               │
│                │ 80: HTTP (Web)                                      │
│                │ 110: POP3 (Email)                                   │
│                │ 143: IMAP (Email)                                   │
│                │ 443: HTTPS (Secure Web)                             │
│                │ 3306: MySQL (Database)                              │
│                │ 3389: RDP (Remote Desktop)                          │
├────────────────┼────────────────────────────────────────────────────────┤
│ 1024-49151     │ REGISTERED PORTS                                    │
│                │ User applications ke liye reserved                  │
│                │ Example: 3306 MySQL, 5432 PostgreSQL                │
├────────────────┼────────────────────────────────────────────────────────┤
│ 49152-65535    │ DYNAMIC/PRIVATE PORTS                               │
│                │ Temporary connections ke liye                       │
│                │ Client-side connections use karte hain              │
└────────────────┴────────────────────────────────────────────────────────┘

PORT STATES:

Jab Nmap scan karta hai, ports ki different states hoti hain:

OPEN: Port pe service chal rahi hai, connection accept karti hai
CLOSED: Port accessible hai, lekin koi service nahi chal rahi
FILTERED: Firewall port ko block kar raha hai
UNFILTERED: Accessible but open/closed pata nahi
OPEN|FILTERED: Uncertain state
CLOSED|FILTERED: Uncertain state

---

[SECTION 3: NMAP INSTALLATION IN TERMUX - 7:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye Nmap install karte hain Termux mein!

STEP 1: Update Termux

Pehle Termux ko update karein:

    pkg update && pkg upgrade -y

Ye command package lists refresh karega aur installed packages ko 
update karega.

STEP 2: Install Nmap

Nmap install karna bahut simple hai:

    pkg install nmap -y

Ye command Nmap package download aur install kar dega.

STEP 3: Verify Installation

Installation complete hone ke baad verify karein:

    nmap --version

Output mein Nmap version number dikhega jaise:
Nmap version 7.94 ( https://nmap.org )

STEP 4: Check Nmap Help

Nmap ki help dekhne ke liye:

    nmap -h

Ye command Nmap ke saare options dikhayegi.

INSTALLATION TROUBLESHOOTING:

Agar installation mein problem aaye:

1. "Unable to locate package":
   - pkg update run karein
   - Internet connection check karein

2. "Permission denied":
   - Termux ko storage permission dein
   - termux-setup-storage run karein

3. Slow download:
   - Different network use karein
   - VPN try karein

┌─────────────────────────────────────────────────────────────────────────┐
│                    NMAP INSTALLATION SUMMARY                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Step 1: pkg update && pkg upgrade -y                                   │
│  Step 2: pkg install nmap -y                                            │
│  Step 3: nmap --version                                                 │
│  Step 4: nmap -h                                                        │
│                                                                          │
│  ✅ Installation Complete!                                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 4: BASIC SCAN - nmap <target> - 10:00 to 13:00]
─────────────────────────────────────────────────────────────────────────────

Ab Nmap use karna seekhte hain. Sabse basic command:

BASIC SCAN SYNTAX:

    nmap <target>

Target kuch bhi ho sakta hai:
- IP Address: nmap 192.168.1.1
- Hostname: nmap scanme.nmap.org
- Domain: nmap example.com

EXAMPLE:

    nmap scanme.nmap.org

Ye command scanme.nmap.org scan karega. Ye Nmap ki official test 
site hai - practice ke liye perfect!

OUTPUT SAMJHNA:

Starting Nmap 7.94 ( https://nmap.org ) at 2024-01-15 10:00 IST
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.25s latency).
Not shown: 992 closed tcp ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
9929/tcp  open  nping-echo
31337/tcp open  Elite

Nmap done: 1 IP address (1 host up) scanned in 15.23 seconds

OUTPUT BREAKDOWN:

- "Starting Nmap..." - Scan start ho gaya
- "Host is up" - Target accessible hai
- "Not shown: 992 closed tcp ports" - 992 ports closed hain
- PORT table - Open ports ki list
- STATE - Port ki state (open/closed/filtered)
- SERVICE - Service ka naam
- "Nmap done" - Scan complete

SCAN YOUR LOCAL ROUTER:

Apne router ka IP dhundhein:

    ip route | grep default

Phir scan karein:

    nmap 192.168.1.1

(Apne router ka IP use karein)

⚠️ NOTE: Sirf apne network ya authorized targets scan karein!

---

[SECTION 5: TCP CONNECT SCAN (-sT) - 13:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab scan types seekhte hain. Pehla - TCP Connect Scan.

-sT: TCP CONNECT SCAN

    nmap -sT <target>

Ye scan:
- Complete TCP connection establish karta hai
- Three-way handshake complete hoti hai
- Most reliable scan type
- Root permission ki zarurat NAHI
- Easily detected by firewalls/IDS

HOW IT WORKS:

1. Nmap target pe SYN packet bhejta hai
2. Agar port open hai: SYN-ACK aata hai
3. Nmap ACK bhejta hai (connection complete)
4. Nmap RST bhejta hai (connection close)

THREE-WAY HANDSHAKE:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TCP THREE-WAY HANDSHAKE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  CLIENT (Nmap)                      SERVER (Target)                      │
│       │                                   │                              │
│       │────── SYN ──────────────────────>│  (Step 1)                    │
│       │                                   │                              │
│       │<───── SYN-ACK ──────────────────│  (Step 2)                    │
│       │                                   │                              │
│       │────── ACK ──────────────────────>│  (Step 3)                    │
│       │                                   │                              │
│       │         CONNECTION ESTABLISHED    │                              │
│       │                                   │                              │
│       │────── RST ──────────────────────>│  (Nmap closes)               │
│       │                                   │                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

EXAMPLE:

    nmap -sT 192.168.1.1

    nmap -sT scanme.nmap.org

ADVANTAGES:
- No root required
- Works on all systems
- Reliable results

DISADVANTAGES:
- Slow
- Easily detected
- Logs mein dikhai deta hai

---

[SECTION 6: SYN SCAN (-sS) - 15:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Ab SYN Scan - sabse popular scan type!

-sS: SYN SCAN (STEALTH SCAN)

    nmap -sS <target>

Ye scan:
- Half-open scan (connection complete nahi hota)
- Sirf SYN packet bhejta hai, ACK nahi bhejta
- ROOT permission REQUIRED
- Fast aur stealthy
- Harder to detect

HOW IT WORKS:

1. Nmap SYN packet bhejta hai
2. Open port: SYN-ACK aata hai
3. Nmap RST bhejta hai (connection complete NAHI)
4. Closed port: RST aata hai

SYN SCAN VS TCP CONNECT:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SYN SCAN vs TCP CONNECT SCAN                          │
├────────────────┬─────────────────────────────────────────────────────────┤
│ Feature        │ SYN Scan (-sS)    │ TCP Connect (-sT)                 │
├────────────────┼─────────────────────────────────────────────────────────┤
│ Root Required  │ ✅ Yes           │ ❌ No                              │
│ Speed          │ Fast             │ Slower                            │
│ Stealth        │ Better           │ Easily detected                   │
│ Reliability    │ Good             │ Best                              │
│ Logging        │ Less logged      │ Fully logged                      │
│ Default Scan   │ Yes (if root)    │ Yes (without root)                │
└────────────────┴─────────────────────────────────────────────────────────┘

EXAMPLE (Requires Root/Sudo):

Termux mein root ke liye:

    su

Phir scan:

    nmap -sS 192.168.1.1

⚠️ NOTE: Termux mein -sS ke liye root phone chahiye. Agar root 
nahi hai to -sT use karein.

SYN SCAN ADVANTAGES:
- Very fast
- Harder to detect
- Less likely to be logged
- Default scan when running as root

---

[SECTION 7: UDP SCAN (-sU) - 17:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

UDP Scan - UDP ports ke liye!

-sU: UDP SCAN

    nmap -sU <target>

Ye scan:
- UDP ports scan karta hai
- ROOT required
- Slower than TCP scans
- Important for DNS, DHCP, SNMP

WHY UDP SCAN?

UDP services bahut important hain:
- DNS (Port 53)
- DHCP (Port 67, 68)
- SNMP (Port 161)
- NTP (Port 123)
- Many gaming servers

EXAMPLE:

    nmap -sU 192.168.1.1

COMMON UDP PORTS:

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON UDP PORTS                                      │
├────────────────┬─────────────────────────────────────────────────────────┤
│ Port           │ Service                                           │
├────────────────┼─────────────────────────────────────────────────────────┤
│ 53/udp         │ DNS (Domain Name System)                          │
│ 67,68/udp      │ DHCP (Dynamic Host Configuration)                 │
│ 69/udp         │ TFTP (Trivial File Transfer)                      │
│ 123/udp        │ NTP (Network Time Protocol)                       │
│ 161/udp        │ SNMP (Simple Network Management)                  │
│ 500/udp        │ IKE (Internet Key Exchange)                       │
│ 514/udp        │ Syslog                                            │
│ 520/udp        │ RIP (Routing Information Protocol)                │
└────────────────┴─────────────────────────────────────────────────────────┘

UDP SCAN SLOW HOTA HAI:

UDP scan slow hai kyunki:
- UDP connectionless protocol hai
- No acknowledgment
- Timeout wait karna padta hai

Speed up karne ke liye:

    nmap -sU --top-ports 20 <target>

Ye sirf top 20 UDP ports scan karega.

TCP + UDP COMBINED SCAN:

    nmap -sS -sU <target>

Ya:

    nmap -sT -sU <target>

---

[SECTION 8: VERSION DETECTION (-sV) - 19:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Version Detection - Service versions dhundhna!

-sV: VERSION DETECTION

    nmap -sV <target>

Ye scan:
- Running services ki version detect karta hai
- Open ports pe probes bhejta hai
- Specific versions identify karta hai
- Helps in vulnerability assessment

WHY VERSION DETECTION IMPORTANT HAI?

Jab aap version jaante ho:
- Known vulnerabilities dhundh sakte ho
- Exploits select kar sakte ho
- Patch status check kar sakte ho

EXAMPLE:

    nmap -sV scanme.nmap.org

OUTPUT EXAMPLE:

PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13
80/tcp   open  http    Apache httpd 2.4.7 ((Ubuntu))
443/tcp  open  ssl     OpenSSL

VERSION DETECTION INTENSITY:

    nmap -sV --version-intensity <0-9> <target>

- 0: Least intensive (fast)
- 9: Most intensive (slow, thorough)

EXAMPLE:

    nmap -sV --version-intensity 5 scanme.nmap.org

ALL INFO SCAN (-A):

-A combines multiple scans:

    nmap -A <target>

Ye command:
- OS detection (-O)
- Version detection (-sV)
- Script scanning (-sC)
- Traceroute (--traceroute)

    nmap -A scanme.nmap.org

---

[SECTION 9: OS DETECTION (-O) - 21:00 to 22:30]
─────────────────────────────────────────────────────────────────────────────

OS Detection - Operating System dhundhna!

-O: OS DETECTION

    nmap -O <target>

Ye scan:
- Target ka Operating System detect karta hai
- ROOT REQUIRED
- TCP/IP fingerprinting use karta hai
- Accuracy depends on open ports

HOW IT WORKS:

Nmap different OS ke TCP/IP stacks alag behave karte hain:
- Initial packet sequence numbers
- Window sizes
- TCP options order
- ICMP responses

EXAMPLE:

    nmap -O 192.168.1.1

OUTPUT EXAMPLE:

OS CPE: cpe:/o:linux:linux_kernel:3
OS details: Linux 3.2 - 3.16
Network Distance: 1 hop

OS DETECTION LIMITATIONS:

┌─────────────────────────────────────────────────────────────────────────┐
│                    OS DETECTION LIMITATIONS                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✓ Requires at least 1 open AND 1 closed port                          │
│  ✓ Root/sudo required                                                   │
│  ✓ Works best on local network                                          │
│  ✓ Can be fooled by OS fingerprint obfuscation                          │
│  ✓ Virtual machines may give false results                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

LIMIT OS DETECTION:

    nmap -O --osscan-limit <target>

Sirf scan karein jab good conditions hain.

GUESS OS AGGRESSIVELY:

    nmap -O --osscan-guess <target>

---

[SECTION 10: PORT SPECIFICATION - 22:30 to 24:30]
─────────────────────────────────────────────────────────────────────────────

Ab port specification seekhte hain - specific ports scan karna.

SCAN SPECIFIC PORT (-p):

    nmap -p 80 <target>
    nmap -p 22,80,443 <target>
    nmap -p 1-1000 <target>

EXAMPLES:

    # Single port
    nmap -p 80 scanme.nmap.org

    # Multiple ports
    nmap -p 22,80,443,3306 scanme.nmap.org

    # Port range
    nmap -p 1-1000 scanme.nmap.org

    # Specific UDP port
    nmap -sU -p 53 scanme.nmap.org

    # TCP and UDP ports
    nmap -p T:80,U:53 scanme.nmap.org

SCAN ALL PORTS (-p-):

    nmap -p- <target>

Ye command ALL 65535 ports scan karega. Slow hai lekin comprehensive.

EXAMPLE:

    nmap -p- 192.168.1.1

FAST SCAN (-F):

    nmap -F <target>

Ye sirf 100 most common ports scan karta hai. Quick results.

EXAMPLE:

    nmap -F scanme.nmap.org

TOP PORTS:

    nmap --top-ports 20 <target>
    nmap --top-ports 100 <target>
    nmap --top-ports 1000 <target>

PORT SPECIFICATION SUMMARY:

┌─────────────────────────────────────────────────────────────────────────┐
│                    PORT SPECIFICATION OPTIONS                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  -p 22               Single port                                        │
│  -p 22,80,443        Multiple ports                                     │
│  -p 1-1000           Port range                                         │
│  -p-                 All 65535 ports                                    │
│  -F                  Fast scan (100 common ports)                       │
│  --top-ports 20      Top 20 most common ports                           │
│  -p T:80,U:53        Specific TCP and UDP ports                         │
│  -p U:53,111,137     UDP only ports                                     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 11: OUTPUT FORMATS - 24:30 to 26:30]
─────────────────────────────────────────────────────────────────────────────

Output save karna important hai for documentation and analysis.

NORMAL OUTPUT (-oN):

    nmap -oN scan_results.txt <target>

Human-readable format. Good for reports.

EXAMPLE:

    nmap -oN myscan.txt scanme.nmap.org

XML OUTPUT (-oX):

    nmap -oX scan_results.xml <target>

Machine-readable format. Good for tools and parsing.

EXAMPLE:

    nmap -oX myscan.xml scanme.nmap.org

GREPABLE OUTPUT (-oG):

    nmap -oG scan_results.gnmap <target>

Easy to parse with grep, awk, etc.

EXAMPLE:

    nmap -oG myscan.gnmap scanme.nmap.org

ALL FORMATS (-oA):

    nmap -oA scan_results <target>

Creates .nmap, .xml, and .gnmap files together.

EXAMPLE:

    nmap -oA myscan scanme.nmap.org

OUTPUT FORMAT COMPARISON:

┌─────────────────────────────────────────────────────────────────────────┐
│                    OUTPUT FORMAT COMPARISON                              │
├────────────────┬─────────────────────────────────────────────────────────┤
│ Format         │ Best For                                          │
├────────────────┼─────────────────────────────────────────────────────────┤
│ -oN (Normal)   │ Human reading, Reports                            │
│ -oX (XML)      │ Tools, Parsing, Import to other apps              │
│ -oG (Grepable) │ Command line processing, grep, awk                │
│ -oA (All)      │ Complete documentation                            │
└────────────────┴─────────────────────────────────────────────────────────┘

VERBOSE OUTPUT (-v):

    nmap -v <target>

More details during scan.

    nmap -vv <target>

Even more verbose.

DEBUG OUTPUT (-d):

    nmap -d <target>

Debug information for troubleshooting.

---

[SECTION 12: TIMING TEMPLATES - 26:30 to 28:30]
─────────────────────────────────────────────────────────────────────────────

Timing templates se scan speed control karte hain.

TIMING TEMPLATES (-T):

    nmap -T<0-5> <target>

TEMPLATES:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TIMING TEMPLATES                                      │
├────────────────┬─────────────────────────────────────────────────────────┤
│ Template       │ Description                                        │
├────────────────┼─────────────────────────────────────────────────────────┤
│ -T0 (Paranoid) │ Very slow, IDS evasion, 5 min between probes       │
│ -T1 (Sneaky)   │ Slow, IDS evasion, 15 sec between probes           │
│ -T2 (Polite)   │ Slower, uses less bandwidth                        │
│ -T3 (Normal)   │ Default speed                                      │
│ -T4 (Aggressive)│ Fast, reliable network, quick scans               │
│ -T5 (Insane)   │ Very fast, may miss ports, fast network only       │
└────────────────┴─────────────────────────────────────────────────────────┘

WHEN TO USE WHAT:

-T0, -T1: IDS/Firewall evasion, stealthy scans
-T2: Polite scanning, shared networks
-T3: Default, general use
-T4: Fast networks, internal scans
-T5: Very fast networks, quick assessment

EXAMPLES:

    # Stealthy scan
    nmap -T1 -sS scanme.nmap.org

    # Fast scan
    nmap -T4 -F scanme.nmap.org

    # Aggressive scan
    nmap -T4 -A scanme.nmap.org

RECOMMENDATION:

For beginners:
- Use -T3 or -T4 for most scans
- Use -T1 or -T2 for stealth

---

[SECTION 13: PRACTICAL SCAN EXAMPLES - 28:30 to 31:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch practical examples dekhte hain:

EXAMPLE 1: Quick Network Discovery

    nmap -sn 192.168.1.0/24

-sn = ping scan, no port scan
Ye network mein saare live hosts dhundhega.

EXAMPLE 2: Common Port Scan

    nmap -sV -p 22,80,443,3306,8080 192.168.1.1

Service versions on common ports.

EXAMPLE 3: Full TCP Scan with Scripts

    nmap -sS -sV -sC -p- 192.168.1.1

Complete scan with default scripts.

EXAMPLE 4: Fast Scan All Hosts

    nmap -T4 -F 192.168.1.0/24

Quick scan of entire network.

EXAMPLE 5: UDP Top Ports

    nmap -sU --top-ports 20 192.168.1.1

Top 20 UDP ports scan.

EXAMPLE 6: Save All Results

    nmap -A -oA fullscan 192.168.1.1

Aggressive scan, save in all formats.

EXAMPLE 7: Scan Multiple Targets

    nmap 192.168.1.1 192.168.1.2 192.168.1.3

    nmap 192.168.1.1-10

    nmap -iL targets.txt

EXAMPLE 8: Scan with Reason

    nmap --reason 192.168.1.1

Shows why port is marked as open/closed.

EXAMPLE 9: Detect Vulnerabilities

    nmap --script vuln 192.168.1.1

Run vulnerability detection scripts.

EXAMPLE 10: Comprehensive Scan

    nmap -sS -sU -sV -O -p- -oA full_scan 192.168.1.1

Complete scan - TCP, UDP, versions, OS, all ports, save results.

---

[SECTION 14: LEGAL AND ETHICAL USE - 31:00 to 33:00]
─────────────────────────────────────────────────────────────────────────────

⚠️ IMPORTANT: ETHICAL AND LEGAL CONSIDERATIONS

Nmap ek powerful tool hai. Power ke saath responsibility aati hai.

LEGAL WARNING:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ⚠️ LEGAL WARNING ⚠️                                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PORT SCANNING WITHOUT PERMISSION IS ILLEGAL IN MANY COUNTRIES!        │
│                                                                          │
│  ✓ ONLY scan systems you OWN or have WRITTEN PERMISSION for           │
│  ✓ Unauthorized scanning can result in criminal charges                 │
│  ✓ You may be banned from networks/ISPs                                 │
│  ✓ Scanning can trigger security alerts                                 │
│                                                                          │
│  THIS VIDEO IS FOR EDUCATIONAL PURPOSES ONLY                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

SAFE TARGETS FOR PRACTICE:

1. scanme.nmap.org
   - Nmap's official test server
   - Specifically for learning

2. your own devices
   - Your phone
   - Your computer
   - Your router

3. Your local network (with permission)
   - Home network
   - Lab environment

4. Authorized test environments
   - CTF challenges
   - HackTheBox
   - TryHackMe
   - VulnHub

WHAT NOT TO SCAN:

❌ Government websites
❌ Banking websites
❌ Healthcare systems
❌ Any production system without permission
❌ Random internet IPs

ETHICAL HACKER'S CODE:

1. Always get written permission
2. Document everything you do
3. Report vulnerabilities responsibly
4. Don't cause damage or downtime
5. Follow responsible disclosure
6. Stay within legal boundaries

---

[SECTION 15: SUMMARY & COMMANDS RECAP - 33:00 to 35:00]
─────────────────────────────────────────────────────────────────────────────

CHAPTER SUMMARY:

Aaj humne seekha:

✅ Nmap kya hai - Network Mapper, security scanner
✅ Ports kya hote hain - 0-65535, well-known, registered, dynamic
✅ Nmap installation in Termux - pkg install nmap
✅ Basic scan - nmap <target>
✅ TCP Connect Scan (-sT) - Complete handshake, no root
✅ SYN Scan (-sS) - Stealth, requires root
✅ UDP Scan (-sU) - UDP ports, requires root
✅ Version Detection (-sV) - Service versions
✅ OS Detection (-O) - Operating system fingerprinting
✅ Port Specification - -p, -p-, -F
✅ Output Formats - -oN, -oX, -oG, -oA
✅ Timing Templates - -T0 to -T5
✅ Legal and ethical use

ESSENTIAL COMMANDS YAAD RAKHEIN:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ESSENTIAL NMAP COMMANDS                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  INSTALLATION:                                                          │
│  pkg install nmap -y                                                    │
│                                                                          │
│  BASIC SCANS:                                                           │
│  nmap <target>                  Basic scan                              │
│  nmap -sT <target>              TCP Connect scan                        │
│  nmap -sS <target>              SYN scan (requires root)                │
│  nmap -sU <target>              UDP scan (requires root)                │
│                                                                          │
│  DETECTION:                                                             │
│  nmap -sV <target>              Version detection                       │
│  nmap -O <target>               OS detection (requires root)            │
│  nmap -A <target>               All detection                           │
│                                                                          │
│  PORTS:                                                                 │
│  nmap -p 22,80,443 <target>     Specific ports                          │
│  nmap -p- <target>              All 65535 ports                         │
│  nmap -F <target>               Fast scan (100 ports)                   │
│                                                                          │
│  OUTPUT:                                                                │
│  nmap -oN file.txt <target>     Normal output                           │
│  nmap -oX file.xml <target>     XML output                              │
│  nmap -oA filename <target>     All formats                             │
│                                                                          │
│  TIMING:                                                                │
│  nmap -T4 <target>              Fast scan                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[OUTRO - 35:00 to 36:00]
─────────────────────────────────────────────────────────────────────────────

Dosto, Chapter 25 complete!

Nmap basics seekh liye. Ye foundation bahut important hai. Next chapter 
mein hum Nmap Advanced Techniques seekhenge - NSE scripts, firewall 
evasion, aur automation.

Practice karte rahien. Apne local network scan karein. Different 
options try karein. Experience is the best teacher!

Yaad rakhein:
- Sirf authorized targets scan karein
- Results save karein
- Outputs analyze karein

Agar ye video helpful lagi:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 26!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Nmap Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         NMAP ARCHITECTURE                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      NMAP CORE ENGINE                           │   │
│   │              (Port Scanning, Service Detection)                 │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      SCAN MODULES                               │   │
│   ├─────────────────────────────────────────────────────────────────┤   │
│   │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐           │   │
│   │  │ TCP SCAN │ │ SYN SCAN │ │ UDP SCAN │ │HOST DISC │           │   │
│   │  └──────────┘ └──────────┘ └──────────┘ └──────────┘           │   │
│   │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐           │   │
│   │  │ VERSION  │ │    OS    │ │  SCRIPT  │ │TRACEROUTE│           │   │
│   │  │ DETECT   │ │ DETECT   │ │ ENGINE   │ │          │           │   │
│   │  └──────────┘ └──────────┘ └──────────┘ └──────────┘           │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    OUTPUT FORMATTERS                            │   │
│   │        Normal, XML, Grepable, Script Kiddie                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      NSE SCRIPTS                                │   │
│   │              (600+ Lua Scripts for Advanced Scanning)           │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Scan Types Comparison

| Scan Type | Flag | Root Required | Description | Speed |
|-----------|------|---------------|-------------|-------|
| TCP Connect | -sT | No | Full TCP connection | Slow |
| SYN Scan | -sS | Yes | Half-open scan | Fast |
| UDP Scan | -sU | Yes | UDP ports | Slow |
| Version | -sV | No | Service versions | Medium |
| OS Detection | -O | Yes | Operating system | Fast |

### 3. Port Ranges and Services

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON PORTS AND SERVICES                             │
├────────────────┬─────────────────────────────────────────────────────────┤
│ Port           │ Service                                          │
├────────────────┼─────────────────────────────────────────────────────────┤
│ 20, 21/tcp     │ FTP - File Transfer Protocol                     │
│ 22/tcp         │ SSH - Secure Shell                               │
│ 23/tcp         │ Telnet - Remote Terminal (insecure)              │
│ 25/tcp         │ SMTP - Email Sending                             │
│ 53/tcp,udp     │ DNS - Domain Name System                         │
│ 67,68/udp      │ DHCP - Dynamic IP Assignment                     │
│ 69/udp         │ TFTP - Trivial File Transfer                     │
│ 80/tcp         │ HTTP - Web Server                                │
│ 110/tcp        │ POP3 - Email Retrieval                           │
│ 123/udp        │ NTP - Network Time Protocol                      │
│ 143/tcp        │ IMAP - Email Retrieval                           │
│ 161/udp        │ SNMP - Network Management                        │
│ 389/tcp        │ LDAP - Directory Service                         │
│ 443/tcp        │ HTTPS - Secure Web                               │
│ 445/tcp        │ SMB - Windows File Sharing                       │
│ 993/tcp        │ IMAPS - Secure IMAP                              │
│ 995/tcp        │ POP3S - Secure POP3                              │
│ 1433/tcp       │ MS SQL - Microsoft Database                      │
│ 1521/tcp       │ Oracle Database                                  │
│ 3306/tcp       │ MySQL - Database                                 │
│ 3389/tcp       │ RDP - Remote Desktop Protocol                    │
│ 5432/tcp       │ PostgreSQL - Database                            │
│ 5900/tcp       │ VNC - Remote Desktop                             │
│ 6379/tcp       │ Redis - In-memory Database                       │
│ 8080/tcp       │ HTTP Alternate - Web Server                      │
│ 8443/tcp       │ HTTPS Alternate                                  │
│ 27017/tcp      │ MongoDB - NoSQL Database                         │
└────────────────┴─────────────────────────────────────────────────────────┘
```

### 4. TCP Handshake and Scan Types

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TCP CONNECT SCAN (-sT)                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  OPEN PORT:                                                             │
│  Client          Server          Client          Server                  │
│   SYN    ────────>               ACK    ────────>                        │
│           <─────── SYN-ACK               <─────── RST                    │
│                                                                          │
│  CLOSED PORT:                                                           │
│  Client          Server                                                  │
│   SYN    ────────>                                                       │
│           <─────── RST                                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│                    SYN SCAN (-sS)                                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  OPEN PORT:                                                             │
│  Client          Server                                                  │
│   SYN    ────────>                                                       │
│           <─────── SYN-ACK                                               │
│   RST    ────────>  (No connection established)                          │
│                                                                          │
│  CLOSED PORT:                                                           │
│  Client          Server                                                  │
│   SYN    ────────>                                                       │
│           <─────── RST                                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5. Timing Templates Details

| Template | Flag | Timing | Use Case |
|----------|------|--------|----------|
| Paranoid | -T0 | 5 min between probes | IDS evasion, extremely slow |
| Sneaky | -T1 | 15 sec between probes | IDS evasion, slow |
| Polite | -T2 | 0.4 sec between probes | Bandwidth conservation |
| Normal | -T3 | Default | General use |
| Aggressive | -T4 | Fast | Fast networks |
| Insane | -T5 | Very fast | Very fast networks only |

---

## 🔧 INSTALLATION GUIDE

### Step-by-Step Termux Installation

```
Step 1: Update Termux
├── Run: pkg update && pkg upgrade -y
└── Wait for completion

Step 2: Install Nmap
├── Run: pkg install nmap -y
└── Confirm installation with Y when prompted

Step 3: Verify Installation
├── Run: nmap --version
└── Check version output

Step 4: Test Basic Scan
├── Run: nmap scanme.nmap.org
└── Verify scan works

Step 5: Check Available Options
├── Run: nmap -h
└── Review all options
```

### Additional Tools for Network Scanning

```bash
# Install additional networking tools
pkg install netcat -y      # Netcat for manual port testing
pkg install ncat -y        # Nmap's netcat (part of nmap)
pkg install nping -y       # Nmap's ping tool
pkg install masscan -y     # Fast port scanner (optional)
```

---

## 📋 COMMANDS REFERENCE

### 25+ Essential Nmap Commands

```bash
#═══════════════════════════════════════════════════════════════════════════
# NMAP COMMANDS REFERENCE - 25+ COMMANDS
#═══════════════════════════════════════════════════════════════════════════

#═══════════════════════════════════════════════════════════════════════════
# BASIC SCANS
#═══════════════════════════════════════════════════════════════════════════

# 1. Basic scan (default 1000 ports)
nmap 192.168.1.1

# 2. Scan hostname
nmap scanme.nmap.org

# 3. Scan multiple targets
nmap 192.168.1.1 192.168.1.2 192.168.1.3

# 4. Scan IP range
nmap 192.168.1.1-254

# 5. Scan entire subnet
nmap 192.168.1.0/24

#═══════════════════════════════════════════════════════════════════════════
# SCAN TYPES
#═══════════════════════════════════════════════════════════════════════════

# 6. TCP Connect scan (no root required)
nmap -sT 192.168.1.1

# 7. SYN scan (requires root)
nmap -sS 192.168.1.1

# 8. UDP scan (requires root)
nmap -sU 192.168.1.1

# 9. TCP ACK scan
nmap -sA 192.168.1.1

# 10. TCP Window scan
nmap -sW 192.168.1.1

# 11. TCP Maimon scan
nmap -sM 192.168.1.1

#═══════════════════════════════════════════════════════════════════════════
# DETECTION SCANS
#═══════════════════════════════════════════════════════════════════════════

# 12. Version detection
nmap -sV 192.168.1.1

# 13. OS detection (requires root)
nmap -O 192.168.1.1

# 14. Aggressive scan (OS + Version + Scripts + Traceroute)
nmap -A 192.168.1.1

#═══════════════════════════════════════════════════════════════════════════
# PORT SPECIFICATION
#═══════════════════════════════════════════════════════════════════════════

# 15. Scan specific port
nmap -p 80 192.168.1.1

# 16. Scan multiple ports
nmap -p 22,80,443,3306 192.168.1.1

# 17. Scan port range
nmap -p 1-1000 192.168.1.1

# 18. Scan all 65535 ports
nmap -p- 192.168.1.1

# 19. Fast scan (100 common ports)
nmap -F 192.168.1.1

# 20. Top N ports
nmap --top-ports 20 192.168.1.1

# 21. Scan specific TCP and UDP ports
nmap -p T:22,80,U:53 192.168.1.1

#═══════════════════════════════════════════════════════════════════════════
# HOST DISCOVERY
#═══════════════════════════════════════════════════════════════════════════

# 22. Ping scan only (no port scan)
nmap -sn 192.168.1.0/24

# 23. Skip host discovery
nmap -Pn 192.168.1.1

# 24. TCP SYN ping
nmap -PS22,80 192.168.1.1

# 25. TCP ACK ping
nmap -PA80,443 192.168.1.1

#═══════════════════════════════════════════════════════════════════════════
# OUTPUT OPTIONS
#═══════════════════════════════════════════════════════════════════════════

# 26. Save normal output
nmap -oN scan.txt 192.168.1.1

# 27. Save XML output
nmap -oX scan.xml 192.168.1.1

# 28. Save grepable output
nmap -oG scan.gnmap 192.168.1.1

# 29. Save all formats
nmap -oA scan_results 192.168.1.1

# 30. Verbose output
nmap -v 192.168.1.1

#═══════════════════════════════════════════════════════════════════════════
# TIMING AND PERFORMANCE
#═══════════════════════════════════════════════════════════════════════════

# 31. Paranoid timing (very slow)
nmap -T0 192.168.1.1

# 32. Sneaky timing
nmap -T1 192.168.1.1

# 33. Aggressive timing
nmap -T4 192.168.1.1

# 34. Insane timing
nmap -T5 192.168.1.1

#═══════════════════════════════════════════════════════════════════════════
# SCRIPT SCANNING
#═══════════════════════════════════════════════════════════════════════════

# 35. Default scripts
nmap -sC 192.168.1.1

# 36. Vulnerability scripts
nmap --script vuln 192.168.1.1

# 37. Safe scripts
nmap --script safe 192.168.1.1

#═══════════════════════════════════════════════════════════════════════════
# COMBINED PRACTICAL SCANS
#═══════════════════════════════════════════════════════════════════════════

# 38. Quick comprehensive scan
nmap -T4 -F 192.168.1.0/24

# 39. Full scan with version detection
nmap -sV -p- 192.168.1.1

# 40. Complete scan with all options
nmap -A -T4 -p- -oA fullscan 192.168.1.1

# 41. Network discovery scan
nmap -sn 192.168.1.0/24 -oG hosts.gnmap

# 42. Web server scan
nmap -sV -p 80,443,8080,8443 192.168.1.1

# 43. Database server scan
nmap -sV -p 1433,1521,3306,5432,27017 192.168.1.1

# 44. Windows machine scan
nmap -sS -sU -p 135,137,138,139,445,3389 192.168.1.1

# 45. Test target (official Nmap server)
nmap -A scanme.nmap.org
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Network Discovery

```bash
# Task: Discover all live hosts on your network

# Step 1: Find your network range
ip route | grep default

# Step 2: Run ping scan to find live hosts
nmap -sn 192.168.1.0/24

# Step 3: Save the results
nmap -sn 192.168.1.0/24 -oG live_hosts.gnmap

# Step 4: Parse results to get IP list
grep "Up" live_hosts.gnmap | awk '{print $2}'

# Expected: List of all live hosts on your network
```

### Exercise 2: Port Scanning Practice

```bash
# Task: Scan a test server and identify services

# Step 1: Basic scan
nmap scanme.nmap.org

# Step 2: Service version scan
nmap -sV scanme.nmap.org

# Step 3: Specific ports scan
nmap -p 22,80,443,9929,31337 scanme.nmap.org

# Step 4: Save results
nmap -sV -oN scan_results.txt scanme.nmap.org

# Expected: List of open ports with service versions
```

### Exercise 3: Comprehensive Router Scan

```bash
# Task: Scan your home router comprehensively

# Step 1: Find router IP
ip route | grep default | awk '{print $3}'

# Step 2: Quick scan
nmap -F <router-ip>

# Step 3: Full port scan
nmap -p- <router-ip>

# Step 4: Service detection
nmap -sV -p- <router-ip>

# Step 5: Save all results
nmap -sV -p- -oA router_scan <router-ip>

# Expected: Complete port map of your router
```

### Exercise 4: Timing Template Comparison

```bash
# Task: Compare different timing templates

# Step 1: Run with T2 (polite)
time nmap -T2 -F scanme.nmap.org

# Step 2: Run with T4 (aggressive)
time nmap -T4 -F scanme.nmap.org

# Step 3: Compare the time difference

# Expected: T4 should be significantly faster
```

### Exercise 5: Output Format Practice

```bash
# Task: Generate different output formats and analyze

# Step 1: Generate all output formats
nmap -F -oA myscan scanme.nmap.org

# Step 2: View normal output
cat myscan.nmap

# Step 3: Parse grepable output
grep "open" myscan.gnmap

# Step 4: View XML structure
head -50 myscan.xml

# Expected: Understanding of different output formats
```

### Exercise 6: Create Target List

```bash
# Task: Create and scan from a target list

# Step 1: Create target file
cat > targets.txt << 'EOF'
scanme.nmap.org
192.168.1.1
localhost
EOF

# Step 2: Scan from file
nmap -iL targets.txt

# Step 3: Save results
nmap -F -iL targets.txt -oN targets_scan.txt

# Expected: Scan multiple targets from file
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Unable to locate package nmap"

```bash
# Cause: Outdated package lists

# Solution 1: Update package lists
pkg update

# Solution 2: Full upgrade
pkg update && pkg upgrade -y

# Solution 3: Check internet connection
ping -c 3 google.com

# Solution 4: Try apt instead of pkg
apt update && apt install nmap -y
```

### Problem 2: "Operation not permitted" for SYN/UDP scans

```bash
# Cause: SYN (-sS) and UDP (-sU) scans require root

# Solution 1: Use TCP Connect scan instead (no root needed)
nmap -sT <target>

# Solution 2: If you have rooted phone
su
nmap -sS <target>

# Solution 3: Check if you have root
whoami
# If output is not "root", you don't have root access
```

### Problem 3: Scan taking too long

```bash
# Cause: Scanning all ports or slow network

# Solution 1: Use fast scan
nmap -F <target>

# Solution 2: Use aggressive timing
nmap -T4 <target>

# Solution 3: Limit ports
nmap --top-ports 100 <target>

# Solution 4: Combine optimizations
nmap -T4 -F <target>
```

### Problem 4: "Host seems down"

```bash
# Cause: Firewall blocking ping or host is down

# Solution 1: Skip host discovery
nmap -Pn <target>

# Solution 2: Use different ping methods
nmap -PS22,80,443 <target>

# Solution 3: Check if target is really up
ping <target>
```

### Problem 5: "nmap: command not found"

```bash
# Cause: Nmap not installed or PATH issue

# Solution 1: Install nmap
pkg install nmap -y

# Solution 2: Check if installed
pkg list-installed | grep nmap

# Solution 3: Reinstall
pkg uninstall nmap
pkg install nmap -y

# Solution 4: Check PATH
echo $PATH
which nmap
```

### Problem 6: Permission denied for output files

```bash
# Cause: Writing to protected directory

# Solution 1: Write to home directory
nmap -oN ~/scan.txt <target>

# Solution 2: Write to current directory
nmap -oN ./scan.txt <target>

# Solution 3: Check storage permission
termux-setup-storage

# Solution 4: Check write permissions
ls -la .
```

### Problem 7: Scan results showing all ports filtered

```bash
# Cause: Firewall blocking scan

# Solution 1: Use different scan technique
nmap -sT <target>  # Instead of -sS

# Solution 2: Use slower timing
nmap -T2 <target>

# Solution 3: Try source port manipulation
nmap --source-port 53 <target>

# Solution 4: Combine techniques
nmap -Pn -sT -T2 <target>
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔍 NMAP                          │
│   NETWORK SCANNER                  │
│                                    │
│   ✓ Port Scanning                  │
│   ✓ Service Detection              │
│   ✓ OS Fingerprinting              │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Beginner Friendly**
```
┌────────────────────────────────────┐
│  🎯 NMAP FOR BEGINNERS             │
│                                    │
│  ┌──────────────────────────────┐  │
│  │ pkg install nmap             │  │
│  │ nmap -sS target              │  │
│  └──────────────────────────────┘  │
│                                    │
│  25+ COMMANDS TUTORIAL             │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Eye-Catching**
```
┌────────────────────────────────────┐
│  ⚡ MASTER NMAP IN 20 MIN          │
│                                    │
│  🔓 Port Scanning                  │
│  🎭 Stealth Scans                  │
│  🔍 Service Detection              │
│                                    │
│  COMPLETE BEGINNER GUIDE           │
│  Chapter 25 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔍 Termux Full Course - Chapter 25: Nmap Installation & Basics

🔥 In this video you'll learn:
• Nmap kya hai aur kyun important hai
• Termux mein Nmap install karna
• Port scanning fundamentals
• TCP, SYN, UDP scans
• Version aur OS detection
• Output formats save karna
• 25+ practical Nmap commands

⏱️ Timestamps:
0:00 - Introduction
0:50 - What is Nmap?
4:00 - Port Scanning Fundamentals
7:00 - Nmap Installation in Termux
10:00 - Basic Scan (nmap <target>)
13:00 - TCP Connect Scan (-sT)
15:00 - SYN Scan (-sS)
17:00 - UDP Scan (-sU)
19:00 - Version Detection (-sV)
21:00 - OS Detection (-O)
22:30 - Port Specification
24:30 - Output Formats
26:30 - Timing Templates
28:30 - Practical Examples
31:00 - Legal & Ethical Use
33:00 - Summary

📥 Commands from this video:
pkg install nmap -y
nmap scanme.nmap.org
nmap -sT <target>
nmap -sV <target>
nmap -A <target>

🎯 Practice Targets:
• scanme.nmap.org (Official test server)
• Your own devices
• Your local network (with permission)

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Nmap #NmapTutorial #Termux #PortScanning #NetworkSecurity #T3rmuxk1ng #EthicalHacking #TermuxHindi #CyberSecurity

---
⚠️ Disclaimer: This video is for educational purposes only. Only scan systems you own or have explicit permission to test. Unauthorized port scanning may be illegal in your jurisdiction.
```

### Tags List

```
nmap, nmap tutorial, nmap port scanning, nmap basics, 
nmap for beginners, nmap hindi, nmap termux, termux nmap,
port scanning, network scanning, ethical hacking, 
cybersecurity, penetration testing, security tools,
tcp scan, syn scan, udp scan, os detection,
version detection, nmap commands, t3rmuxk1ng,
termux course, termux tutorial hindi, network security,
hacking tools, security scanning, vulnerability assessment
```

### Hashtags

```
#Nmap #PortScanning #NetworkSecurity #EthicalHacking 
#CyberSecurity #Termux #TermuxCourse #T3rmuxk1ng 
#NmapTutorial #PenetrationTesting #SecurityTools 
#NmapBasics #NetworkScanning #HindiTutorial
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| Nmap Official Site | https://nmap.org/ |
| Nmap Documentation | https://nmap.org/book/man.html |
| Nmap Reference Guide | https://nmap.org/book/nmap-documentation.html |
| NSE Scripts | https://nmap.org/nsedoc/ |
| Nmap GitHub | https://github.com/nmap/nmap |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Nmap Book | Free online book by Fyodor |
| Nmap Cheat Sheet | Quick reference for commands |
| Practice Target | scanme.nmap.org |
| TryHackMe | Nmap rooms for practice |
| HackTheBox | Real-world targets |

### Community

| Platform | Link |
|----------|------|
| Nmap IRC | #nmap on Libera.Chat |
| Stack Overflow | [nmap] tag |
| Reddit | r/netsec, r/howtohack |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 26, verify:

- [ ] Nmap installed successfully in Termux
- [ ] `nmap --version` shows version
- [ ] Basic scan tested on scanme.nmap.org
- [ ] TCP Connect scan (-sT) understood
- [ ] Difference between -sT and -sS understood
- [ ] Port specification (-p, -p-, -F) practiced
- [ ] Output formats (-oN, -oX, -oG, -oA) tested
- [ ] Timing templates (-T0 to -T5) understood
- [ ] Legal and ethical considerations understood
- [ ] Practiced on authorized targets only

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 26: Nmap Advanced Techniques**

- Nmap Scripting Engine (NSE)
- Default scripts (-sC)
- Vulnerability detection scripts
- Firewall evasion techniques
- Host discovery methods
- Idle scan (-sI)
- Decoy scans
- Automation and reporting

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
