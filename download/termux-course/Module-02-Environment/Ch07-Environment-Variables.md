# Chapter 7: Environment Variables

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║   🔧 ════════════════════════════════════════════════════════════════ 🔧      ║
║                                                                               ║
║        ███████╗███╗   ██╗███████╗██████╗  ██████╗ ███████╗██████╗             ║
║        ██╔════╝████╗  ██║██╔════╝██╔══██╗██╔═══██╗██╔════╝██╔══██╗            ║
║        █████╗  ██╔██╗ ██║█████╗  ██████╔╝██║   ██║█████╗  ██████╔╝            ║
║        ██╔══╝  ██║╚██╗██║██╔══╝  ██╔══██╗██║   ██║██╔══╝  ██╔══██╗            ║
║        ███████╗██║ ╚████║███████╗██║  ██║╚██████╔╝███████╗██║  ██║            ║
║        ╚══════╝╚═╝  ╚═══╝╚══════╝╚═╝  ╚═╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝            ║
║                                                                               ║
║               🎛️ CONFIGURE YOUR TERMINAL ENVIRONMENT 🎛️                       ║
║                                                                               ║
║   🔧 ════════════════════════════════════════════════════════════════ 🔧      ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 2 - Environment
> **Chapter:** 7 of 61
> **Duration:** 15-20 Minutes
> **Difficulty:** ⭐⭐ Intermediate

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Environment variables deep dive |
| Variables Reference | PATH, HOME, PREFIX, SHELL, USER, TERM, TMPDIR |
| Practical Examples | 25+ hands-on examples |
| Practice Exercises | Real-world tasks |
| Troubleshooting | Common variable issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 7
Title: Environment Variables | Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - Environment Variables.

Agar aap Termux ko seriously use karna chahte ho - scripting, development,
automation, hacking tools - sab ke liye environment variables samajhna
zaruri hai.

Ye wo cheez hai jo aapke terminal ko configure karti hai - aapka prompt
kaisa dikhe, aapke commands kahan se run ho, aapki scripts kahan save ho,
sab kuch environment variables control karta hai.

Is chapter mein hum cover karenge:
- Environment variables kya hote hain
- Important variables jaise PATH, HOME, PREFIX
- Variables ko kaise dekhein, set karein, delete karein
- Permanent configuration ke liye .bashrc aur .profile files
- PS1 prompt customization
- 25+ practical examples

To chaliye shuru karte hain!

---

