# 🔍 Chapter 55: Project 5 - Custom Port Scanner

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ██████╗  █████╗ ███████╗███████╗████████╗    ██████╗ ██████╗ ███████╗    ║
║   ██╔══██╗██╔══██╗██╔════╝██╔════╝╚══██╔══╝    ██╔══██╗██╔══██╗██╔════╝    ║
║   ██████╔╝███████║███████╗█████╗     ██║       ██████╔╝██████╔╝█████╗      ║
║   ██╔══██╗██╔══██║╚════██║██╔══╝     ██║       ██╔═══╝ ██╔══██╗██╔══╝      ║
║   ██║  ██║██║  ██║███████║███████╗   ██║       ██║     ██║  ██║███████╗    ║
║   ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚══════╝   ╚═╝       ╚═╝     ╚═╝  ╚═╝╚══════╝    ║
║                                                                              ║
║              🔍 PORT SCANNER 🔍                                              ║
║                    by T3rmuxk1ng                                             ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 9 - Projects  
> **Chapter:** 55 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Detailed port scanning concepts |
| Python Implementation | Socket-based scanner with threading |
| Bash Implementation | Netcat-based scanner |
| Source Code | Complete production-ready code |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 55
Title: Custom Port Scanner Banayein | Python + Bash | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum banayenge ek powerful tool - Custom Port Scanner!

Ye project aapke liye bahut important hai kyunki:
1. Aap real-world security tool banana seekhenge
2. Python aur dono approaches sikhenge
3. Multi-threading ka practical use samjhenge
4. Banner grabbing technique seekhenge

Nmap jaisa professional tool hum bhi bana sakte hain - 
apne haathon se! Chaliye shuru karte hain!

Play button dabaiye, video like karein, aur channel subscribe karein!

---

