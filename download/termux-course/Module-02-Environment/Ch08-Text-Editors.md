# Chapter 8: Text Editors in Termux

> **Module:** 2 - Environment  
> **Chapter:** 8 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐ Beginner  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Nano & Vim editors complete guide |
| Commands Reference | All shortcuts and commands |
| Practice Exercises | Hands-on editing tasks |
| Troubleshooting | Common editor issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 8
Title: Text Editors in Termux | Nano & Vim Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main aapka host hoon aur aaj hum seekhenge Termux mein sabse important 
topic - Text Editors.

Jab aap Termux mein kaam karte ho - scripts likhte ho, configuration 
files edit karte ho, code likhte ho - to aapko text editor ki zarurat 
padti hai. Terminal mein GUI editors nahi hote, text-based editors 
hote hain.

Aaj hum do main editors cover karenge - Nano aur Vim. Nano simple hai, 
beginners ke liye perfect. Vim powerful hai, professionals ka favorite.

Dono ko detail mein samjhein ge, shortcuts seekhein ge, aur end tak 
aap expert ban jaoge.

To chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein 
notification bell ke saath.

---

[SECTION 1: TEXT EDITORS KYA HAIN - 0:45 to 2:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain ki text editors kya hote hain aur Termux 
mein kaun kaun se editors available hain.

Text editor ek program hai jo text files create aur edit karne ke 
liye use hota hai. Notepad jaisa - lekin terminal mein.

Termux mein multiple editors available hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX TEXT EDITORS                                   │
├────────────────┬──────────────────┬─────────────────────────────────────┤
│ Editor         │ Difficulty       │ Best For                            │
├────────────────┼──────────────────┼─────────────────────────────────────┤
│ Nano           │ ⭐ Easy          │ Beginners, Quick edits              │
│ Vim            │ ⭐⭐⭐ Medium      │ Power users, Coding                 │
│ Micro          │ ⭐⭐ Easy-Medium  │ Modern feel, Mouse support          │
│ Emacs          │ ⭐⭐⭐⭐ Hard       │ Advanced users, Extensible          │
│ Neovim         │ ⭐⭐⭐ Medium      │ Modern Vim, Lua plugins             │
└────────────────┴──────────────────┴─────────────────────────────────────┘

Aaj hum Nano aur Vim detail mein cover karenge - ye do sabse popular 
hain aur har Linux user ko aana chahiye.

Nano beginner-friendly hai. Bottom mein shortcuts dikhate rehte hain.
Vim thoda complex hai lekin bahut powerful hai - modal editor hai.

---

[SECTION 2: NANO EDITOR INTRODUCTION - 2:30 to 4:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye pehle Nano editor se shuru karte hain.

Nano ek simple, user-friendly text editor hai. Ye default Termux 
mein installed aata hai, lekin agar nahi hai to install karna bahut 
easy hai.

NANO KA MATLAB:
- Simple interface
- Bottom mein shortcuts visible
- No modes - seedha type karo
- Perfect for beginners
- Good for quick edits

Install karna:

    pkg install nano

Check karna:

    nano --version

Nano open karna simple hai:

    nano              # Opens empty file
    nano filename     # Opens specific file
    nano -m file      # With mouse support

Jab Nano open hota hai, aapko screen ke neeche shortcuts dikhenge:
^G Get Help    ^O Write Out   ^W Where Is    ^K Cut
^X Exit        ^R Read File   ^\ Replace     ^U Paste

Yahan ^ ka matlab hai Ctrl key. To ^O ka matlab Ctrl+O.

---

[SECTION 3: NANO BASIC OPERATIONS - 4:30 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye Nano ke basic operations seekhte hain:

[FILE CREATE KARNA]

    nano myfile.txt

Ye command myfile.txt create karegi agar exist nahi karti, ya open 
karegi agar already hai.

[TYPING KARNA]

File open hone ke baad seedha type karna shuru karo. Koi mode nahi 
hai - directly type karo.

[SAVE KARNA - Ctrl+O]

Save karne ke liye:
1. Ctrl+O press karein (Write Out)
2. Filename confirm karein (Enter press karein)
3. "Wrote X lines" message aayega

Remember: O for Output, O for Write Out

[EXIT KARNA - Ctrl+X]

Exit karne ke liye Ctrl+X press karein.

Agar changes hain aur save nahi kiye:
- "Save modified buffer?" poochega
- Y for Yes, N for No, Ctrl+C for Cancel

[SEARCH KARNA - Ctrl+W]

Search karne ke liye:
1. Ctrl+W press karein (Where Is)
2. Search term type karein
3. Enter press karein
4. Next match ke liye Alt+W press karein

[REPLACE KARNA - Ctrl+\]

Find and Replace:
1. Ctrl+\ press karein
2. Search term type karein, Enter
3. Replace term type karein, Enter
4. Y for this occurrence, A for all

[CUT, COPY, PASTE]

Cut line: Ctrl+K (cut karega current line)
Paste: Ctrl+U (paste karega cut content)
Copy: No direct copy - cut then paste back

Multiple lines cut:
1. Ctrl+A (mark start)
2. Arrow keys se select karein
3. Ctrl+K (cut selection)
4. Ctrl+U (paste)

[GO TO LINE - Ctrl+_]

Specific line pe jaane ke liye:
1. Ctrl+_ (Ctrl+Shift+hyphen)
2. Line number type karein
3. Enter press karein

---

[SECTION 4: NANO SHORTCUTS SUMMARY - 8:00 to 9:30]
─────────────────────────────────────────────────────────────────────────────

Nano ke important shortcuts yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    NANO KEYBOARD SHORTCUTS                               │
├─────────────────────────────────────────────────────────────────────────┤
│ FILE OPERATIONS                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+O        Save file (Write Out)                                     │
│ Ctrl+X        Exit Nano                                                  │
│ Ctrl+R        Read/Insert another file                                  │
│ Ctrl+S        Save without prompting                                    │
├─────────────────────────────────────────────────────────────────────────┤
│ EDITING                                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+K        Cut current line/selection                                │
│ Ctrl+U        Paste                                                     │
│ Ctrl+J        Justify paragraph                                         │
│ Ctrl+T        Spell check (if installed)                                │
│ Alt+U         Undo                                                      │
│ Alt+E         Redo                                                      │
├─────────────────────────────────────────────────────────────────────────┤
│ SEARCH & REPLACE                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+W        Search                                                    │
│ Alt+W         Next search match                                         │
│ Ctrl+\        Find and Replace                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ NAVIGATION                                                              │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+A        Move to beginning of line                                 │
│ Ctrl+E        Move to end of line                                       │
│ Ctrl+_        Go to specific line number                                │
│ Ctrl+Y        Page Up                                                   │
│ Ctrl+V        Page Down                                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ SELECTION                                                               │
├─────────────────────────────────────────────────────────────────────────┤
│ Alt+A         Start/End selection                                       │
│ Alt+6         Copy selection                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ HELP                                                                    │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+G        Display help                                              │
│ F1            Display help                                              │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 5: VIM EDITOR INTRODUCTION - 9:30 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye Vim editor ki baat karte hain.

VIM = Vi IMproved. Ye Unix ke classic vi editor ka improved version hai.

Vim ek MODAL editor hai. Iska matlab hai ki keyboard ke keys ka 
behavior change hota hai depending on kis mode mein ho.

Vim mein 4 main modes hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM MODES                                             │
├────────────────┬────────────────────────────────────────────────────────┤
│ Mode           │ Description                                            │
├────────────────┼────────────────────────────────────────────────────────┤
│ NORMAL         │ Default mode - navigation, commands                    │
│ INSERT         │ Text typing mode - like normal editor                  │
│ COMMAND        │ Bottom commands - save, exit, search, replace          │
│ VISUAL         │ Text selection mode                                    │
└────────────────┴────────────────────────────────────────────────────────┘

Install karna:

    pkg install vim

Vim open karna:

    vim              # Opens empty
    vim filename     # Opens/creates file
    vim +10 file     # Opens at line 10
    vim +/pattern file # Opens at first pattern match

Jab Vim open hota hai, aap NORMAL mode mein hote ho.
Is mode mein aap type NAHI kar sakte - cursor move karte ho, 
commands run karte ho.

---

[SECTION 6: VIM MODES & BASIC COMMANDS - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye Vim ke modes detail mein samjhte hain:

[NORMAL MODE]

Default mode. Esc press karke kabhi bhi Normal mode mein aa sakte ho.

Navigation (Normal mode mein):
h - Left (←)
j - Down (↓)
k - Up (↑)
l - Right (→)

Word navigation:
w - Next word start
b - Previous word start
e - Current/next word end

Line navigation:
0 - Beginning of line
$ - End of line
^ - First non-blank character

File navigation:
gg - First line
G - Last line
5G - Go to line 5
:10 - Go to line 10

[INSERT MODE]

Text type karne ke liye Insert mode mein jao:

i - Insert before cursor
I - Insert at beginning of line
a - Insert after cursor
A - Insert at end of line
o - Open new line below
O - Insert at end of line (wait, O - Open new line ABOVE)
s - Delete character and insert
S - Delete line and insert

Insert mode se wapas Normal mode: Press Esc

[COMMAND MODE]

Commands run karne ke liye Normal mode mein : (colon) press karo.

:w - Save file
:q - Quit
:wq - Save and quit
:q! - Quit without saving
:x - Save and quit (same as :wq)
:e filename - Edit/open file
:r filename - Read/insert file content
:set number - Show line numbers
:set nonumber - Hide line numbers

[VISUAL MODE]

Text select karne ke liye:

v - Visual mode (character selection)
V - Visual Line mode (line selection)
Ctrl+V - Visual Block mode (block selection)

Visual mode mein arrow keys se select karo, then:
d - Delete selection
y - Copy (yank) selection
c - Change selection

---

[SECTION 7: VIM EDITING COMMANDS - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Ab Vim ke editing commands seekhte hain:

[DELETE COMMANDS]

x - Delete character under cursor
X - Delete character before cursor
dd - Delete entire line
dw - Delete word
d$ - Delete to end of line
d0 - Delete to beginning of line
dG - Delete to end of file
dgg - Delete to beginning of file
5dd - Delete 5 lines

[COPY & PASTE]

Vim mein copy ko "yank" kehte hain.

yy - Yank (copy) current line
yw - Yank word
y$ - Yank to end of line
y0 - Yank to beginning of line
5yy - Yank 5 lines

p - Paste after cursor
P - Paste before cursor

[UNDO & REDO]

u - Undo last change
Ctrl+R - Redo
. - Repeat last command

[REPLACE COMMANDS]

r - Replace single character
R - Enter Replace mode (overwrite)
c - Change (delete and enter insert mode)
cw - Change word
c$ - Change to end of line
cc - Change entire line

[SEARCH]

/pattern - Search forward
?pattern - Search backward
n - Next match
N - Previous match

[SEARCH & REPLACE]

:s/old/new/ - Replace first occurrence in line
:s/old/new/g - Replace all in line
:%s/old/new/g - Replace all in file
:%s/old/new/gc - Replace with confirmation

Example:
:%s/hello/hi/g - Saari "hello" ko "hi" mein change

---

[SECTION 8: VIM SHORTCUTS SUMMARY - 17:30 to 18:30]
─────────────────────────────────────────────────────────────────────────────

Vim shortcuts ka complete reference:

┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM CHEAT SHEET                                       │
├─────────────────────────────────────────────────────────────────────────┤
│ MODE SWITCHING                                                           │
├─────────────────────────────────────────────────────────────────────────┤
│ i/I/a/A/o/O    Enter Insert mode                                        │
│ v/V/Ctrl+V     Enter Visual mode                                        │
│ :              Enter Command mode                                       │
│ Esc            Return to Normal mode                                    │
├─────────────────────────────────────────────────────────────────────────┤
│ NAVIGATION (Normal Mode)                                                │
├─────────────────────────────────────────────────────────────────────────┤
│ h/j/k/l        Left/Down/Up/Right                                       │
│ w/b/e          Word forward/back/end                                    │
│ 0/$            Line start/end                                           │
│ gg/G           File start/end                                           │
│ Ctrl+u/d       Page up/down (half)                                      │
│ Ctrl+f/b       Page forward/back (full)                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ EDITING (Normal Mode)                                                   │
├─────────────────────────────────────────────────────────────────────────┤
│ dd             Delete line                                              │
│ dw             Delete word                                              │
│ x/X            Delete char under/before cursor                          │
│ yy             Copy line                                                │
│ p/P            Paste after/before cursor                                │
│ u              Undo                                                     │
│ Ctrl+r         Redo                                                     │
│ .              Repeat last command                                      │
├─────────────────────────────────────────────────────────────────────────┤
│ COMMAND MODE                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ :w             Save                                                     │
│ :q             Quit                                                     │
│ :wq or :x      Save and quit                                            │
│ :q!            Force quit without saving                                │
│ :%s/old/new/g  Replace all                                              │
│ :set number    Show line numbers                                        │
│ :syntax on     Enable syntax highlighting                               │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 9: NANO VS VIM COMPARISON - 18:30 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Ab comparison dekhte hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    NANO VS VIM COMPARISON                                │
├─────────────────────┬─────────────────┬─────────────────────────────────┤
│ Feature             │ Nano            │ Vim                             │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ Learning Curve      │ Easy            │ Steep                           │
│ Modes               │ None            │ Multiple modes                  │
│ Shortcuts           │ Always visible  │ Must memorize                   │
│ Mouse Support       │ Limited         │ Limited                         │
│ Syntax Highlighting │ Basic           │ Excellent                       │
│ Customization       │ Limited         │ Extensive (.vimrc)              │
│ Plugins             │ No              │ Yes, thousands                  │
│ Speed               │ Good            │ Excellent (once learned)        │
│ Best For            │ Quick edits     │ Heavy coding                    │
│ Memory Usage        │ Low             │ Low-Medium                      │
└─────────────────────┴─────────────────┴─────────────────────────────────┘

Recommendation:
- Beginner? Start with Nano
- Quick edit? Use Nano
- Heavy coding? Learn Vim
- Professional? Master Vim

---

[SECTION 10: OTHER EDITORS & SUMMARY - 19:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Termux mein aur bhi editors hain:

[Micro Editor]
Modern terminal editor with mouse support:

    pkg install micro
    micro filename

Features:
- Mouse support built-in
- Ctrl+C/V/X shortcuts
- Multiple cursors
- Plugin support

[Emacs]
Powerful, extensible editor:

    pkg install emacs

Features:
- Unlimited customization
- Built-in Lisp interpreter
- Can do anything (email, chat, games)

[SUMMARY]

Aaj humne seekha:

✅ Text editors kya hote hain
✅ Nano editor complete guide
✅ Nano shortcuts
✅ Vim editor modes
✅ Vim commands and shortcuts
✅ Nano vs Vim comparison
✅ Other editors (Micro, Emacs)

Important commands yaad rakhein:

Nano:
- Ctrl+O: Save
- Ctrl+X: Exit
- Ctrl+W: Search
- Ctrl+K/U: Cut/Paste

Vim:
- i: Insert mode
- Esc: Normal mode
- :w: Save
- :q: Quit
- :wq: Save and quit
- dd: Delete line
- yy/p: Copy/Paste

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Next Chapter mein hum seekhenge Termux Styling - colors, fonts, 
aur customization!

Thank you for watching! See you in Chapter 9!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Nano Editor Complete Guide

#### Installation

```bash
# Install Nano
pkg install nano

# Verify installation
nano --version

# Check if installed
which nano
```

#### Opening Files

```bash
# Open/create a file
nano filename.txt

# Open multiple files
nano file1.txt file2.txt

# Open with line numbers
nano -c filename.txt

# Open at specific line
nano +10 filename.txt

# Open in read-only mode
nano -v filename.txt

# Enable mouse support
nano -m filename.txt

# Smooth scrolling
nano -S filename.txt
```

#### Navigation in Nano

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NANO NAVIGATION                                       │
├─────────────────────────────────────────────────────────────────────────┤
│ CHARACTER MOVEMENT                                                       │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+B / ←      Move back one character                                 │
│ Ctrl+F / →      Move forward one character                              │
├─────────────────────────────────────────────────────────────────────────┤
│ WORD MOVEMENT                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+Space      Move forward one word                                   │
│ Alt+Space       Move back one word                                      │
├─────────────────────────────────────────────────────────────────────────┤
│ LINE MOVEMENT                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+A          Move to beginning of line                               │
│ Ctrl+E          Move to end of line                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ PAGE MOVEMENT                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+Y          Page Up                                                 │
│ Ctrl+V          Page Down                                               │
├─────────────────────────────────────────────────────────────────────────┤
│ FILE MOVEMENT                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ Alt+\           Move to beginning of file                               │
│ Alt+/           Move to end of file                                     │
│ Ctrl+_          Go to specific line                                     │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Editing Operations

```bash
# Cut entire line
Ctrl+K

# Cut multiple lines
# Press Ctrl+K multiple times

# Cut selection
# 1. Ctrl+A to set mark
# 2. Move cursor to select
# 3. Ctrl+K to cut

# Paste
Ctrl+U

# Copy selection (instead of cut)
Alt+6

# Justify paragraph
Ctrl+J

# Insert another file
Ctrl+R, then type filename

# Execute command and insert output
Ctrl+T
```

#### Search and Replace

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NANO SEARCH & REPLACE                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ SEARCH                                                                   │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+W          Start search                                            │
│ Alt+W           Find next occurrence                                    │
│ Alt+Q           Find previous occurrence                                │
├─────────────────────────────────────────────────────────────────────────┤
│ SEARCH OPTIONS (at search prompt)                                        │
├─────────────────────────────────────────────────────────────────────────┤
│ Alt+B           Search backward                                         │
│ Alt+C           Case sensitive                                          │
│ Alt+R           Use regex                                               │
├─────────────────────────────────────────────────────────────────────────┤
│ REPLACE                                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+\          Start search & replace                                  │
│ Y               Replace this occurrence                                 │
│ N               Skip this occurrence                                    │
│ A               Replace all remaining                                   │
│ Ctrl+C          Cancel replace                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Nano Configuration (.nanorc)

```bash
# Create/edit .nanorc
nano ~/.nanorc
```

Example `.nanorc` configuration:

```bash
# ~/.nanorc - Nano configuration file

# Enable syntax highlighting
include /data/data/com.termux/files/usr/share/nano/*.nanorc

# Show line numbers
set linenumber

# Auto-indentation
set autoindent

# Tab size
set tabsize 4

# Convert tabs to spaces
set tabstospaces

# Smooth scrolling
set smooth

# Enable mouse support
set mouse

# Show cursor position in status bar
set const

# Word wrap
set softwrap

# Backup files before saving
set backup

# Matching brackets highlighting
set brackets "'")}]>"

# Enable smart home key
set smarthome

# Allow nano to be suspended
set suspend

# Custom keybindings (optional)
# bind ^X exit all

# Color scheme
set titlecolor brightwhite,blue
set statuscolor brightwhite,green
set keycolor brightwhite
set functioncolor green
```

### 2. Vim Editor Complete Guide

#### Installation

```bash
# Install Vim
pkg install vim

# Verify installation
vim --version

# Install enhanced version
pkg install vim-python vim-runtime

# Check if installed
which vim
```

#### Vim Modes Explained

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM MODES DETAILED                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                          ┌──────────────┐                               │
│                          │  NORMAL MODE │ ←──────────────┐              │
│                          │   (Default)  │                 │              │
│                          └──────┬───────┘                 │              │
│                                  │                         │              │
│              ┌───────────────────┼───────────────────┐    │              │
│              │                   │                   │    │              │
│              ▼                   ▼                   ▼    │              │
│     ┌────────────────┐  ┌────────────────┐  ┌────────────┴──────────┐   │
│     │  INSERT MODE   │  │  COMMAND MODE  │  │     VISUAL MODE       │   │
│     │                │  │                │  │                       │   │
│     │ i, I, a, A,    │  │ : (colon)      │  │ v, V, Ctrl+V         │   │
│     │ o, O, s, S     │  │                │  │                       │   │
│     │                │  │ :w, :q, :wq    │  │ Text selection        │   │
│     │ Type text      │  │ :%s/old/new/g  │  │ d, y, c operations   │   │
│     │ normally       │  │ :set options   │  │                       │   │
│     │                │  │                │  │                       │   │
│     │ Press Esc to   │  │ Press Esc to   │  │ Press Esc to         │   │
│     │ return to      │  │ return to      │  │ return to            │   │
│     │ Normal mode    │  │ Normal mode    │  │ Normal mode          │   │
│     └────────────────┘  └────────────────┘  └───────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Normal Mode Commands

**Navigation Commands:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM NAVIGATION (NORMAL MODE)                          │
├─────────────────────────────────────────────────────────────────────────┤
│ CHARACTER MOVEMENT                                                       │
├─────────────────────────────────────────────────────────────────────────┤
│ h               Left one character                                      │
│ j               Down one line                                           │
│ k               Up one line                                             │
│ l               Right one character                                     │
│ ← ↓ ↑ →         Arrow keys (alternative)                                │
├─────────────────────────────────────────────────────────────────────────┤
│ WORD MOVEMENT                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ w               Next word start                                         │
│ W               Next WORD start (WORD = non-blank chars)                │
│ b               Previous word start                                     │
│ B               Previous WORD start                                     │
│ e               End of current/next word                                │
│ E               End of current/next WORD                                │
├─────────────────────────────────────────────────────────────────────────┤
│ LINE MOVEMENT                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ 0               Beginning of line                                       │
│ ^               First non-blank character                               │
│ $               End of line                                             │
│ |               Go to column n (e.g., 10|)                              │
├─────────────────────────────────────────────────────────────────────────┤
│ FILE MOVEMENT                                                            │
├─────────────────────────────────────────────────────────────────────────┤
│ gg              Go to first line                                        │
│ G               Go to last line                                         │
│ nG              Go to line n (e.g., 10G)                                │
│ :n              Go to line n (e.g., :10)                                │
│ Ctrl+g          Show file info and current line                         │
├─────────────────────────────────────────────────────────────────────────┤
│ SCREEN MOVEMENT                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+f          Page down (forward)                                     │
│ Ctrl+b          Page up (backward)                                      │
│ Ctrl+d          Half page down                                          │
│ Ctrl+u          Half page up                                            │
│ H               Top of screen (High)                                    │
│ M               Middle of screen                                        │
│ L               Bottom of screen (Low)                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ MARKERS                                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ ma              Set marker 'a'                                          │
│ 'a              Jump to marker 'a'                                      │
│ '.              Jump to last edit                                       │
└─────────────────────────────────────────────────────────────────────────┘
```

**Editing Commands:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM EDITING (NORMAL MODE)                             │
├─────────────────────────────────────────────────────────────────────────┤
│ DELETE COMMANDS                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ x               Delete character under cursor                            │
│ X               Delete character before cursor                           │
│ dd              Delete entire line                                       │
│ dw              Delete word                                              │
│ d$ or D         Delete to end of line                                   │
│ d0              Delete to beginning of line                              │
│ d^              Delete to first non-blank                                │
│ dG              Delete to end of file                                    │
│ dgg             Delete to beginning of file                              │
│ dt[char]        Delete until character                                   │
│ df[char]        Delete through character                                 │
│ ndd             Delete n lines (e.g., 5dd)                               │
├─────────────────────────────────────────────────────────────────────────┤
│ COPY (YANK) COMMANDS                                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ yy              Yank (copy) current line                                │
│ Y               Yank current line (same as yy)                          │
│ yw              Yank word                                               │
│ y$              Yank to end of line                                     │
│ y0              Yank to beginning of line                               │
│ yG              Yank to end of file                                     │
│ ygg             Yank to beginning of file                               │
│ nyy             Yank n lines (e.g., 5yy)                                │
├─────────────────────────────────────────────────────────────────────────┤
│ PASTE COMMANDS                                                           │
├─────────────────────────────────────────────────────────────────────────┤
│ p               Paste after cursor                                      │
│ P               Paste before cursor                                     │
│ ]p              Paste with auto-indent                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ REPLACE COMMANDS                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│ r               Replace single character                                │
│ R               Enter Replace mode (overwrite)                          │
│ ~               Toggle case of character                                │
├─────────────────────────────────────────────────────────────────────────┤
│ CHANGE COMMANDS                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ cc              Change entire line                                      │
│ cw              Change word                                             │
│ c$ or C         Change to end of line                                   │
│ c0              Change to beginning of line                             │
│ ct[char]        Change until character                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ UNDO/REDO                                                                │
├─────────────────────────────────────────────────────────────────────────┤
│ u               Undo last change                                        │
│ Ctrl+r          Redo                                                   │
│ U               Restore line (undo all changes on line)                 │
│ .               Repeat last command                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ JOIN/SPLIT                                                               │
├─────────────────────────────────────────────────────────────────────────┤
│ J               Join current line with next                              │
│ gJ             Join without space                                       │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Insert Mode

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM INSERT MODE                                       │
├─────────────────────────────────────────────────────────────────────────┤
│ ENTERING INSERT MODE                                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ i               Insert before cursor                                    │
│ I               Insert at beginning of line                             │
│ a               Insert after cursor (append)                            │
│ A               Insert at end of line                                   │
│ o               Open new line below                                     │
│ O               Open new line above                                     │
│ s               Substitute character (delete and insert)                │
│ S               Substitute line (delete line and insert)                │
│ gi              Insert at last insert position                          │
├─────────────────────────────────────────────────────────────────────────┤
│ INSERT MODE SHORTCUTS                                                    │
├─────────────────────────────────────────────────────────────────────────┤
│ Ctrl+h          Delete previous character                               │
│ Ctrl+w          Delete previous word                                    │
│ Ctrl+u          Delete to beginning of line                             │
│ Ctrl+t          Indent line                                             │
│ Ctrl+d          Unindent line                                           │
│ Ctrl+n          Autocomplete (next match)                               │
│ Ctrl+p          Autocomplete (previous match)                           │
│ Ctrl+o          Execute one normal command, then return                 │
│ Esc             Exit insert mode                                        │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Command Mode Commands

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM COMMAND MODE                                      │
├─────────────────────────────────────────────────────────────────────────┤
│ FILE OPERATIONS                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│ :w              Save file                                               │
│ :w filename     Save as filename                                        │
│ :w!              Force save (readonly)                                  │
│ :q              Quit                                                    │
│ :q!             Force quit (discard changes)                            │
│ :wq              Save and quit                                          │
│ :x              Save and quit (only if modified)                        │
│ :ZZ              Save and quit                                          │
│ :ZQ              Quit without saving                                    │
│ :e filename      Edit/open another file                                 │
│ :e!              Reload current file (discard changes)                  │
│ :r filename      Read/insert file content                               │
│ :r !command      Insert command output                                  │
│ :sav filename    Save as and switch to new file                         │
├─────────────────────────────────────────────────────────────────────────┤
│ NAVIGATION                                                               │
├─────────────────────────────────────────────────────────────────────────┤
│ :n              Go to line n                                            │
│ :$              Go to last line                                         │
│ :1              Go to first line                                        │
├─────────────────────────────────────────────────────────────────────────┤
│ SEARCH & REPLACE                                                         │
├─────────────────────────────────────────────────────────────────────────┤
│ :/pattern       Search forward                                          │
│ :?pattern       Search backward                                         │
│ :n              Next match                                              │
│ :N              Previous match                                          │
│ :s/old/new/     Replace first in line                                   │
│ :s/old/new/g    Replace all in line                                     │
│ :%s/old/new/g   Replace all in file                                     │
│ :%s/old/new/gc  Replace with confirmation                               │
│ :%s/old/new/gi  Replace (case insensitive)                              │
│ :noh            Clear search highlighting                               │
├─────────────────────────────────────────────────────────────────────────┤
│ OPTIONS                                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ :set number     Show line numbers                                       │
│ :set nonumber   Hide line numbers                                       │
│ :set relativenumber  Show relative line numbers                         │
│ :set autoindent Enable auto-indentation                                 │
│ :set tabstop=4  Set tab width to 4                                      │
│ :set expandtab  Convert tabs to spaces                                  │
│ :syntax on      Enable syntax highlighting                              │
│ :set wrap        Enable line wrapping                                   │
│ :set nowrap      Disable line wrapping                                  │
│ :set hlsearch    Highlight search results                               │
│ :set incsearch   Incremental search                                     │
│ :set ignorecase  Case insensitive search                                │
│ :set smartcase   Smart case search                                      │
│ :set paste       Paste mode (no auto-indent)                            │
│ :set nopaste     Exit paste mode                                        │
├─────────────────────────────────────────────────────────────────────────┤
│ WINDOWS                                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ :split          Horizontal split                                        │
│ :vsplit         Vertical split                                          │
│ :new            New horizontal window                                   │
│ :vnew           New vertical window                                     │
│ :close          Close current window                                    │
│ :only           Close all other windows                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ BUFFERS                                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ :buffers        List all buffers                                        │
│ :bn             Next buffer                                             │
│ :bp             Previous buffer                                         │
│ :bd             Delete buffer                                           │
│ :b1             Switch to buffer 1                                      │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Visual Mode

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    VIM VISUAL MODE                                       │
├─────────────────────────────────────────────────────────────────────────┤
│ ENTERING VISUAL MODE                                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ v               Visual mode (character-wise)                            │
│ V               Visual Line mode (line-wise)                            │
│ Ctrl+v          Visual Block mode (block-wise)                          │
│ gv              Reselect last selection                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ OPERATIONS ON SELECTION                                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ d               Delete selection                                        │
│ y               Yank (copy) selection                                   │
│ c               Change selection                                        │
│ x               Delete selection                                        │
│ >               Indent selection                                        │
│ <               Unindent selection                                      │
│ ~               Toggle case                                             │
│ u               Convert to lowercase                                    │
│ U               Convert to uppercase                                    │
│ :               Run command on selection                                │
├─────────────────────────────────────────────────────────────────────────┤
│ VISUAL BLOCK SPECIAL                                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ I               Insert at beginning of block                            │
│ A               Insert at end of block                                  │
│ r               Replace all with character                              │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Search and Replace

```bash
# Basic search
/pattern          # Search forward
?pattern          # Search backward

# Search navigation
n                 # Next match
N                 # Previous match

# Search with options
/\<word\>         # Search whole word only
/^pattern         # Search at line start
/pattern$         # Search at line end
/[0-9]            # Search for digits (regex)

# Replace examples
:s/foo/bar/       # Replace first foo with bar in line
:s/foo/bar/g      # Replace all foo with bar in line
:%s/foo/bar/g     # Replace all foo with bar in file
:%s/foo/bar/gc    # Replace with confirmation
:%s/foo/bar/gi    # Case insensitive replace
:%s/\<foo\>/bar/g # Replace whole word only
:%s/^/    /g      # Add 4 spaces to beginning of all lines
:%s/$/;/g         # Add ; to end of all lines
:%s/\n//g         # Remove all newlines (join lines)
:%s/\s\+$//g      # Remove trailing whitespace
```

#### Vim Configuration (.vimrc)

```bash
# Create/edit .vimrc
vim ~/.vimrc
```

Example `.vimrc` configuration:

```vim
" ~/.vimrc - Vim configuration file
" ============================================================

" ----- Basic Settings -----
set nocompatible          " Use Vim settings, not Vi
set encoding=utf-8        " Set encoding
set fileencoding=utf-8    " File encoding

" ----- Appearance -----
syntax on                 " Enable syntax highlighting
set background=dark       " Dark background
set number                " Show line numbers
set relativenumber        " Relative line numbers
set cursorline            " Highlight current line
set showcmd               " Show command in bottom bar
set showmode              " Show current mode
set wildmenu              " Visual autocomplete for command menu
set showmatch             " Highlight matching [{()}]
set ruler                 " Show cursor position
set scrolloff=5           " Keep 5 lines above/below cursor

" ----- Indentation -----
set autoindent            " Auto-indent new lines
set smartindent           " Smart auto-indenting
set tabstop=4             " Number of spaces per tab
set shiftwidth=4          " Number of spaces for auto-indent
set softtabstop=4         " Number of spaces in tab when editing
set expandtab             " Convert tabs to spaces
set backspace=indent,eol,start  " Backspace behavior

" ----- Search -----
set incsearch             " Search as characters are entered
set hlsearch              " Highlight matches
set ignorecase            " Ignore case when searching
set smartcase             " Unless uppercase is used

" ----- Editing -----
set mouse=a               " Enable mouse support
set clipboard=unnamedplus " Use system clipboard
set undolevels=1000       " Number of undo levels
set updatecount=100       " Save swap file after 100 characters
set updatetime=1000       " Save swap file after 1 second
set wrap                  " Enable line wrapping
set linebreak             " Wrap at word boundaries
set breakindent           " Preserve indentation in wrapped lines
set splitbelow            " Horizontal split below
set splitright            " Vertical split right

" ----- Backup & Swap -----
set nobackup              " Don't create backup files
set nowritebackup         " Don't create backup before writing
set noswapfile            " Don't create swap files

" ----- Key Mappings -----
" Leader key
let mapleader = " "

" Quick save
nnoremap <Leader>w :w<CR>
nnoremap <Leader>q :q<CR>
nnoremap <Leader>x :x<CR>

" Clear search highlighting
nnoremap <Leader>h :noh<CR>

" Navigate splits
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

" Resize splits
nnoremap <Leader>= :vertical resize +5<CR>
nnoremap <Leader>- :vertical resize -5<CR>

" Buffer navigation
nnoremap <Leader>bn :bnext<CR>
nnoremap <Leader>bp :bprevious<CR>
nnoremap <Leader>bd :bdelete<CR>

" Move lines up/down
nnoremap <A-j> :m .+1<CR>==
nnoremap <A-k> :m .-2<CR>==
vnoremap <A-j> :m '>+1<CR>gv=gv
vnoremap <A-k> :m '<-2<CR>gv=gv

" Better tabbing
vnoremap < <gv
vnoremap > >gv

" ----- Status Line -----
set statusline=
set statusline+=\ %F          " Filename
set statusline+=\ %m          " Modified flag
set statusline+=\ %r          " Read-only flag
set statusline+=\ %=          " Right side
set statusline+=\ %y          " Filetype
set statusline+=\ [%l:%c]     " Line and column
set statusline+=\ [%L]        " Total lines

" ----- File Type Specific -----
" Python
autocmd FileType python setlocal tabstop=4 shiftwidth=4 expandtab

" JavaScript/TypeScript
autocmd FileType javascript,typescript setlocal tabstop=2 shiftwidth=2

" HTML/CSS
autocmd FileType html,css setlocal tabstop=2 shiftwidth=2

" ----- Functions -----
" Remove trailing whitespace on save
autocmd BufWritePre * :%s/\s\+$//e

" Return to last edit position when opening files
autocmd BufReadPost *
     \ if line("'\"") > 0 && line("'\"") <= line("$") |
     \   exe "normal! g`\"" |
     \ endif

" ----- Abbreviations -----
iabbrev adn and
iabbrev teh the
iabbrev @@ user@example.com
```

### 3. Comparison: Nano vs Vim

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NANO VS VIM DETAILED COMPARISON                       │
├─────────────────────┬─────────────────┬─────────────────────────────────┤
│ Aspect              │ Nano            │ Vim                             │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ LEARNING CURVE                                                            │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ Time to basic use   │ 5 minutes       │ 1-2 hours                       │
│ Time to proficient  │ 1 day           │ 1-2 weeks                       │
│ Time to master      │ 1 week          │ Months/Years                    │
│ Mental model        │ Like Notepad    │ Modal editing                   │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ INTERFACE                                                                 │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ Help                │ Always visible  │ :help command                   │
│ Shortcuts           │ Shown at bottom │ Must memorize                   │
│ Modes               │ Single mode     │ Multiple modes                  │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ FEATURES                                                                  │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ Syntax highlighting │ Basic           │ Advanced                        │
│ Multiple files      │ Yes (limited)   │ Yes (buffers, splits)           │
│ Search/Replace      │ Basic           │ Advanced (regex)                │
│ Undo/Redo           │ Single undo     │ Multiple undo levels            │
│ Macros              │ No              │ Yes                             │
│ Plugins             │ No              │ Extensive                       │
│ Scripting           │ No              │ Vimscript, Lua                  │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ PERFORMANCE                                                               │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ Startup time        │ Very fast       │ Fast                            │
│ Memory usage        │ Very low        │ Low                             │
│ Large files         │ Good            │ Excellent                       │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ CUSTOMIZATION                                                             │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ Config file         │ .nanorc         │ .vimrc                          │
│ Options             │ Limited         │ Extensive                       │
│ Theming             │ Basic           │ Full color schemes              │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ BEST USE CASES                                                            │
├─────────────────────┼─────────────────┼─────────────────────────────────┤
│ Quick edits         │ ⭐⭐⭐⭐⭐        │ ⭐⭐⭐                           │
│ Config files        │ ⭐⭐⭐⭐⭐        │ ⭐⭐⭐⭐                          │
│ Programming         │ ⭐⭐            │ ⭐⭐⭐⭐⭐                        │
│ Long sessions       │ ⭐⭐            │ ⭐⭐⭐⭐⭐                        │
│ Remote servers      │ ⭐⭐⭐⭐         │ ⭐⭐⭐⭐⭐                        │
│ Learning            │ ⭐⭐⭐⭐⭐        │ ⭐⭐                            │
└─────────────────────┴─────────────────┴─────────────────────────────────┘
```

### 4. Other Editors

#### Micro Editor

```bash
# Install Micro
pkg install micro

# Open file
micro filename.txt

# Key features
# - Ctrl+C/V/X for copy/paste/cut
# - Ctrl+S to save
# - Ctrl+Q to quit
# - Mouse support by default
# - Multiple cursors (Alt+click)
# - Plugin support
```

Micro configuration:

```bash
# Create config directory
mkdir -p ~/.config/micro

# Create settings file
cat > ~/.config/micro/settings.json << 'EOF'
{
    "autosave": 60,
    "colorscheme": "monokai",
    "cursorline": true,
    "diffgutter": true,
    "eofnewline": true,
    "fastdirty": true,
    "fileformat": "unix",
    "ignorecase": true,
    "indentchar": " ",
    "keepautoindent": true,
    "matchbrace": true,
    "mkparents": true,
    "rmtrailingws": true,
    "savecursor": true,
    "saveundo": true,
    "scrollmargin": 5,
    "scrollspeed": 2,
    "softwrap": true,
    "splitbottom": true,
    "splitright": true,
    "statusformatl": "$(filename) $(modified)($(line),$(col))",
    "statusformatr": "$(bind:ToggleKeyMenu): bindings, $(bind:ToggleHelp): help",
    "syntax": true,
    "tabhighlight": true,
    "tabsize": 4,
    "tabstospaces": true
}
EOF
```

#### Emacs

```bash
# Install Emacs
pkg install emacs

# Open Emacs
emacs

# Open file
emacs filename.txt

# Basic Emacs commands
# Ctrl+x Ctrl+f - Find/open file
# Ctrl+x Ctrl+s - Save file
# Ctrl+x Ctrl+c - Quit Emacs
# Ctrl+x Ctrl+w - Save as
# Ctrl+s - Search forward
# Ctrl+r - Search backward
# Ctrl+k - Cut line
# Ctrl+y - Paste
# Ctrl+_ - Undo
# Ctrl+g - Cancel command
```

#### Neovim

```bash
# Install Neovim
pkg install neovim

# Open file
nvim filename.txt

# Neovim is a modern fork of Vim
# - Better default settings
# - Built-in LSP support
# - Lua scripting
# - Modern plugin architecture
# - Compatible with most Vim commands
```

---

## 📋 COMMANDS REFERENCE

### Nano Quick Reference Card

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         NANO QUICK REFERENCE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  FILE                    │  EDITING                 │  NAVIGATION       │
│  ────                    │  ────────                │  ──────────       │
│  Ctrl+O  Save            │  Ctrl+K  Cut line        │  Ctrl+A  Line     │
│  Ctrl+X  Exit            │  Ctrl+U  Paste           │          start    │
│  Ctrl+R  Read file       │  Alt+6   Copy            │  Ctrl+E  Line     │
│  Ctrl+S  Quick save      │  Alt+U   Undo            │          end      │
│                          │  Alt+E   Redo            │  Ctrl+_  Go to    │
│  SEARCH                  │                          │          line     │
│  ──────                  │  SELECTION               │  Ctrl+Y  Page     │
│  Ctrl+W  Search          │  ──────────              │          up       │
│  Alt+W   Next match      │  Alt+A   Start/End       │  Ctrl+V  Page     │
│  Ctrl+\  Replace         │          selection       │          down     │
│                          │  Alt+6   Copy            │                   │
│                          │  Ctrl+K  Cut             │  Ctrl+G  Help     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Vim Quick Reference Card

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         VIM QUICK REFERENCE                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  MODES                   │  NAVIGATION             │  EDITING           │
│  ─────                   │  ──────────             │  ───────           │
│  i     Insert mode       │  h j k l  ←↓↑→          │  dd  Delete line   │
│  v     Visual mode       │  w  b     Word          │  yy  Copy line     │
│  :     Command mode      │  0  $     Line          │  p   Paste         │
│  Esc   Normal mode       │  gg G     File          │  u   Undo          │
│                          │  :n       Line n        │  x   Delete char   │
│  COMMAND MODE            │                          │                    │
│  ────────────            │  SEARCH                 │  REPLACE           │
│  :w   Save               │  ──────                 │  ───────           │
│  :q   Quit               │  /pattern  Forward      │  r   Replace char  │
│  :wq  Save & quit        │  ?pattern  Backward     │  R   Replace mode  │
│  :q!  Force quit         │  n    Next match        │  cw  Change word   │
│  :x   Save & quit        │  N    Prev match        │  cc  Change line   │
│                                                                          │
│  INSERT MODE: i I a A o O    VISUAL: v V Ctrl+v                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### All Nano Shortcuts

| Shortcut | Action |
|----------|--------|
| **File Operations** | |
| Ctrl+O | Write Out (Save) |
| Ctrl+X | Exit |
| Ctrl+R | Read/Insert file |
| Ctrl+S | Save without prompt |
| **Navigation** | |
| Ctrl+A | Move to beginning of line |
| Ctrl+E | Move to end of line |
| Ctrl+Y | Page Up |
| Ctrl+V | Page Down |
| Ctrl+_ | Go to line number |
| Alt+\ | Go to beginning of file |
| Alt+/ | Go to end of file |
| **Editing** | |
| Ctrl+K | Cut current line |
| Ctrl+U | Paste |
| Alt+6 | Copy |
| Ctrl+J | Justify paragraph |
| Alt+U | Undo |
| Alt+E | Redo |
| **Search** | |
| Ctrl+W | Search |
| Alt+W | Next search match |
| Alt+Q | Previous search match |
| Ctrl+\ | Find and Replace |
| **Selection** | |
| Alt+A | Start/End selection |
| Alt+Shift+6 | Copy selection |
| **Other** | |
| Ctrl+G | Help |
| Ctrl+T | Spell check |
| Ctrl+C | Show cursor position |

### All Vim Commands

| Command | Action |
|---------|--------|
| **Modes** | |
| i | Insert before cursor |
| I | Insert at line beginning |
| a | Insert after cursor |
| A | Insert at line end |
| o | New line below |
| O | New line above |
| v | Visual mode |
| V | Visual Line mode |
| Ctrl+v | Visual Block mode |
| Esc | Return to Normal mode |
| **Navigation** | |
| h, j, k, l | Left, Down, Up, Right |
| w | Next word start |
| b | Previous word start |
| e | Word end |
| 0 | Line beginning |
| $ | Line end |
| ^ | First non-blank |
| gg | First line |
| G | Last line |
| nG or :n | Go to line n |
| Ctrl+f | Page down |
| Ctrl+b | Page up |
| Ctrl+d | Half page down |
| Ctrl+u | Half page up |
| H | Screen top |
| M | Screen middle |
| L | Screen bottom |
| **Editing** | |
| x | Delete character |
| X | Delete previous character |
| dd | Delete line |
| dw | Delete word |
| d$ or D | Delete to line end |
| d0 | Delete to line start |
| yy | Copy line |
| yw | Copy word |
| y$ | Copy to line end |
| p | Paste after |
| P | Paste before |
| u | Undo |
| Ctrl+r | Redo |
| r | Replace character |
| R | Replace mode |
| cw | Change word |
| cc | Change line |
| c$ or C | Change to line end |
| ~ | Toggle case |
| J | Join lines |
| **Search** | |
| /pattern | Search forward |
| ?pattern | Search backward |
| n | Next match |
| N | Previous match |
| * | Search word under cursor |
| # | Search word backward |
| **Replace** | |
| :s/old/new/ | Replace first in line |
| :s/old/new/g | Replace all in line |
| :%s/old/new/g | Replace all in file |
| :%s/old/new/gc | Replace with confirmation |
| **Command Mode** | |
| :w | Save |
| :q | Quit |
| :wq or :x | Save and quit |
| :q! | Quit without saving |
| :e file | Edit file |
| :r file | Read/insert file |
| :set number | Show line numbers |
| :syntax on | Enable highlighting |
| :noh | Clear search highlight |
| **Visual Mode** | |
| d | Delete selection |
| y | Copy selection |
| c | Change selection |
| > | Indent |
| < | Unindent |
| u | Lowercase |
| U | Uppercase |

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Nano Basics

```bash
# Task: Learn basic Nano operations

# Step 1: Create a new file
nano practice1.txt

# Step 2: Type the following content:
"""
Hello, this is my first file in Nano!
Line 2: Learning Nano editor
Line 3: This is line number three
Line 4: Termux is awesome
Line 5: Keep practicing!
"""

# Step 3: Save the file (Ctrl+O, then Enter)
# Step 4: Exit Nano (Ctrl+X)

# Step 5: Reopen the file
nano practice1.txt

# Step 6: Search for "Learning" (Ctrl+W, type "Learning", Enter)
# Step 7: Replace "awesome" with "amazing" (Ctrl+\, "awesome", "amazing", Y)
# Step 8: Go to line 3 (Ctrl+_, type 3, Enter)
# Step 9: Cut line 3 (Ctrl+K)
# Step 10: Paste it at the end (go to end, Ctrl+U)
# Step 11: Save and exit

# Verify
cat practice1.txt
```

### Exercise 2: Vim Basics

```bash
# Task: Learn basic Vim operations

# Step 1: Create a new file
vim practice2.txt

# Step 2: Press 'i' to enter Insert mode
# Step 3: Type the following:
"""
Vim Practice File
=================
1. First item
2. Second item
3. Third item
4. Fourth item
5. Fifth item
"""

# Step 4: Press Esc to return to Normal mode
# Step 5: Type :w and press Enter to save
# Step 6: Practice navigation (h, j, k, l)
# Step 7: Go to first line (gg)
# Step 8: Go to last line (G)
# Step 9: Go to line 3 (:3)
# Step 10: Delete line 3 (dd)
# Step 11: Undo (u)
# Step 12: Copy line 1 (yy)
# Step 13: Paste it at end (G, then p)
# Step 14: Search for "item" (/item, Enter)
# Step 15: Go to next match (n)
# Step 16: Save and quit (:wq)

# Verify
cat practice2.txt
```

### Exercise 3: Nano Configuration

```bash
# Task: Configure Nano with .nanorc

# Step 1: Create .nanorc file
nano ~/.nanorc

# Step 2: Add the following configuration:
"""
# Nano Configuration
set autoindent
set constantshow
set linenumbers
set mouse
set softwrap
set tabsize 4
set tabstospaces

# Include syntax highlighting
include /data/data/com.termux/files/usr/share/nano/*.nanorc
"""

# Step 3: Save and exit

# Step 4: Test the configuration
nano test_nano_config.txt

# Notice:
# - Line numbers on left
# - Soft wrap enabled
# - Mouse support active
```

### Exercise 4: Vim Configuration

```bash
# Task: Configure Vim with .vimrc

# Step 1: Create .vimrc file
vim ~/.vimrc

# Step 2: Enter Insert mode (i) and add:
"""
" Vim Configuration
syntax on
set number
set autoindent
set tabstop=4
set shiftwidth=4
set expandtab
set hlsearch
set incsearch
set ignorecase
set smartcase
"""

# Step 3: Save and exit (:wq)

# Step 4: Test the configuration
vim test_vim_config.txt

# Type some content and notice:
# - Line numbers visible
# - Syntax highlighting active
# - Tab inserts 4 spaces
```

### Exercise 5: Create a Script with Nano

```bash
# Task: Create a Python script using Nano

# Step 1: Create script file
nano hello.py

# Step 2: Type the following Python code:
"""
#!/usr/bin/env python3

def greet(name):
    \"\"\"Greet the user.\"\"\"
    print(f"Hello, {name}!")
    print("Welcome to Termux!")

def main():
    name = input("Enter your name: ")
    greet(name)

if __name__ == "__main__":
    main()
"""

# Step 3: Save and exit (Ctrl+O, Enter, Ctrl+X)

# Step 4: Make executable
chmod +x hello.py

# Step 5: Run the script
python hello.py

# Step 6: Test syntax highlighting
nano hello.py
# Notice Python syntax is highlighted
```

### Exercise 6: Create a Script with Vim

```bash
# Task: Create a Bash script using Vim

# Step 1: Create script file
vim backup.sh

# Step 2: Press 'i' for Insert mode and type:
"""
#!/bin/bash

# Simple backup script

BACKUP_DIR="$HOME/backups"
DATE=$(date +%Y%m%d_%H%M%S)

# Create backup directory
mkdir -p "$BACKUP_DIR"

# Backup home directory
echo "Creating backup..."
tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" -C "$HOME" .

echo "Backup created: $BACKUP_DIR/backup_$DATE.tar.gz"
echo "Done!"
"""

# Step 3: Press Esc, then :wq to save and quit

# Step 4: Make executable
chmod +x backup.sh

# Step 5: View the file
cat backup.sh

# Step 6: Edit with Vim and test syntax highlighting
vim backup.sh
# Notice shell syntax is highlighted
```

### Exercise 7: Vim Search and Replace

```bash
# Task: Practice Vim search and replace

# Step 1: Create a test file
vim replace_test.txt

# Step 2: Enter Insert mode (i) and type:
"""
The quick brown fox jumps over the lazy dog.
The quick brown fox is very quick.
The fox is quicker than the dog.
The dog is not quick at all.
Quick thinking wins the game.
"""

# Step 3: Return to Normal mode (Esc)

# Step 4: Save (:w)

# Step 5: Replace all "quick" with "fast"
# Type: :%s/quick/fast/g
# Press Enter

# Step 6: Undo (u)

# Step 7: Replace with confirmation
# Type: :%s/quick/fast/gc
# Press Enter
# Press 'y' or 'n' for each occurrence

# Step 8: Save and quit (:wq)
```

### Exercise 8: Advanced Vim Operations

```bash
# Task: Practice advanced Vim operations

# Step 1: Create a test file
vim advanced_test.txt

# Step 2: Enter Insert mode and type 10 lines:
"""
Line 1: First line of text
Line 2: Second line of text
Line 3: Third line of text
Line 4: Fourth line of text
Line 5: Fifth line of text
Line 6: Sixth line of text
Line 7: Seventh line of text
Line 8: Eighth line of text
Line 9: Ninth line of text
Line 10: Tenth line of text
"""

# Step 3: Practice these operations:
# Delete 3 lines: 3dd
# Undo: u
# Copy 5 lines: 5yy
# Go to end: G
# Paste: p
# Go to beginning: gg
# Delete to end of line: d$
# Change word: cw
# Set marker: ma
# Go to marker: 'a

# Step 4: Visual mode practice:
# Enter Visual mode: v
# Select text with movement keys
# Delete selection: d
# Undo: u

# Step 5: Visual Block practice:
# Enter Visual Block: Ctrl+v
# Select a block
# Insert text: I (type text, then Esc)

# Step 6: Save and quit (:wq)
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Nano not installed

```bash
# Cause: Nano not in default installation

# Solution:
pkg update
pkg install nano

# Verify:
which nano
nano --version
```

### Problem 2: Nano shows garbled characters

```bash
# Cause: Encoding issues

# Solution 1: Set locale
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8

# Solution 2: Use -w flag for wide characters
nano -w filename

# Solution 3: Check terminal encoding
echo $TERM
# Should show something like xterm-256color

# Solution 4: Install locales
pkg install locales
```

### Problem 3: Vim stuck in insert mode

```bash
# Cause: User doesn't know how to exit insert mode

# Solution: Press Esc key
# If still stuck, press Esc multiple times
# Or press Ctrl+[ (equivalent to Esc)

# If completely stuck:
# Press Ctrl+C to cancel any command
# Then press Esc
```

### Problem 4: Can't exit Vim

```bash
# The classic problem! Here are all ways to exit:

# Normal exit:
Esc (to return to Normal mode)
:q (then Enter)

# Force quit (discard changes):
:q! (then Enter)

# Save and quit:
:wq (then Enter)
# OR
:x (then Enter)
# OR
ZZ (in Normal mode, without colon)

# Emergency exit:
Ctrl+z (suspend - then 'kill %1' to kill)
# OR
Ctrl+c then :q!
```

### Problem 5: Vim syntax highlighting not working

```bash
# Cause: Syntax highlighting disabled or not available

# Solution 1: Enable in Vim
:syntax on

# Solution 2: Add to .vimrc
echo "syntax on" >> ~/.vimrc

# Solution 3: Check filetype detection
:filetype on
:filetype plugin on
:filetype indent on

# Solution 4: Check terminal colors
echo $TERM
# Should be xterm-256color or similar

# Solution 5: Install vim-runtime for extra syntax files
pkg install vim-runtime
```

### Problem 6: Vim arrow keys insert letters

```bash
# Cause: In Insert mode, arrow keys may not work correctly

# Solution 1: Use Normal mode for navigation
# Press Esc, then use h,j,k,l

# Solution 2: Add to .vimrc
cat >> ~/.vimrc << 'EOF'
" Fix arrow keys in insert mode
set nocompatible
EOF

# Solution 3: Check if nocompatible is set
:set nocompatible
```

### Problem 7: Nano paste messes up indentation

```bash
# Cause: Auto-indent interacting with paste

# Solution 1: Disable auto-indent temporarily
# In Nano: Alt+P (toggle auto-indent)

# Solution 2: Use -i flag to disable
nano -i filename

# Solution 3: Paste slowly or use Ctrl+U after Ctrl+K
```

### Problem 8: Vim paste has extra indentation

```bash
# Cause: Auto-indent interfering with paste

# Solution 1: Use paste mode
:set paste
# Then paste your content
:set nopaste

# Solution 2: Add toggle to .vimrc
echo 'set pastetoggle=<F2>' >> ~/.vimrc
# Then press F2 to toggle paste mode

# Solution 3: Use bracketed paste (if terminal supports)
set t_BE=
```

### Problem 9: Large file makes editor slow

```bash
# Nano with large files:
# Solution: Use -S for smooth scrolling
nano -S largefile.txt

# Vim with large files:
# Solution 1: Disable some features
vim -u NONE largefile.txt

# Solution 2: Use Vim LargeFile plugin
# Or add to .vimrc:
autocmd BufReadPre * if getfsize(expand('%')) > 10000000 | set eventignore+=FileType | endif
```

### Problem 10: Colors not showing correctly

```bash
# Check terminal capability:
echo $TERM
tput colors

# If colors are limited, set TERM:
export TERM=xterm-256color

# For Nano:
# Colors are limited, syntax highlighting is basic

# For Vim:
:syntax on
:colorscheme default
:colorscheme desert  # Try different schemes
:colorscheme evening
:colorscheme morning

# List available colorschemes:
:colorscheme <Tab>
```

### Problem 11: Nano or Vim crashes

```bash
# Cause: Low memory or corrupted file

# Solution 1: Check disk space
df -h

# Solution 2: Check memory
free -h

# Solution 3: Check for swap files (Vim)
ls -la .*swp
rm .filename.swp  # Remove if found

# Solution 4: Recover from swap
vim -r filename

# Solution 5: Restart Termux
exit
# Reopen Termux
```

### Problem 12: Can't save file (permission denied)

```bash
# Cause: No write permission

# Check permissions:
ls -la filename

# Solution 1: Change permissions
chmod +w filename

# Solution 2: Save to different location
# In Nano: Ctrl+O, change path
# In Vim: :w ~/newpath/filename

# Solution 3: If system file, need to understand limitations
# Termux runs in sandbox, can't edit system files
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Nano & Vim Comparison**
```
┌────────────────────────────────────┐
│  [Split Screen]                    │
│                                    │
│  NANO        │        VIM          │
│  ⭐ Easy     │    ⭐⭐⭐ Pro        │
│  Beginners   │    Power Users      │
│                                    │
│  TEXT EDITORS                      │
│  COMPLETE GUIDE                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option B: Vim Focus**
```
┌────────────────────────────────────┐
│  🔥 MASTER VIM 🔥                  │
│                                    │
│  i → Insert                        │
│  Esc → Normal                      │
│  :wq → Save & Quit                 │
│                                    │
│  TERMINAL EDITING                  │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Cheat Sheet Style**
```
┌────────────────────────────────────┐
│  📝 TEXT EDITORS                   │
│                                    │
│  NANO: Ctrl+O = Save               │
│        Ctrl+X = Exit               │
│                                    │
│  VIM: :wq = Save & Quit            │
│       dd = Delete Line             │
│                                    │
│  COMPLETE TUTORIAL                 │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📝 Termux Full Course - Chapter 8: Text Editors | Nano & Vim Complete Guide

🔥 In this video you'll learn:
• Text editors kya hote hain
• Nano editor complete tutorial
• Nano shortcuts aur configuration
• Vim editor modes aur commands
• Vim navigation aur editing
• Search aur replace operations
• Nano vs Vim comparison
• .vimrc aur .nanorc configuration

⏱️ Timestamps:
0:00 - Introduction
0:45 - Text Editors Introduction
2:30 - Nano Editor Basics
4:30 - Nano Operations
8:00 - Nano Shortcuts Summary
9:30 - Vim Editor Introduction
12:00 - Vim Modes & Commands
15:00 - Vim Editing Commands
17:30 - Vim Shortcuts Summary
18:30 - Nano vs Vim Comparison
19:30 - Other Editors & Summary

📝 Commands from this video:
pkg install nano
pkg install vim
nano filename
vim filename

Nano: Ctrl+O (Save), Ctrl+X (Exit), Ctrl+W (Search)
Vim: i (Insert), Esc (Normal), :wq (Save & Quit)

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #Vim #Nano #TermuxEditor #T3rmuxk1ng #LinuxTerminal #TerminalEditor #LearnVim #TermuxCourse

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux, vim, nano, text editor, termux vim, termux nano, 
vim tutorial, nano tutorial, vim hindi, terminal editor, 
linux editor, vim commands, nano commands, vim basics, 
learn vim, vim for beginners, termux text editor, 
termux course, t3rmuxk1ng, vim modes, vim navigation, 
vim shortcuts, nano shortcuts, .vimrc, .nanorc, 
terminal text editing, command line editor
```

### Hashtags

```
#Termux #Vim #Nano #TextEditor #TerminalEditor #VimTutorial 
#NanoTutorial #TermuxCourse #T3rmuxk1ng #LinuxTerminal 
#LearnVim #VimCommands #TermuxHindi #HindiTutorial
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Nano Manual | `man nano` in terminal |
| Nano Manual Online | https://nano-editor.org/dist/latest/nano.html |
| Vim Documentation | `:help` in Vim |
| Vim Official | https://www.vim.org/ |
| Vim Tips Wiki | https://vim.fandom.com/ |
| Micro Editor | https://micro-editor.github.io/ |
| Neovim | https://neovim.io/ |

### Cheat Sheets

| Resource | Description |
|----------|-------------|
| Vim Cheat Sheet | https://vim.rtorr.com/ |
| Nano Cheat Sheet | https://www.nano-editor.org/dist/latest/cheatsheet.html |
| Vim Adventures | Learn Vim through a game |
| OpenVim | Interactive Vim tutorial |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Vim Tutor | Run `vimtutor` in terminal |
| Vim Adventures | https://vim-adventures.com/ |
| Vim Golf | https://www.vimgolf.com/ |
| OpenVim | https://www.openvim.com/ |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 9, verify:

- [ ] Nano installed and working
- [ ] Can create, edit, save files in Nano
- [ ] Know Nano shortcuts: Ctrl+O, Ctrl+X, Ctrl+W
- [ ] Vim installed and working
- [ ] Understand Vim modes (Normal, Insert, Command, Visual)
- [ ] Can navigate in Vim (h,j,k,l, w, b, gg, G)
- [ ] Know basic Vim commands (i, Esc, :w, :q, :wq, dd, yy, p)
- [ ] Created .nanorc configuration
- [ ] Created .vimrc configuration
- [ ] Understand difference between Nano and Vim
- [ ] Completed practice exercises

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 9: Termux Styling**

- Customizing Termux appearance
- Changing colors and fonts
- Creating custom color schemes
- Termux:Styling app usage
- PS1 prompt customization
- Creating an attractive terminal
- Best practices for readability

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
