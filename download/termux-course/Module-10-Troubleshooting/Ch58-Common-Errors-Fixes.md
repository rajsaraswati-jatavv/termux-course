# Chapter 58: Common Errors & Fixes

> **Module:** 10 - Troubleshooting  
> **Chapter:** 58 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed error categories and solutions |
| Error Reference | 50+ common errors with fixes |
| Debugging Guide | strace, logs, diagnostic techniques |
| Practice Exercises | Hands-on troubleshooting tasks |
| Advanced Section | SELinux, Path issues, Environment problems |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 58
Title: Common Errors & Fixes | Complete Troubleshooting Guide | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon aur aaj ka chapter bahut important hai - Common 
Errors & Fixes!

Har Termux user ko errors aate hain. Koi naya package install karo -
error. Koi script run karo - error. Storage access lo - error. Ye 
sab normal hai!

Lekin problem ye hai ki beginners error dekh ke dar jaate hain. Unhe 
pata nahi hota ki error ka matlab kya hai aur kaise fix karein.

Aaj hum seekhenge:
✓ 50+ common errors aur unka solution
✓ Error messages ko kaise padhein
✓ Debugging techniques
✓ Log files kaise check karein
✓ strace se debugging
✓ Environment aur Path issues

Ye chapter ek complete reference guide hai jo aapko har situation 
mein help karega. Bookmark karke rakhein!

To chaliye shuru karte hain!

---

