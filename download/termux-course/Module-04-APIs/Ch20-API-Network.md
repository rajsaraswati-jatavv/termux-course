# Chapter 20: Termux API - Network Operations

> **Module:** 4 - APIs  
> **Chapter:** 20 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | WiFi, Mobile Data, Hotspot, Network Info |
| Commands Reference | All network API commands |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common network API issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 20
Title: Termux Network API | WiFi, Hotspot, IP Address | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj ka chapter bahut important hai - Network Operations with Termux API.

Network operations ka matlab hai - WiFi control karna, IP address nikalna,
MAC address dekhna, hotspot on/off karna, mobile data control karna, aur
bahut kuch - sab kuch terminal se!

Ye skills penetration testing mein bahut useful hain. Network information
gather karna, WiFi networks scan karna, connection details analyze karna -
ye sab ethical hacker ke basic skills hain.

Aur sabse best baat - ye sab bina root ke kaam karega!

To chaliye shuru karte hain. Video like karein, subscribe karein, aur
notification bell on karein.

---

[SECTION 1: TERMUX-API INSTALLATION CHECK - 0:45 to 2:30]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle, Termux:API app install honi chahiye.

Termux API commands use karne ke liye do cheezein chahiye:
1. Termux app (jo already hai)
2. Termux:API app (F-Droid se install karein)

Check karein:

    pkg install termux-api -y

Ye command Termux API package install karta hai.

Ab check karein ki API kaam kar rahi hai:

    termux-wifi-connectioninfo

Agar JSON output aaya with WiFi details - to sab theek hai!

Agar error aaya:
- "permission denied" → Android settings mein permission enable karein
- "not installed" → Termux:API app install karein F-Droid se

Important: Termux:API app Termux app ke saath match karni chahiye -
dono F-Droid se honi chahiye, ya dono Play Store se. Mix mat karein!

---

