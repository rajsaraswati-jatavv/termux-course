# Chapter 39: YouTube Downloaders in Termux

> **Module:** 7 - Utilities  
> **Chapter:** 39 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed yt-dlp & youtube-dl coverage |
| Installation Guide | yt-dlp, youtube-dl, ffmpeg setup |
| Commands Reference | 30+ yt-dlp commands |
| Practice Exercises | Hands-on download tasks |
| Troubleshooting | Common download issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 39
Title: YouTube Downloaders in Termux | yt-dlp Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon T3rmuxk1ng aur aaj hum seekhenge ek bahut hi 
useful topic - YouTube Video Download karna Termux ke through!

Haan, aapne sahi suna! Aap apne Android phone se bina kisi app ke, 
sirf commands use karke YouTube videos download kar sakte ho - 
HD quality mein, audio extract kar sakte ho, playlists download 
kar sakte ho, subtitles bhi nikal sakte ho!

Sab kuch FREE mein, koi ads nahi, koi premium subscription nahi!

Ye chapter hamare utilities module ka part hai. Hum seekhenge 
yt-dlp tool jo ki youtube-dl ka advanced version hai - faster, 
more features, actively maintained.

Chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe 
karein - taki koi video miss na ho.

---

[SECTION 1: YT-DLP INTRODUCTION - 0:45 to 3:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain ki yt-dlp kya hai aur kyun use karein.

yt-dlp ek command-line tool hai jo YouTube aur 1000+ websites se 
videos download kar sakta hai. Ye youtube-dl ka fork hai - matlab 
ye usi code pe based hai but with improvements.

YouTube-dl purana ho gaya tha - slow tha, YouTube frequently 
usko block karta tha. yt-dlp banaya gaya with:
- Better performance
- More site support
- Regular updates
- More format options

┌─────────────────────────────────────────────────────────────────────────┐
│                    YT-DLP VS YOUTUBE-DL COMPARISON                       │
├──────────────────┬──────────────────┬───────────────────────────────────┤
│ Feature          │ yt-dlp           │ youtube-dl                        │
├──────────────────┼──────────────────┼───────────────────────────────────┤
│ Speed            │ ⭐⭐⭐⭐⭐ Fast     │ ⭐⭐⭐ Slow                        │
│ Updates          │ ✅ Active        │ ❌ Sporadic                       │
│ Sites Support    │ 1000+            │ ~500                              │
│ Format Selection │ ✅ Advanced      │ Basic                             │
│ Thumbnail Embed  │ ✅ Yes           │ ❌ No                             │
│ SponsorBlock     │ ✅ Yes           │ ❌ No                             │
│ Age Restricted   │ ✅ Works         │ ❌ Often fails                    │
│ Termux Support   │ ✅ Excellent     │ ✅ Good                           │
└──────────────────┴──────────────────┴───────────────────────────────────┘

Kya yt-dlp sirf YouTube ke liye hai? NAHI!

Ye 1000+ websites support karta hai:
✓ YouTube (obviously)
✓ YouTube Music
✓ Vimeo
✓ Dailymotion
✓ Twitch
✓ Twitter/X
✓ Instagram
✓ TikTok
✓ Facebook
✓ Reddit
✓ And many more...

Sabse best baat - ye Termux pe perfectly kaam karta hai!

---

[SECTION 2: INSTALLATION - 3:30 to 6:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab yt-dlp install karte hain Termux mein.

Pehle apna Termux update karein:

    pkg update && pkg upgrade -y

Ab yt-dlp install karein:

    pkg install yt-dlp -y

Installation mein kuch seconds lagenge. Wait karein.

[SCREEN: yt-dlp installation output]

Installation ke baad verify karein:

    yt-dlp --version

Version number dikhna chahiye jaise: 2023.11.16 ya newer.

Agar version dikha raha hai - installation successful hai!

Ab ek aur important package chahiye - FFmpeg!

FFmpeg kya karta hai? Ye video aur audio processing ke liye 
chahiye - formats convert karne ke liye, audio extract karne 
ke liye, video merge karne ke liye.

Install karein:

    pkg install ffmpeg -y

FFmpeg bahut bada package hai, thoda time lagega.

Verify installation:

    ffmpeg -version

Agar dono install ho gaye - aap ready hain download karne ke liye!

[Alternative Installation Method - Python pip]

Agar pkg se install nahi ho raha, to Python pip use kar sakte ho:

    pkg install python -y
    pip install yt-dlp

Ye bhi kaam karega!

---

[SECTION 3: BASIC VIDEO DOWNLOAD - 6:30 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Ab actual download start karte hain!

Sabse basic command:

    yt-dlp "VIDEO_URL"

Example:

    yt-dlp "https://www.youtube.com/watch?v=dQw4w9WgXcQ"

[SCREEN: Download in progress]

Kya dikhega?
- Video title
- Video description
- Available formats
- Download progress
- File size
- Speed
- ETA (estimated time)

Download complete hone ke baad, video current directory mein 
save hoga.

Check karein:

    ls -la

Video file dikhegi jaise: "Video Title [dQw4w9WgXcQ].mp4"

Ab storage mein save karna ho to:

    cd ~/storage/downloads
    yt-dlp "VIDEO_URL"

Ye video directly downloads folder mein save hoga!

Important tip: URL ko quotes mein rakhein, especially agar URL 
mein special characters hain.

---

[SECTION 4: VIDEO QUALITY SELECTION - 9:00 to 11:30]
─────────────────────────────────────────────────────────────────────────────

By default yt-dlp best available quality download karta hai.
Lekin aap specific quality bhi select kar sakte ho.

Pehle dekhein kya qualities available hain:

    yt-dlp -F "VIDEO_URL"

[SCREEN: Format list output]

Ye command list dikha degi:
- Format code
- Extension (mp4, webm, etc.)
- Resolution (144p, 360p, 720p, 1080p, 4K)
- File size
- Note (video only, audio only, etc.)

Example output:
┌─────────────────────────────────────────────────────────────────────────┐
│ ID    EXT  RESOLUTION  │   FILESIZE  │ NOTE                            │
├─────────────────────────────────────────────────────────────────────────┤
│ 137   mp4  1920x1080   │   450.5MiB  │ video only                      │
│ 136   mp4  1280x720    │   250.2MiB  │ video only                      │
│ 135   mp4  854x480     │   120.8MiB  │ video only                      │
│ 134   mp4  640x360     │    80.5MiB  │ video only                      │
│ 133   mp4  426x240     │    35.2MiB  │ video only                      │
│ 140   m4a  audio only  │     5.2MiB  │ audio only                      │
│ 22    mp4  1280x720    │   280.3MiB  │ video + audio (pre-merged)      │
└─────────────────────────────────────────────────────────────────────────┘

Specific quality download karne ke liye:

    yt-dlp -f 136 "VIDEO_URL"    # 720p video only
    yt-dlp -f 22 "VIDEO_URL"     # 720p with audio

Better tareeka - quality selector use karein:

    yt-dlp -f "best[height<=720]" "VIDEO_URL"    # Best 720p or lower
    yt-dlp -f "best[height<=480]" "VIDEO_URL"    # Best 480p or lower
    yt-dlp -f "bestvideo[height<=1080]+bestaudio" "VIDEO_URL"  # 1080p video + best audio

Best practice for mobile:

    yt-dlp -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]" "VIDEO_URL"

Ye 720p video with audio download karega, mobile compatible format mein!

---

[SECTION 5: AUDIO-ONLY DOWNLOAD - 11:30 to 13:30]
─────────────────────────────────────────────────────────────────────────────

Bahut baar hume sirf audio chahiye - songs download karne ke liye, 
podcasts ke liye, etc.

Audio extract karne ke liye:

    yt-dlp -x "VIDEO_URL"

Ya phir:

    yt-dlp --extract-audio "VIDEO_URL"

Ye best quality audio download karega.

Audio format specify karna ho to:

    yt-dlp -x --audio-format mp3 "VIDEO_URL"
    yt-dlp -x --audio-format m4a "VIDEO_URL"
    yt-dlp -x --audio-format wav "VIDEO_URL"
    yt-dlp -x --audio-format flac "VIDEO_URL"

MP3 most common hai, M4A better quality deta hai for same size.

Audio quality set karna ho to:

    yt-dlp -x --audio-format mp3 --audio-quality 0 "VIDEO_URL"   # Best
    yt-dlp -x --audio-format mp3 --audio-quality 5 "VIDEO_URL"   # Medium
    yt-dlp -x --audio-format mp3 --audio-quality 9 "VIDEO_URL"   # Worst

0 = best quality, 9 = worst quality

Best quality ke liye:

    yt-dlp -x --audio-format mp3 --audio-quality 0 "VIDEO_URL"

Thumbnail bhi embed karna ho audio mein:

    yt-dlp -x --audio-format mp3 --embed-thumbnail "VIDEO_URL"

Metadata bhi add ho:

    yt-dlp -x --audio-format mp3 --embed-thumbnail --add-metadata "VIDEO_URL"

Ab aapka audio file properly tagged hoga with thumbnail!

---

[SECTION 6: PLAYLIST DOWNLOAD - 13:30 to 15:30]
─────────────────────────────────────────────────────────────────────────────

Playlist download karna bahut easy hai!

Bas playlist URL dalein:

    yt-dlp "PLAYLIST_URL"

Example:

    yt-dlp "https://www.youtube.com/playlist?list=PLxxxxx"

Saari videos download ho jaayengi!

Lekin control bhi chahiye hota hai:

Playlist mein se specific videos download karna ho:

    yt-dlp --playlist-items 1,3,5 "PLAYLIST_URL"        # Videos 1, 3, 5
    yt-dlp --playlist-items 1-10 "PLAYLIST_URL"         # Videos 1 to 10
    yt-dlp --playlist-items 5- "PLAYLIST_URL"           # From 5 to end
    yt-dlp --playlist-items -5 "PLAYLIST_URL"           # First 5 videos

Reverse order mein download:

    yt-dlp --playlist-reverse "PLAYLIST_URL"

Playlist info dekhne ke liye (without downloading):

    yt-dlp --flat-playlist -j "PLAYLIST_URL" | jq -r '.title'

Sirf playlist ke names nikalna ho:

    yt-dlp --flat-playlist --print "%(title)s" "PLAYLIST_URL"

Playlist ka archive maintain karna (track which videos downloaded):

    yt-dlp --download-archive downloaded.txt "PLAYLIST_URL"

Ye file mein record rakhega, dobara run karne pe sirf new videos 
download hongi!

---

[SECTION 7: SUBTITLES DOWNLOAD - 15:30 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Subtitles download karna bhi possible hai!

Available subtitles dekhein:

    yt-dlp --list-subs "VIDEO_URL"

Subtitles download karne ke liye:

    yt-dlp --write-subs "VIDEO_URL"              # Download subtitles
    yt-dlp --write-auto-subs "VIDEO_URL"         # Auto-generated subtitles
    yt-dlp --write-subs --write-auto-subs "VIDEO_URL"  # Both

Language specify karna ho to:

    yt-dlp --write-subs --sub-lang en "VIDEO_URL"        # English
    yt-dlp --write-subs --sub-lang hi "VIDEO_URL"        # Hindi
    yt-dlp --write-subs --sub-lang en,hi "VIDEO_URL"     # Both

Subtitle format:

    yt-dlp --write-subs --sub-lang en --sub-format srt "VIDEO_URL"

Subtitle ko video mein embed karna ho:

    yt-dlp --embed-subs --sub-lang en "VIDEO_URL"

Ye hardcode nahi karega, bas soft subtitle add hoga.

---

[SECTION 8: ADVANCED FEATURES - 17:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch advanced features dekhte hain:

[OUTPUT FILENAME CUSTOMIZATION]

    yt-dlp -o "my_video.mp4" "VIDEO_URL"
    yt-dlp -o "%(title)s.%(ext)s" "VIDEO_URL"
    yt-dlp -o "%(title)s-%(id)s.%(ext)s" "VIDEO_URL"
    yt-dlp -o "~/storage/downloads/%(title)s.%(ext)s" "VIDEO_URL"

More template options:
- %(title)s - Video title
- %(id)s - Video ID
- %(ext)s - File extension
- %(uploader)s - Channel name
- %(upload_date)s - Upload date
- %(resolution)s - Resolution
- %(format_id)s - Format ID

[DOWNLOAD SPEED LIMIT]

Speed limit karna ho (data save karne ke liye):

    yt-dlp --limit-rate 1M "VIDEO_URL"    # Max 1 MB/s
    yt-dlp --limit-rate 500K "VIDEO_URL"  # Max 500 KB/s

[PROXY CONFIGURATION]

Proxy use karna ho to:

    yt-dlp --proxy "http://proxy:port" "VIDEO_URL"
    yt-dlp --proxy "socks5://127.0.0.1:9050" "VIDEO_URL"

[COOKIES FOR AGE-RESTRICTED VIDEOS]

Age-restricted videos ke liye cookies chahiye:

Pehle browser se cookies export karein (browser extension use karke)

    yt-dlp --cookies cookies.txt "VIDEO_URL"

Ya browser cookies directly use karein:

    yt-dlp --cookies-from-browser chrome "VIDEO_URL"
    yt-dlp --cookies-from-browser firefox "VIDEO_URL"

[BATCH DOWNLOADING]

Multiple videos ek saath:

    yt-dlp "URL1" "URL2" "URL3"

Ya file se URLs read karein:

    yt-dlp -a urls.txt

urls.txt file mein ek URL per line:

    https://youtube.com/watch?v=xxxxx
    https://youtube.com/watch?v=yyyyy
    https://youtube.com/watch?v=zzzzz

---

[SECTION 9: AUTOMATION SCRIPT - 19:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek practical script banate hain jo common tasks automate kare!

[CODE DEMONSTRATION]

    nano ytdown.sh

Script mein likhein:

```bash
#!/bin/bash
# YouTube Downloader Script by T3rmuxk1ng

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m'

echo -e "${GREEN}═══════════════════════════════════════${NC}"
echo -e "${GREEN}   YouTube Downloader - T3rmuxk1ng${NC}"
echo -e "${GREEN}═══════════════════════════════════════${NC}"

# Check if URL provided
if [ -z "$1" ]; then
    echo -e "${RED}Usage: ./ytdown.sh <URL> [option]${NC}"
    echo "Options:"
    echo "  -v  : Video (720p)"
    echo "  -a  : Audio only (MP3)"
    echo "  -h  : HD Video (1080p)"
    exit 1
fi

URL="$1"
OPTION="$2"

case $OPTION in
    -v)
        echo -e "${YELLOW}Downloading 720p video...${NC}"
        yt-dlp -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]" \
               -o "~/storage/downloads/%(title)s.%(ext)s" "$URL"
        ;;
    -a)
        echo -e "${YELLOW}Extracting audio (MP3)...${NC}"
        yt-dlp -x --audio-format mp3 --audio-quality 0 \
               --embed-thumbnail --add-metadata \
               -o "~/storage/downloads/%(title)s.%(ext)s" "$URL"
        ;;
    -h)
        echo -e "${YELLOW}Downloading 1080p HD video...${NC}"
        yt-dlp -f "bestvideo[height<=1080][ext=mp4]+bestaudio[ext=m4a]" \
               -o "~/storage/downloads/%(title)s.%(ext)s" "$URL"
        ;;
    *)
        echo -e "${YELLOW}Downloading best quality...${NC}"
        yt-dlp -o "~/storage/downloads/%(title)s.%(ext)s" "$URL"
        ;;
esac

echo -e "${GREEN}✓ Download complete!${NC}"
```

Script ko executable banayein:

    chmod +x ytdown.sh

Ab use karein:

    ./ytdown.sh "VIDEO_URL" -v    # Video
    ./ytdown.sh "VIDEO_URL" -a    # Audio
    ./ytdown.sh "VIDEO_URL" -h    # HD Video

---

[SECTION 10: SUMMARY & NEXT PREVIEW - 21:00 to 22:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 39 complete! Let's summarize:

✅ yt-dlp kya hai - Best YouTube downloader for Termux
✅ Installation - pkg install yt-dlp ffmpeg
✅ Basic download - Simple video download
✅ Quality selection - 720p, 1080p, custom formats
✅ Audio extraction - MP3, M4A with metadata
✅ Playlist download - Full playlist with options
✅ Subtitles - Download and embed
✅ Advanced features - Proxy, cookies, batch download
✅ Automation script - Custom download script

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 39 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ yt-dlp "URL"                          │ Basic download                  │
│ yt-dlp -F "URL"                       │ List available formats          │
│ yt-dlp -f 22 "URL"                    │ Specific format                 │
│ yt-dlp -x --audio-format mp3 "URL"    │ Audio only (MP3)                │
│ yt-dlp --write-subs "URL"             │ Download subtitles              │
│ yt-dlp --playlist-items 1-10 "URL"    │ Playlist range                  │
│ yt-dlp --limit-rate 1M "URL"          │ Speed limit                     │
│ yt-dlp -o "%(title)s.%(ext)s" "URL"   │ Custom filename                 │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 40 mein hum seekhenge:
- File compression tools
- ZIP, TAR, GZ archives
- 7z compression
- Encryption and password protection

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 40!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. yt-dlp Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         YT-DLP WORKFLOW                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐             │
│   │   URL Input  │───▶│   Extractor  │───▶│   Info Dict  │             │
│   └──────────────┘    └──────────────┘    └──────────────┘             │
│                              │                    │                     │
│                              ▼                    ▼                     │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐             │
│   │   Website    │    │   Formats    │    │  Metadata    │             │
│   │   Detection  │    │   Analysis   │    │  Extraction  │             │
│   └──────────────┘    └──────────────┘    └──────────────┘             │
│                                                    │                     │
│   ┌────────────────────────────────────────────────┘                    │
│   │                                                                      │
│   ▼                                                                      │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐             │
│   │   Format     │───▶│  Downloader  │───▶│  File Writer │             │
│   │   Selection  │    │   (HTTP)     │    │  (Output)    │             │
│   └──────────────┘    └──────────────┘    └──────────────┘             │
│                                                    │                     │
│                                                    ▼                     │
│                                            ┌──────────────┐             │
│                                            │  Post-Proc   │             │
│                                            │  (FFmpeg)    │             │
│                                            └──────────────┘             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Supported Sites (Categories)

| Category | Examples |
|----------|----------|
| Video Platforms | YouTube, Vimeo, Dailymotion, Rumble |
| Social Media | Twitter/X, Instagram, TikTok, Facebook |
| Streaming | Twitch, Kick, Vimeo, DTube |
| News | CNN, BBC, ABC News, Reuters |
| Education | Khan Academy, Coursera, edX |
| Music | YouTube Music, SoundCloud, Bandcamp |
| Adult | PornHub, XVideos, xHamster |
| Other | Reddit, Imgur, Pinterest |

### 3. Format Selection Syntax

```
FORMAT SELECTION SYNTAX
═══════════════════════

Basic:
  -f FORMAT           Select specific format

Quality Selectors:
  best                Best quality (pre-merged video+audio)
  worst               Worst quality
  bestvideo           Best video only
  bestaudio           Best audio only

Filters (square brackets):
  [height=N]          Exact resolution
  [height<=N]         Maximum resolution
  [height>=N]         Minimum resolution
  [ext=EXT]           File extension
  [filesize<N]        Maximum file size
  [proto=PROTOCOL]    Protocol (http, https, m3u8)

Combinations:
  +                   Merge video and audio
  /                   Fallback options

Examples:
  -f "best[height<=720]"
  -f "bestvideo[height<=1080]+bestaudio"
  -f "bestvideo[ext=mp4]+bestaudio[ext=m4a]/best"
  -f "best[filesize<100M]"
```

### 4. Output Template Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `%(title)s` | Video title | "My Video" |
| `%(id)s` | Video ID | "dQw4w9WgXcQ" |
| `%(ext)s` | File extension | "mp4" |
| `%(uploader)s` | Uploader name | "ChannelName" |
| `%(channel)s` | Channel name | "ChannelName" |
| `%(uploader_id)s` | Uploader ID | "@username" |
| `%(upload_date)s` | Upload date (YYYYMMDD) | "20231115" |
| `%(duration)s` | Duration in seconds | "245" |
| `%(resolution)s` | Resolution | "1920x1080" |
| `%(format_id)s` | Format ID | "22" |
| `%(view_count)s` | View count | "1234567" |
| `%(like_count)s` | Like count | "12345" |
| `%(playlist)s` | Playlist name | "My Playlist" |
| `%(playlist_index)s` | Playlist position | "1" |
| `%(autonumber)s` | Auto-increment number | "001" |

---

## 🔧 INSTALLATION GUIDE

### Method 1: Termux Package (Recommended)

```bash
# Update Termux
pkg update && pkg upgrade -y

# Install yt-dlp
pkg install yt-dlp -y

# Install FFmpeg (required for format conversion)
pkg install ffmpeg -y

# Verify installations
yt-dlp --version
ffmpeg -version
```

### Method 2: Python pip

```bash
# Install Python
pkg install python -y

# Install yt-dlp via pip
pip install yt-dlp

# Install FFmpeg
pkg install ffmpeg -y

# Verify
yt-dlp --version
```

### Method 3: Direct Binary

```bash
# Download latest binary
curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o $PREFIX/bin/yt-dlp

# Make executable
chmod +x $PREFIX/bin/yt-dlp

# Verify
yt-dlp --version
```

### Updating yt-dlp

```bash
# If installed via pkg
pkg upgrade yt-dlp

# If installed via pip
pip install -U yt-dlp

# Using yt-dlp self-update (if installed via pip)
yt-dlp -U
```

---

## 📋 COMMANDS REFERENCE (30+ yt-dlp Commands)

### Basic Download Commands

```bash
# 1. Basic video download
yt-dlp "https://www.youtube.com/watch?v=VIDEO_ID"

# 2. Download to specific directory
yt-dlp -o "/sdcard/Download/%(title)s.%(ext)s" "URL"

# 3. Download with custom filename
yt-dlp -o "my_video.mp4" "URL"

# 4. Download with title and ID
yt-dlp -o "%(title)s-%(id)s.%(ext)s" "URL"

# 5. Download and show progress only
yt-dlp --progress "URL"
```

### Quality Selection Commands

```bash
# 6. List available formats
yt-dlp -F "URL"

# 7. Download specific format by ID
yt-dlp -f 22 "URL"

# 8. Download best quality
yt-dlp -f best "URL"

# 9. Download worst quality (for small size)
yt-dlp -f worst "URL"

# 10. Download best video up to 720p
yt-dlp -f "bestvideo[height<=720]+bestaudio" "URL"

# 11. Download best video up to 1080p
yt-dlp -f "bestvideo[height<=1080]+bestaudio" "URL"

# 12. Download 4K video if available
yt-dlp -f "bestvideo[height<=2160]+bestaudio" "URL"

# 13. Download MP4 format only
yt-dlp -f "bestvideo[ext=mp4]+bestaudio[ext=m4a]/best[ext=mp4]" "URL"

# 14. Download with file size limit
yt-dlp -f "best[filesize<100M]" "URL"
```

### Audio Extraction Commands

```bash
# 15. Extract audio (auto format)
yt-dlp -x "URL"

# 16. Extract audio as MP3
yt-dlp -x --audio-format mp3 "URL"

# 17. Extract audio as M4A (better quality)
yt-dlp -x --audio-format m4a "URL"

# 18. Extract audio as FLAC (lossless)
yt-dlp -x --audio-format flac "URL"

# 19. Extract audio with best quality
yt-dlp -x --audio-format mp3 --audio-quality 0 "URL"

# 20. Extract audio with embedded thumbnail
yt-dlp -x --audio-format mp3 --embed-thumbnail "URL"

# 21. Extract audio with full metadata
yt-dlp -x --audio-format mp3 --embed-thumbnail --add-metadata "URL"

# 22. Extract audio with custom filename
yt-dlp -x --audio-format mp3 -o "%(title)s.%(ext)s" "URL"
```

### Playlist Commands

```bash
# 23. Download entire playlist
yt-dlp "PLAYLIST_URL"

# 24. Download specific videos from playlist
yt-dlp --playlist-items 1,3,5 "PLAYLIST_URL"

# 25. Download range from playlist
yt-dlp --playlist-items 1-10 "PLAYLIST_URL"

# 26. Download from position 5 to end
yt-dlp --playlist-items 5- "PLAYLIST_URL"

# 27. Download first 5 videos
yt-dlp --playlist-items -5 "PLAYLIST_URL"

# 28. Download playlist in reverse order
yt-dlp --playlist-reverse "PLAYLIST_URL"

# 29. Download playlist with archive tracking
yt-dlp --download-archive archive.txt "PLAYLIST_URL"

# 30. Number playlist files
yt-dlp -o "%(playlist_index)s-%(title)s.%(ext)s" "PLAYLIST_URL"
```

### Subtitle Commands

```bash
# 31. List available subtitles
yt-dlp --list-subs "URL"

# 32. Download all subtitles
yt-dlp --write-subs "URL"

# 33. Download auto-generated subtitles
yt-dlp --write-auto-subs "URL"

# 34. Download specific language subtitles
yt-dlp --write-subs --sub-lang en "URL"

# 35. Download Hindi subtitles
yt-dlp --write-subs --sub-lang hi "URL"

# 36. Download subtitles in SRT format
yt-dlp --write-subs --sub-lang en --sub-format srt "URL"

# 37. Embed subtitles in video
yt-dlp --embed-subs --sub-lang en "URL"
```

### Advanced Commands

```bash
# 38. Download with speed limit
yt-dlp --limit-rate 1M "URL"

# 39. Download with proxy
yt-dlp --proxy "http://127.0.0.1:8080" "URL"

# 40. Download with SOCKS5 proxy
yt-dlp --proxy "socks5://127.0.0.1:9050" "URL"

# 41. Download age-restricted video with cookies
yt-dlp --cookies cookies.txt "URL"

# 42. Download using browser cookies
yt-dlp --cookies-from-browser chrome "URL"

# 43. Download multiple videos from file
yt-dlp -a urls.txt

# 44. Download with verbose output
yt-dlp -v "URL"

# 45. Download video info as JSON
yt-dlp --dump-json "URL"

# 46. Download video description
yt-dlp --write-description "URL"

# 47. Download video thumbnail
yt-dlp --write-thumbnail "URL"

# 48. Download and embed thumbnail
yt-dlp --embed-thumbnail "URL"

# 49. Skip download, only get info
yt-dlp --skip-download "URL"

# 50. Download with retry on error
yt-dlp --retries 10 "URL"

# 51. Download private video (with authentication)
yt-dlp --username USER --password PASS "URL"

# 52. Download with custom user agent
yt-dlp --user-agent "Mozilla/5.0" "URL"

# 53. Download with referer header
yt-dlp --add-header "Referer:https://example.com" "URL"

# 54. Download and convert to MP4
yt-dlp --recode-video mp4 "URL"

# 55. Download and merge to MKV
yt-dlp --merge-output-format mkv "URL"

# 56. Download with SponsorBlock marking
yt-dlp --sponsorblock-mark all "URL"

# 57. Download without SponsorBlock segments
yt-dlp --sponsorblock-remove all "URL"

# 58. Download YouTube video with chapters
yt-dlp --write-info-json "URL"

# 59. Download with concurrent fragments
yt-dlp --concurrent-fragments 4 "URL"

# 60. Download live stream after it ends
yt-dlp --wait-for-video 30 "LIVE_URL"
```

### Configuration Commands

```bash
# 61. Create config file
mkdir -p ~/.config/yt-dlp
nano ~/.config/yt-dlp/config

# Example config file contents:
# --no-mtime
# -f bestvideo[height<=1080]+bestaudio
# -o ~/storage/downloads/%(title)s.%(ext)s
# --embed-thumbnail
# --add-metadata

# 62. Use custom config file
yt-dlp --config-location /path/to/config "URL"

# 63. Ignore config file
yt-dlp --ignore-config "URL"
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Download

```bash
# Task: Download a YouTube video and verify

# Step 1: Navigate to downloads folder
cd ~/storage/downloads

# Step 2: Download a video
yt-dlp "https://www.youtube.com/watch?v=jNQXAC9IVRw"

# Step 3: Check downloaded file
ls -la

# Step 4: Play or move file
# File will be in current directory

# Expected: Video file downloaded successfully
```

### Exercise 2: Quality Selection

```bash
# Task: Download video in specific quality

# Step 1: List available formats
yt-dlp -F "https://www.youtube.com/watch?v=jNQXAC9IVRw"

# Step 2: Note the format codes for 720p

# Step 3: Download 720p video
yt-dlp -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]" \
       -o "video_720p.%(ext)s" \
       "https://www.youtube.com/watch?v=jNQXAC9IVRw"

# Step 4: Verify file
ls -la video_720p.*

# Expected: 720p MP4 video downloaded
```

### Exercise 3: Audio Extraction

```bash
# Task: Extract audio from video as MP3

# Step 1: Navigate to music folder (create if needed)
mkdir -p ~/storage/music
cd ~/storage/music

# Step 2: Extract audio with metadata
yt-dlp -x \
       --audio-format mp3 \
       --audio-quality 0 \
       --embed-thumbnail \
       --add-metadata \
       -o "%(title)s.%(ext)s" \
       "https://www.youtube.com/watch?v=jNQXAC9IVRw"

# Step 3: Verify audio file
ls -la *.mp3

# Expected: MP3 file with thumbnail and metadata
```

### Exercise 4: Playlist Download

```bash
# Task: Download first 3 videos from a playlist

# Step 1: Create playlist directory
mkdir -p ~/storage/downloads/playlist
cd ~/storage/downloads/playlist

# Step 2: Download first 3 videos
yt-dlp --playlist-items 1-3 \
       -o "%(playlist_index)s-%(title)s.%(ext)s" \
       "PLAYLIST_URL"

# Step 3: Check downloaded files
ls -la

# Expected: 3 numbered video files
```

### Exercise 5: Create Download Script

```bash
# Task: Create a download automation script

# Step 1: Create script file
cat > ~/ytdown.sh << 'EOF'
#!/bin/bash

# Colors for output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
CYAN='\033[0;36m'
NC='\033[0m'

show_help() {
    echo -e "${CYAN}YouTube Downloader - T3rmuxk1ng${NC}"
    echo ""
    echo "Usage: $0 [option] <URL>"
    echo ""
    echo "Options:"
    echo "  -v, --video      Download video (720p)"
    echo "  -h, --hd         Download HD video (1080p)"
    echo "  -a, --audio      Download audio only (MP3)"
    echo "  -f, --formats    List available formats"
    echo "  -p, --playlist   Download playlist"
    echo "  --help           Show this help"
    echo ""
    echo "Examples:"
    echo "  $0 -v https://youtube.com/watch?v=xxxxx"
    echo "  $0 -a https://youtube.com/watch?v=xxxxx"
    echo "  $0 -p https://youtube.com/playlist?list=xxxxx"
}

if [ -z "$1" ] || [ "$1" = "--help" ]; then
    show_help
    exit 0
fi

OPTION="$1"
URL="$2"

case $OPTION in
    -v|--video)
        echo -e "${YELLOW}Downloading video (720p)...${NC}"
        yt-dlp -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]" \
               -o "~/storage/downloads/%(title)s.%(ext)s" "$URL"
        ;;
    -h|--hd)
        echo -e "${YELLOW}Downloading HD video (1080p)...${NC}"
        yt-dlp -f "bestvideo[height<=1080][ext=mp4]+bestaudio[ext=m4a]" \
               -o "~/storage/downloads/%(title)s.%(ext)s" "$URL"
        ;;
    -a|--audio)
        echo -e "${YELLOW}Downloading audio (MP3)...${NC}"
        yt-dlp -x --audio-format mp3 --audio-quality 0 \
               --embed-thumbnail --add-metadata \
               -o "~/storage/music/%(title)s.%(ext)s" "$URL"
        ;;
    -f|--formats)
        echo -e "${YELLOW}Available formats:${NC}"
        yt-dlp -F "$URL"
        ;;
    -p|--playlist)
        echo -e "${YELLOW}Downloading playlist...${NC}"
        yt-dlp -o "~/storage/downloads/playlist/%(playlist_index)s-%(title)s.%(ext)s" "$URL"
        ;;
    *)
        # Assume it's a URL without option
        URL="$OPTION"
        echo -e "${YELLOW}Downloading best quality...${NC}"
        yt-dlp -o "~/storage/downloads/%(title)s.%(ext)s" "$URL"
        ;;
