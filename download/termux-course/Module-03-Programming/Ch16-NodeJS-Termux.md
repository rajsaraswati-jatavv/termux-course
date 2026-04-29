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

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always use `npm init -y` to quickly create package.json, then edit it manually.

> 💡 **Pro Tip #2:** Use `npm install --save-dev` for development tools like nodemon, eslint - they won't be bundled in production.

> 💡 **Pro Tip #3:** Use `npm ci` instead of `npm install` in CI/CD pipelines - it's faster and follows lockfile exactly.

> 💡 **Pro Tip #4:** Use `npx` to run packages without installing them globally: `npx create-react-app myapp`.

> 💡 **Pro Tip #5:** Use `package-lock.json` in version control - it ensures consistent installs across machines.

> 💡 **Pro Tip #6:** Use `npm outdated` to check for package updates and `npm audit` for security vulnerabilities.

> 💡 **Pro Tip #7:** Always use `process.env.PORT || 3000` for port configuration in production.

> 💡 **Pro Tip #8:** Use `dotenv` package for environment variables instead of hardcoding secrets.

> 💡 **Pro Tip #9:** In Termux, use PM2 with `--no-daemon` mode if you encounter issues with the daemon.

> 💡 **Pro Tip #10:** Use `node --inspect` for debugging Node.js applications with Chrome DevTools.

---

## 🔥 REAL WORLD APPLICATIONS

### Where Node.js Skills Apply in Real Life

**1. Backend API Development**
- Building RESTful APIs for mobile apps
- Creating microservices architectures
- Real-time applications with WebSockets

**2. CLI Tools Development**
- Building command-line tools
- Automation scripts
- Code generators

**3. Server-Side Rendering**
- Next.js applications
- Server-side React/Vue rendering
- Static site generation

**4. IoT and Hardware Projects**
- Controlling devices via HTTP
- Data collection APIs
- Gateway services

**5. Mobile Development Support**
- Backend for Android apps
- Push notification servers
- File upload services

---

## ⚡ QUICK REFERENCE CARD

### Node.js Commands Quick Reference

| Task | Command |
|------|---------|
| Install Node.js | `pkg install nodejs` |
| Check version | `node --version` |
| Check npm | `npm --version` |
| Run script | `node script.js` |
| Run REPL | `node` |
| Run one-liner | `node -e "code"` |
| Init project | `npm init -y` |
| Install package | `npm install <pkg>` |
| Install dev dep | `npm install -D <pkg>` |
| Install global | `npm install -g <pkg>` |
| Uninstall | `npm uninstall <pkg>` |
| List packages | `npm list` |
| Update packages | `npm update` |
| Run script | `npm run <script>` |
| Start (default) | `npm start` |
| Test (default) | `npm test` |
| Audit security | `npm audit` |
| Fix audit | `npm audit fix` |
| Clear cache | `npm cache clean --force` |
| PM2 start | `pm2 start app.js` |
| PM2 list | `pm2 list` |
| PM2 logs | `pm2 logs` |
| PM2 restart | `pm2 restart all` |
| PM2 stop | `pm2 stop all` |

---

## 🏆 BONUS: ADVANCED TIPS

### Express.js Project Template

```javascript
// Complete Express.js server template
const express = require('express');
const app = express();

// Middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// CORS middleware
app.use((req, res, next) => {
    res.header('Access-Control-Allow-Origin', '*');
    res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE');
    res.header('Access-Control-Allow-Headers', 'Content-Type, Authorization');
    next();
});

// Request logging
app.use((req, res, next) => {
    console.log(`${new Date().toISOString()} ${req.method} ${req.path}`);
    next();
});

// Routes
app.get('/', (req, res) => {
    res.json({ message: 'API is running', timestamp: new Date() });
});

app.get('/api/health', (req, res) => {
    res.json({ status: 'healthy', uptime: process.uptime() });
});

// 404 handler
app.use((req, res) => {
    res.status(404).json({ error: 'Not found' });
});

// Error handler
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).json({ error: 'Internal server error' });
});

// Start server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});
```

### npm Scripts Collection

```json
{
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js",
    "test": "jest",
    "test:watch": "jest --watch",
    "lint": "eslint .",
    "lint:fix": "eslint . --fix",
    "format": "prettier --write .",
    "build": "node build.js",
    "clean": "rm -rf node_modules && npm install",
    "prod": "NODE_ENV=production node index.js",
    "debug": "node --inspect index.js",
    "pm2:start": "pm2 start index.js --name myapp",
    "pm2:stop": "pm2 stop myapp",
    "pm2:logs": "pm2 logs myapp"
  }
}
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ Node.js installation in Termux
- ✅ JavaScript runtime fundamentals
- ✅ npm package manager mastery
- ✅ package.json configuration
- ✅ Local vs global package management
- ✅ Creating and running Node.js scripts
- ✅ Express.js web framework basics
- ✅ Termux API integration with Node.js
- ✅ PM2 process management
- ✅ Yarn package manager alternative

### Key Takeaways

1. **Node.js = JavaScript on Server** - Same language for frontend and backend
2. **npm is essential** - Largest package ecosystem in the world
3. **Use package.json** - Always manage dependencies properly
4. **Express.js simplifies web development** - Minimal code for powerful APIs
5. **PM2 for production** - Keep your apps running continuously

---

## 🎯 INTERVIEW QUESTIONS

### Node.js Interview Questions

**Q1: What is the difference between Node.js and browser JavaScript?**

```javascript
// Answer:
// Browser JS:
// - DOM manipulation available
// - Window object exists
// - No file system access
// - Limited to browser APIs

// Node.js:
// - No DOM (document, window)
// - Global object is 'global'
// - File system access (fs module)
// - Server-side APIs (http, net, crypto)
// - CommonJS modules by default

// Key differences:
// 1. Environment: Browser vs Server
// 2. APIs: DOM vs FS/HTTP
// 3. Modules: ES6 imports vs require()
// 4. Concurrency: Event loop same, but different I/O
```

**Q2: Explain the Node.js event loop.**

```javascript
// Answer: The event loop is Node.js's mechanism for handling async operations

// Phases:
// 1. Timers - setTimeout, setInterval
// 2. Pending callbacks - I/O callbacks deferred
// 3. Idle, prepare - Internal
// 4. Poll - Retrieve new I/O events
// 5. Check - setImmediate callbacks
// 6. Close callbacks - socket.on('close')

