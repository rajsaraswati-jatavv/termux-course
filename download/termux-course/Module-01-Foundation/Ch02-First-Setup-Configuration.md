# Chapter 2: First Setup & Configuration

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║   ████████╗███████╗██████╗ ███╗   ███╗██╗███╗   ██╗ ██████╗ ██████╗ ███████╗  ║
║   ╚══██╔══╝██╔════╝██╔══██╗████╗ ████║██║████╗  ██║██╔════╝██╔═══██╗██╔════╝  ║
║       ██║   █████╗  ██████╔╝██╔████╔██║██║██╔██╗ ██║██║     ██║   ██║███████╗  ║
║       ██║   ██╔══╝  ██╔══██╗██║╚██╔╝██║██║██║╚██╗██║██║     ██║   ██║╚════██║  ║
║       ██║   ███████╗██║  ██║██║ ╚═╝ ██║██║██║ ╚████║╚██████╗╚██████╔╝███████║  ║
║       ╚═╝   ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝╚═╝  ╚═══╝ ╚═════╝ ╚═════╝ ╚══════╝  ║
║                                                                               ║
║   ███████╗ █████╗ ██╗     ███████╗███████╗███████╗██████╗ ██████╗ ██████╗ ██╗  ║
║   ██╔════╝██╔══██╗██║     ██╔════╝██╔════╝██╔════╝██╔══██╗██╔══██╗██╔══██╗██║  ║
║   █████╗  ███████║██║     █████╗  ███████╗█████╗  ██████╔╝██████╔╝██║  ██║██║  ║
║   ██╔══╝  ██╔══██║██║     ██╔══╝  ╚════██║██╔══╝  ██╔══██╗██╔══██╗██║  ██║██║  ║
║   ██║     ██║  ██║███████╗███████╗███████║███████╗██║  ██║██║  ██║██████╔╝██║  ║
║   ╚═╝     ╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═════╝ ╚═╝  ║
║                                                                               ║
║                    🔧 SETUP & CUSTOMIZATION 🔧                                ║
║                         By T3rmuxk1ng                                         ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 1 - Foundation  
> **Chapter:** 2 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐ Beginner  
> **Prerequisites:** Chapter 1 (Termux Installation)  

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

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

Test your understanding of Termux configuration with these 15 questions!

---

### Question 1: What is the purpose of the .bashrc file?

<details>
<summary>🔍 Click to see options</summary>

A) System configuration file  
B) Shell configuration that runs on each terminal start  
C) Network configuration file  
D) Package manager settings  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) Shell configuration that runs on each terminal start**

**Explanation:** The `.bashrc` file is a shell script that Bash runs whenever it is started interactively. It's used to set up your shell environment with aliases, functions, environment variables, and custom prompts. In Termux, it's located at `~/.bashrc` and runs every time you open the app.

</details>

---

### Question 2: Where is Termux's main configuration file located?

<details>
<summary>🔍 Click to see options</summary>

A) `/etc/termux/`  
B) `~/.termux/termux.properties`  
C) `/system/termux/`  
D) `~/.config/termux/`  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) `~/.termux/termux.properties`**

**Explanation:** Termux's application-level settings are stored in `~/.termux/termux.properties`. This file controls things like back key behavior, bell character handling, extra keys row configuration, and other Termux-specific settings. After editing, you must run `termux-reload-settings` or restart Termux.

</details>

---

### Question 3: What command reloads Termux settings after editing termux.properties?

<details>
<summary>🔍 Click to see options</summary>

A) `source ~/.termux/termux.properties`  
B) `termux-reload-settings`  
C) `reload termux`  
D) `restart-termux`  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) `termux-reload-settings`**

**Explanation:** The `termux-reload-settings` command tells Termux to re-read the `termux.properties` file and apply changes immediately. Without this, you would need to completely close and reopen Termux for changes to take effect.

</details>

---

### Question 4: What does an alias do in Bash?

<details>
<summary>🔍 Click to see options</summary>

A) Creates a shortcut for a long command  
B) Renames a file  
C) Creates a symbolic link  
D) Hides a file  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: A) Creates a shortcut for a long command**

**Explanation:** An alias is a substitute for a command or set of commands. For example, `alias update='pkg update && pkg upgrade -y'` lets you type just `update` instead of the full command. Aliases make frequently used commands shorter and easier to remember.

</details>

---

### Question 5: Which command makes an alias permanent?

<details>
<summary>🔍 Click to see options</summary>

A) `alias --save`  
B) Adding it to .bashrc  
C) `export alias`  
D) Aliases are permanent by default  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) Adding it to .bashrc**

**Explanation:** Aliases created on the command line are temporary and disappear when you close Termux. To make them permanent, add the alias definition to your `~/.bashrc` file. The .bashrc runs each time Termux starts, recreating your aliases.

</details>

---

### Question 6: What does $PATH environment variable contain?

<details>
<summary>🔍 Click to see options</summary>

A) Current directory path  
B) List of directories to search for executables  
C) Path to home directory  
D) Path to configuration files  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) List of directories to search for executables**

**Explanation:** `$PATH` contains a colon-separated list of directories that the shell searches when you type a command. When you run `python`, the shell looks in each directory in PATH to find the python executable. You can add custom directories to run your own scripts from anywhere.

</details>

---

### Question 7: How do you add a custom scripts directory to PATH?

<details>
<summary>🔍 Click to see options</summary>

A) `add-path ~/scripts`  
B) `export PATH="$HOME/scripts:$PATH"`  
C) `set PATH + ~/scripts`  
D) `path --add ~/scripts`  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) `export PATH="$HOME/scripts:$PATH"`**

**Explanation:** To add a directory to PATH, use the export command. The syntax `$HOME/scripts:$PATH` prepends your scripts directory to the existing PATH. Put this in .bashrc to make it permanent. The shell will then find executables in ~/scripts.

</details>

---

### Question 8: What is PS1 in Bash?

<details>
<summary>🔍 Click to see options</summary>

A) First process ID  
B) Prompt string variable that defines command prompt appearance  
C) Primary shell  
D) Process status 1  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) Prompt string variable that defines command prompt appearance**

**Explanation:** PS1 is the primary prompt string variable. It defines what your command prompt looks like. You can customize it with special characters like `\w` (current directory), `\u` (username), colors, and more. Example: `PS1="\w $ "` shows current directory followed by $.

</details>

---

### Question 9: Which file stores command history in Bash?

<details>
<summary>🔍 Click to see options</summary>

A) `.history`  
B) `.bash_history`  
C) `.command_history`  
D) `.shell_history`  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) `.bash_history`**

**Explanation:** Bash stores your command history in `~/.bash_history`. You can control history size with `HISTSIZE` and `HISTFILESIZE` variables in .bashrc. Use `history` command to view past commands, and `!!` to repeat the last command.

</details>

---

### Question 10: What does HISTCONTROL=ignoreboth do?

<details>
<summary>🔍 Click to see options</summary>

A) Ignores all history  
B) Ignores duplicates and commands starting with space  
C) Ignores errors in history  
D) Clears history on exit  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) Ignores duplicates and commands starting with space**

**Explanation:** `ignoreboth` is a shorthand for `ignorespace:ignoredups`. It means:
- `ignorespace`: Commands starting with a space won't be saved to history
- `ignoredups`: Duplicate consecutive commands won't be saved again
This keeps your history cleaner and more useful.

</details>

---

### Question 11: What is the difference between a function and an alias?

<details>
<summary>🔍 Click to see options</summary>

A) No difference  
B) Functions can take arguments, aliases cannot  
C) Aliases are faster  
D) Functions are only for scripts  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) Functions can take arguments, aliases cannot**

**Explanation:** While both create shortcuts, functions are more powerful:
- Functions can accept and process arguments ($1, $2, etc.)
- Functions can contain multiple commands and logic
- Aliases are simple text substitutions
Example function: `mkcd() { mkdir -p "$1" && cd "$1"; }` - creates and enters a directory.

</details>

---

### Question 12: Which environment variable sets your default editor?

<details>
<summary>🔍 Click to see options</summary>

A) $DEFAULT_EDITOR  
B) $EDITOR  
C) $TEXT_EDITOR  
D) $EDIT  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) $EDITOR**

**Explanation:** The `EDITOR` environment variable specifies your preferred text editor. Many programs (like git, visudo, crontab) use this variable to open an editor. Set it in .bashrc: `export EDITOR=nano` or `export EDITOR=vim`.

</details>

---

### Question 13: What does `source ~/.bashrc` do?

<details>
<summary>🔍 Click to see options</summary>

A) Opens .bashrc in editor  
B) Re-runs .bashrc in current shell  
C) Backs up .bashrc  
D) Validates .bashrc syntax  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) Re-runs .bashrc in current shell**

**Explanation:** The `source` command (also written as `.`) reads and executes commands from a file in the current shell. After editing .bashrc, `source ~/.bashrc` applies your changes immediately without needing to restart Termux. It's like running all the commands in that file.

</details>

---

### Question 14: What is the correct syntax for an extra keys row in termux.properties?

<details>
<summary>🔍 Click to see options</summary>

A) `extra-keys = ESC, CTRL, ALT`  
B) `extra-keys = [[ {key: ESC}, {key: CTRL} ]]`  
C) `keys-extra = [ESC, CTRL, ALT]`  
D) `additional-keys = ESC CTRL ALT`  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) `extra-keys = [[ {key: ESC}, {key: CTRL} ]]`**

