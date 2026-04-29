# Chapter 57: Project 7 - Backup Automation System

> **Module:** 9 - Projects  
> **Chapter:** 57 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed backup system design |
| Project Features | Full, Incremental, Scheduled backups |
| Implementation | Python + Bash versions |
| Source Code | Complete, production-ready code |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common backup issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 57
Title: Backup Automation System | Complete Project | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon aur aaj hum ek bahut hi important project banayenge - 
Backup Automation System!

Dosto, data sabse valuable cheez hai aaj ke digital world mein. Ek single 
click mein aapki saari photos, documents, projects, scripts - sab kuch 
kachra ho sakta hai. Phone format, accidental delete, virus attack, ya 
storage corruption - koi bhi reason ho, data loss ka dard bahut hota hai.

Lekin agar aapke paas automated backup system ho - to tension zero!

Is project mein hum ek complete backup solution banayenge jo:
- Automatic backups lega
- Multiple backup types support karega
- Cloud pe upload karega
- Encryption provide karega
- Restore bhi karega

Ye project real-world production ready hai. To chaliye shuru karte hain!

Play button dabaiye, like karein, subscribe karein - aur shuru!

---

[SECTION 1: PROJECT OVERVIEW - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle samajhte hain ki ye project kya karega aur kyun zaroori hai.

Backup Automation System ek aisa tool hai jo aapki important files ka 
automatic backup le. Ye manual backup ki problem solve karta hai.

Manual backup mein kya problems hoti hain?

1. Bhool jana - "Aaj backup lena tha, yaad nahi raha"
2. Irregular - Kabhi weekly, kabhi monthly, kabhi kabhi nahi
3. Incomplete - Kuch files miss ho jaati hain
4. No verification - Backup sahi hai ya nahi, pata nahi
5. No rotation - Purane backups space le rahe hain

Automated system ye sab problems solve karta hai!

Hamare project mein ye features honge:

┌─────────────────────────────────────────────────────────────────────────┐
│                    BACKUP SYSTEM FEATURES                                │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Full Backup          │ Complete backup of all files                    │
│ Incremental Backup   │ Sirf changed files ka backup                    │
│ Scheduled Backup     │ Automatic timing pe backup                      │
│ Compression          │ Space bachane ke liye compress                  │
│ Encryption           │ Password protection for security                │
│ Cloud Upload         │ Google Drive, Dropbox support                   │
│ Verification         │ Backup integrity check                          │
│ Restore              │ Files wapas lana                                │
│ Rotation             │ Purane backups automatically delete             │
│ Notifications        │ Success/failure notifications                   │
└──────────────────────┴──────────────────────────────────────────────────┘

Ye project hum Python aur Bash dono mein implement karenge. Python version 
zyada features ke saath, Bash version lightweight ke liye.

Architecture samjhte hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│   Source Files ──► Backup Engine ──► Compress ──► Encrypt ──► Store    │
│        │               │                │           │          │        │
│        │               │                │           │          ▼        │
│        │               │                │           │    Local Backup   │
│        │               │                │           │          │        │
│        │               │                │           │          ▼        │
│        │               │                │           │    Cloud Upload   │
│        │               │                │           │          │        │
│        │               │                │           │          ▼        │
│        │               │                │           │   Notification    │
│        │               │                │           │                   │
│        ▼               ▼                ▼           ▼                   │
│   Config File ◄─── Log File ◄──── Verification ◄── Restore             │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 2: BACKUP STRATEGY DESIGN - 4:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab backup strategy design karte hain. Ye bahut important hai kyunki 
ek achhi strategy aapko data loss se bachati hai.

3-2-1 Backup Rule:
─────────────────

Industry standard rule ye hai:

• 3 Copies of Data - Original + 2 Backups
• 2 Different Media - Phone storage + External/Cloud
• 1 Offsite Location - Cloud backup

Is rule ko follow karke aap data loss se almost safe rahenge.

Backup Types:
─────────────

1. FULL BACKUP
   - Saari files ka complete backup
   - Space zyada lagta hai
   - Restore easy hai
   - Weekly ya monthly recommended

2. INCREMENTAL BACKUP
   - Sirf changed files ka backup
   - Space kam lagta hai
   - Fast backup
   - Daily recommended

3. DIFFERENTIAL BACKUP
   - Last full backup ke baad changed files
   - Full aur incremental ke beech ka

Hamara system Full aur Incremental dono support karega.

Backup Rotation:
────────────────

Purane backups ka management:

┌─────────────────────────────────────────────────────────────────────────┐
│                    BACKUP ROTATION SCHEME                                │
├─────────────────────────────────────────────────────────────────────────┤
│ Daily Backups    │ Keep last 7 days                                     │
│ Weekly Backups   │ Keep last 4 weeks                                    │
│ Monthly Backups  │ Keep last 6 months                                   │
│ Yearly Backups   │ Keep last 2 years                                    │
└─────────────────────────────────────────────────────────────────────────┘

Isse space bhi bachega aur purane data tak access bhi rahega.

Backup Schedule Example:
────────────────────────

• Daily 2 AM - Incremental backup
• Weekly Sunday 3 AM - Full backup
• Monthly 1st - Full backup + Cloud sync
• Quarterly - Archive backup

Termux mein cron job se ye automatic hoga!

---

[SECTION 3: PYTHON IMPLEMENTATION - 7:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Ab Python implementation start karte hain. Pehle requirements install karein:

    pkg install python python-pip -y
    pip install cryptography google-api-python-client dropbox

Main code structure samjhata hoon:

[FILE STRUCTURE]

backup_system/
├── backup.py          # Main backup script
├── config.json        # Configuration file
├── restore.py         # Restore functionality
├── scheduler.py       # Cron integration
├── cloud_upload.py    # Cloud providers
├── utils.py           # Helper functions
└── logs/              # Backup logs
    └── backup.log

[CONFIGURATION FILE - config.json]

Ye file backup settings store karegi:

{
    "source_dirs": [
        "/sdcard/Documents",
        "/sdcard/DCIM",
        "/sdcard/Download"
    ],
    "backup_dir": "/sdcard/Backup",
    "encryption": {
        "enabled": true,
        "password": "your_secure_password"
    },
    "compression": "gzip",
    "retention": {
        "daily": 7,
        "weekly": 4,
        "monthly": 6
    },
    "cloud": {
        "enabled": false,
        "provider": "dropbox",
        "token": ""
    },
    "notifications": true
}

[MAIN BACKUP SCRIPT]

Ab main code likhte hain. Code bahut bada hai, to main important 
parts explain karunga. Full code description mein milega.

Core backup function:

def create_backup(source_dirs, backup_dir, backup_type="full"):
    """
    Create backup of specified directories
    """
    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
    backup_name = f"backup_{backup_type}_{timestamp}"
    
    if backup_type == "full":
        # Full backup - copy all files
        for source in source_dirs:
            copy_directory(source, backup_dir)
    else:
        # Incremental - only changed files
        last_backup = get_last_backup_time()
        for source in source_dirs:
            copy_changed_files(source, backup_dir, last_backup)
    
    # Compress backup
    compressed = compress_backup(backup_dir, backup_name)
    
    # Encrypt if enabled
    if config['encryption']['enabled']:
        encrypted = encrypt_backup(compressed)
    
    return backup_name

Incremental backup ke liye hum file modification time check karte hain:

def get_changed_files(directory, since_time):
    """
    Get files modified after since_time
    """
    changed = []
    for root, dirs, files in os.walk(directory):
        for file in files:
            filepath = os.path.join(root, file)
            mtime = os.path.getmtime(filepath)
            if mtime > since_time:
                changed.append(filepath)
    return changed

Compression ke liye tarfile aur gzip use karte hain:

def compress_backup(source_dir, output_name):
    """
    Compress backup using gzip
    """
    import tarfile
    output_path = f"{output_name}.tar.gz"
    
    with tarfile.open(output_path, "w:gz") as tar:
        tar.add(source_dir, arcname=os.path.basename(source_dir))
    
    return output_path

Encryption ke liye cryptography library:

def encrypt_backup(filepath, password):
    """
    Encrypt backup with password
    """
    from cryptography.fernet import Fernet
    import base64
    import hashlib
    
    # Generate key from password
    key = base64.urlsafe_b64encode(
        hashlib.sha256(password.encode()).digest()
    )
    fernet = Fernet(key)
    
    with open(filepath, 'rb') as f:
        data = f.read()
    
    encrypted = fernet.encrypt(data)
    
    with open(filepath + '.enc', 'wb') as f:
        f.write(encrypted)
    
    # Remove unencrypted file
    os.remove(filepath)
    
    return filepath + '.enc'

[SCREEN: Code running demonstration]

Ab is code ko run karte hain:

    python backup.py --config config.json --type full

Output dikhega:
[*] Starting full backup...
[*] Scanning /sdcard/Documents...
[*] Found 156 files
[*] Scanning /sdcard/DCIM...
[*] Found 2,341 files
[*] Creating archive...
[*] Compressing... (saved 45% space)
[*] Encrypting...
[+] Backup created: backup_full_20241215_020000.tar.gz.enc
[*] Size: 1.2 GB
[*] Time: 3 minutes 24 seconds

Incremental backup:

    python backup.py --config config.json --type incremental

Output:
[*] Starting incremental backup...
[*] Last backup: 2024-12-14 02:00:00
[*] Finding changed files...
[*] Found 23 modified files
[*] Creating archive...
[+] Backup created: backup_inc_20241215_020000.tar.gz
[*] Size: 45 MB
[*] Time: 12 seconds

Dekha? Incremental backup kitna fast hai!

---

[SECTION 4: RESTORE FUNCTIONALITY - 14:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Backup lene se zyada important hai use wapas lana! Restore functionality 
bahut critical hai.

Restore script mein ye features honge:

1. List available backups
2. Select backup to restore
3. Choose restore location
4. Verify backup integrity
5. Decrypt if needed
6. Extract files
7. Verify restored files

Restore function:

def restore_backup(backup_file, restore_dir, password=None):
    """
    Restore files from backup
    """
    # Decrypt if encrypted
    if backup_file.endswith('.enc'):
        if not password:
            password = get_password()
        backup_file = decrypt_backup(backup_file, password)
    
    # Verify integrity
    if not verify_backup(backup_file):
        print("[!] Backup corrupted!")
        return False
    
    # Extract files
    with tarfile.open(backup_file, 'r:gz') as tar:
        tar.extractall(restore_dir)
    
    print(f"[+] Restored to {restore_dir}")
    return True

List backups function:

def list_backups(backup_dir):
    """
    List all available backups
    """
    backups = []
    for file in os.listdir(backup_dir):
        if file.startswith('backup_'):
            info = parse_backup_name(file)
            info['size'] = os.path.getsize(
                os.path.join(backup_dir, file)
            )
            backups.append(info)
    
    # Sort by date, newest first
    backups.sort(key=lambda x: x['date'], reverse=True)
    
    return backups

Restore command:

    python restore.py --list
    python restore.py --file backup_full_20241215.tar.gz.enc --to /sdcard/Restored

Output:
[*] Available Backups:
#   Name                          Type         Date         Size
1   backup_full_20241215.enc      Full    2024-12-15     1.2 GB
2   backup_inc_20241214.enc       Inc     2024-12-14     45 MB
3   backup_full_20241208.enc      Full    2024-12-08     1.1 GB

Select backup number: 1
Enter password: ****
[*] Decrypting...
[*] Verifying integrity...
[+] Integrity OK!
[*] Extracting to /sdcard/Restored...
[+] Restored 2,497 files successfully!

---

[SECTION 5: CLOUD INTEGRATION - 17:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Ab cloud integration add karte hain. Dropbox aur Google Drive support karenge.

DROPBOX INTEGRATION:
────────────────────

Pehle Dropbox app banani hai:
1. Go to dropbox.com/developers
2. Create new app
3. Generate access token

Code:

def upload_to_dropbox(filepath, token):
    """
    Upload backup to Dropbox
    """
    import dropbox
    
    dbx = dropbox.Dropbox(token)
    
    filename = os.path.basename(filepath)
    remote_path = f'/Backups/{filename}'
    
    with open(filepath, 'rb') as f:
        file_size = os.path.getsize(filepath)
        
        # Large files - use chunked upload
        if file_size > 150 * 1024 * 1024:  # 150MB
            upload_session_start_result = dbx.files_upload_session_start(
                f.read(150 * 1024 * 1024)
            )
            cursor = dropbox.files.UploadSessionCursor(
                session_id=upload_session_start_result.session_id,
                offset=0
            )
            
            while f.tell() < file_size:
                chunk = f.read(150 * 1024 * 1024)
                dbx.files_upload_session_append_v2(
                    chunk,
                    cursor
                )
                cursor.offset = f.tell()
            
            dbx.files_upload_session_finish(
                f.read(),
                cursor,
                dropbox.files.CommitInfo(path=remote_path)
            )
        else:
            dbx.files_upload(f.read(), remote_path)
    
    print(f"[+] Uploaded to Dropbox: {remote_path}")

GOOGLE DRIVE INTEGRATION:
─────────────────────────

Google Drive ke liye zyada setup chahiye:

1. Go to console.cloud.google.com
2. Create project
3. Enable Google Drive API
4. Create OAuth credentials
5. Download credentials.json

Code:

def upload_to_gdrive(filepath, credentials_file):
    """
    Upload backup to Google Drive
    """
    from google.oauth2.credentials import Credentials
    from google_auth_oauthlib.flow import InstalledAppFlow
    from googleapiclient.discovery import build
    from googleapiclient.http import MediaFileUpload
    
    # Authenticate
    flow = InstalledAppFlow.from_client_secrets_file(
        credentials_file,
        ['https://www.googleapis.com/auth/drive.file']
    )
    creds = flow.run_local_server(port=0)
    
    service = build('drive', 'v3', credentials=creds)
    
    # Upload file
    file_metadata = {
        'name': os.path.basename(filepath),
        'parents': ['appDataFolder']  # Hidden app folder
    }
    
    media = MediaFileUpload(
        filepath,
        resumable=True
    )
    
    file = service.files().create(
        body=file_metadata,
        media_body=media,
        fields='id'
    ).execute()
    
    print(f"[+] Uploaded to Google Drive, ID: {file.get('id')}")

Cloud upload command:

    python backup.py --upload dropbox
    python backup.py --upload gdrive

---

[SECTION 6: SCHEDULING & NOTIFICATIONS - 20:00 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Ab automation ka asli magic - Scheduling!

CRON JOB SETUP:
───────────────

Termux mein crond daemon chalao:

    pkg install cronie -y
    crond

Cron job add karo:

    crontab -e

Daily incremental backup (2 AM):

    0 2 * * * /data/data/com.termux/files/home/backup_system/backup.sh incremental

Weekly full backup (Sunday 3 AM):

    0 3 * * 0 /data/data/com.termux/files/home/backup_system/backup.sh full

Backup rotation (Monday midnight):

    0 0 * * 1 /data/data/com.termux/files/home/backup_system/rotate.sh

Termux:Boot se auto-start:
─────────────────────────

Phone restart hone pe cron auto-start ke liye:

    mkdir -p ~/.termux/boot
    cat > ~/.termux/boot/cron.sh << 'EOF'
    #!/data/data/com.termux/files/usr/bin/bash
    crond
    EOF
    chmod +x ~/.termux/boot/cron.sh

Termux:Boot app install karna padega F-Droid se.

NOTIFICATIONS:
──────────────

Backup completion notification:

def send_notification(title, message):
    """
    Send Termux notification
    """
    import subprocess
    
    cmd = [
        'termux-notification',
        '--title', title,
        '--content', message,
        '--sound'
    ]
    
    subprocess.run(cmd)

Success notification:

    send_notification(
        "✅ Backup Complete",
        f"Created: {backup_name}\nSize: {size}"
    )

Failure notification:

    send_notification(
        "❌ Backup Failed",
        f"Error: {error_message}"
    )

---

[SECTION 7: BASH IMPLEMENTATION - 23:00 to 26:00]
─────────────────────────────────────────────────────────────────────────────

Ab Bash version banate hain - lightweight aur simple!

Bash backup script:

[backup.sh]

#!/data/data/com.termux/files/usr/bin/bash

# Backup Automation System - Bash Version
# Author: T3rmuxk1ng

# Configuration
BACKUP_DIR="/sdcard/Backup"
SOURCE_DIRS=("/sdcard/Documents" "/sdcard/DCIM")
LOG_FILE="$HOME/backup_system/logs/backup.log"
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_TYPE=${1:-"full"}

# Create backup directory
mkdir -p "$BACKUP_DIR"
mkdir -p "$(dirname $LOG_FILE)"

log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOG_FILE"
}

# Full backup function
full_backup() {
    log "Starting full backup..."
    
    BACKUP_NAME="backup_full_$DATE.tar.gz"
    
    # Create tar archive
    tar -czf "$BACKUP_DIR/$BACKUP_NAME" "${SOURCE_DIRS[@]}" 2>/dev/null
    
    if [ $? -eq 0 ]; then
        SIZE=$(du -h "$BACKUP_DIR/$BACKUP_NAME" | cut -f1)
        log "Backup created: $BACKUP_NAME (Size: $SIZE)"
        
        # Send notification
        termux-notification --title "✅ Backup Complete" \
            --content "Full backup created: $BACKUP_NAME" --sound
        
        return 0
    else
        log "ERROR: Backup failed!"
        termux-notification --title "❌ Backup Failed" \
            --content "Check log: $LOG_FILE" --sound
        return 1
    fi
}

# Incremental backup function
incremental_backup() {
    log "Starting incremental backup..."
    
    BACKUP_NAME="backup_inc_$DATE.tar.gz"
    SNAPSHOT_FILE="$BACKUP_DIR/.snapshot"
    
    # Find changed files since last backup
    if [ -f "$SNAPSHOT_FILE" ]; then
        LAST_BACKUP=$(cat "$SNAPSHOT_FILE")
        CHANGED_FILES=$(find "${SOURCE_DIRS[@]}" -newer "$LAST_BACKUP" -type f 2>/dev/null)
    else
        CHANGED_FILES=$(find "${SOURCE_DIRS[@]}" -type f 2>/dev/null)
    fi
    
    if [ -z "$CHANGED_FILES" ]; then
        log "No files changed since last backup"
        return 0
    fi
    
    # Create archive of changed files
    echo "$CHANGED_FILES" | tar -czf "$BACKUP_DIR/$BACKUP_NAME" -T - 2>/dev/null
    
    # Update snapshot
    touch "$BACKUP_DIR/.snapshot_new"
    mv "$BACKUP_DIR/.snapshot_new" "$SNAPSHOT_FILE"
    
    SIZE=$(du -h "$BACKUP_DIR/$BACKUP_NAME" | cut -f1)
    log "Incremental backup created: $BACKUP_NAME (Size: $SIZE)"
    
    termux-notification --title "✅ Backup Complete" \
        --content "Incremental backup: $BACKUP_NAME" --sound
}

# Backup rotation
rotate_backups() {
    log "Rotating old backups..."
    
    # Keep last 7 daily backups
    DAILY_COUNT=$(ls "$BACKUP_DIR"/backup_inc_*.tar.gz 2>/dev/null | wc -l)
    if [ "$DAILY_COUNT" -gt 7 ]; then
        ls -t "$BACKUP_DIR"/backup_inc_*.tar.gz | tail -n +8 | xargs rm -f
        log "Removed old incremental backups"
    fi
    
    # Keep last 4 weekly backups
    WEEKLY_COUNT=$(ls "$BACKUP_DIR"/backup_full_*.tar.gz 2>/dev/null | wc -l)
    if [ "$WEEKLY_COUNT" -gt 4 ]; then
        ls -t "$BACKUP_DIR"/backup_full_*.tar.gz | tail -n +5 | xargs rm -f
        log "Removed old full backups"
    fi
}

# Main execution
case "$BACKUP_TYPE" in
    full)
        full_backup
        ;;
    incremental|inc)
        incremental_backup
        ;;
    rotate)
        rotate_backups
        ;;
    *)
        echo "Usage: $0 {full|incremental|rotate}"
        exit 1
        ;;