// Example:
console.log('1'); // Synchronous
setTimeout(() => console.log('2'), 0); // Timer phase
Promise.resolve().then(() => console.log('3')); // Microtask
console.log('4'); // Synchronous

// Output: 1, 4, 3, 2
// Microtasks (Promises) run before timer phase
```

**Q3: What are streams in Node.js?**

```javascript
// Answer: Streams are objects for handling streaming data

// Types:
// 1. Readable - For reading (fs.createReadStream)
// 2. Writable - For writing (fs.createWriteStream)
// 3. Duplex - Both readable and writable
// 4. Transform - Modify data as it passes

// Example:
const fs = require('fs');
const zlib = require('zlib');

// Stream-based file compression
fs.createReadStream('input.txt')
  .pipe(zlib.createGzip())
  .pipe(fs.createWriteStream('input.txt.gz'));

// Benefits:
// - Memory efficient (don't load entire file)
// - Process data piece by piece
// - Pipe for chaining operations
```

**Q4: How do you handle errors in Node.js?**

```javascript
// Answer: Multiple approaches depending on context

// 1. Try-catch for synchronous code
try {
    const data = fs.readFileSync('file.txt');
} catch (err) {
    console.error(err);
}

// 2. Error-first callbacks (traditional)
fs.readFile('file.txt', (err, data) => {
    if (err) {
        console.error(err);
        return;
    }
    console.log(data);
});

// 3. Promise-based (modern)
fs.promises.readFile('file.txt')
    .then(data => console.log(data))
    .catch(err => console.error(err));

// 4. Async/await
try {
    const data = await fs.promises.readFile('file.txt');
} catch (err) {
    console.error(err);
}

// 5. Global error handlers
process.on('uncaughtException', (err) => {
    console.error('Uncaught:', err);
});

process.on('unhandledRejection', (reason) => {
    console.error('Unhandled rejection:', reason);
});
```

**Q5: What is middleware in Express.js?**

```javascript
// Answer: Middleware functions have access to req, res, and next

// Structure:
function middleware(req, res, next) {
    // Do something
    next(); // Pass to next middleware
}

// Types:
// 1. Application-level
app.use((req, res, next) => {
    console.log('Request received');
    next();
});

// 2. Router-level
router.use(authMiddleware);

// 3. Error-handling
app.use((err, req, res, next) => {
    res.status(500).json({ error: err.message });
});

// 4. Built-in
app.use(express.json());

// 5. Third-party
const cors = require('cors');
app.use(cors());
```

---

## 🚀 BEST PRACTICES

### Code Style Guidelines

```javascript
// Use const/let instead of var
const PORT = 3000;
let count = 0;

// Use async/await over callbacks
// Bad:
fs.readFile('file.txt', (err, data) => { });

// Good:
const data = await fs.promises.readFile('file.txt');

// Use meaningful variable names
// Bad:
const d = new Date();

// Good:
const currentDate = new Date();

// Handle all errors
// Bad:
app.get('/users', async (req, res) => {
    const users = await User.find();
    res.json(users);
});

// Good:
app.get('/users', async (req, res) => {
    try {
        const users = await User.find();
        res.json(users);
    } catch (error) {
        res.status(500).json({ error: error.message });
    }
});
```

### Performance Tips

```javascript
// 1. Use async operations
// Bad (blocks event loop)
const data = fs.readFileSync('file.txt');

// Good (non-blocking)
const data = await fs.promises.readFile('file.txt');

// 2. Use streaming for large data
// Instead of loading entire file:
fs.createReadStream('large.txt')
    .pipe(response);

// 3. Use clustering for CPU tasks
const cluster = require('cluster');
if (cluster.isMaster) {
    for (let i = 0; i < require('os').cpus().length; i++) {
        cluster.fork();
    }
}

// 4. Cache frequently used data
const cache = new Map();
function getCached(key, fetchFn) {
    if (cache.has(key)) return cache.get(key);
    const value = fetchFn();
    cache.set(key, value);
    return value;
}
```

### Common Mistakes to Avoid

```javascript
// ❌ Mistake: Not handling promise rejections
fetch(url).then(res => res.json());

// ✅ Fix: Always handle errors
fetch(url)
    .then(res => res.json())
    .catch(err => console.error(err));

// ❌ Mistake: Blocking the event loop
for (let i = 0; i < 1e10; i++) { }

// ✅ Fix: Use setImmediate for heavy tasks
function processChunk(array, index = 0) {
    const chunk = array.slice(index, index + 1000);
    // Process chunk
    if (index + 1000 < array.length) {
        setImmediate(() => processChunk(array, index + 1000));
    }
}

// ❌ Mistake: Not using environment variables
const dbPassword = "hardcoded_password";

// ✅ Fix: Use dotenv
require('dotenv').config();
const dbPassword = process.env.DB_PASSWORD;
```

---

## 📊 CODE COMPARISON

### Before vs After: Node.js Server

```javascript
// ❌ BEFORE: Basic, no structure
const http = require('http');
http.createServer((req, res) => {
    res.writeHead(200);
    res.end('Hello');
}).listen(3000);

// ✅ AFTER: Production-ready Express server
const express = require('express');
const helmet = require('helmet');
const morgan = require('morgan');
const app = express();

// Security middleware
app.use(helmet());
app.use(morgan('combined'));
app.use(express.json());

// Routes with proper error handling
app.get('/api/health', async (req, res, next) => {
    try {
        res.json({ status: 'ok', uptime: process.uptime() });
    } catch (error) {
        next(error);
    }
});