**Explanation:** The extra-keys format uses JSON-like syntax with arrays and objects. Each key is defined as `{key: NAME}` or with popups as `{key: NAME, popup: ACTION}`. Double brackets `[[ ]]` define rows. This adds a customizable row of keys above your keyboard.

</details>

---

### Question 15: How do you make a welcome message appear when Termux starts?

<details>
<summary>🔍 Click to see options</summary>

A) Edit /etc/motd  
B) Add echo commands or a function to .bashrc  
C) Configure in Termux settings  
D) Create a .welcome file  

</details>

<details>
<summary>✅ Click to see answer</summary>

**Answer: B) Add echo commands or a function to .bashrc**

**Explanation:** To show a custom welcome message, add echo statements or a function to your .bashrc:
```bash
echo "Welcome to Termux!"
echo "Today is $(date)"
```
Or create a function that displays system info and call it at the end of .bashrc.

</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

Prepare for technical interviews with these configuration-related questions!

---

### Q1: Explain the difference between .bashrc, .bash_profile, and .profile.

<details>
<summary>📖 View Answer</summary>

**Answer:**

| File | When it runs | Purpose |
|------|--------------|---------|
| `.bash_profile` | Login shell | Set up environment once per session |
| `.bashrc` | Every interactive shell | Aliases, functions, prompts |
| `.profile` | Login shell (if no .bash_profile) | Generic POSIX settings |

**In Termux:**
- Termux starts as an interactive non-login shell
- Only `.bashrc` runs automatically
- You can source `.bash_profile` from `.bashrc` if needed

**Best Practice:**
```bash
# In .bash_profile
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```

**Follow-up:** Why might you want settings in .bash_profile instead of .bashrc?
**Answer:** For environment variables that should only be set once (like PATH modifications that accumulate), or for commands that only need to run at login (like starting SSH agent).

</details>

---

### Q2: How would you organize a complex .bashrc file for maintainability?

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Modular Organization:**

```bash
# ~/.bashrc - Main configuration file

# Source separate configuration files
for file in ~/.config/bash/{aliases,functions,env,prompt}; do
    [ -f "$file" ] && source "$file"
done

# Or source individual files
if [ -f ~/.bash_aliases ]; then
    source ~/.bash_aliases
fi

if [ -f ~/.bash_functions ]; then
    source ~/.bash_functions
fi

if [ -f ~/.bash_env ]; then
    source ~/.bash_env
fi
```

**Directory Structure:**
```
~/.config/bash/
├── aliases      # All alias definitions
├── functions    # All function definitions
├── env          # Environment variables
├── prompt       # PS1 customization
└── completions  # Custom completions
```

**Benefits:**
1. Easier to find specific configurations
2. Can version control separate files
3. Easier to share configurations
4. Less conflicts when editing

**Follow-up:** How would you handle machine-specific configurations?
**Answer:**
```bash
# Source local machine-specific config
if [ -f ~/.bashrc.local ]; then
    source ~/.bashrc.local
fi
```

</details>

---

### Q3: What security considerations should be taken with shell configuration?

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Security Considerations:**

1. **File Permissions:**
```bash
chmod 600 ~/.bashrc        # Only owner can read/write
chmod 700 ~/scripts/       # Only owner can access
```

2. **Avoid Sensitive Data:**
```bash
# DON'T put passwords in .bashrc
# BAD: export DB_PASSWORD="secret123"

# BETTER: Use environment or prompt
export DB_PASSWORD=$(cat ~/.secure/db_pass)
# Or use SSH keys, credential helpers
```

3. **PATH Security:**
```bash
# Don't add world-writable directories to PATH
# Check permissions before adding
[ -d "$HOME/bin" ] && export PATH="$HOME/bin:$PATH"
```

4. **Sourcing Files Safely:**
```bash
# Check file exists and is owned by you
source_if_safe() {
    local file=$1
    if [ -f "$file" ] && [ -O "$file" ]; then
        source "$file"
    fi
}
```

5. **History Security:**
```bash
# Don't save sensitive commands
export HISTCONTROL=ignorespace
# Type sensitive commands with leading space
```

**Follow-up:** What are the risks of sourcing untrusted files?
**Answer:** Arbitrary code execution - the sourced file runs with your permissions and could do anything you can do: delete files, steal data, install backdoors, etc.

</details>

---

### Q4: Explain how you would debug a problematic .bashrc.

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Debugging Steps:**

1. **Start with default config:**
```bash
mv ~/.bashrc ~/.bashrc.broken
# Termux will use default settings
```

2. **Run with error output:**
```bash
bash -x ~/.bashrc 2>&1 | less
# Shows each command as it executes
```

3. **Check syntax:**
```bash
bash -n ~/.bashrc
# Checks for syntax errors without running
```

4. **Add debug output:**
```bash
# In .bashrc
set -x  # Print commands and arguments
echo "Reached line $LINENO"
set +x  # Turn off debug
```

5. **Source incrementally:**
```bash
# Comment out everything
# Uncomment sections one at a time
# Find which section causes the issue
```

6. **Common issues:**
- Missing quotes around variables
- Incorrect path separators (`:` vs ` `)
- Unmatched quotes or brackets
- Circular sourcing
- Command not available at startup

**Follow-up:** What if .bashrc prevents Termux from starting?
**Answer:** Use a rescue method:
1. Long-press Termux icon → Properties → Clear Data (last resort)
2. Use `adb shell` if USB debugging enabled
3. Use file manager to delete/rename .bashrc

</details>

---

### Q5: How would you set up a consistent development environment across multiple devices?

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Git-based Configuration Management:**

```bash
# Create config repository
mkdir -p ~/dotfiles
cd ~/dotfiles
git init

# Move and link configuration files
mv ~/.bashrc ~/dotfiles/bashrc
mv ~/.termux/termux.properties ~/dotfiles/termux.properties
ln -s ~/dotfiles/bashrc ~/.bashrc
ln -s ~/dotfiles/termux.properties ~/.termux/termux.properties

# Create setup script
cat > ~/dotfiles/setup.sh << 'EOF'
#!/bin/bash
# Link all dotfiles
for file in bashrc bash_aliases bash_functions; do
    ln -sf ~/dotfiles/$file ~/.$file
done
ln -sf ~/dotfiles/termux.properties ~/.termux/termux.properties
termux-reload-settings
source ~/.bashrc
EOF

# Push to GitHub
git remote add origin https://github.com/user/dotfiles
git push -u origin main
```

**On new device:**
```bash
git clone https://github.com/user/dotfiles ~/dotfiles
cd ~/dotfiles && ./setup.sh
```

**Follow-up:** How do you handle device-specific configurations?
**Answer:** Use hostname or create local override files:
```bash
if [ -f ~/.bashrc.$(hostname) ]; then
    source ~/.bashrc.$(hostname)
fi
```

</details>

---

### Q6: What are shell options (shopt) and how are they useful?

<details>
<summary>📖 View Answer</summary>

**Answer:**

**shopt (shell options) controls optional shell behavior:**

**Useful Options:**

```bash
# Autocorrect typos in cd
shopt -s cdspell
# cd ~/Documets → ~/Documents

# Enable extended globbing
shopt -s extglob
# ls !(*.txt) - list all except .txt files

# Append to history, don't overwrite
shopt -s histappend

# Check window size after each command
shopt -s checkwinsize

# Auto-correct directory names in path
shopt -s dirspell

# ** matches all files and directories
shopt -s globstar
# ls **/*.py - all Python files recursively
```

**View all options:**
```bash
shopt           # Show all options
shopt -p        # Show in reusable format
shopt -s        # Show enabled options
shopt -u        # Show disabled options
```

**Follow-up:** What does `shopt -s extglob` enable?
**Answer:** Extended pattern matching with these patterns:
- `?(pattern)` - Zero or one occurrence
- `*(pattern)` - Zero or more occurrences
- `+(pattern)` - One or more occurrences
- `@(pattern)` - Exactly one occurrence
- `!(pattern)` - Anything except pattern

</details>

---

### Q7: How would you create a custom command completion in Bash?

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Basic Completion Setup:**

```bash
# Complete for custom command
_mycommand_completion() {
    local cur words
    cur="${COMP_WORDS[COMP_CWORD]}"
    words="start stop restart status config help"
    
    COMPREPLY=($(compgen -W "${words}" -- "${cur}"))
    return 0
}

# Register the completion
complete -F _mycommand_completion mycommand
```

**Advanced Example with Files:**

```bash
# Completion that suggests files and keywords
_script_completion() {
    local cur prev words
    _init_completion || return
    
    case $prev in
        -f|--file)
            _filedir
            return
            ;;
        -d|--dir)
            _filedir -d
            return
            ;;
    esac
    
    if [[ $cur == -* ]]; then
        COMPREPLY=($(compgen -W "--file --dir --help --version" -- "$cur"))
    else
        COMPREPLY=($(compgen -W "run test build deploy" -- "$cur"))
    fi
}

complete -F _script_completion myscript
```

**Follow-up:** How do you use existing completion functions?
**Answer:** Source the completion file first:
```bash
source /usr/share/bash-completion/bash_completion
source /usr/share/bash-completion/completions/git
```

</details>

---

### Q8: Explain environment variable precedence and scope.

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Variable Types and Scope:**

1. **Shell Variables (local):**
```bash
myvar="value"        # Only in current shell
```

