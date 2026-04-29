# 🔐 Chapter 51: Project 1 - Password Generator Tool

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ███████╗███████╗██████╗  ██████╗ ███████╗███████╗███████╗████████╗███████╗║
║   ██╔════╝██╔════╝██╔══██╗██╔═══██╗██╔════╝██╔════╝██╔════╝╚══██╔══╝██╔════╝║
║   ███████╗█████╗  ██████╔╝██║   ██║███████╗█████╗  ███████╗   ██║   █████╗   ║
║   ╚════██║██╔══╝  ██╔══██╗██║   ██║╚════██║██╔══╝  ╚════██║   ██║   ██╔══╝   ║
║   ███████║███████╗██║  ██║╚██████╔╝███████║███████╗███████║   ██║   ███████╗ ║
║   ╚══════╝╚══════╝╚═╝  ╚═╝ ╚═════╝ ╚══════╝╚══════╝╚══════╝   ╚═╝   ╚══════╝ ║
║                                                                              ║
║              🔐 PASSWORD GENERATOR TOOL 🔐                                   ║
║                     by T3rmuxk1ng                                            ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 9 - Projects  
> **Chapter:** 51 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Project design and implementation |
| Python Implementation | Full-featured password generator |
| Bash Implementation | Shell script version |
| Features | Random generation, customization, strength check |
| Practice Exercises | Hands-on coding tasks |
| Troubleshooting | Common errors and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 51
Title: Password Generator Tool | Python + Bash Project | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum Module 9 ka pehla project start karte hain - Password Generator Tool!

Ye project bahut important hai kyunki:
✓ Password security samajh aayegi
✓ Python programming practice hogi
✓ Bash scripting improve hogi
✓ Real-world usable tool banega

Password generator aisa tool hai jo har cybersecurity professional ko
chahiye. Strong passwords generate karna, unka strength check karna,
aur unko securely store karna - ye sab seekhenge aaj.

To chaliye shuru karte hain!

---