// Error handler
app.use((err, req, res, next) => {
    console.error(err);
    res.status(500).json({ error: 'Internal error' });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server: ${PORT}`));
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relevance |
|---------|-------|-----------|
| Chapter 11 | Python Installation | Compare runtimes |
| Chapter 12 | Python Basics | Language comparison |
| Chapter 13 | Bash Scripting | Node + Shell |
| Chapter 15 | Git Version Control | Version Node projects |
| Chapter 25 | API Development | Express.js deep dive |
| Chapter 30 | Web Scraping | Node.js tools |
| Chapter 35 | Full Stack | Node.js backend |

---

## 🎮 INTERACTIVE QUIZ

**1. What command installs Node.js in Termux?**
- A) `apt install nodejs`
- B) `pkg install nodejs`
- C) `pip install nodejs`
- D) `npm install nodejs`

<details>
<summary>Answer</summary>
**B) `pkg install nodejs`** - Termux uses pkg package manager.
</details>

**2. Which file manages Node.js project dependencies?**
- A) `config.js`
- B) `package.json`
- C) `dependencies.json`
- D) `node.json`

<details>
<summary>Answer</summary>
**B) `package.json`** - Contains project metadata and dependencies.
</details>

**3. What does `npm install -D` do?**
- A) Installs dependencies
- B) Installs dev dependencies
- C) Deletes packages
- D) Debugs installation

<details>
<summary>Answer</summary>
**B) Installs dev dependencies** - Adds to devDependencies in package.json.
</details>

---

## 🔧 DEBUG THIS EXERCISES

### Debug This #1: Module Not Found

```javascript
// Problem: Cannot find module 'express'
const express = require('express');
const app = express();
```

<details>
<summary>Solution</summary>

```javascript
// Solution: Install the missing package
// Run in terminal:
// npm install express

// Then run your script
// node app.js

// If still failing, check node_modules:
// ls node_modules/express
```
</details>

### Debug This #2: Port Already in Use

```javascript
// Problem: EADDRINUSE error
app.listen(3000);
// Error: listen EADDRINUSE: address already in use :::3000
```

<details>
<summary>Solution</summary>

```bash
# Solution 1: Kill process using port
lsof -i :3000
kill -9 <PID>

# Solution 2: Use different port
PORT=3001 node app.js

# Solution 3: In code, handle gracefully
app.listen(PORT, () => {
    console.log(`Server running on ${PORT}`);
}).on('error', (err) => {
    if (err.code === 'EADDRINUSE') {
        console.log('Port busy, trying next...');
        app.listen(PORT + 1);
    }
});
```
</details>

---

## 💻 CODING CHALLENGES

### Challenge 1: REST API Server

Create a complete REST API for a todo list.

```javascript
// Challenge: Create Express API with:
// 1. GET /todos - List all todos
// 2. POST /todos - Create todo
// 3. PUT /todos/:id - Update todo
// 4. DELETE /todos/:id - Delete todo
```

<details>
<summary>Solution</summary>

```javascript
const express = require('express');
const app = express();
app.use(express.json());

let todos = [];
let idCounter = 1;

// GET all todos
app.get('/todos', (req, res) => {
    res.json(todos);
});

// POST new todo
app.post('/todos', (req, res) => {
    const { title } = req.body;
    if (!title) return res.status(400).json({ error: 'Title required' });
    
    const todo = { id: idCounter++, title, completed: false };
    todos.push(todo);
    res.status(201).json(todo);
});

// PUT update todo
app.put('/todos/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const todo = todos.find(t => t.id === id);
    if (!todo) return res.status(404).json({ error: 'Not found' });
    
    todo.title = req.body.title || todo.title;
    todo.completed = req.body.completed ?? todo.completed;
    res.json(todo);
});

// DELETE todo
app.delete('/todos/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const index = todos.findIndex(t => t.id === id);
    if (index === -1) return res.status(404).json({ error: 'Not found' });
    
    todos.splice(index, 1);
    res.status(204).send();
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`API: http://localhost:${PORT}`));
```
</details>

---

*Created by T3rmuxk1ng | Termux Full Course*

---

## 🎮 INTERACTIVE QUIZ

### Test Your Node.js Knowledge!

**Q1: What is Node.js?**
- A) Web browser
- B) JavaScript runtime
- C) Database
- D) CSS framework

<details>
<summary>Answer</summary>
**B) JavaScript runtime** - Node.js allows JavaScript to run outside the browser (server-side).
</details>

---

**Q2: Which command installs Node.js in Termux?**
- A) `apt install nodejs`
- B) `pkg install nodejs`
- C) `npm install nodejs`
- D) `pip install nodejs`

<details>
<summary>Answer</summary>
**B) `pkg install nodejs`** - Termux uses `pkg` for system packages. npm is for JavaScript packages.
</details>

---

**Q3: What is npm?**
- A) Node Package Manager
- B) New Project Maker
- C) Node Process Monitor
- D) Network Protocol Module

<details>
<summary>Answer</summary>
**A) Node Package Manager** - npm is the default package manager for Node.js, used to install JavaScript libraries.
</details>

---

**Q4: Which file stores project dependencies?**
- A) `config.json`
- B) `package.json`
- C) `dependencies.txt`
- D) `node_modules.json`

<details>
<summary>Answer</summary>
**B) `package.json`** - Contains project metadata, scripts, and dependencies.
</details>

---

**Q5: What does `npm init -y` do?**
- A) Installs dependencies
- B) Creates package.json with defaults
- C) Updates npm
- D) Runs the project

<details>
<summary>Answer</summary>
**B) Creates package.json with defaults** - Initializes a new project with default values without prompts.
</details>

---

**Q6: Where are installed packages stored?**
- A) `packages/`
- B) `node_modules/`
- C) `lib/`
- D) `modules/`

<details>
<summary>Answer</summary>
**B) `node_modules/`** - All local dependencies are installed in the node_modules directory.
</details>

---

**Q7: How do you run a Node.js script?**
- A) `node script.js`
- B) `run script.js`
- C) `npm script.js`
- D) `js script.js`

<details>
<summary>Answer</summary>
**A) `node script.js`** - The `node` command executes JavaScript files.
</details>

---

**Q8: What is Express.js?**
- A) Database
- B) Web framework for Node.js
- C) Testing tool
- D) Package manager

<details>
<summary>Answer</summary>
**B) Web framework for Node.js** - Express is a minimal and flexible web application framework.
</details>

---

**Q9: What is the `-g` flag in npm install?**
- A) Install globally
- B) Install with git
- C) Generate package
- D) Group dependencies

<details>
<summary>Answer</summary>
**A) Install globally** - Packages installed with `-g` are available system-wide, not just in the current project.
</details>

**Q10: What is the Node.js REPL?**
- A) A testing framework
- B) Interactive shell for JavaScript
- C) A package manager
- D) A file system

<details>
<summary>Answer</summary>
**B) Interactive shell for JavaScript** - REPL (Read-Eval-Print-Loop) allows you to run JavaScript interactively.
</details>

---

**Q11: Which command starts the Node.js REPL?**
- A) `node repl`
- B) `node`
- C) `npm start`
- D) `js shell`

<details>
<summary>Answer</summary>
**B) `node`** - Simply typing `node` in terminal starts the interactive shell.
</details>

---

**Q12: What does `require()` do in Node.js?**
- A) Requires user input
- B) Imports modules
- C) Requests HTTP
- D) Requires dependencies

<details>
<summary>Answer</summary>
**B) Imports modules** - `require()` is used to include modules in your Node.js application (CommonJS).
</details>

---

**Q13: What is the difference between `fork` and `spawn` in child_process?**
- A) No difference
- B) `fork` creates Node processes, `spawn` creates any process
- C) `spawn` is faster
- D) `fork` is deprecated

<details>
<summary>Answer</summary>
**B) `fork` creates Node processes, `spawn` creates any process** - `fork` is specifically for creating Node.js child processes with IPC.
</details>

---

**Q14: What is `process.nextTick()` used for?**
- A) Next timer
- B) Scheduling callback before I/O
- C) Next HTTP request
- D) Process termination

<details>
<summary>Answer</summary>
**B) Scheduling callback before I/O** - `process.nextTick()` schedules a callback to run before any I/O events in the event loop.
</details>

---

**Q15: How do you read environment variables in Node.js?**
- A) `env.VARIABLE`
- B) `process.env.VARIABLE`
- C) `getenv('VARIABLE')`
- D) `node.env.VARIABLE`

<details>
<summary>Answer</summary>
**B) `process.env.VARIABLE`** - Environment variables are accessed through the `process.env` object.
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Node.js in Termux - Practical Applications

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    SCENARIO 1: Mobile REST API Server                      ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  Problem: Need to test a mobile app with a backend API, but no laptop.    ║
║                                                                            ║
║  Solution: Create Express.js server directly on Android phone!            ║
║                                                                            ║
║  Steps:                                                                   ║
║  1. pkg install nodejs                                                    ║
║  2. mkdir api-server && cd api-server                                     ║
║  3. npm init -y && npm install express cors                               ║
║  4. Create server.js with endpoints                                       ║
║  5. node server.js (runs on localhost:3000)                               ║
║                                                                            ║
║  Benefits:                                                                ║
║  ✓ Test APIs anywhere                                                     ║
║  ✓ No laptop required                                                     ║
║  ✓ Share with team via ngrok                                              ║
║  ✓ Quick prototyping                                                      ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    SCENARIO 2: Automated Task Runner                       ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  Problem: Need to run scheduled tasks on Android automatically.           ║
║                                                                            ║
║  Solution: Node.js + cron + Termux APIs!                                  ║
║                                                                            ║
║  Implementation:                                                          ║
║  const cron = require('node-cron');                                       ║
║  const { exec } = require('child_process');                               ║
║                                                                            ║
║  // Daily backup at 2 AM                                                  ║
║  cron.schedule('0 2 * * *', () => {                                       ║
║    exec('termux-notification --title "Backup" --content "Starting..."');  ║
║    // Backup logic here                                                   ║
║  });                                                                       ║
║                                                                            ║
║  Use cases:                                                               ║
║  ✓ Automated backups                                                      ║
║  ✓ Periodic data sync                                                     ║
║  ✓ Scheduled notifications                                                ║
║  ✓ Health monitoring                                                      ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    SCENARIO 3: Web Scraper on Mobile                       ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  Problem: Need to scrape data from websites without a PC.                 ║
║                                                                            ║
║  Solution: Node.js with Cheerio or Puppeteer!                             ║
║                                                                            ║
║  Code:                                                                    ║
║  const axios = require('axios');                                          ║
║  const cheerio = require('cheerio');                                      ║
║                                                                            ║
║  async function scrape(url) {                                             ║
║    const { data } = await axios.get(url);                                 ║
║    const $ = cheerio.load(data);                                          ║
║    return $('h1').text();                                                 ║
║  }                                                                         ║
║                                                                            ║
║  Applications:                                                            ║
║  ✓ Price monitoring                                                       ║
║  ✓ News aggregation                                                       ║
║  ✓ Data collection                                                        ║
║  ✓ Content monitoring                                                     ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    SCENARIO 4: IoT Dashboard Server                        ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  Problem: Control IoT devices from Android phone.                         ║
║                                                                            ║
║  Solution: Node.js server with WebSocket + Termux sensors!                ║
║                                                                            ║
║  Architecture:                                                            ║
║  ┌─────────────┐     WebSocket     ┌─────────────┐                        ║
║  │   Phone     │◄──────────────►│  IoT Device  │                        ║
║  │ (Node.js)   │                   │  (ESP8266)  │                        ║
║  └─────────────┘                   └─────────────┘                        ║
║        │                                                                   ║
║        ▼                                                                   ║
║  ┌─────────────┐                                                          ║
║  │ Termux APIs │                                                          ║
║  │ (Sensors)   │                                                          ║
║  └─────────────┘                                                          ║
║                                                                            ║
║  Features:                                                                ║
║  ✓ Real-time sensor data                                                  ║
║  ✓ Device control interface                                               ║
║  ✓ Local network access                                                   ║
║  ✓ Mobile alerts                                                          ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                    SCENARIO 5: File Processing Pipeline                    ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                            ║
║  Problem: Process large files on mobile device.                           ║
║                                                                            ║
║  Solution: Node.js streams for memory-efficient processing!               ║
║                                                                            ║
║  Code:                                                                    ║
║  const fs = require('fs');                                                ║
║  const readline = require('readline');                                    ║
║                                                                            ║
║  const rl = readline.createInterface({                                    ║
║    input: fs.createReadStream('large-file.txt')                           ║
║  });                                                                       ║
║                                                                            ║
║  rl.on('line', (line) => {                                                ║
║    // Process each line without loading entire file                       ║
║  });                                                                       ║
║                                                                            ║
║  Use cases:                                                               ║
║  ✓ Log file analysis                                                      ║
║  ✓ CSV processing                                                         ║
║  ✓ Data transformation                                                    ║
║  ✓ Large file manipulation                                                ║
║                                                                            ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

---

## 📊 ARCHITECTURE DIAGRAMS

### 1. Node.js Event Loop Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         NODE.JS EVENT LOOP                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│    ┌──────────────────────────────────────────────────────────────────┐     │
│    │                        CALL STACK                                 │     │
│    │    ┌──────────────┐                                               │     │
│    │    │   Function   │  ← LIFO (Last In, First Out)                 │     │
│    │    └──────────────┘                                               │     │
│    └──────────────────────────────────────────────────────────────────┘     │
│                                     │                                        │
│                                     ▼                                        │
│    ┌──────────────────────────────────────────────────────────────────┐     │
│    │                     EVENT LOOP PHASES                             │     │
│    │                                                                   │     │
│    │   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐         │     │
│    │   │ TIMERS  │──►│PENDING  │──►│  POLL   │──►│  CHECK  │         │     │
│    │   │         │   │CALLBACKS│   │         │   │         │         │     │
│    │   │setTimeout│   │  I/O    │   │ I/O     │   │setImmed-│         │     │
│    │   │setInterv-│   │callbacks│   │ events  │   │  iate   │         │     │
│    │   │   al     │   │         │   │         │   │         │         │     │
│    │   └─────────┘   └─────────┘   └─────────┘   └─────────┘         │     │
│    │        ▲                                          │              │     │
│    │        └──────────────────────────────────────────┘              │     │
│    └──────────────────────────────────────────────────────────────────┘     │
│                                     │                                        │
│    ┌──────────────────────────────────────────────────────────────────┐     │
│    │                     BACKGROUND TASKS                              │     │
│    │                                                                   │     │
│    │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │     │
│    │   │  Microtask  │  │   Timers    │  │    I/O      │             │     │
│    │   │   Queue     │  │   Queue     │  │   Queue     │             │     │
│    │   │ (Promises)  │  │ (setTimeout)│  │ (fs, net)   │             │     │
│    │   └─────────────┘  └─────────────┘  └─────────────┘             │     │
│    └──────────────────────────────────────────────────────────────────┘     │
│                                                                              │
│    Execution Order:                                                          │
│    1. Call Stack executes sync code                                         │
│    2. Microtasks (Promises) run after sync, before next phase              │
│    3. Event Loop phases process async callbacks                            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 2. Node.js Module System

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      NODE.JS MODULE SYSTEM                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   YOUR APPLICATION                                                           │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  const express = require('express');                                │   │
│   │  const fs = require('fs');                                          │   │
│   │  const myModule = require('./myModule');                            │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    ▼                                         │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    MODULE RESOLUTION                                │    │
│   │                                                                    │    │
│   │   require('module') ──► Is it Core Module?                         │    │
│   │                              │                                     │    │
│   │                     Yes ┌────┴────┐ No                             │    │
│   │                         ▼         ▼                                │    │
│   │                    ┌────────┐ ┌─────────────────┐                 │    │
│   │                    │  CORE  │ │ Is it relative? │                 │    │
│   │                    │ MODULE │ │   ./ or ../     │                 │    │
│   │                    └────────┘ └────────┬────────┘                 │    │
│   │                                 Yes ┌──┴──┐ No                    │    │
│   │                                     ▼     ▼                       │    │
│   │                              ┌────────┐ ┌──────────────┐          │    │
│   │                              │RESOLVE │ │ node_modules │          │    │
│   │                              │ FROM   │ │   LOOKUP     │          │    │
│   │                              │ PATH   │ │ (up to root) │          │    │
│   │                              └────────┘ └──────────────┘          │    │
│   └────────────────────────────────────────────────────────────────────┘    │
│                                    │                                         │
│                                    ▼                                         │
│   ┌────────────────────────────────────────────────────────────────────┐    │
│   │                    MODULE CACHE                                     │    │
│   │                                                                    │    │
│   │   ┌─────────────────────────────────────────────────────────┐     │    │
│   │   │  require.cache = {                                       │     │    │
│   │   │    '/path/to/module.js': { exports: {...} },            │     │    │
│   │   │    '/path/to/express/index.js': { exports: {...} }      │     │    │
│   │   │  }                                                       │     │    │
│   │   └─────────────────────────────────────────────────────────┘     │    │
│   │                                                                    │    │
│   │   Note: Modules are cached after first require!                  │    │
│   └────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
│   Module Types:                                                              │
│   ┌────────────────┐  ┌────────────────┐  ┌────────────────┐               │
│   │  Core Modules  │  │  Local Modules │  │  NPM Modules   │               │
│   │  fs, http,     │  │  ./myModule    │  │  express,      │               │
│   │  path, crypto  │  │  ../utils     │  │  lodash, axios │               │
│   └────────────────┘  └────────────────┘  └────────────────┘               │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 3. Express.js Request Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      EXPRESS.JS REQUEST FLOW                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   CLIENT REQUEST                                                             │
│        │                                                                     │
│        ▼                                                                     │
│   ┌─────────┐                                                               │
│   │  HTTP   │  GET /api/users HTTP/1.1                                      │
│   │ REQUEST │  Host: localhost:3000                                         │
│   └─────────┘                                                               │
│        │                                                                     │
│        ▼                                                                     │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    MIDDLEWARE STACK                                  │   │
│   │                                                                    │    │
│   │   ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    │    │
│   │   │   app    │───►│  cors()  │───►│  json()  │───►│  auth()  │    │    │
│   │   │  .use()  │    │          │    │          │    │          │    │    │
│   │   └──────────┘    └──────────┘    └──────────┘    └──────────┘    │    │
│   │         │                                                │         │    │
│   │         └──────────────── next() ────────────────────────┘         │    │
│   │                                                                    │    │
│   │   Middleware: function(req, res, next) { ... next(); }            │    │
│   │                                                                    │    │
│   └─────────────────────────────────────────────────────────────────────┘   │
│        │                                                                     │
│        ▼                                                                     │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                      ROUTE HANDLER                                   │   │
│   │                                                                    │    │
│   │   app.get('/api/users', (req, res) => {                            │    │
│   │       const users = getUsers();                                     │    │
│   │       res.json({ users });  // Send response                       │    │
│   │   });                                                               │    │
│   │                                                                    │    │
│   │   Available Methods:                                                │    │
│   │   app.get()    - Read data                                         │    │
│   │   app.post()   - Create data                                       │    │
│   │   app.put()    - Update data (full)                                │    │
│   │   app.patch()  - Update data (partial)                             │    │
│   │   app.delete() - Delete data                                       │    │
│   │                                                                    │    │
│   └─────────────────────────────────────────────────────────────────────┘   │
│        │                                                                     │
│        ▼                                                                     │
│   ┌─────────┐                                                               │
│   │  HTTP   │  HTTP/1.1 200 OK                                             │
│   │RESPONSE │  Content-Type: application/json                              │
│   └─────────┘  {"users": [...]}                                             │
│        │                                                                     │
│        ▼                                                                     │
│   CLIENT RECEIVES RESPONSE                                                   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Worker Threads

```javascript
// main.js - Offload CPU-intensive tasks to worker threads
const { Worker, isMainThread, parentPort, workerData } = require('worker_threads');