[SECTION 1: WHAT ARE ENVIRONMENT VARIABLES - 0:45 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle sawal - Environment Variables kya hai?

Simple shabdon mein - Environment variables wo values hain jo aapke
terminal environment ko define karti hain. Ye variables aapke shell
ko batati hain ki system kaise behave kare.

Ek example se samjhein:

Jab aap terminal mein 'python' type karte ho, to system ko ye pata
 hona chahiye ki python kahan hai. Ye information PATH variable
mein stored hoti hai.

PATH variable ek list hoti hai directories ki - jahan system
commands search karta hai.

Environment variable ek key-value pair hota hai:

    VARIABLE_NAME=value

Jaise:
    HOME=/data/data/com.termux/files/home
    USER=u0_a123
    SHELL=/data/data/com.termux/files/usr/bin/bash

Har variable ka ek specific purpose hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ENVIRONMENT VARIABLES EXAMPLES                        │
├─────────────────────────────────────────────────────────────────────────┤
│ Variable    │ Value                                    │ Purpose         │
├─────────────┼──────────────────────────────────────────┼─────────────────│
│ HOME        │ /data/data/com.termux/files/home         │ Home directory  │
│ USER        │ u0_a123                                  │ Current user    │
│ SHELL       │ /data/data/.../bin/bash                  │ Default shell   │
│ PATH        │ /data/.../bin:/system/bin                │ Command paths   │
│ TERM        │ xterm-256color                           │ Terminal type   │
│ PREFIX      │ /data/data/com.termux/files/usr          │ Install prefix  │
└─────────────────────────────────────────────────────────────────────────┘

Types of Variables:

1. System Variables - Termux/Android set karta hai
   - PATH, HOME, PREFIX, TERM

2. User Variables - Aap khud create karte ho
   - MY_PROJECT, API_KEY, DB_NAME

3. Shell Variables - Shell ke liye specific
   - PS1 (prompt), HISTSIZE (history size)

Important: Environment variables CASE-SENSITIVE hote hain!
PATH aur path alag-alag hain.

---

[SECTION 2: IMPORTANT ENVIRONMENT VARIABLES - 4:00 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye Termux ke important environment variables ko detail mein
dekhte hain:

[PATH Variable]

PATH sabse important variable hai. Ye batata hai ki shell ko
commands kahan search karni hain.

    echo $PATH

Output aisa aayega:
/data/data/com.termux/files/usr/bin:/data/data/com.termux/files/usr/bin/applets

Matlab jab aap 'ls' ya 'python' type karte ho, shell PATH mein
di gayi directories mein search karta hai.

Agar aap koi custom script banate ho aur use directly run karna
chahte ho, to us directory ko PATH mein add karna padega.

[HOME Variable]

HOME variable aapka home directory batata hai.

    echo $HOME
    # Output: /data/data/com.termux/files/home

Iska matlab hai:
- ~ (tilde) ka meaning HOME hai
- cd ~ se aap home pe ja sakte ho
- Aapki personal files yahan hoti hain

[PREFIX Variable]

PREFIX Termux-specific variable hai. Ye batata hai ki Termux
files kahan installed hain.

    echo $PREFIX
    # Output: /data/data/com.termux/files/usr

PREFIX ke andar:
- $PREFIX/bin - Executables (python, bash, git)
- $PREFIX/lib - Libraries
- $PREFIX/etc - Configuration files
- $PREFIX/share - Documentation

[SHELL Variable]

SHELL variable batata hai ki aapka default shell kya hai.

    echo $SHELL
    # Output: /data/data/com.termux/files/usr/bin/bash

Agar aap zsh install karte ho, to ye change ho sakta hai.

[USER Variable]

USER variable current user ka naam batata hai.

    echo $USER
    # Output: u0_a123 (ya similar)

Termux mein har app ka ek unique user ID hota hai Android
security ke karan.

[TERM Variable]

TERM variable terminal type batata hai. Ye important hai
colors aur terminal features ke liye.

    echo $TERM
    # Output: xterm-256color

xterm-256color matlab aapko 256 colors support hai.

[TMPDIR Variable]

TMPDIR temporary files ka location batata hai.

    echo $TMPDIR
    # Output: /data/data/com.termux/files/usr/tmp

Ye directory temporary storage ke liye use hoti hai.

---

[SECTION 3: VIEWING ENVIRONMENT VARIABLES - 8:00 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain ki environment variables ko kaise view karein.

[Method 1: echo command]

Sabse simple tarika - echo with $ symbol:

    echo $HOME
    echo $PATH
    echo $SHELL

Important: Variable name se pehle $ lagana zaruri hai.
$HOME - correct
HOME - ye variable ki value nahi, sirf naam print karega

[Method 2: env command]

env command SAARI environment variables dikhati hai:

    env

Ye bahut lambi output dega. Filter ke liye:

    env | grep HOME
    env | grep PATH
    env | grep TERM

[Method 3: printenv command]

printenv bhi env jaisa hai:

    printenv

Specific variable ke liye:

    printenv HOME
    printenv PATH
    printenv USER

printenv ka fayda: $ symbol ki zarurat nahi.

[Method 4: set command]

set command SAARE variables dikhati hai - environment + shell:

    set

Ye environment variables se zyada output dega.

Sirf variable names dekhne ke liye:

    set | grep -E '^[A-Z_]+='

[Method 5: declare command]

declare command variables ko formatted mein dikhata hai:

    declare -p

Ye bhi saare variables dikhata hai with attributes.

[Quick Comparison]

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMANDS TO VIEW VARIABLES                            │
├─────────────────┬───────────────────────────────────────────────────────┤
│ Command         │ Description                                          │
├─────────────────┼───────────────────────────────────────────────────────┤
│ echo $VAR       │ Single variable value                                │
│ env             │ All environment variables                            │
│ printenv        │ All environment variables                            │
│ printenv VAR    │ Specific variable (no $ needed)                      │
│ set             │ All variables (environment + shell)                  │
│ declare -p      │ All variables with attributes                        │
└─────────────────┴───────────────────────────────────────────────────────┘

---

[SECTION 4: SETTING ENVIRONMENT VARIABLES - 11:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Ab seekhte hain variables ko kaise set karein.

[Temporary Variables]

Temporary variables sirf current session ke liye rehte hain.
Terminal band karo, variable gayab.

Method 1: Direct assignment

    MY_VAR="Hello Termux"
    echo $MY_VAR

Method 2: export command

    export MY_VAR="Hello Termux"
    echo $MY_VAR

Difference kya hai?

Direct assignment (=) sirf current shell mein variable set karta hai.
export command variable ko child processes ko bhi pass karta hai.

Example:

    # Without export
    MY_TEST="test1"
    bash
    echo $MY_TEST    # Empty - variable not inherited

    # With export
    export MY_TEST="test2"
    bash
    echo $MY_TEST    # "test2" - variable inherited

[Modifying Existing Variables]

Variables ko modify karna:

    # Add to PATH
    export PATH="$PATH:/my/custom/path"

    # Prepend to PATH
    export PATH="/my/custom/path:$PATH"

    # Modify HOME (not recommended!)
    export HOME="/new/home"

[Setting Multiple Variables]

    export VAR1="value1" VAR2="value2" VAR3="value3"

Ya:

    export VAR1="value1"
    export VAR2="value2"
    export VAR3="value3"

[Variable with Spaces]

Agar value mein spaces hain, to quotes use karein:

    export MY_MESSAGE="Hello World from Termux"

[Variable Expansion]

Ek variable ko dusre mein use karna:

    export FIRST="Hello"
    export SECOND="$FIRST World"
    echo $SECOND    # Output: Hello World

---

[SECTION 5: PERMANENT VS TEMPORARY VARIABLES - 14:00 to 16:30]
─────────────────────────────────────────────────────────────────────────────

Ab samjhte hain permanent aur temporary variables mein farak.

[Temporary Variables]

Jab aap terminal mein variable set karte ho, wo temporary hai.
Terminal close karo, variable delete.

    export TEMP_VAR="temporary"
    echo $TEMP_VAR    # Works
    # Close and reopen Termux
    echo $TEMP_VAR    # Empty!

[Permanent Variables]

Permanent ke liye configuration files use karni padti hain.

Configuration files:
- ~/.bashrc - Interactive shell configuration
- ~/.bash_profile - Login shell configuration
- ~/.profile - Generic profile (if .bash_profile doesn't exist)
- ~/.zshrc - For zsh shell

[Setting Permanent Variables]

Step 1: Open .bashrc

    nano ~/.bashrc

Step 2: Add variable at the end

    # My custom variables
    export MY_PROJECT="/sdcard/projects"
    export EDITOR="nano"
    export BROWSER="firefox"

Step 3: Save and exit (Ctrl+X, Y, Enter)

Step 4: Reload configuration

    source ~/.bashrc

Ya:

    . ~/.bashrc

Step 5: Verify

    echo $MY_PROJECT

Ab ye variable har baar Termux open karne pe available hoga!

[Which File to Use?]

┌─────────────────────────────────────────────────────────────────────────┐
│                    CONFIGURATION FILES GUIDE                             │
├────────────────────┬────────────────────────────────────────────────────┤
│ File               │ When to Use                                       │
├────────────────────┼────────────────────────────────────────────────────┤
│ ~/.bashrc          │ Interactive shell, aliases, functions             │
│ ~/.bash_profile    │ Login shell, PATH, environment variables          │
│ ~/.profile         │ If .bash_profile doesn't exist                    │
│ ~/.zshrc           │ If using zsh instead of bash                      │
└────────────────────┴────────────────────────────────────────────────────┘

Termux mein usually .bashrc use karte hain.

---

[SECTION 6: PS1 CUSTOMIZATION - 16:30 to 18:30]
─────────────────────────────────────────────────────────────────────────────

PS1 variable aapka terminal prompt control karta hai.

Default Termux prompt:
    ~ $

PS1 change karna:

    export PS1="termux> "

Ab prompt aisa dikhega:
    termux>

[PS1 Special Characters]

┌─────────────────────────────────────────────────────────────────────────┐
│                    PS1 SPECIAL CHARACTERS                                │
├──────────────┬──────────────────────────────────────────────────────────┤
│ Character    │ Shows                                                    │
├──────────────┼──────────────────────────────────────────────────────────┤
│ \u           │ Username                                                 │
│ \h           │ Hostname                                                 │
│ \w           │ Current directory (full path)                            │
│ \W           │ Current directory (name only)                            │
│ \d           │ Date                                                     │
│ \t           │ Time (24-hour)                                           │
│ \T           │ Time (12-hour)                                           │
│ \n           │ Newline                                                  │
│ \$           │ $ for user, # for root                                   │
│ \[           │ Start of non-printing characters                         │
│ \]           │ End of non-printing characters                           │
└──────────────┴──────────────────────────────────────────────────────────┘

[PS1 Examples]

    # Simple prompt
    export PS1="termux\$ "

    # With username and directory
    export PS1="\u:\w\$ "

    # With time
    export PS1="[\t] \w\$ "

    # Colored prompt (green)
    export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

    # Fancy prompt with git branch (requires function)
    export PS1="\[\033[1;34m\]\w\[\033[0;33m\]\$(git branch 2>/dev/null | grep '*')\[\033[00m\]\$ "

[Permanent PS1]

PS1 ko .bashrc mein add karein:

    echo 'export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "' >> ~/.bashrc
    source ~/.bashrc

---

[SECTION 7: PATH MODIFICATION - 18:30 to 20:00]
─────────────────────────────────────────────────────────────────────────────

PATH modification bahut common hai jab aap custom tools banate ho.

[Current PATH dekho]

    echo $PATH

[Add Directory to PATH]

Temporarily:

    export PATH="$PATH:/path/to/directory"

Example - custom scripts folder:

    mkdir -p ~/my-scripts
    echo '#!/bin/bash' > ~/my-scripts/hello
    echo 'echo "Hello from my script!"' >> ~/my-scripts/hello
    chmod +x ~/my-scripts/hello
    export PATH="$PATH:$HOME/my-scripts"
    hello    # Runs your script!

[Permanent PATH Addition]

Add to .bashrc:

    echo 'export PATH="$PATH:$HOME/my-scripts"' >> ~/.bashrc
    source ~/.bashrc

[Prepend vs Append]

    # Append (add at end) - less priority
    export PATH="$PATH:/new/path"

    # Prepend (add at beginning) - more priority
    export PATH="/new/path:$PATH"

Prepend use karein jab aap system command ko override karna chahte ho.

[Remove from PATH]

PATH se remove karna tricky hai, ye function use karein:

    remove_from_path() {
        export PATH=$(echo "$PATH" | sed -e "s|:$1||g" -e "s|^$1:||g")
    }

    remove_from_path "/path/to/remove"

---

[SECTION 8: CREATING CUSTOM VARIABLES - 20:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Custom variables aapke kaam ko easy bana sakte hain.

[Useful Custom Variables]

    # Project directories
    export PROJECTS="/sdcard/Projects"
    export SCRIPTS="$HOME/scripts"

    # API Keys (be careful with security!)
    export MY_API_KEY="your-api-key-here"

    # Editor preferences
    export EDITOR="nano"
    export VISUAL="nano"

    # Default browser
    export BROWSER="firefox"

    # Custom settings
    export MY_NAME="T3rmuxk1ng"
    export MY_EMAIL="contact@example.com"

[Using Variables in Scripts]

script.sh:
    #!/bin/bash
    echo "Welcome, $MY_NAME!"
    echo "Your project is at: $PROJECTS"
    echo "Editor: $EDITOR"

[Best Practices for Custom Variables]

1. UPPERCASE names for environment variables
2. lowercase for local shell variables
3. Descriptive names: MY_PROJECT_DIR instead of MPD
4. Don't overwrite system variables

---

[SECTION 9: UNSETTING VARIABLES - 21:30 to 22:30]
─────────────────────────────────────────────────────────────────────────────

Variable ko delete karna:

[unset command]

    export TEST_VAR="hello"
    echo $TEST_VAR    # Output: hello
    unset TEST_VAR
    echo $TEST_VAR    # Output: (empty)

[Unset from environment but keep as shell variable]

    export MY_VAR="test"
    declare +x MY_VAR    # Remove export attribute
    # Now it's only a shell variable, not environment

[Clear all variables (DANGEROUS!)]

    unset $(env | awk -F= '{print $1}')

WARNING: Ye sab environment variables delete kar dega!
Termux restart karna padega recovery ke liye.

---

[SECTION 10: SUMMARY & NEXT PREVIEW - 22:30 to 24:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 7 complete! Let's summarize:

✅ Environment variables kya hai - key-value pairs jo system configure karti hain
✅ Important variables - PATH, HOME, PREFIX, SHELL, USER, TERM, TMPDIR
✅ Viewing variables - echo $VAR, env, printenv, set
✅ Setting variables - export, direct assignment
✅ Permanent variables - .bashrc configuration
✅ PS1 customization - terminal prompt design
✅ PATH modification - custom directories
✅ Custom variables - apne variables banana
✅ Unsetting variables - delete karna

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 7 - IMPORTANT COMMANDS                        │
├─────────────────────────────────────────────────────────────────────────┤
│ echo $VAR           │ View variable value                               │
│ env                 │ List all environment variables                    │
│ printenv VAR        │ View specific variable                            │
│ export VAR="value"  │ Set environment variable                          │
│ unset VAR           │ Delete variable                                   │
│ source ~/.bashrc    │ Reload configuration                              │
│ export PS1="..."    │ Customize prompt                                  │
│ export PATH="$PATH:... │ Add to PATH                                   │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 8 mein hum seekhenge:
- Text editors in Termux
- Nano editor complete guide
- Vim basics
- Editor comparison
- Productivity tips

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 8!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. What Are Environment Variables?

Environment variables are dynamic named values that affect the behavior of running processes. They exist in every Unix-like operating system and provide a way to store system-wide information that programs can access.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ENVIRONMENT VARIABLES ARCHITECTURE                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android/Linux Kernel                          │   │
│   │   (System-level environment)                                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Termux Application                           │   │
│   │   - Sets PREFIX, HOME, TMPDIR                                   │   │
│   │   - Configures PATH for Termux binaries                         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Shell (Bash/Zsh)                             │   │
│   │   - Reads .bashrc / .zshrc                                      │   │
│   │   - Sets PS1, HISTSIZE, aliases                                 │   │
│   │   - Inherits parent environment                                 │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Child Processes                              │   │
│   │   - Scripts, programs, tools                                    │   │
│   │   - Inherit exported variables                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Variable Types

| Type | Scope | Inheritance | Example |
|------|-------|-------------|---------|
| Environment Variable | All processes | Yes (if exported) | PATH, HOME |
| Shell Variable | Current shell only | No | PS1, HISTSIZE |
| Local Variable | Current function/script | No | local var |
| Readonly Variable | Cannot be modified | Varies | readonly VAR |

### 3. Important Termux Environment Variables

#### PATH Variable

```bash
# Current PATH
echo $PATH

# Termux default PATH
# /data/data/com.termux/files/usr/bin:/data/data/com.termux/files/usr/bin/applets

# How PATH works:
# When you type a command, shell searches each directory in PATH (left to right)
# First match is executed
# If not found: "command not found" error

# View PATH directories
echo "$PATH" | tr ':' '\n'
```

#### HOME Variable

```bash
# Home directory location
echo $HOME
# /data/data/com.termux/files/home

# Common uses
cd ~              # Go home
cd $HOME          # Go home
ls -la ~/         # List home contents
mkdir ~/projects  # Create in home
```

#### PREFIX Variable (Termux-Specific)

```bash
# Termux installation prefix
echo $PREFIX
# /data/data/com.termux/files/usr

# Navigate to Termux system
cd $PREFIX

# Explore structure
ls $PREFIX/
# bin  etc  include  lib  libexec  share  tmp  var

# Find executables
ls $PREFIX/bin/ | head -20
```

#### SHELL Variable

```bash
# Current shell
echo $SHELL
# /data/data/com.termux/files/usr/bin/bash

# Available shells
cat /etc/shells  # May not exist in Termux
ls $PREFIX/bin/*sh

# Change shell (requires chsh or manual config)
chsh -s $PREFIX/bin/zsh
```

#### USER Variable

```bash
# Current username
echo $USER
# u0_aXXX (Termux app-specific user)

# Related variables
echo $LOGNAME
echo $UID
id
```

#### TERM Variable

```bash
# Terminal type
echo $TERM
# xterm-256color

# Why it matters:
# - Determines color support
# - Affects cursor movement
# - Impacts text formatting
# - Used by programs like vim, htop

# Common values
# xterm          - Basic xterm
# xterm-256color - 256 color support
# screen         - For screen/tmux
# linux          - Linux console
```

#### TMPDIR Variable

```bash
# Temporary files directory
echo $TMPDIR
# /data/data/com.termux/files/usr/tmp

# Uses
# - Temporary files by scripts
# - Download buffers
# - Process communication

# Create if doesn't exist
mkdir -p $TMPDIR
```

### 4. Viewing Environment Variables

```bash
# Method 1: echo with $ prefix
echo $HOME
echo $PATH
echo ${PATH}    # Braces for safety

# Method 2: env command
env                    # All variables
env | grep -i path     # Filter
env | sort             # Sorted

# Method 3: printenv
printenv               # All variables
printenv HOME          # Specific variable
printenv HOME PATH     # Multiple variables

# Method 4: set command
set                    # All variables (shell + environment)
set | grep "^PATH"

# Method 5: declare
declare -p             # All with attributes
declare -p PATH        # Specific variable

# Method 6: printf (for formatting)
printf '%s\n' "$PATH"
```

### 5. Setting Environment Variables

```bash
# Basic assignment (shell variable)
MY_VAR="value"

# Export to environment
export MY_VAR="value"

# Combine
MY_VAR="value"
export MY_VAR

# Multiple exports
export VAR1="val1" VAR2="val2"

# Append to existing variable
export PATH="$PATH:/new/path"

# Prepend to existing variable
export PATH="/new/path:$PATH"

# Using variable in assignment
export FULL_PATH="$HOME/projects"

# Conditional assignment (set if not exists)
export MY_VAR="${MY_VAR:-default_value}"

# Readonly variable (cannot be changed)
readonly CONSTANT_VAR="never_changes"
```

### 6. Configuration Files

#### .bashrc

```bash
# Location: ~/.bashrc
# Purpose: Interactive shell configuration
# Loads: Every new terminal session

# Sample .bashrc content
┌─────────────────────────────────────────────────────────────────────────┐
│ # ~/.bashrc - Termux Bash Configuration                                 │
│                                                                          │
│ # If not running interactively, don't do anything                       │
│ [[ $- != *i* ]] && return                                                │
│                                                                          │
│ # Environment Variables                                                  │
│ export EDITOR="nano"                                                     │
│ export VISUAL="nano"                                                     │
│ export HISTSIZE=5000                                                     │
│ export HISTFILESIZE=10000                                                │
│ export HISTCONTROL=ignoreboth                                            │
│                                                                          │
│ # Custom Variables                                                       │
│ export PROJECTS="$HOME/projects"                                         │
│ export SCRIPTS="$HOME/scripts"                                           │
│ export PATH="$PATH:$HOME/scripts"                                        │
│                                                                          │
│ # Prompt Customization                                                   │
│ export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ ' │
│                                                                          │
│ # Aliases                                                                │
│ alias ll='ls -la'                                                        │
│ alias la='ls -A'                                                         │
│ alias l='ls -CF'                                                         │
│ alias ..='cd ..'                                                         │
│ alias ...='cd ../..'                                                     │
│ alias cls='clear'                                                        │
│ alias h='history'                                                        │
│                                                                          │
│ # Functions                                                              │
│ mkcd() {                                                                 │
│     mkdir -p "$1" && cd "$1"                                             │
│ }                                                                        │
│                                                                          │
│ # Welcome message                                                        │
│ echo "Welcome to Termux!"                                                │
│ echo "Today is $(date '+%A, %B %d, %Y')"                                 │
└─────────────────────────────────────────────────────────────────────────┘
```

#### .bash_profile

```bash
# Location: ~/.bash_profile
# Purpose: Login shell configuration
# Loads: Once at login

# Sample content
┌─────────────────────────────────────────────────────────────────────────┐
│ # ~/.bash_profile - Login Shell Configuration                           │
│                                                                          │
│ # Source .bashrc if exists                                               │
│ if [[ -f ~/.bashrc ]]; then                                              │
│     . ~/.bashrc                                                          │
│ fi                                                                       │
│                                                                          │
│ # Set PATH                                                               │
│ export PATH="$HOME/bin:$PATH"                                            │
│                                                                          │
│ # Start SSH agent (if needed)                                            │
│ # eval "$(ssh-agent -s)"                                                 │
└─────────────────────────────────────────────────────────────────────────┘
```

#### .profile

```bash
# Location: ~/.profile
# Purpose: Generic profile (used if .bash_profile doesn't exist)
# Loads: At login for any POSIX-compatible shell

# Sample content
┌─────────────────────────────────────────────────────────────────────────┐
│ # ~/.profile - Generic Shell Profile                                     │
│                                                                          │
│ # Set environment variables                                              │
│ export PATH="$HOME/bin:$PATH"                                            │
│ export EDITOR="nano"                                                     │
│                                                                          │
│ # Source .bashrc for interactive shells                                  │
│ if [[ -n "$BASH_VERSION" ]]; then                                        │
│     if [[ -f "$HOME/.bashrc" ]]; then                                    │
│         . "$HOME/.bashrc"                                                │
│     fi                                                                   │
│ fi                                                                       │
└─────────────────────────────────────────────────────────────────────────┘
```

### 7. PS1 Prompt Customization

```bash
# PS1 Special Characters Reference
┌─────────────────────────────────────────────────────────────────────────┐
│                    PS1 ESCAPE SEQUENCES                                  │
├──────────────┬──────────────────────────────────────────────────────────┤
│ Sequence     │ Description                                              │
├──────────────┼──────────────────────────────────────────────────────────┤
│ \a           │ ASCII bell character (07)                                │
│ \d           │ Date in "Weekday Month Date" format                      │
│ \D{format}   │ Date in strftime format                                  │
│ \e           │ ASCII escape character (033)                             │
│ \h           │ Hostname up to the first '.'                             │
│ \H           │ Hostname                                                 │
│ \j           │ Number of jobs currently managed by the shell            │
│ \l           │ Basename of the shell's terminal device name             │
│ \n           │ Newline                                                  │
│ \r           │ Carriage return                                          │
│ \s           │ Name of the shell, basename of $0                        │
│ \t           │ Current time in 24-hour HH:MM:SS format                  │
│ \T           │ Current time in 12-hour HH:MM:SS format                  │
│ \@           │ Current time in 12-hour am/pm format                     │
│ \A           │ Current time in 24-hour HH:MM format                     │
│ \u           │ Username of the current user                             │
│ \v           │ Version of bash (e.g., 4.4)                              │
│ \V           │ Release of bash, version + patch level (e.g., 4.4.23)    │
│ \w           │ Current working directory                                │
│ \W           │ Basename of the current working directory                │
│ \!           │ History number of this command                           │
│ \#           │ Command number of this command                           │
│ \$           │ If the effective UID is 0, a #, otherwise a $           │
│ \nnn         │ Character corresponding to the octal number nnn          │
│ \\           │ A backslash                                              │
│ \[           │ Begin a sequence of non-printing characters              │
│ \]           │ End a sequence of non-printing characters                │
└──────────────┴──────────────────────────────────────────────────────────┘
```

```bash
# Color Codes for PS1
┌─────────────────────────────────────────────────────────────────────────┐
│                    ANSI COLOR CODES                                      │
├──────────────┬──────────────────────────────────────────────────────────┤
│ Color        │ Foreground Code    │ Background Code                      │
├──────────────┼────────────────────┼──────────────────────────────────────┤
│ Black        │ \[\033[0;30m\]     │ \[\033[0;40m\]                       │
│ Red          │ \[\033[0;31m\]     │ \[\033[0;41m\]                       │
│ Green        │ \[\033[0;32m\]     │ \[\033[0;42m\]                       │
│ Yellow       │ \[\033[0;33m\]     │ \[\033[0;43m\]                       │
│ Blue         │ \[\033[0;34m\]     │ \[\033[0;44m\]                       │
│ Magenta      │ \[\033[0;35m\]     │ \[\033[0;45m\]                       │
│ Cyan         │ \[\033[0;36m\]     │ \[\033[0;46m\]                       │
│ White        │ \[\033[0;37m\]     │ \[\033[0;47m\]                       │
├──────────────┼────────────────────┼──────────────────────────────────────┤
│ Bold Black   │ \[\033[1;30m\]     │ \[\033[1;40m\]                       │
│ Bold Red     │ \[\033[1;31m\]     │ \[\033[1;41m\]                       │
│ Bold Green   │ \[\033[1;32m\]     │ \[\033[1;42m\]                       │
│ Bold Yellow  │ \[\033[1;33m\]     │ \[\033[1;43m\]                       │
│ Bold Blue    │ \[\033[1;34m\]     │ \[\033[1;44m\]                       │
│ Bold Magenta │ \[\033[1;35m\]     │ \[\033[1;45m\]                       │
│ Bold Cyan    │ \[\033[1;36m\]     │ \[\033[1;46m\]                       │
│ Bold White   │ \[\033[1;37m\]     │ \[\033[1;47m\]                       │
├──────────────┼────────────────────┼──────────────────────────────────────┤
│ Reset        │ \[\033[0m\]        │                                      │
└──────────────┴────────────────────┴──────────────────────────────────────┘
```

```bash
# PS1 Examples

# Example 1: Simple prompt
export PS1="termux\$ "

# Example 2: Username and directory
export PS1="\u:\w\$ "

# Example 3: Full path with username
export PS1="\u@\h:\w\$ "

# Example 4: With time
export PS1="[\t] \w\$ "

# Example 5: Green username, blue directory
export PS1="\[\033[01;32m\]\u\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

# Example 6: Two-line prompt
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\n\$ "

# Example 7: With git branch (requires git)
export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[33m\]$(git branch 2>/dev/null | grep "\*" | sed "s/\* //")\[\033[00m\]\$ '

# Example 8: Minimal with arrow
export PS1="➜ \W \$ "

# Example 9: Emoji prompt
export PS1="🚀 \w \$ "

# Example 10: Full featured with colors
export PS1="\[\033[0;36m\][\[\033[0;33m\]\t\[\033[0;36m\]] \[\033[1;32m\]\u\[\033[0m\]@\[\033[1;34m\]\h\[\033[0m\]:\[\033[1;35m\]\w\[\033[0m\]\$ "
```

### 8. PATH Modification

```bash
# View current PATH
echo $PATH

# Parse PATH into lines
echo "$PATH" | tr ':' '\n'

# Count PATH entries
echo "$PATH" | tr ':' '\n' | wc -l

# Check if directory is in PATH
[[ ":$PATH:" == *":/my/path:"* ]] && echo "Found" || echo "Not found"

# Add to end of PATH (low priority)
export PATH="$PATH:/new/directory"

# Add to beginning of PATH (high priority)
export PATH="/new/directory:$PATH"

# Add multiple directories
export PATH="$PATH:$HOME/bin:$HOME/scripts"

# Function to safely add to PATH
add_to_path() {
    if [[ ":$PATH:" != *":$1:"* ]]; then
        export PATH="$PATH:$1"
    fi
}
add_to_path "$HOME/my-scripts"

# Function to remove from PATH
remove_from_path() {
    local new_path
    new_path=$(echo "$PATH" | sed -e "s|$1:\{0,1\}||" -e "s|:\{0,1\}$1||")
    export PATH="$new_path"
}

# Function to check if command exists in PATH
command_exists() {
    command -v "$1" >/dev/null 2>&1
}

# Find where a command is located
which python
type python
command -v python
```

### 9. Creating Custom Variables

```bash
# Project paths
export PROJECT_HOME="$HOME/projects"
export PYTHON_PROJECTS="$PROJECT_HOME/python"
export WEB_PROJECTS="$PROJECT_HOME/web"

# Development settings
export DEV_MODE="true"
export DEBUG_LEVEL="2"

# API configurations
export API_BASE_URL="https://api.example.com"
export API_TIMEOUT="30"

# Editor preferences
export EDITOR="nano"
export VISUAL="nano"
export PAGER="less"

# Browser
export BROWSER="firefox"

# Locale
export LANG="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"

# History settings
export HISTSIZE=5000
export HISTFILESIZE=10000
export HISTCONTROL=ignoreboth:erasedups
export HISTIGNORE="ls:cd:cd -:pwd:exit:date:* --help"

# Less configuration
export LESS="-R"
export LESSHISTFILE=-

# Node.js (if using nvm)
export NVM_DIR="$HOME/.nvm"

# Python
export PYTHONSTARTUP="$HOME/.pythonrc"
export PYTHONDONTWRITEBYTECODE=1

# Java (if needed)
export JAVA_HOME="/data/data/com.termux/files/usr/lib/jvm/java-17-openjdk"

# Custom functions as variables
export TODAY=$(date +%Y-%m-%d)
export NOW=$(date +%H:%M:%S)
```

### 10. Unsetting Variables

```bash
# Basic unset
unset MY_VAR

# Unset multiple variables
unset VAR1 VAR2 VAR3

# Unset function
unset -f my_function

# Remove export attribute but keep value
declare +x MY_VAR

# Check if variable is set
[[ -v MY_VAR ]] && echo "Set" || echo "Not set"
[[ -z "${MY_VAR+x}" ]] && echo "Not set" || echo "Set"

# Unset all variables matching pattern (DANGEROUS)
# unset ${!MY_PREFIX_*}

# Clear environment (VERY DANGEROUS - for demonstration only)
# exec env -i HOME="$HOME" TERM="$TERM" bash --norc --noprofile
```

---

## 💻 25+ PRACTICAL EXAMPLES

### Example 1: View All Environment Variables

```bash
# Basic view
env

# Sorted view
env | sort

# Filter specific variable
env | grep -i path

# Beautiful output
env | column -t -s '='
```

### Example 2: Check Variable Exists

```bash
# Method 1: Using -v test
[[ -v HOME ]] && echo "HOME is set" || echo "HOME not set"

# Method 2: Using parameter expansion
[[ -n "${HOME+x}" ]] && echo "HOME is set" || echo "HOME not set"

# Method 3: Using printenv
printenv HOME >/dev/null 2>&1 && echo "HOME is set" || echo "HOME not set"

# Method 4: Simple echo test
if [[ -n "$HOME" ]]; then
    echo "HOME is set to: $HOME"
else
    echo "HOME is not set"
fi
```

### Example 3: Set and Use Custom Variable

```bash
# Set variable
export MY_PROJECT="$HOME/projects/myapp"

# Use in command
cd $MY_PROJECT

# Use in script
echo "Project location: $MY_PROJECT"

# Use with braces (safer)
echo "Project: ${MY_PROJECT}"
ls "${MY_PROJECT}/src"
```

### Example 4: Modify PATH Temporarily

```bash
# Add custom scripts directory
export PATH="$PATH:$HOME/scripts"

# Verify
echo $PATH

# Test with custom script
echo '#!/bin/bash' > ~/scripts/hello
echo 'echo "Hello from custom script!"' >> ~/scripts/hello
chmod +x ~/scripts/hello
hello
```

### Example 5: Modify PATH Permanently

```bash
# Add to .bashrc
echo 'export PATH="$PATH:$HOME/scripts"' >> ~/.bashrc

# Reload configuration
source ~/.bashrc

# Verify
echo $PATH | tr ':' '\n' | grep scripts
```

### Example 6: Create Simple Prompt

```bash
# Minimal prompt
export PS1="termux\$ "

# With current directory
export PS1="\W \$ "

# With full path
export PS1="\w \$ "

# With username
export PS1="\u:\w\$ "
```

### Example 7: Create Colorful Prompt

```bash
# Green prompt
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

# Red, green, blue combination
export PS1="\[\033[0;31m\][\[\033[0;32m\]\w\[\033[0;31m\]]\[\033[0m\]\$ "

# Yellow username, cyan path
export PS1="\[\033[1;33m\]\u\[\033[0m\]:\[\033[1;36m\]\w\[\033[0m\]\$ "
```

### Example 8: Prompt with Git Branch

```bash
# Add to .bashrc
parse_git_branch() {
    git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\]\$ "
```

### Example 9: Prompt with Time

```bash
# Time and directory
export PS1="[\t] \w\$ "

# Date and time
export PS1="[\d \t] \$ "

# Full datetime
export PS1="[$(date '+%Y-%m-%d %H:%M:%S')] \$ "
```

### Example 10: Two-Line Prompt

```bash
# First line: user and path, second line: prompt
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\n\$ "

# With separator
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\n└─\$ "
```

### Example 11: Set Editor Variable

```bash
# Set nano as default editor
export EDITOR="nano"
export VISUAL="nano"

# Set vim as default (if installed)
export EDITOR="vim"
export VISUAL="vim"

# Use in scripts
$EDITOR myfile.txt
```

### Example 12: Configure History

```bash
# Set history size
export HISTSIZE=5000
export HISTFILESIZE=10000

# Ignore duplicates and spaces
export HISTCONTROL=ignoreboth

# Ignore specific commands
export HISTIGNORE="ls:cd:pwd:exit:clear"

# Timestamp in history
export HISTTIMEFORMAT="%F %T "

# View history
history
```

### Example 13: Create Configuration File

```bash
# Create .bashrc
cat > ~/.bashrc << 'EOF'
# Termux Configuration
# Created by T3rmuxk1ng

# Environment Variables
export EDITOR="nano"
export HISTSIZE=5000
export PATH="$PATH:$HOME/scripts"

# Custom Variables
export PROJECTS="$HOME/projects"
export MY_NAME="TermuxUser"

# Prompt
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

# Aliases
alias ll='ls -la'
alias la='ls -A'
alias cls='clear'

# Welcome message
echo "Welcome to Termux, $MY_NAME!"
EOF

# Reload
source ~/.bashrc
```

### Example 14: Use Variables in Script

```bash
#!/bin/bash
# Script: backup.sh

# Use environment variables
BACKUP_DIR="${BACKUP_DIR:-$HOME/backups}"
DATE=$(date +%Y%m%d)

echo "Backing up to: $BACKUP_DIR"
echo "Date: $DATE"

# Create backup directory
mkdir -p "$BACKUP_DIR"

# Backup
tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" -C "$HOME" .
echo "Backup complete!"
```

### Example 15: Conditional Variable Assignment

```bash
# Set default if not defined
export MY_VAR="${MY_VAR:-default_value}"

# Set and use
export CONFIG_FILE="${CONFIG_FILE:-$HOME/config.yml}"
echo "Config file: $CONFIG_FILE"

# Alternative syntax
export PORT="${PORT:=8080}"
echo "Port: $PORT"
```

### Example 16: Export Multiple Variables

```bash
# Method 1: Multiple exports
export VAR1="value1"
export VAR2="value2"
export VAR3="value3"

# Method 2: Single line
export VAR1="value1" VAR2="value2" VAR3="value3"

# Method 3: From file
cat > env_vars << 'EOF'
export DB_HOST="localhost"
export DB_PORT="5432"
export DB_NAME="mydb"
EOF
source env_vars
```

### Example 17: List Variables by Prefix

```bash
# Set some variables
export MY_VAR1="a"
export MY_VAR2="b"
export MY_VAR3="c"

# List all MY_ variables
echo "${!MY_*}"

# Use in loop
for var in "${!MY_*}"; do
    echo "$var = ${!var}"
done
```

### Example 18: Safely Add Directory to PATH

```bash
# Function to safely add to PATH
add_path() {
    local dir="$1"
    if [[ -d "$dir" ]]; then
        if [[ ":$PATH:" != *":$dir:"* ]]; then
            export PATH="$PATH:$dir"
            echo "Added $dir to PATH"
        else
            echo "$dir already in PATH"
        fi
    else
        echo "Directory $dir does not exist"
    fi
}

# Usage
add_path "$HOME/scripts"
add_path "$HOME/.local/bin"
```

### Example 19: Remove Directory from PATH

```bash
# Function to remove from PATH
remove_path() {
    local dir="$1"
    local new_path=""

    IFS=':' read -ra PATHS <<< "$PATH"
    for p in "${PATHS[@]}"; do
        if [[ "$p" != "$dir" ]]; then
            new_path="${new_path:+$new_path:}$p"
        fi
    done

    export PATH="$new_path"
    echo "Removed $dir from PATH"
}

# Usage
remove_path "/old/directory"
```

### Example 20: Create Project Environment

```bash
#!/bin/bash
# setup_project.sh - Set up project environment

PROJECT_NAME="${1:-myproject}"
PROJECT_ROOT="$HOME/projects/$PROJECT_NAME"

# Create project structure
mkdir -p "$PROJECT_ROOT"/{src,tests,docs,config}

# Set environment variables
export PROJECT_ROOT
export PROJECT_NAME
export SRC_DIR="$PROJECT_ROOT/src"
export TEST_DIR="$PROJECT_ROOT/tests"
export CONFIG_DIR="$PROJECT_ROOT/config"

# Create .env file
cat > "$PROJECT_ROOT/.env" << EOF
export PROJECT_ROOT="$PROJECT_ROOT"
export PROJECT_NAME="$PROJECT_NAME"
export SRC_DIR="$SRC_DIR"
export TEST_DIR="$TEST_DIR"
export CONFIG_DIR="$CONFIG_DIR"
export PYTHONPATH="$SRC_DIR"
EOF

echo "Project $PROJECT_NAME created at $PROJECT_ROOT"
echo "Run: source $PROJECT_ROOT/.env"
```

### Example 21: Use Array Variables

```bash
# Array of paths
export MY_PATHS=("$HOME/bin" "$HOME/scripts" "/opt/bin")

# Add each to PATH
for p in "${MY_PATHS[@]}"; do
    export PATH="$PATH:$p"
done

# Array of servers
export SERVERS=("server1.example.com" "server2.example.com" "server3.example.com")

# Use in loop
for server in "${SERVERS[@]}"; do
    echo "Connecting to $server..."
done
```

### Example 22: Debug Variable Expansion

```bash
# Enable debug mode
set -x

# Commands will show variable expansion
echo $HOME
echo $PATH

# Disable debug mode
set +x

# Or use for specific section
(
    set -x
    export TEST="value"
    echo $TEST
)
```

### Example 23: Save and Restore Environment

```bash
# Save current environment
env > ~/environment_backup.txt

# Or specific variables
printenv HOME PATH SHELL > ~/important_vars.txt

# Restore from file
while IFS='=' read -r name value; do
    export "$name=$value"
done < ~/important_vars.txt
```

### Example 24: Check for Sensitive Variables

```bash
#!/bin/bash
# check_secrets.sh - Check for sensitive variables

sensitive_vars=("PASSWORD" "SECRET" "API_KEY" "TOKEN" "PRIVATE_KEY")

for var in "${sensitive_vars[@]}"; do
    if [[ -n "${!var}" ]]; then
        echo "WARNING: $var is set!"
    fi
done
```

### Example 25: Dynamic PS1 with Exit Code

```bash
# Show last exit code in prompt
export PS1='$(if [[ $? -eq 0 ]]; then echo "\[\033[01;32m\]✓\[\033[00m\]"; else echo "\[\033[01;31m\]✗\[\033[00m\]"; fi) \[\033[01;34m\]\w\[\033[00m\]\$ '

# Green checkmark for success, red X for failure
```

### Example 26: Environment Variables for Python

```bash
# Python-specific variables
export PYTHONSTARTUP="$HOME/.pythonrc"
export PYTHONPATH="$HOME/projects/lib"
export PYTHONDONTWRITEBYTECODE=1
export PYTHONUNBUFFERED=1

# Virtual environment
export VIRTUAL_ENV="$HOME/venv"
export PATH="$VIRTUAL_ENV/bin:$PATH"
```

### Example 27: Environment Variables for Node.js

```bash
# Node.js variables
export NODE_PATH="$HOME/.npm-global/lib/node_modules"
export NODE_ENV="development"
export NPM_CONFIG_PREFIX="$HOME/.npm-global"

# Add npm global bin to PATH
export PATH="$HOME/.npm-global/bin:$PATH"
```

### Example 28: Quick Variable Backup and Restore

```bash
#!/bin/bash
# var_manager.sh - Variable backup and restore utility

BACKUP_FILE="$HOME/.var_backup"

backup_vars() {
    printenv > "$BACKUP_FILE"
    echo "Environment backed up to $BACKUP_FILE"
}

restore_vars() {
    if [[ -f "$BACKUP_FILE" ]]; then
        while IFS='=' read -r name value; do
            export "$name=$value"
        done < "$BACKUP_FILE"
        echo "Environment restored from $BACKUP_FILE"
    else
        echo "No backup file found"
    fi
}

case "$1" in
    backup) backup_vars ;;
    restore) restore_vars ;;
    *) echo "Usage: $0 {backup|restore}" ;;
esac
```

### Example 29: Show Variable Changes

```bash
#!/bin/bash
# watch_vars.sh - Watch for variable changes

echo "Current PATH:"
echo "$PATH"
echo
echo "Press Ctrl+C to stop"
echo

old_path="$PATH"
while true; do
    sleep 1
    if [[ "$PATH" != "$old_path" ]]; then
        echo "$(date): PATH changed!"
        echo "Old: $old_path"
        echo "New: $PATH"
        old_path="$PATH"
    fi
done
```

### Example 30: Create Environment File for Projects

```bash
#!/bin/bash
# create_env_file.sh

PROJECT_DIR="${1:-$HOME/projects/myproject}"
ENV_FILE="$PROJECT_DIR/.env"

cat > "$ENV_FILE" << 'EOF'
# Development Environment Configuration
# Copy this file to .env.local for local overrides

# Application
export APP_NAME="MyApp"
export APP_ENV="development"
export APP_DEBUG="true"

# Paths
export PROJECT_ROOT="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
export LOG_DIR="$PROJECT_ROOT/logs"
export TMP_DIR="$PROJECT_ROOT/tmp"

# Database
export DB_HOST="localhost"
export DB_PORT="5432"
export DB_NAME="myapp_dev"
export DB_USER="devuser"
export DB_PASSWORD="devpass"

# API
export API_URL="https://api.example.com"
export API_KEY="your-api-key-here"

# Server
export SERVER_HOST="0.0.0.0"
export SERVER_PORT="8080"
EOF

echo "Created $ENV_FILE"
echo "Edit it to customize your environment"
```

---

## 📋 COMMANDS REFERENCE

### Viewing Variables

```bash
# View single variable
echo $HOME
echo ${HOME}

# View all environment variables
env
printenv

# View specific variable
printenv HOME
printenv PATH

# View all variables (environment + shell)
set

# View variables with attributes
declare -p

# View function definitions
declare -f

# View variable names only
env | cut -d= -f1

# View sorted
env | sort
```

### Setting Variables

```bash
# Set shell variable
VAR="value"

# Set environment variable
export VAR="value"

# Set and export separately
VAR="value"
export VAR

# Set multiple variables
export A="1" B="2" C="3"

# Append to variable
export PATH="$PATH:/new/path"

# Prepend to variable
export PATH="/new/path:$PATH"

# Set with default value
export VAR="${VAR:-default}"

# Set readonly variable
readonly CONSTANT="value"

# Declare with attributes
declare -i NUMBER=10     # Integer
declare -a ARRAY=(1 2 3) # Array
declare -r READONLY="x"  # Readonly
declare -x EXPORT="y"    # Export
```

### Unsetting Variables

```bash
# Unset variable
unset VAR

# Unset multiple
unset VAR1 VAR2 VAR3

# Unset function
unset -f function_name

# Remove export attribute
declare +x VAR

# Check if unset
[[ -v VAR ]] && echo "Set" || echo "Not set"
```

### Configuration Files

```bash
# Create .bashrc
nano ~/.bashrc

# Reload .bashrc
source ~/.bashrc
. ~/.bashrc

# Edit .profile
nano ~/.profile

# Check if file exists
[[ -f ~/.bashrc ]] && echo "Exists"

# View current config
cat ~/.bashrc
```

### PATH Management

```bash
# View PATH
echo $PATH
echo "$PATH" | tr ':' '\n'

# Add to PATH (temporary)
export PATH="$PATH:/new/dir"

# Add to PATH (permanent)
echo 'export PATH="$PATH:$HOME/scripts"' >> ~/.bashrc
source ~/.bashrc

# Check if in PATH
[[ ":$PATH:" == *":$dir:"* ]] && echo "In PATH"

# Find command location
which python
type python
command -v python
```

### PS1 Prompt

```bash
# Simple prompt
export PS1="\$ "

# With directory
export PS1="\w \$ "

# With username and host
export PS1="\u@\h:\w\$ "

# Color prompt
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

# Make permanent
echo 'export PS1="..."' >> ~/.bashrc
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Variable Operations

```bash
# Task: Create, view, modify, and delete variables

# Step 1: Create a variable
export MY_NAME="YourName"

# Step 2: View the variable
echo $MY_NAME

# Step 3: Modify the variable
export MY_NAME="NewName"

# Step 4: Create another variable using the first
export GREETING="Hello, $MY_NAME!"

# Step 5: View both variables
echo $MY_NAME
echo $GREETING

# Step 6: Delete the greeting variable
unset GREETING

# Step 7: Verify deletion
echo $GREETING  # Should be empty

# Expected: Understanding of variable creation, usage, and deletion
```

### Exercise 2: PATH Manipulation

```bash
# Task: Add a custom scripts directory to PATH

# Step 1: Create scripts directory
mkdir -p ~/my-scripts

# Step 2: Create a test script
cat > ~/my-scripts/hello << 'EOF'
#!/bin/bash
echo "Hello from my custom script!"
echo "Current time: $(date)"
echo "User: $USER"
EOF

# Step 3: Make executable
chmod +x ~/my-scripts/hello

# Step 4: Add to PATH
export PATH="$PATH:$HOME/my-scripts"

# Step 5: Test
hello

# Step 6: Make permanent
echo 'export PATH="$PATH:$HOME/my-scripts"' >> ~/.bashrc

# Expected: Script runs from anywhere
```

### Exercise 3: PS1 Customization

```bash
# Task: Create a custom prompt

# Step 1: Try different prompts
export PS1="termux\$ "
export PS1="\w\$ "
export PS1="\u@\h:\w\$ "

# Step 2: Create a colorful prompt
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

# Step 3: Create a two-line prompt
export PS1="\[\033[01;33m\]\u in \w\[\033[00m\]\n\$ "

# Step 4: Make your favorite permanent
nano ~/.bashrc
# Add your PS1 line at the end

# Step 5: Reload
source ~/.bashrc

# Expected: Customized prompt that suits your style
```

### Exercise 4: Configuration File Setup

```bash
# Task: Set up a complete .bashrc file

# Step 1: Backup existing .bashrc
[[ -f ~/.bashrc ]] && cp ~/.bashrc ~/.bashrc.backup

# Step 2: Create new .bashrc
cat > ~/.bashrc << 'EOF'
# Termux Configuration
# Created on: $(date)

# ===== Environment Variables =====
export EDITOR="nano"
export VISUAL="nano"
export PAGER="less"

# ===== History Settings =====
export HISTSIZE=5000
export HISTFILESIZE=10000
export HISTCONTROL=ignoreboth
export HISTTIMEFORMAT="%F %T "

# ===== Custom Variables =====
export PROJECTS="$HOME/projects"
export SCRIPTS="$HOME/scripts"
export DOWNLOADS="$HOME/storage/downloads"

# ===== PATH =====
export PATH="$PATH:$HOME/scripts"

# ===== Prompt =====
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

# ===== Aliases =====
alias ll='ls -la'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias cls='clear'
alias h='history'
alias grep='grep --color=auto'

# ===== Functions =====
mkcd() {
    mkdir -p "$1" && cd "$1"
}

# ===== Welcome Message =====
clear
echo "Welcome to Termux!"
echo "Today is $(date '+%A, %B %d, %Y at %H:%M')"
echo "Current directory: $(pwd)"
echo ""
EOF

# Step 3: Reload configuration
source ~/.bashrc

# Expected: Fully configured Termux environment
```

### Exercise 5: Environment Debugging

```bash
# Task: Debug environment variable issues

# Step 1: Create test variable
export TEST_VAR="test_value"

# Step 2: Verify it exists
printenv TEST_VAR
env | grep TEST_VAR

# Step 3: Check in subshell
bash -c 'echo $TEST_VAR'

# Step 4: Create non-exported variable
LOCAL_VAR="local_only"

# Step 5: Check in subshell (should be empty)
bash -c 'echo $LOCAL_VAR'

# Step 6: Export and check again
export LOCAL_VAR
bash -c 'echo $LOCAL_VAR'

# Step 7: Clean up
unset TEST_VAR LOCAL_VAR

# Expected: Understanding of export vs non-export variables
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Variable Not Persisting

```bash
# Cause: Variable not added to configuration file

# Solution 1: Add to .bashrc
echo 'export MY_VAR="value"' >> ~/.bashrc
source ~/.bashrc

# Solution 2: Check if .bashrc is loaded
echo "test" >> ~/.bashrc
# Restart Termux and check if you see "test"

# Solution 3: Create .bashrc if doesn't exist
[[ ! -f ~/.bashrc ]] && touch ~/.bashrc

# Solution 4: Check shell type
echo $SHELL
# If zsh, use ~/.zshrc instead
```

### Problem 2: PATH Not Working

```bash
# Cause: Incorrect PATH format or missing directory

# Solution 1: Check PATH format
echo $PATH
# Should have format: /path1:/path2:/path3

# Solution 2: Check if directory exists
ls -la ~/scripts
# Must exist before adding to PATH

# Solution 3: Verify script is executable
ls -l ~/scripts/myscript
# Should show -rwxr-xr-x or similar

# Solution 4: Check for typos
export PATH="$PATH:$HOME/scripts"  # Correct
export PATH="$PATH:$HOME/scripys"  # Wrong!

# Solution 5: Debug which command runs
type myscript
which myscript
```

### Problem 3: PS1 Not Displaying Correctly

```bash
# Cause: Incorrect escape sequences or missing brackets

# Solution 1: Use correct escape sequences
# Wrong:
export PS1="\033[32m\u\033[0m\$ "
# Correct:
export PS1="\[\033[32m\]\u\[\033[0m\]\$ "

# Solution 2: Check terminal supports colors
echo $TERM
# Should be xterm-256color or similar

# Solution 3: Test colors
echo -e "\033[31mRed\033[0m"
echo -e "\033[32mGreen\033[0m"
echo -e "\033[34mBlue\033[0m"

# Solution 4: Use simpler prompt
export PS1="\u:\w\$ "
```

### Problem 4: "command not found" After PATH Change

```bash
# Cause: PATH overwritten instead of appended

# Wrong (overwrites PATH):
export PATH="/my/path"

# Correct (appends):
export PATH="$PATH:/my/path"

# Solution: Reset PATH
export PATH="/data/data/com.termux/files/usr/bin:/data/data/com.termux/files/usr/bin/applets"

# Or restart Termux
```

### Problem 5: Variable with Spaces Not Working

```bash
# Cause: Missing quotes around value

# Wrong:
export MY_PATH=/path with spaces

# Correct:
export MY_PATH="/path with spaces"

# Using variable:
cd "$MY_PATH"        # Correct with quotes
cd $MY_PATH          # Wrong, splits on spaces

# Always quote variables!
```

### Problem 6: .bashrc Not Loading

```bash
# Cause: File doesn't exist or shell startup issue

# Solution 1: Check if file exists
ls -la ~/.bashrc

# Solution 2: Create if missing
touch ~/.bashrc

# Solution 3: Manually source
source ~/.bashrc

# Solution 4: Check for syntax errors
bash -n ~/.bashrc

# Solution 5: Check shell
echo $SHELL
# If /bin/zsh, use ~/.zshrc
```

### Problem 7: Can't Unset Variable

```bash
# Cause: Variable is readonly

# Check if readonly
declare -p VARNAME

# Output shows:
# declare -r VARNAME="value"  # -r means readonly

# Solution: Can't unset readonly variables without restarting shell
# If needed, find where it's set readonly and remove that

# Find in config files
grep -r "readonly VARNAME" ~
```

### Problem 8: Special Characters in Variable Value

```bash
# Problem: Variable contains $ or other special characters

# Using single quotes (literal)
export MSG='$HOME is my home'
echo $MSG  # Output: $HOME is my home

# Using double quotes (expand)
export MSG="$HOME is my home"
echo $MSG  # Output: /data/data/... is my home

# Escape special characters
export MSG="\$HOME is \${HOME}"
echo $MSG  # Output: $HOME is /data/data/...

# Use single quotes for literal strings
export PASSWORD='P@$$w0rd!'
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔧 ENVIRONMENT VARIABLES         │
│   Complete Guide                   │
│                                    │
│   ✓ PATH, HOME, PREFIX             │
│   ✓ PS1 Customization              │
│   ✓ .bashrc Setup                  │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Code Style**
```
┌────────────────────────────────────┐
│  $ echo $PATH                      │
│  /data/data/.../bin:...            │
│                                    │
│  $ export PS1="custom> "           │
│  custom> _                         │
│                                    │
│  ENVIRONMENT VARIABLES             │
│  Chapter 7 | T3rmuxk1ng            │
└────────────────────────────────────┘
```

**Option C: Visual Diagram**
```
┌────────────────────────────────────┐
│  ┌─────┐   ┌─────┐   ┌─────┐       │
│  │PATH │   │HOME │   │PS1  │       │
│  └──┬──┘   └──┬──┘   └──┬──┘       │
│     │         │         │          │
│     └─────────┼─────────┘          │
│               ▼                    │
│        ENVIRONMENT                 │
│         VARIABLES                  │
│    Chapter 7 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔧 Termux Full Course - Chapter 7: Environment Variables Complete Guide

🔥 In this video you'll learn:
• Environment variables kya hote hain
• Important variables: PATH, HOME, PREFIX, SHELL, USER, TERM
• Variables ko kaise dekhein, set karein, delete karein
• .bashrc aur configuration files
• PS1 prompt customization with colors
• PATH modification aur custom paths
• 25+ practical examples

⏱️ Timestamps:
0:00 - Introduction
0:45 - What Are Environment Variables
4:00 - Important Environment Variables
8:00 - Viewing Environment Variables
11:00 - Setting Environment Variables
14:00 - Permanent vs Temporary Variables
16:30 - PS1 Customization
18:30 - PATH Modification
20:00 - Creating Custom Variables
21:30 - Unsetting Variables
22:30 - Summary

📝 Commands from this video:
echo $PATH
export MY_VAR="value"
env | grep PATH
source ~/.bashrc
export PS1="\[\033[32m\]\u@\h\[\033[0m\]:\[\033[34m\]\w\[\033[0m\]\$ "

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #EnvironmentVariables #TermuxCourse #T3rmuxk1ng #LinuxOnAndroid #BashConfiguration #PS1Customization #TermuxHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux, termux tutorial, environment variables, termux environment,
termux course, termux bashrc, termux ps1, termux path,
termux configuration, termux setup, linux environment variables,
bash environment, shell variables, termux hindi, termux tutorial hindi,
terminal customization, bash prompt, command line, t3rmuxk1ng,
termux course hindi, linux on android, bash configuration,
shell configuration, path variable, home variable, prefix termux
```

### Hashtags

```
#Termux #EnvironmentVariables #TermuxCourse #TermuxHindi #TermuxTutorial
#LinuxOnAndroid #BashConfiguration #PS1Customization #ShellVariables
#T3rmuxk1ng #LearnTermux #TermuxSetup #PathVariable #BashPrompt
#HindiTutorial #CommandLine #TerminalEmulator
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Bash Manual | `man bash` |
| Termux Wiki | https://wiki.termux.com/ |
| Bash Variables | https://www.gnu.org/software/bash/manual/html_node/Bash-Variables.html |

### Related Commands

| Command | Description |
|---------|-------------|
| `env` | Display/set environment |
| `printenv` | Print environment variables |
| `set` | Set/display shell variables |
| `export` | Export to environment |
| `unset` | Remove variable |
| `declare` | Declare variable with attributes |
| `readonly` | Make variable read-only |

### Quick Reference Card

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ENVIRONMENT VARIABLES QUICK REFERENCE                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  VIEWING:                                                                │
│    echo $VAR          - View single variable                            │
│    env                - View all environment variables                  │
│    printenv VAR       - View specific variable                          │
│    set                - View all variables                              │
│                                                                          │
│  SETTING:                                                                │
│    VAR="value"        - Set shell variable                              │
│    export VAR="value" - Set environment variable                        │
│    VAR="$VAR:extra"   - Append to variable                              │
│                                                                          │
│  DELETING:                                                               │
│    unset VAR          - Remove variable                                 │
│    unset -f FUNC      - Remove function                                 │
│                                                                          │
│  CONFIG FILES:                                                           │
│    ~/.bashrc          - Interactive shell config                        │
│    ~/.bash_profile    - Login shell config                              │
│    ~/.profile         - Generic profile                                 │
│                                                                          │
│  RELOAD:                                                                 │
│    source ~/.bashrc   - Reload configuration                            │
│                                                                          │
│  IMPORTANT VARIABLES:                                                    │
│    $HOME    - Home directory                                            │
│    $PATH    - Command search paths                                      │
│    $USER    - Current username                                          │
│    $SHELL   - Current shell                                             │
│    $PWD     - Current directory                                         │
│    $TERM    - Terminal type                                             │
│    $PREFIX  - Termux installation prefix                                │
│    $PS1     - Prompt string                                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 8, verify:

- [ ] Understand what environment variables are
- [ ] Know important variables: PATH, HOME, PREFIX, SHELL
- [ ] Can view variables using echo, env, printenv
- [ ] Can set variables using export
- [ ] Understand difference between temporary and permanent variables
- [ ] Have created/modified .bashrc file
- [ ] Have customized PS1 prompt
- [ ] Have added custom directory to PATH
- [ ] Can unset variables
- [ ] Completed all practice exercises

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 8: Text Editors in Termux**

- Nano editor complete guide
- Vim basics and essential commands
- Editor comparison (Nano vs Vim vs others)
- Editor customization
- Productivity tips and tricks
- Creating and editing files efficiently

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

<details>
<summary><b>❓ Question 1: What is the purpose of the PATH environment variable?</b></summary>

**Options:**
- A) Store file paths
- B) Define where shell looks for executable commands
- C) Set the current directory
- D) Store password hashes

**✅ Answer: B) Define where shell looks for executable commands**

**Explanation:** PATH contains a colon-separated list of directories. When you type a command, the shell searches these directories (left to right) to find the executable. If not found, you get "command not found".
</details>

<details>
<summary><b>❓ Question 2: Which command makes a variable available to child processes?</b></summary>

**Options:**
- A) `set VAR=value`
- B) `VAR=value`
- C) `export VAR=value`
- D) `define VAR=value`

