```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║      ██╗ ██████╗ ██████╗  ██████╗ ██╗   ██╗██╗██████╗                         ║
║      ██║██╔═══██╗██╔══██╗██╔════╝ ██║   ██║██║██╔══██╗                        ║
║      ██║██║   ██║██████╔╝██║  ███╗██║   ██║██║██║  ██║                        ║
║  ██   ██║██║   ██║██╔══██╗██║   ██║██║   ██║██║██║  ██║                        ║
║  ╚█████╔╝╚██████╔╝██║  ██║╚██████╔╝╚██████╔╝██║██████╔╝                        ║
║   ╚════╝  ╚═════╝ ╚═╝  ╚═╝ ╚═════╝  ╚═════╝ ╚═╝╚═════╝                         ║
║                                                                               ║
║  ██████╗ ██████╗ ██████╗ ███████╗██╗    ██╗██╗███████╗███████╗ █████╗ ██████╗ ██╗██╗██╗    ║
║  ██╔══██╗██╔══██╗██╔══██╗██╔════╝██║    ██║██║██╔════╝██╔════╝██╔══██╗██╔══██╗██║██║██║    ║
║  ██████╔╝██████╔╝██████╔╝█████╗  ██║ █╗ ██║██║█████╗  █████╗  ███████║██████╔╝██║██║██║    ║
║  ██╔══██╗██╔═══╝ ██╔═══╝ ██╔══╝  ██║███╗██║██║██╔══╝  ██╔══╝  ██╔══██║██╔══██╗██║██║██║    ║
║  ██║  ██║██║     ██║     ███████╗╚███╔███╔╝██║██║     ███████╗██║  ██║██║  ██║██║██║██║    ║
║  ╚═╝  ╚═╝╚═╝     ╚═╝     ╚══════╝ ╚══╝╚══╝ ╚═╝╚═╝     ╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝╚═╝╚═╝    ║
║                                                                               ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                      CHAPTER 33: HASH CRACKING MASTERY                        ║
║                                                                               ║
║   📚 Module: 6 - Security Tools                                               ║
║   📖 Chapter: 33 of 61                                                        ║
║   ⏱️ Duration: 20-25 Minutes                                                   ║
║   ⭐ Difficulty: ⭐⭐⭐ Intermediate                                             ║
║   👨‍💻 Author: T3rmuxk1ng                                                       ║
║                                                                               ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                           LEARNING OBJECTIVES                                 ║
║                                                                               ║
║   ▶️ Understand password hashing and one-way functions                        ║
║   ▶️ Identify 15+ hash types by length and prefix                            ║
║   ▶️ Master wordlist, incremental, and rule-based attacks                    ║
║   ▶️ Use hash extraction tools (zip2john, pdf2john, ssh2john)                ║
║   ▶️ Configure custom cracking rules for targeted attacks                     ║
║   ▶️ Optimize performance with multi-core processing                          ║
║                                                                               ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                           TOOLS COVERED                                       ║
║                                                                               ║
║   🔧 John the Ripper - Offline password hash cracking (400+ formats)          ║
║   🔧 zip2john        - ZIP archive hash extraction                            ║
║   🔧 pdf2john        - PDF password hash extraction                           ║
║   🔧 ssh2john        - SSH key passphrase extraction                          ║
║   🔧 unshadow        - Linux password file combiner                           ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

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
- [ ] Completed the interactive quiz
- [ ] Attempted at least 2 challenges

---

## 🎮 INTERACTIVE QUIZ

Test your John the Ripper knowledge! Answers are hidden below each question.

### Question 1
**What is the difference between online and offline password cracking?**
<details>
<summary>Click to reveal answer</summary>

Online cracking (like Hydra) attacks live services over the network. Offline cracking (like John) works on captured password hashes without network interaction - faster and undetectable.
</details>

### Question 2
**How do you identify a hash type?**
<details>
<summary>Click to reveal answer</summary>

Check the hash length and prefix:
- 32 chars = MD5, NTLM
- 40 chars = SHA1
- 64 chars = SHA256
- 128 chars = SHA512
- Starts with $2a$/$2b$ = bcrypt
- Starts with $6$ = SHA-512crypt
</details>

### Question 3
**What command lists all supported formats in John?**
<details>
<summary>Click to reveal answer</summary>

`john --list=formats` shows all 400+ supported hash formats. Use `john --list=formats | grep -i "sha256"` to search for specific formats.
</details>

### Question 4
**How do you use a wordlist with John?**
<details>
<summary>Click to reveal answer</summary>

Use `--wordlist=/path/to/wordlist.txt`: `john --wordlist=rockyou.txt hash.txt`
</details>

### Question 5
**What does zip2john do?**
<details>
<summary>Click to reveal answer</summary>

zip2john extracts the password hash from ZIP archives into a format John can crack. Usage: `zip2john protected.zip > hash.txt`
</details>

### Question 6
**How do you resume a stopped cracking session?**
<details>
<summary>Click to reveal answer</summary>

Use `john --restore` to resume the last session, or `john --restore=session_name` for a named session.
</details>

### Question 7
**What is incremental mode in John?**
<details>
<summary>Click to reveal answer</summary>

Incremental mode is brute-force attack that tries all possible character combinations. It's thorough but very slow for complex passwords.
</details>

### Question 8
**How do you show already cracked passwords?**
<details>
<summary>Click to reveal answer</summary>

Use `john --show hash.txt` to display all cracked passwords from a hash file.
</details>

### Question 9
**What is unshadow command used for?**
<details>
<summary>Click to reveal answer</summary>

unshadow combines /etc/passwd and /etc/shadow files from Linux systems into a format John can crack: `unshadow /etc/passwd /etc/shadow > combined.txt`
</details>

### Question 10
**How do you use multiple CPU cores in John?**
<details>
<summary>Click to reveal answer</summary>

Use `--fork=N` where N is the number of cores: `john --fork=4 hash.txt` or `john --fork=$(nproc) hash.txt`
</details>

### Question 11
**What are custom rules in John?**
<details>
<summary>Click to reveal answer</summary>

Custom rules define password mutations like adding numbers, capitalizing, or leet speak. Use with `--rules=RuleName` option.
</details>

### Question 12
**How do you crack a PDF password?**
<details>
<summary>Click to reveal answer</summary>

Extract hash with pdf2john: `pdf2john protected.pdf > hash.txt`, then crack: `john --wordlist=rockyou.txt hash.txt`
</details>

### Question 13
**What is john.pot file?**
<details>
<summary>Click to reveal answer</summary>

john.pot stores all successfully cracked passwords. Located at ~/.john/john.pot. Clear it with `rm ~/.john/john.pot` for fresh start.
</details>

### Question 14
**How do you specify a specific hash format?**
<details>
<summary>Click to reveal answer</summary>

Use `--format=formatname`: `john --format=raw-md5 --wordlist=rockyou.txt hash.txt`
</details>

### Question 15
**What's the difference between single crack mode and wordlist mode?**
<details>
<summary>Click to reveal answer</summary>

Single crack mode uses the username and other information from the hash file itself to try variations. Wordlist mode tries passwords from an external wordlist file.
</details>

---

## 🎯 INTERVIEW QUESTIONS

### Q1: Explain the difference between hashing and encryption.

**Answer:**
- **Hashing** is one-way: data → hash, but hash → data is not possible. Used for password storage. Examples: MD5, SHA, bcrypt.
- **Encryption** is two-way: data ↔ encrypted data (with key). Used for data confidentiality. Examples: AES, RSA.

Passwords are stored as hashes because if the database is compromised, attackers can't reverse the hash to get the original password. They must try passwords and compare hashes.

### Q2: Why is bcrypt considered more secure than MD5 for passwords?

**Answer:**
1. **Work factor**: bcrypt has adjustable cost parameter (iterations) making it deliberately slow
2. **Salt built-in**: bcrypt generates unique salts automatically
3. **Memory-hard**: bcrypt requires more memory, resistant to GPU attacks
4. **MD5 is fast**: Billions of hashes/second can be computed, enabling brute-force attacks

A bcrypt hash with cost factor 12 takes ~250ms per attempt, while MD5 takes microseconds. This makes dictionary attacks impractical for bcrypt.

### Q3: How would you approach cracking a large password database?

**Answer:**
```
Step 1: Analyze hash types
- Identify hash formats with hash-identifier
- Group by hash type

Step 2: Quick wins first
- Single crack mode (uses usernames)
- Common passwords (admin, password123)
- Dictionary attack with top 10k passwords

Step 3: Medium effort
- Full wordlist (rockyou.txt)
- Apply rules (best64, OneRuleToRuleThemAll)
- Mangling rules (add numbers, symbols)

Step 4: Targeted attacks
- Company-specific wordlist
- Password policy analysis
- Mask attacks if pattern known

Step 5: Brute force
- Incremental mode for short passwords
- Distributed across multiple machines
```

### Q4: What is a salt and why is it important in password hashing?

**Answer:**
A salt is random data added to the password before hashing:
`hash(password + salt)`

**Importance:**
1. **Prevents rainbow table attacks**: Each user gets unique salt, so precomputed tables are useless
2. **Same password = different hashes**: Two users with "password123" have different hashes
3. **Increases cracking effort**: Must crack each password individually

Modern hash functions (bcrypt, Argon2) include automatic salting.

### Q5: How do you extract hashes from various file formats?

**Answer:**
John includes extraction tools for many formats:

| File Type | Tool | Usage |
|-----------|------|-------|
| ZIP | zip2john | `zip2john file.zip > hash.txt` |
| PDF | pdf2john | `pdf2john file.pdf > hash.txt` |
| RAR | rar2john | `rar2john file.rar > hash.txt` |
| Office | office2john | `office2john file.docx > hash.txt` |
| SSH Key | ssh2john | `ssh2john id_rsa > hash.txt` |
| KeePass | keepass2john | `keepass2john db.kdbx > hash.txt` |
| 7z | 7z2john | `7z2john file.7z > hash.txt` |

### Q6: What are rainbow tables and are they still effective?

**Answer:**
Rainbow tables are precomputed hash chains for quick lookup.

**How they work:**
1. Precompute chains of hash → reduce → hash → reduce
2. Store only start and end points
3. Lookup: regenerate chains until match found

**Effectiveness:**
- **Effective against**: Unsalted hashes (MD5, SHA1), old Windows LM hashes
- **Ineffective against**: Salted hashes, bcrypt, Argon2, modern systems

**Modern defense**: Salting, slow hash functions, and pepper make rainbow tables impractical. They're largely obsolete for password cracking.

### Q7: How would you optimize John's performance on limited hardware?

**Answer:**
1. **Use appropriate mode**: Wordlist > Rules > Incremental (in terms of speed)
2. **Fork processes**: Use multiple CPU cores with `--fork`
3. **Target specific users**: `--users=admin,root`
4. **Limit charset**: `--incremental=Lower` for lowercase only
5. **Use smaller wordlists**: Start with top passwords, expand if needed
6. **External modes**: Some are faster than built-in
7. **Skip already cracked**: John does this automatically via john.pot

### Q8: What is the difference between mask attack and incremental attack?

**Answer:**
**Mask Attack:**
- Defines specific pattern: `?d?d?d?d?d?d` (6 digits)
- Uses known password format
- Much faster for known patterns
- Example: `john --mask=?u?l?l?l?d?d hash.txt`

**Incremental Attack:**
- Tries all possible combinations
- No pattern assumption
- Extremely slow for long passwords
- Example: `john --incremental hash.txt`

Use mask when password policy or hints are known; use incremental as last resort.

### Q9: How do you handle password-protected Office documents?

**Answer:**
```bash
# Extract hash
office2john document.docx > office_hash.txt

# View hash format
cat office_hash.txt

# Crack with wordlist
john --wordlist=rockyou.txt office_hash.txt

# Check results
john --show office_hash.txt