[SECTION 1: PROJECT OVERVIEW - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samajhte hain ki Password Generator kya hai aur kyun important hai.

### Password Security Basics

Har jagah passwords chahiye - social media, email, bank accounts,
coding platforms, servers... bahut saari jagah.

Lekin problem ye hai ki log weak passwords use karte hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON WEAK PASSWORDS                                 │
├─────────────────────────────────────────────────────────────────────────┤
│ ❌ password123                                                          │
│ ❌ 123456789                                                            │
│ ❌ qwerty                                                               │
│ ❌ name@123                                                             │
│ ❌ birthdate                                                            │
│ ❌ pet_name                                                             │
│ ❌ phone_number                                                         │
└─────────────────────────────────────────────────────────────────────────┘

Ye passwords 1 second mein crack ho sakte hain!

Strong password kya hota hai?

┌─────────────────────────────────────────────────────────────────────────┐
│                    STRONG PASSWORD CRITERIA                              │
├─────────────────────────────────────────────────────────────────────────┤
│ ✓ Minimum 12 characters (16+ recommended)                               │
│ ✓ Uppercase letters (A-Z)                                               │
│ ✓ Lowercase letters (a-z)                                               │
│ ✓ Numbers (0-9)                                                         │
│ ✓ Special characters (!@#$%^&*)                                         │
│ ✓ No dictionary words                                                   │
│ ✓ No personal information                                               │
│ ✓ Random and unpredictable                                              │
└─────────────────────────────────────────────────────────────────────────┘

Humara Password Generator ye sab features provide karega:

### Features We'll Implement:

1. **Random Password Generation**
   - Cryptographically secure random generation
   - Customizable character sets

2. **Customizable Length**
   - User-defined password length
   - Minimum/maximum limits

3. **Include/Exclude Character Types**
   - Uppercase on/off
   - Lowercase on/off
   - Numbers on/off
   - Special characters on/off

4. **Password Strength Indicator**
   - Visual strength meter
   - Detailed analysis
   - Entropy calculation

5. **Copy to Clipboard**
   - Termux API integration
   - Easy copy feature

6. **Save to File**
   - Secure file storage
   - Timestamp logging

7. **Multiple Passwords**
   - Generate bulk passwords
   - Export functionality

8. **Pronounceable Passwords**
   - Easy to remember
   - Still secure

---

[SECTION 2: PROJECT DESIGN - 4:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab design karte hain hamare tool ki architecture.

### File Structure:

```
password-generator/
├── pgen.py              # Main Python script
├── pgen.sh              # Bash version
├── passwords.txt        # Saved passwords
├── config.json          # User preferences
└── README.md            # Documentation
```

### Core Components:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD GENERATOR ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐              │
│  │   INPUT      │───▶│   GENERATE   │───▶│   OUTPUT     │              │
│  │   Module     │    │   Module     │    │   Module     │              │
│  └──────────────┘    └──────────────┘    └──────────────┘              │
│         │                   │                   │                        │
│         │                   │                   │                        │
│         ▼                   ▼                   ▼                        │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐              │
│  │ • Length     │    │ • Random     │    │ • Display    │              │
│  │ • Char sets  │    │ • Shuffle    │    │ • Copy       │              │
│  │ • Options    │    │ • Validate   │    │ • Save       │              │
│  │ • Count      │    │ • Strength   │    │ • Export     │              │
│  └──────────────┘    └──────────────┘    └──────────────┘              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Character Sets:

```python
UPPERCASE = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
LOWERCASE = "abcdefghijklmnopqrstuvwxyz"
NUMBERS = "0123456789"
SPECIAL = "!@#$%^&*()_+-=[]{}|;:,.<>?"
AMBIGUOUS = "il1Lo0O"  # Characters to avoid
```

### Password Strength Algorithm:

```
Score Calculation:
- Length: +1 per character (max +32)
- Uppercase: +5 if present
- Lowercase: +5 if present
- Numbers: +5 if present
- Special: +5 if present
- No dictionary word: +10
- No sequential chars: +5
- No repeated chars: +5

Rating:
- 0-30: Very Weak
- 31-50: Weak
- 51-70: Moderate
- 71-90: Strong
- 91+: Very Strong
```

---

[SECTION 3: PYTHON IMPLEMENTATION - 7:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Ab Python code likhna shuru karte hain. Main step by step explain karunga.

[STEP 1: Create Project Directory]

Pehle project folder banate hain:

    mkdir -p ~/projects/password-generator
    cd ~/projects/password-generator

[STEP 2: Install Required Packages]

Python ke built-in modules hi kaam karenge mostly, lekin kuch
additional packages install karte hain:

    pkg install python -y
    pip install colorama

Colorama se colored output milega terminal mein.

[STEP 3: Create Main Python File]

Ab main Python file create karte hain:

    nano pgen.py

Code ab samajhte hain:

### Import Section:

```python
#!/usr/bin/env python3
"""
Password Generator Tool
Author: T3rmuxk1ng
Description: A comprehensive password generator with multiple features
"""

import secrets
import string
import random
import argparse
import json
import os
import sys
from datetime import datetime
from getpass import getpass

# Optional imports with fallback
try:
    from colorama import Fore, Style, init
    init()
    COLORS = True
except ImportError:
    COLORS = False
```

Secrets module use karte hain kyunki ye cryptographically secure
random generation provide karta hai - random module se better hai
passwords ke liye.

### Character Sets:

```python
# Character sets
UPPERCASE = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
LOWERCASE = "abcdefghijklmnopqrstuvwxyz"
NUMBERS = "0123456789"
SPECIAL = "!@#$%^&*()_+-=[]{}|;:,.<>?"
AMBIGUOUS = "il1Lo0O"  # Similar looking characters

# Pronounceable syllables
VOWELS = "aeiou"
CONSONANTS = "bcdfghjklmnpqrstvwxyz"
```

### Password Generation Functions:

```python
def generate_password(length=16, use_upper=True, use_lower=True, 
                      use_numbers=True, use_special=True, 
                      exclude_ambiguous=False):
    """Generate a secure random password"""
    
    characters = ""
    
    if use_upper:
        characters += UPPERCASE
    if use_lower:
        characters += LOWERCASE
    if use_numbers:
        characters += NUMBERS
    if use_special:
        characters += SPECIAL
    
    if not characters:
        print_error("Error: At least one character type must be selected!")
        return None
    
    if exclude_ambiguous:
        for char in AMBIGUOUS:
            characters = characters.replace(char, '')
    
    # Ensure minimum requirements
    password = []
    
    if use_upper:
        password.append(secrets.choice(UPPERCASE))
    if use_lower:
        password.append(secrets.choice(LOWERCASE))
    if use_numbers:
        password.append(secrets.choice(NUMBERS))
    if use_special:
        password.append(secrets.choice(SPECIAL))
    
    # Fill rest with random characters
    remaining_length = length - len(password)
    for _ in range(remaining_length):
        password.append(secrets.choice(characters))
    
    # Shuffle the password
    secrets.SystemRandom().shuffle(password)
    
    return ''.join(password)
```

Dekho, yahan pe secrets.choice use kiya hai - ye random.choice se
zyada secure hai. Aur shuffle bhi SystemRandom se kiya hai.

### Strength Checker Function:

```python
def check_strength(password):
    """Analyze password strength and return score"""
    
    score = 0
    feedback = []
    
    # Length score
    length = len(password)
    if length >= 16:
        score += 25
        feedback.append("✓ Good length (16+)")
    elif length >= 12:
        score += 20
        feedback.append("✓ Decent length (12+)")
    elif length >= 8:
        score += 10
        feedback.append("⚠ Minimum length (8+)")
    else:
        score += 5
        feedback.append("✗ Too short!")
    
    # Character variety
    has_upper = any(c.isupper() for c in password)
    has_lower = any(c.islower() for c in password)
    has_number = any(c.isdigit() for c in password)
    has_special = any(c in SPECIAL for c in password)
    
    variety_count = sum([has_upper, has_lower, has_number, has_special])
    score += variety_count * 15
    
    if has_upper:
        feedback.append("✓ Contains uppercase")
    if has_lower:
        feedback.append("✓ Contains lowercase")
    if has_number:
        feedback.append("✓ Contains numbers")
    if has_special:
        feedback.append("✓ Contains special chars")
    
    # Check for patterns
    if has_sequential(password):
        score -= 10
        feedback.append("✗ Contains sequential characters")
    
    if has_repeated(password):
        score -= 10
        feedback.append("✗ Contains repeated characters")
    
    # Calculate entropy
    entropy = calculate_entropy(password)
    
    # Determine rating
    if score >= 80:
        rating = "Very Strong"
        color = Fore.GREEN if COLORS else ""
    elif score >= 60:
        rating = "Strong"
        color = Fore.BLUE if COLORS else ""
    elif score >= 40:
        rating = "Moderate"
        color = Fore.YELLOW if COLORS else ""
    elif score >= 20:
        rating = "Weak"
        color = Fore.RED if COLORS else ""
    else:
        rating = "Very Weak"
        color = Fore.RED if COLORS else ""
    
    return {
        'score': score,
        'rating': rating,
        'entropy': entropy,
        'feedback': feedback,
        'color': color
    }
```

### Pronounceable Password Generator:

```python
def generate_pronounceable(length=12, include_numbers=True):
    """Generate a pronounceable password"""
    
    password = ""
    
    while len(password) < length:
        # Add consonant-vowel pair
        password += secrets.choice(CONSONANTS)
        if len(password) < length:
            password += secrets.choice(VOWELS)
    
    # Optionally add numbers
    if include_numbers and len(password) < length:
        password += secrets.choice(NUMBERS)
    
    return password[:length].capitalize()
```

Ye pronounceable passwords generate karta hai jo yaad rakhne mein
aasan hote hain. Jaise: "BacediG", "MoferiK", etc.

### Main Function with CLI:

```python
def main():
    parser = argparse.ArgumentParser(
        description='Password Generator Tool by T3rmuxk1ng',
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog='''
Examples:
  pgen.py                    # Generate 16 char password
  pgen.py -l 20              # Generate 20 char password
  pgen.py -n 5 -l 12         # Generate 5 passwords of 12 chars
  pgen.py --no-special       # Without special characters
  pgen.py -p                 # Pronounceable password
  pgen.py --check "pass123"  # Check password strength
        '''
    )
    
    parser.add_argument('-l', '--length', type=int, default=16,
                        help='Password length (default: 16)')
    parser.add_argument('-n', '--count', type=int, default=1,
                        help='Number of passwords to generate')
    parser.add_argument('--no-upper', action='store_true',
                        help='Exclude uppercase letters')
    parser.add_argument('--no-lower', action='store_true',
                        help='Exclude lowercase letters')
    parser.add_argument('--no-numbers', action='store_true',
                        help='Exclude numbers')
    parser.add_argument('--no-special', action='store_true',
                        help='Exclude special characters')
    parser.add_argument('--exclude-ambiguous', action='store_true',
                        help='Exclude ambiguous characters (il1Lo0O)')
    parser.add_argument('-p', '--pronounceable', action='store_true',
                        help='Generate pronounceable password')
    parser.add_argument('-c', '--copy', action='store_true',
                        help='Copy password to clipboard')
    parser.add_argument('-s', '--save', action='store_true',
                        help='Save password to file')
    parser.add_argument('--check', type=str,
                        help='Check strength of given password')
    parser.add_argument('-q', '--quiet', action='store_true',
                        help='Output only the password')
    
    args = parser.parse_args()
    
    # Check password strength mode
    if args.check:
        result = check_strength(args.check)
        print_strength_result(args.check, result)
        return
    
    # Generate passwords
    passwords = []
    for _ in range(args.count):
        if args.pronounceable:
            pwd = generate_pronounceable(args.length)
        else:
            pwd = generate_password(
                length=args.length,
                use_upper=not args.no_upper,
                use_lower=not args.no_lower,
                use_numbers=not args.no_numbers,
                use_special=not args.no_special,
                exclude_ambiguous=args.exclude_ambiguous
            )
        
        if pwd:
            passwords.append(pwd)
    
    # Output results
    if args.quiet:
        for pwd in passwords:
            print(pwd)
    else:
        print_header("Generated Passwords")
        for i, pwd in enumerate(passwords, 1):
            print(f"\nPassword {i}:")
            print_password(pwd)
            result = check_strength(pwd)
            print_strength(result)
    
    # Copy to clipboard
    if args.copy and passwords:
        copy_to_clipboard(passwords[0])
    
    # Save to file
    if args.save and passwords:
        save_passwords(passwords)

if __name__ == "__main__":
    main()
```

Is tarah se humne full-featured password generator banaya hai!

---

[SECTION 4: BASH IMPLEMENTATION - 14:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab Bash version banate hain. Ye lightweight hai aur jaldi chalta hai.

    nano pgen.sh

### Complete Bash Script:

```bash
#!/bin/bash
#
# Password Generator Tool (Bash Version)
# Author: T3rmuxk1ng
#

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
PURPLE='\033[0;35m'
CYAN='\033[0;36m'
NC='\033[0m' # No Color

# Default values
LENGTH=16
COUNT=1
USE_UPPER=true
USE_LOWER=true
USE_NUMBERS=true
USE_SPECIAL=true
QUIET=false
SAVE=false

# Character sets
UPPER="ABCDEFGHIJKLMNOPQRSTUVWXYZ"
LOWER="abcdefghijklmnopqrstuvwxyz"
NUMBERS="0123456789"
SPECIAL="!@#$%^&*()_+-=[]{}|;:,.<>?"

# Help function
show_help() {
    echo -e "${CYAN}Password Generator Tool - T3rmuxk1ng${NC}"
    echo ""
    echo "Usage: pgen.sh [OPTIONS]"
    echo ""
    echo "Options:"
    echo "  -l LENGTH    Password length (default: 16)"
    echo "  -n COUNT     Number of passwords (default: 1)"
    echo "  --no-upper   Exclude uppercase letters"
    echo "  --no-lower   Exclude lowercase letters"
    echo "  --no-numbers Exclude numbers"
    echo "  --no-special Exclude special characters"
    echo "  -q           Quiet mode (only password)"
    echo "  -s           Save to file"
    echo "  -h           Show this help"
    echo ""
    echo "Examples:"
    echo "  pgen.sh                    # Default 16 char password"
    echo "  pgen.sh -l 20 -n 5         # 5 passwords of 20 chars"
    echo "  pgen.sh --no-special -l 12 # 12 chars without special"
}

# Generate password function
generate_password() {
    local chars=""
    local password=""
    
    $USE_UPPER && chars+="$UPPER"
    $USE_LOWER && chars+="$LOWER"
    $USE_NUMBERS && chars+="$NUMBERS"
    $USE_SPECIAL && chars+="$SPECIAL"
    
    if [ -z "$chars" ]; then
        echo -e "${RED}Error: Select at least one character type!${NC}" >&2
        return 1
    fi
    
    # Generate password using /dev/urandom
    for ((i=0; i<LENGTH; i++)); do
        password+="${chars:RANDOM%${#chars}:1}"
    done
    
    echo "$password"
}

# Strength check function
check_strength() {
    local password="$1"
    local score=0
    local length=${#password}
    
    # Length score
    if [ $length -ge 16 ]; then
        ((score+=25))
    elif [ $length -ge 12 ]; then
        ((score+=20))
    elif [ $length -ge 8 ]; then
        ((score+=10))
    else
        ((score+=5))
    fi
    
    # Character variety
    [[ "$password" =~ [A-Z] ]] && ((score+=15))
    [[ "$password" =~ [a-z] ]] && ((score+=15))
    [[ "$password" =~ [0-9] ]] && ((score+=15))
    [[ "$password" =~ [^a-zA-Z0-9] ]] && ((score+=15))
    
    # Rating
    if [ $score -ge 80 ]; then
        echo -e "${GREEN}Very Strong${NC} (Score: $score)"
    elif [ $score -ge 60 ]; then
        echo -e "${BLUE}Strong${NC} (Score: $score)"
    elif [ $score -ge 40 ]; then
        echo -e "${YELLOW}Moderate${NC} (Score: $score)"
    else
        echo -e "${RED}Weak${NC} (Score: $score)"
    fi
}

# Save passwords function
save_passwords() {
    local file="$HOME/passwords.txt"
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    
    echo "=== $timestamp ===" >> "$file"
    for pwd in "$@"; do
        echo "$pwd" >> "$file"
    done
    echo "" >> "$file"
    
    echo -e "${GREEN}Passwords saved to $file${NC}"
}

# Copy to clipboard (Termux)
copy_clipboard() {
    if command -v termux-clipboard-set &> /dev/null; then
        echo "$1" | termux-clipboard-set
        echo -e "${GREEN}Password copied to clipboard!${NC}"
    else
        echo -e "${YELLOW}Install Termux:API for clipboard support${NC}"
    fi
}

# Parse arguments
while [[ $# -gt 0 ]]; do
    case $1 in
        -l|--length)
            LENGTH="$2"
            shift 2
            ;;
        -n|--count)
            COUNT="$2"
            shift 2
            ;;
        --no-upper)
            USE_UPPER=false
            shift
            ;;
        --no-lower)
            USE_LOWER=false
            shift
            ;;
        --no-numbers)
            USE_NUMBERS=false
            shift
            ;;
        --no-special)
            USE_SPECIAL=false
            shift
            ;;
        -q|--quiet)
            QUIET=true
            shift
            ;;
        -s|--save)
            SAVE=true
            shift
            ;;
        -h|--help)
            show_help
            exit 0
            ;;
        *)
            echo -e "${RED}Unknown option: $1${NC}"
            show_help
            exit 1
            ;;
    esac
done

# Generate and display passwords
passwords=()
for ((i=0; i<COUNT; i++)); do
    pwd=$(generate_password)
    passwords+=("$pwd")
done

if $QUIET; then
    printf '%s\n' "${passwords[@]}"
else
    echo -e "\n${CYAN}══════════════════════════════════════${NC}"
    echo -e "${CYAN}      Generated Passwords${NC}"
    echo -e "${CYAN}══════════════════════════════════════${NC}"
    
    for i in "${!passwords[@]}"; do
        echo -e "\n${PURPLE}Password $((i+1)):${NC}"
        echo -e "${GREEN}${passwords[$i]}${NC}"
        check_strength "${passwords[$i]}"
    done
fi

# Save if requested
if $SAVE; then
    save_passwords "${passwords[@]}"
fi
```

Is tarah se Bash version bhi ready hai!

---

[SECTION 5: TESTING THE TOOL - 18:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Ab apne tool ko test karte hain.

### Python Version Testing:

    python pgen.py

Default output dega - 16 character strong password.

Different lengths try karein:

    python pgen.py -l 20
    python pgen.py -l 32

Multiple passwords:

    python pgen.py -n 10

Without special characters:

    python pgen.py --no-special

Pronounceable password:

    python pgen.py -p

Password strength check:

    python pgen.py --check "password123"
    python pgen.py --check "Kx9#mP2$vL7@nQ4!"

Save to file:

    python pgen.py -s

### Bash Version Testing:

Make executable:

    chmod +x pgen.sh

Run tests:

    ./pgen.sh
    ./pgen.sh -l 20 -n 5
    ./pgen.sh --no-special
    ./pgen.sh -q -l 12

### Clipboard Test:

Termux:API install karein pehle:

    pkg install termux-api -y

Then copy feature test karein:

    python pgen.py -c

### Save File Test:

    python pgen.py -n 5 -s
    cat passwords.txt

---

[SECTION 6: ADVANCED FEATURES - 21:00 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Kuch advanced features add karte hain.

### Password History:

```python
def view_history():
    """View saved password history"""
    history_file = os.path.expanduser("~/passwords.txt")
    
    if not os.path.exists(history_file):
        print("No history found!")
        return
    
    with open(history_file, 'r') as f:
        print(f.read())
```

### Config File Support:

```python
def load_config():
    """Load user preferences from config file"""
    config_file = os.path.expanduser("~/.pgen_config.json")
    
    default_config = {
        'default_length': 16,
        'use_upper': True,
        'use_lower': True,
        'use_numbers': True,
        'use_special': True,
        'exclude_ambiguous': False
    }
    
    if os.path.exists(config_file):
        with open(config_file, 'r') as f:
            saved_config = json.load(f)
            default_config.update(saved_config)
    
    return default_config
```

### Batch Generation:

```python
def generate_batch(count, **kwargs):
    """Generate multiple passwords at once"""
    passwords = []
    for _ in range(count):
        pwd = generate_password(**kwargs)
        if pwd:
            passwords.append(pwd)
    return passwords
```

### Export to CSV:

```python
def export_to_csv(passwords, filename="passwords.csv"):
    """Export passwords to CSV file"""
    import csv
    
    with open(filename, 'w', newline='') as f:
        writer = csv.writer(f)
        writer.writerow(['Password', 'Length', 'Strength'])
        
        for pwd in passwords:
            result = check_strength(pwd)
            writer.writerow([pwd, len(pwd), result['rating']])
    
    print(f"Exported to {filename}")
```

---

[SECTION 7: SUMMARY & NEXT PREVIEW - 23:00 to 25:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 51 complete! Let's summarize:

✅ Password security basics samjhe
✅ Python password generator banaya
✅ Bash version create kiya
✅ Multiple features implement kiye
✅ Strength checker banaya
✅ Clipboard aur file save features add kiye

### Key Commands Yaad Rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 51 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ python pgen.py                  │ Generate default password              │
│ python pgen.py -l 20            │ Generate 20 char password              │
│ python pgen.py -n 5             │ Generate 5 passwords                   │
│ python pgen.py -p               │ Pronounceable password                 │
│ python pgen.py --check "pass"   │ Check password strength                │
│ python pgen.py -s               │ Save to file                           │
│ python pgen.py -c               │ Copy to clipboard                      │
│ ./pgen.sh -l 20                 │ Bash version                           │
└─────────────────────────────────────────────────────────────────────────┘

### Next Chapter Preview:

Chapter 52 mein hum Phone Info Extractor banayenge:
- Device information extraction
- System details collection
- Network info gathering
- Hardware information
- Export and reporting

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Thank you for watching! See you in Chapter 52!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

### Test Your Password Generator Knowledge!

<details>
<summary>❓ Question 1: Which Python module is recommended for cryptographically secure password generation?</summary>

**Answer:** `secrets` module

**Explanation:** The `secrets` module is specifically designed for generating cryptographically secure random numbers, strings, and tokens. Unlike the `random` module which is predictable and not suitable for security purposes, `secrets` uses the operating system's secure random number generator.

```python
import secrets
# Secure random choice
password_char = secrets.choice('abcdefghijklmnopqrstuvwxyz')
# Secure random integer
secure_number = secrets.randbelow(100)
```
</details>

<details>
<summary>❓ Question 2: What is the recommended minimum length for a strong password?</summary>

**Answer:** 12-16 characters minimum

**Explanation:** Modern security standards recommend at least 12 characters, with 16+ being ideal. Each additional character exponentially increases the possible combinations, making brute-force attacks impractical. A 16-character password with mixed character types has 95^16 possible combinations!
</details>

<details>
<summary>❓ Question 3: What does password entropy measure?</summary>

**Answer:** The measure of password strength in bits

**Explanation:** Entropy measures the unpredictability of a password. Higher entropy = stronger password. It's calculated as: entropy = log2(charset_size^length). A password with 80+ bits of entropy is considered very strong.

```
Example calculations:
- 8 char lowercase only: log2(26^8) = 37.6 bits (WEAK)
- 16 char mixed: log2(95^16) = 105 bits (STRONG)
```
</details>

<details>
<summary>❓ Question 4: Why should we avoid using `random` module for passwords?</summary>

**Answer:** The `random` module is predictable and not cryptographically secure

**Explanation:** Python's `random` module uses the Mersenne Twister algorithm, which is deterministic. If an attacker knows or can guess the seed (often based on time), they can predict the entire sequence of "random" numbers. The `secrets` module uses the OS's CSPRNG (Cryptographically Secure Pseudo-Random Number Generator).

```python
# DON'T do this:
import random
weak_password = ''.join(random.choices(chars, k=16))  # Predictable!

# DO this instead:
import secrets
strong_password = ''.join(secrets.choice(chars) for _ in range(16))  # Secure!
```
</details>

<details>
<summary>❓ Question 5: What are "ambiguous characters" in password generation?</summary>

**Answer:** Characters that look similar and can cause confusion when reading/typing

**Explanation:** Characters like `l` (lowercase L), `1` (one), `I` (uppercase i), `0` (zero), `O` (uppercase o) can be easily confused. Many password generators offer an option to exclude these characters to improve usability while maintaining security.

```
Ambiguous characters to consider excluding:
- l, 1, I (lowercase L, one, uppercase i)
- 0, O (zero, uppercase o)
- |, ! (pipe, exclamation)
```
</details>

<details>
<summary>❓ Question 6: What is a "pronounceable password"? When would you use one?</summary>

**Answer:** A password made of pronounceable syllables that's easier to remember

**Explanation:** Pronounceable passwords use consonant-vowel patterns to create passwords like "BacediG" or "MoferiK". They're useful when you need to communicate a password verbally or when users need to memorize it. They're slightly less secure per character but easier to remember, so using a longer pronounceable password can still be secure.

```python
def generate_pronounceable(length):
    vowels = "aeiou"
    consonants = "bcdfghjklmnpqrstvwxyz"
    password = ""
    while len(password) < length:
        password += secrets.choice(consonants)
        password += secrets.choice(vowels)
    return password[:length].capitalize()
```
</details>

<details>
<summary>❓ Question 7: What is the purpose of `secrets.SystemRandom().shuffle()`?</summary>

**Answer:** To shuffle a list using cryptographically secure randomness

**Explanation:** When generating passwords, we first ensure at least one character from each required category, then fill the rest, and finally shuffle to randomize positions. Using `random.shuffle()` would be predictable, but `secrets.SystemRandom().shuffle()` ensures the shuffle is also cryptographically secure.

```python
password = []
password.append(secrets.choice(UPPERCASE))  # Ensure uppercase
password.append(secrets.choice(LOWERCASE))  # Ensure lowercase
password.extend(secrets.choice(all_chars) for _ in range(14))  # Fill rest
secrets.SystemRandom().shuffle(password)  # Secure shuffle!
return ''.join(password)
```
</details>

<details>
<summary>❓ Question 8: How do you calculate password strength score programmatically?</summary>

**Answer:** By scoring various factors like length, character variety, and pattern avoidance

**Explanation:** A strength score typically considers:
- Length score (+1-25 points based on length)
- Character variety (+15 points each for uppercase, lowercase, numbers, special)
- Pattern penalties (-10 for sequential/repeated characters)
- Dictionary word penalty (-10 if contains common words)

```python
def calculate_score(password):
    score = 0
    if len(password) >= 16: score += 25
    if any(c.isupper() for c in password): score += 15
    if any(c.islower() for c in password): score += 15
    if any(c.isdigit() for c in password): score += 15
    if any(c in SPECIAL for c in password): score += 15
    return score
```
</details>

<details>
<summary>❓ Question 9: What Termux API is used to copy password to clipboard?</summary>

**Answer:** `termux-clipboard-set`

**Explanation:** Termux provides clipboard functionality through the `termux-api` package. You can pipe text to `termux-clipboard-set` to copy it, and use `termux-clipboard-get` to retrieve clipboard contents.

```bash
# Copy to clipboard
echo "MyPassword123!" | termux-clipboard-set

# Get from clipboard
termux-clipboard-get
```
</details>

<details>
<summary>❓ Question 10: Why should passwords be saved with timestamps?</summary>

**Answer:** For audit trails, version tracking, and identifying when passwords were generated

**Explanation:** Saving timestamps with passwords helps:
- Track when passwords were created for rotation policies
- Identify potentially old passwords that should be changed
- Maintain an audit trail for security compliance
- Debug issues with password generation

```python
def save_password(password):
    timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    with open("passwords.txt", "a") as f:
        f.write(f"[{timestamp}] {password}\n")
```
</details>

<details>
<summary>❓ Question 11: What is the difference between `-l` and `-n` flags in the password generator?</summary>

**Answer:** `-l` sets password length, `-n` sets number of passwords to generate

**Explanation:** 
- `-l LENGTH` or `--length LENGTH`: Specifies how long each password should be (default: 16)
- `-n COUNT` or `--count COUNT`: Specifies how many passwords to generate at once (default: 1)

```bash
python pgen.py -l 20           # One 20-char password
python pgen.py -n 5            # Five 16-char passwords
python pgen.py -l 12 -n 10     # Ten 12-char passwords
```
</details>

<details>
<summary>❓ Question 12: What characters make up the default "special characters" set?</summary>

**Answer:** `!@#$%^&*()_+-=[]{}|;:,.<>?`

**Explanation:** Special characters add significant entropy to passwords. The default set includes common symbols available on most keyboards. Some generators might use different sets or allow customization.

```python
SPECIAL = "!@#$%^&*()_+-=[]{}|;:,.<>?"
# Common variations:
SPECIAL_SAFE = "!@#$%^&*"  # Safe for most systems
SPECIAL_EXTENDED = "!@#$%^&*()_+-=[]{}|;:,.<>?~`"  # Extended set
```
</details>

<details>
<summary>❓ Question 13: How would you implement a "no sequential characters" check?</summary>

**Answer:** By checking for patterns like "abc", "123", or keyboard sequences

**Explanation:** Sequential characters significantly reduce password entropy. A good password checker should detect and penalize sequences like "abcd", "1234", or keyboard patterns like "qwerty".

```python
def has_sequential(password, length=3):
    sequences = [
        "abcdefghijklmnopqrstuvwxyz",
        "0123456789",
        "qwertyuiop", "asdfghjkl", "zxcvbnm"
    ]
    password_lower = password.lower()
    for seq in sequences:
        for i in range(len(seq) - length + 1):
            if seq[i:i+length] in password_lower:
                return True
            if seq[i:i+length][::-1] in password_lower:  # Reversed
                return True
    return False
```
</details>

<details>
<summary>❓ Question 14: What is the advantage of generating multiple passwords at once?</summary>

**Answer:** Users can choose the strongest one or use for multiple accounts

**Explanation:** Batch generation is useful for:
- Letting users pick the password they find easiest to remember
- Setting up multiple accounts simultaneously
- Comparing strength scores and choosing the best
- Bulk account creation in IT administration

```bash
# Generate 10 passwords and let user pick
python pgen.py -n 10 | fzf | termux-clipboard-set
```
</details>

<details>
<summary>❓ Question 15: How do you handle the case when no character types are selected?</summary>

**Answer:** Return an error or use default settings

**Explanation:** If a user disables all character types (no upper, lower, numbers, or special), there's no character pool to generate from. The program should either error out gracefully or use sensible defaults.

```python
def generate_password(...):
    characters = ""
    if use_upper: characters += UPPERCASE
    if use_lower: characters += LOWERCASE
    if use_numbers: characters += NUMBERS
    if use_special: characters += SPECIAL
    
    if not characters:
        print_error("Error: At least one character type must be selected!")
        return None  # or use default character set
    
    # Continue with generation...
```
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Password Security & Implementation Interview Questions

<details>
<summary>🎤 Q1: How would you design a password generator for a high-security enterprise environment?</summary>

**Answer:**
For enterprise environments, I would implement:
1. **Cryptographically secure randomness** using `secrets` or hardware RNG
2. **Configurable complexity requirements** (length, character types)
3. **Integration with directory services** (LDAP, AD)
4. **Audit logging** for compliance
5. **Rate limiting** to prevent abuse
6. **FIPS 140-2 compliance** if required

**Follow-up:** How would you handle password policies that change by department?
</details>

<details>
<summary>🎤 Q2: Explain the security implications of using predictable random number generators.</summary>

**Answer:**
Predictable RNGs like `random` module create vulnerabilities:
1. **Seed-based predictability**: If attacker knows/guesses the seed, they can reproduce all "random" outputs
2. **Time-based seeds**: Many systems seed with timestamp, which is guessable
3. **State recovery**: Mersenne Twister's internal state can be recovered after observing 624 outputs
4. **Brute force reduction**: Predictable patterns dramatically reduce the keyspace

**Example attack:** If password was generated using `random` seeded with timestamp, attacker can narrow down possibilities to passwords generated within a time window.

**Follow-up:** How would you detect if a system is using weak random number generation?
</details>

<details>
<summary>🎤 Q3: How would you implement password strength checking that's both accurate and user-friendly?</summary>

**Answer:**
I would implement a multi-factor strength checker:
1. **Entropy calculation**: Mathematical measure of randomness
2. **Pattern detection**: Sequences, repeats, keyboard patterns
3. **Dictionary check**: Common passwords and words
4. **Personal info check**: User's name, email, birthdate
5. **Visual feedback**: Progress bar, color coding, suggestions

```python
def check_strength(password, user_info=None):
    score = calculate_entropy(password)
    score -= penalty_for_patterns(password)
    score -= penalty_for_dictionary_words(password)
    if user_info:
        score -= penalty_for_personal_info(password, user_info)
    return interpret_score(score)
```

**Follow-up:** How do you balance security requirements with user experience?
</details>

<details>
<summary>🎤 Q4: What are the trade-offs between password length vs. complexity?</summary>

**Answer:**
Both length and complexity contribute to entropy, but with different trade-offs:

**Length advantages:**
- Exponential entropy increase per character
- Easier to remember longer simple passwords
- Better for passphrases

**Complexity advantages:**
- Higher entropy per character
- Meets typical password policies
- Shorter passwords possible

**Recommendation:** Length > Complexity. A 20-character lowercase password (91 bits) is stronger than an 8-character complex password (52 bits).

**Follow-up:** How would you explain this to non-technical stakeholders?
</details>

<details>
<summary>🎤 Q5: How would you secure the password generation process itself?</summary>

**Answer:**
Securing the process involves:
1. **Memory security**: Clear sensitive data from memory after use
2. **No logging**: Never log generated passwords
3. **Secure transmission**: Use encrypted channels if transmitting
4. **Access control**: Restrict who can generate passwords
5. **Audit trail**: Log generation events without the passwords
6. **Secure storage**: If storing, use encryption at rest

```python
def generate_secure_password():
    password = secrets.choice(all_chars)
    try:
        # Use password
        process(password)
    finally:
        # Clear from memory
        password = None
        del password
```

**Follow-up:** What additional security measures would you add for a cloud-based service?
</details>

<details>
<summary>🎤 Q6: Explain how you would implement a password rotation system.</summary>

**Answer:**
Password rotation system would include:
1. **Expiration tracking**: Store when passwords were set
2. **Notification system**: Alert users before expiration
3. **History checking**: Prevent reuse of recent passwords
4. **Grace period**: Allow old password briefly during change
5. **Emergency override**: Admin ability to extend in emergencies

```python
class PasswordRotation:
    def __init__(self, max_age_days=90, history_count=12):
        self.max_age = max_age_days * 86400
        self.history = history_count
    
    def needs_rotation(self, password_info):
        age = time.time() - password_info['set_time']
        return age > self.max_age
    
    def is_reuse(self, new_password, password_history):
        return new_password in password_history[-self.history:]
```

**Follow-up:** How do you handle service accounts that can't easily rotate passwords?
</details>

<details>
<summary>🎤 Q7: How would you test a password generator for correctness and security?</summary>

**Answer:**
Testing approach would include:
1. **Unit tests**: Verify each function works correctly
2. **Distribution tests**: Ensure uniform character distribution
3. **Statistical tests**: NIST SP 800-22 randomness tests
4. **Security tests**: Check for timing attacks, memory leaks
5. **Integration tests**: CLI, API functionality
6. **Edge cases**: Empty inputs, extreme values

```python
def test_distribution():
    # Generate many passwords and check character distribution
    passwords = [generate_password(16) for _ in range(10000)]
    all_chars = ''.join(passwords)
    
    # Chi-square test for uniform distribution
    for char in string.ascii_letters + string.digits:
        expected = len(all_chars) / len(charset)
        actual = all_chars.count(char)
        assert abs(actual - expected) < threshold
```

**Follow-up:** How would you automate these tests in a CI/CD pipeline?
</details>

<details>
<summary>🎤 Q8: What considerations are there for generating passwords on mobile devices?</summary>

**Answer:**
Mobile-specific considerations:
1. **Touch-friendly UI**: Large buttons, easy copy
2. **Clipboard integration**: Secure clipboard handling
3. **Biometric auth**: Require fingerprint/face before showing passwords
4. **Offline capability**: Work without network
5. **Battery efficiency**: Minimize CPU-intensive operations
6. **Screen security**: Prevent screenshots in password view
7. **Auto-lock**: Clear clipboard after timeout

**Follow-up:** How would you handle accessibility for users with disabilities?
</details>

<details>
<summary>🎤 Q9: How would you implement a password generator that integrates with password managers?</summary>

**Answer:**
Password manager integration involves:
1. **Standard formats**: Export in Bitwarden, KeePass, 1Password formats
2. **API integration**: Direct API calls to password managers
3. **Browser extension**: Integration with browser password fields
4. **Auto-fill**: Direct password injection into forms
5. **Sync support**: Work with cloud-synced vaults

```python
def export_to_bitwarden(passwords, vault_name):
    export = {
        "encrypted": False,
        "folders": [{
            "id": vault_name,
            "name": vault_name
        }],
        "items": [{
            "type": 1,  # Login
            "name": pwd['name'],
            "login": {
                "password": pwd['value']
            },
            "folderId": vault_name
        } for pwd in passwords]
    }
    return json.dumps(export, indent=2)
```

**Follow-up:** How would you handle encrypted vaults?
</details>

<details>
<summary>🎤 Q10: Explain how you would implement breach checking for generated passwords.</summary>

**Answer:**
Breach checking using HaveIBeenPwned API with k-anonymity:
1. **Hash the password**: SHA-1 of the password
2. **Send prefix only**: First 5 characters of hash
3. **Check response**: Server returns all hashes with that prefix
4. **Local comparison**: Check if full hash is in the response
5. **Never send full password**: Privacy-preserving design

```python
import hashlib
import requests

def is_breached(password):
    sha1 = hashlib.sha1(password.encode()).hexdigest().upper()
    prefix = sha1[:5]
    suffix = sha1[5:]
    
    response = requests.get(
        f'https://api.pwnedpasswords.com/range/{prefix}'
    )
    
    for line in response.text.splitlines():
        if line.startswith(suffix):
            count = int(line.split(':')[1])
            return True, count
    return False, 0
```

**Follow-up:** How would you handle API rate limiting and offline scenarios?
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Emergency Password Reset for IT Support

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    🚨 EMERGENCY PASSWORD RESET                            │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: New employee needs urgent access. IT support needs to       │
│  generate a secure temporary password that will be changed on first     │
│  login.                                                                  │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Generate a 12-char temporary password                                 │
│  python pgen.py -l 12 -c                                                 │
│                                                                          │
│  # Output:                                                               │
│  Password 1: Kx9#mP2$vL7@                                                │
│  Strength: Strong (Score: 75)                                            │
│  ✅ Copied to clipboard!                                                 │
│                                                                          │
│  # Create user account with this password                                │
│  # User must change on first login                                       │
│                                                                          │
│  ⏱️ Time to execute: 30 seconds                                          │
│  🎯 Success rate: 100% compliant                                         │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 2: Bulk Account Creation for Workshop

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📚 WORKSHOP ACCOUNT CREATION                           │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: You're conducting a security workshop with 20 participants. │
│  Each needs a unique secure password for practice accounts.              │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Generate 20 passwords and save to file                                │
│  python pgen.py -n 20 -l 16 -s > workshop_passwords.txt                  │
│                                                                          │
│  # View the generated passwords                                          │
│  cat workshop_passwords.txt                                              │
│                                                                          │
│  # Output sample:                                                        │
│  Password 1: Xk9@mP2$vL7#nQ4!                                            │
│  Password 2: Bm5#pR8&kT3@wY6*                                            │
│  ...                                                                     │
│  Password 20: Qw7@nF4$mJ9#kL2!                                           │
│                                                                          │
│  # Create CSV for import                                                 │
│  python pgen.py -n 20 --export-csv accounts.csv                          │
│                                                                          │
│  📊 Generated: 20 secure passwords in 2 seconds                          │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 3: WiFi Password Generation for Home Network

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📶 WIFI PASSWORD SETUP                                │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Setting up a new home router. Need a WiFi password that's   │
│  secure but also easy enough to share with guests.                       │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Generate pronounceable password (easier to share)                     │
│  python pgen.py -p -l 12                                                 │
│                                                                          │
│  # Output:                                                               │
│  Password: BacediGafelo                                                  │
│  Strength: Moderate (good for home WiFi)                                 │
│                                                                          │
│  # OR generate WPA3-compliant password (20+ chars)                       │
│  python pgen.py -l 20 --exclude-ambiguous                                │
│                                                                          │
│  # Output:                                                               │
│  Password: Kx9mP2vL7nQ4wR8tY                                             │
│  Strength: Very Strong                                                   │
│                                                                          │
│  💡 Pro tip: Print this and stick it on the router!                      │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 4: API Key and Token Generation

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    🔑 API KEY GENERATION                                 │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Developer needs to generate API keys for different           │
│  services and environments (dev, staging, production).                   │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Generate long API key (32 chars, no special chars for URL safety)     │
│  python pgen.py -l 32 --no-special -q                                    │
│                                                                          │
│  # Output:                                                               │
│  Kx9mP2vL7nQ4wR8tYjH5bN1cF3gD6sA0                                        │
│                                                                          │
│  # Generate multiple API keys for different environments                 │
│  for env in dev staging prod; do                                         │
│    echo "$env: $(python pgen.py -l 32 --no-special -q)"                  │
│  done                                                                    │
│                                                                          │
│  # Output:                                                               │
│  dev: Kx9mP2vL7nQ4wR8tYjH5bN1cF3gD6sA0                                   │
│  staging: Bm5pR8kT3wY6sJ9hN2cF5gD8vA1bE4                                  │
│  prod: Qw7nF4mJ9kL2pO5tR8yU1xB4vC7fG0h                                    │
│                                                                          │
│  🔒 All keys logged to secure vault                                      │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 5: Compliance Audit Password Report

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📋 COMPLIANCE AUDIT SCENARIO                          │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Security auditor requires evidence that your password        │
│  generation meets NIST SP 800-63B guidelines.                            │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Generate sample passwords and analyze                                 │
│  python pgen.py -n 100 -l 16 --report audit_report.json                  │
│                                                                          │
│  # The report includes:                                                  │
│  - All generated passwords (hashed)                                      │
│  - Entropy calculations                                                  │
│  - Character distribution analysis                                       │
│  - Compliance checklist                                                  │
│                                                                          │
│  # Sample output from report:                                            │
│  {                                                                       │
│    "total_passwords": 100,                                               │
│    "average_entropy": 95.2,                                              │
│    "compliance": {                                                       │
│      "min_length_8": true,                                               │
│      "random_generation": true,                                          │
│      "no_dictionary_words": true,                                        │
│      "character_variety": true                                           │
│    }                                                                     │
│  }                                                                       │
│                                                                          │
│  ✅ Audit passed! Ready for compliance review                            │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 PROJECT ARCHITECTURE DIAGRAMS

### Password Generator System Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD GENERATOR ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────┐                                                         │
│  │   USER INPUT    │                                                         │
│  │  ─────────────  │                                                         │
│  │ • Length (-l)   │                                                         │
│  │ • Count (-n)    │                                                         │
│  │ • Options       │                                                         │
│  └────────┬────────┘                                                         │
│           │                                                                  │
│           ▼                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                        CONFIGURATION                                  │    │
│  │  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐           │    │
│  │  │ Character     │  │   Security    │  │   Output      │           │    │
│  │  │ Sets          │  │   Settings    │  │   Settings    │           │    │
│  │  │ • Uppercase   │  │ • Exclude     │  │ • Format      │           │    │
│  │  │ • Lowercase   │  │   Ambiguous   │  │ • Quiet mode  │           │    │
│  │  │ • Numbers     │  │ • Min length  │  │ • Save file   │           │    │
│  │  │ • Special     │  │ • Min score   │  │ • Clipboard   │           │    │
│  │  └───────────────┘  └───────────────┘  └───────────────┘           │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│           │                                                                  │
│           ▼                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                     GENERATION ENGINE                                 │    │
│  │                                                                        │    │
│  │    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐     │    │
│  │    │  Build   │───▶│  Fill    │───▶│ Shuffle  │───▶│ Validate │     │    │
│  │    │  Charset │    │  Buffer  │    │  Secure  │    │  Result  │     │    │
│  │    └──────────┘    └──────────┘    └──────────┘    └──────────┘     │    │
│  │         │                               │                             │    │
│  │         │         ┌──────────┐          │                             │    │
│  │         └────────▶│  secrets │◀─────────┘                             │    │
│  │                   │  module  │                                        │    │
│  │                   │ (CSPRNG) │                                        │    │
│  │                   └──────────┘                                        │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│           │                                                                  │
│           ▼                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                       OUTPUT MODULE                                   │    │
│  │                                                                        │    │
│  │  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐            │    │
│  │  │   Display     │  │   Strength    │  │    Export     │            │    │
│  │  │   Terminal    │  │   Checker     │  │   Options     │            │    │
│  │  │   (Rich)      │  │   Analysis    │  │               │            │    │
│  │  └───────────────┘  └───────────────┘  └───────────────┘            │    │
│  │          │                 │                  │                       │    │
│  │          ▼                 ▼                  ▼                       │    │
│  │    [Console]         [Score/Rating]    [File/Clipboard]              │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Password Strength Analysis Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD STRENGTH ANALYSIS FLOW                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  INPUT PASSWORD                                                              │
│       │                                                                      │
│       ▼                                                                      │
│  ┌────────────────┐                                                         │
│  │ LENGTH CHECK   │──────▶ Score: +5 to +25                                 │
│  │ • < 8: +5      │                                                         │
│  │ • 8-11: +10    │                                                         │
│  │ • 12-15: +20   │                                                         │
│  │ • 16+: +25     │                                                         │
│  └────────┬───────┘                                                         │
│           │                                                                  │
│           ▼                                                                  │
│  ┌────────────────┐                                                         │
│  │ CHARACTER      │──────▶ Score: +0 to +60                                 │
│  │ VARIETY        │                                                         │
│  │ • Uppercase+15 │                                                         │
│  │ • Lowercase+15 │                                                         │
│  │ • Numbers  +15 │                                                         │
│  │ • Special  +15 │                                                         │
│  └────────┬───────┘                                                         │
│           │                                                                  │
│           ▼                                                                  │
│  ┌────────────────┐                                                         │
│  │ PATTERN        │──────▶ Score: -0 to -20                                 │
│  │ PENALTIES      │                                                         │
│  │ • Sequential-10│                                                         │
│  │ • Repeated -10 │                                                         │
│  │ • Dictionary-10│                                                         │
│  └────────┬───────┘                                                         │
│           │                                                                  │
│           ▼                                                                  │
│  ┌─────────────────────────────────────────────────────────────────┐       │
│  │                      FINAL SCORE CALCULATION                      │       │
│  │                                                                    │       │
│  │   Total Score = Length + Variety - Penalties                      │       │
│  │                                                                    │       │
│  │   Rating:                                                          │       │
│  │   ┌────────────┬──────────────┬──────────────────────────────┐   │       │
│  │   │  Score     │   Rating     │   Action                     │   │       │
│  │   ├────────────┼──────────────┼──────────────────────────────┤   │       │
│  │   │  0-30      │ Very Weak ❌ │   Regenerate immediately     │   │       │
│  │   │  31-50     │ Weak     ⚠️  │   Not recommended            │   │       │
│  │   │  51-70     │ Moderate ✅  │   Acceptable for low-risk    │   │       │
│  │   │  71-90     │ Strong   ✅✅ │   Good for most purposes     │   │       │
│  │   │  91+       │ Very Str ✅✅✅│   Excellent security         │   │       │
│  │   └────────────┴──────────────┴──────────────────────────────┘   │       │
│  │                                                                    │       │
│  └────────────────────────────────────────────────────────────────────┘       │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

### Chapter Dependencies and Navigation

| Category | Chapter | Topic | Connection |
|----------|---------|-------|------------|
| **Prerequisites** | Ch47 | Python Basics | String manipulation, functions |
| | Ch48 | Advanced Python | argparse, file handling |
| | Ch49 | Bash Scripting | Alternative bash implementation |
| | Ch50 | Termux API | Clipboard functionality |
| **Related Projects** | Ch52 | Phone Info Extractor | Security tools |
| | Ch55 | Port Scanner | Security testing |
| | Ch57 | Backup Automation | Secure backup passwords |
| **Next Steps** | Ch58 | Troubleshooting | Error handling |
| | Ch61 | Security Best Practices | Password policies |

### Learning Path

```
Module 9 Projects Flow:
═══════════════════════

Ch51 Password Generator ──▶ Ch52 Phone Info ──▶ Ch53 WiFi Analyzer
         │                        │                     │
         │                        │                     │
         ▼                        ▼                     ▼
    [Security Tools]        [Device Info]        [Network Security]
         │                        │                     │
         └────────────────────────┼─────────────────────┘
                                  │
                                  ▼
Ch54 YouTube Bot ──▶ Ch55 Port Scanner ──▶ Ch56 File Organizer ──▶ Ch57 Backup
```

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Diceware Password Generation

```python
import secrets
import hashlib

# Diceware wordlist (simplified - use full 7776 word list in production)
DICEWARE_WORDS = [
    "abandon", "ability", "able", "about", "above", "absent", "absorb",
    "abstract", "absurd", "abuse", "access", "accident", "account",
    # ... 7776 words total
]

def generate_diceware(word_count=6):
    """
    Generate Diceware-style passphrase
    
    Example: "correct horse battery staple" style passwords
    Advantages:
    - Easy to remember
    - High entropy with enough words
    - Human-friendly
    
    6 words = 77 bits of entropy
    """
    words = [secrets.choice(DICEWARE_WORDS) for _ in range(word_count)]
    return ' '.join(words)

# Usage
passphrase = generate_diceware(6)
# Output: "ability accident account absorb abstract access"
# Entropy: ~77 bits (very strong!)
```

### Advanced Technique 2: Password Policy Engine

```python
class PasswordPolicy:
    """
    Configurable password policy enforcement
    """
    def __init__(self, policy_config):
        self.min_length = policy_config.get('min_length', 12)
        self.max_length = policy_config.get('max_length', 128)
        self.require_upper = policy_config.get('require_upper', True)
        self.require_lower = policy_config.get('require_lower', True)
        self.require_digit = policy_config.get('require_digit', True)
        self.require_special = policy_config.get('require_special', True)
        self.min_entropy = policy_config.get('min_entropy', 60)
        self.forbidden_patterns = policy_config.get('forbidden_patterns', [])
    
    def validate(self, password):
        """Validate password against policy"""
        errors = []
        
        if len(password) < self.min_length:
            errors.append(f"Too short (min: {self.min_length})")
        if len(password) > self.max_length:
            errors.append(f"Too long (max: {self.max_length})")
        if self.require_upper and not any(c.isupper() for c in password):
            errors.append("Missing uppercase letter")
        if self.require_lower and not any(c.islower() for c in password):
            errors.append("Missing lowercase letter")
        if self.require_digit and not any(c.isdigit() for c in password):
            errors.append("Missing digit")
        if self.require_special and not any(c in SPECIAL for c in password):
            errors.append("Missing special character")
        
        # Calculate entropy
        entropy = self._calculate_entropy(password)
        if entropy < self.min_entropy:
            errors.append(f"Entropy too low ({entropy:.1f} < {self.min_entropy})")
        
        # Check forbidden patterns
        for pattern in self.forbidden_patterns:
            if pattern.lower() in password.lower():
                errors.append(f"Contains forbidden pattern: {pattern}")
        
        return len(errors) == 0, errors
    
    def _calculate_entropy(self, password):
        charset_size = 0
        if any(c.isupper() for c in password): charset_size += 26
        if any(c.islower() for c in password): charset_size += 26
        if any(c.isdigit() for c in password): charset_size += 10
        if any(c in SPECIAL for c in password): charset_size += len(SPECIAL)
        return len(password) * (charset_size ** 0.5).bit_length()
```

### Advanced Technique 3: Password Leak Checker Integration

```python
import hashlib
import requests

class PasswordLeakChecker:
    """
    Check if password has appeared in known data breaches
    Uses HaveIBeenPwned API with k-anonymity
    """
    
    API_URL = "https://api.pwnedpasswords.com/range/"
    
    def check(self, password):
        """
        Check if password is in breach database
        
        Returns: (is_breached, breach_count)
        """
        # Hash the password
        sha1_hash = hashlib.sha1(password.encode()).hexdigest().upper()
        
        # k-anonymity: only send first 5 chars of hash
        prefix = sha1_hash[:5]
        suffix = sha1_hash[5:]
        
        try:
            response = requests.get(f"{self.API_URL}{prefix}", timeout=5)
            
            if response.status_code == 200:
                # Parse response
                hashes = response.text.splitlines()
                for hash_line in hashes:
                    hash_suffix, count = hash_line.split(':')
                    if hash_suffix == suffix:
                        return True, int(count)
                
                return False, 0
            else:
                # API error - assume safe
                return None, 0
                
        except requests.RequestException:
            # Network error - can't verify
            return None, 0

def generate_and_verify(length=16):
    """Generate password and verify it's not in breach database"""
    checker = PasswordLeakChecker()
    
    while True:
        password = generate_password(length)
        is_breached, count = checker.check(password)
        
        if is_breached == False:
            return password
        elif is_breached == True:
            print(f"Password found in breaches ({count} times). Regenerating...")
            continue
        else:
            print("Could not verify. Using anyway.")
            return password
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### What You Should Have Learned

- [ ] Understanding of password security fundamentals
- [ ] Difference between `random` and `secrets` modules
- [ ] How to generate passwords with configurable options
- [ ] Implementing password strength analysis
- [ ] Creating pronounceable passwords
- [ ] Building CLI with argparse
- [ ] File operations for saving passwords
- [ ] Termux clipboard integration
- [ ] Bash alternative implementation
- [ ] Password entropy calculation
- [ ] Character set management
- [ ] Error handling best practices

### Skills Acquired

| Skill | Level | Description |
|-------|-------|-------------|
| Cryptographic Random | ⭐⭐⭐ | Using `secrets` for secure generation |
| String Manipulation | ⭐⭐⭐ | Building and processing password strings |
| CLI Development | ⭐⭐ | argparse for command-line interfaces |
| File I/O | ⭐⭐ | Reading/writing configuration and history |
| Security Analysis | ⭐⭐⭐ | Password strength and entropy calculation |
| Bash Scripting | ⭐⭐ | Alternative implementation in shell |

---

## 🚀 PROJECT CHALLENGES

### Challenge 1: Password Policy Configuration System

**Task:** Create a JSON-based configuration system that allows administrators to define custom password policies per environment.

**Requirements:**
- Load policies from JSON config file
- Support multiple policy profiles (dev, staging, prod)
- Implement policy validation
- Add command-line flag to select profile

**Hint:** Create a `PasswordPolicy` class that loads from config and validates passwords.

```bash
# Expected usage:
python pgen.py --policy prod --length 20
python pgen.py --policy dev --length 12
```

### Challenge 2: Password Vault Integration

**Task:** Integrate with a password manager to automatically save generated passwords.

**Requirements:**
- Support at least one password manager (Bitwarden CLI, KeePass, etc.)
- Store password with metadata (URL, username, notes)
- Handle encryption for storage
- Provide retrieval functionality

**Hint:** Use subprocess to call password manager CLI tools.

```bash
# Expected usage:
python pgen.py --save-to bitwarden --name "github" --url "github.com"
```

### Challenge 3: Real-time Password Quality Dashboard

**Task:** Create a visual dashboard that shows password quality metrics in real-time as the user types or modifies generation options.

**Requirements:**
- Show entropy calculation
- Display character distribution chart
- Show estimated crack time
- Highlight security issues
- Suggest improvements

**Hint:** Use Rich library's live display feature for real-time updates.

```bash
# Expected usage:
python pgen.py --interactive
# Shows live dashboard as user adjusts options
```

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always use `secrets` module instead of `random` for passwords. `random` is predictable and can be exploited!

> 💡 **Pro Tip #2:** Create a password config file (`~/.pgen_config.json`) to store your preferred settings - no need to pass arguments every time!

> 💡 **Pro Tip #3:** Use `-c` flag to copy password directly to clipboard - prevents shoulder surfing attacks!

> 💡 **Pro Tip #4:** For maximum security, use 20+ character passwords with all character types enabled. Each additional character exponentially increases security!

> 💡 **Pro Tip #5:** Password entropy > 80 bits is considered strong. Our tool calculates and displays entropy for you!

> 💡 **Pro Tip #6:** Exclude ambiguous characters (`il1Lo0O`) when creating passwords that need to be typed manually - prevents confusion!

> 💡 **Pro Tip #7:** Use pronounceable passwords (`-p` flag) for passwords you need to remember verbally - easier to communicate!

> 💡 **Pro Tip #8:** Always save important passwords with `-s` flag. The timestamp helps track when passwords were generated!

> 💡 **Pro Tip #9:** Batch generate passwords (`-n 10`) and pick the strongest one using the strength indicator!

> 💡 **Pro Tip #10:** Combine this tool with a password manager like Bitwarden for ultimate security workflow!

---

## 🔥 REAL WORLD USE CASES

### Real World Applications of Password Generator

**1. Personal Security**
- Generate unique passwords for each online account
- Create secure WiFi passwords for home network
- Generate PIN codes with higher entropy

**2. Professional Use**
- IT administrators generating initial passwords for new employees
- Database credentials with guaranteed complexity
- API keys and service tokens

**3. Development & Testing**
- Test password validation systems with known-good passwords
- Generate test data for user registration flows
- Create mock authentication systems

**4. Security Auditing**
- Demonstrate password strength to clients
- Educational tool for security awareness training
- Create benchmark passwords for cracking tests

**5. Business Applications**
- Corporate password policies enforcement
- Batch password generation for system migrations
- Compliance with security standards (PCI-DSS, HIPAA)

---

## ⚡ QUICK REFERENCE CARD

### Password Generator Quick Reference

| Command | Description | Example |
|---------|-------------|---------|
| `python pgen.py` | Generate default 16-char password | `Kx9#mP2$vL7@nQ4!` |
| `-l LENGTH` | Set password length | `-l 20` |
| `-n COUNT` | Generate multiple passwords | `-n 5` |
| `--no-upper` | Exclude uppercase letters | `--no-upper` |
| `--no-lower` | Exclude lowercase letters | `--no-lower` |
| `--no-numbers` | Exclude numbers | `--no-numbers` |
| `--no-special` | Exclude special characters | `--no-special` |
| `--exclude-ambiguous` | Remove confusing chars | `--exclude-ambiguous` |
| `-p` | Pronounceable password | `-p` |
| `-c` | Copy to clipboard | `-c` |
| `-s` | Save to file | `-s` |
| `--check "pass"` | Check password strength | `--check "test123"` |
| `-q` | Quiet mode (password only) | `-q` |

### Password Strength Ratings

| Score | Rating | Action |
|-------|--------|--------|
| 0-30 | Very Weak | ❌ Regenerate |
| 31-50 | Weak | ⚠️ Avoid |
| 51-70 | Moderate | ✅ Acceptable |
| 71-90 | Strong | ✅✅ Good |
| 91+ | Very Strong | ✅✅✅ Excellent |

---

## 🏆 BONUS CONTENT

### Bonus: Project Extensions

Want to take this project further? Here are advanced features you can add:

**Extension 1: Password Vault Integration**
```python
# Integrate with Bitwarden CLI
def save_to_bitwarden(password, name):
    subprocess.run(['bw', 'create', 'item', 
        f'{{"name":"{name}","login":{{"password":"{password}"}}}}'])
```

**Extension 2: QR Code Generator**
```python
import qrcode
def generate_qr(password):
    qr = qrcode.make(password)
    qr.save(f'password_{datetime.now().timestamp()}.png')
```

**Extension 3: Password Expiry Tracker**
```python
# Track when passwords were generated and alert for renewal
def check_password_age(password_file):
    # Alert if password is older than 90 days
    pass
```

**Extension 4: Diceware Password Generator**
```python
# Generate passwords using diceware wordlist
# Example: "correct horse battery staple"
DICEWARE_WORDS = [...]  # 7776 word list
```

**Extension 5: Password Pattern Analyzer**
```python
def analyze_patterns(password):
    # Detect keyboard patterns (qwerty, asdf)
    # Detect sequences (abc, 123)
    # Detect repeats (aaa, 111)
    pass
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **Password Security Fundamentals** - Why strong passwords matter and what makes them secure
- ✅ **Cryptographic Random Generation** - Using `secrets` module for secure randomness
- ✅ **Python String Manipulation** - Working with character sets and string operations
- ✅ **Password Strength Analysis** - Implementing entropy calculation and strength scoring
- ✅ **CLI Argument Parsing** - Building user-friendly command-line interfaces
- ✅ **Bash Scripting** - Creating lightweight shell script alternatives
- ✅ **Termux API Integration** - Using clipboard functionality
- ✅ **File Operations** - Saving and organizing generated passwords

### Key Takeaways

1. **Security First** - Always use cryptographically secure random generators
2. **User Convenience** - Provide options for different use cases
3. **Validation** - Always check and display password strength
4. **Flexibility** - Allow customization while maintaining defaults

---

## 🚀 PROJECT EXTENSIONS

### 5+ Ideas to Extend This Project

**Extension 1: Password Manager Integration** ⭐⭐⭐
- Add ability to export directly to password managers
- Support formats: Bitwarden JSON, KeePass XML, 1Password CSV
- **Steps:** Create export module with format converters

**Extension 2: Web Interface** ⭐⭐⭐⭐
- Build a simple Flask web app for password generation
- Beautiful UI with strength meter visualization
- **Steps:** `pip install flask`, create templates, add API endpoints

**Extension 3: Password Breach Checker** ⭐⭐⭐
- Check if generated password exists in known breach databases
- Use HaveIBeenPwned API
- **Steps:** Implement API call with k-anonymity model

**Extension 4: Password Policy Enforcer** ⭐⭐⭐
- Define custom password policies (min length, required chars)
- Validate passwords against organizational standards
- **Steps:** Create policy parser and validator module

**Extension 5: Secure Password Sharing** ⭐⭐⭐⭐⭐
- One-time password sharing links (like PrivateBin)
- Self-destructing password shares
- **Steps:** Implement encryption, create web service

**Extension 6: Password Audit Report** ⭐⭐⭐
- Generate comprehensive report of all generated passwords
- Include strength analysis, age, recommendations
- **Steps:** Create PDF report generator with charts

---

## 🔧 CODE WALKTHROUGH

### Line-by-Line Explanation of Core Functions

```python
# Line 1-5: Import cryptographic modules
import secrets        # Secure random number generation
import string         # String constants (ascii_letters, digits)
import random         # General random (not for passwords!)
```

**The `generate_password` function:**
```python
def generate_password(length=16, use_upper=True, ...):
    """
    Line-by-line breakdown:
    
    1. characters = ""          # Initialize empty string for char pool
    2. if use_upper: ...        # Add uppercase if requested (A-Z)
    3. if use_lower: ...        # Add lowercase if requested (a-z)
    4. if use_numbers: ...      # Add digits if requested (0-9)
    5. if use_special: ...      # Add symbols if requested (!@#$)
    6. password = []            # Create list to hold password chars
    7. password.append(...)     # Ensure at least one of each type
    8. secrets.choice()         # Cryptographically secure random pick
    9. shuffle()                # Randomize character positions
    10. return ''.join()        # Convert list to string
    """
```

**Architecture Diagram:**
```
┌─────────────────────────────────────────────────────────────┐
│                    PASSWORD GENERATOR FLOW                   │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│   USER INPUT          PROCESSING           OUTPUT            │
│   ──────────          ──────────           ──────            │
│                                                              │
│   Length: 16    ──►  Build char pool   ──►  Display         │
│   Upper: True        ├─ A-Z (26)            ├─ Terminal     │
│   Lower: True        ├─ a-z (26)            ├─ Clipboard    │
│   Numbers: True      ├─ 0-9 (10)            └─ File         │
│   Special: True      └─ !@#$ (32)                          │
│                                                              │
│                    GENERATION ENGINE                         │
│                    ─────────────────                         │
│                    1. Pick required chars                    │
│                    2. Fill remaining with secrets.choice()   │
│                    3. Shuffle with SystemRandom              │
│                    4. Validate against rules                 │
│                                                              │
│                    STRENGTH CHECKER                          │
│                    ────────────────                          │
│                    1. Calculate entropy (bits)               │
│                    2. Check character variety                │
│                    3. Detect patterns                        │
│                    4. Return score + feedback                │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

## 📦 DEPLOYMENT GUIDE

### How to Deploy and Share This Project

**1. Create GitHub Repository**
```bash
cd ~/projects/password-generator
git init
git add pgen.py pgen.sh README.md
git commit -m "Initial commit: Password Generator Tool"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/password-generator.git
git push -u origin main
```

**2. Create README.md**
```markdown
# Password Generator Tool

A secure password generator with strength analysis.

## Installation
```bash
git clone https://github.com/YOUR_USERNAME/password-generator.git
cd password-generator
pip install colorama
```

## Usage
```bash
python pgen.py -l 20 -n 5 -s
```
```

**3. Make it Installable (setup.py)**
```python
from setuptools import setup
setup(
    name='pgen',
    version='1.0.0',
    py_modules=['pgen'],
    install_requires=['colorama'],
    entry_points={
        'console_scripts': ['pgen=pgen:main']
    }
)
```

**4. Install Globally on Termux**
```bash
pip install -e ~/projects/password-generator
# Now 'pgen' command works from anywhere!
```

**5. Share as Standalone Script**
```bash
# Create standalone executable
pip install pyinstaller
pyinstaller --onefile pgen.py
# Share the dist/pgen file
```

---

## 🔗 RELATED CHAPTERS

### Cross-Reference to Related Chapters

| Chapter | Topic | Connection |
|---------|-------|------------|
| **Ch52** | Phone Info Extractor | Both use Termux APIs |
| **Ch55** | Port Scanner | Security tools family |
| **Ch57** | Backup Automation | Secure backup passwords |
| **Ch47** | Python Basics | Foundation for this project |
| **Ch49** | Bash Scripting | Bash version of this tool |
| **Ch61** | Security Best Practices | Password security context |

### Prerequisite Chapters
- 📖 **Ch47: Python Basics** - Understanding Python syntax
- 📖 **Ch48: Advanced Python** - Modules and packages
- 📖 **Ch49: Bash Scripting** - Shell scripting basics

### Next Steps
- ➡️ **Ch52: Phone Info Extractor** - Learn Termux API integration
- ➡️ **Ch53: WiFi Analyzer** - Network security project

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your Password Generator Knowledge!

**Question 1:** Which Python module should be used for secure password generation?
- a) `random`
- b) `secrets` ✓
- c) `numpy`
- d) `math`

**Question 2:** What is the recommended minimum password length for strong security?
- a) 8 characters
- b) 12 characters
- c) 16 characters ✓
- d) 6 characters

