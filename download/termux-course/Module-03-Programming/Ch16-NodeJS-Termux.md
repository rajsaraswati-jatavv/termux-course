# Chapter 16: Node.js in Termux

> **Module:** 3 - Programming  
> **Chapter:** 16 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Node.js installation, npm, Express.js |
| Commands Reference | All Node.js and npm commands |
| Practice Exercises | 15+ hands-on Node.js examples |
| Troubleshooting | Common Node.js issues in Termux |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 16
Title: Node.js in Termux | Complete JavaScript Development | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut special hai - Node.js! Agar aap web development 
seekhna chahte ho, backend development karna chahte ho, ya JavaScript 
ko server-side pe use karna chahte ho - to Node.js aapke liye must hai.

Termux mein Node.js kya special hai? Directly Android ke upar JavaScript 
code run kar sakte ho, servers bana sakte ho, APIs develop kar sakte ho, 
aur ye sab bina laptop ke - bas apne phone se!

Python ke baad Node.js sabse popular hai developers mein. Aur Termux 
mein Node.js installation bahut smooth hai.

To chaliye shuru karte hain - Node.js in Termux!

Play button dabaiye, video like karein, subscribe karein - let's go!

---

[SECTION 1: NODE.JS INTRODUCTION - 0:50 to 3:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle - Node.js kya hai?

Node.js ek JavaScript runtime hai. Traditionally JavaScript sirf browsers 
mein chalti thi - websites ke liye. Lekin Node.js ne JavaScript ko backend 
tak pahuncha diya. Ab aap JavaScript server pe bhi likh sakte ho.

Node.js key features:

✓ Event-driven architecture - Fast aur efficient
✓ Non-blocking I/O - Perfect for real-time apps
✓ Single-threaded but scalable
✓ NPM - World's largest package registry
✓ Cross-platform - Windows, Linux, Mac, Android (Termux!)

Node.js kahan use hota hai?

┌─────────────────────────────────────────────────────────────────────────┐
│                    NODE.JS USE CASES                                     │
├─────────────────────────────────────────────────────────────────────────┤
│ ✓ Web Servers - Express.js, Fastify, Koa                               │
│ ✓ REST APIs - Backend services                                          │
│ ✓ Real-time Apps - Chat apps, gaming servers                           │
│ ✓ Microservices - Modular architecture                                  │
│ ✓ CLI Tools - Command line applications                                 │
│ ✓ Web Scraping - Puppeteer, Cheerio                                     │
│ ✓ Automation Scripts - File processing, backups                        │
│ ✓ IoT - Internet of Things devices                                      │
└─────────────────────────────────────────────────────────────────────────┘

Big companies Node.js use karti hain:
- Netflix
- Uber
- PayPal
- LinkedIn
- Walmart
- NASA (!)

To clearly Node.js industry standard hai - seekhna must hai!

---

[SECTION 2: NODE.JS INSTALLATION - 3:30 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Ab installation process dekhte hain. Termux mein Node.js install karna 
bahut easy hai.

[SCREEN: Termux terminal]

Pehle packages update karein:

    pkg update && pkg upgrade -y

Ab Node.js install karein:

    pkg install nodejs -y

Wait karein, installation complete hogi. Size thoda badi hai - Node.js 
packages download honge.

[SCREEN: Installation progress]

Installation ke baad verify karein:

    node --version

Output kuch aisa aayega: v20.x.x ya v18.x.x

npm (Node Package Manager) bhi automatically install ho jata hai:

    npm --version

Output: 9.x.x ya 10.x.x

Agar dono commands version return kar rahi hain - CONGRATULATIONS! 
Node.js successfully installed hai!

[CHECK INSTALLED PACKAGES]

    pkg list-installed | grep node

Ye command show karegi ki Node.js related kya kya install hai.

---

[SECTION 3: RUNNING JAVASCRIPT IN TERMUX - 6:00 to 8:30]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye JavaScript code run karna seekhte hain Termux mein.

[METHOD 1: REPL - Interactive Shell]

Node.js REPL (Read-Eval-Print-Loop) ek interactive shell hai:

    node

Ab aap JavaScript code type kar sakte ho:

    > 2 + 2
    4
    > console.log("Hello Termux!")
    Hello Termux!
    > const name = "T3rmuxk1ng"
    undefined
    > name
    'T3rmuxk1ng'
    > .exit

REPL se bahar aane ke liye: .exit ya Ctrl+C (2 baar)

[METHOD 2: JavaScript File]

File create karein:

    nano hello.js

Code likhein:

    console.log("Hello from Node.js in Termux!");
    console.log("Node version:", process.version);
    console.log("Platform:", process.platform);

Save karein: Ctrl+O, Enter, Ctrl+X

Ab run karein:

    node hello.js

Output:
    Hello from Node.js in Termux!
    Node version: v20.x.x
    Platform: linux

[METHOD 3: Direct Execute]

    node -e "console.log('Direct execution!')"

Ye quick testing ke liye useful hai.

---

[SECTION 4: NPM PACKAGE MANAGER - 8:30 to 11:00]
─────────────────────────────────────────────────────────────────────────────

NPM - Node Package Manager. Ye Node.js ka biggest strength hai.

NPM kya karta hai?
- Packages install karta hai
- Dependencies manage karta hai
- Scripts run karta hai
- Project initialize karta hai

[PACKAGE.JSON - PROJECT INITIALIZATION]

Naya project folder banayein:

    mkdir my-node-project
    cd my-node-project

Project initialize karein:

    npm init -y

Ye package.json file create karega. Ye file aapke project ki 
configuration hai.

[SCREEN: package.json content]

    cat package.json

Output kuch aisa hoga:

    {
      "name": "my-node-project",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\""
      },
      "keywords": [],
      "author": "",
      "license": "ISC"
    }

[INSTALLING PACKAGES - LOCAL VS GLOBAL]

LOCAL INSTALLATION (Project-specific):

    npm install express

Ya shortened:

    npm i express

Ye package node_modules folder mein install hoga aur package.json 
mein dependencies mein add ho jayega.

GLOBAL INSTALLATION (System-wide):

    npm install -g nodemon

-s ya -g flag se control karte hain local ya global.

[SCREEN: Show difference]

Local packages:
    ./node_modules/express/

Global packages location:
    npm root -g

Common npm commands:

    npm install          # Install all dependencies from package.json
    npm install <pkg>    # Install specific package
    npm install -g <pkg> # Install globally
    npm uninstall <pkg>  # Remove package
    npm update           # Update packages
    npm list             # List installed packages
    npm outdated         # Check for updates
    npm audit            # Security check

---

[SECTION 5: CREATING NODE.JS SCRIPTS - 11:00 to 13:30]
─────────────────────────────────────────────────────────────────────────────

Ab practical examples dekhte hain - real Node.js scripts.

[EXAMPLE 1: File System Operations]

    nano file-demo.js

Code:

    const fs = require('fs');
    
    // Create file
    fs.writeFileSync('test.txt', 'Hello Termux!');
    console.log('File created!');
    
    // Read file
    const data = fs.readFileSync('test.txt', 'utf8');
    console.log('File content:', data);
    
    // Append to file
    fs.appendFileSync('test.txt', '\nNew line added');
    console.log('Data appended!');

Run:

    node file-demo.js

[EXAMPLE 2: HTTP Server]

    nano server.js

Code:

    const http = require('http');
    
    const server = http.createServer((req, res) => {
        res.writeHead(200, {'Content-Type': 'text/html'});
        res.end('<h1>Hello from Termux Node.js!</h1>');
    });
    
    server.listen(3000, () => {
        console.log('Server running at http://localhost:3000');
    });

Run:

    node server.js

Ab browser mein ya curl se access karein:

    curl http://localhost:3000

[EXAMPLE 3: Fetch API (Node 18+)]

    nano fetch-demo.js

Code:

    async function getData() {
        try {
            const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
            const data = await response.json();
            console.log('Fetched data:', data.title);
        } catch (error) {
            console.error('Error:', error.message);
        }
    }
    
    getData();

Run:

    node fetch-demo.js

---

[SECTION 6: EXPRESS.JS BASICS - 13:30 to 15:30]
─────────────────────────────────────────────────────────────────────────────

Express.js Node.js ka most popular web framework hai.

Installation:

    npm install express

Basic Express Server:

    nano express-server.js

Code:

    const express = require('express');
    const app = express();
    
    // Middleware
    app.use(express.json());
    
    // Routes
    app.get('/', (req, res) => {
        res.send('Hello Express!');
    });
    
    app.get('/api/info', (req, res) => {
        res.json({
            name: 'Termux Node Server',
            version: '1.0.0',
            platform: process.platform
        });
    });
    
    app.post('/api/data', (req, res) => {
        console.log('Received:', req.body);
        res.json({ status: 'success', received: req.body });
    });
    
    const PORT = 3000;
    app.listen(PORT, () => {
        console.log(`Express server running on port ${PORT}`);
    });

Run:

    node express-server.js

Test karein:

    curl http://localhost:3000
    curl http://localhost:3000/api/info
    curl -X POST http://localhost:3000/api/data -H "Content-Type: application/json" -d '{"name":"test"}'

Express ki power ye hai ki complex APIs bahut easily ban jaate hain!

---

[SECTION 7: TERMUX API WITH NODE.JS - 15:30 to 17:30]
─────────────────────────────────────────────────────────────────────────────

Best part - Node.js se Termux APIs access kar sakte ho!

Pehle Termux:API app install hona chahiye aur termux-api package:

    pkg install termux-api

Ab Node.js se call karein:

    nano termux-api-demo.js

Code:

    const { exec } = require('child_process');
    
    // Get battery info
    exec('termux-battery-status', (error, stdout, stderr) => {
        if (error) {
            console.error('Error:', error.message);
            return;
        }
        console.log('Battery Info:', stdout);
    });
    
    // Send notification
    exec('termux-notification --title "Node.js" --content "Hello from Termux!"', 
        (error, stdout, stderr) => {
            if (!error) {
                console.log('Notification sent!');
            }
        }
    );
    
    // Get location
    exec('termux-location', (error, stdout, stderr) => {
        if (!error) {
            console.log('Location:', stdout);
        }
    });
    
    // Vibrate
    exec('termux-vibrate -d 500', () => {
        console.log('Phone vibrated!');
    });

Run:

    node termux-api-demo.js

Ye examples show karte hain ki Node.js aur Termux APIs combine karke 
kitne powerful applications ban sakte hain!

---

[SECTION 8: PM2 PROCESS MANAGER - 17:30 to 19:00]
─────────────────────────────────────────────────────────────────────────────

PM2 ek production-grade process manager hai Node.js ke liye.

Install:

    npm install -g pm2

Features:
✓ Auto-restart on crash
✓ Logging
✓ Clustering
✓ Process monitoring
✓ Startup scripts

[USING PM2]

Start application:

    pm2 start server.js --name "my-app"

List processes:

    pm2 list

Monitor:

    pm2 monit

Logs:

    pm2 logs

Stop:

    pm2 stop my-app

Restart:

    pm2 restart my-app

Delete:

    pm2 delete my-app

PM2 best hai jab aapko Node.js apps continuously run karne hain - 
background mein, phone off hone pe bhi!

---

[SECTION 9: YARN ALTERNATIVE - 19:00 to 19:45]
─────────────────────────────────────────────────────────────────────────────

Yarn bhi ek package manager hai - npm ka alternative.

Install:

    npm install -g yarn

Basic Yarn commands:

    yarn init -y         # Initialize project
    yarn add express     # Add package
    yarn add -D nodemon  # Dev dependency
    yarn remove express  # Remove package
    yarn install         # Install all dependencies
    yarn upgrade         # Upgrade packages

Yarn vs NPM:

┌─────────────────────────────────────────────────────────────────────────┐
│                    YARN VS NPM COMPARISON                                │
├──────────────────┬──────────────────┬───────────────────────────────────┤
│ Feature          │ NPM              │ Yarn                              │
├──────────────────┼──────────────────┼───────────────────────────────────┤
│ Speed            │ Slower           │ Faster (parallel downloads)       │
│ Lock File        │ package-lock.json│ yarn.lock                         │
│ Workspaces       │ ✅ Yes           │ ✅ Yes (better support)           │
│ Offline Cache    │ Limited          │ Better caching                    │
│ Output           │ Verbose          │ Clean, minimal                    │
│ Stability        │ ⭐⭐⭐⭐           │ ⭐⭐⭐⭐⭐                           │
└──────────────────┴──────────────────┴───────────────────────────────────┘

Choice aapki - dono achhe hain!

---

[SECTION 10: NODE.JS VS PYTHON - 19:45 to 20:45]
─────────────────────────────────────────────────────────────────────────────

Dono languages powerful hain - comparison dekhte hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    NODE.JS VS PYTHON                                     │
├──────────────────────┬──────────────────┬───────────────────────────────┤
│ Aspect               │ Node.js          │ Python                        │
├──────────────────────┼──────────────────┼───────────────────────────────┤
│ Syntax               │ JavaScript       │ Python (simpler)              │
│ Speed                │ Faster (V8)      │ Slower                        │
│ Concurrency          │ Event-driven     │ Threading/Async               │
│ Web Development      │ ⭐⭐⭐⭐⭐           │ ⭐⭐⭐⭐                         │
│ Data Science         │ ⭐⭐⭐             │ ⭐⭐⭐⭐⭐                         │
│ Machine Learning     │ ⭐⭐⭐             │ ⭐⭐⭐⭐⭐                         │
│ Scripting            │ ⭐⭐⭐⭐            │ ⭐⭐⭐⭐⭐                         │
│ Learning Curve       │ Medium           │ Easy                          │
│ Package Manager      │ npm/yarn         │ pip                           │
│ Termux Usage         │ ⭐⭐⭐⭐⭐           │ ⭐⭐⭐⭐⭐                         │
└──────────────────────┴──────────────────┴───────────────────────────────┘

Use Node.js when:
- Web servers/APIs
- Real-time applications
- Full-stack JavaScript
- Frontend developers transitioning

Use Python when:
- Data science/ML
- Automation scripts
- Quick prototyping
- Security tools

Dono seekh lo - dono useful hain!

---

[SECTION 11: SUMMARY & NEXT PREVIEW - 20:45 to 22:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 16 complete! Let's summarize:

✅ Node.js kya hai - JavaScript runtime for server-side
✅ Installation - pkg install nodejs
✅ Running JS - REPL, files, direct execute
✅ NPM - Package manager mastery
✅ package.json - Project configuration
✅ Local vs Global packages
✅ Express.js - Web framework basics
✅ Termux APIs with Node.js
✅ PM2 - Process management
✅ Yarn - npm alternative
✅ Node.js vs Python comparison

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 16 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install nodejs           │ Install Node.js                          │
│ node --version               │ Check Node version                        │
│ npm --version                │ Check npm version                         │
│ node <file.js>               │ Run JavaScript file                       │
│ npm init -y                  │ Initialize project                        │
│ npm install <package>        │ Install package locally                   │
│ npm install -g <package>     │ Install globally                          │
│ npm list                     │ List packages                             │
│ pm2 start <file>             │ Start with PM2                            │
│ pm2 monit                    │ Monitor processes                         │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 17 mein hum seekhenge:
- Termux API File Operations
- File manipulation through APIs
- Storage access methods
- File picker integration

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 17!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Node.js Architecture in Termux

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NODE.JS TERMUX ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Your Node.js Application                      │   │
│   │   (JavaScript code - server.js, app.js, etc.)                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Node.js Runtime (V8 Engine)                   │   │
│   │   - JavaScript execution                                         │   │
│   │   - Event loop                                                   │   │
│   │   - Non-blocking I/O                                             │   │
│   │   Location: $PREFIX/bin/node                                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Built-in Modules                              │   │
│   │   fs, http, path, os, crypto, events, stream, etc.              │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    NPM Ecosystem                                 │   │
│   │   - 1M+ packages available                                       │   │
│   │   - Express, lodash, axios, etc.                                 │   │
│   │   Location: ./node_modules/ (local)                              │   │
│   │             $PREFIX/lib/node_modules (global)                    │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android Linux Kernel                          │   │
│   │   (System calls, network, file system access)                    │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Key Node.js Paths in Termux

| Path | Description |
|------|-------------|
| `$PREFIX/bin/node` | Node.js executable |
| `$PREFIX/bin/npm` | NPM executable |
| `$PREFIX/lib/node_modules` | Global packages |
| `./node_modules` | Local project packages |
| `./package.json` | Project configuration |
| `./package-lock.json` | Dependency lock file |
| `~/.npm` | NPM cache directory |

### 3. Package.json Structure

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "description": "My Node.js project",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js",
    "test": "node test.js"
  },
  "keywords": ["termux", "nodejs"],
  "author": "T3rmuxk1ng",
  "license": "MIT",
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^3.0.1"
  }
}
```

### 4. NPM Scripts Explained

```bash
# Run scripts with npm run
npm run start     # Runs: node index.js
npm run dev       # Runs: nodemon index.js
npm test          # Special: can run with just 'npm test'

