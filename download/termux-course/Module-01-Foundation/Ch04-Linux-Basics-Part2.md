# Chapter 4: Linux Basics - Part 2

> **Module:** 1 - Foundation  
> **Chapter:** 4 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Beginner-Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | File operations, permissions, text processing |
| Commands Reference | 20+ practical examples |
| Practice Exercises | 5 hands-on tasks |
| Troubleshooting | Common errors and fixes |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 4
Title: Linux Basics Part 2 | Files, Permissions & Text Processing | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main hoon T3rmuxk1ng aur aaj Chapter 4 mein hum Linux ke aur bhi powerful
commands seekhenge jo aapko ek pro user banane ke liye zaroori hain.

Pichle chapter mein humne basics seekhe the - ls, cd, mkdir, rm, cp, mv.
Aaj hum seekhenge:

- Files ko kaise view aur create karein (cat, touch)
- Text mein search kaise karein (grep)
- Files kaise dhundein (find)
- Permissions aur ownership (chmod, chown)
- File content analyze karna (head, tail, wc, sort, uniq, diff)
- Redirection aur pipes - command chaining

Ye sab commands daily use aate hain - scripting mein, hacking tools mein,
automation mein - har jagah.

To chaliye shuru karte hain!

---

[SECTION 1: CAT COMMAND - 0:45 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle cat command - ye ek bahut hi useful command hai.

Cat ka full form hai "concatenate" - matlab jodna. Lekin iske 3 main uses
hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                        CAT COMMAND USES                                  │
├─────────────────────────────────────────────────────────────────────────┤
│ 1. File content dekhna (view)                                           │
│ 2. Naye files create karna                                               │
│ 3. Multiple files jodna (concatenate)                                   │
└─────────────────────────────────────────────────────────────────────────┘

[DEMO: View File Content]

Pehle ek file bana lete hain:
    echo "Hello Termux!" > test.txt

Ab cat se dekhein:
    cat test.txt

Output: Hello Termux!

Simple! File ka content screen pe aa gaya.

[DEMO: View Multiple Files]

    echo "File One" > file1.txt
    echo "File Two" > file2.txt
    cat file1.txt file2.txt

Output:
File One
File Two

Dono files ka content ek saath aa gaya.

[DEMO: Create New File with cat]

    cat > newfile.txt

Ab aap type karein:
    This is line 1
    This is line 2

Ctrl+D dabayein save karne ke liye.

Ab check karein:
    cat newfile.txt

File ban gayi with content!

[DEMO: Append to File]

    cat >> newfile.txt

Type karein:
    This is line 3

Ctrl+D dabayein.

Ab cat newfile.txt karein - teen lines dikhengi.

[DEMO: Concatenate Files into One]

    cat file1.txt file2.txt > merged.txt
    cat merged.txt

Dono files ka content merged.txt mein aa gaya.

[DEMO: Line Numbers with cat]

    cat -n test.txt

Output mein line numbers bhi dikhenge.

    cat -b test.txt

Non-empty lines ka number dikhata hai.

Pro tip: Badi files ke liye cat ke saath use karein:
    cat bigfile.txt | less
    Less se scroll kar sakte ho, q press karke exit karein.

---

[SECTION 2: TOUCH COMMAND - 4:00 to 5:30]
─────────────────────────────────────────────────────────────────────────────

Ab touch command - ye bahut simple hai lekin useful.

Touch ke 2 main uses hain:

1. Empty files create karna
2. File timestamps update karna

[DEMO: Create Empty Files]

    touch myfile.txt

Empty file ban gayi! Check karein:
    ls -la myfile.txt

Size 0 dikhega - empty file.

[DEMO: Multiple Files Create]

    touch file1.txt file2.txt file3.txt

Ek command mein 3 files ban gayi!

    ls *.txt

[DEMO: Update Timestamp]

Pehle file ka timestamp dekhein:
    ls -la myfile.txt

Ab touch karein:
    touch myfile.txt

Phir dekhein:
    ls -la myfile.txt

Timestamp update ho gaya - current time dikhega.

Ye scripts mein use hota hai jab aapko:
- Placeholder files create karni ho
- File modification time change karni ho
- Quick empty files banani ho

---

[SECTION 3: GREP COMMAND - 5:30 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Ab aata hai GREP - ye bahut powerful command hai!

Grep ka full form hai "Global Regular Expression Print".

Ye text files mein search karta hai. Searching ka king hai!

Basic syntax:
    grep "pattern" filename

[DEMO: Basic Search]

Pehle ek file bana lete hain with some content:

    cat > data.txt << 'EOF'
apple
banana
apple pie
APPLE JUICE
grape
pineapple
orange
EOF

Ab search karein:
    grep "apple" data.txt

Output:
apple
apple pie
pineapple

Saari lines jo "apple" contain karti hain, wo aa gayi!

[DEMO: Case Insensitive Search -i]

    grep -i "apple" data.txt

Output:
apple
apple pie
APPLE JUICE
pineapple

-i flag case ignore karta hai - chhota bada sab milega.

[DEMO: Show Line Numbers -n]

    grep -n "apple" data.txt

Output:
1:apple
3:apple pie
6:pineapple

Line numbers bhi dikhenge!

[DEMO: Invert Match -v]

    grep -v "apple" data.txt

Output:
banana
APPLE JUICE
grape
orange

-v flag lines ko EXCLUDE karta hai jo match karti hain.

[DEMO: Recursive Search -r]

Bahut useful! Directory mein saari files mein search:

    mkdir testdir
    cp data.txt testdir/
    echo "secret data" > testdir/secret.txt

    grep -r "secret" testdir/

Output:
testdir/secret.txt:secret data

Saari files mein dhundh ke batayega!

[DEMO: Count Matches -c]

    grep -c "apple" data.txt

Output: 3

Kitni lines match hui, count batayega.

[DEMO: Exact Word Match -w]

    grep -w "apple" data.txt

Sirf exact word match karega - "apple pie" mein "apple" word 
milega, "pineapple" mein nahi milega.

[DEMO: Regular Expression]

    grep "^a" data.txt

^ ka matlab start - sirf a se shuru hone wali lines.

    grep "e$" data.txt

$ ka matlab end - e se khatam hone wali lines.

    grep "a.*e" data.txt

.* ka matlab kuch bhi - a se shuru e se khatam.

Grep bahut powerful hai - isse practice karein!

---

[SECTION 4: FIND COMMAND - 9:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab find command - ye files dhundhne ke liye use hota hai.

Grep text search karta hai, find files search karta hai!

Basic syntax:
    find [path] [options] [pattern]

[DEMO: Find by Name]

    find . -name "data.txt"

Current directory (.) mein data.txt dhundhega.

    find . -name "*.txt"

Saari .txt files list karega.

[DEMO: Case Insensitive -iname]

    find . -iname "DATA.txt"

Case ignore karega.

[DEMO: Find by Type -type]

    find . -type d

Sirf directories dikhayega.

    find . -type f

Sirf files dikhayega.

    find . -type f -name "*.txt"

Sirf txt files.

[DEMO: Find by Size -size]

    find . -size +1M

1MB se badi files.

    find . -size -100k

100KB se chhoti files.

    find . -size +100k -size -1M

100KB se badi, 1MB se chhoti.

[DEMO: Find by Time -mtime]

    find . -mtime -1

Last 1 din mein modify hui files.

    find . -mtime +7

7 din pehle modify hui files.

    find . -mmin -60

Last 60 minutes mein modify hui files.

[DEMO: Execute Command on Found Files -exec]

    find . -name "*.txt" -exec cat {} \;

Ye saari txt files ka content dikhayega!

{} ka matlab mil gayi file, \; command end karta hai.

    find . -name "*.log" -exec rm {} \;

Saari .log files delete kar dega!

[DEMO: Combine Conditions]

    find . -type f -name "*.txt" -size +1k

Txt files jo 1KB se badi hain.

Find bahut powerful hai - isse daily use karein!

---

[SECTION 5: CHMOD COMMAND - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab permissions ki baat - ye Linux ka most important concept hai!

Linux mein har file ke 3 types ke permissions hote hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    FILE PERMISSIONS                                      │
├──────────────┬──────────────────────────────────────────────────────────┤
│ Permission   │ Meaning                                                  │
├──────────────┼──────────────────────────────────────────────────────────┤
│ r (read)     │ File padh sakte, directory list kar sakte                │
│ w (write)    │ File modify kar sakte, directory mein add/delete         │
│ x (execute)  │ File run kar sakte, directory mein enter kar sakte       │
└──────────────┴──────────────────────────────────────────────────────────┘

Aur ye permissions 3 categories ke liye hote hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    PERMISSION CATEGORIES                                 │
├──────────────┬──────────────────────────────────────────────────────────┤
│ Category     │ Description                                              │
├──────────────┼──────────────────────────────────────────────────────────┤
│ User (u)     │ File ka owner - aap                                      │
│ Group (g)    │ File ki group members                                    │
│ Others (o)   │ Baaki sab users                                          │
└──────────────┴──────────────────────────────────────────────────────────┘

Permissions check karein:
    ls -la

Output kuch aisa dikhega:
-rw------- 1 u0_aXXX u0_aXXX 12 Jan 1 12:00 myfile.txt

Pehla character - (dash) = file, d = directory

Agle 9 characters: rw------- 
- First 3: User permissions (rw-)
- Next 3: Group permissions (---)
- Last 3: Others permissions (---)

[DEMO: Symbolic Notation]

Symbolic notation mein letters use hote hain:

    chmod u+x script.sh

User ko execute permission dena.

    chmod g+w file.txt

Group ko write permission dena.

    chmod o+r file.txt

Others ko read permission dena.

    chmod ugo+rwx file.txt

Sabko saare permissions dena.

    chmod +x script.sh

Sabko execute permission (shortcut).

    chmod -x script.sh

Execute permission lena.

    chmod u=rwx,g=rx,o=r file.txt

Exact permissions set karna.

[DEMO: Octal Notation - Numbers]

Ye thoda confusing lagta hai, lekin bahut fast hai!

┌─────────────────────────────────────────────────────────────────────────┐
│                    OCTAL NOTATION                                        │
├──────────────┬──────────────────────────────────────────────────────────┤
│ Number       │ Permissions                                              │
├──────────────┼──────────────────────────────────────────────────────────┤
│ 0            │ --- (no permissions)                                     │
│ 1            │ --x (execute only)                                       │
│ 2            │ -w- (write only)                                         │
│ 3            │ -wx (write + execute)                                    │
│ 4            │ r-- (read only)                                          │
│ 5            │ r-x (read + execute)                                     │
│ 6            │ rw- (read + write)                                       │
│ 7            │ rwx (all permissions)                                    │
└──────────────┴──────────────────────────────────────────────────────────┘

Examples:

    chmod 755 script.sh

7 = User = rwx (4+2+1)
5 = Group = r-x (4+0+1)
5 = Others = r-x (4+0+1)

Ye scripts ke liye common hai - owner sab kar sakta, baaki read aur execute.

    chmod 644 file.txt

6 = User = rw- (4+2+0)
4 = Group = r-- (4+0+0)
4 = Others = r-- (4+0+0)

Ye normal files ke liye common hai - owner read/write, baaki sirf read.

    chmod 700 secret.txt

7 = User = rwx
0 = Group = ---
0 = Others = ---

Sirf owner - koi aur nahi.

    chmod 777 public.txt

Sab kuch - sabko! (Dangerous - use carefully)

[DEMO: Recursive chmod]

    chmod -R 755 myfolder/

Folder aur uski saari files/folders ka permission change.

Ye bahut important hai - scripts tabhi chalti hain jab execute permission ho!

---

[SECTION 6: CHOWN COMMAND - 15:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Chown ka matlab "change owner".

Termux mein normally aap hi owner hote ho, to chown ki zarurat kam hoti hai.
Lekin knowledge hona chahiye.

Syntax:
    chown user:group filename

[DEMO: Change Owner]

    touch testfile.txt
    ls -la testfile.txt

Owner dikhega: u0_aXXX (aapka Termux user ID)

    chown u0_aXXX testfile.txt

(Same owner - demo ke liye)

Recursively:
    chown -R user:group folder/

Termux mein ye command limited hai - root ke saath zyada useful hai.

---

[SECTION 7: HEAD AND TAIL COMMANDS - 16:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Head aur tail - file ke parts dekhne ke liye.

Head = Starting se lines
Tail = Ending se lines

[DEMO: Head Command]

    head data.txt

Pehli 10 lines dikhayega (default).

    head -5 data.txt

Pehli 5 lines.

    head -n 20 data.txt

Pehli 20 lines.

    head -c 100 data.txt

Pehle 100 bytes.

[DEMO: Tail Command]

    tail data.txt

Last 10 lines (default).

    tail -5 data.txt

Last 5 lines.

    tail -n 20 data.txt

Last 20 lines.

[DEMO: Tail -f (Follow Mode) - SUPER USEFUL]

    tail -f /var/log/logfile

Ye file ko follow karta hai - naye lines automatically dikhata hai!

Logs monitor karne ke liye best:
    tail -f /data/data/com.termux/files/usr/var/log/*.log

Ctrl+C se exit karein.

---

[SECTION 8: WC, SORT, UNIQ, DIFF - 17:30 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Ye text processing commands hain - data analysis ke liye.

[DEMO: WC - Word Count]

    wc data.txt

Output: 7 7 54 data.txt
- 7 lines
- 7 words
- 54 bytes

    wc -l data.txt

Sirf lines count.

    wc -w data.txt

Sirf words count.

    wc -c data.txt

Sirf bytes count.

[DEMO: Sort]

    sort data.txt

Alphabetical order mein sort karta hai.

    sort -r data.txt

Reverse order.

    sort -n numbers.txt

Numeric sort.

    sort -u data.txt

Unique lines only (duplicates remove).

[DEMO: Uniq]

    cat > duplicates.txt << 'EOF'
apple
apple
banana
banana
banana
cherry
EOF

    uniq duplicates.txt

Duplicates remove karta hai (consecutive).

    sort duplicates.txt | uniq

Pehle sort, phir uniq - perfect!

    sort duplicates.txt | uniq -c

Count bhi dikhata hai:
   2 apple
   3 banana
   1 cherry

[DEMO: Diff - Compare Files]

    cat > file1.txt << 'EOF'
line 1
line 2
line 3
EOF

    cat > file2.txt << 'EOF'
line 1
line 2 modified
line 3
line 4
EOF

    diff file1.txt file2.txt

Output:
2c2
< line 2
---
> line 2 modified
3a4
> line 4

< = file1 mein, > = file2 mein

Side by side diff:
    diff -y file1.txt file2.txt

---

[SECTION 9: REDIRECTION AND PIPES - 19:30 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Ab aata hai command chaining - sabse powerful concept!

[DEMO: Output Redirection >]

    echo "Hello" > file.txt

Output file mein save karna. File overwrite hoti hai!

    echo "Another line" > file.txt

Purana content gayab - file overwrite ho gayi.

[DEMO: Append Redirection >>]

    echo "Line 1" >> file.txt
    echo "Line 2" >> file.txt

Content add hota hai, file overwrite nahi hoti.

[DEMO: Input Redirection <]

    cat < file.txt

File ka content as input dena.

    wc -l < file.txt

File se input leke count karna.

[DEMO: Pipes |]

Pipe ek command ka output doosri command mein bhejta hai!

    cat data.txt | grep "apple"

Pehle file padh lo, phir grep karo.

    ls -la | grep ".txt"

Sirf txt files list karo.

    ls | wc -l

Kitni files hain count karo.

    cat data.txt | sort | uniq

Sort karo, unique lines nikaalo.

    history | grep "python"

History mein python commands dhundho.

    ps aux | grep "termux"

Running processes mein termux dhundho.

    find . -name "*.txt" | wc -l

Kitni txt files hain count karo.

Pipes se complex tasks easy ho jaate hain!

---

[SECTION 10: SUMMARY & NEXT PREVIEW - 21:30 to 22:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 4 complete! Let's summarize:

✅ cat - Files view, create, concatenate
✅ touch - Empty files, timestamps
✅ grep - Text search with options -i, -r, -n, -v
✅ find - File search by name, type, size, time
✅ chmod - Permissions (symbolic & octal)
✅ chown - Change ownership
✅ head/tail - File content preview
✅ wc, sort, uniq, diff - Text processing
✅ Redirection > >> < and pipes |

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 4 - IMPORTANT COMMANDS                        │
├─────────────────────────────────────────────────────────────────────────┤
│ cat file.txt               │ View file content                          │
│ cat file1 file2 > merged   │ Concatenate files                          │
│ touch file.txt             │ Create empty file                          │
│ grep "pattern" file        │ Search text in file                        │
│ grep -r "pattern" dir/     │ Recursive search                           │
│ find . -name "*.txt"       │ Find txt files                             │
│ chmod 755 script.sh        │ Set execute permission                     │
│ chmod +x script.sh         │ Add execute permission                     │
│ head -10 file.txt          │ First 10 lines                             │
│ tail -f logfile            │ Follow log file                            │
│ wc -l file.txt             │ Count lines                                │
│ sort file.txt              │ Sort alphabetically                        │
│ sort file | uniq           │ Unique sorted lines                        │
│ command > file             │ Redirect output to file                    │
│ command >> file            │ Append output to file                      │
│ cmd1 | cmd2                │ Pipe output to next command                │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 5 mein hum seekhenge:
- Package management in detail
- pkg, apt commands
- Repository management
- Installing tools and dependencies

Practice karein! Commands tabhi yaad rahenge.

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Thank you for watching! See you in Chapter 5!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. cat Command - Complete Reference

The `cat` command is one of the most frequently used commands in Linux.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         CAT COMMAND SYNTAX                               │
├─────────────────────────────────────────────────────────────────────────┤
│ cat [OPTIONS] [FILE]...                                                  │
└─────────────────────────────────────────────────────────────────────────┘
```

**Options:**

| Option | Description |
|--------|-------------|
| `-n` | Number all output lines |
| `-b` | Number non-empty lines only |
| `-s` | Suppress repeated empty lines |
| `-T` | Display TAB characters as ^I |
| `-e` | Display $ at end of each line |
| `-A` | Show all (equivalent to -vET) |

**Common Use Cases:**

```bash
# View single file
cat filename.txt

# View multiple files
cat file1.txt file2.txt file3.txt

# Concatenate files into new file
cat file1.txt file2.txt > combined.txt

# Create new file from terminal
cat > newfile.txt
# Type content, press Ctrl+D to save

# Append to existing file
cat >> existing.txt
# Type content, press Ctrl+D to save

# Display with line numbers
cat -n file.txt

# Display non-blank lines with numbers
cat -b file.txt

# Combine multiple files with line numbers
cat -n file1.txt file2.txt > numbered.txt

# View file with special characters visible
cat -A file.txt

# Copy file content to another
cat source.txt > destination.txt

# Display file content in uppercase
cat file.txt | tr 'a-z' 'A-Z'

# Quick file preview
cat file.txt | head -20
```

### 2. touch Command

The `touch` command creates empty files and updates timestamps.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        TOUCH COMMAND SYNTAX                              │
├─────────────────────────────────────────────────────────────────────────┤
│ touch [OPTIONS] FILE...                                                  │
└─────────────────────────────────────────────────────────────────────────┘
```

**Timestamp Types:**

| Timestamp | Description | Option |
|-----------|-------------|--------|
| Access Time (atime) | Last time file was read | -a |
| Modification Time (mtime) | Last time file content changed | -m |
| Change Time (ctime) | Last time metadata changed | (automatic) |

**Options:**

| Option | Description |
|--------|-------------|
| `-a` | Change only access time |
| `-m` | Change only modification time |
| `-d STRING` | Use specified date |
| `-t STAMP` | Use specified timestamp |
| `-r FILE` | Use another file's timestamps |
| `-c` | Don't create if doesn't exist |

**Examples:**

```bash
# Create single empty file
touch newfile.txt

# Create multiple files
touch file1.txt file2.txt file3.txt

# Create file with specific date
touch -d "2024-01-15" file.txt

# Create file with specific time
touch -t 202401151200 file.txt  # YYYYMMDDhhmm

# Update timestamps to current time
touch existing_file.txt

# Copy timestamps from another file
touch -r source.txt target.txt

# Update only access time
touch -a file.txt

# Update only modification time
touch -m file.txt

# Create numbered files (brace expansion)
touch file{1..10}.txt
# Creates file1.txt, file2.txt, ..., file10.txt

# Create files for multiple extensions
touch script.{py,sh,txt}
# Creates script.py, script.sh, script.txt
```

### 3. grep Command - Complete Reference

The `grep` command searches for patterns in text files.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        GREP COMMAND SYNTAX                               │
├─────────────────────────────────────────────────────────────────────────┤
│ grep [OPTIONS] PATTERN [FILE...]                                         │
│ grep [OPTIONS] [-e PATTERN]... [-f FILE] [FILE...]                      │
└─────────────────────────────────────────────────────────────────────────┘
```

**Essential Options:**

| Option | Description |
|--------|-------------|
| `-i` | Case insensitive search |
| `-v` | Invert match (exclude matching lines) |
| `-n` | Show line numbers |
| `-r` | Recursive search in directory |
| `-l` | Show only filenames with matches |
| `-c` | Count matching lines |
| `-w` | Match whole word only |
| `-x` | Match whole line only |
| `-o` | Show only matching part |
| `-A NUM` | Show NUM lines after match |
| `-B NUM` | Show NUM lines before match |
| `-C NUM` | Show NUM lines around match |
| `-E` | Extended regex (use +, ?, |) |
| `-F` | Fixed string (no regex) |
| `--color=auto` | Highlight matches |

**Regular Expression Patterns:**

| Pattern | Meaning |
|---------|---------|
| `^pattern` | Line starts with pattern |
| `pattern$` | Line ends with pattern |
| `.` | Any single character |
| `*` | Zero or more of previous |
| `+` | One or more of previous |
| `?` | Zero or one of previous |
| `[abc]` | Any character in set |
| `[^abc]` | Any character NOT in set |
| `[a-z]` | Any character in range |
| `\b` | Word boundary |
| `\d` | Digit [0-9] |
| `\s` | Whitespace |
| `\w` | Word character [a-zA-Z0-9_] |

**Examples:**

```bash
# Basic search
grep "error" logfile.txt

# Case insensitive
grep -i "error" logfile.txt

# Show line numbers
grep -n "error" logfile.txt

# Invert match (exclude lines)
grep -v "debug" logfile.txt

# Recursive search
grep -r "password" /home/user/

# Search in specific file types
grep -r --include="*.py" "import" .

# Count matches
grep -c "error" logfile.txt

# Match whole word
grep -w "cat" file.txt  # Won't match "catalog"

# Show context around match
grep -C 3 "error" logfile.txt  # 3 lines before and after
grep -A 5 "error" logfile.txt  # 5 lines after
grep -B 2 "error" logfile.txt  # 2 lines before

# Multiple patterns (OR)
grep -E "error|warning|fail" logfile.txt

# Show only matching part
grep -o "[0-9]\+" file.txt  # Extract all numbers

# Line starts with pattern
grep "^Error" logfile.txt

# Line ends with pattern
grep "failed$" logfile.txt

# Empty lines
grep "^$" file.txt

# Email addresses
grep -E "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}" file.txt

# IP addresses
grep -E "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" file.txt

# Combine options
grep -rn --color=auto "function" *.py

# Use with pipe
cat log.txt | grep "error" | grep -v "ignore"
ps aux | grep python
history | grep "apt"
```

### 4. find Command - Complete Reference

The `find` command searches for files in a directory hierarchy.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        FIND COMMAND SYNTAX                               │
├─────────────────────────────────────────────────────────────────────────┤
│ find [PATH] [EXPRESSION]                                                 │
└─────────────────────────────────────────────────────────────────────────┘
```

**Search Criteria:**

| Criteria | Description | Example |
|----------|-------------|---------|
| `-name` | Match filename (case sensitive) | `-name "*.txt"` |
| `-iname` | Match filename (case insensitive) | `-iname "*.TXT"` |
| `-type` | File type | `-type f` (file), `-type d` (dir) |
| `-size` | File size | `-size +1M` (larger than 1MB) |
| `-mtime` | Modified time (days) | `-mtime -7` (within 7 days) |
| `-mmin` | Modified time (minutes) | `-mmin -60` (within 60 min) |
| `-atime` | Access time (days) | `-atime +30` |
| `-ctime` | Change time (days) | `-ctime -1` |
| `-perm` | Permissions | `-perm 755` |
| `-user` | Owner | `-user root` |
| `-group` | Group | `-group termux` |
| `-empty` | Empty files/dirs | `-empty` |
| `-executable` | Executable files | `-executable` |

**Size Specifications:**

| Suffix | Meaning |
|--------|---------|
| `c` | Bytes |
| `k` | Kilobytes (1024 bytes) |
| `M` | Megabytes (1024 KB) |
| `G` | Gigabytes (1024 MB) |
| `+` | Greater than |
| `-` | Less than |

**Action Options:**

| Action | Description |
|--------|-------------|
| `-print` | Print path (default) |
| `-ls` | ls -dils format |
| `-delete` | Delete found files |
| `-exec CMD {} \;` | Execute command on each file |
| `-exec CMD {} +` | Execute with multiple files |
| `-ok CMD {} \;` | Prompt before execution |

**Examples:**

```bash
# Find by name
find . -name "file.txt"
find /home -name "*.py"
find . -iname "README*"

# Find by type
find . -type f          # Files only
find . -type d          # Directories only
find . -type l          # Symlinks only

# Find by size
find . -size 0          # Empty files
find . -size +100M      # Larger than 100MB
find . -size -1k        # Smaller than 1KB
find . -size +10k -size -100k  # Between 10KB and 100KB

# Find by time
find . -mtime -1        # Modified in last 24 hours
find . -mtime +7        # Modified more than 7 days ago
find . -mmin -60        # Modified in last 60 minutes
find . -atime +30       # Not accessed in 30 days

# Find by permission
find . -perm 755        # Exact permission
find . -perm -111       # Has execute for all
find . -perm /u+x       # Has user execute

# Find empty files/directories
find . -empty
find . -empty -type f   # Empty files only
find . -empty -type d   # Empty directories only

# Find executable files
find . -executable -type f

# Combine conditions (AND is implicit)
find . -name "*.txt" -size +1k

# OR condition
find . -name "*.txt" -o -name "*.md"

# NOT condition
find . -not -name "*.txt"
find . ! -name "*.txt"

# Execute command on results
find . -name "*.log" -exec rm {} \;
find . -name "*.txt" -exec cat {} \;
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;

# Find and delete
find . -name "*.tmp" -delete
find . -empty -delete

# Find recent files and copy
find . -mtime -1 -exec cp {} /backup/ \;

# Complex example: Find large old files
find . -type f -size +100M -mtime +30 -ls
```

### 5. chmod Command - Complete Reference

The `chmod` command changes file permissions.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        CHMOD COMMAND SYNTAX                              │
├─────────────────────────────────────────────────────────────────────────┤
│ chmod [OPTIONS] MODE FILE...                                             │
└─────────────────────────────────────────────────────────────────────────┘
```

**Permission Categories:**

| Category | Letter | Description |
|----------|--------|-------------|
| User/Owner | `u` | File owner |
| Group | `g` | File's group members |
| Others | `o` | Everyone else |
| All | `a` | User + Group + Others |

**Permission Types:**

| Permission | Letter | Octal | Description |
|------------|--------|-------|-------------|
| Read | `r` | 4 | View content / List directory |
| Write | `w` | 2 | Modify content / Create/delete files |
| Execute | `x` | 1 | Run file / Enter directory |

**Octal Permission Values:**

| Octal | Binary | Permissions |
|-------|--------|-------------|
| 0 | 000 | --- (no permissions) |
| 1 | 001 | --x (execute only) |
| 2 | 010 | -w- (write only) |
| 3 | 011 | -wx (write + execute) |
| 4 | 100 | r-- (read only) |
| 5 | 101 | r-x (read + execute) |
| 6 | 110 | rw- (read + write) |
| 7 | 111 | rwx (all permissions) |

**Common Permission Patterns:**

| Octal | Symbolic | Use Case |
|-------|----------|----------|
| 755 | rwxr-xr-x | Executable scripts/programs |
| 644 | rw-r--r-- | Regular files (documents) |
| 600 | rw------- | Private files (keys, configs) |
| 700 | rwx------ | Private scripts |
| 777 | rwxrwxrwx | World-writable (dangerous!) |
| 775 | rwxrwxr-x | Shared directories |
| 750 | rwxr-x--- | Group-accessible scripts |

**Symbolic Mode Operations:**

| Operator | Action |
|----------|--------|
| `+` | Add permission |
| `-` | Remove permission |
| `=` | Set exact permission |

**Examples:**

```bash
# Symbolic notation
chmod u+x script.sh          # Add execute for user
chmod g+w file.txt           # Add write for group
chmod o-r file.txt           # Remove read from others
chmod a+x script.sh          # Add execute for all
chmod +x script.sh           # Same as a+x (default)
chmod u=rw,go=r file.txt     # Set exact permissions
chmod u=rwx,g=rx,o= script.sh  # Owner full, group read/exec, others none

# Octal notation
chmod 755 script.sh          # rwxr-xr-x
chmod 644 document.txt       # rw-r--r--
chmod 600 private.key        # rw-------
chmod 700 secret/            # rwx------ (directory)
chmod 777 public/            # rwxrwxrwx (warning: unsafe)

# Recursive
chmod -R 755 /path/to/directory
chmod -R 644 *.txt           # All txt files

# Using reference file
chmod --reference=source.txt target.txt

# Set execute only if already executable (useful for X)
chmod a+X directory/         # Execute for directories
chmod -R a+X *               # Recursive with X

# Remove all permissions
chmod a= file.txt            # ----------

# Copy permission from one file to many
chmod --reference=template.txt *.txt
```

### 6. chown Command

The `chown` command changes file owner and group.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        CHOWN COMMAND SYNTAX                              │
├─────────────────────────────────────────────────────────────────────────┤
│ chown [OPTIONS] [OWNER][:[GROUP]] FILE...                               │
└─────────────────────────────────────────────────────────────────────────┘
```

**Examples:**

```bash
# Change owner only
chown user file.txt

# Change group only
chown :group file.txt

# Change both owner and group
chown user:group file.txt

# Recursive
chown -R user:group directory/

# Reference file
chown --reference=source.txt target.txt

# Verbose output
chown -v user file.txt
```

### 7. head and tail Commands

**head Command:**

```bash
head [OPTIONS] [FILE]...
```

| Option | Description |
|--------|-------------|
| `-n NUM` | Output first NUM lines |
| `-c NUM` | Output first NUM bytes |
| `-q` | Never print headers |
| `-v` | Always print headers |

**tail Command:**

```bash
tail [OPTIONS] [FILE]...
```

| Option | Description |
|--------|-------------|
| `-n NUM` | Output last NUM lines |
| `-c NUM` | Output last NUM bytes |
| `-f` | Follow mode (append data) |
| `-F` | Follow with file rotation |
| `-q` | Never print headers |
| `-v` | Always print headers |

**Examples:**

```bash
# Head examples
head file.txt              # First 10 lines
head -n 20 file.txt        # First 20 lines
head -5 file.txt           # First 5 lines (shorthand)
head -c 100 file.txt       # First 100 bytes
head -n -5 file.txt        # All except last 5 lines

# Tail examples
tail file.txt              # Last 10 lines
tail -n 20 file.txt        # Last 20 lines
tail -5 file.txt           # Last 5 lines (shorthand)
tail -c 100 file.txt       # Last 100 bytes
tail -n +5 file.txt        # Start from line 5 to end

# Follow mode (very useful for logs)
tail -f /var/log/app.log
tail -f -n 50 /var/log/app.log  # Last 50 lines then follow

# Follow multiple files
tail -f /var/log/*.log

# Multiple files
head file1.txt file2.txt
tail -n 5 file1.txt file2.txt

# Combine head and tail
head -100 file.txt | tail -20  # Lines 81-100
tail -100 file.txt | head -20  # Lines -100 to -81
```

### 8. wc, sort, uniq, diff Commands

**wc (Word Count):**

```bash
wc [OPTIONS] [FILE]...
```

| Option | Description |
|--------|-------------|
| `-l` | Lines only |
| `-w` | Words only |
| `-c` | Bytes only |
| `-m` | Characters only |
| `-L` | Longest line length |

**sort:**

```bash
sort [OPTIONS] [FILE]...
```

| Option | Description |
|--------|-------------|
| `-r` | Reverse order |
| `-n` | Numeric sort |
| `-h` | Human numeric (1K, 2M) |
| `-k N` | Sort by field N |
| `-t CHAR` | Field separator |
| `-u` | Unique only |
| `-f` | Case insensitive |
| `-V` | Version sort |
| `-o FILE` | Output to file |

**uniq:**

```bash
uniq [OPTIONS] [INPUT [OUTPUT]]
```

| Option | Description |
|--------|-------------|
| `-c` | Count occurrences |
| `-d` | Only duplicate lines |
| `-u` | Only unique lines |
| `-i` | Case insensitive |
| `-f N` | Skip first N fields |
| `-s N` | Skip first N characters |

**diff:**

```bash
diff [OPTIONS] FILE1 FILE2
```

| Option | Description |
|--------|-------------|
| `-y` | Side by side output |
| `-u` | Unified format |
| `-i` | Case insensitive |
| `-w` | Ignore whitespace |
| `-r` | Recursive for directories |
| `-q` | Brief (files differ only) |

**Examples:**

```bash
# wc examples
wc file.txt                # Lines, words, bytes
wc -l file.txt             # Lines only
wc -w file.txt             # Words only
wc -c file.txt             # Bytes only
wc -L file.txt             # Longest line length
wc *.txt                   # Count for multiple files
cat file.txt | wc -l       # Count lines from pipe

# sort examples
sort names.txt             # Alphabetical
sort -r names.txt          # Reverse alphabetical
sort -n numbers.txt        # Numeric sort
sort -h sizes.txt          # Human readable (1K, 2M, etc)
sort -u names.txt          # Unique sorted
sort -k 2 data.txt         # Sort by second field
sort -t ',' -k 2 csv.txt   # Sort CSV by second field
sort -V versions.txt       # Version sort (1.2, 1.10, 2.1)
sort -n -r numbers.txt     # Numeric reverse (highest first)
sort file.txt -o sorted.txt  # Output to file

# uniq examples
sort data.txt | uniq       # Unique lines (must sort first!)
sort data.txt | uniq -c    # Count occurrences
sort data.txt | uniq -d    # Only duplicates
sort data.txt | uniq -u    # Only unique lines
sort -i names.txt | uniq -i  # Case insensitive unique

# diff examples
diff file1.txt file2.txt   # Basic diff
diff -y file1.txt file2.txt  # Side by side
diff -u file1.txt file2.txt  # Unified format
diff -q dir1/ dir2/        # Brief directory comparison
diff -r dir1/ dir2/        # Recursive diff
diff -i file1.txt file2.txt  # Case insensitive

# Combining commands
sort data.txt | uniq -c | sort -rn  # Most common lines first
cat log.txt | grep "error" | wc -l   # Count errors
cut -d',' -f1 data.csv | sort | uniq  # Unique first column values
```

### 9. Redirection and Pipes

**Redirection Operators:**

| Operator | Description |
|----------|-------------|
| `>` | Redirect stdout to file (overwrite) |
| `>>` | Redirect stdout to file (append) |
| `<` | Redirect stdin from file |
| `2>` | Redirect stderr to file |
| `2>&1` | Redirect stderr to stdout |
| `&>` | Redirect both stdout and stderr |
| `|` | Pipe stdout to another command |
| `|&` | Pipe both stdout and stderr |

**File Descriptors:**

| FD | Name | Default |
|----|------|---------|
| 0 | stdin | Keyboard |
| 1 | stdout | Screen |
| 2 | stderr | Screen |

**Examples:**

```bash
# Output redirection
echo "Hello" > file.txt        # Create/overwrite file
echo "World" >> file.txt       # Append to file

# Input redirection
cat < file.txt                 # Read from file
wc -l < file.txt               # Count lines from file

# Error redirection
ls nonexistent 2> errors.txt   # Redirect errors to file
ls /root 2>/dev/null           # Discard error messages

# Redirect both stdout and stderr
command &> output.txt
command > output.txt 2>&1      # Older syntax

# Pipes
cat file.txt | grep "pattern"
ls -la | grep ".txt" | wc -l
ps aux | grep python
history | grep "git"
find . -name "*.txt" | wc -l
cat log.txt | sort | uniq -c | sort -rn

# Here document (multiline input)
cat << 'EOF' > script.sh
#!/bin/bash
echo "Hello World"
echo "This is a test"
EOF

# Here string (single line)
grep "pattern" <<< "search in this string"

# Named pipes (advanced)
mkfifo mypipe
command1 > mypipe &
command2 < mypipe

# Process substitution
diff <(sort file1.txt) <(sort file2.txt)

# Tee - output to both file and screen
command | tee output.txt
command | tee -a output.txt    # Append mode

# Multiple redirections
command 2>&1 | tee log.txt     # Log everything
```

---

## 📋 COMMANDS REFERENCE

### Quick Reference Table (25+ Commands)

```bash
# ═══════════════════════════════════════════════════════════════════════
# CAT COMMAND
# ═══════════════════════════════════════════════════════════════════════
cat file.txt                    # View file content
cat -n file.txt                 # View with line numbers
cat -b file.txt                 # Number non-blank lines
cat file1.txt file2.txt         # View multiple files
cat file1.txt file2.txt > merged.txt  # Concatenate files
cat > newfile.txt               # Create file from input (Ctrl+D to save)
cat >> file.txt                 # Append to file from input
cat -s file.txt                 # Squeeze blank lines

# ═══════════════════════════════════════════════════════════════════════
# TOUCH COMMAND
# ═══════════════════════════════════════════════════════════════════════
touch file.txt                  # Create empty file / update timestamp
touch file1.txt file2.txt file3.txt  # Create multiple files
touch -d "2024-01-15" file.txt  # Set specific date
touch -t 202401151200 file.txt  # Set specific timestamp
touch -r source.txt target.txt  # Copy timestamps from another file
touch -a file.txt               # Update access time only
touch -m file.txt               # Update modification time only

# ═══════════════════════════════════════════════════════════════════════
# GREP COMMAND
# ═══════════════════════════════════════════════════════════════════════
grep "pattern" file.txt         # Basic search
grep -i "pattern" file.txt      # Case insensitive
grep -n "pattern" file.txt      # Show line numbers
grep -v "pattern" file.txt      # Invert match (exclude)
grep -r "pattern" directory/    # Recursive search
grep -l "pattern" *.txt         # Show filenames only
grep -c "pattern" file.txt      # Count matches
grep -w "word" file.txt         # Whole word match
grep -E "pattern1|pattern2" file.txt  # Multiple patterns (OR)
grep -A 3 "pattern" file.txt    # Show 3 lines after match
grep -B 3 "pattern" file.txt    # Show 3 lines before match
grep -C 3 "pattern" file.txt    # Show 3 lines around match
grep --color=auto "pattern" file.txt  # Highlight matches

# ═══════════════════════════════════════════════════════════════════════
# FIND COMMAND
# ═══════════════════════════════════════════════════════════════════════
find . -name "file.txt"         # Find by name
find . -iname "file.txt"        # Find by name (case insensitive)
find . -type f                  # Find files only
find . -type d                  # Find directories only
find . -name "*.txt"            # Find all txt files
find . -size +1M                # Find files larger than 1MB
find . -size -100k              # Find files smaller than 100KB
find . -mtime -7                # Modified in last 7 days
find . -mmin -60                # Modified in last 60 minutes
find . -empty                   # Find empty files/directories
find . -perm 755                # Find by permission
find . -executable              # Find executable files
find . -name "*.log" -delete    # Find and delete
find . -name "*.txt" -exec cat {} \;  # Execute command on results

# ═══════════════════════════════════════════════════════════════════════
# CHMOD COMMAND
# ═══════════════════════════════════════════════════════════════════════
chmod 755 script.sh             # rwxr-xr-x (executable)
chmod 644 file.txt              # rw-r--r-- (readable)
chmod 600 private.key           # rw------- (private)
chmod 700 directory/            # rwx------ (private directory)
chmod +x script.sh              # Add execute permission
chmod -x script.sh              # Remove execute permission
chmod u+x script.sh             # Add execute for user
chmod g+w file.txt              # Add write for group
chmod o-r file.txt              # Remove read from others
chmod a+r file.txt              # Add read for all
chmod -R 755 directory/         # Recursive permission change

# ═══════════════════════════════════════════════════════════════════════
# CHOWN COMMAND
# ═══════════════════════════════════════════════════════════════════════
chown user file.txt             # Change owner
chown :group file.txt           # Change group
chown user:group file.txt       # Change owner and group
chown -R user:group directory/  # Recursive change

# ═══════════════════════════════════════════════════════════════════════
# HEAD AND TAIL
# ═══════════════════════════════════════════════════════════════════════
head file.txt                   # First 10 lines
head -n 20 file.txt             # First 20 lines
head -5 file.txt                # First 5 lines
tail file.txt                   # Last 10 lines
tail -n 20 file.txt             # Last 20 lines
tail -5 file.txt                # Last 5 lines
tail -f logfile.txt             # Follow file (live updates)
tail -f -n 50 logfile.txt       # Last 50 lines then follow

# ═══════════════════════════════════════════════════════════════════════
# WC, SORT, UNIQ, DIFF
# ═══════════════════════════════════════════════════════════════════════
wc file.txt                     # Lines, words, bytes
wc -l file.txt                  # Lines only
wc -w file.txt                  # Words only
wc -c file.txt                  # Bytes only
sort file.txt                   # Alphabetical sort
sort -r file.txt                # Reverse sort
sort -n numbers.txt             # Numeric sort
sort -u file.txt                # Unique sorted
sort file.txt | uniq            # Unique lines
sort file.txt | uniq -c         # Count occurrences
sort file.txt | uniq -d         # Duplicates only
diff file1.txt file2.txt        # Compare files
diff -y file1.txt file2.txt     # Side by side comparison
diff -u file1.txt file2.txt     # Unified format

# ═══════════════════════════════════════════════════════════════════════
# REDIRECTION AND PIPES
# ═══════════════════════════════════════════════════════════════════════
command > file.txt              # Redirect output to file (overwrite)
command >> file.txt             # Redirect output to file (append)
command < file.txt              # Redirect input from file
command 2> errors.txt           # Redirect stderr
command &> output.txt           # Redirect stdout and stderr
command1 | command2             # Pipe output to another command
command | tee output.txt        # Output to file and screen
cat file.txt | grep "pattern"   # Chain commands with pipe
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: File Content Analysis

```bash
# Task: Create a sample data file and analyze it

# Step 1: Create sample data file
cat > employees.txt << 'EOF'
101,John Doe,Engineering,75000
102,Jane Smith,Marketing,65000
103,Bob Johnson,Engineering,80000
104,Alice Brown,HR,55000
105,Charlie Wilson,Engineering,72000
106,Diana Davis,Marketing,68000
107,Edward Miller,HR,52000
108,Fiona Garcia,Engineering,85000
EOF

# Step 2: Count total lines
wc -l employees.txt

# Step 3: Find all Engineering employees
grep "Engineering" employees.txt

# Step 4: Count employees per department
cut -d',' -f3 employees.txt | sort | uniq -c

# Step 5: Find highest salary (bonus challenge)
sort -t',' -k4 -nr employees.txt | head -1

# Step 6: Extract employee names only
cut -d',' -f2 employees.txt

# Step 7: Find employees with salary above 70000
awk -F',' '$4 > 70000' employees.txt

# Expected: Understanding of text processing
```

### Exercise 2: Permission Management

```bash
# Task: Set up proper file permissions for a project

# Step 1: Create project structure
mkdir -p myproject/{bin,docs,configs}

# Step 2: Create sample files
touch myproject/bin/app.sh
touch myproject/bin/setup.sh
touch myproject/docs/readme.txt
touch myproject/configs/settings.conf
echo "#!/bin/bash" > myproject/bin/app.sh
echo "echo 'Hello World'" >> myproject/bin/app.sh

# Step 3: Check current permissions
ls -laR myproject/

# Step 4: Make scripts executable
chmod +x myproject/bin/*.sh

# Step 5: Make configs readable only by owner
chmod 600 myproject/configs/*.conf

# Step 6: Make docs readable by all
chmod 644 myproject/docs/*.txt

# Step 7: Make directories accessible
chmod 755 myproject myproject/*

# Step 8: Verify permissions
ls -laR myproject/

# Expected: Proper permission structure
```

### Exercise 3: Log File Analysis

```bash
# Task: Analyze a sample log file

# Step 1: Create sample log file
cat > server.log << 'EOF'
2024-01-15 08:00:01 INFO Server started
2024-01-15 08:00:05 INFO Loading configuration
2024-01-15 08:00:10 ERROR Database connection failed
2024-01-15 08:00:15 INFO Retrying database connection
2024-01-15 08:00:20 INFO Database connected
2024-01-15 08:01:00 WARNING High memory usage
2024-01-15 08:02:00 ERROR Request timeout
2024-01-15 08:02:30 INFO Request processed
2024-01-15 08:03:00 ERROR Authentication failed
2024-01-15 08:03:30 WARNING Slow response time
2024-01-15 08:04:00 INFO User logged in
2024-01-15 08:05:00 ERROR File not found
2024-01-15 08:05:30 INFO Cleanup completed
EOF

# Step 2: Count total lines
wc -l server.log

# Step 3: Count errors
grep -c "ERROR" server.log

# Step 4: Show all errors with line numbers
grep -n "ERROR" server.log

# Step 5: Show errors and warnings
grep -E "ERROR|WARNING" server.log

# Step 6: Show 2 lines after each error
grep -A 2 "ERROR" server.log

# Step 7: Count by log level
grep -o "INFO\|ERROR\|WARNING" server.log | sort | uniq -c

# Step 8: View first 5 and last 5 lines
head -5 server.log
tail -5 server.log

# Expected: Log analysis skills
```

### Exercise 4: Find and Organize

```bash
# Task: Find and organize files by type

# Step 1: Create test structure
mkdir -p fileorg/{images,docs,scripts,logs}
touch fileorg/images/{photo1.jpg,photo2.png,logo.gif}
touch fileorg/docs/{report.txt,notes.md,readme.txt}
touch fileorg/scripts/{backup.sh,deploy.py,test.sh}
touch fileorg/logs/{error.log,access.log,debug.log}
touch fileorg/misc.txt fileorg/temp.log fileorg/config.json

# Step 2: Find all shell scripts
find fileorg -name "*.sh"

# Step 3: Find all image files
find fileorg -name "*.jpg" -o -name "*.png" -o -name "*.gif"

# Step 4: Find all files modified today
find fileorg -mtime -1

# Step 5: Count files per extension
find fileorg -type f | sed 's/.*\.//' | sort | uniq -c

# Step 6: Find empty directories
find fileorg -type d -empty

# Step 7: Find and list all log files
find fileorg -name "*.log" -exec ls -la {} \;

# Step 8: Find files larger than 0 bytes
find fileorg -type f -size +0

# Expected: File finding skills
```

### Exercise 5: Redirection and Pipes Mastery

```bash
# Task: Master command chaining

# Step 1: Create sample data
for i in {1..100}; do
    echo "Line $i: $(head /dev/urandom | tr -dc 'a-zA-Z0-9' | head -c 20)"
done > bigdata.txt

# Step 2: View first 10 lines
head bigdata.txt

# Step 3: Count lines containing "Line 5"
grep "Line 5" bigdata.txt | wc -l

# Step 4: Extract line numbers only
grep -o "Line [0-9]*" bigdata.txt | cut -d' ' -f2

# Step 5: Save lines 50-60 to separate file
sed -n '50,60p' bigdata.txt > excerpt.txt

# Step 6: Create sorted unique first words list
cat bigdata.txt | cut -d' ' -f1 | sort | uniq

# Step 7: Find lines with specific pattern and count
grep -c "Line [0-9][0-9]:" bigdata.txt

# Step 8: Combine multiple operations
cat bigdata.txt | grep "Line 1" | sort | head -5 | tee results.txt

# Step 9: Use process substitution
diff <(head -20 bigdata.txt) <(tail -20 bigdata.txt)

# Step 10: Clean up
rm -f bigdata.txt excerpt.txt results.txt

# Expected: Advanced command chaining
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Permission Denied

```bash
# Error: bash: ./script.sh: Permission denied

# Cause: File is not executable

# Solution 1: Add execute permission
chmod +x script.sh

# Solution 2: Run with interpreter
bash script.sh
python script.py

# Solution 3: Check current permissions
ls -la script.sh

# Verify with
./script.sh
```

### Problem 2: grep Command Not Finding Pattern

```bash
# Error: No output when pattern exists

# Cause: Case sensitivity or wrong file

# Solution 1: Use case insensitive
grep -i "pattern" file.txt

# Solution 2: Verify file content
cat file.txt

# Solution 3: Check for hidden characters
cat -A file.txt

# Solution 4: Use extended regex
grep -E "pattern1|pattern2" file.txt
```

### Problem 3: find Command Too Slow

```bash
# Error: find taking very long

# Cause: Searching entire filesystem or many files

# Solution 1: Limit search depth
find . -maxdepth 3 -name "*.txt"

# Solution 2: Use specific path
find /specific/path -name "*.txt"

# Solution 3: Combine with grep (faster for content)
grep -r "pattern" --include="*.txt" .

# Solution 4: Exclude directories
find . -name "*.txt" -not -path "*/\.*"
```

### Problem 4: Redirection Overwrites Important File

```bash
# Error: Accidentally overwrote file with >

# Prevention:
# Use >> for append instead of >
# Use set -o noclobber in bash to prevent overwriting

# Recovery attempts:
# Check for backup
ls -la filename.bak
ls -la filename~

# Check git if in repo
git checkout -- filename

# Check Termux backup if exists
ls ~/storage/downloads/backup/

# Enable noclobber to prevent future accidents
set -o noclobber
# Now > will fail if file exists
# Use >| to force overwrite
```

### Problem 5: chown Operation Not Permitted

```bash
# Error: chown: changing ownership: Operation not permitted

# Cause: Not running as root

# In Termux without root:
# You ARE the owner of files you create
# chown is limited

# Solution 1: Check current owner
ls -la file.txt

# Solution 2: Use chmod instead for permissions
chmod 755 file.txt

# Solution 3: If root access needed
# Use tools like tsu (Termux su) or run with root
pkg install tsu
tsudo chown user:group file.txt
```

### Problem 6: tail -f Not Following New File

```bash
# Error: tail -f shows old content, not new

# Cause: File rotation or buffering

# Solution 1: Use -F instead of -f
tail -F logfile.txt

# -F handles file rotation (logrotate)

# Solution 2: Use less +F
less +F logfile.txt
# Press Ctrl+C to pause, F to resume, q to quit

# Solution 3: Check if file exists
ls -la logfile.txt

# Solution 4: Combine with grep
tail -f logfile.txt | grep --line-buffered "pattern"
```

### Problem 7: sort Not Sorting Numbers Correctly

```bash
# Error: Numbers sorted alphabetically (1, 10, 2, 20 instead of 1, 2, 10, 20)

# Cause: Using default sort instead of numeric

# Wrong:
sort numbers.txt
# Output: 1, 10, 2, 20

# Correct:
sort -n numbers.txt
# Output: 1, 2, 10, 20

# For human-readable sizes:
sort -h sizes.txt
# Output: 1K, 2M, 1G in correct order

# For reverse numeric:
sort -rn numbers.txt
# Output: 20, 10, 2, 1
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Command Showcase**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   LINUX BASICS - PART 2            │
│   ─────────────────────            │
│   grep | find | chmod              │
│   cat | touch | pipes              │
│                                    │
│   🔥 10+ COMMANDS!                 │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Focus on grep**
```
┌────────────────────────────────────┐
│  [Green on Black Terminal]         │
│                                    │
│   $ grep "secret" files/           │
│   found: 24 matches                │
│                                    │
│   🔍 MASTER GREP & FIND            │
│                                    │
│   Chapter 4 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Permissions Focus**
```
┌────────────────────────────────────┐
│  [Split Design]                    │
│                                    │
│  chmod 777 ❌  │  chmod 755 ✅      │
│  ──────────────┼─────────────────  │
│  Dangerous!    │  Safe!            │
│                                    │
│  PERMISSIONS MASTERCLASS           │
│  Chapter 4 | T3rmuxk1ng            │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📱 Termux Full Course - Chapter 4: Linux Basics Part 2 | Files, Permissions & Text Processing

🔥 In this video you'll learn:
• cat command - View, create, concatenate files
• touch command - Create empty files
• grep command - Powerful text search
• find command - Search for files
• chmod command - Manage permissions
• head, tail, wc, sort, uniq, diff
• Redirection and pipes - Command chaining

⏱️ Timestamps:
0:00 - Introduction
0:45 - cat Command
4:00 - touch Command
5:30 - grep Command (Text Search)
9:00 - find Command (File Search)
12:00 - chmod Command (Permissions)
15:00 - chown Command (Ownership)
16:00 - head and tail Commands
17:30 - wc, sort, uniq, diff
19:30 - Redirection and Pipes
21:30 - Summary

📝 Commands from this video:
cat file.txt
touch newfile.txt
grep -r "pattern" directory/
find . -name "*.txt"
chmod 755 script.sh
tail -f logfile.txt
command1 | command2

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #LinuxBasics #grep #chmod #LinuxCommands #T3rmuxk1ng #TermuxCourse #TerminalCommands #LinuxForBeginners

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux, termux tutorial, termux course, linux basics, 
linux commands, grep command, find command, chmod command,
cat command, touch command, linux permissions, 
text processing linux, pipes linux, redirection linux,
head tail commands, wc command, sort command, 
termux hindi, termux tutorial hindi, linux for beginners,
terminal commands, command line, t3rmuxk1ng,
termux course hindi, android terminal, linux on android
```

### Hashtags

```
#Termux #LinuxBasics #LinuxCommands #grep #chmod #TermuxTutorial 
#Commandline #LinuxForBeginners #TerminalCommands #T3rmuxk1ng 
#TermuxHindi #TermuxCourse #TextProcessing #LinuxPermissions
```

---

## 📚 ADDITIONAL RESOURCES

### Command Manuals

```bash
# View manual pages (install man first)
pkg install man -y

man cat
man grep
man find
man chmod

# Quick help
grep --help
find --help
chmod --help
```

### Online Resources

| Resource | Link |
|----------|------|
| GNU grep Manual | https://www.gnu.org/software/grep/manual/ |
| GNU find Manual | https://www.gnu.org/software/findutils/manual/ |
| chmod Calculator | https://chmod-calculator.com/ |
| Regex Tester | https://regex101.com/ |
| Linux Command Library | https://linuxcommandlibrary.com/ |

### Quick Reference Cards

**grep Options:**
```
-i = ignore case
-v = invert match
-n = line numbers
-r = recursive
-l = filenames only
-c = count matches
-w = whole word
-E = extended regex
```

**chmod Octal:**
```
7 = rwx (4+2+1)
6 = rw- (4+2+0)
5 = r-x (4+0+1)
4 = r-- (4+0+0)
0 = --- (0+0+0)

Common: 755, 644, 600, 700
```

**find Options:**
```
-name = by filename
-type f/d = file/directory
-size +N/-N = larger/smaller
-mtime +/-N = days
-exec {} \; = execute command
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 5, verify:

- [ ] Understand cat for viewing and creating files
- [ ] Can create files with touch
- [ ] Mastered basic grep searches
- [ ] Know grep options: -i, -r, -n, -v
- [ ] Can find files by name and type
- [ ] Understand find options: -name, -type, -size, -mtime
- [ ] Understand file permissions (r, w, x)
- [ ] Can use chmod with octal (755, 644, etc.)
- [ ] Can use chmod with symbolic (u+x, g-w)
- [ ] Know head and tail commands
- [ ] Understand tail -f for live monitoring
- [ ] Can use wc, sort, uniq, diff
- [ ] Understand redirection: >, >>, <
- [ ] Can chain commands with pipes |
- [ ] Completed all practice exercises

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 5: Package Management**

- Understanding pkg and apt
- Installing, updating, removing packages
- Repository management
- Finding packages with pkg search
- Handling dependencies
- Package troubleshooting

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
