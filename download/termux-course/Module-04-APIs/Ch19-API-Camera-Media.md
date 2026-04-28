# Chapter 19: Termux API - Camera & Media

> **Module:** 4 - APIs  
> **Chapter:** 19 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Camera, Media Player, Volume, Microphone APIs |
| Commands Reference | All camera & media commands |
| Practice Exercises | Hands-on scripts and projects |
| Troubleshooting | Common issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 19
Title: Termux Camera & Media API | Photos, Videos, Audio Control
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut exciting hai - hum seekhenge Termux se camera aur 
media ko control karna!

Sochiye aapke phone ka camera command se capture karein, audio play 
karein, volume adjust karein, aur ye sab bina kisi app open kiye!

Ye Termux API ki power hai. Camera access, microphone recording, 
media player control - sab kuch terminal se.

Security tools ke liye ye bahut useful hai - surveillance scripts, 
automated photo capture, audio recording, aur bahut kuch!

To chaliye shuru karte hain - like, subscribe, aur notification bell 
ON kar lijiye!

---

[SECTION 1: CAMERA API OVERVIEW - 0:45 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle baat karte hain Termux Camera API ki.

Termux ke through aap phone ke camera ko fully control kar sakte ho:
- Front camera aur back camera dono accessible hain
- Photo capture kar sakte ho
- Camera parameters set kar sakte ho
- Multiple cameras list kar sakte ho

Lekin ye kaam karne ke liye chahiye:
1. Termux:API app installed hona chahiye
2. Camera permission dena padega
3. Storage permission bhi chahiye photos save ke liye

Pehle check karte hain Termux:API install hai ya nahi:

    pkg install termux-api

Agar pehle se installed hai to updated version milega.

Ab camera permissions check karte hain. Termux ko camera permission 
dena padega. Android Settings mein jao:
Settings → Apps → Termux → Permissions → Camera → Allow

Storage permission bhi chahiye:
Settings → Apps → Termux → Permissions → Storage/Files → Allow

Ye permissions ek baar mil gayi to har baar nahi puchega.

---

[SECTION 2: TERMUX-CAMERA-INFO - 3:00 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Pehla command seekhte hain - camera information:

    termux-camera-info

Ye command aapke phone ke saare cameras list karti hai. Output JSON 
format mein aata hai jisme ye information hoti hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CAMERA INFO OUTPUT EXAMPLE                            │
├─────────────────────────────────────────────────────────────────────────┤
│ [                                                                        │
│   {                                                                      │
│     "id": "0",                    ← Camera ID                           │
│     "facing": "back",             ← back ya front                       │
│     "jpeg_output_sizes": [...],   ← Available JPEG sizes                │
│     "focal_lengths": [1.0],       ← Focus info                          │
│     "auto_exposure_modes": [...], ← Exposure modes                      │
│     "capabilities": [...]         ← Camera capabilities                 │
│   },                                                                     │
│   {                                                                      │
│     "id": "1",                                                           │
│     "facing": "front",                                                   │
│     ...                                                                  │
│   }                                                                      │
│ ]                                                                        │
└─────────────────────────────────────────────────────────────────────────┘

Is output se aap pata kar sakte ho:
- Camera ID (0, 1, 2...) - multiple cameras ho sakte hain
- Front camera hai ya back
- Supported resolutions
- Available features

Demo karte hain:

    termux-camera-info | python -m json.tool

Ye command JSON ko readable format mein convert kar deta hai. Pipe 
symbol | use karke Python ka json.tool use kiya hai parsing ke liye.

Ya phir simpler output:

    termux-camera-info | grep -E '"id"|"facing"'

Ye sirf ID aur facing dikhayega.

---

[SECTION 3: TERMUX-CAMERA-PHOTO - 5:00 to 8:30]
─────────────────────────────────────────────────────────────────────────────

Ab main command - photo capture karna!

    termux-camera-photo <filename.jpg>

Basic example:

    termux-camera-photo photo.jpg

Ye command back camera use karke photo.jpg naam ki file current 
directory mein save karegi.

[DEMO: Photo capture]

Photo capture hone mein 2-3 seconds lagenge. Screen pe kuch nahi 
dikhega lekin background mein camera activate hoga aur photo lega.

Photo check karte hain:

    ls -la photo.jpg

File size se pata chalega ki photo successfully bani hai.

Ab dekhte hain camera selection kaise karte hain:

    termux-camera-photo -c 1 selfie.jpg

-c flag camera ID specify karta hai:
- -c 0 = Back camera (default)
- -c 1 = Front camera
- -c 2 = Extra camera (if available)

Different cameras check karte hain:

    # Back camera photo
    termux-camera-photo -c 0 back_photo.jpg
    
    # Front camera photo  
    termux-camera-photo -c 1 front_photo.jpg

Photo quality aur size bhi customize kar sakte ho:

    termux-camera-photo -c 0 --size 1920x1080 hd_photo.jpg

Size parameter resolution set karta hai. Available sizes 
termux-camera-info mein dikh jate hain.

[SCREEN: Showing captured photos in gallery]

Photo storage folder mein save hui hai. Aap use gallery mein 
dekh sakte ho ya file manager se access kar sakte ho.

Path: /data/data/com.termux/files/home/photo.jpg
Ya: ~/photo.jpg

Storage folder mein move karein gallery ke liye:

    mv photo.jpg ~/storage/dcim/

Ab ye photo aapki gallery mein dikhegi!

---

[SECTION 4: MEDIA PLAYER API - 8:30 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab media player ki baat karte hain.

Termux se audio files play kar sakte ho:

    termux-media-player play <audio_file>

Example:

    termux-media-player play song.mp3

Supported formats:
- MP3, WAV, OGG, FLAC, AAC, M4A
- Most common audio formats

Media player ke aur bhi commands hain:

    # Pause current playback
    termux-media-player pause
    
    # Resume playback
    termux-media-player play
    
    # Stop playback completely
    termux-media-player stop
    
    # Get current playback info
    termux-media-player info

Info command se current track ki detail milti hai:
- Track name
- Duration
- Current position
- Playback state

[DEMO: Media player controls]

Practical example - notification sound play karna:

    termux-media-player play /sdcard/Notifications/alert.mp3

Ye security scripts mein useful hai - jab koi event trigger ho 
to sound play ho jaye.

---

[SECTION 5: MEDIA SCAN API - 11:00 to 12:30]
─────────────────────────────────────────────────────────────────────────────

termux-media-scan command se files ko Android MediaStore mein add 
kar sakte ho.

Jab aap Termux mein naye files create karte ho - photos, videos, 
downloads - wo gallery mein immediately nahi dikh te. Media scan 
karna padta hai:

    termux-media-scan <file_or_directory>

Example:

    # Single file scan
    termux-media-scan photo.jpg
    
    # Directory scan
    termux-media-scan ~/storage/dcim/
    
    # Recursive scan
    termux-media-scan -r ~/storage/downloads/

Media scan ke baad files:
- Gallery app mein dikhenge
- Media players mein access honge
- File managers mein appear honge

Ye especially useful hai jab aap script se photos capture kar rahe 
ho aur unhe immediately gallery mein dikhana hai.

---

[SECTION 6: VOLUME CONTROL API - 12:30 to 14:30]
─────────────────────────────────────────────────────────────────────────────

Ab volume control seekhte hain - bahut useful feature!

    termux-volume <stream> <volume>

Android mein different audio streams hote hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    AUDIO STREAM TYPES                                    │
├──────────────────┬──────────────────────────────────────────────────────┤
│ Stream           │ Description                                          │
├──────────────────┼──────────────────────────────────────────────────────┤
│ ring             │ Ringtone volume                                      │
│ music            │ Media/music volume                                   │
│ notification     │ Notification volume                                  │
│ alarm            │ Alarm volume                                         │
│ call             │ Voice call volume                                    │
│ system           │ System sounds volume                                 │
└──────────────────┴──────────────────────────────────────────────────────┘

Examples:

    # Set music volume to 50%
    termux-volume music 50
    
    # Set notification volume to maximum
    termux-volume notification 100
    
    # Mute ringtone
    termux-volume ring 0
    
    # Set alarm volume to 75%
    termux-volume alarm 75

Current volume check karna:

    termux-volume music

Volume value 0 se 100 tak hota hai:
- 0 = Mute
- 50 = Half
- 100 = Maximum

[DEMO: Volume control]

Ye automation scripts mein bahut useful hai. Example - agar security 
alert ho to automatically volume maximum kar do aur alarm sound play 
kar do!

---

[SECTION 7: MICROPHONE RECORDING - 14:30 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek powerful feature - Audio recording!

    termux-microphone-record <command>

Commands available:

    # Start recording
    termux-microphone-record -f recording.mp3 -l 30
    
    # -f = filename
    # -l = limit in seconds (optional)
    
    # Get recording info
    termux-microphone-record -i
    
    # Stop recording
    termux-microphone-record -q

Recording examples:

    # Record 10 second audio
    termux-microphone-record -f audio.mp3 -l 10
    
    # Record unlimited (manual stop)
    termux-microphone-record -f long_recording.mp3
    
    # Check recording status
    termux-microphone-record -i
    
    # Stop recording
    termux-microphone-record -q

Quality settings:

    # High quality recording
    termux-microphone-record -f hq.mp3 -l 60 -r 44100 -c 2
    
    # -r = sample rate (44100 = CD quality)
    # -c = channels (1 = mono, 2 = stereo)

[DEMO: Recording audio]

Microphone permission bhi chahiye:
Settings → Apps → Termux → Permissions → Microphone → Allow

Recorded files ko storage mein move karein:

    mv audio.mp3 ~/storage/music/

---

[SECTION 8: PRACTICAL SCRIPTS - 17:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch practical scripts banate hain!

[SCRIPT 1: Automatic Photo Capture Script]

```bash
#!/bin/bash
# auto_photo.sh - Automatic photo capture

FOLDER=~/storage/dcim/TermuxPhotos
mkdir -p $FOLDER

TIMESTAMP=$(date +%Y%m%d_%H%M%S)
FILENAME="photo_$TIMESTAMP.jpg"

echo "Capturing photo..."
termux-camera-photo -c 0 "$FOLDER/$FILENAME"

if [ -f "$FOLDER/$FILENAME" ]; then
    echo "Photo saved: $FILENAME"
    termux-media-scan "$FOLDER/$FILENAME"
    termux-notification --title "Photo Captured" --content "$FILENAME saved"
else
    echo "Failed to capture photo"
fi
```

[SCRIPT 2: Security Camera Script]

```bash
#!/bin/bash
# security_cam.sh - Motion-triggered camera

FOLDER=~/storage/dcim/SecurityCam
mkdir -p $FOLDER

while true; do
    TIMESTAMP=$(date +%Y%m%d_%H%M%S)
    FILENAME="security_$TIMESTAMP.jpg"
    
    # Capture photo
    termux-camera-photo -c 0 "$FOLDER/$FILENAME"
    
    # Notify
    echo "Captured: $FILENAME"
    
    # Wait 30 seconds
    sleep 30
done
```

[SCRIPT 3: Voice Note Script]

```bash
#!/bin/bash
# voice_note.sh - Quick voice recorder

FOLDER=~/storage/music/VoiceNotes
mkdir -p $FOLDER

TIMESTAMP=$(date +%Y%m%d_%H%M%S)
FILENAME="note_$TIMESTAMP.mp3"

echo "Recording... Press Ctrl+C to stop"
termux-microphone-record -f "$FOLDER/$FILENAME"

# Ctrl+C will stop recording
trap 'termux-microphone-record -q; echo "Saved: $FILENAME"; exit' SIGINT
```

[SCRIPT 4: Time-lapse Script]

```bash
#!/bin/bash
# timelapse.sh - Capture photos at intervals

FOLDER=~/storage/dcim/TimeLapse
mkdir -p $FOLDER

INTERVAL=${1:-5}  # Default 5 seconds
COUNT=${2:-10}    # Default 10 photos

echo "Time-lapse: $COUNT photos at ${INTERVAL}s interval"

for i in $(seq 1 $COUNT); do
    FILENAME="frame_$(printf %04d $i).jpg"
    termux-camera-photo -c 0 "$FOLDER/$FILENAME"
    echo "Captured frame $i/$COUNT"
    sleep $INTERVAL
done

echo "Time-lapse complete!"
termux-notification --title "Time-lapse Done" --content "$COUNT photos captured"
```

---

[SECTION 9: SUMMARY & NEXT PREVIEW - 19:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 19 complete! Let's summarize:

✅ termux-camera-info - Camera details
✅ termux-camera-photo - Photo capture
✅ Camera selection - Front/back camera
✅ termux-media-player - Audio playback
✅ termux-media-scan - Gallery integration
✅ termux-volume - Volume control
✅ termux-microphone-record - Audio recording
✅ Practical scripts - Automation

Important Commands:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 19 - KEY COMMANDS                             │
├─────────────────────────────────────────────────────────────────────────┤
│ termux-camera-info              │ List all cameras                      │
│ termux-camera-photo photo.jpg   │ Capture photo                         │
│ termux-camera-photo -c 1 s.jpg  │ Front camera photo                    │
│ termux-media-player play x.mp3  │ Play audio                            │
│ termux-media-player pause       │ Pause playback                        │
│ termux-media-scan file.jpg      │ Add to gallery                        │
│ termux-volume music 75          │ Set volume to 75%                     │
│ termux-microphone-record -f a.mp3│ Record audio                         │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 20 mein:
- Network information APIs
- WiFi scanning
- Connection details
- Network monitoring

Agar video helpful lagi:
👍 Like karein
🔔 Subscribe karein
💬 Comment karein
📤 Share karein

Thank you for watching! See you in Chapter 20!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Camera API Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX CAMERA API ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Termux Shell Command                          │   │
│   │   termux-camera-photo / termux-camera-info                       │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Termux:API App (Bridge)                       │   │
│   │   Receives broadcast intent, accesses Android Camera API         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android Camera Service                        │   │
│   │   Camera2 API (Android 5.0+)                                     │   │
│   │   - Camera device access                                         │   │
│   │   - Capture requests                                             │   │
│   │   - Image processing                                             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Hardware Camera                               │   │
│   │   - Back Camera (ID: 0)                                          │   │
│   │   - Front Camera (ID: 1)                                         │   │
│   │   - Additional cameras (if available)                            │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Camera Commands Deep Dive

#### termux-camera-info

```bash
# Basic usage - list all cameras
termux-camera-info

# Output is JSON - parse with jq if installed
pkg install jq
termux-camera-info | jq '.'

# Extract specific camera info
termux-camera-info | jq '.[] | select(.facing=="back")'

# Get camera IDs only
termux-camera-info | jq '.[].id'

# Get facing direction
termux-camera-info | jq '.[] | {id, facing}'

# Check supported resolutions
termux-camera-info | jq '.[] | .jpeg_output_sizes'

# Parse without jq (using Python)
termux-camera-info | python -c "
import sys, json
data = json.load(sys.stdin)
for cam in data:
    print(f\"Camera {cam['id']}: {cam['facing']}\")
"
```

#### termux-camera-photo Options

```bash
# Basic photo capture
termux-camera-photo output.jpg

# Camera selection
termux-camera-photo -c 0 photo.jpg     # Back camera (default)
termux-camera-photo -c 1 selfie.jpg    # Front camera

# Custom size/resolution
termux-camera-photo --size 1920x1080 hd.jpg
termux-camera-photo --size 1280x720 medium.jpg
termux-camera-photo --size 640x480 small.jpg

# Save to specific location
termux-camera-photo ~/storage/dcim/Photo_$(date +%s).jpg

# Combine options
termux-camera-photo -c 0 --size 1920x1080 ~/storage/dcim/photo.jpg
```

### 3. Media Player Commands

```bash
# Play audio file
termux-media-player play /sdcard/Music/song.mp3

# Play from Termux home
termux-media-player play ~/music.mp3

# Control playback
termux-media-player pause      # Pause current track
termux-media-player play       # Resume (without file = resume)
termux-media-player stop       # Stop completely

# Get info
termux-media-player info       # Current track info

# Example output of info:
# {
#   "track": "song.mp3",
#   "duration": 240,
#   "position": 45,
#   "state": "playing"
# }
```

### 4. Volume Control Details

```bash
# Get current volume
termux-volume music

# Set volume (0-100)
termux-volume music 50

# All stream types
termux-volume ring 80          # Ringtone
termux-volume music 70         # Media/music
termux-volume notification 60  # Notifications
termux-volume alarm 100        # Alarms
termux-volume call 50          # Call volume
termux-volume system 50        # System sounds

# Mute specific stream
termux-volume music 0

# Maximum volume
termux-volume music 100
```

### 5. Microphone Recording Options

```bash
# Basic recording (unlimited duration)
termux-microphone-record -f recording.mp3

# Time-limited recording (30 seconds)
termux-microphone-record -f recording.mp3 -l 30

# High quality recording
termux-microphone-record -f hq.mp3 -r 44100 -c 2
# -r = sample rate (8000, 16000, 22050, 44100)
# -c = channels (1 = mono, 2 = stereo)

# Low quality (smaller file)
termux-microphone-record -f lq.mp3 -r 8000 -c 1

# Check recording info
termux-microphone-record -i

# Stop recording
termux-microphone-record -q
```

### 6. Media Scan Usage

```bash
# Scan single file
termux-media-scan photo.jpg

# Scan directory
termux-media-scan ~/storage/dcim/

# Recursive scan
termux-media-scan -r ~/storage/downloads/

# Scan multiple files
termux-media-scan photo1.jpg photo2.jpg photo3.jpg

# Scan with wildcards
for f in *.jpg; do termux-media-scan "$f"; done
```

---

## 💻 COMPLETE SCRIPT EXAMPLES

### Example 1: Photo Capture with Metadata

```bash
#!/bin/bash
# smart_photo.sh - Photo capture with metadata

PHOTO_DIR=~/storage/dcim/TermuxPhotos
mkdir -p "$PHOTO_DIR"

TIMESTAMP=$(date +%Y%m%d_%H%M%S)
PHOTO_FILE="$PHOTO_DIR/IMG_$TIMESTAMP.jpg"
META_FILE="$PHOTO_DIR/IMG_$TIMESTAMP.txt"

# Capture photo
echo "Capturing photo..."
termux-camera-photo -c 0 "$PHOTO_FILE"

if [ -f "$PHOTO_FILE" ]; then
    # Save metadata
    echo "Photo: IMG_$TIMESTAMP.jpg" > "$META_FILE"
    echo "Date: $(date)" >> "$META_FILE"
    echo "Location: $(termux-location 2>/dev/null || echo 'Unknown')" >> "$META_FILE"
    echo "Device: $(termux-telephony-deviceinfo 2>/dev/null | head -1 || echo 'Unknown')" >> "$META_FILE"
    
    # Scan to gallery
    termux-media-scan "$PHOTO_FILE"
    
    # Notify
    termux-notification --title "Photo Captured" \
        --content "Saved as IMG_$TIMESTAMP.jpg" \
        --sound
    
    echo "✅ Photo saved: $PHOTO_FILE"
else
    echo "❌ Failed to capture photo"
    exit 1
fi
```

### Example 2: Time-Lapse Photography

```bash
#!/bin/bash
# timelapse.sh - Advanced time-lapse script

# Configuration
OUTPUT_DIR=~/storage/dcim/TimeLapse
INTERVAL=${1:-10}      # Seconds between shots (default: 10)
DURATION=${2:-300}     # Total duration in seconds (default: 5 min)
CAMERA=${3:-0}         # Camera ID (default: back)

mkdir -p "$OUTPUT_DIR"

# Calculate number of shots
SHOTS=$((DURATION / INTERVAL))

echo "═══════════════════════════════════════════"
echo "     TIME-LAPSE PHOTOGRAPHY"
echo "═══════════════════════════════════════════"
echo "Camera: $CAMERA"
echo "Interval: ${INTERVAL}s"
echo "Duration: ${DURATION}s"
echo "Total shots: $SHOTS"
echo "═══════════════════════════════════════════"

# Create session folder
SESSION="session_$(date +%Y%m%d_%H%M%S)"
SESSION_DIR="$OUTPUT_DIR/$SESSION"
mkdir -p "$SESSION_DIR"

# Capture loop
for i in $(seq -w 1 $SHOTS); do
    FILENAME="frame_$i.jpg"
    FILEPATH="$SESSION_DIR/$FILENAME"
    
    termux-camera-photo -c "$CAMERA" "$FILEPATH"
    
    # Progress
    PROGRESS=$((i * 100 / SHOTS))
    echo "[$PROGRESS%] Captured: $FILENAME"
    
    # Notification for every 10%
    if [ $((i % (SHOTS / 10))) -eq 0 ]; then
        termux-notification --title "Time-lapse" --content "$PROGRESS% complete"
    fi
    
    # Wait (except for last shot)
    if [ "$i" -lt "$SHOTS" ]; then
        sleep "$INTERVAL"
    fi
done

# Scan all photos
termux-media-scan -r "$SESSION_DIR"

# Create info file
cat > "$SESSION_DIR/info.txt" << EOF
Time-lapse Session: $SESSION
Date: $(date)
Camera: $CAMERA
Interval: ${INTERVAL}s
Duration: ${DURATION}s
Frames: $SHOTS
EOF

# Final notification
termux-notification --title "Time-lapse Complete" \
    --content "$SHOTS photos saved in $SESSION" \
    --sound

echo ""
echo "✅ Time-lapse complete!"
echo "📁 Location: $SESSION_DIR"
echo "📸 Frames: $SHOTS"
```

### Example 3: Security Camera with Motion Detection

```bash
#!/bin/bash
# security_camera.sh - Basic surveillance script

# Configuration
WATCH_DIR=~/storage/dcim/SecurityWatch
LOG_FILE=~/security_log.txt
INTERVAL=30           # Check interval in seconds
CAMERA=0              # Camera ID

mkdir -p "$WATCH_DIR"

echo "═══════════════════════════════════════════"
echo "     SECURITY CAMERA MONITOR"
echo "═══════════════════════════════════════════"
echo "Started: $(date)"
echo "Interval: ${INTERVAL}s"
echo "Watch directory: $WATCH_DIR"
echo "Press Ctrl+C to stop"
echo "═══════════════════════════════════════════"

# Log function
log_message() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOG_FILE"
}

# Capture function
capture_photo() {
    TIMESTAMP=$(date +%Y%m%d_%H%M%S)
    FILENAME="security_$TIMESTAMP.jpg"
    FILEPATH="$WATCH_DIR/$FILENAME"
    
    termux-camera-photo -c "$CAMERA" "$FILEPATH"
    
    if [ -f "$FILEPATH" ]; then
        termux-media-scan "$FILEPATH"
        log_message "Captured: $FILENAME"
        return 0
    else
        log_message "ERROR: Failed to capture"
        return 1
    fi
}

# Main loop
counter=0
while true; do
    counter=$((counter + 1))
    capture_photo
    
    # Every 10 captures, show status
    if [ $((counter % 10)) -eq 0 ]; then
        log_message "Status: $counter photos captured"
        termux-notification --title "Security Camera" \
            --content "$counter photos captured" --priority low
    fi
    
    sleep "$INTERVAL"
done
```

### Example 4: Audio Recorder with Timer

```bash
#!/bin/bash
# voice_recorder.sh - Advanced voice recorder

RECORD_DIR=~/storage/music/VoiceRecordings
mkdir -p "$RECORD_DIR"

# Arguments
DURATION=${1:-30}  # Default 30 seconds
NAME=${2:-recording}

FILENAME="${NAME}_$(date +%Y%m%d_%H%M%S).mp3"
FILEPATH="$RECORD_DIR/$FILENAME"

echo "═══════════════════════════════════════════"
echo "     VOICE RECORDER"
echo "═══════════════════════════════════════════"
echo "Duration: ${DURATION}s"
echo "Output: $FILENAME"
echo "═══════════════════════════════════════════"

# Start recording with limit
termux-microphone-record -f "$FILEPATH" -l "$DURATION" -r 44100 -c 2

# Wait for recording to complete
echo "Recording..."
for i in $(seq 1 "$DURATION"); do
    REMAINING=$((DURATION - i))
    printf "\rTime remaining: %02ds " "$REMAINING"
    sleep 1
done
echo ""

# Stop recording (in case limit didn't work)
termux-microphone-record -q 2>/dev/null

# Verify and scan
if [ -f "$FILEPATH" ]; then
    FILESIZE=$(du -h "$FILEPATH" | cut -f1)
    termux-media-scan "$FILEPATH"
    termux-notification --title "Recording Complete" \
        --content "$FILENAME ($FILESIZE)"
    echo "✅ Saved: $FILEPATH ($FILESIZE)"
else
    echo "❌ Recording failed"
    exit 1
fi
```

### Example 5: Media Control Script

```bash
#!/bin/bash
# media_control.sh - Complete media control

MUSIC_DIR=~/storage/music

show_menu() {
    clear
    echo "═══════════════════════════════════════════"
    echo "     MEDIA CONTROL CENTER"
    echo "═══════════════════════════════════════════"
    echo "1. Play audio file"
    echo "2. Pause/Resume"
    echo "3. Stop playback"
    echo "4. Set volume"
    echo "5. Current track info"
    echo "6. Record audio"
    echo "7. Exit"
    echo "═══════════════════════════════════════════"
}

play_audio() {
    echo "Available audio files:"
    find "$MUSIC_DIR" -type f \( -name "*.mp3" -o -name "*.wav" -o -name "*.ogg" \) | head -20
    
    echo ""
    read -p "Enter file path: " filepath
    if [ -f "$filepath" ]; then
        termux-media-player play "$filepath"
        echo "Now playing: $(basename "$filepath")"
    else
        echo "File not found!"
    fi
}

set_volume() {
    echo "Stream types: music, ring, notification, alarm, call, system"
    read -p "Enter stream type: " stream
    read -p "Enter volume (0-100): " vol
    
    termux-volume "$stream" "$vol"
    echo "Volume set: $stream = $vol"
}

record_audio() {
    read -p "Enter duration (seconds): " dur
    read -p "Enter filename: " name
    
    FILEPATH="$MUSIC_DIR/${name}.mp3"
    termux-microphone-record -f "$FILEPATH" -l "$dur"
    echo "Recording for $dur seconds..."
    sleep "$dur"
    termux-microphone-record -q
    echo "Recording saved: $FILEPATH"
}

# Main loop
while true; do
    show_menu
    read -p "Choose option: " choice
    
    case $choice in
        1) play_audio ;;
        2) termux-media-player pause ;;
        3) termux-media-player stop ;;
        4) set_volume ;;
        5) termux-media-player info ;;
        6) record_audio ;;
        7) echo "Goodbye!"; exit 0 ;;
        *) echo "Invalid option" ;;
    esac
    
    read -p "Press Enter to continue..."
done
```

### Example 6: Python Integration - Camera Class

```python
#!/usr/bin/env python3
"""
termux_camera.py - Python class for Termux camera operations
"""

import subprocess
import json
import os
from datetime import datetime

class TermuxCamera:
    """Termux Camera API wrapper"""
    
    def __init__(self, storage_dir="~/storage/dcim/TermuxPhotos"):
        self.storage_dir = os.path.expanduser(storage_dir)
        os.makedirs(self.storage_dir, exist_ok=True)
    
    def get_cameras(self):
        """Get list of available cameras"""
        try:
            result = subprocess.run(
                ['termux-camera-info'],
                capture_output=True,
                text=True
            )
            if result.returncode == 0:
                return json.loads(result.stdout)
            return []
        except Exception as e:
            print(f"Error getting cameras: {e}")
            return []
    
    def list_camera_ids(self):
        """Get camera IDs and facing direction"""
        cameras = self.get_cameras()
        return [(cam['id'], cam['facing']) for cam in cameras]
    
    def capture(self, camera_id=0, filename=None):
        """Capture photo from specified camera"""
        if filename is None:
            timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
            filename = f"photo_{timestamp}.jpg"
        
        filepath = os.path.join(self.storage_dir, filename)
        
        try:
            result = subprocess.run(
                ['termux-camera-photo', '-c', str(camera_id), filepath],
                capture_output=True,
                text=True
            )
            
            if result.returncode == 0 and os.path.exists(filepath):
                self._scan_media(filepath)
                return filepath
            return None
        except Exception as e:
            print(f"Error capturing photo: {e}")
            return None
    
    def capture_front(self, filename=None):
        """Capture from front camera"""
        return self.capture(camera_id=1, filename=filename)
    
    def capture_back(self, filename=None):
        """Capture from back camera"""
        return self.capture(camera_id=0, filename=filename)
    
    def _scan_media(self, filepath):
        """Add file to media gallery"""
        subprocess.run(['termux-media-scan', filepath], capture_output=True)
    
    def timelapse(self, count=10, interval=5, camera_id=0):
        """Capture time-lapse photos"""
        import time
        
        photos = []
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        session_dir = os.path.join(self.storage_dir, f"timelapse_{timestamp}")
        os.makedirs(session_dir, exist_ok=True)
        
        for i in range(count):
            filename = f"frame_{i:04d}.jpg"
            filepath = self.capture(camera_id, os.path.join(session_dir, filename))
            if filepath:
                photos.append(filepath)
                print(f"Captured frame {i+1}/{count}")
            
            if i < count - 1:
                time.sleep(interval)
        
        return photos


# Usage example
if __name__ == "__main__":
    cam = TermuxCamera()
    
    # List cameras
    print("Available cameras:")
    for cam_id, facing in cam.list_camera_ids():
        print(f"  Camera {cam_id}: {facing}")
    
    # Capture photo
    print("\nCapturing photo...")
    filepath = cam.capture_back("test_photo.jpg")
    if filepath:
        print(f"Photo saved: {filepath}")
    else:
        print("Failed to capture photo")
```

### Example 7: Python Media Controller

```python
#!/usr/bin/env python3
"""
termux_media.py - Python class for Termux media operations
"""

import subprocess
import json
import os
from datetime import datetime

class TermuxMedia:
    """Termux Media API wrapper"""
    
    def __init__(self):
        pass
    
    def play(self, filepath):
        """Play audio file"""
        if not os.path.exists(filepath):
            raise FileNotFoundError(f"File not found: {filepath}")
        
        result = subprocess.run(
            ['termux-media-player', 'play', filepath],
            capture_output=True,
            text=True
        )
        return result.returncode == 0
    
    def pause(self):
        """Pause playback"""
        subprocess.run(['termux-media-player', 'pause'], capture_output=True)
    
    def resume(self):
        """Resume playback"""
        subprocess.run(['termux-media-player', 'play'], capture_output=True)
    
    def stop(self):
        """Stop playback"""
        subprocess.run(['termux-media-player', 'stop'], capture_output=True)
    
    def info(self):
        """Get current playback info"""
        result = subprocess.run(
            ['termux-media-player', 'info'],
            capture_output=True,
            text=True
        )
        if result.returncode == 0 and result.stdout.strip():
            try:
                return json.loads(result.stdout)
            except json.JSONDecodeError:
                pass
        return None
    
    def set_volume(self, stream, volume):
        """Set volume for a stream type"""
        if volume < 0 or volume > 100:
            raise ValueError("Volume must be between 0 and 100")
        
        subprocess.run(
            ['termux-volume', stream, str(volume)],
            capture_output=True
        )
    
    def get_volume(self, stream):
        """Get current volume for a stream type"""
        result = subprocess.run(
            ['termux-volume', stream],
            capture_output=True,
            text=True
        )
        if result.returncode == 0:
            try:
                data = json.loads(result.stdout)
                return data.get('volume', data.get('percentage', None))
            except:
                pass
        return None


class TermuxRecorder:
    """Termux Audio Recording wrapper"""
    
    def __init__(self, output_dir="~/storage/music/Recordings"):
        self.output_dir = os.path.expanduser(output_dir)
        os.makedirs(self.output_dir, exist_ok=True)
        self.recording = False
    
    def start(self, filename=None, limit=None, sample_rate=44100, channels=2):
        """Start recording"""
        if self.recording:
            return False
        
        if filename is None:
            filename = f"recording_{datetime.now().strftime('%Y%m%d_%H%M%S')}.mp3"
        
        filepath = os.path.join(self.output_dir, filename)
        
        cmd = ['termux-microphone-record', '-f', filepath, 
               '-r', str(sample_rate), '-c', str(channels)]
        
        if limit:
            cmd.extend(['-l', str(limit)])
        
        subprocess.Popen(cmd, stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)
        self.recording = True
        self.current_file = filepath
        return filepath
    
    def stop(self):
        """Stop recording"""
        if not self.recording:
            return None
        
        subprocess.run(['termux-microphone-record', '-q'], capture_output=True)
        self.recording = False
        
        if os.path.exists(self.current_file):
            subprocess.run(['termux-media-scan', self.current_file], capture_output=True)
            return self.current_file
        return None
    
    def info(self):
        """Get recording info"""
        result = subprocess.run(
            ['termux-microphone-record', '-i'],
            capture_output=True,
            text=True
        )
        if result.returncode == 0 and result.stdout.strip():
            try:
                return json.loads(result.stdout)
            except:
                pass
        return None


# Usage example
if __name__ == "__main__":
    media = TermuxMedia()
    recorder = TermuxRecorder()
    
    # Volume control
    print("Setting music volume to 70%...")
    media.set_volume('music', 70)
    
    # Recording example
    print("\nRecording 5 second audio...")
    filepath = recorder.start(limit=5)
    print(f"Recording to: {filepath}")
    
    import time
    time.sleep(6)  # Wait for recording
    
    result = recorder.stop()
    if result:
        print(f"Recording saved: {result}")
```

---

## 📋 COMMANDS REFERENCE

### Camera Commands

| Command | Description | Example |
|---------|-------------|---------|
| `termux-camera-info` | List all cameras | `termux-camera-info` |
| `termux-camera-photo <file>` | Capture photo | `termux-camera-photo photo.jpg` |
| `termux-camera-photo -c <id>` | Use specific camera | `termux-camera-photo -c 1 selfie.jpg` |
| `termux-camera-photo --size WxH` | Set resolution | `termux-camera-photo --size 1920x1080 hd.jpg` |

### Media Player Commands

| Command | Description | Example |
|---------|-------------|---------|
| `termux-media-player play <file>` | Play audio | `termux-media-player play song.mp3` |
| `termux-media-player pause` | Pause playback | `termux-media-player pause` |
| `termux-media-player stop` | Stop playback | `termux-media-player stop` |
| `termux-media-player info` | Get track info | `termux-media-player info` |

### Media Scan Commands

| Command | Description | Example |
|---------|-------------|---------|
| `termux-media-scan <file>` | Scan single file | `termux-media-scan photo.jpg` |
| `termux-media-scan <dir>` | Scan directory | `termux-media-scan ~/storage/dcim/` |
| `termux-media-scan -r <dir>` | Recursive scan | `termux-media-scan -r ~/storage/downloads/` |

### Volume Commands

| Command | Description | Example |
|---------|-------------|---------|
| `termux-volume <stream>` | Get volume | `termux-volume music` |
| `termux-volume <stream> <vol>` | Set volume | `termux-volume music 75` |

### Recording Commands

| Command | Description | Example |
|---------|-------------|---------|
| `termux-microphone-record -f <file>` | Start recording | `termux-microphone-record -f rec.mp3` |
| `termux-microphone-record -f <file> -l <sec>` | Time-limited recording | `termux-microphone-record -f rec.mp3 -l 30` |
| `termux-microphone-record -i` | Recording info | `termux-microphone-record -i` |
| `termux-microphone-record -q` | Stop recording | `termux-microphone-record -q` |

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Camera Operations

```bash
# Task: Learn camera basics

# Step 1: Check available cameras
termux-camera-info

# Step 2: Capture photo with back camera
termux-camera-photo back_photo.jpg

# Step 3: Capture selfie with front camera
termux-camera-photo -c 1 selfie.jpg

# Step 4: Move photos to gallery
mkdir -p ~/storage/dcim/TermuxTest
mv *.jpg ~/storage/dcim/TermuxTest/

# Step 5: Scan so they appear in gallery
termux-media-scan -r ~/storage/dcim/TermuxTest/

# Expected: Two photos in gallery
```

### Exercise 2: Media Player Control

```bash
# Task: Control audio playback

# Step 1: Find an audio file
find ~/storage/music -name "*.mp3" | head -5

# Step 2: Play the audio file
termux-media-player play ~/storage/music/song.mp3

# Step 3: Check playback info
termux-media-player info

# Step 4: Pause playback
termux-media-player pause

# Step 5: Resume playback
termux-media-player play

# Step 6: Stop playback
termux-media-player stop

# Step 7: Adjust volume
termux-volume music 50
```

### Exercise 3: Audio Recording

```bash
# Task: Record audio with different settings

# Step 1: Create recordings folder
mkdir -p ~/storage/music/MyRecordings

# Step 2: Record 10 second audio (default quality)
termux-microphone-record -f ~/storage/music/MyRecordings/test1.mp3 -l 10

# Step 3: Wait for recording
echo "Recording for 10 seconds..."
sleep 12

# Step 4: Record high quality audio
termux-microphone-record -f ~/storage/music/MyRecordings/hq.mp3 -l 5 -r 44100 -c 2
sleep 7

# Step 5: Check recordings
ls -la ~/storage/music/MyRecordings/

# Step 6: Play your recording
termux-media-player play ~/storage/music/MyRecordings/test1.mp3
```

### Exercise 4: Create a Photo Script

```bash
# Task: Create an automated photo capture script

# Create the script
cat > ~/capture_photos.sh << 'EOF'
#!/bin/bash
# Automated photo capture script

FOLDER=~/storage/dcim/AutoPhotos
mkdir -p "$FOLDER"

# Get arguments
COUNT=${1:-5}
INTERVAL=${2:-3}
CAMERA=${3:-0}

echo "Capturing $COUNT photos at ${INTERVAL}s interval..."

for i in $(seq 1 $COUNT); do
    FILENAME="photo_$(date +%Y%m%d_%H%M%S)_$i.jpg"
    termux-camera-photo -c "$CAMERA" "$FOLDER/$FILENAME"
    echo "Captured $i/$COUNT: $FILENAME"
    
    if [ $i -lt $COUNT ]; then
        sleep "$INTERVAL"
    fi
done

termux-media-scan -r "$FOLDER"
echo "Done! Photos saved in $FOLDER"
EOF

chmod +x ~/capture_photos.sh

# Run the script
~/capture_photos.sh 5 2 0
```

### Exercise 5: Volume Automation

```bash
# Task: Create volume control script

cat > ~/volume_control.sh << 'EOF'
#!/bin/bash
# Volume control utility

show_volumes() {
    echo "Current Volumes:"
    echo "─────────────────────────"
    for stream in music ring notification alarm call system; do
        vol=$(termux-volume $stream 2>/dev/null | grep -o '"volume":[0-9]*' | cut -d: -f2)
        echo "$stream: $vol"
    done
    echo "─────────────────────────"
}

case "$1" in
    show) show_volumes ;;
    set)
        termux-volume "$2" "$3"
        echo "Set $2 to $3"
        ;;
    mute)
        termux-volume "$2" 0
        echo "Muted $2"
        ;;
    max)
        termux-volume "$2" 100
        echo "Maxed $2"
        ;;
    *)
        echo "Usage: $0 {show|set <stream> <vol>|mute <stream>|max <stream>}"
        ;;
esac
EOF

chmod +x ~/volume_control.sh

# Test it
~/volume_control.sh show
~/volume_control.sh set music 50
~/volume_control.sh mute notification
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Camera Permission Denied

```bash
# Symptoms:
# - "Error: Could not access camera"
# - Empty photo file
# - No output from termux-camera-info

# Solution 1: Grant permission via Android Settings
# Settings → Apps → Termux → Permissions → Camera → Allow

# Solution 2: Request permission from Termux
# Note: This triggers the permission dialog
termux-camera-photo test.jpg
# If dialog doesn't appear, go to Settings manually

# Solution 3: Check if Termux:API is installed
pkg list-installed | grep termux-api
# If not installed:
pkg install termux-api

# Solution 4: Check camera availability
# Some devices may have camera restrictions
dumpsys media.camera | head -20
```

### Problem 2: Photo Not Saving

```bash
# Symptoms:
# - Command runs but no file created
# - 0 byte file
# - Permission denied errors

# Solution 1: Check storage permission
termux-setup-storage
ls ~/storage/

# Solution 2: Use absolute path
termux-camera-photo ~/storage/dcim/photo.jpg

# Solution 3: Check disk space
df -h

# Solution 4: Create directory first
mkdir -p ~/storage/dcim/TermuxPhotos
termux-camera-photo ~/storage/dcim/TermuxPhotos/photo.jpg
```

### Problem 3: Media Player Not Working

```bash
# Symptoms:
# - "Error: Could not play file"
# - No sound
# - File not found

# Solution 1: Check file exists
ls -la /path/to/audio.mp3

# Solution 2: Check file format
file audio.mp3
# Supported: MP3, WAV, OGG, FLAC, AAC, M4A

# Solution 3: Check volume
termux-volume music
termux-volume music 50

# Solution 4: Stop any existing playback
termux-media-player stop
termux-media-player play audio.mp3

# Solution 5: Check audio focus
# Other apps might be using audio
```

### Problem 4: Recording Fails

```bash
# Symptoms:
# - "Error: Could not start recording"
# - Empty recording file
# - Recording stops immediately

# Solution 1: Check microphone permission
# Settings → Apps → Termux → Permissions → Microphone → Allow

# Solution 2: Check if another app is using microphone
# Close other recording apps

# Solution 3: Try different parameters
termux-microphone-record -f test.mp3 -r 16000 -c 1

# Solution 4: Check recording status
termux-microphone-record -i

# Solution 5: Stop any stuck recordings
termux-microphone-record -q
```

### Problem 5: Photos Not Showing in Gallery

```bash
# Symptoms:
# - Photo file exists
# - Gallery app doesn't show it
# - File manager shows it but not gallery

# Solution 1: Run media scan
termux-media-scan /path/to/photo.jpg

# Solution 2: Scan entire directory
termux-media-scan -r ~/storage/dcim/

# Solution 3: Move to standard location
mv photo.jpg ~/storage/dcim/Camera/
termux-media-scan ~/storage/dcim/Camera/

# Solution 4: Force media scan (requires root)
# For non-root, restart the device
# Or use: am broadcast -a android.intent.action.MEDIA_MOUNTED -d file:///sdcard

# Solution 5: Check file extension
# Must be .jpg or .jpeg for photos
mv photo photo.jpg
termux-media-scan photo.jpg
```

### Problem 6: Volume Not Changing

```bash
# Symptoms:
# - Command runs but volume unchanged
# - Wrong stream affected
# - Volume resets after command

# Solution 1: Check available streams
termux-volume

# Solution 2: Use correct stream name
# Common mistake: "media" instead of "music"
termux-volume music 50  # Correct
termux-volume media 50  # Wrong

# Solution 3: Check if device overrides
# Some devices have "Do Not Disturb" or volume limit

# Solution 4: Verify change
termux-volume music 75
termux-volume music  # Should show 75

# Solution 5: Check for automation apps
# Tasker or similar might override volume
```

### Problem 7: Termux:API Not Responding

```bash
# Symptoms:
# - Commands hang
# - "Error: Termux:API not installed"
# - Timeout errors

# Solution 1: Install Termux:API app
# Download from F-Droid:
# https://f-droid.org/packages/com.termux.api/

# Solution 2: Reinstall termux-api package
pkg uninstall termux-api
pkg install termux-api

# Solution 3: Check if API app can run
# Open Termux:API app from launcher

# Solution 4: Grant all permissions
# Settings → Apps → Termux:API → Permissions
# Allow all requested permissions

# Solution 5: Restart Termux
exit
# Open Termux again

# Solution 6: Check battery optimization
# Settings → Battery → Unoptimized apps
# Add Termux and Termux:API to unoptimized
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Camera Focus**
```
┌────────────────────────────────────┐
│  [Camera icon with code overlay]   │
│                                    │
│   📸 TERMUX CAMERA API             │
│   Command-Line Photography!        │
│                                    │
│   ✓ Photo Capture                  │
│   ✓ Time-lapse                     │
│   ✓ Security Camera                │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Media Control**
```
┌────────────────────────────────────┐
│  [Speaker/Media icons]             │
│                                    │
│   🎵 TERMUX MEDIA CONTROL          │
│                                    │
│   📸 Camera | 🎤 Mic | 🔊 Volume   │
│                                    │
│   Full API Tutorial                │
│   Chapter 19 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Script Focus**
```
┌────────────────────────────────────┐
│  [Terminal screen with script]     │
│                                    │
│   $ termux-camera-photo hack.jpg   │
│   $ termux-microphone-record       │
│                                    │
│   🚀 CAMERA & MEDIA MASTERY        │
│   15+ Practical Scripts!           │
│                                    │
│   [T3rmuxk1ng]                     │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📸 Termux Full Course - Chapter 19: Camera & Media API

🔥 In this video you'll learn:
• Camera API - photo capture from terminal
• Front and back camera selection
• Media player control
• Audio recording with microphone
• Volume control for all streams
• Time-lapse photography script
• Security camera automation
• Python integration for camera & media

⏱️ Timestamps:
0:00 - Introduction
0:45 - Camera API Overview
3:00 - termux-camera-info
5:00 - termux-camera-photo
8:30 - Media Player API
11:00 - Media Scan API
12:30 - Volume Control
14:30 - Microphone Recording
17:00 - Practical Scripts
19:00 - Summary

📝 Commands from this video:
termux-camera-info
termux-camera-photo photo.jpg
termux-camera-photo -c 1 selfie.jpg
termux-media-player play song.mp3
termux-volume music 75
termux-microphone-record -f audio.mp3 -l 30

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxAPI #CameraAPI #TermuxCourse #T3rmuxk1ng #MediaControl #TermuxTutorial #AndroidHacking

---
⚠️ Disclaimer: This video is for educational purposes only. Use tools responsibly and respect privacy laws when recording.
```

### Tags List

```
termux, termux api, termux camera, termux media, termux tutorial,
termux camera photo, termux media player, termux volume control,
termux microphone record, termux audio recording, termux camera api,
termux time lapse, termux security camera, termux automation,
termux scripts, termux python, android camera terminal,
command line camera, terminal media control, termux course hindi,
t3rmuxk1ng, termux full course, android automation
```

### Hashtags

```
#Termux #TermuxAPI #CameraAPI #TermuxCamera #MediaControl 
#TermuxTutorial #TermuxHindi #AndroidTerminal #TermuxCourse 
#T3rmuxk1ng #Automation #Privacy #Security #CommandLine
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux API Wiki | https://wiki.termux.com/wiki/Termux:API |
| Termux API GitHub | https://github.com/termux/termux-api |
| Camera2 API Docs | https://developer.android.com/reference/android/hardware/camera2 |

### Related Tools

| Tool | Purpose |
|------|---------|
| ffmpeg | Video/audio processing |
| ImageMagick | Image manipulation |
| sox | Audio processing |
| exiftool | Metadata handling |

### Python Libraries for Extension

```python
# For advanced image processing
pip install Pillow
pip install opencv-python-headless

# For audio processing
pip install pydub
pip install soundfile

# For video creation from images
pip install moviepy
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 20, verify:

- [ ] Termux:API app installed
- [ ] Camera, microphone, storage permissions granted
- [ ] Successfully captured photo with back camera
- [ ] Successfully captured selfie with front camera
- [ ] Audio playback working with media player
- [ ] Volume control tested
- [ ] Audio recording completed
- [ ] At least one practical script created and tested
- [ ] Photos appear in gallery after media scan

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 20: Termux API - Network**

- Network information APIs
- WiFi connection details
- WiFi scanning (requires root on some devices)
- Connection monitoring
- Network statistics
- IP address information

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
