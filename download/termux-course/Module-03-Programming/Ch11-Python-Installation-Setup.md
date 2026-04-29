# Chapter 11: Python Installation & Setup

> **Module:** 3 - Programming  
> **Chapter:** 11 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐ Beginner

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Python installation & configuration |
| Installation Guide | Python 2, Python 3, pip, venv setup |
| Commands Reference | All commands covered in chapter |
| Practice Exercises | Hands-on Python setup tasks |
| Troubleshooting | Common Python issues in Termux |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 11
Title: Python Installation & Setup | Complete Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome to Chapter 11 of Termux Full Course!

Main aapka host hoon aur aaj ek bahut important chapter hai - Python 
Installation & Setup in Termux.

Python - programming world ka king! Agar aap ethical hacking, 
automation, web development, data science, machine learning - kuch 
bhi seekhna chahte ho - Python aapke liye zaruri hai.

Termux mein Python install karna easy hai, lekin sahi tarah setup 
karna important hai. Aaj hum cover karenge:
- Python installation
- pip package manager
- Virtual environments
- Common packages
- Python IDE in Termux

Ye chapter beginners ke liye hai - koi prior Python knowledge 
chahiye nahi. Bas Termux installed hona chahiye (Chapter 1 se 
install kar sakte ho agar nahi hai).

To chaliye shuru karte hain!

Play button dabaiye, video like karein, subscribe karein.

---

