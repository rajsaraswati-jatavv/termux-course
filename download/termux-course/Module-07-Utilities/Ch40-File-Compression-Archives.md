# Chapter 40: File Compression & Archives

> **Module:** 7 - Utilities  
> **Chapter:** 40 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | All compression tools & archive formats |
| Commands Reference | 25+ commands with examples |
| Practice Exercises | Hands-on compression tasks |
| Troubleshooting | Common archive issues & solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 40
Title: File Compression & Archives | Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - File Compression aur Archives!

Dosto, jab bhi aap files download karte ho, backups lete ho, ya data 
share karte ho - compression kaam aata hai. ZIP files, TAR files, 
GZIP, 7Z - ye sab formats aapko milenge har jagah.

Termux mein compression tools ki full power hai. Aaj hum seekhenge:
- ZIP aur UNZIP commands
- TAR archives create aur extract karna
- GZIP, BZIP2, XZ compression
- 7-Zip aur RAR support
- Password protected archives
- Split archives - badi files ko todna
- Batch compression - ek saath multiple files
- Automated backup scripts
- Aur bahut kuch!

To bina time waste kiye, chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein.

---

[SECTION 1: COMPRESSION BASICS - 0:45 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhein - Compression kya hai?

Compression ka simple matlab hai - files ka size kam karna bina data 
khoje. Jaise aap kapde suitcase mein baandhte ho, compression bhi 
data ko "baandh deta hai" taaki space kam lage.

Do tarah ki compression hoti hai:

1. LOSSLESS COMPRESSION
   - Data loss nahi hota
   - Original file perfectly recoverable
   - ZIP, GZIP, BZIP2, XZ, 7Z - sab lossless hain
   - Text files, code, documents ke liye

2. LOSSY COMPRESSION
   - Kuch data loss hota hai
   - MP3, JPEG, MP4 - ye lossy formats hain
   - Audio, video, images ke liye

Aaj hum LOSSLESS compression seekhenge kyunki ye files aur data ke 
liye use hoti hai.

Archive kya hai?

Archive = Multiple files ko ek file mein combine karna

Jaise aap 100 files ko ek ZIP file mein daal sakte ho. Archive 
combination deta hai, compression size kam karta hai. Dono ek saath 
bhi ho sakte hain - compressed archive!

Common formats:

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMPRESSION FORMATS OVERVIEW                          │
├────────────────┬──────────────┬──────────────────────────────────────────┤
│ Format         │ Extension    │ Use Case                                │
├────────────────┼──────────────┼──────────────────────────────────────────┤
│ ZIP            │ .zip         │ Universal, Windows compatible           │
│ TAR            │ .tar         │ Archive only (no compression)          │
│ GZIP           │ .gz, .tar.gz │ Unix/Linux standard                    │
│ BZIP2          │ .bz2, .tar.bz2│ Better compression, slower            │
│ XZ             │ .xz, .tar.xz │ Best compression, slowest              │
│ 7-Zip          │ .7z          │ Highest compression ratio              │
│ RAR            │ .rar         │ Proprietary, password protection       │
└────────────────┴──────────────┴──────────────────────────────────────────┘

---

[SECTION 2: ZIP & UNZIP - 3:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye pehle package install karein:

    pkg install zip unzip -y

ZIP command - Archive create karna:

[Example 1: Single file compress karna]

    zip backup.zip file.txt

Ye command file.txt ko compress karke backup.zip banayegi.

[Example 2: Multiple files compress karna]

    zip backup.zip file1.txt file2.txt file3.txt

[Example 3: Directory compress karna - RECURSIVE]

    zip -r project.zip myproject/

-r flag recursive ke liye - saari subfolders bhi include hongi.

[Example 4: Maximum compression]

    zip -9 -r backup.zip folder/

-9 means maximum compression (1-9 scale, 9 = best)

[Example 5: Exclude files]

    zip -r backup.zip folder/ -x "*.log"

Ye command .log files ko exclude karegi.

[Example 6: Password protected ZIP]

    zip -P mypassword secret.zip confidential.txt

⚠️ Warning: Password command line pe dikhayi dega history mein!
Better method:

    zip -e secret.zip confidential.txt

-e flag interactive prompt dega password ke liye.

UNZIP command - Extract karna:

[Example 7: Simple extract]

    unzip backup.zip

[Example 8: Specific location pe extract]

    unzip backup.zip -d /sdcard/extracted/

[Example 9: List contents without extracting]

    unzip -l backup.zip

[Example 10: Extract specific file]

    unzip backup.zip file1.txt

[Example 11: Overwrite without asking]

    unzip -o backup.zip

-o flag automatically overwrite karega.

[Example 12: Test archive integrity]

    unzip -t backup.zip

---

[SECTION 3: TAR COMMAND - 6:00 to 9:00]
─────────────────────────────────────────────────────────────────────────────

TAR - Tape ARchive. Ye Linux/Unix ka standard archive tool hai.

TAR sirf archive banata hai, compress nahi karta - LEKIN compression 
tools ke saath combine ho sakta hai!

Package install karein (Termux mein default available hai):

    pkg install tar -y

TAR OPTIONS YAAD RAKHNE KA TARIIKA:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TAR OPTIONS - EASY WAY TO REMEMBER                    │
├─────────────────────────────────────────────────────────────────────────┤
│ -c = Create (archive banana)                                            │
│ -x = Extract (archive kholna)                                           │
│ -t = List (contents dikhana)                                            │
│ -v = Verbose (details dikhana)                                          │
│ -f = File (filename specify karna)                                      │
│ -z = Gzip compression                                                   │
│ -j = Bzip2 compression                                                  │
│ -J = XZ compression                                                     │
└─────────────────────────────────────────────────────────────────────────┘

Common combinations:

TAR.GZ - Create:

    tar -czvf archive.tar.gz folder/

Breakdown:
- c = create
- z = gzip compression
- v = verbose (progress dikhao)
- f = file (archive.tar.gz)

TAR.GZ - Extract:

    tar -xzvf archive.tar.gz

TAR.GZ - Extract to specific directory:

    tar -xzvf archive.tar.gz -C /sdcard/extract/

TAR.BZ2 - Create:

    tar -cjvf archive.tar.bz2 folder/

TAR.BZ2 - Extract:

    tar -xjvf archive.tar.bz2

TAR.XZ - Create:

    tar -cJvf archive.tar.xz folder/

TAR.XZ - Extract:

    tar -xJvf archive.tar.xz

Simple TAR (no compression):

    tar -cvf archive.tar folder/

Extract:

    tar -xvf archive.tar

List contents:

    tar -tvf archive.tar.gz

Add files to existing archive:

    tar -rvf archive.tar newfile.txt

Append only works with plain tar, not compressed!

---

[SECTION 4: GZIP, BZIP2, XZ - 9:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab seekhte hain individual compression tools.

### GZIP

Install:

    pkg install gzip -y

Compress single file:

    gzip file.txt

Output: file.txt.gz (original file remove ho jayega)

Compress but keep original:

    gzip -k file.txt

Decompress:

    gunzip file.txt.gz

Ya:

    gzip -d file.txt.gz

View compressed file content without extracting:

    zcat file.txt.gz

Compress with compression level (1-9):

    gzip -9 file.txt    # Maximum compression
    gzip -1 file.txt    # Fastest compression

### BZIP2

Install:

    pkg install bzip2 -y

BZIP2 GZIP se better compression deta hai, lekin slower hai.

Compress:

    bzip2 file.txt

Output: file.txt.bz2

Keep original:

    bzip2 -k file.txt

Decompress:

    bunzip2 file.txt.bz2

Ya:

    bzip2 -d file.txt.bz2

View content:

    bzcat file.txt.bz2

### XZ

Install:

    pkg install xz -y

XZ sabse best compression deta hai, lekin slowest hai.

Compress:

    xz file.txt

Output: file.txt.xz

Keep original:

    xz -k file.txt

Decompress:

    unxz file.txt.xz

Ya:

    xz -d file.txt.xz

View content:

    xzcat file.txt.xz

Extreme compression:

    xz -9e file.txt

---

[SECTION 5: 7-ZIP & RAR - 12:00 to 14:30]
─────────────────────────────────────────────────────────────────────────────

### 7-ZIP

7-Zip open source hai aur sabse high compression ratio deta hai!

Install:

    pkg install p7zip -y

Create 7z archive:

    7z a archive.7z folder/

'a' = add to archive

Extract 7z:

    7z x archive.7z

'x' = extract with full paths

List contents:

    7z l archive.7z

Password protection:

    7z a -p archive.7z folder/

System password prompt aayega.

Ya direct password:

    7z a -pMyPassword archive.7z secret.txt

Maximum compression:

    7z a -t7z -mx=9 archive.7z folder/

-t7z = 7z format
-mx=9 = maximum compression level

Extract with password:

    7z x -pMyPassword archive.7z

Test archive:

    7z t archive.7z

### RAR

RAR proprietary format hai. Termux mein UNRAR free hai, RAR create 
karne ke liye paid version chahiye, lekin extract free hai.

Install unrar:

    pkg install unrar -y

Extract RAR:

    unrar x archive.rar

List contents:

    unrar l archive.rar

Extract specific file:

    unrar e archive.rar file.txt

'e' = extract to current directory

Extract with password:

    unrar x -pMyPassword archive.rar

---

[SECTION 6: COMPRESSION COMPARISON - 14:30 to 15:30]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain kaun sa format best hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMPRESSION COMPARISON                               │
├──────────────┬────────────┬──────────────┬──────────────────────────────┤
│ Format       │ Speed      │ Compression  │ Best For                    │
├──────────────┼────────────┼──────────────┼──────────────────────────────┤
│ ZIP          │ ⭐⭐⭐⭐⭐ Fast │ ⭐⭐⭐ Good    │ Cross-platform sharing      │
│ GZIP         │ ⭐⭐⭐⭐ Fast  │ ⭐⭐⭐ Good    │ Linux standard, servers     │
│ BZIP2        │ ⭐⭐ Medium  │ ⭐⭐⭐⭐ Better │ Source code, text           │
│ XZ           │ ⭐ Slow     │ ⭐⭐⭐⭐⭐ Best  │ Software distribution       │
│ 7Z           │ ⭐⭐ Medium  │ ⭐⭐⭐⭐⭐ Best  │ Maximum compression         │
│ RAR          │ ⭐⭐ Medium  │ ⭐⭐⭐⭐ Good   │ Recovery features           │
└──────────────┴────────────┴──────────────┴──────────────────────────────┘

Recommendations:

✅ Quick sharing → ZIP
✅ Linux/Unix standard → TAR.GZ  
✅ Best compression → 7Z or XZ
✅ Password protection → 7Z or ZIP
✅ Maximum compatibility → ZIP

---

[SECTION 7: ADVANCED FEATURES - 15:30 to 17:30]
─────────────────────────────────────────────────────────────────────────────

### SPLIT ARCHIVES

Badi files ko chote parts mein todo:

ZIP split:

    zip -s 50m largefile.zip bigfile.iso

Ye 50MB ke parts banayega: largefile.z01, largefile.z02, etc.

7z split:

    7z a -v50m archive.7z bigfile.iso

Parts: archive.7z.001, archive.7z.002, etc.

Split files combine karna:

    cat archive.7z.* > archive.7z
    7z x archive.7z

### BATCH COMPRESSION

Multiple folders ko separate archives mein:

    for dir in */; do
        zip -r "${dir%/}.zip" "$dir"
    done

### AUTOMATED BACKUP SCRIPT

    #!/bin/bash
    # backup.sh - Automated backup script
    
    DATE=$(date +%Y%m%d_%H%M%S)
    BACKUP_DIR="/sdcard/backups"
    SOURCE_DIR="/sdcard/important"
    
    mkdir -p "$BACKUP_DIR"
    
    tar -czvf "$BACKUP_DIR/backup_$DATE.tar.gz" "$SOURCE_DIR"
    
    echo "Backup created: backup_$DATE.tar.gz"

Script run karo:

    chmod +x backup.sh
    ./backup.sh

### ARCHIVE TESTING

ZIP test:

    unzip -t archive.zip

TAR test:

    gzip -t archive.tar.gz

7z test:

    7z t archive.7z

### CORRUPTED ARCHIVE RECOVERY

ZIP repair:

    zip -FF broken.zip --out fixed.zip

7z recovery:

    7z x archive.7z -aoa

-aoa = overwrite all, continue on errors

RAR recovery (if recovery record exists):

    unrar r archive.rar

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 17:30 to 19:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 40 complete! Let's summarize:

✅ ZIP/UNZIP - Universal format, easy to use
✅ TAR - Linux standard archive tool
✅ GZIP/BZIP2/XZ - Compression levels
✅ 7-Zip - Maximum compression
✅ RAR - Extract support
✅ Password protection - Secure archives
✅ Split archives - Handle large files
✅ Batch compression - Automate tasks
✅ Backup automation - Script creation
✅ Recovery - Fix corrupted archives

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 40 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ zip -r archive.zip folder/        │ Create ZIP archive                  │
│ unzip archive.zip                 │ Extract ZIP                         │
│ tar -czvf file.tar.gz folder/     │ Create TAR.GZ                       │
│ tar -xzvf file.tar.gz             │ Extract TAR.GZ                      │
│ gzip file.txt                     │ Compress with GZIP                  │
│ gunzip file.txt.gz                │ Decompress GZIP                     │
│ 7z a archive.7z folder/           │ Create 7Z archive                   │
│ 7z x archive.7z                   │ Extract 7Z                          │
│ unrar x archive.rar               │ Extract RAR                         │
│ 7z a -p archive.7z folder/        │ Password protected 7Z               │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 41 mein hum seekhenge:
- Image processing tools
- ImageMagick commands
- Image conversion & resizing
- Bulk image operations
- Screenshot & screen recording

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 41!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Compression Algorithms Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    COMPRESSION ALGORITHMS                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  DEFLATE (ZIP, GZIP)                                                     │
│  ├── Combination of LZ77 + Huffman coding                               │
│  ├── Fast compression/decompression                                     │
│  └── Good balance of speed and size                                     │
│                                                                          │
│  BWT + RLE + HUFFMAN (BZIP2)                                            │
│  ├── Burrows-Wheeler Transform based                                    │
│  ├── Better compression than GZIP                                       │
│  └── Slower but smaller output                                          │
│                                                                          │
│  LZMA/LZMA2 (7Z, XZ)                                                    │
│  ├── Lempel-Ziv-Markov chain Algorithm                                  │
│  ├── Best compression ratio                                             │
│  └── Slowest but most efficient                                         │
│                                                                          │
│  RAR                                                                     │
│  ├── Proprietary algorithm                                              │
│  ├── Good compression + recovery records                                │
│  └── Partial open-source (unrar only)                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. File Extensions Reference

| Extension | Format | Description |
|-----------|--------|-------------|
| `.zip` | ZIP | Standard archive format |
| `.tar` | TAR | Archive only (no compression) |
| `.gz` | GZIP | Single file compressed |
| `.tar.gz`, `.tgz` | TAR+GZIP | Compressed archive |
| `.bz2` | BZIP2 | Single file compressed |
| `.tar.bz2`, `.tbz2` | TAR+BZIP2 | Compressed archive |
| `.xz` | XZ | Single file compressed |
| `.tar.xz`, `.txz` | TAR+XZ | Compressed archive |
| `.7z` | 7-Zip | 7-Zip archive |
| `.rar` | RAR | RAR archive |
| `.z01`, `.z02`... | ZIP Split | Split ZIP parts |
| `.001`, `.002`... | 7Z Split | Split 7z parts |

### 3. Compression Level Comparison

```bash
# Test with same 100MB text file
# Results may vary based on content type

| Level   | GZIP Size | GZIP Time | XZ Size  | XZ Time  |
|---------|-----------|-----------|----------|----------|
| Original| 100 MB    | -         | 100 MB   | -        |
| Fast (-1)| 35 MB    | 2 sec     | 30 MB    | 5 sec    |
| Default | 28 MB     | 5 sec     | 22 MB    | 15 sec   |
| Best (-9)| 25 MB    | 8 sec     | 18 MB    | 45 sec   |
```

### 4. Archive Structure

```
ZIP FILE STRUCTURE:
┌─────────────────────────────────────┐
│ Local File Header 1                 │
│ ├── Signature (PK\x03\x04)         │
│ ├── Compression method              │
│ ├── CRC-32                          │
│ ├── Compressed size                 │
│ ├── Uncompressed size               │
│ ├── Filename                        │
│ └── File data                       │
├─────────────────────────────────────┤
│ Local File Header 2                 │
│ └── ...                             │
├─────────────────────────────────────┤
│ Central Directory                   │
│ ├── Entry 1                         │
│ ├── Entry 2                         │
│ └── ...                             │
├─────────────────────────────────────┤
│ End of Central Directory            │
│ ├── Total entries                   │
│ ├── Central directory size          │
│ └── Comment (optional)              │
└─────────────────────────────────────┘

TAR FILE STRUCTURE:
┌─────────────────────────────────────┐
│ Header Block (512 bytes)            │
│ ├── Filename (100 bytes)            │
│ ├── File mode (8 bytes)             │
│ ├── Owner ID (8 bytes)              │
│ ├── Group ID (8 bytes)              │
│ ├── File size (12 bytes)            │
│ ├── Modification time (12 bytes)    │
│ ├── Checksum (8 bytes)              │
│ ├── Type flag (1 byte)              │
│ └── ...                             │
├─────────────────────────────────────┤
│ File Content (padded to 512 bytes)  │
├─────────────────────────────────────┤
│ Next Header Block...                │
└─────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### ZIP Commands (25+ Commands)

```bash
# ═══════════════════════════════════════════════════════════════
# ZIP - CREATE ARCHIVES
# ═══════════════════════════════════════════════════════════════

# Install zip/unzip
pkg install zip unzip -y

# Basic - compress single file
zip backup.zip file.txt

# Compress multiple files
zip backup.zip file1.txt file2.txt file3.txt

# Compress directory recursively
zip -r project.zip myproject/

# Maximum compression (level 9)
zip -9 -r backup.zip folder/

# Fast compression (level 1)
zip -1 -r backup.zip folder/

# Password protect (interactive)
zip -e secret.zip confidential.txt

# Password protect (command line - NOT recommended)
zip -P mypassword secret.zip confidential.txt

# Exclude files
zip -r backup.zip folder/ -x "*.log"

# Exclude multiple patterns
zip -r backup.zip folder/ -x "*.log" -x "*.tmp" -x "*.bak"

# Include only specific files
zip -r backup.zip folder/ -i "*.txt"

# Add files to existing archive
zip backup.zip newfile.txt

# Update existing files in archive
zip -u backup.zip modified.txt

# Delete file from archive
zip -d backup.zip unwanted.txt

# Freshen (update only if newer)
zip -f backup.zip file.txt

# Split archive into parts
zip -s 50m largefile.zip bigfile.iso

# Quiet mode (no output)
zip -q backup.zip file.txt

# Show progress
zip backup.zip file.txt

# ═══════════════════════════════════════════════════════════════
# UNZIP - EXTRACT ARCHIVES
# ═══════════════════════════════════════════════════════════════

# Extract all
unzip backup.zip

# Extract to specific directory
unzip backup.zip -d /sdcard/extracted/

# List contents
unzip -l backup.zip

# List detailed info
unzip -Z backup.zip

# Extract specific file
unzip backup.zip file1.txt

# Extract multiple files
unzip backup.zip "file1.txt" "file2.txt"

# Extract with pattern
unzip backup.zip "*.txt"

# Test archive integrity
unzip -t backup.zip

# Overwrite without asking
unzip -o backup.zip

# Never overwrite
unzip -n backup.zip

# Freshen existing files only
unzip -f backup.zip

# Verbose output
unzip -v backup.zip

# Quiet mode
unzip -q backup.zip

# Exclude files when extracting
unzip backup.zip -x "*.log"

# Password protected
unzip -P mypassword secret.zip

# Fix/repair zip
zip -FF broken.zip --out fixed.zip
unzip fixed.zip
```

### TAR Commands

```bash
# ═══════════════════════════════════════════════════════════════
# TAR - ARCHIVE OPERATIONS
# ═══════════════════════════════════════════════════════════════

# Install tar
pkg install tar -y

# ─────────────────────────────────────────────────────────────
# CREATE ARCHIVES
# ─────────────────────────────────────────────────────────────

# Simple tar (no compression)
tar -cvf archive.tar folder/

# TAR.GZ (gzip compression)
tar -czvf archive.tar.gz folder/

# TAR.BZ2 (bzip2 compression)
tar -cjvf archive.tar.bz2 folder/

# TAR.XZ (xz compression)
tar -cJvf archive.tar.xz folder/

# Create with specific files
tar -czvf archive.tar.gz file1.txt file2.txt file3.txt

# Create from multiple directories
tar -czvf archive.tar.gz dir1/ dir2/ dir3/

# Create with exclude
tar -czvf archive.tar.gz folder/ --exclude="*.log"

# Multiple excludes
tar -czvf archive.tar.gz folder/ --exclude="*.log" --exclude="*.tmp"

# Use exclude file
echo "*.log" > exclude.txt
echo "*.tmp" >> exclude.txt
tar -czvf archive.tar.gz folder/ -X exclude.txt

# ─────────────────────────────────────────────────────────────
# EXTRACT ARCHIVES
# ─────────────────────────────────────────────────────────────

# Extract tar
tar -xvf archive.tar

# Extract tar.gz
tar -xzvf archive.tar.gz

# Extract tar.bz2
tar -xjvf archive.tar.bz2

# Extract tar.xz
tar -xJvf archive.tar.xz

# Extract to specific directory
tar -xzvf archive.tar.gz -C /sdcard/extracted/

# Extract specific file
tar -xzvf archive.tar.gz path/to/file.txt

# Extract with pattern
tar -xzvf archive.tar.gz --wildcards "*.txt"

# ─────────────────────────────────────────────────────────────
# LIST CONTENTS
# ─────────────────────────────────────────────────────────────

# List tar contents
tar -tvf archive.tar

# List tar.gz contents
tar -tzvf archive.tar.gz

# List tar.bz2 contents
tar -tjvf archive.tar.bz2

# List tar.xz contents
tar -tJvf archive.tar.xz

# List with pattern
tar -tzvf archive.tar.gz | grep ".txt"

# ─────────────────────────────────────────────────────────────
# MODIFY ARCHIVES
# ─────────────────────────────────────────────────────────────

# Add file to tar (not compressed tar)
tar -rvf archive.tar newfile.txt

# Update file in tar
tar -uvf archive.tar modified.txt

# Delete from tar (requires GNU tar)
tar --delete -f archive.tar unwanted.txt

# ─────────────────────────────────────────────────────────────
# ADVANCED OPTIONS
# ─────────────────────────────────────────────────────────────

# Preserve permissions
tar -czvpf archive.tar.gz folder/

# Preserve ownership
tar -czvf archive.tar.gz --owner=user --group=group folder/

# Show totals
tar -czvf archive.tar.gz folder/ --totals

# Verify after creation
tar -czvWf archive.tar.gz folder/

# Use compression level (with external gzip)
GZIP=-9 tar -czvf archive.tar.gz folder/

# Create incremental backup
tar -czvf backup.tar.gz --listed-incremental=backup.snar folder/

# Differential backup
tar -czvf diff.tar.gz --listed-incremental=backup.snar folder/
```

### GZIP Commands

```bash
# ═══════════════════════════════════════════════════════════════
# GZIP - COMPRESSION
# ═══════════════════════════════════════════════════════════════

# Install gzip
pkg install gzip -y

# Compress file (removes original)
gzip file.txt
# Output: file.txt.gz

# Compress but keep original
gzip -k file.txt

# Compress with specific level (1-9)
gzip -9 file.txt    # Best compression
gzip -1 file.txt    # Fastest
gzip -6 file.txt    # Default

# Compress multiple files
gzip file1.txt file2.txt file3.txt

# Compress with verbose
gzip -v file.txt

# Force compression
gzip -f file.txt

# Compress and rename
gzip -c file.txt > compressed.gz

# Append to existing archive
gzip -c file.txt >> existing.gz

# ─────────────────────────────────────────────────────────────
# GZIP - DECOMPRESSION
# ─────────────────────────────────────────────────────────────

# Decompress
gunzip file.txt.gz

# Decompress with gzip -d
gzip -d file.txt.gz

# Decompress but keep original
gunzip -k file.txt.gz

# Decompress with verbose
gunzip -v file.txt.gz

# Force decompress
gunzip -f file.txt.gz

# Decompress to stdout
gzip -dc file.txt.gz > file.txt

# ─────────────────────────────────────────────────────────────
# GZIP - TESTING & VIEWING
# ─────────────────────────────────────────────────────────────

# Test integrity
gzip -t file.txt.gz

# View compressed content
zcat file.txt.gz

# View with less
zless file.txt.gz

# View with more
zmore file.txt.gz

# Compare compressed files
zcmp file1.txt.gz file2.txt.gz

# Diff compressed files
zdiff file1.txt.gz file2.txt.gz

# Grep in compressed file
zgrep "pattern" file.txt.gz

# ─────────────────────────────────────────────────────────────
# GZIP - ADVANCED
# ─────────────────────────────────────────────────────────────

# Compress with custom suffix
gzip -S .compressed file.txt

# Decompress custom suffix
gzip -d -S .compressed file.txt.compressed

# Show compression info
gzip -l file.txt.gz

# Recursive compress (files only)
gzip -r folder/

# Get number of compressed blocks
gzip -l file.txt.gz
```

### BZIP2 Commands

```bash
# ═══════════════════════════════════════════════════════════════
# BZIP2 - COMPRESSION
# ═══════════════════════════════════════════════════════════════

# Install bzip2
pkg install bzip2 -y

# Compress file
bzip2 file.txt
# Output: file.txt.bz2

# Compress but keep original
bzip2 -k file.txt

# Compression level (1-9)
bzip2 -9 file.txt    # Best compression (900K memory)
bzip2 -1 file.txt    # Fastest (100K memory)

# Compress with verbose
bzip2 -v file.txt

# Force compression
bzip2 -f file.txt

# Compress to stdout
bzip2 -c file.txt > file.bz2

# ─────────────────────────────────────────────────────────────
# BZIP2 - DECOMPRESSION
# ─────────────────────────────────────────────────────────────

# Decompress
bunzip2 file.txt.bz2

# Or use bzip2 -d
bzip2 -d file.txt.bz2

# Keep original after decompress
bunzip2 -k file.txt.bz2

# Decompress with verbose
bunzip2 -v file.txt.bz2

# ─────────────────────────────────────────────────────────────
# BZIP2 - TESTING & VIEWING
# ─────────────────────────────────────────────────────────────

# Test integrity
bzip2 -t file.txt.bz2

# View content
bzcat file.txt.bz2

# View with less
bzless file.txt.bz2

# ─────────────────────────────────────────────────────────────
# BZIP2 - RECOVERY
# ─────────────────────────────────────────────────────────────

# Recover from damaged archive
bzip2recover file.txt.bz2
# Creates: rec00001file.txt.bz2, rec00002file.txt.bz2, etc.
```

### XZ Commands

```bash
# ═══════════════════════════════════════════════════════════════
# XZ - COMPRESSION
# ═══════════════════════════════════════════════════════════════

# Install xz
pkg install xz -y

# Compress file
xz file.txt
# Output: file.txt.xz

# Compress but keep original
xz -k file.txt

# Compression level (0-9)
xz -0 file.txt    # No compression, fast
xz -6 file.txt    # Default
xz -9 file.txt    # Best compression

# Extreme compression
xz -9e file.txt

# Ultra compression (very slow)
xz -9e --lzma2=dict=512MiB file.txt

# Fast mode
xz -1 file.txt

# Multi-threaded compression
xz -T4 file.txt    # Use 4 threads

# Use all CPU cores
xz -T0 file.txt

# Compress with verbose
xz -v file.txt

# Force compression
xz -f file.txt

# Compress to stdout
xz -c file.txt > file.xz

# ─────────────────────────────────────────────────────────────
# XZ - DECOMPRESSION
# ─────────────────────────────────────────────────────────────

# Decompress
unxz file.txt.xz

# Or use xz -d
xz -d file.txt.xz

# Keep original
unxz -k file.txt.xz

# Decompress to stdout
xz -dc file.txt.xz > file.txt

# ─────────────────────────────────────────────────────────────
# XZ - TESTING & VIEWING
# ─────────────────────────────────────────────────────────────

# Test integrity
xz -t file.txt.xz

# View content
xzcat file.txt.xz

# Show info
xz -l file.txt.xz

# ─────────────────────────────────────────────────────────────
# XZ - UTILITIES
# ┐────────────────────────────────────────────────────────────

# Create LZMA format
xz -F lzma file.txt

# Create raw stream
xz -F raw file.txt

# Dictionary size
xz --lzma2=dict=64MiB file.txt
```

### 7-Zip Commands

```bash
# ═══════════════════════════════════════════════════════════════
# 7-ZIP - COMPRESSION
# ═══════════════════════════════════════════════════════════════

# Install p7zip
pkg install p7zip -y

# Create 7z archive
7z a archive.7z folder/

# Create with files
7z a archive.7z file1.txt file2.txt

# Maximum compression
7z a -t7z -mx=9 archive.7z folder/

# Fast compression
7z a -t7z -mx=1 archive.7z folder/

# Specific compression method
7z a -t7z -m0=lzma2 archive.7z folder/

# Multi-threaded
7z a -mmt=on archive.7z folder/

# Use specific number of threads
7z a -mmt=4 archive.7z folder/

# Create ZIP with 7z
7z a -tzip archive.zip folder/

# Create TAR
7z a -ttar archive.tar folder/

# ─────────────────────────────────────────────────────────────
# 7-ZIP - PASSWORD PROTECTION
# ─────────────────────────────────────────────────────────────

# Password protect (interactive)
7z a -p archive.7z folder/

# Password on command line
7z a -pMyPassword archive.7z secret.txt

# Encrypt filenames also
7z a -pMyPassword -mhe=on archive.7z folder/

# ─────────────────────────────────────────────────────────────
# 7-ZIP - EXTRACTION
# ─────────────────────────────────────────────────────────────

# Extract
7z x archive.7z

# Extract to specific directory
7z x archive.7z -o/sdcard/extracted/

# Extract with full paths
7z x archive.7z

# Extract to current directory (no paths)
7z e archive.7z

# Extract with password
7z x -pMyPassword archive.7z

# Extract specific files
7z x archive.7z file1.txt file2.txt

# Extract with pattern
7z x archive.7z *.txt -r

# Overwrite all
7z x archive.7z -aoa

# Skip existing
7z x archive.7z -aos

# Rename if exists
7z x archive.7z -aou

# ─────────────────────────────────────────────────────────────
# 7-ZIP - LISTING & TESTING
# ─────────────────────────────────────────────────────────────

# List contents
7z l archive.7z

# List with details
7z l -slt archive.7z

# Test archive
7z t archive.7z

# Test with password
7z t -pMyPassword archive.7z

# ─────────────────────────────────────────────────────────────
# 7-ZIP - SPLIT ARCHIVES
# ─────────────────────────────────────────────────────────────

# Create split archive (50MB each)
7z a -v50m archive.7z bigfile.iso

# Extract split archive
7z x archive.7z.001

# ─────────────────────────────────────────────────────────────
# 7-ZIP - ADVANCED
# ─────────────────────────────────────────────────────────────

# Update archive
7z u archive.7z newfile.txt

# Delete from archive
7z d archive.7z unwanted.txt

# Rename in archive
7z rn archive.7z oldname.txt newname.txt

# Benchmark
7z b

# Calculate hash
7z h file.txt

# Show supported formats
7z i
```

### RAR Commands

```bash
# ═══════════════════════════════════════════════════════════════
# RAR - EXTRACTION (UNRAR)
# ═══════════════════════════════════════════════════════════════

# Install unrar
pkg install unrar -y

# Extract all
unrar x archive.rar

# Extract to specific directory
unrar x archive.rar /sdcard/extracted/

# Extract to current directory
unrar e archive.rar

# List contents
unrar l archive.rar

# List with technical info
unrar lt archive.rar

# Test archive
unrar t archive.rar

# Extract with password
unrar x -pMyPassword archive.rar

# Extract specific file
unrar x archive.rar file.txt

# Extract with pattern
unrar x archive.rar *.txt

# Verbose extraction
unrar v archive.rar

# Keep broken files
unrar x -kb archive.rar

# Freshen files (update only)
unrar f archive.rar

# Repair archive
unrar r archive.rar

# Lock archive (prevent modification)
# Note: unrar cannot lock, need rar tool

# Show comments
unrar c archive.rar

# Disable comments
unrar x -c- archive.rar
```

### Additional Utility Commands

```bash
# ═══════════════════════════════════════════════════════════════
# FILE TYPE DETECTION
# ═══════════════════════════════════════════════════════════════

# Identify file type
file archive.zip
file archive.tar.gz
file archive.7z

# Check magic bytes
xxd archive.zip | head -1
# ZIP: 50 4b 03 04
# GZIP: 1f 8b
# BZIP2: 42 5a 68
# XZ: fd 37 7a 58 5a 00
# 7Z: 37 7a bc af 27 1c
# RAR: 52 61 72 21

# ═══════════════════════════════════════════════════════════════
# SIZE COMPARISON
# ═══════════════════════════════════════════════════════════════

# Show file sizes
ls -lh archive.*

# Compare compression
du -sh folder/
du -sh archive.tar.gz
du -sh archive.tar.bz2
du -sh archive.tar.xz
du -sh archive.7z

# ═══════════════════════════════════════════════════════════════
# BATCH OPERATIONS
# ═══════════════════════════════════════════════════════════════

# Compress all .txt files
for f in *.txt; do gzip "$f"; done

# Compress each folder to separate archive
for dir in */; do
    zip -r "${dir%/}.zip" "$dir"
done

# Extract all .zip files
for f in *.zip; do
    unzip "$f" -d "${f%.zip}"
done

# Find and compress old logs
find . -name "*.log" -mtime +30 -exec gzip {} \;

# Batch convert tar.gz to tar.xz
for f in *.tar.gz; do
    gunzip -c "$f" | xz > "${f%.gz}.xz"
done
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Compression

```bash
# Task: Learn basic compression operations

# Step 1: Create test directory and files
mkdir -p ~/compression-test
cd ~/compression-test
echo "This is file 1" > file1.txt
echo "This is file 2" > file2.txt
echo "This is file 3" > file3.txt
mkdir subdir
echo "Subdir content" > subdir/subfile.txt

# Step 2: Create ZIP archive
zip -r test.zip file1.txt file2.txt file3.txt subdir/

# Step 3: List contents
unzip -l test.zip

# Step 4: Extract to new directory
mkdir extracted
unzip test.zip -d extracted/

# Step 5: Verify
ls -la extracted/

# Step 6: Clean up
rm -rf extracted test.zip
```

### Exercise 2: TAR Archives

```bash
# Task: Master TAR compression

# Step 1: Create sample project
mkdir -p ~/myproject/{src,docs,config}
echo "print('Hello')" > ~/myproject/src/main.py
echo "# Documentation" > ~/myproject/docs/README.md
echo "setting=value" > ~/myproject/config/settings.conf

# Step 2: Create TAR.GZ
tar -czvf project.tar.gz ~/myproject/

# Step 3: Create TAR.BZ2
tar -cjvf project.tar.bz2 ~/myproject/

# Step 4: Create TAR.XZ
tar -cJvf project.tar.xz ~/myproject/

# Step 5: Compare sizes
ls -lh project.tar.*

# Step 6: Extract and verify
mkdir test_extract
tar -xzvf project.tar.gz -C test_extract/
ls -la test_extract/

# Step 7: Clean up
rm -rf test_extract project.tar.*
```

### Exercise 3: Password Protected Archives

```bash
# Task: Create secure archives

# Step 1: Create sensitive file
echo "Confidential data: password123" > secret.txt

# Step 2: Create password ZIP
zip -e secure.zip secret.txt
# Enter password when prompted

# Step 3: Create password 7z (with hidden filenames)
7z a -p -mhe=on secure.7z secret.txt
# Enter password when prompted

# Step 4: Test extraction
rm secret.txt
unzip secure.zip    # Will ask for password
7z x secure.7z      # Will ask for password

# Step 5: Verify
cat secret.txt

# Step 6: Clean up
rm -f secret.txt secure.zip secure.7z
```

### Exercise 4: Split Archives

```bash
# Task: Create and handle split archives

# Step 1: Create a large file
dd if=/dev/zero of=largefile.bin bs=1M count=10

# Step 2: Split with 7z
7z a -v2m split.7z largefile.bin

# Step 3: List parts
ls -la split.7z.*

# Step 4: Combine and extract
7z x split.7z.001

# Step 5: Verify
ls -la largefile.bin

# Step 6: Alternative - split command
split -b 2M largefile.bin part_

# List parts
ls -la part_*

# Combine back
cat part_* > combined.bin
diff largefile.bin combined.bin  # Should show no difference

# Step 7: Clean up
rm -f largefile.bin split.7z.* part_* combined.bin
```

### Exercise 5: Automated Backup Script

```bash
# Task: Create automated backup system

# Step 1: Create backup script
cat > ~/backup.sh << 'EOF'
#!/bin/bash

# Configuration
BACKUP_DIR="/sdcard/backups"
SOURCE_DIRS=("$HOME" "/sdcard/documents")
DATE=$(date +%Y%m%d_%H%M%S)
LOG_FILE="$BACKUP_DIR/backup.log"

# Create backup directory
mkdir -p "$BACKUP_DIR"

# Log function
log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOG_FILE"
}

log "Starting backup..."

# Create backup for each source
for src in "${SOURCE_DIRS[@]}"; do
    if [ -d "$src" ]; then
        name=$(basename "$src")
        archive="$BACKUP_DIR/${name}_${DATE}.tar.gz"
        
        log "Backing up: $src"
        tar -czvf "$archive" "$src" 2>/dev/null
        
        if [ $? -eq 0 ]; then
            size=$(du -h "$archive" | cut -f1)
            log "Created: $archive ($size)"
        else
            log "ERROR: Failed to backup $src"
        fi
    else
        log "WARNING: Source not found: $src"
    fi
done

# Cleanup old backups (keep last 7 days)
log "Cleaning old backups..."
find "$BACKUP_DIR" -name "*.tar.gz" -mtime +7 -delete

log "Backup complete!"
EOF

# Step 2: Make executable
chmod +x ~/backup.sh

# Step 3: Create test source
mkdir -p /sdcard/documents
echo "Important document" > /sdcard/documents/doc.txt

# Step 4: Run backup
~/backup.sh

# Step 5: Verify
ls -la /sdcard/backups/
cat /sdcard/backups/backup.log

# Step 6: Extract test
cd /sdcard/backups
tar -tzf *.tar.gz | head
```

### Exercise 6: Compression Benchmark

```bash
# Task: Compare compression methods

# Step 1: Create test file
mkdir -p ~/benchmark
cd ~/benchmark

# Create a log-style file (compresses well)
for i in {1..10000}; do
    echo "$(date) - Log entry $i - Some text data here"
done > testfile.log

# Check original size
echo "Original size:"
du -h testfile.log

# Step 2: Test GZIP
echo -e "\n=== GZIP ==="
time gzip -k -9 testfile.log
du -h testfile.log.gz

# Step 3: Test BZIP2
echo -e "\n=== BZIP2 ==="
time bzip2 -k -9 testfile.log
du -h testfile.log.bz2

# Step 4: Test XZ
echo -e "\n=== XZ ==="
time xz -k -9 testfile.log
du -h testfile.log.xz

# Step 5: Test 7Z
echo -e "\n=== 7Z ==="
time 7z a -t7z -mx=9 testfile.7z testfile.log
du -h testfile.7z

# Step 6: Summary
echo -e "\n=== SUMMARY ==="
ls -lh testfile.*

# Step 7: Clean up
rm -f testfile.log.gz testfile.log.bz2 testfile.log.xz testfile.7z
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "command not found" for zip/unzip

```bash
# Cause: Package not installed

# Solution:
pkg install zip unzip -y

# Verify:
which zip
which unzip
```

### Problem 2: "Permission denied" when extracting

```bash
# Cause: No write permission in target directory

# Solution 1: Extract to different location
unzip archive.zip -d ~/output/

# Solution 2: Check directory permissions
ls -la /target/directory/

# Solution 3: Use different directory
mkdir -p ~/extracted
unzip archive.zip -d ~/extracted/
```

### Problem 3: "No space left on device"

```bash
# Cause: Not enough storage

# Check disk space:
df -h

# Check Termux home space:
du -sh ~

# Solution 1: Clean cache
pkg clean
rm -rf $PREFIX/var/cache/apt/archives/*.deb

# Solution 2: Remove old archives
find ~ -name "*.tar.gz" -mtime +30 -delete

# Solution 3: Extract to external storage
unzip archive.zip -d /sdcard/extracted/
```

### Problem 4: Corrupted ZIP file

```bash
# Symptoms: "unzip: cannot find or open file"

# Solution 1: Test archive
unzip -t archive.zip

# Solution 2: Try to fix
zip -FF archive.zip --out fixed.zip
unzip fixed.zip

# Solution 3: Extract what's possible
unzip -v archive.zip  # List files
unzip archive.zip -x broken_file.txt  # Skip broken file

# Solution 4: Use 7z for recovery
7z x archive.zip -aoa  # Continue on errors
```

### Problem 5: "Can't replace" errors in unzip

```bash
# Cause: File already exists

# Solution 1: Force overwrite
unzip -o archive.zip

# Solution 2: Skip existing
unzip -n archive.zip

# Solution 3: Rename existing
unzip archive.zip
# When prompted: enter 'r' to rename
```

### Problem 6: Password not working

```bash
# Cause: Wrong password or encoding issue

# Solution 1: Make sure password is correct
# Type carefully, check caps lock

# Solution 2: For 7z with encrypted filenames
7z l -p archive.7z  # Test password

# Solution 3: Try different encoding
unzip -O UTF-8 archive.zip    # Force UTF-8
unzip -O CP1252 archive.zip   # Try Windows encoding
```

### Problem 7: TAR not preserving permissions

```bash
# Cause: Missing flags or filesystem limitations

# Solution 1: Use -p flag
tar -czvpf archive.tar.gz folder/

# Solution 2: For FAT filesystems (external storage)
# Note: FAT doesn't support Unix permissions
# Files will have default permissions after extraction

# Solution 3: Store permissions separately
tar -czvf archive.tar.gz folder/
tar -tzvf archive.tar.gz  # Verify permissions in archive
```

### Problem 8: Split archive parts missing

```bash
# Cause: Incomplete download or transfer

# Solution 1: Check all parts exist
ls -la archive.7z.*

# Solution 2: For ZIP, combine first
cat archive.z* > combined.zip
unzip combined.zip

# Solution 3: For 7z, missing parts will cause error
7z x archive.7z.001
# If parts missing, extraction will fail

# Solution 4: Use par2 for recovery (if parity files exist)
pkg install par2
par2 r archive.par2
```

### Problem 9: Very slow XZ compression

```bash
# Cause: High compression level on large files

# Solution 1: Use lower compression level
xz -1 file.txt    # Fast but larger

# Solution 2: Use multi-threading
xz -T0 file.txt   # Use all cores

# Solution 3: Use faster algorithm
gzip -9 file.txt  # Faster than xz

# Solution 4: Compare and choose
time xz -1 file.txt
time gzip -9 file.txt
```

### Problem 10: Can't extract RAR files

```bash
# Cause: unrar not installed or RAR5 format

# Solution 1: Install unrar
pkg install unrar -y

# Solution 2: Check RAR version
unrar l archive.rar
# If RAR5, you need newer unrar

# Solution 3: Use 7z (supports some RAR)
7z x archive.rar

# Solution 4: For RAR5, might need newer p7zip
pkg install p7zip -y
7z x archive.rar
```

### Problem 11: TAR recursive issues

```bash
# Cause: Symlinks or special files

# Solution 1: Follow symlinks
tar -czvhf archive.tar.gz folder/

# Solution 2: Exclude symlinks
tar -czvf archive.tar.gz --exclude='*' --no-recursion folder/

# Solution 3: Handle special files
tar -czvf archive.tar.gz --acls --xattrs folder/

# Solution 4: One filesystem only
tar -czvf archive.tar.gz --one-file-system folder/
```

### Problem 12: Memory issues with large archives

```bash
# Cause: Not enough RAM for compression

# Solution 1: Use less memory-intensive method
bzip2 -1 file.txt    # Uses less memory than xz

# Solution 2: Split large file first
split -b 100M largefile.bin part_
for f in part_*; do gzip "$f"; done

# Solution 3: Use tar with -L for tape length
tar -czf - folder/ | split -b 100M - archive.tar.gz.

# Solution 4: Check memory usage
free -h
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Tool Comparison**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📦 FILE COMPRESSION              │
│   ────────────────────────────     │
│   ZIP │ TAR │ GZIP │ 7Z │ RAR      │
│                                    │
│   Which is BEST?                   │
│   🔥 COMPLETE GUIDE 🔥             │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Compression Ratio**
```
┌────────────────────────────────────┐
│  [Comparison Visual]               │
│                                    │
│   100MB                            │
│   ━━━━━━━━━━━━━━━━━━━━━━           │
│                                    │
│   ZIP:    35MB ━━━━━━━             │
│   GZIP:   32MB ━━━━━━              │
│   7Z:     22MB ━━━━                │
│   XZ:     20MB ━━━                 │
│                                    │
│   Chapter 40 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Command Focus**
```
┌────────────────────────────────────┐
│  [Green on Black]                  │
│                                    │
│   $ tar -czvf backup.tar.gz        │
│   $ zip -r project.zip folder/     │
│   $ 7z a -p secure.7z secret/      │
│                                    │
│   📚 25+ COMMANDS                  │
│   🔐 PASSWORD PROTECTION           │
│   ⚡ BATCH OPERATIONS              │
│                                    │
│   [T3rmuxk1ng]                     │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📦 Termux Full Course - Chapter 40: File Compression & Archives

🔥 In this video you'll learn:
• ZIP & UNZIP commands complete guide
• TAR archives - create, extract, list
• GZIP, BZIP2, XZ compression tools
• 7-Zip maximum compression
• RAR extraction with unrar
• Password protected archives
• Split archives for large files
• Batch compression automation
• Automated backup scripts
• Archive testing & recovery

⏱️ Timestamps:
0:00 - Introduction
0:45 - Compression Basics
3:00 - ZIP & UNZIP Commands
6:00 - TAR Command Complete
9:00 - GZIP, BZIP2, XZ Tools
12:00 - 7-Zip & RAR Support
14:30 - Compression Comparison
15:30 - Advanced Features (Split, Batch, Backup)
17:30 - Summary

📝 Commands from this video:

# Install packages
pkg install zip unzip tar gzip bzip2 xz p7zip unrar -y

# Create archives
zip -r backup.zip folder/
tar -czvf archive.tar.gz folder/
7z a archive.7z folder/

# Extract archives
unzip backup.zip
tar -xzvf archive.tar.gz
7z x archive.7z

# Password protection
zip -e secure.zip secret.txt
7z a -p -mhe=on secure.7z folder/

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #FileCompression #T3rmuxk1ng #ZipUnzip #TarCommand #LinuxCommands #TermuxTutorial #HindiTutorial

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux, file compression, zip unzip, tar command, gzip, bzip2, xz, 
7zip, 7z, rar unrar, archive, compression tools, termux compression,
linux compression, tar gz, tar bz2, tar xz, password protection,
split archive, batch compression, backup automation, termux tutorial,
termux hindi, t3rmuxk1ng, termux course, linux commands, 
file archiving, data compression, termux utilities, android terminal
```

### Hashtags

```
#Termux #FileCompression #ZipUnzip #TarCommand #LinuxCommands 
#TermuxTutorial #TermuxHindi #DataCompression #ArchiveTools 
#T3rmuxk1ng #TermuxCourse #AndroidTerminal #LinuxOnAndroid 
#CompressionTools #BackupAutomation
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| GNU TAR Manual | https://www.gnu.org/software/tar/manual/ |
| ZIP Manual | `man zip` in Termux |
| 7-Zip Documentation | https://www.7-zip.org/documentation.html |
| GZIP Manual | `man gzip` in Termux |

### Quick Reference Cards

```bash
# ZIP Quick Reference
zip -r archive.zip folder/          # Create
unzip archive.zip                   # Extract
unzip -l archive.zip                # List
unzip -t archive.zip                # Test

# TAR Quick Reference
tar -czvf file.tar.gz folder/       # Create GZIP
tar -xzvf file.tar.gz               # Extract GZIP
tar -cjvf file.tar.bz2 folder/      # Create BZIP2
tar -xjvf file.tar.bz2              # Extract BZIP2
tar -cJvf file.tar.xz folder/       # Create XZ
tar -xJvf file.tar.xz               # Extract XZ
tar -tvf file.tar.gz                # List

# GZIP Quick Reference
gzip file.txt                       # Compress
gunzip file.txt.gz                  # Decompress
gzip -k file.txt                    # Keep original
zcat file.txt.gz                    # View content

# 7-Zip Quick Reference
7z a archive.7z folder/             # Create
7z x archive.7z                     # Extract
7z l archive.7z                     # List
7z t archive.7z                     # Test
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 41, verify:

- [ ] Installed all compression packages (zip, unzip, tar, gzip, bzip2, xz, p7zip, unrar)
- [ ] Can create and extract ZIP files
- [ ] Understand TAR with different compressions (gz, bz2, xz)
- [ ] Can use GZIP, BZIP2, XZ for single file compression
- [ ] Know how to create password protected archives
- [ ] Understand compression level tradeoffs
- [ ] Can create split archives
- [ ] Written a basic backup script
- [ ] Know how to test and repair corrupted archives

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 41: Image & Media Tools**

- ImageMagick installation and basics
- Image format conversion
- Resizing and cropping images
- Bulk image processing
- Adding watermarks
- Screenshot capture in Termux
- Video thumbnails with ffmpeg
- PDF from images

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 💡 PRO TIPS BOX (10 Advanced Tips)

> 💡 **Pro Tip #1:** Use `tar -czvf` for creating archives and `tar -xzvf` for extracting - the pattern is easy to remember: **c**reate, e**x**tract, **z**ip (gzip), **v**erbose, **f**ile.

> 💡 **Pro Tip #2:** For maximum compression with 7z, use `7z a -t7z -mx=9 -m0=lzma2 -md=64M` - this uses LZMA2 algorithm with 64MB dictionary for best results.

> 💡 **Pro Tip #3:** When extracting tar files, always use `tar -xvf file.tar --one-top-level` to extract into a subdirectory automatically - prevents file clutter!

> 💡 **Pro Tip #4:** Use `zip -r archive.zip folder/ -x "*.git*"` to exclude hidden git directories when archiving projects.

> 💡 **Pro Tip #5:** For splitting large files, use `split -b 100M largefile.iso part_` then combine with `cat part_* > largefile.iso`.

> 💡 **Pro Tip #6:** Test archive integrity before deleting originals: `unzip -t archive.zip` or `7z t archive.7z` - saves you from corrupted backups!

> 💡 **Pro Tip #7:** Use `tar -czvf - folder/ | gpg -c > encrypted.tar.gz.gpg` to create encrypted archives without intermediate files.

> 💡 **Pro Tip #8:** For incremental backups, use `tar -czvf backup.tar.gz --newer-mtime="2024-01-01" folder/` to only archive changed files.

> 💡 **Pro Tip #9:** Use `pigz` instead of `gzip` for parallel compression on multi-core devices - much faster for large files!

> 💡 **Pro Tip #10:** Archive timestamps matter! Use `tar --mtime='2024-01-01 00:00:00'` for reproducible builds.

---

## 🔥 REAL WORLD USE CASES

### Use Case 1: Automated Backup System

```bash
#!/bin/bash
# Daily Backup Script - Add to cron

BACKUP_DIR="/sdcard/Backups"
DATE=$(date +%Y%m%d_%H%M%S)
SOURCE="$HOME/projects"

mkdir -p "$BACKUP_DIR"

# Create compressed backup
tar -czvf "$BACKUP_DIR/projects_$DATE.tar.gz" \
    --exclude='*.log' \
    --exclude='node_modules' \
    --exclude='.git' \
    "$SOURCE"

# Keep only last 7 backups
ls -t "$BACKUP_DIR"/projects_*.tar.gz | tail -n +8 | xargs rm -f 2>/dev/null

# Verify backup
if tar -tzf "$BACKUP_DIR/projects_$DATE.tar.gz" > /dev/null 2>&1; then
    echo "Backup verified: projects_$DATE.tar.gz"
else
    echo "Backup FAILED!"
fi
```

### Use Case 2: Project Distribution

```bash
#!/bin/bash
# Create distributable project archive

PROJECT_NAME="myapp"
VERSION="1.0.0"
OUTPUT="${PROJECT_NAME}-v${VERSION}.tar.gz"

# Clean and create release archive
tar -czvf "$OUTPUT" \
    --exclude='*.log' \
    --exclude='*.tmp' \
    --exclude='.env' \
    --exclude='node_modules' \
    --exclude='.git' \
    --transform "s,^,${PROJECT_NAME}/," \
    *

echo "Created: $OUTPUT"
```

### Use Case 3: Secure File Transfer

```bash
#!/bin/bash
# Secure archive with encryption

SOURCE="confidential/"
OUTPUT="secure_backup.tar.gz.gpg"

# Create and encrypt in one command
tar -czvf - "$SOURCE" | gpg --symmetric --cipher-algo AES256 -o "$OUTPUT"

echo "Encrypted archive created: $OUTPUT"

# Decrypt and extract later:
# gpg -d secure_backup.tar.gz.gpg | tar -xzvf -
```

### Use Case 4: Log Rotation

```bash
#!/bin/bash
# Log rotation and compression

LOG_DIR="/var/log/myapp"
ARCHIVE_DIR="$LOG_DIR/archive"

mkdir -p "$ARCHIVE_DIR"

# Compress logs older than 7 days
find "$LOG_DIR" -name "*.log" -mtime +7 -exec gzip {} \;

# Move compressed logs to archive
find "$LOG_DIR" -name "*.log.gz" -exec mv {} "$ARCHIVE_DIR/" \;

# Remove archives older than 30 days
find "$ARCHIVE_DIR" -name "*.log.gz" -mtime +30 -delete
```

### Productivity Hacks

| Task | Command | Time Saved |
|------|---------|------------|
| Quick backup | `tar -czvf backup.tar.gz folder/` | 2 minutes |
| Exclude files | `zip -r arch.zip dir/ -x "*.tmp"` | 5 minutes |
| Verify archive | `unzip -t archive.zip` | Prevents disaster |
| Split large file | `split -b 100M largefile part_` | Enables sharing |
| Compare archives | `diff <(tar -tf a.tar) <(tar -tf b.tar)` | Quick comparison |

### Daily Automation Ideas

1. **Automatic Code Backup** - Backup code projects every 4 hours
2. **Log Compression** - Compress and archive logs daily
3. **Photo Archive** - Monthly archive of photos with date stamps
4. **Config Backup** - Backup dotfiles before any changes
5. **Database Dump Archive** - Compress database exports automatically

---

## ⚡ QUICK REFERENCE CARD

### ZIP Commands

| Task | Command |
|------|---------|
| Create ZIP | `zip -r archive.zip folder/` |
| Extract ZIP | `unzip archive.zip` |
| Extract to dir | `unzip archive.zip -d output/` |
| List contents | `unzip -l archive.zip` |
| Test integrity | `unzip -t archive.zip` |
| Password protect | `zip -e secure.zip files/` |
| Maximum compression | `zip -9 -r archive.zip folder/` |
| Exclude files | `zip -r arch.zip dir/ -x "*.log"` |

### TAR Commands

| Task | Command |
|------|---------|
| Create tar.gz | `tar -czvf archive.tar.gz folder/` |
| Extract tar.gz | `tar -xzvf archive.tar.gz` |
| Create tar.bz2 | `tar -cjvf archive.tar.bz2 folder/` |
| Extract tar.bz2 | `tar -xjvf archive.tar.bz2` |
| Create tar.xz | `tar -cJvf archive.tar.xz folder/` |
| Extract tar.xz | `tar -xJvf archive.tar.xz` |
| List contents | `tar -tvf archive.tar.gz` |
| Extract specific | `tar -xzvf archive.tar.gz file.txt` |
| Extract to dir | `tar -xzvf archive.tar.gz -C output/` |

### GZIP/BZIP2/XZ Commands

| Task | GZIP | BZIP2 | XZ |
|------|------|-------|-----|
| Compress | `gzip file` | `bzip2 file` | `xz file` |
| Decompress | `gunzip file.gz` | `bunzip2 file.bz2` | `unxz file.xz` |
| Keep original | `gzip -k file` | `bzip2 -k file` | `xz -k file` |
| View content | `zcat file.gz` | `bzcat file.bz2` | `xzcat file.xz` |

### 7Z Commands

| Task | Command |
|------|---------|
| Create archive | `7z a archive.7z folder/` |
| Extract archive | `7z x archive.7z` |
| List contents | `7z l archive.7z` |
| Test integrity | `7z t archive.7z` |
| Password protect | `7z a -p archive.7z folder/` |
| Max compression | `7z a -t7z -mx=9 archive.7z folder/` |
| Split archive | `7z a -v100m archive.7z largefile` |

---

## 🏆 BONUS: POWER USER TIPS

### Advanced Compression Techniques

```bash
# Multi-threaded compression with pigz (faster)
pkg install pigz
tar -cvf - folder/ | pigz -p 4 > archive.tar.gz

# Parallel bzip2 with pbzip2
pkg install pbzip2
tar -cvf - folder/ | pbzip2 > archive.tar.bz2

# Extreme XZ compression (very slow, very small)
xz -9e --threads=4 largefile.iso

# Create self-extracting archive
makeself folder/ archive.run "Description" ./install.sh
```

### Incremental Backup Strategy

```bash
#!/bin/bash
# Incremental backup system

BACKUP_DIR="/sdcard/Backups"
SOURCE="$HOME/important"
DATE=$(date +%Y%m%d)
SNAPSHOT="$BACKUP_DIR/.snapshot"

mkdir -p "$BACKUP_DIR"

# Full backup on Sunday, incremental otherwise
if [ "$(date +%u)" -eq 7 ]; then
    # Full backup
    tar -czvf "$BACKUP_DIR/full_$DATE.tar.gz" "$SOURCE"
    rm -f "$SNAPSHOT"
    touch "$SNAPSHOT"
else
    # Incremental backup
    tar -czvf "$BACKUP_DIR/incr_$DATE.tar.gz" \
        --listed-incremental="$SNAPSHOT" "$SOURCE"
fi
```

### Archive Comparison Script

```bash
#!/bin/bash
# Compare two archives

ARCH1="$1"
ARCH2="$2"

echo "Comparing archives..."

# Extract to temp directories
TMP1=$(mktemp -d)
TMP2=$(mktemp -d)

tar -xzf "$ARCH1" -C "$TMP1"
tar -xzf "$ARCH2" -C "$TMP2"

# Compare
diff -rq "$TMP1" "$TMP2"

# Cleanup
rm -rf "$TMP1" "$TMP2"
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### Key Takeaways

- ✅ **ZIP Format** - Universal compatibility, use `zip`/`unzip` commands
- ✅ **TAR Archives** - Linux standard, use `tar -c` to create, `tar -x` to extract
- ✅ **Compression Types** - GZIP (fast), BZIP2 (balanced), XZ (best compression)
- ✅ **7-Zip** - Highest compression ratio, password protection built-in
- ✅ **RAR Extraction** - Use `unrar x` for RAR files (creation requires paid version)
- ✅ **Password Protection** - `zip -e` or `7z a -p` for encryption
- ✅ **Split Archives** - `zip -s` or `7z -v` for large files
- ✅ **Archive Testing** - Always verify with `unzip -t` or `7z t`
- ✅ **Incremental Backups** - Use `--listed-incremental` for efficient backups
- ✅ **Automation** - Combine with cron for scheduled backups

### Skills Acquired

| Skill | Level |
|-------|-------|
| ZIP Operations | ⭐⭐⭐⭐⭐ |
| TAR Archives | ⭐⭐⭐⭐ |
| Compression Types | ⭐⭐⭐⭐ |
| 7-Zip Advanced | ⭐⭐⭐ |
| Backup Automation | ⭐⭐⭐ |

---

## 🔧 AUTOMATION SCRIPTS

### Ready-to-Use Scripts

**1. Quick Backup Script:**
```bash
#!/bin/bash
# Save as: ~/scripts/quick-backup.sh
SOURCE="${1:-.}"
OUTPUT="backup_$(date +%Y%m%d_%H%M%S).tar.gz"
tar -czvf "$OUTPUT" --exclude='*.log' --exclude='*.tmp' "$SOURCE"
echo "Created: $OUTPUT"
```

**2. Project Archive Script:**
```bash
#!/bin/bash
# Save as: ~/scripts/project-archive.sh
PROJECT="$1"
[ -z "$PROJECT" ] && echo "Usage: $0 <project_dir>" && exit 1
tar -czvf "${PROJECT}_$(date +%Y%m%d).tar.gz" \
    --exclude='node_modules' --exclude='.git' --exclude='*.log' "$PROJECT"
```

**3. Compress All PDFs:**
```bash
#!/bin/bash
# Save as: ~/scripts/compress-pdfs.sh
for pdf in *.pdf; do
    gzip "$pdf"
    echo "Compressed: $pdf → ${pdf}.gz"
done
```

### Cron Job Templates

```bash
# Add to crontab with: crontab -e

# Daily backup at midnight
0 0 * * * tar -czf ~/backups/daily_$(date +\%Y\%m\%d).tar.gz ~/projects

# Weekly backup on Sunday
0 2 * * 0 tar -czf ~/backups/weekly_$(date +\%Y\%m\%d).tar.gz ~/important

# Monthly cleanup - delete old backups
0 3 1 * * find ~/backups -name "*.tar.gz" -mtime +30 -delete
```

---

## 🚀 WORKFLOW OPTIMIZATION

### Speed Up Daily Tasks

| Task | Slow Way | Fast Way |
|------|----------|----------|
| Compress folder | Open app → Select → Compress | `tar -czvf out.tar.gz folder/` |
| Extract archive | Open app → Extract | `tar -xzvf archive.tar.gz` |
| Verify backup | Hope for the best | `unzip -t archive.zip` |
| Split file | Use splitter app | `split -b 100M file part_` |
| Compare archives | Extract both manually | `diff <(tar -tf a.tar) <(tar -tf b.tar)` |

### Efficiency Tips

1. **Use Aliases** - Add to `.bashrc`:
   ```bash
   alias backup='tar -czvf backup_$(date +%Y%m%d).tar.gz'
   alias extract='tar -xzvf'
   alias zipit='zip -r archive.zip'
   ```

2. **Use Tab Completion** - Most shells complete archive names

3. **Use Archive Extensions** - Let the extension guide extraction:
   ```bash
   extract() {
       case "$1" in
           *.tar.gz) tar -xzvf "$1" ;;
           *.tar.bz2) tar -xjvf "$1" ;;
           *.tar.xz) tar -xJvf "$1" ;;
           *.zip) unzip "$1" ;;
           *.7z) 7z x "$1" ;;
           *.rar) unrar x "$1" ;;
       esac
   }
   ```

4. **Use Compression Levels** - `-1` for speed, `-9` for size

5. **Exclude Patterns** - Use `--exclude` or `-x` to skip unwanted files

---

## 📊 COMPARISON TABLES

### Compression Format Comparison

| Format | Speed | Compression | CPU Usage | Compatibility |
|--------|-------|-------------|-----------|---------------|
| ZIP | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | Low | Universal |
| GZIP | ⭐⭐⭐⭐ | ⭐⭐⭐ | Medium | Unix/Linux |
| BZIP2 | ⭐⭐⭐ | ⭐⭐⭐⭐ | High | Unix/Linux |
| XZ | ⭐ | ⭐⭐⭐⭐⭐ | Very High | Linux |
| 7Z | ⭐⭐ | ⭐⭐⭐⭐⭐ | High | Windows/Linux |
| RAR | ⭐⭐ | ⭐⭐⭐⭐ | Medium | Windows/Linux |

### When to Use What

| Scenario | Recommended Format | Reason |
|----------|-------------------|--------|
| Sharing with Windows users | ZIP | Universal support |
| Linux server backup | TAR.GZ | Unix standard |
| Maximum compression needed | XZ or 7Z | Smallest files |
| Password protection | 7Z or ZIP | Built-in encryption |
| Fast compression needed | GZIP | Best speed/size ratio |
| Archiving source code | TAR.GZ or TAR.XZ | Preserves permissions |
| Large file splitting | 7Z | Built-in split support |

### Compression Ratio Examples

| File Type | Original | ZIP | GZIP | BZIP2 | XZ | 7Z |
|-----------|----------|-----|------|-------|-----|-----|
| Text (10MB) | 10 MB | 3 MB | 2.8 MB | 2.2 MB | 1.8 MB | 1.7 MB |
| Code (50MB) | 50 MB | 12 MB | 11 MB | 9 MB | 7 MB | 6.5 MB |
| Image (5MB) | 5 MB | 4.8 MB | 4.7 MB | 4.6 MB | 4.5 MB | 4.4 MB |
| Video (100MB) | 100 MB | 98 MB | 97 MB | 96 MB | 95 MB | 94 MB |

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relationship |
|---------|-------|--------------|
| Ch39 | YouTube Downloaders | Compress downloaded videos |
| Ch41 | Image/Media Tools | Compress processed images |
| Ch42 | PDF Tools | Archive PDF collections |
| Ch43 | Task Automation | Schedule automated backups |
| Ch44 | Termux Widgets | Widget-triggered backups |
| Ch45 | SSH Server | Transfer compressed archives |

---

## 🎮 INTERACTIVE QUIZ

### Test Your Knowledge (10 Questions)

**Q1:** Which command creates a gzip-compressed tar archive?
- A) `tar -czvf archive.tar folder/`
- B) `tar -czvf archive.tar.gz folder/`
- C) `tar -xzvf archive.tar.gz folder/`
- D) `gzip -c archive.tar folder/`

**Q2:** What does the `-j` flag do in tar?
- A) Use gzip compression
- B) Use bzip2 compression
- C) Use xz compression
- D) Use zip compression

**Q3:** How do you extract a RAR file?
- A) `rar x archive.rar`
- B) `unrar x archive.rar`
- C) `unzip archive.rar`
- D) `tar -xvf archive.rar`

**Q4:** Which format offers the best compression ratio?
- A) ZIP
- B) GZIP
- C) XZ
- D) BZIP2

**Q5:** How do you create a password-protected ZIP file interactively?
- A) `zip -p archive.zip files/`
- B) `zip -e archive.zip files/`
- C) `zip --password archive.zip files/`
- D) `zip -secure archive.zip files/`

**Q6:** What command tests a ZIP archive's integrity?
- A) `zip -t archive.zip`
- B) `unzip -t archive.zip`
- C) `test archive.zip`
- D) `check archive.zip`

**Q7:** Which flag keeps the original file when compressing with gzip?
- A) `-k`
- B) `-c`
- C) `-p`
- D) `-o`

**Q8:** How do you exclude files when creating a tar archive?
- A) `tar -czvf arch.tar.gz --ignore "*.log" folder/`
- B) `tar -czvf arch.tar.gz --exclude "*.log" folder/`
- C) `tar -czvf arch.tar.gz -x "*.log" folder/`
- D) `tar -czvf arch.tar.gz --skip "*.log" folder/`

**Q9:** What does 7z use for maximum compression?
- A) `-mx=5`
- B) `-mx=9`
- C) `-max`
- D) `-best`

**Q10:** How do you view a compressed file without extracting?
- A) `view file.gz`
- B) `zcat file.gz`
- C) `read file.gz`
- D) `display file.gz`

**Answers:** 1-B, 2-B, 3-B, 4-C, 5-B, 6-B, 7-A, 8-B, 9-B, 10-B

---

## 🎯 AUTOMATION CHALLENGES

### Challenge 1: Create a Backup Widget
**Objective:** Create a Termux:Widget that backs up a specified folder with one tap.
**Hint:** Use timestamp in filename for versioning.

### Challenge 2: Build a Log Rotator
**Objective:** Create a script that compresses logs older than 7 days and deletes archives older than 30 days.
**Hint:** Use `find` with `-mtime` parameter.

### Challenge 3: Incremental Backup System
**Objective:** Create a script that does full backup on Sunday and incremental backups on other days.
**Hint:** Use `--listed-incremental` with tar.

### Challenge 4: Archive Organizer
**Objective:** Create a script that organizes archives by date into year/month folders.
**Hint:** Use `date` command and `mkdir -p`.

### Challenge 5: Compression Benchmark
**Objective:** Create a script that compresses a file using all methods and compares sizes.
**Hint:** Use `time` command and `du` for measurements.

---

## 📝 SCRIPT WRITING EXERCISES

### Exercise A: Backup Script
Create a script that accepts a source directory and creates a dated backup:
```bash
#!/bin/bash
# Your code here
```

### Exercise B: Archive Extractor
Create a universal extractor that handles any archive format:
```bash
#!/bin/bash
# Your code here
```

### Exercise C: Compression Analyzer
Create a script that shows compression statistics for different methods:
```bash
#!/bin/bash
# Your code here
```

---

**End of Chapter 40 Upgrade**
