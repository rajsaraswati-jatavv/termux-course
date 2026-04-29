# Chapter 28: HTTP Tools in Termux

> **Module:** 5 - Networking  
> **Chapter:** 28 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | HTTP tools: httpx, httping, httpie, curl |
| Advanced Topics | Headers, Cookies, Auth, JSON, Proxies |
| Commands Reference | 25+ HTTP commands |
| Practice Exercises | Hands-on API testing tasks |
| Troubleshooting | Common HTTP tool issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 28
Title: HTTP Tools in Termux | API Testing & Web Requests | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course!

Main hoon aapka host T3rmuxk1ng aur aaj ka chapter bahut important hai 
- especially agar aap ethical hacking, API development, ya web security 
mein interest rakhte ho.

Aaj hum baat karenge HTTP Tools ki - ye wo tools hain jo web ke saath 
communicate karte hain. Har website, har API, har online service - 
sab HTTP protocol use karti hai.

Agar aapko APIs test karni hai, web servers scan karne hain, ya 
penetration testing karni hai - to HTTP tools aapka primary weapon hai.

Is chapter mein hum seekhenge:
- httpx - modern HTTP toolkit
- httpie - user-friendly HTTP client
- httping - HTTP latency testing
- Advanced curl techniques
- Headers manipulation
- Authentication methods
- JSON handling
- Proxy configuration
- Aur much more!

To chaliye shuru karte hain!

---

