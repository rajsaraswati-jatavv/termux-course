# Chapter 46: SSH Client Usage in Termux

> **Module:** 8 - Advanced  
> **Chapter:** 46 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | SSH client deep dive with all features |
| SSH Key Management | Generate, manage, and use multiple keys |
| File Transfer | SCP, SFTP, and rsync usage |
| SSH Tunneling | Local, remote, and dynamic forwarding |
| Commands Reference | 25+ SSH client commands |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common SSH issues and fixes |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 46
Title: SSH Client Usage in Termux | Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - SSH Client! Agar aap servers 
manage karte ho, remote systems pe kaam karte ho, ya cybersecurity 
field mein ho - SSH aapke liye daily driver hai.

Previous chapter mein humne SSH Server setup kiya Termux pe. Aaj 
hum seekhenge ki Termux se dusre servers ko kaise connect karein,
files kaise transfer karein, SSH tunneling kaise karein, aur 
bahut kuch.

SSH client remote access ka most secure aur standard tareeka hai.
Linux servers, cloud instances, VPS - sab SSH pe hi chalte hain.

To bina time waste kiye, chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein.

---

[SECTION 1: SSH CLIENT BASICS - 0:50 to 3:30]
─────────────────────────────────────────────────────────────────────────────

SSH kya hai? SSH ka full form hai Secure Shell.

Ye ek network protocol hai jo secure communication provide karta 
hai between two systems. Encrypted connection hoti hai, isliye 
password aur data safe rehte hain.

Termux mein SSH client by default available hai. Agar nahi hai 
to install karein:

    pkg install openssh -y

SSH ka basic syntax:

    ssh username@hostname

Ya phir IP address ke saath:

    ssh root@192.168.1.100

Ya custom port ke saath:

    ssh -p 2222 user@server.com

Jab aap connect karte ho, pehle ek prompt aayega:

    The authenticity of host '192.168.1.100' can't be established.
    ECDSA key fingerprint is SHA256:xxx...
    Are you sure you want to continue? (yes/no)

Ye first time connection prompt hai. "yes" type karein. Isse 
server ki identity save ho jaati hai known_hosts file mein.

Phir password mangega. Password type karein (screen pe nahi dikhega 
security ke liye) aur Enter dabayein.

Successfully connect ho jaoge!

---

