```
 ██████╗██╗  ██╗███████╗███╗   ███╗██╗   ██╗███████╗████████╗███████╗██████╗ 
██╔════╝██║  ██║██╔════╝████╗ ████║██║   ██║██╔════╝╚══██╔══╝██╔════╝██╔══██╗
██║     ███████║█████╗  ██╔████╔██║██║   ██║███████╗   ██║   █████╗  ██████╔╝
██║     ██╔══██║██╔══╝  ██║╚██╔╝██║██║   ██║╚════██║   ██║   ██╔══╝  ██╔══██╗
╚██████╗██║  ██║███████╗██║ ╚═╝ ██║╚██████╔╝███████║   ██║   ███████╗██║  ██║
 ╚═════╝╚═╝  ╚═╝╚══════╝╚═╝     ╚═╝ ╚═════╝ ╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝
                                                                              
 ██████╗ ██████╗  ██████╗ ██╗  ██╗██╗   ██╗    ███╗   ██╗ ██████╗ ██████╗ ███████╗
██╔════╝ ██╔══██╗██╔═══██╗╚██╗██╔╝╚██╗ ██╔╝    ████╗  ██║██╔════╝██╔═══██╗██╔════╝
██║  ███╗██████╔╝██║   ██║ ╚███╔╝  ╚████╔╝     ██╔██╗ ██║██║     ██║   ██║█████╗  
██║   ██║██╔══██╗██║   ██║ ██╔██╗   ╚██╔╝      ██║╚██╗██║██║     ██║   ██║██╔══╝  
╚██████╔╝██║  ██║╚██████╔╝██╔╝ ██╗   ██║       ██║ ╚████║╚██████╗╚██████╔╝███████╗
 ╚═════╝ ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝   ╚═╝       ╚═╝  ╚═══╝ ╚═════╝ ╚═════╝ ╚══════╝
                                                                              
 ██████╗ ██████╗  █████╗ ███╗   ███╗███████╗███████╗████████╗███████╗██████╗ 
██╔════╝██╔═══██╗██╔══██╗████╗ ████║██╔════╝██╔════╝╚══██╔══╝██╔════╝██╔══██╗
██║     ██║   ██║███████║██╔████╔██║█████╗  ███████╗   ██║   █████╗  ██████╔╝
██║     ██║   ██║██╔══██║██║╚██╔╝██║██╔══╝  ╚════██║   ██║   ██╔══╝  ██╔══██╗
╚██████╗╚██████╔╝██║  ██║██║ ╚═╝ ██║███████╗███████║   ██║   ███████╗██║  ██║
 ╚═════╝ ╚═════╝ ╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝
```

# 🐍 Chapter 12: Python Basics in Termux

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

---

## 🎮 INTERACTIVE QUIZ

### Test Your Python Basics Knowledge! (15 Questions)

**Q1: What is the output of `type(3.14)`?**
- A) `<class 'int'>`
- B) `<class 'float'>`
- C) `<class 'double'>`
- D) `<class 'number'>`

<details>
<summary>🔍 Click for Answer</summary>

**B) `<class 'float'>`** - In Python, decimal numbers are of type float. There's no 'double' type in Python like in other languages.
</details>

---

**Q2: What does `len("Hello")` return?**
- A) 4
- B) 5
- C) 6
- D) Error

<details>
<summary>🔍 Click for Answer</summary>

**B) 5** - The `len()` function returns the number of characters in a string. "Hello" has 5 characters: H, e, l, l, o.
</details>

---

**Q3: Which is the correct way to create a list?**
- A) `list = (1, 2, 3)`
- B) `list = {1, 2, 3}`
- C) `list = [1, 2, 3]`
- D) `list = <1, 2, 3>`

<details>
<summary>🔍 Click for Answer</summary>

**C) `list = [1, 2, 3]`** - Lists in Python are created using square brackets `[]`. Parentheses `()` create tuples, and curly braces `{}` create sets or dictionaries.
</details>

---

**Q4: What is `my_list[-1]` if `my_list = [1, 2, 3, 4, 5]`?**
- A) 1
- B) 5
- C) Error
- D) -1

<details>
<summary>🔍 Click for Answer</summary>

**B) 5** - Negative indexing in Python starts from the end. `-1` is the last element, `-2` is second to last, etc.
</details>

---

**Q5: Which loop is used to iterate over a sequence?**
- A) `for`
- B) `while`
- C) `foreach`
- D) Both A and B

<details>
<summary>🔍 Click for Answer</summary>

**D) Both A and B** - While `for` is more common for iterating over sequences, `while` can also be used with a counter. Python doesn't have `foreach`.
</details>

---

**Q6: What is the output of `10 // 3`?**
- A) 3.33
- B) 3
- C) 4
- D) 1

<details>
<summary>🔍 Click for Answer</summary>

**B) 3** - The `//` operator performs floor division, which divides and returns the largest integer less than or equal to the result.
</details>

---

**Q7: Which statement exits a loop immediately?**
- A) `exit`
- B) `break`
- C) `stop`
- D) `return`

<details>
<summary>🔍 Click for Answer</summary>

**B) `break`** - The `break` statement immediately exits the innermost enclosing loop. `continue` skips to the next iteration.
</details>

---

**Q8: How do you define a function in Python?**
- A) `function myFunc():`
- B) `def myFunc():`
- C) `func myFunc():`
- D) `define myFunc():`

<details>
<summary>🔍 Click for Answer</summary>

**B) `def myFunc():`** - Python uses the `def` keyword to define functions, followed by the function name and parentheses.
</details>

---

**Q9: What is a dictionary in Python?**
- A) An ordered list
- B) A key-value pair collection
- C) A string manipulation tool
- D) A sorting algorithm

<details>
<summary>🔍 Click for Answer</summary>

**B) A key-value pair collection** - Dictionaries store data in key-value pairs. Keys must be unique and immutable. Example: `{"name": "John", "age": 25}`.
</details>

---

**Q10: What does `**kwargs` mean in function definition?**
- A) Keyword arguments as dictionary
- B) Variable length positional arguments
- C) Required arguments
- D) Default arguments

<details>
<summary>🔍 Click for Answer</summary>

**A) Keyword arguments as dictionary** - `**kwargs` allows a function to accept any number of keyword arguments, which are accessible as a dictionary inside the function.
</details>

---

**Q11: What is the output of `"hello".upper()`?**
- A) "hello"
- B) "Hello"
- C) "HELLO"
- D) Error

<details>
<summary>🔍 Click for Answer</summary>

**C) "HELLO"** - The `.upper()` method converts all characters in a string to uppercase.
</details>

---

**Q12: Which method adds an element to the end of a list?**
- A) `add()`
- B) `insert()`
- C) `append()`
- D) `push()`

<details>
<summary>🔍 Click for Answer</summary>

**C) `append()`** - `append()` adds an element to the end of a list. `insert()` adds at a specific position.
</details>

---

**Q13: What is the output of `bool("")`?**
- A) True
- B) False
- C) None
- D) Error

<details>
<summary>🔍 Click for Answer</summary>

**B) False** - Empty strings, empty lists, empty dictionaries, 0, and None all evaluate to False in Python.
</details>

---

**Q14: Which is correct f-string syntax?**
- A) `f"Hello {name}"`
- B) `"Hello {name}f"`
- C) `f'Hello name'`
- D) `f"Hello $(name)"`

<details>
<summary>🔍 Click for Answer</summary>

**A) `f"Hello {name}"`** - f-strings start with `f` before the quotes and variables are placed inside `{}` braces.
</details>

---

**Q15: What does `range(5)` produce?**
- A) Numbers 1 to 5
- B) Numbers 0 to 4
- C) Numbers 0 to 5
- D) Numbers 1 to 4

<details>
<summary>🔍 Click for Answer</summary>

**B) Numbers 0 to 4** - `range(5)` produces 0, 1, 2, 3, 4. Python ranges are exclusive of the stop value and start at 0 by default.
</details>

---

## 🎯 INTERVIEW QUESTIONS

### Python Basics Interview Questions (10 Questions with Detailed Answers)

**Q1: Explain the difference between mutable and immutable objects in Python.**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    MUTABLE vs IMMUTABLE OBJECTS                          │
├────────────────┬────────────────────────────────┬───────────────────────┤
│ Type           │ Mutable                        │ Immutable             │
├────────────────┼────────────────────────────────┼───────────────────────┤
│ Can Change     │ ✅ Yes                         │ ❌ No                 │
│ Examples       │ list, dict, set               │ int, str, tuple       │
│ Memory         │ Same object, changes in place │ New object on change  │
│ Hashable       │ ❌ No (can't be dict keys)    │ ✅ Yes (can be keys)  │
│ Thread-safe    │ ❌ Need locks                  │ ✅ Naturally safe     │
└────────────────┴────────────────────────────────┴───────────────────────┘

Examples:
─────────
# Mutable - same ID after modification
my_list = [1, 2, 3]
print(id(my_list))        # 140123456
my_list.append(4)
print(id(my_list))        # 140123456 (same!)

# Immutable - new ID after "modification"
my_str = "hello"
print(id(my_str))         # 140789012
my_str = my_str + " world"
print(id(my_str))         # 140789999 (different!)
```

**Key Point:** Immutable objects are safer for use as dictionary keys and in sets because their hash value never changes.
</details>

---

**Q2: What is the difference between `==` and `is` operators?**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```python
# == compares VALUES
# is compares IDENTITY (memory location)

a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)  # True - same values
print(a is b)  # False - different objects
print(a is c)  # True - same object

# Memory diagram:
# a ──────────────┐
#                 ├──► [1, 2, 3] (Object 1)
# c ──────────────┘
# b ───────────────────► [1, 2, 3] (Object 2)

# Special case - small integers are cached
x = 256
y = 256
print(x is y)  # True (cached)

x = 257
y = 257
print(x is y)  # May be False (not cached)

# Best practice:
# - Use == for value comparison
# - Use is only for None, True, False checks
if x is None:  # Correct
if x == None:  # Works but not Pythonic
```
</details>

---

**Q3: Explain list comprehension with examples.**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```python
# List comprehension - concise way to create lists

# Basic syntax: [expression for item in iterable]

# 1. Simple transformation
squares = [x**2 for x in range(10)]
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# 2. With condition (filtering)
evens = [x for x in range(20) if x % 2 == 0]
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# 3. With if-else (transformation)
labels = ["even" if x % 2 == 0 else "odd" for x in range(5)]
# ['even', 'odd', 'even', 'odd', 'even']

# 4. Nested loops (matrix flattening)
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [num for row in matrix for num in row]
# [1, 2, 3, 4, 5, 6, 7, 8, 9]

# 5. Dictionary comprehension
names = ['alice', 'bob', 'charlie']
name_lengths = {name: len(name) for name in names}
# {'alice': 5, 'bob': 3, 'charlie': 7}

# 6. Set comprehension
unique_lengths = {len(name) for name in names}
# {3, 5, 7}

# Performance tip: List comprehension is usually faster than loops
# but avoid for very complex logic - readability matters!
```
</details>

---

**Q4: What are decorators in Python?**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```python
# Decorators modify function behavior without changing the function itself

# Basic decorator structure:
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function call")
        result = func(*args, **kwargs)
        print("After function call")
        return result
    return wrapper

# Using decorator:
@my_decorator
def say_hello(name):
    print(f"Hello, {name}!")

say_hello("World")
# Output:
# Before function call
# Hello, World!
# After function call

# Practical example - timing decorator:
import time

def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end-start:.4f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
    return "Done"

# Decorators with arguments:
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(times=3)
def greet(name):
    print(f"Hi {name}!")
```
</details>

---

**Q5: Explain Python's GIL (Global Interpreter Lock).**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    GLOBAL INTERPRETER LOCK (GIL)                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  What is GIL?                                                           │
│  ─────────────                                                          │
│  • A mutex that allows only one thread to execute Python bytecode       │
│  • Present in CPython (standard Python implementation)                  │
│  • Prevents multiple threads from running Python code simultaneously    │
│                                                                          │
│  Why GIL exists?                                                        │
│  ─────────────────                                                      │
│  • Memory management in CPython is not thread-safe                      │
│  • Simplifies implementation of CPython                                │
│  • Improves performance of single-threaded programs                     │
│                                                                          │
│  Impact:                                                                │
│  ────────                                                               │
│  ✅ CPU-bound tasks: NO benefit from threading (GIL blocks)             │
│  ✅ I/O-bound tasks: Threading still useful (GIL released during I/O)   │
│                                                                          │
│  Solutions for CPU-bound parallelism:                                   │
│  ────────────────────────────────────────                               │
│  • multiprocessing module (separate processes)                          │
│  • concurrent.futures.ProcessPoolExecutor                              │
│  • asyncio for I/O-bound tasks                                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

# Example - multiprocessing bypasses GIL:
from multiprocessing import Pool

def cpu_intensive(n):
    return sum(i * i for i in range(n))

with Pool(4) as p:
    results = p.map(cpu_intensive, [10**6] * 4)
```
</details>

---

**Q6: What is the difference between `__str__` and `__repr__`?**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```python
# __str__ - for readable string representation (end users)
# __repr__ - for unambiguous representation (developers/debugging)

class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __str__(self):
        return f"{self.name} ({self.age} years old)"
    
    def __repr__(self):
        return f"Person(name='{self.name}', age={self.age})"

p = Person("Alice", 30)

print(str(p))   # Alice (30 years old)
print(repr(p))  # Person(name='Alice', age=30)

# Key differences:
# ┌────────────┬─────────────────────┬───────────────────────┐
# │ Aspect     │ __str__             │ __repr__               │
# ├────────────┼─────────────────────┼───────────────────────┤
# │ Purpose    │ User-friendly       │ Developer-friendly     │
# │ Called by  │ str(), print()      │ repr(), interactive    │
# │ Goal       │ Readable            │ Unambiguous            │
# │ Fallback   │ Uses __repr__       │ No fallback            │
# └────────────┴─────────────────────┴───────────────────────┘

# Best practice:
# - Always implement __repr__
# - Implement __str__ only if you need a user-friendly version
# - __repr__ should ideally be valid Python code to recreate object
```
</details>

---

**Q7: Explain generators and the `yield` keyword.**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```python
# Generators produce values one at a time, saving memory

# Generator function:
def countdown(n):
    while n > 0:
        yield n  # Pause and return value
        n -= 1

# Using generator:
for i in countdown(5):
    print(i)  # 5, 4, 3, 2, 1

# Memory comparison:
# List - all values in memory
big_list = [x for x in range(10**6)]  # ~8MB memory

# Generator - one value at a time
big_gen = (x for x in range(10**6))   # ~100 bytes memory!

# Generator expressions (like list comprehensions):
squares = (x**2 for x in range(10))
print(next(squares))  # 0
print(next(squares))  # 1

# Infinite generator:
def infinite_counter():
    n = 0
    while True:
        yield n
        n += 1

counter = infinite_counter()
print(next(counter))  # 0
print(next(counter))  # 1

# Pipeline with generators:
def read_lines(filename):
    with open(filename) as f:
        for line in f:
            yield line.strip()

def filter_comments(lines):
    for line in lines:
        if not line.startswith('#'):
            yield line

# Chain generators
lines = read_lines('config.txt')
filtered = filter_comments(lines)
```
</details>

