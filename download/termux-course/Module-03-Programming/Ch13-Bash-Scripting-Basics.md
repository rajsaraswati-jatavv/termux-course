# Chapter 13: Bash Scripting Basics

> **Module:** 3 - Programming  
> **Chapter:** 13 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Beginner to Intermediate

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed Bash scripting concepts |
| Script Examples | 25+ practical examples |
| Commands Reference | All commands covered in chapter |
| Practice Exercises | 5 hands-on scripting tasks |
| Troubleshooting | Common scripting errors |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 13
Title: Bash Scripting Basics | Shell Scripting Seekhein | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut special hai kyunki aaj hum seekhenge Bash Scripting -
Linux automation ki foundation!

Sochiye aapko 100 files ka naam change karna hai. Manually karne mein 
kitna time lagega? Ghanton? Lekin ek bash script se ye kaam 5 second 
mein ho jaayega!

Bash scripting seekh ke aap:
- Automation kar sakte ho
- Complex tasks ko simplify kar sakte ho
- Apne tools bana sakte ho
- Time bacha sakte ho

Ye chapter beginners ke liye hai - zero se start karke advanced tak 
jaayenge. 25+ practical examples ke saath!

To chaliye shuru karte hain!

---

[SECTION 1: WHAT IS BASH SCRIPTING - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - Bash kya hai?

Bash ka full form hai "Bourne Again Shell". Ye ek command interpreter hai -
yaani ye aapke commands ko read karke execute karta hai.

Jab aap terminal mein koi command type karte ho jaise `ls`, `pwd`, `cd` -
ye sab Bash shell process karta hai.

Bash Script kya hai?

Script ek text file hai jisme multiple commands likhe hote hain. Jab aap 
script ko run karte ho, to ye saari commands ek ke baad ek execute hoti 
hain automatically.

Samjhein ye example:

    # Manual tareeka
    mkdir project
    cd project
    touch file1.txt file2.txt file3.txt
    echo "Project created" > readme.md
    ls -la

Ye 5 commands hain. Har baar ye sab type karna padega.

Lekin agar script banayein:

    # Script mein
    #!/bin/bash
    mkdir project
    cd project
    touch file1.txt file2.txt file3.txt
    echo "Project created" > readme.md
    ls -la

Ab bas ek command: bash create-project.sh

 aur kaam ho gaya!

Bash scripting use cases:

┌─────────────────────────────────────────────────────────────────────────┐
│                    BASH SCRIPTING USE CASES                              │
├─────────────────────────────────────────────────────────────────────────┤
│ ✓ System Administration - User management, backups, monitoring         │
│ ✓ File Operations - Rename, move, delete multiple files automatically  │
│ ✓ Automation - Scheduled tasks, cron jobs                              │
│ ✓ DevOps - Deployment scripts, server configuration                    │
│ ✓ Security Tools - Network scanning automation, log analysis           │
│ ✓ Data Processing - Text processing, log parsing                       │
│ ✓ Termux Tools - Custom tools for Android                              │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 2: CREATING FIRST SCRIPT - 4:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye apna pehla bash script banate hain!

Pehle ek naya file create karte hain:

    nano hello.sh

Ab file mein ye likhein:

    #!/bin/bash
    # Ye mera pehla script hai
    echo "Hello, Termux!"
    echo "Welcome to Bash Scripting"
    date
    whoami
    pwd

Ab file save karein: Ctrl+O, Enter, Ctrl+X

Dekho pehli line: #!/bin/bash

Isko kehte hain SHEBANG. Ye batata hai ki ye script Bash shell mein 
run hogi. #! ek special combination hai, aur /bin/bash interpreter 
ka path hai.

Ye line har bash script ki pehli line honi chahiye.

Script run karne ke 2 tareeke hain:

Tareeka 1 - Direct bash command:

    bash hello.sh

Tareeka 2 - Executable permission:

    chmod +x hello.sh
    ./hello.sh

Dono tareeke se script chalegi!

Output dekho:

    Hello, Termux!
    Welcome to Bash Scripting
    Tue Jan 15 10:30:45 IST 2025
    u0_a123
    /data/data/com.termux/files/home

Ye tha aapka pehla bash script! 🎉

---

[SECTION 3: VARIABLES IN BASH - 7:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab variables seekhte hain.

Variables ek container hai jisme data store karte hain. Bash mein 
variable banana easy hai:

    name="T3rmuxk1ng"
    age=25
    course="Termux Full Course"

Important rules yaad rakhein:

1. Equal sign ke dono side space NAHI hona chahiye
   WRONG: name = "John"
   RIGHT: name="John"

2. Variable use karne ke liye $ lagana padega
   echo $name
   echo ${name}

3. String value ke liye quotes use karein
   name="John Doe"  # Correct

Chaliye ek script banate hain:

    #!/bin/bash
    # Variables demo

    name="Hacker"
    tool="Termux"
    version=2025

    echo "Welcome, $name!"
    echo "You are using $tool"
    echo "Version: $version"

    # String concatenation
    full_message="Hello $name, welcome to $tool!"
    echo $full_message

Special Variables in Bash:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SPECIAL BASH VARIABLES                                 │
├────────────────┬────────────────────────────────────────────────────────┤
│ Variable       │ Description                                         │
├────────────────┼────────────────────────────────────────────────────────┤
│ $0             │ Script name                                         │
│ $1, $2...      │ Command line arguments                              │
│ $#             │ Number of arguments                                 │
│ $@             │ All arguments as array                              │
│ $*             │ All arguments as single string                      │
│ $?             │ Exit status of last command (0 = success)          │
│ $$             │ Process ID of current shell                         │
│ $!             │ Process ID of last background command               │
│ $HOME          │ User's home directory                               │
│ $PWD           │ Current working directory                           │
│ $USER          │ Current username                                    │
│ $PATH          │ Executable search path                              │
└────────────────┴────────────────────────────────────────────────────────┘

---

[SECTION 4: USER INPUT - 10:00 to 12:30]
─────────────────────────────────────────────────────────────────────────────

Ab user se input lerna seekhte hain.

`read` command se user input le sakte hain:

    #!/bin/bash
    # User input demo

    echo "Enter your name:"
    read name
    echo "Hello, $name!"

Multiple inputs:

    echo "Enter first name and last name:"
    read fname lname
    echo "Full name: $fname $lname"

Silent input (password type):

    read -s -p "Enter password: " pass
    echo
    echo "Password received!"

-p flag prompt ke saath input leta hai:

    read -p "Enter age: " age
    echo "You are $age years old"

Real example - User info script:

    #!/bin/bash
    # User information collector

    echo "═══════════════════════════════"
    echo "    USER INFORMATION FORM"
    echo "═══════════════════════════════"

    read -p "Enter your name: " name
    read -p "Enter your email: " email
    read -s -p "Enter password: " password
    echo
    read -p "Enter your age: " age

    echo ""
    echo "═══════════════════════════════"
    echo "    INFORMATION SUMMARY"
    echo "═══════════════════════════════"
    echo "Name: $name"
    echo "Email: $email"
    echo "Age: $age"
    echo "Password: [HIDDEN]"
    echo "═══════════════════════════════"

---

[SECTION 5: ARITHMETIC OPERATIONS - 12:30 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Bash mein mathematical operations ke liye special syntax chahiye.

Methods for arithmetic:

Method 1: Double Parentheses (( ))

    a=10
    b=5
    
    sum=$((a + b))
    diff=$((a - b))
    mult=$((a * b))
    div=$((a / b))
    mod=$((a % b))
    
    echo "Sum: $sum"
    echo "Difference: $diff"
    echo "Product: $mult"
    echo "Division: $div"
    echo "Modulo: $mod"

Method 2: expr command

    result=$(expr 10 + 5)
    echo $result
    
    # Note: expr mein spaces zaroori hain

Method 3: let command

    let x=10+5
    echo $x

Increment/Decrement:

    count=0
    ((count++))    # count = 1
    ((count--))    # count = 0
    ((count+=5))   # count = 5
    ((count-=2))   # count = 3

Comparison operators:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ARITHMETIC COMPARISON OPERATORS                       │
├────────────────┬─────────────────────────────────────────────────────────┤
│ Operator       │ Meaning                                          │
├────────────────┼─────────────────────────────────────────────────────────┤
│ -eq            │ Equal to                                         │
│ -ne            │ Not equal to                                     │
│ -gt            │ Greater than                                     │
│ -lt            │ Less than                                        │
│ -ge            │ Greater than or equal to                         │
│ -le            │ Less than or equal to                            │
│ ==             │ Equal (in (( )) )                                │
│ !=             │ Not equal (in (( )) )                            │
│ >              │ Greater (in (( )) )                              │
│ <              │ Less (in (( )) )                                 │
└────────────────┴─────────────────────────────────────────────────────────┘

Calculator script:

    #!/bin/bash
    # Simple calculator

    read -p "Enter first number: " num1
    read -p "Enter second number: " num2

    echo "Select operation:"
    echo "1) Addition"
    echo "2) Subtraction"
    echo "3) Multiplication"
    echo "4) Division"
    read -p "Choice: " choice

    case $choice in
        1) result=$((num1 + num2)); op="+" ;;
        2) result=$((num1 - num2)); op="-" ;;
        3) result=$((num1 * num2)); op="*" ;;
        4) result=$((num1 / num2)); op="/" ;;
        *) echo "Invalid choice"; exit 1 ;;
    esac

    echo "Result: $num1 $op $num2 = $result"

---