[SECTION 2: WIFI CONNECTION INFO - 2:30 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Pehla command - WiFi connection information.

    termux-wifi-connectioninfo

Ye command current WiFi connection ki detailed information deta hai.

Output mein kya kya aata hai:

{
  "bssid": "aa:bb:cc:dd:ee:ff",      // Router ka MAC address
  "ssid": "MyWiFiNetwork",            // Network name
  "ip": "192.168.1.100",              // Aapka IP address
  "mac": "11:22:33:44:55:66",         // Aapke device ka MAC
  "rssi": -45,                        // Signal strength
  "link_speed": 65,                   // Mbps
  "network_id": 5                     // Saved network ID
}

Har field ka explanation:

BSSID - Ye router ka unique identifier hai, MAC address jaise.
SSD - Ye network ka naam hai jo aap connected ho.
IP - Aapka current IP address network pe.
MAC - Aapke phone ka WiFi MAC address.
RSSI - Signal strength in dBm. -30 se -50 excellent, -70 fair, -90 weak.
Link Speed - Current connection speed Mbps mein.

Practical example - Check karein ki aap kis network pe ho:

    termux-wifi-connectioninfo | jq '.ssid'

"HomeWiFi" output aayega.

Wait, jq kya hai? jq ek JSON processor hai.

Install karein:

    pkg install jq -y

Ab aap specific values extract kar sakte ho:

    # IP address only
    termux-wifi-connectioninfo | jq '.ip'
    
    # Signal strength
    termux-wifi-connectioninfo | jq '.rssi'
    
    # Network name
    termux-wifi-connectioninfo | jq '.ssid'

---

[SECTION 3: WIFI ENABLE/DISABLE - 5:00 to 7:30]
─────────────────────────────────────────────────────────────────────────────

Ab WiFi ko on/off karna seekhte hain.

WiFi ON karne ke liye:

    termux-wifi-enable true

WiFi OFF karne ke liye:

    termux-wifi-enable false

Simple hai na?

Lekin wait - Android 10+ pe ye permission chahiye:
- Location access (required for WiFi operations)

Permission grant karne ke liye:

    termux-location

Ye command permission popup laayegi. Allow karein.

Ab WiFi toggle kaam karega.

Practical use case - Script bana sakte ho:

    # wifi-toggle.sh
    #!/bin/bash
    
    CURRENT=$(termux-wifi-connectioninfo 2>/dev/null)
    
    if [ -z "$CURRENT" ]; then
        echo "WiFi is OFF, turning ON..."
        termux-wifi-enable true
    else
        echo "WiFi is ON, turning OFF..."
        termux-wifi-enable false
    fi

Ye script check karegi WiFi status aur toggle karegi.

Automation ke liye useful hai - Tasker ke saath, cron jobs ke saath.

---

[SECTION 4: WIFI SCAN INFO - 7:30 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab sabse powerful command - WiFi scanning!

    termux-wifi-scaninfo

Ye command aas-paas ke saare WiFi networks scan karti hai.

Output mein har network ki details aati hai:

[
  {
    "ssid": "HomeWiFi",
    "bssid": "aa:bb:cc:dd:ee:ff",
    "frequency": 2412,
    "rssi": -45,
    "capabilities": "[WPA2-PSK-CCMP][ESS]"
  },
  {
    "ssid": "Neighbor_Net",
    "bssid": "11:22:33:44:55:66",
    "frequency": 2437,
    "rssi": -75,
    "capabilities": "[WPA2-PSK-CCMP][WPS][ESS]"
  }
]

Har field ka matlab:

SSID - Network name (hidden networks mein empty)
BSSID - Router ka MAC address
Frequency - WiFi frequency in MHz (2412 = channel 1, 2437 = channel 6)
RSSI - Signal strength
Capabilities - Security features (WPA2, WPS, etc.)

Interesting fact: Hidden networks bhi detect hote hain!
SSID empty hoga, lekin BSSID aur signal strength dikhegi.

Practical use - Network audit karein:

    # Count available networks
    termux-wifi-scaninfo | jq 'length'
    
    # List all SSIDs
    termux-wifi-scaninfo | jq '.[].ssid'
    
    # Find open networks (no password)
    termux-wifi-scaninfo | jq '.[] | select(.capabilities | contains("ESS"))'
    
    # Strongest signal first
    termux-wifi-scaninfo | jq 'sort_by(.rssi) | reverse | .[0:5]'

Security tip: WPS enabled networks vulnerable ho sakte hain.
Check karein:

    termux-wifi-scaninfo | jq '.[] | select(.capabilities | contains("WPS"))'

---

[SECTION 5: GET WIFI PASSWORD (ROOT REQUIRED) - 10:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek sensitive topic - WiFi password retrieve karna.

⚠️ WARNING: Ye ROOT access chahiye aur sirf apne networks ke liye use karein!

Normal Termux API se saved WiFi passwords nahi milte.
Android security ke wajah se passwords encrypted hain.

Root access ke saath:

Method 1: Direct file access (older Android)

    su -c "cat /data/misc/wifi/wpa_supplicant.conf"

Method 2: Android 10+ ke liye

    su -c "cat /data/misc/wifi/WifiConfigStore.xml"

Ye files mein saved networks aur passwords hote hain.

Alternative - Root ke bina:

Kuch third-party apps saved WiFi share kar sakte hain QR code mein:
- Share WiFi from Settings → WiFi → Tap network → Share

Termux se QR generate kar sakte ho:

    # Install qrencode
    pkg install qrencode -y
    
    # Generate QR for WiFi (manual entry)
    qrencode -t ANSIUTF8 "WIFI:T:WPA;S:NetworkName;P:Password;;"

Important: Kisi ke WiFi password bina permission ke access karna
illegal hai. Sirf apne networks ke liye use karein!

---

[SECTION 6: MOBILE DATA CONTROL - 12:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Mobile data ko control karna Termux API se:

Mobile Data ON:

    termux-telephony-cellinfo
    # Note: Direct mobile data toggle requires special permissions

Actually, Termux API directly mobile data toggle nahi karti
Android security restrictions ke wajah se.

Alternative methods:

Method 1: Using settings command (Android 5+)

    # View mobile data setting
    settings get global mobile_data
    
    # Toggle (requires WRITE_SECURE_SETTINGS - adb needed)
    settings put global mobile_data 1  # ON
    settings put global mobile_data 0  # OFF

Method 2: Using su (root required)

    su -c "svc data enable"   # ON
    su -c "svc data disable"  # OFF

Method 3: Using am command (intent)

    # Open mobile data settings
    am start -a android.settings.DATA_ROAMING_SETTINGS

Network status check karein:

    termux-telephony-deviceinfo

Ye command SIM aur network information deti hai.

Data usage check (Android settings se):

    dumpsys netstats | head -50

---

[SECTION 7: HOTSPOT CONTROL - 14:00 to 15:30]
─────────────────────────────────────────────────────────────────────────────

WiFi Hotspot control - Termux API se direct hotspot toggle nahi hota.
Lekin dusre methods hain:

Method 1: Settings intent

    # Open hotspot settings
    am start -a android.settings.WIFI_HOTSPOT_SETTINGS

Method 2: Root users ke liye

    # Enable hotspot
    su -c "svc wifi disable"  # WiFi off first
    su -c "ndc softap start wlan0 MyHotspot 12345678"
    
    # Disable hotspot
    su -c "ndc softap stop wlan0"

Method 3: Using ifconfig (root)

    # Check hotspot interface
    su -c "ifconfig wlan0"

Hotspot information:

    # Network interfaces
    ifconfig
    
    # IP tables (requires root)
    su -c "iptables -t nat -L"

Hotspot connected devices check:

    su -c "cat /proc/net/arp"

Ye command ARP table dikhati hai - connected devices ke IP aur MAC.

---

[SECTION 8: IP ADDRESS INFORMATION - 15:30 to 17:00]
─────────────────────────────────────────────────────────────────────────────

IP address information - Multiple ways se nikal sakte hain.

Internal IP (local network):

    # Method 1: ifconfig
    ifconfig wlan0
    
    # Method 2: ip command
    ip addr show wlan0
    
    # Method 3: Termux API
    termux-wifi-connectioninfo | jq '.ip'
    
    # Quick one-liner
    ifconfig wlan0 | grep "inet " | awk '{print $2}'

External IP (public IP - internet se):

    # Using curl
    curl -s ifconfig.me
    
    # Alternative services
    curl -s icanhazip.com
    curl -s ipecho.net/plain
    curl -s api.ipify.org
    
    # With more info
    curl -s ipinfo.io

All network interfaces:

    # List all interfaces
    ip link show
    
    # All IPs
    ip addr
    
    # Specific interface
    ip addr show wlan0
    ip addr show rmnet0  # Mobile data

Gateway IP:

    # Using ip route
    ip route | grep default
    
    # Using route command (install net-tools)
    pkg install net-tools -y
    route -n

DNS servers:

    # Check DNS
    cat /etc/resolv.conf
    
    # Android DNS (requires root)
    su -c "getprop | grep dns"

---

[SECTION 9: MAC ADDRESS - 17:00 to 18:30]
─────────────────────────────────────────────────────────────────────────────

MAC address - Device ka unique hardware identifier.

WiFi MAC address:

    # Method 1: ifconfig
    ifconfig wlan0 | grep -o '..:..:..:..:..:..'
    
    # Method 2: ip command
    ip link show wlan0 | grep -o '..:..:..:..:..:..'
    
    # Method 3: Termux API
    termux-wifi-connectioninfo | jq '.mac'

Mobile Data MAC:

    # Check rmnet interface
    ip link show rmnet0

All interfaces MAC:

    # List all with MACs
    ip link | grep -E "^[0-9]:|ether"

MAC address randomization:

Android 10+ randomize MAC addresses for privacy.
Real MAC address sirf root se milta hai.

    # Real MAC (root)
    su -c "cat /sys/class/net/wlan0/address"

Spoof MAC address (root):

    # Turn off WiFi first
    su -c "ifconfig wlan0 down"
    
    # Change MAC
    su -c "ifconfig wlan0 hw ether 00:11:22:33:44:55"
    
    # Turn on WiFi
    su -c "ifconfig wlan0 up"

⚠️ Warning: MAC spoofing some networks pe kaam nahi karega
aur unethical activities ke liye illegal hai.

---

[SECTION 10: NETWORK STATS & MONITORING - 18:30 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Network statistics aur monitoring.

Data usage stats:

    # Network statistics (Android)
    dumpsys netstats | grep -A 10 "Dev stats"
    
    # Current connections
    netstat -tunl
    
    # Established connections
    netstat -tun

Network monitoring tools:

    # Install useful tools
    pkg install nmap netcat curl wget -y

Ping test:

    # Simple ping
    ping -c 4 google.com
    
    # Local network ping
    ping -c 4 192.168.1.1

DNS lookup:

    # Using nslookup
    nslookup google.com
    
    # Using dig (install dnsutils)
    pkg install dnsutils -y
    dig google.com

Port scanning (local network):

    # Quick scan
    nmap -sP 192.168.1.0/24
    
    # Port scan specific IP
    nmap -p 80,443,22 192.168.1.1

Bandwidth test:

    # Simple speed test
    curl -o /dev/null -w "Speed: %{speed_download} bytes/sec\n" http://speedtest.tele2.net/1MB.zip

---

[SECTION 11: PRACTICAL SCRIPTS - 20:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Ab kuch practical scripts banate hain.

[SCRIPT 1: Network Info Dashboard]

    #!/bin/bash
    # network-info.sh - Complete network information
    
    echo "╔══════════════════════════════════════════╗"
    echo "║     NETWORK INFORMATION DASHBOARD        ║"
    echo "╚══════════════════════════════════════════╝"
    echo ""
    
    # WiFi Info
    echo "📡 WiFi INFORMATION"
    echo "───────────────────"
    WIFI_INFO=$(termux-wifi-connectioninfo 2>/dev/null)
    if [ -n "$WIFI_INFO" ]; then
        echo "SSID: $(echo $WIFI_INFO | jq -r '.ssid')"
        echo "IP: $(echo $WIFI_INFO | jq -r '.ip')"
        echo "MAC: $(echo $WIFI_INFO | jq -r '.mac')"
        echo "Signal: $(echo $WIFI_INFO | jq -r '.rssi') dBm"
        echo "Speed: $(echo $WIFI_INFO | jq -r '.link_speed') Mbps"
    else
        echo "WiFi not connected"
    fi
    echo ""
    
    # Public IP
    echo "🌍 PUBLIC IP"
    echo "───────────────────"
    PUBLIC_IP=$(curl -s --max-time 5 ifconfig.me)
    if [ -n "$PUBLIC_IP" ]; then
        echo "Public IP: $PUBLIC_IP"
    else
        echo "Unable to fetch public IP"
    fi
    echo ""
    
    # Available Networks
    echo "📶 AVAILABLE NETWORKS"
    echo "───────────────────"
    termux-wifi-scaninfo 2>/dev/null | jq -r '.[] | "• \(.ssid // "Hidden") - Signal: \(.rssi) dBm"' | head -10

[SCRIPT 2: WiFi Analyzer]

    #!/bin/bash
    # wifi-analyzer.sh - Analyze WiFi networks
    
    echo "🔍 WiFi ANALYZER"
    echo "══════════════════════════════════════"
    echo ""
    
    # Scan networks
    NETWORKS=$(termux-wifi-scaninfo)
    
    # Count
    COUNT=$(echo "$NETWORKS" | jq 'length')
    echo "Found $COUNT networks"
    echo ""
    
    # Sort by signal strength
    echo "📶 SIGNAL STRENGTH RANKING"
    echo "─────────────────────────────"
    echo "$NETWORKS" | jq -r 'sort_by(.rssi) | reverse | .[] | "[\(.rssi) dBm] \(.ssid // "Hidden")"' | head -15
    echo ""
    
    # Security analysis
    echo "🔒 SECURITY ANALYSIS"
    echo "─────────────────────────────"
    WPA3=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA3"))] | length')
    WPA2=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA2"))] | length')
    WPA=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA-") and contains("WPA2") | not)] | length')
    OPEN=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("ESS") and contains("WPA") | not)] | length')
    
    echo "WPA3 Networks: $WPA3"
    echo "WPA2 Networks: $WPA2"
    echo "WPA Networks: $WPA"
    echo "Open Networks: $OPEN"
    echo ""
    
    # WPS Warning
    WPS=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPS"))] | length')
    if [ "$WPS" -gt 0 ]; then
        echo "⚠️  WARNING: $WPS networks have WPS enabled!"
        echo "WPS can be vulnerable to brute force attacks."
        echo "$NETWORKS" | jq -r '.[] | select(.capabilities | contains("WPS")) | "   - \(.ssid // "Hidden")"'
    fi

[SCRIPT 3: Network Monitor]

    #!/bin/bash
    # network-monitor.sh - Continuous network monitoring
    
    LOG_FILE="network_monitor.log"
    
    echo "📊 NETWORK MONITOR STARTED"
    echo "Logging to: $LOG_FILE"
    echo "Press Ctrl+C to stop"
    echo ""
    
    while true; do
        TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')
        WIFI_STATUS=$(termux-wifi-connectioninfo 2>/dev/null | jq -r '.ssid // "Disconnected"')
        SIGNAL=$(termux-wifi-connectioninfo 2>/dev/null | jq -r '.rssi // "N/A"')
        
        echo "[$TIMESTAMP] WiFi: $WIFI_STATUS | Signal: $SIGNAL dBm" | tee -a "$LOG_FILE"
        sleep 5
    done

---

[SECTION 12: PYTHON INTEGRATION - 22:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Python se Termux network API use karna.

Basic Python script:

    #!/usr/bin/env python3
    # network_tool.py
    
    import subprocess
    import json
    
    def get_wifi_info():
        """Get current WiFi connection info"""
        try:
            result = subprocess.run(
                ['termux-wifi-connectioninfo'],
                capture_output=True,
                text=True
            )
            return json.loads(result.stdout)
        except Exception as e:
            return {"error": str(e)}
    
    def get_public_ip():
        """Get public IP address"""
        try:
            result = subprocess.run(
                ['curl', '-s', 'ifconfig.me'],
                capture_output=True,
                text=True,
                timeout=10
            )
            return result.stdout.strip()
        except Exception as e:
            return None
    
    def scan_networks():
        """Scan available WiFi networks"""
        try:
            result = subprocess.run(
                ['termux-wifi-scaninfo'],
                capture_output=True,
                text=True
            )
            return json.loads(result.stdout)
        except Exception as e:
            return []
    
    def get_signal_quality(rssi):
        """Convert RSSI to quality percentage"""
        if rssi >= -50:
            return "Excellent (90-100%)"
        elif rssi >= -60:
            return "Good (70-89%)"
        elif rssi >= -70:
            return "Fair (50-69%)"
        elif rssi >= -80:
            return "Weak (30-49%)"
        else:
            return "Very Weak (<30%)"
    
    if __name__ == "__main__":
        print("═" * 45)
        print("     TERMUX NETWORK TOOL (Python)")
        print("═" * 45)
        
        # WiFi Info
        wifi = get_wifi_info()
        if "error" not in wifi and wifi:
            print(f"\n📡 Connected to: {wifi.get('ssid', 'N/A')}")
            print(f"   IP Address: {wifi.get('ip', 'N/A')}")
            print(f"   Signal: {get_signal_quality(wifi.get('rssi', -100))}")
        else:
            print("\n📡 WiFi: Not connected")
        
        # Public IP
        public = get_public_ip()
        print(f"\n🌍 Public IP: {public or 'Unable to fetch'}")
        
        # Network count
        networks = scan_networks()
        print(f"\n📶 Networks found: {len(networks)}")

Advanced Python - WiFi Security Checker:

    #!/usr/bin/env python3
    # wifi_security_check.py
    
    import subprocess
    import json
    from datetime import datetime
    
    class WiFiSecurityScanner:
        def __init__(self):
            self.networks = []
        
        def scan(self):
            """Perform WiFi scan"""
            result = subprocess.run(
                ['termux-wifi-scaninfo'],
                capture_output=True,
                text=True
            )
            self.networks = json.loads(result.stdout)
            return self.networks
        
        def analyze_security(self, capabilities):
            """Analyze network security"""
            security = {
                'wpa3': 'WPA3' in capabilities,
                'wpa2': 'WPA2' in capabilities,
                'wpa': 'WPA-' in capabilities and 'WPA2' not in capabilities,
                'wps': 'WPS' in capabilities,
                'open': 'ESS' in capabilities and 'WPA' not in capabilities
            }
            return security
        
        def get_risk_level(self, capabilities):
            """Determine network risk level"""
            sec = self.analyze_security(capabilities)
            
            if sec['open']:
                return "HIGH RISK - Open network"
            elif sec['wps']:
                return "MEDIUM RISK - WPS enabled"
            elif sec['wpa']:
                return "LOW RISK - Outdated WPA"
            elif sec['wpa2']:
                return "LOW RISK - WPA2 secure"
            elif sec['wpa3']:
                return "MINIMAL RISK - WPA3 secure"
            else:
                return "UNKNOWN RISK"
        
        def generate_report(self):
            """Generate security report"""
            print("\n" + "═" * 55)
            print("     WiFi Security Assessment Report")
            print("     Generated:", datetime.now().strftime("%Y-%m-%d %H:%M"))
            print("═" * 55 + "\n")
            
            if not self.networks:
                self.scan()
            
            # Statistics
            total = len(self.networks)
            open_count = sum(1 for n in self.networks 
                           if self.analyze_security(n.get('capabilities', '')).get('open'))
            wps_count = sum(1 for n in self.networks 
                          if self.analyze_security(n.get('capabilities', '')).get('wps'))
            
            print(f"📊 SUMMARY")
            print(f"   Total Networks: {total}")
            print(f"   Open Networks: {open_count} ⚠️")
            print(f"   WPS Enabled: {wps_count} ⚠️")
            print("\n" + "─" * 55)
            
            # Details
            print("\n📋 NETWORK DETAILS\n")
            for net in sorted(self.networks, key=lambda x: x.get('rssi', 0), reverse=True):
                ssid = net.get('ssid') or 'Hidden Network'
                rssi = net.get('rssi', 0)
                caps = net.get('capabilities', '')
                risk = self.get_risk_level(caps)
                
                print(f"• {ssid}")
                print(f"  Signal: {rssi} dBm")
                print(f"  Security: {risk}")
                print()
    
    # Run
    if __name__ == "__main__":
        scanner = WiFiSecurityScanner()
        scanner.generate_report()

---

[SECTION 13: 20+ PRACTICAL EXAMPLES - 24:00 to 27:00]
─────────────────────────────────────────────────────────────────────────────

Ab 20+ practical examples quickly:

1. Get WiFi name only
    termux-wifi-connectioninfo | jq -r '.ssid'

2. Get IP only
    termux-wifi-connectioninfo | jq -r '.ip'

3. Get MAC only
    termux-wifi-connectioninfo | jq -r '.mac'

4. Check signal strength
    termux-wifi-connectioninfo | jq '.rssi'

5. Turn WiFi on
    termux-wifi-enable true

6. Turn WiFi off
    termux-wifi-enable false

7. Count nearby networks
    termux-wifi-scaninfo | jq 'length'

8. List all SSIDs
    termux-wifi-scaninfo | jq '.[].ssid' | sort | uniq

9. Find strongest network
    termux-wifi-scaninfo | jq 'sort_by(.rssi) | reverse | .[0]'

10. Find open networks
    termux-wifi-scaninfo | jq '.[] | select(.capabilities | contains("ESS") and contains("WPA") | not)'

11. Find WPS enabled (vulnerable)
    termux-wifi-scaninfo | jq '.[] | select(.capabilities | contains("WPS"))'

12. Get public IP
    curl -s ifconfig.me

13. Get IP with location
    curl -s ipinfo.io

14. Check local IP
    ip addr show wlan0 | grep inet

15. Check gateway
    ip route | grep default

16. Ping test
    ping -c 3 google.com

17. DNS lookup
    nslookup google.com

18. Check open ports (local)
    netstat -tunl

19. Network interfaces
    ip link show

20. Quick speed test
    curl -o /dev/null -w "%{speed_download}\n" http://example.com

21. WiFi toggle script
    [ -z "$(termux-wifi-connectioninfo 2>/dev/null)" ] && termux-wifi-enable true || termux-wifi-enable false

22. Monitor signal
    watch -n 2 'termux-wifi-connectioninfo | jq ".rssi"'

23. Export networks to file
    termux-wifi-scaninfo > networks_$(date +%Y%m%d).json

24. Find specific network
    termux-wifi-scaninfo | jq '.[] | select(.ssid | contains("MyNetwork"))'

25. Check connection quality
    RSSI=$(termux-wifi-connectioninfo | jq '.rssi'); [ $RSSI -gt -70 ] && echo "Good" || echo "Weak"

---

[SECTION 14: SUMMARY & NEXT PREVIEW - 27:00 to 28:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 20 complete! Let's summarize:

✅ termux-wifi-connectioninfo - Current WiFi details
✅ termux-wifi-enable - WiFi on/off control
✅ termux-wifi-scaninfo - Network scanning
✅ WiFi password retrieval (root methods)
✅ Mobile data control methods
✅ Hotspot management
✅ IP address information
✅ MAC address extraction
✅ Network statistics
✅ Python integration
✅ 20+ practical examples
✅ Network monitoring scripts

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 20 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ termux-wifi-connectioninfo   │ Current WiFi details                      │
│ termux-wifi-enable true/false│ WiFi on/off                               │
│ termux-wifi-scaninfo         │ Scan nearby networks                      │
│ curl -s ifconfig.me          │ Get public IP                             │
│ ip addr show wlan0           │ Local IP & MAC                            │
│ ip route                     │ Gateway info                              │
│ ping -c 4 google.com         │ Connectivity test                         │
│ nmap -sP 192.168.1.0/24      │ Network scan                              │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 21 mein hum seekhenge:
- Termux Notification API
- Custom notifications create karna
- Notification actions
- Progress notifications
- Notification channels

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 21!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Termux Network API Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX NETWORK API ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Termux Commands Layer                         │   │
│   │   termux-wifi-connectioninfo, termux-wifi-enable, etc.          │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Termux:API Application                        │   │
│   │   (Android Service with System Permissions)                     │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Android System APIs                           │   │
│   │   WifiManager, ConnectivityManager, NetworkInfo                 │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Linux Network Stack                           │   │
│   │   Network interfaces, routing, DNS resolution                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. WiFi API Commands

#### termux-wifi-connectioninfo

Returns detailed information about the current WiFi connection.

**Output Fields:**

| Field | Type | Description |
|-------|------|-------------|
| bssid | string | Router's MAC address |
| ssid | string | Network name |
| ip | string | Device's local IP address |
| mac | string | Device's WiFi MAC address |
| rssi | integer | Signal strength in dBm |
| link_speed | integer | Connection speed in Mbps |
| network_id | integer | Saved network ID |
| frequency | integer | WiFi frequency in MHz |

**Example Output:**
```json
{
  "bssid": "aa:bb:cc:dd:ee:ff",
  "ssid": "MyWiFiNetwork",
  "ip": "192.168.1.100",
  "mac": "11:22:33:44:55:66",
  "rssi": -45,
  "link_speed": 65,
  "network_id": 5,
  "frequency": 2412
}
```

**Signal Strength Guide:**

| RSSI Range | Quality | Description |
|------------|---------|-------------|
| -30 to -50 | Excellent | Full signal bars |
| -50 to -60 | Good | Strong signal |
| -60 to -70 | Fair | Moderate signal |
| -70 to -80 | Weak | Poor signal |
| -80 to -90 | Very Weak | Unstable connection |
| Below -90 | Unusable | No connection |

#### termux-wifi-enable

Controls WiFi radio state.

**Syntax:**
```bash
termux-wifi-enable true   # Turn WiFi ON
termux-wifi-enable false  # Turn WiFi OFF
```

**Requirements:**
- Android 10+: Location permission required
- Termux:API app must be installed

**Permission Setup:**
```bash
# Trigger permission request
termux-location

# Or manually grant in Settings
# Settings → Apps → Termux:API → Permissions → Location
```

#### termux-wifi-scaninfo

Scans for nearby WiFi networks.

**Output Fields:**

| Field | Type | Description |
|-------|------|-------------|
| ssid | string | Network name (empty for hidden) |
| bssid | string | Router's MAC address |
| frequency | integer | WiFi frequency in MHz |
| rssi | integer | Signal strength in dBm |
| capabilities | string | Security capabilities |

**Example Output:**
```json
[
  {
    "ssid": "HomeWiFi",
    "bssid": "aa:bb:cc:dd:ee:ff",
    "frequency": 2412,
    "rssi": -45,
    "capabilities": "[WPA2-PSK-CCMP][ESS]"
  },
  {
    "ssid": "",
    "bssid": "11:22:33:44:55:66",
    "frequency": 2437,
    "rssi": -75,
    "capabilities": "[WPA2-PSK-CCMP][ESS]"
  }
]
```

**Frequency to Channel Mapping:**

| Frequency (MHz) | Channel |
|-----------------|---------|
| 2412 | 1 |
| 2417 | 2 |
| 2422 | 3 |
| 2427 | 4 |
| 2432 | 5 |
| 2437 | 6 |
| 2442 | 7 |
| 2447 | 8 |
| 2452 | 9 |
| 2457 | 10 |
| 2462 | 11 |

**Security Capabilities:**

| Capability | Meaning |
|------------|---------|
| WPA2-PSK | WPA2 Personal |
| WPA3-PSK | WPA3 Personal |
| WPA-EAP | WPA Enterprise |
| CCMP | AES encryption |
| TKIP | Legacy encryption (less secure) |
| WPS | WiFi Protected Setup |
| ESS | Extended Service Set |

### 3. WiFi Password Retrieval (Root Required)

#### Method 1: wpa_supplicant.conf (Android 9 and below)

```bash
# Access wpa_supplicant configuration
su -c "cat /data/misc/wifi/wpa_supplicant.conf"

# Output contains:
# network={
#     ssid="NetworkName"
#     psk="Password"
# }
```

#### Method 2: WifiConfigStore.xml (Android 10+)

```bash
# Access WifiConfigStore
su -c "cat /data/misc/wifi/WifiConfigStore.xml"

# Search for PreSharedKey
su -c "cat /data/misc/wifi/WifiConfigStore.xml | grep -A5 'PreSharedKey'"
```

#### Method 3: Using dumpsys

```bash
# Get WiFi configuration
su -c "dumpsys wifi | grep -A20 'Networks'"

# Requires Android 10+ with additional permissions
```

### 4. Mobile Data Control

Android security restrictions prevent direct mobile data toggle from apps. Alternative methods:

#### Method 1: ADB with WRITE_SECURE_SETTINGS

```bash
# Grant permission via ADB (from PC)
adb shell pm grant com.termux android.permission.WRITE_SECURE_SETTINGS

# Then in Termux
settings put global mobile_data 1  # ON
settings put global mobile_data 0  # OFF
```

#### Method 2: Root Command

```bash
# Using su
su -c "svc data enable"   # Enable mobile data
su -c "svc data disable"  # Disable mobile data
```

#### Method 3: Intent to Settings

```bash
# Open mobile data settings
am start -a android.settings.DATA_ROAMING_SETTINGS
```

### 5. Hotspot Control

#### Via Android Settings Intent

```bash
# Open hotspot settings
am start -a android.settings.WIFI_HOTSPOT_SETTINGS
```

#### Root Commands

```bash
# Enable hotspot (root)
su -c "svc wifi disable"  # Disable WiFi first
su -c "ndc softap start wlan0 MyHotspot 12345678"

# Disable hotspot
su -c "ndc softap stop wlan0"
```

#### Check Connected Devices

```bash
# View ARP table
su -c "cat /proc/net/arp"

# Output shows IP and MAC of connected devices
```

### 6. IP Address Information

#### Internal IP Address

```bash
# Using ifconfig
ifconfig wlan0 | grep "inet " | awk '{print $2}'

# Using ip command
ip -f inet addr show wlan0 | grep inet | awk '{print $2}' | cut -d'/' -f1

# Using Termux API
termux-wifi-connectioninfo | jq -r '.ip'
```

#### External IP Address

```bash
# Various services
curl -s ifconfig.me
curl -s icanhazip.com
curl -s ipecho.net/plain
curl -s api.ipify.org
curl -s ident.me

# With location info
curl -s ipinfo.io

# Output:
# {
#   "ip": "1.2.3.4",
#   "hostname": "example.com",
#   "city": "City",
#   "region": "State",
#   "country": "IN",
#   "loc": "28.6,77.2",
#   "org": "ISP Name"
# }
```

#### Gateway IP

```bash
# Default gateway
ip route | grep default | awk '{print $3}'

# All routes
ip route show

# Using route command
route -n | grep '^0.0.0.0'
```

#### DNS Servers

```bash
# Termux DNS
cat /etc/resolv.conf

# Android DNS (root)
su -c "getprop | grep dns"

# Test DNS resolution
dig google.com
nslookup google.com
```

### 7. MAC Address

#### Get WiFi MAC Address

```bash
# Method 1: ifconfig
ifconfig wlan0 | grep -o -E '([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}'

# Method 2: ip command
ip link show wlan0 | grep -o -E '([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}'

# Method 3: Termux API
termux-wifi-connectioninfo | jq -r '.mac'

# Method 4: sysfs (may require root)
cat /sys/class/net/wlan0/address
```

#### MAC Address Format

```
AA:BB:CC:DD:EE:FF

First 3 octets (AA:BB:CC) = OUI (Organizationally Unique Identifier)
Last 3 octets (DD:EE:FF) = Device specific

Example: 00:1A:2B = Apple Inc.
         00:1B:63 = Intel Corporate
```

#### MAC Randomization

Android 10+ uses MAC randomization for privacy. Real MAC address differs from reported MAC.

```bash
# Get real MAC (root required)
su -c "cat /sys/class/net/wlan0/address"

# Factory MAC may be stored in
su -c "cat /efs/wifi/.mac.info"  # Samsung devices
```

### 8. Network Statistics

#### Connection Statistics

```bash
# Network statistics
cat /proc/net/dev

# Specific interface
cat /proc/net/dev | grep wlan0

# Human readable format
ifconfig wlan0
```

#### Active Connections

```bash
# List all connections
netstat -an

# Established connections only
netstat -an | grep ESTABLISHED

# Listening ports
netstat -tunl

# With process info (root)
su -c "netstat -tunlp"
```

#### Network Usage

```bash
# Android network stats
dumpsys netstats

# Summary
dumpsys netstats | grep -A5 "Dev stats"
```

### 9. Creating Network Info Script

```bash
#!/bin/bash
# network-info.sh - Complete network information dashboard

echo "╔══════════════════════════════════════════════════════════════╗"
echo "║              NETWORK INFORMATION DASHBOARD                    ║"
echo "╚══════════════════════════════════════════════════════════════╝"

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m' # No Color

# Function: WiFi Information
wifi_info() {
    echo -e "\n${BLUE}📡 WiFi INFORMATION${NC}"
    echo "─────────────────────────────────"
    
    WIFI_DATA=$(termux-wifi-connectioninfo 2>/dev/null)
    
    if [ -n "$WIFI_DATA" ] && [ "$WIFI_DATA" != "null" ]; then
        SSID=$(echo "$WIFI_DATA" | jq -r '.ssid // "N/A"')
        IP=$(echo "$WIFI_DATA" | jq -r '.ip // "N/A"')
        MAC=$(echo "$WIFI_DATA" | jq -r '.mac // "N/A"')
        RSSI=$(echo "$WIFI_DATA" | jq -r '.rssi // 0')
        SPEED=$(echo "$WIFI_DATA" | jq -r '.link_speed // 0')
        BSSID=$(echo "$WIFI_DATA" | jq -r '.bssid // "N/A"')
        FREQ=$(echo "$WIFI_DATA" | jq -r '.frequency // 0')
        
        # Calculate channel
        if [ "$FREQ" -ge 2412 ] && [ "$FREQ" -le 2484 ]; then
            CHANNEL=$(( ($FREQ - 2407) / 5 ))
        elif [ "$FREQ" -ge 5170 ] && [ "$FREQ" -le 5825 ]; then
            CHANNEL=$(( ($FREQ - 5000) / 5 ))
        else
            CHANNEL="Unknown"
        fi
        
        # Signal quality
        if [ "$RSSI" -ge -50 ]; then
            QUALITY="${GREEN}Excellent${NC}"
        elif [ "$RSSI" -ge -60 ]; then
            QUALITY="${GREEN}Good${NC}"
        elif [ "$RSSI" -ge -70 ]; then
            QUALITY="${YELLOW}Fair${NC}"
        else
            QUALITY="${RED}Weak${NC}"
        fi
        
        echo "  SSID:      $SSID"
        echo "  IP:        $IP"
        echo "  MAC:       $MAC"
        echo "  Signal:    ${RSSI} dBm (${QUALITY})"
        echo "  Speed:     ${SPEED} Mbps"
        echo "  Channel:   $CHANNEL"
        echo "  Router:    $BSSID"
    else
        echo -e "  ${RED}WiFi not connected${NC}"
    fi
}

# Function: Public IP
public_ip() {
    echo -e "\n${BLUE}🌍 PUBLIC IP${NC}"
    echo "─────────────────────────────────"
    
    PUBLIC=$(curl -s --max-time 5 ifconfig.me 2>/dev/null)
    
    if [ -n "$PUBLIC" ]; then
        echo "  Public IP: $PUBLIC"
        
        # Get location info
        INFO=$(curl -s --max-time 5 ipinfo.io 2>/dev/null)
        if [ -n "$INFO" ]; then
            CITY=$(echo "$INFO" | jq -r '.city // "N/A"')
            REGION=$(echo "$INFO" | jq -r '.region // "N/A"')
            COUNTRY=$(echo "$INFO" | jq -r '.country // "N/A"')
            ISP=$(echo "$INFO" | jq -r '.org // "N/A"')
            
            echo "  Location:  $CITY, $REGION, $COUNTRY"
            echo "  ISP:       $ISP"
        fi
    else
        echo -e "  ${RED}Unable to fetch public IP${NC}"
    fi
}

# Function: Network Interfaces
interfaces() {
    echo -e "\n${BLUE}🔌 NETWORK INTERFACES${NC}"
    echo "─────────────────────────────────"
    
    ip link show | grep -E "^[0-9]+" | while read line; do
        IFACE=$(echo "$line" | awk -F: '{print $2}' | tr -d ' ')
        STATE=$(echo "$line" | grep -o 'state [^ ]*' | awk '{print $2}')
        MAC=$(ip link show "$IFACE" | grep -o -E '([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}' | head -1)
        
        if [ "$STATE" = "UP" ]; then
            STATE_COLOR="${GREEN}UP${NC}"
        else
            STATE_COLOR="${RED}DOWN${NC}"
        fi
        
        echo "  $IFACE: ${STATE_COLOR} (${MAC:-N/A})"
    done
}

# Function: Available Networks
available_networks() {
    echo -e "\n${BLUE}📶 NEARBY NETWORKS${NC}"
    echo "─────────────────────────────────"
    
    NETWORKS=$(termux-wifi-scaninfo 2>/dev/null)
    COUNT=$(echo "$NETWORKS" | jq 'length' 2>/dev/null)
    
    echo "  Found: $COUNT networks"
    echo ""
    
    echo "$NETWORKS" | jq -r 'sort_by(.rssi) | reverse | .[] | "[\(.rssi) dBm] \(.ssid // "Hidden")"' 2>/dev/null | head -10
}

# Function: Gateway and DNS
gateway_dns() {
    echo -e "\n${BLUE}🌐 GATEWAY & DNS${NC}"
    echo "─────────────────────────────────"
    
    GATEWAY=$(ip route | grep default | awk '{print $3}' | head -1)
    echo "  Gateway:   ${GATEWAY:-N/A}"
    
    DNS=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}')
    echo "  DNS:       ${DNS:-N/A}"
}

# Main execution
wifi_info
public_ip
interfaces
available_networks
gateway_dns

echo ""
echo "══════════════════════════════════════════════════════════════"
```

### 10. WiFi Analyzer Script

```bash
#!/bin/bash
# wifi-analyzer.sh - Comprehensive WiFi analysis tool

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
PURPLE='\033[0;35m'
CYAN='\033[0;36m'
NC='\033[0m'

# Signal strength indicator
signal_bars() {
    local rssi=$1
    if [ "$rssi" -ge -50 ]; then
        echo "████████ Excellent"
    elif [ "$rssi" -ge -60 ]; then
        echo "██████░░ Good"
    elif [ "$rssi" -ge -70 ]; then
        echo "████░░░░ Fair"
    elif [ "$rssi" -ge -80 ]; then
        echo "██░░░░░░ Weak"
    else
        echo "░░░░░░░░ Very Weak"
    fi
}

# Security analyzer
analyze_security() {
    local caps="$1"
    local result=""
    
    if echo "$caps" | grep -q "WPA3"; then
        result="${GREEN}WPA3${NC}"
    elif echo "$caps" | grep -q "WPA2"; then
        result="${GREEN}WPA2${NC}"
    elif echo "$caps" | grep -q "WPA-PSK"; then
        result="${YELLOW}WPA${NC}"
    else
        result="${RED}Open/WEP${NC}"
    fi
    
    if echo "$caps" | grep -q "WPS"; then
        result="$result ${YELLOW}[WPS]${NC}"
    fi
    
    echo "$result"
}

# Channel analysis
channel_analysis() {
    local freq=$1
    local channel
    
    # 2.4 GHz
    if [ "$freq" -ge 2412 ] && [ "$freq" -le 2484 ]; then
        channel=$(( ($freq - 2407) / 5 ))
        echo "$channel (2.4 GHz)"
    # 5 GHz
    elif [ "$freq" -ge 5170 ] && [ "$freq" -le 5825 ]; then
        channel=$(( ($freq - 5000) / 5 ))
        echo "$channel (5 GHz)"
    else
        echo "Unknown"
    fi
}

echo -e "${PURPLE}"
echo "╔══════════════════════════════════════════════════════════════╗"
echo "║                    WIFI ANALYZER v1.0                         ║"
echo "║                    by T3rmuxk1ng                              ║"
echo "╚══════════════════════════════════════════════════════════════╝"
echo -e "${NC}"

# Scan networks
echo -e "${CYAN}[*] Scanning WiFi networks...${NC}"
NETWORKS=$(termux-wifi-scaninfo 2>/dev/null)

if [ -z "$NETWORKS" ] || [ "$NETWORKS" = "[]" ]; then
    echo -e "${RED}[!] No networks found. Make sure WiFi is enabled.${NC}"
    exit 1
fi

TOTAL=$(echo "$NETWORKS" | jq 'length')
echo -e "${GREEN}[+] Found $TOTAL networks${NC}"

# Statistics
echo -e "\n${BLUE}══════════════════════════════════════════════════════════════${NC}"
echo -e "${BLUE}📊 NETWORK STATISTICS${NC}"
echo -e "${BLUE}══════════════════════════════════════════════════════════════${NC}"

WPA3=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA3"))] | length')
WPA2=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA2") and contains("WPA3") | not)] | length')
WPA=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA-PSK") and contains("WPA2") | not)] | length')
OPEN=$(echo "$NETWORKS" | jq '[.[] | select((.capabilities | contains("ESS")) and (.capabilities | contains("WPA") | not))] | length')
WPS=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPS"))] | length')
HIDDEN=$(echo "$NETWORKS" | jq '[.[] | select(.ssid == "")] | length')

echo ""
echo -e "  Total Networks:     $TOTAL"
echo -e "  WPA3 Secured:       ${GREEN}$WPA3${NC}"
echo -e "  WPA2 Secured:       ${GREEN}$WPA2${NC}"
echo -e "  WPA Secured:        ${YELLOW}$WPA${NC}"
echo -e "  Open Networks:      ${RED}$OPEN${NC}"
echo -e "  WPS Enabled:        ${YELLOW}$WPS${NC} ⚠️"
echo -e "  Hidden Networks:    $HIDDEN"

# Channel Distribution
echo -e "\n${BLUE}══════════════════════════════════════════════════════════════${NC}"
echo -e "${BLUE}📡 CHANNEL DISTRIBUTION${NC}"
echo -e "${BLUE}══════════════════════════════════════════════════════════════${NC}"

# 2.4 GHz channels
echo ""
echo "  2.4 GHz Band:"
for ch in 1 2 3 4 5 6 7 8 9 10 11; do
    FREQ=$((2407 + ch * 5))
    COUNT=$(echo "$NETWORKS" | jq "[.[] | select(.frequency == $FREQ)] | length")
    if [ "$COUNT" -gt 0 ]; then
        BAR=$(printf '█%.0s' $(seq 1 $COUNT))
        echo "    Channel $ch: ${GREEN}$BAR${NC} ($COUNT)"
    fi
done

# Network Details
echo -e "\n${BLUE}══════════════════════════════════════════════════════════════${NC}"
echo -e "${BLUE}📶 NETWORK DETAILS (Sorted by Signal)${NC}"
echo -e "${BLUE}══════════════════════════════════════════════════════════════${NC}"

echo ""
printf "  %-25s %-8s %-12s %s\n" "SSID" "Signal" "Security" "Channel"
echo "  ─────────────────────────────────────────────────────────────"

echo "$NETWORKS" | jq -r 'sort_by(.rssi) | reverse | .[] | @base64' | while read NET_B64; do
    NET=$(echo "$NET_B64" | base64 -d)
    SSID=$(echo "$NET" | jq -r '.ssid // "Hidden"')
    RSSI=$(echo "$NET" | jq -r '.rssi')
    CAPS=$(echo "$NET" | jq -r '.capabilities')
    FREQ=$(echo "$NET" | jq -r '.frequency')
    
    # Truncate long SSIDs
    SSID_DISPLAY="${SSID:0:22}"
    [ ${#SSID} -gt 22 ] && SSID_DISPLAY="${SSID_DISPLAY}..."
    
    SECURITY=$(analyze_security "$CAPS")
    CHANNEL=$(channel_analysis "$FREQ")
    BARS=$(signal_bars "$RSSI")
    
    printf "  %-25s %4d dBm   %-20s %s\n" "$SSID_DISPLAY" "$RSSI" "$(echo -e $SECURITY)" "$CHANNEL"
done

# Security Warnings
if [ "$WPS" -gt 0 ]; then
    echo -e "\n${YELLOW}══════════════════════════════════════════════════════════════${NC}"
    echo -e "${YELLOW}⚠️  SECURITY WARNING${NC}"
    echo -e "${YELLOW}══════════════════════════════════════════════════════════════${NC}"
    echo -e "${YELLOW}$WPS networks have WPS enabled, which is vulnerable to${NC}"
    echo -e "${YELLOW}brute force attacks. Consider disabling WPS on your router.${NC}"
    echo ""
    echo -e "${YELLOW}Networks with WPS:${NC}"
    echo "$NETWORKS" | jq -r '.[] | select(.capabilities | contains("WPS")) | "  - \(.ssid // "Hidden")"' | head -10
fi

if [ "$OPEN" -gt 0 ]; then
    echo -e "\n${RED}══════════════════════════════════════════════════════════════${NC}"
    echo -e "${RED}⚠️  OPEN NETWORK DETECTED${NC}"
    echo -e "${RED}══════════════════════════════════════════════════════════════${NC}"
    echo -e "${RED}$OPEN open networks detected. Avoid sending sensitive data${NC}"
    echo -e "${RED}over unsecured connections.${NC}"
fi

echo -e "\n${GREEN}══════════════════════════════════════════════════════════════${NC}"
echo -e "${GREEN}Scan Complete${NC}"
```

### 11. Network Monitoring Script

```bash
#!/bin/bash
# network-monitor.sh - Continuous network monitoring

# Configuration
INTERVAL=5
LOG_DIR="$HOME/network_logs"
LOG_FILE="$LOG_DIR/monitor_$(date +%Y%m%d_%H%M%S).log"
ALERT_THRESHOLD=-75  # Alert if signal weaker than this

# Create log directory
mkdir -p "$LOG_DIR"

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m'

# Signal quality indicator
get_quality() {
    local rssi=$1
    if [ "$rssi" -ge -50 ]; then echo "${GREEN}████████${NC}"
    elif [ "$rssi" -ge -60 ]; then echo "${GREEN}██████${NC}░░"
    elif [ "$rssi" -ge -70 ]; then echo "${YELLOW}████${NC}░░░░"
    elif [ "$rssi" -ge -80 ]; then echo "${RED}██${NC}░░░░░░"
    else echo "${RED}░░░░░░░░${NC}"
    fi
}

# Log function
log() {
    local message="$1"
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    echo "[$timestamp] $message" >> "$LOG_FILE"
}

# Alert function
alert() {
    local message="$1"
    echo -e "${RED}[ALERT] $message${NC}"
    log "ALERT: $message"
    
    # Optional: Send notification
    termux-notification --title "Network Alert" --content "$message" --sound
}

# Graceful exit
cleanup() {
    echo -e "\n${YELLOW}Stopping network monitor...${NC}"
    log "Monitor stopped by user"
    echo "Log saved to: $LOG_FILE"
    exit 0
}

trap cleanup SIGINT SIGTERM

# Display header
echo "╔══════════════════════════════════════════════════════════════╗"
echo "║                  NETWORK MONITOR v1.0                        ║"
echo "║                  by T3rmuxk1ng                               ║"
echo "╚══════════════════════════════════════════════════════════════╝"
echo ""
echo "📊 Monitoring interval: ${INTERVAL}s"
echo "📝 Log file: $LOG_FILE"
echo "⚠️  Alert threshold: ${ALERT_THRESHOLD} dBm"
echo ""
echo "Press Ctrl+C to stop"
echo ""

log "Monitor started"

# Previous state tracking
PREV_SSID=""
PREV_RSSI=0

# Main monitoring loop
while true; do
    TIMESTAMP=$(date '+%H:%M:%S')
    
    # Get WiFi info
    WIFI_DATA=$(termux-wifi-connectioninfo 2>/dev/null)
    
    if [ -n "$WIFI_DATA" ] && [ "$WIFI_DATA" != "null" ]; then
        SSID=$(echo "$WIFI_DATA" | jq -r '.ssid // "Unknown"')
        IP=$(echo "$WIFI_DATA" | jq -r '.ip // "N/A"')
        RSSI=$(echo "$WIFI_DATA" | jq -r '.rssi // 0')
        SPEED=$(echo "$WIFI_DATA" | jq -r '.link_speed // 0')
        
        QUALITY=$(get_quality "$RSSI")
        
        # Check for network change
        if [ "$SSID" != "$PREV_SSID" ]; then
            if [ -n "$PREV_SSID" ]; then
                alert "Network changed: $PREV_SSID → $SSID"
            fi
            PREV_SSID="$SSID"
        fi
        
        # Check signal strength
        if [ "$RSSI" -lt "$ALERT_THRESHOLD" ]; then
            alert "Weak signal: ${RSSI} dBm on $SSID"
        fi
        
        # Display status
        echo -ne "\r[$TIMESTAMP] 📶 $SSID | ${QUALITY} ${RSSI}dBm | 🚀 ${SPEED}Mbps | 🌐 $IP   "
        
        # Log data
        log "SSID=$SSID RSSI=$RSSI SPEED=$SPEED IP=$IP"
        
    else
        echo -ne "\r[$TIMESTAMP] ❌ WiFi Disconnected                                      "
        log "WiFi Disconnected"
        
        # Alert on disconnection
        if [ -n "$PREV_SSID" ]; then
            alert "Disconnected from $PREV_SSID"
            PREV_SSID=""
        fi
    fi
    
    sleep "$INTERVAL"
done
```

### 12. Python Integration

#### Basic Network Module

```python
#!/usr/bin/env python3
"""
Termux Network Module
Provides network information and control functions
"""

import subprocess
import json
import re
from typing import Dict, List, Optional

class TermuxNetwork:
    """Termux Network API wrapper"""
    
    @staticmethod
    def run_command(cmd: List[str]) -> str:
        """Execute a command and return output"""
        try:
            result = subprocess.run(
                cmd,
                capture_output=True,
                text=True,
                timeout=30
            )
            return result.stdout.strip()
        except subprocess.TimeoutExpired:
            return ""
        except Exception as e:
            print(f"Error: {e}")
            return ""
    
    @staticmethod
    def run_json_command(cmd: List[str]) -> Optional[dict]:
        """Execute command and parse JSON output"""
        output = TermuxNetwork.run_command(cmd)
        if output:
            try:
                return json.loads(output)
            except json.JSONDecodeError:
                return None
        return None
    
    @staticmethod
    def get_wifi_info() -> Optional[Dict]:
        """Get current WiFi connection information"""
        return TermuxNetwork.run_json_command(['termux-wifi-connectioninfo'])
    
    @staticmethod
    def enable_wifi() -> bool:
        """Enable WiFi"""
        result = TermuxNetwork.run_command(['termux-wifi-enable', 'true'])
        return True
    
    @staticmethod
    def disable_wifi() -> bool:
        """Disable WiFi"""
        result = TermuxNetwork.run_command(['termux-wifi-enable', 'false'])
        return True
    
    @staticmethod
    def scan_networks() -> List[Dict]:
        """Scan for available WiFi networks"""
        result = TermuxNetwork.run_json_command(['termux-wifi-scaninfo'])
        return result if result else []
    
    @staticmethod
    def get_local_ip() -> Optional[str]:
        """Get local IP address"""
        wifi_info = TermuxNetwork.get_wifi_info()
        if wifi_info:
            return wifi_info.get('ip')
        return None
    
    @staticmethod
    def get_public_ip() -> Optional[str]:
        """Get public IP address"""
        return TermuxNetwork.run_command(['curl', '-s', '--max-time', '5', 'ifconfig.me']) or None
    
    @staticmethod
    def get_mac_address() -> Optional[str]:
        """Get WiFi MAC address"""
        wifi_info = TermuxNetwork.get_wifi_info()
        if wifi_info:
            return wifi_info.get('mac')
        return None
    
    @staticmethod
    def get_signal_strength() -> Optional[int]:
        """Get WiFi signal strength in dBm"""
        wifi_info = TermuxNetwork.get_wifi_info()
        if wifi_info:
            return wifi_info.get('rssi')
        return None
    
    @staticmethod
    def get_signal_quality() -> str:
        """Get signal quality as text"""
        rssi = TermuxNetwork.get_signal_strength()
        if rssi is None:
            return "Unknown"
        if rssi >= -50:
            return "Excellent"
        elif rssi >= -60:
            return "Good"
        elif rssi >= -70:
            return "Fair"
        elif rssi >= -80:
            return "Weak"
        else:
            return "Very Weak"
    
    @staticmethod
    def get_gateway() -> Optional[str]:
        """Get default gateway IP"""
        output = TermuxNetwork.run_command(['ip', 'route'])
        if output:
            match = re.search(r'default via (\S+)', output)
            if match:
                return match.group(1)
        return None
    
    @staticmethod
    def get_dns_servers() -> List[str]:
        """Get DNS servers"""
        output = TermuxNetwork.run_command(['cat', '/etc/resolv.conf'])
        servers = []
        if output:
            for line in output.split('\n'):
                if line.startswith('nameserver'):
                    parts = line.split()
                    if len(parts) >= 2:
                        servers.append(parts[1])
        return servers
    
    @staticmethod
    def ping(host: str = "google.com", count: int = 4) -> Dict:
        """Ping a host and return statistics"""
        output = TermuxNetwork.run_command(['ping', '-c', str(count), host])
        
        result = {
            'host': host,
            'packets_sent': count,
            'packets_received': 0,
            'packet_loss': 100.0,
            'avg_latency': None,
            'success': False
        }
        
        if output:
            # Parse packet loss
            loss_match = re.search(r'(\d+)% packet loss', output)
            if loss_match:
                result['packet_loss'] = float(loss_match.group(1))
                result['packets_received'] = count - int(count * result['packet_loss'] / 100)
            
            # Parse latency
            latency_match = re.search(r'rtt min/avg/max/mdev = [\d.]+/([\d.]+)/', output)
            if latency_match:
                result['avg_latency'] = float(latency_match.group(1))
            
            result['success'] = result['packet_loss'] < 100
        
        return result


class WiFiSecurity:
    """WiFi Security Analysis"""
    
    @staticmethod
    def analyze_capabilities(capabilities: str) -> Dict:
        """Analyze security capabilities"""
        return {
            'wpa3': 'WPA3' in capabilities,
            'wpa2': 'WPA2' in capabilities,
            'wpa': 'WPA-PSK' in capabilities and 'WPA2' not in capabilities,
            'wps': 'WPS' in capabilities,
            'open': 'ESS' in capabilities and 'WPA' not in capabilities,
            'ccmp': 'CCMP' in capabilities,  # AES
            'tkip': 'TKIP' in capabilities,  # Legacy
        }
    
    @staticmethod
    def get_risk_level(capabilities: str) -> str:
        """Get security risk level"""
        sec = WiFiSecurity.analyze_capabilities(capabilities)
        
        if sec['open']:
            return "HIGH - Open network"
        elif sec['wps']:
            return "MEDIUM - WPS enabled"
        elif sec['wpa'] and not sec['wpa2']:
            return "MEDIUM - Outdated WPA"
        elif sec['wpa2']:
            return "LOW - WPA2 secure"
        elif sec['wpa3']:
            return "MINIMAL - WPA3 secure"
        else:
            return "UNKNOWN"
    
    @staticmethod
    def get_security_score(capabilities: str) -> int:
        """Get security score (0-100)"""
        sec = WiFiSecurity.analyze_capabilities(capabilities)
        
        score = 0
        if sec['wpa3']:
            score = 100
        elif sec['wpa2']:
            score = 80
        elif sec['wpa']:
            score = 50
        
        # Deductions
        if sec['wps']:
            score -= 20
        if sec['tkip']:
            score -= 10
        
        return max(0, score)


# Example usage
if __name__ == "__main__":
    net = TermuxNetwork()
    
    print("═" * 50)
    print("     TERMUX NETWORK MODULE DEMO")
    print("═" * 50)
    
    # WiFi Info
    wifi = net.get_wifi_info()
    if wifi:
        print(f"\n📡 WiFi: {wifi.get('ssid', 'N/A')}")
        print(f"   IP: {wifi.get('ip', 'N/A')}")
        print(f"   Signal: {net.get_signal_quality()} ({wifi.get('rssi', 'N/A')} dBm)")
    
    # Public IP
    print(f"\n🌍 Public IP: {net.get_public_ip() or 'N/A'}")
    
    # Gateway
    print(f"\n🚪 Gateway: {net.get_gateway() or 'N/A'}")
    
    # DNS
    dns = net.get_dns_servers()
    print(f"\n📖 DNS: {', '.join(dns) or 'N/A'}")
    
    # Ping test
    ping = net.ping('google.com', 3)
    print(f"\n🏓 Ping: {ping['avg_latency'] or 'N/A'}ms (Loss: {ping['packet_loss']}%)")
    
    # Network scan
    networks = net.scan_networks()
    print(f"\n📶 Networks found: {len(networks)}")
    
    # Security analysis
    if networks:
        print("\n🔒 Security Analysis:")
        for net_data in networks[:5]:
            ssid = net_data.get('ssid') or 'Hidden'
            caps = net_data.get('capabilities', '')
            risk = WiFiSecurity.get_risk_level(caps)
            score = WiFiSecurity.get_security_score(caps)
            print(f"   {ssid}: {risk} (Score: {score}/100)")
```

### 13. 20+ Practical Examples

```bash
# ═══════════════════════════════════════════════════════════════
# WIFI INFORMATION EXAMPLES
# ═══════════════════════════════════════════════════════════════

# 1. Get current WiFi SSID
termux-wifi-connectioninfo | jq -r '.ssid'

# 2. Get current local IP
termux-wifi-connectioninfo | jq -r '.ip'

# 3. Get WiFi MAC address
termux-wifi-connectioninfo | jq -r '.mac'

# 4. Get signal strength in dBm
termux-wifi-connectioninfo | jq '.rssi'

# 5. Get connection speed
termux-wifi-connectioninfo | jq '.link_speed'

# 6. Get router MAC (BSSID)
termux-wifi-connectioninfo | jq -r '.bssid'

# 7. Get complete WiFi info as JSON
termux-wifi-connectioninfo

# ═══════════════════════════════════════════════════════════════
# WIFI CONTROL EXAMPLES
# ═══════════════════════════════════════════════════════════════

# 8. Turn WiFi ON
termux-wifi-enable true

# 9. Turn WiFi OFF
termux-wifi-enable false

# 10. WiFi toggle script
[ -z "$(termux-wifi-connectioninfo 2>/dev/null)" ] && termux-wifi-enable true || termux-wifi-enable false

# ═══════════════════════════════════════════════════════════════
# WIFI SCANNING EXAMPLES
# ═══════════════════════════════════════════════════════════════

# 11. Scan all networks
termux-wifi-scaninfo

# 12. Count available networks
termux-wifi-scaninfo | jq 'length'

# 13. List all SSIDs sorted
termux-wifi-scaninfo | jq -r '.[].ssid' | sort | uniq

# 14. Find strongest network
termux-wifi-scaninfo | jq 'sort_by(.rssi) | reverse | .[0]'

# 15. Find open networks (no password)
termux-wifi-scaninfo | jq '.[] | select(.capabilities | contains("ESS") and contains("WPA") | not)'

# 16. Find WPS enabled networks (vulnerable)
termux-wifi-scaninfo | jq '.[] | select(.capabilities | contains("WPS"))'

# 17. Find WPA3 networks
termux-wifi-scaninfo | jq '.[] | select(.capabilities | contains("WPA3"))'

# 18. Find specific network by name
termux-wifi-scaninfo | jq '.[] | select(.ssid | contains("MyNetwork"))'

# 19. Get top 5 strongest networks
termux-wifi-scaninfo | jq 'sort_by(.rssi) | reverse | .[0:5]'

# 20. List networks with signal strength
termux-wifi-scaninfo | jq -r '.[] | "\(.ssid // "Hidden"): \(.rssi) dBm"'

# ═══════════════════════════════════════════════════════════════
# IP ADDRESS EXAMPLES
# ═══════════════════════════════════════════════════════════════

# 21. Get public IP address
curl -s ifconfig.me

# 22. Get public IP with location
curl -s ipinfo.io

# 23. Get local IP via ifconfig
ifconfig wlan0 | grep "inet " | awk '{print $2}'

# 24. Get local IP via ip command
ip -f inet addr show wlan0 | grep inet | awk '{print $2}' | cut -d'/' -f1

# 25. Get default gateway
ip route | grep default | awk '{print $3}'

# 26. Get all IP addresses
hostname -I

# ═══════════════════════════════════════════════════════════════
# MAC ADDRESS EXAMPLES
# ═══════════════════════════════════════════════════════════════

# 27. Get WiFi MAC address
ifconfig wlan0 | grep -o -E '([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}'

# 28. Get MAC via ip command
ip link show wlan0 | grep -o -E '([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}'

# 29. Get MAC via sysfs
cat /sys/class/net/wlan0/address

# ═══════════════════════════════════════════════════════════════
# NETWORK DIAGNOSTICS EXAMPLES
# ═══════════════════════════════════════════════════════════════

# 30. Ping test
ping -c 4 google.com

# 31. DNS lookup
nslookup google.com

# 32. Check open ports locally
netstat -tunl

# 33. List active connections
netstat -tun | grep ESTABLISHED

# 34. Check network interfaces
ip link show

# 35. Check routing table
ip route show

# 36. DNS server check
cat /etc/resolv.conf

# 37. Quick speed test
curl -o /dev/null -w "Speed: %{speed_download} bytes/sec\n" http://speedtest.tele2.net/1MB.zip

# 38. Network scan with nmap
nmap -sP 192.168.1.0/24

# 39. Port scan specific host
nmap -p 80,443,22 192.168.1.1

# 40. Check internet connectivity
curl -Is http://google.com | head -1

# ═══════════════════════════════════════════════════════════════
# UTILITY EXAMPLES
# ═══════════════════════════════════════════════════════════════

# 41. Check if connected to WiFi
[ -n "$(termux-wifi-connectioninfo 2>/dev/null)" ] && echo "Connected" || echo "Disconnected"

# 42. Monitor WiFi signal (continuous)
watch -n 2 'termux-wifi-connectioninfo | jq ".rssi"'

# 43. Export network scan to file
termux-wifi-scaninfo > networks_$(date +%Y%m%d_%H%M%S).json

# 44. Create QR code for WiFi sharing
qrencode -t ANSIUTF8 "WIFI:T:WPA;S:NetworkName;P:Password;;"

# 45. Check signal quality
RSSI=$(termux-wifi-connectioninfo | jq '.rssi'); [ $RSSI -gt -70 ] && echo "Good Signal" || echo "Weak Signal"

# 46. Count networks by security type
echo "WPA3: $(termux-wifi-scaninfo | jq '[.[] | select(.capabilities | contains("WPA3"))] | length')"
echo "WPA2: $(termux-wifi-scaninfo | jq '[.[] | select(.capabilities | contains("WPA2"))] | length')"
echo "Open: $(termux-wifi-scaninfo | jq '[.[] | select(.capabilities | contains("ESS") and contains("WPA") | not)] | length')"

# 47. Get channel from frequency
FREQ=$(termux-wifi-connectioninfo | jq '.frequency'); CHANNEL=$(( ($FREQ - 2407) / 5 )); echo "Channel: $CHANNEL"

# 48. Check if specific network is available
termux-wifi-scaninfo | jq -e '.[] | select(.ssid == "MyNetwork")' > /dev/null && echo "Available" || echo "Not found"

# 49. Get network statistics
echo "Networks: $(termux-wifi-scaninfo | jq 'length')"
echo "Connected: $(termux-wifi-connectioninfo | jq -r '.ssid // "None"')"
echo "IP: $(termux-wifi-connectioninfo | jq -r '.ip // "None"')"

# 50. Log network info with timestamp
echo "$(date '+%Y-%m-%d %H:%M:%S') | SSID: $(termux-wifi-connectioninfo | jq -r '.ssid') | IP: $(termux-wifi-connectioninfo | jq -r '.ip') | Signal: $(termux-wifi-connectioninfo | jq '.rssi') dBm" >> network_log.txt
```

---

## 📋 COMMANDS REFERENCE

### Termux API Network Commands

```bash
# WiFi Information
termux-wifi-connectioninfo         # Current WiFi connection details
termux-wifi-connectioninfo | jq    # Parsed JSON output

# WiFi Control
termux-wifi-enable true            # Turn WiFi ON
termux-wifi-enable false           # Turn WiFi OFF

# WiFi Scanning
termux-wifi-scaninfo               # Scan nearby networks
termux-wifi-scaninfo | jq          # Parsed JSON output
```

### Network Interface Commands

```bash
# List interfaces
ip link show
ifconfig -a

# Interface details
ip addr show wlan0
ifconfig wlan0

# Interface statistics
ip -s link show wlan0
cat /proc/net/dev
```

### IP Address Commands

```bash
# Local IP
ip addr show wlan0 | grep inet
hostname -I
ifconfig wlan0 | grep "inet "

# Public IP
curl -s ifconfig.me
curl -s icanhazip.com
curl -s api.ipify.org

# With details
curl -s ipinfo.io
```

### Routing Commands

```bash
# Show routing table
ip route show
route -n

# Default gateway
ip route | grep default

# Add/remove routes
ip route add default via 192.168.1.1
ip route del default
```

### DNS Commands

```bash
# DNS servers
cat /etc/resolv.conf

# DNS lookup
nslookup google.com
dig google.com
host google.com

# Flush DNS (root)
su -c "ndc resolver clearnetdns wlan0"
```

### Connectivity Testing

```bash
# Ping
ping -c 4 google.com
ping -c 4 8.8.8.8

# Port check
nc -zv google.com 80
nc -zv google.com 443

# HTTP check
curl -Is http://google.com | head -1
curl -I https://google.com
```

### Network Statistics

```bash
# Active connections
netstat -an
netstat -tunl
netstat -tun

# Network usage
cat /proc/net/dev
ifconfig wlan0

# Connection tracking (root)
su -c "cat /proc/net/nf_conntrack"
```

### Network Scanning

```bash
# Host discovery
nmap -sP 192.168.1.0/24

# Port scan
nmap -p 22,80,443 192.168.1.1

# Service detection
nmap -sV 192.168.1.1

# OS detection (root)
su -c "nmap -O 192.168.1.1"
```

### MAC Address Commands

```bash
# Get MAC
ip link show wlan0 | grep ether
ifconfig wlan0 | grep -o -E '([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}'
cat /sys/class/net/wlan0/address

# Change MAC (root)
su -c "ifconfig wlan0 down"
su -c "ifconfig wlan0 hw ether 00:11:22:33:44:55"
su -c "ifconfig wlan0 up"
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic WiFi Information

```bash
# Task: Get complete WiFi information and save to file

# Step 1: Get WiFi connection info
termux-wifi-connectioninfo

# Step 2: Parse and display specific fields
echo "SSID: $(termux-wifi-connectioninfo | jq -r '.ssid')"
echo "IP: $(termux-wifi-connectioninfo | jq -r '.ip')"
echo "MAC: $(termux-wifi-connectioninfo | jq -r '.mac')"
echo "Signal: $(termux-wifi-connectioninfo | jq '.rssi') dBm"

# Step 3: Save to file
termux-wifi-connectioninfo > wifi_info.json

# Step 4: Verify
cat wifi_info.json | jq .
```

### Exercise 2: Network Scanner

```bash
# Task: Create a network scanning script

# Step 1: Scan networks
NETWORKS=$(termux-wifi-scaninfo)

# Step 2: Count total
echo "Total networks: $(echo "$NETWORKS" | jq 'length')"

# Step 3: List by signal strength
echo "$NETWORKS" | jq -r 'sort_by(.rssi) | reverse | .[] | "[\(.rssi) dBm] \(.ssid // "Hidden")"'

# Step 4: Count by security
echo "WPA3: $(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA3"))] | length')"
echo "WPA2: $(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA2"))] | length')"
echo "Open: $(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("ESS") and contains("WPA") | not)] | length')"