[SECTION 1: PORT SCANNING KYA HAI? - 1:00 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain - Port Scanning kya hai?

Computer networks mein, "port" ek communication endpoint hai. 
Jaise aapke ghar mein different doors hain - main door, back door, 
windows - waise hi computer ke paas 65535 ports hote hain.

Har port ek specific service ke liye hota hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON PORTS AND THEIR SERVICES                      │
├────────────┬─────────────────────┬──────────────────────────────────────┤
│ Port       │ Service             │ Description                          │
├────────────┼─────────────────────┼──────────────────────────────────────┤
│ 20, 21     │ FTP                 │ File Transfer Protocol               │
│ 22         │ SSH                 │ Secure Shell - Remote Access         │
│ 23         │ Telnet              │ Unencrypted Remote Access            │
│ 25         │ SMTP                │ Email Sending                        │
│ 53         │ DNS                 │ Domain Name System                   │
│ 80         │ HTTP                │ Web Traffic                          │
│ 110        │ POP3                │ Email Receiving                      │
│ 143        │ IMAP                │ Email Receiving                      │
│ 443        │ HTTPS               │ Secure Web Traffic                   │
│ 3306       │ MySQL               │ Database                             │
│ 3389       │ RDP                 │ Remote Desktop                       │
│ 5432       │ PostgreSQL          │ Database                             │
│ 8080       │ HTTP Proxy          │ Alternative HTTP                     │
└────────────┴─────────────────────┴──────────────────────────────────────┘

Port Scanning ka matlab hai - check karna ki target machine pe 
kaun kaun se ports open hain.

Open port ka matlab: Wo port service ke liye ready hai, 
connection accept kar sakta hai.

Closed port ka matlab: Port accessible hai lekin koi service 
nahi chal rahi.

Filtered port ka matlab: Firewall port ko block kar raha hai.

Port Scanning LEGAL hai jab aap apne systems test karein, 
ya permission le kar karein. Bina permission ke scanning 
ILLEGAL hai - yaad rakhein!

---

[SECTION 2: PORT SCANNING TYPES - 5:00 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Port Scanning ke different types hote hain:

1. TCP CONNECT SCAN (Full Open Scan)
   - Complete 3-way handshake
   - Most reliable
   - Easy to detect
   - Hum ye use karenge!

2. SYN SCAN (Half-Open / Stealth Scan)
   - Only SYN packet bhejte hain
   - Less detectable
   - Root access chahiye

3. UDP SCAN
   - UDP ports check karta hai
   - Slower, less reliable
   - DNS, SNMP ke liye useful

4. FIN, NULL, XMAS SCAN
   - Stealth techniques
   - Firewall bypass ke liye

Hum apna scanner TCP Connect Scan se banayenge kyunki:
✓ Python socket se easy hai
✓ Root ki zarurat nahi
✓ Most accurate results
✓ Beginner friendly

Three-Way Handshake yaad rakhein:

Client                    Server
  |                         |
  |------- SYN ------------>|  (Hey, can we talk?)
  |                         |
  |<---- SYN + ACK ---------|  (Sure, let's talk!)
  |                         |
  |------- ACK ------------>|  (Okay, connected!)
  |                         |
  [CONNECTION ESTABLISHED]

---

[SECTION 3: PROJECT FEATURES - 8:00 to 11:00]
─────────────────────────────────────────────────────────────────────────────

Hamare Port Scanner mein ye features honge:

┌─────────────────────────────────────────────────────────────────────────┐
│                    PORT SCANNER FEATURES                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. SINGLE HOST SCAN                                                     │
│     - Ek target ka scan                                                  │
│     - Single port ya range                                               │
│     - Example: scan 192.168.1.1 port 22                                  │
│                                                                          │
│  2. RANGE SCAN                                                           │
│     - Port range specify karein                                          │
│     - Example: 1-1000, 20-80, etc.                                       │
│     - Fast enumeration                                                   │
│                                                                          │
│  3. COMMON PORTS SCAN                                                    │
│     - Top 100 common ports                                               │
│     - Quick reconnaissance                                               │
│     - Time saving                                                        │
│                                                                          │
│  4. SERVICE DETECTION                                                    │
│     - Service name identify                                              │
│     - Version detection                                                  │
│     - Banner grabbing                                                    │
│                                                                          │
│  5. MULTI-THREADING                                                      │
│     - Fast parallel scanning                                             │
│     - Multiple ports ek saath                                            │
│     - Configurable threads                                               │
│                                                                          │
│  6. OUTPUT FORMATS                                                       │
│     - Terminal output                                                    │
│     - JSON file export                                                   │
│     - Text file report                                                   │
│                                                                          │
│  7. PROGRESS DISPLAY                                                     │
│     - Real-time progress bar                                             │
│     - Scanned ports counter                                              │
│     - ETA calculation                                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Ye features professional grade scanner banate hain!

---

[SECTION 4: PYTHON IMPLEMENTATION - 11:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Ab Python code samjhte hain. Main line by line explain karunga.

[CODE EXPLANATION]

Sabse pehle imports:

    import socket          # Network connections ke liye
    import threading       # Multi-threading ke liye
    import argparse        # Command line arguments ke liye
    from datetime import datetime   # Timestamps ke liye

Socket module Python mein network programming ka foundation hai.

Main function structure:

    def scan_port(host, port):
        try:
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.settimeout(1)
            result = sock.connect_ex((host, port))
            
            if result == 0:
                # Port is OPEN!
                service = get_service(port)
                banner = grab_banner(sock)
                print(f"[+] Port {port}: OPEN - {service}")
            
            sock.close()
        except:
            pass

Yahan:
- socket.AF_INET = IPv4 address family
- socket.SOCK_STREAM = TCP connection
- settimeout(1) = 1 second wait karo
- connect_ex = Connect attempt, returns 0 if success

Multi-threading kaise kaam karti hai:

    threads = []
    for port in range(start, end):
        t = threading.Thread(target=scan_port, args=(host, port))
        threads.append(t)
        t.start()
    
    for t in threads:
        t.join()

Har port ke liye ek separate thread banate hain - 
parallel scanning, fast results!

Banner Grabbing:

    def grab_banner(sock):
        try:
            sock.send(b'HEAD / HTTP/1.1\r\n\r\n')
            banner = sock.recv(1024).decode().strip()
            return banner
        except:
            return None

Banner se hum service version pata kar sakte hain -
useful for vulnerability assessment!

---

[SECTION 5: BASH IMPLEMENTATION - 17:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

Ab Bash version samjhte hain - Netcat ka use karke!

Netcat ke basics:

    # Check single port
    nc -zv 192.168.1.1 22
    
    # -z = Zero I/O mode (scan only)
    # -v = Verbose output

Bash script structure:

    #!/bin/bash
    
    # Port Scanner using Netcat
    # By T3rmuxk1ng
    
    HOST=$1
    START_PORT=$2
    END_PORT=$3
    
    echo "Scanning $HOST..."
    
    for port in $(seq $START_PORT $END_PORT); do
        (echo >/dev/tcp/$HOST/$port) 2>/dev/null && \
        echo "Port $port is OPEN"
    done

Yahan /dev/tcp special Bash feature hai - 
TCP connection ke liye!

Timeout handle karna:

    timeout 1 bash -c "echo >/dev/tcp/$HOST/$port" 2>/dev/null
    
    timeout command se 1 second wait karo,
    nahi to next port pe jao.

Multi-threaded Bash:

    for port in $(seq $START_PORT $END_PORT); do
        (
            timeout 1 bash -c "echo >/dev/tcp/$HOST/$port" 2>/dev/null && \
            echo "Port $port is OPEN"
        ) &
    done
    wait
    
    & se background mein run hota hai
    wait se sab complete hone ka wait karo

---

[SECTION 6: DEMO & TESTING - 21:00 to 23:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye apne scanner ko test karte hain!

[PYTHON VERSION TEST]

    python port_scanner.py -H localhost -p 1-1000
    
Output:
    [*] Scanning target: localhost
    [*] Starting scan at 2024-01-15 10:30:00
    [*] Scanning ports 1-1000
    
    [+] Port 22: OPEN - SSH
    [+] Port 80: OPEN - HTTP
    [+] Port 443: OPEN - HTTPS
    
    [*] Scan complete in 5.23 seconds
    [*] Open ports found: 3

[BASH VERSION TEST]

    bash port_scanner.sh localhost 1 100
    
Output:
    Scanning localhost ports 1-100...
    Port 22 is OPEN
    Port 80 is OPEN
    
    Scan complete!

[COMMON PORTS SCAN]

    python port_scanner.py -H 192.168.1.1 --common
    
    Scanning top 100 common ports...
    [+] Port 22: OPEN - SSH (OpenSSH 8.2)
    [+] Port 80: OPEN - HTTP (nginx/1.18.0)
    [+] Port 443: OPEN - HTTPS

---

[SECTION 7: ETHICAL USAGE & LEGAL WARNING - 23:30 to 24:30]
─────────────────────────────────────────────────────────────────────────────

⚠️ IMPORTANT: LEGAL WARNING

Port scanning SENSITIVE activity hai. Yaad rakhein:

❌ DON'T scan without permission:
   - Government websites
   - Banking systems
   - Any system you don't own
   - Critical infrastructure

✅ DO scan:
   - Your own devices
   - Your local network
   - Systems with written permission
   - Authorized penetration tests

Legal consequences:
   - Computer Fraud and Abuse Act (USA)
   - IT Act 2000 (India) Section 66
   - Similar laws worldwide

Ethical hacker ki pehchan - PERMISSION!

Hamara scanner EDUCATIONAL purpose ke liye hai.
Real security work ke liye Nmap use karein -
wo more powerful aur feature-rich hai.

---

[SECTION 8: SUMMARY & NEXT PREVIEW - 24:30 to 25:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 55 complete! Let's summarize:

✅ Port Scanning kya hai - TCP/UDP ports
✅ Scanning types - TCP Connect, SYN, etc.
✅ Python implementation - Socket + Threading
✅ Bash implementation - Netcat + /dev/tcp
✅ Banner grabbing - Service detection
✅ Multi-threading - Fast parallel scanning
✅ Output formats - Terminal, JSON, Text
✅ Ethical usage - Legal considerations

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 55 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ python port_scanner.py -H <host> -p <start-end>  │ Range scan          │
│ python port_scanner.py -H <host> --common        │ Top 100 ports       │
│ python port_scanner.py -H <host> -p 22           │ Single port         │
│ bash port_scanner.sh <host> <start> <end>        │ Bash scan           │
│ nc -zv <host> <port>                             │ Netcat check        │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 56 mein hum banayenge:
   - File Organizer Tool
   - Automatic file sorting
   - Extension-based organization

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 56!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

<details>
<summary><b>❓ Question 1: What is the range of well-known ports?</b></summary>

**Answer:** 0-1023

Well-known ports (0-1023) are reserved for standard services like SSH (22), HTTP (80), HTTPS (443). These ports require root/admin privileges to run servers on them.
</details>

<details>
<summary><b>❓ Question 2: Which Python method returns 0 on successful connection?</b></summary>

**Answer:** `socket.connect_ex()`

Unlike `socket.connect()` which raises an exception on failure, `connect_ex()` returns 0 on success and an error code otherwise. This is perfect for port scanning as it allows silent failure handling.
</details>

<details>
<summary><b>❓ Question 3: What does a "filtered" port mean?</b></summary>

**Answer:** A port blocked by a firewall

Filtered ports don't respond to scan attempts because a firewall is blocking the connection. This is different from "closed" ports which respond with a rejection.
</details>

<details>
<summary><b>❓ Question 4: Why is multi-threading used in port scanners?</b></summary>

**Answer:** For faster parallel scanning

Single-threaded scanners scan one port at a time, which is extremely slow. Multi-threading allows scanning multiple ports simultaneously, drastically reducing scan time.
</details>

<details>
<summary><b>❓ Question 5: What is banner grabbing?</b></summary>

**Answer:** Retrieving service information from an open port

Banner grabbing involves connecting to a service and reading the initial response (banner) which often contains the service name, version, and other useful information for vulnerability assessment.
</details>

<details>
<summary><b>❓ Question 6: Which port is used for SSH connections?</b></summary>

**Answer:** Port 22

SSH (Secure Shell) uses port 22 by default for encrypted remote access to systems.
</details>

<details>
<summary><b>❓ Question 7: What is a SYN scan also known as?</b></summary>

**Answer:** Half-open scan or Stealth scan

SYN scan sends only a SYN packet and analyzes the response without completing the handshake. It's called "half-open" because the connection is never fully established.
</details>

<details>
<summary><b>❓ Question 8: Why should you set a socket timeout for port scanning?</b></summary>

**Answer:** To prevent hanging on unresponsive ports

Without a timeout, the scanner would wait indefinitely for closed/filtered ports. Setting a 1-2 second timeout ensures the scan continues efficiently.
</details>

<details>
<summary><b>❓ Question 9: What is the three-way handshake in TCP?</b></summary>

**Answer:** SYN → SYN-ACK → ACK

The TCP three-way handshake establishes a connection: Client sends SYN, Server responds with SYN-ACK, Client sends ACK. Connection is then established.
</details>

<details>
<summary><b>❓ Question 10: Is port scanning legal?</b></summary>

**Answer:** Only with permission on systems you own or have authorization to test

Unauthorized port scanning can be illegal under laws like the Computer Fraud and Abuse Act (USA) or IT Act 2000 (India). Always get written permission before scanning.
</details>

<details>
<summary><b>❓ Question 11: What port does HTTPS use?</b></summary>

**Answer:** Port 443

HTTPS (HTTP Secure) uses port 443 for encrypted web traffic. It's the secure version of HTTP which uses port 80.
</details>

<details>
<summary><b>❓ Question 12: What is the difference between TCP and UDP scanning?</b></summary>

**Answer:** TCP is connection-oriented, UDP is connectionless

TCP scanning is more reliable as it gets clear responses. UDP scanning is harder because UDP doesn't guarantee delivery or responses, making it slower and less accurate.
</details>

<details>
<summary><b>❓ Question 13: What does Nmap stand for?</b></summary>

**Answer:** Network Mapper

Nmap (Network Mapper) is the industry-standard port scanning tool. Our custom scanner implements similar basic functionality.
</details>

<details>
<summary><b>❓ Question 14: What socket type is used for TCP connections?</b></summary>

**Answer:** `socket.SOCK_STREAM`

`SOCK_STREAM` provides sequenced, reliable, two-way connection-based byte streams - perfect for TCP connections.
</details>

<details>
<summary><b>❓ Question 15: What is OS fingerprinting?</b></summary>

**Answer:** Identifying the operating system based on network responses

OS fingerprinting analyzes responses to network probes to guess the target operating system. Different OSs respond differently to certain packet types.
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Question 1: Explain the difference between TCP Connect scan and SYN scan.

**Answer:**

**TCP Connect Scan:**
- Completes the full three-way handshake (SYN → SYN-ACK → ACK)
- Uses system's connect() call
- No special privileges required
- More detectable as connections are logged
- Returns reliable results

**SYN Scan:**
- Sends only SYN packet, doesn't complete handshake
- Requires raw socket access (root privileges)
- Less detectable - "stealth" scan
- Faster as it doesn't establish full connections
- Can be blocked by modern IDS/IPS

**When to use:** TCP Connect for general auditing (no root needed), SYN for penetration testing where stealth is important.

---

### Question 2: How would you optimize a port scanner for scanning large networks?

**Answer:**

1. **Threading/Async:** Use ThreadPoolExecutor with optimal worker count
2. **Timeout Optimization:** Balance between speed and accuracy (1-2 seconds)
3. **Port Selection:** Start with common ports, then expand if needed
4. **Batch Processing:** Scan in batches to manage memory
5. **Rate Limiting:** Avoid triggering IDS/IPS alerts
6. **Caching:** Cache DNS lookups for repeated targets
7. **Distributed Scanning:** Split work across multiple machines

```python
from concurrent.futures import ThreadPoolExecutor
with ThreadPoolExecutor(max_workers=100) as executor:
    results = executor.map(scan_port, port_list)
```

---

### Question 3: What security considerations should be taken when using a port scanner?

**Answer:**

**Legal Considerations:**
- Always get written authorization
- Document scope of testing
- Understand local laws (CFAA in US, IT Act in India)

**Technical Considerations:**
- Rate limiting to avoid DoS conditions
- Avoid scanning critical infrastructure
- Use test environments when possible

**Operational Security:**
- Scans can trigger security alerts
- IP addresses get logged
- May violate ISP terms of service

**Best Practices:**
- Start with common ports only
- Use appropriate timing templates
- Document all activities
- Report findings responsibly

---

### Question 4: How does a firewall affect port scanning results?

**Answer:**

**Firewall Effects on Scan Results:**

| Port State | Response | Meaning |
|------------|----------|---------|
| Open | SYN-ACK | Service running, accessible |
| Closed | RST | No service, but port reachable |
| Filtered | No response | Firewall blocking |
| Open|Filtered | No response (UDP) | Uncertain state |

**Detection Methods:**
- Compare scan results from different angles
- Use multiple scan types (TCP, UDP, SYN)
- Analyze response timing patterns
- Check for consistent "filtered" patterns

**Counter-measures:**
- Firewalls can return fake responses
- Some block all ICMP (ping)
- Rate limiting can appear as filtering

---

### Question 5: Explain how banner grabbing works and its ethical implications.

**Answer:**

**How It Works:**
```python
def grab_banner(sock):
    sock.send(b'HEAD / HTTP/1.1\r\n\r\n')
    return sock.recv(1024).decode()
```

1. Connect to open port
2. Send protocol-specific request
3. Receive service response (banner)
4. Parse for version information

**Information Revealed:**
- Service name and version
- Server type (Apache, nginx, IIS)
- Sometimes OS information
- Configuration details

**Ethical Implications:**
- Version info helps attackers find vulnerabilities
- Some consider it reconnaissance for attacks
- Others argue it's passive information gathering

**Best Practice:** Only banner grab on systems you own or have permission to test.

---

### Question 6: How would you implement service version detection?

**Answer:**

**Approach:**
1. Identify open port
2. Send protocol-specific probe
3. Analyze response pattern
4. Match against service database

```python
import re

def detect_service_version(banner):
    patterns = {
        'OpenSSH': r'OpenSSH[_-]([\d.]+p?\d*)',
        'Apache': r'Apache/([\d.]+)',
        'nginx': r'nginx/([\d.]+)',
        'MySQL': r'([\d.]+)-MariaDB|MySQL',
    }
    
    for service, pattern in patterns.items():
        match = re.search(pattern, banner, re.IGNORECASE)
        if match:
            return service, match.group(1)
    return None, None
```

**Considerations:**
- Some services hide version info
- Banners can be modified
- Multiple probes may be needed
- Protocol-specific detection required

---

### Question 7: What are the limitations of a basic port scanner compared to Nmap?

**Answer:**

**Nmap Advantages:**
1. **Scripting Engine (NSE):** 500+ scripts for vuln detection
2. **OS Detection:** TCP/IP fingerprinting
3. **Multiple Scan Types:** SYN, FIN, XMAS, NULL, Maimon
4. **Version Detection:** Comprehensive service probing
5. **Timing Templates:** T0-T5 for different scenarios
6. **Decoy Scanning:** Hide real source IP
7. **IPv6 Support:** Full IPv6 capability
8. **Firewall Evasion:** Fragmentation, timing tricks

**Basic Scanner Limitations:**
- TCP Connect only
- No OS detection
- Limited service detection
- No scripting capability
- Basic output formats

**When Basic is Enough:**
- Quick reconnaissance
- Learning network programming
- Custom integration needs
- Lightweight requirements

---

### Question 8: How do you handle scanning errors and edge cases?

**Answer:**

**Common Error Scenarios:**

```python
def safe_scan(host, port):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(2)
        result = sock.connect_ex((host, port))
        sock.close()
        return result == 0
    except socket.gaierror:
        return "Hostname resolution failed"
    except socket.error as e:
        return f"Socket error: {e}"
    except Exception as e:
        return f"Unexpected error: {e}"
```

**Edge Cases to Handle:**
1. **Invalid hostnames:** DNS resolution failures
2. **Network unreachable:** ICMP errors
3. **Connection refused:** RST packets
4. **Timeout:** Filtered ports
5. **Resource limits:** Too many threads
6. **Interrupted scans:** Graceful shutdown

**Best Practices:**
- Use try-except blocks liberally
- Log all errors for debugging
- Implement retry logic with backoff
- Clean up resources (close sockets)

---

### Question 9: Explain the concept of scan timing and why it matters.

**Answer:**

**Timing Concepts:**

| Template | Speed | Use Case |
|----------|-------|----------|
| Paranoid (T0) | Very slow | IDS evasion |
| Sneaky (T1) | Slow | Stealth |
| Polite (T2) | Moderate | Reduce load |
| Normal (T3) | Default | Standard |
| Aggressive (T4) | Fast | Trusted networks |
| Insane (T5) | Very fast | Local LAN |

**Why Timing Matters:**
1. **IDS Detection:** Fast scans trigger alerts
2. **Network Load:** Aggressive scans can DoS
3. **Accuracy:** Too fast = missed ports
4. **Bandwidth:** Consider connection speed

**Implementation:**
```python
def get_delay(template):
    delays = {
        'paranoid': 5.0,
        'sneaky': 2.0,
        'polite': 0.5,
        'normal': 0.1,
        'aggressive': 0.01,
        'insane': 0.001
    }
    return delays.get(template, 0.1)
```

---

### Question 10: How would you design a port scanner for cloud/container environments?

**Answer:**

**Cloud Environment Considerations:**

1. **Service Discovery:** Containers have dynamic IPs
2. **Network Policies:** Kubernetes/Docker network rules
3. **Internal Scanning:** Different from external
4. **API Integration:** Use cloud APIs for discovery

**Design Approach:**

```python
class CloudPortScanner:
    def __init__(self, cloud_provider):
        self.provider = cloud_provider
    
    def discover_targets(self):
        # Use cloud API to find instances
        if self.provider == 'aws':
            return self.discover_ec2()
        elif self.provider == 'gcp':
            return self.discover_gce()
    
    def scan_internal(self, targets, ports):
        # Internal network scanning
        # Often faster, no NAT issues
        for target in targets:
            self.scan_ports(target['private_ip'], ports)
    
    def check_security_groups(self, target):
        # API call to check firewall rules
        return self.provider_api.get_rules(target)
```

**Special Features:**
- Auto-discovery of instances
- Security group awareness
- Internal vs external scanning
- Compliance checking
- Integration with monitoring

---

## 🔥 REAL-WORLD SCENARIOS

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 1: SECURITY AUDIT FOR SMALL BUSINESS NETWORK                  │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: A small business wants to audit their network security.        │
│                                                                             │
│  Challenge: They have 20 devices including servers, workstations, and      │
│  IoT devices. Need to identify exposed services without disrupting         │
│  operations.                                                                │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Scan during off-hours (night)                                           │
│  2. Use polite timing (T2) to avoid impact                                  │
│  3. Start with common ports (21,22,23,25,53,80,443,3389)                   │
│  4. Document all findings in JSON format                                    │
│  5. Generate security report with recommendations                           │
│                                                                             │
│  Command: python port_scanner.py -H 192.168.1.0/24 --timing polite         │
│                                                                             │
│  Outcome: Found 3 unnecessary open ports, closed them, improved            │
│  security posture significantly.                                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 2: PENETRATION TESTING ENGAGEMENT                             │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: Authorized penetration test for a web application.             │
│                                                                             │
│  Challenge: Need to map the attack surface and identify potential          │
│  entry points without triggering security alerts.                          │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Start with slow, stealthy scanning                                     │
│  2. Identify all open ports and services                                   │
│  3. Banner grab to identify versions                                       │
│  4. Research CVEs for identified versions                                  │
│  5. Document findings for the penetration test report                      │
│                                                                             │
│  Command: python port_scanner.py -H target.com --banner --timing sneaky    │
│                                                                             │
│  Key Finding: Outdated OpenSSH version with known vulnerability.           │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 3: TROUBLESHOOTING SERVER CONNECTIVITY                        │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: Application cannot connect to database server.                 │
│                                                                             │
│  Challenge: Need to verify if database port is accessible and service      │
│  is running.                                                                │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Scan database server on MySQL port (3306)                              │
│  2. Check if port is open and banner reveals MySQL version                 │
│  3. If closed, check firewall rules                                        │
│  4. If filtered, investigate network path                                  │
│                                                                             │
│  Command: python port_scanner.py -H db-server.local -p 3306 --banner       │
│                                                                             │
│  Result: Port 3306 was filtered - firewall rule was blocking the          │
│  application server's IP. Fixed by updating firewall rules.                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 4: IOT DEVICE SECURITY ASSESSMENT                             │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: Home network with multiple IoT devices needs security check.   │
│                                                                             │
│  Challenge: IoT devices often have unexpected open ports and services.     │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Scan entire home network range (192.168.1.0/24)                        │
│  2. Identify all devices by open ports                                     │
│  3. Check for default credentials on discovered services                   │
│  4. Document and secure each device                                        │
│                                                                             │
│  Command: python port_scanner.py -H 192.168.1.0/24 --common                │
│                                                                             │
│  Findings: Smart TV had Telnet open (port 23), camera had default          │
│  password. Both secured after assessment.                                  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  🔥 SCENARIO 5: DEVELOPMENT ENVIRONMENT VERIFICATION                       │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Situation: Verify all required services are running in dev environment.   │
│                                                                             │
│  Challenge: Multiple services (web server, database, cache, etc.) need     │
│  to be verified before development work begins.                            │
│                                                                             │
│  Solution Approach:                                                         │
│  1. Create list of required services and ports                             │
│  2. Scan development server for these ports                                │
│  3. Generate status report                                                  │
│  4. Alert if any service is down                                           │
│                                                                             │
│  Command: python port_scanner.py -H dev-server -p 80,443,3306,6379,27017   │
│                                                                             │
│  Automation: Added to CI/CD pipeline to verify environment before          │
│  deployment.                                                                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 PROJECT ARCHITECTURE DIAGRAMS

### Diagram 1: Port Scanner Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         PORT SCANNER EXECUTION FLOW                          │
└─────────────────────────────────────────────────────────────────────────────┘

┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   USER INPUT │────►│  PARSE ARGS  │────►│ VALIDATE IP  │────►│ RESOLVE DNS  │
│  (Host/Port) │     │ (argparse)   │     │  & PORTS     │     │  (if needed) │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│    OUTPUT    │◄────│   RESULTS    │◄────│   THREAD     │◄────│  CREATE      │
│   (JSON/TXT) │     │   COLLECTOR  │     │   POOL       │     │  THREADS     │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
        │                   │                    │                     │
        │                   │                    │                     │
        ▼                   ▼                    ▼                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                          SINGLE THREAD OPERATION                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐  │
│  │ CREATE      │───►│ SET         │───►│ CONNECT_EX  │───►│ CHECK       │  │
│  │ SOCKET      │    │ TIMEOUT     │    │ (host,port) │    │ RESULT      │  │
│  └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘  │
│                                                                  │          │
│                         ┌───────────────────────────────────────┘          │
│                         │                                                  │
│                         ▼                                                  │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐  │
│  │ CLOSE       │◄───│ GRAB BANNER │◄───│ GET SERVICE │◄───│ IF OPEN     │  │
│  │ SOCKET      │    │ (optional)  │    │ NAME        │    │ (result==0) │  │
│  └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘  │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Network Communication

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        TCP THREE-WAY HANDSHAKE                               │
└─────────────────────────────────────────────────────────────────────────────┘

    SCANNER (Client)                              TARGET (Server)
    ─────────────────                             ───────────────
         │                                              │
         │  ┌────────────────────────────────────┐     │
         │  │ SYN (seq=100)                      │────►│
         │  │ "Can we talk?"                     │     │
         │  └────────────────────────────────────┘     │
         │                                              │
         │  ┌────────────────────────────────────┐     │
         │◄──│ SYN-ACK (seq=200, ack=101)         │     │
         │  │ "Sure, let's talk!"                │     │
         │  └────────────────────────────────────┘     │
         │                                              │
         │  ┌────────────────────────────────────┐     │
         │  │ ACK (seq=101, ack=201)             │────►│
         │  │ "Connected!"                       │     │
         │  └────────────────────────────────────┘     │
         │                                              │
         │         ╔══════════════════════╗             │
         │         ║ CONNECTION ESTABLISHED║            │
         │         ╚══════════════════════╝             │
         │                                              │
         │  ┌────────────────────────────────────┐     │
         │◄──│ BANNER: "OpenSSH_8.2p1"           │     │
         │  └────────────────────────────────────┘     │
         │                                              │


┌─────────────────────────────────────────────────────────────────────────────┐
│                        PORT STATES EXPLAINED                                 │
└─────────────────────────────────────────────────────────────────────────────┘

    ┌─────────────────┐         ┌─────────────────┐
    │   OPEN PORT     │         │  CLOSED PORT    │
    ├─────────────────┤         ├─────────────────┤
    │ SYN ────────►   │         │ SYN ────────►   │
    │ ◄──── SYN-ACK   │         │ ◄──── RST       │
    │ (Service Ready) │         │ (No Service)    │
    └─────────────────┘         └─────────────────┘

    ┌─────────────────┐         ┌─────────────────┐
    │  FILTERED PORT  │         │   FIREWALL      │
    ├─────────────────┤         ├─────────────────┤
    │ SYN ────────►   │         │    ┌─────┐      │
    │ (No Response)   │ ──────► │    │ 🚫 │      │
    │ (Timeout)       │         │    └─────┘      │
    └─────────────────┘         └─────────────────┘
```

### Diagram 3: Multi-Threading Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      MULTI-THREADING ARCHITECTURE                            │
└─────────────────────────────────────────────────────────────────────────────┘

                        ┌─────────────────────┐
                        │   MAIN THREAD       │
                        │   (Coordinator)     │
                        └──────────┬──────────┘
                                   │
         ┌─────────────┬───────────┼───────────┬─────────────┐
         │             │           │           │             │
         ▼             ▼           ▼           ▼             ▼
    ┌─────────┐   ┌─────────┐ ┌─────────┐ ┌─────────┐   ┌─────────┐
    │Thread 1 │   │Thread 2 │ │Thread 3 │ │Thread 4 │...│Thread N │
    │Port 1   │   │Port 2   │ │Port 3   │ │Port 4   │   │Port N   │
    └────┬────┘   └────┬────┘ └────┬────┘ └────┬────┘   └────┬────┘
         │             │           │           │             │
         │             │           │           │             │
         ▼             ▼           ▼           ▼             ▼
    ┌─────────────────────────────────────────────────────────────┐
    │                    SHARED RESULT QUEUE                       │
    │  ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐          │
    │  │Port 1 │ │Port 2 │ │Port 3 │ │Port 4 │ │Port N │          │
    │  │OPEN   │ │CLOSED │ │OPEN   │ │FILTER │ │OPEN   │          │
    │  └───────┘ └───────┘ └───────┘ └───────┘ └───────┘          │
    └─────────────────────────────────────────────────────────────┘
                                   │
                                   ▼
                        ┌─────────────────────┐
                        │   RESULTS COLLECTOR │
                        │   & FORMATTER       │
                        └─────────────────────┘
                                   │
                    ┌──────────────┼──────────────┐
                    ▼              ▼              ▼
              ┌──────────┐  ┌──────────┐  ┌──────────┐
              │ Terminal │  │   JSON   │  │   TXT    │
              │  Output  │  │  Report  │  │  Report  │
              └──────────┘  └──────────┘  └──────────┘
```

---

## 🔗 RELATED CHAPTERS

| Previous Chapter | Current Chapter | Next Chapter |
|-----------------|-----------------|--------------|
| **Ch54: YouTube Downloader** | **Ch55: Port Scanner** | **Ch56: File Organizer** |

### Prerequisites
| Chapter | Topic | Why It's Needed |
|---------|-------|-----------------|
| Ch47 | Python Basics | Socket programming foundation |
| Ch48 | Advanced Python | Multi-threading concepts |
| Ch53 | WiFi Analyzer | Network security context |
| Ch51 | Password Generator | Security tools ecosystem |

### Follow-up Chapters
| Chapter | Topic | Connection |
|---------|-------|------------|
| Ch56 | File Organizer | Next project in series |
| Ch57 | Backup Automation | Data security continuation |
| Ch61 | Security Best Practices | Complete security knowledge |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: OS Fingerprinting Implementation

```python
import subprocess
import re

def os_fingerprint(host):
    """
    Attempt to identify the operating system based on TTL values
    """
    try:
        # Ping the host and capture output
        result = subprocess.run(
            ['ping', '-c', '1', '-W', '2', host],
            capture_output=True,
            text=True
        )
        
        # Extract TTL from ping response
        ttl_match = re.search(r'ttl=(\d+)', result.stdout.lower())
        
        if ttl_match:
            ttl = int(ttl_match.group(1))
            
            # OS identification based on default TTL
            if ttl <= 64:
                return "Linux/Unix (TTL: {})".format(ttl)
            elif ttl <= 128:
                return "Windows (TTL: {})".format(ttl)
            elif ttl <= 255:
                return "Cisco/Network Device (TTL: {})".format(ttl)
        
        return "Unknown OS"
    except Exception as e:
        return f"Detection failed: {e}"

# Usage
print(os_fingerprint("192.168.1.1"))
```

---

### Advanced Technique 2: Service-Specific Probing

```python
def probe_service(host, port, service_type):
    """
    Send service-specific probes for better detection
    """
    PROBES = {
        'http': b'HEAD / HTTP/1.1\r\nHost: {}\r\n\r\n',
        'ssh': b'SSH-2.0-Scanner\r\n',
        'ftp': b'USER anonymous\r\n',
        'smtp': b'EHLO scanner\r\n',
        'mysql': b'\x00\x00\x00\x00\x00',
    }
    
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(3)
        sock.connect((host, port))
        
        if service_type in PROBES:
            probe = PROBES[service_type].format(host.encode())
            sock.send(probe)
            response = sock.recv(1024)
            return response.decode(errors='ignore')
        
        sock.close()
    except Exception as e:
        return str(e)
    
    return None
```

---

### Advanced Technique 3: Scan Result Comparison & Diff

```python
import json
from datetime import datetime

def compare_scans(old_scan_file, new_scan_file):
    """
    Compare two scan results and identify changes
    """
    with open(old_scan_file) as f:
        old_scan = json.load(f)
    
    with open(new_scan_file) as f:
        new_scan = json.load(f)
    
    old_ports = {p['port']: p for p in old_scan['ports']}
    new_ports = {p['port']: p for p in new_scan['ports']}
    
    changes = {
        'new_open': [],
        'new_closed': [],
        'new_filtered': [],
        'service_changed': []
    }
    
    for port, data in new_ports.items():
        if port not in old_ports:
            if data['state'] == 'open':
                changes['new_open'].append(port)
        else:
            old_state = old_ports[port]['state']
            new_state = data['state']
            
            if old_state != new_state:
                if new_state == 'open':
                    changes['new_open'].append(port)
                elif new_state == 'closed':
                    changes['new_closed'].append(port)
            
            if data.get('service') != old_ports[port].get('service'):
                changes['service_changed'].append(port)
    
    return changes

# Usage
# changes = compare_scans('scan_yesterday.json', 'scan_today.json')
# print(f"Newly opened ports: {changes['new_open']}")
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### ✅ Knowledge Checkpoint

- [ ] I understand what port scanning is and its purpose
- [ ] I know the difference between well-known, registered, and dynamic ports
- [ ] I can explain the TCP three-way handshake
- [ ] I understand the difference between open, closed, and filtered ports
- [ ] I know how to use Python sockets for network programming
- [ ] I can implement multi-threading for parallel port scanning
- [ ] I understand banner grabbing and its uses
- [ ] I know the ethical and legal implications of port scanning
- [ ] I can create both Python and Bash versions of a port scanner
- [ ] I understand different scan types (TCP Connect, SYN, UDP)
- [ ] I can set appropriate timeouts for efficient scanning
- [ ] I know how to parse and output results in different formats
- [ ] I understand service detection from open ports
- [ ] I can integrate this tool with other security tools

### 🎯 Skills Acquired

| Skill | Level |
|-------|-------|
| Socket Programming | ⭐⭐⭐⭐ |
| Multi-threading | ⭐⭐⭐⭐ |
| Network Protocols | ⭐⭐⭐ |
| Security Concepts | ⭐⭐⭐⭐ |
| Python Development | ⭐⭐⭐⭐ |
| Bash Scripting | ⭐⭐⭐ |

---

## 🚀 PROJECT CHALLENGES

### Challenge 1: Add UDP Scanning Capability

**Task:** Extend the port scanner to support UDP port scanning.

**Requirements:**
- Add `--udp` flag for UDP scanning
- Handle the connectionless nature of UDP
- Implement appropriate timeout handling
- Display results differently (open|filtered state)

**Hint:** UDP requires sending data and checking for ICMP errors.

**Estimated Time:** 2-3 hours

---

### Challenge 2: Implement Port Range Optimization

**Task:** Create a smart port scanner that prioritizes common ports.

**Requirements:**
- Scan top 100, top 1000 ports options
- Implement randomized port order for stealth
- Add progress estimation based on scan rate
- Support CIDR notation for network scanning

**Hint:** Use `--top-ports` argument and shuffle for randomization.

**Estimated Time:** 1-2 hours

---

### Challenge 3: Build a Web Dashboard for Scan Results

**Task:** Create a Flask web app to visualize scan results.

**Requirements:**
- Upload and parse JSON scan results
- Display open ports in a sortable table
- Show service distribution charts
- Compare multiple scans visually

**Hint:** Use Flask for backend, Chart.js for visualizations.

**Estimated Time:** 3-4 hours

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** ALWAYS get permission before scanning! Unauthorized scanning is ILLEGAL!

> 💡 **Pro Tip #2:** Use threading for faster scans - single-threaded scans are too slow for large ranges!

> 💡 **Pro Tip #3:** Set socket timeout to 1-2 seconds - longer timeouts waste time on closed ports!

> 💡 **Pro Tip #4:** Start with common ports scan (`--common`) for quick reconnaissance!

> 💡 **Pro Tip #5:** Banner grabbing reveals service versions - useful for vulnerability assessment!

> 💡 **Pro Tip #6:** Port 0-1023 are "well-known" ports requiring root for servers!

> 💡 **Pro Tip #7:** Use `-oG` grepable output format for parsing results in scripts!

> 💡 **Pro Tip #8:** Combine with Ch53 WiFi Analyzer for complete network mapping!

> 💡 **Pro Tip #9:** For stealth scanning, use SYN scan (requires root) - harder to detect!

> 💡 **Pro Tip #10:** Always save scan results - you'll want to compare later!

---

## 🔥 REAL WORLD USE CASES

### Real World Applications of Port Scanner

**1. Network Administration**
- Verify services are running
- Find unauthorized services
- Audit network security

**2. Security Auditing**
- Identify open ports for assessment
- Find potential attack vectors
- Compliance verification

**3. Penetration Testing**
- Reconnaissance phase
- Service identification
- Vulnerability discovery

**4. Troubleshooting**
- Check if services are accessible
- Diagnose connectivity issues
- Verify firewall rules

**5. Development**
- Test application connectivity
- Verify port bindings
- Debug network issues

**6. Home Network Security**
- Scan your own devices
- Find exposed services
- Secure IoT devices

---

## ⚡ QUICK REFERENCE CARD

### Port Scanner Quick Reference

| Port Range | Category | Examples |
|------------|----------|----------|
| 0-1023 | Well-Known | 22(SSH), 80(HTTP), 443(HTTPS) |
| 1024-49151 | Registered | 3306(MySQL), 5432(PostgreSQL) |
| 49152-65535 | Dynamic/Ephemeral | Client connections |

### Common Ports Reference

| Port | Service | Description |
|------|---------|-------------|
| 21 | FTP | File Transfer |
| 22 | SSH | Secure Shell |
| 23 | Telnet | Remote Access (insecure) |
| 25 | SMTP | Email Sending |
| 53 | DNS | Domain Name System |
| 80 | HTTP | Web Traffic |
| 110 | POP3 | Email Receiving |
| 143 | IMAP | Email Receiving |
| 443 | HTTPS | Secure Web |
| 3306 | MySQL | Database |
| 3389 | RDP | Remote Desktop |
| 5432 | PostgreSQL | Database |

### Command Reference

| Command | Purpose |
|---------|---------|
| `python port_scanner.py -H host -p 1-1000` | Range scan |
| `python port_scanner.py -H host --common` | Common ports |
| `python port_scanner.py -H host -p 22` | Single port |
| `bash port_scanner.sh host 1 100` | Bash version |

---

## 🏆 BONUS CONTENT

### Bonus: Advanced Scanning Techniques

**Technique 1: Service Version Detection**
```python
def detect_version(banner):
    """Parse banner to extract version"""
    import re
    # Example: "OpenSSH_8.2p1" -> version 8.2p1
    match = re.search(r'(\d+\.\d+[\w.]*)', banner)
    return match.group(1) if match else None
```

**Technique 2: OS Fingerprinting**
```python
def os_fingerprint(host, open_ports):
    """Guess OS based on open ports"""
    # Windows: 135, 139, 445, 3389
    # Linux: 22, 80, 443
    # Use TTL from ping as additional indicator
```

**Technique 3: Scan Timing Templates**
```python
TIMING_TEMPLATES = {
    'paranoid': 5,    # Very slow, IDS evasion
    'sneaky': 2,
    'polite': 1,
    'normal': 0.5,
    'aggressive': 0.1,
    'insane': 0.01    # Very fast, may miss ports
}
```

**Technique 4: Firewall Detection**
```python
def detect_firewall(host, ports):
    """Detect if port is filtered by firewall"""
    # If no response (not even RST), likely filtered
    # Compare with known open ports
```

**Technique 5: Scan Comparison**
```python
def compare_scans(old_scan, new_scan):
    """Compare two scans for changes"""
    # New open ports = potential security issue
    # Closed ports = service stopped
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **Port Scanning Fundamentals** - TCP/UDP ports and their purposes
- ✅ **Scanning Types** - TCP Connect, SYN, UDP scanning
- ✅ **Python Socket Programming** - Network connections in Python
- ✅ **Multi-Threading** - Parallel scanning for speed
- ✅ **Banner Grabbing** - Service identification
- ✅ **Bash Implementation** - Alternative scanning method
- ✅ **Ethical Considerations** - Legal and responsible scanning
- ✅ **Output Formats** - JSON and text reports

### Key Takeaways

1. **Permission is MANDATORY** - Never scan without authorization
2. **Threading = Speed** - Use threads for efficient scanning
3. **Banner reveals version** - Useful for security assessment
4. **Timeout matters** - Balance between speed and accuracy
5. **Document everything** - Save all scan results

---

## 🚀 PROJECT EXTENSIONS

### 5+ Ideas to Extend This Project

**Extension 1: Web Interface** ⭐⭐⭐⭐
- Flask web app for scanning
- Visual results display
- **Steps:** Create Flask app, add scan endpoints

**Extension 2: Vulnerability Scanner** ⭐⭐⭐⭐⭐
- Check for known vulnerabilities
- CVE database integration
- **Steps:** Add CVE lookup, create vulnerability DB

**Extension 3: Network Topology Mapper** ⭐⭐⭐⭐
- Visualize network structure
- Service dependencies
- **Steps:** Use graph libraries, create visual output

**Extension 4: Automated Alerts** ⭐⭐⭐
- Alert on new open ports
- Schedule regular scans
- **Steps:** Add cron job, notification system

**Extension 5: Compliance Checker** ⭐⭐⭐⭐
- Check against security policies
- Generate compliance reports
- **Steps:** Create policy engine, report generator

**Extension 6: Port Monitoring Service** ⭐⭐⭐
- Continuous port monitoring
- Change detection alerts
- **Steps:** Background service, state comparison

---

## 🔧 CODE WALKTHROUGH

### Port Scanner Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PORT SCANNER ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   ┌─────────────┐      ┌─────────────┐       ┌─────────────┐        │
│   │   Target    │      │   Port      │       │   Thread    │        │
│   │   Host/IP   │ ───► │   Range     │ ───►  │   Pool      │        │
│   └─────────────┘      └─────────────┘       └─────────────┘        │
│         │                    │                     │                 │
│         │                    │                     ▼                 │
│         │                    │           ┌─────────────────┐        │
│         │                    │           │  Scan Thread 1  │        │
│         │                    │           │  Port 1-100     │        │
│         │                    │           ├─────────────────┤        │
│         │                    │           │  Scan Thread 2  │        │
│         │                    │           │  Port 101-200   │        │
│         │                    │           ├─────────────────┤        │
│         │                    │           │  ...            │        │
│         │                    │           └─────────────────┘        │
│         │                    │                     │                 │
│         ▼                    ▼                     ▼                 │
│   ┌─────────────────────────────────────────────────────────┐      │
│   │                    SOCKET LAYER                          │      │
│   │  socket.connect_ex((host, port)) → 0 = OPEN, else CLOSED │      │
│   └─────────────────────────────────────────────────────────┘      │
│                                │                                     │
│         ┌──────────────────────┼──────────────────────┐             │
│         ▼                      ▼                      ▼             │
│   ┌───────────┐         ┌───────────┐         ┌───────────┐        │
│   │ Terminal  │         │ JSON      │         │ Text      │        │
│   │ Output    │         │ Report    │         │ Report    │        │
│   └───────────┘         └───────────┘         └───────────┘        │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 📦 DEPLOYMENT GUIDE

### How to Deploy and Share This Project

**1. Create Project**
```bash
mkdir -p ~/port-scanner
cd ~/port-scanner
```

**2. Install Dependencies**
```bash
pkg install python -y
# No additional packages needed - uses standard library
```

**3. GitHub Deployment**
```bash
git init
git add port_scanner.py port_scanner.sh README.md
git commit -m "Custom Port Scanner for Termux"
git push origin main
```

**4. Create Alias**
```bash
echo 'alias pscan="python ~/port-scanner/port_scanner.py"' >> ~/.bashrc
source ~/.bashrc
```

---

## 🔗 RELATED CHAPTERS

### Cross-Reference to Related Chapters

| Chapter | Topic | Connection |
|---------|-------|------------|
| **Ch53** | WiFi Analyzer | Network security tools |
| **Ch51** | Password Generator | Security tools suite |
| **Ch47** | Python Basics | Socket programming |
| **Ch61** | Security Best Practices | Network security |

### Next Steps
- ➡️ **Ch56: File Organizer** - File management
- ➡️ **Ch57: Backup Automation** - Data protection

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your Port Scanner Knowledge!

**Question 1:** Which port range contains well-known ports?
- a) 0-1023 ✓
- b) 1024-49151
- c) 49152-65535
- d) 1-100

**Question 2:** What does socket.connect_ex() return on success?
- a) 1
- b) 0 ✓
- c) -1
- d) True

