# Chapter 60: Termux Backup & Restore

> **Module:** 10 - Troubleshooting  
> **Chapter:** 60 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed backup & restore methods |
| Backup Scripts | Complete automated backup solution |
| Practice Exercises | Hands-on backup tasks |
| Troubleshooting | Common backup issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 60
Title: Termux Backup & Restore | Data Safe Rakhein | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - Termux Backup & Restore!

Sochein aapne mahino mehnat ki, Python scripts likhi, tools install kiye,
environment setup kiya, aur ek din phone format karna pada ya naya phone
aagaya... SAB GAYA! Zero se shuru karna padega!

Ye problem har Termux user face karta hai. Lekin aaj ke baad aapka data
safe rahega. Main sikhaunga:
- Kya backup karna hai
- Kaise backup karna hai
- Automated scripts kaise banate hain
- Cloud backup options
- New phone mein migrate kaise karein

To bina time waste kiye, chaliye shuru karte hain!

Play button dabaiye, video like karein, subscribe karein!

---

[SECTION 1: BACKUP KYA IMPORTANT HAI - 0:50 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - backup itna important kyun hai?

Termux ka data ye location pe hota hai:
    /data/data/com.termux/files/

Ye Android ke internal storage mein hai, jo ki:
1. App uninstall hone pe DELETE ho jaata hai
2. Phone format pe DELETE ho jaata hai
3. App crash ya corrupt hone pe data LOSS ho sakta hai
4. Phone change karne pe data TRANSFER nahi hota automatically

Aapne mehnat se kya kya banaya hoga:
✓ Custom scripts - hours of coding
✓ Installed packages - 50-100 packages
✓ Configuration files - .bashrc, .profile, etc.
✓ Projects aur code
✓ API keys aur credentials
✓ SSH keys
✓ Database files
✓ Downloaded tools

Ek command se sab gaya:
    pkg uninstall something-wrong
    # Ya phone reset

Real life examples:
- Student ne 6 mahine ka project code kiya, phone hang hua, format karna pada
- Security researcher ne tools setup kiye, naya phone aaya, sab dobara setup
- Developer ne Python environment banaya, app crash, sab lost

Isliye backup RULE NUMBER 1 hai:
    "Data jo backup nahi, wo data nahi hai!"

---

[SECTION 2: KYA BACKUP KARNA HAI - 3:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab samjhte hain - exactly kya kya backup karna hai?

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX BACKUP CHECKLIST                               │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Category             │ Location / Files                                 │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Home Directory       │ ~/ (entire home folder)                         │
│ Installed Packages   │ pkg list-installed output                       │
│ Config Files         │ ~/.bashrc, ~/.profile, ~/.bash_profile          │
│ Custom Scripts       │ ~/scripts/, ~/tools/, ~/bin/                    │
│ SSH Keys             │ ~/.ssh/ (id_rsa, id_rsa.pub, known_hosts)       │
│ Git Configs          │ ~/.gitconfig                                    │
│ Environment Vars     │ ~/.env, custom exports                          │
│ Cron Jobs            │ crontab -l output                               │
│ Python Packages      │ pip list output                                 │
│ Node Modules         │ npm list -g output                              │
│ Projects             │ ~/projects/, ~/workspace/                       │
│ Databases            │ ~/.local/share/ (app databases)                 │
└──────────────────────┴──────────────────────────────────────────────────┘

IN DETAIL:

[1] HOME DIRECTORY
    Location: /data/data/com.termux/files/home
    Ye SABSE IMPORTANT hai - isme sab kuch hai
    Command: tar -czvf home_backup.tar.gz ~/

[2] INSTALLED PACKAGES LIST
    Ye naye phone pe same environment banane ke liye chahiye
    Command: pkg list-installed > installed_packages.txt
    
[3] CONFIGURATION FILES
    Files:
    - ~/.bashrc - Bash configuration, aliases
    - ~/.profile - Login shell config
    - ~/.bash_aliases - Custom aliases
    - ~/.nanorc - Nano editor config
    - ~/.vimrc - Vim config (if using vim)
    
[4] CUSTOM SCRIPTS
    Agar aapne custom tools banaye hain
    Common locations:
    - ~/bin/
    - ~/scripts/
    - ~/tools/
    
[5] SSH KEYS
    Location: ~/.ssh/
    Files:
    - id_rsa (private key - SECRET!)
    - id_rsa.pub (public key)
    - known_hosts
    - config (SSH config)
    
    Ye BAHUT important hai agar SSH use karte ho
    
[6] ENVIRONMENT VARIABLES
    Custom exports jo .bashrc ya .profile mein hain
    Example:
    - API keys
    - PATH modifications
    - Custom variables
    
---

[SECTION 3: MANUAL BACKUP METHODS - 6:00 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain manual backup kaise karte hain - step by step.

[METHOD 1: TAR BACKUP - Simple & Effective]

Tar se entire home folder ka backup:

    # Basic backup
    tar -czvf termux_backup_$(date +%Y%m%d).tar.gz ~/
    
    # With exclusions (large folders skip)
    tar -czvf termux_backup.tar.gz \
        --exclude='~/.cache' \
        --exclude='~/node_modules' \
        --exclude='~/.npm' \
        ~/

Explain karta hoon:
- -c : create new archive
- -z : gzip compression
- -v : verbose (show progress)
- -f : filename

Packages list backup:

    # System packages
    pkg list-installed | cut -d'/' -f1 > packages.txt
    
    # Python packages
    pip list --format=freeze > requirements.txt
    
    # Node global packages
    npm list -g --depth=0 > npm_packages.txt

[METHOD 2: RSYNC BACKUP - Incremental]

Rsync better hai agar regular backup lete ho:

    # Install rsync
    pkg install rsync
    
    # Backup to storage
    rsync -avz --progress ~/ ~/storage/downloads/termux_backup/
    
    # Sync only changes (incremental)
    rsync -avz --delete ~/ ~/storage/downloads/termux_backup/

Flags explain:
- -a : archive mode (preserves permissions, times, etc.)
- -v : verbose
- -z : compress during transfer
- --delete : delete extra files in destination
- --progress : show progress

[METHOD 3: STORAGE COPY]

Simple copy to phone storage:

    # Create backup directory
    mkdir -p ~/storage/downloads/termux_backup
    
    # Copy important files
    cp -r ~/.bashrc ~/storage/downloads/termux_backup/
    cp -r ~/.profile ~/storage/downloads/termux_backup/
    cp -r ~/.ssh ~/storage/downloads/termux_backup/
    cp -r ~/scripts ~/storage/downloads/termux_backup/
    
    # Copy projects
    cp -r ~/projects ~/storage/downloads/termux_backup/

---

[SECTION 4: AUTOMATED BACKUP SCRIPT - 9:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab main sikhaunga automated backup script - ek command mein sab ho jaayega!

[COMPLETE BACKUP SCRIPT]

Ye script main special banaya hai:
- Home directory backup
- Packages list
- Config files
- Compressed archive
- Date wise naming
- Storage mein save

    #!/bin/bash
    # Termux Complete Backup Script
    # Author: T3rmuxk1ng
    
    # Colors
    RED='\033[0;31m'
    GREEN='\033[0;32m'
    YELLOW='\033[1;33m'
    BLUE='\033[0;34m'
    NC='\033[0m'
    
    echo -e "${GREEN}╔════════════════════════════════════════╗${NC}"
    echo -e "${GREEN}║   TERMUX BACKUP SCRIPT - T3rmuxk1ng    ║${NC}"
    echo -e "${GREEN}╚════════════════════════════════════════╝${NC}"
    
    # Backup directory
    BACKUP_DIR=~/storage/downloads/termux_backups
    DATE=$(date +%Y%m%d_%H%M%S)
    BACKUP_NAME="termux_backup_${DATE}"
    
    # Create backup directory
    mkdir -p "$BACKUP_DIR"
    mkdir -p "$BACKUP_DIR/$BACKUP_NAME"
    
    echo -e "${YELLOW}[1/5] Backing up home directory...${NC}"
    tar -czvf "$BACKUP_DIR/$BACKUP_NAME/home.tar.gz" \
        --exclude='~/.cache' \
        --exclude='~/node_modules' \
        --exclude='~/.npm/_cacache' \
        --exclude='~/storage' \
        ~/ 2>/dev/null
    
    echo -e "${YELLOW}[2/5] Saving installed packages list...${NC}"
    pkg list-installed | cut -d'/' -f1 > "$BACKUP_DIR/$BACKUP_NAME/packages.txt"
    
    echo -e "${YELLOW}[3/5] Saving Python packages...${NC}"
    pip list --format=freeze > "$BACKUP_DIR/$BACKUP_NAME/requirements.txt" 2>/dev/null
    
    echo -e "${YELLOW}[4/5] Saving Node packages...${NC}"
    npm list -g --depth=0 > "$BACKUP_DIR/$BACKUP_NAME/npm_packages.txt" 2>/dev/null
    
    echo -e "${YELLOW}[5/5] Creating final archive...${NC}"
    tar -czvf "$BACKUP_DIR/${BACKUP_NAME}.tar.gz" -C "$BACKUP_DIR" "$BACKUP_NAME"
    rm -rf "$BACKUP_DIR/$BACKUP_NAME"
    
    # Calculate size
    SIZE=$(du -h "$BACKUP_DIR/${BACKUP_NAME}.tar.gz" | cut -f1)
    
    echo ""
    echo -e "${GREEN}╔════════════════════════════════════════╗${NC}"
    echo -e "${GREEN}║         BACKUP COMPLETED!              ║${NC}"
    echo -e "${GREEN}╚════════════════════════════════════════╝${NC}"
    echo -e "Backup Location: ${BLUE}$BACKUP_DIR/${BACKUP_NAME}.tar.gz${NC}"
    echo -e "Backup Size: ${BLUE}$SIZE${NC}"

[Kaise use karein:]

    # Script save karein
    nano ~/backup.sh
    
    # Execute permission
    chmod +x ~/backup.sh
    
    # Run backup
    ./backup.sh

---

[SECTION 5: CLOUD BACKUP OPTIONS - 12:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Local backup achha hai, lekin cloud backup EXTRA SAFE hai!

[OPTION 1: GOOGLE DRIVE via RCLONE]

    # Install rclone
    pkg install rclone
    
    # Configure Google Drive
    rclone config
    # Follow prompts - n for new remote
    # Name: gdrive
    # Storage: drive (Google Drive)
    # Authenticate via browser
    
    # Backup to Drive
    rclone copy ~/storage/downloads/termux_backup.tar.gz gdrive:TermuxBackups/

[OPTION 2: DROPBOX]

    # Install rclone (supports Dropbox too)
    rclone config
    # Add Dropbox remote
    
    # Sync
    rclone sync ~/storage/downloads/termux_backups dropbox:TermuxBackups/

[OPTION 3: GITHUB/GITLAB - For Scripts]

    # Create private repo for backup
    # Initialize in scripts folder
    cd ~/scripts
    git init
    git remote add origin https://github.com/username/termux-scripts.git
    git add .
    git commit -m "Backup $(date)"
    git push -u origin main

[OPTION 4: TELEGRAM BOT]

    # Use Telegram API to send backup
    # Useful for small backup files
    
    BOT_TOKEN="your_bot_token"
    CHAT_ID="your_chat_id"
    FILE="backup.tar.gz"
    
    curl -F document=@$FILE \
        "https://api.telegram.org/bot${BOT_TOKEN}/sendDocument?chat_id=${CHAT_ID}"

---

[SECTION 6: RESTORE PROCESS - 14:00 to 16:30]
─────────────────────────────────────────────────────────────────────────────

Ab sabse important part - RESTORE kaise karein!

[RESTORE STEP 1: FRESH TERMUX SETUP]

    # New phone ya fresh install
    # Install Termux from F-Droid
    # Run initial setup
    pkg update && pkg upgrade -y
    termux-setup-storage

[RESTORE STEP 2: EXTRACT BACKUP]

    # Copy backup to storage
    # Via USB, cloud download, etc.
    
    # Extract home backup
    cd ~
    tar -xzvf /sdcard/Download/termux_backup.tar.gz
    
    # Extract with full path
    tar -xzvf /sdcard/Download/termux_backup_20240115.tar.gz -C /

[RESTORE STEP 3: RESTORE PACKAGES]

    # Read packages list
    cat packages.txt
    
    # Install all packages at once
    xargs pkg install -y < packages.txt
    
    # Or manually
    pkg install python nodejs git curl wget ...

[RESTORE STEP 4: RESTORE PYTHON PACKAGES]

    # If you saved requirements.txt
    pip install -r requirements.txt

[RESTORE STEP 5: RESTORE NODE PACKAGES]

    # Install from list
    npm install -g $(cat npm_packages.txt | awk '{print $2}')

[RESTORE STEP 6: VERIFY]

    # Check configurations
    cat ~/.bashrc
    
    # Check scripts
    ls ~/scripts/
    
    # Test SSH keys
    ssh -T git@github.com

[QUICK RESTORE SCRIPT]

    #!/bin/bash
    # Restore script
    
    BACKUP_FILE=$1
    
    if [ -z "$BACKUP_FILE" ]; then
        echo "Usage: ./restore.sh <backup_file.tar.gz>"
        exit 1
    fi
    
    echo "Restoring Termux from $BACKUP_FILE..."
    
    # Extract backup
    tar -xzvf "$BACKUP_FILE" -C ~/
    
    # Find packages file
    PKG_FILE=$(tar -tzf "$BACKUP_FILE" | grep packages.txt | head -1)
    
    if [ -n "$PKG_FILE" ]; then
        echo "Restoring packages..."
        tar -xzvf "$BACKUP_FILE" -O "$PKG_FILE" | xargs pkg install -y
    fi
    
    echo "Restore complete! Restart Termux."

---

[SECTION 7: MIGRATING TO NEW PHONE - 16:30 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Naya phone aaya? Migration easy hai!

[MIGRATION CHECKLIST]

┌─────────────────────────────────────────────────────────────────────────┐
│                    NEW PHONE MIGRATION STEPS                             │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  OLD PHONE:                                                              │
│  □ Run backup script                                                     │
│  □ Copy backup to cloud (Google Drive, etc.)                            │
│  □ Export SSH keys separately                                            │
│  □ Note any custom PATH or environment variables                        │
│                                                                          │
│  TRANSFER:                                                               │
│  □ Download backup on new phone                                          │
│  □ Or use USB transfer                                                   │
│  □ Or use Shareit/Xender for fast transfer                              │
│                                                                          │
│  NEW PHONE:                                                              │
│  □ Install Termux from F-Droid (NOT Play Store!)                        │
│  □ Run: pkg update && pkg upgrade -y                                    │
│  □ Run: termux-setup-storage                                            │
│  □ Extract backup                                                        │
│  □ Restore packages                                                      │
│  □ Test all scripts                                                      │
│  □ Update any hardcoded paths                                            │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘

[IMPORTANT NOTES FOR MIGRATION]

1. ANDROID VERSION DIFFERENCE
   - New phone may have different Android version
   - Some packages may behave differently
   - Test everything after migration

2. STORAGE PATHS
   - /sdcard/ path same rahta hai
   - Internal paths change ho sakte hain
   - Update any hardcoded paths in scripts

3. PERMISSIONS
   - Re-grant storage permission
   - Check any app-specific permissions

4. TERMUX:API
   - Install Termux:API app separately
   - pkg install termux-api

---

[SECTION 8: TERMUX BACKUP APPS - 18:00 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Kuch apps hain jo Termux backup mein help karti hain:

[1] TERMUX:TASKER
    - Tasker se automated backups schedule kar sakte ho
    - Trigger on time, battery, etc.
    
[2] TERMUX:WIDGET
    - Home screen widget for one-tap backup
    - Add backup script shortcut

[3] RCLONE
    - Best for cloud backups
    - Supports 40+ cloud providers

[4] SYNCTHING (Separate App)
    - Continuous sync between devices
    - Can sync Termux folders

[TASKER AUTOMATION EXAMPLE]

    Task: Termux Backup
    Action 1: Termux Command
        Command: /data/data/com.termux/files/home/backup.sh
        Working Dir: /data/data/com.termux/files/home
    
    Profile: Time
        Time: 02:00 (Daily at 2 AM)
    
    Link Profile → Task

---

[SECTION 9: BACKUP BEST PRACTICES - 19:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Final section - Best Practices!

┌─────────────────────────────────────────────────────────────────────────┐
│                    BACKUP BEST PRACTICES                                 │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. REGULAR BACKUPS                                                      │
│     □ Daily for active development                                       │
│     □ Weekly for casual use                                              │
│     □ Before major changes                                               │
│                                                                          │
│  2. 3-2-1 RULE                                                           │
│     □ 3 copies of data                                                   │
│     □ 2 different storage types (local + cloud)                         │
│     □ 1 offsite backup                                                   │
│                                                                          │
│  3. TEST YOUR BACKUPS                                                    │
│     □ Verify backup integrity                                            │
│     □ Test restore process                                               │
│     □ Don't wait for disaster to find out backup is corrupt             │
│                                                                          │
│  4. VERSION YOUR BACKUPS                                                 │
│     □ Keep multiple dated backups                                        │
│     □ Don't overwrite previous backups                                   │
│     □ Keep at least last 3-5 backups                                    │
│                                                                          │
│  5. SENSITIVE DATA                                                       │
│     □ Don't backup passwords in plain text                               │
│     □ Encrypt sensitive backups                                          │
│     □ Use environment variables for secrets                              │
│                                                                          │
│  6. DOCUMENT YOUR SETUP                                                  │
│     □ Keep a setup_notes.txt                                             │
│     □ Document any custom configurations                                 │
│     □ Note non-standard package sources                                 │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘

[BACKUP SCHEDULE EXAMPLE]

    # Add to crontab
    crontab -e
    
    # Daily backup at 2 AM
    0 2 * * * /data/data/com.termux/files/home/backup.sh
    
    # Weekly full backup Sunday midnight
    0 0 * * 0 /data/data/com.termux/files/home/full_backup.sh

---

[SECTION 10: SUMMARY - 21:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 60 complete! Let's summarize:

✅ Backup kyun important hai - data loss prevention
✅ Kya backup karna hai - home, packages, configs, scripts
✅ Manual backup methods - tar, rsync, copy
✅ Automated backup script - one-click complete backup
✅ Cloud backup options - rclone, GitHub, Telegram
✅ Restore process - step by step recovery
✅ New phone migration - checklist aur process
✅ Backup apps - Tasker, Widget, rclone
✅ Best practices - 3-2-1 rule, testing, versioning

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    BACKUP COMMANDS QUICK REFERENCE                       │
├─────────────────────────────────────────────────────────────────────────┤
│ tar -czvf backup.tar.gz ~/          │ Create backup archive             │
│ tar -xzvf backup.tar.gz             │ Extract backup                    │
│ pkg list-installed > packages.txt   │ Save packages list                │
│ xargs pkg install -y < packages.txt │ Restore packages                  │
│ rsync -avz ~/ /sdcard/backup/       │ Sync backup to storage            │
│ rclone copy backup.tar.gz gdrive:/  │ Upload to Google Drive            │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 61 mein hum discuss karenge:
- Useful resources for Termux
- Community links
- Documentation
- Learning paths

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 61!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Why Backup is Critical in Termux

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX DATA VULNERABILITY                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Data Loss Scenarios                           │   │
│   │                                                                   │   │
│   │  1. App Uninstall         → ALL DATA DELETED                     │   │
│   │  2. Clear App Data        → ALL DATA DELETED                     │   │
│   │  3. Phone Factory Reset   → ALL DATA DELETED                     │   │
│   │  4. Phone Lost/Stolen     → ALL DATA LOST                        │   │
│   │  5. Android Update Issue  → POSSIBLE DATA LOSS                   │   │
│   │  6. App Crash/Corrupt     → POSSIBLE DATA LOSS                   │   │
│   │  7. Storage Corruption    → POSSIBLE DATA LOSS                   │   │
│   │                                                                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Termux Data Location:                                                  │
│   /data/data/com.termux/files/                                          │
│                                                                          │
│   This is PRIVATE app storage - NOT accessible via:                     │
│   - File manager apps                                                   │
│   - USB connection                                                      │
│   - Other apps                                                          │
│                                                                          │
│   ONLY accessible from within Termux itself!                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. What to Backup - Complete List

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    COMPLETE BACKUP INVENTORY                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  CATEGORY 1: HOME DIRECTORY (~)                                          │
│  ═══════════════════════════════                                         │
│  Priority: CRITICAL                                                      │
│  Size: 50MB - 5GB (depends on usage)                                    │
│  Command: tar -czvf home.tar.gz ~/                                      │
│                                                                          │
│  Contains:                                                               │
│  ├── All user files and scripts                                         │
│  ├── Configuration files (.bashrc, .profile)                            │
│  ├── SSH keys (~/.ssh/)                                                 │
│  ├── Git configuration                                                  │
│  ├── Projects and code                                                  │
│  └── Custom tools                                                       │
│                                                                          │
│  ─────────────────────────────────────────────────────────────────────  │
│                                                                          │
│  CATEGORY 2: INSTALLED PACKAGES                                          │
│  ═════════════════════════════════                                       │
│  Priority: HIGH                                                          │
│  Size: < 1MB (text file)                                                │
│  Command: pkg list-installed | cut -d'/' -f1 > packages.txt             │
│                                                                          │
│  Important for:                                                          │
│  - Recreating environment                                                │
│  - Quick restore                                                         │
│  - Documentation                                                         │
│                                                                          │
│  ─────────────────────────────────────────────────────────────────────  │
│                                                                          │
│  CATEGORY 3: CONFIGURATION FILES                                         │
│  ═══════════════════════════════════                                     │
│  Priority: HIGH                                                          │
│                                                                          │
│  Files to backup:                                                        │
│  ├── ~/.bashrc          - Bash shell configuration                       │
│  ├── ~/.bash_profile    - Login shell configuration                      │
│  ├── ~/.profile         - Profile settings                               │
│  ├── ~/.bash_aliases    - Custom command aliases                         │
│  ├── ~/.bash_completion - Completion settings                            │
│  ├── ~/.gitconfig       - Git configuration                              │
│  ├── ~/.gitignore       - Global git ignore                              │
│  ├── ~/.nanorc          - Nano editor config                             │
│  ├── ~/.vimrc           - Vim editor config                              │
│  ├── ~/.inputrc         - Readline configuration                         │
│  └── ~/.curlrc          - Curl defaults                                  │
│                                                                          │
│  ─────────────────────────────────────────────────────────────────────  │
│                                                                          │
│  CATEGORY 4: SSH & GPG KEYS                                              │
│  ══════════════════════════════                                          │
│  Priority: CRITICAL (if you use SSH)                                    │
│  Security: ENCRYPT BACKUP                                                │
│                                                                          │
│  Location: ~/.ssh/                                                       │
│  Files:                                                                  │
│  ├── id_rsa            - Private key (SECRET!)                           │
│  ├── id_rsa.pub        - Public key                                      │
│  ├── id_ed25519        - Ed25519 private key                             │
│  ├── id_ed25519.pub    - Ed25519 public key                              │
│  ├── known_hosts       - Known server fingerprints                       │
│  ├── authorized_keys   - Keys allowed to login                           │
│  └── config            - SSH client configuration                        │
│                                                                          │
│  GPG Keys (~/.gnupg/):                                                   │
│  ├── pubring.kbx       - Public keyring                                  │
│  ├── trustdb.gpg       - Trust database                                  │
│  └── private-keys-v1.d/ - Private keys                                   │
│                                                                          │
│  ─────────────────────────────────────────────────────────────────────  │
│                                                                          │
│  CATEGORY 5: DEVELOPMENT ENVIRONMENTS                                    │
│  ═══════════════════════════════════                                     │
│  Priority: MEDIUM-HIGH                                                   │
│                                                                          │
│  Python:                                                                 │
│  ├── pip list --format=freeze > requirements.txt                        │
│  ├── Virtual environments in ~/venvs/                                   │
│  └── Poetry/pipenv projects                                             │
│                                                                          │
│  Node.js:                                                                │
│  ├── npm list -g --depth=0 > npm_global.txt                             │
│  ├── ~/.npmrc - npm configuration                                        │
│  └── Global packages in ~/.npm-global/                                  │
│                                                                          │
│  Go:                                                                     │
│  ├── ~/go/bin/ - Compiled binaries                                      │
│  └── ~/go/src/ - Source code                                            │
│                                                                          │
│  Rust:                                                                   │
│  ├── ~/.cargo/ - Cargo configuration                                    │
│  └── Cargo projects                                                     │
│                                                                          │
│  ─────────────────────────────────────────────────────────────────────  │
│                                                                          │
│  CATEGORY 6: CRON JOBS                                                   │
│  ═══════════════════                                                     │
│  Priority: MEDIUM                                                        │
│  Command: crontab -l > my_cron.txt                                      │
│                                                                          │
│  ─────────────────────────────────────────────────────────────────────  │
│                                                                          │
│  CATEGORY 7: DATABASES                                                   │
│  ══════════════════                                                      │
│  Priority: HIGH (if applicable)                                          │
│                                                                          │
│  SQLite:                                                                 │
│  ├── Location: Various project folders                                  │
│  └── Backup: Copy .db files                                             │
│                                                                          │
│  MySQL/MariaDB:                                                          │
│  └── mysqldump -u user -p database > backup.sql                         │
│                                                                          │
│  PostgreSQL:                                                             │
│  └── pg_dump database > backup.sql                                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Manual Backup Methods

#### Method A: TAR Archive Backup

```bash
# Basic tar backup
tar -czvf backup.tar.gz ~/

# TAR with compression levels (1-9, higher = more compression)
tar -cvf - ~/ | gzip -9 > backup.tar.gz

# TAR with exclusions
tar -czvf backup.tar.gz \
    --exclude="$HOME/.cache" \
    --exclude="$HOME/node_modules" \
    --exclude="$HOME/.npm/_cacache" \
    --exclude="$HOME/storage" \
    --exclude="$HOME/.local/share/Trash" \
    ~/

# TAR with progress bar (requires pv)
tar -cf - ~/ | pv -s $(du -sb ~/ | cut -f1) | gzip > backup.tar.gz

# Split large backup into parts
tar -czvf - ~/ | split -b 500M - backup_part_

# Verify archive integrity
tar -tzvf backup.tar.gz | head -20
```

#### Method B: RSYNC Backup

```bash
# Install rsync
pkg install rsync

# Basic rsync to storage
rsync -avz ~/ ~/storage/downloads/termux_backup/

# Rsync with progress
rsync -avz --progress ~/ ~/storage/downloads/termux_backup/

# Mirror backup (delete extra files in destination)
rsync -avz --delete ~/ ~/storage/downloads/termux_backup/

# Incremental backup with backup-dir
rsync -avz --backup --backup-dir=~/storage/backups/incremental \
    ~/ ~/storage/backups/current/

# Rsync over SSH to remote server
rsync -avz -e ssh ~/ user@server:/backup/termux/

# Rsync dry-run (test without copying)
rsync -avz --dry-run ~/ ~/storage/downloads/test/
```

#### Method C: Package List Backup

```bash
# System packages (Termux pkg)
pkg list-installed | cut -d'/' -f1 > ~/packages.txt

# Alternative: apt method
apt list --installed 2>/dev/null | cut -d'/' -f1 > packages.txt

# Python pip packages
pip list --format=freeze > requirements.txt

# With versions
pip freeze > requirements_versions.txt

# Node.js global packages
npm list -g --depth=0 --json > npm_global.json

# Just names
npm list -g --depth=0 | tail -n +2 | awk '{print $2}' > npm_global.txt

# Go packages
go list -m all > go_modules.txt

# Rust crates (if using cargo)
cargo install --list > cargo_installed.txt
```

### 4. Automated Backup Scripts

#### Complete Backup Script

```bash
#!/bin/bash
#################################################################
# TERMUX COMPLETE BACKUP SCRIPT
# Author: T3rmuxk1ng
# Version: 2.0
# Description: Full automated backup solution for Termux
#################################################################

# ═══════════════════════════════════════════════════════════
# CONFIGURATION
# ═══════════════════════════════════════════════════════════

# Colors for output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
PURPLE='\033[0;35m'
CYAN='\033[0;36m'
NC='\033[0m' # No Color

# Backup configuration
BACKUP_BASE_DIR="${HOME}/storage/downloads/termux_backups"
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_NAME="termux_backup_${DATE}"
TEMP_DIR="${BACKUP_BASE_DIR}/${BACKUP_NAME}"
LOG_FILE="${BACKUP_BASE_DIR}/backup.log"

# Exclusions
EXCLUDE_PATTERNS=(
    ".cache"
    "node_modules"
    ".npm/_cacache"
    ".local/share/Trash"
    "storage"
    "__pycache__"
    "*.pyc"
    ".git/objects/pack/*.pack"
)

# ═══════════════════════════════════════════════════════════
# FUNCTIONS
# ═══════════════════════════════════════════════════════════

log() {
    echo -e "$1"
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" >> "$LOG_FILE"
}

show_banner() {
    echo -e "${GREEN}"
    echo "╔═════════════════════════════════════════════════════════╗"
    echo "║                                                         ║"
    echo "║         TERMUX BACKUP SCRIPT v2.0                       ║"
    echo "║            by T3rmuxk1ng                                ║"
    echo "║                                                         ║"
    echo "╚═════════════════════════════════════════════════════════╝"
    echo -e "${NC}"
}

check_storage() {
    if [ ! -d "$HOME/storage/downloads" ]; then
        log "${RED}ERROR: Storage not accessible!${NC}"
        log "${YELLOW}Run: termux-setup-storage${NC}"
        exit 1
    fi
}

create_directories() {
    mkdir -p "$BACKUP_BASE_DIR"
    mkdir -p "$TEMP_DIR"
    mkdir -p "$TEMP_DIR/configs"
    mkdir -p "$TEMP_DIR/lists"
}

backup_home_directory() {
    log "${CYAN}[1/7] Backing up home directory...${NC}"
    
    local exclude_args=""
    for pattern in "${EXCLUDE_PATTERNS[@]}"; do
        exclude_args="$exclude_args --exclude=$HOME/$pattern"
    done
    
    tar -czvf "$TEMP_DIR/home.tar.gz" $exclude_args ~/ 2>/dev/null
    
    local size=$(du -h "$TEMP_DIR/home.tar.gz" | cut -f1)
    log "${GREEN}✓ Home backup created: $size${NC}"
}

backup_config_files() {
    log "${CYAN}[2/7] Backing up configuration files...${NC}"
    
    local configs=(
        "$HOME/.bashrc"
        "$HOME/.bash_profile"
        "$HOME/.profile"
        "$HOME/.bash_aliases"
        "$HOME/.gitconfig"
        "$HOME/.gitignore"
        "$HOME/.nanorc"
        "$HOME/.vimrc"
        "$HOME/.inputrc"
        "$HOME/.curlrc"
        "$HOME/.wget-hsts"
        "$HOME/.screenrc"
    )
    
    for config in "${configs[@]}"; do
        if [ -f "$config" ]; then
            cp "$config" "$TEMP_DIR/configs/"
            log "  ${GREEN}✓${NC} $(basename $config)"
        fi
    done
    
    # SSH directory
    if [ -d "$HOME/.ssh" ]; then
        cp -r "$HOME/.ssh" "$TEMP_DIR/configs/"
        log "  ${GREEN}✓${NC} .ssh directory"
    fi
    
    # GPG directory
    if [ -d "$HOME/.gnupg" ]; then
        cp -r "$HOME/.gnupg" "$TEMP_DIR/configs/"
        log "  ${GREEN}✓${NC} .gnupg directory"
    fi
}

backup_package_lists() {
    log "${CYAN}[3/7] Saving package lists...${NC}"
    
    # System packages
    pkg list-installed | cut -d'/' -f1 > "$TEMP_DIR/lists/packages.txt"
    log "  ${GREEN}✓${NC} packages.txt"
    
    # Python packages
    if command -v pip &> /dev/null; then
        pip list --format=freeze > "$TEMP_DIR/lists/requirements.txt" 2>/dev/null
        log "  ${GREEN}✓${NC} requirements.txt"
    fi
    
    # Node packages
    if command -v npm &> /dev/null; then
        npm list -g --depth=0 > "$TEMP_DIR/lists/npm_global.txt" 2>/dev/null
        log "  ${GREEN}✓${NC} npm_global.txt"
    fi
    
    # Go packages
    if command -v go &> /dev/null; then
        go list -m all > "$TEMP_DIR/lists/go_modules.txt" 2>/dev/null
        log "  ${GREEN}✓${NC} go_modules.txt"
    fi
}

backup_cron_jobs() {
    log "${CYAN}[4/7] Saving cron jobs...${NC}"
    
    if command -v crontab &> /dev/null; then
        crontab -l > "$TEMP_DIR/lists/crontab.txt" 2>/dev/null
        if [ -s "$TEMP_DIR/lists/crontab.txt" ]; then
            log "  ${GREEN}✓${NC} crontab.txt"
        else
            rm "$TEMP_DIR/lists/crontab.txt"
            log "  ${YELLOW}○${NC} No cron jobs found"
        fi
    fi
}

backup_environment() {
    log "${CYAN}[5/7] Saving environment info...${NC}"
    
    # Environment variables
    env > "$TEMP_DIR/lists/environment.txt"
    
    # PATH
    echo "$PATH" | tr ':' '\n' > "$TEMP_DIR/lists/path.txt"
    
    # Termux version
    echo "TERMUX_VERSION=$TERMUX_VERSION" >> "$TEMP_DIR/lists/environment.txt"
    
    # Device info
    {
        echo "=== Device Info ==="
        echo "Date: $(date)"
        echo "Termux Version: $TERMUX_VERSION"
        echo "Android Version: $(getprop ro.build.version.release)"
        echo "Device: $(getprop ro.product.model)"
        echo "Architecture: $(uname -m)"
    } > "$TEMP_DIR/lists/device_info.txt"
    
    log "  ${GREEN}✓${NC} Environment and device info saved"
}

create_final_archive() {
    log "${CYAN}[6/7] Creating final archive...${NC}"
    
    cd "$BACKUP_BASE_DIR"
    tar -czvf "${BACKUP_NAME}.tar.gz" "$BACKUP_NAME"
    
    # Remove temp directory
    rm -rf "$TEMP_DIR"
    
    local size=$(du -h "${BACKUP_NAME}.tar.gz" | cut -f1)
    log "${GREEN}✓ Final archive created: $size${NC}"
}

cleanup_old_backups() {
    log "${CYAN}[7/7] Cleaning up old backups...${NC}"
    
    # Keep only last 5 backups
    local count=$(ls -1 "$BACKUP_BASE_DIR"/termux_backup_*.tar.gz 2>/dev/null | wc -l)
    
    if [ "$count" -gt 5 ]; then
        ls -1t "$BACKUP_BASE_DIR"/termux_backup_*.tar.gz | tail -n +6 | xargs rm -f
        log "  ${GREEN}✓${NC} Removed old backups (keeping last 5)"
    else
        log "  ${GREEN}✓${NC} No cleanup needed"
    fi
}

show_summary() {
    local final_size=$(du -h "$BACKUP_BASE_DIR/${BACKUP_NAME}.tar.gz" | cut -f1)
    local file_count=$(tar -tzf "$BACKUP_BASE_DIR/${BACKUP_NAME}.tar.gz" | wc -l)
    
    echo ""
    echo -e "${GREEN}╔═════════════════════════════════════════════════════════╗${NC}"
    echo -e "${GREEN}║               BACKUP COMPLETED!                         ║${NC}"
    echo -e "${GREEN}╚═════════════════════════════════════════════════════════╝${NC}"
    echo ""
    echo -e "  📁 Location: ${BLUE}$BACKUP_BASE_DIR/${BACKUP_NAME}.tar.gz${NC}"
    echo -e "  📦 Size: ${BLUE}$final_size${NC}"
    echo -e "  📄 Files: ${BLUE}$file_count${NC}"
    echo -e "  📅 Date: ${BLUE}$(date)${NC}"
    echo ""
}

# ═══════════════════════════════════════════════════════════
# MAIN EXECUTION
# ═══════════════════════════════════════════════════════════

main() {
    show_banner
    check_storage
    create_directories
    
    backup_home_directory
    backup_config_files
    backup_package_lists
    backup_cron_jobs
    backup_environment
    create_final_archive
    cleanup_old_backups
    
    show_summary
}

# Run main function
main "$@"
```

#### Quick Backup Script

```bash
#!/bin/bash
# Quick backup script for daily use

BACKUP_DIR=~/storage/downloads/termux_backups
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p "$BACKUP_DIR"

# Quick home backup
tar -czvf "$BACKUP_DIR/quick_${DATE}.tar.gz" \
    --exclude="$HOME/.cache" \
    --exclude="$HOME/node_modules" \
    --exclude="$HOME/storage" \
    ~/ 2>/dev/null

# Package list
pkg list-installed | cut -d'/' -f1 > "$BACKUP_DIR/packages_${DATE}.txt"

echo "Backup saved: $BACKUP_DIR/quick_${DATE}.tar.gz"
```

### 5. Cloud Backup Options

#### Rclone Setup (Google Drive, Dropbox, etc.)

```bash
# Install rclone
pkg install rclone

# Configure Google Drive
rclone config

# Setup steps:
# n) New remote
# name> gdrive
# Storage> drive (or number for Google Drive)
# client_id> (press Enter for default)
# client_secret> (press Enter for default)
# scope> 1 (full access)
# root_folder_id> (press Enter)
# service_account_file> (press Enter)
# y/n> n (not advanced)
# y/n> y (auto config - opens browser)
# Authenticate in browser
# y/n> n (shared drive)
# y/n> y (confirm)

# Upload backup
rclone copy ~/storage/downloads/backup.tar.gz gdrive:TermuxBackups/

# Download backup
rclone copy gdrive:TermuxBackups/backup.tar.gz ~/storage/downloads/

# Sync entire backup folder
rclone sync ~/storage/downloads/termux_backups gdrive:TermuxBackups/

# List remote files
rclone ls gdrive:TermuxBackups/
```

#### GitHub Backup for Scripts

```bash
# Initialize git in scripts directory
cd ~/scripts
git init
git add .
git commit -m "Initial backup"

# Create GitHub repo and push
git remote add origin https://github.com/username/termux-scripts.git
git branch -M main
git push -u origin main

# Daily backup script
cat > ~/scripts/git_backup.sh << 'EOF'
#!/bin/bash
cd ~/scripts
git add .
git commit -m "Backup $(date +%Y%m%d)"
git push
EOF

chmod +x ~/scripts/git_backup.sh
```

### 6. Restore Process

```bash
#!/bin/bash
#################################################################
# TERMUX RESTORE SCRIPT
# Author: T3rmuxk1ng
# Version: 1.0
# Description: Restore Termux from backup archive
#################################################################

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m'

BACKUP_FILE=$1

# Check if backup file provided
if [ -z "$BACKUP_FILE" ]; then
    echo -e "${RED}Usage: $0 <backup_file.tar.gz>${NC}"
    echo ""
    echo "Available backups:"
    ls -lh ~/storage/downloads/termux_backups/*.tar.gz 2>/dev/null
    exit 1
fi

# Check if file exists
if [ ! -f "$BACKUP_FILE" ]; then
    echo -e "${RED}Error: Backup file not found!${NC}"
    exit 1
fi

echo -e "${GREEN}╔═════════════════════════════════════════════════════════╗${NC}"
echo -e "${GREEN}║           TERMUX RESTORE SCRIPT                         ║${NC}"
echo -e "${GREEN}╚═════════════════════════════════════════════════════════╝${NC}"
echo ""

# Create temp directory
TEMP_DIR=$(mktemp -d)

echo -e "${YELLOW}[1/5] Extracting backup archive...${NC}"
tar -xzvf "$BACKUP_FILE" -C "$TEMP_DIR"

# Find the extracted directory
BACKUP_DIR=$(find "$TEMP_DIR" -mindepth 1 -maxdepth 1 -type d | head -1)

echo -e "${YELLOW}[2/5] Restoring home directory...${NC}"
if [ -f "$BACKUP_DIR/home.tar.gz" ]; then
    tar -xzvf "$BACKUP_DIR/home.tar.gz" -C ~/
    echo -e "${GREEN}✓ Home directory restored${NC}"
fi

echo -e "${YELLOW}[3/5] Restoring configuration files...${NC}"
if [ -d "$BACKUP_DIR/configs" ]; then
    cp -r "$BACKUP_DIR/configs"/.* ~/ 2>/dev/null
    cp -r "$BACKUP_DIR/configs"/* ~/ 2>/dev/null
    echo -e "${GREEN}✓ Config files restored${NC}"
fi

echo -e "${YELLOW}[4/5] Restoring packages...${NC}"
if [ -f "$BACKUP_DIR/lists/packages.txt" ]; then
    echo "Installing packages from list..."
    pkg install -y $(cat "$BACKUP_DIR/lists/packages.txt") 2>/dev/null
    echo -e "${GREEN}✓ Packages restored${NC}"
fi

echo -e "${YELLOW}[5/5] Restoring Python packages...${NC}"
if [ -f "$BACKUP_DIR/lists/requirements.txt" ]; then
    pip install -r "$BACKUP_DIR/lists/requirements.txt"
    echo -e "${GREEN}✓ Python packages restored${NC}"
fi

# Cleanup
rm -rf "$TEMP_DIR"

echo ""
echo -e "${GREEN}╔═════════════════════════════════════════════════════════╗${NC}"
echo -e "${GREEN}║              RESTORE COMPLETED!                         ║${NC}"
echo -e "${GREEN}╚═════════════════════════════════════════════════════════╝${NC}"
echo ""
echo -e "${YELLOW}Please restart Termux for all changes to take effect.${NC}"
```

### 7. New Phone Migration Guide

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NEW PHONE MIGRATION GUIDE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  STEP 1: PREPARE OLD PHONE                                               │
│  ═══════════════════════════                                             │
│  □ Run complete backup script                                            │
│  □ Verify backup was created successfully                                │
│  □ Copy backup to cloud storage (Google Drive/Dropbox)                   │
│  □ Alternatively, transfer via USB to PC                                 │
│  □ Note down any important passwords/API keys separately                 │
│  □ Document any manual configurations                                    │
│                                                                          │
│  STEP 2: TRANSFER BACKUP                                                  │
│  ═══════════════════════                                                  │
│  Option A - Cloud Download                                               │
│  ├── Install Google Drive/Dropbox on new phone                           │
│  ├── Download backup file                                                │
│  └── Place in Downloads folder                                           │
│                                                                          │
│  Option B - Direct Transfer                                              │
│  ├── Use USB OTG with flash drive                                        │
│  ├── Use ShareIt/Xender                                                  │
│  └── Use Bluetooth (slow for large files)                                │
│                                                                          │
│  STEP 3: SETUP NEW PHONE                                                 │
│  ══════════════════════                                                  │
│  □ Install Termux from F-Droid (NOT Play Store!)                         │
│  □ Run: pkg update && pkg upgrade -y                                     │
│  □ Run: termux-setup-storage (grant permission)                          │
│  □ Install git: pkg install git                                          │
│  □ Install python: pkg install python                                    │
│                                                                          │
│  STEP 4: RESTORE BACKUP                                                   │
│  ═════════════════════                                                    │
│  □ Copy restore script to home directory                                 │
│  □ Run: chmod +x restore.sh                                              │
│  □ Run: ./restore.sh /sdcard/Download/backup.tar.gz                      │
│  □ Wait for completion                                                   │
│  □ Restart Termux                                                        │
│                                                                          │
│  STEP 5: VERIFY RESTORE                                                   │
│  ═════════════════════                                                    │
│  □ Check .bashrc loaded: echo $PS1                                       │
│  □ List custom scripts: ls ~/scripts/                                    │
│  □ Test SSH keys: ssh -T git@github.com                                  │
│  □ Run a test script                                                     │
│  □ Check installed packages: pkg list-installed                          │
│                                                                          │
│  STEP 6: TROUBLESHOOTING                                                  │
│  ═════════════════════                                                    │
│  If scripts don't work:                                                  │
│  ├── Check file permissions: ls -la ~/scripts/                           │
│  ├── Fix permissions: chmod +x ~/scripts/*.sh                            │
│  └── Check shebang lines: head -1 script.sh                              │
│                                                                          │
│  If packages fail to install:                                            │
│  ├── Update first: pkg update                                            │
│  ├── Try individual installs                                             │
│  └── Check if package name changed                                       │
│                                                                          │
│  If SSH keys don't work:                                                 │
│  ├── Check permissions: chmod 600 ~/.ssh/id_rsa                          │
│  ├── Verify key exists: ls -la ~/.ssh/                                   │
│  └── Test connection manually                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 8. Backup Best Practices

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BACKUP BEST PRACTICES                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. THE 3-2-1 BACKUP RULE                                                │
│  ══════════════════════════                                               │
│                                                                          │
│     ┌─────────────┐                                                      │
│     │   3 COPIES  │ → Original + 2 backup copies                         │
│     └─────────────┘                                                      │
│            │                                                             │
│            ▼                                                             │
│     ┌─────────────┐                                                      │
│     │ 2 MEDIAS    │ → Phone storage + Cloud/External                     │
│     └─────────────┘                                                      │
│            │                                                             │
│            ▼                                                             │
│     ┌─────────────┐                                                      │
│     │ 1 OFFSITE   │ → Cloud storage (Google Drive, etc.)                 │
│     └─────────────┘                                                      │
│                                                                          │
│  2. BACKUP SCHEDULE                                                       │
│  ═════════════════                                                        │
│                                                                          │
│     User Type          │ Recommended Frequency                           │
│     ───────────────────┼────────────────────────────────                 │
│     Active Developer   │ Daily                                          │
│     Regular User       │ Weekly                                         │
│     Casual User        │ Bi-weekly                                      │
│     Before Changes     │ Always                                         │
│                                                                          │
│  3. WHAT NOT TO BACKUP                                                    │
│  ══════════════════════                                                   │
│                                                                          │
│     ✗ Cache directories (.cache, npm cache)                              │
│     ✗ node_modules (can be reinstalled)                                  │
│     ✗ Build artifacts                                                    │
│     ✗ Temporary files                                                    │
│     ✗ Large media files (unless needed)                                  │
│     ✗ .git objects (re-clone instead)                                    │
│                                                                          │
│  4. TESTING BACKUPS                                                       │
│  ═════════════════                                                        │
│                                                                          │
│     Monthly restore test:                                                │
│     □ Create test directory                                              │
│     □ Extract backup                                                     │
│     □ Verify file count                                                  │
│     □ Check critical files                                               │
│     □ Test restore script                                                │
│                                                                          │
│  5. SECURITY CONSIDERATIONS                                               │
│  ══════════════════════════                                               │
│                                                                          │
│     For sensitive backups:                                               │
│                                                                          │
│     # Encrypt with password                                              │
│     tar -czvf - ~/ | gpg -c > backup.tar.gz.gpg                          │
│                                                                          │
│     # Decrypt                                                            │
│     gpg -d backup.tar.gz.gpg | tar -xzvf -                               │
│                                                                          │
│     Or use openssl:                                                      │
│     tar -czvf - ~/ | openssl enc -aes-256-cbc > backup.enc               │
│                                                                          │
│  6. DOCUMENTATION                                                         │
│  ════════════════                                                         │
│                                                                          │
│     Keep a SETUP_NOTES.txt file with:                                    │
│     - Custom package sources                                             │
│     - Non-standard configurations                                        │
│     - API keys location (not the keys themselves!)                       │
│     - SSH key passphrases hint                                           │
│     - Important paths                                                    │
│     - Manual installation steps                                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 💻 FULL BACKUP SCRIPT

```bash
#!/bin/bash
#################################################################
#                                                               #
#  ████████╗██╗   ██╗██████╗ ███████╗██████╗                    #
#  ╚══██╔══╝██║   ██║██╔══██╗██╔════╝██╔══██╗                   #
#     ██║   ██║   ██║██║  ██║█████╗  ██████╔╝                   #
#     ██║   ██║   ██║██║  ██║██╔══╝  ██╔══██╗                   #
#     ██║   ╚██████╔╝██████╔╝███████╗██║  ██║                   #
#     ╚═╝    ╚═════╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝                   #
#                                                               #
#  COMPLETE BACKUP & RESTORE SOLUTION FOR TERMUX                #
#  Version: 3.0                                                 #
#  Author: T3rmuxk1ng                                           #
#                                                               #
#################################################################

# ═══════════════════════════════════════════════════════════════
# CONFIGURATION
# ═══════════════════════════════════════════════════════════════

# Colors
readonly RED='\033[0;31m'
readonly GREEN='\033[0;32m'
readonly YELLOW='\033[1;33m'
readonly BLUE='\033[0;34m'
readonly PURPLE='\033[0;35m'
readonly CYAN='\033[0;36m'
readonly WHITE='\033[1;37m'
readonly NC='\033[0m'

# Paths
readonly BACKUP_BASE="${HOME}/storage/downloads/termux_backups"
readonly LOG_FILE="${BACKUP_BASE}/backup.log"
readonly DATE=$(date +%Y%m%d_%H%M%S)
readonly BACKUP_NAME="termux_backup_${DATE}"

# Exclusions
readonly EXCLUDE_DIRS=(
    ".cache"
    ".npm/_cacache"
    ".local/share/Trash"
    "node_modules"
    "__pycache__"
    ".git/objects"
    "storage"
)

# ═══════════════════════════════════════════════════════════════
# UTILITY FUNCTIONS
# ═══════════════════════════════════════════════════════════════

log() {
    local level="$1"; shift
    local message="$*"
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    echo -e "${level}${message}${NC}"
    echo "[${timestamp}] ${message}" >> "$LOG_FILE"
}

show_banner() {
    clear
    echo -e "${CYAN}"
    cat << "EOF"
╔═══════════════════════════════════════════════════════════════╗
║                                                               ║
║   ████████╗██╗   ██╗██████╗ ███████╗██████╗                   ║
║   ╚══██╔══╝██║   ██║██╔══██╗██╔════╝██╔══██╗                  ║
║      ██║   ██║   ██║██║  ██║█████╗  ██████╔╝                  ║
║      ██║   ██║   ██║██║  ██║██╔══╝  ██╔══██╗                  ║
║      ██║   ╚██████╔╝██████╔╝███████╗██║  ██║                  ║
║      ╚═╝    ╚═════╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝                  ║
║                                                               ║
║         COMPLETE BACKUP & RESTORE SOLUTION                    ║
║                    Version 3.0                                ║
║                   by T3rmuxk1ng                               ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
EOF
    echo -e "${NC}"
}

check_dependencies() {
    local missing=()
    
    command -v tar &>/dev/null || missing+=("tar")
    command -v gzip &>/dev/null || missing+=("gzip")
    
    if [ ${#missing[@]} -ne 0 ]; then
        log "$RED" "Missing dependencies: ${missing[*]}"
        exit 1
    fi
}

check_storage() {
    if [ ! -d "${HOME}/storage/downloads" ]; then
        log "$RED" "Storage not accessible!"
        log "$YELLOW" "Please run: termux-setup-storage"
        exit 1
    fi
}

get_size() {
    du -h "$1" 2>/dev/null | cut -f1
}

format_duration() {
    local seconds=$1
    local minutes=$((seconds / 60))
    local secs=$((seconds % 60))
    printf "%02d:%02d" $minutes $secs
}

# ═══════════════════════════════════════════════════════════════
# BACKUP FUNCTIONS
# ═══════════════════════════════════════════════════════════════

backup_home() {
    log "$CYAN" "[1/6] Creating home directory backup..."
    
    local exclude_args=""
    for dir in "${EXCLUDE_DIRS[@]}"; do
        exclude_args="${exclude_args} --exclude=${HOME}/${dir}"
    done
    
    if tar -czvf "${TEMP_DIR}/home.tar.gz" $exclude_args "${HOME}/" 2>/dev/null; then
        local size=$(get_size "${TEMP_DIR}/home.tar.gz")
        log "$GREEN" "✓ Home backup: $size"
        return 0
    else
        log "$RED" "✗ Home backup failed"
        return 1
    fi
}

backup_configs() {
    log "$CYAN" "[2/6] Backing up configuration files..."
    
    local config_dir="${TEMP_DIR}/configs"
    mkdir -p "$config_dir"
    
    local configs=(
        ".bashrc:.bashrc"
        ".bash_profile:.bash_profile"
        ".profile:.profile"
        ".bash_aliases:.bash_aliases"
        ".bash_completion:.bash_completion"
        ".gitconfig:.gitconfig"
        ".gitignore:.gitignore"
        ".nanorc:.nanorc"
        ".vimrc:.vimrc"
        ".inputrc:.inputrc"
        ".curlrc:.curlrc"
        ".tmux.conf:.tmux.conf"
        ".editorconfig:.editorconfig"
    )
    
    local count=0
    for config in "${configs[@]}"; do
        local src="${HOME}/${config%%:*}"
        local dst="${config_dir}/${config##*:}"
        
        if [ -f "$src" ]; then
            cp "$src" "$dst"
            ((count++))
        fi
    done
    
    # Backup directories
    [ -d "${HOME}/.ssh" ] && cp -r "${HOME}/.ssh" "${config_dir}/"
    [ -d "${HOME}/.gnupg" ] && cp -r "${HOME}/.gnupg" "${config_dir}/"
    [ -d "${HOME}/.config" ] && cp -r "${HOME}/.config" "${config_dir}/"
    
    log "$GREEN" "✓ Config files backed up: $count files"
}

backup_package_lists() {
    log "$CYAN" "[3/6] Saving package lists..."
    
    local list_dir="${TEMP_DIR}/lists"
    mkdir -p "$list_dir"
    
    # Termux packages
    pkg list-installed 2>/dev/null | cut -d'/' -f1 > "${list_dir}/packages.txt"
    
    # Python packages
    if command -v pip &>/dev/null; then
        pip list --format=freeze 2>/dev/null > "${list_dir}/requirements.txt"
    fi
    
    # pip3 specific
    if command -v pip3 &>/dev/null && [ "$pip3" != "$pip" ]; then
        pip3 list --format=freeze 2>/dev/null > "${list_dir}/requirements3.txt"
    fi
    
    # Node.js global packages
    if command -v npm &>/dev/null; then
        npm list -g --depth=0 2>/dev/null > "${list_dir}/npm_global.txt"
        npm config list 2>/dev/null > "${list_dir}/npm_config.txt"
    fi
    
    # Go packages
    if command -v go &>/dev/null; then
        go list -m all 2>/dev/null > "${list_dir}/go_modules.txt"
        go env 2>/dev/null > "${list_dir}/go_env.txt"
    fi
    
    # Rust/Cargo packages
    if command -v cargo &>/dev/null; then
        cargo install --list 2>/dev/null > "${list_dir}/cargo_installed.txt"
    fi
    
    # Crontab
    if command -v crontab &>/dev/null; then
        crontab -l 2>/dev/null > "${list_dir}/crontab.txt"
    fi
    
    log "$GREEN" "✓ Package lists saved"
}

backup_environment() {
    log "$CYAN" "[4/6] Saving environment information..."
    
    local env_dir="${TEMP_DIR}/environment"
    mkdir -p "$env_dir"
    
    # Environment variables
    env > "${env_dir}/env.txt"
    
    # PATH components
    echo "$PATH" | tr ':' '\n' > "${env_dir}/path.txt"
    
    # System information
    {
        echo "=== System Information ==="
        echo "Backup Date: $(date)"
        echo "Termux Version: ${TERMUX_VERSION:-unknown}"
        echo "Android Version: $(getprop ro.build.version.release 2>/dev/null || echo 'unknown')"
        echo "Device Model: $(getprop ro.product.model 2>/dev/null || echo 'unknown')"
        echo "Device Brand: $(getprop ro.product.brand 2>/dev/null || echo 'unknown')"
        echo "Architecture: $(uname -m)"
        echo "Kernel: $(uname -r)"
        echo ""
        echo "=== Disk Usage ==="
        df -h | head -5
        echo ""
        echo "=== Memory Info ==="
        free -h
    } > "${env_dir}/system_info.txt"
    
    log "$GREEN" "✓ Environment saved"
}

backup_projects() {
    log "$CYAN" "[5/6] Checking for projects..."
    
    local project_dirs=(
        "projects"
        "workspace"
        "code"
        "scripts"
        "tools"
        "bin"
    )
    
    local found=0
    local project_backup="${TEMP_DIR}/projects"
    mkdir -p "$project_backup"
    
    for dir in "${project_dirs[@]}"; do
        if [ -d "${HOME}/${dir}" ]; then
            cp -r "${HOME}/${dir}" "${project_backup}/"
            ((found++))
        fi
    done
    
    if [ $found -gt 0 ]; then
        log "$GREEN" "✓ Projects backed up: $found directories"
    else
        rmdir "$project_backup"
        log "$YELLOW" "○ No project directories found"
    fi
}

create_archive() {
    log "$CYAN" "[6/6] Creating final archive..."
    
    local archive="${BACKUP_BASE}/${BACKUP_NAME}.tar.gz"
    
    if tar -czvf "$archive" -C "${BACKUP_BASE}" "$BACKUP_NAME"; then
        # Remove temp directory
        rm -rf "${TEMP_DIR}"
        
        local size=$(get_size "$archive")
        log "$GREEN" "✓ Archive created: $size"
        
        # Generate checksum
        sha256sum "$archive" > "${archive}.sha256"
        log "$GREEN" "✓ Checksum generated"
        
        return 0
    else
        log "$RED" "✗ Archive creation failed"
        return 1
    fi
}

cleanup_old_backups() {
    local keep=5
    local count=$(ls -1 "${BACKUP_BASE}"/termux_backup_*.tar.gz 2>/dev/null | wc -l)
    
    if [ "$count" -gt "$keep" ]; then
        log "$YELLOW" "Cleaning up old backups..."
        ls -1t "${BACKUP_BASE}"/termux_backup_*.tar.gz | tail -n +$((keep + 1)) | xargs rm -f
        local removed=$((count - keep))
        log "$GREEN" "✓ Removed $removed old backup(s)"
    fi
}

# ═══════════════════════════════════════════════════════════════
# RESTORE FUNCTIONS
# ═══════════════════════════════════════════════════════════════

list_backups() {
    echo -e "\n${WHITE}Available Backups:${NC}\n"
    printf "  %-35s %-10s %s\n" "Filename" "Size" "Date"
    printf "  %s\n" "$(printf '─%.0s' {1..60})"
    
    ls -lht "${BACKUP_BASE}"/termux_backup_*.tar.gz 2>/dev/null | while read -r line; do
        local file=$(echo "$line" | awk '{print $NF}')
        local size=$(echo "$line" | awk '{print $5}')
        local date=$(echo "$line" | awk '{print $6" "$7}')
        printf "  %-35s %-10s %s\n" "$(basename "$file")" "$size" "$date"
    done
    
    echo ""
}

restore_backup() {
    local backup_file="$1"
    
    if [ ! -f "$backup_file" ]; then
        log "$RED" "Backup file not found: $backup_file"
        return 1
    fi
    
    log "$CYAN" "Starting restore from: $(basename $backup_file)"
    
    # Verify checksum if available
    if [ -f "${backup_file}.sha256" ]; then
        log "$YELLOW" "Verifying checksum..."
        if sha256sum -c "${backup_file}.sha256" &>/dev/null; then
            log "$GREEN" "✓ Checksum verified"
        else
            log "$RED" "✗ Checksum verification failed!"
            read -p "Continue anyway? (y/N): " confirm
            [ "$confirm" != "y" ] && [ "$confirm" != "Y" ] && return 1
        fi
    fi
    
    # Extract to temp
    local temp_restore=$(mktemp -d)
    tar -xzvf "$backup_file" -C "$temp_restore"
    
    local backup_dir=$(find "$temp_restore" -mindepth 1 -maxdepth 1 -type d | head -1)
    
    # Restore home
    if [ -f "${backup_dir}/home.tar.gz" ]; then
        log "$YELLOW" "Restoring home directory..."
        tar -xzvf "${backup_dir}/home.tar.gz" -C ~/
    fi
    
    # Restore configs
    if [ -d "${backup_dir}/configs" ]; then
        log "$YELLOW" "Restoring configuration files..."
        cp -r "${backup_dir}/configs"/.* ~/ 2>/dev/null
        cp -r "${backup_dir}/configs"/* ~/ 2>/dev/null
    fi
    
    # Restore packages
    if [ -f "${backup_dir}/lists/packages.txt" ]; then
        log "$YELLOW" "Restoring packages..."
        xargs pkg install -y < "${backup_dir}/lists/packages.txt"
    fi
    
    # Restore Python packages
    if [ -f "${backup_dir}/lists/requirements.txt" ]; then
        log "$YELLOW" "Restoring Python packages..."
        pip install -r "${backup_dir}/lists/requirements.txt"
    fi
    
    # Cleanup
    rm -rf "$temp_restore"
    
    log "$GREEN" "✓ Restore completed!"
    log "$YELLOW" "Please restart Termux for all changes to take effect."
}

# ═══════════════════════════════════════════════════════════════
# CLOUD BACKUP FUNCTIONS
# ═══════════════════════════════════════════════════════════════

upload_to_cloud() {
    local backup_file="$1"
    
    if ! command -v rclone &>/dev/null; then
        log "$RED" "rclone not installed. Run: pkg install rclone"
        return 1
    fi
    
    log "$YELLOW" "Available remotes:"
    rclone listremotes
    
    read -p "Enter remote name: " remote
    
    if [ -z "$remote" ]; then
        log "$RED" "No remote specified"
        return 1
    fi
    
    log "$CYAN" "Uploading to $remote..."
    rclone copy "$backup_file" "${remote}:TermuxBackups/" -P
    
    if [ $? -eq 0 ]; then
        log "$GREEN" "✓ Upload completed"
    else
        log "$RED" "✗ Upload failed"
    fi
}

# ═══════════════════════════════════════════════════════════════
# MAIN MENU
# ═══════════════════════════════════════════════════════════════

show_menu() {
    echo -e "\n${WHITE}╔═══════════════════════════════════════════════════════════════╗${NC}"
    echo -e "${WHITE}║                    MAIN MENU                                  ║${NC}"
    echo -e "${WHITE}╠═══════════════════════════════════════════════════════════════╣${NC}"
    echo -e "${WHITE}║  ${GREEN}1${NC}  ${WHITE}Create Full Backup${NC}                                 ${WHITE}║${NC}"
    echo -e "${WHITE}║  ${GREEN}2${NC}  ${WHITE}Quick Backup (home only)${NC}                           ${WHITE}║${NC}"
    echo -e "${WHITE}║  ${GREEN}3${NC}  ${WHITE}List Available Backups${NC}                             ${WHITE}║${NC}"
    echo -e "${WHITE}║  ${GREEN}4${NC}  ${WHITE}Restore from Backup${NC}                                ${WHITE}║${NC}"
    echo -e "${WHITE}║  ${GREEN}5${NC}  ${WHITE}Upload to Cloud${NC}                                    ${WHITE}║${NC}"
    echo -e "${WHITE}║  ${GREEN}6${NC}  ${WHITE}Backup Info${NC}                                        ${WHITE}║${NC}"
    echo -e "${WHITE}║  ${GREEN}7${NC}  ${WHITE}Settings${NC}                                           ${WHITE}║${NC}"
    echo -e "${WHITE}║  ${RED}0${NC}  ${WHITE}Exit${NC}                                                ${WHITE}║${NC}"
    echo -e "${WHITE}╚═══════════════════════════════════════════════════════════════╝${NC}"
    echo ""
}

show_info() {
    echo -e "\n${WHITE}╔═══════════════════════════════════════════════════════════════╗${NC}"
    echo -e "${WHITE}║                    BACKUP INFORMATION                         ║${NC}"
    echo -e "${WHITE}╚═══════════════════════════════════════════════════════════════╝${NC}\n"
    
    echo -e "${CYAN}Backup Location:${NC} ${BACKUP_BASE}"
    echo -e "${CYAN}Log File:${NC} ${LOG_FILE}"
    echo ""
    
    # Count backups
    local count=$(ls -1 "${BACKUP_BASE}"/termux_backup_*.tar.gz 2>/dev/null | wc -l)
    echo -e "${CYAN}Total Backups:${NC} $count"
    
    # Total size
    if [ $count -gt 0 ]; then
        local total_size=$(du -sh "${BACKUP_BASE}" 2>/dev/null | cut -f1)
        echo -e "${CYAN}Total Size:${NC} $total_size"
        
        # Latest backup
        local latest=$(ls -t "${BACKUP_BASE}"/termux_backup_*.tar.gz 2>/dev/null | head -1)
        echo -e "${CYAN}Latest Backup:${NC} $(basename $latest)"
    fi
    
    echo ""
}

perform_backup() {
    local start_time=$(date +%s)
    
    # Create directories
    mkdir -p "$BACKUP_BASE"
    TEMP_DIR="${BACKUP_BASE}/${BACKUP_NAME}"
    mkdir -p "$TEMP_DIR"
    
    # Perform backup steps
    backup_home
    backup_configs
    backup_package_lists
    backup_environment
    backup_projects
    create_archive
    
    # Calculate duration
    local end_time=$(date +%s)
    local duration=$((end_time - start_time))
    
    # Cleanup
    cleanup_old_backups
    
    # Summary
    echo ""
    echo -e "${GREEN}╔═══════════════════════════════════════════════════════════════╗${NC}"
    echo -e "${GREEN}║                   BACKUP COMPLETED!                           ║${NC}"
    echo -e "${GREEN}╠═══════════════════════════════════════════════════════════════╣${NC}"
    echo -e "${GREEN}║${NC}                                                               ${GREEN}║${NC}"
    echo -e "${GREEN}║${NC}  ${WHITE}Location:${NC} ${BACKUP_BASE}/${BACKUP_NAME}.tar.gz          ${GREEN}║${NC}"
    echo -e "${GREEN}║${NC}  ${WHITE}Duration:${NC} $(format_duration $duration)                                        ${GREEN}║${NC}"
    echo -e "${GREEN}║${NC}                                                               ${GREEN}║${NC}"
    echo -e "${GREEN}╚═══════════════════════════════════════════════════════════════╝${NC}"
    echo ""
}

quick_backup() {
    log "$CYAN" "Creating quick backup..."
    
    local quick_name="quick_backup_${DATE}.tar.gz"
    local quick_path="${BACKUP_BASE}/${quick_name}"
    
    mkdir -p "$BACKUP_BASE"
    
    tar -czvf "$quick_path" \
        --exclude="${HOME}/.cache" \
        --exclude="${HOME}/node_modules" \
        --exclude="${HOME}/storage" \
        "${HOME}/" 2>/dev/null
    
    pkg list-installed | cut -d'/' -f1 > "${BACKUP_BASE}/packages_${DATE}.txt"
    
    log "$GREEN" "✓ Quick backup created: $(get_size $quick_path)"
}

# ═══════════════════════════════════════════════════════════════
# MAIN EXECUTION
# ═══════════════════════════════════════════════════════════════

main() {
    show_banner
    check_dependencies
    check_storage
    
    # Handle command line arguments
    case "$1" in
        backup)
            perform_backup
            exit 0
            ;;
        restore)
            restore_backup "$2"
            exit 0
            ;;
        list)
            list_backups
            exit 0
            ;;
        quick)
            quick_backup
            exit 0
            ;;
    esac
    
    # Interactive menu
    while true; do
        show_menu
        read -p "Enter choice: " choice
        
        case $choice in
            1) perform_backup ;;
            2) quick_backup ;;
            3) list_backups ;;
            4)
                list_backups
                read -p "Enter backup filename: " backup_file
                restore_backup "${BACKUP_BASE}/${backup_file}"
                ;;
            5)
                list_backups
                read -p "Enter backup filename to upload: " backup_file
                upload_to_cloud "${BACKUP_BASE}/${backup_file}"
                ;;
            6) show_info ;;
            7) echo -e "\n${YELLOW}Settings coming soon...${NC}" ;;
            0)
                echo -e "\n${GREEN}Thank you for using Termux Backup!${NC}"
                exit 0
                ;;
            *)
                echo -e "${RED}Invalid choice${NC}"
                ;;
        esac
        
        read -p "Press Enter to continue..."
    done
}

# Run main
main "$@"
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Manual Backup

```bash
# Task: Create a manual backup of your Termux environment

# Step 1: Create backup directory
mkdir -p ~/storage/downloads/my_backups

# Step 2: Backup home directory
tar -czvf ~/storage/downloads/my_backups/home_$(date +%Y%m%d).tar.gz ~/

# Step 3: Save packages list
pkg list-installed | cut -d'/' -f1 > ~/storage/downloads/my_backups/packages.txt

# Step 4: Verify backup
ls -lh ~/storage/downloads/my_backups/

# Step 5: Test extraction (to temp directory)
mkdir -p /tmp/test_restore
tar -tzvf ~/storage/downloads/my_backups/home_*.tar.gz | head -20
```

### Exercise 2: Create Automated Backup Script

```bash
# Task: Create a simple automated backup script

# Step 1: Create script
cat > ~/my_backup.sh << 'EOF'
#!/bin/bash
# Simple Backup Script

BACKUP_DIR=~/storage/downloads/auto_backups
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p "$BACKUP_DIR"

echo "Starting backup..."

# Home backup
tar -czvf "$BACKUP_DIR/home_$DATE.tar.gz" \
    --exclude="$HOME/.cache" \
    --exclude="$HOME/node_modules" \
    --exclude="$HOME/storage" \
    ~/ 2>/dev/null

# Packages
pkg list-installed | cut -d'/' -f1 > "$BACKUP_DIR/packages_$DATE.txt"

# Cleanup old (keep last 3)
ls -t "$BACKUP_DIR"/home_*.tar.gz | tail -n +4 | xargs rm -f 2>/dev/null

echo "Backup complete!"
echo "Location: $BACKUP_DIR"
EOF

# Step 2: Make executable
chmod +x ~/my_backup.sh

# Step 3: Run and test
~/my_backup.sh

# Step 4: Verify
ls -lh ~/storage/downloads/auto_backups/
```

### Exercise 3: Restore Simulation

```bash
# Task: Simulate a restore process

# Step 1: Create test directory
mkdir -p /tmp/restore_test

# Step 2: Extract backup to test
tar -xzvf ~/storage/downloads/my_backups/home_*.tar.gz -C /tmp/restore_test

# Step 3: Check what was extracted
ls -la /tmp/restore_test/home/

# Step 4: Verify important files
ls -la /tmp/restore_test/home/.bashrc
ls -la /tmp/restore_test/home/.ssh/

# Step 5: Clean up
rm -rf /tmp/restore_test
```

### Exercise 4: Schedule Automatic Backups

```bash
# Task: Setup automatic daily backup

# Step 1: Install cron
pkg install cronie

# Step 2: Start cron service
sv-enable crond
sv up crond

# Step 3: Add backup to crontab
crontab -e

# Add this line (backup at 2 AM daily):
# 0 2 * * * /data/data/com.termux/files/home/my_backup.sh >> /data/data/com.termux/files/home/backup.log 2>&1

# Step 4: Verify crontab
crontab -l

# Step 5: Check cron is running
sv status crond
```

### Exercise 5: Cloud Backup Setup

```bash
# Task: Setup cloud backup with rclone

# Step 1: Install rclone
pkg install rclone

# Step 2: Configure (follow interactive prompts)
rclone config
# Select cloud provider and authenticate

# Step 3: Test connection
rclone lsd <remote_name>:

# Step 4: Create backup upload script
cat > ~/cloud_backup.sh << 'EOF'
#!/bin/bash
BACKUP=~/storage/downloads/my_backups/home_*.tar.gz
REMOTE=your_remote:TermuxBackups/

rclone copy $REMOTE . -P
echo "Cloud backup complete!"
EOF

# Step 5: Make executable and test
chmod +x ~/cloud_backup.sh
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Permission denied" when creating backup

```bash
# Cause: No storage access

# Solution 1: Grant storage permission
termux-setup-storage

# Solution 2: Check if storage links exist
ls -la ~/storage/

# Solution 3: Create directory manually
mkdir -p ~/storage/downloads/termux_backups
```

### Problem 2: "No space left on device"

```bash
# Cause: Storage full

# Solution 1: Check space
df -h

# Solution 2: Clear Termux cache
pkg clean
rm -rf ~/.cache/*

# Solution 3: Clear npm cache
rm -rf ~/.npm/_cacache

# Solution 4: Remove old backups
ls -lt ~/storage/downloads/termux_backups/ | head -20
rm ~/storage/downloads/termux_backups/old_backup.tar.gz
```

### Problem 3: Backup file is too large

```bash
# Cause: Including unnecessary files

# Solution 1: Use exclusions
tar -czvf backup.tar.gz \
    --exclude="$HOME/.cache" \
    --exclude="$HOME/node_modules" \
    --exclude="$HOME/.npm" \
    --exclude="$HOME/storage" \
    --exclude="$HOME/__pycache__" \
    ~/

# Solution 2: Split large backup
tar -czvf - ~/ | split -b 500M - backup_part_

# Solution 3: Compress more aggressively
tar -cvf - ~/ | xz -9 > backup.tar.xz
```

### Problem 4: Restore fails with "permission denied"

```bash
# Cause: Files extracted with wrong permissions

# Solution 1: Check current permissions
ls -la ~/.ssh/

# Solution 2: Fix SSH key permissions
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub

# Solution 3: Fix script permissions
chmod +x ~/scripts/*.sh

# Solution 4: Fix all executable files
find ~/bin -type f -exec chmod +x {} \;
```

### Problem 5: Packages fail to restore

```bash
# Cause: Package list has issues or packages no longer exist

# Solution 1: Update first
pkg update

# Solution 2: Install packages one by one to find problematic one
while read pkg; do
    echo "Installing: $pkg"
    pkg install -y "$pkg" || echo "Failed: $pkg"
done < packages.txt

# Solution 3: Check if package exists
pkg search <package_name>

# Solution 4: Some packages may have been renamed
# Check available packages
pkg list-all | grep -i <keyword>
```

### Problem 6: Cron job not running

```bash
# Cause: Cron service not running or wrong path

# Solution 1: Check cron status
sv status crond

# Solution 2: Start cron
sv up crond

# Solution 3: Enable at boot
sv-enable crond

# Solution 4: Use absolute paths in crontab
# Wrong: 0 2 * * * ~/backup.sh
# Correct: 0 2 * * * /data/data/com.termux/files/home/backup.sh

# Solution 5: Check crontab format
crontab -l

# Solution 6: Test manually
/data/data/com.termux/files/home/backup.sh
```

### Problem 7: Backup corrupted

```bash
# Cause: Incomplete backup or transfer error

# Solution 1: Verify archive integrity
tar -tzvf backup.tar.gz | head

# Solution 2: Check checksum
sha256sum backup.tar.gz

# Solution 3: Try to recover partial archive
tar -xzvf backup.tar.gz --ignore-zeros

# Solution 4: Always generate checksum with backup
sha256sum backup.tar.gz > backup.tar.gz.sha256

# Solution 5: Verify before restore
sha256sum -c backup.tar.gz.sha256
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   💾 TERMUX BACKUP                 │
│   & RESTORE GUIDE                  │
│                                    │
│   ✓ Complete Backup Script         │
│   ✓ Cloud Backup Options           │
│   ✓ Migration Guide                │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Warning Style**
```
┌────────────────────────────────────┐
│  ⚠️ PHONE FORMAT?                  │
│     DATA LOST?                     │
│                                    │
│  💡 LEARN BACKUP NOW!              │
│                                    │
│  Chapter 60 | T3rmuxk1ng           │
│  Complete Backup Solution          │
└────────────────────────────────────┘
```

**Option C: Process Style**
```
┌────────────────────────────────────┐
│  📦 BACKUP → ☁️ CLOUD → 📱 RESTORE │
│                                    │
│  Complete Termux                   │
│  Backup & Restore Guide            │
│                                    │
│  Scripts Included!                 │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
💾 Termux Full Course - Chapter 60: Complete Backup & Restore Guide

🔥 In this video you'll learn:
• Backup kyun zaroori hai
• Kya kya backup karna hai
• Manual backup methods (tar, rsync)
• Automated backup scripts
• Cloud backup setup (Google Drive)
• Restore process step by step
• New phone migration guide

⏱️ Timestamps:
0:00 - Introduction
0:50 - Why Backup is Important
3:00 - What to Backup
6:00 - Manual Backup Methods
9:00 - Automated Backup Script
12:00 - Cloud Backup Options
14:00 - Restore Process
16:30 - New Phone Migration
18:00 - Backup Apps
19:30 - Best Practices
21:00 - Summary

📝 Commands from this video:
# Create backup
tar -czvf backup.tar.gz ~/

# Save packages
pkg list-installed > packages.txt

# Restore packages
xargs pkg install -y < packages.txt

📥 Backup Script Download:
[GitHub Link]

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxBackup #TermuxRestore #T3rmuxk1ng #TermuxCourse #DataBackup #TermuxHindi #LinuxOnAndroid

---
⚠️ Disclaimer: Always test your backups! A backup you haven't tested restoring is not a backup.
```

### Tags List

```
termux backup, termux restore, termux backup script, termux data backup,
termux full backup, termux migration, termux new phone, termux backup restore,
termux tar backup, termux rsync, termux cloud backup, termux google drive,
termux packages backup, termux home backup, termux scripts, termux course,
t3rmuxk1ng, termux tutorial hindi, termux full course, android backup,
linux backup, termux data recovery, termux save data
```

### Hashtags

```
#Termux #TermuxBackup #TermuxRestore #TermuxCourse #TermuxHindi 
#DataBackup #TermuxTutorial #LinuxOnAndroid #TermuxScripts 
#T3rmuxk1ng #TermuxMigration #CloudBackup #LearnTermux
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux Wiki - Backup | https://wiki.termux.com/wiki/Backup |
| Termux GitHub | https://github.com/termux |
| Rclone Docs | https://rclone.org/docs/ |

### Tools Reference

| Tool | Purpose | Install |
|------|---------|---------|
| tar | Archive creation | Built-in |
| rsync | Incremental sync | pkg install rsync |
| rclone | Cloud sync | pkg install rclone |
| gpg | Encryption | pkg install gnupg |
| openssl | Encryption | pkg install openssl |

### Backup Checklist

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BACKUP CHECKLIST                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  BEFORE BACKUP:                                                          │
│  □ Storage permission granted (termux-setup-storage)                    │
│  □ Enough disk space available                                          │
│  □ Backup directory exists                                               │
│                                                                          │
│  BACKUP INCLUDES:                                                        │
│  □ Home directory (~)                                                    │
│  □ Configuration files (.bashrc, etc.)                                  │
│  □ SSH keys (~/.ssh/)                                                   │
│  □ Package lists                                                         │
│  □ Custom scripts                                                        │
│  □ Projects                                                              │
│                                                                          │
│  AFTER BACKUP:                                                           │
│  □ Verify backup file exists                                             │
│  □ Check backup size is reasonable                                       │
│  □ Generate checksum                                                     │
│  □ Test restore (important!)                                             │
│  □ Upload to cloud (3-2-1 rule)                                         │
│                                                                          │
│  REGULAR MAINTENANCE:                                                    │
│  □ Weekly backups minimum                                                │
│  □ Monthly restore tests                                                 │
│  □ Cleanup old backups                                                   │
│  □ Update backup script                                                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 61, verify:

- [ ] Understand why backup is critical in Termux
- [ ] Know what files to backup
- [ ] Can create manual tar backup
- [ ] Have automated backup script saved
- [ ] Tested restore process
- [ ] Setup cloud backup (optional but recommended)
- [ ] Created backup schedule
- [ ] Documented custom setup

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 61: Useful Resources & Course Completion**

- Essential Termux resources
- Community links
- Documentation reference
- Learning paths
- What to do next
- Course summary

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