[SECTION 1: HTTP PROTOCOL BASICS - 0:45 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle, HTTP kya hai - ye samajhna zaruri hai.

HTTP matlab Hypertext Transfer Protocol. Ye internet ki language hai.
Jab aap browser mein koi website open karte ho - browser HTTP request 
bhejta hai server ko, server HTTP response bhejta hai.

HTTP Request mein hota hai:
- Method (GET, POST, PUT, DELETE, etc.)
- Headers (metadata about request)
- Body (data for POST/PUT requests)
- URL (target address)

HTTP Response mein hota hai:
- Status Code (200 OK, 404 Not Found, 500 Error)
- Headers (server information)
- Body (actual content - HTML, JSON, etc.)

Common HTTP Methods:
┌─────────────────────────────────────────────────────────────────────────┐
│                    HTTP METHODS QUICK REFERENCE                          │
├─────────────┬───────────────────────────────────────────────────────────┤
│ Method      │ Purpose                                                   │
├─────────────┼───────────────────────────────────────────────────────────┤
│ GET         │ Data retrieve karna - sirf read                           │
│ POST        │ Naya data create karna - form submit, upload             │
│ PUT         │ Existing data update karna - full replace                │
│ PATCH       │ Partial update karna                                      │
│ DELETE      │ Data remove karna                                         │
│ HEAD        │ Sirf headers dekhna - body nahi                          │
│ OPTIONS     │ Allowed methods check karna                               │
└─────────────┴───────────────────────────────────────────────────────────┘

HTTP Status Codes:
- 1xx: Informational
- 2xx: Success (200 OK, 201 Created)
- 3xx: Redirect (301 Moved, 302 Found)
- 4xx: Client Error (400 Bad Request, 401 Unauthorized, 404 Not Found)
- 5xx: Server Error (500 Internal Error, 503 Service Unavailable)

Ye basics samajh liye? Chaliye ab tools install karte hain.

---

[SECTION 2: INSTALLING HTTP TOOLS - 3:00 to 5:30]
─────────────────────────────────────────────────────────────────────────────

Termux mein HTTP tools install karna easy hai. Ek ek karke install karte hain:

[STEP 1: Install curl]
curl sabse basic aur powerful tool hai:

    pkg install curl -y

curl almost har Linux system mein hota hai - Termux mein bhi available hai.

[STEP 2: Install wget]
wget download ke liye use hota hai:

    pkg install wget -y

[STEP 3: Install httpie]
httpie ek modern, user-friendly alternative hai:

    pkg install httpie -y

Isse `http` command mil jayegi - bahut easy syntax hai.

[STEP 4: Install httping]
httping HTTP latency test ke liye:

    pkg install httping -y

[STEP 5: Install httpx (Go required)]
httpx modern reconnaissance tool hai - installation thoda different hai:

    pkg install golang -y
    go install github.com/projectdiscovery/httpx/cmd/httpx@latest

Binary ~/go/bin/ mein install hoga. Path add karein:

    export PATH=$PATH:~/go/bin

[STEP 6: Install jq (JSON processor)]
JSON data ko beautifully display karne ke liye:

    pkg install jq -y

Verification karein:

    curl --version
    http --version
    httping -v
    httpx -version

Sab kuch install ho gaya? Chaliye ab use karna seekhte hain!

---

[SECTION 3: CURL BASICS & ADVANCED - 5:30 to 9:00]
─────────────────────────────────────────────────────────────────────────────

curl Command Line URL - iska matlab hai URL se data fetch karna.

BASIC USAGE:

    curl https://example.com

Ye simple GET request hai. Website ka HTML output mein aayega.

OUTPUT SAVE KARNA:

    curl https://example.com -o webpage.html
    curl https://example.com -O  # Same filename as remote

HEADERS DEKHNA:

    curl -I https://example.com

Ye sirf headers dikhayega - body nahi. Useful hai server info ke liye.

VERBOSE MODE:

    curl -v https://example.com

-v flag se complete request/response dikhayi deta hai - headers, body, 
sab kuch. Debugging ke liye bahut useful.

FOLLOW REDIRECTS:

    curl -L https://example.com

-L flag se redirects follow hote hain. Agar server 301/302 bhejta hai 
to curl automatically new location pe jayega.

CUSTOM HEADERS:

    curl -H "User-Agent: MyCustomAgent/1.0" https://example.com
    curl -H "Authorization: Bearer token123" https://api.example.com

Multiple headers:

    curl -H "Content-Type: application/json" \
         -H "Authorization: Bearer token123" \
         https://api.example.com

POST REQUEST:

    curl -X POST https://example.com/api

POST WITH DATA:

    curl -X POST -d "name=John&age=25" https://example.com/api

POST JSON DATA:

    curl -X POST \
         -H "Content-Type: application/json" \
         -d '{"name":"John","age":25}' \
         https://api.example.com/users

FILE UPLOAD:

    curl -X POST -F "file=@photo.jpg" https://example.com/upload
    curl -X POST -F "image=@photo.png" -F "name=My Photo" https://api.example.com/upload

COOKIES:

    # Send cookie
    curl -b "session=abc123" https://example.com

    # Save cookies from response
    curl -c cookies.txt https://example.com

    # Use saved cookies
    curl -b cookies.txt https://example.com/dashboard

AUTHENTICATION:

    # Basic Auth
    curl -u username:password https://api.example.com

    # Bearer Token
    curl -H "Authorization: Bearer YOUR_TOKEN" https://api.example.com

    # API Key
    curl -H "X-API-Key: YOUR_API_KEY" https://api.example.com

PROXY:

    curl -x http://proxy.server:8080 https://example.com
    curl -x socks5://127.0.0.1:9050 https://example.com

SSL OPTIONS:

    # Ignore SSL certificate errors (for testing only!)
    curl -k https://self-signed.example.com

    # Specify custom certificate
    curl --cacert /path/to/cert.pem https://example.com

TIMEOUT:

    curl --connect-timeout 10 https://example.com
    curl --max-time 30 https://example.com

YE SAB CURL COMMANDS YAAD RAKHEIN - bahut useful hain!

---

[SECTION 4: HTTPIE - USER FRIENDLY HTTP CLIENT - 9:00 to 11:30]
─────────────────────────────────────────────────────────────────────────────

httpie ek modern alternative hai curl ka - syntax bahut simple hai.

Command name hai `http` - simple!

BASIC GET REQUEST:

    http https://example.com

Ye automatically:
- Colorized output deta hai
- JSON ko pretty print karta hai
- Headers clearly dikhata hai

PRETTY OUTPUT:

    http --print=h https://example.com  # Headers only
    http --print=b https://example.com  # Body only
    http --print=HhBb https://example.com  # Request & Response headers and body

POST REQUEST:

    http POST https://example.com/api name=John age:=25

Note the := syntax for non-string values (numbers, booleans).

POST JSON:

    http POST https://example.com/api name=John age:=25 active:=true

Automatically JSON format mein bhejta hai!

CUSTOM HEADERS:

    http https://example.com User-Agent:MyAgent/1.0
    http https://example.com Authorization:"Bearer token123"

AUTHENTICATION:

    # Basic Auth (automatic)
    http -a username:password https://example.com

    # Digest Auth
    http --auth-type=digest -a user:pass https://example.com

DOWNLOAD FILE:

    http --download https://example.com/file.zip

UPLOAD FILE:

    http POST https://example.com/upload file@/path/to/file.txt

SESSIONS:

    # Create session
    http --session=/tmp/session.json https://example.com/login user=test pass=123

    # Use session
    http --session=/tmp/session.json https://example.com/dashboard

OFFLINE MODE (dry run):

    http --offline POST https://example.com/api name=test

Ye request print karega lekin bhejega nahi - testing ke liye useful!

---

[SECTION 5: HTTPING - HTTP LATENCY TESTING - 11:30 to 13:00]
─────────────────────────────────────────────────────────────────────────────

httping ping jaisa hai lekin HTTP layer pe kaam karta hai. Web server 
ki latency check karne ke liye perfect hai.

BASIC USAGE:

    httping https://example.com

Ye repeated HTTP requests bhejta hai aur latency report karta hai.

SPECIFY COUNT:

    httping -c 5 https://example.com

INTERVAL SET:

    httping -i 2 https://example.com  # 2 second interval

USE POST METHOD:

    httping -X POST https://example.com/api

SHOW RESPONSE CODES:

    httping -s https://example.com

TIMEOUT:

    httping -t 5 https://example.com  # 5 second timeout

DNS RESOLUTION TIME:

    httping -D https://example.com

COMPLETE OUTPUT:

    httping -v https://example.com

Output aisa dikhta hai:

PING example.com:80 (https://example.com):
connected to 93.184.216.34:80 (443 bytes), seq=0 time= 45.23 ms
connected to 93.184.216.34:80 (443 bytes), seq=1 time= 42.87 ms
connected to 93.184.216.34:80 (443 bytes), seq=2 time= 43.12 ms
--- https://example.com httping statistics ---
3 requests transmitted, 3 replies received, 0% loss
round-trip min/avg/max = 42.87/43.74/45.23 ms

Ye tool server health monitoring ke liye bahut useful hai!

---

[SECTION 6: HTTPX - MODERN HTTP TOOLKIT - 13:00 to 15:00]
─────────────────────────────────────────────────────────────────────────────

httpx ProjectDiscovery ka tool hai - professional security researchers 
ke liye designed hai. Fast, multi-purpose, aur powerful hai.

BASIC USAGE:

    httpx -u https://example.com

MULTIPLE URLS:

    httpx -u https://example.com,https://test.com

URLS FROM FILE:

    httpx -l urls.txt

TECHNOLOGY DETECTION:

    httpx -u https://example.com -tech-detect

Ye website pe kya technology chal rahi hai batata hai - WordPress, 
Nginx, React, etc.

STATUS CODE FILTER:

    httpx -l urls.txt -mc 200,301,302

-mc = match code - sirf specific status codes dikhao

CONTENT LENGTH:

    httpx -u https://example.com -content-length

FOLLOW REDIRECTS:

    httpx -u https://example.com -follow-redirects

SCREENSHOT:

    httpx -u https://example.com -screenshot

WEBHOOK TESTING:

    httpx -u https://webhook.site/YOUR_ID -X POST -d '{"test":"data"}'

JSON OUTPUT:

    httpx -u https://example.com -json -o results.json

VERBOSE:

    httpx -u https://example.com -v

PROBE ALL PORTS:

    httpx -u example.com -ports 80,443,8080,8443

TITLE EXTRACTION:

    httpx -u https://example.com -title

COMPLETE SCAN:

    httpx -u https://example.com -title -tech-detect -status-code -content-length -web-server

httpx penetration testing ke liye bahut powerful hai!

---

[SECTION 7: JSON HANDLING WITH JQ - 15:00 to 16:30]
─────────────────────────────────────────────────────────────────────────────

API responses mostly JSON format mein aate hain. jq isse handle karne 
ke liye perfect tool hai.

BASIC JSON PARSING:

    curl -s https://jsonplaceholder.typicode.com/users/1 | jq

PRETTY PRINT:

    curl -s https://api.example.com/data.json | jq '.'

EXTRACT SPECIFIC FIELD:

    curl -s https://jsonplaceholder.typicode.com/users/1 | jq '.name'
    curl -s https://jsonplaceholder.typicode.com/users/1 | jq '.address.city'

EXTRACT MULTIPLE FIELDS:

    curl -s https://jsonplaceholder.typicode.com/users/1 | jq '.name, .email'

ARRAY HANDLING:

    curl -s https://jsonplaceholder.typicode.com/users | jq '.[0]'
    curl -s https://jsonplaceholder.typicode.com/users | jq '.[0:3]'
    curl -s https://jsonplaceholder.typicode.com/users | jq '.[] | .name'

FILTER DATA:

    curl -s https://jsonplaceholder.typicode.com/users | jq '.[] | select(.id > 5)'
    curl -s https://jsonplaceholder.typicode.com/users | jq '.[] | select(.address.city == "London")'

CREATE JSON:

    jq -n '{name: "John", age: 25}'

MODIFY JSON:

    echo '{"name":"John"}' | jq '.age = 25'

KEYS LIST:

    curl -s https://jsonplaceholder.typicode.com/users/1 | jq 'keys'

JSON TO CSV:

    curl -s https://jsonplaceholder.typicode.com/users | jq -r '.[] | [.id, .name, .email] | @csv'

---

[SECTION 8: PRACTICAL API TESTING - 16:30 to 18:30]
─────────────────────────────────────────────────────────────────────────────

Ab practical API testing karte hain. Free API use karenge: 
https://jsonplaceholder.typicode.com/

[DEMO 1: GET Request]

    curl -s https://jsonplaceholder.typicode.com/posts | jq '.[0:3]'

[DEMO 2: POST Request]

    curl -X POST \
         -H "Content-Type: application/json" \
         -d '{"title":"My Post","body":"Content here","userId":1}' \
         https://jsonplaceholder.typicode.com/posts | jq

[DEMO 3: PUT Request]

    curl -X PUT \
         -H "Content-Type: application/json" \
         -d '{"id":1,"title":"Updated Title","body":"Updated body","userId":1}' \
         https://jsonplaceholder.typicode.com/posts/1 | jq

[DEMO 4: DELETE Request]

    curl -X DELETE https://jsonplaceholder.typicode.com/posts/1

[DEMO 5: With httpie]

    http https://jsonplaceholder.typicode.com/posts
    http POST https://jsonplaceholder.typicode.com/posts title="Test" body="Test body" userId:=1

[DEMO 6: Complete API Testing Script]

    #!/bin/bash
    API="https://jsonplaceholder.typicode.com"
    
    echo "=== GET Posts ==="
    curl -s "$API/posts?_limit=3" | jq
    
    echo "=== GET Single Post ==="
    curl -s "$API/posts/1" | jq
    
    echo "=== Create Post ==="
    curl -s -X POST "$API/posts" \
         -H "Content-Type: application/json" \
         -d '{"title":"Test","body":"Test","userId":1}' | jq

---

[SECTION 9: SUMMARY & BEST PRACTICES - 18:30 to 20:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 28 complete! Chaliye summarize karte hain:

✅ HTTP Protocol basics samjhe
✅ curl - powerful and versatile HTTP client
✅ httpie - user-friendly alternative
✅ httping - latency testing
✅ httpx - modern reconnaissance tool
✅ jq - JSON processing
✅ API testing techniques
✅ Authentication methods
✅ Proxy configuration
✅ Headers manipulation

BEST PRACTICES yaad rakhein:

1. Always use -s (silent) with curl in scripts
2. Use jq for JSON parsing - readable output
3. Test APIs with httpie first, then automate with curl
4. httpx for reconnaissance and bulk testing
5. Never ignore SSL warnings in production
6. Use environment variables for sensitive data

┌─────────────────────────────────────────────────────────────────────────┐
│                    HTTP TOOLS QUICK REFERENCE                            │
├──────────────────┬──────────────────────────────────────────────────────┤
│ Tool             │ Best Use Case                                        │
├──────────────────┼──────────────────────────────────────────────────────┤
│ curl             │ General purpose, scripting, automation               │
│ httpie           │ Interactive use, API testing, readability            │
│ httping          │ Server health monitoring, latency testing           │
│ httpx            │ Security testing, reconnaissance, bulk operations   │
│ jq               │ JSON processing and parsing                         │
│ wget             │ File downloads, mirroring                           │
└──────────────────┴──────────────────────────────────────────────────────┘

Important Commands yaad rakhein:

curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' URL
http POST URL key=value
httping -c 5 URL
httpx -u URL -tech-detect -title
cat data.json | jq '.field'

Next Chapter 29 mein hum DNS aur Domain Tools seekhenge:
- DNS enumeration
- WHOIS lookup
- Subdomain discovery
- And more!

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 29!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. HTTP Protocol Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         HTTP REQUEST STRUCTURE                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │ REQUEST LINE                                                     │   │
│   │ GET /api/users HTTP/1.1                                          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │ REQUEST HEADERS                                                  │   │
│   │ Host: example.com                                                │   │
│   │ User-Agent: curl/7.68.0                                          │   │
│   │ Accept: application/json                                         │   │
│   │ Authorization: Bearer token123                                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │ REQUEST BODY (for POST/PUT/PATCH)                               │   │
│   │ {"name": "John", "email": "john@example.com"}                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│                        HTTP RESPONSE STRUCTURE                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │ STATUS LINE                                                      │   │
│   │ HTTP/1.1 200 OK                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │ RESPONSE HEADERS                                                 │   │
│   │ Content-Type: application/json                                   │   │
│   │ Content-Length: 234                                              │   │
│   │ Server: nginx/1.18.0                                             │   │
│   │ Date: Mon, 01 Jan 2024 12:00:00 GMT                             │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │ RESPONSE BODY                                                    │   │
│   │ {"id": 1, "name": "John", "email": "john@example.com"}          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. HTTP Status Codes Reference

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      HTTP STATUS CODES REFERENCE                         │
├──────────┬──────────────────┬────────────────────────────────────────────┤
│ Code     │ Status           │ Description                                │
├──────────┼──────────────────┼────────────────────────────────────────────┤
│ 1xx      │ Informational    │ Request received, continuing process       │
│ 100      │ Continue         │ Server received request headers            │
│ 101      │ Switching        │ Protocol switching                         │
├──────────┼──────────────────┼────────────────────────────────────────────┤
│ 2xx      │ Success          │ Request successfully received              │
│ 200      │ OK               │ Standard success response                  │
│ 201      │ Created          │ Resource successfully created              │
│ 204      │ No Content       │ Success but no response body               │
├──────────┼──────────────────┼────────────────────────────────────────────┤
│ 3xx      │ Redirection      │ Further action needed                     │
│ 301      │ Moved Permanently│ Resource moved to new URL                  │
│ 302      │ Found            │ Resource temporarily at different URL      │
│ 304      │ Not Modified     │ Resource not modified (cached)            │
├──────────┼──────────────────┼────────────────────────────────────────────┤
│ 4xx      │ Client Error     │ Request contains bad syntax                │
│ 400      │ Bad Request      │ Server cannot understand request           │
│ 401      │ Unauthorized     │ Authentication required                    │
│ 403      │ Forbidden        │ Access denied                              │
│ 404      │ Not Found        │ Resource does not exist                    │
│ 405      │ Method Not Allowed│ HTTP method not supported                │
│ 429      │ Too Many Requests│ Rate limit exceeded                        │
├──────────┼──────────────────┼────────────────────────────────────────────┤
│ 5xx      │ Server Error     │ Server failed to fulfill request           │
│ 500      │ Internal Error   │ Unexpected server error                    │
│ 502      │ Bad Gateway      │ Invalid response from upstream             │
│ 503      │ Unavailable      │ Server temporarily unavailable            │
│ 504      │ Gateway Timeout  │ Upstream server timeout                    │
└──────────┴──────────────────┴────────────────────────────────────────────┘
```

### 3. Tool Comparison Matrix

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      HTTP TOOLS COMPARISON                               │
├──────────────────┬────────┬────────┬────────┬────────┬──────────────────┤
│ Feature          │ curl   │ wget   │ httpie │ httpx  │ httping          │
├──────────────────┼────────┼────────┼────────┼────────┼──────────────────┤
│ GET Requests     │   ✅   │   ✅   │   ✅   │   ✅   │       ✅         │
│ POST Requests    │   ✅   │   ❌   │   ✅   │   ✅   │       ❌         │
│ Custom Headers   │   ✅   │   ✅   │   ✅   │   ✅   │       ✅         │
│ JSON Support     │   ✅   │   ❌   │   ✅✅  │   ✅   │       ❌         │
│ Authentication   │   ✅   │   ✅   │   ✅   │   ✅   │       ✅         │
│ Proxy Support    │   ✅   │   ✅   │   ✅   │   ✅   │       ✅         │
│ SSL/TLS Options  │   ✅   │   ✅   │   ✅   │   ✅   │       ✅         │
│ File Upload      │   ✅   │   ❌   │   ✅   │   ❌   │       ❌         │
│ File Download    │   ✅   │   ✅✅  │   ✅   │   ❌   │       ❌         │
│ Colorized Output │   ❌   │   ❌   │   ✅   │   ✅   │       ❌         │
│ Bulk Testing     │   ❌   │   ❌   │   ❌   │   ✅✅  │       ❌         │
│ Latency Testing  │   ❌   │   ❌   │   ❌   │   ❌   │       ✅✅        │
│ Scripting        │   ✅✅  │   ✅   │   ✅   │   ✅   │       ✅         │
│ Learning Curve   │ Medium │ Easy   │  Easy  │ Medium │      Easy        │
└──────────────────┴────────┴────────┴────────┴────────┴──────────────────┘
```

### 4. Installation Commands

```bash
# Update Termux first
pkg update && pkg upgrade -y

# Install curl (usually pre-installed)
pkg install curl -y

# Install wget
pkg install wget -y

# Install httpie
pkg install httpie -y

# Install httping
pkg install httping -y

# Install jq (JSON processor)
pkg install jq -y

# Install httpx (requires Go)
pkg install golang -y
go install github.com/projectdiscovery/httpx/cmd/httpx@latest

# Add Go bin to PATH
echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.bashrc
source ~/.bashrc

# Verify installations
curl --version
wget --version
http --version
httping -V
jq --version
httpx -version
```

---

## 🔧 CURL ADVANCED GUIDE

### Basic Operations

```bash
# Simple GET request
curl https://example.com

# Save output to file
curl https://example.com -o output.html

# Save with original filename
curl https://example.com/file.zip -O

# Show headers only
curl -I https://example.com

# Show both request and response headers
curl -v https://example.com

# Silent mode (no progress bar)
curl -s https://example.com

# Follow redirects
curl -L https://example.com

# Combine options
curl -sL https://example.com
```

### HTTP Methods

```bash
# GET request (default)
curl -X GET https://example.com/api

# POST request
curl -X POST https://example.com/api

# PUT request
curl -X PUT https://example.com/api/1

# PATCH request
curl -X PATCH https://example.com/api/1

# DELETE request
curl -X DELETE https://example.com/api/1

# HEAD request
curl -I https://example.com

# OPTIONS request
curl -X OPTIONS https://example.com -i
```

### Headers Manipulation

```bash
# Single custom header
curl -H "User-Agent: MyBot/1.0" https://example.com

# Multiple headers
curl -H "User-Agent: MyBot/1.0" \
     -H "Accept: application/json" \
     -H "X-Custom-Header: value" \
     https://example.com

# Content-Type headers
curl -H "Content-Type: application/json" https://example.com
curl -H "Content-Type: application/x-www-form-urlencoded" https://example.com

# Authorization headers
curl -H "Authorization: Bearer YOUR_TOKEN" https://api.example.com
curl -H "Authorization: Basic BASE64_ENCODED_CREDENTIALS" https://api.example.com

# Remove default header
curl -H "User-Agent:" https://example.com

# Add header from file
curl -H @headers.txt https://example.com
```

### POST Requests with Data

```bash
# POST with form data
curl -X POST -d "name=John&email=john@example.com" https://example.com/api

# POST with URL-encoded data
curl -X POST \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "name=John&age=25" \
     https://example.com/api

# POST JSON data
curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"name":"John","age":25}' \
     https://example.com/api

# POST JSON from file
curl -X POST \
     -H "Content-Type: application/json" \
     -d @data.json \
     https://example.com/api

# POST with multipart/form-data (file upload)
curl -X POST \
     -F "file=@/path/to/file.txt" \
     https://example.com/upload

# Multiple files upload
curl -X POST \
     -F "file1=@file1.txt" \
     -F "file2=@file2.txt" \
     https://example.com/upload

# File upload with additional fields
curl -X POST \
     -F "profile=@photo.jpg" \
     -F "name=John" \
     -F "description=My photo" \
     https://example.com/upload
```

### Cookies Handling

```bash
# Send cookie with request
curl -b "session=abc123" https://example.com

# Send multiple cookies
curl -b "session=abc123; user=john" https://example.com

# Save cookies from response
curl -c cookies.txt https://example.com/login

# Use saved cookies
curl -b cookies.txt https://example.com/dashboard

# Save and use cookies together
curl -c cookies.txt -b cookies.txt https://example.com

# Cookie file format
cat cookies.txt
# .example.com  TRUE    /   FALSE   0   session abc123

# Delete cookie (set empty value)
curl -b "session=" https://example.com
```

### Authentication Methods

```bash
# Basic Authentication
curl -u username:password https://api.example.com
curl -u username: https://api.example.com  # Prompts for password

# Basic Auth with base64
curl -H "Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=" https://api.example.com

# Bearer Token
curl -H "Authorization: Bearer YOUR_ACCESS_TOKEN" https://api.example.com

# API Key in header
curl -H "X-API-Key: YOUR_API_KEY" https://api.example.com

# API Key in URL
curl "https://api.example.com?api_key=YOUR_API_KEY"

# OAuth 1.0 (complex - use specialized tools)
# Usually requires signing the request

# OAuth 2.0 Client Credentials
curl -X POST \
     -d "grant_type=client_credentials" \
     -d "client_id=YOUR_CLIENT_ID" \
     -d "client_secret=YOUR_CLIENT_SECRET" \
     https://auth.example.com/oauth/token

# JWT Token
curl -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIs..." https://api.example.com

# AWS Signature (use aws cli or specialized tools)
# NTLM Authentication
curl --ntlm -u user:pass https://example.com

# Digest Authentication
curl --digest -u user:pass https://example.com
```

### Proxy Configuration

```bash
# HTTP Proxy
curl -x http://proxy.example.com:8080 https://example.com

# HTTPS Proxy
curl -x https://proxy.example.com:443 https://example.com

# SOCKS4 Proxy
curl -x socks4://127.0.0.1:1080 https://example.com

# SOCKS5 Proxy
curl -x socks5://127.0.0.1:1080 https://example.com

# Proxy with authentication
curl -x http://user:pass@proxy.example.com:8080 https://example.com

# Use environment variable
export http_proxy=http://proxy.example.com:8080
curl https://example.com

# Ignore proxy for certain hosts
export no_proxy=localhost,127.0.0.1,.example.com

# Tor proxy
curl -x socks5://127.0.0.1:9050 https://check.torproject.org
```

### SSL/TLS Options

```bash
# Ignore SSL certificate errors (NOT for production!)
curl -k https://self-signed.example.com

# Specify CA certificate
curl --cacert /path/to/ca-cert.pem https://example.com

# Client certificate authentication
curl --cert /path/to/client.pem --key /path/to/key.pem https://example.com

# Specify certificate and key in one file
curl -E /path/to/cert.pem https://example.com

# Show SSL certificate info
curl -v https://example.com 2>&1 | grep -A 10 "SSL certificate"

# Force specific SSL version
curl --tlsv1.2 https://example.com
curl --sslv3 https://example.com  # If server requires SSLv3

# List supported ciphers
curl --ciphers 'HIGH:!aNULL:!MD5' https://example.com
```

### Timeout and Rate Limiting

```bash
# Connection timeout (seconds)
curl --connect-timeout 10 https://example.com

# Maximum time for whole operation (seconds)
curl --max-time 30 https://example.com

# Limit download speed
curl --limit-rate 100K https://example.com/file.zip

# Retry on failure
curl --retry 3 https://example.com

# Retry with delay
curl --retry 3 --retry-delay 5 https://example.com

# Speed threshold (abort if too slow)
curl --speed-time 10 --speed-limit 1000 https://example.com

# Limit bandwidth
curl --limit-rate 1M https://example.com/large-file.zip
```

---

## 🔧 HTTPIE GUIDE

### Basic Usage

```bash
# GET request
http https://example.com

# GET with pretty print
http --print=hHbB https://example.com

# Specific output parts
http --print=h https://example.com  # Response headers
http --print=b https://example.com  # Response body
http --print=H https://example.com  # Request headers
http --print=B https://example.com  # Request body

# Quiet mode (only body)
http --print=b https://example.com

# Verbose mode
http --verbose https://example.com
```

### HTTP Methods

```bash
# GET (default)
http GET https://example.com/api
http https://example.com/api

# POST
http POST https://example.com/api name=John age:=25

# PUT
http PUT https://example.com/api/1 name=Updated

# PATCH
http PATCH https://example.com/api/1 name=Updated

# DELETE
http DELETE https://example.com/api/1

# HEAD
http HEAD https://example.com
```

### Request Data

```bash
# Form data (default for POST)
http --form POST https://example.com/api name=John email=john@example.com

# JSON data (default)
http POST https://example.com/api name=John email=john@example.com

# Different data types
http POST https://example.com/api \
    name=John \          # String
    age:=25 \            # Integer
    height:=5.9 \        # Float
    active:=true \       # Boolean
    tags:='["a","b"]' \  # Array
    nested:='{"x":1}'    # Object

# Raw JSON input
echo '{"name":"John"}' | http POST https://example.com/api

# JSON from file
http POST https://example.com/api < data.json
```

### Headers and Authentication

```bash
# Custom headers
http https://example.com User-Agent:MyBot/1.0
http https://example.com X-Custom-Header:value

# Multiple headers
http https://example.com \
    User-Agent:MyBot/1.0 \
    Accept:application/json \
    X-API-Key:secret123

# Basic Auth
http -a username:password https://example.com

# Bearer Token
http https://example.com Authorization:"Bearer token123"

# Digest Auth
http --auth-type=digest -a user:pass https://example.com

# API Key
http https://example.com X-API-Key:your_key_here
```

### File Operations

```bash
# Download file
http --download https://example.com/file.zip

# Download with custom name
http --download -o myfile.zip https://example.com/file.zip

# Upload file
http POST https://example.com/upload file@/path/to/file.txt

# Upload with additional data
http POST https://example.com/upload \
    file@/path/to/photo.jpg \
    name="My Photo" \
    description="Profile picture"

# Multiple files
http POST https://example.com/upload \
    file1@file1.txt \
    file2@file2.txt
```

### Sessions

```bash
# Create named session
http --session=login -a user:pass https://example.com/login

# Use existing session
http --session=login https://example.com/dashboard

# Session stored in file
http --session=/tmp/session.json https://example.com

# Read-only session
http --session-read-only=login https://example.com

# List sessions
ls ~/.httpie/sessions/
```

### Advanced Features

```bash
# Offline mode (don't send request)
http --offline POST https://example.com/api name=test

# Follow redirects
http --follow https://example.com

# Max redirects
http --follow --max-redirects=5 https://example.com

# Verify SSL
http --verify=yes https://example.com
http --verify=no https://self-signed.example.com

# Timeout
http --timeout=30 https://example.com

# Proxy
http --proxy=http:http://proxy:8080 https://example.com

# Chunked transfer encoding
http --chunked POST https://example.com/api data@file.txt
```

---

## 🔧 HTTPX GUIDE

### Installation and Setup

```bash
# Install Go first
pkg install golang -y

# Install httpx
go install github.com/projectdiscovery/httpx/cmd/httpx@latest

# Add to PATH
export PATH=$PATH:$HOME/go/bin

# Verify
httpx -version
```

### Basic Usage

```bash
# Single URL
httpx -u https://example.com

# Multiple URLs
httpx -u https://example.com,https://test.com

# URLs from file
httpx -l urls.txt

# URLs from stdin
cat urls.txt | httpx

# Multiple threads
httpx -l urls.txt -threads 20
```

### Response Filtering

```bash
# Match status codes
httpx -l urls.txt -mc 200,201,301

# Filter status codes
httpx -l urls.txt -fc 404,500

# Match content length
httpx -l urls.txt -ml 1234

# Filter content length
httpx -l urls.txt -fl 0

# Match regex in response
httpx -l urls.txt -mr "password"

# Filter regex in response
httpx -l urls.txt -fr "Not Found"

# Match word count
httpx -l urls.txt -mw 100-500
```

### Information Gathering

```bash
# Extract title
httpx -u https://example.com -title

# Technology detection
httpx -u https://example.com -tech-detect

# Web server info
httpx -u https://example.com -web-server

# Content length
httpx -u https://example.com -content-length

# Status code
httpx -u https://example.com -status-code

# All information
httpx -u https://example.com -title -tech-detect -web-server -status-code -content-length

# Favicon hash
httpx -u https://example.com -favicon

# Host IP
httpx -u https://example.com -ip

# CDN detection
httpx -u https://example.com -cdn
```

### Advanced Scanning

```bash
# Follow redirects
httpx -u https://example.com -follow-redirects

# Max redirects
httpx -u https://example.com -follow-redirects -max-redirs 5

# Custom method
httpx -u https://example.com -x POST

# Custom headers
httpx -u https://example.com -H "User-Agent: CustomBot"

# Request body
httpx -u https://example.com -x POST -d '{"key":"value"}'

# Custom ports
httpx -u example.com -ports 80,443,8080,8443,3000

# All common ports
httpx -u example.com -ports 80-100,443,8080-8090

# Resolvers
httpx -u https://example.com -r resolvers.txt

# Timeout
httpx -u https://example.com -timeout 10

# Retry
httpx -u https://example.com -retry 3
```

### Output Options

```bash
# JSON output
httpx -u https://example.com -json

# CSV output
httpx -u https://example.com -csv

# Save to file
httpx -u https://example.com -o results.txt
httpx -u https://example.com -json -o results.json

# Silent mode
httpx -u https://example.com -silent

# Verbose
httpx -u https://example.com -verbose

# Debug mode
httpx -u https://example.com -debug
```

### Screenshot (requires headless browser)

```bash
# Take screenshot
httpx -u https://example.com -screenshot

# Screenshot with custom path
httpx -u https://example.com -screenshot -sd /path/to/dir
```

---

## 🔧 HTTPING GUIDE

### Basic Usage

```bash
# Basic HTTP ping
httping https://example.com

# Specify count
httping -c 10 https://example.com

# Interval between requests
httping -i 2 https://example.com

# Port specific
httping -p 8080 example.com
```

### HTTP Options

```bash
# POST method
httping -X POST https://example.com/api

# Custom URL path
httping -P /api/health https://example.com

# Send data
httping -d "test=data" https://example.com

# Custom headers
httping -H "Authorization: Bearer token" https://example.com

# User agent
httping -U "MyHealthChecker/1.0" https://example.com
```

### Performance Testing

```bash
# Show response codes
httping -s https://example.com

# DNS resolution time
httping -D https://example.com

# Connection time
httping -S https://example.com

# All timing details
httping -G https://example.com

# Timeout
httping -t 5 https://example.com

# Quiet mode
httping -q https://example.com
```

### SSL Options

```bash
# Use SSL/TLS
httping -l https://example.com

# Ignore SSL errors
httping -l --insecure https://example.com

# Specify SSL version
httping -l --tls1_2 https://example.com
```

---

## 🔧 JSON PROCESSING WITH JQ

### Basic Operations

```bash
# Pretty print JSON
curl -s https://api.example.com/data | jq

# Compact output
curl -s https://api.example.com/data | jq -c

# Raw output (no quotes)
curl -s https://api.example.com/data | jq -r

# Get specific field
curl -s https://api.example.com/user | jq '.name'
curl -s https://api.example.com/user | jq '.address.city'

# Nested field
curl -s https://api.example.com/data | jq '.user.profile.name'

# Get multiple fields
curl -s https://api.example.com/user | jq '.name, .email, .id'
```

### Array Operations

```bash
# First element
curl -s https://api.example.com/users | jq '.[0]'

# Last element
curl -s https://api.example.com/users | jq '.[-1]'

# Range of elements
curl -s https://api.example.com/users | jq '.[0:5]'
curl -s https://api.example.com/users | jq '.[2:]'

# All elements
curl -s https://api.example.com/users | jq '.[]'

# Extract field from all elements
curl -s https://api.example.com/users | jq '.[].name'

# Array length
curl -s https://api.example.com/users | jq 'length'
```

### Filtering and Selection

```bash
# Filter by condition
curl -s https://api.example.com/users | jq '.[] | select(.age > 25)'

# Multiple conditions
curl -s https://api.example.com/users | jq '.[] | select(.age > 25 and .active == true)'

# Filter by string match
curl -s https://api.example.com/users | jq '.[] | select(.name | contains("John"))'

# Filter by regex
curl -s https://api.example.com/users | jq '.[] | select(.email | test("@gmail\\.com$"))'

# Filter and extract
curl -s https://api.example.com/users | jq '.[] | select(.active == true) | .name'
```

### Transformations

```bash
# Create new object
curl -s https://api.example.com/user | jq '{name: .name, email: .email}'

# Rename fields
curl -s https://api.example.com/user | jq '{username: .name, contact: .email}'

# Add field
curl -s https://api.example.com/user | jq '. + {processed: true}'

# Remove field
curl -s https://api.example.com/user | jq 'del(.password)'

# Modify value
curl -s https://api.example.com/user | jq '.age = .age + 1'

# Map over array
curl -s https://api.example.com/users | jq 'map(.name)'

# Sort array
curl -s https://api.example.com/users | jq 'sort_by(.age)'

# Reverse sort
curl -s https://api.example.com/users | jq 'sort_by(.age) | reverse'

# Unique values
curl -s https://api.example.com/users | jq '[.[].city] | unique'
```

### Output Formats

```bash
# JSON to CSV
curl -s https://api.example.com/users | jq -r '.[] | [.id, .name, .email] | @csv'

# JSON to TSV
curl -s https://api.example.com/users | jq -r '.[] | [.id, .name, .email] | @tsv'

# JSON to HTML
curl -s https://api.example.com/users | jq -r '.[] | @html "<li>\(.name)</li>"'

# JSON to URL encoded
curl -s https://api.example.com/data | jq -r '@uri'

# JSON to base64
curl -s https://api.example.com/data | jq -r '@base64'

# JSON to YAML (requires python-yaml)
curl -s https://api.example.com/data | python -c "import yaml, json, sys; print(yaml.dump(json.load(sys.stdin)))"
```

---

## 🔧 WEB SCRAPING BASICS

### Using curl for Scraping

```bash
# Get page content
curl -sL https://example.com > page.html

# Extract links with grep
curl -sL https://example.com | grep -oP 'href="[^"]*"'

# Extract URLs
curl -sL https://example.com | grep -oP 'https?://[^"<>]+'

# Extract images
curl -sL https://example.com | grep -oP '<img[^>]+src="[^"]+"'

# Extract emails
curl -sL https://example.com | grep -oE '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}'
```

### Using Python for Scraping

```bash
# Install required packages
pkg install python -y
pip install beautifulsoup4 requests lxml

# Simple scraper
python << 'EOF'
import requests
from bs4 import BeautifulSoup

url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

# Extract all links
for link in soup.find_all('a'):
    print(link.get('href'))

# Extract all text from paragraphs
for p in soup.find_all('p'):
    print(p.text)
EOF
```

---

## 📋 COMMANDS REFERENCE

### curl Commands (25+ Commands)

```bash
# === BASIC OPERATIONS ===
curl https://example.com                     # GET request
curl -I https://example.com                  # Headers only
curl -L https://example.com                  # Follow redirects
curl -s https://example.com                  # Silent mode
curl -v https://example.com                  # Verbose output
curl -o file.html https://example.com        # Save to file
curl -O https://example.com/file.zip         # Save with original name

# === HTTP METHODS ===
curl -X POST https://example.com             # POST request
curl -X PUT https://example.com              # PUT request
curl -X DELETE https://example.com           # DELETE request
curl -X PATCH https://example.com            # PATCH request

# === DATA SUBMISSION ===
curl -d "key=value" https://example.com      # Form data
curl -d @file.txt https://example.com        # Data from file
curl -d '{"key":"value"}' -H "Content-Type: application/json" https://example.com  # JSON

# === HEADERS ===
curl -H "User-Agent: Custom" https://example.com        # Custom header
curl -H "Authorization: Bearer token" https://api.com   # Auth header
curl -H "Accept: application/json" https://example.com  # Accept header

# === AUTHENTICATION ===
curl -u user:pass https://example.com                    # Basic auth
curl -H "Authorization: Bearer token" https://api.com    # Bearer token
curl -H "X-API-Key: key123" https://api.com              # API key

# === COOKIES ===
curl -b "cookie=value" https://example.com     # Send cookie
curl -c cookies.txt https://example.com        # Save cookies
curl -b cookies.txt https://example.com        # Use saved cookies

# === PROXY ===
curl -x http://proxy:8080 https://example.com  # HTTP proxy
curl -x socks5://127.0.0.1:9050 https://example.com  # SOCKS5 proxy

# === SSL/TLS ===
curl -k https://example.com                    # Ignore SSL errors
curl --cacert cert.pem https://example.com     # Custom CA cert

# === TIMEOUT ===
curl --connect-timeout 10 https://example.com  # Connection timeout
curl --max-time 30 https://example.com         # Max time

# === UPLOAD ===
curl -F "file=@local.txt" https://example.com/upload   # File upload
curl -T file.txt https://example.com/upload/           # PUT upload
```

### httpie Commands

```bash
# === BASIC OPERATIONS ===
http https://example.com                      # GET request
http GET https://example.com                  # Explicit GET
http POST https://example.com                 # POST request
http PUT https://example.com name=value       # PUT request
http DELETE https://example.com/api/1         # DELETE request

# === DATA ===
http POST https://example.com name=John       # Form data
http POST https://example.com name:=25        # JSON integer
http POST https://example.com active:=true    # JSON boolean
http POST https://example.com < data.json     # JSON from file

# === HEADERS ===
http https://example.com User-Agent:Custom    # Custom header
http https://example.com X-API-Key:secret     # API key header

# === AUTH ===
http -a user:pass https://example.com         # Basic auth
http https://example.com Authorization:"Bearer token"  # Bearer

# === FILE OPERATIONS ===
http --download https://example.com/file.zip  # Download
http POST https://example.com file@local.txt  # Upload

# === OUTPUT ===
http --print=h https://example.com            # Headers only
http --print=b https://example.com            # Body only
http --verbose https://example.com            # Verbose

# === SESSIONS ===
http --session=mysession https://example.com  # Use session
```

### httpx Commands

```bash
# === BASIC ===
httpx -u https://example.com                  # Single URL
httpx -l urls.txt                             # From file
httpx -u https://example.com -threads 20      # Multi-threaded

# === INFORMATION GATHERING ===
httpx -u https://example.com -title           # Page title
httpx -u https://example.com -tech-detect     # Technology
httpx -u https://example.com -status-code     # Status code
httpx -u https://example.com -web-server      # Server info
httpx -u https://example.com -content-length  # Content length
httpx -u https://example.com -ip              # IP address
httpx -u https://example.com -cdn             # CDN detection

# === FILTERING ===
httpx -l urls.txt -mc 200,301                 # Match codes
httpx -l urls.txt -fc 404,500                 # Filter codes
httpx -l urls.txt -ml 100-500                 # Match length
httpx -l urls.txt -mr "login"                 # Match regex

# === SCANNING ===
httpx -u https://example.com -follow-redirects  # Follow redirects
httpx -u https://example.com -ports 80,443,8080  # Custom ports
httpx -u https://example.com -x POST -d "data"   # POST request
httpx -u https://example.com -H "Custom: val"    # Custom header

# === OUTPUT ===
httpx -u https://example.com -json            # JSON output
httpx -u https://example.com -o results.txt   # Save to file
httpx -u https://example.com -silent          # Silent mode
```

### httping Commands

```bash
# === BASIC ===
httping https://example.com                   # Basic ping
httping -c 10 https://example.com             # 10 requests
httping -i 2 https://example.com              # 2s interval

# === HTTP OPTIONS ===
httping -X POST https://example.com           # POST method
httping -P /api/health https://example.com    # Custom path
httping -H "X-Header: value" https://example.com  # Custom header

# === PERFORMANCE ===
httping -s https://example.com                # Show status codes
httping -D https://example.com                # DNS time
httping -G https://example.com                # All timing
httping -t 5 https://example.com              # Timeout

# === SSL ===
httping -l https://example.com                # Use SSL
httping -l --insecure https://example.com     # Ignore SSL errors
```

### jq Commands

```bash
# === BASIC ===
jq '.' file.json                              # Pretty print
jq -c '.' file.json                           # Compact
jq -r '.field' file.json                      # Raw output

# === ACCESSING FIELDS ===
jq '.name' data.json                          # Single field
jq '.user.name' data.json                     # Nested field
jq '.["field name"]' data.json               # Field with space
jq '.name, .email' data.json                 # Multiple fields

# === ARRAYS ===
jq '.[0]' data.json                           # First element
jq '.[-1]' data.json                          # Last element
jq '.[0:3]' data.json                         # Range
jq '.[]' data.json                            # All elements
jq '.[].name' data.json                       # Field from all

# === FILTERING ===
jq '.[] | select(.age > 25)' data.json        # Condition filter
jq '.[] | select(.name | contains("John"))'   # String filter
jq '[.[] | select(.active)]' data.json        # Boolean filter

# === TRANSFORMATION ===
jq '{name, email}' data.json                  # New object
jq 'map(.name)' data.json                     # Map over array
jq 'sort_by(.age)' data.json                  # Sort array
jq 'unique' data.json                         # Unique values

# === OUTPUT ===
jq -r '.[] | @csv' data.json                  # CSV output
jq -r '.[] | @tsv' data.json                  # TSV output
jq 'keys' data.json                           # Get all keys
jq 'length' data.json                         # Get length
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic HTTP Requests

```bash
# Task: Make various HTTP requests and analyze responses

# Step 1: Simple GET request
curl https://httpbin.org/get

# Step 2: Save response to file
curl -o response.txt https://httpbin.org/get

# Step 3: View headers
curl -I https://httpbin.org

# Step 4: Follow redirects
curl -L https://httpbin.org/redirect/3

# Step 5: Verbose output
curl -v https://httpbin.org/get
```

### Exercise 2: POST Requests

```bash
# Task: Send POST requests with different data types

# Step 1: POST form data
curl -X POST -d "name=John&age=25" https://httpbin.org/post

# Step 2: POST JSON data
curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"name":"John","skills":["Python","Bash"]}' \
     https://httpbin.org/post

# Step 3: POST with httpie
http POST https://httpbin.org/post name=John age:=25 skills:='["Python","Bash"]'

# Step 4: POST file
echo "Hello World" > test.txt
curl -X POST -F "file=@test.txt" https://httpbin.org/post
```

### Exercise 3: Authentication

```bash
# Task: Test different authentication methods

# Step 1: Basic Authentication
curl -u user:pass https://httpbin.org/basic-auth/user/pass

# Step 2: Bearer Token
curl -H "Authorization: Bearer mytoken123" https://httpbin.org/bearer

# Step 3: With httpie
http -a user:pass https://httpbin.org/basic-auth/user/pass

# Step 4: API Key in header
curl -H "X-API-Key: secret123" https://httpbin.org/headers
```

### Exercise 4: JSON Processing

```bash
# Task: Process JSON responses with jq

# Step 1: Get and pretty print
curl -s https://jsonplaceholder.typicode.com/users/1 | jq

# Step 2: Extract specific fields
curl -s https://jsonplaceholder.typicode.com/users/1 | jq '.name, .email'

# Step 3: Nested field extraction
curl -s https://jsonplaceholder.typicode.com/users/1 | jq '.address.city'

# Step 4: Process array
curl -s https://jsonplaceholder.typicode.com/users | jq '.[].name'

# Step 5: Filter data
curl -s https://jsonplaceholder.typicode.com/users | jq '.[] | select(.id <= 3)'

# Step 6: Create CSV output
curl -s https://jsonplaceholder.typicode.com/users | jq -r '.[] | [.id, .name, .email] | @csv'
```

### Exercise 5: API Testing Script

```bash
#!/bin/bash
# Task: Create a complete API testing script

API_URL="https://jsonplaceholder.typicode.com"

echo "=== API Testing Script ==="
echo ""

# GET all posts (limited)
echo "1. GET Posts (first 3):"
curl -s "$API_URL/posts?_limit=3" | jq '.[].title'
echo ""

# GET single post
echo "2. GET Single Post:"
curl -s "$API_URL/posts/1" | jq '{id, title, body}'
echo ""

# POST new post
echo "3. POST New Post:"
curl -s -X POST "$API_URL/posts" \
     -H "Content-Type: application/json" \
     -d '{"title":"Test Post","body":"Test Body","userId":1}' | jq
echo ""

# PUT update post
echo "4. PUT Update Post:"
curl -s -X PUT "$API_URL/posts/1" \
     -H "Content-Type: application/json" \
     -d '{"id":1,"title":"Updated Title","body":"Updated Body","userId":1}' | jq
echo ""

# DELETE post
echo "5. DELETE Post:"
curl -s -X DELETE "$API_URL/posts/1" -w "Status: %{http_code}\n"
echo ""

echo "=== Testing Complete ==="
```

### Exercise 6: Server Health Check

```bash
#!/bin/bash
# Task: Create a server health monitoring script

check_server() {
    local url=$1
    echo "Checking: $url"
    
    # Get status code
    status=$(curl -s -o /dev/null -w "%{http_code}" "$url")
    
    # Get response time
    time=$(curl -s -o /dev/null -w "%{time_total}" "$url")
    
    echo "  Status: $status"
    echo "  Time: ${time}s"
    
    if [ "$status" = "200" ]; then
        echo "  ✅ Server is healthy"
    else
        echo "  ❌ Server issue detected"
    fi
    echo ""
}

# Check multiple servers
check_server "https://google.com"
check_server "https://github.com"
check_server "https://example.com"
```

### Exercise 7: Batch URL Testing

```bash
#!/bin/bash
# Task: Test multiple URLs and save results

# Create URL list
cat > urls.txt << EOF
https://google.com
https://github.com
https://example.com
https://httpbin.org
EOF

# Test each URL
echo "URL,Status,Time" > results.csv

while read url; do
    status=$(curl -s -o /dev/null -w "%{http_code}" "$url")
    time=$(curl -s -o /dev/null -w "%{time_total}" "$url")
    echo "$url,$status,$time" >> results.csv
    echo "Tested: $url - $status (${time}s)"
done < urls.txt

echo ""
echo "Results saved to results.csv"
cat results.csv | column -t -s ','
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: Connection Refused

```bash
# Cause: Server not running or firewall blocking

# Solution 1: Check if server is up
ping example.com

# Solution 2: Try different port
curl http://example.com:8080

# Solution 3: Check firewall
# May need VPN or different network

# Solution 4: Check DNS resolution
nslookup example.com
```

### Problem 2: SSL Certificate Error

```bash
# Cause: Invalid or self-signed certificate

# Error: SSL certificate problem: unable to get local issuer certificate

# Solution 1: For testing only - skip verification
curl -k https://self-signed.example.com

# Solution 2: Add certificate to trusted store
curl --cacert /path/to/cert.pem https://example.com

# Solution 3: Update CA certificates
pkg install ca-certificates
```

### Problem 3: Timeout Errors

```bash
# Cause: Slow server or network issues

# Error: Connection timed out

# Solution 1: Increase timeout
curl --connect-timeout 30 --max-time 60 https://example.com

# Solution 2: Check internet connection
ping -c 3 google.com

# Solution 3: Use different DNS
curl --dns-servers 8.8.8.8 https://example.com

# Solution 4: Try with proxy
curl -x http://proxy:8080 https://example.com
```

### Problem 4: HTTP 403 Forbidden

```bash
# Cause: Access denied, authentication required, or blocked

# Solution 1: Add User-Agent header
curl -H "User-Agent: Mozilla/5.0" https://example.com

# Solution 2: Add authentication
curl -u user:pass https://example.com

# Solution 3: Check required headers
curl -H "Accept: application/json" https://api.example.com

# Solution 4: API key
curl -H "X-API-Key: your_key" https://api.example.com
```

### Problem 5: JSON Parsing Error with jq

```bash
# Cause: Invalid JSON or empty response

# Error: parse error: Invalid numeric literal

# Solution 1: Check if response is valid JSON
curl -s https://api.example.com | head

# Solution 2: Check for errors
curl -s -w "\nHTTP Status: %{http_code}\n" https://api.example.com

# Solution 3: Handle empty responses
curl -s https://api.example.com | jq 'if . == null then "Empty response" else . end'

# Solution 4: Use -R flag for raw input
curl -s https://api.example.com | jq -R .
```

### Problem 6: httpx Not Found

```bash
# Cause: Go binary not in PATH

# Solution 1: Add to current session
export PATH=$PATH:$HOME/go/bin

# Solution 2: Add to bashrc
echo 'export PATH=$PATH:$HOME/go/bin' >> ~/.bashrc
source ~/.bashrc

# Solution 3: Use full path
~/go/bin/httpx -u https://example.com

# Solution 4: Move to standard location
sudo mv ~/go/bin/httpx $PREFIX/bin/
```

### Problem 7: Rate Limiting (429 Error)

```bash
# Cause: Too many requests

# Solution 1: Add delay between requests
for url in $(cat urls.txt); do
    curl -s "$url"
    sleep 2
done

# Solution 2: Use curl rate limiting
curl --limit-rate 100K https://example.com

# Solution 3: Implement retry logic
curl --retry 3 --retry-delay 5 https://api.example.com

# Solution 4: Cache responses
if [ ! -f "cache.json" ]; then
    curl -s https://api.example.com > cache.json
fi
```

### Problem 8: Cookie Not Persisting

```bash
# Cause: Cookie file format or permissions

# Solution 1: Use both -b and -c together
curl -b cookies.txt -c cookies.txt https://example.com

# Solution 2: Check cookie file format
cat cookies.txt

# Solution 3: Create fresh cookie file
touch cookies.txt
curl -c cookies.txt -b cookies.txt https://example.com

# Solution 4: With httpie sessions
http --session=mysession https://example.com/login user=xxx pass=xxx
http --session=mysession https://example.com/dashboard
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🌐 HTTP TOOLS                    │
│   IN TERMUX                        │
│                                    │
│   ✓ curl ✓ httpie                  │
│   ✓ httpx ✓ httping                │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Code Style**
```
┌────────────────────────────────────┐
│  $ curl -X POST api.com            │
│  $ http POST url data=value        │
│  $ httpx -l urls.txt -mc 200       │
│                                    │
│  🔥 HTTP TOOLS MASTERCLASS         │
│                                    │
│  Chapter 28 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  ⚡ 25+ HTTP COMMANDS              │
│                                    │
│  📡 API TESTING                    │
│  🔐 AUTHENTICATION                 │
│  📊 JSON PROCESSING                │
│                                    │
│  HTTP TOOLS IN TERMUX              │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🌐 Termux Full Course - Chapter 28: HTTP Tools in Termux | API Testing & Web Requests

🔥 In this video you'll learn:
• HTTP Protocol basics samjhe
• curl advanced usage
• httpie - user-friendly HTTP client
• httpx - modern reconnaissance tool
• httping - latency testing
• JSON processing with jq
• Authentication methods
• Cookies and headers
• Proxy configuration
• Practical API testing

⏱️ Timestamps:
0:00 - Introduction
0:45 - HTTP Protocol Basics
3:00 - Installing HTTP Tools
5:30 - curl Basics & Advanced
9:00 - httpie Guide
11:30 - httping for Latency Testing
13:00 - httpx Modern Toolkit
15:00 - JSON Handling with jq
16:30 - Practical API Testing
18:30 - Summary

📥 Commands from this video:
pkg install curl wget httpie httping jq -y
go install github.com/projectdiscovery/httpx/cmd/httpx@latest
curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' URL
http POST URL key=value
httpx -u URL -tech-detect -title

🔗 Useful Links:
• httpbin.org - HTTP Testing Service
• jsonplaceholder.typicode.com - Fake API
• ProjectDiscovery - httpx

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #HTTPTools #API #curl #httpie #httpx #T3rmuxk1ng #TermuxHindi #WebRequests #JSON

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on systems you have permission to test.
```

### Tags List

```
termux, http tools, curl, httpie, httpx, httping, jq, api testing, 
http requests, termux networking, termux http, curl tutorial, 
json processing, termux api, web scraping, authentication, 
http headers, cookies handling, proxy configuration, ssl tls,
termux tutorial, termux hindi, termux course, t3rmuxk1ng,
ethical hacking, web security, penetration testing, security tools,
api testing tutorial, rest api, json parsing, termux commands
```

### Hashtags

```
#Termux #HTTPTools #curl #httpie #httpx #API #JSON #WebRequests 
#TermuxTutorial #TermuxHindi #Networking #CyberSecurity 
#EthicalHacking #T3rmuxk1ng #APITesting #REST
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| curl Documentation | https://curl.se/docs/ |
| httpie Documentation | https://httpie.io/docs |
| httpx Documentation | https://github.com/projectdiscovery/httpx |
| jq Manual | https://stedolan.github.io/jq/manual/ |

### Testing APIs

| Service | Purpose |
|---------|---------|
| httpbin.org | HTTP request testing |
| jsonplaceholder.typicode.com | Fake REST API |
| webhook.site | Webhook testing |
| reqres.in | API testing |

### Learning Resources

| Resource | Description |
|----------|-------------|
| curl cheat sheet | https://curl.se/docs/cheatsheet.html |
| HTTP Status Codes | https://httpstatuses.com/ |
| REST API Tutorial | https://restfulapi.net/ |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 29, verify:

- [ ] curl installed and tested
- [ ] httpie installed and tested
- [ ] httping installed and tested
- [ ] httpx installed and tested
- [ ] jq installed for JSON processing
- [ ] Made GET, POST, PUT, DELETE requests
- [ ] Tested authentication methods
- [ ] Used custom headers
- [ ] Handled cookies
- [ ] Configured proxy
- [ ] Processed JSON with jq
- [ ] Created API testing script

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 29: DNS & Domain Tools**

- DNS enumeration basics
- WHOIS lookups
- Subdomain discovery
- DNS record types
- DNS zone transfers
- dig command usage
- host command
- nslookup alternatives
- DNS security testing

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Use `curl -sL` combination in scripts - silent mode with redirect following. This is the most common pattern for automated HTTP requests.

> 💡 **Pro Tip #2:** Always add `-H "Content-Type: application/json"` when sending JSON data. Without this, most APIs will reject or misparse your request.

> 💡 **Pro Tip #3:** Use `curl -v` during development to see exact request/response details, then switch to `-s` for production scripts.

> 💡 **Pro Tip #4:** The `jq` tool is your best friend for APIs. Learn `.[]`, `select()`, and `map()` functions - they handle 90% of JSON processing needs.

> 💡 **Pro Tip #5:** For API testing, use `httpie` (http command) - it's more readable than curl and shows colorized output automatically.

> 💡 **Pro Tip #6:** Save and reuse cookies with `curl -c cookies.txt -b cookies.txt` - essential for authenticated session testing.

> 💡 **Pro Tip #7:** Use `--max-time` flag to prevent hanging: `curl --max-time 10 URL` - critical for scripts that need to fail gracefully.

> 💡 **Pro Tip #8:** `curl -w "@format.txt"` lets you create custom output formats with timing, response codes, etc. Great for performance testing.

> 💡 **Pro Tip #9:** For debugging APIs, `curl -v --trace-ascii debug.txt URL` saves complete request/response to a file for detailed analysis.

> 💡 **Pro Tip #10:** Use `httpx` for bulk HTTP reconnaissance - it can probe hundreds of hosts simultaneously with `httpx -l urls.txt -tech-detect`.

---

## 🔥 REAL WORLD APPLICATIONS

### Penetration Testing Scenarios

**Scenario 1: API Endpoint Discovery**
```bash
# Find hidden API endpoints
for endpoint in api v1 v2 admin users posts auth login register; do
  echo "Testing: /$endpoint/"
  curl -s -o /dev/null -w "%{http_code}" https://target.com/$endpoint/
  echo ""
done
```

**Scenario 2: Authentication Testing**
```bash
# Test for auth bypass
curl -s -H "Authorization: Bearer admin" https://target.com/api/admin
curl -s -H "X-Forwarded-For: 127.0.0.1" https://target.com/api/admin
curl -s -H "X-Original-URL: /admin" https://target.com/
```

**Scenario 3: Rate Limit Testing**
```bash
# Test rate limiting
for i in {1..100}; do
  curl -s -o /dev/null -w "Request $i: %{http_code}\n" https://api.target.com/endpoint
done
```

### Network Administration Use Cases

**Use Case 1: Health Check Script**
```bash
#!/bin/bash
# Website health check
URL="https://example.com"
RESPONSE=$(curl -s -o /dev/null -w "%{http_code}" --max-time 10 $URL)
if [ "$RESPONSE" = "200" ]; then
  echo "$(date): $URL is UP (HTTP $RESPONSE)"
else
  echo "$(date): $URL is DOWN (HTTP $RESPONSE)"
fi
```

**Use Case 2: API Response Time Monitor**
```bash
# Monitor API latency
while true; do
  TIME=$(curl -s -o /dev/null -w "%{time_total}" https://api.example.com/health)
  echo "$(date): Response time: ${TIME}s"
  sleep 60
done
```

**Use Case 3: Bulk URL Status Check**
```bash
# Check all URLs from file
while read url; do
  STATUS=$(curl -s -o /dev/null -w "%{http_code}" --max-time 5 "$url")
  echo "$url: HTTP $STATUS"
done < urls.txt
```

---

## ⚡ QUICK REFERENCE CARD

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    🌐 HTTP TOOLS QUICK REFERENCE CARD                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  CURL BASICS                                                                 │
│  ────────────────                                                            │
│  curl URL                       │ Simple GET request                        │
│  curl -I URL                    │ Headers only                              │
│  curl -L URL                    │ Follow redirects                          │
│  curl -s URL                    │ Silent mode                               │
│  curl -v URL                    │ Verbose output                            │
│  curl -o file URL               │ Save to file                              │
│                                                                              │
│  CURL HTTP METHODS                                                            │
│  ────────────────                                                            │
│  curl -X GET URL               │ GET request                                │
│  curl -X POST -d 'data' URL    │ POST with data                            │
│  curl -X PUT -d 'data' URL     │ PUT request                               │
│  curl -X DELETE URL            │ DELETE request                            │
│  curl -X PATCH -d 'data' URL   │ PATCH request                             │
│                                                                              │
│  CURL HEADERS & AUTH                                                          │
│  ────────────────                                                            │
│  curl -H "Header: value" URL   │ Custom header                              │
│  curl -H "Content-Type: json"  │ JSON content type                         │
│  curl -u user:pass URL         │ Basic authentication                      │
│  curl -H "Authorization: Bearer token" │ Bearer token                      │
│  curl -b "cookie=value" URL    │ Send cookie                               │
│  curl -c cookies.txt URL       │ Save cookies                              │
│                                                                              │
│  CURL DATA OPTIONS                                                            │
│  ────────────────                                                            │
│  curl -d "key=value" URL       │ Form data                                 │
│  curl -d '{"key":"val"}' URL   │ JSON string                               │
│  curl -d @file.json URL        │ Data from file                            │
│  curl -F "file=@file" URL      │ File upload                               │
│                                                                              │
│  HTTPIE (user-friendly)                                                       │
│  ────────────────                                                            │
│  http URL                      │ GET request (colorized)                    │
│  http POST URL key=value       │ POST with data                            │
│  http -a user:pass URL         │ Basic auth                                │
│  http --download URL           │ Download file                             │
│                                                                              │
│  JQ (JSON processor)                                                          │
│  ────────────────                                                            │
│  jq '.'                        │ Pretty print                               │
│  jq '.field'                   │ Get field                                 │
│  jq '.[]'                      │ Array elements                            │
│  jq '.[] | select(.id>5)'      │ Filter array                             │
│  jq 'keys'                     │ List keys                                 │
│  jq 'length'                   │ Count elements                            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🏆 BONUS: ADVANCED TECHNIQUES

### HTTP Request Flowchart

```
                    ┌─────────────────────────┐
                    │   What HTTP method?     │
                    └───────────┬─────────────┘
                                │
          ┌─────────────────────┼─────────────────────┐
          │                     │                     │
          ▼                     ▼                     ▼
    ┌───────────┐         ┌───────────┐         ┌───────────┐
    │  GET/HEAD │         │  POST/PUT │         │  DELETE   │
    └─────┬─────┘         └─────┬─────┘         └─────┬─────┘
          │                     │                     │
          ▼                     ▼                     ▼
    ┌───────────┐         ┌───────────┐         ┌───────────┐
    │ curl -sL  │         │ curl -X   │         │ curl -X   │
    │ URL       │         │ POST -d   │         │ DELETE    │
    └───────────┘         │ -H json   │         └───────────┘
                          └───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │ What's the response?  │
                    └───────────┬───────────┘
                                │
          ┌─────────────────────┼─────────────────────┐
          │                     │                     │
          ▼                     ▼                     ▼
    ┌───────────┐         ┌───────────┐         ┌───────────┐
    │  2xx OK   │         │  4xx ERR  │         │  5xx ERR │
    └─────┬─────┘         └─────┬─────┘         └─────┬─────┘
          │                     │                     │
          ▼                     ▼                     ▼
    ┌───────────┐         ┌───────────┐         ┌───────────┐
    │ Process   │         │ Check:    │         │ Server    │
    │ with jq   │         │ - Headers │         │ issue     │
    └───────────┘         │ - Auth    │         └───────────┘
                          │ - Data    │
                          └───────────┘
```

### Advanced curl One-Liners

```bash
# Check website is up with timing info
curl -s -o /dev/null -w "HTTP: %{http_code}\nTime: %{time_total}s\nSize: %{size_download} bytes\n" URL

# Download with retry and resume
curl -C - --retry 3 --retry-delay 5 -O URL

# Test for HTTP methods allowed
for method in GET POST PUT DELETE PATCH OPTIONS; do
  echo -n "$method: "; curl -s -o /dev/null -w "%{http_code}\n" -X $method URL
done

# Extract all links from webpage
curl -s URL | grep -oP 'href="\K[^"]+' | sort -u

# Test API authentication
curl -s -H "Authorization: Bearer INVALID" URL | jq .

# Check SSL certificate details
curl -vI https://example.com 2>&1 | grep -A 10 "SSL connection"

# Send webhook notification
curl -X POST -H "Content-Type: application/json" \
  -d '{"text":"Alert: Server down!"}' \
  https://hooks.slack.com/services/YOUR/WEBHOOK/URL

# Download all images from webpage
curl -s URL | grep -oP 'src="\K[^"]+\.(jpg|png|gif)' | while read img; do
  curl -O "$img"
done

# Test redirect chain
curl -sIL URL | grep -E "HTTP|location"

# Benchmark API response times
for i in {1..10}; do
  curl -s -o /dev/null -w "Request $i: %{time_total}s\n" URL
done
```

---

## 🎯 SECURITY CONSIDERATIONS

### Legal Disclaimers

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ⚠️ HTTP TOOLS SECURITY WARNING ⚠️                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  HTTP TOOLS CAN BE USED FOR BOTH LEGITIMATE AND ILLEGAL PURPOSES           │
│                                                                              │
│  ⚠️ Authorized uses:                                                        │
│     • Testing your own APIs                                                │
│     • Security assessments with permission                                  │
│     • Network administration                                               │
│     • Development and debugging                                            │
│                                                                              │
│  ⚠️ Potentially illegal uses:                                               │
│     • Unauthorized API access                                               │
│     • Credential stuffing attacks                                          │
│     • DDoS through excessive requests                                      │
│     • Exploiting web vulnerabilities                                      │
│                                                                              │
│  BEST PRACTICES:                                                             │
│  • Always get authorization before testing APIs                            │
│  • Respect rate limits                                                     │
│  • Never test credentials you don't own                                   │
│  • Document all testing activities                                        │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Ethical Use Guidelines

1. **Only test APIs you own or have permission to test**
2. **Respect rate limits and terms of service**
3. **Don't use stolen or leaked credentials**
4. **Report vulnerabilities responsibly**
5. **Clean up test data after testing**

### Authorization Checklist

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ✅ API TESTING AUTHORIZATION CHECKLIST                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  □ API owner has given written permission                                  │
│  □ Scope of testing defined (endpoints, methods)                           │
│  □ Test credentials provided (not production)                               │
│  □ Rate limits agreed upon                                                  │
│  □ Testing window specified                                                │
│  □ Emergency contacts exchanged                                             │
│  □ Rules of engagement documented                                          │
│                                                                              │
│  FOR SECURITY TESTING:                                                       │
│  □ Specific authorization for security tests                               │
│  □ Isolated test environment confirmed                                     │
│  □ Impact assessment completed                                             │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🚀 TOOL COMPARISON

### HTTP Clients Comparison

| Feature | curl | wget | httpie | httpx |
|---------|------|------|--------|-------|
| GET requests | ✅ | ✅ | ✅ | ✅ |
| POST requests | ✅ | ❌ | ✅ | ✅ |
| Custom headers | ✅ | ✅ | ✅ | ✅ |
| JSON support | ✅ | ❌ | ✅✅ | ✅ |
| Color output | ❌ | ❌ | ✅ | ✅ |
| SSL/TLS options | ✅ | ✅ | ✅ | ✅ |
| Proxy support | ✅ | ✅ | ✅ | ✅ |
| File upload | ✅ | ✅ | ✅ | ❌ |
| Bulk testing | ❌ | ❌ | ❌ | ✅✅ |
| Tech detection | ❌ | ❌ | ❌ | ✅✅ |
| Scripting | ✅✅ | ✅ | ✅ | ✅ |
| Learning curve | Medium | Easy | Easy | Medium |

### When to Use Which Tool

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    🔧 HTTP TOOL SELECTION GUIDE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  USE CURL WHEN:                                                             │
│  ├── Writing scripts or automation                                         │
│  ├── Need maximum flexibility                                              │
│  ├── Working with complex authentication                                   │
│  ├── Debugging network issues                                              │
│  └── CI/CD pipelines                                                       │
│                                                                              │
│  USE WGET WHEN:                                                             │
│  ├── Downloading files                                                     │
│  ├── Mirroring websites                                                    │
│  ├── Recursive downloads                                                   │
│  └── Resume interrupted downloads                                          │
│                                                                              │
│  USE HTTPIE WHEN:                                                           │
│  ├── Interactive API testing                                               │
│  ├── Learning HTTP concepts                                                │
│  ├── Need readable output                                                  │
│  └── Quick manual testing                                                 │
│                                                                              │
│  USE HTTPX WHEN:                                                            │
│  ├── Bulk HTTP probing                                                    │
│  ├── Reconnaissance (tech detection)                                       │
│  ├── Security assessments                                                  │
│  └── Processing multiple URLs                                              │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 OUTPUT ANALYSIS

### HTTP Status Code Reference

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    HTTP STATUS CODES CHEAT SHEET                            │
├──────┬──────────────────┬───────────────────────────────────────────────────┤
│ Code │ Status           │ Meaning                                        │
├──────┼──────────────────┼───────────────────────────────────────────────────┤
│ 200  │ OK               │ Request succeeded                              │
│ 201  │ Created          │ Resource created successfully                  │
│ 204  │ No Content       │ Success, no body returned                      │
│ 301  │ Moved Permanently│ Resource moved permanently                     │
│ 302  │ Found            │ Temporary redirect                             │
│ 304  │ Not Modified     │ Cached version is valid                        │
│ 400  │ Bad Request      │ Invalid request syntax                         │
│ 401  │ Unauthorized     │ Authentication required                        │
│ 403  │ Forbidden        │ Access denied                                  │
│ 404  │ Not Found        │ Resource doesn't exist                         │
│ 405  │ Method Not Allowed│ HTTP method not supported                    │
│ 408  │ Request Timeout  │ Server timed out waiting                       │
│ 429  │ Too Many Requests│ Rate limit exceeded                            │
│ 500  │ Internal Error   │ Server error                                   │
│ 502  │ Bad Gateway      │ Invalid response from upstream                 │
│ 503  │ Unavailable      │ Server overloaded                              │
│ 504  │ Gateway Timeout  │ Upstream server timeout                        │
└──────┴──────────────────┴───────────────────────────────────────────────────┘
```

### Response Header Analysis

```
HTTP/1.1 200 OK                    ← Status line
Server: nginx/1.18.0              ← Web server
Date: Mon, 01 Jan 2024 12:00:00 GMT ← Timestamp
Content-Type: application/json    ← Response format
Content-Length: 1234             ← Body size
Connection: keep-alive           ← Connection type
X-Frame-Options: DENY            ← Security header
X-XSS-Protection: 1              ← XSS protection
Strict-Transport-Security: max-age=31536000 ← HTTPS enforcement
Set-Cookie: session=abc123       ← Cookie being set

KEY HEADERS TO CHECK:
├── Server: Reveals server software
├── X-Powered-By: Framework/language
├── X-Frame-Options: Clickjacking protection
├── Content-Security-Policy: XSS prevention
├── Strict-Transport-Security: HTTPS enforcement
└── Set-Cookie: Session management
```

### jq Output Analysis

```
# API Response:
{"users": [{"id": 1, "name": "John"}, {"id": 2, "name": "Jane"}]}

# jq '.users'          → Returns users array
# jq '.users[0]'       → First user object
# jq '.users[].name'   → All names: "John" "Jane"
# jq '.users | length' → Count: 2
# jq '.users[] | select(.id > 1)' → Filter: second user
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### Key Takeaways

✅ **HTTP Protocol**
- Request/response model
- Methods: GET, POST, PUT, PATCH, DELETE
- Status codes: 2xx, 3xx, 4xx, 5xx

✅ **curl Command**
- Most versatile HTTP client
- Supports all methods, headers, authentication
- Perfect for scripting and automation

✅ **httpie**
- User-friendly alternative to curl
- Colorized output
- JSON support built-in

✅ **httping**
- HTTP latency testing
- Server health monitoring

✅ **httpx**
- Bulk HTTP probing
- Technology detection
- Security reconnaissance

✅ **jq**
- JSON processing
- Powerful filtering and transformation
- API response parsing

### Skills Acquired

1. **API testing** - Making various HTTP requests
2. **JSON processing** - Parsing and filtering JSON data
3. **Web debugging** - Analyzing HTTP headers and responses
4. **Automation** - Scripting HTTP tasks

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relation |
|---------|-------|----------|
| **Ch24** | Networking Basics | Foundation concepts |
| **Ch25** | Nmap Basics | Port scanning for web servers |
| **Ch27** | Netcat Mastery | Raw HTTP connections |
| **Ch29** | DNS & Domain Tools | DNS for HTTP |
| **Ch38** | Metasploit | Exploitation via HTTP |
| **Ch40** | Web Application Security | Web vulnerability testing |

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your Knowledge (10 Questions)

**Q1:** Which curl flag follows redirects?
- A) `-r`
- B) `-L`
- C) `-f`
- D) `-R`