esac

Bash version simple hai lekin powerful hai!

Usage:

    chmod +x backup.sh
    ./backup.sh full        # Full backup
    ./backup.sh incremental # Incremental backup
    ./backup.sh rotate      # Rotate old backups

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 26:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 57 complete! Let's summarize:

✅ Project Overview - Backup automation ka importance
✅ Strategy Design - 3-2-1 rule, backup types
✅ Python Implementation - Full featured backup system
✅ Restore Functionality - Files wapas lana
✅ Cloud Integration - Dropbox, Google Drive
✅ Scheduling - Cron jobs automation
✅ Notifications - Termux notifications
✅ Bash Version - Lightweight alternative

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 57 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ python backup.py --type full        │ Create full backup                │
│ python backup.py --type incremental │ Create incremental backup         │
│ python restore.py --list            │ List available backups            │
│ python restore.py --file <name>     │ Restore specific backup           │
│ crontab -e                          │ Edit cron jobs                    │
│ crond                               │ Start cron daemon                 │
│ ./backup.sh full                    │ Bash full backup                  │
│ ./backup.sh incremental             │ Bash incremental backup           │
│ termux-notification                 │ Send notification                 │
└─────────────────────────────────────────────────────────────────────────┘

Files created:

backup_system/
├── backup.py          # Main Python script
├── restore.py         # Restore functionality
├── config.json        # Configuration
├── backup.sh          # Bash version
├── rotate.sh          # Backup rotation
└── logs/
    └── backup.log     # Backup logs

Next Chapter 58 mein hum seekhenge:
- Common Termux errors
- Troubleshooting techniques
- Performance optimization
- Resource management

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 58!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Follow the 3-2-1 rule: 3 copies, 2 media types, 1 offsite!

> 💡 **Pro Tip #2:** Always encrypt sensitive backups - especially if uploading to cloud!

> 💡 **Pro Tip #3:** Use incremental backups daily, full backups weekly!

> 💡 **Pro Tip #4:** Test your restore process regularly - a backup you can't restore is useless!

> 💡 **Pro Tip #5:** Set up cron jobs for automated scheduling - don't rely on remembering!

> 💡 **Pro Tip #6:** Use backup rotation to save space - delete old backups automatically!

> 💡 **Pro Tip #7:** Always verify backup integrity after creation!

> 💡 **Pro Tip #8:** Document your backup process - you'll thank yourself later!

> 💡 **Pro Tip #9:** Combine with Ch56 File Organizer for complete data management!

> 💡 **Pro Tip #10:** Keep at least one backup disconnected from your device (air-gapped)!

---

## 🔥 REAL WORLD USE CASES

### Real World Applications of Backup Automation

**1. Personal Data Protection**
- Photos and memories
- Documents and important files
- Project code

**2. System Recovery**
- Full system restore after crash
- Migration to new device
- Disaster recovery

**3. Version Control**
- Keep history of file changes
- Rollback to previous versions
- Point-in-time recovery

**4. Business Continuity**
- Critical data backup
- Compliance requirements
- Audit trails

**5. Development Workflow**
- Code backup
- Database dumps
- Configuration backup

**6. Multi-Device Sync**
- Sync files between devices
- Cloud backup automation
- Cross-platform recovery

---

## ⚡ QUICK REFERENCE CARD

### Backup Automation Quick Reference

| Command | Description |
|---------|-------------|
| `python backup.py --type full` | Create full backup |
| `python backup.py --type incremental` | Create incremental backup |
| `python restore.py --list` | List available backups |
| `python restore.py --file NAME` | Restore specific backup |
| `./backup.sh full` | Bash full backup |
| `./backup.sh incremental` | Bash incremental backup |
| `crontab -e` | Edit cron schedule |
| `crond` | Start cron daemon |

### Backup Types Comparison

| Type | Description | Speed | Size | Use Case |
|------|-------------|-------|------|----------|
| Full | Complete copy | Slow | Large | Weekly/Monthly |
| Incremental | Changed since last | Fast | Small | Daily |
| Differential | Changed since full | Medium | Medium | Alternative |

### Retention Policy Guide

| Backup Type | Keep | Storage Impact |
|-------------|------|----------------|
| Daily | 7 days | Low |
| Weekly | 4 weeks | Medium |
| Monthly | 6 months | Medium |
| Yearly | 2 years | Low |

---

## 🏆 BONUS CONTENT

### Bonus: Advanced Backup Features

**Feature 1: Differential Backup**
```python
def differential_backup(source, last_full):
    """Backup all changes since last full backup"""
    # Different from incremental (changes since ANY last backup)
    # Larger size but easier restore
```

**Feature 2: Backup Verification**
```python
def verify_backup(backup_file):
    """Verify backup integrity"""
    # Calculate checksum
    # Compare with stored checksum
    # Test extract sample files
```