2. **Environment Variables (exported):**
```bash
export MYVAR="value" # Available to child processes
```

3. **Precedence Order:**
```
System defaults → /etc/profile → ~/.bash_profile → ~/.bashrc → command line
```

**Export Behavior:**
```bash
# Not exported - child process can't see
VAR="hello"
bash -c 'echo $VAR'  # Output: (empty)

# Exported - child inherits
export VAR="hello"
bash -c 'echo $VAR'  # Output: hello
```

**Important Environment Variables:**
| Variable | Purpose |
|----------|---------|
| PATH | Executable search paths |
| HOME | User's home directory |
| USER | Current username |
| SHELL | Current shell |
| PWD | Current directory |
| EDITOR | Default text editor |
| LANG | Language/locale |

**Follow-up:** How do you make variables persistent across sessions?
**Answer:** Add export statements to .bashrc for non-login shells, or .bash_profile for login shells.

</details>

---

### Q9: How would you implement a custom prompt that shows git branch?

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Simple Git Prompt:**

```bash
# Function to get git branch
parse_git_branch() {
    git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# Use in PS1
export PS1="\u@\h \w\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
```

**Advanced Git Prompt with Status:**

```bash
# Colors
RED='\[\033[0;31m\]'
GREEN='\[\033[0;32m\]'
YELLOW='\[\033[0;33m\]'
BLUE='\[\033[0;34m\]'
RESET='\[\033[0m\]'

# Git status function
git_status() {
    local branch status
    
    if ! branch=$(git symbolic-ref --short HEAD 2>/dev/null); then
        return
    fi
    
    # Check for changes
    if git diff --quiet 2>/dev/null; then
        status="${GREEN}✓"
    else
        status="${RED}✗"
    fi
    
    # Check for staged changes
    if ! git diff --cached --quiet 2>/dev/null; then
        status="${YELLOW}●${status}"
    fi
    
    echo " (${branch})${status}${RESET}"
}

# Set prompt
export PS1="${BLUE}\w${RESET}\$(git_status) $ "
```

**Using git-prompt.sh (if available):**
```bash
source /usr/share/git/completion/git-prompt.sh
export PS1='\w$(__git_ps1 " (%s)") $ '
```

**Follow-up:** How would you optimize for performance in large repos?
**Answer:** Use `__git_ps1` with `GIT_PS1_SHOWDIRTYSTATE=false` for faster response, or use async prompt updates.

</details>

---

### Q10: How do Termux configuration files differ from standard Linux distributions?

<details>
<summary>📖 View Answer</summary>

**Answer:**

**Key Differences:**

| Aspect | Standard Linux | Termux |
|--------|---------------|--------|
| Home location | `/home/user/` | `/data/data/com.termux/files/home/` |
| Config location | `/etc/` or `~/.config/` | `~/.termux/` |
| Shell path | `/bin/bash` | `$PREFIX/bin/bash` |
| Shebang | `#!/bin/bash` | `#!/data/data/com.termux/files/usr/bin/bash` |
| Root user | Yes | No (unless device rooted) |

**Termux-Specific Files:**
```
~/.termux/
├── termux.properties  # App settings (unique to Termux)
├── colors.properties  # Color scheme
└── font.ttf          # Custom font
```

**termux.properties Options:**
```bash
# Termux-specific settings
back-key=escape
bell-character=ignore
extra-keys = [[ ... ]]
# These don't exist in standard Linux
```

**Standard Linux Files Not Used in Termux:**
- `/etc/passwd` (uses Android's user system)
- `/etc/shadow` (no password authentication)
- `/etc/fstab` (no mount control)

**Follow-up:** How do you write portable scripts?
**Answer:** Use environment variables instead of hardcoded paths:
```bash
#!/usr/bin/env bash  # Portable shebang
# Or in Termux-specific:
#!/data/data/com.termux/files/usr/bin/bash

# Use variables
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
```

</details>

---

## 🔥 REAL-WORLD SCENARIOS

Practical scenarios you'll encounter when configuring Termux!

---

### Scenario 1: The "My Aliases Disappeared" Mystery

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                          😰 SCENARIO: LOST ALIASES                           │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  SITUATION: User created aliases yesterday but they're gone today            │
│  They ran: alias update='pkg update && pkg upgrade -y'                       │
│                                                                              │
│  USER CONTEXT:                                                               │
│  - Created aliases on command line                                           │
│  - Didn't add to any file                                                    │
│  - Closed and reopened Termux                                                │
│                                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  🛠️ DIAGNOSIS & SOLUTION:                                                    │
│                                                                              │
│  Step 1: Understand the Problem                                              │
│  ─────────────────────────────                                               │
│  Command-line aliases are TEMPORARY                                          │
│  They only exist in current shell session                                    │
│  Closing Termux = starting new shell = aliases gone                          │
│                                                                              │
│  Step 2: Make Aliases Permanent                                              │
│  ─────────────────────────────                                               │
│  $ nano ~/.bashrc                                                            │
│                                                                              │
│  # Add at the end:                                                           │
│  # === MY ALIASES ===                                                        │
│  alias update='pkg update && pkg upgrade -y'                                 │
│  alias install='pkg install'                                                 │
│  alias ll='ls -la'                                                           │
│  alias c='clear'                                                             │
│                                                                              │
│  Step 3: Apply Changes                                                       │
│  ─────────────────────────────                                               │
│  $ source ~/.bashrc                                                          │
│                                                                              │
│  Step 4: Verify                                                              │
│  ─────────────────────────────                                               │
│  $ alias                                                                     │
│  # Should show your aliases                                                  │
│                                                                              │
│  $ update                                                                    │
│  # Should work now!                                                          │
│                                                                              │
│  ✅ RESULT: Aliases now permanent!                                           │
│                                                                              │
│  💡 PREVENTION TIP: Always add aliases to .bashrc immediately!               │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

### Scenario 2: Creating a Productivity-Optimized Environment

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                   ⚡ SCENARIO: PRODUCTIVITY SETUP                            │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  SITUATION: Developer wants maximum productivity on mobile                   │
│  Goal: Quick navigation, smart aliases, informative prompt                   │
│                                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  🛠️ COMPLETE PRODUCTIVITY CONFIG:                                            │
│                                                                              │
│  # === CREATE CONFIGURATION ===                                              │
│  cat >> ~/.bashrc << 'EOF'                                                   │
│                                                                              │
│  # ══════════════════════════════════════════════════════                   │
│  # PRODUCTIVITY CONFIGURATION                                                │
│  # ══════════════════════════════════════════════════════                   │
│                                                                              │
│  # === SMART NAVIGATION ===                                                  │
│  alias ..='cd ..'                                                            │
│  alias ...='cd ../..'                                                        │
│  alias ....='cd ../../..'                                                    │
│  alias ~='cd ~'                                                              │
│  alias projects='cd ~/projects'                                              │
│  alias downloads='cd ~/storage/downloads'                                    │
│  alias back='cd "$OLDPWD"'                                                   │
│                                                                              │
│  # === QUICK ACTIONS ===                                                     │
│  alias update='pkg update && pkg upgrade -y'                                 │
│  alias install='pkg install'                                                 │
│  alias search='pkg search'                                                   │
│  alias rmb='rm -rf ~/.bash_history && history -c'  # Clear history           │
│                                                                               │
│  # === GIT SHORTCUTS ===                                                     │
│  alias gs='git status'                                                       │
│  alias ga='git add .'                                                        │
│  alias gc='git commit -m'                                                    │
│  alias gp='git push'                                                         │
│  alias gl='git log --oneline -10'                                            │
│  alias gd='git diff'                                                         │
│  alias gb='git branch'                                                       │
│  alias gco='git checkout'                                                    │
│                                                                              │
│  # === DEVELOPMENT HELPERS ===                                               │
│  alias py='python'                                                           │
│  alias pipi='pip install'                                                    │
│  alias venv='python -m venv venv && source venv/bin/activate'               │
│  alias serve='python -m http.server 8000'                                    │
│  alias json='python -m json.tool'                                            │
│                                                                              │
│  # === USEFUL FUNCTIONS ===                                                  │
│  # Create and enter directory                                                │
│  mkcd() { mkdir -p "$1" && cd "$1"; }                                        │
│                                                                              │
│  # Quick backup                                                              │
│  backup() { cp "$1" "$1.bak.$(date +%Y%m%d%H%M%S)"; }                        │
│                                                                              │
│  # Find file by name                                                         │
│  ff() { find . -type f -iname "*$1*" 2>/dev/null; }                          │
│                                                                              │
│  # Count files in directory                                                  │
│  count() { ls -1 | wc -l; }                                                  │
│                                                                              │
│  # Extract archives                                                          │
│  extract() {                                                                 │
│      case "$1" in                                                            │
│          *.tar.gz) tar xzf "$1" ;;                                           │
│          *.zip) unzip "$1" ;;                                                │
│          *) echo "Unknown format" ;;                                         │
│      esac                                                                    │
│  }                                                                           │
│                                                                              │
│  # === INFORMATIVE PROMPT ===                                                │
│  parse_git_branch() {                                                        │
│      git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'       │
│  }                                                                           │
│                                                                              │
│  GREEN='\[\033[0;32m\]'                                                      │
│  BLUE='\[\033[0;34m\]'                                                       │
│  YELLOW='\[\033[0;33m\]'                                                     │
│  RESET='\[\033[0m\]'                                                         │
│                                                                              │
│  PS1="${GREEN}\u${RESET}:${BLUE}\w${YELLOW}\$(parse_git_branch)${RESET}\$ "  │
│                                                                              │
│  # === WELCOME MESSAGE ===                                                   │
│  echo ""                                                                     │
│  echo "👋 Welcome back, $(whoami)!"                                          │
│  echo "📅 $(date '+%A, %B %d, %Y')"                                          │
│  echo "📦 $(pkg list-installed | wc -l) packages installed"                  │
│  echo ""                                                                     │
│  EOF                                                                         │
│                                                                              │
│  $ source ~/.bashrc                                                          │
│                                                                              │
│  ✅ RESULT: Fully optimized productivity environment!                        │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