<details>
<summary>Answer</summary>
B) `-L` - Follows HTTP redirects (301, 302, etc.)
</details>

**Q2:** What jq command extracts a field from JSON?
- A) `jq get field`
- B) `jq '.field'`
- C) `jq -f field`
- D) `jq extract field`

<details>
<summary>Answer</summary>
B) `jq '.field'` - Uses JSONPath syntax
</details>

**Q3:** Which tool is best for bulk HTTP probing?
- A) curl
- B) wget
- C) httpx
- D) httpie

<details>
<summary>Answer</summary>
C) httpx - Designed for bulk reconnaissance
</details>

**Q4:** What does HTTP status 404 mean?
- A) Success
- B) Redirect
- C) Not Found
- D) Server Error

<details>
<summary>Answer</summary>
C) Not Found - Resource doesn't exist
</details>

**Q5:** Which curl flag shows only headers?
- A) `-h`
- B) `-I`
- C) `-H`
- D) `-head`

<details>
<summary>Answer</summary>
B) `-I` - Fetches headers only (HEAD request)
</details>

**Q6:** What's the user-friendly alternative to curl?
- A) wget
- B) httpx
- C) httpie
- D) httping

<details>
<summary>Answer</summary>
C) httpie - Colorized, human-readable output
</details>

**Q7:** Which HTTP method creates a new resource?
- A) GET
- B) POST
- C) PUT
- D) DELETE

