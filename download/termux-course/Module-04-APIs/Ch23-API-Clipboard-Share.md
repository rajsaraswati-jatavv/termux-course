# Chapter 23: Termux API - Clipboard & Share

> **Module:** 4 - APIs  
> **Chapter:** 23 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Clipboard & Share API deep dive |
| Practical Scripts | Clipboard manager, Quick note, URL shortener |
| Commands Reference | All commands covered in chapter |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 23
Title: Termux Clipboard & Share API | Terminal se Share Karo! | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter ekdum practical aur useful hai - Clipboard aur Share API.

Sochein aap terminal mein kaam kar rahe ho, koi important text copy karna 
hai, ya koi file share karni hai WhatsApp pe, Telegram pe - sab terminal 
se hi kar sakte ho!

Bina phone ke bahar aaye, bina apps switch kiye - direct terminal se 
clipboard manage karo aur content share karo.

Is chapter mein hum seekhenge:
✓ Clipboard se text get aur set karna
✓ Files aur text share karna different apps mein
✓ Clipboard manager script banana
✓ Quick note taker script
✓ URL shortener with share feature
✓ Python integration for advanced features

Play button dabaiye, video like karein, aur channel subscribe karein!

---

[SECTION 1: CLIPBOARD API INTRODUCTION - 0:45 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samajhte hain Clipboard API kya hai.

Android mein clipboard ek temporary storage hota hai jahan copied text 
store hota hai. Jab aap kisi app mein text select karke "Copy" karte ho, 
wo clipboard mein jata hai. Phir "Paste" karke wapas la sakte ho.

Termux API aapko is clipboard ko programmatically control karne ki power 
deta hai - directly terminal se!

Do main commands hain:

1. termux-clipboard-get
   - Clipboard ka current content nikalta hai
   - Whatever text aapne copy kiya hai, wo dikhata hai

2. termux-clipboard-set
   - Clipboard mein naya text set karta hai
   - Jo text aap terminal se set karoge, wo kisi bhi app mein paste kar sakte ho

Yeh dono commands milke ek powerful combination banate hain. Imagine -
aap terminal mein koi command output generate karte ho, aur directly 
clipboard mein copy kar dete ho - bina mouse ya touch ke!

Prerequisites check karein:
- Termux:API app installed hona chahiye
- termux-api package install hona chahiye

Check karte hain:

    pkg list-installed | grep termux-api

Agar nahi hai to install karein:

    pkg install termux-api -y

---

[SECTION 2: TERMUX-CLIPBOARD-GET - 3:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Pehla command seekhte hain - clipboard content read karna.

Syntax bahut simple hai:

    termux-clipboard-get

Chaliye practical demo karte hain.

[DEMO: Basic clipboard get]

Pehle apne phone mein koi text copy karein - kisi bhi app se. 
Main "Hello Termux" copy kar raha hoon browser se.

Ab terminal mein command run karein:

    termux-clipboard-get

Output: Hello Termux

Dekha? Jo bhi clipboard mein hai, wo terminal pe aa gaya!

Ab ek interesting use case dekho - clipboard content ko file mein save karna:

    termux-clipboard-get > clipboard_content.txt

Ab file check karein:

    cat clipboard_content.txt

Ye useful hai jab aapko quick notes capture karne ho!

[DEMO: With other commands]

Clipboard content ko process bhi kar sakte ho:

    termux-clipboard-get | wc -w

Ye clipboard text mein kitne words hain, wo batayega.

    termux-clipboard-get | wc -c

Character count dega.

Uppercase mein convert:

    termux-clipboard-get | tr 'a-z' 'A-Z'

Lowercase mein convert:

    termux-clipboard-get | tr 'A-Z' 'a-z'

JSON format karna:

    termux-clipboard-get | python -m json.tool

Ye tab useful hai jab clipboard mein JSON data ho aur aap formatted dekhna chahte ho.

---

[SECTION 3: TERMUX-CLIPBOARD-SET - 6:00 to 9:30]
─────────────────────────────────────────────────────────────────────────────

Ab seekhte hain clipboard mein text set karna.

Basic syntax:

    termux-clipboard-set "Your text here"

[DEMO: Basic set]

    termux-clipboard-set "This is from Termux!"

Ab kisi bhi app mein jaake paste karein - WhatsApp, Notes, anywhere - 
ye text paste hoga!

Pipelines se bhi set kar sakte ho:

    echo "Generated at $(date)" | termux-clipboard-set

Ab clipboard mein timestamp wala text hoga.

Command output clipboard mein:

    date | termux-clipboard-set

    whoami | termux-clipboard-set

    pwd | termux-clipboard-set

[DEMO: File content to clipboard]

Kisi file ka content clipboard mein:

    cat ~/.bashrc | termux-clipboard-set

Ya specific lines:

    head -5 script.sh | termux-clipboard-set

[DEMO: Generate password and copy]

Random password generate karke clipboard mein:

    openssl rand -base64 12 | termux-clipboard-set

Ya Python se:

    python -c "import secrets; print(secrets.token_urlsafe(16))" | termux-clipboard-set

Ye bahut useful hai! Password generate, clipboard mein copy - ek command mein!

[DEMO: Combine get and set]

Clipboard content modify karna:

    termux-clipboard-get | tr 'a-z' 'A-Z' | termux-clipboard-set

Jo text clipboard mein tha, uppercase mein convert hoke wapas clipboard mein!

Ye ek powerful pattern hai:
get → process → set

---

[SECTION 4: TERMUX-SHARE API - 9:30 to 13:00]
─────────────────────────────────────────────────────────────────────────────

Ab aate hain Share API pe - ye ekdum amazing feature hai!

termux-share command aapko terminal se directly content share karne ki 
ability deta hai - WhatsApp, Telegram, Gmail, Bluetooth, anywhere!

Basic syntax:

    termux-share "Text to share"

[DEMO: Basic text share]

    termux-share "Hello from Termux Terminal!"

Jab ye command run karoge, Android ka share sheet open hoga with all 
available apps. Select karo jahan share karna hai!

[DEMO: Share with specific action]

Direct action ke saath share:

    termux-share -a send "Direct message"

-a flag action specify karta hai.

[DEMO: Share file]

File share karna:

    termux-share script.sh

Ya multiple files:

    termux-share file1.txt file2.txt

Image share:

    termux-share ~/storage/downloads/image.png

Screenshot share:

    termux-share /sdcard/Pictures/screenshot.png

[DEMO: Share with title]

Title ke saath share:

    termux-share -t "My Script" script.py

-t flag title set karta hai jo share sheet mein dikhega.

[DEMO: Share command output]

Command output directly share:

    df -h | termux-share

System info share:

    neofetch | termux-share

Log file share:

    cat /var/log/app.log | termux-share

[DEMO: Share to specific app type]

Content type specify:

    termux-share -c text/plain "Plain text content"

    termux-share -c image/jpeg photo.jpg

-c flag content type specify karta hai jo apps filter karne mein help karta hai.

---

[SECTION 5: CLIPBOARD MANAGER SCRIPT - 13:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek practical project banate hain - Clipboard Manager!

Ye script:
- Multiple clipboard entries store karega
- History maintain karega
- Quick access dega previous clips

Script likhte hain:

    nano ~/clipboard-manager.sh

```bash
#!/bin/bash
# Clipboard Manager by T3rmuxk1ng

HISTORY_FILE="$HOME/.clipboard_history"
MAX_HISTORY=20

show_menu() {
    clear
    echo "╔══════════════════════════════════════╗"
    echo "║     CLIPBOARD MANAGER v1.0           ║"
    echo "║          by T3rmuxk1ng               ║"
    echo "╠══════════════════════════════════════╣"
    echo "║  1. View Current Clipboard           ║"
    echo "║  2. Copy from History                ║"
    echo "║  3. Add to History                   ║"
    echo "║  4. View History                     ║"
    echo "║  5. Clear History                    ║"
    echo "║  6. Share Clipboard                  ║"
    echo "║  7. Exit                             ║"
    echo "╚══════════════════════════════════════╝"
}

view_clipboard() {
    echo -e "\n📋 Current Clipboard Content:"
    echo "─────────────────────────────"
    termux-clipboard-get
    echo ""
}

add_to_history() {
    local content=$(termux-clipboard-get)
    if [ -n "$content" ]; then
        echo "$(date '+%Y-%m-%d %H:%M'): $content" >> "$HISTORY_FILE"
        # Keep only last MAX_HISTORY entries
        tail -n $MAX_HISTORY "$HISTORY_FILE" > "$HISTORY_FILE.tmp"
        mv "$HISTORY_FILE.tmp" "$HISTORY_FILE"
        echo "✅ Added to history!"
    else
        echo "❌ Clipboard is empty!"
    fi
}

view_history() {
    echo -e "\n📜 Clipboard History:"
    echo "─────────────────────────────"
    if [ -f "$HISTORY_FILE" ]; then
        nl -w2 -s'. ' "$HISTORY_FILE"
    else
        echo "History is empty"
    fi
}

copy_from_history() {
    view_history
    echo -e "\nEnter number to copy: "
    read -r num
    local content=$(sed -n "${num}p" "$HISTORY_FILE" | cut -d: -f2-)
    if [ -n "$content" ]; then
        echo "$content" | termux-clipboard-set
        echo "✅ Copied to clipboard!"
    else
        echo "❌ Invalid selection!"
    fi
}

clear_history() {
    rm -f "$HISTORY_FILE"
    echo "✅ History cleared!"
}

share_clipboard() {
    local content=$(termux-clipboard-get)
    if [ -n "$content" ]; then
        termux-share "$content"
    else
        echo "❌ Clipboard is empty!"
    fi
}

# Main loop
while true; do
    show_menu
    read -p "Enter choice: " choice
    case $choice in
        1) view_clipboard ;;
        2) copy_from_history ;;
        3) add_to_history ;;
        4) view_history ;;
        5) clear_history ;;
        6) share_clipboard ;;
        7) echo "Goodbye!"; exit 0 ;;
        *) echo "Invalid choice!" ;;
    esac
    read -p "Press Enter to continue..."
done
```

Script ko executable banayein:

    chmod +x ~/clipboard-manager.sh

Run karein:

    ./clipboard-manager.sh

Ye ek complete clipboard manager hai terminal mein!

---

[SECTION 6: QUICK NOTE SCRIPT - 16:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ek aur useful script - Quick Note Taker with share feature!

    nano ~/quick-note.sh

```bash
#!/bin/bash
# Quick Note Taker by T3rmuxk1ng

NOTES_DIR="$HOME/quick_notes"
mkdir -p "$NOTES_DIR"

quick_note() {
    echo "📝 Enter your note (Ctrl+D to finish):"
    local note=$(cat)
    local timestamp=$(date '+%Y%m%d_%H%M%S')
    local filename="note_${timestamp}.txt"
    
    echo "$note" > "$NOTES_DIR/$filename"
    echo "✅ Note saved: $filename"
    
    # Also copy to clipboard
    echo "$note" | termux-clipboard-set
    echo "📋 Note copied to clipboard!"
    
    # Ask to share
    read -p "Share this note? (y/n): " share
    if [ "$share" = "y" ]; then
        termux-share "$note"
    fi
}

view_notes() {
    echo "📚 Your Notes:"
    echo "─────────────────────────────"
    ls -lt "$NOTES_DIR" | head -10
}

share_note() {
    view_notes
    read -p "Enter note filename: " filename
    if [ -f "$NOTES_DIR/$filename" ]; then
        termux-share "$NOTES_DIR/$filename"
    else
        echo "❌ Note not found!"
    fi
}

# Main
case "$1" in
    "list") view_notes ;;
    "share") share_note ;;
    *) quick_note ;;
esac
```

Use karein:

    ./quick-note.sh         # New note
    ./quick-note.sh list    # List notes
    ./quick-note.sh share   # Share a note

---

[SECTION 7: URL SHORTENER + SHARE - 18:00 to 20:30]
─────────────────────────────────────────────────────────────────────────────

Ab ek advanced script - URL Shortener with automatic share!

Pehle requirements:

    pkg install curl jq -y

Script banate hain:

    nano ~/url-shorten.sh

```bash
#!/bin/bash
# URL Shortener + Share by T3rmuxk1ng

SHORTEN_API="https://is.gd/create.php?format=json&url="

shorten_url() {
    local url="$1"
    local response=$(curl -s "${SHORTEN_API}${url}")
    
    if echo "$response" | jq -e '.shorturl' > /dev/null 2>&1; then
        local short=$(echo "$response" | jq -r '.shorturl')
        echo "$short"
    else
        echo "Error: Could not shorten URL"
        return 1
    fi
}

# Get URL from argument or clipboard
if [ -n "$1" ]; then
    url="$1"
else
    url=$(termux-clipboard-get)
    echo "📋 Using URL from clipboard: $url"
fi

echo "⏳ Shortening URL..."
short_url=$(shorten_url "$url")

if [ $? -eq 0 ]; then
    echo "✅ Shortened: $short_url"
    
    # Copy to clipboard
    echo "$short_url" | termux-clipboard-set
    echo "📋 Copied to clipboard!"
    
    # Ask to share
    read -p "Share shortened URL? (y/n): " share
    if [ "$share" = "y" ]; then
        termux-share "$short_url"
    fi
fi
```

Use karein:

    ./url-shorten.sh https://very-long-url.com/path/to/something

Ya clipboard se URL le:

    ./url-shorten.sh

---

[SECTION 8: PYTHON INTEGRATION - 20:30 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Ab Python se clipboard aur share APIs use karna seekhte hain.

Python script:

    nano ~/clip_tools.py

```python
#!/usr/bin/env python3
"""Clipboard & Share Tools by T3rmuxk1ng"""

import subprocess
import json
from datetime import datetime

def get_clipboard():
    """Get current clipboard content"""
    result = subprocess.run(
        ['termux-clipboard-get'],
        capture_output=True,
        text=True
    )
    return result.stdout.strip()

def set_clipboard(text):
    """Set clipboard content"""
    subprocess.run(
        ['termux-clipboard-set', text],
        capture_output=True
    )
    return True

def share_content(content, title=None):
    """Share content via Android share sheet"""
    cmd = ['termux-share']
    if title:
        cmd.extend(['-t', title])
    cmd.append(content)
    subprocess.run(cmd)

def share_file(filepath):
    """Share a file"""
    subprocess.run(['termux-share', filepath])

def clipboard_history_manager():
    """Manage clipboard history"""
    history_file = "clipboard_history.json"
    
    try:
        with open(history_file, 'r') as f:
            history = json.load(f)
    except:
        history = []
    
    return history

def save_to_history(content):
    """Save clipboard content to history"""
    history_file = "clipboard_history.json"
    
    try:
        with open(history_file, 'r') as f:
            history = json.load(f)
    except:
        history = []
    
    history.append({
        'content': content,
        'timestamp': datetime.now().isoformat()
    })
    
    # Keep last 50 entries
    history = history[-50:]
    
    with open(history_file, 'w') as f:
        json.dump(history, f, indent=2)

# Demo usage
if __name__ == "__main__":
    import sys
    
    if len(sys.argv) < 2:
        print("Usage: python clip_tools.py [get|set|share|history]")
        sys.exit(1)
    
    command = sys.argv[1]
    
    if command == "get":
        print(get_clipboard())
    
    elif command == "set":
        if len(sys.argv) > 2:
            set_clipboard(' '.join(sys.argv[2:]))
            print("✅ Clipboard updated!")
        else:
            text = sys.stdin.read()
            set_clipboard(text)
            print("✅ Clipboard updated!")
    
    elif command == "share":
        content = get_clipboard() if len(sys.argv) == 2 else ' '.join(sys.argv[2:])
        share_content(content)
    
    elif command == "history":
        save_to_history(get_clipboard())
        print("✅ Saved to history!")
```

Use karein:

    python clip_tools.py get           # Get clipboard
    python clip_tools.py set "Hello"   # Set clipboard
    python clip_tools.py share         # Share clipboard
    python clip_tools.py history       # Save to history

---

[SECTION 9: PRACTICAL EXAMPLES COLLECTION - 23:00 to 26:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab 15+ practical examples dekho jo daily use mein kaam aayenge:

[EXAMPLE 1: Copy command output]

    ls -la | termux-clipboard-set

[EXAMPLE 2: Share system info]

    neofetch | termux-share

[EXAMPLE 3: Copy WiFi password]

    termux-wifi-connectioninfo | jq -r '.password' | termux-clipboard-set

[EXAMPLE 4: Generate and copy UUID]

    python -c "import uuid; print(uuid.uuid4())" | termux-clipboard-set

[EXAMPLE 5: Share file with specific app]

    termux-share -t "Important Document" report.pdf

[EXAMPLE 6: Copy IP address]

    curl -s ifconfig.me | termux-clipboard-set

[EXAMPLE 7: Share current directory listing]

    ls -la | termux-share

[EXAMPLE 8: Copy git branch name]

    git branch --show-current | termux-clipboard-set

[EXAMPLE 9: Share command history]

    history | tail -20 | termux-share

[EXAMPLE 10: Copy formatted date]

    date '+%Y-%m-%d %H:%M:%S' | termux-clipboard-set

[EXAMPLE 11: Share disk usage]

    df -h | termux-share

[EXAMPLE 12: Copy base64 encoded text]

    echo "Secret Message" | base64 | termux-clipboard-set

[EXAMPLE 13: Share code snippet]

    cat script.py | termux-share

[EXAMPLE 14: Copy QR code data]

    qrencode -t UTF8 "https://example.com" | termux-clipboard-set

[EXAMPLE 15: Share multiple files]

    termux-share photo1.jpg photo2.jpg photo3.jpg

[EXAMPLE 16: Copy SHA256 hash]

    sha256sum file.txt | cut -d' ' -f1 | termux-clipboard-set

[EXAMPLE 17: Quick note with timestamp]

    echo "Note: $(date '+%H:%M') - $1" | termux-clipboard-set

---

[SECTION 10: SUMMARY & NEXT PREVIEW - 26:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 23 complete! Let's summarize:

✅ Clipboard API - get aur set commands
✅ Share API - text aur files share karna
✅ Clipboard Manager script - complete solution
✅ Quick Note Taker - notes with share feature
✅ URL Shortener - automatic shortening with share
✅ Python integration - programmatic access
✅ 17 practical examples - daily use cases

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 23 - IMPORTANT COMMANDS                        │
├─────────────────────────────────────────────────────────────────────────┤
│ termux-clipboard-get              │ Read clipboard content              │
│ termux-clipboard-set "text"       │ Set clipboard content               │
│ termux-share "text"               │ Share text via share sheet          │
│ termux-share file.txt             │ Share a file                        │
│ termux-share -t "Title" file      │ Share with title                    │
│ termux-share -c type file         │ Share with content type             │
│ echo "text" | termux-clipboard-set│ Pipe to clipboard                   │
│ termux-clipboard-get | process    │ Process clipboard content           │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 24 mein hum seekhenge:
- Termux Notification API
- Custom notifications create karna
- Notification with actions
- Progress notifications
- Notification channels

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 24!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Clipboard API Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX CLIPBOARD API FLOW                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────┐    termux-clipboard-get    ┌─────────────────┐   │
│   │   Android       │ ─────────────────────────▶ │   Termux        │   │
│   │   Clipboard     │                            │   Terminal      │   │
│   │   (System)      │ ◀───────────────────────── │   Output        │   │
│   └─────────────────┘    termux-clipboard-set    └─────────────────┘   │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     Share Flow                                   │   │
│   │                                                                   │   │
│   │   Termux ──▶ termux-share ──▶ Android Share Sheet ──▶ App      │   │
│   │                                                                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. termux-clipboard-get

The `termux-clipboard-get` command retrieves the current clipboard content.

**Syntax:**
```bash
termux-clipboard-get
```

**Options:**
- No options required - simply outputs clipboard content

**Return Value:**
- Exit code 0 on success
- Exit code 1 on failure

**Usage Examples:**

```bash
# Basic get
termux-clipboard-get

# Save to file
termux-clipboard-get > saved_text.txt

# Process the content
termux-clipboard-get | wc -w           # Word count
termux-clipboard-get | grep "pattern"  # Search pattern
termux-clipboard-get | sort            # Sort lines

# Use in scripts
content=$(termux-clipboard-get)
echo "Clipboard contains: $content"

# Check if clipboard has content
if [ -n "$(termux-clipboard-get)" ]; then
    echo "Clipboard is not empty"
fi

# Convert format
termux-clipboard-get | tr 'a-z' 'A-Z'   # Uppercase
termux-clipboard-get | tr 'A-Z' 'a-z'   # Lowercase
termux-clipboard-get | base64 -d        # Decode base64
```

### 3. termux-clipboard-set

The `termux-clipboard-set` command sets new content to the clipboard.

**Syntax:**
```bash
termux-clipboard-set [text]
```

**Input Methods:**
1. Direct argument: `termux-clipboard-set "text"`
2. Pipe: `echo "text" | termux-clipboard-set`
3. File: `cat file | termux-clipboard-set`

**Usage Examples:**

```bash
# Basic set
termux-clipboard-set "Hello World"

# From command output
date | termux-clipboard-set
whoami | termux-clipboard-set
pwd | termux-clipboard-set

# From file
cat script.py | termux-clipboard-set

# Multi-line text
cat << EOF | termux-clipboard-set
Line 1
Line 2
Line 3
EOF

# Generated content
openssl rand -base64 16 | termux-clipboard-set  # Random string
uuidgen | termux-clipboard-set                   # UUID
date '+%s' | termux-clipboard-set                # Timestamp

# From Python
python -c "import secrets; print(secrets.token_urlsafe(20))" | termux-clipboard-set
```

### 4. termux-share

The `termux-share` command shares content through Android's share sheet.

**Syntax:**
```bash
termux-share [options] [content|file...]
```

**Options:**

| Option | Description |
|--------|-------------|
| `-a, --action` | Action to perform (send/view/edit) |
| `-c, --content-type` | MIME type of content |
| `-d, --default` | Use default send action |
| `-t, --title` | Title for share sheet |
| `-e, --edit` | Open in edit mode |

**Content Types:**

| Type | MIME |
|------|------|
| Text | text/plain |
| HTML | text/html |
| Image | image/jpeg, image/png |
| Video | video/mp4 |
| File | application/octet-stream |

**Usage Examples:**

```bash
# Share text
termux-share "Check out this cool thing!"

# Share with title
termux-share -t "Important Message" "Don't forget!"

# Share file
termux-share document.pdf
termux-share ~/storage/downloads/photo.jpg

# Share command output
df -h | termux-share
neofetch | termux-share

# Share with content type
termux-share -c text/html "<h1>Hello</h1>"

# Share multiple files
termux-share file1.txt file2.txt file3.txt

# Share from clipboard
termux-clipboard-get | termux-share
```

### 5. Share to Specific Apps

While `termux-share` opens the system share sheet, you can create shortcuts for specific apps:

```bash
# Function to share to WhatsApp
share_whatsapp() {
    am start -a android.intent.action.SEND \
        -t text/plain \
        --es android.intent.extra.TEXT "$1" \
        com.whatsapp
}

# Function to share to Telegram
share_telegram() {
    am start -a android.intent.action.SEND \
        -t text/plain \
        --es android.intent.extra.TEXT "$1" \
        org.telegram.messenger
}

# Function to share to Gmail
share_gmail() {
    am start -a android.intent.action.SEND \
        -t text/plain \
        --es android.intent.extra.TEXT "$1" \
        com.google.android.gm
}

# Usage
share_whatsapp "Hello from Termux!"
share_telegram "Check this out!"
```

### 6. Clipboard Manager Script (Complete)

```bash
#!/bin/bash
# Advanced Clipboard Manager by T3rmuxk1ng
# Version: 2.0

CONFIG_DIR="$HOME/.clipboard_manager"
HISTORY_FILE="$CONFIG_DIR/history.json"
PINNED_FILE="$CONFIG_DIR/pinned.txt"
MAX_HISTORY=50

# Initialize
mkdir -p "$CONFIG_DIR"
[ ! -f "$HISTORY_FILE" ] && echo "[]" > "$HISTORY_FILE"
[ ! -f "$PINNED_FILE" ] && touch "$PINNED_FILE"

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m'

show_banner() {
    clear
    echo -e "${BLUE}╔════════════════════════════════════════╗${NC}"
    echo -e "${BLUE}║      CLIPBOARD MANAGER v2.0            ║${NC}"
    echo -e "${BLUE}║          by T3rmuxk1ng                 ║${NC}"
    echo -e "${BLUE}╠════════════════════════════════════════╣${NC}"
    echo -e "${BLUE}║  1.${NC} View Current Clipboard            ${BLUE}║${NC}"
    echo -e "${BLUE}║  2.${NC} Copy to Clipboard                 ${BLUE}║${NC}"
    echo -e "${BLUE}║  3.${NC} View History                      ${BLUE}║${NC}"
    echo -e "${BLUE}║  4.${NC} Restore from History               ${BLUE}║${NC}"
    echo -e "${BLUE}║  5.${NC} Pin Current Clipboard              ${BLUE}║${NC}"
    echo -e "${BLUE}║  6.${NC} View Pinned Items                  ${BLUE}║${NC}"
    echo -e "${BLUE}║  7.${NC} Share Clipboard                    ${BLUE}║${NC}"
    echo -e "${BLUE}║  8.${NC} Search History                     ${BLUE}║${NC}"
    echo -e "${BLUE}║  9.${NC} Clear History                      ${BLUE}║${NC}"
    echo -e "${BLUE}║  0.${NC} Exit                              ${BLUE}║${NC}"
    echo -e "${BLUE}╚════════════════════════════════════════╝${NC}"
}

get_current_clipboard() {
    termux-clipboard-get 2>/dev/null
}

set_clipboard() {
    echo -n "$1" | termux-clipboard-set
}

add_to_history() {
    local content="$1"
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    
    python3 << EOF
import json
with open("$HISTORY_FILE", "r") as f:
    data = json.load(f)
data.insert(0, {"content": """$content""", "time": "$timestamp"})
data = data[:$MAX_HISTORY]
with open("$HISTORY_FILE", "w") as f:
    json.dump(data, f, indent=2)
EOF
}

view_clipboard() {
    echo -e "\n${GREEN}📋 Current Clipboard Content:${NC}"
    echo "────────────────────────────────"
    local content=$(get_current_clipboard)
    if [ -n "$content" ]; then
        echo "$content"
        echo ""
        echo "Characters: $(echo -n "$content" | wc -c)"
        echo "Words: $(echo "$content" | wc -w)"
        echo "Lines: $(echo "$content" | wc -l)"
    else
        echo -e "${RED}Empty${NC}"
    fi
}

copy_to_clipboard() {
    echo -e "\n${YELLOW}Enter text (Ctrl+D to finish):${NC}"
    local text=$(cat)
    if [ -n "$text" ]; then
        set_clipboard "$text"
        add_to_history "$text"
        echo -e "${GREEN}✅ Copied and added to history!${NC}"
    fi
}

view_history() {
    echo -e "\n${GREEN}📜 Clipboard History:${NC}"
    echo "────────────────────────────────"
    python3 << 'EOF'
import json
try:
    with open("$HISTORY_FILE", "r") as f:
        data = json.load(f)
    for i, item in enumerate(data[:20], 1):
        content = item["content"][:50] + "..." if len(item["content"]) > 50 else item["content"]
        content = content.replace("\n", "\\n")
        print(f"{i:2d}. [{item['time']}] {content}")
except:
    print("History is empty")
EOF
}

restore_from_history() {
    view_history
    echo -e "\n${YELLOW}Enter number to restore:${NC}"
    read -r num
    local content=$(python3 -c "
import json
with open('$HISTORY_FILE', 'r') as f:
    data = json.load(f)
if 0 < $num <= len(data):
    print(data[$num-1]['content'])
")
    if [ -n "$content" ]; then
        set_clipboard "$content"
        echo -e "${GREEN}✅ Restored to clipboard!${NC}"
    else
        echo -e "${RED}❌ Invalid selection${NC}"
    fi
}

pin_clipboard() {
    local content=$(get_current_clipboard)
    if [ -n "$content" ]; then
        echo "$(date '+%Y-%m-%d %H:%M'): $content" >> "$PINNED_FILE"
        echo -e "${GREEN}✅ Pinned!${NC}"
    else
        echo -e "${RED}❌ Clipboard is empty${NC}"
    fi
}

view_pinned() {
    echo -e "\n${GREEN}📌 Pinned Items:${NC}"
    echo "────────────────────────────────"
    if [ -s "$PINNED_FILE" ]; then
        nl -w2 -s'. ' "$PINNED_FILE"
    else
        echo "No pinned items"
    fi
}

share_clipboard() {
    local content=$(get_current_clipboard)
    if [ -n "$content" ]; then
        termux-share "$content"
    else
        echo -e "${RED}❌ Clipboard is empty${NC}"
    fi
}

search_history() {
    echo -e "\n${YELLOW}Enter search term:${NC}"
    read -r term
    echo -e "\n${GREEN}Search Results:${NC}"
    python3 << EOF
import json
with open("$HISTORY_FILE", "r") as f:
    data = json.load(f)
for i, item in enumerate(data):
    if "$term".lower() in item["content"].lower():
        content = item["content"][:60]
        print(f"{i+1}. {content}")
EOF
}

clear_history() {
    echo "[]" > "$HISTORY_FILE"
    echo -e "${GREEN}✅ History cleared${NC}"
}

# Main
while true; do
    show_banner
    read -p "Choice: " choice
    case $choice in
        1) view_clipboard ;;
        2) copy_to_clipboard ;;
        3) view_history ;;
        4) restore_from_history ;;
        5) pin_clipboard ;;
        6) view_pinned ;;
        7) share_clipboard ;;
        8) search_history ;;
        9) clear_history ;;
        0) echo "Goodbye!"; exit 0 ;;
        *) echo -e "${RED}Invalid choice${NC}" ;;
    esac
    read -p "Press Enter..."
done
```

### 7. Quick Note Script (Complete)

```bash
#!/bin/bash
# Quick Note Taker with Share by T3rmuxk1ng

NOTES_DIR="$HOME/notes"
TEMPLATE_DIR="$NOTES_DIR/templates"
mkdir -p "$NOTES_DIR" "$TEMPLATE_DIR"

# Colors
GREEN='\033[0;32m'
BLUE='\033[0;34m'
YELLOW='\033[1;33m'
NC='\033[0m'

new_note() {
    local timestamp=$(date '+%Y%m%d_%H%M%S')
    local filename="${1:-note}_${timestamp}.txt"
    local filepath="$NOTES_DIR/$filename"
    
    echo -e "${BLUE}📝 Quick Note (Ctrl+D to save)${NC}"
    echo "──────────────────────────────"
    
    # Add timestamp header
    echo "# Note created: $(date '+%Y-%m-%d %H:%M:%S')" > "$filepath"
    echo "# Tags: " >> "$filepath"
    echo "" >> "$filepath"
    
    # Add template if exists
    if [ -f "$TEMPLATE_DIR/default.txt" ]; then
        cat "$TEMPLATE_DIR/default.txt" >> "$filepath"
    fi
    
    # Read user input
    cat >> "$filepath"
    
    echo -e "\n${GREEN}✅ Saved: $filepath${NC}"
    
    # Copy to clipboard
    tail -n +4 "$filepath" | termux-clipboard-set
    echo -e "${GREEN}📋 Content copied to clipboard${NC}"
    
    # Share option
    read -p "Share this note? (y/n): " share
    [ "$share" = "y" ] && termux-share "$filepath"
}

list_notes() {
    echo -e "${GREEN}📚 Your Notes:${NC}"
    echo "──────────────────────────────"
    ls -lt "$NOTES_DIR"/*.txt 2>/dev/null | head -20 || echo "No notes yet"
}

view_note() {
    list_notes
    read -p "Enter filename: " filename
    [ -f "$NOTES_DIR/$filename" ] && cat "$NOTES_DIR/$filename" || echo "Not found"
}

share_note() {
    list_notes
    read -p "Enter filename: " filename
    local filepath="$NOTES_DIR/$filename"
    [ -f "$filepath" ] && termux-share "$filepath" || echo "Not found"
}

delete_note() {
    list_notes
    read -p "Enter filename to delete: " filename
    local filepath="$NOTES_DIR/$filename"
    if [ -f "$filepath" ]; then
        rm "$filepath"
        echo "✅ Deleted"
    fi
}

search_notes() {
    read -p "Search term: " term
    echo -e "${GREEN}Results:${NC}"
    grep -r "$term" "$NOTES_DIR"/*.txt 2>/dev/null || echo "No matches"
}

quick_clipboard_note() {
    local content=$(termux-clipboard-get)
    if [ -n "$content" ]; then
        local filename="clip_$(date '+%Y%m%d_%H%M%S').txt"
        echo "$content" > "$NOTES_DIR/$filename"
        echo "✅ Saved clipboard to: $filename"
    else
        echo "❌ Clipboard is empty"
    fi
}

# Main
case "${1:-new}" in
    new) new_note "$2" ;;
    list|ls) list_notes ;;
    view) view_note ;;
    share) share_note ;;
    delete|rm) delete_note ;;
    search) search_notes ;;
    clip) quick_clipboard_note ;;
    *)
        echo "Usage: $0 {new|list|view|share|delete|search|clip}"
        ;;
esac
```

### 8. URL Shortener + Share Script

```bash
#!/bin/bash
# URL Shortener with Share by T3rmuxk1ng
# Supports multiple services

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m'

shorten_isgd() {
    local url="$1"
    local response=$(curl -s "https://is.gd/create.php?format=json&url=${url}")
    echo "$response" | jq -r '.shorturl' 2>/dev/null
}

shorten_vgd() {
    local url="$1"
    local response=$(curl -s "https://v.gd/create.php?format=json&url=${url}")
    echo "$response" | jq -r '.shorturl' 2>/dev/null
}

shorten_tinyurl() {
    local url="$1"
    curl -s "https://tinyurl.com/api-create.php?url=${url}"
}

shorten_cleanuri() {
    local url="$1"
    curl -s -X POST "https://cleanuri.com/api/v1/shorten" \
        -d "url=${url}" | jq -r '.result_url' 2>/dev/null
}

get_url() {
    if [ -n "$1" ]; then
        echo "$1"
    else
        local clip=$(termux-clipboard-get)
        if [[ "$clip" =~ ^https?:// ]]; then
            echo "$clip"
        else
            echo ""
        fi
    fi
}

# Get URL
url=$(get_url "$1")

if [ -z "$url" ]; then
    echo -e "${RED}❌ No valid URL found${NC}"
    echo "Usage: $0 [URL]"
    echo "   or: Copy URL to clipboard and run"
    exit 1
fi

echo -e "${GREEN}Original URL:${NC} $url"
echo -e "${YELLOW}⏳ Shortening...${NC}"

# Try services in order
short_url=$(shorten_isgd "$url")

if [ -z "$short_url" ] || [[ "$short_url" == "null" ]]; then
    short_url=$(shorten_tinyurl "$url")
fi

if [ -n "$short_url" ] && [[ "$short_url" != "null" ]]; then
    echo -e "${GREEN}✅ Shortened:${NC} $short_url"
    
    # Copy to clipboard
    echo -n "$short_url" | termux-clipboard-set
    echo -e "${GREEN}📋 Copied to clipboard${NC}"
    
    # Share option
    read -p "Share? (y/n): " share
    [ "$share" = "y" ] && termux-share "$short_url"
else
    echo -e "${RED}❌ Could not shorten URL${NC}"
fi
```

### 9. Python Integration Module

```python
#!/usr/bin/env python3
"""
Termux Clipboard & Share Integration
Complete Python module by T3rmuxk1ng
"""

import subprocess
import json
import os
from datetime import datetime
from typing import Optional, List, Dict
from pathlib import Path


class ClipboardManager:
    """Manage Android clipboard from Python"""
    
    def __init__(self, history_file: str = None):
        self.history_file = history_file or os.path.expanduser(
            "~/.clipboard_history.json"
        )
        self._ensure_history_file()
    
    def _ensure_history_file(self):
        """Create history file if not exists"""
        if not os.path.exists(self.history_file):
            with open(self.history_file, 'w') as f:
                json.dump([], f)
    
    def get(self) -> str:
        """Get current clipboard content"""
        result = subprocess.run(
            ['termux-clipboard-get'],
            capture_output=True,
            text=True
        )
        return result.stdout.strip()
    
    def set(self, content: str) -> bool:
        """Set clipboard content"""
        try:
            subprocess.run(
                ['termux-clipboard-set'],
                input=content,
                capture_output=True,
                text=True
            )
            return True
        except Exception as e:
            print(f"Error: {e}")
            return False
    
    def share(self, content: str, title: str = None) -> bool:
        """Share content via Android share sheet"""
        try:
            cmd = ['termux-share']
            if title:
                cmd.extend(['-t', title])
            cmd.append(content)
            subprocess.run(cmd)
            return True
        except Exception as e:
            print(f"Error: {e}")
            return False
    
    def share_file(self, filepath: str) -> bool:
        """Share a file"""
        try:
            subprocess.run(['termux-share', filepath])
            return True
        except Exception as e:
            print(f"Error: {e}")
            return False
    
    def get_history(self) -> List[Dict]:
        """Get clipboard history"""
        try:
            with open(self.history_file, 'r') as f:
                return json.load(f)
        except:
            return []
    
    def save_to_history(self, content: str = None, max_items: int = 50):
        """Save current clipboard to history"""
        content = content or self.get()
        if not content:
            return
        
        history = self.get_history()
        history.insert(0, {
            'content': content,
            'timestamp': datetime.now().isoformat(),
            'length': len(content)
        })
        
        # Trim to max items
        history = history[:max_items]
        
        with open(self.history_file, 'w') as f:
            json.dump(history, f, indent=2)
    
    def restore_from_history(self, index: int) -> bool:
        """Restore item from history to clipboard"""
        history = self.get_history()
        if 0 <= index < len(history):
            return self.set(history[index]['content'])
        return False
    
    def search_history(self, query: str) -> List[Dict]:
        """Search clipboard history"""
        history = self.get_history()
        return [
            item for item in history 
            if query.lower() in item['content'].lower()
        ]
    
    def clear_history(self):
        """Clear all history"""
        with open(self.history_file, 'w') as f:
            json.dump([], f)


class QuickNote:
    """Quick note taking with clipboard integration"""
    
    def __init__(self, notes_dir: str = None):
        self.notes_dir = Path(notes_dir or os.path.expanduser("~/notes"))
        self.notes_dir.mkdir(parents=True, exist_ok=True)
        self.clipboard = ClipboardManager()
    
    def create(self, content: str = None, tags: List[str] = None) -> str:
        """Create a new note"""
        content = content or self.clipboard.get()
        if not content:
            raise ValueError("No content to save")
        
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        filename = f"note_{timestamp}.txt"
        filepath = self.notes_dir / filename
        
        note_content = f"""# Note: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}
# Tags: {', '.join(tags or [])}

{content}
"""
        with open(filepath, 'w') as f:
            f.write(note_content)
        
        return str(filepath)
    
    def list_notes(self, limit: int = 20) -> List[Dict]:
        """List all notes"""
        notes = []
        for note_file in sorted(
            self.notes_dir.glob("*.txt"), 
            key=os.path.getmtime, 
            reverse=True
        )[:limit]:
            notes.append({
                'path': str(note_file),
                'name': note_file.name,
                'modified': datetime.fromtimestamp(
                    note_file.stat().st_mtime
                ).isoformat()
            })
        return notes
    
    def share(self, filename: str):
        """Share a note"""
        filepath = self.notes_dir / filename
        if filepath.exists():
            self.clipboard.share_file(str(filepath))


class URLShortener:
    """URL shortening with clipboard integration"""
    
    def __init__(self):
        self.clipboard = ClipboardManager()
    
    def shorten_isgd(self, url: str) -> Optional[str]:
        """Shorten using is.gd"""
        import urllib.request
        import urllib.parse
        
        api_url = f"https://is.gd/create.php?format=json&url={urllib.parse.quote(url)}"
        try:
            with urllib.request.urlopen(api_url) as response:
                data = json.loads(response.read())
                return data.get('shorturl')
        except:
            return None
    
    def shorten_tinyurl(self, url: str) -> Optional[str]:
        """Shorten using TinyURL"""
        import urllib.request
        import urllib.parse
        
        api_url = f"https://tinyurl.com/api-create.php?url={urllib.parse.quote(url)}"
        try:
            with urllib.request.urlopen(api_url) as response:
                return response.read().decode()
        except:
            return None
    
    def shorten(self, url: str = None, copy: bool = True) -> Optional[str]:
        """Shorten URL"""
        url = url or self.clipboard.get()
        
        if not url or not url.startswith(('http://', 'https://')):
            print("Invalid URL")
            return None
        
        # Try services
        short_url = self.shorten_isgd(url)
        if not short_url:
            short_url = self.shorten_tinyurl(url)
        
        if short_url and copy:
            self.clipboard.set(short_url)
        
        return short_url


# CLI interface
if __name__ == "__main__":
    import sys
    
    def print_help():
        print("""
Termux Clipboard Tools by T3rmuxk1ng

Usage:
    python clip_tools.py get                  Get clipboard content
    python clip_tools.py set "text"           Set clipboard
    python clip_tools.py share                Share clipboard content
    python clip_tools.py share "text"         Share text
    python clip_tools.py history              Show clipboard history
    python clip_tools.py note                 Create note from clipboard
    python clip_tools.py shorten              Shorten URL from clipboard
    python clip_tools.py shorten "url"        Shorten specific URL
""")
    
    if len(sys.argv) < 2:
        print_help()
        sys.exit(1)
    
    cmd = sys.argv[1]
    cm = ClipboardManager()
    
    if cmd == "get":
        print(cm.get())
    
    elif cmd == "set":
        text = sys.argv[2] if len(sys.argv) > 2 else sys.stdin.read()
        cm.set(text)
        print("✅ Clipboard updated")
    
    elif cmd == "share":
        content = sys.argv[2] if len(sys.argv) > 2 else cm.get()
        cm.share(content)
    
    elif cmd == "history":
        for i, item in enumerate(cm.get_history()[:10]):
            preview = item['content'][:50] + "..."
            print(f"{i+1}. {preview}")
    
    elif cmd == "note":
        note = QuickNote()
        path = note.create()
        print(f"✅ Note created: {path}")
    
    elif cmd == "shorten":
        url = sys.argv[2] if len(sys.argv) > 2 else None
        shortener = URLShortener()
        result = shortener.shorten(url)
        if result:
            print(f"✅ Shortened: {result}")
        else:
            print("❌ Failed to shorten")
    
    else:
        print_help()
```

---

## 📋 COMMANDS REFERENCE

### Clipboard Commands

```bash
# Get clipboard content
termux-clipboard-get

# Set clipboard content
termux-clipboard-set "Your text here"

# Set from pipe
echo "Text from command" | termux-clipboard-set

# Set from file
cat file.txt | termux-clipboard-set

# Get and save to file
termux-clipboard-get > saved.txt

# Get and process
termux-clipboard-get | wc -w                    # Word count
termux-clipboard-get | tr 'a-z' 'A-Z'           # Uppercase
termux-clipboard-get | grep "pattern"           # Search
termux-clipboard-get | base64                   # Encode

# Transform and set back
termux-clipboard-get | tr 'a-z' 'A-Z' | termux-clipboard-set
```

### Share Commands

```bash
# Share text
termux-share "Hello World"

# Share file
termux-share document.pdf

# Share with title
termux-share -t "Important Document" file.txt

# Share with content type
termux-share -c text/plain "text content"
termux-share -c image/jpeg photo.jpg

# Share command output
df -h | termux-share
neofetch | termux-share
cat log.txt | termux-share

# Share multiple files
termux-share file1.txt file2.txt file3.txt

# Share from clipboard
termux-clipboard-get | termux-share
```

### Combined Workflows

```bash
# Generate password and copy
openssl rand -base64 16 | termux-clipboard-set

# Get IP and share
curl -s ifconfig.me | termux-share

# Copy git status
git status | termux-clipboard-set

# Share directory listing
ls -la | termux-share

# Copy timestamp
date '+%Y-%m-%d %H:%M:%S' | termux-clipboard-set

# Generate UUID and copy
python -c "import uuid; print(uuid.uuid4())" | termux-clipboard-set

# Copy file hash
sha256sum file.txt | cut -d' ' -f1 | termux-clipboard-set
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Clipboard Operations

```bash
# Task: Master clipboard get and set

# Step 1: Set clipboard with your name
termux-clipboard-set "Your Name Here"

# Step 2: Verify by pasting in any app (WhatsApp, Notes, etc.)

# Step 3: Copy something from another app, then read in Termux
termux-clipboard-get

# Step 4: Get clipboard word count
termux-clipboard-get | wc -w

# Step 5: Get clipboard character count
termux-clipboard-get | wc -c

# Step 6: Convert clipboard to uppercase
termux-clipboard-get | tr 'a-z' 'A-Z'

# Step 7: Convert and set back
termux-clipboard-get | tr 'a-z' 'A-Z' | termux-clipboard-set
```

### Exercise 2: Share Operations

```bash
# Task: Practice sharing content

# Step 1: Share simple text
termux-share "Hello from Termux!"

# Step 2: Share current date/time
date | termux-share

# Step 3: Share system info
uname -a | termux-share

# Step 4: Share disk usage
df -h | termux-share

# Step 5: Share a file from downloads
termux-share ~/storage/downloads/test.txt

# Step 6: Share with title
termux-share -t "System Report" "$(uname -a)"

# Step 7: Share clipboard content
termux-clipboard-get | termux-share
```

### Exercise 3: Create Clipboard Manager

```bash
# Task: Build and test clipboard manager

# Step 1: Create the script
cat > ~/clipboard-manager.sh << 'EOF'
#!/bin/bash
# Simple clipboard manager

case "$1" in
    get) termux-clipboard-get ;;
    set) echo "$2" | termux-clipboard-set ;;
    save) termux-clipboard-get >> ~/.clipboard_history ;;
    history) cat ~/.clipboard_history ;;
    share) termux-clipboard-get | termux-share ;;
    *) echo "Usage: $0 {get|set|save|history|share}" ;;
esac
EOF

# Step 2: Make executable
chmod +x ~/clipboard-manager.sh

# Step 3: Test get
~/clipboard-manager.sh get

# Step 4: Test set
~/clipboard-manager.sh set "Test message"

# Step 5: Test save to history
~/clipboard-manager.sh save

# Step 6: View history
~/clipboard-manager.sh history

# Step 7: Test share
~/clipboard-manager.sh share
```

### Exercise 4: Create Quick Note Script

```bash
# Task: Build quick note script

# Step 1: Create directories
mkdir -p ~/notes

# Step 2: Create the script
cat > ~/quick-note.sh << 'EOF'
#!/bin/bash
# Quick note with share

NOTE_DIR="$HOME/notes"
TIMESTAMP=$(date '+%Y%m%d_%H%M%S')

create_note() {
    echo "Enter note (Ctrl+D to finish):"
    cat > "$NOTE_DIR/note_$TIMESTAMP.txt"
    echo "Note saved!"
    cat "$NOTE_DIR/note_$TIMESTAMP.txt" | termux-clipboard-set
    echo "Copied to clipboard!"
    read -p "Share? (y/n): " ans
    [ "$ans" = "y" ] && termux-share "$NOTE_DIR/note_$TIMESTAMP.txt"
}

case "$1" in
    new) create_note ;;
    list) ls -lt "$NOTE_DIR" ;;
    *) create_note ;;
