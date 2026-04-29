# Chapter 53: Project 3 - WiFi Analyzer

> **Module:** 9 - Projects  
> **Chapter:** 53 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | WiFi scanning with Termux API |
| Project Implementation | Complete WiFi Analyzer tool |
| Source Code | Full Python implementation |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common issues and fixes |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 53
Title: Project 3 - WiFi Analyzer | Build Your Own Network Scanner | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut exciting hai - hum banayenge apna khud ka WiFi Analyzer
tool! Ye project aapko bahut kuch sikhayega - API integration, data parsing,
report generation, aur real-time monitoring.

WiFi Analyzer kya hai? Ye ek aisa tool hai jo aapke aas-paas ke WiFi networks
scan karta hai aur unki complete information dikhata hai - signal strength,
encryption type, channel, BSSID, frequency - sab kuch ek jagah!

Network administrators use karte hain, penetration testers use karte hain,
aur ab aap bhi apna khud ka tool bana sakte ho - bina kisi external app ke!

To chaliye shuru karte hain - WiFi Analyzer project!

Play button dabaiye, video like karein, channel subscribe karein!

---

[SECTION 1: PROJECT OVERVIEW - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samajhte hain ki hum kya bana rahe hain aur kyun.

WiFi Analyzer ek network scanning tool hai jo:
1. Nearby WiFi networks discover karta hai
2. Har network ki detailed information dikhata hai
3. Signal strength analyze karta hai
4. Security configuration check karta hai
5. Channel congestion identify karta hai
6. Network recommendations deta hai

┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI ANALYZER FEATURES                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    SCAN AVAILABLE NETWORKS                       │   │
│   │   • SSID (Network Name)                                         │   │
│   │   • BSSID (MAC Address)                                         │   │
│   │   • Signal Strength (dBm)                                       │   │
│   │   • Frequency (2.4GHz / 5GHz)                                   │   │
│   │   • Channel Number                                              │   │
│   │   • Encryption Type (WPA2, WPA3, Open, etc.)                    │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    ANALYSIS & REPORTING                         │   │
│   │   • Signal Quality Assessment                                   │   │
│   │   • Security Rating                                             │   │
│   │   • Channel Overlap Detection                                   │   │
│   │   • Network Recommendations                                     │   │
│   │   • Export to File (JSON/Text)                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Real-world use cases:

1. Network Troubleshooting: WiFi slow hai? Check karo signal strength
   aur channel congestion.

2. Security Auditing: Kaunse networks open hain? Kaunse weak encryption
   use kar rahe hain?

3. Site Survey: Naya WiFi setup kar rahe ho? Best channel select karo.

4. Penetration Testing: Target identification ke liye - humne previous
   chapters mein dekha tha.

Is project se aap seekhoge:
✓ Termux WiFi API ka deep usage
✓ JSON data parsing Python mein
✓ Rich console output formatting
✓ Real-time monitoring loops
✓ Report generation
✓ Error handling best practices

---

[SECTION 2: TERMUX WIFI API DEEP DIVE - 4:00 to 7:30]
─────────────────────────────────────────────────────────────────────────────

Ab hum Termux WiFi API ko detail mein samajhte hain.

Termux ke paas do main WiFi commands hain:

[COMMAND 1: termux-wifi-scaninfo]

Ye command nearby WiFi networks scan karta hai:

    termux-wifi-scaninfo

Output JSON format mein aata hai:

[
  {
    "bssid": "AA:BB:CC:DD:EE:FF",
    "frequency": 2437,
    "channel": 6,
    "level": -45,
    "timestamp": 1699876543210,
    "ssid": "MyWiFi",
    "capabilities": "[WPA2-PSK-CCMP][ESS]",
    "centerFreq0": 0,
    "centerFreq1": 0,
    "channelWidth": 0
  },
  ...
]

Let me explain each field:

┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI SCAN OUTPUT FIELDS                               │
├──────────────────┬──────────────────────────────────────────────────────┤
│ Field            │ Description                                          │
├──────────────────┼──────────────────────────────────────────────────────┤
│ bssid            │ MAC address of the access point (router)            │
│ ssid             │ Network name (hidden if network is hidden)          │
│ frequency        │ Frequency in MHz (2412-2484 for 2.4GHz,            │
│                  │ 5170-5825 for 5GHz)                                 │
│ channel          │ WiFi channel number (1-14 for 2.4GHz,              │
│                  │ 36-165 for 5GHz)                                    │
│ level            │ Signal strength in dBm (negative value,            │
│                  │ closer to 0 = stronger signal)                      │
│ capabilities     │ Security protocols supported (WPA2, WPA3, etc.)     │
│ timestamp        │ Scan timestamp in milliseconds                      │
│ channelWidth     │ Channel bandwidth (20MHz, 40MHz, 80MHz)            │
└──────────────────┴──────────────────────────────────────────────────────┘

[COMMAND 2: termux-wifi-connectioninfo]

Ye command currently connected WiFi ki info deta hai:

    termux-wifi-connectioninfo

Output:
{
  "bssid": "AA:BB:CC:DD:EE:FF",
  "frequency": 2437,
  "ip": "192.168.1.100",
  "link_speed": 65,
  "mac_address": "11:22:33:44:55:66",
  "network_id": 1,
  "rssi": -45,
  "ssid": "MyWiFi",
  "ssid_hidden": false
}

[COMMAND 3: termux-wifi-enable]

WiFi on/off karne ke liye:

    termux-wifi-enable true   # WiFi on
    termux-wifi-enable false  # WiFi off

⚠️ NOTE: Android 10+ mein ye command properly kaam nahi karti due to
Android restrictions. WiFi toggle ke liye Settings use karna padega.

[PERMISSION REQUIREMENT]

WiFi scan ke liye Location permission zaroori hai:

Android Settings:
Settings → Apps → Termux:API → Permissions → Location → Allow

Ya first scan pe popup aayega - "Allow" karein.

---

[SECTION 3: SIGNAL STRENGTH UNDERSTANDING - 7:30 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Signal strength samajhna bahut important hai. Ye dBm mein measure hota hai
(decibels relative to milliwatt).

WiFi signal values hamesha negative hote hain (-30 to -100):

┌─────────────────────────────────────────────────────────────────────────┐
│                    SIGNAL STRENGTH QUALITY CHART                         │
├──────────────────┬────────────────┬─────────────────────────────────────┤
│ Signal (dBm)     │ Quality        │ Experience                          │
├──────────────────┼────────────────┼─────────────────────────────────────┤
│ -30 to -50       │ ⭐⭐⭐⭐⭐ Excellent │ Right next to router                │
│ -50 to -60       │ ⭐⭐⭐⭐ Very Good  │ Strong signal, great speeds         │
│ -60 to -67       │ ⭐⭐⭐ Good        │ Reliable, good for streaming        │
│ -67 to -70       │ ⭐⭐ Fair         │ Okay for basic use                  │
│ -70 to -80       │ ⭐ Weak          │ Slow speeds, may disconnect         │
│ -80 to -90       │ ❌ Very Weak    │ Unreliable, frequent drops          │
│ -90 to -100      │ ❌ Unusable     │ Barely detectable                   │
└──────────────────┴────────────────┴─────────────────────────────────────┘

Real-world mein:
- -30 dBm: Router se 1-2 meter door
- -50 dBm: Same room mein
- -67 dBm: Ek wall ke peeche
- -80 dBm: Do teen walls ke peeche ya floor difference

Ye information humare tool mein signal quality rating ke liye use hoga.

---

[SECTION 4: CHANNEL ANALYSIS - 10:00 to 12:30]
─────────────────────────────────────────────────────────────────────────────

WiFi channels bahut important hain network performance ke liye.

[2.4 GHz Band Channels]

┌─────────────────────────────────────────────────────────────────────────┐
│                    2.4 GHz CHANNEL OVERLAP                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│ Channel:  1    2    3    4    5    6    7    8    9   10   11   12   13 │
│           ├────┼────┼────┼────┼────┼────┼────┼────┼────┼────┼────┼────┤  │
│           │████████████│                                                      │
│           │   Ch 1    │    (Center: 2412 MHz)                                │
│           │           │████████████│                                          │
│           │           │    Ch 6    │    (Center: 2437 MHz)                  │
│           │           │            │████████████│                            │
│           │           │            │    Ch 11   │    (Center: 2462 MHz)     │
│                                                                          │
│   ████ = Channel bandwidth (20MHz)                                       │
│   Non-overlapping channels: 1, 6, 11                                     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Key points:
• Channels 1, 6, 11 non-overlapping hain (best to use)
• Agar multiple networks same channel pe hain = interference
• Overlapping channels = speed issues

[5 GHz Band Channels]

5 GHz band mein zyada channels hain aur less interference:

Non-overlapping channels: 36, 40, 44, 48, 52, 56, 60, 64, 
                          100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 144, 
                          149, 153, 157, 161, 165

Benefits:
✓ More channels = less congestion
✓ Higher speeds
✓ Less interference from other devices

Drawbacks:
✗ Shorter range
✗ Walls penetrate nahi karti easily

Hamara tool channel congestion detect karega aur best channel recommend karega.

---

[SECTION 5: ENCRYPTION TYPES - 12:30 to 15:00]
─────────────────────────────────────────────────────────────────────────────

WiFi security bahut important hai. Let me explain encryption types:

┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI ENCRYPTION TYPES                                 │
├──────────────────────┬────────────────┬──────────────────────────────────┤
│ Type                 │ Security Level │ Description                      │
├──────────────────────┼────────────────┼──────────────────────────────────┤
│ Open (No encryption) │ ❌ None        │ No password required. Very risky │
│ WEP                  │ ❌ Broken      │ Deprecated. Easily cracked       │
│ WPA                  │ ⭐ Weak        │ Old standard. Vulnerable         │
│ WPA2-PSK             │ ⭐⭐⭐ Good     │ Current standard. Secure         │
│ WPA2-Enterprise      │ ⭐⭐⭐⭐ Very Good│ Corporate networks. 802.1X auth │
│ WPA3-PSK             │ ⭐⭐⭐⭐⭐ Excellent│ Latest standard. Best security   │
│ WPA3-Enterprise      │ ⭐⭐⭐⭐⭐ Excellent│ Enterprise grade WPA3           │
└──────────────────────┴────────────────┴──────────────────────────────────┘

Capabilities string mein ye aise dikhata hai:

[WPA2-PSK-CCMP][ESS]
└─┬──┘└─┬─┘└┬┘└─┬┘
  │     │    │   └─ Extended Service Set (infrastructure mode)
  │     │    └───── Cipher (CCMP = AES encryption, TKIP = older)
  │     └────────── Pre-Shared Key (password-based)
  └──────────────── WPA2 protocol

Common patterns:
• [WPA2-PSK-CCMP][ESS] = WPA2 Personal with AES (Good)
• [WPA2-PSK-CCMP+TKIP][ESS] = WPA2 with mixed mode
• [WPA3-PSK][ESS] = WPA3 Personal (Best)
• [ESS] = Open network (No security!)

Hamara tool ye parse karega aur security rating dega.

---

[SECTION 6: PROJECT STRUCTURE - 15:00 to 17:00]
─────────────────────────────────────────────────────────────────────────────

Ab hum project structure design karte hain:

~/wifi-analyzer/
├── wifi_analyzer.py      # Main application
├── modules/
│   ├── __init__.py
│   ├── scanner.py        # WiFi scanning functions
│   ├── analyzer.py       # Analysis functions
│   ├── display.py        # Output formatting
│   └── report.py         # Report generation
├── reports/              # Generated reports folder
└── requirements.txt      # Python dependencies

Hamare project mein ye features honge:

[FEATURE 1: Basic Scan]
• Single scan aur display all networks

[FEATURE 2: Detailed View]
• Single network ki complete details

[FEATURE 3: Continuous Monitor]
• Real-time signal monitoring
• Live updates har 5 seconds

[FEATURE 4: Analysis]
• Signal quality assessment
• Security rating
• Channel congestion analysis
• Best channel recommendation

[FEATURE 5: Report Generation]
• Export to JSON
• Export to Text
• Timestamp included

[FEATURE 6: Network Recommendations]
• Security improvement suggestions
• Channel optimization tips

---

[SECTION 7: CODING - PART 1 - 17:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Ab coding shuru karte hain. Pehle setup:

[STEP 1: Create Project Directory]

    mkdir -p ~/wifi-analyzer/modules
    mkdir -p ~/wifi-analyzer/reports
    cd ~/wifi-analyzer

[STEP 2: Install Dependencies]

    pkg install python -y
    pip install rich

Rich library se beautiful console output milta hai - colors, tables, progress bars!

[STEP 3: Create Main Application]

Ab main file likhte hain:

    nano wifi_analyzer.py

Main code mein ye features honge:
1. Scan nearby networks
2. Display in formatted table
3. Analyze signal strength
4. Check security status
5. Channel analysis
6. Generate reports
7. Continuous monitoring mode

Main code explain karta hoon step by step...

[CODE EXPLANATION]

Pehle imports:
- subprocess: Termux API commands run karne ke liye
- json: Output parse karne ke liye
- rich: Beautiful output ke liye
- datetime: Timestamps ke liye
- time: Continuous monitoring ke liye

WiFiScanner class banayenge with methods:
- scan_networks(): termux-wifi-scaninfo run karo
- parse_capabilities(): Security info extract karo
- get_signal_quality(): Signal strength rating
- analyze_channels(): Channel congestion check
- generate_report(): JSON/Text file create karo

display_results() function:
- Rich Table use karo beautiful output ke liye
- Color coding by signal strength
- Security badges

Main menu:
- Interactive menu with options
- User input se feature select karo

---

[SECTION 8: CODING - PART 2 - 20:00 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Ab detailed features implement karte hain:

[CONTINUOUS MONITORING MODE]

Ye feature real-time signal changes dikhata hai:

def monitor_mode(interval=5):
    while True:
        clear screen
        scan networks
        display results
        show signal graph (ASCII)
        wait for interval

[SIGNAL HISTORY TRACKING]

Previous readings store karo aur trend dikhao:
- Improving ⬆️
- Stable ➡️
- Declining ⬇️

[CHANNEL RECOMMENDATION LOGIC]

def recommend_channel(networks):
    # Count networks per channel
    # Find least congested channel
    # Check for overlapping
    # Return best option

[SECURITY ANALYSIS]

def analyze_security(capabilities):
    # Parse capabilities string
    # Identify encryption type
    # Check for vulnerabilities
    # Rate security level
    # Provide recommendations

[REPORT GENERATION]

JSON report structure:
{
    "scan_time": "2024-11-15 10:30:00",
    "total_networks": 12,
    "networks": [...],
    "analysis": {
        "best_signal": "MyWiFi",
        "most_secure": "OfficeNet",
        "channel_congestion": {...},
        "recommendations": [...]
    }
}

---

[SECTION 9: DEMO & TESTING - 23:00 to 25:00]
─────────────────────────────────────────────────────────────────────────────

Ab tool test karte hain!

[TEST 1: Basic Scan]

    python wifi_analyzer.py

Menu se option 1 select karo - Scan Networks

Dekho kaise networks list ho rahe hain with all details!

[TEST 2: Detailed Analysis]

Option 2 select karo - Analyze Network
Network number enter karo

Dekho detailed analysis with recommendations!

[TEST 3: Continuous Monitor]

Option 5 select karo - Monitor Mode

Dekho real-time updates har 5 second mein!

[TEST 4: Report Generation]

Option 6 select karo - Generate Report
Format choose karo (JSON/Text)

Report file check karo:
    cat reports/wifi_report_*.json

[SAMPLE OUTPUT]

┌─────────────────────────────────────────────────────────────────────────┐
│                        WIFI ANALYZER RESULTS                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Found 8 networks in range                                               │
│                                                                          │
│  ┌──────┬──────────────────┬─────────┬──────────┬────────┬───────────┐  │
│  │ #    │ SSID             │ Signal  │ Channel  │ Freq   │ Security  │  │
│  ├──────┼──────────────────┼─────────┼──────────┼────────┼───────────┤  │
│  │ 1    │ MyWiFi           │ -45 dBm │ 6        │ 2.4GHz │ WPA2 ✅   │  │
│  │ 2    │ Neighbor_Net     │ -67 dBm │ 6        │ 2.4GHz │ WPA2 ✅   │  │
│  │ 3    │ Office_5G        │ -72 dBm │ 36       │ 5GHz   │ WPA3 ⭐   │  │
│  │ 4    │ Guest_Network    │ -80 dBm │ 11       │ 2.4GHz │ OPEN ⚠️  │  │
│  │ 5    │ IoT_Devices      │ -85 dBm │ 1        │ 2.4GHz │ WPA ⚠️   │  │
│  └──────┴──────────────────┴─────────┴──────────┴────────┴───────────┘  │
│                                                                          │
│  📊 ANALYSIS SUMMARY:                                                    │
│  • Strongest Signal: MyWiFi (-45 dBm)                                   │
│  • Most Secure: Office_5G (WPA3)                                        │
│  • Open Networks: 1 (⚠️ Security Risk)                                  │
│  • Channel Congestion: Channel 6 (3 networks)                           │
│  • Recommended Channel: 11 (less crowded)                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 10: SUMMARY - 25:00 to 26:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 53 complete! WiFi Analyzer project ready hai!

Let's summarize kya kya seekha:

✅ WiFi scanning with termux-wifi-scaninfo
✅ Signal strength understanding (dBm)
✅ Channel analysis and congestion detection
✅ Encryption types and security rating
✅ Python implementation with Rich library
✅ Report generation (JSON/Text)
✅ Continuous monitoring mode
✅ Network recommendations

Important concepts yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    KEY CONCEPTS FROM THIS CHAPTER                        │
├─────────────────────────────────────────────────────────────────────────┤
│ Signal Strength: -30 to -50 excellent, -80 to -90 weak                  │
│ Channels 2.4GHz: Use 1, 6, 11 (non-overlapping)                         │
│ WPA3 > WPA2 > WPA > WEP > Open                                          │
│ BSSID = Router MAC Address                                              │
│ SSID = Network Name                                                     │
│ Frequency: 2.4GHz (range), 5GHz (speed)                                 │
└─────────────────────────────────────────────────────────────────────────┘

Real-world applications:
• Network troubleshooting
• WiFi site surveys
• Security auditing
• Channel optimization
• Penetration testing (reconnaissance)

Next Chapter 54 mein hum banayenge:
YouTube Downloader Bot - Complete automation with notifications!

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 54!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Signal strength closer to 0 is BETTER! -40 dBm is excellent, -90 dBm is poor!

> 💡 **Pro Tip #2:** Use channels 1, 6, or 11 for 2.4GHz networks - they don't overlap!

> 💡 **Pro Tip #3:** WPA3 is the current security standard - avoid WEP and WPA if possible!

> 💡 **Pro Tip #4:** 5GHz networks are faster but have shorter range - use for nearby devices!

> 💡 **Pro Tip #5:** Hidden networks (SSID not shown) are NOT more secure - security by obscurity doesn't work!

> 💡 **Pro Tip #6:** BSSID reveals the router manufacturer - first 3 octets (OUI) identify the vendor!

> 💡 **Pro Tip #7:** RSSI values are always negative - positive values indicate measurement errors!

> 💡 **Pro Tip #8:** Channel congestion kills WiFi speed - scan and switch to less crowded channels!

> 💡 **Pro Tip #9:** Open networks are dangerous - your traffic can be intercepted!

> 💡 **Pro Tip #10:** Use the continuous monitoring mode to track signal changes as you move around!

---

## 🔥 REAL WORLD USE CASES

### Real World Applications of WiFi Analyzer

**1. Network Troubleshooting**
- Diagnose slow WiFi issues
- Identify dead zones in coverage
- Find optimal router placement

**2. Security Auditing**
- Detect rogue access points
- Identify open networks in your area
- Assess encryption strength of networks

**3. Site Surveys**
- Plan WiFi deployment for buildings
- Map coverage areas
- Determine optimal channel allocation

**4. Performance Optimization**
- Find least congested channels
- Balance network load across channels
- Optimize router settings

**5. Penetration Testing**
- Reconnaissance phase for security testing
- Target identification
- Vulnerability assessment

**6. Smart Home Setup**
- Find best location for IoT devices
- Ensure coverage for all smart devices
- Avoid interference between devices

---

## ⚡ QUICK REFERENCE CARD

### WiFi Analyzer Quick Reference

| Field | Description | Good Values |
|-------|-------------|-------------|
| `ssid` | Network name | Shown if not hidden |
| `bssid` | Router MAC address | Format: AA:BB:CC:DD:EE:FF |
| `level` | Signal strength (dBm) | -30 to -67 (excellent/good) |
| `frequency` | Frequency in MHz | 2412-2484 (2.4GHz), 5170-5825 (5GHz) |
| `channel` | WiFi channel | 2.4GHz: 1,6,11 best |
| `capabilities` | Security info | WPA3 > WPA2 > WPA > Open |

### Signal Strength Guide

| dBm Range | Quality | Use Case |
|-----------|---------|----------|
| -30 to -50 | ⭐⭐⭐⭐⭐ Excellent | Gaming, 4K streaming |
| -50 to -60 | ⭐⭐⭐⭐ Very Good | HD video, video calls |
| -60 to -67 | ⭐⭐⭐ Good | Web browsing, email |
| -67 to -70 | ⭐⭐ Fair | Basic use, may buffer |
| -70 to -80 | ⭐ Weak | Connectivity issues |
| -80 to -90 | ❌ Very Weak | Unreliable |
| Below -90 | ❌ Unusable | No connection |

### Security Ratings

| Encryption | Rating | Recommendation |
|------------|--------|----------------|
| WPA3-PSK | ⭐⭐⭐⭐⭐ | Best - Use this! |
| WPA2-PSK (AES) | ⭐⭐⭐⭐ | Good - Widely supported |
| WPA2-PSK (TKIP) | ⭐⭐⭐ | Acceptable - Consider upgrading |
| WPA | ⭐⭐ | Weak - Upgrade recommended |
| WEP | ⭐ | Broken - Do not use! |
| Open | ❌ | None - Dangerous! |

---

## 🏆 BONUS CONTENT

### Bonus: Advanced WiFi Analysis Features

**Feature 1: Heat Map Generator**
```python
def generate_heat_map(locations, signals):
    """Create WiFi signal heat map"""
    # Plot signal strength on floor plan
    # Color-code by strength
    import matplotlib.pyplot as plt
    # Implementation...
```

**Feature 2: Channel Interference Calculator**
```python
def calculate_interference(networks, target_channel):
    """Calculate interference score for channel"""
    # Sum interference from overlapping channels
    # Return 0-100 interference score
    score = 0
    for net in networks:
        if abs(net['channel'] - target_channel) <= 4:
            score += net['signal_strength']
    return score
```

**Feature 3: Network Performance Predictor**
```python
def predict_performance(signal, channel_congestion):
    """Predict expected throughput"""
    # Based on signal and congestion
    # Return expected Mbps
```

**Feature 4: Rogue AP Detector**
```python
def detect_rogue_aps(known_networks, scanned_networks):
    """Detect unauthorized access points"""
    # Compare BSSIDs with known list
    # Alert on unknown networks with same SSID
```

**Feature 5: WiFi Speed Test Integration**
```python
def run_speed_test():
    """Test actual network speed"""
    import speedtest
    st = speedtest.Speedtest()
    return st.download(), st.upload()
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **WiFi Scanning Fundamentals** - How WiFi discovery works
- ✅ **Signal Strength Analysis** - Understanding dBm values and quality
- ✅ **Channel Analysis** - Overlapping channels and optimization
- ✅ **Security Assessment** - Encryption types and their effectiveness
- ✅ **Termux WiFi API** - Deep usage of termux-wifi-scaninfo
- ✅ **Rich Library** - Beautiful terminal output with tables and panels
- ✅ **Real-time Monitoring** - Continuous scanning mode
- ✅ **Report Generation** - Export findings to JSON/Text files

### Key Takeaways

1. **Signal strength is measured in dBm** - Closer to 0 is better
2. **2.4GHz has only 3 non-overlapping channels** - Use 1, 6, or 11
3. **5GHz offers more channels** - Less interference, shorter range
4. **WPA3 is the current standard** - Avoid legacy encryption
5. **Hidden SSIDs don't improve security** - Just obscurity

---

## 🚀 PROJECT EXTENSIONS

### 5+ Ideas to Extend This Project

**Extension 1: WiFi Heat Map Generator** ⭐⭐⭐⭐⭐
- Walk around with phone to collect signal data
- Generate visual heat map of coverage
- **Steps:** Use matplotlib, collect GPS/location data, plot on floor plan

**Extension 2: Automated Channel Optimizer** ⭐⭐⭐⭐
- Analyze all networks and suggest best channel
- Optionally configure router (with API support)
- **Steps:** Add router API integration, create recommendation engine

**Extension 3: Network Speed Dashboard** ⭐⭐⭐
- Combine WiFi analysis with speed tests
- Track performance over time
- **Steps:** Integrate speedtest-cli, add database storage

**Extension 4: Security Audit Report** ⭐⭐⭐⭐
- Comprehensive security assessment
- Compliance checking against standards
- **Steps:** Add security rules engine, generate PDF reports

**Extension 5: WiFi Deauth Detector** ⭐⭐⭐⭐⭐
- Detect deauthentication attacks
- Alert on suspicious activity
- **Steps:** Monitor for sudden disconnections, log anomalies

**Extension 6: Mesh Network Analyzer** ⭐⭐⭐⭐
- Analyze mesh network performance
- Optimize node placement
- **Steps:** Track multiple BSSIDs with same SSID, compare signals

---

## 🔧 CODE WALKTHROUGH

### WiFi Scanning Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    WIFI ANALYZER ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   ┌──────────────────────────────────────────────────────────────┐  │
│   │                    INPUT LAYER                                │  │
│   │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │  │
│   │  │ termux-wifi │  │ User CLI    │  │ Config      │          │  │
│   │  │ -scaninfo   │  │ Arguments   │  │ File        │          │  │
│   │  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘          │  │
│   └─────────┼────────────────┼────────────────┼──────────────────┘  │
│             │                │                │                      │
│             ▼                ▼                ▼                      │
│   ┌──────────────────────────────────────────────────────────────┐  │
│   │                    PROCESSING LAYER                           │  │
│   │                                                                │  │
│   │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │  │
│   │  │ JSON Parser │  │ Signal      │  │ Security    │          │  │
│   │  │             │  │ Analyzer    │  │ Assessor    │          │  │
│   │  └─────────────┘  └─────────────┘  └─────────────┘          │  │
│   │                                                                │  │
│   │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │  │
│   │  │ Channel     │  │ Network     │  │ Recommender │          │  │
│   │  │ Analyzer    │  │ Comparator  │  │ Engine      │          │  │
│   │  └─────────────┘  └─────────────┘  └─────────────┘          │  │
│   └──────────────────────────────────────────────────────────────┘  │
│                                │                                     │
│                                ▼                                     │
│   ┌──────────────────────────────────────────────────────────────┐  │
│   │                    OUTPUT LAYER                               │  │
│   │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │  │
│   │  │ Rich Tables │  │ JSON Report │  │ Text Report │          │  │
│   │  │ (Console)   │  │ (File)      │  │ (File)      │          │  │
│   │  └─────────────┘  └─────────────┘  └─────────────┘          │  │
│   └──────────────────────────────────────────────────────────────┘  │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Key Functions Explained

```python
def scan_networks():
    """
    Execute termux-wifi-scaninfo and return parsed results.
    
    Flow:
    1. Run termux-wifi-scaninfo command
    2. Capture JSON output
    3. Parse into Python list of dicts
    4. Sort by signal strength (strongest first)
    5. Return sorted list
    """

def analyze_security(capabilities):
    """
    Parse capabilities string to determine security level.
    
    Examples:
    - "[WPA2-PSK-CCMP][ESS]" → WPA2 Personal with AES
    - "[WPA3-PSK][ESS]" → WPA3 Personal
    - "[ESS]" → Open network (no security)
    
    Returns: (encryption_type, security_score, rating)
    """

def get_signal_quality(level):
    """
    Convert dBm level to quality rating.
    
    Input: -45 (dBm)
    Output: "Excellent" with color code
    
    Range:
    -30 to -50: Excellent
    -50 to -60: Very Good
    -60 to -67: Good
    -67 to -70: Fair
    -70 to -80: Weak
    Below -80: Very Weak
    """
```

---

## 📦 DEPLOYMENT GUIDE

### How to Deploy and Share This Project

**1. Create Project Package**
```bash
mkdir -p ~/wifi-analyzer
cd ~/wifi-analyzer
# Copy wifi_analyzer.py
```

**2. Create requirements.txt**
```
rich>=13.0.0
```

**3. Create Installation Script**
```bash
cat > install.sh << 'EOF'
#!/bin/bash
pkg install python termux-api -y
pip install rich
echo "WiFi Analyzer installed!"
echo "Run: python wifi_analyzer.py"
EOF
chmod +x install.sh
```

**4. GitHub Deployment**
```bash
git init
git add wifi_analyzer.py requirements.txt install.sh README.md
git commit -m "WiFi Analyzer - Complete network scanning tool"
git branch -M main
git remote add origin https://github.com/USERNAME/wifi-analyzer.git
git push -u origin main
```

**5. Create Alias for Easy Access**
```bash
echo 'alias wifi-scan="python ~/wifi-analyzer/wifi_analyzer.py"' >> ~/.bashrc
source ~/.bashrc
# Now just type: wifi-scan
```

---

## 🔗 RELATED CHAPTERS

### Cross-Reference to Related Chapters

| Chapter | Topic | Connection |
|---------|-------|------------|
| **Ch52** | Phone Info Extractor | Similar Termux API usage |
| **Ch55** | Port Scanner | Network security tools |
| **Ch50** | Termux API Deep Dive | API commands reference |
| **Ch61** | Security Best Practices | WiFi security context |
| **Ch49** | Bash Scripting | Alternative implementation |

### Prerequisite Chapters
- 📖 **Ch47: Python Basics** - Python fundamentals
- 📖 **Ch50: Termux API** - Understanding Termux APIs
- 📖 **Ch48: Advanced Python** - Rich library basics

### Next Steps
- ➡️ **Ch54: YouTube Downloader** - Media automation
- ➡️ **Ch55: Port Scanner** - Network scanning

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your WiFi Analyzer Knowledge!

**Question 1:** What does dBm measure?
- a) Data transfer rate
- b) Signal strength ✓
- c) Bandwidth
- d) Latency

**Question 2:** Which signal strength is considered "Excellent"?
- a) -90 dBm
- b) -70 dBm
- c) -45 dBm ✓
- d) -100 dBm

**Question 3:** Which channels don't overlap in 2.4GHz band?
- a) 1, 2, 3
- b) 1, 6, 11 ✓
- c) 1, 5, 9
- d) 3, 6, 9

**Question 4:** What does BSSID represent?
- a) Network name
- b) Router MAC address ✓
- c) IP address
- d) Security key

**Question 5:** Which encryption is the most secure?
- a) WEP
- b) WPA
- c) WPA2
- d) WPA3 ✓

**Question 6:** What is the range of 5GHz WiFi compared to 2.4GHz?
- a) Longer range
- b) Shorter range ✓
- c) Same range
- d) No range limit

**Question 7:** What does SSID stand for?
- a) Secure Service ID
- b) Service Set Identifier ✓
- c) Signal Strength ID
- d) Security System ID

**Question 8:** Which Termux command scans for WiFi networks?
- a) termux-wifi-scan
- b) termux-wifi-scaninfo ✓
- c) termux-wifi-list
- d) termux-scan-wifi

**Question 9:** What indicates an open network in capabilities?
- a) [WPA2]
- b) [OPEN]
- c) [ESS] only ✓
- d) [PUBLIC]

**Question 10:** What is channel congestion?
- a) Too many devices on one channel
- b) Multiple networks on overlapping channels ✓
- c) Router hardware issue
- d) ISP problem

**Question 11:** Which frequency band has more non-overlapping channels?
- a) 2.4 GHz
- b) 5 GHz ✓
- c) Both same
- d) Depends on router

**Question 12:** Why should hidden networks not be considered secure?
- a) They use weak encryption
- b) SSID is still transmitted in some frames ✓
- c) They're easier to hack
- d) They have shorter range

---

### Extend the Project Challenges

**Challenge 1:** Add signal strength graph over time
```python
# Hint: Store readings and plot with matplotlib
def plot_signal_history(network_name, readings):
    # X-axis: Time
    # Y-axis: Signal strength (dBm)
    # Show trend over time
```

**Challenge 2:** Implement network change detection
```python
# Detect when networks appear/disappear
def detect_changes(previous_scan, current_scan):
    # Compare BSSIDs
    # Alert on new networks
    # Note disappeared networks
```

**Challenge 3:** Add GPS coordinate logging
```python
# Store location with each scan
def log_with_location(networks):
    # Get GPS coordinates
    # Create geo-tagged report
```

### Bug Fixing Exercises

**Bug 1:** Signal strength shows as 0
```python
level = network.get('level', 0)  # Wrong default!
```
*Fix: Use `None` as default and handle missing values*

**Bug 2:** Channel calculation wrong for 5GHz
```python
channel = frequency - 2407  # Only works for 2.4GHz!
```
*Fix: Check frequency band and use correct formula*

**Bug 3:** Security parsing fails on complex capabilities
```python
if 'WPA3' in capabilities:
    security = 'WPA3'
elif 'WPA2' in capabilities:  # This never runs if WPA3 is present!
```
*Fix: Parse all security types and show all supported*

---

## 📖 TECHNICAL GUIDE

### 1. WiFi Scanning Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    WIFI SCANNING ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Python Application                            │   │
│   │                   (wifi_analyzer.py)                             │   │
│   │                                                                  │   │
│   │   ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐          │   │
│   │   │ Scanner  │ │ Analyzer │ │ Display  │ │ Report   │          │   │
│   │   │ Module   │ │ Module   │ │ Module   │ │ Module   │          │   │
│   │   └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘          │   │
│   │        │            │            │            │                  │   │
│   └────────┼────────────┼────────────┼────────────┼──────────────────┘   │
│            │            │            │            │                       │
│            │ subprocess │            │ Rich       │ file write            │
│            ▼            │            ▼            ▼                       │
│   ┌─────────────────────┴────────────────────────────────────────────┐   │
│   │                    Termux:API App                                │   │
│   │                                                                  │   │
│   │   termux-wifi-scaninfo  →  Android WifiManager.scan()           │   │
│   │   termux-wifi-connectioninfo  →  WifiInfo                       │   │
│   │                                                                  │   │
│   └─────────────────────────────┬────────────────────────────────────┘   │
│                                 │                                        │
│                                 │ Android APIs                           │
│                                 ▼                                        │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android System                                │   │
│   │                                                                  │   │
│   │   WifiManager → ScanResults → List<ScanResult>                  │   │
│   │                                                                  │   │
│   │   Each ScanResult contains:                                      │   │
│   │   • SSID (network name)                                          │   │
│   │   • BSSID (MAC address)                                          │   │
│   │   • level (signal strength in dBm)                               │   │
│   │   • frequency (in MHz)                                           │   │
│   │   • capabilities (security info)                                 │   │
│   │   • channelWidth                                                 │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. WiFi Scan Data Structure

```json
{
  "bssid": "AA:BB:CC:DD:EE:FF",
  "frequency": 2437,
  "channel": 6,
  "level": -45,
  "timestamp": 1699876543210,
  "ssid": "MyWiFi",
  "capabilities": "[WPA2-PSK-CCMP][ESS]",
  "centerFreq0": 0,
  "centerFreq1": 0,
  "channelWidth": 0
}
```

### 3. Frequency to Channel Mapping

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    FREQUENCY TO CHANNEL MAPPING                          │
├─────────────────────┬────────────────────┬──────────────────────────────┤
│ Band                │ Frequency (MHz)    │ Channel                      │
├─────────────────────┼────────────────────┼──────────────────────────────┤
│ 2.4 GHz             │ 2412               │ 1                            │
│ 2.4 GHz             │ 2417               │ 2                            │
│ 2.4 GHz             │ 2422               │ 3                            │
│ 2.4 GHz             │ 2427               │ 4                            │
│ 2.4 GHz             │ 2432               │ 5                            │
│ 2.4 GHz             │ 2437               │ 6                            │
│ 2.4 GHz             │ 2442               │ 7                            │
│ 2.4 GHz             │ 2447               │ 8                            │
│ 2.4 GHz             │ 2452               │ 9                            │
│ 2.4 GHz             │ 2457               │ 10                           │
│ 2.4 GHz             │ 2462               │ 11                           │
│ 2.4 GHz             │ 2467               │ 12                           │
│ 2.4 GHz             │ 2472               │ 13                           │
│ 2.4 GHz             │ 2484               │ 14 (Japan only)              │
├─────────────────────┼────────────────────┼──────────────────────────────┤
│ 5 GHz               │ 5180               │ 36                           │
│ 5 GHz               │ 5200               │ 40                           │
│ 5 GHz               │ 5220               │ 44                           │
│ 5 GHz               │ 5240               │ 48                           │
│ 5 GHz               │ 5260               │ 52 (DFS)                     │
│ 5 GHz               │ 5280               │ 56 (DFS)                     │
│ 5 GHz               │ 5300               │ 60 (DFS)                     │
│ 5 GHz               │ 5320               │ 64 (DFS)                     │
│ 5 GHz               │ 5500               │ 100 (DFS)                    │
│ 5 GHz               │ 5745               │ 149                          │
│ 5 GHz               │ 5765               │ 153                          │
│ 5 GHz               │ 5785               │ 157                          │
│ 5 GHz               │ 5805               │ 161                          │
│ 5 GHz               │ 5825               │ 165                          │
└─────────────────────┴────────────────────┴──────────────────────────────┘
```

### 4. Capabilities String Parsing

```
Common Patterns:

[WPA2-PSK-CCMP][ESS]
├── WPA2: Protocol version
├── PSK: Pre-Shared Key (personal)
├── CCMP: AES encryption cipher
└── ESS: Extended Service Set (infrastructure)

[WPA2-PSK-CCMP+TKIP][ESS]
├── CCMP+TKIP: Mixed mode (supports both)
└── Less secure than pure CCMP

[WPA3-PSK][ESS]
├── WPA3: Latest protocol
└── Best security for personal use

[WPA2-EAP-CCMP][ESS]
├── EAP: Enterprise authentication
└── Used in corporate networks

[ESS]
└── No security - Open network!
```

---

## 💻 COMPLETE SOURCE CODE

### File: wifi_analyzer.py

```python
#!/usr/bin/env python3
"""
WiFi Analyzer - Complete Network Analysis Tool
Created for Termux Full Course by T3rmuxk1ng

Features:
- Scan nearby WiFi networks
- Analyze signal strength and quality
- Security assessment
- Channel congestion analysis
- Continuous monitoring
- Report generation
"""

import subprocess
import json
import os
import sys
import time
from datetime import datetime
from typing import List, Dict, Optional, Tuple

# Rich library for beautiful output
try:
    from rich.console import Console
    from rich.table import Table
    from rich.panel import Panel
    from rich.progress import Progress, SpinnerColumn, TextColumn
    from rich.prompt import Prompt, IntPrompt
    from rich import print as rprint
    RICH_AVAILABLE = True
except ImportError:
    RICH_AVAILABLE = False
    print("Note: Install 'rich' for better output: pip install rich")

# Initialize console
console = Console() if RICH_AVAILABLE else None

# Configuration
REPORTS_DIR = os.path.expanduser("~/wifi-analyzer/reports")
os.makedirs(REPORTS_DIR, exist_ok=True)


class WiFiScanner:
    """WiFi Scanner class - handles all scanning operations"""
    
    def __init__(self):
        self.networks = []
        self.last_scan_time = None
        self.scan_error = None
    
    def scan_networks(self) -> List[Dict]:
        """
        Scan nearby WiFi networks using termux-wifi-scaninfo
        
        Returns:
            List of network dictionaries
        """
        try:
            # Run termux-wifi-scaninfo command
            result = subprocess.run(
                ['termux-wifi-scaninfo'],
                capture_output=True,
                text=True,
                timeout=30
            )
            
            if result.returncode != 0:
                self.scan_error = f"Scan failed: {result.stderr}"
                return []
            
            # Parse JSON output
            self.networks = json.loads(result.stdout)
            self.last_scan_time = datetime.now()
            self.scan_error = None
            
            # Sort by signal strength (strongest first)
            self.networks.sort(key=lambda x: x.get('level', -100), reverse=True)
            
            return self.networks
            
        except subprocess.TimeoutExpired:
            self.scan_error = "Scan timeout - please try again"
            return []
        except json.JSONDecodeError as e:
            self.scan_error = f"JSON parse error: {e}"
            return []
        except FileNotFoundError:
            self.scan_error = "termux-api not installed. Run: pkg install termux-api"
            return []
        except Exception as e:
            self.scan_error = f"Unexpected error: {e}"
            return []
    
    def get_connection_info(self) -> Optional[Dict]:
        """
        Get current WiFi connection information
        
        Returns:
            Connection info dictionary or None
        """
        try:
            result = subprocess.run(
                ['termux-wifi-connectioninfo'],
                capture_output=True,
                text=True,
                timeout=10
            )
            
            if result.returncode == 0 and result.stdout.strip():
                return json.loads(result.stdout)
            return None
            
        except Exception:
            return None


class WiFiAnalyzer:
    """WiFi Analyzer class - handles all analysis operations"""
    
    # Signal strength thresholds
    SIGNAL_THRESHOLDS = {
        'excellent': -50,
        'very_good': -60,
        'good': -67,
        'fair': -70,
        'weak': -80,
        'very_weak': -90
    }
    
    # Frequency to channel mapping
    FREQ_TO_CHANNEL = {
        # 2.4 GHz band
        2412: 1, 2417: 2, 2422: 3, 2427: 4, 2432: 5,
        2437: 6, 2442: 7, 2447: 8, 2452: 9, 2457: 10,
        2462: 11, 2467: 12, 2472: 13, 2484: 14,
        # 5 GHz band
        5180: 36, 5200: 40, 5220: 44, 5240: 48,
        5260: 52, 5280: 56, 5300: 60, 5320: 64,
        5500: 100, 5520: 104, 5540: 108, 5560: 112,
        5580: 116, 5600: 120, 5620: 124, 5640: 128,
        5660: 132, 5680: 136, 5700: 140, 5720: 144,
        5745: 149, 5765: 153, 5785: 157, 5805: 161, 5825: 165
    }
    
    @classmethod
    def get_signal_quality(cls, level: int) -> Tuple[str, str, str]:
        """
        Get signal quality assessment
        
        Args:
            level: Signal level in dBm
            
        Returns:
            Tuple of (quality_text, rating_stars, color)
        """
        if level >= cls.SIGNAL_THRESHOLDS['excellent']:
            return ("Excellent", "⭐⭐⭐⭐⭐", "green")
        elif level >= cls.SIGNAL_THRESHOLDS['very_good']:
            return ("Very Good", "⭐⭐⭐⭐", "green")
        elif level >= cls.SIGNAL_THRESHOLDS['good']:
            return ("Good", "⭐⭐⭐", "yellow")
        elif level >= cls.SIGNAL_THRESHOLDS['fair']:
            return ("Fair", "⭐⭐", "yellow")
        elif level >= cls.SIGNAL_THRESHOLDS['weak']:
            return ("Weak", "⭐", "red")
        else:
            return ("Very Weak", "❌", "red")
    
    @classmethod
    def get_channel_from_freq(cls, frequency: int) -> int:
        """
        Convert frequency to channel number
        
        Args:
            frequency: Frequency in MHz
            
        Returns:
            Channel number
        """
        return cls.FREQ_TO_CHANNEL.get(frequency, 0)
    
    @classmethod
    def get_band(cls, frequency: int) -> str:
        """
        Determine WiFi band from frequency
        
        Args:
            frequency: Frequency in MHz
            
        Returns:
            Band string (2.4GHz or 5GHz)
        """
        if 2412 <= frequency <= 2484:
            return "2.4GHz"
        elif 5170 <= frequency <= 5825:
            return "5GHz"
        else:
            return "Unknown"
    
    @classmethod
    def parse_capabilities(cls, capabilities: str) -> Dict:
        """
        Parse capabilities string to extract security information
        
        Args:
            capabilities: Capabilities string from scan result
            
        Returns:
            Dictionary with security details
        """
        result = {
            'protocol': 'Unknown',
            'encryption': 'Unknown',
            'authentication': 'Unknown',
            'is_secure': False,
            'security_rating': 0,
            'security_emoji': '❓'
        }
        
        if not capabilities:
            result['protocol'] = 'Open'
            result['encryption'] = 'None'
            result['authentication'] = 'None'
            result['is_secure'] = False
            result['security_rating'] = 0
            result['security_emoji'] = '⚠️'
            return result
        
        caps_lower = capabilities.lower()
        
        # Check for WPA3
        if 'wpa3' in caps_lower:
            result['protocol'] = 'WPA3'
            result['is_secure'] = True
            result['security_rating'] = 5
            result['security_emoji'] = '🔒'
            if 'psk' in caps_lower:
                result['authentication'] = 'PSK (Personal)'
            elif 'eap' in caps_lower or 'enterprise' in caps_lower:
                result['authentication'] = 'Enterprise'
            else:
                result['authentication'] = 'Personal'
                
        # Check for WPA2
        elif 'wpa2' in caps_lower:
            result['protocol'] = 'WPA2'
            result['is_secure'] = True
            result['security_rating'] = 4
            result['security_emoji'] = '✅'
            if 'psk' in caps_lower:
                result['authentication'] = 'PSK (Personal)'
            elif 'eap' in caps_lower:
                result['authentication'] = 'Enterprise'
                result['security_rating'] = 4.5
            else:
                result['authentication'] = 'Personal'
                
        # Check for WPA
        elif 'wpa' in caps_lower and 'wpa2' not in caps_lower:
            result['protocol'] = 'WPA'
            result['is_secure'] = True  # Technically yes, but weak
            result['security_rating'] = 2
            result['security_emoji'] = '⚠️'
            result['authentication'] = 'PSK'
            
        # Check for WEP (deprecated)
        elif 'wep' in caps_lower:
            result['protocol'] = 'WEP'
            result['is_secure'] = False
            result['security_rating'] = 1
            result['security_emoji'] = '❌'
            result['authentication'] = 'Shared Key'
            
        # Open network
        elif 'ess' in caps_lower and 'wpa' not in caps_lower:
            result['protocol'] = 'Open'
            result['encryption'] = 'None'
            result['authentication'] = 'None'
            result['is_secure'] = False
            result['security_rating'] = 0
            result['security_emoji'] = '⚠️'
            return result
        
        # Determine encryption cipher
        if 'ccmp' in caps_lower:
            result['encryption'] = 'AES (CCMP)'
        elif 'tkip' in caps_lower:
            result['encryption'] = 'TKIP'
        elif 'ccmp' in caps_lower and 'tkip' in caps_lower:
            result['encryption'] = 'AES/TKIP (Mixed)'
        
        return result
    
    @classmethod
    def analyze_channel_congestion(cls, networks: List[Dict]) -> Dict:
        """
        Analyze channel congestion across all networks
        
        Args:
            networks: List of network dictionaries
            
        Returns:
            Dictionary with channel analysis
        """
        channel_stats = {}
        
        for network in networks:
            freq = network.get('frequency', 0)
            channel = cls.get_channel_from_freq(freq)
            band = cls.get_band(freq)
            
            if channel == 0:
                continue
                
            key = f"{channel}_{band}"
            if key not in channel_stats:
                channel_stats[key] = {
                    'channel': channel,
                    'band': band,
                    'count': 0,
                    'networks': [],
                    'avg_signal': 0,
                    'signals': []
                }
            
            channel_stats[key]['count'] += 1
            channel_stats[key]['networks'].append(network.get('ssid', 'Hidden'))
            channel_stats[key]['signals'].append(network.get('level', -100))
        
        # Calculate averages and congestion
        for key in channel_stats:
            signals = channel_stats[key]['signals']
            channel_stats[key]['avg_signal'] = sum(signals) / len(signals) if signals else -100
            
            # Congestion level
            count = channel_stats[key]['count']
            if count >= 4:
                channel_stats[key]['congestion'] = 'High'
            elif count >= 2:
                channel_stats[key]['congestion'] = 'Medium'
            else:
                channel_stats[key]['congestion'] = 'Low'
        
        return channel_stats
    
    @classmethod
    def get_best_channel_recommendation(cls, networks: List[Dict]) -> Dict:
        """
        Recommend the best channel for 2.4GHz and 5GHz bands
        
        Args:
            networks: List of network dictionaries
            
        Returns:
            Dictionary with recommendations
        """
        channel_analysis = cls.analyze_channel_congestion(networks)
        
        # Default recommendations (non-overlapping channels)
        best_24ghz = {'channel': 1, 'reason': 'Default - no networks found'}
        best_5ghz = {'channel': 36, 'reason': 'Default - no networks found'}
        
        # Analyze 2.4GHz
        channels_24ghz = {1: 0, 6: 0, 11: 0}  # Non-overlapping channels
        
        for key, stats in channel_analysis.items():
            if stats['band'] == '2.4GHz':
                ch = stats['channel']
                # Map to nearest non-overlapping channel
                if ch in [1, 2, 3]:
                    channels_24ghz[1] += stats['count']
                elif ch in [4, 5, 6, 7, 8]:
                    channels_24ghz[6] += stats['count']
                elif ch in [9, 10, 11, 12, 13]:
                    channels_24ghz[11] += stats['count']
        
        # Find least congested
        min_count = min(channels_24ghz.values())
        for ch, count in channels_24ghz.items():
            if count == min_count:
                best_24ghz = {
                    'channel': ch,
                    'networks_on_channel': count,
                    'reason': f'Least congested (only {count} nearby networks)'
                }
                break
        
        # Analyze 5GHz
        channels_5ghz = {}
        for key, stats in channel_analysis.items():
            if stats['band'] == '5GHz':
                ch = stats['channel']
                channels_5ghz[ch] = stats['count']
        
        if channels_5ghz:
            # Find least congested 5GHz channel
            min_ch = min(channels_5ghz, key=channels_5ghz.get)
            best_5ghz = {
                'channel': min_ch,
                'networks_on_channel': channels_5ghz[min_ch],
                'reason': f'Least congested 5GHz channel'
            }
        
        return {
            '2.4GHz': best_24ghz,
            '5GHz': best_5ghz
        }


class WiFiDisplay:
    """Display class - handles all output formatting"""
    
    @staticmethod
    def display_header():
        """Display application header"""
        if RICH_AVAILABLE and console:
            console.clear()
            header = Panel.fit(
                "[bold cyan]📡 WiFi ANALYZER[/bold cyan]\n"
                "[dim]Complete Network Analysis Tool | T3rmuxk1ng[/dim]",
                border_style="cyan"
            )
            console.print(header)
        else:
            print("\n" + "="*60)
            print("📡 WIFI ANALYZER")
            print("Complete Network Analysis Tool | T3rmuxk1ng")
            print("="*60 + "\n")
    
    @staticmethod
    def display_networks_table(networks: List[Dict]):
        """
        Display networks in a formatted table
        
        Args:
            networks: List of network dictionaries
        """
        if not networks:
            if RICH_AVAILABLE and console:
                console.print("[yellow]No networks found![/yellow]")
            else:
                print("No networks found!")
            return
        
        if RICH_AVAILABLE and console:
            table = Table(
                title=f"[bold]Found {len(networks)} Networks[/bold]",
                show_header=True,
                header_style="bold cyan",
                border_style="blue"
            )
            
            table.add_column("#", style="dim", width=3)
            table.add_column("SSID", width=20)
            table.add_column("Signal", width=15)
            table.add_column("Channel", width=10)
            table.add_column("Band", width=8)
            table.add_column("Security", width=15)
            table.add_column("BSSID", width=18)
            
            for idx, network in enumerate(networks, 1):
                ssid = network.get('ssid', '[Hidden]')
                level = network.get('level', -100)
                freq = network.get('frequency', 0)
                bssid = network.get('bssid', 'Unknown')
                
                # Get analysis data
                quality, stars, color = WiFiAnalyzer.get_signal_quality(level)
                channel = WiFiAnalyzer.get_channel_from_freq(freq)
                band = WiFiAnalyzer.get_band(freq)
                security = WiFiAnalyzer.parse_capabilities(network.get('capabilities', ''))
                
                # Format signal display
                signal_display = f"{level} dBm\n[{color}]{quality}[/{color}]"
                
                # Format security display
                security_display = f"{security['protocol']} {security['security_emoji']}"
                
                table.add_row(
                    str(idx),
                    ssid[:20],
                    f"{level} dBm [{color}]{quality}[/{color}]",
                    str(channel),
                    band,
                    security_display,
                    bssid
                )
            
            console.print(table)
            
        else:
            # Fallback for non-rich display
            print(f"\nFound {len(networks)} Networks:")
            print("-" * 100)
            print(f"{'#':<3} {'SSID':<20} {'Signal':<15} {'Ch':<5} {'Band':<8} {'Security':<15}")
            print("-" * 100)
            
            for idx, network in enumerate(networks, 1):
                ssid = network.get('ssid', '[Hidden]')[:20]
                level = network.get('level', -100)
                freq = network.get('frequency', 0)
                
                quality, _, _ = WiFiAnalyzer.get_signal_quality(level)
                channel = WiFiAnalyzer.get_channel_from_freq(freq)
                band = WiFiAnalyzer.get_band(freq)
                security = WiFiAnalyzer.parse_capabilities(network.get('capabilities', ''))
                
                print(f"{idx:<3} {ssid:<20} {level} dBm ({quality})".ljust(40) + 
                      f"{channel:<5} {band:<8} {security['protocol']} {security['security_emoji']}")
            print("-" * 100)
    
    @staticmethod
    def display_network_detail(network: Dict, index: int):
        """
        Display detailed information for a single network
        
        Args:
            network: Network dictionary
            index: Network index number
        """
        ssid = network.get('ssid', '[Hidden Network]')
        level = network.get('level', -100)
        freq = network.get('frequency', 0)
        bssid = network.get('bssid', 'Unknown')
        capabilities = network.get('capabilities', '')
        
        # Get analysis
        quality, stars, color = WiFiAnalyzer.get_signal_quality(level)
        channel = WiFiAnalyzer.get_channel_from_freq(freq)
        band = WiFiAnalyzer.get_band(freq)
        security = WiFiAnalyzer.parse_capabilities(capabilities)
        
        if RICH_AVAILABLE and console:
            # Main info panel
            info_text = f"""
[bold]Network #{index}[/bold]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[bold cyan]BASIC INFORMATION[/bold cyan]
  SSID:          {ssid}
  BSSID:         {bssid}
  Channel:       {channel}
  Band:          {band}
  Frequency:     {freq} MHz

[bold cyan]SIGNAL ANALYSIS[/bold cyan]
  Signal Level:  {level} dBm
  Quality:       [{color}]{quality}[/{color}] {stars}
  Range:         {WiFiDisplay._estimate_distance(level)}

[bold cyan]SECURITY ANALYSIS[/bold cyan]
  Protocol:      {security['protocol']} {security['security_emoji']}
  Encryption:    {security['encryption']}
  Authentication: {security['authentication']}
  Secure:        {'✅ Yes' if security['is_secure'] else '❌ No'}
  Rating:        {security['security_rating']}/5

[bold cyan]CAPABILITIES STRING[/bold cyan]
  {capabilities if capabilities else 'N/A'}
"""
            console.print(Panel(info_text, title=f"[bold]{ssid}[/bold]", border_style="cyan"))
            
            # Security recommendations
            if not security['is_secure'] or security['security_rating'] < 3:
                rec_text = ""
                if security['protocol'] == 'Open':
                    rec_text = "⚠️ [bold red]WARNING:[/bold red] This network has NO encryption!\n" \
                              "   All your data is visible to anyone on the network.\n" \
                              "   Avoid accessing sensitive information."
                elif security['protocol'] in ['WEP', 'WPA']:
                    rec_text = "⚠️ [bold yellow]CAUTION:[/bold yellow] This network uses outdated encryption.\n" \
                              f"   {security['protocol']} has known vulnerabilities.\n" \
                              "   Upgrade to WPA2 or WPA3 recommended."
                
                if rec_text:
                    console.print(Panel(rec_text, title="Security Recommendations", border_style="yellow"))
            
            # Signal recommendations
            if level < -70:
                signal_rec = f"📡 [bold]Signal Tips:[/bold]\n" \
                            f"   Signal is {quality}. Consider:\n" \
                            "   • Moving closer to the access point\n" \
                            "   • Removing obstacles between you and router\n" \
                            "   • Checking for interference from other devices"
                console.print(Panel(signal_rec, border_style="blue"))
                
        else:
            print(f"\n{'='*60}")
            print(f"Network #{index}: {ssid}")
            print(f"{'='*60}")
            print(f"BSSID:         {bssid}")
            print(f"Channel:       {channel} ({band})")
            print(f"Frequency:     {freq} MHz")
            print(f"Signal:        {level} dBm ({quality})")
            print(f"Security:      {security['protocol']} {security['security_emoji']}")
            print(f"Encryption:    {security['encryption']}")
            print(f"{'='*60}\n")
    
    @staticmethod
    def _estimate_distance(level: int) -> str:
        """Estimate distance based on signal level"""
        if level >= -50:
            return "Very close (1-5 meters)"
        elif level >= -60:
            return "Near (5-10 meters)"
        elif level >= -67:
            return "Same room (10-15 meters)"
        elif level >= -70:
            return "Nearby room (15-20 meters)"
        elif level >= -80:
            return "Far (20-30 meters)"
        else:
            return "Very far (>30 meters)"
    
    @staticmethod
    def display_analysis_summary(networks: List[Dict]):
        """
        Display analysis summary for all networks
        
        Args:
            networks: List of network dictionaries
        """
        if not networks:
            return
        
        # Find best and worst
        strongest = max(networks, key=lambda x: x.get('level', -100))
        weakest = min(networks, key=lambda x: x.get('level', -100))
        
        # Security analysis
        open_networks = [n for n in networks if 
                        WiFiAnalyzer.parse_capabilities(n.get('capabilities', '')).get('protocol') == 'Open']
        wpa3_networks = [n for n in networks if 
                        'wpa3' in n.get('capabilities', '').lower()]
        insecure_networks = [n for n in networks if 
                            WiFiAnalyzer.parse_capabilities(n.get('capabilities', '')).get('security_rating', 0) < 3]
        
        # Channel analysis
        channel_analysis = WiFiAnalyzer.analyze_channel_congestion(networks)
        channel_recommendations = WiFiAnalyzer.get_best_channel_recommendation(networks)
        
        if RICH_AVAILABLE and console:
            summary_text = f"""
[bold cyan]NETWORK STATISTICS[/bold cyan]
  Total Networks Found:    {len(networks)}
  
[bold cyan]SIGNAL ANALYSIS[/bold cyan]
  Strongest Signal:        {strongest.get('ssid', 'Hidden')} ({strongest.get('level', 'N/A')} dBm)
  Weakest Signal:          {weakest.get('ssid', 'Hidden')} ({weakest.get('level', 'N/A')} dBm)

[bold cyan]SECURITY OVERVIEW[/bold cyan]
  Open Networks:           {len(open_networks)} {'⚠️ WARNING' if open_networks else '✅'}
  WPA3 Networks:           {len(wpa3_networks)} {'🔒 Secure' if wpa3_networks else ''}
  Insecure Networks:       {len(insecure_networks)} {'⚠️' if insecure_networks else '✅'}

[bold cyan]CHANNEL RECOMMENDATIONS[/bold cyan]
  Best 2.4GHz Channel:     {channel_recommendations['2.4GHz']['channel']} ({channel_recommendations['2.4GHz']['reason']})
  Best 5GHz Channel:       {channel_recommendations['5GHz']['channel']} ({channel_recommendations['5GHz']['reason']})
"""
            console.print(Panel(summary_text, title="[bold]📊 Analysis Summary[/bold]", border_style="green"))
            
            # Security warnings
            if open_networks:
                warning = f"⚠️ [bold red]SECURITY ALERT:[/bold red] {len(open_networks)} open network(s) detected!\n" \
                         "Open networks transmit data without encryption.\n" \
                         "Never access sensitive information on open networks."
                console.print(Panel(warning, border_style="red"))
            
            # Channel congestion warning
            high_congestion = [k for k, v in channel_analysis.items() if v.get('congestion') == 'High']
            if high_congestion:
                congest_text = "📡 [bold yellow]Channel Congestion Detected:[/bold yellow]\n"
                for key in high_congestion[:3]:
                    stats = channel_analysis[key]
                    congest_text += f"   Channel {stats['channel']} ({stats['band']}): {stats['count']} networks\n"
                console.print(Panel(congest_text, border_style="yellow"))
                
        else:
            print("\n📊 ANALYSIS SUMMARY")
            print("-" * 40)
            print(f"Total Networks: {len(networks)}")
            print(f"Strongest: {strongest.get('ssid', 'Hidden')} ({strongest.get('level', 'N/A')} dBm)")
            print(f"Open Networks: {len(open_networks)}")
            print(f"Best 2.4GHz Channel: {channel_recommendations['2.4GHz']['channel']}")
            print("-" * 40)
    
    @staticmethod
    def display_continuous_monitor(scanner: WiFiScanner, interval: int = 5):
        """
        Display continuous monitoring mode
        
        Args:
            scanner: WiFiScanner instance
            interval: Update interval in seconds
        """
        signal_history = {}  # Track signal history for each network
        
        try:
            while True:
                # Clear and show header
                WiFiDisplay.display_header()
                
                if RICH_AVAILABLE and console:
                    console.print(f"[dim]Refreshing every {interval} seconds... (Ctrl+C to stop)[/dim]\n")
                else:
                    print(f"Refreshing every {interval} seconds... (Ctrl+C to stop)\n")
                
                # Scan networks
                networks = scanner.scan_networks()
                
                if not networks:
                    if RICH_AVAILABLE and console:
                        console.print(f"[red]Scan error: {scanner.scan_error}[/red]")
                    else:
                        print(f"Scan error: {scanner.scan_error}")
                    time.sleep(interval)
                    continue
                
                # Update signal history and show trends
                for network in networks:
                    ssid = network.get('ssid', '[Hidden]')
                    level = network.get('level', -100)
                    
                    if ssid not in signal_history:
                        signal_history[ssid] = []
                    signal_history[ssid].append(level)
                    
                    # Keep last 10 readings
                    if len(signal_history[ssid]) > 10:
                        signal_history[ssid] = signal_history[ssid][-10:]
                
                # Display networks
                WiFiDisplay.display_networks_table(networks)
                
                # Show signal trends
                if RICH_AVAILABLE and console:
                    console.print("\n[bold]Signal Trends:[/bold]")
                    for ssid, history in list(signal_history.items())[:5]:  # Show top 5
                        if len(history) >= 2:
                            trend = history[-1] - history[-2]
                            if trend > 2:
                                trend_str = f"[green]↑ Improving (+{trend} dBm)[/green]"
                            elif trend < -2:
                                trend_str = f"[red]↓ Declining ({trend} dBm)[/red]"
                            else:
                                trend_str = "[yellow]→ Stable[/yellow]"
                            console.print(f"  {ssid}: {trend_str}")
                
                # Show timestamp
                if RICH_AVAILABLE and console:
                    console.print(f"\n[dim]Last update: {datetime.now().strftime('%H:%M:%S')}[/dim]")
                else:
                    print(f"\nLast update: {datetime.now().strftime('%H:%M:%S')}")
                
                time.sleep(interval)
                
        except KeyboardInterrupt:
            if RICH_AVAILABLE and console:
                console.print("\n[yellow]Monitoring stopped by user.[/yellow]")
            else:
                print("\nMonitoring stopped by user.")


class WiFiReport:
    """Report class - handles report generation"""
    
    @staticmethod
    def generate_json_report(networks: List[Dict], scanner: WiFiScanner) -> str:
        """
        Generate JSON report
        
        Args:
            networks: List of network dictionaries
            scanner: WiFiScanner instance
            
        Returns:
            Path to generated report file
        """
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        filename = f"wifi_report_{timestamp}.json"
        filepath = os.path.join(REPORTS_DIR, filename)
        
        # Analyze networks
        analyzed_networks = []
        for network in networks:
            analysis = {
                **network,
                'analysis': {
                    'signal_quality': WiFiAnalyzer.get_signal_quality(network.get('level', -100)),
                    'channel': WiFiAnalyzer.get_channel_from_freq(network.get('frequency', 0)),
                    'band': WiFiAnalyzer.get_band(network.get('frequency', 0)),
                    'security': WiFiAnalyzer.parse_capabilities(network.get('capabilities', ''))
                }
            }
            analyzed_networks.append(analysis)
        
        report_data = {
            'scan_time': scanner.last_scan_time.isoformat() if scanner.last_scan_time else None,
            'total_networks': len(networks),
            'networks': analyzed_networks,
            'analysis': {
                'strongest_signal': max(networks, key=lambda x: x.get('level', -100)).get('ssid', 'Hidden') if networks else None,
                'channel_recommendations': WiFiAnalyzer.get_best_channel_recommendation(networks),
                'channel_congestion': WiFiAnalyzer.analyze_channel_congestion(networks)
            }
        }
        
        with open(filepath, 'w') as f:
            json.dump(report_data, f, indent=2, default=str)
        
        return filepath
    
    @staticmethod
    def generate_text_report(networks: List[Dict], scanner: WiFiScanner) -> str:
        """
        Generate text report
        
        Args:
            networks: List of network dictionaries
            scanner: WiFiScanner instance
            
        Returns:
            Path to generated report file
        """
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        filename = f"wifi_report_{timestamp}.txt"
        filepath = os.path.join(REPORTS_DIR, filename)
        
        lines = []
        lines.append("="*70)
        lines.append("                    WIFI ANALYZER REPORT")
        lines.append("="*70)
        lines.append(f"\nScan Time: {scanner.last_scan_time.strftime('%Y-%m-%d %H:%M:%S') if scanner.last_scan_time else 'N/A'}")
        lines.append(f"Total Networks: {len(networks)}")
        lines.append("\n" + "-"*70)
        lines.append("DISCOVERED NETWORKS")
        lines.append("-"*70)
        
        for idx, network in enumerate(networks, 1):
            ssid = network.get('ssid', '[Hidden]')
            level = network.get('level', -100)
            freq = network.get('frequency', 0)
            bssid = network.get('bssid', 'Unknown')
            
            quality, _, _ = WiFiAnalyzer.get_signal_quality(level)
            channel = WiFiAnalyzer.get_channel_from_freq(freq)
            band = WiFiAnalyzer.get_band(freq)
            security = WiFiAnalyzer.parse_capabilities(network.get('capabilities', ''))
            
            lines.append(f"\n[{idx}] {ssid}")
            lines.append(f"    BSSID:       {bssid}")
            lines.append(f"    Signal:      {level} dBm ({quality})")
            lines.append(f"    Channel:     {channel} ({band})")
            lines.append(f"    Security:    {security['protocol']} {security['security_emoji']}")
        
        # Add recommendations
        lines.append("\n" + "-"*70)
        lines.append("RECOMMENDATIONS")
        lines.append("-"*70)
        
        channel_recs = WiFiAnalyzer.get_best_channel_recommendation(networks)
        lines.append(f"\nBest 2.4GHz Channel: {channel_recs['2.4GHz']['channel']}")
        lines.append(f"  Reason: {channel_recs['2.4GHz']['reason']}")
        lines.append(f"\nBest 5GHz Channel: {channel_recs['5GHz']['channel']}")
        lines.append(f"  Reason: {channel_recs['5GHz']['reason']}")
        
        # Security warnings
        open_networks = [n for n in networks if 
                        WiFiAnalyzer.parse_capabilities(n.get('capabilities', '')).get('protocol') == 'Open']
        if open_networks:
            lines.append(f"\n⚠️  SECURITY WARNING: {len(open_networks)} open network(s) detected!")
        
        lines.append("\n" + "="*70)
        lines.append("Report generated by WiFi Analyzer | T3rmuxk1ng")
        lines.append("="*70)
        
        with open(filepath, 'w') as f:
            f.write('\n'.join(lines))
        
        return filepath


def main():
    """Main function - handles user interaction"""
    scanner = WiFiScanner()
    
    while True:
        WiFiDisplay.display_header()
        
        # Display menu
        if RICH_AVAILABLE and console:
            menu_text = """
[bold]MAIN MENU[/bold]

[1] 🔍 Scan Networks
[2] 📋 View Network Details
[3] 📊 Analysis Summary
[4] 🔐 Security Check
[5] 📡 Continuous Monitor
[6] 📄 Generate Report
[7] 📍 Current Connection Info
[0] 🚪 Exit
"""
            console.print(Panel(menu_text, border_style="cyan"))
            choice = Prompt.ask("Select option", choices=['0','1','2','3','4','5','6','7'], default='1')
        else:
            print("\nMAIN MENU")
            print("1. Scan Networks")
            print("2. View Network Details")
            print("3. Analysis Summary")
            print("4. Security Check")
            print("5. Continuous Monitor")
            print("6. Generate Report")
            print("7. Current Connection Info")
            print("0. Exit")
            choice = input("\nSelect option: ").strip()
        
        # Handle choices
        if choice == '0':
            if RICH_AVAILABLE and console:
                console.print("\n[green]Thank you for using WiFi Analyzer![/green]")
            else:
                print("\nThank you for using WiFi Analyzer!")
            break
            
        elif choice == '1':
            # Scan networks
            if RICH_AVAILABLE and console:
                with Progress(
                    SpinnerColumn(),
                    TextColumn("[progress.description]{task.description}"),
                    console=console
                ) as progress:
                    progress.add_task("Scanning WiFi networks...", total=None)
                    networks = scanner.scan_networks()
            else:
                print("Scanning WiFi networks...")
                networks = scanner.scan_networks()
            
            if scanner.scan_error:
                if RICH_AVAILABLE and console:
                    console.print(f"[red]Error: {scanner.scan_error}[/red]")
                else:
                    print(f"Error: {scanner.scan_error}")
            else:
                WiFiDisplay.display_networks_table(networks)
            
            input("\nPress Enter to continue...")
            
        elif choice == '2':
            # View network details
            if not scanner.networks:
                if RICH_AVAILABLE and console:
                    console.print("[yellow]No networks scanned yet. Run option 1 first.[/yellow]")
                else:
                    print("No networks scanned yet. Run option 1 first.")
                input("\nPress Enter to continue...")
                continue
            
            WiFiDisplay.display_networks_table(scanner.networks)
            
            if RICH_AVAILABLE and console:
                idx = IntPrompt.ask("Enter network number", default=1)
            else:
                idx = int(input("Enter network number: "))
            
            if 1 <= idx <= len(scanner.networks):
                WiFiDisplay.display_network_detail(scanner.networks[idx-1], idx)
            else:
                if RICH_AVAILABLE and console:
                    console.print("[red]Invalid network number![/red]")
                else:
                    print("Invalid network number!")
            
            input("\nPress Enter to continue...")
            
        elif choice == '3':
            # Analysis summary
            if not scanner.networks:
                if RICH_AVAILABLE and console:
                    console.print("[yellow]No networks scanned yet. Run option 1 first.[/yellow]")
                else:
                    print("No networks scanned yet. Run option 1 first.")
                input("\nPress Enter to continue...")
                continue
            
            WiFiDisplay.display_analysis_summary(scanner.networks)
            input("\nPress Enter to continue...")
            
        elif choice == '4':
            # Security check
            if not scanner.networks:
                if RICH_AVAILABLE and console:
                    console.print("[yellow]No networks scanned yet. Run option 1 first.[/yellow]")
                else:
                    print("No networks scanned yet. Run option 1 first.")
                input("\nPress Enter to continue...")
                continue
            
            # Display security-focused analysis
            open_networks = []
            weak_security = []
            secure_networks = []
            
            for network in scanner.networks:
                security = WiFiAnalyzer.parse_capabilities(network.get('capabilities', ''))
                if security['protocol'] == 'Open':
                    open_networks.append((network, security))
                elif security['security_rating'] < 3:
                    weak_security.append((network, security))
                else:
                    secure_networks.append((network, security))
            
            if RICH_AVAILABLE and console:
                # Open networks
                if open_networks:
                    console.print(Panel(
                        "\n".join([f"• {n.get('ssid', 'Hidden')}" for n, _ in open_networks]),
                        title=f"[bold red]⚠️ OPEN NETWORKS ({len(open_networks)})[/bold red]",
                        border_style="red"
                    ))
                
                # Weak security
                if weak_security:
                    console.print(Panel(
                        "\n".join([f"• {n.get('ssid', 'Hidden')} ({s['protocol']})" for n, s in weak_security]),
                        title=f"[bold yellow]⚠️ WEAK SECURITY ({len(weak_security)})[/bold yellow]",
                        border_style="yellow"
                    ))
                
                # Secure networks
                if secure_networks:
                    console.print(Panel(
                        "\n".join([f"• {n.get('ssid', 'Hidden')} ({s['protocol']})" for n, s in secure_networks]),
                        title=f"[bold green]✅ SECURE NETWORKS ({len(secure_networks)})[/bold green]",
                        border_style="green"
                    ))
            else:
                print(f"\nOpen Networks: {len(open_networks)}")
                for n, _ in open_networks:
                    print(f"  ⚠️ {n.get('ssid', 'Hidden')}")
                
                print(f"\nWeak Security: {len(weak_security)}")
                for n, s in weak_security:
                    print(f"  ⚠️ {n.get('ssid', 'Hidden')} ({s['protocol']})")
                
                print(f"\nSecure Networks: {len(secure_networks)}")
                for n, s in secure_networks:
                    print(f"  ✅ {n.get('ssid', 'Hidden')} ({s['protocol']})")
            
            input("\nPress Enter to continue...")
            
        elif choice == '5':
            # Continuous monitor
            interval = 5
            if RICH_AVAILABLE and console:
                interval = IntPrompt.ask("Update interval (seconds)", default=5)
            else:
                try:
                    interval = int(input("Update interval (seconds) [5]: ") or "5")
                except ValueError:
                    interval = 5
            
            WiFiDisplay.display_continuous_monitor(scanner, interval)
            input("\nPress Enter to continue...")
            
        elif choice == '6':
            # Generate report
            if not scanner.networks:
                if RICH_AVAILABLE and console:
                    console.print("[yellow]No networks scanned yet. Run option 1 first.[/yellow]")
                else:
                    print("No networks scanned yet. Run option 1 first.")
                input("\nPress Enter to continue...")
                continue
            
            if RICH_AVAILABLE and console:
                format_choice = Prompt.ask("Report format", choices=['json', 'text', 'both'], default='json')
            else:
                format_choice = input("Report format (json/text/both) [json]: ").lower() or 'json'
            
            if format_choice in ['json', 'both']:
                json_path = WiFiReport.generate_json_report(scanner.networks, scanner)
                if RICH_AVAILABLE and console:
                    console.print(f"[green]JSON report saved: {json_path}[/green]")
                else:
                    print(f"JSON report saved: {json_path}")
            
            if format_choice in ['text', 'both']:
                text_path = WiFiReport.generate_text_report(scanner.networks, scanner)
                if RICH_AVAILABLE and console:
                    console.print(f"[green]Text report saved: {text_path}[/green]")
                else:
                    print(f"Text report saved: {text_path}")
            
            input("\nPress Enter to continue...")
            
        elif choice == '7':
            # Current connection info
            connection = scanner.get_connection_info()
            
            if connection:
                if RICH_AVAILABLE and console:
                    info_text = f"""
[bold cyan]CURRENT CONNECTION[/bold cyan]

  SSID:       {connection.get('ssid', 'N/A')}
  BSSID:      {connection.get('bssid', 'N/A')}
  IP Address: {connection.get('ip', 'N/A')}
  Link Speed: {connection.get('link_speed', 'N/A')} Mbps
  Signal:     {connection.get('rssi', 'N/A')} dBm
  Frequency:  {connection.get('frequency', 'N/A')} MHz
  MAC:        {connection.get('mac_address', 'N/A')}
"""
                    console.print(Panel(info_text, border_style="green"))
                else:
                    print("\nCURRENT CONNECTION")
                    print("-" * 40)
                    print(f"SSID:       {connection.get('ssid', 'N/A')}")
                    print(f"BSSID:      {connection.get('bssid', 'N/A')}")
                    print(f"IP Address: {connection.get('ip', 'N/A')}")
                    print(f"Link Speed: {connection.get('link_speed', 'N/A')} Mbps")
                    print(f"Signal:     {connection.get('rssi', 'N/A')} dBm")
                    print("-" * 40)
            else:
                if RICH_AVAILABLE and console:
                    console.print("[yellow]Not connected to any WiFi network.[/yellow]")
                else:
                    print("Not connected to any WiFi network.")
            
            input("\nPress Enter to continue...")


if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        if RICH_AVAILABLE and console:
            console.print("\n[yellow]Exiting...[/yellow]")
        else:
            print("\nExiting...")
        sys.exit(0)
```

---

## 📁 PROJECT FILES STRUCTURE

```
~/wifi-analyzer/
├── wifi_analyzer.py          # Main application (complete)
├── modules/
│   ├── __init__.py           # Empty init file
│   ├── scanner.py            # Scanner module (optional separate)
│   ├── analyzer.py           # Analyzer module (optional separate)
│   ├── display.py            # Display module (optional separate)
│   └── report.py             # Report module (optional separate)
├── reports/                  # Generated reports folder
│   ├── wifi_report_*.json    # JSON reports
│   └── wifi_report_*.txt     # Text reports
└── README.md                 # Project documentation
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Scan and Analysis

```bash
# Task: Run WiFi analyzer and identify networks

# Step 1: Setup
mkdir -p ~/wifi-analyzer
cd ~/wifi-analyzer

# Step 2: Install dependencies
pkg install python -y
pip install rich

# Step 3: Create the main file (copy the source code above)
nano wifi_analyzer.py

# Step 4: Run the analyzer
python wifi_analyzer.py

# Step 5: Select option 1 to scan
# Step 6: Select option 3 for analysis
# Step 7: Note down:
#   - Total networks found
#   - Strongest signal
#   - Open networks (if any)
#   - Recommended channels

# Expected: You should see all nearby WiFi networks with details
```

### Exercise 2: Security Assessment

```bash
# Task: Analyze security of nearby networks

# Step 1: Run analyzer
python wifi_analyzer.py

# Step 2: Select option 1 to scan
# Step 3: Select option 4 for Security Check

# Step 4: Answer these questions:
#   - How many open networks are nearby?
#   - Which network has the best security (WPA3)?
#   - Which networks have weak security?

# Step 5: Document security recommendations for each network type
```

### Exercise 3: Channel Optimization

```bash
# Task: Determine optimal WiFi channel for your location

# Step 1: Run scan
python wifi_analyzer.py

# Step 2: Generate report (option 6)
# Step 3: View the channel recommendations

# Step 4: Analyze channel congestion:
#   - Which channels are most crowded?
#   - Which channels are recommended?
#   - Why are certain channels recommended?

# Step 5: If you have access to a router:
#   - Login to router admin panel
#   - Change WiFi channel to recommended one
#   - Re-scan and verify improvement
```

### Exercise 4: Continuous Monitoring

```bash
# Task: Monitor signal strength changes over time

# Step 1: Run analyzer
python wifi_analyzer.py

# Step 2: Select option 5 (Continuous Monitor)

# Step 3: Set interval to 3 seconds

# Step 4: Walk around your location:
#   - Go to different rooms
#   - Note signal changes
#   - Identify dead zones

# Step 5: Document:
#   - Where is signal strongest?
#   - Where is signal weakest?
#   - Signal variation range (e.g., -45 to -75 dBm)
```

### Exercise 5: Report Generation

```bash
# Task: Generate and analyze reports

# Step 1: Run scan
python wifi_analyzer.py

# Step 2: Select option 6 - Generate Report
# Step 3: Choose 'both' format

# Step 4: View JSON report
cat ~/wifi-analyzer/reports/wifi_report_*.json | python -m json.tool | head -50

# Step 5: View text report
cat ~/wifi-analyzer/reports/wifi_report_*.txt

# Step 6: Compare reports:
#   - Which format is more readable?
#   - What information is in JSON but not in text?
#   - How could reports be improved?
```

### Exercise 6: Custom Feature Addition

```python
# Task: Add a new feature to WiFi Analyzer

# Add this function to wifi_analyzer.py:

def export_to_csv(networks: List[Dict], filename: str = None) -> str:
    """Export networks to CSV format"""
    import csv
    
    if not filename:
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        filename = f"wifi_report_{timestamp}.csv"
    
    filepath = os.path.join(REPORTS_DIR, filename)
    
    with open(filepath, 'w', newline='') as f:
        writer = csv.writer(f)
        writer.writerow(['SSID', 'BSSID', 'Signal (dBm)', 'Channel', 
                        'Band', 'Security', 'Quality'])
        
        for network in networks:
            ssid = network.get('ssid', '[Hidden]')
            bssid = network.get('bssid', 'Unknown')
            level = network.get('level', -100)
            freq = network.get('frequency', 0)
            channel = WiFiAnalyzer.get_channel_from_freq(freq)
            band = WiFiAnalyzer.get_band(freq)
            security = WiFiAnalyzer.parse_capabilities(network.get('capabilities', ''))
            quality, _, _ = WiFiAnalyzer.get_signal_quality(level)
            
            writer.writerow([ssid, bssid, level, channel, band, 
                           security['protocol'], quality])
    
    return filepath

# Add this to the menu (option 8) and test it!
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "termux-api not installed"

```bash
# Cause: termux-api package is missing

# Solution:
pkg install termux-api -y

# Also ensure Termux:API app is installed from F-Droid
# Check:
dpkg -l | grep termux-api

# Test:
termux-battery-status
```

### Problem 2: "Scan returns empty list"

```bash
# Cause: Location permission not granted or WiFi off

# Solution 1: Check WiFi is enabled
termux-wifi-enable true  # May not work on Android 10+
# Manually enable WiFi in Android settings

# Solution 2: Grant location permission
# Android Settings → Apps → Termux:API → Permissions → Location → Allow

# Solution 3: Enable location in Android
# Pull down notification bar → Location icon → Enable

# Solution 4: First scan requires location access popup
# Run scan command and accept the permission popup
termux-wifi-scaninfo
```

### Problem 3: "Rich library not working"

```bash
# Cause: Rich not installed or incompatible version

# Solution 1: Install rich
pip install rich

# Solution 2: Upgrade pip and reinstall
pkg install python -y
pip install --upgrade pip
pip install --upgrade rich

# Solution 3: If still not working, the script will fallback to plain output
# The code handles missing rich gracefully
```

### Problem 4: "Permission denied" when creating reports

```bash
# Cause: Reports directory not accessible

# Solution 1: Create directory manually
mkdir -p ~/wifi-analyzer/reports

# Solution 2: Check permissions
ls -la ~/wifi-analyzer/

# Solution 3: Use different path
# Edit the script and change REPORTS_DIR
REPORTS_DIR = os.path.expanduser("~/storage/downloads/wifi-reports")
# But first run: termux-setup-storage
```

### Problem 5: Continuous monitor doesn't refresh

```bash
# Cause: Terminal not clearing properly

# Solution 1: Use simple terminal clear
# The script uses console.clear() with rich
# Try running without rich to see if it's the issue

# Solution 2: Increase interval
# Use longer interval like 10 seconds

# Solution 3: Check for errors
# Run with debug output
python wifi_analyzer.py 2>&1 | tee wifi_debug.log
```

### Problem 6: Hidden SSIDs showing as empty

```bash
# Cause: Hidden networks don't broadcast SSID

# Explanation: This is normal behavior
# Hidden networks return empty or "<Hidden>" SSID
# You can still see BSSID, signal, and security

# BSSID can help identify known hidden networks
# Compare with your router's MAC address
```

### Problem 7: Signal strength fluctuating wildly

```bash
# Cause: Physical obstacles, interference, or device antenna

# Solution 1: Take multiple readings
# Use continuous monitor for average

# Solution 2: Check for interference
# Look at channel congestion analysis

# Solution 3: Physical factors
# Move closer to access point
# Remove cases that might block antenna
# Check for microwave ovens, bluetooth devices nearby
```

### Problem 8: "No networks found" but WiFi is on

```bash
# Cause: Android 10+ background location restrictions

# Solution 1: Enable precise location
Settings → Apps → Termux:API → Permissions → Location → "Allow all the time"

# Solution 2: Disable battery optimization for Termux:API
Settings → Apps → Termux:API → Battery → Unrestricted

# Solution 3: Android 12+ requires precise location
Settings → Location → App location permissions → Termux:API → "Allow all the time" + "Use precise location"

# Solution 4: Try multiple scans
# First scan might fail, subsequent succeed
for i in {1..3}; do termux-wifi-scaninfo; sleep 2; done
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📡 WIFI ANALYZER                 │
│   Build Your Own Scanner           │
│                                    │
│   ✓ Signal Analysis                │
│   ✓ Security Check                 │
│   ✓ Channel Optimization           │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Network Visualization**
```
┌────────────────────────────────────┐
│  [WiFi Signal Bars Animation]      │
│                                    │
│   ┌──────┐ ┌──────┐ ┌──────┐      │
│   │ MyNet│ │ Guest│ │ IoT  │      │
│   │ -45  │ │ -67  │ │ -80  │      │
│   │ WPA3 │ │ OPEN │ │ WPA2 │      │
│   └──────┘ └──────┘ └──────┘      │
│                                    │
│   PROJECT 3 | T3RMUXK1NG           │
└────────────────────────────────────┘
```

**Option C: Signal Analysis Style**
```
┌────────────────────────────────────┐
│  📊 SIGNAL ANALYSIS                │
│                                    │
│  MyWiFi    ████████████ -45 dBm   │
│  Guest     ████████     -67 dBm   │
│  IoT       ████         -80 dBm   │
│                                    │
│  📡 Python + Termux API            │
│  Chapter 53 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📡 Termux Full Course - Chapter 53: Project 3 - WiFi Analyzer | Build Your Own Network Scanner

🔥 In this video you'll learn:
• Complete WiFi Analyzer tool development
• Using termux-wifi-scaninfo API
• Signal strength analysis and quality assessment
• Security evaluation of networks
• Channel congestion detection
• Real-time monitoring implementation
• Report generation (JSON/Text)

⏱️ Timestamps:
0:00 - Introduction
1:00 - Project Overview
4:00 - Termux WiFi API Deep Dive
7:30 - Signal Strength Understanding
10:00 - Channel Analysis
12:30 - Encryption Types
15:00 - Project Structure
17:00 - Coding Part 1
20:00 - Coding Part 2
23:00 - Demo & Testing
25:00 - Summary

📥 Source Code:
Full source code available in the course materials!

📝 Prerequisites:
• Termux installed from F-Droid
• Termux:API app installed
• Python installed (pkg install python)
• Rich library (pip install rich)

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #WiFiAnalyzer #Python #TermuxProject #NetworkAnalysis #T3rmuxk1ng #TermuxCourse #EthicalHacking #NetworkSecurity

---
⚠️ Disclaimer: This video is for educational purposes only. Use these tools responsibly and only on networks you own or have permission to analyze. Do not use for illegal activities.
```

### Tags List

```
termux, wifi analyzer, termux wifi scan, python termux, termux project,
network scanner, wifi signal strength, termux api, termux tutorial,
wifi security, channel analysis, termux course, t3rmuxk1ng,
ethical hacking, network analysis, wifi troubleshooting,
termux python, android wifi scanner, wifi optimization,
network security, penetration testing, termux full course
```

### Hashtags

```
#Termux #WiFiAnalyzer #PythonProject #TermuxCourse #NetworkAnalysis 
#WiFiSecurity #TermuxTutorial #T3rmuxk1ng #EthicalHacking #NetworkSecurity 
#WiFiOptimization #TermuxAPI #AndroidHacking #CyberSecurity #LearnTermux
```

---

## 📚 ADDITIONAL RESOURCES

### WiFi Standards Reference

| Standard | Frequency | Max Speed | Year |
|----------|-----------|-----------|------|
| 802.11b | 2.4 GHz | 11 Mbps | 1999 |
| 802.11a | 5 GHz | 54 Mbps | 1999 |
| 802.11g | 2.4 GHz | 54 Mbps | 2003 |
| 802.11n | 2.4/5 GHz | 600 Mbps | 2009 |
| 802.11ac | 5 GHz | 6.9 Gbps | 2013 |
| 802.11ax (WiFi 6) | 2.4/5 GHz | 9.6 Gbps | 2019 |
| 802.11be (WiFi 7) | 2.4/5/6 GHz | 46 Gbps | 2024 |

### Useful Commands Quick Reference

```bash
# Scan WiFi networks
termux-wifi-scaninfo

# Get current connection info
termux-wifi-connectioninfo

# Enable/disable WiFi (may not work on newer Android)
termux-wifi-enable true
termux-wifi-enable false

# Quick scan with Python parsing
termux-wifi-scaninfo | python -m json.tool

# Count networks
termux-wifi-scaninfo | python -c "import sys,json; print(len(json.load(sys.stdin)))"

# Find open networks
termux-wifi-scaninfo | python -c "import sys,json; [print(n['ssid']) for n in json.load(sys.stdin) if 'WPA' not in n.get('capabilities','') and n.get('ssid')]"
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 54, verify:

- [ ] WiFi analyzer tool created and working
- [ ] Successfully scanned nearby networks
- [ ] Understood signal strength values (dBm)
- [ ] Analyzed security configurations
- [ ] Generated reports (JSON and Text)
- [ ] Tested continuous monitoring mode
- [ ] Identified channel recommendations
- [ ] Completed practice exercises
- [ ] Understood WiFi frequency bands

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 54: Project 4 - YouTube Downloader Bot**

- yt-dlp integration in Termux
- Download videos and audio
- Format selection and quality options
- Batch download automation
- Telegram bot integration
- Notification system
- Download queue management
- Complete source code

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