# Step 5: Save scan results
echo "$NETWORKS" > network_scan_$(date +%Y%m%d).json
```

### Exercise 3: Network Dashboard

```bash
# Task: Create a complete network dashboard script

cat > ~/network_dashboard.sh << 'EOF'
#!/bin/bash

echo "╔════════════════════════════════════════════════╗"
echo "║         NETWORK DASHBOARD                      ║"
echo "╚════════════════════════════════════════════════╝"

# WiFi Status
WIFI=$(termux-wifi-connectioninfo 2>/dev/null)
if [ -n "$WIFI" ]; then
    echo ""
    echo "📡 WiFi: $(echo $WIFI | jq -r '.ssid')"
    echo "   IP: $(echo $WIFI | jq -r '.ip')"
    echo "   Signal: $(echo $WIFI | jq '.rssi') dBm"
else
    echo ""
    echo "📡 WiFi: Not Connected"
fi

# Public IP
echo ""
echo "🌍 Public IP: $(curl -s --max-time 5 ifconfig.me)"

# Gateway
echo ""
echo "🚪 Gateway: $(ip route | grep default | awk '{print $3}')"

# DNS
echo ""
echo "📖 DNS: $(cat /etc/resolv.conf | grep nameserver | awk '{print $2}' | head -1)"