esac

echo -e "${GREEN}✓ Done!${NC}"
EOF

# Step 2: Make executable
chmod +x ~/ytdown.sh

# Step 3: Test the script
~/ytdown.sh --help

# Step 4: Try a download
~/ytdown.sh -a "https://www.youtube.com/watch?v=jNQXAC9IVRw"

# Expected: Script works with all options
```

### Exercise 6: Batch Download

```bash
# Task: Download multiple videos from a URL list

# Step 1: Create URL list file
cat > ~/urls.txt << 'EOF'
https://www.youtube.com/watch?v=jNQXAC9IVRw
https://www.youtube.com/watch?v=dQw4w9WgXcQ
https://www.youtube.com/watch?v=9bZkp7q19f0
EOF

# Step 2: Create batch download script
cat > ~/batch_download.sh << 'EOF'
#!/bin/bash

URL_FILE="$1"
OUTPUT_DIR="$HOME/storage/downloads/batch"

mkdir -p "$OUTPUT_DIR"

if [ -z "$URL_FILE" ]; then
    echo "Usage: $0 <url_file>"
    exit 1
fi

echo "Starting batch download..."
echo "Output: $OUTPUT_DIR"
echo "URLs: $(wc -l < $URL_FILE)"

yt-dlp -a "$URL_FILE" \
       -o "$OUTPUT_DIR/%(title)s.%(ext)s" \
       --download-archive "$OUTPUT_DIR/archive.txt"