# For newer Office (2013+), may need specific format
john --format=office2013 --wordlist=rockyou.txt office_hash.txt
```

Office 2010+ uses AES-128/256 which is slow to crack. Older Office (XP/2003) uses weak encryption.

### Q10: What are the legal and ethical considerations of password cracking?

**Answer:**
**Legal:**
- Only crack passwords you own or have explicit permission
- Written authorization required for client systems
- Document scope and methodology
- Return or securely delete cracked passwords after testing

**Ethical:**
- Report findings to system owners
- Recommend password policy improvements
- Don't share cracked passwords
- Help implement better security

**Consequences of unauthorized cracking:**
- Computer Fraud and Abuse Act (US)
- IT Act violations (India)
- GDPR violations (EU)
- Criminal charges and imprisonment

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: IT Audit - Password Strength Testing

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                  IT AUDIT - PASSWORD STRENGTH TESTING                     ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Company wants to audit password security. IT extracted shadow file.     ║
║  500 users, policy requires 8+ chars with complexity.                    ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Combine passwd and shadow:                                           ║
║     unshadow passwd.txt shadow.txt > combined.txt                        ║
║                                                                           ║
║  2. Quick analysis:                                                       ║
║     john --show combined.txt  # Already cracked?                         ║
║                                                                           ║
║  3. Single crack mode first:                                              ║
║     john --single combined.txt                                           ║
║     # Uses usernames as password hints                                    ║
║                                                                           ║
║  4. Dictionary attack:                                                    ║
║     john --wordlist=rockyou.txt combined.txt                             ║
║                                                                           ║
║  5. Rules attack:                                                         ║
║     john --wordlist=rockyou.txt --rules=best64 combined.txt              ║
║                                                                           ║
║  RESULT: Cracked 45 passwords (9%)                                       ║
║  - 20 used company name variations                                       ║
║  - 15 used simple patterns (Summer2024!)                                 ║
║  - 10 used common passwords                                              ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: Forensic Investigation

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    FORENSIC INVESTIGATION                                 ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Legal case requires access to password-protected documents.             ║
║  ZIP, PDF, and Office files found on suspect's computer.                 ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Extract all hashes:                                                   ║
║     for f in *.zip; do zip2john "$f" >> all_hashes.txt; done             ║
║     for f in *.pdf; do pdf2john "$f" >> all_hashes.txt; done             ║
║     for f in *.docx; do office2john "$f" >> all_hashes.txt; done         ║
║                                                                           ║
║  2. Create targeted wordlist:                                             ║
║     # From suspect's social media, emails, personal info                 ║
║     cat suspect_info.txt > wordlist.txt                                  ║
║     cat birthdays.txt >> wordlist.txt                                    ║
║     cat pet_names.txt >> wordlist.txt                                    ║
║                                                                           ║
║  3. Crack with personal wordlist:                                         ║
║     john --wordlist=wordlist.txt --rules all_hashes.txt                  ║
║                                                                           ║
║  4. Full dictionary if needed:                                            ║
║     john --wordlist=rockyou.txt all_hashes.txt                           ║
║                                                                           ║
║  RESULT: Cracked 12 of 15 files within 2 hours                           ║
║  Password patterns: pet names + birth years                              ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: Penetration Test Deliverable

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                  PENETRATION TEST DELIVERABLE                             ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Pentester dumped hashes from compromised Windows domain controller.     ║
║  Need to crack NTLM hashes for privilege escalation.                     ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Extract NTLM hashes:                                                  ║
║     # From SAM database or lsass dump                                    ║
║     # Format: user:RID:LM:NTLM:::                                        ║
║                                                                           ║
║  2. Quick NTLM crack:                                                     ║
║     john --format=NT --wordlist=rockyou.txt ntlm_hashes.txt              ║
║     # NTLM is fast - millions/sec                                        ║
║                                                                           ║
║  3. Use hashcat for GPU acceleration (if available):                      ║
║     hashcat -m 1000 -a 0 ntlm_hashes.txt rockyou.txt                     ║
║                                                                           ║
║  4. Check for admin accounts:                                             ║
║     grep -i "admin" cracked_passwords.txt                                ║
║                                                                           ║
║  RESULT: Cracked 200+ passwords in 30 minutes                            ║
║  - Found Domain Admin password: Company2024!                             ║
║  - Full domain compromise achieved                                        ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: Password Recovery

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    PASSWORD RECOVERY                                      ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  User forgot password to important KeePass database.                     ║
║  Remembers it was about 10 chars with "summer" somewhere.                ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Extract hash:                                                         ║
║     keepass2john database.kdbx > keepass_hash.txt                        ║
║                                                                           ║
║  2. Create targeted mask:                                                 ║
║     # Pattern: summer + some characters                                   ║
║     john --mask='summer?d?d?d?d' keepass_hash.txt                        ║
║     john --mask='?d?dsummer?d?d' keepass_hash.txt                        ║
║     john --mask='?l?l?l?lsummer?d?d' keepass_hash.txt                    ║
║                                                                           ║
║  3. Use rules with base word:                                             ║
║     echo "summer" > base.txt                                              ║
║     john --wordlist=base.txt --rules keepass_hash.txt                    ║
║                                                                           ║
║  4. Incremental limited length:                                            ║
║     john --incremental --min-length=8 --max-length=12 keepass_hash.txt   ║
║                                                                           ║
║  RESULT: Recovered password: Summer2023! after 4 hours                   ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: SSH Key Recovery

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    SSH KEY PASSPHRASE RECOVERY                            ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Developer's encrypted SSH private key passphrase forgotten.             ║
║  Key needed for production server access.                                ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Extract hash from key:                                                ║
║     ssh2john id_rsa > ssh_hash.txt                                       ║
║                                                                           ║
║  2. Try common developer passwords:                                       ║
║     john --wordlist=dev_passwords.txt ssh_hash.txt                       ║
║     # Include: project names, company name, tech terms                   ║
║                                                                           ║
║  3. Dictionary attack:                                                    ║
║     john --wordlist=rockyou.txt ssh_hash.txt                             ║
║                                                                           ║
║  4. Mask attack if partial memory:                                        ║
║     # Developer remembers "github" was part of it                         ║
║     john --mask='github?d?d?d?d' ssh_hash.txt                            ║
║     john --mask='?d?dgithub?d?d' ssh_hash.txt                            ║
║                                                                           ║
║  RESULT: Recovered passphrase: github2024                                ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

---

## ⚠️ SECURITY BEST PRACTICES

### ✅ DO's

| Practice | Description |
|----------|-------------|
| ✅ Use strong hashes | bcrypt, Argon2, scrypt for passwords |
| ✅ Add salts | Unique random salt per password |
| ✅ Set work factor | High iteration count (bcrypt cost 12+) |
| ✅ Use wordlists for testing | Test password policies before deployment |
| ✅ Document cracking attempts | For audit and reporting |
| ✅ Report findings | Help improve security posture |
| ✅ Use sessions | Save progress for long operations |
| ✅ Clean john.pot | Remove cracked passwords after testing |
| ✅ Use multi-core | Fork across available CPU cores |
| ✅ Start simple | Quick wins before complex attacks |

### ❌ DON'Ts

| Practice | Risk |
|----------|------|
| ❌ Use MD5/SHA1 for passwords | Fast, easily cracked |
| ❌ Skip salting | Vulnerable to rainbow tables |
| ❌ Ignore work factors | Low iterations = fast cracking |
| ❌ Store plain passwords | Security disaster |
| ❌ Crack without authorization | Illegal and unethical |
| ❌ Share cracked passwords | Security breach |
| ❌ Ignore hash identification | Wrong format = failed cracking |
| ❌ Use only brute force | Inefficient for long passwords |
| ❌ Forget to test policies | Weak passwords in production |
| ❌ Neglect GPU acceleration | Much faster than CPU alone |

---

## 📊 ARCHITECTURE DIAGRAMS

### John the Ripper Workflow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        JOHN THE RIPPER WORKFLOW                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌────────────┐ │
│   │   INPUT     │    │   CRACKING  │    │    HASH     │    │   OUTPUT   │ │
│   │   SOURCE    │    │    MODES    │    │  COMPARISON │    │            │ │
│   │             │    │             │    │             │    │            │ │
│   │ - Hash file │───►│ - Single    │───►│ Candidate   │───►│ Cracked    │ │
│   │ - Shadow    │    │ - Wordlist  │    │ Hash        │    │ Password   │ │
│   │ - Extracted │    │ - Increment │    │ Compare     │    │ Store in   │ │
│   │             │    │ - Rules     │    │ Target      │    │ john.pot   │ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └────────────┘ │
│                                                                             │
│   Extraction Tools:                                                         │
│   ┌────────────────────────────────────────────────────────────────────┐   │
│   │ zip2john │ pdf2john │ office2john │ ssh2john │ rar2john │ ...    │   │
│   └────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Hash Type Identification

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    HASH TYPE IDENTIFICATION                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   HASH STRING                          IDENTIFY BY                          │
│   ───────────                          ───────────                          │
│                                                                             │
│   5d41402abc4b2a76b9719d911017c592     Length: 32 → MD5, NTLM             │
│                                                                             │
│   aaf4c61ddcc5e8a2dabede0f3b482cd...   Length: 40 → SHA1                   │
│                                                                             │
│   2c26b46b68ffc68ff99b453c1d304134     Length: 40 → SHA1                     │
│                                                                             │
│   2c26b46b68ffc68ff99b453c1d304134...  Length: 64 → SHA256                │
│                                                                             │
│   $2a$10$N9qo8uLOickgx2ZMRZoMy...     Prefix: $2 → bcrypt                 │
│                                                                             │
│   $6$rounds=5000$salt$hash...          Prefix: $6 → SHA-512crypt          │
│                                                                             │
│   $5$rounds=5000$salt$hash...          Prefix: $5 → SHA-256crypt          │
│                                                                             │
│   $1$salt$hash...                      Prefix: $1 → MD5crypt               │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Attack Mode Selection

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ATTACK MODE SELECTION                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌───────────────────────────────────────────────────────────────────┐    │
│   │                    START CRACKING                                  │    │
│   └──────────────────────────────────┬────────────────────────────────┘    │
│                                      │                                      │
│                    ┌─────────────────┼─────────────────┐                   │
│                    ▼                 ▼                 ▼                   │
│   ┌────────────────────┐ ┌────────────────────┐ ┌────────────────────┐    │
│   │   SINGLE CRACK     │ │    WORDLIST        │ │   INCREMENTAL      │    │
│   │                    │ │                    │ │                    │    │
│   │ - Uses username    │ │ - External file    │ │ - Brute force      │    │
│   │ - Fast             │ │ - Medium speed     │ │ - Very slow        │    │
│   │ - Low success      │ │ - Good success     │ │ - Complete         │    │
│   │                    │ │                    │ │                    │    │
│   │ john --single      │ │ john --wordlist=   │ │ john --incremental │    │
│   │                    │ │   rockyou.txt      │ │                    │    │
│   └────────────────────┘ └─────────┬──────────┘ └────────────────────┘    │
│                                    │                                        │
│                                    ▼                                        │
│                         ┌────────────────────┐                             │
│                         │   RULES ATTACK     │                             │
│                         │                    │                             │
│                         │ - Wordlist + rules │                             │
│                         │ - Password mutations│                             │
│                         │ - Best success rate│                             │
│                         │                    │                             │
│                         │ john --wordlist=   │                             │
│                         │   x --rules=best64 │                             │
│                         └────────────────────┘                             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relevance |
|---------|-------|-----------|
| Chapter 31 | Hydra Password Cracking | Online password attacks |
| Chapter 32 | Hydra Advanced | Advanced online cracking |
| Chapter 34 | SQLMap Basics | Database credential extraction |
| Chapter 45 | Password Security | Password policy design |
| Chapter 46 | Hash Identification | Hash type analysis |
| Chapter 47 | Encryption Basics | Hashing vs encryption |
| Chapter 50 | Forensics Basics | Evidence handling |

---

## 🏆 BONUS ADVANCED CONTENT

### Technique 1: Custom Rule Creation

Create powerful password mutation rules:

```bash
# Create custom rules file
cat > ~/.john/custom_rules.conf << 'EOF'
[List.Rules:CustomComplex]
# Add common suffixes
$[0-9]$[0-9]$[0-9]$[0-9]
$[1-9][0-9][0-9][0-9]

# Add year suffixes  
$2023
$2024
$2025

# Capitalize variations
c Az"
l Az"

# Leet speak
sa@ se3 si1 so0 ss$
EOF

# Use custom rules
john --wordlist=rockyou.txt --rules=CustomComplex --config=~/.john/custom_rules.conf hash.txt
```

### Technique 2: Mask Attack for Known Patterns

Use masks when password pattern is known:

```bash
# Password is 8 chars: Capital letter + lowercase + 6 digits
john --mask='?u?l?d?d?d?d?d?d' hash.txt

# Password contains "Password" followed by 4 digits
john --mask='Password?d?d?d?d' hash.txt

# Password pattern: Word + Year + Symbol
john --mask='?w?w?w?w?w?w2024?s' hash.txt

# Incremental with mask
john --mask='?l?l?l?l?d?d?d?d' --min-length=8 --max-length=8 hash.txt
```

### Technique 3: Multi-Format Batch Processing

Process multiple file types automatically:

```bash
#!/bin/bash
# Batch hash extraction and cracking

HASH_FILE="all_hashes.txt"
WORDLIST="rockyou.txt"

# Clear previous hashes
> $HASH_FILE

# Extract from all supported files
for f in *.zip; do
    echo "# $f" >> $HASH_FILE
    zip2john "$f" >> $HASH_FILE 2>/dev/null
done

for f in *.pdf; do
    echo "# $f" >> $HASH_FILE
    pdf2john "$f" >> $HASH_FILE 2>/dev/null
done

for f in *.doc* *.xls* *.ppt*; do
    echo "# $f" >> $HASH_FILE
    office2john "$f" >> $HASH_FILE 2>/dev/null
done

for f in *.rar; do
    echo "# $f" >> $HASH_FILE
    rar2john "$f" >> $HASH_FILE 2>/dev/null
done

for f in id_rsa*; do
    echo "# $f" >> $HASH_FILE
    ssh2john "$f" >> $HASH_FILE 2>/dev/null
done

# Start cracking session
john --wordlist=$WORDLIST --session=batch_crack $HASH_FILE

# Show results
john --show $HASH_FILE
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

- [ ] Understood difference between hashing and encryption
- [ ] Learned to identify hash types by length and prefix
- [ ] Mastered wordlist, incremental, and single crack modes
- [ ] Used hash extraction tools (zip2john, pdf2john, ssh2john)
- [ ] Applied custom rules for password mutations
- [ ] Configured session management and restore
- [ ] Optimized performance with multi-core processing
- [ ] Completed all practice exercises
- [ ] Completed the interactive quiz
- [ ] Attempted at least 2 challenges

---

## 🎮 INTERACTIVE QUIZ

Test your John the Ripper knowledge! Click to reveal answers.

<details>
<summary><b>Q1: What type of password cracking is John the Ripper used for?</b></summary>

Answer: **Offline password cracking**

John the Ripper works on captured hash files, not live services. It cracks hashes that have been extracted from systems, files, or databases.
</details>

<details>
<summary><b>Q2: Which command lists all supported hash formats in John?</b></summary>

Answer: **`john --list=formats`**

```bash
john --list=formats        # List all formats
john --list=formats | grep -i md5    # Search for MD5 formats
john --list=formats | wc -l          # Count formats (400+)
```
</details>

<details>
<summary><b>Q3: How do you extract a hash from a ZIP file?</b></summary>

Answer: **Using `zip2john` command**

```bash
zip2john protected.zip > zip_hash.txt
john zip_hash.txt                    # Crack the hash
john --show zip_hash.txt             # Show results
```
</details>

<details>
<summary><b>Q4: What is the difference between --wordlist and --incremental modes?</b></summary>

Answer: **Dictionary vs Brute-force**

| Mode | Description |
|------|-------------|
| `--wordlist` | Uses a predefined list of passwords |
| `--incremental` | Tries all possible character combinations (brute-force) |

```bash
john --wordlist=rockyou.txt hash.txt   # Dictionary attack
john --incremental hash.txt            # Brute-force attack
```
</details>

<details>
<summary><b>Q5: How do you specify the hash format manually?</b></summary>

