# 📁 Chapter 56: Project 6 - File Organizer

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ███████╗██████╗ ██╗██╗  ██╗███████╗██╗     ███████╗ ██████╗ ██╗██████╗     ║
║   ██╔════╝██╔══██╗██║██║ ██╔╝██╔════╝██║     ██╔════╝██╔═══██╗██║██╔══██╗    ║
║   █████╗  ██████╔╝██║█████╔╝ █████╗  ██║     ███████╗██║   ██║██║██║  ██║    ║
║   ██╔══╝  ██╔══██╗██║██╔═██╗ ██╔══╝  ██║     ╚════██║██║   ██║██║██║  ██║    ║
║   ██║     ██║  ██║██║██║  ██╗███████╗███████╗███████║╚██████╔╝██║██████╔╝    ║
║   ╚═╝     ╚═╝  ╚═╝╚═╝╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝ ╚═════╝ ╚═╝╚═════╝     ║
║                                                                              ║
║              📁 FILE ORGANIZER 📁                                            ║
║                    by T3rmuxk1ng                                             ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 9 - Projects  
> **Chapter:** 56 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed file organization concepts |
| Python Implementation | Full-featured organizer with all modes |
| Configuration File | JSON-based custom rules |
| Source Code | Complete production-ready code |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 56
Title: File Organizer Tool Banayein | Auto Sort Files | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum banayenge ek bahut hi useful tool - File Organizer!

Ye project aapke liye bahut practical hai kyunki:
1. Aap apne messy downloads folder ko organize kar sakte ho
2. Python file handling ka practical use seekhenge
3. Automation ka real-world example banayenge
4. Configuration-driven development samjhenge

Kabhi socha hai - Downloads folder mein kitne files bikhre hote hain?
Images, videos, PDFs, APKs - sab ek jagah! Dhundne mein musibat hoti hai.

Aaj hum banayenge aisa tool jo automatically files ko sort karega!

Chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein!

---

