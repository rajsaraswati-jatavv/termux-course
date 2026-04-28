# Chapter 26: Nmap Advanced Techniques

> **Module:** 5 - Networking  
> **Chapter:** 26 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed NSE, evasion, and automation |
| Commands Reference | 25+ advanced Nmap commands |
| Practice Exercises | Hands-on scanning labs |
| Troubleshooting | Common Nmap issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 26
Title: Nmap Advanced Techniques | NSE Scripts & Firewall Evasion | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon T3rmuxk1ng, aur aaj ek bahut powerful chapter hai -
Chapter 26: Nmap Advanced Techniques!

Pichhle chapter mein humne Nmap ki basics seekhi thi - installation, 
basic scans, port scanning techniques. Aaj hum advanced level pe jaayenge.

Aaj hum seekhenge:
- Nmap Scripting Engine (NSE) - Nmap ko aur bhi powerful banana
- Firewall evasion techniques - Security bypass karna
- Host discovery methods - Hidden hosts dhundhna
- Custom NSE scripts banana
- Automation aur reporting

Ye chapter ethical hackers aur penetration testers ke liye bahut 
important hai. Chaliye shuru karte hain!

Play button dabaiye, like karein, subscribe karein - notification bell ke saath.

---

[SECTION 1: NMAP SCRIPTING ENGINE INTRODUCTION - 0:50 to 3:30]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle - Nmap Scripting Engine ya NSE kya hai?

NSE Nmap ki sabse powerful feature hai. Ye Nmap ko ek simple port 
scanner se badhkar ek complete vulnerability scanner bana deta hai.

Imagine karein - aap ek network scan karte ho, aur saath hi:
- Vulnerabilities detect ho jaate hain
- Default credentials check ho jaate hain
- Service versions pata chal jaate hain
- Backdoors detect ho jaate hain
- Exploits automatically test ho jaate hain

Ye sab NSE scripts karte hain!

NSE scripts Lua programming language mein likhe jaate hain. Nmap ke 
saath 600+ built-in scripts aate hain, aur aap custom bhi bana sakte ho.

SCRIPT CATEGORIES:

┌─────────────────────────────────────────────────────────────────────────┐
│                    NSE SCRIPT CATEGORIES                                 │
├────────────────┬────────────────────────────────────────────────────────┤
│ Category       │ Purpose                                                │
├────────────────┼────────────────────────────────────────────────────────┤
│ auth          │ Authentication related scripts                         │
│ broadcast     │ Network broadcast discovery                            │
│ brute         │ Brute force attacks                                    │
│ default       │ Default scripts (run with -sC)                         │
│ discovery     │ Network and service discovery                          │
│ dos           │ Denial of service scripts                              │
│ exploit       │ Exploitation scripts                                   │
│ external      │ Third-party services                                   │
│ fuzzer        │ Fuzzing scripts                                        │
│ intrusive     │ Intrusive scripts (may crash services)                 │
│ malware       │ Malware detection                                      │
│ safe          │ Safe scripts (won't harm target)                       │
│ version       │ Version detection scripts                              │
│ vuln          │ Vulnerability detection                                │
└────────────────┴────────────────────────────────────────────────────────┘

---

[SECTION 2: -sC AND --script USAGE - 3:30 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab commands seekhte hain. Sabse pehle default scripts:

DEFAULT SCRIPTS (-sC):

    nmap -sC target.com

-sC option default scripts run karta hai. Ye safe aur useful scripts 
ka collection hai jo:
- Service detection
- Version detection
- Basic vulnerability checks
- Common misconfigurations

Example output dikhaata hai ki scripts automatically run hote hain.

SPECIFIC SCRIPTS (--script):

    nmap --script <script-name> target.com

Specific script run karna:

    nmap --script http-title target.com

Multiple scripts:

    nmap --script http-title,http-headers target.com

Script category run karna:

    nmap --script vuln target.com

    nmap --script auth target.com

    nmap --script "safe and discovery" target.com

Wildcard use karna:

    nmap --script "http-*" target.com

Ye saare http scripts run karega.

SCRIPTS LIST KARNA:

    nmap --script-help all

    nmap --script-help http-title

Scripts ki details dekhni ho:

    nmap --script-help "vuln and safe"

---

[SECTION 3: COMMON NSE SCRIPTS - 6:00 to 9:30]
─────────────────────────────────────────────────────────────────────────────

Ab kuch important scripts detail mein dekhein:

1. AUTH SCRIPTS (Authentication):

    nmap --script auth target.com

Ye authentication bypass, default credentials, aur weak auth detect karta hai.

Specific auth scripts:
    nmap --script ssh-auth-methods target.com
    nmap --script mysql-enum target.com
    nmap --script ftp-anon target.com

2. VULN SCRIPTS (Vulnerability):

    nmap --script vuln target.com

Ye saare vulnerability detection scripts run karta hai.

Specific vuln scripts:
    nmap --script ssl-heartbleed target.com
    nmap --script ssl-poodle target.com
    nmap --script smb-vuln-ms17-010 target.com
    nmap --script http-sql-injection target.com
    nmap --script http-xssed target.com

3. EXPLOIT SCRIPTS:

    nmap --script exploit target.com

Specific exploit scripts:
    nmap --script http-shellshock target.com
    nmap --script clamav-exec target.com

⚠️ WARNING: Exploit scripts dangerous ho sakte hain. Sirf authorized 
testing pe use karein.

4. DISCOVERY SCRIPTS:

    nmap --script discovery target.com

Specific discovery scripts:
    nmap --script dns-brute target.com
    nmap --script http-enum target.com
    nmap --script smb-enum-shares target.com
    nmap --script ldap-search target.com

5. BRUTE FORCE SCRIPTS:

    nmap --script brute target.com

Specific brute scripts:
    nmap --script ssh-brute target.com
    nmap --script ftp-brute target.com
    nmap --script http-brute target.com
    nmap --script mysql-brute target.com

---

[SECTION 4: --script-args USAGE - 9:30 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Script arguments se aap scripts ko customize kar sakte ho.

SYNTAX:

    nmap --script <script> --script-args <arg1>=<value1>,<arg2>=<value2> target

EXAMPLES:

1. HTTP Title with custom user-agent:

    nmap --script http-title --script-args http.useragent="Mozilla/5.0" target.com

2. SSH Brute Force with custom credentials:

    nmap --script ssh-brute --script-args userdb=users.txt,passdb=passwords.txt target.com

3. DNS Brute with custom wordlist:

    nmap --script dns-brute --script-args dns-brute.hostlist=hosts.txt target.com

4. HTTP Enum with specific base path:

    nmap --script http-enum --script-args http-enum.basepath=/admin/ target.com

5. MySQL brute with specific credentials:

    nmap --script mysql-brute --script-args mysql-brute.timeout=30 target.com

6. SMB Enum with credentials:

    nmap --script smb-enum-shares --script-args smbuser=admin,smbpass=password target.com

COMMON ARGUMENTS:

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON SCRIPT ARGUMENTS                               │
├─────────────────────────────────────────────────────────────────────────┤
│ http.useragent      │ Custom User-Agent string                          │
│ http.timeout        │ HTTP timeout in seconds                           │
│ userdb              │ Username database file                            │
│ passdb              │ Password database file                            │
│ unpwdb.timelimit    │ Time limit for brute force                        │
│ smbuser             │ SMB username                                      │
│ smbpass             │ SMB password                                      │
│ ssh     │ SSH timeout                                       │
│ mysql-brute.timeout │ MySQL brute timeout                               │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 5: HOST DISCOVERY TECHNIQUES - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab host discovery techniques seekhte hain. Kabhi-kabhi hosts hidden 
hote hain, firewalls block karte hain. Kaise dhundhein?

-sn: Ping Scan (No Port Scan):

    nmap -sn 192.168.1.0/24

Ye sirf check karta hai ki host up hai ya nahi, ports scan nahi karta.

-PS: TCP SYN Ping:

    nmap -PS target.com

    nmap -PS80,443,22 target.com

SYN packets bhejta hai. Agar response aaya to host up hai.

-PA: TCP ACK Ping:

    nmap -PA target.com

    nmap -PA80,443 target.com

ACK packets bhejta hai. Firewalls sometimes ACK allow karte hain.

-PU: UDP Ping:

    nmap -PU target.com

    nmap -PU53,161 target.com

UDP packets bhejta hai. Good for sneaking past firewalls.

-PE: ICMP Echo Request:

    nmap -PE target.com

Normal ping request. Many firewalls block this.

-PP: ICMP Timestamp Request:

    nmap -PP target.com

ICMP timestamp request. Sometimes firewalls miss this.

-PM: ICMP Address Mask Request:

    nmap -PM target.com

Another ICMP technique.

-PN: No Ping (Skip Host Discovery):

    nmap -PN target.com

Treat all hosts as online. Useful when firewall blocks ping.

COMBINED HOST DISCOVERY:

    nmap -PS22,80 -PA80,443 -PU53 target.com

    nmap -PE -PP -PS443 target.com

Multiple techniques combine karo for better results!

---

[SECTION 6: FIREWALL EVASION - 15:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab firewall evasion techniques - sabse important part!

-f: Fragmentation:

    nmap -f target.com

Packets ko fragments mein todta hai. Some firewalls can't reassemble.

--mtu: Custom MTU:

    nmap --mtu 24 target.com

Custom MTU size. Fragmentation with specific size.

-D: Decoy Scan:

    nmap -D RND:10 target.com

    nmap -D decoy1,decoy2,ME target.com

Decoy IPs add karta hai. Target ko lagta hai multiple systems 
scan kar rahe hain. Real IP hidden rahta hai.

-S: Spoof Source IP:

    nmap -S 192.168.1.100 target.com

Source IP spoof karta hai. Note: Response aapko nahi milega 
unless you're on the same network!

--source-port: Source Port Manipulation:

    nmap --source-port 53 target.com

    nmap -g 53 target.com

Source port 53 (DNS) use karta hai. Many firewalls allow DNS traffic.

-e: Specify Interface:

    nmap -e wlan0 target.com

Specific network interface use karna.

--badsum: Send Bad Checksum:

    nmap --badsum target.com

Invalid checksum bhejta hai. Some firewalls pass bad packets.

TTL Manipulation:

    nmap --ttl 128 target.com

Set custom TTL value.

DATA LENGTH:

    nmap --data-length 25 target.com

Random data add karta hai packets mein.

TIMING TEMPLATES:

    nmap -T0 target.com  # Paranoid - very slow
    nmap -T1 target.com  # Sneaky
    nmap -T2 target.com  # Polite
    nmap -T3 target.com  # Normal
    nmap -T4 target.com  # Aggressive
    nmap -T5 target.com  # Insane - very fast

T0 and T1 are good for IDS evasion.

---

[SECTION 7: IDLE SCAN (-sI) - 18:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Idle scan ek unique technique hai - completely anonymous scanning!

How it works:
1. Find a zombie host (idle machine)
2. Send spoofed packets to target
3. Monitor zombie's IP ID to see if target responded

SYNTAX:

    nmap -sI <zombie-host> target.com

Example:

    nmap -sI 192.168.1.50 target.com

FINDING ZOMBIE HOST:

Zombie host should be:
- Idle (not generating traffic)
- Predictable IP ID sequence
- Not behind NAT

Good candidates:
- Printers
- Old servers
- IoT devices

IDLE SCAN ADVANTAGES:
- Completely anonymous
- Target doesn't see your IP
- Bypasses firewall rules

DISADVANTAGES:
- Slow
- Requires suitable zombie
- May not work behind NAT

---

[SECTION 8: FTP BOUNCE SCAN - 20:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

FTP Bounce scan ek old technique hai but still interesting!

SYNTAX:

    nmap -b <username:password@ftp-server> target.com

Example:

    nmap -b anonymous:anonymous@ftp.example.com target.com

How it works:
1. Connect to FTP server
2. Use FTP's PORT command to connect to target
3. Scan through FTP server

This was used to hide attacker's IP. Modern FTP servers 
usually block this (FTP bounce protection).

USAGE TODAY:
- Legacy systems
- Misconfigured FTP servers
- Educational purposes

---

[SECTION 9: IPv6 SCANNING - 21:30 to 23:00]
─────────────────────────────────────────────────────────────────────────────

IPv6 scanning bhi important hai as IPv6 adoption increases.

ENABLE IPv6:

    nmap -6 target.com

IPv6 ADDRESS FORMATS:

    nmap -6 2001:db8::1

    nmap -6 2001:db8::1-100

IPv6 NETWORK SCANNING:

IPv6 addresses bahut bade hain - 128 bits. Full network scan 
impossible hai. Use targeted scanning:

    nmap -6 -p 80,443,22 target.com

IPv6 HOST DISCOVERY:

    nmap -6 -sn target.com

LIMITATIONS:
- Slower than IPv4
- Less script support
- Larger address space = harder to scan

---

[SECTION 10: ZENMAP ALTERNATIVE ON ANDROID - 23:00 to 24:30]
─────────────────────────────────────────────────────────────────────────────

Zenmap Nmap ka GUI version hai for desktop. Android pe Zenmap nahi hai.

ALTERNATIVES:

1. Nmap Termux (Command Line):
   - Full Nmap functionality
   - All features available
   - Command line interface

2. Network Mapper (Android App):
   - GUI wrapper for Nmap
   - Limited features
   - Good for beginners

3. DroidNmap:
   - Simple GUI
   - Basic scans only

4. Use Termux + Custom Scripts:
   - Best option
   - Create your own GUI-like experience
   - Full control

TERMUX SCRIPTS FOR NMAP:

Create simple menu-driven scripts:

    #!/bin/bash
    # nmap-menu.sh

    echo "=== NMAP SCANNER ==="
    echo "1. Quick Scan"
    echo "2. Full Scan"
    echo "3. Vulnerability Scan"
    read -p "Choice: " choice
    read -p "Target: " target

    case $choice in
        1) nmap -sV $target ;;
        2) nmap -A $target ;;
        3) nmap --script vuln $target ;;
    esac

---

[SECTION 11: CREATING CUSTOM NSE SCRIPTS - 24:30 to 27:00]
─────────────────────────────────────────────────────────────────────────────

Ab custom NSE script banana seekhte hain!

NSE SCRIPT STRUCTURE:

```lua
-- Script metadata
description = [[
Script description here
]]

author = "Your Name"
license = "Same as Nmap"
categories = {"default", "safe"}

-- Import libraries
local http = require "http"
local nmap = require "nmap"

-- The action function
action = function(host, port)
    -- Your script logic here
    return "Result"
end
```

SIMPLE HTTP BANNER SCRIPT:

```lua
description = [[
Simple HTTP banner grabber
]]

author = "T3rmuxk1ng"
license = "Same as Nmap"
categories = {"discovery", "safe"}

local http = require "http"

action = function(host, port)
    local response = http.get(host, port, "/")
    if response and response.header then
        local server = response.header["server"]
        if server then
            return "Server: " .. server
        end
    end
    return nil
end
```

SAVE AND RUN:

1. Save as: myscript.nse
2. Place in: /usr/share/nmap/scripts/ (or ~/.nmap/scripts/)
3. Run: nmap --script myscript.nse target.com

TESTING SCRIPTS:

    nmap --script myscript.nse --script-trace target.com

--script-trace shows what script is doing.

---

[SECTION 12: NMAP AUTOMATION SCRIPTS - 27:00 to 29:00]
─────────────────────────────────────────────────────────────────────────────

Automation ke liye scripts banana important hai.

BASH AUTOMATION SCRIPT:

```bash
#!/bin/bash
# nmap-automator.sh

TARGET=$1
OUTPUT_DIR="nmap_scan_$(date +%Y%m%d_%H%M%S)"

mkdir -p $OUTPUT_DIR

echo "[*] Starting comprehensive scan of $TARGET"

# Quick scan
echo "[*] Running quick scan..."
nmap -T4 -F $TARGET -oN $OUTPUT_DIR/quick_scan.txt

# Version detection
echo "[*] Running version scan..."
nmap -sV $TARGET -oN $OUTPUT_DIR/version_scan.txt

# Script scan
echo "[*] Running script scan..."
nmap -sC $TARGET -oN $OUTPUT_DIR/script_scan.txt

# Vulnerability scan
echo "[*] Running vulnerability scan..."
nmap --script vuln $TARGET -oN $OUTPUT_DIR/vuln_scan.txt

# Full scan
echo "[*] Running full scan..."
nmap -p- -sV -sC $TARGET -oN $OUTPUT_DIR/full_scan.txt

echo "[*] All scans complete! Results in $OUTPUT_DIR"
```

PYTHON AUTOMATION:

```python
#!/usr/bin/env python3
import subprocess
import sys

def nmap_scan(target, scan_type):
    scans = {
        'quick': ['nmap', '-T4', '-F', target],
        'full': ['nmap', '-p-', '-sV', '-sC', target],
        'vuln': ['nmap', '--script', 'vuln', target],
        'udp': ['nmap', '-sU', '--top-ports', '100', target]
    }
    
    cmd = scans.get(scan_type)
    if cmd:
        result = subprocess.run(cmd, capture_output=True, text=True)
        return result.stdout
    return "Unknown scan type"

if __name__ == "__main__":
    if len(sys.argv) < 3:
        print("Usage: python nmap_auto.py <target> <scan_type>")
        sys.exit(1)
    
    target = sys.argv[1]
    scan_type = sys.argv[2]
    
    print(nmap_scan(target, scan_type))
```

---

[SECTION 13: REPORTING AND DOCUMENTATION - 29:00 to 31:00]
─────────────────────────────────────────────────────────────────────────────

Professional reporting important hai for penetration testing.

OUTPUT FORMATS:

1. Normal Output (-oN):

    nmap -oN scan_results.txt target.com

Human-readable format.

2. XML Output (-oX):

    nmap -oX scan_results.xml target.com

Machine-readable, can be parsed by other tools.

3. Grepable Output (-oG):

    nmap -oG scan_results.gnmap target.com

Easy to parse with grep/awk.

4. All Formats (-oA):

    nmap -oA scan_results target.com

Creates .nmap, .xml, and .gnmap files.

ENHANCED REPORTING:

Using nmap-report tools:

    pip install nmap-report
    nmap-report -i scan.xml -o report.html

CUSTOM REPORT SCRIPT:

```bash
#!/bin/bash
# generate-report.sh

TARGET=$1
DATE=$(date +%Y-%m-%d)

nmap -sV -sC -oX /tmp/scan.xml $TARGET

cat << EOF > report_$DATE.md
# Nmap Scan Report

**Target:** $TARGET
**Date:** $DATE
**Scanner:** Nmap $(nmap --version | head -1)

## Open Ports

$(nmap -sV -sC $TARGET | grep open)

## Services Detected

$(nmap -sV $TARGET | grep -E "^[0-9]+")

## Script Results

$(nmap -sC $TARGET)

EOF

echo "Report saved to report_$DATE.md"
```

---

[SECTION 14: SUMMARY & BEST PRACTICES - 31:00 to 33:00]
─────────────────────────────────────────────────────────────────────────────

CHAPTER SUMMARY:

Aaj humne seekha:
✅ Nmap Scripting Engine (NSE) introduction
✅ -sC aur --script usage
✅ Common NSE scripts - auth, vuln, exploit
✅ --script-args customization
✅ Host discovery techniques - -sn, -PS, -PA, -PU
✅ Firewall evasion - -f, --mtu, -D, -S
✅ Decoy scans
✅ Idle scan (-sI)
✅ FTP bounce scan
✅ IPv6 scanning
✅ Zenmap alternatives on Android
✅ Creating custom NSE scripts
✅ Nmap automation
✅ Reporting and documentation

BEST PRACTICES:

✓ Always get authorization before scanning
✓ Start with safe scripts first
✓ Document everything
✓ Use appropriate timing templates
✓ Combine multiple techniques for better results
✓ Save output in multiple formats
✓ Test scripts on your own systems first
✓ Keep Nmap and scripts updated
✓ Use --reason to understand results
✓ Combine with other tools for comprehensive testing

IMPORTANT COMMANDS YAAD RAKHEIN:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ESSENTIAL ADVANCED NMAP COMMANDS                      │
├─────────────────────────────────────────────────────────────────────────┤
│ nmap -sC target            │ Run default scripts                        │
│ nmap --script vuln target  │ Run vulnerability scripts                  │
│ nmap --script-args ...     │ Pass arguments to scripts                  │
│ nmap -sn 192.168.1.0/24    │ Ping sweep (no port scan)                  │
│ nmap -PS,PA,PU target      │ Advanced host discovery                    │
│ nmap -f target             │ Fragmented packets                         │
│ nmap -D RND:10 target      │ Decoy scan                                 │
│ nmap -sI zombie target     │ Idle scan                                  │
│ nmap -oA results target    │ Output all formats                         │
│ nmap -T4 -A target         │ Aggressive timing + OS detection           │
└─────────────────────────────────────────────────────────────────────────┘

---

[OUTRO - 33:00 to 34:00]
─────────────────────────────────────────────────────────────────────────────

Dosto, Chapter 26 complete!

Nmap ek incredible tool hai. Jo humne aaj seekha wo advanced 
techniques hain. Practice karte rahien - practice makes perfect!

Yaad rakhein: With great power comes great responsibility.
Sirf authorized systems pe scan karein. Ethical hacking seekh rahe ho,
toh ethical bhi raho.

Agar ye video helpful lagi:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Next Chapter 27 mein hum Netcat mastery seekhenge - network 
hacker ka Swiss Army knife!

Thank you for watching! See you in Chapter 27!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Nmap Scripting Engine (NSE) Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NMAP SCRIPTING ENGINE ARCHITECTURE                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      NMAP CORE ENGINE                           │   │
│   │              (Port Scanning, Service Detection)                 │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                        NSE LAYER                                │   │
│   ├─────────────────────────────────────────────────────────────────┤   │
│   │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐           │   │
│   │  │  AUTH    │ │  VULN    │ │ EXPLOIT  │ │ DISCOVERY │           │   │
│   │  │ SCRIPTS  │ │ SCRIPTS  │ │ SCRIPTS  │ │ SCRIPTS   │           │   │
│   │  └──────────┘ └──────────┘ └──────────┘ └──────────┘           │   │
│   │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐           │   │
│   │  │  BRUTE   │ │  SAFE    │ │INTRUSIVE │ │  CUSTOM   │           │   │
│   │  │ SCRIPTS  │ │ SCRIPTS  │ │ SCRIPTS  │ │ SCRIPTS   │           │   │
│   │  └──────────┘ └──────────┘ └──────────┘ └──────────┘           │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      LUA INTERPRETER                            │   │
│   │                 (Script Execution Engine)                       │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      NSE LIBRARIES                              │   │
│   │   http, ssh, ftp, smb, mysql, ssl, dns, ldap, etc.              │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Script Execution Phases

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NSE SCRIPT EXECUTION PHASES                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PHASE 1: RULE                                                          │
│  ├── portrule: Run for specific ports                                   │
│  ├── hostrule: Run for specific hosts                                   │
│  └── Determines when script runs                                        │
│                                                                          │
│  PHASE 2: ACTION                                                        │
│  ├── Main script logic                                                  │
│  ├── Network operations                                                 │
│  └── Returns results                                                    │
│                                                                          │
│  PHASE 3: POSTPROCESSING                                                │
│  ├── Format output                                                      │
│  └── Display to user                                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Host Discovery Techniques Comparison

| Technique | Flag | Description | Bypasses |
|-----------|------|-------------|----------|
| No Ping | -Pn | Skip discovery | All ping blocks |
| SYN Ping | -PS | TCP SYN packets | Basic firewalls |
| ACK Ping | -PA | TCP ACK packets | Stateful firewalls |
| UDP Ping | -PU | UDP packets | TCP-only firewalls |
| ICMP Echo | -PE | Standard ping | Non-ICMP blocks |
| ICMP Timestamp | -PP | Timestamp request | Some ICMP blocks |
| ICMP Mask | -PM | Address mask request | Some ICMP blocks |
| ARP Ping | -PR | ARP requests | Local network only |

### 4. Firewall Evasion Techniques

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    FIREWALL EVASION TECHNIQUES                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  FRAGMENTATION (-f)                                                     │
│  ├── Breaks packets into small fragments                                │
│  ├── Some firewalls can't reassemble                                    │
│  └── Example: nmap -f target.com                                        │
│                                                                          │
│  MTU MANIPULATION (--mtu)                                               │
│  ├── Custom Maximum Transmission Unit                                   │
│  ├── Creates specific fragment sizes                                    │
│  └── Example: nmap --mtu 24 target.com                                  │
│                                                                          │
│  DECOY SCAN (-D)                                                        │
│  ├── Multiple fake source IPs                                           │
│  ├── Hides real attacker IP                                             │
│  └── Example: nmap -D RND:10 target.com                                 │
│                                                                          │
│  SOURCE PORT MANIPULATION (--source-port)                               │
│  ├── Uses trusted port numbers                                          │
│  ├── Often bypasses firewall rules                                      │
│  └── Example: nmap --source-port 53 target.com                          │
│                                                                          │
│  TIMING TEMPLATES (-T)                                                  │
│  ├── T0: Paranoid (very slow)                                           │
│  ├── T1: Sneaky (slow)                                                  │
│  ├── T2: Polite (moderate)                                              │
│  ├── T3: Normal (default)                                               │
│  ├── T4: Aggressive (fast)                                              │
│  └── T5: Insane (very fast)                                             │
│                                                                          │
│  DATA PADDING (--data-length)                                           │
│  ├── Adds random data to packets                                        │
│  ├── Makes packets look different                                       │
│  └── Example: nmap --data-length 25 target.com                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5. NSE Script Categories Deep Dive

| Category | Count | Purpose | Risk Level |
|----------|-------|---------|------------|
| **auth** | 30+ | Authentication testing | Medium |
| **broadcast** | 20+ | Network broadcast discovery | Safe |
| **brute** | 50+ | Brute force attacks | High |
| **default** | 100+ | Safe default scripts | Low |
| **discovery** | 150+ | Service/host discovery | Low |
| **dos** | 10+ | DoS testing | Very High |
| **exploit** | 100+ | Exploitation | Very High |
| **fuzzer** | 10+ | Fuzzing | Medium |
| **intrusive** | 200+ | Intrusive testing | High |
| **malware** | 10+ | Malware detection | Safe |
| **safe** | 300+ | Non-intrusive | Very Low |
| **vuln** | 200+ | Vulnerability detection | Medium |

### 6. Idle Scan Mechanism

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         IDLE SCAN MECHANISM                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  STEP 1: Get Zombie's Current IP ID                                     │
│  ├── Attacker probes zombie                                             │
│  └── Records IP ID value (e.g., 1000)                                   │
│                                                                          │
│  STEP 2: Send Spoofed SYN to Target                                     │
│  ├── Source IP = Zombie's IP                                            │
│  ├── Target responds to Zombie (not Attacker)                           │
│  └── Zombie's IP ID increments if port is open                          │
│                                                                          │
│  STEP 3: Probe Zombie Again                                             │
│  ├── Attacker probes zombie again                                       │
│  └── Compare IP ID value                                                │
│                                                                          │
│  ANALYSIS:                                                              │
│  ├── IP ID increased by 1 = No response from target (closed)            │
│  ├── IP ID increased by 2 = Target responded (open)                     │
│  └── Target never sees attacker's real IP                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 7. Output Formats Comparison

| Format | Flag | Use Case | Human Readable |
|--------|------|----------|----------------|
| Normal | -oN | General reporting | Yes |
| XML | -oX | Tool parsing, CI/CD | No |
| Grepable | -oG | Grep/awk processing | Partially |
| JSON | -oX + conversion | API integration | No |
| All | -oA | Multiple purposes | Mixed |

---

## 📋 COMMANDS REFERENCE

### NSE Script Commands

```bash
# DEFAULT SCRIPTS
nmap -sC target.com                    # Run default scripts
nmap --script default target.com       # Same as -sC

# SPECIFIC CATEGORY
nmap --script auth target.com          # Authentication scripts
nmap --script vuln target.com          # Vulnerability scripts
nmap --script discovery target.com     # Discovery scripts
nmap --script exploit target.com       # Exploit scripts
nmap --script brute target.com         # Brute force scripts
nmap --script safe target.com          # Safe scripts only

# MULTIPLE CATEGORIES
nmap --script "auth,vuln" target.com
nmap --script "safe and discovery" target.com

# SPECIFIC SCRIPT
nmap --script http-title target.com
nmap --script ssh-auth-methods target.com
nmap --script ssl-heartbleed target.com
nmap --script smb-vuln-ms17-010 target.com

# WILDCARD
nmap --script "http-*" target.com      # All HTTP scripts
nmap --script "ssh-*" target.com       # All SSH scripts

# SCRIPT WITH ARGUMENTS
nmap --script http-title --script-args http.useragent="CustomAgent" target.com
nmap --script ssh-brute --script-args userdb=users.txt,passdb=passes.txt target.com
nmap --script dns-brute --script-args dns-brute.hostlist=hosts.txt target.com

# SCRIPT HELP
nmap --script-help all                 # List all scripts
nmap --script-help http-title          # Specific script help
nmap --script-help "vuln and safe"     # Category help

# SCRIPT TRACE (debug)
nmap --script http-title --script-trace target.com

# UPDATE SCRIPTS
nmap --script-updatedb
```

### Host Discovery Commands

```bash
# PING SCAN (No port scan)
nmap -sn 192.168.1.0/24                # Ping sweep network
nmap -sn 192.168.1.1-100               # Range ping sweep

# TCP SYN PING
nmap -PS target.com                    # SYN ping (default ports)
nmap -PS80,443,22 target.com           # SYN ping (specific ports)

# TCP ACK PING
nmap -PA target.com                    # ACK ping (default)
nmap -PA80,443 target.com              # ACK ping (specific)

# UDP PING
nmap -PU target.com                    # UDP ping
nmap -PU53,161,123 target.com          # UDP ping (specific)

# ICMP PING
nmap -PE target.com                    # ICMP echo request
nmap -PP target.com                    # ICMP timestamp
nmap -PM target.com                    # ICMP address mask

# NO PING (Skip host discovery)
nmap -Pn target.com                    # Treat all hosts as up

# COMBINED DISCOVERY
nmap -PS22,80 -PA443 -PU53 target.com  # Multiple techniques
nmap -PE -PP -PS443 target.com         # ICMP + TCP combined

# ARP DISCOVERY (local)
nmap -PR target.com                    # ARP ping
nmap -PR 192.168.1.0/24                # ARP sweep (local only)
```

### Firewall Evasion Commands

```bash
# FRAGMENTATION
nmap -f target.com                     # Fragment packets
nmap -f -f target.com                  # Double fragmentation
nmap --mtu 24 target.com               # Custom MTU size

# DECOY SCAN
nmap -D RND:10 target.com              # Random 10 decoys
nmap -D RND:target.com                 # Random decoys
nmap -D decoy1,decoy2,ME target.com    # Specific decoys + you

# SOURCE IP SPOOFING
nmap -S 192.168.1.100 target.com       # Spoof source IP
nmap -S 192.168.1.100 -e wlan0 target.com  # Spoof + interface

# SOURCE PORT
nmap --source-port 53 target.com       # Source port 53 (DNS)
nmap -g 80 target.com                  # Source port 80
nmap --source-port 443 target.com      # Source port 443

# BAD CHECKSUM
nmap --badsum target.com               # Invalid checksum

# DATA LENGTH
nmap --data-length 25 target.com       # Add 25 bytes random data
nmap --data-length 100 target.com      # Add 100 bytes

# TTL
nmap --ttl 128 target.com              # Set TTL to 128
nmap --ttl 64 target.com               # Set TTL to 64

# TIMING
nmap -T0 target.com                    # Paranoid (slowest)
nmap -T1 target.com                    # Sneaky
nmap -T2 target.com                    # Polite
nmap -T3 target.com                    # Normal
nmap -T4 target.com                    # Aggressive
nmap -T5 target.com                    # Insane (fastest)

# COMBINED EVASION
nmap -f -D RND:5 --source-port 53 -T2 target.com
```

### Idle Scan Commands

```bash
# BASIC IDLE SCAN
nmap -sI zombie_host target.com

# WITH PORT SPECIFICATION
nmap -sI zombie_host -p 80,443,22 target.com

# WITH PROBE PORT
nmap -sI zombie_host:80 target.com     # Use port 80 on zombie
```

### FTP Bounce Scan

```bash
# FTP BOUNCE
nmap -b anonymous:anonymous@ftp.server.com target.com
nmap -b user:pass@ftp.example.com target.com
```

### IPv6 Scanning

```bash
# IPv6 SCAN
nmap -6 target.com                     # IPv6 scan
nmap -6 -p 80,443,22 target.com        # Specific ports
nmap -6 -sV target.com                 # Version detection
nmap -6 --script http-title target.com # Script scan
```

### Output and Reporting

```bash
# OUTPUT FORMATS
nmap -oN results.txt target.com        # Normal output
nmap -oX results.xml target.com        # XML output
nmap -oG results.gnmap target.com      # Grepable output
nmap -oA results target.com            # All formats

# VERBOSE
nmap -v target.com                     # Verbose
nmap -vv target.com                    # Very verbose

# DEBUG
nmap -d target.com                     # Debug
nmap -dd target.com                    # More debug

# REASON
nmap --reason target.com               # Show reason for port state

# OPEN ONLY
nmap --open target.com                 # Show only open ports

# APPEND
nmap --append-output -oN results.txt target.com
```

### Complete Advanced Scan Commands

```bash
# COMPREHENSIVE SCAN
nmap -A -T4 -v target.com              # Aggressive + verbose

# STEALTH SCAN
nmap -sS -T2 -f -D RND:3 target.com    # Stealth with decoys

# VULNERABILITY SCAN
nmap -sV --script vuln -oA vuln_scan target.com

# FULL PORT SCAN
nmap -p- -sV -sC -T4 -oA full_scan target.com

# UDP SCAN
nmap -sU --top-ports 100 -T4 target.com

# COMBINED TCP/UDP
nmap -sS -sU -p T:1-1000,U:53,161 -T4 target.com

# QUICK DISCOVERY
nmap -sn -PS22,80,443 -PA80,443 192.168.1.0/24

# INTERNAL NETWORK SCAN
nmap -sS -sV -O -T4 192.168.1.0/24
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: NSE Script Exploration

```bash
# Task: Explore and use various NSE scripts

# Step 1: List all available scripts
nmap --script-help all | head -100

# Step 2: Search for specific script
nmap --script-help | grep -i "http"

# Step 3: Run default scripts on a test target
nmap -sC scanme.nmap.org

# Step 4: Run vulnerability scripts
nmap --script vuln scanme.nmap.org

# Step 5: Run specific script with help
nmap --script-help http-title
nmap --script http-title scanme.nmap.org

# Step 6: Use script arguments
nmap --script http-enum --script-args http-enum.basepath=/ scanme.nmap.org
```

### Exercise 2: Host Discovery Practice

```bash
# Task: Practice various host discovery techniques

# Step 1: Ping sweep your local network (adjust for your network)
nmap -sn 192.168.1.0/24

# Step 2: Use SYN ping
nmap -sn -PS22,80,443 192.168.1.0/24

# Step 3: Use UDP ping
nmap -sn -PU53,161 192.168.1.0/24

# Step 4: Combine techniques
nmap -sn -PS22,80 -PA443 -PU53 192.168.1.0/24

# Step 5: Save results
nmap -sn -PS22,80,443 -oN discovery.txt 192.168.1.0/24
```

### Exercise 3: Firewall Evasion Techniques

```bash
# Task: Practice firewall evasion (on authorized targets only)

# Step 1: Normal scan (baseline)
nmap -sS scanme.nmap.org

# Step 2: Fragmented scan
nmap -f scanme.nmap.org

# Step 3: Slow timing
nmap -T0 scanme.nmap.org

# Step 4: Source port manipulation
nmap --source-port 53 scanme.nmap.org

# Step 5: Combined evasion
nmap -f -T2 --source-port 53 scanme.nmap.org

# Step 6: Decoy scan
nmap -D RND:5 scanme.nmap.org
```

### Exercise 4: Creating Custom NSE Script

```bash
# Task: Create a simple custom NSE script

# Step 1: Create script directory
mkdir -p ~/.nmap/scripts

# Step 2: Create custom script
cat > ~/.nmap/scripts/simple-banner.nse << 'EOF'
description = [[
Simple banner grabbing script
]]

author = "Student"
license = "Same as Nmap"
categories = {"discovery", "safe"}

local comm = require "comm"

portrule = function(host, port)
    return port.state == "open"
end

action = function(host, port)
    local banner = comm.get_banner(host, port)
    if banner then
        return "Banner: " .. banner
    end
    return nil
end
EOF

# Step 3: Update script database
nmap --script-updatedb

# Step 4: Test script
nmap --script simple-banner.nse scanme.nmap.org
```

### Exercise 5: Automation Script

```bash
# Task: Create automation script for comprehensive scanning

# Step 1: Create script
cat > ~/nmap-auto.sh << 'EOF'
#!/bin/bash

TARGET=$1

if [ -z "$TARGET" ]; then
    echo "Usage: ./nmap-auto.sh <target>"
    exit 1
fi

echo "[*] Starting Nmap Automation for $TARGET"
echo "[*] Results will be saved to nmap_results/"

mkdir -p nmap_results

echo "[*] Phase 1: Host Discovery"
nmap -sn $TARGET -oN nmap_results/01_discovery.txt

echo "[*] Phase 2: Quick Port Scan"
nmap -T4 -F $TARGET -oN nmap_results/02_quick.txt

echo "[*] Phase 3: Full Port Scan"
nmap -p- -T4 $TARGET -oN nmap_results/03_fullports.txt

echo "[*] Phase 4: Service Version Scan"
nmap -sV $TARGET -oN nmap_results/04_versions.txt

echo "[*] Phase 5: Default Script Scan"
nmap -sC $TARGET -oN nmap_results/05_scripts.txt

echo "[*] Phase 6: Vulnerability Scan"
nmap --script vuln $TARGET -oN nmap_results/06_vuln.txt

echo "[+] All scans complete! Check nmap_results/ directory"
EOF

# Step 2: Make executable
chmod +x ~/nmap-auto.sh

# Step 3: Run on test target
~/nmap-auto.sh scanme.nmap.org
```

### Exercise 6: Report Generation

```bash
# Task: Generate professional scan report

# Step 1: Run comprehensive scan with all output formats
nmap -sV -sC -oA report_scan scanme.nmap.org

# Step 2: Parse grepable output
cat report_scan.gnmap | grep "open" | awk '{print $2}'

# Step 3: Create summary
cat > report_summary.md << EOF
# Nmap Scan Report

**Target:** scanme.nmap.org
**Date:** $(date)
**Scanner:** $(nmap --version | head -1)

## Open Ports

\`\`\`
$(nmap -F scanme.nmap.org | grep open)
\`\`\`

## Services

\`\`\`
$(nmap -sV scanme.nmap.org | grep -E "^[0-9]+")
\`\`\`

## Scripts Output

\`\`\`
$(nmap -sC scanme.nmap.org)
\`\`\`
EOF

# Step 4: View report
cat report_summary.md
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Scripts Not Running

```bash
# Cause: Script database not updated or script path wrong

# Solution 1: Update script database
nmap --script-updatedb

# Solution 2: Check script location
ls /usr/share/nmap/scripts/
ls ~/.nmap/scripts/

# Solution 3: Specify full path
nmap --script /path/to/script.nse target.com

# Solution 4: Verify script exists
nmap --script-help script-name
```

### Problem 2: Permission Denied Errors

```bash
# Cause: Nmap requires root for certain scans

# Solution 1: Use sudo for SYN scans
sudo nmap -sS target.com

# Solution 2: Use alternatives that don't need root
nmap -sT target.com  # TCP Connect (no root needed)

# Note: In Termux, most scans work without root
```

### Problem 3: Slow Scans

```bash
# Cause: Default timing is conservative

# Solution 1: Use faster timing template
nmap -T4 target.com

# Solution 2: Increase parallelism
nmap --min-rate 100 target.com

# Solution 3: Reduce scope
nmap -F target.com  # Fast scan (fewer ports)

# Solution 4: Combine techniques
nmap -T4 --min-rate 50 -F target.com
```

### Problem 4: Host Appears Down (But Is Up)

```bash
# Cause: Firewall blocking ping probes

# Solution 1: Skip host discovery
nmap -Pn target.com

# Solution 2: Use alternative ping methods
nmap -PS80,443 target.com

# Solution 3: Combine methods
nmap -PS22,80,443 -PA80,443 -PU53 target.com
```

### Problem 5: All Ports Show Filtered

```bash
# Cause: Firewall blocking all traffic

# Solution 1: Use decoy scan
nmap -D RND:10 target.com

# Solution 2: Fragment packets
nmap -f target.com

# Solution 3: Use trusted source port
nmap --source-port 53 target.com

# Solution 4: Slow down scan
nmap -T1 target.com

# Solution 5: Combine evasion techniques
nmap -f -T1 --source-port 53 -D RND:5 target.com
```

### Problem 6: NSE Script Errors

```bash
# Cause: Script syntax error or missing library

# Solution 1: Check script syntax
nmap --script-trace --script script.nse target.com

# Solution 2: Enable debug
nmap -d --script script.nse target.com

# Solution 3: Check Lua syntax
luac -p script.nse  # If luac available

# Solution 4: Read script documentation
nmap --script-help script.nse
```

### Problem 7: Memory Issues on Termux

```bash
# Cause: Large scans can use significant memory

# Solution 1: Reduce parallelism
nmap --max-parallelism 10 target.com

# Solution 2: Scan smaller port ranges
nmap -p 1-1000 target.com

# Solution 3: Scan in batches
nmap -p 1-100 target.com -oN batch1.txt
nmap -p 101-200 target.com -oN batch2.txt

# Solution 4: Use --max-retries
nmap --max-retries 1 target.com
```

### Problem 8: IPv6 Scan Not Working

```bash
# Cause: IPv6 not properly configured or supported

# Solution 1: Check IPv6 connectivity
ping6 -c 3 ipv6.google.com

# Solution 2: Specify IPv6 explicitly
nmap -6 -p 80,443 target.com

# Solution 3: Check if target has IPv6
dig AAAA target.com +short
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Script Power Theme**
```
┌────────────────────────────────────┐
│  [Terminal Background]             │
│                                    │
│   🔥 NMAP ADVANCED                 │
│   NSE SCRIPTS + EVASION            │
│                                    │
│   ✓ 600+ Scripts                   │
│   ✓ Firewall Bypass                │
│   ✓ Custom Scripts                 │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Stealth Theme**
```
┌────────────────────────────────────┐
│  🎭 STEALTH SCANNING               │
│                                    │
│  Nmap Advanced Techniques          │
│                                    │
│  ┌────────────────────────────┐   │
│  │ Target: ???                │   │
│  │ Attacker: HIDDEN           │   │
│  └────────────────────────────┘   │
│                                    │
│  Chapter 26 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Power User Theme**
```
┌────────────────────────────────────┐
│  ⚡ NMAP SUPERPOWERS               │
│                                    │
│  [Code snippets background]        │
│                                    │
│  • NSE Scripts                     │
│  • Idle Scan                       │
│  • Firewall Evasion                │
│                                    │
│  Master Class | T3rmuxk1ng         │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔥 Nmap Advanced Techniques | NSE Scripts & Firewall Evasion | Termux Full Course Ch 26

⚡ In this chapter you'll learn:
• Nmap Scripting Engine (NSE) - Full Guide
• --script usage and categories
• Common NSE scripts (auth, vuln, exploit)
• --script-args customization
• Host discovery techniques (-sn, -PS, -PA, -PU)
• Firewall evasion methods (-f, --mtu, -D, -S)
• Decoy scans and idle scan (-sI)
• FTP bounce and IPv6 scanning
• Zenmap alternatives on Android
• Creating custom NSE scripts
• Nmap automation and reporting

⏱️ Timestamps:
0:00 - Introduction
0:50 - NSE Introduction
3:30 - Script Usage (-sC, --script)
6:00 - Common NSE Scripts
9:30 - Script Arguments
12:00 - Host Discovery
15:00 - Firewall Evasion
18:00 - Idle Scan
20:00 - FTP Bounce & IPv6
23:00 - Zenmap Alternatives
24:30 - Custom NSE Scripts
27:00 - Automation Scripts
29:00 - Reporting
31:00 - Summary

📝 Key Commands:
nmap -sC target.com
nmap --script vuln target.com
nmap -D RND:10 target.com
nmap -sI zombie target.com

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]

#Nmap #NSE #NmapAdvanced #Termux #TermuxCourse #T3rmuxk1ng #EthicalHacking #NetworkScanning #FirewallEvasion

---
⚠️ Disclaimer: This video is for educational purposes. Only scan systems you have authorization to test. Unauthorized scanning is illegal.
```

### Tags List

```
nmap, nmap advanced, nmap nse, nmap scripts, nmap scripting engine,
nmap firewall evasion, nmap tutorial, nmap course, nmap termux,
termux nmap, network scanning, port scanning, security tools,
ethical hacking, penetration testing, nmap idle scan, nmap decoy,
nse scripts, nmap automation, nmap custom scripts, nmap reporting,
t3rmuxk1ng, termux course, termux hindi, cybersecurity tools,
vulnerability scanning, network security, hacking tools
```

### Hashtags

```
#Nmap #NmapAdvanced #NSE #NetworkScanning #EthicalHacking 
#Termux #TermuxCourse #CyberSecurity #PenetrationTesting 
#T3rmuxk1ng #FirewallEvasion #SecurityTools #NmapScripts 
#HindiTutorial #LearnHacking
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Nmap Official Site | https://nmap.org/ |
| Nmap Documentation | https://nmap.org/docs.html |
| NSE Documentation | https://nmap.org/book/nse.html |
| Nmap Scripts API | https://nmap.org/nsedoc/ |

### Script Repositories

| Repository | Description |
|------------|-------------|
| Default Scripts | /usr/share/nmap/scripts/ |
| Nmap NSE Vault | https://github.com/scipag/nmap-nse-scripts |
| Vulners NSE | https://github.com/vulnersCom/nmap-vulners |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Nmap Network Scanning Book | Official book by Gordon Lyon |
| Nmap Cheat Sheet | Quick reference guide |
| TryHackMe Nmap Room | Interactive practice |
| HackTheBox | Real-world practice targets |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 27, verify:

- [ ] Understand NSE architecture and categories
- [ ] Successfully ran -sC default scripts
- [ ] Used --script with specific scripts
- [ ] Applied --script-args for customization
- [ ] Practiced host discovery techniques
- [ ] Tested firewall evasion methods
- [ ] Understand idle scan mechanism
- [ ] Can create basic automation script
- [ ] Know output format options
- [ ] Understand legal/ethical boundaries

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 27: Netcat Mastery**

- Netcat introduction and installation
- Port scanning with Netcat
- Banner grabbing techniques
- File transfer methods
- Reverse and bind shells
- Chat server setup
- Port forwarding and relays
- Netcat vs Ncat vs NCat
- Advanced Netcat techniques

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
