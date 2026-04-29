# Chapter 47: Web Server in Termux

> **Module:** 8 - Advanced  
> **Chapter:** 47 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Web server options, configuration, deployment |
| Installation Guide | Python, Node.js, Apache, Nginx, databases |
| Commands Reference | 25+ web server commands |
| Practice Exercises | Hands-on hosting tasks |
| Troubleshooting | Common server issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 47
Title: Web Server in Termux | Complete Hosting Guide | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut exciting hai - Web Server in Termux!

Kabhi socha hai ki aapka Android phone ek full-fledged web server ban 
sakta hai? Haan, aap apne phone pe websites host kar sakte ho, 
databases run kar sakte ho, aur apne projects ko internet pe launch 
kar sakte ho - sab kuch Termux ke through!

Ye chapter mein hum cover karenge:
- Python http.server se quick hosting
- Node.js server setup
- Apache installation aur configuration
- Nginx reverse proxy
- PHP aur MySQL integration
- SSL/HTTPS configuration
- ngrok se public access

To bina time waste kiye, chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein.

---

[SECTION 1: WEB SERVER OPTIONS IN TERMUX - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Termux mein multiple web server options hain. Har ek ka apna use case hai.

Sabse pehle dekhte hain kaun kaun se servers available hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    WEB SERVER OPTIONS IN TERMUX                          │
├──────────────────┬────────────────┬──────────────────────────────────────┤
│ Server           │ Best For       │ Difficulty                           │
├──────────────────┼────────────────┼──────────────────────────────────────┤
│ Python http      │ Quick testing  │ ⭐ Easy                              │
│ Node.js http     │ API/SPA apps   │ ⭐⭐ Medium                           │
│ Apache           │ PHP/MySQL      │ ⭐⭐⭐ Advanced                        │
│ Nginx            │ Reverse proxy  │ ⭐⭐⭐ Advanced                        │
│ PHP built-in     │ PHP testing    │ ⭐⭐ Medium                           │
│ Darkhttpd        │ Static files   │ ⭐ Easy                              │
└──────────────────┴────────────────┴──────────────────────────────────────┘

Pehle simple se start karte hain - Python http.server.

Ye sabse easy hai aur Python ke saath built-in aata hai. Koi extra 
installation nahi chahiye.

Use cases:
- Quick file sharing
- Static website testing
- Development preview
- Local network access

Lekin limitations bhi hain:
- No PHP support
- No database connection
- Basic functionality only
- Single threaded

Isliye production ke liye Apache ya Nginx use karte hain.

---

[SECTION 2: PYTHON HTTP.SERVER - 4:00 to 7:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye Python http.server se start karte hain.

Sabse pehle ek folder bana lete hain apni website ke liye:

    mkdir ~/website
    cd ~/website

Ab ek simple HTML file create karte hain:

    echo '<h1>Hello from Termux!</h1>' > index.html

Ab server start karte hain:

    python -m http.server 8080

[SCREEN: Server running output]

Output mein dikhega:
    Serving HTTP on 0.0.0.0 port 8080 (http://0.0.0.0:8080/) ...

Ye server aapke current directory ko host kar raha hai!

Ab browser mein jao aur type karo:
    http://localhost:8080

Ya phone ke browser mein:
    http://127.0.0.1:8080

Aapko "Hello from Termux!" dikhega!

Ab ek important baat - ye server LOCALHOST pe hai. Matlab sirf aapke 
phone pe accessible hai.

Agar aap same network ke kisi aur device se access karna chahte ho, 
to aapko apna IP address chahiye:

    ifconfig wlan0

Ya:

    ip addr show wlan0

IP address note karo, jaise: 192.168.1.100

Ab dusre device ke browser mein:
    http://192.168.1.100:8080

Server band karne ke liye: Ctrl+C press karein

Different port use karne ke liye:

    python -m http.server 3000

Python 2 ke liye (agar installed ho):

    python2 -m SimpleHTTPServer 8080

Specific directory host karne ke liye:

    python -m http.server 8080 --directory /sdcard/Download

---

[SECTION 3: NODE.JS HTTP SERVER - 7:30 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Ab Node.js se web server banate hain.

Pehle Node.js install karein:

    pkg install nodejs -y

Node.js se aap dynamic servers bana sakte ho, APIs create kar sakte ho.

Basic server banate hain:

    nano server.js

Code likhein:

```javascript
const http = require('http');
const hostname = '0.0.0.0';
const port = 3000;

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/html');
    res.end('<h1>Hello from Node.js in Termux!</h1>');
});

server.listen(port, hostname, () => {
    console.log(`Server running at http://${hostname}:${port}/`);
});
```

Save karein: Ctrl+O, Enter, Ctrl+X

Ab server run karein:

    node server.js

Browser mein jao: http://localhost:3000

Ab thoda advanced banate hain - file server:

    nano file-server.js

```javascript
const http = require('http');
const fs = require('fs');
const path = require('path');

const port = 8080;

const server = http.createServer((req, res) => {
    let filePath = '.' + req.url;
    if (filePath === './') filePath = './index.html';
    
    const extname = String(path.extname(filePath)).toLowerCase();
    const mimeTypes = {
        '.html': 'text/html',
        '.js': 'text/javascript',
        '.css': 'text/css',
        '.json': 'application/json',
        '.png': 'image/png',
        '.jpg': 'image/jpeg',
        '.gif': 'image/gif',
    };
    
    const contentType = mimeTypes[extname] || 'application/octet-stream';
    
    fs.readFile(filePath, (error, content) => {
        if (error) {
            if (error.code === 'ENOENT') {
                res.writeHead(404);
                res.end('File not found');
            } else {
                res.writeHead(500);
                res.end('Server error');
            }
        } else {
            res.writeHead(200, { 'Content-Type': contentType });
            res.end(content, 'utf-8');
        }
    });
});

server.listen(port, '0.0.0.0', () => {
    console.log(`Server running at http://localhost:${port}/`);
});
```

Express.js use karna ho to:

    npm install express

Phir:

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
    res.send('Hello from Express!');
});

app.listen(port, '0.0.0.0', () => {
    console.log(`Express server running on port ${port}`);
});
```

---

[SECTION 4: APACHE INSTALLATION - 11:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Ab Apache install karte hain - ye professional web server hai.

    pkg install apache2 -y

Apache start karein:

    apachectl start

Check karein browser mein:
    http://localhost:8080

Agar "It works!" dikha to Apache successfully run ho raha hai!

Apache configuration file location:
    $PREFIX/etc/apache2/httpd.conf

Document root (jahan website files rakhni hain):
    $PREFIX/var/www/html/

Ab custom website banate hain:

    cd $PREFIX/var/www/html/
    rm index.html
    nano index.html

Apna HTML code likhein:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Termux Website</title>
    <style>
        body { font-family: Arial; background: #1a1a2e; color: #eee; 
               display: flex; justify-content: center; align-items: center; 
               height: 100vh; margin: 0; }
        h1 { color: #00ff88; }
    </style>
</head>
<body>
    <h1>Welcome to My Termux Server!</h1>
</body>
</html>
```

Apache restart karein:

    apachectl restart

Virtual host setup:

    nano $PREFIX/etc/apache2/httpd.conf

Neeche jao aur virtual host add karo:

```
<VirtualHost *:8080>
    ServerAdmin admin@localhost
    DocumentRoot "/data/data/com.termux/files/home/mysite"
    ServerName mysite.local
    ErrorLog "$PREFIX/var/log/apache2/mysite-error.log"
    CustomLog "$PREFIX/var/log/apache2/mysite-access.log" common
    <Directory "/data/data/com.termux/files/home/mysite">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Apache commands yaad rakhein:
- apachectl start - Server start
- apachectl stop - Server stop
- apachectl restart - Server restart
- apachectl configtest - Config test
- apachectl -v - Version check

---

[SECTION 5: NGINX INSTALLATION - 15:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Nginx ek powerful web server hai - high performance aur reverse proxy 
ke liye best hai.

Install karein:

    pkg install nginx -y

Nginx start karein:

    nginx

Check karein:
    http://localhost:8080

Nginx welcome page dikhega!

Configuration file:
    $PREFIX/etc/nginx/nginx.conf

Default document root:
    $PREFIX/usr/share/nginx/html/

Nginx configuration samajhte hain:

    nano $PREFIX/etc/nginx/nginx.conf

Basic configuration:

```nginx
worker_processes 1;
events {
    worker_connections 1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;
    sendfile      on;
    keepalive_timeout 65;

    server {
        listen       8080;
        server_name  localhost;

        location / {
            root   $PREFIX/usr/share/nginx/html;
            index  index.html index.htm;
        }

        error_page 404 /404.html;
        error_page 500 502 503 504 /50x.html;
    }
}
```

Reverse proxy setup (Node.js app ke liye):

```nginx
server {
    listen 8080;
    server_name localhost;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

Nginx commands:
- nginx - Start server
- nginx -s stop - Stop server
- nginx -s reload - Reload config
- nginx -t - Test configuration
- nginx -v - Version

---

[SECTION 6: PHP INTEGRATION - 18:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Ab PHP install karte hain Apache ke saath:

    pkg install php -y
    pkg install php-apache -y

PHP configuration Apache mein enable karein:

    nano $PREFIX/etc/apache2/httpd.conf

Ye lines add/uncomment karein:

```
LoadModule php_module $PREFIX/libexec/apache2/libphp.so
AddHandler php-script .php

<FilesMatch "\.php$">
    SetHandler application/x-httpd-php
</FilesMatch>

DirectoryIndex index.php index.html
```

PHP module load karein:

    echo "LoadModule php_module $PREFIX/libexec/apache2/libphp.so" >> $PREFIX/etc/apache2/httpd.conf

Apache restart karein:

    apachectl restart

Test PHP file banayein:

    nano $PREFIX/var/www/html/test.php

```php
<?php
phpinfo();
?>
```

Browser mein check karein:
    http://localhost:8080/test.php

PHP info page dikhegi!

Ab ek dynamic page banate hain:

    nano $PREFIX/var/www/html/info.php

```php
<?php
echo "<h1>Server Information</h1>";
echo "<p>PHP Version: " . phpversion() . "</p>";
echo "<p>Server Time: " . date('Y-m-d H:i:s') . "</p>";
echo "<p>Server Software: " . $_SERVER['SERVER_SOFTWARE'] . "</p>";
?>
```

PHP built-in server bhi use kar sakte ho:

    php -S 0.0.0.0:8080

---

[SECTION 7: MYSQL/MARIADB SETUP - 21:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Database install karte hain web application ke liye:

    pkg install mariadb -y

MariaDB initialize karein:

    mysql_install_db

MariaDB start karein:

    mysqld_safe &

Wait karein 5-10 seconds, phir connect karein:

    mysql -u root

MariaDB prompt mein:

```sql
-- Database create karein
CREATE DATABASE mywebsite;

-- User create karein
CREATE USER 'webuser'@'localhost' IDENTIFIED BY 'password123';

-- Permissions grant karein
GRANT ALL PRIVILEGES ON mywebsite.* TO 'webuser'@'localhost';

-- Apply changes
FLUSH PRIVILEGES;

-- Exit
EXIT;
```

PHP se MySQL connect karein:

    nano $PREFIX/var/www/html/dbtest.php

```php
<?php
$host = 'localhost';
$user = 'webuser';
$pass = 'password123';
$db   = 'mywebsite';

$conn = new mysqli($host, $user, $pass, $db);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

echo "<h1>Connected to MySQL successfully!</h1>";

// Create a test table
$sql = "CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(50)
)";

if ($conn->query($sql) === TRUE) {
    echo "<p>Table created successfully</p>";
}

$conn->close();
?>
```

MariaDB commands:
- mysqld_safe & - Start server
- mysql -u root - Connect as root
- mysqladmin -u root shutdown - Stop server

---

[SECTION 8: SQLITE USAGE - 24:00 to 26:30]
─────────────────────────────────────────────────────────────────────────────

SQLite lightweight database hai - perfect for mobile:

    pkg install sqlite -y

Database create karein:

    sqlite3 myapp.db

SQLite prompt mein:

```sql
-- Table create
CREATE TABLE contacts (
    id INTEGER PRIMARY KEY,
    name TEXT,
    email TEXT
);

-- Data insert
INSERT INTO contacts (name, email) VALUES 
    ('John', 'john@example.com'),
    ('Alice', 'alice@example.com');

-- Data read
SELECT * FROM contacts;

-- Exit
.quit
```

PHP se SQLite use karein:

```php
<?php
$db = new SQLite3('myapp.db');

$results = $db->query('SELECT * FROM contacts');
while ($row = $results->fetchArray()) {
    echo $row['name'] . " - " . $row['email'] . "<br>";
}
?>
```

---

[SECTION 9: NGROK FOR PUBLIC ACCESS - 26:30 to 29:30]
─────────────────────────────────────────────────────────────────────────────

Ab tak jo server banaye wo localhost pe tha. Agar public access chahiye 
to ngrok use karein.

Ngrok download karein:

    pkg install wget -y
    wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-arm64.tgz
    tar -xzf ngrok-v3-stable-linux-arm64.tgz
    mv ngrok $PREFIX/bin/

Ngrok account banayein: https://ngrok.com

Auth token add karein:

    ngrok config add-authtoken YOUR_TOKEN

Ab local server ko public banayein:

    ngrok http 8080

[SCREEN: Ngrok tunnel output]

Output mein ek public URL milega jaise:
    https://abc123.ngrok.io

Ye URL kisi bhi internet connected device se accessible hai!

---

[SECTION 10: SSL/HTTPS CONFIGURATION - 29:30 to 32:00]
─────────────────────────────────────────────────────────────────────────────

Self-signed SSL certificate generate karein:

    openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
        -keyout $PREFIX/etc/apache2/server.key \
        -out $PREFIX/etc/apache2/server.crt

Apache SSL configuration:

    nano $PREFIX/etc/apache2/httpd.conf

Add karein:

```
LoadModule ssl_module $PREFIX/libexec/apache2/mod_ssl.so

Listen 8443
<VirtualHost *:8443>
    ServerName localhost
    SSLEngine on
    SSLCertificateFile $PREFIX/etc/apache2/server.crt
    SSLCertificateKeyFile $PREFIX/etc/apache2/server.key
    DocumentRoot $PREFIX/var/www/html
</VirtualHost>
```

Restart Apache:

    apachectl restart

HTTPS access:
    https://localhost:8443

---

[SECTION 11: HOSTING PERSONAL PROJECTS - 32:00 to 35:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek complete project host karte hain:

    mkdir -p ~/projects/portfolio
    cd ~/projects/portfolio

Project structure:

```
portfolio/
├── index.html
├── about.html
├── style.css
├── script.js
└── images/
```

index.html:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Welcome to My Portfolio</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
        </nav>
    </header>
    <main>
        <p>This website is hosted on Termux!</p>
    </main>
    <script src="script.js"></script>
</body>
</html>
```

style.css:

```css
* { margin: 0; padding: 0; box-sizing: border-box; }
body { 
    font-family: 'Segoe UI', Arial, sans-serif;
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
    color: #eee;
    min-height: 100vh;
}
header { 
    background: rgba(0,0,0,0.3); 
    padding: 20px;
    text-align: center;
}
h1 { color: #00ff88; }
nav a { color: #fff; margin: 0 15px; text-decoration: none; }
nav a:hover { color: #00ff88; }
main { padding: 40px; text-align: center; }
```

Server start karein:

    python -m http.server 8080

Ya ngrok ke saath:

    ngrok http 8080

---

[SECTION 12: SUMMARY & NEXT PREVIEW - 35:00 to 37:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 47 complete! Let's summarize:

✅ Python http.server - Quick testing
✅ Node.js server - Dynamic applications
✅ Apache - Professional PHP hosting
✅ Nginx - High performance, reverse proxy
✅ PHP integration - Dynamic web pages
✅ MySQL/MariaDB - Database management
✅ SQLite - Lightweight database
✅ ngrok - Public URL tunnel
✅ SSL/HTTPS - Secure connections
✅ Project hosting - Complete workflow

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 47 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ python -m http.server 8080      │ Quick Python server                   │
│ node server.js                  │ Start Node.js server                  │
│ apachectl start                 │ Start Apache                          │
│ nginx                           │ Start Nginx                           │
│ mysql -u root                   │ Connect to MariaDB                    │
│ ngrok http 8080                 │ Create public tunnel                  │
│ php -S 0.0.0.0:8080             │ PHP built-in server                   │
│ sqlite3 myapp.db                │ Open SQLite database                  │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 48 mein hum seekhenge:
- Database in Termux detail
- PostgreSQL installation
- Redis setup
- Database administration

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 48!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Web Server Architecture in Termux

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX WEB SERVER ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Internet / External Network                    │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    ngrok Tunnel (Optional)                        │   │
│   │   Public URL → Tunnel → localhost:port                           │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Reverse Proxy (Nginx)                          │   │
│   │   Port 8080 → Route to appropriate backend                        │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│            ┌──────────────────────┼──────────────────────┐              │
│            ▼                      ▼                      ▼              │
│   ┌──────────────┐      ┌──────────────┐      ┌──────────────┐         │
│   │   Apache     │      │   Node.js    │      │   Python     │         │
│   │   :8080      │      │   :3000      │      │   :8000      │         │
│   │   (PHP/HTML) │      │   (API/App)  │      │   (Django)   │         │
│   └──────────────┘      └──────────────┘      └──────────────┘         │
│            │                      │                      │              │
│            └──────────────────────┼──────────────────────┘              │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Database Layer                                 │   │
│   │   ┌──────────┐  ┌──────────┐  ┌──────────┐                       │   │
│   │   │ MariaDB  │  │  SQLite  │  │  Redis   │                       │   │
│   │   │  :3306   │  │  (file)  │  │  :6379   │                       │   │
│   │   └──────────┘  └──────────┘  └──────────┘                       │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Server Comparison

| Feature | Python | Node.js | Apache | Nginx |
|---------|--------|---------|--------|-------|
| Static Files | ✅ | ✅ | ✅ | ✅ |
| Dynamic Content | ❌ | ✅ | ✅ (PHP) | ❌ |
| Reverse Proxy | ❌ | ❌ | ❌ | ✅ |
| SSL/TLS | ❌ | ✅ | ✅ | ✅ |
| Virtual Hosts | ❌ | ❌ | ✅ | ✅ |
| Performance | Medium | High | Medium | Very High |
| Memory Usage | Low | Medium | High | Low |
| Config Complexity | Simple | Medium | Complex | Medium |

### 3. Port Reference

| Port | Service | Description |
|------|---------|-------------|
| 80 | HTTP | Default web (requires root) |
| 443 | HTTPS | Secure web (requires root) |
| 8080 | HTTP Alt | Common alternative |
| 3000 | Node.js | Default Node.js |
| 8000 | Python | Default Python server |
| 3306 | MySQL | MariaDB default |
| 5432 | PostgreSQL | Postgres default |
| 6379 | Redis | Redis default |

---

## 🔧 INSTALLATION GUIDES

### 1. Python HTTP Server

```bash
# No installation needed - Python includes it
pkg install python -y

# Basic usage
python -m http.server 8080

# Specific directory
python -m http.server 8080 --directory /path/to/files

# Bind to specific IP
python -m http.server 8080 --bind 127.0.0.1
```

### 2. Node.js Server

```bash
# Install Node.js
pkg install nodejs -y

# Check version
node --version
npm --version

# Create project
mkdir myapp && cd myapp
npm init -y

# Install Express
npm install express

# Install common packages
npm install express cors body-parser helmet
```

### 3. Apache Installation

```bash
# Install Apache
pkg install apache2 -y

# Install PHP module
pkg install php php-apache -y

# Start Apache
apachectl start

# Configuration location
# $PREFIX/etc/apache2/httpd.conf

# Document root
# $PREFIX/var/www/html/

# Log files
# $PREFIX/var/log/apache2/
```

### 4. Nginx Installation

```bash
# Install Nginx
pkg install nginx -y

# Start Nginx
nginx

# Configuration
# $PREFIX/etc/nginx/nginx.conf

# Document root
# $PREFIX/usr/share/nginx/html/

# Stop Nginx
nginx -s stop

# Reload config
nginx -s reload
```

### 5. MariaDB Installation

```bash
# Install MariaDB
pkg install mariadb -y

# Initialize database
mysql_install_db

# Start server
mysqld_safe &

# Connect
mysql -u root

# Secure installation
mysql_secure_installation

# Stop server
mysqladmin -u root shutdown
```

### 6. SQLite Installation

```bash
# Install SQLite
pkg install sqlite -y

# Create/open database
sqlite3 myapp.db

# Install Python SQLite support
pkg install python -y  # Included by default
```

---

## 📋 COMMANDS REFERENCE

### Python HTTP Server Commands

```bash
# Start basic server on port 8080
python -m http.server 8080

# Start on default port 8000
python -m http.server

# Bind to specific interface
python -m http.server 8080 --bind 192.168.1.100

# Serve specific directory
python -m http.server 8080 --directory /sdcard/Download

# Run in background
nohup python -m http.server 8080 &

# Python 2 simple server (legacy)
python2 -m SimpleHTTPServer 8080
```

### Node.js Server Commands

```bash
# Run JavaScript file
node server.js

# Run with watch mode (if nodemon installed)
nodemon server.js

# Install global package
npm install -g nodemon

# Create package.json
npm init -y

# Install dependencies
npm install

# Install dev dependencies
npm install --save-dev nodemon

# Run npm script
npm start

# Kill node process
pkill node
```

### Apache Commands

```bash
# Start Apache
apachectl start

# Stop Apache
apachectl stop

# Restart Apache
apachectl restart

# Test configuration
apachectl configtest

# Check version
apachectl -v

# Check compiled modules
apachectl -M

# Check status
apachectl -S

# Graceful restart (no downtime)
apachectl graceful

# Full status
apachectl fullstatus
```

### Nginx Commands

```bash
# Start Nginx
nginx

# Stop Nginx
nginx -s stop

# Quit Nginx (graceful)
nginx -s quit

# Reload configuration
nginx -s reload

# Reopen log files
nginx -s reopen

# Test configuration
nginx -t

# Test configuration with verbose output
nginx -T

# Check version
nginx -v

# Show compiled modules
nginx -V
```

### PHP Commands

```bash
# Start PHP built-in server
php -S 0.0.0.0:8080

# Start with specific document root
php -S 0.0.0.0:8080 -t /path/to/web

# Start with router file
php -S 0.0.0.0:8080 router.php

# Check PHP version
php -v

# Check installed modules
php -m

# Check PHP configuration
php -i

# Run PHP file
php file.php

# Interactive shell
php -a

# Syntax check
php -l file.php
```

### MySQL/MariaDB Commands

```bash
# Start MariaDB server
mysqld_safe &

# Connect as root
mysql -u root

# Connect with password
mysql -u root -p

# Connect to specific database
mysql -u root myapp

# Connect with host
mysql -h localhost -u root -p

# Execute SQL file
mysql -u root < backup.sql

# Export database
mysqldump -u root myapp > backup.sql

# Export specific tables
mysqldump -u root myapp table1 table2 > tables.sql

# Import database
mysql -u root myapp < backup.sql

# Stop server
mysqladmin -u root shutdown

# Check server status
mysqladmin -u root status

# Create database
mysql -u root -e "CREATE DATABASE myapp;"

# Show databases
mysql -u root -e "SHOW DATABASES;"

# Process list
mysqladmin -u root processlist
```

### SQLite Commands

```bash
# Open/create database
sqlite3 myapp.db

# Open with header and column mode
sqlite3 -header -column myapp.db

# Execute SQL from command line
sqlite3 myapp.db "SELECT * FROM users;"

# Import CSV
sqlite3 myapp.db ".import data.csv users"

# Export to CSV
sqlite3 myapp.db ".output users.csv" ".mode csv" "SELECT * FROM users;"

# Dump database to SQL
sqlite3 myapp.db .dump > backup.sql

# Restore from SQL
sqlite3 new.db < backup.sql

# Database file info
sqlite3 myapp.db ".dbinfo"

# List tables
sqlite3 myapp.db ".tables"

# Schema
sqlite3 myapp.db ".schema"
```

### ngrok Commands

```bash
# Start HTTP tunnel
ngrok http 8080

# Start with specific region
ngrok http 8080 --region in

# Start HTTPS tunnel
ngrok http https://localhost:8080

# Start TCP tunnel
ngrok tcp 22

# Start with basic auth
ngrok http 8080 --auth user:pass

# Add authtoken
ngrok config add-authtoken YOUR_TOKEN

# Check tunnels
ngrok tunnels

# Kill ngrok
pkill ngrok

# Version
ngrok version
```

### SSL/Security Commands

```bash
# Generate self-signed certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout server.key -out server.crt

# Generate private key
openssl genrsa -out private.key 2048

# Generate CSR
openssl req -new -key private.key -out request.csr

# Check certificate
openssl x509 -in server.crt -text -noout

# Check key
openssl rsa -in server.key -check

# Convert PEM to DER
openssl x509 -in server.crt -outform der -out server.der

# Generate random password
openssl rand -base64 32

# Hash a password
openssl passwd -1 "mypassword"
```

### Process Management Commands

```bash
# Find process on port
lsof -i :8080

# Kill process by PID
kill PID

# Force kill
kill -9 PID

# Find and kill by name
pkill nginx

# Show all running processes
ps aux

# Show processes with tree
ps auxf

# Monitor processes
top

# Background process
nohup python -m http.server 8080 &

# List background jobs
jobs

# Bring to foreground
fg %1

# Check open ports
netstat -tlnp

# Check connections
netstat -an | grep ESTABLISHED
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic File Server

```bash
# Task: Create a file sharing server

# Step 1: Create share directory
mkdir -p ~/share/files
cd ~/share

# Step 2: Create some test files
echo "Welcome to my file server!" > files/readme.txt
echo '{"status": "ok"}' > files/status.json
echo '<h1>Hello World</h1>' > files/index.html

# Step 3: Create a simple HTML listing page
cat > index.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>My File Server</title>
    <style>
        body { font-family: Arial; max-width: 800px; margin: 50px auto; }
        h1 { color: #333; }
        a { color: #0066cc; text-decoration: none; }
        a:hover { text-decoration: underline; }
        .file-list { list-style: none; padding: 0; }
        .file-list li { padding: 10px; border-bottom: 1px solid #eee; }
    </style>
</head>
<body>
    <h1>📁 My File Server</h1>
    <ul class="file-list">
        <li><a href="files/readme.txt">📄 readme.txt</a></li>
        <li><a href="files/status.json">📋 status.json</a></li>
        <li><a href="files/index.html">🌐 index.html</a></li>
    </ul>
</body>
</html>
EOF

# Step 4: Start the server
python -m http.server 8080

# Step 5: Test in browser
# http://localhost:8080

# Press Ctrl+C to stop
```

### Exercise 2: Node.js API Server

```bash
# Task: Create a REST API server

# Step 1: Create project
mkdir -p ~/api-server
cd ~/api-server

# Step 2: Initialize npm
npm init -y

# Step 3: Install Express
npm install express cors

# Step 4: Create server file
cat > server.js << 'EOF'
const express = require('express');
const cors = require('cors');
const app = express();
const PORT = 3000;

// Middleware
app.use(cors());
app.use(express.json());

// Sample data
let users = [
    { id: 1, name: 'John', email: 'john@example.com' },
    { id: 2, name: 'Alice', email: 'alice@example.com' }
];

// Routes
app.get('/', (req, res) => {
    res.json({ message: 'Welcome to Termux API Server!' });
});

// GET all users
app.get('/api/users', (req, res) => {
    res.json(users);
});

// GET single user
app.get('/api/users/:id', (req, res) => {
    const user = users.find(u => u.id === parseInt(req.params.id));
    if (!user) return res.status(404).json({ error: 'User not found' });
    res.json(user);
});

// POST new user
app.post('/api/users', (req, res) => {
    const user = {
        id: users.length + 1,
        name: req.body.name,
        email: req.body.email
    };
    users.push(user);
    res.status(201).json(user);
});

// DELETE user
app.delete('/api/users/:id', (req, res) => {
    users = users.filter(u => u.id !== parseInt(req.params.id));
    res.json({ message: 'User deleted' });
});

// Start server
app.listen(PORT, '0.0.0.0', () => {
    console.log(`API Server running on http://localhost:${PORT}`);
});
EOF

# Step 5: Start server
node server.js

# Step 6: Test with curl (in new terminal)
curl http://localhost:3000
curl http://localhost:3000/api/users
curl -X POST -H "Content-Type: application/json" \
    -d '{"name":"Bob","email":"bob@test.com"}' \
    http://localhost:3000/api/users
```

### Exercise 3: Complete LAMP Stack

```bash
# Task: Set up Apache + PHP + MySQL

# Step 1: Install packages
pkg install apache2 php php-apache mariadb -y

# Step 2: Start MariaDB
mysqld_safe &
sleep 5

# Step 3: Setup database
mysql -u root << 'EOF'
CREATE DATABASE appdb;
CREATE USER 'appuser'@'localhost' IDENTIFIED BY 'apppass123';
GRANT ALL PRIVILEGES ON appdb.* TO 'appuser'@'localhost';
FLUSH PRIVILEGES;

USE appdb;
CREATE TABLE items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
INSERT INTO items (name) VALUES ('Item 1'), ('Item 2'), ('Item 3');
EOF

# Step 4: Create PHP application
cat > $PREFIX/var/www/html/index.php << 'EOF'
<?php
$host = 'localhost';
$db   = 'appdb';
$user = 'appuser';
$pass = 'apppass123';

try {
    $pdo = new PDO("mysql:host=$host;dbname=$db", $user, $pass);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    
    // Handle form submission
    if ($_SERVER['REQUEST_METHOD'] === 'POST' && !empty($_POST['name'])) {
        $stmt = $pdo->prepare("INSERT INTO items (name) VALUES (?)");
        $stmt->execute([$_POST['name']]);
        header("Location: " . $_SERVER['PHP_SELF']);
        exit;
    }
    
    // Fetch items
    $stmt = $pdo->query("SELECT * FROM items ORDER BY id DESC");
    $items = $stmt->fetchAll(PDO::FETCH_ASSOC);
} catch(PDOException $e) {
    die("Connection failed: " . $e->getMessage());
}
?>
<!DOCTYPE html>
<html>
<head>
    <title>Termux LAMP App</title>
    <style>
        body { font-family: Arial; max-width: 600px; margin: 50px auto; padding: 20px; }
        h1 { color: #333; }
        form { background: #f5f5f5; padding: 20px; border-radius: 8px; }
        input[type="text"] { padding: 10px; width: 70%; border: 1px solid #ddd; }
        button { padding: 10px 20px; background: #0066cc; color: white; border: none; cursor: pointer; }
        ul { list-style: none; padding: 0; }
        li { padding: 10px; background: #f9f9f9; margin: 5px 0; border-radius: 4px; }
        .success { color: green; }
    </style>
</head>
<body>
    <h1>📦 Item Manager</h1>
    <p class="success">✅ Connected to MySQL!</p>
    
    <form method="POST">
        <input type="text" name="name" placeholder="Enter item name" required>
        <button type="submit">Add Item</button>
    </form>
    
    <h2>Items List</h2>
    <ul>
        <?php foreach($items as $item): ?>
            <li><?= htmlspecialchars($item['name']) ?> 
                <small>(<?= $item['created_at'] ?>)</small>
            </li>
        <?php endforeach; ?>
    </ul>
    
    <hr>
    <p><small>Powered by Termux: Apache + PHP + MariaDB</small></p>
</body>
</html>
EOF

# Step 5: Configure Apache for PHP
# Add PHP handler to Apache config
echo "AddHandler php-script .php" >> $PREFIX/etc/apache2/httpd.conf
echo "DirectoryIndex index.php index.html" >> $PREFIX/etc/apache2/httpd.conf

# Step 6: Start Apache
apachectl start

# Step 7: Test in browser
# http://localhost:8080/index.php
```

### Exercise 4: Public Website with ngrok

```bash
# Task: Make local server publicly accessible

# Step 1: Create a simple website
mkdir -p ~/public-site
cd ~/public-site

cat > index.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>My Public Website</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .card {
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            text-align: center;
            max-width: 400px;
        }
        h1 { color: #333; margin-bottom: 15px; }
        p { color: #666; margin-bottom: 20px; }
        .badge {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 10px 20px;
            border-radius: 50px;
            display: inline-block;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <div class="card">
        <h1>🌐 Hello World!</h1>
        <p>This website is hosted on Termux and accessible worldwide!</p>
        <span class="badge">Powered by Termux + ngrok</span>
    </div>
</body>
</html>
EOF

# Step 2: Start local server
python -m http.server 8080 &

# Step 3: Start ngrok (requires ngrok setup)
ngrok http 8080

# Step 4: Share the ngrok URL with anyone!
# Example: https://abc123.ngrok-free.app

# When done, kill both processes
pkill python
pkill ngrok
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Address already in use"

```bash
# Cause: Another process using the port

# Find what's using the port
lsof -i :8080

# Kill the process
kill -9 PID

# Or use a different port
python -m http.server 8081
```

### Problem 2: Apache won't start

```bash
# Cause: Configuration error or port conflict

# Check configuration
apachectl configtest

# Check error logs
cat $PREFIX/var/log/apache2/error_log

# Kill any existing Apache processes
pkill httpd

# Try starting again
apachectl start

# Check if running
ps aux | grep httpd
```

### Problem 3: MySQL connection refused

```bash
# Cause: MariaDB not running

# Check if MariaDB is running
ps aux | grep mysql

# Start MariaDB
mysqld_safe &

# Wait for it to start
sleep 5

# Test connection
mysql -u root -e "SELECT 1;"

# If socket error, check socket location
ls -la /tmp/mysql.sock
```

### Problem 4: PHP not executing

```bash
# Cause: PHP module not loaded in Apache

# Check if PHP module is loaded
apachectl -M | grep php

# Add PHP configuration
cat >> $PREFIX/etc/apache2/httpd.conf << 'EOF'
LoadModule php_module $PREFIX/libexec/apache2/libphp.so
AddHandler php-script .php
<FilesMatch "\.php$">
    SetHandler application/x-httpd-php
</FilesMatch>
EOF

# Restart Apache
apachectl restart

# Test PHP
echo "<?php phpinfo(); ?>" > $PREFIX/var/www/html/test.php
```

### Problem 5: ngrok not connecting

```bash
# Cause: No authtoken or network issue

# Add authtoken (get from ngrok.com)
ngrok config add-authtoken YOUR_TOKEN

# Check internet
ping -c 3 google.com

# Try different region
ngrok http 8080 --region us

# Check ngrok status
ngrok tunnels
```

### Problem 6: Nginx 403 Forbidden

```bash
# Cause: Permission issue or wrong path

# Check document root permissions
ls -la $PREFIX/usr/share/nginx/html/

# Check Nginx user in config
grep user $PREFIX/etc/nginx/nginx.conf

# Add proper permissions
chmod 755 $PREFIX/usr/share/nginx/html/

# Check if index file exists
ls $PREFIX/usr/share/nginx/html/index.html

# Test config
nginx -t
```

### Problem 7: Can't access from other devices

```bash
# Cause: Firewall or binding to localhost only

# Make sure server binds to 0.0.0.0
python -m http.server 8080 --bind 0.0.0.0

# Check IP address
ifconfig wlan0 | grep inet

# Test from same device first
curl http://localhost:8080

# Check if port is open
netstat -tlnp | grep 8080

# Android might block connections - check settings
```

### Problem 8: Server crashes with large files

```bash
# Cause: Memory limits

# Use darkhttpd for large static files
pkg install darkhttpd
darkhttpd /path/to/files --port 8080

# Or use Nginx for better performance
nginx

# For Python, increase buffer
# (Not easily configurable in http.server)
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🌐 WEB SERVER                    │
│   IN TERMUX                        │
│                                    │
│   ✓ Apache ✓ Nginx                 │
│   ✓ PHP ✓ MySQL                    │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Visual Stack**
```
┌────────────────────────────────────┐
│  ┌─────────────────────────────┐   │
│  │  🌐 NGROK (Public URL)      │   │
│  └─────────────────────────────┘   │
│            ↓                        │
│  ┌─────────────────────────────┐   │
│  │  🔧 NGINX / APACHE          │   │
│  └─────────────────────────────┘   │
│            ↓                        │
│  ┌─────────────────────────────┐   │
│  │  📦 PHP / NODE.JS           │   │
│  └─────────────────────────────┘   │
│            ↓                        │
│  ┌─────────────────────────────┐   │
│  │  💾 MySQL / SQLite          │   │
│  └─────────────────────────────┘   │
│                                    │
│  Chapter 47 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Action Shot**
```
┌────────────────────────────────────┐
│  📱 TERMUX SCREENSHOT              │
│  ┌────────────────────────────┐    │
│  │ $ python -m http.server    │    │
│  │ Serving HTTP on 0.0.0.0... │    │
│  │ $ ngrok http 8080          │    │
│  │ Tunnel: https://abc.ngrok  │    │
│  └────────────────────────────┘    │
│                                    │
│  🔥 HOST WEBSITES ON ANDROID!      │
│                                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🌐 Termux Full Course - Chapter 47: Web Server in Termux | Complete Hosting Guide

🔥 In this video you'll learn:
• Python http.server se quick hosting
• Node.js API server setup
• Apache installation aur configuration
• Nginx reverse proxy setup
• PHP aur MySQL integration
• SQLite database usage
• ngrok se public access
• SSL/HTTPS configuration

⏱️ Timestamps:
0:00 - Introduction
1:00 - Web Server Options in Termux
4:00 - Python HTTP Server
7:30 - Node.js HTTP Server
11:00 - Apache Installation
15:00 - Nginx Installation
18:00 - PHP Integration
21:00 - MySQL/MariaDB Setup
24:00 - SQLite Usage
26:30 - ngrok for Public Access
29:30 - SSL/HTTPS Configuration
32:00 - Hosting Personal Projects
35:00 - Summary

📝 Commands from this video:
# Python server
python -m http.server 8080

# Apache
pkg install apache2 -y
apachectl start

# Nginx  
pkg install nginx -y
nginx

# MySQL
pkg install mariadb -y
mysqld_safe &

# ngrok
ngrok http 8080

📥 Download Links:
• ngrok: https://ngrok.com

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #WebServer #T3rmuxk1ng #Apache #Nginx #NodeJS #TermuxCourse #HindiTutorial #AndroidServer

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on systems you have permission to work with.
```

### Tags List

```
termux, termux web server, apache termux, nginx termux, 
php termux, mysql termux, nodejs termux, python http server,
termux hosting, termux website, web server android,
termux lamp stack, termux server, ngrok termux,
termux tutorial, termux course, termux hindi,
android web server, mobile hosting, t3rmuxk1ng,
termux apache, termux nginx, termux php,
termux mysql, termux sqlite, termux ssl,
host website on android, termux public server
```

### Hashtags

```
#Termux #WebServer #TermuxCourse #Apache #Nginx #NodeJS #PHP #MySQL 
#TermuxHindi #AndroidServer #TermuxTutorial #T3rmuxk1ng #MobileHosting 
#TermuxLAMP #LearnTermux #HindiTutorial #WebDevelopment
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Apache Docs | https://httpd.apache.org/docs/ |
| Nginx Docs | https://nginx.org/en/docs/ |
| Node.js Docs | https://nodejs.org/docs/ |
| MariaDB Docs | https://mariadb.com/kb/ |
| PHP Docs | https://www.php.net/docs.php |
| ngrok Docs | https://ngrok.com/docs |

### Configuration File Locations

| Server | Config File |
|--------|-------------|
| Apache | `$PREFIX/etc/apache2/httpd.conf` |
| Nginx | `$PREFIX/etc/nginx/nginx.conf` |
| PHP | `$PREFIX/etc/php.ini` |
| MySQL | `$PREFIX/etc/mysql/my.cnf` |

### Quick Reference URLs

```
Local Server URLs:
- http://localhost:8080
- http://127.0.0.1:8080

Network Access:
- http://[YOUR_IP]:8080

Check IP:
- ifconfig wlan0
- ip addr show wlan0

Test server:
- curl http://localhost:8080
- wget -qO- http://localhost:8080
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 48, verify:

- [ ] Python http.server working and accessible
- [ ] Node.js server created and tested
- [ ] Apache installed and serving pages
- [ ] Nginx installed and configured
- [ ] PHP executing in Apache
- [ ] MariaDB running and accessible
- [ ] SQLite database created and queried
- [ ] ngrok tunnel created successfully
- [ ] Understood difference between servers
- [ ] Can host a static website
- [ ] Can create a dynamic page with PHP

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 48: Database in Termux**

- PostgreSQL installation and configuration
- Redis setup for caching
- MongoDB basics
- Database administration
- Backup and restore
- Performance optimization
- Query optimization

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 💡 PRO TIPS BOXES

> 💡 **Pro Tip #1:** Use `python -m http.server 8080 --bind 127.0.0.1` for localhost-only access - prevents network exposure!

> 💡 **Pro Tip #2:** For production-like testing, use Nginx as reverse proxy to Node.js apps - better performance and SSL support

> 💡 **Pro Tip #3:** Enable gzip compression in Nginx: `gzip on; gzip_types text/plain text/css application/json;`

> 💡 **Pro Tip #4:** Use PM2 (npm install -g pm2) to keep Node.js apps running and auto-restart on crashes

> 💡 **Pro Tip #5:** Always set proper file permissions: `chmod 644` for files, `chmod 755` for directories in web root

> 💡 **Pro Tip #6:** For static sites, use `darkhttpd` - it's lighter than Python's server and shows real-time logs

> 💡 **Pro Tip #7:** Protect sensitive files with `.htaccess` in Apache or `location` blocks in Nginx

> 💡 **Pro Tip #8:** Use Let's Encrypt with certbot for free SSL certificates - even works with ngrok!

> 💡 **Pro Tip #9:** Monitor your web server with `htop` and `netstat -tlnp` to catch resource issues early

> 💡 **Pro Tip #10:** For local development, use `php -S 0.0.0.0:8080` instead of full Apache setup - much faster!

---

## 🔥 REAL WORLD USE CASES

### Production Web Server Stack

```bash
# Full LAMP stack setup in Termux

# 1. Install all components
pkg install apache2 php php-apache mariadb nginx -y

# 2. Configure Apache with PHP
cat >> $PREFIX/etc/apache2/httpd.conf << 'EOF'
LoadModule php_module $PREFIX/libexec/apache2/libphp.so
AddHandler php-script .php
AddType text/html .php

<Directory "$PREFIX/var/www/html">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
    DirectoryIndex index.php index.html
</Directory>
EOF

# 3. Start MariaDB
mysql_install_db
mysqld_safe &

# 4. Create application database
mysql -u root << 'SQL'
CREATE DATABASE webapp;
CREATE USER 'webapp'@'localhost' IDENTIFIED BY 'secure_password';
GRANT ALL PRIVILEGES ON webapp.* TO 'webapp'@'localhost';
FLUSH PRIVILEGES;
SQL

# 5. Start Apache
apachectl start

# 6. Verify
curl http://localhost:8080
```

### Development Environment Setup

```bash
# Complete Node.js development server

# 1. Install Node.js
pkg install nodejs -y

# 2. Create project structure
mkdir -p ~/dev-server/{public,routes,views}
cd ~/dev-server

# 3. Initialize project
npm init -y
npm install express morgan body-parser cors helmet

# 4. Create server file
cat > server.js << 'EOF'
const express = require('express');
const morgan = require('morgan');
const helmet = require('helmet');
const cors = require('cors');

const app = express();
const PORT = process.env.PORT || 3000;

// Middleware
app.use(helmet());
app.use(cors());
app.use(morgan('combined'));
app.use(express.json());
app.use(express.static('public'));

// Routes
app.get('/', (req, res) => {
    res.json({ status: 'ok', message: 'Termux Dev Server Running!' });
});

app.get('/api/info', (req, res) => {
    res.json({
        platform: process.platform,
        arch: process.arch,
        nodeVersion: process.version,
        uptime: process.uptime()
    });
});

// Start server
app.listen(PORT, '0.0.0.0', () => {
    console.log(`Server running on http://0.0.0.0:${PORT}`);
});
EOF

# 5. Start with PM2 for persistence
npm install -g pm2
pm2 start server.js --name dev-server
pm2 save
pm2 startup
```

### API Server with Database

```bash
# RESTful API server with SQLite

cat > api-server.js << 'EOF'
const express = require('express');
const sqlite3 = require('sqlite3').verbose();
const app = express();
const PORT = 3000;

app.use(express.json());

// Initialize database
const db = new sqlite3.Database('./api.db');
db.serialize(() => {
    db.run(`CREATE TABLE IF NOT EXISTS users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        email TEXT UNIQUE,
        created_at DATETIME DEFAULT CURRENT_TIMESTAMP
    )`);
});

// CRUD Endpoints
// Create
app.post('/users', (req, res) => {
    const { name, email } = req.body;
    db.run('INSERT INTO users (name, email) VALUES (?, ?)', [name, email], function(err) {
        if (err) return res.status(400).json({ error: err.message });
        res.status(201).json({ id: this.lastID, name, email });
    });
});

// Read all
app.get('/users', (req, res) => {
    db.all('SELECT * FROM users', [], (err, rows) => {
        if (err) return res.status(500).json({ error: err.message });
        res.json({ data: rows });
    });
});

// Read one
app.get('/users/:id', (req, res) => {
    db.get('SELECT * FROM users WHERE id = ?', [req.params.id], (err, row) => {
        if (err) return res.status(500).json({ error: err.message });
        if (!row) return res.status(404).json({ error: 'User not found' });
        res.json(row);
    });
});

// Update
app.put('/users/:id', (req, res) => {
    const { name, email } = req.body;
    db.run('UPDATE users SET name = ?, email = ? WHERE id = ?', 
        [name, email, req.params.id], function(err) {
        if (err) return res.status(400).json({ error: err.message });
        res.json({ changes: this.changes });
    });
});

// Delete
app.delete('/users/:id', (req, res) => {
    db.run('DELETE FROM users WHERE id = ?', [req.params.id], function(err) {
        if (err) return res.status(500).json({ error: err.message });
        res.json({ deleted: this.changes > 0 });
    });
});

app.listen(PORT, '0.0.0.0', () => console.log(`API running on port ${PORT}`));
EOF

# Install dependencies and run
npm install express sqlite3
node api-server.js
```

---

## ⚡ QUICK REFERENCE CARD

| Category | Command | Description |
|----------|---------|-------------|
| **Python Server** | `python -m http.server 8080` | Basic HTTP server |
| | `python -m http.server 8080 --bind 127.0.0.1` | Localhost only |
| | `python -m http.server 8080 --directory /path` | Custom directory |
| **Node.js** | `node server.js` | Run Node server |
| | `npm start` | Run via package.json |
| | `pm2 start app.js` | Run with PM2 |
| | `pm2 list` | List PM2 apps |
| | `pm2 logs app` | View PM2 logs |
| **Apache** | `apachectl start` | Start Apache |
| | `apachectl stop` | Stop Apache |
| | `apachectl restart` | Restart Apache |
| | `apachectl configtest` | Test config |
| **Nginx** | `nginx` | Start Nginx |
| | `nginx -s stop` | Stop Nginx |
| | `nginx -s reload` | Reload config |
| | `nginx -t` | Test config |
| **PHP** | `php -S 0.0.0.0:8080` | Built-in server |
| | `php -S 0.0.0.0:8080 -t public` | Custom docroot |
| **MariaDB** | `mysqld_safe &` | Start MySQL |
| | `mysql -u root` | Connect as root |
| | `mysqladmin -u root shutdown` | Stop MySQL |
| **Ngrok** | `ngrok http 8080` | HTTP tunnel |
| | `ngrok tcp 22` | TCP tunnel |
| **SSL** | `openssl req -x509 ...` | Generate cert |

---

## 🏆 BONUS: PRODUCTION TIPS

### Web Server Security Hardening

```bash
# Security hardening checklist

# 1. Hide server version
# Apache: In httpd.conf
ServerTokens Prod
ServerSignature Off

# Nginx: In nginx.conf
server_tokens off;

# 2. Security headers
# Nginx configuration
add_header X-Frame-Options "SAMEORIGIN";
add_header X-Content-Type-Options "nosniff";
add_header X-XSS-Protection "1; mode=block";
add_header Content-Security-Policy "default-src 'self'";
add_header Referrer-Policy "strict-origin-when-cross-origin";

# 3. Disable directory listing
# Apache
Options -Indexes

# Nginx
autoindex off;

# 4. Limit request size
# Nginx
client_max_body_size 10M;

# Apache (in .htaccess)
LimitRequestBody 10485760

# 5. Rate limiting
# Nginx
limit_req_zone $binary_remote_addr zone=one:10m rate=10r/s;
limit_req zone=one burst=20 nodelay;

# 6. Block common attacks
# In Nginx location block
if ($request_method !~ ^(GET|HEAD|POST)$) { return 405; }
if ($http_user_agent ~* (bot|crawl|spider)) { return 403; }

# 7. Secure PHP settings
# In php.ini
expose_php = Off
display_errors = Off
log_errors = On
```

### SSL/HTTPS Configuration

```bash
# Complete SSL setup

# 1. Generate self-signed certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout $PREFIX/etc/apache2/server.key \
    -out $PREFIX/etc/apache2/server.crt \
    -subj "/C=IN/ST=State/L=City/O=Org/CN=localhost"

# 2. Apache SSL configuration
cat >> $PREFIX/etc/apache2/httpd.conf << 'EOF'
LoadModule ssl_module $PREFIX/libexec/apache2/mod_ssl.so

Listen 8443
<VirtualHost *:8443>
    ServerName localhost
    SSLEngine on
    SSLCertificateFile $PREFIX/etc/apache2/server.crt
    SSLCertificateKeyFile $PREFIX/etc/apache2/server.key
    DocumentRoot $PREFIX/var/www/html
    
    <Directory "$PREFIX/var/www/html">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
EOF

# 3. Nginx SSL configuration
cat >> $PREFIX/etc/nginx/nginx.conf << 'EOF'
server {
    listen 8443 ssl;
    server_name localhost;
    
    ssl_certificate $PREFIX/etc/nginx/server.crt;
    ssl_certificate_key $PREFIX/etc/nginx/server.key;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
    
    location / {
        root $PREFIX/usr/share/nginx/html;
        index index.html;
    }
}
EOF

# 4. Test HTTPS
curl -k https://localhost:8443
```

### Firewall Configuration

```bash
# Firewall rules for web servers (if iptables available)

# Allow HTTP and HTTPS
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT

# Allow from specific IP only
iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j DROP

# Rate limit connections
iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/min --limit-burst 100 -j ACCEPT

# Block common attack patterns
iptables -A INPUT -p tcp --dport 80 -m string --string "SELECT" --algo bm -j DROP
iptables -A INPUT -p tcp --dport 80 -m string --string "UNION" --algo bm -j DROP

# Save rules
iptables-save > /etc/iptables/rules.v4
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **Python HTTP Server**: Quick file sharing and testing
- ✅ **Node.js Server**: Dynamic web applications and APIs
- ✅ **Apache Setup**: PHP hosting and virtual hosts
- ✅ **Nginx Configuration**: Reverse proxy and static files
- ✅ **PHP Integration**: Dynamic web pages with Apache
- ✅ **Database Setup**: MariaDB and SQLite for web apps
- ✅ **Public Access**: Using ngrok for internet exposure
- ✅ **SSL Configuration**: HTTPS setup and certificates

### Key Takeaways

1. **Choose the right server**: Python for quick tests, Nginx for production
2. **Security first**: Always use HTTPS in production
3. **Monitor resources**: Use htop/netstat to watch server health
4. **Backup configs**: Keep copies of working configurations
5. **Test thoroughly**: Always test from external devices before going live

---

## 📈 PERFORMANCE TUNING

### Apache Optimization

```apache
# Apache performance tuning in httpd.conf

# MPM Configuration
<IfModule mpm_prefork_module>
    StartServers             5
    MinSpareServers          5
    MaxSpareServers         10
    MaxRequestWorkers      150
    MaxConnectionsPerChild   0
</IfModule>

# Enable compression
LoadModule deflate_module $PREFIX/libexec/apache2/mod_deflate.so
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/plain text/xml text/css application/javascript
</IfModule>

# Enable caching
LoadModule expires_module $PREFIX/libexec/apache2/mod_expires.so
<IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType image/jpg "access plus 1 month"
    ExpiresByType image/css "access plus 1 week"
    ExpiresByType application/javascript "access plus 1 week"
</IfModule>

# Connection settings
KeepAlive On
KeepAliveTimeout 5
MaxKeepAliveRequests 100
```

### Nginx Optimization

```nginx
# nginx.conf performance tuning

worker_processes 1;  # Set to CPU cores

events {
    worker_connections 1024;
    use epoll;
    multi_accept on;
}

http {
    # Basic optimization
    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;
    
    # Compression
    gzip on;
    gzip_vary on;
    gzip_proxied any;
    gzip_comp_level 6;
    gzip_types text/plain text/css text/xml application/json application/javascript application/xml;
    
    # Caching
    open_file_cache max=1000 inactive=20s;
    open_file_cache_valid 30s;
    open_file_cache_min_uses 2;
    open_file_cache_errors on;
    
    # Buffer sizes
    client_body_buffer_size 16K;
    client_header_buffer_size 1k;
    client_max_body_size 8m;
    large_client_header_buffers 4 8k;
}
```

### Node.js Optimization

```javascript
// Node.js server optimization

const cluster = require('cluster');
const numCPUs = require('os').cpus().length;

if (cluster.isMaster) {
    // Fork workers
    for (let i = 0; i < numCPUs; i++) {
        cluster.fork();
    }
    
    cluster.on('exit', (worker) => {
        console.log(`Worker ${worker.process.pid} died`);
        cluster.fork(); // Restart worker
    });
} else {
    const express = require('express');
    const app = express();
    
    // Enable trust proxy
    app.set('trust proxy', true);
    
    // Compression middleware
    const compression = require('compression');
    app.use(compression());
    
    // Cache headers
    app.use((req, res, next) => {
        res.set('Cache-Control', 'public, max-age=300');
        next();
    });
    
    app.listen(3000);
}
```

---

## 🔄 BACKUP & RECOVERY

### Web Server Backup Script

```bash
#!/bin/bash
# web-server-backup.sh

BACKUP_DIR=~/web-backups
DATE=$(date +%Y%m%d_%H%M%S)

mkdir -p $BACKUP_DIR

# Backup web root
tar czf $BACKUP_DIR/www-$DATE.tar.gz -C $PREFIX/var/www html

# Backup Apache config
tar czf $BACKUP_DIR/apache-config-$DATE.tar.gz -C $PREFIX/etc/apache2 .

# Backup Nginx config
tar czf $BACKUP_DIR/nginx-config-$DATE.tar.gz -C $PREFIX/etc/nginx .

# Backup SSL certificates
tar czf $BACKUP_DIR/ssl-certs-$DATE.tar.gz -C $PREFIX/etc/apache2 server.crt server.key 2>/dev/null

# Backup databases
mysqldump -u root --all-databases > $BACKUP_DIR/all-databases-$DATE.sql 2>/dev/null

# Keep only last 7 backups
find $BACKUP_DIR -name "*.tar.gz" -mtime +7 -delete
find $BACKUP_DIR -name "*.sql" -mtime +7 -delete

echo "Web server backup completed: $BACKUP_DIR"
ls -la $BACKUP_DIR/
```

### Disaster Recovery Plan

```bash
# Web server disaster recovery

# 1. Stop all services
pkill nginx
apachectl stop
mysqladmin -u root shutdown

# 2. Restore web files
tar xzf www-backup.tar.gz -C $PREFIX/var/www/

# 3. Restore configurations
tar xzf apache-config-backup.tar.gz -C $PREFIX/etc/apache2/
tar xzf nginx-config-backup.tar.gz -C $PREFIX/etc/nginx/

# 4. Restore SSL certificates
cp server.crt server.key $PREFIX/etc/apache2/

# 5. Restore databases
mysqld_safe &
sleep 5
mysql -u root < all-databases-backup.sql

# 6. Fix permissions
chmod -R 755 $PREFIX/var/www/html
chmod 644 $PREFIX/var/www/html/*.html
chmod 644 $PREFIX/var/www/html/*.php

# 7. Test configuration
apachectl configtest
nginx -t

# 8. Start services
apachectl start
nginx
```

---

## 🎮 INTERACTIVE QUIZ

### Quiz: Web Server Mastery

**Question 1:** What command starts Python's HTTP server on port 8080?
- A) `python http.server 8080`
- B) `python -m http.server 8080`
- C) `python3 --http 8080`
- D) `python -s http 8080`

**Question 2:** How do you start Apache in Termux?
- A) `service apache2 start`
- B) `apache2 start`
- C) `apachectl start`
- D) `/etc/init.d/apache start`

**Question 3:** What is the default Apache document root in Termux?
- A) `/var/www/html`
- B) `$PREFIX/var/www/html`
- C) `/home/www`
- D) `~/www`

**Question 4:** Which command stops Nginx?
- A) `nginx stop`
- B) `nginx -s stop`
- C) `service nginx stop`
- D) `killall nginx`