Answer: **Using `--format=` option**

```bash
john --format=raw-md5 hash.txt
john --format=bcrypt hash.txt
john --format=nt hash.txt
```
John usually auto-detects, but manual specification helps with ambiguous hashes.
</details>

<details>
<summary><b>Q6: What is the purpose of the --rules option?</b></summary>

Answer: **Applies password mutation rules**

```bash
john --wordlist=rockyou.txt --rules hash.txt
```
Rules modify passwords: capitalize, add numbers, leet speak (a→@), etc.
Common rules: `best64`, `OneRuleToRuleThemAll`, `Jumbo`
</details>

<details>
<summary><b>Q7: How do you resume an interrupted cracking session?</b></summary>

Answer: **Using `--restore` option**

```bash
john --restore                    # Resume last session
john --restore=my_session         # Resume named session
```
Sessions are saved automatically. Use `--session=name` to name them.
</details>

<details>
<summary><b>Q8: What command shows already cracked passwords?</b></summary>

Answer: **`john --show hash.txt`**

```bash
john --show hash.txt
```
Cracked passwords are stored in `~/.john/john.pot` file.
</details>

<details>
<summary><b>Q9: How do you combine /etc/passwd and /etc/shadow files?</b></summary>

Answer: **Using `unshadow` command**

```bash
unshadow /etc/passwd /etc/shadow > combined.txt
john combined.txt
```
This is needed for cracking Linux password hashes.
</details>

<details>
<summary><b>Q10: What is the purpose of --fork option?</b></summary>

Answer: **Multi-core parallel processing**

```bash
john --fork=4 hash.txt           # Use 4 CPU cores
john --fork=$(nproc) hash.txt    # Use all available cores
```
Significantly speeds up cracking on multi-core systems.
</details>

<details>
<summary><b>Q11: How do you crack a PDF file password?</b></summary>

Answer: **Using `pdf2john` to extract hash first**

```bash
pdf2john protected.pdf > pdf_hash.txt
john --wordlist=rockyou.txt pdf_hash.txt
john --show pdf_hash.txt
```
</details>

<details>
<summary><b>Q12: What is the john.pot file?</b></summary>

Answer: **Database of cracked passwords**

Location: `~/.john/john.pot`

Contains all successfully cracked password:hash pairs. Used by `--show` command to display results.
</details>

<details>
<summary><b>Q13: How do you use incremental mode with limited character set?</b></summary>

Answer: **Specify the charset**

```bash
john --incremental=Digits hash.txt     # Numbers only
john --incremental=Lower hash.txt      # Lowercase only
john --incremental=Alnum hash.txt      # Alphanumeric
```
</details>

<details>
<summary><b>Q14: What is ssh2john used for?</b></summary>

Answer: **Extract hash from SSH private key**

```bash
ssh2john id_rsa > ssh_hash.txt
john --wordlist=rockyou.txt ssh_hash.txt
```
Used to crack the passphrase of encrypted SSH private keys.
</details>

<details>
<summary><b>Q15: How do you benchmark John the Ripper performance?</b></summary>

Answer: **Using `--test` option**

```bash
john --test                      # Benchmark all formats
john --test --format=raw-md5     # Benchmark specific format
```
Shows cracking speed in passwords per second for each hash type.
</details>

---

## 🎯 INTERVIEW QUESTIONS

### Q1: Explain the difference between John the Ripper and Hashcat.

**Answer:**

| Feature | John the Ripper | Hashcat |
|---------|----------------|---------|
| **Primary Focus** | CPU-based cracking | GPU-based cracking |
| **Hash Support** | 400+ formats | 300+ formats |
| **Speed** | Slower (CPU) | Much faster (GPU) |
| **Rules Engine** | Built-in, extensive | Separate rule files |
| **Modes** | Wordlist, Incremental, Single | Attack modes 0-9 |
| **Platform** | Works on any system | Needs GPU drivers |
| **Learning Curve** | Easier | Steeper |
| **Termux Support** | Excellent | Limited |

**When to use John:**
- CPU-only systems (Termux on Android)
- Quick hash identification
- File password cracking (zip, pdf, office)
- Systems without GPU support

---

### Q2: What are hash extraction tools and why are they needed?

**Answer:**

**Purpose:** John cannot directly read password-protected files. It needs the hash extracted first.

**Common Tools:**

| Tool | Purpose |
|------|---------|
| `zip2john` | Extract hash from ZIP archives |
| `rar2john` | Extract hash from RAR archives |
| `pdf2john` | Extract hash from PDF files |
| `office2john` | Extract hash from MS Office documents |
| `ssh2john` | Extract hash from SSH private keys |
| `keepass2john` | Extract hash from KeePass databases |
| `7z2john` | Extract hash from 7z archives |
| `unshadow` | Combine passwd & shadow for Linux |

**Workflow:**
```bash
# 1. Extract hash
zip2john file.zip > hash.txt

# 2. Crack the hash
john --wordlist=rockyou.txt hash.txt

# 3. View results
john --show hash.txt
```

---

### Q3: Explain John's cracking modes and when to use each.

**Answer:**

**1. Single Crack Mode (Default)**
```bash
john --single hash.txt
```
- Uses username as password variations
- Fastest for username-based passwords
- Best first attempt

**2. Wordlist Mode**
```bash
john --wordlist=rockyou.txt hash.txt
```
- Tests passwords from a file
- Most common approach
- Use targeted wordlists for better results

**3. Incremental Mode (Brute-force)**
```bash
john --incremental hash.txt
john --incremental=Digits --min-length=4 --max-length=6 hash.txt
```
- Tries all possible combinations
- Very slow for long passwords
- Best for short passwords (1-6 chars)

**4. External Mode**
```bash
john --external=lanman hash.txt
```
- Custom cracking algorithms
- Requires programming knowledge

**Recommended Order:**
1. Single crack
2. Wordlist with rules
3. Incremental (short passwords only)

---

### Q4: How would you approach cracking a bcrypt hash?

**Answer:**

**Understanding bcrypt:**
- Very slow by design
- Cost factor determines iteration count
- 10 rounds = 1024 iterations
- Designed to resist cracking

**Strategy:**

```bash
# 1. Identify the hash type
john --show=types hash.txt

# 2. Start with targeted wordlist
john --wordlist=custom_wordlist.txt --format=bcrypt hash.txt

# 3. Use rules for variations
john --wordlist=rockyou.txt --rules=best64 --format=bcrypt hash.txt

# 4. Multi-core processing
john --fork=4 --format=bcrypt hash.txt
```

**Realistic Expectations:**
- bcrypt cracking is SLOW (100-1000 hashes/sec vs millions for MD5)
- Focus on weak/common passwords
- Prioritize wordlist quality over brute-force
- Consider GPU-based Hashcat for serious bcrypt cracking

---

### Q5: What is the role of rules in password cracking?

**Answer:**

**Rules modify passwords to create variations:**

**Common Rule Examples:**
```
# Original: password
l             → password (lowercase)
u             → PASSWORD (uppercase)
c             → Password (capitalize)
$1            → password1 (append)
^123          → 123password (prepend)
r             → drowssap (reverse)
sa@ se3 si1   → p@ssword (leet speak)
```

**Using Rules:**
```bash
# Built-in rules
john --wordlist=rockyou.txt --rules hash.txt        # Default rules
john --wordlist=rockyou.txt --rules=best64 hash.txt # Best64 rules
john --wordlist=rockyou.txt --rules=Jumbo hash.txt  # Jumbo rules

# Custom rules
john --wordlist=rockyou.txt --rules=MyRule --config=my.conf hash.txt
```

**Creating Custom Rules:**
```
[List.Rules:CustomRule]
$[0-9]$[0-9]     # Add 2 digits at end
^[A-Z]           # Capitalize first letter
$[!@#$]          # Add special character
```

---

### Q6: How do you crack Windows password hashes?

**Answer:**

**Windows Hash Types:**

| Hash | Description | Security |
|------|-------------|----------|
| LM | Legacy, disabled by default | Very weak |
| NTLM | Current standard | Weak (no salt) |
| NTLMv2 | Network authentication | Better |

**Cracking Process:**

```bash
# 1. Extract hashes from Windows
# Using samdump2, pwdump, or mimikatz
samdump2 SYSTEM SAM > windows_hashes.txt

# 2. Crack NTLM hashes
john --format=nt windows_hashes.txt

# 3. With wordlist
john --format=nt --wordlist=rockyou.txt windows_hashes.txt

# 4. Show results
john --show --format=nt windows_hashes.txt
```

**Note:** NTLM hashes are unsalted, making them fast to crack. Rainbow tables also work well.

---

### Q7: How would you optimize John for performance?

**Answer:**

**Performance Optimization Techniques:**

**1. Multi-core Processing:**
```bash
john --fork=$(nproc) hash.txt
```

**2. Format-Specific Optimization:**
```bash
john --format=raw-md5 --fork=4 hash.txt
```

**3. Benchmarking:**
```bash
john --test --format=raw-md5
```

**4. Memory Management:**
```bash
# Use --max-length to limit search space
john --incremental --max-length=8 hash.txt

# Skip already cracked hashes
john hash.txt  # Automatically skips john.pot entries
```

**5. Rule Selection:**
```bash
# Light rules for speed
john --rules=single hash.txt

# Heavy rules for thoroughness
john --rules=best64 hash.txt
```

**6. OpenCL (if available):**
```bash
john --list=opencl-devices
john --opencl hash.txt
```

---

### Q8: Explain the unshadow command and its importance.

**Answer:**

**Purpose:** Combines `/etc/passwd` and `/etc/shadow` files for Linux password cracking.

**Linux Password Storage:**
- `/etc/passwd` - User info (world-readable)
- `/etc/shadow` - Password hashes (root-only)

**Why Unshadow is Needed:**
- John needs both username (from passwd) and hash (from shadow)
- Shadow file alone doesn't have user context

**Usage:**
```bash
# On the target Linux system (requires root)
cat /etc/passwd > passwd.txt
cat /etc/shadow > shadow.txt

# Combine them
unshadow passwd.txt shadow.txt > combined.txt

# Crack
john --wordlist=rockyou.txt combined.txt

# View cracked passwords
john --show combined.txt
```

**Output Format:**
```
username:$6$salt$hash:UID:GID:info:/home/dir:/shell
```

---

### Q9: What strategies would you use for cracking an unknown hash?

**Answer:**

**Step-by-Step Approach:**

**1. Identify Hash Type:**
```bash
# Using john
john --show=types hash.txt

# Using hash-identifier (separate tool)
hash-identifier
# Paste hash, get possible types

# Manual identification by length
# 32 chars = MD5/NTLM
# 40 chars = SHA1
# 64 chars = SHA256
# 60 chars starting $2 = bcrypt
```

**2. Try Common Formats:**
```bash
john --format=raw-md5 hash.txt
john --format=raw-sha1 hash.txt
john --format=raw-sha256 hash.txt
```

**3. Let John Auto-detect:**
```bash
john hash.txt  # John tries to identify automatically
```

**4. Check Prefix:**
```
$1$ = MD5crypt
$5$ = SHA-256crypt
$6$ = SHA-512crypt
$2a$/$2b$ = bcrypt
```

---

### Q10: How would you set up a comprehensive password cracking workflow?

**Answer:**

**Professional Workflow:**

```bash
#!/bin/bash
# Comprehensive John workflow

HASH_FILE=$1

# Step 1: Identify hash
echo "[*] Identifying hash type..."
john --show=types $HASH_FILE

# Step 2: Quick single crack
echo "[*] Running single crack mode..."
john --single $HASH_FILE
john --show $HASH_FILE

# Step 3: Common passwords
echo "[*] Testing common passwords..."
john --wordlist=rockyou.txt --rules=single $HASH_FILE
john --show $HASH_FILE

# Step 4: Full wordlist with rules
echo "[*] Full wordlist attack..."
john --wordlist=rockyou.txt --rules=best64 --fork=$(nproc) $HASH_FILE
john --show $HASH_FILE

# Step 5: Incremental for remaining
echo "[*] Incremental attack (short passwords)..."
john --incremental --min-length=1 --max-length=6 $HASH_FILE
john --show $HASH_FILE

echo "[*] Workflow complete"
```

**Documentation:**
- Save session names
- Track time spent
- Document success rates
- Maintain wordlist versions

---

## 🔥 REAL-WORLD SCENARIOS

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 1: Corporate Password Audit                   ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
A company discovered their password database was exposed. They need to 
identify which accounts have weak passwords before attackers do.

🎯 Objective:
Audit password strength and identify vulnerable accounts.

🔧 Approach:
# Step 1: Extract hashes from database
# (Assuming MySQL hash export)

# Step 2: Identify hash format
john --show=types company_hashes.txt

# Step 3: Test with company wordlist
john --wordlist=company_terms.txt --rules company_hashes.txt

# Step 4: Test with rockyou
john --wordlist=rockyou.txt --rules=best64 --fork=4 company_hashes.txt

# Step 5: Export results
john --show company_hashes.txt > cracked_passwords.txt

📊 Results:
- Cracked 23% of passwords within 24 hours
- Found several admin accounts with weak passwords
- Recommended password policy enforcement and MFA

⚠️ Notes:
- Use company-specific wordlist first
- Document all findings for compliance
- Secure handling of cracked credentials
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 2: Encrypted Document Recovery                ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
An employee left the company and their important password-protected 
documents need to be accessed for business continuity.

🎯 Objective:
Recover passwords for critical business documents.

🔧 Approach:
# PDF document
pdf2john confidential.pdf > pdf_hash.txt
john --wordlist=company_wordlist.txt pdf_hash.txt

# Office document
office2john report.docx > doc_hash.txt
john --wordlist=rockyou.txt --rules doc_hash.txt

# ZIP archive
zip2john backup.zip > zip_hash.txt
john --incremental --min-length=1 --max-length=6 zip_hash.txt

📊 Results:
- PDF cracked in 2 hours (password was company name + year)
- DOCX cracked in 30 minutes (common password)
- ZIP required custom wordlist but eventually cracked