if (isMainThread) {
    // Main thread - create worker
    const worker = new Worker(__filename, {
        workerData: { start: 1, end: 10000000 }
    });
    
    worker.on('message', (result) => {
        console.log('Result:', result);
    });
    
    worker.on('error', (err) => {
        console.error('Worker error:', err);
    });
    
    worker.on('exit', (code) => {
        if (code !== 0) {
            console.error(`Worker stopped with exit code ${code}`);
        }
    });
} else {
    // Worker thread - perform heavy computation
    const { start, end } = workerData;
    let sum = 0;
    for (let i = start; i <= end; i++) {
        sum += i;
    }
    parentPort.postMessage(sum);
}

// Use case: Image processing, cryptography, heavy calculations
// Note: Worker threads work in Termux on Node.js 12+
```

### Advanced Technique 2: Custom Streams

```javascript
// Create custom readable/writable streams
const { Readable, Writable, Transform } = require('stream');

// Custom Readable Stream
class NumberStream extends Readable {
    constructor(max) {
        super();
        this.max = max;
        this.current = 0;
    }
    
    _read(size) {
        if (this.current >= this.max) {
            this.push(null); // End stream
            return;
        }
        this.push(`${this.current++}\n`);
    }
}

// Custom Transform Stream
class DoubleTransform extends Transform {
    _transform(chunk, encoding, callback) {
        const num = parseInt(chunk.toString());
        this.push(`${num * 2}\n`);
        callback();
    }
}