# Pass arguments to scripts
npm run start -- --port 4000

# Custom scripts
npm run build
npm run lint
npm run deploy
```

---

## 🔧 INSTALLATION GUIDE

### Complete Node.js Setup

```bash
# Step 1: Update Termux
pkg update && pkg upgrade -y

# Step 2: Install Node.js (includes npm)
pkg install nodejs -y

# Step 3: Verify installation
node --version
npm --version

# Step 4: Check installation location
which node
which npm

# Step 5: Optional - Install useful global packages
npm install -g nodemon      # Auto-restart on file changes
npm install -g pm2          # Process manager
npm install -g yarn         # Alternative package manager
npm install -g typescript   # TypeScript compiler
```

### Common NPM Packages for Termux

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    RECOMMENDED NPM PACKAGES                              │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Package              │ Purpose                                         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ express              │ Web framework                                   │
│ fastify              │ Fast web framework                              │
│ axios                │ HTTP client                                     │
│ node-fetch           │ Fetch API for older Node                        │
│ cheerio              │ HTML parsing (jQuery-like)                      │
│ puppeteer            │ Headless browser (limited in Termux)            │
│ commander            │ CLI framework                                   │
│ inquirer             │ Interactive CLI prompts                         │
│ chalk                │ Terminal colors                                 │
│ ora                  │ Elegant terminal spinner                        │
│ moment/date-fns      │ Date manipulation                               │
│ lodash               │ Utility functions                               │
│ dotenv               │ Environment variables                           │
│ nodemon              │ Development auto-restart                        │
│ pm2                  │ Process manager                                 │
│ jest                 │ Testing framework                               │
│ eslint               │ Code linter                                     │
│ prettier             │ Code formatter                                  │
└──────────────────────┴──────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### Node.js Commands

```bash
# Check version
node --version
node -v