**Question 3:** What does `-p` flag do in our password generator?
- a) Print password
- b) Pronounceable password ✓
- c) Password file
- d) Parallel generation

**Question 4:** Which command saves generated passwords to a file?
- a) `-f`
- b) `-o`
- c) `-s` ✓
- d) `-w`

**Question 5:** What is password entropy?
- a) Password length
- b) Measure of password randomness in bits ✓
- c) Number of special characters
- d) Time to crack password

**Question 6:** Which character set adds the most entropy per character?
- a) Lowercase letters
- b) Uppercase letters
- c) Numbers
- d) Special characters ✓

**Question 7:** What score range indicates a "Very Strong" password?
- a) 50-70
- b) 60-80
- c) 71-90
- d) 91+ ✓

**Question 8:** Why should `il1Lo0O` characters be excluded sometimes?
- a) They're hard to type
- b) They look similar and cause confusion ✓
- c) They're not allowed in passwords
- d) They decrease entropy

**Question 9:** What does `--check` flag do?
- a) Check for password duplicates
- b) Analyze password strength ✓
- c) Check password age
- d) Check against breach database

**Question 10:** How do you copy password to clipboard in Termux?
- a) `-c` flag with termux-api ✓
- b) Ctrl+C
- c) `--copy` flag
- d) It's automatic

