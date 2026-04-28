# Chapter 54: Project 4 - YouTube Downloader Bot

> **Module:** 9 - Projects  
> **Chapter:** 54 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed project architecture |
| yt-dlp Integration | Complete yt-dlp usage |
| Features Implementation | All features with code |
| Source Code | Complete production-ready bot |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common issues and fixes |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 54
Title: YouTube Downloader Bot | Complete Python Project | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum banayenge ek bahut hi useful project - YouTube Downloader Bot!

Haan, aapne sahi suna! Apne Android phone se, Termux mein, ek aisa bot 
banayenge jo YouTube videos download kar sake, audio extract kar sake, 
playlists download kar sake - sab kuch automatically!

Ye project Module 9 ka 4th project hai. Isse hum seekhenge:
- yt-dlp library ka use karna
- Python mein menu-driven applications banana
- Progress tracking karna
- File handling aur batch processing
- Notifications bhejna Termux API se

To bina time waste kiye, chaliye shuru karte hain!

Play button dabaiye, video like karein, channel subscribe karein!

---

[SECTION 1: PROJECT OVERVIEW - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle, samajhte hain ye project kya karega.

YouTube Downloader Bot ek Python-based tool hai jo aapko YouTube se 
content download karne ki power deta hai - directly Termux se.

┌─────────────────────────────────────────────────────────────────────────┐
│                    YOUTUBE DOWNLOADER BOT FEATURES                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  🎬 VIDEO DOWNLOAD                                                       │
│     • Single video download                                              │
│     • Quality selection (360p, 480p, 720p, 1080p, 4K)                  │
│     • Format selection (MP4, WebM, etc.)                                │
│     • Automatic format conversion                                        │
│                                                                          │
│  🎵 AUDIO EXTRACTION                                                     │
│     • Extract audio from video                                           │
│     • MP3, M4A, AAC formats                                             │
│     • Metadata embedding                                                 │
│     • Thumbnail embedding                                               │
│                                                                          │
│  📁 PLAYLIST DOWNLOAD                                                    │
│     • Download entire playlists                                         │
│     • Select specific videos from playlist                              │
│     • Progress tracking for each video                                   │
│     • Resume interrupted downloads                                       │
│                                                                          │
│  📊 BATCH DOWNLOAD                                                       │
│     • Download from URL list in file                                    │
│     • Multiple videos at once                                            │
│     • Queue management                                                   │
│                                                                          │
│  📜 DOWNLOAD HISTORY                                                     │
│     • Track all downloads                                               │
│     • View history with details                                         │
│     • Export history to file                                            │
│                                                                          │
│  🔔 NOTIFICATIONS                                                        │
│     • Notification on completion                                        │
│     • Vibration alert                                                   │
│     • Sound notification                                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Real-world use cases:
✓ Offline videos dekhne ke liye
✓ Music download karna (audio extraction)
✓ Tutorial series download karna (playlists)
✓ Multiple videos ek saath download karna (batch)

Sabse important - ye sab FREE hai, koi premium subscription nahi!

---

[SECTION 2: TOOLS REQUIRED - 4:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab baat aati hai ki kis cheez ki zarurat hogi.

Prerequisites:

1. Termux (obviously!) - Updated version from F-Droid
2. Python 3 - Already installed hona chahiye
3. ffmpeg - Video/audio processing ke liye
4. yt-dlp - Main downloading library
5. Termux:API app - Notifications ke liye

Chaliye check karte hain ki sab installed hai ya nahi:

    python --version

Agar Python nahi hai:

    pkg install python -y

ffmpeg check:

    ffmpeg -version

Agar nahi hai:

    pkg install ffmpeg -y

yt-dlp install karna:

    pip install yt-dlp

Termux:API check:

    termux-notification --title "Test"

Agar ye command kaam karti hai to Termux:API installed hai.
Agar error aaye to F-Droid se Termux:API app install karein.

---

[SECTION 3: YT-DLP BASICS - 6:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab samajhte hain yt-dlp kya hai aur kaise kaam karta hai.

yt-dlp ek powerful command-line tool hai YouTube videos download karne 
ke liye. Ye youtube-dl ka improved version hai with more features.

Basic yt-dlp commands:

[SCREEN: Terminal]

Simple video download:

    yt-dlp "https://www.youtube.com/watch?v=VIDEO_ID"

Best quality download:

    yt-dlp -f "best" "URL"

Specific quality:

    yt-dlp -f "best[height<=720]" "URL"

Audio only extract:

    yt-dlp -x --audio-format mp3 "URL"

Playlist download:

    yt-dlp "PLAYLIST_URL"

Video info dekhna:

    yt-dlp --print "%(title)s %(duration)s" "URL"

Available formats list:

    yt-dlp -F "URL"

Output filename customize:

    yt-dlp -o "~/storage/downloads/%(title)s.%(ext)s" "URL"

Ye commands directly use kar sakte ho, lekin hum Python script 
banayenge jo in sab ko easy menu-driven interface dega.

---

[SECTION 4: PROJECT STRUCTURE - 10:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab project ka structure design karte hain.

Directory structure:

    ~/youtube-bot/
    ├── yt_bot.py           # Main bot script
    ├── config.py           # Configuration settings
    ├── history.json        # Download history
    ├── batch.txt           # Batch download URLs
    └── downloads/          # Downloaded files

Main components:

┌─────────────────────────────────────────────────────────────────────────┐
│                    PROJECT ARCHITECTURE                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────┐                                                   │
│   │   MAIN MENU     │                                                   │
│   │   (User Input)  │                                                   │
│   └────────┬────────┘                                                   │
│            │                                                             │
│     ┌──────┴──────┬─────────────┬──────────────┬──────────┐            │
│     ▼             ▼             ▼              ▼          ▼            │
│ ┌───────┐   ┌───────┐   ┌───────────┐   ┌─────────┐  ┌────────┐       │
│ │Video  │   │Audio  │   │ Playlist  │   │ Batch   │  │History │       │
│ │Download│  │Extract│   │ Download  │   │Download │  │ View   │       │
│ └───┬───┘   └───┬───┘   └─────┬─────┘   └────┬────┘  └───┬────┘       │
│     │           │             │              │            │            │
│     └───────────┴─────────────┴──────────────┴────────────┘            │
│                              │                                          │
│                              ▼                                          │
│                    ┌─────────────────┐                                  │
│                    │    yt-dlp       │                                  │
│                    │    Engine       │                                  │
│                    └────────┬────────┘                                  │
│                             │                                           │
│                    ┌────────┴────────┐                                  │
│                    ▼                 ▼                                  │
│             ┌───────────┐      ┌───────────┐                            │
│             │  History  │      │Notificaton│                            │
│             │   Log     │      │  System   │                            │
│             └───────────┘      └───────────┘                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Key functions:

1. download_video()      - Single video download
2. extract_audio()       - Audio extraction
3. download_playlist()   - Playlist download
4. batch_download()      - Download from file
5. show_history()        - View download history
6. send_notification()   - Termux notification
7. progress_hook()       - Download progress tracking

---

[SECTION 5: CODE EXPLANATION - 12:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab main code ko explain karta hoon part by part.

[Part 1: Imports and Configuration]

Sabse pehle required libraries import karte hain:

    import yt_dlp
    import json
    import os
    from datetime import datetime

Configuration settings:

    DOWNLOAD_PATH = os.path.expanduser("~/storage/downloads/youtube-bot")
    HISTORY_FILE = "history.json"

[Part 2: Progress Hook]

Progress hook download progress track karta hai:

    def progress_hook(d):
        if d['status'] == 'downloading':
            percent = d.get('_percent_str', 'N/A')
            speed = d.get('_speed_str', 'N/A')
            print(f"\rProgress: {percent} | Speed: {speed}", end='')
        elif d['status'] == 'finished':
            print("\n✅ Download Complete!")

[Part 3: Video Download Function]

Ye main download function hai:

    def download_video(url, quality='best'):
        ydl_opts = {
            'format': f'best[height<={quality}]' if quality != 'best' else 'best',
            'outtmpl': f'{DOWNLOAD_PATH}/%(title)s.%(ext)s',
            'progress_hooks': [progress_hook],
            'quiet': True,
            'no_warnings': True,
        }
        
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            ydl.download([url])

[Part 4: Audio Extraction]

Audio extraction separate function mein:

    def extract_audio(url, format='mp3'):
        ydl_opts = {
            'format': 'bestaudio/best',
            'outtmpl': f'{DOWNLOAD_PATH}/%(title)s.%(ext)s',
            'postprocessors': [{
                'key': 'FFmpegExtractAudio',
                'preferredcodec': format,
            }],
            'progress_hooks': [progress_hook],
        }

[Part 5: Playlist Download]

Playlist download with numbering:

    def download_playlist(url):
        ydl_opts = {
            'format': 'best',
            'outtmpl': f'{DOWNLOAD_PATH}/%(playlist_index)02d-%(title)s.%(ext)s',
            'progress_hooks': [progress_hook],
        }

[Part 6: Notification System]

Termux API se notification:

    def send_notification(title, message):
        os.system(f'termux-notification --title "{title}" --content "{message}"')

[Part 7: Main Menu]

Menu-driven interface:

    def main():
        while True:
            print_banner()
            print("1. 🎬 Download Video")
            print("2. 🎵 Extract Audio (MP3)")
            print("3. 📁 Download Playlist")
            print("4. 📊 Batch Download")
            print("5. 📜 View History")
            print("6. ⚙️  Settings")
            print("0. 🚪 Exit")
            
            choice = input("\nEnter choice: ")
            # Handle choices...

Main function mein infinite loop hai jo user input leta hai aur 
appropriate function call karta hai.

---

[SECTION 6: LIVE DEMO - 18:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye live demo dekhte hain!

[SCREEN: Termux terminal]

Step 1: Project directory create karein

    mkdir -p ~/youtube-bot
    cd ~/youtube-bot

Step 2: Bot script run karein

    python yt_bot.py

[SCREEN: Main menu]

    ╔══════════════════════════════════════════════════════════════╗
    ║           🎬 YOUTUBE DOWNLOADER BOT 🎬                       ║
    ║              by T3rmuxk1ng                                   ║
    ╠══════════════════════════════════════════════════════════════╣
    ║  1. 🎬 Download Video                                        ║
    ║  2. 🎵 Extract Audio (MP3)                                   ║
    ║  3. 📁 Download Playlist                                     ║
    ║  4. 📊 Batch Download                                        ║
    ║  5. 📜 View History                                          ║
    ║  6. ⚙️  Settings                                             ║
    ║  0. 🚪 Exit                                                  ║
    ╚══════════════════════════════════════════════════════════════╝

[Demo 1: Video Download]

Option 1 select karein:
- URL paste karein
- Quality select karein (1-5)
- Download start hoga with progress bar
- Notification aayega complete hone par

[Demo 2: Audio Extraction]

Option 2 select karein:
- YouTube URL paste karein
- MP3 format mein audio extract hoga
- Metadata automatically embed hoga

[Demo 3: Playlist Download]

Option 3 select karein:
- Playlist URL paste karein
- Saari videos download hongi with numbering
- Progress each video ke liye dikhega

[Demo 4: Batch Download]

Option 4 select karein:
- batch.txt file mein URLs daalein
- Ek ek karke saari download hongi

[Demo 5: View History]

Option 5 select karein:
- Complete download history dikhegi
- Timestamp, URL, filename sab dikhega

Ye bahut smooth hai! Real-world mein use kar sakte ho.

---

[SECTION 7: ADVANCED FEATURES - 22:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Kuch advanced features bhi add kar sakte ho:

1. Auto Subtitle Download:

    ydl_opts = {
        'writesubtitles': True,
        'subtitleslangs': ['en', 'hi'],
    }

2. Thumbnail Embed:

    ydl_opts = {
        'writethumbnail': True,
        'postprocessors': [{
            'key': 'FFmpegThumbnailsConvertor',
        }],
    }

3. Speed Limitation (for slow internet):

    ydl_opts = {
        'ratelimit': 1000000,  # 1MB/s
    }

4. Proxy Support:

    ydl_opts = {
        'proxy': 'http://proxy:port',
    }

5. Age Restriction Bypass:

    yt-dlp automatically handles age-gated videos.

Ye features optional hain, basic bot ke saath kaafi hai!

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 24:00 to 25:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 54 complete! Let's summarize:

✅ YouTube Downloader Bot kya hai - Complete overview
✅ yt-dlp library - Installation aur basics
✅ Video download with quality selection
✅ Audio extraction - MP3 format mein
✅ Playlist download with progress
✅ Batch download from file
✅ Download history tracking
✅ Termux notifications on completion

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 54 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install python ffmpeg -y    │ Install required packages             │
│ pip install yt-dlp              │ Install yt-dlp library                │
│ python yt_bot.py                │ Run the bot                           │
│ yt-dlp -F "URL"                 │ List available formats                │
│ yt-dlp -x --audio-format mp3    │ Extract audio only                    │
│ termux-notification             │ Send notification                     │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 55 mein hum seekhenge:
- Port Scanner Tool
- Network scanning concepts
- Python socket programming
- Multi-threaded scanning

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 55!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Project Overview

YouTube Downloader Bot is a comprehensive Python-based tool designed for Termux that enables users to download YouTube content through a user-friendly menu-driven interface.

#### Key Features:

| Feature | Description |
|---------|-------------|
| Video Download | Download videos in various qualities (360p to 4K) |
| Audio Extraction | Extract audio in MP3, M4A, AAC formats |
| Playlist Download | Download entire playlists with numbering |
| Quality Selection | Choose video quality before download |
| Progress Display | Real-time download progress with speed |
| Download History | Track all downloads with timestamps |
| Batch Download | Download multiple videos from a file |
| Notifications | Android notifications on completion |

### 2. yt-dlp Integration

yt-dlp is a powerful command-line program to download videos from YouTube and other sites. It's a fork of youtube-dl with additional features and fixes.

#### Installation:

```bash
# Update Termux packages
pkg update && pkg upgrade -y

# Install Python and ffmpeg
pkg install python ffmpeg -y

# Install yt-dlp via pip
pip install yt-dlp

# Verify installation
yt-dlp --version
```

#### yt-dlp Options Reference:

```python
# Common yt-dlp options dictionary
ydl_opts = {
    # Format selection
    'format': 'best',                    # Best quality
    'format': 'best[height<=720]',       # Max 720p
    'format': 'worst',                   # Worst quality
    'format': 'bestaudio/best',          # Audio only
    
    # Output template
    'outtmpl': '%(title)s.%(ext)s',      # Filename pattern
    'outtmpl': '%(playlist_index)02d-%(title)s.%(ext)s',  # Playlist numbering
    
    # Download location
    'paths': {'home': '~/downloads'},    # Download directory
    
    # Progress hooks
    'progress_hooks': [my_hook],         # Progress callback
    
    # Subtitles
    'writesubtitles': True,              # Download subtitles
    'subtitleslangs': ['en', 'hi'],      # Subtitle languages
    
    # Thumbnail
    'writethumbnail': True,              # Download thumbnail
    
    # Metadata
    'writedescription': True,            # Write description to file
    'writeinfojson': True,               # Write metadata JSON
    
    # Post processors
    'postprocessors': [{
        'key': 'FFmpegExtractAudio',
        'preferredcodec': 'mp3',
        'preferredquality': '192',
    }],
    
    # Network options
    'ratelimit': 1000000,                # Limit speed (bytes/sec)
    'retries': 10,                       # Retry count
    'fragment_retries': 10,              # Fragment retry count
    
    # Quiet mode
    'quiet': True,                       # Suppress output
    'no_warnings': True,                 # No warnings
    
    # Overwrite
    'overwrites': True,                  # Overwrite existing files
    'nopart': True,                      # Don't use .part files
}
```

### 3. Project Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YOUTUBE DOWNLOADER BOT ARCHITECTURE                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                        USER INTERFACE LAYER                       │  │
│   │  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌────────┐ │  │
│   │  │  Menu   │  │ Banner  │  │  Input  │  │  Output │  │ Config │ │  │
│   │  │ Display │  │  Show   │  │ Handler │  │ Format  │  │ Manager│ │  │
│   │  └─────────┘  └─────────┘  └─────────┘  └─────────┘  └────────┘ │  │
│   └──────────────────────────────────────────────────────────────────┘  │
│                                   │                                      │
│                                   ▼                                      │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                        CORE FUNCTION LAYER                        │  │
│   │  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────────┐ │  │
│   │  │  Video    │  │  Audio    │  │ Playlist  │  │    Batch      │ │  │
│   │  │ Downloader│  │ Extractor │  │ Downloader│  │  Downloader   │ │  │
│   │  └───────────┘  └───────────┘  └───────────┘  └───────────────┘ │  │
│   └──────────────────────────────────────────────────────────────────┘  │
│                                   │                                      │
│                                   ▼                                      │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                        SUPPORT LAYER                              │  │
│   │  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌────────┐ │  │
│   │  │ Progress│  │ History │  │ Notify  │  │  Error  │  │  File  │ │  │
│   │  │  Hook   │  │ Manager │  │ System  │  │ Handler │  │ Manager│ │  │
│   │  └─────────┘  └─────────┘  └─────────┘  └─────────┘  └────────┘ │  │
│   └──────────────────────────────────────────────────────────────────┘  │
│                                   │                                      │
│                                   ▼                                      │
│   ┌──────────────────────────────────────────────────────────────────┐  │
│   │                        EXTERNAL LIBRARIES                         │  │
│   │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  │  │
│   │  │     yt-dlp      │  │     ffmpeg      │  │  Termux:API     │  │  │
│   │  │  (Download)     │  │  (Processing)   │  │  (Notification) │  │  │
│   │  └─────────────────┘  └─────────────────┘  └─────────────────┘  │  │
│   └──────────────────────────────────────────────────────────────────┘  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. Feature Implementation Details

#### 4.1 Video Download

```python
def download_video(url, quality='best'):
    """
    Download a YouTube video with specified quality.
    
    Args:
        url (str): YouTube video URL
        quality (str): Video quality (360, 480, 720, 1080, best)
    
    Returns:
        bool: True if successful, False otherwise
    """
    quality_map = {
        '360': 'best[height<=360]',
        '480': 'best[height<=480]',
        '720': 'best[height<=720]',
        '1080': 'best[height<=1080]',
        'best': 'bestvideo+bestaudio/best'
    }
    
    ydl_opts = {
        'format': quality_map.get(quality, 'best'),
        'outtmpl': os.path.join(DOWNLOAD_PATH, '%(title)s.%(ext)s'),
        'progress_hooks': [progress_hook],
        'merge_output_format': 'mp4',
        'quiet': True,
        'no_warnings': True,
    }
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            return True, info.get('title', 'Unknown')
    except Exception as e:
        return False, str(e)
```

#### 4.2 Audio Extraction

```python
def extract_audio(url, audio_format='mp3', quality='192'):
    """
    Extract audio from a YouTube video.
    
    Args:
        url (str): YouTube video URL
        audio_format (str): Output format (mp3, m4a, aac, wav)
        quality (str): Audio quality in kbps
    
    Returns:
        bool: True if successful, False otherwise
    """
    ydl_opts = {
        'format': 'bestaudio/best',
        'outtmpl': os.path.join(DOWNLOAD_PATH, '%(title)s.%(ext)s'),
        'postprocessors': [{
            'key': 'FFmpegExtractAudio',
            'preferredcodec': audio_format,
            'preferredquality': quality,
        }],
        'progress_hooks': [progress_hook],
        'quiet': True,
        'no_warnings': True,
    }
    
    # Add thumbnail embedding for MP3
    if audio_format == 'mp3':
        ydl_opts['writethumbnail'] = True
        ydl_opts['postprocessors'].append({
            'key': 'FFmpegThumbnailsConvertor',
        })
        ydl_opts['postprocessors'].append({
            'key': 'FFmpegMetadata',
        })
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            return True, info.get('title', 'Unknown')
    except Exception as e:
        return False, str(e)
```

#### 4.3 Playlist Download

```python
def download_playlist(url, start=1, end=None):
    """
    Download videos from a YouTube playlist.
    
    Args:
        url (str): YouTube playlist URL
        start (int): Start index (1-based)
        end (int): End index (optional)
    
    Returns:
        tuple: (success_count, total_count, errors)
    """
    ydl_opts = {
        'format': 'best[height<=720]/best',
        'outtmpl': os.path.join(DOWNLOAD_PATH, 'playlist/%(playlist_index)02d-%(title)s.%(ext)s'),
        'progress_hooks': [progress_hook],
        'playliststart': start,
        'playlistend': end,
        'quiet': True,
        'no_warnings': True,
        'ignoreerrors': True,  # Continue on errors
    }
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            # Get playlist info first
            info = ydl.extract_info(url, download=False)
            
            if 'entries' not in info:
                return False, "Not a valid playlist URL"
            
            total = len(info['entries'])
            print(f"\n📁 Playlist: {info.get('title', 'Unknown')}")
            print(f"📊 Total videos: {total}")
            
            # Download
            ydl.download([url])
            
            return True, total
    except Exception as e:
        return False, str(e)
```

#### 4.4 Batch Download

```python
def batch_download(file_path):
    """
    Download videos from URLs listed in a file.
    
    Args:
        file_path (str): Path to file containing URLs (one per line)
    
    Returns:
        dict: Download results
    """
    results = {
        'success': [],
        'failed': [],
        'total': 0
    }
    
    try:
        with open(file_path, 'r') as f:
            urls = [line.strip() for line in f if line.strip()]
        
        results['total'] = len(urls)
        
        for i, url in enumerate(urls, 1):
            print(f"\n[{i}/{len(urls)}] Processing: {url[:50]}...")
            
            success, info = download_video(url)
            
            if success:
                results['success'].append(url)
                save_to_history(url, info, 'video')
            else:
                results['failed'].append((url, info))
                print(f"❌ Failed: {info}")
        
        return results
    except FileNotFoundError:
        return {'error': f"File not found: {file_path}"}
    except Exception as e:
        return {'error': str(e)}
```

#### 4.5 Progress Display

```python
def progress_hook(d):
    """
    Progress hook for yt-dlp downloads.
    
    Args:
        d (dict): Progress information dictionary
    """
    if d['status'] == 'downloading':
        # Get progress information
        percent = d.get('_percent_str', 'N/A')
        speed = d.get('_speed_str', 'N/A')
        eta = d.get('_eta_str', 'N/A')
        downloaded = d.get('_total_bytes_str', 'N/A')
        
        # Create progress bar
        try:
            percent_num = float(percent.strip('%'))
            bar_length = 30
            filled = int(bar_length * percent_num / 100)
            bar = '█' * filled + '░' * (bar_length - filled)
            
            print(f"\r[{bar}] {percent} | Speed: {speed} | ETA: {eta}", end='', flush=True)
        except:
            print(f"\rProgress: {percent} | Speed: {speed}", end='', flush=True)
    
    elif d['status'] == 'finished':
        filename = os.path.basename(d.get('filename', 'Unknown'))
        print(f"\n✅ Downloaded: {filename}")
        print("🔄 Processing...")
    
    elif d['status'] == 'error':
        print(f"\n❌ Error: {d.get('error', 'Unknown error')}")
```

#### 4.6 Download History

```python
def save_to_history(url, title, download_type):
    """
    Save download information to history file.
    
    Args:
        url (str): Video URL
        title (str): Video title
        download_type (str): Type of download (video/audio/playlist)
    """
    history_entry = {
        'url': url,
        'title': title,
        'type': download_type,
        'timestamp': datetime.now().strftime('%Y-%m-%d %H:%M:%S'),
        'date': datetime.now().strftime('%Y-%m-%d'),
    }
    
    history = []
    
    # Load existing history
    if os.path.exists(HISTORY_FILE):
        try:
            with open(HISTORY_FILE, 'r') as f:
                history = json.load(f)
        except:
            history = []
    
    # Add new entry
    history.append(history_entry)
    
    # Save history
    with open(HISTORY_FILE, 'w') as f:
        json.dump(history, f, indent=2)


def show_history(limit=20):
    """
    Display download history.
    
    Args:
        limit (int): Maximum number of entries to show
    """
    if not os.path.exists(HISTORY_FILE):
        print("\n📜 No download history found.")
        return
    
    try:
        with open(HISTORY_FILE, 'r') as f:
            history = json.load(f)
        
        if not history:
            print("\n📜 History is empty.")
            return
        
        print(f"\n{'='*70}")
        print(f"📜 DOWNLOAD HISTORY (Last {min(limit, len(history))} entries)")
        print(f"{'='*70}")
        
        for entry in history[-limit:][::-1]:
            print(f"\n📌 {entry['title'][:50]}...")
            print(f"   Type: {entry['type'].upper()}")
            print(f"   Date: {entry['timestamp']}")
            print(f"   URL:  {entry['url'][:60]}...")
        
        print(f"\n{'='*70}")
        print(f"Total downloads: {len(history)}")
        
    except Exception as e:
        print(f"❌ Error reading history: {e}")
```

#### 4.7 Notification on Completion

```python
def send_notification(title, message, sound=True, vibration=True):
    """
    Send Android notification using Termux:API.
    
    Args:
        title (str): Notification title
        message (str): Notification message
        sound (bool): Play notification sound
        vibration (bool): Vibrate on notification
    """
    cmd = f'termux-notification --title "{title}" --content "{message}"'
    
    if sound:
        cmd += ' --sound'
    
    if vibration:
        cmd += ' --vibrate 500,200,500'
    
    try:
        os.system(cmd)
        return True
    except Exception as e:
        print(f"⚠️ Notification failed: {e}")
        return False


def notify_download_complete(filename, download_type='video'):
    """
    Send notification for completed download.
    """
    title = "🎬 Download Complete!"
    message = f"Your {download_type} has been downloaded: {filename}"
    send_notification(title, message)
```

### 5. User Interface (Menu-Driven)

```python
def print_banner():
    """Display the main banner."""
    banner = """
╔══════════════════════════════════════════════════════════════════╗
║                                                                  ║
║     ███╗   ███╗███████╗██████╗ ██╗   ██╗██╗   ██╗███████╗       ║
║     ████╗ ████║██╔════╝██╔══██╗██║   ██║██║   ██║██╔════╝       ║
║     ██╔████╔██║█████╗  ██████╔╝██║   ██║██║   ██║███████╗       ║
║     ██║╚██╔╝██║██╔══╝  ██╔══██╗╚██╗ ██╔╝██║   ██║╚════██║       ║
║     ██║ ╚═╝ ██║███████╗██║  ██║ ╚████╔╝ ╚██████╔╝███████║       ║
║     ╚═╝     ╚═╝╚══════╝╚═╝  ╚═╝  ╚═══╝   ╚═════╝ ╚══════╝       ║
║                                                                  ║
║              🎬 YOUTUBE DOWNLOADER BOT 🎬                        ║
║                    by T3rmuxk1ng                                 ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
"""
    print(banner)


def get_video_info(url):
    """Get video information without downloading."""
    ydl_opts = {
        'quiet': True,
        'no_warnings': True,
        'extract_flat': False,
    }
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=False)
            
            return {
                'title': info.get('title', 'Unknown'),
                'duration': info.get('duration_string', 'N/A'),
                'uploader': info.get('uploader', 'Unknown'),
                'view_count': info.get('view_count', 0),
                'description': info.get('description', '')[:200] + '...',
            }
    except Exception as e:
        return None


def quality_menu():
    """Display quality selection menu."""
    print("\n📊 Select Video Quality:")
    print("─" * 30)
    print("1. 📱 360p  (Smallest file)")
    print("2. 📱 480p  (Medium quality)")
    print("3. 📺 720p  (HD Ready)")
    print("4. 📺 1080p (Full HD)")
    print("5. 🎬 Best  (Highest available)")
    print("─" * 30)
    
    choice = input("Enter choice (1-5) [default: 3]: ").strip() or '3'
    
    quality_map = {'1': '360', '2': '480', '3': '720', '4': '1080', '5': 'best'}
    return quality_map.get(choice, '720')


def main_menu():
    """Display main menu and handle user input."""
    while True:
        print_banner()
        
        print("\n📍 MAIN MENU")
        print("=" * 40)
        print("1. 🎬 Download Video")
        print("2. 🎵 Extract Audio (MP3/M4A)")
        print("3. 📁 Download Playlist")
        print("4. 📊 Batch Download from File")
        print("5. 📜 View Download History")
        print("6. 🗑️  Clear History")
        print("7. ⚙️  Settings")
        print("0. 🚪 Exit")
        print("=" * 40)
        
        choice = input("\n👉 Enter your choice: ").strip()
        
        if choice == '1':
            handle_video_download()
        elif choice == '2':
            handle_audio_extraction()
        elif choice == '3':
            handle_playlist_download()
        elif choice == '4':
            handle_batch_download()
        elif choice == '5':
            show_history()
        elif choice == '6':
            clear_history()
        elif choice == '7':
            settings_menu()
        elif choice == '0':
            print("\n👋 Thank you for using YouTube Downloader Bot!")
            print("   Made with ❤️ by T3rmuxk1ng")
            break
        else:
            print("\n❌ Invalid choice. Please try again.")
        
        input("\nPress Enter to continue...")


def handle_video_download():
    """Handle video download flow."""
    print("\n" + "=" * 50)
    print("🎬 VIDEO DOWNLOAD")
    print("=" * 50)
    
    url = input("\nEnter YouTube URL: ").strip()
    
    if not url:
        print("❌ No URL provided.")
        return
    
    # Get video info
    print("\n🔄 Fetching video information...")
    info = get_video_info(url)
    
    if info:
        print(f"\n📹 Title: {info['title']}")
        print(f"⏱️  Duration: {info['duration']}")
        print(f"👤 Uploader: {info['uploader']}")
    
    # Select quality
    quality = quality_menu()
    
    # Confirm download
    confirm = input(f"\n⬇️  Download in {quality}p? (y/n): ").strip().lower()
    
    if confirm == 'y':
        print(f"\n🚀 Starting download...")
        success, result = download_video(url, quality)
        
        if success:
            print(f"\n✅ Successfully downloaded: {result}")
            save_to_history(url, result, 'video')
            send_notification("Download Complete", f"Video: {result[:40]}")
        else:
            print(f"\n❌ Download failed: {result}")
    else:
        print("❌ Download cancelled.")


def handle_audio_extraction():
    """Handle audio extraction flow."""
    print("\n" + "=" * 50)
    print("🎵 AUDIO EXTRACTION")
    print("=" * 50)
    
    url = input("\nEnter YouTube URL: ").strip()
    
    if not url:
        print("❌ No URL provided.")
        return
    
    # Get video info
    print("\n🔄 Fetching video information...")
    info = get_video_info(url)
    
    if info:
        print(f"\n📹 Title: {info['title']}")
        print(f"⏱️  Duration: {info['duration']}")
    
    # Format selection
    print("\n🎵 Select Audio Format:")
    print("1. MP3 (Most compatible)")
    print("2. M4A (Better quality)")
    print("3. AAC (Apple devices)")
    
    format_choice = input("Enter choice (1-3) [default: 1]: ").strip() or '1'
    
    format_map = {'1': 'mp3', '2': 'm4a', '3': 'aac'}
    audio_format = format_map.get(format_choice, 'mp3')
    
    print(f"\n🚀 Extracting audio as {audio_format.upper()}...")
    success, result = extract_audio(url, audio_format)
    
    if success:
        print(f"\n✅ Successfully extracted: {result}")
        save_to_history(url, result, 'audio')
        send_notification("Audio Extracted", f"Audio: {result[:40]}")
    else:
        print(f"\n❌ Extraction failed: {result}")


def handle_playlist_download():
    """Handle playlist download flow."""
    print("\n" + "=" * 50)
    print("📁 PLAYLIST DOWNLOAD")
    print("=" * 50)
    
    url = input("\nEnter YouTube Playlist URL: ").strip()
    
    if not url:
        print("❌ No URL provided.")
        return
    
    print("\n🔄 Fetching playlist information...")
    
    # Get playlist info
    ydl_opts = {'quiet': True, 'extract_flat': True}
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=False)
            
            if 'entries' not in info:
                print("❌ Not a valid playlist URL.")
                return
            
            entries = list(info['entries'])
            total = len(entries)
            
            print(f"\n📁 Playlist: {info.get('title', 'Unknown')}")
            print(f"📊 Total videos: {total}")
            
            # Range selection
            print(f"\nDownload options:")
            print("1. Download all videos")
            print("2. Download specific range")
            print("3. Cancel")
            
            choice = input("\nEnter choice: ").strip()
            
            if choice == '1':
                start, end = 1, None
            elif choice == '2':
                start = int(input("Start from video #: ") or '1')
                end = int(input("End at video #: ") or str(total))
            else:
                print("❌ Cancelled.")
                return
            
            print(f"\n🚀 Starting playlist download...")
            success, result = download_playlist(url, start, end)
            
            if success:
                print(f"\n✅ Playlist download complete!")
                save_to_history(url, info.get('title', 'Playlist'), 'playlist')
                send_notification("Playlist Complete", f"Downloaded {result} videos")
            else:
                print(f"\n❌ Download failed: {result}")
                
    except Exception as e:
        print(f"❌ Error: {e}")


def handle_batch_download():
    """Handle batch download flow."""
    print("\n" + "=" * 50)
    print("📊 BATCH DOWNLOAD")
    print("=" * 50)
    
    # Check if batch file exists
    if not os.path.exists('batch.txt'):
        print("\n📝 Creating batch.txt file...")
        print("   Add one YouTube URL per line.")
        
        with open('batch.txt', 'w') as f:
            f.write("# Add YouTube URLs below (one per line)\n")
            f.write("# Lines starting with # are ignored\n\n")
        
        print("✅ batch.txt created in current directory.")
        print("   Edit the file and add your URLs, then try again.")
        return
    
    # Show URLs in batch file
    with open('batch.txt', 'r') as f:
        lines = [l.strip() for l in f if l.strip() and not l.startswith('#')]
    
    if not lines:
        print("\n⚠️ No URLs found in batch.txt")
        print("   Add URLs to the file and try again.")
        return
    
    print(f"\n📋 Found {len(lines)} URLs in batch.txt:")
    for i, url in enumerate(lines[:5], 1):
        print(f"   {i}. {url[:60]}...")
    if len(lines) > 5:
        print(f"   ... and {len(lines) - 5} more")
    
    confirm = input(f"\n⬇️  Download all {len(lines)} videos? (y/n): ").strip().lower()
    
    if confirm == 'y':
        results = batch_download('batch.txt')
        
        print(f"\n📊 BATCH DOWNLOAD RESULTS")
        print(f"✅ Successful: {len(results.get('success', []))}")
        print(f"❌ Failed: {len(results.get('failed', []))}")
        
        send_notification("Batch Complete", 
                         f"Success: {len(results.get('success', []))}, Failed: {len(results.get('failed', []))}")
    else:
        print("❌ Cancelled.")
```

### 6. Error Handling

```python
class YouTubeBotError(Exception):
    """Base exception for YouTube Bot errors."""
    pass


class InvalidURLError(YouTubeBotError):
    """Raised when URL is not a valid YouTube URL."""
    pass


class DownloadFailedError(YouTubeBotError):
    """Raised when download fails."""
    pass


class NetworkError(YouTubeBotError):
    """Raised when network issues occur."""
    pass


def validate_youtube_url(url):
    """
    Validate if the URL is a valid YouTube URL.
    
    Args:
        url (str): URL to validate
    
    Returns:
        bool: True if valid YouTube URL
    """
    youtube_patterns = [
        r'youtube\.com/watch\?v=',
        r'youtu\.be/',
        r'youtube\.com/playlist\?list=',
        r'youtube\.com/shorts/',
        r'youtube\.com/embed/',
    ]
    
    for pattern in youtube_patterns:
        if re.search(pattern, url):
            return True
    
    return False


def safe_download(download_func, *args, **kwargs):
    """
    Wrapper for safe download with error handling.
    
    Args:
        download_func: Download function to call
        *args, **kwargs: Arguments to pass to function
    
    Returns:
        tuple: (success, result/error_message)
    """
    try:
        return download_func(*args, **kwargs)
    
    except yt_dlp.utils.DownloadError as e:
        return False, f"Download error: {str(e)}"
    
    except yt_dlp.utils.ExtractorError as e:
        return False, f"Extractor error: {str(e)}"
    
    except urllib.error.URLError as e:
        return False, f"Network error: {str(e)}"
    
    except socket.timeout:
        return False, "Connection timeout. Check your internet."
    
    except KeyboardInterrupt:
        return False, "Download cancelled by user."
    
    except Exception as e:
        return False, f"Unexpected error: {str(e)}"


def check_dependencies():
    """
    Check if all required dependencies are installed.
    
    Returns:
        tuple: (all_installed, missing_list)
    """
    missing = []
    
    # Check Python packages
    try:
        import yt_dlp
    except ImportError:
        missing.append('yt-dlp (pip install yt-dlp)')
    
    # Check ffmpeg
    if os.system('ffmpeg -version > /dev/null 2>&1') != 0:
        missing.append('ffmpeg (pkg install ffmpeg)')
    
    # Check Termux:API
    if os.system('termux-notification --help > /dev/null 2>&1') != 0:
        missing.append('Termux:API app (install from F-Droid)')
    
    return len(missing) == 0, missing
```

---

## 💻 COMPLETE SOURCE CODE

### yt_bot.py

```python
#!/usr/bin/env python3
"""
╔══════════════════════════════════════════════════════════════════╗
║          YOUTUBE DOWNLOADER BOT - Complete Edition               ║
║                     by T3rmuxk1ng                                ║
║                                                                  ║
║  Features:                                                       ║
║  • Video download with quality selection                         ║
║  • Audio extraction (MP3, M4A, AAC)                             ║
║  • Playlist download                                             ║
║  • Batch download from file                                      ║
║  • Download history tracking                                     ║
║  • Notifications on completion                                   ║
╚══════════════════════════════════════════════════════════════════╝
"""

import os
import sys
import json
import re
import time
import urllib.error
import socket
from datetime import datetime
from pathlib import Path

# Try to import yt_dlp
try:
    import yt_dlp
except ImportError:
    print("❌ yt-dlp not found!")
    print("   Install with: pip install yt-dlp")
    sys.exit(1)


# ============================================================================
# CONFIGURATION
# ============================================================================

# Download directory
DOWNLOAD_PATH = os.path.expanduser("~/storage/downloads/youtube-bot")

# History file
HISTORY_FILE = os.path.join(os.path.dirname(__file__), "history.json")

# Batch file
BATCH_FILE = os.path.join(os.path.dirname(__file__), "batch.txt")

# Create directories if not exist
os.makedirs(DOWNLOAD_PATH, exist_ok=True)


# ============================================================================
# PROGRESS HOOK
# ============================================================================

def progress_hook(d):
    """Progress hook for yt-dlp downloads."""
    if d['status'] == 'downloading':
        percent = d.get('_percent_str', 'N/A')
        speed = d.get('_speed_str', 'N/A')
        eta = d.get('_eta_str', 'N/A')
        
        # Create visual progress bar
        try:
            percent_clean = percent.strip().replace('%', '')
            percent_num = float(percent_clean)
            bar_length = 30
            filled = int(bar_length * percent_num / 100)
            bar = '█' * filled + '░' * (bar_length - filled)
            
            print(f"\r[{bar}] {percent:>7} | ⚡ {speed:>10} | ⏱️ {eta:>5}", end='', flush=True)
        except:
            print(f"\r⬇️  Progress: {percent} | Speed: {speed}", end='', flush=True)
    
    elif d['status'] == 'finished':
        filename = os.path.basename(d.get('filename', 'Unknown'))
        print(f"\n✅ Downloaded: {filename[:50]}...")
        print("🔄 Processing file...")
    
    elif d['status'] == 'error':
        print(f"\n❌ Error occurred during download")


# ============================================================================
# VIDEO INFO
# ============================================================================

def get_video_info(url):
    """Get video information without downloading."""
    ydl_opts = {
        'quiet': True,
        'no_warnings': True,
        'extract_flat': False,
    }
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=False)
            
            # Format view count
            views = info.get('view_count', 0)
            if views:
                views = f"{views:,}"
            else:
                views = "N/A"
            
            return {
                'title': info.get('title', 'Unknown'),
                'duration': info.get('duration_string', 'N/A'),
                'uploader': info.get('uploader', 'Unknown'),
                'views': views,
                'thumbnail': info.get('thumbnail', ''),
                'description': (info.get('description', '') or '')[:200],
            }
    except Exception as e:
        return None


def get_playlist_info(url):
    """Get playlist information without downloading."""
    ydl_opts = {
        'quiet': True,
        'no_warnings': True,
        'extract_flat': True,
    }
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=False)
            
            if 'entries' not in info:
                return None
            
            entries = list(info['entries'])
            
            return {
                'title': info.get('title', 'Unknown Playlist'),
                'count': len(entries),
                'entries': entries,
            }
    except Exception as e:
        return None


# ============================================================================
# DOWNLOAD FUNCTIONS
# ============================================================================

def download_video(url, quality='720'):
    """
    Download a YouTube video with specified quality.
    
    Args:
        url (str): YouTube video URL
        quality (str): Video quality (360, 480, 720, 1080, best)
    
    Returns:
        tuple: (success, title/error_message)
    """
    quality_map = {
        '360': 'best[height<=360][ext=mp4]/best[height<=360]',
        '480': 'best[height<=480][ext=mp4]/best[height<=480]',
        '720': 'best[height<=720][ext=mp4]/best[height<=720]',
        '1080': 'best[height<=1080][ext=mp4]/best[height<=1080]',
        'best': 'bestvideo+bestaudio/best',
    }
    
    ydl_opts = {
        'format': quality_map.get(quality, quality_map['720']),
        'outtmpl': os.path.join(DOWNLOAD_PATH, '%(title)s.%(ext)s'),
        'progress_hooks': [progress_hook],
        'merge_output_format': 'mp4',
        'quiet': True,
        'no_warnings': True,
        'noplaylist': True,
    }
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            return True, info.get('title', 'Unknown')
    
    except yt_dlp.utils.DownloadError as e:
        return False, f"Download error: {str(e)}"
    except Exception as e:
        return False, f"Error: {str(e)}"


def extract_audio(url, audio_format='mp3', quality='192'):
    """
    Extract audio from a YouTube video.
    
    Args:
        url (str): YouTube video URL
        audio_format (str): Output format (mp3, m4a, aac, wav)
        quality (str): Audio quality in kbps
    
    Returns:
        tuple: (success, title/error_message)
    """
    ydl_opts = {
        'format': 'bestaudio/best',
        'outtmpl': os.path.join(DOWNLOAD_PATH, '%(title)s.%(ext)s'),
        'progress_hooks': [progress_hook],
        'quiet': True,
        'no_warnings': True,
        'noplaylist': True,
        'postprocessors': [{
            'key': 'FFmpegExtractAudio',
            'preferredcodec': audio_format,
            'preferredquality': quality,
        }],
    }
    
    # Add thumbnail embedding for MP3
    if audio_format == 'mp3':
        ydl_opts['writethumbnail'] = True
        ydl_opts['postprocessors'].extend([
            {'key': 'FFmpegThumbnailsConvertor'},
            {'key': 'FFmpegMetadata'},
        ])
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            return True, info.get('title', 'Unknown')
    
    except yt_dlp.utils.DownloadError as e:
        return False, f"Download error: {str(e)}"
    except Exception as e:
        return False, f"Error: {str(e)}"


def download_playlist(url, start=1, end=None):
    """
    Download videos from a YouTube playlist.
    
    Args:
        url (str): YouTube playlist URL
        start (int): Start index (1-based)
        end (int): End index (optional)
    
    Returns:
        tuple: (success, count/error_message)
    """
    playlist_dir = os.path.join(DOWNLOAD_PATH, 'playlists')
    os.makedirs(playlist_dir, exist_ok=True)
    
    ydl_opts = {
        'format': 'best[height<=720][ext=mp4]/best[height<=720]/best',
        'outtmpl': os.path.join(playlist_dir, '%(playlist_title)s/%(playlist_index)02d-%(title)s.%(ext)s'),
        'progress_hooks': [progress_hook],
        'playliststart': start,
        'playlistend': end,
        'quiet': True,
        'no_warnings': True,
        'ignoreerrors': True,  # Continue on errors
    }
    
    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            # Get playlist info first
            info = ydl.extract_info(url, download=False)
            
            if 'entries' not in info:
                return False, "Not a valid playlist URL"
            
            entries = [e for e in info['entries'] if e is not None]
            total = len(entries)
            
            print(f"\n📁 Playlist: {info.get('title', 'Unknown')}")
            print(f"📊 Total videos: {total}")
            print(f"📥 Downloading to: {playlist_dir}")
            
            # Download
            ydl.download([url])
            
            return True, total
    
    except Exception as e:
        return False, f"Error: {str(e)}"


def batch_download(file_path):
    """
    Download videos from URLs listed in a file.
    
    Args:
        file_path (str): Path to file containing URLs
    
    Returns:
        dict: Download results
    """
    results = {
        'success': [],
        'failed': [],
        'total': 0
    }
    
    try:
        with open(file_path, 'r') as f:
            urls = [line.strip() for line in f 
                    if line.strip() and not line.strip().startswith('#')]
        
        results['total'] = len(urls)
        
        if not urls:
            return {'error': 'No URLs found in file'}
        
        print(f"\n📋 Processing {len(urls)} URLs from batch file...")
        
        for i, url in enumerate(urls, 1):
            print(f"\n{'='*50}")
            print(f"[{i}/{len(urls)}] Processing: {url[:50]}...")
            print('='*50)
            
            success, info = download_video(url)
            
            if success:
                results['success'].append({'url': url, 'title': info})
                save_to_history(url, info, 'video')
            else:
                results['failed'].append({'url': url, 'error': info})
                print(f"❌ Failed: {info}")
        
        return results
    
    except FileNotFoundError:
        return {'error': f"File not found: {file_path}"}
    except Exception as e:
        return {'error': str(e)}


# ============================================================================
# HISTORY MANAGEMENT
# ============================================================================

def save_to_history(url, title, download_type):
    """Save download information to history file."""
    history_entry = {
        'url': url,
        'title': title,
        'type': download_type,
        'timestamp': datetime.now().strftime('%Y-%m-%d %H:%M:%S'),
    }
    
    history = []
    
    # Load existing history
    if os.path.exists(HISTORY_FILE):
        try:
            with open(HISTORY_FILE, 'r') as f:
                history = json.load(f)
        except:
            history = []
    
    # Add new entry
    history.append(history_entry)
    
    # Keep only last 100 entries
    if len(history) > 100:
        history = history[-100:]
    
    # Save history
    with open(HISTORY_FILE, 'w') as f:
        json.dump(history, f, indent=2)


def show_history(limit=20):
    """Display download history."""
    if not os.path.exists(HISTORY_FILE):
        print("\n📜 No download history found.")
        return
    
    try:
        with open(HISTORY_FILE, 'r') as f:
            history = json.load(f)
        
        if not history:
            print("\n📜 History is empty.")
            return
        
        print(f"\n{'='*60}")
        print(f"📜 DOWNLOAD HISTORY (Last {min(limit, len(history))} entries)")
        print(f"{'='*60}")
        
        for i, entry in enumerate(history[-limit:][::-1], 1):
            type_icon = {'video': '🎬', 'audio': '🎵', 'playlist': '📁'}.get(entry['type'], '📄')
            
            print(f"\n{i}. {type_icon} {entry['title'][:45]}...")
            print(f"   📅 {entry['timestamp']}")
            print(f"   🔗 {entry['url'][:50]}...")
        
        print(f"\n{'='*60}")
        print(f"📊 Total downloads in history: {len(history)}")
        
    except Exception as e:
        print(f"❌ Error reading history: {e}")


def clear_history():
    """Clear download history."""
    if os.path.exists(HISTORY_FILE):
        os.remove(HISTORY_FILE)
        print("\n🗑️  Download history cleared.")
    else:
        print("\n📜 No history to clear.")


# ============================================================================
# NOTIFICATIONS
# ============================================================================

def send_notification(title, message):
    """Send Android notification using Termux:API."""
    cmd = f'termux-notification --title "{title}" --content "{message}" --sound'
    
    try:
        result = os.system(cmd + ' > /dev/null 2>&1')
        return result == 0
    except:
        return False


# ============================================================================
# UI FUNCTIONS
# ============================================================================

def clear_screen():
    """Clear terminal screen."""
    os.system('clear')


def print_banner():
    """Display the main banner."""
    banner = """
╔══════════════════════════════════════════════════════════════════╗
║                                                                  ║
║     ██╗   ██╗███████╗██████╗  ██████╗ ██████╗ ██████╗ ███████╗  ║
║     ██║   ██║██╔════╝██╔══██╗██╔════╝██╔═══██╗██╔══██╗██╔════╝  ║
║     ██║   ██║█████╗  ██████╔╝██║     ██║   ██║██║  ██║█████╗    ║
║     ╚██╗ ██╔╝██╔══╝  ██╔══██╗██║     ██║   ██║██║  ██║██╔══╝    ║
║      ╚████╔╝ ███████╗██║  ██║╚██████╗╚██████╔╝██████╔╝███████╗  ║
║       ╚═══╝  ╚══════╝╚═╝  ╚═╝ ╚═════╝ ╚═════╝ ╚═════╝ ╚══════╝  ║
║                                                                  ║
║              🎬 YOUTUBE DOWNLOADER BOT 🎬                        ║
║                    by T3rmuxk1ng                                 ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
"""
    print(banner)


def print_menu():
    """Display main menu."""
    print("\n┌─────────────────────────────────────┐")
    print("│          📍 MAIN MENU               │")
    print("├─────────────────────────────────────┤")
    print("│  1. 🎬 Download Video               │")
    print("│  2. 🎵 Extract Audio (MP3/M4A)     │")
    print("│  3. 📁 Download Playlist            │")
    print("│  4. 📊 Batch Download               │")
    print("│  5. 📜 View History                 │")
    print("│  6. 🗑️  Clear History               │")
    print("│  7. ⚙️  Settings                    │")
    print("│  0. 🚪 Exit                         │")
    print("└─────────────────────────────────────┘")


def quality_menu():
    """Display quality selection menu."""
    print("\n┌─────────────────────────────────────┐")
    print("│       📊 Select Video Quality       │")
    print("├─────────────────────────────────────┤")
    print("│  1. 📱 360p  (Smallest file)        │")
    print("│  2. 📱 480p  (Medium quality)       │")
    print("│  3. 📺 720p  (HD Ready)      ⭐     │")
    print("│  4. 📺 1080p (Full HD)              │")
    print("│  5. 🎬 Best  (Highest available)    │")
    print("└─────────────────────────────────────┘")
    
    choice = input("\n👉 Enter choice (1-5) [default: 3]: ").strip() or '3'
    
    quality_map = {'1': '360', '2': '480', '3': '720', '4': '1080', '5': 'best'}
    return quality_map.get(choice, '720')


# ============================================================================
# MENU HANDLERS
# ============================================================================

def handle_video_download():
    """Handle video download flow."""
    clear_screen()
    print_banner()
    
    print("\n" + "="*50)
    print("🎬 VIDEO DOWNLOAD")
    print("="*50)
    
    url = input("\n🔗 Enter YouTube URL: ").strip()
    
    if not url:
        print("❌ No URL provided.")
        return
    
    # Get video info
    print("\n🔄 Fetching video information...")
    info = get_video_info(url)
    
    if info:
        print(f"\n{'─'*50}")
        print(f"📹 Title: {info['title'][:50]}...")
        print(f"⏱️  Duration: {info['duration']}")
        print(f"👤 Uploader: {info['uploader']}")
        print(f"👁️  Views: {info['views']}")
        print(f"{'─'*50}")
    else:
        print("⚠️  Could not fetch video info. Proceeding anyway...")
    
    # Select quality
    quality = quality_menu()
    
    # Confirm download
    confirm = input(f"\n⬇️  Download in {quality}p? (y/n): ").strip().lower()
    
    if confirm == 'y':
        print(f"\n🚀 Starting download...")
        print(f"📂 Saving to: {DOWNLOAD_PATH}")
        print()
        
        success, result = download_video(url, quality)
        
        if success:
            print(f"\n{'─'*50}")
            print(f"✅ Successfully downloaded!")
            print(f"📄 Title: {result}")
            print(f"{'─'*50}")
            
            save_to_history(url, result, 'video')
            send_notification("🎬 Download Complete!", f"Video: {result[:40]}")
        else:
            print(f"\n❌ Download failed: {result}")
    else:
        print("❌ Download cancelled.")


def handle_audio_extraction():
    """Handle audio extraction flow."""
    clear_screen()
    print_banner()
    
    print("\n" + "="*50)
    print("🎵 AUDIO EXTRACTION")
    print("="*50)
    
    url = input("\n🔗 Enter YouTube URL: ").strip()
    
    if not url:
        print("❌ No URL provided.")
        return
    
    # Get video info
    print("\n🔄 Fetching video information...")
    info = get_video_info(url)
    
    if info:
        print(f"\n{'─'*50}")
        print(f"📹 Title: {info['title'][:50]}...")
        print(f"⏱️  Duration: {info['duration']}")
        print(f"{'─'*50}")
    
    # Format selection
    print("\n┌─────────────────────────────────────┐")
    print("│       🎵 Select Audio Format        │")
    print("├─────────────────────────────────────┤")
    print("│  1. MP3 (Most compatible)    ⭐     │")
    print("│  2. M4A (Better quality)           │")
    print("│  3. AAC (Apple devices)            │")
    print("└─────────────────────────────────────┘")
    
    format_choice = input("\n👉 Enter choice (1-3) [default: 1]: ").strip() or '1'
    
    format_map = {'1': 'mp3', '2': 'm4a', '3': 'aac'}
    audio_format = format_map.get(format_choice, 'mp3')
    
    print(f"\n🚀 Extracting audio as {audio_format.upper()}...")
    print(f"📂 Saving to: {DOWNLOAD_PATH}")
    print()
    
    success, result = extract_audio(url, audio_format)
    
    if success:
        print(f"\n{'─'*50}")
        print(f"✅ Successfully extracted!")
        print(f"📄 Title: {result}")
        print(f"🎵 Format: {audio_format.upper()}")
        print(f"{'─'*50}")
        
        save_to_history(url, result, 'audio')
        send_notification("🎵 Audio Extracted!", f"Audio: {result[:40]}")
    else:
        print(f"\n❌ Extraction failed: {result}")


def handle_playlist_download():
    """Handle playlist download flow."""
    clear_screen()
    print_banner()
    
    print("\n" + "="*50)
    print("📁 PLAYLIST DOWNLOAD")
    print("="*50)
    
    url = input("\n🔗 Enter YouTube Playlist URL: ").strip()
    
    if not url:
        print("❌ No URL provided.")
        return
    
    print("\n🔄 Fetching playlist information...")
    
    info = get_playlist_info(url)
    
    if not info:
        print("❌ Not a valid playlist URL or error fetching info.")
        return
    
    print(f"\n{'─'*50}")
    print(f"📁 Playlist: {info['title'][:40]}...")
    print(f"📊 Total videos: {info['count']}")
    print(f"{'─'*50}")
    
    # Range selection
    print(f"\n📥 Download options:")
    print("1. Download all videos")
    print("2. Download specific range")
    print("3. Cancel")
    
    choice = input("\n👉 Enter choice: ").strip()
    
    if choice == '1':
        start, end = 1, None
    elif choice == '2':
        try:
            start = int(input("Start from video #: ") or '1')
            end = int(input("End at video #: ") or str(info['count']))
        except ValueError:
            print("❌ Invalid input.")
            return
    else:
        print("❌ Cancelled.")
        return
    
    confirm = input(f"\n⬇️  Download {end - start + 1 if end else info['count']} videos? (y/n): ").strip().lower()
    
    if confirm == 'y':
        print(f"\n🚀 Starting playlist download...")
        print()
        
        success, result = download_playlist(url, start, end)
        
        if success:
            print(f"\n{'─'*50}")
            print(f"✅ Playlist download complete!")
            print(f"📊 Downloaded: {result} videos")
            print(f"{'─'*50}")
            
            save_to_history(url, info['title'], 'playlist')
            send_notification("📁 Playlist Complete!", f"Downloaded {result} videos")
        else:
            print(f"\n❌ Download failed: {result}")
    else:
        print("❌ Cancelled.")


def handle_batch_download():
    """Handle batch download flow."""
    clear_screen()
    print_banner()
    
    print("\n" + "="*50)
    print("📊 BATCH DOWNLOAD")
    print("="*50)
    
    # Check if batch file exists
    if not os.path.exists(BATCH_FILE):
        print(f"\n📝 Creating batch.txt file...")
        
        with open(BATCH_FILE, 'w') as f:
            f.write("# YouTube Downloader Bot - Batch File\n")
            f.write("# Add one YouTube URL per line\n")
            f.write("# Lines starting with # are ignored\n")
            f.write("# Example:\n")
            f.write("# https://www.youtube.com/watch?v=example1\n")
            f.write("# https://www.youtube.com/watch?v=example2\n\n")
        
        print(f"✅ batch.txt created: {BATCH_FILE}")
        print("   Edit the file and add your URLs, then try again.")
        return
    
    # Show URLs in batch file
    with open(BATCH_FILE, 'r') as f:
        lines = [l.strip() for l in f if l.strip() and not l.strip().startswith('#')]
    
    if not lines:
        print("\n⚠️  No URLs found in batch.txt")
        print("   Add URLs to the file and try again.")
        return
    
    print(f"\n📋 Found {len(lines)} URLs in batch.txt:")
    print(f"{'─'*50}")
    
    for i, url in enumerate(lines[:5], 1):
        print(f"   {i}. {url[:50]}...")
    
    if len(lines) > 5:
        print(f"   ... and {len(lines) - 5} more")
    
    print(f"{'─'*50}")
    
    confirm = input(f"\n⬇️  Download all {len(lines)} videos? (y/n): ").strip().lower()
    
    if confirm == 'y':
        results = batch_download(BATCH_FILE)
        
        if 'error' in results:
            print(f"\n❌ Error: {results['error']}")
            return
        
        print(f"\n{'='*50}")
        print(f"📊 BATCH DOWNLOAD RESULTS")
        print(f"{'='*50}")
        print(f"✅ Successful: {len(results['success'])}")
        print(f"❌ Failed: {len(results['failed'])}")
        
        if results['failed']:
            print(f"\n❌ Failed downloads:")
            for item in results['failed']:
                print(f"   • {item['url'][:40]}... - {item['error'][:30]}")
        
        print(f"{'='*50}")
        
        send_notification("📊 Batch Complete!", 
                         f"Success: {len(results['success'])}, Failed: {len(results['failed'])}")
    else:
        print("❌ Cancelled.")


def handle_settings():
    """Handle settings menu."""
    clear_screen()
    print_banner()
    
    print("\n" + "="*50)
    print("⚙️  SETTINGS")
    print("="*50)
    
    print(f"\n📂 Download Path: {DOWNLOAD_PATH}")
    print(f"📜 History File: {HISTORY_FILE}")
    print(f"📋 Batch File: {BATCH_FILE}")
    
    print(f"\n{'─'*50}")
    print("Options:")
    print("1. Open download folder")
    print("2. Open batch file for editing")
    print("3. Check dependencies")
    print("0. Back to main menu")
    print(f"{'─'*50}")
    
    choice = input("\n👉 Enter choice: ").strip()
    
    if choice == '1':
        print(f"\n📂 Opening {DOWNLOAD_PATH}...")
        os.system(f'termux-open {DOWNLOAD_PATH}')
    
    elif choice == '2':
        print(f"\n📝 Opening batch file...")
        os.system(f'nano {BATCH_FILE}')
    
    elif choice == '3':
        print("\n🔄 Checking dependencies...")
        
        # Check yt-dlp
        try:
            import yt_dlp
            print(f"✅ yt-dlp: Installed (v{yt_dlp.version.__version__})")
        except ImportError:
            print("❌ yt-dlp: Not installed")
            print("   Install with: pip install yt-dlp")
        
        # Check ffmpeg
        if os.system('ffmpeg -version > /dev/null 2>&1') == 0:
            print("✅ ffmpeg: Installed")
        else:
            print("❌ ffmpeg: Not installed")
            print("   Install with: pkg install ffmpeg")
        
        # Check Termux:API
        if os.system('termux-notification --help > /dev/null 2>&1') == 0:
            print("✅ Termux:API: Installed")
        else:
            print("⚠️  Termux:API: Not installed or not working")
            print("   Install Termux:API app from F-Droid")
    
    input("\nPress Enter to continue...")


# ============================================================================
# MAIN FUNCTION
# ============================================================================

def main():
    """Main function - entry point."""
    # Check dependencies on first run
    try:
        import yt_dlp
    except ImportError:
        print("❌ yt-dlp is not installed!")
        print("   Install with: pip install yt-dlp")
        sys.exit(1)
    
    # Main loop
    while True:
        clear_screen()
        print_banner()
        print_menu()
        
        choice = input("\n👉 Enter your choice: ").strip()
        
        if choice == '1':
            handle_video_download()
        elif choice == '2':
            handle_audio_extraction()
        elif choice == '3':
            handle_playlist_download()
        elif choice == '4':
            handle_batch_download()
        elif choice == '5':
            clear_screen()
            print_banner()
            show_history()
        elif choice == '6':
            clear_screen()
            print_banner()
            clear_history()
        elif choice == '7':
            handle_settings()
        elif choice == '0':
            clear_screen()
            print("\n👋 Thank you for using YouTube Downloader Bot!")
            print("   Made with ❤️ by T3rmuxk1ng")
            print("   🔔 Subscribe to @T3rmuxk1ng\n")
            break
        else:
            print("\n❌ Invalid choice. Please try again.")
        
        if choice not in ['0', '7']:
            input("\n\nPress Enter to continue...")


if __name__ == "__main__":
    main()
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Video Download

```bash
# Task: Download a single video in 720p quality

# Step 1: Navigate to project directory
cd ~/youtube-bot

# Step 2: Run the bot
python yt_bot.py

# Step 3: Select option 1 (Video Download)
# Step 4: Enter any YouTube URL
# Step 5: Select quality 3 (720p)
# Step 6: Confirm download with 'y'
# Step 7: Wait for download to complete

# Verify the download
ls ~/storage/downloads/youtube-bot/
```

### Exercise 2: Audio Extraction

```bash
# Task: Extract audio from a music video as MP3

# Step 1: Run the bot
python yt_bot.py

# Step 2: Select option 2 (Audio Extraction)
# Step 3: Enter a music video URL
# Step 4: Select format 1 (MP3)
# Step 5: Wait for extraction

# Verify the audio file
ls ~/storage/downloads/youtube-bot/*.mp3
```

### Exercise 3: Playlist Download

```bash
# Task: Download a small playlist (3-5 videos)

# Step 1: Find a small playlist on YouTube
# Step 2: Run the bot
python yt_bot.py

# Step 3: Select option 3 (Playlist Download)
# Step 4: Enter playlist URL
# Step 5: Select range option (2)
# Step 6: Enter start and end numbers
# Step 7: Confirm download

# Verify downloads
ls ~/storage/downloads/youtube-bot/playlists/
```

### Exercise 4: Batch Download

```bash
# Task: Create a batch file with multiple URLs

# Step 1: Create/edit batch.txt
nano batch.txt

# Step 2: Add URLs (one per line)
https://www.youtube.com/watch?v=VIDEO1
https://www.youtube.com/watch?v=VIDEO2
https://www.youtube.com/watch?v=VIDEO3

# Step 3: Save and exit (Ctrl+X, Y, Enter)

# Step 4: Run batch download
python yt_bot.py
# Select option 4

# Step 5: View results
```

### Exercise 5: Direct yt-dlp Commands

```bash
# Task: Learn yt-dlp command line usage

# Get video info
yt-dlp --print "%(title)s - %(duration)s" "URL"

# List available formats
yt-dlp -F "URL"

# Download specific format
yt-dlp -f "22" "URL"  # Format 22 is usually 720p MP4

# Download with custom filename
yt-dlp -o "my_video.%(ext)s" "URL"

# Extract audio with yt-dlp directly
yt-dlp -x --audio-format mp3 "URL"

# Download subtitles
yt-dlp --write-subs --sub-lang en "URL"
```

### Exercise 6: Customization Challenge

```python
# Task: Add a new feature to the bot

# 1. Add download speed limit option
# Hint: Add 'ratelimit': <bytes_per_sec> to ydl_opts

# 2. Add subtitle download option
# Hint: Add 'writesubtitles': True, 'subtitleslangs': ['en', 'hi']

# 3. Add custom output folder option
# Hint: Modify DOWNLOAD_PATH based on user input

# 4. Add video description download
# Hint: Add 'writedescription': True to ydl_opts
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "yt-dlp: command not found"

```bash
# Cause: yt-dlp not installed or not in PATH

# Solution 1: Install yt-dlp via pip
pip install yt-dlp

# Solution 2: If pip install fails, try
pip install --upgrade pip
pip install yt-dlp

# Solution 3: Install via pkg (if available)
pkg install yt-dlp

# Verify installation
yt-dlp --version
```

### Problem 2: "ffmpeg: command not found"

```bash
# Cause: ffmpeg not installed

# Solution: Install ffmpeg
pkg install ffmpeg -y

# Verify installation
ffmpeg -version
```

### Problem 3: "Unable to download video"

```bash
# Possible causes and solutions:

# 1. Invalid URL
# Solution: Make sure URL is a valid YouTube URL
# Supported formats:
# - https://www.youtube.com/watch?v=VIDEO_ID
# - https://youtu.be/VIDEO_ID
# - https://www.youtube.com/playlist?list=PLAYLIST_ID

# 2. Video is age-restricted
# Solution: yt-dlp usually handles this, but if it fails:
yt-dlp --age-limit 21 "URL"

# 3. Video is private or deleted
# Solution: Cannot download private/deleted videos

# 4. Region locked
# Solution: Try with proxy
yt-dlp --proxy "http://proxy:port" "URL"

# 5. YouTube changed their system
# Solution: Update yt-dlp
pip install --upgrade yt-dlp
```

### Problem 4: "Permission denied" errors

```bash
# Cause: No storage permission

# Solution 1: Grant storage permission
termux-setup-storage

# Solution 2: Check if permission granted
ls /sdcard/

# Solution 3: Manual permission grant
# Settings → Apps → Termux → Permissions → Enable Storage
```

### Problem 5: Download very slow

```bash
# Cause: Slow internet or server throttling

# Solution 1: Lower quality
# Select 360p or 480p instead of 1080p

# Solution 2: Try different time of day
# YouTube servers may be busy during peak hours

# Solution 3: Use external downloader
yt-dlp --external-downloader aria2c "URL"

# Install aria2 first:
pkg install aria2 -y
```

### Problem 6: "No space left on device"

```bash
# Cause: Storage full

# Solution 1: Check available space
df -h

# Solution 2: Clear Termux cache
pkg clean

# Solution 3: Move downloads to SD card
# Edit DOWNLOAD_PATH in the script:
DOWNLOAD_PATH = "/sdcard/external_sd/downloads"

# Solution 4: Delete old downloads
rm -rf ~/storage/downloads/youtube-bot/*
```

### Problem 7: Notifications not working

```bash
# Cause: Termux:API not installed or not working

# Solution 1: Install Termux:API app from F-Droid
# (Not from Play Store!)

# Solution 2: Grant notification permission
# Settings → Apps → Termux:API → Notifications → Enable

# Solution 3: Test notification manually
termux-notification --title "Test" --content "Hello"

# Solution 4: Reinstall Termux:API
# Uninstall both Termux:API apps
# Install fresh from F-Droid
```

### Problem 8: Python script errors

```bash
# Cause: Outdated Python or missing modules

# Solution 1: Update Python
pkg upgrade python -y

# Solution 2: Reinstall dependencies
pip uninstall yt-dlp
pip install yt-dlp

# Solution 3: Check Python version
python --version
# Should be 3.8 or higher

# Solution 4: Check for syntax errors
python -m py_compile yt_bot.py
```

### Problem 9: Playlist download incomplete

```bash
# Cause: Network issues or private videos in playlist

# Solution 1: Use ignore errors (already in script)
# The script continues even if some videos fail

# Solution 2: Download specific range
# Use the range option to skip problematic videos

# Solution 3: Manual retry
# Download failed videos individually

# Solution 4: Check playlist URL
# Make sure it's not a "mix" playlist (they're temporary)
```

### Problem 10: Audio extraction fails

```bash
# Cause: ffmpeg not working or format issue

# Solution 1: Check ffmpeg
ffmpeg -version

# Solution 2: Reinstall ffmpeg
pkg uninstall ffmpeg
pkg install ffmpeg -y

# Solution 3: Try different format
# Use M4A instead of MP3

# Solution 4: Check for space
df -h
# Audio files can be large

# Solution 5: Manual extraction
yt-dlp -x --audio-format mp3 "URL"
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Feature Showcase**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🎬 YOUTUBE DOWNLOADER BOT        │
│   ────────────────────────────     │
│   📹 Video Download                │
│   🎵 Audio Extraction              │
│   📁 Playlist Support              │
│   📊 Batch Download                │
│                                    │
│   [T3rmuxk1ng Logo]                │
│   Chapter 54 | Termux Course       │
└────────────────────────────────────┘
```

**Option B: Before/After Style**
```
┌────────────────────────────────────┐
│  ❌ WITHOUT: Manual downloading    │
│     • Open browser                 │
│     • Find website                 │
│     • Wait for ads                 │
│     • Quality issues               │
│                                    │
│  ✅ WITH: YouTube Bot              │
│     • One command download         │
│     • Any quality                  │
│     • Audio extraction             │
│     • No ads!                      │
│                                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Eye-Catching**
```
┌────────────────────────────────────┐
│  🔥 BUILD YOUR OWN                 │
│                                    │
│  YOUTUBE DOWNLOADER                │
│  🎬 BOT 🎬                         │
│                                    │
│  In Termux! 📱                     │
│                                    │
│  ✓ Video Download                  │
│  ✓ Audio Extraction                │
│  ✓ Playlist Support                │
│  ✓ Batch Download                  │
│                                    │
│  Chapter 54 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🎬 Termux Full Course - Chapter 54: YouTube Downloader Bot | Complete Python Project

🔥 In this video you'll learn:
• YouTube Downloader Bot kaise banate hain
• yt-dlp library ka complete usage
• Video download with quality selection
• Audio extraction (MP3/M4A)
• Playlist download karna
• Batch download from file
• Notifications on completion
• Complete source code

⏱️ Timestamps:
0:00 - Introduction
1:00 - Project Overview
4:00 - Tools Required
6:00 - yt-dlp Basics
10:00 - Project Structure
12:00 - Code Explanation
18:00 - Live Demo
22:00 - Advanced Features
24:00 - Summary

📥 Commands from this video:
pkg install python ffmpeg -y
pip install yt-dlp
python yt_bot.py

📝 Source Code:
Available in the description/chapter file

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #YouTubeDownloader #PythonProject #T3rmuxk1ng #TermuxCourse #YTDLP #TermuxHindi #AndroidDevelopment #PythonBot

---
⚠️ Disclaimer: This video is for educational purposes. Download only content you have permission to download. Respect copyright laws.
```

### Tags List

```
termux, youtube downloader, yt-dlp, python project, termux project, 
youtube bot, video downloader, audio extraction, playlist download,
termux course, termux hindi, python termux, termux tutorial,
t3rmuxk1ng, android programming, mobile development, download youtube,
youtube mp3, batch download, termux python, learn python,
ethical hacking, cybersecurity, programming tutorial, hindi tutorial,
termux commands, android terminal, linux on android
```

### Hashtags

```
#Termux #YouTubeDownloader #PythonProject #TermuxCourse #YTDLP
#T3rmuxk1ng #TermuxHindi #AndroidDevelopment #PythonProgramming
#VideoDownloader #AudioExtraction #TermuxTutorial #LearnPython
#ProgrammingTutorial #HindiTutorial #MobileDevelopment
```

---

## 📚 ADDITIONAL RESOURCES

### yt-dlp Documentation

| Resource | Link |
|----------|------|
| yt-dlp GitHub | https://github.com/yt-dlp/yt-dlp |
| yt-dlp Docs | https://github.com/yt-dlp/yt-dlp#readme |
| Supported Sites | https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md |
| Format Selection | https://github.com/yt-dlp/yt-dlp#format-selection |

### Python Resources

| Resource | Description |
|----------|-------------|
| Python Docs | https://docs.python.org/3/ |
| yt-dlp Python API | Use `import yt_dlp` |
| JSON Module | `import json` for history |

### ffmpeg Resources

| Resource | Link |
|----------|------|
| ffmpeg Docs | https://ffmpeg.org/documentation.html |
| ffmpeg Wiki | https://trac.ffmpeg.org/wiki |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 55, verify:

- [ ] yt-dlp installed (`yt-dlp --version`)
- [ ] ffmpeg installed (`ffmpeg -version`)
- [ ] Termux:API installed for notifications
- [ ] Bot runs without errors (`python yt_bot.py`)
- [ ] Successfully downloaded at least one video
- [ ] Successfully extracted audio to MP3
- [ ] Tested playlist download
- [ ] Created and used batch.txt file
- [ ] Viewed download history
- [ ] Received notification on completion
- [ ] Downloaded files visible in storage

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 55: Project 5 - Port Scanner**

- Network scanning concepts
- Python socket programming
- Multi-threaded port scanner
- Service detection
- Scan result reporting
- Banner grabbing
- Common ports reference

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