# Network count
echo ""
echo "📶 Nearby Networks: $(termux-wifi-scaninfo 2>/dev/null | jq 'length')"
EOF

chmod +x ~/network_dashboard.sh
./network_dashboard.sh
```

### Exercise 4: Signal Monitor

```bash
# Task: Create a signal strength monitor

cat > ~/signal_monitor.sh << 'EOF'
#!/bin/bash

echo "WiFi Signal Monitor"
echo "Press Ctrl+C to stop"
echo ""

while true; do
    INFO=$(termux-wifi-connectioninfo 2>/dev/null)
    if [ -n "$INFO" ]; then
        RSSI=$(echo "$INFO" | jq '.rssi')
        SSID=$(echo "$INFO" | jq -r '.ssid')
        
        # Signal bars
        if [ "$RSSI" -ge -50 ]; then
            BARS="████████"
        elif [ "$RSSI" -ge -60 ]; then
            BARS="██████░░"
        elif [ "$RSSI" -ge -70 ]; then
            BARS="████░░░░"
        else
            BARS="██░░░░░░"
        fi
        
        echo -ne "\r[$(date +%H:%M:%S)] $SSID: $BARS ${RSSI}dBm   "
    else
        echo -ne "\r[$(date +%H:%M:%S)] WiFi Disconnected           "
    fi
    sleep 2