# Run JavaScript file
node script.js

# Run with inspect (debugging)
node --inspect script.js

# Evaluate expression
node -e "console.log(2+2)"

# Run REPL
node

# Run with specific module
node --experimental-modules script.mjs

# Check memory usage
node -e "console.log(process.memoryUsage())"

# Check Node.js features
node -e "console.log(process.features)"

# Get Node.js installation path
which node
```

### NPM Commands

```bash
# Initialize project
npm init
npm init -y                    # Skip questions

# Install packages
npm install                    # Install all dependencies
npm install <package>          # Install specific package
npm install <package>@version  # Install specific version
npm install -g <package>       # Install globally
npm install --save-dev <pkg>   # Install as dev dependency

# Remove packages
npm uninstall <package>
npm uninstall -g <package>

# Update packages
npm update
npm update <package>

# View packages
npm list                       # Local packages
npm list -g --depth=0          # Global packages
npm list --depth=0             # Top-level only
npm outdated                   # Check for updates

# Package information
npm view <package>             # Package details
npm view <package> versions    # All versions
npm view <package> repository  # Repo URL

# Security
npm audit                      # Check vulnerabilities
npm audit fix                  # Fix vulnerabilities

# Cache
npm cache clean --force        # Clear cache

# Run scripts
npm run <script>
npm start
npm test

# Configuration
npm config list                # Show config
npm config set <key> <value>   # Set config
npm config get <key>           # Get config
```

### Yarn Commands

```bash
# Initialize
yarn init -y

# Install
yarn                           # Install all dependencies
yarn add <package>             # Add package
yarn add -D <package>          # Add dev dependency
yarn global add <package>      # Global install

# Remove
yarn remove <package>

# Update
yarn upgrade

# Run scripts
yarn <script>
yarn start

# Info
yarn list
yarn info <package>
```

### PM2 Commands

```bash
# Start
pm2 start app.js
pm2 start app.js --name "my-app"
pm2 start app.js -i 4          # Cluster mode (4 instances)

# Manage
pm2 stop all
pm2 stop <app-name>
pm2 restart all
pm2 restart <app-name>
pm2 delete all
pm2 delete <app-name>

# Monitor
pm2 list
pm2 monit                      # Interactive monitor
pm2 logs                       # All logs
pm2 logs <app-name>            # App-specific logs
pm2 describe <app-name>        # App details
pm2 env <id>                   # Environment variables

# Save & Restore
pm2 save                       # Save process list
pm2 resurrect                  # Restore saved processes
pm2 startup                    # Generate startup script

# Reset
pm2 reset <app-name>           # Reset restart count
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Node.js Scripts

```bash
# Create project directory
mkdir node-exercises
cd node-exercises
npm init -y

# Create basic script
cat > basics.js << 'EOF'
// Node.js Basics Demo

// 1. Console output
console.log("Hello from Node.js in Termux!");

// 2. Process information
console.log("\n--- Process Info ---");
console.log("Node Version:", process.version);
console.log("Platform:", process.platform);
console.log("Architecture:", process.arch);
console.log("PID:", process.pid);
console.log("Current Directory:", process.cwd());

// 3. Environment variables
console.log("\n--- Environment ---");
console.log("HOME:", process.env.HOME);
console.log("PATH:", process.env.PATH?.split(':').slice(0, 3).join('\n       '));

// 4. Timing
console.log("\n--- Timing ---");
console.time("loop");
let sum = 0;
for (let i = 0; i < 1000000; i++) {
    sum += i;
}
console.timeEnd("loop");
console.log("Sum:", sum);

// 5. Command line arguments
console.log("\n--- Arguments ---");
console.log("Args:", process.argv);
EOF

node basics.js arg1 arg2
```

### Exercise 2: File System Operations

