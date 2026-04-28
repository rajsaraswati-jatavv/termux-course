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