<details>
<summary>Answer</summary>
B) POST - Creates new resources
</details>

**Q8:** How do you send JSON content type in curl?
- A) `-H "Content-Type: application/json"`
- B) `-json`
- C) `-j`
- D) `--json-type`

<details>
<summary>Answer</summary>
A) `-H "Content-Type: application/json"` - Custom header
</details>

**Q9:** What does HTTP status 401 indicate?
- A) Forbidden
- B) Not Found
- C) Unauthorized
- D) Bad Request

<details>
<summary>Answer</summary>
C) Unauthorized - Authentication required
</details>

**Q10:** Which command saves cookies from response?
- A) `curl -b cookies.txt`
- B) `curl -c cookies.txt`
- C) `curl -s cookies.txt`
- D) `curl --save-cookies`

<details>
<summary>Answer</summary>
B) `curl -c cookies.txt` - Saves cookies to file
</details>

---

### HTTP Challenges

**Challenge 1: API Testing**
```bash
# Task: Make a POST request with JSON data
# Difficulty: ⭐⭐

curl -X POST -H "Content-Type: application/json" \
  -d '{"title":"Test","body":"Content"}' \
  https://jsonplaceholder.typicode.com/posts
```

**Challenge 2: JSON Parsing**
```bash
# Task: Extract all email addresses from API response
# Difficulty: ⭐⭐

curl -s https://jsonplaceholder.typicode.com/users | jq '.[].email'
```