```bash
cat > file-ops.js << 'EOF'
const fs = require('fs');
const path = require('path');

console.log("=== File System Operations ===\n");

// Create directory
const dirPath = './test-dir';
if (!fs.existsSync(dirPath)) {
    fs.mkdirSync(dirPath);
    console.log("✓ Directory created:", dirPath);
}

// Write file
const filePath = path.join(dirPath, 'data.txt');
fs.writeFileSync(filePath, 'Hello Termux!\n');
console.log("✓ File created:", filePath);

// Append to file
fs.appendFileSync(filePath, 'Line 2 added\n');
fs.appendFileSync(filePath, 'Line 3 added\n');
console.log("✓ Data appended");

// Read file
const content = fs.readFileSync(filePath, 'utf8');
console.log("\n--- File Content ---");
console.log(content);

// File stats
const stats = fs.statSync(filePath);
console.log("--- File Stats ---");
console.log("Size:", stats.size, "bytes");
console.log("Created:", stats.birthtime);
console.log("Modified:", stats.mtime);
console.log("Is File:", stats.isFile());
console.log("Is Directory:", stats.isDirectory());

// List directory
console.log("\n--- Directory Listing ---");
const files = fs.readdirSync('.');
files.forEach(file => {
    const fstat = fs.statSync(file);
    const type = fstat.isDirectory() ? 'DIR' : 'FILE';
    console.log(`[${type}] ${file}`);
});

// Watch for changes
console.log("\n--- Watching for file changes (10 sec) ---");
const watcher = fs.watch(filePath, (eventType, filename) => {
    console.log(`Event: ${eventType} on ${filename}`);
});

setTimeout(() => {
    watcher.close();
    console.log("Watch ended");
    
    // Cleanup
    fs.unlinkSync(filePath);
    fs.rmdirSync(dirPath);
    console.log("\n✓ Cleanup done");
}, 10000);
EOF

node file-ops.js
```

### Exercise 3: HTTP Server

```bash
cat > http-server.js << 'EOF'
const http = require('http');
const url = require('url');

const PORT = 3000;

const server = http.createServer((req, res) => {
    const parsedUrl = url.parse(req.url, true);
    const pathname = parsedUrl.pathname;
    const query = parsedUrl.query;
    
    console.log(`${new Date().toISOString()} - ${req.method} ${pathname}`);
    
    // Routes
    if (pathname === '/') {
        res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(`
            <html>
            <head><title>Termux Node Server</title></head>
            <body>
                <h1>🏠 Welcome to Termux Node.js Server!</h1>
                <ul>
                    <li><a href="/api/info">/api/info</a> - Server info</li>
                    <li><a href="/api/time">/api/time</a> - Current time</li>
                    <li><a href="/api/echo?msg=hello">/api/echo?msg=hello</a> - Echo message</li>
                </ul>
            </body>
            </html>
        `);
    }
    else if (pathname === '/api/info') {
        res.writeHead(200, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify({
            node: process.version,
            platform: process.platform,
            arch: process.arch,
            uptime: process.uptime(),
            memory: process.memoryUsage()
        }, null, 2));
    }
    else if (pathname === '/api/time') {
        res.writeHead(200, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify({
            timestamp: Date.now(),
            iso: new Date().toISOString(),
            utc: new Date().toUTCString()
        }, null, 2));
    }
    else if (pathname === '/api/echo') {
        res.writeHead(200, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify({
            message: query.msg || 'No message provided',
            received: Object.keys(query).length > 0 ? query : null
        }, null, 2));
    }
    else {
        res.writeHead(404, { 'Content-Type': 'application/json' });
        res.end(JSON.stringify({ error: 'Not Found', path: pathname }));
    }
});

server.listen(PORT, () => {
    console.log(`Server running at http://localhost:${PORT}`);
    console.log('Press Ctrl+C to stop');
});
EOF

# Run server (in background for testing)
node http-server.js &
HTTP_PID=$!

# Test endpoints
sleep 2
echo "Testing server..."
curl http://localhost:3000/api/info
echo ""
curl http://localhost:3000/api/time
echo ""
curl "http://localhost:3000/api/echo?msg=HelloTermux"

# Stop server
kill $HTTP_PID 2>/dev/null
```

### Exercise 4: Express.js REST API

```bash
# Install Express
npm install express

cat > express-api.js << 'EOF'
const express = require('express');
const app = express();

// Middleware
app.use(express.json());

// In-memory database
let items = [
    { id: 1, name: 'Item 1', price: 100 },
    { id: 2, name: 'Item 2', price: 200 }
];

// Logger middleware
app.use((req, res, next) => {
    console.log(`${new Date().toISOString()} - ${req.method} ${req.url}`);
    next();
});

// Routes
app.get('/', (req, res) => {
    res.json({
        message: 'Welcome to Express API',
        endpoints: {
            'GET /items': 'Get all items',
            'GET /items/:id': 'Get item by ID',
            'POST /items': 'Create item',
            'PUT /items/:id': 'Update item',
            'DELETE /items/:id': 'Delete item'
        }
    });
});

// GET all items
app.get('/items', (req, res) => {
    res.json({ count: items.length, items });
});

// GET item by ID
app.get('/items/:id', (req, res) => {
    const item = items.find(i => i.id === parseInt(req.params.id));
    if (!item) {
        return res.status(404).json({ error: 'Item not found' });
    }
    res.json(item);
});

// POST new item
app.post('/items', (req, res) => {
    const { name, price } = req.body;
    if (!name || !price) {
        return res.status(400).json({ error: 'Name and price required' });
    }
    
    const newItem = {
        id: items.length + 1,
        name,
        price
    };
    items.push(newItem);
    res.status(201).json(newItem);
});

// PUT update item
app.put('/items/:id', (req, res) => {
    const index = items.findIndex(i => i.id === parseInt(req.params.id));
    if (index === -1) {
        return res.status(404).json({ error: 'Item not found' });
    }
    
    items[index] = { ...items[index], ...req.body };
    res.json(items[index]);
});

// DELETE item
app.delete('/items/:id', (req, res) => {
    const index = items.findIndex(i => i.id === parseInt(req.params.id));
    if (index === -1) {
        return res.status(404).json({ error: 'Item not found' });
    }
    
    const deleted = items.splice(index, 1);
    res.json({ message: 'Item deleted', item: deleted[0] });
});

// Error handler
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).json({ error: 'Internal server error' });
});

const PORT = 3000;
app.listen(PORT, () => {
    console.log(`Express API running on http://localhost:${PORT}`);
});
EOF

node express-api.js &
API_PID=$!

sleep 2
echo "Testing API..."
echo "GET all items:"
curl http://localhost:3000/items
echo -e "\n\nPOST new item:"
curl -X POST http://localhost:3000/items -H "Content-Type: application/json" -d '{"name":"New Item","price":150}'
echo -e "\n\nGET item 1:"
curl http://localhost:3000/items/1

kill $API_PID 2>/dev/null
```

### Exercise 5: Async/Await with Fetch

```bash
cat > async-demo.js << 'EOF'
// Async/Await Demo - Fetch API (Node 18+)

const API_BASE = 'https://jsonplaceholder.typicode.com';

// Fetch with async/await
async function fetchUsers() {
    console.log('Fetching users...');
    try {
        const response = await fetch(`${API_BASE}/users`);
        if (!response.ok) {
            throw new Error(`HTTP error: ${response.status}`);
        }
        const users = await response.json();
        return users;
    } catch (error) {
        console.error('Error fetching users:', error.message);
        return [];
    }
}

async function fetchPosts(userId) {
    const response = await fetch(`${API_BASE}/posts?userId=${userId}`);
    return response.json();
}