**Question 5:** What does `-t` flag do in PHP built-in server?
- A) Test mode
- B) Specify document root
- C) Enable TLS
- D) Timeout setting

**Question 6:** How to start MariaDB server?
- A) `service mysql start`
- B) `mysqld_safe &`
- C) `mysql start`
- D) `systemctl start mariadb`

**Question 7:** What is ngrok used for?
- A) DNS management
- B) SSL certificate generation
- C) Creating public tunnels
- D) Load balancing

**Question 8:** Which Nginx command tests configuration?
- A) `nginx -c`
- B) `nginx -t`
- C) `nginx --test`
- D) `nginx configtest`

**Question 9:** What Apache module enables PHP?
- A) `mod_php`
- B) `php_module`
- C) `mod_script`
- D) `libphp`

**Question 10:** Which port is default for HTTPS?
- A) 80
- B) 443
- C) 8080
- D) 8443

**Question 11:** What PHP command shows installed modules?
- A) `php -m`
- B) `php --modules`
- C) `php -i`
- D) `php -l`

**Question 12:** How to make Python server accessible only on localhost?
- A) `python -m http.server --local`
- B) `python -m http.server --bind 127.0.0.1`
- C) `python -m http.server --only localhost`
- D) `python -m http.server -l 127.0.0.1`