**Question 3:** Which port is used for SSH?
- a) 21
- b) 22 ✓
- c) 23
- d) 80

**Question 4:** What is banner grabbing?
- a) Capturing website headers
- b) Getting service information from response ✓
- c) Network speed test
- d) Port enumeration

**Question 5:** Why use multi-threading for port scanning?
- a) Better accuracy
- b) Faster scanning ✓
- c) More secure
- d) Smaller code

**Question 6:** What timeout is recommended for port scanning?
- a) 0.1 seconds
- b) 1-2 seconds ✓
- c) 10 seconds
- d) 60 seconds

**Question 7:** Is port scanning legal?
- a) Always legal
- b) Only with permission ✓
- c) Never legal
- d) Only for security professionals

**Question 8:** Which scan type requires root access?
- a) TCP Connect
- b) SYN Scan ✓
- c) UDP Scan
- d) Banner Grab

**Question 9:** What does a filtered port mean?
- a) Port is open
- b) Port is closed
- c) Firewall blocking the port ✓
- d) Service running

**Question 10:** Which module is used for socket programming in Python?
- a) network
- b) socket ✓
- c) port
- d) connect

**Question 11:** What is the default HTTP port?
- a) 21
- b) 22
- c) 80 ✓
- d) 443

**Question 12:** What does dBm measure in network context? (Trick question!)
- a) Signal strength (WiFi, not ports!)
- b) Port speed
- c) Thread count
- d) Scan duration