### Scenario 3: Setting Up Extra Keys Row for Coding

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                   ⌨️ SCENARIO: CODING KEYBOARD SETUP                         │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  SITUATION: Developer needs quick access to coding keys                      │
│  Problem: On-screen keyboard lacks ESC, CTRL, TAB, brackets                  │
│                                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  🛠️ CONFIGURATION:                                                           │
│                                                                              │
│  $ mkdir -p ~/.termux                                                        │
│  $ nano ~/.termux/termux.properties                                          │
│                                                                              │
│  # Add this configuration:                                                   │
│  extra-keys = [[                                                            │
│    {key: ESC, popup: {macro: "CTRL d", display: "exit"}},                   │
│    {key: CTRL, popup: {macro: "CTRL c", display: "cancel"}},                │
│    {key: ALT, popup: {macro: "CTRL z", display: "undo"}},                   │
│    {key: TAB, popup: {macro: "CTRL a", display: "all"}},                    │
│    {key: '/', popup: '~'},                                                  │
│    {key: '-', popup: '_'},                                                  │
│    {key: HOME, popup: END},                                                 │
│    {key: UP, popup: PGUP},                                                  │
│    {key: DOWN, popup: PGDN}                                                 │
│  ], [                                                                        │
│    {key: KEYBOARD, popup: {macro: "KEYBOARD 5", display: "5"}},             │
│    {key: {macro: "ALT ENTER", display: "search"}, popup: "ENTER"},          │
│    {key: DEL, popup: BACKSPACE},                                            │
│    {key: LEFT, popup: HOME},                                                │
│    {key: RIGHT, popup: END}                                                 │
│  ]]                                                                         │
│                                                                              │
│  # Alternative: Developer-focused layout                                     │
│  extra-keys = [[                                                            │
│    {key: ESC}, {key: '/'}, {key: '-'}, {key: HOME}, {key: UP}, {key: END},  │
│    {key: TAB}, {key: CTRL}, {key: ALT}, {key: LEFT}, {key: DOWN},           │
│    {key: RIGHT}                                                             │
│  ], [                                                                        │
│    {key: '('}, {key: ')'}, {key: '{'}, {key: '}'}, {key: '['}, {key: ']'},  │
│    {key: '"'}, {key: "'"}, {key: '`'}, {key: ';'}, {key: ':'}, {key: '|'}   │
│  ]]                                                                         │
│                                                                              │
│  $ termux-reload-settings                                                    │
│                                                                              │
│  ✅ RESULT: Extra keys row now visible above keyboard!                       │
│                                                                              │
│  💡 TIP: Long-press keys for popup alternatives!                             │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

### Scenario 4: Creating Project-Specific Configurations

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                   📁 SCENARIO: PROJECT CONFIGS                               │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  SITUATION: Developer works on multiple projects with different needs        │
│  Goal: Auto-load project-specific aliases and environment when entering      │
│                                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  🛠️ SOLUTION: AUTOMATIC PROJECT CONFIG                                       │
│                                                                              │
│  # Create project structure                                                  │
│  mkdir -p ~/projects/{webapp,api,scripts}                                    │
│                                                                              │
│  # Add project-specific config files                                         │
│  cat > ~/projects/webapp/.envrc << 'EOF'                                     │
│  # Webapp project settings                                                   │
│  export PROJECT_NAME="WebApp"                                                │
│  alias run='python -m http.server 8000'                                      │
│  alias test='python -m pytest tests/'                                        │
│  alias build='npm run build'                                                 │
│  alias dev='npm run dev'                                                     │
│  echo "🌐 WebApp project loaded"                                             │
│  EOF                                                                         │
│                                                                              │
│  cat > ~/projects/api/.envrc << 'EOF'                                        │
│  # API project settings                                                      │
│  export PROJECT_NAME="API"                                                   │
│  export API_URL="http://localhost:3000"                                      │
│  alias run='node server.js'                                                  │
│  alias test='npm test'                                                       │
│  alias migrate='node migrate.js'                                             │
│  echo "🔌 API project loaded"                                                │
│  EOF                                                                         │
│                                                                              │
│  # Add auto-load function to .bashrc                                         │
│  cat >> ~/.bashrc << 'EOF'                                                   │
│  # Auto-load project config when entering directory                          │
│  cd() {                                                                      │
│      builtin cd "$@"                                                         │
│      if [ -f .envrc ]; then                                                  │
│          source .envrc                                                       │
│      fi                                                                      │
│  }                                                                           │
│  EOF                                                                         │
│                                                                              │
│  # Test it!                                                                  │
│  $ source ~/.bashrc                                                          │
│  $ cd ~/projects/webapp                                                      │
│  🌐 WebApp project loaded                                                    │
│  $ run      # Runs python -m http.server 8000                                │
│  $ cd ~/projects/api                                                         │
│  🔌 API project loaded                                                       │
│  $ run      # Runs node server.js                                            │
│                                                                              │
│  ✅ RESULT: Project-specific configs auto-load on cd!                        │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

### Scenario 5: Troubleshooting a Broken Configuration

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                   🔧 SCENARIO: BROKEN BASHRC                                 │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  SITUATION: User added bad code to .bashrc, now Termux won't start properly  │
│  Symptoms: Error messages, commands not working, weird behavior              │
│                                                                              │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  🛠️ RECOVERY PROCEDURE:                                                      │
│                                                                              │
│  Step 1: Open Termux anyway (even with errors)                               │
│  ─────────────────────────────                                               │
│  Termux will try to run, errors will show but you get a prompt               │
│                                                                              │
│  Step 2: Find the error                                                      │
│  ─────────────────────────────                                               │
│  $ bash -x ~/.bashrc 2>&1 | head -50                                        │
│  # This shows each line as it executes and stops at the error                │
│                                                                              │
│  Step 3: Check syntax                                                        │
│  ─────────────────────────────                                               │
│  $ bash -n ~/.bashrc                                                         │
│  # Shows syntax errors without running                                       │
│                                                                              │
│  Step 4: Backup and fix                                                      │
│  ─────────────────────────────                                               │
│  $ cp ~/.bashrc ~/.bashrc.broken                                             │
│  $ nano ~/.bashrc                                                            │
│  # Comment out or remove the problematic lines                               │
│                                                                              │
│  Step 5: Test before applying                                                │
│  ─────────────────────────────                                               │
│  $ bash --norc  # Start shell without loading .bashrc                        │
│  $ source ~/.bashrc  # Test your fixed version                               │
│                                                                              │
│  Step 6: If completely broken                                                │
│  ─────────────────────────────                                               │
│  # Reset to default (CAUTION: loses all customizations)                      │
│  $ rm ~/.bashrc                                                              │
│  $ pkg reinstall bash  # May restore default .bashrc                         │
│                                                                              │
│  # Or create minimal .bashrc                                                 │
│  $ echo '# Basic .bashrc' > ~/.bashrc                                        │
│  $ echo 'export PS1="$ "' >> ~/.bashrc                                       │
│                                                                              │
│  💡 PREVENTION: Always backup before editing!                                │
│  $ cp ~/.bashrc ~/.bashrc.backup                                             │
│                                                                              │
│  ✅ RESULT: Termux working again!                                            │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 ARCHITECTURE DIAGRAMS

Visual understanding of Termux configuration!

---

