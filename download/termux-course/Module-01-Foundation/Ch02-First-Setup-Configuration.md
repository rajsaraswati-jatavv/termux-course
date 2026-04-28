# Chapter 2: First Setup & Configuration

> **Module:** 1 - Foundation  
> **Chapter:** 2 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐ Beginner  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Configuration files, environment variables |
| .bashrc Setup | Complete customization with 20+ aliases |
| Commands Reference | All commands covered in chapter |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common configuration issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 2
Title: Termux Setup & Configuration | .bashrc, Aliases, Customization
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Chapter 1 mein humne Termux install kiya, update kiya, aur storage 
access setup kiya. Ab aapka Termux ready hai.

Lekin abhi ye default configuration hai - jo ki basic hai. Aaj ke 
chapter mein hum Termux ko PROFESSIONAL level pe configure karenge.

Hum seekhenge:
- Configuration files kahan hoti hain
- Environment variables kya hote hain
- .bashrc file banana aur customize karna
- 20+ useful aliases jo aapka kaam aasan banayein
- Custom prompt (PS1) design karna
- Welcome message setup karna

Ye chapter aapke Termux ko personalized banayega - jaise aap apne 
laptop ka terminal customize karte ho.

To chaliye shuru karte hain!

---

[SECTION 1: CONFIGURATION DIRECTORY - 0:45 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle, hum Termux ki configuration directory samjhte hain.

Termux mein ek special directory hoti hai - ~/.termux/

~ ka matlab hai aapka home directory, yaani:
/data/data/com.termux/files/home

.termux folder mein Termux ke configuration files hoti hain.

Chaliye check karte hain:

    ls -la ~/.termux/

Agar ye folder nahi hai, to create karein:

    mkdir ~/.termux

Is folder mein kya kya hota hai? Main explain karta hoon:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX CONFIGURATION FILES                            │
├──────────────────────────┬──────────────────────────────────────────────┤
│ File                     │ Purpose                                      │
├──────────────────────────┼──────────────────────────────────────────────┤
│ termux.properties        │ Main Termux config file                      │
│ termux-shell.properties  │ Shell-specific settings                      │
│ colors.properties        │ Color scheme (via Termux:Styling)            │
│ font.ttf                 │ Custom font file                             │
│ termux-url-opener        │ URL handler script                           │
└──────────────────────────┴──────────────────────────────────────────────┘

Sabse important file hai - termux.properties

Ye file Termux app ke behaviour ko control karti hai. Jaise:
- Back button kya kare
- Terminal bells enable/disable
- Shortcut keys
- Extra keys row

Chaliye ek example dekhein. Create karte hain termux.properties file:

    nano ~/.termux/termux.properties

Nan editor mein ye content likhein:

    # Back button behavior - back key acts as escape
    back-key=escape
    
    # Enable bell
    bell-character=ignore
    
    # Extra keys row
    extra-keys = [[ \
      {key: ESC, popup: {macro: "CTRL d", display: "exit"}}, \
      {key: CTRL, popup: {macro: "CTRL c", display: "cancel"}}, \
      {key: ALT, popup: {macro: "CTRL z", display: "undo"}}, \
      {key: TAB, popup: {macro: "CTRL a", display: "all"}}, \
      {key: '/', popup: '~'}, \
      {key: '-', popup: '_'}, \
      {key: HOME, popup: END}, \
      {key: UP, popup: PGUP}, \
      {key: DOWN, popup: PGDN} \
    ]]

CTRL + O press karein to save, Enter karein, phir CTRL + X to exit.

Ab Termux ko reload karein:

    termux-reload-settings

Ya phir Termux app ko close karein (swipe from recent apps) aur 
phir se open karein.

Ab aapko extra keys row dikhega keyboard ke upar! Ye bahut useful 
hai commands type karne ke liye.

---

[SECTION 2: ENVIRONMENT VARIABLES - 4:00 to 7:30]
─────────────────────────────────────────────────────────────────────────────

Ab environment variables ki baat karte hain.

Environment variables ye hote hain - system-wide values jo programs 
ko important paths aur settings batate hain.

Termux mein kuch important environment variables hain:

    echo $PREFIX

PREFIX variable batata hai ki Termux ka main folder kahan hai.
Output: /data/data/com.termux/files/usr

Is folder mein:
- bin/ - Executable files (commands)
- lib/ - Libraries
- etc/ - Configuration files
- share/ - Documentation and data

    echo $HOME

HOME variable aapka home directory batata hai.
Output: /data/data/com.termux/files/home

Ye aapka personal space hai jahan aap apni files, scripts, 
projects rakh sakte ho.

    echo $PATH

PATH variable batata hai ki system ko commands kahan dhundhne hain.
Multiple paths hote hain, colon (:) se separate:

Output kuch aisa dikhega:
/data/data/com.termux/files/usr/bin:/data/data/com.termux/files/usr/bin/applets

Jab aap koi command type karte ho, jaise "python", system PATH 
mein diye gaye folders mein dhundhta hai.

Isliye aap directly "python" likh sakte ho instead of:
/data/data/com.termux/files/usr/bin/python

Kuch aur important variables:

    echo $SHELL
    # Output: /data/data/com.termux/files/usr/bin/bash

    echo $TERMUX_VERSION
    # Output: 0.118.0 (or your version)

    echo $LANG
    # Output: en_US.UTF-8

    echo $PWD
    # Current working directory

    echo $USER
    # Current username

Ye variables scripts mein bahut useful hain. Aap inhe apni 
scripts mein use kar sakte ho.

Custom environment variable banana:

    export MY_VARIABLE="Hello Termux"
    echo $MY_VARIABLE
    # Output: Hello Termux

Lekin ye temporary hai - Termux band karne pe delete ho jaayega.

Permanent ke liye .bashrc file use karte hain - jo next section mein 
seekhenge.

---

[SECTION 3: .bashrc FILE CREATION - 7:30 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab main aapko .bashrc file banana sikhaunga - ye bahut powerful hai.

.bashrc ek aisi file hai jo har baar run hoti jab aap Termux 
open karte ho ya naya bash shell start karte ho.

Isme aap likh sakte ho:
- Aliases (command shortcuts)
- Custom functions
- Environment variables
- Welcome messages
- Custom prompts
- Auto-run commands

Pehle check karein ki .bashrc file hai ya nahi:

    ls -la ~

Agar .bashrc nahi hai, to create karein:

    nano ~/.bashrc

Ab hum isme content add karenge. Main step by step bataunga.

Pehle shebang line - ye batata hai ki ye bash script hai:

    #!/data/data/com.termux/files/usr/bin/bash

Ab comments add karein:

    #############################################################
    #                                                           #
    #              TERMUX BASH CONFIGURATION FILE               #
    #                    Created by T3rmuxk1ng                  #
    #                                                           #
    #############################################################

Ab useful environment variables:

    # =====================================
    # ENVIRONMENT VARIABLES
    # =====================================
    
    # Editor preference
    export EDITOR=nano
    export VISUAL=nano
    
    # History settings
    export HISTSIZE=10000
    export HISTFILESIZE=20000
    export HISTCONTROL=ignoreboth
    
    # Custom paths (if you have custom scripts)
    export PATH="$HOME/scripts:$PATH"
    
    # Language
    export LANG=en_US.UTF-8

Ab save karein: CTRL + O, Enter, CTRL + X

Har baar Termux open karne pe ye settings load hongi!

---

[SECTION 4: ALIASES - 20+ USEFUL ALIASES - 11:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab aliases ki baad karte hain - ye sabse useful feature hai!

Alias kya hai? Alias ek shortcut hai - ek chhota naam bade command ke liye.

Example:
Har baar "pkg update && pkg upgrade -y" type karna boring hai.
Sahi hai "update" likho aur kaam ho jaaye!

Chaliye 20+ useful aliases banate hain. .bashrc file karein:

    nano ~/.bashrc

Neeche ye content add karein:

    # =====================================
    # USEFUL ALIASES
    # =====================================
    
    # === PACKAGE MANAGEMENT ===
    alias update='pkg update && pkg upgrade -y'
    alias install='pkg install'
    alias remove='pkg uninstall'
    alias search='pkg search'
    alias packages='pkg list-installed'
    
    # === NAVIGATION ===
    alias ..='cd ..'
    alias ...='cd ../..'
    alias ....='cd ../../..'
    alias home='cd ~'
    alias root='cd $PREFIX'
    
    # === LISTING FILES ===
    alias ls='ls --color=auto'
    alias ll='ls -la'
    alias la='ls -A'
    alias l='ls -CF'
    alias lsize='ls -lhS'
    alias ltime='ls -lt'
    
    # === FILE OPERATIONS ===
    alias cp='cp -i'
    alias mv='mv -i'
    alias rm='rm -i'
    alias mkdir='mkdir -pv'
    alias ..='cd ..'
    
    # === GREP ===
    alias grep='grep --color=auto'
    alias egrep='egrep --color=auto'
    alias fgrep='fgrep --color=auto'
    
    # === SYSTEM ===
    alias c='clear'
    alias cls='clear'
    alias h='history'
    alias j='jobs'
    alias path='echo $PATH | tr ":" "\n"'
    alias now='date'
    alias week='date +%V'
    
    # === NETWORK ===
    alias myip='curl -s ifconfig.me'
    alias ports='netstat -tulanp'
    alias ping='ping -c 5'
    
    # === DEVELOPMENT ===
    alias py='python'
    alias python='python3'
    alias pip='pip3'
    alias g='git'
    alias gs='git status'
    alias ga='git add'
    alias gc='git commit'
    alias gp='git push'
    alias gl='git log --oneline'
    
    # === TERMUX SPECIFIC ===
    alias ts='termux-setup-storage'
    alias reload='source ~/.bashrc && echo "Bashrc reloaded!"'
    alias bashrc='nano ~/.bashrc'
    alias bashrc-edit='nano ~/.bashrc'
    
    # === FUN ===
    alias weather='curl -s wttr.in'
    alias starwars='telnet towel.blinkenlights.nl'
    alias myinfo='echo "User: $(whoami)" && echo "Home: $HOME" && echo "Shell: $SHELL"'

Save karein: CTRL + O, Enter, CTRL + X

Ab ye aliases load karein:

    source ~/.bashrc

Ya simply Termux close aur open karein.

Ab test karein:

    update
    # Ye pkg update && pkg upgrade -y run karega
    
    myip
    # Aapka public IP dikhayega
    
    weather
    # Weather forecast dikhega
    
    ll
    # Detailed file listing
    
    c
    # Screen clear

Kitna aasan ho gaya! Chhote commands, bade kaam!

---

[SECTION 5: PS1 PROMPT CUSTOMIZATION - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Ab prompt customize karte hain - PS1 variable se.

Prompt wo text hai jo har command ke baad dikhta hai, jaise:
~ $

Ye default prompt boring hai. Chaliye ise customize karein!

.bashrc file mein ye add karein:

    nano ~/.bashrc

Neeche add karein:

    # =====================================
    # CUSTOM PROMPT (PS1)
    # =====================================
    
    # Color codes
    RED='\[\033[0;31m\]'
    GREEN='\[\033[0;32m\]'
    YELLOW='\[\033[0;33m\]'
    BLUE='\[\033[0;34m\]'
    PURPLE='\[\033[0;35m\]'
    CYAN='\[\033[0;36m\]'
    WHITE='\[\033[0;37m\]'
    RESET='\[\033[0m\]'
    
    # Option 1: Simple colored prompt
    # PS1="${GREEN}\w${RESET} \$ "
    
    # Option 2: Detailed prompt with user and path
    # PS1="${CYAN}\u${WHITE}@${GREEN}\h${WHITE}:${YELLOW}\w${RESET}\$ "
    
    # Option 3: Advanced prompt (RECOMMENDED)
    PS1="${RED}[${GREEN}\w${RED}]${CYAN}\$${RESET} "
    
    # Option 4: Two-line prompt (great for long paths)
    # PS1="${YELLOW}\w\n${GREEN}┌─[${RED}\u${GREEN}]─${BLUE}\$${RESET} "

Save karein aur reload karein:

    source ~/.bashrc

Prompt ke parts:
- \u = username
- \h = hostname
- \w = current directory (full path)
- \W = current directory name only
- \$ = $ for normal user, # for root
- \n = new line
- \t = current time
- \d = current date

Colors:
- RED = \[\033[0;31m\]
- GREEN = \[\033[0;32m\]
- YELLOW = \[\033[0;33m\]
- BLUE = \[\033[0;34m\]
- PURPLE = \[\033[0;35m\]
- CYAN = \[\033[0;36m\]
- WHITE = \[\033[0;37m\]
- RESET = \[\033[0m\]

Apne hisaab se customize karein!

---

[SECTION 6: CUSTOM WELCOME MESSAGE - 17:30 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Ab ek professional welcome message add karte hain!

.bashrc mein ye add karein:

    nano ~/.bashrc

End mein add karein:

    # =====================================
    # WELCOME MESSAGE
    # =====================================
    
    # Function to show welcome message
    show_welcome() {
        echo ""
        echo "╔═══════════════════════════════════════════════════════════════╗"
        echo "║                                                               ║"
        echo "║              ████████╗███████╗██████╗ ███╗   ███╗             ║"
        echo "║              ╚══██╔══╝██╔════╝██╔══██╗████╗ ████║             ║"
        echo "║                 ██║   █████╗  ██████╔╝██╔████╔██║             ║"
        echo "║                 ██║   ██╔══╝  ██╔══██╗██║╚██╔╝██║             ║"
        echo "║                 ██║   ███████╗██║  ██║██║ ╚═╝ ██║             ║"
        echo "║                 ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝             ║"
        echo "║                                                               ║"
        echo "╚═══════════════════════════════════════════════════════════════╝"
        echo ""
        echo "    ┌─────────────────────────────────────────────────────────┐"
        echo "    │  Welcome to Termux - T3rmuxk1ng Edition                 │"
        echo "    ├─────────────────────────────────────────────────────────┤"
        echo "    │  User: $(whoami)                                         "
        echo "    │  Host: $(hostname)                                       "
        echo "    │  Shell: Bash $(bash --version | head -1 | cut -d' ' -f4)    "
        echo "    │  Termux: v$(echo $TERMUX_VERSION)                                  "
        echo "    │  Date: $(date '+%A, %d %B %Y')                        "
        echo "    │  Time: $(date '+%H:%M:%S')                                   "
        echo "    ├─────────────────────────────────────────────────────────┤"
        echo "    │  Useful Commands:                                       │"
        echo "    │  • update    - Update packages                          │"
        echo "    │  • install   - Install package                          │"
        echo "    │  • myip      - Show public IP                           │"
        echo "    │  • weather   - Weather forecast                         │"
        echo "    │  • bashrc    - Edit .bashrc                             │"
        echo "    │  • reload    - Reload .bashrc                           │"
        echo "    └─────────────────────────────────────────────────────────┘"
        echo ""
    }
    
    # Show welcome message
    show_welcome

Save karein: CTRL + O, Enter, CTRL + X

Reload karein:

    source ~/.bashrc

Ab har baar Termux open karne pe ye beautiful welcome message dikhega!

---

[SECTION 7: COMPLETE .bashrc FILE - 19:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Dosto, ab main aapko complete .bashrc file dikhata hoon jo humne 
banayi hai. Ye ready-to-use hai:

[SCREEN: Complete .bashrc file scrolling]

Ye file:
- 20+ useful aliases hai
- Custom colorful prompt hai
- Welcome message hai
- Environment variables set hain
- History settings configured hain

Ise copy karke directly use kar sakte ho!

Agar kuch change karna ho:
    bashrc

Ye command nano editor mein .bashrc open karegi.

Change ke baad:
    reload

Ye command .bashrc reload karega.

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 21:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 2 complete! Let's summarize:

✅ ~/.termux/ directory - Configuration files ka home
✅ termux.properties - Termux behavior customize karna
✅ Environment variables - $PREFIX, $HOME, $PATH
✅ .bashrc file - Shell customization ka powerhouse
✅ 20+ aliases - Commands ke shortcuts
✅ PS1 prompt - Colorful professional prompt
✅ Welcome message - Personalized greeting

Important Files yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 2 - IMPORTANT FILES                           │
├─────────────────────────────────────────────────────────────────────────┤
│ ~/.termux/termux.properties    │ Termux app settings                    │
│ ~/.bashrc                       │ Bash shell configuration               │
│ ~/.bash_history                 │ Command history                        │
│ $PREFIX/etc/                    │ System configuration                   │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 3 mein hum seekhenge:
- Linux basics part 1
- File system navigation
- File and directory operations
- Permissions and ownership
- Text manipulation basics

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 3!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Termux Directory Structure

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX DIRECTORY STRUCTURE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   /data/data/com.termux/files/                                          │
│   ├── home/                           # User home directory ($HOME)      │
│   │   ├── .bashrc                     # Bash configuration               │
│   │   ├── .bash_history               # Command history                  │
│   │   ├── .bash_profile               # Bash login config                │
│   │   ├── .profile                    # User profile                     │
│   │   ├── .termux/                    # Termux config directory          │
│   │   │   ├── termux.properties       # Main Termux config               │
│   │   │   ├── colors.properties       # Color scheme                     │
│   │   │   └── font.ttf                # Custom font                      │
│   │   ├── storage/                    # Storage symlinks                 │
│   │   │   ├── dcim -> /sdcard/DCIM                                       │
│   │   │   ├── downloads -> /sdcard/Download                              │
│   │   │   ├── music -> /sdcard/Music                                     │
│   │   │   └── pictures -> /sdcard/Pictures                               │
│   │   └── scripts/                    # Custom scripts (optional)        │
│   │                                                                       │
│   └── usr/                            # System prefix ($PREFIX)          │
│       ├── bin/                        # Executable binaries              │
│       │   ├── bash                                                       │
│       │   ├── python                                                     │
│       │   ├── git                                                        │
│       │   └── ...                                                        │
│       ├── lib/                        # Libraries                        │
│       ├── etc/                        # System configuration             │
│       │   ├── apt/                    # APT configuration                │
│       │   ├── bash.bashrc             # System-wide bashrc               │
│       │   └── passwd                  # User database                    │
│       ├── share/                      # Documentation & data             │
│       ├── tmp/                        # Temporary files                  │
│       └── var/                        # Variable data                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Environment Variables Reference

| Variable | Value | Description |
|----------|-------|-------------|
| `$HOME` | `/data/data/com.termux/files/home` | User home directory |
| `$PREFIX` | `/data/data/com.termux/files/usr` | System installation prefix |
| `$PATH` | Multiple paths | Command search paths |
| `$SHELL` | `/data/data/com.termux/files/usr/bin/bash` | Current shell |
| `$TERMUX_VERSION` | `0.118.0` (varies) | Termux version |
| `$LANG` | `en_US.UTF-8` | Language setting |
| `$PWD` | Current directory | Present working directory |
| `$USER` | `u0_aXXX` | Current username |
| `$EDITOR` | User defined | Default text editor |
| `$HISTSIZE` | User defined | History size |
| `$HISTFILE` | `~/.bash_history` | History file location |

### 3. termux.properties Options

```properties
# ═══════════════════════════════════════════════════════════════
# COMPLETE TERMUX.PROPERTIES REFERENCE
# ═══════════════════════════════════════════════════════════════

# ─── BACK KEY BEHAVIOR ─────────────────────────────────────────
# Options: escape, back
# escape - Back key sends Escape (for vim, etc.)
# back   - Back key acts as normal Android back
back-key=escape

# ─── BELL CHARACTER ────────────────────────────────────────────
# Options: audible, visual, ignore
# audible - Beep sound
# visual  - Flash screen
# ignore  - Do nothing
bell-character=ignore

# ─── EXTRA KEYS ROW ────────────────────────────────────────────
# Basic row
extra-keys = [[ \
  {key: ESC, popup: '~'}, \
  {key: '/', popup: '_'}, \
  {key: '-', popup: '+'}, \
  {key: HOME, popup: END}, \
  {key: UP, popup: PGUP}, \
  {key: DOWN, popup: PGDN} \
]]

# Advanced row with modifiers
extra-keys = [[ \
  {key: ESC, popup: {macro: "CTRL d", display: "exit"}}, \
  {key: CTRL, popup: {macro: "CTRL c", display: "cancel"}}, \
  {key: ALT, popup: {macro: "CTRL z", display: "undo"}}, \
  {key: TAB, popup: {macro: "CTRL a", display: "all"}}, \
  {key: '/', popup: '~'}, \
  {key: '-', popup: '_'}, \
  {key: HOME, popup: END}, \
  {key: UP, popup: PGUP}, \
  {key: DOWN, popup: PGDN} \
]]

# Two rows
extra-keys = [[ \
  {key: ESC, popup: '~'}, \
  {key: '/', popup: '_'}, \
  {key: '-', popup: '+'}, \
  {key: HOME, popup: END}, \
  {key: UP, popup: PGUP}, \
  {key: DOWN, popup: PGDN} \
], [ \
  {key: TAB}, \
  {key: CTRL}, \
  {key: ALT}, \
  {key: LEFT, popup: HOME}, \
  {key: DOWN, popup: PGDN}, \
  {key: UP, popup: PGUP}, \
  {key: RIGHT, popup: END} \
]]

# ─── SHORTCUTS ─────────────────────────────────────────────────
# Create keyboard shortcuts
# Format: shortcut key = command
# Note: Requires Hacker's Keyboard or similar

# ─── URL OPENER ────────────────────────────────────────────────
# Specify script for handling URLs
# Default: ~/.termux/termux-url-opener

# ─── TERMINAL TITLE ────────────────────────────────────────────
# Automatically set terminal title
# (handled by shell usually)
```

### 4. Bash Configuration Files

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BASH CONFIGURATION FILES ORDER                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Login Shell (interactive):                                             │
│   1. /etc/profile          (system-wide)                                │
│   2. ~/.bash_profile       (user)                                       │
│   3. ~/.bash_login         (user, if no .bash_profile)                  │
│   4. ~/.profile            (user, if no .bash_login)                    │
│                                                                          │
│   Non-Login Shell (interactive):                                         │
│   1. ~/.bashrc             (user - MAIN FILE WE USE)                    │
│                                                                          │
│   Termux starts as non-login interactive shell,                          │
│   so ~/.bashrc is the primary config file.                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 COMPLETE .bashrc FILE

```bash
#!/data/data/com.termux/files/usr/bin/bash

#############################################################
#                                                           #
#              TERMUX BASH CONFIGURATION FILE               #
#                    Created by T3rmuxk1ng                  #
#                                                           #
#############################################################

# =====================================
# ENVIRONMENT VARIABLES
# =====================================

# Editor preference
export EDITOR=nano
export VISUAL=nano

# History settings
export HISTSIZE=10000
export HISTFILESIZE=20000
export HISTCONTROL=ignoreboth:erasedups
export HISTIGNORE="ls:cd:cd -:pwd:exit:date:* --help"

# Custom paths (add your script directory to PATH)
export PATH="$HOME/scripts:$HOME/bin:$PATH"

# Language
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8

# Less settings
export LESS="-R"
export LESSOPEN="|lesspipe.sh %s"

# =====================================
# SHELL OPTIONS
# =====================================

# Enable extended globbing
shopt -s extglob

# Append to history file, don't overwrite
shopt -s histappend

# Check window size after each command
shopt -s checkwinsize

# Autocorrect typos in cd
shopt -s cdspell

# =====================================
# COLOR CODES (for prompt and scripts)
# =====================================

# Regular colors
BLACK='\[\033[0;30m\]'
RED='\[\033[0;31m\]'
GREEN='\[\033[0;32m\]'
YELLOW='\[\033[0;33m\]'
BLUE='\[\033[0;34m\]'
PURPLE='\[\033[0;35m\]'
CYAN='\[\033[0;36m\]'
WHITE='\[\033[0;37m\]'

# Bold colors
BBLACK='\[\033[1;30m\]'
BRED='\[\033[1;31m\]'
BGREEN='\[\033[1;32m\]'
BYELLOW='\[\033[1;33m\]'
BBLUE='\[\033[1;34m\]'
BPURPLE='\[\033[1;35m\]'
BCYAN='\[\033[1;36m\]'
BWHITE='\[\033[1;37m\]'

# Background colors
BG_BLACK='\[\033[40m\]'
BG_RED='\[\033[41m\]'
BG_GREEN='\[\033[42m\]'
BG_YELLOW='\[\033[43m\]'
BG_BLUE='\[\033[44m\]'
BG_PURPLE='\[\033[45m\]'
BG_CYAN='\[\033[46m\]'
BG_WHITE='\[\033[47m\]'

# Reset
RESET='\[\033[0m\]'

# =====================================
# CUSTOM PROMPT (PS1)
# =====================================

# Option 1: Minimal
# PS1="${GREEN}\w${RESET} \$ "

# Option 2: Detailed
# PS1="${CYAN}\u${WHITE}@${GREEN}\h${WHITE}:${YELLOW}\w${RESET}\$ "

# Option 3: Two-line with box (RECOMMENDED)
PS1="${GREEN}┌─[${RED}\w${GREEN}]${RESET}
${GREEN}└─${CYAN}\$${RESET} "

# Option 4: With git branch (requires git-prompt)
# PS1="${GREEN}┌─[${RED}\w${GREEN}]${YELLOW}\$(__git_ps1)${RESET}
# ${GREEN}└─${CYAN}\$${RESET} "

# =====================================
# USEFUL ALIASES
# =====================================

# === PACKAGE MANAGEMENT ===
alias update='pkg update && pkg upgrade -y'
alias install='pkg install'
alias remove='pkg uninstall'
alias search='pkg search'
alias packages='pkg list-installed'
alias pclean='pkg clean && pkg autoclean'

# === NAVIGATION ===
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
alias ~='cd ~'
alias home='cd ~'
alias root='cd $PREFIX'
alias back='cd "$OLDPWD"'

# === LISTING FILES ===
alias ls='ls --color=auto'
alias ll='ls -laF'
alias la='ls -A'
alias l='ls -CF'
alias ld='ls -ld */'           # List only directories
alias lf='ls -l | grep -v "^d"' # List only files
alias lsize='ls -lhSr'          # Sort by size
alias ltime='ls -ltr'           # Sort by time
alias lhidden='ls -la | grep "^\."' # List hidden files

# === FILE OPERATIONS ===
alias cp='cp -iv'               # Interactive, verbose
alias mv='mv -iv'               # Interactive, verbose
alias rm='rm -i'                # Interactive
alias rmf='rm -rf'              # Force remove (use carefully!)
alias mkdir='mkdir -pv'         # Create parents, verbose
alias rmdir='rmdir -v'          # Verbose

# === GREP & SEARCH ===
alias grep='grep --color=auto'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias sgrep='grep -R -n -H -C 5 --exclude-dir={.git,.svn,CVS}'

# === SYSTEM ===
alias c='clear'
alias cls='clear'
alias h='history'
alias j='jobs'
alias path='echo -e ${PATH//:/\\n}'  # Print PATH one per line
alias now='date +"%T"'
alias nowdate='date +"%d-%m-%Y"'
alias week='date +%V'
alias ports='netstat -tulanp'
alias meminfo='free -h'
alias cpuinfo='cat /proc/cpuinfo'
alias diskusage='df -h'
alias pscpu='ps auxf | sort -nr -k 3 | head -10'
alias psmem='ps auxf | sort -nr -k 4 | head -10'

# === NETWORK ===
alias myip='curl -s ifconfig.me && echo'
alias myiplocal='hostname -I'
alias ping='ping -c 5'
alias fastping='ping -c 100 -i 0.2'
alias nettest='ping -c 3 google.com'

# === DEVELOPMENT ===
alias py='python'
alias python='python3'
alias pip='pip3'
alias pipi='pip install'
alias pipu='pip install --upgrade'
alias piplist='pip list'
alias pipfreeze='pip freeze'
alias g='git'
alias gs='git status'
alias ga='git add'
alias gaa='git add --all'
alias gc='git commit -m'
alias gca='git commit --amend'
alias gp='git push'
alias gpl='git pull'
alias gl='git log --oneline -10'
alias gd='git diff'
alias gb='git branch'
alias gco='git checkout'
alias gcl='git clone'

# === TERMUX SPECIFIC ===
alias ts='termux-setup-storage'
alias reload='source ~/.bashrc && echo "✓ .bashrc reloaded!"'
alias bashrc='nano ~/.bashrc'
alias bashrc-view='cat ~/.bashrc'
alias termuxconf='nano ~/.termux/termux.properties'
alias termuxreload='termux-reload-settings'
alias backup='tar -czf ~/storage/downloads/termux-backup-$(date +%Y%m%d).tar.gz ~ --exclude=storage'

# === TEXT EDITORS ===
alias n='nano'
alias v='vim'
alias vi='vim'

# === FUN & UTILITIES ===
alias weather='curl -s wttr.in'
alias weather2='curl -s v2.wttr.in'
alias cheat='curl -s cheat.sh'
alias qr='qrencode -t UTF8'
alias starwars='telnet towel.blinkenlights.nl'
alias dict='curl -s dict://dict.org/d:'
alias myinfo='echo -e "User: $(whoami)\nHome: $HOME\nShell: $SHELL\nPrefix: $PREFIX"'

# =====================================
# USEFUL FUNCTIONS
# =====================================

# Create directory and cd into it
mkcd() {
    mkdir -p "$1" && cd "$1"
}

# Extract various archive formats
extract() {
    if [ -f "$1" ]; then
        case "$1" in
            *.tar.bz2)   tar xjf "$1"     ;;
            *.tar.gz)    tar xzf "$1"     ;;
            *.tar.xz)    tar xJf "$1"     ;;
            *.bz2)       bunzip2 "$1"     ;;
            *.rar)       unrar x "$1"     ;;
            *.gz)        gunzip "$1"      ;;
            *.tar)       tar xf "$1"      ;;
            *.tbz2)      tar xjf "$1"     ;;
            *.tgz)       tar xzf "$1"     ;;
            *.zip)       unzip "$1"       ;;
            *.Z)         uncompress "$1"  ;;
            *.7z)        7z x "$1"        ;;
            *)           echo "Unknown format: $1" ;;
        esac
    else
        echo "File not found: $1"
    fi
}

# Find file by name
ff() {
    find . -type f -iname "*$1*"
}

# Find directory by name
fd() {
    find . -type d -iname "*$1*"
}

# Quick backup
backup() {
    cp "$1" "$1.backup.$(date +%Y%m%d%H%M%S)"
}

# Get file size
size() {
    du -sh "$1" 2>/dev/null || echo "File not found"
}

# Countdown timer
timer() {
    if [ -z "$1" ]; then
        echo "Usage: timer <seconds>"
        return
    fi
    local seconds=$1
    while [ $seconds -gt 0 ]; do
        echo -ne "Time remaining: $seconds seconds\r"
        sleep 1
        ((seconds--))
    done
    echo -e "\nTimer complete!"
    termux-vibrate -d 500
}

# Simple calculator
calc() {
    echo "scale=2; $*" | bc -l
}

# Quick server
serve() {
    local port="${1:-8000}"
    python -m http.server "$port"
    echo "Server running at http://localhost:$port"
}

# =====================================
# WELCOME MESSAGE
# =====================================

show_welcome() {
    local user=$(whoami)
    local host=$(hostname)
    local date=$(date '+%A, %d %B %Y')
    local time=$(date '+%H:%M:%S')
    local bash_ver=$(bash --version | head -1 | cut -d' ' -f4)
    
    echo ""
    echo "╔═══════════════════════════════════════════════════════════════╗"
    echo "║                                                               ║"
    echo "║     ████████╗███████╗██████╗ ███╗   ███╗                     ║"
    echo "║     ╚══██╔══╝██╔════╝██╔══██╗████╗ ████║                     ║"
    echo "║        ██║   █████╗  ██████╔╝██╔████╔██║                     ║"
    echo "║        ██║   ██╔══╝  ██╔══██╗██║╚██╔╝██║                     ║"
    echo "║        ██║   ███████╗██║  ██║██║ ╚═╝ ██║                     ║"
    echo "║        ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝                     ║"
    echo "║                                                               ║"
    echo "╚═══════════════════════════════════════════════════════════════╝"
    echo ""
    echo "    ┌─────────────────────────────────────────────────────────┐"
    echo "    │  Welcome to Termux - T3rmuxk1ng Edition                 │"
    echo "    ├─────────────────────────────────────────────────────────┤"
    printf "    │  User: %-48s│\n" "$user"
    printf "    │  Host: %-48s│\n" "$host"
    printf "    │  Shell: Bash %-43s│\n" "$bash_ver"
    printf "    │  Termux: v%-44s│\n" "$TERMUX_VERSION"
    printf "    │  Date: %-48s│\n" "$date"
    printf "    │  Time: %-48s│\n" "$time"
    echo "    ├─────────────────────────────────────────────────────────┤"
    echo "    │  Useful Aliases:                                        │"
    echo "    │  • update     - Update all packages                     │"
    echo "    │  • install    - Install a package                       │"
    echo "    │  • myip       - Show public IP address                  │"
    echo "    │  • weather    - Show weather forecast                   │"
    echo "    │  • bashrc     - Edit .bashrc file                       │"
    echo "    │  • reload     - Reload .bashrc                          │"
    echo "    │  • backup     - Backup Termux data                      │"
    echo "    └─────────────────────────────────────────────────────────┘"
    echo ""
}

# Show welcome message on new session
show_welcome
```

---

## 📋 COMMANDS REFERENCE

### Configuration Commands

```bash
# View Termux version
echo $TERMUX_VERSION

# View home directory
echo $HOME

# View prefix directory
echo $PREFIX

# View PATH
echo $PATH

# View current shell
echo $SHELL

# List Termux config directory
ls -la ~/.termux/

# Create Termux config directory
mkdir -p ~/.termux

# Edit termux.properties
nano ~/.termux/termux.properties

# Reload Termux settings
termux-reload-settings

# Edit .bashrc
nano ~/.bashrc

# Reload .bashrc
source ~/.bashrc

# View .bashrc
cat ~/.bashrc
```

### Environment Variable Commands

```bash
# Display all environment variables
env

# Display all environment variables (sorted)
env | sort

# Search for specific variable
env | grep -i termux

# Set temporary variable
export MY_VAR="value"

# Use variable
echo $MY_VAR

# Unset variable
unset MY_VAR

# Add directory to PATH
export PATH="$HOME/scripts:$PATH"

# Make variable permanent (add to .bashrc)
echo 'export MY_VAR="value"' >> ~/.bashrc
source ~/.bashrc
```

### Alias Commands

```bash
# List all aliases
alias

# Create temporary alias
alias ll='ls -la'

# Remove alias
unalias ll

# Make alias permanent (add to .bashrc)
echo "alias ll='ls -la'" >> ~/.bashrc
source ~/.bashrc
```

### History Commands

```bash
# View command history
history

# View last 20 commands
history 20

# Search history
history | grep "search_term"

# Clear history
history -c

# Execute command from history (e.g., command 42)
!42

# Execute last command
!!

# Execute last command with sudo
sudo !!

# Execute last command starting with 'git'
!git
```

### Termux Specific Commands

```bash
# Setup storage access
termux-setup-storage

# Reload Termux settings
termux-reload-settings

# Get Termux info
termux-info

# Termux API commands (requires Termux:API app)
termux-battery-status
termux-wifi-connectioninfo
termux-telephony-deviceinfo
termux-notification --title "Hello" --content "Test"
termux-vibrate -d 500
termux-toast "Hello World"
termux-clipboard-get
termux-clipboard-set "text to copy"
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Create Your Custom .bashrc

```bash
# Task: Create and customize your .bashrc file

# Step 1: Backup existing .bashrc (if any)
cp ~/.bashrc ~/.bashrc.backup 2>/dev/null

# Step 2: Create new .bashrc
cat > ~/.bashrc << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash

# My custom Termux configuration
export EDITOR=nano
export HISTSIZE=5000

# My favorite aliases
alias c='clear'
alias ll='ls -la'
alias update='pkg update && pkg upgrade -y'
alias myip='curl -s ifconfig.me'

# Simple prompt
PS1='\[\033[1;32m\]\w\[\033[0m\] \$ '

# Welcome message
echo "Welcome to Termux! Today is $(date '+%A, %B %d')"
EOF

# Step 3: Make it executable (optional, for scripts)
chmod +x ~/.bashrc

# Step 4: Test it
source ~/.bashrc

# Step 5: Verify aliases work
ll
myip

# Expected: Custom prompt and aliases working
```

### Exercise 2: Create Extra Keys Row

```bash
# Task: Configure extra keys row in Termux

# Step 1: Create .termux directory if not exists
mkdir -p ~/.termux

# Step 2: Create termux.properties
cat > ~/.termux/termux.properties << 'EOF'
# Back key as escape (useful for vim)
back-key=escape

# Disable bell sound
bell-character=ignore

# Extra keys row
extra-keys = [[ \
  {key: ESC}, \
  {key: '/'}, \
  {key: '-'}, \
  {key: HOME, popup: END}, \
  {key: UP, popup: PGUP}, \
  {key: DOWN, popup: PGDN}, \
  {key: LEFT, popup: HOME}, \
  {key: RIGHT, popup: END} \
]]
EOF

# Step 3: Reload Termux settings
termux-reload-settings

# Step 4: Close and reopen Termux
# Expected: Extra keys row appears above keyboard

# Step 5: Test extra keys
# Press HOME key - cursor should go to start of line
# Press END key (long press HOME) - cursor to end of line
```

### Exercise 3: Build Your Alias Collection

```bash
# Task: Create 10 custom aliases for your workflow

# Step 1: Open .bashrc
nano ~/.bashrc

# Step 2: Add these aliases (customize as needed)
# Paste at the end of file:

# === MY CUSTOM ALIASES ===
alias ..='cd ..'
alias ...='cd ../..'
alias cls='clear'
alias h='history'
alias l='ls -la'
alias p='python'
alias g='git'
alias gs='git status'
alias update='pkg update && pkg upgrade -y'

# Step 3: Save and exit (CTRL+O, Enter, CTRL+X)

# Step 4: Reload configuration
source ~/.bashrc

# Step 5: Test each alias
..
pwd        # Should be in parent directory
cd ~
l          # Should list files with details
h | tail   # Should show recent history

# Step 6: Create your own alias
# Think of a command you use often and create a shortcut
# Example: alias projects='cd ~/storage/downloads/projects'

# Step 7: Add your custom alias
echo "alias projects='cd ~/storage/downloads/projects'" >> ~/.bashrc
source ~/.bashrc

# Expected: All aliases working correctly
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: .bashrc not loading

```bash
# Cause: File not in correct location or wrong permissions

# Solution 1: Check file exists
ls -la ~/.bashrc

# Solution 2: Check file is readable
cat ~/.bashrc

# Solution 3: Manually source the file
source ~/.bashrc

# Solution 4: Check for syntax errors
bash -n ~/.bashrc

# Solution 5: Check if bash is the shell
echo $SHELL
# Should output: /data/data/com.termux/files/usr/bin/bash

# Solution 6: Create .bash_profile if needed
echo 'source ~/.bashrc' > ~/.bash_profile
```

### Problem 2: Alias not working

```bash
# Cause: Alias not saved in .bashrc or not reloaded

# Solution 1: Check if alias exists
alias | grep "alias_name"

# Solution 2: Manually create alias
alias name='command'

# Solution 3: Add to .bashrc
echo "alias name='command'" >> ~/.bashrc
source ~/.bashrc

# Solution 4: Check for conflicting alias
type alias_name
# Shows what the alias/command points to

# Solution 5: Remove conflicting alias
unalias name

# Solution 6: Check .bashrc syntax
bash -c "source ~/.bashrc"
```

### Problem 3: termux.properties not working

```bash
# Cause: File not in correct location or not reloaded

# Solution 1: Check file location
ls -la ~/.termux/termux.properties

# Solution 2: Create .termux directory if missing
mkdir -p ~/.termux

# Solution 3: Check file syntax
cat ~/.termux/termux.properties

# Solution 4: Reload settings
termux-reload-settings

# Solution 5: Restart Termux completely
# Swipe Termux from recent apps, reopen

# Solution 6: Check for typos in property names
# Common typos: extra-keys vs extra_keys
```

### Problem 4: Custom prompt broken

```bash
# Cause: Syntax error in PS1 or color codes

# Solution 1: Reset to default prompt
export PS1='\$ '

# Solution 2: Test simple prompt
export PS1='\w \$ '

# Solution 3: Check for missing escape brackets
# Correct: \[\033[0;31m\]
# Wrong: \033[0;31m (without \[ \])

# Solution 4: Use verified prompt from .bashrc template
PS1="${GREEN}\w${RESET} \$ "

# Solution 5: Check color variables are defined
echo $GREEN
echo $RESET

# Solution 6: Define missing colors
export GREEN='\[\033[0;32m\]'
export RESET='\[\033[0m\]'
```

### Problem 5: Welcome message errors

```bash
# Cause: Missing commands or syntax error in function

# Solution 1: Check for missing packages
pkg install bc coreutils

# Solution 2: Test welcome function manually
type show_welcome

# Solution 3: Check date command
date '+%A, %d %B %Y'

# Solution 4: Check whoami command
whoami

# Solution 5: Debug the function
bash -x ~/.bashrc

# Solution 6: Use simpler welcome message
echo 'echo "Welcome back, $(whoami)!"' >> ~/.bashrc
source ~/.bashrc
```

### Problem 6: History not saving

```bash
# Cause: HISTFILE not set or permissions issue

# Solution 1: Check history file
ls -la ~/.bash_history

# Solution 2: Check HISTFILE variable
echo $HISTFILE

# Solution 3: Set HISTFILE explicitly
export HISTFILE=~/.bash_history

# Solution 4: Check history settings
echo $HISTSIZE
echo $HISTFILESIZE

# Solution 5: Add history settings to .bashrc
echo 'export HISTSIZE=5000' >> ~/.bashrc
echo 'export HISTFILESIZE=10000' >> ~/.bashrc
echo 'shopt -s histappend' >> ~/.bashrc
source ~/.bashrc

# Solution 6: Create history file if missing
touch ~/.bash_history
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔧 TERMUX SETUP                  │
│   .bashrc | Aliases | Custom       │
│                                    │
│   ✓ 20+ Aliases                    │
│   ✓ Custom Prompt                  │
│   ✓ Welcome Message                │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Before/After Style**
```
┌────────────────────────────────────┐
│  BEFORE          │  AFTER          │
│  ────────────────┼──────────────── │
│  $ (boring)      │  [~/home] $     │
│  Basic setup     │  Custom prompt  │
│  Long commands   │  Short aliases  │
│  No welcome      │  Cool message   │
│                                    │
│  TRANSFORM YOUR TERMUX!            │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Focus on Aliases**
```
┌────────────────────────────────────┐
│  ⚡ 20+ USEFUL ALIASES ⚡          │
│                                    │
│  update → pkg update && upgrade    │
│  myip  → curl ifconfig.me          │
│  ll    → ls -la                    │
│                                    │
│  👉 SPEED UP YOUR WORKFLOW         │
│                                    │
│  Chapter 2 | T3rmuxk1ng            │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔧 Termux Full Course - Chapter 2: First Setup & Configuration

🔥 In this video you'll learn:
• ~/.termux/ configuration directory
• Environment variables ($PREFIX, $HOME, $PATH)
• Complete .bashrc file creation
• 20+ useful aliases for productivity
• Custom PS1 prompt design
• Professional welcome message

⏱️ Timestamps:
0:00 - Introduction
0:45 - Configuration Directory
4:00 - Environment Variables
7:30 - .bashrc File Creation
11:00 - 20+ Useful Aliases
15:00 - PS1 Prompt Customization
17:30 - Custom Welcome Message
19:30 - Complete .bashrc Overview
21:00 - Summary

📝 Key Files from this video:
• ~/.termux/termux.properties - Termux settings
• ~/.bashrc - Bash configuration

📦 Useful Aliases Covered:
• update - Update packages
• myip - Show public IP
• weather - Weather forecast
• bashrc - Edit .bashrc
• reload - Reload configuration

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxConfiguration #T3rmuxk1ng #Bashrc #TerminalCustomization #TermuxAliases #TermuxHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux, termux configuration, termux setup, termux bashrc, 
termux aliases, termux customization, termux prompt, termux ps1,
termux environment variables, termux properties, termux hindi,
termux tutorial, termux course, termux for beginners,
linux terminal customization, bash configuration, bash aliases,
bashrc tutorial, terminal setup, command line productivity,
t3rmuxk1ng, termux course hindi, android terminal,
customize termux, termux tips and tricks
```

### Hashtags

```
#Termux #TermuxConfiguration #TermuxSetup #Bashrc #TerminalCustomization 
#TermuxAliases #TermuxHindi #TermuxTutorial #LinuxOnAndroid 
#Commandline #T3rmuxk1ng #LearnTermux #BashTips #TerminalPro
```

### Timestamps for YouTube

```
0:00 - Introduction
0:45 - Configuration Directory (~/.termux/)
4:00 - Environment Variables Explained
7:30 - Creating .bashrc File
11:00 - 20+ Useful Aliases Setup
15:00 - PS1 Prompt Customization
17:30 - Custom Welcome Message
19:30 - Complete .bashrc Walkthrough
21:00 - Summary & Next Chapter
```

---

## 📚 ADDITIONAL RESOURCES

### Configuration Templates

| Template | Description |
|----------|-------------|
| Minimal .bashrc | Basic configuration for beginners |
| Developer .bashrc | Extended config with git, python aliases |
| Hacker .bashrc | Security tools focused configuration |

### Useful Links

| Resource | Link |
|----------|------|
| Bash Manual | `man bash` in Termux |
| Termux Wiki | https://wiki.termux.com/ |
| Termux Styling | Termux:Styling app on F-Droid |
| ASCII Art Generator | https://patorjk.com/software/taag/ |

### Color Code Reference

```bash
# Regular Colors
Black        \033[0;30m
Red          \033[0;31m
Green        \033[0;32m
Yellow       \033[0;33m
Blue         \033[0;34m
Purple       \033[0;35m
Cyan         \033[0;36m
White        \033[0;37m

# Bold Colors
Black        \033[1;30m
Red          \033[1;31m
Green        \033[1;32m
Yellow       \033[1;33m
Blue         \033[1;34m
Purple       \033[1;35m
Cyan         \033[1;36m
White        \033[1;37m

# Reset
Reset        \033[0m
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 3, verify:

- [ ] ~/.termux/ directory created
- [ ] termux.properties configured with extra keys
- [ ] termux-reload-settings executed
- [ ] .bashrc file created in home directory
- [ ] At least 10 aliases added to .bashrc
- [ ] Custom PS1 prompt configured
- [ ] Welcome message displays on startup
- [ ] `source ~/.bashrc` command works
- [ ] `reload` alias works
- [ ] `bashrc` alias opens editor

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 3: Linux Basics - Part 1**

- Understanding file system hierarchy
- Navigation commands (cd, pwd, ls)
- File and directory operations
- Understanding permissions (chmod, chown)
- File viewing commands (cat, less, head, tail)
- Text searching with grep

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