**Feature 3: Compression Levels**
```python
COMPRESSION_LEVELS = {
    'fast': 1,      # Quick but larger
    'balanced': 6,  # Default
    'maximum': 9    # Smallest but slowest
}
```

**Feature 4: Bandwidth Throttling**
```python
def upload_with_limit(file, max_kbps):
    """Limit upload speed for cloud backup"""
    # Useful for slow connections
    # Prevent bandwidth saturation
```

**Feature 5: Backup Notifications**
```python
def send_backup_notification(status, details):
    """Send notification via multiple channels"""
    # Termux notification
    # Email (optional)
    # Telegram bot (optional)
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **Backup Strategy Design** - 3-2-1 rule, backup types
- ✅ **Full Backup Creation** - Complete data backup
- ✅ **Incremental Backup** - Changed files only
- ✅ **Compression** - tarfile, gzip for space saving
- ✅ **Encryption** - Fernet for password protection
- ✅ **Cloud Integration** - Dropbox, Google Drive
- ✅ **Restore Functionality** - Recovering files
- ✅ **Cron Scheduling** - Automated backups

### Key Takeaways

1. **Automate everything** - Manual backups are forgotten
2. **Test restore process** - Backups are useless if you can't restore
3. **Encrypt sensitive data** - Especially for cloud uploads
4. **Rotate old backups** - Save storage space
5. **Verify integrity** - Corrupted backups are worthless

---

## 🚀 PROJECT EXTENSIONS

### 5+ Ideas to Extend This Project

**Extension 1: Web Dashboard** ⭐⭐⭐⭐
- Visual backup status
- Storage usage graphs
- **Steps:** Flask backend, HTML frontend

**Extension 2: Multi-Cloud Support** ⭐⭐⭐⭐
- Backup to multiple providers
- Redundancy for critical data
- **Steps:** Add S3, OneDrive, Mega support

**Extension 3: Backup Browser** ⭐⭐⭐
- Browse backup contents without restore
- Search within backups
- **Steps:** Create backup index, web interface

**Extension 4: Automated Testing** ⭐⭐⭐⭐
- Automatic restore tests
- Integrity verification schedule
- **Steps:** Create test harness, schedule tests

**Extension 5: Bandwidth Monitor** ⭐⭐⭐
- Track upload bandwidth
- Optimize upload schedule
- **Steps:** Add monitoring, adaptive scheduling

**Extension 6: Backup History Analytics** ⭐⭐⭐
- Track backup sizes over time
- Predict storage needs
- **Steps:** Create analytics module, charts

---

## 🔧 CODE WALKTHROUGH

### Backup System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    BACKUP AUTOMATION ARCHITECTURE                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   SOURCE DATA                  BACKUP ENGINE                   OUTPUT│
│   ───────────                  ─────────────                   ──────│
│                                                                      │
│   ┌─────────────┐            ┌─────────────┐            ┌──────────┐│
│   │ Documents/  │            │             │            │ Compressed││
│   │ DCIM/       │ ─────────► │  Scanner    │ ────────► │ Archive   ││
│   │ Download/   │            │             │            │ .tar.gz   ││
│   └─────────────┘            └─────────────┘            └──────────┘│
│                                     │                      │        │
│                                     │                      ▼        │
│                              ┌─────────────┐            ┌──────────┐│
│                              │ Compression │            │ Encrypted││
│                              │ (gzip)      │ ────────► │ Archive  ││
│                              └─────────────┘            │ .tar.gz  ││
│                                     │                   │ .enc     ││
│                                     │                   └──────────┘│
│                              ┌─────────────┐                  │      │
│                              │ Encryption  │                  │      │
│                              │ (Fernet)    │                  │      │
│                              └─────────────┘                  │      │
│                                     │                         │      │
│   ┌─────────────┐            ┌─────────────┐            ┌──────────┐│
│   │ Config      │            │ Scheduler   │            │ Cloud    ││
│   │ (JSON)      │ ─────────► │ (Cron)      │ ────────► │ Upload   ││
│   └─────────────┘            └─────────────┘            └──────────┘│
│                                                              │      │
│                                                              ▼      │
│   ┌─────────────┐            ┌─────────────┐            ┌──────────┐│
│   │ Rotation    │            │ Verify      │            │ Local    ││
│   │ Manager     │ ◄───────── │ Integrity   │ ◄───────── │ Storage  ││
│   └─────────────┘            └─────────────┘            └──────────┘│
│                                                              │      │
│                                                              ▼      │
│                                                        ┌──────────┐│
│                                                        │Notification│
│                                                        │ (Termux)  ││
│                                                        └──────────┘│
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 📦 DEPLOYMENT GUIDE

### How to Deploy and Share This Project

**1. Create Project Structure**
```bash
mkdir -p ~/backup_system/{logs,cache,temp}
cd ~/backup_system
```

**2. Install Dependencies**
```bash
pkg install python cronie -y
pip install cryptography
```

**3. Create Config File**
```bash
cp config.json.example config.json
nano config.json  # Edit your settings
```

**4. Set Up Cron**
```bash
crond
crontab -e
```

Add cron jobs:
```
# Daily incremental at 2 AM
0 2 * * * ~/backup_system/backup.sh incremental

# Weekly full backup Sunday 3 AM
0 3 * * 0 ~/backup_system/backup.sh full

# Monthly rotation
0 4 1 * * ~/backup_system/rotate.sh
```

**5. Enable Boot Start**
```bash
mkdir -p ~/.termux/boot
echo '#!/bin/bash
crond' > ~/.termux/boot/cron.sh
chmod +x ~/.termux/boot/cron.sh
```

---

## 🔗 RELATED CHAPTERS

### Cross-Reference to Related Chapters

| Chapter | Topic | Connection |
|---------|-------|------------|
| **Ch51** | Password Generator | Secure backup passwords |
| **Ch56** | File Organizer | Organize before backup |
| **Ch54** | YouTube Downloader | Backup downloads |
| **Ch50** | Termux API | Notifications |
| **Ch49** | Bash Scripting | Bash version |

### Next Steps
- ➡️ **Ch58: Troubleshooting** - Common errors
- ➡️ **Ch59: Performance Optimization** - Speed up backups

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your Backup Knowledge!

**Question 1:** What is the 3-2-1 backup rule?
- a) 3 backups, 2 locations, 1 day
- b) 3 copies, 2 media types, 1 offsite ✓
- c) 3 days, 2 weeks, 1 month
- d) 3 computers, 2 drives, 1 cloud

**Question 2:** Which backup type is fastest to create?
- a) Full backup
- b) Incremental backup ✓
- c) Differential backup
- d) Mirror backup

**Question 3:** What does cron do?
- a) Compresses files
- b) Schedules tasks ✓
- c) Encrypts data
- d) Uploads to cloud

**Question 4:** Which Python module encrypts backups?
- a) crypto
- b) cryptography ✓
- c) pycryptodome
- d) encrypt

**Question 5:** What compression format does our backup use?
- a) .zip
- b) .rar
- c) .tar.gz ✓
- d) .7z

**Question 6:** What command starts the cron daemon?
- a) cron start
- b) crond ✓
- c) service cron start
- d) cron -d

**Question 7:** How often should you test restore?
- a) Never
- b) Once a year
- c) Regularly ✓
- d) Only when needed

**Question 8:** What is backup rotation?
- a) Moving backups around
- b) Deleting old backups to save space ✓
- c) Rotating encryption keys
- d) Spinning hard drives

**Question 9:** Which command edits cron jobs?
- a) cron -e
- b) crontab -e ✓
- c) edit-cron
- d) nano /etc/cron

**Question 10:** What verifies backup integrity?
- a) Checking file size
- b) Comparing checksums ✓
- c) Opening the file
- d) Checking date

**Question 11:** What cloud services can be integrated?
- a) Only Dropbox
- b) Dropbox and Google Drive ✓
- c) Only Google Drive
- d) None

**Question 12:** What is the recommended daily backup type?
- a) Full
- b) Incremental ✓
- c) Mirror
- d) Clone

---

### Extend the Project Challenges

**Challenge 1:** Add backup encryption key rotation
```python
def rotate_encryption_key(old_key, new_key):
    # Re-encrypt all backups with new key
    # Maintain backup accessibility
```

**Challenge 2:** Implement parallel upload
```python
def parallel_upload(files, threads=4):
    # Upload multiple files simultaneously
    # Track progress of each
```

**Challenge 3:** Add backup deduplication
```python
def deduplicate_backup(source):
    # Find duplicate files
    # Store only unique data
    # Create hard links for duplicates
```

### Bug Fixing Exercises

**Bug 1:** Backup fails silently
```python
try:
    create_backup()
except:
    pass  # Silent failure!
```
*Fix: Log errors, send notification on failure*

**Bug 2:** Cron job doesn't run
```bash
# Missing shebang!
./backup.sh
```
*Fix: Add #!/bin/bash at top, chmod +x*

**Bug 3:** Incremental backup too large
```python
# Not checking last backup time correctly
last_backup = get_last_backup()  # Returns None sometimes!
```
*Fix: Add None check, default to last full backup time*

---

## 💻 FULL SOURCE CODE

### 1. Project Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        BACKUP AUTOMATION ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │
│   │ Source      │    │ Backup      │    │ Compression │    │ Encryption  │ │
│   │ Directories │───►│ Engine      │───►│ Module      │───►│ Module      │ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │
│         │                  │                    │                  │        │
│         │                  │                    │                  │        │
│         ▼                  ▼                    ▼                  ▼        │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │
│   │ Config      │    │ Verification│    │ Local       │    │ Cloud       │ │
│   │ Manager     │    │ Module      │    │ Storage     │    │ Upload      │ │
│   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │
│         │                  │                    │                  │        │
│         └──────────────────┼────────────────────┼──────────────────┘        │
│                            │                    │                           │
│                            ▼                    ▼                           │
│                     ┌─────────────┐      ┌─────────────┐                    │
│                     │ Scheduler   │      │ Notification│                    │
│                     │ (Cron)      │      │ System      │                    │
│                     └─────────────┘      └─────────────┘                    │
│                            │                    │                           │
│                            └────────┬───────────┘                           │
│                                     ▼                                       │
│                              ┌─────────────┐                                │
│                              │ Restore     │                                │
│                              │ Module      │                                │
│                              └─────────────┘                                │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 2. Backup Types Explained

| Type | Description | Space | Speed | Use Case |
|------|-------------|-------|-------|----------|
| Full | Complete copy of all files | High | Slow | Weekly/Monthly |
| Incremental | Only changed files since last backup | Low | Fast | Daily |
| Differential | Changed files since last FULL backup | Medium | Medium | Alternative to incremental |

### 3. Backup Rotation Strategy

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        GRANDFATHER-FATHER-SON ROTATION                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   Daily (Son)          Weekly (Father)         Monthly (Grandfather)         │
│   ────────────         ──────────────          ─────────────────────         │
│   Keep: 7 days         Keep: 4 weeks           Keep: 6 months                │
│   Type: Incremental    Type: Full              Type: Full                    │
│                                                                              │
│   Mon ◄── Day 1        Week 1 ◄── Days 1-7    Jan ◄── Month 1               │
│   Tue ◄── Day 2        Week 2 ◄── Days 8-14   Feb ◄── Month 2               │
│   Wed ◄── Day 3        Week 3 ◄── Days 15-21  Mar ◄── Month 3               │
│   Thu ◄── Day 4        Week 4 ◄── Days 22-28  ...                           │
│   Fri ◄── Day 5                                                          │
│   Sat ◄── Day 6                                                          │
│   Sun ◄── Day 7 (Full backup)                                             │
│                                                                              │
│   After 7 days: Oldest daily deleted                                        │
│   After 4 weeks: Oldest weekly deleted                                      │
│   After 6 months: Oldest monthly deleted                                    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 4. File Structure

```
backup_system/
├── backup.py              # Main backup script
├── restore.py             # Restore functionality
├── config.json            # Configuration file
├── scheduler.py           # Cron job manager
├── cloud_upload.py        # Cloud providers
├── utils.py               # Helper functions
├── backup.sh              # Bash version (lightweight)
├── rotate.sh              # Backup rotation script
├── verify.sh              # Backup verification
├── logs/
│   ├── backup.log         # Main log file
│   ├── error.log          # Error log
│   └── history.log        # Backup history
├── cache/
│   ├── .snapshot          # Last backup timestamp
│   └── file_hashes.json   # File hash cache
└── temp/                  # Temporary files
```

---

## 💻 FULL SOURCE CODE

### Python Implementation

#### config.json - Configuration File

```json
{
    "source_dirs": [
        "/sdcard/Documents",
        "/sdcard/DCIM",
        "/sdcard/Download",
        "/sdcard/Scripts"
    ],
    "backup_dir": "/sdcard/Backup",
    "temp_dir": "/sdcard/Backup/temp",
    
    "backup_types": {
        "full": {
            "extension": ".tar.gz",
            "prefix": "backup_full"
        },
        "incremental": {
            "extension": ".tar.gz",
            "prefix": "backup_inc"
        }
    },
    
    "compression": {
        "enabled": true,
        "method": "gzip",
        "level": 6
    },
    
    "encryption": {
        "enabled": true,
        "method": "fernet",
        "key_file": "~/.backup_key"
    },
    
    "retention": {
        "daily": 7,
        "weekly": 4,
        "monthly": 6,
        "yearly": 2
    },
    
    "cloud": {
        "enabled": false,
        "provider": "dropbox",
        "dropbox_token": "",
        "gdrive_credentials": "",
        "upload_after_backup": true
    },
    
    "notifications": {
        "enabled": true,
        "on_success": true,
        "on_failure": true,
        "vibrate": true,
        "sound": true
    },
    
    "exclude_patterns": [
        "*.tmp",
        "*.cache",
        "*.log",
        "__pycache__",
        ".git",
        "node_modules",
        "*.pyc"
    ],
    
    "schedule": {
        "daily_incremental": "02:00",
        "weekly_full": "Sunday 03:00",
        "monthly_archive": "1st 04:00"
    }
}
```

#### backup.py - Main Backup Script

```python
#!/usr/bin/env python3
"""
Backup Automation System - Python Implementation
Author: T3rmuxk1ng
Version: 1.0.0

Features:
- Full backup
- Incremental backup
- Compression (gzip)
- Encryption (Fernet)
- Cloud upload (Dropbox, Google Drive)
- Backup rotation
- Notifications
- Verification
"""