// Process data
async function main() {
    console.log('=== Async/Await Demo ===\n');
    
    // Get users
    const users = await fetchUsers();
    console.log(`Found ${users.length} users\n`);
    
    // Display first 3 users
    console.log('First 3 users:');
    users.slice(0, 3).forEach(user => {
        console.log(`  ${user.id}. ${user.name} (${user.email})`);
    });
    
    // Get posts for user 1
    console.log('\nPosts by User 1:');
    const posts = await fetchPosts(1);
    posts.slice(0, 3).forEach(post => {
        console.log(`  - ${post.title}`);
    });
    
    // Parallel requests
    console.log('\n--- Parallel Requests ---');
    const start = Date.now();
    
    const [posts1, posts2, posts3] = await Promise.all([
        fetchPosts(1),
        fetchPosts(2),
        fetchPosts(3)
    ]);
    
    const elapsed = Date.now() - start;
    console.log(`Fetched ${posts1.length + posts2.length + posts3.length} posts in ${elapsed}ms`);
    
    console.log('\n✓ Demo complete!');
}

main().catch(console.error);
EOF

node async-demo.js
```

### Exercise 6: Termux API Integration

```bash
cat > termux-integration.js << 'EOF'
const { exec, execSync } = require('child_process');
const util = require('util');
const execPromise = util.promisify(exec);

// Termux API wrapper
const TermuxAPI = {
    // Battery status
    async getBattery() {
        try {
            const { stdout } = await execPromise('termux-battery-status');
            return JSON.parse(stdout);
        } catch (e) {
            return { error: 'Battery info not available' };
        }
    },
    
    // Device info
    async getDeviceInfo() {
        try {
            const { stdout } = await execPromise('termux-telephony-deviceinfo');
            return JSON.parse(stdout);
        } catch (e) {
            return { error: 'Device info not available' };
        }
    },
    
    // Send notification
    async notify(title, content) {
        try {
            await execPromise(`termux-notification --title "${title}" --content "${content}"`);
            return true;
        } catch (e) {
            return false;
        }
    },
    
    // Vibrate
    async vibrate(duration = 500) {
        try {
            await execPromise(`termux-vibrate -d ${duration}`);
            return true;
        } catch (e) {
            return false;
        }
    },
    
    // Torch toggle
    async torch(state = true) {
        try {
            await execPromise(`termux-torch ${state ? 'on' : 'off'}`);
            return true;
        } catch (e) {
            return false;
        }
    },
    
    // Get location
    async getLocation() {
        try {
            const { stdout } = await execPromise('termux-location');
            return JSON.parse(stdout);
        } catch (e) {
            return { error: 'Location not available' };
        }
    },
    
    // Clipboard
    async getClipboard() {
        try {
            const { stdout } = await execPromise('termux-clipboard-get');
            return stdout;
        } catch (e) {
            return '';
        }
    },
    
    async setClipboard(text) {
        try {
            await execPromise(`termux-clipboard-set "${text}"`);
            return true;
        } catch (e) {
            return false;
        }
    },
    
    // Volume
    async getVolume(stream = 'music') {
        try {
            const { stdout } = await execPromise(`termux-volume ${stream}`);
            return JSON.parse(stdout);
        } catch (e) {
            return { error: 'Volume info not available' };
        }
    },
    
    // WiFi info
    async getWifiInfo() {
        try {
            const { stdout } = await execPromise('termux-wifi-connectioninfo');
            return JSON.parse(stdout);
        } catch (e) {
            return { error: 'WiFi info not available' };
        }
    }
};

// Demo
async function main() {
    console.log('=== Termux API Integration Demo ===\n');
    
    // Battery
    console.log('Battery Status:');
    const battery = await TermuxAPI.getBattery();
    console.log(`  Level: ${battery.percentage}%`);
    console.log(`  Status: ${battery.status}`);
    console.log(`  Health: ${battery.health}`);
    
    // Device info
    console.log('\nDevice Info:');
    const device = await TermuxAPI.getDeviceInfo();
    if (device.device_id) {
        console.log(`  Device ID: ${device.device_id}`);
    }
    
    // WiFi
    console.log('\nWiFi Info:');
    const wifi = await TermuxAPI.getWifiInfo();
    if (wifi.ssid) {
        console.log(`  SSID: ${wifi.ssid}`);
        console.log(`  IP: ${wifi.ip}`);
    }
    
    // Clipboard
    console.log('\nClipboard:');
    const clipContent = await TermuxAPI.getClipboard();
    console.log(`  Content: "${clipContent.substring(0, 50)}..."`);
    
    // Notification
    console.log('\nSending notification...');
    await TermuxAPI.notify('Node.js Demo', 'Hello from Termux Node.js!');
    console.log('  ✓ Notification sent');
    
    // Vibrate
    console.log('\nVibrating...');
    await TermuxAPI.vibrate(300);
    console.log('  ✓ Done');
    
    console.log('\n✓ Demo complete!');
}

main().catch(console.error);
EOF

node termux-integration.js
```

### Exercise 7: File Watcher Service

```bash
cat > file-watcher.js << 'EOF'
const fs = require('fs');
const path = require('path');

class FileWatcher {
    constructor(watchPath) {
        this.watchPath = watchPath;
        this.watchers = [];
    }
    
    start() {
        console.log(`Watching: ${this.watchPath}\n`);
        
        // Watch directory recursively
        this.watchRecursive(this.watchPath);
        
        console.log('Press Ctrl+C to stop\n');
    }
    
    watchRecursive(dir) {
        // Watch current directory
        const watcher = fs.watch(dir, (eventType, filename) => {
            const fullPath = path.join(dir, filename);
            fs.stat(fullPath, (err, stats) => {
                if (err) return;
                
                const type = stats.isDirectory() ? 'DIR' : 'FILE';
                const time = new Date().toLocaleTimeString();
                console.log(`[${time}] ${eventType.toUpperCase()}: ${type} ${filename}`);
            });
        });
        
        this.watchers.push(watcher);
        
        // Watch subdirectories
        fs.readdirSync(dir).forEach(file => {
            const fullPath = path.join(dir, file);
            if (fs.statSync(fullPath).isDirectory()) {
                this.watchRecursive(fullPath);
            }
        });
    }
    
    stop() {
        this.watchers.forEach(w => w.close());
        console.log('\nWatchers stopped');
    }
}

// Create test files
const testDir = './watch-test';
if (!fs.existsSync(testDir)) {
    fs.mkdirSync(testDir);
}

// Start watcher
const watcher = new FileWatcher(testDir);
watcher.start();

// Simulate file activity
setTimeout(() => {
    console.log('\n--- Simulating file activity ---');
    fs.writeFileSync(`${testDir}/test1.txt`, 'Hello');
    setTimeout(() => {
        fs.appendFileSync(`${testDir}/test1.txt`, ' World');
        setTimeout(() => {
            fs.unlinkSync(`${testDir}/test1.txt`);
            setTimeout(() => {
                watcher.stop();
                fs.rmdirSync(testDir);
                console.log('Cleanup done');
            }, 2000);
        }, 2000);
    }, 2000);
}, 2000);
EOF

node file-watcher.js
```

### Exercise 8: CLI Tool with Commander

```bash
# Install commander
npm install commander

cat > cli-tool.js << 'EOF'
#!/usr/bin/env node

const { Command } = require('commander');
const fs = require('fs');
const chalk = require('chalk'); // npm install chalk

const program = new Command();

program
    .name('mycli')
    .description('CLI Demo Tool for Termux')
    .version('1.0.0');

// Hello command
program.command('hello <name>')
    .description('Say hello to someone')
    .option('-e, --excited', 'Add exclamation')
    .action((name, options) => {
        const punctuation = options.excited ? '!!!' : '!';
        console.log(`\x1b[32mHello, ${name}${punctuation}\x1b[0m`);
    });