done
EOF

chmod +x ~/signal_monitor.sh
./signal_monitor.sh
```

### Exercise 5: Network Security Audit

```bash
# Task: Perform a network security audit

cat > ~/security_audit.sh << 'EOF'
#!/bin/bash

echo "🔒 NETWORK SECURITY AUDIT"
echo "════════════════════════════════════════"

# Current network security
CURRENT=$(termux-wifi-connectioninfo 2>/dev/null)
if [ -n "$CURRENT" ]; then
    echo ""
    echo "Current Network: $(echo $CURRENT | jq -r '.ssid')"
    echo "Local IP: $(echo $CURRENT | jq -r '.ip')"
    echo "MAC: $(echo $CURRENT | jq -r '.mac')"
fi

# Scan and analyze
echo ""
echo "Scanning networks..."
NETWORKS=$(termux-wifi-scaninfo)

# Security statistics
TOTAL=$(echo "$NETWORKS" | jq 'length')
WPA3=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA3"))] | length')
WPA2=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPA2") and contains("WPA3") | not)] | length')
WPS=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("WPS"))] | length')
OPEN=$(echo "$NETWORKS" | jq '[.[] | select(.capabilities | contains("ESS") and contains("WPA") | not)] | length')

echo ""
echo "📊 SECURITY SUMMARY"
echo "─────────────────────"
echo "Total Networks: $TOTAL"
echo "WPA3 (Secure): $WPA3"
echo "WPA2 (Secure): $WPA2"
echo "WPS Enabled: $WPS ⚠️"
echo "Open Networks: $OPEN ⚠️"