[SECTION 6: STRING OPERATIONS - 15:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Strings Bash mein bahut important hain. Chaliye operations dekhte hain.

String length:

    str="Hello Termux"
    echo ${#str}           # Output: 12

String concatenation:

    str1="Hello"
    str2="World"
    result="$str1 $str2"
    echo $result           # Output: Hello World

Substring extraction:

    str="Hello Termux"
    echo ${str:0:5}        # Output: Hello (0 se 5 characters)
    echo ${str:6}          # Output: Termux (6 se end tak)

String replacement:

    str="Hello World"
    echo ${str/World/Termux}    # Output: Hello Termux

Case conversion (Bash 4+):

    str="Hello"
    echo ${str,,}          # lowercase: hello
    echo ${str^^}          # UPPERCASE: HELLO

Check if string contains substring:

    str="Hello Termux"
    if [[ $str == *"Termux"* ]]; then
        echo "Found!"
    fi

String comparison:

    str1="hello"
    str2="hello"
    
    if [ "$str1" = "$str2" ]; then
        echo "Strings are equal"
    fi

---

[SECTION 7: CONDITIONAL STATEMENTS - 17:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Ab aata hai decision making - if, elif, else.

Basic if syntax:

    if [ condition ]; then
        # commands
    fi

if-else:

    if [ condition ]; then
        # true commands
    else
        # false commands
    fi

if-elif-else:

    if [ condition1 ]; then
        # commands
    elif [ condition2 ]; then
        # commands
    else
        # commands
    fi

Test operators for files:

┌─────────────────────────────────────────────────────────────────────────┐
│                    FILE TEST OPERATORS                                   │
├────────────────┬────────────────────────────────────────────────────────┤
│ Operator       │ Description                                        │
├────────────────┼────────────────────────────────────────────────────────┤
│ -e file        │ True if file exists                                │
│ -f file        │ True if file exists and is regular file            │
│ -d file        │ True if file exists and is directory               │
│ -r file        │ True if file is readable                           │
│ -w file        │ True if file is writable                           │
│ -x file        │ True if file is executable                         │
│ -s file        │ True if file exists and is not empty               │
│ -L file        │ True if file is symbolic link                      │
│ file1 -nt file2│ True if file1 is newer than file2                  │
│ file1 -ot file2│ True if file1 is older than file2                  │
└────────────────┴────────────────────────────────────────────────────────┘

Test operators for strings:

┌─────────────────────────────────────────────────────────────────────────┐
│                    STRING TEST OPERATORS                                 │
├────────────────┬────────────────────────────────────────────────────────┤
│ Operator       │ Description                                        │
├────────────────┼────────────────────────────────────────────────────────┤
│ -z string      │ True if string is empty                            │
│ -n string      │ True if string is not empty                        │
│ str1 = str2    │ True if strings are equal                          │
│ str1 != str2   │ True if strings are not equal                      │
│ str1 < str2    │ True if str1 sorts before str2                     │
│ str1 > str2    │ True if str1 sorts after str2                      │
└────────────────┴────────────────────────────────────────────────────────┘

Practical example - File checker:

    #!/bin/bash
    # File checker script

    read -p "Enter file path: " filepath

    if [ -e "$filepath" ]; then
        echo "✓ File exists"
        
        if [ -f "$filepath" ]; then
            echo "✓ It's a regular file"
        elif [ -d "$filepath" ]; then
            echo "✓ It's a directory"
        fi
        
        if [ -r "$filepath" ]; then
            echo "✓ File is readable"
        fi
        
        if [ -w "$filepath" ]; then
            echo "✓ File is writable"
        fi
        
        if [ -x "$filepath" ]; then
            echo "✓ File is executable"
        fi
    else
        echo "✗ File does not exist"
    fi

Logical operators:

    # AND
    if [ condition1 ] && [ condition2 ]; then
        echo "Both true"
    fi

    # OR
    if [ condition1 ] || [ condition2 ]; then
        echo "At least one true"
    fi

    # NOT
    if [ ! condition ]; then
        echo "Condition is false"
    fi

---

[SECTION 8: LOOPS - 21:00 to 25:00]
─────────────────────────────────────────────────────────────────────────────

Loops se aap same kaam repeatedly kar sakte ho.

FOR LOOP - Most common:

    # Basic for loop
    for i in 1 2 3 4 5; do
        echo "Number: $i"
    done

    # Range (sequence)
    for i in {1..10}; do
        echo "Count: $i"
    done

    # C-style for loop
    for ((i=0; i<5; i++)); do
        echo "Iteration: $i"
    done

    # Loop through files
    for file in *.txt; do
        echo "Processing: $file"
    done

    # Loop through command output
    for user in $(cat users.txt); do
        echo "User: $user"
    done

WHILE LOOP - Run until condition false:

    count=0
    while [ $count -lt 5 ]; do
        echo "Count: $count"
        ((count++))
    done

    # Read file line by line
    while read line; do
        echo "Line: $line"
    done < file.txt

    # Infinite loop with break
    while true; do
        read -p "Continue? (y/n): " choice
        if [ "$choice" = "n" ]; then
            break
        fi
    done

UNTIL LOOP - Run until condition true:

    count=0
    until [ $count -ge 5 ]; do
        echo "Count: $count"
        ((count++))
    done

Loop control:

    # break - exit loop
    for i in {1..10}; do
        if [ $i -eq 5 ]; then
            break
        fi
        echo $i
    done

    # continue - skip iteration
    for i in {1..5}; do
        if [ $i -eq 3 ]; then
            continue
        fi
        echo $i
    done

---

[SECTION 9: ARRAYS - 25:00 to 27:30]
─────────────────────────────────────────────────────────────────────────────

Bash mein arrays bhi support hain.

Array declaration:

    # Method 1
    fruits=("Apple" "Banana" "Orange")

    # Method 2
    declare -a fruits
    fruits[0]="Apple"
    fruits[1]="Banana"
    fruits[2]="Orange"

Accessing elements:

    echo ${fruits[0]}       # First element: Apple
    echo ${fruits[1]}       # Second element: Banana
    echo ${fruits[-1]}      # Last element: Orange

All elements:

    echo ${fruits[@]}       # All elements
    echo ${fruits[*]}       # All elements

Array length:

    echo ${#fruits[@]}      # Number of elements
    echo ${#fruits[0]}      # Length of first element

Loop through array:

    for fruit in "${fruits[@]}"; do
        echo "Fruit: $fruit"
    done

    # With index
    for i in "${!fruits[@]}"; do
        echo "Index $i: ${fruits[$i]}"
    done

Add/remove elements:

    fruits+=("Mango")       # Add element
    unset fruits[1]         # Remove element at index 1

Associative arrays (key-value):

    declare -A user
    user[name]="John"
    user[age]=25
    user[city]="Mumbai"

    echo ${user[name]}
    echo ${user[age]}

---

[SECTION 10: FUNCTIONS - 27:30 to 30:00]
─────────────────────────────────────────────────────────────────────────────

Functions code ko reusable banate hain.

Function syntax:

    # Method 1
    function greet() {
        echo "Hello, World!"
    }

    # Method 2
    greet() {
        echo "Hello, World!"
    }

    # Call function
    greet

Function with arguments:

    greet() {
        echo "Hello, $1!"
        echo "You are $2 years old"
    }

    greet "John" 25

Function with return value:

    add() {
        result=$(($1 + $2))
        echo $result
    }

    sum=$(add 10 20)
    echo "Sum: $sum"

Local variables:

    myfunction() {
        local x=10     # Local scope
        y=20           # Global scope
    }

Real example - Menu system:

    #!/bin/bash

    show_menu() {
        clear
        echo "═══════════════════════════════"
        echo "         MAIN MENU"
        echo "═══════════════════════════════"
        echo "1. System Information"
        echo "2. Disk Usage"
        echo "3. Memory Usage"
        echo "4. Network Info"
        echo "5. Exit"
        echo "═══════════════════════════════"
    }

    sys_info() {
        echo "System: $(uname -a)"
        echo "User: $(whoami)"
        echo "Home: $HOME"
    }

    disk_usage() {
        df -h
    }

    mem_usage() {
        free -h
    }

    # Main loop
    while true; do
        show_menu
        read -p "Enter choice: " choice
        
        case $choice in
            1) sys_info ;;
            2) disk_usage ;;
            3) mem_usage ;;
            4) ifconfig 2>/dev/null || ip addr ;;
            5) echo "Goodbye!"; exit 0 ;;
            *) echo "Invalid choice" ;;
        esac
        
        read -p "Press Enter to continue..."
    done

---

[SECTION 11: DEBUGGING SCRIPTS - 30:00 to 32:00]
─────────────────────────────────────────────────────────────────────────────

Debugging bahut important hai scripting mein.

Method 1: bash -x

    bash -x script.sh

Ye har command ko print karta hai before execution (+ sign ke saath).

Method 2: set -x in script

    #!/bin/bash
    set -x    # Enable debug mode
    
    echo "Hello"
    
    set +x    # Disable debug mode

Method 3: set -e (Exit on error)

    #!/bin/bash
    set -e    # Script will exit if any command fails

Method 4: set -u (Error on undefined variable)

    #!/bin/bash
    set -u    # Error if undefined variable used

Method 5: All checks combined

    #!/bin/bash
    set -euo pipefail

Common debugging tips:

1. echo statements add karein variable values check karne ke liye
2. ShellCheck tool use karein: shellcheck script.sh
3. Syntax check: bash -n script.sh

---

[SECTION 12: PRACTICAL EXAMPLES - 32:00 to 35:00]
─────────────────────────────────────────────────────────────────────────────

Ab main kuch practical scripts dikhata hoon jo aap daily use kar sakte ho.

Example 1: System Backup Script

    #!/bin/bash
    # Backup script

    backup_dir="$HOME/backups"
    date=$(date +%Y%m%d_%H%M%S)
    
    mkdir -p "$backup_dir"
    
    echo "Creating backup..."
    tar -czf "$backup_dir/backup_$date.tar.gz" -C $HOME .
    echo "Backup created: backup_$date.tar.gz"

Example 2: File Organizer

    #!/bin/bash
    # Organize files by extension

    for file in *; do
        if [ -f "$file" ]; then
            ext="${file##*.}"
            mkdir -p "$ext"
            mv "$file" "$ext/"
        fi
    done
    echo "Files organized!"

Example 3: Network Scanner

    #!/bin/bash
    # Simple network scanner

    read -p "Enter network (e.g., 192.168.1): " network
    
    echo "Scanning network..."
    for i in {1..254}; do
        if ping -c 1 -W 1 "$network.$i" &>/dev/null; then
            echo "Host up: $network.$i"
        fi
    done

Example 4: Password Generator

    #!/bin/bash
    # Password generator

    length=${1:-12}
    chars='abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%'
    
    password=$(cat /dev/urandom | tr -dc "$chars" | fold -w "$length" | head -n 1)
    echo "Generated password: $password"