**✅ Answer: C) `export VAR=value`**

**Explanation:** `export` marks the variable for export to child processes. Without export, the variable is only available in the current shell session.
</details>

<details>
<summary><b>❓ Question 3: What file is typically used for permanent environment variables in Termux?</b></summary>

**Options:**
- A) /etc/environment
- B) ~/.bashrc
- C) /etc/profile
- D) ~/.config

**✅ Answer: B) ~/.bashrc**

**Explanation:** ~/.bashrc is executed for each interactive shell session. This is where you add permanent environment variables, aliases, and functions in Termux.
</details>

<details>
<summary><b>❓ Question 4: How do you view all environment variables?</b></summary>

**Options:**
- A) `list all`
- B) `env` or `printenv`
- C) `show vars`
- D) `cat /etc/env`

**✅ Answer: B) `env` or `printenv`**

**Explanation:** Both `env` and `printenv` display all environment variables. `printenv VARNAME` shows a specific variable without needing the $ prefix.
</details>

<details>
<summary><b>❓ Question 5: What does $PREFIX represent in Termux?</b></summary>

**Options:**
- A) Command prefix
- B) Termux system root directory
- C) User preferences
- D) File prefix

**✅ Answer: B) Termux system root directory**

**Explanation:** $PREFIX points to /data/data/com.termux/files/usr - Termux's equivalent of /usr in standard Linux. It contains bin/, lib/, etc/, share/ directories.
</details>