[SECTION 1: PROJECT OVERVIEW - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - File Organizer kya karega?

File Organizer ek automation tool hai jo:
- Files ko unke extension ke basis pe categorize karta hai
- Different folders mein move karta hai
- Manual organization ka kaam automatic karta hai

┌─────────────────────────────────────────────────────────────────────────┐
│                    FILE ORGANIZER - KAAM KAISE KARTA HAI                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  BEFORE (Messy Downloads Folder):                                       │
│  ┌───────────────────────────────────────────────────────────────┐     │
│  │ downloads/                                                     │     │
│  │ ├── photo1.jpg                                                │     │
│  │ ├── document.pdf                                              │     │
│  │ ├── song.mp3                                                  │     │
│  │ ├── video.mp4                                                 │     │
│  │ ├── app.apk                                                   │     │
│  │ ├── script.py                                                 │     │
│  │ ├── image.png                                                 │     │
│  │ └── report.docx                                               │     │
│  └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
│  AFTER (Organized):                                                     │
│  ┌───────────────────────────────────────────────────────────────┐     │
│  │ downloads/                                                     │     │
│  │ ├── Images/                                                   │     │
│  │ │   ├── photo1.jpg                                            │     │
│  │ │   └── image.png                                             │     │
│  │ ├── Documents/                                                │     │
│  │ │   ├── document.pdf                                          │     │
│  │ │   └── report.docx                                           │     │
│  │ ├── Audio/                                                    │     │
│  │ │   └── song.mp3                                              │     │
│  │ ├── Videos/                                                   │     │
│  │ │   └── video.mp4                                             │     │
│  │ ├── Apps/                                                     │     │
│  │ │   └── app.apk                                               │     │
│  │ └── Code/                                                     │     │
│  │     └── script.py                                             │     │
│  └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Ye tool aapki life easy bana dega - trust me!

---

[SECTION 2: FEATURES OVERVIEW - 4:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Hamare File Organizer mein ye features honge:

┌─────────────────────────────────────────────────────────────────────────┐
│                    FILE ORGANIZER FEATURES                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. SORT BY EXTENSION                                                    │
│     - Files ko extension ke basis pe sort karo                           │
│     - .jpg → Images, .pdf → Documents                                    │
│     - Default categorization                                             │
│                                                                          │
│  2. SORT BY DATE                                                         │
│     - Creation date ke basis pe                                          │
│     - Modification date ke basis pe                                      │
│     - Year/Month folders mein organize                                   │
│                                                                          │
│  3. SORT BY SIZE                                                         │
│     - Small (< 1MB), Medium (1-100MB), Large (> 100MB)                   │
│     - Size-based categorization                                          │
│                                                                          │
│  4. CUSTOM RULES                                                         │
│     - Apne rules define karo JSON mein                                   │
│     - Specific extensions ke liye custom folders                         │
│     - Wildcard support                                                   │
│                                                                          │
│  5. PREVIEW MODE                                                         │
│     - Pehle dekho kya hoga                                               │
│     - Actually move nahi hoga                                            │
│     - Safe testing ke liye                                               │
│                                                                          │
│  6. UNDO OPERATION                                                       │
│     - Galti ho gayi? Undo karo!                                          │
│     - History maintain hoti hai                                          │
│     - Last operation reverse karo                                        │
│                                                                          │
│  7. RECURSIVE ORGANIZATION                                               │
│     - Subfolders bhi scan karo                                           │
│     - Deep directory traversal                                           │
│     - Complete cleanup                                                   │
│                                                                          │
│  8. WATCH MODE (AUTO-ORGANIZE)                                           │
│     - Real-time monitoring                                               │
│     - New file aate hi organize                                          │
│     - Set-and-forget mode                                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Ye sab features hum implement karenge step by step!

---

[SECTION 3: EXTENSION SORTING - 7:00 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab sabse important feature samjhte hain - Extension-based Sorting!

Har file ka extension hota hai - .jpg, .pdf, .mp3, etc.
Hum in extensions ko categories mein divide karenge:

┌─────────────────────────────────────────────────────────────────────────┐
│                    DEFAULT CATEGORIES                                    │
├────────────────────┬────────────────────────────────────────────────────┤
│ Category           │ Extensions                                       │
├────────────────────┼────────────────────────────────────────────────────┤
│ Images             │ .jpg, .jpeg, .png, .gif, .bmp, .svg, .webp        │
│ Videos             │ .mp4, .mkv, .avi, .mov, .wmv, .flv, .webm        │
│ Audio              │ .mp3, .wav, .flac, .aac, .ogg, .m4a, .wma        │
│ Documents          │ .pdf, .doc, .docx, .txt, .xls, .xlsx, .ppt       │
│ Archives           │ .zip, .rar, .7z, .tar, .gz, .bz2                 │
│ Code               │ .py, .js, .html, .css, .java, .cpp, .sh          │
│ Apps               │ .apk, .exe, .deb, .rpm, .dmg                     │
│ Others             │ (Files without matching category)                 │
└────────────────────┴────────────────────────────────────────────────────┘

Python code samjhte hain:

    import os
    import shutil
    from pathlib import Path
    
    # Define categories
    CATEGORIES = {
        'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.svg', '.webp'],
        'Videos': ['.mp4', '.mkv', '.avi', '.mov', '.wmv', '.flv', '.webm'],
        'Audio': ['.mp3', '.wav', '.flac', '.aac', '.ogg', '.m4a', '.wma'],
        'Documents': ['.pdf', '.doc', '.docx', '.txt', '.xls', '.xlsx', '.ppt'],
        'Archives': ['.zip', '.rar', '.7z', '.tar', '.gz', '.bz2'],
        'Code': ['.py', '.js', '.html', '.css', '.java', '.cpp', '.sh'],
        'Apps': ['.apk', '.exe', '.deb', '.rpm', '.dmg']
    }
    
    def get_category(extension):
        """Find category for a file extension"""
        ext = extension.lower()
        for category, extensions in CATEGORIES.items():
            if ext in extensions:
                return category
        return 'Others'
    
    def organize_by_extension(source_dir):
        """Organize files by extension"""
        source = Path(source_dir)
        
        for file_path in source.iterdir():
            if file_path.is_file():
                # Get category
                category = get_category(file_path.suffix)
                
                # Create category folder
                dest_folder = source / category
                dest_folder.mkdir(exist_ok=True)
                
                # Move file
                dest_path = dest_folder / file_path.name
                shutil.move(str(file_path), str(dest_path))
                print(f"Moved: {file_path.name} → {category}/")

Simple aur powerful! Har file apni category folder mein chali jaayegi!

---

[SECTION 4: DATE & SIZE SORTING - 11:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab date-based sorting samjhte hain:

    import os
    from datetime import datetime
    from pathlib import Path
    
    def organize_by_date(source_dir, by='modified'):
        """Organize files by date"""
        source = Path(source_dir)
        
        for file_path in source.iterdir():
            if file_path.is_file():
                # Get file timestamp
                if by == 'modified':
                    timestamp = file_path.stat().st_mtime
                else:  # created
                    timestamp = file_path.stat().st_ctime
                
                # Convert to date
                date = datetime.fromtimestamp(timestamp)
                folder_name = date.strftime('%Y-%m')  # 2024-01
                
                # Create folder
                dest_folder = source / folder_name
                dest_folder.mkdir(exist_ok=True)
                
                # Move file
                dest_path = dest_folder / file_path.name
                shutil.move(str(file_path), str(dest_path))
                print(f"Moved: {file_path.name} → {folder_name}/")

Yahan:
- st_mtime = Modification time
- st_ctime = Creation time
- strftime = Date ko string mein convert

Ab size-based sorting:

    def organize_by_size(source_dir):
        """Organize files by size"""
        source = Path(source_dir)
        
        SIZE_CATEGORIES = {
            'Small': (0, 1024 * 1024),           # 0 - 1MB
            'Medium': (1024 * 1024, 100 * 1024 * 1024),  # 1MB - 100MB
            'Large': (100 * 1024 * 1024, float('inf'))    # > 100MB
        }
        
        for file_path in source.iterdir():
            if file_path.is_file():
                size = file_path.stat().st_size
                
                # Find size category
                for category, (min_size, max_size) in SIZE_CATEGORIES.items():
                    if min_size <= size < max_size:
                        dest_folder = source / category
                        dest_folder.mkdir(exist_ok=True)
                        dest_path = dest_folder / file_path.name
                        shutil.move(str(file_path), str(dest_path))
                        print(f"Moved: {file_path.name} → {category}/")
                        break

Ye teeno modes - Extension, Date, Size - bahut useful hain!

---

[SECTION 5: CUSTOM RULES & PREVIEW MODE - 15:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab custom rules samjhte hain - JSON configuration file!

Configuration file (organizer_config.json):

    {
        "rules": {
            "Work": [".work", ".project", "*.work.*"],
            "Personal": [".personal", ".private"],
            "Downloads": [".torrent", ".part"]
        },
        "exclude_folders": ["System", "Important"],
        "exclude_files": [".nomedia", ".gitignore"],
        "naming_convention": "lowercase"
    }

Python code for custom rules:

    import json
    
    def load_config(config_file):
        """Load custom rules from JSON"""
        with open(config_file, 'r') as f:
            return json.load(f)
    
    def organize_with_rules(source_dir, config):
        """Organize using custom rules"""
        source = Path(source_dir)
        rules = config.get('rules', {})
        exclude_folders = config.get('exclude_folders', [])
        
        for file_path in source.iterdir():
            if file_path.is_file():
                if file_path.name in config.get('exclude_files', []):
                    continue
                
                # Check custom rules
                for folder, patterns in rules.items():
                    for pattern in patterns:
                        if fnmatch.fnmatch(file_path.name, pattern):
                            dest_folder = source / folder
                            dest_folder.mkdir(exist_ok=True)
                            dest_path = dest_folder / file_path.name
                            shutil.move(str(file_path), str(dest_path))
                            print(f"Custom Rule: {file_path.name} → {folder}/")
                            break

Preview Mode - Safe testing:

    def preview_organization(source_dir, mode='extension'):
        """Preview what would happen without moving"""
        source = Path(source_dir)
        changes = []
        
        for file_path in source.iterdir():
            if file_path.is_file():
                if mode == 'extension':
                    category = get_category(file_path.suffix)
                    dest = source / category / file_path.name
                elif mode == 'date':
                    date = datetime.fromtimestamp(file_path.stat().st_mtime)
                    folder = date.strftime('%Y-%m')
                    dest = source / folder / file_path.name
                
                changes.append({
                    'source': str(file_path),
                    'destination': str(dest),
                    'action': 'move'
                })
        
        print("\n📋 PREVIEW MODE - No files will be moved\n")
        for change in changes:
            print(f"{Path(change['source']).name} → {Path(change['destination']).parent.name}/")
        
        print(f"\nTotal changes: {len(changes)}")
        return changes

Preview mode se aap pehle dekh sakte ho kya hoga - safe!

---

[SECTION 6: UNDO & WATCH MODE - 18:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Undo Operation:

Har operation ke baad hum history save karenge:

    import json
    from datetime import datetime
    
    HISTORY_FILE = 'organizer_history.json'
    
    def save_history(operations):
        """Save operation history for undo"""
        history = {
            'timestamp': datetime.now().isoformat(),
            'operations': operations
        }
        
        with open(HISTORY_FILE, 'w') as f:
            json.dump(history, f, indent=2)
    
    def undo_last_operation():
        """Undo the last organization operation"""
        if not os.path.exists(HISTORY_FILE):
            print("No history found!")
            return
        
        with open(HISTORY_FILE, 'r') as f:
            history = json.load(f)
        
        print("Undoing last operation...")
        for op in reversed(history['operations']):
            # Reverse the move
            source = Path(op['destination'])
            dest = Path(op['source'])
            shutil.move(str(source), str(dest))
            print(f"Restored: {source.name}")
        
        # Clear history
        os.remove(HISTORY_FILE)
        print("Undo complete!")

Watch Mode - Auto-organize:

Ye sabse powerful feature hai! New files automatically organize hongi:

    import time
    from watchdog.observers import Observer
    from watchdog.events import FileSystemEventHandler
    
    class FileOrganizerHandler(FileSystemEventHandler):
        """Handler for file system events"""
        
        def __init__(self, organizer):
            self.organizer = organizer
        
        def on_created(self, event):
            """When a new file is created"""
            if not event.is_directory:
                file_path = Path(event.src_path)
                print(f"\n📁 New file detected: {file_path.name}")
                self.organizer.organize_file(file_path)
    
    def watch_mode(source_dir):
        """Watch directory for new files"""
        print(f"👀 Watching {source_dir} for new files...")
        print("Press Ctrl+C to stop\n")
        
        event_handler = FileOrganizerHandler(organizer)
        observer = Observer()
        observer.schedule(event_handler, source_dir, recursive=False)
        observer.start()
        
        try:
            while True:
                time.sleep(1)
        except KeyboardInterrupt:
            observer.stop()
            print("\nWatch mode stopped.")
        
        observer.join()

Watch mode chalao, aur jab bhi naya file aayega - automatically organize ho jaayega!

Iske liye watchdog package install karna padega:
    pip install watchdog

---

[SECTION 7: DEMO & TESTING - 22:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye apne tool ko test karte hain!

[TEST 1: Extension-based Organization]

    python file_organizer.py ~/storage/downloads --mode extension

Output:
    📂 Organizing by extension...
    
    Moving files:
    photo.jpg → Images/
    video.mp4 → Videos/
    song.mp3 → Audio/
    report.pdf → Documents/
    script.py → Code/
    game.apk → Apps/
    
    ✅ Organized 6 files!
    📊 Created folders: Images, Videos, Audio, Documents, Code, Apps

[TEST 2: Preview Mode]

    python file_organizer.py ~/storage/downloads --preview

Output:
    📋 PREVIEW MODE - No files will be moved
    
    Files that would be moved:
    ├── photo.jpg → Images/
    ├── video.mp4 → Videos/
    └── report.pdf → Documents/
    
    Total: 3 files
    Confirm? (y/n): y
    
    ✅ Preview complete!

[TEST 3: Undo Operation]

    python file_organizer.py --undo

Output:
    ↩️ Undoing last operation...
    
    Restored: photo.jpg → root
    Restored: video.mp4 → root
    Restored: report.pdf → root
    
    ✅ Undo complete! All files restored.

[TEST 4: Watch Mode]

    python file_organizer.py ~/storage/downloads --watch

Output:
    👀 Watching /storage/downloads for new files...
    Press Ctrl+C to stop
    
    📁 New file detected: screenshot.png
    Moving: screenshot.png → Images/
    
    📁 New file detected: lecture.pdf
    Moving: lecture.pdf → Documents/
    
    (Auto-organizing in real-time!)

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 24:00 to 25:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 56 complete! Let's summarize:

✅ File Organizer kya hai - Automatic file sorting
✅ Extension-based sorting - Category-wise organization
✅ Date-based sorting - Year/Month folders
✅ Size-based sorting - Small/Medium/Large
✅ Custom rules - JSON configuration
✅ Preview mode - Safe testing
✅ Undo operation - History-based reverse
✅ Watch mode - Real-time auto-organize
✅ Recursive organization - Subfolders included

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 56 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ python file_organizer.py <folder> --mode extension  │ Sort by ext      │
│ python file_organizer.py <folder> --mode date       │ Sort by date     │
│ python file_organizer.py <folder> --mode size       │ Sort by size     │
│ python file_organizer.py <folder> --preview         │ Preview changes  │
│ python file_organizer.py <folder> --watch           │ Auto-organize    │
│ python file_organizer.py <folder> --recursive       │ Include subs     │
│ python file_organizer.py --undo                     │ Undo last        │
│ python file_organizer.py --config rules.json        │ Custom rules     │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 57 mein hum banayenge:
   - Backup Automation Tool
   - Scheduled backups
   - Cloud integration
   - Compression & encryption

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 57!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

<details>
<summary><b>❓ Question 1: What is the primary purpose of a file organizer?</b></summary>

**Answer:** To automatically categorize and sort files based on their attributes like extension, date, or size.

File organizers save time by eliminating manual sorting and help maintain a clean, structured file system.
</details>

<details>
<summary><b>❓ Question 2: Which Python module is used for file operations?</b></summary>

**Answer:** `pathlib` and `shutil`

`pathlib` provides object-oriented filesystem paths, while `shutil` offers high-level file operations like moving, copying, and deleting files.
</details>

<details>
<summary><b>❓ Question 3: What is the advantage of using preview mode?</b></summary>

**Answer:** It shows what would happen without actually moving files, allowing safe testing.

Preview mode helps prevent accidental file operations and lets you verify the organization rules before applying them.
</details>

<details>
<summary><b>❓ Question 4: How does extension-based sorting work?</b></summary>

**Answer:** Files are categorized based on their file extension (e.g., .jpg → Images, .pdf → Documents).

The program matches each file's extension against predefined categories and moves them to corresponding folders.
</details>

<details>
<summary><b>❓ Question 5: What is the purpose of the undo feature?</b></summary>

**Answer:** To reverse the last organization operation by moving files back to their original locations.

The undo feature maintains a history of operations, allowing users to recover from mistakes.
</details>

<details>
<summary><b>❓ Question 6: What is watch mode in a file organizer?</b></summary>

**Answer:** Real-time monitoring that automatically organizes new files as they are added to a directory.

Watch mode uses filesystem event monitoring to detect new files and immediately categorize them.
</details>

<details>
<summary><b>❓ Question 7: What are the three main sorting modes?</b></summary>

**Answer:** Extension-based, Date-based, and Size-based sorting

Each mode categorizes files differently: by file type, by creation/modification date, or by file size.
</details>

<details>
<summary><b>❓ Question 8: How do you handle file naming conflicts when organizing?</b></summary>

**Answer:** Append a number suffix, timestamp, or use a renaming strategy to ensure unique names.

Common approaches: `file_1.pdf`, `file_20240115.pdf`, or asking the user for resolution.
</details>

<details>
<summary><b>❓ Question 9: What Python library is used for file system watching?</b></summary>

**Answer:** `watchdog`

The watchdog library provides cross-platform file system event monitoring, detecting file creation, modification, deletion, and movement.
</details>

<details>
<summary><b>❓ Question 10: What is the difference between move and copy operations?</b></summary>

**Answer:** Move transfers the file (removes from source), Copy creates a duplicate (keeps original).

Move is faster and saves space, while Copy is safer for preserving original files.
</details>

<details>
<summary><b>❓ Question 11: How do you organize files by date?</b></summary>

**Answer:** Extract the file's timestamp (creation or modification) and create date-based folders (YYYY-MM format).

This is useful for photos, logs, and documents where chronological organization matters.
</details>

<details>
<summary><b>❓ Question 12: What is a JSON configuration file used for?</b></summary>

**Answer:** To store custom organization rules, excluded folders, and user preferences.

JSON configs allow users to define their own categories and rules without modifying code.
</details>

<details>
<summary><b>❓ Question 13: What is recursive organization?</b></summary>

**Answer:** Scanning and organizing files in all subdirectories, not just the top-level folder.

This provides complete cleanup of nested folder structures.
</details>

<details>
<summary><b>❓ Question 14: How do you get file size in Python?</b></summary>

**Answer:** Use `pathlib.Path.stat().st_size` or `os.path.getsize()`

This returns the file size in bytes, which can be converted to KB, MB, GB as needed.
</details>

<details>
<summary><b>❓ Question 15: What is the benefit of size-based sorting?</b></summary>

**Answer:** It helps identify large files wasting space and categorizes files for storage management.

Size categories like Small, Medium, Large help users quickly find space-consuming files.
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Question 1: How would you handle duplicate files during organization?

**Answer:**

**Detection Strategies:**
1. **Name-based:** Same filename in different locations
2. **Hash-based:** Same content but different names
3. **Size-based:** Quick initial check

```python
import hashlib
from pathlib import Path

def calculate_hash(filepath, algorithm='md5'):
    """Calculate file hash for duplicate detection"""
    hash_func = hashlib.new(algorithm)
    with open(filepath, 'rb') as f:
        for chunk in iter(lambda: f.read(8192), b''):
            hash_func.update(chunk)
    return hash_func.hexdigest()

def find_duplicates(directory):
    """Find duplicate files by hash"""
    hashes = {}
    duplicates = []
    
    for filepath in Path(directory).rglob('*'):
        if filepath.is_file():
            file_hash = calculate_hash(filepath)
            if file_hash in hashes:
                duplicates.append((filepath, hashes[file_hash]))
            else:
                hashes[file_hash] = filepath
    
    return duplicates
```

**Resolution Options:**
- Skip duplicates
- Keep newer version
- Ask user for each duplicate
- Create "Duplicates" folder
- Log and report only

---

### Question 2: Explain how you would implement a file organization rules engine.

**Answer:**

**Architecture:**

```python
from dataclasses import dataclass
from typing import Callable, List
from pathlib import Path

@dataclass
class Rule:
    name: str
    condition: Callable[[Path], bool]
    action: Callable[[Path], Path]
    priority: int = 0

class RulesEngine:
    def __init__(self):
        self.rules: List[Rule] = []
    
    def add_rule(self, rule: Rule):
        self.rules.append(rule)
        self.rules.sort(key=lambda r: r.priority, reverse=True)
    
    def apply(self, filepath: Path) -> Path:
        for rule in self.rules:
            if rule.condition(filepath):
                return rule.action(filepath)
        return filepath  # Default: no action

# Example rules
def is_image(filepath):
    return filepath.suffix.lower() in ['.jpg', '.png', '.gif']

def move_to_images(filepath):
    return filepath.parent / 'Images' / filepath.name

engine = RulesEngine()
engine.add_rule(Rule('images', is_image, move_to_images, priority=10))
```

**Features:**
- Priority-based rule matching
- Composable conditions
- Configurable actions
- Rule inheritance
- Conflict resolution

---

### Question 3: How would you optimize file organization for large directories?

**Answer:**

**Optimization Strategies:**

1. **Parallel Processing:**
```python
from concurrent.futures import ThreadPoolExecutor

def organize_parallel(files, max_workers=4):
    with ThreadPoolExecutor(max_workers=max_workers) as executor:
        results = list(executor.map(organize_file, files))
    return results
```

2. **Batched Processing:**
```python
def organize_in_batches(files, batch_size=1000):
    for i in range(0, len(files), batch_size):
        batch = files[i:i+batch_size]
        process_batch(batch)
        # Allow system to catch up
        time.sleep(0.1)
```

3. **Caching Directory Structure:**
```python
class DirectoryCache:
    def __init__(self):
        self.cache = {}
    
    def get_or_create(self, path):
        if path not in self.cache:
            self.cache[path] = Path(path)
            self.cache[path].mkdir(exist_ok=True)
        return self.cache[path]
```

4. **Streaming vs Loading:**
- Don't load all files into memory
- Use generators for file listing
- Process one file at a time

**Performance Considerations:**
- I/O bound operations benefit from threading
- Network paths need special handling
- SSD vs HDD performance differs
- Monitor memory usage

---

### Question 4: How would you implement a safe file organization with rollback capability?

**Answer:**

**Transaction-Based Approach:**

```python
import json
from datetime import datetime
from pathlib import Path

class FileOrganizerTransaction:
    def __init__(self, log_file='organizer_log.json'):
        self.log_file = Path(log_file)
        self.operations = []
    
    def begin(self):
        """Start a new transaction"""
        self.operations = []
        return self
    
    def move(self, source, destination):
        """Record a move operation"""
        self.operations.append({
            'type': 'move',
            'source': str(source),
            'destination': str(destination),
            'timestamp': datetime.now().isoformat()
        })
        source.rename(destination)
    
    def commit(self):
        """Save transaction log"""
        with open(self.log_file, 'a') as f:
            json.dump({
                'operations': self.operations,
                'committed': datetime.now().isoformat()
            }, f)
            f.write('\n')
        self.operations = []
    
    def rollback(self):
        """Undo all operations in current transaction"""
        for op in reversed(self.operations):
            if op['type'] == 'move':
                Path(op['destination']).rename(Path(op['source']))
        self.operations = []

# Usage with context manager
with FileOrganizerTransaction() as txn:
    txn.move(file1, dest1)
    txn.move(file2, dest2)
    # If exception occurs, rollback is automatic
```

**Features:**
- Atomic operations
- Automatic rollback on failure
- Persistent transaction log
- Recovery after crash

---

### Question 5: How do you handle file permissions and errors during organization?

**Answer:**

**Error Handling Strategy:**

```python
import os
import stat
from pathlib import Path

class SafeOrganizer:
    def __init__(self):
        self.errors = []
        self.skipped = []
    
    def check_permissions(self, filepath):
        """Check if we have necessary permissions"""
        try:
            # Check read permission
            if not os.access(filepath, os.R_OK):
                return False, "No read permission"
            
            # Check write permission on parent directory
            parent = filepath.parent
            if not os.access(parent, os.W_OK):
                return False, "No write permission on parent"
            
            return True, "OK"
        except OSError as e:
            return False, str(e)
    
    def safe_move(self, source, destination):
        """Move file with comprehensive error handling"""
        try:
            # Pre-flight checks
            if not source.exists():
                self.skipped.append((source, "File not found"))
                return False
            
            can_proceed, msg = self.check_permissions(source)
            if not can_proceed:
                self.skipped.append((source, msg))
                return False
            
            # Ensure destination exists
            destination.parent.mkdir(parents=True, exist_ok=True)
            
            # Attempt move
            shutil.move(str(source), str(destination))
            return True
            
        except PermissionError as e:
            self.errors.append((source, f"Permission denied: {e}"))
        except OSError as e:
            self.errors.append((source, f"OS Error: {e}"))
        except Exception as e:
            self.errors.append((source, f"Unexpected: {e}"))
        
        return False
    
    def get_report(self):
        """Generate error report"""
        return {
            'errors': len(self.errors),
            'skipped': len(self.skipped),
            'details': {
                'errors': self.errors,
                'skipped': self.skipped
            }
        }
```

---

### Question 6: How would you design a plugin system for custom organization rules?

**Answer:**

**Plugin Architecture:**

```python
from abc import ABC, abstractmethod
from pathlib import Path
import importlib
import inspect

class OrganizerPlugin(ABC):
    """Base class for organizer plugins"""
    
    @property
    @abstractmethod
    def name(self) -> str:
        """Plugin name"""
        pass
    
    @property
    @abstractmethod
    def version(self) -> str:
        """Plugin version"""
        pass
    
    @abstractmethod
    def can_handle(self, filepath: Path) -> bool:
        """Check if this plugin handles the file"""
        pass
    
    @abstractmethod
    def get_destination(self, filepath: Path) -> Path:
        """Determine destination for the file"""
        pass
    
    def before_move(self, filepath: Path):
        """Hook called before moving"""
        pass
    
    def after_move(self, source: Path, destination: Path):
        """Hook called after moving"""
        pass

class PluginManager:
    def __init__(self):
        self.plugins = []
    
    def load_plugin(self, plugin_path):
        """Load plugin from file path"""
        spec = importlib.util.spec_from_file_location("plugin", plugin_path)
        module = importlib.util.module_from_spec(spec)
        spec.loader.exec_module(module)
        
        for name, obj in inspect.getmembers(module):
            if inspect.isclass(obj) and issubclass(obj, OrganizerPlugin) and obj != OrganizerPlugin:
                self.plugins.append(obj())
    
    def get_destination(self, filepath: Path) -> Path:
        """Get destination from first matching plugin"""
        for plugin in self.plugins:
            if plugin.can_handle(filepath):
                return plugin.get_destination(filepath)
        return filepath.parent / 'Others' / filepath.name

# Example plugin: PhotoOrganizer
class PhotoOrganizer(OrganizerPlugin):
    @property
    def name(self):
        return "Photo Organizer"
    
    @property
    def version(self):
        return "1.0"
    
    def can_handle(self, filepath):
        return filepath.suffix.lower() in ['.jpg', '.jpeg', '.png', '.raw', '.heic']
    
    def get_destination(self, filepath):
        # Get EXIF date if available, fall back to file date
        date = self.get_photo_date(filepath)
        return Path('Photos') / date.strftime('%Y/%m') / filepath.name
```

---

### Question 7: Explain how you would implement smart file naming during organization.

**Answer:**

**Smart Naming Implementation:**

```python
import re
from datetime import datetime
from pathlib import Path

class SmartNamer:
    def __init__(self):
        self.patterns = [
            # Remove special characters
            (r'[<>:"/\\|?*]', '_'),
            # Replace spaces with underscores
            (r'\s+', '_'),
            # Remove multiple underscores
            (r'_+', '_'),
            # Remove leading/trailing underscores
            (r'^_|_$', ''),
        ]
    
    def sanitize(self, filename: str) -> str:
        """Remove illegal characters from filename"""
        for pattern, replacement in self.patterns:
            filename = re.sub(pattern, replacement, filename)
        return filename
    
    def add_date_prefix(self, filepath: Path, date_format='%Y%m%d') -> Path:
        """Add date prefix based on file modification time"""
        mtime = datetime.fromtimestamp(filepath.stat().st_mtime)
        prefix = mtime.strftime(date_format)
        new_name = f"{prefix}_{filepath.name}"
        return filepath.parent / new_name
    
    def make_unique(self, filepath: Path) -> Path:
        """Ensure filename is unique by adding suffix"""
        if not filepath.exists():
            return filepath
        
        counter = 1
        while True:
            new_name = f"{filepath.stem}_{counter}{filepath.suffix}"
            new_path = filepath.parent / new_name
            if not new_path.exists():
                return new_path
            counter += 1
    
    def apply_convention(self, filepath: Path, convention='lowercase') -> Path:
        """Apply naming convention"""
        name = filepath.stem
        suffix = filepath.suffix
        
        if convention == 'lowercase':
            name = name.lower()
        elif convention == 'uppercase':
            name = name.upper()
        elif convention == 'titlecase':
            name = name.title()
        elif convention == 'snakecase':
            name = re.sub(r'([A-Z])', r'_\1', name).lower().strip('_')
        
        return filepath.parent / f"{name}{suffix}"
    
    def smart_rename(self, filepath: Path, config: dict) -> Path:
        """Apply all smart naming rules"""
        name = filepath.name
        
        # Sanitize
        name = self.sanitize(name)
        
        # Apply convention
        if config.get('convention'):
            name = self.apply_convention(filepath, config['convention']).name
        
        # Add prefix
        if config.get('date_prefix'):
            filepath = self.add_date_prefix(filepath)
        
        # Make unique
        return self.make_unique(filepath)
```

---

### Question 8: How would you integrate file organization with cloud storage?

**Answer:**

**Cloud Integration Approach:**

```python
from abc import ABC, abstractmethod
from pathlib import Path

class CloudProvider(ABC):
    @abstractmethod
    def upload(self, local_path: Path, remote_path: str):
        pass
    
    @abstractmethod
    def download(self, remote_path: str, local_path: Path):
        pass
    
    @abstractmethod
    def exists(self, remote_path: str) -> bool:
        pass

class DropboxProvider(CloudProvider):
    def __init__(self, token):
        import dropbox
        self.dbx = dropbox.Dropbox(token)
    
    def upload(self, local_path: Path, remote_path: str):
        with open(local_path, 'rb') as f:
            self.dbx.files_upload(f.read(), remote_path)
    
    def exists(self, remote_path: str) -> bool:
        try:
            self.dbx.files_get_metadata(remote_path)
            return True
        except:
            return False

class CloudOrganizer:
    def __init__(self, provider: CloudProvider, sync_folder: Path):
        self.provider = provider
        self.sync_folder = sync_folder
    
    def organize_to_cloud(self, local_file: Path, category: str):
        """Move local file to cloud storage"""
        remote_path = f"/{category}/{local_file.name}"
        
        # Check if already exists
        if self.provider.exists(remote_path):
            remote_path = self.make_unique_remote(remote_path)
        
        # Upload
        self.provider.upload(local_file, remote_path)
        
        # Optionally delete local
        if self.delete_after_upload:
            local_file.unlink()
        
        return remote_path
    
    def sync_from_cloud(self, category: str):
        """Download files from cloud to local"""
        # Implementation depends on provider
        pass
```

---

### Question 9: How do you handle symbolic links and special files?

**Answer:**

**Special File Handling:**

```python
import os
import stat
from pathlib import Path

class SpecialFileHandler:
    def categorize_file(self, filepath: Path) -> str:
        """Determine file type including special files"""
        if not filepath.exists():
            # Handle broken symlinks
            if filepath.is_symlink():
                return 'broken_symlink'
            return 'missing'
        
        mode = filepath.lstat().st_mode
        
        if stat.S_ISLNK(mode):
            return 'symlink'
        elif stat.S_ISDIR(mode):
            return 'directory'
        elif stat.S_ISREG(mode):
            return 'regular'
        elif stat.S_ISFIFO(mode):
            return 'fifo'
        elif stat.S_ISSOCK(mode):
            return 'socket'
        elif stat.S_ISCHR(mode):
            return 'character_device'
        elif stat.S_ISBLK(mode):
            return 'block_device'
        
        return 'unknown'
    
    def handle_symlink(self, filepath: Path) -> dict:
        """Get symlink information"""
        if filepath.is_symlink():
            target = os.readlink(filepath)
            return {
                'type': 'symlink',
                'target': target,
                'valid': Path(target).exists()
            }
        return None
    
    def safe_organize(self, filepath: Path, rules: dict):
        """Organize with special file handling"""
        file_type = self.categorize_file(filepath)
        
        if file_type == 'symlink':
            if rules.get('follow_symlinks'):
                return self.organize_regular(filepath.resolve())
            elif rules.get('preserve_symlinks'):
                return self.preserve_symlink(filepath)
            else:
                return 'skip'
        
        elif file_type == 'broken_symlink':
            if rules.get('delete_broken'):
                filepath.unlink()
            return 'removed'
        
        elif file_type == 'regular':
            return self.organize_regular(filepath)
        
        else:
            return 'skip'
```

---

### Question 10: How would you implement a file organization scheduler?

**Answer:**

**Scheduler Implementation:**

```python
import schedule
import time
import threading
from datetime import datetime
from pathlib import Path

class OrganizationScheduler:
    def __init__(self, organizer):
        self.organizer = organizer
        self.jobs = []
        self.running = False
        self.thread = None
    
    def schedule_daily(self, directory: Path, time_str: str, mode: str = 'extension'):
        """Schedule daily organization at specific time"""
        job = schedule.every().day.at(time_str).do(
            self.organize_task,
            directory=directory,
            mode=mode
        )
        self.jobs.append({
            'type': 'daily',
            'time': time_str,
            'directory': str(directory),
            'mode': mode,
            'job': job
        })
        return job
    
    def schedule_weekly(self, directory: Path, day: str, time_str: str):
        """Schedule weekly organization"""
        day_map = {
            'monday': schedule.every().monday,
            'tuesday': schedule.every().tuesday,
            # ... etc
        }
        job = day_map[day.lower()].at(time_str).do(
            self.organize_task,
            directory=directory,
            mode='full'
        )
        return job
    
    def organize_task(self, directory: Path, mode: str):
        """Task wrapper with logging"""
        try:
            print(f"[{datetime.now()}] Starting organization of {directory}")
            result = self.organizer.organize(directory, mode=mode)
            print(f"[{datetime.now()}] Completed: {result}")
            self.notify(result)
        except Exception as e:
            print(f"[{datetime.now()}] Error: {e}")
    
    def notify(self, result):
        """Send notification on completion"""
        # Termux notification
        import subprocess
        subprocess.run([
            'termux-notification',
            '--title', 'File Organization Complete',
            '--content', f"Organized {result['files']} files"
        ])
    
    def start(self):
        """Start the scheduler in background thread"""
        self.running = True
        self.thread = threading.Thread(target=self._run, daemon=True)
        self.thread.start()
    
    def _run(self):
        """Main scheduler loop"""
        while self.running:
            schedule.run_pending()
            time.sleep(1)
    
    def stop(self):
        """Stop the scheduler"""
        self.running = False
        if self.thread:
            self.thread.join()

# Usage
scheduler = OrganizationScheduler(organizer)
scheduler.schedule_daily(Path('~/downloads'), '02:00', 'extension')
scheduler.schedule_weekly(Path('~/documents'), 'sunday', '03:00')
scheduler.start()
```

---

## 🔥 REAL-WORLD SCENARIOS

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 1: DOWNLOADS FOLDER CHAOS CLEANUP                             │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: User's downloads folder has 500+ files accumulated over months │
│                                                                             │
│  Challenge: Files of all types mixed together - photos, APKs, PDFs,       │
│  videos, and more. Finding anything is difficult and frustrating.          │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Run preview mode first to see organization plan                        │
│  2. Use extension-based sorting for quick categorization                   │
│  3. Create custom rules for project-specific file types                    │
│  4. Enable watch mode for future automatic organization                    │
│                                                                             │
│  Command: python file_organizer.py ~/storage/downloads --mode extension    │
│                                                                             │
│  Outcome: 500+ files organized into 8 folders. Future downloads            │
│  automatically sorted. User saves 30 minutes daily.                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 2: PHOTO LIBRARY DATE ORGANIZATION                            │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: 10,000+ photos in DCIM folder with random filenames.          │
│                                                                             │
│  Challenge: Photos from multiple years mixed together. Need to find       │
│  photos from specific events or time periods.                              │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Use date-based sorting with EXIF data extraction                       │
│  2. Create Year/Month folder structure                                     │
│  3. Preserve original filenames as backup reference                        │
│  4. Handle photos without EXIF gracefully                                  │
│                                                                             │
│  Command: python file_organizer.py ~/DCIM --mode date --by modified        │
│                                                                             │
│  Outcome: Photos organized into 2023/01, 2023/02, etc. Easy to            │
│  find memories by date. Backup created before organization.                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 3: PROJECT FILES MANAGEMENT FOR DEVELOPERS                   │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: Developer has projects folder with mixed file types.          │
│                                                                             │
│  Challenge: Source code, documentation, images, and binaries all in       │
│  one place. Need to separate without breaking project structure.           │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Use recursive organization with project awareness                      │
│  2. Exclude .git and node_modules folders                                  │
│  3. Create custom rules: *.py → Code, *.md → Docs                         │
│  4. Preview changes before applying                                        │
│                                                                             │
│  Command: python file_organizer.py ~/projects --recursive --config dev.json│
│                                                                             │
│  Outcome: Clean project structure with organized subdirectories.           │
│  No broken imports or git issues.                                          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 4: STORAGE OPTIMIZATION THROUGH SIZE SORTING                 │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: Phone storage nearly full, need to identify large files.      │
│                                                                             │
│  Challenge: Not sure which files are consuming space. Need to quickly     │
│  identify and optionally delete or move large files.                       │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Use size-based sorting to categorize files                             │
│  2. Large folder (>100MB) shows space hogs                                 │
│  3. Medium folder has manageable files                                     │
│  4. Small folder contains text/config files                                │
│                                                                             │
│  Command: python file_organizer.py ~/storage --mode size                   │
│                                                                             │
│  Outcome: Found 15GB in Large folder (old videos). Moved to cloud.        │
│  Recovered 15GB of storage space.                                          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 5: AUTOMATED DOCUMENT WORKFLOW                                │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: Office worker receives many PDFs, DOCs daily via email.       │
│                                                                             │
│  Challenge: Downloaded documents pile up. Need automatic sorting by        │
│  document type for quick access during work.                               │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Enable watch mode on downloads folder                                  │
│  2. Create custom rules for document types                                 │
│  3. Invoices → Finance, Reports → Work, Contracts → Legal                 │
│  4. Add date suffix to filename automatically                              │
│                                                                             │
│  Command: python file_organizer.py ~/downloads --watch --config office.json│
│                                                                             │
│  Outcome: Documents automatically organized as they download.              │
│  Time saved: 15 minutes daily. No more lost documents.                     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 PROJECT ARCHITECTURE DIAGRAMS

### Diagram 1: File Organization Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      FILE ORGANIZER EXECUTION FLOW                           │
└─────────────────────────────────────────────────────────────────────────────┘

┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  USER INPUT  │────►│  LOAD CONFIG │────►│  SCAN DIR    │────►│  FILTER      │
│  (Directory) │     │  (JSON)      │     │  (Files)     │     │  (Exclusions)│
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   OUTPUT     │◄────│   EXECUTE    │◄────│   PREVIEW    │◄────│  CLASSIFY    │
│   (Results)  │     │   MOVES      │     │   (Optional) │     │  FILES       │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
        │
        ├──────────────────┬──────────────────┐
        ▼                  ▼                  ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ JSON Report  │    │ Text Summary │    │ Notification │
└──────────────┘    └──────────────┘    └──────────────┘
```

### Diagram 2: Classification System

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      FILE CLASSIFICATION SYSTEM                              │
└─────────────────────────────────────────────────────────────────────────────┘

                            ┌─────────────────┐
                            │   INPUT FILE    │
                            │   example.jpg   │
                            └────────┬────────┘
                                     │
              ┌──────────────────────┼──────────────────────┐
              │                      │                      │
              ▼                      ▼                      ▼
     ┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
     │ EXTENSION MODE  │   │   DATE MODE     │   │   SIZE MODE     │
     ├─────────────────┤   ├─────────────────┤   ├─────────────────┤
     │ Check .jpg      │   │ Get mtime       │   │ Get file size   │
     │ → Images        │   │ → 2024-01       │   │ → Medium        │
     └────────┬────────┘   └────────┬────────┘   └────────┬────────┘
              │                      │                      │
              ▼                      ▼                      ▼
     ┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
     │ Images/         │   │ 2024-01/        │   │ Medium/         │
     │ example.jpg     │   │ example.jpg     │   │ example.jpg     │
     └─────────────────┘   └─────────────────┘   └─────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│                      DEFAULT CATEGORY MAPPING                                │
└─────────────────────────────────────────────────────────────────────────────┘

  ┌────────────┐    ┌────────────┐    ┌────────────┐    ┌────────────┐
  │  Images/   │    │  Videos/   │    │  Audio/    │    │ Documents/ │
  ├────────────┤    ├────────────┤    ├────────────┤    ├────────────┤
  │ .jpg       │    │ .mp4       │    │ .mp3       │    │ .pdf       │
  │ .png       │    │ .mkv       │    │ .wav       │    │ .doc       │
  │ .gif       │    │ .avi       │    │ .flac      │    │ .docx      │
  │ .svg       │    │ .mov       │    │ .aac       │    │ .txt       │
  │ .webp      │    │ .webm      │    │ .ogg       │    │ .xlsx      │
  └────────────┘    └────────────┘    └────────────┘    └────────────┘

  ┌────────────┐    ┌────────────┐    ┌────────────┐    ┌────────────┐
  │ Archives/  │    │   Code/    │    │   Apps/    │    │  Others/   │
  ├────────────┤    ├────────────┤    ├────────────┤    ├────────────┤
  │ .zip       │    │ .py        │    │ .apk       │    │ (unknown   │
  │ .rar       │    │ .js        │    │ .exe       │    │  types)    │
  │ .7z        │    │ .html      │    │ .deb       │    │            │
  │ .tar       │    │ .css       │    │ .rpm       │    │            │
  │ .gz        │    │ .sh        │    │ .dmg       │    │            │
  └────────────┘    └────────────┘    └────────────┘    └────────────┘
```

### Diagram 3: Watch Mode Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      WATCH MODE ARCHITECTURE                                 │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   ┌─────────────────┐                    ┌─────────────────┐               │
│   │  FILE SYSTEM    │                    │   WATCHDOG      │               │
│   │                 │───────────────────►│   OBSERVER      │               │
│   │  (Downloads/)   │   File Events      │                 │               │
│   └─────────────────┘                    └────────┬────────┘               │
│                                                   │                         │
│                                                   │ Events                  │
│                                                   ▼                         │
│                                          ┌─────────────────┐               │
│                                          │   EVENT         │               │
│                                          │   HANDLER       │               │
│                                          └────────┬────────┘               │
│                                                   │                         │
│                    ┌──────────────────────────────┼──────────────────┐      │
│                    │                              │                  │      │
│                    ▼                              ▼                  ▼      │
│           ┌─────────────────┐          ┌─────────────────┐  ┌───────────┐  │
│           │ on_created      │          │ on_modified     │  │ on_deleted│  │
│           │ (New file)      │          │ (File changed)  │  │ (Removed) │  │
│           └────────┬────────┘          └─────────────────┘  └───────────┘  │
│                    │                                                       │
│                    ▼                                                       │
│           ┌─────────────────┐                                             │
│           │  CLASSIFY &     │                                             │
│           │  ORGANIZE       │                                             │
│           └────────┬────────┘                                             │
│                    │                                                       │
│                    ▼                                                       │
│           ┌─────────────────┐                                             │
│           │  MOVE TO        │                                             │
│           │  CATEGORY       │                                             │
│           └─────────────────┘                                             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Previous Chapter | Current Chapter | Next Chapter |
|-----------------|-----------------|--------------|
| **Ch55: Port Scanner** | **Ch56: File Organizer** | **Ch57: Backup Automation** |

### Prerequisites
| Chapter | Topic | Why It's Needed |
|---------|-------|-----------------|
| Ch47 | Python Basics | File handling foundation |
| Ch48 | Advanced Python | Pathlib and OOP concepts |
| Ch49 | Bash Scripting | Alternative implementation |
| Ch54 | YouTube Downloader | File download context |

### Follow-up Chapters
| Chapter | Topic | Connection |
|---------|-------|------------|
| Ch57 | Backup Automation | Combine with file organization |
| Ch58 | Troubleshooting | Handle file operation errors |
| Ch61 | Security Best Practices | Secure file handling |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Duplicate Detection with Hashing

```python
import hashlib
from pathlib import Path
from collections import defaultdict

class DuplicateFinder:
    def __init__(self):
        self.hash_cache = {}
    
    def calculate_hash(self, filepath: Path, chunk_size: int = 8192) -> str:
        """Calculate MD5 hash of file"""
        # Check cache first
        mtime = filepath.stat().st_mtime
        cache_key = str(filepath)
        if cache_key in self.hash_cache:
            cached_mtime, cached_hash = self.hash_cache[cache_key]
            if cached_mtime == mtime:
                return cached_hash
        
        # Calculate hash
        hasher = hashlib.md5()
        with open(filepath, 'rb') as f:
            while chunk := f.read(chunk_size):
                hasher.update(chunk)
        
        file_hash = hasher.hexdigest()
        self.hash_cache[cache_key] = (mtime, file_hash)
        return file_hash
    
    def find_duplicates(self, directory: Path) -> dict:
        """Find all duplicate files in directory"""
        hash_map = defaultdict(list)
        
        for filepath in directory.rglob('*'):
            if filepath.is_file():
                file_hash = self.calculate_hash(filepath)
                hash_map[file_hash].append(filepath)
        
        # Return only duplicates
        return {h: files for h, files in hash_map.items() if len(files) > 1}
    
    def handle_duplicates(self, duplicates: dict, action: str = 'report'):
        """Handle found duplicates"""
        results = []
        
        for file_hash, files in duplicates.items():
            # Keep first file, handle others
            original = files[0]
            duplicates_to_handle = files[1:]
            
            for dup in duplicates_to_handle:
                if action == 'delete':
                    dup.unlink()
                    results.append(f"Deleted: {dup}")
                elif action == 'move':
                    dest = dup.parent / 'Duplicates' / dup.name
                    dest.parent.mkdir(exist_ok=True)
                    dup.rename(dest)
                    results.append(f"Moved: {dup}")
                else:
                    results.append(f"Found: {dup} (duplicate of {original})")
        
        return results
```

---

### Advanced Technique 2: Smart Content-Based Classification

```python
import magic
from pathlib import Path

class ContentClassifier:
    def __init__(self):
        # Try to use python-magic, fallback to extension
        try:
            self.mime = magic.Magic(mime=True)
            self.use_magic = True
        except:
            self.use_magic = False
    
    def get_mime_type(self, filepath: Path) -> str:
        """Get MIME type of file"""
        if self.use_magic:
            return self.mime.from_file(str(filepath))
        return self.guess_from_extension(filepath)
    
    def guess_from_extension(self, filepath: Path) -> str:
        """Fallback: guess MIME from extension"""
        extension_map = {
            '.jpg': 'image/jpeg',
            '.png': 'image/png',
            '.pdf': 'application/pdf',
            '.mp4': 'video/mp4',
            '.mp3': 'audio/mpeg',
            '.py': 'text/x-python',
            '.zip': 'application/zip',
        }
        return extension_map.get(filepath.suffix.lower(), 'application/octet-stream')
    
    def classify_by_content(self, filepath: Path) -> str:
        """Classify file based on actual content, not extension"""
        mime_type = self.get_mime_type(filepath)
        
        category_map = {
            'image': 'Images',
            'video': 'Videos',
            'audio': 'Audio',
            'application/pdf': 'Documents',
            'text': 'Documents',
            'application/zip': 'Archives',
        }
        
        for key, category in category_map.items():
            if key in mime_type:
                return category
        
        return 'Others'
```

---

### Advanced Technique 3: Organization Statistics Dashboard

```python
from pathlib import Path
from collections import Counter
from datetime import datetime
import json

class OrganizationStats:
    def __init__(self, directory: Path):
        self.directory = directory
        self.stats = {
            'total_files': 0,
            'total_size': 0,
            'by_extension': Counter(),
            'by_category': Counter(),
            'by_size': Counter(),
            'by_date': Counter(),
            'largest_files': [],
        }
    
    def analyze(self):
        """Collect statistics about files"""
        files = []
        
        for filepath in self.directory.rglob('*'):
            if filepath.is_file():
                stat = filepath.stat()
                files.append({
                    'path': filepath,
                    'size': stat.st_size,
                    'mtime': datetime.fromtimestamp(stat.st_mtime),
                    'extension': filepath.suffix.lower(),
                })
        
        self.stats['total_files'] = len(files)
        self.stats['total_size'] = sum(f['size'] for f in files)
        
        for f in files:
            self.stats['by_extension'][f['extension']] += 1
            self.stats['by_category'][self._get_category(f['extension'])] += 1
            self.stats['by_size'][self._size_category(f['size'])] += 1
            self.stats['by_date'][f['mtime'].strftime('%Y-%m')] += 1
        
        # Find largest files
        sorted_files = sorted(files, key=lambda x: x['size'], reverse=True)[:10]
        self.stats['largest_files'] = [
            {'path': str(f['path']), 'size': self._format_size(f['size'])}
            for f in sorted_files
        ]
    
    def generate_report(self) -> str:
        """Generate human-readable report"""
        report = []
        report.append("=" * 50)
        report.append("FILE ORGANIZATION STATISTICS REPORT")
        report.append("=" * 50)
        report.append(f"\nTotal Files: {self.stats['total_files']}")
        report.append(f"Total Size: {self._format_size(self.stats['total_size'])}")
        
        report.append("\n📁 By Category:")
        for category, count in self.stats['by_category'].most_common():
            report.append(f"  {category}: {count} files")
        
        report.append("\n📊 By Size:")
        for size_cat, count in self.stats['by_size'].most_common():
            report.append(f"  {size_cat}: {count} files")
        
        report.append("\n🏆 Top 10 Largest Files:")
        for f in self.stats['largest_files']:
            report.append(f"  {f['size']}: {f['path']}")
        
        return "\n".join(report)
    
    def _format_size(self, size: int) -> str:
        for unit in ['B', 'KB', 'MB', 'GB']:
            if size < 1024:
                return f"{size:.1f} {unit}"
            size /= 1024
        return f"{size:.1f} TB"
    
    def _get_category(self, ext: str) -> str:
        categories = {
            'Images': ['.jpg', '.png', '.gif', '.svg'],
            'Videos': ['.mp4', '.mkv', '.avi'],
            'Audio': ['.mp3', '.wav', '.flac'],
            'Documents': ['.pdf', '.doc', '.txt'],
            'Code': ['.py', '.js', '.html'],
        }
        for cat, exts in categories.items():
            if ext in exts:
                return cat
        return 'Others'
    
    def _size_category(self, size: int) -> str:
        if size < 1024 * 1024:
            return 'Small'
        elif size < 100 * 1024 * 1024:
            return 'Medium'
        else:
            return 'Large'
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### ✅ Knowledge Checkpoint

- [ ] I understand the purpose and benefits of file organization
- [ ] I can implement extension-based file sorting
- [ ] I know how to implement date-based file sorting
- [ ] I can implement size-based file sorting
- [ ] I understand how to use Python pathlib for file operations
- [ ] I know how to create and use JSON configuration files
- [ ] I can implement preview mode for safe testing
- [ ] I understand how to implement undo functionality
- [ ] I know how to use the watchdog library for file monitoring
- [ ] I can handle file naming conflicts
- [ ] I understand recursive directory traversal
- [ ] I can implement custom organization rules
- [ ] I know how to handle special files and errors
- [ ] I can generate organization reports

### 🎯 Skills Acquired

| Skill | Level |
|-------|-------|
| File Handling (pathlib) | ⭐⭐⭐⭐⭐ |
| JSON Configuration | ⭐⭐⭐⭐ |
| Event Monitoring | ⭐⭐⭐⭐ |
| Error Handling | ⭐⭐⭐⭐ |
| Python Development | ⭐⭐⭐⭐ |
| Automation | ⭐⭐⭐⭐⭐ |

---

## 🚀 PROJECT CHALLENGES

### Challenge 1: Add Duplicate Detection Feature

**Task:** Extend the file organizer to detect and handle duplicate files.

**Requirements:**
- Calculate file hashes for comparison
- Group files by hash to find duplicates
- Provide options: delete, move to Duplicates folder, or report only
- Handle large files efficiently with chunked hashing

**Hint:** Use `hashlib.md5()` with chunked reading for memory efficiency.

**Estimated Time:** 2-3 hours

---

### Challenge 2: Implement EXIF-Based Photo Organization

**Task:** Organize photos using their EXIF metadata instead of file dates.

**Requirements:**
- Extract EXIF data from image files
- Use DateTimeOriginal for date-based folders
- Handle images without EXIF gracefully (fallback to file date)
- Support common image formats (JPEG, PNG, HEIC)

**Hint:** Use `PIL` or `exifread` library for EXIF extraction.

**Estimated Time:** 2-3 hours

---

### Challenge 3: Build a Web Interface for File Organization

**Task:** Create a Flask web app for visual file organization.

**Requirements:**
- Web interface to select directories and modes
- Real-time progress display during organization
- Preview and confirm interface
- History of past organizations
- Download organization reports

**Hint:** Use Flask-SocketIO for real-time progress updates.

**Estimated Time:** 4-5 hours

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always use preview mode (`--preview`) first to see what will happen!

> 💡 **Pro Tip #2:** Use watch mode (`--watch`) to automatically organize new downloads!

> 💡 **Pro Tip #3:** Create custom rules in JSON for project-specific organization!

> 💡 **Pro Tip #4:** The undo feature only works for the LAST operation - be careful!

> 💡 **Pro Tip #5:** Combine with Ch54 YouTube Downloader - auto-organize downloaded files!

> 💡 **Pro Tip #6:** Use `--recursive` for deep cleaning of nested folders!

> 💡 **Pro Tip #7:** Date-based sorting is perfect for photos and videos!

> 💡 **Pro Tip #8:** Exclude system folders in config to prevent accidents!

> 💡 **Pro Tip #9:** Size-based sorting helps identify large files wasting space!

> 💡 **Pro Tip #10:** Set up a cron job to run organizer weekly automatically!

---

## 🔥 REAL WORLD USE CASES

### Real World Applications of File Organizer

**1. Downloads Folder Cleanup**
- Auto-organize messy downloads
- Find files quickly by type
- Save time searching

**2. Photo Organization**
- Sort by date for photo libraries
- Separate by file type
- Create yearly/monthly archives

**3. Project File Management**
- Organize by file type
- Keep project folders clean
- Separate source code from assets

**4. Download Automation**
- Combine with download tools
- Real-time organization
- Set-and-forget workflow

**5. Storage Optimization**
- Find large files easily
- Identify duplicate types
- Clean up clutter

**6. Office Document Management**
- Organize by document type
- Sort by date for records
- Create document archives

---

## ⚡ QUICK REFERENCE CARD

### File Organizer Quick Reference

| Mode | Command | Description |
|------|---------|-------------|
| Extension | `--mode extension` | Sort by file type |
| Date | `--mode date` | Sort by date |
| Size | `--mode size` | Sort by file size |
| Preview | `--preview` | Show without moving |
| Watch | `--watch` | Real-time monitoring |
| Recursive | `--recursive` | Include subfolders |
| Undo | `--undo` | Reverse last operation |
| Config | `--config file.json` | Use custom rules |

### Default Categories

| Category | Extensions |
|----------|------------|
| Images | .jpg, .png, .gif, .svg, .webp |
| Videos | .mp4, .mkv, .avi, .mov, .webm |
| Audio | .mp3, .wav, .flac, .aac, .ogg |
| Documents | .pdf, .doc, .docx, .txt, .xlsx |
| Archives | .zip, .rar, .7z, .tar, .gz |
| Code | .py, .js, .html, .css, .java |
| Apps | .apk, .exe, .deb, .dmg |

### Size Categories

| Category | Size Range |
|----------|------------|
| Tiny | 0 - 100 KB |
| Small | 100 KB - 1 MB |
| Medium | 1 MB - 100 MB |
| Large | 100 MB - 1 GB |
| Huge | > 1 GB |

---

## 🏆 BONUS CONTENT

### Bonus: Advanced Features to Add

**Feature 1: Duplicate Detection**
```python
import hashlib
def find_duplicates(directory):
    """Find and list duplicate files by hash"""
    hashes = {}
    for file in directory:
        file_hash = hash_file(file)
        if file_hash in hashes:
            duplicates.append(file)
        else:
            hashes[file_hash] = file
```

**Feature 2: Smart Naming**
```python
def smart_rename(file):
    """Rename files with intelligent patterns"""
    # Remove special characters
    # Add date prefix
    # Convert to lowercase
```

**Feature 3: Compression on Organize**
```python
def organize_and_compress(source, category):
    """Compress old files while organizing"""
    if file_age > 30_days:
        compress(file)
    move(file, category)
```

**Feature 4: Cloud Sync**
```python
def sync_to_cloud(category, provider='dropbox'):
    """Sync organized files to cloud"""
    # Upload new files
    # Track sync status
```

**Feature 5: Statistics Dashboard**
```python
def show_stats(directory):
    """Show file type distribution"""
    # Pie chart by type
    # Size distribution
    # File age histogram
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **Extension-Based Sorting** - Organize files by type
- ✅ **Date-Based Sorting** - Organize by creation/modification date
- ✅ **Size-Based Sorting** - Categorize by file size
- ✅ **Custom Rules** - JSON configuration for special cases
- ✅ **Preview Mode** - Safe testing before moving
- ✅ **Undo Functionality** - Reverse last operation
- ✅ **Watch Mode** - Real-time file monitoring
- ✅ **Recursive Operations** - Deep folder scanning

### Key Takeaways

1. **Preview first** - Always check before moving files
2. **History tracking** - Essential for undo feature
3. **Modular design** - Each mode is independent
4. **Error handling** - Skip problematic files gracefully
5. **Configuration** - JSON makes rules flexible

---

## 🚀 PROJECT EXTENSIONS

### 5+ Ideas to Extend This Project

**Extension 1: GUI Interface** ⭐⭐⭐⭐
- Visual drag-and-drop organization
- Real-time preview with icons
- **Steps:** Use tkinter or web interface

**Extension 2: Duplicate Finder** ⭐⭐⭐⭐
- Find duplicate files by hash
- Option to delete duplicates
- **Steps:** Add hashlib, create comparison module

**Extension 3: Smart Sort with AI** ⭐⭐⭐⭐⭐
- ML-based content categorization
- Learn user preferences
- **Steps:** Integrate TensorFlow Lite model

**Extension 4: Network Storage Support** ⭐⭐⭐
- Organize files on SMB/NFS
- Cloud storage integration
- **Steps:** Add network file system support

**Extension 5: Backup Before Organize** ⭐⭐⭐
- Create backup before major changes
- Incremental backup support
- **Steps:** Integrate with Ch57 Backup tool

**Extension 6: File Statistics Dashboard** ⭐⭐⭐⭐
- Visual charts of file distribution
- Storage usage reports
- **Steps:** Use matplotlib or web charts

---

## 🔧 CODE WALKTHROUGH

### File Organizer Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    FILE ORGANIZER ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   SOURCE DIRECTORY                                                   │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │ 📁 downloads/                                                │   │
│   │ ├── 📄 document.pdf                                         │   │
│   │ ├── 🖼️ photo.jpg                                            │   │
│   │ ├── 🎵 song.mp3                                             │   │
│   │ └── 🎬 video.mp4                                            │   │
│   └─────────────────────────────────────────────────────────────┘   │
│                          │                                           │
│                          ▼                                           │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │                    SCANNER MODULE                            │   │
│   │  • List all files                                            │   │
│   │  • Get file metadata (size, date, extension)                 │   │
│   │  • Apply filters (exclude patterns)                          │   │
│   └─────────────────────────────────────────────────────────────┘   │
│                          │                                           │
│                          ▼                                           │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │                    CLASSIFIER MODULE                         │   │
│   │  Extension Mode → Match extension to category                │   │
│   │  Date Mode → Extract date from metadata                      │   │
│   │  Size Mode → Calculate size category                         │   │
│   └─────────────────────────────────────────────────────────────┘   │
│                          │                                           │
│                          ▼                                           │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │                    ACTION MODULE                             │   │
│   │  Preview Mode → Display only                                 │   │
│   │  Normal Mode → Create folders & move files                   │   │
│   │  Watch Mode → Monitor for new files                          │   │
│   └─────────────────────────────────────────────────────────────┘   │
│                          │                                           │
│                          ▼                                           │
│   ORGANIZED RESULT                                                   │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │ 📁 downloads/                                                │   │
│   │ ├── 📁 Documents/📄 document.pdf                            │   │
│   │ ├── 📁 Images/🖼️ photo.jpg                                 │   │
│   │ ├── 📁 Audio/🎵 song.mp3                                    │   │
│   │ └── 📁 Videos/🎬 video.mp4                                  │   │
│   └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 📦 DEPLOYMENT GUIDE

### How to Deploy and Share This Project

**1. Create Project**
```bash
mkdir -p ~/file-organizer
cd ~/file-organizer
```

**2. Install Dependencies**
```bash
pip install watchdog  # For watch mode
```

**3. Create Config File**
```json
{
    "rules": {},
    "exclude_folders": ["System", ".git"],
    "exclude_files": [".nomedia", ".gitignore"]
}
```

**4. Set Up Cron Job**
```bash
# Weekly organization
crontab -e
# Add: 0 0 * * 0 python ~/file-organizer/file_organizer.py ~/storage/downloads
```

**5. Create Alias**
```bash
echo 'alias organize="python ~/file-organizer/file_organizer.py"' >> ~/.bashrc
```

---

## 🔗 RELATED CHAPTERS

### Cross-Reference to Related Chapters

| Chapter | Topic | Connection |
|---------|-------|------------|
| **Ch54** | YouTube Downloader | Organize downloaded files |
| **Ch57** | Backup Automation | Backup before organizing |
| **Ch47** | Python Basics | File operations |
| **Ch49** | Bash Scripting | Alternative implementation |

### Next Steps
- ➡️ **Ch57: Backup Automation** - Data protection
- ➡️ **Ch58** - Troubleshooting

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your File Organizer Knowledge!

**Question 1:** Which mode sorts files by type?
- a) `--mode type`
- b) `--mode extension` ✓
- c) `--mode category`
- d) `--sort type`

**Question 2:** What does `--preview` do?
- a) Shows file thumbnails
- b) Shows what would happen without moving ✓
- c) Previews file content
- d) Shows progress