---

**Q8: What is the difference between `*args` and `**kwargs`?**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```python
# *args - variable positional arguments (tuple)
# **kwargs - variable keyword arguments (dict)

def example_function(*args, **kwargs):
    print(f"args: {args}")       # Tuple
    print(f"kwargs: {kwargs}")    # Dictionary

example_function(1, 2, 3, name="Alice", age=30)
# args: (1, 2, 3)
# kwargs: {'name': 'Alice', 'age': 30}

# Practical example:
def create_element(tag, *children, **attributes):
    attrs = ' '.join(f'{k}="{v}"' for k, v in attributes.items())
    content = ''.join(str(child) for child in children)
    return f"<{tag} {attrs}>{content}</{tag}>"

html = create_element('div', 'Hello', 'World', 
                      id='container', class_='main')
# <div id="container" class="main">HelloWorld</div>

# Unpacking with * and **:
numbers = [1, 2, 3]
print(*numbers)  # 1 2 3 (unpacks list)

config = {'host': 'localhost', 'port': 8080}
connect(**config)  # Equivalent to connect(host='localhost', port=8080)

# Combining with regular parameters:
def greet(greeting, *names, punctuation='!'):
    for name in names:
        print(f"{greeting}, {name}{punctuation}")

greet("Hello", "Alice", "Bob", punctuation="?")
# Hello, Alice?
# Hello, Bob?
```
</details>

---

**Q9: How does Python handle memory management?**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PYTHON MEMORY MANAGEMENT                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. Reference Counting                                                  │
│  ─────────────────────                                                  │
│  • Every object has a reference counter                                 │
│  • Counter increases when assigned to variable                          │
│  • Counter decreases when reference is deleted                         │
│  • When counter reaches 0, memory is freed                             │
│                                                                          │
│  2. Garbage Collection (GC)                                             │
│  ───────────────────────────                                            │
│  • Handles circular references                                         │
│  • Generational (3 generations: 0, 1, 2)                               │
│  • New objects start in generation 0                                   │
│  • Surviving objects move to older generations                         │
│                                                                          │
│  3. Memory Pools ( pymalloc )                                          │
│  ───────────────────────────                                            │
│  • Small objects (< 512 bytes) use pools                               │
│  • Reduces malloc/free overhead                                        │
│  • Improves performance                                                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

import sys
import gc

# Check reference count
a = [1, 2, 3]
print(sys.getrefcount(a) - 1)  # 1 (minus the getrefcount reference)

# Force garbage collection
gc.collect()

# Disable/enable GC
gc.disable()
gc.enable()

# Get GC thresholds
print(gc.get_threshold())  # (700, 10, 10)
```
</details>

---

**Q10: What are context managers and the `with` statement?**

<details>
<summary>💡 Show Answer</summary>

**Answer:**

```python
# Context managers handle setup and cleanup automatically

# Using built-in context manager:
with open('file.txt', 'w') as f:
    f.write('Hello!')
# File automatically closed, even if exception occurs

# Creating custom context manager with class:
class Timer:
    def __enter__(self):
        import time
        self.start = time.time()
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        import time
        self.end = time.time()
        print(f"Elapsed: {self.end - self.start:.2f}s")
        return False  # Don't suppress exceptions

with Timer() as t:
    # Some code
    pass
# Elapsed: 0.00s

# Creating context manager with decorator:
from contextlib import contextmanager

@contextmanager
def file_manager(filename, mode):
    f = open(filename, mode)
    try:
        yield f
    finally:
        f.close()

# Nested context managers:
with open('in.txt') as infile, open('out.txt', 'w') as outfile:
    outfile.write(infile.read())

# Common use cases:
# - File handling (automatic close)
# - Database connections (automatic commit/rollback)
# - Locks (automatic release)
# - Timing code execution
# - Changing directories temporarily
```

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Building a Data Processing Pipeline

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                    DATA PROCESSING PIPELINE IN PYTHON                         ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  Goal: Process CSV data with multiple transformations                        ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

```python
# Data processing pipeline
import csv
from typing import List, Dict, Any

def load_csv(filename: str) -> List[Dict[str, Any]]:
    """Load CSV file into list of dictionaries."""
    with open(filename, 'r') as f:
        return list(csv.DictReader(f))

def filter_data(data: List[Dict], key: str, value: Any) -> List[Dict]:
    """Filter data by key-value pair."""
    return [row for row in data if row.get(key) == value]

def transform_data(data: List[Dict], transformations: Dict[str, callable]) -> List[Dict]:
    """Apply transformations to data."""
    result = []
    for row in data:
        new_row = row.copy()
        for key, func in transformations.items():
            if key in new_row:
                new_row[key] = func(new_row[key])
        result.append(new_row)
    return result

def aggregate_data(data: List[Dict], group_by: str, agg_key: str) -> Dict[str, float]:
    """Aggregate data by grouping."""
    groups = {}
    for row in data:
        key = row.get(group_by, 'Unknown')
        if key not in groups:
            groups[key] = []
        groups[key].append(float(row.get(agg_key, 0)))
    return {k: sum(v)/len(v) for k, v in groups.items()}

# Usage
data = load_csv('sales.csv')
filtered = filter_data(data, 'region', 'North')
transformed = transform_data(filtered, {'price': float, 'quantity': int})
summary = aggregate_data(transformed, 'product', 'price')
```

---

### Scenario 2: Error Handling in Production Code

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                    ROBUST ERROR HANDLING PATTERN                              ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  Goal: Handle multiple failure modes gracefully                               ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

```python
import logging
from functools import wraps
from typing import Callable, Any

# Setup logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s'
)
logger = logging.getLogger(__name__)

# Retry decorator
def retry(max_attempts: int = 3, delay: float = 1.0):
    def decorator(func: Callable) -> Callable:
        @wraps(func)
        def wrapper(*args, **kwargs) -> Any:
            last_exception = None
            for attempt in range(max_attempts):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    last_exception = e
                    logger.warning(
                        f"Attempt {attempt + 1}/{max_attempts} failed: {e}"
                    )
                    if attempt < max_attempts - 1:
                        import time
                        time.sleep(delay * (attempt + 1))
            raise last_exception
        return wrapper
    return decorator

# Safe operation wrapper
def safe_operation(default=None):
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            try:
                return func(*args, **kwargs)
            except Exception as e:
                logger.error(f"Error in {func.__name__}: {e}")
                return default
        return wrapper
    return decorator

# Usage
@retry(max_attempts=3)
def fetch_data(url: str) -> dict:
    import requests
    response = requests.get(url, timeout=10)
    response.raise_for_status()
    return response.json()

@safe_operation(default=[])
def process_data(data: dict) -> list:
    return [item['value'] for item in data['items']]
```

---

### Scenario 3: Configuration Management

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                    CONFIGURATION MANAGEMENT SYSTEM                            ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  Goal: Manage app configuration from multiple sources                        ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

```python
import os
import json
from dataclasses import dataclass
from typing import Optional

@dataclass
class Config:
    """Application configuration."""
    debug: bool = False
    database_url: str = "sqlite:///app.db"
    api_key: Optional[str] = None
    max_workers: int = 4
    
    @classmethod
    def from_env(cls) -> 'Config':
        """Load configuration from environment variables."""
        return cls(
            debug=os.getenv('DEBUG', 'false').lower() == 'true',
            database_url=os.getenv('DATABASE_URL', 'sqlite:///app.db'),
            api_key=os.getenv('API_KEY'),
            max_workers=int(os.getenv('MAX_WORKERS', '4'))
        )
    
    @classmethod
    def from_file(cls, filename: str) -> 'Config':
        """Load configuration from JSON file."""
        with open(filename) as f:
            data = json.load(f)
        return cls(**data)
    
    def merge(self, other: 'Config') -> 'Config':
        """Merge with another config (other takes precedence)."""
        return Config(
            debug=other.debug if other.debug != self.debug else self.debug,
            database_url=other.database_url or self.database_url,
            api_key=other.api_key or self.api_key,
            max_workers=other.max_workers or self.max_workers
        )

# Usage
# Priority: file < environment < runtime
file_config = Config.from_file('config.json')
env_config = Config.from_env()
final_config = file_config.merge(env_config)
```

---

### Scenario 4: Building a CLI Tool

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                    COMMAND LINE TOOL DEVELOPMENT                              ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  Goal: Create a professional CLI tool with argparse                          ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

```python
#!/usr/bin/env python3
"""CLI Tool for file operations."""

import argparse
import sys
from pathlib import Path

def create_parser() -> argparse.ArgumentParser:
    parser = argparse.ArgumentParser(
        prog='filetool',
        description='A powerful file manipulation CLI tool',
        epilog='Example: filetool process --input ./data --output ./out'
    )
    
    # Subcommands
    subparsers = parser.add_subparsers(dest='command', help='Available commands')
    
    # Process command
    process_parser = subparsers.add_parser('process', help='Process files')
    process_parser.add_argument('-i', '--input', required=True, type=Path,
                               help='Input directory')
    process_parser.add_argument('-o', '--output', type=Path, default=Path('.'),
                               help='Output directory')
    process_parser.add_argument('-v', '--verbose', action='store_true',
                               help='Verbose output')
    process_parser.add_argument('--format', choices=['json', 'csv', 'txt'],
                               default='json', help='Output format')
    
    # Analyze command
    analyze_parser = subparsers.add_parser('analyze', help='Analyze files')
    analyze_parser.add_argument('path', type=Path, help='Path to analyze')
    analyze_parser.add_argument('--recursive', '-r', action='store_true',
                               help='Recursive analysis')
    
    return parser

def main():
    parser = create_parser()
    args = parser.parse_args()
    
    if not args.command:
        parser.print_help()
        sys.exit(1)
    
    if args.command == 'process':
        print(f"Processing {args.input} -> {args.output}")
        if args.verbose:
            print(f"Format: {args.format}")
    
    elif args.command == 'analyze':
        print(f"Analyzing {args.path}")
        if args.recursive:
            print("Recursive mode enabled")

if __name__ == '__main__':
    main()
```

---

### Scenario 5: Working with APIs

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                    API CLIENT IMPLEMENTATION                                  ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  Goal: Create a robust API client with error handling                        ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

```python
import requests
from typing import Dict, Any, Optional
from dataclasses import dataclass
import time

@dataclass
class APIResponse:
    success: bool
    data: Any
    error: Optional[str] = None
    status_code: int = 200

class APIClient:
    """Robust API client with retries and error handling."""
    
    def __init__(self, base_url: str, api_key: str, timeout: int = 30):
        self.base_url = base_url.rstrip('/')
        self.api_key = api_key
        self.timeout = timeout
        self.session = requests.Session()
        self.session.headers.update({
            'Authorization': f'Bearer {api_key}',
            'Content-Type': 'application/json'
        })
    
    def _request(self, method: str, endpoint: str, 
                 params: Dict = None, data: Dict = None,
                 retries: int = 3) -> APIResponse:
        """Make HTTP request with retries."""
        url = f"{self.base_url}/{endpoint.lstrip('/')}"
        
        for attempt in range(retries):
            try:
                response = self.session.request(
                    method=method,
                    url=url,
                    params=params,
                    json=data,
                    timeout=self.timeout
                )
                
                if response.status_code == 429:  # Rate limited
                    wait = int(response.headers.get('Retry-After', 60))
                    time.sleep(wait)
                    continue
                
                response.raise_for_status()
                return APIResponse(
                    success=True,
                    data=response.json(),
                    status_code=response.status_code
                )
                
            except requests.exceptions.JSONDecodeError:
                return APIResponse(
                    success=False,
                    data=None,
                    error="Invalid JSON response",
                    status_code=response.status_code
                )
            except requests.exceptions.RequestException as e:
                if attempt == retries - 1:
                    return APIResponse(
                        success=False,
                        data=None,
                        error=str(e),
                        status_code=0
                    )
                time.sleep(2 ** attempt)  # Exponential backoff
        
        return APIResponse(success=False, data=None, error="Max retries exceeded")
    
    def get(self, endpoint: str, params: Dict = None) -> APIResponse:
        return self._request('GET', endpoint, params=params)
    
    def post(self, endpoint: str, data: Dict) -> APIResponse:
        return self._request('POST', endpoint, data=data)