**Challenge 3: Header Analysis**
```bash
# Task: Extract all security headers from a website
# Difficulty: ⭐⭐⭐

curl -sI https://example.com | grep -i "x-\|strict-\|content-security"
```

---

### CTF-Style Exercises

**Exercise 1: API Reconnaissance**
```
🎯 Objective: Discover all available endpoints of an API
   and document what each returns.

🔧 Tools: curl, jq

📝 Steps:
1. Test common endpoints
2. Check response codes
3. Document findings

⏱️ Time: 20 minutes
```

**Exercise 2: Authentication Bypass Test**
```
🎯 Objective: Test various authentication methods
   on a test API endpoint.

🔧 Tools: curl with various auth headers

📝 Steps:
1. Test no auth
2. Test with Authorization header
3. Test with API key
4. Document results

⏱️ Time: 15 minutes
```

**Exercise 3: Performance Benchmark**
```
🎯 Objective: Measure and compare API response times
   across different endpoints.

🔧 Tools: curl with -w flag

📝 Steps:
1. Create benchmark script
2. Test 5 endpoints
3. Compare results

⏱️ Time: 25 minutes
```

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 🎮 INTERACTIVE QUIZ - Test Your HTTP Tools Knowledge!

### Questions (Answers at the end)

**Q1.** What does HTTP stand for?
- A) HyperText Transfer Protocol
- B) HyperText Transmission Protocol
- C) High Transfer Text Protocol
- D) HyperText Transit Protocol