# Warnings
if [ "$WPS" -gt 0 ]; then
    echo ""
    echo "⚠️  WARNING: $WPS networks have WPS enabled"
    echo "WPS is vulnerable to brute force attacks"
fi

if [ "$OPEN" -gt 0 ]; then
    echo ""
    echo "⚠️  WARNING: $OPEN open networks detected"
    echo "Avoid transmitting sensitive data on open networks"
fi

echo ""
echo "════════════════════════════════════════"
EOF

chmod +x ~/security_audit.sh
./security_audit.sh
```

### Exercise 6: Python Network Tool

```bash
# Task: Create a Python network information tool

cat > ~/nettool.py << 'EOF'
#!/usr/bin/env python3
import subprocess
import json

def run_cmd(cmd):
    try:
        result = subprocess.run(cmd, capture_output=True, text=True, timeout=30)
        return result.stdout.strip()
    except:
        return ""

def get_wifi_info():
    output = run_cmd(['termux-wifi-connectioninfo'])
    if output:
        return json.loads(output)
    return {}

def get_public_ip():
    return run_cmd(['curl', '-s', '--max-time', '5', 'ifconfig.me'])

def scan_networks():
    output = run_cmd(['termux-wifi-scaninfo'])
    if output:
        return json.loads(output)
    return []

