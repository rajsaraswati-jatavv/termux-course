# Chapter 15: Git & Version Control in Termux

> **Module:** 3 - Programming  
> **Chapter:** 15 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed Git concepts and workflows |
| Installation Guide | Git setup in Termux |
| Commands Reference | 25+ Git commands with examples |
| Practice Exercises | Create and push repository |
| Troubleshooting | Common Git issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 15
Title: Git Version Control in Termux | Complete Guide | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - Git Version Control!

Agar aap developer banne chahte ho, ya ethical hacker, ya koi bhi 
technical field mein jaana chahte ho - Git aapke liye essential skill 
hai. Bina Git ke aap real-world projects mein kaam hi nahi kar sakte.

Ye aisi cheez hai jo har interview mein puchi jaati hai, har job 
requirement mein hoti hai, aur har developer use karta hai.

Aaj hum seekhenge:
- Git kya hai aur kyun important hai
- Termux mein Git install karna
- Local repositories create karna
- GitHub ke saath integrate karna
- SSH keys setup karna
- Branching, merging, conflicts handle karna
- Aur bahut kuch!

To bina time waste kiye, chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein.

---

[SECTION 1: GIT INTRODUCTION - 0:50 to 4:00]
─────────────────────────────────────────────────────────────────────────────

To sabse pehle sawal - Git kya hai?

Git ek distributed version control system hai. Simple shabdon mein 
samjhein - ye aapke code ka time machine hai!

Jab aap coding karte ho, to bahut saare changes aate hain. Aaj aapne 
ek feature add kiya, kal bug fix kiya, parso design change kiya. 
Agar kuch galat ho gaya to kya? Code kharab, project crash!

Yahan Git madad karta hai. Git har ek change ko track karta hai. 
Aap kabhi bhi purana version dekh sakte ho, wapas ja sakte ho, 
compare kar sakte ho.

Git ke main features:

✓ Version History - Har change ka record
✓ Collaboration - Multiple log saath mein kaam kar sakte hain
✓ Branches - Alag-alag versions parallel mein develop karo
✓ Backup - Code cloud mein safe rahega
✓ Rollback - Galti ho to wapas jao

Real-world example samjhein:

Imagine karo aap ek website bana rahe ho. Din 1 pe aapne login page 
banaya. Din 2 pe dashboard banaya. Din 3 pe aapne login page change 
kiya aur... sab tod diya! Website crash!

Without Git: Panic! Kya change kiya? Kaise fix karein? Pata hi nahi!
With Git: Git log dekho, dekho kya change kiya, purana version 
restore karo, problem solved!

Isliye Git developers ke liye boon hai.

---