# Usage
client = APIClient('https://api.example.com', 'your-api-key')
response = client.get('/users', params={'page': 1})
if response.success:
    print(response.data)
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: Python Data Types Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PYTHON DATA TYPES HIERARCHY                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│                           ┌───────────┐                                     │
│                           │  object   │ (Base class)                        │
│                           └─────┬─────┘                                     │
│                    ┌────────────┼────────────┐                              │
│                    │            │            │                              │
│            ┌───────▼───────┐ ┌──▼──┐ ┌──────▼──────┐                      │
│            │   Numbers     │ │  ... │ │ Collections │                      │
│            └───────┬───────┘ └─────┘ └──────┬──────┘                      │
│                    │                       │                               │
│         ┌──────────┼──────────┐    ┌───────┼───────┐                      │
│         │          │          │    │       │       │                       │
│    ┌────▼───┐ ┌────▼───┐ ┌───▼──┐ │  ┌────▼────┐ │                       │
│    │  int   │ │ float  │ │ bool │ │  │  list   │ │                       │
│    └────────┘ └────────┘ └──────┘ │  └────┬────┘ │                       │
│                                     │       │       │                       │
│         ┌───────────────┐           │  ┌────▼────┐  │                       │
│         │   complex     │           │  │  dict   │  │                       │
│         └───────────────┘           │  └────────┘  │                       │
│                                     │       │       │                       │
│                                     │  ┌────▼────┐  │                       │
│                                     │  │  set    │  │                       │
│                                     │  └────────┘  │                       │
│                                     │       │       │                       │
│                                     │  ┌────▼────┐  │                       │
│                                     └──│  tuple  │──┘                       │
│                                        └────────┘                           │
│                                                                              │
│   Immutable: int, float, complex, bool, str, tuple, frozenset, bytes       │
│   Mutable: list, dict, set, bytearray                                      │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### Diagram 2: Python Function Call Stack

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PYTHON FUNCTION CALL MECHANISM                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   Code:                          Memory:                                    │
│   ──────                         ───────                                    │
│                                                                              │
│   def outer(x):                  ┌─────────────────────┐                    │
│       y = 10                     │    Call Stack       │                    │
│       def inner(z):              ├─────────────────────┤                    │
│           return x + y + z       │                     │                    │
│       return inner(5)            │  ┌───────────────┐  │                    │
│                                  │  │ inner(5)      │  │ ◄── Current frame │
│   result = outer(3)              │  │ z=5           │  │                    │
│                                  │  │ x=3, y=10     │  │                    │
│                                  │  └───────────────┘  │                    │
│                                  │         ▲          │                    │
│                                  │         │ closure  │                    │
│                                  │  ┌──────┴────────┐ │                    │
│                                  │  │ outer(3)      │ │                    │
│                                  │  │ x=3, y=10     │ │                    │
│                                  │  └───────────────┘ │                    │
│                                  │         ▲          │                    │
│                                  │         │          │                    │
│                                  │  ┌──────┴────────┐ │                    │
│                                  │  │ __main__      │ │                    │
│                                  │  │ result=...    │ │                    │
│                                  │  └───────────────┘ │                    │
│                                  └─────────────────────┘                    │
│                                                                              │
│   Execution Flow:                                                            │
│   1. outer(3) called → new frame created with x=3                           │
│   2. y=10 assigned in outer's frame                                         │
│   3. inner(5) called → new frame with z=5                                   │
│   4. inner accesses x and y from enclosing scope (closure)                  │
│   5. Result returned up the stack, frames popped                            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### Diagram 3: Python Memory Model

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PYTHON MEMORY MODEL                                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         Stack Memory                                │   │
│   │   ─────────────────────────────────────────                        │   │
│   │   • Function calls and local variables                             │   │
│   │   • Fixed size, fast access                                        │   │
│   │   • Automatic management (LIFO)                                    │   │
│   │                                                                     │   │
│   │   Example:                                                          │   │
│   │   def func():                                                       │   │
│   │       x = 10        ← x is on stack                                │   │
│   │       y = "hello"   ← y (reference) on stack                       │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         Heap Memory                                 │   │
│   │   ─────────────────────────────────────────                        │   │
│   │   • Objects and data structures                                    │   │
│   │   • Dynamic size                                                   │   │
│   │   • Garbage collected                                              │   │
│   │                                                                     │   │
│   │   Example Objects:                                                  │   │
│   │   ┌──────────┐  ┌──────────┐  ┌──────────────────┐               │   │
│   │   │ int: 10  │  │str:"hello"│  │ list: [1,2,3]   │               │   │
│   │   │ id: 123  │  │ id: 456  │  │ id: 789         │               │   │
│   │   └──────────┘  └──────────┘  └──────────────────┘               │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    Variable Assignment                              │   │
│   │                                                                     │   │
│   │   Code:                    Memory:                                 │   │
│   │   ──────                   ───────                                 │   │
│   │   a = 10                  Stack: a → [ref to int(10)]              │   │
│   │   b = a                   Stack: b → [same ref to int(10)]         │   │
│   │   a = 20                  Stack: a → [ref to int(20)]              │   │
│   │                            Stack: b → [still ref to int(10)]       │   │
│   │                                                                     │   │
│   │   Note: Python variables are REFERENCES, not containers            │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relevance |
|---------|-------|-----------|
| Chapter 11 | Python Installation | Prerequisite - Python setup |
| Chapter 13 | Bash Scripting Basics | Combine Python with Bash |
| Chapter 14 | Advanced Bash | Python + Bash integration |
| Chapter 15 | Git Version Control | Version Python projects |
| Chapter 16 | Node.js | Compare Python vs JavaScript |
| Chapter 25 | Automation | Python automation scripts |
| Chapter 30 | Web Development | Flask/Django frameworks |

---

## 🏆 BONUS ADVANCED CONTENT

### Bonus 1: Python Iterators and Custom Iterables

```python
# Custom iterator class
class Countdown:
    def __init__(self, start):
        self.start = start
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.start <= 0:
            raise StopIteration
        self.start -= 1
        return self.start + 1

# Usage
for i in Countdown(5):
    print(i)  # 5, 4, 3, 2, 1

# Generator iterator (simpler)
def countdown_gen(n):
    while n > 0:
        yield n
        n -= 1

# Custom range-like class
class MyRange:
    def __init__(self, start, stop=None, step=1):
        if stop is None:
            stop, start = start, 0
        self.start, self.stop, self.step = start, stop, step
    
    def __iter__(self):
        current = self.start
        while current < self.stop:
            yield current
            current += self.step

# Usage
for i in MyRange(0, 10, 2):
    print(i)  # 0, 2, 4, 6, 8
```

---

### Bonus 2: Python Descriptors

```python
# Descriptor for type checking
class TypedProperty:
    def __init__(self, name, expected_type):
        self.name = name
        self.expected_type = expected_type
    
    def __get__(self, instance, owner):
        if instance is None:
            return self
        return instance.__dict__.get(self.name)
    
    def __set__(self, instance, value):
        if not isinstance(value, self.expected_type):
            raise TypeError(
                f"{self.name} must be {self.expected_type.__name__}"
            )
        instance.__dict__[self.name] = value
    
    def __delete__(self, instance):
        raise AttributeError(f"Cannot delete {self.name}")

class Person:
    name = TypedProperty('name', str)
    age = TypedProperty('age', int)
    
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Usage
p = Person("Alice", 30)
p.name = "Bob"  # OK
p.age = "thirty"  # TypeError: age must be int
```

---

### Bonus 3: Python Metaclasses

```python
# Metaclass for automatic registration
class RegisteredMeta(type):
    _registry = {}
    
    def __new__(mcs, name, bases, namespace):
        cls = super().__new__(mcs, name, bases, namespace)
        if name != 'BasePlugin':  # Don't register base class
            mcs._registry[name] = cls
        return cls
    
    @classmethod
    def get_plugins(mcs):
        return dict(mcs._registry)

class BasePlugin(metaclass=RegisteredMeta):
    """Base class for all plugins."""
    def run(self):
        raise NotImplementedError

class LoggingPlugin(BasePlugin):
    def run(self):
        print("Logging plugin running")

class CachePlugin(BasePlugin):
    def run(self):
        print("Cache plugin running")

# All plugins automatically registered
print(RegisteredMeta.get_plugins())
# {'LoggingPlugin': <class 'LoggingPlugin'>, 'CachePlugin': <class 'CachePlugin'>}

# Singleton pattern using metaclass
class SingletonMeta(type):
    _instances = {}
    
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Database(metaclass=SingletonMeta):
    def __init__(self):
        self.connection = "Connected"

# Usage
db1 = Database()
db2 = Database()
print(db1 is db2)  # True - same instance
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### ✅ Python Basics Mastery Checklist

**Variables & Data Types:**
- [ ] Understand dynamic typing
- [ ] Know basic types: int, float, str, bool
- [ ] Understand None type
- [ ] Can use type() and isinstance()

**Data Structures:**
- [ ] Create and manipulate lists
- [ ] Use tuples for immutable sequences
- [ ] Work with dictionaries
- [ ] Understand sets for unique values
- [ ] Can use list comprehensions

**Control Flow:**
- [ ] Write if/elif/else statements
- [ ] Use for loops with range()
- [ ] Write while loops
- [ ] Use break and continue
- [ ] Understand ternary operator

**Functions:**
- [ ] Define functions with def
- [ ] Use parameters and return values
- [ ] Understand default parameters
- [ ] Use *args and **kwargs
- [ ] Write lambda functions

**File Handling:**
- [ ] Open and close files properly
- [ ] Use context managers (with)
- [ ] Read and write files
- [ ] Handle JSON data

**Modules:**
- [ ] Import modules
- [ ] Use from...import
- [ ] Create your own modules
- [ ] Use standard library modules

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Use f-strings for string formatting - they're faster and more readable than `.format()` or `%` formatting.

> 💡 **Pro Tip #2:** Always use `with open()` for file handling - it automatically closes files even if an error occurs.

> 💡 **Pro Tip #3:** Use list comprehensions instead of loops for creating lists - they're more Pythonic and often faster.

> 💡 **Pro Tip #4:** Use `enumerate()` when you need both index and value in a loop - avoid manual counter variables.

> 💡 **Pro Tip #5:** Use `dict.get(key, default)` instead of direct key access to avoid KeyError exceptions.

> 💡 **Pro Tip #6:** Use `if __name__ == "__main__":` guard to make scripts both importable and executable.

> 💡 **Pro Tip #7:** Use `try/except/finally` for robust error handling - always clean up resources in `finally`.

> 💡 **Pro Tip #8:** Use `*args` and `**kwargs` for flexible function signatures - makes functions more versatile.

> 💡 **Pro Tip #9:** Use `range(len(list))` only when necessary - prefer `for item in list` or `enumerate(list)`.

> 💡 **Pro Tip #10:** Use `json.dump()` and `json.load()` with `indent=4` for readable JSON files.

---

## 🔥 REAL WORLD APPLICATIONS

### Where Python Basics Apply in Real Life

**1. Automation Scripts**
- File organization and batch renaming
- Automated backups and log rotation
- Scheduled task execution

**2. Data Processing**
- Parsing log files and extracting insights
- Converting between file formats (CSV, JSON, XML)
- Data validation and cleaning

**3. Security Tools**
- Network scanning scripts
- Password strength checkers
- Log analysis for suspicious activity

**4. Web Scraping**
- Extracting product prices from websites
- Gathering research data automatically
- Monitoring website changes

**5. System Administration**
- Server health monitoring
- User management automation
- Configuration file generation

---

## ⚡ QUICK REFERENCE CARD

### Python Basics Quick Reference

| Concept | Syntax | Example |
|---------|--------|---------|
| Variable | `name = value` | `x = 10` |
| String | `"text"` or `'text'` | `name = "Termux"` |
| f-string | `f"text {var}"` | `f"Hello {name}"` |
| List | `[1, 2, 3]` | `items = [1, 2, 3]` |
| Dict | `{"key": "val"}` | `user = {"name": "John"}` |
| If | `if condition:` | `if x > 5:` |
| Elif | `elif condition:` | `elif x == 5:` |
| Else | `else:` | `else:` |
| For | `for item in list:` | `for i in range(10):` |
| While | `while condition:` | `while x < 10:` |
| Function | `def name():` | `def greet():` |
| Return | `return value` | `return x + y` |
| Lambda | `lambda x: x*2` | `square = lambda x: x**2` |
| Import | `import module` | `import os` |
| From | `from x import y` | `from os import path` |
| Try | `try:` | `try: ... except:` |
| With | `with open() as f:` | `with open("f.txt") as f:` |
| Class | `class Name:` | `class User:` |

---

## 🏆 BONUS: ADVANCED TIPS

### Advanced Python Patterns

```python
# 1. Context Managers for Custom Resources
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()
        return False

# Usage
with FileManager('test.txt', 'w') as f:
    f.write('Hello!')

