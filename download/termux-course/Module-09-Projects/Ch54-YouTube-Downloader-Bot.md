# 📺 Chapter 54: Project 4 - YouTube Downloader Bot

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ██╗   ██╗████████╗███████╗██████╗  ██████╗ ██████╗ ███████╗██████╗        ║
║   ██║   ██║╚══██╔══╝██╔════╝██╔══██╗██╔════╝ ██╔══██╗██╔════╝██╔══██╗       ║
║   ██║   ██║   ██║   █████╗  ██████╔╝██║  ███╗██████╔╝█████╗  ██████╔╝       ║
║   ██║   ██║   ██║   ██╔══╝  ██╔══██╗██║   ██║██╔══██╗██╔══╝  ██╔══██╗       ║
║   ╚██████╔╝   ██║   ███████╗██║  ██║╚██████╔╝██║  ██║███████╗██║  ██║       ║
║    ╚═════╝    ╚═╝   ╚══════╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝       ║
║                                                                              ║
║              📺 YOUTUBE DOWNLOADER BOT 📺                                    ║
║                     by T3rmuxk1ng                                            ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

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

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

### Test Your YouTube Downloader Knowledge!

<details>
<summary>❓ Question 1: Which library is recommended for YouTube downloads in Python?</summary>

**Answer:** `yt-dlp`

**Explanation:** yt-dlp is a fork of the popular youtube-dl with more features and active maintenance. It supports 1000+ sites, not just YouTube, and handles various video formats and qualities.

```bash
pip install yt-dlp
```
</details>

<details>
<summary>❓ Question 2: What is the purpose of ffmpeg in video downloading?</summary>

**Answer:** Merging separate video and audio streams

**Explanation:** YouTube often stores high-quality videos as separate video-only and audio-only streams. ffmpeg merges these into a single file after download. Without ffmpeg, you might get video without audio or vice versa.

```bash
pkg install ffmpeg -y
```
</details>

<details>
<summary>❓ Question 3: Which flag extracts audio only from a video?</summary>

**Answer:** `-x` or `--extract-audio`

**Explanation:** The `-x` flag tells yt-dlp to extract audio from the video file. You can also specify the format with `--audio-format mp3`.

```bash
yt-dlp -x --audio-format mp3 "URL"
```
</details>

<details>
<summary>❓ Question 4: How do you limit download quality to 720p?</summary>

**Answer:** `-f "best[height<=720]"`

**Explanation:** The `-f` flag specifies format selection. The `[height<=720]` filter restricts downloads to videos with height 720 pixels or less.

```bash
yt-dlp -f "best[height<=720]" "URL"
```
</details>

<details>
<summary>❓ Question 5: What does the progress hook do in yt-dlp?</summary>

**Answer:** Monitors download progress in real-time

**Explanation:** Progress hooks are callback functions that yt-dlp calls during download, allowing you to update UI, show progress bars, or track download status.

```python
def progress_hook(d):
    if d['status'] == 'downloading':
        print(f"Progress: {d['_percent_str']}")
```
</details>

<details>
<summary>❓ Question 6: How do you download a playlist with proper numbering?</summary>

**Answer:** Use `%(playlist_index)02d` in output template

**Explanation:** The playlist_index variable numbers each video in the playlist. The `02d` formats it as a 2-digit number with leading zeros.

```bash
yt-dlp -o "%(playlist_index)02d-%(title)s.%(ext)s" "PLAYLIST_URL"
```
</details>

<details>
<summary>❓ Question 7: Which Termux API sends notifications?</summary>

**Answer:** `termux-notification`

**Explanation:** The termux-notification command sends Android notifications from Termux. You can customize title, content, sound, and actions.

```bash
termux-notification --title "Download Complete" --content "Video saved!"
```
</details>

<details>
<summary>❓ Question 8: What is the `-F` flag used for?</summary>

**Answer:** List all available formats for a video

**Explanation:** The `-F` flag shows all available video/audio formats, their quality, file size, and format codes. Useful for selecting specific formats.

```bash
yt-dlp -F "URL"
```
</details>

<details>
<summary>❓ Question 9: How do you update yt-dlp to the latest version?</summary>

**Answer:** `pip install --upgrade yt-dlp` or `yt-dlp -U`

**Explanation:** YouTube frequently changes their API, so yt-dlp needs regular updates. Both methods work to get the latest version.

```bash
pip install --upgrade yt-dlp
# or
yt-dlp -U
```
</details>

<details>
<summary>❓ Question 10: What is the default output filename format?</summary>

**Answer:** `%(title)s.%(ext)s`

**Explanation:** By default, yt-dlp names files using the video title and appropriate extension. You can customize this with the `-o` flag.

```bash
yt-dlp -o "%(title)s [%(id)s].%(ext)s" "URL"
```
</details>

