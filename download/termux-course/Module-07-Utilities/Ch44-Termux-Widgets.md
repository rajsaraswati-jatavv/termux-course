# Chapter 44: Termux Widgets & Shortcuts

> **Module:** 7 - Utilities  
> **Chapter:** 44 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Termux:Widget, shortcuts, Tasker integration, automation |
| Commands Reference | All widget and shortcut commands |
| Practice Exercises | Hands-on widget creation tasks |
| Troubleshooting | Common widget issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 44
Title: Termux Widgets & Shortcuts | Home Screen Automation | Tasker Integration
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut exciting hai - Termux Widgets & Shortcuts!

Socho, aapka phone ek powerful Linux machine hai Termux ke saath. Lekin har 
baar Termux open karo, command type karo, script run karo - ye repetitive 
hai na?

Kya aisa ho ki ek tap pe sab kuch ho jaaye? WiFi toggle, quick backup, 
speed test, IP check - sab home screen se?

Haan, ye possible hai Termux:Widget ke saath!

Aaj hum seekhenge:
✓ Termux:Widget installation aur setup
✓ ~/.shortcuts directory structure
✓ Single-tap scripts banana
✓ Tasker integration for advanced automation
✓ Home screen widgets
✓ Quick settings tiles
✓ Notification shortcuts
✓ Voice commands with Tasker
✓ 15+ practical widget examples

Chaliye shuru karte hain!

---