// Custom Writable Stream
class LogWritable extends Writable {
    _write(chunk, encoding, callback) {
        console.log('Received:', chunk.toString().trim());
        callback();
    }
}

// Pipeline
const { pipeline } = require('stream');
pipeline(
    new NumberStream(10),
    new DoubleTransform(),
    new LogWritable(),
    (err) => {
        if (err) console.error('Pipeline failed:', err);
        else console.log('Pipeline succeeded');
    }
);
```

### Advanced Technique 3: Cluster Mode for Production

```javascript
// cluster.js - Utilize all CPU cores
const cluster = require('cluster');
const os = require('os');
const express = require('express');

const numCPUs = os.cpus().length;

if (cluster.isMaster) {
    console.log(`Master ${process.pid} is running`);
    console.log(`Forking ${numCPUs} workers...`);
    
    // Fork workers
    for (let i = 0; i < numCPUs; i++) {
        cluster.fork();
    }
    
    // Restart worker on exit
    cluster.on('exit', (worker, code, signal) => {
        console.log(`Worker ${worker.process.pid} died. Restarting...`);
        cluster.fork();
    });
    
    // Handle worker disconnect
    cluster.on('disconnect', (worker) => {
        console.log(`Worker ${worker.process.pid} disconnected`);
    });
} else {
    // Worker process - create Express server
    const app = express();
    
    app.get('/', (req, res) => {
        res.json({
            worker: process.pid,
            message: 'Hello from worker!'
        });
    });
    
    app.get('/heavy', (req, res) => {
        // CPU-intensive task
        let sum = 0;
        for (let i = 0; i < 1e7; i++) sum += i;
        res.json({ worker: process.pid, sum });
    });
    
    app.listen(3000, () => {
        console.log(`Worker ${process.pid} started on port 3000`);
    });
}