Example 5: Log Analyzer

    #!/bin/bash
    # Analyze log file

    logfile="$1"
    
    echo "Total lines: $(wc -l < "$logfile")"
    echo "Errors: $(grep -c "ERROR" "$logfile")"
    echo "Warnings: $(grep -c "WARN" "$logfile")"
    echo "Unique IPs: $(grep -oE '[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+' "$logfile" | sort -u | wc -l)"

---

[SECTION 13: SUMMARY & NEXT CHAPTER PREVIEW - 35:00 to 37:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 13 complete! Let's summarize:

✅ Bash scripting kya hai - Automation ka powerful tool
✅ Shebang - #!/bin/bash script ki pehli line
✅ Variables - Data store karna, special variables
✅ User input - read command ke saath
✅ Arithmetic - (( )), expr, let
✅ String operations - Length, substring, replacement
✅ Conditional statements - if, elif, else
✅ Test operators - Files, strings, numbers ke liye
✅ Loops - for, while, until
✅ Arrays - Indexed aur associative
✅ Functions - Reusable code
✅ Debugging - bash -x, set options

Important commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 13 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ chmod +x script.sh      │ Make script executable                       │
│ bash script.sh          │ Run script with bash                         │
│ bash -x script.sh       │ Debug script                                 │
│ ./script.sh             │ Execute script directly                      │
│ read -p "Prompt: " var  │ Get user input with prompt                   │
│ echo ${#var}            │ Get string length                            │
│ [[ $str == *"sub"* ]]   │ Check if string contains substring           │
│ set -e                  │ Exit on error                                │
│ set -x                  │ Enable debug mode                            │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 14 mein hum seekhenge:
- Advanced bash scripting
- Error handling
- Signal trapping
- Process management
- Regular expressions
- Here documents
- Process substitution

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 14!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. What is Bash Scripting?

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BASH SCRIPTING OVERVIEW                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Bash (Bourne Again Shell) is:                                          │
│  ├── Command interpreter (shell)                                        │
│  ├── Default shell on most Linux distributions                          │
│  ├── Available on Termux/Android                                        │
│  └── Powerful scripting language                                        │
│                                                                          │
│  Bash Script is:                                                        │
│  ├── A text file containing commands                                    │
│  ├── Executed line by line                                              │
│  ├── Can use variables, loops, functions                                │
│  └── Perfect for automation tasks                                       │
│                                                                          │
│  Why Bash Scripting?                                                    │
│  ├── Automate repetitive tasks                                          │
│  ├── Create custom tools                                                │
│  ├── System administration                                              │
│  ├── File processing                                                    │
│  ├── Text manipulation                                                  │
│  └── Build complex workflows                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Creating Shell Scripts

```bash
# Step 1: Create file with .sh extension
nano myscript.sh

# Step 2: Add shebang line (FIRST LINE!)
#!/bin/bash

# Step 3: Write your code
echo "Hello World"

# Step 4: Save and exit
# nano: Ctrl+O, Enter, Ctrl+X

# Step 5: Make executable
chmod +x myscript.sh

# Step 6: Run script
./myscript.sh
# OR
bash myscript.sh
```

### 3. Shebang (#!)

The shebang tells the system which interpreter to use:

```bash
#!/bin/bash          # Bash shell
#!/bin/sh            # POSIX shell
#!/usr/bin/env bash  # Portable bash (recommended)
#!/usr/bin/python3   # Python script
#!/usr/bin/env node  # Node.js script
```

**Why use #!/usr/bin/env bash?**
- More portable across different systems
- Works even if bash is not in /bin
- Recommended for cross-platform scripts

### 4. Variables in Bash

```bash
# Variable assignment (NO SPACES around =)
name="John"
age=25
PI=3.14

# Using variables
echo $name
echo ${name}          # Preferred syntax
echo "Name: $name"

# Command substitution
current_date=$(date)
files=$(ls -la)
kernel=$(uname -r)

# Read-only variable
readonly PI=3.14159
PI=3.14              # Error!

# Unset variable
unset name

# Default value
echo ${name:-"Guest"}    # Use "Guest" if name is unset
echo ${name:="Guest"}    # Assign "Guest" if name is unset
```

### 5. User Input (read command)

```bash
# Basic input
read name

# With prompt
read -p "Enter name: " name

# Silent input (passwords)
read -s -p "Password: " pass

# With timeout (seconds)
read -t 5 -p "Quick! Enter name: " name

# Limit characters
read -n 1 -p "Continue? (y/n): " choice

# Read into array
read -a words <<< "one two three"

# Multiple variables
read -p "First and Last name: " first last

# IFS (Internal Field Separator)
IFS=',' read -ra emails <<< "a@b.com,c@d.com,e@f.com"
```

### 6. Arithmetic Operations

```bash
# Method 1: $(( )) - Most common
a=10
b=3
echo $((a + b))      # Addition: 13
echo $((a - b))      # Subtraction: 7
echo $((a * b))      # Multiplication: 30
echo $((a / b))      # Division: 3 (integer)
echo $((a % b))      # Modulo: 1
echo $((a ** b))     # Exponent: 1000

# Method 2: let command
let x=5+3
let x++              # Increment
let x--              # Decrement

# Method 3: expr command
expr 5 + 3           # Spaces required!
result=$(expr 5 + 3)

# Method 4: bc for floating point
echo "scale=2; 10/3" | bc    # 3.33

# Increment styles
((count++))
((count+=5))
count=$((count+1))
```

### 7. String Operations

```bash
str="Hello World"

# Length
echo ${#str}               # 11

# Substring
echo ${str:0:5}            # Hello (position:length)
echo ${str:6}              # World (from position 6)

# Remove from start
str="/path/to/file.txt"
echo ${str#*/}             # path/to/file.txt (shortest)
echo ${str##*/}            # file.txt (longest)

# Remove from end
str="file.txt.bak"
echo ${str%.*}             # file.txt (shortest)
echo ${str%%.*}            # file (longest)

# Replacement
str="Hello World"
echo ${str/World/Termux}   # Hello Termux
echo ${str//l/L}           # HeLLo WorLd (global)

# Case conversion (Bash 4+)
str="Hello"
echo ${str^^}              # HELLO (uppercase)
echo ${str,,}              # hello (lowercase)
echo ${str^}               # Hello (first letter upper)
```

### 8. Conditional Statements

```bash
# Basic if
if [ condition ]; then
    commands
fi

# if-else
if [ condition ]; then
    commands1
else
    commands2
fi

# if-elif-else
if [ condition1 ]; then
    commands1
elif [ condition2 ]; then
    commands2
else
    commands3
fi

# Nested if
if [ condition1 ]; then
    if [ condition2 ]; then
        commands
    fi
fi

# Using [[ ]] (preferred)
if [[ $name == "John" ]]; then
    echo "Hello John"
fi

# Logical operators
if [ $a -gt 5 ] && [ $a -lt 10 ]; then
    echo "a is between 5 and 10"
fi

if [ $a -lt 5 ] || [ $a -gt 10 ]; then
    echo "a is outside 5-10"
fi

# Negation
if [ ! -f "$file" ]; then
    echo "File not found"
fi
```

### 9. Test Operators

#### File Test Operators

```bash
[ -e file ]     # Exists (any type)
[ -f file ]     # Regular file
[ -d file ]     # Directory
[ -r file ]     # Readable
[ -w file ]     # Writable
[ -x file ]     # Executable
[ -s file ]     # Not empty
[ -L file ]     # Symbolic link
[ -b file ]     # Block device
[ -c file ]     # Character device
[ -S file ]     # Socket
[ -p file ]     # Named pipe

# File comparisons
[ file1 -nt file2 ]    # Newer than
[ file1 -ot file2 ]    # Older than
[ file1 -ef file2 ]    # Same file (hard link)
```

#### String Test Operators

```bash
[ -z string ]       # Zero length (empty)
[ -n string ]       # Non-zero length
[ str1 = str2 ]     # Equal
[ str1 != str2 ]    # Not equal
[ str1 \< str2 ]    # Less than (ASCII)
[ str1 \> str2 ]    # Greater than (ASCII)

# Using [[ ]] (preferred for strings)
[[ $str == pattern ]]     # Pattern matching
[[ $str == *text* ]]      # Contains substring
[[ $str =~ regex ]]       # Regex matching
```

#### Numeric Test Operators

```bash
[ $a -eq $b ]       # Equal
[ $a -ne $b ]       # Not equal
[ $a -gt $b ]       # Greater than
[ $a -lt $b ]       # Less than
[ $a -ge $b ]       # Greater than or equal
[ $a -le $b ]       # Less than or equal

# Using (( )) for numbers
(( a == b ))        # Equal
(( a != b ))        # Not equal
(( a > b ))         # Greater than
(( a < b ))         # Less than
(( a >= b ))        # Greater than or equal
(( a <= b ))        # Less than or equal
```

### 10. Loops

#### For Loop

```bash
# List iteration
for item in apple banana orange; do
    echo $item
done

# Range
for i in {1..10}; do
    echo $i
done

# Range with step
for i in {0..100..10}; do
    echo $i
done

# C-style
for ((i=0; i<5; i++)); do
    echo $i
done

# Files
for file in *.txt; do
    echo "Processing $file"
done

# Command output
for user in $(cat users.txt); do
    echo "User: $user"
done

# Directory
for dir in */; do
    echo "Directory: $dir"
done
```

#### While Loop

```bash
# Basic while
count=0
while [ $count -lt 5 ]; do
    echo $count
    ((count++))
done

# Read file
while read line; do
    echo $line
done < file.txt

# Read with IFS
while IFS=',' read -r col1 col2 col3; do
    echo "$col1 - $col2 - $col3"
done < data.csv

# Infinite loop
while true; do
    # Do something
    sleep 1
done

# Until keystroke
while true; do
    read -t 1 -n 1 key
    if [ $? -eq 0 ]; then
        break
    fi
done
```

#### Until Loop

```bash
# Run until condition is true
count=0
until [ $count -ge 5 ]; do
    echo $count
    ((count++))
done

# Wait for service
until ping -c 1 google.com &>/dev/null; do
    echo "Waiting for network..."
    sleep 2
done
```

#### Loop Control

```bash
# break - Exit loop
for i in {1..10}; do
    [ $i -eq 5 ] && break
    echo $i
done

# continue - Skip iteration
for i in {1..10}; do
    [ $((i%2)) -eq 0 ] && continue
    echo $i    # Only odd numbers
done

# Nested loops
for i in {1..3}; do
    for j in {1..3}; do
        echo "i=$i, j=$j"
    done
done
```

### 11. Arrays

```bash
# Indexed Arrays

# Declaration
arr=(one two three four)
declare -a arr

# Assignment
arr[0]="one"
arr[1]="two"
arr[2]="three"

# Access
echo ${arr[0]}          # First element
echo ${arr[-1]}         # Last element
echo ${arr[@]}          # All elements
echo ${arr[*]}          # All elements

# Length
echo ${#arr[@]}         # Number of elements
echo ${#arr[0]}         # Length of first element

# Indices
echo ${!arr[@]}         # All indices

# Add element
arr+=("five")

# Remove element
unset arr[2]

# Slice
echo ${arr[@]:1:2}      # Elements from index 1, count 2

# Loop
for element in "${arr[@]}"; do
    echo $element
done

for i in "${!arr[@]}"; do
    echo "Index $i: ${arr[$i]}"
done

# Associative Arrays

# Declaration
declare -A user

# Assignment
user[name]="John"
user[age]=25
user[city]="Mumbai"

# Access
echo ${user[name]}
echo ${user[age]}

# All keys
echo ${!user[@]}

# All values
echo ${user[@]}

# Loop
for key in "${!user[@]}"; do
    echo "$key: ${user[$key]}"
done
```

### 12. Functions

```bash
# Basic function
greet() {
    echo "Hello!"
}
greet

# With keyword
function greet() {
    echo "Hello!"
}

# Arguments
greet() {
    echo "Hello, $1!"
    echo "Age: $2"
}
greet "John" 25

# All arguments
show_args() {
    echo "All args: $@"
    echo "Number of args: $#"
    echo "First arg: $1"
    echo "Script name: $0"
}

# Return value
add() {
    echo $(($1 + $2))
}
result=$(add 5 3)
echo $result

# Return status
is_even() {
    if [ $(($1 % 2)) -eq 0 ]; then
        return 0    # True
    else
        return 1    # False
    fi
}

if is_even 4; then
    echo "Even!"
fi

# Local variables
myfunc() {
    local x=10
    echo $x
}

# Recursive function
factorial() {
    if [ $1 -le 1 ]; then
        echo 1
    else
        local prev=$(factorial $(($1 - 1)))
        echo $(($1 * prev))
    fi
}
factorial 5

# Passing array
show_array() {
    local arr=("$@")
    for element in "${arr[@]}"; do
        echo $element
    fi
}
show_array "${myarray[@]}"
```

### 13. Script Permissions and Execution

```bash
# Permission system
# r = read (4)
# w = write (2)
# x = execute (1)

# View permissions
ls -l script.sh

# Add execute permission
chmod +x script.sh

# Remove execute permission
chmod -x script.sh

# Explicit permissions
chmod 755 script.sh    # rwxr-xr-x
chmod 700 script.sh    # rwx------

# Execute methods
./script.sh            # Direct (needs execute permission)
bash script.sh         # Via bash interpreter
source script.sh       # In current shell
. script.sh            # Same as source

# Difference between execute and source
# Execute: Runs in new subprocess
# Source: Runs in current shell

# Check if script is sourced or executed
if [[ "${BASH_SOURCE[0]}" != "${0}" ]]; then
    echo "Script is sourced"
else
    echo "Script is executed"
fi
```

### 14. Debugging Scripts

```bash
# Debug entire script
bash -x script.sh

# Debug parts of script
#!/bin/bash
echo "Starting..."
set -x              # Start debug
# Debug code here
set +x              # Stop debug
echo "Done..."

# Exit on error
set -e              # Exit if any command fails

# Error on undefined variable
set -u              # Error if using undefined variable

# Pipeline failures
set -o pipefail     # Pipeline fails if any command fails

# Combined (strict mode)
set -euo pipefail

# Verbose mode
bash -v script.sh   # Show each line before execution

# No execution (syntax check)
bash -n script.sh

# Debug traps
trap 'echo "Error on line $LINENO"' ERR

# Function trace
set -o functrace    # Inherit traps in functions

# Using PS4 for better debugging
export PS4='+(${BASH_SOURCE}:${LINENO}): ${FUNCNAME[0]:+${FUNCNAME[0]}(): }'
bash -x script.sh
```

---

## 📝 25+ SCRIPT EXAMPLES

### Example 1: Hello World

```bash
#!/bin/bash
# hello.sh - Basic script

echo "Hello, World!"
echo "Welcome to Bash Scripting"
echo "Current time: $(date)"
echo "Current user: $(whoami)"
```

### Example 2: Variables Demo

```bash
#!/bin/bash
# variables.sh - Variable examples

# String variables
name="T3rmuxk1ng"
course="Termux Full Course"

# Number variables
chapter=13
year=2025

# Command substitution
current_date=$(date +%Y-%m-%d)
home_dir=$HOME

echo "Name: $name"
echo "Course: $course"
echo "Chapter: $chapter"
echo "Date: $current_date"
echo "Home: $home_dir"
```

### Example 3: User Input Script

```bash
#!/bin/bash
# user_input.sh - Get user input

echo "═══════════════════════════════"
echo "    USER REGISTRATION FORM"
echo "═══════════════════════════════"

read -p "Enter your name: " name
read -p "Enter your email: " email
read -s -p "Enter password: " password
echo
read -p "Enter your age: " age

echo ""
echo "═══════════════════════════════"
echo "    REGISTRATION SUMMARY"
echo "═══════════════════════════════"
echo "Name: $name"
echo "Email: $email"
echo "Age: $age years"
echo "Password: ********"
echo "═══════════════════════════════"
```

### Example 4: Calculator

```bash
#!/bin/bash
# calculator.sh - Simple calculator

read -p "Enter first number: " num1
read -p "Enter second number: " num2

echo ""
echo "Select Operation:"
echo "1) Addition (+)"
echo "2) Subtraction (-)"
echo "3) Multiplication (*)"
echo "4) Division (/)"
echo "5) Modulo (%)"
read -p "Choice [1-5]: " choice

case $choice in
    1) 
        result=$((num1 + num2))
        echo "Result: $num1 + $num2 = $result"
        ;;
    2) 
        result=$((num1 - num2))
        echo "Result: $num1 - $num2 = $result"
        ;;
    3) 
        result=$((num1 * num2))
        echo "Result: $num1 × $num2 = $result"
        ;;
    4) 
        if [ $num2 -ne 0 ]; then
            result=$((num1 / num2))
            echo "Result: $num1 ÷ $num2 = $result"
        else
            echo "Error: Division by zero!"
        fi
        ;;
    5) 
        result=$((num1 % num2))
        echo "Result: $num1 % $num2 = $result"
        ;;
    *) 
        echo "Invalid choice!"
        ;;
esac
```

### Example 5: Even/Odd Checker

```bash
#!/bin/bash
# even_odd.sh - Check if number is even or odd

read -p "Enter a number: " num

if [ $((num % 2)) -eq 0 ]; then
    echo "$num is Even"
else
    echo "$num is Odd"
fi
```

### Example 6: Grade Calculator

```bash
#!/bin/bash
# grade.sh - Calculate grade based on marks

read -p "Enter marks (0-100): " marks

if [ $marks -ge 90 ]; then
    grade="A+"
elif [ $marks -ge 80 ]; then
    grade="A"
elif [ $marks -ge 70 ]; then
    grade="B"
elif [ $marks -ge 60 ]; then
    grade="C"
elif [ $marks -ge 50 ]; then
    grade="D"
else
    grade="F"
fi

echo "Marks: $marks"
echo "Grade: $grade"
```

### Example 7: File Checker

```bash
#!/bin/bash
# file_check.sh - Check file properties

read -p "Enter file path: " filepath

if [ -e "$filepath" ]; then
    echo "✓ File exists"
    
    [ -f "$filepath" ] && echo "✓ Regular file"
    [ -d "$filepath" ] && echo "✓ Directory"
    [ -r "$filepath" ] && echo "✓ Readable"
    [ -w "$filepath" ] && echo "✓ Writable"
    [ -x "$filepath" ] && echo "✓ Executable"
    [ -s "$filepath" ] && echo "✓ Non-empty" || echo "○ Empty file"
    
    # File size
    size=$(stat -c%s "$filepath" 2>/dev/null || stat -f%z "$filepath" 2>/dev/null)
    echo "Size: $size bytes"
    
    # Line count (if text file)
    lines=$(wc -l < "$filepath" 2>/dev/null)
    [ -n "$lines" ] && echo "Lines: $lines"
else
    echo "✗ File does not exist"
fi
```

### Example 8: Directory Creator

```bash
#!/bin/bash
# create_dirs.sh - Create multiple directories

read -p "Enter parent directory name: " parent
read -p "Enter number of subdirectories: " count
read -p "Enter prefix for subdirectories: " prefix

mkdir -p "$parent"

for i in $(seq 1 $count); do
    mkdir -p "$parent/${prefix}_$i"
    echo "Created: $parent/${prefix}_$i"
done

echo ""
echo "Directory structure:"
tree "$parent" 2>/dev/null || ls -R "$parent"
```

### Example 9: File Counter

```bash
#!/bin/bash
# file_counter.sh - Count files by type

directory=${1:-.}

echo "Analyzing directory: $directory"
echo ""

# Count by extension
declare -A extensions

for file in "$directory"/*; do
    if [ -f "$file" ]; then
        ext="${file##*.}"
        ((extensions[$ext]++))
    fi
done

echo "File count by extension:"
echo "═════════════════════════"

for ext in "${!extensions[@]}"; do
    printf "%-10s: %d\n" ".$ext" "${extensions[$ext]}"
done

echo ""
echo "Total files: $(ls -1 "$directory" | wc -l)"
echo "Directories: $(ls -d "$directory"/*/ 2>/dev/null | wc -l)"
```

### Example 10: Backup Script

```bash
#!/bin/bash
# backup.sh - Simple backup script

backup_source="$HOME"
backup_dest="$HOME/backups"
date_stamp=$(date +%Y%m%d_%H%M%S)
backup_file="backup_${date_stamp}.tar.gz"

# Create backup directory
mkdir -p "$backup_dest"

# Create backup
echo "Creating backup..."
tar -czf "${backup_dest}/${backup_file}" \
    --exclude="$backup_dest" \
    --exclude="*.cache" \
    --exclude="*.tmp" \
    -C "$backup_source" . 2>/dev/null

if [ $? -eq 0 ]; then
    echo "✓ Backup created: ${backup_file}"
    echo "✓ Location: ${backup_dest}"
    echo "✓ Size: $(du -h "${backup_dest}/${backup_file}" | cut -f1)"
else
    echo "✗ Backup failed!"
fi
```

### Example 11: Password Generator

```bash
#!/bin/bash
# password_gen.sh - Generate random passwords

length=${1:-16}
count=${2:-1}

echo "Generating $count password(s) of $length characters..."
echo ""

chars='abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()'

for i in $(seq 1 $count); do
    password=$(cat /dev/urandom | tr -dc "$chars" | fold -w "$length" | head -n 1)
    echo "Password $i: $password"
done
```

### Example 12: String Manipulator

```bash
#!/bin/bash
# string_ops.sh - String operations demo

read -p "Enter a string: " str

echo ""
echo "String Operations:"
echo "═══════════════════════════════"
echo "Original: $str"
echo "Length: ${#str}"
echo "Uppercase: ${str^^}"
echo "Lowercase: ${str,,}"
echo "First 5 chars: ${str:0:5}"
echo "Last 5 chars: ${str: -5}"
echo "Reverse: $(echo "$str" | rev)"

# Word count
words=$(echo "$str" | wc -w)
echo "Word count: $words"

# Character count
chars=$(echo -n "$str" | wc -c)
echo "Character count: $chars"
```

### Example 13: Number Guesser Game

```bash
#!/bin/bash
# guess_game.sh - Number guessing game

target=$((RANDOM % 100 + 1))
attempts=0

echo "═══════════════════════════════"
echo "   NUMBER GUESSING GAME"
echo "═══════════════════════════════"
echo "I'm thinking of a number between 1 and 100"
echo ""

while true; do
    read -p "Your guess: " guess
    ((attempts++))
    
    if [ $guess -lt $target ]; then
        echo "Too low! Try again."
    elif [ $guess -gt $target ]; then
        echo "Too high! Try again."
    else
        echo ""
        echo "🎉 CORRECT! You got it in $attempts attempts!"
        break
    fi
done
```

### Example 14: Simple Menu System

```bash
#!/bin/bash
# menu.sh - Interactive menu system

show_menu() {
    clear
    echo "═══════════════════════════════"
    echo "       SYSTEM MENU"
    echo "═══════════════════════════════"
    echo "1. Show Date & Time"
    echo "2. Show Calendar"
    echo "3. Show Disk Usage"
    echo "4. Show Memory Usage"
    echo "5. Show Users"
    echo "6. Network Info"
    echo "7. System Info"
    echo "8. Exit"
    echo "═══════════════════════════════"
}

while true; do
    show_menu
    read -p "Enter choice [1-8]: " choice
    
    case $choice in
        1) echo ""; date; echo "" ;;
        2) echo ""; cal; echo "" ;;
        3) echo ""; df -h; echo "" ;;
        4) echo ""; free -h; echo "" ;;
        5) echo ""; who; echo "" ;;
        6) echo ""; ip addr 2>/dev/null || ifconfig; echo "" ;;
        7) echo ""; uname -a; echo "" ;;
        8) echo "Goodbye!"; exit 0 ;;
        *) echo "Invalid choice!"; sleep 1 ;;
    esac
    
    read -p "Press Enter to continue..."
done
```

### Example 15: For Loop Examples

```bash
#!/bin/bash
# for_loops.sh - For loop examples

echo "═══════════════════════════════"
echo "   FOR LOOP EXAMPLES"
echo "═══════════════════════════════"

echo ""
echo "1. Simple iteration:"
for i in 1 2 3 4 5; do
    echo "  Number: $i"
done

echo ""
echo "2. Range iteration:"
for i in {1..5}; do
    echo "  Count: $i"
done

echo ""
echo "3. C-style loop:"
for ((i=0; i<5; i++)); do
    echo "  Iteration: $i"
done

echo ""
echo "4. Files in directory:"
for file in *.sh; do
    [ -f "$file" ] && echo "  Script: $file"
done

echo ""
echo "5. Command output:"
for user in $(cut -d: -f1 /etc/passwd | head -5); do
    echo "  User: $user"
done

echo ""
echo "6. Array iteration:"
fruits=("Apple" "Banana" "Orange" "Mango")
for fruit in "${fruits[@]}"; do
    echo "  Fruit: $fruit"
done
```

### Example 16: While Loop Examples

```bash
#!/bin/bash
# while_loops.sh - While loop examples

echo "═══════════════════════════════"
echo "   WHILE LOOP EXAMPLES"
echo "═══════════════════════════════"

echo ""
echo "1. Counter:"
count=1
while [ $count -le 5 ]; do
    echo "  Count: $count"
    ((count++))
done

echo ""
echo "2. Reading file (simulated):"
echo -e "Line 1\nLine 2\nLine 3" | while read line; do
    echo "  Read: $line"
done

echo ""
echo "3. Wait for file:"
file="/tmp/test_file_$$"
echo "  Creating file in 3 seconds..."
(sleep 3 && touch "$file") &
while [ ! -f "$file" ]; do
    echo "  Waiting..."
    sleep 1
done
echo "  File created!"
rm -f "$file"

echo ""
echo "4. Infinite loop with break:"
count=0
while true; do
    ((count++))
    echo "  Iteration: $count"
    [ $count -ge 3 ] && break
done
echo "  Loop ended"
```

### Example 17: Array Operations

```bash
#!/bin/bash
# arrays.sh - Array examples

echo "═══════════════════════════════"
echo "   ARRAY EXAMPLES"
echo "═══════════════════════════════"

# Indexed array
echo ""
echo "1. Indexed Array:"
languages=("Python" "Bash" "JavaScript" "Go" "Rust")

echo "  All elements: ${languages[@]}"
echo "  First element: ${languages[0]}"
echo "  Last element: ${languages[-1]}"
echo "  Array length: ${#languages[@]}"

echo ""
echo "2. Loop through array:"
for lang in "${languages[@]}"; do
    echo "  Language: $lang"
done

echo ""
echo "3. Add/Remove elements:"
languages+=("C++")
echo "  After adding: ${languages[@]}"

unset languages[2]
echo "  After removing index 2: ${languages[@]}"

# Associative array
echo ""
echo "4. Associative Array:"
declare -A user
user[name]="T3rmuxk1ng"
user[course]="Termux Full Course"
user[chapter]=13

echo "  Name: ${user[name]}"
echo "  Course: ${user[course]}"
echo "  Chapter: ${user[chapter]}"

echo ""
echo "5. Loop through associative array:"
for key in "${!user[@]}"; do
    echo "  $key: ${user[$key]}"
done
```

### Example 18: Function Examples

```bash
#!/bin/bash
# functions.sh - Function examples

# Simple function
greet() {
    echo "Hello, $1! Welcome to $2."
}

# Function with return value
add() {
    echo $(($1 + $2))
}

# Function with local variables
calculate_area() {
    local length=$1
    local width=$2
    local area=$((length * width))
    echo $area
}

# Recursive function
factorial() {
    if [ $1 -le 1 ]; then
        echo 1
    else
        local prev=$(factorial $(($1 - 1)))
        echo $(($1 * prev))
    fi
}

# Check if number is prime
is_prime() {
    local n=$1
    if [ $n -lt 2 ]; then
        echo "No"
        return
    fi
    for ((i=2; i*i<=n; i++)); do
        if [ $((n % i)) -eq 0 ]; then
            echo "No"
            return
        fi
    done
    echo "Yes"
}

# Demo
echo "═══════════════════════════════"
echo "   FUNCTION EXAMPLES"
echo "═══════════════════════════════"

echo ""
greet "User" "Termux"

echo ""
result=$(add 10 20)
echo "Sum of 10 and 20: $result"

echo ""
area=$(calculate_area 5 3)
echo "Area of 5x3 rectangle: $area"

echo ""
fact=$(factorial 5)
echo "Factorial of 5: $fact"

echo ""
prime=$(is_prime 17)
echo "Is 17 prime? $prime"
```

### Example 19: Case Statement

```bash
#!/bin/bash
# case.sh - Case statement examples

echo "═══════════════════════════════"
echo "   CASE STATEMENT EXAMPLES"
echo "═══════════════════════════════"

echo ""
read -p "Enter a day (1-7): " day

case $day in
    1) echo "Monday - Start of week" ;;
    2) echo "Tuesday" ;;
    3) echo "Wednesday - Mid week" ;;
    4) echo "Thursday" ;;
    5) echo "Friday - Weekend coming!" ;;
    6) echo "Saturday - Weekend!" ;;
    7) echo "Sunday - Rest day!" ;;
    *) echo "Invalid day number!" ;;
esac

echo ""
read -p "Enter a character: " char

case $char in
    [a-z]) echo "Lowercase letter" ;;
    [A-Z]) echo "Uppercase letter" ;;
    [0-9]) echo "Digit" ;;
    *) echo "Special character" ;;
esac

echo ""
read -p "Enter file extension: " ext

case $ext in
    sh) echo "Bash script" ;;
    py) echo "Python script" ;;
    js) echo "JavaScript file" ;;
    txt|md) echo "Text file" ;;
    jpg|png|gif) echo "Image file" ;;
    mp4|avi|mkv) echo "Video file" ;;
    *) echo "Unknown file type" ;;
esac
```

### Example 20: File Organizer

```bash
#!/bin/bash
# organizer.sh - Organize files by extension

target_dir=${1:-.}

echo "Organizing files in: $target_dir"
echo ""

for file in "$target_dir"/*; do
    # Skip directories
    [ -d "$file" ] && continue
    
    # Get extension
    filename=$(basename "$file")
    ext="${filename##*.}"
    
    # Skip if no extension
    [ "$ext" = "$filename" ] && continue
    
    # Create directory for extension
    mkdir -p "$target_dir/$ext"
    
    # Move file
    mv "$file" "$target_dir/$ext/"
    echo "Moved: $filename → $ext/"
done

echo ""
echo "Organization complete!"
ls -la "$target_dir"
```

### Example 21: System Monitor

```bash
#!/bin/bash
# sys_monitor.sh - Simple system monitor

clear
echo "════════════════════════════════════════════════════════════"
echo "                  SYSTEM MONITOR"
echo "════════════════════════════════════════════════════════════"
echo ""

# System info
echo "┌─────────────────────────────────────────────────────────────┐"
echo "│ SYSTEM INFORMATION                                          │"
echo "├─────────────────────────────────────────────────────────────┤"
printf "│ %-20s: %-35s │\n" "Hostname" "$(hostname)"
printf "│ %-20s: %-35s │\n" "Kernel" "$(uname -r)"
printf "│ %-20s: %-35s │\n" "Uptime" "$(uptime -p)"
printf "│ %-20s: %-35s │\n" "Shell" "$SHELL"
printf "│ %-20s: %-35s │\n" "User" "$(whoami)"
echo "└─────────────────────────────────────────────────────────────┘"

echo ""

# Memory
echo "┌─────────────────────────────────────────────────────────────┐"
echo "│ MEMORY USAGE                                                │"
echo "├─────────────────────────────────────────────────────────────┤"
free -h | awk 'NR==2 {printf "│ %-10s: %-8s / %-8s (%-15s │\n", "Memory", $3, $2, $3/$2*100"% used)"}'
free -h | awk 'NR==3 {printf "│ %-10s: %-8s / %-8s (%-15s │\n", "Swap", $3, $2, $3/$2*100"% used)"}'
echo "└─────────────────────────────────────────────────────────────┘"

echo ""

# Disk
echo "┌─────────────────────────────────────────────────────────────┐"
echo "│ DISK USAGE                                                  │"
echo "├─────────────────────────────────────────────────────────────┤"
df -h / | awk 'NR==2 {printf "│ %-10s: %-10s / %-10s (%s used)    │\n", "Root", $3, $2, $5}'
echo "└─────────────────────────────────────────────────────────────┘"

echo ""

# Date/Time
echo "┌─────────────────────────────────────────────────────────────┐"
printf "│ %-60s │\n" "Current Time: $(date '+%Y-%m-%d %H:%M:%S')"
echo "└─────────────────────────────────────────────────────────────┘"
```

### Example 22: Text Processing

```bash
#!/bin/bash
# text_process.sh - Text processing examples

echo "═══════════════════════════════"
echo "   TEXT PROCESSING"
echo "═══════════════════════════════"

read -p "Enter a sentence: " sentence

echo ""
echo "Original: $sentence"
echo ""

# Word count
words=$(echo "$sentence" | wc -w)
echo "Word count: $words"

# Character count
chars=$(echo -n "$sentence" | wc -c)
echo "Character count: $chars"

# Uppercase
echo "Uppercase: ${sentence^^}"

# Lowercase
echo "Lowercase: ${sentence,,}"

# Reverse
echo "Reversed: $(echo "$sentence" | rev)"

# First letter of each word uppercase
echo "Title case: $(echo "$sentence" | sed 's/\b\(.\)/\u\1/g')"

# Replace spaces with underscores
echo "No spaces: ${sentence// /_}"

# Remove all spaces
echo "Compact: ${sentence// /}"

# Extract words
echo ""
echo "Words in sentence:"
for word in $sentence; do
    echo "  - $word"
done
```

### Example 23: Network Scanner

```bash
#!/bin/bash
# network_scan.sh - Simple network scanner

read -p "Enter network prefix (e.g., 192.168.1): " network
read -p "Start IP (default 1): " start
read -p "End IP (default 254): " end

start=${start:-1}
end=${end:-254}

echo ""
echo "Scanning $network.$start to $network.$end..."
echo "═══════════════════════════════"
echo ""

active=0
for i in $(seq $start $end); do
    ip="$network.$i"
    if ping -c 1 -W 1 "$ip" &>/dev/null; then
        echo "✓ Host up: $ip"
        ((active++))
    fi
done

echo ""
echo "═══════════════════════════════"
echo "Scan complete!"
echo "Active hosts: $active"
```

### Example 24: Log File Analyzer

```bash
#!/bin/bash
# log_analyze.sh - Analyze log files

logfile=${1:-/var/log/syslog}

if [ ! -f "$logfile" ]; then
    echo "Log file not found: $logfile"
    exit 1
fi

echo "═══════════════════════════════"
echo "   LOG FILE ANALYZER"
echo "═══════════════════════════════"
echo "File: $logfile"
echo ""

# Basic stats
echo "┌─────────────────────────────────────────┐"
echo "│ STATISTICS                              │"
echo "├─────────────────────────────────────────┤"
printf "│ %-20s: %15d │\n" "Total lines" "$(wc -l < "$logfile")"
printf "│ %-20s: %15d │\n" "ERROR entries" "$(grep -c "ERROR" "$logfile" 2>/dev/null || echo 0)"
printf "│ %-20s: %15d │\n" "WARNING entries" "$(grep -c "WARN" "$logfile" 2>/dev/null || echo 0)"
printf "│ %-20s: %15d │\n" "INFO entries" "$(grep -c "INFO" "$logfile" 2>/dev/null || echo 0)"
echo "└─────────────────────────────────────────┘"

echo ""

# Unique IPs
echo "Unique IP addresses:"
grep -oE '[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+' "$logfile" 2>/dev/null | sort -u | head -10

echo ""

# Most recent errors
echo "Most recent ERROR entries:"
grep "ERROR" "$logfile" 2>/dev/null | tail -5
```

### Example 25: Todo List Manager

```bash
#!/bin/bash
# todo.sh - Todo list manager

TODO_FILE="$HOME/.todo_list"

# Create file if not exists
[ ! -f "$TODO_FILE" ] && touch "$TODO_FILE"

show_menu() {
    clear
    echo "═══════════════════════════════"
    echo "       TODO LIST MANAGER"
    echo "═══════════════════════════════"
    echo "1. View todos"
    echo "2. Add todo"
    echo "3. Remove todo"
    echo "4. Clear all"
    echo "5. Exit"
    echo "═══════════════════════════════"
}

view_todos() {
    echo ""
    echo "YOUR TODOS:"
    echo "───────────────────────────────"
    if [ -s "$TODO_FILE" ]; then
        nl -w2 -s'. ' "$TODO_FILE"
    else
        echo "No todos yet!"
    fi
    echo ""
}

add_todo() {
    read -p "Enter todo: " todo
    echo "$todo" >> "$TODO_FILE"
    echo "✓ Added: $todo"
}

remove_todo() {
    view_todos
    read -p "Enter number to remove: " num
    if [ "$num" -gt 0 ] 2>/dev/null; then
        sed -i "${num}d" "$TODO_FILE"
        echo "✓ Removed todo #$num"
    else
        echo "✗ Invalid number"
    fi
}

# Main loop
while true; do
    show_menu
    read -p "Choice [1-5]: " choice
    
    case $choice in
        1) view_todos ;;
        2) add_todo ;;
        3) remove_todo ;;
        4) > "$TODO_FILE"; echo "✓ All todos cleared" ;;
        5) echo "Goodbye!"; exit 0 ;;
        *) echo "Invalid choice" ;;
    esac
    
    read -p "Press Enter to continue..."
done
```

### Example 26: Temperature Converter

```bash
#!/bin/bash
# temp_convert.sh - Temperature converter

convert_c_to_f() {
    echo $(($1 * 9 / 5 + 32))
}

convert_f_to_c() {
    echo $((($1 - 32) * 5 / 9))
}

convert_c_to_k() {
    echo $(($1 + 273))
}

echo "═══════════════════════════════"
echo "   TEMPERATURE CONVERTER"
echo "═══════════════════════════════"
echo ""
echo "1. Celsius to Fahrenheit"
echo "2. Fahrenheit to Celsius"
echo "3. Celsius to Kelvin"
echo ""

read -p "Choice [1-3]: " choice
read -p "Enter temperature: " temp

case $choice in
    1) 
        result=$(convert_c_to_f $temp)
        echo "$temp°C = $result°F"
        ;;
    2) 
        result=$(convert_f_to_c $temp)
        echo "$temp°F = $result°C"
        ;;
    3) 
        result=$(convert_c_to_k $temp)
        echo "$temp°C = $result°K"
        ;;
    *) 
        echo "Invalid choice"
        ;;
esac
```

### Example 27: Countdown Timer

```bash
#!/bin/bash
# countdown.sh - Countdown timer

read -p "Enter seconds: " seconds

echo ""
echo "Countdown started..."
echo ""

while [ $seconds -gt 0 ]; do
    mins=$((seconds / 60))
    secs=$((seconds % 60))
    printf "\rTime remaining: %02d:%02d " $mins $secs
    sleep 1
    ((seconds--))
done

echo ""
echo "⏰ Time's up!"
```

### Example 28: File Renamer

```bash
#!/bin/bash
# renamer.sh - Batch file renamer

directory=${1:-.}
pattern=${2:-"file"}
extension=${3:-".txt"}

echo "Creating test files..."
for i in {1..5}; do
    touch "$directory/${pattern}_$i$extension"
done
echo "Created 5 test files"
echo ""

echo "Original files:"
ls "$directory"/${pattern}*$extension

echo ""
read -p "Enter new prefix: " new_prefix

for file in "$directory"/${pattern}*$extension; do
    [ -f "$file" ] || continue
    old_name=$(basename "$file")
    new_name="${new_prefix}_${old_name}"
    mv "$file" "$directory/$new_name"
    echo "Renamed: $old_name → $new_name"
done
```

---

## 📋 COMMANDS REFERENCE

### Script Execution Commands

```bash
# Make script executable
chmod +x script.sh

# Run script
./script.sh              # Direct execution
bash script.sh           # Via bash
source script.sh         # In current shell
. script.sh              # Same as source

# Debug script
bash -x script.sh        # Debug mode
bash -n script.sh        # Syntax check only
bash -v script.sh        # Verbose mode

# Run with options
bash -e script.sh        # Exit on error
bash -u script.sh        # Error on undefined var
```

### Variable Commands

```bash
# Set variable
var=value

# Use variable
echo $var
echo ${var}

# Command substitution
result=$(command)
result=`command`         # Old style

# Default value
echo ${var:-default}     # Use default if unset
echo ${var:=default}     # Assign default if unset

# String length
echo ${#var}

# Export variable
export VAR=value         # Available to child processes
```

### Read Command Options

```bash
read var                 # Basic input
read -p "Prompt: " var   # With prompt
read -s var              # Silent (password)
read -t 5 var            # Timeout (5 seconds)
read -n 1 var            # Single character
read -a arr              # Into array
read -r var              # Don't interpret backslashes
```

### Test Operators Quick Reference

```bash
# File tests
[ -e file ]              # Exists
[ -f file ]              # Regular file
[ -d file ]              # Directory
[ -r file ]              # Readable
[ -w file ]              # Writable
[ -x file ]              # Executable
[ -s file ]              # Not empty

# String tests
[ -z str ]               # Empty
[ -n str ]               # Not empty
[ str1 = str2 ]          # Equal
[ str1 != str2 ]         # Not equal

# Numeric tests
[ $a -eq $b ]            # Equal
[ $a -ne $b ]            # Not equal
[ $a -gt $b ]            # Greater than
[ $a -lt $b ]            # Less than
[ $a -ge $b ]            # Greater or equal
[ $a -le $b ]            # Less or equal
```

### Arithmetic Syntax

```bash
# Operations
$((a + b))               # Addition
$((a - b))               # Subtraction
$((a * b))               # Multiplication
$((a / b))               # Division
$((a % b))               # Modulo
$((a ** b))              # Exponent

# Increment/Decrement
((i++))                  # Increment
((i--))                  # Decrement
((i+=5))                 # Add 5
((i-=3))                 # Subtract 3
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Create a User Info Script

```bash
#!/bin/bash
# Exercise: Create a script that collects and displays user information

# Requirements:
# 1. Ask user for: name, age, email, favorite programming language
# 2. Store each input in a variable
# 3. Display a formatted summary
# 4. Include current date in the summary

# Your code here:

```

<details>
<summary>🔑 Solution</summary>

```bash
#!/bin/bash
# Solution: User info script

echo "═══════════════════════════════"
echo "    USER INFORMATION FORM"
echo "═══════════════════════════════"

read -p "Enter your name: " name
read -p "Enter your age: " age
read -p "Enter your email: " email
read -p "Favorite programming language: " language

current_date=$(date +%Y-%m-%d)
current_time=$(date +%H:%M:%S)

echo ""
echo "═══════════════════════════════"
echo "    INFORMATION SUMMARY"
echo "═══════════════════════════════"
echo "Name: $name"
echo "Age: $age years old"
echo "Email: $email"
echo "Favorite Language: $language"
echo ""
echo "Date: $current_date"
echo "Time: $current_time"
echo "═══════════════════════════════"
```

</details>

---

### Exercise 2: Create a Number Comparison Script

```bash
#!/bin/bash
# Exercise: Create a script that compares two numbers

# Requirements:
# 1. Ask user for two numbers
# 2. Compare them and display which is larger (or if equal)
# 3. Show sum, difference, product, and division result
# 4. Check if numbers are even or odd

# Your code here:

```

<details>
<summary>🔑 Solution</summary>

```bash
#!/bin/bash
# Solution: Number comparison

read -p "Enter first number: " num1
read -p "Enter second number: " num2

echo ""
echo "═══════════════════════════════"
echo "    NUMBER COMPARISON"
echo "═══════════════════════════════"

# Comparison
if [ $num1 -gt $num2 ]; then
    echo "$num1 is greater than $num2"
elif [ $num1 -lt $num2 ]; then
    echo "$num2 is greater than $num1"
else
    echo "Both numbers are equal!"
fi

# Arithmetic
echo ""
echo "Arithmetic Operations:"
echo "Sum: $((num1 + num2))"
echo "Difference: $((num1 - num2))"
echo "Product: $((num1 * num2))"
[ $num2 -ne 0 ] && echo "Division: $((num1 / num2))" || echo "Division: Cannot divide by zero"

# Even/Odd
echo ""
echo "Even/Odd Check:"
if [ $((num1 % 2)) -eq 0 ]; then
    echo "$num1 is Even"
else
    echo "$num1 is Odd"
fi

if [ $((num2 % 2)) -eq 0 ]; then
    echo "$num2 is Even"
else
    echo "$num2 is Odd"
fi
```

</details>

---

### Exercise 3: Create a File Manager Script

```bash
#!/bin/bash
# Exercise: Create a file management script

# Requirements:
# 1. Menu with options: create file, delete file, list files, search file
# 2. Use functions for each operation
# 3. Use loops for the menu system
# 4. Handle errors gracefully

# Your code here:

```

<details>
<summary>🔑 Solution</summary>

```bash
#!/bin/bash
# Solution: File manager

show_menu() {
    clear
    echo "═══════════════════════════════"
    echo "      FILE MANAGER"
    echo "═══════════════════════════════"
    echo "1. Create file"
    echo "2. Delete file"
    echo "3. List files"
    echo "4. Search file"
    echo "5. View file"
    echo "6. Exit"
    echo "═══════════════════════════════"
}

create_file() {
    read -p "Enter filename: " filename
    if [ -e "$filename" ]; then
        echo "File already exists!"
    else
        touch "$filename"
        echo "✓ File created: $filename"
    fi
}

delete_file() {
    read -p "Enter filename to delete: " filename
    if [ -f "$filename" ]; then
        rm "$filename"
        echo "✓ File deleted: $filename"
    else
        echo "✗ File not found!"
    fi
}

list_files() {
    echo ""
    echo "Files in current directory:"
    ls -lh | tail -n +2
}

search_file() {
    read -p "Enter filename pattern: " pattern
    echo ""
    echo "Matching files:"
    find . -name "*$pattern*" 2>/dev/null
}

view_file() {
    read -p "Enter filename: " filename
    if [ -f "$filename" ]; then
        echo ""
        echo "Content of $filename:"
        echo "───────────────────────────────"
        cat "$filename"
    else
        echo "✗ File not found!"
    fi
}

# Main loop
while true; do
    show_menu
    read -p "Choice [1-6]: " choice
    
    case $choice in
        1) create_file ;;
        2) delete_file ;;
        3) list_files ;;
        4) search_file ;;
        5) view_file ;;
        6) echo "Goodbye!"; exit 0 ;;
        *) echo "Invalid choice!" ;;
    esac
    
    echo ""
    read -p "Press Enter to continue..."
