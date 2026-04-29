# Chapter 1: Termux Kya Hai & Installation Guide

> **Module:** 1 - Foundation  
> **Chapter:** 1 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐ Beginner  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed Termux introduction |
| Installation Guide | Step-by-step F-Droid installation |
| Commands Reference | All commands covered in chapter |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common installation issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 1
Title: Termux Kya Hai? | Complete Installation Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome to Termux Full Course by T3rmuxk1ng!

Main aapka host hoon aur aaj se shuru ho raha hai ek journey - ek aisi 
journey jo aapke Android phone ko ek powerful hacking aur development 
machine mein badal degi.

Agar aap ethical hacking, programming, cybersecurity, ya sirf Linux 
seekhna chahte ho - aur laptop nahi hai - to Termux aapke liye game 
changer hai.

Ye course 61 chapters ka hai, 10 modules mein divided hai. Har ek cheez 
step by step, from scratch to advanced. Koi prior knowledge chahiye 
nahi - bas ek Android phone aur internet connection.

To bina time waste kiye, chaliye shuru karte hain Chapter 1 se - 
Termux Kya Hai aur Kaise Install Karte Hain.

Play button dabaiye, video like karein, aur channel subscribe karein 
notification bell ke saath - taki koi video miss na ho.

---

[SECTION 1: TERMUX INTRODUCTION - 0:50 to 4:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle sawal - Termux kya hai?

Termux ek Android terminal emulator hai. Simple shabdon mein samjhein - 
ye aapke Android phone ko ek mini Linux computer bana deta hai.

Jab aap Android phone use karte ho, to aap buttons dabate ho, apps 
open karte ho, touch karte ho - ye sab GUI hai, Graphical User 
Interface. Graphical interface aapko easy dikhata hai, lekin power 
kam hoti hai.

Termux CLI deta hai - Command Line Interface. Black screen, green 
ya white text, commands type karo, output dekho. Ye professionals 
ka tareeka hai, hackers ka tareeka, developers ka tareeka.

Terminal ki power ye hai ki aap system ko directly control kar sakte 
ho. Files create karo, delete karo, scripts run karo, servers host 
karo, networks scan karo - sab kuch ek command se.

Lekin Termux sirf terminal emulator nahi hai. Ye ek complete Linux 
environment hai Android ke upar. Debian aur Ubuntu jaise packages 
support karta hai. Over 1000 packages available hain free mein.

Termux mein kya kya kar sakte hain? List badi lambi hai:

✓ Programming Languages - Python, Node.js, C, C++, Ruby, Go, Rust
✓ Development Tools - Git, Vim, Nano, Emacs
✓ Networking Tools - Nmap, Netcat, curl, wget
✓ Security Tools - Hydra, John, SQLMap, Metasploit
✓ Media Tools - ffmpeg, ImageMagick, yt-dlp
✓ Databases - MySQL, SQLite, PostgreSQL
✓ Servers - Apache, Nginx, Node.js server, Python server
✓ And much more...

Sabse important baat - Termux ROOT ke bina kaam karta hai!
Haan, aapko phone root karne ki zarurat nahi. Root optional hai 
advanced features ke liye, lekin 90% kaam root ke bina ho jaata hai.

Isliye Termux beginners ke liye perfect hai - safe, powerful, 
aur free.

---

[SECTION 2: TERMUX VS OTHER APPS - 4:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab sawal aata hai - Play Store pe to bahut saare terminal apps hain.
Kya Termux special hai? Kyun nahi UserLAnd, GNURoot, ya Linux Deploy?

Achha sawal hai. Main explain karta hoon differences:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX VS OTHER TERMINAL APPS                         │
├────────────────┬──────────────────┬─────────────────────────────────────┤
│ Feature        │ Termux           │ Other Apps                          │
├────────────────┼──────────────────┼─────────────────────────────────────┤
│ Root Required  │ ❌ No            │ Some require root                   │
│ Native Android │ ✅ Yes           │ Many use VM/chroot                 │
│ Performance    │ ⭐⭐⭐⭐⭐ Fast      │ Slower (VM overhead)                │
│ Package Mgmt   │ ✅ pkg/apt        │ Limited or complex                  │
│ Updates        │ ✅ Active         │ Many discontinued                   │
│ Community      │ ✅ Large          │ Smaller                             │
│ APIs           │ ✅ Termux:API     │ Limited                             │
│ Learning Curve │ Easy to Medium   │ Medium to Hard                      │
└────────────────┴──────────────────┴─────────────────────────────────────┘

UserLAnd aur GNURoot VM use karte hain - Virtual Machine. Wo ek 
Linux system ko Android ke upar run karte hain virtualization se. 
Isse performance slow hoti hai, storage zyada lagta hai.

Termux directly Android ke Linux kernel pe kaam karta hai - no VM, 
no overhead. Fast, lightweight, aur native experience.

Linux Deploy root require karta hai. Termux root free hai basic 
usage ke liye.

Aur sabse important - Termux ki community bahut active hai. Regular 
updates aate hain, new packages add hote hain, issues jaldi solve 
hote hain. Documentation excellent hai.

Isliye Termux best choice hai - beginners ke liye bhi, professionals 
ke liye bhi.

---

[SECTION 3: WHY F-DROID, NOT PLAY STORE - 6:00 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Ab installation ki baat aate hain. Yahan ek CRITICAL warning hai.

⚠️ WARNING: Termux ko Play Store se INSTALL NA KAREIN!

Main serious hoon. Play Store wala Termux outdated hai. Google ne 
Termux ke updates band kar diye hain Play Store pe. Last update 
2020 mein tha. Uske baad koi update nahi aaya.

Outdated Termux mein ye problems hongi:

❌ Packages install nahi honge (repository changed)
❌ Python latest version nahi milega
❌ Security vulnerabilities
❌ Many tools won't work
❌ Bugs jo fix ho chuke hain, wo bhi rahenge

Sahi source hai F-Droid. F-Droid ek open-source app store hai 
jo privacy-focused hai aur updates regularly deta hai.

Alternative: GitHub releases se direct APK download kar sakte ho.
Lekin F-Droid recommended hai kyunki automatic updates milte rahte hain.

---

[SECTION 4: INSTALLATION PROCESS - 8:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab installation process start karte hain. Main step by step 
bataunga, aap follow karein.

[STEP 1: F-Droid Installation]

Pehle F-Droid app download karein:
1. Browser mein jao: https://f-droid.org
2. "Download F-Droid" button pe click karein
3. APK download hogi
4. APK install karein (Unknown sources permission chahiye hoga)

Android setting mein jao:
Settings → Security → Unknown Sources → Enable

Ya phir Android 10+ mein:
Settings → Apps → Special Access → Install Unknown Apps → 
Browser enable karein

[STEP 2: Install Termux from F-Droid]

1. F-Droid app open karein
2. Search bar mein "Termux" type karein
3. Termux app pe click karein
4. Install button dabayein
5. Wait for installation

[STEP 3: Additional Apps (Recommended)]

F-Droid se ye apps bhi install karein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    RECOMMENDED TERMUX ADD-ONS                            │
├──────────────────────┬──────────────────────────────────────────────────┤
│ App                  │ Purpose                                         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Termux:API           │ Access Android features (camera, SMS, etc.)     │
│ Termux:Styling       │ Customize Termux colors and fonts               │
│ Termux:Float         │ Floating terminal window                        │
│ Termux:Tasker        │ Tasker integration for automation               │
│ Termux:Widget        │ Home screen shortcuts for scripts               │
│ Termux:Boot          │ Run scripts at boot                             │
└──────────────────────┴──────────────────────────────────────────────────┘

Minimum: Termux + Termux:API install karein
Recommended: Saare add-ons install karein

---

[SECTION 5: FIRST LAUNCH & SETUP - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Termux first time open karein.

[SCREEN: Termux loading screen]

Aapko "Installing..." ya "Setting up..." dikhega. Wait karein - 
ye normal hai. Pehli baar Termux apna environment extract kar raha hai.

30 seconds to 1 minute lag sakta hai depending on phone speed.

[SCREEN: Termux terminal ready]

Jab terminal ready ho, aapko welcome message dikhega aur ek 
blinking cursor milega.

Sabse pehla kaam - UPDATE karein:

    pkg update && pkg upgrade -y

Ye command:
- pkg update: Repository list refresh karta hai
- pkg upgrade: Installed packages update karta hai
- && : Do commands ko connect karta hai
- -y: Automatically yes karta hai prompts ka

[SCREEN: Running update command]

Thoda time lagega - internet speed pe depend karta hai. 
Wait karein jab tak complete na ho.

Agar koi error aaye to:
- Internet connection check karein
- Storage permission check karein (next step)
- F-Droid se install kiya hai na? Play Store wala nahi?

---

[SECTION 6: STORAGE ACCESS SETUP - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Ab ek important setup baaki hai - Storage Access.

By default Termux ko aapke phone ka internal storage access nahi 
hotas. Photos, downloads, files - sab inaccessible hai.

Access ke liye ye command run karein:

    termux-setup-storage

[SCREEN: Permission popup]

Ek popup aayega: "Allow Termux to access photos, media, and files?"

"Allow" button press karein.

Iske baad Termux ko storage access mil jaayega. Symbolic links 
ban jaayenge:

~/storage/dcim → /sdcard/DCIM
~/storage/downloads → /sdcard/Download
~/storage/music → /sdcard/Music
~/storage/pictures → /sdcard/Pictures
... etc

Test karein:

    ls ~/storage/

Ye command aapko storage folders dikha degi.

    ls /sdcard/

Ye bhi kaam karega - internal storage ka content dikhayega.

Ab aap:
- Files download folder se access kar sakte ho
- Scripts storage mein save kar sakte ho
- Media files work kar sakte ho
- Data backup kar sakte ho

---

[SECTION 7: BASIC COMMANDS TEST - 17:30 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab check karte hain ki sab kuch theek se kaam kar raha hai.

[TEST 1: Check Package Manager]

    pkg

Ye command pkg ke options dikhayega. Agar output aaya to package 
manager kaam kar raha hai.

[TEST 2: Check Python]

    python --version

Agar Python installed hai to version dikhayega. Agar nahi hai to:

    pkg install python -y

Install karein, phir version check karein.

[TEST 3: Run Python Command]

    python -c "print('Hello Termux!')"

Output: Hello Termux! aana chahiye.

[TEST 4: Current Directory]

    pwd

Ye command current directory batati hai - /data/data/com.termux/files/home

[TEST 5: List Files]

    ls

Current directory ke files list hongi.

[TEST 6: Clear Screen]

    clear

Screen clear ho jaayega.

Agar ye saare commands kaam kar rahe hain - CONGRATULATIONS! 🎉

Aapka Termux successfully install aur configured hai!

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 19:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 1 complete! Let's summarize:

✅ Termux kya hai - Linux environment Android pe, bina root ke
✅ Termux vs other apps - Kyun Termux best hai
✅ F-Droid installation - Play Store nahi, F-Droid use karein
✅ First setup - pkg update && pkg upgrade -y
✅ Storage access - termux-setup-storage
✅ Basic tests - Commands verify kiye

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 1 - IMPORTANT COMMANDS                        │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg update && pkg upgrade -y    │ Update Termux packages                │
│ termux-setup-storage            │ Grant storage access                  │
│ pkg install <package>           │ Install new package                   │
│ pkg search <name>               │ Search for package                    │
│ pkg uninstall <package>         │ Remove package                        │
│ python --version                │ Check Python version                  │
│ pwd                             │ Print current directory               │
│ ls                              │ List files                            │
│ clear                           │ Clear screen                          │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 2 mein hum seekhenge:
- Termux configuration files
- Environment variables kya hote hain
- .bashrc file customize karna
- Aliases banana - shortcuts commands ke liye
- Welcome message setup

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 2!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Termux Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         TERMUX ARCHITECTURE                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android Application Layer                      │   │
│   │   (Termux App - Java/Kotlin code, UI, User Interaction)          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     JNI Native Layer                             │   │
│   │   (Native C/C++ code, terminal emulation)                        │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Linux Environment                             │   │
│   │   ($PREFIX = /data/data/com.termux/files/usr)                    │   │
│   │                                                                   │   │
│   │   ├── bin/        (executables - python, bash, etc.)            │   │
│   │   ├── lib/        (libraries)                                   │   │
│   │   ├── etc/        (configuration files)                         │   │
│   │   ├── share/      (documentation, data)                         │   │
│   │   ├── tmp/        (temporary files)                             │   │
│   │   └── var/        (variable data)                               │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android Linux Kernel                          │   │
│   │   (Standard Android kernel - no modification needed)             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Key Paths

| Path | Description |
|------|-------------|
| `$HOME` or `~` | `/data/data/com.termux/files/home` - User home directory |
| `$PREFIX` | `/data/data/com.termux/files/usr` - System prefix |
| `$PREFIX/bin` | Executable binaries location |
| `$PREFIX/etc` | Configuration files |
| `~/storage` | Symlinks to shared storage |
| `/sdcard` | Internal storage (after termux-setup-storage) |

### 3. Package Sources

Termux packages come from multiple repositories:

```bash
# Main repository
deb https://packages.termux.dev/termux-main stable main

# Games repository
deb https://packages.termux.dev/termux-games games stable

# Science repository
deb https://packages.termux.dev/termux-science science stable

# Root repository (requires root)
deb https://packages.termux.dev/termux-root root stable

# X11 repository (GUI apps)
deb https://packages.termux.dev/termux-x11 x11 stable
```

Repository files location: `$PREFIX/etc/apt/sources.list`

---

## 🔧 INSTALLATION GUIDE

### Method 1: F-Droid (Recommended)

```
Step 1: Enable Unknown Sources
├── Settings → Security → Unknown Sources (Android < 10)
└── Settings → Apps → Special Access → Install Unknown Apps (Android 10+)

Step 2: Download F-Droid
├── Open browser
├── Go to: https://f-droid.org
├── Tap "Download F-Droid"
└── Install the APK

Step 3: Install Termux
├── Open F-Droid app
├── Wait for repository sync (first time)
├── Search "Termux"
├── Tap Install
└── Wait for installation

Step 4: Install Add-ons
├── Termux:API (Required for API features)
├── Termux:Styling (Optional - themes)
├── Termux:Float (Optional - floating window)
└── Termux:Widget (Optional - home shortcuts)
```

### Method 2: GitHub Releases

```bash
# Direct download links (latest version)
https://github.com/termux/termux-app/releases
https://github.com/termux/termux-api/releases

# Download APK files and install manually
```

### Method 3: Build from Source

```bash
# For developers who want to build themselves
git clone https://github.com/termux/termux-app
cd termux-app
./gradlew assembleDebug
```

---

## 📋 COMMANDS REFERENCE

### Package Management Commands

```bash
# Update package lists
pkg update

# Upgrade all installed packages
pkg upgrade

# Update and upgrade together
pkg update && pkg upgrade -y

# Install a package
pkg install <package-name>

# Install multiple packages
pkg install python nodejs git

# Remove a package
pkg uninstall <package-name>

# Remove package with dependencies
pkg uninstall <package-name> && pkg autoclean

# Search for a package
pkg search <keyword>

# List all installed packages
pkg list-installed

# Show package info
pkg show <package-name>

# Clean cache
pkg clean

# Hold package (prevent upgrade)
pkg hold <package-name>

# Unhold package
pkg unhold <package-name>
```

### Essential First Commands

```bash
# Grant storage permission
termux-setup-storage

# Check current directory
pwd
# Output: /data/data/com.termux/files/home

# List files in current directory
ls

# List files with details
ls -la

# List storage links
ls ~/storage/

# Check disk usage
df -h

# Check memory usage
free -h

# Clear terminal screen
clear

# Exit Termux
exit
```

### System Information Commands

```bash
# Termux version
echo $TERMUX_VERSION

# Android version
getprop ro.build.version.release

# Device model
getprop ro.product.model

# CPU info
cat /proc/cpuinfo

# Memory info
cat /proc/meminfo

# Kernel version
uname -a
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Installation Verification

```bash
# Task: Verify Termux is installed correctly

# Step 1: Check Termux is working
echo "Termux is working!"

# Step 2: Check package manager
pkg

# Step 3: Update everything
pkg update && pkg upgrade -y

# Step 4: Install Python
pkg install python -y

# Step 5: Test Python
python -c "print('Hello from Termux!')"

# Step 6: Grant storage
termux-setup-storage
# Press "Allow" on popup

# Step 7: Verify storage
ls ~/storage/

# Expected: You should see dcim, downloads, music, etc.
```

### Exercise 2: Create Your First Script

```bash
# Task: Create and run a simple Python script

# Step 1: Create a Python file
cat > hello.py << 'EOF'
# My first Termux script
import os
import platform

print("=" * 40)
print("Termux System Information")
print("=" * 40)
print(f"Python Version: {platform.python_version()}")
print(f"System: {platform.system()}")
print(f"Machine: {platform.machine()}")
print(f"Home: {os.path.expanduser('~')}")
print("=" * 40)
EOF

# Step 2: Run the script
python hello.py

# Expected: System information output
```

### Exercise 3: Explore Termux

```bash
# Task: Explore Termux environment

# Step 1: Navigate to Termux root
cd $PREFIX

# Step 2: List directories
ls

# Step 3: Check bin folder (executables)
ls bin/ | head -20

# Step 4: Check etc folder (configs)
ls etc/

# Step 5: Go back home
cd ~

# Step 6: Check current path
pwd

# Step 7: List all files including hidden
ls -la

# Step 8: Create a test directory
mkdir test

# Step 9: Navigate into it
cd test

# Step 10: Create a test file
echo "This is a test file" > test.txt

# Step 11: Read the file
cat test.txt

# Step 12: Go back and clean up
cd ~
rm -rf test
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Unable to locate package"

```bash
# Cause: Outdated package lists or wrong repository

# Solution 1: Update package lists
pkg update

# Solution 2: Check internet connection
ping -c 3 google.com

# Solution 3: Check if you installed from F-Droid (not Play Store)
# If Play Store version - uninstall and install from F-Droid

# Solution 4: Reset repositories
pkg upgrade
```

### Problem 2: "Permission denied" for storage

```bash
# Cause: Storage permission not granted

# Solution 1: Run setup command
termux-setup-storage

# If popup doesn't appear:

# Solution 2: Manual permission grant
# Go to: Settings → Apps → Termux → Permissions
# Enable: Storage / Files and Media

# Solution 3: Check if permission granted
ls /sdcard/
# Should show internal storage contents
```

### Problem 3: "Command not found"

```bash
# Cause: Package not installed

# Example: python: command not found
# Solution:
pkg install python -y

# Example: git: command not found
# Solution:
pkg install git -y

# Search for package
pkg search <command-name>
```

### Problem 4: "Segmentation fault" or crashes

```bash
# Cause: Corrupted installation or old version

# Solution 1: Clear cache
pkg clean

# Solution 2: Reinstall problematic package
pkg uninstall <package>
pkg install <package>

# Solution 3: Full reset (WARNING: deletes all data)
# Go to Android Settings → Apps → Termux → Clear Data
# Then reinstall from F-Droid
```

### Problem 5: Slow or hanging installation

```bash
# Cause: Slow internet or mirror issues

# Solution 1: Use different mirror
# Edit sources list
nano $PREFIX/etc/apt/sources.list

# Change mirror URL to:
# deb https://packages.termux.dev/termux-main stable main

# Solution 2: Check internet speed
curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -

# Solution 3: Use VPN if your ISP blocks the repo
```

### Problem 6: Play Store Version Issues

```bash
# Symptoms:
# - pkg update fails
# - "old version" errors
# - Packages not found

# Diagnosis:
echo $TERMUX_VERSION
# If version < 0.118, you have Play Store version

# Solution: COMPLETELY UNINSTALL and reinstall from F-Droid
# 1. Settings → Apps → Termux → Uninstall
# 2. Download from F-Droid
# 3. Install fresh
# 4. Run: pkg update && pkg upgrade -y
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Green Terminal Background]       │
│                                    │
│   📱 TERMUX                        │
│   COMPLETE INSTALL GUIDE           │
│                                    │
│   ✓ F-Droid Method                 │
│   ✓ No Root Required               │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Comparison Style**
```
┌────────────────────────────────────┐
│  Play Store ❌  │  F-Droid ✅       │
│  ───────────────┼───────────────── │
│  Outdated       │  Updated         │
│  Broken         │  Working         │
│  Bugs           │  Latest          │
│                                    │
│  USE F-DROID!                      │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Eye-Catching**
```
┌────────────────────────────────────┐
│  ⚠️ STOP!                          │
│                                    │
│  Don't Install Termux from         │
│  Play Store!                       │
│                                    │
│  👉 WATCH THIS FIRST 👈            │
│                                    │
│  Chapter 1 | T3rmuxk1ng            │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📱 Termux Full Course - Chapter 1: Termux Kya Hai? | Complete Installation Guide

🔥 In this video you'll learn:
• Termux kya hai aur kyun use karein
• F-Droid se sahi tarah install karna
• First setup aur configuration
• Storage access setup
• Basic commands test

⏱️ Timestamps:
0:00 - Introduction
0:50 - Termux Introduction
4:00 - Termux vs Other Apps
6:00 - Why F-Droid, Not Play Store
8:00 - Installation Process
12:00 - First Launch Setup
15:00 - Storage Access Setup
17:30 - Basic Commands Test
19:30 - Summary

📥 Download Links:
• F-Droid: https://f-droid.org
• Termux GitHub: https://github.com/termux/termux-app

📝 Commands from this video:
pkg update && pkg upgrade -y
termux-setup-storage
pkg install python -y

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxCourse #T3rmuxk1ng #LinuxOnAndroid #EthicalHacking #TermuxInstallation #TermuxHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on systems you have permission to test.
```

### Tags List

```
termux, termux tutorial, termux installation, termux course, 
termux full course, termux kya hai, termux install kaise kare,
termux f-droid, termux hindi, termux tutorial hindi,
android terminal emulator, linux on android, termux for beginners,
learn termux, termux setup, termux guide, ethical hacking,
cybersecurity, hacking tools, t3rmuxk1ng, termux course hindi,
android hacking, mobile hacking, termux commands, termux basics
```

### Hashtags

```
#Termux #TermuxCourse #TermuxHindi #TermuxTutorial #LinuxOnAndroid 
#AndroidHacking #EthicalHacking #CyberSecurity #TermuxForBeginners 
#T3rmuxk1ng #LearnTermux #TermuxInstallation #HindiTutorial
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| Termux Wiki | https://wiki.termux.com/ |
| Termux GitHub | https://github.com/termux |
| Termux Packages | https://github.com/termux/termux-packages |
| F-Droid | https://f-droid.org/ |

### Community

| Platform | Link |
|----------|------|
| Reddit | r/termux |
| Telegram | @termux |
| IRC | #termux on Libera.Chat |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Termux Help | Run `pkg help` in Termux |
| Package Info | Run `pkg show <package>` |
| Man Pages | Run `man <command>` (install man first) |
| Command Help | Run `<command> --help` |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 2, verify:

- [ ] Termux installed from F-Droid (not Play Store)
- [ ] `pkg update && pkg upgrade -y` completed successfully
- [ ] `termux-setup-storage` executed and permission granted
- [ ] Python installed and tested
- [ ] Basic commands working: pwd, ls, clear
- [ ] Storage access verified with `ls ~/storage/`
- [ ] Understood why Play Store version is bad

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 2: First Setup & Configuration**

- Termux configuration files location
- Understanding environment variables
- Creating and customizing .bashrc
- Setting up useful aliases
- Custom welcome message
- Prompt customization (PS1)

---

## 💡 PRO TIPS - MASTER THESE!

> 💡 **Pro Tip #1:** Always install Termux from F-Droid, never from Play Store. Play Store version is outdated since 2020 and most packages won't work!

> 💡 **Pro Tip #2:** Run `pkg update && pkg upgrade -y` every few days to keep your system updated with latest packages and security fixes.

> 💡 **Pro Tip #3:** Install all Termux add-ons together (API, Styling, Float, Widget, Boot, Tasker) for maximum functionality.

> 💡 **Pro Tip #4:** Use `termux-setup-storage` immediately after installation - without it, you can't access your phone's files.

> 💡 **Pro Tip #5:** Bookmark `~/storage/downloads` symlink - it's your bridge between Termux and your phone's Download folder.

> 💡 **Pro Tip #6:** Check your Termux version with `echo $TERMUX_VERSION` - if it's below 0.118, you have the wrong version!

> 💡 **Pro Tip #7:** Create an alias `alias update='pkg update && pkg upgrade -y'` in your .bashrc for quick updates.

> 💡 **Pro Tip #8:** Keep F-Droid app installed - it will notify you of Termux updates automatically.

> 💡 **Pro Tip #9:** If installation fails, try `pkg clean` first, then retry - it often fixes cache issues.

> 💡 **Pro Tip #10:** Use `pkg search <keyword>` to find packages before installing - there are 1000+ available!

---

## 🔥 REAL WORLD APPLICATIONS

### Where This Knowledge Applies:

**1. Mobile Development on the Go**
- Install Node.js, Python, Git on your phone
- Code and test applications anywhere
- Perfect for developers without laptops

**2. Ethical Hacking & Security Testing**
- Run Nmap, Netcat, Hydra, SQLMap
- Perform network scanning and analysis
- Learn cybersecurity hands-on

**3. Server Administration**
- SSH into remote servers from your phone
- Run web servers (Apache, Nginx, Python)
- Manage databases (MySQL, SQLite)

**4. Learning Linux**
- Practice Linux commands anywhere
- Prepare for Linux certifications
- Build command-line skills

**5. Automation & Scripting**
- Write Python/Bash scripts
- Automate repetitive tasks
- Create cron jobs for scheduled tasks

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    REAL WORLD USE CASE DIAGRAM                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                         ┌──────────────┐                                │
│                         │    TERMUX    │                                │
│                         └──────┬───────┘                                │
│                                 │                                        │
│         ┌───────────────────────┼───────────────────────┐               │
│         │                       │                       │                │
│         ▼                       ▼                       ▼                │
│   ┌───────────┐          ┌───────────┐          ┌───────────┐          │
│   │  Coding   │          │  Hacking  │          │  Servers  │          │
│   │  Python   │          │   Nmap    │          │   SSH     │          │
│   │  Node.js  │          │   Hydra   │          │   Apache  │          │
│   │   Git     │          │   Netcat  │          │   Nginx   │          │
│   └───────────┘          └───────────┘          └───────────┘          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ⚡ QUICK REFERENCE CARD

### Essential Commands Table

| Command | Description | Example |
|---------|-------------|---------|
| `pkg update` | Update package list | `pkg update` |
| `pkg upgrade -y` | Upgrade all packages | `pkg upgrade -y` |
| `pkg install <name>` | Install a package | `pkg install python` |
| `pkg uninstall <name>` | Remove a package | `pkg uninstall python` |
| `pkg search <term>` | Search packages | `pkg search nmap` |
| `pkg list-installed` | List installed packages | `pkg list-installed` |
| `pkg show <name>` | Show package info | `pkg show python` |
| `pkg clean` | Clean package cache | `pkg clean` |
| `termux-setup-storage` | Grant storage access | `termux-setup-storage` |
| `pwd` | Print working directory | `pwd` |
| `ls` | List files | `ls -la` |
| `cd` | Change directory | `cd ~/storage/downloads` |
| `clear` | Clear screen | `clear` |
| `exit` | Exit Termux | `exit` |

### Important Paths

| Path | Description |
|------|-------------|
| `$HOME` or `~` | `/data/data/com.termux/files/home` |
| `$PREFIX` | `/data/data/com.termux/files/usr` |
| `~/storage/downloads` | Link to Download folder |
| `~/storage/dcim` | Link to DCIM/Camera |
| `$PREFIX/bin` | Executable binaries |

---

## 🏆 BONUS: ADVANCED TIPS

### Extra Commands Not Covered in Main Content

```bash
# Check device architecture (for correct package downloads)
uname -m
# Output: aarch64 (most modern phones)

# Get system information
getprop ro.build.version.release    # Android version
getprop ro.product.model            # Device model

# Check disk space
df -h

# Check memory
free -h

# View CPU info
cat /proc/cpuinfo

# See Termux environment variables
env | grep TERMUX

# Reset Termux to factory state (WARNING: deletes everything!)
# Go to: Settings → Apps → Termux → Clear Data

# Backup your Termux setup
tar -czf ~/storage/downloads/termux-backup.tar.gz ~ --exclude=storage

# Install from GitHub releases
pkg install wget
wget https://github.com/termux/termux-app/releases/download/v0.118.0/termux-app_v0.118.0+github-debug_arm64-v8a.apk
```

### Hidden Features

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX HIDDEN FEATURES                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. Long press screen → Context menu (Copy, Paste, More)               │
│  2. Volume Up + Q → Show extra keys row                                 │
│  3. Volume Up + K → Show/hide soft keyboard                            │
│  4. Volume Up + M → Show menu                                           │
│  5. Volume Up + V → Paste from clipboard                               │
│  6. Pinch to zoom → Adjust font size                                    │
│  7. Two-finger tap → Toggle extra keys                                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### ✅ Key Takeaways

- **Termux is a Linux environment** for Android that works without root
- **Always install from F-Droid**, never from Play Store (outdated since 2020)
- **Termux:API add-on** is essential for accessing Android features
- **`pkg update && pkg upgrade -y`** should be your first command
- **`termux-setup-storage`** grants access to phone's internal storage
- **1000+ packages** are available including Python, Node.js, Nmap, Git
- **`$PREFIX`** is Termux's system directory (`/data/data/com.termux/files/usr`)
- **`~/storage/`** contains symlinks to your phone's folders
- Termux supports **programming, security tools, servers, and automation**
- **Tab completion** saves typing - use it!

### 🎯 Skills Acquired

- [ ] Install Termux correctly from F-Droid
- [ ] Update and upgrade packages
- [ ] Grant storage permissions
- [ ] Install packages using `pkg install`
- [ ] Navigate directories with `pwd`, `ls`, `cd`
- [ ] Understand Termux directory structure
- [ ] Verify installation is working correctly

---

## 🎯 INTERVIEW QUESTIONS

### Test Your Knowledge (With Answers)

**Q1: What is Termux and how does it differ from other terminal emulators?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Termux is an Android terminal emulator and Linux environment that runs without root. Unlike other terminal apps that use VMs or require root, Termux runs natively on Android's Linux kernel, making it faster and more efficient. It includes a package manager (pkg/apt) with 1000+ packages.
</details>

**Q2: Why should you install Termux from F-Droid instead of Play Store?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** The Play Store version of Termux hasn't been updated since 2020 (v0.101). Google changed policies that prevented updates. The F-Droid version is actively maintained (currently v0.118+), has updated packages, security fixes, and working repositories.
</details>

**Q3: What does the command `termux-setup-storage` do?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** It requests storage permission and creates symbolic links in `~/storage/` pointing to your phone's internal storage folders (downloads, dcim, music, pictures, etc). Without this, Termux cannot access your phone's files.
</details>

**Q4: Explain the difference between `pkg update` and `pkg upgrade`.**
<details>
<summary>Click to reveal answer</summary>

**Answer:** `pkg update` refreshes the package list from repositories (downloads metadata about available packages). `pkg upgrade` actually downloads and installs newer versions of installed packages. They're often combined: `pkg update && pkg upgrade -y`
</details>

**Q5: What is `$PREFIX` in Termux and why is it important?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** `$PREFIX` is an environment variable pointing to `/data/data/com.termux/files/usr` - the system directory containing all installed packages, binaries, libraries, and configuration files. It's Termux's equivalent of `/usr` in standard Linux.
</details>

**Q6: How would you install Python and verify it works in Termux?**
<details>
<summary>Click to reveal answer</summary>

**Answer:**
```bash
pkg install python -y
python --version
python -c "print('Hello Termux!')"
```
</details>

**Q7: What are Termux add-ons and name at least 3 useful ones.**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Termux add-ons extend functionality:
- **Termux:API** - Access Android features (camera, SMS, sensors)
- **Termux:Styling** - Customize colors and fonts
- **Termux:Float** - Floating terminal window
- **Termux:Widget** - Home screen shortcuts
- **Termux:Boot** - Run scripts at startup
- **Termux:Tasker** - Tasker automation integration
</details>

**Q8: What does the error "Unable to locate package" usually mean and how do you fix it?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** This error usually means:
1. Package list is outdated → Run `pkg update`
2. You have Play Store version → Reinstall from F-Droid
3. No internet connection → Check connectivity
4. Package name is wrong → Use `pkg search <keyword>`
</details>

**Q9: How would you check your Termux version and why does it matter?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Use `echo $TERMUX_VERSION`. Version matters because:
- Below 0.118 likely means Play Store version (outdated)
- Older versions have broken repositories
- Security vulnerabilities in old versions
- Many packages require newer Termux versions
</details>

**Q10: Explain the Termux directory structure.**
<details>
<summary>Click to reveal answer</summary>

**Answer:**
```
/data/data/com.termux/files/
├── home/        # User home directory ($HOME, ~)
│   ├── .bashrc  # Shell configuration
│   └── storage/ # Symlinks to phone storage
└── usr/         # System directory ($PREFIX)
    ├── bin/     # Executables
    ├── lib/     # Libraries
    ├── etc/     # Configurations
    └── var/     # Variable data
```
</details>

---

## 🚀 NEXT LEVEL TIPS

### Performance Optimization

```bash
# Use faster mirrors (if slow downloads)
# Edit sources.list
nano $PREFIX/etc/apt/sources.list

# Uncomment or add:
# deb https://grimler.se/termux-packages-24 stable main
```

### Best Practices

1. **Always update before installing packages** - `pkg update && pkg upgrade -y`
2. **Read package info first** - `pkg show <package>` before installing
3. **Use `-y` flag for automation** - Skip confirmation prompts
4. **Clean cache regularly** - `pkg clean` to free space
5. **Backup your setup** - Use tar to backup home directory
6. **Keep Termux in memory** - Enable "Acquire Wake Lock" to prevent killing

### Common Mistakes to Avoid

| ❌ Mistake | ✅ Correct Approach |
|-----------|---------------------|
| Installing from Play Store | Install from F-Droid only |
| Not running `pkg update` | Always update first |
| Skipping `termux-setup-storage` | Run it immediately after install |
| Ignoring storage warnings | Grant permissions when asked |
| Installing too many packages | Only install what you need |
| Not backing up | Backup important scripts regularly |

### Pro Workflow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    RECOMMENDED FIRST-DAY WORKFLOW                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Step 1: Install Termux from F-Droid                                   │
│           ↓                                                              │
│   Step 2: pkg update && pkg upgrade -y                                  │
│           ↓                                                              │
│   Step 3: termux-setup-storage (press Allow)                            │
│           ↓                                                              │
│   Step 4: pkg install python git nano vim -y                            │
│           ↓                                                              │
│   Step 5: Create .bashrc with aliases                                   │
│           ↓                                                              │
│   Step 6: Install Termux:API add-on                                     │
│           ↓                                                              │
│   Step 7: Test: python -c "print('Ready!')"                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🎮 INTERACTIVE ELEMENTS

### 📝 Quiz: Test Your Knowledge

**Score yourself: 10 points per correct answer**

1. What does Termux stand for?
   - a) Terminal for Unix Mobile X
   - b) Terminal Emulator for Android with Linux packages
   - c) Terminal UX
   - d) Terminal Multiplexer

2. Which source should you install Termux from?
   - a) Google Play Store
   - b) F-Droid
   - c) APKMirror
   - d) Any APK website

3. What is the first command you should run in Termux?
   - a) ls
   - b) pwd
   - c) pkg update && pkg upgrade -y
   - d) exit

4. What does `$PREFIX` point to?
   - a) /home
   - b) /sdcard
   - c) /data/data/com.termux/files/usr
   - d) /system

5. Which command grants storage access?
   - a) pkg install storage
   - b) termux-setup-storage
   - c) chmod storage
   - d) mount storage

6. How do you check installed packages?
   - a) pkg list
   - b) pkg list-installed
   - c) pkg show
   - d) dpkg -l

7. What is `~/storage/downloads`?
   - a) A folder inside Termux
   - b) A symbolic link to your phone's Download folder
   - c) A backup folder
   - d) A temporary folder

8. Which is NOT a Termux add-on?
   - a) Termux:API
   - b) Termux:Styling
   - c) Termux:Pro
   - d) Termux:Float

9. Why is Play Store Termux problematic?
   - a) It costs money
   - b) It's outdated (last updated 2020)
   - c) It requires root
   - d) It's in Chinese

10. What architecture does most modern phones use?
    - a) x86
    - b) ARM (aarch64)
    - c) MIPS
    - d) PowerPC

**Answers:** 1-b, 2-b, 3-c, 4-c, 5-b, 6-b, 7-b, 8-c, 9-b, 10-b

---

### 🛠️ Try It Yourself Challenges

**Challenge 1: Installation Verification**
```bash
# Task: Verify your Termux installation is correct
# Steps:
# 1. Check Termux version (should be 0.118+)
echo $TERMUX_VERSION

# 2. Check you can install packages
pkg install cowsay -y

# 3. Test it works
cowsay "Termux is working!"

# Expected: A cow saying "Termux is working!"
```

**Challenge 2: Storage Setup**
```bash
# Task: Set up and verify storage access
# Steps:
# 1. Run storage setup
termux-setup-storage

# 2. List storage links
ls -la ~/storage/

# 3. Navigate to downloads
cd ~/storage/downloads

# 4. Create a test file
echo "Hello from Termux!" > termux-test.txt

# 5. Verify in your phone's Files app
# Go to Download folder and find termux-test.txt
```

**Challenge 3: Package Management**
```bash
# Task: Install and manage packages
# Steps:
# 1. Search for a package
pkg search figlet

# 2. Install it
pkg install figlet -y

# 3. Use it
figlet "TERMUX"

# 4. Check it's installed
pkg list-installed | grep figlet

# 5. View package info
pkg show figlet
```

**Challenge 4: Create a Project Folder**
```bash
# Task: Set up a project workspace
# Steps:
# 1. Create projects directory
mkdir -p ~/projects/my-first-project

# 2. Navigate to it
cd ~/projects/my-first-project

# 3. Create a README
echo "# My First Project" > README.md

# 4. Create a Python script
cat > hello.py << 'EOF'
#!/usr/bin/env python3
print("Hello from my first Termux project!")
EOF

# 5. Run it
python hello.py
```

---

### ✅ Skill Check Checkpoints

**Checkpoint 1: Basic Setup Complete**
- [ ] Termux installed from F-Droid
- [ ] Version 0.118 or higher
- [ ] `pkg update && pkg upgrade -y` executed successfully
- [ ] Termux:API installed

**Checkpoint 2: Storage Configured**
- [ ] `termux-setup-storage` executed
- [ ] Permission granted
- [ ] `ls ~/storage/` shows dcim, downloads, etc.
- [ ] Can create files in downloads

**Checkpoint 3: Package Management**
- [ ] Can search packages: `pkg search`
- [ ] Can install packages: `pkg install`
- [ ] Can list installed: `pkg list-installed`
- [ ] Can remove packages: `pkg uninstall`

**Checkpoint 4: Navigation**
- [ ] Understand `pwd`, `ls`, `cd`
- [ ] Know `$HOME` and `$PREFIX`
- [ ] Can navigate to storage folders
- [ ] Can create and delete directories

---

## 🔗 RELATED CHAPTERS

### Cross-Reference Guide

| This Chapter | Related Chapter | Why Related |
|-------------|-----------------|-------------|
| Ch01: Introduction | **Ch02: Setup & Config** | Continue your setup |
| Ch01: Installation | **Ch05: Package Management** | Learn to install tools |
| Ch01: Basics | **Ch03: Linux Basics Part 1** | Learn essential commands |
| Ch01: Storage | **Ch04: Linux Basics Part 2** | File operations |
| Ch01: Architecture | **Ch06: File System** | Understand Termux structure |

### Next Steps Flowchart

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YOUR LEARNING PATH                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Chapter 1 ──→ Chapter 2 ──→ Chapter 3 ──→ Chapter 4 ──→ Chapter 5   │
│   (You are    (Setup &    (Linux       (Linux       (Package           │
│    here)       Config)     Basics 1)   Basics 2)    Management)        │
│                                                                          │
│              After Module 1, you'll be ready for:                       │
│              • Module 2: Programming (Python, Bash)                    │
│              • Module 3: Networking Tools                               │
│              • Module 4: Security & Hacking                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 VISUAL DIAGRAMS

### Termux Ecosystem

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX ECOSYSTEM OVERVIEW                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                          ┌──────────────┐                               │
│                          │   ANDROID    │                               │
│                          │     OS       │                               │
│                          └──────┬───────┘                               │
│                                 │                                        │
│                    ┌────────────┴────────────┐                          │
│                    │                         │                          │
│                    ▼                         ▼                          │
│           ┌──────────────┐          ┌──────────────┐                   │
│           │   TERMUX     │          │ TERMUX:API   │                   │
│           │   APP        │◄────────►│   ADD-ON     │                   │
│           └──────┬───────┘          └──────────────┘                   │
│                  │                                                       │
│                  ▼                                                       │
│    ┌──────────────────────────────────────┐                            │
│    │         TERMUX ENVIRONMENT            │                            │
│    ├──────────────────────────────────────┤                            │
│    │                                      │                            │
│    │  ┌─────────┐  ┌─────────┐  ┌──────┐ │                            │
│    │  │  BASH   │  │  PKG    │  │ TOOLS│ │                            │
│    │  │  SHELL  │  │  APT    │  │ 1000+│ │                            │
│    │  └─────────┘  └─────────┘  └──────┘ │                            │
│    │                                      │                            │
│    │  Languages: Python, Node, Ruby, Go  │                            │
│    │  Tools: Git, Vim, Nano, wget, curl  │                            │
│    │  Security: Nmap, Netcat, Hydra      │                            │
│    │                                      │                            │
│    └──────────────────────────────────────┘                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Installation Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    INSTALLATION PROCESS FLOW                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐               │
│   │  Download   │───►│   Install   │───►│   First     │               │
│   │  F-Droid    │    │   Termux    │    │   Launch    │               │
│   └─────────────┘    └─────────────┘    └──────┬──────┘               │
│                                                  │                       │
│                                                  ▼                       │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐               │
│   │   Setup     │◄───│   Grant     │◄───│   Pkg       │               │
│   │   Complete  │    │   Storage   │    │   Update    │               │
│   └─────────────┘    └─────────────┘    └─────────────┘               │
│                                                                          │
│   Time Required: 5-10 minutes                                           │
│   Internet Required: Yes                                                │
│   Storage Required: ~500MB (with common packages)                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