import os
import sys
import json
import tarfile
import hashlib
import argparse
import subprocess
from datetime import datetime, timedelta
from pathlib import Path
from typing import List, Dict, Optional, Tuple
import logging
import shutil

# Setup logging
logging.basicConfig(
    level=logging.INFO,
    format='[%(asctime)s] %(message)s',
    datefmt='%Y-%m-%d %H:%M:%S'
)
logger = logging.getLogger(__name__)


class BackupConfig:
    """Configuration manager for backup system"""
    
    def __init__(self, config_path: str = "config.json"):
        self.config_path = config_path
        self.config = self._load_config()
        
    def _load_config(self) -> Dict:
        """Load configuration from JSON file"""
        default_config = {
            "source_dirs": ["/sdcard/Documents"],
            "backup_dir": "/sdcard/Backup",
            "temp_dir": "/sdcard/Backup/temp",
            "compression": {"enabled": True, "method": "gzip", "level": 6},
            "encryption": {"enabled": False, "key_file": "~/.backup_key"},
            "retention": {"daily": 7, "weekly": 4, "monthly": 6},
            "cloud": {"enabled": False, "provider": "dropbox"},
            "notifications": {"enabled": True, "on_success": True, "on_failure": True},
            "exclude_patterns": ["*.tmp", "*.cache", ".git", "node_modules"]
        }
        
        if os.path.exists(self.config_path):
            try:
                with open(self.config_path, 'r') as f:
                    loaded = json.load(f)
                    default_config.update(loaded)
            except Exception as e:
                logger.warning(f"Error loading config: {e}. Using defaults.")
        
        return default_config
    
    def get(self, key: str, default=None):
        """Get configuration value"""
        keys = key.split('.')
        value = self.config
        for k in keys:
            if isinstance(value, dict):
                value = value.get(k, default)
            else:
                return default
        return value


class BackupEngine:
    """Main backup engine"""
    
    def __init__(self, config: BackupConfig):
        self.config = config
        self.backup_dir = Path(config.get('backup_dir'))
        self.temp_dir = Path(config.get('temp_dir'))
        self.log_dir = self.backup_dir / 'logs'
        
        # Create directories
        self.backup_dir.mkdir(parents=True, exist_ok=True)
        self.temp_dir.mkdir(parents=True, exist_ok=True)
        self.log_dir.mkdir(parents=True, exist_ok=True)
        
        # Setup file logging
        log_file = self.log_dir / 'backup.log'
        file_handler = logging.FileHandler(log_file)
        file_handler.setFormatter(logging.Formatter('[%(asctime)s] %(levelname)s: %(message)s'))
        logger.addHandler(file_handler)
    
    def get_excluded_files(self, source_dir: str) -> set:
        """Get set of files to exclude based on patterns"""
        excluded = set()
        patterns = self.config.get('exclude_patterns', [])
        source_path = Path(source_dir)
        
        for pattern in patterns:
            for matched in source_path.rglob(pattern):
                if matched.is_file():
                    excluded.add(str(matched))
                elif matched.is_dir():
                    for f in matched.rglob('*'):
                        excluded.add(str(f))
        
        return excluded
    
    def get_file_hash(self, filepath: str) -> str:
        """Calculate MD5 hash of file"""
        hash_md5 = hashlib.md5()
        with open(filepath, 'rb') as f:
            for chunk in iter(lambda: f.read(4096), b''):
                hash_md5.update(chunk)
        return hash_md5.hexdigest()
    
    def get_changed_files(self, source_dir: str, since_time: datetime) -> List[str]:
        """Get files modified since specified time"""
        changed = []
        excluded = self.get_excluded_files(source_dir)
        source_path = Path(source_dir)
        
        for filepath in source_path.rglob('*'):
            if filepath.is_file():
                if str(filepath) in excluded:
                    continue
                try:
                    mtime = datetime.fromtimestamp(filepath.stat().st_mtime)
                    if mtime > since_time:
                        changed.append(str(filepath))
                except Exception as e:
                    logger.warning(f"Error checking {filepath}: {e}")
        
        return changed
    
    def get_last_backup_time(self) -> datetime:
        """Get timestamp of last successful backup"""
        snapshot_file = self.backup_dir / '.last_backup'
        if snapshot_file.exists():
            with open(snapshot_file, 'r') as f:
                time_str = f.read().strip()
                try:
                    return datetime.strptime(time_str, '%Y-%m-%d %H:%M:%S')
                except:
                    pass
        return datetime.now() - timedelta(days=365)  # Default: 1 year ago
    
    def create_backup(self, backup_type: str = 'full') -> Tuple[str, int]:
        """Create backup of specified type"""
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        backup_name = f"backup_{backup_type}_{timestamp}"
        temp_backup_dir = self.temp_dir / backup_name
        
        logger.info(f"Starting {backup_type} backup...")
        
        # Get source directories
        source_dirs = self.config.get('source_dirs', [])
        if not source_dirs:
            raise ValueError("No source directories configured!")
        
        # Collect files to backup
        files_to_backup = []
        
        if backup_type == 'incremental':
            last_backup = self.get_last_backup_time()
            logger.info(f"Last backup: {last_backup}")
            
            for source_dir in source_dirs:
                if os.path.exists(source_dir):
                    changed = self.get_changed_files(source_dir, last_backup)
                    files_to_backup.extend(changed)
                    logger.info(f"Found {len(changed)} changed files in {source_dir}")
        else:
            for source_dir in source_dirs:
                if os.path.exists(source_dir):
                    excluded = self.get_excluded_files(source_dir)
                    for filepath in Path(source_dir).rglob('*'):
                        if filepath.is_file() and str(filepath) not in excluded:
                            files_to_backup.append(str(filepath))
                    logger.info(f"Found {len(files_to_backup)} files in {source_dir}")
        
        if not files_to_backup:
            logger.info("No files to backup!")
            return None, 0
        
        # Create tar archive
        archive_path = self.backup_dir / f"{backup_name}.tar"
        logger.info(f"Creating archive: {archive_path}")
        
        with tarfile.open(archive_path, 'w') as tar:
            for filepath in files_to_backup:
                try:
                    arcname = os.path.basename(filepath)
                    tar.add(filepath, arcname=arcname)
                except Exception as e:
                    logger.warning(f"Could not add {filepath}: {e}")
        
        # Compress
        compressed_path = self._compress_archive(archive_path)
        archive_size = os.path.getsize(compressed_path)
        
        # Encrypt if enabled
        final_path = compressed_path
        if self.config.get('encryption.enabled'):
            final_path = self._encrypt_backup(compressed_path)
        
        # Update last backup time
        snapshot_file = self.backup_dir / '.last_backup'
        with open(snapshot_file, 'w') as f:
            f.write(datetime.now().strftime('%Y-%m-%d %H:%M:%S'))
        
        # Save file manifest
        self._save_manifest(backup_name, files_to_backup)
        
        logger.info(f"Backup created: {final_path}")
        logger.info(f"Size: {self._format_size(archive_size)}")
        
        return str(final_path), archive_size
    
    def _compress_archive(self, archive_path: Path) -> Path:
        """Compress archive using gzip"""
        if not self.config.get('compression.enabled'):
            return archive_path
        
        logger.info("Compressing backup...")
        compressed_path = Path(str(archive_path) + '.gz')
        
        # Using tarfile for compression
        with tarfile.open(compressed_path, 'w:gz') as tar_out:
            tar_out.add(archive_path, arcname=archive_path.name)
        
        # Remove uncompressed archive
        archive_path.unlink()
        
        original_size = os.path.getsize(archive_path) if archive_path.exists() else 0
        compressed_size = os.path.getsize(compressed_path)
        ratio = (1 - compressed_size / max(original_size, 1)) * 100
        
        logger.info(f"Compression saved {ratio:.1f}% space")
        
        return compressed_path
    
    def _encrypt_backup(self, filepath: Path) -> Path:
        """Encrypt backup using Fernet symmetric encryption"""
        try:
            from cryptography.fernet import Fernet
            import base64
        except ImportError:
            logger.warning("cryptography not installed. Skipping encryption.")
            return filepath
        
        logger.info("Encrypting backup...")
        
        key_file = Path(self.config.get('encryption.key_file', '~/.backup_key')).expanduser()
        
        # Generate or load key
        if key_file.exists():
            with open(key_file, 'rb') as f:
                key = f.read()
        else:
            key = Fernet.generate_key()
            key_file.parent.mkdir(parents=True, exist_ok=True)
            with open(key_file, 'wb') as f:
                f.write(key)
            logger.info(f"New encryption key saved to {key_file}")
        
        fernet = Fernet(key)
        
        with open(filepath, 'rb') as f:
            data = f.read()
        
        encrypted = fernet.encrypt(data)
        
        encrypted_path = Path(str(filepath) + '.enc')
        with open(encrypted_path, 'wb') as f:
            f.write(encrypted)
        
        # Remove unencrypted file
        filepath.unlink()
        
        logger.info("Backup encrypted successfully")
        
        return encrypted_path
    
    def _save_manifest(self, backup_name: str, files: List[str]):
        """Save manifest of backed up files"""
        manifest_dir = self.backup_dir / 'manifests'
        manifest_dir.mkdir(exist_ok=True)
        
        manifest_path = manifest_dir / f"{backup_name}.json"
        
        manifest = {
            'backup_name': backup_name,
            'created': datetime.now().isoformat(),
            'file_count': len(files),
            'files': files
        }
        
        with open(manifest_path, 'w') as f:
            json.dump(manifest, f, indent=2)
    
    def _format_size(self, size_bytes: int) -> str:
        """Format size in human-readable format"""
        for unit in ['B', 'KB', 'MB', 'GB', 'TB']:
            if size_bytes < 1024:
                return f"{size_bytes:.2f} {unit}"
            size_bytes /= 1024
        return f"{size_bytes:.2f} PB"
    
    def verify_backup(self, backup_path: str) -> bool:
        """Verify backup integrity"""
        logger.info(f"Verifying backup: {backup_path}")
        
        backup_file = Path(backup_path)
        
        if not backup_file.exists():
            logger.error("Backup file not found!")
            return False
        
        # Check if encrypted
        if backup_path.endswith('.enc'):
            # Verify decryption works
            try:
                from cryptography.fernet import Fernet, InvalidToken
                key_file = Path(self.config.get('encryption.key_file', '~/.backup_key')).expanduser()
                
                if not key_file.exists():
                    logger.error("Encryption key not found!")
                    return False
                
                with open(key_file, 'rb') as f:
                    key = f.read()
                
                fernet = Fernet(key)
                
                with open(backup_path, 'rb') as f:
                    # Try to decrypt first chunk
                    data = f.read()
                    fernet.decrypt(data)
                
                logger.info("Backup decryption verified")
                return True
                
            except InvalidToken:
                logger.error("Invalid encryption key!")
                return False
            except Exception as e:
                logger.error(f"Verification failed: {e}")
                return False
        
        # Check tar integrity
        try:
            if backup_path.endswith('.gz'):
                with tarfile.open(backup_path, 'r:gz') as tar:
                    # Check each member
                    for member in tar.getmembers():
                        pass  # Just iterating checks integrity
            else:
                with tarfile.open(backup_path, 'r') as tar:
                    for member in tar.getmembers():
                        pass
            
            logger.info("Backup integrity verified")
            return True
            
        except Exception as e:
            logger.error(f"Backup corrupted: {e}")
            return False
    
    def rotate_backups(self):
        """Rotate old backups based on retention policy"""
        logger.info("Rotating old backups...")
        
        retention = self.config.get('retention', {})
        daily_keep = retention.get('daily', 7)
        weekly_keep = retention.get('weekly', 4)
        monthly_keep = retention.get('monthly', 6)
        
        # Get all backups
        backups = list(self.backup_dir.glob('backup_*.tar.gz*'))
        backups.sort(key=lambda x: x.stat().st_mtime, reverse=True)
        
        # Separate by type
        daily_backups = [b for b in backups if 'backup_inc_' in b.name]
        full_backups = [b for b in backups if 'backup_full_' in b.name]
        
        # Remove old daily backups
        if len(daily_backups) > daily_keep:
            for old_backup in daily_backups[daily_keep:]:
                logger.info(f"Removing old backup: {old_backup.name}")
                old_backup.unlink()
        
        # Remove old full backups
        if len(full_backups) > weekly_keep + monthly_keep:
            for old_backup in full_backups[weekly_keep + monthly_keep:]:
                logger.info(f"Removing old backup: {old_backup.name}")
                old_backup.unlink()
        
        logger.info("Backup rotation complete")


