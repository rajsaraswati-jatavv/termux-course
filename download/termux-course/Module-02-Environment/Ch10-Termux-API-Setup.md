# Chapter 10: Termux API Setup & Overview

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                                                                           ║
║   ████████╗███████╗██████╗ ███╗   ███╗██╗███╗   ██╗ █████╗ ██╗            ║
║   ╚══██╔══╝██╔════╝██╔══██╗████╗ ████║██║████╗  ██║██╔══██╗██║            ║
║      ██║   █████╗  ██████╔╝██╔████╔██║██║██╔██╗ ██║███████║██║            ║
║      ██║   ██╔══╝  ██╔══██╗██║╚██╔╝██║██║██║╚██╗██║██╔══██║██║            ║
║      ██║   ███████╗██║  ██║██║ ╚═╝ ██║██║██║ ╚████║██║  ██║███████╗       ║
║      ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝╚═╝  ╚═══╝╚═╝  ╚═╝╚══════╝       ║
║                                                                           ║
║   █████╗ ██████╗ ██████╗ ██╗   ██╗████████╗    █████╗ ███████╗████████╗   ║
║  ██╔══██╗██╔══██╗██╔══██╗██║   ██║╚══██╔══╝   ██╔══██╗██╔════╝╚══██╔══╝   ║
║  ███████║██████╔╝██████╔╝██║   ██║   ██║      ███████║███████╗   ██║      ║
║  ██╔══██║██╔═══╝ ██╔═══╝ ██║   ██║   ██║      ██╔══██║╚════██║   ██║      ║
║  ██║  ██║██║     ██║     ╚██████╔╝   ██║      ██║  ██║███████║   ██║      ║
║  ╚═╝  ╚═╝╚═╝     ╚═╝      ╚═════╝    ╚═╝      ╚═╝  ╚═╝╚══════╝   ╚═╝      ║
║                                                                           ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                   📱 CONTROL YOUR PHONE FROM TERMINAL 📱                  ║
║                      Camera • SMS • Location • Sensors                    ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 2 - Environment  
> **Chapter:** 10 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Termux:API app and package installation |
| API Commands | Complete list with examples |
| Commands Reference | All API commands covered |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Permission and setup issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 10
Title: Termux API Setup & Overview | Complete API Command Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut special hai - kyunki aaj hum seekhenge Termux ki 
sabse powerful feature ke baare mein - Termux API!

Termux API aapke phone ko ek complete automation machine bana deta hai.
Aap apne phone ko commands se control kar sakte ho - camera on karo,
SMS bhejo, call log dekho, location track karo, notification bhejo,
torch on karo, volume control karo - sab kuch terminal se!

Ye automation ke liye, scripting ke liye, aur penetration testing ke 
liye bahut useful hai. Imagine karein - ek script likho jo automatic
screenshot le, location check kare, aur report bhej de. All possible!

To chaliye shuru karte hain - Termux API Setup & Complete Overview!

Play button dabaiye, video like karein, channel subscribe karein!

---