### Diagram 1: Configuration File Loading Order

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    TERMUX CONFIGURATION LOADING ORDER                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   Termux App Start                                                          │
│   ════════════════                                                          │
│        │                                                                     │
│        ▼                                                                     │
│   ┌──────────────────────────────────────────────────────────────┐          │
│   │  ~/.termux/termux.properties                                  │          │
│   │  ───────────────────────────────                              │          │
│   │  • Loads FIRST (app-level settings)                           │          │
│   │  • Controls: back-key, bell, extra-keys, colors               │          │
│   │  • Requires: termux-reload-settings OR app restart            │          │
│   └──────────────────────────┬───────────────────────────────────┘          │
│                              │                                               │
│                              ▼                                               │
│   ┌──────────────────────────────────────────────────────────────┐          │
│   │  System-wide Bash Configuration                               │          │
│   │  ───────────────────────────────                              │          │
│   │  $PREFIX/etc/bash.bashrc                                      │          │
│   │  • Default Termux bash settings                               │          │
│   │  • Sets up basic environment                                  │          │
│   └──────────────────────────┬───────────────────────────────────┘          │
│                              │                                               │
│                              ▼                                               │
│   ┌──────────────────────────────────────────────────────────────┐          │
│   │  User Bash Configuration                                      │          │
│   │  ────────────────────────                                     │          │
│   │  ~/.bashrc                                                    │          │
│   │  ────────────                                                 │          │
│   │  • Runs EVERY interactive shell                               │          │
│   │  • Your customizations go here:                               │          │
│   │    - Aliases                                                  │          │
│   │    - Functions                                                │          │
│   │    - Environment variables                                    │          │
│   │    - Custom prompt (PS1)                                      │          │
│   │    - Welcome messages                                         │          │
│   └──────────────────────────┬───────────────────────────────────┘          │
│                              │                                               │
│                              ▼                                               │
│   ┌──────────────────────────────────────────────────────────────┐          │
│   │  Ready for User Input!                                        │          │
│   └──────────────────────────────────────────────────────────────┘          │
│                                                                              │
│   NOTE: Termux uses non-login interactive shells,                           │
│         so .bash_profile and .profile are NOT loaded by default.            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### Diagram 2: Environment Variable Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ENVIRONMENT VARIABLES FLOW                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌────────────────────────────────────────────────────────────────┐        │
│   │                    SYSTEM DEFAULTS                              │        │
│   ├────────────────────────────────────────────────────────────────┤        │
│   │  HOME     = /data/data/com.termux/files/home                   │        │
│   │  PREFIX   = /data/data/com.termux/files/usr                    │        │
│   │  PATH     = $PREFIX/bin:$PREFIX/bin/applets                    │        │
│   │  SHELL    = $PREFIX/bin/bash                                   │        │
│   │  LANG     = en_US.UTF-8                                        │        │
│   │  TERMUX_VERSION = 0.118.0                                      │        │
│   └──────────────────────────┬─────────────────────────────────────┘        │
│                              │                                               │
│                              ▼                                               │
│   ┌────────────────────────────────────────────────────────────────┐        │
│   │                    USER ADDITIONS                               │        │
│   │              (in ~/.bashrc)                                     │        │
│   ├────────────────────────────────────────────────────────────────┤        │
│   │  export EDITOR=nano                # Default editor            │        │
│   │  export HISTSIZE=10000             # History size              │        │
│   │  export PATH="$HOME/scripts:$PATH" # Add custom path          │        │
│   │  export MY_PROJECT=/path/to/proj   # Custom variable          │        │
│   └──────────────────────────┬─────────────────────────────────────┘        │
│                              │                                               │
│                              ▼                                               │
│   ┌────────────────────────────────────────────────────────────────┐        │
│   │                    SHELL SESSION                               │        │
│   │                                                                 │        │
│   │   echo $PATH                                                   │        │
│   │   → /data/data/.../home/scripts:/data/.../usr/bin:...          │        │
│   │                                                                 │        │
│   │   echo $EDITOR                                                 │        │
│   │   → nano                                                       │        │
│   │                                                                 │        │
│   │   $MY_VARIABLE                                                 │        │
│   │   → Available to all child processes                           │        │
│   └────────────────────────────────────────────────────────────────┘        │
│                                                                              │
│   ┌───────────────────────────────────────────────────────────────┐         │
│   │  EXPORT VS NO EXPORT                                          │         │
│   │  ───────────────────                                          │         │
│   │  MY_VAR="value"      → Shell variable (current shell only)    │         │
│   │  export MY_VAR="val" → Environment var (inherited by children)│         │
│   └───────────────────────────────────────────────────────────────┘         │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### Diagram 3: Alias vs Function vs Script

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ALIAS vs FUNCTION vs SCRIPT                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌───────────────────────────────────────────────────────────────┐         │
│   │                       ALIAS                                    │         │
│   │                   (Text Substitution)                          │         │
│   ├───────────────────────────────────────────────────────────────┤         │
│   │  Syntax: alias name='command'                                  │         │
│   │                                                                 │         │
│   │  Example:                                                      │         │
│   │  alias ll='ls -la'                                             │         │
│   │  alias update='pkg update && pkg upgrade -y'                   │         │
│   │                                                                 │         │
│   │  Characteristics:                                              │         │
│   │  ✓ Simple text replacement                                     │         │
│   │  ✓ No arguments possible                                       │         │
│   │  ✓ Fast execution                                              │         │
│   │  ✓ Defined in .bashrc                                          │         │
│   │  ✗ Limited flexibility                                         │         │
│   └───────────────────────────────────────────────────────────────┘         │
│                              │                                               │
│                              ▼                                               │
│   ┌───────────────────────────────────────────────────────────────┐         │
│   │                      FUNCTION                                  │         │
│   │                   (Shell Code Block)                           │         │
│   ├───────────────────────────────────────────────────────────────┤         │
│   │  Syntax: name() { commands; }                                  │         │
│   │                                                                 │         │
│   │  Example:                                                      │         │
│   │  mkcd() {                                                      │         │
│   │      mkdir -p "$1"                                             │         │
│   │      cd "$1"                                                   │         │
│   │  }                                                             │         │
│   │                                                                 │         │
│   │  Characteristics:                                              │         │
│   │  ✓ Accepts arguments ($1, $2, ...)                             │         │
│   │  ✓ Can contain logic/conditionals                              │         │
│   │  ✓ Runs in current shell                                       │         │
│   │  ✓ Can modify environment                                      │         │
│   │  ✓ Defined in .bashrc                                          │         │
│   └───────────────────────────────────────────────────────────────┘         │
│                              │                                               │
│                              ▼                                               │
│   ┌───────────────────────────────────────────────────────────────┐         │
│   │                       SCRIPT                                   │         │
│   │                   (Executable File)                            │         │
│   ├───────────────────────────────────────────────────────────────┤         │
│   │  File: ~/scripts/myscript.sh                                   │         │
│   │  #!/data/data/com.termux/files/usr/bin/bash                    │         │
│   │  # Complex script with multiple functions                      │         │
│   │                                                                 │         │
│   │  Characteristics:                                              │         │
│   │  ✓ Standalone executable file                                  │         │
│   │  ✓ Can be called from anywhere (if in PATH)                    │         │
│   │  ✓ Runs in subprocess                                          │         │
│   │  ✓ Can be version controlled                                   │         │
│   │  ✓ Shareable between users                                     │         │
│   │  ✓ Environment isolated (unless exported)                      │         │
│   └───────────────────────────────────────────────────────────────┘         │
│                                                                              │
│   WHEN TO USE:                                                              │
│   ────────────                                                              │
│   • Alias   → Single command shortcuts, simple replacements                 │
│   • Function → Multi-step operations with arguments, need current shell     │
│   • Script  → Complex programs, reusable tools, sharing                     │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

Navigate the course efficiently!

| Previous Chapter | Current Chapter | Next Chapter |
|-----------------|-----------------|--------------|
| [Ch 1: Termux Introduction](./Ch01-Termux-Introduction-Installation.md) | **Ch 2: First Setup & Configuration** | [Ch 3: Linux Basics Part 1](./Ch03-Linux-Basics-Part1.md) |

### Prerequisites & Learning Path

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         MODULE 1: FOUNDATION                                 │
│                                                                              │
│  ┌─────────┐     ┌─────────┐     ┌─────────┐     ┌─────────┐              │
│  │  Ch 1   │────▶│  Ch 2   │────▶│  Ch 3   │────▶│  Ch 4   │              │
│  │Intro &  │     │ Setup & │     │ Linux   │     │ Linux   │              │
│  │Install  │     │ Config  │     │Basic 1  │     │Basic 2  │              │
│  └─────────┘     └─────────┘     └─────────┘     └─────────┘              │
│       │               │                                                   │
│       │               │                                                   │
│       │          🎯 YOU ARE HERE                                          │
│       │          Ch 2: First Setup & Configuration                        │
│       │                                                                   │
│       │              ┌─────────┐     ┌─────────┐                          │
│       └─────────────▶│  Ch 5   │────▶│ Ch 6+   │                          │
│                      │ Package │     │Advanced │                          │
│                      │  Mgmt   │     │ Topics  │                          │
│                      └─────────┘     └─────────┘                          │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

| Chapter | Title | Topics Covered | Difficulty |
|---------|-------|---------------|------------|
| Ch 1 | Termux Introduction & Installation | What is Termux, F-Droid install, First setup | ⭐ Beginner |
| Ch 2 | First Setup & Configuration | .bashrc, aliases, environment variables | ⭐ Beginner |
| Ch 3 | Linux Basics Part 1 | pwd, ls, cd, mkdir, rm, cp, mv | ⭐ Beginner |
| Ch 4 | Linux Basics Part 2 | cat, touch, grep, find, chmod, pipes | ⭐⭐ Intermediate |
| Ch 5 | Package Management | pkg, apt, dpkg, repositories | ⭐ Beginner |

---

## 🏆 BONUS ADVANCED CONTENT

Advanced configuration techniques beyond the basics!

---

### Advanced 1: Dynamic Prompt with System Information

