# Chapter 22: Termux API - Contacts & SMS

> **Module:** 4 - APIs  
> **Chapter:** 22 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed Contacts & SMS API usage |
| Commands Reference | All commands covered in chapter |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 22
Title: Termux API - Contacts & SMS | Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum seekhenge ek bahut hi powerful aur practical topic - Contacts aur 
SMS management using Termux API.

Socho, aap apne phone ke contacts ko programmatically access kar sakte ho,
SMS bhej sakte ho, receive kar sakte ho, call log dekh sakte ho - sab kuch 
command line se ya scripts ke through!

Ye features automation ke liye game changer hain. Bulk SMS bhejna ho, 
auto-reply setup karna ho, contact backup lena ho - sab kuch possible hai 
Termux ke through.

To chaliye shuru karte hain! Like, subscribe aur notification bell on 
karein, aur video start karte hain.

---

[SECTION 1: PREREQUISITES & SETUP - 0:45 to 2:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle, prerequisites check karte hain:

✓ Termux installed (F-Droid se)
✓ Termux:API app installed
✓ termux-api package installed
✓ Permissions granted

Agar Termux:API app nahi hai, to F-Droid se install karein:
Search "Termux:API" aur install karein.

Phir Termux mein ye command run karein:

    pkg install termux-api -y

Ab permissions ki baat. Contacts aur SMS access ke liye Android permissions 
chahiye. Termux automatically maangega jab aap pehli baar contact ya SMS 
command run karoge.

Android 12+ mein additional permissions chahiye:
- Contacts permission
- SMS permission  
- Phone permission (call log ke liye)

Ye permissions Settings > Apps > Termux > Permissions mein manually bhi 
de sakte ho.

Verify karte hain ki API kaam kar rahi hai:

    termux-contact-list | head -5

Agar contacts list dikh rahi hai, to sab theek hai!

---

[SECTION 2: CONTACT LIST API - 2:30 to 5:30]
─────────────────────────────────────────────────────────────────────────────

Pehla command - contacts access karna:

    termux-contact-list

Ye command aapke phone ke saare contacts ko JSON format mein return karti hai.

Output kuch aisa dikhega:

{
  "name": "Rahul Sharma",
  "number": "+919876543210"
},
{
  "name": "Priya Singh",
  "number": "+919123456789"
}

JSON format hai, ye data hai - machine readable. Isse process karna easy 
hai programmatically.

Contacts count karna ho to:

    termux-contact-list | jq length

JQ ek JSON processor hai. Pehle install karein:

    pkg install jq -y

Specific contact search karna ho:

    termux-contact-list | jq '.[] | select(.name | contains("Rahul"))'

Ya number se search:

    termux-contact-list | jq '.[] | select(.number | contains("9876"))'

Contacts ko simple list format mein dekhna ho:

    termux-contact-list | jq -r '.[] | "\(.name): \(.number)"'

CSV format mein export:

    termux-contact-list | jq -r '.[] | "\(.name),\(.number)"' > contacts.csv

Ab aapke contacts ka backup ready hai!

---

[SECTION 3: SMS LIST API - 5:30 to 8:30]
─────────────────────────────────────────────────────────────────────────────

Ab SMS access karte hain. SMS read karne ke liye:

    termux-sms-list

Default mein last 10 SMS dikhata hai. Arguments se control kar sakte ho:

Last 20 SMS:

    termux-sms-list -l 20

Specific number ke SMS:

    termux-sms-list -n "+919876543210"

All SMS (limit remove):

    termux-sms-list --limit 1000

Output JSON format mein hota hai:

{
  "threadid": 5,
  "type": "inbox",
  "read": 1,
  "sender": "+919876543210",
  "number": "+919876543210",
  "received": 1698765432000,
  "body": "Hello, kya haal hai?"
}

Fields explain karta hoon:
- threadid: Conversation thread ID
- type: "inbox" (received) ya "sent" 
- read: 1 = read, 0 = unread
- sender/number: Phone number
- received: Timestamp (milliseconds)
- body: SMS content

Sent messages dekhna ho:

    termux-sms-list -t sent

Received messages:

    termux-sms-list -t inbox

Unread messages only:

    termux-sms-list | jq '.[] | select(.read == 0)'

Specific date ke baad ke SMS:

    termux-sms-list -d 2024-01-01

---

[SECTION 4: SMS SEND API - 8:30 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab SMS bhejna seekhte hain. Command:

    termux-sms-send -n "+919876543210" "Hello from Termux!"

Parameters:
- -n: Number (required)
- Message text in quotes

Multiple numbers pe bhejna ho:

    termux-sms-send -n "+919876543210" -n "+919123456789" "Group message"

File se message bhejna:

    termux-sms-send -n "+919876543210" < message.txt

Emoji bhejna ho:

    termux-sms-send -n "+919876543210" "Hello! 👋 Testing SMS from Termux"

Script se dynamic message:

    NAME="Rahul"
    MSG="Hello $NAME, ye Termux se test SMS hai!"
    termux-sms-send -n "+919876543210" "$MSG"

Important: Android ke according background SMS restrictions hain. 
Foreground app hona chahiye ya user interaction chahiye Android 10+ 
pe. Isliye automation ke liye extra setup chahiye.

---

[SECTION 5: CALL LOG API - 11:00 to 13:00]
─────────────────────────────────────────────────────────────────────────────

Call log access karte hain:

    termux-call-log

Default last 10 calls dikhata hai.

More records:

    termux-call-log -l 50

Output format:

{
  "name": "Rahul Sharma",
  "phone_number": "+919876543210",
  "duration": 120,
  "type": "INCOMING",
  "date": 1698765432000
}

Fields:
- name: Contact name (agar saved hai)
- phone_number: Number
- duration: Call duration in seconds
- type: INCOMING, OUTGOING, MISSED
- date: Timestamp

Missed calls filter:

    termux-call-log | jq '.[] | select(.type == "MISSED")'

Long calls (>5 minutes):

    termux-call-log | jq '.[] | select(.duration > 300)'

Specific number ke calls:

    termux-call-log | jq '.[] | select(.phone_number | contains("9876"))'

Call stats calculate karna:

    termux-call-log | jq '[.[] | .duration] | add'

Ye total call time dega seconds mein.

---

[SECTION 6: MAKING CALLS - 13:00 to 14:30]
─────────────────────────────────────────────────────────────────────────────

Phone call initiate karna:

    termux-telephony-call +919876543210

Ye command phone dialer open karega number ke saath. 
Auto-dial nahi hota - user ko call button press karna padta hai.

Ye security feature hai Android ka - background calls block karta hai.

Script mein use karna:

    # Quick call script
    echo "Select contact to call:"
    termux-contact-list | jq -r '.[] | "\(.name): \(.number)"' | nl
    read -p "Enter number: " choice
    NUMBER=$(termux-contact-list | jq -r ".[$choice-1].number")
    termux-telephony-call "$NUMBER"

---

[SECTION 7: PRACTICAL SCRIPTS - 14:30 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch practical scripts banate hain.

[SCRIPT 1: Contact Backup]

    #!/bin/bash
    # contact-backup.sh
    # Contacts ka complete backup with timestamp
    
    BACKUP_DIR="$HOME/backups"
    TIMESTAMP=$(date +%Y%m%d_%H%M%S)
    
    mkdir -p "$BACKUP_DIR"
    
    # JSON backup
    termux-contact-list > "$BACKUP_DIR/contacts_$TIMESTAMP.json"
    
    # CSV backup
    echo "Name,Number" > "$BACKUP_DIR/contacts_$TIMESTAMP.csv"
    termux-contact-list | jq -r '.[] | "\(.name),\(.number)"' >> "$BACKUP_DIR/contacts_$TIMESTAMP.csv"
    
    echo "Backup created in $BACKUP_DIR"
    ls -la "$BACKUP_DIR"

[SCRIPT 2: Bulk SMS Sender]

    #!/bin/bash
    # bulk-sms.sh
    # Multiple contacts ko ek saath SMS bhejna
    
    MESSAGE="$1"
    
    if [ -z "$MESSAGE" ]; then
        echo "Usage: ./bulk-sms.sh 'Your message'"
        exit 1
    fi
    
    echo "Select contacts:"
    termux-contact-list | jq -r '.[] | .name' | nl
    
    echo "Enter numbers (space separated): "
    read -a INDICES
    
    for i in "${INDICES[@]}"; do
        NUMBER=$(termux-contact-list | jq -r ".[$i-1].number")
        NAME=$(termux-contact-list | jq -r ".[$i-1].name")
        echo "Sending to $NAME ($NUMBER)..."
        termux-sms-send -n "$NUMBER" "$MESSAGE"
        sleep 2  # Delay to avoid blocking
    done
    
    echo "Bulk SMS sent!"

[SCRIPT 3: Auto-Reply SMS]

    #!/bin/bash
    # auto-reply.sh
    # Unread SMS ka automatic reply
    
    while true; do
        UNREAD=$(termux-sms-list -l 10 | jq '[.[] | select(.read == 0)]')
        
        echo "$UNREAD" | jq -c '.[]' | while read -r sms; do
            SENDER=$(echo "$sms" | jq -r '.sender')
            BODY=$(echo "$sms" | jq -r '.body')
            
            # Auto-reply message
            REPLY="Thanks for your message. I'm currently busy. Will reply soon!"
            
            echo "Auto-replying to $SENDER..."
            termux-sms-send -n "$SENDER" "$REPLY"
        done
        
        sleep 30  # Check every 30 seconds
    done

[SCRIPT 4: Contact Search Tool]

    #!/bin/bash
    # contact-search.sh
    # Interactive contact search
    
    echo "=== Contact Search Tool ==="
    read -p "Enter search term: " QUERY
    
    RESULTS=$(termux-contact-list | jq -r ".[] | select(.name | contains(\"$QUERY\") or .number | contains(\"$QUERY\")) | \"\(.name) - \(.number)\"")
    
    if [ -z "$RESULTS" ]; then
        echo "No contacts found."
    else
        echo "Results:"
        echo "$RESULTS"
        
        read -p "Send SMS? (y/n): " choice
        if [ "$choice" = "y" ]; then
            read -p "Enter message: " MSG
            NUMBER=$(termux-contact-list | jq -r ".[] | select(.name | contains(\"$QUERY\")) | .number" | head -1)
            termux-sms-send -n "$NUMBER" "$MSG"
            echo "SMS sent!"
        fi
    fi

[SCRIPT 5: SMS Backup]

    #!/bin/bash
    # sms-backup.sh
    # Complete SMS backup
    
    BACKUP_DIR="$HOME/sms-backups"
    TIMESTAMP=$(date +%Y%m%d)
    
    mkdir -p "$BACKUP_DIR"
    
    # All SMS backup
    termux-sms-list --limit 10000 > "$BACKUP_DIR/sms_$TIMESTAMP.json"
    
    # Count
    COUNT=$(termux-sms-list | jq length)
    
    echo "SMS Backup Complete!"
    echo "Total SMS backed up: $COUNT"
    echo "Location: $BACKUP_DIR/sms_$TIMESTAMP.json"

---

[SECTION 8: PYTHON INTEGRATION - 18:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Python se Contacts aur SMS handle karna:

    import subprocess
    import json

    # Get contacts
    def get_contacts():
        result = subprocess.run(['termux-contact-list'], capture_output=True, text=True)
        contacts = json.loads(result.stdout)
        return contacts

    # Search contact
    def search_contact(name):
        contacts = get_contacts()
        for contact in contacts:
            if name.lower() in contact['name'].lower():
                return contact
        return None

    # Send SMS
    def send_sms(number, message):
        subprocess.run(['termux-sms-send', '-n', number, message])
        print(f"SMS sent to {number}")

    # Get SMS list
    def get_sms(limit=10):
        result = subprocess.run(['termux-sms-list', '-l', str(limit)], capture_output=True, text=True)
        messages = json.loads(result.stdout)
        return messages

    # Example usage
    if __name__ == "__main__":
        # List contacts
        contacts = get_contacts()
        for c in contacts[:5]:
            print(f"{c['name']}: {c['number']}")
        
        # Send SMS
        send_sms("+919876543210", "Hello from Python!")

Advanced Python script - SMS Dashboard:

    import subprocess
    import json
    from datetime import datetime

    class SMSManager:
        def __init__(self):
            pass
        
        def run_command(self, cmd):
            result = subprocess.run(cmd, capture_output=True, text=True, shell=True)
            return result.stdout
        
        def get_stats(self):
            contacts = len(json.loads(self.run_command('termux-contact-list')))
            sms_count = len(json.loads(self.run_command('termux-sms-list -l 100')))
            calls = len(json.loads(self.run_command('termux-call-log -l 100')))
            
            return {
                'contacts': contacts,
                'sms_last_100': sms_count,
                'calls_last_100': calls
            }
        
        def show_dashboard(self):
            stats = self.get_stats()
            print("=" * 40)
            print("SMS & Contacts Dashboard")
            print("=" * 40)
            print(f"Total Contacts: {stats['contacts']}")
            print(f"Recent SMS: {stats['sms_last_100']}")
            print(f"Recent Calls: {stats['calls_last_100']}")
            print("=" * 40)

    # Run
    manager = SMSManager()
    manager.show_dashboard()

---

[SECTION 9: PRIVACY & PERMISSIONS - 20:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Security aur privacy important hai!

Permissions:
- Contacts access sensitive data hai
- SMS can send messages (cost involved)
- Call log reveals communication patterns

Best Practices:

1. Data Handling:
   - Encrypted backups use karein
   - Sensitive data store na karein plain text mein
   - Old backups delete karein regularly

2. Script Security:
   - API keys hardcode na karein
   - User confirmation lo bulk operations se pehle
   - Rate limiting use karein

3. Android Restrictions:
   - Android 10+ background SMS restrict karta hai
   - SMS_SEND permission chahiye
   - Default SMS app banne ki requirement kuch features ke liye

4. Ethical Use:
   - Sirf apne device pe use karein
   - Doosron ke contacts/SMS access na karein bina permission
   - Bulk SMS marketing ke liye use na karein

Permission check:

    # Check if Termux has SMS permission
    termux-sms-list -l 1 > /dev/null 2>&1 && echo "SMS OK" || echo "No SMS permission"

    # Check contacts permission
    termux-contact-list > /dev/null 2>&1 && echo "Contacts OK" || echo "No Contacts permission"

---

[SECTION 10: SUMMARY - 21:30 to 23:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 22 complete! Let's summarize:

✅ termux-contact-list - Contacts access JSON format mein
✅ termux-sms-list - SMS read with filters
✅ termux-sms-send - SMS bhejna
✅ termux-call-log - Call history access
✅ termux-telephony-call - Call initiate karna
✅ Python integration - Programming approach
✅ Practical scripts - Backup, Bulk SMS, Auto-reply
✅ Privacy considerations - Security best practices

Key Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 22 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ termux-contact-list              │ List all contacts (JSON)             │
│ termux-sms-list                  │ List recent SMS messages             │
│ termux-sms-list -n "number"      │ SMS from specific number             │
│ termux-sms-send -n "num" "msg"   │ Send SMS to number                   │
│ termux-call-log                  │ View call history                    │
│ termux-telephony-call number     │ Initiate phone call                  │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 23 mein hum seekhenge:
- Termux Clipboard API
- Share functionality
- Data sharing between apps
- File sharing scripts

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 23!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Contacts API Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX CONTACTS API FLOW                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────┐        ┌─────────────────┐                        │
│   │ termux-contact- │        │  Termux:API     │                        │
│   │ list command    │───────▶│  App (Java)     │                        │
│   └─────────────────┘        └────────┬────────┘                        │
│                                       │                                  │
│                                       ▼                                  │
│                          ┌────────────────────┐                         │
│                          │ Android Contacts   │                         │
│                          │ ContentProvider    │                         │
│                          └────────┬───────────┘                         │
│                                   │                                      │
│                                   ▼                                      │
│                          ┌────────────────────┐                         │
│                          │ Contacts Database  │                         │
│                          │ (SQLite)           │                         │
│                          └────────────────────┘                         │
│                                                                          │
│   Output Format:                                                         │
│   [                                                                      │
│     {"name": "Contact Name", "number": "+91XXXXXXXXXX"},                │
│     {"name": "Another", "number": "+91YYYYYYYYYY"}                      │
│   ]                                                                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. SMS API Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX SMS API FLOW                                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────┐        ┌─────────────────┐                        │
│   │ termux-sms-send │───────▶│  Termux:API     │                        │
│   │ termux-sms-list │        │  App (Java)     │                        │
│   └─────────────────┘        └────────┬────────┘                        │
│                                       │                                  │
│                      ┌────────────────┴────────────────┐                │
│                      ▼                                 ▼                │
│            ┌─────────────────┐              ┌─────────────────┐        │
│            │ SMS Content     │              │ SMS Manager     │        │
│            │ Provider        │              │ (Send SMS)      │        │
│            │ (Read SMS)      │              │                 │        │
│            └────────┬────────┘              └────────┬────────┘        │
│                     │                                │                  │
│                     ▼                                ▼                  │
│            ┌─────────────────────────────────────────────────┐         │
│            │            Android SMS Database                 │         │
│            │            (mmssms.db)                          │         │
│            └─────────────────────────────────────────────────┘         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Command Parameters

#### termux-contact-list

```bash
# No parameters - returns all contacts
termux-contact-list

# Output format (JSON array)
[
  {
    "name": "Contact Name",
    "number": "+919876543210"
  }
]
```

#### termux-sms-list

```bash
# Parameters
-l, --limit      Number of messages to show (default: 10)
-n, --number     Filter by phone number
-t, --type       Message type: inbox, sent, draft, outbox, all
-d, --date       Messages after date (YYYY-MM-DD)
--offset         Skip first N messages

# Examples
termux-sms-list                    # Last 10 messages
termux-sms-list -l 50              # Last 50 messages
termux-sms-list -n "+919876543210" # From specific number
termux-sms-list -t sent            # Only sent messages
termux-sms-list -d 2024-01-01      # Since Jan 1, 2024
```

#### termux-sms-send

```bash
# Parameters
-n, --number     Phone number(s) to send to (required)
--recipient      Alternative for -n

# Examples
termux-sms-send -n "+919876543210" "Hello!"
termux-sms-send -n "+91111" -n "+91222" "Bulk message"
echo "Message" | termux-sms-send -n "+919876543210"
```

#### termux-call-log

```bash
# Parameters
-l, --limit      Number of calls to show (default: 10)
-o, --offset     Skip first N records

# Examples
termux-call-log           # Last 10 calls
termux-call-log -l 100    # Last 100 calls
termux-call-log -o 10     # Skip first 10, show next 10
```

#### termux-telephony-call

```bash
# Parameters
<number>        Phone number to call (required)

# Example
termux-telephony-call +919876543210
```

### 4. JSON Output Structure

#### Contact Object
```json
{
  "name": "John Doe",
  "number": "+919876543210"
}
```

#### SMS Object
```json
{
  "threadid": 5,
  "type": "inbox",
  "read": 1,
  "sender": "+919876543210",
  "number": "+919876543210",
  "received": 1698765432000,
  "body": "Hello, this is a test message"
}
```

| Field | Description |
|-------|-------------|
| threadid | Conversation thread identifier |
| type | Message type: inbox/sent/draft/outbox |
| read | Read status: 1=read, 0=unread |
| sender | Sender phone number |
| number | Phone number (same as sender for inbox) |
| received | Unix timestamp in milliseconds |
| body | Message content |

#### Call Log Object
```json
{
  "name": "John Doe",
  "phone_number": "+919876543210",
  "duration": 120,
  "type": "INCOMING",
  "date": 1698765432000
}
```

| Field | Description |
|-------|-------------|
| name | Contact name (null if not saved) |
| phone_number | Phone number |
| duration | Call duration in seconds |
| type | INCOMING/OUTGOING/MISSED |
| date | Unix timestamp in milliseconds |

---

## 🔧 PRACTICAL EXAMPLES (20+ Examples)

### Example 1: List All Contacts
```bash
termux-contact-list
```

### Example 2: Count Total Contacts
```bash
termux-contact-list | jq length
```

### Example 3: Search Contact by Name
```bash
termux-contact-list | jq '.[] | select(.name | test("Rahul"; "i"))'
```

### Example 4: Search Contact by Number
```bash
termux-contact-list | jq '.[] | select(.number | contains("9876"))'
```

### Example 5: Export Contacts to CSV
```bash
echo "Name,Number" > contacts.csv
termux-contact-list | jq -r '.[] | "\(.name),\(.number)"' >> contacts.csv
```

### Example 6: Export Contacts to JSON File
```bash
termux-contact-list > contacts_backup.json
```

### Example 7: Find Duplicate Numbers
```bash
termux-contact-list | jq -r '.[].number' | sort | uniq -d
```

### Example 8: List Recent SMS
```bash
termux-sms-list
```

### Example 9: List Last 50 SMS
```bash
termux-sms-list -l 50
```

### Example 10: SMS from Specific Number
```bash
termux-sms-list -n "+919876543210"
```

### Example 11: Only Sent Messages
```bash
termux-sms-list -t sent
```

### Example 12: Only Unread Messages
```bash
termux-sms-list | jq '.[] | select(.read == 0)'
```

### Example 13: Count Unread Messages
```bash
termux-sms-list | jq '[.[] | select(.read == 0)] | length'
```

### Example 14: Send SMS
```bash
termux-sms-send -n "+919876543210" "Hello from Termux!"
```

### Example 15: Send SMS from File
```bash
cat message.txt | termux-sms-send -n "+919876543210"
```

### Example 16: Send SMS to Multiple Numbers
```bash
termux-sms-send -n "+91111111111" -n "+92222222222" "Group message"
```

### Example 17: View Call Log
```bash
termux-call-log
```

### Example 18: View Only Missed Calls
```bash
termux-call-log | jq '.[] | select(.type == "MISSED")'
```

### Example 19: View Only Outgoing Calls
```bash
termux-call-log | jq '.[] | select(.type == "OUTGOING")'
```

### Example 20: Calculate Total Call Duration
```bash
termux-call-log | jq '[.[] | .duration] | add'
```

### Example 21: Find Long Calls (>5 min)
```bash
termux-call-log | jq '.[] | select(.duration > 300)'
```

### Example 22: Make a Call
```bash
termux-telephony-call +919876543210
```

### Example 23: Search Contact and Call
```bash
NUMBER=$(termux-contact-list | jq -r '.[] | select(.name | contains("Rahul")) | .number' | head -1)
termux-telephony-call "$NUMBER"
```

### Example 24: Backup SMS with Date Filter
```bash
termux-sms-list -d 2024-01-01 > sms_2024.json
```

### Example 25: Extract SMS Body Text Only
```bash
termux-sms-list | jq -r '.[].body'
```

---

## 📋 COMMANDS REFERENCE

### Contacts Commands

```bash
# List all contacts (JSON)
termux-contact-list

# Count contacts
termux-contact-list | jq length

# Search by name
termux-contact-list | jq '.[] | select(.name | contains("Name"))'

# Search by number
termux-contact-list | jq '.[] | select(.number | contains("1234"))'

# Export to CSV
termux-contact-list | jq -r '.[] | "\(.name),\(.number)"' > contacts.csv

# Export to JSON
termux-contact-list > contacts.json

# Get names only
termux-contact-list | jq -r '.[].name'

# Get numbers only
termux-contact-list | jq -r '.[].number'
```

### SMS Commands

```bash
# List SMS (default 10)
termux-sms-list

# List specific count
termux-sms-list -l 50

# Filter by number
termux-sms-list -n "+919876543210"

# Filter by type
termux-sms-list -t inbox    # Received
termux-sms-list -t sent     # Sent
termux-sms-list -t all      # All

# Filter by date
termux-sms-list -d 2024-01-01

# Send SMS
termux-sms-send -n "+919876543210" "Your message"

# Send to multiple
termux-sms-send -n "+91111" -n "+91222" "Message"

# Send from file
cat msg.txt | termux-sms-send -n "+919876543210"

# Count SMS
termux-sms-list | jq length

# Get unread
termux-sms-list | jq '.[] | select(.read == 0)'
```

### Call Log Commands

```bash
# List calls (default 10)
termux-call-log

# List specific count
termux-call-log -l 100

# Filter by type
termux-call-log | jq '.[] | select(.type == "MISSED")'
termux-call-log | jq '.[] | select(.type == "INCOMING")'
termux-call-log | jq '.[] | select(.type == "OUTGOING")'

# Filter by duration
termux-call-log | jq '.[] | select(.duration > 300)'

# Filter by number
termux-call-log | jq '.[] | select(.phone_number | contains("9876"))'

# Total duration
termux-call-log | jq '[.[] | .duration] | add'

# Make call
termux-telephony-call +919876543210
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Contact Manager

```bash
# Task: Create a contact management script

cat > contact_manager.sh << 'EOF'
#!/bin/bash

echo "=== Contact Manager ==="
echo "1. List all contacts"
echo "2. Search contact"
echo "3. Export contacts"
echo "4. Count contacts"
echo "5. Exit"

read -p "Enter choice: " choice

case $choice in
    1)
        termux-contact-list | jq -r '.[] | "\(.name): \(.number)"'
        ;;
    2)
        read -p "Enter search term: " term
        termux-contact-list | jq -r ".[] | select(.name | test(\"$term\"; \"i\")) | \"\(.name): \(.number)\""
        ;;
    3)
        termux-contact-list > contacts_backup.json
        echo "Exported to contacts_backup.json"
        ;;
    4)
        echo "Total contacts: $(termux-contact-list | jq length)"
        ;;
    5)
        exit 0
        ;;
    *)
        echo "Invalid choice"
        ;;