if __name__ == "__main__":
    print("═" * 45)
    print("     NETWORK TOOL (Python)")
    print("═" * 45)
    
    # WiFi info
    wifi = get_wifi_info()
    if wifi:
        print(f"\n📡 WiFi: {wifi.get('ssid', 'N/A')}")
        print(f"   IP: {wifi.get('ip', 'N/A')}")
        print(f"   Signal: {wifi.get('rssi', 'N/A')} dBm")
    else:
        print("\n📡 WiFi: Not connected")
    
    # Public IP
    print(f"\n🌍 Public IP: {get_public_ip() or 'N/A'}")
    
    # Networks
    networks = scan_networks()
    print(f"\n📶 Networks: {len(networks)}")
EOF

chmod +x ~/nettool.py
python ~/nettool.py
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "termux-wifi-connectioninfo: command not found"

```bash
# Cause: Termux API not installed

# Solution 1: Install Termux API package
pkg install termux-api -y

# Solution 2: Ensure Termux:API app is installed
# Download from F-Droid (not Play Store)
# https://f-droid.org/packages/com.termux.api/

# Solution 3: Check installation
which termux-wifi-connectioninfo
# Should output: /data/data/com.termux/files/usr/bin/termux-wifi-connectioninfo
```

### Problem 2: "Permission denied" for WiFi operations