[SECTION 1: TERMUX API KYA HAI - 0:50 to 3:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle samajhte hain - Termux API kya hai?

Termux by default ek terminal hai - Linux environment. Lekin ye Android 
system ke features tak directly access nahi kar sakta. Camera, SMS, 
calls, storage - ye sab Android ke restricted features hain.

Termux:API ek bridge hai - Termux aur Android system ke beech ka. 
Isse Termux commands se Android features access kar sakta hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                      TERMUX API ARCHITECTURE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────┐         ┌─────────────────┐                       │
│   │   Termux App    │         │  Android OS     │                       │
│   │   (Terminal)    │         │  (System APIs)  │                       │
│   └────────┬────────┘         └────────┬────────┘                       │
│            │                           │                                 │
│            │   ┌───────────────────────┤                                │
│            │   │                       │                                │
│            ▼   ▼                       ▼                                │
│   ┌─────────────────────────────────────────────┐                       │
│   │           Termux:API App                    │                       │
│   │   (Android App with Permissions)           │                       │
│   │                                             │                       │
│   │   • Receives commands from Termux          │                       │
│   │   • Accesses Android features              │                       │
│   │   • Returns results to Termux              │                       │
│   └─────────────────────────────────────────────┘                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Termux API se kya kya kar sakte hain? List impressive hai:

✓ Device Info - Battery, Phone details, IMEI
✓ Media - Camera, Audio recording, Media player
✓ Communication - SMS, Call log, Contacts
✓ Connectivity - WiFi, Location, Telephony
✓ Notifications - Toast, Status bar notifications
✓ Hardware - Torch, Vibration, Brightness, Volume
✓ Storage - File picker, Downloads
✓ Sensors - Accelerometer, Gyroscope, etc.
✓ Biometrics - Fingerprint authentication
✓ Sharing - Share files, text to other apps

Ye sab ROOT ke bina kaam karta hai! 

---

[SECTION 2: API INSTALLATION - 3:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab installation ki baat aate hain. Termux API ke liye DO cheezein chahiye:

1. Termux:API App (Android application)
2. termux-api package (Terminal package)

Dono install hona zaroori hai. Sirf ek se kaam nahi chalega.

[STEP 1: Install Termux:API App]

Pehle F-Droid se Termux:API app install karein:

1. F-Droid app kholen
2. Search karein "Termux:API"
3. Install button press karein
4. Wait for installation

⚠️ IMPORTANT: Termux:API bhi F-Droid se hi install karein!
Play Store wala compatible nahi hoga F-Droid Termux ke saath.

[STEP 2: Install termux-api Package]

Ab Termux terminal kholen aur package install karein:

    pkg install termux-api -y

Ye command termux-api package install karega jisme saare API 
commands hain - termux-battery-status, termux-camera-photo, etc.

[STEP 3: Verify Installation]

Check karein ki package install ho gaya:

    dpkg -l | grep termux-api

Output mein termux-api package dikhna chahiye.

Test karein basic command:

    termux-battery-status

Agar output aaya with battery info - CONGRATULATIONS! API kaam kar raha hai!

Agar error aaya - "Error: Termux:API app not installed" - to app 
install nahi hai ya Galat source se install hai.

---

[SECTION 3: PERMISSIONS SETUP - 6:00 to 8:30]
─────────────────────────────────────────────────────────────────────────────

Ye section BAHUT IMPORTANT hai. Bahut log yahan pe atak jaate hain.

Termux:API app ko Android permissions chahiye hote hain different 
features ke liye. By default kuch permissions granted nahi hote.

Android Settings mein jao:
Settings → Apps → Termux:API → Permissions

Required permissions by feature:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX:API PERMISSIONS REQUIRED                       │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Permission           │ Required For                                    │
├──────────────────────┼──────────────────────────────────────────────────┤
│ Camera               │ termux-camera-photo, termux-camera-info         │
│ Microphone           │ Audio recording                                 │
│ Location             │ termux-location, WiFi scan                      │
│ Phone                │ termux-telephony-*, termux-call-log             │
│ SMS                  │ termux-sms-list, termux-sms-send                │
│ Contacts             │ termux-contact-list                             │
│ Storage              │ termux-storage-get, termux-share                │
│ Nearby Devices       │ termux-wifi-*, Bluetooth features               │
└──────────────────────┴──────────────────────────────────────────────────┘

Permission grant karne ke baad bhi, kuch commands runtime permission 
mangengi pehli baar. Jaise:

    termux-location

First run pe popup aayega: "Allow Termux:API to access device location?"
"Allow" press karein.

Pro Tip: Sab permissions pehle se enable kar do Settings se, 
taaki baad mein problem na ho.

---

[SECTION 4: DEVICE INFO APIs - 8:30 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye API commands ek ek karke explore karte hain. Pehle device 
information wale commands.

[BATTERY STATUS]

    termux-battery-status

Output example:
{
  "battery": 85,
  "percentage": 85,
  "status": "CHARGING",
  "temperature": 32.0,
  "health": "GOOD",
  "plugged": "PLUGGED_AC"
}

Ye JSON format mein data deta hai. Aap isse Python mein parse kar 
sakte ho automation ke liye.

[TELEPHONY DEVICE INFO]

    termux-telephony-deviceinfo

Output:
{
  "device_id": "IMEI_NUMBER",
  "phone_count": 2,
  "phone_type": "GSM",
  "network_type": "LTE",
  "network_operator_name": "Jio",
  "sim_country": "in",
  "sim_operator": "40585",
  "sim_operator_name": "Jio",
  "sim_serial_number": "SIM_SERIAL"
}

[TELEPHONY CELL INFO]

    termux-telephony-cellinfo

Cell tower information deta hai - location tracking ke liye useful.

[WIFI CONNECTION INFO]

    termux-wifi-connectioninfo

Current WiFi connection details:
{
  "bssid": "AA:BB:CC:DD:EE:FF",
  "frequency": 2437,
  "ip": "192.168.1.100",
  "link_speed": 65,
  "mac_address": "11:22:33:44:55:66",
  "network_id": 1,
  "rssi": -45,
  "ssid": "MyWiFi",
  "ssid_hidden": false
}

[WIFI SCAN INFO]

    termux-wifi-scaninfo

Nearby WiFi networks scan karta hai. Penetration testing ke liye 
bahut useful!

[SENSOR INFO]

    termux-sensor -l

Available sensors list deta hai. Specific sensor ke liye:

    termux-sensor -s "accelerometer" -d 5000

Accelerometer data 5 seconds ke liye.

---

[SECTION 5: HARDWARE CONTROL APIs - 11:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Ab hardware control APIs dekhte hain - torch, brightness, volume, vibration.

[TORCH CONTROL]

Flashlight on karein:

    termux-torch on

Flashlight off karein:

    termux-torch off

Simple aur powerful! Penetration testing mein dark areas ke liye useful,
ya automation scripts mein.

[BRIGHTNESS CONTROL]

Brightness set karein (0-255):

    termux-brightness 100

    termux-brightness 255  # Maximum

    termux-brightness 50   # Low

Auto-brightness override ho jaata hai.

[VOLUME CONTROL]

Different streams control kar sakte ho:

    termux-volume stream value

Streams: call, notification, alarm, music, ring, system

Examples:
    termux-volume music 10      # Music volume 50%
    termux-volume music 15      # Music volume max
    termux-volume notification 5

    termux-volume ring 0        # Silent ring
    termux-volume call 10       # Call volume

[VIBRATION]

Phone vibrate karein:

    termux-vibrate

Custom duration (milliseconds):

    termux-vibrate -d 1000    # 1 second

    termux-vibrate -d 3000    # 3 seconds

[CAMERA INFO]

Available cameras list:

    termux-camera-info

Output:
[
  {
    "id": "0",
    "facing": "back",
    "jpeg_output_sizes": [{"width":4160,"height":3120},...],
    "focal_lengths": [1.95],
    "auto_exposure_modes": [...],
    ...
  },
  {
    "id": "1",
    "facing": "front",
    ...
  }
]

[CAMERA PHOTO]

Photo capture karein:

    termux-camera-photo -c 0 photo.jpg

Options:
    -c 0   # Back camera
    -c 1   # Front camera

    termux-camera-photo -c 1 selfie.jpg

Photo current directory mein save hoga.

[FINGERPRINT AUTH]

Biometric authentication:

    termux-fingerprint

Output (if successful):
{
  "auth_result": "AUTH_RESULT_SUCCESS",
  "auth_result_message": "Fingerprint recognized."
}

Useful for secure scripts!

---

[SECTION 6: MEDIA & NOTIFICATION APIs - 14:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Ab media aur notifications dekhte hain.

[NOTIFICATION]

Desktop jaisa notification:

    termux-notification --title "Hello" --content "This is a test notification"

More options:
    termux-notification \
      --title "Download Complete" \
      --content "File saved to downloads" \
      --sound \
      --vibrate 500 \
      --led-color FF0000 \
      --priority high

Options:
    --title         : Notification title
    --content       : Body text
    --sound         : Play notification sound
    --vibrate       : Vibration pattern
    --led-color     : LED color (hex)
    --priority      : low, default, high, max
    --ongoing       : Persistent notification
    --id            : Unique ID for updates
    --action        : Action when tapped
    --button1       : Action button text
    --button1-action: Button action

[TOAST]

Quick popup message:

    termux-toast "Hello World!"

Duration options:
    termux-toast -s "Short toast"    # Short duration
    termux-toast -l "Long toast"     # Long duration

Position (on some Android versions):
    termux-toast -g top "Top toast"
    termux-toast -g bottom "Bottom toast"
    termux-toast -g center "Center toast"

[MEDIA PLAYER]

Audio/video play karein:

    termux-media-player play song.mp3

Commands:
    termux-media-player play <file>
    termux-media-player pause
    termux-media-player resume
    termux-media-player stop
    termux-media-player info

Example workflow:
    termux-media-player play music.mp3
    sleep 30
    termux-media-player pause

[MEDIA SCAN]

Media scanner trigger - gallery mein files dikhane ke liye:

    termux-media-scan /sdcard/Download/photo.jpg

Multiple files:
    termux-media-scan /sdcard/DCIM/*.jpg

[DOWNLOAD]

Download manager se file download:

    termux-download -d /sdcard/Download -t "MyFile.zip" URL

Options:
    -d    : Destination folder
    -t    : Title for notification
    -p    : Path (same as -d)

Example:
    termux-download -d /sdcard/Download "https://example.com/file.pdf"

---

[SECTION 7: COMMUNICATION APIs - 17:00 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Ab communication APIs - SMS, Contacts, Call log.

⚠️ WARNING: Ye features sensitive hain. Ethical use karein!

[CONTACT LIST]

All contacts list:

    termux-contact-list

Output (JSON array):
[
  {
    "name": "John Doe",
    "number": "+919876543210"
  },
  ...
]

Specific contact find karein:
    termux-contact-list | grep -i "John"

[SMS LIST]

SMS messages list:

    termux-sms-list

Options:
    -d, --offset      : Offset from latest
    -l, --limit       : Number of messages
    -n, --number      : Filter by number
    -t, --type        : inbox, sent, draft, outbox

Examples:
    termux-sms-list -l 10           # Last 10 messages
    termux-sms-list -t inbox        # Only inbox
    termux-sms-list -n "+919876543210"  # From specific number

[SMS SEND]

SMS bhejein:

    termux-sms-send -n "+919876543210" "Hello from Termux!"

Options:
    -n, --number      : Recipient number
    -t, --text        : Message text (optional, can use stdin)

From file:
    cat message.txt | termux-sms-send -n "+919876543210"

Multiple recipients:
    termux-sms-send -n "+911111111111" -n "+912222222222" "Broadcast message"

[CALL LOG]

Call history:

    termux-call-log

Options:
    -l, --limit       : Number of entries
    -o, --offset      : Offset from latest

Examples:
    termux-call-log -l 20           # Last 20 calls
    termux-call-log | grep "missed" # Filter missed calls

Output:
[
  {
    "name": "John Doe",
    "number": "+919876543210",
    "duration": 120,
    "type": "incoming",
    "date": 1699999999000
  },
  ...
]

---

[SECTION 8: OTHER APIs - 19:30 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Baki ke APIs bhi dekh lete hain.

[CLIPBOARD]

Clipboard text get karein:

    termux-clipboard-get

Clipboard text set karein:

    termux-clipboard-set "Copied from Termux!"

Useful for automation - data copy karo aur kisi app mein paste karo.

[LOCATION]

GPS location:

    termux-location

Options:
    -p, --provider    : gps, network, passive
    -r, --request     : once, last, updates

Examples:
    termux-location -p gps          # GPS location
    termux-location -p network      # Network-based (faster)
    termux-location -p gps -r last  # Last known location

Output:
{
  "latitude": 28.6139,
  "longitude": 77.2090,
  "altitude": 200.0,
  "accuracy": 10.0,
  "bearing": 0.0,
  "speed": 0.0,
  "elapsedMs": 500,
  "provider": "gps"
}

[STORAGE GET]

File picker dialog:

    termux-storage-get ~/picked_file.txt

Ye Android file picker open karega. User file select karega aur 
wo Termux mein copy ho jaayega.

[SHARE]

Share content to other apps:

    termux-share file.txt

Share text:
    echo "Share this text" | termux-share

Options:
    -a, --action      : send, view, edit
    -c, --content-type: MIME type
    -d, --default     : Use default app

Examples:
    termux-share -c "image/jpeg" photo.jpg
    echo "Hello" | termux-share -c "text/plain"

[INFRARED FREQUENCIES]

IR blaster frequencies (if supported):

    termux-infrared-frequencies

Not all phones have IR blaster.

[WIFI ENABLE/DISABLE]

WiFi toggle:

    termux-wifi-enable true    # Turn on
    termux-wifi-enable false   # Turn off

Requires Android 10+ or special permissions.

---

[SECTION 9: PRACTICAL EXAMPLES - 21:30 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch practical examples dekhte hain jo aap use kar sakte ho.

[EXAMPLE 1: Battery Monitor Script]

    #!/bin/bash
    # battery_monitor.sh
    
    BATTERY=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')
    
    if [ "$BATTERY" -lt 20 ]; then
        termux-notification --title "Low Battery!" --content "Battery is at ${BATTERY}%" --sound
        termux-toast "Battery Low: ${BATTERY}%"
    fi

[EXAMPLE 2: Location Tracker]

    #!/bin/bash
    # location_track.sh
    
    LOCATION=$(termux-location -p gps)
    LAT=$(echo $LOCATION | grep -o '"latitude": [0-9.]*' | grep -o '[0-9.]*')
    LON=$(echo $LOCATION | grep -o '"longitude": [0-9.]*' | grep -o '[0-9.]*')
    
    echo "Latitude: $LAT, Longitude: $LON"
    echo "$(date): $LAT, $LON" >> ~/location_log.txt

[EXAMPLE 3: Auto Brightness by Time]

    #!/bin/bash
    # auto_brightness.sh
    
    HOUR=$(date +%H)
    
    if [ "$HOUR" -ge 20 ] || [ "$HOUR" -lt 6 ]; then
        # Night time - low brightness
        termux-brightness 50
    else
        # Day time - high brightness
        termux-brightness 200
    fi

[EXAMPLE 4: WiFi Scanner]

    #!/bin/bash
    # wifi_scan.sh
    
    echo "Scanning WiFi networks..."
    termux-wifi-scaninfo > ~/wifi_scan_$(date +%Y%m%d_%H%M%S).json
    termux-toast "WiFi scan complete!"

[EXAMPLE 5: SMS Logger]

    #!/bin/bash
    # sms_backup.sh
    
    echo "Backing up SMS..."
    termux-sms-list -l 100 > ~/sms_backup_$(date +%Y%m%d).json
    termux-notification --title "SMS Backup" --content "100 messages backed up"

Ye scripts aap cron jobs ke saath use kar sakte ho automatic 
execution ke liye - jo hum aage ke chapters mein cover karenge.

---

[SECTION 10: SUMMARY - 24:00 to 25:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 10 complete! Let's summarize:

✅ Termux API kya hai - Bridge between Termux and Android
✅ Installation - Termux:API app + termux-api package
✅ Permissions - Settings se enable karein
✅ Device Info APIs - battery, telephony, wifi, sensors
✅ Hardware APIs - torch, brightness, volume, vibration, camera
✅ Media APIs - notification, toast, media player
✅ Communication APIs - SMS, contacts, call log
✅ Other APIs - location, clipboard, storage, share

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 10 - IMPORTANT API COMMANDS                   │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install termux-api          │ Install API package                   │
│ termux-battery-status           │ Check battery info                    │
│ termux-torch on/off             │ Flashlight control                    │
│ termux-brightness 100           │ Set brightness                        │
│ termux-notification             │ Create notification                   │
│ termux-toast "Message"          │ Show toast message                    │
│ termux-sms-send -n NUM "TEXT"   │ Send SMS                              │
│ termux-location                 │ Get GPS location                      │
│ termux-camera-photo photo.jpg   │ Capture photo                         │
│ termux-clipboard-get/set        │ Clipboard operations                  │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter mein hum seekhenge:
- Termux automation with cron jobs
- Background execution
- Boot scripts
- Tasker integration

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 11!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Termux API Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      TERMUX API ARCHITECTURE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │                        Termux Terminal                              │ │
│  │                                                                     │ │
│  │   $ termux-battery-status                                          │ │
│  │   $ termux-torch on                                                │ │
│  │   $ termux-notification --title "Hi" --content "Hello"            │ │
│  │                                                                     │ │
│  └─────────────────────────────┬──────────────────────────────────────┘ │
│                                │                                         │
│                                │ Broadcast Intent                        │
│                                │ (com.termux.api.*)                      │
│                                ▼                                         │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │                     Termux:API Application                          │ │
│  │                                                                     │ │
│  │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐               │ │
│  │   │  Receivers  │  │  Services   │  │  Activities │               │ │
│  │   └──────┬──────┘  └──────┬──────┘  └──────┬──────┘               │ │
│  │          │                │                │                        │ │
│  └──────────┼────────────────┼────────────────┼───────────────────────┘ │
│             │                │                │                          │
│             │                │                │                          │
│             ▼                ▼                ▼                          │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │                       Android System APIs                           │ │
│  │                                                                     │ │
│  │   CameraManager │ SmsManager │ LocationManager │ ConnectivityManager│
│  │   AudioManager  │ Vibrator   │ NotificationManager │ etc.          │ │
│  │                                                                     │ │
│  └────────────────────────────────────────────────────────────────────┘ │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Installation Components

| Component | Source | Purpose |
|-----------|--------|---------|
| Termux App | F-Droid | Terminal emulator |
| Termux:API App | F-Droid | Android system bridge |
| termux-api package | pkg install | CLI commands |

### 3. Permission Mapping

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PERMISSION TO API MAPPING                              │
├────────────────────────┬────────────────────────────────────────────────┤
│ Permission             │ API Commands                                    │
├────────────────────────┼────────────────────────────────────────────────┤
│ android.permission.CAMERA             │ termux-camera-photo             │
│ android.permission.READ_CONTACTS      │ termux-contact-list             │
│ android.permission.READ_SMS           │ termux-sms-list                 │
│ android.permission.SEND_SMS           │ termux-sms-send                 │
│ android.permission.READ_CALL_LOG      │ termux-call-log                 │
│ android.permission.ACCESS_FINE_LOCATION│ termux-location                │
│ android.permission.ACCESS_COARSE_LOCATION│ termux-location, wifi-scan   │
│ android.permission.READ_PHONE_STATE   │ termux-telephony-*              │
│ android.permission.VIBRATE            │ termux-vibrate                  │
│ android.permission.FLASHLIGHT         │ termux-torch                    │
│ android.permission.WRITE_SETTINGS     │ termux-brightness               │
│ android.permission.READ_EXTERNAL_STORAGE│ termux-storage-get            │
│ android.permission.WRITE_EXTERNAL_STORAGE│ termux-share, download       │
└────────────────────────┴────────────────────────────────────────────────┘
```

---

## 📋 COMPLETE API COMMANDS REFERENCE

### Device Information Commands

```bash
# Battery Status
termux-battery-status
# Output: JSON with battery percentage, status, temperature, health

# Telephony Device Info
termux-telephony-deviceinfo
# Output: IMEI, phone type, network info, SIM details

# Telephony Cell Info
termux-telephony-cellinfo
# Output: Cell tower information for location tracking

# Camera Info
termux-camera-info
# Output: List of available cameras with capabilities

# WiFi Connection Info
termux-wifi-connectioninfo
# Output: Current WiFi network details (SSID, BSSID, IP, etc.)

# WiFi Scan Info
termux-wifi-scaninfo
# Output: List of nearby WiFi networks
```

### Hardware Control Commands

```bash
# Torch (Flashlight)
termux-torch on          # Turn on flashlight
termux-torch off         # Turn off flashlight

# Brightness (0-255 range)
termux-brightness 50     # Low brightness
termux-brightness 100    # Medium brightness
termux-brightness 255    # Maximum brightness

# Volume Control
termux-volume call 10        # Call volume
termux-volume music 15       # Music volume (max)
termux-volume notification 5 # Notification volume
termux-volume ring 10        # Ring volume
termux-volume alarm 15       # Alarm volume
termux-volume system 10      # System volume

# Vibration
termux-vibrate              # Default vibration
termux-vibrate -d 1000      # Vibrate for 1 second
termux-vibrate -d 3000      # Vibrate for 3 seconds

# Camera Photo
termux-camera-photo photo.jpg           # Back camera
termux-camera-photo -c 0 photo.jpg      # Back camera (explicit)
termux-camera-photo -c 1 selfie.jpg     # Front camera

# Fingerprint Authentication
termux-fingerprint         # Prompt for fingerprint
# Output: AUTH_RESULT_SUCCESS or AUTH_RESULT_FAILURE

# Infrared (if supported)
termux-infrared-frequencies    # List IR frequencies
```

### Media Commands

```bash
# Notification
termux-notification --title "Title" --content "Message"

# Notification with options
termux-notification \
  --title "Download Complete" \
  --content "File saved successfully" \
  --sound \
  --vibrate 500 \
  --led-color FF0000 \
  --priority high \
  --id "download_001"

# Ongoing notification (persistent)
termux-notification \
  --title "Running" \
  --content "Task in progress" \
  --ongoing \
  --id "task_001"

# Toast Messages
termux-toast "Hello World"              # Default duration
termux-toast -s "Short message"         # Short duration
termux-toast -l "Long message"          # Long duration
termux-toast -g top "Top position"      # Top position
termux-toast -g center "Center"         # Center position
termux-toast -g bottom "Bottom"         # Bottom position

# Media Player
termux-media-player play song.mp3       # Play audio/video
termux-media-player pause               # Pause playback
termux-media-player resume              # Resume playback
termux-media-player stop                # Stop playback
termux-media-player info                # Show current playback info

# Media Scan (Gallery refresh)
termux-media-scan /sdcard/DCIM/photo.jpg
termux-media-scan /sdcard/Download/*.pdf

# Download
termux-download "https://example.com/file.pdf"
termux-download -d /sdcard/Download -t "MyFile" "https://example.com/file.zip"
```

### Communication Commands

```bash
# Contact List
termux-contact-list
# Output: JSON array of contacts with name and number

# Search contacts
termux-contact-list | grep -i "John"

# SMS List
termux-sms-list                          # All messages
termux-sms-list -l 10                    # Last 10 messages
termux-sms-list -t inbox                 # Inbox only
termux-sms-list -t sent                  # Sent messages
termux-sms-list -n "+919876543210"       # From specific number
termux-sms-list -l 20 -t inbox           # Last 20 inbox messages

# SMS Send
termux-sms-send -n "+919876543210" "Hello from Termux"

# SMS from file
cat message.txt | termux-sms-send -n "+919876543210"

# Multiple recipients
termux-sms-send -n "+911111111111" -n "+912222222222" "Broadcast"

# Call Log
termux-call-log                          # All calls
termux-call-log -l 20                    # Last 20 calls
termux-call-log -l 50 -o 10              # 50 calls starting from offset 10

# Filter call log
termux-call-log | grep "missed"
termux-call-log | grep "incoming"
```

### Location & WiFi Commands

```bash
# Location
termux-location                          # Default (GPS if available)
termux-location -p gps                   # GPS provider (accurate)
termux-location -p network               # Network provider (faster)
termux-location -p passive               # Passive provider
termux-location -r once                  # Single request
termux-location -r last                  # Last known location
termux-location -p gps -r once           # GPS single request

# WiFi Enable/Disable
termux-wifi-enable true                  # Turn on WiFi
termux-wifi-enable false                 # Turn off WiFi
```

### Clipboard & Storage Commands

```bash
# Clipboard Get
termux-clipboard-get
# Output: Current clipboard text

# Clipboard Set
termux-clipboard-set "Text to copy"
echo "Copy this" | termux-clipboard-set

# Storage Get (File Picker)
termux-storage-get ~/selected_file.txt
# Opens file picker, saves selected file to specified path

# Share
termux-share file.txt                    # Share file
termux-share -c "image/jpeg" photo.jpg   # Share with MIME type
termux-share -a view photo.jpg           # View action
termux-share -a edit document.txt        # Edit action
echo "Share this text" | termux-share    # Share text
```

### Sensor Commands

```bash
# List available sensors
termux-sensor -l

# Get sensor data
termux-sensor -s "accelerometer"         # Accelerometer data
termux-sensor -s "gyroscope"             # Gyroscope data
termux-sensor -s "light"                 # Light sensor
termux-sensor -s "proximity"             # Proximity sensor

# Sensor with duration
termux-sensor -s "accelerometer" -d 5000 # 5 seconds

# Multiple sensors
termux-sensor -s "accelerometer,gyroscope" -d 10000

# All sensors
termux-sensor -a -d 3000                 # All sensors for 3 seconds
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: API Installation Verification

```bash
# Task: Verify API is properly installed and working

# Step 1: Check if Termux:API app is installed
pkg list-installed | grep termux-api

# Step 2: Test battery status command
termux-battery-status

# Step 3: Test toast command
termux-toast "API is working!"

# Step 4: Test torch
termux-torch on
sleep 2
termux-torch off

# Expected: All commands should work without errors
```

### Exercise 2: Create System Info Script

```bash
# Task: Create a script that displays system information

cat > ~/sysinfo.sh << 'EOF'
#!/bin/bash
# System Information Script

echo "=================================="
echo "     TERMUX SYSTEM INFO"
echo "=================================="
echo ""

# Battery
echo "[BATTERY]"
termux-battery-status | python3 -c "
import sys, json
data = json.load(sys.stdin)
print(f'  Level: {data[\"percentage\"]}%')
print(f'  Status: {data[\"status\"]}')
print(f'  Health: {data[\"health\"]}')
print(f'  Temperature: {data[\"temperature\"]}°C')
"
echo ""

# WiFi
echo "[WIFI]"
termux-wifi-connectioninfo 2>/dev/null | python3 -c "
import sys, json
try:
    data = json.load(sys.stdin)
    print(f'  SSID: {data.get(\"ssid\", \"Not connected\")}')
    print(f'  IP: {data.get(\"ip\", \"N/A\")}')
    print(f'  Signal: {data.get(\"rssi\", \"N/A\")} dBm')
except:
    print('  Not connected to WiFi')
" 2>/dev/null || echo "  WiFi not available"
echo ""

# Telephony
echo "[NETWORK]"
termux-telephony-deviceinfo 2>/dev/null | python3 -c "
import sys, json
try:
    data = json.load(sys.stdin)
    print(f'  Operator: {data.get(\"network_operator_name\", \"N/A\")}')
    print(f'  Network: {data.get(\"network_type\", \"N/A\")}')
except:
    print('  Network info not available')
" 2>/dev/null || echo "  Not available"
echo ""

echo "=================================="
EOF

chmod +x ~/sysinfo.sh
~/sysinfo.sh
```

### Exercise 3: Battery Alert Script

```bash
# Task: Create a battery monitoring script

cat > ~/battery_alert.sh << 'EOF'
#!/bin/bash
# Battery Alert Script

LOW_THRESHOLD=20
HIGH_THRESHOLD=90

# Get battery info
BATTERY_JSON=$(termux-battery-status)
PERCENTAGE=$(echo "$BATTERY_JSON" | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')
STATUS=$(echo "$BATTERY_JSON" | grep -o '"status": "[^"]*"' | cut -d'"' -f4)

echo "Battery: $PERCENTAGE% ($STATUS)"

# Check conditions
if [ "$PERCENTAGE" -le "$LOW_THRESHOLD" ] && [ "$STATUS" != "CHARGING" ]; then
    termux-notification \
        --title "⚠️ Low Battery" \
        --content "Battery is at ${PERCENTAGE}%. Please charge your device." \
        --sound \
        --priority high
    termux-toast "Low Battery: ${PERCENTAGE}%"
fi

if [ "$PERCENTAGE" -ge "$HIGH_THRESHOLD" ] && [ "$STATUS" = "CHARGING" ]; then
    termux-notification \
        --title "🔋 Battery Charged" \
        --content "Battery is at ${PERCENTAGE}%. You can unplug now." \
        --sound
    termux-toast "Battery ${PERCENTAGE}%"
fi
EOF

chmod +x ~/battery_alert.sh
./battery_alert.sh
```

### Exercise 4: WiFi Network Scanner

```bash
# Task: Create WiFi scanner and save results

cat > ~/wifi_scanner.sh << 'EOF'
#!/bin/bash
# WiFi Scanner Script

TIMESTAMP=$(date +%Y%m%d_%H%M%S)
OUTPUT_FILE="~/wifi_scan_$TIMESTAMP.json"

echo "Scanning WiFi networks..."
termux-wifi-scaninfo > "$OUTPUT_FILE"

# Count networks
NETWORK_COUNT=$(cat "$OUTPUT_FILE" | grep -c '"ssid"')
echo "Found $NETWORK_COUNT networks"
echo "Results saved to: $OUTPUT_FILE"

# Show summary
echo ""
echo "Network Summary:"
cat "$OUTPUT_FILE" | python3 -c "
import sys, json
try:
    data = json.load(sys.stdin)
    for i, net in enumerate(data, 1):
        ssid = net.get('ssid', '[Hidden]')
        rssi = net.get('rssi', 'N/A')
        freq = net.get('frequency', 'N/A')
        print(f'  {i}. {ssid} (Signal: {rssi} dBm, Freq: {freq} MHz)')
except Exception as e:
    print(f'Error parsing data: {e}')
"

termux-toast "WiFi scan complete: $NETWORK_COUNT networks"
EOF

chmod +x ~/wifi_scanner.sh
./wifi_scanner.sh
```

### Exercise 5: Location Logger

```bash
# Task: Create GPS location logger

cat > ~/location_logger.sh << 'EOF'
#!/bin/bash
# Location Logger Script

LOG_FILE=~/location_log.txt
TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

echo "Getting GPS location..."
LOCATION=$(termux-location -p gps)

# Extract coordinates
LAT=$(echo "$LOCATION" | grep -o '"latitude": [0-9.-]*' | grep -o '[0-9.-]*')
LON=$(echo "$LOCATION" | grep -o '"longitude": [0-9.-]*' | grep -o '[0-9.-]*')
ACC=$(echo "$LOCATION" | grep -o '"accuracy": [0-9.-]*' | grep -o '[0-9.-]*')

if [ -n "$LAT" ] && [ -n "$LON" ]; then
    echo "$TIMESTAMP | Lat: $LAT | Lon: $LON | Accuracy: ${ACC}m" >> "$LOG_FILE"
    echo "Location logged successfully"
    echo "  Latitude: $LAT"
    echo "  Longitude: $LON"
    echo "  Accuracy: ${ACC}m"
    
    termux-notification \
        --title "Location Logged" \
        --content "Lat: $LAT, Lon: $LON"
else
    echo "Failed to get location. Check GPS permissions."
    termux-toast "Location failed"
fi

echo ""
echo "Recent logs:"
tail -5 "$LOG_FILE"
EOF

chmod +x ~/location_logger.sh
./location_logger.sh
```

### Exercise 6: Notification Center

```bash
# Task: Create a notification management script

cat > ~/notify.sh << 'EOF'
#!/bin/bash
# Notification Helper Script

show_help() {
    echo "Usage: notify.sh [command]"
    echo ""
    echo "Commands:"
    echo "  alert <title> <message>  - High priority notification"
    echo "  info <title> <message>   - Normal notification"
    echo "  toast <message>          - Quick toast message"
    echo "  battery                  - Battery status notification"
    echo "  location                 - Location notification"
    echo "  clear <id>               - Clear notification by ID"
}

case "$1" in
    alert)
        termux-notification \
            --title "$2" \
            --content "$3" \
            --sound \
            --vibrate 500 \
            --priority high \
            --led-color FF0000
        ;;
    info)
        termux-notification \
            --title "$2" \
            --content "$3" \
            --priority default
        ;;
    toast)
        termux-toast "$2"
        ;;
    battery)
        BATTERY=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')
        STATUS=$(termux-battery-status | grep -o '"status": "[^"]*"' | cut -d'"' -f4)
        termux-notification \
            --title "Battery Status" \
            --content "${BATTERY}% - ${STATUS}"
        ;;
    location)
        LOC=$(termux-location -p network -r last)
        LAT=$(echo "$LOC" | grep -o '"latitude": [0-9.-]*' | grep -o '[0-9.-]*')
        LON=$(echo "$LOC" | grep -o '"longitude": [0-9.-]*' | grep -o '[0-9.-]*')
        termux-notification \
            --title "Current Location" \
            --content "Lat: $LAT, Lon: $LON"
        ;;
    clear)
        termux-notification --cancel "$2"
        ;;
    *)
        show_help
        ;;
esac
EOF

chmod +x ~/notify.sh

# Test the script
./notify.sh toast "Notification system ready!"
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Error: Termux:API app not installed"

```bash
# Cause: Termux:API app is not installed or not from correct source

# Diagnosis:
# Check if Termux:API package is installed
pkg list-installed | grep termux-api

# Check if app is installed (requires root or ADB)
pm list packages | grep termux.api

# Solution:
# 1. Install Termux:API app from F-Droid (NOT Play Store)
# 2. Make sure it's the same source as your Termux app
# 3. Both Termux and Termux:API should be from F-Droid

# If both are from F-Droid but still not working:
pkg uninstall termux-api
pkg install termux-api -y
```

### Problem 2: "Permission denied" errors

```bash
# Cause: Required Android permission not granted

# Solution 1: Grant permissions via Settings
# Go to: Settings → Apps → Termux:API → Permissions
# Enable all required permissions

# Solution 2: Check specific permission
# For location:
termux-location
# Watch for permission popup, tap "Allow"

# For SMS:
termux-sms-list
# Watch for permission popup, tap "Allow"

# Solution 3: Reset app permissions
# Settings → Apps → Termux:API → Permissions → Reset
# Then run commands again to re-prompt
```

### Problem 3: Commands hang or return empty

```bash
# Cause: Waiting for user input or GPS lock

# For location commands:
# GPS needs time to get lock
termux-location -p network -r last  # Use network for faster result
termux-location -p gps -r once      # Wait up to 60 seconds for GPS

# For camera commands:
# Ensure no other app is using camera
termux-camera-info  # Check if camera is available

# For WiFi scan:
# Ensure WiFi is enabled
termux-wifi-enable true
sleep 2
termux-wifi-scaninfo
```

### Problem 4: Notification not appearing

```bash
# Cause: Notification permission or Do Not Disturb mode

# Solution 1: Check notification permission
# Settings → Apps → Termux:API → Notifications → Enable

# Solution 2: Check Do Not Disturb
# Pull down notification shade → Disable DND

# Solution 3: Add notification channel importance
termux-notification \
  --title "Test" \
  --content "Testing" \
  --priority high \
  --sound

# Solution 4: Check notification history
# Settings → Notifications → Notification history
```

### Problem 5: SMS commands not working

```bash
# Cause: SMS permissions not granted or Android restrictions

# Solution 1: Grant SMS permission
# Settings → Apps → Termux:API → Permissions → SMS → Allow

# Solution 2: Set as default SMS app (for some features)
# Settings → Apps → Default apps → SMS app
# Note: Termux:API may not work as default SMS app

# Solution 3: Check Android version restrictions
# Android 10+ has stricter SMS permissions
# You may need to grant permission via ADB:
# adb shell pm grant com.termux.api android.permission.READ_SMS
# adb shell pm grant com.termux.api android.permission.SEND_SMS
```

### Problem 6: Location returns null or 0,0

```bash
# Cause: GPS not available or location disabled

# Solution 1: Enable location in Android settings
# Settings → Location → On

# Solution 2: Use network provider instead of GPS
termux-location -p network

# Solution 3: Wait for GPS lock
termux-location -p gps -r once
# Go outside or near window for better GPS signal

# Solution 4: Check location permission accuracy
# Settings → Apps → Termux:API → Permissions → Location
# Select "Allow all the time" for background location
```

### Problem 7: Camera commands fail

```bash
# Cause: Camera in use or permission issue

# Solution 1: Close other camera apps
# Make sure no other app is using camera

# Solution 2: Check camera permission
# Settings → Apps → Termux:API → Permissions → Camera → Allow

# Solution 3: Try different camera ID
termux-camera-info
# Check available camera IDs

termux-camera-photo -c 0 test.jpg  # Back camera
termux-camera-photo -c 1 test.jpg  # Front camera

# Solution 4: Check storage permission
termux-setup-storage
# Photos are saved to current directory
```

### Problem 8: Play Store vs F-Droid Compatibility

```bash
# Cause: Mix of Play Store and F-Droid versions

# Symptoms:
# - "Error: Termux:API app not installed" (but it is installed)
# - Commands return nothing
# - Commands hang forever

# Diagnosis:
echo $TERMUX_VERSION
# Check version - Play Store versions are outdated

# Solution: COMPLETELY REINSTALL both apps
# 1. Uninstall Termux
# 2. Uninstall Termux:API
# 3. Download BOTH from F-Droid
# 4. Install both
# 5. Run: pkg update && pkg upgrade -y
# 6. Run: pkg install termux-api -y
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Feature Showcase**
```
┌────────────────────────────────────┐
│  [Gradient Dark Background]        │
│                                    │
│   🔌 TERMUX API                    │
│   COMPLETE GUIDE                   │
│                                    │
│   📱 Camera  📍 Location           │
│   💬 SMS     🔔 Notifications      │
│   📶 WiFi    💡 Flashlight         │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Command Style**
```
┌────────────────────────────────────┐
│  [Terminal Black Background]       │
│                                    │
│   $ termux-torch on                │
│   $ termux-sms-send                │
│   $ termux-location                │
│                                    │
│   🔥 25+ API COMMANDS!             │
│                                    │
│   Chapter 10 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Action Style**
```
┌────────────────────────────────────┐
│  ⚡ AUTOMATE YOUR PHONE!           │
│                                    │
│   Control Everything from          │
│   Terminal!                        │
│                                    │
│   📷 Camera  📍 GPS  💬 SMS        │
│   🔔 Notify 📶 WiFi 💡 Torch       │
│                                    │
│   Termux API | T3rmuxk1ng          │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔌 Termux Full Course - Chapter 10: Termux API Setup & Complete Overview

🔥 In this video you'll learn:
• Termux API kya hai aur kaise kaam karta hai
• Termux:API app aur package installation
• Android permissions setup
• 25+ API commands with examples
• Device info, hardware control, media APIs
• SMS, contacts, location, WiFi commands
• Practical automation scripts

⏱️ Timestamps:
0:00 - Introduction
0:50 - Termux API Kya Hai
3:00 - API Installation
6:00 - Permissions Setup
8:30 - Device Info APIs
11:00 - Hardware Control APIs
14:00 - Media & Notification APIs
17:00 - Communication APIs
19:30 - Other APIs
21:30 - Practical Examples
24:00 - Summary

📥 Download Links:
• F-Droid: https://f-droid.org
• Termux:API on F-Droid: Search "Termux:API"

📝 Key Commands:
pkg install termux-api
termux-battery-status
termux-torch on/off
termux-notification --title "Hi" --content "Hello"
termux-location
termux-sms-send -n "+91..." "Message"

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxAPI #T3rmuxk1ng #TermuxTutorial #AndroidAutomation #TermuxHindi #TermuxCourse

---
⚠️ Disclaimer: This video is for educational purposes. Use Termux API responsibly and respect privacy laws when accessing SMS, contacts, or location data.
```

### Tags List

```
termux api, termux api setup, termux api commands, termux api tutorial,
termux tutorial, termux course, termux hindi, termux commands,
termux notification, termux sms, termux camera, termux location,
termux wifi, termux torch, termux battery, termux automation,
android automation, android terminal, linux on android,
termux api not working, termux api permissions, t3rmuxk1ng,
termux full course, termux for beginners, ethical hacking tools
```

### Hashtags

```
#Termux #TermuxAPI #TermuxTutorial #TermuxHindi #AndroidAutomation 
#TermuxCommands #LinuxOnAndroid #TermuxCourse #T3rmuxk1ng 
#EthicalHacking #CyberSecurity #AndroidTerminal #TermuxSMS 
#TermuxLocation #Automation
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux:API GitHub | https://github.com/termux/termux-api |
| Termux Wiki - API | https://wiki.termux.com/wiki/Termux:API |
| API Package Info | Run `pkg show termux-api` |

### Command Help

```bash
# Get help for any API command
termux-battery-status --help
termux-notification --help
termux-location --help
# etc.

# View all available API commands
ls $PREFIX/bin/termux-*
```

### Related Packages

```bash
# Additional useful packages for API scripts
pkg install python      # Python for JSON parsing
pkg install jq          # JSON processor
pkg install bc          # Calculator for scripts
pkg install cronie      # For scheduled tasks
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 11, verify:

- [ ] Termux:API app installed from F-Droid
- [ ] termux-api package installed (`pkg install termux-api`)
- [ ] Battery status command works (`termux-battery-status`)
- [ ] Toast command works (`termux-toast "test"`)
- [ ] Torch command works (`termux-torch on/off`)
- [ ] Notification command works
- [ ] All required permissions granted in Settings
- [ ] Created at least one automation script
- [ ] Understood the difference between Termux and Termux:API app

---

## 🎮 INTERACTIVE QUIZ

Test your knowledge! Try to answer these questions before checking the answers at the bottom.

### Quiz Questions

**Q1.** What are the TWO components required for Termux API to work?
```
A) Termux app and root access
B) Termux:API app and termux-api package
C) Termux:Styling and termux-api package
D) Just the termux-api package
```

**Q2.** Which command checks battery status?
```
A) termux-battery
B) termux-battery-status
C) termux-power
D) termux-status battery
```

**Q3.** What command turns on the flashlight?
```
A) termux-flash on
B) termux-torch on
C) termux-light on
D) termux-led on
```

**Q4.** How do you capture a photo with front camera?
```
A) termux-camera-photo -f selfie.jpg
B) termux-camera-photo -c 1 selfie.jpg
C) termux-camera-photo --front selfie.jpg
D) termux-photo selfie.jpg
```

**Q5.** Which permission is required for termux-location?
```
A) Camera
B) Storage
C) Location
D) Phone
```

**Q6.** What does termux-sms-list -l 10 do?
```
A) Lists 10 SMS drafts
B) Lists last 10 SMS messages
C) Deletes 10 SMS messages
D) Sends 10 SMS messages
```

**Q7.** Which command sends a notification?
```
A) termux-notify
B) termux-alert
C) termux-notification
D) termux-message
```

**Q8.** What is the range for termux-brightness?
```
A) 0-100
B) 0-255
C) 1-10
D) 0-1000
```

**Q9.** Which command gets GPS location?
```
A) termux-gps
B) termux-location
C) termux-geo
D) termux-coordinates
```

**Q10.** What does termux-toast do?
```
A) Shows a popup message
B) Makes the phone vibrate
C) Plays a sound
D) Shows a notification
```

**Q11.** Which API requires Camera permission?
```
A) termux-location
B) termux-camera-photo
C) termux-sms-send
D) termux-call-log
```

**Q12.** Where should Termux:API app be installed from?
```
A) Play Store
B) F-Droid
C) GitHub only
D) APKMirror
```

### 📝 Quiz Answers
```
Q1: B) Termux:API app and termux-api package
Q2: B) termux-battery-status
Q3: B) termux-torch on
Q4: B) termux-camera-photo -c 1 selfie.jpg
Q5: C) Location
Q6: B) Lists last 10 SMS messages
Q7: C) termux-notification
Q8: B) 0-255
Q9: B) termux-location
Q10: A) Shows a popup message
Q11: B) termux-camera-photo
Q12: B) F-Droid
```


## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

<details>
<summary><b>Q1. What two components are required for Termux API to work?</b></summary>

**Answer:** 
1. **Termux:API App** - The Android application (installed from F-Droid)
2. **termux-api package** - The CLI package installed via `pkg install termux-api`

Both must be installed from the same source (F-Droid) for compatibility.
</details>

<details>
<summary><b>Q2. Which command checks battery status?</b></summary>

**Answer:** `termux-battery-status` returns JSON with:
- percentage: Battery level (0-100)
- status: CHARGING, DISCHARGING, FULL, NOT_CHARGING
- health: GOOD, OVERHEAT, DEAD, etc.
- temperature: Temperature in Celsius
</details>

<details>
<summary><b>Q3. How do you turn on the flashlight?</b></summary>

**Answer:** 
```bash
termux-torch on    # Turn on
termux-torch off   # Turn off
```
Requires flashlight permission for Termux:API app in Android settings.
</details>

<details>
<summary><b>Q4. What command captures a photo from camera?</b></summary>

**Answer:** 
```bash
termux-camera-photo photo.jpg        # Back camera (default)
termux-camera-photo -c 0 photo.jpg   # Back camera (explicit)
termux-camera-photo -c 1 selfie.jpg  # Front camera
```
Requires Camera permission granted to Termux:API app.
</details>

<details>
<summary><b>Q5. Which permission is needed for termux-location?</b></summary>

**Answer:** **Location permission** - Both "Allow all the time" or "Allow only while using" work. The first time you run `termux-location`, Android will prompt for permission.

```bash
termux-location -p gps      # GPS (most accurate)
termux-location -p network  # Network-based (faster)
```
</details>

<details>
<summary><b>Q6. How do you send an SMS from Termux?</b></summary>

**Answer:** 
```bash
termux-sms-send -n "+919876543210" "Hello from Termux!"

# From file:
cat message.txt | termux-sms-send -n "+919876543210"

# Multiple recipients:
termux-sms-send -n "+91XXXXXXXXXX" -n "+91YYYYYYYYYY" "Broadcast message"
```
Requires SMS permission in Android settings.
</details>

<details>
<summary><b>Q7. What does termux-notification do?</b></summary>

**Answer:** Creates Android notifications with customizable options:
```bash
termux-notification \
  --title "Download Complete" \
  --content "File saved successfully" \
  --sound \
  --vibrate 500 \
  --led-color FF0000 \
  --priority high
```
Useful for script alerts, completion notifications, and automation feedback.
</details>

<details>
<summary><b>Q8. What is the brightness value range?</b></summary>

**Answer:** **0-255** (0 = minimum, 255 = maximum)
```bash
termux-brightness 50   # Low brightness
termux-brightness 100  # Medium
termux-brightness 255  # Maximum
```
Requires WRITE_SETTINGS permission or works on some devices without it.
</details>

<details>
<summary><b>Q9. How do you get WiFi information?</b></summary>

**Answer:** 
```bash
termux-wifi-connectioninfo   # Current connection (SSID, IP, MAC, signal)
termux-wifi-scaninfo         # Scan nearby networks
termux-wifi-enable true      # Turn on WiFi
termux-wifi-enable false     # Turn off WiFi
```
Requires Location permission for WiFi scanning on Android 8.1+.
</details>

<details>
<summary><b>Q10. How do you create a toast message?</b></summary>

**Answer:** 
```bash
termux-toast "Hello World!"           # Default duration
termux-toast -s "Short message"       # Short duration
termux-toast -l "Long message"        # Long duration
termux-toast -g center "Centered!"    # Position: top, center, bottom
```
Toast messages are quick popup notifications that disappear automatically.
</details>

<details>
<summary><b>Q11. Which command lists contacts?</b></summary>

**Answer:** 
```bash
termux-contact-list

# Output format (JSON):
# [{"name": "John Doe", "number": "+919876543210"}, ...]

# Search for specific contact:
termux-contact-list | grep -i "John"
```
Requires Contacts permission granted to Termux:API app.
</details>

<details>
<summary><b>Q12. Where should Termux:API app be installed from?</b></summary>

**Answer:** **F-Droid** - This is critical because:
- F-Droid Termux app requires F-Droid Termux:API
- Play Store versions are incompatible with F-Droid versions
- Using mismatched sources causes "API not installed" errors

Always match your Termux and add-on app sources!
</details>

<details>
<summary><b>Q13. How do you vibrate the phone?</b></summary>

**Answer:** 
```bash
termux-vibrate              # Default vibration
termux-vibrate -d 1000      # Vibrate for 1 second (1000ms)
termux-vibrate -d 3000      # Vibrate for 3 seconds
```
Works without special permissions - VIBRATE permission is normal permission.
</details>

<details>
<summary><b>Q14. What command accesses the clipboard?</b></summary>

**Answer:** 
```bash
# Get clipboard content:
termux-clipboard-get

# Set clipboard content:
termux-clipboard-set "Text to copy"

# From command output:
echo "$(date)" | termux-clipboard-set
```
Great for automation scripts that need to interact with other apps.
</details>

<details>
<summary><b>Q15. How do you control volume levels?</b></summary>

**Answer:** 
```bash
termux-volume <stream> <value>

# Streams: call, notification, alarm, music, ring, system
# Value: 0-15 (varies by device)

termux-volume music 10      # Music volume
termux-volume ring 0        # Silent ring
termux-volume alarm 15      # Maximum alarm
termux-volume notification 5
```
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Q1: What is the architecture of Termux:API and how does it work?

**Answer:**
Termux:API uses a client-server architecture:

1. **Termux Terminal** - Runs CLI commands like `termux-battery-status`
2. **Broadcast Intent** - Commands are sent as Android broadcast intents
3. **Termux:API App** - Android application that receives intents
4. **Android System APIs** - The app accesses native Android features

**Flow:**
```
Command → Intent → Termux:API App → Android API → Response → Terminal
```

This separation allows the terminal to access restricted Android features without root, using the Termux:API app as a privileged bridge.

### Q2: Why must Termux:API app be installed from F-Droid?

**Answer:**
**Compatibility reasons:**
1. **Package signing** - Both apps must be signed by the same certificate
2. **Version matching** - F-Droid Termux and F-Droid Termux:API are built together
3. **Shared UID** - They communicate through a shared user ID

**Play Store issues:**
- Play Store Termux is outdated and incompatible
- Different signing certificates break communication
- Google Play restrictions limit functionality

**Best practice:** Install ALL Termux ecosystem apps from F-Droid: Termux, Termux:API, Termux:Styling, Termux:Float, etc.

### Q3: How would you create an automation script using Termux:API?

**Answer:**
Example automation script:

```bash
#!/bin/bash
# smart_battery_alert.sh

while true; do
    battery=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')
    status=$(termux-battery-status | grep -o '"status": "[^"]*"' | cut -d'"' -f4)
    
    if [ "$battery" -le 20 ] && [ "$status" = "DISCHARGING" ]; then
        termux-notification \
            --title "⚠️ Low Battery" \
            --content "Battery at ${battery}% - Connect charger!" \
            --sound \
            --priority high \
            --vibrate 500,200,500
    fi
    
    sleep 300  # Check every 5 minutes
done
```

This script demonstrates:
- JSON parsing
- Conditional logic
- User notification
- Background execution

### Q4: What security considerations should be made when using Termux:API?

**Answer:**
**Security considerations:**

1. **Permission Management:**
   - Grant only necessary permissions
   - Review permissions regularly
   - Be cautious with SMS/Contacts/Location access

2. **Script Security:**
   - Don't hardcode sensitive data
   - Use environment variables for secrets
   - Validate all inputs

3. **API Key Protection:**
   ```bash
   # Store keys in protected files
   chmod 600 ~/.api_keys
   source ~/.api_keys
   ```

4. **Ethical Use:**
   - Never send spam SMS
   - Respect privacy with contacts/messages
   - Use location responsibly

5. **App Security:**
   - Keep Termux and add-ons updated
   - Don't install from unknown sources
   - Review running processes

### Q5: How would you implement a location tracking system?

**Answer:**
Complete implementation:

```bash
#!/bin/bash
# location_tracker.sh

LOG_FILE="$HOME/location_log.csv"
INTERVAL=60  # seconds

# Create log file with header
[ ! -f "$LOG_FILE" ] && echo "timestamp,latitude,longitude,accuracy,provider" > "$LOG_FILE"

while true; do
    # Get location with timeout
    location=$(timeout 30 termux-location -p network 2>/dev/null)
    
    if [ $? -eq 0 ]; then
        # Parse JSON
        lat=$(echo "$location" | grep -o '"latitude": [0-9.]*' | grep -o '[0-9.]*')
        lon=$(echo "$location" | grep -o '"longitude": [0-9.]*' | grep -o '[0-9.]*')
        acc=$(echo "$location" | grep -o '"accuracy": [0-9.]*' | grep -o '[0-9.]*')
        prov=$(echo "$location" | grep -o '"provider": "[^"]*"' | cut -d'"' -f4)
        ts=$(date -Iseconds)
        
        # Log to CSV
        echo "$ts,$lat,$lon,$acc,$prov" >> "$LOG_FILE"
        
        # Optional: Send to server
        # curl -X POST -d "lat=$lat&lon=$lon" https://api.example.com/location
    fi
    
    sleep "$INTERVAL"
done
```

### Q6: Explain how you would set up SMS automation for alerts.

**Answer:**
SMS automation setup:

```bash
#!/bin/bash
# sms_alert_system.sh

# Configuration
RECIPIENTS=("+91XXXXXXXXXX" "+91YYYYYYYYYY")
ALERT_FILE="/tmp/alerts.txt"

send_alert() {
    local message="$1"
    local priority="$2"
    
    for number in "${RECIPIENTS[@]}"; do
        termux-sms-send -n "$number" "$message"
        
        # Log the alert
        echo "$(date): Sent to $number - $message" >> "$ALERT_FILE"
    done
    
    # Also show notification
    termux-notification \
        --title "Alert Sent" \
        --content "$message" \
        --priority "$priority"
}

# Usage examples:
# send_alert "Server down!" "high"
# send_alert "Backup completed" "default"

# CRITICAL: Always get consent before sending automated SMS!
```

### Q7: How do you handle API command failures gracefully?

**Answer:**
Error handling pattern:

```bash
#!/bin/bash
# robust_api_script.sh

# Function to safely execute API commands
safe_api_call() {
    local cmd="$1"
    local max_retries=3
    local retry_delay=5
    
    for ((i=1; i<=max_retries; i++)); do
        result=$($cmd 2>&1)
        exit_code=$?
        
        if [ $exit_code -eq 0 ]; then
            echo "$result"
            return 0
        fi
        
        # Check for specific errors
        if echo "$result" | grep -q "not installed"; then
            echo "ERROR: Termux:API app not installed" >&2
            return 1
        fi
        
        if echo "$result" | grep -q "permission"; then
            echo "ERROR: Permission denied. Grant in Android Settings" >&2
            return 1
        fi
        
        # Retry for transient errors
        echo "Attempt $i failed, retrying in ${retry_delay}s..." >&2
        sleep "$retry_delay"
    done
    
    echo "ERROR: Command failed after $max_retries attempts" >&2
    return 1
}

# Usage:
battery=$(safe_api_call "termux-battery-status")
if [ $? -eq 0 ]; then
    echo "Battery: $(echo "$battery" | grep -o '"percentage": [0-9]*')"
else
    echo "Failed to get battery status"
fi
```

### Q8: What are the limitations of Termux:API on different Android versions?

**Answer:**
**Version-specific limitations:**

| Android Version | Limitations |
|-----------------|-------------|
| 6.0-7.1 | Generally good API access |
| 8.0-8.1 | Background limits, need Location for WiFi |
| 9.0 | Restricted background access, microphone limits |
| 10+ | Scoped storage, WiFi toggle requires special permission |
| 11+ | More aggressive background restrictions |
| 12+ | Even stricter foreground service requirements |

**Workarounds:**
- Use `termux-wake-lock` for long operations
- Request "Allow all the time" for Location
- Use WorkManager via Termux:Tasker for reliability
- Consider root access for full functionality

### Q9: How would you integrate Termux:API with Tasker?

**Answer:**
Termux:Tasker integration:

1. **Install Termux:Tasker** from F-Droid
2. **Enable Tasker plugin** in Termux settings

**Tasker → Termux flow:**
```
Tasker Event → Plugin → Termux:Tasker → Run Script
```

**Termux → Tasker flow:**
```bash
# In Termux script
termux-notification \
    --title "Tasker Trigger" \
    --action "tasker://runtask?taskname=MyTask"
```

**Example automation:**
```bash
#!/bin/bash
# termux_tasker_bridge.sh

battery=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')

if [ "$battery" -lt 20 ]; then
    # Trigger Tasker task
    termux-notification \
        --title "LowBattery" \
        --content "$battery" \
        --action "tasker://runtask?taskname=PowerSaving"
fi
```

### Q10: How would you implement a complete device monitoring system?

**Answer:**
Complete monitoring system:

```bash
#!/bin/bash
# device_monitor.sh

MONITOR_DIR="$HOME/monitoring"
mkdir -p "$MONITOR_DIR"

collect_metrics() {
    local ts=$(date -Iseconds)
    local log_file="$MONITOR_DIR/metrics_$(date +%Y%m%d).csv"
    
    # Battery
    local battery_json=$(termux-battery-status)
    local battery_pct=$(echo "$battery_json" | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')
    local battery_temp=$(echo "$battery_json" | grep -o '"temperature": [0-9.]*' | grep -o '[0-9.]*')
    
    # WiFi
    local wifi_ssid="N/A"
    local wifi_signal="N/A"
    if wifi_json=$(termux-wifi-connectioninfo 2>/dev/null); then
        wifi_ssid=$(echo "$wifi_json" | grep -o '"ssid": "[^"]*"' | cut -d'"' -f4)
        wifi_signal=$(echo "$wifi_json" | grep -o '"rssi": -[0-9]*' | grep -o '\-[0-9]*')
    fi
    
    # Location (if available)
    local location="N/A"
    if loc_json=$(timeout 10 termux-location -p network 2>/dev/null); then
        local lat=$(echo "$loc_json" | grep -o '"latitude": [0-9.]*' | grep -o '[0-9.]*')
        local lon=$(echo "$loc_json" | grep -o '"longitude": [0-9.]*' | grep -o '[0-9.]*')
        location="$lat,$lon"
    fi
    
    # Log to CSV
    echo "$ts,$battery_pct,$battery_temp,$wifi_ssid,$wifi_signal,$location" >> "$log_file"
    
    # Check thresholds
    [ "$battery_pct" -lt 20 ] && termux-notification --title "Low Battery" --content "${battery_pct}%"
}

# Main loop
while true; do
    collect_metrics
    sleep 300  # Every 5 minutes
done
```

---

## 🔥 REAL-WORLD SCENARIOS

```
┌───────────────────────────────────────────────────────────────────────────┐
│                    SCENARIO 1: SERVER MONITORING AGENT                    │
├───────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  SITUATION: You're running a home server and want to receive SMS        │
│  alerts when critical events occur                                       │
│                                                                           │
│  SOLUTION:                                                                │
│  ```bash                                                                 │
│  #!/bin/bash                                                             │
│  # server_monitor.sh                                                     │
│                                                                           │
│  SERVER_IP="192.168.1.100"                                               │
│  ADMIN_SMS="+919876543210"                                               │
│                                                                           │
│  while true; do                                                          │
│      if ! ping -c 1 -W 5 "$SERVER_IP" > /dev/null 2>&1; then             │
│          termux-sms-send -n "$ADMIN_SMS" "ALERT: Server unreachable!"    │
│          termux-notification --title "Server Down" --priority max        │
│      fi                                                                  │
│      sleep 60                                                            │
│  done                                                                    │
│  ```                                                                     │
│                                                                           │
│  RUN: Use `nohup ./server_monitor.sh &` for background execution         │
│                                                                           │
└───────────────────────────────────────────────────────────────────────────┘
```

```
┌───────────────────────────────────────────────────────────────────────────┐
│                   SCENARIO 2: AUTOMATED BACKUP SYSTEM                     │
├───────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  SITUATION: Automatically backup important files and receive            │
│  notifications when backup completes or fails                            │
│                                                                           │
│  SOLUTION:                                                                │
│  ```bash                                                                 │
│  #!/bin/bash                                                             │
│  # auto_backup.sh                                                        │
│                                                                           │
│  SOURCE="/sdcard/Documents"                                              │
│  DEST="/sdcard/Backup/$(date +%Y%m%d)"                                   │
│                                                                           │
│  mkdir -p "$DEST"                                                        │
│                                                                           │
│  if cp -r "$SOURCE"/* "$DEST/" 2>/dev/null; then                         │
│      termux-notification \                                               │
│          --title "Backup Complete" \                                     │
│          --content "Files saved to $DEST" \                              │
│          --sound                                                         │
│      termux-toast "Backup successful!"                                   │
│  else                                                                    │
│      termux-notification \                                               │
│          --title "Backup Failed" \                                       │
│          --content "Check storage permissions" \                         │
│          --priority high \                                               │
│          --sound                                                         │
│  fi                                                                      │
│  ```                                                                     │
│                                                                           │
│  SCHEDULE: Run via cron at specific times                                 │
│                                                                           │
└───────────────────────────────────────────────────────────────────────────┘
```

```
┌───────────────────────────────────────────────────────────────────────────┐
│                  SCENARIO 3: SECURITY CAMERA INTEGRATION                  │
├───────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  SITUATION: Capture photos automatically when motion is detected        │
│  or at scheduled intervals for security monitoring                       │
│                                                                           │
│  SOLUTION:                                                                │
│  ```bash                                                                 │
│  #!/bin/bash                                                             │
│  # security_camera.sh                                                    │
│                                                                           │
│  PHOTO_DIR="/sdcard/SecurityCam"                                         │
│  mkdir -p "$PHOTO_DIR"                                                   │
│                                                                           │
│  while true; do                                                          │
│      TIMESTAMP=$(date +%Y%m%d_%H%M%S)                                    │
│      PHOTO="$PHOTO_DIR/photo_$TIMESTAMP.jpg"                             │
│                                                                           │
│      # Capture photo from back camera                                    │
│      termux-camera-photo -c 0 "$PHOTO"                                   │
│                                                                           │
│      # Log capture                                                       │
│      echo "$(date): Photo captured - $PHOTO" >> security.log            │
│                                                                           │
│      # Optional: Upload to cloud                                         │
│      # rclone copy "$PHOTO" gdrive:security/                             │
│                                                                           │
│      sleep 300  # Every 5 minutes                                        │
│  done                                                                    │
│  ```                                                                     │
│                                                                           │
│  TIP: Combine with motion detection using Termux sensors                 │
│                                                                           │
└───────────────────────────────────────────────────────────────────────────┘
```

```
┌───────────────────────────────────────────────────────────────────────────┐
│                    SCENARIO 4: LOCATION TRACKER                           │
├───────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  SITUATION: Track device location for family safety or fleet           │
│  management, logging coordinates periodically                            │
│                                                                           │
│  SOLUTION:                                                                │
│  ```bash                                                                 │
│  #!/bin/bash                                                             │
│  # location_tracker.sh                                                   │
│                                                                           │
│  LOG_FILE="$HOME/location_history.csv"                                   │
│  echo "timestamp,latitude,longitude,accuracy" > "$LOG_FILE"              │
│                                                                           │
│  while true; do                                                          │
│      LOCATION=$(termux-location -p network 2>/dev/null)                  │
│                                                                           │
│      if [ $? -eq 0 ]; then                                               │
│          LAT=$(echo "$LOCATION" | grep -o '"latitude": [0-9.]*' | \      │
│                grep -o '[0-9.]*')                                        │
│          LON=$(echo "$LOCATION" | grep -o '"longitude": [0-9.]*' | \     │
│                grep -o '[0-9.]*')                                        │
│          ACC=$(echo "$LOCATION" | grep -o '"accuracy": [0-9.]*' | \      │
│                grep -o '[0-9.]*')                                        │
│                                                                           │
│          echo "$(date -Iseconds),$LAT,$LON,$ACC" >> "$LOG_FILE"          │
│      fi                                                                  │
│                                                                           │
│      sleep 600  # Every 10 minutes                                       │
│  done                                                                    │
│  ```                                                                     │
│                                                                           │
│  PRIVACY: Always get consent before tracking anyone's location            │
│                                                                           │
└───────────────────────────────────────────────────────────────────────────┘
```

```
┌───────────────────────────────────────────────────────────────────────────┐
│                   SCENARIO 5: SMART HOME CONTROLLER                       │
├───────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  SITUATION: Control device functions and integrate with smart home     │
│  systems using Termux API commands                                       │
│                                                                           │
│  SOLUTION:                                                                │
│  ```bash                                                                 │
│  #!/bin/bash                                                             │
│  # smart_home.sh                                                         │
│                                                                           │
│  # Morning routine                                                       │
│  morning_routine() {                                                     │
│      termux-brightness 200        # Bright screen                        │
│      termux-volume music 10       # Set music volume                     │
│      termux-notification --title "Good Morning!" \                       │
│          --content "Have a great day!"                                   │
│      termux-toast "Morning routine activated"                            │
│  }                                                                       │
│                                                                           │
│  # Night routine                                                         │
│  night_routine() {                                                       │
│      termux-brightness 50         # Dim screen                           │
│      termux-volume ring 0         # Silent ring                          │
│      termux-volume notification 0 # Silent notifications                 │
│      termux-notification --title "Good Night" \                          │
│          --content "Sleep well!"                                         │
│  }                                                                       │
│                                                                           │
│  # Auto-trigger based on time                                            │
│  hour=$(date +%H)                                                        │
│  if [ "$hour" -eq 7 ]; then morning_routine; fi                          │
│  if [ "$hour" -eq 22 ]; then night_routine; fi                           │
│  ```                                                                     │
│                                                                           │
│  EXTEND: Add Tasker integration for more complex automations              │
│                                                                           │
└───────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Termux:API Communication Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX:API COMMUNICATION FLOW                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     USER LAYER                                   │   │
│   │                                                                  │   │
│   │   $ termux-battery-status                                       │   │
│   │   $ termux-torch on                                             │   │
│   │   $ termux-notification --title "Hi"                            │   │
│   │                                                                  │   │
│   └────────────────────────────┬────────────────────────────────────┘   │
│                                │                                         │
│                                ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                  TERMUX TERMINAL (CLI)                           │   │
│   │                                                                  │   │
│   │   ┌───────────────────────────────────────────────────────────┐ │   │
│   │   │  termux-api package                                      │ │   │
│   │   │  - termux-battery-status                                 │ │   │
│   │   │  - termux-torch                                          │ │   │
│   │   │  - termux-notification                                   │ │   │
│   │   │  - termux-camera-photo                                   │ │   │
│   │   │  - ... (40+ commands)                                    │ │   │
│   │   └───────────────────────────────────────────────────────────┘ │   │
│   │                            │                                     │   │
│   │                            │ Broadcast Intent                    │   │
│   │                            │ com.termux.api.*                     │   │
│   └────────────────────────────┼────────────────────────────────────┘   │
│                                │                                         │
│                                ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                  TERMUX:API APPLICATION                          │   │
│   │                                                                  │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │   │
│   │   │  Receivers  │  │  Services   │  │  Activities │             │   │
│   │   └──────┬──────┘  └──────┬──────┘  └──────┬──────┘             │   │
│   │          │                │                │                      │   │
│   │          └────────────────┼────────────────┘                      │   │
│   │                           │                                        │   │
│   └───────────────────────────┼───────────────────────────────────────┘   │
│                               │                                          │
│                               ▼                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    ANDROID SYSTEM APIs                           │   │
│   │                                                                  │   │
│   │   ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │   │
│   │   │CameraManager│ │  SmsManager │ │LocationMgr  │               │   │
│   │   └─────────────┘ └─────────────┘ └─────────────┘               │   │
│   │   ┌─────────────┐ ┌─────────────┐ ┌─────────────┐               │   │
│   │   │ AudioManager│ │ Vibrator    │ │Notification │               │   │
│   │   └─────────────┘ └─────────────┘ └─────────────┘               │   │
│   │                                                                  │   │
│   └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### API Permission Mapping

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    API COMMAND → PERMISSION MAPPING                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                 DEVICE INFO APIs                               │    │
│   ├────────────────────────────────────────────────────────────────┤    │
│   │ termux-battery-status    → No special permission               │    │
│   │ termux-telephony-*       → READ_PHONE_STATE                    │    │
│   │ termux-wifi-*            → LOCATION / NEARBY_DEVICES            │    │
│   │ termux-sensor            → No special permission               │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                 HARDWARE CONTROL APIs                          │    │
│   ├────────────────────────────────────────────────────────────────┤    │
│   │ termux-torch             → FLASHLIGHT / CAMERA                 │    │
│   │ termux-brightness        → WRITE_SETTINGS                       │    │
│   │ termux-volume            → No special permission               │    │
│   │ termux-vibrate           → VIBRATE                              │    │
│   │ termux-camera-*          → CAMERA                               │    │
│   │ termux-fingerprint       → USE_BIOMETRIC                        │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                 COMMUNICATION APIs                             │    │
│   ├────────────────────────────────────────────────────────────────┤    │
│   │ termux-sms-*             → READ_SMS, SEND_SMS                   │    │
│   │ termux-call-log          → READ_CALL_LOG                        │    │
│   │ termux-contact-list      → READ_CONTACTS                        │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                 LOCATION & STORAGE APIs                        │    │
│   ├────────────────────────────────────────────────────────────────┤    │
│   │ termux-location          → ACCESS_FINE_LOCATION                 │    │
│   │ termux-storage-get       → READ_EXTERNAL_STORAGE                │    │
│   │ termux-share            → No special permission               │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### API Script Integration Pattern

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    API SCRIPT INTEGRATION PATTERN                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                    TRIGGER LAYER                                  │  │
│   │                                                                   │  │
│   │   ┌────────────┐  ┌────────────┐  ┌────────────┐                │  │
│   │   │   Cron     │  │  Tasker    │  │   Manual   │                │  │
│   │   │  Schedule  │  │  Events    │  │  Execution │                │  │
│   │   └─────┬──────┘  └─────┬──────┘  └─────┬──────┘                │  │
│   │         │               │               │                         │  │
│   └─────────┼───────────────┼───────────────┼─────────────────────────┘  │
│             │               │               │                             │
│             └───────────────┼───────────────┘                             │
│                             ▼                                             │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                    SCRIPT LAYER                                   │  │
│   │                                                                   │  │
│   │   #!/bin/bash                                                     │  │
│   │   1. Check conditions (battery, time, location)                   │  │
│   │   2. Execute API commands                                         │  │
│   │   3. Process results (parse JSON, make decisions)                 │  │
│   │   4. Take action (notify, log, trigger next)                      │  │
│   │                                                                   │  │
│   └──────────────────────────────────────────────────────────────────┘  │
│                             │                                             │
│                             ▼                                             │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                    API EXECUTION LAYER                            │  │
│   │                                                                   │  │
│   │   termux-battery-status  →  termux-notification                  │  │
│   │   termux-location         →  termux-sms-send                     │  │
│   │   termux-wifi-scaninfo    →  termux-toast                        │  │
│   │   termux-camera-photo     →  termux-vibrate                      │  │
│   │                                                                   │  │
│   └──────────────────────────────────────────────────────────────────┘  │
│                             │                                             │
│                             ▼                                             │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                    OUTPUT LAYER                                   │  │
│   │                                                                   │  │
│   │   ┌────────────┐  ┌────────────┐  ┌────────────┐                │  │
│   │   │  Log File  │  │ Notification│  │   SMS/    │                │  │
│   │   │  Records   │  │   Alerts    │  │   Alerts  │                │  │
│   │   └────────────┘  └────────────┘  └────────────┘                │  │
│   │                                                                   │  │
│   └──────────────────────────────────────────────────────────────────┘  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Relationship | Chapter | Description |
|--------------|---------|-------------|
| **Prerequisites** | Ch 1: Termux Installation | Install Termux before API |
| **Prerequisites** | Ch 2: Initial Setup | Basic configuration |
| **Prerequisites** | Ch 8: Text Editors | Write scripts using Nano/Vim |
| **Prerequisites** | Ch 9: Termux Styling | Customize appearance |
| **Current** | Ch 10: Termux:API Setup | **You are here** |
| **Next** | Ch 11: Shell Customization | Advanced shell configuration |
| **Related** | Ch 15: Shell Scripting | Write automation scripts |
| **Related** | Ch 20: Cron Jobs | Schedule automated tasks |
| **Related** | Ch 25: Git Version Control | API for git hooks |
| **Advanced** | Ch 30: Tasker Integration | Advanced automation |
| **Advanced** | Ch 45: IoT Integration | Control IoT devices via API |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: JSON Response Parsing Library

Create a reusable parsing library for Termux:API responses:

```bash
# ~/.termux/api_utils.sh - API parsing utilities

# Parse battery status
get_battery_percentage() {
    termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*'
}

get_battery_status() {
    termux-battery-status | grep -o '"status": "[^"]*"' | cut -d'"' -f4
}

get_battery_temperature() {
    termux-battery-status | grep -o '"temperature": [0-9.]*' | grep -o '[0-9.]*'
}

# Parse location
get_location_lat() {
    termux-location "$@" | grep -o '"latitude": [0-9.]*' | grep -o '[0-9.]*'
}

get_location_lon() {
    termux-location "$@" | grep -o '"longitude": [0-9.]*' | grep -o '[0-9.]*'
}

# Parse WiFi info
get_wifi_ssid() {
    termux-wifi-connectioninfo | grep -o '"ssid": "[^"]*"' | cut -d'"' -f4
}

get_wifi_ip() {
    termux-wifi-connectioninfo | grep -o '"ip": "[^"]*"' | cut -d'"' -f4
}

# Usage example:
# source ~/.termux/api_utils.sh
# battery=$(get_battery_percentage)
# ssid=$(get_wifi_ssid)
```

### Advanced Technique 2: Event-Driven API Automation

Create a system that responds to device events:

```bash
#!/bin/bash
# event_responder.sh - React to device state changes

# State tracking directory
STATE_DIR="$HOME/.device_state"
mkdir -p "$STATE_DIR"

# Check and react to battery changes
check_battery() {
    local current=$(get_battery_percentage)
    local previous=$(cat "$STATE_DIR/battery" 2>/dev/null || echo "100")
    
    # State changed?
    if [ "$current" != "$previous" ]; then
        # React to low battery
        if [ "$current" -le 20 ] && [ "$previous" -gt 20 ]; then
            termux-notification --title "Low Battery" --content "${current}%"
            termux-volume ring 0  # Silent ring
        fi
        
        # React to charging
        local status=$(get_battery_status)
        if [ "$status" = "CHARGING" ] && [ "$previous_status" != "CHARGING" ]; then
            termux-toast "Charging started"
        fi
        
        # Save new state
        echo "$current" > "$STATE_DIR/battery"
        echo "$status" > "$STATE_DIR/battery_status"
    fi
}

# Check and react to WiFi changes
check_wifi() {
    local current_ssid=$(get_wifi_ssid 2>/dev/null || echo "disconnected")
    local previous_ssid=$(cat "$STATE_DIR/wifi_ssid" 2>/dev/null || echo "disconnected")
    
    if [ "$current_ssid" != "$previous_ssid" ]; then
        if [ "$current_ssid" = "disconnected" ]; then
            termux-notification --title "WiFi Lost" --content "Disconnected"
        else
            termux-notification --title "WiFi Connected" --content "$current_ssid"
        fi
        echo "$current_ssid" > "$STATE_DIR/wifi_ssid"
    fi
}

# Main monitoring loop
while true; do
    check_battery
    check_wifi
    sleep 30
done
```

### Advanced Technique 3: API Command Scheduler

Create a flexible scheduling system for API commands:

```bash
#!/bin/bash
# api_scheduler.sh - Schedule Termux:API commands

SCHEDULE_FILE="$HOME/.api_schedule"
LOG_FILE="$HOME/.api_schedule.log"

# Schedule format: HH:MM:command:args
# Example: 08:00:termux-notification:--title Morning --content "Time to wake up"

add_schedule() {
    local time="$1"
    local cmd="$2"
    local args="$3"
    echo "$time:$cmd:$args" >> "$SCHEDULE_FILE"
    echo "Scheduled: $time - $cmd $args"
}

run_scheduler() {
    while true; do
        local current_time=$(date +%H:%M)
        
        while IFS=: read -r time cmd args; do
            if [ "$time" = "$current_time" ]; then
                echo "$(date): Running $cmd $args" >> "$LOG_FILE"
                $cmd $args
            fi
        done < "$SCHEDULE_FILE"
        
        sleep 60
    done
}

# Usage examples:
# ./api_scheduler.sh add 08:00 termux-notification "--title Morning --content Wake\ up"
# ./api_scheduler.sh add 22:00 termux-brightness "50"
# ./api_scheduler.sh add 22:00 termux-volume "ring 0"

case "$1" in
    add) add_schedule "$2" "$3" "$4" ;;
    run) run_scheduler ;;
    *) echo "Usage: $0 {add|run} [time] [command] [args]" ;;
esac
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

After completing this chapter, you should be able to:

- [ ] Install Termux:API app from F-Droid
- [ ] Install termux-api package with `pkg install termux-api`
- [ ] Grant necessary permissions to Termux:API app
- [ ] Check battery status with `termux-battery-status`
- [ ] Control flashlight with `termux-torch`
- [ ] Adjust brightness with `termux-brightness`
- [ ] Control volume levels with `termux-volume`
- [ ] Vibrate device with `termux-vibrate`
- [ ] Capture photos with `termux-camera-photo`
- [ ] Use fingerprint authentication with `termux-fingerprint`
- [ ] Create notifications with `termux-notification`
- [ ] Show toast messages with `termux-toast`
- [ ] Control media playback with `termux-media-player`
- [ ] List contacts with `termux-contact-list`
- [ ] Send SMS with `termux-sms-send`
- [ ] List SMS with `termux-sms-list`
- [ ] View call log with `termux-call-log`
- [ ] Get location with `termux-location`
- [ ] Scan WiFi networks with `termux-wifi-scaninfo`
- [ ] Use clipboard with `termux-clipboard-get/set`
- [ ] Share content with `termux-share`
- [ ] Pick files with `termux-storage-get`
- [ ] Write automation scripts using API commands
- [ ] Troubleshoot API permission issues

---

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1: JSON Parsing Made Easy**
>
> Use Python to parse API JSON output:
> ```bash
> termux-battery-status | python3 -c "import sys,json; print(json.load(sys.stdin)['percentage'])"
> ```

> 💡 **Pro Tip #2: Quick Test Script**
>
> Create a quick API test function:
> ```bash
> test_api() {
>     termux-toast "Testing API..."
>     termux-vibrate -d 100
>     termux-battery-status > /dev/null && echo "API Working!" || echo "API Failed!"
> }
> ```

> 💡 **Pro Tip #3: Battery Alert Script**
>
> Get notified when battery is low:
> ```bash
> battery=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')
> [ "$battery" -lt 20 ] && termux-notification --title "Low Battery" --content "${battery}%"
> ```

> 💡 **Pro Tip #4: Location One-Liner**
>
> Quick GPS coordinates extraction:
> ```bash
> termux-location -p gps | grep -E '"latitude"|"longitude"'
> ```

> 💡 **Pro Tip #5: Silent Hours Script**
>
> Auto-silent at night:
> ```bash
> hour=$(date +%H)
> [ "$hour" -ge 22 ] || [ "$hour" -lt 7 ] && termux-volume ring 0
> ```

> 💡 **Pro Tip #6: WiFi Info Dashboard**
>
> Display comprehensive WiFi info:
> ```bash
> termux-wifi-connectioninfo | python3 -m json.tool
> ```

> 💡 **Pro Tip #7: Clipboard Integration**
>
> Copy command output to clipboard:
> ```bash
> echo "$(date): $(pwd)" | termux-clipboard-set
> ```

> 💡 **Pro Tip #8: Quick Torch Toggle**
>
> Create a torch toggle alias:
> ```bash
> alias torch='termux-torch on; sleep 5; termux-torch off'
> ```

> 💡 **Pro Tip #9: Notification with Action**
>
> Create actionable notification:
> ```bash
> termux-notification --title "Backup" --content "Ready?" \
>   --button1 "Run" --button1-action "bash ~/backup.sh"
> ```

> 💡 **Pro Tip #10: Sensor Monitoring**
>
> Monitor all sensors for debugging:
> ```bash
> termux-sensor -a -d 5000 | tee sensor_log.txt
> ```

---

## 🔥 REAL WORLD USE CASES

### Use Case 1: Automated Security Camera
```bash
#!/bin/bash
# security_cam.sh - Take photos at intervals

while true; do
    timestamp=$(date +%Y%m%d_%H%M%S)
    termux-camera-photo -c 0 "/sdcard/DCIM/security_${timestamp}.jpg"
    termux-toast "Photo captured: $timestamp"
    sleep 300  # Every 5 minutes
done
```

### Use Case 2: WiFi Reconnaissance Tool
```bash
#!/bin/bash
# wifi_recon.sh - Scan and log WiFi networks

output=~/wifi_scans/scan_$(date +%Y%m%d_%H%M%S).json
mkdir -p ~/wifi_scans

echo "Scanning WiFi networks..."
termux-wifi-scaninfo > "$output"

# Count networks
count=$(grep -c '"ssid"' "$output" 2>/dev/null || echo "0")
termux-notification --title "WiFi Scan Complete" --content "Found $count networks"
```

### Use Case 3: SMS Backup Automation
```bash
#!/bin/bash
# sms_backup.sh - Backup SMS to dated files

backup_dir=~/storage/downloads/sms_backups
mkdir -p "$backup_dir"

filename="sms_backup_$(date +%Y%m%d).json"
termux-sms-list -l 500 > "$backup_dir/$filename"

termux-notification --title "SMS Backup" --content "500 messages saved"
```

### Use Case 4: Location Logger
```bash
#!/bin/bash
# location_logger.sh - Track GPS coordinates

log_file=~/location_history.log

# Get location
location=$(termux-location -p gps -r last 2>/dev/null)

if [ -n "$location" ]; then
    lat=$(echo "$location" | grep -o '"latitude": [0-9.-]*' | grep -o '[0-9.-]*')
    lon=$(echo "$location" | grep -o '"longitude": [0-9.-]*' | grep -o '[0-9.-]*')
    
    echo "$(date '+%Y-%m-%d %H:%M:%S') | Lat: $lat | Lon: $lon" >> "$log_file"
fi
```

### Use Case 5: Smart Brightness Control
```bash
#!/bin/bash
# smart_brightness.sh - Adjust brightness by time and battery

hour=$(date +%H)
battery=$(termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*')

# Night mode
if [ "$hour" -ge 20 ] || [ "$hour" -lt 6 ]; then
    termux-brightness 30
# Low battery mode
elif [ "$battery" -lt 20 ]; then
    termux-brightness 50
# Day mode
else
    termux-brightness 150
fi
```

---

## ⚡ QUICK REFERENCE CARD

### Device Information
| Command | Description |
|---------|-------------|
| `termux-battery-status` | Battery percentage, health, temperature |
| `termux-telephony-deviceinfo` | IMEI, SIM info, network details |
| `termux-telephony-cellinfo` | Cell tower information |
| `termux-wifi-connectioninfo` | Current WiFi connection details |
| `termux-wifi-scaninfo` | Nearby WiFi networks |
| `termux-camera-info` | Available cameras list |

### Hardware Control
| Command | Description |
|---------|-------------|
| `termux-torch on/off` | Flashlight control |
| `termux-brightness N` | Set brightness (0-255) |
| `termux-volume STREAM N` | Volume control |
| `termux-vibrate -d MS` | Vibration (milliseconds) |
| `termux-camera-photo FILE` | Capture photo |
| `termux-fingerprint` | Biometric auth |

### Media & Notifications
| Command | Description |
|---------|-------------|
| `termux-notification` | Create status notification |
| `termux-toast "MSG"` | Popup message |
| `termux-media-player play FILE` | Play audio/video |
| `termux-media-scan FILE` | Gallery refresh |
| `termux-download URL` | Download file |

### Communication
| Command | Description |
|---------|-------------|
| `termux-contact-list` | List all contacts |
| `termux-sms-list -l N` | List N SMS messages |
| `termux-sms-send -n NUM "MSG"` | Send SMS |
| `termux-call-log -l N` | List N call entries |

### Location & Storage
| Command | Description |
|---------|-------------|
| `termux-location -p gps` | Get GPS coordinates |
| `termux-clipboard-get` | Get clipboard text |
| `termux-clipboard-set "TEXT"` | Set clipboard text |
| `termux-storage-get FILE` | File picker |
| `termux-share FILE` | Share to apps |

---

## 🏆 BONUS CONTENT

### Advanced API Combinations

#### 1. Voice Notification System
```bash
#!/bin/bash
# voice_notify.sh - Convert notification to speech (requires espeak)

notify_speak() {
    termux-notification --title "$1" --content "$2"
    echo "$2" | espeak -v en 2>/dev/null
}

notify_speak "Alert" "Your task is complete!"
```

#### 2. Geofencing Alert
```bash
#!/bin/bash
# geofence.sh - Alert when leaving designated area

HOME_LAT=28.6139
HOME_LON=77.2090
THRESHOLD=0.01  # Degrees (~1km)

while true; do
    loc=$(termux-location -p network)
    lat=$(echo "$loc" | grep -o '"latitude": [0-9.-]*' | grep -o '[0-9.-]*')
    lon=$(echo "$loc" | grep -o '"longitude": [0-9.-]*' | grep -o '[0-9.-]*')
    
    # Calculate distance (simplified)
    dist=$(echo "sqrt(($lat-$HOME_LAT)^2 + ($lon-$HOME_LON)^2)" | bc -l)
    
    if (( $(echo "$dist > $THRESHOLD" | bc -l) )); then
        termux-notification --title "Geofence Alert" --content "Left home area!"
    fi
    
    sleep 60
done
```

#### 3. Emergency Broadcast
```bash
#!/bin/bash
# emergency.sh - Send alert to multiple contacts

CONTACTS=("+911111111111" "+912222222222" "+913333333333")
MESSAGE="EMERGENCY: Please check on me immediately!"

for contact in "${CONTACTS[@]}"; do
    termux-sms-send -n "$contact" "$MESSAGE"
done

termux-vibrate -d 2000
termux-notification --title "Emergency" --content "Alerts sent to all contacts"
```

#### 4. Data Exfiltration Detection
```bash
#!/bin/bash
# data_monitor.sh - Monitor for unusual data usage

# Get initial WiFi scan
termux-wifi-scaninfo > /tmp/wifi_baseline.json

# Compare later scans
check_wifi_changes() {
    termux-wifi-scaninfo > /tmp/wifi_current.json
    diff /tmp/wifi_baseline.json /tmp/wifi_current.json && echo "No changes"
}
```

---

## 📝 CHAPTER SUMMARY

### Key Takeaways:

1. **API Architecture**
   - Two components required: Termux:API app + termux-api package
   - Bridge between Termux terminal and Android system
   - Works without root access

2. **Installation Essentials**
   - Install both components from F-Droid (NOT Play Store)
   - Grant permissions in Android Settings
   - Test with `termux-battery-status`

3. **Hardware APIs**
   - `termux-torch` for flashlight
   - `termux-brightness` (0-255)
   - `termux-volume` for streams
   - `termux-vibrate` for haptic feedback

4. **Media APIs**
   - `termux-notification` for alerts
   - `termux-toast` for quick messages
   - `termux-media-player` for audio/video
   - `termux-camera-photo` for capture

5. **Communication APIs**
   - SMS: list, send, filter
   - Contacts: list, search
   - Call log: history, filter

6. **Location & Sensors**
   - GPS with accuracy info
   - Multiple providers (gps, network, passive)
   - Sensor data streaming


---

**Chapter Complete! 🎉**

*Upgraded to NEXT LEVEL with all powerful features!*

*Created by T3rmuxk1ng | Termux Full Course*