**Question 3:** Which Python module is used for file monitoring?
- a) monitor
- b) watchdog ✓
- c) observer
- d) filewatch

**Question 4:** What is the undo limit?
- a) Unlimited
- b) 10 operations
- c) Last operation only ✓
- d) 5 operations

**Question 5:** Which function moves files?
- a) os.move()
- b) shutil.move() ✓
- c) file.move()
- d) move.file()

**Question 6:** What does recursive mode do?
- a) Repeats organization
- b) Includes subfolders ✓
- c) Creates backup
- d) Shows progress

**Question 7:** What file contains custom rules?
- a) rules.txt
- b) config.json ✓
- c) settings.py
- d) organizer.cfg

**Question 8:** How to organize by date?
- a) `--mode time`
- b) `--mode date` ✓
- c) `--sort date`
- d) `--by-date`

**Question 9:** What is used to track operations for undo?
- a) Log file
- b) History file ✓
- c) Memory only
- d) Database

**Question 10:** Which function gets file extension?
- a) os.path.splitext() ✓
- b) file.extension()
- c) get.extension()
- d) os.getext()

**Question 11:** What category is .py file?
- a) Scripts
- b) Code ✓
- c) Python
- d) Programming

**Question 12:** What is the default Downloads folder in Termux?
- a) ~/downloads
- b) ~/storage/downloads ✓
- c) /sdcard/downloads
- d) ~/Downloads