class RestoreEngine:
    """Restore functionality"""
    
    def __init__(self, config: BackupConfig):
        self.config = config
        self.backup_dir = Path(config.get('backup_dir'))
    
    def list_backups(self) -> List[Dict]:
        """List all available backups"""
        backups = []
        
        for backup_file in self.backup_dir.glob('backup_*.tar.gz*'):
            info = self._parse_backup_name(backup_file.name)
            info['path'] = str(backup_file)
            info['size'] = backup_file.stat().st_size
            info['created'] = datetime.fromtimestamp(backup_file.stat().st_mtime)
            backups.append(info)
        
        # Sort by date, newest first
        backups.sort(key=lambda x: x['created'], reverse=True)
        
        return backups
    
    def _parse_backup_name(self, filename: str) -> Dict:
        """Parse backup filename to extract info"""
        # Format: backup_type_YYYYMMDD_HHMMSS.tar.gz[.enc]
        parts = filename.replace('.tar.gz', '').replace('.enc', '').split('_')
        
        if len(parts) >= 4:
            return {
                'type': parts[1],
                'date_str': f"{parts[2]}_{parts[3]}",
                'encrypted': filename.endswith('.enc')
            }
        
        return {'type': 'unknown', 'date_str': '', 'encrypted': False}
    
    def restore_backup(self, backup_path: str, restore_dir: str, password: str = None) -> bool:
        """Restore files from backup"""
        logger.info(f"Restoring backup: {backup_path}")
        logger.info(f"Restore directory: {restore_dir}")
        
        backup_file = Path(backup_path)
        restore_path = Path(restore_dir)
        
        if not backup_file.exists():
            logger.error("Backup file not found!")
            return False
        
        # Create restore directory
        restore_path.mkdir(parents=True, exist_ok=True)
        
        current_file = backup_file
        
        # Decrypt if needed
        if backup_path.endswith('.enc'):
            current_file = self._decrypt_backup(backup_file, password)
            if current_file is None:
                return False
        
        # Extract files
        try:
            if str(current_file).endswith('.gz'):
                with tarfile.open(current_file, 'r:gz') as tar:
                    tar.extractall(restore_path)
            else:
                with tarfile.open(current_file, 'r') as tar:
                    tar.extractall(restore_path)
            
            logger.info(f"Backup restored to {restore_path}")
            return True
            
        except Exception as e:
            logger.error(f"Restore failed: {e}")
            return False
    
    def _decrypt_backup(self, backup_file: Path, password: str = None) -> Optional[Path]:
        """Decrypt backup file"""
        try:
            from cryptography.fernet import Fernet, InvalidToken
        except ImportError:
            logger.error("cryptography not installed!")
            return None
        
        key_file = Path(self.config.get('encryption.key_file', '~/.backup_key')).expanduser()
        
        if not key_file.exists():
            logger.error("Encryption key not found!")
            return None
        
        with open(key_file, 'rb') as f:
            key = f.read()
        
        fernet = Fernet(key)
        
        try:
            with open(backup_file, 'rb') as f:
                encrypted_data = f.read()
            
            decrypted_data = fernet.decrypt(encrypted_data)
            
            # Save decrypted file temporarily
            decrypted_path = backup_file.with_suffix('')  # Remove .enc
            with open(decrypted_path, 'wb') as f:
                f.write(decrypted_data)
            
            logger.info("Backup decrypted")
            return decrypted_path
            
        except InvalidToken:
            logger.error("Invalid encryption key!")
            return None
        except Exception as e:
            logger.error(f"Decryption failed: {e}")
            return None


class NotificationManager:
    """Handle Termux notifications"""
    
    @staticmethod
    def send_notification(title: str, message: str, sound: bool = True, vibrate: bool = True):
        """Send Termux notification"""
        cmd = ['termux-notification', '--title', title, '--content', message]
        
        if sound:
            cmd.append('--sound')
        if vibrate:
            cmd.append('--vibrate')
        
        try:
            subprocess.run(cmd, check=True)
        except subprocess.CalledProcessError:
            logger.warning("Failed to send notification (termux-api not available?)")
        except FileNotFoundError:
            logger.warning("termux-notification not found. Install termux-api.")


class CloudUploader:
    """Upload backups to cloud storage"""
    
    def __init__(self, config: BackupConfig):
        self.config = config
    
    def upload_to_dropbox(self, filepath: str, token: str) -> bool:
        """Upload backup to Dropbox"""
        try:
            import dropbox
        except ImportError:
            logger.error("dropbox package not installed. Run: pip install dropbox")
            return False
        
        logger.info(f"Uploading to Dropbox: {filepath}")
        
        try:
            dbx = dropbox.Dropbox(token)
            
            filename = os.path.basename(filepath)
            remote_path = f'/Backups/{filename}'
            
            with open(filepath, 'rb') as f:
                file_size = os.path.getsize(filepath)
                
                # Chunked upload for large files
                CHUNK_SIZE = 150 * 1024 * 1024  # 150MB
                
                if file_size > CHUNK_SIZE:
                    upload_session_start_result = dbx.files_upload_session_start(
                        f.read(CHUNK_SIZE)
                    )
                    cursor = dropbox.files.UploadSessionCursor(
                        session_id=upload_session_start_result.session_id,
                        offset=f.tell()
                    )
                    
                    while f.tell() < file_size:
                        if file_size - f.tell() <= CHUNK_SIZE:
                            # Last chunk
                            dbx.files_upload_session_finish(
                                f.read(),
                                cursor,
                                dropbox.files.CommitInfo(path=remote_path)
                            )
                        else:
                            dbx.files_upload_session_append_v2(
                                f.read(CHUNK_SIZE),
                                cursor
                            )
                            cursor.offset = f.tell()
                else:
                    dbx.files_upload(f.read(), remote_path)
            
            logger.info(f"Uploaded to Dropbox: {remote_path}")
            return True
            
        except Exception as e:
            logger.error(f"Dropbox upload failed: {e}")
            return False
    
    def upload_to_gdrive(self, filepath: str, credentials_file: str) -> bool:
        """Upload backup to Google Drive"""
        try:
            from google.oauth2.credentials import Credentials
            from google_auth_oauthlib.flow import InstalledAppFlow
            from googleapiclient.discovery import build
            from googleapiclient.http import MediaFileUpload
        except ImportError:
            logger.error("Google API packages not installed.")
            logger.error("Run: pip install google-api-python-client google-auth-oauthlib")
            return False
        
        logger.info(f"Uploading to Google Drive: {filepath}")
        
        try:
            SCOPES = ['https://www.googleapis.com/auth/drive.file']
            
            creds = None
            token_file = Path(credentials_file).parent / 'token.json'
            
            if token_file.exists():
                creds = Credentials.from_authorized_user_file(str(token_file), SCOPES)
            
            if not creds or not creds.valid:
                flow = InstalledAppFlow.from_client_secrets_file(
                    credentials_file, SCOPES
                )
                creds = flow.run_local_server(port=0)
                
                with open(token_file, 'w') as f:
                    f.write(creds.to_json())
            
            service = build('drive', 'v3', credentials=creds)
            
            file_metadata = {
                'name': os.path.basename(filepath),
                'parents': ['appDataFolder']
            }
            
            media = MediaFileUpload(filepath, resumable=True)
            
            file = service.files().create(
                body=file_metadata,
                media_body=media,
                fields='id'
            ).execute()
            
            logger.info(f"Uploaded to Google Drive, ID: {file.get('id')}")
            return True
            
        except Exception as e:
            logger.error(f"Google Drive upload failed: {e}")
            return False


def main():
    """Main entry point"""
    parser = argparse.ArgumentParser(
        description='Backup Automation System',
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog="""
Examples:
  python backup.py --type full           # Create full backup
  python backup.py --type incremental    # Create incremental backup
  python backup.py --rotate              # Rotate old backups
  python backup.py --verify backup.tar   # Verify backup integrity
  python backup.py --upload dropbox      # Upload last backup to Dropbox
        """
    )
    
    parser.add_argument('--config', '-c', default='config.json',
                        help='Configuration file path')
    parser.add_argument('--type', '-t', choices=['full', 'incremental'],
                        help='Backup type')
    parser.add_argument('--rotate', action='store_true',
                        help='Rotate old backups')
    parser.add_argument('--verify', metavar='BACKUP_FILE',
                        help='Verify backup integrity')
    parser.add_argument('--upload', choices=['dropbox', 'gdrive'],
                        help='Upload to cloud provider')
    parser.add_argument('--notify', action='store_true', default=True,
                        help='Send notifications')
    
    args = parser.parse_args()
    
    # Load configuration
    config = BackupConfig(args.config)
    
    # Initialize components
    backup_engine = BackupEngine(config)
    notification = NotificationManager() if args.notify else None
    
    try:
        if args.type:
            # Create backup
            backup_path, size = backup_engine.create_backup(args.type)
            
            if backup_path:
                if notification:
                    notification.send_notification(
                        "✅ Backup Complete",
                        f"Created: {os.path.basename(backup_path)}\nSize: {backup_engine._format_size(size)}"
                    )
                
                # Upload if requested
                if args.upload:
                    uploader = CloudUploader(config)
                    
                    if args.upload == 'dropbox':
                        token = config.get('cloud.dropbox_token')
                        if token:
                            uploader.upload_to_dropbox(backup_path, token)
                    
                    elif args.upload == 'gdrive':
                        creds = config.get('cloud.gdrive_credentials')
                        if creds:
                            uploader.upload_to_gdrive(backup_path, creds)
        
        elif args.rotate:
            backup_engine.rotate_backups()
            
            if notification:
                notification.send_notification(
                    "🔄 Backup Rotation",
                    "Old backups have been cleaned up"
                )
        
        elif args.verify:
            result = backup_engine.verify_backup(args.verify)
            print(f"Backup integrity: {'✅ VALID' if result else '❌ CORRUPTED'}")
        
        else:
            parser.print_help()
    
    except Exception as e:
        logger.error(f"Backup failed: {e}")
        
        if notification:
            notification.send_notification(
                "❌ Backup Failed",
                f"Error: {str(e)}"
            )
        
        sys.exit(1)


if __name__ == '__main__':
    main()
```

#### restore.py - Restore Script

```python
#!/usr/bin/env python3
"""
Backup Restore Tool
Author: T3rmuxk1ng
"""

import os
import sys
import argparse
from datetime import datetime

# Import from backup.py
from backup import BackupConfig, RestoreEngine, BackupEngine


def format_size(size_bytes: int) -> str:
    """Format size in human-readable format"""
    for unit in ['B', 'KB', 'MB', 'GB']:
        if size_bytes < 1024:
            return f"{size_bytes:.2f} {unit}"
        size_bytes /= 1024
    return f"{size_bytes:.2f} TB"