# 2. Decorators for Function Enhancement
def timer(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"{func.__name__} took {time.time()-start:.4f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)

# 3. Generator Functions for Memory Efficiency
def read_large_file(filename):
    with open(filename) as f:
        for line in f:
            yield line.strip()

# 4. Data Classes for Clean Data Structures
from dataclasses import dataclass

@dataclass
class User:
    name: str
    age: int
    active: bool = True

# 5. Async/Await for Concurrent Operations
import asyncio

async def fetch_data(url):
    await asyncio.sleep(1)  # Simulate network
    return f"Data from {url}"

async def main():
    results = await asyncio.gather(
        fetch_data("url1"),
        fetch_data("url2"),
        fetch_data("url3")
    )
    print(results)
```

### Useful Python One-Liners

```python
# Flatten a list of lists
flat = [item for sublist in nested for item in sublist]

# Get unique elements preserving order
unique = list(dict.fromkeys(duplicates))

# Most common element in list
from collections import Counter
most_common = Counter(lst).most_common(1)[0][0]

# Merge dictionaries (Python 3.9+)
merged = dict1 | dict2

# Swap variables
a, b = b, a

# Check if all elements are unique
len(lst) == len(set(lst))

# Read file into string
content = Path('file.txt').read_text()

# Chunk a list into n-sized pieces
chunks = [lst[i::n] for i in range(n)]
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ Python interactive shell (REPL) usage
- ✅ Variables and data types (str, int, float, bool, None)
- ✅ String operations and formatting with f-strings
- ✅ Numbers and mathematical operations
- ✅ Lists, tuples, dictionaries, and sets
- ✅ Control flow with if/elif/else statements
- ✅ Loops: for and while with break/continue/pass
- ✅ Functions, parameters, return values, and lambdas
- ✅ File handling: read, write, append modes
- ✅ Modules and imports for code organization
- ✅ Termux-specific Python with subprocess and os modules
- ✅ Creating executable Python scripts

### Key Takeaways

1. **Python is beginner-friendly** - Clear syntax, readable code
2. **Indentation matters** - Python uses whitespace for blocks
3. **Everything is an object** - Even functions and classes
4. **Use the standard library** - Rich set of built-in modules
5. **Practice makes perfect** - Write code, break it, fix it

---

## 🎯 INTERVIEW QUESTIONS

### Python Basics Interview Questions

**Q1: What is the difference between a list and a tuple?**

```python
# Answer:
# List: Mutable (can be changed)
my_list = [1, 2, 3]
my_list[0] = 10  # OK
my_list.append(4)  # OK

# Tuple: Immutable (cannot be changed)
my_tuple = (1, 2, 3)
my_tuple[0] = 10  # TypeError!

# When to use:
# - Lists: When you need to modify the collection
# - Tuples: For fixed data, dictionary keys, function returns
```

**Q2: Explain the difference between `==` and `is`**

```python
# Answer:
# == compares values (equality)
# is compares identity (same object in memory)

a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)  # True (same values)
print(a is b)  # False (different objects)
print(a is c)  # True (same object)
```

**Q3: What are *args and **kwargs?**

```python
# Answer:
# *args: Variable positional arguments (tuple)
# **kwargs: Variable keyword arguments (dict)

def function(*args, **kwargs):
    print(f"Args: {args}")      # (1, 2, 3)
    print(f"Kwargs: {kwargs}")  # {'a': 1, 'b': 2}

function(1, 2, 3, a=1, b=2)

# Practical use: Flexible function signatures
def log_message(*messages, level="INFO", **metadata):
    print(f"[{level}]", *messages, metadata)
```

**Q4: What is a lambda function? When would you use one?**

```python
# Answer:
# Lambda: Anonymous, single-expression function

# Regular function
def square(x):
    return x ** 2

# Lambda equivalent
square = lambda x: x ** 2

# Use cases:
# 1. Short callbacks
sorted(users, key=lambda u: u.age)

# 2. With map/filter
doubled = list(map(lambda x: x*2, numbers))
evens = list(filter(lambda x: x%2==0, numbers))

# 3. Quick transformations
df['upper'] = df['name'].apply(lambda x: x.upper())
```

**Q5: Explain list comprehension with examples**

```python
# Answer: List comprehension creates lists concisely

# Basic: squares of 0-9
squares = [x**2 for x in range(10)]

# With condition: even numbers
evens = [x for x in range(20) if x % 2 == 0]

# With transformation
upper_names = [name.upper() for name in names]

# Nested: flatten matrix
flat = [item for row in matrix for item in row]

# Dictionary comprehension
word_lengths = {word: len(word) for word in words}

# Set comprehension
unique_lengths = {len(word) for word in words}
```

**Q6: What is the difference between shallow and deep copy?**

```python
import copy

# Answer:
# Shallow copy: Creates new object, but references nested objects
# Deep copy: Creates new object and recursively copies nested objects

original = [[1, 2], [3, 4]]

shallow = original.copy()  # or list(original)
deep = copy.deepcopy(original)

original[0][0] = 'X'

print(shallow)  # [['X', 2], [3, 4]] - affected!
print(deep)     # [[1, 2], [3, 4]]   - unaffected

# Use deep copy when you need complete independence
```

**Q7: How does Python handle memory management?**

```python
# Answer:
# 1. Reference counting: Objects tracked by references
# 2. Garbage collection: Cyclic references handled
# 3. Memory pools: Small objects optimized

import sys

a = []
print(sys.getrefcount(a) - 1)  # Reference count

# Memory management best practices:
# - Use context managers (with statement)
# - Avoid circular references
# - Use generators for large data
# - Delete large objects when done
```

**Q8: Explain decorators with a practical example**

```python
# Answer: Decorators modify function behavior without changing code

def log_calls(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        result = func(*args, **kwargs)
        print(f"Finished {func.__name__}")
        return result
    return wrapper

@log_calls
def process_data(data):
    return data.upper()

# Equivalent to:
# process_data = log_calls(process_data)

# Practical uses: logging, timing, authentication, caching
```

**Q9: What is the GIL and how does it affect Python?**

```text
Answer: GIL (Global Interpreter Lock) ensures only one thread 
executes Python bytecode at a time.

Implications:
1. CPU-bound tasks don't benefit from threading
2. I/O-bound tasks can still use threading effectively
3. Multiprocessing bypasses GIL for CPU tasks

Solutions for CPU-heavy work:
- Use multiprocessing instead of threading
- Use libraries like NumPy that release GIL
- Use alternative implementations (PyPy, Cython)
```

**Q10: How do you handle exceptions properly?**

```python
# Answer: Use specific exceptions and proper cleanup

# Bad: Catching all exceptions
try:
    risky_operation()
except:
    pass  # Hides all errors!

# Good: Specific exceptions with context
try:
    result = risky_operation()
except FileNotFoundError:
    logging.error("File not found")
    raise
except PermissionError as e:
    logging.error(f"Permission denied: {e}")
    return None
except Exception as e:
    logging.exception("Unexpected error")
    raise
finally:
    cleanup()  # Always runs
```

---

## 🚀 BEST PRACTICES

### Code Style Guidelines (PEP 8)

```python
# Good: snake_case for variables and functions
user_name = "John"
def calculate_total(price, quantity):
    pass

# Good: PascalCase for classes
class UserManager:
    pass

# Good: UPPER_CASE for constants
MAX_CONNECTIONS = 100
DEFAULT_TIMEOUT = 30

# Good: Descriptive names
def get_user_by_id(user_id):
    pass

# Bad: Single letter variables (except in loops)
x = get_user_by_id(123)  # What is x?

# Good: Type hints (Python 3.5+)
def greet(name: str) -> str:
    return f"Hello, {name}"
```

### Performance Tips

```python
# Use list comprehension instead of loops
# Slow:
result = []
for x in range(1000):
    result.append(x * 2)

# Fast:
result = [x * 2 for x in range(1000)]

# Use generators for large data
# Memory heavy:
data = [x for x in range(1000000)]

# Memory efficient:
data = (x for x in range(1000000))

# Use local variables in loops
# Slow:
for i in range(len(data)):
    result.append(my_list.count(data[i]))

# Fast:
count = my_list.count
append = result.append
for item in data:
    append(count(item))

# Use set for membership tests
# Slow (O(n)):
if item in my_list:

# Fast (O(1)):
if item in my_set:
```

### Common Mistakes to Avoid

```python
# ❌ Mistake: Mutable default arguments
def add_item(item, items=[]):  # Shared across calls!
    items.append(item)
    return items

# ✅ Fix: Use None as default
def add_item(item, items=None):
    if items is None:
        items = []
    items.append(item)
    return items

# ❌ Mistake: Not closing files
f = open('file.txt')
data = f.read()
# Forgot f.close()!

# ✅ Fix: Use context manager
with open('file.txt') as f:
    data = f.read()

# ❌ Mistake: Modifying list while iterating
for item in my_list:
    if condition:
        my_list.remove(item)  # Skips items!

# ✅ Fix: Create new list or iterate copy
my_list = [item for item in my_list if not condition]
# or
for item in my_list[:]:  # Copy
    if condition:
        my_list.remove(item)
```

---

## 📊 CODE COMPARISON

### Before vs After: Python Code Quality

```python
# ❌ BEFORE: Unstructured, hard to maintain
x=10
y=20
z=x+y
print(z)
if x>5:
 print("big")
else:
 print("small")

# ✅ AFTER: Clean, maintainable, documented
def calculate_sum(a: int, b: int) -> int:
    """Calculate the sum of two numbers."""
    return a + b

def evaluate_number(number: int) -> str:
    """Evaluate if number is large or small."""
    return "large" if number > 5 else "small"

def main():
    x, y = 10, 20
    result = calculate_sum(x, y)
    print(f"Sum: {result}")
    print(f"X is {evaluate_number(x)}")

if __name__ == "__main__":
    main()
```

### Bad vs Good Practices

```python
# ❌ BAD: Nested conditionals
def process_data(data):
    if data:
        if isinstance(data, list):
            if len(data) > 0:
                for item in data:
                    if item:
                        process(item)

# ✅ GOOD: Early returns and guard clauses
def process_data(data):
    if not data:
        return
    if not isinstance(data, list):
        return
    if len(data) == 0:
        return
    
    for item in data:
        if item:
            process(item)

# ❌ BAD: String concatenation in loop
result = ""
for word in words:
    result += word + " "

# ✅ GOOD: Join method
result = " ".join(words)

# ❌ BAD: Manual index tracking
i = 0
for item in items:
    print(i, item)
    i += 1

# ✅ GOOD: Enumerate
for i, item in enumerate(items):
    print(i, item)
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relevance |
|---------|-------|-----------|
| Chapter 11 | Python Installation | Prerequisites for this chapter |
| Chapter 13 | Bash Scripting Basics | Alternative scripting approach |
| Chapter 14 | Bash Scripting Advanced | Shell scripting patterns |
| Chapter 15 | Git Version Control | Version control for Python projects |
| Chapter 16 | Node.js | JavaScript runtime comparison |
| Chapter 25 | Python for Hacking | Security applications |
| Chapter 30 | Web Scraping | Python requests & BeautifulSoup |
| Chapter 35 | API Development | Flask/Django in Termux |

---

## 🎮 INTERACTIVE QUIZ

### Quiz: Python Basics

**1. What is the output of `type([])`?**
- A) `<class 'array'>`
- B) `<class 'list'>`
- C) `<class 'tuple'>`
- D) `<class 'dict'>`

<details>
<summary>Click for Answer</summary>
**Answer: B) `<class 'list'>`**

Empty brackets `[]` create a list in Python.
</details>

**2. Which is NOT a valid way to create a dictionary?**
- A) `{}`
- B) `dict()`
- C) `{"key": "value"}`
- D) `["key": "value"]`

<details>
<summary>Click for Answer</summary>
**Answer: D) `["key": "value"]`**

Brackets `[]` are for lists, not dictionaries. Use `{}` for dicts.
</details>

**3. What does `range(5)` return?**
- A) List: `[0, 1, 2, 3, 4]`
- B) Tuple: `(0, 1, 2, 3, 4)`
- C) Range object: `range(0, 5)`
- D) Iterator

<details>
<summary>Click for Answer</summary>
**Answer: C) Range object: `range(0, 5)`**

In Python 3, `range()` returns a range object, not a list. Use `list(range(5))` to get a list.
</details>

**4. What is the output of `print("Hello"[::-1])`?**
- A) `Hello`
- B) `olleH`
- C) `H`
- D) `o`

<details>
<summary>Click for Answer</summary>
**Answer: B) `olleH`**

`[::-1]` reverses a string. Start:stop:step with -1 step reverses.
</details>

**5. Which statement exits a loop prematurely?**
- A) `exit`
- B) `break`
- C) `continue`
- D) `return`

<details>
<summary>Click for Answer</summary>
**Answer: B) `break`**

`break` exits the loop entirely. `continue` skips to next iteration.
</details>

**6. What is a lambda function?**
- A) A named function
- B) An anonymous function
- C) A recursive function
- D) A generator function

<details>
<summary>Click for Answer</summary>
**Answer: B) An anonymous function**

Lambda creates anonymous, single-expression functions.
</details>

**7. Which method adds an item to a list?**
- A) `add()`
- B) `insert()`
- C) `append()`
- D) `push()`

<details>
<summary>Click for Answer</summary>
**Answer: C) `append()`**

`append()` adds to end of list. `insert()` adds at specific index.
</details>

**8. What does `**kwargs` represent?**
- A) Variable positional arguments
- B) Variable keyword arguments
- C) Default arguments
- D) Required arguments

<details>
<summary>Click for Answer</summary>
**Answer: B) Variable keyword arguments**

`**kwargs` collects keyword arguments into a dictionary.
</details>

**9. Which is correct for reading a file?**
- A) `open('file.txt', 'r')`
- B) `read('file.txt')`
- C) `file.read('file.txt')`
- D) `open.read('file.txt')`

<details>
<summary>Click for Answer</summary>
**Answer: A) `open('file.txt', 'r')`**

Use `open()` with mode `'r'` for reading. Best with `with` statement.
</details>

**10. What is the output of `bool("")`?**
- A) `True`
- B) `False`
- C) `None`
- D) `Error`

<details>
<summary>Click for Answer</summary>
**Answer: B) `False`**

Empty strings, lists, dicts, and 0 are falsy in Python.
</details>

---

## 🔧 DEBUG THIS EXERCISES

### Debug This #1: Indentation Error

```python
# Problem: Code doesn't run
def greet(name):
print(f"Hello, {name}")
return name

# Error: IndentationError
```

<details>
<summary>Click for Solution</summary>

```python
# Solution: Python requires proper indentation
def greet(name):
    print(f"Hello, {name}")  # Indent with 4 spaces
    return name

greet("Termux")
```
</details>

### Debug This #2: Variable Scope

```python
# Problem: UnboundLocalError
count = 0

def increment():
    count += 1
    return count

print(increment())
```

<details>
<summary>Click for Solution</summary>

```python
# Solution: Use 'global' keyword for global variables
count = 0

def increment():
    global count
    count += 1
    return count

# Better solution: Avoid global variables
def increment(current_count):
    return current_count + 1

count = increment(count)
```
</details>

### Debug This #3: List Modification

```python
# Problem: Skips items during iteration
numbers = [1, 2, 3, 4, 5, 6]
for num in numbers:
    if num % 2 == 0:
        numbers.remove(num)

print(numbers)  # Expected [1, 3, 5], got something else
```

<details>
<summary>Click for Solution</summary>

```python
# Solution 1: List comprehension
numbers = [1, 2, 3, 4, 5, 6]
numbers = [num for num in numbers if num % 2 != 0]
print(numbers)  # [1, 3, 5]

# Solution 2: Iterate over copy
numbers = [1, 2, 3, 4, 5, 6]
for num in numbers[:]:  # Copy
    if num % 2 == 0:
        numbers.remove(num)
```
</details>

### Debug This #4: Mutable Default Argument

```python
# Problem: List grows unexpectedly
def add_item(item, items=[]):
    items.append(item)
    return items

print(add_item("a"))  # ['a']
print(add_item("b"))  # ['a', 'b'] - Expected ['b']!
```

<details>
<summary>Click for Solution</summary>

```python
# Solution: Use None as default
def add_item(item, items=None):
    if items is None:
        items = []
    items.append(item)
    return items

print(add_item("a"))  # ['a']
print(add_item("b"))  # ['b']
```
</details>

### Debug This #5: File Not Closing

```python
# Problem: File not closed if exception occurs
f = open('data.txt', 'w')
f.write(data)
# Exception here!
f.close()
```

<details>
<summary>Click for Solution</summary>

```python
# Solution: Use context manager
try:
    with open('data.txt', 'w') as f:
        f.write(data)
except IOError as e:
    print(f"Error writing file: {e}")

# File is automatically closed even if exception occurs
```
</details>

---

## 💻 CODING CHALLENGES

### Challenge 1: Password Generator

Create a password generator function with customizable options.

```python
# Challenge: Complete this function
import random
import string

def generate_password(length=12, include_upper=True, include_digits=True, include_special=True):
    """Generate a secure random password."""
    # Your code here
    pass

# Test cases
print(generate_password(8))
print(generate_password(16, include_special=False))
```

<details>
<summary>Click for Solution</summary>

```python
import random
import string

def generate_password(length=12, include_upper=True, include_digits=True, include_special=True):
    """Generate a secure random password."""
    characters = string.ascii_lowercase
    required = []
    
    if include_upper:
        characters += string.ascii_uppercase
        required.append(random.choice(string.ascii_uppercase))
    
    if include_digits:
        characters += string.digits
        required.append(random.choice(string.digits))
    
    if include_special:
        characters += string.punctuation
        required.append(random.choice(string.punctuation))
    
    # Generate rest of password
    remaining_length = length - len(required)
    password = required + [random.choice(characters) for _ in range(remaining_length)]
    
    # Shuffle to randomize positions
    random.shuffle(password)
    return ''.join(password)

# Test
print(generate_password(12))  # Random 12-char password
print(generate_password(16, include_special=False))  # No special chars
```
</details>

### Challenge 2: File Analyzer

Create a function that analyzes a text file and returns statistics.

```python
# Challenge: Implement this function
def analyze_file(filename):
    """
    Analyze a text file and return:
    - Line count
    - Word count
    - Character count
    - Most common word
    - Average word length
    """
    pass

# Test on any text file
```

<details>
<summary>Click for Solution</summary>

```python
from collections import Counter
import re

def analyze_file(filename):
    """Analyze a text file and return statistics."""
    with open(filename, 'r') as f:
        content = f.read()
    
    lines = content.split('\n')
    words = re.findall(r'\b\w+\b', content.lower())
    characters = len(content)
    
    word_freq = Counter(words)
    most_common_word = word_freq.most_common(1)[0] if words else None
    avg_word_length = sum(len(w) for w in words) / len(words) if words else 0
    
    return {
        'line_count': len([l for l in lines if l.strip()]),
        'word_count': len(words),
        'character_count': characters,
        'most_common_word': most_common_word,
        'average_word_length': round(avg_word_length, 2)
    }

# Test
# stats = analyze_file('sample.txt')
# print(stats)
```
</details>

### Challenge 3: Data Transformer

Create a class that transforms data between different formats.

```python
# Challenge: Implement this class
class DataTransformer:
    def __init__(self, data):
        self.data = data
    
    def to_json(self):
        """Convert data to JSON string."""
        pass
    
    def to_csv(self):
        """Convert list of dicts to CSV string."""
        pass
    
    def filter_by(self, key, value):
        """Filter data by key-value pair."""
        pass
    
    def sort_by(self, key, reverse=False):
        """Sort data by key."""
        pass

# Test with sample data
users = [
    {"name": "Alice", "age": 25, "city": "Mumbai"},
    {"name": "Bob", "age": 30, "city": "Delhi"},
    {"name": "Charlie", "age": 25, "city": "Mumbai"}
]
```

<details>
<summary>Click for Solution</summary>

```python
import json
from typing import List, Dict, Any

class DataTransformer:
    def __init__(self, data: List[Dict[str, Any]]):
        self.data = data
    
    def to_json(self, indent=2):
        """Convert data to JSON string."""
        return json.dumps(self.data, indent=indent)
    
    def to_csv(self):
        """Convert list of dicts to CSV string."""
        if not self.data:
            return ""
        
        headers = list(self.data[0].keys())
        csv_lines = [','.join(headers)]
        
        for item in self.data:
            row = [str(item.get(h, '')) for h in headers]
            csv_lines.append(','.join(row))
        
        return '\n'.join(csv_lines)
    
    def filter_by(self, key, value):
        """Filter data by key-value pair."""
        filtered = [item for item in self.data if item.get(key) == value]
        return DataTransformer(filtered)
    
    def sort_by(self, key, reverse=False):
        """Sort data by key."""
        sorted_data = sorted(self.data, key=lambda x: x.get(key, ''), reverse=reverse)
        return DataTransformer(sorted_data)
    
    def get(self):
        """Return the current data."""
        return self.data

# Test
users = [
    {"name": "Alice", "age": 25, "city": "Mumbai"},
    {"name": "Bob", "age": 30, "city": "Delhi"},
    {"name": "Charlie", "age": 25, "city": "Mumbai"}
]

transformer = DataTransformer(users)
print(transformer.filter_by('city', 'Mumbai').get())
print(transformer.sort_by('age', reverse=True).get())
print(transformer.to_csv())
```
</details>

---

*Created by T3rmuxk1ng | Termux Full Course*

---

## 🎮 INTERACTIVE QUIZ

### Test Your Python Basics Knowledge!

**Q1: What is the output of `print(type([]))`?**
- A) `<class 'list'>`
- B) `<class 'array'>`
- C) `<class 'collection'>`
- D) `<type 'list'>`

<details>
<summary>Answer</summary>
**A) `<class 'list'>`** - Empty brackets create a list, and `type()` returns the class type.
</details>

---

**Q2: Which is NOT a valid variable name in Python?**
- A) `_myvar`
- B) `myVar123`
- C) `123myvar`
- D) `my_var`

<details>
<summary>Answer</summary>
**C) `123myvar`** - Variable names cannot start with a number in Python.
</details>

---

**Q3: What does `2 ** 3` return?**
- A) 6
- B) 8
- C) 5
- D) Error

<details>
<summary>Answer</summary>
**B) 8** - The `**` operator is exponentiation: 2 to the power of 3 = 8.
</details>

---

**Q4: What is the output of `print("Hello"[::-1])`?**
- A) `Hello`
- B) `olleH`
- C) `HelloHello`
- D) Error

<details>
<summary>Answer</summary>
**B) `olleH`** - Slicing with step -1 reverses the string.
</details>

---

**Q5: Which data structure is immutable?**
- A) List
- B) Dictionary
- C) Tuple
- D) Set

<details>
<summary>Answer</summary>
**C) Tuple** - Tuples cannot be modified after creation, making them immutable.
</details>

---

**Q6: What does `range(5)` produce?**
- A) 0, 1, 2, 3, 4, 5
- B) 0, 1, 2, 3, 4
- C) 1, 2, 3, 4, 5
- D) 1, 2, 3, 4

<details>
<summary>Answer</summary>
**B) 0, 1, 2, 3, 4** - range(5) produces numbers from 0 to 4 (5 is exclusive).
</details>

---

**Q7: How do you create an empty dictionary?**
- A) `[]`
- B) `{}`
- C) `()`
- D) `{}`

<details>
<summary>Answer</summary>
**B) `{}`** - Curly braces create a dictionary. `[]` creates a list, `()` creates a tuple.
</details>

---

**Q8: What is the output of `bool(0)`?**
- A) `True`
- B) `False`
- C) `0`
- D) Error

<details>
<summary>Answer</summary>
**B) `False`** - Zero is falsy in Python. All non-zero numbers are truthy.
</details>

---

**Q9: Which operator checks if two variables refer to the same object?**
- A) `==`
- B) `===`
- C) `is`
- D) `equals`

<details>
<summary>Answer</summary>
**C) `is`** - `is` checks identity (same memory location), `==` checks equality of values.
</details>

---

**Q10: What is a lambda function?**
- A) A recursive function
- B) An anonymous function
- C) A class method
- D) A built-in function

<details>
<summary>Answer</summary>
**B) An anonymous function** - Lambda creates small, nameless functions in one line.
</details>

---

**Q11: What does `break` do in a loop?**
- A) Pauses the loop
- B) Skips current iteration
- C) Exits the loop completely
- D) Restarts the loop

<details>
<summary>Answer</summary>
**C) Exits the loop completely** - `break` terminates the loop. `continue` skips to next iteration.
</details>

---

**Q12: How do you open a file for reading?**
- A) `open(file, "w")`
- B) `open(file, "r")`
- C) `read(file)`
- D) `file.open()`

<details>
<summary>Answer</summary>
**B) `open(file, "r")`** - Mode "r" is for reading. "w" is for writing.
</details>

---

## 💡 PRO TIPS

### 10 Expert Python Tips

> **💡 Pro Tip #1: Use List Comprehensions**
> Replace verbose loops with elegant one-liners:
> ```python
> # Instead of:
> squares = []
> for i in range(10):
>     squares.append(i**2)
> 
> # Use:
> squares = [i**2 for i in range(10)]
> ```

> **💡 Pro Tip #2: Use f-strings for Formatting**
> Modern Python (3.6+) uses f-strings:
> ```python
> name = "T3rmuxk1ng"
> print(f"Hello, {name}!")  # Better than %s or .format()
> ```

> **💡 Pro Tip #3: Use `with` for File Operations**
> Automatically handles file closing:
> ```python
> with open('file.txt', 'r') as f:
>     content = f.read()
> # File is automatically closed
> ```

> **💡 Pro Tip #4: Use enumerate() for Index**
> Get both index and value:
> ```python
> for i, item in enumerate(items, start=1):
>     print(f"{i}. {item}")
> ```

> **💡 Pro Tip #5: Dictionary .get() Method**
> Avoid KeyError with default values:
> ```python
> value = my_dict.get('key', 'default_value')
> ```

> **💡 Pro Tip #6: Use `in` for Membership**
> Cleaner than manual checking:
> ```python
> if item in my_list:  # Simple and readable
> if 'text' in my_string:  # Works for strings too
> ```

> **💡 Pro Tip #7: Tuple Unpacking**
> Swap variables without temp:
> ```python
> a, b = b, a  # Swap in one line!
> first, *middle, last = [1, 2, 3, 4, 5]
> ```

> **💡 Pro Tip #8: Use `any()` and `all()`**
> Check conditions across iterables:
> ```python
> if any(x > 10 for x in numbers):  # True if any matches
> if all(x > 0 for x in numbers):   # True if all match
> ```

> **💡 Pro Tip #9: Context Managers with Classes**
> Create your own context managers:
> ```python
> class Timer:
>     def __enter__(self):
>         self.start = time.time()
>         return self
>     def __exit__(self, *args):
>         print(f"Time: {time.time() - self.start:.2f}s")
> 
> with Timer():
>     # Your code here
> ```

> **💡 Pro Tip #10: Use Type Hints**
> Make code self-documenting:
> ```python
> def greet(name: str) -> str:
>     return f"Hello, {name}"
> ```

---

## 🔥 REAL WORLD USE CASES

### Practical Python Applications in Termux

**Use Case #1: Network Scanner**
```python
#!/usr/bin/env python3
import socket
import subprocess

def scan_network(target):
    """Scan a network for live hosts."""
    live_hosts = []
    for i in range(1, 255):
        host = f"{target}.{i}"
        try:
            result = subprocess.run(
                ['ping', '-c', '1', '-W', '1', host],
                capture_output=True
            )
            if result.returncode == 0:
                live_hosts.append(host)
                print(f"[+] {host} is up")
        except:
            pass
    return live_hosts

# Usage: scan_network("192.168.1")
```

**Use Case #2: Password Generator**
```python
#!/usr/bin/env python3
import random
import string

def generate_password(length=16, symbols=True):
    """Generate a secure random password."""
    chars = string.ascii_letters + string.digits
    if symbols:
        chars += "!@#$%^&*()_+-="
    
    password = ''.join(random.choice(chars) for _ in range(length))
    return password

# Generate multiple passwords
for _ in range(5):
    print(generate_password(20))
```

**Use Case #3: File Organizer**
```python
#!/usr/bin/env python3
import os
import shutil
from pathlib import Path

def organize_downloads(folder):
    """Organize files by extension."""
    extensions = {
        'Images': ['.jpg', '.png', '.gif', '.jpeg'],
        'Documents': ['.pdf', '.doc', '.txt', '.xlsx'],
        'Videos': ['.mp4', '.mkv', '.avi'],
        'Music': ['.mp3', '.wav', '.flac'],
        'Archives': ['.zip', '.rar', '.7z', '.tar']
    }
    
    for file in Path(folder).iterdir():
        if file.is_file():
            ext = file.suffix.lower()
            for category, exts in extensions.items():
                if ext in exts:
                    dest = Path(folder) / category
                    dest.mkdir(exist_ok=True)
                    shutil.move(str(file), str(dest / file.name))
                    print(f"Moved {file.name} to {category}/")
                    break

# Usage: organize_downloads("/sdcard/Download")
```

**Use Case #4: API Data Fetcher**
```python
#!/usr/bin/env python3
import requests
import json

def fetch_api_data(url, save_to_file=True):
    """Fetch data from an API and optionally save to file."""
    try:
        response = requests.get(url, timeout=10)
        response.raise_for_status()
        data = response.json()
        
        if save_to_file:
            filename = url.split('/')[-1] or 'data'
            with open(f"{filename}.json", 'w') as f:
                json.dump(data, f, indent=2)
            print(f"Saved to {filename}.json")
        
        return data
    except Exception as e:
        print(f"Error: {e}")
        return None

# Usage: fetch_api_data("https://api.github.com/users/t3rmuxk1ng")
```

**Use Case #5: Log Analyzer**
```python
#!/usr/bin/env python3
import re
from collections import Counter

def analyze_logs(logfile):
    """Analyze log file for patterns."""
    ip_pattern = r'\d+\.\d+\.\d+\.\d+'
    error_pattern = r'ERROR|WARN|CRITICAL'
    
    ips = []
    errors = []
    
    with open(logfile, 'r') as f:
        for line in f:
            ips.extend(re.findall(ip_pattern, line))
            if re.search(error_pattern, line):
                errors.append(line.strip())
    
    return {
        'top_ips': Counter(ips).most_common(10),
        'error_count': len(errors),
        'recent_errors': errors[-5:]
    }
```

---

## ⚡ QUICK REFERENCE CARD

### Data Types

| Type | Example | Mutable |
|------|---------|---------|
| int | `42` | No |
| float | `3.14` | No |
| str | `"hello"` | No |
| bool | `True`, `False` | No |
| list | `[1, 2, 3]` | Yes |
| tuple | `(1, 2, 3)` | No |
| dict | `{"key": "value"}` | Yes |
| set | `{1, 2, 3}` | Yes |

### Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `+` | Addition | `5 + 3 = 8` |
| `-` | Subtraction | `5 - 3 = 2` |
| `*` | Multiplication | `5 * 3 = 15` |
| `/` | Division | `7 / 2 = 3.5` |
| `//` | Floor Division | `7 // 2 = 3` |
| `%` | Modulus | `7 % 3 = 1` |
| `**` | Exponent | `2 ** 3 = 8` |
| `==` | Equal | `5 == 5` |
| `!=` | Not Equal | `5 != 3` |
| `and` | Logical AND | `True and False` |
| `or` | Logical OR | `True or False` |
| `not` | Logical NOT | `not True` |
| `in` | Membership | `'a' in 'abc'` |

### Control Flow

```python
# If-else
if condition:
    pass
elif condition:
    pass
else:
    pass

# For loop
for item in iterable:
    pass

# While loop
while condition:
    pass

# Try-except
try:
    pass
except Exception as e:
    pass
finally:
    pass
```

### String Methods

| Method | Description |
|--------|-------------|
| `.upper()` | Uppercase |
| `.lower()` | Lowercase |
| `.strip()` | Remove whitespace |
| `.split()` | Split to list |
| `.join()` | Join list to string |
| `.replace()` | Replace substring |
| `.find()` | Find index |
| `.format()` | Format string |
| `.startswith()` | Check prefix |
| `.endswith()` | Check suffix |

### List Methods

| Method | Description |
|--------|-------------|
| `.append(x)` | Add to end |
| `.insert(i, x)` | Insert at index |
| `.remove(x)` | Remove first x |
| `.pop()` | Remove & return last |
| `.sort()` | Sort in place |
| `.reverse()` | Reverse in place |
| `.copy()` | Shallow copy |
| `.clear()` | Remove all |

---

## 🏆 BONUS CONTENT

### Advanced Python Patterns

```python
# 1. Generator Functions (Memory Efficient)
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

# Usage: list(fibonacci(10))

# 2. Decorators
def timer(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"Time: {time.time() - start:.2f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)

# 3. Context Manager
from contextlib import contextmanager

@contextmanager
def file_manager(filename, mode):
    f = open(filename, mode)
    try:
        yield f
    finally:
        f.close()

# 4. Data Classes (Python 3.7+)
from dataclasses import dataclass

@dataclass
class User:
    name: str
    age: int
    email: str = ""

# 5. Async/Await (Python 3.5+)
import asyncio

async def fetch_data(url):
    await asyncio.sleep(1)  # Simulate async operation
    return {"url": url, "data": "response"}

async def main():
    result = await fetch_data("https://example.com")
    print(result)

# asyncio.run(main())
```

### Python One-Liners

```python
# Reverse a string
reversed_str = "hello"[::-1]

# Flatten a list
flat = [item for sublist in nested for item in sublist]

# Remove duplicates while preserving order
unique = list(dict.fromkeys(my_list))

# Check if all elements are unique
is_unique = len(my_list) == len(set(my_list))

# Most frequent element
most_common = max(set(my_list), key=my_list.count)

# Merge dictionaries (Python 3.9+)
merged = dict1 | dict2

# List to dictionary
my_dict = {k: v for k, v in zip(keys, values)}

# Read file lines to list
lines = open('file.txt').read().splitlines()

# Execute shell command
import os; os.system('ls -la')
```

---

## 📝 CHAPTER SUMMARY

### Key Takeaways

| Topic | Key Points |
|-------|------------|
| **Variables** | Dynamic typing, no declaration needed |
| **Data Types** | int, float, str, bool, list, tuple, dict, set |
| **Strings** | Immutable, sliceable, rich methods |
| **Lists** | Mutable, ordered, indexed from 0 |
| **Dictionaries** | Key-value pairs, mutable |
| **Control Flow** | if/elif/else, for, while |
| **Functions** | def, return, args, kwargs, lambda |
| **File I/O** | open(), with statement, modes r/w/a |
| **Modules** | import, from, as |

### Common Patterns

```python
# Read file
with open('file.txt') as f:
    content = f.read()

# Write file
with open('file.txt', 'w') as f:
    f.write("content")

# Loop with index
for i, item in enumerate(items):
    print(i, item)

# Safe dictionary access
value = d.get('key', default)

# List comprehension
result = [x**2 for x in range(10) if x % 2 == 0]
```

---

## 🎯 INTERVIEW QUESTIONS

### Python Basics Interview Questions

**Q1: What's the difference between `is` and `==`?**

<details>
<summary>Answer</summary>
- `==` compares values (equality)
- `is` compares identity (same object in memory)
```python
a = [1, 2, 3]
b = [1, 2, 3]
a == b  # True (same values)
a is b  # False (different objects)
```
</details>

**Q2: Explain mutable vs immutable objects.**

<details>
<summary>Answer</summary>
**Immutable**: Cannot be changed after creation (int, float, str, tuple, frozenset)
**Mutable**: Can be modified (list, dict, set)

```python
# Immutable - creates new object
s = "hello"
s = s + " world"  # New string object

# Mutable - modifies in place
l = [1, 2, 3]
l.append(4)  # Same list object modified
```
</details>

**Q3: What are *args and **kwargs?**

<details>
<summary>Answer</summary>
- `*args`: Variable positional arguments (tuple)
- `**kwargs`: Variable keyword arguments (dict)

```python
def func(*args, **kwargs):
    print(args)    # (1, 2, 3)
    print(kwargs)  # {'a': 1, 'b': 2}

func(1, 2, 3, a=1, b=2)
```
</details>

**Q4: What's the difference between `deepcopy` and `copy`?**

<details>
<summary>Answer</summary>
- `copy()`: Shallow copy - creates new container, but references same nested objects
- `deepcopy()`: Deep copy - recursively copies all nested objects

```python
import copy
original = [[1, 2], [3, 4]]
shallow = copy.copy(original)
deep = copy.deepcopy(original)

original[0][0] = 'X'
# shallow[0][0] is now 'X' (shared reference)
# deep[0][0] is still 1 (independent copy)
```
</details>

**Q5: Explain list comprehension vs generator expression.**

<details>
<summary>Answer</summary>
```python
# List comprehension - creates list in memory
squares_list = [x**2 for x in range(1000000)]  # Uses ~8MB

# Generator expression - lazy evaluation
squares_gen = (x**2 for x in range(1000000))  # Minimal memory

# Use generator for large data or single iteration
# Use list for multiple iterations or indexing
```
</details>

**Q6: What is the GIL (Global Interpreter Lock)?**

<details>
<summary>Answer</summary>
- Mutex that allows only one thread to execute Python bytecode at a time
- Affects CPU-bound multi-threaded programs
- Doesn't affect I/O-bound operations
- Use multiprocessing for CPU-intensive parallel tasks
</details>

**Q7: How does Python handle memory management?**

<details>
<summary>Answer</summary>
1. **Reference counting**: Tracks references to objects
2. **Garbage collection**: Removes unreferenced objects
3. **Memory pools**: Small objects use pymalloc allocator

```python
import sys
a = []
print(sys.getrefcount(a))  # Reference count
```
</details>

**Q8: Explain decorators with an example.**

<details>
<summary>Answer</summary>
Decorators modify function behavior without changing the function itself.

```python
def log_calls(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        result = func(*args, **kwargs)
        print(f"Finished {func.__name__}")
        return result
    return wrapper

@log_calls
def greet(name):
    return f"Hello, {name}"
```
</details>

**Q9: What are context managers?**

<details>
<summary>Answer</summary>
Objects that define `__enter__` and `__exit__` methods for resource management.

```python
with open('file.txt') as f:  # __enter__ called
    content = f.read()
# __exit__ called automatically - file closed
```
</details>

**Q10: Explain the difference between `@staticmethod` and `@classmethod`.**

<details>
<summary>Answer</summary>
- `@staticmethod`: Doesn't receive instance or class as first argument
- `@classmethod`: Receives the class as first argument (cls)

```python
class MyClass:
    @staticmethod
    def static_method():
        return "No access to self or cls"
    
    @classmethod
    def class_method(cls):
        return f"Access to class: {cls.__name__}"
```
</details>

---

## 🚀 BEST PRACTICES

### Python Style Guide (PEP 8)

```python
# ✅ GOOD: Clear naming
def calculate_total_price(items):
    total = sum(item.price for item in items)
    return total

# ❌ BAD: Unclear naming
def calc(x):
    y = 0
    for i in x:
        y = y + i.p
    return y

# ✅ GOOD: Proper spacing
result = function(arg1, arg2, kwarg=value)

# ✅ GOOD: Maximum line length 79 characters
long_string = (
    "This is a very long string that "
    "spans multiple lines for readability"
)

# ✅ GOOD: Type hints
def greet(name: str) -> str:
    return f"Hello, {name}"
```

### Common Anti-Patterns

| ❌ Anti-Pattern | ✅ Better Approach |
|----------------|-------------------|
| `from module import *` | Import specific names |
| Mutable default args | Use `None` as default |
| Bare `except:` | Catch specific exceptions |
| `eval(user_input)` | Never use eval with untrusted input |
| Global variables | Use function parameters |

### Error Handling Best Practices

```python
# ✅ GOOD: Specific exception handling
try:
    value = my_dict['key']
except KeyError:
    value = default_value

# ✅ GOOD: Context for errors
try:
    result = divide(a, b)
except ZeroDivisionError as e:
    logger.error(f"Division failed: {e}")
    raise ValueError("Cannot divide by zero") from e

# ✅ GOOD: Cleanup with finally
try:
    file = open('data.txt')
    process(file)
finally:
    file.close()

# Even better: Use context manager
with open('data.txt') as file:
    process(file)
```

---

## 📊 CODE COMPARISON

### Bad vs Good: Python Code Examples

**String Formatting**
```python
# ❌ BAD: Old style formatting
name = "John"
age = 25
print("Name: %s, Age: %d" % (name, age))

# ✅ GOOD: f-strings (Python 3.6+)
print(f"Name: {name}, Age: {age}")
```

**Loop Patterns**
```python
# ❌ BAD: Manual index tracking
i = 0
for item in items:
    print(i, item)
    i += 1

# ✅ GOOD: Using enumerate
for i, item in enumerate(items):
    print(i, item)
```

**Dictionary Access**
```python
# ❌ BAD: Can raise KeyError
value = my_dict['key']

# ✅ GOOD: Safe access with default
value = my_dict.get('key', 'default')
```

**File Handling**
```python
# ❌ BAD: Manual close, can leak resources
f = open('file.txt')
content = f.read()
f.close()

# ✅ GOOD: Context manager auto-closes
with open('file.txt') as f:
    content = f.read()
```

**List Creation**
```python
# ❌ BAD: Verbose loop
squares = []
for i in range(10):
    squares.append(i ** 2)

# ✅ GOOD: List comprehension
squares = [i ** 2 for i in range(10)]
```

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

<details>
<summary><b>Q1: Python mein variable declare karne ka sahi syntax kya hai?</b></summary>

**Options:**
- A) `var name = "John"`
- B) `name = "John"`
- C) `string name = "John"`
- D) `let name = "John"`