[SECTION 1: TERMUX:WIDGET INTRODUCTION - 0:50 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - Termux:Widget kya hai?

Termux:Widget ek add-on app hai jo aapke Termux scripts ko home screen 
pe shortcuts ki tarah dikhata hai. Single tap pe script execute ho jaata hai.

Key Features:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX:WIDGET FEATURES                                │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Feature              │ Description                                     │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Home Screen Shortcuts│ Scripts directly on home screen                 │
│ Single Tap Execute   │ No terminal needed for execution                │
│ Folders Support      │ Organize scripts in folders                     │
│ Tasker Integration   │ Connect with Tasker automation                  │
│ Custom Icons         │ Scripts show as list in widget                  │
│ Background Execution │ Scripts run silently                            │
│ Output Display       │ Optional toast notifications                    │
└──────────────────────┴──────────────────────────────────────────────────┘

Termux:Widget kyun use karein?

1. Quick Access - Termux open karne ki zarurat nahi
2. One-Tap Actions - Simple tasks ek tap mein
3. Professional Feel - Custom launcher jaisa experience
4. Automation Gateway - Tasker ke saath integrate karein
5. Productivity - Time saving for repetitive tasks

Real-world use cases:
• WiFi/Bluetooth toggle
• Quick backup button
• System info widget
• Speed test shortcut
• IP address checker
• Quick note taker
• Server status checker
• Database backup button
• Cache cleaner
• Network scanner trigger

---

[SECTION 2: INSTALLATION & SETUP - 3:00 to 5:30]
─────────────────────────────────────────────────────────────────────────────

Ab install karte hain Termux:Widget ko!

⚠️ IMPORTANT: F-Droid se install karein, Play Store se NAHI!

Step 1: Install Termux:Widget

    # F-Droid app kholen
    # Search: Termux:Widget
    # Install button press karein

Step 2: Termux mein setup

    # Shortcuts directory create karein
    mkdir -p ~/.shortcuts

    # Verify directory created
    ls -la ~ | grep shortcuts

    # Optional: Tasker directory bhi
    mkdir -p ~/.termux/tasker

Directory structure samjhein:

    ~/.shortcuts/              # Main shortcuts folder
    ├── script1.sh            # Direct shortcut
    ├── script2.sh            # Another shortcut
    └── folder/               # Folder of shortcuts
        ├── script3.sh
        └── script4.sh

Important Paths:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX WIDGET PATHS                                   │
├─────────────────────────────────────────────────────────────────────────┤
│ ~/.shortcuts/           │ Home screen widget scripts                    │
│ ~/.shortcuts/tasks/     │ Tasker integration scripts                    │
│ ~/.termux/tasker/       │ Alternative Tasker scripts location           │
│ ~/.termux/boot/         │ Boot scripts (different from widgets)         │
└─────────────────────────────────────────────────────────────────────────┘

Step 3: Widget Add Karna

1. Home screen pe long press karein
2. "Widgets" option select karein
3. Scroll karke "Termux:Widget" dhundhein
4. Hold and drag to home screen
5. Widget show karega scripts list

Widget sizes available:
• Small (1x1) - Single script name
• Medium (2x1) - Multiple scripts list
• Large (2x2) - Folder with many scripts

---

[SECTION 3: CREATING YOUR FIRST WIDGET - 5:30 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye apna pehla widget banate hain!

[EXAMPLE 1: Simple Hello Widget]

    nano ~/.shortcuts/hello.sh

Script content:

    #!/bin/bash
    # Simple Hello Widget
    
    echo "Hello from Termux Widget!"
    echo "Current time: $(date)"
    sleep 3

Make executable:

    chmod +x ~/.shortcuts/hello.sh

Test karein:
1. Home screen pe widget add karein
2. Widget mein "hello" script dikhega
3. Tap karein
4. Terminal open hoga aur script run hoga

[EXAMPLE 2: System Info Widget]

    nano ~/.shortcuts/sysinfo.sh

    #!/bin/bash
    # System Information Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       SYSTEM INFORMATION"
    echo "═══════════════════════════════════"
    echo ""
    echo "📅 Date: $(date '+%Y-%m-%d %H:%M:%S')"
    echo "📱 Device: $(getprop ro.product.model)"
    echo "🤖 Android: $(getprop ro.build.version.release)"
    echo ""
    echo "═══════════════════════════════════"
    echo "       MEMORY STATUS"
    echo "═══════════════════════════════════"
    free -h
    echo ""
    echo "═══════════════════════════════════"
    echo "       DISK USAGE"
    echo "═══════════════════════════════════"
    df -h / 2>/dev/null | tail -1
    echo ""
    echo "Press Enter to close..."
    read

Make executable:

    chmod +x ~/.shortcuts/sysinfo.sh

[EXAMPLE 3: Quick Note Widget]

    nano ~/.shortcuts/quicknote.sh

    #!/bin/bash
    # Quick Note Widget
    
    NOTES_FILE="/sdcard/quick_notes.txt"
    
    echo "═══════════════════════════════════"
    echo "         QUICK NOTE"
    echo "═══════════════════════════════════"
    echo ""
    echo "Enter your note (press Enter to save):"
    read note
    
    if [ -n "$note" ]; then
        echo "[$(date '+%Y-%m-%d %H:%M')] $note" >> "$NOTES_FILE"
        echo ""
        echo "✅ Note saved!"
        echo ""
        echo "Recent notes:"
        tail -5 "$NOTES_FILE"
    else
        echo "No note entered."
    fi
    
    sleep 2

---

[SECTION 4: WIDGET EXAMPLES - NETWORK TOOLS - 8:00 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab network related widgets banate hain!

[EXAMPLE 4: IP Address Widget]

    nano ~/.shortcuts/check-ip.sh

    #!/bin/bash
    # IP Address Checker Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       IP ADDRESS INFO"
    echo "═══════════════════════════════════"
    echo ""
    
    # Internal IP
    echo "🏠 Internal IP:"
    ifconfig 2>/dev/null | grep -o 'inet addr:[0-9.]*' | cut -d: -f2
    echo ""
    
    # External IP
    echo "🌍 External IP:"
    external_ip=$(curl -s ifconfig.me 2>/dev/null)
    if [ -n "$external_ip" ]; then
        echo "   $external_ip"
    else
        echo "   Unable to fetch (check internet)"
    fi
    echo ""
    
    # WiFi Info
    echo "📶 WiFi Info:"
    termux-wifi-connectioninfo 2>/dev/null | python3 -c "
import sys, json
try:
    data = json.load(sys.stdin)
    print(f\"   SSID: {data.get('ssid', 'N/A')}\")
    print(f\"   IP: {data.get('ip', 'N/A')}\")
except:
    print('   WiFi not connected or API not available')
" 2>/dev/null || echo "   Install termux-api for WiFi info"
    
    echo ""
    echo "Press Enter to close..."
    read

[EXAMPLE 5: Speed Test Widget]

    nano ~/.shortcuts/speedtest.sh

    #!/bin/bash
    # Speed Test Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "         SPEED TEST"
    echo "═══════════════════════════════════"
    echo ""
    
    # Check if speedtest-cli installed
    if ! command -v speedtest-cli &> /dev/null; then
        echo "Installing speedtest-cli..."
        pkg install speedtest-cli -y 2>/dev/null || pip install speedtest-cli
    fi
    
    echo "Running speed test..."
    echo "Please wait..."
    echo ""
    
    speedtest-cli --simple 2>/dev/null || {
        echo "Speed test failed. Check internet connection."
    }
    
    echo ""
    echo "Press Enter to close..."
    read

[EXAMPLE 6: WiFi Toggle Widget]

    nano ~/.shortcuts/wifi-toggle.sh

    #!/bin/bash
    # WiFi Toggle Widget
    
    # Check current WiFi state
    wifi_state=$(termux-wifi-connectioninfo 2>/dev/null | grep -c "ssid" || echo "0")
    
    if [ "$wifi_state" -gt 0 ]; then
        echo "Turning WiFi OFF..."
        termux-wifi-enable false
        sleep 1
        echo "WiFi is now OFF"
    else
        echo "Turning WiFi ON..."
        termux-wifi-enable true
        sleep 3
        echo "WiFi is now ON"
        # Show connected network
        termux-wifi-connectioninfo 2>/dev/null | python3 -c "
import sys, json
try:
    data = json.load(sys.stdin)
    print(f\"Connected to: {data.get('ssid', 'Unknown')}\")
except:
    print('Connecting...')
" 2>/dev/null
    fi
    
    sleep 2

[EXAMPLE 7: Network Scanner Widget]

    nano ~/.shortcuts/network-scan.sh

    #!/bin/bash
    # Quick Network Scanner Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       NETWORK SCANNER"
    echo "═══════════════════════════════════"
    echo ""
    
    # Get local network
    local_ip=$(ifconfig 2>/dev/null | grep -o 'inet addr:[0-9.]*' | head -1 | cut -d: -f2)
    network="${local_ip%.*}.0/24"
    
    echo "Scanning network: $network"
    echo "This may take a moment..."
    echo ""
    
    # Quick ping sweep
    if command -v nmap &> /dev/null; then
        nmap -sn "$network" 2>/dev/null | grep "Nmap scan"
    else
        echo "Installing nmap..."
        pkg install nmap -y
        nmap -sn "$network" 2>/dev/null | grep "Nmap scan"
    fi
    
    echo ""
    echo "Press Enter to close..."
    read

---

[SECTION 5: WIDGET EXAMPLES - SYSTEM TOOLS - 11:00 to 13:30]
─────────────────────────────────────────────────────────────────────────────

Ab system related widgets banate hain!

[EXAMPLE 8: Battery Info Widget]

    nano ~/.shortcuts/battery.sh

    #!/bin/bash
    # Battery Information Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       BATTERY STATUS"
    echo "═══════════════════════════════════"
    echo ""
    
    termux-battery-status 2>/dev/null | python3 -c "
import sys, json
try:
    data = json.load(sys.stdin)
    level = data.get('percentage', 'N/A')
    status = data.get('status', 'N/A')
    health = data.get('health', 'N/A')
    temp = data.get('temperature', 'N/A')
    
    print(f'🔋 Level: {level}%')
    print(f'⚡ Status: {status}')
    print(f'💚 Health: {health}')
    if temp != 'N/A':
        print(f'🌡️ Temperature: {temp}°C')
    
    # Battery bar
    bar_length = int(level / 5)
    bar = '█' * bar_length + '░' * (20 - bar_length)
    print(f'\n[{bar}] {level}%')
except:
    print('Unable to get battery info')
    print('Make sure termux-api is installed')
" || echo "Install termux-api package"
    
    echo ""
    echo "Press Enter to close..."
    read

[EXAMPLE 9: Storage Cleaner Widget]

    nano ~/.shortcuts/clean-cache.sh

    #!/bin/bash
    # Cache Cleaner Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       CACHE CLEANER"
    echo "═══════════════════════════════════"
    echo ""
    
    # Calculate cache size before
    echo "Calculating cache size..."
    cache_before=$(du -sh $PREFIX/var/cache/apt 2>/dev/null | cut -f1)
    echo "Current cache: $cache_before"
    echo ""
    
    # Clean apt cache
    echo "Cleaning package cache..."
    pkg clean
    apt autoremove -y 2>/dev/null
    
    # Clean tmp
    echo "Cleaning temp files..."
    rm -rf $TMPDIR/* 2>/dev/null
    
    # Clean pip cache if exists
    if command -v pip &> /dev/null; then
        echo "Cleaning pip cache..."
        pip cache purge 2>/dev/null
    fi
    
    # Calculate cache size after
    cache_after=$(du -sh $PREFIX/var/cache/apt 2>/dev/null | cut -f1)
    
    echo ""
    echo "✅ Cleaning complete!"
    echo "Cache after: $cache_after"
    echo ""
    
    sleep 2

[EXAMPLE 10: Process Monitor Widget]

    nano ~/.shortcuts/process-monitor.sh

    #!/bin/bash
    # Process Monitor Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       TOP PROCESSES"
    echo "═══════════════════════════════════"
    echo ""
    
    echo "CPU Usage:"
    echo "----------------------------------------"
    ps aux --sort=-%cpu 2>/dev/null | head -10
    echo ""
    echo "Memory Usage:"
    echo "----------------------------------------"
    ps aux --sort=-%mem 2>/dev/null | head -10
    echo ""
    
    # Quick summary
    echo "Summary:"
    echo "  Total processes: $(ps aux | wc -l)"
    echo "  Memory: $(free -h | grep Mem | awk '{print $3 "/" $2}')"
    echo ""
    
    echo "Press Enter to close..."
    read

---

[SECTION 6: ADVANCED WIDGETS - 13:30 to 15:30]
─────────────────────────────────────────────────────────────────────────────

Ab kuch advanced widgets banate hain!

[EXAMPLE 11: Quick Backup Widget]

    nano ~/.shortcuts/quick-backup.sh

    #!/bin/bash
    # Quick Backup Widget
    
    BACKUP_DIR="/sdcard/TermuxBackups"
    DATE=$(date +%Y%m%d_%H%M%S)
    
    clear
    echo "═══════════════════════════════════"
    echo "       QUICK BACKUP"
    echo "═══════════════════════════════════"
    echo ""
    
    mkdir -p "$BACKUP_DIR"
    
    echo "Creating backup..."
    echo "Please wait..."
    echo ""
    
    # Backup scripts
    tar -czf "$BACKUP_DIR/scripts_$DATE.tar.gz" \
        -C ~ shortcuts 2>/dev/null
    
    # Backup important configs
    tar -czf "$BACKUP_DIR/configs_$DATE.tar.gz" \
        -C ~ .bashrc .profile .tmux.conf 2>/dev/null
    
    # Create combined backup
    tar -czf "$BACKUP_DIR/full_backup_$DATE.tar.gz" \
        -C ~ shortcuts .bashrc .profile 2>/dev/null
    
    echo "✅ Backup complete!"
    echo ""
    echo "Backup saved to: $BACKUP_DIR"
    echo "Files created:"
    ls -lh "$BACKUP_DIR" | tail -5
    echo ""
    
    # Keep only last 5 backups
    cd "$BACKUP_DIR"
    ls -t full_backup_*.tar.gz 2>/dev/null | tail -n +6 | xargs rm -f 2>/dev/null
    
    sleep 3

[EXAMPLE 12: Server Status Widget]

    nano ~/.shortcuts/server-status.sh

    #!/bin/bash
    # Server Status Check Widget
    
    # Define servers to check
    SERVERS=(
        "google.com:80:Google"
        "github.com:443:GitHub"
        "youtube.com:443:YouTube"
    )
    
    clear
    echo "═══════════════════════════════════"
    echo "       SERVER STATUS"
    echo "═══════════════════════════════════"
    echo ""
    
    for server in "${SERVERS[@]}"; do
        IFS=':' read -r host port name <<< "$server"
        
        if timeout 3 bash -c "echo >/dev/tcp/$host/$port" 2>/dev/null; then
            echo "✅ $name ($host) - Online"
        else
            echo "❌ $name ($host) - Offline"
        fi
    done
    
    echo ""
    echo "Checked at: $(date '+%H:%M:%S')"
    echo ""
    echo "Press Enter to close..."
    read

[EXAMPLE 13: QR Code Generator Widget]

    nano ~/.shortcuts/qr-code.sh

    #!/bin/bash
    # QR Code Generator Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       QR CODE GENERATOR"
    echo "═══════════════════════════════════"
    echo ""
    
    echo "Enter text/URL for QR code:"
    read text
    
    if [ -z "$text" ]; then
        echo "No input provided!"
        sleep 2
        exit
    fi
    
    # Install qrencode if not present
    if ! command -v qrencode &> /dev/null; then
        echo "Installing qrencode..."
        pkg install qrencode -y
    fi
    
    OUTPUT="/sdcard/qr_code.png"
    
    qrencode -o "$OUTPUT" "$text"
    
    echo ""
    echo "✅ QR Code generated!"
    echo "Saved to: $OUTPUT"
    echo ""
    echo "Content: $text"
    
    # Optional: Share the QR code
    termux-share "$OUTPUT" 2>/dev/null
    
    sleep 2

[EXAMPLE 14: Quick Command Widget]

    nano ~/.shortcuts/quick-cmd.sh

    #!/bin/bash
    # Quick Command Widget
    
    clear
    echo "═══════════════════════════════════"
    echo "       QUICK COMMANDS"
    echo "═══════════════════════════════════"
    echo ""
    
    echo "Select a command:"
    echo ""
    echo "1) Show IP Address"
    echo "2) Check Battery"
    echo "3) Clear Cache"
    echo "4) Update Packages"
    echo "5) Show Storage"
    echo "6) Kill Background Apps"
    echo ""
    echo "Enter choice (1-6):"
    read choice
    
    case $choice in
        1) curl -s ifconfig.me ;;
        2) termux-battery-status ;;
        3) pkg clean && echo "Cache cleared!" ;;
        4) pkg update && pkg upgrade -y ;;
        5) df -h ;;
        6) am kill-all 2>/dev/null && echo "Background apps killed" ;;
        *) echo "Invalid choice" ;;
    esac
    
    echo ""
    sleep 2

---

[SECTION 7: TASKER INTEGRATION - 15:30 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Ab Tasker integration dekhte hain!

Tasker ek powerful automation app hai Android ke liye. Termux:Tasker se 
integration karein.

Installation:
1. Tasker install karein (Play Store)
2. Termux:Tasker install karein (F-Droid)

Tasker Scripts Directory:

    mkdir -p ~/.termux/tasker

Tasker Script Example:

    nano ~/.termux/tasker/battery-alert.sh

    #!/bin/bash
    # Battery Alert for Tasker
    
    # Get battery level
    battery=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')
    
    if [ "$battery" -lt 20 ]; then
        termux-notification --title "Low Battery" --content "Battery at $battery%!"
        echo "low"
    else
        echo "ok"
    fi

Tasker Setup Steps:
1. Tasker → Profiles → New Profile
2. State → Power → Battery Level
3. Set range (e.g., 0-20)
4. Add Task → Plugin → Termux:Tasker
5. Select script: battery-alert.sh

Voice Commands with Tasker:

    nano ~/.termux/tasker/voice-command.sh

    #!/bin/bash
    # Voice Command Handler
    
    # Get command from Tasker variable
    command="%VOICE_COMMAND"
    
    case "$command" in
        "wifi on")
            termux-wifi-enable true
            ;;
        "wifi off")
            termux-wifi-enable false
            ;;
        "battery")
            termux-battery-status
            ;;
        "ip")
            curl -s ifconfig.me
            ;;
        *)
            echo "Unknown command: $command"
            ;;
    esac

Quick Settings Tiles (Android 7+):

Termux scripts ko Quick Settings panel mein add karein:

    # Create tile script
    nano ~/.shortcuts/tile-wifi.sh

    #!/bin/bash
    # Quick Settings Tile - WiFi Toggle
    
    wifi_state=$(termux-wifi-connectioninfo 2>/dev/null | grep -c "ssid")
    
    if [ "$wifi_state" -gt 0 ]; then
        termux-wifi-enable false
        termux-toast "WiFi Disabled"
    else
        termux-wifi-enable true
        termux-toast "WiFi Enabled"
    fi

Notification Shortcuts:

    nano ~/.shortcuts/notification-controls.sh

    #!/bin/bash
    # Notification with Action Buttons
    
    termux-notification \
        --title "Termux Controls" \
        --content "Quick actions available" \
        --action "termux-wifi-enable true" \
        --button1 "WiFi On" \
        --button1-action "termux-wifi-enable true" \
        --button2 "WiFi Off" \
        --button2-action "termux-wifi-enable false" \
        --button3 "Status" \
        --button3-action "termux-battery-status"

---

[SECTION 8: WIDGET BEST PRACTICES - 17:30 to 19:00]
─────────────────────────────────────────────────────────────────────────────

Widget banate waqt yaad rakhein ye best practices:

1. SHEBANG LINE
   - Hamesha #!/bin/bash first line mein
   - Ensures script runs correctly

2. EXECUTABLE PERMISSION
   - chmod +x script.sh zaroor karein
   - Without this, script run nahi hoga

3. FULL PATHS
   - Cron aur widgets mein limited PATH
   - Use /data/data/com.termux/files/usr/bin/...

4. ERROR HANDLING
   - Check if commands exist
   - Use command -v || pkg install

5. USER FEEDBACK
   - Show progress messages
   - Use termux-toast for quick feedback
   - Use termux-notification for results

6. TIMEOUT
   - Long operations mein timeout use karein
   - Network operations ke liye important

7. CLEANUP
   - Temporary files delete karein
   - Old backups rotate karein

Organized Folder Structure:

    ~/.shortcuts/
    ├── network/
    │   ├── check-ip.sh
    │   ├── wifi-toggle.sh
    │   └── speedtest.sh
    ├── system/
    │   ├── battery.sh
    │   ├── sysinfo.sh
    │   └── clean-cache.sh
    ├── backup/
    │   ├── quick-backup.sh
    │   └── restore.sh
    └── tools/
        ├── qr-code.sh
        ├── quicknote.sh
        └── clipboard.sh

---

[SECTION 9: SUMMARY & HOMEWORK - 19:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Termux Widgets & Shortcuts ka chapter complete! Let's summarize:

✅ Termux:Widget installation from F-Droid
✅ ~/.shortcuts directory setup
✅ Single-tap script creation
✅ 15+ practical widget examples
✅ Network tools widgets
✅ System tools widgets
✅ Tasker integration
✅ Voice commands setup
✅ Quick settings tiles
✅ Notification shortcuts
✅ Best practices

Important Commands:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 44 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ mkdir -p ~/.shortcuts          │ Create shortcuts directory             │
│ chmod +x script.sh             │ Make script executable                 │
│ termux-toast "message"         │ Show toast notification                │
│ termux-notification ...        │ Create notification                    │
│ termux-wifi-enable true/false  │ Toggle WiFi                            │
│ termux-battery-status          │ Get battery info                       │
│ termux-share file              │ Share file                             │
│ termux-clipboard-set "text"    │ Set clipboard                          │
│ curl -s ifconfig.me            │ Get external IP                        │
│ qrencode -o qr.png "text"      │ Generate QR code                       │
└─────────────────────────────────────────────────────────────────────────┘

HOMEWORK:
1. Ek WiFi toggle widget banao
2. Ek battery info widget banao
3. Ek quick note widget banao
4. Ek custom widget banao apni need ke hisaab se

Next Chapter 45 mein hum SSH Server setup seekhenge!

Agar video helpful lagi:
👍 Like karein
🔔 Subscribe karein
💬 Questions comment mein poochein

Thank you for watching! See you in Chapter 45!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Termux:Widget Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX:WIDGET ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android Home Screen                           │   │
│   │                                                                   │   │
│   │   ┌─────────────────┐                                            │   │
│   │   │ Termux:Widget   │                                            │   │
│   │   │ ┌─────────────┐ │                                            │   │
│   │   │ │ script1.sh  │ │  ← Tap to execute                          │   │
│   │   │ │ script2.sh  │ │                                            │   │
│   │   │ │ folder/     │ │                                            │   │
│   │   │ └─────────────┘ │                                            │   │
│   │   └─────────────────┘                                            │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                 ~/.shortcuts/ directory                          │   │
│   │                                                                   │   │
│   │   ├── script1.sh          (Direct shortcut)                      │   │
│   │   ├── script2.sh          (Direct shortcut)                      │   │
│   │   └── folder/             (Folder of shortcuts)                  │   │
│   │       ├── script3.sh                                             │   │
│   │       └── script4.sh                                             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Script Execution                              │   │
│   │                                                                   │   │
│   │   1. Termux app opens (minimized window)                        │   │
│   │   2. Script runs with bash interpreter                          │   │
│   │   3. Output displays in terminal                                │   │
│   │   4. Terminal closes when script completes                      │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Directory Structure

```bash
# Main shortcuts directory
~/.shortcuts/

# Tasker integration directory
~/.termux/tasker/

# Boot scripts directory (different from widgets)
~/.termux/boot/

# Recommended organization
~/.shortcuts/
├── network/
│   ├── check-ip.sh
│   ├── wifi-toggle.sh
│   ├── speedtest.sh
│   └── network-scan.sh
├── system/
│   ├── battery.sh
│   ├── sysinfo.sh
│   ├── storage.sh
│   └── clean-cache.sh
├── backup/
│   ├── quick-backup.sh
│   ├── backup-configs.sh
│   └── restore.sh
├── tools/
│   ├── qr-code.sh
│   ├── quicknote.sh
│   ├── clipboard.sh
│   └── timer.sh
└── development/
    ├── git-pull.sh
    ├── server-start.sh
    └── log-view.sh
```

### 3. Widget Script Template

```bash
#!/bin/bash
#===============================================
# Script Name: [name].sh
# Description: [What the script does]
# Author: [Your name]
# Version: 1.0
#===============================================

# Clear screen for clean output
clear

# Header
echo "═══════════════════════════════════"
echo "       [WIDGET NAME]"
echo "═══════════════════════════════════"
echo ""

# Main logic here
# ...

# Footer
echo ""
echo "Press Enter to close..."
read

# Or for auto-close
# sleep 3
```

### 4. Executable Permissions

```bash
# Make single script executable
chmod +x ~/.shortcuts/script.sh

# Make all scripts executable
chmod +x ~/.shortcuts/*.sh

# Make all scripts in subdirectories executable
find ~/.shortcuts -type f -name "*.sh" -exec chmod +x {} \;

# Verify permissions
ls -la ~/.shortcuts/
```

### 5. Widget Execution Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    WIDGET EXECUTION FLOW                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   User taps widget item                                                 │
│           │                                                              │
│           ▼                                                              │
│   Termux:Widget app receives intent                                     │
│           │                                                              │
│           ▼                                                              │
│   Termux app launches (if not running)                                  │
│           │                                                              │
│           ▼                                                              │
│   Script file is read from ~/.shortcuts/                                │
│           │                                                              │
│           ▼                                                              │
│   Bash interpreter executes script                                      │
│           │                                                              │
│           ▼                                                              │
│   Script runs with user's environment                                   │
│           │                                                              │
│           ▼                                                              │
│   Output displays in Termux window                                      │
│           │                                                              │
│           ▼                                                              │
│   Script completes or user exits                                        │
│           │                                                              │
│           ▼                                                              │
│   Termux window closes/minimizes                                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 COMPLETE WIDGET EXAMPLES

### Widget 1: WiFi Toggle

```bash
#!/bin/bash
# WiFi Toggle Widget

# Check current WiFi state
wifi_state=$(termux-wifi-connectioninfo 2>/dev/null | grep -c "ssid" || echo "0")

if [ "$wifi_state" -gt 0 ]; then
    termux-wifi-enable false
    termux-toast "WiFi Disabled"
else
    termux-wifi-enable true
    sleep 2
    termux-toast "WiFi Enabled"
fi
```

### Widget 2: Quick Note

```bash
#!/bin/bash
# Quick Note Widget

NOTES_FILE="/sdcard/quick_notes.txt"

echo "═══════════════════════════════════"
echo "         QUICK NOTE"
echo "═══════════════════════════════════"
echo ""
echo "Enter your note:"
read note

if [ -n "$note" ]; then
    echo "[$(date '+%Y-%m-%d %H:%M')] $note" >> "$NOTES_FILE"
    echo "✅ Note saved!"
else
    echo "No note entered."
fi

sleep 2
```

### Widget 3: System Info

```bash
#!/bin/bash
# System Info Widget

clear
echo "═══════════════════════════════════"
echo "       SYSTEM INFORMATION"
echo "═══════════════════════════════════"
echo ""
echo "📅 Date: $(date '+%Y-%m-%d %H:%M:%S')"
echo "📱 Device: $(getprop ro.product.model)"
echo "🤖 Android: $(getprop ro.build.version.release)"
echo ""
echo "--- Memory ---"
free -h
echo ""
echo "--- Storage ---"
df -h / 2>/dev/null | tail -1
echo ""
read -p "Press Enter to close..."
```

### Widget 4: Speed Test

```bash
#!/bin/bash
# Speed Test Widget

clear
echo "═══════════════════════════════════"
echo "         SPEED TEST"
echo "═══════════════════════════════════"
echo ""

if ! command -v speedtest-cli &> /dev/null; then
    echo "Installing speedtest-cli..."
    pkg install speedtest-cli -y 2>/dev/null || pip install speedtest-cli
fi

echo "Running speed test..."
speedtest-cli --simple

echo ""
read -p "Press Enter to close..."
```

### Widget 5: IP Address

```bash
#!/bin/bash
# IP Address Widget

clear
echo "═══════════════════════════════════"
echo "       IP ADDRESS INFO"
echo "═══════════════════════════════════"
echo ""

echo "🏠 Internal IP:"
ifconfig 2>/dev/null | grep "inet " | grep -v 127.0.0.1 | awk '{print $2}'

echo ""
echo "🌍 External IP:"
curl -s --connect-timeout 5 ifconfig.me 2>/dev/null || echo "Unable to fetch"

echo ""
read -p "Press Enter to close..."
```

### Widget 6: Battery Info

```bash
#!/bin/bash
# Battery Info Widget

clear
echo "═══════════════════════════════════"
echo "       BATTERY STATUS"
echo "═══════════════════════════════════"
echo ""

termux-battery-status 2>/dev/null | python3 -c "
import sys, json
try:
    data = json.load(sys.stdin)
    level = data.get('percentage', 'N/A')
    status = data.get('status', 'N/A')
    health = data.get('health', 'N/A')
    
    print(f'🔋 Level: {level}%')
    print(f'⚡ Status: {status}')
    print(f'💚 Health: {health}')
    
    # Visual bar
    bar_length = int(level / 5)
    bar = '█' * bar_length + '░' * (20 - bar_length)
    print(f'\n[{bar}] {level}%')
except:
    print('Install termux-api')
" || echo "Install termux-api package"

echo ""
read -p "Press Enter to close..."
```

### Widget 7: Cache Cleaner

```bash
#!/bin/bash
# Cache Cleaner Widget

clear
echo "═══════════════════════════════════"
echo "       CACHE CLEANER"
echo "═══════════════════════════════════"
echo ""

echo "Cleaning package cache..."
pkg clean 2>/dev/null

echo "Cleaning temp files..."
rm -rf $TMPDIR/* 2>/dev/null

echo "Running autoremove..."
apt autoremove -y 2>/dev/null

echo ""
echo "✅ Cleaning complete!"
echo ""
sleep 2
```

### Widget 8: Quick Backup

```bash
#!/bin/bash
# Quick Backup Widget

BACKUP_DIR="/sdcard/TermuxBackups"
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p "$BACKUP_DIR"

echo "Creating backup..."

tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" \
    -C ~ shortcuts .bashrc .profile 2>/dev/null

echo "✅ Backup saved to $BACKUP_DIR"

# Keep only last 5 backups
cd "$BACKUP_DIR"
ls -t backup_*.tar.gz 2>/dev/null | tail -n +6 | xargs rm -f 2>/dev/null

sleep 2
```

### Widget 9: QR Code Generator

```bash
#!/bin/bash
# QR Code Generator Widget

clear
echo "═══════════════════════════════════"
echo "       QR CODE GENERATOR"
echo "═══════════════════════════════════"
echo ""

echo "Enter text/URL:"
read text

[ -z "$text" ] && exit

if ! command -v qrencode &> /dev/null; then
    pkg install qrencode -y
fi

OUTPUT="/sdcard/qr_code.png"
qrencode -o "$OUTPUT" "$text"

echo ""
echo "✅ QR Code saved to: $OUTPUT"

termux-share "$OUTPUT" 2>/dev/null

sleep 2
```

### Widget 10: Network Scanner

```bash
#!/bin/bash
# Network Scanner Widget

clear
echo "═══════════════════════════════════"
echo "       NETWORK SCANNER"
echo "═══════════════════════════════════"
echo ""

# Get local network
local_ip=$(ifconfig 2>/dev/null | grep "inet " | grep -v 127.0.0.1 | awk '{print $2}' | head -1)
network="${local_ip%.*}.0/24"

echo "Scanning: $network"
echo ""

if ! command -v nmap &> /dev/null; then
    pkg install nmap -y
fi

nmap -sn "$network" 2>/dev/null | grep "Nmap scan"

echo ""
read -p "Press Enter to close..."
```

### Widget 11: Server Status

```bash
#!/bin/bash
# Server Status Widget

clear
echo "═══════════════════════════════════"
echo "       SERVER STATUS"
echo "═══════════════════════════════════"
echo ""

SERVERS=(
    "google.com:80:Google"
    "github.com:443:GitHub"
    "youtube.com:443:YouTube"
)

for server in "${SERVERS[@]}"; do
    IFS=':' read -r host port name <<< "$server"
    
    if timeout 3 bash -c "echo >/dev/tcp/$host/$port" 2>/dev/null; then
        echo "✅ $name - Online"
    else
        echo "❌ $name - Offline"
    fi
done

echo ""
echo "Checked: $(date '+%H:%M:%S')"
echo ""
read -p "Press Enter to close..."
```

### Widget 12: Clipboard Manager

```bash
#!/bin/bash
# Clipboard Manager Widget

HISTORY_FILE=~/.clipboard_history

clear
echo "═══════════════════════════════════"
echo "       CLIPBOARD MANAGER"
echo "═══════════════════════════════════"
echo ""

echo "1) Save current clipboard"
echo "2) View history"
echo "3) Clear history"
echo ""
echo "Choice:"
read choice

case $choice in
    1)
        content=$(termux-clipboard-get 2>/dev/null)
        echo "[$(date '+%H:%M')] $content" >> "$HISTORY_FILE"
        echo "Saved: $content"
        ;;
    2)
        [ -f "$HISTORY_FILE" ] && tail -10 "$HISTORY_FILE" || echo "No history"
        ;;
    3)
        rm -f "$HISTORY_FILE"
        echo "History cleared"
        ;;
esac

sleep 2
```

### Widget 13: Timer

```bash
#!/bin/bash
# Timer Widget

clear
echo "═══════════════════════════════════"
echo "           TIMER"
echo "═══════════════════════════════════"
echo ""

echo "Enter minutes:"
read minutes

[ -z "$minutes" ] && exit

seconds=$((minutes * 60))

echo ""
echo "Timer set for $minutes minutes"
echo "Starting..."
echo ""

while [ $seconds -gt 0 ]; do
    mins=$((seconds / 60))
    secs=$((seconds % 60))
    printf "\r⏱️  %02d:%02d remaining  " $mins $secs
    sleep 1
    ((seconds--))
done

echo ""
echo ""
echo "⏰ TIME'S UP!"
termux-vibrate -d 1000
termux-notification --title "Timer" --content "Time's up!"

sleep 2
```

### Widget 14: Quick Commands Menu

```bash
#!/bin/bash
# Quick Commands Menu Widget

clear
echo "═══════════════════════════════════"
echo "       QUICK COMMANDS"
echo "═══════════════════════════════════"
echo ""

echo "1) Show IP Address"
echo "2) Check Battery"
echo "3) Clear Cache"
echo "4) Update Packages"
echo "5) Show Storage"
echo "6) System Info"
echo ""
echo "Choice:"
read choice

case $choice in
    1) curl -s ifconfig.me ;;
    2) termux-battery-status ;;
    3) pkg clean && echo "Done!" ;;
    4) pkg update && pkg upgrade -y ;;
    5) df -h ;;
    6) 
        echo "Device: $(getprop ro.product.model)"
        echo "Android: $(getprop ro.build.version.release)"
        free -h
        ;;
esac

echo ""
sleep 2
```

### Widget 15: Weather

```bash
#!/bin/bash
# Weather Widget

clear
echo "═══════════════════════════════════"
echo "           WEATHER"
echo "═══════════════════════════════════"
echo ""

# You can change the city
CITY="Delhi"

if command -v curl &> /dev/null; then
    weather=$(curl -s "wttr.in/$CITY?format=3" 2>/dev/null)
    echo "📍 $weather"
    echo ""
    
    # Detailed weather
    curl -s "wttr.in/$CITY?0" 2>/dev/null | head -15
else
    echo "curl not available"
fi

echo ""
read -p "Press Enter to close..."
```

---

## 📋 COMMANDS REFERENCE

### Directory Setup Commands

```bash
# Create shortcuts directory
mkdir -p ~/.shortcuts

# Create tasker directory
mkdir -p ~/.termux/tasker

# Create organized structure
mkdir -p ~/.shortcuts/{network,system,backup,tools,dev}

# List all shortcuts
ls -la ~/.shortcuts/

# Find all script files
find ~/.shortcuts -name "*.sh"
```

### Permission Commands

```bash
# Make script executable
chmod +x ~/.shortcuts/script.sh

# Make all scripts executable
chmod +x ~/.shortcuts/*.sh

# Make all scripts executable recursively
find ~/.shortcuts -type f -name "*.sh" -exec chmod +x {} \;

# Check permissions
ls -la ~/.shortcuts/
```

### Termux API Commands for Widgets

```bash
# Toast notification
termux-toast "Message here"

# Notification
termux-notification --title "Title" --content "Content"

# WiFi control
termux-wifi-enable true
termux-wifi-enable false

# Battery status
termux-battery-status

# Clipboard
termux-clipboard-get
termux-clipboard-set "text"

# Share file
termux-share /path/to/file

# Vibrate
termux-vibrate -d 500

# Torch/Flashlight
termux-torch on
termux-torch off

# Volume
termux-volume music 10

# Contact list
termux-contact-list

# Send SMS
termux-sms-send -n number "message"

# Phone call
termux-telephony-call number

# Location
termux-location

# Camera photo
termux-camera-photo photo.jpg
```

### Network Commands for Widgets

```bash
# External IP
curl -s ifconfig.me

# Internal IP
ifconfig | grep "inet " | grep -v 127.0.0.1

# WiFi info
termux-wifi-connectioninfo

# Network scan (requires nmap)
nmap -sn 192.168.1.0/24

# Speed test (requires speedtest-cli)
speedtest-cli --simple

# Check port
timeout 3 bash -c "echo >/dev/tcp/host/port"
```

### System Commands for Widgets

```bash
# Device info
getprop ro.product.model
getprop ro.build.version.release

# Memory
free -h

# Storage
df -h /

# Processes
ps aux --sort=-%cpu | head -10

# CPU info
cat /proc/cpuinfo | grep "model name" | head -1

# Uptime
uptime

# Clean cache
pkg clean
apt autoremove -y
```

### File Commands for Widgets

```bash
# Create backup
tar -czf backup.tar.gz -C ~ shortcuts

# Extract backup
tar -xzf backup.tar.gz -C ~

# QR code (requires qrencode)
qrencode -o qr.png "text"

# Quick note
echo "$(date): note" >> /sdcard/notes.txt

# Find files
find /sdcard -name "*.pdf" 2>/dev/null | head -10
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Widget Creation

```bash
# Task: Create a simple greeting widget

# Step 1: Create shortcuts directory
mkdir -p ~/.shortcuts

# Step 2: Create greeting script
cat > ~/.shortcuts/greeting.sh << 'EOF'
#!/bin/bash
clear
echo "═══════════════════════════════════"
echo "         GREETING"
echo "═══════════════════════════════════"
echo ""
hour=$(date +%H)
if [ $hour -lt 12 ]; then
    echo "🌅 Good Morning!"
elif [ $hour -lt 17 ]; then
    echo "☀️ Good Afternoon!"
elif [ $hour -lt 21 ]; then
    echo "🌆 Good Evening!"
else
    echo "🌙 Good Night!"
fi
echo ""
echo "Time: $(date '+%H:%M:%S')"
echo "Date: $(date '+%A, %B %d, %Y')"
sleep 3
EOF

# Step 3: Make executable
chmod +x ~/.shortcuts/greeting.sh

# Step 4: Add widget to home screen
# Long press home screen → Widgets → Termux:Widget → Drag to screen

# Step 5: Test by tapping the widget
```

### Exercise 2: Network Widget Suite

```bash
# Task: Create multiple network-related widgets

# Create network folder
mkdir -p ~/.shortcuts/network

# Widget 1: Check IP
cat > ~/.shortcuts/network/check-ip.sh << 'EOF'
#!/bin/bash
echo "External IP: $(curl -s ifconfig.me)"
echo "Internal IP: $(ifconfig | grep 'inet ' | grep -v 127.0.0.1 | awk '{print $2}')"
sleep 3
EOF

# Widget 2: WiFi Toggle
cat > ~/.shortcuts/network/wifi-toggle.sh << 'EOF'
#!/bin/bash
state=$(termux-wifi-connectioninfo 2>/dev/null | grep -c ssid)
if [ $state -gt 0 ]; then
    termux-wifi-enable false
    termux-toast "WiFi OFF"
else
    termux-wifi-enable true
    termux-toast "WiFi ON"
fi
EOF

# Widget 3: Speed Test
cat > ~/.shortcuts/network/speedtest.sh << 'EOF'
#!/bin/bash
clear
echo "Running speed test..."
speedtest-cli --simple
sleep 5
EOF

# Make all executable
chmod +x ~/.shortcuts/network/*.sh
```

### Exercise 3: System Monitor Widget

```bash
# Task: Create a comprehensive system monitoring widget

cat > ~/.shortcuts/system-monitor.sh << 'EOF'
#!/bin/bash
clear
echo "╔════════════════════════════════════╗"
echo "║       SYSTEM MONITOR               ║"
echo "╚════════════════════════════════════╝"
echo ""
echo "┌─ DEVICE ─────────────────────────┐"
echo "│ Model: $(getprop ro.product.model)"
echo "│ Android: $(getprop ro.build.version.release)"
echo "│ Uptime: $(uptime -p)"
echo "└──────────────────────────────────┘"
echo ""
echo "┌─ MEMORY ─────────────────────────┐"
free -h | sed 's/^/│ /'
echo "└──────────────────────────────────┘"
echo ""
echo "┌─ STORAGE ────────────────────────┐"
df -h / | tail -1 | awk '{print "│ Used: " $3 " / " $2 " (" $5 ")"}'
echo "└──────────────────────────────────┘"
echo ""
echo "┌─ TOP PROCESSES ──────────────────┐"
ps aux --sort=-%mem | head -6 | sed 's/^/│ /'
echo "└──────────────────────────────────┘"
echo ""
read -p "Press Enter to close..."
EOF

chmod +x ~/.shortcuts/system-monitor.sh
```

### Exercise 4: Quick Backup Widget

```bash
# Task: Create a backup widget with progress notification

cat > ~/.shortcuts/backup.sh << 'EOF'
#!/bin/bash

BACKUP_DIR="/sdcard/Backups"
DATE=$(date +%Y%m%d_%H%M%S)

termux-toast "Starting backup..."

mkdir -p "$BACKUP_DIR"

# Create backup
tar -czf "$BACKUP_DIR/termux_$DATE.tar.gz" \
    -C ~ shortcuts .bashrc .profile 2>/dev/null

# Get size
SIZE=$(du -h "$BACKUP_DIR/termux_$DATE.tar.gz" | cut -f1)

# Notify
termux-notification \
    --title "Backup Complete" \
    --content "Size: $SIZE | Saved to Backups folder"

# Cleanup old backups (keep last 5)
cd "$BACKUP_DIR"
ls -t termux_*.tar.gz 2>/dev/null | tail -n +6 | xargs rm -f 2>/dev/null

termux-toast "Backup saved: $SIZE"
EOF

chmod +x ~/.shortcuts/backup.sh
```

### Exercise 5: Tasker Integration

```bash
# Task: Set up Tasker integration with Termux

# Step 1: Create tasker directory
mkdir -p ~/.termux/tasker

# Step 2: Create a script for Tasker
cat > ~/.termux/tasker/battery-check.sh << 'EOF'
#!/bin/bash
# This script can be called from Tasker

battery=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')

if [ "$battery" -lt 20 ]; then
    echo "low"
    termux-notification --title "Low Battery" --content "Battery at $battery%"
elif [ "$battery" -lt 50 ]; then
    echo "medium"
else
    echo "high"
fi
EOF

chmod +x ~/.termux/tasker/battery-check.sh

# Step 3: In Tasker
# - Create Profile: State → Power → Battery Level (0-20)
# - Add Task: Plugin → Termux:Tasker
# - Select: battery-check.sh
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Widget Not Showing Scripts

```bash
# Cause: Directory not created or wrong location

# Solution: Verify shortcuts directory
ls -la ~/.shortcuts/

# Create if not exists
mkdir -p ~/.shortcuts

# Check correct path
echo $HOME
# Should be: /data/data/com.termux/files/home

# If using wrong path, create symlink
ln -s /data/data/com.termux/files/home/.shortcuts ~/.shortcuts
```

### Problem 2: Script Not Executing

```bash
# Cause: Script not executable

# Solution: Check permissions
ls -la ~/.shortcuts/script.sh

# Make executable
chmod +x ~/.shortcuts/script.sh

# Verify shebang line
head -1 ~/.shortcuts/script.sh
# Should be: #!/bin/bash

# Test script directly
bash ~/.shortcuts/script.sh
```

### Problem 3: "Permission Denied" Error

```bash
# Cause: Missing execute permission or wrong interpreter

# Solution 1: Add execute permission
chmod +x ~/.shortcuts/*.sh

# Solution 2: Check script syntax
bash -n ~/.shortcuts/script.sh

# Solution 3: Check for hidden characters (Windows line endings)
file ~/.shortcuts/script.sh

# Fix if needed
dos2unix ~/.shortcuts/script.sh
# Or
sed -i 's/\r$//' ~/.shortcuts/script.sh
```

### Problem 4: Widget Shows Empty List

```bash
# Cause: No scripts in shortcuts directory

# Solution: Add scripts
echo '#!/bin/bash' > ~/.shortcuts/test.sh
echo 'echo "Hello"' >> ~/.shortcuts/test.sh
chmod +x ~/.shortcuts/test.sh

# Verify
ls ~/.shortcuts/

# Refresh widget
# Remove and re-add widget to home screen
```

### Problem 5: Termux API Commands Not Working

```bash
# Cause: termux-api not installed

# Solution: Install termux-api package
pkg install termux-api -y

# Also install Termux:API app from F-Droid

# Test API
termux-battery-status

# If still not working, check app permissions
# Settings → Apps → Termux:API → Permissions
```

### Problem 6: Widget Closes Immediately

```bash
# Cause: Script has errors or completes too fast

# Solution 1: Add pause at end
echo "read -p 'Press Enter...'" >> ~/.shortcuts/script.sh

# Solution 2: Add sleep
echo "sleep 5" >> ~/.shortcuts/script.sh

# Solution 3: Debug script
bash -x ~/.shortcuts/script.sh
```

### Problem 7: Network Commands Fail

```bash
# Cause: No internet or timeout

# Solution 1: Check internet
ping -c 3 google.com

# Solution 2: Add timeout to curl
curl -s --connect-timeout 10 ifconfig.me

# Solution 3: Use alternative services
curl -s icanhazip.com
curl -s ipecho.net/plain
```

### Problem 8: Tasker Integration Not Working

```bash
# Cause: Wrong directory or permissions

# Solution: Check tasker directory
ls -la ~/.termux/tasker/

# Scripts must be executable
chmod +x ~/.termux/tasker/*.sh

# Check Tasker plugin settings
# Tasker → Task → Plugin → Termux:Tasker
# Ensure correct script is selected
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Widget Showcase**
```
┌────────────────────────────────────┐
│  [Phone Home Screen Mockup]        │
│                                    │
│   📱 Termux Widgets                │
│   ┌────────────┐                   │
│   │ WiFi Toggle│ ← One Tap!        │
│   │ Speed Test │                   │
│   │ Quick Note │                   │
│   └────────────┘                   │
│                                    │
│   HOME SCREEN AUTOMATION           │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Feature List**
```
┌────────────────────────────────────┐
│  ⚡ TERMUX WIDGETS                  │
│                                    │
│  ✅ One-Tap Scripts                │
│  ✅ Home Screen Shortcuts          │
│  ✅ Tasker Integration             │
│  ✅ 15+ Widget Examples            │
│                                    │
│  Chapter 44 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Before/After**
```
┌────────────────────────────────────┐
│  ❌ Before: Open Termux            │
│     Type Command                   │
│     Wait for Output                │
│  ────────────────────────────────  │
│  ✅ After: One Tap                 │
│     Script Runs                    │
│     Done!                          │
│                                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📱 Termux Full Course - Chapter 44: Termux Widgets & Shortcuts

🔥 In this video you'll learn:
• Termux:Widget installation and setup
• Creating home screen shortcuts
• 15+ practical widget examples
• Tasker integration for automation
• Network tools widgets
• System monitoring widgets

⏱️ Timestamps:
0:00 - Introduction
0:50 - Termux:Widget Introduction
3:00 - Installation & Setup
5:30 - Creating Your First Widget
8:00 - Network Tools Widgets
11:00 - System Tools Widgets
13:30 - Advanced Widgets
15:30 - Tasker Integration
17:30 - Best Practices
19:00 - Summary

📥 Required Apps:
• Termux (F-Droid)
• Termux:Widget (F-Droid)
• Termux:API (F-Droid)
• Tasker (Play Store - Optional)

📝 Widget Scripts:
All scripts available in the course materials!

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]

#Termux #TermuxWidgets #T3rmuxk1ng #TermuxCourse #AndroidAutomation #Tasker

---
⚠️ Disclaimer: This video is for educational purposes only.
```

### Tags List

```
termux widgets, termux shortcuts, termux widget tutorial,
termux home screen, termux automation, termux tasker,
termux api, termux course, termux hindi, termux tutorial,
android widgets, android automation, termux scripts,
termux tips, t3rmuxk1ng, termux course hindi,
one tap shortcuts, termux quick settings, termux notification,
termux wifi toggle, termux speed test, termux ip check,
termux system info, termux battery widget, termux backup widget
```

### Hashtags

```
#Termux #TermuxWidgets #TermuxShortcuts #AndroidAutomation 
#TermuxTutorial #TermuxHindi #T3rmuxk1ng #TermuxCourse 
#TaskerIntegration #HomeScreenWidgets #TermuxAPI 
#OneTapScripts #TermuxTips #AndroidHacking
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux Wiki | https://wiki.termux.com/ |
| Termux:Widget GitHub | https://github.com/termux/termux-widget |
| Termux:Tasker GitHub | https://github.com/termux/termux-tasker |
| Tasker Wiki | https://tasker.joaoapps.com/ |

### Related Packages

| Package | Purpose |
|---------|---------|
| termux-api | Termux API commands |
| termux-widget | Home screen widgets |
| termux-tasker | Tasker integration |
| termux-boot | Boot scripts |
| termux-float | Floating terminal |

### Useful Third-Party Tools

| Tool | Purpose |
|------|---------|
| Tasker | Advanced automation |
| Automate | Visual automation |
| MacroDroid | Simple automation |
| QR & Barcode | QR code generation |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 45, verify:

- [ ] Termux:Widget installed from F-Droid
- [ ] ~/.shortcuts directory created
- [ ] At least 3 widgets created and working
- [ ] Scripts have executable permissions
- [ ] Widget appears on home screen
- [ ] Scripts execute correctly when tapped
- [ ] Termux:API installed for API commands
- [ ] Tasker integration attempted (optional)
- [ ] Network widgets tested
- [ ] System widgets tested

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 45: SSH Server Setup in Termux**

- Installing OpenSSH server
- SSH configuration files
- Key-based authentication
- Port forwarding
- SSH tunneling
- Remote access to Android
- Security best practices
- SSH over internet

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