def print_backup_table(backups: list):
    """Print backups in table format"""
    print("\n" + "=" * 80)
    print(f"{'#':<4} {'Name':<35} {'Type':<12} {'Date':<12} {'Size':<12} {'Enc':<4}")
    print("=" * 80)
    
    for i, backup in enumerate(backups, 1):
        name = backup['path'].split('/')[-1][:33]
        backup_type = backup.get('type', 'unknown').upper()[:10]
        date = backup['created'].strftime('%Y-%m-%d')
        size = format_size(backup['size'])
        enc = '🔒' if backup.get('encrypted') else '  '
        
        print(f"{i:<4} {name:<35} {backup_type:<12} {date:<12} {size:<12} {enc:<4}")
    
    print("=" * 80 + "\n")


def main():
    """Main entry point for restore tool"""
    parser = argparse.ArgumentParser(
        description='Backup Restore Tool',
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog="""
Examples:
  python restore.py --list                          # List all backups
  python restore.py --file backup.tar.gz --to /sdcard/Restored
  python restore.py --interactive                   # Interactive restore
        """
    )
    
    parser.add_argument('--config', '-c', default='config.json',
                        help='Configuration file path')
    parser.add_argument('--list', '-l', action='store_true',
                        help='List available backups')
    parser.add_argument('--file', '-f', metavar='BACKUP_FILE',
                        help='Backup file to restore')
    parser.add_argument('--to', '-t', default='/sdcard/Restored',
                        help='Restore destination directory')
    parser.add_argument('--password', '-p',
                        help='Decryption password')
    parser.add_argument('--interactive', '-i', action='store_true',
                        help='Interactive mode')
    parser.add_argument('--verify', '-v', action='store_true',
                        help='Verify backup before restore')
    
    args = parser.parse_args()
    
    # Load configuration
    config = BackupConfig(args.config)
    restore_engine = RestoreEngine(config)
    backup_engine = BackupEngine(config)
    
    if args.list:
        # List all backups
        backups = restore_engine.list_backups()
        
        if not backups:
            print("\n❌ No backups found!\n")
            return
        
        print_backup_table(backups)
        print(f"Total backups: {len(backups)}\n")
    
    elif args.interactive:
        # Interactive restore mode
        backups = restore_engine.list_backups()
        
        if not backups:
            print("\n❌ No backups found!\n")
            return
        
        print_backup_table(backups)
        
        try:
            selection = int(input("Select backup number (or 0 to cancel): "))
            
            if selection == 0:
                print("Cancelled.")
                return
            
            if selection < 1 or selection > len(backups):
                print("Invalid selection!")
                return
            
            selected_backup = backups[selection - 1]
            backup_path = selected_backup['path']
            
            print(f"\nSelected: {backup_path}")
            
            restore_dir = input(f"Restore directory [{args.to}]: ") or args.to
            
            password = None
            if selected_backup.get('encrypted'):
                print("\n🔒 This backup is encrypted.")
                password = input("Enter password: ")
            
            # Verify if requested
            if args.verify:
                print("\nVerifying backup...")
                if not backup_engine.verify_backup(backup_path):
                    print("❌ Backup verification failed!")
                    return
                print("✅ Backup verified!")
            
            # Perform restore
            print(f"\nRestoring to {restore_dir}...")
            result = restore_engine.restore_backup(backup_path, restore_dir, password)
            
            if result:
                print(f"\n✅ Successfully restored to {restore_dir}")
            else:
                print("\n❌ Restore failed!")
        
        except KeyboardInterrupt:
            print("\n\nCancelled.")
        except ValueError:
            print("Invalid input!")
    
    elif args.file:
        # Direct restore mode
        if args.verify:
            print("Verifying backup...")
            if not backup_engine.verify_backup(args.file):
                print("❌ Backup verification failed!")
                return
            print("✅ Backup verified!")
        
        print(f"Restoring {args.file} to {args.to}...")
        result = restore_engine.restore_backup(args.file, args.to, args.password)
        
        if result:
            print(f"✅ Successfully restored to {args.to}")
        else:
            print("❌ Restore failed!")
    
    else:
        parser.print_help()


if __name__ == '__main__':
    main()
```

### Bash Implementation

#### backup.sh - Bash Backup Script

```bash
#!/data/data/com.termux/files/usr/bin/bash
#
# Backup Automation System - Bash Implementation
# Author: T3rmuxk1ng
# Version: 1.0.0
#
# Features:
# - Full backup
# - Incremental backup
# - Compression
# - Backup rotation
# - Notifications
#

set -e

#═══════════════════════════════════════════════════════════════════════════════
# CONFIGURATION
#═══════════════════════════════════════════════════════════════════════════════

# Default configuration
BACKUP_DIR="${BACKUP_DIR:-/sdcard/Backup}"
LOG_DIR="${BACKUP_DIR}/logs"
LOG_FILE="${LOG_DIR}/backup.log"
SNAPSHOT_FILE="${BACKUP_DIR}/.snapshot"

# Source directories (space-separated)
SOURCE_DIRS=(
    "/sdcard/Documents"
    "/sdcard/DCIM"
    "/sdcard/Download"
)

# Retention policy
DAILY_KEEP="${DAILY_KEEP:-7}"
WEEKLY_KEEP="${WEEKLY_KEEP:-4}"
MONTHLY_KEEP="${MONTHLY_KEEP:-6}"

# Notification settings
NOTIFY_SUCCESS="${NOTIFY_SUCCESS:-true}"
NOTIFY_FAILURE="${NOTIFY_FAILURE:-true}"

# Exclude patterns (for find command)
EXCLUDE_PATTERNS="*.tmp *.cache *.log .git node_modules __pycache__"

#═══════════════════════════════════════════════════════════════════════════════
# UTILITY FUNCTIONS
#═══════════════════════════════════════════════════════════════════════════════

# Logging function
log() {
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    echo "[$timestamp] $1"
    echo "[$timestamp] $1" >> "$LOG_FILE"
}

# Error handling
error_exit() {
    log "ERROR: $1"
    send_notification "❌ Backup Failed" "$1"
    exit 1
}

# Format size
format_size() {
    local size=$1
    local units=("B" "KB" "MB" "GB" "TB")
    local unit=0
    
    while (( size > 1024 )) && (( unit < 4 )); do
        size=$(( size / 1024 ))
        (( unit++ ))
    done
    
    echo "${size} ${units[$unit]}"
}

# Send notification
send_notification() {
    local title="$1"
    local message="$2"
    
    if command -v termux-notification &> /dev/null; then
        termux-notification --title "$title" --content "$message" --sound
    fi
}

# Create exclude arguments for find
build_exclude_args() {
    local args=""
    for pattern in $EXCLUDE_PATTERNS; do
        args="$args -not -name '$pattern'"
    done
    echo "$args"
}

#═══════════════════════════════════════════════════════════════════════════════
# BACKUP FUNCTIONS
#═══════════════════════════════════════════════════════════════════════════════

# Full backup
full_backup() {
    log "Starting full backup..."
    
    local timestamp=$(date +%Y%m%d_%H%M%S)
    local backup_name="backup_full_${timestamp}.tar.gz"
    local backup_path="${BACKUP_DIR}/${backup_name}"
    
    # Create backup directory
    mkdir -p "$BACKUP_DIR"
    mkdir -p "$LOG_DIR"
    
    # Count files
    local file_count=0
    for dir in "${SOURCE_DIRS[@]}"; do
        if [[ -d "$dir" ]]; then
            count=$(find "$dir" -type f 2>/dev/null | wc -l)
            file_count=$(( file_count + count ))
            log "Found $count files in $dir"
        fi
    done
    
    log "Total files to backup: $file_count"
    
    # Create tar archive
    log "Creating archive..."
    
    local tar_args=("-czf" "$backup_path")
    
    for dir in "${SOURCE_DIRS[@]}"; do
        if [[ -d "$dir" ]]; then
            tar_args+=("-C" "$(dirname "$dir")" "$(basename "$dir")")
        fi
    done
    
    if tar "${tar_args[@]}" 2>/dev/null; then
        local size=$(stat -c%s "$backup_path" 2>/dev/null || echo "0")
        local formatted_size=$(format_size "$size")
        
        log "Backup created: $backup_name (Size: $formatted_size)"
        
        # Update snapshot
        touch "$SNAPSHOT_FILE"
        
        # Send notification
        if [[ "$NOTIFY_SUCCESS" == "true" ]]; then
            send_notification "✅ Backup Complete" "Full backup: $backup_name\nSize: $formatted_size"
        fi
        
        return 0
    else
        error_exit "Failed to create backup archive"
    fi
}

# Incremental backup
incremental_backup() {
    log "Starting incremental backup..."
    
    local timestamp=$(date +%Y%m%d_%H%M%S)
    local backup_name="backup_inc_${timestamp}.tar.gz"
    local backup_path="${BACKUP_DIR}/${backup_name}"
    
    # Create directories
    mkdir -p "$BACKUP_DIR"
    mkdir -p "$LOG_DIR"
    
    # Find changed files
    local changed_files=()
    local file_count=0
    
    if [[ -f "$SNAPSHOT_FILE" ]]; then
        log "Last backup: $(date -r "$SNAPSHOT_FILE" '+%Y-%m-%d %H:%M:%S')"
        
        for dir in "${SOURCE_DIRS[@]}"; do
            if [[ -d "$dir" ]]; then
                while IFS= read -r -d '' file; do
                    changed_files+=("$file")
                    (( file_count++ ))
                done < <(find "$dir" -type f -newer "$SNAPSHOT_FILE" -print0 2>/dev/null)
            fi
        done
    else
        log "No previous backup found. Creating full backup instead."
        full_backup
        return $?
    fi
    
    if [[ $file_count -eq 0 ]]; then
        log "No files changed since last backup"
        
        if [[ "$NOTIFY_SUCCESS" == "true" ]]; then
            send_notification "ℹ️ Backup Skipped" "No files changed since last backup"
        fi
        
        return 0
    fi
    
    log "Found $file_count changed files"
    
    # Create archive of changed files
    log "Creating incremental archive..."
    
    # Create file list
    local list_file=$(mktemp)
    printf '%s\n' "${changed_files[@]}" > "$list_file"
    
    if tar -czf "$backup_path" -T "$list_file" 2>/dev/null; then
        rm -f "$list_file"
        
        local size=$(stat -c%s "$backup_path" 2>/dev/null || echo "0")
        local formatted_size=$(format_size "$size")
        
        log "Incremental backup created: $backup_name (Size: $formatted_size)"
        
        # Update snapshot
        touch "$SNAPSHOT_FILE"
        
        # Send notification
        if [[ "$NOTIFY_SUCCESS" == "true" ]]; then
            send_notification "✅ Backup Complete" "Incremental: $backup_name\nFiles: $file_count\nSize: $formatted_size"
        fi
        
        return 0
    else
        rm -f "$list_file"
        error_exit "Failed to create incremental backup"
    fi
}

# Verify backup
verify_backup() {
    local backup_file="$1"
    
    if [[ ! -f "$backup_file" ]]; then
        log "ERROR: Backup file not found: $backup_file"
        return 1
    fi
    
    log "Verifying backup: $backup_file"
    
    if tar -tzf "$backup_file" &>/dev/null; then
        log "✅ Backup integrity verified"
        return 0
    else
        log "❌ Backup is corrupted!"
        return 1
    fi
}

# Restore backup
restore_backup() {
    local backup_file="$1"
    local restore_dir="${2:-/sdcard/Restored}"
    
    if [[ ! -f "$backup_file" ]]; then
        error_exit "Backup file not found: $backup_file"
    fi
    
    log "Restoring $backup_file to $restore_dir"
    
    mkdir -p "$restore_dir"
    
    if tar -xzf "$backup_file" -C "$restore_dir" 2>/dev/null; then
        log "✅ Backup restored to $restore_dir"
        send_notification "✅ Restore Complete" "Backup restored to $restore_dir"
        return 0
    else
        error_exit "Failed to restore backup"
    fi
}