esac
EOF

# Step 3: Make executable
chmod +x ~/quick-note.sh

# Step 4: Test create
~/quick-note.sh new

# Step 5: List notes
~/quick-note.sh list
```

### Exercise 5: URL Shortener Script

```bash
# Task: Create URL shortener

# Step 1: Install dependencies
pkg install curl jq -y

# Step 2: Create the script
cat > ~/shorten-url.sh << 'EOF'
#!/bin/bash
# URL Shortener by T3rmuxk1ng

url="${1:-$(termux-clipboard-get)}"

if [[ ! "$url" =~ ^https?:// ]]; then
    echo "Invalid URL"
    exit 1
fi

echo "Shortening: $url"
short=$(curl -s "https://is.gd/create.php?format=json&url=$url" | jq -r '.shorturl')

if [ -n "$short" ] && [ "$short" != "null" ]; then
    echo "Shortened: $short"
    echo -n "$short" | termux-clipboard-set
    echo "Copied to clipboard!"
    read -p "Share? (y/n): " ans
    [ "$ans" = "y" ] && termux-share "$short"
else
    echo "Failed to shorten"
fi
EOF

# Step 3: Make executable
chmod +x ~/shorten-url.sh

# Step 4: Test with URL
~/shorten-url.sh "https://www.google.com/search?q=termux+tutorial"

# Step 5: Copy a URL to clipboard and test
~/shorten-url.sh
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "termux-clipboard-get: command not found"

```bash
# Cause: termux-api package not installed

# Solution 1: Install termux-api
pkg install termux-api -y

# Solution 2: Check if Termux:API app is installed
# Go to Android Settings → Apps → Look for Termux:API
# If not found, install from F-Droid

# Solution 3: Verify installation
which termux-clipboard-get
# Should output: /data/data/com.termux/files/usr/bin/termux-clipboard-get
```

### Problem 2: Clipboard returns empty

```bash
# Cause: Permission issue or no content

# Solution 1: Check Termux:API app permissions
# Settings → Apps → Termux:API → Permissions → Allow all

# Solution 2: Try setting clipboard first
termux-clipboard-set "test"
termux-clipboard-get
# Should return: test

# Solution 3: Check for special characters
# Some special characters may cause issues
# Try with simple text first
```

### Problem 3: Share doesn't open apps

```bash
# Cause: No apps installed or permission issue

# Solution 1: Check if share intent works
termux-share "test"
# Should open share sheet

# Solution 2: Check content type
# Use -c flag for specific content type
termux-share -c text/plain "text content"

# Solution 3: Check file exists when sharing file
ls -la ~/storage/downloads/
termux-share ~/storage/downloads/existing_file.txt
```

### Problem 4: Clipboard not syncing with apps

```bash
# Cause: Android clipboard API limitations

# Solution 1: Use termux-clipboard-set explicitly
echo "content" | termux-clipboard-set

# Solution 2: Check for clipboard manager apps
# Some clipboard manager apps may interfere
# Temporarily disable them to test

# Solution 3: Restart Termux:API app
# Settings → Apps → Termux:API → Force Stop
# Then try again
```

### Problem 5: "Permission denied" when sharing files

```bash
# Cause: File permission or storage access

# Solution 1: Check file permissions
ls -la /path/to/file

# Solution 2: Ensure storage permission granted
termux-setup-storage

# Solution 3: Use absolute paths
termux-share /sdcard/Download/file.txt
# Instead of relative paths
```

### Problem 6: Python clipboard module not working

```bash
# Cause: subprocess issues or encoding

# Solution 1: Use proper encoding
import subprocess
result = subprocess.run(
    ['termux-clipboard-get'],
    capture_output=True,
    text=True  # Important for text output
)

# Solution 2: Handle empty clipboard
content = result.stdout.strip()
if not content:
    print("Clipboard is empty")

# Solution 3: Check for special characters
# Some Unicode may cause issues
content = content.encode('utf-8', errors='ignore').decode('utf-8')
```

### Problem 7: Share history not working

```bash
# Cause: History file permission or location

# Solution 1: Create history file manually
touch ~/.clipboard_history
chmod 644 ~/.clipboard_history

# Solution 2: Check file location
ls -la ~/.clipboard_history

# Solution 3: Use absolute path in script
HISTORY_FILE="$HOME/.clipboard_history"
# Not: HISTORY_FILE="~/.clipboard_history"
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Feature Highlight**
```
┌────────────────────────────────────┐
│  [Terminal Screenshot Background]  │
│                                    │
│   📋 CLIPBOARD API                 │
│   🔗 SHARE FROM TERMINAL           │
│                                    │
│   ✓ Copy & Paste                   │
│   ✓ Share to WhatsApp              │
│   ✓ URL Shortener                  │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Action Shot**
```
┌────────────────────────────────────┐
│  📱 Terminal → 📋 → 📲 Apps        │
│                                    │
│   SHARE ANYTHING                   │
│   FROM TERMINAL!                   │
│                                    │
│   WhatsApp | Telegram | Gmail      │
│                                    │
│   Chapter 23 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Before/After**
```
┌────────────────────────────────────┐
│  ❌ WITHOUT: Copy → Exit → Paste   │
│  ────────────────────────────────  │
│  ✅ WITH TERMUX: One Command!      │
│                                    │
│   termux-share "text"              │
│                                    │
│   🚀 SUPER FAST!                   │
│   [T3rmuxk1ng]                     │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📋 Termux Full Course - Chapter 23: Clipboard & Share API

🔥 In this video you'll learn:
• Clipboard API - Get & Set text programmatically
• Share API - Share text, files directly from terminal
• Clipboard Manager Script - Complete solution
• Quick Note Script - Notes with share feature
• URL Shortener + Share - Automatic shortening
• Python Integration - Programmatic clipboard access
• 17+ Practical Examples for daily use

⏱️ Timestamps:
0:00 - Introduction
0:45 - Clipboard API Introduction
3:00 - termux-clipboard-get
6:00 - termux-clipboard-set
9:30 - termux-share API
13:00 - Clipboard Manager Script
16:00 - Quick Note Script
18:00 - URL Shortener + Share
20:30 - Python Integration
23:00 - 17 Practical Examples
26:00 - Summary

📝 Commands from this video:
pkg install termux-api -y
termux-clipboard-get
termux-clipboard-set "text"
termux-share "content"
termux-share file.txt

💻 Scripts in this video:
• Clipboard Manager: Complete clipboard management
• Quick Note: Fast note taking with share
• URL Shortener: Shorten and share URLs

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxAPI #Clipboard #ShareAPI #T3rmuxk1ng #TermuxHindi #AndroidTerminal

---
⚠️ Disclaimer: This video is for educational purposes only.
```

### Tags List

```
termux, termux api, termux clipboard, termux share, 
termux clipboard api, termux share api, termux tutorial,
termux course, termux hindi, termux scripts, 
share from terminal, clipboard manager, termux tips,
android terminal, t3rmuxk1ng, termux python,
termux automation, termux utilities, url shortener,
quick notes, termux productivity
```

### Hashtags

```
#Termux #TermuxAPI #ClipboardAPI #ShareAPI #TermuxHindi 
#TermuxTutorial #TermuxCourse #AndroidTerminal #T3rmuxk1ng 
#TermuxScripts #LearnTermux #TerminalTips #CommandLine
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux API Wiki | https://wiki.termux.com/wiki/Termux:API |
| Termux Clipboard | https://wiki.termux.com/wiki/Termux:API#Clipboard |
| Termux Share | https://wiki.termux.com/wiki/Termux:API#Share |
| Android Intent | https://developer.android.com/reference/android/content/Intent |

### Related Chapters

| Chapter | Topic |
|---------|-------|
| Ch10 | Termux API Setup |
| Ch21 | API Notifications |
| Ch22 | API Contacts & SMS |
| Ch43 | Task Automation |
| Ch44 | Termux Widgets |

### Useful Packages

```bash
# For URL shortening
pkg install curl jq

# For QR codes
pkg install qrencode

# For text processing
pkg install gawk sed

# For Python integration
pkg install python
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 24, verify:

- [ ] Termux:API app installed
- [ ] `pkg install termux-api -y` completed
- [ ] `termux-clipboard-get` working
- [ ] `termux-clipboard-set` working
- [ ] `termux-share` opening share sheet
- [ ] Clipboard manager script created and tested
- [ ] Quick note script created and tested
- [ ] URL shortener script created and tested
- [ ] Python integration tested
- [ ] At least 10 practical examples tried

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 24: Networking Basics**

- Understanding IP addresses and ports
- Network configuration commands
- ifconfig and ip command usage
- Checking network connectivity
- DNS lookup commands
- Network troubleshooting basics

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Combine `termux-clipboard-get` with text processing tools for powerful clipboard transformations.

> 💡 **Pro Tip #2:** Use `termux-clipboard-set` in aliases for quick clipboard operations: `alias cclip='termux-clipboard-set'`

> 💡 **Pro Tip #3:** Always check if clipboard is empty before processing: `[ -n "$(termux-clipboard-get)" ]`

> 💡 **Pro Tip #4:** Use `-t` flag with `termux-share` for better share sheet presentation.

> 💡 **Pro Tip #5:** For sharing code, use `-c text/plain` to ensure proper formatting in target apps.

> 💡 **Pro Tip #6:** Create a clipboard history by periodically saving clipboard content to a file with timestamps.

> 💡 **Pro Tip #7:** Use `termux-share` with file paths for quick sharing without opening file managers.

> 💡 **Pro Tip #8:** Chain clipboard operations: `termux-clipboard-get | process | termux-clipboard-set`

> 💡 **Pro Tip #9:** For secure clipboard clearing: `termux-clipboard-set ""` removes sensitive data.

> 💡 **Pro Tip #10:** Combine with other APIs: `termux-location | jq '.' | termux-clipboard-set` for quick data sharing.

---

## 🔥 REAL WORLD APPLICATIONS

### 1. Password Generator with Auto-Copy
Generate secure passwords and automatically copy to clipboard.

```bash
#!/bin/bash
# password_gen.sh - Generate and copy passwords
LENGTH=${1:-16}

PASSWORD=$(openssl rand -base64 32 | head -c "$LENGTH")
echo "$PASSWORD" | termux-clipboard-set

termux-toast --bgcolor "#4CAF50" "Password copied!"
echo "Generated password (also in clipboard): $PASSWORD"
```

### 2. Code Snippet Manager
Quickly save and share code snippets.

```bash
#!/bin/bash
# snippet_manager.sh - Code snippet manager
SNIPPET_DIR=~/snippets
mkdir -p "$SNIPPET_DIR"

save_snippet() {
    NAME=$(termux-dialog --title "Name" --text "Snippet name:" | jq -r '.text')
    echo "Paste your code (Ctrl+D to save):"
    cat > "$SNIPPET_DIR/$NAME.txt"
    echo "Saved as $NAME.txt"
}

share_snippet() {
    ls "$SNIPPET_DIR"
    read -p "Which snippet? " name
    termux-share -c text/plain "$SNIPPET_DIR/$name"
}

echo "1. Save snippet"
echo "2. Share snippet"
read -p "Choice: " choice

case $choice in
    1) save_snippet ;;
    2) share_snippet ;;