echo "Batch download complete!"
EOF

chmod +x ~/batch_download.sh

# Step 3: Run batch download
~/batch_download.sh ~/urls.txt

# Expected: All videos downloaded
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Unable to extract video data"

```bash
# Cause: YouTube changed something, yt-dlp outdated

# Solution: Update yt-dlp
pkg upgrade yt-dlp

# Or via pip
pip install -U yt-dlp

# Or direct update
yt-dlp -U
```

### Problem 2: "HTTP Error 403: Forbidden"

```bash
# Cause: YouTube blocking the request

# Solution 1: Update yt-dlp (most common fix)
pkg upgrade yt-dlp

# Solution 2: Use different user agent
yt-dlp --user-agent "Mozilla/5.0" "URL"

# Solution 3: Add delay between requests
yt-dlp --sleep-requests 2 "URL"

# Solution 4: Use cookies
yt-dlp --cookies-from-browser chrome "URL"
```

### Problem 3: "ffmpeg not found" during merge

```bash
# Cause: FFmpeg not installed

# Solution: Install FFmpeg
pkg install ffmpeg -y

# Verify installation
ffmpeg -version
```

### Problem 4: Slow download speed

```bash
# Cause: Server throttling or slow connection

# Solution 1: Use concurrent fragments
yt-dlp --concurrent-fragments 4 "URL"

# Solution 2: Use external downloader
pkg install aria2
yt-dlp --external-downloader aria2c "URL"

# Solution 3: Lower quality to save time
yt-dlp -f "bestvideo[height<=480]+bestaudio" "URL"
```