<details>
<summary>❓ Question 11: How do you download subtitles with a video?</summary>

**Answer:** `--write-subs` or `--write-auto-subs`

**Explanation:** `--write-subs` downloads available subtitles, while `--write-auto-subs` downloads auto-generated subtitles if manual ones aren't available.

```bash
yt-dlp --write-subs --sub-langs en "URL"
```
</details>

<details>
<summary>❓ Question 12: What does the `--no-playlist` flag do?</summary>

**Answer:** Downloads only the single video if URL contains playlist

**Explanation:** When you provide a URL that's part of a playlist, yt-dlp might download the whole playlist. `--no-playlist` ensures only the single video is downloaded.

```bash
yt-dlp --no-playlist "VIDEO_IN_PLAYLIST_URL"
```
</details>

<details>
<summary>❓ Question 13: How do you set a download speed limit?</summary>

**Answer:** `--limit-rate` option

**Explanation:** The `--limit-rate` option throttles download speed, useful when you don't want to saturate your bandwidth.

```bash
yt-dlp --limit-rate 1M "URL"  # Limit to 1 MB/s
```
</details>

<details>
<summary>❓ Question 14: What is cookies.txt used for?</summary>

**Answer:** Authentication for private/restricted videos

**Explanation:** Some videos require login to view. Exporting cookies from your browser allows yt-dlp to authenticate as your account.

```bash
yt-dlp --cookies cookies.txt "PRIVATE_URL"
```
</details>

<details>
<summary>❓ Question 15: How do you embed thumbnail into audio file?</summary>

**Answer:** `--embed-thumbnail` flag

**Explanation:** This embeds the video thumbnail as cover art in the audio file, visible in music players.

```bash
yt-dlp -x --audio-format mp3 --embed-thumbnail "URL"
```
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### YouTube Downloader & Media Processing Interview Questions

<details>
<summary>🎤 Q1: How would you design a scalable media downloading service?</summary>

**Answer:**
A scalable media downloading service would include:
1. **Queue system**: Redis/RabbitMQ for download tasks
2. **Worker pool**: Multiple download workers
3. **Storage abstraction**: Support for local, S3, CDN
4. **Progress tracking**: WebSocket for real-time updates
5. **Error handling**: Retry logic, dead letter queue
6. **Rate limiting**: Respect site terms of service

**Follow-up:** How would you handle YouTube's rate limiting?
</details>

<details>
<summary>🎤 Q2: Explain the architecture of video streaming vs downloading.</summary>

**Answer:**
Key differences:
- **Streaming**: Adaptive bitrate (HLS/DASH), chunks on demand, no local storage
- **Downloading**: Complete file transfer, local storage, offline access

**Architecture components:**
```
Streaming:
Client → CDN → Origin Server → Transcoder
         ↓
      (Chunk requests)

Downloading:
Client → Download Manager → Local Storage
         ↓
      (Full file transfer)
```

**Follow-up:** How would you implement resumable downloads?
</details>

<details>
<summary>🎤 Q3: How do you handle different video codecs and formats?</summary>

**Answer:**
Handling multiple formats requires:
1. **Format detection**: ffprobe to analyze streams
2. **Transcoding**: ffmpeg for format conversion
3. **Codec support**: Check device capabilities
4. **Container selection**: MP4 for compatibility, MKV for features
5. **Quality presets**: 360p, 720p, 1080p, 4K options

```python
def transcode_video(input_path, output_path, preset='720p'):
    presets = {
        '360p': '-vf scale=640:360 -b:v 800k',
        '720p': '-vf scale=1280:720 -b:v 2M',
        '1080p': '-vf scale=1920:1080 -b:v 5M'
    }
    cmd = f'ffmpeg -i {input_path} {presets[preset]} {output_path}'
    subprocess.run(cmd, shell=True)
```

**Follow-up:** How do you optimize for mobile devices?
</details>

<details>
<summary>🎤 Q4: How would you implement a secure download system?</summary>

**Answer:**
Security measures for download systems:
1. **URL validation**: Sanitize and verify URLs
2. **Content scanning**: Virus/malware detection
3. **Access control**: Authentication and authorization
4. **Rate limiting**: Prevent abuse
5. **Encryption**: HTTPS for transfers, encrypt stored files
6. **Audit logging**: Track all downloads

**Follow-up:** How do you handle copyrighted content detection?
</details>

<details>
<summary>🎤 Q5: Explain how you would optimize download performance.</summary>

**Answer:**
Performance optimization strategies:
1. **Parallel downloads**: Multiple connections
2. **Chunked transfer**: Range requests
3. **Connection pooling**: Reuse HTTP connections
4. **CDN selection**: Choose closest server
5. **Compression**: Accept-Encoding headers
6. **Caching**: Cache frequently accessed content