⚠️ Notes:
- Legal authorization required
- Document the recovery process
- Update password policies after recovery
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 3: Linux Server Compromise                    ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
A Linux server was compromised. Security team needs to identify 
which accounts may have been accessed.

🎯 Objective:
Crack password hashes to assess exposure.

🔧 Approach:
# Step 1: Extract passwd and shadow files
# (Already done during incident response)

# Step 2: Unshadow
unshadow passwd.txt shadow.txt > linux_hashes.txt

# Step 3: Identify hash types
# $6$ = SHA-512crypt (modern Linux)

# Step 4: Targeted attack
john --wordlist=common_passwords.txt linux_hashes.txt

# Step 5: Full wordlist with multi-core
john --wordlist=rockyou.txt --fork=4 linux_hashes.txt

📊 Results:
- 3 user accounts cracked within 4 hours
- Root password was strong (not cracked)
- Identified compromised service account
- Forced password reset for all users

⚠️ Notes:
- SHA-512crypt is slow, prioritize accounts
- Document for incident report
- Implement account lockout policies
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 4: SSH Key Passphrase Recovery                ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
A developer lost the passphrase for their SSH private key, but the 
key is needed urgently for production deployment.

🎯 Objective:
Recover SSH key passphrase to regain access.

🔧 Approach:
# Step 1: Extract hash from SSH key
ssh2john id_rsa > ssh_hash.txt

# Step 2: Try developer's common passwords
cat > dev_wordlist.txt << EOF
password123
developer
projectname
company2024
EOF

john --wordlist=dev_wordlist.txt ssh_hash.txt

# Step 3: With rules for variations
john --wordlist=dev_wordlist.txt --rules ssh_hash.txt

📊 Results:
- Passphrase recovered in 15 minutes
- Developer used project name + year
- Implemented SSH key backup process
- Added passphrase hints system

⚠️ Notes:
- Private key security is critical
- Consider hardware tokens instead
- Document key management policy
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 5: Forensic Investigation                     ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
Law enforcement needs to access encrypted evidence files as part 
of an investigation with proper legal authorization.

🎯 Objective:
Crack passwords on evidence files legally.

🔧 Approach:
# Multiple file types from seized device
for f in *.pdf; do pdf2john "$f" >> all_hashes.txt; done
for f in *.zip; do zip2john "$f" >> all_hashes.txt; done
for f in *.docx; do office2john "$f" >> all_hashes.txt; done

# Comprehensive cracking
john --wordlist=rockyou.txt --rules=best64 --fork=8 all_hashes.txt

# Session management for long operation
john --session=evidence_case001 all_hashes.txt

📊 Results:
- 67% of files accessed within 48 hours
- Case-related documents recovered
- Chain of custody maintained
- Full documentation for court

⚠️ Notes:
- Legal authorization required
- Document all actions for chain of custody
- Secure handling of recovered data
```

---

## ⚠️ SECURITY BEST PRACTICES

### ✅ DO's - Ethical Password Cracking

| Practice | Description |
|----------|-------------|
| ✅ **Get Authorization** | Always have written permission before testing |
| ✅ **Use Test Systems** | Practice on your own systems or dedicated labs |
| ✅ **Secure Hashes** | Protect hash files as sensitive data |
| ✅ **Document Everything** | Keep detailed logs of all cracking activities |
| ✅ **Delete After Use** | Securely delete cracked passwords after reporting |
| ✅ **Report Properly** | Include methodology and remediation recommendations |
| ✅ **Respect Privacy** | Handle personal data according to regulations |
| ✅ **Use Strong Passwords** | Set example with your own password practices |
| ✅ **Educate Users** | Help improve organizational password policies |
| ✅ **Stay Legal** | Know and follow local laws and regulations |

### ❌ DON'Ts - What to Avoid

| Practice | Consequence |
|----------|-------------|
| ❌ **Crack Without Permission** | Criminal liability, prosecution |
| ❌ **Share Cracked Passwords** | Security breach, legal action |
| ❌ **Store Passwords Insecurely** | Data breach potential |
| ❌ **Use Production Systems** | Service disruption risk |
| ❌ **Ignore Password Policy** | Weak security posture |
| ❌ **Skip Documentation** | Lack of audit trail |
| ❌ **Exceed Scope** | Contract violation, legal issues |
| ❌ **Crack Personal Accounts** | Privacy violation, legal action |
| ❌ **Distribute Tools Improperly** | Legal liability |
| ❌ **Ignore Regulations** | GDPR/compliance violations |

### 🛡️ Defensive Recommendations

```bash
# For Organizations - Password Policy Recommendations:

# 1. Use strong hashing
# bcrypt with cost factor 12+
# Argon2id for new systems

# 2. Implement password policies
# Minimum 12 characters
# Complexity requirements
# No common passwords
# Regular rotation (controversial - consider NIST guidelines)

# 3. Use Multi-Factor Authentication
# Reduces impact of password compromise

# 4. Monitor for breaches
# Check against leaked password databases
# Implement breach notification

# 5. Use password managers
# Generate strong, unique passwords
# Reduce password reuse
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: John the Ripper Cracking Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      JOHN THE RIPPER WORKFLOW                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌──────────────┐     ┌──────────────┐     ┌──────────────┐            │
│  │   INPUT      │     │   CRACKING   │     │   OUTPUT     │            │
│  │              │     │              │     │              │            │
│  │ • Hash File  │     │ • Wordlist   │     │ • Cracked    │            │
│  │ • Wordlist   │────►│ • Rules      │────►│   Passwords  │            │
│  │ • Options    │     │ • Increment  │     │ • john.pot   │            │
│  └──────────────┘     │ • Multi-core │     └──────────────┘            │
│                       └──────────────┘                                   │
│                              │                                           │
│                              ▼                                           │
│                       ┌──────────────┐                                   │
│                       │    HASH      │                                   │
│                       │   DATABASE   │                                   │
│                       │   (Target)   │                                   │
│                       └──────────────┘                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Hash Extraction Tools Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    HASH EXTRACTION ECOSYSTEM                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                      PROTECTED FILES                             │    │
│  │  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐  ┌────────┐   │    │
│  │  │  ZIP   │  │  PDF   │  │ Office │  │  SSH   │  │  RAR   │   │    │
│  │  └────────┘  └────────┘  └────────┘  └────────┘  └────────┘   │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│         │            │           │           │           │              │
│         ▼            ▼           ▼           ▼           ▼              │
│  ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐           │
│  │ zip2john   │ │ pdf2john   │ │office2john │ │ ssh2john   │           │
│  └────────────┘ └────────────┘ └────────────┘ └────────────┘           │
│         │            │           │           │                          │
│         └────────────┴───────────┴───────────┘                          │
│                              │                                          │
│                              ▼                                          │
│                       ┌──────────────┐                                   │
│                       │  HASH FILE   │                                   │
│                       │  (.txt)      │                                   │
│                       └──────┬───────┘                                   │
│                              │                                          │
│                              ▼                                          │
│                       ┌──────────────┐                                   │
│                       │    JOHN      │                                   │
│                       │ THE RIPPER   │                                   │
│                       └──────────────┘                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Cracking Modes Comparison

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      JOHN CRACKING MODES                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────┐ │
│  │    SINGLE CRACK     │  │     WORDLIST        │  │   INCREMENTAL   │ │
│  │                     │  │                     │  │                 │ │
│  │ • Uses username     │  │ • Dictionary attack │  │ • Brute-force   │ │
│  │ • Fast              │  │ • Medium speed      │  │ • Very slow     │ │
│  │ • Low success rate  │  │ • High success rate │  │ • Guaranteed*   │ │
│  │                     │  │ • Needs wordlist    │  │ • Limited time  │ │
│  └─────────────────────┘  └─────────────────────┘  └─────────────────┘ │
│                                                                          │
│  Recommended Order: SINGLE → WORDLIST+RULES → INCREMENTAL              │
│                                                                          │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │                    RULES ENGINE                                   │   │
│  │  ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐         │   │
│  │  │ Case    │   │ Append  │   │ Prepend │   │ Leet    │         │   │
│  │  │ Change  │   │ Numbers │   │ Chars   │   │ Speak   │         │   │
│  │  └─────────┘   └─────────┘   └─────────┘   └─────────┘         │   │
│  │                                                                   │   │
│  │  password → Password, password1, 1password, p@ssw0rd            │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relation |
|---------|-------|----------|
| **Ch32** | Hydra Advanced | Online password cracking counterpart |
| **Ch31** | Hydra Password Cracking | Online password cracking basics |
| **Ch34** | SQLMap Basics | May extract password hashes from databases |
| **Ch35** | Metasploit Framework | Hash dumping during exploitation |
| **Ch49** | Brute Force Techniques | Theory behind password cracking |
| **Ch50** | Password Attacks | Comprehensive password attack overview |
| **Ch47** | Privilege Escalation | May involve hash extraction |

---

## 🏆 BONUS ADVANCED CONTENT

### Technique 1: Creating Custom Rules

Create sophisticated password mutation rules:

```bash
# Create custom rules file
cat > custom_rules.conf << 'EOF'
[List.Rules:CompanyRules]
# Add company-specific variations
# Append year
$[2][0][0-9][0-9]

# Prepend company initials
^Company

# Common substitutions
sa@ se3 si1 so0 ss$

# Capitalize and add number
c $[0-9]

# Reverse and add suffix
r $!
EOF

# Use custom rules
john --wordlist=rockyou.txt --rules=CompanyRules \
     --config=custom_rules.conf hash.txt
```

---

### Technique 2: Mask Attack Implementation

While John doesn't have native mask attack like Hashcat, you can simulate it:

```bash
# Generate password list with specific pattern
# Format: 4 uppercase letters + 2 digits + special char

# Using crunch
crunch 7 7 -t @@@@%%^ -l aaaaaa@ -o mask_list.txt
# @ = lowercase, , = uppercase, % = digit, ^ = special

# Or use maskprocessor if available
mp64 '?l?l?l?l?d?d?s' > mask_list.txt

# Then crack with generated list
john --wordlist=mask_list.txt hash.txt
```

---

### Technique 3: Distributed Cracking with John

Set up distributed cracking across multiple machines:

```bash
# Split hash file or wordlist across machines

# Method 1: Split wordlist
split -l 100000 rockyou.txt part_

# Machine 1
john --wordlist=part_aa --session=machine1 hash.txt

# Machine 2
john --wordlist=part_ab --session=machine2 hash.txt

# Method 2: Use MPI version of John (if compiled with MPI support)
mpirun -np 4 john --wordlist=rockyou.txt hash.txt

# Method 3: Share john.pot across instances
# Central storage for cracked passwords
john --wordlist=wordlist1.txt --pot=/shared/john.pot hash.txt
```

**Benefits:**
- Parallel processing
- Faster results
- Resource optimization

---

## 📝 CHAPTER SUMMARY CHECKLIST

### Core Concepts Mastered
- [ ] Understood offline vs online password cracking
- [ ] Learned hash identification techniques
- [ ] Mastered wordlist attacks
- [ ] Applied incremental brute-force mode
- [ ] Used rules for password mutations
- [ ] Configured session management

### Technical Skills Developed
- [ ] Hash extraction (zip2john, pdf2john, ssh2john)
- [ ] Linux password cracking with unshadow
- [ ] Multi-core processing with --fork
- [ ] Performance benchmarking
- [ ] Custom rule creation

### Practical Applications
- [ ] Document password recovery
- [ ] Security audit assistance
- [ ] Incident response support
- [ ] Forensic investigations

### Best Practices Adopted
- [ ] Always obtain authorization
- [ ] Secure hash file handling
- [ ] Document all activities
- [ ] Delete cracked passwords after reporting
- [ ] Follow legal and ethical guidelines

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always identify the hash type before cracking. Use `hash-identifier` or online tools like CrackStation's hash analyzer.

> 💡 **Pro Tip #2:** Start with `--show` to check if you've already cracked a hash - John saves everything in john.pot file!

> 💡 **Pro Tip #3:** Use `--fork=$(nproc)` to utilize all CPU cores. Multi-core cracking is significantly faster.

> 💡 **Pro Tip #4:** Create targeted wordlists with CeWL for web application testing - extract words directly from the target website.

> 💡 **Pro Tip #5:** Use `--rules=best64` for wordlist mutations. It applies 64 common password variations automatically.

> 💡 **Pro Tip #6:** For large hash files, use `--session=name` to save progress. Resume anytime with `--restore=name`.

> 💡 **Pro Tip #7:** `zip2john` and `pdf2john` are your best friends for file cracking. Always extract hashes first, then crack offline.

> 💡 **Pro Tip #8:** Check `~/.john/john.pot` for all cracked passwords - great for maintaining a personal knowledge base.

> 💡 **Pro Tip #9:** Use `--incremental=Digits` for PIN cracking - much faster than full character sets.

> 💡 **Pro Tip #10:** Combine multiple wordlists: `cat wordlist1.txt wordlist2.txt | sort -u > combined.txt` for better coverage.

---

## 🔥 REAL WORLD APPLICATIONS

### Password Audit Report Template

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD AUDIT REPORT                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ORGANIZATION: _________________________                                 │
│  AUDIT DATE: _________________________                                   │
│  AUDITOR: ___________________________                                    │
│                                                                          │
│  SUMMARY:                                                                │
│  ├── Total hashes collected: ________                                    │
│  ├── Successfully cracked: ________                                      │
│  ├── Crack rate: ________%                                              │
│  └── Time taken: ________                                                │
│                                                                          │
│  CRACKED PASSWORDS ANALYSIS:                                             │
│  ├── < 8 characters: ________%                                          │
│  ├── Dictionary words: ________%                                        │
│  ├── Common patterns: ________%                                         │
│  └── Weak complexity: ________%                                         │
│                                                                          │
│  RECOMMENDATIONS:                                                        │
│  ├── Minimum 12 character passwords                                     │
│  ├── Implement password complexity requirements                        │
│  ├── Enable multi-factor authentication                                │
│  └── Regular password audits                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Hash Extraction Workflow