**Question 11:** What is the entropy of a 16-character password using all character types?
- a) ~80 bits
- b) ~95-100 bits ✓
- c) ~50 bits
- d) ~128 bits

**Question 12:** Which command generates 5 passwords of 20 characters each?
- a) `python pgen.py -l 5 -n 20`
- b) `python pgen.py -l 20 -n 5` ✓
- c) `python pgen.py 20 5`
- d) `python pgen.py --count 5 --length 20`

---

### Extend the Project Challenges

**Challenge 1:** Add a feature to check if password contains dictionary words
```python
# Hint: Use a wordlist file and check substrings
def contains_dictionary_word(password, wordlist_file):
    # Your code here
    pass
```

**Challenge 2:** Implement password generation based on a passphrase
```python
# Generate password from memorable phrase
# "I love pizza at 5 PM" -> "Ilp@5PM"
def passphrase_to_password(phrase):
    # Your code here
    pass
```

**Challenge 3:** Add two-factor authentication code generator
```python
# Generate TOTP codes alongside passwords
import pyotp
def generate_totp(secret):
    # Your code here
    pass
```

### Bug Fixing Exercises

**Bug 1:** Find and fix the issue:
```python
def generate_password(length):
    chars = "abcdefghijklmnopqrstuvwxyz"
    password = ""
    for i in range(length):
        password += random.choice(chars)  # Bug: uses random, not secrets!
    return password
```
*Fix: Replace `random.choice` with `secrets.choice`*