---

### Extend the Project Challenges

**Challenge 1:** Add file content analysis
```python
def analyze_content(file_path):
    # Detect file type by content, not extension
    # Use magic numbers/file signatures
```

**Challenge 2:** Implement batch rename
```python
def batch_rename(directory, pattern):
    # Rename all files matching pattern
    # Support placeholders like {date}, {counter}
```

**Challenge 3:** Add file compression
```python
def compress_old_files(directory, days=30):
    # Compress files older than X days
    # Save space while keeping access
```

### Bug Fixing Exercises

**Bug 1:** Files disappear on organize
```python
shutil.move(src, dst)  # Overwrites if exists!
```
*Fix: Check if destination exists, add suffix*

**Bug 2:** Watch mode doesn't trigger
```python
def on_created(event):
    organize_file(event.src_path)  # Too early!
```
*Fix: Add small delay, file might still be copying*

**Bug 3:** Extension not recognized
```python
ext = file.suffix  # Includes the dot!
```
*Fix: Use file.suffix.lower() or file.suffix[1:]*

---

## 📖 TECHNICAL GUIDE

### 1. Project Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    FILE ORGANIZER PROJECT OVERVIEW                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Project Name: File Organizer Tool                                       │
│  Version: 1.0                                                            │
│  Language: Python 3                                                      │
│  Dependencies: Python3, watchdog (for watch mode)                        │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                      PROJECT STRUCTURE                           │    │
│  ├─────────────────────────────────────────────────────────────────┤    │
│  │                                                                  │    │
│  │  file_organizer/                                                 │    │
│  │  ├── file_organizer.py      # Main organizer script              │    │
│  │  ├── organizer_config.json  # Configuration file                 │    │
│  │  ├── organizer_history.json # Operation history (auto-generated) │    │
│  │  ├── organizer.log          # Log file (auto-generated)          │    │
│  │  └── README.md              # Documentation                      │    │
│  │                                                                  │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  Use Case: Automatic file organization, cleanup automation              │
│  Skill Level: Intermediate                                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. File Organization Logic