esac
```

### 3. URL Shortener
Shorten URLs and copy to clipboard automatically.

```bash
#!/bin/bash
# url_shorten.sh - Shorten and copy URL
URL=${1:-$(termux-clipboard-get)}

SHORT=$(curl -s "https://is.gd/create.php?format=json&url=$URL" | jq -r '.shorturl')

if [ -n "$SHORT" ]; then
    echo "$SHORT" | termux-clipboard-set
    termux-toast "Shortened URL copied!"
    echo "Original: $URL"
    echo "Short: $SHORT"
else
    echo "Failed to shorten URL"
fi
```

### 4. Quick Note Sharing
Take quick notes and share instantly.

```bash
#!/bin/bash
# quick_share.sh - Quick note with share
echo "Enter note (Ctrl+D to finish):"
NOTE=$(cat)

echo "$NOTE" | termux-clipboard-set

read -p "Share now? (y/n): " share
if [ "$share" = "y" ]; then
    termux-share "$NOTE"
fi
```

### 5. Clipboard Transformer
Transform clipboard content in various ways.

```bash
#!/bin/bash
# clip_transform.sh - Transform clipboard content

show_menu() {
    echo "Transform clipboard:"
    echo "1. UPPERCASE"
    echo "2. lowercase"
    echo "3. Base64 encode"
    echo "4. Base64 decode"
    echo "5. URL encode"
    echo "6. JSON format"
    echo "7. Trim whitespace"
    echo "8. Exit"
}

