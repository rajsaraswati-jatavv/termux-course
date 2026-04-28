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

*Created by T3rmuxk1ng | Termux Full Course*