// File command
program.command('file <action> <filename>')
    .description('File operations')
    .action((action, filename) => {
        switch (action) {
            case 'create':
                fs.writeFileSync(filename, '');
                console.log(`\x1b[32m✓ Created: ${filename}\x1b[0m`);
                break;
            case 'read':
                if (fs.existsSync(filename)) {
                    console.log(fs.readFileSync(filename, 'utf8'));
                } else {
                    console.log('\x1b[31mFile not found\x1b[0m');
                }
                break;
            case 'delete':
                if (fs.existsSync(filename)) {
                    fs.unlinkSync(filename);
                    console.log(`\x1b[33m✓ Deleted: ${filename}\x1b[0m`);
                } else {
                    console.log('\x1b[31mFile not found\x1b[0m');
                }
                break;
            default:
                console.log('\x1b[31mUnknown action\x1b[0m');
        }
    });

// Info command
program.command('info')
    .description('Show system info')
    .action(() => {
        console.log('\n=== System Info ===');
        console.log(`Node: ${process.version}`);
        console.log(`Platform: ${process.platform}`);
        console.log(`Arch: ${process.arch}`);
        console.log(`CWD: ${process.cwd()}`);
        console.log(`PID: ${process.pid}`);
        console.log(`Uptime: ${Math.floor(process.uptime())}s\n`);
    });

// Math command
program.command('calc <operation> <a> <b>')
    .description('Calculator')
    .action((operation, a, b) => {
        const x = parseFloat(a);
        const y = parseFloat(b);
        let result;
        
        switch (operation) {
            case 'add': result = x + y; break;
            case 'sub': result = x - y; break;
            case 'mul': result = x * y; break;
            case 'div': result = y !== 0 ? x / y : 'Error: Division by zero'; break;
            default: result = 'Unknown operation';
        }
        
        console.log(`\x1b[36mResult: ${result}\x1b[0m`);
    });

program.parse();
EOF

chmod +x cli-tool.js

# Test CLI
node cli-tool.js --help
node cli-tool.js hello Termux --excited
node cli-tool.js info
node cli-tool.js calc add 10 5
node cli-tool.js file create test.txt
node cli-tool.js file delete test.txt
```

### Exercise 9: JSON Database

```bash
cat > json-db.js << 'EOF'
const fs = require('fs');
const path = require('path');

class JsonDatabase {
    constructor(dbPath) {
        this.dbPath = dbPath;
        this.data = this.load();
    }
    
    load() {
        if (fs.existsSync(this.dbPath)) {
            return JSON.parse(fs.readFileSync(this.dbPath, 'utf8'));
        }
        return {};
    }
    
    save() {
        fs.writeFileSync(this.dbPath, JSON.stringify(this.data, null, 2));
    }
    
    // Create/Update
    set(key, value) {
        const keys = key.split('.');
        let obj = this.data;
        
        for (let i = 0; i < keys.length - 1; i++) {
            if (!obj[keys[i]]) obj[keys[i]] = {};
            obj = obj[keys[i]];
        }
        
        obj[keys[keys.length - 1]] = value;
        this.save();
        return value;
    }
    
    // Read
    get(key) {
        const keys = key.split('.');
        let obj = this.data;
        
        for (const k of keys) {
            if (obj[k] === undefined) return null;
            obj = obj[k];
        }
        
        return obj;
    }
    
    // Delete
    delete(key) {
        const keys = key.split('.');
        let obj = this.data;
        
        for (let i = 0; i < keys.length - 1; i++) {
            if (!obj[keys[i]]) return false;
            obj = obj[keys[i]];
        }
        
        delete obj[keys[keys.length - 1]];
        this.save();
        return true;
    }
    
    // List
    list(key = '') {
        const obj = key ? this.get(key) : this.data;
        return obj ? Object.keys(obj) : [];
    }
    
    // Find
    find(key, predicate) {
        const arr = this.get(key);
        if (!Array.isArray(arr)) return null;
        return arr.find(predicate);
    }
    
    // Filter
    filter(key, predicate) {
        const arr = this.get(key);
        if (!Array.isArray(arr)) return [];
        return arr.filter(predicate);
    }
}

// Demo
const db = new JsonDatabase('./database.json');

console.log('=== JSON Database Demo ===\n');

// Set values
db.set('users', []);
db.set('users', [...db.get('users'), { id: 1, name: 'Alice', age: 25 }]);
db.set('users', [...db.get('users'), { id: 2, name: 'Bob', age: 30 }]);
db.set('users', [...db.get('users'), { id: 3, name: 'Charlie', age: 35 }]);

db.set('settings.theme', 'dark');
db.set('settings.language', 'en');
db.set('metadata.version', '1.0.0');

console.log('Users:', db.get('users'));
console.log('\nTheme:', db.get('settings.theme'));
console.log('All Settings:', db.get('settings'));

// Query
console.log('\n--- Queries ---');
const user = db.find('users', u => u.id === 2);
console.log('Find user id=2:', user);

const olderUsers = db.filter('users', u => u.age >= 30);
console.log('Users >= 30:', olderUsers);

// Delete
db.delete('users');
console.log('\nAfter deleting users:', db.get('users'));

// Show database file
console.log('\n--- Database File Content ---');
console.log(fs.readFileSync('./database.json', 'utf8'));

// Cleanup
fs.unlinkSync('./database.json');
console.log('\n✓ Demo complete, database cleaned');
EOF

node json-db.js
```

### Exercise 10: Simple Chat Server

```bash
cat > chat-server.js << 'EOF'
const net = require('net');

const clients = new Set();

const server = net.createServer((socket) => {
    console.log(`Client connected: ${socket.remoteAddress}:${socket.remotePort}`);
    
    socket.write('Welcome to Termux Chat! Enter your name: ');
    let name = '';
    let hasName = false;
    
    socket.on('data', (data) => {
        const message = data.toString().trim();
        
        if (!hasName) {
            name = message || 'Anonymous';
            hasName = true;
            socket.name = name;
            clients.add(socket);
            
            broadcast(`${name} has joined the chat!`, socket);
            socket.write(`You are now connected as ${name}\n`);
            return;
        }
        
        if (message === '/quit') {
            socket.end();
            return;
        }
        
        if (message === '/users') {
            const users = Array.from(clients).map(c => c.name).join(', ');
            socket.write(`Online users: ${users}\n`);
            return;
        }
        
        // Broadcast message
        broadcast(`${name}: ${message}`, socket);
    });
    
    socket.on('end', () => {
        clients.delete(socket);
        if (name) {
            broadcast(`${name} has left the chat`, socket);
        }
        console.log(`Client disconnected: ${name}`);
    });
    
    socket.on('error', (err) => {
        console.error('Socket error:', err.message);
        clients.delete(socket);
    });
});

function broadcast(message, sender) {
    for (const client of clients) {
        if (client !== sender) {
            client.write(message + '\n');
        }
    }
    console.log(message);
}

const PORT = 8888;
server.listen(PORT, () => {
    console.log(`Chat server running on port ${PORT}`);
    console.log('Connect with: nc localhost 8888');
    console.log('Commands: /users, /quit\n');
});
EOF

# Run server in background
node chat-server.js &
CHAT_PID=$!

# Test with netcat
sleep 1
echo "Testing chat server..."
echo -e "User1\nHello everyone!" | nc localhost 8888 &

sleep 2
kill $CHAT_PID 2>/dev/null
```

### Exercise 11: QR Code Generator

```bash
# Install qrcode package
npm install qrcode

cat > qr-gen.js << 'EOF'
const QRCode = require('qrcode');
const fs = require('fs');

async function generateQR(text, filename = 'qrcode.png') {
    try {
        // Generate QR code as file
        await QRCode.toFile(filename, text, {
            width: 300,
            margin: 2,
            color: {
                dark: '#000000',
                light: '#ffffff'
            }
        });
        console.log(`✓ QR code saved as ${filename}`);
        
        // Also generate as terminal ASCII
        console.log('\nTerminal QR Code:');
        const terminal = await QRCode.toString(text, { type: 'terminal' });
        console.log(terminal);
        
    } catch (err) {
        console.error('Error:', err.message);
    }
}

