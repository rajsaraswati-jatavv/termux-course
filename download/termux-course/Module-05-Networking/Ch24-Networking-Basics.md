# Chapter 24: Networking Basics in Termux

> **Module:** 5 - Networking  
> **Chapter:** 24 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Network fundamentals, commands, HTTP, APIs |
| Commands Reference | 30+ networking commands covered |
| Practice Exercises | Hands-on network tasks |
| Troubleshooting | Common network issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 24
Title: Networking Basics in Termux | Complete Guide | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum Module 5 ka pehla chapter start kar rahe hain - Networking Basics!

Networking ethical hacking ki foundation hai. Jab aap kisi bhi system 
ya network ko test karte ho, sabse pehle aapko network samajhna hota hai.
IP addresses, ports, protocols, connectivity - ye sab basics hain.

Aaj ke chapter mein hum seekhenge:
- Network fundamentals kya hote hain
- ping command se connectivity test karna
- curl aur wget se data fetch karna
- ifconfig aur ip commands
- netstat aur ss commands
- DNS lookup tools
- HTTP requests aur APIs
- Aur 30+ networking commands

To chaliye shuru karte hain!

---

[SECTION 1: NETWORK FUNDAMENTALS - 1:00 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle networking ke basics samjhte hain.

[ON SCREEN: Network Diagram]

```
    ┌─────────┐          ┌─────────┐
    │ Phone A │ ──────── │ Phone B │
    │.1.1     │  Network │ .1.2    │
    └─────────┘          └─────────┘
          │                    │
          └────────┬───────────┘
                   │
            ┌──────▼──────┐
            │   Router    │
            │  192.168.1.1│
            │   Gateway   │
            └──────┬──────┘
                   │
              ┌────▼────┐
              │ Internet│
              │  (WAN)  │
              └─────────┘
```

**IP Address:**

IP Address har device ka unique identity hota hai network pe.
Jaise ghar ka address - postal service ke liye unique hai.
Waise hi IP address network ke liye unique hai.

IP Address do types ke hote hain:
- IPv4: 192.168.1.100 (4 numbers, dots se separate)
- IPv6: 2001:0db8:85a3:0000:0000:8a2e:0370:7334 (longer format)

IPv4 zyada common hai. IPv6 future ke liye hai kyunki IPv4 addresses 
khatam ho rahe hain.

**Private vs Public IP:**

Private IP: Sirf local network mein valid hai
- 192.168.x.x (home networks)
- 10.x.x.x (large organizations)
- 172.16.x.x to 172.31.x.x

Public IP: Internet pe visible hai, ISP deta hai.

**Port:**

Port ek number hai jo specific service ko identify karta hai.

Common ports yaad rakhein:
- Port 20, 21: FTP (File Transfer)
- Port 22: SSH (Secure Shell)
- Port 23: Telnet
- Port 25: SMTP (Email)
- Port 53: DNS
- Port 80: HTTP (Websites)
- Port 443: HTTPS (Secure Websites)
- Port 3306: MySQL Database
- Port 5432: PostgreSQL

Ports 0-1023: Well-known ports (system reserved)
Ports 1024-49151: Registered ports
Ports 49152-65535: Dynamic/Private ports

**Protocol:**

Protocol rules ka set hai - data kaise communicate hoga.

TCP: Reliable, connection-based
- Guarantee ki data pahunchega
- Used for: Web, Email, SSH

UDP: Fast, connectionless
- No guarantee, but fast
- Used for: Gaming, Streaming, DNS

Yehi fundamentals hai. Ab practical commands start karte hain.

---

[SECTION 2: PING COMMAND - 5:00 to 8:00]
─────────────────────────────────────────────────────────────────────────────

Ping sabse basic aur important network command hai.

Ping ka use connectivity test karne ke liye hota hai - kya device 
reachable hai ya nahi.

Basic syntax:

    ping <ip-or-domain>

Chaliye test karte hain:

    ping -c 4 google.com

[ON SCREEN: Command execution]

Output samjhte hain:

```
PING google.com (142.250.195.78): 56 data bytes
64 bytes from 142.250.195.78: icmp_seq=0 ttl=117 time=25.3 ms
64 bytes from 142.250.195.78: icmp_seq=1 ttl=117 time=24.8 ms
64 bytes from 142.250.195.78: icmp_seq=2 ttl=117 time=26.1 ms
64 bytes from 142.250.195.78: icmp_seq=3 ttl=117 time=25.7 ms

--- google.com ping statistics ---
4 packets transmitted, 4 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 24.8/25.5/26.1/0.5 ms
```

Ye output kya batati hai:
- icmp_seq: Packet number
- ttl: Time to Live (hops before discard)
- time: Response time in milliseconds

Packet loss 0% hona chahiye for good connection.

Ping ke useful options:

    # Specific count
    ping -c 4 google.com
    
    # Interval between packets (seconds)
    ping -i 2 google.com
    
    # Packet size
    ping -s 100 google.com
    
    # Timeout
    ping -W 5 google.com
    
    # Verbose output
    ping -v google.com
    
    # Don't fragment
    ping -M do google.com

Ping troubleshooting ke liye best tool hai. Agar website open nahi 
ho rahi, pehle ping check karein.

Agar ping fail ho raha hai:
1. Check internet connection
2. Check if host is down
3. Check if firewall is blocking ICMP
4. Check DNS resolution

---

[SECTION 3: CURL COMMAND - 8:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Curl ek powerful tool hai HTTP requests ke liye.

Curl se aap:
- Websites fetch kar sakte ho
- APIs call kar sakte ho
- Files download kar sakte ho
- Headers dekh sakte ho
- POST/PUT/DELETE requests bhej sakte ho

Basic usage:

    curl https://example.com

Ye pura HTML return karega.

**Useful Options:**

    # Show response headers
    curl -I https://google.com
    
    # Show both request and response headers
    curl -v https://google.com
    
    # Follow redirects
    curl -L https://google.com
    
    # Save output to file
    curl -o page.html https://example.com
    
    # Download with original filename
    curl -O https://example.com/file.zip
    
    # Silent mode (no progress)
    curl -s https://example.com
    
    # Show error only
    curl -f https://nonexistent.com
    
    # Set timeout
    curl --max-time 10 https://example.com
    
    # Specify HTTP method
    curl -X GET https://api.example.com
    curl -X POST https://api.example.com
    curl -X PUT https://api.example.com
    curl -X DELETE https://api.example.com

**Sending Data:**

    # POST with data
    curl -X POST -d "name=test&email=test@test.com" https://api.example.com/users
    
    # POST JSON data
    curl -X POST -H "Content-Type: application/json" -d '{"name":"test"}' https://api.example.com/users
    
    # POST from file
    curl -X POST -d @data.json https://api.example.com/users

**Headers:**

    # Add custom header
    curl -H "Authorization: Bearer token123" https://api.example.com
    
    # Add multiple headers
    curl -H "Content-Type: application/json" -H "Authorization: Bearer token" https://api.example.com

**Cookies:**

    # Send cookies
    curl -b "session=abc123" https://example.com
    
    # Save cookies from response
    curl -c cookies.txt https://example.com
    
    # Use saved cookies
    curl -b cookies.txt https://example.com

**Authentication:**

    # Basic auth
    curl -u username:password https://api.example.com
    
    # Bearer token
    curl -H "Authorization: Bearer YOUR_TOKEN" https://api.example.com

Curl API testing ke liye perfect hai!

---

[SECTION 4: WGET COMMAND - 12:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

Wget primarily file downloading ke liye use hota hai.

Curl vs Wget:
- Curl: Data transfer, API testing
- Wget: Downloading files, mirroring websites

Basic download:

    wget https://example.com/file.zip

**Useful Options:**

    # Download with different name
    wget -O myfile.zip https://example.com/file.zip
    
    # Resume interrupted download
    wget -c https://example.com/large-file.zip
    
    # Download in background
    wget -b https://example.com/file.zip
    
    # Limit download speed
    wget --limit-rate=200k https://example.com/file.zip
    
    # Retry on failure
    wget -t 5 https://example.com/file.zip
    
    # Download multiple files from list
    wget -i urls.txt
    
    # Mirror entire website
    wget -m https://example.com
    
    # Download specific file types
    wget -r -A.pdf https://example.com
    
    # Ignore robots.txt
    wget -e robots=off https://example.com
    
    # Set user agent
    wget -U "Mozilla/5.0" https://example.com
    
    # Authenticate
    wget --user=username --password=password https://example.com/protected.zip
    
    # Recursive download with depth
    wget -r -l 2 https://example.com

**Practical Examples:**

    # Download GitHub repository archive
    wget https://github.com/user/repo/archive/main.zip
    
    # Download with all required files
    wget -p -k https://example.com/page.html
    
    # Download entire site for offline viewing
    wget --mirror --convert-links --adjust-extension --page-requisites --no-parent https://example.com

Wget bahut powerful hai downloading ke liye!

---

[SECTION 5: IFCONFIG VS IP COMMAND - 15:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Network interfaces check karne ke liye ifconfig aur ip commands use hote hain.

**ifconfig (Old but still useful):**

Termux mein ifconfig ke liye net-tools install karein:

    pkg install net-tools

Usage:

    # Show all interfaces
    ifconfig
    
    # Show specific interface
    ifconfig wlan0
    
    # Show only active interfaces
    ifconfig -s

Output samjhte hain:

```
wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::1a2b:3c4d:5e6f  prefixlen 64  scopeid 0x20<link>
        ether aa:bb:cc:dd:ee:ff  txqueuelen 1000  (Ethernet)
        RX packets 12345  bytes 1234567 (1.2 MB)
        TX packets 54321  bytes 5432109 (5.4 MB)
```

Key fields:
- inet: IPv4 address
- inet6: IPv6 address
- ether: MAC address
- RX packets: Received data
- TX packets: Transmitted data

**ip command (Modern):**

ip command newer hai aur zyada features deta hai.

    # Show all interfaces
    ip addr
    ip a
    
    # Show specific interface
    ip addr show wlan0
    
    # Show IPv4 only
    ip -4 addr
    
    # Show IPv6 only
    ip -6 addr
    
    # Show link status
    ip link
    
    # Show routing table
    ip route
    ip r
    
    # Show default gateway
    ip route | grep default
    
    # Show ARP table
    ip neigh

**Network Statistics:**

    # Show socket statistics
    ss
    
    # Show all sockets
    ss -a
    
    # Show TCP sockets
    ss -t
    
    # Show UDP sockets
    ss -u
    
    # Show listening sockets
    ss -l
    
    # Show with process info
    ss -p
    
    # Show with numeric addresses
    ss -n

Ye commands network troubleshooting ke liye essential hain!

---

[SECTION 6: NETSTAT AND SS COMMANDS - 17:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

netstat aur ss commands se aap network connections dekh sakte ho.

**netstat (Classic):**

    pkg install net-tools

Usage:

    # Show all connections
    netstat -a
    
    # Show TCP connections
    netstat -t
    
    # Show UDP connections
    netstat -u
    
    # Show listening ports
    netstat -l
    
    # Show with PID/Program
    netstat -p
    
    # Show numeric addresses
    netstat -n
    
    # Show routing table
    netstat -r
    
    # Show interface statistics
    netstat -i
    
    # Common combination
    netstat -tulpn
    
    # Continuous monitoring
    netstat -c

**ss (Socket Statistics - Modern):**

ss netstat ka replacement hai - faster aur more detailed.

    # Show all sockets
    ss -a
    
    # Show TCP sockets
    ss -t
    
    # Show UDP sockets
    ss -u
    
    # Show listening sockets
    ss -l
    
    # Show with process info
    ss -p
    
    # Show numeric
    ss -n
    
    # Show established connections
    ss -s
    
    # Common combination
    ss -tulpn
    
    # Filter by state
    ss -t state established
    ss -t state listening
    
    # Filter by port
    ss -t 'sport = :80'
    ss -t 'dport = :443'

**Practical Use Cases:**

    # Check if port is in use
    ss -tulpn | grep :80
    
    # Check all SSH connections
    ss -t | grep :22
    
    # Count connections
    ss -s

---

[SECTION 7: DNS LOOKUP TOOLS - 19:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

DNS lookup tools se aap domain names ka IP address nikal sakte ho 
aur DNS records dekh sakte ho.

**nslookup:**

    pkg install dnsutils

    # Basic lookup
    nslookup google.com
    
    # Query specific DNS server
    nslookup google.com 8.8.8.8
    
    # Query specific record type
    nslookup -type=mx gmail.com
    nslookup -type=ns google.com
    nslookup -type=txt google.com
    
    # Reverse DNS lookup
    nslookup 8.8.8.8

**dig (More Powerful):**

    # Basic query
    dig google.com
    
    # Short answer
    dig +short google.com
    
    # Specific record type
    dig MX gmail.com
    dig NS google.com
    dig TXT google.com
    dig A google.com
    dig AAAA google.com
    dig CNAME www.google.com
    dig SOA google.com
    
    # Use specific DNS server
    dig @8.8.8.8 google.com
    
    # Reverse lookup
    dig -x 8.8.8.8
    
    # Trace DNS path
    dig +trace google.com
    
    # Show only answer
    dig google.com +noall +answer
    
    # Query all record types
    dig google.com ANY

**DNS Record Types:**

    A       - IPv4 address
    AAAA    - IPv6 address
    CNAME   - Canonical name (alias)
    MX      - Mail exchange
    NS      - Name server
    TXT     - Text records
    SOA     - Start of authority
    PTR     - Pointer (reverse DNS)
    SRV     - Service record

---

[SECTION 8: TRACEROUTE - 21:00 to 22:30]
─────────────────────────────────────────────────────────────────────────────

Traceroute se aap dekh sakte ho ki aapka data kahan-kahan se guzarta hai.

    pkg install traceroute

    # Basic traceroute
    traceroute google.com
    
    # Use ICMP
    traceroute -I google.com
    
    # Use TCP
    traceroute -T google.com
    
    # Specify max hops
    traceroute -m 30 google.com
    
    # Specify port
    traceroute -p 443 google.com
    
    # Don't resolve hostnames
    traceroute -n google.com

Output samjhte hain:

```
 1  192.168.1.1 (192.168.1.1)  1.234 ms  1.123 ms  1.111 ms
 2  10.0.0.1 (10.0.0.1)  5.432 ms  5.321 ms  5.234 ms
 3  172.16.0.1 (172.16.0.1)  10.123 ms  10.234 ms  10.345 ms
 4  * * *
 5  google-router.net (142.250.80.46)  25.123 ms  24.987 ms  25.456 ms
```

Har line ek hop hai - ek router jahan se data guzra.
Three times ka measurement hai (round trip time).
`* * *` ka matlab timeout - wo router respond nahi kar raha.

Traceroute network troubleshooting ke liye bahut useful hai:
- Kahan lag rahi hai problem
- Kitna latency hai
- Data ka path kya hai

---

[SECTION 9: HTTP METHODS AND API REQUESTS - 22:30 to 25:00]
─────────────────────────────────────────────────────────────────────────────

Ab HTTP methods aur API requests ke baare mein samjhte hain.

**HTTP Methods:**

GET     - Data retrieve karna
POST    - New data create karna
PUT     - Existing data update karna
PATCH   - Partial update
DELETE  - Data delete karna

**HTTP Status Codes:**

2xx - Success
- 200 OK
- 201 Created
- 204 No Content

3xx - Redirect
- 301 Moved Permanently
- 302 Found
- 304 Not Modified

4xx - Client Error
- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 429 Too Many Requests

5xx - Server Error
- 500 Internal Server Error
- 502 Bad Gateway
- 503 Service Unavailable

**API Request Examples:**

    # GET request
    curl -X GET https://jsonplaceholder.typicode.com/posts
    
    # POST request with JSON
    curl -X POST \
      -H "Content-Type: application/json" \
      -d '{"title":"Test","body":"Content","userId":1}' \
      https://jsonplaceholder.typicode.com/posts
    
    # PUT request
    curl -X PUT \
      -H "Content-Type: application/json" \
      -d '{"title":"Updated"}' \
      https://jsonplaceholder.typicode.com/posts/1
    
    # DELETE request
    curl -X DELETE https://jsonplaceholder.typicode.com/posts/1

**JSON Parsing with jq:**

jq ek powerful tool hai JSON data ko parse karne ke liye.

    pkg install jq

    # Pretty print JSON
    curl -s https://jsonplaceholder.typicode.com/posts/1 | jq
    
    # Get specific field
    curl -s https://jsonplaceholder.typicode.com/posts/1 | jq '.title'
    
    # Get nested field
    curl -s 'https://jsonplaceholder.typicode.com/users/1' | jq '.address.city'
    
    # Get array elements
    curl -s https://jsonplaceholder.typicode.com/posts | jq '.[0]'
    
    # Get all titles
    curl -s https://jsonplaceholder.typicode.com/posts | jq '.[].title'
    
    # Filter data
    curl -s https://jsonplaceholder.typicode.com/posts | jq '.[] | select(.userId == 1)'
    
    # Count elements
    curl -s https://jsonplaceholder.typicode.com/posts | jq 'length'
    
    # Extract multiple fields
    curl -s https://jsonplaceholder.typicode.com/posts/1 | jq '{id, title, body}'

**URL Encoding:**

    pkg install python
    
    # URL encode
    python3 -c "import urllib.parse; print(urllib.parse.quote('hello world'))"
    
    # URL decode
    python3 -c "import urllib.parse; print(urllib.parse.unquote('hello%20world'))"

---

[SECTION 10: 30+ NETWORKING COMMANDS SUMMARY - 25:00 to 27:00]
─────────────────────────────────────────────────────────────────────────────

Ab main aapko 30+ networking commands ka quick summary deta hoon:

┌─────────────────────────────────────────────────────────────────────────┐
│                    NETWORKING COMMANDS CHEAT SHEET                        │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Command              │ Purpose                                          │
├──────────────────────┼──────────────────────────────────────────────────┤
│ ping                 │ Test connectivity                                │
│ curl                 │ HTTP requests, data transfer                     │
│ wget                 │ Download files                                   │
│ ifconfig             │ Network interface info (old)                     │
│ ip addr              │ Network interface info (modern)                  │
│ ip route             │ Routing table                                    │
│ ip link              │ Network links                                    │
│ netstat              │ Network statistics (old)                         │
│ ss                   │ Socket statistics (modern)                       │
│ nslookup             │ DNS lookup                                       │
│ dig                  │ Advanced DNS lookup                              │
│ traceroute           │ Trace packet path                                │
│ tracepath            │ Trace path with MTU                              │
│ host                 │ DNS lookup utility                               │
│ whois                │ Domain info lookup                               │
│ nc/netcat            │ Network utility tool                             │
│ nmap                 │ Network scanner                                  │
│ arp                  │ ARP table manipulation                           │
│ route                │ Routing table (old)                              │
│ iwconfig             │ Wireless interface config                        │
│ iw                   │ Wireless interface (modern)                      │
│ hostname             │ Show/set hostname                                │
│ dnsdomainname        │ Show DNS domain name                             │
│ ntpdate              │ Sync time with NTP server                        │
│ scp                  │ Secure copy over SSH                             │
│ sftp                 │ Secure file transfer                             │
│ rsync                │ File synchronization                             │
│ ssh                  │ Secure shell client                              │
│ telnet               │ Telnet protocol client                           │
│ ftp                  │ FTP client                                       │
│ tftp                 │ Trivial FTP client                               │
│ curl                 │ Transfer data with URLs                          │
│ httping              │ Ping HTTP servers                                │
│ mtr                  │ My traceroute (combined ping+trace)              │
│ hping3               │ Packet crafting tool                             │
└──────────────────────┴──────────────────────────────────────────────────┘

Ye commands install karna padega Termux mein:

    pkg install net-tools curl wget dnsutils traceroute jq

---

[SECTION 11: SUMMARY & NEXT CHAPTER PREVIEW - 27:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 24 complete! Let's summarize:

✅ Network fundamentals - IP, Ports, Protocols
✅ ping command - Connectivity testing
✅ curl command - HTTP requests aur API testing
✅ wget command - File downloading
✅ ifconfig vs ip - Network interface info
✅ netstat aur ss - Connection statistics
✅ DNS lookup - nslookup, dig
✅ traceroute - Path tracing
✅ HTTP methods - GET, POST, PUT, DELETE
✅ jq - JSON parsing
✅ 30+ networking commands

Important commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 24 - IMPORTANT COMMANDS                        │
├─────────────────────────────────────────────────────────────────────────┤
│ ping -c 4 google.com              │ Test connectivity                   │
│ curl -I https://google.com        │ Get HTTP headers                    │
│ curl -X POST -d '{"key":"val"}'   │ POST JSON data                      │
│ wget -c URL                       │ Resume download                     │
│ ip addr                           │ Show IP addresses                   │
│ ip route                          │ Show routing table                  │
│ ss -tulpn                         │ Show listening ports                │
│ dig +short google.com             │ Quick DNS lookup                    │
│ traceroute google.com             │ Trace network path                  │
│ jq '.' file.json                  │ Pretty print JSON                   │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 25 mein hum seekhenge:
- Nmap installation
- Nmap basics
- Port scanning techniques
- Service detection
- OS detection
- Nmap scripting engine

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 25!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Network Fundamentals

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         NETWORK FUNDAMENTALS                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                        OSI MODEL                                 │    │
│  ├─────────────────────────────────────────────────────────────────┤    │
│  │  Layer 7  │ Application   │ HTTP, FTP, DNS, SSH               │    │
│  │  Layer 6  │ Presentation  │ SSL/TLS, JPEG, JSON               │    │
│  │  Layer 5  │ Session       │ NetBIOS, RPC                      │    │
│  │  Layer 4  │ Transport     │ TCP, UDP                          │    │
│  │  Layer 3  │ Network       │ IP, ICMP, IPSec                   │    │
│  │  Layer 2  │ Data Link     │ Ethernet, WiFi, MAC               │    │
│  │  Layer 1  │ Physical      │ Cables, Radio Waves               │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                        IP ADDRESS TYPES                          │    │
│  ├─────────────────────────────────────────────────────────────────┤    │
│  │  IPv4: 32-bit (4 octets)    │ Example: 192.168.1.1             │    │
│  │  IPv6: 128-bit (8 groups)   │ Example: 2001:db8::1             │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                    PRIVATE IP RANGES                             │    │
│  ├─────────────────────────────────────────────────────────────────┤    │
│  │  Class A: 10.0.0.0 - 10.255.255.255                             │    │
│  │  Class B: 172.16.0.0 - 172.31.255.255                           │    │
│  │  Class C: 192.168.0.0 - 192.168.255.255                         │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Common Ports Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         COMMON PORTS REFERENCE                           │
├─────────┬───────────────┬───────────────────────────────────────────────┤
│ Port    │ Service       │ Description                                   │
├─────────┼───────────────┼───────────────────────────────────────────────┤
│ 20      │ FTP Data      │ File Transfer Protocol (data)                 │
│ 21      │ FTP Control   │ File Transfer Protocol (control)              │
│ 22      │ SSH           │ Secure Shell                                  │
│ 23      │ Telnet        │ Telnet Protocol (insecure)                    │
│ 25      │ SMTP          │ Simple Mail Transfer Protocol                 │
│ 53      │ DNS           │ Domain Name System                            │
│ 67/68   │ DHCP          │ Dynamic Host Configuration Protocol           │
│ 69      │ TFTP          │ Trivial File Transfer Protocol                │
│ 80      │ HTTP          │ Hypertext Transfer Protocol                   │
│ 110     │ POP3          │ Post Office Protocol v3                       │
│ 119     │ NNTP          │ Network News Transfer Protocol                │
│ 123     │ NTP           │ Network Time Protocol                         │
│ 143     │ IMAP          │ Internet Message Access Protocol              │
│ 161     │ SNMP          │ Simple Network Management Protocol            │
│ 194     │ IRC           │ Internet Relay Chat                           │
│ 389     │ LDAP          │ Lightweight Directory Access Protocol         │
│ 443     │ HTTPS         │ HTTP Secure                                   │
│ 465     │ SMTPS         │ SMTP over SSL                                 │
│ 514     │ Syslog        │ System Logging Protocol                       │
│ 587     │ SMTP          │ SMTP (submission)                             │
│ 636     │ LDAPS         │ LDAP over SSL                                 │
│ 993     │ IMAPS         │ IMAP over SSL                                 │
│ 995     │ POP3S         │ POP3 over SSL                                 │
│ 1433    │ MS-SQL        │ Microsoft SQL Server                          │
│ 1521    │ Oracle        │ Oracle Database                               │
│ 3306    │ MySQL         │ MySQL Database                                │
│ 3389    │ RDP           │ Remote Desktop Protocol                       │
│ 5432    │ PostgreSQL    │ PostgreSQL Database                           │
│ 5900    │ VNC           │ Virtual Network Computing                     │
│ 6379    │ Redis         │ Redis Database                                │
│ 8080    │ HTTP Proxy    │ HTTP Proxy / Alternate HTTP                   │
│ 8443    │ HTTPS Alt     │ Alternate HTTPS                               │
│ 27017   │ MongoDB       │ MongoDB Database                              │
└─────────┴───────────────┴───────────────────────────────────────────────┘
```

### 3. HTTP Request/Response Structure

```
┌─────────────────────────────────────────────────────────────────────────┐
│                       HTTP REQUEST STRUCTURE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  GET /api/users HTTP/1.1                                                 │
│  Host: example.com                                                       │
│  User-Agent: curl/7.68.0                                                 │
│  Accept: application/json                                                │
│  Authorization: Bearer token123                                          │
│  Content-Type: application/json                                          │
│                                                                          │
│  {"query": "search term"}                                                │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  1. Request Line: METHOD PATH VERSION                            │    │
│  │  2. Headers: Key: Value pairs                                    │    │
│  │  3. Empty Line: Separator                                        │    │
│  │  4. Body: Data (for POST/PUT/PATCH)                              │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│                      HTTP RESPONSE STRUCTURE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  HTTP/1.1 200 OK                                                         │
│  Date: Mon, 01 Jan 2024 12:00:00 GMT                                     │
│  Server: nginx/1.18.0                                                    │
│  Content-Type: application/json                                          │
│  Content-Length: 1234                                                    │
│  Connection: keep-alive                                                  │
│                                                                          │
│  {"status": "success", "data": [...]}                                    │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │  1. Status Line: VERSION STATUS_CODE STATUS_TEXT                 │    │
│  │  2. Headers: Key: Value pairs                                    │    │
│  │  3. Empty Line: Separator                                        │    │
│  │  4. Body: Response data                                          │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. DNS Record Types

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         DNS RECORD TYPES                                 │
├─────────┬───────────────────────────────────────────────────────────────┤
│ Type    │ Description                                                   │
├─────────┼───────────────────────────────────────────────────────────────┤
│ A       │ Maps domain to IPv4 address                                   │
│ AAAA    │ Maps domain to IPv6 address                                   │
│ CNAME   │ Alias of one domain to another                                │
│ MX      │ Mail exchange servers for domain                              │
│ NS      │ Authoritative name servers                                    │
│ PTR     │ Reverse DNS lookup (IP to domain)                             │
│ SOA     │ Start of Authority record                                     │
│ SRV     │ Service location (port and weight)                            │
│ TXT     │ Text records (SPF, DKIM, verification)                        │
│ CAA     │ Certificate Authority Authorization                           │
│ DMARC   │ Domain-based Message Authentication                           │
│ DKIM    │ DomainKeys Identified Mail                                    │
│ SPF     │ Sender Policy Framework                                       │
└─────────┴───────────────────────────────────────────────────────────────┘
```

### 5. curl Options Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         CURL OPTIONS REFERENCE                           │
├─────────────────────┬───────────────────────────────────────────────────┤
│ Option              │ Description                                       │
├─────────────────────┼───────────────────────────────────────────────────┤
│ -X, --request       │ HTTP method (GET, POST, PUT, DELETE)             │
│ -H, --header        │ Add header                                        │
│ -d, --data          │ Send data (form/JSON)                             │
│ --data-raw          │ Send raw data without processing                  │
│ --data-urlencode    │ URL encode data                                   │
│ -F, --form          │ Send multipart form data                          │
│ -I, --head          │ Fetch headers only                                │
│ -i, --include       │ Include headers in output                         │
│ -v, --verbose       │ Verbose output                                    │
│ -s, --silent        │ Silent mode                                       │
│ -S, --show-error    │ Show errors in silent mode                        │
│ -L, --location      │ Follow redirects                                  │
│ -o, --output        │ Write output to file                              │
│ -O, --remote-name   │ Write output with remote filename                 │
│ -u, --user          │ Username and password                             │
│ -k, --insecure      │ Skip SSL verification                             │
│ -x, --proxy         │ Use proxy                                         │
│ --connect-timeout   │ Connection timeout (seconds)                      │
│ --max-time          │ Maximum time for request                          │
│ --retry             │ Number of retries                                 │
│ -A, --user-agent    │ User-Agent header                                 │
│ -b, --cookie        │ Send cookies                                      │
│ -c, --cookie-jar    │ Save cookies to file                              │
│ -e, --referer       │ Referer header                                    │
│ --compressed        │ Request compressed response                       │
│ -T, --upload-file   │ Upload file                                       │
│ --limit-rate        │ Limit transfer speed                              │
└─────────────────────┴───────────────────────────────────────────────────┘
```

### 6. jq Command Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          JQ COMMAND REFERENCE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  # Basic Filters                                                         │
│  jq '.'              # Pretty print                                      │
│  jq '.key'           # Get specific key                                  │
│  jq '.key.nested'    # Get nested value                                  │
│  jq '.[0]'           # Get array element                                 │
│  jq '.[]'            # Iterate all elements                              │
│  jq '.[].key'        # Get key from all elements                         │
│                                                                          │
│  # Selection & Filtering                                                 │
│  jq 'select(.age > 18)'           # Conditional selection               │
│  jq '.[] | select(.active)'       # Filter by boolean                   │
│  jq 'map(select(.id > 5))'        # Map with filter                     │
│                                                                          │
│  # Transformation                                                        │
│  jq 'map(.price * 1.1)'           # Transform values                    │
│  jq 'sort_by(.name)'              # Sort array                          │
│  jq 'group_by(.category)'         # Group elements                      │
│  jq 'unique'                      # Remove duplicates                   │
│  jq 'reverse'                     # Reverse array                       │
│                                                                          │
│  # Object Creation                                                       │
│  jq '{name, age}'                 # Create new object                   │
│  jq '{user: .username}'           # Rename keys                         │
│                                                                          │
│  # String Operations                                                     │
│  jq 'length'                      # Length of string/array              │
│  jq 'split(",")'                  # Split string                        │
│  jq 'join(",")'                   # Join array                          │
│  jq 'ascii_downcase'              # Lowercase                           │
│  jq 'ascii_upcase'                # Uppercase                           │
│  jq 'gsub("old"; "new")'          # Replace all                        │
│                                                                          │
│  # Math                                                                  │
│  jq 'add'                         # Sum of array                        │
│  jq 'min'                         # Minimum value                       │
│  jq 'max'                         # Maximum value                       │
│  jq 'floor'                       # Round down                          │
│  jq 'sqrt'                        # Square root                         │
│                                                                          │
│  # Useful Combinations                                                   │
│  jq 'keys'                        # Get all keys                        │
│  jq 'values'                      # Get all values                      │
│  jq 'to_entries'                  # Convert to key-value pairs          │
│  jq 'from_entries'                # Convert back from entries           │
│  jq 'has("key")'                  # Check if key exists                 │
│  jq 'type'                        # Get value type                      │
│  jq 'empty'                       # Produce no output                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### Connectivity Testing

```bash
# Basic ping
ping google.com

# Ping with count
ping -c 4 google.com

# Ping with interval
ping -i 2 google.com

# Ping with packet size
ping -s 1000 google.com

# Ping with timeout
ping -W 5 google.com

# Don't fragment ping
ping -M do -s 1472 google.com

# Flood ping (root required)
ping -f google.com

# HTTP ping
pkg install httping
httping google.com
httping -c 5 google.com

# MTR (My Traceroute)
pkg install mtr
mtr google.com
```

### HTTP Requests with curl

```bash
# Basic GET request
curl https://example.com

# GET with headers shown
curl -i https://example.com

# GET headers only
curl -I https://example.com

# Follow redirects
curl -L https://example.com

# Save to file
curl -o output.html https://example.com

# Download with original name
curl -O https://example.com/file.zip

# POST form data
curl -X POST -d "name=John&age=30" https://api.example.com/users

# POST JSON
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"name":"John","age":30}' \
  https://api.example.com/users

# POST from file
curl -X POST -d @data.json https://api.example.com/users

# PUT request
curl -X PUT \
  -H "Content-Type: application/json" \
  -d '{"name":"John Updated"}' \
  https://api.example.com/users/1

# DELETE request
curl -X DELETE https://api.example.com/users/1

# Basic authentication
curl -u username:password https://api.example.com

# Bearer token
curl -H "Authorization: Bearer YOUR_TOKEN" https://api.example.com

# Add custom headers
curl -H "X-Custom-Header: value" https://api.example.com

# Send cookies
curl -b "session=abc123" https://example.com

# Save cookies
curl -c cookies.txt https://example.com

# Use saved cookies
curl -b cookies.txt https://example.com

# User agent
curl -A "Mozilla/5.0" https://example.com

# Proxy
curl -x http://proxy:8080 https://example.com

# Timeout
curl --connect-timeout 10 --max-time 30 https://example.com

# Retry on failure
curl --retry 3 https://example.com

# Silent mode
curl -s https://example.com

# Verbose mode
curl -v https://example.com

# Skip SSL verification
curl -k https://self-signed.example.com

# Upload file
curl -T file.txt https://example.com/upload

# Multiple requests
curl -O https://example.com/file1.zip -O https://example.com/file2.zip
```

### File Download with wget

```bash
# Basic download
wget https://example.com/file.zip

# Download with different name
wget -O myfile.zip https://example.com/file.zip

# Resume download
wget -c https://example.com/large-file.zip

# Background download
wget -b https://example.com/file.zip

# Download from list
wget -i urls.txt

# Limit speed
wget --limit-rate=200k https://example.com/file.zip

# Retry count
wget -t 5 https://example.com/file.zip

# Mirror website
wget -m https://example.com

# Download recursively
wget -r https://example.com

# Download specific file types
wget -r -A.pdf https://example.com

# Ignore robots.txt
wget -e robots=off https://example.com

# Authentication
wget --user=username --password=password https://example.com/protected

# Set user agent
wget -U "Mozilla/5.0" https://example.com

# Complete mirror options
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent https://example.com
```

### Network Interface Commands

```bash
# Show all interfaces (ifconfig)
ifconfig

# Show specific interface
ifconfig wlan0

# Show interface statistics
ifconfig -s

# Show all interfaces (ip)
ip addr
ip a

# Show specific interface
ip addr show wlan0

# Show IPv4 only
ip -4 addr

# Show IPv6 only
ip -6 addr

# Show link status
ip link

# Bring interface up/down
ip link set wlan0 up
ip link set wlan0 down

# Show routing table
ip route
ip r

# Show default gateway
ip route | grep default

# Add route
ip route add 192.168.2.0/24 via 192.168.1.1

# Delete route
ip route del 192.168.2.0/24

# Show ARP table
ip neigh
ip n

# Flush ARP cache
ip neigh flush all

# Show hostname
hostname

# Show DNS domain
dnsdomainname
```

### Connection Statistics

```bash
# Show all connections (netstat)
netstat -a

# Show TCP connections
netstat -t

# Show UDP connections
netstat -u

# Show listening sockets
netstat -l

# Show with PIDs
netstat -p

# Show numeric
netstat -n

# Common combination
netstat -tulpn

# Show routing table
netstat -r

# Show interface statistics
netstat -i

# Continuous monitoring
netstat -c

# Show all sockets (ss)
ss -a

# Show TCP sockets
ss -t

# Show UDP sockets
ss -u

# Show listening sockets
ss -l

# Show with PIDs
ss -p

# Show numeric
ss -n

# Show statistics
ss -s

# Common combination
ss -tulpn

# Filter by state
ss -t state established
ss -t state listening

# Filter by port
ss -t 'sport = :80'
ss -t 'dport = :443'

# Check specific port
ss -tulpn | grep :80
```

### DNS Commands

```bash
# Basic nslookup
nslookup google.com

# Use specific DNS server
nslookup google.com 8.8.8.8

# Query specific record
nslookup -type=mx gmail.com
nslookup -type=ns google.com
nslookup -type=txt google.com

# Reverse lookup
nslookup 8.8.8.8

# Basic dig
dig google.com

# Short answer
dig +short google.com

# Specific record types
dig A google.com
dig AAAA google.com
dig MX gmail.com
dig NS google.com
dig TXT google.com
dig CNAME www.google.com
dig SOA google.com
dig ANY google.com

# Use specific DNS server
dig @8.8.8.8 google.com

# Reverse lookup
dig -x 8.8.8.8

# Trace query
dig +trace google.com

# Show only answer
dig google.com +noall +answer

# Query multiple domains
dig google.com yahoo.com

# host command
host google.com
host -t mx gmail.com
host 8.8.8.8

# whois lookup
pkg install whois
whois google.com
```

### Traceroute Commands

```bash
# Basic traceroute
traceroute google.com

# Use ICMP
traceroute -I google.com

# Use TCP
traceroute -T google.com

# Specify max hops
traceroute -m 30 google.com

# Specify port
traceroute -p 443 google.com

# Don't resolve hostnames
traceroute -n google.com

# tracepath (no root required)
pkg install iputils
tracepath google.com

# MTR (My Traceroute)
mtr google.com
mtr -c 10 google.com
mtr -r google.com  # Report mode
```

### JSON Processing with jq

```bash
# Install jq
pkg install jq

# Pretty print
curl -s https://jsonplaceholder.typicode.com/posts/1 | jq

# Get specific field
curl -s https://jsonplaceholder.typicode.com/posts/1 | jq '.title'

# Get nested field
curl -s 'https://jsonplaceholder.typicode.com/users/1' | jq '.address.city'

# Get array element
curl -s https://jsonplaceholder.typicode.com/posts | jq '.[0]'

# Get all titles
curl -s https://jsonplaceholder.typicode.com/posts | jq '.[].title'

# Filter data
curl -s https://jsonplaceholder.typicode.com/posts | jq '.[] | select(.userId == 1)'

# Count elements
curl -s https://jsonplaceholder.typicode.com/posts | jq 'length'

# Extract multiple fields
curl -s https://jsonplaceholder.typicode.com/posts/1 | jq '{id, title, body}'

# Create new object
curl -s https://jsonplaceholder.typicode.com/posts/1 | jq '{post_id: .id, post_title: .title}'

# Sort by field
curl -s https://jsonplaceholder.typicode.com/posts | jq 'sort_by(.id)'

# Get unique values
curl -s https://jsonplaceholder.typicode.com/posts | jq '[.[].userId] | unique'

# Process local file
jq '.' data.json
jq '.users' data.json
```

### URL Encoding

```bash
# URL encode
python3 -c "import urllib.parse; print(urllib.parse.quote('hello world'))"
# Output: hello%20world

# URL decode
python3 -c "import urllib.parse; print(urllib.parse.unquote('hello%20world'))"
# Output: hello world

# Encode with safe characters
python3 -c "import urllib.parse; print(urllib.parse.quote('hello world', safe=''))"

# Encode dictionary
python3 -c "import urllib.parse; print(urllib.parse.urlencode({'name': 'John Doe', 'age': 30}))"
# Output: name=John+Doe&age=30

# Using jq for URL encoding
jq -Rr '@uri' <<< "hello world"
```

### Miscellaneous Network Commands

```bash
# Show open files and network connections
lsof -i
lsof -i :80

# Check if port is open (netcat)
nc -zv google.com 80
nc -zv google.com 80-443

# Get public IP
curl ifconfig.me
curl icanhazip.com
curl ipinfo.io/ip

# Get IP info
curl ipinfo.io

# Check HTTP headers
curl -I https://google.com

# Download speed test
curl -o /dev/null -w "Speed: %{speed_download} bytes/sec\n" https://example.com/large-file

# Check if website is up
curl -Is https://google.com | head -n 1

# HTTP status code only
curl -s -o /dev/null -w "%{http_code}" https://google.com

# Network speed (iperf - requires server)
pkg install iperf3
iperf3 -c server.ip

# Wake on LAN
pkg install wakeonlan
wakeonlan AA:BB:CC:DD:EE:FF

# Check bandwidth
pkg install nload
nload

# Network monitoring
pkg install iftop
iftop
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Connectivity Testing

```bash
# Task: Test connectivity to various hosts

# Step 1: Test basic connectivity
ping -c 4 google.com

# Step 2: Test with different packet sizes
ping -c 4 -s 100 google.com
ping -c 4 -s 1000 google.com

# Step 3: Check if host is reachable
ping -c 1 google.com && echo "Host is up" || echo "Host is down"

# Step 4: Test multiple hosts
for host in google.com youtube.com github.com; do
    ping -c 1 $host > /dev/null && echo "$host is up" || echo "$host is down"
done

# Step 5: Check your public IP
curl ifconfig.me

# Expected: Your public IP address displayed
```

### Exercise 2: HTTP Requests

```bash
# Task: Make various HTTP requests

# Step 1: Simple GET request
curl https://jsonplaceholder.typicode.com/posts

# Step 2: Get specific resource
curl https://jsonplaceholder.typicode.com/posts/1

# Step 3: Get headers only
curl -I https://jsonplaceholder.typicode.com/posts/1

# Step 4: POST request with JSON
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"title":"My Post","body":"This is content","userId":1}' \
  https://jsonplaceholder.typicode.com/posts

# Step 5: PUT request
curl -X PUT \
  -H "Content-Type: application/json" \
  -d '{"title":"Updated Title"}' \
  https://jsonplaceholder.typicode.com/posts/1

# Step 6: DELETE request
curl -X DELETE https://jsonplaceholder.typicode.com/posts/1

# Step 7: Check HTTP status code
curl -s -o /dev/null -w "%{http_code}\n" https://jsonplaceholder.typicode.com/posts/1
```

### Exercise 3: JSON Processing

```bash
# Task: Process JSON data with jq

# Step 1: Install jq
pkg install jq -y

# Step 2: Pretty print JSON
curl -s https://jsonplaceholder.typicode.com/posts/1 | jq

# Step 3: Extract specific fields
curl -s https://jsonplaceholder.typicode.com/posts/1 | jq '.title'

# Step 4: Get nested data
curl -s 'https://jsonplaceholder.typicode.com/users/1' | jq '.address'

# Step 5: Get all user names
curl -s https://jsonplaceholder.typicode.com/users | jq '.[].name'

# Step 6: Filter posts by user
curl -s https://jsonplaceholder.typicode.com/posts | jq '.[] | select(.userId == 1)'

# Step 7: Create custom output
curl -s https://jsonplaceholder.typicode.com/users/1 | \
  jq '{name: .name, email: .email, city: .address.city}'

# Step 8: Count items
curl -s https://jsonplaceholder.typicode.com/posts | jq 'length'

# Step 9: Sort by field
curl -s https://jsonplaceholder.typicode.com/posts | jq 'sort_by(.id) | .[-3:]'
```

### Exercise 4: DNS Investigation

```bash
# Task: Investigate DNS records

# Step 1: Install DNS tools
pkg install dnsutils -y

# Step 2: Basic lookup
dig google.com

# Step 3: Get only the answer
dig +short google.com

# Step 4: Query specific record types
dig A google.com +short
dig AAAA google.com +short
dig MX gmail.com +short
dig NS google.com +short
dig TXT google.com +short

# Step 5: Use specific DNS server
dig @8.8.8.8 google.com

# Step 6: Reverse lookup
dig -x 8.8.8.8

# Step 7: Trace DNS query
dig +trace google.com

# Step 8: Create a DNS lookup script
cat > dns_check.sh << 'EOF'
#!/bin/bash
DOMAIN=$1
echo "=== DNS Records for $DOMAIN ==="
echo "A Record: $(dig +short A $DOMAIN)"
echo "AAAA Record: $(dig +short AAAA $DOMAIN)"
echo "MX Record: $(dig +short MX $DOMAIN)"
echo "NS Record: $(dig +short NS $DOMAIN)"
EOF

chmod +x dns_check.sh
./dns_check.sh google.com
```

### Exercise 5: Network Scanner Script

```bash
# Task: Create a simple network information script

cat > network_info.sh << 'EOF'
#!/bin/bash

echo "═══════════════════════════════════════════════════"
echo "           NETWORK INFORMATION SCRIPT"
echo "═══════════════════════════════════════════════════"

echo ""
echo "📡 Network Interfaces:"
ip -4 addr show | grep inet

echo ""
echo "🌐 Public IP Address:"
curl -s ifconfig.me

echo ""
echo "🚪 Default Gateway:"
ip route | grep default

echo ""
echo "📋 DNS Servers:"
cat /data/data/com.termux/files/usr/etc/resolv.conf 2>/dev/null || echo "DNS info not accessible"

echo ""
echo "🔌 Listening Ports:"
ss -tlnp 2>/dev/null || netstat -tlnp 2>/dev/null

echo ""
echo "🌐 Connectivity Test:"
ping -c 2 google.com > /dev/null && echo "✅ Internet is working" || echo "❌ No internet connection"

echo ""
echo "═══════════════════════════════════════════════════"
EOF

chmod +x network_info.sh
./network_info.sh
```

### Exercise 6: API Testing Script

```bash
# Task: Create an API testing script

cat > api_test.sh << 'EOF'
#!/bin/bash

API_URL="https://jsonplaceholder.typicode.com"

echo "═══════════════════════════════════════════════════"
echo "           API TESTING SCRIPT"
echo "═══════════════════════════════════════════════════"

echo ""
echo "1️⃣ GET Request - All Posts"
curl -s "$API_URL/posts" | jq '.[0:3]'

echo ""
echo "2️⃣ GET Request - Single Post"
curl -s "$API_URL/posts/1" | jq

echo ""
echo "3️⃣ POST Request - Create Post"
curl -s -X POST \
  -H "Content-Type: application/json" \
  -d '{"title":"Test Post","body":"Test Body","userId":1}' \
  "$API_URL/posts" | jq

echo ""
echo "4️⃣ PUT Request - Update Post"
curl -s -X PUT \
  -H "Content-Type: application/json" \
  -d '{"title":"Updated Post"}' \
  "$API_URL/posts/1" | jq

echo ""
echo "5️⃣ DELETE Request"
curl -s -X DELETE "$API_URL/posts/1" | jq

echo ""
echo "6️⃣ Response Headers"
curl -s -I "$API_URL/posts" | head -10

echo ""
echo "7️⃣ Status Code Check"
STATUS=$(curl -s -o /dev/null -w "%{http_code}" "$API_URL/posts")
echo "HTTP Status Code: $STATUS"

echo ""
echo "═══════════════════════════════════════════════════"
EOF

chmod +x api_test.sh
./api_test.sh
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "ping: command not found"

```bash
# Cause: ping not installed

# Solution: Install iputils
pkg install iputils -y

# Alternative: Install inetutils
pkg install inetutils -y

# Verify installation
which ping
```

### Problem 2: "curl: command not found"

```bash
# Cause: curl not installed

# Solution:
pkg install curl -y

# Verify
curl --version
```

### Problem 3: "Temporary failure in name resolution"

```bash
# Cause: DNS not working

# Solution 1: Check internet connection
ping -c 2 8.8.8.8

# Solution 2: Use IP instead of domain
ping -c 2 8.8.8.8  # Google DNS

# Solution 3: Check DNS servers
cat /data/data/com.termux/files/usr/etc/resolv.conf

# Solution 4: Change DNS
echo "nameserver 8.8.8.8" > /data/data/com.termux/files/usr/etc/resolv.conf
echo "nameserver 8.8.4.4" >> /data/data/com.termux/files/usr/etc/resolv.conf
```

### Problem 4: "Permission denied" for network commands

```bash
# Cause: Some network commands require root or specific permissions

# Solution 1: Commands that work without root
ping -c 4 google.com
curl https://example.com
wget https://example.com
dig google.com

# Solution 2: For root-required commands
# You need a rooted device or use proot

# Solution 3: Use alternatives
# Instead of: traceroute -I google.com (requires root)
# Use: traceroute google.com (works without root)
```

### Problem 5: "Could not resolve host"

```bash
# Cause: DNS resolution failure

# Solution 1: Check internet
ping -c 2 8.8.8.8

# Solution 2: Use different DNS
echo "nameserver 1.1.1.1" > /data/data/com.termux/files/usr/etc/resolv.conf

# Solution 3: Check hosts file
cat /data/data/com.termux/files/usr/etc/hosts

# Solution 4: Add entry to hosts
echo "142.250.195.78 google.com" >> /data/data/com.termux/files/usr/etc/hosts
```

### Problem 6: wget/curl download fails

```bash
# Cause: SSL issues, network problems, or restrictions

# Solution 1: Skip SSL verification
curl -k https://example.com
wget --no-check-certificate https://example.com

# Solution 2: Use different user agent
curl -A "Mozilla/5.0" https://example.com
wget -U "Mozilla/5.0" https://example.com

# Solution 3: Increase timeout
curl --max-time 60 https://example.com
wget --timeout=60 https://example.com

# Solution 4: Resume failed download
wget -c https://example.com/large-file.zip

# Solution 5: Use different protocol
curl -L --proto-redir =https https://example.com
```

### Problem 7: jq not parsing JSON correctly

```bash
# Cause: Invalid JSON or incorrect jq syntax

# Solution 1: Validate JSON first
curl -s https://api.example.com/data | jq '.' > /dev/null
if [ $? -eq 0 ]; then
    echo "Valid JSON"
else
    echo "Invalid JSON"
fi

# Solution 2: Check raw output
curl -s https://api.example.com/data

# Solution 3: Use -r flag for raw strings
curl -s https://api.example.com/data | jq -r '.name'

# Solution 4: Debug jq
curl -s https://api.example.com/data | jq 'debug'
```

### Problem 8: Network commands slow or hanging

```bash
# Cause: IPv6 resolution issues or slow DNS

# Solution 1: Force IPv4
curl -4 https://example.com
wget -4 https://example.com
ping -4 google.com

# Solution 2: Use faster DNS
echo "nameserver 1.1.1.1" > /data/data/com.termux/files/usr/etc/resolv.conf

# Solution 3: Add timeout
curl --connect-timeout 10 --max-time 30 https://example.com

# Solution 4: Disable DNS caching issues
# Restart Termux completely
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🌐 NETWORKING BASICS             │
│   in TERMUX                        │
│                                    │
│   ✓ 30+ Commands                   │
│   ✓ ping, curl, wget               │
│   ✓ API Testing                    │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Command Focus**
```
┌────────────────────────────────────┐
│  [Green on Black Terminal]         │
│                                    │
│   $ ping google.com                │
│   $ curl api.example.com           │
│   $ wget file.zip                  │
│                                    │
│   NETWORKING BASICS                │
│   Complete Guide 🚀                │
│                                    │
│   Chapter 24 | T3rmuxk1ng          │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  [Gradient Network Background]     │
│                                    │
│   📡 NETWORKING IN TERMUX          │
│                                    │
│   🔹 ping - Connectivity           │
│   🔹 curl - HTTP Requests          │
│   🔹 wget - Downloads              │
│   🔹 jq - JSON Parsing             │
│                                    │
│   30+ COMMANDS! | Chapter 24       │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🌐 Termux Full Course - Chapter 24: Networking Basics in Termux | Complete Guide

🔥 In this video you'll learn:
• Network fundamentals - IP, Ports, Protocols
• ping command for connectivity testing
• curl for HTTP requests and API testing
• wget for file downloading
• ifconfig and ip commands
• netstat and ss commands
• DNS lookup with nslookup and dig
• traceroute for path tracing
• HTTP methods and API requests
• JSON parsing with jq
• 30+ networking commands

⏱️ Timestamps:
0:00 - Introduction
1:00 - Network Fundamentals
5:00 - ping Command
8:00 - curl Command
12:00 - wget Command
15:00 - ifconfig vs ip Command
17:00 - netstat and ss Commands
19:00 - DNS Lookup Tools
21:00 - traceroute
22:30 - HTTP Methods and APIs
25:00 - 30+ Commands Summary
27:00 - Summary & Next Chapter

📥 Required Packages:
pkg install curl wget net-tools dnsutils traceroute jq iputils

📝 Commands from this video:
# All commands available in the chapter guide!

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #Networking #TermuxCourse #T3rmuxk1ng #curl #wget #NetworkCommands #HTTPRequests #API #JSON #LinuxOnAndroid #EthicalHacking

---
⚠️ Disclaimer: This video is for educational purposes only. Use networking tools responsibly and only on systems you have permission to test.
```

### Tags List

```
termux, termux networking, termux commands, termux course, 
termux full course, ping command, curl command, wget command,
ifconfig termux, ip command, netstat, ss command, dns lookup,
nslookup, dig command, traceroute, http requests, api testing,
json parsing jq, network basics, networking fundamentals,
termux hindi, termux tutorial hindi, linux networking,
android terminal, ethical hacking, t3rmuxk1ng, termux course hindi,
network commands, http methods, curl api, wget download,
termux ping, termux curl, termux network tools
```

### Hashtags

```
#Termux #TermuxNetworking #TermuxCourse #TermuxHindi #NetworkingBasics 
#CurlCommand #WgetCommand #PingCommand #HTTPRequest #APITesting 
#NetworkCommands #LinuxNetworking #TermuxTutorial #T3rmuxk1ng 
#LearnTermux #NetworkFundamentals #DNSLookup #Traceroute #JSONParsing
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| curl Documentation | https://curl.se/docs/ |
| wget Manual | https://www.gnu.org/software/wget/manual/ |
| jq Manual | https://stedolan.github.io/jq/manual/ |
| ip Command | man ip |
| DNS Tools | man dig |

### Practice APIs

| API | Description |
|------|-------------|
| JSONPlaceholder | https://jsonplaceholder.typicode.com |
| ReqRes | https://reqres.in |
| HTTPBin | https://httpbin.org |
| PokeAPI | https://pokeapi.co |
| Cat Facts | https://catfact.ninja |

### Network Tools Reference

| Tool | Package | Purpose |
|------|---------|---------|
| ping | iputils | Connectivity test |
| curl | curl | HTTP client |
| wget | wget | File downloader |
| dig | dnsutils | DNS lookup |
| nslookup | dnsutils | DNS lookup |
| traceroute | traceroute | Trace route |
| nc | netcat | Network utility |
| nmap | nmap | Network scanner |
| ss | iproute2 | Socket statistics |
| jq | jq | JSON processor |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 25, verify:

- [ ] Understand network fundamentals (IP, Ports, Protocols)
- [ ] ping command working and understood
- [ ] curl installed and tested HTTP requests
- [ ] wget installed and downloaded files
- [ ] ifconfig and ip commands understood
- [ ] netstat and ss commands tested
- [ ] DNS lookup with dig/nslookup working
- [ ] traceroute tested
- [ ] HTTP methods (GET, POST, PUT, DELETE) understood
- [ ] jq installed and JSON parsing working
- [ ] Completed all practice exercises

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 25: Nmap Installation & Basics**

- Nmap installation in Termux
- Basic scanning techniques
- Port scanning options
- Service version detection
- OS detection
- Nmap output formats
- Common scan types
- Script scanning basics

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
