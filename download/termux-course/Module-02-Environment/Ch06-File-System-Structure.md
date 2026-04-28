# Chapter 6: File System Structure

> **Module:** 2 - Environment  
> **Chapter:** 6 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Beginner-Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed file system architecture |
| Directory Structure | $PREFIX, $HOME, storage paths |
| Commands Reference | ls, tree, find, du, df, file, stat |
| Practice Exercises | Explore file system hands-on |
| Troubleshooting | Common file system issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 6
Title: File System Structure | Termux Directory Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - File System Structure.

Agar aap Termux ko seriously use karna chahte ho - scripting, development, 
hacking tools, ya servers - to aapko file system samajhna zaruri hai.

Ye chapter aapko sikhayega ki:
- Termux ka file system kaise organized hai
- Important directories kahan hain
- $PREFIX kya hai aur kyun important hai
- Storage paths kaise kaam karte hain
- Hidden files kya hoti hain

Linux mein kaam karte waqt aapko raaste samajhne honge - jaise ek nayi 
city mein ghar dhoondhna. Agar map nahi pata, to bhatak jaoge.

To chaliye shuru karte hain - File System ka map banate hain!

Play button dabaiye, video like karein, aur channel subscribe karein!

---

[SECTION 1: UNDERSTANDING FILE SYSTEM BASICS - 0:45 to 3:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle, file system kya hota hai?

File system ek organized tareeka hai files ko store karne ka. Jaise aapke 
ghar mein almirah hoti hai clothes ke liye, kitchen hoti hai utensils ke 
liye, study room hoti hai books ke liye - waise hi computer mein folders 
hote hain different files ke liye.

Android ka file system Linux based hai. Linux mein ek standard hota hai - 
FHS - Filesystem Hierarchy Standard.

Lekin Termux thoda alag hai. Kyun?

Kyunki Termux ek app hai Android ke andar. Uska apna isolated environment hai.

Standard Linux mein root directory "/" hoti hai. Uske andar:
- /bin - binaries/executables
- /etc - configuration files
- /home - user directories
- /usr - user programs
- /var - variable data
- /tmp - temporary files

Lekin Termux ke case mein, ye sab ek specific location pe hain.

Chaliye dekhte hain Termux ka structure:

    pwd

Ye command current directory batati hai. Output aayega:
/data/data/com.termux/files/home

Ye aapka HOME directory hai. Iska matlab ~ (tilde) se bhi likh sakte ho.

Ab dekho PREFIX:

    echo $PREFIX

Output: /data/data/com.termux/files/usr

Ye Termux ka "root" hai. Yahan saari system files hain.

Samjho aise:
- $PREFIX = Ye Termux ka system root hai (jaise Linux ka /usr)
- $HOME = Ye aapka personal space hai (jaise Linux ka /home/user)

---

[SECTION 2: $PREFIX DIRECTORY STRUCTURE - 3:30 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab $PREFIX directory ko explore karte hain.

    cd $PREFIX
    ls

Aapko ye directories dikhengi:

┌─────────────────────────────────────────────────────────────────────────┐
│                    $PREFIX DIRECTORY STRUCTURE                          │
├────────────────┬────────────────────────────────────────────────────────┤
│ Directory      │ Purpose                                                │
├────────────────┼────────────────────────────────────────────────────────┤
│ bin/           │ Executable files (commands/programs)                   │
│ etc/           │ Configuration files                                    │
│ lib/           │ Libraries (.so files - shared libraries)               │
│ libexec/       │ Helper executables (internal use)                      │
│ share/         │ Documentation, data files, locales                     │
│ tmp/           │ Temporary files                                        │
│ var/           │ Variable data (logs, caches, databases)                │
│ include/       │ Header files (for compilation)                         │
│ opt/           │ Optional add-on packages                               │
│ etc/termux/    │ Termux-specific configurations                         │
└────────────────┴────────────────────────────────────────────────────────┘

Har directory ka detailed explanation:

[bin/ - Executables]
Ye sabse important directory hai. Yahan saare commands aur programs hain.

    ls $PREFIX/bin | head -20

Output mein aapko python, bash, git, ls, cat, vim - sab dikhega.

Jab aap koi command run karte ho - jaise "python" - system is directory 
mein search karta hai.

Is directory ko PATH mein add kiya hota hai. Check karein:

    echo $PATH

Aapko /data/data/com.termux/files/usr/bin dikhega.

[etc/ - Configuration Files]
Ye configuration files ka ghar hai.

    ls $PREFIX/etc

Important files:
- passwd - User information
- group - Group information  
- hosts - Network hostnames
- apt/ - Package manager config
- termux/ - Termux-specific configs

Configuration files modify karne se system behavior change hota hai.

[lib/ - Libraries]
Yahan shared libraries hain - .so files. Ye executables ki helper files hain.

    ls $PREFIX/lib | head -10

Python libraries, C libraries, etc. - sab yahan hain.

Bina libraries ke programs run nahi honge.

[share/ - Data Files]
Documentation, locale data, icons - ye sab yahan hai.

    ls $PREFIX/share

Yahan aapko:
- doc/ - Documentation
- man/ - Manual pages
- locale/ - Language translations
- bash-completion/ - Bash auto-complete scripts

[tmp/ - Temporary Files]
Ye temporary files ke liye hai. Programs yahan apna temp data rakhte hain.

    ls $PREFIX/tmp

Reboot ke baad ye files clear ho sakti hain.

[var/ - Variable Data]
Logs, caches, databases - jo change hota rehta hai.

    ls $PREFIX/var

Yahan:
- cache/ - Package cache
- log/ - Log files
- lib/ - Variable library data

---

[SECTION 3: $HOME DIRECTORY STRUCTURE - 8:00 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab aapke personal space ki baat - $HOME directory.

    cd ~
    pwd

Output: /data/data/com.termux/files/home

Ye aapka personal workspace hai. Yahan aap apni files, scripts, projects 
rakh sakte ho.

    ls -la

-a flag se hidden files bhi dikhengi (jo . se start hoti hain).

┌─────────────────────────────────────────────────────────────────────────┐
│                    $HOME DIRECTORY STRUCTURE                            │
├──────────────────────────┬──────────────────────────────────────────────┤
│ File/Directory           │ Purpose                                      │
├──────────────────────────┼──────────────────────────────────────────────┤
│ .bashrc                  │ Bash shell configuration                     │
│ .bash_profile            │ Login shell configuration                    │
│ .profile                 │ Generic shell profile                        │
│ .bash_history            │ Command history                              │
│ .vimrc                   │ Vim editor configuration                     │
│ .nano/                   │ Nano editor configuration                    │
│ .config/                 │ Application configurations                   │
│ .local/                  │ Local user programs and data                 │
│ .cache/                  │ User cache files                             │
│ storage/                 │ Symlinks to Android storage                  │
│ projects/                │ (Optional) Your project folder               │
│ scripts/                 │ (Optional) Your scripts folder               │
└──────────────────────────┴──────────────────────────────────────────────┘

Hidden files ka importance:

Hidden files (dot files) configuration files hoti hain. Ye settings store 
kartee hain - color scheme, aliases, preferences, etc.

.bashrc sabse important hai:

    cat ~/.bashrc

Ye file har baar run hoti hai jab naya terminal khulta hai. Yahan aap:
- Aliases define kar sakte ho
- PATH modify kar sakte ho
- Custom functions bana sakte ho
- Welcome message add kar sakte ho

.storage/ directory:

Ye special directory hai. Iske andar symlinks hain Android storage ke:

    ls ~/storage/

Output:
- dcim → /sdcard/DCIM
- downloads → /sdcard/Download
- music → /sdcard/Music
- pictures → /sdcard/Pictures
- movies → /sdcard/Movies
- shared → /sdcard

Ye symlinks aapko Android storage access karne dete hain.

---

[SECTION 4: STORAGE PATHS AND SYMLINKS - 11:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Storage access Termux mein bahut important topic hai.

Pehle samjho ki Android ka storage structure kya hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ANDROID STORAGE STRUCTURE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Internal Storage (Phone memory)                                       │
│   ├── /sdcard/                    │ Main user-accessible storage        │
│   │   ├── DCIM/                   │ Camera photos/videos                │
│   │   ├── Download/               │ Downloaded files                    │
│   │   ├── Music/                  │ Music files                         │
│   │   ├── Pictures/               │ Pictures                            │
│   │   ├── Movies/                 │ Video files                         │
│   │   ├── Documents/              │ Document files                      │
│   │   └── Android/                │ App-specific data                   │
│   │                                                                │
│   External Storage (SD Card - if present)                              │
│   └── /storage/XXXX-XXXX/         │ SD card mount point                 │
│                                                                          │
│   Termux Private Storage                                                │
│   └── /data/data/com.termux/      │ Termux app data (isolated)          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Termux ke liye storage access:

By default, Termux ko storage access nahi hota. Access ke liye:

    termux-setup-storage

Ye command Android se permission maangti hai. "Allow" karne ke baad 
symlinks banti hain.

/sdcard vs ~/storage:

Dono ek hi jagah point karte hain, lekin:

    /sdcard          → Direct path (absolute)
    ~/storage/shared → Symlink (more organized)

Symlinks ka fayeda:

~/storage/ ke andar categorized symlinks hain:

~/storage/dcim      → Photos/Videos
~/storage/downloads → Downloads
~/storage/music     → Music
~/storage/pictures  → Pictures

Ye organized tareeka hai. Direct /sdcard use kar sakte ho, lekin 
~/storage/ better hai readability ke liye.

Testing karein:

    ls ~/storage/downloads
    ls /sdcard/Download

Dono same content dikhayenge.

SD Card access:

Agar phone mein SD card hai, to:

    ls ~/storage/external-1

Ye SD card ko point karega.

---

[SECTION 5: HIDDEN FILES & PATH NAVIGATION - 14:00 to 16:30]
─────────────────────────────────────────────────────────────────────────────

Hidden files samajhna bahut important hai.

Linux mein jo files "." (dot) se start hoti hain, wo hidden hoti hain.

Normal ls se nahi dikhengi:

    ls          # Hidden files nahi dikhengi
    ls -a       # Hidden files dikhegi
    ls -la      # Hidden files with details

Common hidden files:

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON HIDDEN FILES                                  │
├──────────────────────────┬──────────────────────────────────────────────┤
│ File                     │ Purpose                                      │
├──────────────────────────┼──────────────────────────────────────────────┤
│ .bashrc                  │ Bash configuration (run on each shell)       │
│ .bash_profile            │ Login shell config                           │
│ .profile                 │ Generic profile                              │
│ .bash_history            │ Command history                              │
│ .vimrc                   │ Vim settings                                 │
│ .gitconfig               │ Git configuration                            │
│ .ssh/                    │ SSH keys and config                          │
│ .config/                 │ App-specific configs                         │
│ .local/                  │ User-local installations                     │
│ .cache/                  │ Application cache                            │
│ .npm/                    │ Node.js package cache                        │
│ .pip/                    │ Python pip cache                             │
└──────────────────────────┴──────────────────────────────────────────────┘

Ye files edit karke customize kar sakte ho apna environment.

Path Navigation Tips:

Navigation commands yaad rakhein:

    pwd              # Current directory batata hai
    cd               # Home directory pe le jaata hai
    cd ~             # Same as cd (home directory)
    cd $PREFIX       # Termux system directory
    cd ~/storage     # Storage symlinks
    cd /sdcard       # Direct storage access
    cd ..            # Ek level upar (parent directory)
    cd ../..         # Do level upar
    cd -             # Previous directory pe wapas

Relative vs Absolute Paths:

    Absolute Path:   /data/data/com.termux/files/home/script.sh
                     Pura raasta root se
                     
    Relative Path:   ./script.sh
                     Current directory se

    Home Relative:   ~/script.sh
                     Home directory se

Quick shortcuts:

    cd ~        → Home
    cd $PREFIX  → Termux system root
    cd /sdcard  → Internal storage
    cd -        → Previous directory

---

[SECTION 6: FILE SYSTEM COMMANDS - 16:30 to 19:00]
─────────────────────────────────────────────────────────────────────────────

Ab important commands dekhte hain file system explore karne ke liye.

[ls - List Directory Contents]

    ls              # Simple list
    ls -l           # Detailed list (permissions, size, date)
    ls -la          # All files including hidden
    ls -lh          # Human-readable sizes
    ls -laS         # Sort by size
    ls -lat         # Sort by time (newest first)
    ls -R           # Recursive listing

[tree - Directory Tree]

Pehle install karein:

    pkg install tree

    tree            # Show directory tree
    tree -L 2       # Limit depth to 2 levels
    tree -a         # Include hidden files
    tree -h         # Human-readable sizes

[find - Search Files]

    find . -name "*.py"        # Find Python files
    find ~ -type d             # Find all directories
    find ~ -size +10M          # Files larger than 10MB
    find ~ -mtime -7           # Modified in last 7 days

[du - Disk Usage]

    du              # Directory sizes
    du -h           # Human-readable
    du -sh *        # Size of each item in current dir
    du -sh ~        # Total home directory size

[df - Disk Free]

    df              # Filesystem space
    df -h           # Human-readable
    df -h /sdcard   # Check SD card space

[file - Identify File Type]

    file script.sh  # Tell file type
    file image.png  # Image file info
    file *          # All files in directory

[stat - File Statistics]

    stat file.txt   # Detailed file info
    # Shows: size, permissions, inode, access/modify times

---

[SECTION 7: LINUX FHS COMPARISON - 19:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Linux FHS (Filesystem Hierarchy Standard) samajhna helpful hai.

Standard Linux structure:

/
├── bin/       → Essential binaries
├── sbin/      → System binaries
├── etc/       → Configuration
├── home/      → User directories
├── usr/       → User programs
├── var/       → Variable data
├── tmp/       → Temporary files
├── root/      → Root user home
├── dev/       → Device files
├── proc/      → Process information
└── sys/       → System information

Termux comparison:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX vs STANDARD LINUX                              │
├────────────────┬──────────────────────┬─────────────────────────────────┤
│ Linux Path     │ Termux Equivalent    │ Notes                           │
├────────────────┼──────────────────────┼─────────────────────────────────┤
│ /bin           │ $PREFIX/bin          │ Merged in Termux                │
│ /sbin          │ $PREFIX/bin          │ No separate sbin                │
│ /etc           │ $PREFIX/etc          │ Same structure                  │
│ /home/user     │ $HOME                │ Single user system              │
│ /usr           │ $PREFIX              │ Termux uses /usr-like structure │
│ /var           │ $PREFIX/var          │ Same concept                    │
│ /tmp           │ $PREFIX/tmp          │ Same concept                    │
│ /root          │ $HOME                │ No separate root user           │
│ /dev           │ /dev (Android)       │ Android kernel provides         │
│ /proc          │ /proc (Android)      │ Android kernel provides         │
│ /sys           │ /sys (Android)       │ Android kernel provides         │
└────────────────┴──────────────────────┴─────────────────────────────────┘

Key differences:

1. No root user - Termux single-user hai
2. No separate /bin, /sbin - Sab $PREFIX/bin mein
3. Isolated environment - Android sandbox
4. $PREFIX replaces /usr essentially
5. Android provides kernel interfaces (/dev, /proc, /sys)

Why this matters:

Agar aap Linux tutorials follow karte ho, to aapko ye differences pata 
hone chahiye. Kabhi /usr/bin pe command dhoond rahe ho, to actually 
$PREFIX/bin mein hoga.

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 21:30 to 23:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 6 complete! Let's summarize:

✅ File System basics - Organized structure for files
✅ $PREFIX directory - Termux ka system root
✅ Important directories - bin, lib, etc, share, tmp, var
✅ $HOME directory - Personal workspace
✅ Hidden files - Dot files for configuration
✅ Storage paths - ~/storage symlinks
✅ /sdcard vs ~/storage - Direct vs organized access
✅ File commands - ls, tree, find, du, df, file, stat
✅ Linux FHS comparison - How Termux differs from standard Linux

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 6 - IMPORTANT COMMANDS                        │
├─────────────────────────────────────────────────────────────────────────┤
│ pwd                    │ Print current directory                        │
│ echo $PREFIX           │ Show Termux system path                        │
│ echo $HOME             │ Show home directory                            │
│ ls -la                 │ List all files with details                    │
│ tree -L 2              │ Show directory tree (2 levels)                 │
│ find . -name "*.txt"   │ Find all text files                            │
│ du -sh *               │ Directory sizes                                │
│ df -h                  │ Disk space                                     │
│ file filename          │ Identify file type                             │
│ stat filename          │ File statistics                                │
│ cd $PREFIX             │ Go to Termux system directory                  │
│ cd ~/storage           │ Go to storage symlinks                         │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 7 mein hum seekhenge:
- Environment variables kya hoti hain
- PATH variable ka importance
- Custom environment variables banana
- .bashrc se environment configure karna
- Practical use cases

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 7!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Termux File System Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX FILE SYSTEM ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Android Sandbox Boundary                                              │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │                                                                 │   │
│   │   /data/data/com.termux/                                       │   │
│   │   │                                                             │   │
│   │   ├── files/                                                    │   │
│   │   │   ├── usr/  ← $PREFIX (System environment)                 │   │
│   │   │   │   ├── bin/     (Executables: python, bash, git...)    │   │
│   │   │   │   ├── lib/     (Libraries: .so files)                 │   │
│   │   │   │   ├── libexec/ (Helper executables)                   │   │
│   │   │   │   ├── etc/     (Config: passwd, hosts, apt...)        │   │
│   │   │   │   ├── share/   (Data: docs, man, locales)             │   │
│   │   │   │   ├── include/ (C/C++ headers)                        │   │
│   │   │   │   ├── tmp/     (Temporary files)                      │   │
│   │   │   │   ├── var/     (Logs, cache, databases)               │   │
│   │   │   │   └── opt/     (Optional packages)                    │   │
│   │   │   │                                                        │   │
│   │   │   └── home/ ← $HOME (User space)                          │   │
│   │   │       ├── .bashrc        (Bash config)                     │   │
│   │   │       ├── .bash_profile  (Login config)                    │   │
│   │   │       ├── .bash_history  (Command history)                 │   │
│   │   │       ├── .config/       (App configs)                     │   │
│   │   │       ├── .local/        (User programs)                   │   │
│   │   │       └── storage/       (Storage symlinks)                │   │
│   │   │                                                            │   │
│   │   └── cache/ (Package cache - managed by Android)              │   │
│   │                                                                 │   │
│   └────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Shared Storage (after termux-setup-storage)                          │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │   ~/storage/ → symlinks to:                                    │   │
│   │   ├── dcim      → /sdcard/DCIM                                │   │
│   │   ├── downloads → /sdcard/Download                            │   │
│   │   ├── music     → /sdcard/Music                               │   │
│   │   ├── pictures  → /sdcard/Pictures                            │   │
│   │   ├── movies    → /sdcard/Movies                              │   │
│   │   ├── shared    → /sdcard                                     │   │
│   │   └── external-1→ SD Card (if present)                        │   │
│   └────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Key Environment Variables

| Variable | Value | Description |
|----------|-------|-------------|
| `$HOME` | `/data/data/com.termux/files/home` | User home directory |
| `$PREFIX` | `/data/data/com.termux/files/usr` | Termux system prefix |
| `$PATH` | Includes `$PREFIX/bin` | Executable search path |
| `$TERM` | `xterm-256color` | Terminal type |
| `$SHELL` | `/data/data/com.termux/files/usr/bin/bash` | Default shell |
| `$TMPDIR` | `$PREFIX/tmp` | Temporary files directory |
| `$LD_LIBRARY_PATH` | `$PREFIX/lib` | Library search path |

### 3. $PREFIX Directory Structure Details

```
$PREFIX = /data/data/com.termux/files/usr
│
├── bin/                    # Executables (500+ commands)
│   ├── bash               # Shell
│   ├── python             # Python interpreter
│   ├── pip                # Python package manager
│   ├── git                # Version control
│   ├── vim                # Text editor
│   ├── ls, cat, grep...   # Core utilities
│   └── node, npm...       # Node.js (if installed)
│
├── lib/                    # Shared libraries
│   ├── libpython3.11.so   # Python library
│   ├── libcrypto.so       # OpenSSL library
│   ├── libc.so            # C library
│   └── python3.11/        # Python modules
│
├── libexec/                # Internal executables
│   └── (helper programs)
│
├── etc/                    # Configuration files
│   ├── passwd             # User database
│   ├── group              # Group database
│   ├── hosts              # Hostname lookup
│   ├── bash.bashrc        # System-wide bash config
│   ├── apt/               # APT configuration
│   │   └── sources.list   # Package repositories
│   └── termux/            # Termux-specific configs
│       └── termux.properties
│
├── share/                  # Data files
│   ├── doc/               # Documentation
│   ├── man/               # Manual pages
│   ├── locale/            # Translations
│   ├── bash-completion/   # Bash completions
│   └── vim/               # Vim runtime files
│
├── include/                # C/C++ headers
│   ├── python3.11/        # Python headers
│   ├── openssl/           # OpenSSL headers
│   └── (other headers)
│
├── tmp/                    # Temporary files
│   └── (temp data)
│
├── var/                    # Variable data
│   ├── cache/             # Package cache
│   │   └── apt/           # APT cache
│   ├── log/               # Log files
│   └── lib/               # Variable library data
│
└── opt/                    # Optional packages
    └── (additional software)
```

### 4. $HOME Directory Details

```
$HOME = /data/data/com.termux/files/home (~)
│
├── .bashrc                 # Bash interactive shell config
├── .bash_profile           # Login shell config
├── .profile                # Generic profile
├── .bash_history           # Command history
├── .bash_logout            # Logout script
│
├── .vimrc                  # Vim configuration
├── .vim/                   # Vim directory
│
├── .config/                # XDG config directory
│   ├── git/               # Git config
│   │   └── config
│   └── (other apps)
│
├── .local/                 # XDG local directory
│   ├── bin/               # User executables
│   ├── share/             # User data
│   └── lib/               # User libraries
│
├── .cache/                 # Cache directory
│
├── .ssh/                   # SSH configuration
│   ├── config             # SSH client config
│   ├── id_rsa             # Private key
│   ├── id_rsa.pub         # Public key
│   └── known_hosts        # Known hosts
│
├── .gitconfig              # Git configuration
│
├── .npm/                   # Node.js cache (if node installed)
├── .pip/                   # Python pip cache
│
└── storage/                # Storage symlinks
    ├── dcim       → /sdcard/DCIM
    ├── downloads  → /sdcard/Download
    ├── music      → /sdcard/Music
    ├── pictures   → /sdcard/Pictures
    ├── movies     → /sdcard/Movies
    ├── shared     → /sdcard
    └── external-1 → /storage/XXXX-XXXX (SD Card)
```

### 5. Understanding Linux FHS (Filesystem Hierarchy Standard)

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    LINUX FILESYSTEM HIERARCHY STANDARD                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   / (Root Directory)                                                    │
│   │                                                                     │
│   ├── bin/     Essential user binaries (ls, cat, cp, mv)               │
│   ├── sbin/    Essential system binaries (init, fdisk, mkfs)           │
│   ├── etc/     Host-specific system configuration                      │
│   ├── home/    User home directories                                   │
│   │   └── user/   User's personal files                                │
│   ├── root/    Root user's home directory                              │
│   ├── usr/     User utilities and applications                         │
│   │   ├── bin/   User commands                                         │
│   │   ├── sbin/  Non-essential system binaries                         │
│   │   ├── lib/   Libraries                                             │
│   │   ├── include/ Header files                                        │
│   │   ├── share/  Architecture-independent data                        │
│   │   └── local/  Local software                                       │
│   ├── var/     Variable files (logs, spool, cache)                     │
│   ├── tmp/     Temporary files                                          │
│   ├── lib/     Shared libraries needed by bin/ and sbin/               │
│   ├── dev/     Device files                                             │
│   ├── proc/    Virtual filesystem (process info)                       │
│   ├── sys/     Virtual filesystem (kernel info)                        │
│   ├── boot/    Boot loader files                                        │
│   ├── mnt/     Mount point for temporary mounts                        │
│   ├── media/   Mount point for removable media                         │
│   ├── opt/     Optional application software packages                  │
│   └── srv/     Site-specific data served by this system                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 6. Termux vs Standard Linux Comparison

| Aspect | Standard Linux | Termux |
|--------|---------------|--------|
| **Root Directory** | `/` | `$PREFIX` acts as root |
| **Single/Multi-user** | Multi-user | Single user |
| **Root Access** | root user exists | No root user concept |
| **/bin + /sbin** | Separate directories | Merged into `$PREFIX/bin` |
| **/home** | Multiple user homes | Single `$HOME` |
| **/usr** | Contains user programs | `$PREFIX` serves this purpose |
| **Package Manager** | apt, yum, pacman | pkg/apt |
| **Init System** | systemd, init | None (app-based) |
| **Kernel** | Linux kernel | Android's Linux kernel |
| **Privilege Escalation** | sudo, su | tsu (requires root) |
| **Device Files** | `/dev/*` | Android's `/dev/*` |
| **Process Info** | `/proc/*` | Android's `/proc/*` |

### 7. Hidden Files Reference

| File | Purpose | Example Content |
|------|---------|-----------------|
| `.bashrc` | Bash configuration | Aliases, functions, PATH |
| `.bash_profile` | Login shell config | Environment variables |
| `.profile` | Generic profile | Universal shell config |
| `.bash_history` | Command history | List of past commands |
| `.vimrc` | Vim configuration | Editor settings |
| `.gitconfig` | Git settings | User name, email, aliases |
| `.ssh/config` | SSH client config | Host shortcuts |
| `.config/` | App configs | Application-specific |
| `.local/bin/` | User scripts | Custom executables |
| `.cache/` | Cache files | Temporary app data |

### 8. Storage Access Details

```bash
# Grant storage permission
termux-setup-storage

# After permission, these symlinks are created:
~/storage/dcim       → /sdcard/DCIM           # Camera photos/videos
~/storage/downloads  → /sdcard/Download       # Downloaded files
~/storage/music      → /sdcard/Music          # Music files
~/storage/pictures   → /sdcard/Pictures       # Pictures
~/storage/movies     → /sdcard/Movies         # Video files
~/storage/shared     → /sdcard                # Root of internal storage

# If SD card is present:
~/storage/external-1 → /storage/XXXX-XXXX     # SD card
```

### 9. Path Navigation Reference

| Command | Description | Example Output |
|---------|-------------|----------------|
| `pwd` | Print working directory | `/data/data/com.termux/files/home` |
| `cd` | Go to home directory | Changes to `$HOME` |
| `cd ~` | Go to home directory | Same as `cd` |
| `cd $PREFIX` | Go to system directory | Changes to `/data/data/com.termux/files/usr` |
| `cd /sdcard` | Go to internal storage | Changes to `/sdcard` |
| `cd ~/storage` | Go to storage links | Changes to `$HOME/storage` |
| `cd ..` | Go up one level | Parent directory |
| `cd ../..` | Go up two levels | Grandparent directory |
| `cd -` | Go to previous directory | Returns to last location |
| `cd ~/projects` | Go to projects in home | `$HOME/projects` |

---

## 📋 COMMANDS REFERENCE

### ls - List Directory Contents

```bash
# Basic listing
ls                    # List files in current directory
ls /sdcard           # List files in specific directory
ls ~/storage         # List storage symlinks

# Detailed listing
ls -l                # Long format (permissions, owner, size, date)
ls -la               # Include hidden files (starting with .)
ls -lh               # Human-readable sizes (K, M, G)
ls -laS              # Sort by size (largest last)
ls -laSr             # Sort by size (largest first)
ls -lat              # Sort by modification time (newest first)
ls -laSrh            # Combined: all files, human sizes, reverse sort

# Recursive listing
ls -R                # List all subdirectories recursively
ls -R | head -50     # First 50 lines of recursive listing

# Special listings
ls -d */             # List only directories
ls -ld .*            # List only hidden files/directories
ls -1                # One file per line
ls -p                # Add / to directories

# Practical examples
ls $PREFIX/bin | wc -l           # Count executables
ls -la ~ | grep "^d"             # List only directories
ls -lha /sdcard/Download         # Check downloads folder
```

### tree - Display Directory Tree

```bash
# Installation
pkg install tree

# Basic usage
tree                    # Show directory tree from current location
tree ~                  # Tree of home directory
tree $PREFIX            # Tree of system directory

# Depth control
tree -L 1               # Only 1 level deep
tree -L 2               # 2 levels deep
tree -L 3 $PREFIX       # 3 levels of system directory

# Include/exclude options
tree -a                 # Include hidden files
tree -d                 # Directories only
tree -f                 # Show full path prefix
tree -i 'node_modules'  # Exclude pattern

# Size information
tree -h                 # Human-readable sizes
tree -du                # Show directory size

# Output formats
tree -F                 # Add indicators (/, *, @)
tree -p                 # Show permissions
tree -u                 # Show username

# Practical examples
tree -L 2 -d ~          # Show home directory structure
tree -a -L 1 ~/storage  # Show storage symlinks
tree -h -d -L 1 ~       # Directory sizes in home
```

### find - Search for Files

```bash
# Basic search
find . -name "file.txt"           # Find file.txt in current directory
find ~ -name "*.py"               # Find all Python files in home
find $PREFIX -name "python*"      # Find files starting with python

# Search by type
find ~ -type f                    # Find all regular files
find ~ -type d                    # Find all directories
find ~ -type l                    # Find all symbolic links

# Search by size
find ~ -size +100M                # Files larger than 100MB
find ~ -size -10k                 # Files smaller than 10KB
find ~ -size +1G                  # Files larger than 1GB

# Search by time
find ~ -mtime -7                  # Modified in last 7 days
find ~ -mtime +30                 # Modified more than 30 days ago
find ~ -mmin -60                  # Modified in last 60 minutes
find ~ -atime -1                  # Accessed in last 24 hours

# Search by permissions
find ~ -perm 755                  # Files with exact permission 755
find ~ -executable                # Executable files

# Search by owner
find ~ -user root                 # Files owned by root (won't work in Termux)

# Combined searches
find ~ -name "*.log" -size +10M   # Log files larger than 10MB
find ~ -name "*.txt" -mtime -1    # Text files modified today

# Actions on found files
find ~ -name "*.tmp" -delete      # Delete all .tmp files
find ~ -name "*.py" -exec chmod +x {} \;  # Make Python files executable

# Practical examples
find ~ -maxdepth 2 -type d        # Find directories (max 2 levels deep)
find /sdcard -name "*.jpg"        # Find all JPEG images
find $PREFIX/bin -type f | wc -l  # Count all executables
```

### du - Disk Usage

```bash
# Basic usage
du                      # Show size of current directory
du ~                    # Show size of home directory
du $PREFIX              # Show size of system directory

# Human-readable
du -h                   # Human-readable sizes
du -sh                  # Summary only, human-readable

# Multiple items
du -sh *                # Size of each item in current directory
du -sh ~/*              # Size of each item in home
du -sh ~/storage/*      # Size of each storage link

# Sort by size
du -sh * | sort -h      # Sort by size (smallest first)
du -sh * | sort -hr     # Sort by size (largest first)

# Depth control
du -h --max-depth=1     # Only 1 level deep
du -h --max-depth=2     # 2 levels deep

# Total only
du -s                   # Total only
du -sh ~                # Total size of home directory

# Practical examples
du -sh $PREFIX/*        # Size of each system directory
du -sh ~/.cache         # Check cache size
du -sh /sdcard/*        # Check storage usage
du -sh ~ | grep -E "^[0-9]+G"  # Show if home > 1GB
```

### df - Disk Free Space

```bash
# Basic usage
df                      # Show filesystem space
df -h                   # Human-readable output
df -H                   # SI units (1000-based)

# Specific filesystem
df -h /sdcard           # Check SD card space
df -h ~                 # Check home filesystem

# Show all filesystems
df -a                   # Include dummy filesystems

# Show inode information
df -i                   # Inode usage

# Specific columns
df -h --output=source,size,used,avail  # Custom columns

# Practical examples
df -h | grep -E "^/dev"          # Show only real devices
df -h /sdcard | tail -1 | awk '{print $5}'  # Get usage percentage
```

### file - Determine File Type

```bash
# Basic usage
file filename.txt              # Identify file type
file script.sh                 # Identify shell script
file image.png                 # Identify image file

# Multiple files
file *                         # Identify all files in directory
file ~/.bashrc                 # Identify bashrc file

# Detailed output
file -b filename               # Brief mode (no filename)
file -i filename               # MIME type
file -i *                      # MIME types of all files

# Special files
file /sdcard/Download/*        # Identify all downloads
file script.py                 # Check Python script

# Practical examples
file /sdcard/DCIM/Camera/*     # Identify camera files
file -i *.py                   # MIME type of Python files
file -b *.sh                   # Brief check of shell scripts
```

### stat - Display File Status

```bash
# Basic usage
stat filename                  # Detailed file information
stat ~/.bashrc                 # Info about bashrc
stat $PREFIX/bin/python        # Info about Python executable

# Specific information
stat -c "%s" filename          # File size only
stat -c "%U %G" filename       # Owner and group
stat -c "%A" filename          # Permissions in symbolic form
stat -c "%a" filename          # Permissions in octal

# Time information
stat -c "%y" filename          # Last modification time
stat -c "%z" filename          # Last change time
stat -c "%x" filename          # Last access time

# Inode information
stat -c "%i" filename          # Inode number

# Multiple formats
stat -c "%n: %s bytes, modified %y" filename

# Practical examples
stat ~/.bash_history           # When was history last modified
stat -c "%a %n" *              # Permissions and names of all files
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Explore $PREFIX Directory

```bash
# Task: Understand the Termux system directory structure

# Step 1: Navigate to PREFIX
cd $PREFIX
pwd
# Expected: /data/data/com.termux/files/usr

# Step 2: List all directories
ls -d */

# Step 3: Count files in bin directory
ls bin | wc -l
# Note the number of executables

# Step 4: Check what's in etc
ls -la etc/

# Step 5: View passwd file
cat etc/passwd

# Step 6: Check hosts file
cat etc/hosts

# Step 7: Navigate to share/doc
cd share/doc
ls

# Step 8: Check disk usage of PREFIX
du -sh $PREFIX

# Step 9: Go back home
cd ~
```

### Exercise 2: Explore $HOME Directory

```bash
# Task: Understand your home directory and hidden files

# Step 1: Navigate to home
cd ~
pwd

# Step 2: List visible files only
ls

# Step 3: List ALL files including hidden
ls -la

# Step 4: List only hidden files
ls -ld .*

# Step 5: Check .bashrc exists
cat ~/.bashrc

# Step 6: Check command history
cat ~/.bash_history | head -20

# Step 7: Create a directory structure
mkdir -p ~/projects/python
mkdir -p ~/scripts
mkdir -p ~/tools

# Step 8: Verify structure
tree -L 2 ~

# Step 9: Check total home size
du -sh ~
```

### Exercise 3: Storage Exploration

```bash
# Task: Explore storage symlinks and understand paths

# Step 1: List storage symlinks
ls -la ~/storage/

# Step 2: Check what each symlink points to
readlink ~/storage/downloads
readlink ~/storage/dcim
readlink ~/storage/shared

# Step 3: List downloads folder
ls ~/storage/downloads

# Step 4: List DCIM folder
ls ~/storage/dcim

# Step 5: Compare /sdcard and ~/storage/shared
ls /sdcard | head -10
ls ~/storage/shared | head -10

# Step 6: Check storage usage
df -h /sdcard

# Step 7: Find all images on storage
find ~/storage/shared -name "*.jpg" 2>/dev/null | head -10

# Step 8: Create a test file in storage
echo "Termux test file" > ~/storage/downloads/termux_test.txt

# Step 9: Verify file exists
cat ~/storage/downloads/termux_test.txt
ls /sdcard/Download/termux_test.txt

# Step 10: Clean up
rm ~/storage/downloads/termux_test.txt
```

### Exercise 4: File System Analysis

```bash
# Task: Analyze Termux file system with various commands

# Step 1: Find all Python files in PREFIX
find $PREFIX -name "*.py" | wc -l

# Step 2: Find all executables
find $PREFIX/bin -type f | wc -l

# Step 3: Get size breakdown of PREFIX subdirectories
du -sh $PREFIX/*

# Step 4: Find largest files in PREFIX
find $PREFIX -type f -exec du -h {} + 2>/dev/null | sort -rh | head -10

# Step 5: Count file types in PREFIX/bin
file $PREFIX/bin/* | grep -c "executable"
file $PREFIX/bin/* | grep -c "script"

# Step 6: Check library sizes
du -sh $PREFIX/lib

# Step 7: Find files modified in last 24 hours
find ~ -mtime -1 2>/dev/null

# Step 8: Get detailed info about bash
stat $PREFIX/bin/bash

# Step 9: Check file types of scripts
file $PREFIX/bin/* | grep "script" | head -10

# Step 10: Analyze cache directory
du -sh ~/.cache 2>/dev/null
du -sh $PREFIX/var/cache
```

### Exercise 5: Create Organized Directory Structure

```bash
# Task: Create a well-organized workspace

# Step 1: Create main directories
mkdir -p ~/workspace/{projects,scripts,tools,downloads,temp}
mkdir -p ~/workspace/projects/{python,bash,web}
mkdir -p ~/workspace/scripts/{utils,automation}

# Step 2: Verify structure
tree ~/workspace

# Step 3: Create some sample files
echo '#!/bin/bash\necho "Hello from Termux!"' > ~/workspace/scripts/hello.sh
echo 'print("Hello Python!")' > ~/workspace/projects/python/hello.py

# Step 4: Make script executable
chmod +x ~/workspace/scripts/hello.sh

# Step 5: Test the files
bash ~/workspace/scripts/hello.sh
python ~/workspace/projects/python/hello.py

# Step 6: Create README
cat > ~/workspace/README.md << 'EOF'
# My Termux Workspace

## Structure
- projects/  - Coding projects
- scripts/   - Shell scripts
- tools/     - Custom tools
- downloads/ - Downloaded files
- temp/      - Temporary files
EOF

# Step 7: Verify everything
ls -laR ~/workspace/
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Permission denied" accessing storage

```bash
# Cause: Storage permission not granted

# Solution 1: Run setup command
termux-setup-storage
# Press "Allow" on the popup

# Solution 2: Check permission manually
ls ~/storage/

# If still not working:
# Solution 3: Manual permission grant
# Android Settings → Apps → Termux → Permissions → Storage/Files → Allow

# Solution 4: Check if symlinks exist
ls -la ~/storage

# Solution 5: Recreate symlinks (if broken)
rm -rf ~/storage
termux-setup-storage
```

### Problem 2: "No such file or directory"

```bash
# Cause: Wrong path or directory doesn't exist

# Solution 1: Check current directory
pwd

# Solution 2: Use absolute paths
cd /data/data/com.termux/files/home

# Solution 3: Check if PREFIX is set
echo $PREFIX

# Solution 4: Verify directory exists
ls -ld /sdcard
ls -ld ~/storage

# Solution 5: Check for typos
# Use tab completion to avoid typos
cd ~/stora<TAB>  # Press Tab key
```

### Problem 3: Symlinks not working

```bash
# Cause: Broken symlinks or missing storage access

# Check symlink status
ls -la ~/storage/

# If symlinks are broken (show in red):
# Solution: Recreate storage setup
rm -rf ~/storage
termux-setup-storage

# Check symlink target
readlink ~/storage/downloads

# If target doesn't exist, check /sdcard access
ls /sdcard

# If /sdcard not accessible:
ls -la /storage/emulated/0/
```

### Problem 4: Cannot find installed package

```bash
# Cause: PATH not including $PREFIX/bin

# Solution 1: Check PATH
echo $PATH

# Should include: /data/data/com.termux/files/usr/bin

# Solution 2: Add to PATH manually
export PATH=$PATH:$PREFIX/bin

# Solution 3: Check if package is installed
pkg list-installed | grep <package-name>

# Solution 4: Reinstall package
pkg uninstall <package>
pkg install <package>

# Solution 5: Find where binary is installed
find $PREFIX -name "python*" -type f
```

### Problem 5: "tree: command not found"

```bash
# Cause: tree package not installed

# Solution: Install tree
pkg install tree

# Verify installation
which tree
tree --version
```

### Problem 6: Hidden files not showing

```bash
# Cause: Not using -a flag with ls

# Wrong:
ls ~          # Hidden files not shown

# Correct:
ls -a ~       # Show hidden files
ls -la ~      # Show hidden files with details

# List only hidden files:
ls -ld .*
ls -la | grep "^\."
```

### Problem 7: Disk space issues

```bash
# Check disk usage
df -h

# Check what's using space
du -sh $PREFIX/*
du -sh ~/*

# Clean package cache
pkg clean

# Clean user cache
rm -rf ~/.cache/*

# Remove unused packages
pkg autoclean

# Check large files
find ~ -size +100M 2>/dev/null
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Directory Tree Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📁 $PREFIX/bin/                  │
│   📁 $PREFIX/etc/                  │
│   📁 $PREFIX/lib/                  │
│   📁 ~/storage/                    │
│                                    │
│   FILE SYSTEM EXPLAINED            │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Comparison Style**
```
┌────────────────────────────────────┐
│  Standard Linux │ Termux           │
│  ───────────────┼───────────────── │
│  /bin           │ $PREFIX/bin      │
│  /etc           │ $PREFIX/etc      │
│  /home/user     │ $HOME            │
│                                    │
│  UNDERSTAND THE DIFFERENCE!        │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Visual Map**
```
┌────────────────────────────────────┐
│  🗺️ TERMUX FILE SYSTEM MAP         │
│                                    │
│  $PREFIX ──┬── bin/ (commands)     │
│            ├── etc/ (configs)      │
│            └── lib/ (libraries)    │
│                                    │
│  $HOME ────┬── .bashrc             │
│            └── storage/            │
│                                    │
│  Chapter 6 | T3rmuxk1ng            │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📁 Termux Full Course - Chapter 6: File System Structure

🔥 In this video you'll learn:
• Termux file system architecture explained
• $PREFIX directory structure detailed
• $HOME directory and hidden files
• Storage paths and symlinks
• Important commands: ls, tree, find, du, df
• Linux FHS comparison with Termux

⏱️ Timestamps:
0:00 - Introduction
0:45 - File System Basics
3:30 - $PREFIX Directory Structure
8:00 - $HOME Directory Structure
11:00 - Storage Paths and Symlinks
14:00 - Hidden Files & Navigation
16:30 - File System Commands
19:00 - Linux FHS Comparison
21:30 - Summary

📝 Key Commands from this video:
echo $PREFIX       # Show system path
echo $HOME         # Show home path
ls -la             # List all files
tree -L 2          # Directory tree
find . -name "*.py" # Search files
du -sh *           # Directory sizes
df -h              # Disk space
termux-setup-storage  # Grant storage access

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxFileSystem #T3rmuxk1ng #LinuxOnAndroid #TermuxTutorial 
#TermuxDirectory #LinuxFHS #TermuxCourse #TermuxHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux, termux file system, termux directory structure, termux prefix,
termux home directory, termux storage, termux tutorial, termux course,
termux hindi, termux commands, ls command, find command, tree command,
linux file system, linux fhs, filesystem hierarchy standard, 
termux path, termux environment, learn termux, t3rmuxk1ng,
termux for beginners, linux on android, android terminal
```

### Hashtags

```
#Termux #TermuxFileSystem #TermuxTutorial #TermuxHindi #TermuxCourse 
#LinuxOnAndroid #FileHierarchy #TermuxDirectory #T3rmuxk1ng 
#LearnTermux #TermuxStorage #LinuxFHS #TerminalCommands
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux Wiki - File System | https://wiki.termux.com/wiki/File_System |
| Termux Wiki - Storage | https://wiki.termux.com/wiki/Termux-setup-storage |
| FHS Standard | https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.html |
| Linux Directory Structure | https://www.pathname.com/fhs/ |

### Useful Commands Reference

| Task | Command |
|------|---------|
| Show current directory | `pwd` |
| Show system prefix | `echo $PREFIX` |
| Show home directory | `echo $HOME` |
| List all files | `ls -la` |
| Show directory tree | `tree -L 2` |
| Find files | `find . -name "pattern"` |
| Directory sizes | `du -sh *` |
| Disk space | `df -h` |
| File type | `file filename` |
| File details | `stat filename` |
| Grant storage access | `termux-setup-storage` |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 7, verify:

- [ ] Understand $PREFIX and $HOME environment variables
- [ ] Can navigate to important directories ($PREFIX/bin, $PREFIX/etc, ~)
- [ ] Know how to list hidden files with `ls -la`
- [ ] Understand storage symlinks and can access ~/storage/
- [ ] Successfully ran `termux-setup-storage` and have storage access
- [ ] Can use `tree` command to visualize directory structure
- [ ] Can search for files with `find` command
- [ ] Understand the difference between Termux and standard Linux file system
- [ ] Created organized directory structure in home folder

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 7: Environment Variables**

- What are environment variables?
- PATH variable importance
- Viewing all environment variables
- Creating custom variables
- Persistent variables in .bashrc
- Practical use cases for scripts

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