// Benefits:
// - Handles more concurrent requests
// - Zero downtime restarts
// - Better CPU utilization
// - Built-in fault tolerance
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### Fundamentals
- [ ] Installed Node.js in Termux (`pkg install nodejs`)
- [ ] Verified installation (`node --version`, `npm --version`)
- [ ] Understood Node.js = JavaScript on server
- [ ] Learned REPL (interactive shell)

### NPM Mastery
- [ ] Initialized project (`npm init -y`)
- [ ] Installed packages locally (`npm install <package>`)
- [ ] Installed packages globally (`npm install -g <package>`)
- [ ] Understood package.json structure
- [ ] Used npm scripts

### Core Modules
- [ ] Used `fs` module for file operations
- [ ] Created HTTP server with `http` module
- [ ] Used `path` for path manipulation
- [ ] Accessed process information

### Express.js Basics
- [ ] Installed Express (`npm install express`)
- [ ] Created basic server
- [ ] Defined routes (GET, POST, PUT, DELETE)
- [ ] Used middleware (`app.use()`)
- [ ] Served JSON responses

### Advanced Topics
- [ ] Used async/await for async operations
- [ ] Implemented error handling
- [ ] Used streams for large files
- [ ] Integrated Termux APIs with Node.js

### Process Management
- [ ] Installed PM2 (`npm install -g pm2`)
- [ ] Started applications with PM2
- [ ] Monitored processes
- [ ] Configured auto-restart

---

## 💡 PRO TIPS

### 10 Node.js Pro Tips

> **💡 Pro Tip #1: Use `npm ci` for CI/CD**
> Faster, deterministic installs:
> ```bash
> npm ci  # Uses package-lock.json exactly
> # Faster than npm install
> ```

> **💡 Pro Tip #2: Use `nodemon` for Development**
> Auto-restart on file changes:
> ```bash
> npm install -g nodemon
> nodemon server.js
> ```

> **💡 Pro Tip #3: Use `package-lock.json`**
> Commit it for consistent installs:
> ```bash
> git add package-lock.json
> # Ensures same versions everywhere
> ```

> **💡 Pro Tip #4: Use ES Modules (ESM)**
> Modern import syntax:
> ```javascript
> // package.json: "type": "module"
> import express from 'express';
> export default app;
> ```