```bash
# Add to .bashrc for a professional, informative prompt

# Colors
RED='\[\033[0;31m\]'
GREEN='\[\033[0;32m\]'
YELLOW='\[\033[0;33m\]'
BLUE='\[\033[0;34m\]'
PURPLE='\[\033[0;35m\]'
CYAN='\[\033[0;36m\]'
WHITE='\[\033[0;37m\]'
BOLD='\[\033[1m\]'
RESET='\[\033[0m\]'

# Git branch and status
parse_git() {
    local branch status
    
    # Check if in git repo
    if ! git rev-parse --is-inside-work-tree &>/dev/null; then
        return
    fi
    
    # Get branch name
    branch=$(git symbolic-ref --short HEAD 2>/dev/null || git rev-parse --short HEAD)
    
    # Get status
    local modified=$(git diff --name-only 2>/dev/null | wc -l)
    local staged=$(git diff --cached --name-only 2>/dev/null | wc -l)
    local untracked=$(git ls-files --others --exclude-standard 2>/dev/null | wc -l)
    
    status=""
    [ "$modified" -gt 0 ] && status="${status}${RED}+${modified}${RESET}"
    [ "$staged" -gt 0 ] && status="${status}${GREEN}*${staged}${RESET}"
    [ "$untracked" -gt 0 ] && status="${status}${YELLOW}?${untracked}${RESET}"
    
    echo " (${CYAN}${branch}${RESET}${status})"
}

# Virtual environment detection
parse_venv() {
    if [ -n "$VIRTUAL_ENV" ]; then
        echo "(${PURPLE}$(basename $VIRTUAL_ENV)${RESET})"
    fi
}

# Battery status (requires termux-api)
battery_status() {
    if command -v termux-battery-status &>/dev/null; then
        local battery=$(termux-battery-status 2>/dev/null | grep percentage | cut -d: -f2 | tr -d ' "%,')
        if [ -n "$battery" ]; then
            if [ "$battery" -gt 50 ]; then
                echo "${GREEN}${battery}%${RESET}"
            elif [ "$battery" -gt 20 ]; then
                echo "${YELLOW}${battery}%${RESET}"
            else
                echo "${RED}${battery}%${RESET}"
            fi
        fi
    fi
}

# Set dynamic prompt
set_prompt() {
    local battery=$(battery_status)
    local venv=$(parse_venv)
    local git=$(parse_git)
    
    PS1="${battery:+$battery }${GREEN}\u${RESET}@${BLUE}\h${RESET}:${YELLOW}\w${RESET}${venv}${git}\n${WHITE}\$${RESET} "
}

PROMPT_COMMAND=set_prompt
```

---

### Advanced 2: Smart Command History with Fuzzy Search

```bash
# Install fzf for fuzzy finding
pkg install fzf

# Add to .bashrc for enhanced history search

# Fuzzy search command history (Ctrl+R)
bind -x '"\C-r": __fzf_history__'

__fzf_history__() {
    local selection
    selection=$(HISTTIMEFORMAT= history | fzf --tac --no-sort --height=40% \
        --preview='echo {}' --preview-window=down:1:wrap | cut -d' ' -f2-)
    if [ -n "$selection" ]; then
        READLINE_LINE="$selection"
        READLINE_POINT=${#READLINE_LINE}
    fi
}

# Fuzzy directory navigation (Alt+C)
_fzf_cd() {
    local dir
    dir=$(find . -type d 2>/dev/null | fzf --height=40%)
    if [ -n "$dir" ]; then
        cd "$dir"
    fi
}
bind -m emacs '"\ec": "_fzf_cd\n"'

# Fuzzy file opening (Ctrl+T)
_fzf_file() {
    local file
    file=$(find . -type f 2>/dev/null | fzf --height=40%)
    if [ -n "$file" ]; then
        ${EDITOR:-nano} "$file"
    fi
}
bind -x '"\C-t": _fzf_file'

# Auto-completion with fzf
source $PREFIX/share/fzf/completion.bash
source $PREFIX/share/fzf/key-bindings.bash
```

---

### Advanced 3: Custom Termux Widget with Quick Actions