---

### Extend the Project Challenges

**Challenge 1:** Add UDP scanning
```python
def scan_udp_port(host, port):
    # UDP requires different approach
    # Send packet, wait for response or timeout
```

**Challenge 2:** Implement SYN scan
```python
# Requires raw sockets (root)
def syn_scan(host, port):
    # Send SYN packet
    # Check for SYN-ACK (open) or RST (closed)
```

**Challenge 3:** Add scan scheduling
```python
import schedule
def schedule_scan(host, time):
    schedule.every().day.at(time).do(scan, host)
```

### Bug Fixing Exercises

**Bug 1:** All ports show as closed
```python
sock.settimeout(0.01)  # Too short!
```
*Fix: Increase timeout to at least 1 second*

**Bug 2:** Memory error on large scans
```python
threads = []
for port in range(1, 65536):
    t = Thread(target=scan, args=(port))
    t.start()  # Too many threads!
```
*Fix: Use ThreadPoolExecutor with max_workers limit*

---

## 📖 TECHNICAL GUIDE

### 1. Project Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PORT SCANNER PROJECT OVERVIEW                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Project Name: Custom Port Scanner                                       │
│  Version: 1.0                                                            │
│  Language: Python 3 + Bash                                               │
│  Dependencies: Python3, Netcat (for Bash version)                        │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                      PROJECT STRUCTURE                           │    │
│  ├─────────────────────────────────────────────────────────────────┤    │
│  │                                                                  │    │
│  │  port_scanner/                                                   │    │
│  │  ├── port_scanner.py      # Main Python scanner                  │    │
│  │  ├── port_scanner.sh      # Bash version                         │    │
│  │  ├── common_ports.py      # Common ports database                │    │
│  │  ├── scanner_utils.py     # Utility functions                    │    │
│  │  ├── results/             # Output directory                     │    │
│  │  │   ├── scan_report.json                                       │    │
│  │  │   └── scan_report.txt                                        │    │
│  │  └── README.md            # Documentation                        │    │
│  │                                                                  │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  Use Case: Network reconnaissance, security auditing                     │
│  Skill Level: Intermediate                                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Understanding Port Scanning