[SECTION 2: SSH KEY GENERATION - 3:30 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab passwords ke baare mein - passwords se connect karna theek hai, 
lekin SSH keys zyada secure aur convenient hain.

SSH key pair hota hai:
- Private Key (aapke paas rehti hai - SECRET!)
- Public Key (server pe lagti hai)

Key generate karna:

    ssh-keygen -t ed25519 -C "my-termux-key"

Ya RSA key ke liye:

    ssh-keygen -t rsa -b 4096 -C "my-termux-key"

Options explain karta hoon:
- -t: Key type (ed25519 recommended, rsa legacy)
- -b: Bits (RSA ke liye 4096 recommended)
- -C: Comment (identifier ke liye)

Command run karne pe:
1. File location poochega - Enter dabayein for default
2. Passphrase poochega - optional, extra security ke liye
3. Confirm passphrase

Keys generate ho jaayengi:
- ~/.ssh/id_ed25519 (Private Key)
- ~/.ssh/id_ed25519.pub (Public Key)

Public key server pe copy karna:

    ssh-copy-id user@server.com

Ya manually:

    cat ~/.ssh/id_ed25519.pub | ssh user@server "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"

Ab password ke bina connect ho jaoge!

---

[SECTION 3: MULTIPLE SSH KEYS - 7:00 to 9:30]
─────────────────────────────────────────────────────────────────────────────

Agar aapke paas multiple servers hain aur alag-alag keys use karni 
hain, to kaise manage karein?

Multiple keys generate karein:

    ssh-keygen -t ed25519 -f ~/.ssh/github_key -C "github"
    ssh-keygen -t ed25519 -f ~/.ssh/server_key -C "myserver"
    ssh-keygen -t ed25519 -f ~/.ssh/aws_key -C "aws-ec2"

Ab in keys ko use karne ke do tarike hain:

[METHOD 1: Command Line]

    ssh -i ~/.ssh/aws_key ubuntu@aws-server.com

[METHOD 2: SSH Config File - RECOMMENDED]

Config file create karein:

    nano ~/.ssh/config

Example config:

    # GitHub
    Host github.com
        User git
        IdentityFile ~/.ssh/github_key
        IdentitiesOnly yes

    # My Server
    Host myserver
        HostName 192.168.1.100
        User root
        Port 2222
        IdentityFile ~/.ssh/server_key

    # AWS EC2
    Host aws-prod
        HostName ec2-xx-xx-xx-xx.compute.amazonaws.com
        User ubuntu
        IdentityFile ~/.ssh/aws_key

Ab simple command se connect karein:

    ssh myserver
    ssh aws-prod

Bahut easy ho gaya na?

---

[SECTION 4: FILE TRANSFER WITH SCP - 9:30 to 12:00]
─────────────────────────────────────────────────────────────────────────────

SSH se file transfer karna ho to SCP use karein - Secure Copy.

SCP ka syntax:

[Local to Remote]

    scp file.txt user@server:/path/to/destination

Example:

    scp myfile.txt root@192.168.1.100:/home/root/

Folder copy karna ho to -r flag:

    scp -r myfolder/ user@server:/home/user/

[Remote to Local]

    scp user@server:/path/to/file.txt ./local/path/

Example:

    scp root@192.168.1.100:/var/log/auth.log ./downloads/

Custom port ke saath:

    scp -P 2222 file.txt user@server:/path/

Multiple files:

    scp file1.txt file2.txt user@server:/path/

SCP bahut simple aur fast hai for quick transfers!

---

[SECTION 5: SFTP USAGE - 12:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

SCP se advanced hai SFTP - SSH File Transfer Protocol.

SFTP interactive mode deta hai jaise FTP client.

Connect karna:

    sftp user@server.com

Commands available:

    sftp> ls              # List remote files
    sftp> lls             # List local files
    sftp> cd /path        # Change remote directory
    sftp> lcd /path       # Change local directory
    sftp> get file.txt    # Download file
    sftp> put file.txt    # Upload file
    sftp> mget *.txt      # Download multiple files
    sftp> mput *.txt      # Upload multiple files
    sftp> mkdir newdir    # Create remote directory
    sftp> rm file.txt     # Delete remote file
    sftp> pwd             # Print remote working directory
    sftp> lpwd            # Print local working directory
    sftp> help            # Show all commands
    sftp> exit            # Exit SFTP

SFTP best hai jab aapko files browse karni ho, multiple 
operations karni ho, aur interactive experience chahiye.

---

[SECTION 6: RSYNC IN TERMUX - 14:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

RSYNC sabse powerful tool hai file synchronization ke liye.

Install karein:

    pkg install rsync -y

Basic syntax:

    rsync -avz source/ destination/

Remote sync:

    rsync -avz ./localfolder/ user@server:/remote/path/

Remote se local:

    rsync -avz user@server:/remote/path/ ./localfolder/

Important flags:
- -a: Archive mode (preserves permissions, times, etc.)
- -v: Verbose output
- -z: Compress during transfer
- -h: Human-readable format
- --progress: Show progress
- --delete: Delete extra files at destination
- --exclude: Exclude patterns

Real-world example:

    rsync -avzh --progress --delete \
        ./website/ user@server:/var/www/html/

Ye command:
- Local website folder ko remote pe sync karega
- Progress show karega
- Remote pe extra files delete kar dega
- Compressed transfer karega

RSYNC best hai backup automation aur large transfers ke liye!

---

[SECTION 7: SSH TUNNELING - 16:00 to 18:30]
─────────────────────────────────────────────────────────────────────────────

Ab aata hai ek advanced topic - SSH Tunneling!

Tunneling ka matlab hai ki aap SSH connection ke through kisi 
dusre service ko access kar sakte ho.

[LOCAL PORT FORWARDING]

Kisi remote service ko local port pe access karna:

    ssh -L 8080:localhost:80 user@server

Isse remote server ka port 80 aapke local port 8080 pe accessible 
ho jayega. Browser mein http://localhost:8080 karo aur remote 
web server dikhega!

Example - MySQL access:

    ssh -L 3306:localhost:3306 user@database-server

[REMOTE PORT FORWARDING]

Local service ko remote accessible banana:

    ssh -R 9000:localhost:3000 user@server

Isse aapka local port 3000 remote server ke port 9000 pe accessible 
ho jayega.

[DYNAMIC PORT FORWARDING - SOCKS PROXY]

    ssh -D 9050 user@server

Ye ek SOCKS proxy create karta hai. Browser ya tools mein 
SOCKS5 proxy configure karein:
- Host: 127.0.0.1
- Port: 9050

Ab saara traffic SSH tunnel se guzrega - encrypted aur secure!

Use cases:
- Bypass firewalls
- Access internal services
- Secure browsing on public WiFi
- Penetration testing

---

[SECTION 8: SSH JUMP HOSTS - 18:30 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Kabhi-kabhi directly server access nahi hota - ek intermediate 
server se guzarna padta hai. Isse Jump Host ya Bastion Host kehte hain.

Command syntax:

    ssh -J jumpuser@jumpserver targetuser@targetserver

Multiple jumps:

    ssh -J user1@jump1,user2@jump2 user3@final-server

SSH config mein:

    Host jump-server
        HostName jump.example.com
        User jumpuser

    Host target-server
        HostName 192.168.2.100
        User targetuser
        ProxyJump jump-server

Ab simple command:

    ssh target-server

Automatic jump through intermediate server hoga!

---

[SECTION 9: SSH AGENT - 20:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Multiple keys hain aur har baar passphrase enter karna pad raha hai?
SSH Agent use karein!

Start SSH agent:

    eval "$(ssh-agent -s)"

Key add karein:

    ssh-add ~/.ssh/id_ed25519
    ssh-add ~/.ssh/github_key

Passphrase ek baar enter karo, session ke liye yaad rakhega!

Added keys dekhein:

    ssh-add -l

Sab keys delete karein:

    ssh-add -D

Termux mein SSH agent ko automatically start karne ke liye 
.bashrc mein add karein:

    # Auto-start SSH agent
    if [ -z "$SSH_AUTH_SOCK" ]; then
        eval "$(ssh-agent -s)" > /dev/null
    fi

---

[SECTION 10: SUMMARY & NEXT PREVIEW - 21:30 to 23:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 46 complete! Let's summarize:

✅ SSH Client basics - Connect to remote servers
✅ SSH Key generation - ED25519 and RSA keys
✅ Multiple key management - SSH config file
✅ SCP for file transfer - Secure copy
✅ SFTP usage - Interactive file transfer
✅ RSYNC - Advanced synchronization
✅ SSH Tunneling - Local, Remote, Dynamic
✅ Jump hosts - Multi-hop connections
✅ SSH Agent - Passphrase management

Important commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 46 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ ssh user@server                 │ Basic SSH connection                  │
│ ssh -i key.pem user@server      │ Connect with specific key             │
│ ssh -L 8080:localhost:80 server │ Local port forwarding                │
│ ssh -D 9050 user@server         │ SOCKS proxy tunnel                    │
│ ssh-keygen -t ed25519           │ Generate SSH key                      │
│ ssh-copy-id user@server         │ Copy key to server                    │
│ scp file user@server:/path      │ Secure file copy                      │
│ rsync -avz src/ dest/           │ Synchronize directories               │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 47 mein hum seekhenge:
- Web Server setup in Termux
- Apache, Nginx, Python server
- Hosting websites locally
- PHP and MySQL setup

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 47!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. SSH Client Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         SSH CLIENT WORKFLOW                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────────┐         SSH Protocol          ┌──────────────────┐  │
│   │   TERMUX     │    ┌────────────────────┐    │   SSH SERVER     │  │
│   │   CLIENT     │    │  Encrypted Tunnel  │    │   (Remote)       │  │
│   │              │    │                    │    │                  │  │
│   │  ssh client  │◄──►│  • Authentication  │◄──►│  sshd daemon     │  │
│   │  scp/sftp    │    │  • Encryption      │    │  port 22         │  │
│   │  rsync       │    │  • Integrity       │    │                  │  │
│   │              │    │  • Compression     │    │  authorized_keys │  │
│   └──────────────┘    └────────────────────┘    └──────────────────┘  │
│                                                                          │
│   LOCAL MACHINE                          REMOTE MACHINE                 │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. SSH Key Types Comparison

| Key Type | Key Size | Security | Speed | Compatibility |
|----------|----------|----------|-------|---------------|
| **ED25519** | 256-bit | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Modern systems |
| **RSA 4096** | 4096-bit | ⭐⭐⭐⭐ | ⭐⭐⭐ | Universal |
| **ECDSA** | 256-521 bit | ⭐⭐⭐ | ⭐⭐⭐⭐ | Good |
| **DSA** | 1024-bit | ⭐⭐ (deprecated) | ⭐⭐⭐ | Legacy |

### 3. SSH Configuration Files

```
~/.ssh/
├── id_ed25519          # Default private key (ED25519)
├── id_ed25519.pub      # Default public key
├── id_rsa              # RSA private key
├── id_rsa.pub          # RSA public key
├── config              # SSH client configuration
├── known_hosts         # Known server fingerprints
├── authorized_keys     # Keys allowed to login (for server)
└── known_hosts.old     # Backup of known_hosts
```

### 4. SSH Config File Structure

```bash
# ~/.ssh/config - Complete Example

# Global defaults
Host *
    AddKeysToAgent yes
    Compression yes
    ServerAliveInterval 60
    ServerAliveCountMax 3

# GitHub Configuration
Host github.com
    User git
    HostName github.com
    IdentityFile ~/.ssh/github_key
    IdentitiesOnly yes

# Personal Server
Host myserver
    HostName 192.168.1.100
    User root
    Port 22
    IdentityFile ~/.ssh/personal_key

# AWS EC2 Instance
Host aws-prod
    HostName ec2-xx-xx-xx-xx.compute.amazonaws.com
    User ubuntu
    IdentityFile ~/.ssh/aws_key.pem
    ServerAliveInterval 300

# VPS with custom port
Host vps
    HostName myvps.com
    User admin
    Port 2222
    IdentityFile ~/.ssh/vps_key

# Jump host configuration
Host internal-server
    HostName 10.0.0.50
    User internal
    ProxyJump jump-server
    IdentityFile ~/.ssh/internal_key

# SOCKS proxy alias
Host proxy
    HostName proxy-server.com
    User proxyuser
    DynamicForward 9050
```

### 5. SSH Cipher Suites

```bash
# Check supported ciphers
ssh -Q cipher

# Check MACs
ssh -Q mac

# Check key exchange algorithms
ssh -Q kex

# Force specific cipher (for testing)
ssh -c aes256-gcm@openssh.com user@server

# Preferred algorithms (modern)
# Ciphers: chacha20-poly1305, aes256-gcm, aes128-gcm
# MACs: hmac-sha2-512-etm, hmac-sha2-256-etm
# KEX: curve25519-sha256, diffie-hellman-group16-sha512
```

---

## 🔧 SSH KEY MANAGEMENT

### Generate SSH Keys

```bash
# ED25519 (Recommended - Modern, Fast, Secure)
ssh-keygen -t ed25519 -C "your_email@example.com"

# RSA 4096-bit (Universal compatibility)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# With custom filename
ssh-keygen -t ed25519 -f ~/.ssh/my_custom_key -C "custom key"

# Without passphrase (not recommended for production)
ssh-keygen -t ed25519 -N "" -f ~/.ssh/key_no_pass

# With specific comment
ssh-keygen -t ed25519 -C "termux-$(date +%Y%m%d)"

# Show public key fingerprint
ssh-keygen -lf ~/.ssh/id_ed25519.pub

# Show randomart image
ssh-keygen -lvf ~/.ssh/id_ed25519.pub
```

### Copy SSH Keys to Server

```bash
# Method 1: ssh-copy-id (easiest)
ssh-copy-id user@server

# With custom port
ssh-copy-id -p 2222 user@server

# With specific key
ssh-copy-id -i ~/.ssh/custom_key.pub user@server

# Method 2: Manual copy
cat ~/.ssh/id_ed25519.pub | ssh user@server "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"

# Method 3: Using pipe
ssh user@server "echo '$(cat ~/.ssh/id_ed25519.pub)' >> ~/.ssh/authorized_keys"
```

### Manage Multiple Keys

```bash
# List all keys in .ssh directory
ls -la ~/.ssh/*.pub

# Test which key is being used
ssh -v user@server 2>&1 | grep "Trying private key"

# Specify key manually
ssh -i ~/.ssh/specific_key user@server

# Add multiple keys to agent
ssh-add ~/.ssh/key1 ~/.ssh/key2 ~/.ssh/key3

# Test connection with verbose output
ssh -vvv user@server
```

### Key Security Best Practices

```bash
# Set correct permissions
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
chmod 600 ~/.ssh/config
chmod 644 ~/.ssh/known_hosts

# Verify permissions
ls -la ~/.ssh/

# Backup private key (encrypted)
cp ~/.ssh/id_ed25519 ~/.ssh/id_ed25519.backup

# Export public key for sharing
cat ~/.ssh/id_ed25519.pub

# Generate public key from private key (if lost)
ssh-keygen -y -f ~/.ssh/id_ed25519 > ~/.ssh/id_ed25519.pub

# Change passphrase of existing key
ssh-keygen -p -f ~/.ssh/id_ed25519
```

---

## 📂 FILE TRANSFER METHODS

### SCP Commands

```bash
# Upload single file
scp file.txt user@server:/remote/path/

# Upload with new filename
scp file.txt user@server:/remote/path/newname.txt

# Download single file
scp user@server:/remote/file.txt ./local/path/

# Upload directory (recursive)
scp -r mydir/ user@server:/remote/path/

# Download directory
scp -r user@server:/remote/directory/ ./local/path/

# Custom port
scp -P 2222 file.txt user@server:/path/

# Preserve file attributes
scp -p file.txt user@server:/path/

# Limit bandwidth (KB/s)
scp -l 1000 file.txt user@server:/path/

# Compress during transfer
scp -C file.txt user@server:/path/

# Multiple files
scp file1.txt file2.txt file3.txt user@server:/path/

# Using wildcard
scp *.txt user@server:/path/

# Between two remote servers
scp user1@server1:/file.txt user2@server2:/path/
```

### SFTP Commands

```bash
# Connect to server
sftp user@server

# Connect with custom port
sftp -P 2222 user@server

# Connect with specific key
sftp -i ~/.ssh/key user@server

# Batch mode (execute commands from file)
sftp -b commands.txt user@server

# Download file
sftp> get filename.txt

# Download with different name
sftp> get remote.txt local.txt

# Upload file
sftp> put localfile.txt

# Download multiple files
sftp> mget *.txt

# Upload multiple files
sftp> mput *.txt

# Create directory
sftp> mkdir newdir

# Remove file
sftp> rm filename.txt

# Remove directory
sftp> rmdir dirname

# Change permissions
sftp> chmod 755 script.sh

# Show current directory
sftp> pwd           # remote
sftp> lpwd          # local

# List files
sftp> ls            # remote
sftp> lls           # local

# Change directory
sftp> cd /path      # remote
sftp> lcd /path     # local

# Get help
sftp> help

# Exit
sftp> exit
sftp> quit
```

### RSYNC Commands

```bash
# Install rsync
pkg install rsync -y

# Basic sync (local)
rsync -av source/ destination/

# Sync to remote
rsync -avz ./local/ user@server:/remote/

# Sync from remote
rsync -avz user@server:/remote/ ./local/

# Dry run (preview changes)
rsync -avzn --delete source/ destination/

# Sync with progress
rsync -avz --progress ./files/ user@server:/backup/

# Sync with delete (mirror)
rsync -avz --delete source/ destination/

# Exclude files
rsync -avz --exclude='*.log' --exclude='tmp/' source/ dest/

# Include only specific files
rsync -avz --include='*.txt' --exclude='*' source/ dest/

# Sync with SSH on custom port
rsync -avz -e 'ssh -p 2222' source/ user@server:/dest/

# Sync with bandwidth limit
rsync -avz --bwlimit=1000 source/ dest/

# Show stats
rsync -avz --stats source/ dest/

# Partial transfer (resume)
rsync -avz --partial --progress source/ dest/

# Backup before overwrite
rsync -avz --backup --backup-dir=/backup source/ dest/

# Compress during transfer
rsync -avz source/ dest/

# Preserve all attributes
rsync -avzAX source/ dest/
# -a: archive
# -A: preserve ACLs
# -X: preserve extended attributes

# Use checksum for comparison
rsync -avzc source/ dest/

# One-way sync (push)
rsync -avz --delete-delay ./website/ server:/var/www/

# Pull from server
rsync -avzP server:/var/log/app/ ./logs/
```

---

## 🚇 SSH TUNNELING

### Local Port Forwarding

```bash
# Syntax: ssh -L [local_port]:[remote_host]:[remote_port] user@server

# Forward remote web server to local
ssh -L 8080:localhost:80 user@server
# Access: http://localhost:8080

# Forward remote database
ssh -L 3306:localhost:3306 user@database-server
# Connect: mysql -h 127.0.0.1 -P 3306

# Forward to different internal host
ssh -L 8080:internal-server:80 user@jump-server
# Access internal web server through jump server

# Forward multiple ports
ssh -L 8080:localhost:80 -L 3306:localhost:3306 user@server

# Background tunnel
ssh -fNL 8080:localhost:80 user@server

# Bind to specific interface
ssh -L 0.0.0.0:8080:localhost:80 user@server
# Accessible from other machines on network
```

### Remote Port Forwarding

```bash
# Syntax: ssh -R [remote_port]:[local_host]:[local_port] user@server

# Expose local web server remotely
ssh -R 8080:localhost:3000 user@server
# Others can access: http://server:8080

# Expose local service
ssh -R 9000:localhost:9000 user@server

# Reverse tunnel for VNC
ssh -R 5900:localhost:5900 user@server

# Allow remote connections (GatewayPorts)
ssh -R 0.0.0.0:8080:localhost:3000 user@server
# Requires GatewayPorts yes in sshd_config on server
```

### Dynamic Port Forwarding (SOCKS Proxy)

```bash
# Create SOCKS5 proxy
ssh -D 9050 user@server

# Use with specific port
ssh -D 1080 user@server

# Background SOCKS proxy
ssh -fND 9050 user@server

# Configure proxy in browser
# Firefox: Settings → Network → Manual proxy
# SOCKS Host: 127.0.0.1 Port: 9050
# SOCKS v5: checked

# Use with curl
curl --socks5 127.0.0.1:9050 http://example.com

# Use with proxychains
echo "socks5 127.0.0.1 9050" >> /etc/proxychains.conf
proxychains nmap target.com

# SSH through SOCKS
ssh -o ProxyCommand='nc -X 5 -x 127.0.0.1:9050 %h %p' user@target
```

### SSH Tunnel for Specific Applications

```bash
# MySQL tunnel
ssh -L 3306:127.0.0.1:3306 user@mysql-server
mysql -h 127.0.0.1 -u root -p

# PostgreSQL tunnel
ssh -L 5432:127.0.0.1:5432 user@postgres-server
psql -h 127.0.0.1 -U postgres

# Redis tunnel
ssh -L 6379:127.0.0.1:6379 user@redis-server
redis-cli -h 127.0.0.1

# MongoDB tunnel
ssh -L 27017:127.0.0.1:27017 user@mongo-server
mongo --host 127.0.0.1

# VNC tunnel
ssh -L 5901:localhost:5901 user@vnc-server
vncviewer localhost:5901

# RDP tunnel
ssh -L 3389:localhost:3389 user@rdp-server
rdesktop localhost

# Jupyter notebook tunnel
ssh -L 8888:localhost:8888 user@server
# Access: http://localhost:8888
```

---

## 🔄 SSH JUMP HOSTS

### Single Jump Host

```bash
# Direct command
ssh -J jumpuser@jumpserver targetuser@targetserver

# With ports
ssh -J jumpuser@jumpserver:2222 targetuser@targetserver:22

# Using ProxyCommand (older method)
ssh -o ProxyCommand="ssh -W %h:%p jumpuser@jumpserver" targetuser@targetserver

# Config file method (recommended)
# ~/.ssh/config:
Host jump
    HostName jump.example.com
    User jumpuser

Host target
    HostName 10.0.0.50
    User targetuser
    ProxyJump jump

# Then simply:
ssh target
```

### Multiple Jump Hosts

```bash
# Chain multiple jumps
ssh -J user1@jump1,user2@jump2 user3@final-server

# Config for multiple jumps
Host jump1
    HostName jump1.example.com
    User user1

Host jump2
    HostName jump2.internal
    User user2
    ProxyJump jump1

Host final
    HostName 192.168.2.100
    User user3
    ProxyJump jump2

# Connect
ssh final  # goes through jump1 -> jump2 -> final
```

### Jump Host with Key Authentication

```bash
# Different keys for each hop
Host jump
    HostName jump.com
    User jumpuser
    IdentityFile ~/.ssh/jump_key

Host target
    HostName target.internal
    User targetuser
    IdentityFile ~/.ssh/target_key
    ProxyJump jump

# Connect
ssh target
```

---

## 🔐 SSH AGENT

### SSH Agent Commands

```bash
# Start SSH agent
eval "$(ssh-agent -s)"

# Start with specific shell
eval $(ssh-agent -c)  # for csh

# Add default key
ssh-add

# Add specific key
ssh-add ~/.ssh/custom_key

# Add key with timeout (seconds)
ssh-add -t 3600 ~/.ssh/id_ed25519

# List added keys
ssh-add -l

# List public keys
ssh-add -L

# Delete specific key
ssh-add -d ~/.ssh/id_ed25519

# Delete all keys
ssh-add -D

# Delete from card (smartcard)
ssh-add -e /path/to/pkcs11.so

# Lock agent (requires password)
ssh-add -x

# Unlock agent
ssh-add -X

# Show agent PID
echo $SSH_AGENT_PID

# Show agent socket
echo $SSH_AUTH_SOCK

# Kill agent
ssh-agent -k
```

### Auto-start SSH Agent in Termux

```bash
# Add to ~/.bashrc
# SSH Agent Auto-start
env=~/.ssh/agent.env

agent_load_env() {
    test -f "$env" && . "$env" > /dev/null
}

agent_start() {
    (umask 077; ssh-agent > "$env")
    . "$env" > /dev/null
}

agent_load_env

# Agent run state
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env
```

---

## 📋 KNOWN HOSTS MANAGEMENT

### Manage Known Hosts

```bash
# View known hosts
cat ~/.ssh/known_hosts

# List hosts with hashes (if HashKnownServers yes)
ssh-keygen -l -f ~/.ssh/known_hosts

# Remove specific host
ssh-keygen -R server.example.com

# Remove by IP
ssh-keygen -R 192.168.1.100

# Remove with custom file
ssh-keygen -R server.com -f ~/.ssh/custom_known_hosts

# Remove all hosts
> ~/.ssh/known_hosts

# Backup before removing
cp ~/.ssh/known_hosts ~/.ssh/known_hosts.backup

# Add host without prompt
ssh -o StrictHostKeyChecking=no user@server

# Disable host checking (insecure, testing only)
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null user@server

# View fingerprints of all known hosts
ssh-keygen -l -f ~/.ssh/known_hosts

# Check if host exists in known_hosts
ssh-keygen -F server.example.com

# Visualize key type
ssh-keygen -lv -f ~/.ssh/known_hosts
```

---

## 🤖 SSH AUTOMATION SCRIPTS

### Auto-backup Script

```bash
#!/bin/bash
# backup-to-server.sh - Automated backup via SSH

SERVER="user@backup-server.com"
REMOTE_PATH="/backups/termux"
LOCAL_PATH="$HOME/projects"
DATE=$(date +%Y%m%d_%H%M%S)
LOG_FILE="$HOME/backup.log"

log() {
    echo "[$(date)] $1" >> "$LOG_FILE"
}

log "Starting backup..."

# Check SSH connection
if ! ssh -o ConnectTimeout=5 "$SERVER" "exit" 2>/dev/null; then
    log "ERROR: Cannot connect to server"
    exit 1
fi

# Create remote directory
ssh "$SERVER" "mkdir -p $REMOTE_PATH/$DATE"

# Sync files
rsync -avz --progress "$LOCAL_PATH/" "$SERVER:$REMOTE_PATH/$DATE/"

if [ $? -eq 0 ]; then
    log "Backup completed successfully"
else
    log "ERROR: Backup failed"
    exit 1
fi

# Keep only last 7 backups
ssh "$SERVER" "cd $REMOTE_PATH && ls -t | tail -n +8 | xargs -r rm -rf"

log "Old backups cleaned"
```

### SSH Connection Monitor

```bash
#!/bin/bash
# ssh-monitor.sh - Monitor SSH connections

check_ssh() {
    local server=$1
    local user=$2
    local port=${3:-22}
    
    if ssh -o ConnectTimeout=5 -o BatchMode=yes -p "$port" "$user@$server" "exit" 2>/dev/null; then
        echo "[OK] $server:$port"
        return 0
    else
        echo "[FAIL] $server:$port"
        return 1
    fi
}

# Servers to check
SERVERS=(
    "server1.example.com:root:22"
    "server2.example.com:admin:2222"
    "192.168.1.100:user:22"
)

for server_info in "${SERVERS[@]}"; do
    IFS=':' read -r server user port <<< "$server_info"
    check_ssh "$server" "$user" "$port"
done
```

### Multi-server Command Executor

```bash
#!/bin/bash
# ssh-run-all.sh - Run command on multiple servers

COMMAND="$1"
SERVERS=("server1" "server2" "server3")

if [ -z "$COMMAND" ]; then
    echo "Usage: $0 'command to run'"
    exit 1
fi

for server in "${SERVERS[@]}"; do
    echo "=== $server ==="
    ssh "$server" "$COMMAND"
    echo ""
done
```

### SSH Tunnel Manager

```bash
#!/bin/bash
# tunnel-manager.sh - Manage SSH tunnels

PID_FILE="$HOME/.tunnel.pid"

start_tunnel() {
    if [ -f "$PID_FILE" ]; then
        echo "Tunnel already running (PID: $(cat $PID_FILE))"
        return 1
    fi
    
    ssh -fN -D 9050 -S /tmp/ssh-tunnel.sock user@proxy-server
    echo $! > "$PID_FILE"
    echo "Tunnel started (PID: $(cat $PID_FILE))"
}

stop_tunnel() {
    if [ ! -f "$PID_FILE" ]; then
        echo "No tunnel running"
        return 1
    fi
    
    ssh -S /tmp/ssh-tunnel.sock -O exit user@proxy-server
    rm -f "$PID_FILE"
    echo "Tunnel stopped"
}

status_tunnel() {
    if [ -f "$PID_FILE" ]; then
        echo "Tunnel running (PID: $(cat $PID_FILE))"
    else
        echo "No tunnel running"
    fi
}

case "$1" in
    start)   start_tunnel ;;
    stop)    stop_tunnel ;;
    status)  status_tunnel ;;
    restart) stop_tunnel; start_tunnel ;;
    *)       echo "Usage: $0 {start|stop|status|restart}" ;;
esac
```

---

## 📋 COMMANDS REFERENCE

### Basic SSH Commands

```bash
# Connect to server
ssh user@hostname

# Connect with specific port
ssh -p 2222 user@hostname

# Connect with specific key
ssh -i ~/.ssh/key.pem user@hostname

# Connect with verbose output
ssh -v user@hostname

# Connect with maximum verbosity
ssh -vvv user@hostname

# Run command on remote server
ssh user@hostname 'command'

# Run multiple commands
ssh user@hostname 'command1; command2; command3'

# Run command with tty
ssh -t user@hostname 'sudo command'

# Force pseudo-terminal allocation
ssh -tt user@hostname

# Disable pseudo-terminal
ssh -T user@hostname

# Connect with specific cipher
ssh -c aes256-gcm@openssh.com user@hostname

# Connect with compression
ssh -C user@hostname

# Keep connection alive
ssh -o ServerAliveInterval=60 user@hostname

# Timeout connection attempt
ssh -o ConnectTimeout=10 user@hostname

# Exit on connection error
ssh -o BatchMode=yes user@hostname

# Disable strict host checking
ssh -o StrictHostKeyChecking=no user@hostname

# Use specific known_hosts file
ssh -o UserKnownHostsFile=~/.ssh/custom_hosts user@hostname

# Connection with multiple options
ssh -o ConnectTimeout=10 -o ServerAliveInterval=60 -p 2222 user@hostname
```

### SSH Key Commands

```bash
# Generate ED25519 key
ssh-keygen -t ed25519 -C "comment"

# Generate RSA 4096-bit key
ssh-keygen -t rsa -b 4096 -C "comment"

# Generate key with custom filename
ssh-keygen -t ed25519 -f ~/.ssh/mykey

# Generate key without passphrase
ssh-keygen -t ed25519 -N "" -f ~/.ssh/mykey

# Change key passphrase
ssh-keygen -p -f ~/.ssh/id_ed25519

# Show public key fingerprint
ssh-keygen -lf ~/.ssh/id_ed25519.pub

# Show key randomart
ssh-keygen -lvf ~/.ssh/id_ed25519.pub

# Generate public from private key
ssh-keygen -y -f ~/.ssh/id_ed25519 > ~/.ssh/id_ed25519.pub

# Copy key to server
ssh-copy-id user@server

# Copy key with custom port
ssh-copy-id -p 2222 user@server

# Copy specific key
ssh-copy-id -i ~/.ssh/custom_key.pub user@server
```

### SCP Commands

```bash
# Upload file
scp file.txt user@server:/path/

# Download file
scp user@server:/path/file.txt ./

# Upload directory
scp -r dir/ user@server:/path/

# Download directory
scp -r user@server:/path/dir/ ./

# Custom port
scp -P 2222 file.txt user@server:/path/

# Preserve attributes
scp -p file.txt user@server:/path/

# Compress transfer
scp -C file.txt user@server:/path/

# Limit bandwidth
scp -l 1000 file.txt user@server:/path/

# Recursive with compression
scp -rC dir/ user@server:/path/

# Multiple files
scp file1.txt file2.txt user@server:/path/

# Wildcard
scp *.txt user@server:/path/
```

### RSYNC Commands

```bash
# Basic sync
rsync -avz source/ dest/

# Sync to remote
rsync -avz source/ user@server:/dest/

# Sync from remote
rsync -avz user@server:/source/ dest/

# Dry run
rsync -avzn source/ dest/

# With progress
rsync -avz --progress source/ dest/

# Mirror (delete extra)
rsync -avz --delete source/ dest/

# Exclude patterns
rsync -avz --exclude='*.log' source/ dest/

# Include specific files
rsync -avz --include='*.txt' --exclude='*' source/ dest/

# Custom SSH port
rsync -avz -e 'ssh -p 2222' source/ user@server:/dest/

# Bandwidth limit
rsync -avz --bwlimit=1000 source/ dest/

# Partial (resume)
rsync -avz --partial --progress source/ dest/

# Backup mode
rsync -avz --backup --backup-dir=/backup source/ dest/

# Compress during transfer
rsync -avz source/ dest/

# Show stats
rsync -avz --stats source/ dest/
```

### SSH Tunnel Commands

```bash
# Local port forward
ssh -L 8080:localhost:80 user@server

# Remote port forward
ssh -R 8080:localhost:3000 user@server

# Dynamic (SOCKS) forward
ssh -D 9050 user@server

# Background tunnel
ssh -fNL 8080:localhost:80 user@server

# Multiple local forwards
ssh -L 8080:localhost:80 -L 3306:localhost:3306 user@server

# Forward to internal host
ssh -L 8080:internal-host:80 user@jump-server

# Bind to all interfaces
ssh -L 0.0.0.0:8080:localhost:80 user@server

# Control socket for tunnel management
ssh -S /tmp/tunnel.sock -fNT -D 9050 user@server

# Check tunnel status
ssh -S /tmp/tunnel.sock -O check user@server

# Stop tunnel
ssh -S /tmp/tunnel.sock -O exit user@server
```

### SSH Agent Commands

```bash
# Start agent
eval "$(ssh-agent -s)"

# Add key
ssh-add ~/.ssh/id_ed25519

# List keys
ssh-add -l

# List public keys
ssh-add -L

# Delete key
ssh-add -d ~/.ssh/id_ed25519

# Delete all keys
ssh-add -D

# Add key with timeout
ssh-add -t 3600 ~/.ssh/id_ed25519

# Lock agent
ssh-add -x

# Unlock agent
ssh-add -X

# Kill agent
ssh-agent -k
```

### SFTP Commands

```bash
# Connect
sftp user@server

# Connect with port
sftp -P 2222 user@server

# Batch mode
sftp -b commands.txt user@server

# Download file
sftp> get file.txt

# Upload file
sftp> put file.txt

# Download multiple
sftp> mget *.txt

# Upload multiple
sftp> mput *.txt

# List remote
sftp> ls

# List local
sftp> lls

# Change remote dir
sftp> cd /path

# Change local dir
sftp> lcd /path

# Create directory
sftp> mkdir newdir

# Delete file
sftp> rm file.txt

# Exit
sftp> exit
```

### SSH Config Commands

```bash
# View config
cat ~/.ssh/config

# Edit config
nano ~/.ssh/config

# Check config syntax
ssh -G hostname | head

# Test specific host config
ssh -G myserver | grep -i user

# List all configured hosts
grep "^Host " ~/.ssh/config
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic SSH Connection

```bash
# Task: Connect to a remote server

# Step 1: Install OpenSSH client
pkg install openssh -y

# Step 2: Verify SSH is installed
ssh -V

# Step 3: Connect to a server (use your own server or test server)
# ssh user@your-server-ip

# Step 4: Run a command on remote server
# ssh user@server 'uname -a'

# Step 5: Check current SSH client options
ssh -G localhost | head -20
```

### Exercise 2: SSH Key Setup

```bash
# Task: Generate and use SSH keys

# Step 1: Generate ED25519 key
ssh-keygen -t ed25519 -C "termux-practice-$(date +%Y%m%d)"

# Step 2: View the generated keys
ls -la ~/.ssh/

# Step 3: Display public key
cat ~/.ssh/id_ed25519.pub

# Step 4: Show key fingerprint
ssh-keygen -lf ~/.ssh/id_ed25519.pub

# Step 5: Show key randomart
ssh-keygen -lvf ~/.ssh/id_ed25519.pub

# Step 6: Generate a second key with custom name
ssh-keygen -t ed25519 -f ~/.ssh/second_key -C "second-key"

# Step 7: List all your public keys
for key in ~/.ssh/*.pub; do
    echo "=== $key ==="
    ssh-keygen -lf "$key"
done
```

### Exercise 3: SSH Config File

```bash
# Task: Create and use SSH config

# Step 1: Create SSH config file
cat > ~/.ssh/config << 'EOF'
# Global defaults
Host *
    AddKeysToAgent yes
    IdentitiesOnly yes
    ServerAliveInterval 60

# Example server configuration (modify with your details)
# Host myserver
#     HostName 192.168.1.100
#     User root
#     Port 22
#     IdentityFile ~/.ssh/id_ed25519

# GitHub example
Host github.com
    User git
    HostName github.com
    IdentityFile ~/.ssh/id_ed25519
EOF

# Step 2: Set correct permissions
chmod 600 ~/.ssh/config

# Step 3: Verify config syntax
cat ~/.ssh/config

# Step 4: Test config parsing (replace 'myserver' with your host)
# ssh -G myserver | head -20
```

### Exercise 4: SCP File Transfer

```bash
# Task: Transfer files using SCP

# Step 1: Create test files
mkdir -p ~/test-scp
echo "Test file 1" > ~/test-scp/file1.txt
echo "Test file 2" > ~/test-scp/file2.txt
echo "Test file 3" > ~/test-scp/file3.txt

# Step 2: Upload single file (use your server)
# scp ~/test-scp/file1.txt user@server:/tmp/

# Step 3: Upload multiple files
# scp ~/test-scp/*.txt user@server:/tmp/

# Step 4: Upload directory
# scp -r ~/test-scp/ user@server:/tmp/

# Step 5: Download file
# scp user@server:/etc/passwd ~/test-scp/remote-passwd

# Step 6: Cleanup
rm -rf ~/test-scp
```

### Exercise 5: RSYNC Synchronization

```bash
# Task: Synchronize directories with rsync

# Step 1: Install rsync
pkg install rsync -y

# Step 2: Create test directory structure
mkdir -p ~/rsync-test/source/subdir
echo "File A" > ~/rsync-test/source/fileA.txt
echo "File B" > ~/rsync-test/source/fileB.txt
echo "File C" > ~/rsync-test/source/subdir/fileC.txt
echo "Log file" > ~/rsync-test/source/debug.log

# Step 3: Create destination
mkdir -p ~/rsync-test/destination

# Step 4: Dry run sync
rsync -avzn ~/rsync-test/source/ ~/rsync-test/destination/

# Step 5: Actual sync
rsync -avz ~/rsync-test/source/ ~/rsync-test/destination/

# Step 6: Verify
ls -la ~/rsync-test/destination/

# Step 7: Sync with exclude
rsync -avz --exclude='*.log' ~/rsync-test/source/ ~/rsync-test/destination/

# Step 8: Sync with delete (mirror)
echo "File D" > ~/rsync-test/source/fileD.txt
rsync -avz --delete ~/rsync-test/source/ ~/rsync-test/destination/

# Step 9: Cleanup
rm -rf ~/rsync-test
```

### Exercise 6: SSH Tunneling

```bash
# Task: Create and use SSH tunnels

# Step 1: Create local port forward (example)
# ssh -L 8080:localhost:80 user@server

# Step 2: Test the tunnel
# curl http://localhost:8080

# Step 3: Create SOCKS proxy (example)
# ssh -D 9050 user@server

# Step 4: Test SOCKS proxy (install curl first)
pkg install curl -y
# curl --socks5 127.0.0.1:9050 http://ifconfig.me

# Step 5: Create background tunnel
# ssh -fNL 3306:localhost:3306 user@server

# Step 6: Find tunnel process
# ps aux | grep ssh

# Step 7: Kill tunnel
# pkill -f "ssh -fNL"
```

### Exercise 7: SSH Agent

```bash
# Task: Use SSH agent for key management

# Step 1: Start SSH agent
eval "$(ssh-agent -s)"

# Step 2: Add your key
ssh-add ~/.ssh/id_ed25519

# Step 3: List added keys
ssh-add -l

# Step 4: Show public keys
ssh-add -L

# Step 5: Test connection with agent
# ssh user@server

# Step 6: Remove all keys from agent
ssh-add -D

# Step 7: Verify removal
ssh-add -l

# Step 8: Kill agent
ssh-agent -k
```

### Exercise 8: Automated Backup Script

```bash
# Task: Create an automated backup script

# Step 1: Create backup script
cat > ~/scripts/backup.sh << 'SCRIPT'
#!/bin/bash
# Simple backup script using rsync

SOURCE="$HOME/projects/"
DEST_SERVER="user@backup-server.com"
DEST_PATH="/backups/termux/"
LOG="$HOME/backup.log"
DATE=$(date)

log() {
    echo "[$DATE] $1" >> "$LOG"
}

# Check if source exists
if [ ! -d "$SOURCE" ]; then
    log "ERROR: Source directory not found"
    exit 1
fi

# Run backup
log "Starting backup..."
rsync -avz --progress "$SOURCE" "$DEST_SERVER:$DEST_PATH"

if [ $? -eq 0 ]; then
    log "Backup completed successfully"
else
    log "ERROR: Backup failed"
fi
SCRIPT

# Step 2: Make executable
chmod +x ~/scripts/backup.sh

# Step 3: Create test data
mkdir -p ~/projects
echo "Important data" > ~/projects/important.txt

# Step 4: Test the script (you'll need a real server)
# ~/scripts/backup.sh

# Step 5: View log
# cat ~/backup.log
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Connection refused"

```bash
# Cause: SSH service not running or port blocked

# Diagnosis:
# Check if port is open
nc -zv server.com 22

# Check if SSH is installed
pkg list-installed | grep openssh

# Solutions:

# 1. Check server status
ssh -v user@server

# 2. Try different port
ssh -p 2222 user@server

# 3. Check firewall on server side
# On server: sudo ufw status
# On server: sudo iptables -L

# 4. Check SSH service on server
# On server: sudo systemctl status sshd
```

### Problem 2: "Permission denied (publickey)"

```bash
# Cause: Key not recognized or not provided

# Diagnosis:
ssh -vvv user@server 2>&1 | grep -i "auth"

# Solutions:

# 1. Check key permissions
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub

# 2. Specify key explicitly
ssh -i ~/.ssh/mykey user@server

# 3. Add key to agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# 4. Copy key to server
ssh-copy-id -i ~/.ssh/id_ed25519.pub user@server

# 5. Check if key is added to authorized_keys
# On server: cat ~/.ssh/authorized_keys

# 6. Verify key type matches server requirements
ssh-keygen -lf ~/.ssh/id_ed25519.pub
```

### Problem 3: "Host key verification failed"

```bash
# Cause: Server key changed or mismatch

# Solution 1: Remove old key
ssh-keygen -R server.com

# Solution 2: Remove by IP
ssh-keygen -R 192.168.1.100

# Solution 3: Edit known_hosts manually
nano ~/.ssh/known_hosts
# Delete the offending line

# Solution 4: Temporary bypass (not recommended for production)
ssh -o StrictHostKeyChecking=no user@server

# Solution 5: Clear all known hosts (nuclear option)
> ~/.ssh/known_hosts
```

### Problem 4: "Connection timed out"

```bash
# Cause: Network issues or server unreachable

# Diagnosis:
# Test connectivity
ping -c 3 server.com

# Test port
nc -zv server.com 22

# Solutions:

# 1. Increase timeout
ssh -o ConnectTimeout=30 user@server

# 2. Check if server is up
ping server.com

# 3. Try with verbose output
ssh -vvv user@server

# 4. Check if using correct IP/hostname
host server.com
dig server.com

# 5. Try alternative port
ssh -p 2222 user@server

# 6. Check local network
curl -I https://google.com
```

### Problem 5: "No route to host"

```bash
# Cause: Network routing issue

# Solutions:

# 1. Check network connectivity
ping -c 3 8.8.8.8

# 2. Check DNS resolution
nslookup server.com

# 3. Check if VPN is interfering
# Disconnect VPN and try again

# 4. Check if on correct network
# Some servers only accessible from specific networks

# 5. Try IP instead of hostname
ssh user@192.168.1.100
```

### Problem 6: SSH key passphrase not working

```bash
# Cause: Wrong passphrase or corrupted key

# Solutions:

# 1. Verify key is not corrupted
ssh-keygen -lf ~/.ssh/id_ed25519

# 2. Test key with verbose output
ssh -v -i ~/.ssh/id_ed25519 user@server

# 3. Generate new key if necessary
ssh-keygen -t ed25519 -f ~/.ssh/new_key

# 4. Change passphrase
ssh-keygen -p -f ~/.ssh/id_ed25519

# 5. Check if using correct key
ls -la ~/.ssh/
```

### Problem 7: "Too many authentication failures"

```bash
# Cause: Too many keys being tried

# Solutions:

# 1. Specify key explicitly
ssh -i ~/.ssh/specific_key -o IdentitiesOnly=yes user@server

# 2. Clear SSH agent keys
ssh-add -D

# 3. Add only needed key
ssh-add ~/.ssh/correct_key

# 4. Use config file with IdentitiesOnly
Host myserver
    HostName server.com
    User user
    IdentityFile ~/.ssh/mykey
    IdentitiesOnly yes
```

### Problem 8: SCP/RSYNC not working

```bash
# Cause: SCP or rsync not installed on remote

# Solutions:

# 1. Check if command exists on remote
ssh user@server "which scp rsync"

# 2. Use SFTP instead
sftp user@server

# 3. Install rsync on remote (if you have sudo)
# ssh user@server "sudo apt install rsync"

# 4. Use tar over SSH as alternative
tar czf - ./localfiles | ssh user@server "tar xzf - -C /remote/path/"

# 5. Use SSH with redirection
ssh user@server "cat /remote/file.txt" > local_file.txt
```

### Problem 9: Slow SSH connection

```bash
# Cause: DNS resolution, encryption overhead, or network

# Solutions:

# 1. Disable DNS resolution on server (if admin)
# Add to /etc/ssh/sshd_config: UseDNS no

# 2. Use faster cipher
ssh -c aes128-gcm@openssh.com user@server

# 3. Enable compression for slow networks
ssh -C user@server

# 4. Use control master for persistent connections
# Add to ~/.ssh/config:
Host *
    ControlMaster auto
    ControlPath /tmp/ssh-%r@%h:%p
    ControlPersist 600

# 5. Reduce encryption overhead
ssh -o Ciphers=aes128-gcm@openssh.com user@server
```

### Problem 10: SSH session disconnects

```bash
# Cause: Timeout or network interruption

# Solutions:

# 1. Keep connection alive
ssh -o ServerAliveInterval=60 -o ServerAliveCountMax=3 user@server

# 2. Add to config
Host *
    ServerAliveInterval 60
    ServerAliveCountMax 3

# 3. Use screen or tmux for persistent sessions
ssh user@server "tmux new-session -d"

# 4. Use autossh for automatic reconnection
pkg install autossh -y
autossh -M 0 user@server
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔐 SSH CLIENT                    │
│   COMPLETE GUIDE                   │
│                                    │
│   ✓ Key Management                 │
│   ✓ File Transfer                  │
│   ✓ Tunneling                      │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Feature Highlight**
```
┌────────────────────────────────────┐
│  SSH CLIENT IN TERMUX              │
│  ─────────────────────────────     │
│                                    │
│  🔑 Keys    📁 SCP     🚇 Tunnels  │
│                                    │
│  25+ Commands | Full Guide         │
│                                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Security Focus**
```
┌────────────────────────────────────┐
│  ⚡ MASTER SSH CLIENT              │
│                                    │
│  Secure Remote Access              │
│  Key-Based Auth                    │
│  Advanced Tunneling                │
│                                    │
│  Chapter 46 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔐 Termux Full Course - Chapter 46: SSH Client Usage Complete Guide

🔥 In this video you'll learn:
• SSH client basics and connection methods
• SSH key generation and management
• Multiple keys with SSH config file
• SCP for secure file transfer
• SFTP interactive file operations
• RSYNC for directory synchronization
• SSH tunneling (Local, Remote, SOCKS)
• Jump hosts and SSH agent
• 25+ essential SSH commands

⏱️ Timestamps:
0:00 - Introduction
0:50 - SSH Client Basics
3:30 - SSH Key Generation
7:00 - Multiple SSH Keys
9:30 - SCP File Transfer
12:00 - SFTP Usage
14:00 - RSYNC in Termux
16:00 - SSH Tunneling
18:30 - SSH Jump Hosts
20:00 - SSH Agent
21:30 - Summary

📥 Essential Commands:
ssh-keygen -t ed25519 -C "my-key"
ssh-copy-id user@server
scp -r folder/ user@server:/path/
rsync -avz --progress source/ dest/
ssh -L 8080:localhost:80 user@server
ssh -D 9050 user@server

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#SSH #Termux #TermuxCourse #T3rmuxk1ng #SSHTutorial #SecureShell 
#LinuxCommands #RemoteAccess #FileTransfer #SSHTunnel

---
⚠️ Disclaimer: This video is for educational purposes. Only connect to servers you have permission to access.
```

### Tags List

```
ssh, ssh client, ssh tutorial, termux ssh, termux ssh client,
ssh key, ssh keygen, scp, sftp, rsync, ssh tunneling,
ssh port forwarding, socks proxy, ssh config, ssh agent,
termux tutorial, termux course, t3rmuxk1ng, linux ssh,
remote access, secure shell, file transfer, ssh jump host,
ssh automation, ssh commands, terminal, command line,
cybersecurity, ethical hacking, server management
```

### Hashtags

```
#SSH #Termux #TermuxCourse #SSHTutorial #SecureShell 
#RemoteAccess #FileTransfer #SSHTunnel #SSHClinet 
#LinuxCommands #T3rmuxk1ng #CyberSecurity #TermuxHindi
#SCP #SFTP #RSYNC #SSHKey #PortForwarding
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| OpenSSH Manual | https://www.openssh.com/manual.html |
| SSH Config Syntax | https://linux.die.net/man/5/ssh_config |
| SSH Protocol RFC | https://tools.ietf.org/html/rfc4251 |

### Quick Reference Cards

```bash
# SSH Cheat Sheet - Save as ~/ssh-cheatsheet.txt

=== CONNECTION ===
ssh user@host                    # Basic connection
ssh -p PORT user@host            # Custom port
ssh -i KEY user@host             # Specific key
ssh -L PORT:localhost:PORT host  # Local tunnel
ssh -D PORT host                 # SOCKS proxy

=== KEYS ===
ssh-keygen -t ed25519            # Generate key
ssh-copy-id user@host            # Copy to server
ssh-add -l                       # List agent keys

=== TRANSFER ===
scp FILE user@host:PATH          # Upload
scp user@host:FILE .             # Download
rsync -avz SRC/ DEST/            # Sync

=== TROUBLESHOOT ===
ssh -vvv user@host               # Verbose debug
ssh-keygen -R host               # Remove from known_hosts
```

### Useful SSH Config Templates

```bash
# Minimal config
Host myserver
    HostName 192.168.1.100
    User root

# Full config with all options
Host complete-example
    HostName server.example.com
    User username
    Port 2222
    IdentityFile ~/.ssh/specific_key
    IdentitiesOnly yes
    ServerAliveInterval 60
    ServerAliveCountMax 3
    Compression yes
    ForwardAgent yes
    LocalForward 8080 localhost:80
    DynamicForward 9050
    ProxyJump jump-server
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 47, verify:

- [ ] SSH client installed (`pkg install openssh`)
- [ ] Can connect to a remote server
- [ ] Generated at least one SSH key pair
- [ ] Created SSH config file with at least one host
- [ ] Successfully transferred files with SCP
- [ ] Used rsync for directory sync
- [ ] Created at least one SSH tunnel
- [ ] Used SSH agent for key management
- [ ] Understood local, remote, and dynamic forwarding
- [ ] Know how to troubleshoot common SSH issues

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 47: Web Server in Termux**

- Setting up Apache HTTP Server
- Nginx installation and configuration
- Python simple HTTP server
- PHP and MySQL setup
- Hosting local websites
- Reverse proxy configuration
- SSL/HTTPS setup

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
