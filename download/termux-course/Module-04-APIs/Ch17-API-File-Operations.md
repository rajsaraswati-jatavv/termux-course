# 📁 Chapter 17: Termux API - File Operations

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ████████╗███████╗██████╗ ███╗   ███╗██╗███╗   ██╗ █████╗ ██╗               ║
║   ╚══██╔══╝██╔════╝██╔══██╗████╗ ████║██║████╗  ██║██╔══██╗██║               ║
║      ██║   █████╗  ██████╔╝██╔████╔██║██║██╔██╗ ██║███████║██║               ║
║      ██║   ██╔══╝  ██╔══██╗██║╚██╔╝██║██║██║╚██╗██║██╔══██║██║               ║
║      ██║   ███████╗██║  ██║██║ ╚═╝ ██║██║██║ ╚████║██║  ██║███████╗          ║
║      ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝╚═╝  ╚═══╝╚═╝  ╚═╝╚══════╝          ║
║                                                                              ║
║   ██████╗  █████╗ ██████╗ ██╗  ██╗███╗   ██╗███████╗                         ║
║   ██╔══██╗██╔══██╗██╔══██╗██║ ██╔╝████╗  ██║██╔════╝                         ║
║   ██████╔╝███████║██████╔╝█████╔╝ ██╔██╗ ██║█████╗                           ║
║   ██╔══██╗██╔══██║██╔══██╗██╔═██╗ ██║╚██╗██║██╔══╝                           ║
║   ██║  ██║██║  ██║██║  ██║██║  ██╗██║ ╚████║███████╗                         ║
║   ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═══╝╚══════╝                         ║
║                                                                              ║
║                    📂 FILE OPERATIONS CHAPTER 📂                             ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 4 - APIs  
> **Chapter:** 17 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  
> **Prerequisites:** Chapters 1-16 (Basic Termux Setup)

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

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always use `termux-setup-storage` before any file operation to ensure proper permissions. Without this, many operations will fail silently.

> 💡 **Pro Tip #2:** Use `termux-storage-get` with a timestamped filename to avoid overwriting previous picks: `termux-storage-get ~/picked_$(date +%s).file`

> 💡 **Pro Tip #3:** When sharing files programmatically, always specify the MIME type with `-c` flag for better app compatibility: `termux-share -c "application/pdf" report.pdf`

> 💡 **Pro Tip #4:** Combine `termux-download` with `termux-media-scan` in a script to automatically make downloaded files visible in the gallery.

> 💡 **Pro Tip #5:** Use `--title` in `termux-download` to make notifications more informative and track downloads easily.

> 💡 **Pro Tip #6:** For batch file operations, use Python's `subprocess` module instead of bash loops - it's more reliable and easier to debug.

> 💡 **Pro Tip #7:** Create a file picker wrapper function that validates file existence before returning: saves debugging time in complex scripts.

> 💡 **Pro Tip #8:** Use `termux-share -d` (default) to bypass the share dialog and send directly to the default app for that file type.

> 💡 **Pro Tip #9:** For large downloads, check available storage first with `df -h ~/storage/downloads` to avoid failed downloads.

> 💡 **Pro Tip #10:** Store common MIME types in variables for cleaner scripts: `PDF="application/pdf"`, `JPG="image/jpeg"`, etc.

---

## 🔥 REAL WORLD APPLICATIONS

### 1. Automated Backup System
Create scheduled backups of important files to cloud storage or email them automatically.

```bash
#!/bin/bash
# Auto-backup script
BACKUP_FILE="backup_$(date +%Y%m%d).tar.gz"
tar -czf ~/$BACKUP_FILE ~/important_data/
termux-share -c "application/gzip" ~/$BACKUP_FILE
```

### 2. Photo Organizer Script
Scan photos, organize by date, and share the organized folder info.

```bash
#!/bin/bash
# Photo organizer using file APIs
termux-storage-get ~/photo.jpg
# Process and organize
termux-media-scan ~/photo.jpg
termux-share ~/photo.jpg
```

### 3. Document Workflow Automation
Download documents from URLs, process them, and share via preferred app.

```bash
#!/bin/bash
# Document workflow
termux-download -d ~/storage/downloads "$DOC_URL"
termux-storage-get ~/processed_doc.pdf
termux-share -c "application/pdf" ~/processed_doc.pdf
```

### 4. Media Gallery Sync Script
Automatically scan and register new media files to appear in gallery apps.

```bash
#!/bin/bash
for f in ~/storage/downloads/*.{jpg,png,mp4}; do
    termux-media-scan "$f" 2>/dev/null
done
echo "Gallery sync complete!"
```

### 5. Bulk File Picker & Share Tool
Select multiple files and share them together with a single command.

```bash
#!/bin/bash
FILES=()
for i in {1..5}; do
    termux-storage-get ~/temp_file_$i
    FILES+=("~/temp_file_$i")
done
termux-share "${FILES[@]}"
```

---

## ⚡ QUICK REFERENCE CARD

| Command | Syntax | Purpose |
|---------|--------|---------|
| `termux-storage-get` | `termux-storage-get <dest_path>` | Open file picker, save to destination |
| `termux-share` | `termux-share [options] <file\|text>` | Share file/text via Android share sheet |
| `termux-download` | `termux-download [options] <url>` | Download file from URL |
| `termux-media-scan` | `termux-media-scan <path>` | Register media files in Android gallery |

### File Operation Options

| Option | Command | Description |
|--------|---------|-------------|
| `-c, --content-type` | share | MIME type (image/jpeg, application/pdf) |
| `-a, --action` | share | Action: send, view, edit |
| `-d, --path` | download | Destination folder |
| `-t, --title` | download | Notification title |
| `-r` | media-scan | Recursive scan |

### Common MIME Types

| File Type | MIME Type |
|-----------|-----------|
| JPEG Image | `image/jpeg` |
| PNG Image | `image/png` |
| PDF Document | `application/pdf` |
| Plain Text | `text/plain` |
| JSON | `application/json` |
| MP3 Audio | `audio/mpeg` |
| MP4 Video | `video/mp4` |

---

## 🏆 BONUS: AUTOMATION IDEAS

### Idea 1: Smart Download Manager
```bash
#!/bin/bash
# smart_download.sh - Download with progress and auto-share

URL="$1"
FILENAME=$(basename "$URL" | cut -d'?' -f1)
DEST="$HOME/downloads"

echo "Downloading: $FILENAME"
termux-download -d "$DEST" -t "$FILENAME" "$URL"

# Wait for download
sleep 5

# Scan for gallery if media
if [[ "$FILENAME" =~ \.(jpg|png|mp4|mp3)$ ]]; then
    termux-media-scan "$DEST/$FILENAME"
fi

# Ask to share
read -p "Share downloaded file? (y/n): " choice
[ "$choice" = "y" ] && termux-share "$DEST/$FILENAME"
```

### Idea 2: Clipboard to File Saver
```bash
#!/bin/bash
# Save clipboard content to timestamped file
CONTENT=$(termux-clipboard-get 2>/dev/null)
TIMESTAMP=$(date +%Y%m%d_%H%M%S)
echo "$CONTENT" > ~/notes/clip_$TIMESTAMP.txt
termux-toast "Saved to clip_$TIMESTAMP.txt"
```

### Idea 3: Batch Media Importer
```bash
#!/bin/bash
# Import and scan multiple media files
IMPORT_DIR=~/storage/dcim/Imported
mkdir -p "$IMPORT_DIR"

for i in {1..10}; do
    termux-storage-get "$IMPORT_DIR/file_$i"
    if [ -f "$IMPORT_DIR/file_$i" ]; then
        termux-media-scan "$IMPORT_DIR/file_$i"
        echo "Imported file $i"
    fi
done
```

---

## 📝 CHAPTER SUMMARY

### ✅ What You Learned

- **termux-storage-get**: Opens Android file picker and copies selected file to Termux
- **termux-share**: Shares files and text through Android's share sheet
- **termux-download**: Downloads files using Android's download manager with background support
- **termux-media-scan**: Registers files in Android's MediaStore for gallery visibility
- **MIME types**: How to specify content types for better app compatibility
- **Storage paths**: Termux home, shared storage, and special directories
- **Python integration**: Using subprocess to call Termux API commands
- **Bash scripting**: Practical scripts for file automation

### 🎯 Key Takeaways

1. Always run `termux-setup-storage` before file operations
2. Files get copied (not moved) when using `termux-storage-get`
3. Use MIME types for better share compatibility
4. `termux-download` works in background even if Termux closes
5. Always scan media files for gallery visibility
6. JSON output from APIs can be parsed with `jq` or Python

---

## 🎯 PRACTICAL PROJECTS

### Project 1: File Manager Dashboard
Create a complete file manager with pick, download, share, and scan features.

```bash
#!/bin/bash
# file_manager.sh - Complete file manager dashboard

show_menu() {
    clear
    echo "╔════════════════════════════════════════╗"
    echo "║      FILE MANAGER DASHBOARD            ║"
    echo "╠════════════════════════════════════════╣"
    echo "║ 1. Pick File                           ║"
    echo "║ 2. Download from URL                   ║"
    echo "║ 3. Share File                          ║"
    echo "║ 4. Scan Media Files                    ║"
    echo "║ 5. View Downloads                      ║"
    echo "║ 6. Exit                                ║"
    echo "╚════════════════════════════════════════╝"
}

pick_file() {
    termux-storage-get ~/picked_file
    ls -la ~/picked_file
}

download_file() {
    read -p "Enter URL: " url
    termux-download "$url"
}

share_file() {
    read -p "Enter file path: " path
    termux-share "$path"
}

scan_media() {
    read -p "Enter directory: " dir
    find "$dir" -type f -exec termux-media-scan {} \;
}

view_downloads() {
    ls -la ~/storage/downloads/
}

while true; do
    show_menu
    read -p "Choice: " choice
    case $choice in
        1) pick_file ;;
        2) download_file ;;
        3) share_file ;;
        4) scan_media ;;
        5) view_downloads ;;
        6) exit 0 ;;
    esac
    read -p "Press Enter..."
done
```

### Project 2: Auto Photo Backup
Automatically pick photos and backup to a timestamped folder.

```bash
#!/bin/bash
# auto_backup.sh - Photo backup automation
BACKUP_DIR=~/storage/dcim/Backups/$(date +%Y%m%d)
mkdir -p "$BACKUP_DIR"

echo "Select photos to backup (3 files)..."
for i in {1..3}; do
    termux-storage-get "$BACKUP_DIR/photo_$i.jpg"
    termux-media-scan "$BACKUP_DIR/photo_$i.jpg"
done

echo "Backup complete in: $BACKUP_DIR"
termux-notification --title "Backup Complete" --content "Saved to $BACKUP_DIR"
```

---

## 🚀 INTEGRATION TIPS

### Combining File APIs with Other Termux APIs

**File + Notification Integration:**
```bash
# Download with notification
termux-download "$URL" && \
termux-notification --title "Download Complete" --content "File saved"
```