esac
EOF

chmod +x contact_manager.sh
./contact_manager.sh
```

### Exercise 2: SMS Analyzer

```bash
# Task: Analyze SMS patterns

cat > sms_analyzer.sh << 'EOF'
#!/bin/bash

echo "=== SMS Analyzer ==="

# Total SMS
TOTAL=$(termux-sms-list -l 1000 | jq length)
echo "Total SMS analyzed: $TOTAL"

# Unread count
UNREAD=$(termux-sms-list -l 1000 | jq '[.[] | select(.read == 0)] | length')
echo "Unread SMS: $UNREAD"

# Inbox vs Sent
INBOX=$(termux-sms-list -l 1000 | jq '[.[] | select(.type == "inbox")] | length')
SENT=$(termux-sms-list -l 1000 | jq '[.[] | select(.type == "sent")] | length')
echo "Inbox: $INBOX | Sent: $SENT"

# Top senders
echo "Top senders:"
termux-sms-list -l 100 | jq -r '.[].sender' | sort | uniq -c | sort -rn | head -5
EOF

chmod +x sms_analyzer.sh
./sms_analyzer.sh
```

### Exercise 3: Call Log Report

```bash
# Task: Generate call log report

cat > call_report.sh << 'EOF'
#!/bin/bash

REPORT_FILE="call_report_$(date +%Y%m%d).txt"