#### Extension-Based Classification

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    EXTENSION CATEGORIES                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  IMAGES                                                          │    │
│  │  .jpg, .jpeg, .png, .gif, .bmp, .svg, .webp, .ico, .tiff        │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  VIDEOS                                                          │    │
│  │  .mp4, .mkv, .avi, .mov, .wmv, .flv, .webm, .m4v, .3gp          │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  AUDIO                                                           │    │
│  │  .mp3, .wav, .flac, .aac, .ogg, .m4a, .wma, .opus               │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  DOCUMENTS                                                       │    │
│  │  .pdf, .doc, .docx, .txt, .xls, .xlsx, .ppt, .pptx, .odt        │    │
│  │  .rtf, .csv, .md                                                 │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  ARCHIVES                                                        │    │
│  │  .zip, .rar, .7z, .tar, .gz, .bz2, .xz, .iso                     │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  CODE                                                            │    │
│  │  .py, .js, .ts, .html, .css, .java, .cpp, .c, .go, .rs, .sh     │    │
│  │  .php, .rb, .swift, .kt, .json, .xml, .yaml, .sql               │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  APPS & EXECUTABLES                                              │    │
│  │  .apk, .exe, .deb, .rpm, .dmg, .app, .msi, .jar                  │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  OTHERS (Default)                                                │    │
│  │  Files that don't match any category                             │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Date-Based Organization Structure

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    DATE ORGANIZATION PATTERNS                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Pattern 1: Year-Month (Default)                                        │
│  ┌───────────────────────────────────────────────────────────────┐     │
│  │ folder/                                                        │     │
│  │ ├── 2024-01/  (January 2024)                                  │     │
│  │ │   ├── file1.pdf                                             │     │
│  │ │   └── file2.jpg                                             │     │
│  │ ├── 2024-02/  (February 2024)                                 │     │
│  │ └── 2024-03/  (March 2024)                                    │     │
│  └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
│  Pattern 2: Year Only                                                   │
│  ┌───────────────────────────────────────────────────────────────┐     │
│  │ folder/                                                        │     │
│  │ ├── 2023/                                                     │     │
│  │ ├── 2024/                                                     │     │
│  │ └── 2025/                                                     │     │
│  └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
│  Pattern 3: Year/Month Hierarchy                                        │
│  ┌───────────────────────────────────────────────────────────────┐     │
│  │ folder/                                                        │     │
│  │ ├── 2024/                                                     │     │
│  │ │   ├── 01-January/                                           │     │
│  │ │   ├── 02-February/                                          │     │
│  │ │   └── 03-March/                                             │     │
│  │ └── 2025/                                                     │     │
│  └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Size-Based Classification

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SIZE CATEGORIES                                       │
├──────────────────┬───────────────────────────────────────────────────────┤
│ Category         │ Size Range                                           │
├──────────────────┼───────────────────────────────────────────────────────┤
│ Tiny             │ 0 - 100 KB (kilobytes)                               │
│ Small            │ 100 KB - 1 MB                                        │
│ Medium           │ 1 MB - 100 MB                                        │
│ Large            │ 100 MB - 1 GB                                        │
│ Huge             │ > 1 GB                                               │
└──────────────────┴───────────────────────────────────────────────────────┘

Size Calculation:
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  1 Byte = 8 bits                                                        │
│  1 KB (Kilobyte) = 1024 Bytes                                           │
│  1 MB (Megabyte) = 1024 KB = 1,048,576 Bytes                            │
│  1 GB (Gigabyte) = 1024 MB = 1,073,741,824 Bytes                        │
│                                                                          │
│  Python conversion:                                                     │
│  size_bytes = file_path.stat().st_size                                  │
│  size_mb = size_bytes / (1024 * 1024)                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Features Implementation

#### Feature 1: Sort by Extension

```python
import os
import shutil
from pathlib import Path
from typing import Dict, List, Optional

# Default category mappings
DEFAULT_CATEGORIES: Dict[str, List[str]] = {
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.svg', '.webp', 
               '.ico', '.tiff', '.tif', '.raw', '.heic', '.heif'],
    'Videos': ['.mp4', '.mkv', '.avi', '.mov', '.wmv', '.flv', '.webm', 
               '.m4v', '.3gp', '.mpeg', '.mpg', '.vob'],
    'Audio': ['.mp3', '.wav', '.flac', '.aac', '.ogg', '.m4a', '.wma', 
              '.opus', '.aiff', '.ape', '.amr'],
    'Documents': ['.pdf', '.doc', '.docx', '.txt', '.xls', '.xlsx', 
                  '.ppt', '.pptx', '.odt', '.rtf', '.csv', '.md', 
                  '.odp', '.ods', '.pages', '.numbers'],
    'Archives': ['.zip', '.rar', '.7z', '.tar', '.gz', '.bz2', 
                 '.xz', '.iso', '.dmg', '.tgz'],
    'Code': ['.py', '.js', '.ts', '.html', '.css', '.java', '.cpp', 
             '.c', '.go', '.rs', '.sh', '.php', '.rb', '.swift', 
             '.kt', '.json', '.xml', '.yaml', '.yml', '.sql', '.bat'],
    'Apps': ['.apk', '.exe', '.deb', '.rpm', '.app', '.msi', '.jar', '.appimage'],
    'Ebooks': ['.epub', '.mobi', '.azw', '.azw3', '.fb2'],
    'Fonts': ['.ttf', '.otf', '.woff', '.woff2', '.eot']
}

def get_category(extension: str, categories: Optional[Dict] = None) -> str:
    """
    Determine the category for a file extension.
    
    Args:
        extension: File extension (including dot, e.g., '.jpg')
        categories: Custom categories dict (optional)
    
    Returns:
        Category name string
    """
    if categories is None:
        categories = DEFAULT_CATEGORIES
    
    ext = extension.lower()
    
    for category, extensions in categories.items():
        if ext in [e.lower() for e in extensions]:
            return category
    
    return 'Others'

def organize_by_extension(
    source_dir: str,
    categories: Optional[Dict] = None,
    create_others: bool = True,
    dry_run: bool = False
) -> List[Dict]:
    """
    Organize files by their extensions.
    
    Args:
        source_dir: Directory to organize
        categories: Custom category mappings
        create_others: Create 'Others' folder for unmatched files
        dry_run: If True, don't actually move files
    
    Returns:
        List of operations performed
    """
    source = Path(source_dir)
    operations = []
    
    if categories is None:
        categories = DEFAULT_CATEGORIES
    
    for file_path in source.iterdir():
        if file_path.is_file():
            # Get category for this file
            category = get_category(file_path.suffix, categories)
            
            # Skip 'Others' if not creating that folder
            if category == 'Others' and not create_others:
                continue
            
            # Create destination folder
            dest_folder = source / category
            
            if not dry_run:
                dest_folder.mkdir(exist_ok=True)
            
            # Handle name conflicts
            dest_path = dest_folder / file_path.name
            if dest_path.exists():
                base = file_path.stem
                suffix = file_path.suffix
                counter = 1
                while dest_path.exists():
                    new_name = f"{base}_{counter}{suffix}"
                    dest_path = dest_folder / new_name
                    counter += 1
            
            # Record operation
            operation = {
                'source': str(file_path),
                'destination': str(dest_path),
                'category': category,
                'filename': file_path.name
            }
            operations.append(operation)
            
            # Move file (if not dry run)
            if not dry_run:
                shutil.move(str(file_path), str(dest_path))
    
    return operations
```

#### Feature 2: Sort by Date

```python
from datetime import datetime
from typing import Literal

def organize_by_date(
    source_dir: str,
    date_type: Literal['modified', 'created', 'accessed'] = 'modified',
    pattern: Literal['year-month', 'year', 'year-month-name'] = 'year-month',
    dry_run: bool = False
) -> List[Dict]:
    """
    Organize files by their date.
    
    Args:
        source_dir: Directory to organize
        date_type: Which date to use (modified, created, accessed)
        pattern: Folder naming pattern
        dry_run: Preview mode
    
    Returns:
        List of operations performed
    """
    source = Path(source_dir)
    operations = []
    
    # Map date type to stat attribute
    date_attrs = {
        'modified': 'st_mtime',
        'created': 'st_ctime',
        'accessed': 'st_atime'
    }
    date_attr = date_attrs.get(date_type, 'st_mtime')
    
    # Date format patterns
    date_patterns = {
        'year-month': '%Y-%m',
        'year': '%Y',
        'year-month-name': '%Y-%B'
    }
    date_format = date_patterns.get(pattern, '%Y-%m')
    
    for file_path in source.iterdir():
        if file_path.is_file():
            # Get file timestamp
            stat = file_path.stat()
            timestamp = getattr(stat, date_attr)
            
            # Convert to datetime
            date = datetime.fromtimestamp(timestamp)
            folder_name = date.strftime(date_format)
            
            # Create destination folder
            dest_folder = source / folder_name
            
            if not dry_run:
                dest_folder.mkdir(exist_ok=True)
            
            # Handle name conflicts
            dest_path = dest_folder / file_path.name
            if dest_path.exists():
                base = file_path.stem
                suffix = file_path.suffix
                counter = 1
                while dest_path.exists():
                    dest_path = dest_folder / f"{base}_{counter}{suffix}"
                    counter += 1
            
            # Record operation
            operations.append({
                'source': str(file_path),
                'destination': str(dest_path),
                'folder': folder_name,
                'date': date.isoformat(),
                'filename': file_path.name
            })
            
            # Move file
            if not dry_run:
                shutil.move(str(file_path), str(dest_path))
    
    return operations
```

#### Feature 3: Sort by Size

```python
def format_size(size_bytes: int) -> str:
    """Convert bytes to human-readable format."""
    for unit in ['B', 'KB', 'MB', 'GB', 'TB']:
        if size_bytes < 1024:
            return f"{size_bytes:.2f} {unit}"
        size_bytes /= 1024
    return f"{size_bytes:.2f} PB"

def organize_by_size(
    source_dir: str,
    size_categories: Optional[Dict[str, tuple]] = None,
    dry_run: bool = False
) -> List[Dict]:
    """
    Organize files by their size.
    
    Args:
        source_dir: Directory to organize
        size_categories: Dict of {category_name: (min_bytes, max_bytes)}
        dry_run: Preview mode
    
    Returns:
        List of operations performed
    """
    source = Path(source_dir)
    operations = []
    
    # Default size categories (in bytes)
    if size_categories is None:
        KB = 1024
        MB = KB * 1024
        GB = MB * 1024
        
        size_categories = {
            'Tiny': (0, 100 * KB),
            'Small': (100 * KB, MB),
            'Medium': (MB, 100 * MB),
            'Large': (100 * MB, GB),
            'Huge': (GB, float('inf'))
        }
    
    def get_size_category(size: int) -> str:
        """Determine size category for a file."""
        for category, (min_size, max_size) in size_categories.items():
            if min_size <= size < max_size:
                return category
        return 'Unknown'
    
    for file_path in source.iterdir():
        if file_path.is_file():
            size = file_path.stat().st_size
            category = get_size_category(size)
            
            # Create destination folder
            dest_folder = source / category
            
            if not dry_run:
                dest_folder.mkdir(exist_ok=True)
            
            # Handle name conflicts
            dest_path = dest_folder / file_path.name
            if dest_path.exists():
                base = file_path.stem
                suffix = file_path.suffix
                counter = 1
                while dest_path.exists():
                    dest_path = dest_folder / f"{base}_{counter}{suffix}"
                    counter += 1
            
            # Record operation
            operations.append({
                'source': str(file_path),
                'destination': str(dest_path),
                'category': category,
                'size_bytes': size,
                'size_human': format_size(size),
                'filename': file_path.name
            })
            
            # Move file
            if not dry_run:
                shutil.move(str(file_path), str(dest_path))
    
    return operations
```

#### Feature 4: Custom Rules

```python
import json
import fnmatch
from typing import Any, Dict

class CustomRules:
    """Handle custom organization rules from JSON config."""
    
    def __init__(self, config_path: str):
        self.config_path = Path(config_path)
        self.config = self._load_config()
    
    def _load_config(self) -> Dict[str, Any]:
        """Load configuration from JSON file."""
        if not self.config_path.exists():
            return self._get_default_config()
        
        with open(self.config_path, 'r') as f:
            return json.load(f)
    
    def _get_default_config(self) -> Dict[str, Any]:
        """Return default configuration."""
        return {
            'rules': DEFAULT_CATEGORIES,
            'exclude_folders': [],
            'exclude_files': [],
            'naming_convention': 'original',
            'conflict_resolution': 'rename'
        }
    
    def get_category_for_file(self, filename: str) -> Optional[str]:
        """
        Get category for a file using custom rules.
        
        Supports:
        - Exact extension match: '.pdf'
        - Wildcard patterns: '*.temp', 'backup_*'
        """
        rules = self.config.get('rules', {})
        filename_lower = filename.lower()
        
        for category, patterns in rules.items():
            for pattern in patterns:
                # Handle extension patterns
                if pattern.startswith('.'):
                    if filename_lower.endswith(pattern.lower()):
                        return category
                # Handle wildcard patterns
                elif '*' in pattern:
                    if fnmatch.fnmatch(filename_lower, pattern.lower()):
                        return category
                # Exact match
                elif filename_lower == pattern.lower():
                    return category
        
        return None
    
    def should_exclude(self, filename: str, is_folder: bool = False) -> bool:
        """Check if file/folder should be excluded."""
        if is_folder:
            return filename in self.config.get('exclude_folders', [])
        return filename in self.config.get('exclude_files', [])
    
    def organize_with_rules(
        self,
        source_dir: str,
        dry_run: bool = False
    ) -> List[Dict]:
        """Organize files using custom rules."""
        source = Path(source_dir)
        operations = []
        
        for file_path in source.iterdir():
            if file_path.is_file():
                # Check exclusions
                if self.should_exclude(file_path.name):
                    continue
                
                # Get category
                category = self.get_category_for_file(file_path.name)
                
                if category is None:
                    category = 'Others'
                
                # Create destination folder
                dest_folder = source / category
                
                if not dry_run:
                    dest_folder.mkdir(exist_ok=True)
                
                # Handle conflicts
                dest_path = dest_folder / file_path.name
                if dest_path.exists():
                    dest_path = self._resolve_conflict(file_path, dest_folder)
                
                operations.append({
                    'source': str(file_path),
                    'destination': str(dest_path),
                    'category': category,
                    'filename': file_path.name
                })
                
                if not dry_run:
                    shutil.move(str(file_path), str(dest_path))
        
        return operations
    
    def _resolve_conflict(self, source: Path, dest_folder: Path) -> Path:
        """Resolve file name conflicts."""
        resolution = self.config.get('conflict_resolution', 'rename')
        
        if resolution == 'rename':
            base = source.stem
            suffix = source.suffix
            counter = 1
            dest_path = dest_folder / f"{base}_{counter}{suffix}"
            while dest_path.exists():
                counter += 1
                dest_path = dest_folder / f"{base}_{counter}{suffix}"
            return dest_path
        elif resolution == 'skip':
            return source  # Don't move
        elif resolution == 'overwrite':
            return dest_folder / source.name
        
        return dest_folder / source.name

def create_sample_config(output_path: str):
    """Create a sample configuration file."""
    config = {
        'rules': {
            'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.svg', '.webp'],
            'Videos': ['.mp4', '.mkv', '.avi', '.mov', '.wmv'],
            'Audio': ['.mp3', '.wav', '.flac', '.aac', '.ogg'],
            'Documents': ['.pdf', '.doc', '.docx', '.txt', '.xls', '.xlsx'],
            'Archives': ['.zip', '.rar', '.7z', '.tar', '.gz'],
            'Code': ['.py', '.js', '.html', '.css', '.java', '.cpp', '.sh'],
            'Apps': ['.apk', '.exe', '.deb'],
            'Work': ['.work', '*.project'],
            'Personal': ['.personal', '*.private'],
            'Downloads': ['.torrent', '.part', '*.tmp']
        },
        'exclude_folders': ['System', 'Important', 'DoNotTouch'],
        'exclude_files': ['.nomedia', '.gitignore', 'README.md', 'LICENSE'],
        'naming_convention': 'original',
        'conflict_resolution': 'rename'
    }
    
    with open(output_path, 'w') as f:
        json.dump(config, f, indent=2)
    
    return output_path
```