done
```

</details>

---

### Exercise 4: Create a Simple Quiz Game

```bash
#!/bin/bash
# Exercise: Create a quiz game script

# Requirements:
# 1. Ask at least 5 questions
# 2. Track the score
# 3. Show correct answer if wrong
# 4. Display final score with percentage

# Your code here:

```

<details>
<summary>🔑 Solution</summary>

```bash
#!/bin/bash
# Solution: Quiz game

echo "═══════════════════════════════"
echo "       TECH QUIZ GAME"
echo "═══════════════════════════════"
echo ""

score=0
total=5

# Question 1
echo "Q1: What does 'ls' command do?"
echo "a) List services"
echo "b) List files"
echo "c) Load system"
echo "d) Lock screen"
read -p "Answer: " ans

if [[ $ans == "b" ]]; then
    echo "✓ Correct!"
    ((score++))
else
    echo "✗ Wrong! Correct answer: b"
fi
echo ""

# Question 2
echo "Q2: What is the shebang line?"
echo "a) #!/bin/bash"
echo "b) //bin/bash"
echo "c) <!--bin/bash-->"
echo "d) /*bin/bash*/"
read -p "Answer: " ans

if [[ $ans == "a" ]]; then
    echo "✓ Correct!"
    ((score++))
else
    echo "✗ Wrong! Correct answer: a"