# Rotate old backups
rotate_backups() {
    log "Rotating old backups..."
    
    local inc_count=$(ls "$BACKUP_DIR"/backup_inc_*.tar.gz 2>/dev/null | wc -l)
    local full_count=$(ls "$BACKUP_DIR"/backup_full_*.tar.gz 2>/dev/null | wc -l)
    
    # Rotate incremental (daily) backups
    if [[ $inc_count -gt $DAILY_KEEP ]]; then
        local to_remove=$(( inc_count - DAILY_KEEP ))
        log "Removing $to_remove old incremental backups"
        
        ls -t "$BACKUP_DIR"/backup_inc_*.tar.gz | tail -n $to_remove | xargs rm -f
    fi
    
    # Rotate full (weekly) backups
    if [[ $full_count -gt $WEEKLY_KEEP ]]; then
        local to_remove=$(( full_count - WEEKLY_KEEP ))
        log "Removing $to_remove old full backups"
        
        ls -t "$BACKUP_DIR"/backup_full_*.tar.gz | tail -n $to_remove | xargs rm -f
    fi
    
    log "Backup rotation complete"
    
    if [[ "$NOTIFY_SUCCESS" == "true" ]]; then
        send_notification "🔄 Backup Rotation" "Old backups cleaned up"
    fi
}

# List backups
list_backups() {
    echo ""
    echo "═══════════════════════════════════════════════════════════════════════════════"
    printf "%-4s %-35s %-12s %-12s %-12s\n" "#" "Name" "Type" "Date" "Size"
    echo "═══════════════════════════════════════════════════════════════════════════════"
    
    local i=1
    for backup in $(ls -t "$BACKUP_DIR"/backup_*.tar.gz 2>/dev/null); do
        local name=$(basename "$backup")
        local type="Incremental"
        [[ "$name" == *full* ]] && type="Full"
        
        local date=$(stat -c%y "$backup" 2>/dev/null | cut -d' ' -f1)
        local size=$(stat -c%s "$backup" 2>/dev/null || echo "0")
        local formatted_size=$(format_size "$size")
        
        printf "%-4s %-35s %-12s %-12s %-12s\n" "$i" "${name:0:33}" "$type" "$date" "$formatted_size"
        (( i++ ))
    done
    
    echo "═══════════════════════════════════════════════════════════════════════════════"
    echo ""
}

# Show backup statistics
show_stats() {
    echo ""
    echo "═══════════════════════════════════════════════════════════════════════════════"
    echo "                            BACKUP STATISTICS                                   "
    echo "═══════════════════════════════════════════════════════════════════════════════"
    
    local inc_count=$(ls "$BACKUP_DIR"/backup_inc_*.tar.gz 2>/dev/null | wc -l)
    local full_count=$(ls "$BACKUP_DIR"/backup_full_*.tar.gz 2>/dev/null | wc -l)
    local total_count=$(( inc_count + full_count ))
    
    local total_size=0
    for backup in "$BACKUP_DIR"/backup_*.tar.gz; do
        [[ -f "$backup" ]] && total_size=$(( total_size + $(stat -c%s "$backup" 2>/dev/null || echo 0) ))
    done
    
    local formatted_total=$(format_size "$total_size")
    
    echo "Backup Directory: $BACKUP_DIR"
    echo "Full Backups:     $full_count"
    echo "Incremental:      $inc_count"
    echo "Total Backups:    $total_count"
    echo "Total Size:       $formatted_total"
    
    if [[ -f "$SNAPSHOT_FILE" ]]; then
        echo "Last Backup:      $(date -r "$SNAPSHOT_FILE" '+%Y-%m-%d %H:%M:%S')"
    fi
    
    echo "═══════════════════════════════════════════════════════════════════════════════"
    echo ""
}

#═══════════════════════════════════════════════════════════════════════════════
# MAIN EXECUTION
#═══════════════════════════════════════════════════════════════════════════════

show_help() {
    cat << EOF
Backup Automation System v1.0.0
Author: T3rmuxk1ng

Usage: $0 <command> [options]

Commands:
    full              Create full backup
    incremental       Create incremental backup (only changed files)
    rotate            Rotate old backups (cleanup)
    list              List all backups
    stats             Show backup statistics
    verify <file>     Verify backup integrity
    restore <file> [dir]   Restore backup to directory

Options:
    --config <file>   Use custom config file
    --no-notify       Disable notifications

Examples:
    $0 full                      # Create full backup
    $0 incremental               # Create incremental backup
    $0 rotate                    # Rotate old backups
    $0 list                      # List all backups
    $0 verify backup.tar.gz      # Verify backup
    $0 restore backup.tar.gz /sdcard/Restored

EOF
}

# Parse arguments
COMMAND="${1:-help}"
shift || true

while [[ $# -gt 0 ]]; do
    case "$1" in
        --config)
            CONFIG_FILE="$2"
            shift 2
            ;;
        --no-notify)
            NOTIFY_SUCCESS="false"
            NOTIFY_FAILURE="false"
            shift
            ;;
        *)
            # Positional argument
            if [[ -z "$ARG1" ]]; then
                ARG1="$1"
            elif [[ -z "$ARG2" ]]; then
                ARG2="$1"
            fi
            shift
            ;;
    esac
done

# Execute command
case "$COMMAND" in
    full)
        full_backup
        ;;
    incremental|inc)
        incremental_backup
        ;;
    rotate)
        rotate_backups
        ;;
    list)
        list_backups
        ;;
    stats)
        show_stats
        ;;
    verify)
        [[ -z "$ARG1" ]] && { echo "Usage: $0 verify <backup_file>"; exit 1; }
        verify_backup "$ARG1"
        ;;
    restore)
        [[ -z "$ARG1" ]] && { echo "Usage: $0 restore <backup_file> [restore_dir]"; exit 1; }
        restore_backup "$ARG1" "$ARG2"
        ;;
    help|--help|-h)
        show_help
        ;;
    *)
        echo "Unknown command: $COMMAND"
        echo "Run '$0 help' for usage information"
        exit 1
        ;;
esac
```

#### scheduler.sh - Cron Setup Script

```bash
#!/data/data/com.termux/files/usr/bin/bash
#
# Backup Scheduler Setup
# Author: T3rmuxk1ng
#

SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
BACKUP_SCRIPT="$SCRIPT_DIR/backup.sh"

echo "═══════════════════════════════════════════════════════════════════════════════"
echo "                        BACKUP SCHEDULER SETUP                                  "
echo "═══════════════════════════════════════════════════════════════════════════════"

# Check if cron is installed
if ! command -v crond &> /dev/null; then
    echo "[*] Installing cron..."
    pkg install cronie -y
fi

# Create cron job entries
echo ""
echo "Select backup schedule:"
echo "  1) Daily incremental at 2 AM, Weekly full on Sunday 3 AM"
echo "  2) Daily incremental at 3 AM, Weekly full on Saturday 4 AM"
echo "  3) Custom schedule"
echo "  4) Remove all backup schedules"
echo ""
read -p "Enter choice [1-4]: " choice

case "$choice" in
    1)
        CRON_JOBS=(
            "0 2 * * * $BACKUP_SCRIPT incremental"
            "0 3 * * 0 $BACKUP_SCRIPT full"
            "0 0 * * 1 $BACKUP_SCRIPT rotate"
        )
        ;;
    2)
        CRON_JOBS=(
            "0 3 * * * $BACKUP_SCRIPT incremental"
            "0 4 * * 6 $BACKUP_SCRIPT full"
            "0 0 * * 1 $BACKUP_SCRIPT rotate"
        )
        ;;
    3)
        echo ""
        echo "Enter incremental backup time (hour in 24h format, e.g., 2):"
        read -p "Hour: " inc_hour
        echo "Enter full backup day (0=Sunday, 1=Monday, etc.):"
        read -p "Day: " full_day
        echo "Enter full backup hour:"
        read -p "Hour: " full_hour
        
        CRON_JOBS=(
            "0 $inc_hour * * * $BACKUP_SCRIPT incremental"
            "0 $full_hour * * $full_day $BACKUP_SCRIPT full"
            "0 0 * * 1 $BACKUP_SCRIPT rotate"
        )
        ;;
    4)
        echo "[*] Removing all backup cron jobs..."
        crontab -l 2>/dev/null | grep -v "backup.sh" | crontab -
        echo "[+] Backup schedules removed"
        exit 0
        ;;
    *)
        echo "Invalid choice!"
        exit 1
        ;;
esac

# Get existing crontab
CURRENT_CRON=$(crontab -l 2>/dev/null | grep -v "backup.sh" || true)

# Add new jobs
for job in "${CRON_JOBS[@]}"; do
    CURRENT_CRON="$CURRENT_CRON
$job"
done

# Install new crontab
echo "$CURRENT_CRON" | crontab -

echo ""
echo "[+] Cron jobs installed:"
crontab -l | grep "backup.sh"
echo ""

# Start cron daemon
echo "[*] Starting cron daemon..."
if pgrep -x "crond" > /dev/null; then
    echo "[+] Cron daemon already running"
else
    crond
    echo "[+] Cron daemon started"
fi

# Setup auto-start on boot
BOOT_SCRIPT="$HOME/.termux/boot/cron.sh"
mkdir -p "$(dirname "$BOOT_SCRIPT")"

cat > "$BOOT_SCRIPT" << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
# Start cron daemon on boot
crond
EOF

chmod +x "$BOOT_SCRIPT"
echo "[+] Boot script created: $BOOT_SCRIPT"
echo ""
echo "═══════════════════════════════════════════════════════════════════════════════"
echo "                         SETUP COMPLETE!                                        "
echo "═══════════════════════════════════════════════════════════════════════════════"
echo ""
echo "Your backups will now run automatically!"
echo ""
echo "Useful commands:"
echo "  crontab -l        # View scheduled jobs"
echo "  crontab -e        # Edit scheduled jobs"
echo "  pkill crond       # Stop cron daemon"
echo "  crond             # Start cron daemon"
echo ""
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Backup Setup

```bash
# Task: Set up basic backup system

# Step 1: Create backup directory structure
mkdir -p ~/backup_system
mkdir -p /sdcard/Backup/{full,incremental,logs}

# Step 2: Create test files
mkdir -p /sdcard/TestBackup
echo "Important document 1" > /sdcard/TestBackup/doc1.txt
echo "Important document 2" > /sdcard/TestBackup/doc2.txt

# Step 3: Create configuration file
cat > ~/backup_system/config.json << 'EOF'
{
    "source_dirs": ["/sdcard/TestBackup"],
    "backup_dir": "/sdcard/Backup",
    "retention": {"daily": 3, "weekly": 2}
}
EOF

# Step 4: Create simple backup script
cat > ~/backup_system/simple_backup.sh << 'EOF'
#!/bin/bash
BACKUP_DIR="/sdcard/Backup"
SOURCE="/sdcard/TestBackup"
DATE=$(date +%Y%m%d_%H%M%S)

tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" -C "$(dirname $SOURCE)" "$(basename $SOURCE)"
echo "Backup created: backup_$DATE.tar.gz"
EOF

chmod +x ~/backup_system/simple_backup.sh

# Step 5: Run backup
~/backup_system/simple_backup.sh

# Step 6: Verify backup
ls -la /sdcard/Backup/
tar -tzf /sdcard/Backup/backup_*.tar.gz

# Expected: Backup file created and contains test files
```

### Exercise 2: Incremental Backup Implementation

```bash
# Task: Implement incremental backup

# Step 1: Create incremental backup script
cat > ~/backup_system/incremental.sh << 'EOF'
#!/bin/bash
BACKUP_DIR="/sdcard/Backup"
SOURCE="/sdcard/TestBackup"
SNAPSHOT="$BACKUP_DIR/.snapshot"
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p "$BACKUP_DIR"

if [ -f "$SNAPSHOT" ]; then
    echo "Finding changed files since last backup..."
    CHANGED=$(find "$SOURCE" -type f -newer "$SNAPSHOT" 2>/dev/null)
    
    if [ -z "$CHANGED" ]; then
        echo "No files changed."
        exit 0
    fi
    
    echo "$CHANGED" | tar -czf "$BACKUP_DIR/inc_$DATE.tar.gz" -T -
    echo "Incremental backup created: inc_$DATE.tar.gz"
else
    echo "First backup - creating full backup..."
    tar -czf "$BACKUP_DIR/full_$DATE.tar.gz" -C "$(dirname $SOURCE)" "$(basename $SOURCE)"
    echo "Full backup created: full_$DATE.tar.gz"
fi

touch "$SNAPSHOT"
EOF

chmod +x ~/backup_system/incremental.sh

# Step 2: Run first backup (full)
~/backup_system/incremental.sh

# Step 3: Add new file
echo "New file" > /sdcard/TestBackup/newfile.txt

# Step 4: Run incremental backup
~/backup_system/incremental.sh

# Step 5: Compare sizes
ls -lh /sdcard/Backup/

# Expected: Second backup smaller (only new file)
```