transform() {
    CONTENT=$(termux-clipboard-get)
    
    case $1 in
        1) echo "$CONTENT" | tr 'a-z' 'A-Z' ;;
        2) echo "$CONTENT" | tr 'A-Z' 'a-z' ;;
        3) echo -n "$CONTENT" | base64 ;;
        4) echo "$CONTENT" | base64 -d ;;
        5) python3 -c "import urllib.parse; print(urllib.parse.quote('$CONTENT'))" ;;
        6) echo "$CONTENT" | python3 -m json.tool 2>/dev/null || echo "Invalid JSON" ;;
        7) echo "$CONTENT" | xargs ;;
        8) exit 0 ;;
    esac | termux-clipboard-set
    
    termux-toast "Transformed!"
}

while true; do
    show_menu
    read -p "Choice: " choice
    transform "$choice"
done
```

---

## ⚡ QUICK REFERENCE CARD

### Clipboard Commands

| Command | Purpose |
|---------|---------|
| `termux-clipboard-get` | Get clipboard content |
| `termux-clipboard-set "text"` | Set clipboard content |
| `echo "text" \| termux-clipboard-set` | Set via pipe |
| `command \| termux-clipboard-set` | Set command output |

### Share Commands

| Command | Purpose |
|---------|---------|
| `termux-share "text"` | Share text |
| `termux-share file.txt` | Share file |
| `termux-share -t "Title" file` | Share with title |
| `termux-share -c type file` | Share with content type |
| `command \| termux-share` | Share command output |

### Content Types (MIME)

| Type | MIME |
|------|------|
| Text | `text/plain` |
| HTML | `text/html` |
| JSON | `application/json` |
| Image JPEG | `image/jpeg` |
| Image PNG | `image/png` |
| PDF | `application/pdf` |

### Share Actions

| Flag | Action |
|------|--------|
| `-a send` | Send (default) |
| `-a view` | View in app |
| `-a edit` | Edit in app |

---

## 🏆 BONUS: AUTOMATION IDEAS

### Idea 1: Clipboard Monitor Daemon
```bash
#!/bin/bash
# clip_monitor.sh - Monitor and log clipboard changes
LOG=~/clipboard_history.log
LAST=""