```bash
#!/bin/bash
# Comprehensive Hash Extraction Script
# Usage: ./extract_hashes.sh target_directory

DIR=$1
OUTPUT_DIR="extracted_hashes"

mkdir -p $OUTPUT_DIR

echo "[*] Extracting hashes from $DIR"

# ZIP files
for f in $(find $DIR -name "*.zip"); do
    echo "[*] Processing: $f"
    zip2john "$f" >> "$OUTPUT_DIR/zip_hashes.txt"
done

# RAR files
for f in $(find $DIR -name "*.rar"); do
    echo "[*] Processing: $f"
    rar2john "$f" >> "$OUTPUT_DIR/rar_hashes.txt"
done

# PDF files
for f in $(find $DIR -name "*.pdf"); do
    echo "[*] Processing: $f"
    pdf2john "$f" >> "$OUTPUT_DIR/pdf_hashes.txt"
done

# Office documents
for f in $(find $DIR -name "*.doc*" -o -name "*.xls*" -o -name "*.ppt*"); do
    echo "[*] Processing: $f"
    office2john "$f" >> "$OUTPUT_DIR/office_hashes.txt"
done

# 7z archives
for f in $(find $DIR -name "*.7z"); do
    echo "[*] Processing: $f"
    7z2john "$f" >> "$OUTPUT_DIR/7z_hashes.txt"
done

echo "[!] Hash extraction complete. Output in $OUTPUT_DIR/"
```

---

## ⚡ QUICK REFERENCE CARD

### John the Ripper Commands

| Task | Command |
|------|---------|
| **Basic Crack** | `john hashes.txt` |
| **Wordlist Attack** | `john --wordlist=rockyou.txt hashes.txt` |
| **Show Results** | `john --show hashes.txt` |
| **Identify Hash** | `john --list=formats` |
| **Incremental Attack** | `john --incremental hashes.txt` |
| **With Rules** | `john --wordlist=list.txt --rules hashes.txt` |
| **Multi-core** | `john --fork=4 hashes.txt` |
| **Save Session** | `john --session=myattack hashes.txt` |
| **Restore Session** | `john --restore=myattack` |
| **Benchmark** | `john --test` |

### Hash Extraction Tools

| Tool | Extracts From |
|------|---------------|
| `zip2john` | ZIP archives |
| `rar2john` | RAR archives |
| `pdf2john` | PDF files |
| `office2john` | MS Office docs |
| `ssh2john` | SSH private keys |
| `7z2john` | 7z archives |
| `keepass2john` | KeePass databases |
| `unshadow` | Linux passwd+shadow |

### Hash Types Quick Reference

| Hash | Length | Format Example |
|------|--------|----------------|
| MD5 | 32 chars | `5f4dcc3b5aa7...` |
| SHA1 | 40 chars | `5baa61e4c9b0...` |
| SHA256 | 64 chars | `5e884898da28...` |
| SHA512 | 128 chars | `b109f3bbbc24...` |
| bcrypt | 60 chars | `$2a$10$N9qo8u...` |
| NTLM | 32 chars | `8846F7EAEE8F...` |
| MySQL | 41 chars | `*A4B6157319...` |

---

## 🏆 BONUS: ADVANCED EXPLOITATION

### Custom Rule Configuration

```bash
# Create custom rules file
cat > ~/.john/custom_rules.conf << 'EOF'
[List.Rules:CustomStrong]
# Add numbers at end
$[0-9]
# Add symbols at end
$[!@#$%^&*()]
# Capitalize first letter
c
# Leet speak conversions
sa@ se3 si1 so0 ss$
# Add year suffixes
$[0-9]$[0-9]$[0-9]$[0-9]
# Reverse the word
r
# Double the word
d
EOF

# Use custom rules
john --wordlist=rockyou.txt --rules=CustomStrong --config=~/.john/custom_rules.conf hashes.txt
```

### Automated Cracking Pipeline

```bash
#!/bin/bash
# Advanced John Pipeline

HASH_FILE=$1
WORDLISTS=("rockyou.txt" "top1000.txt" "common.txt")
OUTPUT_DIR="cracking_results"

mkdir -p $OUTPUT_DIR

echo "[*] Starting Advanced Cracking Pipeline"

# Phase 1: Quick single mode
echo "[*] Phase 1: Single Mode"
john --single --session=single "$HASH_FILE"

# Phase 2: Dictionary attacks
for wl in "${WORDLISTS[@]}"; do
    echo "[*] Phase: Wordlist $wl"
    john --wordlist="$wl" --session="dict_$wl" --rules=best64 "$HASH_FILE"
done

# Phase 3: Show results
echo "[!] Results:"
john --show "$HASH_FILE"

echo "[!] Pipeline complete!"
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### Key Concepts Mastered

- ✅ **Hash Fundamentals**: Understanding password hashing, one-way functions, and collision resistance
- ✅ **Hash Types**: MD5, SHA family, bcrypt, NTLM, and 400+ supported formats
- ✅ **John Architecture**: Single mode, wordlist mode, incremental mode, rules
- ✅ **Hash Extraction**: zip2john, pdf2john, office2john, and other extraction tools
- ✅ **Session Management**: Saving and resuming cracking sessions
- ✅ **Performance Optimization**: Multi-core cracking, GPU acceleration concepts
- ✅ **Custom Rules**: Creating password mutation rules

### Key Takeaways

1. **Hashes Can't Be Reversed**: Hashing is one-way; cracking requires comparing hash outputs
2. **Wordlist Quality Matters**: Better wordlists = faster cracking
3. **Rules Multiply Effectiveness**: One wordlist with rules = thousands of variations
4. **Session Management Essential**: Long attacks need save/resume capability
5. **Multi-core Speedup**: Use `--fork` for parallel processing

---

## 🛡️ DEFENSIVE SECURITY: Password Security

### Password Hardening Guide

```bash
# Password Policy Configuration (Linux)
sudo nano /etc/security/pwquality.conf

# Recommended settings:
minlen = 14
minclass = 4
dcredit = -1
ucredit = -1
lcredit = -1
ocredit = -1
maxrepeat = 2
maxsequence = 3

# Enable password aging
sudo chage -M 90 username

# Check password strength
echo "password123" | pwscore
```

### Password Security Checklist

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD SECURITY CHECKLIST                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  FOR USERS:                                                             │
│  ├── Use unique passwords for each account                              │
│  ├── Minimum 12 characters                                              │
│  ├── Mix uppercase, lowercase, numbers, symbols                        │
│  ├── Use password manager                                               │
│  ├── Enable 2FA everywhere                                              │
│  └── Never share passwords                                              │
│                                                                          │
│  FOR ADMINISTRATORS:                                                    │
│  ├── Enforce strong password policies                                   │
│  ├── Implement account lockout                                          │
│  ├── Regular password audits                                            │
│  ├── Monitor for breached passwords                                     │
│  ├── Use bcrypt or Argon2 for hashing                                  │
│  ├── Implement salting                                                 │
│  └── Educate users on security                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 METHODOLOGY: Hash Cracking Workflow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    HASH CRACKING METHODOLOGY                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  STEP 1: HASH COLLECTION                                                │
│  ─────────────────────────                                              │
│  □ Obtain hash file (authorized only!)                                  │
│  □ Document hash source and type                                        │
│  □ Verify hash integrity                                                │
│                                                                          │
│  STEP 2: HASH IDENTIFICATION                                           │
│  ─────────────────────────────                                          │
│  □ Analyze hash length                                                  │
│  □ Check hash format markers ($, etc.)                                 │
│  □ Use hash-identifier tools                                            │
│  □ Confirm with John format list                                       │
│                                                                          │
│  STEP 3: CRACKING STRATEGY                                              │
│  ─────────────────────────                                              │
│  □ Start with single mode                                               │
│  □ Try common wordlists                                                 │
│  □ Apply rules for variations                                           │
│  □ Use incremental if needed                                            │
│                                                                          │
│  STEP 4: EXECUTION                                                      │
│  ─────────────                                                          │
│  □ Configure session for resume                                         │
│  □ Enable multi-core processing                                         │
│  □ Monitor progress                                                     │
│  □ Document timeline                                                    │
│                                                                          │
│  STEP 5: DOCUMENTATION                                                  │
│  ─────────────────                                                      │
│  □ Record cracked passwords                                             │
│  □ Analyze patterns                                                     │
│  □ Generate security report                                             │
│  □ Recommend improvements                                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ⚠️ LEGAL & ETHICS

### Authorization Requirements for Hash Cracking

```
HASH CRACKING AUTHORIZATION
===========================

This document authorizes password hash cracking for security testing.

CLIENT: _________________________
SYSTEM: _________________________
HASH SOURCE: ____________________
TESTER: _________________________

AUTHORIZED ACTIVITIES:
□ Hash extraction from authorized files
□ Offline password cracking
□ Password strength analysis
□ Security report generation

LIMITATIONS:
- Hashes must be from authorized systems only
- Cracked passwords must be securely stored
- Results must be reported to client only
- All test data must be deleted after engagement

LEGAL ACKNOWLEDGMENT:
I understand unauthorized hash cracking is illegal under IT Act 2000 Section 66.

CLIENT SIGNATURE: _________________ DATE: ________
TESTER SIGNATURE: _________________ DATE: ________
```

---

## 🔗 RELATED CHAPTERS

### Prerequisites
- **Chapter 30**: Security Tools Overview
- **Chapter 31-32**: Hydra (Online password cracking)

### Related Chapters
| Chapter | Title | Relationship |
|---------|-------|--------------|
| **31** | Hydra Basics | Online vs Offline cracking |
| **32** | Hydra Advanced | Complementary tools |
| **34** | SQLMap Basics | Database password extraction |
| **35** | Metasploit Framework | Post-exploitation hash dumping |

---

## 🎮 INTERACTIVE QUIZ

**Q1: What is the main difference between John and Hydra?**
- A) John is faster
- B) John cracks offline hashes, Hydra attacks online services
- C) John is newer
- D) No difference

**Q2: Which command shows already cracked passwords?**
- A) `john --results hashes.txt`
- B) `john --show hashes.txt`
- C) `john --display hashes.txt`
- D) `john --found hashes.txt`

**Q3: What does zip2john do?**
- A) Cracks ZIP files
- B) Extracts password hash from ZIP files
- C) Creates ZIP files
- D) Repairs ZIP files

**Q4: Which mode tries all possible combinations?**
- A) Wordlist mode
- B) Single mode
- C) Incremental mode
- D) Rules mode

**Q5: How do you enable multi-core cracking?**
- A) `john --multi hashes.txt`
- B) `john --fork=4 hashes.txt`
- C) `john --parallel hashes.txt`
- D) `john --cores=4 hashes.txt`

**Q6: What is bcrypt identified by?**
- A) 32 character string
- B) $2a$, $2b$, or $2y$ prefix
- C) SHA prefix
- D) MD5 prefix

**Q7: Which file stores all cracked passwords?**
- A) `john.log`
- B) `john.pot`
- C) `john.out`
- D) `john.cache`

**Q8: What does --rules=best64 do?**
- A) Uses 64 threads
- B) Applies 64 common password variations
- C) Limits to 64 passwords
- D) Creates 64 wordlists

**Q9: How do you resume a saved session?**
- A) `john --resume=session_name`
- B) `john --restore=session_name`
- C) `john --continue=session_name`
- D) Both A and B work

**Q10: What is the purpose of salting?**
- A) Make passwords tasty
- B) Add randomness to prevent rainbow table attacks
- C) Speed up cracking
- D) Compress passwords

**Q11: Which tool extracts hashes from PDF files?**
- A) `pdfcrack`
- B) `pdf2john`
- C) `pdftocrack`
- D) `john-pdf`

**Q12: What is the minimum recommended password length today?**
- A) 6 characters
- B) 8 characters
- C) 12 characters
- D) 4 characters

<details>
<summary>📝 Click to Reveal Answers</summary>

1. **B** - John cracks offline hashes, Hydra attacks online services
2. **B** - `john --show hashes.txt`
3. **B** - Extracts password hash from ZIP files
4. **C** - Incremental mode
5. **B** - `john --fork=4 hashes.txt`
6. **B** - $2a$, $2b$, or $2y$ prefix
7. **B** - `john.pot`
8. **B** - Applies 64 common password variations
9. **D** - Both A and B work
10. **B** - Add randomness to prevent rainbow table attacks
11. **B** - `pdf2john`
12. **C** - 12 characters

</details>

---

## 🎯 ETHICAL HACKING CHALLENGES

### Challenge 1: Hash Identification
- [ ] Download sample hash files
- [ ] Identify hash types by length and format
- [ ] Use `john --list=formats` to verify
- [ ] Document findings

### Challenge 2: ZIP File Cracking
- [ ] Create password-protected ZIP file
- [ ] Extract hash with zip2john
- [ ] Crack with John using wordlist
- [ ] Verify password works

### Challenge 3: Session Management
- [ ] Start a cracking session
- [ ] Save with `--session=name`
- [ ] Interrupt and restore
- [ ] Verify continuation point

### Challenge 4: Custom Rules
- [ ] Create custom rules file
- [ ] Apply to wordlist attack
- [ ] Compare success rate vs no rules
- [ ] Document improvements

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

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

### John the Ripper Assessment

<details>
<summary><b>❓ Q1: What is the difference between online and offline password cracking?</b></summary>

**Answer:**
- **Online (Hydra):** Tests credentials against live services, subject to rate limiting
- **Offline (John):** Works on captured hashes locally, limited only by computing power

John the Ripper is an offline cracker - it needs the hash file first.
</details>

<details>
<summary><b>❓ Q2: How do you identify an MD5 hash?</b></summary>

**Answer:**
- Length: 32 hexadecimal characters
- No prefix (unlike bcrypt with $2a$)
- Example: `5d41402abc4b2a76b9719d911017c592`

Use `john --list=formats | grep -i md5` to see MD5 variants.
</details>

<details>
<summary><b>❓ Q3: What is the purpose of zip2john?</b></summary>

**Answer:**
`zip2john` extracts the password hash from a ZIP archive so John can crack it.

```bash
zip2john protected.zip > hash.txt
john hash.txt
```
</details>

<details>
<summary><b>❓ Q4: What's the difference between wordlist and incremental mode?</b></summary>

**Answer:**
- **Wordlist Mode:** Uses a dictionary file of common passwords
  - `john --wordlist=rockyou.txt hash.txt`
- **Incremental Mode:** Brute-force all possible combinations
  - `john --incremental hash.txt` (slow but thorough)
</details>

<details>
<summary><b>❓ Q5: How do you resume a John session?</b></summary>

**Answer:**
```bash
# John auto-saves sessions
john --restore