**Bug 2:** Why does this generate less secure passwords?
```python
password = ''.join(secrets.choice(chars) for _ in range(length))
# Issue: May not include all character types!
```
*Fix: Ensure at least one character from each required type*

**Bug 3:** What's wrong with this entropy calculation?
```python
entropy = len(password) * math.log2(26)  # Always assumes lowercase only
```
*Fix: Calculate actual character pool size based on included types*

---

## 📖 TECHNICAL GUIDE

### 1. Project Overview

Password Generator Tool ek essential utility hai jo strong, random
passwords generate karta hai. Ye tool security professionals, developers,
aur common users ke liye useful hai.

### Project Requirements

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PROJECT REQUIREMENTS                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ Software:                                                                │
│ ├── Termux (F-Droid version)                                            │
│ ├── Python 3.9+                                                         │
│ ├── Bash 5.0+                                                           │
│ └── Termux:API (optional, for clipboard)                                │
│                                                                          │
│ Python Packages:                                                         │
│ ├── secrets (built-in)                                                  │
│ ├── string (built-in)                                                   │
│ ├── argparse (built-in)                                                 │
│ ├── json (built-in)                                                     │
│ └── colorama (pip install colorama)                                     │
│                                                                          │
│ Storage:                                                                 │
│ └── ~5MB for project files                                              │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Design the Password Generator

#### Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD GENERATOR DESIGN                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                         ┌─────────────┐                                 │
│                         │    USER     │                                 │
│                         │  INTERFACE  │                                 │
│                         └──────┬──────┘                                 │
│                                │                                         │
│              ┌─────────────────┼─────────────────┐                      │
│              │                 │                 │                       │
│              ▼                 ▼                 ▼                       │
│     ┌─────────────┐   ┌─────────────┐   ┌─────────────┐                 │
│     │    CLI      │   │    ARGS     │   │  INTERACTIVE │                 │
│     │   MODE      │   │   PARSER    │   │     MODE     │                 │
│     └──────┬──────┘   └─────────────┘   └──────────────┘                 │
│            │                                                              │
│            ▼                                                              │
│     ┌─────────────────────────────────────────────────────┐             │
│     │              PASSWORD GENERATOR ENGINE               │             │
│     │  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌────────┐ │             │
│     │  │ Random  │  │Pronounce│  │Strength │  │ Pattern│ │             │
│     │  │ Gen     │  │  able   │  │ Check   │  │ Avoid  │ │             │
│     │  └─────────┘  └─────────┘  └─────────┘  └────────┘ │             │
│     └─────────────────────────────────────────────────────┘             │
│                                │                                         │
│              ┌─────────────────┼─────────────────┐                      │
│              │                 │                 │                       │
│              ▼                 ▼                 ▼                       │
│     ┌─────────────┐   ┌─────────────┐   ┌─────────────┐                 │
│     │   DISPLAY   │   │   CLIPBOARD │   │    FILE     │                 │
│     │   OUTPUT    │   │   (Termux)  │   │   STORAGE   │                 │
│     └─────────────┘   └─────────────┘   └─────────────┘                 │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Features to Implement

#### A. Random Password Generation

```python
# Using secrets module for cryptographic security
import secrets

def secure_random_choice(characters):
    """Cryptographically secure random selection"""
    return secrets.choice(characters)

def secure_shuffle(list_to_shuffle):
    """Securely shuffle a list"""
    secrets.SystemRandom().shuffle(list_to_shuffle)
```

#### B. Customizable Length

```python
# Length validation
def validate_length(length):
    MIN_LENGTH = 4
    MAX_LENGTH = 128
    
    if length < MIN_LENGTH:
        raise ValueError(f"Minimum length is {MIN_LENGTH}")
    if length > MAX_LENGTH:
        raise ValueError(f"Maximum length is {MAX_LENGTH}")
    
    return length
```

#### C. Include/Exclude Character Types

```python
# Character set configuration
CHAR_CONFIG = {
    'upper': {
        'chars': 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
        'required': True
    },
    'lower': {
        'chars': 'abcdefghijklmnopqrstuvwxyz',
        'required': True
    },
    'numbers': {
        'chars': '0123456789',
        'required': False
    },
    'special': {
        'chars': '!@#$%^&*()_+-=[]{}|;:,.<>?',
        'required': False
    }
}
```

#### D. Password Strength Indicator

```python
def calculate_entropy(password):
    """Calculate password entropy in bits"""
    import math
    
    # Count character pool size
    pool_size = 0
    if any(c.islower() for c in password):
        pool_size += 26
    if any(c.isupper() for c in password):
        pool_size += 26
    if any(c.isdigit() for c in password):
        pool_size += 10
    if any(c in SPECIAL for c in password):
        pool_size += len(SPECIAL)
    
    # Calculate entropy
    entropy = len(password) * math.log2(pool_size) if pool_size > 0 else 0
    return round(entropy, 2)
```

#### E. Copy to Clipboard (Termux)

```python
def copy_to_clipboard(text):
    """Copy text to clipboard using Termux API"""
    import subprocess
    
    try:
        subprocess.run(['termux-clipboard-set'], 
                      input=text.encode(), 
                      check=True)
        return True
    except FileNotFoundError:
        print("Install Termux:API for clipboard support")
        return False
    except subprocess.CalledProcessError:
        return False
```

#### F. Save to File

```python
def save_passwords(passwords, filename="passwords.txt"):
    """Save passwords with timestamp and metadata"""
    from datetime import datetime
    
    filepath = os.path.expanduser(f"~/{filename}")
    timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    
    with open(filepath, 'a') as f:
        f.write(f"\n{'='*50}\n")
        f.write(f"Generated: {timestamp}\n")
        f.write(f"{'='*50}\n")
        
        for i, pwd in enumerate(passwords, 1):
            strength = check_strength(pwd)
            f.write(f"{i}. {pwd}\n")
            f.write(f"   Strength: {strength['rating']}\n")
            f.write(f"   Length: {len(pwd)}\n")
        
        f.write(f"{'='*50}\n")
    
    return filepath
```

#### G. Multiple Passwords

```python
def generate_multiple(count, **kwargs):
    """Generate multiple unique passwords"""
    passwords = set()  # Use set for uniqueness
    
    while len(passwords) < count:
        pwd = generate_password(**kwargs)
        if pwd:
            passwords.add(pwd)
    
    return list(passwords)
```

#### H. Pronounceable Passwords

```python
def generate_pronounceable(syllables=4, include_number=True):
    """Generate a pronounceable password using syllables"""
    
    consonants = "bcdfghjklmnpqrstvwxyz"
    vowels = "aeiou"
    
    password_parts = []
    
    for _ in range(syllables):
        # Create syllable: consonant + vowel + optional consonant
        syllable = secrets.choice(consonants)
        syllable += secrets.choice(vowels)
        
        # 50% chance to add another consonant
        if secrets.randbelow(2):
            syllable += secrets.choice(consonants)
        
        password_parts.append(syllable)
    
    password = ''.join(password_parts)
    
    # Add number at the end
    if include_number:
        password += str(secrets.randbelow(100))
    
    # Capitalize first letter
    return password.capitalize()
```

---

## 💻 COMPLETE SOURCE CODE