#### Feature 5: Preview Mode

```python
from typing import List, Dict
from datetime import datetime

class PreviewMode:
    """Preview organization changes without executing."""
    
    def __init__(self, source_dir: str):
        self.source_dir = Path(source_dir)
        self.changes: List[Dict] = []
    
    def preview_extension_sort(self, categories: Optional[Dict] = None) -> List[Dict]:
        """Preview extension-based organization."""
        self.changes = []
        
        for file_path in self.source_dir.iterdir():
            if file_path.is_file():
                category = get_category(file_path.suffix, categories)
                dest = self.source_dir / category / file_path.name
                
                self.changes.append({
                    'type': 'move',
                    'source': str(file_path),
                    'destination': str(dest),
                    'filename': file_path.name,
                    'category': category
                })
        
        return self.changes
    
    def preview_date_sort(
        self,
        date_type: str = 'modified',
        pattern: str = 'year-month'
    ) -> List[Dict]:
        """Preview date-based organization."""
        self.changes = []
        
        date_attrs = {'modified': 'st_mtime', 'created': 'st_ctime'}
        date_attr = date_attrs.get(date_type, 'st_mtime')
        date_formats = {'year-month': '%Y-%m', 'year': '%Y'}
        date_format = date_formats.get(pattern, '%Y-%m')
        
        for file_path in self.source_dir.iterdir():
            if file_path.is_file():
                timestamp = getattr(file_path.stat(), date_attr)
                date = datetime.fromtimestamp(timestamp)
                folder_name = date.strftime(date_format)
                dest = self.source_dir / folder_name / file_path.name
                
                self.changes.append({
                    'type': 'move',
                    'source': str(file_path),
                    'destination': str(dest),
                    'filename': file_path.name,
                    'date_folder': folder_name
                })
        
        return self.changes
    
    def display_preview(self, max_items: int = 50) -> None:
        """Display preview in formatted output."""
        print("\n" + "=" * 60)
        print("📋 PREVIEW MODE - No files will be moved")
        print("=" * 60 + "\n")
        
        if not self.changes:
            print("No files to organize!")
            return
        
        # Group by destination
        by_category: Dict[str, List[str]] = {}
        for change in self.changes:
            dest_folder = Path(change['destination']).parent.name
            if dest_folder not in by_category:
                by_category[dest_folder] = []
            by_category[dest_folder].append(change['filename'])
        
        # Display
        for category, files in by_category.items():
            print(f"📁 {category}/")
            for i, filename in enumerate(files[:max_items]):
                prefix = "└──" if i == len(files) - 1 else "├──"
                print(f"   {prefix} {filename}")
            if len(files) > max_items:
                print(f"   ... and {len(files) - max_items} more files")
            print()
        
        print("-" * 60)
        print(f"Total files: {len(self.changes)}")
        print(f"Categories: {len(by_category)}")
        print("-" * 60)
    
    def confirm_execution(self) -> bool:
        """Ask user for confirmation."""
        response = input("\nProceed with organization? (y/n): ")
        return response.lower().strip() == 'y'
```

#### Feature 6: Undo Operation

```python
import json
from datetime import datetime
from typing import List, Dict, Optional

class UndoManager:
    """Manage undo operations for file organization."""
    
    HISTORY_FILE = 'organizer_history.json'
    
    def __init__(self, history_path: Optional[str] = None):
        self.history_path = Path(history_path or self.HISTORY_FILE)
    
    def save_operation(self, operations: List[Dict], mode: str) -> None:
        """Save operation to history for potential undo."""
        history = {
            'timestamp': datetime.now().isoformat(),
            'mode': mode,
            'operations': operations,
            'operation_count': len(operations)
        }
        
        with open(self.history_path, 'w') as f:
            json.dump(history, f, indent=2)
        
        print(f"💾 Operation saved to history ({len(operations)} files)")
    
    def load_history(self) -> Optional[Dict]:
        """Load the last operation history."""
        if not self.history_path.exists():
            return None
        
        with open(self.history_path, 'r') as f:
            return json.load(f)
    
    def can_undo(self) -> bool:
        """Check if undo is possible."""
        if not self.history_path.exists():
            return False
        
        history = self.load_history()
        if history is None:
            return False
        
        # Check if all source files still exist at destination
        for op in history.get('operations', []):
            if not Path(op['destination']).exists():
                return False
        
        return True
    
    def undo(self) -> bool:
        """Undo the last organization operation."""
        history = self.load_history()
        
        if history is None:
            print("❌ No history found to undo!")
            return False
        
        print(f"\n↩️ Undoing operation from {history['timestamp']}")
        print(f"   Mode: {history['mode']}")
        print(f"   Files: {history['operation_count']}\n")
        
        success_count = 0
        failed_count = 0
        
        # Reverse operations (process in reverse order)
        for op in reversed(history['operations']):
            source = Path(op['source'])
            dest = Path(op['destination'])
            
            try:
                if dest.exists():
                    # Ensure source parent exists
                    source.parent.mkdir(parents=True, exist_ok=True)
                    
                    # Move back
                    shutil.move(str(dest), str(source))
                    print(f"   ✅ Restored: {dest.name} → {source.parent.name}/")
                    success_count += 1
                else:
                    print(f"   ⚠️ File not found: {dest.name}")
                    failed_count += 1
            except Exception as e:
                print(f"   ❌ Failed: {dest.name} - {e}")
                failed_count += 1
        
        # Clean up empty folders
        self._cleanup_empty_folders(history)
        
        # Remove history file
        self.history_path.unlink()
        
        print(f"\n✅ Undo complete!")
        print(f"   Restored: {success_count}")
        print(f"   Failed: {failed_count}")
        
        return failed_count == 0
    
    def _cleanup_empty_folders(self, history: Dict) -> None:
        """Remove empty folders created during organization."""
        folders_checked = set()
        
        for op in history['operations']:
            dest_folder = Path(op['destination']).parent
            if str(dest_folder) not in folders_checked:
                folders_checked.add(str(dest_folder))
                try:
                    if dest_folder.exists() and not any(dest_folder.iterdir()):
                        dest_folder.rmdir()
                        print(f"   🗑️ Removed empty folder: {dest_folder.name}")
                except:
                    pass
    
    def show_history(self) -> None:
        """Display the last operation details."""
        history = self.load_history()
        
        if history is None:
            print("No history found.")
            return
        
        print("\n" + "=" * 50)
        print("LAST OPERATION HISTORY")
        print("=" * 50)
        print(f"Timestamp: {history['timestamp']}")
        print(f"Mode: {history['mode']}")
        print(f"Files: {history['operation_count']}")
        print("\nOperations:")
        
        for i, op in enumerate(history['operations'][:10], 1):
            src = Path(op['source'])
            dst = Path(op['destination'])
            print(f"  {i}. {src.name} → {dst.parent.name}/")
        
        if len(history['operations']) > 10:
            print(f"  ... and {len(history['operations']) - 10} more")
        
        print("=" * 50)
```

#### Feature 7: Recursive Organization

```python
from typing import Generator

def recursive_scan(directory: Path, exclude: Optional[List[str]] = None) -> Generator[Path, None, None]:
    """
    Recursively scan directory for files.
    
    Args:
        directory: Root directory to scan
        exclude: List of folder names to exclude
    
    Yields:
        Path objects for each file found
    """
    exclude = exclude or []
    
    for item in directory.iterdir():
        if item.is_file():
            yield item
        elif item.is_dir() and item.name not in exclude:
            yield from recursive_scan(item, exclude)

def organize_recursive(
    source_dir: str,
    mode: str = 'extension',
    exclude_folders: Optional[List[str]] = None,
    flatten: bool = False,
    dry_run: bool = False
) -> List[Dict]:
    """
    Recursively organize files in all subfolders.
    
    Args:
        source_dir: Root directory
        mode: Organization mode ('extension', 'date', 'size')
        exclude_folders: Folders to skip
        flatten: If True, move all files to root folders
        dry_run: Preview mode
    
    Returns:
        List of operations
    """
    source = Path(source_dir)
    exclude_folders = exclude_folders or []
    operations = []
    
    # Scan all files recursively
    all_files = list(recursive_scan(source, exclude_folders))
    
    print(f"Found {len(all_files)} files in subfolders")
    
    for file_path in all_files:
        # Skip if file is already in a category folder
        parent_name = file_path.parent.name
        if parent_name in DEFAULT_CATEGORIES.keys():
            continue
        
        # Get category based on mode
        if mode == 'extension':
            category = get_category(file_path.suffix)
        elif mode == 'date':
            date = datetime.fromtimestamp(file_path.stat().st_mtime)
            category = date.strftime('%Y-%m')
        else:
            category = 'Organized'
        
        # Determine destination
        if flatten:
            dest_folder = source / category
        else:
            # Keep relative structure
            rel_path = file_path.relative_to(source)
            dest_folder = source / category / rel_path.parent
        
        dest_folder.mkdir(parents=True, exist_ok=True)
        dest_path = dest_folder / file_path.name
        
        # Handle conflicts
        if dest_path.exists():
            base = file_path.stem
            suffix = file_path.suffix
            counter = 1
            while dest_path.exists():
                dest_path = dest_folder / f"{base}_{counter}{suffix}"
                counter += 1
        
        operations.append({
            'source': str(file_path),
            'destination': str(dest_path),
            'category': category,
            'filename': file_path.name
        })
        
        if not dry_run:
            shutil.move(str(file_path), str(dest_path))
    
    return operations
```

#### Feature 8: Watch Mode (Auto-Organize)

```python
import time
import logging
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler, FileCreatedEvent

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(message)s',
    handlers=[
        logging.FileHandler('organizer.log'),
        logging.StreamHandler()
    ]
)

class AutoOrganizerHandler(FileSystemEventHandler):
    """Event handler for automatic file organization."""
    
    def __init__(self, organizer, mode: str = 'extension'):
        self.organizer = organizer
        self.mode = mode
        self.processed_files = set()
    
    def on_created(self, event):
        """Handle file creation event."""
        if event.is_directory:
            return
        
        file_path = Path(event.src_path)
        
        # Skip if already processed (prevent duplicates)
        if str(file_path) in self.processed_files:
            return
        
        # Skip temporary files
        if file_path.suffix in ['.tmp', '.part', '.crdownload']:
            return
        
        # Wait for file to be fully written
        time.sleep(0.5)
        
        if not file_path.exists():
            return
        
        self.processed_files.add(str(file_path))
        
        logging.info(f"📁 New file detected: {file_path.name}")
        
        try:
            self._organize_file(file_path)
        except Exception as e:
            logging.error(f"Failed to organize {file_path.name}: {e}")
    
    def _organize_file(self, file_path: Path):
        """Organize a single file."""
        source_dir = file_path.parent
        
        if self.mode == 'extension':
            category = get_category(file_path.suffix)
        elif self.mode == 'date':
            date = datetime.fromtimestamp(file_path.stat().st_mtime)
            category = date.strftime('%Y-%m')
        else:
            category = 'Organized'
        
        dest_folder = source_dir / category
        dest_folder.mkdir(exist_ok=True)
        
        dest_path = dest_folder / file_path.name
        
        # Handle conflicts
        if dest_path.exists():
            base = file_path.stem
            suffix = file_path.suffix
            counter = 1
            while dest_path.exists():
                dest_path = dest_folder / f"{base}_{counter}{suffix}"
                counter += 1
        
        shutil.move(str(file_path), str(dest_path))
        logging.info(f"✅ Moved: {file_path.name} → {category}/")

def watch_directory(
    directory: str,
    mode: str = 'extension',
    recursive: bool = False
) -> None:
    """
    Watch a directory and auto-organize new files.
    
    Args:
        directory: Directory to watch
        mode: Organization mode
        recursive: Watch subdirectories too
    """
    directory = Path(directory)
    
    if not directory.exists():
        print(f"❌ Directory not found: {directory}")
        return
    
    print("\n" + "=" * 50)
    print("👀 WATCH MODE - Auto-Organizing New Files")
    print("=" * 50)
    print(f"Directory: {directory}")
    print(f"Mode: {mode}")
    print(f"Recursive: {recursive}")
    print("\nPress Ctrl+C to stop...\n")
    
    # Create handler and observer
    handler = AutoOrganizerHandler(None, mode)
    observer = Observer()
    observer.schedule(handler, str(directory), recursive=recursive)
    
    # Start watching
    observer.start()
    
    try:
        while True:
            time.sleep(1)
    except KeyboardInterrupt:
        print("\n\n⏹️ Stopping watch mode...")
        observer.stop()
    
    observer.join()
    print("✅ Watch mode stopped.")
    
    # Show stats
    print(f"\n📊 Statistics:")
    print(f"   Files processed: {len(handler.processed_files)}")
    print(f"   Log file: organizer.log")
```

### 4. Configuration File

```json
{
    "version": "1.0",
    "description": "File Organizer Configuration",
    
    "rules": {
        "Images": [".jpg", ".jpeg", ".png", ".gif", ".bmp", ".svg", ".webp", ".ico", ".tiff", ".raw", ".heic"],
        "Videos": [".mp4", ".mkv", ".avi", ".mov", ".wmv", ".flv", ".webm", ".m4v", ".3gp", ".mpeg"],
        "Audio": [".mp3", ".wav", ".flac", ".aac", ".ogg", ".m4a", ".wma", ".opus", ".aiff"],
        "Documents": [".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx", ".odt", ".rtf", ".csv", ".md"],
        "Archives": [".zip", ".rar", ".7z", ".tar", ".gz", ".bz2", ".xz", ".iso"],
        "Code": [".py", ".js", ".ts", ".html", ".css", ".java", ".cpp", ".c", ".go", ".rs", ".sh", ".php", ".rb", ".json", ".xml", ".yaml", ".sql"],
        "Apps": [".apk", ".exe", ".deb", ".rpm", ".app", ".msi", ".jar", ".appimage"],
        "Ebooks": [".epub", ".mobi", ".azw", ".azw3", ".fb2"],
        "Fonts": [".ttf", ".otf", ".woff", ".woff2", ".eot"],
        "Torrents": [".torrent"],
        "Subtitles": [".srt", ".sub", ".ass", ".vtt"],
        "Work": [".work", "*.project", "*.draft"],
        "Personal": [".personal", "*.private"],
        "Temp": [".tmp", ".part", ".crdownload", ".partial"]
    },
    
    "exclude_folders": [
        "System",
        "Important",
        "DoNotTouch",
        "Archive",
        "Backup"
    ],
    
    "exclude_files": [
        ".nomedia",
        ".gitignore",
        "README.md",
        "LICENSE",
        ".DS_Store",
        "Thumbs.db"
    ],
    
    "naming_convention": "original",
    
    "conflict_resolution": "rename",
    
    "size_categories": {
        "Tiny": [0, 102400],
        "Small": [102400, 1048576],
        "Medium": [1048576, 104857600],
        "Large": [104857600, 1073741824],
        "Huge": [1073741824, null]
    },
    
    "date_format": "%Y-%m",
    
    "logging": {
        "enabled": true,
        "log_file": "organizer.log",
        "level": "INFO"
    },
    
    "watch_mode": {
        "debounce_seconds": 0.5,
        "ignore_patterns": ["*.tmp", "*.part", "*.crdownload"]
    }
}
```

### 5. Logging Implementation