<details>
<summary><b>❓ Question 6: What happens when you run `source ~/.bashrc`?</b></summary>

**Options:**
- A) Deletes .bashrc
- B) Reloads .bashrc in current shell
- C) Creates backup
- D) Opens in editor

**✅ Answer: B) Reloads .bashrc in current shell**

**Explanation:** `source` (or `.`) executes the file in the current shell, applying any changes immediately without needing to restart Termux.
</details>

<details>
<summary><b>❓ Question 7: Which variable controls your terminal prompt appearance?</b></summary>

**Options:**
- A) $PROMPT
- B) $PS1
- C) $DISPLAY
- D) $TERM

**✅ Answer: B) $PS1**

**Explanation:** PS1 (Prompt String 1) defines the primary prompt. You can customize it with special characters like \u (user), \w (directory), \t (time).
</details>

<details>
<summary><b>❓ Question 8: How do you add ~/scripts to PATH permanently?</b></summary>

**Options:**
- A) `PATH=$PATH:~/scripts`
- B) Add `export PATH="$PATH:$HOME/scripts"` to ~/.bashrc
- C) `setpath ~/scripts`
- D) `addpath ~/scripts`

**✅ Answer: B) Add `export PATH="$PATH:$HOME/scripts"` to ~/.bashrc**