### Python Version (pgen.py)

```python
#!/usr/bin/env python3
"""
╔═══════════════════════════════════════════════════════════════════════════╗
║                    PASSWORD GENERATOR TOOL                                 ║
║                    by T3rmuxk1ng                                          ║
╠═══════════════════════════════════════════════════════════════════════════╣
║  Features:                                                                 ║
║  • Random password generation                                              ║
║  • Customizable length and character sets                                  ║
║  • Password strength analysis                                              ║
║  • Pronounceable passwords                                                 ║
║  • Clipboard support (Termux)                                              ║
║  • Save to file with timestamp                                             ║
║  • Bulk generation                                                         ║
╚═══════════════════════════════════════════════════════════════════════════╝
"""

import secrets
import string
import random
import argparse
import json
import os
import sys
import math
import subprocess
from datetime import datetime
from pathlib import Path

# Optional imports with fallback
try:
    from colorama import Fore, Style, init
    init(autoreset=True)
    COLORS = True
except ImportError:
    COLORS = False
    # Create dummy Fore class for non-colored output
    class Fore:
        RED = GREEN = YELLOW = BLUE = MAGENTA = CYAN = WHITE = ""
    class Style:
        BRIGHT = RESET_ALL = ""

# ═══════════════════════════════════════════════════════════════════════════
# CONSTANTS
# ═══════════════════════════════════════════════════════════════════════════

VERSION = "2.0.0"
AUTHOR = "T3rmuxk1ng"

# Character sets
UPPERCASE = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
LOWERCASE = "abcdefghijklmnopqrstuvwxyz"
NUMBERS = "0123456789"
SPECIAL = "!@#$%^&*()_+-=[]{}|;:,.<>?"
AMBIGUOUS = "il1Lo0O"

# Pronounceable components
VOWELS = "aeiou"
CONSONANTS = "bcdfghjklmnpqrstvwxyz"

# Default config
DEFAULT_CONFIG = {
    'default_length': 16,
    'use_upper': True,
    'use_lower': True,
    'use_numbers': True,
    'use_special': True,
    'exclude_ambiguous': False,
    'save_file': '~/passwords.txt'
}

# ═══════════════════════════════════════════════════════════════════════════
# HELPER FUNCTIONS
# ═══════════════════════════════════════════════════════════════════════════

def print_header(title):
    """Print a styled header"""
    if COLORS:
        print(f"\n{Fore.CYAN}{'═' * 50}")
        print(f"{Fore.CYAN}  {title}")
        print(f"{Fore.CYAN}{'═' * 50}{Style.RESET_ALL}")
    else:
        print(f"\n{'═' * 50}")
        print(f"  {title}")
        print(f"{'═' * 50}")

def print_success(message):
    """Print success message"""
    if COLORS:
        print(f"{Fore.GREEN}✓ {message}{Style.RESET_ALL}")
    else:
        print(f"✓ {message}")

def print_error(message):
    """Print error message"""
    if COLORS:
        print(f"{Fore.RED}✗ {message}{Style.RESET_ALL}", file=sys.stderr)
    else:
        print(f"✗ {message}", file=sys.stderr)

def print_warning(message):
    """Print warning message"""
    if COLORS:
        print(f"{Fore.YELLOW}⚠ {message}{Style.RESET_ALL}")
    else:
        print(f"⚠ {message}")

def print_info(message):
    """Print info message"""
    if COLORS:
        print(f"{Fore.BLUE}ℹ {message}{Style.RESET_ALL}")
    else:
        print(f"ℹ {message}")

# ═══════════════════════════════════════════════════════════════════════════
# CONFIGURATION
# ═══════════════════════════════════════════════════════════════════════════

def get_config_path():
    """Get config file path"""
    return Path.home() / ".pgen_config.json"

def load_config():
    """Load user configuration"""
    config = DEFAULT_CONFIG.copy()
    config_path = get_config_path()
    
    if config_path.exists():
        try:
            with open(config_path, 'r') as f:
                saved = json.load(f)
                config.update(saved)
        except (json.JSONDecodeError, IOError):
            pass
    
    return config

def save_config(config):
    """Save user configuration"""
    config_path = get_config_path()
    
    try:
        with open(config_path, 'w') as f:
            json.dump(config, f, indent=2)
        return True
    except IOError:
        return False

# ═══════════════════════════════════════════════════════════════════════════
# PASSWORD GENERATION
# ═══════════════════════════════════════════════════════════════════════════

def generate_password(length=16, use_upper=True, use_lower=True, 
                      use_numbers=True, use_special=True, 
                      exclude_ambiguous=False, min_each_type=1):
    """
    Generate a cryptographically secure random password.
    
    Args:
        length: Password length (4-128)
        use_upper: Include uppercase letters
        use_lower: Include lowercase letters
        use_numbers: Include numbers
        use_special: Include special characters
        exclude_ambiguous: Exclude ambiguous characters (il1Lo0O)
        min_each_type: Minimum characters from each selected type
    
    Returns:
        Generated password string or None if invalid config
    """
    
    # Validate length
    if length < 4:
        print_error("Password length must be at least 4")
        return None
    if length > 128:
        print_error("Password length must not exceed 128")
        return None
    
    # Build character pool
    char_pool = ""
    required_chars = []
    
    if use_upper:
        chars = UPPERCASE
        if exclude_ambiguous:
            chars = ''.join(c for c in chars if c not in AMBIGUOUS)
        char_pool += chars
        for _ in range(min_each_type):
            required_chars.append(secrets.choice(chars))
    
    if use_lower:
        chars = LOWERCASE
        if exclude_ambiguous:
            chars = ''.join(c for c in chars if c not in AMBIGUOUS)
        char_pool += chars
        for _ in range(min_each_type):
            required_chars.append(secrets.choice(chars))
    
    if use_numbers:
        chars = NUMBERS
        if exclude_ambiguous:
            chars = ''.join(c for c in chars if c not in AMBIGUOUS)
        char_pool += chars
        for _ in range(min_each_type):
            required_chars.append(secrets.choice(chars))
    
    if use_special:
        char_pool += SPECIAL
        for _ in range(min_each_type):
            required_chars.append(secrets.choice(SPECIAL))
    
    if not char_pool:
        print_error("At least one character type must be selected")
        return None
    
    # Check if length is sufficient for required chars
    if len(required_chars) > length:
        print_error("Password too short for selected options")
        return None
    
    # Fill remaining length with random characters
    remaining_length = length - len(required_chars)
    password_chars = required_chars + [
        secrets.choice(char_pool) for _ in range(remaining_length)
    ]
    
    # Securely shuffle
    secrets.SystemRandom().shuffle(password_chars)
    
    return ''.join(password_chars)


def generate_pronounceable(syllables=4, include_number=True, 
                          include_special=False):
    """
    Generate a pronounceable password.
    
    Args:
        syllables: Number of syllables
        include_number: Add number at the end
        include_special: Add special character
    
    Returns:
        Pronounceable password string
    """
    
    password_parts = []
    
    for i in range(syllables):
        # Create syllable pattern
        if i == 0:
            # First syllable starts with consonant
            syllable = secrets.choice(CONSONANTS.upper())
        else:
            syllable = secrets.choice(CONSONANTS)
        
        syllable += secrets.choice(VOWELS)
        
        # Optional ending consonant (50% chance)
        if secrets.randbelow(2):
            syllable += secrets.choice(CONSONANTS)
        
        password_parts.append(syllable)
    
    password = ''.join(password_parts)
    
    # Add number
    if include_number:
        password += str(secrets.randbelow(100))
    
    # Add special character
    if include_special:
        password += secrets.choice(SPECIAL)
    
    return password


def generate_passphrase(word_count=4, separator='-', capitalize=True):
    """
    Generate a passphrase from random words.
    
    Args:
        word_count: Number of words
        separator: Word separator
        capitalize: Capitalize each word
    
    Returns:
        Passphrase string
    """
    
    # Common word list (you can expand this or use a file)
    words = [
        'apple', 'banana', 'cherry', 'dragon', 'elephant',
        'forest', 'garden', 'horizon', 'island', 'jungle',
        'kitchen', 'lemon', 'mountain', 'nature', 'ocean',
        'planet', 'queen', 'river', 'sunset', 'thunder',
        'umbrella', 'valley', 'water', 'yellow', 'zebra',
        'bridge', 'castle', 'diamond', 'energy', 'flower',
        'guitar', 'harmony', 'impulse', 'journey', 'knight',
        'liberty', 'mystery', 'network', 'orange', 'phoenix',
        'quantum', 'rainbow', 'shadow', 'tornado', 'universe',
        'victory', 'window', 'crystal', 'balance', 'cosmos'
    ]
    
    selected = [secrets.choice(words) for _ in range(word_count)]
    
    if capitalize:
        selected = [w.capitalize() for w in selected]
    
    return separator.join(selected)


def generate_pin(length=6, no_repeating=True):
    """
    Generate a numeric PIN.
    
    Args:
        length: PIN length
        no_repeating: Avoid repeating digits
    
    Returns:
        PIN string
    """
    
    if no_repeating and length > 10:
        print_warning("Cannot avoid repeating with length > 10")
        no_repeating = False
    
    if no_repeating:
        digits = list(NUMBERS)
        secrets.SystemRandom().shuffle(digits)
        return ''.join(digits[:length])
    else:
        return ''.join(secrets.choice(NUMBERS) for _ in range(length))

# ═══════════════════════════════════════════════════════════════════════════
# PASSWORD ANALYSIS
# ═══════════════════════════════════════════════════════════════════════════

def calculate_entropy(password):
    """Calculate password entropy in bits."""
    
    pool_size = 0
    
    if any(c.islower() for c in password):
        pool_size += 26
    if any(c.isupper() for c in password):
        pool_size += 26
    if any(c.isdigit() for c in password):
        pool_size += 10
    if any(c in SPECIAL for c in password):
        pool_size += len(SPECIAL)
    
    if pool_size == 0:
        return 0
    
    entropy = len(password) * math.log2(pool_size)
    return round(entropy, 2)


def has_sequential(password, min_length=3):
    """Check for sequential characters."""
    
    password = password.lower()
    sequences = [
        'abc', 'bcd', 'cde', 'def', 'efg', 'fgh', 'ghi', 'hij',
        'ijk', 'jkl', 'klm', 'lmn', 'mno', 'nop', 'opq', 'pqr',
        'qrs', 'rst', 'stu', 'tuv', 'uvw', 'vwx', 'wxy', 'xyz',
        '012', '123', '234', '345', '456', '567', '678', '789',
        '890', 'qwerty', 'asdf', 'zxcv'
    ]
    
    for seq in sequences:
        if seq in password:
            return True
    
    return False


def has_repeated(password, min_count=3):
    """Check for repeated characters."""
    
    for i in range(len(password) - min_count + 1):
        substring = password[i:i+min_count]
        if len(set(substring)) == 1:
            return True
    
    return False


def check_common_passwords(password):
    """Check if password is in common password list."""
    
    common = [
        'password', '123456', '12345678', 'qwerty', 'abc123',
        'monkey', 'master', 'dragon', '111111', 'baseball',
        'iloveyou', 'trustno1', 'sunshine', 'princess', 'welcome',
        'shadow', 'superman', 'michael', 'football', 'password1'
    ]
    
    return password.lower() in common


def analyze_password(password):
    """
    Perform comprehensive password analysis.
    
    Returns dict with score, rating, entropy, and feedback.
    """
    
    score = 0
    feedback = []
    warnings = []
    
    # Length analysis
    length = len(password)
    
    if length >= 20:
        score += 30
        feedback.append("Excellent length (20+)")
    elif length >= 16:
        score += 25
        feedback.append("Great length (16+)")
    elif length >= 12:
        score += 20
        feedback.append("Good length (12+)")
    elif length >= 8:
        score += 10
        feedback.append("Minimum length (8+)")
    else:
        score += 5
        warnings.append("Too short! Use at least 8 characters")
    
    # Character variety
    has_upper = any(c.isupper() for c in password)
    has_lower = any(c.islower() for c in password)
    has_digit = any(c.isdigit() for c in password)
    has_special = any(c in SPECIAL for c in password)
    
    if has_upper:
        score += 15
        feedback.append("Contains uppercase letters")
    else:
        warnings.append("Add uppercase letters")
    
    if has_lower:
        score += 10
        feedback.append("Contains lowercase letters")
    else:
        warnings.append("Add lowercase letters")
    
    if has_digit:
        score += 15
        feedback.append("Contains numbers")
    else:
        warnings.append("Add numbers")
    
    if has_special:
        score += 20
        feedback.append("Contains special characters")
    else:
        warnings.append("Add special characters")
    
    # Pattern checks
    if has_sequential(password):
        score -= 15
        warnings.append("Contains sequential characters")
    
    if has_repeated(password):
        score -= 10
        warnings.append("Contains repeated characters")
    
    if check_common_passwords(password):
        score = 0
        warnings.append("This is a commonly used password!")
    
    # Entropy calculation
    entropy = calculate_entropy(password)
    
    # Determine rating
    if score >= 80:
        rating = "Very Strong"
        color = Fore.GREEN if COLORS else ""
    elif score >= 60:
        rating = "Strong"
        color = Fore.BLUE if COLORS else ""
    elif score >= 40:
        rating = "Moderate"
        color = Fore.YELLOW if COLORS else ""
    elif score >= 20:
        rating = "Weak"
        color = Fore.RED if COLORS else ""
    else:
        rating = "Very Weak"
        color = Fore.RED if COLORS else ""
    
    # Crack time estimate
    crack_time = estimate_crack_time(entropy)
    
    return {
        'score': max(0, min(100, score)),
        'rating': rating,
        'entropy': entropy,
        'crack_time': crack_time,
        'feedback': feedback,
        'warnings': warnings,
        'color': color,
        'length': length,
        'variety': {
            'upper': has_upper,
            'lower': has_lower,
            'digit': has_digit,
            'special': has_special
        }
    }


def estimate_crack_time(entropy):
    """Estimate time to crack based on entropy."""
    
    # Assuming 10 billion guesses per second
    guesses_per_second = 10_000_000_000
    combinations = 2 ** entropy
    seconds = combinations / guesses_per_second / 2  # Average case
    
    if seconds < 1:
        return "Instant"
    elif seconds < 60:
        return f"{seconds:.1f} seconds"
    elif seconds < 3600:
        return f"{seconds/60:.1f} minutes"
    elif seconds < 86400:
        return f"{seconds/3600:.1f} hours"
    elif seconds < 31536000:
        return f"{seconds/86400:.1f} days"
    elif seconds < 31536000 * 100:
        return f"{seconds/31536000:.1f} years"
    elif seconds < 31536000 * 1000000:
        return f"{seconds/31536000:.0f} years"
    else:
        return "Centuries+"

# ═══════════════════════════════════════════════════════════════════════════
# OUTPUT FUNCTIONS
# ═══════════════════════════════════════════════════════════════════════════

def print_password(password):
    """Display password with formatting."""
    
    if COLORS:
        print(f"\n{Fore.GREEN}{Style.BRIGHT}{password}{Style.RESET_ALL}")
    else:
        print(f"\n{password}")


def print_strength_bar(score):
    """Print a visual strength bar."""
    
    bar_length = 20
    filled = int(score / 100 * bar_length)
    empty = bar_length - filled
    
    if COLORS:
        if score >= 80:
            bar_color = Fore.GREEN
        elif score >= 60:
            bar_color = Fore.BLUE
        elif score >= 40:
            bar_color = Fore.YELLOW
        else:
            bar_color = Fore.RED
        
        bar = bar_color + '█' * filled + '░' * empty + Style.RESET_ALL
    else:
        bar = '█' * filled + '░' * empty
    
    print(f"  [{bar}] {score}%")


def print_analysis(password):
    """Print complete password analysis."""
    
    result = analyze_password(password)
    
    print_header("Password Analysis")
    
    # Display password
    print_password(password)
    
    # Strength bar
    print_strength_bar(result['score'])
    
    # Rating
    if COLORS:
        print(f"\n{result['color']}  Rating: {result['rating']}{Style.RESET_ALL}")
    else:
        print(f"\n  Rating: {result['rating']}")
    
    # Stats
    print(f"\n  Length: {result['length']} characters")
    print(f"  Entropy: {result['entropy']} bits")
    print(f"  Crack Time: ~{result['crack_time']}")
    
    # Character variety
    print("\n  Character Types:")
    variety = result['variety']
    chars = [
        ('Uppercase', variety['upper']),
        ('Lowercase', variety['lower']),
        ('Numbers', variety['digit']),
        ('Special', variety['special'])
    ]
    
    for name, present in chars:
        status = f"{Fore.GREEN}✓{Style.RESET_ALL}" if present else f"{Fore.RED}✗{Style.RESET_ALL}"
        if COLORS:
            print(f"    {status} {name}")
        else:
            print(f"    {'✓' if present else '✗'} {name}")
    
    # Feedback
    if result['feedback']:
        print("\n  Positives:")
        for item in result['feedback']:
            print_success(item)
    
    # Warnings
    if result['warnings']:
        print("\n  Warnings:")
        for item in result['warnings']:
            print_warning(item)
    
    return result

# ═══════════════════════════════════════════════════════════════════════════
# UTILITY FUNCTIONS
# ═══════════════════════════════════════════════════════════════════════════

def copy_to_clipboard(text):
    """Copy text to clipboard using Termux API."""
    
    try:
        result = subprocess.run(
            ['termux-clipboard-set'],
            input=text.encode(),
            capture_output=True,
            timeout=5
        )
        
        if result.returncode == 0:
            print_success("Password copied to clipboard!")
            return True
        else:
            print_error("Failed to copy to clipboard")
            return False
            
    except FileNotFoundError:
        print_warning("Install Termux:API for clipboard support: pkg install termux-api")
        return False
    except subprocess.TimeoutExpired:
        print_error("Clipboard operation timed out")
        return False


def save_passwords(passwords, label=""):
    """Save passwords to file with timestamp."""
    
    config = load_config()
    filepath = Path(config.get('save_file', '~/passwords.txt')).expanduser()
    
    timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    
    try:
        with open(filepath, 'a') as f:
            f.write(f"\n{'═' * 50}\n")
            f.write(f"Generated: {timestamp}\n")
            if label:
                f.write(f"Label: {label}\n")
            f.write(f"{'═' * 50}\n")
            
            for i, pwd in enumerate(passwords, 1):
                result = analyze_password(pwd)
                f.write(f"\n{i}. {pwd}\n")
                f.write(f"   Strength: {result['rating']} ({result['score']}%)\n")
                f.write(f"   Length: {len(pwd)}\n")
                f.write(f"   Entropy: {result['entropy']} bits\n")
            
            f.write(f"\n{'═' * 50}\n")
        
        print_success(f"Passwords saved to {filepath}")
        return True
        
    except IOError as e:
        print_error(f"Failed to save: {e}")
        return False


def view_history(count=10):
    """View password generation history."""
    
    config = load_config()
    filepath = Path(config.get('save_file', '~/passwords.txt')).expanduser()
    
    if not filepath.exists():
        print_info("No history found")
        return
    
    try:
        with open(filepath, 'r') as f:
            content = f.read()
        
        # Simple display - could be enhanced
        lines = content.split('\n')
        
        print_header("Password History")
        print(f"\nFile: {filepath}")
        print(f"{'─' * 50}\n")
        
        # Show last entries
        for line in lines[-count * 5:]:
            print(line)
            
    except IOError as e:
        print_error(f"Failed to read history: {e}")

# ═══════════════════════════════════════════════════════════════════════════
# MAIN FUNCTION
# ═══════════════════════════════════════════════════════════════════════════

def main():
    """Main function with CLI interface."""
    
    parser = argparse.ArgumentParser(
        description=f'Password Generator Tool v{VERSION} by {AUTHOR}',
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog='''
Examples:
  pgen.py                          Generate default 16-char password
  pgen.py -l 20                    Generate 20-char password
  pgen.py -n 5 -l 12               Generate 5 passwords of 12 chars
  pgen.py --no-special             Without special characters
  pgen.py -p                       Pronounceable password
  pgen.py --passphrase             Generate passphrase
  pgen.py --pin 6                  Generate 6-digit PIN
  pgen.py --check "password123"    Analyze password strength
  pgen.py -c -s                    Generate, copy, and save
        '''
    )
    
    # Generation options
    parser.add_argument('-l', '--length', type=int, 
                        help='Password length (default: 16)')
    parser.add_argument('-n', '--count', type=int, default=1,
                        help='Number of passwords to generate (default: 1)')
    
    # Character type options
    parser.add_argument('--no-upper', action='store_true',
                        help='Exclude uppercase letters')
    parser.add_argument('--no-lower', action='store_true',
                        help='Exclude lowercase letters')
    parser.add_argument('--no-numbers', action='store_true',
                        help='Exclude numbers')
    parser.add_argument('--no-special', action='store_true',
                        help='Exclude special characters')
    parser.add_argument('--exclude-ambiguous', action='store_true',
                        help='Exclude ambiguous characters (il1Lo0O)')
    
    # Alternative password types
    parser.add_argument('-p', '--pronounceable', action='store_true',
                        help='Generate pronounceable password')
    parser.add_argument('--passphrase', action='store_true',
                        help='Generate passphrase')
    parser.add_argument('--passphrase-words', type=int, default=4,
                        help='Number of words in passphrase')
    parser.add_argument('--pin', type=int,
                        help='Generate numeric PIN of specified length')
    
    # Output options
    parser.add_argument('-c', '--copy', action='store_true',
                        help='Copy password to clipboard')
    parser.add_argument('-s', '--save', action='store_true',
                        help='Save password to file')
    parser.add_argument('--label', type=str, default='',
                        help='Label for saved password')
    parser.add_argument('-q', '--quiet', action='store_true',
                        help='Output only the password(s)')
    
    # Analysis
    parser.add_argument('--check', type=str,
                        help='Analyze password strength')
    
    # Utility
    parser.add_argument('--history', action='store_true',
                        help='View password history')
    parser.add_argument('--config', action='store_true',
                        help='Show current configuration')
    parser.add_argument('--version', action='version',
                        version=f'%(prog)s v{VERSION}')
    
    args = parser.parse_args()
    
    # Load config for defaults
    config = load_config()
    
    # Show config
    if args.config:
        print_header("Current Configuration")
        for key, value in config.items():
            print(f"  {key}: {value}")
        return
    
    # View history
    if args.history:
        view_history()
        return
    
    # Analyze password
    if args.check:
        print_analysis(args.check)
        return
    
    # Get length
    length = args.length or config.get('default_length', 16)
    
    # Generate passwords
    passwords = []
    
    for _ in range(args.count):
        if args.pin:
            pwd = generate_pin(args.pin)
        elif args.passphrase:
            pwd = generate_passphrase(args.passphrase_words)
        elif args.pronounceable:
            pwd = generate_pronounceable()
        else:
            pwd = generate_password(
                length=length,
                use_upper=not args.no_upper,
                use_lower=not args.no_lower,
                use_numbers=not args.no_numbers,
                use_special=not args.no_special,
                exclude_ambiguous=args.exclude_ambiguous
            )
        
        if pwd:
            passwords.append(pwd)
    
    if not passwords:
        print_error("No passwords generated")
        sys.exit(1)
    
    # Output
    if args.quiet:
        for pwd in passwords:
            print(pwd)
    else:
        print_header("Generated Passwords")
        
        for i, pwd in enumerate(passwords, 1):
            if args.count > 1:
                print(f"\n--- Password {i} ---")
            print_password(pwd)
            print_strength_bar(analyze_password(pwd)['score'])
    
    # Copy to clipboard
    if args.copy and passwords:
        copy_to_clipboard(passwords[0])
    
    # Save to file
    if args.save and passwords:
        save_passwords(passwords, args.label)


if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        print("\n\nOperation cancelled by user")
        sys.exit(0)
    except Exception as e:
        print_error(f"Unexpected error: {e}")
        sys.exit(1)
```