### Problem 5: Age-restricted video not downloading

```bash
# Cause: Age verification required

# Solution: Use browser cookies
yt-dlp --cookies-from-browser chrome "URL"

# Or export cookies manually:
# 1. Install browser extension to export cookies
# 2. Save as cookies.txt
# 3. Run: yt-dlp --cookies cookies.txt "URL"
```

### Problem 6: "Video unavailable" error

```bash
# Cause: Video private, deleted, or region-blocked

# Solution 1: Use proxy/VPN for region restriction
yt-dlp --proxy "http://proxy:port" "URL"

# Solution 2: Verify video exists
yt-dlp --skip-download "URL"  # Check video info

# Solution 3: Check if video is private
# Private videos cannot be downloaded without authentication
```

### Problem 7: Playlist not downloading completely

```bash
# Cause: Some videos unavailable or restricted

# Solution 1: Ignore errors and continue
yt-dlp --ignore-errors "PLAYLIST_URL"

# Solution 2: Download available only
yt-dlp --ignore-errors --no-abort-on-error "PLAYLIST_URL"

# Solution 3: Use archive to track progress
yt-dlp --download-archive archive.txt --ignore-errors "PLAYLIST_URL"
```

### Problem 8: Storage permission denied

```bash
# Cause: Termux storage not set up

# Solution: Grant storage permission
termux-setup-storage

# Press "Allow" on the popup

# Verify access
ls ~/storage/downloads
```