[SECTION 1: PYTHON INTRODUCTION - 0:50 to 3:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle - Python kya hai aur kyun important hai?

Python ek high-level programming language hai. Simple syntax, 
easy to learn, powerful capabilities. 1991 mein Guido van Rossum 
ne banaya tha.

Python ki special baat - readability. Code padhna easy hai, 
likhna easy hai. Beginners ke liye perfect language.

Termux mein Python ka importance:

✓ Hacking Tools - Most tools Python mein bane hain
✓ Automation - Scripts se repetitive tasks automate karo
✓ Web Scraping - Data extract karo websites se
✓ API Testing - Security testing ke liye
✓ Exploit Development - Many exploits Python mein
✓ Machine Learning - Data analysis

Termux mein Python install karna desktop se thoda alaga hai. 
Desktop pe aap python.org se download karte ho. Termux mein 
pkg command se install hota hai - simple!

Python ke do major versions hain - Python 2 aur Python 3.

Python 2 - OLD, deprecated, 2020 mein end of life ho gaya.
Python 3 - CURRENT, actively developed, use this!

Termux mein dono versions available hain, lekin hum Python 3 
use karenge kyunki wo modern hai aur supported hai.

---

[SECTION 2: PYTHON INSTALLATION - 3:30 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Ab chaliye Python install karte hain Termux mein.

[SCREEN: Termux terminal]

Step 1: Pehle Termux ko update karein

    pkg update && pkg upgrade -y

Ye command packages list update karega aur installed packages 
ko upgrade karega. Good practice hai regular updates ka.

Step 2: Python install karein

    pkg install python -y

Ye command Python 3 install karega. 'python' package Python 3 
denge Termux mein.

Installation mein thoda time lagega - Python dependencies 
download hogi. Wait karein.

[SCREEN: Installation progress]

Step 3: Installation verify karein

    python --version

Output kuch aisa aana chahiye:
    Python 3.11.x (version number different ho sakta hai)

Agar version dikh raha hai - Congratulations! Python 
successfully install ho gaya!

Step 4: Python executable check

    which python

Output: /data/data/com.termux/files/usr/bin/python

Ye path batata hai ki Python kahan installed hai.

Step 5: Python 3 specific command

    python3 --version

Termux mein 'python' aur 'python3' dono same hain - Python 3.

Step 6: pip install verify

pip - Python package manager. Ye Python ke saath automatically 
install ho jata hai.

    pip --version

Output: pip 23.x.x from ...

pip working hai - perfect!

---

[SECTION 3: PYTHON 2 VS PYTHON 3 - 7:00 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Ab samjhte hain Python 2 aur Python 3 mein kya difference hai.

[COMPARISON TABLE]

┌─────────────────────────────────────────────────────────────────────────┐
│                    PYTHON 2 VS PYTHON 3                                 │
├────────────────┬──────────────────────┬────────────────────────────────┤
│ Feature        │ Python 2             │ Python 3                       │
├────────────────┼──────────────────────┼────────────────────────────────┤
│ Status         │ ❌ Deprecated        │ ✅ Active Development          │
│ Print Syntax   │ print "Hello"        │ print("Hello")                 │
│ Division       │ 5/2 = 2 (integer)    │ 5/2 = 2.5 (float)              │
│ Unicode        │ ASCII default        │ Unicode default                │
│ Support        │ Ended Jan 2020       │ Ongoing                        │
│ Security       │ No patches           │ Active security updates        │
│ Recommendation │ ❌ Don't use         │ ✅ Use this                    │
└────────────────┴──────────────────────┴────────────────────────────────┘

Python 2 install karna (agar zarurat ho):

    pkg install python2 -y

Tab command hogi:
    python2 --version

Lekin 99% cases mein Python 3 use karein. Old scripts ho 
sakte hain Python 2 ke, lekin naye projects ke liye 
Python 3 mandatory hai.

---

[SECTION 4: PIP PACKAGE MANAGER - 9:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

pip - Python ka package manager. "Pip Installs Packages" ya 
"Preferred Installer Program".

Python ki real power uske packages mein hai. Thousands of 
packages available hain - ready-to-use code.

pip Commands:

[COMMAND 1: Package Install]

    pip install <package-name>

Example:
    pip install requests

Ye 'requests' package install karega - HTTP requests ke liye.

[COMMAND 2: Package Uninstall]

    pip uninstall <package-name>

Example:
    pip uninstall requests

Confirm ke liye 'y' press karein.

[COMMAND 3: List Installed Packages]

    pip list

Saare installed packages dikhega with versions.

[COMMAND 4: Show Package Info]

    pip show <package-name>

Example:
    pip show requests

Details dikhega - version, location, dependencies.

[COMMAND 5: Upgrade Package]

    pip install --upgrade <package-name>

Example:
    pip install --upgrade requests

[COMMAND 6: Install Specific Version]

    pip install <package-name>==<version>

Example:
    pip install requests==2.28.0

[COMMAND 7: Search Package]

    pip search <keyword>

Note: PyPI search disabled hai ab. Use pypi.org website.

[COMMAND 8: Freeze Requirements]

    pip freeze > requirements.txt

Ye installed packages ki list requirements.txt mein save karega.

[COMMAND 9: Install from Requirements]

    pip install -r requirements.txt

requirements.txt se saare packages install karega.

---

[SECTION 5: VIRTUAL ENVIRONMENTS - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Virtual Environment - Ek isolated Python environment.

Imagine karein:
- Project A ko Django 3.x chahiye
- Project B ko Django 4.x chahiye
- Global install se conflict hoga!

Solution: Virtual Environments

Har project ka apna environment - apna Python, apne packages, 
apna isolation. No conflicts!

Termux mein do tarah ke virtual environments hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    VENV VS VIRTUALENV                                    │
├────────────────┬──────────────────────┬────────────────────────────────┤
│ Feature        │ venv                 │ virtualenv                     │
├────────────────┼──────────────────────┼────────────────────────────────┤
│ Built-in       │ ✅ Yes (Python 3.3+) │ ❌ No (need to install)        │
│ Speed          │ Fast                 │ Faster                         │
│ Python 2       │ ❌ No support        │ ✅ Supports                    │
│ Activation     │ source bin/activate  │ source bin/activate            │
│ Recommendation │ ✅ Use this          │ For advanced needs             │
└────────────────┴──────────────────────┴────────────────────────────────┘

[VENV DEMO]

Step 1: Create virtual environment

    python -m venv myenv

Ye 'myenv' naam ka virtual environment create karega.

Step 2: Activate environment

    source myenv/bin/activate

Prompt change hoga:
    (myenv) u0_a123@localhost:~$

(myenv) prefix indicate karta hai ki environment active hai.

Step 3: Install packages in venv

    pip install requests

Ye package SIRF is environment mein install hoga. Global 
Python affect nahi hoga.

Step 4: Deactivate environment

    deactivate

Environment se bahar aa jaoge. (myenv) prefix hat jaayega.

Step 5: Delete virtual environment

    rm -rf myenv

Simple delete - environment permanently remove.

[VIRTUALENV INSTALL & USE]

Install:
    pip install virtualenv

Create:
    virtualenv myenv

Activate:
    source myenv/bin/activate

Same as venv!

---

[SECTION 6: PIP VS PKG - 15:00 to 16:30]
─────────────────────────────────────────────────────────────────────────────

Termux mein do package managers hain - pkg aur pip.

Confusion common hai - kab kya use karein?

┌─────────────────────────────────────────────────────────────────────────┐
│                    PKG VS PIP FOR PYTHON PACKAGES                        │
├────────────────┬──────────────────────┬────────────────────────────────┤
│ Aspect         │ pkg (apt)            │ pip                            │
├────────────────┼──────────────────────┼────────────────────────────────┤
│ Source         │ Termux repositories  │ PyPI (Python Package Index)    │
│ Packages       │ Limited Python pkgs  │ All Python packages            │
│ Compilation    │ Pre-compiled         │ May compile from source        │
│ Speed          │ ⚡ Fast              │ Slower (if compiling)          │
│ Dependencies   │ System-level         │ Python-level                   │
│ Update Speed   │ Delayed              │ Immediate (from PyPI)          │
│ Recommendation │ For system packages  │ For Python packages            │
└────────────────┴──────────────────────┴────────────────────────────────┘

Rule of Thumb:
- System tools (git, wget, curl) → pkg
- Python packages (requests, flask) → pip
- Both available? pip recommended for Python packages

Example:

    # Wrong approach - limited packages
    pkg install python-requests  # May not exist

    # Right approach
    pip install requests         # Direct from PyPI

Some packages available in both:
    pkg install python-numpy     # Pre-compiled, fast
    pip install numpy            # Compiles, takes time

For beginners: pip use karein. Zyada packages available hain.

---

[SECTION 7: COMMON PYTHON PACKAGES - 16:30 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Termux ke liye useful Python packages:

┌─────────────────────────────────────────────────────────────────────────┐
│                    ESSENTIAL PYTHON PACKAGES FOR TERMUX                  │
├─────────────────────────┬───────────────────────────────────────────────┤
│ Package                 │ Purpose                                       │
├─────────────────────────┼───────────────────────────────────────────────┤
│ requests                │ HTTP requests                                 │
│ beautifulsoup4          │ Web scraping                                  │
│ httpx                   │ Modern HTTP client                            │
│ paramiko                │ SSH library                                   │
│ pycryptodome            │ Cryptography                                  │
│ colorama                │ Colored terminal output                       │
│ rich                    │ Beautiful terminal formatting                 │
│ click                   │ CLI apps                                      │
│ flask                   │ Web framework                                 │
│ django                  │ Full-stack web framework                      │
│ fastapi                 │ Modern API framework                          │
│ scapy                   │ Network packet manipulation                   │
│ pwntools                │ CTF & exploit development                     │
│ impacket                │ Network protocols                             │
│ pynput                  │ Keyboard/mouse control                        │
└─────────────────────────┴───────────────────────────────────────────────┘

Install multiple packages:
    pip install requests beautifulsoup4 colorama

---

[SECTION 8: PYTHON REPL & RUNNING SCRIPTS - 18:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Python do tarah se use kar sakte ho:

[METHOD 1: REPL - Interactive Shell]

    python

Python prompt open hoga:
    >>>

Ye interactive shell hai. Commands type karo, immediate 
output dekho.

Example:
    >>> print("Hello Termux!")
    Hello Termux!
    >>> 2 + 2
    4
    >>> import os
    >>> os.getcwd()
    '/data/data/com.termux/files/home'

Exit:
    >>> exit()
    Ya: Ctrl+D

[METHOD 2: Script File]

Create script:
    nano hello.py

Type:
    print("Hello from Python script!")
    name = input("Enter your name: ")
    print(f"Welcome, {name}!")

Save: Ctrl+O, Enter, Ctrl+X

Run script:
    python hello.py

Output:
    Hello from Python script!
    Enter your name: T3rmuxk1ng
    Welcome, T3rmuxk1ng!

[METHOD 3: One-liner]

    python -c "print('Hello World!')"

Quick commands ke liye useful.

[METHOD 4: Module as script]

    python -m <module>

Example:
    python -m http.server 8000

Ye simple HTTP server start karega port 8000 pe!

---

[SECTION 9: PYTHON IDE IN TERMUX - 20:00 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Termux mein coding ke liye options:

┌─────────────────────────────────────────────────────────────────────────┐
│                    PYTHON EDITORS/IDE IN TERMUX                          │
├─────────────────────────┬───────────────────────────────────────────────┤
│ Editor                  │ Features                                      │
├─────────────────────────┼───────────────────────────────────────────────┤
│ nano                    │ Simple, built-in, good for beginners          │
│ vim                     │ Powerful, steep learning curve                │
│ neovim                  │ Modern vim with Lua support                   │
│ micro                   │ User-friendly, mouse support                  │
│ emacs                   │ Ultimate customization                        │
│ code-server             │ VS Code in browser (needs Node.js)            │
└─────────────────────────┴───────────────────────────────────────────────┘

Recommended for beginners: nano or micro

Install micro:
    pkg install micro

Run:
    micro script.py

Features:
- Syntax highlighting
- Mouse support
- Modern keybindings
- Easy to use

Advanced: Neovim with plugins

    pkg install neovim

Configuration needed, but powerful results.

---

[SECTION 10: REQUIREMENTS.TXT - 21:30 to 22:30]
─────────────────────────────────────────────────────────────────────────────

requirements.txt - Project dependencies ka record.

Create:
    pip freeze > requirements.txt

Content example:
    requests==2.31.0
    beautifulsoup4==4.12.2
    colorama==0.4.6
    certifi==2023.7.22

Install from file:
    pip install -r requirements.txt

Best Practice:
- Har project ke liye requirements.txt maintain karein
- Virtual environment use karein
- Share requirements.txt with code

Version pinning:
    requests==2.31.0      # Exact version
    requests>=2.28.0      # Minimum version
    requests<=2.31.0      # Maximum version
    requests~=2.31.0      # Compatible release

---

[SECTION 11: SUMMARY & NEXT PREVIEW - 22:30 to 24:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 11 complete! Let's summarize:

✅ Python installation in Termux - pkg install python
✅ Python 2 vs Python 3 - Python 3 use karein
✅ pip package manager - install, uninstall, list, freeze
✅ Virtual environments - venv for isolation
✅ pip vs pkg - pip for Python packages
✅ Common packages - requests, bs4, flask, etc.
✅ Running Python - REPL, scripts, one-liners
✅ IDE options - nano, micro, vim
✅ requirements.txt - dependency management

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 11 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install python               │ Install Python 3                     │
│ python --version                 │ Check Python version                 │
│ pip install <package>            │ Install Python package               │
│ pip uninstall <package>          │ Remove Python package                │
│ pip list                         │ List installed packages              │
│ pip freeze > requirements.txt    │ Export dependencies                  │
│ pip install -r requirements.txt  │ Install from requirements            │
│ python -m venv myenv             │ Create virtual environment           │
│ source myenv/bin/activate        │ Activate venv                        │
│ deactivate                       │ Deactivate venv                      │
│ python script.py                 │ Run Python script                    │
│ python -c "code"                 │ Run one-liner                        │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 12 mein hum seekhenge:
- Python basics - variables, data types
- Control flow - if, for, while
- Functions in Python
- File handling
- Python for Termux automation

Practice exercises zarur karein. Python seekhne ka best tarika 
hai practice karna!

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 12!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Python in Termux Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PYTHON IN TERMUX ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Python Installation                           │   │
│   │   Location: $PREFIX/bin/python                                   │   │
│   │   Version: Python 3.x                                            │   │
│   │                                                                   │   │
│   │   ┌─────────────────┐    ┌─────────────────┐                    │   │
│   │   │ Python Binary   │    │ Python Libraries │                    │   │
│   │   │ /bin/python3    │    │ /lib/python3.xx/ │                    │   │
│   │   └─────────────────┘    └─────────────────┘                    │   │
│   │                                                                   │   │
│   │   ┌─────────────────┐    ┌─────────────────┐                    │   │
│   │   │ pip Package Mgr │    │ Site-packages   │                    │   │
│   │   │ /bin/pip        │    │ /lib/.../site   │                    │   │
│   │   └─────────────────┘    └─────────────────┘                    │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Virtual Environments                          │   │
│   │                                                                   │   │
│   │   myenv/                                                         │   │
│   │   ├── bin/                                                       │   │
│   │   │   ├── activate      (activation script)                     │   │
│   │   │   ├── python        (symlink to system python)              │   │
│   │   │   └── pip           (venv-specific pip)                     │   │
│   │   ├── lib/                                                       │   │
│   │   │   └── python3.xx/site-packages/  (installed packages)       │   │
│   │   └── pyvenv.cfg        (configuration)                         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Package Sources                               │   │
│   │                                                                   │   │
│   │   Termux Repos ──► pkg (apt) ──► Pre-compiled packages           │   │
│   │   PyPI ──────────► pip ──────► Source/compiled packages          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Key Python Paths in Termux

| Path | Description |
|------|-------------|
| `$PREFIX/bin/python` | Python executable |
| `$PREFIX/bin/python3` | Python 3 symlink |
| `$PREFIX/bin/pip` | pip package manager |
| `$PREFIX/bin/pip3` | pip3 symlink |
| `$PREFIX/lib/python3.xx/` | Python standard library |
| `$PREFIX/lib/python3.xx/site-packages/` | Third-party packages |
| `~/.local/bin/` | User-installed scripts |
| `~/.local/lib/python3.xx/site-packages/` | User packages (pip --user) |

### 3. Python PATH Configuration

```bash
# Python's module search path
python -c "import sys; print('\n'.join(sys.path))"

# Output typically:
# /data/data/com.termux/files/usr/lib/python311.zip
# /data/data/com.termux/files/usr/lib/python3.11
# /data/data/com.termux/files/usr/lib/python3.11/lib-dynload
# /data/data/com.termux/files/usr/lib/python3.11/site-packages

# Add custom path
export PYTHONPATH="/path/to/modules:$PYTHONPATH"

# Permanent addition to ~/.bashrc
echo 'export PYTHONPATH="$HOME/my_modules:$PYTHONPATH"' >> ~/.bashrc
```

### 4. pip Configuration

```bash
# pip config file location
~/.config/pip/pip.conf

# Create pip config directory
mkdir -p ~/.config/pip

# Example pip.conf
[global]
timeout = 60
index-url = https://pypi.org/simple
trusted-host = pypi.org

[install]
user = false

# Check pip configuration
pip config list
```

---

## 🔧 INSTALLATION GUIDE

### Method 1: Standard Installation (Recommended)

```bash
# Step 1: Update Termux
pkg update && pkg upgrade -y

# Step 2: Install Python
pkg install python -y

# Step 3: Verify installation
python --version
pip --version

# Step 4: Test Python
python -c "print('Python is working!')"
```

### Method 2: Install Python with Build Tools

```bash
# For compiling Python packages from source
pkg install python build-essential libffi openssl -y

# This enables:
# - Building C extensions
# - Installing packages with native code
# - Cryptography libraries
```

### Method 3: Install Python 2 (Legacy)

```bash
# Only if you need Python 2 for old scripts
pkg install python2 -y

# Verify
python2 --version

# Use pip2 for Python 2 packages
pip2 install <package>
```

### Post-Installation Setup

```bash
# Upgrade pip to latest version
pip install --upgrade pip

# Install essential packages
pip install --upgrade setuptools wheel

# Install useful development tools
pip install virtualenv pipenv poetry

# Verify pip works
pip list
```

---

## 📋 COMMANDS REFERENCE

### Python Commands

```bash
# Check Python version
python --version
python3 --version

# Check Python location
which python

# Start Python REPL
python

# Run Python script
python script.py

# Run Python script with unbuffered output
python -u script.py

# Run Python one-liner
python -c "print('Hello')"

# Run Python module
python -m <module>

# Example: HTTP server
python -m http.server 8000

# Example: JSON pretty print
python -m json.tool file.json

# Example: pip as module
python -m pip install <package>

# Compile Python file
python -m py_compile script.py

# Check Python info
python -c "import sys; print(sys.executable)"
python -c "import sys; print(sys.version)"
```

### pip Commands

```bash
# Install package
pip install <package>

# Install specific version
pip install <package>==1.2.3

# Install minimum version
pip install <package>>=1.2.3

# Install multiple packages
pip install pkg1 pkg2 pkg3

# Install from requirements file
pip install -r requirements.txt

# Install from git repository
pip install git+https://github.com/user/repo.git

# Install from local directory
pip install ./local-package/

# Install in editable mode
pip install -e ./local-package/

# Uninstall package
pip uninstall <package>

# Uninstall multiple packages
pip uninstall pkg1 pkg2 -y

# List installed packages
pip list

# List with format
pip list --format=freeze
pip list --format=columns

# Show package details
pip show <package>

# Check package dependencies
pip show <package> | grep Requires

# Upgrade package
pip install --upgrade <package>

# Upgrade pip itself
pip install --upgrade pip

# Freeze installed packages
pip freeze

# Freeze to file
pip freeze > requirements.txt

# Download package without installing
pip download <package>

# Search packages (deprecated, use pypi.org)
pip search <query>

# Check for outdated packages
pip list --outdated

# Check for security vulnerabilities
pip check

# Clear pip cache
pip cache purge

# Show pip cache location
pip cache dir
```

### Virtual Environment Commands

```bash
# Create virtual environment (venv)
python -m venv myenv

# Create with specific Python version
python3.11 -m venv myenv

# Create virtualenv (alternative)
pip install virtualenv
virtualenv myenv

# Create with specific Python
virtualenv -p python3.11 myenv

# Activate virtual environment
source myenv/bin/activate

# Activate in fish shell
source myenv/bin/activate.fish

# Deactivate
deactivate

# Delete virtual environment
rm -rf myenv

# Check active environment
which python  # Should point to venv
echo $VIRTUAL_ENV

# Install packages in venv
pip install <package>

# Export venv packages
pip freeze > requirements.txt
```

### requirements.txt Commands

```bash
# Create requirements.txt
pip freeze > requirements.txt

# Install from requirements
pip install -r requirements.txt

# Install without cache
pip install -r requirements.txt --no-cache-dir

# Create with versions
pip freeze | grep -i "package" >> requirements.txt

# Requirements with constraints
pip install -r requirements.txt -c constraints.txt
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Python Installation & Verification

```bash
# Task: Verify Python is correctly installed

# Step 1: Check Python version
python --version
# Expected: Python 3.11.x or higher

# Step 2: Check pip version
pip --version
# Expected: pip 23.x.x from ...

# Step 3: Start Python REPL
python

# In REPL, type:
>>> import sys
>>> print(f"Python: {sys.version}")
>>> print(f"Platform: {sys.platform}")
>>> print(f"Executable: {sys.executable}")
>>> exit()

# Step 4: Run one-liner
python -c "import platform; print(f'Running on {platform.system()}')"

# Expected: Running on Linux
```

### Exercise 2: Install and Use Python Packages

```bash
# Task: Install and use requests package

# Step 1: Install requests
pip install requests

# Step 2: Verify installation
pip show requests

# Step 3: Create a test script
cat > test_requests.py << 'EOF'
import requests

# Test HTTP request
response = requests.get('https://httpbin.org/get')
print(f"Status Code: {response.status_code}")
print(f"Response: {response.json()}")
EOF

# Step 4: Run script
python test_requests.py

# Expected: JSON response from httpbin.org

# Step 5: List installed packages
pip list | grep requests

# Step 6: Create requirements.txt
pip freeze > requirements.txt

# Step 7: View requirements
cat requirements.txt
```

### Exercise 3: Virtual Environment Workflow

```bash
# Task: Create and use a virtual environment

# Step 1: Create project directory
mkdir ~/my_project
cd ~/my_project

# Step 2: Create virtual environment
python -m venv venv

# Step 3: List venv contents
ls venv/

# Step 4: Activate venv
source venv/bin/activate

# Notice prompt change: (venv) appears

# Step 5: Verify venv is active
which python
# Expected: /data/.../my_project/venv/bin/python

# Step 6: Install package in venv
pip install colorama

# Step 7: Create test script
cat > colors.py << 'EOF'
from colorama import Fore, Style

print(Fore.RED + "This is red text")
print(Fore.GREEN + "This is green text")
print(Fore.BLUE + "This is blue text")
print(Style.RESET_ALL + "Back to normal")
EOF

# Step 8: Run script
python colors.py

# Step 9: Export dependencies
pip freeze > requirements.txt
cat requirements.txt

# Step 10: Deactivate
deactivate

# Step 11: Verify deactivation
which python
# Expected: /data/data/com.termux/files/usr/bin/python

# Step 12: Reactivate and verify packages still there
source venv/bin/activate
pip list | grep colorama
deactivate
```

### Exercise 4: requirements.txt Management

```bash
# Task: Manage project dependencies

# Step 1: Create new project
mkdir ~/dep_project
cd ~/dep_project
python -m venv venv
source venv/bin/activate

# Step 2: Install multiple packages
pip install requests beautifulsoup4 colorama httpx

# Step 3: Generate requirements
pip freeze > requirements.txt

# Step 4: View requirements
cat requirements.txt

# Step 5: Simulate new environment
deactivate
rm -rf venv
python -m venv venv
source venv/bin/activate

# Step 6: Verify no packages
pip list | grep -E "requests|beautifulsoup|colorama|httpx"
# Should show nothing

# Step 7: Install from requirements
pip install -r requirements.txt

# Step 8: Verify packages installed
pip list | grep -E "requests|beautifulsoup|colorama|httpx"

# Cleanup
deactivate
cd ~
rm -rf dep_project
```

### Exercise 5: Python REPL Practice

```bash
# Task: Use Python REPL for calculations

python << 'EOF'
import math

# Basic math
print("Basic Math:")
print(f"2 + 2 = {2 + 2}")
print(f"10 / 3 = {10 / 3:.2f}")
print(f"10 // 3 = {10 // 3}")  # Integer division

# Math functions
print("\nMath Functions:")
print(f"π = {math.pi}")
print(f"√2 = {math.sqrt(2):.4f}")
print(f"sin(90°) = {math.sin(math.radians(90))}")

# String operations
print("\nString Operations:")
text = "Hello Termux Python"
print(f"Original: {text}")
print(f"Uppercase: {text.upper()}")
print(f"Lowercase: {text.lower()}")
print(f"Length: {len(text)}")
print(f"Split: {text.split()}")

# List operations
print("\nList Operations:")
numbers = [1, 2, 3, 4, 5]
print(f"List: {numbers}")
print(f"Sum: {sum(numbers)}")
print(f"Max: {max(numbers)}")
print(f"Squared: {[x**2 for x in numbers]}")
EOF
```

### Exercise 6: HTTP Server in Termux

```bash
# Task: Run Python HTTP server

# Step 1: Create directory for server
mkdir ~/webserver
cd ~/webserver

# Step 2: Create HTML file
cat > index.html << 'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>Termux Python Server</title>
    <style>
        body { font-family: Arial; margin: 40px; background: #1a1a2e; color: #eee; }
        h1 { color: #00ff88; }
    </style>
</head>
<body>
    <h1>🐍 Python HTTP Server</h1>
    <p>Running from Termux!</p>
    <p>Chapter 11 - Python Installation & Setup</p>
</body>
</html>
EOF

# Step 3: Start server (port 8080)
python -m http.server 8080 &

# Step 4: Test server
curl http://localhost:8080/

# Step 5: Find and kill server
ps aux | grep python
kill <PID>

# Or use fg to bring to foreground, then Ctrl+C
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "pip install" fails with compilation error

```bash
# Cause: Missing build dependencies

# Solution: Install build tools
pkg install build-essential clang -y

# For specific packages:
# Cryptography packages
pkg install openssl libffi -y
pip install cryptography

# Database packages
pkg install sqlite -y
pip install sqlalchemy

# Image processing
pkg install libpng libjpeg-turbo -y
pip install pillow

# lxml package
pkg install libxml2 libxslt -y
pip install lxml
```

### Problem 2: "Permission denied" when installing packages

```bash
# Cause: Virtual environment not active, trying to install globally

# Solution 1: Use virtual environment
python -m venv myenv
source myenv/bin/activate
pip install <package>

# Solution 2: Install with --user flag (not recommended in Termux)
pip install --user <package>

# Solution 3: Fix permissions (if needed)
chmod -R 755 $PREFIX/lib/python*/
```

### Problem 3: "Module not found" error

```bash
# Cause: Package not installed or wrong Python version

# Step 1: Check if package is installed
pip list | grep <package>

# Step 2: Install missing package
pip install <package>

# Step 3: Check Python path
python -c "import sys; print('\n'.join(sys.path))"

# Step 4: Verify installation location
pip show <package>

# Step 5: If venv active, check correct Python
which python
# Should point to venv/bin/python
```

### Problem 4: "externally-managed-environment" error

```bash
# Cause: PEP 668 - Python environment protection

# Solution 1: Use virtual environment (recommended)
python -m venv myenv
source myenv/bin/activate
pip install <package>

# Solution 2: Override with --break-system-packages (not recommended)
pip install --break-system-packages <package>

# Solution 3: Use pipx for CLI tools
pip install pipx
pipx install <tool>
```

### Problem 5: pip is very slow

```bash
# Cause: Network issues or PyPI mirror slow

# Solution 1: Use mirror
pip install <package> -i https://pypi.org/simple/

# Solution 2: Permanent mirror in pip.conf
mkdir -p ~/.config/pip
cat > ~/.config/pip/pip.conf << EOF
[global]
index-url = https://pypi.org/simple
trusted-host = pypi.org
EOF

# Solution 3: Use cache
pip cache dir  # Check cache location

# Solution 4: Install pre-built wheels
pip install --only-binary :all: <package>
```

### Problem 6: Virtual environment activation fails

```bash
# Cause: Script not sourced properly

# Wrong way:
./venv/bin/activate  # ❌ Won't work

# Right way:
source venv/bin/activate  # ✅ Correct
. venv/bin/activate       # ✅ Also correct

# If still failing, check script exists:
ls -la venv/bin/activate

# Recreate venv if corrupted:
rm -rf venv
python -m venv venv
```

### Problem 7: "SSL certificate verify failed"

```bash
# Cause: Outdated certificates

# Solution: Install ca-certificates
pkg install ca-certificates -y

# Update pip with cert
pip install --upgrade certifi

# If specific issue, bypass (not recommended for production)
pip install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org <package>
```

### Problem 8: Python script won't run - "command not found"

```bash
# Cause: Script not executable or wrong path

# Solution 1: Run with Python directly
python script.py

# Solution 2: Make executable
chmod +x script.py
./script.py

# Solution 3: Check shebang line
head -1 script.py
# Should be: #!/usr/bin/env python

# Solution 4: Add correct shebang
sed -i '1i#!/usr/bin/env python' script.py
```

### Problem 9: "Killed" or crash during pip install

```bash
# Cause: Out of memory (OOM)

# Solution 1: Close other apps, free memory

# Solution 2: Increase swap (if rooted)
# Not applicable for non-rooted devices

# Solution 3: Install from pkg instead
pkg search python-<package>

# Solution 4: Install with no cache
pip install --no-cache-dir <package>

# Solution 5: Use pre-built wheel if available
pip install --prefer-binary <package>
```

### Problem 10: pip install from Git fails

```bash
# Cause: git not installed

# Solution: Install git
pkg install git -y

# Then try again
pip install git+https://github.com/user/repo.git

# For private repos, use SSH (requires key setup)
pip install git+ssh://git@github.com/user/repo.git
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Blue/Yellow Python Logo]         │
│                                    │
│   🐍 PYTHON in TERMUX              │
│   Complete Setup Guide             │
│                                    │
│   ✓ pip install                    │
│   ✓ Virtual Environments           │
│   ✓ requirements.txt               │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Command Style**
```
┌────────────────────────────────────┐
│  [Terminal Background]             │
│                                    │
│   $ pkg install python             │
│   $ pip install requests           │
│   $ python -m venv myenv           │
│                                    │
│   🐍 PYTHON MASTERY                │
│   Chapter 11                       │
│                                    │
│   [T3rmuxk1ng]                     │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  🐍 PYTHON 3                       │
│  ─────────────────────────────     │
│                                    │
│  ✅ pip Package Manager            │
│  ✅ Virtual Environments           │
│  ✅ 1000+ Packages Available       │
│  ✅ No Root Required               │
│                                    │
│  TERMUX SETUP GUIDE                │
│  Chapter 11 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🐍 Termux Full Course - Chapter 11: Python Installation & Setup | Complete Guide

🔥 In this video you'll learn:
• Termux mein Python install karna
• pip package manager ka complete use
• Virtual environments (venv) setup
• requirements.txt management
• Python REPL aur scripts run karna
• Common Python packages install karna

⏱️ Timestamps:
0:00 - Introduction
0:50 - Python Introduction
3:30 - Python Installation
7:00 - Python 2 vs Python 3
9:00 - pip Package Manager
12:00 - Virtual Environments
15:00 - pip vs pkg
16:30 - Common Python Packages
18:00 - Python REPL & Running Scripts
20:00 - Python IDE in Termux
21:30 - requirements.txt
22:30 - Summary

📝 Commands from this video:
pkg update && pkg upgrade -y
pkg install python -y
python --version
pip install requests
python -m venv myenv
source myenv/bin/activate
pip freeze > requirements.txt

📦 Essential Packages:
pip install requests beautifulsoup4 colorama flask

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #Python #TermuxPython #PythonInstallation #pip #venv #T3rmuxk1ng #PythonTermux #TermuxCourse #Programming #PythonHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly.
```

### Tags List

```
termux python, python termux, python installation termux, 
pip termux, termux pip install, python setup termux,
virtual environment termux, venv termux, termux programming,
python hindi, termux python tutorial, install python termux,
termux course, termux full course, pip package manager,
python 3 termux, termux python pip, requirements.txt,
python repl termux, termux python ide, python setup guide,
t3rmuxk1ng, termux tutorial hindi, python for beginners
```

### Hashtags

```
#Termux #Python #TermuxPython #PythonInstallation #pip 
#VirtualEnvironment #venv #PythonTutorial #TermuxCourse 
#Programming #T3rmuxk1ng #LearnPython #PythonHindi 
#TermuxHindi #pipTutorial #requirements
```

---

## 📚 ADDITIONAL RESOURCES

### Official Resources

| Resource | Link |
|----------|------|
| Python Official | https://www.python.org/ |
| PyPI (Python Package Index) | https://pypi.org/ |
| Python Documentation | https://docs.python.org/3/ |
| pip Documentation | https://pip.pypa.io/ |
| venv Documentation | https://docs.python.org/3/library/venv.html |

### Termux-Specific Resources

| Resource | Link |
|----------|------|
| Termux Python Wiki | https://wiki.termux.com/wiki/Python |
| Termux Packages | https://github.com/termux/termux-packages/tree/master/packages/python |
| Termux PyPI Packages | https://wiki.termux.com/wiki/Python#Package_management |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Python Tutorial | Run `python -m tutorial` (if installed) |
| Python Help | Run `help()` in Python REPL |
| pip Help | Run `pip help` |
| Package Info | Run `pip show <package>` |

### Recommended Packages by Category

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PYTHON PACKAGES BY CATEGORY                           │
├─────────────────────┬───────────────────────────────────────────────────┤
│ Category            │ Recommended Packages                             │
├─────────────────────┼───────────────────────────────────────────────────┤
│ HTTP/Networking     │ requests, httpx, aiohttp, websocket-client       │
│ Web Scraping        │ beautifulsoup4, lxml, scrapy, selenium          │
│ Security/Hacking    │ pycryptodome, paramiko, pwntools, scapy          │
│ CLI Tools           │ click, argparse, rich, colorama                  │
│ Web Frameworks      │ flask, django, fastapi, bottle                   │
│ Data Processing     │ pandas, numpy, openpyxl, csv                     │
│ JSON/API            │ requests, pydantic, marshmallow                  │
│ Testing             │ pytest, unittest, mock                           │
│ Automation          │ fabric, invoke, schedule                         │
│ Database            │ sqlalchemy, sqlite3, pymongo                     │
└─────────────────────┴───────────────────────────────────────────────────┘
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 12, verify:

- [ ] Python 3 installed via `pkg install python`
- [ ] `python --version` shows correct version
- [ ] pip working - `pip --version` succeeds
- [ ] Successfully installed a package with pip
- [ ] Created and activated a virtual environment
- [ ] Deactivated virtual environment properly
- [ ] Created and used requirements.txt
- [ ] Ran Python script successfully
- [ ] Used Python REPL for interactive coding
- [ ] Understand pip vs pkg difference

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 12: Python Basics in Termux**

- Python variables and data types
- Control flow (if/else, loops)
- Functions and modules
- File handling in Python
- Python for Termux automation
- Practical Python scripts

---

**Chapter Complete! 🎉**

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always use virtual environments for projects! This prevents dependency conflicts and makes your projects portable.

> 💡 **Pro Tip #2:** Use `pip install --upgrade pip` regularly to keep pip updated with latest features and security fixes.

> 💡 **Pro Tip #3:** When installing packages, use `pip install package_name==version` to pin exact versions for reproducibility.

> 💡 **Pro Tip #4:** Create a `requirements.txt` immediately after setting up a project - don't wait until you forget what packages you installed.

> 💡 **Pro Tip #5:** Use `python -m venv --help` to see all venv options including `--system-site-packages` to inherit system packages.

> 💡 **Pro Tip #6:** For faster package installation, use `pip install --no-cache-dir package_name` if you have limited storage.

> 💡 **Pro Tip #7:** Use `pip list --outdated` to check which packages need updates, then update selectively.

> 💡 **Pro Tip #8:** Add `export PYTHONIOENCODING=utf-8` to your `.bashrc` to avoid encoding issues in Termux.

> 💡 **Pro Tip #9:** Use `python -c "import sys; print(sys.executable)"` to quickly verify which Python interpreter you're using.

> 💡 **Pro Tip #10:** Keep a `~/.pip/pip.conf` configuration file for consistent pip settings across all projects.

---

## 🔥 REAL WORLD APPLICATIONS

### Where Python Setup Skills Apply in Real Life

**1. Penetration Testing Setup**
- Installing security tools like impacket, pwntools, scapy
- Managing tool-specific virtual environments
- Isolating tools to prevent conflicts

**2. Mobile Development Environment**
- Setting up Termux as a portable dev environment
- Running Python scripts on Android devices
- Mobile automation and scripting

**3. DevOps & CI/CD Pipelines**
- Managing Python versions in deployment
- Creating reproducible environments
- Dependency management in production

**4. Data Science Projects**
- Managing complex ML library dependencies
- Isolating project-specific environments
- Sharing reproducible analysis setups

**5. Freelance Development**
- Quick project setup for client work
- Environment isolation between projects
- Easy project handoff with requirements.txt

---

## ⚡ QUICK REFERENCE CARD

### Python Installation Commands

| Task | Command |
|------|---------|
| Install Python | `pkg install python -y` |
| Check Python version | `python --version` |
| Check pip version | `pip --version` |
| Install package | `pip install <package>` |
| Uninstall package | `pip uninstall <package>` |
| List packages | `pip list` |
| Show package info | `pip show <package>` |
| Export requirements | `pip freeze > requirements.txt` |
| Install from requirements | `pip install -r requirements.txt` |
| Create venv | `python -m venv <name>` |
| Activate venv | `source <name>/bin/activate` |
| Deactivate venv | `deactivate` |
| Delete venv | `rm -rf <name>` |
| Run Python script | `python <script.py>` |
| Run one-liner | `python -c "code"` |
| HTTP server | `python -m http.server 8000` |
| Upgrade pip | `pip install --upgrade pip` |
| Check outdated | `pip list --outdated` |
| Security audit | `pip check` |

---

## 🏆 BONUS: ADVANCED TIPS

### Advanced Python Environment Management

```bash
# Poetry - Modern dependency management
pip install poetry
poetry new myproject
poetry add requests
poetry install

# Pipenv - Combines pip and virtualenv
pip install pipenv
pipenv install requests
pipenv shell

# Conda alternative in Termux (miniconda not fully supported)
# Use venv + pip instead

# Multiple Python versions with pyenv (requires build tools)
pkg install git build-essential
curl https://pyenv.run | bash
```

### Custom pip Configuration

```bash
# Create pip config directory
mkdir -p ~/.config/pip

# Create pip.conf with custom settings
cat > ~/.config/pip/pip.conf << 'EOF'
[global]
timeout = 120
index-url = https://pypi.org/simple
trusted-host = pypi.org
no-cache-dir = false

[install]
no-warn-script-location = true

[list]
format = columns
EOF
```

### Python Profile Optimization

```bash
# Add to ~/.bashrc for Python optimizations
export PYTHONSTARTUP=~/.pythonrc
export PYTHONIOENCODING=utf-8
export PYTHONUNBUFFERED=1

# Create Python startup file
cat > ~/.pythonrc << 'EOF'
import sys
import os
import readline
import rlcompleter
import atexit

# Enable tab completion
readline.parse_and_bind("tab: complete")

# Save command history
histfile = os.path.join(os.environ["HOME"], ".python_history")
try:
    readline.read_history_file(histfile)
except:
    pass
atexit.register(readline.write_history_file, histfile)
EOF
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ How to install Python 3 in Termux using `pkg install python`
- ✅ Understanding Python 2 vs Python 3 differences
- ✅ Using pip package manager to install/uninstall packages
- ✅ Creating and managing virtual environments with venv
- ✅ Difference between pkg and pip package managers
- ✅ Essential Python packages for Termux development
- ✅ Running Python code via REPL, scripts, and one-liners
- ✅ Managing project dependencies with requirements.txt
- ✅ Choosing and configuring code editors in Termux
- ✅ Python architecture and paths in Termux

### Key Takeaways

1. **Always use Python 3** - Python 2 is deprecated and insecure
2. **Use pip for Python packages** - More packages available than via pkg
3. **Virtual environments are essential** - Prevent dependency conflicts
4. **requirements.txt enables reproducibility** - Share and recreate environments easily
5. **Keep pip updated** - Security and feature updates

---

## 🎯 INTERVIEW QUESTIONS

### Python Installation & Setup Interview Questions

**Q1: What is the difference between pip and pkg in Termux?**

```text
Answer:
- pkg (apt): System-level package manager, installs pre-compiled packages from Termux repos
- pip: Python package manager, installs packages from PyPI (Python Package Index)
- pkg is for system tools, pip is for Python libraries
- pip has access to many more Python-specific packages
```

**Q2: Why should you use virtual environments?**

```python
# Answer: Virtual environments provide:
# 1. Dependency isolation between projects
# 2. Different package versions for different projects
# 3. Reproducible development environments
# 4. Easy project sharing and deployment
# 5. Prevents global package pollution

# Example: Project A needs Django 3.x, Project B needs Django 4.x
python -m venv project_a_env
source project_a_env/bin/activate
pip install django==3.2
```

**Q3: How do you create a requirements.txt file and why is it important?**

```bash
# Create requirements.txt
pip freeze > requirements.txt

# Why important:
# 1. Documents all project dependencies with versions
# 2. Enables reproducible installations
# 3. Makes deployment consistent
# 4. Helps in onboarding new developers
# 5. Essential for CI/CD pipelines

# Install from requirements
pip install -r requirements.txt
```

**Q4: What is the purpose of version pinning in requirements.txt?**

```text
Answer: Version pinning ensures consistent installations:
- package==1.2.3  # Exact version (most restrictive)
- package>=1.2.3  # Minimum version
- package<=1.2.3  # Maximum version
- package~=1.2.3  # Compatible release (>=1.2.3, <1.3.0)

Benefits:
1. Reproducible builds
2. Avoids breaking changes
3. Predictable behavior across environments
```

**Q5: How do you check for security vulnerabilities in installed packages?**

```bash
# Check for known vulnerabilities
pip check

# Check for outdated packages
pip list --outdated

# For comprehensive security audit
pip install safety
safety check

# Alternative: pip-audit
pip install pip-audit
pip-audit
```

**Q6: Explain the Python module search path.**

```python
# Python searches for modules in this order:
import sys
print(sys.path)

# Order:
# 1. Current directory
# 2. PYTHONPATH environment variable
# 3. Standard library directories
# 4. Site-packages directory (pip installed packages)

# Custom path addition:
import sys
sys.path.append('/custom/module/path')
```

**Q7: What is the difference between `python -m pip` and `pip`?**

```bash
# pip - Runs the pip executable directly
pip install requests

# python -m pip - Runs pip as a module
python -m pip install requests

# Difference:
# - python -m pip ensures you're using pip for the active Python interpreter
# - Useful when multiple Python versions exist
# - Recommended in scripts and documentation
```

**Q8: How would you handle a package that fails to install due to missing dependencies?**

```bash
# Step 1: Install build dependencies
pkg install build-essential libffi openssl

# Step 2: Try installation with verbose output
pip install package_name --verbose

# Step 3: Check if pre-compiled wheel is available
pip install package_name --only-binary=:all:

# Step 4: Try pre-release version if available
pip install package_name --pre

# Step 5: Use alternative package if exists
pip search alternative_package  # (if enabled)
```

**Q9: What is the shebang line and why is it important?**

```python
#!/usr/bin/env python3
"""
The shebang (#!) tells the system which interpreter to use.

Why important:
1. Makes scripts executable directly (./script.py)
2. Portable across different systems
3. No need to specify interpreter each time

Best practices:
- Use #!/usr/bin/env python3 for portability
- Use #!/data/data/com.termux/files/usr/bin/python for Termux-specific
"""
```

**Q10: How do you upgrade all outdated packages safely?**

```bash
# List outdated packages first
pip list --outdated

# Option 1: Upgrade all at once (not recommended for production)
pip list --outdated --format=freeze | grep -v '^\-e' | cut -d = -f 1 | xargs -n1 pip install -U

# Option 2: Upgrade one by one (safer)
pip install --upgrade package_name

# Option 3: Use pip-review tool
pip install pip-review
pip-review --auto

# Always test after upgrades!
```

---

## 🚀 BEST PRACTICES

### Code Style Guidelines

```python
# Good: Use clear variable names
python_version = "3.11"
package_name = "requests"

# Bad: Cryptic variable names
pv = "3.11"
pn = "requests"

# Good: Use virtual environments for every project
python -m venv myproject_env

# Bad: Installing everything globally
pip install package  # without venv
```

### Performance Tips

```bash
# Use pre-compiled packages when available (faster installation)
pkg install python-numpy  # Pre-compiled in Termux
pip install numpy         # Compiles from source (slower)

# Use --no-cache-dir to save storage
pip install package --no-cache-dir

# Use --prefer-binary for faster installs
pip install package --prefer-binary

# Disable unnecessary features
pip install package --no-deps  # If deps already installed
```

### Common Mistakes to Avoid

```bash
# ❌ Mistake: Spaces around = in variable assignment (in bash)
name = "value"  # Wrong!
name="value"    # Correct!

# ❌ Mistake: Not activating venv before installing
pip install package  # Installs globally
# Correct: Activate venv first
source venv/bin/activate
pip install package

# ❌ Mistake: Using Python 2 for new projects
python2 script.py  # Wrong!
python script.py   # Correct (Python 3)

# ❌ Mistake: Not pinning versions in requirements
requests  # Wrong - any version
requests==2.31.0  # Correct - specific version

# ❌ Mistake: Ignoring pip security warnings
pip install package  # Check warnings!
pip check  # Run security audit
```

---

## 📊 CODE COMPARISON

### Before vs After: Python Setup

```bash
# ❌ BEFORE: Messy global installation
pip install django
pip install flask
pip install requests
pip install numpy
# Now everything is global, potential conflicts!

# ✅ AFTER: Proper isolated setup
mkdir myproject && cd myproject
python -m venv venv
source venv/bin/activate
pip install django flask requests numpy
pip freeze > requirements.txt
# Clean, isolated, reproducible!
```

### Bad vs Good Practices

```bash
# ❌ BAD: No version control, no isolation
pip install package
pip install another-package
pip install yet-another

# ✅ GOOD: Proper workflow
python -m venv .venv
source .venv/bin/activate
pip install package==1.2.3 another-package==2.0.0
pip freeze > requirements.txt
```

```python
# ❌ BAD: No documentation of dependencies
# (No requirements.txt, packages installed randomly)

# ✅ GOOD: Documented dependencies
# requirements.txt:
requests==2.31.0
beautifulsoup4==4.12.2
colorama==0.4.6
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relevance |
|---------|-------|-----------|
| Chapter 10 | Termux Storage Setup | Understanding file paths for Python |
| Chapter 12 | Python Basics | Next step after installation |
| Chapter 13 | Bash Scripting Basics | Shell integration with Python |
| Chapter 15 | Git Version Control | Managing Python projects |
| Chapter 16 | Node.js | Alternative runtime comparison |
| Chapter 25 | Python for Hacking | Advanced Python usage |
| Chapter 30 | Web Scraping | Python requests & BeautifulSoup |
| Chapter 35 | API Development | Flask/Django in Termux |

---

## 🎮 INTERACTIVE QUIZ

### Quiz: Python Installation & Setup

**1. What command installs Python 3 in Termux?**
- A) `apt install python3`
- B) `pkg install python`
- C) `pip install python`
- D) `python install`

<details>
<summary>Click for Answer</summary>
**Answer: B) `pkg install python`**

In Termux, the `pkg` command is used for system packages. `python` package provides Python 3.
</details>

**2. Which command creates a virtual environment named "myenv"?**
- A) `venv create myenv`
- B) `python venv myenv`
- C) `python -m venv myenv`
- D) `pip venv myenv`

<details>
<summary>Click for Answer</summary>
**Answer: C) `python -m venv myenv`**

The `venv` module is run as a Python module using `-m` flag.
</details>

**3. What is the purpose of requirements.txt?**
- A) Store Python code
- B) Document project dependencies
- C) Configure Python settings
- D) Store environment variables

<details>
<summary>Click for Answer</summary>
**Answer: B) Document project dependencies**

requirements.txt lists all packages with versions for reproducible installations.
</details>

**4. Which pip command shows installed packages?**
- A) `pip show`
- B) `pip installed`
- C) `pip list`
- D) `pip packages`

<details>
<summary>Click for Answer</summary>
**Answer: C) `pip list`**

`pip list` shows all installed packages with versions.
</details>

**5. How do you activate a virtual environment?**
- A) `activate myenv`
- B) `source myenv/bin/activate`
- C) `venv activate myenv`
- D) `python activate myenv`

<details>
<summary>Click for Answer</summary>
**Answer: B) `source myenv/bin/activate`**

The activate script is in the bin directory of the venv.
</details>

**6. What does `pip freeze` do?**
- A) Stops pip from working
- B) Freezes package installations
- C) Outputs installed packages in requirements format
- D) Pauses package downloads

<details>
<summary>Click for Answer</summary>
**Answer: C) Outputs installed packages in requirements format**

`pip freeze` lists packages as `package==version` format suitable for requirements.txt.
</details>

**7. Which is the recommended Python version for new projects?**
- A) Python 2.7
- B) Python 3.x
- C) Python 1.x
- D) Any version works

<details>
<summary>Click for Answer</summary>
**Answer: B) Python 3.x**

Python 2 is deprecated (ended Jan 2020). Always use Python 3 for new projects.
</details>

**8. What command runs Python interactively?**
- A) `python -i`
- B) `python interactive`
- C) `python`
- D) `python shell`

<details>
<summary>Click for Answer</summary>
**Answer: C) `python`**

Typing `python` alone starts the REPL (interactive shell).
</details>

**9. How do you install a specific version of a package?**
- A) `pip install package@1.2.3`
- B) `pip install package==1.2.3`
- C) `pip install package:1.2.3`
- D) `pip install package-1.2.3`

<details>
<summary>Click for Answer</summary>
**Answer: B) `pip install package==1.2.3`**

Use `==` to specify exact version for pip.
</details>

**10. What command checks for package vulnerabilities?**
- A) `pip secure`
- B) `pip check`
- C) `pip scan`
- D) `pip audit`

<details>
<summary>Click for Answer</summary>
**Answer: B) `pip check`**

`pip check` verifies installed packages have compatible dependencies and no known issues.
</details>

---

## 🔧 DEBUG THIS EXERCISES

### Debug This #1: Installation Error

```bash
# Problem: Command fails
pkg install python3

# Error: E: Unable to locate package python3
```

<details>
<summary>Click for Solution</summary>

```bash
# Solution: In Termux, the package is named 'python' not 'python3'
# Correct command:
pkg install python

# Verify:
python --version  # Shows Python 3.x.x
```
</details>

### Debug This #2: Virtual Environment Not Activating

```bash
# Problem: No (venv) prefix in prompt
python -m venv myenv
myenv/bin/activate
# Prompt doesn't change
```

<details>
<summary>Click for Solution</summary>

```bash
# Solution: Forgot 'source' command
# Correct command:
source myenv/bin/activate

# Now prompt shows:
(myenv) u0_a123@localhost:~$
```
</details>

### Debug This #3: pip Not Found

```bash
# Problem: pip command not found after Python installation
pkg install python
pip --version
# Error: pip: command not found
```

<details>
<summary>Click for Solution</summary>

```bash
# Solution 1: Restart Termux or reload shell
exec bash

# Solution 2: Use python -m pip
python -m pip --version

# Solution 3: Reinstall pip
python -m ensurepip --upgrade
```
</details>

### Debug This #4: Package Installation Fails

```bash
# Problem: Package fails to compile
pip install cryptography
# Error: Failed building wheel for cryptography
```

<details>
<summary>Click for Solution</summary>

```bash
# Solution: Install build dependencies first
pkg install build-essential libffi openssl

# Then retry installation
pip install cryptography

# Alternative: Use pre-compiled version if available
pip install cryptography --prefer-binary
```
</details>

### Debug This #5: Import Error

```python
# Problem: Module not found
import requests
# ModuleNotFoundError: No module named 'requests'
```

<details>
<summary>Click for Solution</summary>

```python
# Solution 1: Install the package
# pip install requests

# Solution 2: Check if in correct venv
import sys
print(sys.executable)  # Should show venv path if activated

# Solution 3: Verify installation
# pip list | grep requests
```
</details>

---

## 💻 CODING CHALLENGES

### Challenge 1: Environment Setup Script

Create a script that sets up a complete Python project environment.

```bash
#!/bin/bash
# Challenge: Complete this script to:
# 1. Create a project directory
# 2. Create virtual environment
# 3. Activate it
# 4. Install common packages
# 5. Create requirements.txt

PROJECT_NAME=$1

# Your code here...

# Solution: (Don't peek until you try!)
```

<details>
<summary>Click for Solution</summary>

```bash
#!/bin/bash
PROJECT_NAME=${1:-"myproject"}

# 1. Create project directory
mkdir -p "$PROJECT_NAME"
cd "$PROJECT_NAME"

# 2. Create virtual environment
python -m venv venv

# 3. Activate it
source venv/bin/activate

# 4. Install common packages
pip install requests beautifulsoup4 colorama rich click

# 5. Create requirements.txt
pip freeze > requirements.txt

# 6. Create basic structure
mkdir -p src tests
touch src/__init__.py
touch src/main.py
touch tests/__init__.py

echo "Project '$PROJECT_NAME' created successfully!"
echo "Run 'source venv/bin/activate' to activate the environment."
```
</details>

### Challenge 2: Requirements Parser

Write a Python script that parses requirements.txt and checks which packages are outdated.

```python
# Challenge: Complete this function
def check_outdated_packages(requirements_file):
    """
    Read requirements.txt and check for outdated packages.
    Return a list of packages that need updates.
    """
    pass

# Test your solution
```

<details>
<summary>Click for Solution</summary>

```python
import subprocess
import re

def check_outdated_packages(requirements_file="requirements.txt"):
    """
    Read requirements.txt and check for outdated packages.
    Return a list of packages that need updates.
    """
    # Read requirements file
    with open(requirements_file, 'r') as f:
        lines = f.readlines()
    
    # Extract package names (remove version specifiers)
    packages = []
    for line in lines:
        line = line.strip()
        if line and not line.startswith('#'):
            # Get package name (before ==, >=, <=, ~=, etc.)
            match = re.match(r'^([a-zA-Z0-9_-]+)', line)
            if match:
                packages.append(match.group(1))
    
    # Get outdated packages
    result = subprocess.run(
        ['pip', 'list', '--outdated', '--format=freeze'],
        capture_output=True, text=True
    )
    
    outdated = []
    for line in result.stdout.strip().split('\n'):
        if line:
            pkg_name = line.split('==')[0]
            if pkg_name in packages:
                outdated.append(line)
    
    return outdated

# Run the check
if __name__ == "__main__":
    outdated = check_outdated_packages()
    if outdated:
        print("Outdated packages:")
        for pkg in outdated:
            print(f"  - {pkg}")
    else:
        print("All packages are up to date!")
```
</details>

### Challenge 3: Virtual Environment Manager

Create a Python script that manages virtual environments.

```python
# Challenge: Implement these functions
class VenvManager:
    def __init__(self):
        pass
    
    def create(self, name):
        """Create a new virtual environment."""
        pass
    
    def list_all(self):
        """List all virtual environments in current directory."""
        pass
    
    def delete(self, name):
        """Delete a virtual environment."""
        pass

# Test your implementation
```

<details>
<summary>Click for Solution</summary>

```python
import os
import subprocess
import shutil

class VenvManager:
    def __init__(self, base_dir="."):
        self.base_dir = os.path.expanduser(base_dir)
    
    def create(self, name):
        """Create a new virtual environment."""
        venv_path = os.path.join(self.base_dir, name)
        if os.path.exists(venv_path):
            return f"Error: Virtual environment '{name}' already exists!"
        
        subprocess.run(['python', '-m', 'venv', venv_path], check=True)
        return f"Created virtual environment: {name}"
    
    def list_all(self):
        """List all virtual environments in current directory."""
        venvs = []
        for item in os.listdir(self.base_dir):
            venv_path = os.path.join(self.base_dir, item)
            activate_script = os.path.join(venv_path, 'bin', 'activate')
            if os.path.isfile(activate_script):
                venvs.append(item)
        return venvs
    
    def delete(self, name):
        """Delete a virtual environment."""
        venv_path = os.path.join(self.base_dir, name)
        if not os.path.exists(venv_path):
            return f"Error: Virtual environment '{name}' not found!"
        
        shutil.rmtree(venv_path)
        return f"Deleted virtual environment: {name}"
    
    def get_activate_command(self, name):
        """Get the activation command for a venv."""
        venv_path = os.path.join(self.base_dir, name)
        if os.path.exists(venv_path):
            return f"source {venv_path}/bin/activate"
        return None

# Example usage
if __name__ == "__main__":
    manager = VenvManager()
    
    # Create a venv
    print(manager.create("test_env"))
    
    # List all venvs
    print("Available venvs:", manager.list_all())
    
    # Get activate command
    print("Activate:", manager.get_activate_command("test_env"))
    
    # Delete venv
    print(manager.delete("test_env"))
```
</details>

---

*Created by T3rmuxk1ng | Termux Full Course*

---

## 🎮 INTERACTIVE QUIZ

### Test Your Python Installation Knowledge!

**Q1: What command installs Python in Termux?**
- A) `apt install python`
- B) `pkg install python`
- C) `pip install python`
- D) `install python`

<details>
<summary>Answer</summary>
**B) pkg install python** - Termux uses `pkg` command which wraps apt for package management.
</details>

---

**Q2: Which Python version should you use in 2024?**
- A) Python 2.7
- B) Python 3.6
- C) Python 3.11+
- D) Any version works

<details>
<summary>Answer</summary>
**C) Python 3.11+** - Python 2 is deprecated (ended 2020), and Python 3.11+ has the best performance and features.
</details>

---

**Q3: What does pip stand for?**
- A) Python Install Program
- B) Pip Installs Packages
- C) Package Installation Program
- D) Python Integrated Platform

<details>
<summary>Answer</summary>
**B) Pip Installs Packages** - It's also known as "Preferred Installer Program"
</details>

---

**Q4: Which command creates a virtual environment?**
- A) `python -m venv myenv`
- B) `pip create venv myenv`
- C) `venv create myenv`
- D) `python venv myenv`

<details>
<summary>Answer</summary>
**A) python -m venv myenv** - The `-m` flag runs the venv module to create a virtual environment.
</details>

---

**Q5: How do you activate a virtual environment in Termux?**
- A) `activate myenv`
- B) `source myenv/bin/activate`
- C) `python activate myenv`
- D) `venv activate myenv`

<details>
<summary>Answer</summary>
**B) source myenv/bin/activate** - On Linux/Termux, you source the activate script from the venv's bin directory.
</details>

---

**Q6: What file stores project dependencies?**
- A) `dependencies.txt`
- B) `packages.txt`
- C) `requirements.txt`
- D) `pip.txt`

<details>
<summary>Answer</summary>
**C) requirements.txt** - This is the standard file for Python project dependencies.
</details>

---

**Q7: Which command installs packages from requirements.txt?**
- A) `pip install requirements.txt`
- B) `pip install -r requirements.txt`
- C) `pip -r requirements.txt`
- D) `python install requirements.txt`

<details>
<summary>Answer</summary>
**B) pip install -r requirements.txt** - The `-r` flag tells pip to read from a requirements file.
</details>

---

**Q8: What's the difference between pip and pkg in Termux?**
- A) No difference
- B) pip is for Python packages, pkg is for system packages
- C) pkg is faster than pip
- D) pip only works with Python 2

<details>
<summary>Answer</summary>
**B) pip is for Python packages, pkg is for system packages** - Use pkg for Termux/system tools, pip for Python libraries.
</details>

---

**Q9: Which command starts Python's interactive shell?**
- A) `python shell`
- B) `python`
- C) `python -i`
- D) Both B and C

<details>
<summary>Answer</summary>
**D) Both B and C** - `python` starts the REPL, and `python -i` starts interactive mode after running a script.
</details>

---

**Q10: How do you check installed Python packages?**
- A) `pip show`
- B) `pip list`
- C) `pip packages`
- D) `python packages`

<details>
<summary>Answer</summary>
**B) pip list** - This shows all installed packages with their versions.
</details>

---

**Q11: What command exports all installed packages to a file?**
- A) `pip export > requirements.txt`
- B) `pip freeze > requirements.txt`
- C) `pip list > requirements.txt`
- D) `pip save > requirements.txt`

<details>
<summary>Answer</summary>
**B) pip freeze > requirements.txt** - `pip freeze` outputs packages in requirements format.
</details>

---

**Q12: Which editor is recommended for beginners in Termux?**
- A) vim
- B) emacs
- C) nano or micro
- D) vscode

<details>
<summary>Answer</summary>
**C) nano or micro** - These are the most beginner-friendly editors available in Termux.
</details>

---

## 💡 PRO TIPS

### 10 Expert Tips for Python in Termux

> **💡 Pro Tip #1: Always Use Virtual Environments**
> Create a venv for every project to avoid dependency conflicts. It takes seconds but saves hours of debugging!
> ```bash
> python -m venv venv && source venv/bin/activate
> ```

> **💡 Pro Tip #2: Upgrade pip First Thing**
> After installing Python, always upgrade pip to avoid issues:
> ```bash
> pip install --upgrade pip setuptools wheel
> ```

> **💡 Pro Tip #3: Use requirements.txt with Versions**
> Pin exact versions for reproducible environments:
> ```bash
> pip freeze | grep -i "package" >> requirements.txt
> ```

> **💡 Pro Tip #4: Quick HTTP Server**
> Need to share files quickly? Python has a built-in server:
> ```bash
> python -m http.server 8000
> ```

> **💡 Pro Tip #5: Use pip check**
> Run `pip check` to find dependency conflicts before they cause problems.

> **💡 Pro Tip #6: Install Build Dependencies**
> Some packages need compilation. Install build tools first:
> ```bash
> pkg install build-essential libffi openssl
> ```

> **💡 Pro Tip #7: Use pip.conf for Mirrors**
> If PyPI is slow, configure a mirror in `~/.config/pip/pip.conf`:
> ```ini
> [global]
> index-url = https://pypi.org/simple
> ```

> **💡 Pro Tip #8: Batch Install Packages**
> Install multiple packages at once to save time:
> ```bash
> pip install requests beautifulsoup4 colorama rich
> ```

> **💡 Pro Tip #9: Use python -c for Quick Tasks**
> Execute one-liners without creating files:
> ```bash
> python -c "import json; print(json.dumps({'key': 'value'}, indent=2))"
> ```

> **💡 Pro Tip #10: Check Package Info Before Installing**
> View package details on PyPI or use:
> ```bash
> pip show package_name
> ```

---

## 🔥 REAL WORLD USE CASES

### Practical Applications of Python in Termux

**Use Case #1: Security Tools Development**
```python
# Quick port scanner for network reconnaissance
import socket
for port in range(1, 1024):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(0.1)
    if sock.connect_ex(('target.com', port)) == 0:
        print(f"Port {port} is open")
    sock.close()
```

**Use Case #2: Automation Scripts**
```python
# Automated file organizer
import os
import shutil

for file in os.listdir('.'):
    if os.path.isfile(file):
        ext = file.split('.')[-1]
        os.makedirs(ext, exist_ok=True)
        shutil.move(file, f'{ext}/{file}')
```

**Use Case #3: API Testing**
```python
# Quick API tester
import requests

def test_endpoint(url):
    try:
        r = requests.get(url, timeout=5)
        print(f"Status: {r.status_code}")
        print(f"Time: {r.elapsed.total_seconds()}s")
    except Exception as e:
        print(f"Error: {e}")

test_endpoint('https://api.github.com')
```

**Use Case #4: Data Processing**
```python
# Log file analyzer
import re
from collections import Counter

def analyze_logs(filename):
    with open(filename) as f:
        ips = re.findall(r'\d+\.\d+\.\d+\.\d+', f.read())
    return Counter(ips).most_common(10)
```

**Use Case #5: Termux Integration**
```python
# Send notification from Python
import subprocess

def notify(title, message):
    subprocess.run([
        'termux-notification',
        '--title', title,
        '--content', message
    ])

notify('Python Script', 'Task completed!')
```

---

## ⚡ QUICK REFERENCE CARD

### Python Installation Commands

| Command | Description |
|---------|-------------|
| `pkg install python` | Install Python 3 |
| `python --version` | Check Python version |
| `which python` | Find Python location |

### pip Commands

| Command | Description |
|---------|-------------|
| `pip install <pkg>` | Install package |
| `pip uninstall <pkg>` | Remove package |
| `pip list` | List packages |
| `pip show <pkg>` | Package info |
| `pip freeze` | Export packages |
| `pip install -r req.txt` | Install from file |
| `pip install --upgrade <pkg>` | Update package |
| `pip check` | Check conflicts |
| `pip cache purge` | Clear cache |

### Virtual Environment Commands

| Command | Description |
|---------|-------------|
| `python -m venv myenv` | Create venv |
| `source myenv/bin/activate` | Activate venv |
| `deactivate` | Exit venv |
| `rm -rf myenv` | Delete venv |

### Python Execution

| Command | Description |
|---------|-------------|
| `python` | Start REPL |
| `python script.py` | Run script |
| `python -c "code"` | One-liner |
| `python -m http.server` | HTTP server |
| `python -m json.tool file` | JSON formatter |

---

## 🏆 BONUS CONTENT

### Advanced Python Setup for Termux

```bash
#!/bin/bash
# complete_python_setup.sh - Complete Python development setup

# Update system
pkg update && pkg upgrade -y

# Install Python with build tools
pkg install python build-essential libffi openssl git -y

# Upgrade pip
pip install --upgrade pip setuptools wheel

# Install essential packages
pip install requests beautifulsoup4 colorama rich httpx

# Install development tools
pip install virtualenv black flake8 pytest

# Create workspace
mkdir -p ~/python-projects
cd ~/python-projects

# Create and activate venv
python -m venv venv
source venv/bin/activate

echo "✅ Python development environment ready!"
```

### pip Aliases for ~/.bashrc

```bash
# Add these to your ~/.bashrc
alias pi='pip install'
alias pu='pip uninstall'
alias pl='pip list'
alias pf='pip freeze'
alias pch='pip check'
alias pout='pip list --outdated'

# Virtual environment helpers
alias venv='python -m venv'
alias activate='source venv/bin/activate'
alias deactivate='deactivate'

# Quick commands
alias py='python'
alias pyc='python -c'
alias pys='python -m http.server'
```

### Python Project Template

```python
#!/usr/bin/env python3
"""
Project: [Project Name]
Author: [Your Name]
Description: [Brief description]
"""

import os
import sys
import argparse
from pathlib import Path

# Version
__version__ = "1.0.0"

def parse_args():
    """Parse command line arguments."""
    parser = argparse.ArgumentParser(description="Project description")
    parser.add_argument("-v", "--version", action="version", version=f"%(prog)s {__version__}")
    parser.add_argument("-q", "--quiet", action="store_true", help="Suppress output")
    parser.add_argument("input", help="Input file or directory")
    return parser.parse_args()

def main():
    """Main function."""
    args = parse_args()
    
    if not args.quiet:
        print(f"Processing: {args.input}")
    
    # Your code here
    
    return 0

if __name__ == "__main__":
    sys.exit(main())
```

---

## 📝 CHAPTER SUMMARY

### Key Takeaways

| Topic | Key Points |
|-------|------------|
| **Installation** | Use `pkg install python` - includes pip automatically |
| **Python 2 vs 3** | Always use Python 3 - Python 2 is deprecated |
| **pip** | Package manager for installing Python libraries |
| **Virtual Environments** | Isolate project dependencies with venv |
| **requirements.txt** | Track and share project dependencies |
| **REPL** | Interactive shell for quick testing |
| **Scripts** | Save code in .py files for reuse |
| **Editors** | nano/micro for beginners, vim/neovim for advanced |

### Must Remember Commands

```bash
# Installation
pkg install python

# Package management
pip install package_name
pip freeze > requirements.txt
pip install -r requirements.txt

# Virtual environments
python -m venv myenv
source myenv/bin/activate
deactivate

# Running Python
python script.py
python -m http.server 8000
```

---

## 🎯 INTERVIEW QUESTIONS

### Common Python Installation Questions

**Q1: What's the difference between pip and conda?**

<details>
<summary>Answer</summary>
- **pip**: Python's default package manager, installs from PyPI
- **conda**: Cross-platform package manager, handles non-Python dependencies
- In Termux, pip is the standard choice as conda requires Anaconda/Miniconda
</details>

**Q2: Why use virtual environments?**

<details>
<summary>Answer</summary>
1. **Dependency isolation** - Different projects can use different package versions
2. **Clean environment** - No conflicts between projects
3. **Reproducibility** - Easy to share exact dependencies
4. **System protection** - Can't break system Python
</details>

**Q3: How would you handle a package that fails to install?**

<details>
<summary>Answer</summary>
1. Check error message for missing dependencies
2. Install build tools: `pkg install build-essential libffi openssl`
3. Try pre-compiled version from pkg: `pkg install python-package`
4. Check if package supports ARM/Termux architecture
5. Look for alternatives or compile from source
</details>

**Q4: Explain the difference between `pip install` and `pip install --user`.**

<details>
<summary>Answer</summary>
- `pip install`: Installs to system/site-packages (requires venv or root in some systems)
- `pip install --user`: Installs to user's home directory (~/.local/)
- In Termux, both work similarly since you have full control
</details>

**Q5: How do you update all installed packages?**

<details>
<summary>Answer</summary>
```bash
# Method 1: Using pip-review (install first)
pip install pip-review
pip-review --auto

# Method 2: Manual
pip list --outdated --format=freeze | grep -v "^\-e" | cut -d = -f 1 | xargs -n1 pip install -U

# Method 3: Simple one-by-one
pip list --outdated
pip install --upgrade package_name
```
</details>

**Q6: What is the purpose of setup.py?**

<details>
<summary>Answer</summary>
- `setup.py` is used to define package metadata and installation configuration
- It's being replaced by `pyproject.toml` in modern Python packaging
- Used for: package name, version, dependencies, entry points
- Allows `pip install -e .` for development mode
</details>

**Q7: How would you install a package from GitHub?**

<details>
<summary>Answer</summary>
```bash
# Direct from git
pip install git+https://github.com/user/repo.git

# Specific branch
pip install git+https://github.com/user/repo.git@branch

# Specific tag
pip install git+https://github.com/user/repo.git@v1.0.0

# Editable/development mode
pip install -e git+https://github.com/user/repo.git#egg=package_name
```
</details>

**Q8: What's the difference between venv and virtualenv?**

<details>
<summary>Answer</summary>
- **venv**: Built into Python 3.3+, lighter weight, recommended
- **virtualenv**: External package, supports Python 2, faster creation
- Both create isolated environments
- In Termux, venv is preferred (no extra installation needed)
</details>

**Q9: How do you check which Python packages have security vulnerabilities?**

<details>
<summary>Answer</summary>
```bash
# Using pip-audit (recommended)
pip install pip-audit
pip-audit

# Using safety
pip install safety
safety check

# Basic check
pip check  # Only checks for dependency conflicts
```
</details>

**Q10: Explain the Python search path for modules.**

<details>
<summary>Answer</summary>
Python searches for modules in this order:
1. Current directory
2. PYTHONPATH environment variable
3. Standard library directories
4. site-packages directory
5. .pth files in site-packages

View with: `python -c "import sys; print('\n'.join(sys.path))"`
</details>

---

## 🚀 BEST PRACTICES

### Code Style & Project Structure

```
my_project/
├── venv/                    # Virtual environment (gitignored)
├── src/                     # Source code
│   ├── __init__.py
│   └── main.py
├── tests/                   # Test files
│   └── test_main.py
├── docs/                    # Documentation
├── .gitignore              # Git ignore file
├── requirements.txt        # Dependencies
├── setup.py               # Package setup
└── README.md              # Project info
```

### .gitignore for Python

```gitignore
# Byte-compiled files
__pycache__/
*.py[cod]
*$py.class

# Virtual environments
venv/
env/
.venv/

# IDE
.vscode/
.idea/

# Distribution
dist/
build/
*.egg-info/

# Testing
.pytest_cache/
.coverage

# Environment
.env
.env.local
```

### Common Mistakes to Avoid

| ❌ Mistake | ✅ Solution |
|-----------|------------|
| Installing globally | Always use virtual environments |
| Not pinning versions | Use `package==1.2.3` in requirements |
| Ignoring dependency conflicts | Run `pip check` regularly |
| Using Python 2 | Always use Python 3 |
| Not upgrading pip | `pip install --upgrade pip` first |
| Committing venv | Add to .gitignore |

---

## 📊 CODE COMPARISON

### Bad vs Good: Virtual Environment Usage

```python
# ❌ BAD: Installing globally, no isolation
pip install requests flask django
pip install requests==2.25.0  # Conflict!

# ✅ GOOD: Using virtual environment
python -m venv myproject-env
source myproject-env/bin/activate
pip install requests flask django
pip freeze > requirements.txt
```

### Bad vs Good: Requirements Management

```python
# ❌ BAD: No requirements tracking
# Team members don't know what to install
# "Works on my machine" syndrome

# ✅ GOOD: Proper requirements.txt
requests==2.31.0
beautifulsoup4==4.12.2
colorama==0.4.6

# Install with:
pip install -r requirements.txt
```

### Bad vs Good: Package Installation

```python
# ❌ BAD: Using wrong package manager
pkg install python-requests  # May not exist or outdated

# ✅ GOOD: Using pip for Python packages
pip install requests  # Direct from PyPI, always latest
```

---

## 🔗 RELATED CHAPTERS

### Prerequisites
- **Chapter 1**: Termux Installation & Setup
- **Chapter 2**: Basic Termux Commands
- **Chapter 5**: Package Management (pkg)

### Next Steps
- **Chapter 12**: Python Basics in Termux ← Continue learning Python
- **Chapter 17**: Termux API with Python
- **Chapter 22**: Automation Scripts with Python

### Advanced Topics
- **Chapter 25**: Web Scraping with Python
- **Chapter 30**: Security Tools Development
- **Chapter 35**: Machine Learning in Termux

### Related Programming
- **Chapter 13**: Bash Scripting Basics
- **Chapter 16**: Node.js in Termux
- **Chapter 19**: Git Version Control

---

*Updated by T3rmuxk1ng | Termux Full Course - Module 3: Programming*