**Q2.** Which HTTP status code indicates success?
- A) 404
- B) 200
- C) 500
- D) 301

**Q3.** What curl flag shows only headers?
- A) -H
- B) -I
- C) -h
- D) -head

**Q4.** Which tool has the most user-friendly syntax for APIs?
- A) curl
- B) wget
- C) httpie
- D) httping

**Q5.** What does -L flag do in curl?
- A) List files
- B) Follow redirects
- C) Large output
- D) Local mode

**Q6.** Which HTTP method creates new data?
- A) GET
- B) PUT
- C) POST
- D) PATCH

**Q7.** What tool is best for testing HTTP latency?
- A) curl
- B) httping
- C) httpx
- D) httpie

**Q8.** Which command parses JSON output?
- A) curl
- B) jq
- C) grep
- D) awk

**Q9.** What does -X flag specify in curl?
- A) Proxy
- B) HTTP method
- C) Output file
- D) Extra headers

**Q10.** Which tool is best for bulk URL testing?
- A) httpie
- B) curl
- C) httpx
- D) wget

**BONUS Q11.** What does 403 status code mean?
- A) Not Found
- B) Unauthorized
- C) Forbidden
- D) Bad Request

**BONUS Q12.** Which jq filter gets all items in an array?
- A) .[]
- B) .*
- C) .all
- D) .array