while true; do
    CURRENT=$(termux-clipboard-get 2>/dev/null)
    
    if [ "$CURRENT" != "$LAST" ] && [ -n "$CURRENT" ]; then
        echo "$(date): $CURRENT" >> "$LOG"
        LAST="$CURRENT"
    fi
    
    sleep 5
done
```

### Idea 2: Quick Code Share
```bash
#!/bin/bash
# Share code from file with syntax highlighting info
FILE=$1
EXT="${FILE##*.}"

termux-share -c "text/x-$EXT" -t "$(basename $FILE)" "$FILE"
```

### Idea 3: IP Address Sharer
```bash
#!/bin/bash
# Share current IP addresses
LOCAL=$(termux-wifi-connectioninfo | jq -r '.ip // "Not connected"')
PUBLIC=$(curl -s --max-time 5 ifconfig.me)

echo "Local: $LOCAL
Public: $PUBLIC" | termux-clipboard-set

termux-notification --title "IP Addresses" --content "Copied to clipboard"
```

---

## 📝 CHAPTER SUMMARY

### ✅ What You Learned

- **termux-clipboard-get**: Retrieve current clipboard content
- **termux-clipboard-set**: Set new content to clipboard
- **termux-share**: Share text and files via Android share sheet
- **Content types**: Using MIME types for better app compatibility
- **Share actions**: send, view, and edit actions
- **Clipboard transformations**: Processing clipboard content with pipes
- **Integration**: Combining clipboard with other Termux APIs

### 🎯 Key Takeaways

1. Clipboard operations are instant - no delay
2. Use pipes for efficient clipboard manipulation
3. Share API works with both text and files
4. MIME types help target apps handle content correctly
5. Multiple files can be shared at once
6. Clipboard can store any text content
7. Always check for empty clipboard before processing

---

## 🎯 PRACTICAL PROJECTS

### Project 1: Complete Clipboard Manager
```bash
#!/bin/bash
# clip_manager.sh - Full clipboard manager