**File + Share + Contacts:**
```bash
# Pick file, share via SMS
termux-storage-get ~/doc.pdf
NUMBER=$(termux-contact-list | jq -r '.[0].number')
# Then manually share or use intent
```

**File + Battery Check:**
```bash
# Only download if battery > 20%
BATTERY=$(termux-battery-status | jq -r '.percentage')
if [ "$BATTERY" -gt 20 ]; then
    termux-download "$URL"
else
    echo "Low battery, skipping download"
fi
```

**File + Location Tagging:**
```bash
# Pick photo and tag with location
termux-storage-get ~/photo.jpg
LOCATION=$(termux-location | jq -r '"\(.latitude), \(.longitude)"')
echo "Location: $LOCATION" > ~/photo_location.txt
```

---

## 📊 JSON OUTPUT GUIDE

### Parsing termux-storage-get Output
```bash
# Check if file was picked successfully
if [ -f ~/picked_file ]; then
    FILE_SIZE=$(stat -c %s ~/picked_file)
    FILE_TYPE=$(file -b ~/picked_file)
    echo "Size: $FILE_SIZE bytes, Type: $FILE_TYPE"
fi
```

### jq Examples for File Operations

```bash
# Parse file info (if API returns JSON)
termux-storage-get ~/file 2>&1 | jq '.' 

# Extract specific fields
cat file_info.json | jq -r '.path, .size'

# Process multiple files
ls -la *.json | jq -s '.[] | .filename'

# Combine with file commands
find . -name "*.json" -exec jq '.' {} \;
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relation |
|---------|-------|----------|
| Chapter 18 | Device Info APIs | Get device storage info before file ops |
| Chapter 19 | Camera & Media | Photos need media-scan after capture |
| Chapter 20 | Network APIs | Download files from URLs |
| Chapter 21 | Notifications | Notify on download completion |
| Chapter 22 | Contacts & SMS | Share files via SMS/contacts |
| Chapter 23 | Clipboard & Share | Share clipboard content as files |

---

## 🎮 INTERACTIVE QUIZ

### Test Your Knowledge!

**Q1.** What command opens Android's file picker?
- A) `termux-file-picker`
- B) `termux-storage-get`
- C) `termux-pick-file`
- D) `termux-file-select`

**Q2.** Which MIME type is correct for a PDF file?
- A) `text/pdf`
- B) `file/pdf`
- C) `application/pdf`
- D) `document/pdf`

**Q3.** What is the default download location for `termux-download`?
- A) `~/`
- B) `/sdcard/`
- C) `/sdcard/Download`
- D) `~/downloads`

**Q4.** Why would you use `termux-media-scan`?
- A) To scan for viruses
- B) To make files visible in gallery apps
- C) To reduce file size
- D) To encrypt files

**Q5.** Which flag sets the notification title for downloads?
- A) `--name`
- B) `--label`
- C) `--title`
- D) `--notification`

**Q6.** What happens if you don't specify a MIME type when sharing?
- A) Share fails
- B) Android guesses the type
- C) File is deleted
- D) Nothing happens

**Q7.** Which command would you use to share text directly?
- A) `echo "text" | termux-share`
- B) `termux-share-text "text"`
- C) `termux-share --text "text"`
- D) `termux-clipboard-set "text"`

**Q8.** What is the purpose of `termux-setup-storage`?
- A) Install storage drivers
- B) Grant storage permissions and create symlinks
- C) Format storage
- D) Mount external storage

**Q9.** Can `termux-download` continue if Termux is closed?
- A) No, it stops immediately
- B) Yes, it uses Android Download Manager
- C) Only with root
- D) Only on Android 10+

**Q10.** Which path is valid for `termux-storage-get` destination?
- A) `/sdcard/file.txt`
- B) `~/file.txt`
- C) `/data/data/com.termux/files/home/file.txt`
- D) Both B and C

**Q11.** How many buttons can a notification have?
- A) 1
- B) 2
- C) 3
- D) Unlimited

**Q12.** What does `-c 0` mean in `termux-camera-photo`?
- A) No compression
- B) Use camera ID 0 (back camera)
- C) Capture count 0
- D) Cancel capture

### Quiz Answers

1. **B** - `termux-storage-get` opens the file picker
2. **C** - `application/pdf` is the correct MIME type for PDFs
3. **C** - `/sdcard/Download` is the default download location
4. **B** - `termux-media-scan` registers files in MediaStore for gallery visibility
5. **C** - `--title` sets the notification title
6. **B** - Android attempts to guess the MIME type
7. **A** - Piped text to `termux-share` shares it directly
8. **B** - It grants storage permissions and creates storage symlinks
9. **B** - Uses Android Download Manager which runs independently
10. **D** - Both Termux home paths are valid
11. **C** - Maximum 3 buttons (button1, button2, button3)
12. **B** - `-c 0` selects camera ID 0 (typically back camera)

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Question 1: File Operations Security
**Q:** What security considerations should you keep in mind when using `termux-storage-get`?

<details>
<summary>📖 Show Answer</summary>

**Answer:** Key security considerations include:
1. **Permission Scope:** Only request storage permissions when needed
2. **File Validation:** Always verify file type and size before processing
3. **Sensitive Data:** Be cautious with user-selected files that may contain personal data
4. **Path Traversal:** Validate and sanitize file paths
5. **Temporary Files:** Clean up copied files after processing

```bash
# Example: Safe file handling
termux-storage-get ~/temp_file
FILE_TYPE=$(file -b ~/temp_file)
EXPECTED_TYPES="JPEG PDF PNG MP4"
if [[ ! " $EXPECTED_TYPES " =~ " $FILE_TYPE " ]]; then
    echo "Invalid file type"
    rm ~/temp_file
    exit 1
