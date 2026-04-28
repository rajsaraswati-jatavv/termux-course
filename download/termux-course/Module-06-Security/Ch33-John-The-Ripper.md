# Chapter 33: John the Ripper - Hash Cracking

> **Module:** 6 - Security Tools  
> **Chapter:** 33 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed John the Ripper usage |
| Hash Types | MD5, SHA1, SHA256, bcrypt and more |
| Hash Extraction | zip2john, rar2john, pdf2john, ssh2john |
| Commands Reference | 25+ commands and examples |
| Practice Exercises | Hands-on cracking tasks |
| Troubleshooting | Common John issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 33
Title: John the Ripper - Password Hash Cracking | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut interesting hai - John the Ripper! Ye world ka 
sabse popular password cracking tool hai. Agar aap ethical hacking 
seekh rahe ho, to John the Ripper aana zaruri hai.

Previous chapters mein humne Hydra seekha tha - wo online password 
cracking ke liye hai. John the Ripper offline password cracking ke 
liye hai - matlab hash files crack karna.

Is chapter mein hum cover karenge:
✓ Hash kya hota hai
✓ Different hash types kaise identify karein
✓ John install aur use karna
✓ Wordlist attacks
✓ Incremental attacks
✓ Hash extraction tools - zip2john, pdf2john, ssh2john
✓ Custom rules banana
✓ Session management
✓ Performance tuning

To chaliye shuru karte hain!

---