### Quiz Answers

| Q | Answer | Explanation |
|---|--------|-------------|
| Q1 | **A** | HTTP = HyperText Transfer Protocol |
| Q2 | **B** | 200 = OK (success) |
| Q3 | **B** | -I shows headers only (HEAD request) |
| Q4 | **C** | httpie has the most readable syntax |
| Q5 | **B** | -L follows HTTP redirects |
| Q6 | **C** | POST creates new data, PUT updates |
| Q7 | **B** | httping tests HTTP latency |
| Q8 | **B** | jq is the JSON processor |
| Q9 | **B** | -X specifies HTTP method (GET, POST, etc.) |
| Q10 | **C** | httpx is designed for bulk URL testing |
| Q11 | **C** | 403 = Forbidden (access denied) |
| Q12 | **A** | .[] iterates through all array items |

---

## 💡 PRO TIPS - HTTP Tools Expert Tips

### Pro Tip #1: Beautiful JSON Output
```bash
# Always pipe JSON through jq for readability
curl -s https://api.example.com/data | jq

# Extract specific field
curl -s https://api.example.com/users | jq '.[].name'
```

### Pro Tip #2: Silent Curl with Error Handling
```bash
# Silent mode but show errors
curl -sS https://example.com

# Fail on HTTP errors
curl -f https://example.com || echo "Request failed"
```

### Pro Tip #3: Debug HTTP Requests
```bash
# See complete request and response
curl -v https://example.com

# Only response headers
curl -I https://example.com

# Time breakdown
curl -w "DNS: %{time_namelookup}s\nConnect: %{time_connect}s\nTotal: %{time_total}s\n" https://example.com
```

### Pro Tip #4: Save and Use Cookies
```bash
# Login and save cookies
curl -c cookies.txt -X POST -d "user=test&pass=123" https://example.com/login

# Use saved cookies
curl -b cookies.txt https://example.com/dashboard
```

### Pro Tip #5: Test API Endpoints Quickly
```bash
# With httpie (cleaner syntax)
http GET https://api.example.com/users
http POST https://api.example.com/users name=John age:=25
```

### Pro Tip #6: Download with Progress
```bash
# Progress bar only
curl -# -O https://example.com/file.zip

# Resume download
curl -C - -O https://example.com/file.zip
```

### Pro Tip #7: Test with Different User Agents
```bash
# Mobile user agent
curl -A "Mozilla/5.0 (iPhone; CPU iPhone OS 14_0)" https://example.com

# Googlebot
curl -A "Googlebot/2.1" https://example.com
```

### Pro Tip #8: Batch URL Testing
```bash
# Test multiple URLs with httpx
httpx -l urls.txt -title -status-code -tech-detect
```

### Pro Tip #9: POST JSON Easily
```bash
# With curl
curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' URL

# With httpie (easier)
http POST URL key=value
```

### Pro Tip #10: Rate Limiting
```bash
# Limit request rate
curl --limit-rate 100K https://example.com/largefile

# Delay between requests (bash)
for url in $(cat urls.txt); do
    curl -s "$url"
    sleep 1
done
```

---

## 🔥 REAL WORLD USE CASES - Penetration Testing Scenarios