> **💡 Pro Tip #5: Environment Variables**
> Keep secrets safe:
> ```bash
> npm install dotenv
> ```
> ```javascript
> require('dotenv').config();
> const port = process.env.PORT || 3000;
> ```

> **💡 Pro Tip #6: Use `npm scripts`**
> Automate common tasks:
> ```json
> {
>   "scripts": {
>     "start": "node server.js",
>     "dev": "nodemon server.js",
>     "test": "jest"
>   }
> }
> ```

> **💡 Pro Tip #7: Handle Uncaught Exceptions**
> Prevent crashes:
> ```javascript
> process.on('uncaughtException', (err) => {
>   console.error('Uncaught Exception:', err);
>   process.exit(1);
> });
> ```

> **💡 Pro Tip #8: Use Async/Await**
> Clean asynchronous code:
> ```javascript
> // Instead of callbacks
> async function getData() {
>   try {
>     const response = await fetch(url);
>     const data = await response.json();
>     return data;
>   } catch (error) {
>     console.error(error);
>   }
> }
> ```

> **💡 Pro Tip #9: Cluster Mode**
> Use all CPU cores:
> ```javascript
> const cluster = require('cluster');
> const numCPUs = require('os').cpus().length;
> 
> if (cluster.isMaster) {
>   for (let i = 0; i < numCPUs; i++) {
>     cluster.fork();
>   }
> }
> ```

> **💡 Pro Tip #10: Use PM2 for Production**
> Process management:
> ```bash
> npm install -g pm2
> pm2 start server.js --name "app"
> pm2 monit
> ```

---

## 🔥 REAL WORLD USE CASES

### Node.js Applications in Termux

**Use Case #1: REST API Server**
```javascript
// server.js - RESTful API
const express = require('express');
const app = express();

app.use(express.json());

let items = [];

// CRUD Operations
app.get('/items', (req, res) => res.json(items));

app.post('/items', (req, res) => {
  const item = { id: Date.now(), ...req.body };
  items.push(item);
  res.status(201).json(item);
});

app.put('/items/:id', (req, res) => {
  const index = items.findIndex(i => i.id === +req.params.id);
  if (index === -1) return res.status(404).json({ error: 'Not found' });
  items[index] = { ...items[index], ...req.body };
  res.json(items[index]);
});

app.delete('/items/:id', (req, res) => {
  items = items.filter(i => i.id !== +req.params.id);
  res.status(204).send();
});

app.listen(3000, () => console.log('API running on port 3000'));
```

**Use Case #2: Web Scraper**
```javascript
// scraper.js - Web scraping with Node.js
const https = require('https');
const cheerio = require('cheerio');

async function scrape(url) {
  return new Promise((resolve, reject) => {
    https.get(url, (res) => {
      let data = '';
      res.on('data', chunk => data += chunk);
      res.on('end', () => {
        const $ = cheerio.load(data);
        const titles = [];
        $('h2').each((i, el) => titles.push($(el).text()));
        resolve(titles);
      });
    }).on('error', reject);
  });
}

// Usage
scrape('https://example.com').then(console.log);
```

**Use Case #3: File Watcher**
```javascript
// watcher.js - Monitor file changes
const fs = require('fs');
const path = require('path');

function watchDirectory(dir, callback) {
  fs.watch(dir, { recursive: true }, (event, filename) => {
    if (filename) {
      callback(event, path.join(dir, filename));
    }
  });
  console.log(`Watching: ${dir}`);
}

watchDirectory('./src', (event, file) => {
  console.log(`${event}: ${file}`);
  // Add your logic here
});
```

**Use Case #4: CLI Tool**
```javascript
#!/usr/bin/env node
// mycli.js - Command Line Tool
const { program } = require('commander');

program
  .version('1.0.0')
  .description('My CLI Tool')
  .option('-n, --name <name>', 'Your name')
  .option('-v, --verbose', 'Verbose output')
  .action((options) => {
    console.log(`Hello, ${options.name || 'World'}!`);
    if (options.verbose) {
      console.log('Verbose mode enabled');
    }
  });

program.parse();
```

**Use Case #5: Termux API Integration**
```javascript
// termux-notify.js - Send notifications
const { exec } = require('child_process');

function notify(title, message) {
  exec(`termux-notification --title "${title}" --content "${message}"`, 
    (error) => {
      if (error) console.error('Notification failed:', error);
      else console.log('Notification sent!');
    }
  );
}

function vibrate(duration = 500) {
  exec(`termux-vibrate -d ${duration}`);
}

function getBattery() {
  return new Promise((resolve) => {
    exec('termux-battery-status', (error, stdout) => {
      if (!error) resolve(JSON.parse(stdout));
    });
  });
}

// Usage
notify('My App', 'Task completed!');
getBattery().then(console.log);
```

---

## ⚡ QUICK REFERENCE CARD

### Node.js Commands

| Command | Description |
|---------|-------------|
| `node` | Start REPL |
| `node file.js` | Run script |
| `node -v` | Check version |
| `node -e "code"` | Execute one-liner |

### npm Commands

| Command | Description |
|---------|-------------|
| `npm init` | Create package.json |
| `npm init -y` | Create with defaults |
| `npm install` | Install dependencies |
| `npm install pkg` | Install package |
| `npm install -g pkg` | Install globally |
| `npm uninstall pkg` | Remove package |
| `npm update` | Update packages |
| `npm list` | List packages |
| `npm run script` | Run npm script |
| `npm audit` | Security check |

### package.json Structure

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js",
    "test": "jest"
  },
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^3.0.0"
  }
}
```

### Built-in Modules

| Module | Purpose |
|--------|---------|
| `fs` | File system |
| `http` | HTTP server |
| `path` | Path utilities |
| `os` | OS info |
| `crypto` | Cryptography |
| `events` | Event emitter |
| `util` | Utilities |
| `stream` | Streaming |
| `child_process` | Spawn processes |

---

## 🏆 BONUS CONTENT

### Express.js Application Template

```javascript
// app.js - Production-ready Express app
const express = require('express');
const app = express();

// Middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Request logging
app.use((req, res, next) => {
  console.log(`${new Date().toISOString()} ${req.method} ${req.path}`);
  next();
});