echo "=== Call Log Report ===" > $REPORT_FILE
echo "Generated: $(date)" >> $REPORT_FILE
echo "" >> $REPORT_FILE

# Total calls
TOTAL=$(termux-call-log -l 500 | jq length)
echo "Total calls: $TOTAL" >> $REPORT_FILE

# By type
MISSED=$(termux-call-log -l 500 | jq '[.[] | select(.type == "MISSED")] | length')
INCOMING=$(termux-call-log -l 500 | jq '[.[] | select(.type == "INCOMING")] | length')
OUTGOING=$(termux-call-log -l 500 | jq '[.[] | select(.type == "OUTGOING")] | length')

echo "Missed: $MISSED | Incoming: $INCOMING | Outgoing: $OUTGOING" >> $REPORT_FILE

# Total duration
DURATION=$(termux-call-log -l 500 | jq '[.[] | .duration] | add // 0')
MINUTES=$((DURATION / 60))
echo "Total talk time: ${MINUTES} minutes" >> $REPORT_FILE

echo "" >> $REPORT_FILE
echo "Recent calls:" >> $REPORT_FILE
termux-call-log -l 10 | jq -r '.[] | "\(.type): \(.phone_number) (\(.duration)s)"' >> $REPORT_FILE

cat $REPORT_FILE
EOF