```python
import logging
import json
from datetime import datetime
from typing import Dict, List, Any

class OrganizerLogger:
    """Comprehensive logging for file organization operations."""
    
    def __init__(self, log_file: str = 'organizer.log'):
        self.log_file = log_file
        self._setup_logging()
        self.session_start = datetime.now()
        self.operations_log: List[Dict[str, Any]] = []
    
    def _setup_logging(self) -> None:
        """Configure logging handlers."""
        self.logger = logging.getLogger('FileOrganizer')
        self.logger.setLevel(logging.DEBUG)
        
        # File handler
        file_handler = logging.FileHandler(self.log_file)
        file_handler.setLevel(logging.DEBUG)
        file_formatter = logging.Formatter(
            '%(asctime)s | %(levelname)-8s | %(message)s',
            datefmt='%Y-%m-%d %H:%M:%S'
        )
        file_handler.setFormatter(file_formatter)
        
        # Console handler
        console_handler = logging.StreamHandler()
        console_handler.setLevel(logging.INFO)
        console_formatter = logging.Formatter('%(message)s')
        console_handler.setFormatter(console_formatter)
        
        self.logger.addHandler(file_handler)
        self.logger.addHandler(console_handler)
    
    def log_start(self, directory: str, mode: str) -> None:
        """Log organization start."""
        self.logger.info("=" * 50)
        self.logger.info("FILE ORGANIZATION SESSION")
        self.logger.info(f"Directory: {directory}")
        self.logger.info(f"Mode: {mode}")
        self.logger.info(f"Started: {self.session_start}")
        self.logger.info("=" * 50)
    
    def log_operation(self, source: str, destination: str, success: bool) -> None:
        """Log a single file operation."""
        operation = {
            'timestamp': datetime.now().isoformat(),
            'source': source,
            'destination': destination,
            'success': success
        }
        self.operations_log.append(operation)
        
        if success:
            self.logger.info(f"✅ {Path(source).name} → {Path(destination).parent.name}/")
        else:
            self.logger.error(f"❌ Failed: {Path(source).name}")
    
    def log_summary(self) -> None:
        """Log session summary."""
        total = len(self.operations_log)
        success = sum(1 for op in self.operations_log if op['success'])
        failed = total - success
        
        duration = datetime.now() - self.session_start
        
        self.logger.info("\n" + "=" * 50)
        self.logger.info("SESSION SUMMARY")
        self.logger.info("=" * 50)
        self.logger.info(f"Total files: {total}")
        self.logger.info(f"Successful: {success}")
        self.logger.info(f"Failed: {failed}")
        self.logger.info(f"Duration: {duration}")
        self.logger.info("=" * 50)
    
    def export_log(self, filename: str = 'session_log.json') -> str:
        """Export detailed log as JSON."""
        log_data = {
            'session': {
                'start': self.session_start.isoformat(),
                'end': datetime.now().isoformat(),
                'log_file': self.log_file
            },
            'statistics': {
                'total_operations': len(self.operations_log),
                'successful': sum(1 for op in self.operations_log if op['success']),
                'failed': sum(1 for op in self.operations_log if not op['success'])
            },
            'operations': self.operations_log
        }
        
        with open(filename, 'w') as f:
            json.dump(log_data, f, indent=2)
        
        return filename
```

---

## 💻 COMPLETE SOURCE CODE

### Main Script (file_organizer.py)

```python
#!/usr/bin/env python3
"""
╔═══════════════════════════════════════════════════════════════════════════╗
║                        FILE ORGANIZER TOOL                                ║
║                       By T3rmuxk1ng | Version 1.0                         ║
╠═══════════════════════════════════════════════════════════════════════════╣
║  Features:                                                                ║
║  • Sort by extension, date, or size                                       ║
║  • Custom rules via JSON configuration                                    ║
║  • Preview mode for safe testing                                          ║
║  • Undo operation with history                                            ║
║  • Recursive directory organization                                       ║
║  • Watch mode for auto-organization                                       ║
║  • Comprehensive logging                                                  ║
╚═══════════════════════════════════════════════════════════════════════════╝
"""

import os
import sys
import json
import shutil
import argparse
import fnmatch
import time
import logging
from pathlib import Path
from datetime import datetime
from typing import Dict, List, Optional, Any, Generator, Literal
from concurrent.futures import ThreadPoolExecutor

# ============================================================================
# CONFIGURATION
# ============================================================================

# Default extension categories
DEFAULT_CATEGORIES: Dict[str, List[str]] = {
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.svg', '.webp', 
               '.ico', '.tiff', '.tif', '.raw', '.heic', '.heif', '.webp'],
    'Videos': ['.mp4', '.mkv', '.avi', '.mov', '.wmv', '.flv', '.webm', 
               '.m4v', '.3gp', '.mpeg', '.mpg', '.vob', '.ogv'],
    'Audio': ['.mp3', '.wav', '.flac', '.aac', '.ogg', '.m4a', '.wma', 
              '.opus', '.aiff', '.ape', '.amr', '.ac3'],
    'Documents': ['.pdf', '.doc', '.docx', '.txt', '.xls', '.xlsx', 
                  '.ppt', '.pptx', '.odt', '.rtf', '.csv', '.md', 
                  '.odp', '.ods', '.pages', '.numbers', '.tex'],
    'Archives': ['.zip', '.rar', '.7z', '.tar', '.gz', '.bz2', 
                 '.xz', '.iso', '.dmg', '.tgz', '.bz2'],
    'Code': ['.py', '.js', '.ts', '.html', '.css', '.java', '.cpp', 
             '.c', '.h', '.go', '.rs', '.sh', '.bash', '.zsh', '.php', 
             '.rb', '.swift', '.kt', '.json', '.xml', '.yaml', '.yml', 
             '.sql', '.bat', '.ps1', '.vim', '.lua', '.pl', '.scala'],
    'Apps': ['.apk', '.exe', '.deb', '.rpm', '.app', '.msi', '.jar', 
             '.appimage', '.flatpak', '.snap'],
    'Ebooks': ['.epub', '.mobi', '.azw', '.azw3', '.fb2', '.ibook'],
    'Fonts': ['.ttf', '.otf', '.woff', '.woff2', '.eot'],
    'Torrents': ['.torrent', '.magnet'],
    'Subtitles': ['.srt', '.sub', '.ass', '.vtt', '.ssa'],
}

# Size categories (in bytes)
SIZE_CATEGORIES: Dict[str, tuple] = {
    'Tiny': (0, 100 * 1024),                    # 0 - 100 KB
    'Small': (100 * 1024, 1024 * 1024),         # 100 KB - 1 MB
    'Medium': (1024 * 1024, 100 * 1024 * 1024), # 1 MB - 100 MB
    'Large': (100 * 1024 * 1024, 1024 * 1024 * 1024),  # 100 MB - 1 GB
    'Huge': (1024 * 1024 * 1024, float('inf')), # > 1 GB
}

# History file for undo
HISTORY_FILE = 'organizer_history.json'

# ============================================================================
# HELPER FUNCTIONS
# ============================================================================

def format_size(size_bytes: int) -> str:
    """Convert bytes to human-readable format."""
    for unit in ['B', 'KB', 'MB', 'GB', 'TB']:
        if size_bytes < 1024:
            return f"{size_bytes:.2f} {unit}"
        size_bytes /= 1024
    return f"{size_bytes:.2f} PB"

def get_category(extension: str, categories: Optional[Dict] = None) -> str:
    """Determine the category for a file extension."""
    if categories is None:
        categories = DEFAULT_CATEGORIES
    
    ext = extension.lower()
    for category, extensions in categories.items():
        if ext in [e.lower() for e in extensions]:
            return category
    return 'Others'

def resolve_conflict(source: Path, dest_folder: Path) -> Path:
    """Resolve filename conflicts by adding a counter."""
    dest_path = dest_folder / source.name
    if not dest_path.exists():
        return dest_path
    
    base = source.stem
    suffix = source.suffix
    counter = 1
    
    while dest_path.exists():
        dest_path = dest_folder / f"{base}_{counter}{suffix}"
        counter += 1
    
    return dest_path

def recursive_scan(directory: Path, exclude: Optional[List[str]] = None) -> Generator[Path, None, None]:
    """Recursively scan directory for files."""
    exclude = exclude or []
    
    for item in directory.iterdir():
        if item.is_file():
            yield item
        elif item.is_dir() and item.name not in exclude and not item.name.startswith('.'):
            yield from recursive_scan(item, exclude)

# ============================================================================
# ORGANIZATION FUNCTIONS
# ============================================================================

def organize_by_extension(
    source_dir: Path,
    categories: Optional[Dict] = None,
    dry_run: bool = False,
    recursive: bool = False,
    exclude_folders: Optional[List[str]] = None
) -> List[Dict]:
    """Organize files by their extension."""
    if categories is None:
        categories = DEFAULT_CATEGORIES
    
    operations = []
    exclude_folders = exclude_folders or []
    
    # Get files to process
    if recursive:
        files = list(recursive_scan(source_dir, exclude_folders))
    else:
        files = [f for f in source_dir.iterdir() if f.is_file()]
    
    for file_path in files:
        # Skip if already in a category folder
        if file_path.parent.name in categories:
            continue
        
        category = get_category(file_path.suffix, categories)
        
        # Create destination folder
        if recursive:
            # Keep relative path structure
            rel_path = file_path.relative_to(source_dir)
            dest_folder = source_dir / category
        else:
            dest_folder = source_dir / category
        
        if not dry_run:
            dest_folder.mkdir(parents=True, exist_ok=True)
        
        # Resolve conflicts
        dest_path = resolve_conflict(file_path, dest_folder)
        
        operations.append({
            'source': str(file_path),
            'destination': str(dest_path),
            'category': category,
            'filename': file_path.name
        })
        
        if not dry_run:
            shutil.move(str(file_path), str(dest_path))
    
    return operations

def organize_by_date(
    source_dir: Path,
    date_type: Literal['modified', 'created'] = 'modified',
    pattern: Literal['year-month', 'year', 'year-month-name'] = 'year-month',
    dry_run: bool = False,
    recursive: bool = False
) -> List[Dict]:
    """Organize files by their date."""
    operations = []
    
    # Map date types to stat attributes
    date_attrs = {
        'modified': 'st_mtime',
        'created': 'st_ctime'
    }
    date_attr = date_attrs.get(date_type, 'st_mtime')
    
    # Date format patterns
    date_formats = {
        'year-month': '%Y-%m',
        'year': '%Y',
        'year-month-name': '%Y-%B'
    }
    date_format = date_formats.get(pattern, '%Y-%m')
    
    # Get files
    if recursive:
        files = list(recursive_scan(source_dir))
    else:
        files = [f for f in source_dir.iterdir() if f.is_file()]
    
    for file_path in files:
        # Get file timestamp
        timestamp = getattr(file_path.stat(), date_attr)
        date = datetime.fromtimestamp(timestamp)
        folder_name = date.strftime(date_format)
        
        # Create destination
        dest_folder = source_dir / folder_name
        
        if not dry_run:
            dest_folder.mkdir(parents=True, exist_ok=True)
        
        dest_path = resolve_conflict(file_path, dest_folder)
        
        operations.append({
            'source': str(file_path),
            'destination': str(dest_path),
            'folder': folder_name,
            'date': date.isoformat(),
            'filename': file_path.name
        })
        
        if not dry_run:
            shutil.move(str(file_path), str(dest_path))
    
    return operations

def organize_by_size(
    source_dir: Path,
    size_categories: Optional[Dict[str, tuple]] = None,
    dry_run: bool = False,
    recursive: bool = False
) -> List[Dict]:
    """Organize files by their size."""
    if size_categories is None:
        size_categories = SIZE_CATEGORIES
    
    operations = []
    
    def get_size_category(size: int) -> str:
        for category, (min_size, max_size) in size_categories.items():
            if min_size <= size < max_size:
                return category
        return 'Unknown'
    
    # Get files
    if recursive:
        files = list(recursive_scan(source_dir))
    else:
        files = [f for f in source_dir.iterdir() if f.is_file()]
    
    for file_path in files:
        size = file_path.stat().st_size
        category = get_size_category(size)
        
        # Create destination
        dest_folder = source_dir / category
        
        if not dry_run:
            dest_folder.mkdir(parents=True, exist_ok=True)
        
        dest_path = resolve_conflict(file_path, dest_folder)
        
        operations.append({
            'source': str(file_path),
            'destination': str(dest_path),
            'category': category,
            'size_bytes': size,
            'size_human': format_size(size),
            'filename': file_path.name
        })
        
        if not dry_run:
            shutil.move(str(file_path), str(dest_path))
    
    return operations

def organize_with_config(
    source_dir: Path,
    config_path: Path,
    dry_run: bool = False,
    recursive: bool = False
) -> List[Dict]:
    """Organize files using custom configuration."""
    # Load configuration
    with open(config_path, 'r') as f:
        config = json.load(f)
    
    categories = config.get('rules', DEFAULT_CATEGORIES)
    exclude_folders = config.get('exclude_folders', [])
    exclude_files = config.get('exclude_files', [])
    
    operations = []
    
    # Get files
    if recursive:
        files = list(recursive_scan(source_dir, exclude_folders))
    else:
        files = [f for f in source_dir.iterdir() if f.is_file()]
    
    for file_path in files:
        # Skip excluded files
        if file_path.name in exclude_files:
            continue
        
        # Get category
        category = None
        filename_lower = file_path.name.lower()
        
        for cat, patterns in categories.items():
            for pattern in patterns:
                if pattern.startswith('.'):
                    if filename_lower.endswith(pattern.lower()):
                        category = cat
                        break
                elif '*' in pattern:
                    if fnmatch.fnmatch(filename_lower, pattern.lower()):
                        category = cat
                        break
            if category:
                break
        
        if category is None:
            category = 'Others'
        
        # Create destination
        dest_folder = source_dir / category
        
        if not dry_run:
            dest_folder.mkdir(parents=True, exist_ok=True)
        
        dest_path = resolve_conflict(file_path, dest_folder)
        
        operations.append({
            'source': str(file_path),
            'destination': str(dest_path),
            'category': category,
            'filename': file_path.name
        })
        
        if not dry_run:
            shutil.move(str(file_path), str(dest_path))
    
    return operations

# ============================================================================
# PREVIEW MODE
# ============================================================================

def preview_operations(operations: List[Dict], mode: str) -> None:
    """Display preview of operations."""
    print("\n" + "=" * 60)
    print("📋 PREVIEW MODE - No files will be moved")
    print("=" * 60 + "\n")
    
    if not operations:
        print("No files to organize!")
        return
    
    # Group by destination
    by_dest: Dict[str, List[str]] = {}
    for op in operations:
        dest_folder = Path(op['destination']).parent.name
        if dest_folder not in by_dest:
            by_dest[dest_folder] = []
        by_dest[dest_folder].append(op['filename'])
    
    # Display
    for dest, files in by_dest.items():
        print(f"📁 {dest}/")
        for i, filename in enumerate(files[:20]):
            prefix = "└──" if i == len(files) - 1 else "├──"
            print(f"   {prefix} {filename}")
        if len(files) > 20:
            print(f"   ... and {len(files) - 20} more files")
        print()
    
    print("-" * 60)
    print(f"Total files: {len(operations)}")
    print(f"Categories: {len(by_dest)}")
    print("-" * 60)

# ============================================================================
# UNDO FUNCTIONALITY
# ============================================================================

def save_history(operations: List[Dict], mode: str) -> None:
    """Save operations to history file."""
    history = {
        'timestamp': datetime.now().isoformat(),
        'mode': mode,
        'operations': operations,
        'operation_count': len(operations)
    }
    
    with open(HISTORY_FILE, 'w') as f:
        json.dump(history, f, indent=2)

def undo_last_operation() -> bool:
    """Undo the last organization operation."""
    if not os.path.exists(HISTORY_FILE):
        print("❌ No history found to undo!")
        return False
    
    with open(HISTORY_FILE, 'r') as f:
        history = json.load(f)
    
    print(f"\n↩️ Undoing operation from {history['timestamp']}")
    print(f"   Mode: {history['mode']}")
    print(f"   Files: {history['operation_count']}\n")
    
    success_count = 0
    failed_count = 0
    
    # Reverse operations
    for op in reversed(history['operations']):
        source = Path(op['source'])
        dest = Path(op['destination'])
        
        try:
            if dest.exists():
                source.parent.mkdir(parents=True, exist_ok=True)
                shutil.move(str(dest), str(source))
                print(f"   ✅ Restored: {dest.name}")
                success_count += 1
            else:
                print(f"   ⚠️ File not found: {dest.name}")
                failed_count += 1
        except Exception as e:
            print(f"   ❌ Failed: {dest.name} - {e}")
            failed_count += 1
    
    # Clean up empty folders
    folders_checked = set()
    for op in history['operations']:
        dest_folder = Path(op['destination']).parent
        if str(dest_folder) not in folders_checked:
            folders_checked.add(str(dest_folder))
            try:
                if dest_folder.exists() and not any(dest_folder.iterdir()):
                    dest_folder.rmdir()
                    print(f"   🗑️ Removed empty folder: {dest_folder.name}")
            except:
                pass
    
    # Remove history file
    os.remove(HISTORY_FILE)
    
    print(f"\n✅ Undo complete!")
    print(f"   Restored: {success_count}")
    print(f"   Failed: {failed_count}")
    
    return failed_count == 0

# ============================================================================
# WATCH MODE
# ============================================================================

def watch_directory(directory: Path, mode: str, config_path: Optional[Path] = None) -> None:
    """Watch directory for new files and auto-organize."""
    try:
        from watchdog.observers import Observer
        from watchdog.events import FileSystemEventHandler
    except ImportError:
        print("❌ Watch mode requires 'watchdog' package!")
        print("   Install with: pip install watchdog")
        return
    
    class AutoOrganizerHandler(FileSystemEventHandler):
        def __init__(self, mode, config):
            self.mode = mode
            self.config = config
            self.processed = set()
        
        def on_created(self, event):
            if event.is_directory:
                return
            
            file_path = Path(event.src_path)
            
            # Skip if already processed
            if str(file_path) in self.processed:
                return
            
            # Skip temp files
            if file_path.suffix in ['.tmp', '.part', '.crdownload']:
                return
            
            # Wait for file to be fully written
            time.sleep(0.5)
            
            if not file_path.exists():
                return
            
            self.processed.add(str(file_path))
            print(f"\n📁 New file: {file_path.name}")
            
            # Organize the file
            self._organize_file(file_path)
        
        def _organize_file(self, file_path):
            source_dir = file_path.parent
            
            if self.mode == 'extension':
                category = get_category(file_path.suffix)
            elif self.mode == 'date':
                date = datetime.fromtimestamp(file_path.stat().st_mtime)
                category = date.strftime('%Y-%m')
            elif self.mode == 'size':
                size = file_path.stat().st_size
                for cat, (min_s, max_s) in SIZE_CATEGORIES.items():
                    if min_s <= size < max_s:
                        category = cat
                        break
            else:
                category = 'Organized'
            
            dest_folder = source_dir / category
            dest_folder.mkdir(exist_ok=True)
            
            dest_path = resolve_conflict(file_path, dest_folder)
            
            try:
                shutil.move(str(file_path), str(dest_path))
                print(f"✅ Moved to: {category}/")
            except Exception as e:
                print(f"❌ Failed: {e}")
    
    # Load config if provided
    config = None
    if config_path and config_path.exists():
        with open(config_path, 'r') as f:
            config = json.load(f)
    
    print("\n" + "=" * 50)
    print("👀 WATCH MODE - Auto-Organizing New Files")
    print("=" * 50)
    print(f"Directory: {directory}")
    print(f"Mode: {mode}")
    print("\nPress Ctrl+C to stop...\n")
    
    handler = AutoOrganizerHandler(mode, config)
    observer = Observer()
    observer.schedule(handler, str(directory), recursive=False)
    observer.start()
    
    try:
        while True:
            time.sleep(1)
    except KeyboardInterrupt:
        print("\n\n⏹️ Stopping watch mode...")
        observer.stop()
    
    observer.join()
    print("✅ Watch mode stopped.")

# ============================================================================
# MAIN FUNCTION
# ============================================================================

def main():
    parser = argparse.ArgumentParser(
        description='File Organizer Tool - Automatically organize files by extension, date, or size',
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog="""
Examples:
  %(prog)s ~/storage/downloads                    # Organize by extension (default)
  %(prog)s ~/storage/downloads --mode date        # Organize by date
  %(prog)s ~/storage/downloads --mode size        # Organize by size
  %(prog)s ~/storage/downloads --preview          # Preview changes
  %(prog)s ~/storage/downloads --recursive        # Include subfolders
  %(prog)s ~/storage/downloads --watch            # Auto-organize new files
  %(prog)s --undo                                 # Undo last operation
  %(prog)s --config rules.json ~/storage/downloads # Use custom rules
        """
    )
    
    parser.add_argument('directory', nargs='?', help='Directory to organize')
    parser.add_argument('--mode', '-m', choices=['extension', 'date', 'size'],
                       default='extension', help='Organization mode (default: extension)')
    parser.add_argument('--preview', '-p', action='store_true',
                       help='Preview changes without moving files')
    parser.add_argument('--recursive', '-r', action='store_true',
                       help='Process subdirectories')
    parser.add_argument('--watch', '-w', action='store_true',
                       help='Watch for new files and auto-organize')
    parser.add_argument('--undo', '-u', action='store_true',
                       help='Undo last organization operation')
    parser.add_argument('--config', '-c', type=str,
                       help='Path to custom configuration JSON file')
    parser.add_argument('--date-type', choices=['modified', 'created'],
                       default='modified', help='Date type for date mode')
    parser.add_argument('--date-pattern', choices=['year-month', 'year', 'year-month-name'],
                       default='year-month', help='Date folder pattern')
    parser.add_argument('--create-config', action='store_true',
                       help='Create sample configuration file')
    
    args = parser.parse_args()
    
    # Create sample config
    if args.create_config:
        sample_config = {
            'rules': DEFAULT_CATEGORIES,
            'exclude_folders': ['System', 'Important'],
            'exclude_files': ['.nomedia', '.gitignore'],
            'naming_convention': 'original',
            'conflict_resolution': 'rename'
        }
        with open('organizer_config.json', 'w') as f:
            json.dump(sample_config, f, indent=2)
        print("✅ Created sample configuration: organizer_config.json")
        return
    
    # Undo operation
    if args.undo:
        undo_last_operation()
        return
    
    # Check directory
    if not args.directory:
        parser.print_help()
        return
    
    source_dir = Path(args.directory).expanduser().resolve()
    
    if not source_dir.exists():
        print(f"❌ Directory not found: {source_dir}")
        sys.exit(1)
    
    if not source_dir.is_dir():
        print(f"❌ Not a directory: {source_dir}")
        sys.exit(1)
    
    # Watch mode
    if args.watch:
        config_path = Path(args.config) if args.config else None
        watch_directory(source_dir, args.mode, config_path)
        return
    
    # Organization
    print(f"\n📂 Organizing: {source_dir}")
    print(f"   Mode: {args.mode}")
    if args.recursive:
        print("   Recursive: Yes")
    if args.preview:
        print("   Preview: Yes (no files will be moved)")
    print()
    
    config_path = Path(args.config) if args.config else None
    
    # Run organization based on mode
    if config_path and config_path.exists():
        operations = organize_with_config(source_dir, config_path, args.preview, args.recursive)
    elif args.mode == 'extension':
        operations = organize_by_extension(source_dir, dry_run=args.preview, recursive=args.recursive)
    elif args.mode == 'date':
        operations = organize_by_date(source_dir, args.date_type, args.date_pattern, 
                                      args.preview, args.recursive)
    elif args.mode == 'size':
        operations = organize_by_size(source_dir, dry_run=args.preview, recursive=args.recursive)
    else:
        operations = []
    
    # Display results
    if args.preview:
        preview_operations(operations, args.mode)
    else:
        # Print results
        for op in operations:
            print(f"✅ {op['filename']} → {Path(op['destination']).parent.name}/")
        
        print(f"\n✅ Organized {len(operations)} files!")
        
        # Save history for undo
        if operations:
            save_history(operations, args.mode)
            print(f"💾 History saved (use --undo to reverse)")

if __name__ == '__main__':
    main()
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Extension Organization

```bash
# Task: Organize your Downloads folder by extension