#### TCP/IP Ports

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PORT RANGES EXPLAINED                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Total Ports: 65,535 (0-65535)                                          │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  WELL-KNOWN PORTS (0-1023)                                      │    │
│  │  - Reserved for standard services                               │    │
│  │  - Require root/admin for servers                               │    │
│  │  - Examples: 22(SSH), 80(HTTP), 443(HTTPS)                      │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  REGISTERED PORTS (1024-49151)                                   │    │
│  │  - Assigned by IANA                                             │    │
│  │  - Used by applications                                         │    │
│  │  - Examples: 3306(MySQL), 5432(PostgreSQL)                      │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  DYNAMIC/PRIVATE PORTS (49152-65535)                            │    │
│  │  - Used for client connections                                  │    │
│  │  - Temporary ports                                              │    │
│  │  - Ephemeral ports                                              │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### TCP Three-Way Handshake

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TCP THREE-WAY HANDSHAKE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│      CLIENT                                    SERVER                    │
│        │                                          │                      │
│        │ ─────────── SYN ──────────────────────> │                      │
│        │          (seq=x)                         │                      │
│        │                                          │                      │
│        │ <─────────── SYN+ACK ───────────────── │                      │
│        │          (seq=y, ack=x+1)               │                      │
│        │                                          │                      │
│        │ ─────────── ACK ──────────────────────> │                      │
│        │          (ack=y+1)                       │                      │
│        │                                          │                      │
│        │        [CONNECTION ESTABLISHED]          │                      │
│        │                                          │                      │
│                                                                          │
│  TCP CONNECT SCAN:                                                       │
│  1. Send SYN packet                                                      │
│  2. Wait for SYN+ACK (port open) or RST (port closed)                   │
│  3. Send ACK to complete handshake                                       │
│  4. Send RST to close (or use full connection)                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

#### Port States

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PORT STATES                                           │
├──────────────────┬──────────────────────────────────────────────────────┤
│ State            │ Description                                          │
├──────────────────┼──────────────────────────────────────────────────────┤
│ OPEN             │ Service is listening, accepting connections          │
│ CLOSED           │ No service listening, but port is accessible        │
│ FILTERED         │ Firewall blocking, cannot determine state           │
│ UNFILTERED       │ Accessible but cannot determine open/closed         │
│ OPEN|FILTERED    │ Either open or filtered (uncertain)                 │
│ CLOSED|FILTERED  │ Either closed or filtered (uncertain)               │
└──────────────────┴──────────────────────────────────────────────────────┘
```

### 3. Features Implementation

#### Feature 1: Single Host Scan

```python
# Scan a single host for specified ports
# Usage: python port_scanner.py -H 192.168.1.1 -p 22

def scan_single_port(host, port):
    """
    Scan a single port on a host
    Returns: True if open, False if closed
    """
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((host, port))
        sock.close()
        return result == 0
    except socket.error:
        return False
```

#### Feature 2: Range Scan

```python
# Scan a range of ports
# Usage: python port_scanner.py -H 192.168.1.1 -p 1-1000

def scan_port_range(host, start_port, end_port, threads=100):
    """
    Scan a range of ports using multiple threads
    """
    open_ports = []
    
    def scan_thread(port):
        if scan_single_port(host, port):
            open_ports.append(port)
    
    # Create thread pool
    with ThreadPoolExecutor(max_workers=threads) as executor:
        ports = range(start_port, end_port + 1)
        list(executor.map(scan_thread, ports))
    
    return sorted(open_ports)
```

#### Feature 3: Common Ports Scan

```python
# Scan most common ports
# Usage: python port_scanner.py -H 192.168.1.1 --common

COMMON_PORTS = {
    21: 'FTP',
    22: 'SSH',
    23: 'Telnet',
    25: 'SMTP',
    53: 'DNS',
    80: 'HTTP',
    110: 'POP3',
    143: 'IMAP',
    443: 'HTTPS',
    445: 'SMB',
    993: 'IMAPS',
    995: 'POP3S',
    1433: 'MSSQL',
    1521: 'Oracle',
    3306: 'MySQL',
    3389: 'RDP',
    5432: 'PostgreSQL',
    5900: 'VNC',
    6379: 'Redis',
    8080: 'HTTP-Proxy',
    8443: 'HTTPS-Alt',
    27017: 'MongoDB'
}

def scan_common_ports(host):
    """Scan top common ports"""
    results = {}
    for port, service in COMMON_PORTS.items():
        if scan_single_port(host, port):
            results[port] = service
    return results
```

#### Feature 4: Service Detection (Banner Grabbing)

```python
def grab_banner(host, port, timeout=2):
    """
    Attempt to grab service banner
    Returns: Banner string or None
    """
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(timeout)
        sock.connect((host, port))
        
        # Send HTTP request for web services
        if port in [80, 443, 8080, 8443]:
            request = f"HEAD / HTTP/1.1\r\nHost: {host}\r\n\r\n"
            sock.send(request.encode())
        else:
            # Wait for banner
            sock.send(b'\r\n')
        
        banner = sock.recv(1024).decode('utf-8', errors='ignore').strip()
        sock.close()
        return banner[:200]  # Limit banner length
        
    except socket.error:
        return None

def detect_service(port, banner=None):
    """
    Detect service based on port and banner
    """
    service_map = {
        21: 'FTP',
        22: 'SSH',
        23: 'Telnet',
        25: 'SMTP',
        80: 'HTTP',
        110: 'POP3',
        143: 'IMAP',
        443: 'HTTPS',
        3306: 'MySQL',
        5432: 'PostgreSQL',
        3389: 'RDP'
    }
    
    service = service_map.get(port, 'Unknown')
    
    if banner:
        # Try to extract version from banner
        if 'OpenSSH' in banner:
            service = 'SSH (OpenSSH)'
        elif 'nginx' in banner.lower():
            service = 'HTTP (nginx)'
        elif 'Apache' in banner:
            service = 'HTTP (Apache)'
        elif 'Microsoft-IIS' in banner:
            service = 'HTTP (IIS)'
    
    return service
```

#### Feature 5: Multi-Threading

```python
from concurrent.futures import ThreadPoolExecutor, as_completed
import threading

class PortScanner:
    def __init__(self, max_threads=100):
        self.max_threads = max_threads
        self.results = []
        self.lock = threading.Lock()
        self.progress = 0
        self.total = 0
    
    def scan_port(self, host, port):
        """Thread-safe port scan"""
        try:
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.settimeout(1)
            result = sock.connect_ex((host, port))
            
            if result == 0:
                banner = self.grab_banner(host, port, sock)
                service = detect_service(port, banner)
                
                with self.lock:
                    self.results.append({
                        'port': port,
                        'state': 'open',
                        'service': service,
                        'banner': banner
                    })
            
            sock.close()
            
            with self.lock:
                self.progress += 1
                
        except socket.error:
            pass
    
    def scan_range(self, host, start_port, end_port):
        """Multi-threaded range scan"""
        self.total = end_port - start_port + 1
        self.progress = 0
        self.results = []
        
        with ThreadPoolExecutor(max_workers=self.max_threads) as executor:
            futures = []
            for port in range(start_port, end_port + 1):
                future = executor.submit(self.scan_port, host, port)
                futures.append(future)
            
            # Wait for all threads
            for future in as_completed(futures):
                pass
        
        return sorted(self.results, key=lambda x: x['port'])
```

#### Feature 6: Output Formats

```python
import json
from datetime import datetime

def save_json(results, host, filename='scan_report.json'):
    """Save results to JSON file"""
    output = {
        'target': host,
        'scan_date': datetime.now().isoformat(),
        'open_ports': len(results),
        'results': results
    }
    
    with open(filename, 'w') as f:
        json.dump(output, f, indent=4)
    
    return filename

def save_text(results, host, filename='scan_report.txt'):
    """Save results to text file"""
    with open(filename, 'w') as f:
        f.write("=" * 60 + "\n")
        f.write("PORT SCAN REPORT\n")
        f.write("=" * 60 + "\n\n")
        f.write(f"Target: {host}\n")
        f.write(f"Scan Date: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}\n")
        f.write(f"Open Ports: {len(results)}\n\n")
        f.write("-" * 60 + "\n")
        f.write(f"{'PORT':<10} {'STATE':<10} {'SERVICE':<20}\n")
        f.write("-" * 60 + "\n")
        
        for result in results:
            port = result['port']
            service = result.get('service', 'Unknown')
            f.write(f"{port:<10} {'OPEN':<10} {service:<20}\n")
        
        f.write("-" * 60 + "\n")
    
    return filename

def print_results(results, host):
    """Print results to terminal"""
    print(f"\n{'='*60}")
    print(f"SCAN RESULTS FOR: {host}")
    print(f"{'='*60}\n")
    
    if not results:
        print("No open ports found.")
        return
    
    print(f"{'PORT':<10} {'STATE':<10} {'SERVICE':<20}")
    print("-" * 40)
    
    for result in results:
        port = result['port']
        service = result.get('service', 'Unknown')
        print(f"{port:<10} {'OPEN':<10} {service:<20}")
    
    print(f"\nTotal open ports: {len(results)}")
```

#### Feature 7: Progress Display

```python
import sys
import time

class ProgressBar:
    def __init__(self, total, width=50):
        self.total = total
        self.width = width
        self.current = 0
        self.start_time = time.time()
    
    def update(self, current):
        self.current = current
        percent = (current / self.total) * 100
        filled = int(self.width * current / self.total)
        bar = '█' * filled + '░' * (self.width - filled)
        
        # Calculate ETA
        elapsed = time.time() - self.start_time
        if current > 0:
            eta = (elapsed / current) * (self.total - current)
            eta_str = f"ETA: {int(eta)}s"
        else:
            eta_str = "ETA: --"
        
        sys.stdout.write(f'\r[{bar}] {percent:.1f}% | {current}/{self.total} | {eta_str}')
        sys.stdout.flush()
    
    def complete(self):
        self.update(self.total)
        print()

def scan_with_progress(scanner, host, start_port, end_port):
    """Scan with progress bar"""
    total = end_port - start_port + 1
    progress = ProgressBar(total)
    
    def update_progress():
        while scanner.progress < total:
            progress.update(scanner.progress)
            time.sleep(0.1)
    
    # Start progress thread
    import threading
    progress_thread = threading.Thread(target=update_progress)
    progress_thread.start()
    
    # Run scan
    results = scanner.scan_range(host, start_port, end_port)
    
    progress_thread.join()
    progress.complete()
    
    return results
```

---

## 💻 COMPLETE SOURCE CODE

### Python Version (port_scanner.py)

```python
#!/usr/bin/env python3
"""
╔═══════════════════════════════════════════════════════════════════════════╗
║                     CUSTOM PORT SCANNER - PYTHON                          ║
║                        By T3rmuxk1ng | Version 1.0                        ║
╠═══════════════════════════════════════════════════════════════════════════╣
║  Features:                                                                ║
║  • Single/Range/Common port scanning                                      ║
║  • Multi-threaded for fast performance                                    ║
║  • Service detection with banner grabbing                                 ║
║  • JSON and text report output                                            ║
║  • Real-time progress display                                             ║
╚═══════════════════════════════════════════════════════════════════════════╝
"""

import socket
import argparse
import threading
import json
import sys
import time
from datetime import datetime
from concurrent.futures import ThreadPoolExecutor, as_completed
from typing import Dict, List, Optional, Tuple

# ============================================================================
# CONFIGURATION
# ============================================================================

# Common ports database
COMMON_PORTS: Dict[int, str] = {
    # Well-known ports
    20: 'FTP Data',
    21: 'FTP Control',
    22: 'SSH',
    23: 'Telnet',
    25: 'SMTP',
    53: 'DNS',
    67: 'DHCP Server',
    68: 'DHCP Client',
    69: 'TFTP',
    80: 'HTTP',
    110: 'POP3',
    119: 'NNTP',
    123: 'NTP',
    135: 'RPC',
    137: 'NetBIOS Name',
    138: 'NetBIOS Datagram',
    139: 'NetBIOS Session',
    143: 'IMAP',
    161: 'SNMP',
    162: 'SNMP Trap',
    389: 'LDAP',
    443: 'HTTPS',
    445: 'SMB',
    465: 'SMTPS',
    514: 'Syslog',
    587: 'SMTP (TLS)',
    636: 'LDAPS',
    993: 'IMAPS',
    995: 'POP3S',
    # Database ports
    1433: 'MSSQL',
    1521: 'Oracle DB',
    3306: 'MySQL',
    5432: 'PostgreSQL',
    6379: 'Redis',
    27017: 'MongoDB',
    # Application ports
    1080: 'SOCKS Proxy',
    3128: 'Squid Proxy',
    3389: 'RDP',
    5900: 'VNC',
    5901: 'VNC-1',
    5902: 'VNC-2',
    6667: 'IRC',
    8000: 'HTTP-Alt',
    8080: 'HTTP-Proxy',
    8443: 'HTTPS-Alt',
    9000: 'PHP-FPM',
    9090: 'Prometheus',
    # Popular services
    25565: 'Minecraft',
    27015: 'Steam',
}

# Color codes for terminal output
class Colors:
    HEADER = '\033[95m'
    BLUE = '\033[94m'
    CYAN = '\033[96m'
    GREEN = '\033[92m'
    YELLOW = '\033[93m'
    RED = '\033[91m'
    END = '\033[0m'
    BOLD = '\033[1m'

# ============================================================================
# BANNER GRABBING
# ============================================================================