chmod +x call_report.sh
./call_report.sh
```

### Exercise 4: Bulk SMS Tool

```bash
# Task: Create bulk SMS sender with confirmation

cat > bulk_sms.sh << 'EOF'
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: ./bulk_sms.sh 'message'"
    exit 1
fi

MESSAGE="$1"

echo "Available contacts:"
termux-contact-list | jq -r '.[] | "\(.name) - \(.number)"' | nl

echo ""
read -p "Enter contact numbers to send (comma-separated indices): " INDICES

IFS=',' read -ra ARR <<< "$INDICES"

echo ""
echo "Will send message: $MESSAGE"
echo "To ${#ARR[@]} contacts"
read -p "Confirm? (y/n): " CONFIRM

if [ "$CONFIRM" = "y" ]; then
    for i in "${ARR[@]}"; do
        NUMBER=$(termux-contact-list | jq -r ".[$((i-1))].number")
        NAME=$(termux-contact-list | jq -r ".[$((i-1))].name")
        echo "Sending to $NAME ($NUMBER)..."
        termux-sms-send -n "$NUMBER" "$MESSAGE"
        sleep 2
    done
    echo "Done!"
else
    echo "Cancelled"
fi
EOF

chmod +x bulk_sms.sh
./bulk_sms.sh "Test message from Termux"
```

### Exercise 5: Python SMS Dashboard

```python
# Task: Create Python SMS/Contacts dashboard
# Save as: sms_dashboard.py