[SECTION 2: GIT INSTALLATION - 4:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ab Termux mein Git install karte hain.

Installation bahut simple hai - ek command:

    pkg install git -y

[SCREEN: Git installation]

Ye command Git package download aur install kar degi. Thoda time 
lagega, internet speed pe depend karta hai.

Installation ke baad verify karein:

    git --version

Output kuch aisa aana chahiye:
git version 2.x.x

Agar version dikha raha hai, Git successfully install ho gaya!

Ab Git ko configure karna hai - aapki identity.

Git ko pata hona chahiye ki aap kaun ho. Ye information har commit 
ke saath store hoti hai.

    git config --global user.name "Aapka Name"
    git config --global user.email "aapka@email.com"

Example:

    git config --global user.name "T3rmuxk1ng"
    git config --global user.email "t3rmuxk1ng@example.com"

Ye globally set ho gaya - ab har repository mein ye hi use hoga.

Verify karein:

    git config --global user.name
    git config --global user.email

Output mein aapka name aur email dikhega.

---

[SECTION 3: CREATING REPOSITORY - 6:00 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Ab hum seekhte hain repository kaise create karte hain.

Repository ya repo - basically ek folder hai jo Git track karta hai.

[STEP 1: Create New Repository]

Pehle ek folder banao:

    mkdir my-first-repo
    cd my-first-repo

Ab Git initialize karo:

    git init

Output: Initialized empty Git repository in /data/data/com.termux/files/home/my-first-repo/.git/

Ye command ek hidden .git folder banati hai. Is folder mein Git 
apna saara data store karta hai - history, branches, configurations.

Check karein:

    ls -la

Dikhega: .git folder

[STEP 2: Clone Existing Repository]

Agar koi existing repository download karni hai GitHub se:

    git clone <repository-url>

Example:

    git clone https://github.com/username/repo-name.git

Ye command repository download karke local folder banati hai.

    git clone https://github.com/t3rmuxk1ng/tools.git

Isse 'tools' naam ka folder banega us repository ka content.

[STEP 3: Repository Status]

Har time check kar sakte ho ki repository ka state kya hai:

    git status

Ye command batati hai:
- Kaunsi files modified hain
- Kaunsi files staged hain
- Kaunsi files untracked hain
- Current branch kaunsi hai

---

[SECTION 4: BASIC GIT WORKFLOW - 9:00 to 13:00]
─────────────────────────────────────────────────────────────────────────────

Ab hum seekhte hain basic Git workflow - add, commit, push, pull.

[WORKFLOW DIAGRAM]

Working Directory → Staging Area → Local Repository → Remote Repository

Ye cycle hai Git ka. Samjhein step by step.

[STEP 1: Create/Modify Files]

Pehle kuch files banao:

    echo "# My First Repo" > README.md
    echo "print('Hello Git!')" > hello.py

Ab check karo status:

    git status

Output mein dikhega:
Untracked files: README.md, hello.py

Matlab Git jaanta hai ye files hain, lekin track nahi kar raha.

[STEP 2: Stage Files - git add]

Files ko staging area mein laao:

    git add README.md

Ye single file add karta hai.

    git add .

Ye SAARI files add karta hai current directory ki.

    git add -A

Ye SAARI files add karta hai poore repository ki.

Ab status check karo:

    git status

Dikhega:
Changes to be committed:
  new file: README.md
  new file: hello.py

Green color mein - matlab staged!

[STEP 3: Commit Changes - git commit]

Staged files ko commit karo - ye history mein save ho jaate hain:

    git commit -m "Initial commit: Added README and hello.py"

-m flag message ke liye hai. Hamesha meaningful message likhein.

Ab check karo:

    git status

Output: nothing to commit, working tree clean

Aur dekho history:

    git log

Dikhega commit ka details - author, date, message, hash.

[STEP 4: View History - git log]

git log ka different formats:

    git log              # Full details
    git log --oneline    # One line per commit
    git log --oneline -5 # Last 5 commits
    git log -p           # With patch/diff

[STEP 5: View Changes - git diff]

Agar file mein change kiya:

    echo "## More content" >> README.md

Ab diff dekho:

    git diff

Ye modified files ka difference dikhata hai.

Staged files ka diff:

    git diff --staged

---

[SECTION 5: REMOTE REPOSITORIES - 13:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Ab hum seekhte hain GitHub ke saath kaise kaam karte hain.

GitHub ek cloud platform hai jahan aap apne repositories store kar 
sakte ho. Public free hai, private bhi free hai.

[STEP 1: Create GitHub Account]

GitHub.com pe jao, sign up karo free account ke liye.

[STEP 2: Create Remote Repository]

GitHub pe new repository create karo:
1. "+" button click karo
2. "New repository" select karo
3. Repository name do
4. Public ya Private choose karo
5. "Create repository" click karo

[STEP 3: Connect Local to Remote]

Terminal mein aao, remote add karo:

    git remote add origin https://github.com/username/repo-name.git

'origin' ek name hai - default convention hai. Aap kuch bhi rakh sakte ho.

Check remotes:

    git remote -v

[STEP 4: Push to Remote]

Local commits ko remote pe bhejo:

    git push -u origin main

-u flag upstream set karta hai - future mein sirf 'git push' chalega.

Pehli baar GitHub username aur password ya token maange ga.

NOTE: Password deprecated hai, Personal Access Token use karna padega.

[STEP 5: Pull from Remote]

Remote se latest changes lao:

    git pull origin main

Ya agar upstream set hai:

    git pull

---

[SECTION 6: SSH KEYS FOR GITHUB - 16:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

Har baar password/token daarna boring hai. SSH keys use karo!

SSH key ek secure pair hai - public aur private. Public GitHub pe 
rakhenge, private aapke phone pe. Authentication automatic ho jaati hai.

[STEP 1: Generate SSH Key]

    ssh-keygen -t ed25519 -C "aapka@email.com"

-t: key type (ed25519 is modern and secure)
-C: comment (usually email)

Press Enter for default location.

Passphrase daal sakte ho ya blank rehne do (less secure but convenient).

[STEP 2: View Public Key]

    cat ~/.ssh/id_ed25519.pub

Ye output copy karo - pura content!

[STEP 3: Add to GitHub]

1. GitHub pe jao
2. Settings → SSH and GPG keys
3. "New SSH key" click karo
4. Title do (e.g., "Termux")
5. Key paste karo
6. "Add SSH key" click karo

[STEP 4: Test SSH Connection]

    ssh -T git@github.com

Output: Hi username! You've successfully authenticated...

[STEP 5: Clone/Push with SSH]

SSH URL use karo:

    git clone git@github.com:username/repo.git

Remote URL change karo existing repo mein:

    git remote set-url origin git@github.com:username/repo.git

Ab push karo - no password needed!

    git push

---

[SECTION 7: BRANCHING & MERGING - 19:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Branching Git ki sabse powerful feature hai!

Main branch hoti hai - usually 'main' ya 'master'. Ye production 
code hoti hai.

New features ke liye naye branches banao, work karo, jab ready ho 
to merge kar do.

[CREATE BRANCH]

    git branch feature-login

Ye new branch banata hai lekin switch nahi karta.

[SWITCH BRANCH]

    git checkout feature-login

Ya create aur switch ek saath:

    git checkout -b feature-login

[LIST BRANCHES]

    git branch

Current branch * se mark hoga.

[WORK ON BRANCH]

    echo "# Login Feature" > login.py
    git add login.py
    git commit -m "Added login feature"

[SWITCH BACK TO MAIN]

    git checkout main

[MERGE BRANCH]

    git merge feature-login

Ye feature-login branch ko main mein merge kar dega.

[DELETE BRANCH]

    git branch -d feature-login

---

[SECTION 8: MERGE CONFLICTS - 22:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Kabhi-kabhi merge conflict ho jaate hain.

Conflict tab hota hai jab same line different branches mein alag-alag 
change ki gayi ho.

Example:

Main branch mein:
print("Hello")

Feature branch mein:
print("Hi")

Jab merge karoge, conflict aayega.

[CONFLICT MARKERS]

Git file mein markers daal deta hai:

<<<<<<< HEAD
print("Hello")
=======
print("Hi")
>>>>>>> feature-branch

[RESOLUTION]

Manually edit karo:

print("Hello")  # ya jo chahiye wo rakho

Phir:

    git add filename
    git commit -m "Resolved merge conflict"

[ABORT MERGE]

Agar conflict resolve nahi karna:

    git merge --abort

---

[SECTION 9: GIT STASH & TAGS - 24:00 to 26:00]
─────────────────────────────────────────────────────────────────────────────

[GIT STASH]

Kabhi-kabhi aap kaam kar rahe ho, aur suddenly kisi aur branch pe 
jana hai. Changes commit nahi karna, lekin save bhi karna hai.

Stash use karo!

    git stash

Ye changes temporarily save kar leta hai.

    git stash list

Stash dekho.

    git stash pop

Stash wapas lao.

[GIT TAGS]

Tags releases mark karne ke liye use hote hain.

    git tag v1.0.0

Lightweight tag.

    git tag -a v1.0.0 -m "Version 1.0.0 Release"

Annotated tag with message.

Tags push karo:

    git push origin v1.0.0
    git push origin --tags  # All tags

---

[SECTION 10: GITHUB CLI (gh) - 26:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

Termux mein GitHub CLI bhi install kar sakte ho!

    pkg install gh

Authentication:

    gh auth login

Interactive process hai - GitHub.com select karo, SSH ya HTTPS, 
browser ya token.

Useful commands:

    gh repo create          # Create new repo
    gh repo clone           # Clone repo
    gh repo list            # List your repos
    gh issue create         # Create issue
    gh pr create            # Create pull request
    gh pr list              # List PRs

Bohot powerful tool hai - GitHub ka sab kuch terminal se!

---

[SECTION 11: .gitignore FILE - 28:00 to 29:30]
─────────────────────────────────────────────────────────────────────────────

.gitignore file batati hai Git ko kaunsi files ignore karni hain.

Example:

    # .gitignore file
    *.pyc           # Python compiled files
    __pycache__/    # Python cache folder
    node_modules/   # Node.js dependencies
    .env            # Environment variables
    *.log           # Log files
    secrets.txt     # Sensitive file

Create karo:

    nano .gitignore

Patterns likho, save karo.

Ab ye files kabhi track nahi hongi!

---

[SECTION 12: SUMMARY - 29:30 to 31:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 15 complete! Let's summarize:

✅ Git kya hai - Version Control System, code ka time machine
✅ Git installation - pkg install git
✅ Configuration - user.name aur user.email
✅ Repository creation - git init, git clone
✅ Basic workflow - add, commit, push, pull
✅ Remote repositories - GitHub integration
✅ SSH keys - Secure passwordless authentication
✅ Branching - Create, switch, merge, delete
✅ Merge conflicts - Resolution techniques
✅ Git stash - Temporary save
✅ Git tags - Release management
✅ GitHub CLI - gh commands
✅ .gitignore - Ignore unwanted files

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 15 - ESSENTIAL GIT COMMANDS                   │
├─────────────────────────────────────────────────────────────────────────┤
│ git init                  │ Initialize new repository                    │
│ git clone <url>           │ Clone existing repository                    │
│ git add .                 │ Stage all changes                            │
│ git commit -m "message"   │ Commit changes with message                  │
│ git push                  │ Push to remote                               │
│ git pull                  │ Pull from remote                             │
│ git status                │ Check repository status                      │
│ git log --oneline         │ View commit history                          │
│ git branch <name>         │ Create new branch                            │
│ git checkout <branch>     │ Switch branch                                │
│ git merge <branch>        │ Merge branch                                 │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 16 mein hum seekhenge:
- Node.js installation in Termux
- JavaScript runtime
- NPM package manager
- Building Node.js applications

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 16!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Git Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         GIT ARCHITECTURE                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Remote Repository (GitHub/GitLab)            │   │
│   │   - Central server storage                                       │   │
│   │   - Collaboration hub                                            │   │
│   │   - Backup location                                              │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                          git push │ git pull                             │
│                                   │                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Local Repository (.git folder)               │   │
│   │   - Full history                                                 │   │
│   │   - All branches                                                 │   │
│   │   - Complete object database                                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                          git commit                                      │
│                                   │                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Staging Area (Index)                         │   │
│   │   - Prepared changes                                             │   │
│   │   - Next commit content                                          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                          git add                                         │
│                                   │                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Working Directory                            │   │
│   │   - Actual files                                                 │   │
│   │   - Your workspace                                               │   │
│   │   - Current edits                                                │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Git Object Model

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         GIT OBJECT TYPES                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   BLOB (Binary Large Object)                                             │
│   ├── Stores file content                                                │
│   ├── Identified by SHA-1 hash                                           │
│   └── Compressed using zlib                                              │
│                                                                          │
│   TREE                                                                   │
│   ├── Stores directory structure                                         │
│   ├── References blobs and other trees                                   │
│   └── Contains file names and permissions                                │
│                                                                          │
│   COMMIT                                                                 │
│   ├── Points to a tree                                                   │
│   ├── Contains parent commit(s)                                          │
│   ├── Includes author, committer, message                                │
│   └── Identified by SHA-1 hash                                           │
│                                                                          │
│   TAG                                                                    │
│   ├── Named reference to a commit                                        │
│   ├── Can include message and tagger info                                │
│   └── Used for releases                                                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Branching Model

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      GIT BRANCHING WORKFLOW                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   main ──────●────────●────────●────────●──────→                        │
│               \              /                                           │
│                \            /                                            │
│   feature ─────●──────────●──────→                                       │
│                                                                          │
│   Steps:                                                                 │
│   1. Create branch from main                                             │
│   2. Work on feature branch                                              │
│   3. Make commits                                                        │
│   4. Merge back to main                                                  │
│                                                                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Git Flow Model:                                                        │
│                                                                          │
│   main ────────●────────────●────────────●──────→ (Production)          │
│                 \           /                                            │
│   develop ───────●────●────●────●────●───→ (Development)                │
│                   \   /         /                                        │
│   feature ─────────●──────────/───→ (Feature branches)                  │
│                                                                          │
│   main: Production-ready code                                            │
│   develop: Integration branch                                            │
│   feature/*: New features                                                │
│   hotfix/*: Emergency fixes                                              │
│   release/*: Release preparation                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. SSH Key Authentication Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SSH AUTHENTICATION FLOW                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   [Your Device]                          [GitHub Server]                 │
│                                                                          │
│   ┌─────────────┐                        ┌─────────────┐                │
│   │ Private Key │                        │ Public Key  │                │
│   │ (id_ed25519)│                        │ (deployed)  │                │
│   └──────┬──────┘                        └──────┬──────┘                │
│          │                                      │                        │
│          │    1. Connection Request              │                        │
│          │ ─────────────────────────────────►   │                        │
│          │                                      │                        │
│          │    2. Challenge (random string)       │                        │
│          │ ◄─────────────────────────────────   │                        │
│          │                                      │                        │
│          │    3. Signed Response                 │                        │
│          │ ─────────────────────────────────►   │                        │
│          │                                      │                        │
│          │    4. Verify with Public Key          │                        │
│          │                                      │                        │
│          │    5. Authentication Success         │                        │
│          │ ◄─────────────────────────────────   │                        │
│          │                                      │                        │
│   └─────────────┘                        └─────────────┘                │
│                                                                          │
│   Security: Private key NEVER leaves your device                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5. Merge Conflict Resolution

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    MERGE CONFLICT EXAMPLE                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   File: config.py                                                        │
│                                                                          │
│   CONFLICT (content): Merge conflict in config.py                        │
│                                                                          │
│   <<<<<<< HEAD                                                           │
│   DATABASE = "postgresql"    # Your change (current branch)              │
│   =======                                                                 │
│   DATABASE = "mysql"         # Incoming change (merging branch)          │
│   >>>>>>> feature-mysql                                                  │
│                                                                          │
│   ───────────────────────────────────────────────────────────────────    │
│                                                                          │
│   Resolution Options:                                                    │
│                                                                          │
│   Option 1: Keep your change                                            │
│   DATABASE = "postgresql"                                                │
│                                                                          │
│   Option 2: Keep incoming change                                        │
│   DATABASE = "mysql"                                                     │
│                                                                          │
│   Option 3: Combine/modify                                              │
│   DATABASE = os.getenv("DB_TYPE", "postgresql")                          │
│                                                                          │
│   After resolution:                                                      │
│   git add config.py                                                      │
│   git commit -m "Resolved database config conflict"                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 INSTALLATION & CONFIGURATION

### Git Installation in Termux

```bash
# Update package lists first
pkg update && pkg upgrade -y

# Install Git
pkg install git -y

# Verify installation
git --version
# Output: git version 2.x.x

# Install additional useful tools
pkg install gnupg -y     # For GPG signing commits
pkg install openssh -y   # For SSH operations
```

### Initial Configuration

```bash
# Set your identity (required for commits)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Set default editor
git config --global core.editor nano

# Configure line endings
git config --global core.autocrlf input

# Enable color output
git config --global color.ui auto

# Set pull behavior
git config --global pull.rebase false

# Configure credential helper (for HTTPS)
git config --global credential.helper store

# View all configurations
git config --global --list
```

### SSH Key Setup for GitHub

```bash
# Step 1: Generate SSH key pair
ssh-keygen -t ed25519 -C "your.email@example.com"

# Press Enter for default location (~/.ssh/id_ed25519)
# Enter passphrase (optional, press Enter for none)

# Step 2: Start SSH agent
eval "$(ssh-agent -s)"

# Step 3: Add key to agent
ssh-add ~/.ssh/id_ed25519

# Step 4: Display public key (copy this)
cat ~/.ssh/id_ed25519.pub

# Step 5: Add to GitHub
# Go to: GitHub → Settings → SSH and GPG keys → New SSH key
# Paste the public key and save

# Step 6: Test connection
ssh -T git@github.com
# Output: Hi username! You've successfully authenticated...

# Step 7: Configure Git to use SSH
# For existing repo:
git remote set-url origin git@github.com:username/repo.git

# For new clone:
git clone git@github.com:username/repo.git
```

### GitHub CLI Installation

```bash
# Install GitHub CLI
pkg install gh -y

# Verify installation
gh --version

# Authenticate
gh auth login
# Select: GitHub.com
# Select: SSH
# Select: Use existing SSH key
# Complete the authentication

# Verify authentication
gh auth status

# Useful gh commands
gh repo list                  # List your repos
gh repo create <name>         # Create new repo
gh repo clone <repo>          # Clone repo
gh issue list                 # List issues
gh pr list                    # List pull requests
```

---

## 📋 COMMANDS REFERENCE

### Repository Creation Commands

```bash
# Initialize new repository in current directory
git init

# Initialize with specific branch name
git init -b main

# Initialize bare repository (for servers)
git init --bare

# Clone repository via HTTPS
git clone https://github.com/username/repo.git

# Clone repository via SSH
git clone git@github.com:username/repo.git

# Clone into specific directory
git clone <url> my-project

# Clone specific branch only
git clone -b main --single-branch <url>

# Clone shallow (faster, less history)
git clone --depth 1 <url>
```

### Configuration Commands

```bash
# Set global configuration
git config --global user.name "Name"
git config --global user.email "email@example.com"

# Set local configuration (current repo only)
git config --local user.name "Name"

# Get configuration value
git config user.name

# List all configurations
git config --global --list

# Remove configuration
git config --global --unset user.name

# Edit configuration file
git config --global --edit
```

### Staging & Commit Commands

```bash
# Check repository status
git status

# Check status in short format
git status -s

# Stage single file
git add filename.txt

# Stage multiple files
git add file1.txt file2.txt

# Stage all changes in current directory
git add .

# Stage all changes in repository
git add -A

# Stage all changes (including deletions)
git add -u

# Stage interactively
git add -p

# Unstage file (keep changes)
git reset filename.txt

# Unstage everything
git reset

# Commit with message
git commit -m "Your commit message"

# Commit with multi-line message
git commit -m "Title" -m "Detailed description"

# Commit all tracked changes (skip staging)
git commit -a -m "Message"

# Amend last commit
git commit --amend -m "New message"

# Amend last commit (keep message)
git commit --amend --no-edit
```

### Branch Commands

```bash
# List all local branches
git branch

# List all remote branches
git branch -r

# List all branches (local and remote)
git branch -a

# Create new branch
git branch feature-name

# Create branch from specific commit
git branch feature-name abc123

# Switch to branch
git checkout feature-name

# Create and switch to new branch
git checkout -b feature-name

# Modern way to switch (Git 2.23+)
git switch feature-name

# Create and switch (modern)
git switch -c feature-name

# Delete branch (safe - only if merged)
git branch -d feature-name

# Delete branch (force)
git branch -D feature-name

# Rename branch
git branch -m old-name new-name

# Push branch to remote
git push -u origin feature-name

# Track remote branch
git branch --track feature-name origin/feature-name
```

### Merge & Rebase Commands

```bash
# Merge branch into current branch
git merge feature-name

# Merge with no fast-forward
git merge --no-ff feature-name

# Merge with squash (single commit)
git merge --squash feature-name

# Abort merge (during conflict)
git merge --abort

# Rebase current branch onto main
git rebase main

# Continue rebase after resolving conflicts
git rebase --continue

# Abort rebase
git rebase --abort

# Interactive rebase (edit history)
git rebase -i HEAD~3
```

### Remote Commands

```bash
# List remotes
git remote

# List remotes with URLs
git remote -v

# Add remote
git remote add origin https://github.com/user/repo.git

# Remove remote
git remote remove origin

# Rename remote
git remote rename old-name new-name

# Get remote URL
git remote get-url origin

# Set remote URL
git remote set-url origin https://github.com/user/new-repo.git

# Show remote details
git remote show origin

# Fetch from remote (no merge)
git fetch origin

# Fetch all remotes
git fetch --all

# Pull (fetch + merge)
git pull origin main

# Pull with rebase
git pull --rebase origin main

# Push to remote
git push origin main

# Push and set upstream
git push -u origin main

# Force push (dangerous!)
git push -f origin main

# Push all branches
git push --all origin

# Push tags
git push --tags
```

### History & Log Commands

```bash
# View commit history
git log

# View history in one line per commit
git log --oneline

# View last N commits
git log -5

# View history with graph
git log --oneline --graph --all

# View history with patch (diff)
git log -p

# View history with stats
git log --stat

# View history by author
git log --author="Name"

# View history after date
git log --since="2024-01-01"

# View history before date
git log --until="2024-12-31"

# View history for specific file
git log -- filename.txt

# View history with custom format
git log --pretty=format:"%h - %an, %ar : %s"

# Show specific commit
git show abc123

# Show specific commit's changes
git show abc123 --stat
```

### Diff Commands

```bash
# Show unstaged changes
git diff

# Show staged changes
git diff --staged
git diff --cached  # Same as --staged

# Show changes between commits
git diff abc123 def456

# Show changes between branches
git diff main..feature

# Show only file names
git diff --name-only

# Show statistics
git diff --stat

# Show changes for specific file
git diff filename.txt

# Show changes with context
git diff -U5  # 5 lines of context
```

### Stash Commands

```bash
# Stash current changes
git stash

# Stash with message
git stash push -m "Work in progress"

# Stash including untracked files
git stash -u

# List all stashes
git stash list

# Show stash details
git stash show stash@{0}

# Apply most recent stash
git stash pop

# Apply specific stash
git stash apply stash@{1}

# Apply without removing from list
git stash apply

# Drop stash
git stash drop stash@{0}

# Drop all stashes
git stash clear

# Create branch from stash
git stash branch new-branch stash@{0}
```

### Tag Commands

```bash
# List all tags
git tag

# Create lightweight tag
git tag v1.0.0

# Create annotated tag (recommended)
git tag -a v1.0.0 -m "Version 1.0.0 release"

# Tag specific commit
git tag v0.9.0 abc123

# Show tag details
git show v1.0.0

# Push single tag
git push origin v1.0.0

# Push all tags
git push origin --tags

# Delete local tag
git tag -d v1.0.0

# Delete remote tag
git push origin --delete v1.0.0

# Checkout specific tag
git checkout v1.0.0
```

### Reset & Revert Commands

```bash
# Soft reset (keep changes staged)
git reset --soft HEAD~1

# Mixed reset (keep changes unstaged)
git reset --mixed HEAD~1
git reset HEAD~1  # Default is mixed

# Hard reset (discard all changes)
git reset --hard HEAD~1

# Reset to specific commit
git reset --hard abc123

# Revert commit (create new commit that undoes)
git revert abc123

# Revert multiple commits
git revert abc123..def456

# Revert without commit
git revert --no-commit abc123
```

### Cleanup Commands

```bash
# Remove untracked files (dry run)
git clean -n

# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd

# Remove ignored files too
git clean -fdx

# Garbage collect
git gc

# Prune unreachable objects
git prune

# Remove stale remote branches
git remote prune origin
```

### Debug Commands

```bash
# Find who changed a line
git blame filename.txt

# Find who changed specific line range
git blame -L 10,20 filename.txt

# Search commits for pattern
git log -S "function_name"

# Search commits for pattern (regex)
git log -G "pattern"

# Binary search to find bug
git bisect start
git bisect bad          # Current commit has bug
git bisect good abc123  # This commit was fine
# Git will guide through bisect

# End bisect
git bisect reset
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Create and Initialize Repository

```bash
# Task: Create a new Git repository and make your first commit

# Step 1: Create project directory
mkdir ~/git-practice
cd ~/git-practice

# Step 2: Initialize Git repository
git init

# Step 3: Configure local settings (if not set globally)
git config user.name "Your Name"
git config user.email "your.email@example.com"

# Step 4: Create README file
cat > README.md << 'EOF'
# Git Practice Repository

This is a practice repository for learning Git.

## Features
- Feature 1
- Feature 2

## Installation
Run the setup script.

## Author
Your Name
EOF

# Step 5: Check status
git status

# Step 6: Stage the file
git add README.md

# Step 7: Commit
git commit -m "Initial commit: Added README.md"

# Step 8: View log
git log --oneline

# Expected: You should see your initial commit
```

### Exercise 2: Branch and Merge Workflow

```bash
# Task: Practice branching and merging

# Step 1: Create a new branch
git checkout -b feature-readme-update

# Step 2: Modify README
echo "" >> README.md
echo "## Updated Section" >> README.md
echo "This is an update from feature branch." >> README.md

# Step 3: Stage and commit
git add README.md
git commit -m "Added updated section to README"

# Step 4: Switch back to main
git checkout main

# Step 5: Create another branch
git checkout -b feature-readme-extra

# Step 6: Add different content
echo "" >> README.md
echo "## Extra Section" >> README.md
echo "This is extra content from another branch." >> README.md

# Step 7: Commit
git add README.md
git commit -m "Added extra section to README"

# Step 8: Switch to main and merge first branch
git checkout main
git merge feature-readme-update

# Step 9: Merge second branch (may have conflict)
git merge feature-readme-extra

# Step 10: Resolve any conflicts if they occur
# (Edit the file, remove conflict markers, keep desired content)

# Step 11: Complete the merge
git add README.md
git commit -m "Merged feature branches"

# Step 12: View branch history
git log --oneline --graph --all

# Step 13: Clean up branches
git branch -d feature-readme-update
git branch -d feature-readme-extra
```

### Exercise 3: Create and Push to GitHub

```bash
# Task: Create a repository on GitHub and push code

# Prerequisites:
# - GitHub account created
# - SSH key set up (or Personal Access Token ready)

# Step 1: Create repository on GitHub
# Go to: https://github.com/new
# Name: my-termux-project
# Description: My first Git project from Termux
# Public, No README (we have one locally)
# Click "Create repository"

# Step 2: Add remote origin (SSH)
git remote add origin git@github.com:YOUR_USERNAME/my-termux-project.git

# Or for HTTPS:
git remote add origin https://github.com/YOUR_USERNAME/my-termux-project.git

# Step 3: Verify remote
git remote -v

# Step 4: Push to GitHub
git push -u origin main
# Or if branch is named master:
git push -u origin master

# Step 5: Go to your GitHub repository page and verify files are uploaded

# Step 6: Make a change and push
echo "" >> README.md
echo "## Remote Update" >> README.md
echo "This update was pushed from Termux!" >> README.md
git add README.md
git commit -m "Added remote update section"
git push

# Expected: Your repository should be on GitHub with all commits
```

### Exercise 4: Git Stash Practice

```bash
# Task: Learn to use git stash

# Step 1: Start working on something
echo "Work in progress..." > work.txt

# Step 2: Check status
git status
# Shows: Untracked file: work.txt

# Step 3: Stage the file
git add work.txt

# Step 4: Now you need to switch branches but don't want to commit
# Stash your changes
git stash push -m "Work in progress on work.txt"

# Step 5: Check status - should be clean
git status

# Step 6: List stashes
git stash list

# Step 7: Work on something else
echo "Quick fix" > fix.txt
git add fix.txt
git commit -m "Quick fix added"

# Step 8: Restore your stashed work
git stash pop

# Step 9: Verify your work.txt is back
cat work.txt

# Step 10: Clean up
rm work.txt fix.txt
```

### Exercise 5: Create Release Tags

```bash
# Task: Create and manage tags for releases

# Step 1: Create a lightweight tag
git tag v0.1.0

# Step 2: Create an annotated tag (preferred)
git tag -a v1.0.0 -m "Version 1.0.0 - First stable release"

# Step 3: List tags
git tag

# Step 4: View tag details
git show v1.0.0

# Step 5: Push tags to remote
git push origin v1.0.0
# Or push all tags:
git push origin --tags

# Step 6: Make some changes
echo "New feature" > feature.txt
git add feature.txt
git commit -m "Added new feature"

# Step 7: Create new version tag
git tag -a v1.1.0 -m "Version 1.1.0 - Added new feature"

# Step 8: Push new tag
git push origin v1.1.0

# Expected: Tags visible on GitHub releases/tags page
```

### Exercise 6: Complete Git Workflow

```bash
# Task: Complete workflow - clone, branch, commit, PR

# Step 1: Clone a repository (use your own or a public one)
git clone https://github.com/username/repo.git
cd repo

# Step 2: Create feature branch
git checkout -b feature-contribution

# Step 3: Make changes
echo "## Contribution" >> README.md
echo "This is my contribution from Termux!" >> README.md

# Step 4: Stage and commit
git add README.md
git commit -m "Added contribution section to README"

# Step 5: Push branch
git push -u origin feature-contribution

# Step 6: Create Pull Request (if you have permissions)
gh pr create --title "Add contribution section" --body "Added a new section to README"

# Or manually on GitHub website

# Expected: Branch pushed and PR created
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "git: command not found"

```bash
# Cause: Git not installed

# Solution: Install Git
pkg install git -y

# Verify
git --version
```

### Problem 2: "fatal: not a git repository"

```bash
# Cause: Running git commands outside a git repository

# Solution 1: Initialize repository first
git init

# Solution 2: Navigate to existing repository
cd /path/to/your/repo

# Solution 3: Check if you're in a git repo
ls -la | grep .git
# Should show .git directory
```

### Problem 3: "fatal: unable to access... Connection refused"

```bash
# Cause: Network issues or firewall

# Solution 1: Check internet connection
ping -c 3 github.com

# Solution 2: Use different protocol
# HTTPS to SSH or vice versa
git remote set-url origin git@github.com:user/repo.git

# Solution 3: Check if using VPN/proxy

# Solution 4: Increase timeout
git config --global http.lowSpeedLimit 1000
git config --global http.lowSpeedTime 300
```

### Problem 4: "Permission denied (publickey)"

```bash
# Cause: SSH key not set up or not added to GitHub

# Solution 1: Check if SSH key exists
ls -la ~/.ssh/
# Should see id_ed25519 and id_ed25519.pub

# Solution 2: Generate SSH key if missing
ssh-keygen -t ed25519 -C "your@email.com"

# Solution 3: Add public key to GitHub
cat ~/.ssh/id_ed25519.pub
# Copy output, add to GitHub Settings → SSH Keys

# Solution 4: Test SSH connection
ssh -T git@github.com

# Solution 5: Start SSH agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Problem 5: "fatal: Authentication failed"

```bash
# Cause: Wrong credentials or token expired

# Solution 1: For HTTPS, use Personal Access Token
# Go to GitHub → Settings → Developer settings → Personal access tokens
# Generate new token with repo permissions
# Use token as password when prompted

# Solution 2: Use SSH instead of HTTPS
git remote set-url origin git@github.com:user/repo.git

# Solution 3: Reset stored credentials
git config --global --unset credential.helper
```

### Problem 6: Merge Conflicts

```bash
# Cause: Same file modified differently in merging branches

# Step 1: See conflicted files
git status

# Step 2: Open conflicted file and look for markers
# <<<<<<< HEAD
# Your changes
# =======
# Their changes
# >>>>>>> branch-name

# Step 3: Edit file to resolve conflict
# Remove markers and keep desired content

# Step 4: Stage resolved file
git add filename

# Step 5: Complete merge
git commit -m "Resolved merge conflict in filename"

# OR abort merge if you want to start over
git merge --abort
```

### Problem 7: "Your branch is behind/ahead of origin/main"

```bash
# Behind: Local is older than remote
git pull origin main

# Ahead: Local has commits not pushed
git push origin main

# Diverged: Both have different commits
git pull --rebase origin main
git push origin main
```

### Problem 8: Accidental Commit to Wrong Branch

```bash
# Scenario: Committed to main instead of feature branch

# Step 1: Undo commit (keep changes)
git reset --soft HEAD~1

# Step 2: Stash changes
git stash

# Step 3: Switch to correct branch
git checkout feature-branch

# Step 4: Apply stashed changes
git stash pop

# Step 5: Commit on correct branch
git add .
git commit -m "Your message"
```

### Problem 9: Large File Upload Fails

```bash
# Cause: GitHub has 100MB file limit

# Solution 1: Use Git LFS (Large File Storage)
pkg install git-lfs
git lfs install
git lfs track "*.large"
git add .gitattributes
git commit -m "Configure Git LFS"

# Solution 2: Remove large file from history
git filter-branch --force --index-filter \
  'git rm --cached --ignore-unmatch path/to/large/file' \
  --prune-empty --tag-name-filter cat -- --all

# Solution 3: Use .gitignore for large files
echo "*.mp4" >> .gitignore
echo "*.zip" >> .gitignore
```

### Problem 10: Detached HEAD State

```bash
# Cause: Checked out a specific commit or tag

# Solution 1: Create new branch from here
git checkout -b new-branch-name

# Solution 2: Go back to a branch
git checkout main

# Solution 3: If you made commits in detached state
# First, note the commit hash
git log --oneline -5

# Then create branch from that commit
git branch new-branch abc123
git checkout new-branch
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔀 GIT VERSION CONTROL           │
│   IN TERMUX                        │
│                                    │
│   ✓ SSH Keys Setup                 │
│   ✓ GitHub Integration             │
│   ✓ Branching & Merging            │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Command Focus**
```
┌────────────────────────────────────┐
│  $ git commit -m "Awesome!"        │
│  $ git push origin main            │
│                                    │
│  📱 GIT IN TERMUX                  │
│  Complete Guide                    │
│                                    │
│  🔐 SSH | 🌿 Branches | 🏷️ Tags    │
│                                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: GitHub Integration**
```
┌────────────────────────────────────┐
│  🐙 GitHub + Termux = ❤️           │
│                                    │
│  GIT VERSION CONTROL               │
│  Complete Tutorial                 │
│                                    │
│  📦 25+ Commands                   │
│  🔑 SSH Keys                       │
│  🌿 Branching                      │
│                                    │
│  Chapter 15 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔀 Git Version Control in Termux | Complete Guide | T3rmuxk1ng

🔥 In this video you'll learn:
• Git kya hai aur kyun important hai
• Termux mein Git install karna
• Local repositories create karna
• GitHub ke saath integrate karna
• SSH keys setup karna (passwordless login)
• Branching, merging, conflicts handle karna
• Git stash, tags, aur GitHub CLI

⏱️ Timestamps:
0:00 - Introduction
0:50 - Git Introduction
4:00 - Git Installation
6:00 - Creating Repository
9:00 - Basic Git Workflow
13:00 - Remote Repositories
16:00 - SSH Keys for GitHub
19:00 - Branching & Merging
22:00 - Merge Conflicts
24:00 - Git Stash & Tags
26:00 - GitHub CLI (gh)
28:00 - .gitignore File
29:30 - Summary

📝 Commands from this video:
pkg install git -y
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git init
git add .
git commit -m "Initial commit"
git push origin main
ssh-keygen -t ed25519 -C "your@email.com"

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Git #VersionControl #Termux #GitHub #T3rmuxk1ng #GitTutorial #GitHindi #TermuxCourse #LearnGit #GitBranch #GitSSH

---
⚠️ Disclaimer: This video is for educational purposes. Always use version control for your projects!
```

### Tags List

```
git, git tutorial, git version control, termux git, git in termux,
git hindi, git tutorial hindi, learn git, git basics, git commands,
github, github tutorial, git ssh, ssh key github, git branch,
git merge, git commit, git push, git pull, version control,
git for beginners, git course, termux course, t3rmuxk1ng,
github cli, gh cli, git stash, git tags, gitignore, 
git conflicts, merge conflicts, git workflow, github ssh setup
```

### Hashtags

```
#Git #VersionControl #GitTutorial #GitHindi #Termux #TermuxCourse 
#GitHub #LearnGit #GitCommands #GitBranch #GitMerge #GitSSH 
#T3rmuxk1ng #GitForBeginners #Programming #Coding #Development
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Git Official | https://git-scm.com/ |
| Git Documentation | https://git-scm.com/doc |
| Pro Git Book | https://git-scm.com/book/ |
| GitHub Docs | https://docs.github.com/ |
| GitHub CLI | https://cli.github.com/ |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Learn Git Branching | https://learngitbranching.js.org/ |
| Git Immersion | https://gitimmersion.com/ |
| Atlassian Git Tutorials | https://www.atlassian.com/git |
| GitHub Skills | https://skills.github.com/ |

### Cheat Sheets

| Resource | Link |
|----------|------|
| GitHub Git Cheat Sheet | https://training.github.com/downloads/ |
| Atlassian Git Cheat Sheet | https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet |

### Community

| Platform | Link |
|----------|------|
| Git Mailing List | git@vger.kernel.org |
| GitHub Community | https://github.community/ |
| Reddit | r/git |

---

## 📁 .gitignore Templates

### Python Project

```gitignore
# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
*.egg-info/
.installed.cfg
*.egg

# Virtual environments
venv/
ENV/
env/
.venv/

# IDE
.idea/
.vscode/
*.swp
*.swo

# Testing
.pytest_cache/
.coverage
htmlcov/

# Environment variables
.env
.env.local
```

### Node.js Project

```gitignore
# Dependencies
node_modules/

# Build output
dist/
build/

# Logs
logs
*.log
npm-debug.log*

# Environment
.env
.env.local
.env.production

# IDE
.idea/
.vscode/

# OS
.DS_Store
Thumbs.db

# Coverage
coverage/
```

### General Purpose

```gitignore
# OS generated files
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

# Editor files
*.swp
*.swo
*~
.idea/
.vscode/
*.sublime-*

# Environment
.env
.env.local
*.local

# Secrets
secrets.txt
credentials.json
*.pem
*.key

# Logs
*.log
logs/

# Temporary
tmp/
temp/
*.tmp
*.temp
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 16, verify:

- [ ] Git installed successfully (`git --version`)
- [ ] Global configuration set (user.name, user.email)
- [ ] Created local repository with `git init`
- [ ] Made commits with `git add` and `git commit`
- [ ] Cloned remote repository with `git clone`
- [ ] Created and switched branches
- [ ] Merged branches successfully
- [ ] SSH key generated and added to GitHub
- [ ] Pushed code to GitHub repository
- [ ] Handled a merge conflict (even simulated)
- [ ] Used git stash for temporary saves
- [ ] Created and pushed a tag
- [ ] Installed and configured GitHub CLI (gh)

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 16: Node.js in Termux**

- Node.js installation and setup
- NPM package manager
- Creating Node.js applications
- Express.js web server
- Package.json management
- Running JavaScript on Android
- Building APIs with Node.js

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