### Problem 9: Subtitles not downloading

```bash
# Cause: No subtitles available or wrong language code

# Solution 1: List available subtitles
yt-dlp --list-subs "URL"

# Solution 2: Use auto-generated subtitles
yt-dlp --write-auto-subs "URL"

# Solution 3: Try different language codes
yt-dlp --write-subs --sub-lang en "URL"  # English
yt-dlp --write-subs --sub-lang hi "URL"  # Hindi
```

### Problem 10: "File name too long"

```bash
# Cause: Video title very long

# Solution: Use shorter output template
yt-dlp -o "%(id)s.%(ext)s" "URL"

# Or truncate title
yt-dlp -o "%(title).50s.%(ext)s" "URL"
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📥 YT-DLP                        │
│   YouTube Downloader               │
│   for Termux                       │
│                                    │
│   ✓ 720p • 1080p • 4K              │
│   ✓ MP3 Audio Extract              │
│   ✓ Playlist Download              │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Command Focus**
```
┌────────────────────────────────────┐
│  $ yt-dlp "URL"                    │
│  [████████████] 100%               │
│                                    │
│  🎬 VIDEO DOWNLOADING...           │
│                                    │
│  Chapter 39 | yt-dlp Guide         │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  ⬇️ DOWNLOAD YOUTUBE VIDEOS        │
│     IN TERMUX!                     │
│                                    │
│  🎥 HD Quality                     │
│  🎵 Audio Extract                  │
│  📋 Playlist Support               │
│  📝 Subtitles                      │
│                                    │
│  NO ADS • FREE • FAST              │
│  Chapter 39 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📥 Termux Full Course - Chapter 39: YouTube Downloaders | yt-dlp Complete Guide

🔥 In this video you'll learn:
• yt-dlp installation in Termux
• Basic and advanced video download
• Quality selection (720p, 1080p, 4K)
• Audio extraction as MP3
• Playlist download techniques
• Subtitle download and embed
• Proxy and cookies configuration
• Batch downloading automation
• Custom download script creation

⏱️ Timestamps:
0:00 - Introduction
0:45 - yt-dlp Introduction
3:30 - Installation Guide
6:30 - Basic Video Download
9:00 - Quality Selection
11:30 - Audio-Only Download
13:30 - Playlist Download
15:30 - Subtitle Download
17:00 - Advanced Features
19:00 - Automation Script
21:00 - Summary

📝 Commands from this video:

# Installation
pkg install yt-dlp ffmpeg -y

# Basic download
yt-dlp "URL"

# List formats
yt-dlp -F "URL"

# Download 720p
yt-dlp -f "bestvideo[height<=720]+bestaudio" "URL"