import subprocess
import json
from datetime import datetime

def run_cmd(cmd):
    result = subprocess.run(cmd, shell=True, capture_output=True, text=True)
    return result.stdout

def get_contacts():
    data = run_cmd("termux-contact-list")
    return json.loads(data) if data else []

def get_sms(limit=50):
    data = run_cmd(f"termux-sms-list -l {limit}")
    return json.loads(data) if data else []

def get_calls(limit=50):
    data = run_cmd(f"termux-call-log -l {limit}")
    return json.loads(data) if data else []

def show_dashboard():
    contacts = get_contacts()
    sms = get_sms()
    calls = get_calls()
    
    print("=" * 50)
    print("       TERMUX SMS & CONTACTS DASHBOARD")
    print("=" * 50)
    
    print(f"\n📊 STATISTICS:")
    print(f"   Contacts: {len(contacts)}")
    print(f"   Recent SMS: {len(sms)}")
    print(f"   Recent Calls: {len(calls)}")
    
    # SMS stats
    if sms:
        unread = len([s for s in sms if s.get('read') == 0])
        inbox = len([s for s in sms if s.get('type') == 'inbox'])
        sent = len([s for s in sms if s.get('type') == 'sent'])
        print(f"\n📱 SMS BREAKDOWN:")
        print(f"   Unread: {unread}")
        print(f"   Inbox: {inbox}")
        print(f"   Sent: {sent}")
    
    # Call stats
    if calls:
        missed = len([c for c in calls if c.get('type') == 'MISSED'])
        incoming = len([c for c in calls if c.get('type') == 'INCOMING'])
        outgoing = len([c for c in calls if c.get('type') == 'OUTGOING'])
        total_duration = sum(c.get('duration', 0) for c in calls)
        print(f"\n📞 CALL BREAKDOWN:")
        print(f"   Missed: {missed}")
        print(f"   Incoming: {incoming}")
        print(f"   Outgoing: {outgoing}")
        print(f"   Talk time: {total_duration // 60} min")
    
    print("\n" + "=" * 50)