### Exercise 3: Backup Rotation

```bash
# Task: Implement backup rotation

# Step 1: Create multiple test backups
for i in {1..10}; do
    DATE=$(date -d "$i days ago" +%Y%m%d 2>/dev/null || date -v-${i}d +%Y%m%d)
    touch "/sdcard/Backup/backup_$DATE.tar.gz"
done

# Step 2: List current backups
echo "Current backups:"
ls -la /sdcard/Backup/backup_*.tar.gz

# Step 3: Create rotation script
cat > ~/backup_system/rotate.sh << 'EOF'
#!/bin/bash
BACKUP_DIR="/sdcard/Backup"
KEEP_COUNT=5

BACKUP_COUNT=$(ls "$BACKUP_DIR"/backup_*.tar.gz 2>/dev/null | wc -l)

echo "Total backups: $BACKUP_COUNT"
echo "Keeping: $KEEP_COUNT"

if [ $BACKUP_COUNT -gt $KEEP_COUNT ]; then
    TO_REMOVE=$((BACKUP_COUNT - KEEP_COUNT))
    echo "Removing $TO_REMOVE old backups..."
    
    ls -t "$BACKUP_DIR"/backup_*.tar.gz | tail -n $TO_REMOVE | xargs rm -f
    echo "Rotation complete!"
else
    echo "No rotation needed."
fi
EOF

chmod +x ~/backup_system/rotate.sh

# Step 4: Run rotation
~/backup_system/rotate.sh

# Step 5: Verify result
ls -la /sdcard/Backup/backup_*.tar.gz

# Expected: Only 5 newest backups remain
```

### Exercise 4: Cron Job Setup

```bash
# Task: Set up automated backup with cron

# Step 1: Install cron
pkg install cronie -y

# Step 2: Create backup script path
BACKUP_SCRIPT="$HOME/backup_system/incremental.sh"

# Step 3: Add cron job
# Edit crontab
crontab -l 2>/dev/null > /tmp/current_cron
echo "0 * * * * $BACKUP_SCRIPT" >> /tmp/current_cron
crontab /tmp/current_cron

# Step 4: View scheduled jobs
crontab -l

# Step 5: Start cron daemon
crond

# Step 6: Verify cron is running
pgrep -a crond

# Step 7: Create boot script
mkdir -p ~/.termux/boot
cat > ~/.termux/boot/start_cron.sh << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
crond
EOF
chmod +x ~/.termux/boot/start_cron.sh

# Expected: Cron running and will execute backup hourly
```

### Exercise 5: Complete Backup System

```bash
# Task: Create complete backup system with notifications

# Step 1: Download complete scripts
# (Use the full source code from this chapter)

# Step 2: Make executable
chmod +x ~/backup_system/*.sh
chmod +x ~/backup_system/*.py

# Step 3: Configure
# Edit config.json with your directories

# Step 4: Test full backup
cd ~/backup_system
python backup.py --config config.json --type full

# Step 5: Modify a file
echo "Modified content" >> /sdcard/TestBackup/doc1.txt

# Step 6: Test incremental backup
python backup.py --config config.json --type incremental

# Step 7: List backups
python restore.py --list

# Step 8: Test restore
python restore.py --interactive

# Step 9: Verify restored files
ls -la /sdcard/Restored/

# Expected: Complete backup system working
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Permission Denied

```bash
# Cause: Script not executable or storage permission missing

# Solution 1: Make script executable
chmod +x backup.sh

# Solution 2: Grant storage permission
termux-setup-storage

# Solution 3: Check file ownership
ls -la backup.sh

# Solution 4: Run with bash explicitly
bash backup.sh full
```

### Problem 2: "No space left on device"

```bash
# Cause: Storage full

# Solution 1: Check storage space
df -h

# Solution 2: Clean old backups
./backup.sh rotate

# Solution 3: Manual cleanup
ls -la /sdcard/Backup/
rm /sdcard/Backup/backup_old_*.tar.gz

# Solution 4: Compress more aggressively
# Edit config.json and increase compression level
# "compression": {"level": 9}
```

### Problem 3: Backup Corruption

```bash
# Cause: Interrupted backup or disk errors

# Solution 1: Verify backup integrity
tar -tzf backup_file.tar.gz > /dev/null

# Solution 2: Check for partial files
ls -la /sdcard/Backup/*.partial
rm /sdcard/Backup/*.partial

# Solution 3: Create new full backup
./backup.sh full

# Solution 4: Use verification option
python backup.py --verify backup_file.tar.gz
```

### Problem 4: Cron Job Not Running

```bash
# Cause: Cron daemon not running or wrong path

# Solution 1: Check if crond is running
pgrep -a crond

# Solution 2: Start cron daemon
crond

# Solution 3: Check cron logs
# Cron logs in Termux
cat $PREFIX/var/log/cron.log

# Solution 4: Use absolute paths in crontab
crontab -l
# Should have full paths like:
# 0 2 * * * /data/data/com.termux/files/home/backup_system/backup.sh

# Solution 5: Test script manually
/data/data/com.termux/files/home/backup_system/backup.sh incremental
```

### Problem 5: Encryption/Decryption Fails

```bash
# Cause: Wrong key or corrupted key file

# Solution 1: Check key file exists
ls -la ~/.backup_key

# Solution 2: Generate new key (old backups won't be readable!)
python -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())" > ~/.backup_key

# Solution 3: Decrypt manually for testing
python -c "
from cryptography.fernet import Fernet
import sys

with open('/sdcard/.backup_key', 'rb') as f:
    key = f.read()

fernet = Fernet(key)

with open(sys.argv[1], 'rb') as f:
    encrypted = f.read()

decrypted = fernet.decrypt(encrypted)
sys.stdout.buffer.write(decrypted)
" backup.tar.gz.enc > backup.tar.gz

# Solution 4: Keep backups unencrypted if encryption causes issues
# Edit config.json: "encryption": {"enabled": false}
```

### Problem 6: Notification Not Working

```bash
# Cause: Termux:API not installed or configured

# Solution 1: Install Termux:API app
# Download from F-Droid

# Solution 2: Install termux-api package
pkg install termux-api -y

# Solution 3: Test notification
termux-notification --title "Test" --content "Notification works!"

# Solution 4: Check permissions
# Settings > Apps > Termux:API > Permissions
# Enable all permissions

# Solution 5: Alternative - use toast
termux-toast "Backup complete!"
```

### Problem 7: Incremental Backup Backing Up Everything

```bash
# Cause: Snapshot file missing or corrupted

# Solution 1: Check snapshot file
ls -la /sdcard/Backup/.snapshot

# Solution 2: Create snapshot manually
touch /sdcard/Backup/.snapshot

# Solution 3: Reset incremental chain
# Run full backup first
./backup.sh full

# Solution 4: Check file modification times
stat /sdcard/TestBackup/doc1.txt

# Solution 5: Debug incremental logic
# Add debug to script
find "/sdcard/Documents" -type f -newer "/sdcard/Backup/.snapshot"
```

### Problem 8: Cloud Upload Fails

```bash
# Cause: Authentication or network issues

# Solution 1: Check internet connection
ping -c 3 google.com

# Solution 2: Verify Dropbox token
python -c "
import dropbox
dbx = dropbox.Dropbox('YOUR_TOKEN')
print(dbx.users_get_current_account())
"

# Solution 3: For Google Drive, re-authenticate
# Delete token.json and run upload again
rm ~/.backup_system/token.json

# Solution 4: Check file size limits
# Dropbox: 150MB for simple upload
# Use chunked upload for larger files

# Solution 5: Test with small file first
echo "test" > /sdcard/test_upload.txt
# Then try to upload this small file
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Blue Background]            │
│                                    │
│   💾 BACKUP AUTOMATION             │
│   🔄 Never Lose Data Again!        │
│                                    │
│   ✓ Full & Incremental             │
│   ✓ Cloud Upload                   │
│   ✓ Auto Scheduled                 │
│                                    │
│   [T3rmuxk1ng Logo]                │
│   Chapter 57                       │
└────────────────────────────────────┘
```

**Option B: Warning Style**
```
┌────────────────────────────────────┐
│  ⚠️ DATA LOSS ALERT!               │
│                                    │
│  Don't wait until it's too late!   │
│                                    │
│  🔒 BACKUP AUTOMATION SYSTEM       │
│                                    │
│  Full Project Tutorial             │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  [Terminal Screenshot Background]  │
│                                    │
│  PROJECT 7:                        │
│  BACKUP SYSTEM 🔄                  │
│                                    │
│  Python + Bash Implementation      │
│  Auto-Schedule + Cloud Upload      │
│                                    │
│  Full Course | Ch 57               │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
💾 Termux Full Course - Chapter 57: Backup Automation System | Complete Project

🔥 In this video you'll learn:
• Backup strategy design (3-2-1 rule)
• Full and incremental backup implementation
• Compression and encryption
• Cloud upload (Dropbox, Google Drive)
• Automatic scheduling with cron
• Backup rotation and verification
• Complete restore functionality

⏱️ Timestamps:
0:00 - Introduction
1:00 - Project Overview
4:00 - Backup Strategy Design
7:00 - Python Implementation
14:00 - Restore Functionality
17:00 - Cloud Integration
20:00 - Scheduling & Notifications
23:00 - Bash Implementation
26:00 - Summary & Next Steps

📦 Source Code:
GitHub: [LINK]

📝 Commands from this video:
pkg install python cronie -y
pip install cryptography dropbox
python backup.py --type full
python restore.py --list
crontab -e
crond

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #BackupAutomation #Python #Bash #T3rmuxk1ng #TermuxProject #DataBackup #TermuxCourse

---
⚠️ Disclaimer: This video is for educational purposes. Always test backup systems thoroughly before relying on them for critical data.
```

### Tags List

```
termux, termux backup, backup automation, backup system, 
python backup script, bash backup, incremental backup,
full backup, backup rotation, cron job termux,
termux project, termux course, t3rmuxk1ng, data backup,
cloud backup, dropbox upload, termux automation,
scheduled backup, backup encryption, termux tutorial,
android backup, linux backup script, backup restore,
data protection, backup strategy
```

### Hashtags

```
#Termux #BackupAutomation #PythonScript #BashScript #TermuxProject 
#DataBackup #TermuxCourse #T3rmuxk1ng #BackupSystem #Automation 
#CloudBackup #CronJob #IncrementalBackup #DataProtection
```

---

## 📚 ADDITIONAL RESOURCES

### Backup Best Practices

| Practice | Description |
|----------|-------------|
| 3-2-1 Rule | 3 copies, 2 different media, 1 offsite |
| Test Restores | Regularly verify backups can be restored |
| Document Everything | Keep logs of backup schedules and locations |
| Automate | Remove human error from the equation |
| Encrypt | Protect sensitive backup data |
| Version Control | Keep multiple backup versions |

### Useful Commands Reference

```bash
# Manual backup commands
tar -czf backup.tar.gz /path/to/source    # Create compressed archive
tar -xzf backup.tar.gz -C /restore/path   # Extract archive
tar -tzf backup.tar.gz                     # List archive contents

# File timestamps
stat filename                              # View file timestamps
touch filename                             # Update modification time
find . -mtime -1                           # Files modified in last 24h

# Cron quick reference
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of week (0 - 6) (Sunday = 0)
# │ │ │ │ │
# * * * * * command

# Cron examples
0 2 * * *    # Daily at 2:00 AM
0 3 * * 0    # Weekly Sunday at 3:00 AM
0 4 1 * *    # Monthly on 1st at 4:00 AM
*/30 * * * * # Every 30 minutes
```

### Related Chapters

| Chapter | Topic | Relevance |
|---------|-------|-----------|
| Ch13 | Bash Scripting Basics | Script foundations |
| Ch14 | Bash Scripting Advanced | Advanced techniques |
| Ch43 | Task Automation | Cron & scheduling |
| Ch44 | Termux Widgets | Quick backup shortcuts |
| Ch60 | Termux Backup & Restore | Termux self-backup |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 58, verify:

- [ ] Backup system installed and configured
- [ ] Full backup created successfully
- [ ] Incremental backup working correctly
- [ ] Backup rotation tested
- [ ] Cron job scheduled and running
- [ ] Notifications working
- [ ] Restore tested successfully
- [ ] Understanding of backup strategy

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 58: Common Errors & Fixes**

- Termux error messages explained
- Package installation issues
- Permission problems
- Storage access errors
- Network connectivity issues
- Performance troubleshooting
- Complete error reference guide

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