### Answers

| Q | A | Q | A | Q | A | Q | A |
|---|---|---|---|---|---|---|---|
| 1 | B | 4 | B | 7 | C | 10 | B |
| 2 | C | 5 | B | 8 | B | 11 | A |
| 3 | B | 6 | B | 9 | B | 12 | B |

---

## 🎯 SERVER SETUP CHALLENGES

### Challenge 1: Static Website Hosting
```bash
# Task: Host a static HTML website

# Steps:
# 1. Create website directory
mkdir -p ~/my-website
cd ~/my-website

# 2. Create HTML files
echo '<h1>Welcome to My Website</h1>' > index.html
echo '<p>About page</p>' > about.html

# 3. Start server
python -m http.server 8080 &

# 4. Test access
curl http://localhost:8080
curl http://localhost:8080/about.html

# Verification: Both pages should be accessible
```

### Challenge 2: PHP Application Setup
```bash
# Task: Setup PHP application with Apache

# Steps:
# 1. Install PHP and Apache
pkg install php php-apache apache2 -y

# 2. Configure PHP module
echo "LoadModule php_module $PREFIX/libexec/apache2/libphp.so" >> $PREFIX/etc/apache2/httpd.conf

# 3. Create PHP file
cat > $PREFIX/var/www/html/info.php << 'EOF'
<?php
phpinfo();
?>
EOF

# 4. Start Apache
apachectl start

# 5. Test
curl http://localhost:8080/info.php

# Verification: PHP info page should display
```