if __name__ == "__main__":
    show_dashboard()
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Permission denied" for Contacts

```bash
# Cause: Contacts permission not granted

# Solution 1: Run command and accept permission popup
termux-contact-list

# Solution 2: Manual permission grant
# Settings → Apps → Termux → Permissions → Enable Contacts

# Solution 3: Check permission
dumpsys package com.termux | grep -A5 "runtime permissions"
```

### Problem 2: SMS not sending

```bash
# Cause: Multiple reasons

# Solution 1: Check SMS permission
# Settings → Apps → Termux → Permissions → Enable SMS

# Solution 2: Check if number format is correct
# Use international format: +91XXXXXXXXXX

# Solution 3: Check credit/balance for paid SMS

# Solution 4: Android 10+ background restrictions
# Use Termux in foreground, not background

# Test with simple SMS
termux-sms-send -n "+91XXXXXXXXXX" "Test"
```

### Problem 3: Empty contact list

```bash
# Cause: Permission not granted or no contacts

# Solution 1: Check permission
termux-contact-list
# Accept permission popup

# Solution 2: Verify contacts exist in phone
# Open Phone app → Contacts → Check if contacts are there

# Solution 3: Check Termux:API app is installed
pkg list-installed | grep termux-api

# Solution 4: Reinstall termux-api
pkg uninstall termux-api
pkg install termux-api
```