fi
echo ""

# Question 3
echo "Q3: Which operator checks if file exists?"
echo "a) -f"
echo "b) -e"
echo "c) -x"
echo "d) -r"
read -p "Answer: " ans

if [[ $ans == "b" ]]; then
    echo "✓ Correct!"
    ((score++))
else
    echo "✗ Wrong! Correct answer: b"
fi
echo ""

# Question 4
echo "Q4: What does $@ mean?"
echo "a) Email address"
echo "b) All arguments"
echo "c) At symbol"
echo "d) Array symbol"
read -p "Answer: " ans

if [[ $ans == "b" ]]; then
    echo "✓ Correct!"
    ((score++))
else
    echo "✗ Wrong! Correct answer: b"
fi
echo ""

# Question 5
echo "Q5: Which loop runs until condition is true?"
echo "a) for"
echo "b) while"
echo "c) until"
echo "d) loop"
read -p "Answer: " ans

if [[ $ans == "c" ]]; then
    echo "✓ Correct!"
    ((score++))
else
    echo "✗ Wrong! Correct answer: c"
fi
echo ""

# Final score
percentage=$((score * 100 / total))
echo "═══════════════════════════════"
echo "       QUIZ RESULTS"
echo "═══════════════════════════════"
echo "Score: $score / $total"
echo "Percentage: $percentage%"