**Answer: B) `name = "John"`**

**Explanation:** Python dynamically typed language hai - variable type automatically detect hota hai. Koi keyword (var, let) ki zarurat nahi hoti. Just variable name, equals sign, aur value.
</details>

<details>
<summary><b>Q2: List aur Tuple mein kya main difference hai?</b></summary>

**Options:**
- A) List immutable hai, Tuple mutable
- B) List mutable hai, Tuple immutable
- C) Dono same hain
- D) List sirf numbers store karta hai

**Answer: B) List mutable hai, Tuple immutable**

**Explanation:** List `[1, 2, 3]` mein elements add, remove, modify kar sakte ho. Tuple `(1, 2, 3)` mein changes nahi kar sakte after creation. Tuple use karo jab data constant rehna chahiye.
</details>

<details>
<summary><b>Q3: `elif` keyword kahan use hota hai?</b></summary>

**Options:**
- A) For loop mein
- B) While loop mein
- C) If-else statement mein
- D) Function definition mein

**Answer: C) If-else statement mein**

**Explanation:** `elif` (else if) multiple conditions check karne ke liye use hota hai. Ye `if` aur `else` ke beech mein aata hai jab multiple conditions check karni ho.
</details>

<details>
<summary><b>Q4: Dictionary mein value access karne ka best way kya hai?</b></summary>

