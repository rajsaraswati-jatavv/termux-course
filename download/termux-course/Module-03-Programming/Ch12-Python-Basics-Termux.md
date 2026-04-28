# Chapter 12: Python Basics in Termux

> **Module:** 3 - Programming  
> **Chapter:** 12 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Beginner-Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Python basics crash course |
| Code Examples | 20+ practical Python examples |
| Commands Reference | Python commands and pip usage |
| Practice Exercises | 5 Python programs |
| Troubleshooting | Common Python errors in Termux |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 12
Title: Python Basics in Termux | Complete Beginner Guide | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Previous chapter mein humne Python install kiya tha aur setup kiya tha.
Aaj ke chapter mein hum Python programming seekhenge - from scratch!

Python ek bahut powerful language hai. Agar aap ethical hacking, 
automation, data science, ya web development mein interested ho - 
Python sabse important language hai.

Best part? Python seekhna bahut easy hai! Syntax simple hai, 
readable hai, aur Termux mein perfectly kaam karta hai.

To chaliye shuru karte hain - Python Basics in Termux!

Play button dabaiye, video like karein, aur channel subscribe karein.

---

[SECTION 1: PYTHON INTERACTIVE SHELL - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle Python ka interactive shell dekhte hain.

Termux mein type karein:

    python

Ye command aapko Python interactive shell mein le jaayega.
Aapko prompt milega: >>>

Ye Python ka REPL hai - Read, Eval, Print, Loop.

Yahan aap directly Python code likh sakte ho aur output 
immediately dekh sakte ho.

Chaliye pehla command run karein:

    >>> print("Hello Termux!")
    Hello Termux!

Dekha? Simple aur clear!

Math operations bhi kar sakte ho:

    >>> 5 + 5
    10
    >>> 10 * 5
    50
    >>> 100 / 4
    25.0
    >>> 2 ** 10
    1024

Exit karne ke liye:

    >>> exit()
    
Ya phir Ctrl+D press karein.

Interactive shell testing ke liye perfect hai, lekin actual 
programs ke liye script files banani padti hain.

---

[SECTION 2: VARIABLES & DATA TYPES - 4:00 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Ab variables seekhte hain. Variables containers hain - data 
store karne ke liye.

Python mein variable banana super easy hai - koi declaration 
ki zarurat nahi!

    name = "T3rmuxk1ng"      # String
    age = 25                  # Integer
    height = 5.9              # Float
    is_hacker = True          # Boolean

Dekha? Direct assign karo, kaam ho gaya!

Data types check karne ke liye type() function use karo:

    type(name)        # <class 'str'>
    type(age)         # <class 'int'>
    type(height)      # <class 'float'>
    type(is_hacker)   # <class 'bool'>

Variable naming rules yaad rakho:

✓ Letters, numbers, underscores use kar sakte ho
✓ Number se start nahi kar sakte
✓ Spaces nahi, underscores use karo
✓ Case-sensitive hai (name aur Name alag hain)

Examples:

    # Valid names
    user_name = "hacker"
    userName = "hacker"
    user1 = "hacker"
    _private = "secret"

    # Invalid names (error dega)
    # 1user = "hacker"      # Number se start
    # user-name = "hacker"  # Hyphen allowed nahi
    # user name = "hacker"  # Space allowed nahi

Multiple variables ek saath assign kar sakte ho:

    a, b, c = 1, 2, 3
    print(a, b, c)  # 1 2 3

Same value multiple variables ko:

    x = y = z = 0
    print(x, y, z)  # 0 0 0

---

[SECTION 3: STRINGS & STRING METHODS - 8:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Strings ek important data type hai. Text data represent karte hain.

Single quotes ya double quotes - dono kaam karti hain:

    name1 = 'Termux'
    name2 = "Termux"

Multi-line strings ke liye triple quotes:

    message = """
    Ye ek
    multi-line
    string hai
    """

String concatenation:

    first = "Term"
    last = "ux"
    full = first + last
    print(full)  # Termux

String repetition:

    print("Ha" * 3)  # HaHaHa

String indexing - zero se start hota hai:

    text = "PYTHON"
    print(text[0])   # P
    print(text[1])   # Y
    print(text[-1])  # N (last character)
    print(text[-2])  # O (second last)

String slicing:

    text = "PYTHON"
    print(text[0:3])   # PYT
    print(text[2:])    # THON
    print(text[:4])    # PYTH
    print(text[::2])   # PTO (every 2nd char)
    print(text[::-1])  # NOHTYP (reversed!)

String methods - bahut useful hain:

    name = "t3rmuxk1ng"

    # Uppercase/Lowercase
    print(name.upper())        # T3RMUXK1NG
    print(name.lower())        # t3rmuxk1ng
    print(name.capitalize())   # T3rmuxk1ng
    print(name.title())        # T3Rmuxk1Ng

    # Find and count
    print(name.count('x'))     # 1
    print(name.find('x'))      # 5
    print(name.index('k'))     # 7

    # Replace
    print(name.replace('x', 'X'))  # t3rmuXk1ng

    # Strip whitespace
    text = "  hello  "
    print(text.strip())        # "hello"
    print(text.lstrip())       # "hello  "
    print(text.rstrip())       # "  hello"

    # Split and Join
    sentence = "Python is awesome"
    words = sentence.split()   # ['Python', 'is', 'awesome']
    joined = "-".join(words)   # Python-is-awesome

    # Check methods
    print("hello".isalpha())   # True
    print("123".isdigit())     # True
    print("hello123".isalnum()) # True
    print("hello".startswith("he"))  # True
    print("hello".endswith("lo"))    # True

String length:

    print(len("Termux"))  # 6

f-strings - modern formatting (Python 3.6+):

    name = "T3rmuxk1ng"
    subs = 10000
    print(f"Channel: {name}, Subscribers: {subs}")
    # Channel: T3rmuxk1ng, Subscribers: 10000

---

[SECTION 4: NUMBERS & MATH OPERATIONS - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Numbers se related operations dekhte hain.

Python mein 3 number types hain:

    # Integer (whole numbers)
    a = 10
    b = -5

    # Float (decimal numbers)
    c = 3.14
    d = -0.001

    # Complex numbers
    e = 3 + 4j

Basic arithmetic:

    print(10 + 5)    # 15 (Addition)
    print(10 - 5)    # 5  (Subtraction)
    print(10 * 5)    # 50 (Multiplication)
    print(10 / 5)    # 2.0 (Division - always float)
    print(10 // 5)   # 2  (Floor division - integer)
    print(10 % 3)    # 1  (Modulus - remainder)
    print(2 ** 10)   # 1024 (Exponent/Power)

Math functions:

    import math

    print(abs(-5))         # 5 (absolute value)
    print(round(3.7))      # 4 (rounding)
    print(round(3.14159, 2))  # 3.14

    print(math.ceil(3.1))   # 4 (ceiling)
    print(math.floor(3.9))  # 3 (floor)

    print(math.sqrt(16))    # 4.0 (square root)
    print(math.pow(2, 10))  # 1024.0 (power)

    print(math.pi)          # 3.141592653589793
    print(math.e)           # 2.718281828459045

    print(math.sin(0))      # 0.0
    print(math.cos(0))      # 1.0

Type conversion:

    # String to number
    num_str = "123"
    num_int = int(num_str)      # 123
    num_float = float(num_str)  # 123.0

    # Number to string
    num = 456
    num_str = str(num)          # "456"

    # Float to int (truncates)
    pi = 3.14159
    int_pi = int(pi)            # 3

---

[SECTION 5: LISTS, TUPLES & DICTIONARIES - 15:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Ab data structures seekhte hain - ye bahut important hain!

=== LISTS ===

List ek ordered collection hai, mutable (changeable).

    # Creating lists
    tools = ["nmap", "hydra", "metasploit"]
    numbers = [1, 2, 3, 4, 5]
    mixed = [1, "hello", 3.14, True]

    # Accessing elements
    print(tools[0])    # nmap
    print(tools[-1])   # metasploit (last)
    print(tools[1:3])  # ['hydra', 'metasploit']

    # Modifying list
    tools[0] = "nmap_updated"
    tools.append("sqlmap")        # Add at end
    tools.insert(1, "burpsuite")  # Insert at index
    tools.remove("hydra")         # Remove by value
    tools.pop()                   # Remove last
    tools.pop(0)                  # Remove by index

    # List operations
    print(len(tools))             # Length
    print("nmap" in tools)        # Check membership
    tools.sort()                  # Sort in place
    tools.reverse()               # Reverse in place
    tools_copy = tools.copy()     # Copy list
    tools.clear()                 # Clear all elements

    # List comprehension (powerful!)
    squares = [x**2 for x in range(10)]
    # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

    evens = [x for x in range(20) if x % 2 == 0]
    # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

=== TUPLES ===

Tuple bhi ordered collection hai, lekin immutable (cannot change).

    # Creating tuples
    coords = (10, 20)
    colors = ("red", "green", "blue")
    single = (1,)  # Single element tuple (comma required!)

    # Accessing (same as list)
    print(coords[0])    # 10
    print(coords[-1])   # 20

    # Tuple unpacking
    x, y = coords
    print(x, y)  # 10 20

    # Cannot modify! This will error:
    # coords[0] = 5  # TypeError

    # Useful tuple methods
    print(colors.count("red"))  # Count occurrences
    print(colors.index("green"))  # Find index

=== DICTIONARIES ===

Dictionary key-value pairs store karti hai. Very useful!

    # Creating dictionary
    hacker = {
        "name": "T3rmuxk1ng",
        "age": 25,
        "skills": ["Python", "Bash", "Linux"],
        "active": True
    }

    # Accessing values
    print(hacker["name"])           # T3rmuxk1ng
    print(hacker.get("age"))        # 25
    print(hacker.get("country", "Unknown"))  # Default value

    # Adding/Modifying
    hacker["country"] = "India"     # Add new
    hacker["age"] = 26              # Modify existing

    # Removing
    del hacker["active"]            # Delete key
    value = hacker.pop("age")       # Remove and return
    hacker.clear()                  # Clear all

    # Dictionary methods
    print(hacker.keys())            # All keys
    print(hacker.values())          # All values
    print(hacker.items())           # Key-value pairs

    # Iterating
    for key in hacker:
        print(key, hacker[key])

    for key, value in hacker.items():
        print(f"{key}: {value}")

    # Nested dictionaries
    users = {
        "user1": {"name": "Alice", "age": 25},
        "user2": {"name": "Bob", "age": 30}
    }
    print(users["user1"]["name"])  # Alice

=== SETS ===

Set unique values store karta hai, unordered.

    # Creating sets
    tools = {"nmap", "hydra", "nmap"}  # Duplicates removed
    print(tools)  # {'hydra', 'nmap'}

    # Set operations
    a = {1, 2, 3, 4}
    b = {3, 4, 5, 6}

    print(a | b)  # Union: {1, 2, 3, 4, 5, 6}
    print(a & b)  # Intersection: {3, 4}
    print(a - b)  # Difference: {1, 2}
    print(a ^ b)  # Symmetric diff: {1, 2, 5, 6}

    # Set methods
    tools.add("sqlmap")
    tools.remove("nmap")
    tools.discard("burp")  # No error if not found

---

[SECTION 6: CONTROL FLOW - if, elif, else - 20:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Ab decision making seekhte hain - control flow statements.

=== IF-ELIF-ELSE ===

    # Basic if statement
    age = 18

    if age >= 18:
        print("You are an adult!")

    # If-else
    age = 15

    if age >= 18:
        print("Adult")
    else:
        print("Minor")

    # If-elif-else chain
    score = 85

    if score >= 90:
        grade = "A"
    elif score >= 80:
        grade = "B"
    elif score >= 70:
        grade = "C"
    elif score >= 60:
        grade = "D"
    else:
        grade = "F"

    print(f"Your grade: {grade}")

    # Nested if
    age = 25
    has_license = True

    if age >= 18:
        if has_license:
            print("You can drive!")
        else:
            print("Get a license first!")
    else:
        print("Too young to drive!")

    # Logical operators
    username = "admin"
    password = "secret123"

    if username == "admin" and password == "secret123":
        print("Login successful!")
    else:
        print("Invalid credentials!")

    # Multiple conditions with or
    day = "Saturday"

    if day == "Saturday" or day == "Sunday":
        print("It's weekend!")

    # Not operator
    logged_in = False

    if not logged_in:
        print("Please log in!")

    # Ternary operator (one-liner)
    age = 20
    status = "Adult" if age >= 18 else "Minor"
    print(status)

    # Checking empty values
    name = ""
    if not name:
        print("Name is empty!")

    items = []
    if not items:
        print("List is empty!")

=== COMPARISON OPERATORS ===

    # == Equal
    # != Not equal
    # > Greater than
    # < Less than
    # >= Greater than or equal
    # <= Less than or equal

    # is vs ==
    a = [1, 2, 3]
    b = [1, 2, 3]
    c = a

    print(a == b)  # True (same values)
    print(a is b)  # False (different objects)
    print(a is c)  # True (same object)

    # in operator
    tools = ["nmap", "hydra", "sqlmap"]
    if "nmap" in tools:
        print("Nmap is available!")

---

[SECTION 7: LOOPS - for and while - 24:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

Loops repetition ke kaam aate hain. Bahut important!

=== FOR LOOP ===

    # Iterating over list
    tools = ["nmap", "hydra", "sqlmap"]
    for tool in tools:
        print(f"Tool: {tool}")

    # Using range
    for i in range(5):
        print(i)  # 0, 1, 2, 3, 4

    for i in range(2, 10):
        print(i)  # 2 to 9

    for i in range(0, 20, 2):
        print(i)  # 0, 2, 4, 6, 8... (step of 2)

    # Enumerate (index + value)
    tools = ["nmap", "hydra", "sqlmap"]
    for index, tool in enumerate(tools):
        print(f"{index}: {tool}")

    # Dictionary iteration
    hacker = {"name": "T3rmuxk1ng", "skill": "Python"}
    for key, value in hacker.items():
        print(f"{key}: {value}")

    # Nested loops
    for i in range(3):
        for j in range(3):
            print(f"({i}, {j})")

    # Loop with else
    for i in range(5):
        print(i)
    else:
        print("Loop completed!")

=== WHILE LOOP ===

    # Basic while loop
    count = 0
    while count < 5:
        print(count)
        count += 1

    # While with condition
    password = ""
    while password != "secret":
        password = input("Enter password: ")
    print("Access granted!")

    # Infinite loop (with break)
    while True:
        response = input("Continue? (y/n): ")
        if response == "n":
            break

=== LOOP CONTROL ===

    # break - exit loop completely
    for i in range(10):
        if i == 5:
            break
        print(i)  # 0, 1, 2, 3, 4

    # continue - skip current iteration
    for i in range(10):
        if i % 2 == 0:
            continue
        print(i)  # 1, 3, 5, 7, 9 (odd numbers)

    # pass - do nothing (placeholder)
    for i in range(5):
        if i == 3:
            pass  # TODO: implement later
        print(i)

---

[SECTION 8: FUNCTIONS - 28:00 to 32:00]
─────────────────────────────────────────────────────────────────────────────

Functions reusable code blocks hain. Ek baar likho, baar baar use karo!

    # Basic function
    def greet():
        print("Hello, Hacker!")

    greet()  # Call the function

    # Function with parameters
    def greet(name):
        print(f"Hello, {name}!")

    greet("T3rmuxk1ng")

    # Function with return value
    def add(a, b):
        return a + b

    result = add(5, 3)
    print(result)  # 8

    # Multiple return values
    def get_info():
        name = "T3rmuxk1ng"
        age = 25
        return name, age

    n, a = get_info()
    print(n, a)

    # Default parameters
    def greet(name="Hacker"):
        print(f"Hello, {name}!")

    greet()         # Hello, Hacker!
    greet("Admin")  # Hello, Admin!

    # Keyword arguments
    def profile(name, age, country):
        print(f"{name}, {age}, {country}")

    profile(age=25, country="India", name="T3rmuxk1ng")

    # *args - variable positional arguments
    def add_all(*numbers):
        return sum(numbers)

    print(add_all(1, 2, 3, 4, 5))  # 15

    # **kwargs - variable keyword arguments
    def show_info(**kwargs):
        for key, value in kwargs.items():
            print(f"{key}: {value}")

    show_info(name="T3rmuxk1ng", age=25, skill="Hacking")

    # Lambda functions (anonymous)
    square = lambda x: x ** 2
    print(square(5))  # 25

    add = lambda a, b: a + b
    print(add(3, 5))  # 8

    # Lambda with built-in functions
    numbers = [1, 2, 3, 4, 5]
    squared = list(map(lambda x: x**2, numbers))
    print(squared)  # [1, 4, 9, 16, 25]

    evens = list(filter(lambda x: x % 2 == 0, numbers))
    print(evens)  # [2, 4]

    # Docstrings
    def calculate_area(radius):
        """
        Calculate area of a circle.
        
        Args:
            radius: Radius of the circle
        
        Returns:
            Area of the circle
        """
        return 3.14159 * radius ** 2

    help(calculate_area)  # Shows docstring

---

[SECTION 9: FILE HANDLING - 32:00 to 36:00]
─────────────────────────────────────────────────────────────────────────────

Files se data read/write karna bahut important hai!

    # Writing to file
    with open("test.txt", "w") as f:
        f.write("Hello Termux!\n")
        f.write("Python is awesome!\n")

    # Reading from file
    with open("test.txt", "r") as f:
        content = f.read()
        print(content)

    # Reading line by line
    with open("test.txt", "r") as f:
        for line in f:
            print(line.strip())

    # Reading all lines into list
    with open("test.txt", "r") as f:
        lines = f.readlines()
        print(lines)

    # Appending to file
    with open("test.txt", "a") as f:
        f.write("New line added!\n")

    # File modes:
    # "r" - Read (default)
    # "w" - Write (overwrites)
    # "a" - Append
    # "x" - Create (error if exists)
    # "r+" - Read and Write
    # "b" - Binary mode (e.g., "rb", "wb")

    # Check if file exists
    import os
    if os.path.exists("test.txt"):
        print("File exists!")

    # Get file info
    print(os.path.getsize("test.txt"))  # Size in bytes

    # Delete file
    # os.remove("test.txt")

    # Working with JSON
    import json

    data = {
        "name": "T3rmuxk1ng",
        "skills": ["Python", "Bash"],
        "active": True
    }

    # Write JSON
    with open("data.json", "w") as f:
        json.dump(data, f, indent=4)

    # Read JSON
    with open("data.json", "r") as f:
        loaded = json.load(f)
        print(loaded)

---

[SECTION 10: MODULES & IMPORTS - 36:00 to 39:00]
─────────────────────────────────────────────────────────────────────────────

Python ki real power modules mein hai - pre-written code jo aap use kar sakte ho!

    # Import entire module
    import os
    print(os.getcwd())

    # Import with alias
    import os as operating_system
    print(operating_system.getcwd())

    # Import specific function
    from os import getcwd, mkdir
    print(getcwd())

    # Import all (not recommended)
    from os import *

    # Standard library modules
    import os           # Operating system interface
    import sys          # System-specific parameters
    import math         # Mathematical functions
    import random       # Random number generation
    import datetime     # Date and time
    import json         # JSON handling
    import re           # Regular expressions
    import subprocess   # Run shell commands
    import time         # Time functions

    # Examples:
    import random
    print(random.randint(1, 100))  # Random number 1-100
    print(random.choice(["a", "b", "c"]))  # Random choice

    import datetime
    now = datetime.datetime.now()
    print(now)
    print(now.strftime("%Y-%m-%d %H:%M:%S"))

    import time
    print("Waiting...")
    time.sleep(2)  # Wait 2 seconds
    print("Done!")

    # Install external modules with pip
    # pip install requests
    # pip install beautifulsoup4

    # Then import
    # import requests
    # response = requests.get("https://api.ipify.org")
    # print(response.text)

---

[SECTION 11: TERMUX-SPECIFIC PYTHON - 39:00 to 43:00]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain Termux-specific features!

=== SUBPROCESS MODULE ===

Shell commands Python se run karne ke liye:

    import subprocess

    # Run a command
    result = subprocess.run(["ls", "-la"], capture_output=True, text=True)
    print(result.stdout)

    # Run with shell=True
    result = subprocess.run("ls -la | grep py", shell=True, capture_output=True, text=True)
    print(result.stdout)

    # Get return code
    result = subprocess.run(["ping", "-c", "1", "google.com"])
    if result.returncode == 0:
        print("Ping successful!")

    # Run command in background
    process = subprocess.Popen(["python", "server.py"])
    # process.kill()  # To stop

=== OS MODULE ===

    import os

    # Current directory
    print(os.getcwd())

    # Change directory
    os.chdir("/sdcard")
    print(os.getcwd())

    # List directory
    print(os.listdir("."))

    # Create directory
    os.mkdir("test_dir")

    # Create nested directories
    os.makedirs("path/to/dir", exist_ok=True)

    # Remove directory
    os.rmdir("test_dir")

    # Remove file
    os.remove("test.txt")

    # Rename file
    os.rename("old.txt", "new.txt")

    # Environment variables
    print(os.environ.get("HOME"))
    print(os.environ.get("PREFIX"))

    # Path operations
    path = "/sdcard/Download/file.txt"
    print(os.path.dirname(path))   # /sdcard/Download
    print(os.path.basename(path))  # file.txt
    print(os.path.splitext(path))  # ('/sdcard/Download/file', '.txt')

=== SYS MODULE ===

    import sys

    # Python version
    print(sys.version)

    # Platform
    print(sys.platform)

    # Command line arguments
    print(sys.argv)  # List of arguments

    # Exit program
    # sys.exit(0)

    # Path (module search paths)
    print(sys.path)

=== TERMUX API WITH PYTHON ===

    import subprocess
    import json

    # Get device info
    def get_device_info():
        result = subprocess.run(["termux-telephony-deviceinfo"], 
                                capture_output=True, text=True)
        return json.loads(result.stdout)

    # Get battery status
    def get_battery():
        result = subprocess.run(["termux-battery-status"], 
                                capture_output=True, text=True)
        return json.loads(result.stdout)

    # Send SMS
    def send_sms(number, message):
        subprocess.run(["termux-sms-send", "-n", number, message])

    # Take photo
    def take_photo(output_path):
        subprocess.run(["termux-camera-photo", output_path])

    # Text to speech
    def speak(text):
        subprocess.run(["termux-tts-speak", text])

    # Vibrate
    def vibrate(duration=1000):
        subprocess.run(["termux-vibrate", "-d", str(duration)])

    # Get location
    def get_location():
        result = subprocess.run(["termux-location"], 
                                capture_output=True, text=True)
        return json.loads(result.stdout)

    # Example usage
    # battery = get_battery()
    # print(f"Battery: {battery['percentage']}%")

---

[SECTION 12: CREATING PYTHON SCRIPTS - 43:00 to 46:00]
─────────────────────────────────────────────────────────────────────────────

Ab real scripts banate hain!

    # Create script file
    nano myscript.py

Script structure:

    #!/usr/bin/env python3
    """
    Script Name: My First Python Script
    Author: T3rmuxk1ng
    Description: A sample Python script
    """

    import os
    import sys

    def main():
        print("Hello from Python script!")
        print(f"Python version: {sys.version}")
        print(f"Current directory: {os.getcwd()}")

    if __name__ == "__main__":
        main()

Shebang line important hai:
    #!/usr/bin/env python3

Ye batata hai ki script Python se run hogi.

Make executable:
    chmod +x myscript.py

Run directly:
    ./myscript.py

Ya normally:
    python myscript.py

Command line arguments:

    #!/usr/bin/env python3
    import sys

    if len(sys.argv) < 2:
        print("Usage: python script.py <name>")
        sys.exit(1)

    name = sys.argv[1]
    print(f"Hello, {name}!")

Better way with argparse:

    #!/usr/bin/env python3
    import argparse

    parser = argparse.ArgumentParser(description="My Script")
    parser.add_argument("name", help="Your name")
    parser.add_argument("-a", "--age", type=int, help="Your age")
    parser.add_argument("-v", "--verbose", action="store_true")

    args = parser.parse_args()

    if args.verbose:
        print(f"Name: {args.name}")
        if args.age:
            print(f"Age: {args.age}")

---

[SECTION 13: SUMMARY & NEXT PREVIEW - 46:00 to 48:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 12 complete! Let's summarize:

✅ Python interactive shell
✅ Variables and data types
✅ Strings and string methods
✅ Numbers and math operations
✅ Lists, tuples, dictionaries
✅ Control flow - if, elif, else
✅ Loops - for and while
✅ Functions
✅ File handling
✅ Modules and imports
✅ Termux-specific Python usage
✅ subprocess, os, sys modules
✅ Creating Python scripts

Important commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    PYTHON IMPORTANT COMMANDS                             │
├─────────────────────────────────────────────────────────────────────────┤
│ python                 │ Start interactive shell                         │
│ python script.py       │ Run Python script                               │
│ ./script.py            │ Run executable script (with shebang)            │
│ pip install package    │ Install Python package                          │
│ pip list               │ List installed packages                         │
│ pip freeze             │ List packages for requirements                  │
│ python -m pip install  │ Install using Python module                     │
│ chmod +x script.py     │ Make script executable                          │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 13 mein hum Bash Scripting Basics seekhenge:
- Bash scripting introduction
- Variables and input
- Conditional statements
- Loops in Bash
- Functions in Bash
- Real-world scripts

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 13!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Python Basics Quick Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PYTHON DATA TYPES OVERVIEW                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   MUTABLE (Can Change)           │   IMMUTABLE (Cannot Change)          │
│   ─────────────────────          │   ──────────────────────────         │
│   • list    - [1, 2, 3]          │   • int     - 42                    │
│   • dict    - {"a": 1}           │   • float   - 3.14                  │
│   • set     - {1, 2, 3}          │   • str     - "hello"               │
│                                  │   • tuple   - (1, 2, 3)             │
│                                  │   • bool    - True/False            │
│                                  │   • None    - None                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Python Operators Reference

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `5 - 3` | `2` |
| `*` | Multiplication | `5 * 3` | `15` |
| `/` | Division | `7 / 2` | `3.5` |
| `//` | Floor Division | `7 // 2` | `3` |
| `%` | Modulus | `7 % 3` | `1` |
| `**` | Exponent | `2 ** 3` | `8` |
| `==` | Equal | `5 == 5` | `True` |
| `!=` | Not Equal | `5 != 3` | `True` |
| `>` | Greater Than | `5 > 3` | `True` |
| `<` | Less Than | `5 < 3` | `False` |
| `>=` | Greater or Equal | `5 >= 5` | `True` |
| `<=` | Less or Equal | `3 <= 5` | `True` |
| `and` | Logical AND | `True and False` | `False` |
| `or` | Logical OR | `True or False` | `True` |
| `not` | Logical NOT | `not True` | `False` |
| `in` | Membership | `'a' in 'abc'` | `True` |
| `is` | Identity | `a is a` | `True` |

### 3. String Formatting Methods

```python
# Method 1: f-strings (Python 3.6+) - RECOMMENDED
name = "T3rmuxk1ng"
age = 25
print(f"Name: {name}, Age: {age}")

# Method 2: format() method
print("Name: {}, Age: {}".format(name, age))
print("Name: {0}, Age: {1}".format(name, age))
print("Name: {n}, Age: {a}".format(n=name, a=age))

# Method 3: %-formatting (old style)
print("Name: %s, Age: %d" % (name, age))

# f-string formatting options
pi = 3.14159
print(f"Pi: {pi:.2f}")      # Pi: 3.14 (2 decimal places)
print(f"Pi: {pi:.4f}")      # Pi: 3.1416 (4 decimal places)
print(f"Number: {42:05d}")  # Number: 00042 (pad with zeros)
print(f"Number: {42:>5d}")  # Number:    42 (right align)
print(f"Number: {42:<5d}")  # Number: 42    (left align)
print(f"Number: {42:^5d}")  # Number:  42   (center align)
```

### 4. List Methods Reference

```python
# Creation
lst = [1, 2, 3]
lst = list(range(5))           # [0, 1, 2, 3, 4]
lst = [0] * 5                  # [0, 0, 0, 0, 0]

# Adding elements
lst.append(4)                  # Add to end: [1, 2, 3, 4]
lst.insert(0, 0)               # Insert at index: [0, 1, 2, 3, 4]
lst.extend([5, 6])             # Add multiple: [0, 1, 2, 3, 4, 5, 6]

# Removing elements
lst.remove(0)                  # Remove by value
lst.pop()                      # Remove and return last
lst.pop(0)                     # Remove and return by index
lst.clear()                    # Remove all elements

# Finding elements
lst.index(3)                   # Index of value
lst.count(3)                   # Count occurrences
3 in lst                       # Check membership (returns bool)

# Ordering
lst.sort()                     # Sort in place (ascending)
lst.sort(reverse=True)         # Sort descending
lst.reverse()                  # Reverse in place
sorted(lst)                    # Return new sorted list

# Copying
new_lst = lst.copy()           # Shallow copy
new_lst = lst[:]               # Slice copy
import copy; new_lst = copy.deepcopy(lst)  # Deep copy

# Other operations
len(lst)                       # Length
min(lst)                       # Minimum value
max(lst)                       # Maximum value
sum(lst)                       # Sum of elements
```

### 5. Dictionary Methods Reference

```python
# Creation
d = {"a": 1, "b": 2}
d = dict(a=1, b=2)
d = dict([("a", 1), ("b", 2)])

# Accessing
d["a"]                         # Get value (raises KeyError if not found)
d.get("a")                     # Get value (returns None if not found)
d.get("a", 0)                  # Get value with default

# Adding/Updating
d["c"] = 3                     # Add or update
d.update({"d": 4, "e": 5})     # Add multiple
d.setdefault("f", 6)           # Add if not exists

# Removing
del d["a"]                     # Delete key
d.pop("b")                     # Remove and return value
d.pop("b", None)               # Remove with default (no error)
d.popitem()                    # Remove and return last item
d.clear()                      # Remove all

# Iteration
d.keys()                       # View of keys
d.values()                     # View of values
d.items()                      # View of (key, value) pairs

# Copying
new_d = d.copy()               # Shallow copy

# Other
"a" in d                       # Check key existence
len(d)                         # Number of items
```

---

## 💻 CODE EXAMPLES (20+ Examples)

### Example 1: Hello World

```python
#!/usr/bin/env python3
# ex01_hello.py - Basic Hello World

print("Hello, Termux!")
print("Python is awesome!")

# Multiple print statements
print("Line 1", "Line 2", "Line 3", sep="\n")

# Print with different end character
print("Loading", end="...")
print("Done!")
```

### Example 2: Variables and Types

```python
#!/usr/bin/env python3
# ex02_variables.py - Variables and data types

# String
name = "T3rmuxk1ng"
channel = 'Termux Course'

# Numbers
age = 25
pi = 3.14159
complex_num = 3 + 4j

# Boolean
is_active = True
is_verified = False

# None
result = None

# Type checking
print(f"Name: {name} ({type(name).__name__})")
print(f"Age: {age} ({type(age).__name__})")
print(f"PI: {pi} ({type(pi).__name__})")
print(f"Active: {is_active} ({type(is_active).__name__})")
```

### Example 3: String Operations

```python
#!/usr/bin/env python3
# ex03_strings.py - String operations

text = "Python Programming in Termux"

# Length
print(f"Length: {len(text)}")

# Case conversion
print(f"Upper: {text.upper()}")
print(f"Lower: {text.lower()}")
print(f"Title: {text.title()}")
print(f"Swapcase: {text.swapcase()}")

# Searching
print(f"'Python' found at: {text.find('Python')}")
print(f"Count of 'i': {text.count('i')}")

# Slicing
print(f"First 6 chars: {text[:6]}")
print(f"Last 6 chars: {text[-6:]}")
print(f"Reversed: {text[::-1]}")

# Split and join
words = text.split()
print(f"Words: {words}")
joined = "-".join(words)
print(f"Joined: {joined}")

# Replace
new_text = text.replace("Termux", "Android")
print(f"Replaced: {new_text}")
```

### Example 4: Math Operations

```python
#!/usr/bin/env python3
# ex04_math.py - Mathematical operations

import math

# Basic operations
a, b = 10, 3
print(f"{a} + {b} = {a + b}")
print(f"{a} - {b} = {a - b}")
print(f"{a} * {b} = {a * b}")
print(f"{a} / {b} = {a / b}")
print(f"{a} // {b} = {a // b}")
print(f"{a} % {b} = {a % b}")
print(f"{a} ** {b} = {a ** b}")

# Math functions
print(f"\nMath functions:")
print(f"sqrt(16) = {math.sqrt(16)}")
print(f"ceil(3.2) = {math.ceil(3.2)}")
print(f"floor(3.8) = {math.floor(3.8)}")
print(f"abs(-5) = {abs(-5)}")
print(f"round(3.14159, 2) = {round(3.14159, 2)}")

# Constants
print(f"\nConstants:")
print(f"pi = {math.pi}")
print(f"e = {math.e}")

# Trigonometry
angle = math.pi / 4  # 45 degrees
print(f"\nsin(45°) = {math.sin(angle):.4f}")
print(f"cos(45°) = {math.cos(angle):.4f}")
print(f"tan(45°) = {math.tan(angle):.4f}")
```

### Example 5: List Operations

```python
#!/usr/bin/env python3
# ex05_lists.py - List operations

# Create lists
tools = ["nmap", "hydra", "sqlmap"]
numbers = [3, 1, 4, 1, 5, 9, 2, 6]

# Access elements
print(f"First tool: {tools[0]}")
print(f"Last tool: {tools[-1]}")
print(f"First 2 tools: {tools[:2]}")

# Modify list
tools.append("metasploit")
tools.insert(1, "burpsuite")
print(f"After adding: {tools}")

# Remove elements
tools.remove("burpsuite")
popped = tools.pop()
print(f"After removing: {tools}")
print(f"Popped: {popped}")

# Sort and reverse
numbers.sort()
print(f"Sorted: {numbers}")
numbers.reverse()
print(f"Reversed: {numbers}")

# List comprehension
squares = [x**2 for x in range(1, 6)]
print(f"Squares: {squares}")

evens = [x for x in range(10) if x % 2 == 0]
print(f"Evens: {evens}")
```

### Example 6: Dictionary Operations

```python
#!/usr/bin/env python3
# ex06_dictionaries.py - Dictionary operations

# Create dictionary
hacker = {
    "name": "T3rmuxk1ng",
    "age": 25,
    "skills": ["Python", "Bash", "Linux"],
    "country": "India"
}

# Access values
print(f"Name: {hacker['name']}")
print(f"Age: {hacker.get('age')}")
print(f"City: {hacker.get('city', 'Unknown')}")

# Modify dictionary
hacker["age"] = 26
hacker["city"] = "Mumbai"
print(f"After update: {hacker}")

# Iterate
print("\nAll info:")
for key, value in hacker.items():
    print(f"  {key}: {value}")

# Nested dictionary
users = {
    "user1": {"name": "Alice", "role": "admin"},
    "user2": {"name": "Bob", "role": "user"}
}
print(f"\nUser1 name: {users['user1']['name']}")

# Dictionary comprehension
squares = {x: x**2 for x in range(1, 6)}
print(f"\nSquares dict: {squares}")
```

### Example 7: Control Flow

```python
#!/usr/bin/env python3
# ex07_control_flow.py - If-elif-else statements

# Simple if
age = 18
if age >= 18:
    print("You are an adult")

# If-else
score = 75
if score >= 50:
    print("Passed!")
else:
    print("Failed!")

# If-elif-else
grade = 85
if grade >= 90:
    print("Grade: A")
elif grade >= 80:
    print("Grade: B")
elif grade >= 70:
    print("Grade: C")
elif grade >= 60:
    print("Grade: D")
else:
    print("Grade: F")

# Logical operators
username = "admin"
password = "secret123"
is_admin = True

if username == "admin" and password == "secret123":
    if is_admin:
        print("Welcome, Admin! Full access granted.")
    else:
        print("Welcome! Limited access.")
else:
    print("Invalid credentials!")

# Ternary operator
status = "Online" if is_admin else "Offline"
print(f"Status: {status}")
```

### Example 8: For Loop Examples

```python
#!/usr/bin/env python3
# ex08_for_loops.py - For loop examples

# Iterate over list
tools = ["nmap", "hydra", "sqlmap"]
print("Security Tools:")
for tool in tools:
    print(f"  - {tool}")

# Range examples
print("\nCounting 0-4:")
for i in range(5):
    print(i, end=" ")

print("\n\nEven numbers 0-10:")
for i in range(0, 11, 2):
    print(i, end=" ")

# Enumerate
print("\n\nEnumerated list:")
for index, tool in enumerate(tools, 1):
    print(f"  {index}. {tool}")

# Dictionary iteration
hacker = {"name": "T3rmuxk1ng", "age": 25, "skill": "Python"}
print("\nHacker info:")
for key, value in hacker.items():
    print(f"  {key}: {value}")

# Nested loops
print("\nMultiplication table (1-3):")
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i}x{j}={i*j}", end="  ")
    print()

# Loop control
print("\nBreak example:")
for i in range(10):
    if i == 5:
        break
    print(i, end=" ")

print("\n\nContinue example:")
for i in range(10):
    if i % 2 == 0:
        continue
    print(i, end=" ")
```

### Example 9: While Loop Examples

```python
#!/usr/bin/env python3
# ex09_while_loops.py - While loop examples

# Basic while
print("Countdown:")
count = 5
while count > 0:
    print(count)
    count -= 1
print("Blast off!")

# While with condition
print("\nFinding first multiple of 7 > 100:")
num = 100
while num % 7 != 0:
    num += 1
print(f"Found: {num}")

# While with else
print("\nSearching in list:")
items = ["apple", "banana", "cherry"]
index = 0
while index < len(items):
    if items[index] == "banana":
        print(f"Found banana at index {index}")
        break
    index += 1
else:
    print("Banana not found!")

# Infinite loop with break
print("\nMenu (simulated):")
options = ["1", "2", "3", "q"]
choice_idx = 0
while True:
    choice = options[choice_idx]
    print(f"Selected: {choice}")
    if choice == "q":
        print("Quitting...")
        break
    choice_idx += 1
```

### Example 10: Functions

```python
#!/usr/bin/env python3
# ex10_functions.py - Function examples

# Basic function
def greet():
    print("Hello, Hacker!")

greet()

# Function with parameters
def greet_person(name):
    print(f"Hello, {name}!")

greet_person("T3rmuxk1ng")

# Function with return value
def add(a, b):
    return a + b

result = add(5, 3)
print(f"5 + 3 = {result}")

# Default parameters
def power(base, exponent=2):
    return base ** exponent

print(f"5^2 = {power(5)}")
print(f"5^3 = {power(5, 3)}")

# Multiple return values
def min_max(numbers):
    return min(numbers), max(numbers)

minimum, maximum = min_max([3, 1, 4, 1, 5, 9])
print(f"Min: {minimum}, Max: {maximum}")

# *args
def sum_all(*numbers):
    return sum(numbers)

print(f"Sum: {sum_all(1, 2, 3, 4, 5)}")

# **kwargs
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"  {key}: {value}")

print("Info:")
print_info(name="T3rmuxk1ng", age=25, country="India")

# Lambda functions
square = lambda x: x ** 2
print(f"Square of 7: {square(7)}")

# Lambda with map and filter
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(f"Squared: {squared}")
print(f"Evens: {evens}")
```

### Example 11: File Operations

```python
#!/usr/bin/env python3
# ex11_files.py - File operations

import os

# Write to file
filename = "test_data.txt"
with open(filename, "w") as f:
    f.write("Line 1: Hello Termux\n")
    f.write("Line 2: Python is powerful\n")
    f.write("Line 3: Happy coding!\n")

print(f"File '{filename}' created")

# Read entire file
with open(filename, "r") as f:
    content = f.read()
print("\nFile content:")
print(content)

# Read line by line
print("Lines:")
with open(filename, "r") as f:
    for i, line in enumerate(f, 1):
        print(f"  {i}: {line.strip()}")

# Append to file
with open(filename, "a") as f:
    f.write("Line 4: Added later\n")

# Get file info
print(f"\nFile size: {os.path.getsize(filename)} bytes")
print(f"File exists: {os.path.exists(filename)}")

# Cleanup
# os.remove(filename)
```

### Example 12: JSON Handling

```python
#!/usr/bin/env python3
# ex12_json.py - JSON handling

import json

# Python dict to JSON
data = {
    "name": "T3rmuxk1ng",
    "age": 25,
    "skills": ["Python", "Bash", "Linux"],
    "active": True,
    "projects": [
        {"name": "Termux Course", "chapters": 61},
        {"name": "Security Tools", "tools": 10}
    ]
}

# Write JSON to file
with open("data.json", "w") as f:
    json.dump(data, f, indent=4)

print("JSON file created")

# Read JSON from file
with open("data.json", "r") as f:
    loaded = json.load(f)

print(f"Name: {loaded['name']}")
print(f"Skills: {', '.join(loaded['skills'])}")
print(f"Projects: {len(loaded['projects'])}")

# Convert to/from string
json_string = json.dumps(data, indent=2)
print("\nJSON String:")
print(json_string)

parsed = json.loads(json_string)
print(f"\nParsed name: {parsed['name']}")
```

### Example 13: Modules and Imports

```python
#!/usr/bin/env python3
# ex13_modules.py - Module examples

import os
import sys
import random
import datetime
import time

# os module
print("=== OS Module ===")
print(f"Current dir: {os.getcwd()}")
print(f"Home: {os.path.expanduser('~')}")
print(f"PATH: {os.environ.get('PATH', 'Not set')[:50]}...")

# sys module
print("\n=== sys Module ===")
print(f"Python version: {sys.version}")
print(f"Platform: {sys.platform}")
print(f"Arguments: {sys.argv}")

# random module
print("\n=== random Module ===")
print(f"Random int (1-100): {random.randint(1, 100)}")
print(f"Random float: {random.random():.4f}")
print(f"Random choice: {random.choice(['nmap', 'hydra', 'sqlmap'])}")
items = [1, 2, 3, 4, 5]
random.shuffle(items)
print(f"Shuffled list: {items}")

# datetime module
print("\n=== datetime Module ===")
now = datetime.datetime.now()
print(f"Current time: {now}")
print(f"Formatted: {now.strftime('%Y-%m-%d %H:%M:%S')}")
print(f"Date only: {now.date()}")
print(f"Time only: {now.time()}")

# time module
print("\n=== time Module ===")
print(f"Timestamp: {time.time()}")
print("Sleeping 1 second...")
time.sleep(1)
print("Done!")
```

### Example 14: Subprocess Module

```python
#!/usr/bin/env python3
# ex14_subprocess.py - Running shell commands

import subprocess

# Run command and get output
result = subprocess.run(
    ["echo", "Hello from subprocess"],
    capture_output=True,
    text=True
)
print(f"Output: {result.stdout.strip()}")

# Run ls command
result = subprocess.run(
    ["ls", "-la"],
    capture_output=True,
    text=True
)
print("\nDirectory listing:")
print(result.stdout[:500])  # First 500 chars

# Run with shell=True (use pipes)
result = subprocess.run(
    "ls -la | grep -E '\\.py$' | head -5",
    shell=True,
    capture_output=True,
    text=True
)
print("\nPython files:")
print(result.stdout)

# Check command success
result = subprocess.run(["which", "python"], capture_output=True)
if result.returncode == 0:
    print("\nPython is installed!")
else:
    print("\nPython not found!")

# Get device uptime
result = subprocess.run(["uptime"], capture_output=True, text=True)
print(f"\nUptime: {result.stdout.strip()}")
```

### Example 15: Termux API Integration

```python
#!/usr/bin/env python3
# ex15_termux_api.py - Termux API integration

import subprocess
import json

def run_termux_api(command):
    """Run Termux API command and return JSON result"""
    try:
        result = subprocess.run(
            command,
            capture_output=True,
            text=True,
            timeout=10
        )
        if result.returncode == 0:
            try:
                return json.loads(result.stdout)
            except:
                return result.stdout.strip()
        else:
            return {"error": result.stderr.strip()}
    except FileNotFoundError:
        return {"error": "Termux:API not installed"}
    except Exception as e:
        return {"error": str(e)}

# Get battery status
print("=== Battery Status ===")
battery = run_termux_api(["termux-battery-status"])
print(json.dumps(battery, indent=2))

# Get device info
print("\n=== Device Info ===")
device_info = run_termux_api(["termux-telephony-deviceinfo"])
if "error" not in device_info:
    print(f"Device: {device_info.get('device', 'Unknown')}")
    print(f"Network: {device_info.get('network_operator_name', 'Unknown')}")

# Text to speech
def speak(text):
    """Use Termux TTS"""
    subprocess.run(["termux-tts-speak", text])
    print(f"Speaking: {text}")

# Uncomment to test:
# speak("Hello from Python!")

# Vibrate
def vibrate(duration=500):
    """Trigger vibration"""
    subprocess.run(["termux-vibrate", "-d", str(duration)])
    print(f"Vibrating for {duration}ms")

# Uncomment to test:
# vibrate(300)

# Get clipboard content
def get_clipboard():
    """Get clipboard content"""
    result = subprocess.run(
        ["termux-clipboard-get"],
        capture_output=True,
        text=True
    )
    return result.stdout.strip()

# Set clipboard
def set_clipboard(text):
    """Set clipboard content"""
    subprocess.run(["termux-clipboard-set", text])
    print(f"Clipboard set to: {text}")

# Test clipboard
set_clipboard("Hello Termux!")
print(f"Clipboard: {get_clipboard()}")
```

### Example 16: Argument Parsing

```python
#!/usr/bin/env python3
# ex16_argparse.py - Command line argument parsing

import argparse
import sys

def main():
    parser = argparse.ArgumentParser(
        description="Termux Tool - A sample Python script",
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog="""
Examples:
  python %(prog)s -n T3rmuxk1ng
  python %(prog)s --verbose -n Admin -a 25
  python %(prog)s -f output.txt -c 3
        """
    )

    # Positional argument
    parser.add_argument(
        "action",
        choices=["start", "stop", "status"],
        help="Action to perform"
    )

    # Optional arguments
    parser.add_argument(
        "-n", "--name",
        type=str,
        default="Hacker",
        help="Your name (default: Hacker)"
    )

    parser.add_argument(
        "-a", "--age",
        type=int,
        help="Your age"
    )

    parser.add_argument(
        "-f", "--file",
        type=str,
        help="Output file path"
    )

    parser.add_argument(
        "-c", "--count",
        type=int,
        default=1,
        help="Number of iterations (default: 1)"
    )

    parser.add_argument(
        "-v", "--verbose",
        action="store_true",
        help="Enable verbose output"
    )

    # Parse arguments
    args = parser.parse_args()

    # Display results
    print(f"Action: {args.action}")
    print(f"Name: {args.name}")
    
    if args.age:
        print(f"Age: {args.age}")
    
    if args.file:
        print(f"Output file: {args.file}")
    
    print(f"Count: {args.count}")
    
    if args.verbose:
        print("Verbose mode enabled!")
        print(f"All args: {vars(args)}")

if __name__ == "__main__":
    main()
```

### Example 17: System Information Script

```python
#!/usr/bin/env python3
# ex17_sysinfo.py - System information

import os
import sys
import platform
import subprocess
from datetime import datetime

def get_command_output(cmd):
    """Get output from shell command"""
    try:
        result = subprocess.run(
            cmd,
            shell=True,
            capture_output=True,
            text=True
        )
        return result.stdout.strip()
    except:
        return "N/A"

def get_system_info():
    """Gather system information"""
    info = {}
    
    # Python info
    info["python_version"] = platform.python_version()
    info["python_path"] = sys.executable
    
    # System info
    info["system"] = platform.system()
    info["machine"] = platform.machine()
    
    # Termux specific
    info["termux_version"] = os.environ.get("TERMUX_VERSION", "N/A")
    info["prefix"] = os.environ.get("PREFIX", "N/A")
    info["home"] = os.path.expanduser("~")
    
    # Android info (via getprop)
    info["android_version"] = get_command_output("getprop ro.build.version.release")
    info["device_model"] = get_command_output("getprop ro.product.model")
    info["device_brand"] = get_command_output("getprop ro.product.brand")
    
    # CPU info
    cpu_info = get_command_output("cat /proc/cpuinfo | grep 'model name' | head -1")
    info["cpu"] = cpu_info.split(":")[-1].strip() if ":" in cpu_info else "N/A"
    
    # Memory info
    mem_info = get_command_output("cat /proc/meminfo | grep MemTotal")
    if "MemTotal" in mem_info:
        mem_kb = mem_info.split()[1]
        info["total_memory"] = f"{int(mem_kb) // 1024} MB"
    
    # Uptime
    info["uptime"] = get_command_output("uptime -p")
    
    # Date and time
    info["current_time"] = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    
    return info

def display_info(info):
    """Display system information"""
    print("=" * 50)
    print("TERMUX SYSTEM INFORMATION")
    print("=" * 50)
    
    print("\n[Python]")
    print(f"  Version: {info['python_version']}")
    print(f"  Path: {info['python_path']}")
    
    print("\n[System]")
    print(f"  System: {info['system']}")
    print(f"  Machine: {info['machine']}")
    
    print("\n[Termux]")
    print(f"  Version: {info['termux_version']}")
    print(f"  Prefix: {info['prefix']}")
    print(f"  Home: {info['home']}")
    
    print("\n[Device]")
    print(f"  Android: {info['android_version']}")
    print(f"  Model: {info['device_model']}")
    print(f"  Brand: {info['device_brand']}")
    
    print("\n[Hardware]")
    print(f"  CPU: {info['cpu']}")
    print(f"  Memory: {info['total_memory']}")
    
    print("\n[Status]")
    print(f"  Uptime: {info['uptime']}")
    print(f"  Time: {info['current_time']}")
    
    print("=" * 50)

if __name__ == "__main__":
    info = get_system_info()
    display_info(info)
```

### Example 18: Simple Port Scanner

```python
#!/usr/bin/env python3
# ex18_port_scanner.py - Simple port scanner

import socket
import argparse
from concurrent.futures import ThreadPoolExecutor

def scan_port(host, port, timeout=1):
    """Scan a single port"""
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(timeout)
        result = sock.connect_ex((host, port))
        sock.close()
        return port, result == 0
    except:
        return port, False

def scan_host(host, ports, threads=50):
    """Scan multiple ports on a host"""
    print(f"Scanning {host}...")
    open_ports = []
    
    with ThreadPoolExecutor(max_workers=threads) as executor:
        results = executor.map(lambda p: scan_port(host, p), ports)
        
        for port, is_open in results:
            if is_open:
                open_ports.append(port)
                print(f"  [+] Port {port}: Open")
    
    return open_ports

def main():
    parser = argparse.ArgumentParser(description="Simple Port Scanner")
    parser.add_argument("host", help="Target host")
    parser.add_argument("-p", "--ports", default="1-1000",
                        help="Port range (default: 1-1000)")
    parser.add_argument("-t", "--threads", type=int, default=50,
                        help="Number of threads (default: 50)")
    
    args = parser.parse_args()
    
    # Parse port range
    if "-" in args.ports:
        start, end = map(int, args.ports.split("-"))
        ports = range(start, end + 1)
    else:
        ports = [int(p) for p in args.ports.split(",")]
    
    # Scan
    open_ports = scan_host(args.host, ports, args.threads)
    
    # Summary
    print(f"\nScan complete!")
    print(f"Open ports: {len(open_ports)}")
    if open_ports:
        print(f"Ports: {sorted(open_ports)}")

if __name__ == "__main__":
    main()
```

### Example 19: Password Generator

```python
#!/usr/bin/env python3
# ex19_password_gen.py - Password generator

import random
import string
import argparse

def generate_password(length=16, use_upper=True, use_lower=True, 
                      use_digits=True, use_special=True):
    """Generate a random password"""
    characters = ""
    
    if use_lower:
        characters += string.ascii_lowercase
    if use_upper:
        characters += string.ascii_uppercase
    if use_digits:
        characters += string.digits
    if use_special:
        characters += "!@#$%^&*()_+-=[]{}|;:,.<>?"
    
    if not characters:
        characters = string.ascii_letters + string.digits
    
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def calculate_strength(password):
    """Calculate password strength score"""
    score = 0
    
    if len(password) >= 8:
        score += 1
    if len(password) >= 12:
        score += 1
    if len(password) >= 16:
        score += 1
    if any(c.islower() for c in password):
        score += 1
    if any(c.isupper() for c in password):
        score += 1
    if any(c.isdigit() for c in password):
        score += 1
    if any(c in "!@#$%^&*()_+-=[]{}|;:,.<>?" for c in password):
        score += 1
    
    if score <= 2:
        return "Weak"
    elif score <= 4:
        return "Medium"
    elif score <= 6:
        return "Strong"
    else:
        return "Very Strong"

def main():
    parser = argparse.ArgumentParser(description="Password Generator")
    parser.add_argument("-l", "--length", type=int, default=16,
                        help="Password length (default: 16)")
    parser.add_argument("-c", "--count", type=int, default=1,
                        help="Number of passwords (default: 1)")
    parser.add_argument("--no-upper", action="store_true",
                        help="Exclude uppercase letters")
    parser.add_argument("--no-lower", action="store_true",
                        help="Exclude lowercase letters")
    parser.add_argument("--no-digits", action="store_true",
                        help="Exclude digits")
    parser.add_argument("--no-special", action="store_true",
                        help="Exclude special characters")
    
    args = parser.parse_args()
    
    print(f"Generating {args.count} password(s) of length {args.length}")
    print("=" * 50)
    
    for i in range(args.count):
        password = generate_password(
            length=args.length,
            use_upper=not args.no_upper,
            use_lower=not args.no_lower,
            use_digits=not args.no_digits,
            use_special=not args.no_special
        )
        strength = calculate_strength(password)
        print(f"Password {i+1}: {password}")
        print(f"Strength: {strength}")
        print("-" * 50)

if __name__ == "__main__":
    main()
```

### Example 20: Simple Web Scraper

```python
#!/usr/bin/env python3
# ex20_web_scraper.py - Simple web scraper

import subprocess
import json
import re

def fetch_url(url):
    """Fetch content from URL using curl"""
    try:
        result = subprocess.run(
            ["curl", "-s", "-L", url],
            capture_output=True,
            text=True,
            timeout=30
        )
        return result.stdout
    except Exception as e:
        return f"Error: {e}"

def extract_emails(text):
    """Extract email addresses from text"""
    pattern = r'[\w\.-]+@[\w\.-]+\.\w+'
    emails = re.findall(pattern, text)
    return list(set(emails))

def extract_urls(text):
    """Extract URLs from text"""
    pattern = r'https?://[^\s<>"]+|www\.[^\s<>"]+'
    urls = re.findall(pattern, text)
    return list(set(urls))[:10]  # Return first 10

def extract_titles(text):
    """Extract title from HTML"""
    pattern = r'<title>(.*?)</title>'
    match = re.search(pattern, text, re.IGNORECASE | re.DOTALL)
    return match.group(1).strip() if match else None

def get_ip_info():
    """Get public IP information"""
    try:
        result = subprocess.run(
            ["curl", "-s", "https://ipinfo.io/json"],
            capture_output=True,
            text=True,
            timeout=10
        )
        return json.loads(result.stdout)
    except:
        return None

def main():
    print("=" * 50)
    print("SIMPLE WEB SCRAPER")
    print("=" * 50)
    
    # Get IP info
    print("\n[Your IP Info]")
    ip_info = get_ip_info()
    if ip_info:
        for key, value in ip_info.items():
            print(f"  {key}: {value}")
    
    # Example: Fetch a webpage (commented for safety)
    # print("\n[Fetching example.com]")
    # content = fetch_url("https://example.com")
    # 
    # if not content.startswith("Error"):
    #     title = extract_titles(content)
    #     print(f"  Title: {title}")
    #     
    #     emails = extract_emails(content)
    #     if emails:
    #         print(f"  Emails: {emails}")
    #     
    #     urls = extract_urls(content)
    #     if urls:
    #         print(f"  URLs found: {len(urls)}")
    # else:
    #     print(content)

if __name__ == "__main__":
    main()
```

### Example 21: File Organizer

```python
#!/usr/bin/env python3
# ex21_file_organizer.py - Organize files by extension

import os
import shutil
from pathlib import Path

# File categories
CATEGORIES = {
    "Images": [".jpg", ".jpeg", ".png", ".gif", ".bmp", ".svg", ".webp"],
    "Videos": [".mp4", ".avi", ".mkv", ".mov", ".wmv", ".flv"],
    "Audio": [".mp3", ".wav", ".flac", ".aac", ".ogg", ".m4a"],
    "Documents": [".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx"],
    "Archives": [".zip", ".rar", ".7z", ".tar", ".gz"],
    "Code": [".py", ".js", ".html", ".css", ".java", ".cpp", ".c", ".sh"],
    "Data": [".json", ".xml", ".csv", ".sql", ".db"],
    "APK": [".apk"],
    "Scripts": [".sh", ".bash", ".py", ".rb", ".pl"]
}

def get_category(extension):
    """Get category for a file extension"""
    ext = extension.lower()
    for category, extensions in CATEGORIES.items():
        if ext in extensions:
            return category
    return "Others"

def organize_directory(source_dir, dry_run=True):
    """Organize files in directory by extension"""
    source = Path(source_dir)
    
    if not source.exists():
        print(f"Directory not found: {source_dir}")
        return
    
    print(f"{'[DRY RUN] ' if dry_run else ''}Organizing: {source}")
    print("=" * 50)
    
    moved_count = 0
    
    for file_path in source.iterdir():
        if file_path.is_file():
            category = get_category(file_path.suffix)
            dest_dir = source / category
            
            if not dest_dir.exists():
                if not dry_run:
                    dest_dir.mkdir()
                print(f"Created folder: {category}")
            
            dest_file = dest_dir / file_path.name
            
            # Handle duplicate names
            counter = 1
            while dest_file.exists():
                stem = file_path.stem
                suffix = file_path.suffix
                dest_file = dest_dir / f"{stem}_{counter}{suffix}"
                counter += 1
            
            print(f"  {file_path.name} -> {category}/")
            
            if not dry_run:
                shutil.move(str(file_path), str(dest_file))
            
            moved_count += 1
    
    print("=" * 50)
    print(f"{'Would move' if dry_run else 'Moved'} {moved_count} file(s)")

def main():
    import argparse
    
    parser = argparse.ArgumentParser(description="File Organizer")
    parser.add_argument("directory", help="Directory to organize")
    parser.add_argument("-e", "--execute", action="store_true",
                        help="Actually move files (default is dry run)")
    
    args = parser.parse_args()
    
    organize_directory(args.directory, dry_run=not args.execute)

if __name__ == "__main__":
    main()
```

### Example 22: Network Tools

```python
#!/usr/bin/env python3
# ex22_network_tools.py - Network utilities

import subprocess
import socket
import re

def get_local_ip():
    """Get local IP address"""
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        s.connect(("8.8.8.8", 80))
        ip = s.getsockname()[0]
        s.close()
        return ip
    except:
        return "127.0.0.1"

def get_public_ip():
    """Get public IP address"""
    try:
        result = subprocess.run(
            ["curl", "-s", "https://api.ipify.org"],
            capture_output=True,
            text=True,
            timeout=10
        )
        return result.stdout.strip()
    except:
        return None

def ping_host(host, count=3):
    """Ping a host"""
    try:
        result = subprocess.run(
            ["ping", "-c", str(count), host],
            capture_output=True,
            text=True,
            timeout=10
        )
        return result.returncode == 0
    except:
        return False

def dns_lookup(domain):
    """Perform DNS lookup"""
    try:
        result = subprocess.run(
            ["nslookup", domain],
            capture_output=True,
            text=True
        )
        # Extract IP addresses
        ips = re.findall(r'Address: ([\d.]+)', result.stdout)
        return ips[1:] if len(ips) > 1 else ips  # Skip DNS server IP
    except:
        return []

def check_port(host, port):
    """Check if a port is open"""
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(2)
        result = sock.connect_ex((host, port))
        sock.close()
        return result == 0
    except:
        return False

def get_network_info():
    """Get network information"""
    info = {}
    
    info["local_ip"] = get_local_ip()
    info["public_ip"] = get_public_ip()
    
    # Get hostname
    info["hostname"] = socket.gethostname()
    
    return info

def main():
    print("=" * 50)
    print("NETWORK TOOLS")
    print("=" * 50)
    
    # Network info
    info = get_network_info()
    print("\n[Network Info]")
    print(f"  Hostname: {info['hostname']}")
    print(f"  Local IP: {info['local_ip']}")
    print(f"  Public IP: {info['public_ip']}")
    
    # DNS lookup example
    print("\n[DNS Lookup - google.com]")
    ips = dns_lookup("google.com")
    for ip in ips:
        print(f"  IP: {ip}")
    
    # Ping test
    print("\n[Ping Test - google.com]")
    if ping_host("google.com"):
        print("  Status: Reachable")
    else:
        print("  Status: Unreachable")
    
    # Port check
    print("\n[Port Check - google.com:443]")
    if check_port("google.com", 443):
        print("  Port 443: Open")
    else:
        print("  Port 443: Closed/Filtered")

if __name__ == "__main__":
    main()
```

---

## 📋 COMMANDS REFERENCE

### Python Commands

```bash
# Start interactive shell
python

# Run Python script
python script.py

# Run with Python 3 explicitly
python3 script.py

# Execute Python code directly
python -c "print('Hello')"

# Run module as script
python -m pip install package

# Check Python version
python --version
python -V

# Show Python help
python --help

# Start Python with optimization
python -O script.py

# Compile to bytecode
python -m py_compile script.py
```

### pip Commands

```bash
# Install package
pip install package_name

# Install specific version
pip install package_name==1.2.3

# Install from requirements file
pip install -r requirements.txt

# Uninstall package
pip uninstall package_name

# List installed packages
pip list

# Show package info
pip show package_name

# Search for package
pip search keyword

# Freeze installed packages
pip freeze

# Create requirements.txt
pip freeze > requirements.txt

# Upgrade pip
pip install --upgrade pip

# Install from git
pip install git+https://github.com/user/repo.git

# Install in user space
pip install --user package_name

# Clear cache
pip cache purge
```

### Script Execution

```bash
# Make script executable
chmod +x script.py

# Run executable script
./script.py

# Run in background
python script.py &

# Run with nohup (survives terminal close)
nohup python script.py &

# Run with output logging
python script.py > output.log 2>&1

# Run with input
python script.py < input.txt

# Pass arguments
python script.py arg1 arg2 --option value
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Calculator Program

```python
#!/usr/bin/env python3
# exercise1_calculator.py - Simple calculator

"""
Create a calculator that:
1. Takes two numbers and an operation
2. Performs the calculation
3. Handles division by zero
4. Continues until user quits
"""

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Error: Division by zero!"
    return a / b

def main():
    print("=== Simple Calculator ===")
    print("Operations: +, -, *, /, q (quit)")
    
    while True:
        print("\n" + "-" * 30)
        
        # Get operation
        op = input("Enter operation (+, -, *, /, q): ").strip()
        
        if op.lower() == 'q':
            print("Goodbye!")
            break
        
        if op not in ['+', '-', '*', '/']:
            print("Invalid operation!")
            continue
        
        # Get numbers
        try:
            num1 = float(input("Enter first number: "))
            num2 = float(input("Enter second number: "))
        except ValueError:
            print("Invalid number!")
            continue
        
        # Perform calculation
        operations = {
            '+': add,
            '-': subtract,
            '*': multiply,
            '/': divide
        }
        
        result = operations[op](num1, num2)
        print(f"Result: {num1} {op} {num2} = {result}")

if __name__ == "__main__":
    main()
```

### Exercise 2: To-Do List

```python
#!/usr/bin/env python3
# exercise2_todolist.py - To-do list manager

"""
Create a to-do list manager that:
1. Can add tasks
2. Can list all tasks
3. Can mark tasks as done
4. Can delete tasks
5. Saves to file
"""

import json
import os

TODO_FILE = "todo_list.json"

def load_tasks():
    """Load tasks from file"""
    if os.path.exists(TODO_FILE):
        with open(TODO_FILE, 'r') as f:
            return json.load(f)
    return []

def save_tasks(tasks):
    """Save tasks to file"""
    with open(TODO_FILE, 'w') as f:
        json.dump(tasks, f, indent=2)

def add_task(tasks, description):
    """Add a new task"""
    task = {
        "id": len(tasks) + 1,
        "description": description,
        "done": False
    }
    tasks.append(task)
    save_tasks(tasks)
    print(f"Added: {description}")

def list_tasks(tasks):
    """List all tasks"""
    if not tasks:
        print("No tasks!")
        return
    
    print("\n" + "=" * 50)
    print("YOUR TASKS")
    print("=" * 50)
    
    for task in tasks:
        status = "✓" if task["done"] else " "
        print(f"[{status}] {task['id']}. {task['description']}")
    
    print("=" * 50)

def complete_task(tasks, task_id):
    """Mark task as done"""
    for task in tasks:
        if task["id"] == task_id:
            task["done"] = True
            save_tasks(tasks)
            print(f"Completed: {task['description']}")
            return
    print("Task not found!")

def delete_task(tasks, task_id):
    """Delete a task"""
    for i, task in enumerate(tasks):
        if task["id"] == task_id:
            deleted = tasks.pop(i)
            save_tasks(tasks)
            print(f"Deleted: {deleted['description']}")
            return
    print("Task not found!")

def main():
    tasks = load_tasks()
    
    print("=" * 50)
    print("TO-DO LIST MANAGER")
    print("=" * 50)
    print("Commands: add, list, done, delete, quit")
    
    while True:
        command = input("\n> ").strip().lower()
        
        if command == 'quit' or command == 'q':
            print("Goodbye!")
            break
        
        elif command == 'add':
            description = input("Task description: ").strip()
            if description:
                add_task(tasks, description)
        
        elif command == 'list':
            list_tasks(tasks)
        
        elif command == 'done':
            try:
                task_id = int(input("Task ID: "))
                complete_task(tasks, task_id)
            except ValueError:
                print("Invalid ID!")
        
        elif command == 'delete':
            try:
                task_id = int(input("Task ID: "))
                delete_task(tasks, task_id)
            except ValueError:
                print("Invalid ID!")
        
        else:
            print("Unknown command! Use: add, list, done, delete, quit")

if __name__ == "__main__":
    main()
```

### Exercise 3: Guess the Number Game

```python
#!/usr/bin/env python3
# exercise3_guess_number.py - Number guessing game

"""
Create a number guessing game:
1. Computer picks random number 1-100
2. Player guesses
3. Computer says higher/lower
4. Track number of guesses
5. Option to play again
"""

import random

def get_difficulty():
    """Get difficulty level"""
    print("\nSelect Difficulty:")
    print("1. Easy (1-50, 10 attempts)")
    print("2. Medium (1-100, 7 attempts)")
    print("3. Hard (1-200, 5 attempts)")
    
    while True:
        try:
            choice = int(input("Choose (1-3): "))
            if choice in [1, 2, 3]:
                ranges = {1: (1, 50, 10), 2: (1, 100, 7), 3: (1, 200, 5)}
                return ranges[choice]
        except ValueError:
            pass
        print("Invalid choice!")

def play_game():
    """Play one round"""
    min_num, max_num, max_attempts = get_difficulty()
    target = random.randint(min_num, max_num)
    attempts = 0
    
    print(f"\nI'm thinking of a number between {min_num} and {max_num}")
    print(f"You have {max_attempts} attempts")
    
    while attempts < max_attempts:
        try:
            guess = int(input(f"\nAttempt {attempts + 1}/{max_attempts}. Your guess: "))
            
            if guess < min_num or guess > max_num:
                print(f"Please enter a number between {min_num} and {max_num}")
                continue
            
            attempts += 1
            
            if guess == target:
                print(f"\n🎉 Congratulations! You got it in {attempts} attempts!")
                
                # Score based on attempts
                score = (max_attempts - attempts + 1) * 100
                print(f"Score: {score}")
                return True
            
            elif guess < target:
                remaining = max_attempts - attempts
                print(f"Higher! ({remaining} attempts left)")
            
            else:
                remaining = max_attempts - attempts
                print(f"Lower! ({remaining} attempts left)")
        
        except ValueError:
            print("Please enter a valid number!")
    
    print(f"\n😢 Game Over! The number was {target}")
    return False

def main():
    print("=" * 50)
    print("   GUESS THE NUMBER")
    print("=" * 50)
    
    wins = 0
    games = 0
    
    while True:
        games += 1
        if play_game():
            wins += 1
        
        # Show stats
        print(f"\nStats: {wins} wins out of {games} games")
        
        # Play again?
        again = input("\nPlay again? (y/n): ").lower()
        if again != 'y':
            break
    
    print("\nThanks for playing!")
    print(f"Final Score: {wins}/{games} wins")

if __name__ == "__main__":
    main()
```

### Exercise 4: Text File Analyzer

```python
#!/usr/bin/env python3
# exercise4_text_analyzer.py - Text file analyzer

"""
Create a text file analyzer that:
1. Reads a text file
2. Counts words, lines, characters
3. Finds most common words
4. Shows word frequency
"""

import os
from collections import Counter
import string

def read_file(filepath):
    """Read file content"""
    if not os.path.exists(filepath):
        return None
    with open(filepath, 'r', encoding='utf-8', errors='ignore') as f:
        return f.read()

def clean_text(text):
    """Clean and tokenize text"""
    # Remove punctuation and convert to lowercase
    translator = str.maketrans('', '', string.punctuation)
    text = text.lower().translate(translator)
    # Split into words
    words = text.split()
    # Remove common stop words
    stop_words = {'the', 'a', 'an', 'and', 'or', 'but', 'in', 'on', 'at', 
                  'to', 'for', 'of', 'is', 'it', 'this', 'that', 'was', 'are'}
    words = [w for w in words if w not in stop_words and len(w) > 2]
    return words

def analyze_file(filepath):
    """Analyze text file"""
    content = read_file(filepath)
    if content is None:
        print(f"Error: Cannot read file '{filepath}'")
        return
    
    # Basic stats
    lines = content.split('\n')
    words = clean_text(content)
    chars = len(content)
    chars_no_space = len(content.replace(' ', '').replace('\n', ''))
    
    print("=" * 60)
    print(f"FILE ANALYSIS: {filepath}")
    print("=" * 60)
    
    print("\n[BASIC STATISTICS]")
    print(f"  Total lines: {len(lines)}")
    print(f"  Non-empty lines: {len([l for l in lines if l.strip()])}")
    print(f"  Total characters: {chars}")
    print(f"  Characters (no spaces): {chars_no_space}")
    print(f"  Total words: {len(words)}")
    print(f"  Unique words: {len(set(words))}")
    
    # Word frequency
    word_freq = Counter(words)
    most_common = word_freq.most_common(10)
    
    print("\n[TOP 10 MOST COMMON WORDS]")
    for i, (word, count) in enumerate(most_common, 1):
        bar = "█" * min(count, 30)
        print(f"  {i:2}. {word:15} {count:4} {bar}")
    
    # Word length distribution
    lengths = Counter(len(w) for w in words)
    
    print("\n[WORD LENGTH DISTRIBUTION]")
    for length in sorted(lengths.keys())[:10]:
        count = lengths[length]
        bar = "█" * min(count // 2, 30)
        print(f"  {length} chars: {count:4} {bar}")
    
    # Average word length
    avg_length = sum(len(w) for w in words) / len(words) if words else 0
    print(f"\n  Average word length: {avg_length:.2f}")
    
    print("=" * 60)

def main():
    import argparse
    
    parser = argparse.ArgumentParser(description="Text File Analyzer")
    parser.add_argument("file", help="Text file to analyze")
    
    args = parser.parse_args()
    analyze_file(args.file)

if __name__ == "__main__":
    # Demo with sample text
    sample_file = "sample_text.txt"
    sample_text = """
    Python is a powerful programming language. It is used for web development,
    data analysis, artificial intelligence, and automation. Python has a simple
    syntax that makes it easy to learn. Many developers love Python because it
    is versatile and has a large community. Termux allows you to run Python on
    your Android device. This makes it possible to code anywhere, anytime.
    """
    
    # Create sample file
    with open(sample_file, 'w') as f:
        f.write(sample_text)
    
    # Analyze
    analyze_file(sample_file)
    
    # Cleanup
    os.remove(sample_file)
```

### Exercise 5: Simple Contact Manager

```python
#!/usr/bin/env python3
# exercise5_contacts.py - Contact manager

"""
Create a contact manager that:
1. Stores contacts with name, phone, email
2. Can add, search, update, delete contacts
3. Saves contacts to JSON file
4. Can import/export contacts
"""

import json
import os
import re

CONTACTS_FILE = "contacts.json"

def load_contacts():
    """Load contacts from file"""
    if os.path.exists(CONTACTS_FILE):
        with open(CONTACTS_FILE, 'r') as f:
            return json.load(f)
    return {}

def save_contacts(contacts):
    """Save contacts to file"""
    with open(CONTACTS_FILE, 'w') as f:
        json.dump(contacts, f, indent=2)

def validate_phone(phone):
    """Validate phone number"""
    # Remove spaces and dashes
    phone = re.sub(r'[\s\-]', '', phone)
    # Check if it's a valid phone format
    if re.match(r'^\+?[\d]{10,15}$', phone):
        return phone
    return None

def validate_email(email):
    """Validate email address"""
    pattern = r'^[\w\.-]+@[\w\.-]+\.\w+$'
    return re.match(pattern, email) is not None

def add_contact(contacts):
    """Add a new contact"""
    print("\n[Add New Contact]")
    
    name = input("Name: ").strip()
    if not name:
        print("Name is required!")
        return
    
    if name in contacts:
        print("Contact already exists! Use update to modify.")
        return
    
    phone = input("Phone: ").strip()
    if phone:
        phone = validate_phone(phone)
        if not phone:
            print("Invalid phone number!")
            return
    
    email = input("Email: ").strip()
    if email and not validate_email(email):
        print("Invalid email address!")
        return
    
    contacts[name] = {
        "phone": phone or "",
        "email": email or ""
    }
    save_contacts(contacts)
    print(f"Contact '{name}' added!")

def search_contacts(contacts):
    """Search contacts"""
    query = input("Search: ").strip().lower()
    
    results = []
    for name, info in contacts.items():
        if query in name.lower() or query in info.get('phone', '') or query in info.get('email', '').lower():
            results.append((name, info))
    
    if not results:
        print("No contacts found!")
        return
    
    print(f"\nFound {len(results)} contact(s):")
    for name, info in results:
        print(f"\n  Name: {name}")
        print(f"  Phone: {info.get('phone', 'N/A')}")
        print(f"  Email: {info.get('email', 'N/A')}")

def list_contacts(contacts):
    """List all contacts"""
    if not contacts:
        print("No contacts!")
        return
    
    print(f"\n[All Contacts - {len(contacts)}]")
    print("-" * 40)
    
    for name, info in sorted(contacts.items()):
        print(f"  {name}")
        print(f"    Phone: {info.get('phone', 'N/A')}")
        print(f"    Email: {info.get('email', 'N/A')}")
        print()

def delete_contact(contacts):
    """Delete a contact"""
    name = input("Enter name to delete: ").strip()
    
    if name in contacts:
        del contacts[name]
        save_contacts(contacts)
        print(f"Contact '{name}' deleted!")
    else:
        print("Contact not found!")

def export_contacts(contacts):
    """Export contacts to file"""
    filename = input("Export filename (default: contacts_export.json): ").strip()
    filename = filename or "contacts_export.json"
    
    with open(filename, 'w') as f:
        json.dump(contacts, f, indent=2)
    print(f"Exported {len(contacts)} contacts to {filename}")

def main():
    contacts = load_contacts()
    
    print("=" * 50)
    print("   CONTACT MANAGER")
    print("=" * 50)
    print("Commands: add, search, list, delete, export, quit")
    
    while True:
        command = input("\n> ").strip().lower()
        
        if command in ['quit', 'q', 'exit']:
            print("Goodbye!")
            break
        
        elif command == 'add':
            add_contact(contacts)
        
        elif command == 'search':
            search_contacts(contacts)
        
        elif command == 'list':
            list_contacts(contacts)
        
        elif command == 'delete':
            delete_contact(contacts)
        
        elif command == 'export':
            export_contacts(contacts)
        
        else:
            print("Unknown command!")
            print("Commands: add, search, list, delete, export, quit")

if __name__ == "__main__":
    main()
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Python Command Not Found

```bash
# Cause: Python not installed

# Solution:
pkg install python -y

# Verify installation:
python --version
which python
```

### Problem 2: pip Install Fails

```bash
# Cause: Outdated pip or network issues

# Solution 1: Upgrade pip
python -m pip install --upgrade pip

# Solution 2: Use specific version
pip install package_name --no-cache-dir

# Solution 3: Install from wheel
pip download package_name
pip install package_name.whl

# Solution 4: Check internet
ping -c 3 pypi.org
```

### Problem 3: Permission Denied When Running Script

```bash
# Cause: Script not executable

# Solution:
chmod +x script.py
./script.py

# Or run with python directly:
python script.py
```

### Problem 4: Module Not Found Error

```bash
# Cause: Module not installed

# Example: ModuleNotFoundError: No module named 'requests'
# Solution:
pip install requests

# For specific Python version:
python -m pip install requests

# Check installed packages:
pip list | grep requests
```

### Problem 5: SyntaxError in Script

```python
# Common causes and solutions:

# 1. Missing colon after if/for/while/def
# Wrong:
if True
    print("Hello")
# Correct:
if True:
    print("Hello")

# 2. Incorrect indentation
# Wrong:
def greet():
print("Hello")  # IndentationError
# Correct:
def greet():
    print("Hello")

# 3. Missing quotes
# Wrong:
print(Hello)
# Correct:
print("Hello")

# 4. Using Python 2 syntax in Python 3
# Wrong (Python 2):
print "Hello"
# Correct (Python 3):
print("Hello")
```

### Problem 6: Termux API Commands Not Working in Python

```bash
# Cause: Termux:API app not installed

# Solution:
# 1. Install Termux:API from F-Droid
# 2. Grant necessary permissions

# Test in terminal first:
termux-battery-status

# If working in terminal but not in Python:
import subprocess
result = subprocess.run(["termux-battery-status"], capture_output=True, text=True)
print(result.stdout)
print(result.stderr)  # Check for errors
```

### Problem 7: File Not Found Error

```python
# Cause: Wrong path or file doesn't exist

import os

# Check current directory
print(os.getcwd())

# Check if file exists
if os.path.exists("file.txt"):
    print("File exists!")
else:
    print("File not found!")

# Use absolute path
file_path = os.path.expanduser("~/storage/downloads/file.txt")

# Or relative to script location
script_dir = os.path.dirname(os.path.abspath(__file__))
file_path = os.path.join(script_dir, "file.txt")
```

### Problem 8: Unicode Encode/Decode Error

```python
# Cause: Encoding mismatch

# Solution: Specify encoding
with open("file.txt", "r", encoding="utf-8") as f:
    content = f.read()

# Or handle errors
with open("file.txt", "r", errors="ignore") as f:
    content = f.read()

# For printing special characters:
print(text.encode('utf-8', errors='ignore').decode('utf-8'))
```

### Problem 9: Memory Error in Termux

```python
# Cause: Processing large files/data

# Solution: Use generators and process in chunks

# Instead of reading entire file:
with open("large_file.txt", "r") as f:
    for line in f:  # Process line by line
        process(line)

# For large data processing:
def process_in_chunks(data, chunk_size=1000):
    for i in range(0, len(data), chunk_size):
        yield data[i:i+chunk_size]
```

### Problem 10: Script Works in Terminal but Not When Run

```bash
# Cause: PATH or environment differences

# Solution 1: Use full paths
# Instead of:
subprocess.run(["mycommand"])
# Use:
subprocess.run(["/data/data/com.termux/files/usr/bin/mycommand"])

# Solution 2: Set environment
import os
os.environ["PATH"] = "/data/data/com.termux/files/usr/bin:" + os.environ.get("PATH", "")

# Solution 3: Use shell=True
subprocess.run("mycommand", shell=True)
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Python Logo + Terminal]          │
│                                    │
│   🐍 PYTHON BASICS                 │
│   in TERMUX                        │
│                                    │
│   ✓ Variables & Data Types         │
│   ✓ 20+ Code Examples              │
│   ✓ Termux API Integration         │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Learning Path Style**
```
┌────────────────────────────────────┐
│   PYTHON CRASH COURSE              │
│   ─────────────────────────        │
│                                    │
│   Variables → Strings → Lists      │
│      ↓                             │
│   Functions → Files → APIs         │
│                                    │
│   🎯 Complete Beginner Guide       │
│                                    │
│   Chapter 12 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Code Focus**
```
┌────────────────────────────────────┐
│  [Terminal Screenshot]             │
│                                    │
│  $ python                          │
│  >>> print("Hello Termux!")        │
│  Hello Termux!                     │
│  >>>                               │
│                                    │
│  🐍 PYTHON BASICS                  │
│  Complete Guide                    │
│                                    │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🐍 Termux Full Course - Chapter 12: Python Basics in Termux | Complete Beginner Guide

🔥 In this video you'll learn:
• Python fundamentals - variables, data types
• Strings and string manipulation
• Lists, tuples, and dictionaries
• Control flow - if, elif, else
• Loops - for and while
• Functions and modules
• File handling in Python
• Termux-specific Python usage
• subprocess, os, sys modules
• 20+ practical code examples!

⏱️ Timestamps:
0:00 - Introduction
1:00 - Python Interactive Shell
4:00 - Variables & Data Types
8:00 - Strings & String Methods
12:00 - Numbers & Math Operations
15:00 - Lists, Tuples & Dictionaries
20:00 - Control Flow (if/elif/else)
24:00 - Loops (for/while)
28:00 - Functions
32:00 - File Handling
36:00 - Modules & Imports
39:00 - Termux-Specific Python
43:00 - Creating Python Scripts
46:00 - Summary

📝 Code Examples from this video:
# Check Python version
python --version

# Start interactive shell
python

# Run script
python script.py

# Install packages
pip install requests

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Python #Termux #PythonTutorial #TermuxPython #LearnPython #PythonBasics #T3rmuxk1ng #TermuxCourse #Programming #PythonHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on systems you have permission to test.
```

### Tags List

```
python, python tutorial, python basics, python for beginners,
termux python, python in termux, learn python, python hindi,
python crash course, python programming, python variables,
python data types, python lists, python dictionaries,
python functions, python loops, python if else,
termux programming, termux tutorial, termux course,
t3rmuxk1ng, python course hindi, python termux hindi
```

### Hashtags

```
#Python #PythonTutorial #PythonBasics #LearnPython #PythonHindi
#Termux #TermuxPython #TermuxCourse #Programming #Coding
#PythonForBeginners #PythonProgramming #T3rmuxk1ng
#PythonCourse #TermuxHindi #LearnToCode
```

---

## 📚 ADDITIONAL RESOURCES

### Official Python Documentation

| Resource | Link |
|----------|------|
| Python Docs | https://docs.python.org/3/ |
| Python Tutorial | https://docs.python.org/3/tutorial/ |
| Python Standard Library | https://docs.python.org/3/library/ |
| Python Package Index (PyPI) | https://pypi.org/ |

### Learning Resources

| Resource | Description |
|----------|-------------|
| Python Official Tutorial | Best starting point |
| Real Python | In-depth tutorials |
| Python Crash Course | Book by Eric Matthes |
| Automate the Boring Stuff | Free online book |
| Codecademy Python | Interactive lessons |

### Termux-Specific Resources

| Resource | Description |
|----------|-------------|
| Termux Python Wiki | Termux-specific Python info |
| Termux:API Docs | API documentation |
| termux-python-packages | Pre-built packages |

### Useful Python Packages for Termux

```bash
# Web requests
pip install requests

# Web scraping
pip install beautifulsoup4
pip install lxml

# Data processing
pip install pandas
pip install numpy

# JSON/YAML
pip install pyyaml

# Encryption
pip install cryptography

# Network tools
pip install python-nmap
pip install scapy

# Image processing
pip install pillow

# Text processing
pip install python-dateutil

# Progress bars
pip install tqdm

# Terminal colors
pip install colorama
pip install rich
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 13, verify:

- [ ] Python installed and working (`python --version`)
- [ ] Understand variables and data types
- [ ] Can work with strings, lists, dictionaries
- [ ] Can use if/elif/else for control flow
- [ ] Can write for and while loops
- [ ] Can create and use functions
- [ ] Can read and write files
- [ ] Can import and use modules
- [ ] Can run shell commands with subprocess
- [ ] Created at least one Python script
- [ ] Completed at least 2 practice exercises

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 13: Bash Scripting Basics**

- What is Bash scripting
- Variables and user input
- Conditional statements
- Loops in Bash
- Functions in Bash
- Command line arguments
- Real-world script examples
- Automating tasks in Termux

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