```python
import concurrent.futures
import requests

def download_chunk(url, start, end):
    headers = {'Range': f'bytes={start}-{end}'}
    return requests.get(url, headers=headers).content

def parallel_download(url, chunks=4):
    file_size = get_file_size(url)
    chunk_size = file_size // chunks
    
    with concurrent.futures.ThreadPoolExecutor() as executor:
        futures = []
        for i in range(chunks):
            start = i * chunk_size
            end = start + chunk_size - 1
            futures.append(executor.submit(download_chunk, url, start, end))
        
        return [f.result() for f in futures]
```

**Follow-up:** How do you handle network interruptions?
</details>

<details>
<summary>🎤 Q6: How would you design a recommendation system for downloaded content?</summary>

**Answer:**
A recommendation system would use:
1. **Content analysis**: Extract metadata, tags, categories
2. **User behavior**: Track downloads, watch history
3. **Collaborative filtering**: Similar users' preferences
4. **Content-based filtering**: Similar content attributes
5. **Hybrid approach**: Combine multiple methods

**Follow-up:** How do you handle the cold start problem?
</details>

<details>
<summary>🎤 Q7: How do you handle large file downloads efficiently?</summary>

**Answer:**
Large file handling requires:
1. **Streaming writes**: Don't load entire file in memory
2. **Progress persistence**: Track progress for resume
3. **Chunked storage**: Split large files
4. **Checksum verification**: Verify download integrity
5. **Cleanup**: Handle partial downloads

```python
def download_large_file(url, output_path, chunk_size=8192):
    response = requests.get(url, stream=True)
    total_size = int(response.headers.get('content-length', 0))
    
    with open(output_path, 'wb') as f:
        for chunk in response.iter_content(chunk_size=chunk_size):
            f.write(chunk)
            # Update progress...
```

**Follow-up:** How do you implement resumable downloads after failure?
</details>

<details>
<summary>🎤 Q8: Explain the process of audio extraction and encoding.</summary>

**Answer:**
Audio extraction process:
1. **Stream selection**: Identify audio stream
2. **Extraction**: Separate audio from container
3. **Decoding**: Decode if necessary
4. **Encoding**: Convert to desired format
5. **Tagging**: Add metadata

```bash
# Extract and convert audio
ffmpeg -i video.mp4 -vn -acodec libmp3lame -ab 192k audio.mp3

# With metadata
ffmpeg -i video.mp4 -vn -acodec libmp3lame \
       -metadata title="Song Name" \
       -metadata artist="Artist" audio.mp3
```

**Follow-up:** How do you preserve audio quality during extraction?
</details>

<details>
<summary>🎤 Q9: How would you implement a Telegram bot for downloads?</summary>

**Answer:**
A Telegram download bot architecture:
1. **Bot API**: python-telegram-bot library
2. **URL handler**: Parse URLs from messages
3. **Download queue**: Background workers
4. **Progress updates**: Edit message with progress
5. **File upload**: Send completed downloads

```python
from telegram import Update
from telegram.ext import Application, CommandHandler

async def download_command(update: Update, context):
    url = context.args[0] if context.args else None
    if url:
        await update.message.reply_text("Starting download...")
        # Start download in background
        result = await download_video(url)
        await update.message.reply_document(document=result)
```

**Follow-up:** How do you handle Telegram's file size limits?
</details>

<details>
<summary>🎤 Q10: How do you ensure legal compliance in a download tool?</summary>

**Answer:**
Legal compliance involves:
1. **Terms of Service**: Respect platform ToS
2. **Copyright detection**: Identify protected content
3. **User warnings**: Inform users of legal implications
4. **Usage logging**: Maintain audit trails
5. **DMCA compliance**: Respond to takedown requests
6. **Regional restrictions**: Respect geo-blocking