**Options:**
- A) `dict[key]`
- B) `dict.get(key)`
- C) `dict.value(key)`
- D) A and B dono

**Answer: D) A and B dono**

**Explanation:** `dict[key]` direct access deta hai lekin key nahi ho to error aata hai. `dict.get(key)` safe hai - key nahi ho to None return karta hai, error nahi aata.
</details>

<details>
<summary><b>Q5: List comprehension ka syntax kya hai?</b></summary>

**Options:**
- A) `[expression for item in iterable]`
- B) `for item in iterable: [expression]`
- C) `list(expression for item)`
- D) `[item for expression in iterable]`

**Answer: A) `[expression for item in iterable]`**

**Explanation:** List comprehension concise way hai list create karne ka. Example: `[x**2 for x in range(5)]` creates `[0, 1, 4, 9, 16]`.
</details>

<details>
<summary><b>Q6: Function mein default parameter kaise set karte hain?</b></summary>

**Options:**
- A) `def func(param = "default")`
- B) `def func(param := "default")`
- C) `def func(default param)`
- D) `def func(param: "default")`

**Answer: A) `def func(param = "default")`**

**Explanation:** Default parameter function definition mein equals sign ke saath set hota hai. Agar caller value nahi deta to default use hoti hai.
</details>

<details>
<summary><b>Q7: Python mein `pass` keyword ka kya use hai?</b></summary>

**Options:**
- A) Exit the loop
- B) Skip current iteration
- C) Placeholder for empty code block
- D) Return value

**Answer: C) Placeholder for empty code block**

**Explanation:** `pass` ek null operation hai. Jab aapko empty function, class, ya loop likhna ho jo baad mein implement karenge, `pass` use karte hain syntax error se bachne ke liye.
</details>

<details>
<summary><b>Q8: `*args` function mein kya represent karta hai?</b></summary>

**Options:**
- A) Required arguments
- B) Variable positional arguments
- C) Keyword arguments
- D) Default arguments

**Answer: B) Variable positional arguments**

**Explanation:** `*args` se function ko kitne bhi positional arguments le sakte ho. Ye arguments tuple mein store hote hain. Example: `def func(*args):` - ab `func(1, 2, 3, 4)` call kar sakte ho.
</details>

<details>
<summary><b>Q9: File ko safely open karne ka best practice kya hai?</b></summary>

**Options:**
- A) `f = open('file.txt')`
- B) `with open('file.txt') as f:`
- C) `file.open('file.txt')`
- D) `open.file('file.txt')`

**Answer: B) `with open('file.txt') as f:`**

**Explanation:** `with` statement (context manager) automatically file close kar deta hai jab kaam ho jaye. Yaad se close karne ki zarurat nahi. Error aane pe bhi file close hogi.
</details>

<details>
<summary><b>Q10: String mein f-string ka kya use hai?</b></summary>

**Options:**
- A) File path represent karne ke liye
- B) Formatted string with variables
- C) Float numbers ke liye
- D) Function names ke liye

**Answer: B) Formatted string with variables**

**Explanation:** f-strings (Python 3.6+) se directly variables string mein embed kar sakte ho. Example: `name = "John"; print(f"Hello {name}")` → "Hello John". Cleaner aur faster than `.format()`.
</details>

<details>
<summary><b>Q11: `range(5)` kitne numbers generate karega?</b></summary>

**Options:**
- A) 1 se 5 tak
- B) 0 se 4 tak
- C) 0 se 5 tak
- D) 1 se 4 tak

**Answer: B) 0 se 4 tak**

**Explanation:** `range(5)` generates `[0, 1, 2, 3, 4]` - 5 numbers starting from 0. `range(start, stop)` mein stop value exclusive hai. `range(1, 5)` = `[1, 2, 3, 4]`.
</details>

<details>
<summary><b>Q12: Dictionary iterate karne ke liye kaunsa method best hai?</b></summary>

**Options:**
- A) `for key in dict:`
- B) `for key, value in dict.items():`
- C) `for value in dict.values():`
- D) All are valid

**Answer: D) All are valid**

**Explanation:** Teeno methods valid hain. A sirf keys deta hai, B keys aur values dono deta hai, C sirf values deta hai. Need ke according choose karo.
</details>

<details>
<summary><b>Q13: `break` aur `continue` mein kya farak hai?</b></summary>

**Options:**
- A) break loop exit karta hai, continue next iteration pe jata hai
- B) break pause karta hai, continue resume karta hai
- C) Dono same hain
- D) break if mein, continue loop mein use hota hai

**Answer: A) break loop exit karta hai, continue next iteration pe jata hai**

**Explanation:** `break` completely loop se bahar nikal jata hai. `continue` sirf current iteration skip karke next iteration pe jata hai, loop continue rehta hai.
</details>

<details>
<summary><b>Q14: Module import karne ka sahi syntax kya hai?</b></summary>

**Options:**
- A) `import math`
- B) `from math import sqrt`
- C) `import math as m`
- D) All are valid

**Answer: D) All are valid**

**Explanation:** Teeno valid import methods hain. A poora module import karta hai, B specific function import karta hai, C alias ke saath import karta hai. Need ke according use karo.
</details>

<details>
<summary><b>Q15: Lambda function kya hai?</b></summary>

**Options:**
- A) Named function
- B) Anonymous one-line function
- C) Recursive function
- D) Built-in function

**Answer: B) Anonymous one-line function**

**Explanation:** Lambda anonymous, single-expression function hai. Syntax: `lambda x: x * 2`. Quick functions ke liye use hota hai, especially `map()`, `filter()` ke saath.
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Q1: Python mein list aur dictionary comprehension explain karein with examples.

**Answer:**

**List Comprehension:**
```python
# Traditional way
squares = []
for i in range(10):
    squares.append(i ** 2)

# List comprehension
squares = [i ** 2 for i in range(10)]

# With condition
evens = [i for i in range(20) if i % 2 == 0]

# Nested
matrix = [[j for j in range(3)] for i in range(3)]
```