if [ $percentage -ge 80 ]; then
    echo "Grade: A - Excellent! 🎉"
elif [ $percentage -ge 60 ]; then
    echo "Grade: B - Good job! 👍"
elif [ $percentage -ge 40 ]; then
    echo "Grade: C - Keep practicing! 📚"
else
    echo "Grade: F - Need more study! 📖"
fi
echo "═══════════════════════════════"
```

</details>

---

### Exercise 5: Create a System Health Checker

```bash
#!/bin/bash
# Exercise: Create a system health monitoring script

# Requirements:
# 1. Check disk space (warn if > 80% used)
# 2. Check memory usage (warn if > 80% used)
# 3. Check if critical services are running
# 4. Generate a health report
# 5. Use functions for each check

# Your code here:

```

<details>
<summary>🔑 Solution</summary>

```bash
#!/bin/bash
# Solution: System health checker

check_disk() {
    echo "═══════════════════════════════"
    echo "   DISK SPACE CHECK"
    echo "═══════════════════════════════"
    
    df -h / | awk 'NR==2 {
        used=$5
        gsub(/%/,"",used)
        printf "Disk Usage: %s (%s used)\n", $5, $3
        if (used > 80) {
            print "⚠️  WARNING: Disk usage above 80%!"
        } else {
            print "✓ Disk usage is healthy"
        }
    }'
}