**Follow-up:** How do you handle user-generated content vs copyrighted material?
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Educational Content Download

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📚 EDUCATIONAL CONTENT DOWNLOAD                         │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Student wants to download tutorial playlist for offline.    │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Download entire playlist with numbering                               │
│  yt-dlp -o "%(playlist_index)02d-%(title)s.%(ext)s" \                    │
│          -f "best[height<=720]" \                                         │
│          "PLAYLIST_URL"                                                  │
│                                                                          │
│  Output:                                                                 │
│  ────────                                                                │
│  01-Introduction_to_Python.mp4                                           │
│  02-Variables_and_Data_Types.mp4                                         │
│  03-Control_Flow.mp4                                                     │
│  ...                                                                     │
│  25-Project_Demo.mp4                                                     │
│                                                                          │
│  ✅ Downloaded: 25 videos, 2.3GB total                                   │
│  ⏱️ Time: 45 minutes                                                     │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 2: Music Collection Building

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    🎵 MUSIC COLLECTION BUILDING                            │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Building personal music library from YouTube.                │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Extract audio with metadata                                           │
│  yt-dlp -x --audio-format mp3 \                                          │
│          --audio-quality 0 \                                              │
│          --embed-thumbnail \                                              │
│          --add-metadata \                                                 │
│          -o "~/Music/%(title)s.%(ext)s" \                                 │
│          "MUSIC_URL"                                                     │
│                                                                          │
│  Features applied:                                                        │
│  ─────────────────                                                       │
│  ✅ Best quality MP3 (320kbps)                                            │
│  ✅ Thumbnail embedded as album art                                       │
│  ✅ Metadata (title, artist, date)                                       │
│  ✅ Organized in Music folder                                            │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 3: Research Video Archival

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    🔬 RESEARCH VIDEO ARCHIVAL                              │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Archiving research-related videos for reference.             │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Download with subtitles and description                               │
│  yt-dlp --write-subs --sub-langs en \                                     │
│          --write-description \                                            │
│          --write-info-json \                                              │
│          -o "%(upload_date)s-%(title)s.%(ext)s" \                         │
│          "VIDEO_URL"                                                     │
│                                                                          │
│  Files generated:                                                         │
│  ────────────────                                                        │
│  20241215-Research_Methods.mp4                                           │
│  20241215-Research_Methods.en.srt                                        │
│  20241215-Research_Methods.description                                   │
│  20241215-Research_Methods.info.json                                     │
│                                                                          │
│  ✅ Complete archival with all metadata                                  │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 4: Bandwidth-Conscious Download

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📶 BANDWIDTH-CONSCIOUS DOWNLOAD                         │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Limited mobile data, need to download efficiently.          │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Low quality, small size                                               │
│  yt-dlp -f "worst[height>=360]" \                                         │
│          --limit-rate 500K \                                              │
│          -o "%(title)s.%(ext)s" \                                         │
│          "VIDEO_URL"                                                     │
│                                                                          │
│  Comparison:                                                              │
│  ────────────                                                            │
│  1080p version: 500MB                                                    │
│  360p version: 50MB (90% smaller!)                                       │
│                                                                          │
│  💡 Perfect for watching on phone screen                                 │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 5: Batch Processing Multiple URLs

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📋 BATCH PROCESSING MULTIPLE URLs                       │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Download multiple videos from a list of URLs.               │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Create URL list file                                                  │
│  cat > urls.txt << EOF                                                   │
│  https://youtube.com/watch?v=VIDEO1                                      │
│  https://youtube.com/watch?v=VIDEO2                                      │
│  https://youtube.com/watch?v=VIDEO3                                      │
│  EOF                                                                     │
│                                                                          │
│  # Download all from file                                                │
│  yt-dlp -a urls.txt -f "best[height<=480]" \                              │
│          -o "~/Downloads/%(title)s.%(ext)s"                               │
│                                                                          │
│  Output:                                                                 │
│  ────────                                                                │
│  Processing URL 1/3...                                                   │
│  Processing URL 2/3...                                                   │
│  Processing URL 3/3...                                                   │
│                                                                          │
│  ✅ All downloads completed!                                             │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 PROJECT ARCHITECTURE DIAGRAMS

### YouTube Downloader Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    YOUTUBE DOWNLOADER ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  USER INTERFACE                   PROCESSING                     OUTPUT    │
│  ─────────────                   ──────────                     ──────    │
│                                                                              │
│  ┌─────────────┐                ┌─────────────┐                ┌────────┐  │
│  │   CLI Menu  │                │   URL       │                │ Video  │  │
│  │   (User)    │ ─────────────► │   Validator │ ────────────► │ File   │  │
│  └─────────────┘                └──────┬──────┘                └────────┘  │
│                                        │                                     │
│                                        ▼                                     │
│                                 ┌─────────────┐                             │
│                                 │   yt-dlp    │                             │
│                                 │   Engine    │                             │
│                                 └──────┬──────┘                             │
│                                        │                                     │
│                          ┌─────────────┼─────────────┐                       │
│                          │             │             │                       │
│                          ▼             ▼             ▼                       │
│                   ┌──────────┐  ┌──────────┐  ┌──────────┐                  │
│                   │ Download │  │ Progress │  │ Metadata │                  │
│                   │ Manager  │  │  Hook    │  │ Extractor│                  │
│                   └────┬─────┘  └────┬─────┘  └────┬─────┘                  │
│                        │             │             │                         │
│                        ▼             ▼             ▼                         │
│                   ┌──────────────────────────────────────────┐              │
│                   │              ffmpeg                       │              │
│                   │  (Merge, Convert, Extract Audio)         │              │
│                   └──────────────────────────────────────────┘              │
│                                        │                                     │
│                        ┌───────────────┼───────────────┐                     │
│                        ▼               ▼               ▼                     │
│                   ┌────────┐      ┌────────┐      ┌────────┐                │
│                   │ Video  │      │ Audio  │      │Subtitle│                │
│                   │ Output │      │ Output │      │ Output │                │
│                   └────────┘      └────────┘      └────────┘                │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