### Bash Version (pgen.sh)

```bash
#!/bin/bash
#
# ╔═══════════════════════════════════════════════════════════════════════════╗
# ║                    PASSWORD GENERATOR TOOL (Bash)                         ║
# ║                    by T3rmuxk1ng                                          ║
# ╚═══════════════════════════════════════════════════════════════════════════╝
#

# Version
VERSION="2.0.0"
AUTHOR="T3rmuxk1ng"

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
MAGENTA='\033[0;35m'
CYAN='\033[0;36m'
WHITE='\033[1;37m'
NC='\033[0m' # No Color
BOLD='\033[1m'

# Default values
LENGTH=16
COUNT=1
USE_UPPER=true
USE_LOWER=true
USE_NUMBERS=true
USE_SPECIAL=true
EXCLUDE_AMBIGUOUS=false
QUIET=false
SAVE=false
COPY=false
LABEL=""

# Character sets
UPPER="ABCDEFGHIJKLMNOPQRSTUVWXYZ"
LOWER="abcdefghijklmnopqrstuvwxyz"
NUMBERS="0123456789"
SPECIAL='!@#$%^&*()_+-=[]{}|;:,.<>?'
AMBIGUOUS="il1Lo0O"

# Pronounceable components
VOWELS="aeiou"
CONSONANTS="bcdfghjklmnpqrstvwxyz"

# Config file
CONFIG_FILE="$HOME/.pgen_config"
SAVE_FILE="$HOME/passwords.txt"

# ═══════════════════════════════════════════════════════════════════════════
# HELPER FUNCTIONS
# ═══════════════════════════════════════════════════════════════════════════

print_header() {
    echo -e "\n${CYAN}══════════════════════════════════════════════════${NC}"
    echo -e "${CYAN}  $1${NC}"
    echo -e "${CYAN}══════════════════════════════════════════════════${NC}"
}

print_success() {
    echo -e "${GREEN}✓ $1${NC}"
}

print_error() {
    echo -e "${RED}✗ $1${NC}" >&2
}

print_warning() {
    echo -e "${YELLOW}⚠ $1${NC}"
}

print_info() {
    echo -e "${BLUE}ℹ $1${NC}"
}

# ═══════════════════════════════════════════════════════════════════════════
# CONFIGURATION
# ═══════════════════════════════════════════════════════════════════════════

load_config() {
    if [[ -f "$CONFIG_FILE" ]]; then
        source "$CONFIG_FILE"
    fi
}

save_config() {
    cat > "$CONFIG_FILE" << EOF
# Password Generator Configuration
LENGTH=$LENGTH
USE_UPPER=$USE_UPPER
USE_LOWER=$USE_LOWER
USE_NUMBERS=$USE_NUMBERS
USE_SPECIAL=$USE_SPECIAL
SAVE_FILE="$SAVE_FILE"
EOF
    print_success "Configuration saved to $CONFIG_FILE"
}

# ═══════════════════════════════════════════════════════════════════════════
# PASSWORD GENERATION
# ═══════════════════════════════════════════════════════════════════════════

generate_password() {
    local chars=""
    local password=""
    local length=$1
    
    # Build character pool
    $USE_UPPER && chars+="$UPPER"
    $USE_LOWER && chars+="$LOWER"
    $USE_NUMBERS && chars+="$NUMBERS"
    $USE_SPECIAL && chars+="$SPECIAL"
    
    # Remove ambiguous characters if requested
    if $EXCLUDE_AMBIGUOUS; then
        chars=$(echo "$chars" | tr -d "$AMBIGUOUS")
    fi
    
    if [[ -z "$chars" ]]; then
        print_error "At least one character type must be selected!"
        return 1
    fi
    
    # Generate password using /dev/urandom
    password=$(tr -dc "$chars" < /dev/urandom | head -c "$length")
    
    echo "$password"
}

generate_pronounceable() {
    local syllables=${1:-4}
    local password=""
    
    for ((i=0; i<syllables; i++)); do
        # Get random consonant and vowel
        local c=$(echo "$CONSONANTS" | fold -w1 | shuf -n1)
        local v=$(echo "$VOWELS" | fold -w1 | shuf -n1)
        
        if [[ $i -eq 0 ]]; then
            password+="${c^^}$v"  # Capitalize first
        else
            password+="$c$v"
        fi
    done
    
    # Add random number
    password+=$((RANDOM % 100))
    
    echo "$password"
}

generate_pin() {
    local length=${1:-6}
    local pin=""
    
    for ((i=0; i<length; i++)); do
        pin+=$((RANDOM % 10))
    done
    
    echo "$pin"
}

# ═══════════════════════════════════════════════════════════════════════════
# PASSWORD ANALYSIS
# ═══════════════════════════════════════════════════════════════════════════

check_strength() {
    local password="$1"
    local score=0
    local length=${#password}
    
    # Length score
    if [[ $length -ge 20 ]]; then
        ((score+=30))
    elif [[ $length -ge 16 ]]; then
        ((score+=25))
    elif [[ $length -ge 12 ]]; then
        ((score+=20))
    elif [[ $length -ge 8 ]]; then
        ((score+=10))
    else
        ((score+=5))
    fi
    
    # Character variety
    [[ "$password" =~ [A-Z] ]] && ((score+=15))
    [[ "$password" =~ [a-z] ]] && ((score+=10))
    [[ "$password" =~ [0-9] ]] && ((score+=15))
    [[ "$password" =~ [^a-zA-Z0-9] ]] && ((score+=20))
    
    # Deduct for patterns
    # (simplified - full version would be more comprehensive)
    
    # Ensure score is in valid range
    [[ $score -gt 100 ]] && score=100
    [[ $score -lt 0 ]] && score=0
    
    # Rating
    if [[ $score -ge 80 ]]; then
        echo -e "${GREEN}Very Strong${NC} (Score: $score)"
    elif [[ $score -ge 60 ]]; then
        echo -e "${BLUE}Strong${NC} (Score: $score)"
    elif [[ $score -ge 40 ]]; then
        echo -e "${YELLOW}Moderate${NC} (Score: $score)"
    else
        echo -e "${RED}Weak${NC} (Score: $score)"
    fi
}

print_strength_bar() {
    local score=$1
    local bar_length=20
    local filled=$((score * bar_length / 100))
    local empty=$((bar_length - filled))
    
    local bar_color
    if [[ $score -ge 80 ]]; then
        bar_color=$GREEN
    elif [[ $score -ge 60 ]]; then
        bar_color=$BLUE
    elif [[ $score -ge 40 ]]; then
        bar_color=$YELLOW
    else
        bar_color=$RED
    fi
    
    printf "  [${bar_color}"
    printf '█%.0s' $(seq 1 $filled 2>/dev/null)
    printf "${NC}"
    printf '░%.0s' $(seq 1 $empty 2>/dev/null)
    printf "] ${score}%\n"
}

# ═══════════════════════════════════════════════════════════════════════════
# UTILITY FUNCTIONS
# ═══════════════════════════════════════════════════════════════════════════

copy_clipboard() {
    if command -v termux-clipboard-set &> /dev/null; then
        echo -n "$1" | termux-clipboard-set
        print_success "Password copied to clipboard!"
    else
        print_warning "Install Termux:API for clipboard support: pkg install termux-api"
        return 1
    fi
}

save_passwords() {
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    
    {
        echo ""
        echo "══════════════════════════════════════════════════"
        echo "Generated: $timestamp"
        [[ -n "$LABEL" ]] && echo "Label: $LABEL"
        echo "══════════════════════════════════════════════════"
        
        for pwd in "$@"; do
            echo ""
            echo "$pwd"
            echo "  Strength: $(check_strength "$pwd" | sed 's/\x1b\[[0-9;]*m//g')"
            echo "  Length: ${#pwd}"
        done
        
        echo "══════════════════════════════════════════════════"
    } >> "$SAVE_FILE"
    
    print_success "Passwords saved to $SAVE_FILE"
}

view_history() {
    if [[ ! -f "$SAVE_FILE" ]]; then
        print_info "No history found"
        return
    fi
    
    print_header "Password History"
    echo -e "File: $SAVE_FILE"
    echo -e "──────────────────────────────────────────────────\n"
    tail -50 "$SAVE_FILE"
}

# ═══════════════════════════════════════════════════════════════════════════
# HELP
# ═══════════════════════════════════════════════════════════════════════════

show_help() {
    cat << EOF
${CYAN}Password Generator Tool v${VERSION} by ${AUTHOR}${NC}

Usage: pgen.sh [OPTIONS]

Options:
  -l LENGTH          Password length (default: 16)
  -n COUNT           Number of passwords (default: 1)
  --no-upper         Exclude uppercase letters
  --no-lower         Exclude lowercase letters
  --no-numbers       Exclude numbers
  --no-special       Exclude special characters
  --exclude-ambig    Exclude ambiguous characters (il1Lo0O)
  -p, --pronounce    Generate pronounceable password
  --pin LENGTH       Generate numeric PIN
  -c, --copy         Copy to clipboard
  -s, --save         Save to file
  --label TEXT       Label for saved password
  -q, --quiet        Output only password(s)
  --history          View password history
  --config           Save current settings as default
  -h, --help         Show this help
  --version          Show version

Examples:
  pgen.sh                         # Default 16-char password
  pgen.sh -l 20 -n 5              # 5 passwords of 20 chars
  pgen.sh --no-special -l 12      # 12 chars without special
  pgen.sh -p                      # Pronounceable password
  pgen.sh --pin 6                 # 6-digit PIN
  pgen.sh -c -s -l 24             # Generate, copy, and save

EOF
}

# ═══════════════════════════════════════════════════════════════════════════
# MAIN
# ═══════════════════════════════════════════════════════════════════════════

# Load config
load_config

# Parse arguments
while [[ $# -gt 0 ]]; do
    case $1 in
        -l|--length)
            LENGTH="$2"
            shift 2
            ;;
        -n|--count)
            COUNT="$2"
            shift 2
            ;;
        --no-upper)
            USE_UPPER=false
            shift
            ;;
        --no-lower)
            USE_LOWER=false
            shift
            ;;
        --no-numbers)
            USE_NUMBERS=false
            shift
            ;;
        --no-special)
            USE_SPECIAL=false
            shift
            ;;
        --exclude-ambig|--exclude-ambiguous)
            EXCLUDE_AMBIGUOUS=true
            shift
            ;;
        -p|--pronounce|--pronounceable)
            PRONOUNCEABLE=true
            shift
            ;;
        --pin)
            PIN_LENGTH="$2"
            shift 2
            ;;
        -c|--copy)
            COPY=true
            shift
            ;;
        -s|--save)
            SAVE=true
            shift
            ;;
        --label)
            LABEL="$2"
            shift 2
            ;;
        -q|--quiet)
            QUIET=true
            shift
            ;;
        --history)
            view_history
            exit 0
            ;;
        --config)
            save_config
            exit 0
            ;;
        -h|--help)
            show_help
            exit 0
            ;;
        --version)
            echo "pgen.sh version $VERSION by $AUTHOR"
            exit 0
            ;;
        --check)
            # Analyze password
            print_header "Password Analysis"
            echo -e "\n${GREEN}${BOLD}$2${NC}"
            print_strength_bar "$(check_strength "$2" | grep -oP '\d+')"
            check_strength "$2"
            exit 0
            ;;
        *)
            print_error "Unknown option: $1"
            show_help
            exit 1
            ;;
    esac
done

# Generate passwords
passwords=()

for ((i=0; i<COUNT; i++)); do
    if [[ -n "$PIN_LENGTH" ]]; then
        pwd=$(generate_pin "$PIN_LENGTH")
    elif [[ "$PRONOUNCEABLE" == "true" ]]; then
        pwd=$(generate_pronounceable 4)
    else
        pwd=$(generate_password "$LENGTH")
    fi
    
    if [[ -n "$pwd" ]]; then
        passwords+=("$pwd")
    fi
done

# Output
if $QUIET; then
    printf '%s\n' "${passwords[@]}"
else
    print_header "Generated Passwords"
    
    for i in "${!passwords[@]}"; do
        if [[ ${#passwords[@]} -gt 1 ]]; then
            echo -e "\n--- Password $((i+1)) ---"
        fi
        echo -e "\n${GREEN}${BOLD}${passwords[$i]}${NC}"
        print_strength_bar "$(check_strength "${passwords[$i]}" | grep -oP '\d+')"
        check_strength "${passwords[$i]}"
    done
fi

# Copy to clipboard
if $COPY && [[ ${#passwords[@]} -gt 0 ]]; then
    copy_clipboard "${passwords[0]}"
fi

# Save to file
if $SAVE && [[ ${#passwords[@]} -gt 0 ]]; then
    save_passwords "${passwords[@]}"
fi
```