```bash
# Cause: Location permission not granted (Android 10+)

# Solution 1: Request permission
termux-location
# Accept the permission popup

# Solution 2: Manual permission grant
# Settings → Apps → Termux:API → Permissions → Location → Allow

# Solution 3: Check permission
dumpsys package com.termux.api | grep permission
```

### Problem 3: WiFi scan returns empty or error

```bash
# Cause: WiFi disabled or scanning restrictions

# Solution 1: Enable WiFi first
termux-wifi-enable true

# Solution 2: Wait for scan to complete
# Android may throttle scan requests
sleep 5
termux-wifi-scaninfo

# Solution 3: Check location services
# Location must be ON for WiFi scanning on Android 10+
# Settings → Location → ON

# Solution 4: Check WiFi state
settings get global wifi_on
# Should return "1" if WiFi is on
```

### Problem 4: WiFi enable/disable not working

```bash
# Cause: Missing permissions or restrictions

# Solution 1: Grant location permission
termux-location

# Solution 2: Check Termux:API app permissions
# Settings → Apps → Termux:API → Permissions
# Grant all available permissions

# Solution 3: For Android 12+, check if Termux:API can change system settings
# Settings → Apps → Termux:API → Modify system settings → Allow

# Solution 4: Use alternative via settings intent
am start -a android.settings.WIFI_SETTINGS
```

### Problem 5: Cannot get MAC address

```bash
# Cause: MAC randomization on Android 10+

# Solution 1: Get randomized MAC (what apps see)
termux-wifi-connectioninfo | jq -r '.mac'

# Solution 2: Get real MAC (root required)
su -c "cat /sys/class/net/wlan0/address"

# Solution 3: Use ifconfig (may show randomized)
ifconfig wlan0 | grep -o -E '([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}'

# Note: Android 10+ uses MAC randomization for privacy
# Real MAC may differ from what's reported
```

### Problem 6: Public IP not fetching

```bash
# Cause: Network issues or service unavailable

# Solution 1: Check internet connectivity
ping -c 3 google.com

# Solution 2: Try alternative services
curl -s ifconfig.me
curl -s icanhazip.com
curl -s ipecho.net/plain
curl -s api.ipify.org

# Solution 3: Increase timeout
curl -s --max-time 10 ifconfig.me

# Solution 4: Check for proxy/VPN
env | grep -i proxy
```

### Problem 7: JSON parsing errors with jq

```bash
# Cause: Invalid JSON or empty output

# Solution 1: Check raw output first
termux-wifi-connectioninfo
# If empty, WiFi is not connected

# Solution 2: Handle empty/null gracefully
termux-wifi-connectioninfo | jq -r '.ssid // "Not Connected"'

# Solution 3: Validate JSON
termux-wifi-connectioninfo | jq . > /dev/null && echo "Valid JSON" || echo "Invalid JSON"

# Solution 4: Install jq if not present
pkg install jq -y
```

### Problem 8: Mobile data toggle not working

```bash
# Cause: Android security restrictions

# Solution 1: Use settings intent (manual toggle)
am start -a android.settings.DATA_ROAMING_SETTINGS

# Solution 2: Root method
su -c "svc data enable"   # Enable
su -c "svc data disable"  # Disable

# Solution 3: ADB method (requires PC)
# Run on PC with ADB:
adb shell pm grant com.termux android.permission.WRITE_SECURE_SETTINGS
# Then in Termux:
settings put global mobile_data 1  # Enable
```

### Problem 9: Hotspot control not working

```bash
# Cause: Hotspot requires system permissions

# Solution 1: Open hotspot settings manually
am start -a android.settings.WIFI_HOTSPOT_SETTINGS

# Solution 2: Root commands
su -c "svc wifi disable"
su -c "ndc softap start wlan0 MyHotspot password123"

# Solution 3: Check hotspot support
# Not all devices support programmatic hotspot control
# Some carriers disable this feature
```

### Problem 10: Network scan slow or hanging

```bash
# Cause: Android throttling or background restrictions

# Solution 1: Clear Termux from recent apps and reopen
# This resets any throttling

# Solution 2: Disable battery optimization for Termux
# Settings → Apps → Termux → Battery → Unrestricted

# Solution 3: Add delay between scans
termux-wifi-scaninfo
sleep 10
termux-wifi-scaninfo

# Solution 4: Check if Termux:API is running
ps -A | grep termux
# If not running, restart Termux
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📡 TERMUX NETWORK API            │
│   WiFi • IP • Hotspot • MAC        │
│                                    │
│   ✓ No Root Required               │
│   ✓ 20+ Examples                   │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Feature Focus**
```
┌────────────────────────────────────┐
│  📶 WiFi Scanner    ✅             │
│  🌐 IP Address      ✅             │
│  🔒 MAC Address     ✅             │
│  📡 Hotspot         ✅             │
│  ────────────────────────────────  │
│                                    │
│  NETWORK MASTERY                   │
│  Chapter 20 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Code Style**
```
┌────────────────────────────────────┐
│  [Terminal Window]                 │
│  $ termux-wifi-scaninfo            │
│  [{ssid:"HomeWiFi",...}]           │
│  $ termux-wifi-enable true         │
│  WiFi ENABLED ✓                    │
│                                    │
│  NETWORK API TUTORIAL              │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📡 Termux Network API | WiFi, Hotspot, IP Address | Chapter 20

🔥 In this video you'll learn:
• WiFi connection info retrieve karna
• WiFi on/off control karna
• Network scanning aur analysis
• IP address information
• MAC address extraction
• Hotspot management
• Network security analysis
• Python integration
• 20+ practical examples

⏱️ Timestamps:
0:00 - Introduction
0:45 - Termux API Installation Check
2:30 - WiFi Connection Info
5:00 - WiFi Enable/Disable
7:30 - WiFi Scan Info
10:00 - WiFi Password (Root)
12:00 - Mobile Data Control
14:00 - Hotspot Control
15:30 - IP Address Information
17:00 - MAC Address
18:30 - Network Stats & Monitoring
20:00 - Practical Scripts
22:00 - Python Integration
24:00 - 20+ Examples
27:00 - Summary

📝 Commands from this video:
termux-wifi-connectioninfo
termux-wifi-enable true
termux-wifi-scaninfo | jq 'length'
curl -s ifconfig.me
ip addr show wlan0

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxAPI #NetworkAPI #WiFi #T3rmuxk1ng #TermuxTutorial #TermuxHindi #NetworkHacking #CyberSecurity

---
⚠️ Disclaimer: This video is for educational purposes only. Use these tools responsibly and only on networks you have permission to test.
```

### Tags List

```
termux, termux api, termux network, termux wifi, termux ip address,
termux mac address, termux hotspot, termux wifi scanner,
termux tutorial, termux course, termux hindi, t3rmuxk1ng,
wifi scanner android, network scanner android, ip address termux,
mac address android, termux network commands, wifi analyzer,
network monitoring, ethical hacking, penetration testing,
android hacking, mobile security, termux scripts, termux python
```

### Hashtags

```
#Termux #TermuxAPI #NetworkAPI #WiFiScanner #IPAddress 
#TermuxTutorial #TermuxHindi #CyberSecurity #EthicalHacking 
#T3rmuxk1ng #NetworkSecurity #AndroidHacking #TermuxCourse
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux Wiki - API | https://wiki.termux.com/wiki/Termux:API |
| Termux API GitHub | https://github.com/termux/termux-api |
| Android WifiManager | https://developer.android.com/reference/android/net/wifi/WifiManager |

### Related Tools

| Tool | Purpose | Install |
|------|---------|---------|
| nmap | Network scanning | `pkg install nmap` |
| netcat | Network utility | `pkg install netcat` |
| curl | HTTP client | `pkg install curl` |
| wget | File downloader | `pkg install wget` |
| jq | JSON processor | `pkg install jq` |
| dnsutils | DNS tools | `pkg install dnsutils` |
| net-tools | Network utilities | `pkg install net-tools` |
| iproute2 | Advanced IP tools | `pkg install iproute2` |

### Learning Resources

| Topic | Resource |
|-------|----------|
| WiFi Security | OWASP Wireless Security |
| Network Scanning | Nmap Documentation |
| Python Networking | Python socket module docs |
| Android Networking | Android Developer Guide |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 21, verify:

- [ ] Termux:API app installed from F-Droid
- [ ] `pkg install termux-api` completed
- [ ] `termux-wifi-connectioninfo` works correctly
- [ ] `termux-wifi-scaninfo` returns network list
- [ ] Can parse JSON output with jq
- [ ] WiFi enable/disable working
- [ ] Public IP fetch successful
- [ ] MAC address retrieved
- [ ] Created at least one monitoring script
- [ ] Understood security implications of WPS/Open networks

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 21: Termux API - Notifications**

- Notification basics and types
- Creating simple notifications
- Notification with actions
- Progress notifications
- Notification channels (Android 8+)
- Notification sounds and vibrations
- LED and priority settings
- Notification management
- Practical notification scripts
- Tasker integration

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