### Chapter Dependencies and Navigation

| Category | Chapter | Topic | Connection |
|----------|---------|-------|------------|
| **Prerequisites** | Ch47 | Python Basics | File handling, subprocess |
| | Ch48 | Advanced Python | CLI development |
| | Ch50 | Termux API | Notifications |
| **Related Projects** | Ch56 | File Organizer | Organize downloads |
| | Ch57 | Backup Automation | Backup media |
| **Next Steps** | Ch55 | Port Scanner | Network tools |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Telegram Bot Integration

```python
import yt_dlp
from telegram import Update
from telegram.ext import Application, CommandHandler, MessageHandler, filters

class TelegramDownloadBot:
    def __init__(self, token):
        self.app = Application.builder().token(token).build()
        self.setup_handlers()
    
    def setup_handlers(self):
        self.app.add_handler(CommandHandler("download", self.download))
        self.app.add_handler(MessageHandler(filters.TEXT, self.handle_url))
    
    async def download(self, update, context):
        url = context.args[0] if context.args else None
        if not url:
            await update.message.reply_text("Please provide a URL: /download <url>")
            return
        
        await update.message.reply_text("⏳ Downloading...")
        
        ydl_opts = {
            'format': 'best[height<=720]',
            'outtmpl': '/tmp/%(title)s.%(ext)s',
            'quiet': True,
        }
        
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            filename = ydl.prepare_filename(info)
        
        await update.message.reply_document(document=open(filename, 'rb'))
```

### Advanced Technique 2: Download Scheduler

```python
import schedule
import time

def schedule_download(url, time_str, output_dir):
    """Schedule a download for specific time"""
    def download_job():
        ydl_opts = {'outtmpl': f'{output_dir}/%(title)s.%(ext)s'}
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            ydl.download([url])
    
    schedule.every().day.at(time_str).do(download_job)
    print(f"Download scheduled for {time_str}")

# Usage
schedule_download("https://youtube.com/watch?v=xxx", "02:00", "~/Downloads")
while True:
    schedule.run_pending()
    time.sleep(60)
```

### Advanced Technique 3: Multi-Site Support

