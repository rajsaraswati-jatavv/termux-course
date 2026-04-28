# Chapter 41: Image & Media Tools in Termux

> **Module:** 7 - Utilities  
> **Chapter:** 41 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed ImageMagick & FFmpeg coverage |
| Installation Guide | ImageMagick, FFmpeg, media tools setup |
| Commands Reference | 30+ image & media commands |
| Practice Exercises | Hands-on image/video processing tasks |
| Troubleshooting | Common processing issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 41
Title: Image & Media Tools in Termux | ImageMagick & FFmpeg Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon T3rmuxk1ng aur aaj hum seekhenge ek bahut hi 
powerful topic - Image aur Media Processing Termux mein!

Haan, aapne sahi suna! Aap apne Android phone se bina kisi premium 
app ke, sirf commands use karke:
- Images convert, resize, crop kar sakte ho
- Videos compress, convert kar sakte ho
- Audio extract kar sakte ho
- GIFs create kar sakte ho
- Screen recording kar sakte ho
- Watermarks add kar sakte ho

Sab kuch FREE mein, command-line power ke saath!

Ye chapter hamare utilities module ka part hai. Hum seekhenge 
ImageMagick for images aur FFmpeg for videos - dono industry 
standard tools jo Termux pe perfectly kaam karte hain!

Chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe 
karein - taki koi video miss na ho.

---