check_memory() {
    echo ""
    echo "═══════════════════════════════"
    echo "   MEMORY USAGE CHECK"
    echo "═══════════════════════════════"
    
    free | awk '/Mem:/ {
        used=($3/$2)*100
        printf "Memory Usage: %.1f%% (%.1fM / %.1fM)\n", used, $3/1024, $2/1024
        if (used > 80) {
            print "⚠️  WARNING: Memory usage above 80%!"
        } else {
            print "✓ Memory usage is healthy"
        }
    }'
}

check_load() {
    echo ""
    echo "═══════════════════════════════"
    echo "   SYSTEM LOAD CHECK"
    echo "═══════════════════════════════"
    
    load=$(uptime | awk -F'load average:' '{print $2}' | awk '{print $1}' | tr -d ',')
    cpu_count=$(nproc 2>/dev/null || echo 1)
    
    echo "Load Average: $load"
    echo "CPU Cores: $cpu_count"
    
    if (( $(echo "$load > $cpu_count" | bc -l 2>/dev/null || echo 0) )); then
        echo "⚠️  WARNING: High system load!"
    else
        echo "✓ System load is normal"
    fi
}

check_network() {
    echo ""
    echo "═══════════════════════════════"
    echo "   NETWORK CONNECTIVITY"
    echo "═══════════════════════════════"
    
    if ping -c 1 -W 2 google.com &>/dev/null; then
        echo "✓ Internet connection: Active"
    else
        echo "✗ Internet connection: Inactive"
    fi
}