**Dictionary Comprehension:**
```python
# Create dict from lists
names = ['a', 'b', 'c']
values = [1, 2, 3]
d = {k: v for k, v in zip(names, values)}

# With condition
d = {k: v**2 for k, v in {'a': 1, 'b': 2}.items() if v > 0}
```

**Follow-up:** When would you NOT use comprehension?
- When logic is complex (> 1-2 lines)
- When debugging is needed
- When readability suffers

### Q2: Python mein shallow copy aur deep copy mein kya difference hai?

**Answer:**

```python
import copy

# Shallow Copy
original = [[1, 2], [3, 4]]
shallow = copy.copy(original)
shallow[0][0] = 999  # Affects original!

# Deep Copy
original = [[1, 2], [3, 4]]
deep = copy.deepcopy(original)
deep[0][0] = 999  # Does NOT affect original
```

| Aspect | Shallow Copy | Deep Copy |
|--------|-------------|-----------|
| Top level | Copied | Copied |
| Nested objects | Referenced | Recursively copied |
| Speed | Faster | Slower |
| Memory | Less | More |

**Use shallow when:** Nested objects should be shared
**Use deep when:** Complete independence needed

**Follow-up:** How does `list.copy()` work?
- Creates shallow copy
- Same as `copy.copy()` for lists

### Q3: Python mein *args aur **kwargs explain karein.

**Answer:**

```python
def example(*args, **kwargs):
    print(f"Args: {args}")      # Tuple
    print(f"Kwargs: {kwargs}")  # Dictionary

example(1, 2, 3, name="John", age=25)
# Args: (1, 2, 3)
# Kwargs: {'name': 'John', 'age': 25}

# Real-world usage
def log_message(*args, **kwargs):
    timestamp = kwargs.get('timestamp', 'now')
    level = kwargs.get('level', 'INFO')
    message = ' '.join(str(arg) for arg in args)
    print(f"[{timestamp}] {level}: {message}")

log_message("User", "logged in", level="DEBUG")
```

**Best Practices:**
1. Use `*args` for variable positional args
2. Use `**kwargs` for optional named args
3. Order: `def func(pos, *args, named, **kwargs)`

**Follow-up:** Can you have multiple *args?
- No, only one `*args` and one `**kwargs` allowed

### Q4: Python mein context managers (with statement) kya hain?

**Answer:**

```python
# Built-in example
with open('file.txt', 'r') as f:
    content = f.read()
# File automatically closed

# Custom context manager
class Timer:
    def __enter__(self):
        import time
        self.start = time.time()
        return self
    
    def __exit__(self, *args):
        import time
        self.end = time.time()
        print(f"Elapsed: {self.end - self.start:.2f}s")

with Timer():
    # Some operation
    sum(range(1000000))
```

**Using contextlib:**
```python
from contextlib import contextmanager

@contextmanager
def timer():
    import time
    start = time.time()
    yield
    print(f"Elapsed: {time.time() - start:.2f}s")

with timer():
    sum(range(1000000))
```

**Follow-up:** Why use context managers?
- Resource management (files, connections)
- Exception safety
- Clean code pattern

### Q5: Python GIL (Global Interpreter Lock) kya hai?

**Answer:**

**GIL ek mutex hai jo Python objects ko protect karta hai:**
- Sirf ek thread execute kar sakta hai Python bytecode
- CPU-bound tasks mein threading effective nahi
- I/O-bound tasks mein threading works fine

**Solutions for CPU-bound:**
```python
# Multiprocessing (bypasses GIL)
from multiprocessing import Pool

def cpu_task(n):
    return sum(i * i for i in range(n))

with Pool(4) as p:
    results = p.map(cpu_task, [1000000] * 4)

# Or use asyncio for I/O
import asyncio

async def fetch(url):
    # I/O operation
    pass
```

**When GIL is okay:**
- Web servers (I/O bound)
- Data processing
- Scripting tasks

**Follow-up:** Which Python implementations don't have GIL?
- Jython (Java)
- IronPython (.NET)
- PyPy (with STM)

### Q6: Python mein decorators kya hote hain?

**Answer:**

```python
# Basic decorator
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function")
        result = func(*args, **kwargs)
        print("After function")
        return result
    return wrapper

@my_decorator
def say_hello(name):
    print(f"Hello, {name}!")

# Decorator with arguments
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(times=3)
def greet():
    print("Hi!")

# Practical example
import time

def timing(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"{func.__name__} took {time.time()-start:.2f}s")
        return result
    return wrapper
```

**Follow-up:** Common built-in decorators?
- `@property`, `@staticmethod`, `@classmethod`
- `@functools.lru_cache`
- `@contextlib.contextmanager`

### Q7: Python mein exception handling best practices kya hain?

**Answer:**

```python
# Good: Specific exceptions
try:
    result = 10 / x
except ZeroDivisionError:
    result = 0
except ValueError as e:
    print(f"Invalid value: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
    raise  # Re-raise for logging
finally:
    print("Cleanup")

# Better: Context manager
try:
    with open('file.txt') as f:
        content = f.read()
except FileNotFoundError:
    content = ""

# Custom exception
class ValidationError(Exception):
    def __init__(self, field, message):
        self.field = field
        self.message = message
        super().__init__(f"{field}: {message}")

# Raise with context
raise ValueError("Invalid input") from original_error
```

**Best Practices:**
1. Catch specific exceptions, not bare `except:`
2. Use `finally` for cleanup
3. Don't suppress errors silently
4. Log exceptions with context

**Follow-up:** What is exception chaining?
- `raise NewError() from OriginalError`
- Preserves original traceback

### Q8: Python iterators aur generators mein kya difference hai?

**Answer:**

**Iterator:**
```python
class CountIterator:
    def __init__(self, n):
        self.n = n
        self.current = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current < self.n:
            self.current += 1
            return self.current
        raise StopIteration
```

**Generator (simpler):**
```python
def count_generator(n):
    current = 0
    while current < n:
        current += 1
        yield current

# Generator expression
squares = (x**2 for x in range(10))

# Memory efficient
def infinite_stream():
    n = 0
    while True:
        yield n
        n += 1
```

| Aspect | Iterator | Generator |
|--------|----------|-----------|
| Syntax | Class based | Function with yield |
| State | Manual tracking | Automatic |
| Memory | Depends on implementation | Minimal |
| Use case | Complex state | Simple sequences |

**Follow-up:** What is `yield from`?
- Delegates to another generator
- `yield from another_generator()`

### Q9: Python mein data classes kya hain?

**Answer:**

```python
from dataclasses import dataclass
from typing import List

@dataclass
class Person:
    name: str
    age: int
    skills: List[str] = None
    
    def __post_init__(self):
        if self.skills is None:
            self.skills = []
    
    def introduce(self):
        return f"I'm {self.name}, {self.age} years old"

# Auto-generated: __init__, __repr__, __eq__
p1 = Person("Alice", 30, ["Python", "Bash"])
p2 = Person("Bob", 25)
print(p1)  # Person(name='Alice', age=30, skills=['Python', 'Bash'])

# Frozen (immutable)
@dataclass(frozen=True)
class Point:
    x: int
    y: int

# With ordering
@dataclass(order=True)
class Student:
    grade: int
    name: str
```

**Benefits over regular class:**
- Less boilerplate
- Auto `__init__`, `__repr__`, `__eq__`
- Type hints enforced (with type checkers)
- Easy to read

**Follow-up:** When to use vs NamedTuple?
- Dataclass: Mutable, methods needed
- NamedTuple: Immutable, simple data

### Q10: Python mein type hints ka purpose kya hai?

**Answer:**

```python
from typing import List, Dict, Optional, Union, Callable

# Basic types
def greet(name: str) -> str:
    return f"Hello, {name}"

# Collections
def process(items: List[int]) -> Dict[str, int]:
    return {"count": len(items), "sum": sum(items)}

# Optional (can be None)
def find_user(id: int) -> Optional[str]:
    if id > 0:
        return "User"
    return None

# Union types
def parse(value: Union[str, int]) -> int:
    return int(value)

# Callable
def apply(func: Callable[[int], int], value: int) -> int:
    return func(value)

# Type aliases
UserId = int
UserName = str
User = Dict[UserId, UserName]

# Generic
from typing import TypeVar, Generic

T = TypeVar('T')

class Stack(Generic[T]):
    def __init__(self) -> None:
        self.items: List[T] = []
```

**Tools for type checking:**
- `mypy` - Static type checker
- `pyright` - Microsoft's checker
- IDE support (VS Code, PyCharm)