```bash
# Install Termux:Widget add-on from F-Droid first

# Create widgets directory
mkdir -p ~/.shortcuts

# Quick update widget
cat > ~/.shortcuts/Update << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
pkg update && pkg upgrade -y
echo ""
echo "✅ System updated!"
read -p "Press Enter to close..."
EOF
chmod +x ~/.shortcuts/Update

# Server status widget
cat > ~/.shortcuts/Server\ Status << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
dialog --title "Server Status" \
       --msgbox "$(echo "IP: $(curl -s ifconfig.me)\n\n"; netstat -tulanp | head -20)" \
       20 60
EOF
chmod +x ~/.shortcuts/Server\ Status

# Quick backup widget
cat > ~/.shortcuts/Backup << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
BACKUP_DIR=~/storage/downloads/termux-backups
mkdir -p "$BACKUP_DIR"

BACKUP_FILE="$BACKUP_DIR/termux-$(date +%Y%m%d_%H%M%S).tar.gz"

dialog --title "Backup Termux" \
       --infobox "Creating backup...\nThis may take a minute." 5 50

tar -czf "$BACKUP_FILE" \
    --exclude='~/storage' \
    --exclude='~/.cache' \
    ~/ 2>/dev/null

dialog --title "Backup Complete" \
       --msgbox "Backup saved to:\n$BACKUP_FILE\n\nSize: $(du -h "$BACKUP_FILE" | cut -f1)" 10 60
EOF
chmod +x ~/.shortcuts/Backup

# Quick Python shell widget
cat > ~/.shortcuts/Python << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
python3
EOF
chmod +x ~/.shortcuts/Python

# Network info widget
cat > ~/.shortcuts/Network\ Info << 'EOF'
#!/data/data/com.termux/files/usr/bin/bash
dialog --title "Network Information" \
       --msgbox "$(echo "Public IP: $(curl -s ifconfig.me)\n\nLocal IPs:\n$(hostname -I)\n\nDNS: $(cat /proc/net/route | awk '{print $2}' | head -2 | tail -1)")" 12 60
EOF
chmod +x ~/.shortcuts/Network\ Info

echo "✅ Widgets created! Add Termux:Widget to home screen to use them."
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

Complete this checklist to verify your learning!

### ✅ Concepts Understood

- [ ] I understand the purpose of .bashrc file
- [ ] I know the location of Termux configuration files
- [ ] I understand the difference between .bashrc and termux.properties
- [ ] I know what environment variables are and how to set them
- [ ] I understand the difference between aliases and functions
- [ ] I know what PS1 is and how to customize the prompt
- [ ] I understand how to configure extra keys row

### ✅ Skills Acquired

- [ ] I can edit and reload .bashrc
- [ ] I can create and use aliases
- [ ] I can create shell functions with arguments
- [ ] I can customize the command prompt
- [ ] I can add directories to PATH
- [ ] I can configure termux.properties
- [ ] I can add extra keys row above keyboard

### ✅ Practical Tasks Completed

- [ ] Created at least 5 useful aliases
- [ ] Created at least 1 shell function
- [ ] Customized PS1 prompt with colors
- [ ] Added custom scripts directory to PATH
- [ ] Set up extra keys row in termux.properties
- [ ] Created custom welcome message

### ✅ Troubleshooting Knowledge

- [ ] I know how to reload configuration after changes
- [ ] I know how to debug .bashrc errors
- [ ] I know how to backup and restore configuration
- [ ] I know the difference between exported and non-exported variables

---

## 💡 PRO TIPS - MASTER THESE!

> 💡 **Pro Tip #1:** Always backup your .bashrc before making changes: `cp ~/.bashrc ~/.bashrc.backup`

> 💡 **Pro Tip #2:** Use `reload` alias after editing .bashrc instead of restarting Termux - saves time!

> 💡 **Pro Tip #3:** Add your custom scripts folder to PATH: `export PATH="$HOME/scripts:$PATH"` in .bashrc

> 💡 **Pro Tip #4:** Use `HISTCONTROL=ignoreboth:erasedups` to avoid duplicate commands in history

> 💡 **Pro Tip #5:** Set `back-key=escape` in termux.properties - makes Vim/NeoVim much easier to use

> 💡 **Pro Tip #6:** Create a `~/.bash_aliases` file for aliases and source it from .bashrc for better organization

> 💡 **Pro Tip #7:** Use `shopt -s cdspell` in .bashrc to autocorrect minor typos in cd command

> 💡 **Pro Tip #8:** Add extra keys row with most-used keys (ESC, TAB, CTRL, ALT) for faster typing

> 💡 **Pro Tip #9:** Comment your aliases in .bashrc - future you will thank you!

> 💡 **Pro Tip #10:** Use functions instead of aliases for complex operations - they can take arguments!

---

## 🔥 REAL WORLD APPLICATIONS

### Where This Knowledge Applies:

**1. DevOps & System Administration**
- Customize shell for different environments
- Create aliases for frequent server commands
- Set up consistent environment across machines

**2. Penetration Testing**
- Quick access to security tools via aliases
- Custom welcome message with system info
- Efficient navigation through scan results

**3. Software Development**
- Git aliases for faster version control
- Project navigation shortcuts
- Development environment setup

**4. Automation Scripting**
- Functions in .bashrc for reusable code
- PATH modifications for custom tools
- History configuration for debugging

**5. Daily Productivity**
- Shortcuts for common tasks
- Custom prompt showing current directory
- Quick commands for file management

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CONFIGURATION IMPACT DIAGRAM                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ~/.termux/                     ~/.bashrc                               │
│   ┌─────────────┐               ┌─────────────┐                         │
│   │ App Settings│               │Shell Config │                         │
│   │ • Keys      │               │ • Aliases   │                         │
│   │ • Bell      │               │ • Functions │                         │
│   │ • Colors    │               │ • Prompt    │                         │
│   └──────┬──────┘               └──────┬──────┘                         │
│          │                             │                                 │
│          └──────────┬──────────────────┘                                 │
│                     │                                                    │
│                     ▼                                                    │
│          ┌─────────────────────┐                                        │
│          │  PRODUCTIVITY BOOST │                                        │
│          │  ↑ 50% faster       │                                        │
│          │  ↑ Less typing      │                                        │
│          │  ↑ Fewer errors     │                                        │
│          └─────────────────────┘                                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ⚡ QUICK REFERENCE CARD

### Configuration Files

| File | Purpose | Location |
|------|---------|----------|
| `termux.properties` | App settings | `~/.termux/termux.properties` |
| `.bashrc` | Shell configuration | `~/.bashrc` |
| `.bash_history` | Command history | `~/.bash_history` |
| `.profile` | Login settings | `~/.profile` |

### Essential Commands

| Command | Description |
|---------|-------------|
| `source ~/.bashrc` | Reload shell config |
| `termux-reload-settings` | Apply termux.properties changes |
| `nano ~/.bashrc` | Edit bash configuration |
| `nano ~/.termux/termux.properties` | Edit Termux settings |
| `alias` | List all aliases |
| `unalias <name>` | Remove an alias |
| `export VAR=value` | Set environment variable |
| `echo $VAR` | Display variable value |
| `env` | Show all environment variables |

### Prompt Escape Sequences

| Code | Meaning |
|------|---------|
| `\u` | Username |
| `\h` | Hostname |
| `\w` | Full working directory |
| `\W` | Current directory name |
| `\t` | Time (24-hour) |
| `\d` | Date |
| `\$` | $ (normal) or # (root) |

### Color Codes for PS1

| Color | Code |
|-------|------|
| Red | `\[\033[0;31m\]` |
| Green | `\[\033[0;32m\]` |
| Yellow | `\[\033[0;33m\]` |
| Blue | `\[\033[0;34m\]` |
| Purple | `\[\033[0;35m\]` |
| Cyan | `\[\033[0;36m\]` |
| White | `\[\033[0;37m\]` |
| Reset | `\[\033[0m\]` |

---

## 🏆 BONUS: ADVANCED TIPS

### Extra Configuration Options

```bash
# Advanced .bashrc additions

# === GIT BRANCH IN PROMPT ===
parse_git_branch() {
    git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# Prompt with git branch
export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "

# === AUTO-COMPLETION FOR ALIASES ===
# Enable completion for aliases
complete -o default -F _command apt
complete -o default -F _command pkg

# === DIRECTORY BOOKMARKS ===
# Quick directory navigation
export DIR1=~/
export DIR2=~/projects
export DIR3=~/storage/downloads

# Usage: cd $DIR1, cd $DIR2, etc.

# === ADVANCED HISTORY ===
# Ignore specific commands
export HISTIGNORE="ls:cd:clear:exit"

# Append to history, don't overwrite
shopt -s histappend

# Save multi-line commands
shopt -s lithist

# === AUTO-CD (type directory name to cd) ===
shopt -s autocd

# === SPELL CORRECTION ===
shopt -s cdspell
shopt -s dirspell

# === COLORFUL LESS ===
export LESS="-R"
export LESS_TERMCAP_mb=$'\E[1;31m'
export LESS_TERMCAP_md=$'\E[1;36m'
export LESS_TERMCAP_me=$'\E[0m'

# === CUSTOM BINARY PATH ===
export PATH="$HOME/bin:$HOME/.local/bin:$PATH"
```

### Advanced termux.properties

```properties
# ═══════════════════════════════════════════════════════════════
# ADVANCED TERMUX.PROPERTIES
# ═══════════════════════════════════════════════════════════════

# Full extra keys with all modifiers
extra-keys = [[ \
  {key: ESC, popup: {macro: "CTRL d", display: "exit"}}, \
  {key: CTRL, popup: {macro: "CTRL c", display: "cancel"}}, \
  {key: ALT, popup: {macro: "CTRL z", display: "undo"}}, \
  {key: TAB, popup: {macro: "CTRL a", display: "all"}}, \
  {key: '/', popup: '~'}, \
  {key: '-', popup: '_'}, \
  {key: HOME, popup: END}, \
  {key: UP, popup: PGUP}, \
  {key: DOWN, popup: PGDN}, \
  {key: LEFT, popup: HOME}, \
  {key: RIGHT, popup: END} \
]]

# Second row with symbols
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
  {key: '|', popup: '&'}, \
  {key: '>', popup: '<'}, \
  {key: '"', popup: "'"} \
]]
```

### Useful Functions to Add

```bash
# === DIRECTORY SIZE ===
dirsize() {
    du -sh "${1:-.}" 2>/dev/null
}

# === QUICK FIND ===
qfind() {
    find . -name "*$1*" 2>/dev/null
}

# === EXTRACT ANY ARCHIVE ===
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
            *)           echo "'$1' cannot be extracted" ;;
        esac
    else
        echo "'$1' is not a valid file"
    fi
}

# === NETWORK INFO ===
netinfo() {
    echo "Public IP: $(curl -s ifconfig.me)"
    echo "Local IP: $(hostname -I 2>/dev/null || echo 'N/A')"
}

# === SYSTEM INFO ===
sysinfo() {
    echo "=== SYSTEM INFO ==="
    echo "User: $(whoami)"
    echo "Home: $HOME"
    echo "Shell: $SHELL"
    echo "Termux: $TERMUX_VERSION"
    echo "Prefix: $PREFIX"
    echo "==================="
}
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### ✅ Key Takeaways

- **`~/.termux/`** directory contains Termux app configuration files
- **`termux.properties`** controls Termux app behavior (keys, bell, etc.)
- **`~/.bashrc`** is the main shell configuration file
- **Environment variables** store system-wide values accessible by programs
- **Aliases** are shortcuts for frequently used commands
- **PS1 variable** customizes your command prompt
- **`termux-reload-settings`** applies termux.properties changes
- **`source ~/.bashrc`** reloads shell configuration
- **Functions** in .bashrc enable complex reusable commands
- **History settings** control command history behavior

### 🎯 Skills Acquired

- [ ] Create and edit termux.properties file
- [ ] Configure extra keys row
- [ ] Understand and use environment variables
- [ ] Create a comprehensive .bashrc file
- [ ] Write and use aliases for common tasks
- [ ] Customize the PS1 prompt
- [ ] Add welcome message functions
- [ ] Reload configuration without restarting Termux

---

## 🎯 INTERVIEW QUESTIONS

### Test Your Knowledge (With Answers)

**Q1: What is the difference between ~/.bashrc and ~/.bash_profile?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** In Termux, `.bashrc` is used for interactive non-login shells (which is how Termux starts), while `.bash_profile` is for login shells. Termux typically uses `.bashrc`. On desktop Linux, `.bash_profile` runs once at login, while `.bashrc` runs every time you open a new terminal.
</details>

**Q2: How do you make an alias permanent in Termux?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Add the alias command to your `~/.bashrc` file:
```bash
echo "alias ll='ls -la'" >> ~/.bashrc
source ~/.bashrc
```
The alias will now persist across Termux restarts.
</details>

**Q3: What does the PS1 variable control in Bash?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** PS1 controls the primary prompt string - what you see before typing commands. It can include escape sequences for username (`\u`), hostname (`\h`), current directory (`\w`), time (`\t`), and colors using ANSI escape codes.
</details>

**Q4: How do you apply changes made to termux.properties?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Run `termux-reload-settings` command, or completely close Termux (swipe away from recent apps) and reopen it.
</details>

**Q5: What is the purpose of $PATH environment variable?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** `$PATH` contains a list of directories where the shell looks for executable commands. When you type a command, the shell searches these directories in order. Adding custom directories to PATH allows you to run scripts from anywhere.
</details>

**Q6: How would you add a custom scripts directory to PATH?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Add this line to `.bashrc`:
```bash
export PATH="$HOME/scripts:$PATH"
```
This prepends your scripts directory to the existing PATH.
</details>

**Q7: What is the difference between an alias and a function in Bash?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** 
- **Aliases** are simple text substitutions, cannot take arguments directly
- **Functions** can take arguments, contain complex logic, and use variables
- Example: An alias `alias ll='ls -la'` vs a function:
```bash
mkcd() { mkdir -p "$1" && cd "$1"; }
```
</details>

**Q8: How do you disable the terminal bell in Termux?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Add to `~/.termux/termux.properties`:
```
bell-character=ignore
```
Then run `termux-reload-settings`.
</details>

**Q9: What does `shopt -s cdspell` do?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** It enables automatic spelling correction for the `cd` command. If you make a minor typo in directory name, Bash will try to correct it. Example: `cd Documnts` might automatically become `cd Documents`.
</details>

**Q10: How would you display current git branch in your prompt?**
<details>
<summary>Click to reveal answer</summary>

**Answer:** Add a function to parse git branch and include it in PS1:
```bash
parse_git_branch() {
    git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
PS1="\w\$(parse_git_branch)\$ "
```
</details>

---

## 🚀 NEXT LEVEL TIPS

### Performance Optimization

```bash
# Speed up bash startup by loading completions on demand
# Add to .bashrc:

# Lazy load nvm (if using Node.js)
# Instead of: source ~/.nvm/nvm.sh
# Use a function that loads it when needed
node() {
    unset -f node
    source ~/.nvm/nvm.sh
    node "$@"
}
```

### Best Practices

1. **Organize .bashrc** - Use clear sections with comments
2. **Keep a backup** - Version control your dotfiles with Git
3. **Test before applying** - Use `source ~/.bashrc` to test, then fix errors
4. **Document aliases** - Comment what each alias does
5. **Use functions over aliases** - For complex operations
6. **Set proper history** - `HISTSIZE=10000` and `HISTFILESIZE=20000`
7. **Use `||` and `&&`** - Chain commands safely

### Common Mistakes to Avoid

| ❌ Mistake | ✅ Correct Approach |
|-----------|---------------------|
| Editing .bashrc without backup | Always backup first: `cp ~/.bashrc ~/.bashrc.backup` |
| Forgetting to reload | Use `source ~/.bashrc` after edits |
| Overwriting PATH | Append/prepend: `export PATH="$HOME/bin:$PATH"` |
| Spaces around `=` in assignments | No spaces: `VAR=value` not `VAR = value` |
| Not quoting variables | Always quote: `"$VAR"` not `$VAR` |
| Ignoring errors in .bashrc | Test with `bash -c "source ~/.bashrc"` |

### Pro Configuration Workflow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CONFIGURATION BEST PRACTICES                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   1. BACKUP                     2. EDIT                                  │
│   ┌─────────┐                  ┌─────────┐                              │
│   │ cp      │                  │ nano    │                              │
│   │ ~/.bashrc│                  │ ~/.bashrc│                              │
│   │ ~/.bashrc│──►               │         │──►                           │
│   │ .backup  │                  │         │                              │
│   └─────────┘                  └─────────┘                              │
│                                                                          │
│   3. TEST                      4. RELOAD                                 │
│   ┌─────────┐                  ┌─────────┐                              │
│   │ source  │                  │ reload  │                              │
│   │ ~/.bashrc│                  │         │                              │
│   │ (check  │──►               │ (or     │──►  Done!                    │
│   │ errors) │                  │ restart)│                              │
│   └─────────┘                  └─────────┘                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🎮 INTERACTIVE ELEMENTS

### 📝 Quiz: Test Your Knowledge

**Score yourself: 10 points per correct answer**

1. Which file is the main Termux app configuration?
   - a) ~/.bashrc
   - b) ~/.termux/termux.properties
   - c) ~/.profile
   - d) /etc/config

2. How do you reload termux.properties changes?
   - a) source ~/.termux/termux.properties
   - b) termux-reload-settings
   - c) restart phone
   - d) pkg update