# Audio extraction
yt-dlp -x --audio-format mp3 "URL"

# Playlist download
yt-dlp --playlist-items 1-10 "PLAYLIST_URL"

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #yt-dlp #YouTubeDownloader #TermuxTutorial #T3rmuxk1ng #TermuxCourse #LinuxOnAndroid

---
⚠️ Disclaimer: This video is for educational purposes. Download only content you have permission to download. Respect copyright laws.
```

### Tags List

```
yt-dlp, youtube downloader, termux youtube download, termux yt-dlp,
youtube-dl, termux download video, termux mp3 download,
youtube to mp3 termux, termux playlist download, yt-dlp commands,
termux tutorial, termux course, t3rmuxk1ng, android terminal,
linux on android, termux hindi, youtube video download,
audio extract youtube, termux ffmpeg, termux utilities
```

### Hashtags

```
#Termux #yt-dlp #YouTubeDownloader #TermuxTutorial #T3rmuxk1ng 
#TermuxCourse #LinuxOnAndroid #AndroidTerminal #YouTubeToMP3 
#TermuxUtilities #DownloadYouTube #TermuxHindi
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| yt-dlp GitHub | https://github.com/yt-dlp/yt-dlp |
| yt-dlp Documentation | https://github.com/yt-dlp/yt-dlp#readme |
| Supported Sites | https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md |
| Format Selection | https://github.com/yt-dlp/yt-dlp#format-selection |

### Related Tools

| Tool | Purpose |
|------|---------|
| FFmpeg | Video/audio processing |
| aria2 | Alternative downloader |
| jq | JSON processing (for info) |

### Quick Reference Card

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YT-DLP QUICK REFERENCE                                │
├─────────────────────────────────────────────────────────────────────────┤
│ INSTALLATION                                                             │
│   pkg install yt-dlp ffmpeg -y                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ BASIC DOWNLOADS                                                          │
│   yt-dlp "URL"                    # Basic download                      │
│   yt-dlp -F "URL"                 # List formats                        │
│   yt-dlp -f 22 "URL"              # Specific format                     │
├─────────────────────────────────────────────────────────────────────────┤
│ QUALITY SELECTION                                                        │
│   -f best                        # Best quality                         │
│   -f "best[height<=720]"         # Max 720p                             │
│   -f "bestvideo+bestaudio"       # Separate video+audio                 │
├─────────────────────────────────────────────────────────────────────────┤
│ AUDIO                                                                    │
│   -x --audio-format mp3          # Extract MP3                          │
│   --audio-quality 0              # Best audio quality                   │
│   --embed-thumbnail              # Add thumbnail                        │
├─────────────────────────────────────────────────────────────────────────┤
│ PLAYLIST                                                                 │
│   --playlist-items 1-10          # Download range                       │
│   --playlist-reverse             # Reverse order                        │
│   --download-archive file.txt    # Track downloads                      │
├─────────────────────────────────────────────────────────────────────────┤
│ OUTPUT                                                                   │
│   -o "%(title)s.%(ext)s"         # Custom filename                      │
│   -o "~/downloads/%(title)s"     # Custom path                          │
├─────────────────────────────────────────────────────────────────────────┤
│ ADVANCED                                                                 │
│   --limit-rate 1M                # Speed limit                          │
│   --proxy "http://host:port"     # Use proxy                            │
│   --cookies cookies.txt          # Use cookies                          │
│   --write-subs --sub-lang en     # Download subtitles                   │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 40, verify:

- [ ] yt-dlp installed successfully (`yt-dlp --version`)
- [ ] FFmpeg installed successfully (`ffmpeg -version`)
- [ ] Basic video download works
- [ ] Format listing works (`yt-dlp -F`)
- [ ] Quality selection works
- [ ] Audio extraction works (MP3)
- [ ] Playlist download works
- [ ] Subtitle download works
- [ ] Custom output path works
- [ ] Download script created and tested

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 40: File Compression & Archives**

- ZIP file creation and extraction
- TAR archives (tar, tar.gz, tar.bz2)
- 7z compression with password
- Encryption and security
- Batch compression
- Archive automation scripts

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 💡 PRO TIPS BOX (10 Advanced Tips)

> 💡 **Pro Tip #1:** Use `yt-dlp --config-location` to maintain multiple configurations for different download scenarios (music, videos, podcasts).

> 💡 **Pro Tip #2:** Create an alias `alias yt='yt-dlp -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]"'` for quick mobile-optimized downloads.

> 💡 **Pro Tip #3:** Use `--download-archive` to avoid re-downloading videos. It keeps track of all downloaded videos in a text file.

> 💡 **Pro Tip #4:** For age-restricted videos, export cookies from your browser using extensions like "Get cookies.txt" and use `--cookies cookies.txt`.

> 💡 **Pro Tip #5:** Download entire YouTube channels with metadata preservation: `yt-dlp -o "%(uploader)s/%(upload_date)s-%(title)s.%(ext)s" --write-thumbnail --add-metadata "CHANNEL_URL"`

> 💡 **Pro Tip #6:** Use `--sponsorblock-remove all` to automatically skip sponsored segments in YouTube videos!

> 💡 **Pro Tip #7:** For unstable connections, use `--retries 10 --fragment-retries 10 --skip-unavailable-fragments` to handle interruptions gracefully.

> 💡 **Pro Tip #8:** Download only new videos from a playlist: `yt-dlp --download-archive archive.txt --playlist-end 10 "PLAYLIST_URL"` (updates archive as it downloads).

> 💡 **Pro Tip #9:** Use `yt-dlp --simulate "URL"` to preview what would be downloaded without actually downloading - great for checking formats and file sizes.

> 💡 **Pro Tip #10:** Create a batch file with URLs and use `yt-dlp -a urls.txt --batch-file` for unattended downloads overnight.

---

## 🔥 REAL WORLD USE CASES

### Use Case 1: Automated Daily Music Download

```bash
#!/bin/bash
# Daily Music Downloader Script
# Add to cron: 0 6 * * * /path/to/daily-music.sh

PLAYLIST="YOUR_FAVORITE_PLAYLIST_URL"
MUSIC_DIR="/sdcard/Music/Daily"
ARCHIVE="/sdcard/Music/archive.txt"

mkdir -p "$MUSIC_DIR"

yt-dlp --download-archive "$ARCHIVE" \
       -x --audio-format mp3 --audio-quality 0 \
       --embed-thumbnail --add-metadata \
       -o "$MUSIC_DIR/%(title)s.%(ext)s" \
       "$PLAYLIST"

# Send notification
termux-notification --title "Music Download" \
    --content "Daily music download complete!"
```

### Use Case 2: Video Backup Script

```bash
#!/bin/bash
# Backup Important Videos with Metadata

BACKUP_DIR="/sdcard/VideoBackup"
VIDEO_URL="$1"

mkdir -p "$BACKUP_DIR"

yt-dlp --write-description \
       --write-info-json \
       --write-thumbnail \
       --write-subs \
       --add-metadata \
       -o "$BACKUP_DIR/%(upload_date)s-%(title)s/%(title)s.%(ext)s" \
       "$VIDEO_URL"

echo "Backup saved to: $BACKUP_DIR"
```

### Use Case 3: Podcast Auto-Downloader

```bash
#!/bin/bash
# Podcast Auto-Downloader - Run weekly via cron

PODCAST_URL="YOUR_PODCAST_CHANNEL"
PODCAST_DIR="/sdcard/Podcasts"
ARCHIVE="$PODCAST_DIR/podcast_archive.txt"

mkdir -p "$PODCAST_DIR"

# Download last 5 episodes
yt-dlp --download-archive "$ARCHIVE" \
       --playlist-end 5 \
       -x --audio-format m4a --audio-quality 0 \
       --add-metadata \
       -o "$PODCAST_DIR/%(upload_date)s-%(title)s.%(ext)s" \
       "$PODCAST_URL"
```

### Use Case 4: Educational Content Downloader