# Or specific session
john --restore=session_name
```
</details>

<details>
<summary><b>❓ Q6: What is the john.pot file?</b></summary>

**Answer:**
The `john.pot` file stores all cracked passwords. Located at `~/.john/john.pot`

View cracked passwords:
```bash
john --show hash.txt
cat ~/.john/john.pot
```
</details>

<details>
<summary><b>❓ Q7: How do you use custom rules in John?</b></summary>

**Answer:**
```bash
# Create rules in john.conf
[List.Rules:MyRule]
$[0-9]      # Add numbers at end
c           # Capitalize first letter

# Apply rules
john --wordlist=list.txt --rules=MyRule hash.txt
```
</details>

<details>
<summary><b>❓ Q8: What is unshadow and when do you use it?</b></summary>

**Answer:**
`unshadow` combines `/etc/passwd` and `/etc/shadow` files for Linux password cracking.

```bash
unshadow /etc/passwd /etc/shadow > my_hashes.txt
john my_hashes.txt
```
Requires root access on target system.
</details>

<details>
<summary><b>❓ Q9: How do you crack a bcrypt hash?</b></summary>

**Answer:**
```bash
# Bcrypt is slow - use targeted wordlist
john --format=bcrypt --wordlist=rockyou.txt hash.txt

# Check format
john --list=formats | grep bcrypt
```
Note: bcrypt is designed to be slow - can take hours/days for strong passwords.
</details>

<details>
<summary><b>❓ Q10: What's the difference between single and wordlist mode?</b></summary>

**Answer:**
- **Single Mode:** Uses username/GECOS info for guesses (fastest for simple passwords)
- **Wordlist Mode:** Uses dictionary file (most common approach)

```bash
john --single hash.txt      # Single mode
john --wordlist=list.txt hash.txt  # Wordlist mode
```
</details>

<details>
<summary><b>❓ Q11: How do you crack SSH private key passwords?</b></summary>

**Answer:**
```bash
# Extract hash from SSH key
ssh2john id_rsa > ssh_hash.txt

# Crack with John
john --wordlist=rockyou.txt ssh_hash.txt
```
</details>

<details>
<summary><b>❓ Q12: What are the most common hash extraction tools?</b></summary>

**Answer:**
- `zip2john` - ZIP archives
- `rar2john` - RAR archives
- `pdf2john` - PDF files
- `office2john` - MS Office documents
- `ssh2john` - SSH private keys
- `keepass2john` - KeePass databases
- `7z2john` - 7z archives
</details>

<details>
<summary><b>❓ Q13: How do you check John's progress while running?</b></summary>

**Answer:**
```bash
# Press any key during running session for status

# Or check session file
cat ~/.john/john.log

# Show cracked passwords
john --show hash.txt
```
</details>

<details>
<summary><b>❓ Q14: What's the best approach for cracking strong hashes?</b></summary>

**Answer:**
1. Start with common wordlists (rockyou.txt)
2. Apply rules for variations
3. Use targeted wordlists if you know the target
4. Consider GPU-based tools (Hashcat) for speed
5. Accept that some passwords won't crack in reasonable time

```bash
john --wordlist=rockyou.txt --rules=best64 hash.txt
```
</details>

<details>
<summary><b>❓ Q15: How do you specify the hash format manually?</b></summary>

**Answer:**
```bash
# Auto-detect (default)
john hash.txt

# Specify format
john --format=raw-md5 hash.txt
john --format=bcrypt hash.txt
john --format=sha512crypt hash.txt

# List all formats
john --list=formats
```
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Q1: Explain the difference between hashing and encryption.
<details>
<summary>📋 Click for Answer</summary>

**Hashing:**
- One-way function (cannot be reversed)
- Fixed output size regardless of input
- Same input = same output
- Used for password storage, integrity verification
- Examples: MD5, SHA-256, bcrypt

**Encryption:**
- Two-way function (can be decrypted with key)
- Variable output size
- Requires key for encryption/decryption
- Used for data confidentiality
- Examples: AES, RSA

**Why passwords use hashing:**
- If database is breached, attacker can't reverse hashes
- Even administrators can't see original passwords
- Verification: hash(input) == stored_hash
</details>

### Q2: Why is bcrypt more secure than MD5 for passwords?
<details>
<summary>📋 Click for Answer</summary>

**MD5 Weaknesses:**
- Extremely fast (billions of hashes/second on GPU)
- Designed for speed, not security
- Vulnerable to rainbow tables
- No salt by default
- Collision vulnerabilities found

**bcrypt Advantages:**
- Intentionally slow (designed for passwords)
- Built-in salt (unique per password)
- Cost factor adjustable (scales with hardware)
- Resistant to rainbow tables
- No known cryptographic weaknesses

**Performance comparison:**
- MD5: ~10 billion hashes/second (GPU)
- bcrypt: ~10,000 hashes/second (GPU)

**Time to crack 8-char password:**
- MD5: Minutes to hours
- bcrypt: Months to years
</details>

### Q3: What is a salt and why is it important?
<details>
<summary>📋 Click for Answer</summary>

**Salt:**
- Random data added to password before hashing
- Unique per password
- Stored alongside the hash

**Purpose:**
1. Prevents rainbow table attacks
2. Makes identical passwords have different hashes
3. Forces attacker to crack each hash individually

**Example:**
```
Password: "password123"
Salt: "x7kL9mN2"
Hash input: "password123x7kL9mN2"
Stored: $bcrypt$salt$hash
```

**Without salt:**
- Same password = same hash
- Pre-computed tables work
- Crack once, crack all

**With salt:**
- Each hash unique
- Must crack individually
- Rainbow tables useless
</details>

### Q4: How would you design a secure password storage system?
<details>
<summary>📋 Click for Answer</summary>

**Modern Password Storage:**

1. **Algorithm Selection:**
   - Primary: Argon2 (winner of PHC)
   - Alternative: bcrypt, scrypt
   - Never: MD5, SHA1, plain SHA-256

2. **Configuration:**
```python
# Python example with bcrypt
import bcrypt

# Generate salt and hash
password = b"user_password"
salt = bcrypt.gensalt(rounds=12)  # Cost factor
hashed = bcrypt.hashpw(password, salt)

# Verify
bcrypt.checkpw(password, hashed)
```

3. **Best Practices:**
   - Use unique salt per password
   - High enough cost factor (adjust over time)
   - Never log or cache passwords
   - Implement password strength requirements
   - Use pepper (server-side secret) for extra security

4. **Migration Strategy:**
   - Support multiple hash algorithms
   - Upgrade on next login
   - Track algorithm version
</details>

### Q5: What is the difference between John the Ripper and Hashcat?
<details>
<summary>📋 Click for Answer</summary>

| Feature | John the Ripper | Hashcat |
|---------|-----------------|---------|
| **Type** | CPU-focused | GPU-focused |
| **Speed** | Slower | Much faster |
| **Ease of Use** | Simpler | More complex |
| **Formats** | 400+ | 300+ |
| **GPU Support** | Limited | Native |
| **Rules** | Built-in | Requires setup |
| **Free Version** | Open source | Free version available |

**When to use John:**
- CPU-only environment
- Quick cracking tasks
- Learning/educational purposes
- Mobile devices (Termux)

**When to use Hashcat:**
- GPU available
- Large-scale cracking
- Performance-critical work
- Modern hash algorithms

**Speed comparison (bcrypt):**
- John (CPU): ~10,000 H/s
- Hashcat (GPU): ~50,000 H/s
</details>

### Q6: How do you perform a password audit for an organization?
<details>
<summary>📋 Click for Answer</summary>

**Password Audit Process:**

1. **Authorization:**
   - Written permission required
   - Define scope and timeline
   - Incident response plan

2. **Hash Extraction:**
```bash
# Linux
unshadow /etc/passwd /etc/shadow > hashes.txt

# Windows (need SAM and SYSTEM)
samdump2 SYSTEM SAM > hashes.txt

# Active Directory
ntdsutil "ac i ntds" "sn" ...
```

3. **Analysis:**
```bash
# Identify hash types
john --list=formats

# Quick win with common passwords
john --wordlist=common.txt hashes.txt

# Full audit with rules
john --wordlist=rockyou.txt --rules=best64 hashes.txt
```

4. **Reporting:**
   - Statistics (% cracked)
   - Weak password examples (sanitized)
   - Policy recommendations
   - Remediation timeline

5. **Remediation:**
   - Force password reset for cracked accounts
   - Implement stronger policies
   - Deploy MFA
</details>

### Q7: What are rainbow tables and how do salts defeat them?
<details>
<summary>📋 Click for Answer</summary>

**Rainbow Tables:**
- Pre-computed tables of hash chains
- Trade storage for computation time
- Allow instant lookup of passwords

**How they work:**
1. Generate chains: hash → reduce → hash → reduce...
2. Store only start and end points
3. To crack: regenerate chains, find match

**Limitations:**
- Huge storage requirements (terabytes for complex passwords)
- Only work for unsalted hashes
- Time-space trade-off

**How salt defeats rainbow tables:**
```
Without salt:
hash("password123") = always same result
Rainbow table: lookup result → password

With salt:
hash("password123" + "abc") = result1
hash("password123" + "xyz") = result2
Rainbow table would need: all salts × all passwords
```

**Impact:**
- 10-character password with 8-byte salt
- Rainbow table size: impractical (petabytes)
</details>

### Q8: Explain the concept of password entropy.
<details>
<summary>📋 Click for Answer</summary>

**Password Entropy:**
- Measure of password randomness
- Measured in bits
- Higher = harder to crack

**Formula:**
```
Entropy = log2(charset^length)

Where:
- charset: possible characters
- length: password length
```

**Examples:**
```
8-char lowercase: log2(26^8) = 37.6 bits
8-char mixed case: log2(52^8) = 45.6 bits
8-char alphanumeric: log2(62^8) = 47.6 bits
8-char full ASCII: log2(95^8) = 52.6 bits
```

**Cracking Time Estimation:**
```
Time = 2^(entropy - 1) / hash_rate

Example:
Entropy = 40 bits
Rate = 10 billion/sec (GPU MD5)
Time = 2^39 / 10^10 = ~55 seconds

Entropy = 60 bits
Time = 2^59 / 10^10 = ~18 years
```

**Recommendations:**
- Minimum 50 bits for general accounts
- 60+ bits for sensitive accounts
- 80+ bits for cryptographic keys
</details>

### Q9: How do you handle large-scale hash cracking?
<details>
<summary>📋 Click for Answer</summary>

**Strategies for Large Datasets:**

1. **Prioritization:**
```bash
# Crack admin accounts first
john --users=admin*,root* hashes.txt

# High-value hash types first
john --format=nt hashes.txt  # Fast to crack
```

2. **Distributed Cracking:**
```bash
# Split wordlist
split -l 100000 rockyou.txt part_

# Run on multiple machines
# Machine 1
john --wordlist=part_aa hashes.txt
# Machine 2
john --wordlist=part_ab hashes.txt
```

3. **Progressive Approach:**
```bash
# Stage 1: Quick wins
john --wordlist=top1000.txt hashes.txt

# Stage 2: Common passwords
john --wordlist=rockyou.txt hashes.txt

# Stage 3: Rules
john --wordlist=rockyou.txt --rules hashes.txt

# Stage 4: Incremental (limited)
john --incremental=Lower --max-length=6 hashes.txt
```

4. **Efficiency Tips:**
- Remove already-cracked hashes
- Use appropriate formats
- Balance speed vs. thoroughness
- Document all attempts
</details>

### Q10: What is a password policy and how do you enforce it?
<details>
<summary>📋 Click for Answer</summary>

**Password Policy Elements:**

1. **Complexity Requirements:**
   - Minimum length (12+ characters)
   - Mix of upper/lower case
   - Include numbers
   - Include special characters
   - No dictionary words

2. **History Requirements:**
   - Remember last N passwords
   - Prevent reuse
   - Minimum age before change

3. **Expiration:**
   - Maximum age (90 days recommended)
   - Warning period
   - Grace logins

4. **Account Lockout:**
   - Failed attempts threshold
   - Lockout duration
   - Unlock procedure

**Implementation:**
```bash
# Linux PAM configuration
password requisite pam_pwquality.so try_first_pass \
  retry=3 minlen=12 ucredit=-1 lcredit=-1 \
  dcredit=-1 ocredit=-1