### Scenario 1: API Security Testing
```
OBJECTIVE: Test API for security vulnerabilities

STEP 1: Discover endpoints
$ curl -s https://api.example.com/ | jq

STEP 2: Test authentication
$ curl -H "Authorization: Bearer invalid_token" https://api.example.com/users

STEP 3: Test for IDOR (Insecure Direct Object Reference)
$ for i in {1..10}; do curl -s "https://api.example.com/users/$i" | jq; done

STEP 4: Test HTTP methods
$ curl -X OPTIONS https://api.example.com/users -v
$ curl -X PUT https://api.example.com/users/1 -d '{"admin":true}'
```

### Scenario 2: Web Application Fingerprinting
```
OBJECTIVE: Identify technologies used by web application

STEP 1: Header analysis
$ curl -I https://target.com

STEP 2: Technology detection
$ httpx -u https://target.com -tech-detect -title

STEP 3: Server information
$ curl -s https://target.com | grep -i "powered by"

STEP 4: SSL certificate info
$ echo | openssl s_client -connect target.com:443 2>/dev/null | openssl x509 -noout -text
```

### Scenario 3: Authentication Testing
```
OBJECTIVE: Test authentication mechanisms

STEP 1: Basic auth brute force detection
$ curl -u admin:wrongpass https://target.com/admin

STEP 2: Test for default credentials
$ curl -u admin:admin https://target.com/admin
$ curl -u root:root https://target.com/admin

STEP 3: Token testing
$ curl -H "Authorization: Bearer eyJ..." https://target.com/api/user

STEP 4: Session testing
$ curl -b "session=abc123" https://target.com/dashboard
```

### Scenario 4: Content Discovery
```
OBJECTIVE: Discover hidden content

STEP 1: Robots.txt
$ curl -s https://target.com/robots.txt

STEP 2: Sitemap
$ curl -s https://target.com/sitemap.xml

STEP 3: Common files
$ for file in .git/config .env backup.zip admin; do
    curl -s -o /dev/null -w "%{http_code}" https://target.com/$file
    echo " $file"
done

STEP 4: Directory enumeration
$ httpx -l wordlist.txt -u https://target.com/FUZZ -mc 200,301,302
```

---

## ⚡ QUICK REFERENCE CARD - HTTP Commands

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    HTTP TOOLS QUICK REFERENCE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  CURL BASICS                                                             │
│  ───────────                                                             │
│  curl URL                    GET request                                 │
│  curl -I URL                 Headers only                                │
│  curl -L URL                 Follow redirects                            │
│  curl -v URL                 Verbose output                              │
│  curl -s URL                 Silent mode                                 │
│  curl -o file URL            Save to file                                │
│  curl -O URL                 Save with original name                     │
│                                                                          │
│  CURL HTTP METHODS                                                        │
│  ─────────────────                                                       │
│  curl -X GET URL             GET request                                 │
│  curl -X POST URL            POST request                                │
│  curl -X PUT URL             PUT request                                 │
│  curl -X DELETE URL          DELETE request                              │
│  curl -X PATCH URL           PATCH request                               │
│                                                                          │
│  CURL DATA                                                               │
│  ──────────                                                               │
│  curl -d "key=value" URL     Form data                                   │
│  curl -d @file URL           Data from file                              │
│  curl -d '{"json":"data"}' URL JSON data                                 │
│  curl -F "file=@path" URL    File upload                                 │
│                                                                          │
│  CURL HEADERS                                                            │
│  ─────────────                                                           │
│  curl -H "Header: Value" URL Custom header                               │
│  curl -H "Content-Type: json" URL JSON content type                     │
│  curl -H "Authorization: Bearer TOKEN" URL Auth header                  │
│                                                                          │
│  CURL AUTH                                                               │
│  ──────────                                                               │
│  curl -u user:pass URL       Basic auth                                  │
│  curl -H "Bearer TOKEN" URL  Bearer token                                │
│  curl -b "cookie=value" URL  Send cookie                                 │
│  curl -c cookies.txt URL     Save cookies                                │
│                                                                          │
│  HTTPIE                                                                  │
│  ───────                                                                 │
│  http URL                    GET request                                 │
│  http POST URL key=value     POST with data                              │
│  http -a user:pass URL       Basic auth                                  │
│  http --download URL         Download file                               │
│  http --session=name URL     Use session                                 │
│                                                                          │
│  HTTPING                                                                 │
│  ────────                                                                │
│  httping URL                 Test latency                                │
│  httping -c 5 URL            5 requests                                  │
│  httping -s URL              Show status codes                           │
│  httping -X POST URL         POST method                                 │
│                                                                          │
│  HTTPX                                                                   │
│  ─────                                                                   │
│  httpx -u URL                Basic probe                                 │
│  httpx -l urls.txt           Probe list                                  │
│  httpx -u URL -tech-detect   Technology detection                        │
│  httpx -u URL -title         Get page title                              │
│  httpx -u URL -screenshot    Take screenshot                             │
│                                                                          │
│  JQ (JSON PROCESSOR)                                                      │
│  ─────────────────                                                       │
│  jq '.'                      Pretty print                                │
│  jq '.field'                 Get field                                   │
│  jq '.[]'                    All array items                             │
│  jq '.[] | .field'           Field from all items                        │
│  jq 'keys'                   List keys                                   │
│  jq 'length'                 Count items                                 │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🏆 BONUS CONTENT - Advanced HTTP Techniques

### Bonus #1: API Testing Script
```bash
#!/bin/bash
# api_test.sh - Automated API testing

API="https://jsonplaceholder.typicode.com"

echo "[*] Testing API: $API"

# GET all posts
echo "[+] GET /posts"
curl -s "$API/posts?_limit=3" | jq '.[].title'

# POST new post
echo "[+] POST /posts"
curl -s -X POST "$API/posts" \
    -H "Content-Type: application/json" \
    -d '{"title":"Test","body":"Content","userId":1}' | jq '.id'

# PUT update
echo "[+] PUT /posts/1"
curl -s -X PUT "$API/posts/1" \
    -H "Content-Type: application/json" \
    -d '{"title":"Updated"}' | jq '.title'

# DELETE
echo "[+] DELETE /posts/1"
curl -s -X DELETE "$API/posts/1" -w "Status: %{http_code}\n"

echo "[*] API test complete"
```

### Bonus #2: Header Security Check
```bash
#!/bin/bash
# security_headers.sh - Check security headers

URL=$1

echo "[*] Checking security headers for: $URL"
echo

headers=$(curl -sI $URL)

check_header() {
    local header=$1
    if echo "$headers" | grep -qi "$header"; then
        echo "[✓] $header: Present"
    else
        echo "[✗] $header: Missing"
    fi
}

check_header "X-Frame-Options"
check_header "X-Content-Type-Options"
check_header "X-XSS-Protection"
check_header "Strict-Transport-Security"
check_header "Content-Security-Policy"
check_header "Referrer-Policy"
check_header "Permissions-Policy"
```

### Bonus #3: JWT Decoder
```bash
#!/bin/bash
# jwt_decode.sh - Decode JWT tokens

JWT=$1

# Split by dots
header=$(echo $JWT | cut -d. -f1)
payload=$(echo $JWT | cut -d. -f2)

echo "=== HEADER ==="
echo $header | base64 -d 2>/dev/null | jq

echo "=== PAYLOAD ==="
echo $payload | base64 -d 2>/dev/null | jq
```

### Bonus #4: Mass URL Checker
```bash
#!/bin/bash
# url_checker.sh - Check multiple URLs

while read url; do
    status=$(curl -s -o /dev/null -w "%{http_code}" "$url")
    echo "$status - $url"
done < urls.txt
```

---

## 📝 CHAPTER SUMMARY - Key Takeaways

### Core Concepts Learned
- **HTTP Protocol**: Methods, status codes, headers
- **curl**: Versatile HTTP client
- **httpie**: User-friendly alternative
- **httping**: Latency testing
- **httpx**: Bulk URL testing
- **jq**: JSON processing
- **Authentication**: Basic, Bearer, API keys
- **Cookies**: Session management

### Essential Commands
| Command | Purpose |
|---------|---------|
| `curl -I URL` | Get headers |
| `curl -X POST -d "data" URL` | POST data |
| `http POST URL key=value` | Easy POST |
| `httping URL` | Test latency |
| `httpx -l urls.txt` | Bulk test |
| `jq '.field'` | Parse JSON |

---

## 🛡️ SECURITY CONSIDERATIONS

### Legal Requirements
```
┌─────────────────────────────────────────────────────────────────────────┐
│                         ⚠️ LEGAL WARNING ⚠️                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  TESTING WEB APPLICATIONS WITHOUT PERMISSION IS ILLEGAL!                │
│                                                                          │
│  AUTHORIZED TESTING ONLY:                                                │
│  ✓ Bug bounty programs                                                   │
│  ✓ Penetration testing contracts                                        │
│  ✓ Your own applications                                                │
│  ✓ Test environments (CTF, labs)                                        │
│                                                                          │
│  NEVER:                                                                  │
│  ✗ Test APIs without authorization                                      │
│  ✗ Attempt to access other users' data                                  │
│  ✗ Perform denial of service attacks                                    │
│  ✗ Exploit vulnerabilities without reporting                            │
│                                                                          │
│  RESPONSIBLE DISCLOSURE:                                                 │
│  • Report vulnerabilities privately                                     │
│  • Allow time for fixes                                                 │
│  • Don't disclose publicly without permission                           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🚀 TOOL COMPARISON - HTTP Tools

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    HTTP TOOLS COMPARISON                                 │
├──────────────┬────────────────────┬──────────────────────────────────────┤
│ Tool         │ Best For           │ Key Strength                        │
├──────────────┼────────────────────┼──────────────────────────────────────┤
│ curl         │ Scripting/Automation │ Most features, universal          │
│ httpie       │ Interactive use    │ User-friendly syntax                │
│ wget         │ Downloads          │ Recursive downloads                 │
│ httping      │ Latency testing    │ Server monitoring                   │
│ httpx        │ Recon/Bulk testing │ Fast, multi-purpose                 │
│ jq           │ JSON processing    │ Powerful filtering                  │
└──────────────┴────────────────────┴──────────────────────────────────────┘
```

---

## 📊 OUTPUT ANALYSIS - HTTP Response Interpretation

### Status Code Analysis
```
┌─────────────────────────────────────────────────────────────────────────┐
│                    HTTP STATUS CODE MEANINGS                             │
├──────────┬──────────────────────────────────────────────────────────────┤
│ 2xx      │ SUCCESS                                                       │
│ 200 OK   │ Request succeeded                                             │
│ 201 Created │ Resource created successfully                             │
│ 204 No Content │ Success, no response body                              │
├──────────┼──────────────────────────────────────────────────────────────┤
│ 3xx      │ REDIRECTION                                                   │
│ 301 Moved Permanently │ Resource moved permanently                      │
│ 302 Found │ Resource temporarily moved                                   │
│ 304 Not Modified │ Cached version is valid                              │
├──────────┼──────────────────────────────────────────────────────────────┤
│ 4xx      │ CLIENT ERROR                                                  │
│ 400 Bad Request │ Invalid request syntax                                │
│ 401 Unauthorized │ Authentication required                              │
│ 403 Forbidden │ Access denied                                            │
│ 404 Not Found │ Resource doesn't exist                                   │
│ 429 Too Many Requests │ Rate limit exceeded                             │
├──────────┼──────────────────────────────────────────────────────────────┤
│ 5xx      │ SERVER ERROR                                                  │
│ 500 Internal Error │ Server error                                       │
│ 502 Bad Gateway │ Invalid upstream response                             │
│ 503 Unavailable │ Server overloaded                                     │
│ 504 Gateway Timeout │ Upstream timeout                                  │
└──────────┴──────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS - Cross-References

### Prerequisites
| Chapter | Topic | Why It's Important |
|---------|-------|-------------------|
| Ch24 | Networking Basics | HTTP understanding |
| Ch27 | Netcat | Raw connections |

### Next Steps
| Chapter | Topic | What You'll Learn |
|---------|-------|-------------------|
| Ch29 | DNS Tools | Domain reconnaissance |
| Ch30-35 | Security Tools | Web exploitation |

---

*Chapter 28 UPGRADED with 10 POWERFUL features! 🚀*