// Demo
console.log('=== QR Code Generator ===\n');

const data = process.argv[2] || 'https://youtube.com/@T3rmuxk1ng';
console.log(`Generating QR for: ${data}\n`);

generateQR(data, 't3rmuxk1ng-qr.png');

// Generate multiple QR codes
const items = [
    { text: 'https://github.com', file: 'github-qr.png' },
    { text: 'tel:+1234567890', file: 'phone-qr.png' },
    { text: 'WIFI:T:WPA;S:MyNetwork;P:MyPassword;;', file: 'wifi-qr.png' }
];

items.forEach(item => {
    generateQR(item.text, item.file);
});
EOF

node qr-gen.js "https://youtube.com/@T3rmuxk1ng"
```

### Exercise 12: Environment Variables

```bash
# Install dotenv
npm install dotenv

# Create .env file
cat > .env << 'EOF'
APP_NAME=TermuxNodeApp
APP_PORT=3000
DB_HOST=localhost
DB_USER=admin
DB_PASS=secret123
DEBUG=true
EOF

cat > env-demo.js << 'EOF'
require('dotenv').config();

console.log('=== Environment Variables Demo ===\n');

// Access env variables
console.log('App Name:', process.env.APP_NAME);
console.log('Port:', process.env.APP_PORT);
console.log('DB Host:', process.env.DB_HOST);
console.log('Debug Mode:', process.env.DEBUG === 'true');

// Check if required env vars exist
const required = ['APP_NAME', 'APP_PORT', 'DB_HOST'];
const missing = required.filter(key => !process.env[key]);

if (missing.length > 0) {
    console.error('Missing required env vars:', missing.join(', '));
    process.exit(1);
}

// Use in config
const config = {
    app: {
        name: process.env.APP_NAME,
        port: parseInt(process.env.APP_PORT)
    },
    database: {
        host: process.env.DB_HOST,
        user: process.env.DB_USER,
        password: process.env.DB_PASS
    }
};

console.log('\nConfig loaded:', JSON.stringify(config, null, 2));

// Security - don't log passwords
console.log('\nDatabase password:', process.env.DB_PASS ? '***HIDDEN***' : 'Not set');

// Override with command line
const customPort = process.argv[2] || process.env.APP_PORT;
console.log('\nUsing port:', customPort);
EOF

node env-demo.js 4000

# Cleanup
rm .env
```

### Exercise 13: Stream Processing

```bash
cat > streams-demo.js << 'EOF'
const fs = require('fs');
const { Transform, PassThrough } = require('stream');

console.log('=== Node.js Streams Demo ===\n');

// Create test file
const testData = 'Line 1\nLine 2\nLine 3\nLine 4\nLine 5\n';
fs.writeFileSync('input.txt', testData);

// 1. Readable stream
console.log('1. Reading file with streams:');
const readStream = fs.createReadStream('input.txt', { encoding: 'utf8' });

readStream.on('data', (chunk) => {
    console.log('Chunk received:', JSON.stringify(chunk));
});

readStream.on('end', () => {
    console.log('Read complete\n');
    
    // 2. Writable stream
    console.log('2. Writing with streams:');
    demoWritable();
});

function demoWritable() {
    const writeStream = fs.createWriteStream('output.txt');
    
    writeStream.write('First line\n');
    writeStream.write('Second line\n');
    writeStream.end('Final line\n');
    
    writeStream.on('finish', () => {
        console.log('Write complete');
        console.log('Output:', fs.readFileSync('output.txt', 'utf8'));
        
        // 3. Pipe
        demoPipe();
    });
}

function demoPipe() {
    console.log('3. Piping streams:');
    
    // Read -> Transform -> Write
    const upperCase = new Transform({
        transform(chunk, encoding, callback) {
            this.push(chunk.toString().toUpperCase());
            callback();
        }
    });
    
    fs.createReadStream('input.txt')
        .pipe(upperCase)
        .pipe(fs.createWriteStream('uppercase.txt'))
        .on('finish', () => {
            console.log('Uppercase:', fs.readFileSync('uppercase.txt', 'utf8'));
            
            // Cleanup
            fs.unlinkSync('input.txt');
            fs.unlinkSync('output.txt');
            fs.unlinkSync('uppercase.txt');
            
            console.log('✓ Streams demo complete');
        });
}
EOF

node streams-demo.js
```

### Exercise 14: Worker Threads

```bash
cat > worker-demo.js << 'EOF'
const { Worker, isMainThread, parentPort, workerData } = require('worker_threads');

// Main thread
if (isMainThread) {
    console.log('=== Worker Threads Demo ===\n');
    console.log('Main thread PID:', process.pid);
    
    // CPU intensive task in main thread
    function heavyComputation(n) {
        let result = 0;
        for (let i = 0; i < n; i++) {
            result += Math.sqrt(i);
        }
        return result;
    }
    
    // Run in main thread
    console.log('\n1. Running in main thread...');
    const startMain = Date.now();
    const resultMain = heavyComputation(10000000);
    const timeMain = Date.now() - startMain;
    console.log(`Result: ${resultMain.toFixed(2)}`);
    console.log(`Time: ${timeMain}ms`);
    
    // Run in worker thread
    console.log('\n2. Running in worker thread...');
    const startWorker = Date.now();
    
    const worker = new Worker(__filename, {
        workerData: { n: 10000000 }
    });
    
    worker.on('message', (result) => {
        const timeWorker = Date.now() - startWorker;
        console.log(`Result: ${result.toFixed(2)}`);
        console.log(`Time: ${timeWorker}ms`);
        console.log('\n✓ Worker thread demo complete');
    });
    
    worker.on('error', (err) => {
        console.error('Worker error:', err);
    });
    
} else {
    // Worker thread
    let result = 0;
    for (let i = 0; i < workerData.n; i++) {
        result += Math.sqrt(i);
    }
    parentPort.postMessage(result);
}
EOF

node worker-demo.js
```

### Exercise 15: Unit Testing with Jest

```bash
# Install Jest
npm install --save-dev jest

# Create math module to test
cat > math.js << 'EOF'
const math = {
    add: (a, b) => a + b,
    subtract: (a, b) => a - b,
    multiply: (a, b) => a * b,
    divide: (a, b) => {
        if (b === 0) throw new Error('Division by zero');
        return a / b;
    },
    square: (n) => n * n,
    factorial: (n) => {
        if (n < 0) return undefined;
        if (n === 0) return 1;
        return n * math.factorial(n - 1);
    },
    isPrime: (n) => {
        if (n < 2) return false;
        for (let i = 2; i <= Math.sqrt(n); i++) {
            if (n % i === 0) return false;
        }
        return true;
    }
};

module.exports = math;
EOF

# Create test file
cat > math.test.js << 'EOF'
const math = require('./math');

describe('Math Module', () => {
    
    test('adds 1 + 2 to equal 3', () => {
        expect(math.add(1, 2)).toBe(3);
    });
    
    test('subtracts 5 - 3 to equal 2', () => {
        expect(math.subtract(5, 3)).toBe(2);
    });
    
    test('multiplies 4 * 3 to equal 12', () => {
        expect(math.multiply(4, 3)).toBe(12);
    });
    
    test('divides 10 / 2 to equal 5', () => {
        expect(math.divide(10, 2)).toBe(5);
    });
    
    test('throws on division by zero', () => {
        expect(() => math.divide(10, 0)).toThrow('Division by zero');
    });
    
    test('squares 5 to equal 25', () => {
        expect(math.square(5)).toBe(25);
    });
    
    test('calculates factorial of 5', () => {
        expect(math.factorial(5)).toBe(120);
    });
    
    test('factorial of 0 is 1', () => {
        expect(math.factorial(0)).toBe(1);
    });
    
    test('7 is prime', () => {
        expect(math.isPrime(7)).toBe(true);
    });
    
    test('8 is not prime', () => {
        expect(math.isPrime(8)).toBe(false);
    });
    
});
EOF