**Follow-up:** Are types enforced at runtime?
- No, they're hints for static analysis
- Use `typing.get_type_hints()` to access them

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: 📊 Data Processing Script

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                      DATA PROCESSING SCRIPT                                  ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  SITUATION: Process CSV file and generate summary report                    ║
║                                                                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  Code:                                                                       ║
║                                                                              ║
║  import csv                                                                  ║
║  from collections import defaultdict                                        ║
║  from typing import Dict, List                                              ║
║                                                                              ║
║  def process_csv(filename: str) -> Dict[str, float]:                        ║
║      """Process CSV and return column statistics"""                         ║
║      data = defaultdict(list)                                               ║
║                                                                              ║
║      with open(filename, 'r') as f:                                         ║
║          reader = csv.DictReader(f)                                         ║
║          for row in reader:                                                  ║
║              for key, value in row.items():                                 ║
║                  try:                                                        ║
║                      data[key].append(float(value))                         ║
║                  except ValueError:                                         ║
║                      pass                                                    ║
║                                                                              ║
║      stats = {}                                                              ║
║      for key, values in data.items():                                       ║
║          if values:                                                          ║
║              stats[f"{key}_avg"] = sum(values) / len(values)                ║
║              stats[f"{key}_max"] = max(values)                              ║
║              stats[f"{key}_min"] = min(values)                              ║
║                                                                              ║
║      return stats                                                            ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: 🌐 API Client Wrapper

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                         API CLIENT WRAPPER                                   ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  SITUATION: Create a reusable API client class for Termux                   ║
║                                                                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  Code:                                                                       ║
║                                                                              ║
║  import requests                                                             ║
║  from typing import Dict, Any, Optional                                     ║
║  from dataclasses import dataclass                                          ║
║                                                                              ║
║  @dataclass                                                                  ║
║  class APIResponse:                                                          ║
║      status: int                                                             ║
║      data: Dict[str, Any]                                                    ║
║      success: bool                                                           ║
║                                                                              ║
║  class APIClient:                                                            ║
║      def __init__(self, base_url: str, timeout: int = 30):                  ║
║          self.base_url = base_url.rstrip('/')                               ║
║          self.timeout = timeout                                              ║
║          self.session = requests.Session()                                   ║
║                                                                              ║
║      def get(self, endpoint: str, params: Dict = None) -> APIResponse:     ║
║          url = f"{self.base_url}/{endpoint.lstrip('/')}"                    ║
║          try:                                                                ║
║              response = self.session.get(url, params=params,               ║
║                                       timeout=self.timeout)                 ║
║              return APIResponse(                                             ║
║                  status=response.status_code,                                ║
║                  data=response.json() if response.content else {},          ║
║                  success=response.ok                                         ║
║              )                                                               ║
║          except requests.RequestException as e:                             ║
║              return APIResponse(status=0, data={"error": str(e)},           ║
║                                 success=False)                              ║
║                                                                              ║
║  # Usage                                                                     ║
║  client = APIClient("https://api.github.com")                               ║
║  result = client.get("/users/t3rmuxk1ng")                                   ║
║  if result.success:                                                          ║
║      print(f"User: {result.data.get('login')}")                             ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: 📁 File Organization Tool

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                      FILE ORGANIZATION TOOL                                  ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  SITUATION: Organize files by extension in Termux downloads folder           ║
║                                                                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  Code:                                                                       ║
║                                                                              ║
║  import os                                                                   ║
║  import shutil                                                               ║
║  from pathlib import Path                                                   ║
║  from collections import defaultdict                                        ║
║                                                                              ║
║  def organize_by_extension(directory: str, dry_run: bool = False):         ║
║      """Organize files by their extensions"""                               ║
║      path = Path(directory)                                                  ║
║      if not path.exists():                                                   ║
║          print(f"Directory not found: {directory}")                         ║
║          return                                                              ║
║                                                                              ║
║      stats = defaultdict(int)                                               ║
║                                                                              ║
║      for file in path.iterdir():                                            ║
║          if file.is_file():                                                  ║
║              ext = file.suffix.lower() or 'no_extension'                    ║
║              ext = ext.lstrip('.') if ext != 'no_extension' else ext        ║
║                                                                              ║
║              # Create directory for extension                               ║
║              target_dir = path / ext                                        ║
║              if not dry_run:                                                 ║
║                  target_dir.mkdir(exist_ok=True)                            ║
║                  shutil.move(str(file), str(target_dir / file.name))        ║
║                                                                              ║
║              stats[ext] += 1                                                ║
║                                                                              ║
║      # Print statistics                                                      ║
║      print("\n📊 Organization Summary:")                                    ║
║      for ext, count in sorted(stats.items()):                               ║
║          print(f"  {ext}: {count} files")                                   ║
║      print(f"\nTotal: {sum(stats.values())} files organized")               ║
║                                                                              ║
║  # Usage in Termux                                                           ║
║  organize_by_extension("/sdcard/Download")                                  ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: 🔄 Log File Analyzer

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                       LOG FILE ANALYZER                                      ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  SITUATION: Analyze log files for errors and patterns                       ║
║                                                                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  Code:                                                                       ║
║                                                                              ║
║  import re                                                                   ║
║  from datetime import datetime                                              ║
║  from collections import Counter                                            ║
║  from typing import List, Dict                                              ║
║                                                                              ║
║  class LogAnalyzer:                                                          ║
║      def __init__(self, log_file: str):                                     ║
║          self.log_file = log_file                                            ║
║          self.errors: List[str] = []                                        ║
║          self.warnings: List[str] = []                                      ║
║          self.ip_counter: Counter = Counter()                               ║
║                                                                              ║
║      def analyze(self) -> Dict:                                             ║
║          patterns = {                                                        ║
║              'error': re.compile(r'\[ERROR\](.*)'),                         ║
║              'warning': re.compile(r'\[WARN\](.*)'),                        ║
║              'ip': re.compile(r'\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}'),     ║
║          }                                                                   ║
║                                                                              ║
║          with open(self.log_file, 'r') as f:                                ║
║              for line_num, line in enumerate(f, 1):                         ║
║                  if patterns['error'].search(line):                         ║
║                      self.errors.append(f"Line {line_num}: {line.strip()}") ║
║                  if patterns['warning'].search(line):                       ║
║                      self.warnings.append(f"Line {line_num}: {line.strip()}")║
║                  for ip in patterns['ip'].findall(line):                    ║
║                      self.ip_counter[ip] += 1                               ║
║                                                                              ║
║          return {                                                            ║
║              'total_errors': len(self.errors),                              ║
║              'total_warnings': len(self.warnings),                          ║
║              'unique_ips': len(self.ip_counter),                            ║
║              'top_ips': self.ip_counter.most_common(5),                     ║
║          }                                                                   ║
║                                                                              ║
║      def generate_report(self) -> str:                                      ║
║          results = self.analyze()                                           ║
║          report = f"""                                                       ║
║  ╔════════════════════════════════════════════════╗                         ║
║  ║           LOG ANALYSIS REPORT                   ║                         ║
║  ╠════════════════════════════════════════════════╣                         ║
║  ║ Errors:   {results['total_errors']:<37}║         ║
║  ║ Warnings: {results['total_warnings']:<37}║         ║
║  ║ Unique IPs: {results['unique_ips']:<35}║         ║
║  ╠════════════════════════════════════════════════╣                         ║
║  ║ Top IPs:                                        ║                         ║
║  """                                                                         ║
║          for ip, count in results['top_ips']:                               ║
║              report += f"  ║   {ip}: {count} times{' '*22}║\n"             ║
║          report += "  ╚════════════════════════════════════════════════╝"   ║
║          return report                                                       ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: 📱 Termux Automation Helper

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                      TERMUX AUTOMATION HELPER                                ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  SITUATION: Python helper for Termux automation tasks                       ║
║                                                                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  Code:                                                                       ║
║                                                                              ║
║  import subprocess                                                           ║
║  import json                                                                 ║
║  from typing import Dict, Any                                               ║
║                                                                              ║
║  class TermuxHelper:                                                         ║
║      """Helper class for Termux API integration"""                          ║
║                                                                              ║
║      @staticmethod                                                           ║
║      def run_cmd(command: str) -> Dict[str, Any]:                           ║
║          """Run shell command and return result"""                          ║
║          result = subprocess.run(command, shell=True,                       ║
║                                 capture_output=True, text=True)             ║
║          return {                                                            ║
║              'success': result.returncode == 0,                             ║
║              'output': result.stdout.strip(),                               ║
║              'error': result.stderr.strip()                                 ║
║          }                                                                   ║
║                                                                              ║
║      @staticmethod                                                           ║
║      def get_battery() -> Dict:                                             ║
║          """Get battery status using termux-api"""                          ║
║          result = TermuxHelper.run_cmd('termux-battery-status')             ║
║          return json.loads(result['output']) if result['success'] else {}   ║
║                                                                              ║
║      @staticmethod                                                           ║
║      def notify(title: str, message: str) -> bool:                         ║
║          """Send notification"""                                            ║
║          cmd = f'termux-notification --title "{title}" --content "{message}"'║
║          return TermuxHelper.run_cmd(cmd)['success']                        ║
║                                                                              ║
║      @staticmethod                                                           ║
║      def vibrate(duration: int = 500) -> bool:                             ║
║          """Vibrate device"""                                               ║
║          cmd = f'termux-vibrate -d {duration}'                              ║
║          return TermuxHelper.run_cmd(cmd)['success']                        ║
║                                                                              ║
║      @staticmethod                                                           ║
║      def speak(text: str) -> bool:                                         ║
║          """Text to speech"""                                               ║
║          cmd = f'termux-tts-speak "{text}"'                                 ║
║          return TermuxHelper.run_cmd(cmd)['success']                        ║
║                                                                              ║
║  # Usage examples                                                            ║
║  if __name__ == "__main__":                                                 ║
║      helper = TermuxHelper()                                                 ║
║      battery = helper.get_battery()                                          ║
║      print(f"Battery: {battery.get('percentage', 'N/A')}%")                 ║
║      helper.notify("Python", "Script completed!")                           ║
║      helper.vibrate(300)                                                     ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: Python Data Types Hierarchy

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PYTHON DATA TYPES OVERVIEW                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│                         ┌──────────────┐                                    │
│                         │  Data Types  │                                    │
│                         └──────┬───────┘                                    │
│                                │                                             │
│           ┌────────────────────┼────────────────────┐                       │
│           │                    │                    │                       │
│    ┌──────▼──────┐      ┌──────▼──────┐     ┌──────▼──────┐               │
│    │   Numeric   │      │  Sequence   │     │  Mapping    │               │
│    └──────┬──────┘      └──────┬──────┘     └──────┬──────┘               │
│           │                    │                   │                       │
│    ┌──────┴──────┐      ┌──────┴──────┐           │                       │
│    │             │      │             │           │                       │
│ ┌──▼──┐     ┌───▼───┐ ┌─▼─┐     ┌────▼────┐ ┌───▼───┐                   │
│ │ int │     │ float │ │str│     │  list   │ │ dict  │                   │
│ └─────┘     └───────┘ └───┘     │  tuple  │ └───────┘                   │
│                                 │  bytes  │                              │
│ ┌───────┐                       └─────────┘                              │
│ │complex│                                                                 │
│ └───────┘                                                                 │
│                                                                              │
│                    ┌──────────────────────┐                                │
│                    │   Boolean & None     │                                │
│                    │  bool, NoneType      │                                │
│                    └──────────────────────┘                                │
│                                                                              │
│                    ┌──────────────────────┐                                │
│                    │      Set Types       │                                │
│                    │   set, frozenset     │                                │
│                    └──────────────────────┘                                │
│                                                                              │
│   MUTABILITY:                                                               │
│   ──────────                                                                │
│   Mutable:   list, dict, set                                               │
│   Immutable: int, float, str, tuple, frozenset, bool, None                │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Python Control Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PYTHON CONTROL FLOW                                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   IF-ELIF-ELSE STATEMENT                                                    │
│   ─────────────────                                                         │
│                                                                              │
│   ┌─────────────────┐                                                      │
│   │ if condition1:  │──── True ───► [Block 1]                              │
│   └────────┬────────┘                                                      │
│            │ False                                                          │
│            ▼                                                                │
│   ┌─────────────────┐                                                      │
│   │ elif condition2:│──── True ───► [Block 2]                              │
│   └────────┬────────┘                                                      │
│            │ False                                                          │
│            ▼                                                                │
│   ┌─────────────────┐                                                      │
│   │ else:           │────────────► [Block 3]                               │
│   └─────────────────┘                                                      │
│                                                                              │
│                                                                              │
│   FOR LOOP                                                                  │
│   ────────                                                                  │
│                                                                              │
│   ┌─────────────────────────────────┐                                      │
│   │ for item in iterable:           │                                      │
│   │     ┌───────────────────────┐   │                                      │
│   │     │ Process item          │   │◄──┐                                  │
│   │     │ break ──► Exit loop   │   │   │                                  │
│   │     │ continue ──► Next item│   │   │                                  │
│   │     └───────────────────────┘   │   │                                  │
│   │ else: (runs if no break)        │   │                                  │
│   └─────────────────────────────────┘   │                                  │
│            ▲                              │                                  │
│            └────────────────────────────┘                                  │
│                                                                              │
│                                                                              │
│   WHILE LOOP                                                                │
│   ───────────                                                               │
│                                                                              │
│   ┌───────────────────────┐                                                │
│   │ while condition:      │◄──┐                                            │
│   │     [Process]         │   │ Repeat while                               │
│   │     condition is True │   │ condition is True                          │
│   └───────────────────────┘   │                                            │
│            │                  │                                            │
│            └──────────────────┘                                            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Python Function Anatomy

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PYTHON FUNCTION ANATOMY                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌────────────────────────────────────────────────────────────────────┐   │
│   │                                                                    │   │
│   │   def function_name(pos1, pos2, *args, named=None, **kwargs):     │   │
│   │   │    │   │         │     │      │        │          │            │   │
│   │   │    │   │         │     │      │        │          │            │   │
│   │   │    │   │         │     │      │        │          └─ kwargs   │   │
│   │   │    │   │         │     │      │        │                       │   │
│   │   │    │   │         │     │      │        └─ named (default)     │   │
│   │   │    │   │         │     │      │                                │   │
│   │   │    │   │         │     │      └─ keyword-only args            │   │
│   │   │    │   │         │     │                                       │   │
│   │   │    │   │         │     └─ *args (variable positional)         │   │
│   │   │    │   │         │                                            │   │
│   │   │    │   │         └─ positional arguments                     │   │
│   │   │    │   │                                                      │   │
│   │   │    │   └─ function name                                       │   │
│   │   │    │                                                          │   │
│   │   │    └─ def keyword                                             │   │
│   │   │                                                              │   │
│   │   │   """Docstring - function documentation"""                   │   │
│   │   │                                                              │   │
│   │   │   # Function body                                            │   │
│   │   │   result = process(pos1, pos2, *args, named, **kwargs)      │   │
│   │   │                                                              │   │
│   │   │   return result    # Return value                            │   │
│   │   │   # OR                                                       │   │
│   │   │   yield value      # Generator                               │   │
│   │   │                                                              │   │
│   │   └────────────────────────────────────────────────────────────────┘   │
│   │                                                                    │   │
│   └────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│   CALLING EXAMPLES:                                                         │
│   ─────────────────                                                         │
│   function_name(1, 2)                    # positional                     │
│   function_name(1, 2, 3, 4)              # with *args                     │
│   function_name(1, 2, named="value")     # with keyword                   │
│   function_name(1, 2, 3, key="val")      # all types                      │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

### Prerequisites
| Chapter | Topic | Why Important |
|---------|-------|---------------|
| **Ch 11** | **Python Installation** | Must have Python installed first |
| Ch 1 | Termux Setup | Basic environment |
| Ch 2 | Basic Commands | Terminal familiarity |

### Next Steps
| Chapter | Topic | What You'll Learn |
|---------|-------|-------------------|
| Ch 17 | Termux API with Python | Mobile-specific Python |
| Ch 22 | Automation Scripts | Practical Python automation |
| Ch 25 | Web Scraping | Data extraction |

### Advanced Topics
| Chapter | Topic | Prerequisites |
|---------|-------|---------------|
| Ch 27 | Security Tools | Python + networking |
| Ch 30 | Machine Learning | Python + math |
| Ch 35 | Web Development | Python + web basics |

---

## 🏆 BONUS ADVANCED CONTENT

### Technique 1: Async/Await for Concurrent Operations

```python
import asyncio
import aiohttp
from typing import List

async def fetch_url(session, url: str) -> dict:
    """Fetch a single URL asynchronously"""
    async with session.get(url) as response:
        return {
            'url': url,
            'status': response.status,
            'data': await response.text()
        }

async def fetch_all(urls: List[str]) -> List[dict]:
    """Fetch multiple URLs concurrently"""
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        return await asyncio.gather(*tasks)

# Usage
urls = [
    'https://api.github.com',
    'https://api.github.com/users/python',
    'https://api.github.com/repos/python/cpython'
]

results = asyncio.run(fetch_all(urls))
for r in results:
    print(f"{r['url']}: {r['status']}")
```

**Benefits:**
- Concurrent I/O operations
- Much faster than sequential requests
- Perfect for API calls, file I/O

### Technique 2: Metaclasses for Advanced Class Customization

```python
class SingletonMeta(type):
    """Metaclass for singleton pattern"""
    _instances = {}
    
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Database(metaclass=SingletonMeta):
    def __init__(self):
        self.connected = False
    
    def connect(self):
        if not self.connected:
            print("Connecting to database...")
            self.connected = True

# Usage - same instance every time
db1 = Database()
db2 = Database()
print(db1 is db2)  # True

# Registry pattern with metaclass
class PluginMeta(type):
    registry = {}
    
    def __new__(mcs, name, bases, namespace):
        cls = super().__new__(mcs, name, bases, namespace)
        if name != 'Plugin':  # Don't register base class
            mcs.registry[name] = cls
        return cls

class Plugin(metaclass=PluginMeta):
    pass

class AuthPlugin(Plugin):
    def execute(self):
        return "Authenticating..."

print(PluginMeta.registry)  # {'AuthPlugin': <class 'AuthPlugin'>}
```

### Technique 3: Descriptors for Property Validation

```python
class ValidatedAttribute:
    """Descriptor for validated attributes"""
    
    def __init__(self, name: str, type_: type, min_val=None, max_val=None):
        self.name = name
        self.type = type_
        self.min_val = min_val
        self.max_val = max_val
        self.private_name = f'_{name}'
    
    def __get__(self, obj, objtype=None):
        if obj is None:
            return self
        return getattr(obj, self.private_name, None)
    
    def __set__(self, obj, value):
        # Type validation
        if not isinstance(value, self.type):
            raise TypeError(f"{self.name} must be {self.type.__name__}")
        
        # Range validation for numbers
        if self.min_val is not None and value < self.min_val:
            raise ValueError(f"{self.name} must be >= {self.min_val}")
        if self.max_val is not None and value > self.max_val:
            raise ValueError(f"{self.name} must be <= {self.max_val}")
        
        setattr(obj, self.private_name, value)

class User:
    # Using descriptors
    age = ValidatedAttribute('age', int, min_val=0, max_val=150)
    name = ValidatedAttribute('name', str)
    
    def __init__(self, name: str, age: int):
        self.name = name
        self.age = age

# Usage
user = User("Alice", 30)
print(user.name)  # Alice

try:
    user.age = -5  # ValueError: age must be >= 0
except ValueError as e:
    print(f"Error: {e}")

try:
    user.age = "twenty"  # TypeError: age must be int
except TypeError as e:
    print(f"Error: {e}")
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### Variables & Data Types
- [ ] Understood dynamic typing in Python
- [ ] Learned int, float, str, bool types
- [ ] Practiced type conversion
- [ ] Used type() to check types

### Data Structures
- [ ] Created and manipulated lists
- [ ] Understood tuples (immutable)
- [ ] Used dictionaries for key-value data
- [ ] Worked with sets for unique items
- [ ] Applied list/dict comprehensions

### Control Flow
- [ ] Wrote if-elif-else statements
- [ ] Used for loops with range()
- [ ] Implemented while loops
- [ ] Applied break and continue
- [ ] Used ternary operators

### Functions
- [ ] Defined functions with def
- [ ] Used parameters and return values
- [ ] Implemented default parameters
- [ ] Worked with *args and **kwargs
- [ ] Created lambda functions

### File Handling
- [ ] Opened files with context manager
- [ ] Read and wrote file content
- [ ] Handled JSON data
- [ ] Used file modes correctly

### Modules & Imports
- [ ] Imported standard library modules
- [ ] Used from...import syntax
- [ ] Worked with module aliases
- [ ] Installed packages with pip

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Use list comprehensions for simple transformations, but stick to regular loops for complex logic.

> 💡 **Pro Tip #2:** Always use `with` statement for file handling - it automatically closes files even if errors occur.

> 💡 **Pro Tip #3:** Use `dict.get(key, default)` instead of `dict[key]` to avoid KeyError exceptions.

> 💡 **Pro Tip #4:** f-strings (f"{var}") are faster and more readable than `.format()` or `%` formatting.

> 💡 **Pro Tip #5:** Use `enumerate()` when you need both index and value in a loop: `for i, item in enumerate(items):`

---

*Updated by T3rmuxk1ng | Termux Full Course - Module 3: Programming*