HISTORY_FILE=~/.clipboard_history
MAX_HISTORY=50

show_menu() {
    clear
    echo "╔════════════════════════════════════════╗"
    echo "║         CLIPBOARD MANAGER              ║"
    echo "╠════════════════════════════════════════╣"
    echo "║ 1. View Current                        ║"
    echo "║ 2. Set New Content                     ║"
    echo "║ 3. View History                        ║"
    echo "║ 4. Restore from History                ║"
    echo "║ 5. Transform                           ║"
    echo "║ 6. Share Clipboard                     ║"
    echo "║ 7. Clear History                       ║"
    echo "║ 8. Exit                                ║"
    echo "╚════════════════════════════════════════╝"
}

view_current() {
    echo "Current clipboard:"
    termux-clipboard-get
}

set_content() {
    echo "Enter text (Ctrl+D to finish):"
    cat | termux-clipboard-set
    echo "Clipboard updated!"
    save_to_history
}

save_to_history() {
    CONTENT=$(termux-clipboard-get)
    [ -n "$CONTENT" ] && echo "$(date '+%H:%M:%S'): $CONTENT" >> "$HISTORY_FILE"
    tail -n $MAX_HISTORY "$HISTORY_FILE" > "$HISTORY_FILE.tmp" 2>/dev/null
    mv "$HISTORY_FILE.tmp" "$HISTORY_FILE" 2>/dev/null
}