**Explanation:** Adding the export command to ~/.bashrc makes it permanent. Without this, the change is lost when you close Termux.
</details>

<details>
<summary><b>❓ Question 9: What is the difference between `VAR=value` and `export VAR=value`?</b></summary>

**Options:**
- A) No difference
- B) `export` makes VAR available to child processes
- C) `export` is faster
- D) `VAR=value` is permanent

**✅ Answer: B) `export` makes VAR available to child processes**

**Explanation:** Direct assignment creates a shell variable. `export` creates an environment variable that child processes (scripts, programs) can access.
</details>

<details>
<summary><b>❓ Question 10: How do you delete an environment variable?</b></summary>

**Options:**
- A) `delete VAR`
- B) `unset VAR`
- C) `remove VAR`
- D) `VAR=""`

**✅ Answer: B) `unset VAR`**

**Explanation:** `unset VAR` completely removes the variable from both shell and environment. Setting it to empty string keeps the variable but with empty value.
</details>

<details>
<summary><b>❓ Question 11: What does `${VAR:-default}` do?</b></summary>

**Options:**
- A) Sets VAR to default
- B) Returns default if VAR is unset or empty
- C) Deletes VAR
- D) Checks if VAR equals default

**✅ Answer: B) Returns default if VAR is unset or empty**

**Explanation:** This is parameter expansion. If VAR is set and non-empty, returns its value. Otherwise returns "default" without modifying VAR.
</details>

<details>
<summary><b>❓ Question 12: Which variable indicates your default text editor?</b></summary>

**Options:**
- A) $TEXTEDITOR
- B) $EDITOR
- C) $VIM
- D) $EDIT

**✅ Answer: B) $EDITOR**

**Explanation:** $EDITOR is the standard variable for default editor. Programs like git, visudo, crontab use it. Common values: nano, vim, code.
</details>

<details>
<summary><b>❓ Question 13: How do you check if a variable is set?</b></summary>

**Options:**
- A) `test $VAR`
- B) `[ -z "${VAR+x}" ]`
- C) `check VAR`
- D) `isset VAR`

**✅ Answer: B) `[ -z "${VAR+x}" ]`**

**Explanation:** `${VAR+x}` expands to "x" if VAR is set (even if empty), or nothing if unset. `-z` tests for zero length, so this returns true if VAR is unset.
</details>

<details>
<summary><b>❓ Question 14: What's the effect of `readonly VAR=value`?</b></summary>

**Options:**
- A) Makes VAR temporary
- B) Makes VAR read-only (cannot be changed)
- C) Deletes VAR after reading
- D) Makes VAR global

**✅ Answer: B) Makes VAR read-only (cannot be changed)**

**Explanation:** `readonly` marks a variable as read-only. Any attempt to modify or unset it will fail. Useful for constants.
</details>

<details>
<summary><b>❓ Question 15: How do you prepend a directory to PATH?</b></summary>

**Options:**
- A) `export PATH=/new/path:$PATH`
- B) `export PATH=$PATH:/new/path`
- C) `PATH.prepend /new/path`
- D) `export PATH+=/new/path`

**✅ Answer: A) `export PATH=/new/path:$PATH`**

**Explanation:** Prepending (adding at beginning) gives the new directory higher priority. Appending (adding at end) gives lower priority. Use prepending to override system commands.
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Question 1: Explain the difference between shell variables and environment variables.

**Answer:**
**Shell Variables:**
- Only accessible in the current shell
- Not passed to child processes
- Set by simple assignment: `VAR=value`
- Example: PS1, HISTSIZE

**Environment Variables:**
- Accessible to current shell and child processes
- Must be exported: `export VAR=value`
- Inherited by scripts and programs
- Example: PATH, HOME, USER

```bash
# Shell variable - not inherited
MY_SHELL_VAR="test"
bash -c 'echo $MY_SHELL_VAR'  # Empty

# Environment variable - inherited
export MY_ENV_VAR="test"
bash -c 'echo $MY_ENV_VAR'    # Prints: test
```

**Follow-up:** How can you check if a variable is exported?
> Use `declare -p VARNAME` or `export -p | grep VARNAME`. Exported variables show `declare -x`.

### Question 2: How does the PATH variable work? What happens when you type a command?

**Answer:**
When you type a command, the shell:
1. Checks if it's a shell builtin (cd, echo, etc.)
2. Checks if it's an alias or function
3. Searches PATH directories from left to right
4. Executes the first matching executable found
5. Returns "command not found" if no match

```bash
# View PATH directories
echo "$PATH" | tr ':' '\n'

# Find where a command is located
which python
type ls

# Debug command resolution
type -a python  # Shows all matches
```

**Follow-up:** How would you add a custom scripts directory to PATH?
> Add to ~/.bashrc: `export PATH="$HOME/scripts:$PATH"` (prepend for priority) or `export PATH="$PATH:$HOME/scripts"` (append).

### Question 3: A user's .bashrc has an error and Termux won't start properly. How do you fix it?

**Answer:**
1. **Start Termux with safe mode (if available)**
2. **Edit from recovery:**
   ```bash
   # Comment out problematic lines
   nano ~/.bashrc
   # Or restore backup
   cp ~/.bashrc.backup ~/.bashrc
   ```
3. **If terminal exits immediately:**
   - Use another terminal app
   - Or access via ADB: `adb shell`
   - Navigate to Termux files and edit
4. **Nuclear option - recreate .bashrc:**
   ```bash
   mv ~/.bashrc ~/.bashrc.broken
   # Termux will create default on next start
   ```

**Follow-up:** How can you prevent this in the future?
> Always backup before editing: `cp ~/.bashrc ~/.bashrc.backup.$(date +%Y%m%d)`. Test changes in a subshell first: `bash`.

### Question 4: Explain PS1 customization and create a useful prompt.

**Answer:**
PS1 (Prompt String 1) defines the command prompt. Common escape sequences:
- `\u` - Username
- `\h` - Hostname
- `\w` - Full working directory
- `\W` - Current directory name
- `\t` - Time (24-hour)
- `\d` - Date

**Useful Prompts:**
```bash
# Simple colored prompt
export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# With git branch
export PS1='\[\033[1;34m\]\w\[\033[0;33m\]$(git branch 2>/dev/null | grep \* | head -1)\[\033[00m\]\$ '

# Multi-line with time
export PS1='\[\033[1;36m\][\t] \[\033[1;32m\]\u@\h\[\033[00m\]\n\w\$ '

# Hacker style
export PS1='\[\033[0;32m\]┌─[\[\033[1;32m\]\u@\h\[\033[0;32m\]]─[\[\033[1;34m\]\w\[\033[0;32m\]]\n└──╼ \[\033[1;32m\]\$\[\033[0m\] '
```

**Follow-up:** How do color codes work in prompts?
> `\[\033[01;32m\]` starts bold green, `\[\033[00m\]` resets. The `\[ \]` pairs are crucial for proper line editing.

### Question 5: How do you securely store and use API keys as environment variables?

**Answer:**
**Best Practices:**
1. **Never commit to git:** Add to .gitignore
2. **Use separate file for secrets:**
   ```bash
   # ~/.env (chmod 600)
   export API_KEY="secret123"
   export DB_PASSWORD="password"
   
   # In ~/.bashrc
   [ -f ~/.env ] && source ~/.env
   ```
3. **Restrict file permissions:**
   ```bash
   chmod 600 ~/.env
   ```
4. **Use in scripts:**
   ```bash
   curl -H "Authorization: Bearer $API_KEY" https://api.example.com
   ```

**Warning:** Environment variables are visible to any process you run and in /proc.

**Follow-up:** What's a more secure alternative for production?
> Use a secrets manager, encrypted files, or environment-specific configuration. For Termux, consider gpg-encrypted files that decrypt at runtime.

### Question 6: How do you debug environment variable issues?

**Answer:**
```bash
# Check if variable is set
[ -z "${VAR+x}" ] && echo "VAR not set" || echo "VAR is set"

# See variable value and attributes
declare -p VAR

# Check if exported
export -p | grep VAR

# Debug script environment
bash -x script.sh  # Show commands with variable expansion

# Compare shell vs environment
env | grep VAR     # Environment variables only
set | grep VAR     # All variables

# Check PATH for missing directories
echo "$PATH" | tr ':' '\n'

# Find where command is
type -a command
which command
```

**Follow-up:** How would you troubleshoot "command not found"?
> Check `echo $PATH`, verify binary location with `find`, ensure file is executable with `ls -l`, check if directory is in PATH.

### Question 7: Explain the load order of shell configuration files.

**Answer:**
**Interactive Login Shell:**
1. /etc/profile (system-wide)
2. ~/.bash_profile, ~/.bash_login, or ~/.profile (first found)
3. ~/.bash_logout (on exit)

**Interactive Non-Login Shell (Termux default):**
1. ~/.bashrc

**In Termux:**
- Most sessions are non-login shells
- ~/.bashrc is the primary config file
- Can source ~/.bash_profile from ~/.bashrc

```bash
# Typical ~/.bashrc header
if [[ -f ~/.bash_profile ]]; then
    source ~/.bash_profile
fi
```

**Follow-up:** Why does Termux primarily use .bashrc?
> Termux starts interactive shells, not login shells. Each terminal session is a non-login interactive shell that sources .bashrc.

### Question 8: How do you set up environment variables for different projects?

**Answer:**
**Method 1: .env files per project**
```bash
# project/.env
export DATABASE_URL="postgres://localhost/mydb"
export API_ENDPOINT="https://api.example.com"

# Load in shell
cd ~/projects/myproject
source .env
```

**Method 2: direnv-style functions**
```bash
# In ~/.bashrc
project_env() {
    local env_file="$1/.env"
    if [[ -f "$env_file" ]]; then
        source "$env_file"
        echo "Loaded environment from $env_file"
    fi
}

# Usage
cd ~/projects/webapp && project_env .
```

**Method 3: Automatic with cd**
```bash
# In ~/.bashrc
cd() {
    builtin cd "$@"
    [[ -f .env ]] && source .env
}
```

**Follow-up:** How do you unload environment variables when switching projects?
> Create an `env_reset` function or use `unset` for each variable. Consider using subshells for isolation.

### Question 9: How do you create persistent aliases and functions?

**Answer:**
**Aliases:**
```bash
# In ~/.bashrc
alias ll='ls -la'
alias la='ls -A'
alias ..='cd ..'
alias grep='grep --color=auto'
alias cls='clear'
alias h='history'
alias ports='netstat -tulanp'

# With variables
alias scripts='cd $HOME/scripts'
```

**Functions (more powerful):**
```bash
# In ~/.bashrc
mkcd() {
    mkdir -p "$1" && cd "$1"
}

extract() {
    if [[ -f "$1" ]]; then
        case "$1" in
            *.tar.bz2) tar xjf "$1" ;;
            *.tar.gz)  tar xzf "$1" ;;
            *.zip)     unzip "$1" ;;
            *)         echo "Unknown format" ;;
        esac
    fi
}

backup() {
    cp "$1" "$1.backup.$(date +%Y%m%d_%H%M%S)"
}
```

**Follow-up:** What's the difference between alias and function?
> Aliases are simple text substitutions, cannot take arguments directly, and are limited to single commands. Functions are mini-scripts that can have logic, arguments, variables, and multiple commands.

### Question 10: How do you manage PATH modifications cleanly?

**Answer:**
**Clean PATH Management:**
```bash
# In ~/.bashrc

# Function to add to PATH if not already present
path_append() {
    if [[ -d "$1" ]] && [[ ":$PATH:" != *":$1:"* ]]; then
        export PATH="$PATH:$1"
    fi
}

path_prepend() {
    if [[ -d "$1" ]] && [[ ":$PATH:" != *":$1:"* ]]; then
        export PATH="$1:$PATH"
    fi
}

# Use functions
path_append "$HOME/scripts"
path_append "$HOME/.local/bin"
path_prepend "$HOME/bin"

# Function to remove from PATH
path_remove() {
    export PATH=$(echo "$PATH" | sed -e "s|:$1||g" -e "s|^$1:||g")
}

# Function to show PATH nicely
path_show() {
    echo "$PATH" | tr ':' '\n' | nl
}
```