```python
SUPPORTED_SITES = {
    'youtube': r'youtube\.com|youtu\.be',
    'twitter': r'twitter\.com|x\.com',
    'instagram': r'instagram\.com',
    'tiktok': r'tiktok\.com',
    'vimeo': r'vimeo\.com',
}

def detect_site(url):
    import re
    for site, pattern in SUPPORTED_SITES.items():
        if re.search(pattern, url):
            return site
    return 'unknown'

def get_site_specific_options(url):
    site = detect_site(url)
    base_opts = {'outtmpl': '%(title)s.%(ext)s'}
    
    if site == 'twitter':
        base_opts['format'] = 'best'
    elif site == 'tiktok':
        base_opts['format'] = 'best'
    
    return base_opts
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### What You Should Have Learned

- [ ] yt-dlp installation and configuration
- [ ] Video download with quality selection
- [ ] Audio extraction from videos
- [ ] Playlist download with numbering
- [ ] Progress tracking implementation
- [ ] Termux notification integration
- [ ] Batch URL processing
- [ ] Metadata and subtitle downloads
- [ ] File organization for downloads
- [ ] ffmpeg for media processing

### Skills Acquired

| Skill | Level | Description |
|-------|-------|-------------|
| yt-dlp Usage | ⭐⭐⭐ | Full command-line proficiency |
| Media Processing | ⭐⭐ | Audio/video handling with ffmpeg |
| CLI Development | ⭐⭐⭐ | Menu-driven applications |
| Progress Tracking | ⭐⭐ | Real-time progress updates |

---

## 🚀 PROJECT CHALLENGES

### Challenge 1: Download Queue Manager

**Task:** Create a download queue system with pause/resume functionality.

**Requirements:**
- Add URLs to queue
- Start/stop queue processing
- Show queue status
- Resume interrupted downloads

**Hint:** Use a SQLite database to track queue state.

### Challenge 2: Video Quality Analyzer

**Task:** Build a tool that analyzes video quality before downloading.

**Requirements:**
- Show all available formats
- Compare file sizes
- Estimate download time
- Recommend optimal quality

**Hint:** Use `yt-dlp -F` to get format information.

### Challenge 3: Watch Later Sync

**Task:** Create a tool that syncs with YouTube's Watch Later playlist.

**Requirements:**
- Authenticate with YouTube
- Download videos from Watch Later
- Remove downloaded from playlist
- Track download history

**Hint:** Use cookies.txt for authentication.

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always use yt-dlp instead of youtube-dl - it's actively maintained and faster!

> 💡 **Pro Tip #2:** Use `-f "best[height<=720]"` for mobile data saving - smaller file sizes!

> 💡 **Pro Tip #3:** ffmpeg is REQUIRED for merging video+audio streams - install it first!

> 💡 **Pro Tip #4:** Use `--no-playlist` flag to download only single video if URL has playlist!

> 💡 **Pro Tip #5:** Add `--write-thumbnail` to save video thumbnails for your media library!

> 💡 **Pro Tip #6:** Use `--embed-subs` to permanently embed subtitles into the video!

> 💡 **Pro Tip #7:** For private playlists, use `--cookies cookies.txt` with your browser cookies!

> 💡 **Pro Tip #8:** Use `-o "%(playlist_index)02d-%(title)s.%(ext)s"` for proper playlist numbering!

> 💡 **Pro Tip #9:** The `--update` flag updates yt-dlp to latest version - run it weekly!

> 💡 **Pro Tip #10:** Use `yt-dlp -F URL` to see ALL available formats before downloading!

---

## 🔥 REAL WORLD USE CASES

### Real World Applications of YouTube Downloader Bot

**1. Educational Content**
- Download tutorial playlists for offline learning
- Archive educational channels before they're removed
- Create offline course libraries

**2. Music Collection**
- Build personal music library from YouTube
- Extract audio in high quality (320kbps)
- Download full albums and EPs

**3. Content Creation**
- Download reference videos for editing
- Archive your own uploaded content
- Create backup of your channel

**4. Research & Archival**
- Preserve videos that might be deleted
- Document social media content
- Create evidence archives

**5. Entertainment**
- Download movies for travel (offline viewing)
- Save favorite shows and clips
- Build kids' entertainment library

**6. Development & Testing**
- Download sample videos for testing apps
- Create test data for video processing
- Benchmark download speeds

---

## ⚡ QUICK REFERENCE CARD

### YouTube Downloader Quick Reference

| Command | Description |
|---------|-------------|
| `yt-dlp URL` | Download best quality |
| `yt-dlp -f 22 URL` | Download specific format |
| `yt-dlp -x --audio-format mp3 URL` | Extract audio as MP3 |
| `yt-dlp --write-subs URL` | Download subtitles |
| `yt-dlp --playlist-items 1-5 URL` | Download specific items |
| `yt-dlp --dateafter 20240101 URL` | Download after date |
| `yt-dlp -o "%(title)s.%(ext)s" URL` | Custom filename |
| `yt-dlp -F URL` | List available formats |
| `yt-dlp --update` | Update to latest version |

### Quality Selection Guide

| Format Code | Quality | Size Est. |
|-------------|---------|-----------|
| `best` | Best available | Varies |
| `best[height<=1080]` | Max 1080p | ~1GB/hr |
| `best[height<=720]` | Max 720p | ~500MB/hr |
| `best[height<=480]` | Max 480p | ~250MB/hr |
| `worst` | Lowest quality | Minimal |

### Audio Format Options

| Format | Quality | Use Case |
|--------|---------|----------|
| mp3 | Variable | Universal compatibility |
| m4a | Best | Apple devices |
| opus | Best quality | Modern players |
| wav | Uncompressed | Audio editing |

---

## 🏆 BONUS CONTENT

### Bonus: Advanced Features to Add

**Feature 1: Auto-Organize Downloads**
```python
def organize_downloads():
    """Organize downloaded files by type"""
    # Videos → Videos/
    # Audio → Music/
    # Thumbnails → Thumbnails/
```

**Feature 2: Download Queue Manager**
```python
class DownloadQueue:
    def __init__(self):
        self.queue = []
        self.completed = []
    
    def add(self, url, options):
        self.queue.append({'url': url, 'options': options})
    
    def process(self):
        for item in self.queue:
            download(item['url'], item['options'])
```

**Feature 3: Download Scheduler**
```python
def schedule_download(url, time):
    """Schedule download for specific time"""
    import schedule
    schedule.every().day.at(time).do(download, url)
```

**Feature 4: Telegram Bot Integration**
```python
def telegram_bot():
    """Create Telegram bot for remote downloads"""
    # Receive URLs via Telegram
    # Download and send back