view_history() {
    [ -f "$HISTORY_FILE" ] && cat "$HISTORY_FILE" || echo "No history"
}

restore_history() {
    view_history | nl
    read -p "Enter number: " num
    LINE=$(sed -n "${num}p" "$HISTORY_FILE")
    CONTENT="${LINE#*: }"
    echo "$CONTENT" | termux-clipboard-set
    echo "Restored!"
}

transform_menu() {
    echo "Transform options:"
    echo "1. UPPERCASE"
    echo "2. lowercase"
    echo "3. Base64 encode"
    echo "4. Base64 decode"
    read -p "Choice: " choice
    
    CONTENT=$(termux-clipboard-get)
    case $choice in
        1) echo "$CONTENT" | tr 'a-z' 'A-Z' | termux-clipboard-set ;;
        2) echo "$CONTENT" | tr 'A-Z' 'a-z' | termux-clipboard-set ;;
        3) echo -n "$CONTENT" | base64 | termux-clipboard-set ;;
        4) echo "$CONTENT" | base64 -d | termux-clipboard-set ;;
    esac
    echo "Transformed!"
}

share_clip() {
    termux-share "$(termux-clipboard-get)"
}

while true; do
    show_menu
    read -p "Choice: " choice
    case $choice in
        1) view_current ;;
        2) set_content ;;
        3) view_history ;;
        4) restore_history ;;
        5) transform_menu ;;
        6) share_clip ;;
        7) rm -f "$HISTORY_FILE"; echo "Cleared" ;;
        8) exit 0 ;;
    esac
    read -p "Press Enter..."
done
```

---

## 🚀 INTEGRATION TIPS

### Clipboard + Location
```bash
# Copy location coordinates to clipboard
termux-location | jq -r '"\(.latitude), \(.longitude)"' | termux-clipboard-set
termux-toast "Location copied!"
```

### Clipboard + Device Info
```bash
# Share device report
REPORT=$(termux-battery-status; termux-wifi-connectioninfo)
echo "$REPORT" | termux-share
```

### Clipboard + Contacts
```bash
# Copy contact info
CONTACT=$(termux-contact-list | jq '.[0]')
echo "$CONTACT" | termux-clipboard-set
```

### Share + Notifications
```bash
# Share notification content
termux-notification --title "Ready to Share" --content "Content in clipboard" \
    --button1 "Share" --button1-action "termux-share \"$(termux-clipboard-get)\""
```

---

## 📊 JSON OUTPUT GUIDE

### Clipboard Operations
Clipboard commands return plain text, not JSON:
```bash
# Get returns plain text
termux-clipboard-get

# To convert to JSON
termux-clipboard-get | jq -Rs '.'
```

### Share Operations
Share commands don't return output - they open the share dialog:
```bash
# This opens share dialog
termux-share "text"
```

### Processing JSON from Clipboard
```bash
# If clipboard contains JSON
DATA=$(termux-clipboard-get)
echo "$DATA" | jq '.field'

# Format JSON in clipboard
termux-clipboard-get | jq '.' | termux-clipboard-set
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relation |
|---------|-------|----------|
| Chapter 17 | File Operations | Share files via clipboard |
| Chapter 18 | Device Info | Copy device info to clipboard |
| Chapter 19 | Camera & Media | Share captured media |
| Chapter 20 | Network APIs | Share network info |
| Chapter 21 | Notifications | Share notification content |
| Chapter 22 | Contacts & SMS | Share contact info |

---

## 🎮 INTERACTIVE QUIZ

### Test Your Knowledge!

**Q1.** What command gets clipboard content?
- A) `termux-clipboard-read`
- B) `termux-clipboard-get`
- C) `termux-get-clipboard`
- D) `termux-read-clip`

**Q2.** How do you set clipboard via pipe?
- A) `command > termux-clipboard-set`
- B) `command \| termux-clipboard-set`
- C) `command \| termux-clipboard`
- D) `termux-set \| command`

**Q3.** Which flag sets share title?
- A) `--name`
- B) `--title`
- C) `-t`
- D) Both B and C

**Q4.** What MIME type is for plain text?
- A) `text/text`
- B) `text/plain`
- C) `plain/text`
- D) `application/text`

**Q5.** How do you share a file?
- A) `termux-share-send file`
- B) `termux-share file`
- C) `termux-send file`
- D) `termux-file-share file`

**Q6.** What does `-a view` do?
- A) Opens file for viewing
- B) Views share history
- C) Previews content
- D) Nothing

**Q7.** Can you share multiple files at once?
- A) No
- B) Yes, with multiple arguments
- C) Only with zip
- D) Only text

**Q8.** What happens if you run `termux-share` without arguments?
- A) Error
- B) Opens share with clipboard content
- C) Shows help
- D) Shares empty text

**Q9.** Which action opens content for editing?
- A) `-a send`
- B) `-a edit`
- C) `-a modify`
- D) `-e`

**Q10.** How do you clear clipboard?
- A) `termux-clipboard-clear`
- B) `termux-clipboard-set ""`
- C) `termux-clear-clipboard`
- D) `termux-clipboard-reset`

**Q11.** What content type for JSON?
- A) `text/json`
- B) `application/json`
- C) `data/json`
- D) `json/application`

**Q12.** What does `-c` flag specify?
- A) Content count
- B) Content type (MIME)
- C) Copy mode
- D) Compression

### Quiz Answers

1. **B** - `termux-clipboard-get` retrieves clipboard content
2. **B** - Pipe with `| termux-clipboard-set` sets clipboard
3. **D** - Both `--title` and `-t` set the share title
4. **B** - `text/plain` is the MIME type for plain text
5. **B** - `termux-share file` shares a file
6. **A** - `-a view` opens content for viewing in compatible app
7. **B** - Yes, `termux-share file1 file2 file3` shares multiple files
8. **B** - Without arguments, it shares clipboard content
9. **B** - `-a edit` opens content for editing
10. **B** - `termux-clipboard-set ""` clears the clipboard
11. **B** - `application/json` is the MIME type for JSON
12. **B** - `-c` specifies content type (MIME type)

---

## 🎊 FINAL NOTES

Congratulations! You've completed the **Termux API Module 4** chapters on File Operations, Device Info, Camera & Media, Network, Notifications, Contacts & SMS, and Clipboard & Share!

These powerful APIs enable you to:
- 📁 Manage files with Android integration
- 📱 Access device hardware information
- 📸 Control camera and media playback
- 📡 Monitor network connections
- 🔔 Create rich notifications
- 👥 Manage contacts and SMS
- 📋 Share content seamlessly