# Active Directory GPO
Password Policy Settings:
- Minimum password length: 12
- Password must meet complexity: Enabled
- Maximum password age: 90 days
- Enforce password history: 24
- Account lockout threshold: 5
```

**Modern Alternatives:**
- Passwordless authentication
- Biometric authentication
- FIDO2/WebAuthn
- Certificate-based authentication
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Enterprise Password Audit
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    ENTERPRISE PASSWORD AUDIT                                ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  SITUATION:                                                                 ║
║  Company needs to audit 5000+ employee passwords from Active Directory.    ║
║                                                                            ║
║  APPROACH:                                                                  ║
║  1. Extract NTLM hashes from AD database                                   ║
║  2. Use targeted wordlist with company terms                               ║
║  3. Apply rules for common variations                                      ║
║  4. Generate comprehensive report                                          ║
║                                                                            ║
║  COMMANDS:                                                                  ║
║  # Extract hashes (requires Domain Admin)                                  ║
║  impacket-secretsdump domain/user:pass@dc.domain.local                     ║
║                                                                             ║
║  # Quick audit                                                              ║
║  john --format=NT --wordlist=rockyou.txt ad_hashes.txt                     ║
║                                                                             ║
║  # Targeted with company names                                             ║
║  john --format=NT --wordlist=company.txt --rules ad_hashes.txt             ║
║                                                                            ║
║  RESULTS:                                                                   ║
║  • 15% cracked with top 1000 passwords                                     ║
║  • 35% cracked with rockyou.txt                                            ║
║  • 45% cracked with rules                                                  ║
║  • Recommended: Password policy update + MFA                               ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: Forensic Investigation
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                      FORENSIC INVESTIGATION                                 ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  SITUATION:                                                                 ║
║  Investigating a former employee's encrypted documents for legal case.     ║
║                                                                            ║
║  EVIDENCE:                                                                  ║
║  • Password-protected ZIP files                                            ║
║  • Encrypted PDF documents                                                 ║
║  • Password-protected Office files                                         ║
║                                                                            ║
║  PROCESS:                                                                   ║
║  # Extract all hashes                                                       ║
║  zip2john documents.zip > zip_hash.txt                                     ║
║  pdf2john report.pdf > pdf_hash.txt                                        ║
║  office2john spreadsheet.xlsx > office_hash.txt                           ║
║                                                                             ║
║  # Create targeted wordlist from employee info                             ║
║  echo -e "employee_name\ncompany_name\nbirth_date\npet_name" > target.txt  ║
║                                                                             ║
║  # Crack with rules                                                         ║
║  john --wordlist=target.txt --rules=all zip_hash.txt                       ║
║                                                                            ║
║  OUTCOME:                                                                   ║
║  • ZIP password: Company2023!                                              ║
║  • Found incriminating documents                                           ║
║  • Evidence preserved for court                                            ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: Incident Response
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                       INCIDENT RESPONSE                                     ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  SITUATION:                                                                 ║
║  Breach detected. Attacker accessed password database. Need to identify    ║
║  which accounts are at risk.                                               ║
║                                                                            ║
║  IMMEDIATE ACTIONS:                                                         ║
║  1. Isolate affected systems                                               ║
║  2. Preserve evidence                                                      ║
║  3. Extract and analyze hashes                                             ║
║                                                                            ║
║  ANALYSIS:                                                                  ║
║  # Identify hash types                                                      ║
║  head -5 leaked_hashes.txt                                                  ║
║  # Result: SHA-256 with salt                                               ║
║                                                                             ║
║  # Quick assessment                                                         ║
║  john --format=sha256crypt --wordlist=top100.txt leaked_hashes.txt         ║
║                                                                             ║
║  # Full analysis                                                            ║
║  john --format=sha256crypt --wordlist=rockyou.txt leaked_hashes.txt        ║
║                                                                             ║
║  FINDINGS:                                                                  ║
║  • 12% passwords cracked quickly                                           ║
║  • Common passwords: password123, summer2024                               ║
║  • Password policy was not enforced                                        ║
║                                                                            ║
║  REMEDIATION:                                                               ║
║  • Force password reset for all users                                      ║
║  • Implement password policy                                               ║
║  • Deploy MFA immediately                                                  ║
║  • Monitor for credential stuffing                                        ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: Penetration Test Deliverable
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                   PENETRATION TEST DELIVERABLE                              ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  ENGAGEMENT:                                                                ║
║  Password strength assessment as part of security audit.                   ║
║                                                                            ║
║  SCOPE:                                                                     ║
║  • Linux server passwords (100 accounts)                                   ║
║  • Application database hashes (500 users)                                 ║
║                                                                            ║
║  METHODOLOGY:                                                               ║
║  # Linux passwords                                                          ║
║  unshadow passwd shadow > linux_hashes.txt                                 ║
║  john --wordlist=rockyou.txt --rules linux_hashes.txt                      ║
║                                                                             ║
║  # Application hashes (MD5)                                                ║
║  john --format=raw-md5 --wordlist=rockyou.txt app_hashes.txt               ║
║                                                                             ║
║  REPORT METRICS:                                                            ║
║  ┌────────────────────┬───────────┬───────────┐                             ║
║  │ System             │ Total     │ Cracked   │                             ║
║  ├────────────────────┼───────────┼───────────┤                             ║
║  │ Linux (SHA-512)    │ 100       │ 23 (23%)  │                             ║
║  │ Application (MD5)  │ 500       │ 287 (57%) │                             ║
║  └────────────────────┴───────────┴───────────┘                             ║
║                                                                            ║
║  RECOMMENDATIONS:                                                           ║
║  1. Upgrade application to bcrypt                                          ║
║  2. Enforce minimum 12-character passwords                                 ║
║  3. Implement password complexity rules                                    ║
║  4. Deploy MFA for all systems                                             ║
║  5. Regular password audits                                                ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: Personal Password Recovery
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    PERSONAL PASSWORD RECOVERY                               ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  SITUATION:                                                                 ║
║  User forgot password to important personal ZIP archive.                   ║
║                                                                            ║
║  APPROACH:                                                                  ║
║  1. Extract hash from ZIP                                                  ║
║  2. Create targeted wordlist based on user's typical passwords             ║
║  3. Use rules for variations                                               ║
║                                                                            ║
║  USER KNOWLEDGE:                                                            ║
║  • Usually uses pet names                                                  ║
║  • Often adds birth year                                                   ║
║  • Likes to capitalize first letter                                        ║
║                                                                            ║
║  CUSTOM WORDLIST:                                                           ║
║  echo -e "fluffy\nspot\nwhiskers\nbuddy\nmax" > pets.txt                   ║
║                                                                             ║
║  CUSTOM RULES:                                                              ║
║  [List.Rules:Personal]                                                      ║
║  c $[0-9][0-9][0-9][0-9]                                                    ║
║                                                                             ║
║  CRACKING:                                                                  ║
║  zip2john backup.zip > hash.txt                                            ║
║  john --wordlist=pets.txt --rules=Personal hash.txt                        ║
║                                                                             ║
║  RESULT:                                                                    ║
║  Password found: Fluffy2020                                                ║
║  Time: 2 seconds                                                           ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

---

## ⚠️ SECURITY BEST PRACTICES

### ✅ DO's - Ethical Password Cracking

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         SECURITY DO's                                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ✅ ALWAYS have proper authorization before cracking any hashes             │
│  ✅ WORK only with hashes you own or have permission to test                │
│  ✅ USE isolated test environments for learning                             │
│  ✅ DOCUMENT all activities for audit trail                                 │
│  ✅ SECURE cracked password information                                     │
│  ✅ DELETE test data after completing engagement                            │
│  ✅ REPORT findings responsibly to stakeholders                             │
│  ✅ FOLLOW your organization's security policies                             │
│  ✅ OBTAIN written permission for security assessments                       │
│  ✅ RESPECT privacy and confidentiality                                     │
│                                                                              │
│  BEST PRACTICE: Always err on the side of caution                           │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### ❌ DON'Ts - Avoid These Mistakes

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         SECURITY DON'Ts                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ❌ NEVER crack hashes you don't own or have authorization for              │
│  ❌ NEVER share cracked passwords publicly                                  │
│  ❌ NEVER use cracked passwords to access systems unauthorized              │
│  ❌ NEVER store cracked passwords in insecure locations                     │
│  ❌ NEVER attempt to crack government or financial institution hashes       │
│  ❌ NEVER use skills for malicious purposes                                 │
│  ❌ NEVER ignore legal boundaries                                           │
│  ❌ NEVER crack passwords for revenge or harassment                         │
│  ❌ NEVER use breached password databases illegally                         │
│  ❌ NEVER forget that these are real people's accounts                      │
│                                                                              │
│  WARNING: Unauthorized password cracking is a serious crime with            │
│           potential for significant prison time                             │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 🔒 Legal Compliance for Password Cracking

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    LEGAL COMPLIANCE CHECKLIST                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  Authorized Scenarios:                                                       │
│  ☐ Security assessment contract signed                                      │
│  ☐ Internal security audit approved                                         │
│  ☐ Own personal data recovery                                               │
│  ☐ Academic research with proper approvals                                  │
│  ☐ Bug bounty program participation                                        │
│  ☐ Law enforcement with warrant                                             │
│                                                                              │
│  Required Documentation:                                                     │
│  ☐ Rules of Engagement (RoE)                                                │
│  ☐ Scope of work defined                                                    │
│  ☐ Data handling procedures                                                 │
│  ☐ Incident response plan                                                   │
│  ☐ Non-disclosure agreement                                                 │
│                                                                              │
│  Data Protection:                                                            │
│  ☐ Encrypted storage of sensitive data                                      │
│  ☐ Secure deletion after engagement                                         │
│  ☐ Access logging and auditing                                              │
│  ☐ Minimal data collection principle                                        │
│                                                                              │
│  Legal Considerations:                                                       │
│  ☐ Computer Fraud and Abuse Act (CFAA) - US                                 │
│  ☐ Computer Misuse Act - UK                                                 │
│  ☐ IT Act Section 66 - India                                                │
│  ☐ GDPR - EU (data protection)                                              │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: John the Ripper Attack Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      JOHN THE RIPPER ATTACK FLOW                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   INPUT SOURCES                                                              │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                     │
│   │  Hash File   │  │ Shadow File  │  │ Extracted    │                     │
│   │  (hash.txt)  │  │ (unshadow)   │  │ Hash (2john) │                     │
│   └──────┬───────┘  └──────┬───────┘  └──────┬───────┘                     │
│          │                 │                 │                              │
│          └─────────────────┼─────────────────┘                              │
│                            ▼                                                 │
│   ┌──────────────────────────────────────────────────────────────────────┐  │
│   │                        JOHN THE RIPPER                               │  │
│   │  ┌────────────────────────────────────────────────────────────────┐ │  │
│   │  │                     CRACKING MODES                              │ │  │
│   │  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐              │ │  │
│   │  │  │ Single  │ │Wordlist │ │Incremental│ │ Rules  │              │ │  │
│   │  │  │  Mode   │ │  Mode   │ │   Mode   │ │  Mode  │              │ │  │
│   │  │  └─────────┘ └─────────┘ └─────────┘ └─────────┘              │ │  │
│   │  └────────────────────────────────────────────────────────────────┘ │  │
│   │                                                                      │  │
│   │  ┌────────────────────────────────────────────────────────────────┐ │  │
│   │  │                    HASH DETECTION                               │ │  │
│   │  │  Auto-detect by format: MD5, SHA, bcrypt, NTLM, etc.           │ │  │
│   │  │  Or specify: --format=raw-md5                                   │ │  │
│   │  └────────────────────────────────────────────────────────────────┘ │  │
│   └──────────────────────────────────────────────────────────────────────┘  │
│                            │                                                 │
│                            ▼                                                 │
│   ┌──────────────────────────────────────────────────────────────────────┐  │
│   │                          OUTPUT                                      │  │
│   │  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐            │  │
│   │  │   Terminal    │  │   john.pot    │  │   Session     │            │  │
│   │  │   Display     │  │   File        │  │   Files       │            │  │
│   │  │               │  │               │  │               │            │  │
│   │  │ user:password │  │ ~/.john/pot   │  │ ~/.john/      │            │  │
│   │  └───────────────┘  └───────────────┘  └───────────────┘            │  │
│   └──────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Hash Extraction Tools Ecosystem

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    HASH EXTRACTION TOOLS ECOSYSTEM                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   SOURCE FILES                        EXTRACTION TOOLS                      │
│                                                                              │
│   ┌──────────────┐                    ┌──────────────┐                      │
│   │  .zip files  │ ─────────────────► │  zip2john    │                      │
│   └──────────────┘                    └──────┬───────┘                      │
│                                             │                               │
│   ┌──────────────┐                    ┌──────┴───────┐                      │
│   │  .rar files  │ ─────────────────► │  rar2john    │                      │
│   └──────────────┘                    └──────┬───────┘                      │
│                                             │                               │
│   ┌──────────────┐                    ┌──────┴───────┐                      │
│   │  .pdf files  │ ─────────────────► │  pdf2john    │                      │
│   └──────────────┘                    └──────┬───────┘                      │
│                                             │                               │
│   ┌──────────────┐                    ┌──────┴───────┐                      │
│   │  Office docs │ ─────────────────► │ office2john  │                      │
│   └──────────────┘                    └──────┬───────┘                      │
│                                             │                               │
│   ┌──────────────┐                    ┌──────┴───────┐                      │
│   │  SSH keys    │ ─────────────────► │  ssh2john    │                      │
│   └──────────────┘                    └──────┬───────┘                      │
│                                             │                               │
│   ┌──────────────┐                    ┌──────┴───────┐                      │
│   │  KeePass db  │ ─────────────────► │keepass2john  │                      │
│   └──────────────┘                    └──────┬───────┘                      │
│                                             │                               │
│   ┌──────────────┐                    ┌──────┴───────┐                      │
│   │ Linux passwd │ ─────────────────► │  unshadow    │                      │
│   │    shadow    │                    │              │                      │
│   └──────────────┘                    └──────┬───────┘                      │
│                                             │                               │
│                                             ▼                               │
│                                    ┌─────────────────┐                       │
│                                    │  HASH FILE      │                       │
│                                    │  (hash.txt)     │                       │
│                                    │                 │                       │
│                                    │  user:hashvalue │                       │
│                                    └────────┬────────┘                       │
│                                             │                               │
│                                             ▼                               │
│                                    ┌─────────────────┐                       │
│                                    │ JOHN THE RIPPER │                       │
│                                    │                 │                       │
│                                    │ john hash.txt   │                       │
│                                    └─────────────────┘                       │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Password Cracking Comparison

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                  PASSWORD CRACKING TOOLS COMPARISON                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     CRACKING COMPLEXITY                              │   │
│   │                                                                      │   │
│   │   Easy ───────────────────────────────────────────────────► Hard    │   │
│   │    │                                                                  │   │
│   │    │  MD5      SHA1     SHA256    bcrypt    Argon2                   │   │
│   │    │    ▼        ▼         ▼         ▼         ▼                     │   │
│   │    │  Fast    Fast     Medium    Slow     Very Slow                 │   │
│   │    │  Weak    Weak     Good      Strong   Very Strong               │   │
│   │                                                                      │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     TOOL SELECTION GUIDE                             │   │
│   │                                                                      │   │
│   │   ┌───────────────────┐          ┌───────────────────┐              │   │
│   │   │   JOHN THE RIPPER │          │     HASHCAT       │              │   │
│   │   ├───────────────────┤          ├───────────────────┤              │   │
│   │   │ ✓ CPU-based       │          │ ✓ GPU-based       │              │   │
│   │   │ ✓ Easy to use     │          │ ✓ Very fast       │              │   │
│   │   │ ✓ Good for mobile │          │ ✓ Large scale     │              │   │
│   │   │ ✓ 400+ formats    │          │ ✓ 300+ formats    │              │   │
│   │   │ ✓ Built-in rules  │          │ ✓ Custom kernels  │              │   │
│   │   │ ✓ Free & open     │          │ ✓ Requires GPU    │              │   │
│   │   └───────────────────┘          └───────────────────┘              │   │
│   │                                                                      │   │
│   │   Use John When:                Use Hashcat When:                    │   │
│   │   - No GPU available            - GPU available                      │   │
│   │   - Learning/research           - Production cracking                │   │
│   │   - Mobile (Termux)             - Large hash sets                    │   │
│   │   - Quick tests                 - Performance critical               │   │
│   │                                                                      │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     ATTACK TYPE COMPARISON                           │   │
│   │                                                                      │   │
│   │   ┌─────────────────────────────────────────────────────────────┐   │   │
│   │   │  Attack Type  │  Speed  │  Success Rate  │  Use Case        │   │   │
│   │   ├─────────────────────────────────────────────────────────────┤   │   │
│   │   │  Dictionary   │  Fast   │  Medium        │  Common passwords│   │   │
│   │   │  Rule-based   │  Medium │  High          │  Variations      │   │   │
│   │   │  Incremental  │  Slow   │  Low           │  Unknown pwd     │   │   │
│   │   │  Rainbow      │  Fast   │  Low           │  Unsald hashes   │   │   │
│   │   │  Hybrid       │  Medium │  High          │  Targeted        │   │   │
│   │   └─────────────────────────────────────────────────────────────┘   │   │
│   │                                                                      │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

### Chapter Navigation Table

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          CHAPTER NAVIGATION                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                        PREREQUISITE CHAPTERS                          │  │
│  ├───────────┬───────────────────────────────────────────────────────────┤  │
│  │ Chapter   │ Topic                                                      │  │
│  ├───────────┼───────────────────────────────────────────────────────────┤  │
│  │ Ch 01-10  │ Termux Basics, Linux Commands, File Operations            │  │
│  │ Ch 11-20  │ Text Processing, User Management                          │  │
│  │ Ch 21-25  │ Bash Scripting, Automation                                 │  │
│  │ Ch 26-30  │ Network Tools, System Administration                      │  │
│  │ Ch 31     │ Hydra Basics - Online Password Cracking                    │  │
│  │ Ch 32     │ Hydra Advanced Techniques                                   │  │
│  └───────────┴───────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                        THIS CHAPTER                                    │  │
│  ├───────────────────────────────────────────────────────────────────────┤  │
│  │ Chapter 33: John the Ripper - Hash Cracking                           │  │
│  │ • Hash identification and types                                       │  │
│  │ • Cracking modes (wordlist, incremental, rules)                       │  │
│  │ • Hash extraction tools (zip2john, pdf2john, etc.)                    │  │
│  │ • Session management and performance                                   │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                        NEXT CHAPTERS                                   │  │
│  ├───────────┬───────────────────────────────────────────────────────────┤  │
│  │ Chapter   │ Topic                                                      │  │
│  ├───────────┼───────────────────────────────────────────────────────────┤  │
│  │ Ch 34     │ SQLMap - SQL Injection Testing                            │  │
│  │ Ch 35     │ Metasploit Framework Basics                                │  │
│  │ Ch 36     │ PhoneSploit & ADB Tools                                    │  │
│  │ Ch 37     │ Social Engineering Toolkit (SET)                          │  │
│  │ Ch 38     │ WiFi Security Tools                                        │  │
│  └───────────┴───────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                    JOHN VS HYDRA COMPARISON                           │  │
│  ├───────────┬──────────────────────┬─────────────────────────────────────┤  │
│  │ Aspect    │ John the Ripper       │ Hydra                              │  │
│  ├───────────┼──────────────────────┼─────────────────────────────────────┤  │
│  │ Type      │ Offline cracking      │ Online cracking                    │  │
│  │ Requires  │ Hash file             │ Live service                       │  │
│  │ Speed     │ CPU limited           │ Network limited                    │  │
│  │ Detection │ None on target        │ Can be detected                    │  │
│  │ Best for  │ Hash cracking         │ Service authentication             │  │
│  └───────────┴──────────────────────┴─────────────────────────────────────┘  │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Custom Rule Creation

```bash
#!/bin/bash
# Advanced Custom Rules for John the Ripper
# Create powerful password mutation rules