```

**Feature 5: Video Converter**
```python
def convert_video(input_file, output_format):
    """Convert downloaded video to other formats"""
    # Support: mp4, mkv, webm, avi
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **yt-dlp Integration** - Installing and using the best YouTube downloader
- ✅ **Video Download** - Multiple quality options and format selection
- ✅ **Audio Extraction** - Converting videos to audio files
- ✅ **Playlist Download** - Downloading entire playlists with numbering
- ✅ **Progress Tracking** - Real-time download progress display
- ✅ **Notifications** - Termux notification integration
- ✅ **History Management** - Tracking download history
- ✅ **Batch Processing** - Multiple URL downloads

### Key Takeaways

1. **yt-dlp is powerful** - Supports 1000+ sites, not just YouTube
2. **ffmpeg is essential** - Required for merging and converting
3. **Quality selection matters** - Choose based on storage and needs
4. **Batch downloads save time** - Use files for multiple URLs
5. **Always update yt-dlp** - YouTube changes frequently

---

## 🚀 PROJECT EXTENSIONS

### 5+ Ideas to Extend This Project

**Extension 1: Web Interface** ⭐⭐⭐⭐
- Flask web app for downloads
- Queue management UI
- **Steps:** Create Flask app, add routes, build frontend

**Extension 2: Telegram Bot** ⭐⭐⭐⭐⭐
- Send URL to bot, get file back
- Remote download control
- **Steps:** Use python-telegram-bot, add handlers

**Extension 3: Download Scheduler** ⭐⭐⭐
- Schedule downloads for off-peak hours
- Automatic retry on failure
- **Steps:** Use cron or schedule library

**Extension 4: Multi-Site Support** ⭐⭐⭐⭐
- Support TikTok, Instagram, Twitter
- Unified download interface
- **Steps:** yt-dlp already supports, add URL detection

**Extension 5: Media Server Integration** ⭐⭐⭐⭐⭐
- Auto-add to Plex/Jellyfin
- Metadata fetching
- **Steps:** Add API calls to media servers

**Extension 6: Download History Database** ⭐⭐⭐
- SQLite database for tracking
- Search and filter downloads
- **Steps:** Create database, add CRUD operations

---

## 🔧 CODE WALKTHROUGH

### YouTube Downloader Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    YOUTUBE DOWNLOADER ARCHITECTURE                   │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   USER INPUT              PROCESSING              OUTPUT             │
│   ──────────              ──────────              ──────             │
│                                                                      │
│   ┌─────────────┐      ┌─────────────┐       ┌─────────────┐        │
│   │ Menu        │ ───► │ URL         │ ───►  │ Video File  │        │
│   │ Selection   │      │ Validator   │       │ (.mp4)      │        │
│   └─────────────┘      └─────────────┘       └─────────────┘        │
│         │                    │                     │                 │
│         │ URL                │ Info                │ Audio           │
│         │                    ▼                     ▼                 │
│   ┌─────────────┐      ┌─────────────┐       ┌─────────────┐        │
│   │ Quality     │ ───► │ yt-dlp      │ ───►  │ Audio File  │        │
│   │ Selection   │      │ Engine      │       │ (.mp3)      │        │
│   └─────────────┘      └─────────────┘       └─────────────┘        │
│                              │                                       │
│                              │ Progress                              │
│                              ▼                                       │
│                        ┌─────────────┐                              │
│                        │ Progress    │                              │
│                        │ Hook        │                              │
│                        └─────────────┘                              │
│                              │                                       │
│         ┌────────────────────┼────────────────────┐                 │
│         ▼                    ▼                    ▼                 │
│   ┌───────────┐       ┌───────────┐        ┌───────────┐           │
│   │ Terminal  │       │ History   │        │ Notify    │           │
│   │ Display   │       │ Log       │        │ System    │           │
│   └───────────┘       └───────────┘        └───────────┘           │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Key Functions Explained

```python
def download_video(url, quality='best'):
    """
    Download YouTube video with specified quality.
    
    Flow:
    1. Validate URL format
    2. Extract video info
    3. Select format based on quality
    4. Download video + audio streams
    5. Merge with ffmpeg (if needed)
    6. Save to download directory
    """

def progress_hook(d):
    """
    Track download progress in real-time.
    
    States:
    - 'downloading': Show progress bar, speed, ETA
    - 'finished': Show completion message
    - 'error': Show error details
    
    Display: [████████░░] 80% | 5.2MB/s | ETA: 10s
    """

def extract_audio(url, format='mp3'):
    """
    Extract audio from video file.
    
    Process:
    1. Download best audio stream
    2. Convert to specified format with ffmpeg
    3. Optionally embed thumbnail and metadata
    4. Save to audio directory
    """
```

---

## 📦 DEPLOYMENT GUIDE

### How to Deploy and Share This Project

**1. Install Dependencies**
```bash
pkg install python ffmpeg -y
pip install yt-dlp
```

**2. Create Project Directory**
```bash
mkdir -p ~/youtube-bot/downloads
cd ~/youtube-bot
```