[SECTION 1: HASH CRACKING CONCEPTS - 1:00 to 4:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samajhte hain - Hash kya hai aur cracking kaise kaam karti hai?

Hash ek fixed-size string hai jo kisi bhi data se generate hoti hai.
Jab aap password create karte ho, system us password ko hash mein 
convert karke store karta hai - plain text password store nahi karta.

Example samjhein:

    Password: "password123"
    MD5 Hash: "482c811da5d5b4bc6d497ffa98491e38"

Ye hash one-way function hai - aap hash se original password 
wapas nahi nikal sakte directly. Lekin John the Ripper try karta 
hai different passwords, unka hash generate karta hai, aur compare 
karta hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                     PASSWORD HASH CRACKING FLOW                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Target Hash: 482c811da5d5b4bc6d497ffa98491e38                         │
│                                                                          │
│   John tries:                    Hash:           Match?                 │
│   ─────────────────────────────────────────────────────                 │
│   "password"         →    5f4dcc3b...        ❌ No                      │
│   "password1"        →    e38ad21...         ❌ No                      │
│   "password123"      →    482c811d...        ✅ YES!                    │
│                                                                          │
│   Cracked Password: password123                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Hash types bahut hote hain - weak se strong tak:

┌─────────────────────────────────────────────────────────────────────────┐
│                     HASH TYPES - STRENGTH COMPARISON                     │
├───────────────────┬────────────────┬──────────┬────────────────────────┤
│ Hash Type         │ Length         │ Speed    │ Security Status        │
├───────────────────┼────────────────┼──────────┼────────────────────────┤
│ MD5               │ 32 chars       │ Fast     │ ❌ Broken/Weak         │
│ SHA1              │ 40 chars       │ Fast     │ ❌ Weak                │
│ SHA256            │ 64 chars       │ Medium   │ ✅ Good                │
│ SHA512            │ 128 chars      │ Medium   │ ✅ Strong              │
│ bcrypt            │ 60 chars       │ Slow     │ ✅ Very Strong         │
│ Argon2            │ Variable       │ Slow     │ ✅ Best                │
│ NTLM (Windows)    │ 32 chars       │ Fast     │ ❌ Weak                │
│ SHA-256(crypt)    │ Variable       │ Slow     │ ✅ Good                │
└───────────────────┴────────────────┴──────────┴────────────────────────┘

Weak hashes jaise MD5 aur SHA1 fast hain - quickly crack ho jate hain.
Strong hashes jaise bcrypt aur Argon2 slow hain - years lag sakte hain.

Ye concepts samajhna important hai kyunki security testing mein 
aapko ye identify karna hoga ki target kis hash type use kar raha hai.

---

[SECTION 2: JOHN INSTALLATION - 4:30 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab install karte hain John the Ripper ko Termux mein:

    pkg update && pkg upgrade -y
    pkg install john -y

Installation ke baad verify karein:

    john --help

Ye command John ke saare options dikhayegi.

John ke version check karein:

    john --list=build-info

Important: Termux mein John the Ripper "jumbo" version aata hai jo 
bahut saare hash types support karta hai - over 400 types!

Supported formats dekhne ke liye:

    john --list=formats

Ye command bahut lambi list degi. Specific format search karne ke liye:

    john --list=formats | grep -i "md5"
    john --list=formats | grep -i "sha"
    john --list=formats | grep -i "bcrypt"

---

[SECTION 3: HASH IDENTIFICATION - 7:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Pehle step humesha hash identify karna hai. John automatically detect 
kar sakta hai, lekin kabhi kabhi manual identification zaruri hoti hai.

Hash length se identify karna sabse easy hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                     HASH IDENTIFICATION BY LENGTH                        │
├───────────────────────┬──────────────┬──────────────────────────────────┤
│ Hash Length           │ Possible Type│ Example                          │
├───────────────────────┼──────────────┼──────────────────────────────────┤
│ 32 characters         │ MD5, NTLM    │ 5d41402abc4b2a76b9719d911017c592│
│ 40 characters         │ SHA1         │ aaf4c61ddcc5e8a2dabede0f3b482cd9│
│ 64 characters         │ SHA256       │ 2c26b46b68ffc68ff99b453c1d304134│
│ 128 characters        │ SHA512       │ 9b71d224bd62f3785d96d46ad3ea3d73│
│ 60 chars (starts $2)  │ bcrypt       │ $2a$10$N9qo8uLOickgx2ZMRZoMy.Mrq│
│ Variable ($6$)        │ SHA-512crypt │ $6$rounds=5000$salt$hash...     │
│ Variable ($5$)        │ SHA-256crypt │ $5$rounds=5000$salt$hash...     │
└───────────────────────┴──────────────┴──────────────────────────────────┘

Hash examples:

    # MD5
    5d41402abc4b2a76b9719d911017c592
    
    # SHA1
    aaf4c61ddcc5e8a2dabede0f3b482cd9aea9434d
    
    # SHA256
    2c26b46b68ffc68ff99b453c1d30413413422d706483bfa0f98a5e886266e7ae
    
    # bcrypt
    $2a$10$N9qo8uLOickgx2ZMRZoMy.MrqjdD4XYhKJUJOjJGHPzWA.uq9BKR.
    
    # SHA-512crypt (Linux /etc/shadow)
    $6$rounds=5000$saltsalt$HK.
    
    # NTLM (Windows)
    8846F7EAEE8FB117AD06BDD830B7586C

John mein automatic detection ke liye:

    john --show=types hash.txt

Iske liye hash file banana padega pehle.

---

[SECTION 4: BASIC JOHN USAGE - 10:00 to 13:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab practical start karte hain. Ek simple MD5 hash crack karte hain.

Pehle ek hash file banate hain:

    echo "5d41402abc4b2a76b9719d911017c592" > hash.txt

Ye "hello" ka MD5 hash hai.

Basic John command:

    john hash.txt

John automatically:
1. Hash type detect karega
2. Default wordlist use karega
3. Single crack mode try karega
4. Result dikhayega

Output mein aap dekhoge:

    Loaded 1 password hash (Raw-MD5 [MD5 128/128 AVX 4x3])
    Press 'q' or Ctrl-C to abort, almost any other key for status
    hello             (?)     
    1g 0:00:00:00 DONE 2/3 (2024-01-01 12:00) 1.000g/s

"hello" password crack ho gaya!

Cracked password dekhne ke liye:

    john --show hash.txt

Ye command already cracked passwords dikhayegi.

Agar specific format batana ho:

    john --format=raw-md5 hash.txt

---

[SECTION 5: WORDLIST ATTACKS - 13:30 to 16:30]
─────────────────────────────────────────────────────────────────────────────

Default wordlist small hoti hai. Real-world cracking ke liye badi 
wordlist chahiye. Popular wordlists:

1. rockyou.txt - 14 million passwords (most popular)
2. SecLists - Multiple wordlists for different purposes
3. CrackStation - 1.5 billion passwords

Termux mein wordlist download karte hain:

    # Create wordlists directory
    mkdir -p ~/wordlists
    cd ~/wordlists
    
    # Download rockyou.txt
    wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
    tar -xzf rockyou.txt.tar.gz
    
    # Or use pkg
    pkg install seclists -y
    # Wordlists will be in $PREFIX/share/seclists/

Wordlist attack syntax:

    john --wordlist=/path/to/wordlist.txt hash.txt

Example with rockyou:

    john --wordlist=~/wordlists/rockyou.txt hash.txt

Progress check:

    # While running, press any key to see status
    # Or use:
    john --show hash.txt

Statistics dekhne ke liye:

    john --wordlist=rockyou.txt --show=types hash.txt

Agar wordlist mein password nahi mila, to incremental mode use karein.

---

[SECTION 6: INCREMENTAL MODE - 16:30 to 18:30]
─────────────────────────────────────────────────────────────────────────────

Incremental mode brute-force attack hai. Ye saare possible combinations 
try karta hai - a to z, 0 to 9, special characters.

Warning: Incremental mode bahut slow hai for strong passwords!

Basic incremental:

    john --incremental hash.txt

Specific character set ke saath:

    # Only lowercase letters
    john --incremental=Lower hash.txt
    
    # Only digits
    john --incremental=Digits hash.txt
    
    # Alphanumeric
    john --incremental=Alnum hash.txt
    
    # All characters
    john --incremental=All hash.txt

Length limit set karein:

    # Minimum 1, Maximum 6 characters
    john --incremental --min-length=1 --max-length=6 hash.txt

Custom charset:

    john --incremental --external:lanman hash.txt

Real-world tip: Incremental mode chhote passwords (1-6 chars) ke liye 
accha hai. Bade passwords ke liye wordlist + rules use karein.

---

[SECTION 7: HASH EXTRACTION TOOLS - 18:30 to 21:30]
─────────────────────────────────────────────────────────────────────────────

John directly files se hash extract nahi karta. Iske liye separate 
tools hain jo John ke saath aate hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                     HASH EXTRACTION TOOLS                                │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Tool                 │ Purpose                                         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ zip2john             │ Extract hash from ZIP archives                  │
│ rar2john             │ Extract hash from RAR archives                  │
│ pdf2john             │ Extract hash from PDF files                     │
│ office2john          │ Extract hash from Office documents              │
│ ssh2john             │ Extract SSH private key hash                    │
│ keepass2john         │ Extract KeePass database hash                   │
│ 7z2john              │ Extract hash from 7z archives                   │
│ vncpasswd.py         │ Extract VNC password hash                       │
│ unshadow             │ Combine passwd & shadow files                   │
└──────────────────────┴──────────────────────────────────────────────────┘

Chaliye ek-ek example dekhte hain:

[ZIP FILE CRACKING]

    # Extract hash from ZIP
    zip2john protected.zip > zip_hash.txt
    
    # View the hash
    cat zip_hash.txt
    
    # Crack with John
    john --wordlist=rockyou.txt zip_hash.txt
    
    # View cracked password
    john --show zip_hash.txt

[PDF FILE CRACKING]

    # Extract hash from PDF
    pdf2john protected.pdf > pdf_hash.txt
    
    # Crack
    john --wordlist=rockyou.txt pdf_hash.txt

[OFFICE DOCUMENTS]

    # Word, Excel, PowerPoint
    office2john document.docx > office_hash.txt
    office2john spreadsheet.xlsx > office_hash.txt
    
    # Crack
    john --wordlist=rockyou.txt office_hash.txt

[SSH PRIVATE KEY]

    # Extract hash from SSH key
    ssh2john id_rsa > ssh_hash.txt
    
    # Crack the passphrase
    john --wordlist=rockyou.txt ssh_hash.txt

[RAR ARCHIVES]

    rar2john archive.rar > rar_hash.txt
    john --wordlist=rockyou.txt rar_hash.txt

[7z ARCHIVES]

    7z2john archive.7z > 7z_hash.txt
    john --wordlist=rockyou.txt 7z_hash.txt

---

[SECTION 8: UNSHADOW COMMAND - 21:30 to 23:30]
─────────────────────────────────────────────────────────────────────────────

Linux systems mein password hashes /etc/shadow file mein hoti hain.
Lekin shadow file alone kaam nahi karti - /etc/passwd bhi chahiye.

unshadow command dono files combine karti hai:

    # On target Linux system (requires root)
    unshadow /etc/passwd /etc/shadow > my_hashes.txt
    
    # Now crack with John
    john --wordlist=rockyou.txt my_hashes.txt

Termux mein test ke liye:

    # Create test passwd file
    cat > passwd_test << 'EOF'
    root:x:0:0:root:/root:/bin/bash
    user:x:1000:1000:User:/home/user:/bin/bash
    EOF
    
    # Create test shadow file (with hash)
    cat > shadow_test << 'EOF'
    root:$6$xyz123$hashedpassword:18000:0:99999:7:::
    user:$6$abc456$hashedpassword:18000:0:99999:7:::
    EOF
    
    # Combine
    unshadow passwd_test shadow_test > combined_hashes.txt
    
    # Crack
    john --wordlist=rockyou.txt combined_hashes.txt

Specific user crack karna:

    john --users=root --wordlist=rockyou.txt combined_hashes.txt

---

[SECTION 9: CUSTOM RULES - 23:30 to 25:30]
─────────────────────────────────────────────────────────────────────────────

John mein custom rules bana sakte ho password variations ke liye.

Default rules bahut powerful hain:

    # Use all default rules
    john --rules hash.txt
    
    # Use specific rule
    john --rules=Single hash.txt
    john --rules=Wordlist hash.txt
    john --rules=Extra hash.txt
    john --rules=Jumbo hash.txt

Custom rule example:

    # Create john.conf file
    cat > ~/john.conf << 'EOF'
    [List.Rules:MyRule]
    # Add numbers at end
    $[0-9]
    # Add numbers at start
    ^[0-9]
    # Capitalize first letter
    c
    # Leet speak
    sa@ se3 si1 so0 ss$
    EOF

Custom rule use karna:

    john --wordlist=rockyou.txt --rules=MyRule --config=~/john.conf hash.txt

Built-in powerful rules:

    john --wordlist=rockyou.txt --rules=best64 hash.txt
    john --wordlist=rockyou.txt --rules=OneRuleToRuleThemAll hash.txt

---

[SECTION 10: SESSION MANAGEMENT - 25:30 to 27:30]
─────────────────────────────────────────────────────────────────────────────

Long cracking sessions mein agar Termux band ho jaye ya crash ho jaye,
to sab kaam barbaad ho jayega. Isliye session management important hai.

John automatically session save karta hai. Default location:

    ~/.john/john.pot  # Cracked passwords
    ~/.john/sessions/ # Running sessions

Session name se save karna:

    john --session=my_crack --wordlist=rockyou.txt hash.txt

Session restore karna:

    john --restore=my_crack

Default session restore:

    john --restore

Session files check karna:

    ls ~/.john/sessions/

Cracked passwords file:

    cat ~/.john/john.pot

Pot file clear karna (fresh start):

    rm ~/.john/john.pot

---

[SECTION 11: PERFORMANCE TUNING - 27:30 to 29:30]
─────────────────────────────────────────────────────────────────────────────

John performance optimize karne ke liye several options hain:

[PARALLEL PROCESSING]

    # Use all CPU cores
    john --fork=4 hash.txt
    
    # Or automatically detect
    john --fork=$(nproc) hash.txt

[OPENCL/GPU (if available)]

    # List OpenCL devices
    john --list=opencl-devices
    
    # Use OpenCL
    john --opencl hash.txt
    
    # Specific platform
    john --opencl --platform=0 --device=0 hash.txt

[PERFORMANCE TEST]

    # Benchmark all formats
    john --test
    
    # Benchmark specific format
    john --test --format=raw-md5
    john --test --format=bcrypt

[OPTIMIZATION FLAGS]

    # Verbose output
    john --verbosity=5 hash.txt
    
    # Skip certain formats
    john --skip-types=md5,sha1 hash.txt

Android pe GPU acceleration limited hai, lekin multi-core CPU use kar 
sakte hain with --fork option.

---

[SECTION 12: SUMMARY & NEXT PREVIEW - 29:30 to 31:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 33 complete! Let's summarize:

✅ Hash kya hai aur cracking kaise kaam karti hai
✅ John the Ripper installation in Termux
✅ Hash types aur identification
✅ Basic John usage
✅ Wordlist attacks with rockyou.txt
✅ Incremental brute-force mode
✅ Hash extraction tools - zip2john, pdf2john, ssh2john, etc.
✅ unshadow command for Linux passwords
✅ Custom rules banana
✅ Session management
✅ Performance tuning

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 33 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install john                    │ Install John the Ripper          │
│ john hash.txt                       │ Basic crack attempt              │
│ john --wordlist=rockyou.txt hash    │ Wordlist attack                  │
│ john --incremental hash.txt         │ Brute-force attack               │
│ john --show hash.txt                │ Show cracked passwords           │
│ zip2john file.zip > hash.txt        │ Extract ZIP hash                 │
│ pdf2john file.pdf > hash.txt        │ Extract PDF hash                 │
│ ssh2john id_rsa > hash.txt          │ Extract SSH key hash             │
│ unshadow passwd shadow > hashes.txt │ Combine Linux files              │
│ john --restore=session_name         │ Resume cracking session          │
│ john --fork=4 hash.txt              │ Multi-core processing            │
│ john --test                         │ Performance benchmark            │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 34 mein hum SQLMap seekhenge - SQL injection 
automation tool. Database hacking ka king!

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 34!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. John the Ripper Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     JOHN THE RIPPER ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      INPUT LAYER                                 │   │
│   │   Hash File / Extracted Hash / Shadow File                      │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    CRACKING MODES                                │   │
│   │                                                                   │   │
│   │   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐        │   │
│   │   │  Single  │  │ Wordlist │  │Incremental│  │  Rules   │        │   │
│   │   │   Mode   │  │   Mode   │  │   Mode    │  │   Mode   │        │   │
│   │   └──────────┘  └──────────┘  └──────────┘  └──────────┘        │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    HASH FORMATS                                  │   │
│   │   MD5, SHA1, SHA256, SHA512, bcrypt, NTLM, DES, etc.           │   │
│   │   Over 400 supported formats in Jumbo version                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    OUTPUT LAYER                                  │   │
│   │   Cracked passwords stored in john.pot file                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Hash Types Deep Dive

| Hash Type | Algorithm | Length | Prefix | Use Case | Crack Speed |
|-----------|-----------|--------|--------|----------|-------------|
| MD5 | Message Digest 5 | 32 hex | None | Legacy systems | Very Fast |
| SHA1 | Secure Hash 1 | 40 hex | None | Git, legacy | Fast |
| SHA256 | SHA-2 256-bit | 64 hex | None | Certificates | Medium |
| SHA512 | SHA-2 512-bit | 128 hex | None | Modern systems | Medium |
| bcrypt | Blowfish-based | 60 chars | $2a$, $2b$ | Passwords | Slow |
| Argon2 | Memory-hard | Variable | $argon2 | Modern passwords | Very Slow |
| NTLM | MD4-based | 32 hex | None | Windows | Very Fast |
| SHA-256crypt | SHA-256-based | Variable | $5$ | Linux /etc/shadow | Slow |
| SHA-512crypt | SHA-512-based | Variable | $6$ | Linux /etc/shadow | Slow |
| MD5crypt | MD5-based | Variable | $1$ | Legacy Unix | Fast |
| DES | Data Encryption | 13 chars | None | Legacy Unix | Fast |
| LM Hash | DES variant | 32 hex | None | Old Windows | Very Fast |

### 3. John Installation

```bash
# Update Termux
pkg update && pkg upgrade -y

# Install John the Ripper (Jumbo version)
pkg install john -y

# Verify installation
john --help

# Check version and build info
john --list=build-info

# List all supported formats
john --list=formats | wc -l  # Count formats

# Search for specific format
john --list=formats | grep -i "sha256"
john --list=formats | grep -i "bcrypt"
```

### 4. Hash Identification

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     HASH IDENTIFICATION PATTERNS                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   MD5 (32 chars, hex only):                                             │
│   5d41402abc4b2a76b9719d911017c592                                      │
│                                                                          │
│   SHA1 (40 chars, hex only):                                            │
│   aaf4c61ddcc5e8a2dabede0f3b482cd9aea9434d                              │
│                                                                          │
│   SHA256 (64 chars, hex only):                                          │
│   2c26b46b68ffc68ff99b453c1d30413413422d706483bfa0f98a5e886266e7ae     │
│                                                                          │
│   SHA512 (128 chars, hex only):                                         │
│   9b71d224bd62f3785d96d46ad3ea3d73319bfbc2890caadae2dff72519673ca7     │
│   232373b9b0367b2a000fcbf41e9d929e...                                   │
│                                                                          │
│   bcrypt ($2a$, $2b$, $2y$ prefix):                                     │
│   $2a$10$N9qo8uLOickgx2ZMRZoMy.MrqjdD4XYhKJUJOjJGHPzWA.uq9BKR.         │
│                                                                          │
│   SHA-256crypt ($5$ prefix):                                            │
│   $5$rounds=5000$saltsalt$HK.pA6W9F9B5YxYxYxYxYxYxYxYxYxYxYx            │
│                                                                          │
│   SHA-512crypt ($6$ prefix):                                            │
│   $6$rounds=5000$saltsalt$HK.pA6W9F9B5YxYxYxYxYxYxYxYxYxYxYx            │
│                                                                          │
│   NTLM (32 chars, uppercase common):                                    │
│   8846F7EAEE8FB117AD06BDD830B7586C                                      │
│                                                                          │
│   MD5crypt ($1$ prefix):                                                │
│   $1$salt$hashedpassword                                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5. Hash Extraction Tools Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     HASH EXTRACTION TOOLS DETAIL                         │
├──────────────────────┬──────────────────────────────────────────────────┤
│ zip2john             │ Extracts password hash from ZIP archives         │
│                      │ Supports: ZipCrypto, AES-256, WinZip AES        │
│                      │ Usage: zip2john file.zip > hash.txt             │
├──────────────────────┼──────────────────────────────────────────────────┤
│ rar2john             │ Extracts password hash from RAR archives         │
│                      │ Supports: RAR3, RAR5                            │
│                      │ Usage: rar2john file.rar > hash.txt             │
├──────────────────────┼──────────────────────────────────────────────────┤
│ pdf2john             │ Extracts password hash from PDF files            │
│                      │ Supports: PDF 1.1-1.7, AES, RC4                 │
│                      │ Usage: pdf2john file.pdf > hash.txt             │
├──────────────────────┼──────────────────────────────────────────────────┤
│ office2john          │ Extracts hash from MS Office documents           │
│                      │ Supports: DOC, XLS, PPT, DOCX, XLSX, PPTX       │
│                      │ Usage: office2john file.docx > hash.txt         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ ssh2john             │ Extracts passphrase hash from SSH keys           │
│                      │ Supports: RSA, DSA, ECDSA, Ed25519              │
│                      │ Usage: ssh2john id_rsa > hash.txt               │
├──────────────────────┼──────────────────────────────────────────────────┤
│ keepass2john         │ Extracts hash from KeePass databases             │
│                      │ Supports: KDBX 3.x, 4.x                         │
│                      │ Usage: keepass2john file.kdbx > hash.txt        │
├──────────────────────┼──────────────────────────────────────────────────┤
│ 7z2john              │ Extracts hash from 7z archives                   │
│                      │ Supports: LZMA, LZMA2, PPMd, BZip2              │
│                      │ Usage: 7z2john file.7z > hash.txt               │
├──────────────────────┼──────────────────────────────────────────────────┤
│ unshadow             │ Combines passwd and shadow files                 │
│                      │ Requires: Root access on target system          │
│                      │ Usage: unshadow passwd shadow > hash.txt        │
├──────────────────────┼──────────────────────────────────────────────────┤
│ vncpasswd            │ Extracts VNC password hash                       │
│                      │ Supports: VNC 3.3, 4.x                          │
│                      │ Usage: vncpasswd.py file > hash.txt             │
└──────────────────────┴──────────────────────────────────────────────────┘
```

### 6. Cracking Modes Explained

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     JOHN CRACKING MODES                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   1. SINGLE CRACK MODE (Default First)                                  │
│      - Uses username and GECOS info                                     │
│      - Fastest for simple passwords                                     │
│      - Syntax: john --single hash.txt                                   │
│                                                                          │
│   2. WORDLIST MODE (Most Common)                                        │
│      - Uses dictionary of common passwords                              │
│      - rockyou.txt most popular (14M passwords)                         │
│      - Syntax: john --wordlist=list.txt hash.txt                        │
│                                                                          │
│   3. INCREMENTAL MODE (Brute Force)                                     │
│      - Tries all possible combinations                                  │
│      - Slowest but most thorough                                        │
│      - Syntax: john --incremental hash.txt                              │
│                                                                          │
│   4. RULES MODE (Wordlist + Variations)                                 │
│      - Applies transformations to wordlist                              │
│      - Password1, password!, P@ssword, etc.                            │
│      - Syntax: john --wordlist=list.txt --rules hash.txt                │
│                                                                          │
│   5. EXTERNAL MODE (Custom Scripts)                                     │
│      - User-defined cracking logic                                      │
│      - Syntax: john --external=mode_name hash.txt                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 7. Custom Rules Configuration

```bash
# John configuration file location
# Usually: ~/.john/john.conf or $PREFIX/etc/john/john.conf

# Example custom rules
cat > ~/.john/custom.conf << 'EOF'
[List.Rules:CustomRules]
# Rule 1: Append numbers 0-9
$[0-9]

# Rule 2: Prepend numbers 0-9
^[0-9]

# Rule 3: Capitalize first letter
c

# Rule 4: Append special characters
$[!@#$%^&*()]

# Rule 5: Leet speak transformations
sa@ se3 si1 so0 ss$ 

# Rule 6: Double the word
d

# Rule 7: Reverse the word
r

# Rule 8: Append year (2000-2024)
$[0-9]$[0-9]$[0-9]$[0-9]

# Combine multiple rules
c $[0-9]
r $[0-9]
EOF

# Use custom rules
john --wordlist=rockyou.txt --rules=CustomRules \
     --config=~/.john/custom.conf hash.txt
```

### 8. Session Management

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     SESSION MANAGEMENT WORKFLOW                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌────────────────┐                                                    │
│   │ Start Session  │ john --session=name hash.txt                      │
│   └───────┬────────┘                                                    │
│           │                                                              │
│           ▼                                                              │
│   ┌────────────────┐                                                    │
│   │ Running State  │ Progress saved automatically                       │
│   └───────┬────────┘                                                    │
│           │                                                              │
│           │ (Interrupt: Ctrl+C, crash, close Termux)                    │
│           ▼                                                              │
│   ┌────────────────┐                                                    │
│   │ Paused State   │ Session saved in ~/.john/sessions/                 │
│   └───────┬────────┘                                                    │
│           │                                                              │
│           ▼                                                              │
│   ┌────────────────┐                                                    │
│   │ Resume Session │ john --restore=name                                │
│   └───────┬────────┘                                                    │
│           │                                                              │
│           ▼                                                              │
│   ┌────────────────┐                                                    │
│   │ Continue from  │ Last tried position                                │
│   │ last position  │                                                    │
│   └────────────────┘                                                    │
│                                                                          │
│   Important Files:                                                       │
│   ~/.john/john.pot      - Cracked passwords database                    │
│   ~/.john/sessions/     - Active session files                          │
│   ~/.john/log           - Activity log                                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### Installation & Setup Commands

```bash
# Install John the Ripper
pkg install john -y

# Check version
john --version

# Show build information
john --list=build-info

# List all supported formats
john --list=formats

# Count supported formats
john --list=formats | wc -l

# Search for specific format
john --list=formats | grep -i "md5"
john --list=formats | grep -i "sha256"
john --list=formats | grep -i "bcrypt"

# List OpenCL devices (for GPU acceleration)
john --list=opencl-devices

# Run benchmark
john --test
john --test --format=raw-md5
```

### Basic Cracking Commands

```bash
# Basic auto-detect and crack
john hash.txt

# Specify format
john --format=raw-md5 hash.txt
john --format=raw-sha1 hash.txt
john --format=raw-sha256 hash.txt
john --format=bcrypt hash.txt

# Show cracked passwords
john --show hash.txt

# Show cracked passwords with format
john --show --format=raw-md5 hash.txt

# Verbose output
john --verbosity=5 hash.txt
```

### Wordlist Attack Commands

```bash
# Basic wordlist attack
john --wordlist=wordlist.txt hash.txt

# Wordlist with rockyou
john --wordlist=~/wordlists/rockyou.txt hash.txt

# Wordlist with rules
john --wordlist=rockyou.txt --rules hash.txt

# Specific rule set
john --wordlist=rockyou.txt --rules=Single hash.txt
john --wordlist=rockyou.txt --rules=Wordlist hash.txt
john --wordlist=rockyou.txt --rules=Extra hash.txt
john --wordlist=rockyou.txt --rules=best64 hash.txt

# Multiple wordlists
cat wordlist1.txt wordlist2.txt > combined.txt
john --wordlist=combined.txt hash.txt
```

### Incremental Mode Commands

```bash
# Basic incremental (brute-force)
john --incremental hash.txt

# Specific charset
john --incremental=Lower hash.txt      # a-z only
john --incremental=Upper hash.txt      # A-Z only
john --incremental=Digits hash.txt     # 0-9 only
john --incremental=Alnum hash.txt      # a-z, A-Z, 0-9
john --incremental=All hash.txt        # All characters

# Length limits
john --incremental --min-length=4 --max-length=8 hash.txt

# Incremental with format
john --incremental --format=raw-md5 hash.txt
```

### Hash Extraction Commands

```bash
# ZIP file
zip2john protected.zip > zip_hash.txt
john --wordlist=rockyou.txt zip_hash.txt

# RAR file
rar2john archive.rar > rar_hash.txt
john --wordlist=rockyou.txt rar_hash.txt

# PDF file
pdf2john document.pdf > pdf_hash.txt
john --wordlist=rockyou.txt pdf_hash.txt

# Office documents (Word, Excel, PowerPoint)
office2john document.docx > office_hash.txt
office2john spreadsheet.xlsx > office_hash.txt
office2john presentation.pptx > office_hash.txt
john --wordlist=rockyou.txt office_hash.txt

# SSH private key
ssh2john id_rsa > ssh_hash.txt
john --wordlist=rockyou.txt ssh_hash.txt

# KeePass database
keepass2john database.kdbx > keepass_hash.txt
john --wordlist=rockyou.txt keepass_hash.txt

# 7z archive
7z2john archive.7z > 7z_hash.txt
john --wordlist=rockyou.txt 7z_hash.txt

# Unshadow (Linux passwords)
unshadow /etc/passwd /etc/shadow > linux_hashes.txt
john --wordlist=rockyou.txt linux_hashes.txt
```

### Session Management Commands

```bash
# Start named session
john --session=my_crack --wordlist=rockyou.txt hash.txt

# Restore session
john --restore=my_crack

# Restore default session
john --restore

# List session files
ls ~/.john/sessions/

# View pot file (cracked passwords)
cat ~/.john/john.pot

# Clear pot file
rm ~/.john/john.pot

# View log
cat ~/.john/log
```

### Performance Tuning Commands

```bash
# Multi-core processing
john --fork=4 hash.txt
john --fork=$(nproc) hash.txt

# Fork with wordlist
john --fork=4 --wordlist=rockyou.txt hash.txt

# OpenCL (GPU) acceleration
john --opencl hash.txt
john --opencl --platform=0 --device=0 hash.txt

# Benchmark specific format
john --test --format=raw-md5
john --test --format=bcrypt
john --test --format=sha256crypt

# Show performance stats while running
# Press any key during cracking to see stats
```

### Advanced Commands

```bash
# Filter by users
john --users=root hash.txt
john --users=root,admin hash.txt

# Filter by groups
john --groups=wheel hash.txt

# Filter by shells
john --shells=/bin/bash hash.txt

# Skip certain formats
john --skip-types=md5 hash.txt

# External mode (custom)
john --external=lanman hash.txt

# Show estimated time
john --wordlist=rockyou.txt --show=types hash.txt

# Decode hash types
john --show=types hash.txt
```

### Wordlist Management Commands

```bash
# Create wordlists directory
mkdir -p ~/wordlists

# Download rockyou.txt
cd ~/wordlists
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
tar -xzf rockyou.txt.tar.gz

# Install SecLists package
pkg install seclists -y

# SecLists location
ls $PREFIX/share/seclists/Passwords/

# Create custom wordlist
echo -e "password\n123456\nqwerty\nadmin" > custom.txt

# Merge wordlists
cat wordlist1.txt wordlist2.txt > merged.txt

# Remove duplicates
sort merged.txt | uniq > clean_wordlist.txt

# Count passwords in wordlist
wc -l rockyou.txt
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic MD5 Cracking

```bash
# Task: Crack MD5 hashes using John

# Step 1: Create test hash file
# "hello" = 5d41402abc4b2a76b9719d911017c592
echo "5d41402abc4b2a76b9719d911017c592" > md5_hash.txt

# Step 2: Basic crack
john md5_hash.txt

# Step 3: View result
john --show md5_hash.txt

# Step 4: Try another hash
# "password" = 5f4dcc3b5aa765d61d8327deb882cf99
echo "5f4dcc3b5aa765d61d8327deb882cf99" > md5_hash2.txt
john --format=raw-md5 md5_hash2.txt
john --show md5_hash2.txt

# Expected: Both passwords should crack quickly
```

### Exercise 2: Wordlist Attack

```bash
# Task: Use wordlist to crack a hash

# Step 1: Download wordlist (if not done)
mkdir -p ~/wordlists
cd ~/wordlists
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Common-Credentials/10-million-password-list-top-1000.txt
mv 10-million-password-list-top-1000.txt top1000.txt

# Step 2: Create hash file
# "qwerty123" SHA256
echo "d8578edf8458ce06fbc5bb76a58c5ca4a2e1f8b3e7e4b7e8c9d0a1b2c3d4e5f6" > sha256_hash.txt

# Actually let's use a simpler example
# "sunshine" MD5 = 8d0d9e7e0b3e3e3e3e3e3e3e3e3e3e3e
# Let's use "letmein" MD5
echo "1c63129ae9db9c60c3e8aa94d3e00495" > wordlist_hash.txt

# Step 3: Wordlist attack
john --wordlist=~/wordlists/top1000.txt wordlist_hash.txt

# Step 4: Check result
john --show wordlist_hash.txt
```

### Exercise 3: ZIP File Cracking

```bash
# Task: Crack a password-protected ZIP file

# Step 1: Create a test ZIP with password
# First, create a test file
echo "This is secret data" > secret.txt

# Create password-protected ZIP (password: test123)
# Note: Termux zip might not support encryption directly
# We'll simulate with a pre-made hash

# Step 2: Extract hash from ZIP
# If you have a protected ZIP:
# zip2john protected.zip > zip_hash.txt

# Step 3: Create simulated ZIP hash
cat > zip_hash.txt << 'EOF'
protected.zip:$pkzip$1*1*2*0*23*11*test123*0*28*0*23*ab12*...
EOF

# Step 4: Crack the hash
john --wordlist=~/wordlists/top1000.txt zip_hash.txt

# Step 5: Show result
john --show zip_hash.txt
```

### Exercise 4: SSH Key Passphrase Cracking

```bash
# Task: Crack SSH private key passphrase

# Step 1: Create a password-protected SSH key (for practice)
# ssh-keygen -p -f ~/.ssh/id_rsa
# This would prompt for passphrase

# Step 2: Extract hash from SSH key
# ssh2john ~/.ssh/id_rsa > ssh_hash.txt

# Step 3: Create simulated hash
cat > ssh_hash.txt << 'EOF'
id_rsa:$sshng$1$16$abc123...
EOF

# Step 4: Crack
john --wordlist=~/wordlists/top1000.txt ssh_hash.txt

# Step 5: View cracked passphrase
john --show ssh_hash.txt
```

### Exercise 5: Incremental Mode Practice

```bash
# Task: Use incremental mode for short passwords

# Step 1: Create hash of 3-character password
# "abc" MD5 = 900150983cd24fb0d6963f7d28e17f72
echo "900150983cd24fb0d6963f7d28e17f72" > short_hash.txt

# Step 2: Incremental with length limit
john --incremental --min-length=3 --max-length=3 short_hash.txt

# Step 3: Show result
john --show short_hash.txt

# Step 4: Try with lowercase only
john --incremental=Lower --min-length=1 --max-length=4 short_hash.txt
```

### Exercise 6: Custom Rules

```bash
# Task: Create and use custom rules

# Step 1: Create custom config
cat > ~/.john/my_rules.conf << 'EOF'
[List.Rules:MyRules]
# Append numbers 0-9
$[0-9]
# Capitalize and append number
c $[0-9]
# Append year
$[0-9]$[0-9]$[0-9]$[0-9]
EOF

# Step 2: Create hash
# "password1" MD5
echo "e00cf25ad42683b3df678c61f42c6bda" > rule_hash.txt

# Step 3: Use custom rules
john --wordlist=~/wordlists/top1000.txt --rules=MyRules \
     --config=~/.john/my_rules.conf rule_hash.txt

# Step 4: View result
john --show rule_hash.txt
```

### Exercise 7: Session Management

```bash
# Task: Practice session save and restore

# Step 1: Start a named session
john --session=test_session --wordlist=~/wordlists/top1000.txt hash.txt

# Step 2: Interrupt with Ctrl+C (simulate)

# Step 3: List sessions
ls ~/.john/sessions/

# Step 4: Restore session
john --restore=test_session

# Step 5: View pot file
cat ~/.john/john.pot
```

### Exercise 8: Performance Benchmark

```bash
# Task: Benchmark John's performance

# Step 1: Run full benchmark
john --test

# Step 2: Benchmark specific formats
john --test --format=raw-md5
john --test --format=raw-sha256
john --test --format=bcrypt

# Step 3: Compare speeds
# Note: bcrypt will be much slower than MD5
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "No password hashes loaded"

```bash
# Cause: Hash format not recognized or invalid hash

# Solution 1: Check hash format
john --list=formats | grep -i "your_format"

# Solution 2: Specify format manually
john --format=raw-md5 hash.txt

# Solution 3: Check hash file content
cat hash.txt
# Make sure there are no extra spaces or characters

# Solution 4: For shadow-style hashes, ensure correct format
# MD5crypt: $1$salt$hash
# SHA256crypt: $5$salt$hash
# SHA512crypt: $6$salt$hash
```

### Problem 2: "Unknown ciphertext format name"

```bash
# Cause: Wrong format name specified

# Solution 1: List available formats
john --list=formats | less

# Solution 2: Search for correct format name
john --list=formats | grep -i "sha256"
# Note: Format names might be "raw-sha256" not just "sha256"

# Solution 3: Use partial match
john --format=sha256 hash.txt
# John will try to match
```

### Problem 3: Wordlist Not Found

```bash
# Cause: Incorrect wordlist path

# Solution 1: Use absolute path
john --wordlist=/data/data/com.termux/files/home/wordlists/rockyou.txt hash.txt

# Solution 2: Check if file exists
ls -la ~/wordlists/rockyou.txt

# Solution 3: Download wordlist
mkdir -p ~/wordlists
cd ~/wordlists
wget [wordlist_url]

# Solution 4: Use default wordlist location
pkg install seclists -y
john --wordlist=$PREFIX/share/seclists/Passwords/Common-Credentials/10k-most-common.txt hash.txt
```

### Problem 4: Cracking Too Slow

```bash
# Cause: Strong hash type or large wordlist

# Solution 1: Use multi-core
john --fork=$(nproc) hash.txt

# Solution 2: Use smaller wordlist first
john --wordlist=top1000.txt hash.txt

# Solution 3: Add rules for variations
john --wordlist=rockyou.txt --rules hash.txt

# Solution 4: For strong hashes, be patient
# bcrypt can take hours/days for strong passwords

# Solution 5: Check if already cracked
john --show hash.txt
```

### Problem 5: zip2john/pdf2john Not Found

```bash
# Cause: Tools not in PATH or not installed

# Solution 1: Find tool location
find $PREFIX -name "zip2john*" 2>/dev/null

# Solution 2: Use full path
$PREFIX/bin/zip2john file.zip > hash.txt

# Solution 3: Reinstall john
pkg uninstall john
pkg install john -y

# Solution 4: Check if it's a Python script
find $PREFIX -name "*2john*" 2>/dev/null
python $PREFIX/share/john/pdf2john.py file.pdf > hash.txt
```

### Problem 6: Session Won't Restore

```bash
# Cause: Corrupted session file or wrong session name

# Solution 1: List available sessions
ls -la ~/.john/sessions/

# Solution 2: Use correct session name
john --restore=exact_session_name

# Solution 3: Check session file content
cat ~/.john/sessions/session_name.rec

# Solution 4: Start fresh if corrupted
rm ~/.john/sessions/session_name.*
john --session=new_session hash.txt
```

### Problem 7: Pot File Conflicts

```bash
# Cause: Previous cracked passwords interfering

# Solution 1: Clear pot file
rm ~/.john/john.pot

# Solution 2: View pot file first
cat ~/.john/john.pot

# Solution 3: Move pot file as backup
mv ~/.john/john.pot ~/.john/john.pot.bak

# Solution 4: Use different pot file
john --pot=my_pot.pot hash.txt
```

### Problem 8: Out of Memory

```bash
# Cause: Large wordlist or fork too many processes

# Solution 1: Reduce fork count
john --fork=2 hash.txt

# Solution 2: Use smaller wordlist chunks
split -l 1000000 rockyou.txt chunk_
john --wordlist=chunk_aa hash.txt

# Solution 3: Increase Termux memory limit
# Settings → Apps → Termux → Memory

# Solution 4: Use incremental instead
john --incremental hash.txt
```

### Problem 9: Format Detection Fails

```bash
# Cause: Non-standard hash format

# Solution 1: Manually specify format
john --format=raw-md5 hash.txt

# Solution 2: Use hash-identifier tool
pkg install hash-identifier -y
hash-identifier
# Paste your hash

# Solution 3: Check hash prefix
# bcrypt: $2a$, $2b$, $2y$
# SHA256crypt: $5$
# SHA512crypt: $6$
# MD5crypt: $1$

# Solution 4: Normalize hash format
# Remove any prefixes/suffixes
```

### Problem 10: Permission Denied

```bash
# Cause: File permissions issue

# Solution 1: Check file permissions
ls -la hash.txt

# Solution 2: Change permissions
chmod 644 hash.txt

# Solution 3: Check John directory
ls -la ~/.john/
chmod -R 755 ~/.john/

# Solution 4: Run from home directory
cd ~
john hash.txt
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Terminal Style**
```
┌────────────────────────────────────┐
│  [Black Terminal Background]       │
│                                    │
│  🔓 JOHN THE RIPPER                │
│  PASSWORD CRACKING                 │
│                                    │
│  ✓ Hash Types                      │
│  ✓ zip2john, pdf2john              │
│  ✓ Wordlist Attacks                │
│                                    │
│  [T3rmuxk1ng Logo]                 │
└────────────────────────────────────┘
```

**Option B: Comparison Style**
```
┌────────────────────────────────────┐
│  HYDRA        │  JOHN              │
│  Online       │  Offline           │
│  Attack       │  Hash Crack        │
│  ─────────────┼─────────────────   │
│                                    │
│  JOHN THE RIPPER                   │
│  MASTER CLASS                      │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Eye-Catching**
```
┌────────────────────────────────────┐
│  🔥 CRACK ANY PASSWORD?            │
│                                    │
│  John the Ripper Tutorial          │
│  Complete Guide in Termux          │
│                                    │
│  ⚡ ZIP, PDF, SSH, Linux           │
│                                    │
│  Chapter 33 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔓 Termux Full Course - Chapter 33: John the Ripper - Password Hash Cracking

🔥 In this video you'll learn:
• Hash kya hai aur cracking kaise kaam karti hai
• John the Ripper install aur configure karna
• MD5, SHA, bcrypt hash types identify karna
• Wordlist attacks with rockyou.txt
• Incremental brute-force mode
• Hash extraction: zip2john, pdf2john, ssh2john
• Custom rules banana
• Session management aur performance tuning

⏱️ Timestamps:
0:00 - Introduction
1:00 - Hash Cracking Concepts
4:30 - John Installation
7:00 - Hash Identification
10:00 - Basic John Usage
13:30 - Wordlist Attacks
16:30 - Incremental Mode
18:30 - Hash Extraction Tools
21:30 - Unshadow Command
23:30 - Custom Rules
25:30 - Session Management
27:30 - Performance Tuning
29:30 - Summary

📥 Download Links:
• John the Ripper: pkg install john
• SecLists Wordlists: pkg install seclists
• rockyou.txt: https://github.com/danielmiessler/SecLists

📝 Commands from this video:
pkg install john -y
john --wordlist=rockyou.txt hash.txt
zip2john file.zip > hash.txt
john --show hash.txt
john --incremental hash.txt

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#JohnTheRipper #PasswordCracking #Termux #EthicalHacking #T3rmuxk1ng #HashCracking #CyberSecurity

---
⚠️ Disclaimer: This video is for educational purposes only. Only crack passwords on systems you own or have explicit permission to test. Unauthorized password cracking is illegal.
```

### Tags List

```
john the ripper, password cracking, hash cracking, termux john, 
john the ripper tutorial, john the ripper termux, hash cracker,
md5 crack, sha256 crack, bcrypt crack, zip password crack,
pdf password crack, ssh password crack, wordlist attack,
brute force password, ethical hacking, cybersecurity, 
password recovery, hash types, rockyou wordlist, 
zip2john, pdf2john, ssh2john, unshadow, john tutorial,
offline password cracking, t3rmuxk1ng, termux course,
hindi tutorial, learn hacking, security tools
```

### Hashtags

```
#JohnTheRipper #PasswordCracking #HashCracking #Termux 
#EthicalHacking #CyberSecurity #HashTypes #WordlistAttack 
#BruteForce #ZipPassword #PdfPassword #SSHCrack 
#T3rmuxk1ng #TermuxCourse #HindiTutorial #LearnHacking
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| John the Ripper Official | https://www.openwall.com/john/ |
| John GitHub | https://github.com/openwall/john |
| John Wiki | https://openwall.info/wiki/john |
| John Documentation | https://www.openwall.com/john/doc/ |

### Wordlist Resources

| Resource | Description |
|----------|-------------|
| SecLists | Comprehensive collection of security lists |
| rockyou.txt | 14 million passwords from 2009 breach |
| CrackStation | 1.5 billion passwords |
| Weakpass | Various wordlists for different scenarios |

### Hash Identification Tools

| Tool | Usage |
|------|-------|
| hash-identifier | pkg install hash-identifier |
| hashid | pip install hashid |
| name-that-hash | pip install name-that-hash |
| haiti | pip install haiti |

### Learning Resources

| Resource | Description |
|----------|-------------|
| John Examples | /usr/share/john/ or $PREFIX/share/john/ |
| John Config | ~/.john/john.conf |
| Hash Examples | https://hashes.com/en/tools/hash_identifier |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 34, verify:

- [ ] John the Ripper installed successfully
- [ ] Understand what hashes are and how cracking works
- [ ] Can identify common hash types (MD5, SHA, bcrypt)
- [ ] Successfully cracked a hash using wordlist attack
- [ ] Used zip2john or similar extraction tool
- [ ] Understand session management
- [ ] Can use custom rules
- [ ] Know difference between single, wordlist, and incremental modes
- [ ] Understand ethical and legal implications

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 34: SQLMap Basics**

- SQL injection fundamentals
- SQLMap installation in Termux
- Basic SQLMap commands
- Database enumeration
- Dumping tables and columns
- SQL injection types
- Testing on vulnerable apps
- Automated exploitation

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