# Step 1: Create test folder with sample files
mkdir -p ~/test_organize
cd ~/test_organize
touch photo.jpg image.png video.mp4 song.mp3 document.pdf script.py archive.zip

# Step 2: Preview organization
python file_organizer.py ~/test_organize --preview

# Step 3: Run organization
python file_organizer.py ~/test_organize --mode extension

# Step 4: Verify results
ls -R ~/test_organize

# Expected output:
# Images: photo.jpg, image.png
# Videos: video.mp4
# Audio: song.mp3
# Documents: document.pdf
# Code: script.py
# Archives: archive.zip
```

### Exercise 2: Date-Based Organization

```bash
# Task: Organize files by modification date

# Step 1: Create test files with different dates
mkdir -p ~/date_test
touch -d "2024-01-15" ~/date_test/jan_file.txt
touch -d "2024-02-20" ~/date_test/feb_file.txt
touch -d "2024-03-10" ~/date_test/mar_file.txt

# Step 2: Preview date organization
python file_organizer.py ~/date_test --mode date --preview

# Step 3: Organize by date
python file_organizer.py ~/date_test --mode date

# Step 4: Check folder structure
ls -R ~/date_test

# Expected: 2024-01/, 2024-02/, 2024-03/ folders
```

### Exercise 3: Custom Configuration

```bash
# Task: Create and use custom organization rules

# Step 1: Generate sample config
python file_organizer.py --create-config

# Step 2: Edit configuration
nano organizer_config.json

# Add custom rule for "Work" files:
# "Work": [".work", "*.project", "*.draft"]

# Step 3: Create test files
mkdir -p ~/custom_test
touch ~/custom_test/file.work ~/custom_test/project.txt ~/custom_test/draft.doc

# Step 4: Use custom config
python file_organizer.py ~/custom_test --config organizer_config.json

# Expected: Work folder with matching files
```

### Exercise 4: Recursive Organization

```bash
# Task: Organize files in nested directories

# Step 1: Create nested structure
mkdir -p ~/recursive_test/level1/level2
touch ~/recursive_test/file1.jpg
touch ~/recursive_test/level1/file2.pdf
touch ~/recursive_test/level1/level2/file3.mp3

# Step 2: Preview recursive organization
python file_organizer.py ~/recursive_test --recursive --preview

# Step 3: Run recursive organization
python file_organizer.py ~/recursive_test --recursive

# Step 4: Verify all files are organized
find ~/recursive_test -type f
```

### Exercise 5: Undo Operation

```bash
# Task: Practice undoing organization

# Step 1: Create and organize files
mkdir -p ~/undo_test
touch ~/undo_test/{a,b,c}.jpg
python file_organizer.py ~/undo_test

# Step 2: Check organized state
ls ~/undo_test/Images/

# Step 3: Undo the operation
python file_organizer.py --undo

# Step 4: Verify files are back
ls ~/undo_test/

# Expected: Files back in root folder
```

### Exercise 6: Watch Mode Testing

```bash
# Task: Test auto-organization with watch mode

# Step 1: Start watch mode in one terminal
python file_organizer.py ~/watch_test --watch &

# Step 2: Create new files
touch ~/watch_test/newphoto.jpg
touch ~/watch_test/newdoc.pdf

# Step 3: Wait and check organization
sleep 2
ls ~/watch_test/Images/
ls ~/watch_test/Documents/

# Expected: Files automatically moved to categories
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Permission Denied

```bash
# Cause: No write permission for directory

# Solution 1: Check permissions
ls -la /path/to/directory

# Solution 2: Grant permissions (if you own it)
chmod u+w /path/to/directory

# Solution 3: Use a directory you have access to
python file_organizer.py ~/storage/downloads  # Instead of system folders
```

### Problem 2: Files Not Being Organized

```bash
# Cause: Files may already be in category folders, or empty directory

# Solution 1: Check directory contents
ls -la /path/to/directory

# Solution 2: Use recursive flag for nested files
python file_organizer.py /path/to/directory --recursive

# Solution 3: Preview mode to see what would happen
python file_organizer.py /path/to/directory --preview
```

### Problem 3: Undo Not Working

```bash
# Cause: History file missing or files moved again after organization

# Solution 1: Check history file exists
ls -la organizer_history.json

# Solution 2: Verify files are in destination folders
# Undo requires files to still be in their organized locations

# Solution 3: Manual recovery
# Use find to locate files:
find /path/to/directory -name "filename" 2>/dev/null
```

### Problem 4: Watch Mode Not Working

```bash
# Cause: watchdog package not installed

# Solution 1: Install watchdog
pip install watchdog

# Solution 2: Verify installation
python -c "import watchdog; print('watchdog installed')"

# Solution 3: Check for errors
python file_organizer.py /path/to/directory --watch 2>&1 | tee watch.log
```

### Problem 5: Custom Config Errors

```bash
# Cause: Invalid JSON syntax in configuration file

# Solution 1: Validate JSON
python -c "import json; json.load(open('organizer_config.json'))"

# Solution 2: Check for common errors:
# - Missing commas
# - Unclosed brackets
# - Invalid escape characters

# Solution 3: Generate fresh config
python file_organizer.py --create-config
```

### Problem 6: File Name Conflicts

```bash
# Cause: Files with same names in different locations

# Solution: Tool automatically handles by adding suffixes
# Example: photo.jpg → photo_1.jpg if photo.jpg exists

# Preview conflicts:
python file_organizer.py /path/to/directory --preview

# Result shows: photo_1.jpg in destination
```

### Problem 7: Large Directory Performance

```bash
# Cause: Too many files causing slow processing

# Solution 1: Use preview first to estimate
python file_organizer.py /large/directory --preview

# Solution 2: Process in batches
# Move some files to temp, organize, then repeat

# Solution 3: Use find to count files first
find /large/directory -type f | wc -l
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Before/After Comparison**
```
┌────────────────────────────────────┐
│  BEFORE          AFTER             │
│  ────────        ──────            │
│  📁 messy/       📁 Organized/     │
│   ├ photo.jpg    ├📁 Images/       │
│   ├ doc.pdf      ├📁 Documents/    │
│   ├ song.mp3     ├📁 Audio/        │
│   └ video.mp4    └📁 Videos/       │
│                                    │
│  FILE ORGANIZER TOOL               │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option B: Feature Highlights**
```
┌────────────────────────────────────┐
│  🗂️ FILE ORGANIZER                 │
│                                    │
│  ✓ Sort by Extension               │
│  ✓ Sort by Date                    │
│  ✓ Auto-Organize                   │
│  ✓ Undo Support                    │
│                                    │
│  One Command - Clean Folders!      │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Watch Mode Focus**
```
┌────────────────────────────────────┐
│  👀 WATCH MODE                      │
│                                    │
│  New File → Auto Organized!        │
│                                    │
│  photo.jpg → 📁Images/             │
│  doc.pdf  → 📁Documents/           │
│                                    │
│  Set & Forget!                     │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🗂️ Termux Full Course - Chapter 56: File Organizer Tool | Auto-Sort Files

🔥 In this video you'll learn:
• Extension-based file organization
• Date-based organization (by year/month)
• Size-based organization
• Custom rules with JSON configuration
• Preview mode for safe testing
• Undo operation for mistakes
• Watch mode for auto-organization
• Recursive directory organization

⏱️ Timestamps:
0:00 - Introduction
1:00 - Project Overview
4:00 - Features Overview
7:00 - Extension Sorting
11:00 - Date & Size Sorting
15:00 - Custom Rules & Preview
18:00 - Undo & Watch Mode
22:00 - Demo & Testing
24:00 - Summary

📝 Commands from this video:
python file_organizer.py ~/storage/downloads --mode extension
python file_organizer.py ~/storage/downloads --mode date
python file_organizer.py ~/storage/downloads --preview
python file_organizer.py ~/storage/downloads --watch
python file_organizer.py --undo

📥 Installation:
pip install watchdog  # For watch mode

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #FileOrganizer #Python #Automation #TermuxCourse #T3rmuxk1ng

---
⚠️ Disclaimer: This tool is for organizing your own files. Always use preview mode first to verify changes before executing.
```

### Tags List

```
termux, file organizer, python automation, file management, 
termux projects, organize files, auto sort files, python script,
termux tutorial, file sorter, download organizer, desktop organizer,
automatic file organization, python file handling, termux course,
t3rmuxk1ng, watch mode, recursive file organization, undo operation,
file management automation, directory organizer, extension sorter
```

### Hashtags

```
#Termux #FileOrganizer #PythonAutomation #TermuxProjects #FileManagement
#AutoSort #TermuxTutorial #PythonScript #T3rmuxk1ng #LearnPython
#TermuxCourse #FileSorter #Automation #Productivity #Coding
```

---

## 📚 ADDITIONAL RESOURCES

### Python Documentation

| Topic | Link |
|-------|------|
| pathlib | https://docs.python.org/3/library/pathlib.html |
| shutil | https://docs.python.org/3/library/shutil.html |
| os.path | https://docs.python.org/3/library/os.path.html |
| datetime | https://docs.python.org/3/library/datetime.html |
| json | https://docs.python.org/3/library/json.html |

### External Libraries

| Library | Purpose | Install |
|---------|---------|---------|
| watchdog | File system monitoring | `pip install watchdog` |
| send2trash | Safe file deletion | `pip install send2trash` |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 57, verify:

- [ ] File organizer script works with basic extension mode
- [ ] Preview mode tested and understood
- [ ] Date-based organization tested
- [ ] Size-based organization tested
- [ ] Custom configuration created and used
- [ ] Undo operation tested successfully
- [ ] Watch mode installed and tested
- [ ] Recursive organization understood
- [ ] Logging feature verified
- [ ] Can troubleshoot common issues

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 57: Project 7 - Backup Automation**

- Automated backup scripts
- Scheduled backups with cron
- Compression techniques
- Incremental backups
- Cloud storage integration
- Backup verification
- Restore procedures
- Backup rotation policies

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