// Routes
app.get('/', (req, res) => {
  res.json({ message: 'API is running' });
});

app.get('/health', (req, res) => {
  res.json({ status: 'healthy', timestamp: new Date() });
});

// Error handling
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ error: 'Something went wrong!' });
});

// 404 handler
app.use((req, res) => {
  res.status(404).json({ error: 'Not found' });
});

// Start server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});

module.exports = app;
```

### package.json Scripts

```json
{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js",
    "test": "jest --coverage",
    "lint": "eslint .",
    "format": "prettier --write .",
    "build": "node build.js",
    "clean": "rm -rf node_modules && npm install"
  }
}
```

### PM2 Configuration

```javascript
// ecosystem.config.js
module.exports = {
  apps: [{
    name: 'my-app',
    script: 'server.js',
    instances: 'max',
    exec_mode: 'cluster',
    autorestart: true,
    watch: false,
    max_memory_restart: '1G',
    env: {
      NODE_ENV: 'production',
      PORT: 3000
    }
  }]
};
```

---

## 📝 CHAPTER SUMMARY

### Key Takeaways

| Topic | Key Points |
|-------|------------|
| **Installation** | `pkg install nodejs` |
| **npm** | Package manager for JavaScript |
| **package.json** | Project config & dependencies |
| **Running** | `node script.js` |
| **REPL** | Interactive shell (`node`) |
| **Express** | Web framework for APIs |
| **PM2** | Process manager for production |

### Common Commands

```bash
# Setup
pkg install nodejs
npm init -y

# Development
npm install express
npm install -D nodemon
npm run dev

# Production
npm install -g pm2
pm2 start server.js
```

---

## 🎯 INTERVIEW QUESTIONS

### Node.js Interview Questions

**Q1: What is the event loop in Node.js?**

<details>
<summary>Answer</summary>
The event loop is what allows Node.js to perform non-blocking I/O operations. It continuously checks the call stack and task queue, executing callbacks when the stack is empty.

```javascript
console.log('1');
setTimeout(() => console.log('2'), 0);
Promise.resolve().then(() => console.log('3'));
console.log('4');
// Output: 1, 4, 3, 2
```
</details>

**Q2: What's the difference between `process.nextTick()` and `setImmediate()`?**

<details>
<summary>Answer</summary>
- `process.nextTick()`: Executes before the event loop continues (microtask)
- `setImmediate()`: Executes in the next iteration of event loop (check phase)

```javascript
setImmediate(() => console.log('immediate'));
process.nextTick(() => console.log('nextTick'));
// Output: nextTick, immediate
```
</details>

**Q3: Explain the difference between CommonJS and ES Modules.**

<details>
<summary>Answer</summary>
**CommonJS** (Node.js default):
```javascript
const express = require('express');
module.exports = app;
```

**ES Modules** (Modern):
```javascript
import express from 'express';
export default app;
```

Enable ESM with `"type": "module"` in package.json.
</details>

**Q4: What is middleware in Express?**

<details>
<summary>Answer</summary>
Middleware functions have access to request, response, and next function.

```javascript
// Logger middleware
app.use((req, res, next) => {
  console.log(`${req.method} ${req.path}`);
  next(); // Pass to next middleware
});

// Error handling middleware
app.use((err, req, res, next) => {
  res.status(500).json({ error: err.message });
});
```
</details>

**Q5: How do you handle async errors in Express?**

<details>
<summary>Answer</summary>
```javascript
// Wrap async routes
const asyncHandler = fn => (req, res, next) => 
  Promise.resolve(fn(req, res, next)).catch(next);

app.get('/data', asyncHandler(async (req, res) => {
  const data = await fetchData();
  res.json(data);
}));
```
</details>

---

## 🚀 BEST PRACTICES

### Node.js Style Guide

```javascript
// ✅ Use const/let, avoid var
const express = require('express');
let count = 0;

// ✅ Use async/await over callbacks
async function getData() {
  try {
    const response = await fetch(url);
    return await response.json();
  } catch (error) {
    console.error(error);
    throw error;
  }
}

// ✅ Handle errors properly
process.on('unhandledRejection', (reason, promise) => {
  console.error('Unhandled Rejection:', reason);
});

// ✅ Use environment variables
const port = process.env.PORT || 3000;

// ✅ Organize imports
const fs = require('fs');  // Built-in
const express = require('express');  // External
const myModule = require('./myModule');  // Local
```

### Common Mistakes to Avoid

| ❌ Mistake | ✅ Solution |
|-----------|------------|
| Blocking event loop | Use async operations |
| Not handling errors | Use try/catch, error handlers |
| Using `var` | Use `const`/`let` |
| Hardcoded values | Use environment variables |
| No package-lock | Commit package-lock.json |

---

## 📊 CODE COMPARISON

### Bad vs Good: Node.js Code

**Async Handling**
```javascript
// ❌ BAD: Callback hell
getData(function(a) {
  getMoreData(a, function(b) {
    getMoreData(b, function(c) {
      console.log(c);
    });
  });
});

// ✅ GOOD: Async/await
async function getAllData() {
  const a = await getData();
  const b = await getMoreData(a);
  const c = await getMoreData(b);
  return c;
}
```

**Error Handling**
```javascript
// ❌ BAD: No error handling
app.get('/data', async (req, res) => {
  const data = await fetchData();
  res.json(data);
});

// ✅ GOOD: Proper error handling
app.get('/data', async (req, res, next) => {
  try {
    const data = await fetchData();
    res.json(data);
  } catch (error) {
    next(error);
  }
});
```

**Environment Configuration**
```javascript
// ❌ BAD: Hardcoded values
const dbHost = 'localhost';
const dbPort = 5432;

// ✅ GOOD: Environment variables
const dbHost = process.env.DB_HOST || 'localhost';
const dbPort = process.env.DB_PORT || 5432;
```

---

## 🔗 RELATED CHAPTERS

### Prerequisites
- **Chapter 11**: Python Installation (comparison)
- **Chapter 15**: Git Version Control

### Next Steps
- **Chapter 17**: Termux API with Node.js
- **Chapter 22**: Web Development

### Related Topics
- **Chapter 12**: Python Basics (alternative)
- **Chapter 13**: Bash Scripting (npm scripts)

---

*Updated by T3rmuxk1ng | Termux Full Course - Module 3: Programming*
