# Chapter 9: Termux Styling & Customization

> **Module:** 2 - Environment  
> **Chapter:** 9 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Termux:Styling, themes, fonts, customization |
| Commands Reference | All styling commands and configurations |
| Practice Exercises | Apply different themes |
| Troubleshooting | Common styling issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 9
Title: Termux Styling & Customization | Make Your Terminal Beautiful
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut interesting hai - Termux Styling aur Customization!

Dekho, jab aap Termux use karte ho, default look ekdam plain hota hai.
Black background, white text - boring! Lekin kya aap jaante ho ki Termux
ko itna beautiful bana sakte ho ki professional terminal jaisa lage?

Hacker style green text, Dracula theme ka purple glow, Solarized ka
professional look - ye sab possible hai Termux mein!

Aaj hum seekhenge:
- Termux:Styling app se colors aur fonts change karna
- Popular themes apply karna - Monokai, Dracula, Solarized
- Custom color schemes banana
- termux.properties se advanced customization
- PS1 prompt ko apne naam se customize karna
- Full terminal makeover!

To chaliye shuru karte hain - apne Termux ko beautiful banate hain!

---

[SECTION 1: TERMUX:STYLING APP - 0:45 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle baat karte hain Termux:Styling app ki. Ye ek official add-on
hai jo Termux team ne banaya hai specifically for customization.

Termux:Styling app kya karta hai?
- Color schemes change karta hai
- Fonts change karta hai
- Font size adjust karta hai
- Quick access to styling options

Installation simple hai:

[STEP 1: Install Termux:Styling]

F-Droid se install karein:
1. F-Droid app kholen
2. Search karein "Termux:Styling"
3. Install button dabayein

Ya GitHub se:
https://github.com/termux/termux-styling/releases

[STEP 2: Using Termux:Styling]

Installation ke baad Termux mein jaake:
1. Termux app kholen
2. Long press karein screen pe kahi bhi
3. Ek menu aayega - "Style" option dikhega
4. "Style" pe click karein

[SCREEN: Style Menu showing colors and fonts]

Ab aapko do options milenge:
- COLOR: Color schemes ke liye
- FONT: Fonts ke liye

COLOR pe click karein - bahut saare color schemes milenge:
- Default
- Monokai
- Solarized Dark
- Solarized Light
- Dracula
- GitHub Dark
- Gruvbox
- One Half
- And many more...

Koi bhi select karein, turant apply ho jaayega!

Same way mein FONT pe click karke font choose kar sakte ho:
- Normal fonts
- Monospace fonts
- Powerline fonts (for fancy prompts)

Ye sab bina kisi command ke - just clicks se!

---

[SECTION 2: POPULAR COLOR SCHEMES - 4:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab main aapko popular color schemes ke baare mein detail mein bataunga.
Har scheme ki apni specialty hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                    POPULAR TERMUX COLOR SCHEMES                          │
├──────────────────┬────────────────────────────────────────────────────────┤
│ Theme            │ Description                                         │
├──────────────────┼────────────────────────────────────────────────────────┤
│ Monokai          │ Classic coding theme, vibrant colors                │
│ Solarized Dark   │ Eye-friendly, professional look                     │
│ Solarized Light  │ Light background, good for day use                  │
│ Dracula          │ Purple-based, very popular among hackers            │
│ Gruvbox          │ Retro warm colors, unique look                      │
│ Nord             │ Arctic, bluish color palette                        │
│ One Half         │ Clean, modern, VS Code inspired                     │
│ GitHub Dark      │ GitHub's official dark theme                        │
│ Atom One Dark    │ Atom editor's famous dark theme                     │
│ Ayu              │ Modern theme with good contrast                     │
└──────────────────┴────────────────────────────────────────────────────────┘

[MONOKAI THEME DETAILS]

Monokai classic developer theme hai. Ye colors use karta hai:
- Background: Dark gray (#272822)
- Yellow for keywords
- Green for strings
- Pink for functions
- Blue for numbers

Perfect for: Python, JavaScript developers

[SOLARIZED DARK DETAILS]

Solarized scientifically designed hai - eyes ko kam stress deta hai.
- 16 color palette
- Precise color relationships
- Light and dark variants

Perfect for: Long coding sessions, professional work

[DRACULA THEME DETAILS]

Dracula bahut popular hai hackers mein - kyunki yeh dark hai aur
purple accents mast lagte hain!
- Background: Dark purple (#282a36)
- Green, pink, yellow, cyan accents
- Purple glow feel

Perfect for: Hackers, night owls, aesthetic lovers

[NORD THEME DETAILS]

Nord arctic inspired hai - bluish tones:
- Background: Dark bluish-gray
- Blue, cyan, white accents
- Very calming colors

Perfect for: Minimalists, clean look lovers

Demo ke liye main suggest karta hoon:
1. Monokai try karein - classic feel
2. Dracula try karein - hacker feel
3. Solarized Dark try karein - professional feel
4. Jo pasand aaye, use finalize karein!

---

[SECTION 3: FONT STYLES AND SIZES - 7:00 to 9:30]
─────────────────────────────────────────────────────────────────────────────

Ab baat karte hain fonts ki. Fonts terminal ki readability determine
karte hain.

Termux:Styling mein fonts do categories mein hain:
1. Regular Fonts - Simple, readable
2. Powerline Fonts - Fancy icons and symbols

[FONT OPTIONS]

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX FONT OPTIONS                                   │
├────────────────────────┬────────────────────────────────────────────────┤
│ Font                   │ Best For                                       │
├────────────────────────┼────────────────────────────────────────────────┤
│ JetBrains Mono         │ Coding, excellent readability                  │
│ Fira Code              │ Ligatures support, modern look                 │
│ Hack                   │ Classic monospace, very clean                  │
│ Source Code Pro        │ Adobe's font, professional                     │
│ DejaVu Sans Mono       │ Unicode support, widely compatible             │
│ Droid Sans Mono        │ Android native, good for phones                │
│ Ubuntu Mono            │ Ubuntu style, rounded characters               │
│ Powerline fonts        │ Fancy prompts with icons                       │
└────────────────────────┴────────────────────────────────────────────────┘

[FONT SIZE CUSTOMIZATION]

Font size Termux:Styling se nahi, Termux settings se change hota hai:

Method 1: Pinch Gesture
- Two fingers se screen pe pinch karein
- Zoom in/out se font size change

Method 2: Long Press Menu
- Long press screen pe
- "More" option select karein
- "Preferences" jaayein
- Font size slider adjust karein

Method 3: termux.properties
- Configuration file se set karein (baad mein detail mein)

Recommended font size:
- Phone: 12-16
- Tablet: 16-20
- Personal preference

Main personally use karta hoon:
- Theme: Dracula
- Font: JetBrains Mono
- Size: 14

Ye combination bahut comfortable hai long sessions ke liye!

---

[SECTION 4: TERMUX.PROPERTIES CUSTOMIZATION - 9:30 to 12:30]
─────────────────────────────────────────────────────────────────────────────

Ab aate hain advanced customization pe. termux.properties file se aap
bahut kuch control kar sakte ho.

termux.properties kahan hai?
Location: ~/.termux/termux.properties

Agar folder nahi hai to create karein:

    mkdir -p ~/.termux

File create/edit karein:

    nano ~/.termux/termux.properties

[IMPORTANT PROPERTIES]

Main aapko important properties bata raha hoon:

1. FONT SIZE:
   termux.font.size=14

2. BELL TYPE (Notification sound):
   bell-character=ignore
   # Options: ignore, vibrate, beep

3. BACKUP/RESTORE:
   # Backup location
   backup-path=/sdcard/termux-backup

4. EXTRA KEYS ROW:
   extra-keys = [[ \
     {key: ESC, popup: {macro: "CTRL d", display: "exit"}}, \
     {key: CTRL, popup: {macro: "CTRL c", display: "cancel"}}, \
     {key: ALT, popup: {macro: "CTRL z", display: "undo"}}, \
     {key: TAB, popup: {macro: "ALT .", display: "last"}}, \
     {key: '/', popup: '-'}, \
     {key: '-', popup: '_'} \
   ]]

5. SHORTCUT KEYS:
   # Volume + Q = ESC
   # Volume + W = Up
   # etc.

6. FULLSCREEN:
   fullscreen=true

7. TERMINAL CURSOR:
   terminal-cursor-style=block
   # Options: block, underline, bar

8. CURSOR BLINK:
   terminal-cursor-blink=true

[APPLY CHANGES]

File save karne ke baad, changes apply karne ke liye:

    termux-reload-settings

Ya Termux ko close aur reopen karein.

---

[SECTION 5: CUSTOM COLOR SCHEMES - 12:30 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Agar aap existing themes se bore ho gaye ho, to custom theme bana sakte ho!

Custom theme ke liye 2 files chahiye:
1. ~/.termux/colors.properties - For colors
2. ~/.termux/font.ttf - For custom font (optional)

[COLORS.PROPERTIES FORMAT]

    # Background color
    background=#1e1e2e
    
    # Foreground (text) color
    foreground=#cdd6f4
    
    # Cursor color
    cursor=#f5e0dc
    
    # 16 ANSI colors
    color0=#45475a   # Black
    color1=#f38ba8   # Red
    color2=#a6e3a1   # Green
    color3=#f9e2af   # Yellow
    color4=#89b4fa   # Blue
    color5=#f5c2e7   # Magenta
    color6=#94e2d5   # Cyan
    color7=#bac2de   # White
    color8=#585b70   # Bright Black
    color9=#f38ba8   # Bright Red
    color10=#a6e3a1  # Bright Green
    color11=#f9e2af  # Bright Yellow
    color12=#89b4fa  # Bright Blue
    color13=#f5c2e7  # Bright Magenta
    color14=#94e2d5  # Bright Cyan
    color15=#a6adc8  # Bright White

[CUSTOM THEME EXAMPLE]

Main aapke liye ek custom "Hacker Theme" bana raha hoon:

    # Hacker Green Theme
    background=#0d0d0d
    foreground=#00ff00
    cursor=#00ff00
    color0=#000000
    color1=#ff0000
    color2=#00ff00
    color3=#ffff00
    color4=#0000ff
    color5=#ff00ff
    color6=#00ffff
    color7=#ffffff
    color8=#808080
    color9=#ff0000
    color10=#00ff00
    color11=#ffff00
    color12=#0000ff
    color13=#ff00ff
    color14=#00ffff
    color15=#ffffff

Apply karne ke liye:

    termux-reload-settings

Ye classic Matrix/Hacker look dega!

---

[SECTION 6: PS1 PROMPT CUSTOMIZATION - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Prompt wo line hoti hai jahan aap commands type karte ho. Default mein:

    ~ $

Lekin aap isse bahut customize kar sakte ho!

PS1 variable se prompt control hota hai. Isse .bashrc file mein set karein.

[PS1 SPECIAL CODES]

┌─────────────────────────────────────────────────────────────────────────┐
│                    PS1 SPECIAL CHARACTERS                                │
├────────────────┬────────────────────────────────────────────────────────┤
│ Code           │ Displays                                               │
├────────────────┼────────────────────────────────────────────────────────┤
│ \u             │ Username                                               │
│ \h             │ Hostname                                               │
│ \w             │ Full working directory                                 │
│ \W             │ Current directory name only                            │
│ \d             │ Date (e.g., Mon Jan 01)                                │
│ \t             │ Time in 24-hour format                                 │
│ \T             │ Time in 12-hour format                                 │
│ \@             │ Time in 12-hour am/pm format                           │
│ \n             │ Newline                                                │
│ \\$            │ $ for user, # for root                                 │
│ \!             │ History number of command                              │
│ \j             │ Number of jobs                                         │
└────────────────┴────────────────────────────────────────────────────────┘

[COLOR CODES FOR PS1]

    # Colors
    BLACK='\[\033[0;30m\]'
    RED='\[\033[0;31m\]'
    GREEN='\[\033[0;32m\]'
    YELLOW='\[\033[0;33m\]'
    BLUE='\[\033[0;34m\]'
    PURPLE='\[\033[0;35m\]'
    CYAN='\[\033[0;36m\]'
    WHITE='\[\033[0;37m\]'
    
    # Bold colors
    BRED='\[\033[1;31m\]'
    BGREEN='\[\033[1;32m\]'
    BYELLOW='\[\033[1;33m\]'
    BBLUE='\[\033[1;34m\]'
    BPURPLE='\[\033[1;35m\]'
    BCYAN='\[\033[1;36m\]'
    BWHITE='\[\033[1;37m\]'
    
    # Reset
    NC='\[\033[0m\]'

[PROMPT EXAMPLES]

Example 1: Simple Green Prompt
    PS1="\[\033[0;32m\]\u@\h:\w\$\[\033[0m\] "
    Output: user@device:~$

Example 2: Fancy Colored Prompt
    PS1="\[\033[1;34m\][\[\033[1;32m\]\u\[\033[1;34m\]@\[\033[1;31m\]\h\[\033[1;34m\]] \[\033[1;33m\]\w\[\033[0m\]\\$ "
    Output: [user@device] ~/projects$

Example 3: Hacker Style
    PS1="\[\033[0;32m\]┌─[\[\033[1;32m\]\u@\h\[\033[0;32m\]]─[\[\033[1;34m\]\w\[\033[0;32m\]]\n\[\033[0;32m\]└──╼ \[\033[1;32m\]\$\[\033[0m\] "
    Output:
    ┌─[user@device]─[~]
    └──╼ $

Example 4: With Time and Date
    PS1="\[\033[1;36m\][\d \t] \[\033[1;32m\]\u@\h \[\033[1;34m\]\w\[\033[0m\]\n\$ "
    Output:
    [Mon Jan 01 12:00:00] user@device ~
    $

Ye sab .bashrc file mein add karein:

    nano ~/.bashrc
    
    # Add PS1 line at the end
    PS1="your_custom_prompt"
    
    # Save and reload
    source ~/.bashrc

---

[SECTION 7: TERMUX:FLOAT STYLING - 17:30 to 18:30]
─────────────────────────────────────────────────────────────────────────────

Termux:Float ek floating terminal window deta hai jo other apps ke upar
float kar sakta hai.

Installation:
F-Droid se "Termux:Float" install karein.

Styling:
Termux:Float apne alag se styling support karta hai:
1. Termux:Float app kholen
2. Long press karein
3. Style menu se colors aur fonts choose karein

Termux:Float ke liye separate properties:
    ~/.termux/termux.properties mein:
    
    # Float window size
    float-window-width=800
    float-window-height=600
    
    # Float window position
    float-window-x=100
    float-window-y=100

Termux:Float useful hai jab aapko:
- Coding karte waqt reference rakhna ho
- Multiple terminals chahiye
- Quick commands run karne ho without leaving app

---

[SECTION 8: THEME COLLECTIONS - 18:30 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Aapko ready-made themes bhi milte hain GitHub pe. Popular collections:

1. Termux Theme by HugeGreenBug
   https://github.com/HugeGreenBug/termux-theme
   
2. Termux Themes by 4679
   https://github.com/4679/termux-themes

Install karne ka tarika:

    # Clone repository
    git clone https://github.com/4679/termux-themes.git
    
    # Go to directory
    cd termux-themes
    
    # Run install script
    ./install.sh

Ye scripts automatically themes install kar deti hain aur aapko
menu se select karne ka option milta hai.

---

[SECTION 9: SUMMARY - 19:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 9 complete! Let's summarize:

✅ Termux:Styling app - Easy color and font changes
✅ Popular themes - Monokai, Dracula, Solarized, Nord
✅ Font styles - JetBrains Mono, Fira Code, Powerline fonts
✅ termux.properties - Advanced customization
✅ Custom color schemes - colors.properties file
✅ PS1 prompt - Fancy command prompts
✅ Termux:Float styling - Floating terminal customization
✅ Theme collections - GitHub repositories

Important files yaad rakhein:
- ~/.termux/termux.properties - Main config
- ~/.termux/colors.properties - Custom colors
- ~/.bashrc - PS1 prompt customization

Important commands:
- termux-reload-settings - Apply changes
- Long press → Style - Quick styling

Homework:
1. Apna favorite theme select karein
2. Font try karein aur comfortable size set karein
3. Custom PS1 prompt banayein
4. Agar daring hai to custom color scheme create karein!

Next Chapter 10 mein hum seekhenge:
- Termux:API setup
- Camera access from terminal
- SMS and contacts
- Sensor data
- And much more!

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Thank you for watching! See you in Chapter 10!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Termux:Styling App

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX:STYLING APP OVERVIEW                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Termux:Styling Features                       │   │
│   │                                                                   │   │
│   │   • Color Schemes: 20+ built-in themes                          │   │
│   │   • Font Selection: Multiple monospace fonts                     │   │
│   │   • Easy Access: Long press → Style menu                         │   │
│   │   • Instant Apply: No restart required                           │   │
│   │   • Custom Themes: Add your own                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Installation Methods:                                                  │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │ Method 1: F-Droid (Recommended)                                 │    │
│   │   - Open F-Droid                                                │    │
│   │   - Search "Termux:Styling"                                     │    │
│   │   - Install                                                     │    │
│   ├────────────────────────────────────────────────────────────────┤    │
│   │ Method 2: GitHub Releases                                       │    │
│   │   - https://github.com/termux/termux-styling/releases           │    │
│   │   - Download latest APK                                         │    │
│   │   - Install manually                                            │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Color Scheme Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BUILT-IN COLOR SCHEMES                                │
├──────────────────┬───────────────────────────────────────────────────────┤
│ Theme Name       │ Color Codes (Background, Foreground, Accent)        │
├──────────────────┼───────────────────────────────────────────────────────┤
│ Default          │ #000000, #FFFFFF, System colors                      │
│ Monokai          │ #272822, #F8F8F2, Yellow/Green/Pink                 │
│ Solarized Dark   │ #002B36, #839496, Cyan/Blue/Yellow                  │
│ Solarized Light  │ #FDF6E3, #657B83, Blue/Cyan/Green                   │
│ Dracula          │ #282A36, #F8F8F2, Purple/Green/Pink                 │
│ Gruvbox Dark     │ #282828, #EBDBB2, Orange/Green/Blue                 │
│ Nord             │ #2E3440, #D8DEE9, Blue/Cyan/White                   │
│ One Half Dark    │ #282C34, #DCDFE4, Blue/Green/Purple                 │
│ GitHub Dark      │ #0D1117, #C9D1D9, Blue/Green/Orange                 │
│ Atom One Dark    │ #1D2127, #ABB2BF, Blue/Green/Purple                 │
│ Ayu Dark         │ #0A0E14, #B3B1AD, Blue/Green/Orange                 │
│ Zenburn          │ #3F3F3F, #DCDCCC, Yellow/Green/Cyan                 │
│ Tango            │ #2E3436, #EEEEEC, Blue/Green/Red                    │
│ Linux Console    │ #000000, #AAAAAA, Standard console colors           │
└──────────────────┴───────────────────────────────────────────────────────┘
```

### 3. ANSI Color Codes

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ANSI COLOR CODES REFERENCE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Standard Colors (0-7):                                                │
│   ┌──────────┬───────────┬─────────────────────────────────────────┐   │
│   │ Code     │ Name      │ Typical Use                            │   │
│   ├──────────┼───────────┼─────────────────────────────────────────┤   │
│   │ 0        │ Black     │ Normal text, borders                   │   │
│   │ 1        │ Red       │ Errors, warnings, deletion             │   │
│   │ 2        │ Green     │ Success, additions, executable         │   │
│   │ 3        │ Yellow    │ Warnings, highlights                   │   │
│   │ 4        │ Blue      │ Directories, links                     │   │
│   │ 5        │ Magenta   │ Special files, images                  │   │
│   │ 6        │ Cyan      │ Symlinks, sockets                      │   │
│   │ 7        │ White     │ Normal text                            │   │
│   └──────────┴───────────┴─────────────────────────────────────────┘   │
│                                                                          │
│   Bright Colors (8-15):                                                  │
│   Same colors but brighter intensity                                    │
│                                                                          │
│   Escape Sequence Format:                                                │
│   \033[<style>;<color>m                                                 │
│                                                                          │
│   Styles:                                                                │
│   0 = Normal/Reset                                                       │
│   1 = Bold                                                               │
│   4 = Underline                                                          │
│   5 = Blink                                                              │
│   7 = Reverse (swap foreground/background)                              │
│                                                                          │
│   Examples:                                                              │
│   \033[0;31m  = Normal Red                                              │
│   \033[1;31m  = Bold Red                                                │
│   \033[4;32m  = Underline Green                                         │
│   \033[1;34;44m = Bold Blue on Blue background                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. termux.properties Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX.PROPERTIES OPTIONS                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   File Location: ~/.termux/termux.properties                            │
│                                                                          │
│   ═══════════════════════════════════════════════════════════════════   │
│   APPEARANCE SETTINGS                                                    │
│   ═══════════════════════════════════════════════════════════════════   │
│                                                                          │
│   # Font size (in points)                                               │
│   termux.font.size=14                                                   │
│                                                                          │
│   # Cursor style (block, underline, bar)                                │
│   terminal-cursor-style=block                                           │
│                                                                          │
│   # Cursor blink (true/false)                                           │
│   terminal-cursor-blink=true                                            │
│                                                                          │
│   # Fullscreen mode                                                     │
│   fullscreen=false                                                      │
│                                                                          │
│   ═══════════════════════════════════════════════════════════════════   │
│   BEHAVIOR SETTINGS                                                      │
│   ═══════════════════════════════════════════════════════════════════   │
│                                                                          │
│   # Bell character behavior (ignore, vibrate, beep)                     │
│   bell-character=vibrate                                                │
│                                                                          │
│   # Default working directory                                           │
│   # default-working-directory=/sdcard/Download                          │
│                                                                          │
│   ═══════════════════════════════════════════════════════════════════   │
│   EXTRA KEYS CONFIGURATION                                               │
│   ═══════════════════════════════════════════════════════════════════   │
│                                                                          │
│   # Single row of extra keys                                            │
│   extra-keys = [[ \                                                     │
│     {key: ESC, popup: {macro: "CTRL d", display: "exit"}}, \            │
│     {key: CTRL, popup: {macro: "CTRL c", display: "cancel"}}, \         │
│     {key: ALT, popup: {macro: "CTRL z", display: "undo"}}, \            │
│     {key: TAB, popup: {macro: "ALT .", display: "last"}}, \             │
│     {key: '/', popup: '-'}, \                                           │
│     {key: '-', popup: '_'} \                                            │
│   ]]                                                                    │
│                                                                          │
│   # Two rows of extra keys                                              │
│   extra-keys = [[ \                                                     │
│     {key: ESC, popup: '~'}, \                                           │
│     {key: '/', popup: '\\'}, \                                          │
│     {key: '-', popup: '_'}, \                                           │
│     {key: HOME, popup: '^'}, \                                          │
│     {key: UP, popup: '$'}, \                                            │
│     {key: END, popup: ':'} \                                            │
│   ], [ \                                                                 │
│     {key: TAB, popup: INSERT}, \                                        │
│     {key: LEFT, popup: '|'}, \                                          │
│     {key: DOWN, popup: '&'}, \                                          │
│     {key: RIGHT, popup: ';'}, \                                         │
│     {key: DEL, popup: '`'}, \                                           │
│     {key: ENTER, popup: '\\n'} \                                        │
│   ]]                                                                    │
│                                                                          │
│   ═══════════════════════════════════════════════════════════════════   │
│   TERMUX:FLOAT SPECIFIC                                                  │
│   ═══════════════════════════════════════════════════════════════════   │
│                                                                          │
│   # Float window dimensions                                              │
│   float-window-width=800                                                │
│   float-window-height=600                                               │
│   float-window-x=100                                                    │
│   float-window-y=100                                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5. Custom Theme Creation

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CREATING CUSTOM THEMES                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   File: ~/.termux/colors.properties                                     │
│                                                                          │
│   Structure:                                                             │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │ # Basic colors (required)                                      │    │
│   │ background=#HEXCOLOR                                           │    │
│   │ foreground=#HEXCOLOR                                           │    │
│   │                                                                │    │
│   │ # Cursor (optional)                                            │    │
│   │ cursor=#HEXCOLOR                                               │    │
│   │                                                                │    │
│   │ # 16 ANSI colors (required for full theme)                     │    │
│   │ color0=  # Black (normal)                                      │    │
│   │ color1=  # Red (normal)                                        │    │
│   │ color2=  # Green (normal)                                      │    │
│   │ color3=  # Yellow (normal)                                     │    │
│   │ color4=  # Blue (normal)                                       │    │
│   │ color5=  # Magenta (normal)                                    │    │
│   │ color6=  # Cyan (normal)                                       │    │
│   │ color7=  # White (normal)                                      │    │
│   │ color8=  # Black (bright)                                      │    │
│   │ color9=  # Red (bright)                                        │    │
│   │ color10= # Green (bright)                                      │    │
│   │ color11= # Yellow (bright)                                     │    │
│   │ color12= # Blue (bright)                                       │    │
│   │ color13= # Magenta (bright)                                    │    │
│   │ color14= # Cyan (bright)                                       │    │
│   │ color15= # White (bright)                                      │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 6. Sample Custom Themes

**Catppuccin Mocha Theme:**
```properties
# ~/.termux/colors.properties - Catppuccin Mocha
background=#1e1e2e
foreground=#cdd6f4
cursor=#f5e0dc
color0=#45475a
color1=#f38ba8
color2=#a6e3a1
color3=#f9e2af
color4=#89b4fa
color5=#f5c2e7
color6=#94e2d5
color7=#bac2de
color8=#585b70
color9=#f38ba8
color10=#a6e3a1
color11=#f9e2af
color12=#89b4fa
color13=#f5c2e7
color14=#94e2d5
color15=#a6adc8
```

**Hacker Matrix Theme:**
```properties
# ~/.termux/colors.properties - Hacker Matrix
background=#000000
foreground=#00ff00
cursor=#00ff00
color0=#000000
color1=#00ff00
color2=#00ff00
color3=#00ff00
color4=#00ff00
color5=#00ff00
color6=#00ff00
color7=#00ff00
color8=#00aa00
color9=#00ff00
color10=#00ff00
color11=#00ff00
color12=#00ff00
color13=#00ff00
color14=#00ff00
color15=#ffffff
```

**Tokyo Night Theme:**
```properties
# ~/.termux/colors.properties - Tokyo Night
background=#1a1b26
foreground=#a9b1d6
cursor=#c0caf5
color0=#15161e
color1=#f7768e
color2=#9ece6a
color3=#e0af68
color4=#7aa2f7
color5=#bb9af7
color6=#7dcfff
color7=#a9b1d6
color8=#414868
color9=#f7768e
color10=#9ece6a
color11=#e0af68
color12=#7aa2f7
color13=#bb9af7
color14=#7dcfff
color15=#c0caf5
```

### 7. PS1 Prompt Templates

```bash
# ═══════════════════════════════════════════════════════════════════════
# PS1 PROMPT TEMPLATES FOR .bashrc
# ═══════════════════════════════════════════════════════════════════════

# Template 1: Simple and Clean
PS1="\[\033[0;32m\]\w\[\033[0m\]\\$ "

# Template 2: Username and Directory
PS1="\[\033[1;32m\]\u\[\033[0m\]:\[\033[1;34m\]\w\[\033[0m\]\\$ "

# Template 3: Full Info with Color
PS1="\[\033[1;36m\][\u@\h] \[\033[1;34m\]\w\[\033[0m\]\\$ "

# Template 4: Two-Line Prompt
PS1="\[\033[1;34m\]┌─[\[\033[1;32m\]\u@\h\[\033[1;34m\]]─[\[\033[1;33m\]\w\[\033[1;34m\]]\n└─\[\033[1;32m\]\\$\[\033[0m\] "

# Template 5: Hacker Style Green
PS1="\[\033[0;32m\]┌──(\[\033[1;32m\]\u㉿\h\[\033[0;32m\])-[\[\033[1;34m\]\w\[\033[0;32m\]]\n\[\033[0;32m\]└─\$\[\033[0m\] "

# Template 6: With Git Branch (requires git)
parse_git_branch() {
    git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
PS1="\[\033[1;36m\]\u@\h\[\033[0m\]:\[\033[1;34m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[0m\]\\$ "

# Template 7: Minimal with Arrow
PS1="\[\033[1;34m\]❯\[\033[0m\] "

# Template 8: Time-Stamped
PS1="\[\033[1;30m\][\t] \[\033[1;32m\]\u@\h \[\033[1;34m\]\w\[\033[0m\]\n\\$ "

# Template 9: Powerline-style (requires powerline fonts)
PS1="\[\033[0;34m\] \w \[\033[0;34m\]\[\033[0;32m\] \u@\h \[\033[0m\] "

# Template 10: Colorful Multi-line
PS1="\n\[\033[1;35m\]╭─\[\033[1;36m\]\u@\h \[\033[1;33m\]\w\n\[\033[1;35m\]╰─\[\033[1;32m\]\\$\[\033[0m\] "
```

---

## 📋 COMMANDS REFERENCE

### Styling Commands

```bash
# ═══════════════════════════════════════════════════════════════════════
# TERMUX STYLING COMMANDS
# ═══════════════════════════════════════════════════════════════════════

# Create Termux configuration directory
mkdir -p ~/.termux

# Create/edit termux.properties
nano ~/.termux/termux.properties

# Create custom colors file
nano ~/.termux/colors.properties

# Apply changes after editing
termux-reload-settings

# View current PS1 prompt
echo $PS1

# Edit bashrc for prompt customization
nano ~/.bashrc

# Reload bashrc
source ~/.bashrc

# List available fonts (if installed)
ls ~/.termux/*.ttf 2>/dev/null

# View termux.properties
cat ~/.termux/termux.properties

# View colors.properties
cat ~/.termux/colors.properties
```

### Quick Theme Switch Commands

```bash
# ═══════════════════════════════════════════════════════════════════════
# QUICK THEME SWITCH SCRIPTS
# ═══════════════════════════════════════════════════════════════════════

# Switch to Dracula theme
cat > ~/.termux/colors.properties << 'EOF'
background=#282A36
foreground=#F8F8F2
cursor=#F8F8F2
color0=#000000
color1=#FF5555
color2=#50FA7B
color3=#F1FA8C
color4=#BD93F9
color5=#FF79C6
color6=#8BE9FD
color7=#BFBFBF
color8=#4D4D4D
color9=#FF5555
color10=#50FA7B
color11=#F1FA8C
color12=#BD93F9
color13=#FF79C6
color14=#8BE9FD
color15=#E6E6E6
EOF
termux-reload-settings

# Switch to Nord theme
cat > ~/.termux/colors.properties << 'EOF'
background=#2E3440
foreground=#D8DEE9
cursor=#D8DEE9
color0=#3B4252
color1=#BF616A
color2=#A3BE8C
color3=#EBCB8B
color4=#81A1C1
color5=#B48EAD
color6=#88C0D0
color7=#E5E9F0
color8=#4C566A
color9=#BF616A
color10=#A3BE8C
color11=#EBCB8B
color12=#81A1C1
color13=#B48EAD
color14=#8FBCBB
color15=#ECEFF4
EOF
termux-reload-settings

# Switch to Gruvbox theme
cat > ~/.termux/colors.properties << 'EOF'
background=#282828
foreground=#EBDBB2
cursor=#EBDBB2
color0=#282828
color1=#CC241D
color2=#98971A
color3=#D79921
color4=#458588
color5=#B16286
color6=#689D6A
color7=#A89984
color8=#928374
color9=#FB4934
color10=#B8BB26
color11=#FABD2F
color12=#83A598
color13=#D3869B
color14=#8EC07C
color15=#EBDBB2
EOF
termux-reload-settings
```

### Font Management Commands

```bash
# ═══════════════════════════════════════════════════════════════════════
# FONT MANAGEMENT
# ═══════════════════════════════════════════════════════════════════════

# Download custom font (example: JetBrains Mono)
curl -L -o ~/.termux/font.ttf "https://github.com/JetBrains/JetBrainsMono/raw/master/fonts/ttf/JetBrainsMono-Regular.ttf"
termux-reload-settings

# Download Fira Code font
curl -L -o ~/.termux/font.ttf "https://github.com/tonsky/FiraCode/raw/master/distr/ttf/FiraCode-Regular.ttf"
termux-reload-settings

# Download Hack font
curl -L -o ~/.termux/font.ttf "https://github.com/source-foundry/Hack/raw/master/build/ttf/Hack-Regular.ttf"
termux-reload-settings

# Remove custom font (revert to default)
rm ~/.termux/font.ttf
termux-reload-settings

# List installed fonts in Termux
ls -la ~/.termux/
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Theme Application

```bash
# ═══════════════════════════════════════════════════════════════════════
# EXERCISE 1: Apply Different Themes
# Objective: Learn to use Termux:Styling app
# ═══════════════════════════════════════════════════════════════════════

# Step 1: Open Termux:Styling
# Long press on Termux screen
# Select "Style" from menu

# Step 2: Try these themes in order
# - Default
# - Monokai
# - Solarized Dark
# - Dracula
# - Nord

# Step 3: For each theme, note your observations
# Which one is most readable?
# Which one looks best?

# Step 4: Also try different fonts
# Select "FONT" option
# Try: JetBrains Mono, Fira Code, Hack

# Step 5: Select your final combination
# My choice: Theme = _____ Font = _____
```

### Exercise 2: Custom Theme Creation

```bash
# ═══════════════════════════════════════════════════════════════════════
# EXERCISE 2: Create Your Own Theme
# Objective: Learn to create custom color schemes
# ═══════════════════════════════════════════════════════════════════════

# Step 1: Create .termux directory if not exists
mkdir -p ~/.termux

# Step 2: Create custom theme file
nano ~/.termux/colors.properties

# Step 3: Add your custom colors (use template below)
# Tip: Use color picker websites like coolors.co

# Template - Fill in your hex colors:
# background=#??????
# foreground=#??????
# cursor=#???????
# color0=#??????   (Black)
# color1=#??????   (Red)
# color2=#??????   (Green)
# color3=#??????   (Yellow)
# color4=#??????   (Blue)
# color5=#??????   (Magenta)
# color6=#??????   (Cyan)
# color7=#??????   (White)
# color8=#??????   (Bright Black)
# color9=#??????   (Bright Red)
# color10=#??????  (Bright Green)
# color11=#??????  (Bright Yellow)
# color12=#??????  (Bright Blue)
# color13=#??????  (Bright Magenta)
# color14=#??????  (Bright Cyan)
# color15=#??????  (Bright White)

# Step 4: Apply your theme
termux-reload-settings

# Step 5: Test with colorful output
echo -e "\033[0;31mRed\033[0m \033[0;32mGreen\033[0m \033[0;33mYellow\033[0m \033[0;34mBlue\033[0m \033[0;35mMagenta\033[0m \033[0;36mCyan\033[0m"

# Step 6: List files to see color scheme
ls --color=auto ~
```

### Exercise 3: PS1 Prompt Customization

```bash
# ═══════════════════════════════════════════════════════════════════════
# EXERCISE 3: Customize Your Prompt
# Objective: Learn PS1 prompt customization
# ═══════════════════════════════════════════════════════════════════════

# Step 1: Backup current bashrc
cp ~/.bashrc ~/.bashrc.backup 2>/dev/null

# Step 2: Open bashrc
nano ~/.bashrc

# Step 3: Add one of these prompts at the end:

# Option A: Two-line prompt
PS1="\[\033[1;34m\]┌─[\[\033[1;32m\]\u@\h\[\033[1;34m\]]─[\[\033[1;33m\]\w\[\033[1;34m\]]\n└─\[\033[1;32m\]\\$\[\033[0m\] "

# Option B: Hacker style
PS1="\[\033[0;32m\]┌──(\[\033[1;32m\]\u㉿\h\[\033[0;32m\])-[\[\033[1;34m\]\w\[\033[0;32m\]]\n\[\033[0;32m\]└─\$\[\033[0m\] "

# Option C: Minimal arrow
PS1="\[\033[1;36m\]❯\[\033[0m\] "

# Step 4: Save and reload
source ~/.bashrc

# Step 5: Test by navigating
cd ~
cd /sdcard
cd $PREFIX

# Step 6: Try creating your own custom prompt
# Use the PS1 codes reference to create something unique!
```

### Exercise 4: Complete Terminal Makeover

```bash
# ═══════════════════════════════════════════════════════════════════════
# EXERCISE 4: Full Terminal Makeover
# Objective: Apply all styling knowledge together
# ═══════════════════════════════════════════════════════════════════════

# Step 1: Create configuration directory
mkdir -p ~/.termux

# Step 2: Set up termux.properties
cat > ~/.termux/termux.properties << 'EOF'
# Font size
termux.font.size=14

# Cursor style
terminal-cursor-style=block
terminal-cursor-blink=true

# Bell behavior
bell-character=vibrate

# Extra keys
extra-keys = [[ \
  {key: ESC, popup: {macro: "CTRL d", display: "exit"}}, \
  {key: CTRL, popup: {macro: "CTRL c", display: "cancel"}}, \
  {key: ALT, popup: {macro: "CTRL z", display: "undo"}}, \
  {key: TAB, popup: {macro: "ALT .", display: "last"}}, \
  {key: '/', popup: '-'}, \
  {key: '-', popup: '_'} \
]]
EOF

# Step 3: Set up custom colors (Dracula-inspired)
cat > ~/.termux/colors.properties << 'EOF'
background=#282A36
foreground=#F8F8F2
cursor=#BD93F9
color0=#21222C
color1=#FF5555
color2=#50FA7B
color3=#F1FA8C
color4=#BD93F9
color5=#FF79C6
color6=#8BE9FD
color7=#F8F8F2
color8=#6272A4
color9=#FF6E6E
color10=#69FF94
color11=#FFFFA5
color12=#D6ACFF
color13=#FF92DF
color14=#A4FFFF
color15=#FFFFFF
EOF

# Step 4: Download nice font (JetBrains Mono)
curl -L -o ~/.termux/font.ttf "https://github.com/JetBrains/JetBrainsMono/raw/master/fonts/ttf/JetBrainsMono-Regular.ttf" 2>/dev/null

# Step 5: Set up custom prompt
cat >> ~/.bashrc << 'EOF'

# Custom prompt
PS1="\[\033[1;34m\]┌─[\[\033[1;32m\]\u@\h\[\033[1;34m\]]─[\[\033[1;33m\]\w\[\033[1;34m\]]\n└─\[\033[1;35m\]\\$\[\033[0m\] "

# Welcome message
echo ""
echo "┌─────────────────────────────────────────┐"
echo "│  Welcome to Termux! Happy hacking! 🚀   │"
echo "└─────────────────────────────────────────┘"
echo ""
EOF

# Step 6: Apply all changes
termux-reload-settings
source ~/.bashrc

# Step 7: Take a screenshot of your beautiful terminal!
# Your terminal now has:
# ✅ Custom theme (Dracula-inspired)
# ✅ Nice font (JetBrains Mono)
# ✅ Custom prompt
# ✅ Extra keys
# ✅ Welcome message
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Termux:Styling Menu Not Appearing

```bash
# Symptoms: Long press doesn't show Style option

# Cause: Termux:Styling not installed or not linked

# Solution 1: Install Termux:Styling
# Download from F-Droid or GitHub

# Solution 2: Check if installed
pkg list-installed | grep styling

# Solution 3: Reinstall
# Uninstall Termux:Styling
# Reinstall from F-Droid
# Restart Termux

# Solution 4: Check app permissions
# Settings → Apps → Termux:Styling → Permissions
```

### Problem 2: Custom Theme Not Applying

```bash
# Symptoms: colors.properties created but no change

# Cause: Wrong file location or format

# Solution 1: Check file location
ls -la ~/.termux/colors.properties

# Solution 2: Check file content
cat ~/.termux/colors.properties

# Solution 3: Apply changes
termux-reload-settings

# Solution 4: Check hex format
# Colors must be in #RRGGBB format
# Example: #282A36 (correct)
# Example: 282A36 (incorrect - missing #)
# Example: #282 (incorrect - wrong length)

# Solution 5: Check for typos
# Property names must be exact:
# background, foreground, cursor, color0-color15
```

### Problem 3: Font Not Changing

```bash
# Symptoms: font.ttf placed but font unchanged

# Cause: Font file corrupted or unsupported format

# Solution 1: Check font file
ls -la ~/.termux/font.ttf

# Solution 2: Verify file is valid TTF
file ~/.termux/font.ttf

# Solution 3: Redownload font
rm ~/.termux/font.ttf
curl -L -o ~/.termux/font.ttf "FONT_URL_HERE"
termux-reload-settings

# Solution 4: Use different font source
# Some fonts may not work well on Android

# Solution 5: Check font permissions
chmod 644 ~/.termux/font.ttf
termux-reload-settings
```

### Problem 4: termux.properties Not Working

```bash
# Symptoms: Settings in termux.properties not applied

# Cause: Syntax error or not reloaded

# Solution 1: Check syntax
# No spaces around = sign
# Correct: termux.font.size=14
# Wrong: termux.font.size = 14

# Solution 2: Check file location
ls -la ~/.termux/termux.properties

# Solution 3: Reload settings
termux-reload-settings

# Solution 4: Debug mode
# Add debug output to check if file is read
termux-reload-settings && echo "Settings reloaded"

# Solution 5: Restart Termux completely
# Kill Termux from recent apps
# Reopen Termux
```

### Problem 5: PS1 Prompt Not Changing

```bash
# Symptoms: .bashrc edited but prompt unchanged

# Cause: .bashrc not sourced or syntax error

# Solution 1: Source bashrc manually
source ~/.bashrc

# Solution 2: Check for syntax errors
bash -c "source ~/.bashrc && echo OK"

# Solution 3: Check PS1 is set
echo $PS1

# Solution 4: Verify bashrc exists
ls -la ~/.bashrc

# Solution 5: Add PS1 to correct file
# Make sure PS1 is in ~/.bashrc not ~/.bash_profile
# Termux uses ~/.bashrc

# Solution 6: Escape brackets correctly
# Correct: \[\033[1;32m\]
# Wrong: [\033[1;32m] (missing backslash escapes)
```

### Problem 6: Colors Look Wrong

```bash
# Symptoms: Colors don't match expected theme

# Cause: Terminal app override or color mismatch

# Solution 1: Check if Termux:Styling is overriding
# Long press → Style → Check selected theme
# If using custom colors.properties, 
# Termux:Styling should show "Custom"

# Solution 2: Verify color codes
# Use proper hex format
# Ensure colors have good contrast

# Solution 3: Test with echo
echo -e "\033[0;31mRed test\033[0m"
echo -e "\033[0;32mGreen test\033[0m"
echo -e "\033[0;33mYellow test\033[0m"
echo -e "\033[0;34mBlue test\033[0m"
echo -e "\033[0;35mMagenta test\033[0m"
echo -e "\033[0;36mCyan test\033[0m"

# Solution 4: Check background/foreground contrast
# Light foreground needs dark background
# Dark foreground needs light background
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Before/After Style**
```
┌────────────────────────────────────┐
│  BEFORE         │    AFTER         │
│  ───────────────┼───────────────── │
│  Plain Black    │  🎨 Colorful     │
│  Boring Text    │  ✨ Beautiful    │
│  Default        │  Customized      │
│                                    │
│  TERMUX MAKEOVER! 🚀               │
│  [T3rmuxk1ng Logo]                 │
└────────────────────────────────────┘
```

**Option B: Theme Gallery**
```
┌────────────────────────────────────┐
│  🎨 TERMUX THEMES                  │
│                                    │
│  [Monokai] [Dracula] [Nord]        │
│                                    │
│  Make Your Terminal                │
│  BEAUTIFUL! ✨                      │
│                                    │
│  Chapter 9 | T3rmuxk1ng            │
└────────────────────────────────────┘
```

**Option C: Hacker Aesthetic**
```
┌────────────────────────────────────┐
│  💻 HACKER STYLE TERMINAL          │
│                                    │
│  ┌──────────────────────────┐      │
│  │ user@termux:~$           │      │
│  │ ┌─[user@device]─[~]      │      │
│  │ └──╼ $                   │      │
│  └──────────────────────────┘      │
│                                    │
│  Custom Themes & Prompts!          │
│  Ch 9 | T3rmuxk1ng                 │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🎨 Termux Full Course - Chapter 9: Termux Styling & Customization

🔥 In this video you'll learn:
• Termux:Styling app installation and usage
• Popular themes - Monokai, Dracula, Solarized, Nord
• Font styles and sizes
• termux.properties customization
• Creating custom color schemes
• PS1 prompt customization
• Full terminal makeover!

⏱️ Timestamps:
0:00 - Introduction
0:45 - Termux:Styling App
4:00 - Popular Color Schemes
7:00 - Font Styles and Sizes
9:30 - termux.properties Customization
12:30 - Custom Color Schemes
15:00 - PS1 Prompt Customization
17:30 - Termux:Float Styling
18:30 - Theme Collections
19:30 - Summary

📥 Download Links:
• F-Droid: https://f-droid.org
• Termux:Styling: https://github.com/termux/termux-styling

📝 Commands from this video:
mkdir -p ~/.termux
nano ~/.termux/colors.properties
termux-reload-settings

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxStyling #TermuxTheme #TermuxCustomization #TermuxCourse #T3rmuxk1ng #LinuxOnAndroid #TerminalTheme

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux styling, termux theme, termux customization, termux colors,
termux font, termux prompt, termux ps1, termux colors.properties,
termux termux.properties, termux styling app, termux dracula theme,
termux monokai theme, termux solarized, termux nord theme,
termux custom theme, termux hacker theme, termux beautiful terminal,
termux makeover, termux font size, termux cursor style,
termux extra keys, termux course, termux tutorial hindi,
t3rmuxk1ng, android terminal theme, terminal customization
```

### Hashtags

```
#Termux #TermuxStyling #TermuxTheme #TermuxCustomization 
#TermuxCourse #TermuxHindi #LinuxOnAndroid #TerminalTheme 
#DraculaTheme #Monokai #T3rmuxk1ng #LearnTermux #AndroidTerminal
```

---

## 📚 ADDITIONAL RESOURCES

### Theme Repositories

| Resource | Link |
|----------|------|
| Termux:Styling | https://github.com/termux/termux-styling |
| Termux Themes | https://github.com/4679/termux-themes |
| Base16 Termux | https://github.com/kdrag0n/base16-termux |
| iTerm2 Colors (compatible) | https://iterm2colorschemes.com |

### Font Resources

| Font | Source |
|------|--------|
| JetBrains Mono | https://github.com/JetBrains/JetBrainsMono |
| Fira Code | https://github.com/tonsky/FiraCode |
| Hack Font | https://github.com/source-foundry/Hack |
| Source Code Pro | https://github.com/adobe-fonts/source-code-pro |
| Nerd Fonts | https://github.com/ryanoasis/nerd-fonts |

### Color Tools

| Tool | Purpose |
|------|---------|
| Coolors.co | Color palette generator |
| ColorHunt | Trending color palettes |
| HTML Color Codes | Color reference |
| iTerm2 Color Schemes | Theme inspiration |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 10, verify:

- [ ] Termux:Styling app installed and working
- [ ] Tried at least 3 different themes
- [ ] Found a preferred font and size
- [ ] Created ~/.termux directory
- [ ] Edited termux.properties at least once
- [ ] Successfully applied custom theme or prompt
- [ ] Understand PS1 prompt customization
- [ ] Know how to use termux-reload-settings

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 10: Termux:API Setup**

- Termux:API installation
- Camera access from terminal
- SMS and contacts management
- Sensor data reading
- Clipboard operations
- Media playback control
- Notification creation
- And much more!

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