fi
```

**Follow-up:** How would you implement file type validation in a production script?
</details>

### Question 2: Download Manager Integration
**Q:** Explain how `termux-download` differs from using `wget` or `curl`.

<details>
<summary>📖 Show Answer</summary>

**Answer:** Key differences:

| Feature | termux-download | wget/curl |
|---------|-----------------|-----------|
| Background execution | ✅ Yes (Android Download Manager) | ❌ No (process-bound) |
| Resume support | ✅ Automatic | ✅ Manual (-c flag) |
| Notification | ✅ Built-in | ❌ Requires manual setup |
| Survives app kill | ✅ Yes | ❌ No |
| Progress tracking | ✅ System UI | ❌ Terminal only |

**Use Cases:**
- Use `termux-download` for user-facing downloads with progress
- Use `wget/curl` for programmatic downloads in scripts

**Follow-up:** When would you prefer `curl` over `termux-download`?
</details>

### Question 3: Media Scanner Implementation
**Q:** Why does Android require media scanning after file operations?

<details>
<summary>📖 Show Answer</summary>

**Answer:** Android's MediaStore is a content provider that indexes media files for:
- Gallery apps to display photos/videos
- Music players to find audio files
- Document viewers to list files

When files are created outside standard apps, they're not indexed. `termux-media-scan` triggers:
1. File metadata extraction
2. Database entry creation in MediaStore
3. Thumbnail generation
4. Notification to media apps

```bash
# Batch media scan implementation
for file in /sdcard/DCIM/Camera/*.jpg; do
    termux-media-scan "$file"
done
```

**Follow-up:** What happens if you don't run media-scan after creating a photo?
</details>

### Question 4: File Share Architecture
**Q:** Describe the data flow when using `termux-share` with a file.

<details>
<summary>📖 Show Answer</summary>

**Answer:** The flow involves:
```
Termux CLI → termux-share → Termux:API App → Android Intent System → Share Sheet → Target App
```

Steps:
1. Command reads file content
2. Creates a share Intent with URI
3. Android resolves capable apps via intent filters
4. User selects target app
5. Content is passed via ContentProvider or direct file access

**Key consideration:** Apps can only access files they have permission for. Use content:// URIs for secure sharing.

**Follow-up:** How would you share to a specific app programmatically?
</details>

### Question 5: Storage Access Framework
**Q:** How does Termux interact with Android's Storage Access Framework?

<details>
<summary>📖 Show Answer</summary>

**Answer:** `termux-storage-get` uses SAF which:
1. Opens system file picker UI
2. User selects file from any provider (Drive, local, etc.)
3. Returns a content:// URI to the app
4. App receives temporary read access
5. File is copied to specified destination

**Benefits:**
- Access files from cloud storage
- No need for broad storage permissions
- User has full control over file selection

**Limitations:**
- Cannot access files without user interaction
- Temporary access only
- File is copied, not moved

**Follow-up:** What are the implications of "copy vs move" in SAF?
</details>

### Question 6: Error Handling Best Practices
**Q:** Write a robust error handling pattern for file operations.

<details>
<summary>📖 Show Answer</summary>

**Answer:**
```bash
#!/bin/bash
safe_file_operation() {
    local dest="$1"
    local temp_file="/tmp/operation_$$"
    
    # Trap for cleanup on error
    trap 'rm -f "$temp_file" 2>/dev/null; exit 1' ERR INT TERM
    
    # Attempt file picker
    if ! termux-storage-get "$temp_file" 2>/dev/null; then
        echo "Error: User cancelled or no permission"
        return 1
    fi
    
    # Verify file exists and is readable
    if [[ ! -r "$temp_file" ]]; then
        echo "Error: Cannot read selected file"
        return 1
    fi
    
    # Check file size (prevent empty files)
    if [[ ! -s "$temp_file" ]]; then
        echo "Error: Selected file is empty"
        rm -f "$temp_file"
        return 1
    fi
    
    # Move to final destination
    if ! mv "$temp_file" "$dest"; then
        echo "Error: Cannot move file to destination"
        return 1
    fi
    
    # Cleanup trap
    trap - ERR INT TERM
    echo "Success: File saved to $dest"
    return 0
}
```

**Follow-up:** How would you add logging and retry logic?
</details>

### Question 7: MIME Type Handling
**Q:** Why is proper MIME type specification important when sharing files?

<details>
<summary>📖 Show Answer</summary>

**Answer:** MIME types determine:
1. **App filtering:** Which apps appear in share sheet
2. **Preview rendering:** How content is displayed
3. **Default action:** View vs edit vs send
4. **Security:** Prevents executing files as wrong type

```bash
# Correct MIME type examples
termux-share -c "image/jpeg" photo.jpg      # Opens in image viewers
termux-share -c "application/pdf" doc.pdf   # Opens in PDF readers
termux-share -c "text/plain" notes.txt      # Opens in text editors

# Wrong MIME type can cause issues
termux-share -c "application/octet-stream" photo.jpg  # May not open correctly
```

**Follow-up:** What happens if you specify wrong MIME type for a sensitive file?
</details>

### Question 8: Performance Optimization
**Q:** How would you optimize batch file operations in Termux?

<details>
<summary>📖 Show Answer</summary>

**Answer:**
```bash
# Parallel processing for media scanning
process_files_parallel() {
    local dir="$1"
    local jobs=4
    
    find "$dir" -type f \( -name "*.jpg" -o -name "*.png" -o -name "*.mp4" \) | \
    xargs -P $jobs -I {} termux-media-scan {}
}

# Memory-efficient batch download
batch_download() {
    local url_file="$1"
    local dest="/sdcard/Download"
    
    while IFS= read -r url; do
        # Download one at a time to avoid memory issues
        termux-download -d "$dest" "$url"
        
        # Small delay to prevent rate limiting
        sleep 0.5
    done < "$url_file"
}

# Use file descriptors for large files
exec 3< large_file.txt
while IFS= read -r -u 3 line; do
    process_line "$line"
done
exec 3<&-
```

**Follow-up:** What are the trade-offs between parallel and sequential processing?
</details>

### Question 9: Cross-Platform Considerations
**Q:** How do Android version differences affect file operations?

<details>
<summary>📖 Show Answer</summary>

**Answer:**

| Android Version | Storage Access | Key Differences |
|-----------------|----------------|-----------------|
| 9 and below | Direct storage access | Full /sdcard access |
| 10 | Scoped Storage | Limited to app directories |
| 11+ | Enhanced Scoped Storage | MANAGE_EXTERNAL_STORAGE required |
| 13+ | Photo Picker | System picker for media |

**Handling differences:**
```bash
# Check Android version
API_LEVEL=$(getprop ro.build.version.sdk)

if [ "$API_LEVEL" -ge 30 ]; then
    # Android 11+: Use SAF for most operations
    termux-storage-get ~/file
else
    # Older: Can access /sdcard directly
    cp /sdcard/file.txt ~/
fi
```

**Follow-up:** How would you write version-agnostic file operation code?
</details>

### Question 10: Integration Architecture
**Q:** Design a complete file management system using all Termux file APIs.

<details>
<summary>📖 Show Answer</summary>

**Answer:**
```bash
#!/bin/bash
# file_manager.sh - Complete file management system

class FileManager {
    # Pick and process file
    pick_file() {
        local dest="$1"
        termux-storage-get "$dest" && echo "File picked successfully"
    }
    
    # Download with progress
    download_file() {
        local url="$1"
        local dest="${2:-/sdcard/Download}"
        termux-download -d "$dest" "$url"
    }
    
    # Share to apps
    share_file() {
        local file="$1"
        local mime="$2"
        termux-share -c "$mime" "$file"
    }
    
    # Make visible in gallery
    register_media() {
        local file="$1"
        termux-media-scan "$file"
    }
    
    # Complete workflow
    workflow() {
        local url="$1"
        local filename=$(basename "$url")
        
        echo "Downloading $filename..."
        this.download_file "$url"
        
        echo "Registering in gallery..."
        this.register_media "/sdcard/Download/$filename"
        
        echo "Sharing..."
        this.share_file "/sdcard/Download/$filename" "application/octet-stream"
    }
}

# Usage
fm=new FileManager
fm.workflow "https://example.com/file.pdf"
```

**Follow-up:** How would you add error handling and logging to this system?
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Automated Backup System
```
╔══════════════════════════════════════════════════════════════════════════════╗
║                         🔄 AUTOMATED BACKUP SYSTEM                          ║
╠══════════════════════════════════════════════════════════════════════════════╣
║ Situation: Need to backup photos from DCIM to cloud storage weekly          ║
║                                                                              ║
║ Commands:                                                                    ║
║   # 1. Scan for new photos                                                   ║
║   termux-media-scan /sdcard/DCIM/Camera/                                     ║
║                                                                              ║
║   # 2. Create backup archive                                                 ║
║   tar -czf backup_$(date +%Y%m%d).tar.gz /sdcard/DCIM/Camera/*.jpg           ║
║                                                                              ║
║   # 3. Share to cloud app                                                    ║
║   termux-share -c "application/gzip" backup_*.tar.gz                         ║
║                                                                              ║
║ Automation: Run via cron weekly                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: Bulk Document Download
```
╔══════════════════════════════════════════════════════════════════════════════╗
║                        📥 BULK DOCUMENT DOWNLOADER                          ║
╠══════════════════════════════════════════════════════════════════════════════╣
║ Situation: Download 50 PDF documents from a list of URLs                    ║
║                                                                              ║
║ Commands:                                                                    ║
║   # Create download list file                                                ║
║   cat > urls.txt << EOF                                                      ║
║   https://example.com/doc1.pdf                                               ║
║   https://example.com/doc2.pdf                                               ║
║   EOF                                                                        ║
║                                                                              ║
║   # Batch download with progress                                             ║
║   while read url; do                                                         ║
║       echo "Downloading: $url"                                               ║
║       termux-download -d /sdcard/Documents "$url"                            ║
║       sleep 1                                                                ║
║   done < urls.txt                                                            ║
║                                                                              ║
║ Result: All PDFs in /sdcard/Documents with notifications                     ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: Photo Organization Pipeline
```
╔══════════════════════════════════════════════════════════════════════════════╗
║                       📷 PHOTO ORGANIZATION PIPELINE                        ║
╠══════════════════════════════════════════════════════════════════════════════╣
║ Situation: Organize photos by date and share selected ones                  ║
║                                                                              ║
║ Commands:                                                                    ║
║   # 1. Organize by date                                                      ║
║   for photo in /sdcard/DCIM/Camera/*.jpg; do                                 ║
║       date=$(stat -c %y "$photo" | cut -d' ' -f1)                           ║
║       mkdir -p "/sdcard/Pictures/$date"                                     ║
║       cp "$photo" "/sdcard/Pictures/$date/"                                  ║
║       termux-media-scan "/sdcard/Pictures/$date/$(basename $photo)"         ║
║   done                                                                       ║
║                                                                              ║
║   # 2. Share specific album                                                  ║
║   termux-share /sdcard/Pictures/2024-01-15/selected_photo.jpg               ║
║                                                                              ║
║ Result: Photos organized in dated folders, visible in gallery               ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: Secure File Transfer
```
╔══════════════════════════════════════════════════════════════════════════════╗
║                        🔐 SECURE FILE TRANSFER                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║ Situation: Securely transfer encrypted file to another device               ║
║                                                                              ║
║ Commands:                                                                    ║
║   # 1. Pick file to transfer                                                 ║
║   termux-storage-get ~/transfer_file                                        ║
║                                                                              ║
║   # 2. Encrypt the file                                                      ║
║   gpg -c ~/transfer_file                                                    ║
║                                                                              ║
║   # 3. Share encrypted file                                                  ║
║   termux-share -c "application/pgp-encrypted" ~/transfer_file.gpg          ║
║                                                                              ║
║   # 4. Clean up                                                              ║
║   rm ~/transfer_file ~/transfer_file.gpg                                    ║
║                                                                              ║
║ Result: Encrypted file shared securely, originals cleaned up                ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: Document Scanner Workflow
```
╔══════════════════════════════════════════════════════════════════════════════╗
║                       📄 DOCUMENT SCANNER WORKFLOW                          ║
╠══════════════════════════════════════════════════════════════════════════════╣
║ Situation: Capture, process, and share document photos                     ║
║                                                                              ║
║ Commands:                                                                    ║
║   # 1. Capture document photo                                                ║
║   termux-camera-photo -c 0 ~/document_scan.jpg                              ║
║                                                                              ║
║   # 2. Process with imagemagick                                              ║
║   convert ~/document_scan.jpg -deskew 40% -trim ~/document_processed.jpg    ║
║                                                                              ║
║   # 3. Register for gallery                                                  ║
║   termux-media-scan ~/document_processed.jpg                                ║
║                                                                              ║
║   # 4. Copy to documents folder                                              ║
║   cp ~/document_processed.jpg /sdcard/Documents/                            ║
║                                                                              ║
║   # 5. Share via email                                                       ║
║   termux-share -c "image/jpeg" ~/document_processed.jpg                     ║
║                                                                              ║
║ Result: Professional document scan ready for sharing                        ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: File Operations API Flow
```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    FILE OPERATIONS API ARCHITECTURE                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────┐                                                        │
│  │  User Command   │                                                        │
│  │  termux-*       │                                                        │
│  └────────┬────────┘                                                        │
│           │                                                                  │
│           ▼                                                                  │
│  ┌─────────────────────────────────────────────────────────────┐            │
│  │                    TERMUX:API BRIDGE                         │            │
│  │  ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐   │            │
│  │  │ Storage   │ │ Share     │ │ Download  │ │ Media     │   │            │
│  │  │ Access    │ │ Intent    │ │ Manager   │ │ Scanner   │   │            │
│  │  │ Framework │ │ Service   │ │ Service   │ │ Service   │   │            │
│  │  └─────┬─────┘ └─────┬─────┘ └─────┬─────┘ └─────┬─────┘   │            │
│  └────────┼─────────────┼─────────────┼─────────────┼─────────┘            │
│           │             │             │             │                       │
│           ▼             ▼             ▼             ▼                       │
│  ┌─────────────────────────────────────────────────────────────┐            │
│  │                    ANDROID SYSTEM SERVICES                   │            │
│  │                                                              │            │
│  │  ┌─────────────────┐    ┌─────────────────┐                 │            │
│  │  │ ContentProvider │    │ DownloadManager │                 │            │
│  │  │ (SAF)           │    │ (Background)    │                 │            │
│  │  └─────────────────┘    └─────────────────┘                 │            │
│  │                                                              │            │
│  │  ┌─────────────────┐    ┌─────────────────┐                 │            │
│  │  │ Intent System   │    │ MediaStore      │                 │            │
│  │  │ (Share Sheet)   │    │ (Gallery Index) │                 │            │
│  │  └─────────────────┘    └─────────────────┘                 │            │
│  └─────────────────────────────────────────────────────────────┘            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Download Flow
```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         DOWNLOAD OPERATION FLOW                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   User                Termux            Termux:API         Android DM       │
│     │                   │                   │                   │            │
│     │ termux-download   │                   │                   │            │
│     │──────────────────>│                   │                   │            │
│     │                   │                   │                   │            │
│     │                   │  Broadcast Intent │                   │            │
│     │                   │──────────────────>│                   │            │
│     │                   │                   │                   │            │
│     │                   │                   │  Enqueue Download │            │
│     │                   │                   │──────────────────>│            │
│     │                   │                   │                   │            │
│     │                   │                   │                   │ [Download │
│     │                   │                   │                   │  Progress]│
│     │                   │                   │                   │            │
│     │<──────────────────│                   │                   │            │
│     │  Command returns  │                   │                   │            │
│     │  immediately      │                   │                   │            │
│     │                   │                   │                   │            │
│     │  [Notification shows progress]        │                   │            │
│     │                   │                   │                   │            │
│     │  [Download completes - file saved]    │                   │            │
│     │                   │                   │                   │            │
│     │  [Media scan triggered automatically] │                   │            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Share Intent Flow
```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          SHARE OPERATION FLOW                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────────────┐   │
│  │  File/   │     │  Termux  │     │  Android │     │  Target App      │   │
│  │  Text    │────>│  Share   │────>│  Intent  │────>│  (WhatsApp,      │   │
│  │  Source  │     │  Command │     │  Resolver│     │   Gmail, etc.)   │   │
│  └──────────┘     └──────────┘     └──────────┘     └──────────────────┘   │
│                                                                              │
│  Process Steps:                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │ 1. Content Preparation                                               │    │
│  │    - Read file content or use text                                   │    │
│  │    - Determine MIME type                                             │    │
│  │                                                                      │    │
│  │ 2. Intent Creation                                                   │    │
│  │    - Create ACTION_SEND intent                                       │    │
│  │    - Add content URI or text                                         │    │
│  │    - Set MIME type                                                   │    │
│  │                                                                      │    │
│  │ 3. Resolver Activity                                                 │    │
│  │    - Android queries apps with matching intent filters               │    │
│  │    - Shows Share Sheet to user                                       │    │
│  │                                                                      │    │
│  │ 4. Target App Reception                                              │    │
│  │    - Selected app receives intent                                    │    │
│  │    - Processes content                                               │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Parallel File Processing
```bash
#!/bin/bash
# parallel_processor.sh - Process multiple files simultaneously

process_file() {
    local file="$1"
    local output_dir="$2"
    
    # Process each file
    filename=$(basename "$file")
    termux-media-scan "$file"
    cp "$file" "$output_dir/$filename"
    echo "Processed: $filename"
}

export -f process_file

# Process all JPG files in parallel with 4 jobs
find /sdcard/DCIM/Camera -name "*.jpg" -type f | \
    parallel -j 4 process_file {} /sdcard/Pictures/Processed
```

### Advanced Technique 2: Watch Directory for Changes
```bash
#!/bin/bash
# watch_directory.sh - Monitor and auto-process new files

WATCH_DIR="/sdcard/Download"
PROCESSED_DIR="/sdcard/Documents/Processed"

mkdir -p "$PROCESSED_DIR"

echo "Watching $WATCH_DIR for new files..."

inotifywait -m -e create -e moved_to "$WATCH_DIR" 2>/dev/null | \
while read dir action file; do
    echo "New file detected: $file"
    
    filepath="$dir$file"
    
    # Process based on file type
    case "${file##*.}" in
        pdf)
            termux-media-scan "$filepath"
            termux-notification --title "New PDF" --content "$file"
            ;;
        jpg|png)
            termux-media-scan "$filepath"
            termux-share "$filepath"
            ;;
        *)
            echo "Unknown file type: $file"
            ;;
    esac
done
```

### Advanced Technique 3: Smart File Deduplication
```bash
#!/bin/bash
# deduplicate.sh - Find and handle duplicate files

TARGET_DIR="/sdcard/DCIM/Camera"
HASH_FILE="$HOME/.file_hashes"

declare -A file_hashes

# Build hash database
echo "Building hash database..."
find "$TARGET_DIR" -type f | while read file; do
    hash=$(md5sum "$file" | cut -d' ' -f1)
    echo "$hash|$file" >> "$HASH_FILE.tmp"
done

# Find duplicates
echo "Finding duplicates..."
sort "$HASH_FILE.tmp" | uniq -w32 -D > "$HASH_FILE.duplicates"

# Process duplicates
echo "Processing duplicates..."
while IFS='|' read hash file; do
    if [[ -n "${file_hashes[$hash]}" ]]; then
        echo "Duplicate found: $file"
        echo "  Original: ${file_hashes[$hash]}"
        read -p "Delete duplicate? (y/n): " choice
        if [[ "$choice" == "y" ]]; then
            rm "$file"
            echo "  Deleted!"
        fi
    else
        file_hashes[$hash]="$file"
    fi
done < "$HASH_FILE.duplicates"

# Cleanup
rm -f "$HASH_FILE.tmp" "$HASH_FILE.duplicates"
echo "Deduplication complete!"
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### ✅ What You Learned

- [ ] **termux-storage-get** - Opens Android file picker for selecting files
- [ ] **termux-share** - Shares files and text through Android share sheet
- [ ] **termux-download** - Downloads files using Android Download Manager
- [ ] **termux-media-scan** - Registers files in MediaStore for gallery visibility
- [ ] **MIME types** - Proper content type specification for file sharing
- [ ] **Storage paths** - Understanding Termux home vs shared storage locations
- [ ] **Python integration** - Using subprocess to call Termux APIs
- [ ] **Bash scripting** - Creating automation scripts for file operations
- [ ] **Error handling** - Checking return codes and file existence
- [ ] **Batch processing** - Processing multiple files efficiently

### 📋 Quick Reference Commands
```bash
# File picker
termux-storage-get ~/picked_file

# Share file
termux-share document.pdf

# Share text
echo "Hello" | termux-share

# Download file
termux-download "https://example.com/file.pdf"

# Download to specific folder
termux-download -d /sdcard/Documents "URL"

# Make visible in gallery
termux-media-scan /sdcard/DCIM/photo.jpg

# Share with MIME type
termux-share -c "application/pdf" doc.pdf
```

### 🎯 Next Steps
1. Practice file operations with different file types
2. Create automated backup scripts
3. Integrate with other Termux APIs
4. Build a complete file management tool

### 📚 Recommended Practice
- Create a photo organization script
- Build a document scanner workflow
- Implement a file sync system

---

*Chapter 17 Complete! Ready for Chapter 18: Device Information APIs*


---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

<details>
<summary><b>❓ Question 1: Which Termux API command opens the Android file picker?</b></summary>

**Answer:** `termux-storage-get`

This command opens Android's Storage Access Framework file picker, allowing users to select any file from their device. The selected file is copied to the specified destination path in Termux.

Example: `termux-storage-get ~/my_selected_file`
</details>

<details>
<summary><b>❓ Question 2: What is the default download location for termux-download?</b></summary>

**Answer:** `/sdcard/Download`

The termux-download command uses Android's Download Manager, which saves files to the default Downloads folder. You can change this with the `-d` or `--path` flag.

Example: `termux-download -d /sdcard/Documents "https://example.com/file.pdf"`
</details>

<details>
<summary><b>❓ Question 3: How do you share text directly from the terminal?</b></summary>

**Answer:** Using pipe with `termux-share`:

```bash
echo "Your text here" | termux-share
```

This opens the Android share sheet with the text ready to share to any app.
</details>

<details>
<summary><b>❓ Question 4: Why doesn't my downloaded image appear in the gallery?</b></summary>

**Answer:** Android's MediaStore needs to be updated. Use `termux-media-scan`:

```bash
termux-media-scan /sdcard/Download/image.jpg
```

This registers the file with Android's media database, making it visible in gallery apps.
</details>

<details>
<summary><b>❓ Question 5: What does the -c flag do in termux-share?</b></summary>

**Answer:** The `-c` flag specifies the MIME content type:

```bash
termux-share -c "image/jpeg" photo.jpg
termux-share -c "application/pdf" document.pdf
termux-share -c "text/plain" notes.txt
```

This helps apps properly handle the shared content.
</details>

<details>
<summary><b>❓ Question 6: Does termux-storage-get move or copy files?</b></summary>

**Answer:** It **copies** files. The original file remains in its source location. Only a copy is saved to the Termux destination path.

This is important for preserving the original file while making it accessible in Termux.
</details>

<details>
<summary><b>❓ Question 7: What permission is required before using file operation APIs?</b></summary>

**Answer:** Storage permission must be granted:

```bash
termux-setup-storage
```

This creates symlinks to shared storage directories and grants Termux access to Android's shared storage.
</details>

<details>
<summary><b>❓ Question 8: How can you download multiple files programmatically?</b></summary>

**Answer:** Use a loop with the download command:

```bash
while IFS= read -r url; do
    termux-download "$url"
    sleep 2
done < urls.txt
```

The delay between downloads prevents overwhelming the download manager.
</details>

<details>
<summary><b>❓ Question 9: What is the difference between termux-share and termux-storage-get?</b></summary>

**Answer:**

| Command | Purpose | Direction |
|---------|---------|-----------|
| `termux-storage-get` | File picker | Android → Termux |
| `termux-share` | Share content | Termux → Android apps |

`termux-storage-get` brings files INTO Termux, while `termux-share` sends files OUT to other apps.
</details>

<details>
<summary><b>❓ Question 10: How do you specify a custom notification title for downloads?</b></summary>

**Answer:** Use the `-t` flag:

```bash
termux-download -t "My Document" "https://example.com/file.pdf"
```

This sets a custom title in the download notification.
</details>

<details>
<summary><b>❓ Question 11: Can termux-download handle background downloads?</b></summary>

**Answer:** Yes! This is one of its main advantages. Downloads continue even when Termux is closed because it uses Android's system Download Manager.

The download runs as a system service and shows progress in the notification shade.
</details>

<details>
<summary><b>❓ Question 12: What Python module is used to call Termux API commands?</b></summary>

**Answer:** The `subprocess` module:

```python
import subprocess
result = subprocess.run(['termux-storage-get', '~/file'], capture_output=True)
```

This allows Python scripts to execute shell commands and capture their output.
</details>

<details>
<summary><b>❓ Question 13: How do you share a file for viewing instead of sending?</b></summary>

**Answer:** Use the `-a view` flag:

```bash
termux-share -a view photo.jpg
```

Available actions: `send` (default), `view`, `edit`
</details>

<details>
<summary><b>❓ Question 14: What file types can termux-storage-get handle?</b></summary>

**Answer:** Virtually **any file type**:

- Images (jpg, png, gif, webp)
- Videos (mp4, mkv, avi)
- Documents (pdf, doc, txt)
- Archives (zip, tar, gz)
- Audio files (mp3, wav, flac)
- Any other file type the user can access

The file picker shows all accessible files regardless of type.
</details>

<details>
<summary><b>❓ Question 15: What happens if termux-storage-get fails?</b></summary>

**Answer:** It returns a non-zero exit code. You can check this in scripts:

```bash
if termux-storage-get ~/file; then
    echo "File selected successfully"
else
    echo "No file selected or error occurred"
fi
```

Common causes: user cancelled, no permission, destination path not writable.
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Q1: How would you implement a file synchronization system using Termux APIs?

**Answer:**

```python
#!/usr/bin/env python3
import subprocess
import os
import json
import hashlib

class FileSyncManager:
    def __init__(self, source_dir, dest_dir):
        self.source = source_dir
        self.dest = dest_dir
        
    def get_file_hash(self, filepath):
        """Calculate MD5 hash for file comparison"""
        hash_md5 = hashlib.md5()
        with open(filepath, "rb") as f:
            for chunk in iter(lambda: f.read(4096), b""):
                hash_md5.update(chunk)
        return hash_md5.hexdigest()
    
    def sync_files(self):
        """Synchronize files between directories"""
        synced = []
        for root, dirs, files in os.walk(self.source):
            for file in files:
                src_path = os.path.join(root, file)
                rel_path = os.path.relpath(src_path, self.source)
                dest_path = os.path.join(self.dest, rel_path)
                
                # Create destination directory
                os.makedirs(os.path.dirname(dest_path), exist_ok=True)
                
                # Check if sync needed
                needs_sync = True
                if os.path.exists(dest_path):
                    src_hash = self.get_file_hash(src_path)
                    dest_hash = self.get_file_hash(dest_path)
                    needs_sync = (src_hash != dest_hash)
                
                if needs_sync:
                    # Use termux-share for cross-app sync
                    subprocess.run(['cp', src_path, dest_path])
                    subprocess.run(['termux-media-scan', dest_path])
                    synced.append(rel_path)
        
        return synced

# Usage
sync = FileSyncManager('/sdcard/DCIM', '/sdcard/Backup')
synced_files = sync.sync_files()
print(f"Synced {len(synced_files)} files")
```

Key considerations:
- Hash comparison for change detection
- Directory structure preservation
- MediaStore updates for gallery visibility
- Error handling for permission issues
</details>

### Q2: Explain the security implications of Termux file APIs.

**Answer:**

**Security Considerations:**

1. **Permission Model:**
   - Storage permission grants broad access
   - No fine-grained control per file
   - Apps can access all shared storage

2. **Data Exposure:**
   - Files copied to Termux are readable by Termux
   - Shared files pass through Android intents
   - Clipboard content is system-wide accessible

3. **Best Practices:**
```bash
# Always verify file operations
if termux-storage-get ~/sensitive_file; then
    # Encrypt sensitive data
    gpg -c ~/sensitive_file
    # Secure delete original
    shred -u ~/sensitive_file
fi

# Check file permissions
stat -c "%a %n" ~/file

# Limit share scope
termux-share -c "application/octet-stream" encrypted_file.gpg
```

4. **Mitigation Strategies:**
   - Encrypt sensitive files before sharing
   - Use app-specific directories when possible
   - Clear clipboard after sensitive operations
   - Audit file permissions regularly
</details>

### Q3: Design a batch download manager with progress tracking.

**Answer:**

```python
#!/usr/bin/env python3
import subprocess
import json
import os
from datetime import datetime

class BatchDownloadManager:
    def __init__(self, download_dir="/sdcard/Download/BatchDownloads"):
        self.download_dir = download_dir
        self.state_file = os.path.expanduser("~/.download_state.json")
        os.makedirs(download_dir, exist_ok=True)
        
    def load_state(self):
        """Load previous download state"""
        try:
            with open(self.state_file, 'r') as f:
                return json.load(f)
        except:
            return {"completed": [], "failed": [], "pending": []}
    
    def save_state(self, state):
        """Save current download state"""
        with open(self.state_file, 'w') as f:
            json.dump(state, f, indent=2)
    
    def add_urls(self, urls):
        """Add URLs to download queue"""
        state = self.load_state()
        for url in urls:
            if url not in state["completed"] and url not in state["pending"]:
                state["pending"].append({
                    "url": url,
                    "added": datetime.now().isoformat()
                })
        self.save_state(state)
    
    def download_next(self):
        """Download next file in queue"""
        state = self.load_state()
        
        if not state["pending"]:
            return None
        
        item = state["pending"].pop(0)
        url = item["url"]
        
        try:
            # Start download
            result = subprocess.run(
                ['termux-download', '-d', self.download_dir, url],
                capture_output=True,
                timeout=300  # 5 minute timeout
            )
            
            if result.returncode == 0:
                state["completed"].append({
                    "url": url,
                    "completed": datetime.now().isoformat()
                })
            else:
                state["failed"].append({
                    "url": url,
                    "error": result.stderr.decode(),
                    "timestamp": datetime.now().isoformat()
                })
        except Exception as e:
            state["failed"].append({
                "url": url,
                "error": str(e),
                "timestamp": datetime.now().isoformat()
            })
        
        self.save_state(state)
        return item
    
    def process_all(self):
        """Process entire download queue"""
        while True:
            item = self.download_next()
            if item is None:
                break
            print(f"Downloaded: {item['url']}")
        
        state = self.load_state()
        print(f"\nSummary:")
        print(f"  Completed: {len(state['completed'])}")
        print(f"  Failed: {len(state['failed'])}")

# Usage
manager = BatchDownloadManager()
manager.add_urls([
    "https://example.com/file1.pdf",
    "https://example.com/file2.pdf",
])
manager.process_all()
```

Features:
- State persistence for resume capability
- Error tracking and logging
- Timeout handling
- Progress reporting
</details>

### Q4: How would you integrate Termux file APIs with a CI/CD pipeline?

**Answer:**

```bash
#!/bin/bash
# ci_file_pipeline.sh - CI/CD integration script

set -e  # Exit on error

# Configuration
BUILD_DIR="$HOME/build_$(date +%Y%m%d_%H%M%S)"
REPORT_DIR="$HOME/reports"
NOTIFICATION_WEBHOOK="https://hooks.example.com/ci"

# Functions
log() {
    echo "[$(date '+%H:%M:%S')] $1"
}

send_notification() {
    local status="$1"
    local message="$2"
    
    # Send to webhook
    curl -s -X POST "$NOTIFICATION_WEBHOOK" \
        -H "Content-Type: application/json" \
        -d "{\"status\":\"$status\",\"message\":\"$message\"}" &
    
    # Also send local notification
    termux-notification \
        --title "CI Pipeline: $status" \
        --content "$message" \
        --priority high \
        --sound
}

# Main pipeline
main() {
    log "Starting CI pipeline..."
    mkdir -p "$BUILD_DIR" "$REPORT_DIR"
    
    # Step 1: Get configuration file
    log "Fetching configuration..."
    if termux-storage-get "$BUILD_DIR/config.json"; then
        log "Configuration loaded"
    else
        send_notification "FAILED" "Configuration file required"
        exit 1
    fi
    
    # Step 2: Run tests
    log "Running tests..."
    pytest tests/ --json="$REPORT_DIR/test_results.json" || {
        send_notification "TESTS FAILED" "Check test results"
        termux-share "$REPORT_DIR/test_results.json"
        exit 1
    }
    
    # Step 3: Build
    log "Building..."
    python setup.py build 2>&1 | tee "$REPORT_DIR/build.log"
    
    # Step 4: Generate report
    log "Generating report..."
    cat > "$REPORT_DIR/summary.txt" << EOF
Build: $BUILD_DIR
Date: $(date)
Status: SUCCESS
Tests: $(jq '.summary.passed' "$REPORT_DIR/test_results.json") passed
EOF
    
    # Step 5: Share results
    termux-share "$REPORT_DIR/summary.txt"
    
    # Step 6: Backup artifacts
    for artifact in "$BUILD_DIR"/*; do
        termux-media-scan "$artifact" 2>/dev/null || true
    done
    
    send_notification "SUCCESS" "Pipeline completed successfully"
    log "Pipeline complete!"
}

main "$@"
```

Integration points:
- Notification system for build status
- File sharing for reports and logs
- Media scanning for artifact visibility
- Configuration loading from user files
</details>

### Q5: Compare termux-download vs wget/curl for file downloading.

**Answer:**

| Feature | termux-download | wget/curl |
|---------|----------------|-----------|
| **Background download** | ✅ Yes (system service) | ❌ No (process-bound) |
| **Progress notification** | ✅ System notification | ❌ Terminal only |
| **Resume support** | ✅ Automatic | ⚠️ Manual flags needed |
| **Storage location** | Shared storage | Any (Termux filesystem) |
| **Battery optimization** | ✅ System managed | ❌ Runs in foreground |
| **Network handling** | ✅ System handles | ❌ Manual retry logic |

**When to use each:**

```bash
# Use termux-download for user-facing downloads
termux-download "https://example.com/movie.mp4"  # Large files, user visible

# Use wget/curl for scripts and automation
wget -O data.json "https://api.example.com/data"  # Script data
curl -s "https://api.example.com/config" | jq '.'  # API calls

# Combined approach for best of both
download_and_process() {
    # Download with system manager
    termux-download "https://example.com/data.json"
    
    # Process with Termux tools
    jq '.' /sdcard/Download/data.json > ~/processed_data.json
    
    # Share result
    termux-share ~/processed_data.json
}
```

**Recommendation:** Use `termux-download` for large files and user-initiated downloads; use `curl/wget` for API calls and script automation.
</details>

### Q6: Implement a file change detection and backup system.

**Answer:**

```python
#!/usr/bin/env python3
"""File Change Detection and Backup System"""

import os
import hashlib
import json
import subprocess
from datetime import datetime
from pathlib import Path

class FileChangeDetector:
    def __init__(self, watch_dirs, backup_dir):
        self.watch_dirs = watch_dirs
        self.backup_dir = Path(backup_dir)
        self.snapshot_file = Path("~/.file_snapshot.json").expanduser()
        self.backup_dir.mkdir(parents=True, exist_ok=True)
    
    def calculate_hash(self, filepath):
        """Calculate file hash for change detection"""
        hasher = hashlib.sha256()
        try:
            with open(filepath, 'rb') as f:
                for chunk in iter(lambda: f.read(65536), b''):
                    hasher.update(chunk)
            return hasher.hexdigest()
        except:
            return None
    
    def create_snapshot(self):
        """Create snapshot of all watched directories"""
        snapshot = {}
        
        for watch_dir in self.watch_dirs:
            watch_path = Path(watch_dir)
            if not watch_path.exists():
                continue
                
            for filepath in watch_path.rglob('*'):
                if filepath.is_file():
                    rel_path = str(filepath.relative_to(watch_path))
                    file_hash = self.calculate_hash(filepath)
                    if file_hash:
                        snapshot[f"{watch_dir}:{rel_path}"] = {
                            'hash': file_hash,
                            'size': filepath.stat().st_size,
                            'modified': datetime.fromtimestamp(
                                filepath.stat().st_mtime
                            ).isoformat()
                        }
        
        return snapshot
    
    def load_snapshot(self):
        """Load previous snapshot"""
        try:
            with open(self.snapshot_file, 'r') as f:
                return json.load(f)
        except:
            return {}
    
    def detect_changes(self):
        """Detect file changes since last snapshot"""
        current = self.create_snapshot()
        previous = self.load_snapshot()
        
        changes = {
            'added': [],
            'modified': [],
            'deleted': []
        }
        
        # Find added and modified
        for key, info in current.items():
            if key not in previous:
                changes['added'].append(key)
            elif info['hash'] != previous[key]['hash']:
                changes['modified'].append(key)
        
        # Find deleted
        for key in previous:
            if key not in current:
                changes['deleted'].append(key)
        
        return changes
    
    def backup_changed(self, changes):
        """Backup changed files"""
        backed_up = []
        
        for key in changes['added'] + changes['modified']:
            watch_dir, rel_path = key.split(':', 1)
            source = Path(watch_dir) / rel_path
            
            # Create dated backup
            date_dir = self.backup_dir / datetime.now().strftime('%Y-%m-%d')
            dest = date_dir / rel_path
            dest.parent.mkdir(parents=True, exist_ok=True)
            
            # Copy file
            import shutil
            shutil.copy2(source, dest)
            
            # Scan for gallery if media file
            if source.suffix.lower() in ['.jpg', '.png', '.mp4', '.mp3']:
                subprocess.run(['termux-media-scan', str(dest)], 
                             capture_output=True)
            
            backed_up.append(str(dest))
        
        return backed_up
    
    def run(self):
        """Run change detection and backup"""
        changes = self.detect_changes()
        
        if any(changes.values()):
            # Backup changed files
            backed_up = self.backup_changed(changes)
            
            # Update snapshot
            current = self.create_snapshot()
            with open(self.snapshot_file, 'w') as f:
                json.dump(current, f, indent=2)
            
            # Notify
            subprocess.run([
                'termux-notification',
                '--title', 'File Backup Complete',
                '--content', f"{len(backed_up)} files backed up",
                '--sound'
            ])
            
            return changes
        else:
            return None

# Usage
detector = FileChangeDetector(
    watch_dirs=['/sdcard/DCIM', '/sdcard/Documents'],
    backup_dir='/sdcard/Backup'
)
detector.run()
```

Features:
- SHA256 hash-based change detection
- Automatic backup of modified files
- Gallery integration for media
- Notification system
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Photo Backup Automation

```
╔══════════════════════════════════════════════════════════════════════╗
║  📸 SCENARIO: Automatic Photo Backup to Cloud Storage                 ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  SITUATION:                                                            ║
║  User wants all new photos automatically backed up to cloud storage   ║
║  when connected to WiFi and charging.                                 ║
║                                                                        ║
║  SOLUTION:                                                             ║
╚══════════════════════════════════════════════════════════════════════╝
```

```bash
#!/bin/bash
# auto_photo_backup.sh

PHOTO_DIR="/sdcard/DCIM/Camera"
BACKUP_LOG="$HOME/.photo_backup.log"
LAST_BACKUP="$HOME/.last_photo_backup"

# Check conditions
check_conditions() {
    # Check charging
    battery=$(termux-battery-status | jq -r '.plugged')
    [ "$battery" = "PLUGGED_AC" ] || [ "$battery" = "PLUGGED_USB" ] || return 1
    
    # Check WiFi
    wifi=$(termux-wifi-connectioninfo | jq -r '.ssid' 2>/dev/null)
    [ -n "$wifi" ] && [ "$wifi" != "null" ] || return 1
    
    return 0
}

# Get last backup timestamp
get_last_backup() {
    if [ -f "$LAST_BACKUP" ]; then
        cat "$LAST_BACKUP"
    else
        echo "0"
    fi
}

# Backup new photos
backup_photos() {
    local last=$(get_last_backup)
    local count=0
    
    for photo in "$PHOTO_DIR"/*.jpg "$PHOTO_DIR"/*.mp4; do
        [ -f "$photo" ] || continue
        
        local mtime=$(stat -c %Y "$photo")
        
        if [ "$mtime" -gt "$last" ]; then
            # Upload to cloud (example with rclone)
            rclone copy "$photo" gdrive:Photos/Backup/ 2>/dev/null
            
            if [ $? -eq 0 ]; then
                echo "$(date): Backed up $photo" >> "$BACKUP_LOG"
                ((count++))
            fi
        fi
    done
    
    # Update last backup time
    date +%s > "$LAST_BACKUP"
    
    return $count
}

# Main
if check_conditions; then
    backup_photos
    count=$?
    
    if [ $count -gt 0 ]; then
        termux-notification \
            --title "📸 Photo Backup" \
            --content "$count photos backed up to cloud" \
            --priority low
    fi
fi
```

---

### Scenario 2: Document Scanner Workflow

```
╔══════════════════════════════════════════════════════════════════════╗
║  📄 SCENARIO: Document Scanner and OCR Pipeline                       ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  SITUATION:                                                            ║
║  User needs to scan documents using camera, OCR them, and share      ║
║  the text output.                                                     ║
║                                                                        ║
║  SOLUTION:                                                             ║
╚══════════════════════════════════════════════════════════════════════╝
```

```bash
#!/bin/bash
# document_scanner.sh

SCAN_DIR="$HOME/scans"
mkdir -p "$SCAN_DIR"

TIMESTAMP=$(date +%Y%m%d_%H%M%S)
PHOTO="$SCAN_DIR/doc_$TIMESTAMP.jpg"
TEXT="$SCAN_DIR/doc_$TIMESTAMP.txt"

echo "📄 Document Scanner"
echo "==================="
echo ""

# Capture photo
echo "Capturing document..."
termux-camera-photo -c 0 "$PHOTO"

if [ ! -f "$PHOTO" ]; then
    echo "❌ Failed to capture photo"
    exit 1
fi

echo "✅ Photo captured: $PHOTO"

# Process with OCR (requires tesseract)
echo ""
echo "Running OCR..."
if command -v tesseract &> /dev/null; then
    tesseract "$PHOTO" "${TEXT%.txt}" 2>/dev/null
    
    if [ -f "$TEXT" ]; then
        echo "✅ OCR complete!"
        
        # Copy text to clipboard
        cat "$TEXT" | termux-clipboard-set
        echo "📋 Text copied to clipboard"
        
        # Show preview
        echo ""
        echo "Preview:"
        echo "--------"
        head -10 "$TEXT"
        echo "..."
        
        # Ask to share
        read -p "Share document? (y/n): " share
        if [ "$share" = "y" ]; then
            termux-share "$TEXT"
        fi
    else
        echo "❌ OCR failed"
    fi
else
    echo "⚠️ Tesseract not installed"
    echo "Install with: pkg install tesseract"
    
    # Share image instead
    termux-share "$PHOTO"
fi

# Scan for gallery
termux-media-scan "$PHOTO"
```

---

### Scenario 3: Bulk File Organizer

```
╔══════════════════════════════════════════════════════════════════════╗
║  📁 SCENARIO: Automatic File Organizer by Type                        ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  SITUATION:                                                            ║
║  Downloads folder is cluttered with mixed file types. User wants     ║
║  automatic organization by file type.                                 ║
║                                                                        ║
║  SOLUTION:                                                             ║
╚══════════════════════════════════════════════════════════════════════╝
```

```bash
#!/bin/bash
# file_organizer.sh

SOURCE_DIR="/sdcard/Download"
ORGANIZED_DIR="/sdcard/Organized"

# File type mappings
declare -A FILE_TYPES=(
    ["jpg jpeg png gif webp"]="Images"
    ["mp4 mkv avi mov"]="Videos"
    ["mp3 wav flac aac"]="Audio"
    ["pdf"]="Documents/PDFs"
    ["doc docx"]="Documents/Word"
    ["xls xlsx"]="Documents/Excel"
    ["ppt pptx"]="Documents/PowerPoint"
    ["zip tar gz rar"]="Archives"
    ["apk"]="APKs"
    ["json xml csv"]="Data"
)

organize_file() {
    local file="$1"
    local ext="${file##*.}"
    ext="${ext,,}"  # lowercase
    
    local found=0
    
    for types in "${!FILE_TYPES[@]}"; do
        if [[ " $types " =~ " $ext " ]]; then
            dest_folder="${FILE_TYPES[$types]}"
            found=1
            break
        fi
    done
    
    if [ $found -eq 0 ]; then
        dest_folder="Other"
    fi
    
    dest_path="$ORGANIZED_DIR/$dest_folder"
    mkdir -p "$dest_path"
    
    filename=$(basename "$file")
    
    # Move file
    mv "$file" "$dest_path/$filename"
    
    # Scan for media if applicable
    if [[ "$dest_folder" == "Images" ]] || [[ "$dest_folder" == "Videos" ]]; then
        termux-media-scan "$dest_path/$filename"
    fi
    
    echo "Moved: $filename → $dest_folder"
}

# Main
echo "📁 File Organizer"
echo "================="
echo ""
echo "Organizing files in: $SOURCE_DIR"
echo ""

count=0
for file in "$SOURCE_DIR"/*; do
    [ -f "$file" ] || continue
    organize_file "$file"
    ((count++))
done

echo ""
echo "✅ Organized $count files!"

# Notification
termux-notification \
    --title "📁 File Organizer" \
    --content "Organized $count files" \
    --priority low

# Show organized structure
echo ""
echo "New structure:"
find "$ORGANIZED_DIR" -type d | head -20
```

---

### Scenario 4: Secure File Transfer

```
╔══════════════════════════════════════════════════════════════════════╗
║  🔐 SCENARIO: Encrypted File Transfer Between Devices                 ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  SITUATION:                                                            ║
║  User needs to securely transfer sensitive files between devices     ║
║  with encryption.                                                     ║
║                                                                        ║
║  SOLUTION:                                                             ║
╚══════════════════════════════════════════════════════════════════════╝
```

```bash
#!/bin/bash
# secure_transfer.sh

TEMP_DIR="$HOME/secure_transfer"
mkdir -p "$TEMP_DIR"

# Generate encryption key
generate_key() {
    openssl rand -base64 32 > "$TEMP_DIR/key.txt"
    echo "🔑 Key generated: $TEMP_DIR/key.txt"
    
    # Copy key to clipboard for sharing
    cat "$TEMP_DIR/key.txt" | termux-clipboard-set
    echo "📋 Key copied to clipboard (share securely!)"
}

# Encrypt file
encrypt_file() {
    local input="$1"
    local output="$TEMP_DIR/$(basename "$input").enc"
    
    openssl enc -aes-256-cbc -salt -pbkdf2 \
        -in "$input" \
        -out "$output" \
        -pass file:"$TEMP_DIR/key.txt"
    
    echo "🔒 Encrypted: $output"
    
    # Share encrypted file
    termux-share "$output"
}

# Decrypt file
decrypt_file() {
    local input="$1"
    local output="${input%.enc}"
    
    openssl enc -aes-256-cbc -d -pbkdf2 \
        -in "$input" \
        -out "$output" \
        -pass file:"$TEMP_DIR/key.txt"
    
    echo "🔓 Decrypted: $output"
}

# Interactive menu
show_menu() {
    echo ""
    echo "🔐 Secure File Transfer"
    echo "======================="
    echo "1. Generate encryption key"
    echo "2. Encrypt and share file"
    echo "3. Decrypt received file"
    echo "4. Pick and encrypt file"
    echo "5. Exit"
    echo ""
    read -p "Choice: " choice
    
    case $choice in
        1)
            generate_key
            ;;
        2)
            read -p "File to encrypt: " filepath
            [ -f "$filepath" ] && encrypt_file "$filepath"
            ;;
        3)
            read -p "Encrypted file: " filepath
            [ -f "$filepath" ] && decrypt_file "$filepath"
            ;;
        4)
            termux-storage-get "$TEMP_DIR/picked_file"
            [ -f "$TEMP_DIR/picked_file" ] && encrypt_file "$TEMP_DIR/picked_file"
            ;;
        5)
            exit 0
            ;;
    esac
}

# Main loop
while true; do
    show_menu
done
```

---

### Scenario 5: Media Collection Backup

```
╔══════════════════════════════════════════════════════════════════════╗
║  💽 SCENARIO: Complete Media Collection Backup                        ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  SITUATION:                                                            ║
║  User wants to backup all media files with metadata preservation     ║
║  and generate a catalog.                                              ║
║                                                                        ║
║  SOLUTION:                                                             ║
╚══════════════════════════════════════════════════════════════════════╝
```

```bash
#!/bin/bash
# media_backup.sh

SOURCE_DIRS=("/sdcard/DCIM" "/sdcard/Pictures" "/sdcard/Music" "/sdcard/Movies")
BACKUP_DIR="/sdcard/Backup/Media_$(date +%Y%m%d)"
CATALOG="$BACKUP_DIR/catalog.json"

mkdir -p "$BACKUP_DIR"

echo "💾 Media Collection Backup"
echo "========================="
echo ""
echo "Source directories:"
for dir in "${SOURCE_DIRS[@]}"; do
    echo "  - $dir"
done
echo ""
echo "Backup location: $BACKUP_DIR"
echo ""

# Initialize catalog
echo '{"backup_date": "'$(date -Iseconds)'", "files": []}' > "$CATALOG"

total_files=0
total_size=0

backup_media() {
    local source="$1"
    local type="$2"
    
    for file in "$source"/*; do
        [ -f "$file" ] || continue
        
        local filename=$(basename "$file")
        local ext="${filename##*.}"
        ext="${ext,,}"
        
        # Check if media file
        case "$ext" in
            jpg|jpeg|png|gif|webp|mp4|mkv|avi|mp3|wav|flac)
                local dest="$BACKUP_DIR/$type"
                mkdir -p "$dest"
                
                # Copy file
                cp "$file" "$dest/$filename"
                
                # Get file info
                local size=$(stat -c %s "$file")
                local mtime=$(stat -c %Y "$file")
                
                # Add to catalog
                local entry="{\"name\":\"$filename\",\"type\":\"$type\",\"size\":$size,\"modified\":$mtime}"
                jq ".files += [$entry]" "$CATALOG" > "$CATALOG.tmp" && mv "$CATALOG.tmp" "$CATALOG"
                
                # Scan for gallery
                termux-media-scan "$dest/$filename" 2>/dev/null
                
                ((total_files++))
                ((total_size+=size))
                
                echo "  ✓ $filename"
                ;;
        esac
    done
}

# Process each source
for dir in "${SOURCE_DIRS[@]}"; do
    if [ -d "$dir" ]; then
        echo "Processing: $dir"
        type=$(basename "$dir")
        backup_media "$dir" "$type"
        echo ""
    fi
done

# Calculate totals
total_size_mb=$((total_size / 1048576))

echo "=================================="
echo "Backup Complete!"
echo "Files backed up: $total_files"
echo "Total size: ${total_size_mb} MB"
echo "Catalog: $CATALOG"
echo ""

# Share catalog
read -p "Share backup catalog? (y/n): " share
[ "$share" = "y" ] && termux-share "$CATALOG"

# Notification
termux-notification \
    --title "💾 Media Backup Complete" \
    --content "$total_files files (${total_size_mb}MB)" \
    --priority low \
    --sound
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: File Operation API Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    FILE OPERATION API FLOW                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   USER ACTION                                                            │
│       │                                                                  │
│       ▼                                                                  │
│   ┌─────────────┐                                                        │
│   │   Termux    │                                                        │
│   │   Command   │                                                        │
│   └──────┬──────┘                                                        │
│          │                                                               │
│          ▼                                                               │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    TERMUX:API BRIDGE                             │   │
│   │                                                                  │   │
│   │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │   │
│   │  │ termux-      │  │ termux-      │  │ termux-      │          │   │
│   │  │ storage-get  │  │ share        │  │ download     │          │   │
│   │  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘          │   │
│   │         │                 │                 │                   │   │
│   └─────────┼─────────────────┼─────────────────┼───────────────────┘   │
│             │                 │                 │                        │
│             ▼                 ▼                 ▼                        │
│   ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐           │
│   │ Android SAF     │ │ Android Share   │ │ Android Download│           │
│   │ (File Picker)   │ │ Intent          │ │ Manager         │           │
│   └────────┬────────┘ └────────┬────────┘ └────────┬────────┘           │
│            │                   │                   │                     │
│            ▼                   ▼                   ▼                     │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    ANDROID SYSTEM SERVICES                       │   │
│   │                                                                  │   │
│   │  • Storage Access Framework    • Intent Resolution               │   │
│   │  • MediaStore                  • Notification Manager             │   │
│   │  • Content Providers           • Download Service                 │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Share Mechanism Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SHARE MECHANISM ARCHITECTURE                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    TERMUX TERMINAL                               │   │
│   │                                                                  │   │
│   │   $ termux-share document.pdf                                    │   │
│   │   $ echo "text" | termux-share                                   │   │
│   │                                                                  │   │
│   └────────────────────────────┬────────────────────────────────────┘   │
│                                │                                         │
│                                │ Intent: ACTION_SEND                     │
│                                ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    ANDROID SHARE SHEET                           │   │
│   │                                                                  │   │
│   │   ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐       │   │
│   │   │WhatsApp│ │Telegram│ │ Gmail  │ │Bluetooth│ │ More  │       │   │
│   │   └────┬───┘ └────┬───┘ └────┬───┘ └────┬───┘ └────────┘       │   │
│   │        │          │          │          │                        │   │
│   └────────┼──────────┼──────────┼──────────┼────────────────────────┘   │
│            │          │          │          │                             │
│            ▼          ▼          ▼          ▼                             │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                    TARGET APPLICATIONS                           │    │
│   │                                                                  │    │
│   │   WhatsApp: Message to contact/chat                             │    │
│   │   Telegram: Share to chat/saved messages                        │    │
│   │   Gmail:    Attach to email                                     │    │
│   │   Bluetooth: Send to paired device                              │    │
│   │                                                                  │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│   DATA FLOW:                                                            │
│   ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐         │
│   │ Termux   │───▶│ Intent   │───▶│ Share    │───▶│ Target   │         │
│   │ File     │    │ System   │    │ Sheet    │    │ App      │         │
│   └──────────┘    └──────────┘    └──────────┘    └──────────┘         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Download Manager Integration

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    DOWNLOAD MANAGER INTEGRATION                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    DOWNLOAD INITIATION                           │   │
│   │                                                                  │   │
│   │   $ termux-download "https://example.com/file.pdf"              │   │
│   │                                                                  │   │
│   │   ┌──────────────────────────────────────────────────────────┐  │   │
│   │   │ 1. Parse URL                                             │  │   │
│   │   │ 2. Create DownloadManager.Request                        │  │   │
│   │   │ 3. Set destination path                                  │  │   │
│   │   │ 4. Configure notification                                │  │   │
│   │   │ 5. Enqueue download                                      │  │   │
│   │   └──────────────────────────────────────────────────────────┘  │   │
│   │                                                                  │   │
│   └────────────────────────────┬────────────────────────────────────┘   │
│                                │                                         │
│                                ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    ANDROID DOWNLOAD SERVICE                      │   │
│   │                                                                  │   │
│   │   ┌──────────────────────────────────────────────────────────┐  │   │
│   │   │                    Download Queue                        │  │   │
│   │   │                                                          │  │   │
│   │   │   ┌─────────┐  ┌─────────┐  ┌─────────┐                 │  │   │
│   │   │   │ File 1  │  │ File 2  │  │ File 3  │  ...            │  │   │
│   │   │   │ [====]  │  │ [==  ]  │  │ [     ] │                 │  │   │
│   │   │   │  60%    │  │  25%    │  │  Queued │                 │  │   │
│   │   │   └─────────┘  └─────────┘  └─────────┘                 │  │   │
│   │   │                                                          │  │   │
│   │   └──────────────────────────────────────────────────────────┘  │   │
│   │                                                                  │   │
│   │   FEATURES:                                                      │   │
│   │   • Background download (even when Termux closed)               │   │
│   │   • Auto-resume on network recovery                             │   │
│   │   • Progress notification                                        │   │
│   │   • WiFi-only option (configurable)                             │   │
│   │                                                                  │   │
│   └────────────────────────────┬────────────────────────────────────┘   │
│                                │                                         │
│                                ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    COMPLETION                                    │   │
│   │                                                                  │   │
│   │   ┌─────────────────┐    ┌─────────────────┐                    │   │
│   │   │ File saved to   │    │ Notification    │                    │   │
│   │   │ /sdcard/Download│    │ shown           │                    │   │
│   │   └─────────────────┘    └─────────────────┘                    │   │
│   │                                                                  │   │
│   │   ┌─────────────────┐    ┌─────────────────┐                    │   │
│   │   │ MediaStore      │    │ File appears   │                    │   │
│   │   │ updated         │    │ in gallery     │                    │   │
│   │   └─────────────────┘    └─────────────────┘                    │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Relationship | Chapter | Topic |
|--------------|---------|-------|
| **Prerequisites** | Ch 1-3 | Termux Installation & Basic Commands |
| **Prerequisites** | Ch 10 | Termux API Setup & Configuration |
| **Prerequisites** | Ch 14 | File System & Permissions |
| **Related** | Ch 18 | Device Information APIs |
| **Related** | Ch 19 | Camera & Media APIs |
| **Related** | Ch 20 | Network Operations |
| **Related** | Ch 23 | Clipboard & Share APIs |
| **Next** | Ch 18 | Device Information APIs |
| **Advanced** | Ch 45 | Automation Scripts |
| **Advanced** | Ch 52 | Python Integration |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Concurrent Download Manager

```python
#!/usr/bin/env python3
"""Concurrent download manager with progress tracking"""

import subprocess
import threading
import queue
import time
from dataclasses import dataclass
from typing import List, Optional
import json

@dataclass
class DownloadTask:
    url: str
    destination: str
    title: str = ""
    status: str = "pending"
    progress: int = 0

class ConcurrentDownloadManager:
    def __init__(self, max_workers: int = 3):
        self.max_workers = max_workers
        self.task_queue = queue.Queue()
        self.tasks: List[DownloadTask] = []
        self.workers = []
        self.running = False
        
    def add_task(self, url: str, destination: str = "/sdcard/Download", 
                 title: str = ""):
        task = DownloadTask(url=url, destination=destination, title=title)
        self.tasks.append(task)
        self.task_queue.put(task)
        
    def worker(self):
        while self.running:
            try:
                task = self.task_queue.get(timeout=1)
                task.status = "downloading"
                
                # Build command
                cmd = ['termux-download', '-d', task.destination]
                if task.title:
                    cmd.extend(['-t', task.title])
                cmd.append(task.url)
                
                # Execute download
                result = subprocess.run(cmd, capture_output=True)
                
                task.status = "completed" if result.returncode == 0 else "failed"
                self.task_queue.task_done()
                
            except queue.Empty:
                continue
                
    def start(self):
        self.running = True
        for _ in range(self.max_workers):
            worker = threading.Thread(target=self.worker, daemon=True)
            worker.start()
            self.workers.append(worker)
            
    def stop(self):
        self.running = False
        for worker in self.workers:
            worker.join()
            
    def get_status(self) -> dict:
        completed = sum(1 for t in self.tasks if t.status == "completed")
        failed = sum(1 for t in self.tasks if t.status == "failed")
        downloading = sum(1 for t in self.tasks if t.status == "downloading")
        pending = sum(1 for t in self.tasks if t.status == "pending")
        
        return {
            "total": len(self.tasks),
            "completed": completed,
            "failed": failed,
            "downloading": downloading,
            "pending": pending
        }
        
    def show_progress(self):
        status = self.get_status()
        print(f"\rCompleted: {status['completed']}/{status['total']} | "
              f"Active: {status['downloading']} | "
              f"Failed: {status['failed']}", end="")
        
    def wait_completion(self):
        while True:
            status = self.get_status()
            self.show_progress()
            if status['pending'] == 0 and status['downloading'] == 0:
                break
            time.sleep(1)
        print("\nAll downloads complete!")

# Usage
manager = ConcurrentDownloadManager(max_workers=3)
manager.add_task("https://example.com/file1.pdf")
manager.add_task("https://example.com/file2.pdf")
manager.add_task("https://example.com/file3.pdf")

manager.start()
manager.wait_completion()
manager.stop()
```

### Advanced Technique 2: Intelligent File Type Detection

```python
#!/usr/bin/env python3
"""Intelligent file type detection and handling"""

import subprocess
import os
import magic  # python-magic library
from pathlib import Path
from typing import Tuple, Optional
import json

class IntelligentFileHandler:
    MIME_HANDLERS = {
        'image/jpeg': {'share_type': 'image/jpeg', 'scan': True},
        'image/png': {'share_type': 'image/png', 'scan': True},
        'video/mp4': {'share_type': 'video/mp4', 'scan': True},
        'audio/mpeg': {'share_type': 'audio/mpeg', 'scan': True},
        'application/pdf': {'share_type': 'application/pdf', 'scan': False},
        'application/zip': {'share_type': 'application/zip', 'scan': False},
        'text/plain': {'share_type': 'text/plain', 'scan': False},
        'application/json': {'share_type': 'application/json', 'scan': False},
    }
    
    def __init__(self):
        self.mime_detector = magic.Magic(mime=True)
        
    def detect_type(self, filepath: str) -> Tuple[str, Optional[dict]]:
        """Detect file MIME type and get handler info"""
        try:
            mime_type = self.mime_detector.from_file(filepath)
            handler = self.MIME_HANDLERS.get(mime_type, {
                'share_type': 'application/octet-stream',
                'scan': False
            })
            return mime_type, handler
        except:
            return 'application/octet-stream', {
                'share_type': 'application/octet-stream',
                'scan': False
            }
            
    def process_file(self, filepath: str, action: str = 'share') -> dict:
        """Process file with appropriate handler"""
        filepath = os.path.expanduser(filepath)
        
        if not os.path.exists(filepath):
            return {'success': False, 'error': 'File not found'}
            
        mime_type, handler = self.detect_type(filepath)
        result = {
            'filepath': filepath,
            'mime_type': mime_type,
            'handler': handler
        }
        
        if action == 'share':
            # Share with correct MIME type
            cmd = ['termux-share', '-c', handler['share_type'], filepath]
            subprocess.run(cmd)
            result['action'] = 'shared'
            
        elif action == 'scan':
            if handler['scan']:
                subprocess.run(['termux-media-scan', filepath])
                result['action'] = 'scanned'
            else:
                result['action'] = 'scan_not_needed'
                
        elif action == 'info':
            stat = os.stat(filepath)
            result['info'] = {
                'size': stat.st_size,
                'modified': stat.st_mtime,
                'mime': mime_type
            }
            
        result['success'] = True
        return result
        
    def batch_process(self, directory: str, action: str = 'scan') -> list:
        """Process all files in directory"""
        results = []
        for root, dirs, files in os.walk(directory):
            for file in files:
                filepath = os.path.join(root, file)
                result = self.process_file(filepath, action)
                results.append(result)
        return results

# Usage
handler = IntelligentFileHandler()

# Detect file type
mime, info = handler.detect_type("/sdcard/Download/photo.jpg")
print(f"Detected: {mime}")

# Share with correct type
handler.process_file("/sdcard/Download/photo.jpg", 'share')

# Batch scan directory
results = handler.batch_process("/sdcard/DCIM/Camera", 'scan')
```

### Advanced Technique 3: Encrypted File Vault

```python
#!/usr/bin/env python3
"""Encrypted file vault with Termux API integration"""

import subprocess
import os
import hashlib
import base64
from cryptography.fernet import Fernet
from pathlib import Path
import json
from datetime import datetime

class EncryptedVault:
    def __init__(self, vault_path: str = "~/vault"):
        self.vault_path = Path(vault_path).expanduser()
        self.metadata_file = self.vault_path / ".vault_metadata"
        self.key_file = self.vault_path / ".vault_key"
        self.vault_path.mkdir(parents=True, exist_ok=True)
        
    def generate_key(self, password: str) -> bytes:
        """Generate encryption key from password"""
        key = hashlib.sha256(password.encode()).digest()
        return base64.urlsafe_b64encode(key)
        
    def initialize_vault(self, password: str):
        """Initialize vault with password"""
        key = self.generate_key(password)
        with open(self.key_file, 'wb') as f:
            f.write(key)
        
        # Initialize metadata
        metadata = {
            'created': datetime.now().isoformat(),
            'files': {}
        }
        self._save_metadata(metadata)
        
    def _load_key(self) -> bytes:
        """Load encryption key"""
        with open(self.key_file, 'rb') as f:
            return f.read()
            
    def _save_metadata(self, metadata: dict):
        """Save vault metadata"""
        with open(self.metadata_file, 'w') as f:
            json.dump(metadata, f, indent=2)
            
    def _load_metadata(self) -> dict:
        """Load vault metadata"""
        try:
            with open(self.metadata_file, 'r') as f:
                return json.load(f)
        except:
            return {'files': {}}
            
    def encrypt_file(self, source: str, password: str) -> str:
        """Encrypt and store file in vault"""
        key = self.generate_key(password)
        fernet = Fernet(key)
        
        # Read source file
        with open(source, 'rb') as f:
            data = f.read()
            
        # Encrypt
        encrypted = fernet.encrypt(data)
        
        # Generate vault filename
        filename = hashlib.sha256(
            f"{source}{datetime.now()}".encode()
        ).hexdigest()[:16]
        dest = self.vault_path / f"{filename}.enc"
        
        # Save encrypted file
        with open(dest, 'wb') as f:
            f.write(encrypted)
            
        # Update metadata
        metadata = self._load_metadata()
        metadata['files'][filename] = {
            'original_name': os.path.basename(source),
            'size': len(data),
            'encrypted': datetime.now().isoformat()
        }
        self._save_metadata(metadata)
        
        return str(dest)
        
    def decrypt_file(self, vault_file: str, password: str, 
                     output: str = None) -> str:
        """Decrypt file from vault"""
        key = self.generate_key(password)
        fernet = Fernet(key)
        
        # Read encrypted file
        with open(vault_file, 'rb') as f:
            encrypted = f.read()
            
        # Decrypt
        data = fernet.decrypt(encrypted)
        
        # Determine output path
        if output is None:
            metadata = self._load_metadata()
            filename = os.path.basename(vault_file).replace('.enc', '')
            original = metadata['files'].get(filename, {}).get(
                'original_name', 'decrypted_file'
            )
            output = f"~/decrypted_{original}"
            
        output = os.path.expanduser(output)
        
        # Save decrypted file
        with open(output, 'wb') as f:
            f.write(data)
            
        # Scan for gallery if media
        if output.lower().endswith(('.jpg', '.png', '.mp4', '.mp3')):
            subprocess.run(['termux-media-scan', output])
            
        return output
        
    def import_and_encrypt(self, password: str) -> str:
        """Pick file, encrypt, and store in vault"""
        temp_file = self.vault_path / "temp_import"
        
        # Pick file
        subprocess.run(['termux-storage-get', str(temp_file)])
        
        if temp_file.exists():
            # Encrypt
            encrypted_path = self.encrypt_file(str(temp_file), password)
            
            # Delete temp
            temp_file.unlink()
            
            # Notification
            subprocess.run([
                'termux-notification',
                '--title', '🔐 Vault',
                '--content', 'File encrypted and stored',
                '--priority', 'low'
            ])
            
            return encrypted_path
            
        return None
        
    def list_vault(self) -> list:
        """List files in vault"""
        metadata = self._load_metadata()
        return [
            {'id': fid, **info}
            for fid, info in metadata['files'].items()
        ]

# Usage
vault = EncryptedVault()

# Initialize vault
vault.initialize_vault("my_secret_password")

# Import and encrypt file
vault.import_and_encrypt("my_secret_password")

# Decrypt file
vault.decrypt_file("~/vault/abc123.enc", "my_secret_password", 
                   "~/decrypted_photo.jpg")
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### ✅ Commands Learned
- [ ] `termux-storage-get` - Opens Android file picker
- [ ] `termux-share` - Shares files and text
- [ ] `termux-download` - Downloads files using system manager
- [ ] `termux-media-scan` - Registers files in MediaStore

### ✅ Concepts Understood
- [ ] Android Storage Access Framework integration
- [ ] Share Intent mechanism
- [ ] Download Manager service
- [ ] MediaStore and gallery visibility
- [ ] MIME types for content sharing
- [ ] Termux storage paths vs shared storage

### ✅ Skills Acquired
- [ ] File picking from Android storage
- [ ] Sharing files to other apps
- [ ] Background file downloads
- [ ] Making files visible in gallery
- [ ] Python integration for automation
- [ ] Bash scripting for file operations

### ✅ Practical Applications
- [ ] File backup automation
- [ ] Media organization scripts
- [ ] Secure file transfer systems
- [ ] Document scanning workflows
- [ ] Batch download management

### ✅ Best Practices
- [ ] Always check file permissions
- [ ] Use appropriate MIME types
- [ ] Handle errors gracefully
- [ ] Scan media files for gallery visibility
- [ ] Secure sensitive data before sharing

---

*Chapter 17 Complete! Ready for Chapter 18: Device Information APIs*