### Problem 4: Call log not showing

```bash
# Cause: Phone permission not granted

# Solution 1: Grant permission manually
# Settings → Apps → Termux → Permissions → Phone

# Solution 2: Run command and accept popup
termux-call-log

# Solution 3: Check if call log exists in Phone app
```

### Problem 5: JSON parsing errors

```bash
# Cause: Invalid JSON output or jq not installed

# Solution 1: Install jq
pkg install jq -y

# Solution 2: Check raw output
termux-contact-list
# Verify it's valid JSON

# Solution 3: Handle empty results
termux-contact-list | jq '. // []'

# Solution 4: Check for special characters
termux-contact-list | jq '.[] | .name' | cat -v
```

### Problem 6: Termux:API not working

```bash
# Cause: API package or app not installed

# Solution 1: Install package
pkg install termux-api -y

# Solution 2: Install Termux:API app from F-Droid
# Search "Termux:API" in F-Droid

# Solution 3: Check both are from same source
# Don't mix Play Store and F-Droid versions

# Solution 4: Test API
termux-battery-status
# Should show battery info if working
```

### Problem 7: Background SMS fails

```bash
# Cause: Android 10+ background restrictions

# Solution 1: Use Termux in foreground
# Keep Termux app open when sending SMS

# Solution 2: Use Termux:Boot for startup scripts
# Install Termux:Boot from F-Droid

# Solution 3: Use foreground service
# Some Android versions allow with notification

# Solution 4: Use WorkManager/Termux:Tasker
# For automation, use Tasker integration
```