def grab_banner(host: str, port: int, sock: socket.socket = None, 
                timeout: float = 2) -> Optional[str]:
    """
    Attempt to grab service banner
    
    Args:
        host: Target host
        port: Target port
        sock: Existing socket (optional)
        timeout: Connection timeout
    
    Returns:
        Banner string or None
    """
    try:
        if sock is None:
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.settimeout(timeout)
            sock.connect((host, port))
        
        # Different probes based on port type
        if port in [80, 443, 8080, 8000, 8443, 3000]:
            # HTTP probe
            probe = f"HEAD / HTTP/1.1\r\nHost: {host}\r\nUser-Agent: PortScanner/1.0\r\n\r\n"
            sock.send(probe.encode())
        elif port == 22:
            # SSH - just receive banner
            pass
        elif port in [21, 25, 110, 143, 587]:
            # Protocol sends banner first
            pass
        else:
            # Generic probe
            sock.send(b'\r\n')
        
        banner = sock.recv(1024).decode('utf-8', errors='ignore').strip()
        return banner[:300] if banner else None
        
    except (socket.error, socket.timeout):
        return None

def parse_banner(banner: str, port: int) -> Dict[str, str]:
    """
    Parse banner to extract service information
    
    Args:
        banner: Raw banner string
        port: Port number for context
    
    Returns:
        Dictionary with service details
    """
    info = {'service': COMMON_PORTS.get(port, 'Unknown'), 'version': None}
    
    if not banner:
        return info
    
    banner_lower = banner.lower()
    
    # SSH
    if 'ssh' in banner_lower:
        info['service'] = 'SSH'
        if 'openssh' in banner_lower:
            import re
            version = re.search(r'OpenSSH[_\s]([\d.]+)', banner, re.IGNORECASE)
            if version:
                info['version'] = f'OpenSSH {version.group(1)}'
    
    # HTTP Servers
    elif 'nginx' in banner_lower:
        info['service'] = 'HTTP'
        import re
        version = re.search(r'nginx/([\d.]+)', banner, re.IGNORECASE)
        info['version'] = f'nginx/{version.group(1)}' if version else 'nginx'
    
    elif 'apache' in banner_lower:
        info['service'] = 'HTTP'
        import re
        version = re.search(r'Apache/([\d.]+)', banner, re.IGNORECASE)
        info['version'] = f'Apache/{version.group(1)}' if version else 'Apache'
    
    elif 'microsoft-iis' in banner_lower:
        info['service'] = 'HTTP'
        import re
        version = re.search(r'Microsoft-IIS/([\d.]+)', banner, re.IGNORECASE)
        info['version'] = f'IIS/{version.group(1)}' if version else 'IIS'
    
    # FTP
    elif port == 21 and 'ftp' in banner_lower:
        info['service'] = 'FTP'
        info['version'] = banner.split('\n')[0][:50]
    
    # MySQL
    elif port == 3306:
        info['service'] = 'MySQL'
        if banner:
            info['version'] = banner.split('\n')[0][:50]
    
    # Generic - use first line
    if not info['version'] and banner:
        first_line = banner.split('\n')[0][:100]
        if first_line:
            info['version'] = first_line
    
    return info

# ============================================================================
# PORT SCANNER CLASS
# ============================================================================

class PortScanner:
    """
    Multi-threaded Port Scanner
    """
    
    def __init__(self, max_threads: int = 100, timeout: float = 1.0,
                 verbose: bool = True):
        """
        Initialize scanner
        
        Args:
            max_threads: Maximum concurrent threads
            timeout: Socket timeout in seconds
            verbose: Print progress to stdout
        """
        self.max_threads = max_threads
        self.timeout = timeout
        self.verbose = verbose
        self.results: List[Dict] = []
        self.lock = threading.Lock()
        self.scanned = 0
        self.total = 0
        self.start_time = None
    
    def scan_port(self, host: str, port: int) -> Optional[Dict]:
        """
        Scan a single port
        
        Args:
            host: Target host
            port: Port number
        
        Returns:
            Result dictionary if port is open, None otherwise
        """
        try:
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.settimeout(self.timeout)
            result = sock.connect_ex((host, port))
            
            if result == 0:
                # Port is open - grab banner
                banner = grab_banner(host, port, sock)
                service_info = parse_banner(banner, port)
                
                with self.lock:
                    self.scanned += 1
                
                sock.close()
                
                return {
                    'port': port,
                    'state': 'open',
                    'service': service_info['service'],
                    'version': service_info['version'],
                    'banner': banner[:200] if banner else None
                }
            else:
                with self.lock:
                    self.scanned += 1
                sock.close()
                return None
                
        except socket.error:
            with self.lock:
                self.scanned += 1
            return None
    
    def scan_range(self, host: str, start_port: int, end_port: int) -> List[Dict]:
        """
        Scan a range of ports using multiple threads
        
        Args:
            host: Target host
            start_port: Starting port
            end_port: Ending port (inclusive)
        
        Returns:
            List of open port results
        """
        self.results = []
        self.scanned = 0
        self.total = end_port - start_port + 1
        self.start_time = time.time()
        
        if self.verbose:
            print(f"\n{Colors.CYAN}[*] Scanning {host}:{start_port}-{end_port}{Colors.END}")
            print(f"{Colors.CYAN}[*] Using {self.max_threads} threads{Colors.END}\n")
        
        with ThreadPoolExecutor(max_workers=self.max_threads) as executor:
            futures = {
                executor.submit(self.scan_port, host, port): port
                for port in range(start_port, end_port + 1)
            }
            
            for future in as_completed(futures):
                result = future.result()
                if result:
                    self.results.append(result)
                    if self.verbose:
                        self._print_result(result)
        
        return sorted(self.results, key=lambda x: x['port'])
    
    def scan_common(self, host: str) -> List[Dict]:
        """
        Scan common ports only
        
        Args:
            host: Target host
        
        Returns:
            List of open port results
        """
        ports = list(COMMON_PORTS.keys())
        
        self.results = []
        self.scanned = 0
        self.total = len(ports)
        self.start_time = time.time()
        
        if self.verbose:
            print(f"\n{Colors.CYAN}[*] Scanning {host} - Top {len(ports)} common ports{Colors.END}\n")
        
        with ThreadPoolExecutor(max_workers=self.max_threads) as executor:
            futures = {
                executor.submit(self.scan_port, host, port): port
                for port in ports
            }
            
            for future in as_completed(futures):
                result = future.result()
                if result:
                    self.results.append(result)
                    if self.verbose:
                        self._print_result(result)
        
        return sorted(self.results, key=lambda x: x['port'])
    
    def _print_result(self, result: Dict):
        """Print a single result"""
        port = result['port']
        service = result['service']
        version = result.get('version', '')
        
        version_str = f" ({version})" if version and version != service else ""
        print(f"{Colors.GREEN}[+] Port {port:5d}: OPEN - {service}{version_str}{Colors.END}")
    
    def get_stats(self) -> Dict:
        """Get scan statistics"""
        elapsed = time.time() - self.start_time if self.start_time else 0
        return {
            'total_ports': self.total,
            'scanned': self.scanned,
            'open_ports': len(self.results),
            'elapsed_time': round(elapsed, 2),
            'ports_per_second': round(self.scanned / elapsed, 2) if elapsed > 0 else 0
        }

# ============================================================================
# OUTPUT FUNCTIONS
# ============================================================================

def save_json_report(results: List[Dict], host: str, stats: Dict,
                     filename: str = None) -> str:
    """
    Save results to JSON file
    
    Args:
        results: Scan results
        host: Target host
        stats: Scan statistics
        filename: Output filename (optional)
    
    Returns:
        Filename of saved report
    """
    if filename is None:
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        filename = f"scan_{host}_{timestamp}.json"
    
    report = {
        'scan_info': {
            'target': host,
            'scan_date': datetime.now().isoformat(),
            'scan_duration': stats['elapsed_time'],
            'ports_scanned': stats['total_ports'],
            'ports_per_second': stats['ports_per_second']
        },
        'summary': {
            'open_ports': len(results),
            'open_port_list': [r['port'] for r in results]
        },
        'results': results
    }
    
    with open(filename, 'w') as f:
        json.dump(report, f, indent=4)
    
    return filename

def save_text_report(results: List[Dict], host: str, stats: Dict,
                     filename: str = None) -> str:
    """
    Save results to text file
    
    Args:
        results: Scan results
        host: Target host
        stats: Scan statistics
        filename: Output filename (optional)
    
    Returns:
        Filename of saved report
    """
    if filename is None:
        timestamp = datetime.now().strftime('%Y%m%d_%H%M%S')
        filename = f"scan_{host}_{timestamp}.txt"
    
    with open(filename, 'w') as f:
        f.write("=" * 70 + "\n")
        f.write("                    PORT SCAN REPORT\n")
        f.write("                    By T3rmuxk1ng Scanner\n")
        f.write("=" * 70 + "\n\n")
        
        f.write("SCAN INFORMATION\n")
        f.write("-" * 70 + "\n")
        f.write(f"Target Host:      {host}\n")
        f.write(f"Scan Date:        {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}\n")
        f.write(f"Scan Duration:    {stats['elapsed_time']} seconds\n")
        f.write(f"Ports Scanned:    {stats['total_ports']}\n")
        f.write(f"Scan Rate:        {stats['ports_per_second']} ports/sec\n\n")
        
        f.write("SUMMARY\n")
        f.write("-" * 70 + "\n")
        f.write(f"Open Ports Found: {len(results)}\n\n")
        
        if results:
            f.write("OPEN PORTS\n")
            f.write("-" * 70 + "\n")
            f.write(f"{'PORT':<8} {'STATE':<8} {'SERVICE':<20} {'VERSION':<30}\n")
            f.write("-" * 70 + "\n")
            
            for r in results:
                port = r['port']
                service = r.get('service', 'Unknown')
                version = r.get('version', '') or ''
                f.write(f"{port:<8} {'OPEN':<8} {service:<20} {version[:30]:<30}\n")
        
        f.write("-" * 70 + "\n")
        f.write("\n[Scan completed by T3rmuxk1ng Port Scanner v1.0]\n")
    
    return filename

def print_summary(results: List[Dict], host: str, stats: Dict):
    """Print scan summary"""
    print(f"\n{Colors.HEADER}{'='*60}{Colors.END}")
    print(f"{Colors.HEADER}SCAN SUMMARY{Colors.END}")
    print(f"{Colors.HEADER}{'='*60}{Colors.END}\n")
    
    print(f"Target:         {host}")
    print(f"Ports Scanned:  {stats['total_ports']}")
    print(f"Open Ports:     {len(results)}")
    print(f"Scan Time:      {stats['elapsed_time']} seconds")
    print(f"Scan Rate:      {stats['ports_per_second']} ports/sec")
    
    if results:
        print(f"\n{Colors.GREEN}Open Ports:{Colors.END}")
        for r in results:
            port = r['port']
            service = r.get('service', 'Unknown')
            print(f"  {port:5d}/tcp   {service}")
    
    print(f"\n{Colors.HEADER}{'='*60}{Colors.END}")

# ============================================================================
# ARGUMENT PARSING
# ============================================================================

def parse_port_spec(port_spec: str) -> Tuple[int, int]:
    """
    Parse port specification
    
    Args:
        port_spec: Port string like '80', '1-1000', 'common'
    
    Returns:
        Tuple of (start_port, end_port)
    """
    if port_spec.lower() == 'common':
        return None, None  # Signal for common ports
    
    if '-' in port_spec:
        start, end = port_spec.split('-')
        return int(start), int(end)
    else:
        port = int(port_spec)
        return port, port

def parse_arguments():
    """Parse command line arguments"""
    parser = argparse.ArgumentParser(
        description=f'{Colors.CYAN}Custom Port Scanner by T3rmuxk1ng{Colors.END}',
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog=f'''
{Colors.YELLOW}Examples:{Colors.END}
  %(prog)s -H 192.168.1.1 -p 1-1000           # Scan ports 1-1000
  %(prog)s -H 192.168.1.1 -p common            # Scan common ports
  %(prog)s -H 192.168.1.1 -p 22,80,443         # Scan specific ports
  %(prog)s -H scanme.nmap.org -p 1-100 -t 50   # 50 threads
  %(prog)s -H localhost -p 1-1000 -o json      # Save as JSON

{Colors.RED}Disclaimer: Only scan systems you own or have permission to test!{Colors.END}
        '''
    )
    
    parser.add_argument('-H', '--host', required=True,
                        help='Target host to scan')
    
    parser.add_argument('-p', '--ports', default='common',
                        help='Port specification: single port (80), '
                             'range (1-1000), or "common"')
    
    parser.add_argument('-t', '--threads', type=int, default=100,
                        help='Number of threads (default: 100)')
    
    parser.add_argument('--timeout', type=float, default=1.0,
                        help='Socket timeout in seconds (default: 1.0)')
    
    parser.add_argument('-o', '--output', choices=['json', 'txt', 'both'],
                        help='Save output to file')
    
    parser.add_argument('-q', '--quiet', action='store_true',
                        help='Quiet mode - only show open ports')
    
    parser.add_argument('-v', '--version', action='version',
                        version='%(prog)s 1.0 by T3rmuxk1ng')
    
    return parser.parse_args()

# ============================================================================
# MAIN FUNCTION
# ============================================================================

