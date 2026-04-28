# Chapter 10: Termux API Setup & Overview

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

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 11: Termux Boot & Automation**

- Termux:Boot setup and configuration
- Creating boot scripts
- Background execution with nohup
- Cron jobs for scheduling
- Tasker integration basics
- Practical automation examples

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