3. What does `\w` mean in PS1 prompt?
   - a) Username
   - b) Working directory (full path)
   - c) Week number
   - d) Word count

4. Which command shows all defined aliases?
   - a) show aliases
   - b) alias
   - c) list alias
   - d) cat ~/.aliases

5. How do you make a variable available to child processes?
   - a) var=value
   - b) set var=value
   - c) export var=value
   - d) global var=value

6. What does `HISTSIZE=10000` control?
   - a) File size limit
   - b) Number of commands in memory history
   - c) History file size on disk
   - d) Screen width

7. Which is NOT a valid alias syntax?
   - a) alias ll='ls -la'
   - b) alias ls ls --color=auto
   - c) alias c='clear'
   - d) alias ..='cd ..'

8. What color code is `\[\033[0;32m\]`?
   - a) Red
   - b) Green
   - c) Blue
   - d) Yellow

9. How do you remove an alias?
   - a) rm alias <name>
   - b) unalias <name>
   - c) del alias <name>
   - d) alias -d <name>

10. What is the default location of .bashrc in Termux?
    - a) /etc/bashrc
    - b) ~/.bashrc (~/ = /data/data/com.termux/files/home)
    - c) /root/.bashrc
    - d) /usr/share/bashrc

**Answers:** 1-b, 2-b, 3-b, 4-b, 5-c, 6-b, 7-b, 8-b, 9-b, 10-b

---

### 🛠️ Try It Yourself Challenges

**Challenge 1: Create Your First Alias**
```bash
# Task: Create a custom alias for checking disk usage
# Steps:
# 1. Open .bashrc
nano ~/.bashrc

# 2. Add this line at the end
alias du='du -h'

# 3. Save and reload
source ~/.bashrc

# 4. Test
du -sh ~
# Expected: Human-readable disk usage of home directory
```

**Challenge 2: Customize Your Prompt**
```bash
# Task: Create a colorful two-line prompt
# Steps:
# 1. Edit .bashrc
nano ~/.bashrc

# 2. Find PS1 and change to:
PS1="\[\033[1;34m\]\w\[\033[0m\]\n\[\033[1;32m\]┌─$\[\033[0m\] "

# 3. Reload and see the new prompt
source ~/.bashrc

# Expected: Blue current directory, green prompt on new line
```

**Challenge 3: Create a Function**
```bash
# Task: Create a function that creates and enters a directory
# Steps:
# 1. Edit .bashrc
nano ~/.bashrc

# 2. Add this function
mkcd() {
    mkdir -p "$1" && cd "$1"
}

# 3. Reload
source ~/.bashrc

# 4. Test
mkcd ~/test_project
pwd
# Expected: You should be in ~/test_project
```

**Challenge 4: Configure Extra Keys**
```bash
# Task: Add custom extra keys row
# Steps:
# 1. Create/edit termux.properties
nano ~/.termux/termux.properties

# 2. Add this content
extra-keys = [[ \
  {key: ESC}, \
  {key: CTRL}, \
  {key: ALT}, \
  {key: TAB}, \
  {key: '/', popup: '~'}, \
  {key: '-', popup: '_'} \
]]

# 3. Apply changes
termux-reload-settings

# Expected: See new keys row above keyboard
```

---

### ✅ Skill Check Checkpoints

**Checkpoint 1: Configuration Files**
- [ ] Can locate ~/.termux/ directory
- [ ] Created/edited termux.properties
- [ ] Used termux-reload-settings
- [ ] Created/edited ~/.bashrc

**Checkpoint 2: Aliases**
- [ ] Created at least 5 custom aliases
- [ ] Used alias command to list aliases
- [ ] Aliases work after restart
- [ ] Used reload alias successfully

**Checkpoint 3: Prompt Customization**
- [ ] Modified PS1 variable
- [ ] Used color codes correctly
- [ ] Created a two-line prompt
- [ ] Prompt shows useful information

**Checkpoint 4: Environment Variables**
- [ ] Understand $HOME, $PATH, $PREFIX
- [ ] Added custom variables to .bashrc
- [ ] Used export correctly
- [ ] Variables persist after restart

---

## 🔗 RELATED CHAPTERS

### Cross-Reference Guide

| This Chapter | Related Chapter | Why Related |
|-------------|-----------------|-------------|
| Ch02: Configuration | **Ch01: Installation** | Requires Termux installed |
| Ch02: Aliases | **Ch03: Linux Basics 1** | Commands referenced in aliases |
| Ch02: Functions | **Ch07: Bash Scripting** | Functions are mini-scripts |
| Ch02: PATH | **Ch05: Package Management** | Packages add to PATH |
| Ch02: Git Aliases | **Ch08: Git in Termux** | Git configuration |

### Next Steps Flowchart

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YOUR LEARNING PATH                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Chapter 1 ──→ Chapter 2 ──→ Chapter 3 ──→ Chapter 4 ──→ Chapter 5   │
│   (Install)    (You are     (Linux       (Linux       (Package         │
│                 here)        Basics 1)   Basics 2)    Mgmt)            │
│                                                                          │
│   After this chapter, practice:                                         │
│   • Create 10+ custom aliases                                          │
│   • Design your perfect prompt                                          │
│   • Set up a project workspace                                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 VISUAL DIAGRAMS

### Bash Configuration Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BASH STARTUP PROCESS                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Termux Opens                                                          │
│        │                                                                 │
│        ▼                                                                 │
│   ┌─────────────┐                                                       │
│   │ Bash Starts │                                                       │
│   └──────┬──────┘                                                       │
│          │                                                               │
│          ▼                                                               │
│   ┌─────────────────────┐                                               │
│   │ Read ~/.bashrc      │                                               │
│   │ • Set variables     │                                               │
│   │ • Define aliases    │                                               │
│   │ • Define functions  │                                               │
│   │ • Set PS1 prompt    │                                               │
│   │ • Run welcome msg   │                                               │
│   └──────────┬──────────┘                                               │
│             │                                                            │
│             ▼                                                            │
│   ┌─────────────────────┐                                               │
│   │ Ready for Commands! │                                               │
│   └─────────────────────┘                                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Configuration Structure

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX CONFIGURATION LAYERS                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Layer 1: App Configuration                                            │
│   ┌─────────────────────────────────────────────┐                       │
│   │ ~/.termux/termux.properties                 │                       │
│   │ • Extra keys row                            │                       │
│   │ • Back key behavior                         │                       │
│   │ • Bell character                            │                       │
│   └─────────────────────────────────────────────┘                       │
│                                                                          │
│   Layer 2: Shell Configuration                                          │
│   ┌─────────────────────────────────────────────┐                       │
│   │ ~/.bashrc                                   │                       │
│   │ • Environment variables                     │                       │
│   │ • Aliases                                   │                       │
│   │ • Functions                                 │                       │
│   │ • Prompt (PS1)                              │                       │
│   │ • Welcome message                           │                       │
│   └─────────────────────────────────────────────┘                       │
│                                                                          │
│   Layer 3: User Data                                                    │
│   ┌─────────────────────────────────────────────┐                       │
│   │ ~/.bash_history                             │                       │
│   │ ~/.bashrc.backup                            │                       │
│   │ ~/scripts/                                  │                       │
│   └─────────────────────────────────────────────┘                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