**Follow-up:** Why check if directory exists before adding?
> Prevents errors and keeps PATH clean. Non-existent directories in PATH can cause command execution delays.

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: 🛠️ Setting Up Development Environment

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  🛠️ SCENARIO: Configure a complete development environment in Termux          ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  # Create development .bashrc configuration                                   ║
║  cat >> ~/.bashrc << 'EOF'                                                    ║
║                                                                               ║
║  # Development Environment Variables                                          ║
║  export PROJECTS="$HOME/projects"                                            ║
║  export EDITOR="nano"                                                         ║
║  export VISUAL="vim"                                                          ║
║  export BROWSER="firefox"                                                     ║
║  export LANG="en_US.UTF-8"                                                    ║
║                                                                               ║
║  # Python Development                                                         ║
║  export PYTHONDONTWRITEBYTECODE=1                                            ║
║  export PYTHONUNBUFFERED=1                                                    ║
║  export PIPENV_VENV_IN_PROJECT=1                                              ║
║                                                                               ║
║  # Node.js Development                                                        ║
║  export NODE_ENV="development"                                                ║
║  export NPM_CONFIG_PREFIX="$HOME/.npm-global"                                 ║
║                                                                               ║
║  # Add to PATH                                                                ║
║  export PATH="$HOME/scripts:$HOME/.local/bin:$PATH"                          ║
║                                                                               ║
║  # Development Aliases                                                        ║
║  alias p='python'                                                             ║
║  alias pipi='pip install'                                                     ║
║  alias nrs='npm run start'                                                    ║
║  alias goto.proj='cd $PROJECTS'                                               ║
║                                                                               ║
║  EOF                                                                          ║
║  source ~/.bashrc                                                             ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: 🔐 Secure API Key Management

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  🔐 SCENARIO: Manage API keys securely for different services                 ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  # Create secure secrets file (restricted permissions)                        ║
║  touch ~/.secrets                                                             ║
║  chmod 600 ~/.secrets                                                         ║
║                                                                               ║
║  # Add your secrets                                                           ║
║  cat >> ~/.secrets << 'EOF'                                                   ║
║  # API Keys - DO NOT SHARE OR COMMIT                                          ║
║  export GITHUB_TOKEN="ghp_xxxxxxxxxxxx"                                       ║
║  export OPENAI_API_KEY="sk-xxxxxxxxxxxx"                                      ║
║  export AWS_ACCESS_KEY="AKIAXXXXXXXXXX"                                       ║
║  export AWS_SECRET_KEY="xxxxxxxxxxxxxxxxxxxxxxxx"                             ║
║  export TELEGRAM_BOT_TOKEN="123456:ABC-DEF..."                                ║
║  EOF                                                                          ║
║                                                                               ║
║  # Source in .bashrc (add this line)                                          ║
║  [ -f ~/.secrets ] && source ~/.secrets                                       ║
║                                                                               ║
║  # Use in scripts                                                             ║
║  curl -H "Authorization: token $GITHUB_TOKEN" \                               ║
║    https://api.github.com/user/repos                                          ║
║                                                                               ║
║  # Add to .gitignore to prevent accidents                                     ║
║  echo ".secrets" >> ~/.gitignore                                              ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: 🎨 Professional Terminal Prompt

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  🎨 SCENARIO: Create a professional, informative terminal prompt              ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  # Add to ~/.bashrc                                                           ║
║                                                                               ║
║  # Git branch function for prompt                                             ║
║  parse_git_branch() {                                                         ║
║      git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'        ║
║  }                                                                            ║
║                                                                               ║
║  # Color definitions                                                           ║
║  GREEN='\[\033[01;32m\]'                                                      ║
║  BLUE='\[\033[01;34m\]'                                                       ║
║  YELLOW='\[\033[01;33m\]'                                                     ║
║  RED='\[\033[01;31m\]'                                                        ║
║  RESET='\[\033[00m\]'                                                         ║
║                                                                               ║
║  # Professional prompt with git branch                                        ║
║  export PS1="${GREEN}\u@\h${RESET}:${BLUE}\w${YELLOW}\$(parse_git_branch)${RESET}\$ "   ║
║                                                                               ║
║  # Result: user@host:~/projects (main)$                                       ║
║                                                                               ║
║  # Advanced multi-line prompt                                                 ║
║  export PS1="\n${BLUE}┌──(${GREEN}\u@\h${BLUE})─[${YELLOW}\w${BLUE}]${RESET}\n└─\$ "     ║
║                                                                               ║
║  # Result:                                                                    ║
║  ┌──(user@host)─[~/projects]                                                  ║
║  └─$                                                                          ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: 🔄 Project-Specific Environment Switching

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  🔄 SCENARIO: Switch between different project environments                   ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  # In ~/.bashrc - Project environment switcher                                ║
║                                                                               ║
║  # Define project environments                                                ║
║  work_env() {                                                                 ║
║      export PROJECT_NAME="work-project"                                       ║
║      export API_URL="https://api.company.com"                                 ║
║      export DB_HOST="company-db.internal"                                     ║
║      export ENV="production"                                                  ║
║      cd ~/projects/work                                                       ║
║      echo "✅ Work environment loaded"                                         ║
║  }                                                                            ║
║                                                                               ║
║  personal_env() {                                                             ║
║      export PROJECT_NAME="personal"                                           ║
║      export API_URL="https://api.personal.dev"                                ║
║      export DB_HOST="localhost"                                               ║
║      export ENV="development"                                                 ║
║      cd ~/projects/personal                                                   ║
║      echo "✅ Personal environment loaded"                                     ║
║  }                                                                            ║
║                                                                               ║
║  show_env() {                                                                 ║
║      echo "Project: $PROJECT_NAME"                                            ║
║      echo "API: $API_URL"                                                     ║
║      echo "Database: $DB_HOST"                                                ║
║      echo "Environment: $ENV"                                                 ║
║  }                                                                            ║
║                                                                               ║
║  # Usage:                                                                     ║
║  # work_env      # Switch to work environment                                 ║
║  # personal_env  # Switch to personal environment                             ║
║  # show_env      # Display current environment                                ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: 🧪 Testing Environment Variables Script

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  🧪 SCENARIO: Create a script to verify environment setup                     ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  #!/bin/bash                                                                  ║
║  # check_env.sh - Verify environment configuration                            ║
║                                                                               ║
║  echo "═══════════════════════════════════════════════════════"               ║
║  echo "         TERMUX ENVIRONMENT CHECK"                                     ║
║  echo "═══════════════════════════════════════════════════════"               ║
║                                                                               ║
║  # Check essential variables                                                  ║
║  check_var() {                                                                ║
║      if [ -n "${!1}" ]; then                                                  ║
║          echo "✅ $1 = ${!1}"                                                  ║
║      else                                                                     ║
║          echo "❌ $1 is not set"                                               ║
║      fi                                                                       ║
║  }                                                                            ║
║                                                                               ║
║  echo ""                                                                      ║
║  echo "📋 Essential Variables:"                                               ║
║  check_var "HOME"                                                             ║
║  check_var "PREFIX"                                                           ║
║  check_var "PATH"                                                             ║
║  check_var "SHELL"                                                            ║
║  check_var "TERM"                                                             ║
║  check_var "USER"                                                             ║
║                                                                               ║
║  echo ""                                                                      ║
║  echo "🔧 Development Variables:"                                             ║
║  check_var "EDITOR"                                                           ║
║  check_var "PROJECTS"                                                         ║
║  check_var "LANG"                                                             ║
║                                                                               ║
║  echo ""                                                                      ║
║  echo "📁 PATH Directories:"                                                  ║
║  echo "$PATH" | tr ':' '\n' | while read dir; do                              ║
║      if [ -d "$dir" ]; then                                                   ║
║          echo "  ✅ $dir"                                                     ║
║      else                                                                     ║
║          echo "  ❌ $dir (not found)"                                          ║
║      fi                                                                       ║
║  done                                                                         ║
║                                                                               ║
║  echo ""                                                                      ║
║  echo "═══════════════════════════════════════════════════════"               ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: Environment Variable Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ENVIRONMENT VARIABLE HIERARCHY                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    Android/Linux Kernel                             │    │
│   │   Sets initial process environment                                  │    │
│   └───────────────────────────────┬─────────────────────────────────────┘    │
│                                   │                                          │
│                                   ▼                                          │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    Termux Application                               │    │
│   │   ┌──────────────────────────────────────────────────────────────┐ │    │
│   │   │ Sets: PREFIX, HOME, TMPDIR, PATH (initial)                   │ │    │
│   │   │ PATH=/data/data/com.termux/files/usr/bin:...                 │ │    │
│   │   └──────────────────────────────────────────────────────────────┘ │    │
│   └───────────────────────────────┬─────────────────────────────────────┘    │
│                                   │                                          │
│                                   ▼                                          │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    Shell Initialization                             │    │
│   │   ┌──────────────────────────────────────────────────────────────┐ │    │
│   │   │ 1. Read ~/.bashrc                                            │ │    │
│   │   │ 2. Set: PS1, HISTSIZE, EDITOR, aliases, functions            │ │    │
│   │   │ 3. Modify: PATH, custom variables                            │ │    │
│   │   └──────────────────────────────────────────────────────────────┘ │    │
│   └───────────────────────────────┬─────────────────────────────────────┘    │
│                                   │                                          │
│                                   ▼                                          │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    Your Shell Session                               │    │
│   │   ┌──────────────────────────────────────────────────────────────┐ │    │
│   │   │ export MY_VAR="value"   ← You set                            │ │    │
│   │   │ PATH=$PATH:~/scripts    ← You modify                         │ │    │
│   │   └──────────────────────────────────────────────────────────────┘ │    │
│   └───────────────────────────────┬─────────────────────────────────────┘    │
│                                   │                                          │
│                                   ▼                                          │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    Child Processes                                  │    │
│   │   Scripts, Programs, Commands (inherit exported variables)          │    │
│   └────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: PATH Resolution Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         PATH RESOLUTION FLOW                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   User types: python                                                         │
│                                                                              │
│                    ┌─────────────────┐                                      │
│                    │  Command Typed  │                                      │
│                    │    "python"     │                                      │
│                    └────────┬────────┘                                      │
│                             │                                                │
│                             ▼                                                │
│                    ┌─────────────────┐                                      │
│                    │ Shell Built-in? │                                      │
│                    │      NO         │                                      │
│                    └────────┬────────┘                                      │
│                             │                                                │
│                             ▼                                                │
│                    ┌─────────────────┐                                      │
│                    │ Alias/Function? │                                      │
│                    │      NO         │                                      │
│                    └────────┬────────┘                                      │
│                             │                                                │
│                             ▼                                                │
│         ┌───────────────────────────────────────────────┐                  │
│         │              SEARCH PATH DIRECTORIES           │                  │
│         │                                                   │                  │
│         │  $PREFIX/bin/                                    │                  │
│         │  ├── Check: /data/.../usr/bin/python     ✅     │                  │
│         │  │   FOUND! Execute this                        │                  │
│         │  │                                               │                  │
│         │  ├── Check: /data/.../usr/bin/python3    (skip) │                  │
│         │  └── ...                                         │                  │
│         │                                                   │                  │
│         └───────────────────────────────────────────────┘                  │
│                             │                                                │
│                             ▼                                                │
│                    ┌─────────────────┐                                      │
│                    │   EXECUTE       │                                      │
│                    │  /.../bin/python│                                      │
│                    └─────────────────┘                                      │
│                                                                              │
│   If not found in any PATH directory → "command not found" error            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Variable Scope Comparison

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                       VARIABLE SCOPE COMPARISON                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    SHELL VARIABLE                                   │    │
│   │   VAR="value"                                                       │    │
│   │                                                                      │    │
│   │   ┌──────────────┐     ┌──────────────┐     ┌──────────────┐       │    │
│   │   │ Current      │     │ Child        │     │ Parent       │       │    │
│   │   │ Shell        │     │ Process      │     │ Process      │       │    │
│   │   │              │     │              │     │              │       │    │
│   │   │  ✅ Can      │     │  ❌ Cannot   │     │  ❌ Cannot   │       │    │
│   │   │  access      │     │  access      │     │  access      │       │    │
│   │   └──────────────┘     └──────────────┘     └──────────────┘       │    │
│   └────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    ENVIRONMENT VARIABLE                             │    │
│   │   export VAR="value"                                                │    │
│   │                                                                      │    │
│   │   ┌──────────────┐     ┌──────────────┐     ┌──────────────┐       │    │
│   │   │ Current      │     │ Child        │     │ Parent       │       │    │
│   │   │ Shell        │     │ Process      │     │ Process      │       │    │
│   │   │              │     │              │     │              │       │    │
│   │   │  ✅ Can      │     │  ✅ Can      │     │  ❌ Cannot   │       │    │
│   │   │  access      │     │  access      │     │  access      │       │    │
│   │   └──────────────┘     └──────────────┘     └──────────────┘       │    │
│   └────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
│   KEY: Environment variables inherit DOWN to children, not UP to parents    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Type | Chapter | Topic | Relevance |
|------|---------|-------|-----------|
| **📖 Prerequisite** | Chapter 6 | File System Structure | Understanding $PREFIX, $HOME paths |
| **🔄 Current** | **Chapter 7** | **Environment Variables** | **You are here** |
| **⏭️ Next** | Chapter 8 | Text Editors | Editing .bashrc, .vimrc |
| **⏭️ Next** | Chapter 9 | Termux Styling | Customizing terminal appearance |
| **📊 Related** | Chapter 10 | Termux API Setup | API environment configuration |
| **📊 Related** | Chapter 15 | Shell Scripting | Using variables in scripts |
| **📊 Advanced** | Chapter 20 | Bash Functions | Advanced variable techniques |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Dynamic Environment Loading

```bash
# Add to ~/.bashrc - Automatically load project-specific .env files

# Function to load .env if it exists
load_env() {
    local env_file="${1:-.env}"
    if [[ -f "$env_file" ]]; then
        # Export each line as environment variable
        while IFS= read -r line; do
            # Skip comments and empty lines
            [[ "$line" =~ ^#.*$ ]] && continue
            [[ -z "$line" ]] && continue
            export "$line"
        done < "$env_file"
        echo "✅ Loaded environment from $env_file"
    fi
}

# Override cd to auto-load .env
cd() {
    builtin cd "$@" || return
    [[ -f .env ]] && load_env .env
}

# Usage: Just cd into a project with .env file
# Variables are automatically loaded
```

### Advanced Technique 2: Environment Variable Manager

```bash
# Add to ~/.bashrc - Complete environment variable management

# Save current environment state
env_save() {
    local name="${1:-default}"
    env > ~/.env_states/$name.env
    echo "✅ Saved environment state: $name"
}

# Load saved environment state
env_load() {
    local name="${1:-default}"
    if [[ -f ~/.env_states/$name.env ]]; then
        # Clear current env
        unset $(env | awk -F= '{print $1}')
        # Load saved
        source ~/.env_states/$name.env
        echo "✅ Loaded environment state: $name"
    else
        echo "❌ State not found: $name"
    fi
}

# List saved states
env_list() {
    echo "Saved environment states:"
    ls -1 ~/.env_states/*.env 2>/dev/null | xargs -n1 basename | sed 's/.env$//'
}

# Initialize
mkdir -p ~/.env_states
```

### Advanced Technique 3: Secret Injection from Encrypted File