```bash
#!/bin/bash
# Download course playlist with organization

PLAYLIST_URL="$1"
COURSE_DIR="/sdcard/Courses"

yt-dlp --write-subs --sub-lang en \
       --embed-subs \
       --write-description \
       -o "$COURSE_DIR/%(playlist_title)s/%(playlist_index)02d-%(title)s.%(ext)s" \
       "$PLAYLIST_URL"
```

### Productivity Hacks

| Hack | Command | Benefit |
|------|---------|---------|
| Quick MP3 | `yt-dlp -x --audio-format mp3 "URL"` | One command for audio |
| Mobile 720p | `yt-dlp -f "best[height<=720][ext=mp4]" "URL"` | Optimized for phone |
| Data Saver | `yt-dlp -f worst --limit-rate 500K "URL"` | Minimal data usage |
| Archive Mode | `yt-dlp --download-archive archive.txt "URL"` | Never re-download |
| Batch Queue | `echo "URL" >> queue.txt && yt-dlp -a queue.txt` | Queue downloads |

### Daily Automation Ideas

1. **Morning Podcast Download** - Auto-download new podcast episodes at 6 AM
2. **Weekly Playlist Sync** - Keep offline copies of favorite playlists
3. **Channel Monitor** - Download new videos from subscribed channels
4. **Study Material Backup** - Download educational videos with subtitles for offline study
5. **Music Library Builder** - Convert favorite videos to organized MP3 library

---

## ⚡ QUICK REFERENCE CARD

### Essential yt-dlp Commands

| Task | Command |
|------|---------|
| Basic Download | `yt-dlp "URL"` |
| List Formats | `yt-dlp -F "URL"` |
| Download 720p | `yt-dlp -f "best[height<=720]" "URL"` |
| Download 1080p | `yt-dlp -f "best[height<=1080]" "URL"` |
| Extract MP3 | `yt-dlp -x --audio-format mp3 "URL"` |
| Extract M4A | `yt-dlp -x --audio-format m4a "URL"` |
| Download Subtitles | `yt-dlp --write-subs --sub-lang en "URL"` |
| Playlist Range | `yt-dlp --playlist-items 1-10 "URL"` |
| Speed Limit | `yt-dlp --limit-rate 1M "URL"` |
| Custom Filename | `yt-dlp -o "%(title)s.%(ext)s" "URL"` |
| Batch Download | `yt-dlp -a urls.txt` |
| With Metadata | `yt-dlp --add-metadata --embed-thumbnail "URL"` |
| Skip SponsorBlock | `yt-dlp --sponsorblock-remove all "URL"` |
| Use Proxy | `yt-dlp --proxy "http://proxy:port" "URL"` |
| Update yt-dlp | `pip install -U yt-dlp` |

### Quality Presets

| Quality | Command |
|---------|---------|
| 360p (Small) | `-f "best[height<=360]"` |
| 480p (Medium) | `-f "best[height<=480]"` |
| 720p (HD) | `-f "bestvideo[height<=720]+bestaudio"` |
| 1080p (Full HD) | `-f "bestvideo[height<=1080]+bestaudio"` |
| 4K (Ultra HD) | `-f "bestvideo[height<=2160]+bestaudio"` |
| Audio Only | `-x --audio-format mp3` |

---

## 🏆 BONUS: POWER USER TIPS

### Advanced Configuration File

```bash
# Create config directory
mkdir -p ~/.config/yt-dlp

# Create main config
cat > ~/.config/yt-dlp/config << 'EOF'
# Default output location
-o ~/storage/downloads/%(title)s.%(ext)s

# Always embed thumbnail
--embed-thumbnail

# Add metadata
--add-metadata

# Prefer MP4 format
--merge-output-format mp4

# Continue interrupted downloads
--continue

# Retry on errors
--retries 3
EOF

# Create music-specific config
cat > ~/.config/yt-dlp/music.conf << 'EOF'
# Audio-only downloads
-x
--audio-format mp3
--audio-quality 0
--embed-thumbnail
--add-metadata
-o ~/storage/music/%(title)s.%(ext)s
EOF

# Use: yt-dlp --config-location ~/.config/yt-dlp/music.conf "URL"
```

### Advanced Automation Scripts

```bash
#!/bin/bash
# smart-downloader.sh - Intelligent download script

URL="$1"
MODE="${2:-auto}"

analyze_and_download() {
    local url="$1"
    
    # Check if it's a playlist
    if [[ "$url" == *"playlist"* ]] || [[ "$url" == *"list="* ]]; then
        echo "Detected: Playlist"
        yt-dlp --playlist-items 1-10 \
               -o "~/storage/downloads/playlist/%(playlist_index)s-%(title)s.%(ext)s" \
               "$url"
    
    # Check if it's music (by URL pattern)
    elif [[ "$url" == *"music.youtube.com"* ]]; then
        echo "Detected: YouTube Music"
        yt-dlp -x --audio-format m4a \
               --embed-thumbnail --add-metadata \
               -o "~/storage/music/%(title)s.%(ext)s" "$url"
    
    # Default: Smart download
    else
        # Get video duration
        duration=$(yt-dlp --get-duration "$url" 2>/dev/null)
        
        # If longer than 30 mins, probably a long video - use 720p
        if [[ "$duration" == *":"*":"* ]]; then
            echo "Detected: Long video - optimizing for size"
            yt-dlp -f "best[height<=720]" "$url"
        else
            echo "Detected: Short video - best quality"
            yt-dlp "$url"
        fi
    fi
}

case "$MODE" in
    music)
        yt-dlp -x --audio-format mp3 --audio-quality 0 \
               --embed-thumbnail --add-metadata "$URL"
        ;;
    video)
        yt-dlp -f "bestvideo[height<=1080]+bestaudio" "$URL"
        ;;
    auto)
        analyze_and_download "$URL"
        ;;
    *)
        echo "Usage: $0 <URL> [music|video|auto]"
        ;;
esac
```

### Cron Job Examples

```bash
# Edit crontab
crontab -e

# Add these lines:

# Daily music download at 6 AM
0 6 * * * /data/data/com.termux/files/home/scripts/daily-music.sh

# Weekly playlist sync on Sunday at 8 AM
0 8 * * 0 /data/data/com.termux/files/home/scripts/playlist-sync.sh

# Monthly channel backup on 1st at midnight
0 0 1 * * /data/data/com.termux/files/home/scripts/channel-backup.sh
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### Key Takeaways

- ✅ **yt-dlp Installation** - Install via `pkg install yt-dlp ffmpeg` for full functionality
- ✅ **Basic Downloads** - Simple command `yt-dlp "URL"` downloads best quality automatically
- ✅ **Quality Control** - Use `-F` to list formats, `-f` to select specific quality
- ✅ **Audio Extraction** - Use `-x --audio-format mp3` for music downloads with metadata
- ✅ **Playlist Management** - Control with `--playlist-items`, track with `--download-archive`
- ✅ **Subtitles** - Download and embed subtitles in multiple languages
- ✅ **Advanced Features** - Proxy support, cookies, batch downloads, speed limiting
- ✅ **Automation** - Create scripts and cron jobs for scheduled downloads
- ✅ **Configuration** - Use config files for consistent download settings
- ✅ **SponsorBlock** - Skip sponsored segments automatically

### Skills Acquired

| Skill | Level |
|-------|-------|
| Basic Downloads | ⭐⭐⭐⭐⭐ |
| Quality Selection | ⭐⭐⭐⭐ |
| Audio Extraction | ⭐⭐⭐⭐ |
| Playlist Management | ⭐⭐⭐⭐ |
| Script Automation | ⭐⭐⭐ |
| Advanced Configuration | ⭐⭐⭐ |

---

## 🔧 AUTOMATION SCRIPTS

### Ready-to-Use Scripts

**1. Quick Download Script:**
```bash
#!/bin/bash
# Save as: ~/scripts/yt-quick.sh
[ -z "$1" ] && echo "Usage: $0 <URL>" && exit 1
yt-dlp -o "~/storage/downloads/%(title)s.%(ext)s" "$1"
```

**2. Music Download Script:**
```bash
#!/bin/bash
# Save as: ~/scripts/yt-music.sh
[ -z "$1" ] && echo "Usage: $0 <URL>" && exit 1
yt-dlp -x --audio-format mp3 --audio-quality 0 \
       --embed-thumbnail --add-metadata \
       -o "~/storage/music/%(title)s.%(ext)s" "$1"