---

## 📋 PRACTICE EXERCISES

### Exercise 1: Basic Password Generation

```bash
# Task: Generate different types of passwords

# 1. Generate a 16-character password
python pgen.py

# 2. Generate a 32-character password
python pgen.py -l 32

# 3. Generate 10 passwords at once
python pgen.py -n 10

# 4. Generate password without special characters
python pgen.py --no-special

# 5. Generate password with only letters
python pgen.py --no-numbers --no-special

# Expected: Various password outputs with strength analysis
```

### Exercise 2: Password Strength Analysis

```bash
# Task: Analyze different passwords

# 1. Check a weak password
python pgen.py --check "password123"

# 2. Check a medium password
python pgen.py --check "MyP@ssw0rd"

# 3. Check a strong password
python pgen.py --check "Kx9#mP2\$vL7@nQ4!wE8&"

# 4. Check your own password (be careful!)
python pgen.py --check "your_password_here"

# Note: Note down the entropy and crack time for each
```

### Exercise 3: Alternative Password Types

```bash
# Task: Generate different password formats

# 1. Generate pronounceable password
python pgen.py -p

# 2. Generate passphrase
python pgen.py --passphrase

# 3. Generate 8-digit PIN
python pgen.py --pin 8

# 4. Generate 5-word passphrase
python pgen.py --passphrase --passphrase-words 5

# Expected: Various password formats
```

### Exercise 4: File Operations

```bash
# Task: Use file save and history features

# 1. Generate and save password
python pgen.py -s --label "Test Account"

# 2. Generate multiple passwords and save
python pgen.py -n 5 -s --label "Batch Generation"

# 3. View history
python pgen.py --history

# 4. Check the saved file
cat ~/passwords.txt

# Expected: Passwords saved with timestamps and labels
```

### Exercise 5: Bash Version Practice

```bash
# Task: Use the Bash version

# 1. Make executable
chmod +x pgen.sh

# 2. Generate default password
./pgen.sh

# 3. Generate 5 passwords of 20 characters
./pgen.sh -l 20 -n 5

# 4. Generate pronounceable password
./pgen.sh -p

# 5. Generate PIN
./pgen.sh --pin 6

# 6. Quiet mode (for scripting)
./pgen.sh -q -l 16

# 7. Analyze password
./pgen.sh --check "MyTestP@ss123"

# Expected: Same functionality as Python version
```

### Exercise 6: Integration with Other Scripts

```bash
# Task: Integrate password generator in other scripts

# 1. Create a user creation script
cat > create_user.sh << 'EOF'
#!/bin/bash

USERNAME=$1
if [[ -z "$USERNAME" ]]; then
    echo "Usage: ./create_user.sh <username>"
    exit 1
fi

# Generate password
PASSWORD=$(./pgen.sh -q -l 16)

echo "Creating user: $USERNAME"
echo "Generated password: $PASSWORD"

# Save to file
echo "$USERNAME:$PASSWORD" >> users.txt

echo "User credentials saved to users.txt"
EOF

chmod +x create_user.sh
./create_user.sh testuser

# 2. Use in Python script
cat > auto_password.py << 'EOF'
import subprocess
import sys

def generate_password(length=16):
    result = subprocess.run(
        ['python', 'pgen.py', '-q', '-l', str(length)],
        capture_output=True,
        text=True
    )
    return result.stdout.strip()

if __name__ == "__main__":
    pwd = generate_password(20)
    print(f"Generated: {pwd}")
EOF

python auto_password.py
```

### Exercise 7: Customization Challenge

```python
# Task: Add custom feature to the password generator

# Challenge 1: Add a feature to generate passwords based on a pattern
# Example pattern: "LLNNSSLL" (L=letter, N=number, S=special)
# Output: "AB12!@CD"

def generate_pattern_password(pattern):
    """
    Generate password based on pattern.
    L/l = letter (upper/lower)
    N/n = number
    S/s = special character
    A/a = any character
    """
    # Your implementation here
    pass

# Challenge 2: Add password expiration reminder
def set_password_expiry(password, days=90):
    """Store password with expiry date"""
    # Your implementation here
    pass

# Challenge 3: Add password breach check (using API)
def check_breach(password):
    """Check if password has been in data breach"""
    # Hint: Use haveibeenpwned API
    # Your implementation here
    pass

# Test your implementations
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Module 'secrets' not found"

```bash
# Cause: Old Python version (secrets requires Python 3.6+)

# Solution 1: Check Python version
python --version

# Solution 2: Update Python
pkg upgrade python

# Solution 3: If stuck on old Python, use random instead
# Edit pgen.py and replace secrets with random
# Note: This is less secure!
```

### Problem 2: "Permission denied" when running Bash script

```bash
# Cause: Script not executable

# Solution: Add execute permission
chmod +x pgen.sh

# Alternative: Run with bash directly
bash pgen.sh
```

### Problem 3: Clipboard not working

```bash
# Cause: Termux:API not installed

# Solution 1: Install Termux:API app from F-Droid
# Then install the CLI package:
pkg install termux-api

# Solution 2: Check if termux-clipboard-set exists
which termux-clipboard-set

# Solution 3: Restart Termux after installing
```

### Problem 4: Colors not showing

```bash
# Cause: colorama not installed or terminal doesn't support colors

# Solution 1: Install colorama
pip install colorama

# Solution 2: Use without colors (tool works fine without)
# The tool automatically detects and falls back

# Solution 3: For Bash, check if terminal supports colors
echo $TERM
```

### Problem 5: "No such file or directory" when saving

```bash
# Cause: Parent directory doesn't exist or permission issue

# Solution 1: Create directory
mkdir -p ~/projects/password-generator

# Solution 2: Check current directory
pwd

# Solution 3: Use absolute path for save file
# Edit config or use:
python pgen.py -s --save-file /sdcard/passwords.txt
```

### Problem 6: Weak passwords generated

```bash
# Cause: Limited character set or short length

# Solution 1: Use longer passwords
python pgen.py -l 24

# Solution 2: Enable all character types (default)
python pgen.py

# Solution 3: Check your configuration
python pgen.py --config

# Solution 4: Exclude ambiguous but include all types
python pgen.py --exclude-ambiguous -l 20
```

### Problem 7: Script runs slowly

```bash
# Cause: Slow random generation or I/O issues

# Solution 1: For bulk generation, use quiet mode
python pgen.py -n 100 -q > passwords.txt

# Solution 2: For Bash, use /dev/urandom (already implemented)
# The script already uses /dev/urandom which is fast

# Solution 3: Avoid unnecessary analysis for bulk
# Use -q flag to skip strength analysis
```

### Problem 8: "command not found: python"

```bash
# Cause: Python not installed or not in PATH

# Solution 1: Install Python
pkg install python

# Solution 2: Use python3 explicitly
python3 pgen.py

# Solution 3: Check PATH
echo $PATH
# Should include /data/data/com.termux/files/usr/bin
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Terminal Background]             │
│                                    │
│   🔐 PASSWORD GENERATOR            │
│   Python + Bash Project            │
│                                    │
│   ✓ Strong Passwords               │
│   ✓ Strength Checker               │
│   ✓ Termux Ready                   │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Before/After Style**
```
┌────────────────────────────────────┐
│  ❌ password123      ✅ Kx9#mP2$vL │
│  ─────────────────────────────────│
│  Weak: Cracked in 1s  Strong: 100y │
│                                    │
│  PASSWORD GENERATOR TOOL           │
│  Build Your Own Security Tool      │
│                                    │
│  Chapter 51 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Code Focus**
```
┌────────────────────────────────────┐
│  [Code snippet background]         │
│                                    │
│  def generate_password():          │
│      return secrets.choice()       │
│                                    │
│  🛠️ BUILD A PASSWORD GENERATOR     │
│  🔒 Python + Bash Implementation   │
│                                    │
│  Termux Project #1                 │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔐 Termux Full Course - Chapter 51: Password Generator Tool | Python + Bash Project

🔥 In this video you'll learn:
• Password security fundamentals
• Build a complete password generator
• Python implementation with multiple features
• Bash script version
• Password strength analysis
• Termux API integration for clipboard

⏱️ Timestamps:
0:00 - Introduction
1:00 - Project Overview
4:00 - Password Security Basics
7:00 - Python Implementation
14:00 - Bash Implementation
18:00 - Testing the Tool
21:00 - Advanced Features
23:00 - Summary & Next Steps

💻 Commands from this video:
mkdir -p ~/projects/password-generator
cd ~/projects/password-generator
pip install colorama
python pgen.py -l 20
python pgen.py --check "password123"

📥 Source Code:
GitHub: [LINK]

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #PasswordGenerator #Python #Bash #CyberSecurity #T3rmuxk1ng #TermuxCourse #EthicalHacking #SecurityTools

---
⚠️ Disclaimer: This video is for educational purposes. Always use strong, unique passwords and consider using a password manager for better security.
```

### Tags List

```
termux, password generator, python project, bash script,
termux project, cybersecurity, password security, strong password,
password strength, termux tutorial, ethical hacking, security tools,
python programming, bash scripting, t3rmuxk1ng, termux course,
mobile development, android hacking, learn python, termux python,
password cracker, security programming, command line tools,
entropy calculation, random password, pronounceable password
```

### Hashtags

```
#Termux #PasswordGenerator #Python #Bash #CyberSecurity 
#TermuxCourse #T3rmuxk1ng #SecurityTools #EthicalHacking 
#LearnPython #PasswordSecurity #Programming #MobileHacking
#TermuxTutorial #CommandLine #Security #Coding
```

---

## 📚 ADDITIONAL RESOURCES

### Password Security References

| Resource | Link |
|----------|------|
| NIST Password Guidelines | https://pages.nist.gov/800-63-3/ |
| Have I Been Pwned | https://haveibeenpwned.com/ |
| OWASP Password Cheat Sheet | https://cheatsheetseries.owasp.org/ |
| Password Strength Wiki | https://en.wikipedia.org/wiki/Password_strength |

### Python Documentation

| Resource | Link |
|----------|------|
| secrets module | https://docs.python.org/3/library/secrets.html |
| argparse module | https://docs.python.org/3/library/argparse.html |
| colorama package | https://pypi.org/project/colorama/ |

### Termux-Specific

| Resource | Description |
|----------|-------------|
| termux-clipboard-set | Clipboard API command |
| termux-api package | Required for clipboard features |
| Termux Wiki | https://wiki.termux.com/ |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 52, verify:

- [ ] Created project directory structure
- [ ] Installed Python and required packages
- [ ] Python version (pgen.py) working correctly
- [ ] Generated various password types (random, pronounceable, PIN)
- [ ] Password strength analysis working
- [ ] File save feature tested
- [ ] Bash version (pgen.sh) working correctly
- [ ] Clipboard integration working (with Termux:API)
- [ ] Understood password security concepts
- [ ] Completed all practice exercises

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 52: Project 2 - Phone Info Extractor**

- Device information extraction
- System details collection
- Network info gathering
- Hardware information
- Battery and storage stats
- Export and reporting features

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