```bash
# Securely manage secrets with GPG encryption

# Encrypt secrets file
secrets_encrypt() {
    gpg --symmetric --cipher-algo AES256 ~/.secrets
    shred -u ~/.secrets  # Securely delete unencrypted
    echo "✅ Secrets encrypted"
}

# Decrypt and load secrets temporarily
secrets_load() {
    local temp_secrets=$(mktemp)
    gpg --decrypt ~/.secrets.gpg > "$temp_secrets" 2>/dev/null
    source "$temp_secrets"
    shred -u "$temp_secrets"
    echo "✅ Secrets loaded (in memory only)"
}

# Create encrypted secrets file
secrets_create() {
    cat > ~/.secrets << 'EOF'
export API_KEY="your-secret-key"
export DB_PASSWORD="your-password"
EOF
    secrets_encrypt
}

# Usage:
# secrets_create   # First time setup
# secrets_load     # Load secrets when needed
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

Complete this checklist to verify your understanding:

- [ ] **Core Concepts**
  - [ ] Understand what environment variables are
  - [ ] Know the difference between shell and environment variables
  - [ ] Understand variable inheritance (export)

- [ ] **Important Variables**
  - [ ] Know what $PATH does and how it works
  - [ ] Understand $HOME and $PREFIX in Termux
  - [ ] Know $SHELL, $USER, $TERM purposes

- [ ] **Variable Operations**
  - [ ] Can view variables with echo, env, printenv
  - [ ] Can set temporary variables
  - [ ] Can set permanent variables in .bashrc
  - [ ] Can delete variables with unset

- [ ] **PATH Management**
  - [ ] Can add directories to PATH
  - [ ] Understand prepend vs append
  - [ ] Can make PATH changes permanent

- [ ] **Customization**
  - [ ] Can customize PS1 prompt
  - [ ] Can create aliases in .bashrc
  - [ ] Can create functions in .bashrc

- [ ] **Configuration Files**
  - [ ] Know the purpose of .bashrc
  - [ ] Know how to reload .bashrc
  - [ ] Can backup and restore .bashrc

- [ ] **Practical Skills**
  - [ ] Created useful custom variables
  - [ ] Set up development environment
  - [ ] Configured a custom prompt

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1: Backup Your .bashrc Before Editing**
> 
> Always create a backup before modifying configuration files:
> ```bash
> cp ~/.bashrc ~/.bashrc.backup.$(date +%Y%m%d)
> # If something breaks:
> cp ~/.bashrc.backup.YYYYMMDD ~/.bashrc
> ```

> 💡 **Pro Tip #2: Quick Variable Check with Default**
> 
> Use parameter expansion with defaults:
> ```bash
> echo "${EDITOR:-nano}"    # Uses nano if EDITOR not set
> echo "${PROJECTS:-~/projects}"  # Default project path
> 
> # Set default permanently:
> export EDITOR="${EDITOR:-nano}"
> ```

> 💡 **Pro Tip #3: Debug Variable Issues**
> 
> Use `declare -p` to see variable attributes:
> ```bash
> declare -p PATH      # Shows if exported, readonly, etc.
> declare -p           # Shows all with attributes
> 
> # Check if variable exists:
> [ -z "${VAR+x}" ] && echo "VAR not set"
> [ -n "$VAR" ] && echo "VAR is set and non-empty"
> ```

> 💡 **Pro Tip #4: Path Deduplication**
> 
> Remove duplicate entries from PATH:
> ```bash
> # Add to .bashrc
> dedup_path() {
>     export PATH=$(echo "$PATH" | tr ':' '\n' | sort -u | tr '\n' ':' | sed 's/:$//')
> }
> ```

> 💡 **Pro Tip #5: Color Variables for Scripts**
> 
> Define colors once, use everywhere:
> ```bash
> # Add to .bashrc
> export RED='\033[0;31m'
> export GREEN='\033[0;32m'
> export YELLOW='\033[0;33m'
> export BLUE='\033[0;34m'
> export NC='\033[0m'  # No Color
> 
> # Usage in scripts:
> echo -e "${GREEN}Success!${NC}"
> echo -e "${RED}Error!${NC}"
> ```

> 💡 **Pro Tip #6: Project-Specific Environment**
> 
> Create .env file in project directories:
> ```bash
> # In project directory, create .env
> export DATABASE_URL="localhost:5432"
> export API_KEY="your-key"
> export DEBUG="true"
> 
> # Load with:
> source .env
> 
> # Or auto-load in .bashrc:
> [[ -f .env ]] && source .env
> ```

> 💡 **Pro Tip #7: Secure API Keys**
> 
> Store sensitive data in a separate file:
> ```bash
> # Create ~/.secure_env (chmod 600)
> export API_KEY="secret-key"
> export DB_PASSWORD="password"
> 
> # In .bashrc:
> [[ -f ~/.secure_env ]] && source ~/.secure_env
> ```

> 💡 **Pro Tip #8: Dynamic PATH with Local Bin**
> 
> Automatically add local bin if it exists:
> ```bash
> # Add to .bashrc
> [[ -d ~/bin ]] && export PATH="$HOME/bin:$PATH"
> [[ -d ~/.local/bin ]] && export PATH="$HOME/.local/bin:$PATH"
> ```

> 💡 **Pro Tip #9: Prompt with Git Status**
> 
> Show git branch in your prompt:
> ```bash
> parse_git_branch() {
>     git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
> }
> export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\]\$ "
> ```

> 💡 **Pro Tip #10: History with Timestamps**
> 
> Add timestamps to command history:
> ```bash
> export HISTTIMEFORMAT="%F %T: "
> export HISTSIZE=10000
> export HISTFILESIZE=20000
> export HISTCONTROL=ignoreboth:erasedups
> ```

---

## 🔥 REAL WORLD USE CASES

### Use Case 1: Development Environment Setup

```bash
# Set up a complete development environment
# Add to ~/.bashrc

# Project paths
export PROJECTS="$HOME/projects"
export WORK="$HOME/work"

# Editor preferences
export EDITOR="vim"
export VISUAL="vim"
export GIT_EDITOR="vim"

# Language settings
export LANG="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"

# Python
export PYTHONPATH="$HOME/projects/lib:$PYTHONPATH"
export PYTHONDONTWRITEBYTECODE=1

# Node.js
export NODE_PATH="$HOME/.npm-global/lib"

# Go
export GOPATH="$HOME/go"
export PATH="$PATH:$GOPATH/bin"

# Custom scripts
export PATH="$HOME/scripts:$HOME/.local/bin:$PATH"
```

### Use Case 2: Security Tools Configuration

```bash
# Environment for penetration testing
# ~/.bashrc additions

export TOOLS="$HOME/tools"
export WORDLISTS="$TOOLS/wordlists"
export LOOT="$TOOLS/loot"

# Nmap
export NMAPDIR="$PREFIX/share/nmap"

# Metasploit
export MSF_DATABASE_CONFIG="$HOME/.msf4/database.yml"

# Custom aliases for tools
alias scan='nmap -sV -sC'
alias msf='msfconsole'
alias loot='cd $LOOT'
```

### Use Case 3: API Development

```bash
# API development environment
# ~/.config/api_env

# API endpoints (dev/prod)
export API_DEV="http://localhost:8000"
export API_PROD="https://api.example.com"
export API_URL="$API_DEV"  # Current active

# Authentication
export API_TOKEN=""  # Set when needed
export API_KEY=""    # Set when needed

# Helper function
api_call() {
    curl -H "Authorization: Bearer $API_TOKEN" "$API_URL/$1"
}
```

### Use Case 4: Multi-Project Configuration

```bash
# Switch between project environments
# Add to .bashrc

switch_project() {
    case "$1" in
        webapp)
            export PROJECT_ROOT="$HOME/projects/webapp"
            export DATABASE_URL="localhost:5432/webapp"
            export REDIS_URL="localhost:6379"
            ;;
        api)
            export PROJECT_ROOT="$HOME/projects/api"
            export DATABASE_URL="localhost:5432/api"
            export API_PORT="3000"
            ;;
        mobile)
            export PROJECT_ROOT="$HOME/projects/mobile"
            export REACT_NATIVE_PACKAGER_HOSTNAME="localhost"
            ;;
        *)
            echo "Usage: switch_project {webapp|api|mobile}"
            ;;
    esac
    cd "$PROJECT_ROOT"
    echo "Switched to $1 at $PROJECT_ROOT"
}
```

### Use Case 5: Automated Backup Configuration

```bash
# Backup environment configuration
# ~/.backup_env

export BACKUP_DIR="$HOME/backups"
export BACKUP_SERVER="user@backup.example.com"
export BACKUP_PATH="/remote/backups"

# Retention
export BACKUP_DAILY_KEEP=7
export BACKUP_WEEKLY_KEEP=4
export BACKUP_MONTHLY_KEEP=12

# Notifications
export BACKUP_NOTIFY_EMAIL="admin@example.com"
export BACKUP_NOTIFY_TELEGRAM=""  # Bot token if needed

# Helper function
backup_notify() {
    echo "Backup completed: $(date)" | mail -s "Backup Report" $BACKUP_NOTIFY_EMAIL
}
```

---

## ⚡ QUICK REFERENCE CARD

### Viewing Variables

| Command | Description |
|---------|-------------|
| `echo $VAR` | View single variable |
| `printenv` | All environment variables |
| `printenv VAR` | Specific variable (no $) |
| `env` | All environment variables |
| `set` | All variables (shell + env) |
| `declare -p` | All with attributes |
| `declare -p VAR` | Variable with attributes |

### Setting Variables

| Command | Scope | Persistence |
|---------|-------|-------------|
| `VAR=value` | Shell only | Session only |
| `export VAR=value` | Environment | Session only |
| In `.bashrc` | Environment | Permanent |
| In `.bash_profile` | Environment | Login shells |

### Important Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `$HOME` | User home directory | `/data/data/com.termux/files/home` |
| `$PREFIX` | Termux system root | `/data/data/com.termux/files/usr` |
| `$PATH` | Command search paths | Multiple directories |
| `$SHELL` | Current shell | `/data/.../bin/bash` |
| `$USER` | Current username | `u0_aXXX` |
| `$PWD` | Current directory | Current location |
| `$TERM` | Terminal type | `xterm-256color` |
| `$PS1` | Prompt string | Customizable |
| `$EDITOR` | Default editor | `nano` or `vim` |
| `$TMPDIR` | Temp directory | `$PREFIX/tmp` |

### PS1 Special Characters

| Code | Displays |
|------|----------|
| `\u` | Username |
| `\h` | Hostname |
| `\w` | Full working directory |
| `\W` | Current directory name |
| `\d` | Date |
| `\t` | Time (24-hour) |
| `\n` | Newline |
| `\$` | $ for user, # for root |

### Configuration Files

| File | Purpose |
|------|---------|
| `~/.bashrc` | Interactive shell config |
| `~/.bash_profile` | Login shell config |
| `~/.profile` | Generic profile |
| `~/.zshrc` | Zsh configuration |

---

## 🏆 BONUS: ADVANCED TIPS

### Advanced Tip 1: Environment Variable Manager

```bash
# Create a simple environment manager
# Add to ~/.bashrc