# Update package.json
npm pkg set scripts.test="jest"

# Run tests
npm test

# Cleanup
rm math.js math.test.js
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "node: command not found"

```bash
# Cause: Node.js not installed

# Solution: Install Node.js
pkg install nodejs -y

# Verify
node --version
```

### Problem 2: "npm ERR! network" or slow installs

```bash
# Cause: Network issues or slow mirrors

# Solution 1: Check internet
ping -c 3 registry.npmjs.org

# Solution 2: Use different registry
npm config set registry https://registry.npmmirror.com

# Solution 3: Clear cache
npm cache clean --force

# Solution 4: Use yarn instead
npm install -g yarn
yarn install
```

### Problem 3: "EACCES permission denied"

```bash
# Cause: Permission issues with global packages

# Solution 1: Fix npm permissions
mkdir -p ~/.npm-global
npm config set prefix '~/.npm-global'

# Add to PATH (add to .bashrc)
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# Solution 2: Use pkg for global tools in Termux
# Instead of: npm install -g nodemon
# Use: pkg install nodejs (includes npm working properly)
```

### Problem 4: "Cannot find module"

```bash
# Cause: Module not installed or wrong path

# Solution 1: Install missing module
npm install <module-name>

# Solution 2: Check if in correct directory
ls node_modules/

# Solution 3: Reinstall dependencies
rm -rf node_modules package-lock.json
npm install

# Solution 4: Check package.json
cat package.json | grep <module-name>
```

### Problem 5: "SyntaxError: Cannot use import statement"

```bash
# Cause: Using ES modules without proper configuration

# Solution 1: Use CommonJS (require)
# Change: import express from 'express'
# To: const express = require('express')

# Solution 2: Add type: module to package.json
npm pkg set type=module

# Solution 3: Use .mjs extension
mv script.js script.mjs
node script.mjs

# Solution 4: Use dynamic import
const module = await import('./module.js');
```

### Problem 6: PM2 not starting on boot

```bash
# Cause: PM2 startup not configured

# Solution: Generate startup script
pm2 startup

# This will output a command to run
# Example:
# env PATH=$PATH:/data/data/com.termux/files/usr/bin pm2 startup termux

# Save current processes
pm2 save

# Note: In Termux, startup scripts may need additional setup
# Consider using Termux:Boot for auto-start
```

### Problem 7: Memory issues with large projects

```bash
# Cause: Node.js default memory limit

# Solution 1: Increase memory limit
node --max-old-space-size=4096 script.js

# Solution 2: Check memory usage
node -e "console.log(process.memoryUsage())"

# Solution 3: Use streaming for large files
const stream = fs.createReadStream('large-file.txt');
stream.on('data', chunk => process(chunk));

# Solution 4: Free memory
node -e "global.gc && console.log('GC forced')"
# Note: Run with --expose-gc flag
```

### Problem 8: Port already in use

```bash
# Cause: Another process using the port

# Solution 1: Find and kill process
lsof -i :3000
kill -9 <PID>

# Solution 2: Use different port
PORT=3001 node server.js

# Solution 3: Kill all node processes
pkill -f node

# Solution 4: Check with netstat
netstat -tulpn | grep 3000
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Code Focus**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🟢 NODE.JS IN TERMUX             │
│   ─────────────────────            │
│   > node server.js                 │
│   Server running on port 3000      │
│                                    │
│   Complete JavaScript Guide!       │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Feature Highlights**
```
┌────────────────────────────────────┐
│  NODE.JS                           │
│  ──────────                        │
│  ✓ Express.js                      │
│  ✓ npm Packages                    │
│  ✓ APIs & Servers                  │
│  ✓ PM2 Manager                     │
│                                    │
│  Chapter 16 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Comparison Style**
```
┌────────────────────────────────────┐
│  Node.js 🆚 Python                 │
│  ─────────────────                 │
│  Web Dev:  Node ⭐⭐⭐⭐⭐            │
│  ML/AI:    Python ⭐⭐⭐⭐⭐          │
│  Speed:    Node ⭐⭐⭐⭐⭐            │
│                                    │
│  Termux mein kaun best hai?        │
│  👉 WATCH NOW!                     │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🟢 Node.js in Termux | Complete JavaScript Development Guide | Chapter 16

🔥 Is video mein seekhoge:
• Node.js installation in Termux
• npm package manager complete guide
• package.json file samajhna
• Local vs Global packages
• Express.js web framework basics
• Termux APIs with Node.js
• PM2 process manager
• Yarn vs npm comparison
• 15+ practical examples!

⏱️ Timestamps:
0:00 - Introduction
0:50 - Node.js Introduction
3:30 - Installation
6:00 - Running JavaScript
8:30 - NPM Package Manager
11:00 - Creating Node.js Scripts
13:30 - Express.js Basics
15:30 - Termux API Integration
17:30 - PM2 Process Manager
19:00 - Yarn Alternative
19:45 - Node.js vs Python
20:45 - Summary

📥 Commands from video:
pkg install nodejs
node --version
npm init -y
npm install express
node server.js

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Nodejs #Termux #JavaScript #TermuxNodejs #WebDevelopment #Expressjs #T3rmuxk1ng #TermuxCourse #HindiTutorial

---
⚠️ Disclaimer: This video is for educational purposes only. Use tools responsibly.
```

### Tags List

```
nodejs, node js, node.js termux, javascript termux, npm termux,
express js termux, node js installation, npm package manager,
package.json, termux node js tutorial, javascript in termux,
node js hindi, express js tutorial, pm2 process manager,
yarn vs npm, node js server, termux programming, learn node js,
node js for beginners, termux web development, node js api,
javascript server, termux course, t3rmuxk1ng, node js basics
```

### Hashtags

```
#Nodejs #Termux #JavaScript #WebDevelopment #Expressjs 
#NodejsTutorial #TermuxCourse #LearnNodejs #NodejsHindi 
#JavaScriptDevelopment #NPM #T3rmuxk1ng #ProgrammingInTermux
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| Node.js Official | https://nodejs.org |
| NPM Registry | https://www.npmjs.com |
| Node.js Docs | https://nodejs.org/docs |
| Express.js | https://expressjs.com |
| MDN JavaScript | https://developer.mozilla.org/en-US/docs/Web/JavaScript |

### Termux-Specific

| Resource | Description |
|----------|-------------|
| Termux Wiki - Node.js | Node.js specific information for Termux |
| Termux Packages | Node.js package info in Termux repo |
| Termux:API | Required for API integration |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Node.js Best Practices | github.com/goldbergyoni/nodebestpractices |
| JavaScript Info | javascript.info |
| Node.js Design Patterns | Book by Mario Casciaro |
| You Don't Know JS | Book series by Kyle Simpson |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 17, verify:

- [ ] Node.js installed: `pkg install nodejs`
- [ ] Node version checked: `node --version`
- [ ] npm working: `npm --version`
- [ ] Created and run JavaScript file
- [ ] Used npm to install packages
- [ ] Understand package.json structure
- [ ] Built simple HTTP server
- [ ] Tried Express.js basics
- [ ] Know difference between local and global packages
- [ ] Familiar with PM2 for process management

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 17: Termux API - File Operations**

- File manipulation through Termux APIs
- Storage access methods
- File picker integration
- Media file handling
- Document access framework

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
