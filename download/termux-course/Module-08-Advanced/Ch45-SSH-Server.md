# Chapter 45: SSH Server in Termux

> **Module:** 8 - Advanced  
> **Chapter:** 45 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | SSH fundamentals, setup & configuration |
| Installation Guide | OpenSSH installation & setup |
| Authentication | Password & key-based authentication |
| Advanced Features | Tunneling, port forwarding, SCP/SFTP |
| Commands Reference | 25+ SSH commands covered |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common SSH issues & fixes |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 45
Title: SSH Server in Termux | Remote Access Your Phone | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Main aapka host hoon aur aaj ka chapter bahut special hai - SSH Server!

Kya aapne kabhi socha hai ki aap apne Android phone ko remotely access 
kar sakte ho? Bina phone touch kiye - dusre computer se, dusre phone 
se, ya duniya ke kisi bhi corner se?

SSH - Secure Shell - ye sab possible bana deta hai. Aapka Android phone 
ek server ban jaata hai jisko aap kahi se bhi access kar sakte ho.

Ye chapter advanced hai, isliye dhyan se suniye aur practice karein. 
Agar previous chapters dekhe hain - networking basics, Linux commands, 
file system - to ye chapter easy lagega.

Chaliye shuru karte hain!

---

[SECTION 1: SSH FUNDAMENTALS - 1:00 to 4:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - SSH kya hai?

SSH stands for Secure Shell. Ye ek protocol hai - ek tareeka jisse 
do computers securely communicate karte hain over network.

Samjhiye aapke paas do computers hain:
- Ek Server (jisko access karna hai) - ye aapka Android phone hai
- Ek Client (jisse access karna hai) - ye aapka PC ya dusra phone hai

SSH in dono ke beech ek encrypted tunnel banata hai. Is tunnel ke 
through aap:
✓ Remote commands execute kar sakte ho
✓ Files transfer kar sakte ho
✓ Port forwarding kar sakte ho
✓ Secure browsing kar sakte ho

SSH vs Other Remote Access Methods:

┌─────────────────────────────────────────────────────────────────────────┐
│                    REMOTE ACCESS COMPARISON                              │
├────────────────┬──────────────────┬─────────────────────────────────────┤
│ Method         │ Encryption       │ Best For                            │
├────────────────┼──────────────────┼─────────────────────────────────────┤
│ SSH            │ ✅ Yes (Strong)  │ Servers, Linux systems, Termux      │
│ Telnet         │ ❌ No (Plain)    │ Only testing, NEVER production      │
│ RDP            │ ✅ Yes           │ Windows GUI remote desktop          │
│ VNC            │ ⚠️ Optional      │ GUI remote access                   │
│ FTP            │ ❌ No (Plain)    │ File transfer (insecure)            │
│ SFTP (SSH)     │ ✅ Yes           │ Secure file transfer                │
└────────────────┴──────────────────┴─────────────────────────────────────┘

SSH port 22 pe kaam karta hai by default. Lekin aap koi bhi port 
configure kar sakte ho.

SSH ki power ye hai ki ye end-to-end encryption deta hai. Koi bhi 
middle man aapka data nahi dekh sakta - na passwords, na commands, 
na files - kuch bhi nahi!

Isliye ethical hackers, system admins, developers - sab SSH use 
karte hain.

---

[SECTION 2: OPENSSH INSTALLATION - 4:30 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye Termux mein SSH server install karte hain.

Termux mein OpenSSH package available hai. OpenSSH most popular 
SSH implementation hai - free, open-source, aur highly secure.

[OPEN TERMUX - Show terminal]

Pehle update karein:

    pkg update && pkg upgrade -y

Ab OpenSSH install karein:

    pkg install openssh -y

Ye package install hoga aur sath mein ye tools milenge:
- sshd - SSH server daemon
- ssh - SSH client
- scp - Secure copy
- sftp - Secure file transfer
- ssh-keygen - Key generation tool
- ssh-copy-id - Copy keys to server

Installation verify karein:

    sshd -V
    ssh -V

Version number dikhna chahiye. Agar dikh raha hai to installation 
successful hai!

Ek aur important package - nmap (optional but useful):

    pkg install nmap -y

Nmap se hum check karenge ki SSH server properly run ho raha hai ya nahi.

---

[SECTION 3: STARTING SSH SERVER - 7:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab SSH server start karte hain.

Pehle ek important cheez - Password set karna!

SSH server ke liye aapko Termux mein password set karna padega. 
Default mein Termux mein password nahi hota.

Password set karein:

    passwd

Ye command run karein, aapko new password enter karna hoga. 
Password type karte waqt screen pe kuch nahi dikhega - ye 
security feature hai. Do baar enter karein.

Password strong rakhein - combination of letters, numbers, symbols.

Ab SSH server start karein:

    sshd

Bas! Itna hi! SSH server chal pada hai!

Check karein:

    pgrep sshd

Agar output mein ek process ID aaye to server run ho raha hai.

Ya phir:

    ps aux | grep sshd

Port check karein:

    nmap localhost

Ya:

    netstat -tlnp | grep 22

Output mein port 22 pe SSH listen karta dikhega.

---

[SECTION 4: SSH CONFIGURATION - 10:00 to 13:00]
─────────────────────────────────────────────────────────────────────────────

Ab SSH configuration samjhte hain.

Configuration file location:

    $PREFIX/etc/ssh/sshd_config

Default configuration already set hai, lekin customize kar sakte hain.

File dekhein:

    cat $PREFIX/etc/ssh/sshd_config

Important settings:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SSH CONFIGURATION OPTIONS                             │
├─────────────────────────────┬───────────────────────────────────────────┤
│ Setting                     │ Description                               │
├─────────────────────────────┼───────────────────────────────────────────┤
│ Port 22                     │ SSH port (change for security)            │
│ ListenAddress 0.0.0.0       │ Listen on all interfaces                  │
│ PermitRootLogin no          │ Disable root login                        │
│ PasswordAuthentication yes  │ Enable password auth                      │
│ PubkeyAuthentication yes    │ Enable key-based auth                     │
│ PermitEmptyPasswords no     │ No empty passwords                        │
│ MaxAuthTries 3              │ Max login attempts                        │
│ ClientAliveInterval 300     │ Disconnect inactive clients               │
└─────────────────────────────┴───────────────────────────────────────────┘

Port change karna ho to:

    nano $PREFIX/etc/ssh/sshd_config

"Port 22" ko change karein to something else like "Port 2222"

Note: Configuration change ke baad server restart karna padega:

    pkill sshd
    sshd

---

[SECTION 5: CONNECTING FROM PC - 13:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Ab main part - apne phone ko PC se connect karte hain!

Pehle phone ka IP address nikalein:

    ifconfig

Ya:

    ip addr show wlan0

Ya simple:

    hostname -I

IP address note kar lein, for example: 192.168.1.100

Ab PC pe jao (Windows/Mac/Linux):

[ON PC]

Windows ke liye:
- Command Prompt ya PowerShell open karein
- Command: ssh <username>@<phone-ip>
- Termux mein default username: u0_aXXX format ya simple

Pehle Termux mein username check karein:

    whoami

Output username note karein.

Ab PC se connect karein:

    ssh -p 22 <username>@192.168.1.100

Example:

    ssh -p 22 u0_a123@192.168.1.100

First time connect karte waqt ek message aayega:

"The authenticity of host '192.168.1.100' can't be established.
ECDSA key fingerprint is SHA256:xxxxx.
Are you sure you want to continue connecting (yes/no)?"

Type "yes" and press Enter.

Ab password poocha jaayega. Wo password enter karein jo aapne 
Termux mein `passwd` command se set kiya tha.

Login ho gaya! 🎉

Ab aap PC se apne Android phone ko control kar rahe ho!

Test karein:

    pwd
    ls
    whoami
    hostname

Sab commands Termux ke environment mein run hongi!

---

[SECTION 6: CONNECTING FROM ANOTHER PHONE - 16:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Dusre phone se bhi connect kar sakte ho!

Dusre phone mein Termux install hona chahiye.

[ON SECOND PHONE]

Termux open karein:

    pkg install openssh -y

Ab connect karein:

    ssh <username>@<phone1-ip>

Same process - first time "yes" type karein, password enter karein.

Baaki sab same hai!

---

[SECTION 7: SSH KEY-BASED AUTHENTICATION - 17:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Ab security ka next level - Key-based Authentication!

Password authentication mein ek problem hai - brute force attacks. 
Koi dictionary attack kar sakta hai.

Key-based authentication mein aap ek pair of keys generate karte ho:
- Private Key - Ye sirf aapke paas rehti hai, SHARE NAHIN KARNA!
- Public Key - Ye server pe rehti hai

Key generation:

[ON CLIENT PC/PHONE]

    ssh-keygen -t rsa -b 4096

Ya Ed25519 (more modern):

    ssh-keygen -t ed25519

Ye command aapse location poochegi - default mein ~/.ssh/id_rsa

Passphrase set kar sakte ho (additional security) - ya Enter press 
karke skip kar sakte ho.

Keys generate ho gayi!

Ab public key server pe copy karein:

Method 1 - ssh-copy-id:

    ssh-copy-id <username>@<server-ip>

Method 2 - Manual copy:

    cat ~/.ssh/id_rsa.pub

Ye output copy karein.

Server (Termux) pe jao:

    mkdir -p ~/.ssh
    nano ~/.ssh/authorized_keys

Public key paste karein, save karein.

Permissions set karein:

    chmod 700 ~/.ssh
    chmod 600 ~/.ssh/authorized_keys

Ab password disable kar sakte ho:

    nano $PREFIX/etc/ssh/sshd_config

Change:

    PasswordAuthentication no

Server restart:

    pkill sshd
    sshd

Ab sirf key se login hoga!

Test:

    ssh <username>@<server-ip>

Direct login - no password! 🚀

---

[SECTION 8: SCP & SFTP FILE TRANSFER - 21:00 to 23:00]
─────────────────────────────────────────────────────────────────────────────

SSH ke saath files bhi transfer kar sakte ho!

SCP - Secure Copy:

PC se phone pe file bhejni:

    scp /path/to/local/file.txt <username>@<phone-ip>:/home/username/

Phone se PC pe file lani:

    scp <username>@<phone-ip>:/home/username/file.txt /local/path/

Whole folder:

    scp -r /local/folder/ <username>@<phone-ip>:/home/username/

SFTP - Interactive File Transfer:

    sftp <username>@<phone-ip>

Commands:
- ls - list remote files
- lls - list local files
- get file.txt - download file
- put file.txt - upload file
- mkdir - create directory
- rm file - delete file
- exit - disconnect

Ye GUI FTP client jaisa hai but command line pe!

---

[SECTION 9: SSH TUNNELING & PORT FORWARDING - 23:00 to 25:00]
─────────────────────────────────────────────────────────────────────────────

SSH tunneling ek powerful feature hai!

Local Port Forwarding:

Scenario: Aapke phone pe ek web server hai port 8080 pe. PC se access karna hai.

    ssh -L 8080:localhost:8080 <username>@<phone-ip>

Ab PC pe browser mein: http://localhost:8080

Ye phone ke port 8080 ko PC ke port 8080 pe tunnel kar diya!

Remote Port Forwarding:

Phone ke local service ko expose karna internet pe:

    ssh -R 8080:localhost:80 <username>@<public-server>

Dynamic Port Forwarding (SOCKS Proxy):

    ssh -D 9050 <username>@<phone-ip>

Ab proxy configure karo: localhost:9050

All traffic SSH tunnel se jaayega!

---

[SECTION 10: SSH OVER INTERNET - 25:00 to 27:30]
─────────────────────────────────────────────────────────────────────────────

Local network se to connect kar liya, lekin internet se kaise?

Problem: Most phones ke paas public IP nahi hota. NAT ke peeche hote hain.

Solution: Tunneling Services!

Option 1: Ngrok

    pkg install ngrok

    ngrok tcp 22

Ye aapko ek public URL dega like: tcp://0.tcp.ngrok.io:12345

Dusri jagah se connect:

    ssh -p 12345 <username>@0.tcp.ngrok.io

Option 2: Serveo (No installation needed)

    ssh -R 22:localhost:22 serveo.net

Ye automatically ek subdomain dega!

Option 3: Cloudflare Tunnel (cloudflared)

    pkg install cloudflared
    cloudflared tunnel --url ssh://localhost:22

---

[SECTION 11: SECURITY BEST PRACTICES - 27:30 to 29:00]
─────────────────────────────────────────────────────────────────────────────

SSH powerful hai, lekin security important hai!

✓ DO:
- Strong password use karein
- Key-based authentication use karein
- Default port change karein (security through obscurity)
- Fail2Ban jaisa tools use karein
- SSH logs monitor karein
- Regular updates rakhein
- Only necessary users ko access dein

✗ DON'T:
- Empty password mat rakhein
- Private key share mat karein
- Untrusted networks pe SSH mat use karein (without VPN)
- Root login enable mat karein (agar not needed)
- Default port pe persistent attacks ignore mat karein

Logs check:

    cat $PREFIX/var/log/auth.log

Ya:

    last

Ye login history dikhayega!

---

[SECTION 12: SUMMARY & NEXT PREVIEW - 29:00 to 30:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 45 complete! Let's summarize:

✅ SSH fundamentals samjhe
✅ OpenSSH installation
✅ SSH server start/stop
✅ Password authentication setup
✅ PC se connection
✅ Phone se connection
✅ Key-based authentication
✅ SCP/SFTP file transfer
✅ SSH tunneling
✅ Port forwarding
✅ SSH over internet (ngrok/serveo)
✅ Security best practices

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 45 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install openssh             │ Install SSH server                    │
│ passwd                          │ Set password for SSH                  │
│ sshd                            │ Start SSH server                      │
│ pkill sshd                      │ Stop SSH server                       │
│ ssh-keygen -t ed25519           │ Generate SSH keys                     │
│ ssh user@ip                     │ Connect to SSH server                 │
│ scp file user@ip:/path          │ Secure copy file                      │
│ sftp user@ip                    │ Interactive file transfer             │
│ ssh -L port:localhost:port ip   │ Local port forwarding                │
│ ssh -D 9050 user@ip             │ Dynamic port forwarding (SOCKS)      │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 46 mein hum SSH Client seekhenge - kaise dusre servers 
ko Termux se connect karein, SSH config files, aliases, aur more!

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 46!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. SSH Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         SSH ARCHITECTURE                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   CLIENT MACHINE                        SERVER (Termux)                  │
│   ┌─────────────────┐                   ┌─────────────────┐              │
│   │   SSH Client    │                   │   SSH Server    │              │
│   │   (ssh command) │                   │   (sshd daemon) │              │
│   └────────┬────────┘                   └────────┬────────┘              │
│            │                                     │                        │
│            │     ┌───────────────────────┐      │                        │
│            │     │   ENCRYPTED TUNNEL    │      │                        │
│            ├────►│  (AES-256, etc.)      │◄─────┤                        │
│            │     │   Port 22 (default)   │      │                        │
│            │     └───────────────────────┘      │                        │
│            │                                     │                        │
│   Authentication Methods:                        │                        │
│   ├─ Password Authentication                     │                        │
│   ├─ Public Key Authentication                   │                        │
│   └─ Host-based Authentication                   │                        │
│                                                                          │
│   Data Protected:                                                        │
│   ├─ Commands                                                            │
│   ├─ File transfers (SCP/SFTP)                                          │
│   ├─ Port forwarded traffic                                             │
│   └─ X11 forwarding (GUI apps)                                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. SSH Handshake Process

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      SSH HANDSHAKE PROCESS                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  CLIENT                                    SERVER                        │
│    │                                         │                           │
│    │──── 1. TCP Connection (SYN) ──────────►│                           │
│    │◄─── 2. TCP Connection (SYN-ACK) ───────│                           │
│    │──── 3. TCP Connection (ACK) ──────────►│                           │
│    │                                         │                           │
│    │──── 4. SSH Version Exchange ──────────►│                           │
│    │◄─── 5. SSH Version Exchange ───────────│                           │
│    │                                         │                           │
│    │──── 6. Algorithm Negotiation ─────────►│                           │
│    │◄─── 7. Algorithm Negotiation ──────────│                           │
│    │                                         │                           │
│    │──── 8. DH Key Exchange Init ──────────►│                           │
│    │◄─── 9. DH Key Exchange Reply ──────────│                           │
│    │                                         │                           │
│    │◄─── 10. Server Host Key ───────────────│ (First time: save to     │
│    │                                         │  ~/.ssh/known_hosts)     │
│    │                                         │                           │
│    │════ ENCRYPTED CHANNEL ESTABLISHED ═════│                           │
│    │                                         │                           │
│    │──── 11. Authentication Request ───────►│                           │
│    │◄─── 12. Authentication Methods ────────│                           │
│    │                                         │                           │
│    │──── 13. Password/Key Auth ────────────►│                           │
│    │◄─── 14. Authentication Success ────────│                           │
│    │                                         │                           │
│    │═════════ SSH SESSION ACTIVE ═══════════│                           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 3. Key File Locations

| Location | Purpose |
|----------|---------|
| `$PREFIX/etc/ssh/sshd_config` | SSH server configuration |
| `$PREFIX/etc/ssh/ssh_config` | SSH client configuration |
| `~/.ssh/authorized_keys` | Public keys for login |
| `~/.ssh/known_hosts` | Known server fingerprints |
| `~/.ssh/id_rsa` | Default private key (RSA) |
| `~/.ssh/id_rsa.pub` | Default public key (RSA) |
| `~/.ssh/id_ed25519` | Default private key (Ed25519) |
| `~/.ssh/id_ed25519.pub` | Default public key (Ed25519) |
| `$PREFIX/var/run/sshd.pid` | SSH daemon process ID |

### 4. SSH Configuration Options

```bash
# $PREFIX/etc/ssh/sshd_config - Server Configuration

# Network Settings
Port 22                          # SSH port (change for security)
ListenAddress 0.0.0.0            # Listen on all interfaces
AddressFamily any                # IPv4 and IPv6

# Authentication
PermitRootLogin no               # Disable root login
PubkeyAuthentication yes         # Enable key-based auth
PasswordAuthentication yes       # Enable password auth
PermitEmptyPasswords no          # No empty passwords
MaxAuthTries 3                   # Max login attempts
MaxSessions 10                   # Max sessions per connection

# Security
ChallengeResponseAuthentication no
UsePAM no                        # Not available in Termux
X11Forwarding no                 # Disable X11 forwarding
PrintMotd yes                    # Print message of the day

# Logging
SyslogFacility AUTH
LogLevel INFO

# Timeout Settings
ClientAliveInterval 300          # Check client every 5 min
ClientAliveCountMax 2            # Disconnect after 2 misses

# Subsystems
Subsystem sftp $PREFIX/libexec/sftp-server
```

---

## 🔧 INSTALLATION & SETUP GUIDE

### Step-by-Step SSH Server Setup

```bash
# Step 1: Update Termux
pkg update && pkg upgrade -y

# Step 2: Install OpenSSH
pkg install openssh -y

# Step 3: Set password for SSH authentication
passwd
# Enter strong password twice

# Step 4: Start SSH server
sshd

# Step 5: Verify server is running
pgrep sshd
# Output: Process ID (e.g., 12345)

# Step 6: Check SSH port is listening
netstat -tlnp | grep 22
# Or: nmap localhost

# Step 7: Get your IP address
hostname -I
# Or: ifconfig wlan0

# Step 8: Test connection locally
ssh localhost
# Or: ssh 127.0.0.1
```

### Auto-start SSH on Termux Launch

```bash
# Create bashrc entry
echo 'sshd' >> ~/.bashrc

# Or use Termux:Boot for startup
mkdir -p ~/.termux/boot
echo '#!/data/data/com.termux/files/usr/bin/sh
sshd' > ~/.termux/boot/sshd-start.sh
chmod +x ~/.termux/boot/sshd-start.sh
```

---

## 🔑 KEY-BASED AUTHENTICATION

### Generating SSH Keys

```bash
# RSA Key (4096 bits - traditional)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# Ed25519 Key (Modern, faster, more secure)
ssh-keygen -t ed25519 -C "your_email@example.com"

# ECDSA Key (256 bits)
ssh-keygen -t ecdsa -b 256 -C "your_email@example.com"

# With custom filename
ssh-keygen -t ed25519 -f ~/.ssh/my_custom_key -C "description"

# Without passphrase (less secure, but convenient)
ssh-keygen -t ed25519 -N "" -C "no_passphrase"
```

### Setting Up Authorized Keys

```bash
# On SERVER (Termux):
# Create .ssh directory
mkdir -p ~/.ssh

# Set proper permissions
chmod 700 ~/.ssh

# Create authorized_keys file
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

# Edit and add public key
nano ~/.ssh/authorized_keys
# Paste your public key content (id_ed25519.pub or id_rsa.pub)
```

### Copying Keys to Server

```bash
# Method 1: ssh-copy-id (easiest)
ssh-copy-id -i ~/.ssh/id_ed25519.pub username@server-ip

# Method 2: Manual copy via SSH
cat ~/.ssh/id_ed25519.pub | ssh username@server-ip "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"

# Method 3: SCP copy
scp ~/.ssh/id_ed25519.pub username@server-ip:~/.ssh/authorized_keys
```

### Disable Password Authentication

```bash
# Edit SSH config
nano $PREFIX/etc/ssh/sshd_config

# Change these lines:
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM no

# Restart SSH server
pkill sshd
sshd
```

---

## 📡 CONNECTION METHODS

### Connecting from PC (Windows/Mac/Linux)

```bash
# Basic connection
ssh username@192.168.1.100

# With specific port
ssh -p 2222 username@192.168.1.100

# With specific identity file
ssh -i ~/.ssh/my_key username@192.168.1.100

# With verbose output (debugging)
ssh -v username@192.168.1.100
ssh -vvv username@192.168.1.100  # Maximum verbosity

# Running command on remote server
ssh username@192.168.1.100 "ls -la"

# With X11 forwarding (GUI apps)
ssh -X username@192.168.1.100

# With SSH agent forwarding
ssh -A username@192.168.1.100
```

### SSH Config File for Easy Connections

```bash
# Create/edit ~/.ssh/config
nano ~/.ssh/config

# Add entries:
Host termux
    HostName 192.168.1.100
    Port 22
    User u0_a123
    IdentityFile ~/.ssh/id_ed25519
    ServerAliveInterval 60
    ServerAliveCountMax 3

Host termux-tunnel
    HostName 192.168.1.100
    Port 2222
    User u0_a123
    LocalForward 8080 localhost:8080

# Now simply connect with:
ssh termux

# Instead of:
ssh -p 22 -i ~/.ssh/id_ed25519 u0_a123@192.168.1.100
```

---

## 🚇 SSH TUNNELING & PORT FORWARDING

### Local Port Forwarding (-L)

```bash
# Syntax: ssh -L [local_port]:[remote_host]:[remote_port] user@server

# Forward phone's web server (port 8080) to PC's localhost:8080
ssh -L 8080:localhost:8080 username@phone-ip

# Forward phone's database (port 3306) to PC's localhost:3306
ssh -L 3306:localhost:3306 username@phone-ip

# Access remote service through SSH tunnel
ssh -L 9000:internal-server:80 username@jump-server

# Multiple tunnels in one command
ssh -L 8080:localhost:8080 -L 3306:localhost:3306 username@phone-ip
```

### Remote Port Forwarding (-R)

```bash
# Syntax: ssh -R [remote_port]:[local_host]:[local_port] user@server

# Expose local service on remote server
ssh -R 8080:localhost:3000 username@public-server

# Expose local web server to internet via remote server
ssh -R 80:localhost:8080 username@public-server
```

### Dynamic Port Forwarding (-D) - SOCKS Proxy

```bash
# Create SOCKS proxy on local port 9050
ssh -D 9050 username@server-ip

# Use with applications:
# Firefox: Settings → Network → Manual proxy → SOCKS: localhost:9050
# curl: curl --socks5 localhost:9050 http://example.com

# With SSH config for easy use
Host socks-proxy
    HostName server-ip
    DynamicForward 9050
```

### Reverse SSH Tunnel (For NAT Traversal)

```bash
# On phone (behind NAT), connect to public server
ssh -R 2222:localhost:22 username@public-server

# Now from any machine, connect to phone via public server
ssh -p 2222 phone-username@public-server
```

---

## 📁 FILE TRANSFER (SCP/SFTP)

### SCP - Secure Copy

```bash
# Copy local file to remote server
scp /path/to/local/file.txt username@server:/path/to/destination/

# Copy remote file to local machine
scp username@server:/path/to/remote/file.txt /local/destination/

# Copy entire directory
scp -r /local/directory/ username@server:/remote/destination/

# With specific port
scp -P 2222 file.txt username@server:/path/

# With specific identity
scp -i ~/.ssh/key file.txt username@server:/path/

# Preserve timestamps and permissions
scp -p file.txt username@server:/path/

# Show progress and statistics
scp -v file.txt username@server:/path/

# Limit bandwidth (KB/s)
scp -l 100 file.txt username@server:/path/
```

### SFTP - Interactive File Transfer

```bash
# Connect to SFTP
sftp username@server

# SFTP Commands:
sftp> help                    # Show all commands
sftp> ls                      # List remote files
sftp> lls                     # List local files
sftp> pwd                     # Print remote working directory
sftp> lpwd                    # Print local working directory
sftp> cd /path                # Change remote directory
sftp> lcd /path               # Change local directory
sftp> mkdir dirname           # Create remote directory
sftp> rmdir dirname           # Remove remote directory
sftp> get file.txt            # Download file
sftp> get -r directory/       # Download directory
sftp> put file.txt            # Upload file
sftp> put -r directory/       # Upload directory
sftp> rm file.txt             # Delete remote file
sftp> rename old new          # Rename remote file
sftp> chmod 755 file          # Change permissions
sftp> chown user:group file   # Change ownership
sftp> exit                    # Exit SFTP

# Batch mode - download multiple files
sftp username@server << EOF
cd /remote/path
get file1.txt
get file2.txt
get file3.txt
exit
EOF
```

### rsync over SSH

```bash
# Install rsync
pkg install rsync -y

# Sync local to remote
rsync -avz /local/path/ username@server:/remote/path/

# Sync remote to local
rsync -avz username@server:/remote/path/ /local/path/

# With progress bar
rsync -avz --progress /local/path/ username@server:/remote/path/

# Delete files that don't exist in source
rsync -avz --delete /local/path/ username@server:/remote/path/

# Exclude certain files
rsync -avz --exclude '*.log' /local/path/ username@server:/remote/path/

# Dry run (test without actual transfer)
rsync -avz --dry-run /local/path/ username@server:/remote/path/
```

---

## 🌐 SSH OVER INTERNET

### Using Ngrok

```bash
# Install ngrok
pkg install ngrok

# Sign up at ngrok.com and get auth token
ngrok config add-authtoken YOUR_AUTH_TOKEN

# Create TCP tunnel for SSH
ngrok tcp 22

# Output:
# Session Status: online
# Forwarding: tcp://0.tcp.ngrok.io:12345 -> localhost:22

# Connect from anywhere:
ssh -p 12345 username@0.tcp.ngrok.io
```

### Using Serveo

```bash
# No installation required!
# Just run:
ssh -R 22:localhost:22 serveo.net

# Or specify port:
ssh -R yourname:22:localhost:22 serveo.net

# Connect with:
ssh -o ProxyCommand="nc -X 5 -x yourname.serveo.net:22 %h %p" username@localhost
```

### Using Cloudflare Tunnel

```bash
# Install cloudflared
pkg install cloudflared

# Create tunnel
cloudflared tunnel --url ssh://localhost:22

# Or use cloudflare access
cloudflared access ssh --hostname your-domain.com
```

### Using Tailscale (Mesh VPN)

```bash
# Install tailscale
pkg install tailscale

# Start tailscale
tailscaled &
tailscale up

# Follow URL to authenticate
# Now all devices on your tailnet can connect directly

# Connect using tailscale IP
ssh username@100.x.y.z
```

---

## 📋 COMMANDS REFERENCE

### SSH Server Commands

```bash
# Installation & Setup
pkg install openssh              # Install OpenSSH
passwd                           # Set/change password for SSH

# Server Control
sshd                             # Start SSH server
pkill sshd                       # Stop SSH server
pgrep sshd                       # Check if running
ps aux | grep sshd               # Detailed process info

# Configuration
cat $PREFIX/etc/ssh/sshd_config  # View config
nano $PREFIX/etc/ssh/sshd_config # Edit config

# Logs & Monitoring
last                             # Login history
w                                # Who is logged in
who                              # Logged in users
```

### SSH Client Commands

```bash
# Basic Connection
ssh user@host                    # Connect to server
ssh -p 2222 user@host            # Specific port
ssh -i ~/.ssh/key user@host      # With identity file
ssh -v user@host                 # Verbose (debug)
ssh -vvv user@host               # Maximum verbosity

# Remote Command Execution
ssh user@host "command"          # Run single command
ssh user@host "cmd1; cmd2"       # Multiple commands
ssh user@host "cmd1 && cmd2"     # Conditional execution

# Tunneling
ssh -L 8080:localhost:80 user@host    # Local forward
ssh -R 8080:localhost:80 user@host    # Remote forward
ssh -D 9050 user@host                 # SOCKS proxy
ssh -L 8080:remote:80 user@host       # Forward to another host
```

### SSH Key Commands

```bash
# Key Generation
ssh-keygen -t ed25519            # Ed25519 key
ssh-keygen -t rsa -b 4096        # RSA 4096-bit key
ssh-keygen -t ecdsa -b 521       # ECDSA 521-bit key
ssh-keygen -f ~/.ssh/custom_key  # Custom filename

# Key Management
ssh-keygen -l -f ~/.ssh/id_ed25519.pub    # Fingerprint
ssh-keygen -y -f ~/.ssh/id_ed25519        # Show public from private
ssh-keygen -p -f ~/.ssh/id_ed25519        # Change passphrase
ssh-keygen -c -f ~/.ssh/id_ed25519        # Change comment
ssh-keygen -R hostname                     # Remove from known_hosts

# Copy Key to Server
ssh-copy-id user@host            # Copy default key
ssh-copy-id -i ~/.ssh/key.pub user@host  # Specific key
```

### SCP Commands

```bash
# Upload
scp file.txt user@host:/path/              # Single file
scp -r folder/ user@host:/path/            # Directory
scp file1.txt file2.txt user@host:/path/   # Multiple files

# Download
scp user@host:/path/file.txt ./            # Single file
scp -r user@host:/path/folder/ ./          # Directory

# Options
scp -P 2222 file user@host:/path/          # Specific port
scp -i ~/.ssh/key file user@host:/path/    # Identity file
scp -p file user@host:/path/               # Preserve attributes
scp -C file user@host:/path/               # Compress
scp -r -p -C folder/ user@host:/path/      # Combined options
```

### SFTP Commands

```bash
# Connect
sftp user@host                   # Connect to server
sftp -P 2222 user@host           # Specific port

# Navigation
pwd                              # Remote current directory
lpwd                             # Local current directory
ls                               # List remote
lls                              # List local
cd /path                         # Change remote directory
lcd /path                        # Change local directory

# File Operations
get file.txt                     # Download file
get -r folder/                   # Download directory
put file.txt                     # Upload file
put -r folder/                   # Upload directory
rm file.txt                      # Delete remote file
mkdir dirname                    # Create remote directory
rmdir dirname                    # Remove remote directory

# Batch Mode
sftp -b batchfile.txt user@host  # Run commands from file
```

### rsync Commands

```bash
# Basic Sync
rsync -avz source/ dest/         # Local sync
rsync -avz source/ user@host:dest/   # Push to remote
rsync -avz user@host:source/ dest/   # Pull from remote

# Options
-a                               # Archive mode (preserve all)
-v                               # Verbose
-z                               # Compress during transfer
-h                               # Human-readable
--progress                       # Show progress
--delete                         # Delete extra files in dest
--exclude 'pattern'              # Exclude files
--include 'pattern'              # Include files
--dry-run                        # Test without changes
--bwlimit=1000                   # Limit bandwidth (KB/s)

# Examples
rsync -avzhe ssh --progress /local/ user@host:/remote/
rsync -avz --delete --exclude '*.log' src/ user@host:dest/
```

### Network Diagnostic Commands

```bash
# Check SSH Port
netstat -tlnp | grep 22          # Check listening
nmap localhost                   # Scan localhost
nmap -p 22 phone-ip              # Scan remote

# IP Address
hostname -I                      # All IP addresses
ip addr show wlan0               # WiFi interface IP
ifconfig wlan0                   # WiFi IP (traditional)

# Connection Testing
ssh -T git@github.com            # Test GitHub SSH
nc -zv host 22                   # Test port connectivity
telnet host 22                   # Test SSH port (if available)
```

### SSH Agent Commands

```bash
# Start agent
eval $(ssh-agent)                # Start SSH agent

# Add keys
ssh-add                          # Add default key
ssh-add ~/.ssh/custom_key        # Add specific key
ssh-add -l                       # List added keys
ssh-add -L                       # List public keys
ssh-add -d ~/.ssh/key            # Remove key
ssh-add -D                       # Remove all keys

# Kill agent
ssh-agent -k                     # Kill SSH agent
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic SSH Setup

```bash
# Task: Set up SSH server and connect locally

# Step 1: Install and configure
pkg update && pkg upgrade -y
pkg install openssh -y

# Step 2: Set password
passwd
# Enter a strong password

# Step 3: Start server
sshd

# Step 4: Verify
pgrep sshd
netstat -tlnp | grep 22

# Step 5: Local connection test
ssh localhost
# Accept host key, enter password

# Step 6: Run commands
whoami
pwd
ls -la

# Step 7: Exit
exit

# Expected: Successfully connected and executed commands
```

### Exercise 2: SSH Key Setup

```bash
# Task: Generate and use SSH keys

# Step 1: Generate Ed25519 key
ssh-keygen -t ed25519 -C "my-termux-key"

# Step 2: View public key
cat ~/.ssh/id_ed25519.pub

# Step 3: Set up authorized keys
mkdir -p ~/.ssh
chmod 700 ~/.ssh
cat ~/.ssh/id_ed25519.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

# Step 4: Test key-based login
ssh localhost

# Expected: Login without password prompt
```

### Exercise 3: SCP File Transfer

```bash
# Task: Transfer files using SCP

# On Termux (Server):
# Step 1: Create test file
echo "This is a test file from Termux" > ~/test_file.txt
echo "Another file" > ~/another_file.txt
mkdir -p ~/test_folder
echo "File in folder" > ~/test_folder/folder_file.txt

# On PC (Client):
# Step 2: Download single file
scp username@phone-ip:~/test_file.txt ./

# Step 3: Download multiple files
scp username@phone-ip:~/{test_file.txt,another_file.txt} ./

# Step 4: Download directory
scp -r username@phone-ip:~/test_folder ./

# Step 5: Upload file to Termux
echo "From PC" > pc_file.txt
scp pc_file.txt username@phone-ip:~/

# Step 6: Verify on Termux
ls -la ~/
cat ~/pc_file.txt

# Expected: Files transferred successfully
```

### Exercise 4: SSH Tunneling

```bash
# Task: Create and use SSH tunnels

# Prerequisites: Install Python and create simple web server
pkg install python -y

# On Termux:
# Step 1: Create web content
mkdir -p ~/webroot
echo "<h1>Hello from Termux SSH Tunnel!</h1>" > ~/webroot/index.html

# Step 2: Start simple web server
cd ~/webroot
python -m http.server 8080 &

# Step 3: Verify local access
curl http://localhost:8080

# On PC:
# Step 4: Create SSH tunnel
ssh -L 9999:localhost:8080 username@phone-ip

# Step 5: Access through tunnel (in another terminal)
curl http://localhost:9999

# Or open in browser: http://localhost:9999

# Expected: Web content accessible via tunnel
```

### Exercise 5: SFTP Batch Operations

```bash
# Task: Automated file transfer with SFTP

# Step 1: Create batch file
cat > sftp_batch.txt << 'EOF'
mkdir backup
cd backup
put test_file.txt
put another_file.txt
get pc_file.txt
ls
exit
EOF

# Step 2: Run batch transfer
sftp -b sftp_batch.txt username@phone-ip

# Expected: Batch commands executed automatically
```

### Exercise 6: Port Forwarding Web Service

```bash
# Task: Expose Termux web service via SSH tunnel

# On Termux:
# Step 1: Install and start service
pkg install nodejs -y
node -e "require('http').createServer((req,res)=>res.end('Termux Web Server')).listen(3000)" &

# On PC:
# Step 2: Create tunnel
ssh -L 3000:localhost:3000 username@phone-ip

# Step 3: Access
curl http://localhost:3000
# Or browser: http://localhost:3000

# Expected: Web service accessible
```

### Exercise 7: SSH Over Internet with Ngrok

```bash
# Task: Access Termux SSH over internet

# Step 1: Install ngrok
pkg install ngrok -y

# Step 2: Configure (use your auth token from ngrok.com)
ngrok config add-authtoken YOUR_TOKEN

# Step 3: Create tunnel
ngrok tcp 22

# Step 4: Note the forwarding address
# Example: tcp://0.tcp.ngrok.io:12345

# Step 5: Connect from anywhere
ssh -p 12345 username@0.tcp.ngrok.io

# Expected: SSH connection over internet
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Connection refused"

```bash
# Cause: SSH server not running or wrong port

# Solution 1: Check if sshd is running
pgrep sshd
# If no output, start server:
sshd

# Solution 2: Check port
netstat -tlnp | grep 22
# Should show sshd listening on port 22

# Solution 3: Check firewall (if any)
# Termux doesn't have firewall by default

# Solution 4: Check if using correct port
# Default is 22, if changed:
ssh -p YOUR_PORT username@ip
```

### Problem 2: "Permission denied"

```bash
# Cause: Wrong password or key issue

# Solution 1: Verify password is set
passwd
# Set new password

# Solution 2: Check username
whoami
# Use exact username in SSH command

# Solution 3: For key-based auth, check permissions
ls -la ~/.ssh/
# Should be:
# .ssh/ = 700 (drwx------)
# authorized_keys = 600 (-rw-------)

# Fix permissions:
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

# Solution 4: Check if key is correct
ssh -v username@ip
# Look for "Trying private key" messages

# Solution 5: Check PasswordAuthentication setting
grep PasswordAuthentication $PREFIX/etc/ssh/sshd_config
# Should be "yes" if using password auth
```

### Problem 3: "Host key verification failed"

```bash
# Cause: Server key changed or first connection

# Solution 1: Remove old key
ssh-keygen -R server-ip
# Or:
ssh-keygen -R hostname

# Solution 2: Remove all known hosts (nuclear option)
rm ~/.ssh/known_hosts

# Solution 3: For first connection, type "yes" when prompted
# "Are you sure you want to continue connecting (yes/no)?"
```

### Problem 4: "Network is unreachable"

```bash
# Cause: Wrong IP or network issue

# Solution 1: Verify IP address
hostname -I
ip addr show wlan0

# Solution 2: Check if on same network
# Both devices must be on same WiFi for local access

# Solution 3: Check WiFi is connected
ping -c 3 google.com

# Solution 4: Use correct interface IP
# wlan0 = WiFi
# rmnet0 = Mobile data
```

### Problem 5: SSH slow or laggy

```bash
# Cause: DNS resolution or network issues

# Solution 1: Disable DNS lookup in config
nano $PREFIX/etc/ssh/sshd_config
# Add:
UseDNS no

# Solution 2: Use IP instead of hostname
ssh user@192.168.1.100  # Instead of ssh user@hostname

# Solution 3: Enable compression
ssh -C user@host

# Solution 4: Check network latency
ping phone-ip
```

### Problem 6: SSH session disconnects

```bash
# Cause: Timeout or network interruption

# Solution 1: Add keepalive to client config
nano ~/.ssh/config
# Add:
Host *
    ServerAliveInterval 60
    ServerAliveCountMax 3

# Solution 2: Add keepalive to server config
nano $PREFIX/etc/ssh/sshd_config
# Set:
ClientAliveInterval 300
ClientAliveCountMax 2

# Solution 3: Use screen/tmux for persistent sessions
pkg install screen tmux -y
screen -S mysession
# Reconnect: screen -r mysession
```

### Problem 7: "No route to host"

```bash
# Cause: Device not reachable on network

# Solution 1: Check WiFi connection
ifconfig wlan0

# Solution 2: Check if both on same network
# Android hotspot can have different subnet

# Solution 3: Check if WiFi isolation is enabled
# Some routers have AP isolation

# Solution 4: Try pinging first
ping phone-ip
```

### Problem 8: Port already in use

```bash
# Cause: Another service on port 22

# Solution 1: Find what's using port 22
netstat -tlnp | grep 22

# Solution 2: Use different port
nano $PREFIX/etc/ssh/sshd_config
# Change: Port 2222

# Restart:
pkill sshd
sshd

# Solution 3: Kill conflicting process
kill -9 $(lsof -t -i:22)
```

### Problem 9: Can't connect after changing config

```bash
# Cause: Syntax error in config

# Solution 1: Test config
sshd -t
# Will show errors if any

# Solution 2: Check config syntax
grep -v "^#" $PREFIX/etc/ssh/sshd_config | grep -v "^$"

# Solution 3: Restore default config
cp $PREFIX/etc/ssh/sshd_config $PREFIX/etc/ssh/sshd_config.bak
# Reinstall openssh
pkg reinstall openssh
```

### Problem 10: SCP/SFTP not working

```bash
# Cause: Subsystem not configured

# Solution 1: Check sftp subsystem
grep Subsystem $PREFIX/etc/ssh/sshd_config
# Should show: Subsystem sftp $PREFIX/libexec/sftp-server

# Solution 2: Add if missing
echo 'Subsystem sftp $PREFIX/libexec/sftp-server' >> $PREFIX/etc/ssh/sshd_config

# Solution 3: Restart sshd
pkill sshd
sshd

# Solution 4: Use scp with verbose
scp -v file user@host:/path/
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔐 SSH SERVER                    │
│   IN TERMUX                        │
│                                    │
│   ✓ Remote Access                  │
│   ✓ File Transfer                  │
│   ✓ No Root Required               │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Connection Style**
```
┌────────────────────────────────────┐
│  📱 Phone ←──── SSH ────→ 💻 PC    │
│                                    │
│  REMOTE ACCESS                     │
│  YOUR ANDROID                      │
│                                    │
│  🚀 Full Control                   │
│  🔒 Encrypted                      │
│                                    │
│  Chapter 45 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  ⚡ SSH SERVER MASTERY             │
│                                    │
│  ✅ Password Auth                  │
│  ✅ Key-based Auth                 │
│  ✅ Port Forwarding                │
│  ✅ SCP & SFTP                     │
│  ✅ Internet Access                │
│                                    │
│  Complete Guide!                   │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔐 Termux Full Course - Chapter 45: SSH Server in Termux | Remote Access Your Phone

🔥 In this video you'll learn:
• SSH fundamentals aur architecture
• OpenSSH installation aur configuration
• SSH server start/stop karna
• Password authentication setup
• SSH key generation aur setup
• PC se phone connect karna
• Dusre phone se connect karna
• SCP/SFTP se file transfer
• SSH tunneling aur port forwarding
• Internet se SSH access (ngrok/serveo)
• Security best practices

⏱️ Timestamps:
0:00 - Introduction
1:00 - SSH Fundamentals
4:30 - OpenSSH Installation
7:00 - Starting SSH Server
10:00 - SSH Configuration
13:00 - Connecting from PC
16:00 - Connecting from Another Phone
17:30 - Key-based Authentication
21:00 - SCP & SFTP File Transfer
23:00 - SSH Tunneling
25:00 - SSH Over Internet
27:30 - Security Best Practices
29:00 - Summary

📝 Commands from this video:
pkg install openssh -y
passwd
sshd
ssh-keygen -t ed25519
ssh user@ip
scp file user@ip:/path/

📥 Useful Links:
• OpenSSH: https://www.openssh.com/
• Ngrok: https://ngrok.com/
• Serveo: https://serveo.net/

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #SSH #TermuxCourse #T3rmuxk1ng #RemoteAccess #SSHServer #EthicalHacking #LinuxOnAndroid

---
⚠️ Disclaimer: This video is for educational purposes only. Use SSH responsibly and only on devices you own or have permission to access.
```

### Tags List

```
termux ssh, termux ssh server, ssh in termux, termux remote access,
ssh server android, termux openssh, ssh tutorial, ssh explained,
ssh key authentication, scp termux, sftp termux, ssh tunneling,
port forwarding ssh, termux course, termux full course, t3rmuxk1ng,
android ssh server, remote access android, ssh over internet,
ssh keygen, authorized_keys, ssh config, termux advanced,
ethical hacking, cybersecurity, linux commands
```

### Hashtags

```
#Termux #SSH #SSHServer #TermuxCourse #RemoteAccess #AndroidSSH
#EthicalHacking #CyberSecurity #T3rmuxk1ng #LinuxOnAndroid
#SCPSFTP #SSHTunneling #PortForwarding #SSHKeys #OpenSSH
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| OpenSSH Manual | https://www.openssh.com/manual.html |
| SSH Config Examples | https://man.openbsd.org/ssh_config |
| SSH Protocol RFC | https://tools.ietf.org/html/rfc4251 |
| Termux Wiki SSH | https://wiki.termux.com/wiki/Remote_Access |

### Learning Resources

| Resource | Description |
|----------|-------------|
| SSH Academy | https://www.ssh.com/academy/ssh |
| DigitalOcean SSH Guide | Comprehensive SSH tutorials |
| Red Hat SSH Documentation | Enterprise SSH best practices |
| Arch Wiki SSH | Detailed Linux SSH guide |

### Tools & Services

| Tool | Purpose |
|------|---------|
| OpenSSH | Standard SSH implementation |
| PuTTY | Windows SSH client (GUI) |
| MobaXterm | Advanced terminal for Windows |
| Termius | Cross-platform SSH client |
| Ngrok | TCP tunnel for internet access |
| Tailscale | Mesh VPN for secure access |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 46, verify:

- [ ] OpenSSH installed successfully
- [ ] Password set with `passwd` command
- [ ] SSH server starts with `sshd` command
- [ ] Able to connect locally (`ssh localhost`)
- [ ] Able to connect from PC on same network
- [ ] SSH keys generated (`ssh-keygen`)
- [ ] Key-based authentication working
- [ ] SCP file transfer tested
- [ ] SFTP commands understood
- [ ] Basic port forwarding attempted
- [ ] Configuration file location known
- [ ] Security best practices understood

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 46: SSH Client in Termux**

- SSH client configuration
- Connecting to external servers
- SSH config file customization
- SSH aliases and shortcuts
- SSH agent usage
- ProxyJump and jump hosts
- Advanced SSH options
- Troubleshooting remote connections

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