def main():
    """Main entry point"""
    args = parse_arguments()
    
    # Print banner
    if not args.quiet:
        print(f"""
{Colors.CYAN}╔═══════════════════════════════════════════════════════════════╗
║            CUSTOM PORT SCANNER v1.0 - by T3rmuxk1ng            ║
╚═══════════════════════════════════════════════════════════════╝{Colors.END}
""")
    
    # Validate host
    try:
        host = args.host
        # Try to resolve hostname
        socket.gethostbyname(host)
    except socket.gaierror:
        print(f"{Colors.RED}[!] Error: Cannot resolve hostname '{host}'{Colors.END}")
        sys.exit(1)
    
    # Parse port specification
    try:
        if args.ports.lower() == 'common':
            scan_type = 'common'
            start_port = end_port = None
        elif ',' in args.ports:
            # Multiple specific ports
            scan_type = 'specific'
            ports_list = [int(p.strip()) for p in args.ports.split(',')]
        else:
            scan_type = 'range'
            start_port, end_port = parse_port_spec(args.ports)
    except ValueError:
        print(f"{Colors.RED}[!] Error: Invalid port specification{Colors.END}")
        sys.exit(1)
    
    # Initialize scanner
    scanner = PortScanner(
        max_threads=args.threads,
        timeout=args.timeout,
        verbose=not args.quiet
    )
    
    # Run scan
    try:
        if scan_type == 'common':
            results = scanner.scan_common(host)
        elif scan_type == 'specific':
            # Scan specific ports
            scanner.total = len(ports_list)
            scanner.start_time = time.time()
            results = []
            with ThreadPoolExecutor(max_workers=args.threads) as executor:
                futures = {executor.submit(scanner.scan_port, host, p): p 
                          for p in ports_list}
                for future in as_completed(futures):
                    result = future.result()
                    if result:
                        results.append(result)
                        if not args.quiet:
                            scanner._print_result(result)
            results = sorted(results, key=lambda x: x['port'])
        else:
            results = scanner.scan_range(host, start_port, end_port)
        
        # Get statistics
        stats = scanner.get_stats()
        
        # Print summary
        if not args.quiet:
            print_summary(results, host, stats)
        
        # Save output if requested
        if args.output:
            if args.output in ['json', 'both']:
                json_file = save_json_report(results, host, stats)
                print(f"\n{Colors.GREEN}[+] JSON report saved: {json_file}{Colors.END}")
            
            if args.output in ['txt', 'both']:
                txt_file = save_text_report(results, host, stats)
                print(f"{Colors.GREEN}[+] Text report saved: {txt_file}{Colors.END}")
        
    except KeyboardInterrupt:
        print(f"\n{Colors.YELLOW}[!] Scan interrupted by user{Colors.END}")
        sys.exit(130)
    except Exception as e:
        print(f"{Colors.RED}[!] Error: {e}{Colors.END}")
        sys.exit(1)

if __name__ == '__main__':
    main()
```

### Bash Version (port_scanner.sh)

```bash
#!/bin/bash
#
# ╔═══════════════════════════════════════════════════════════════════════════╗
# ║                     CUSTOM PORT SCANNER - BASH                            ║
# ║                        By T3rmuxk1ng | Version 1.0                        ║
# ╠═══════════════════════════════════════════════════════════════════════════╣
# ║  Features:                                                                ║
# ║  • Single/Range port scanning                                             ║
# ║  • Multi-threaded (background jobs)                                       ║
# ║  • Service detection                                                      ║
# ║  • Text report output                                                     ║
# ╚═══════════════════════════════════════════════════════════════════════════╝
#

# ============================================================================
# CONFIGURATION
# ============================================================================

VERSION="1.0"
AUTHOR="T3rmuxk1ng"
DEFAULT_THREADS=50
DEFAULT_TIMEOUT=1

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
BLUE='\033[0;34m'
CYAN='\033[0;36m'
NC='\033[0m' # No Color
BOLD='\033[1m'

# Common ports database
declare -A COMMON_PORTS
COMMON_PORTS[21]="FTP"
COMMON_PORTS[22]="SSH"
COMMON_PORTS[23]="Telnet"
COMMON_PORTS[25]="SMTP"
COMMON_PORTS[53]="DNS"
COMMON_PORTS[80]="HTTP"
COMMON_PORTS[110]="POP3"
COMMON_PORTS[143]="IMAP"
COMMON_PORTS[443]="HTTPS"
COMMON_PORTS[445]="SMB"
COMMON_PORTS[993]="IMAPS"
COMMON_PORTS[995]="POP3S"
COMMON_PORTS[1433]="MSSQL"
COMMON_PORTS[1521]="Oracle"
COMMON_PORTS[3306]="MySQL"
COMMON_PORTS[3389]="RDP"
COMMON_PORTS[5432]="PostgreSQL"
COMMON_PORTS[5900]="VNC"
COMMON_PORTS[6379]="Redis"
COMMON_PORTS[8080]="HTTP-Proxy"
COMMON_PORTS[8443]="HTTPS-Alt"
COMMON_PORTS[27017]="MongoDB"

# Temporary files
TEMP_DIR="/tmp/port_scanner_$$"
RESULTS_FILE="$TEMP_DIR/results.txt"

# ============================================================================
# UTILITY FUNCTIONS
# ============================================================================

# Print colored message
print_color() {
    local color=$1
    local message=$2
    echo -e "${color}${message}${NC}"
}

# Print banner
print_banner() {
    echo -e "${CYAN}"
    echo "╔═══════════════════════════════════════════════════════════════╗"
    echo "║         CUSTOM PORT SCANNER v${VERSION} - by ${AUTHOR}          ║"
    echo "╚═══════════════════════════════════════════════════════════════╝"
    echo -e "${NC}"
}

# Show usage
show_usage() {
    echo -e "${CYAN}Usage:${NC}"
    echo "  $0 [OPTIONS]"
    echo ""
    echo -e "${CYAN}Options:${NC}"
    echo "  -H <host>       Target host (required)"
    echo "  -p <ports>      Port specification:"
    echo "                    - Single port: 80"
    echo "                    - Range: 1-1000"
    echo "                    - Common: 'common'"
    echo "  -t <threads>    Number of threads (default: $DEFAULT_THREADS)"
    echo "  --timeout <sec> Connection timeout (default: ${DEFAULT_TIMEOUT}s)"
    echo "  -o <file>       Output file for report"
    echo "  -q              Quiet mode (only show open ports)"
    echo "  -h              Show this help message"
    echo ""
    echo -e "${CYAN}Examples:${NC}"
    echo "  $0 -H 192.168.1.1 -p 1-1000"
    echo "  $0 -H scanme.nmap.org -p common"
    echo "  $0 -H localhost -p 22,80,443 -o scan_results.txt"
    echo ""
    echo -e "${RED}Disclaimer: Only scan systems you own or have permission to test!${NC}"
}

# Cleanup on exit
cleanup() {
    rm -rf "$TEMP_DIR" 2>/dev/null
    # Kill any background jobs
    jobs -p | xargs kill 2>/dev/null
}

# ============================================================================
# SCANNING FUNCTIONS
# ============================================================================

# Check if a port is open
scan_port() {
    local host=$1
    local port=$2
    local timeout=$3
    local result_file=$4
    
    # Try TCP connection using /dev/tcp
    if (echo >/dev/tcp/$host/$port) 2>/dev/null; then
        # Get service name
        local service="${COMMON_PORTS[$port]:-Unknown}"
        
        # Try to grab banner for some services
        local banner=""
        if [[ $port -eq 22 ]] || [[ $port -eq 80 ]] || [[ $port -eq 21 ]]; then
            banner=$(timeout $timeout bash -c "echo '' | nc $host $port 2>/dev/null" | head -c 100)
        fi
        
        # Save result
        echo "$port|$service|$banner" >> "$result_file"
        echo -e "${GREEN}[+] Port $port: OPEN - $service${NC}"
    fi
}

# Scan range of ports
scan_range() {
    local host=$1
    local start_port=$2
    local end_port=$3
    local threads=$4
    local timeout=$5
    
    local total_ports=$((end_port - start_port + 1))
    local counter=0
    
    print_color "$CYAN" "[*] Scanning $host ports $start_port-$end_port"
    print_color "$CYAN" "[*] Using $threads threads"
    echo ""
    
    # Create temp directory
    mkdir -p "$TEMP_DIR"
    
    # Scan with thread control
    local active_jobs=0
    for port in $(seq $start_port $end_port); do
        # Wait if too many active jobs
        while [[ $active_jobs -ge $threads ]]; do
            wait -n 2>/dev/null
            ((active_jobs--))
        done
        
        # Start background scan
        scan_port "$host" "$port" "$timeout" "$RESULTS_FILE" &
        ((active_jobs++))
        
        # Progress indicator
        ((counter++))
        if [[ $((counter % 100)) -eq 0 ]]; then
            echo -ne "${YELLOW}[*] Progress: $counter/$total_ports ports scanned\r${NC}"
        fi
    done
    
    # Wait for all jobs to complete
    wait
    echo ""
}

# Scan common ports
scan_common() {
    local host=$1
    local threads=$2
    local timeout=$3
    
    local ports="21 22 23 25 53 80 110 143 443 445 993 995 1433 1521 3306 3389 5432 5900 6379 8080 8443 27017"
    local total=$(echo $ports | wc -w)
    
    print_color "$CYAN" "[*] Scanning $host - Top $total common ports"
    echo ""
    
    # Create temp directory
    mkdir -p "$TEMP_DIR"
    
    # Scan each port
    for port in $ports; do
        scan_port "$host" "$port" "$timeout" "$RESULTS_FILE" &
    done
    
    # Wait for all jobs
    wait
}

# Grab banner
grab_banner() {
    local host=$1
    local port=$2
    local timeout=$3
    
    if command -v nc &>/dev/null; then
        timeout $timeout nc -v $host $port 2>&1 | head -1
    fi
}

# ============================================================================
# OUTPUT FUNCTIONS
# ============================================================================

# Print summary
print_summary() {
    local host=$1
    local start_time=$2
    local end_time=$3
    
    local duration=$((end_time - start_time))
    
    echo ""
    echo -e "${CYAN}============================================================${NC}"
    echo -e "${CYAN}SCAN SUMMARY${NC}"
    echo -e "${CYAN}============================================================${NC}"
    echo ""
    echo "Target:        $host"
    echo "Duration:      ${duration} seconds"
    
    if [[ -f "$RESULTS_FILE" ]]; then
        local open_ports=$(wc -l < "$RESULTS_FILE")
        echo "Open Ports:    $open_ports"
        
        if [[ $open_ports -gt 0 ]]; then
            echo ""
            echo -e "${GREEN}Open Ports:${NC}"
            printf "%-8s %-10s %s\n" "PORT" "STATE" "SERVICE"
            echo "----------------------------------------"
            
            while IFS='|' read -r port service banner; do
                printf "%-8s %-10s %s\n" "$port" "OPEN" "$service"
            done < "$RESULTS_FILE"
        fi
    else
        echo "Open Ports:    0"
    fi
    
    echo ""
    echo -e "${CYAN}============================================================${NC}"
}

# Save report
save_report() {
    local output_file=$1
    local host=$2
    local duration=$3
    
    {
        echo "=============================================================="
        echo "                    PORT SCAN REPORT"
        echo "                    By T3rmuxk1ng Scanner"
        echo "=============================================================="
        echo ""
        echo "SCAN INFORMATION"
        echo "--------------------------------------------------------------"
        echo "Target Host:      $host"
        echo "Scan Date:        $(date '+%Y-%m-%d %H:%M:%S')"
        echo "Scan Duration:    ${duration} seconds"
        echo ""
        echo "OPEN PORTS"
        echo "--------------------------------------------------------------"
        printf "%-8s %-10s %-20s\n" "PORT" "STATE" "SERVICE"
        echo "--------------------------------------------------------------"
        
        if [[ -f "$RESULTS_FILE" ]]; then
            while IFS='|' read -r port service banner; do
                printf "%-8s %-10s %-20s\n" "$port" "OPEN" "$service"
            done < "$RESULTS_FILE"
        fi
        
        echo "--------------------------------------------------------------"
        echo ""
        echo "[Scan completed by T3rmuxk1ng Port Scanner v${VERSION}]"
    } > "$output_file"
    
    print_color "$GREEN" "[+] Report saved to: $output_file"
}

# ============================================================================
# MAIN
# ============================================================================

