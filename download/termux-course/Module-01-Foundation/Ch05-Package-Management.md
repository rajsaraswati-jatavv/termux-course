# Chapter 5: Package Management - Complete Guide

> **Module:** 1 - Foundation  
> **Chapter:** 5 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐ Beginner  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | pkg, apt, dpkg complete guide |
| Repository Guide | All repositories explained |
| Commands Reference | 30+ package management commands |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Package errors, dependency issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 5
Title: Package Management Complete Guide | pkg, apt, dpkg Commands
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon aur aaj hum seekhenge ek bahut important topic - 
Package Management.

Agar aap Termux mein tools install karna chahte ho, Python, Node.js, 
Nmap, Metasploit, ya koi bhi software - to aapko package management 
aani chahiye.

Ye chapter foundation ka last chapter hai. Iske baad aap Termux mein 
koi bhi package install, remove, update kar sakte ho.

Previous chapters mein humne basic commands seekhe, Linux basics 
cover kiye. Ab time hai package management master karne ka.

To chaliye shuru karte hain!

---

[SECTION 1: PACKAGE MANAGEMENT INTRODUCTION - 0:45 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - Package Management kya hai?

Windows mein aap software install karte ho .exe files se. 
Mac mein .dmg files hoti hain. Android mein .apk files.

Lekin Linux systems mein - aur Termux mein - alag system hai.
Ye system hai PACKAGE MANAGEMENT.

Package ek compressed file hoti hai jisme software hota hai:
- Program files
- Configuration files
- Metadata (version, dependencies, description)
- Installation scripts

Package Manager ek tool hai jo:
- Packages download karta hai repositories se
- Install karta hai
- Update karta hai
- Remove karta hai
- Dependencies handle karta hai

Termux mein do main package managers hain:
1. pkg - Termux ka native wrapper (recommended for beginners)
2. apt - Advanced Package Tool (more options)

Inke alava dpkg bhi hai jo low-level tool hai.

Aap sochoge - itne saare tools kyun? Simple answer:
- pkg = Easy, beginner-friendly, Termux-specific
- apt = Advanced, more options, Debian-style
- dpkg = Low-level, direct package manipulation

Hum sabko detail mein cover karenge.

---

[SECTION 2: PKG COMMAND - INSTALL & UNINSTALL - 3:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye sabse pehle pkg command master karte hain.

PKG - Package Manager ka short form hai. Ye Termux ka official 
package manager hai, apt ke upar wrapper hai.

[SYNTAX - pkg install]

Package install karna:

    pkg install <package-name>

Example - Python install karna:

    pkg install python

Multiple packages ek saath install karna:

    pkg install python nodejs git

Installation process mein aapko Y/n prompt milega.
Y = Yes, install karo
n = No, skip karo

Automatically yes karne ke liye -y flag use karein:

    pkg install python -y

[SCREEN: Package installation output]

Output mein aapko dikhega:
- Reading package lists...
- Dependency packages
- Download progress
- Unpacking
- Setting up

Package install hone ke baad verify karein:

    python --version

[SYNTAX - pkg uninstall]

Package remove karna:

    pkg uninstall <package-name>

Example:

    pkg uninstall python

Multiple packages remove karna:

    pkg uninstall python nodejs

Package uninstall karte waqt dependencies bhi remove karne ke liye:

    pkg uninstall python && pkg autoclean

Agar package remove nahi ho raha (dependency issues):

    pkg uninstall python --force

Lekin force use tabhi karein jab zaroori ho.

---

[SECTION 3: PKG COMMAND - UPDATE & UPGRADE - 6:00 to 8:30]
─────────────────────────────────────────────────────────────────────────────

Ab update aur upgrade commands dekhte hain.

Bahut log confuse hote hain - update aur upgrade mein kya farak hai?

pkg update = Repository list refresh karta hai
            Ye server se latest package list download karta hai
            Packages install nahi hoti, sirf list update hoti hai

pkg upgrade = Installed packages ko latest version mein update karta hai
              Ye actual packages download aur install karta hai

[DEMONSTRATION]

Pehle repository list update karein:

    pkg update

Output:
- Hit https://packages.termux.dev stable InRelease
- Get:1 https://packages.termux.dev stable/main arm Packages
- Fetched 1500 kB in 5s

Ye output batata hai ki server se package list download ho gayi.

Ab installed packages upgrade karein:

    pkg upgrade

Ye command aapke saare installed packages check karegi aur 
jo outdated hain, unhe update karega.

Best practice - dono commands ek saath:

    pkg update && pkg upgrade -y

Isse pehle list update hogi, phir packages upgrade hongi.
&& ka matlab hai - pehle command success tabhi doosri run hogi.

-y flag se automatically yes ho jayega saare prompts ka.

[KAB UPDATE KAREIN?]

Termux mein updates regular aate hain. Recommended:
- Daily ek baar update karein agar daily use karte ho
- Naye package install karne se pehle update karein
- Koi tool chalane se pehle update karein

---

[SECTION 4: PKG COMMAND - SEARCH & LIST - 8:30 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab search aur list commands dekhte hain.

[SEARCH COMMAND]

Kisi package ko dhundna ho to:

    pkg search <keyword>

Example - Python related packages dhundna:

    pkg search python

Output mein saare packages dikhenge jisme "python" word hai:
- python - Python 3 interpreter
- python2 - Python 2 interpreter
- python-tkinter - Tkinter for Python
- python-numpy - NumPy for Python
- etc.

Specific search:

    pkg search ^python$

Ye exact match dhundega - sirf "python" package.

Case-insensitive search:

    pkg search -i PYTHON

List installed packages:

    pkg list-installed

Ye command aapke Termux mein installed saare packages dikhayegi.
Output mein package name aur version dono honge.

Total count:

    pkg list-installed | wc -l

[LIST-ALL COMMAND]

Saare available packages dekhne ke liye:

    pkg list-all

Ye bahut bada list hogi - 1000+ packages.

Search karne ka better tareeka:

    pkg list-all | grep python

[SHOW COMMAND]

Kisi package ki detail dekhni ho:

    pkg show <package-name>

Example:

    pkg show python

Output:
- Package: python
- Version: 3.11.x
- Architecture: aarch64
- Maintainer: Termux
- Description: Python 3 interpreter
- Depends: libffi, openssl, etc.
- Homepage: https://python.org
- Download size
- Installed size

Ye information bahut useful hai installation se pehle.

---

[SECTION 5: PKG COMMAND - CLEAN & AUTOCLEAN - 11:00 to 13:00]
─────────────────────────────────────────────────────────────────────────────

Package management mein cleanup bhi important hai.

Jab aap packages install karte ho, Termux downloaded .deb files 
cache mein store karta hai. Ye files space leti hain.

Cache location: $PREFIX/var/cache/apt/archives/

[CACHE CHECK]

Cache size check karein:

    du -sh $PREFIX/var/cache/apt/archives/

[CLEAN COMMAND]

Purani cache files delete karna:

    pkg clean

Ye command downloaded .deb files delete kar degi.
Packages installed rahengi, bas download files delete hongi.

[AUTOCLEAN COMMAND]

    pkg autoclean

Ye sirf useless cache files delete karta hai - jo packages ab 
repository mein available nahi hain.

[AUTOREMOVE COMMAND]

    pkg uninstall <package>

Jab aap package uninstall karte ho, uske dependencies nahi 
hataate. Wo dependencies space lete rahte hain.

Uninstall ke baad unnecessary dependencies remove karna:

    pkg autoclean

Ya specific autoremove:

    apt autoremove -y

[WHEN TO CLEAN?]

- Storage kam ho
- Package install errors a rahe ho
- System slow ho raha hai
- Monthly maintenance ke liye

---

[SECTION 6: PKG VS APT - DIFFERENCES - 13:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab apt command ke baare mein baat karte hain.

APT - Advanced Package Tool. Debian, Ubuntu, aur Termux mein use hota hai.

pkg actually apt ka wrapper hai. pkg command internally apt ko 
call karti hai with some Termux-specific settings.

[COMPARISON TABLE]

┌─────────────────────────────────────────────────────────────────────────┐
│                    PKG VS APT COMPARISON                                 │
├────────────────┬────────────────────────┬───────────────────────────────┤
│ Task           │ pkg Command            │ apt Command                   │
├────────────────┼────────────────────────┼───────────────────────────────┤
│ Update         │ pkg update             │ apt update                    │
│ Upgrade        │ pkg upgrade            │ apt upgrade                   │
│ Install        │ pkg install python     │ apt install python            │
│ Remove         │ pkg uninstall python   │ apt remove python             │
│ Search         │ pkg search python      │ apt search python             │
│ Show           │ pkg show python        │ apt show python               │
│ List installed │ pkg list-installed     │ apt list --installed          │
│ Clean          │ pkg clean              │ apt clean                     │
│ Autoclean      │ pkg autoclean          │ apt autoclean                 │
│ Full Upgrade   │ pkg full-upgrade       │ apt full-upgrade              │
│ Fix Broken     │ N/A                    │ apt --fix-broken install      │
│ Hold Package   │ pkg hold python        │ apt-mark hold python          │
│ Download only  │ N/A                    │ apt download python           │
│ Change logs    │ N/A                    │ apt changelog python          │
└────────────────┴────────────────────────┴───────────────────────────────┘

[WHEN TO USE WHICH?]

pkg use karein:
✓ Daily operations
✓ Simple install/remove/update
✓ Beginners
✓ Quick tasks

apt use karein:
✓ Advanced troubleshooting
✓ Fix broken packages
✓ Hold/unhold packages
✓ Download packages without installing
✓ More control needed ho

[APT ADVANTAGES]

apt ke kuch extra features hain:

1. Fix broken installation:
    apt --fix-broken install

2. Package download without install:
    apt download python

3. Hold package (prevent upgrade):
    apt-mark hold python

4. Unhold package:
    apt-mark unhold python

5. Show held packages:
    apt-mark showhold

---

[SECTION 7: PACKAGE REPOSITORIES - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Ab repositories ke baare mein samjhte hain.

Repository ek server hai jahan packages store hote hain.
Termux ke multiple repositories hain different categories ke liye.

[REPOSITORY TYPES]

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX REPOSITORIES                                   │
├─────────────────┬───────────────────────────────────────────────────────┤
│ Repository      │ Description                                          │
├─────────────────┼───────────────────────────────────────────────────────┤
│ main            │ Default, core packages, tools, languages             │
│ games           │ Games and game-related packages                      │
│ science         │ Scientific computing, data analysis tools            │
│ root            │ Root-requiring packages (needs rooted device)        │
│ x11             │ GUI applications, X11 packages                       │
└─────────────────┴───────────────────────────────────────────────────────┘

[DEFAULT REPOSITORIES]

Main repository by default enabled hota hai.

Repository files location:

    $PREFIX/etc/apt/sources.list

Check current repositories:

    cat $PREFIX/etc/apt/sources.list

Output:
deb https://packages.termux.dev/termux-main stable main

[ADDING REPOSITORIES]

Extra repositories add karna:

    pkg install <repo-name>

Example - Games repository:

    pkg install game-repo

Science repository:

    pkg install science-repo

X11 repository (for GUI apps):

    pkg install x11-repo

Root repository (needs root):

    pkg install root-repo

[MANUAL REPOSITORY ADD]

Manual add karna ho to:

    echo "deb https://packages.termux.dev/termux-games games stable" >> $PREFIX/etc/apt/sources.list

Phir update:

    pkg update

[REMOVING REPOSITORY]

Repository uninstall:

    pkg uninstall game-repo

Ya manual remove:

    nano $PREFIX/etc/apt/sources.list

Repository line delete karein, save karein, then update.

---

[SECTION 8: DPKG COMMAND - BASICS - 17:30 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Ab dpkg command dekhte hain.

dpkg - Debian Package. Ye low-level tool hai jo directly .deb 
files handle karta hai.

pkg aur apt repositories se download karte hain.
dpkg local .deb files install karta hai.

[DPKG COMMANDS]

.deb file install:

    dpkg -i package.deb

Example - yt-dlp .deb file install:

    dpkg -i yt-dlp_2023.xx.x_arm64.deb

Package remove:

    dpkg -r package-name

Package info:

    dpkg -I package.deb

Package contents:

    dpkg -c package.deb

List all installed packages:

    dpkg -l

Specific package check:

    dpkg -l | grep python

Package files list:

    dpkg -L python

[WHEN TO USE DPKG?]

- Local .deb file install karni ho
- Package troubleshooting
- Manual package management
- Offline installation

[IMPORTANT NOTE]

dpkg dependencies automatically install nahi karta.
Agar dependencies missing hain, error aayegi.

Fix karne ke liye:

    apt --fix-broken install

---

[SECTION 9: PACKAGE DEPENDENCIES & HOLDING - 19:30 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Dependencies ek important concept hai.

[DEPENDENCIES]

Jab aap koi package install karte ho, wo package dusre packages 
pe depend kar sakta hai. Inhe dependencies kehte hain.

Example: python package depends on:
- libffi
- openssl
- readline
- ncurses
- zlib

Ye sab automatically install ho jaate hain jab aap python install karte ho.

Dependencies check:

    pkg show python | grep Depends

Reverse dependencies - kis package pe ye depend karti hai:

    apt rdepends python

[HOLDING PACKAGES]

Kabhi kabhi aap nahi chahte ki koi package update ho.
Example - specific version chahiye, ya compatibility issues.

Package hold karna:

    pkg hold python

Ya:

    apt-mark hold python

Hold status check:

    apt-mark showhold

Package unhold:

    pkg unhold python

Ya:

    apt-mark unhold python

[PRACTICAL USE CASE]

Node.js project mein specific version chahiye:

    pkg install nodejs
    pkg hold nodejs

Ab nodejs upgrade nahi hoga jab bhi aap pkg upgrade run karo.

---

[SECTION 10: FIXING BROKEN PACKAGES - 21:30 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Package management mein errors aana common hai. Let's learn to fix them.

[COMMON ERRORS]

Error 1: "dpkg was interrupted"

Solution:

    dpkg --configure -a

Error 2: "Unable to correct problems, you have held broken packages"

Solution:

    apt --fix-broken install

Error 3: "Dependency is not satisfiable"

Solution:

    pkg update
    pkg upgrade
    apt --fix-broken install

Error 4: "Package is in a very bad inconsistent state"

Solution:

    dpkg --remove --force-remove-reinstreq <package>
    apt clean
    pkg update

[COMPLETE FIX PROCESS]

Agar kuch bhi kaam nahi kar raha:

    # Step 1: Update repositories
    pkg update

    # Step 2: Fix broken
    apt --fix-broken install

    # Step 3: Configure pending
    dpkg --configure -a

    # Step 4: Clean cache
    pkg clean

    # Step 5: Try installation again
    pkg install <package>

[NUCLEAR OPTION]

Sab kuch reset karna ho (WARNING: deletes all packages):

    rm -rf $PREFIX/var/cache/apt/archives/*.deb
    rm -rf $PREFIX/var/lib/dpkg/lock
    dpkg --configure -a

---

[SECTION 11: INSTALLING FROM SOURCE - 23:00 to 24:30]
─────────────────────────────────────────────────────────────────────────────

Kabhi kabhi package repository mein nahi hota. Tab source se install karna padta hai.

[PREREQUISITES]

Build tools install karein:

    pkg install build-essential git cmake

Ye package install karega:
- gcc (C compiler)
- g++ (C++ compiler)
- make
- git
- cmake

[TYPICAL BUILD PROCESS]

Most projects follow this pattern:

    # Clone repository
    git clone https://github.com/user/project.git
    cd project

    # Check for build instructions
    cat README.md
    cat INSTALL.md

    # Common build steps
    mkdir build
    cd build
    cmake ..
    make
    make install

[EXAMPLE - Installing a tool from source]

    # Example: Installing a hypothetical tool
    git clone https://github.com/example/tool.git
    cd tool
    ./configure
    make
    make install

[UNINSTALLING SOURCE INSTALL]

Source se install kiya hua package remove karna:

    cd project
    make uninstall

Ya manual removal:

    which toolname
    rm /path/to/toolname

---

[SECTION 12: SUMMARY & NEXT PREVIEW - 24:30 to 26:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Package Management chapter complete! Let's summarize:

✅ pkg command - install, uninstall, update, upgrade, search, list, show
✅ apt command - advanced usage, extra features
✅ pkg vs apt - kab kya use karna hai
✅ Repositories - main, games, science, root, x11
✅ dpkg command - .deb files install karna
✅ Dependencies samjhe
✅ Package holding
✅ Broken packages fix karna
✅ Source se installation

[IMPORTANT COMMANDS]

┌─────────────────────────────────────────────────────────────────────────┐
│                    PACKAGE MANAGEMENT QUICK REFERENCE                    │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg update && pkg upgrade -y    │ Full system update                    │
│ pkg install <package>           │ Install package                       │
│ pkg uninstall <package>         │ Remove package                        │
│ pkg search <keyword>            │ Search packages                       │
│ pkg show <package>              │ Package details                       │
│ pkg list-installed              │ List installed packages               │
│ pkg clean                       │ Clean cache                           │
│ apt --fix-broken install        │ Fix broken packages                   │
│ dpkg -i file.deb                │ Install .deb file                     │
│ apt-mark hold <package>         │ Hold package                          │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 6 mein hum seekhenge:
- Termux file system structure
- Important directories
- $PREFIX explained
- File permissions in Termux
- Navigation mastery

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 6!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Package Management Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX PACKAGE MANAGEMENT SYSTEM                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     User Layer                                   │   │
│   │   pkg command (Termux wrapper - recommended)                     │   │
│   │   apt command (Advanced Package Tool - more options)             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Core Package Manager                          │   │
│   │   dpkg - Debian Package Manager                                  │   │
│   │   - Low-level package operations                                 │   │
│   │   - .deb file handling                                           │   │
│   │   - Package database management                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Package Repositories                          │   │
│   │   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐  │   │
│   │   │  main   │ │  games  │ │ science │ │  root   │ │   x11   │  │   │
│   │   └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Package Database Location: $PREFIX/var/lib/dpkg/                       │
│   Cache Location: $PREFIX/var/cache/apt/archives/                        │
│   Sources List: $PREFIX/etc/apt/sources.list                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. pkg Command Complete Guide

#### Installation Commands

```bash
# Basic install
pkg install <package>

# Multiple packages
pkg install python nodejs git vim

# With auto-yes
pkg install python -y

# Install without recommended packages
apt install --no-install-recommends <package>

# Reinstall package
pkg install <package> --reinstall

# Install specific version
apt install python=3.11.0

# Install from specific repository
apt install -t stable <package>
```

#### Removal Commands

```bash
# Remove package (keep config)
pkg uninstall <package>

# Remove package with dependencies
pkg uninstall <package> && pkg autoclean

# Remove package including config files
apt purge <package>

# Remove multiple packages
pkg uninstall python nodejs

# Force removal
dpkg --force-remove-reinstreq -r <package>
```

#### Update Commands

```bash
# Update package list
pkg update

# Upgrade installed packages
pkg upgrade

# Full upgrade (handles dependency changes)
pkg full-upgrade

# Combined update and upgrade
pkg update && pkg upgrade -y

# Upgrade specific package only
pkg upgrade <package>

# Download only (don't install)
apt install --download-only <package>
```

#### Search Commands

```bash
# Search by keyword
pkg search python

# Case insensitive search
pkg search -i PYTHON

# Regex search
pkg search "^python3$"

# Search in package descriptions
apt search python

# Search installed packages
pkg list-installed | grep python

# List all available
pkg list-all

# Search by maintainer
apt search --maintainer termux
```

#### Information Commands

```bash
# Show package details
pkg show python

# Show installed size
pkg show python | grep Installed-Size

# Show dependencies
pkg show python | grep Depends

# Show reverse dependencies
apt rdepends python

# Show package files
dpkg -L python

# Show package status
dpkg -s python

# Check if package installed
dpkg -l | grep python
```

### 3. apt Command Advanced Usage

```bash
# Advanced Package Tool commands

# Update package lists
apt update

# Upgrade packages
apt upgrade

# Full upgrade (more aggressive)
apt full-upgrade

# Install package
apt install <package>

# Remove package
apt remove <package>

# Remove package with config
apt purge <package>

# Autoremove unused dependencies
apt autoremove

# Fix broken packages
apt --fix-broken install

# Download package only
apt download <package>

# Check package changelog
apt changelog <package>

# Show package policy
apt policy <package>

# Mark package as auto-installed
apt-mark auto <package>

# Mark package as manually installed
apt-mark manual <package>

# Hold package (prevent upgrade)
apt-mark hold <package>

# Unhold package
apt-mark unhold <package>

# Show held packages
apt-mark showhold

# Show auto-installed packages
apt-mark showauto

# Clean cache
apt clean

# Clean obsolete cache
apt autoclean
```

### 4. pkg vs apt Complete Comparison

| Feature | pkg | apt | Notes |
|---------|-----|-----|-------|
| Basic Install | `pkg install` | `apt install` | Same result |
| Remove | `pkg uninstall` | `apt remove` | pkg name differs |
| Update | `pkg update` | `apt update` | Same |
| Upgrade | `pkg upgrade` | `apt upgrade` | Same |
| Search | `pkg search` | `apt search` | apt has more options |
| List Installed | `pkg list-installed` | `apt list --installed` | Different syntax |
| List All | `pkg list-all` | No direct equiv | pkg specific |
| Show Info | `pkg show` | `apt show` | Same |
| Clean | `pkg clean` | `apt clean` | Same |
| Autoclean | `pkg autoclean` | `apt autoclean` | Same |
| Full Upgrade | `pkg full-upgrade` | `apt full-upgrade` | Same |
| Fix Broken | Not available | `apt --fix-broken install` | apt only |
| Hold Package | `pkg hold` | `apt-mark hold` | Different tools |
| Download Only | Not available | `apt download` | apt only |
| Changelog | Not available | `apt changelog` | apt only |
| Policy Info | Not available | `apt policy` | apt only |

### 5. Package Repositories

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX REPOSITORY DETAILS                             │
├─────────────────┬───────────────────────────────────────────────────────┤
│ Repository      │ URL                                                   │
├─────────────────┼───────────────────────────────────────────────────────┤
│ Main            │ https://packages.termux.dev/termux-main               │
│ Games           │ https://packages.termux.dev/termux-games               │
│ Science         │ https://packages.termux.dev/termux-science             │
│ Root            │ https://packages.termux.dev/termux-root                │
│ X11             │ https://packages.termux.dev/termux-x11                 │
└─────────────────┴───────────────────────────────────────────────────────┘
```

#### Repository Management

```bash
# Check current repositories
cat $PREFIX/etc/apt/sources.list

# List all sources
ls $PREFIX/etc/apt/sources.list.d/

# Add games repository
pkg install game-repo

# Add science repository
pkg install science-repo

# Add x11 repository
pkg install x11-repo

# Add root repository
pkg install root-repo

# Manual repository add
echo "deb https://packages.termux.dev/termux-games games stable" >> $PREFIX/etc/apt/sources.list

# Remove repository
pkg uninstall game-repo

# Manual edit
nano $PREFIX/etc/apt/sources.list
```

#### Repository Contents

| Repository | Packages | Examples |
|------------|----------|----------|
| main | Core tools | python, nodejs, git, vim, bash |
| games | Gaming tools | nethack,crawl, bsd-games |
| science | Scientific | r, julia, jupyter, numpy |
| root | Root tools | tsu, proot, netutils |
| x11 | GUI apps | xterm, firefox, vlc |

### 6. dpkg Command Reference

```bash
# Install .deb file
dpkg -i package.deb

# Remove package
dpkg -r package-name

# Remove with config
dpkg -P package-name

# List all packages
dpkg -l

# List package files
dpkg -L package-name

# Show package info
dpkg -s package-name

# Show .deb file info
dpkg -I package.deb

# Show .deb contents
dpkg -c package.deb

# Extract .deb file
dpkg -x package.deb /destination/

# Configure packages
dpkg --configure -a

# Force removal
dpkg --force-remove-reinstreq -r package-name

# Search file owner
dpkg -S /path/to/file

# Set package selection
echo "package-name hold" | dpkg --set-selections

# Get package selection
dpkg --get-selections
```

### 7. Package Dependencies

```bash
# Show package dependencies
pkg show python | grep Depends

# Show all dependencies (recursive)
apt-cache depends --recurse python

# Show reverse dependencies
apt rdepends python

# Check dependency availability
apt-cache policy <dependency>

# Show recommended packages
pkg show python | grep Recommends

# Show suggested packages
pkg show python | grep Suggests

# Install with recommends
apt install --install-recommends <package>

# Install without recommends
apt install --no-install-recommends <package>
```

### 8. Package Holding

```bash
# Hold package using pkg
pkg hold python

# Hold using apt-mark
apt-mark hold python

# Unhold package
pkg unhold python
apt-mark unhold python

# Show held packages
apt-mark showhold

# Check if package is on hold
apt policy python

# Hold multiple packages
apt-mark hold python nodejs git

# Unhold multiple packages
apt-mark unhold python nodejs git
```

### 9. Fixing Broken Packages

```bash
# Most common fix
apt --fix-broken install

# Alternative
apt -f install

# Configure pending packages
dpkg --configure -a

# Force install
dpkg --configure --force-all

# Remove problematic package
dpkg --force-remove-reinstreq -r package-name

# Complete fix procedure
pkg update
apt --fix-broken install
dpkg --configure -a
pkg clean
pkg upgrade

# Nuclear option (clear everything)
rm -rf $PREFIX/var/lib/dpkg/lock
rm -rf $PREFIX/var/lib/dpkg/lock-frontend
rm -rf $PREFIX/var/cache/apt/archives/*.deb
dpkg --configure -a
pkg update
```

### 10. Installing from Source

```bash
# Install build essentials
pkg install build-essential git cmake

# Build essentials include
# - gcc (C compiler)
# - g++ (C++ compiler)
# - make
# - binutils
# - git
# - cmake

# Standard build process
git clone https://github.com/user/project.git
cd project
mkdir build
cd build
cmake ..
make
make install

# Alternative with autoconf
git clone https://github.com/user/project.git
cd project
./autogen.sh  # if available
./configure
make
make install

# Simple Makefile project
git clone https://github.com/user/project.git
cd project
make
make install

# Check install location
which project-name

# Uninstall source install
cd project
make uninstall
# or
rm $(which project-name)
```

---

## 📋 30+ PACKAGE MANAGEMENT COMMANDS

### Essential Commands

```bash
# 1. Update package lists
pkg update

# 2. Upgrade all packages
pkg upgrade -y

# 3. Combined update and upgrade
pkg update && pkg upgrade -y

# 4. Install a package
pkg install <package-name>

# 5. Install multiple packages
pkg install python nodejs git vim

# 6. Install with auto-confirm
pkg install <package> -y

# 7. Remove a package
pkg uninstall <package-name>

# 8. Remove multiple packages
pkg uninstall python nodejs

# 9. Remove with dependencies
apt purge <package> && apt autoremove -y

# 10. Search for packages
pkg search <keyword>

# 11. Case-insensitive search
pkg search -i <KEYWORD>

# 12. Show package details
pkg show <package-name>

# 13. List installed packages
pkg list-installed

# 14. List all available packages
pkg list-all

# 15. Clean package cache
pkg clean

# 16. Autoclean cache
pkg autoclean

# 17. Autoremove unused packages
apt autoremove -y

# 18. Fix broken packages
apt --fix-broken install

# 19. Hold a package
pkg hold <package-name>

# 20. Unhold a package
pkg unhold <package-name>

# 21. Show held packages
apt-mark showhold

# 22. Full system upgrade
pkg full-upgrade -y

# 23. Install .deb file
dpkg -i package.deb

# 24. Remove .deb installed package
dpkg -r package-name

# 25. List all packages (dpkg)
dpkg -l

# 26. Show package files
dpkg -L <package-name>

# 27. Check package status
dpkg -s <package-name>

# 28. Configure pending packages
dpkg --configure -a

# 29. Download package without installing
apt download <package-name>

# 30. Show package changelog
apt changelog <package-name>

# 31. Check package policy
apt policy <package-name>

# 32. Show reverse dependencies
apt rdepends <package-name>

# 33. Install games repository
pkg install game-repo

# 34. Install science repository
pkg install science-repo

# 35. Install x11 repository
pkg install x11-repo

# 36. Install root repository
pkg install root-repo

# 37. Check repositories
cat $PREFIX/etc/apt/sources.list

# 38. Count installed packages
pkg list-installed | wc -l

# 39. Show package dependencies
pkg show <package> | grep Depends

# 40. Search in installed packages
pkg list-installed | grep <keyword>
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Package Operations

```bash
# Task: Master basic package operations

# Step 1: Update package lists
pkg update

# Step 2: Search for a package
pkg search cowsay

# Step 3: Install the package
pkg install cowsay -y

# Step 4: Verify installation
cowsay "Hello Termux!"

# Step 5: Show package info
pkg show cowsay

# Step 6: List installed packages
pkg list-installed | grep cowsay

# Step 7: Uninstall the package
pkg uninstall cowsay

# Step 8: Verify removal
pkg list-installed | grep cowsay
# Should return nothing
```

### Exercise 2: Repository Management

```bash
# Task: Add and manage repositories

# Step 1: Check current repositories
cat $PREFIX/etc/apt/sources.list

# Step 2: Add games repository
pkg install game-repo

# Step 3: Update package lists
pkg update

# Step 4: Search for a game
pkg search nethack

# Step 5: Install a game
pkg install nethack -y

# Step 6: Play the game
nethack
# Press 'q' to quit

# Step 7: Check installed repos
ls $PREFIX/etc/apt/sources.list.d/

# Step 8: Remove game repo
pkg uninstall game-repo

# Step 9: Update again
pkg update
```

### Exercise 3: Package Holding

```bash
# Task: Hold and unhold packages

# Step 1: Install a package
pkg install python -y

# Step 2: Check current version
python --version

# Step 3: Hold the package
pkg hold python

# Step 4: Verify hold status
apt-mark showhold

# Step 5: Try to upgrade
pkg upgrade
# Python should not be upgraded

# Step 6: Unhold the package
pkg unhold python

# Step 7: Verify unhold
apt-mark showhold
# Should be empty
```

### Exercise 4: Fix Broken Packages

```bash
# Task: Practice fixing broken packages

# Step 1: Simulate broken state (don't actually run this)
# dpkg --force-depends -r <some-package>

# Step 2: Fix broken packages
apt --fix-broken install

# Step 3: Configure pending
dpkg --configure -a

# Step 4: Clean cache
pkg clean

# Step 5: Update everything
pkg update && pkg upgrade -y
```

### Exercise 5: Advanced Package Info

```bash
# Task: Extract detailed package information

# Step 1: Install a complex package
pkg install nodejs -y

# Step 2: Show all info
pkg show nodejs

# Step 3: Show dependencies only
pkg show nodejs | grep Depends

# Step 4: Show reverse dependencies
apt rdepends nodejs

# Step 5: Show installed files
dpkg -L nodejs | head -20

# Step 6: Check package size
pkg show nodejs | grep -E "Installed-Size|Download-Size"

# Step 7: Show package policy
apt policy nodejs

# Step 8: Check file ownership
dpkg -S $(which node)
```

### Exercise 6: Cache Management

```bash
# Task: Manage package cache

# Step 1: Check cache location
ls $PREFIX/var/cache/apt/archives/

# Step 2: Check cache size
du -sh $PREFIX/var/cache/apt/archives/

# Step 3: Install some packages
pkg install sl figlet -y

# Step 4: Check cache again
ls $PREFIX/var/cache/apt/archives/ | grep -E "sl|figlet"

# Step 5: Clean cache
pkg clean

# Step 6: Verify cache is empty
ls $PREFIX/var/cache/apt/archives/
# Should only have 'lock' file
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Unable to locate package"

```bash
# Cause: Outdated package lists or package doesn't exist

# Solution 1: Update package lists
pkg update

# Solution 2: Check package name
pkg search <keyword>

# Solution 3: Check internet connection
ping -c 3 google.com

# Solution 4: Check if using F-Droid version
echo $TERMUX_VERSION
# Should be 0.118 or higher

# Solution 5: Check repository
cat $PREFIX/etc/apt/sources.list

# Solution 6: Try apt search
apt search <package-name>
```

### Problem 2: "dpkg was interrupted"

```bash
# Cause: Previous installation was stopped midway

# Solution 1: Configure pending
dpkg --configure -a

# Solution 2: If that fails
rm $PREFIX/var/lib/dpkg/lock
dpkg --configure -a

# Solution 3: Force configure
dpkg --configure --force-all
```

### Problem 3: "Broken packages"

```bash
# Cause: Dependency issues

# Solution 1: Fix broken
apt --fix-broken install

# Solution 2: With -y flag
apt -f install -y

# Solution 3: Combined approach
dpkg --configure -a
apt --fix-broken install
pkg clean
pkg update
```

### Problem 4: "Package is in very bad inconsistent state"

```bash
# Cause: Severe package corruption

# Solution: Force remove and reinstall
dpkg --force-remove-reinstreq -r <package-name>
pkg clean
pkg update
pkg install <package-name>
```

### Problem 5: "Sub-process returned an error code"

```bash
# Cause: General package manager error

# Solution 1: Clean and retry
pkg clean
pkg update
pkg upgrade

# Solution 2: Reinstall affected package
pkg uninstall <package> --force
pkg install <package>

# Solution 3: Nuclear reset
rm -rf $PREFIX/var/lib/dpkg/lock*
rm -rf $PREFIX/var/cache/apt/archives/*.deb
dpkg --configure -a
pkg update
```

### Problem 6: "Dependency is not satisfiable"

```bash
# Cause: Required package not available

# Solution 1: Update everything
pkg update && pkg upgrade -y

# Solution 2: Install missing dependency manually
pkg show <package> | grep Depends
pkg install <missing-dependency>

# Solution 3: Check repository
apt policy <dependency>

# Solution 4: Use different version
apt install <package>=<version>
```

### Problem 7: "Unable to lock administration directory"

```bash
# Cause: Another package operation running or crashed

# Solution 1: Wait and retry
# Wait 30 seconds, try again

# Solution 2: Remove lock files
rm $PREFIX/var/lib/dpkg/lock
rm $PREFIX/var/lib/dpkg/lock-frontend
rm $PREFIX/var/cache/apt/archives/lock

# Solution 3: Configure and retry
dpkg --configure -a
pkg update
```

### Problem 8: "Hash sum mismatch"

```bash
# Cause: Corrupted download or bad mirror

# Solution 1: Clean and retry
pkg clean
pkg update

# Solution 2: Check internet stability
ping -c 10 google.com

# Solution 3: Manual clean
rm -rf $PREFIX/var/cache/apt/archives/*
rm -rf $PREFIX/var/lib/apt/lists/*
pkg update
```

### Problem 9: Repository Connection Issues

```bash
# Cause: Network or server issues

# Solution 1: Check connectivity
curl -I https://packages.termux.dev

# Solution 2: Use VPN if blocked
# Install VPN app and connect

# Solution 3: Try different network
# Switch WiFi or mobile data

# Solution 4: DNS issue fix
echo "nameserver 8.8.8.8" | tee $PREFIX/etc/resolv.conf
pkg update
```

### Problem 10: Package Won't Upgrade

```bash
# Cause: Package on hold or dependency issue

# Solution 1: Check if held
apt-mark showhold | grep <package>

# Solution 2: Unhold if needed
pkg unhold <package>

# Solution 3: Force upgrade
apt install --only-upgrade <package>

# Solution 4: Reinstall
pkg uninstall <package>
pkg install <package>
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Command Focus**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📦 PACKAGE MANAGEMENT            │
│   COMPLETE GUIDE                   │
│                                    │
│   pkg install | apt | dpkg         │
│   30+ Commands Covered!            │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Problem-Solution Style**
```
┌────────────────────────────────────┐
│  ❌ Broken Packages?               │
│  ❌ Install Errors?                │
│                                    │
│  ✅ LEARN PKG & APT                │
│  ✅ FIX ALL ISSUES                 │
│                                    │
│  Chapter 5 | T3rmuxk1ng            │
└────────────────────────────────────┘
```

**Option C: Clean Professional**
```
┌────────────────────────────────────┐
│  📦 TERMUX PACKAGE MANAGER         │
│  ─────────────────────────────     │
│                                    │
│  ✓ pkg command                     │
│  ✓ apt advanced                    │
│  ✓ dpkg basics                     │
│  ✓ Fix broken packages             │
│                                    │
│  FULL GUIDE | Chapter 5            │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📦 Termux Full Course - Chapter 5: Package Management Complete Guide

🔥 In this video you'll learn:
• pkg command complete guide
• apt command advanced usage
• pkg vs apt differences
• All 5 repositories explained
• dpkg command basics
• Fixing broken packages
• 30+ package management commands

⏱️ Timestamps:
0:00 - Introduction
0:45 - Package Management Intro
3:00 - pkg Install & Uninstall
6:00 - pkg Update & Upgrade
8:30 - pkg Search & List
11:00 - pkg Clean & Autoclean
13:00 - pkg vs apt Differences
15:00 - Package Repositories
17:30 - dpkg Command Basics
19:30 - Dependencies & Holding
21:30 - Fixing Broken Packages
23:00 - Installing from Source
24:30 - Summary

📝 Essential Commands:
pkg update && pkg upgrade -y
pkg install <package>
pkg search <keyword>
apt --fix-broken install

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #PackageManagement #T3rmuxk1ng #TermuxCourse #pkg #apt #LinuxOnAndroid

---
⚠️ Disclaimer: This video is for educational purposes only.
```

### Tags List

```
termux, termux package management, termux pkg command, termux apt,
termux dpkg, termux install packages, termux uninstall packages,
termux update, termux upgrade, termux repositories, termux fix broken,
pkg command, apt command, dpkg command, termux tutorial hindi,
termux full course, termux commands, termux for beginners,
linux package management, termux tips, t3rmuxk1ng, termux course hindi,
android terminal, termux guide, termux hindi tutorial
```

### Hashtags

```
#Termux #PackageManagement #pkg #apt #dpkg #TermuxCourse 
#TermuxHindi #LinuxOnAndroid #TermuxTutorial #T3rmuxk1ng 
#TermuxCommands #LearnTermux #AndroidTerminal
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux Wiki - Package Management | https://wiki.termux.com/wiki/Package_Management |
| Termux Packages | https://github.com/termux/termux-packages |
| Package List | https://packages.termux.dev/ |
| APT Manual | `man apt` (install man first) |

### Useful Commands

```bash
# Get help
pkg help
apt help
dpkg --help

# Manual pages
pkg install man
man pkg
man apt
man dpkg

# Version info
apt --version
dpkg --version
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 6, verify:

- [ ] Can install packages using `pkg install`
- [ ] Can remove packages using `pkg uninstall`
- [ ] Understand difference between `pkg update` and `pkg upgrade`
- [ ] Can search for packages using `pkg search`
- [ ] Know how to list installed packages
- [ ] Understand pkg vs apt differences
- [ ] Can add/remove repositories
- [ ] Can install .deb files using dpkg
- [ ] Know how to hold packages
- [ ] Can fix broken packages
- [ ] Cleaned package cache at least once

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 6: File System Structure**

- Termux file system layout
- Understanding $PREFIX
- Important directories explained
- File permissions in Termux
- Symbolic links
- Navigation mastery

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