```

**3. Video Compress Script:**
```bash
#!/bin/bash
# Save as: ~/scripts/yt-compress.sh
[ -z "$1" ] && echo "Usage: $0 <URL>" && exit 1
yt-dlp -f "worst[height>=360]" --recode-video mp4 \
       -o "~/storage/downloads/compressed_%(title)s.%(ext)s" "$1"
```

### Cron Job Templates

```bash
# Add to crontab with: crontab -e

# Every day at 6 AM - Download new music
0 6 * * * yt-dlp --download-archive ~/music_archive.txt -x --audio-format mp3 "PLAYLIST_URL"

# Every Sunday - Backup important channel
0 10 * * 0 yt-dlp --download-archive ~/channel_archive.txt "CHANNEL_URL"

# Every hour - Check for new videos (first 5 only)
0 * * * * yt-dlp --download-archive ~/watch_archive.txt --playlist-end 5 "PLAYLIST_URL"
```

---

## 🚀 WORKFLOW OPTIMIZATION

### Speed Up Daily Tasks

| Task | Slow Way | Fast Way |
|------|----------|----------|
| Download video | Open browser → Copy URL → Use app | `yt-dlp "URL"` |
| Extract audio | Download → Convert separately | `yt-dlp -x "URL"` |
| Multiple videos | Download one by one | `yt-dlp -a urls.txt` |
| Same playlist updates | Re-download everything | `--download-archive` |
| Consistent quality | Type format each time | Config file |

### Efficiency Tips

1. **Use Aliases** - Add to `.bashrc`:
   ```bash
   alias yt='yt-dlp'
   alias yta='yt-dlp -x --audio-format mp3'
   alias ytv='yt-dlp -f "best[height<=720]"'
   ```

2. **Use Config Files** - Set defaults once, use everywhere

3. **Use Archive Files** - Never re-download the same video

4. **Use Tab Completion** - Install `bash-completion` for yt-dlp

5. **Use tmux** - Run long downloads in background sessions

---

## 📊 COMPARISON TABLES

### Download Tools Comparison

| Tool | Sites | Speed | Updates | Termux |
|------|-------|-------|---------|--------|
| yt-dlp | 1000+ | ⭐⭐⭐⭐⭐ | Active | ✅ |
| youtube-dl | ~500 | ⭐⭐⭐ | Slow | ✅ |
| youtube-dl-android | Limited | ⭐⭐⭐ | Slow | ❌ |
| NewPipe | YouTube | ⭐⭐⭐⭐ | Active | ❌ |
| YMusic | YouTube | ⭐⭐⭐ | Active | ❌ |

### Audio Format Comparison

| Format | Quality | Size | Compatibility |
|--------|---------|------|---------------|
| MP3 | Good | Small | Universal |
| M4A/AAC | Better | Medium | Apple/Android |
| OPUS | Best | Small | Modern players |
| FLAC | Lossless | Large | Audiophiles |
| WAV | Lossless | Huge | Editing |

### Quality vs Size Guide

| Resolution | File Size (5 min) | Best For |
|------------|-------------------|----------|
| 360p | ~25 MB | Data saving |
| 480p | ~50 MB | Mobile viewing |
| 720p | ~100 MB | Good quality |
| 1080p | ~200 MB | Best quality |
| 4K | ~500 MB | Large screens |

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relationship |
|---------|-------|--------------|
| Ch40 | File Compression | Compress downloaded videos |
| Ch41 | Image/Media Tools | Process thumbnails, convert formats |
| Ch42 | PDF Tools | Download and organize PDF tutorials |
| Ch43 | Task Automation | Schedule downloads with cron |
| Ch44 | Termux Widgets | Create home screen download shortcuts |
| Ch45 | SSH Server | Remote download management |
| Ch46 | Web Servers | Stream downloaded content |

---

## 🎮 INTERACTIVE QUIZ

### Test Your Knowledge (10 Questions)

**Q1:** Which command lists all available video formats?
- A) `yt-dlp -l "URL"`
- B) `yt-dlp -F "URL"`
- C) `yt-dlp --formats "URL"`
- D) `yt-dlp -f "URL"`

**Q2:** What does the `-x` flag do?
- A) Extract subtitles
- B) Extract audio only
- C) Extract metadata
- D) Extract video only

**Q3:** How do you download only the first 5 videos of a playlist?
- A) `yt-dlp --first 5 "URL"`
- B) `yt-dlp --playlist-items -5 "URL"`
- C) `yt-dlp --playlist-start 1 --playlist-end 5 "URL"`
- D) `yt-dlp -n 5 "URL"`

**Q4:** Which audio quality setting gives the best quality?
- A) `--audio-quality 9`
- B) `--audio-quality 5`
- C) `--audio-quality 0`
- D) `--audio-quality best`

**Q5:** What is the correct syntax to download 720p video?
- A) `yt-dlp -f 720 "URL"`
- B) `yt-dlp -f "best[height=720]" "URL"`
- C) `yt-dlp --quality 720 "URL"`
- D) `yt-dlp -r 720 "URL"`

**Q6:** How do you limit download speed to 500KB/s?
- A) `yt-dlp --speed-limit 500K "URL"`
- B) `yt-dlp --limit-rate 500K "URL"`
- C) `yt-dlp --rate 500K "URL"`
- D) `yt-dlp --bandwidth 500K "URL"`

**Q7:** Which flag embeds thumbnails in audio files?
- A) `--add-thumbnail`
- B) `--embed-thumbnail`
- C) `--thumbnail`
- D) `--include-thumbnail`

**Q8:** How do you download subtitles in Hindi?
- A) `yt-dlp --subs hi "URL"`
- B) `yt-dlp --write-subs --sub-lang hi "URL"`
- C) `yt-dlp --hindi-subs "URL"`
- D) `yt-dlp --download-subs hi "URL"`

**Q9:** What does `--download-archive` do?
- A) Creates a ZIP of downloads
- B) Tracks downloaded videos to avoid duplicates
- C) Downloads from archive.org
- D) Archives old downloads

**Q10:** Which command updates yt-dlp installed via pip?
- A) `yt-dlp --update`
- B) `pip install -U yt-dlp`
- C) `pkg upgrade yt-dlp`
- D) `yt-dlp -U`

**Answers:** 1-B, 2-B, 3-B, 4-C, 5-B, 6-B, 7-B, 8-B, 9-B, 10-B

---

## 🎯 AUTOMATION CHALLENGES

### Challenge 1: Create a Music Downloader Widget
**Objective:** Create a Termux:Widget shortcut that downloads audio from a URL in clipboard.
**Hint:** Use `termux-clipboard-get` to get URL.

### Challenge 2: Build a Playlist Monitor
**Objective:** Create a script that checks for new videos in a playlist weekly and downloads only new ones.
**Hint:** Use `--download-archive` and cron jobs.

### Challenge 3: Smart Quality Selector
**Objective:** Create a script that automatically selects quality based on available storage.
**Hint:** Check `df -h` for available space before downloading.

### Challenge 4: Batch Converter
**Objective:** Convert all downloaded videos to audio format automatically.
**Hint:** Use `find` with `ffmpeg` for conversion.

### Challenge 5: Download Scheduler
**Objective:** Schedule downloads during off-peak hours (night) to save data.
**Hint:** Use cron with specific time ranges.

---

## 📝 SCRIPT WRITING EXERCISES

### Exercise A: Basic Script
Create a script that accepts a URL and downloads as MP3:
```bash
#!/bin/bash
# Your code here
```

### Exercise B: Interactive Menu
Create an interactive menu script with options:
1. Download Video
2. Download Audio
3. List Formats
4. Exit

### Exercise C: Batch Processor
Create a script that processes a file of URLs and downloads each with progress logging.

---

**End of Chapter 39 Upgrade**
