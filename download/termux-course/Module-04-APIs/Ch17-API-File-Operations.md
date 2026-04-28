# Chapter 17: Termux API - File Operations

> **Module:** 4 - APIs  
> **Chapter:** 17 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | File operations using Termux API |
| API Commands | termux-storage-get, termux-share, termux-download |
| Commands Reference | All file operation commands covered |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Permission and file access issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 17
Title: Termux API File Operations | Storage, Share, Download | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut practical hai - kyunki aaj hum seekhenge Termux se 
file operations kaise perform karein using Termux API!

File operations ka matlab - files pick karna, share karna, download karna,
aur media scanner ko trigger karna. Ye sab tasks aapko daily automation 
scripts mein kaam aayenge.

Imagine karein - ek script jo automatic files download kare, unhe organize 
kare, aur media gallery mein dikhaye. All possible with Termux API!

To chaliye shuru karte hain - Termux API File Operations!

Play button dabaiye, video like karein, channel subscribe karein!

---

[SECTION 1: FILE OPERATIONS OVERVIEW - 0:50 to 3:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle samajhte hain - Termux mein file operations kya hote hain?

Termux by default Linux filesystem use karta hai. Aapki files 
/data/data/com.termux/files/home mein rehti hain. Ye Android ke 
shared storage se alag hai - jahan photos, downloads, music rehte hain.

File Operations APIs ye kaam karte hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX FILE OPERATION APIs                            │
├──────────────────────┬──────────────────────────────────────────────────┤
│ API Command          │ Purpose                                         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ termux-storage-get   │ File picker - user se file select karna        │
│ termux-share         │ Files/text ko other apps mein share karna      │
│ termux-download      │ URL se files download karna                    │
│ termux-media-scan    │ Media gallery mein files dikhana              │
└──────────────────────┴──────────────────────────────────────────────────┘

Ye APIs Android ke native features use karte hain:

✓ termux-storage-get → Android Storage Access Framework
✓ termux-share → Android Share Intent
✓ termux-download → Android Download Manager
✓ termux-media-scan → Android MediaStore

Sabse important baat - ye sab ROOT ke bina kaam karta hai!

---

[SECTION 2: STORAGE GET - FILE PICKER - 3:00 to 6:30]
─────────────────────────────────────────────────────────────────────────────

Pehle command dekhte hain - termux-storage-get

Ye command Android ka file picker open karta hai. User koi bhi file 
select kar sakta hai - photo, video, document, anything!

Basic syntax:

    termux-storage-get <destination_path>

Example:

    termux-storage-get ~/picked_file.txt

[SCREEN: Android file picker dialog]

Jab aap ye command run karoge, Android file picker popup hoga. Aap 
koi bhi file select kar sakte ho - gallery se photo, downloads se 
PDF, documents se text file - kuch bhi!

File select karne ke baad, wo file Termux mein copy ho jaayegi 
aapke specified path pe.

Let's try a practical example:

    # Pick an image from gallery
    termux-storage-get ~/my_photo.jpg

    # Pick a PDF document
    termux-storage-get ~/document.pdf

    # Pick any file
    termux-storage-get ~/selected_file

File picker se file select karo, aur wo Termux home directory mein 
save ho jaayegi.

Verify karein:

    ls -la ~/
    file ~/my_photo.jpg

Important points yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX-STORAGE-GET IMPORTANT POINTS                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│ 1. Destination path must be writable in Termux                          │
│    ✓ ~/file.txt (Good - Termux home)                                    │
│    ✗ /sdcard/file.txt (Won't work directly)                             │
│                                                                          │
│ 2. File gets COPIED, not moved                                          │
│    Original file remains at source location                             │
│                                                                          │
│ 3. Works with any file type                                             │
│    Images, videos, PDFs, documents, archives - all supported            │
│                                                                          │
│ 4. Requires storage permission                                          │
│    Run: termux-setup-storage first                                      │
│                                                                          │
│ 5. Returns 0 on success, non-zero on failure                            │
│    Useful for scripting conditions                                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 3: SHARE API - FILES & TEXT - 6:30 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab termux-share command dekhte hain - bahut useful hai!

Ye command Android share dialog open karta hai. Aap files ya text 
kisi bhi app mein share kar sakte ho - WhatsApp, Telegram, Gmail, 
Bluetooth - kuch bhi!

Basic syntax:

    termux-share <file_path>

    # Or for text
    echo "text" | termux-share

[EXAMPLE 1: Share a file]

    # Create a file
    echo "Hello from Termux!" > ~/hello.txt

    # Share it
    termux-share ~/hello.txt

[SCREEN: Android share dialog]

Share dialog open hoga with all apps listed - WhatsApp, Telegram, 
Gmail, Bluetooth, etc. Koi bhi app select karo aur file share ho jaayegi!

[EXAMPLE 2: Share with specific MIME type]

    termux-share -c "image/jpeg" ~/photo.jpg

    termux-share -c "application/pdf" ~/document.pdf

    termux-share -c "text/plain" ~/notes.txt

MIME type se apps better handle karti hain files ko.

[EXAMPLE 3: Share text directly]

    echo "Check out this cool Termux trick!" | termux-share

Ye text share hoga - paste kar sakte ho kisi bhi app mein.

[EXAMPLE 4: Share with action]

    # View action
    termux-share -a view ~/photo.jpg

    # Edit action
    termux-share -a edit ~/notes.txt

    # Send action (default)
    termux-share -a send ~/document.pdf

Complete options:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX-SHARE OPTIONS                                  │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Option               │ Description                                     │
├──────────────────────┼──────────────────────────────────────────────────┤
│ -a, --action         │ Action: send, view, edit                        │
│ -c, --content-type   │ MIME type (image/jpeg, text/plain, etc.)       │
│ -d, --default        │ Use default app directly                        │
│ -t, --title          │ Title for the share intent                      │
│ -e, --edit           │ Open in edit mode                               │
│ --input              │ Read file to share from stdin                  │
└──────────────────────┴──────────────────────────────────────────────────┘

Practical use case:

    # Share WiFi scan results
    termux-wifi-scaninfo > ~/wifi_scan.json
    termux-share -c "application/json" ~/wifi_scan.json

    # Share location
    termux-location > ~/location.json
    termux-share ~/location.json

---

[SECTION 4: DOWNLOAD API - FILES FROM URL - 10:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Ab bahut important command - termux-download!

Ye command Android Download Manager use karta hai files download 
karne ke liye. Background mein download, resume support, notification - 
sab automatic!

Basic syntax:

    termux-download <URL>

[EXAMPLE 1: Simple download]

    termux-download "https://example.com/file.pdf"

[SCREEN: Download notification in status bar]

Notification mein download progress dikhai dega. Background mein 
download hoga, aap Termux use karte raho!

Default download location: /sdcard/Download

[EXAMPLE 2: Download with options]

    termux-download \
      -d /sdcard/Download \
      -t "MyFile.pdf" \
      "https://example.com/document.pdf"

Options explained:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX-DOWNLOAD OPTIONS                               │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Option               │ Description                                     │
├──────────────────────┼──────────────────────────────────────────────────┤
│ -d, --path           │ Destination folder (default: /sdcard/Download)  │
│ -t, --title          │ Title for notification                          │
│ -p, --path           │ Same as -d, destination path                   │
│ -r, --description    │ Description for notification                    │
└──────────────────────┴──────────────────────────────────────────────────┘

[EXAMPLE 3: Download to specific folder]

    # Download to custom folder
    termux-download -d /sdcard/Documents "https://example.com/report.pdf"

    # Download image
    termux-download -d /sdcard/Pictures "https://example.com/photo.jpg"

    # Download with custom title
    termux-download -t "Termux Guide" "https://example.com/guide.pdf"

[EXAMPLE 4: Multiple downloads]

    # Download multiple files
    termux-download "https://example.com/file1.pdf"
    termux-download "https://example.com/file2.pdf"

Download command ke benefits:

✓ Background download - Termux band karne pe bhi download hota hai
✓ Resume support - Network issue pe automatically resume
✓ Notification - Progress notification dikhai deta hai
✓ Android Download Manager - Stable and reliable
✓ Works with any file type

Important URLs yaad rakhein:

    # Direct file URLs work best
    https://example.com/file.pdf  ✓

    # Redirect URLs bhi kaam karte hain
    https://drive.google.com/uc?export=download&id=FILE_ID  ✓

    # Password protected files won't work directly
    https://protected-site.com/file.pdf  ✗

---

[SECTION 5: MEDIA SCAN - GALLERY VISIBILITY - 14:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek important but often overlooked command - termux-media-scan!

Samajhte hain problem: Aap Termux mein koi image download ya create 
karte ho. Wo file storage mein hai, lekin Gallery app mein nahi dikhti!

Kyun? Kyunki Android MediaStore ko update karna padta hai.

Media Scanner ye kaam karta hai - files ko MediaStore mein register 
karta hai taaki Gallery, Music Player, etc. mein dikhein.

Basic syntax:

    termux-media-scan <file_path>

[EXAMPLE 1: Scan single file]

    # Download an image
    wget -O /sdcard/DCIM/myphoto.jpg "https://example.com/photo.jpg"

    # Scan it for gallery
    termux-media-scan /sdcard/DCIM/myphoto.jpg

Ab Gallery app check karo - photo dikhegi!

[EXAMPLE 2: Scan multiple files]

    # Scan all images in a folder
    termux-media-scan /sdcard/DCIM/*.jpg

    # Scan all downloads
    termux-media-scan /sdcard/Download/*

[EXAMPLE 3: Scan recursively]

    # Scan entire directory tree
    for file in /sdcard/DCIM/Camera/*; do
        termux-media-scan "$file"
    done

When to use media-scan:

┌─────────────────────────────────────────────────────────────────────────┐
│                    WHEN TO USE TERMUX-MEDIA-SCAN                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│ ✓ After downloading images/videos                                       │
│ ✓ After creating/editing media files                                    │
│ ✓ After copying files to shared storage                                 │
│ ✓ When Gallery doesn't show new files                                   │
│ ✓ After batch file operations                                           │
│                                                                          │
│ ✗ NOT needed for termux-download (automatic scan)                       │
│ ✗ NOT needed for files in Termux home                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Python se batch scan:

    #!/usr/bin/env python3
    import os
    import subprocess
    
    folder = "/sdcard/DCIM/Camera"
    for root, dirs, files in os.walk(folder):
        for file in files:
            if file.lower().endswith(('.jpg', '.png', '.mp4')):
                filepath = os.path.join(root, file)
                subprocess.run(['termux-media-scan', filepath])
                print(f"Scanned: {file}")

---

[SECTION 6: PYTHON INTEGRATION - 17:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain Python ke saath file operations kaise integrate karein.

Python powerful hai automation ke liye. Termux API commands ko 
subprocess se call kar sakte ho.

[EXAMPLE 1: File Picker with Python]

```python
#!/usr/bin/env python3
import subprocess
import os

def pick_file(dest_path):
    """Open file picker and return selected file path"""
    result = subprocess.run(
        ['termux-storage-get', os.path.expanduser(dest_path)],
        capture_output=True
    )
    
    if result.returncode == 0:
        return os.path.expanduser(dest_path)
    else:
        return None

# Usage
selected = pick_file('~/picked_file')
if selected:
    print(f"File saved to: {selected}")
    print(f"Size: {os.path.getsize(selected)} bytes")
else:
    print("No file selected")
```

[EXAMPLE 2: Download with Python]

```python
#!/usr/bin/env python3
import subprocess
import os

def download_file(url, dest_folder="/sdcard/Download", title=None):
    """Download file using Android Download Manager"""
    cmd = ['termux-download', '-d', dest_folder]
    
    if title:
        cmd.extend(['-t', title])
    
    cmd.append(url)
    
    result = subprocess.run(cmd, capture_output=True)
    return result.returncode == 0

# Usage
if download_file(
    "https://example.com/file.pdf",
    "/sdcard/Documents",
    "My Document"
):
    print("Download started!")
else:
    print("Download failed")
```

[EXAMPLE 3: Share with Python]

```python
#!/usr/bin/env python3
import subprocess

def share_file(filepath, mime_type=None):
    """Share file via Android share dialog"""
    cmd = ['termux-share']
    
    if mime_type:
        cmd.extend(['-c', mime_type])
    
    cmd.append(os.path.expanduser(filepath))
    
    subprocess.run(cmd)

def share_text(text):
    """Share text via Android share dialog"""
    subprocess.run(['termux-share'], input=text.encode())

# Usage
share_file('~/report.pdf', 'application/pdf')
share_text("Hello from Termux Python!")
```

[EXAMPLE 4: Media Scanner with Python]

```python
#!/usr/bin/env python3
import subprocess
import os

def scan_media(path):
    """Scan file/folder for media gallery"""
    path = os.path.expanduser(path)
    
    if os.path.isfile(path):
        subprocess.run(['termux-media-scan', path])
        return 1
    
    count = 0
    for root, dirs, files in os.walk(path):
        for file in files:
            filepath = os.path.join(root, file)
            subprocess.run(['termux-media-scan', filepath])
            count += 1
    
    return count

# Usage
scanned = scan_media('/sdcard/DCIM/Camera')
print(f"Scanned {scanned} files")
```

[EXAMPLE 5: Complete File Manager Class]

```python
#!/usr/bin/env python3
import subprocess
import os
import json

class TermuxFileManager:
    def __init__(self):
        self.download_dir = "/sdcard/Download"
        self.home = os.path.expanduser("~")
    
    def pick_file(self, dest_name="picked_file"):
        """Pick file using Android file picker"""
        dest = os.path.join(self.home, dest_name)
        result = subprocess.run(
            ['termux-storage-get', dest],
            capture_output=True
        )
        return dest if result.returncode == 0 else None
    
    def download(self, url, filename=None):
        """Download file from URL"""
        cmd = ['termux-download', '-d', self.download_dir]
        if filename:
            cmd.extend(['-t', filename])
        cmd.append(url)
        subprocess.run(cmd)
        return os.path.join(self.download_dir, filename or "")
    
    def share(self, path, mime=None):
        """Share file"""
        cmd = ['termux-share']
        if mime:
            cmd.extend(['-c', mime])
        cmd.append(path)
        subprocess.run(cmd)
    
    def scan_for_gallery(self, path):
        """Make file visible in gallery"""
        subprocess.run(['termux-media-scan', path])
    
    def get_file_info(self, path):
        """Get file information"""
        if not os.path.exists(path):
            return None
        
        stat = os.stat(path)
        return {
            'path': path,
            'size': stat.st_size,
            'modified': stat.st_mtime,
            'is_file': os.path.isfile(path)
        }

# Usage
fm = TermuxFileManager()

# Pick a file
file = fm.pick_file("my_file")
if file:
    info = fm.get_file_info(file)
    print(json.dumps(info, indent=2))
    
    # Share it
    fm.share(file)
```

---

[SECTION 7: BASH SCRIPT EXAMPLES - 20:00 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch practical Bash scripts dekhte hain.

[SCRIPT 1: File Picker and Analyzer]

```bash
#!/bin/bash
# file_analyzer.sh - Pick and analyze any file

DEST="$HOME/analyzed_file"

echo "Select a file to analyze..."
termux-storage-get "$DEST"

if [ -f "$DEST" ]; then
    echo ""
    echo "================================"
    echo "     FILE ANALYSIS REPORT"
    echo "================================"
    echo ""
    echo "File: $DEST"
    echo "Size: $(du -h "$DEST" | cut -f1)"
    echo "Type: $(file -b "$DEST")"
    echo "Modified: $(stat -c %y "$DEST")"
    echo ""
    
    read -p "Share this file? (y/n): " choice
    if [ "$choice" = "y" ]; then
        termux-share "$DEST"
    fi
else
    echo "No file selected!"
fi
```

[SCRIPT 2: Batch Downloader]

```bash
#!/bin/bash
# batch_download.sh - Download multiple files from list

DOWNLOAD_LIST="$HOME/download_list.txt"
DEST_DIR="/sdcard/Download/TermuxDownloads"

# Create destination
mkdir -p "$DEST_DIR"

# Create download list if not exists
if [ ! -f "$DOWNLOAD_LIST" ]; then
    echo "Creating sample download list..."
    cat > "$DOWNLOAD_LIST" << EOF
# Add URLs here (one per line)
# https://example.com/file1.pdf
# https://example.com/file2.jpg
EOF
    echo "Edit $DOWNLOAD_LIST and add your URLs"
    exit 0
fi

# Download each URL
count=0
while IFS= read -r url; do
    # Skip comments and empty lines
    [[ "$url" =~ ^#.*$ ]] && continue
    [[ -z "$url" ]] && continue
    
    count=$((count + 1))
    filename=$(basename "$url" | cut -d'?' -f1)
    
    echo "Downloading: $filename"
    termux-download -d "$DEST_DIR" -t "$filename" "$url"
    
    # Small delay between downloads
    sleep 2
done < "$DOWNLOAD_LIST"

echo ""
echo "Downloads initiated: $count"
echo "Location: $DEST_DIR"
```

[SCRIPT 3: Media Organizer]

```bash
#!/bin/bash
# media_organizer.sh - Organize and scan media files

SOURCE_DIR="/sdcard/DCIM/Camera"
ORGANIZED_DIR="/sdcard/Pictures/Organized"

mkdir -p "$ORGANIZED_DIR"

echo "Organizing media files..."

# Organize by date
for file in "$SOURCE_DIR"/*; do
    if [ -f "$file" ]; then
        # Get file date
        date_str=$(stat -c %y "$file" | cut -d' ' -f1)
        year=$(echo "$date_str" | cut -d'-' -f1)
        month=$(echo "$date_str" | cut -d'-' -f2)
        
        # Create folder
        dest_folder="$ORGANIZED_DIR/$year/$month"
        mkdir -p "$dest_folder"
        
        # Copy file (keeping original)
        filename=$(basename "$file")
        cp "$file" "$dest_folder/$filename"
        
        # Scan for gallery
        termux-media-scan "$dest_folder/$filename"
    fi
done

echo "Organization complete!"
echo "Files organized in: $ORGANIZED_DIR"

# Share organized folder info
echo "Media files organized by date" | termux-share
```

[SCRIPT 4: Quick Share Tool]

```bash
#!/bin/bash
# quick_share.sh - Quick file/text sharing

show_menu() {
    echo ""
    echo "╔════════════════════════════╗"
    echo "║     QUICK SHARE TOOL       ║"
    echo "╠════════════════════════════╣"
    echo "║ 1. Share text              ║"
    echo "║ 2. Share file              ║"
    echo "║ 3. Pick and share          ║"
    echo "║ 4. Share screenshot        ║"
    echo "║ 5. Exit                    ║"
    echo "╚════════════════════════════╝"
    echo ""
    read -p "Choice: " choice
}

share_text() {
    read -p "Enter text to share: " text
    echo "$text" | termux-share
    echo "Text shared!"
}

share_file() {
    read -p "Enter file path: " filepath
    if [ -f "$filepath" ]; then
        termux-share "$filepath"
        echo "File shared!"
    else
        echo "File not found!"
    fi
}

pick_and_share() {
    TEMP_FILE="$HOME/temp_share_file"
    echo "Select a file..."
    termux-storage-get "$TEMP_FILE"
    
    if [ -f "$TEMP_FILE" ]; then
        termux-share "$TEMP_FILE"
        rm "$TEMP_FILE"
        echo "File shared!"
    else
        echo "No file selected!"
    fi
}

share_screenshot() {
    SCREENSHOT="$HOME/screenshot.png"
    termux-camera-photo "$SCREENSHOT"
    
    if [ -f "$SCREENSHOT" ]; then
        termux-share -c "image/png" "$SCREENSHOT"
    fi
}

# Main loop
while true; do
    show_menu
    case $choice in
        1) share_text ;;
        2) share_file ;;
        3) pick_and_share ;;
        4) share_screenshot ;;
        5) exit 0 ;;
        *) echo "Invalid choice!" ;;
    esac
done
```

---

[SECTION 8: 15+ PRACTICAL EXAMPLES - 23:00 to 26:30]
─────────────────────────────────────────────────────────────────────────────

Ab 15+ practical examples ek saath dekhte hain:

[EXAMPLE 1: Pick Image and Share]

    termux-storage-get ~/image.jpg && termux-share -c "image/jpeg" ~/image.jpg

[EXAMPLE 2: Download and Share]

    termux-download "https://example.com/doc.pdf" && termux-share /sdcard/Download/doc.pdf

[EXAMPLE 3: Pick PDF and Analyze]

    termux-storage-get ~/doc.pdf
    pdftotext ~/doc.pdf - | head -50

[EXAMPLE 4: Batch Media Scan]

    for f in /sdcard/DCIM/Camera/*.jpg; do termux-media-scan "$f"; done

[EXAMPLE 5: Download Audio File]

    termux-download -d /sdcard/Music -t "song.mp3" "https://example.com/song.mp3"

[EXAMPLE 6: Share WiFi Password]

    termux-wifi-connectioninfo | jq -r '.ssid' | termux-share

[EXAMPLE 7: Share Contact]

    termux-contact-list | jq '.[] | select(.name | contains("John"))' | termux-share

[EXAMPLE 8: Pick and Compress]

    termux-storage-get ~/bigfile
    gzip ~/bigfile
    termux-share ~/bigfile.gz

[EXAMPLE 9: Download Video]

    termux-download -d /sdcard/Movies "https://example.com/video.mp4"

[EXAMPLE 10: Pick Multiple Files Loop]

    for i in 1 2 3; do
        termux-storage-get ~/file_$i
    done

[EXAMPLE 11: Share Command Output]

    ls -la ~ | termux-share

[EXAMPLE 12: Download and Scan]

    termux-download "https://example.com/photo.jpg"
    termux-media-scan /sdcard/Download/photo.jpg

[EXAMPLE 13: Pick JSON and Parse]

    termux-storage-get ~/data.json
    cat ~/data.json | jq '.'

[EXAMPLE 14: Share Device Info]

    (termux-battery-status; termux-telephony-deviceinfo) | termux-share

[EXAMPLE 15: Download to Custom Folder]

    mkdir -p /sdcard/Documents/Work
    termux-download -d /sdcard/Documents/Work "https://example.com/report.pdf"

---

[SECTION 9: SUMMARY - 26:30 to 28:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 17 complete! Let's summarize:

✅ termux-storage-get - File picker dialog
✅ termux-share - Share files and text
✅ termux-download - Download files from URL
✅ termux-media-scan - Make files visible in gallery
✅ Python integration for automation
✅ Bash scripts for practical use cases

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 17 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ termux-storage-get ~/file       │ Pick file from Android               │
│ termux-share file.txt           │ Share file to other apps             │
│ echo "text" | termux-share      │ Share text to other apps            │
│ termux-download URL             │ Download file from URL              │
│ termux-download -d /path URL    │ Download to specific folder         │
│ termux-media-scan /sdcard/f.jpg │ Make file visible in gallery        │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter mein hum seekhenge:
- Device Information APIs
- Telephony APIs
- SIM and Network info

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 18!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. File Operation APIs Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                TERMUX FILE OPERATIONS ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Termux Terminal                               │   │
│   │                                                                  │   │
│   │   $ termux-storage-get ~/file       (File Picker)               │   │
│   │   $ termux-share document.pdf       (Share Intent)              │   │
│   │   $ termux-download URL             (Download Manager)          │   │
│   │   $ termux-media-scan /sdcard/f.jpg (Media Scanner)             │   │
│   │                                                                  │   │
│   └────────────────────────────┬────────────────────────────────────┘   │
│                                │                                         │
│                                │ Broadcast Intent                        │
│                                ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                   Termux:API Application                         │   │
│   │                                                                  │   │
│   │   ┌───────────────┐  ┌───────────────┐  ┌───────────────┐       │   │
│   │   │ Storage       │  │ Share         │  │ Download      │       │   │
│   │   │ Access        │  │ Intent        │  │ Manager       │       │   │
│   │   │ Framework     │  │ Service       │  │ Service       │       │   │
│   │   └───────┬───────┘  └───────┬───────┘  └───────┬───────┘       │   │
│   │           │                  │                  │                │   │
│   └───────────┼──────────────────┼──────────────────┼────────────────┘   │
│               │                  │                  │                     │
│               ▼                  ▼                  ▼                     │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                   Android System Services                        │   │
│   │                                                                  │   │
│   │   Storage Access Framework │ Share Sheet │ Download Manager      │   │
│   │   MediaStore           │ Intent System   │ Notification Manager  │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Storage Paths Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX STORAGE PATHS                                  │
├──────────────────────────────┬──────────────────────────────────────────┤
│ Path                         │ Description                              │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~ or $HOME                   │ Termux home directory                    │
│                              │ /data/data/com.termux/files/home         │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~/storage/shared             │ Internal storage root                    │
│                              │ Same as /sdcard                          │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~/storage/downloads          │ Download folder                          │
│                              │ /sdcard/Download                         │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~/storage/dcim               │ Camera photos                            │
│                              │ /sdcard/DCIM                             │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~/storage/pictures           │ Pictures folder                          │
│                              │ /sdcard/Pictures                         │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~/storage/music              │ Music folder                             │
│                              │ /sdcard/Music                            │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~/storage/movies             │ Movies folder                            │
│                              │ /sdcard/Movies                           │
├──────────────────────────────┼──────────────────────────────────────────┤
│ ~/storage/documents          │ Documents folder                         │
│                              │ /sdcard/Documents                        │
└──────────────────────────────┴──────────────────────────────────────────┘
```

### 3. MIME Types Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON MIME TYPES FOR SHARING                         │
├──────────────────────────────┬──────────────────────────────────────────┤
│ MIME Type                    │ File Type                                │
├──────────────────────────────┼──────────────────────────────────────────┤
│ text/plain                   │ Plain text files                         │
│ text/html                    │ HTML files                               │
│ text/csv                     │ CSV data files                           │
│ application/pdf              │ PDF documents                            │
│ application/json             │ JSON files                               │
│ application/xml              │ XML files                                │
│ application/zip              │ ZIP archives                             │
│ application/x-tar            │ TAR archives                             │
│ application/x-gzip           │ GZIP archives                            │
│ image/jpeg                   │ JPEG images                              │
│ image/png                    │ PNG images                               │
│ image/gif                    │ GIF images                               │
│ image/webp                   │ WebP images                              │
│ image/svg+xml                │ SVG images                               │
│ video/mp4                    │ MP4 videos                               │
│ video/webm                   │ WebM videos                              │
│ audio/mpeg                   │ MP3 audio                                │
│ audio/wav                    │ WAV audio                                │
│ audio/ogg                    │ OGG audio                                │
│ audio/mp4                    │ M4A audio                                │
└──────────────────────────────┴──────────────────────────────────────────┘
```

### 4. Download Manager Integration

```
┌─────────────────────────────────────────────────────────────────────────┐
│                ANDROID DOWNLOAD MANAGER FEATURES                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✓ Background Downloads                                                 │
│    - Downloads continue even if Termux is closed                        │
│    - Survives app termination                                           │
│                                                                          │
│  ✓ Automatic Resume                                                     │
│    - Resumes interrupted downloads                                      │
│    - Handles network changes                                            │
│                                                                          │
│  ✓ Progress Notification                                                │
│    - Shows download progress                                            │
│    - Click to open downloaded file                                      │
│                                                                          │
│  ✓ WiFi Only Option                                                     │
│    - Can be configured for WiFi only                                    │
│    - Saves mobile data                                                  │
│                                                                          │
│  ✓ File Type Detection                                                  │
│    - Automatic MIME type detection                                      │
│    - Proper file associations                                           │
│                                                                          │
│  ✓ Media Scanner Integration                                            │
│    - Automatically scans downloaded files                               │
│    - Makes files visible in Gallery                                     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### termux-storage-get

```bash
# Basic usage - pick any file
termux-storage-get ~/destination_file

# Pick and rename
termux-storage-get ~/my_document.pdf

# Pick image
termux-storage-get ~/image.jpg

# Pick to specific location
termux-storage-get ~/storage/downloads/picked_file

# Use in script with error handling
if termux-storage-get ~/selected_file; then
    echo "File selected successfully"
    echo "Size: $(stat -c%s ~/selected_file) bytes"
else
    echo "No file selected or error occurred"
fi
```

### termux-share

```bash
# Share file
termux-share ~/document.pdf

# Share with MIME type
termux-share -c "image/jpeg" ~/photo.jpg
termux-share -c "application/pdf" ~/report.pdf
termux-share -c "text/plain" ~/notes.txt

# Share with action
termux-share -a view ~/image.jpg      # View in gallery
termux-share -a edit ~/document.txt   # Open for editing
termux-share -a send ~/file.zip       # Send (default)

# Share text directly
echo "Hello from Termux" | termux-share

# Share command output
ls -la | termux-share
cat /proc/cpuinfo | termux-share

# Share JSON data
termux-battery-status | termux-share

# Use default app directly
termux-share -d ~/photo.jpg

# Share with title
termux-share -t "My Photo" ~/photo.jpg

# Combine options
termux-share -a view -c "image/png" -t "Screenshot" ~/screenshot.png
```

### termux-download

```bash
# Basic download
termux-download "https://example.com/file.pdf"

# Download to specific folder
termux-download -d /sdcard/Documents "https://example.com/doc.pdf"

# Download with custom title
termux-download -t "My Document" "https://example.com/file.pdf"

# Download with description
termux-download -r "Important report" "https://example.com/report.pdf"

# Download to Pictures
termux-download -d /sdcard/Pictures "https://example.com/image.jpg"

# Download to Music
termux-download -d /sdcard/Music "https://example.com/song.mp3"

# Download multiple files
termux-download "https://example.com/file1.pdf"
termux-download "https://example.com/file2.pdf"

# Download with all options
termux-download -d /sdcard/Download -t "Important" -r "Work document" "https://example.com/doc.pdf"
```

### termux-media-scan

```bash
# Scan single file
termux-media-scan /sdcard/DCIM/photo.jpg

# Scan video
termux-media-scan /sdcard/Movies/video.mp4

# Scan audio
termux-media-scan /sdcard/Music/song.mp3

# Scan multiple files with wildcard
termux-media-scan /sdcard/DCIM/Camera/*.jpg
termux-media-scan /sdcard/Download/*.pdf

# Scan all in directory
for f in /sdcard/Pictures/*; do
    termux-media-scan "$f"
done

# Scan recursively
find /sdcard/DCIM -name "*.jpg" -exec termux-media-scan {} \;

# Scan from script
wget -O /sdcard/DCIM/downloaded.jpg "https://example.com/photo.jpg"
termux-media-scan /sdcard/DCIM/downloaded.jpg
```

### Combined Operations

```bash
# Pick, process, share
termux-storage-get ~/input.txt
cat ~/input.txt | sort | uniq > ~/output.txt
termux-share ~/output.txt

# Download and scan
termux-download -d /sdcard/DCIM "https://example.com/photo.jpg"
termux-media-scan /sdcard/DCIM/photo.jpg

# Pick and upload (conceptual)
termux-storage-get ~/file_to_share.txt
termux-share -a send ~/file_to_share.txt

# Download and share
termux-download "https://example.com/doc.pdf"
termux-share /sdcard/Download/doc.pdf

# Create, scan, share
echo "Important note" > /sdcard/Download/note.txt
termux-media-scan /sdcard/Download/note.txt
termux-share /sdcard/Download/note.txt
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: File Picker Practice

```bash
# Task: Use file picker to select and analyze files

# Step 1: Pick a text file
termux-storage-get ~/my_text.txt

# Step 2: Check if file exists
if [ -f ~/my_text.txt ]; then
    echo "File picked successfully!"
    
    # Step 3: Display file info
    echo "Size: $(wc -c < ~/my_text.txt) bytes"
    echo "Lines: $(wc -l < ~/my_text.txt)"
    echo "Words: $(wc -w < ~/my_text.txt)"
    
    # Step 4: Show first 10 lines
    echo "First 10 lines:"
    head -10 ~/my_text.txt
else
    echo "No file selected"
fi
```

### Exercise 2: Download and Organize

```bash
# Task: Create a download organizer script

cat > ~/download_organizer.sh << 'EOF'
#!/bin/bash

# Configuration
BASE_DIR="/sdcard/Downloads/Organized"

organize_download() {
    url="$1"
    filename=$(basename "$url" | cut -d'?' -f1)
    
    # Determine folder by extension
    ext="${filename##*.}"
    ext=$(echo "$ext" | tr '[:upper:]' '[:lower:]')
    
    case $ext in
        jpg|jpeg|png|gif|webp)
            folder="$BASE_DIR/Images"
            ;;
        mp4|mkv|avi|webm)
            folder="$BASE_DIR/Videos"
            ;;
        mp3|wav|flac|m4a)
            folder="$BASE_DIR/Audio"
            ;;
        pdf)
            folder="$BASE_DIR/Documents"
            ;;
        zip|tar|gz|rar)
            folder="$BASE_DIR/Archives"
            ;;
        *)
            folder="$BASE_DIR/Other"
            ;;
    esac
    
    mkdir -p "$folder"
    termux-download -d "$folder" -t "$filename" "$url"
    echo "Downloaded to: $folder/$filename"
}

# Main
if [ -z "$1" ]; then
    echo "Usage: $0 <URL>"
    exit 1
fi

organize_download "$1"
EOF

chmod +x ~/download_organizer.sh
```

### Exercise 3: Media Scanner Batch

```bash
# Task: Create a script to scan all media in a folder

cat > ~/scan_media.sh << 'EOF'
#!/bin/bash

TARGET_DIR="${1:-/sdcard/DCIM/Camera}"
count=0
failed=0

echo "Scanning media in: $TARGET_DIR"
echo "================================"

for file in "$TARGET_DIR"/*; do
    if [ -f "$file" ]; then
        # Check if it's a media file
        case "$file" in
            *.jpg|*.jpeg|*.png|*.gif|*.webp|*.bmp)
                termux-media-scan "$file" 2>/dev/null
                if [ $? -eq 0 ]; then
                    count=$((count + 1))
                    echo "✓ Scanned: $(basename "$file")"
                else
                    failed=$((failed + 1))
                    echo "✗ Failed: $(basename "$file")"
                fi
                ;;
            *.mp4|*.mkv|*.avi|*.webm|*.mov)
                termux-media-scan "$file" 2>/dev/null
                if [ $? -eq 0 ]; then
                    count=$((count + 1))
                    echo "✓ Scanned: $(basename "$file")"
                else
                    failed=$((failed + 1))
                    echo "✗ Failed: $(basename "$file")"
                fi
                ;;
            *.mp3|*.wav|*.flac|*.m4a|*.ogg)
                termux-media-scan "$file" 2>/dev/null
                if [ $? -eq 0 ]; then
                    count=$((count + 1))
                    echo "✓ Scanned: $(basename "$file")"
                else
                    failed=$((failed + 1))
                    echo "✗ Failed: $(basename "$file")"
                fi
                ;;
        esac
    fi
done

echo ""
echo "================================"
echo "Scan Complete!"
echo "Successfully scanned: $count"
echo "Failed: $failed"
EOF

chmod +x ~/scan_media.sh
```

### Exercise 4: Share Utility

```bash
# Task: Create a comprehensive share utility

cat > ~/quick_share.sh << 'EOF'
#!/bin/bash

show_usage() {
    echo "Quick Share Utility"
    echo "==================="
    echo ""
    echo "Usage:"
    echo "  $0 file <path>     - Share a file"
    echo "  $0 text <message>  - Share text"
    echo "  $0 pick            - Pick and share file"
    echo "  $0 cmd <command>   - Share command output"
    echo ""
    echo "Examples:"
    echo "  $0 file ~/document.pdf"
    echo "  $0 text 'Hello World'"
    echo "  $0 pick"
    echo "  $0 cmd 'ls -la'"
}

share_file() {
    local file="$1"
    if [ ! -f "$file" ]; then
        echo "Error: File not found - $file"
        return 1
    fi
    
    # Auto-detect MIME type
    local ext="${file##*.}"
    local mime=""
    
    case "${ext,,}" in
        jpg|jpeg) mime="image/jpeg" ;;
        png) mime="image/png" ;;
        gif) mime="image/gif" ;;
        pdf) mime="application/pdf" ;;
        txt) mime="text/plain" ;;
        json) mime="application/json" ;;
        mp4) mime="video/mp4" ;;
        mp3) mime="audio/mpeg" ;;
        zip) mime="application/zip" ;;
    esac
    
    if [ -n "$mime" ]; then
        termux-share -c "$mime" "$file"
    else
        termux-share "$file"
    fi
    
    echo "Shared: $file"
}

share_text() {
    echo "$1" | termux-share
    echo "Text shared!"
}

pick_and_share() {
    local temp_file="$HOME/temp_share_$$"
    echo "Select a file to share..."
    
    if termux-storage-get "$temp_file"; then
        share_file "$temp_file"
        rm -f "$temp_file"
    else
        echo "No file selected"
    fi
}

share_command() {
    local cmd="$1"
    echo "Running: $cmd"
    eval "$cmd" | termux-share
    echo "Command output shared!"
}

# Main
case "$1" in
    file)
        [ -z "$2" ] && { show_usage; exit 1; }
        share_file "$2"
        ;;
    text)
        [ -z "$2" ] && { show_usage; exit 1; }
        share_text "$2"
        ;;
    pick)
        pick_and_share
        ;;
    cmd)
        [ -z "$2" ] && { show_usage; exit 1; }
        share_command "$2"
        ;;
    *)
        show_usage
        ;;
esac
EOF

chmod +x ~/quick_share.sh
```

### Exercise 5: Python File Manager

```python
#!/usr/bin/env python3
# file_manager.py - Termux File Manager with API integration

import subprocess
import os
import json
import sys
from pathlib import Path

class TermuxFileManager:
    """File manager using Termux API"""
    
    def __init__(self):
        self.home = Path.home()
        self.download_dir = Path("/sdcard/Download")
        self.pictures_dir = Path("/sdcard/Pictures")
        self.music_dir = Path("/sdcard/Music")
    
    def run_api(self, command, *args):
        """Run Termux API command"""
        cmd = [command] + list(args)
        result = subprocess.run(cmd, capture_output=True, text=True)
        return result.returncode == 0, result.stdout, result.stderr
    
    def pick_file(self, dest_name="picked_file"):
        """Open file picker and save to home"""
        dest = self.home / dest_name
        success, _, _ = self.run_api('termux-storage-get', str(dest))
        return str(dest) if success else None
    
    def download(self, url, dest_dir=None, title=None):
        """Download file from URL"""
        dest = dest_dir or str(self.download_dir)
        args = ['-d', dest]
        if title:
            args.extend(['-t', title])
        args.append(url)
        success, _, _ = self.run_api('termux-download', *args)
        return success
    
    def share(self, path, mime_type=None, action='send'):
        """Share file"""
        args = ['-a', action]
        if mime_type:
            args.extend(['-c', mime_type])
        args.append(path)
        success, _, _ = self.run_api('termux-share', *args)
        return success
    
    def share_text(self, text):
        """Share text"""
        success, _, _ = self.run_api('termux-share', input=text.encode())
        return success
    
    def scan_media(self, path):
        """Scan file for media gallery"""
        success, _, _ = self.run_api('termux-media-scan', path)
        return success
    
    def scan_directory(self, directory, extensions=None):
        """Scan all media files in directory"""
        extensions = extensions or ['.jpg', '.jpeg', '.png', '.gif', 
                                    '.mp4', '.mp3', '.wav']
        count = 0
        for root, dirs, files in os.walk(directory):
            for file in files:
                if any(file.lower().endswith(ext) for ext in extensions):
                    filepath = os.path.join(root, file)
                    if self.scan_media(filepath):
                        count += 1
                        print(f"Scanned: {file}")
        return count
    
    def get_file_info(self, path):
        """Get file information"""
        path = Path(path)
        if not path.exists():
            return None
        
        stat = path.stat()
        return {
            'name': path.name,
            'path': str(path.absolute()),
            'size': stat.st_size,
            'size_human': self._human_size(stat.st_size),
            'modified': stat.st_mtime,
            'is_file': path.is_file(),
            'is_dir': path.is_dir(),
            'extension': path.suffix.lower()
        }
    
    def _human_size(self, size):
        """Convert bytes to human readable"""
        for unit in ['B', 'KB', 'MB', 'GB', 'TB']:
            if size < 1024:
                return f"{size:.2f} {unit}"
            size /= 1024
        return f"{size:.2f} PB"
    
    def interactive_menu(self):
        """Interactive file manager menu"""
        while True:
            print("\n" + "="*40)
            print("     TERMUX FILE MANAGER")
            print("="*40)
            print("1. Pick File")
            print("2. Download File")
            print("3. Share File")
            print("4. Share Text")
            print("5. Scan Media")
            print("6. File Info")
            print("7. Exit")
            print("="*40)
            
            choice = input("\nEnter choice: ").strip()
            
            if choice == '1':
                name = input("Destination name: ").strip() or "picked_file"
                result = self.pick_file(name)
                if result:
                    print(f"File saved to: {result}")
                    info = self.get_file_info(result)
                    if info:
                        print(f"Size: {info['size_human']}")
                else:
                    print("No file selected")
            
            elif choice == '2':
                url = input("Enter URL: ").strip()
                if url:
                    dest = input("Destination folder (leave empty for Download): ").strip()
                    title = input("Title (optional): ").strip()
                    if self.download(url, dest or None, title or None):
                        print("Download started!")
                    else:
                        print("Download failed")
            
            elif choice == '3':
                path = input("Enter file path: ").strip()
                if os.path.exists(path):
                    mime = input("MIME type (optional): ").strip()
                    if self.share(path, mime or None):
                        print("Shared!")
                    else:
                        print("Share failed")
                else:
                    print("File not found")
            
            elif choice == '4':
                text = input("Enter text to share: ").strip()
                if text and self.share_text(text):
                    print("Text shared!")
            
            elif choice == '5':
                path = input("Enter directory path: ").strip()
                if os.path.isdir(path):
                    count = self.scan_directory(path)
                    print(f"Scanned {count} files")
                else:
                    print("Directory not found")
            
            elif choice == '6':
                path = input("Enter file path: ").strip()
                info = self.get_file_info(path)
                if info:
                    print(json.dumps(info, indent=2))
                else:
                    print("File not found")
            
            elif choice == '7':
                print("Goodbye!")
                break
            
            else:
                print("Invalid choice")

if __name__ == "__main__":
    fm = TermuxFileManager()
    
    if len(sys.argv) > 1:
        # Command line mode
        if sys.argv[1] == 'pick':
            result = fm.pick_file(sys.argv[2] if len(sys.argv) > 2 else "file")
            print(result or "cancelled")
        elif sys.argv[1] == 'download':
            fm.download(sys.argv[2])
        elif sys.argv[1] == 'share':
            fm.share(sys.argv[2])
        elif sys.argv[1] == 'scan':
            fm.scan_media(sys.argv[2])
    else:
        # Interactive mode
        fm.interactive_menu()
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "termux-storage-get: command not found"

```bash
# Cause: termux-api package not installed

# Solution:
pkg install termux-api -y

# Also ensure Termux:API app is installed from F-Droid
```

### Problem 2: File picker doesn't open

```bash
# Cause: Storage permission not granted

# Solution 1: Grant storage permission
termux-setup-storage

# Solution 2: Manual permission
# Settings → Apps → Termux:API → Permissions
# Enable: Storage / Files and Media

# Solution 3: Check if Termux:API app is installed
pm list packages | grep termux.api
```

### Problem 3: Download not starting

```bash
# Cause: Invalid URL or network issue

# Solution 1: Test URL manually
curl -I "YOUR_URL_HERE"

# Solution 2: Check internet connection
ping -c 3 google.com

# Solution 3: Verify URL format (must be direct download link)
# Good: https://example.com/file.pdf
# May not work: https://drive.google.com/file/d/xyz/view
```

### Problem 4: Files not appearing in Gallery

```bash
# Cause: Media scanner not triggered

# Solution: Manually scan files
termux-media-scan /sdcard/DCIM/your_file.jpg

# For multiple files:
for f in /sdcard/DCIM/Camera/*.jpg; do
    termux-media-scan "$f"
done

# Alternative: Restart phone (forces full media scan)
```

### Problem 5: Share dialog shows wrong apps

```bash
# Cause: Incorrect MIME type

# Solution: Specify correct MIME type
termux-share -c "image/jpeg" photo.jpg
termux-share -c "application/pdf" document.pdf
termux-share -c "text/plain" notes.txt
```

### Problem 6: Permission denied on /sdcard

```bash
# Cause: Storage permission or scoped storage (Android 11+)

# Solution 1: Run setup
termux-setup-storage

# Solution 2: Use ~/storage/ paths
ls ~/storage/downloads  # Instead of /sdcard/Download

# Solution 3: For Android 11+, use Storage Access Framework
termux-storage-get ~/file  # This works even with scoped storage
```

### Problem 7: "Error: Termux:API app not installed"

```bash
# Cause: Termux:API app missing or incompatible

# Solution: Install from F-Droid (NOT Play Store)
# 1. Open F-Droid
# 2. Search "Termux:API"
# 3. Install

# Verify installation:
pm list packages | grep termux.api

# Should show: package:com.termux.api
```

### Problem 8: Download notification not showing

```bash
# Cause: Notification permission or Download Manager issue

# Solution 1: Check notification permission
# Settings → Apps → Termux:API → Notifications → Enable

# Solution 2: Check Download Manager
# Settings → Apps → Download Manager → Enable

# Solution 3: Check downloads manually
ls /sdcard/Download/
```

### Problem 9: Large file operations timeout

```bash
# Cause: Operation takes too long

# Solution: Use background operations
termux-download "URL" &
disown

# For file copying:
cp /sdcard/large_file ~/large_file &
wait
```

### Problem 10: Share fails with certain apps

```bash
# Cause: App doesn't support the file type or share intent

# Solution 1: Try with explicit MIME type
termux-share -c "image/jpeg" photo.jpg

# Solution 2: Use 'view' action instead of 'send'
termux-share -a view photo.jpg

# Solution 3: Check if target app is installed
pm list packages | grep target_app
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📁 TERMUX FILE OPERATIONS        │
│                                    │
│   ✓ Pick Files                     │
│   ✓ Share Files                    │
│   ✓ Download Files                 │
│   ✓ Media Scan                     │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Action Style**
```
┌────────────────────────────────────┐
│  📥 DOWNLOAD | 📤 SHARE | 📂 PICK  │
│                                    │
│   TERMUX API FILE OPS              │
│                                    │
│   Complete Tutorial                │
│   No Root Required!                │
│                                    │
│   Chapter 17 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Problem-Solution**
```
┌────────────────────────────────────┐
│  ❌ Gallery not showing files?     │
│                                    │
│  ✅ termux-media-scan FIX!         │
│                                    │
│  FILE OPERATIONS API               │
│  Pick • Share • Download           │
│                                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📁 Termux Full Course - Chapter 17: File Operations API | Complete Guide

🔥 In this video you'll learn:
• termux-storage-get - File picker dialog
• termux-share - Share files and text
• termux-download - Download from URL
• termux-media-scan - Gallery visibility
• Python integration for automation
• 15+ practical examples

⏱️ Timestamps:
0:00 - Introduction
0:50 - File Operations Overview
3:00 - Storage Get (File Picker)
6:30 - Share API (Files & Text)
10:00 - Download API (URL Downloads)
14:00 - Media Scan (Gallery)
17:00 - Python Integration
20:00 - Bash Script Examples
23:00 - 15+ Practical Examples
26:30 - Summary

📝 Commands from this video:
termux-storage-get ~/file
termux-share document.pdf
termux-download "https://example.com/file"
termux-media-scan /sdcard/photo.jpg

💻 Scripts:
GitHub: [LINK]

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxAPI #FileOperations #TermuxCourse #T3rmuxk1ng #TermuxHindi #AndroidAutomation

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux, termux api, termux file operations, termux storage get,
termux share, termux download, termux media scan, termux file picker,
termux tutorial, termux course, termux hindi, termux api tutorial,
android file operations, termux automation, termux scripting,
termux python, termux bash, t3rmuxk1ng, termux for beginners,
android automation, termux commands
```

### Hashtags

```
#Termux #TermuxAPI #TermuxFileOperations #TermuxTutorial #TermuxHindi
#AndroidAutomation #TermuxCourse #T3rmuxk1ng #TermuxDownload 
#TermuxShare #LearnTermux #TermuxScripting
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux API Wiki | https://wiki.termux.com/wiki/Termux:API |
| Termux API GitHub | https://github.com/termux/termux-api |
| Android SAF | https://developer.android.com/guide/topics/providers/document-provider |
| Android DownloadManager | https://developer.android.com/reference/android/app/DownloadManager |

### Related Commands

| Command | Description |
|---------|-------------|
| `termux-setup-storage` | Grant storage permission |
| `termux-clipboard-get` | Get clipboard text |
| `termux-clipboard-set` | Set clipboard text |
| `termux-notification` | Create notifications |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 18, verify:

- [ ] termux-api package installed
- [ ] Termux:API app installed from F-Droid
- [ ] Storage permission granted (`termux-setup-storage`)
- [ ] Tested `termux-storage-get` - file picker works
- [ ] Tested `termux-share` - sharing works
- [ ] Tested `termux-download` - downloads work
- [ ] Tested `termux-media-scan` - files appear in Gallery
- [ ] Created at least one automation script
- [ ] Understood MIME types for sharing

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 18: Device Info APIs**

- termux-battery-status
- termux-telephony-deviceinfo
- termux-telephony-cellinfo
- termux-wifi-connectioninfo
- termux-wifi-scaninfo
- termux-sensor
- Hardware information APIs
- JSON parsing techniques

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