# Create custom rules file
cat > ~/.john/custom_rules.conf << 'EOF'
[List.Rules:AdvancedCustom]

# Basic mutations
c               # Capitalize
l               # Lowercase
u               # Uppercase
C               # Lowercase first, uppercase rest

# Append numbers
$[0-9]          # Append single digit
$[0-9]$[0-9]    # Append two digits

# Prepend numbers
^[0-9]          # Prepend single digit

# Append special characters
$[!@#$%^&*()]

# Year variations
$[0-9]$[0-9]$[0-9]$[0-9]  # Append 4 digits (years)

# Leet speak transformations
sa@ se3 si1 so0 ss$

# Common patterns
/^admin/ c      # Prepend 'admin' and capitalize
/^password/ c   # Prepend 'password' and capitalize

# Reverse and double
r               # Reverse the word
d               # Double the word

# Combination rules
c $[0-9]        # Capitalize + append number
l $[!@#]        # Lowercase + append special

# Season + Year
c $[0-9]$[0-9]$[0-9]$[0-9]  # Capitalize + year

# Common replacements
s/a/@/ s/e/3/ s/i/1/ s/o/0/ s/s/$/
EOF

# Use custom rules
john --wordlist=rockyou.txt --rules=AdvancedCustom --config=~/.john/custom_rules.conf hash.txt
```

### Advanced Technique 2: Multi-Stage Cracking Strategy

```bash
#!/bin/bash
# Intelligent Multi-Stage Password Cracking
# Progressively aggressive attacks

HASH_FILE=$1
OUTPUT_DIR="cracking_results"
mkdir -p $OUTPUT_DIR

echo "=== Multi-Stage Cracking Strategy ==="

# Stage 1: Quick wins with top passwords
echo "[Stage 1] Testing top 100 passwords..."
john --wordlist=top100.txt $HASH_FILE --session=stage1
john --show $HASH_FILE > $OUTPUT_DIR/stage1_results.txt

# Stage 2: Common passwords with basic rules
echo "[Stage 2] Common passwords with rules..."
john --wordlist=rockyou_top1000.txt --rules=simple $HASH_FILE --session=stage2
john --show $HASH_FILE > $OUTPUT_DIR/stage2_results.txt

# Stage 3: Full wordlist with advanced rules
echo "[Stage 3] Full wordlist with advanced rules..."
john --wordlist=rockyou.txt --rules=best64 $HASH_FILE --session=stage3
john --show $HASH_FILE > $OUTPUT_DIR/stage3_results.txt

# Stage 4: Targeted attack (if company info available)
if [ -f "company_words.txt" ]; then
    echo "[Stage 4] Targeted company attack..."
    john --wordlist=company_words.txt --rules=all $HASH_FILE --session=stage4
    john --show $HASH_FILE > $OUTPUT_DIR/stage4_results.txt
fi

# Stage 5: Incremental (limited length)
echo "[Stage 5] Incremental attack (1-6 chars)..."
john --incremental=Lower --max-length=6 $HASH_FILE --session=stage5
john --show $HASH_FILE > $OUTPUT_DIR/stage5_results.txt

# Generate report
echo "=== Cracking Summary ===" > $OUTPUT_DIR/final_report.txt
echo "" >> $OUTPUT_DIR/final_report.txt
john --show $HASH_FILE >> $OUTPUT_DIR/final_report.txt
echo "" >> $OUTPUT_DIR/final_report.txt
echo "Total cracked: $(john --show $HASH_FILE | grep -c ':')" >> $OUTPUT_DIR/final_report.txt

cat $OUTPUT_DIR/final_report.txt
```

### Advanced Technique 3: Hash Analysis and Format Detection

```bash
#!/bin/bash
# Advanced Hash Analysis and Format Detection Tool
# Identifies hash types and recommends cracking strategy

analyze_hash() {
    local hash=$1
    local length=${#hash}
    
    echo "=== Hash Analysis ==="
    echo "Hash: $hash"
    echo "Length: $length characters"
    echo ""
    
    # Detect hash type by length and format
    case $length in
        32)
            if [[ $hash =~ ^[a-fA-F0-9]+$ ]]; then
                echo "Likely: MD5 or NTLM"
                echo "John format: raw-md5 or NT"
                echo "Crack speed: Very Fast (GPU: billions/sec)"
            fi
            ;;
        40)
            if [[ $hash =~ ^[a-fA-F0-9]+$ ]]; then
                echo "Likely: SHA-1"
                echo "John format: raw-sha1"
                echo "Crack speed: Fast (GPU: billions/sec)"
            fi
            ;;
        64)
            if [[ $hash =~ ^[a-fA-F0-9]+$ ]]; then
                echo "Likely: SHA-256"
                echo "John format: raw-sha256"
                echo "Crack speed: Medium (GPU: millions/sec)"
            fi
            ;;
        128)
            if [[ $hash =~ ^[a-fA-F0-9]+$ ]]; then
                echo "Likely: SHA-512"
                echo "John format: raw-sha512"
                echo "Crack speed: Medium"
            fi
            ;;
        *)
            # Check for prefix patterns
            if [[ $hash == \$2a\$* ]] || [[ $hash == \$2b\$* ]] || [[ $hash == \$2y\$* ]]; then
                echo "Type: bcrypt"
                echo "John format: bcrypt"
                echo "Crack speed: Very Slow (designed to be slow)"
                echo "Recommended: Targeted wordlist + rules"
            elif [[ $hash == \$6\$* ]]; then
                echo "Type: SHA-512crypt (Linux shadow)"
                echo "John format: sha512crypt"
                echo "Crack speed: Slow"
            elif [[ $hash == \$5\$* ]]; then
                echo "Type: SHA-256crypt"
                echo "John format: sha256crypt"
                echo "Crack speed: Slow"
            elif [[ $hash == \$1\$* ]]; then
                echo "Type: MD5crypt"
                echo "John format: md5crypt"
                echo "Crack speed: Medium"
            else
                echo "Unknown format - trying auto-detection"
                echo "Run: john --list=formats | grep -i 'format_hint'"
            fi
            ;;
    esac
    
    echo ""
    echo "=== Cracking Recommendations ==="
    echo "1. Start with: john --wordlist=rockyou.txt hash.txt"
    echo "2. With rules: john --wordlist=rockyou.txt --rules hash.txt"
    echo "3. Check: john --show hash.txt"
}

# Main
if [ -z "$1" ]; then
    echo "Usage: $0 <hash_or_hashfile>"
    exit 1
fi

if [ -f "$1" ]; then
    # Analyze first hash in file
    FIRST_HASH=$(head -1 $1 | cut -d: -f2)
    analyze_hash "$FIRST_HASH"
else
    analyze_hash "$1"
fi
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### Knowledge Verification Checklist

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      CHAPTER 33 COMPLETION CHECKLIST                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  CORE CONCEPTS:                                                              │
│  ☐ Understood difference between online and offline cracking                │
│  ☐ Learned hash types (MD5, SHA, bcrypt, NTLM)                             │
│  ☐ Understood hash identification by length                                 │
│  ☐ Mastered John installation in Termux                                    │
│                                                                              │
│  CRACKING MODES:                                                             │
│  ☐ Used single crack mode                                                   │
│  ☐ Mastered wordlist mode                                                   │
│  ☐ Understand incremental mode limitations                                  │
│  ☐ Applied rules for variations                                             │
│                                                                              │
│  HASH EXTRACTION:                                                            │
│  ☐ Used zip2john for ZIP files                                              │
│  ☐ Used pdf2john for PDF documents                                         │
│  ☐ Used ssh2john for SSH keys                                              │
│  ☐ Used office2john for Office docs                                         │
│  ☐ Used unshadow for Linux passwords                                        │
│                                                                              │
│  ADVANCED SKILLS:                                                            │
│  ☐ Created custom rules                                                     │
│  ☐ Managed sessions (save/restore)                                          │
│  ☐ Optimized performance with --fork                                        │
│  ☐ Identified hash formats manually                                         │
│                                                                              │
│  PRACTICAL APPLICATIONS:                                                     │
│  ☐ Cracked a ZIP file password                                              │
│  ☐ Cracked an MD5 hash                                                      │
│  ☐ Used rules to improve success rate                                       │
│  ☐ Resumed an interrupted session                                           │
│  ☐ Analyzed hash strength                                                   │
│                                                                              │
│  SECURITY AWARENESS:                                                         │
│  ☐ Understood legal implications                                            │
│  ☐ Know when to use John vs Hydra                                           │
│  ☐ Can recommend secure hash algorithms                                     │
│  ☐ Understand password entropy                                             │
│                                                                              │
│  FINAL ASSESSMENT:                                                           │
│  ☐ Completed all quiz questions                                             │
│  ☐ Reviewed interview questions                                             │
│  ☐ Understood real-world scenarios                                          │
│  ☐ Ready for Chapter 34: SQLMap                                             │
│                                                                              │
│  SCORE: _____/25 items completed                                             │
│                                                                              │
│  Next Steps:                                                                 │
│  • Practice with sample hash files                                          │
│  • Create your own wordlists                                                │
│  • Experiment with custom rules                                             │
│  • Compare John vs Hashcat                                                  │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

**Chapter 33: John the Ripper - Complete! 🎉**

*Enhanced content added for comprehensive learning experience*
*Created by T3rmuxk1ng | Termux Full Course*