envmgr() {
    local env_dir="$HOME/.environments"
    mkdir -p "$env_dir"
    
    case "$1" in
        save)
            [[ -z "$2" ]] && echo "Usage: envmgr save <name>" && return
            env > "$env_dir/$2.env"
            echo "Environment saved as '$2'"
            ;;
        load)
            [[ -z "$2" ]] && echo "Usage: envmgr load <name>" && return
            [[ -f "$env_dir/$2.env" ]] && source "$env_dir/$2.env"
            echo "Environment '$2' loaded"
            ;;
        list)
            ls -1 "$env_dir"/*.env 2>/dev/null | xargs -n1 basename | sed 's/.env$//'
            ;;
        delete)
            [[ -z "$2" ]] && echo "Usage: envmgr delete <name>" && return
            rm -f "$env_dir/$2.env"
            echo "Environment '$2' deleted"
            ;;
        *)
            echo "Usage: envmgr {save|load|list|delete} [name]"
            ;;
    esac
}
```

### Advanced Tip 2: Dynamic PS1 with Exit Code

```bash
# Show exit code when command fails
export PS1='\[\033[0;33m\]$(ret=$?; if [ $ret -ne 0 ]; then echo "[$ret] "; fi)\[\033[0;32m\]\u@\h\[\033[0m\]:\[\033[0;34m\]\w\[\033[0m\]\$ '
```

### Advanced Tip 3: PATH Management Functions

```bash
# Add to ~/.bashrc

# Add to beginning of PATH
path_prepend() {
    [[ -d "$1" ]] && export PATH="$1:$PATH"
}

# Add to end of PATH
path_append() {
    [[ -d "$1" ]] && export PATH="$PATH:$1"
}

# Remove from PATH
path_remove() {
    export PATH=$(echo "$PATH" | tr ':' '\n' | grep -v "^$1$" | tr '\n' ':' | sed 's/:$//')
}

# Check if in PATH
path_has() {
    echo "$PATH" | tr ':' '\n' | grep -q "^$1$"
}
```

### Advanced Tip 4: Secure Environment Loading

```bash
# Securely load environment from encrypted file
# Requires: openssl

load_secure_env() {
    local env_file="$1"
    if [[ -f "$env_file" ]]; then
        echo "Enter password to decrypt environment:"
        openssl enc -aes-256-cbc -d -in "$env_file" 2>/dev/null | source /dev/stdin
        echo "Secure environment loaded"
    else
        echo "File not found: $env_file"
    fi
}

save_secure_env() {
    local env_file="$1"
    echo "Enter variables to encrypt (Ctrl+D to finish):"
    openssl enc -aes-256-cbc -out "$env_file"
    echo "Environment saved to $env_file"
}
```

### Advanced Tip 5: Environment Diff Tool

```bash
# Compare two environments
envdiff() {
    local env1=$(mktemp)
    local env2=$(mktemp)
    
    if [[ -z "$1" ]]; then
        env | sort > "$env1"
        echo "Environment saved. Make changes, then run: envdiff compare"
        echo "Temp file: $env1"
        export _ENVDIFF_FILE="$env1"
    elif [[ "$1" == "compare" ]]; then
        env | sort > "$env2"
        diff "$_ENVDIFF_FILE" "$env2"
        rm -f "$env1" "$env2"
        unset _ENVDIFF_FILE
    fi
}
```

### Advanced Tip 6: Auto-reload .bashrc on Save

```bash
# Function to edit and auto-reload bashrc
bashrc_edit() {
    local backup=~/.bashrc.backup.$(date +%Y%m%d_%H%M%S)
    cp ~/.bashrc "$backup"
    ${EDITOR:-nano} ~/.bashrc
    source ~/.bashrc
    echo ".bashrc reloaded. Backup at: $backup"
}
alias brc='bashrc_edit'
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

✅ **Environment Variables Fundamentals**
- Understood what environment variables are
- Learned the difference between shell and environment variables
- Mastered variable scope and inheritance

✅ **Key Variables**
- PATH - Command search paths
- HOME - User home directory
- PREFIX - Termux system root
- SHELL - Current shell
- PS1 - Prompt customization

✅ **Variable Operations**
- View variables: `echo $VAR`, `env`, `printenv`
- Set variables: `export VAR=value`
- Unset variables: `unset VAR`
- Make permanent: Add to `.bashrc`

✅ **Configuration Files**
- `.bashrc` - Interactive shell configuration
- `.bash_profile` - Login shell configuration
- `.profile` - Generic profile

✅ **PATH Management**
- Add directories to PATH
- Understand search order
- Create custom command directories

✅ **Prompt Customization**
- PS1 special characters
- Color codes
- Dynamic prompts with git

### Key Takeaways

1. **export makes variables global** - Child processes inherit exported variables
2. **.bashrc is your friend** - All customizations go here for persistence
3. **PATH order matters** - First match wins when searching for commands
4. **Quote your variables** - `"$VAR"` prevents issues with spaces
5. **Test before committing** - Always test changes before making permanent

---

## 🎯 INTERVIEW QUESTIONS

### Question 1
**Q: What is the difference between shell variables and environment variables?**

**Answer:**
- **Shell variables** are local to the current shell instance and not passed to child processes
- **Environment variables** are exported and inherited by child processes
- Example:
  ```bash
  SHELL_VAR="local"      # Shell variable
  export ENV_VAR="global" # Environment variable
  bash -c 'echo $SHELL_VAR'  # Empty - not inherited
  bash -c 'echo $ENV_VAR'    # "global" - inherited
  ```

---

### Question 2
**Q: What happens when you run a command in the shell? How does PATH work?**

**Answer:**
When you type a command like `python`:
1. Shell checks if it's a built-in command (like `cd`, `echo`)
2. If not, searches directories in `$PATH` from left to right
3. First executable match is executed
4. If not found anywhere in PATH, returns "command not found"

To see the path of a command: `which python` or `command -v python`

---

### Question 3
**Q: How would you add a custom directory to PATH permanently?**

**Answer:**
Add to `~/.bashrc`:
```bash
# Option 1: Append (lower priority)
export PATH="$PATH:$HOME/scripts"

# Option 2: Prepend (higher priority)
export PATH="$HOME/scripts:$PATH"

# Then reload
source ~/.bashrc
```

---

### Question 4
**Q: What is the difference between .bashrc and .bash_profile?**

**Answer:**
- `.bashrc` runs for every **interactive** shell (new terminal tab/window)
- `.bash_profile` runs for **login** shells (first login)
- Best practice: Source `.bashrc` from `.bash_profile`
- In Termux, usually `.bashrc` is sufficient for all customizations

---

### Question 5
**Q: How do you check if an environment variable is set?**

**Answer:**
```bash
# Method 1: Check if empty
if [ -z "$VAR" ]; then
    echo "VAR is not set or empty"
fi

# Method 2: Check if set (even if empty)
if [ -z "${VAR+x}" ]; then
    echo "VAR is not set"
fi

# Method 3: Use printenv
if printenv VAR > /dev/null 2>&1; then
    echo "VAR is set"
fi

# Method 4: Parameter expansion with default
echo "${VAR:-default}"  # Shows 'default' if VAR not set
```

---

### Question 6
**Q: What is PS1 and how would you customize the prompt?**

**Answer:**
PS1 defines the shell prompt. Customization examples:
```bash
# Simple
export PS1="termux> "

# With username and directory
export PS1="\u:\w\$ "

# With colors
export PS1="\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "

# With git branch
parse_git_branch() { git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'; }
export PS1="\w\$(parse_git_branch)\$ "
```

---

### Question 7
**Q: How would you make a variable read-only?**

**Answer:**
```bash
export CONFIG_PATH="/etc/config"
readonly CONFIG_PATH

# Now trying to change it will fail
CONFIG_PATH="/new/path"  # bash: CONFIG_PATH: readonly variable

# To see readonly variables
readonly -p
```

---

### Question 8
**Q: What is the difference between `export VAR=value` and `VAR=value; export VAR`?**

**Answer:**
Functionally identical - both create an environment variable. The first is shorthand:
```bash
# These are equivalent:
export VAR=value

VAR=value
export VAR

# Multiple variables:
export VAR1="val1" VAR2="val2"
```

---

### Question 9
**Q: How would you pass environment variables to a specific command only?**

**Answer:**
```bash
# Method 1: Inline
DEBUG=true ./script.sh

# Method 2: env command
env DEBUG=true ./script.sh

# Method 3: With multiple variables
NODE_ENV=production API_KEY=secret node app.js

# Clear environment for command
env -i HOME="$HOME" PATH="/bin" ./script.sh
```

---

### Question 10
**Q: How do you debug environment variable issues in a script?**

**Answer:**
```bash
# Print all variables at a point
set | grep VAR

# Use bash's xtrace mode
bash -x script.sh

# Add debugging in script
set -x  # Enable debug
# ... code ...
set +x  # Disable debug

# Check specific variable
echo "DEBUG: VAR=$VAR" >&2

# Use declare to see attributes
declare -p VAR
```

---

## 🚀 NEXT LEVEL TIPS

### Performance Optimization

```
⚡ TIP: Faster Shell Startup

Slow .bashrc can make opening terminals sluggish.

1. Profile your bashrc:
time bash -i -c exit

2. Defer heavy operations:
# Instead of running on every shell
eval "$(direnv hook bash)"  # Slow!

# Run only when needed
if command -v direnv &> /dev/null; then
    eval "$(direnv hook bash)"
fi

3. Use lazy loading for tools:
nvm() {
    unset -f nvm
    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
    nvm "$@"
}
```

### Best Practices

```
📌 BEST PRACTICE: Environment Variable Organization

# Group related variables
# ========== PATH SETTINGS ==========
export PATH="$HOME/bin:$PATH"
export PATH="$HOME/.local/bin:$PATH"

# ========== EDITOR SETTINGS ==========
export EDITOR="vim"
export VISUAL="vim"
export GIT_EDITOR="vim"

# ========== PROJECT PATHS ==========
export PROJECTS="$HOME/projects"
export SCRIPTS="$HOME/scripts"

# ========== LANGUAGE SETTINGS ==========
export LANG="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"

# ========== PYTHON ==========
export PYTHONDONTWRITEBYTECODE=1
export PYTHONUNBUFFERED=1

# ========== HISTORY ==========
export HISTSIZE=10000
export HISTFILESIZE=20000
export HISTCONTROL=ignoreboth
```

### Common Mistakes to Avoid

```
❌ MISTAKE 1: Spaces around = in assignment
Wrong: VAR = "value"
Right: VAR="value"

❌ MISTAKE 2: Forgetting quotes with spaces
Wrong: export MSG=Hello World  # Only "Hello" assigned
Right: export MSG="Hello World"

❌ MISTAKE 3: Not using $ when referencing
Wrong: echo PATH
Right: echo $PATH

❌ MISTAKE 4: Overwriting important variables
Wrong: export PATH="/my/path"  # Lost all other paths!
Right: export PATH="/my/path:$PATH"  # Append

❌ MISTAKE 5: Forgetting to export
Wrong: API_KEY="secret"; python script.py  # Not available
Right: export API_KEY="secret"; python script.py

❌ MISTAKE 6: Case sensitivity confusion
Wrong: Export path="/..."  # Lowercase 'path' ≠ 'PATH'
Right: export PATH="/..."  # Uppercase for env vars
```

### Efficiency Tips

```
⏱️ TIME SAVERS:

1. Use ${VAR:-default} for defaults
   cp "${CONFIG:-/etc/default.conf}" .

2. Chain variable operations
   export PATH="$HOME/bin:$HOME/.local/bin:$PATH"

3. Use aliases for common variable combos
   alias dev='NODE_ENV=development'
   alias prod='NODE_ENV=production'
   # Usage: dev npm start

4. Quick variable unset
   unset ${!API_*}  # Unset all API_* variables

5. Copy variable value to clipboard
   echo $API_KEY | clip  # or termux-clipboard-set

6. Reload bashrc quickly
   alias reload='source ~/.bashrc && echo "Reloaded!"'
```

---

## 📊 VISUAL DIAGRAMS

### Diagram 1: Variable Scope

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        ENVIRONMENT VARIABLE SCOPE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                      PARENT SHELL                                   │   │
│   │                                                                     │   │
│   │   Shell Variables:           Environment Variables:                │   │
│   │   MY_LOCAL="local"           export MY_GLOBAL="global"             │   │
│   │   (Not inherited)            (Inherited by children)               │   │
│   │                                                                     │   │
│   └───────────────────────────────┬─────────────────────────────────────┘   │
│                                   │                                         │
│                    ┌──────────────┴──────────────┐                         │
│                    │     fork() + exec()        │                          │
│                    ▼                           ▼                          │
│   ┌─────────────────────────────┐ ┌─────────────────────────────┐         │
│   │      CHILD PROCESS 1        │ │      CHILD PROCESS 2        │         │
│   │                             │ │                             │         │
│   │  $MY_LOCAL  → (empty)      │ │  $MY_LOCAL  → (empty)       │         │
│   │  $MY_GLOBAL → "global"     │ │  $MY_GLOBAL → "global"      │         │
│   │                             │ │                             │         │
│   │  Can modify its own copy   │ │  Modifications don't affect │         │
│   │  of MY_GLOBAL              │ │  parent or other children   │         │
│   │                             │ │                             │         │
│   └─────────────────────────────┘ └─────────────────────────────┘         │
│                                                                             │
│   KEY: Environment variables flow DOWN (parent → child), never UP          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: PATH Resolution

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        PATH RESOLUTION FLOW                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   User types: python                                                        │
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │ 1. Is "python" a shell builtin?                                     │   │
│   │    No → Continue                                                    │   │
│   └────────────────────────────────┬────────────────────────────────────┘   │
│                                    │                                        │
│   ┌────────────────────────────────▼────────────────────────────────────┐   │
│   │ 2. Is "python" an alias or function?                                │   │
│   │    No → Continue                                                    │   │
│   └────────────────────────────────┬────────────────────────────────────┘   │
│                                    │                                        │
│   ┌────────────────────────────────▼────────────────────────────────────┐   │
│   │ 3. Search PATH directories (left to right):                         │   │
│   │                                                                     │   │
│   │    PATH=/home/user/bin:$PREFIX/bin:/system/bin                     │   │
│   │         │               │              │                            │   │
│   │         ▼               ▼              ▼                            │   │
│   │    ┌─────────┐    ┌─────────┐    ┌─────────┐                       │   │
│   │    │ /home/  │    │ $PREFIX │    │ /system │                       │   │
│   │    │ user/bin│    │  /bin   │    │  /bin   │                       │   │
│   │    │         │    │         │    │         │                       │   │
│   │    │ python? │    │ python? │    │ python? │                       │   │
│   │    │   NO    │───▶│   YES!  │    │         │                       │   │
│   │    └─────────┘    └────┬────┘    └─────────┘                       │   │
│   │                        │                                            │   │
│   │                        ▼                                            │   │
│   │                    Execute: /data/.../bin/python                    │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│   TIP: Order matters! First match wins.                                    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Configuration File Loading

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    SHELL CONFIGURATION FILE LOADING                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    LOGIN SHELL (First login)                        │   │
│   │                                                                     │   │
│   │   1. /etc/profile ──────────────────────────────────────────────┐  │   │
│   │   2. ~/.bash_profile ────┐                                      │  │   │
│   │   3. ~/.bash_login ───────┼── First found wins                  │  │   │
│   │   4. ~/.profile ──────────┘                                      │  │   │
│   │                           │                                       │  │   │
│   │                           ▼                                       │  │   │
│   │   Usually sources ~/.bashrc ◄────────────────────────────────────┘  │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                 INTERACTIVE SHELL (New terminal)                    │   │
│   │                                                                     │   │
│   │   ~/.bashrc ─────────────────────────────────────────────────────── │   │
│   │   • Aliases                                                         │   │
│   │   • Functions                                                       │   │
│   │   • Prompt (PS1)                                                    │   │
│   │   • Custom PATH                                                     │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                   NON-INTERACTIVE SHELL                             │   │
│   │                                                                     │   │
│   │   bash script.sh  →  No config files loaded!                       │   │
│   │                                                                     │   │
│   │   To inherit environment:                                           │   │
│   │   bash -i script.sh  # Interactive mode                            │   │
│   │   source ~/.bashrc   # Manual load                                 │   │
│   │                                                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relevance |
|---------|-------|-----------|
| **Chapter 6** | File System Structure | Understanding $PREFIX, $HOME paths |
| **Chapter 8** | Text Editors | Setting $EDITOR variable |
| **Chapter 11** | Package Management | Commands in $PREFIX/bin |
| **Chapter 15** | Shell Scripting Basics | Using variables in scripts |
| **Chapter 16** | Shell Scripting Advanced | Environment manipulation |
| **Chapter 18** | Git Version Control | Git configuration variables |
| **Chapter 25** | Python Development | Python environment setup |
| **Chapter 35** | Node.js Development | NODE_PATH, npm config |
| **Chapter 40** | Docker in Termux | Container environment variables |

---

## 🎮 INTERACTIVE QUIZ

### Quiz: Test Your Environment Variables Knowledge!

**Question 1:** What command shows all environment variables?
- A) `ls env`
- B) `env`
- C) `show env`
- D) `cat /env`

**Question 2:** How do you make a variable available to child processes?
- A) `VAR=value`
- B) `global VAR=value`
- C) `export VAR=value`
- D) `share VAR=value`

**Question 3:** Which file is loaded for interactive shells?
- A) `.bash_profile`
- B) `.bashrc`
- C) `.profile`
- D) `.bash_login`

**Question 4:** What is the correct syntax to append to PATH?
- A) `export PATH=$PATH:/new/path`
- B) `export PATH=/new/path:$PATH`
- C) `PATH += /new/path`
- D) Both A and B are correct

**Question 5:** What does `${VAR:-default}` do?
- A) Sets VAR to default
- B) Returns default if VAR is unset or empty
- C) Deletes VAR if it equals default
- D) Errors if VAR is default

**Question 6:** Which variable stores the shell prompt?
- A) `$PROMPT`
- B) `$PS1`
- C) `$SHELL_PS`
- D) `$DISPLAY`

**Question 7:** How do you make a variable read-only?
- A) `const VAR=value`
- B) `final VAR=value`
- C) `readonly VAR`
- D) `lock VAR`

**Question 8:** What does `\w` show in PS1?
- A) Username
- B) Working directory (full path)
- C) Hostname
- D) Current directory name only

**Question 9:** How do you unset a variable?
- A) `delete VAR`
- B) `unset VAR`
- C) `remove VAR`
- D) `clear VAR`

**Question 10:** What happens when you run `VAR=value; bash -c 'echo $VAR'`?
- A) Prints "value"
- B) Prints empty
- C) Errors
- D) Prints "VAR"

**Question 11:** Which reloads .bashrc?
- A) `reload`
- B) `source ~/.bashrc`
- C) `restart`
- D) `. reload`

**Question 12:** What's the value of `$?` after `true` command?
- A) 0
- B) 1
- C) true
- D) null

**Question 13:** How to check if VAR is set (not just empty)?
- A) `[ -n "$VAR" ]`
- B) `[ -z "$VAR" ]`
- C) `[ -n "${VAR+x}" ]`
- D) `[ -z "${VAR+x}" ]`

**Question 14:** Which command shows variable attributes?
- A) `show VAR`
- B) `declare -p VAR`
- C) `attr VAR`
- D) `info VAR`

**Question 15:** What does `export` without arguments do?
- A) Exports all variables
- B) Shows all exported variables
- C) Errors
- D) Exports last variable

### Quiz Answers

| Q | Answer | Explanation |
|---|--------|-------------|
| 1 | **B** | `env` displays all environment variables |
| 2 | **C** | `export` makes variables available to child processes |
| 3 | **B** | `.bashrc` is loaded for interactive shells |
| 4 | **D** | A appends, B prepends - both valid |
| 5 | **B** | Returns default if VAR is unset or empty |
| 6 | **B** | `$PS1` stores the primary prompt |
| 7 | **C** | `readonly` makes a variable unchangeable |
| 8 | **B** | `\w` shows full working directory path |
| 9 | **B** | `unset` removes a variable |
| 10 | **B** | Prints empty - VAR wasn't exported |
| 11 | **B** | `source ~/.bashrc` reloads configuration |
| 12 | **A** | Exit code 0 means success |
| 13 | **C** | `${VAR+x}` expands to 'x' if VAR is set |
| 14 | **B** | `declare -p` shows variable attributes |
| 15 | **B** | `export` alone shows all exported variables |

---

## 🔄 TRY IT YOURSELF CHALLENGES

### Challenge 1: Custom PATH Setup
```bash
# Task: Set up a custom scripts directory
# 1. Create ~/scripts directory
# 2. Create a simple script (hello.sh) that prints "Hello from script!"
# 3. Add ~/scripts to PATH in .bashrc
# 4. Make the script executable
# 5. Test by running 'hello.sh' from anywhere

# Your commands here:
```

### Challenge 2: Prompt Customization
```bash
# Task: Create a custom prompt
# 1. Show username, hostname, and current directory
# 2. Add time in 24-hour format
# 3. Add git branch detection
# 4. Use colors: green for user, blue for directory
# 5. Make it permanent in .bashrc

# Your PS1 value:
```

### Challenge 3: Environment Manager
```bash
# Task: Create environment profiles
# 1. Create .env_dev with DEBUG=true, ENV=development
# 2. Create .env_prod with DEBUG=false, ENV=production
# 3. Write a function 'loadenv' that sources the right file
# 4. Test switching between environments

# Your code here:
```

### Challenge 4: Variable Debug Function
```bash
# Task: Create a debug function
# 1. Function should accept variable name
# 2. Show: value, length, attributes
# 3. Check if set, empty, exported

# Your function:
debug_var() {
    # Your implementation
}
```

### Challenge 5: Smart .bashrc Backup
```bash
# Task: Create backup system for .bashrc
# 1. Function to backup with timestamp
# 2. Function to restore latest backup
# 3. Function to list all backups
# 4. Function to compare current with backup

# Your functions:
```

---

## ✅ SKILL CHECK CHECKPOINTS

### Checkpoint 1: Variable Basics
- [ ] Can view variables with `echo $VAR`
- [ ] Can set variables with `export`
- [ ] Understands shell vs environment variables
- [ ] Can use `env` and `printenv`

### Checkpoint 2: Configuration
- [ ] Knows location of `.bashrc`
- [ ] Can edit `.bashrc` safely
- [ ] Can reload with `source`
- [ ] Creates backups before editing

### Checkpoint 3: PATH Management
- [ ] Understands PATH concept
- [ ] Can add directories to PATH
- [ ] Knows prepend vs append
- [ ] Can check if directory in PATH

### Checkpoint 4: Prompt Customization
- [ ] Knows PS1 variable purpose
- [ ] Can use special characters
- [ ] Can add colors to prompt
- [ ] Can add git branch detection

### Checkpoint 5: Advanced Skills
- [ ] Can use parameter expansion
- [ ] Can create readonly variables
- [ ] Can unset variables properly
- [ ] Understands variable scope

---

**Chapter Complete! 🎉**

*Upgraded to NEXT LEVEL with all powerful features!*

*Created by T3rmuxk1ng | Termux Full Course*