main() {
    # Set trap for cleanup
    trap cleanup EXIT
    
    # Default values
    local host=""
    local port_spec="common"
    local threads=$DEFAULT_THREADS
    local timeout=$DEFAULT_TIMEOUT
    local output_file=""
    local quiet=false
    
    # Parse arguments
    while [[ $# -gt 0 ]]; do
        case $1 in
            -H)
                host="$2"
                shift 2
                ;;
            -p)
                port_spec="$2"
                shift 2
                ;;
            -t)
                threads="$2"
                shift 2
                ;;
            --timeout)
                timeout="$2"
                shift 2
                ;;
            -o)
                output_file="$2"
                shift 2
                ;;
            -q)
                quiet=true
                shift
                ;;
            -h|--help)
                show_usage
                exit 0
                ;;
            *)
                print_color "$RED" "Unknown option: $1"
                show_usage
                exit 1
                ;;
        esac
    done
    
    # Validate required arguments
    if [[ -z "$host" ]]; then
        print_color "$RED" "Error: Target host is required"
        show_usage
        exit 1
    fi
    
    # Print banner
    $quiet || print_banner
    
    # Record start time
    local start_time=$(date +%s)
    
    # Run appropriate scan
    if [[ "$port_spec" == "common" ]]; then
        scan_common "$host" "$threads" "$timeout"
    elif [[ "$port_spec" == *","* ]]; then
        # Multiple specific ports
        IFS=',' read -ra PORTS <<< "$port_spec"
        mkdir -p "$TEMP_DIR"
        for port in "${PORTS[@]}"; do
            scan_port "$host" "$port" "$timeout" "$RESULTS_FILE" &
        done
        wait
    elif [[ "$port_spec" == *"-"* ]]; then
        # Port range
        IFS='-' read -r start_port end_port <<< "$port_spec"
        scan_range "$host" "$start_port" "$end_port" "$threads" "$timeout"
    else
        # Single port
        mkdir -p "$TEMP_DIR"
        scan_port "$host" "$port_spec" "$timeout" "$RESULTS_FILE"
    fi
    
    # Record end time
    local end_time=$(date +%s)
    local duration=$((end_time - start_time))
    
    # Print summary
    $quiet || print_summary "$host" "$start_time" "$end_time"
    
    # Save report if requested
    if [[ -n "$output_file" ]]; then
        save_report "$output_file" "$host" "$duration"
    fi
}

# Run main function
main "$@"
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Single Port Scan

```bash
# Task: Scan a single port on localhost

# Step 1: Install Python and netcat
pkg install python netcat -y

# Step 2: Create the scanner file
# (Copy the Python code above to port_scanner.py)

# Step 3: Make executable
chmod +x port_scanner.py

# Step 4: Test single port
python port_scanner.py -H localhost -p 22

# Expected: Shows if SSH port is open or closed
```

### Exercise 2: Range Scan with Threads

```bash
# Task: Scan a range of ports with different thread counts

# Test with default threads (100)
python port_scanner.py -H localhost -p 1-1000

# Test with more threads (faster)
python port_scanner.py -H localhost -p 1-1000 -t 200

# Test with fewer threads (more stable on slow networks)
python port_scanner.py -H localhost -p 1-1000 -t 50

# Compare scan times
```

### Exercise 3: Common Ports Scan

```bash
# Task: Scan common ports on your local network gateway

# Step 1: Find your gateway
ip route | grep default

# Step 2: Scan common ports
python port_scanner.py -H <gateway_ip> -p common

# Step 3: Save results
python port_scanner.py -H <gateway_ip> -p common -o json

# Expected: Shows open common ports like 22, 80, 443
```

### Exercise 4: Banner Grabbing Analysis

```python
# Task: Create a script that identifies specific services

# Create banner_analyzer.py
cat > banner_analyzer.py << 'EOF'
#!/usr/bin/env python3
"""Banner Analyzer - Identify services from banners"""

BANNERS = {
    'SSH': ['OpenSSH', 'dropbear', 'SSH-2.0'],
    'HTTP': ['nginx', 'Apache', 'Microsoft-IIS', 'lighttpd'],
    'FTP': ['ProFTPD', 'vsftpd', 'FileZilla'],
    'SMTP': ['Postfix', 'Sendmail', 'Exim'],
    'Database': ['MySQL', 'MariaDB', 'PostgreSQL', 'MongoDB']
}

def identify_service(banner):
    """Identify service from banner"""
    if not banner:
        return 'Unknown'
    
    banner_lower = banner.lower()
    
    for service, signatures in BANNERS.items():
        for sig in signatures:
            if sig.lower() in banner_lower:
                return f"{service} (matched: {sig})"
    
    return 'Unknown'

# Test banners
test_banners = [
    "SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.5",
    "HTTP/1.1 200 OK\nServer: nginx/1.18.0",
    "220 ProFTPD 1.3.6 Server (FTP Server)",
]

for banner in test_banners:
    print(f"Banner: {banner[:50]}...")
    print(f"Service: {identify_service(banner)}\n")
EOF

python banner_analyzer.py
```

### Exercise 5: Create a Network Scanner

```bash
# Task: Combine port scanning with network discovery

# Step 1: Create network_scanner.sh
cat > network_scanner.sh << 'EOF'
#!/bin/bash
# Simple Network Scanner by T3rmuxk1ng

NETWORK=$1
PORT=${2:-22}

echo "Scanning network $NETWORK for open port $PORT..."

for i in $(seq 1 254); do
    host="$NETWORK.$i"
    (timeout 1 bash -c "echo >/dev/tcp/$host/$PORT" 2>/dev/null) && \
    echo "[+] $host:$PORT is OPEN" &
done

wait
echo "Scan complete!"
EOF

chmod +x network_scanner.sh

# Step 2: Run (replace 192.168.1 with your network)
./network_scanner.sh 192.168.1 22
```

### Exercise 6: Export and Compare Results

```bash
# Task: Scan same target multiple times and compare

# First scan
python port_scanner.py -H localhost -p 1-100 -o json

# Wait a moment and scan again
sleep 5
python port_scanner.py -H localhost -p 1-100 -o json

# Compare the JSON files
# Look for any differences in open ports
ls -la scan_*.json

# View a report
cat scan_*.txt | head -30
```

### Exercise 7: Bash Scanner Implementation

```bash
# Task: Create and use the Bash version

# Step 1: Create the Bash scanner
# (Copy the Bash code above to port_scanner.sh)

# Step 2: Make executable
chmod +x port_scanner.sh

# Step 3: Run different scans
./port_scanner.sh -H localhost -p common
./port_scanner.sh -H localhost -p 1-100 -t 20
./port_scanner.sh -H localhost -p 22,80,443

# Step 4: Save output
./port_scanner.sh -H localhost -p common -o my_scan.txt
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Permission denied" when creating socket

```bash
# Cause: Some ports require root access

# For ports below 1024, you might need:
# (Note: This is usually for binding, not connecting)

# Solution 1: Check if you're using the correct mode
# Our scanner uses connect() which doesn't need root

# Solution 2: If using raw sockets, switch to TCP connect
# In Python, use socket.SOCK_STREAM (TCP) not SOCK_RAW
```

### Problem 2: Scan is very slow

```bash
# Cause: Low thread count or high timeout

# Solution 1: Increase threads
python port_scanner.py -H target -p 1-1000 -t 200

# Solution 2: Reduce timeout
python port_scanner.py -H target -p 1-1000 --timeout 0.5

# Solution 3: Scan common ports only
python port_scanner.py -H target -p common

# Solution 4: Check network latency
ping -c 3 target
```

### Problem 3: "Connection refused" on all ports

```bash
# Cause: Target host is down or firewall blocking

# Solution 1: Check if host is reachable
ping target
nc -zv target 22

# Solution 2: Check if it's a firewall issue
# Try different ports or common ones
python port_scanner.py -H target -p 80,443,22

# Solution 3: Verify target is correct
# Check for typos in IP/hostname
```

### Problem 4: Inconsistent results between scans

```bash
# Cause: Network instability or rate limiting

# Solution 1: Increase timeout
python port_scanner.py -H target -p 1-100 --timeout 2

# Solution 2: Reduce threads (some hosts rate-limit)
python port_scanner.py -H target -p 1-100 -t 20

# Solution 3: Run multiple times and compare
for i in {1..3}; do
    echo "Scan $i:"
    python port_scanner.py -H target -p common -q
done
```

### Problem 5: Bash version not working

```bash
# Cause: /dev/tcp not available or nc not installed

# Solution 1: Check bash version (need 4+)
bash --version

# Solution 2: Install netcat
pkg install netcat -y

# Solution 3: Check if /dev/tcp is supported
# (It's a bash built-in on most systems)
timeout 1 bash -c "echo >/dev/tcp/localhost/22" && echo "Works"

# Solution 4: Use Python version instead
python port_scanner.py -H localhost -p 22
```

### Problem 6: Memory issues with large scans

```bash
# Cause: Scanning too many ports with too many threads

# Solution 1: Break into smaller chunks
python port_scanner.py -H target -p 1-10000 -t 50

# Solution 2: Use chunked scanning
for chunk in {1..6}; do
    start=$(( (chunk-1)*10000 + 1 ))
    end=$(( chunk*10000 ))
    python port_scanner.py -H target -p $start-$end
done

# Solution 3: Reduce thread count
python port_scanner.py -H target -p 1-65535 -t 50
```

### Problem 7: Cannot resolve hostname

```bash
# Cause: DNS issues or invalid hostname

# Solution 1: Test DNS resolution
nslookup target
dig target

# Solution 2: Use IP address directly
# Get IP from hostname
ping -c 1 target | head -1

# Solution 3: Check internet connection
ping -c 3 8.8.8.8

# Solution 4: Add to /etc/hosts if needed
echo "192.168.1.1 mytarget" >> /etc/hosts
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Technical Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔍 PORT SCANNER                  │
│   Build Your Own Tool!             │
│                                    │
│   ✓ Python + Bash                  │
│   ✓ Multi-threading                │
│   ✓ Banner Grabbing                │
│                                    │
│   [Code snippet preview]           │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Comparison Style**
```
┌────────────────────────────────────┐
│  PYTHON vs BASH                    │
│  ─────────────────────────────────│
│  🐍 Python Version                 │
│     • Fast                         │
│     • Feature-rich                 │
│                                    │
│  🐚 Bash Version                   │
│     • Simple                       │
│     • No dependencies              │
│                                    │
│  BUILD YOUR OWN SCANNER!           │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Action Style**
```
┌────────────────────────────────────┐
│  ⚡ CUSTOM PORT SCANNER ⚡         │
│                                    │
│  [Animated scanning effect]        │
│  [Port numbers scrolling]          │
│                                    │
│  Scan 1000 ports in seconds!       │
│  Multi-threaded | Banner Grab      │
│                                    │
│  T3RMUXK1NG PRESENTS               │
│  Chapter 55                        │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔍 Termux Full Course - Chapter 55: Custom Port Scanner Banayein!

🔥 In this video you'll learn:
• Port Scanning kya hai aur kaise kaam karta hai
• Python se multi-threaded port scanner banana
• Bash se simple port scanner banana
• Banner grabbing aur service detection
• JSON aur text reports generate karna

⏱️ Timestamps:
0:00 - Introduction
1:00 - Port Scanning Explained
5:00 - Scanning Types
8:00 - Project Features
11:00 - Python Implementation
17:00 - Bash Implementation
21:00 - Demo & Testing
23:30 - Ethical Usage Warning
24:30 - Summary

📥 Source Code:
• Python Version: port_scanner.py
• Bash Version: port_scanner.sh

📝 Commands from this video:
pip install python3
pkg install netcat
python port_scanner.py -H localhost -p common

⚠️ DISCLAIMER:
Port scanning can be illegal if done without permission.
Only scan systems you own or have explicit permission to test.
This video is for educational purposes only.

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #PortScanner #EthicalHacking #Python #Bash #T3rmuxk1ng #CyberSecurity #NetworkScanning #TermuxCourse

---
⚠️ Legal Disclaimer: This content is for educational purposes. Unauthorized port scanning is illegal. Always obtain proper authorization before testing any systems.
```

### Tags List

```
port scanner, custom port scanner, python port scanner, bash port scanner,
termux port scanner, network scanning, ethical hacking, cybersecurity,
termux tutorial, termux course, t3rmuxk1ng, banner grabbing, 
multi-threading python, socket programming, network reconnaissance,
port scanning tutorial, hacking tools, security tools, termux projects,
python networking, bash scripting, tcp scan, nmap alternative,
open port scanner, service detection, termux hindi
```

### Hashtags

```
#PortScanner #EthicalHacking #CyberSecurity #Termux #Python #Bash 
#NetworkScanning #TermuxCourse #T3rmuxk1ng #SecurityTools 
#PenetrationTesting #InfoSec #HindiTutorial #SocketProgramming
```

---

## 📚 ADDITIONAL RESOURCES

### Port Reference

| Port Range | Category | Examples |
|------------|----------|----------|
| 0-1023 | Well-Known | SSH(22), HTTP(80), HTTPS(443) |
| 1024-49151 | Registered | MySQL(3306), RDP(3389) |
| 49152-65535 | Dynamic | Ephemeral ports |

### Related Tools

| Tool | Description |
|------|-------------|
| Nmap | Professional network scanner |
| Masscan | Fast Internet-scale scanner |
| Rustscan | Modern fast scanner |
| Netcat | Swiss army knife of networking |

### Learning Resources

| Resource | Link |
|----------|------|
| Nmap Docs | https://nmap.org/docs.html |
| Python Socket | https://docs.python.org/3/library/socket.html |
| Port Database | https://www.iana.org/assignments/service-names-port-numbers/ |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 56, verify:

- [ ] Python port scanner working correctly
- [ ] Tested single port scanning
- [ ] Tested range scanning
- [ ] Tested common ports scan
- [ ] Bash version working
- [ ] Understood multi-threading concept
- [ ] Banner grabbing working
- [ ] Generated JSON/text reports
- [ ] Understood ethical and legal considerations

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 56: Project 6 - File Organizer**

- Automatic file organization
- Extension-based sorting
- Directory monitoring
- Custom rules and patterns
- Backup before organizing

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