[SECTION 1: IMAGEMAGICK INTRODUCTION - 0:45 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain ki ImageMagick kya hai.

ImageMagick ek command-line image processing tool hai. Ye basically
Photoshop jaisa hai - but command line pe!

Kya kya kar sakte ho ImageMagick se?

✓ Image format conversion (PNG, JPG, WEBP, GIF, etc.)
✓ Image resize karna
✓ Image crop karna
✓ Image rotate karna
✓ Watermark add karna
✓ Text add karna
✓ Filters apply karna
✓ Batch processing (hundreds of images at once)
✓ Image compression
✓ Thumbnails create karna

┌─────────────────────────────────────────────────────────────────────────┐
│                    IMAGEMAGICK CAPABILITIES                              │
├─────────────────────────────────────────────────────────────────────────┤
│ Input Formats  │ 200+ formats supported                                 │
│ Output Formats │ PNG, JPG, WEBP, GIF, BMP, TIFF, PDF, SVG, etc.        │
│ Operations     │ Convert, Resize, Crop, Rotate, Flip, Flop             │
│ Effects        │ Blur, Sharpen, Contrast, Brightness, Grayscale        │
│ Advanced       │ Watermark, Text, Composite, Montage, Animation        │
│ Batch          │ Process multiple files with single command            │
└─────────────────────────────────────────────────────────────────────────┘

Sabse best baat - ye Termux pe perfectly kaam karta hai!

Professional photographers aur developers worldwide use karte hain!

---

[SECTION 2: IMAGEMAGICK INSTALLATION - 3:00 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab ImageMagick install karte hain Termux mein.

Pehle apna Termux update karein:

    pkg update && pkg upgrade -y

Ab ImageMagick install karein:

    pkg install imagemagick -y

[SCREEN: Installation output]

Installation mein kuch seconds lagenge. Wait karein.

Installation ke baad verify karein:

    magick --version

Ya:

    convert --version

Version number dikhna chahiye jaise: ImageMagick 7.1.x

Agar version dikha raha hai - installation successful hai!

ImageMagick ke saath ye commands milengi:
- magick (main command, newer)
- convert (legacy, still works)
- identify (image info)
- mogrify (batch processing)
- composite (combine images)
- montage (create image grids)

Verify all commands:

    which magick convert identify mogrify composite montage

Sab paths dikhne chahiye!

---

[SECTION 3: BASIC IMAGE OPERATIONS - 5:00 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Ab actual image processing start karte hain!

[IMAGE CONVERSION]

Sabse basic - image format convert karna:

    magick input.png output.jpg

Ya purana convert command:

    convert input.png output.jpg

Isse PNG image JPG mein convert ho jaayega!

Multiple formats support hote hain:
    convert input.png output.webp
    convert input.jpg output.gif
    convert input.bmp output.png

[SCREEN: Before/After image]

[IMAGE INFO]

Image ki details dekhne ke liye:

    identify image.jpg

Detailed info:

    identify -verbose image.jpg

Ye dikhayega:
- Image dimensions
- Format
- File size
- Color depth
- Metadata

[IMAGE RESIZING]

Image resize karna:

    # Specific size
    convert input.jpg -resize 800x600 output.jpg

    # Maintain aspect ratio
    convert input.jpg -resize 800x output.jpg    # Width 800, auto height
    convert input.jpg -resize x600 output.jpg    # Height 600, auto width

    # Percentage
    convert input.jpg -resize 50% output.jpg     # 50% size
    convert input.jpg -resize 200% output.jpg    # Double size

    # Maximum dimensions (fit in box)
    convert input.jpg -resize 800x600\> output.jpg   # Only if larger

    # Minimum dimensions
    convert input.jpg -resize 800x600\< output.jpg   # Only if smaller

[IMAGE CROPPING]

Image crop karna:

    # Crop 100x100 pixels from top-left
    convert input.jpg -crop 100x100+0+0 output.jpg

    # Crop from center
    convert input.jpg -gravity center -crop 200x200+0+0 output.jpg

    # Remove 50 pixels from each side
    convert input.jpg -shave 50x50 output.jpg

[IMAGE ROTATION]

Image rotate karna:

    # Rotate 90 degrees clockwise
    convert input.jpg -rotate 90 output.jpg

    # Rotate 45 degrees (with background)
    convert input.jpg -background white -rotate 45 output.jpg

    # Auto-rotate based on EXIF
    convert input.jpg -auto-orient output.jpg

---

[SECTION 4: ADVANCED IMAGE OPERATIONS - 8:00 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch advanced operations dekhte hain!

[ADDING WATERMARK]

Image pe watermark add karna:

    # Text watermark
    convert input.jpg -fill white -pointsize 36 -gravity southeast \
        -annotate +10+10 "© T3rmuxk1ng" output.jpg

    # Semi-transparent watermark
    convert input.jpg -fill "rgba(255,255,255,0.5)" -pointsize 36 \
        -gravity center -annotate 0 "WATERMARK" output.jpg

    # Image watermark
    composite -dissolve 50% -gravity southeast watermark.png \
        input.jpg output.jpg

[ADDING TEXT TO IMAGES]

Text add karna:

    # Simple text
    convert input.jpg -fill white -pointsize 30 -gravity center \
        -annotate 0 "Hello Termux!" output.jpg

    # Styled text
    convert input.jpg -fill yellow -stroke black -strokewidth 2 \
        -font Helvetica -pointsize 40 -gravity south -annotate +0+20 \
        "Styled Text" output.jpg

[IMAGE EFFECTS]

Effects apply karna:

    # Blur
    convert input.jpg -blur 0x5 output.jpg

    # Sharpen
    convert input.jpg -sharpen 0x5 output.jpg

    # Grayscale
    convert input.jpg -colorspace Gray output.jpg

    # Sepia
    convert input.jpg -sepia-tone 80% output.jpg

    # Negate (invert colors)
    convert input.jpg -negate output.jpg

    # Brightness/Contrast
    convert input.jpg -brightness-contrast 20x10 output.jpg

[IMAGE COMPRESSION]

Image compress karna (reduce file size):

    # JPEG quality (1-100, lower = smaller file)
    convert input.jpg -quality 80 output.jpg
    convert input.jpg -quality 50 output.jpg    # More compression

    # Strip metadata
    convert input.jpg -strip output.jpg

    # Optimize for web
    convert input.jpg -strip -quality 85 -interlace Plane output.jpg

---

[SECTION 5: BATCH IMAGE PROCESSING - 11:00 to 13:00]
─────────────────────────────────────────────────────────────────────────────

Ab sabse powerful feature - batch processing!

Bahut saari images ek saath process karna:

[MULTIPLE FILES WITH MOGRIFY]

mogrify command files ko in-place modify karta hai:

    # Resize all JPGs in folder
    mogrify -resize 800x600 *.jpg

    # Convert all PNGs to JPG
    mogrify -format jpg *.png

    # Compress all images
    mogrify -quality 80 -strip *.jpg

    # Resize all images to max 1920px width
    mogrify -resize 1920x\> *.jpg

[WARNING: mogrify original files ko modify karta hai! Backup rakhein!]

[CONVERT MULTIPLE FILES]

convert ke saath multiple files:

    # Convert all PNGs to JPGs with new names
    for f in *.png; do convert "$f" "${f%.png}.jpg"; done

    # Create thumbnails for all images
    for f in *.jpg; do convert "$f" -thumbnail 200x200 "thumb_$f"; done

[BATCH SCRIPT]

Ek batch script banate hain:

    nano batch_resize.sh

Script:

```bash
#!/bin/bash
# Batch Image Resizer by T3rmuxk1ng

SIZE=$1
if [ -z "$SIZE" ]; then
    SIZE="800x600"
fi

mkdir -p resized

for img in *.jpg *.png *.jpeg; do
    if [ -f "$img" ]; then
        echo "Processing: $img"
        convert "$img" -resize "$SIZE" "resized/$img"
    fi
done

echo "Done! Check 'resized' folder."
```

Use karein:

    chmod +x batch_resize.sh
    ./batch_resize.sh 1920x1080

---

[SECTION 6: FFMPEG INTRODUCTION - 13:00 to 14:30]
─────────────────────────────────────────────────────────────────────────────

Ab video processing ke liye FFmpeg seekhte hain!

FFmpeg ek multimedia framework hai jo:
- Video conversion
- Audio extraction
- Video compression
- Screen recording
- GIF creation
- Video trimming
- Audio conversion

Ye industry standard hai - YouTube, Netflix, VLC sab use karte hain!

┌─────────────────────────────────────────────────────────────────────────┐
│                         FFMPEG CAPABILITIES                              │
├─────────────────────────────────────────────────────────────────────────┤
│ Video Formats  │ MP4, MKV, AVI, WEBM, MOV, FLV, etc.                   │
│ Audio Formats  │ MP3, AAC, WAV, FLAC, OGG, M4A, etc.                   │
│ Operations     │ Convert, Compress, Trim, Merge, Extract                │
│ Recording      │ Screen capture, Audio recording                       │
│ Filters        │ Resize, Crop, Rotate, Watermark, Speed                │
│ Streaming      │ RTMP, HLS, DASH                                       │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 7: FFMPEG INSTALLATION - 14:30 to 15:30]
─────────────────────────────────────────────────────────────────────────────

FFmpeg install karna:

    pkg install ffmpeg -y

FFmpeg bahut bada package hai, thoda time lagega.

Verify installation:

    ffmpeg -version

Version aur configuration details dikhni chahiye.

Useful companion tools:

    pkg install ffprobe -y    # Media analysis (usually included with ffmpeg)

ffprobe se media info:

    ffprobe video.mp4

---

[SECTION 8: VIDEO OPERATIONS - 15:30 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab actual video processing start karte hain!

[VIDEO CONVERSION]

Format convert karna:

    # MP4 to MKV
    ffmpeg -i input.mp4 output.mkv

    # MKV to MP4
    ffmpeg -i input.mkv -c:v libx264 -c:a aac output.mp4

    # Any to MP4 (web compatible)
    ffmpeg -i input.avi -c:v libx264 -c:a aac -movflags +faststart output.mp4

    # MP4 to WEBM
    ffmpeg -i input.mp4 -c:v libvpx-vp9 -c:a libopus output.webm

[VIDEO COMPRESSION]

Video compress karna (reduce file size):

    # CRF compression (lower = better quality, larger file)
    ffmpeg -i input.mp4 -c:v libx264 -crf 28 output.mp4

    # CRF values: 18-28 is good range
    # 18 = visually lossless, 28 = smaller file

    # Set specific bitrate
    ffmpeg -i input.mp4 -b:v 1M -b:a 128k output.mp4

    # Compress with resolution change
    ffmpeg -i input.mp4 -vf "scale=1280:720" -c:v libx264 -crf 26 output.mp4

[VIDEO RESIZING]

Video resolution change:

    # Specific resolution
    ffmpeg -i input.mp4 -vf "scale=1280:720" output.mp4

    # Maintain aspect ratio
    ffmpeg -i input.mp4 -vf "scale=1280:-1" output.mp4    # Width 1280, auto height

    # Half size
    ffmpeg -i input.mp4 -vf "scale=iw/2:ih/2" output.mp4

[VIDEO TRIMMING]

Video se part nikalna:

    # Trim from 00:01:00 to 00:02:00
    ffmpeg -i input.mp4 -ss 00:01:00 -to 00:02:00 -c copy output.mp4

    # Trim 30 seconds starting from 1 minute
    ffmpeg -i input.mp4 -ss 00:01:00 -t 30 -c copy output.mp4

    # Fast trimming (may have issues)
    ffmpeg -ss 00:01:00 -i input.mp4 -t 30 -c copy output.mp4

[AUDIO EXTRACTION]

Video se audio nikalna:

    # Extract audio as MP3
    ffmpeg -i video.mp4 -vn -acodec libmp3lame -ab 192k audio.mp3

    # Extract audio as AAC (M4A)
    ffmpeg -i video.mp4 -vn -acodec aac -ab 192k audio.m4a

    # Extract audio without re-encoding
    ffmpeg -i video.mp4 -vn -acodec copy audio.aac

---

[SECTION 9: GIF CREATION & SCREEN RECORDING - 18:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

[GIF CREATION]

Video se GIF banana:

    # Basic GIF
    ffmpeg -i video.mp4 -vf "fps=10,scale=320:-1" output.gif

    # High quality GIF
    ffmpeg -i video.mp4 -vf "fps=15,scale=480:-1:flags=lanczos" -c:v gif output.gif

    # GIF with palette (better quality)
    ffmpeg -i video.mp4 -vf "fps=15,scale=480:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" output.gif

    # GIF from specific time range
    ffmpeg -ss 00:00:10 -t 5 -i video.mp4 -vf "fps=10,scale=320:-1" output.gif

    # Images to GIF
    ffmpeg -framerate 1 -i img%03d.png -vf "scale=640:-1" output.gif

[SCREEN RECORDING]

Screen record karna (needs termux-api):

    pkg install termux-api -y

    # Screen recording
    termux-screen-record -o screen.mp4

    # With time limit (seconds)
    termux-screen-record -t 30 -o screen.mp4

    # With bit rate
    termux-screen-record -b 4000000 -o screen.mp4

Using FFmpeg directly for recording:

    # Record from camera (if supported)
    ffmpeg -f android_camera -i 0:0 output.mp4

[MEDIA INFO]

Media details dekhna:

    # Basic info
    ffprobe video.mp4

    # Detailed info
    ffprobe -v quiet -print_format json -show_format -show_streams video.mp4

    # Duration only
    ffprobe -v error -show_entries format=duration -of default=noprint_wrappers=1:nokey=1 video.mp4

    # Resolution
    ffprobe -v error -select_streams v:0 -show_entries stream=width,height -of csv=s=x:p=0 video.mp4

---

[SECTION 10: SUMMARY & NEXT PREVIEW - 20:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 41 complete! Let's summarize:

✅ ImageMagick kya hai - Command-line Photoshop
✅ Installation - pkg install imagemagick
✅ Image conversion - PNG, JPG, WEBP, etc.
✅ Image resize, crop, rotate - Complete manipulation
✅ Watermarks & Text - Professional touches
✅ Batch processing - Multiple files at once
✅ FFmpeg installation - pkg install ffmpeg
✅ Video conversion - All major formats
✅ Video compression - Reduce file size
✅ Audio extraction - MP3, M4A from videos
✅ GIF creation - From videos and images
✅ Screen recording - Using termux-api

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 41 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ convert input.png output.jpg         │ Image conversion                 │
│ convert input.jpg -resize 50% out.jpg│ Resize image                     │
│ mogrify -resize 800x600 *.jpg        │ Batch resize                     │
│ ffmpeg -i input.mp4 output.mkv       │ Video conversion                 │
│ ffmpeg -i video.mp4 -vn audio.mp3    │ Extract audio                    │
│ ffmpeg -i video.mp4 -crf 28 out.mp4  │ Compress video                   │
│ ffmpeg -i video.mp4 -ss 1:00 -t 30 out│ Trim video (1min, 30sec)        │
│ ffprobe video.mp4                    │ Media info                       │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 42 mein hum seekhenge:
- PDF Tools
- PDF creation and manipulation
- Text to PDF conversion
- PDF merging and splitting
- Image to PDF conversion

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 42!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. ImageMagick Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      IMAGEMAGICK WORKFLOW                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐             │
│   │  Input Image │───▶│    Decoder   │───▶│  Image Cache │             │
│   └──────────────┘    └──────────────┘    └──────────────┘             │
│                              │                    │                     │
│                              ▼                    ▼                     │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐             │
│   │   Format     │    │   Pixel      │    │   Color      │             │
│   │   Detection  │    │   Operations │    │   Space      │             │
│   └──────────────┘    └──────────────┘    └──────────────┘             │
│                                                    │                     │
│   ┌────────────────────────────────────────────────┘                    │
│   │                                                                      │
│   ▼                                                                      │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐             │
│   │   Filters    │───▶│   Encoder    │───▶│ Output Image │             │
│   │   & Effects  │    │              │    │              │             │
│   └──────────────┘    └──────────────┘    └──────────────┘             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. ImageMagick Commands

| Command | Purpose | Example |
|---------|---------|---------|
| `magick` | Main command (v7+) | `magick input.png output.jpg` |
| `convert` | Legacy conversion | `convert input.png output.jpg` |
| `identify` | Image information | `identify image.jpg` |
| `mogrify` | In-place processing | `mogrify -resize 50% *.jpg` |
| `composite` | Combine images | `composite -blend 50 img1.jpg img2.jpg out.jpg` |
| `montage` | Create image grids | `montage *.jpg -tile 3x3 grid.jpg` |
| `compare` | Image differences | `compare img1.jpg img2.jpg diff.jpg` |
| `stream` | Stream pixels | `stream -map rgb -storage-type char img.raw` |
| `import` | Screenshot | `import screenshot.png` |
| `display` | View image | `display image.jpg` |

### 3. FFmpeg Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         FFMPEG PIPELINE                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐             │
│   │    Input     │───▶│  Demuxer     │───▶│   Decoder    │             │
│   │   (File/URL) │    │              │    │              │             │
│   └──────────────┘    └──────────────┘    └──────────────┘             │
│                                                    │                     │
│                              ┌─────────────────────┴────────┐           │
│                              │                              │           │
│                              ▼                              ▼           │
│                      ┌──────────────┐              ┌──────────────┐    │
│                      │  Video       │              │  Audio       │    │
│                      │  Frames      │              │  Samples     │    │
│                      └──────────────┘              └──────────────┘    │
│                              │                              │           │
│                              ▼                              ▼           │
│                      ┌──────────────┐              ┌──────────────┐    │
│                      │   Filters    │              │   Filters    │    │
│                      │   (Video)    │              │   (Audio)    │    │
│                      └──────────────┘              └──────────────┘    │
│                              │                              │           │
│                              ▼                              ▼           │
│                      ┌──────────────┐              ┌──────────────┐    │
│                      │   Encoder    │              │   Encoder    │    │
│                      └──────────────┘              └──────────────┘    │
│                              │                              │           │
│                              └──────────────┬───────────────┘           │
│                                             ▼                           │
│                                      ┌──────────────┐                  │
│                                      │    Muxer     │                  │
│                                      └──────────────┘                  │
│                                             │                           │
│                                             ▼                           │
│                                      ┌──────────────┐                  │
│                                      │ Output File  │                  │
│                                      └──────────────┘                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. Supported Formats

**ImageMagick Supported Formats:**

| Category | Formats |
|----------|---------|
| Common Web | PNG, JPEG, GIF, WEBP, ICO, SVG |
| Photography | RAW, TIFF, BMP, TGA, PCX |
| Document | PDF, PS, EPS, XCF |
| Video Frames | MP4 (frames), AVI (frames) |
| Animated | GIF, APNG, WEBP |
| Special | HEIC, AVIF, JXL |

**FFmpeg Supported Formats:**

| Category | Input | Output |
|----------|-------|--------|
| Video | MP4, MKV, AVI, MOV, WEBM, FLV, TS, M4V | MP4, MKV, WEBM, AVI, MOV |
| Audio | MP3, AAC, WAV, FLAC, OGG, M4A, WMA | MP3, AAC, WAV, FLAC, OGG, M4A |
| Streaming | RTMP, HLS, DASH, RTP | RTMP, HLS, DASH |
| Image | PNG, JPEG, GIF, BMP, TIFF | PNG, JPEG, GIF, BMP |

### 5. Video Codecs Comparison

| Codec | Quality | Size | Speed | Best For |
|-------|---------|------|-------|----------|
| libx264 | Excellent | Good | Fast | General use, compatibility |
| libx265 (HEVC) | Excellent | Smaller | Slow | High efficiency |
| libvpx-vp9 | Good | Smaller | Slow | Web (WEBM) |
| libaom-av1 | Excellent | Smallest | Very Slow | Future-proof |
| mpeg4 | Good | Larger | Fast | Old devices |

### 6. CRF Quality Guide

```
CRF (Constant Rate Factor) Values for libx264:
═══════════════════════════════════════════════

  0  ──────── Lossless (huge files)
 18 ──────── Visually lossless
 23 ──────── Default (good quality)
 28 ──────── Good for web
 32 ──────── Noticeable compression
 51 ──────── Worst quality

Recommended:
  - High quality: 18-22
  - Normal: 23-26
  - Compression: 27-30
```

---

## 🔧 INSTALLATION GUIDE

### ImageMagick Installation

```bash
# Update Termux
pkg update && pkg upgrade -y

# Install ImageMagick
pkg install imagemagick -y

# Verify installation
magick --version
convert --version
identify -version

# Check supported formats
magick -list format | head -50
```

### FFmpeg Installation

```bash
# Install FFmpeg
pkg install ffmpeg -y

# Verify installation
ffmpeg -version
ffprobe -version

# Check available encoders
ffmpeg -encoders

# Check available decoders
ffmpeg -decoders

# Check available filters
ffmpeg -filters
```

### Additional Media Tools

```bash
# Image optimization tools
pkg install optipng -y       # PNG optimizer
pkg install jpegoptim -y     # JPEG optimizer

# Video tools
pkg install youtube-dl -y    # Video downloader
pkg install yt-dlp -y        # Better video downloader

# Audio tools
pkg install sox -y           # Audio processing
pkg install lame -y          # MP3 encoder
pkg install vorbis-tools -y  # OGG tools

# Screen recording (requires Termux:API app)
pkg install termux-api -y

# Verify termux-api
termux-info
```

---

## 📋 COMMANDS REFERENCE (30+ Commands)

### ImageMagick Commands

#### Image Conversion

```bash
# 1. Basic format conversion
convert input.png output.jpg

# 2. Convert multiple formats
convert input.bmp output.png
convert input.tiff output.webp

# 3. Convert with quality setting
convert input.png -quality 90 output.jpg

# 4. Convert all PNGs to JPG (loop)
for f in *.png; do convert "$f" "${f%.png}.jpg"; done

# 5. Convert to progressive JPEG
convert input.png -interlace Plane output.jpg
```

#### Image Resizing

```bash
# 6. Resize to specific dimensions
convert input.jpg -resize 1920x1080 output.jpg

# 7. Resize maintaining aspect ratio (width)
convert input.jpg -resize 800x output.jpg

# 8. Resize maintaining aspect ratio (height)
convert input.jpg -resize x600 output.jpg

# 9. Resize by percentage
convert input.jpg -resize 50% output.jpg
convert input.jpg -resize 200% output.jpg

# 10. Resize only if larger
convert input.jpg -resize 1920x1080\> output.jpg

# 11. Resize for email/web
convert input.jpg -resize 1024x768\> -quality 85 output.jpg
```

#### Image Cropping

```bash
# 12. Crop specific region
convert input.jpg -crop 500x400+100+50 output.jpg

# 13. Crop from center
convert input.jpg -gravity center -crop 200x200+0+0 output.jpg

# 14. Remove borders
convert input.jpg -shave 50x50 output.jpg

# 15. Auto-crop whitespace
convert input.jpg -trim output.jpg

# 16. Crop percentage
convert input.jpg -crop 50%x50% output.jpg
```

#### Image Rotation & Flip

```bash
# 17. Rotate 90 degrees
convert input.jpg -rotate 90 output.jpg

# 18. Rotate 180 degrees
convert input.jpg -rotate 180 output.jpg

# 19. Rotate with background
convert input.jpg -background white -rotate 45 output.jpg

# 20. Flip vertically
convert input.jpg -flip output.jpg

# 21. Flop horizontally (mirror)
convert input.jpg -flop output.jpg

# 22. Auto-orient based on EXIF
convert input.jpg -auto-orient output.jpg
```

#### Watermark & Text

```bash
# 23. Simple text watermark
convert input.jpg -fill white -pointsize 36 \
    -gravity southeast -annotate +10+10 "© T3rmuxk1ng" output.jpg

# 24. Semi-transparent watermark
convert input.jpg -fill "rgba(255,255,255,0.5)" -pointsize 48 \
    -gravity center -annotate 0 "WATERMARK" output.jpg

# 25. Styled text with shadow
convert input.jpg -fill white -stroke black -strokewidth 2 \
    -font Helvetica -pointsize 40 -gravity south \
    -annotate +0+20 "Styled Text" output.jpg

# 26. Image watermark
composite -dissolve 50% -gravity southeast watermark.png \
    input.jpg output.jpg

# 27. Tiled watermark
convert input.jpg -fill "rgba(255,255,255,0.2)" -pointsize 30 \
    -gravity center -annotate -45 "WATERMARK " -rotate -45 \
    -duplicate 20 -distort SRT 0 -flatten output.jpg
```

#### Image Effects

```bash
# 28. Grayscale conversion
convert input.jpg -colorspace Gray output.jpg

# 29. Sepia tone
convert input.jpg -sepia-tone 80% output.jpg

# 30. Blur effect
convert input.jpg -blur 0x5 output.jpg

# 31. Sharpen
convert input.jpg -sharpen 0x5 output.jpg

# 32. Brightness/Contrast
convert input.jpg -brightness-contrast 20x10 output.jpg

# 33. Invert colors
convert input.jpg -negate output.jpg

# 34. Vignette effect
convert input.jpg -vignette 0x50 output.jpg
```

#### Batch Processing

```bash
# 35. Batch resize all images
mogrify -resize 800x600 *.jpg

# 36. Batch convert PNG to JPG
mogrify -format jpg *.png

# 37. Batch compress all images
mogrify -quality 80 -strip *.jpg

# 38. Batch resize with max width
mogrify -resize 1920x\> *.jpg

# 39. Batch add watermark
mogrify -fill white -pointsize 24 -gravity southeast \
    -annotate +10+10 "© 2024" *.jpg

# 40. Create thumbnails
mkdir -p thumbs
for f in *.jpg; do
    convert "$f" -thumbnail 200x200 "thumbs/$f"
done
```

### FFmpeg Commands

#### Video Conversion

```bash
# 41. Basic video conversion
ffmpeg -i input.mp4 output.mkv

# 42. Convert to MP4 (web compatible)
ffmpeg -i input.avi -c:v libx264 -c:a aac -movflags +faststart output.mp4

# 43. Convert to WEBM
ffmpeg -i input.mp4 -c:v libvpx-vp9 -c:a libopus output.webm

# 44. Convert with specific quality
ffmpeg -i input.mp4 -c:v libx264 -crf 23 -c:a aac -b:a 128k output.mp4
```

#### Video Compression

```bash
# 45. Compress with CRF
ffmpeg -i input.mp4 -c:v libx264 -crf 28 -c:a aac output.mp4

# 46. Compress with bitrate
ffmpeg -i input.mp4 -b:v 1M -b:a 128k output.mp4

# 47. Compress HEVC (H.265)
ffmpeg -i input.mp4 -c:v libx265 -crf 28 -c:a aac output.mp4

# 48. Compress for mobile
ffmpeg -i input.mp4 -vf "scale=854:480" -c:v libx264 -crf 26 \
    -c:a aac -b:a 96k mobile_output.mp4
```

#### Video Resizing

```bash
# 49. Resize video
ffmpeg -i input.mp4 -vf "scale=1280:720" output.mp4

# 50. Resize maintaining aspect ratio
ffmpeg -i input.mp4 -vf "scale=1280:-1" output.mp4

# 51. Resize to half
ffmpeg -i input.mp4 -vf "scale=iw/2:ih/2" output.mp4

# 52. Resize with filter
ffmpeg -i input.mp4 -vf "scale=1920:1080:force_original_aspect_ratio=decrease" output.mp4
```

#### Video Trimming

```bash
# 53. Trim video (from-to)
ffmpeg -i input.mp4 -ss 00:01:00 -to 00:02:00 -c copy output.mp4

# 54. Trim video (start-duration)
ffmpeg -i input.mp4 -ss 00:01:00 -t 30 -c copy output.mp4

# 55. Trim fast (re-encode)
ffmpeg -ss 00:01:00 -i input.mp4 -t 30 -c:v libx264 -c:a aac output.mp4

# 56. Remove last 10 seconds
ffmpeg -i input.mp4 -ss 0 -to $(ffprobe -v error -show_entries format=duration -of default=noprint_wrappers=1:nokey=1 input.mp4 | awk '{print $1-10}') -c copy output.mp4
```

#### Audio Extraction

```bash
# 57. Extract audio as MP3
ffmpeg -i video.mp4 -vn -c:a libmp3lame -b:a 192k audio.mp3

# 58. Extract audio as AAC
ffmpeg -i video.mp4 -vn -c:a aac -b:a 192k audio.m4a

# 59. Extract audio without re-encode
ffmpeg -i video.mp4 -vn -c:a copy audio.aac

# 60. Extract specific audio track
ffmpeg -i video.mkv -map 0:a:1 -c:a copy audio.mp3
```

#### GIF Creation

```bash
# 61. Video to GIF
ffmpeg -i video.mp4 -vf "fps=10,scale=320:-1" output.gif

# 62. High quality GIF
ffmpeg -i video.mp4 -vf "fps=15,scale=480:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" output.gif

# 63. GIF from specific time
ffmpeg -ss 00:00:10 -t 5 -i video.mp4 -vf "fps=10,scale=320:-1" output.gif

# 64. Images to GIF
ffmpeg -framerate 1 -i img%03d.png output.gif

# 65. GIF to video
ffmpeg -i animation.gif -c:v libx264 -pix_fmt yuv420p output.mp4
```

#### Media Information

```bash
# 66. Basic media info
ffprobe video.mp4

# 67. Detailed info in JSON
ffprobe -v quiet -print_format json -show_format -show_streams video.mp4

# 68. Duration only
ffprobe -v error -show_entries format=duration -of default=noprint_wrappers=1:nokey=1 video.mp4

# 69. Resolution
ffprobe -v error -select_streams v:0 -show_entries stream=width,height -of csv=s=x:p=0 video.mp4

# 70. Codec info
ffprobe -v error -select_streams v:0 -show_entries stream=codec_name -of default=noprint_wrappers=1:nokey=1 video.mp4
```

#### Screen Recording

```bash
# 71. Screen record with termux-api
termux-screen-record -o recording.mp4

# 72. Screen record with time limit
termux-screen-record -t 60 -o recording.mp4

# 73. Screen record with bitrate
termux-screen-record -b 8000000 -o recording.mp4
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Image Conversion & Optimization

```bash
# Task: Convert and optimize images for web

# Step 1: Create working directory
mkdir -p ~/storage/downloads/images
cd ~/storage/downloads/images

# Step 2: Download a test image or use existing

# Step 3: Convert PNG to JPG with quality
convert input.png -quality 85 output.jpg

# Step 4: Create web-optimized version
convert input.jpg -resize 1920x1080\> -quality 80 -strip web_optimized.jpg

# Step 5: Compare file sizes
ls -lh input.* output.* web_optimized.*

# Expected: Smaller file size with good quality
```

### Exercise 2: Batch Image Processing

```bash
# Task: Create a batch image processor

# Step 1: Create batch processing script
cat > ~/batch_images.sh << 'EOF'
#!/bin/bash

INPUT_DIR="$1"
OUTPUT_DIR="$2"
SIZE="${3:-1920x1080}"

if [ -z "$INPUT_DIR" ] || [ -z "$OUTPUT_DIR" ]; then
    echo "Usage: $0 <input_dir> <output_dir> [size]"
    echo "Example: $0 ~/storage/downloads/images ~/storage/downloads/processed 800x600"
    exit 1
fi

mkdir -p "$OUTPUT_DIR"

echo "Processing images from: $INPUT_DIR"
echo "Output directory: $OUTPUT_DIR"
echo "Target size: $SIZE"

count=0
for img in "$INPUT_DIR"/*.{jpg,jpeg,png,JPG,JPEG,PNG}; do
    if [ -f "$img" ]; then
        filename=$(basename "$img")
        echo "Processing: $filename"
        convert "$img" -resize "$SIZE\>" -quality 85 -strip "$OUTPUT_DIR/$filename"
        ((count++))
    fi
done

echo "Processed $count images"
EOF

# Step 2: Make executable
chmod +x ~/batch_images.sh

# Step 3: Test the script
~/batch_images.sh ~/storage/downloads/images ~/storage/downloads/processed 800x600

# Expected: All images resized and optimized
```

### Exercise 3: Video Compression

```bash
# Task: Compress a video for sharing

# Step 1: Navigate to video directory
cd ~/storage/downloads

# Step 2: Check original video size
ls -lh input.mp4

# Step 3: Get video info
ffprobe input.mp4

# Step 4: Compress video
ffmpeg -i input.mp4 -c:v libx264 -crf 28 -c:a aac -b:a 128k compressed.mp4

# Step 5: Compare sizes
ls -lh input.mp4 compressed.mp4

# Step 6: Check quality (play video)
termux-open compressed.mp4

# Expected: Smaller file with acceptable quality
```

### Exercise 4: GIF Creation

```bash
# Task: Create GIF from video

# Step 1: Navigate to directory
cd ~/storage/downloads

# Step 2: Create GIF from video segment
ffmpeg -ss 00:00:05 -t 10 -i video.mp4 \
    -vf "fps=15,scale=480:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" \
    output.gif

# Step 3: Check GIF size
ls -lh output.gif

# Step 4: Optimize GIF (if needed)
convert output.gif -coalesce -layers Optimize optimized.gif

# Expected: Smooth GIF with good quality
```

### Exercise 5: Audio Extraction

```bash
# Task: Extract audio from video with metadata

# Step 1: Create extraction script
cat > ~/extract_audio.sh << 'EOF'
#!/bin/bash

VIDEO="$1"
FORMAT="${2:-mp3}"
QUALITY="${3:-192k}"

if [ -z "$VIDEO" ]; then
    echo "Usage: $0 <video_file> [format] [quality]"
    echo "Formats: mp3, aac, m4a, wav, flac"
    exit 1
fi

OUTPUT="${VIDEO%.*}.$FORMAT"

echo "Extracting audio from: $VIDEO"
echo "Format: $FORMAT, Quality: $QUALITY"
echo "Output: $OUTPUT"

case $FORMAT in
    mp3)
        ffmpeg -i "$VIDEO" -vn -c:a libmp3lame -b:a "$QUALITY" "$OUTPUT"
        ;;
    aac|m4a)
        ffmpeg -i "$VIDEO" -vn -c:a aac -b:a "$QUALITY" "${VIDEO%.*}.m4a"
        ;;
    wav)
        ffmpeg -i "$VIDEO" -vn -c:a pcm_s16le "$OUTPUT"
        ;;
    flac)
        ffmpeg -i "$VIDEO" -vn -c:a flac "$OUTPUT"
        ;;
    *)
        echo "Unsupported format: $FORMAT"
        exit 1
        ;;
esac

echo "Done! Audio saved to: $OUTPUT"
EOF

# Step 2: Make executable
chmod +x ~/extract_audio.sh

# Step 3: Test extraction
~/extract_audio.sh video.mp4 mp3 192k

# Expected: Audio file extracted successfully
```

### Exercise 6: Complete Media Processing Script

```bash
# Task: Create comprehensive media processing script

cat > ~/media_tool.sh << 'EOF'
#!/bin/bash

# Media Processing Tool by T3rmuxk1ng
# Supports: Image resize, convert, compress | Video compress, trim, audio extract

RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
CYAN='\033[0;36m'
NC='\033[0m'

show_help() {
    echo -e "${CYAN}═══════════════════════════════════════${NC}"
    echo -e "${CYAN}   Media Processing Tool - T3rmuxk1ng${NC}"
    echo -e "${CYAN}═══════════════════════════════════════${NC}"
    echo ""
    echo "IMAGE COMMANDS:"
    echo "  img-resize <file> <size>     Resize image"
    echo "  img-convert <file> <format>  Convert image format"
    echo "  img-compress <file> <quality> Compress image (1-100)"
    echo "  img-watermark <file> <text>  Add watermark"
    echo "  img-batch <dir> <size>       Batch resize images"
    echo ""
    echo "VIDEO COMMANDS:"
    echo "  vid-compress <file> <crf>    Compress video (18-28)"
    echo "  vid-trim <file> <start> <duration> Trim video"
    echo "  vid-resize <file> <size>     Resize video"
    echo "  vid-audio <file>             Extract audio to MP3"
    echo "  vid-gif <file> <start> <dur> Create GIF from video"
    echo ""
    echo "INFO COMMANDS:"
    echo "  info <file>                  Show media info"
    echo ""
    echo "Examples:"
    echo "  $0 img-resize photo.jpg 800x600"
    echo "  $0 vid-compress video.mp4 28"
    echo "  $0 vid-audio video.mp4"
}

if [ -z "$1" ] || [ "$1" = "--help" ]; then
    show_help
    exit 0
fi

COMMAND="$1"
shift

case $COMMAND in
    img-resize)
        FILE="$1"
        SIZE="$2"
        OUTPUT="resized_$(basename "$FILE")"
        echo -e "${YELLOW}Resizing image to $SIZE...${NC}"
        convert "$FILE" -resize "$SIZE" "$OUTPUT"
        echo -e "${GREEN}✓ Saved to: $OUTPUT${NC}"
        ;;
    img-convert)
        FILE="$1"
        FORMAT="$2"
        OUTPUT="${FILE%.*}.$FORMAT"
        echo -e "${YELLOW}Converting to $FORMAT...${NC}"
        convert "$FILE" "$OUTPUT"
        echo -e "${GREEN}✓ Saved to: $OUTPUT${NC}"
        ;;
    img-compress)
        FILE="$1"
        QUALITY="$2"
        OUTPUT="compressed_$(basename "$FILE")"
        echo -e "${YELLOW}Compressing with quality $QUALITY...${NC}"
        convert "$FILE" -quality "$QUALITY" -strip "$OUTPUT"
        echo -e "${GREEN}✓ Saved to: $OUTPUT${NC}"
        ;;
    img-watermark)
        FILE="$1"
        TEXT="$2"
        OUTPUT="watermarked_$(basename "$FILE")"
        echo -e "${YELLOW}Adding watermark...${NC}"
        convert "$FILE" -fill "rgba(255,255,255,0.5)" -pointsize 24 \
            -gravity southeast -annotate +10+10 "$TEXT" "$OUTPUT"
        echo -e "${GREEN}✓ Saved to: $OUTPUT${NC}"
        ;;
    img-batch)
        DIR="$1"
        SIZE="$2"
        OUTDIR="${DIR}_resized"
        mkdir -p "$OUTDIR"
        echo -e "${YELLOW}Batch resizing images in $DIR...${NC}"
        for img in "$DIR"/*.{jpg,jpeg,png,JPG,JPEG,PNG}; do
            if [ -f "$img" ]; then
                filename=$(basename "$img")
                convert "$img" -resize "$SIZE" "$OUTDIR/$filename"
                echo "  Processed: $filename"
            fi
        done
        echo -e "${GREEN}✓ All images saved to: $OUTDIR${NC}"
        ;;
    vid-compress)
        FILE="$1"
        CRF="$2"
        OUTPUT="compressed_$(basename "$FILE")"
        echo -e "${YELLOW}Compressing video (CRF: $CRF)...${NC}"
        ffmpeg -i "$FILE" -c:v libx264 -crf "$CRF" -c:a aac "$OUTPUT"
        echo -e "${GREEN}✓ Saved to: $OUTPUT${NC}"
        ;;
    vid-trim)
        FILE="$1"
        START="$2"
        DURATION="$3"
        OUTPUT="trimmed_$(basename "$FILE")"
        echo -e "${YELLOW}Trimming video ($START for ${DURATION}s)...${NC}"
        ffmpeg -ss "$START" -i "$FILE" -t "$DURATION" -c copy "$OUTPUT"
        echo -e "${GREEN}✓ Saved to: $OUTPUT${NC}"
        ;;
    vid-resize)
        FILE="$1"
        SIZE="$2"
        OUTPUT="resized_$(basename "$FILE")"
        echo -e "${YELLOW}Resizing video to $SIZE...${NC}"
        ffmpeg -i "$FILE" -vf "scale=$SIZE" -c:v libx264 -c:a aac "$OUTPUT"
        echo -e "${GREEN}✓ Saved to: $OUTPUT${NC}"
        ;;
    vid-audio)
        FILE="$1"
        OUTPUT="${FILE%.*}.mp3"
        echo -e "${YELLOW}Extracting audio...${NC}"
        ffmpeg -i "$FILE" -vn -c:a libmp3lame -b:a 192k "$OUTPUT"
        echo -e "${GREEN}✓ Audio saved to: $OUTPUT${NC}"
        ;;
    vid-gif)
        FILE="$1"
        START="$2"
        DURATION="$3"
        OUTPUT="${FILE%.*}.gif"
        echo -e "${YELLOW}Creating GIF...${NC}"
        ffmpeg -ss "$START" -t "$DURATION" -i "$FILE" \
            -vf "fps=15,scale=480:-1:flags=lanczos" "$OUTPUT"
        echo -e "${GREEN}✓ GIF saved to: $OUTPUT${NC}"
        ;;
    info)
        FILE="$1"
        echo -e "${CYAN}═══════════════════════════════════════${NC}"
        ffprobe -v quiet -print_format json -show_format -show_streams "$FILE" | \
            grep -E '"width"|"height"|"duration"|"bit_rate"|"codec_name"|"format_name"'
        echo -e "${CYAN}═══════════════════════════════════════${NC}"
        ;;
    *)
        echo -e "${RED}Unknown command: $COMMAND${NC}"
        show_help
        ;;
esac
EOF

chmod +x ~/media_tool.sh
~/media_tool.sh --help
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "convert: command not found"

```bash
# Cause: ImageMagick not installed

# Solution: Install ImageMagick
pkg install imagemagick -y

# Verify
which convert
```

### Problem 2: "ffmpeg: command not found"

```bash
# Cause: FFmpeg not installed

# Solution: Install FFmpeg
pkg install ffmpeg -y

# Verify
which ffmpeg
```

### Problem 3: "unable to open image"

```bash
# Cause: File path issue or permissions

# Solution 1: Check file exists
ls -la /path/to/image.jpg

# Solution 2: Use absolute paths
convert /sdcard/Download/image.jpg output.jpg

# Solution 3: Check permissions
chmod 644 image.jpg

# Solution 4: Grant storage permission
termux-setup-storage
```

### Problem 4: Out of memory error

```bash
# Cause: Large image/video processing needs more RAM

# Solution 1: Limit memory usage
export MAGICK_MEMORY_LIMIT=256MB

# Solution 2: Process smaller chunks
convert input.jpg -limit memory 128MB output.jpg

# Solution 3: Resize before processing
convert input.jpg -resize 50% temp.jpg
convert temp.jpg -filter_blur output.jpg
rm temp.jpg

# Solution 4: Use simpler operations
convert input.jpg -strip -quality 80 output.jpg
```

### Problem 5: Video conversion fails

```bash
# Cause: Missing codec or unsupported format

# Solution 1: Check available codecs
ffmpeg -codecs | grep -i "libx264\|aac"

# Solution 2: Use different codec
ffmpeg -i input.mp4 -c:v mpeg4 -c:a aac output.mp4

# Solution 3: Check file info first
ffprobe input.mp4

# Solution 4: Use copy codec (no re-encode)
ffmpeg -i input.mp4 -c copy output.mkv
```

### Problem 6: GIF quality is poor

```bash
# Cause: Default GIF encoding is basic

# Solution: Use palette for better quality
ffmpeg -i video.mp4 -vf "fps=15,scale=480:-1:flags=lanczos,split[s0][s1];[s0]palettegen=stats_mode=full[p];[s1][p]paletteuse=dither=bayer:bayer_scale=5" output.gif

# Alternative: Two-pass palette
ffmpeg -i video.mp4 -vf "palettegen" palette.png
ffmpeg -i video.mp4 -i palette.png -filter_complex "fps=15,scale=480:-1:flags=lanconz[x];[x][1:v]paletteuse" output.gif
```

### Problem 7: Audio extraction has no sound

```bash
# Cause: Wrong audio codec or missing

# Solution 1: Check audio streams
ffprobe -v error -select_streams a -show_entries stream=codec_name video.mp4

# Solution 2: Specify audio stream
ffmpeg -i video.mp4 -map 0:a:0 -c:a libmp3lame audio.mp3

# Solution 3: Re-encode audio
ffmpeg -i video.mp4 -vn -c:a libmp3lame -b:a 192k audio.mp3
```

### Problem 8: Screen recording doesn't work

```bash
# Cause: termux-api not installed or permissions

# Solution 1: Install termux-api
pkg install termux-api -y

# Solution 2: Install Termux:API app from F-Droid
# (Not from Play Store - it's outdated)

# Solution 3: Grant permissions
termux-setup-storage

# Solution 4: Test termux-api
termux-info

# Solution 5: Check recording
termux-screen-record --help
```

### Problem 9: Batch processing slow

```bash
# Cause: Processing one by one

# Solution 1: Use parallel processing
pkg install parallel -y
ls *.jpg | parallel -j 4 convert {} -resize 50% resized/{}

# Solution 2: Use mogrify for in-place
mogrify -resize 800x600 *.jpg

# Solution 3: Limit operations
for f in *.jpg; do
    convert "$f" -resize 800x600 -quality 80 "out/$f"
done
```

### Problem 10: File size too large after conversion

```bash
# Cause: High quality settings or wrong codec

# Solution 1: Use higher CRF for video
ffmpeg -i input.mp4 -crf 30 output.mp4

# Solution 2: Lower video bitrate
ffmpeg -i input.mp4 -b:v 1M output.mp4

# Solution 3: Reduce resolution
ffmpeg -i input.mp4 -vf "scale=1280:-1" output.mp4

# Solution 4: For images, lower quality
convert input.png -quality 60 output.jpg

# Solution 5: Strip metadata
convert input.jpg -strip -quality 80 output.jpg
```

---

## 🎥 VIDEO ASSETS

### Thumbnail Text

```
╔═══════════════════════════════════════════════════════════════╗
║                                                               ║
║     🖼️  IMAGE & MEDIA TOOLS                                  ║
║                                                               ║
║     ImageMagick & FFmpeg                                      ║
║     Complete Guide                                            ║
║                                                               ║
║     [T3rmuxk1ng Logo]                                         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### Video Title

```
Image & Media Tools in Termux | ImageMagick & FFmpeg Complete Guide | T3rmuxk1ng
```

### Video Description

```
🖼️ Termux Full Course - Chapter 41: Image & Media Tools

Namaskar Dosto! Is video mein hum seekhenge Termux mein Image aur Video processing kaise karte hain!

📌 Topics Covered:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⭐ ImageMagick - Command-line Photoshop
⭐ Image conversion, resize, crop, rotate
⭐ Watermark aur text add karna
⭐ Batch image processing
⭐ FFmpeg - Video processing
⭐ Video compression aur conversion
⭐ Audio extraction from video
⭐ GIF creation
⭐ Screen recording
⭐ 30+ practical commands

🔗 Useful Links:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📱 Termux: https://termux.dev
🖼️ ImageMagick: https://imagemagick.org
🎬 FFmpeg: https://ffmpeg.org

📋 Commands from this video:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
pkg install imagemagick -y
pkg install ffmpeg -y
convert input.png output.jpg
ffmpeg -i video.mp4 -vn audio.mp3

⏱️ Timestamps:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
0:00 - Introduction
0:45 - ImageMagick Introduction
3:00 - ImageMagick Installation
5:00 - Basic Image Operations
8:00 - Advanced Image Operations
11:00 - Batch Image Processing
13:00 - FFmpeg Introduction
14:30 - FFmpeg Installation
15:30 - Video Operations
18:00 - GIF Creation & Screen Recording
20:00 - Summary

🔔 Subscribe for more Termux tutorials!
👍 Like this video if it helped you!
💬 Comment your questions below!

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
#Termux #ImageMagick #FFmpeg #T3rmuxk1ng #TermuxCourse
#ImageProcessing #VideoProcessing #CommandLine
#AndroidHacking #TermuxTools #LinuxOnAndroid

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🙏 Thank you for watching!
```

### Video Tags

```
Termux, ImageMagick, FFmpeg, Image Processing, Video Processing, 
Command Line, Android, T3rmuxk1ng, Termux Tutorial, Termux Course, 
Image Resize, Video Compress, GIF Creation, Audio Extraction, 
Batch Processing, Termux Tools, Linux Commands, Android Terminal, 
Termux Commands, Image Conversion, Video Conversion, Watermark, 
Screen Recording, Media Tools, Termux Full Course
```

### Playlist Info

```
Module: 7 - Utilities
Chapter: 41 of 61
Previous: Ch40 - File Compression & Archives
Next: Ch42 - PDF Tools
```

---

## 📚 QUICK REFERENCE CARD

```
┌─────────────────────────────────────────────────────────────────────────┐
│                IMAGEMAGICK QUICK REFERENCE                               │
├─────────────────────────────────────────────────────────────────────────┤
│ convert input.png output.jpg        │ Convert format                    │
│ convert in.jpg -resize 50% out.jpg  │ Resize 50%                        │
│ convert in.jpg -resize 800x out.jpg │ Width 800px                       │
│ convert in.jpg -crop 100x100 out.jpg│ Crop 100x100                      │
│ convert in.jpg -rotate 90 out.jpg   │ Rotate 90°                        │
│ convert in.jpg -blur 0x5 out.jpg    │ Blur effect                       │
│ convert in.jpg -quality 80 out.jpg  │ Compress (quality 80)             │
│ mogrify -resize 800x *.jpg          │ Batch resize                      │
│ identify image.jpg                  │ Image info                        │
├─────────────────────────────────────────────────────────────────────────┤
│                    FFMPEG QUICK REFERENCE                                │
├─────────────────────────────────────────────────────────────────────────┤
│ ffmpeg -i in.mp4 out.mkv            │ Convert format                    │
│ ffmpeg -i in.mp4 -crf 28 out.mp4    │ Compress video                    │
│ ffmpeg -i in.mp4 -vn audio.mp3      │ Extract audio                     │
│ ffmpeg -i in.mp4 -ss 1:00 -t 30 out │ Trim (start 1min, 30sec)          │
│ ffmpeg -i in.mp4 -vf scale=720:-1   │ Resize to 720p                    │
│ ffmpeg -i vid.mp4 -vf fps=10,gif    │ Create GIF                        │
│ ffprobe video.mp4                   │ Media info                        │
└─────────────────────────────────────────────────────────────────────────┘
```

---

**End of Chapter 41**