Combine these APIs to build powerful automation tools, security utilities, and productivity scripts!


---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Clipboard History Manager

```
╔══════════════════════════════════════════════════════════════════════╗
║  📋 SCENARIO: Advanced Clipboard History Manager                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  SITUATION:                                                            ║
║  User needs persistent clipboard history with search and pinning.     ║
║                                                                        ║
║  SOLUTION:                                                             ║
╚══════════════════════════════════════════════════════════════════════╝
```

```python
#!/usr/bin/env python3
import subprocess
import json
import os
import time
from datetime import datetime
from threading import Thread

class ClipboardHistory:
    def __init__(self, history_file="~/.clipboard_history.json", max_items=100):
        self.history_file = os.path.expanduser(history_file)
        self.max_items = max_items
        self.pinned = []
        self.history = self.load_history()
        self.running = False
        
    def load_history(self):
        try:
            with open(self.history_file) as f:
                data = json.load(f)
                self.pinned = data.get('pinned', [])
                return data.get('history', [])
        except:
            return []
            
    def save_history(self):
        with open(self.history_file, 'w') as f:
            json.dump({
                'history': self.history[-self.max_items:],
                'pinned': self.pinned
            }, f, indent=2)
            
    def get_clipboard(self):
        result = subprocess.run(['termux-clipboard-get'], capture_output=True, text=True)
        return result.stdout.strip() if result.returncode == 0 else None
        
    def set_clipboard(self, text):
        subprocess.run(['termux-clipboard-set', text], input=text.encode())
        
    def monitor(self, interval=2):
        """Monitor clipboard for changes"""
        last_content = None
        
        while self.running:
            content = self.get_clipboard()
            
            if content and content != last_content:
                entry = {
                    'content': content,
                    'timestamp': datetime.now().isoformat(),
                    'length': len(content)
                }
                self.history.append(entry)
                self.save_history()
                last_content = content
                print(f"[{datetime.now().strftime('%H:%M:%S')}] Clipboard captured ({len(content)} chars)")
                
            time.sleep(interval)
            
    def start_monitoring(self):
        self.running = True
        Thread(target=self.monitor, daemon=True).start()
        
    def search(self, query):
        """Search clipboard history"""
        results = []
        query = query.lower()
        
        for entry in self.history:
            if query in entry['content'].lower():
                results.append(entry)
        return results
        
    def pin(self, index):
        """Pin a history item"""
        if 0 <= index < len(self.history):
            item = self.history[index]
            if item not in self.pinned:
                self.pinned.append(item)
                self.save_history()
                
    def restore(self, index):
        """Restore history item to clipboard"""
        if 0 <= index < len(self.history):
            self.set_clipboard(self.history[index]['content'])
            return True
        return False
        
    def show_menu(self):
        while True:
            print("\n📋 Clipboard Manager")
            print("=" * 40)
            print("1. View recent")
            print("2. Search")
            print("3. View pinned")
            print("4. Restore")
            print("5. Clear history")
            print("6. Exit")
            
            choice = input("\nChoice: ")
            
            if choice == '1':
                for i, entry in enumerate(self.history[-10:]):
                    preview = entry['content'][:50] + "..." if len(entry['content']) > 50 else entry['content']
                    print(f"{i}: [{entry['timestamp'][:10]}] {preview}")
            elif choice == '2':
                query = input("Search: ")
                for entry in self.search(query)[:10]:
                    print(f"- {entry['content'][:50]}...")
            elif choice == '6':
                self.running = False
                break

# Usage
manager = ClipboardHistory()
manager.start_monitoring()
manager.show_menu()
```

---

### Scenario 2: Quick Share System

```
╔══════════════════════════════════════════════════════════════════════╗
║  📤 SCENARIO: Quick Content Sharing System                            ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  SITUATION:                                                            ║
║  User wants to quickly share command outputs, files, and text.        ║
║                                                                        ║
║  SOLUTION:                                                             ║
╚══════════════════════════════════════════════════════════════════════╝
```

```python
#!/usr/bin/env python3
import subprocess
import os
from datetime import datetime

class QuickShare:
    def __init__(self):
        self.history_dir = os.path.expanduser("~/share_history")
        os.makedirs(self.history_dir, exist_ok=True)
        
    def share_text(self, text, title="Shared from Termux"):
        """Share text content"""
        subprocess.run(['termux-share', '-t', title], input=text.encode())
        
        # Save to history
        filename = f"share_{datetime.now().strftime('%Y%m%d_%H%M%S')}.txt"
        with open(os.path.join(self.history_dir, filename), 'w') as f:
            f.write(text)
            
    def share_file(self, filepath):
        """Share file"""
        if os.path.exists(filepath):
            subprocess.run(['termux-share', filepath])
            
    def share_command_output(self, command):
        """Run command and share output"""
        result = subprocess.run(command, shell=True, capture_output=True, text=True)
        output = f"Command: {command}\n\nOutput:\n{result.stdout}\n"
        if result.stderr:
            output += f"Errors:\n{result.stderr}"
        self.share_text(output)
        
    def share_screenshot(self):
        """Capture and share photo"""
        filepath = f"/sdcard/Pictures/screenshot_{datetime.now().strftime('%Y%m%d_%H%M%S')}.jpg"
        subprocess.run(['termux-camera-photo', '-c', '0', filepath])
        if os.path.exists(filepath):
            subprocess.run(['termux-media-scan', filepath])
            subprocess.run(['termux-share', '-c', 'image/jpeg', filepath])
            return filepath
        return None

# Usage
share = QuickShare()
share.share_text("Hello from Termux!")
share.share_command_output("ls -la")
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: Clipboard & Share API Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CLIPBOARD & SHARE API ARCHITECTURE                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Clipboard Operations                          │   │
│   │                                                                  │   │
│   │   termux-clipboard-get  →  Read system clipboard                 │   │
│   │   termux-clipboard-set  →  Write to system clipboard            │   │
│   │                                                                  │   │
│   │   ┌─────────────────┐           ┌─────────────────┐             │   │
│   │   │ Termux          │ ────────► │ Android        │              │   │
│   │   │ Command         │           │ Clipboard      │              │   │
│   │   └─────────────────┘           │ Service        │              │   │
│   │                                 └─────────────────┘             │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Share Operations                              │   │
│   │                                                                  │   │
│   │   termux-share <content>  →  Open Android Share Sheet           │   │
│   │                                                                  │   │
│   │   ┌─────────────────┐           ┌─────────────────┐             │   │
│   │   │ Content to      │           │ Share Intent    │              │   │
│   │   │ Share           │ ────────► │ Dialog         │              │   │
│   │   └─────────────────┘           └────────┬────────┘             │   │
│   │                                          │                      │   │
│   │                                          ▼                      │   │
│   │   ┌────────────────────────────────────────────────────────┐    │   │
│   │   │ Target Apps                                          │    │   │
│   │   │ WhatsApp │ Telegram │ Gmail │ Bluetooth │ Copy       │    │   │
│   │   └────────────────────────────────────────────────────────┘    │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Relationship | Chapter | Topic |
|--------------|---------|-------|
| **Prerequisites** | Ch 1-22 | All previous APIs |
| **Related** | Ch 17 | File Operations |
| **Related** | Ch 19 | Camera & Media |
| **Related** | Ch 21 | Notifications |
| **Next** | Ch 24 | Advanced APIs |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Cross-Device Sync

```python
#!/usr/bin/env python3
"""Sync clipboard across devices"""

import subprocess
import json
import os

class CrossDeviceSync:
    def __init__(self, sync_file="~/sync_clipboard.json"):
        self.sync_file = os.path.expanduser(sync_file)
        
    def push_clipboard(self):
        """Push clipboard to sync file"""
        result = subprocess.run(['termux-clipboard-get'], capture_output=True, text=True)
        if result.returncode == 0:
            data = {
                'content': result.stdout,
                'timestamp': datetime.now().isoformat()
            }
            with open(self.sync_file, 'w') as f:
                json.dump(data, f)
            return True
        return False
        
    def pull_clipboard(self):
        """Pull clipboard from sync file"""
        try:
            with open(self.sync_file) as f:
                data = json.load(f)
            subprocess.run(['termux-clipboard-set'], input=data['content'].encode())
            return True
        except:
            return False
```

### Advanced Technique 2: Smart Content Detector

```python
#!/usr/bin/env python3
"""Detect content type and handle appropriately"""

import subprocess
import re

class SmartContentHandler:
    def detect_type(self, content):
        """Detect content type"""
        if re.match(r'https?://', content):
            return 'url'
        elif re.match(r'^\d+$', content):
            return 'number'
        elif re.match(r'[\w\.-]+@[\w\.-]+\.\w+', content):
            return 'email'
        elif re.match(r'\+?\d{10,}', content):
            return 'phone'
        elif content.startswith('{') or content.startswith('['):
            return 'json'
        else:
            return 'text'
            
    def handle(self, content):
        """Handle content based on type"""
        ctype = self.detect_type(content)
        
        if ctype == 'url':
            # Open URL
            subprocess.run(['termux-open-url', content])
        elif ctype == 'phone':
            # Dial number
            subprocess.run(['termux-telephony-call', content])
        elif ctype == 'json':
            # Format and copy
            import json
            formatted = json.dumps(json.loads(content), indent=2)
            subprocess.run(['termux-clipboard-set'], input=formatted.encode())
        else:
            # Just share
            subprocess.run(['termux-share'], input=content.encode())
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### ✅ Commands Learned
- [ ] `termux-clipboard-get` - Read clipboard
- [ ] `termux-clipboard-set` - Write clipboard
- [ ] `termux-share` - Share content

### ✅ Concepts Understood
- [ ] Android Clipboard service
- [ ] Share Intent system
- [ ] MIME types for sharing
- [ ] Content type detection

---

## 🎊 MODULE 4 COMPLETE!

Congratulations! You've completed the **Termux API Module 4** chapters!

### 📚 Chapters Covered:
- Ch 17: File Operations API
- Ch 18: Device Information API
- Ch 19: Camera & Media API
- Ch 20: Network Operations API
- Ch 21: Notifications & Dialogs API
- Ch 22: Contacts & SMS API
- Ch 23: Clipboard & Share API

### 🚀 Skills Acquired:
- Complete Termux API mastery
- Android system integration
- Automation scripting
- Security tool development
- Practical application building

**Ready for Module 5: Advanced Topics!**