**3. Create requirements.txt**
```
yt-dlp>=2024.1.0
```

**4. Make Executable Script**
```bash
chmod +x yt_bot.py
```

**5. Create Alias**
```bash
echo 'alias ytd="python ~/youtube-bot/yt_bot.py"' >> ~/.bashrc
source ~/.bashrc
# Now just type: ytd
```

**6. GitHub Deployment**
```bash
git init
git add yt_bot.py requirements.txt README.md
git commit -m "YouTube Downloader Bot for Termux"
git push origin main
```

**7. Create Cron Job for Updates**
```bash
# Auto-update yt-dlp weekly
crontab -e
# Add: 0 0 * * 0 pip install --upgrade yt-dlp
```

---

## 🔗 RELATED CHAPTERS

### Cross-Reference to Related Chapters

| Chapter | Topic | Connection |
|---------|-------|------------|
| **Ch51** | Password Generator | Security tools |
| **Ch56** | File Organizer | Organize downloaded files |
| **Ch57** | Backup Automation | Backup downloads |
| **Ch47** | Python Basics | Foundation |
| **Ch49** | Bash Scripting | Alternative implementation |

### Prerequisite Chapters
- 📖 **Ch47: Python Basics** - Python fundamentals
- 📖 **Ch48: Advanced Python** - subprocess module
- 📖 **Ch50: Termux API** - Notifications

### Next Steps
- ➡️ **Ch55: Port Scanner** - Network security
- ➡️ **Ch56: File Organizer** - Organize downloads

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your YouTube Downloader Knowledge!

**Question 1:** Which library is recommended for YouTube downloads?
- a) youtube-dl
- b) yt-dlp ✓
- c) pytube
- d) requests

**Question 2:** What is ffmpeg used for?
- a) Video downloading
- b) Video/audio processing ✓
- c) URL validation
- d) Authentication

**Question 3:** Which flag extracts audio from video?
- a) --audio
- b) --extract-audio
- c) -x ✓
- d) --mp3

**Question 4:** How do you limit download quality to 720p?
- a) --quality 720
- b) -f "best[height<=720]" ✓
- c) --max-height 720
- d) --720p

**Question 5:** What does -F flag do?
- a) Force download
- b) List available formats ✓
- c) Fast download
- d) Fix errors

**Question 6:** Which command downloads a playlist?
- a) yt-dlp --playlist URL
- b) yt-dlp URL (automatic) ✓
- c) yt-dlp --all URL
- d) yt-dlp --download-playlist URL

**Question 7:** How do you copy output to clipboard in Termux?
- a) termux-clipboard-set
- b) termux-copy
- c) Both a and b work ✓
- d) Not possible

**Question 8:** What format code gives best audio quality?
- a) bestaudio ✓
- b) highest
- c) 320
- d) quality=max

**Question 9:** How do you update yt-dlp?
- a) pip install --upgrade yt-dlp ✓
- b) yt-dlp --update (both work)
- c) pkg upgrade yt-dlp
- d) yt-dlp upgrade

**Question 10:** What is the default output filename format?
- a) video_title.mp4
- b) %(title)s.%(ext)s ✓
- c) download.mp4
- d) youtube_video.mp4

**Question 11:** Which flag adds subtitles?
- a) --subtitles
- b) --write-subs ✓
- c) --subs
- d) --add-subtitles

**Question 12:** What does progress_hook do?
- a) Hooks into video processing
- b) Tracks download progress ✓
- c) Fixes broken downloads
- d) Speeds up downloads

---

### Extend the Project Challenges

**Challenge 1:** Add download speed limiter
```python
# Limit download speed to save bandwidth
def download_with_limit(url, max_speed_kbps):
    ydl_opts = {
        'ratelimit': max_speed_kbps * 1024,
    }
```

**Challenge 2:** Implement proxy support
```python
# Download through proxy
def download_with_proxy(url, proxy_url):
    ydl_opts = {
        'proxy': proxy_url,
    }
```

**Challenge 3:** Add video trimming
```python
# Download only part of video
def download_segment(url, start_time, end_time):
    # Use ffmpeg to cut video after download
```

### Bug Fixing Exercises

**Bug 1:** Download fails with "ffmpeg not found"
```python
# Error: FFmpeg not installed
# Fix: pkg install ffmpeg
```
*Solution: Add check for ffmpeg installation at startup*

**Bug 2:** Playlist numbering wrong
```python
ydl_opts = {'outtmpl': '%(title)s.%(ext)s'}  # Missing playlist index!
```
*Fix: Add %(playlist_index)02d- to template*

**Bug 3:** Audio extraction produces wrong format
```python
'preferredcodec': 'mp4',  # Wrong! Should be 'mp3'
```
*Fix: Change to correct codec name*

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