[SECTION 1: UNDERSTANDING ERRORS - 1:00 to 3:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain ki error kya hoti hai aur kaise padhni hai.

Termux mein errors kaafi informative hoti hain. Har error message 
mein 3 parts hote hain:

1. ERROR TYPE - Kis category ka error hai
2. ERROR MESSAGE - Exactly kya galat hua
3. CONTEXT - Kab aur kahan hua

Example dekhein:

    E: Unable to locate package python3

Ye error mein:
- E: = Error indicator
- Unable to locate package = Error type (package not found)
- python3 = Package name jo nahi mila

Errors ko identify karne ke liye prefix dekhein:
- E: = Error (critical)
- W: = Warning (not critical but attention needed)
- I: = Information
- FAILED = Command failed
- Segmentation fault = Crash
- Permission denied = Access issue

Error categories:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX ERROR CATEGORIES                               │
├─────────────────────────────────────────────────────────────────────────┤
│ 1. Installation Errors    - Package install failures                    │
│ 2. Package Errors         - Dependency, version issues                  │
│ 3. Permission Errors      - Access denied, storage issues               │
│ 4. Network Errors         - Connection, download failures               │
│ 5. Storage Errors         - Space, file access problems                 │
│ 6. Python/pip Errors      - Module, installation issues                 │
│ 7. Compilation Errors     - Build failures, missing headers             │
│ 8. Environment Errors     - PATH, variables issues                      │
│ 9. Repository Errors      - Source list, mirror problems                │
│ 10. Runtime Errors        - Script execution failures                   │
└─────────────────────────────────────────────────────────────────────────┘

Har category ke errors alag tarike se handle hote hain.

---

[SECTION 2: INSTALLATION ERRORS - 3:30 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab shuru karte hain Installation Errors se.

[ERROR 1: Unable to locate package]

Sabse common error ye hai:

    E: Unable to locate package <package-name>

Causes:
1. Package name galat hai
2. Repository outdated hai
3. Internet nahi hai
4. Play Store wala Termux hai

Solutions:

    # Solution 1: Update repositories
    pkg update
    
    # Solution 2: Search correct package name
    pkg search <keyword>
    
    # Solution 3: Check internet
    ping -c 3 google.com
    
    # Solution 4: Check Termux version
    echo $TERMUX_VERSION
    # If < 0.118, reinstall from F-Droid

[ERROR 2: Package has no installation candidate]

    Package 'xyz' has no installation candidate

Ye error tab aata hai jab package available nahi hai ya repository 
add nahi hai.

    # Check available packages
    pkg search <name>
    
    # Add additional repositories if needed
    pkg install root-repo
    pkg install x11-repo

[ERROR 3: Dependency problems]

    dpkg: dependency problems prevent configuration...

Solution:

    # Fix broken dependencies
    pkg install -f
    
    # Or full repair
    pkg update && pkg upgrade -y
    pkg install -f

[ERROR 4: Sub-process returned an error code]

    E: Sub-process /usr/bin/dpkg returned an error code (1)

Solution:

    # Clean and rebuild
    rm -rf $PREFIX/var/lib/dpkg/lock*
    rm -rf $PREFIX/var/cache/apt/archives/*.deb
    pkg update
    pkg upgrade -y

[ERROR 5: Hash sum mismatch]

    Hash sum mismatch

Ye error corrupt downloads ki wajah se aata hai.

    # Solution
    pkg clean
    rm -rf $PREFIX/var/cache/apt/archives/*
    pkg update

---

[SECTION 3: PERMISSION ERRORS - 7:00 to 10:30]
─────────────────────────────────────────────────────────────────────────────

Permission errors Termux mein bahut common hain.

[ERROR 6: Permission denied]

    Permission denied

Causes:
- File executable nahi hai
- Storage permission nahi hai
- File read-only hai

Solutions:

    # Make file executable
    chmod +x script.sh
    
    # Grant storage permission
    termux-setup-storage
    
    # Check file permissions
    ls -la filename

[ERROR 7: Cannot access storage]

    ls: cannot access '/sdcard': Permission denied

Solution:

    # Run storage setup
    termux-setup-storage
    
    # Allow permission in popup
    
    # If still not working, check Android settings
    # Settings → Apps → Termux → Permissions → Storage = Allow

[ERROR 8: Read-only file system]

    Read-only file system

Ye error serious hai - Termux ka partition read-only ho gaya hai.

    # Check if Termux partition is healthy
    df -h
    
    # Restart Termux
    exit
    
    # If persistent, may need to reinstall
    # Backup data first!

[ERROR 9: Operation not permitted]

    Operation not permitted

Ye error usually root-requiring operations ke liye aata hai.

    # Check if root is required
    # Some operations need root access
    
    # If you have root
    su
    
    # Otherwise, find alternative method

[ERROR 10: mkdir cannot create directory]

    mkdir: cannot create directory 'xyz': Permission denied

Solution:

    # Check current directory permissions
    ls -la .
    
    # You might be in a read-only location
    # Navigate to home directory
    cd ~
    mkdir xyz

---

[SECTION 4: NETWORK ERRORS - 10:30 to 13:30]
─────────────────────────────────────────────────────────────────────────────

Network errors kabhi bhi aa sakte hain.

[ERROR 11: Temporary failure resolving]

    Temporary failure resolving 'packages.termux.dev'

Ye DNS error hai.

Solution:

    # Check internet connection
    ping -c 3 8.8.8.8
    
    # If ping works but DNS fails
    # Change DNS settings
    
    # Use Google DNS
    echo "nameserver 8.8.8.8" > $PREFIX/etc/resolv.conf
    echo "nameserver 8.8.4.4" >> $PREFIX/etc/resolv.conf

[ERROR 12: Connection refused]

    Connection refused

Ye error tab aata hai jab server reachable hai lekin port band hai.

    # Check if service is running
    # Example: for SSH
    pgrep sshd
    
    # Start service
    sshd

[ERROR 13: Connection timed out]

    Connection timed out

Causes:
- Firewall blocking
- Server down
- Network slow

Solution:

    # Try different mirror
    # Edit sources.list
    nano $PREFIX/etc/apt/sources.list
    
    # Add alternative mirror
    deb https://grimler.se/termux-packages-24 stable main

[ERROR 14: SSL certificate problem]

    SSL certificate problem: unable to get local issuer certificate

Solution:

    # Update CA certificates
    pkg install ca-certificates
    pkg upgrade ca-certificates

[ERROR 15: Network is unreachable]

    Network is unreachable

Solution:

    # Check all network interfaces
    ifconfig 2>/dev/null || ip addr
    
    # Check if WiFi is connected
    termux-wifi-connectioninfo

---

[SECTION 5: STORAGE ERRORS - 13:30 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Storage errors critical hain - data loss bhi ho sakta hai.

[ERROR 16: No space left on device]

    No space left on device

Solution:

    # Check disk usage
    df -h
    
    # Clean package cache
    pkg clean
    
    # Remove unused packages
    pkg autoclean
    
    # Find big files
    du -sh ~/* 2>/dev/null | sort -rh | head -10

[ERROR 17: Input/output error]

    Input/output error

Ye serious error hai - storage corrupt ho sakta hai.

    # Restart phone first
    # If persists, backup data and reinstall Termux

[ERROR 18: File exists]

    File exists

Solution:

    # Remove existing file
    rm -f filename
    
    # Or force overwrite in command
    cp -f source dest

[ERROR 19: Too many open files]

    Too many open files

Solution:

    # Check open files limit
    ulimit -n
    
    # Increase limit
    ulimit -n 8192

[ERROR 20: Disk quota exceeded]

    Disk quota exceeded

Solution:

    # Termux has no quota by default
    # This might be Android system limit
    # Clean up storage
    pkg clean
    rm -rf ~/.cache/*

---

[SECTION 6: PYTHON/PIP ERRORS - 16:00 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Python errors developers ke liye common hain.

[ERROR 21: Module not found]

    ModuleNotFoundError: No module named 'xyz'

Solution:

    # Install missing module
    pip install <module-name>
    
    # Or for Python 3
    pip3 install <module-name>

[ERROR 22: pip not found]

    pip: command not found

Solution:

    # Install pip
    pkg install python
    # pip comes with Python in Termux

[ERROR 23: Permission denied in pip]

    ERROR: Could not install packages due to an OSError: Permission denied

Solution:

    # Use --user flag
    pip install --user <package>
    
    # In Termux, this usually shouldn't happen
    # If it does, check permissions
    ls -la $PREFIX/lib/python*/

[ERROR 24: Command errored out with exit status 1]

    ERROR: Command errored out with exit status 1

Ye error compilation failure ki wajah se aata hai.

Solution:

    # Install build dependencies
    pkg install build-essential libffi openssl
    
    # Then retry pip install
    pip install <package>

[ERROR 25: SSL module is not available]

    SSL module is not available

Solution:

    # Install OpenSSL
    pkg install openssl libssl
    
    # Reinstall Python if needed
    pkg reinstall python

[ERROR 26: Wheel failed to build]

    Failed building wheel for <package>

Solution:

    # Install build dependencies
    pkg install python-cryptography
    pkg install libffi
    pkg install openssl
    
    # Update pip
    pip install --upgrade pip wheel setuptools

[ERROR 27: Python version conflict]

    ERROR: Package requires a different Python

Solution:

    # Check Python version
    python --version
    
    # Install compatible package version
    pip install <package>==<version>

---

[SECTION 7: COMPILATION ERRORS - 19:30 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Compilation errors complex hain lekin fix ho sakte hain.

[ERROR 28: Command not found]

    make: command not found

Solution:

    pkg install make
    pkg install build-essential

[ERROR 29: gcc not found]

    gcc: command not found

Solution:

    pkg install clang
    # Termux uses clang instead of gcc

[ERROR 30: Header file not found]

    fatal error: xyz.h: No such file or directory

Solution:

    # Search for package containing header
    pkg search <library-name>
    
    # Install development package
    pkg install <library>-dev

[ERROR 31: Library not found]

    cannot find -l<library>

Solution:

    # Find library package
    pkg search <library>
    
    # Install library
    pkg install <library>

[ERROR 32: C compiler cannot create executables]

    C compiler cannot create executables

Solution:

    # Install complete build toolchain
    pkg install build-essential clang

[ERROR 33: pkg-config not found]

    Package 'xyz' not found

Solution:

    pkg install pkg-config
    # Also install the required library

---

[SECTION 8: DEBUGGING TECHNIQUES - 22:00 to 25:30]
─────────────────────────────────────────────────────────────────────────────

Ab debugging techniques seekhte hain.

[LOG FILES]

Termux mein log files important information deti hain.

    # System logs (requires root)
    logcat
    
    # Termux-specific logs
    ls $PREFIX/var/log/
    
    # Apt/dpkg logs
    cat $PREFIX/var/log/apt/history.log
    cat $PREFIX/var/log/dpkg.log
    
    # User command history
    cat ~/.bash_history

[VERBOSE OUTPUT]

Commands ko verbose mode mein run karke details dekhein:

    # Verbose apt
    apt install -v <package>
    
    # Verbose pip
    pip install -v <package>
    
    # Debug mode
    bash -x script.sh

[STRACE DEBUGGING]

strace powerful debugging tool hai.

    # Install strace
    pkg install strace
    
    # Trace a command
    strace ls
    
    # Trace with file operations only
    strace -e trace=file ls
    
    # Save to file
    strace -o trace.log <command>
    
    # Find file access issues
    strace -e openat python script.py 2>&1 | grep -i "no such"

[PROCESS DEBUGGING]

    # List all processes
    ps aux
    
    # Find specific process
    pgrep -a python
    
    # Process details
    cat /proc/<PID>/status
    cat /proc/<PID>/cmdline

[NETWORK DEBUGGING]

    # DNS lookup
    nslookup google.com
    
    # Trace route
    pkg install traceroute
    traceroute google.com
    
    # Port check
    pkg install nmap
    nmap localhost

---

[SECTION 9: ENVIRONMENT & PATH ISSUES - 25:30 to 28:00]
─────────────────────────────────────────────────────────────────────────────

Environment issues tricky hote hain.

[ERROR 34: Command not found (PATH issue)]

    command not found

But package is installed!

Solution:

    # Check PATH
    echo $PATH
    
    # Should include $PREFIX/bin
    # If missing:
    export PATH=$PREFIX/bin:$PREFIX/bin/applets:$PATH
    
    # Add to .bashrc permanently
    echo 'export PATH=$PREFIX/bin:$PREFIX/bin/applets:$PATH' >> ~/.bashrc

[ERROR 35: Environment variable not set]

    $VARIABLE: unbound variable

Solution:

    # Set variable
    export VARIABLE=value
    
    # Check if set
    echo $VARIABLE
    
    # List all environment variables
    env

[ERROR 36: Shared library not found]

    error while loading shared libraries: libxyz.so

Solution:

    # Find package
    pkg search libxyz
    
    # Or search all libraries
    find $PREFIX/lib -name "libxyz*"
    
    # Update library cache
    ldconfig

[ERROR 37: Locale not set]

    locale: Cannot set LC_ALL to default locale

Solution:

    # Install locales
    pkg install locales
    
    # Generate locale
    locale-gen en_US.UTF-8

[ERROR 38: Wrong shell]

    Not in the same shell

Solution:

    # Check current shell
    echo $SHELL
    echo $0
    
    # Switch to bash
    bash
    
    # Make bash default
    chsh -s bash

---

[SECTION 10: REPOSITORY ISSUES - 28:00 to 30:30]
─────────────────────────────────────────────────────────────────────────────

Repository issues packages ko inaccessible bana dete hain.

[ERROR 39: Repository not found]

    The repository is not signed

Solution:

    # Update keys
    pkg update
    
    # If fails, reset repositories
    rm $PREFIX/etc/apt/sources.list.d/*

[ERROR 40: GPG error]

    GPG error: The following signatures couldn't be verified

Solution:

    # Update with key fix
    pkg update --fix-missing
    
    # Or full reset
    rm -rf $PREFIX/etc/apt/sources.list.d/*
    pkg update

[ERROR 41: 404 Not Found]

    404 Not Found

Solution:

    # Repository URL changed
    # Update sources
    pkg update
    
    # If persists, edit sources.list
    nano $PREFIX/etc/apt/sources.list
    
    # Correct URLs:
    deb https://packages.termux.dev/termux-main stable main

[ERROR 42: Mirror issues]

    Mirror sync in progress

Solution:

    # Wait for mirror to sync
    # Or use different mirror
    
    # Edit sources.list
    nano $PREFIX/etc/apt/sources.list

---

[SECTION 11: SELINUX ISSUES - 30:30 to 32:00]
─────────────────────────────────────────────────────────────────────────────

SELinux issues advanced level ke hain.

[ERROR 43: SELinux preventing access]

    AVC denied: Operation not permitted

SELinux Android mein security enforce karta hai.

Check SELinux mode:

    getenforce
    # Output: Enforcing, Permissive, or Disabled

Solutions:

    # For rooted devices
    su -c "setenforce 0"  # Permissive mode
    
    # Or use SELinux mode changer apps
    
    # For non-rooted devices
    # Some operations may not work
    # Find alternative methods

---

[SECTION 12: MORE COMMON ERRORS - 32:00 to 35:30]
─────────────────────────────────────────────────────────────────────────────

Aur bhi common errors dekhein:

[ERROR 44: Termux exiting immediately]

Termux opens and closes instantly.

Solution:

    # Clear Termux data
    Settings → Apps → Termux → Clear Data
    
    # Reinstall from F-Droid

[ERROR 45: Process completed (signal 9)]

    Process completed (signal 9)

Ye OOM Killer ka result hai.

Solution:

    # Reduce memory usage
    # Close other apps
    # Check swap
    free -h

[ERROR 46: Zombie processes]

    defunct process

Solution:

    # Find zombie processes
    ps aux | grep -w Z
    
    # Kill parent process
    kill -9 <PPID>

[ERROR 47: Broken pipe]

    Broken pipe

Solution:

    # Usually harmless
    # Occurs when pipe recipient closes

[ERROR 48: Address already in use]

    Address already in use

Solution:

    # Find process using port
    netstat -tulpn | grep :<port>
    
    # Kill process
    kill -9 <PID>

[ERROR 49: Segmentation fault]

    Segmentation fault (core dumped)

Solution:

    # Program crashed - bug in code
    # Update/reinstall package
    pkg reinstall <package>
    
    # Check memory
    free -h

[ERROR 50: Bus error]

    Bus error (core dumped)

Solution:

    # Memory alignment issue
    # Usually a bug in the program
    # Report to package maintainer

[ERROR 51: Text file busy]

    Text file busy

Solution:

    # File is being executed
    # Stop running instance first
    pkill <process-name>

[ERROR 52: Device or resource busy]

    Device or resource busy

Solution:

    # Find what's using it
    lsof | grep <name>
    
    # Kill process
    kill -9 <PID>

---

[SECTION 13: QUICK FIX REFERENCE - 35:30 to 37:30]
─────────────────────────────────────────────────────────────────────────────

Ab main ek quick reference table deta hoon:

┌─────────────────────────────────────────────────────────────────────────┐
│                    QUICK ERROR FIX REFERENCE                             │
├─────────────────────────────────────────────────────────────────────────┤
│ ERROR                           │ FIX                                    │
├─────────────────────────────────┼────────────────────────────────────────┤
│ Unable to locate package        │ pkg update                             │
│ Permission denied               │ chmod +x / termux-setup-storage        │
│ No space left                   │ pkg clean && rm -rf ~/.cache/*         │
│ Connection refused              │ Check if service is running            │
│ SSL certificate error           │ pkg install ca-certificates            │
│ Command not found               │ pkg install <package>                  │
│ Module not found                │ pip install <module>                   │
│ Dependency problems             │ pkg install -f                         │
│ Hash sum mismatch               │ pkg clean && pkg update                │
│ Broken pipe                     │ Usually harmless                       │
│ Segmentation fault              │ pkg reinstall <package>                │
│ Process killed (signal 9)       │ Reduce memory usage                    │
│ Address in use                  │ kill $(lsof -t -i:<port>)              │
│ locale error                    │ pkg install locales                    │
│ PATH issue                      │ export PATH=$PREFIX/bin:$PATH          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 14: PREVENTION TIPS - 37:30 to 39:00]
─────────────────────────────────────────────────────────────────────────────

Errors se bachne ke liye prevention tips:

1. ✅ Regular updates
   pkg update && pkg upgrade -y

2. ✅ F-Droid se install karein (Play Store nahi)

3. ✅ Storage permissions time pe le lein

4. ✅ Backup regularly

5. ✅ Correct package names use karein

6. ✅ Dependencies pehle install karein

7. ✅ Log files check karein

8. ✅ Internet connection verify karein

9. ✅ Sufficient storage rakhein

10. ✅ Documentation padhein

---

[SECTION 15: SUMMARY - 39:00 to 40:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 58 complete! Let's summarize:

✅ Error categories samjhein - 10 types
✅ Installation errors - 5 fixes
✅ Permission errors - 5 fixes  
✅ Network errors - 5 fixes
✅ Storage errors - 5 fixes
✅ Python/pip errors - 7 fixes
✅ Compilation errors - 6 fixes
✅ Debugging techniques - logs, strace
✅ Environment issues - 5 fixes
✅ Repository issues - 4 fixes
✅ SELinux issues - solutions
✅ 50+ total errors covered!

Key debugging commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    DEBUGGING COMMANDS                                    │
├─────────────────────────────────────────────────────────────────────────┤
│ strace <command>         │ Trace system calls                           │
│ logcat                   │ Android system logs                          │
│ cat $PREFIX/var/log/*    │ Termux logs                                  │
│ pkg install -f           │ Fix broken packages                          │
│ bash -x script.sh        │ Debug bash script                            │
│ pip install -v <pkg>     │ Verbose pip install                          │
│ find $PREFIX -name "*lib"│ Find library files                           │
│ lsof | grep <name>       │ Find open files                              │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 59 mein hum seekhenge:
- Termux performance optimization
- Memory management
- CPU optimization
- Storage cleanup

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Thank you for watching! See you in Chapter 59!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Error Categories Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX ERROR CLASSIFICATION                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    CRITICAL ERRORS                               │   │
│   │   (Immediate attention required)                                │   │
│   │                                                                  │   │
│   │   • Segmentation fault     • Bus error                          │   │
│   │   • Storage corruption     • OOM Kill (signal 9)                │   │
│   │   • Library loading fail   • Disk I/O error                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    RECOVERABLE ERRORS                            │   │
│   │   (Can be fixed with commands)                                  │   │
│   │                                                                  │   │
│   │   • Package not found      • Dependency issues                  │   │
│   │   • Permission denied      • Network timeout                    │   │
│   │   • Path not found         • Config errors                      │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    WARNING MESSAGES                              │   │
│   │   (Non-critical but should address)                             │   │
│   │                                                                  │   │
│   │   • Deprecated commands    • Outdated packages                  │   │
│   │   • Missing optional deps  • Config suggestions                 │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Installation Errors Deep Dive

#### A. Package Installation Flow

```
pkg install <package> Flow:
│
├── 1. Check Repository
│   └── FAIL → "Unable to locate package"
│
├── 2. Download Package
│   └── FAIL → "Network error" / "Hash sum mismatch"
│
├── 3. Verify Dependencies
│   └── FAIL → "Dependency problems"
│
├── 4. Unpack Package
│   └── FAIL → "Disk full" / "I/O error"
│
├── 5. Configure Package
│   └── FAIL → "Configuration error"
│
└── SUCCESS
```

#### B. Common Installation Error Solutions

```bash
# Error: Unable to locate package
# Solution flow:

# Step 1: Update repositories
pkg update

# Step 2: Search for correct package name
pkg search <keyword>

# Step 3: Check if in correct repository
pkg list-installed | grep repository

# Step 4: Add additional repos if needed
pkg install root-repo    # For root packages
pkg install x11-repo     # For GUI packages

# Step 5: Check internet
ping -c 3 packages.termux.dev

# Step 6: Verify Termux version (F-Droid vs Play Store)
echo $TERMUX_VERSION
# Should be >= 0.118
```

```bash
# Error: Dependency problems
# Solution:

# Fix broken dependencies
pkg install -f

# Or manual fix
apt --fix-broken install

# Full repair
dpkg --configure -a
pkg update && pkg upgrade -y
```

```bash
# Error: Hash sum mismatch
# Solution:

# Clean cache completely
rm -rf $PREFIX/var/cache/apt/archives/*
rm -rf $PREFIX/var/lib/apt/lists/*

# Update fresh
pkg update
```

### 3. Permission Errors Solutions

#### A. Storage Permission Issues

```bash
# Problem: Cannot access /sdcard

# Solution 1: Request permission
termux-setup-storage

# Solution 2: Manual permission grant
# Android Settings → Apps → Termux → Permissions → Files/Media = Allow

# Solution 3: Check if permission granted
ls -la ~/storage/
# Should show symlinks to sdcard folders

# Solution 4: Check SELinux (if applicable)
getenforce
# If Enforcing and issues persist, may need to adjust

# Solution 5: Alternative access via termux-api
termux-storage-get <destination> <source>
```

#### B. File Permission Issues

```bash
# Problem: Permission denied when running script

# Check current permissions
ls -la script.sh

# Add execute permission
chmod +x script.sh

# If still fails, check ownership
chown $(whoami):$(whoami) script.sh

# For directories
chmod 755 directory/

# Recursive permission change
chmod -R 755 directory/
```

#### C. Root Permission Issues

```bash
# Check if root available
su -c "id"

# Common root errors:
# 1. "su: not found" - No root installed
# 2. "Permission denied" - Root denied access
# 3. "$ instead of #" - Not in root shell

# Fix su binary not found
# Install su binary or use Magisk

# For Termux root packages
pkg install root-repo
pkg update
```

### 4. Network Error Solutions

#### A. DNS Resolution Issues

```bash
# Problem: Cannot resolve hostnames

# Test DNS
nslookup google.com

# If fails, set DNS manually
echo "nameserver 8.8.8.8" > $PREFIX/etc/resolv.conf
echo "nameserver 8.8.4.4" >> $PREFIX/etc/resolv.conf

# Test again
ping -c 3 google.com
```

#### B. SSL/TLS Certificate Issues

```bash
# Problem: SSL certificate errors

# Install/update certificates
pkg install ca-certificates
pkg upgrade ca-certificates

# For pip SSL issues
pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org <package>

# For wget SSL issues
wget --no-check-certificate <url>
```

#### C. Connection Issues

```bash
# Test connectivity
ping -c 3 8.8.8.8      # Test IP connectivity
ping -c 3 google.com   # Test DNS + connectivity

# Check if port is open
pkg install nmap
nmap -p 80 packages.termux.dev

# Use alternative mirror if primary is slow
# Edit $PREFIX/etc/apt/sources.list
deb https://grimler.se/termux-packages-24 stable main
```

### 5. Storage Error Solutions

#### A. Disk Space Issues

```bash
# Check disk usage
df -h

# Termux specific location
df -h /data/data/com.termux

# Find large directories
du -sh $PREFIX/* 2>/dev/null | sort -rh | head -10
du -sh ~/* 2>/dev/null | sort -rh | head -10

# Cleanup commands
pkg clean                           # Package cache
rm -rf $PREFIX/var/cache/apt/archives/*.deb
rm -rf ~/.cache/*                   # User cache
pkg autoclean                       # Obsolete packages

# Python cache cleanup
find ~ -type d -name __pycache__ -exec rm -rf {} + 2>/dev/null

# Node.js cache cleanup
npm cache clean --force 2>/dev/null

# Find files larger than 50MB
find ~ -type f -size +50M 2>/dev/null
```

#### B. File System Issues

```bash
# Check if read-only
touch ~/test_write
rm ~/test_write

# If fails, file system may be corrupted
# Solution: Restart device

# Find open files (if cannot delete)
pkg install lsof
lsof | grep <filename>

# Force unmount (requires root)
su -c "umount -l <mountpoint>"
```

### 6. Python/pip Error Solutions

#### A. Module Installation Issues

```bash
# Error: ModuleNotFoundError
# Solution:
pip install <module>
pip3 install <module>  # Explicitly Python 3

# Install specific version
pip install <module>==1.2.3

# Install from git
pip install git+https://github.com/user/repo.git

# Install in user space
pip install --user <module>

# Force reinstall
pip install --force-reinstall <module>
```

#### B. Compilation Errors for pip Packages

```bash
# Many Python packages need compilation
# Install build dependencies first

# Common build dependencies
pkg install build-essential clang make
pkg install libffi openssl libffi-dev
pkg install python-cryptography

# Update pip tools
pip install --upgrade pip wheel setuptools

# For packages needing specific libraries
pkg search <library>
pkg install <library>-dev

# Example: Install psycopg2 (PostgreSQL adapter)
pkg install postgresql libpq
pip install psycopg2-binary

# Example: Install Pillow (image processing)
pkg install libjpeg-turbo libpng zlib
pip install Pillow
```

#### C. Virtual Environment Issues

```bash
# Create virtual environment
python -m venv myenv

# Activate
source myenv/bin/activate

# If venv fails
pip install virtualenv
virtualenv myenv
source myenv/bin/activate

# Deactivate
deactivate
```

### 7. Compilation Error Solutions

#### A. Compiler Issues

```bash
# Termux uses clang, not gcc
# If makefile expects gcc

# Create symlink
ln -s $PREFIX/bin/clang $PREFIX/bin/gcc

# Or set CC environment variable
export CC=clang

# Install full build toolchain
pkg install build-essential

# This includes:
# - clang (C compiler)
# - make
# - cmake
# - autoconf
# - automake
# - and more
```

#### B. Header/Library Issues

```bash
# Error: xyz.h not found

# Search for header package
pkg search <library>
# Usually named <library>-dev or lib<name>-dev

# Example: Missing zlib.h
pkg search zlib
pkg install zlib-dev

# Find which package contains a file
pkg install apt-file
apt-file update
apt-file search <filename>

# List files in a package
pkg show <package>
dpkg -L <package>
```

#### C. Library Path Issues

```bash
# Error: cannot find -l<library>

# Check library exists
find $PREFIX -name "lib<name>*"

# Update library cache
ldconfig

# Check library path
echo $LD_LIBRARY_PATH

# Add custom library path
export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH

# Check what libraries a binary needs
readelf -d <binary> | grep NEEDED
ldd <binary>
```

### 8. Debugging Techniques

#### A. Using strace

```bash
# Install strace
pkg install strace

# Basic trace
strace <command>

# Trace only specific system calls
strace -e trace=open,openat,read,write <command>

# Trace file operations
strace -f -e trace=file <command>

# Trace network operations
strace -e trace=network <command>

# Save output to file
strace -o debug.log <command>

# Follow child processes
strace -f <command>

# Count system calls
strace -c <command>

# Common patterns:

# Find file not found errors
strace <command> 2>&1 | grep "No such"

# Find permission denied errors
strace <command> 2>&1 | grep "Permission denied"

# Find library loading issues
strace -e trace=openat <command> 2>&1 | grep "\.so"
```

#### B. Log File Analysis

```bash
# Termux logs location
ls -la $PREFIX/var/log/

# APT history (package changes)
cat $PREFIX/var/log/apt/history.log

# APT term log (apt output)
cat $PREFIX/var/log/apt/term.log

# DPKG log (package operations)
cat $PREFIX/var/log/dpkg.log

# Android logcat (system logs)
logcat -d                         # Dump and exit
logcat -d | grep -i termux        # Filter for Termux
logcat -d | grep -i error         # Filter errors

# User command history
cat ~/.bash_history

# Shell session log
script -a session.log
# ... run commands ...
exit
cat session.log
```

#### C. Process Debugging

```bash
# List all processes
ps aux
ps -ef

# Process tree
pkg install psmisc
pstree -p

# Find specific process
pgrep -a <name>
ps aux | grep <name>

# Process details
cat /proc/<PID>/status
cat /proc/<PID>/cmdline
cat /proc/<PID>/maps     # Memory map
cat /proc/<PID>/fd/      # Open files

# Real-time monitoring
top
htop

# Process memory usage
pmap <PID>

# Trace process signals
strace -p <PID>
```

#### D. Network Debugging

```bash
# DNS lookup
nslookup <domain>
dig <domain>

# Connectivity test
ping -c 3 <host>

# Trace route
traceroute <host>

# Port scanner
nmap <host>

# Open connections
netstat -tulpn
ss -tulpn

# Packet capture (requires root)
tcpdump -i any -w capture.pcap

# HTTP debugging
curl -v <url>
wget --debug <url>
```

### 9. Environment & Path Issues

#### A. PATH Configuration

```bash
# Check current PATH
echo $PATH

# Correct Termux PATH should include:
# /data/data/com.termux/files/usr/bin

# Add to PATH temporarily
export PATH=$PREFIX/bin:$PREFIX/bin/applets:$PATH

# Add permanently to .bashrc
echo 'export PATH=$PREFIX/bin:$PREFIX/bin/applets:$PATH' >> ~/.bashrc
source ~/.bashrc

# If PATH is completely broken
# Use absolute path
/data/data/com.termux/files/usr/bin/nano ~/.bashrc
```

#### B. Environment Variables

```bash
# List all environment variables
env
printenv

# Check specific variable
echo $VARIABLE_NAME

# Set variable
export MY_VAR="value"

# Unset variable
unset MY_VAR

# Common Termux variables
echo $PREFIX        # /data/data/com.termux/files/usr
echo $HOME          # /data/data/com.termux/files/home
echo $TERMUX_VERSION
echo $TERM          # xterm-256color
echo $SHELL         # /data/data/com.termux/files/usr/bin/bash

# Add to .bashrc permanently
echo 'export MY_VAR="value"' >> ~/.bashrc
```

#### C. Locale Issues

```bash
# Error: locale not supported

# Install locales
pkg install locales

# Generate locale
locale-gen en_US.UTF-8

# Set locale
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8

# Add to .bashrc
echo 'export LANG=en_US.UTF-8' >> ~/.bashrc
echo 'export LC_ALL=en_US.UTF-8' >> ~/.bashrc

# Verify
locale
```

### 10. Repository Issues Solutions

#### A. Repository Configuration

```bash
# Repository files location
ls $PREFIX/etc/apt/sources.list
ls $PREFIX/etc/apt/sources.list.d/

# Main repository content
cat $PREFIX/etc/apt/sources.list
# Should be:
# deb https://packages.termux.dev/termux-main stable main

# Additional repositories
pkg install root-repo    # Root packages
pkg install x11-repo     # GUI packages

# Manual repository add
echo "deb https://packages.termux.dev/termux-x11 x11 main" > $PREFIX/etc/apt/sources.list.d/x11.list
pkg update
```

#### B. Repository Key Issues

```bash
# If GPG errors occur

# Update to get new keys
pkg update

# If still failing
rm -rf $PREFIX/etc/apt/sources.list.d/*
pkg update

# Manual key import (rarely needed)
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <KEY_ID>
```

#### C. Mirror Issues

```bash
# If main repository is slow/unreachable

# Alternative mirrors:
# Primary: https://packages.termux.dev/termux-main
# Mirror 1: https://grimler.se/termux-packages-24
# Mirror 2: https://termux.librehat.com/apt/termux-main

# Edit sources.list
nano $PREFIX/etc/apt/sources.list

# Change to mirror
deb https://grimler.se/termux-packages-24 stable main

# Update
pkg update
```

### 11. SELinux Issues

```bash
# Check SELinux status
getenforce
# Enforcing = Blocking
# Permissive = Warning only
# Disabled = Off

# Check SELinux denials
logcat -d | grep -i avc

# For rooted devices
su -c "setenforce 0"   # Set to Permissive
su -c "setenforce 1"   # Set to Enforcing

# Check context of Termux files
su -c "ls -Z /data/data/com.termux"

# Common Termux context
# u:object_r:app_data_file:s0:c512,c768
```

### 12. 50+ Common Errors Quick Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ERROR #1-10: INSTALLATION & PACKAGES                  │
├─────────────────────────────────────────────────────────────────────────┤
│ #1  │ Unable to locate package    │ pkg update; pkg search <name>       │
│ #2  │ No installation candidate   │ Check repo; add correct repo        │
│ #3  │ Dependency problems         │ pkg install -f                      │
│ #4  │ Sub-process error code      │ rm lock files; pkg update           │
│ #5  │ Hash sum mismatch           │ pkg clean; rm cache; pkg update     │
│ #6  │ Package is already newest   │ pkg upgrade <package>               │
│ #7  │ Package broken              │ pkg install --reinstall <pkg>       │
│ #8  │ Held packages               │ pkg unhold <package>                │
│ #9  │ Version conflict            │ Install specific version            │
│ #10 │ Repository not signed       │ pkg update; check sources.list      │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #11-20: PERMISSIONS                             │
├─────────────────────────────────────────────────────────────────────────┤
│ #11 │ Permission denied           │ chmod +x; termux-setup-storage      │
│ #12 │ Cannot access /sdcard       │ termux-setup-storage; check Android │
│ #13 │ Read-only file system       │ Restart device; check disk health   │
│ #14 │ Operation not permitted     │ May need root; find alternative     │
│ #15 │ mkdir permission denied     │ cd ~; mkdir in home                 │
│ #16 │ Cannot delete file          │ Check if open: lsof | grep <file>   │
│ #17 │ chown permission denied     │ Need root for system files          │
│ #18 │ Cannot change permissions   │ Check file ownership                │
│ #19 │ Access denied (SELinux)     │ Check getenforce; adjust if root    │
│ #20 │ Storage permission popup    │ Settings → Apps → Termux → Perms    │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #21-30: NETWORK                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ #21 │ Temporary failure resolving │ Check DNS; set 8.8.8.8 manually     │
│ #22 │ Connection refused          │ Check if service running            │
│ #23 │ Connection timed out        │ Check firewall; try mirror          │
│ #24 │ SSL certificate error       │ pkg install ca-certificates         │
│ #25 │ Network unreachable         │ Check WiFi; ifconfig                │
│ #26 │ Host unreachable            │ ping IP; check routing              │
│ #27 │ 404 Not Found               │ Update sources.list URL             │
│ #28 │ 403 Forbidden               │ Check if IP blocked; use VPN        │
│ #29 │ Connection reset            │ Retry; check server status          │
│ #30 │ Proxy error                 │ Check proxy settings                │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #31-40: STORAGE & FILES                         │
├─────────────────────────────────────────────────────────────────────────┤
│ #31 │ No space left on device     │ pkg clean; rm -rf ~/.cache/*        │
│ #32 │ Input/output error          │ Restart; check storage health       │
│ #33 │ File exists                 │ rm -f file; or use -f flag          │
│ #34 │ Too many open files         │ ulimit -n 8192                      │
│ #35 │ Disk quota exceeded         │ Clean up; delete large files        │
│ #36 │ File not found              │ Check path; use find command        │
│ #37 │ Not a directory             │ Check if path is correct            │
│ #38 │ Is a directory              │ Remove trailing slash               │
│ #39 │ Cross-device link           │ Move instead of rename              │
│ #40 │ Text file busy              │ pkill process using file            │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #41-50: PYTHON & PIP                            │
├─────────────────────────────────────────────────────────────────────────┤
│ #41 │ ModuleNotFoundError         │ pip install <module>                │
│ #42 │ pip: command not found      │ pkg install python                  │
│ #43 │ Permission denied (pip)     │ pip install --user <pkg>            │
│ #44 │ Command errored exit 1      │ Install build deps                  │
│ #45 │ SSL module unavailable      │ pkg install openssl libssl          │
│ #46 │ Wheel build failed          │ pkg install build-essential libffi  │
│ #47 │ Python version conflict     │ Install compatible version          │
│ #48 │ No matching distribution    │ Check Python version; platform      │
│ #49 │ Requirements.txt error      │ Install deps one by one             │
│ #50 │ Virtual env error           │ pip install virtualenv; recreate    │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #51-60: COMPILATION                             │
├─────────────────────────────────────────────────────────────────────────┤
│ #51 │ make: command not found     │ pkg install make build-essential    │
│ #52 │ gcc: command not found      │ pkg install clang (not gcc)         │
│ #53 │ Header file not found       │ pkg install <lib>-dev               │
│ #54 │ Library not found           │ pkg search <lib>; pkg install       │
│ #55 │ C compiler cannot create    │ pkg install build-essential clang   │
│ #56 │ pkg-config not found        │ pkg install pkg-config              │
│ #57 │ Undefined reference         │ Add library to LDFLAGS              │
│ #58 │ Multiple definition         │ Check for duplicate object files    │
│ #59 │ Assembler error             │ Check CPU architecture              │
│ #60 │ Linker error                │ Check library paths; ldconfig       │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #61-70: PROCESS & MEMORY                        │
├─────────────────────────────────────────────────────────────────────────┤
│ #61 │ Segmentation fault          │ Update package; check code          │
│ #62 │ Bus error                   │ Memory alignment issue; report bug  │
│ #63 │ Process completed (sig 9)   │ OOM kill; reduce memory usage       │
│ #64 │ Process completed (sig 11)  │ Segfault; reinstall package         │
│ #65 │ Zombie process              │ Kill parent process                 │
│ #66 │ Address already in use      │ kill $(lsof -t -i:<port>)           │
│ #67 │ Broken pipe                 │ Usually harmless                    │
│ #68 │ Device or resource busy     │ lsof | grep; kill process           │
│ #69 │ Cannot allocate memory      │ free -h; close apps; add swap       │
│ #70 │ Out of memory               │ Increase swap; reduce usage         │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #71-80: ENVIRONMENT & PATH                      │
├─────────────────────────────────────────────────────────────────────────┤
│ #71 │ command not found (PATH)    │ export PATH=$PREFIX/bin:$PATH       │
│ #72 │ Variable unbound            │ export VAR=value                    │
│ #73 │ Shared library not found    │ pkg install library; ldconfig       │
│ #74 │ Locale not set              │ pkg install locales; locale-gen     │
│ #75 │ Wrong shell                 │ chsh -s bash                        │
│ #76 │ cd: too many arguments      │ Quote path with spaces              │
│ #77 │ Syntax error in script      │ Use bash -n script.sh to check      │
│ #78 │ Exec format error           │ Wrong binary architecture           │
│ #79 │ Bad interpreter             │ Check shebang line; dos2unix        │
│ #80 │ Too many arguments          │ Split command; use xargs            │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #81-90: REPOSITORY & SOURCES                    │
├─────────────────────────────────────────────────────────────────────────┤
│ #81 │ Repository not found        │ Check sources.list; pkg update      │
│ #82 │ GPG signature error         │ rm sources.list.d/*; pkg update     │
│ #83 │ Mirror sync in progress     │ Wait; try different mirror          │
│ #84 │ Invalid sources.list entry  │ Check syntax; fix URL               │
│ #85 │ Failed to fetch             │ Check internet; update sources      │
│ #86 │ Release file not found      │ Update sources.list with new URL    │
│ #87 │ InRelease file not found    │ pkg update to regenerate            │
│ #88 │ Repository expired          │ pkg update; check date/time         │
│ #89 │ Repository signed by unknown│ pkg update to get new keys          │
│ #90 │ Multiple repos configured   │ Remove duplicate entries            │
├─────────────────────────────────────────────────────────────────────────┤
│                    ERROR #91-100: ANDROID SPECIFIC                       │
├─────────────────────────────────────────────────────────────────────────┤
│ #91 │ Termux exits immediately    │ Clear data; reinstall from F-Droid  │
│ #92 │ Termux from Play Store      │ UNINSTALL; get from F-Droid         │
│ #93 │ Android OOM killed Termux   │ Set battery to unrestricted         │
│ #94 │ Screen off kills Termux     │ Settings → Battery → Unrestricted   │
│ #95 │ Notification required       │ Enable Termux notifications         │
│ #96 │ Boot scripts not running    │ Install Termux:Boot                 │
│ #97 │ Storage not accessible      │ termux-setup-storage; grant perm    │
│ #98 │ Camera/mic not working      │ Install Termux:API; grant perms     │
│ #99 │ API commands not found      │ pkg install termux-api              │
│ #100│ Foreground service required │ Pull down notification; "ACQUIRE"   │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 ERROR REFERENCE GUIDE

### Quick Diagnostic Commands

```bash
# System Status Check
echo "=== TERMUX DIAGNOSTIC ==="
echo "Termux Version: $TERMUX_VERSION"
echo "Architecture: $(uname -m)"
echo "Android: $(getprop ro.build.version.release)"
echo ""
echo "=== STORAGE ==="
df -h /data
echo ""
echo "=== MEMORY ==="
free -h
echo ""
echo "=== NETWORK ==="
ping -c 1 google.com 2>&1 | head -3
echo ""
echo "=== PACKAGES ==="
pkg list-installed | wc -l
echo "packages installed"
echo ""
echo "=== PATH ==="
echo $PATH | tr ':' '\n'
```

### Error Pattern Matching

```bash
# Find error patterns in logs
grep -i "error" $PREFIX/var/log/apt/term.log
grep -i "failed" $PREFIX/var/log/dpkg.log

# Check for specific issues
grep -i "permission denied" ~/.bash_history
grep -i "not found" /var/log/syslog 2>/dev/null

# Real-time log monitoring
logcat -s termux:V
```

### Recovery Commands

```bash
# Complete Termux repair
pkg clean
rm -rf $PREFIX/var/cache/apt/archives/*.deb
rm -rf $PREFIX/var/lib/dpkg/lock*
pkg update
pkg upgrade -y
pkg install -f

# Reset repositories
rm -rf $PREFIX/etc/apt/sources.list.d/*
pkg update

# Fix broken packages
dpkg --configure -a
apt --fix-broken install

# Reinstall core packages
pkg reinstall coreutils bash
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Diagnose and Fix Installation Error

```bash
# Scenario: Package installation fails
# Task: Diagnose and fix the error

# Step 1: Try to install a package
pkg install nonexistent-package-xyz

# Step 2: Analyze the error
# What type of error is it?
# What does the error message suggest?

# Step 3: Fix the issue
# Use pkg search to find correct package name
pkg search python

# Step 4: Install correct package
pkg install python -y

# Verify
python --version
```

### Exercise 2: Storage Error Resolution

```bash
# Scenario: No space left error
# Task: Clean up and resolve

# Step 1: Check disk usage
df -h

# Step 2: Find big directories
du -sh $PREFIX/* 2>/dev/null | sort -rh | head -5

# Step 3: Clean caches
pkg clean
rm -rf ~/.cache/*

# Step 4: Find and remove Python cache
find ~ -type d -name __pycache__ 2>/dev/null
find ~ -type d -name __pycache__ -exec rm -rf {} + 2>/dev/null

# Step 5: Verify space recovered
df -h
```

### Exercise 3: Permission Error Debugging

```bash
# Scenario: Script not running due to permission error
# Task: Debug and fix

# Step 1: Create a test script
echo '#!/bin/bash
echo "Hello from test script"' > test_script.sh

# Step 2: Try to run
./test_script.sh
# Note the error

# Step 3: Check permissions
ls -la test_script.sh

# Step 4: Fix permissions
chmod +x test_script.sh

# Step 5: Verify
ls -la test_script.sh
./test_script.sh
```

### Exercise 4: Network Error Diagnosis

```bash
# Scenario: Cannot connect to repository
# Task: Diagnose network issues

# Step 1: Test basic connectivity
ping -c 3 8.8.8.8

# Step 2: Test DNS
nslookup google.com

# Step 3: Test specific host
ping -c 3 packages.termux.dev

# Step 4: Check current sources
cat $PREFIX/etc/apt/sources.list

# Step 5: If DNS fails, set manual DNS
echo "nameserver 8.8.8.8" > $PREFIX/etc/resolv.conf

# Step 6: Test again
pkg update
```

### Exercise 5: Using strace for Debugging

```bash
# Scenario: Command fails with unclear error
# Task: Use strace to diagnose

# Step 1: Install strace
pkg install strace -y

# Step 2: Run strace on a command
strace ls /nonexistent 2>&1 | head -30

# Step 3: Find specific errors
strace ls /nonexistent 2>&1 | grep -i "no such"

# Step 4: Trace file operations
strace -e trace=openat cat /etc/passwd 2>&1 | head -20

# Step 5: Save trace to file
strace -o /tmp/trace.log ls
cat /tmp/trace.log | head -30
```

### Exercise 6: Python pip Error Resolution

```bash
# Scenario: Python module installation fails
# Task: Install required dependencies

# Step 1: Try to install a package that needs compilation
pip install pillow 2>&1 | head -20

# Step 2: If it fails, install dependencies
pkg install libjpeg-turbo libpng zlib -y

# Step 3: Retry installation
pip install pillow

# Step 4: Verify
python -c "from PIL import Image; print('Pillow installed successfully')"
```

### Exercise 7: Log File Analysis

```bash
# Scenario: Need to find what went wrong
# Task: Analyze log files

# Step 1: Check APT history
cat $PREFIX/var/log/apt/history.log | tail -30

# Step 2: Check DPKG log
cat $PREFIX/var/log/dpkg.log | tail -30

# Step 3: Check for errors
grep -i "error" $PREFIX/var/log/apt/term.log 2>/dev/null | tail -10

# Step 4: Check Android logs for Termux
logcat -d | grep -i termux | tail -20

# Step 5: Check command history
history | tail -20
```

---

## 🔧 ADVANCED DEBUGGING

### 1. System Call Tracing with strace

```bash
# Comprehensive strace usage

# Install strace
pkg install strace

# Basic usage
strace <command>

# Common useful options:
# -f: Follow child processes
# -e trace=<calls>: Trace specific calls
# -o <file>: Output to file
# -p <pid>: Attach to running process
# -c: Count syscalls
# -t: Show timestamps

# Trace file operations
strace -f -e trace=file <command>

# Trace network operations
strace -f -e trace=network <command>

# Trace memory operations
strace -f -e trace=memory <command>

# Trace process management
strace -f -e trace=process <command>

# Trace signal handling
strace -f -e trace=signal <command>

# Output to file with timestamps
strace -f -t -o debug.log <command>

# Attach to running process
PID=$(pgrep -f "myprocess")
strace -p $PID

# Count syscalls
strace -c <command>
```

### 2. Memory Debugging

```bash
# Check memory usage
free -h
cat /proc/meminfo

# Process memory usage
ps aux --sort=-%mem | head -10

# Specific process memory
PID=$(pgrep python)
cat /proc/$PID/status | grep -i mem
cat /proc/$PID/maps | head -20

# Check for memory leaks (if available)
# valgrind --leak-check=full <program>

# Monitor memory in real-time
watch -n 1 free -h
```

### 3. Network Debugging

```bash
# DNS debugging
nslookup <domain>
dig <domain>

# Connectivity debugging
ping -c 3 <host>
traceroute <host>
mtr <host>  # if available

# Port scanning
nmap -sT localhost
nmap -p- localhost | grep open

# Open connections
netstat -tulpn
ss -tulpn

# Capture packets (requires root)
# tcpdump -i any -w capture.pcap

# HTTP debugging
curl -v <url>
curl -I <url>
wget --debug <url>
```

### 4. Process Debugging

```bash
# List processes
ps aux
ps -ef --forest

# Process tree
pstree -p

# Find process
pgrep -a <name>
pidof <name>

# Process details
PID=<process_id>
cat /proc/$PID/status
cat /proc/$PID/cmdline | tr '\0' ' '
cat /proc/$PID/environ | tr '\0' '\n'
ls -la /proc/$PID/fd/

# Real-time monitoring
top -p $PID
htop -p $PID

# Signal handling
kill -l              # List signals
kill -STOP $PID      # Pause
kill -CONT $PID      # Resume
kill -9 $PID         # Force kill

# Core dumps (if enabled)
ulimit -c unlimited
# Run program that crashes
gdb <program> core
```

### 5. Script Debugging

```bash
# Bash script debugging

# Syntax check
bash -n script.sh

# Debug mode
bash -x script.sh

# Verbose mode
bash -v script.sh

# Both debug and verbose
bash -xv script.sh

# Add debugging to specific parts
#!/bin/bash
set -x  # Start debugging
# ... code ...
set +x  # Stop debugging

# Common debugging flags
set -e  # Exit on error
set -u  # Error on undefined variable
set -o pipefail  # Pipe errors

# Log everything
exec > >(tee -a script.log) 2>&1
```

### 6. Library Dependency Debugging

```bash
# Check library dependencies
ldd <binary>

# Find library
find $PREFIX -name "libname*"

# Check what package provides a file
pkg install apt-file
apt-file update
apt-file search <filename>

# Library cache
ldconfig -p | grep <library>

# Update library cache
ldconfig

# Check RPATH/RUNPATH
readelf -d <binary> | grep PATH
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Error Theme**
```
┌──────────────────────────────┐
│  [Red/Dark Background]       │
│                              │
│  ⚠️ 50+ ERRORS               │
│     & FIXES                  │
│                              │
│  🔧 Complete Guide           │
│                              │
│  [T3rmuxk1ng]                │
└──────────────────────────────┘
```

**Option B: Debugging Theme**
```
┌──────────────────────────────┐
│  [Terminal Style]            │
│                              │
│  $ error: fix it!            │
│  $ pkg install -f            │
│  ✓ FIXED!                    │
│                              │
│  Termux Troubleshooting      │
│  [T3rmuxk1ng]                │
└──────────────────────────────┘
```

**Option C: Reference Guide Theme**
```
┌──────────────────────────────┐
│  📖 ERROR BIBLE              │
│                              │
│  50+ Errors • 100+ Solutions │
│  • Installation Errors       │
│  • Permission Errors         │
│  • Network Errors            │
│                              │
│  [T3rmuxk1ng]                │
└──────────────────────────────┘
```

### Video Description Template

```markdown
📱 Termux Full Course - Chapter 58: Common Errors & Fixes | Complete Troubleshooting Guide

🔥 In this video you'll learn:
• 50+ Common errors and their solutions
• How to read and understand error messages
• Installation, permission, network errors
• Python/pip error troubleshooting
• Debugging techniques with strace
• Log file analysis
• Environment and PATH issues
• Repository problems

⏱️ Timestamps:
0:00 - Introduction
1:00 - Understanding Errors
3:30 - Installation Errors
7:00 - Permission Errors
10:30 - Network Errors
13:30 - Storage Errors
16:00 - Python/pip Errors
19:30 - Compilation Errors
22:00 - Debugging Techniques
25:30 - Environment Issues
28:00 - Repository Issues
30:30 - SELinux Issues
32:00 - More Common Errors
35:30 - Quick Fix Reference
37:30 - Prevention Tips
39:00 - Summary

📝 Key Commands:
pkg install -f          # Fix broken packages
termux-setup-storage    # Grant storage permission
strace <command>        # Debug with strace
pkg clean               # Clean package cache
pip install --user      # User-level pip install

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]

#Termux #TermuxErrors #TermuxTroubleshooting #T3rmuxk1ng #LinuxOnAndroid #TermuxDebug #TermuxFix

---
⚠️ Disclaimer: This video is for educational purposes. Always backup your data before making system changes.
```

### Tags List

```
termux, termux errors, termux troubleshooting, termux fixes,
termux common errors, termux debugging, termux error solution,
termux permission denied, termux package error, termux network error,
termux pip error, termux python error, termux installation error,
termux strace, termux logs, termux guide, termux tutorial,
termux hindi, termux course, t3rmuxk1ng, android terminal,
linux troubleshooting, error fixing, debugging tutorial
```

### Hashtags

```
#Termux #TermuxErrors #TermuxDebug #TermuxTroubleshooting #TermuxFix
#TermuxHindi #TermuxTutorial #TermuxCourse #T3rmuxk1ng #LinuxOnAndroid
#AndroidTerminal #Debugging #ErrorFixing #Troubleshooting
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux Wiki | https://wiki.termux.com/ |
| Termux GitHub Issues | https://github.com/termux/termux-packages/issues |
| Termux Reddit | r/termux |

### Error Reference Sites

| Resource | Description |
|----------|-------------|
| Stack Overflow | Search "[termux] error message" |
| Termux Wiki - FAQ | Common questions and solutions |
| GitHub Issues | Search for your error |

### Debugging Tools

```bash
# Essential debugging packages
pkg install strace      # System call tracer
pkg install ltrace      # Library call tracer
pkg install gdb         # GNU Debugger
pkg install lsof        # List open files
pkg install htop        # Process monitor
pkg install nmap        # Network scanner
pkg install tcpdump     # Packet analyzer
pkg install file        # File type identification
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 59, verify:

- [ ] Understand different error categories
- [ ] Know how to fix "Unable to locate package" error
- [ ] Can resolve permission denied errors
- [ ] Know how to handle network issues
- [ ] Can use strace for debugging
- [ ] Know log file locations
- [ ] Understand PATH and environment issues
- [ ] Can fix Python/pip installation errors
- [ ] Know how to repair broken packages
- [ ] Have quick reference saved

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 59: Termux Performance Tips**

- Storage optimization
- Memory management
- CPU optimization
- Battery saving tips
- Process management
- OOM prevention

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