generate_report() {
    echo ""
    echo "═══════════════════════════════"
    echo "   HEALTH REPORT SUMMARY"
    echo "═══════════════════════════════"
    echo "Hostname: $(hostname)"
    echo "Date: $(date '+%Y-%m-%d %H:%M:%S')"
    echo "Uptime: $(uptime -p)"
    echo "Kernel: $(uname -r)"
    echo "═══════════════════════════════"
}

# Main execution
clear
echo "╔══════════════════════════════════════════════════════════════╗"
echo "║              SYSTEM HEALTH CHECKER                           ║"
echo "║              Generated: $(date '+%Y-%m-%d %H:%M:%S')                       ║"
echo "╚══════════════════════════════════════════════════════════════╝"

check_disk
check_memory
check_load
check_network
generate_report
```

</details>

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Permission denied"

```bash
# Cause: Script not executable

# Solution 1: Add execute permission
chmod +x script.sh

# Solution 2: Run with bash
bash script.sh

# Solution 3: Check permissions
ls -la script.sh
```

### Problem 2: "command not found"

```bash
# Cause: Script uses wrong shebang or bad PATH

# Solution 1: Check shebang
head -1 script.sh
# Should be: #!/bin/bash or #!/usr/bin/env bash

# Solution 2: Use full path to bash
/bin/bash script.sh

# Solution 3: Check if bash is installed
which bash
```

### Problem 3: Script works with bash but not ./script.sh

```bash
# Cause: Wrong shebang line

# Wrong shebang examples:
#!bin/bash          # Missing /
#!/bin/sh           # Different shell

# Correct:
#!/bin/bash
# Or portable:
#!/usr/bin/env bash
```

### Problem 4: Variables not expanding

```bash
# Cause: Using single quotes instead of double quotes

# Wrong (no expansion):
echo 'Hello $name'
# Output: Hello $name

# Correct (expansion):
echo "Hello $name"
# Output: Hello John
```

### Problem 5: "[: too many arguments"

```bash
# Cause: Unquoted variable in test

# Wrong:
[ $name = "John Doe" ]    # Error if name has space

# Correct:
[ "$name" = "John Doe" ]  # Always quote variables

# Better: Use [[ ]]
[[ $name == "John Doe" ]] # No quoting needed
```

### Problem 6: Script hangs

```bash
# Cause: Infinite loop or waiting for input

# Debug: Check where it hangs
bash -x script.sh

# Solution: Add timeout to read
read -t 10 -p "Enter name: " name

# Solution: Add counter to loops
count=0
while [ condition ]; do
    ((count++))
    [ $count -gt 100 ] && break    # Safety limit
done
```

### Problem 7: Arithmetic not working

```bash
# Cause: Wrong syntax

# Wrong:
result = $a + $b           # Spaces around =
result=$a+$b              # No arithmetic evaluation

# Correct:
result=$((a + b))
result=$(expr $a + $b)
((result = a + b))
```

### Problem 8: String comparison fails

```bash
# Cause: Using -eq for strings

# Wrong:
[ "$str1" -eq "$str2" ]    # -eq is for numbers

# Correct:
[ "$str1" = "$str2" ]      # Use = for strings
[[ "$str1" == "$str2" ]]   # Or [[ with ==
```

### Problem 9: Array index out of bounds

```bash
# Cause: Accessing non-existent index

# Check if index exists:
arr=(a b c)
if [ -n "${arr[5]+x}" ]; then
    echo "Index 5 exists"
else
    echo "Index 5 does not exist"
fi

# Safe access:
echo "${arr[5]:-default}"
```

### Problem 10: Script works in terminal but not cron

```bash
# Cause: Different environment in cron

# Solution 1: Use full paths
/bin/bash /full/path/to/script.sh

# Solution 2: Set PATH in script
#!/bin/bash
PATH=/usr/local/bin:/usr/bin:/bin

# Solution 3: Source profile
#!/bin/bash
source ~/.bashrc

# Debug cron:
* * * * * /bin/bash /path/script.sh >> /tmp/cron.log 2>&1
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Code Focus**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   #!/bin/bash                      │
│   echo "Hello Termux!"             │
│                                    │
│   📝 BASH SCRIPTING                │
│   BASICS                           │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Feature List**
```
┌────────────────────────────────────┐
│  🐚 BASH SCRIPTING                 │
│  ──────────────────────────────    │
│  ✓ Variables                       │
│  ✓ Loops                           │
│  ✓ Functions                       │
│  ✓ 25+ Examples                    │
│                                    │
│  FROM ZERO TO HERO!                │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Terminal Style**
```
┌────────────────────────────────────┐
│  ┌──────────────────────────────┐  │
│  │ $ ./script.sh                │  │
│  │ Hello Termux!                │  │
│  │ ✓ Success                    │  │
│  └──────────────────────────────┘  │
│                                    │
│  BASH SCRIPTING BASICS             │
│  Chapter 13 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🐚 Termux Full Course - Chapter 13: Bash Scripting Basics | Shell Scripting Tutorial

🔥 In this video you'll learn:
• Bash scripting kya hai aur kyun important hai
• Shell scripts kaise banate hain
• Variables, arrays, functions
• Loops aur conditional statements
• 25+ practical script examples
• Debugging techniques

⏱️ Timestamps:
0:00 - Introduction
1:00 - What is Bash Scripting
4:00 - Creating First Script
7:00 - Variables in Bash
10:00 - User Input
12:30 - Arithmetic Operations
15:00 - String Operations
17:30 - Conditional Statements
21:00 - Loops
25:00 - Arrays
27:30 - Functions
30:00 - Debugging Scripts
32:00 - Practical Examples
35:00 - Summary

📝 Key Commands:
chmod +x script.sh     # Make executable
./script.sh            # Run script
bash -x script.sh      # Debug mode

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #BashScripting #ShellScripting #TermuxHindi #T3rmuxk1ng #Linux #Automation #Programming

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
bash scripting, shell scripting, bash script tutorial, 
bash scripting hindi, termux bash scripting, learn bash, 
bash for beginners, bash variables, bash loops, bash functions,
bash arrays, bash if else, shell script examples, 
linux scripting, automation scripts, termux programming,
t3rmuxk1ng, termux course, termux tutorial hindi,
bash scripting basics, bash commands, bash tutorial,
shell programming, unix scripting, termux shell scripting
```

### Hashtags

```
#BashScripting #ShellScripting #Termux #TermuxHindi #BashTutorial 
#LinuxScripting #ShellProgramming #Automation #TermuxCourse 
#T3rmuxk1ng #LearnBash #BashForBeginners #Scripting #Programming
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Bash Manual | `man bash` in terminal |
| GNU Bash Manual | https://www.gnu.org/software/bash/manual/ |
| Bash Hackers Wiki | https://wiki.bash-hackers.org/ |
| Advanced Bash Guide | https://tldp.org/LDP/abs/html/ |

### Learning Resources

| Resource | Description |
|----------|-------------|
| ShellCheck | https://www.shellcheck.net/ - Script linter |
| ExplainShell | https://explainshell.com/ - Command explainer |
| Bash Guide | https://mywiki.wooledge.org/BashGuide |

### Quick Reference

```bash
# Help within bash
help               # Built-in help
help read          # Help for read command
man bash           # Full bash manual

# Script analysis
shellcheck script.sh

# Online resources
https://devhints.io/bash
https://github.com/dylanaraps/pure-bash-bible
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 14, verify:

- [ ] Understand what Bash scripting is and why it's useful
- [ ] Can create and execute shell scripts
- [ ] Know how to use shebang (#!/bin/bash)
- [ ] Can declare and use variables
- [ ] Can get user input with read command
- [ ] Understand arithmetic operations
- [ ] Can manipulate strings
- [ ] Understand if/elif/else conditionals
- [ ] Know file and string test operators
- [ ] Can use for, while, and until loops
- [ ] Understand arrays (indexed and associative)
- [ ] Can create and use functions
- [ ] Know how to debug scripts with bash -x
- [ ] Completed all 5 practice exercises

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 14: Advanced Bash Scripting**

- Error handling with trap
- Signal handling (SIGINT, SIGTERM)
- Process management
- Regular expressions in Bash
- Here documents and here strings
- Process substitution
- Advanced text processing
- Building CLI tools
- Self-modifying scripts
- Security best practices

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