### Problem 8: Unicode/Emoji issues

```bash
# Cause: Character encoding

# Solution 1: Use UTF-8 encoding
export LANG=en_US.UTF-8

# Solution 2: For SMS, emojis usually work
termux-sms-send -n "+91XXX" "Hello! 👋"

# Solution 3: Check terminal font supports emojis
# Install Nerd font or emoji font
pkg install fontconfig
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📱 CONTACTS & SMS API            │
│   Complete Guide                   │
│                                    │
│   ✓ Contact Management             │
│   ✓ SMS Automation                 │
│   ✓ Call Log Access                │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Action Style**
```
┌────────────────────────────────────┐
│  💬 SEND SMS FROM TERMINAL!        │
│                                    │
│  📞 Contacts  │  📨 SMS  │  📱 Call │
│                                    │
│  termux-sms-send                   │
│  termux-contact-list               │
│                                    │
│  Chapter 22 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Script Focus**
```
┌────────────────────────────────────┐
│  🔥 AUTOMATE SMS & CALLS           │
│                                    │
│  Bulk SMS │ Auto-Reply │ Backup    │
│                                    │
│  [Code snippet preview]            │
│  termux-sms-send -n...             │
│                                    │
│  T3rmuxk1ng                        │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📱 Termux Full Course - Chapter 22: Contacts & SMS API | Complete Guide

🔥 In this video you'll learn:
• termux-contact-list - Access phone contacts
• termux-sms-list - Read SMS messages
• termux-sms-send - Send SMS from terminal
• termux-call-log - View call history
• Bulk SMS scripts
• Auto-reply automation
• Contact backup scripts
• Python integration

⏱️ Timestamps:
0:00 - Introduction
0:45 - Prerequisites & Setup
2:30 - Contact List API
5:30 - SMS List API
8:30 - SMS Send API
11:00 - Call Log API
13:00 - Making Calls
14:30 - Practical Scripts
18:00 - Python Integration
20:00 - Privacy & Permissions
21:30 - Summary

📝 Commands from this video:
termux-contact-list
termux-sms-list
termux-sms-send -n "+91XXX" "message"
termux-call-log
termux-telephony-call +91XXX

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxAPI #ContactsSMS #TermuxCourse #T3rmuxk1ng #AndroidAutomation #TermuxHindi

---
⚠️ Disclaimer: This video is for educational purposes only. Use responsibly and respect privacy.
```

### Tags List

```
termux, termux api, termux sms, termux contacts, termux call log,
termux sms send, termux contact list, termux automation, termux scripts,
termux tutorial, termux course, termux hindi, termux full course,
android sms terminal, terminal sms, command line sms,
bulk sms termux, sms automation, contact backup termux,
t3rmuxk1ng, termux tutorial hindi, android automation,
termux python sms, sms from terminal, call log terminal
```

### Hashtags

```
#Termux #TermuxAPI #TermuxSMS #TermuxContacts #AndroidAutomation 
#TermuxTutorial #TermuxCourse #TermuxHindi #T3rmuxk1ng #LearnTermux 
#SMSAutomation #ContactManagement #TerminalCommands
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux API Wiki | https://wiki.termux.com/wiki/Termux:API |
| Termux GitHub | https://github.com/termux/termux-api |
| Android SMS Docs | https://developer.android.com/reference/android/telephony/SmsManager |

### Related Packages

| Package | Description |
|---------|-------------|
| jq | JSON processor for parsing API output |
| python | For advanced scripts |
| curl | For SMS gateway integration |

### Useful Scripts Repository

```bash
# Clone example scripts
git clone https://github.com/termux/termux-api-package

# Community scripts
# Search GitHub for "termux sms script"
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 23, verify:

- [ ] termux-api package installed
- [ ] Termux:API app installed from F-Droid
- [ ] Contacts permission granted
- [ ] SMS permission granted
- [ ] Phone permission granted (for call log)
- [ ] Can list contacts with termux-contact-list
- [ ] Can read SMS with termux-sms-list
- [ ] Can send SMS with termux-sms-send
- [ ] Can view call log with termux-call-log
- [ ] Created at least one automation script
- [ ] Understand privacy implications

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 23: Termux API - Clipboard & Share**

- termux-clipboard-get - Read clipboard
- termux-clipboard-set - Write to clipboard
- termux-share - Share content to apps
- Clipboard automation scripts
- Cross-app data sharing
- Share receiver functionality

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