### Challenge 3: Database-Backed Application
```bash
# Task: Create web app with database

# Steps:
# 1. Setup MariaDB
pkg install mariadb -y
mysql_install_db
mysqld_safe &
sleep 3

# 2. Create database and table
mysql -u root << 'SQL'
CREATE DATABASE webapp;
USE webapp;
CREATE TABLE users (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(100));
INSERT INTO users (name) VALUES ('Test User');
SQL

# 3. Create PHP page
cat > $PREFIX/var/www/html/db.php << 'EOF'
<?php
$conn = new mysqli('localhost', 'root', '', 'webapp');
$result = $conn->query('SELECT * FROM users');
while ($row = $result->fetch_assoc()) {
    echo $row['name'] . '<br>';
}
?>
EOF

# 4. Test
curl http://localhost:8080/db.php

# Verification: "Test User" should be displayed
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relevance |
|---------|-------|-----------|
| **Chapter 45** | SSH Server | Secure remote access to web server |
| **Chapter 46** | SSH Client | Tunnel to access web services |
| **Chapter 48** | Database | Backend for dynamic websites |
| **Chapter 49** | Proot Distros | Run full Linux web servers |
| **Chapter 22** | Users & Permissions | File permissions for web root |
| **Chapter 38** | Network Tools | Diagnose web server issues |
| **Chapter 44** | Termux API | Control server via API |

---

**🎉 Chapter 47 Upgraded Successfully!**

