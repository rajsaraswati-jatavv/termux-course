# Chapter 18: Termux API - Device Information

> **Module:** 4 - APIs  
> **Chapter:** 18 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Device info API commands详解 |
| API Reference | All device info commands with examples |
| Commands Reference | All commands covered in chapter |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common API issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 18
Title: Device Information API | Phone Info Extract Karne Ka Tarika | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum Module 4 ka ek bahut important chapter start karte hain - 
Device Information APIs. Is chapter mein hum seekhenge ki kaise 
Termux ke through apne phone ki complete information extract kar sakte hain.

Battery status, brightness control, volume settings, telephony info, 
WiFi details, sensors data, fingerprint authentication, GPS location - 
sab kuch ek command se!

Ye APIs aapko phone ke har hardware component ka access deti hain - 
bina root ke! Automation scripts banane ke liye, security tools 
bane ke liye, ya bas information ke liye - ye APIs bahut useful hain.

Chaliye shuru karte hain!

---

[SECTION 1: PREREQUISITES & SETUP - 0:45 to 2:30]
─────────────────────────────────────────────────────────────────────────────

Device Information APIs use karne ke liye, aapko Termux:API app install 
karni hogi. Agar aapne Chapter 10 follow kiya hai, to ye already 
installed hoga.

Quick check karte hain:

    pkg install termux-api -y

Ye command Termux API package install karti hai.

Ab verify karein:

    termux-battery-status

Agar output mein battery percentage aur status dikha, to sab kuch 
theek hai! Agar error aaya to:

1. Termux:API app F-Droid se install karein
2. Termux app ko "Allow background activity" permission dein
3. Battery optimization disable karein Termux ke liye

Termux:API install karna zaroori hai kyunki ye ek bridge hai Termux 
app aur Android system ke beech. Ye Android ke native APIs ko call 
karta hai aur JSON output deta hai.

---

[SECTION 2: BATTERY STATUS API - 2:30 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Pehle battery status se shuru karte hain - sabse simple aur useful API.

Command:

    termux-battery-status

Output aisa aayega (JSON format mein):

    {
      "health": "GOOD",
      "percentage": 85,
      "plugged": "UNPLUGGED",
      "status": "DISCHARGING",
      "temperature": 32.0,
      "current": -450
    }

Samjhein har field kya batati hai:

• health - Battery ki condition (GOOD, OVERHEAT, DEAD, etc.)
• percentage - Current battery percentage (0-100)
• plugged - Charging status (PLUGGED_AC, PLUGGED_USB, UNPLUGGED)
• status - Current state (CHARGING, DISCHARGING, FULL, NOT_CHARGING)
• temperature - Battery temperature in Celsius
• current - Current in milliAmperes (-ve means discharging)

Ab ise Python mein parse karne ka tarika:

    termux-battery-status | python -c "import sys,json; d=json.load(sys.stdin); print(f'Battery: {d[\"percentage\"]}%')"

Ya ek cleaner script:

    termux-battery-status > battery.json
    python -c "import json; d=json.load(open('battery.json')); print(f'Health: {d[\"health\"]}\nBattery: {d[\"percentage\"]}%\nTemp: {d[\"temperature\"]}°C')"

Practical use case - Low battery alert script:

    #!/bin/bash
    BATTERY=$(termux-battery-status | jq -r '.percentage')
    if [ $BATTERY -lt 20 ]; then
        termux-notification --title "Low Battery!" --content "Battery at ${BATTERY}%"
        termux-vibrate
    fi

Ye script tab use aati hai jab aap automation karna chahte ho - 
jaise battery 20% se neeche ho to notification aur vibration.

---

[SECTION 3: BRIGHTNESS CONTROL API - 5:00 to 7:30]
─────────────────────────────────────────────────────────────────────────────

Ab brightness control ki baat karte hain. Ye API brightness get aur 
set dono kar sakti hai.

Current brightness check karein:

    termux-brightness

Ye current brightness level dikhayega (0-255 ya 0-100 depending on device).

Brightness set karna:

    termux-brightness 100

Ye brightness set kar dega. Range device pe depend karti hai - 
kuch devices 0-255 use karti hain, kuch 0-100.

Ek kaam karein - adaptive brightness test:

    termux-brightness 50
    sleep 1
    echo "Brightness set to medium"

Brightness automation script:

    #!/bin/bash
    # Night mode - dim brightness at night
    HOUR=$(date +%H)
    if [ $HOUR -ge 20 ] || [ $HOUR -lt 6 ]; then
        termux-brightness 30
        echo "Night mode activated"
    else
        termux-brightness 150
        echo "Day mode activated"
    fi

Ye script aap cron job ya Tasker ke saath use kar sakte ho automatic 
brightness adjustment ke liye.

Important note: Kuch devices pe brightness change ke liye additional 
permission chahiye hoti hai - "Modify system settings" permission 
Android settings mein enable karna padega.

Settings → Apps → Termux → Modify system settings → Allow

---

[SECTION 4: VOLUME CONTROL API - 7:30 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Volume API bahut powerful hai - different audio streams ka control 
deti hai.

Volume levels check karein:

    termux-volume

Output aisa aayega:

    {
      "stream": "notification",
      "volume": 5,
      "max_volume": 7
    }

Default ye notification stream dikhata hai. Lekin aap different 
streams check kar sakte ho:

Streams available:
• stream_notification - Notification sounds
• stream_ring - Ringtone volume
• stream_music - Media/Music volume
• stream_alarm - Alarm volume
• stream_system - System sounds

Specific stream check karein:

    termux-volume stream_music

Volume set karna:

    termux-volume stream_music 10

Ya notification volume:

    termux-volume stream_notification 5

Mute karna:

    termux-volume stream_ring 0

Practical script - Meeting mode:

    #!/bin/bash
    # Save current volumes
    termux-volume stream_ring > /tmp/ring_vol.json
    termux-volume stream_notification > /tmp/notif_vol.json
    
    # Set to vibrate/mute
    termux-volume stream_ring 0
    termux-volume stream_notification 0
    termux-notification --title "Meeting Mode" --content "Phone muted"
    
    # Later restore (run separately)
    # RING=$(jq -r '.volume' /tmp/ring_vol.json)
    # termux-volume stream_ring $RING

Ye script meeting ke time phone ko automatically mute karti hai!

---

[SECTION 5: TELEPHONY DEVICE INFO - 10:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

Ab telephony APIs ki baad - ye aapko phone ki detailed information 
deti hain.

Device info command:

    termux-telephony-deviceinfo

Output:

    {
      "device_id": "359881060236451",
      "imei": "359881060236451",
      "meid": "A00000721BCDE5",
      "sim_country": "in",
      "sim_operator": "40485",
      "sim_operator_name": "Jio",
      "sim_serial_number": "89919012345678901234",
      "sim_subscriber_id": "404851234567890",
      "sim_state": "READY",
      "phone_type": "GSM",
      "network_type": "LTE",
      "network_country": "in",
      "network_operator": "40485",
      "network_operator_name": "Jio",
      "network_roaming": false,
      "software_version": "03"
    }

Ye information security research ke liye bahut useful hai. Dekhte 
hain har field kya hai:

• device_id / imei - Unique device identifier (15 digits)
• meid - CDMA device identifier
• sim_country - SIM country code (ISO)
• sim_operator - Mobile network code
• sim_operator_name - Network name (Jio, Airtel, etc.)
• sim_serial_number - ICCID (SIM card serial)
• sim_subscriber_id - IMSI number
• sim_state - READY, ABSENT, LOCKED, etc.
• phone_type - GSM, CDMA, SIP, NONE
• network_type - Current network (LTE, HSPA, etc.)
• network_roaming - Roaming status

Cell info check karein:

    termux-telephony-cellinfo

Output:

    {
      "type": "gsm",
      "mcc": "404",
      "mnc": "85",
      "lac": "28561",
      "cid": "68213321",
      "dbm": -85,
      "asu": 15,
      "level": 3
    }

Ye information cell tower location ke liye use hoti hai - 
security research aur location tracking mein useful!

---

[SECTION 6: WIFI CONNECTION INFO - 12:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

WiFi information API:

    termux-wifi-connectioninfo

Output:

    {
      "bssid": "aa:bb:cc:dd:ee:ff",
      "frequency_mhz": 2437,
      "ip": "192.168.1.105",
      "link_speed_mbps": 72,
      "mac_address": "02:00:00:00:00:00",
      "network_id": 5,
      "rssi": -65,
      "ssid": "MyWiFiNetwork",
      "ssid_hidden": false,
      "supplicant_state": "COMPLETED"
    }

Fields explain:

• bssid - Router ka MAC address
• frequency_mhz - WiFi frequency band
• ip - Assigned IP address
• link_speed_mbps - Connection speed
• mac_address - Device MAC (Android 10+ returns 02:00:00:00:00:00)
• network_id - Saved network ID
• rssi - Signal strength (closer to 0 is better)
• ssid - WiFi name

Signal strength analysis:

    # RSSI values:
    # -30 to -50: Excellent
    # -50 to -60: Good  
    # -60 to -70: Fair
    # -70 to -80: Weak
    # Below -80: Very poor

Python script for WiFi strength:

    termux-wifi-connectioninfo | python -c "
import sys, json
d = json.load(sys.stdin)
rssi = d['rssi']
if rssi > -50:
    strength = 'Excellent'
elif rssi > -60:
    strength = 'Good'
elif rssi > -70:
    strength = 'Fair'
else:
    strength = 'Weak'
print(f'WiFi: {d[\"ssid\"]}\nSignal: {strength} ({rssi} dBm)')
"

---

[SECTION 7: SENSORS API - 14:00 to 16:30]
─────────────────────────────────────────────────────────────────────────────

Sensors API bahut powerful hai - aap phone ke saare sensors access 
kar sakte ho!

Available sensors list:

    termux-sensor -l

Ya:

    termux-sensor -s list

Output mein aapko device ke saare sensors milenge:

• accelerometer - Motion/orientation
• gyroscope - Rotation
• magnetometer - Magnetic field (compass)
• light - Ambient light
• proximity - Near/far detection
• pressure - Barometer
• temperature - Device temperature
• humidity - Ambient humidity
• gravity - Gravity vector
• linear_acceleration - Linear motion
• rotation_vector - Device rotation

Accelerometer data:

    termux-sensor -s accelerometer -n 1

Output:

    {
      "accelerometer": {
        "values": [0.12, 9.81, 0.05],
        "timestamp": 1234567890123456
      }
    }

Values mein [x, y, z] acceleration in m/s².

Gyroscope:

    termux-sensor -s gyroscope -n 1

Magnetometer (compass):

    termux-sensor -s magnetometer -n 1

Continuous sensor monitoring:

    termux-sensor -s accelerometer -d 1000

-d 1000 means updates every 1000ms (1 second). Ctrl+C to stop.

Multiple sensors ek saath:

    termux-sensor -s "accelerometer,gyroscope,magnetometer" -d 500

Sensor data Python script:

    #!/usr/bin/env python3
    import subprocess
    import json
    
    def get_acceleration():
        result = subprocess.run(
            ['termux-sensor', '-s', 'accelerometer', '-n', '1'],
            capture_output=True, text=True
        )
        data = json.loads(result.stdout)
        values = data['accelerometer']['values']
        return {
            'x': values[0],
            'y': values[1],
            'z': values[2],
            'magnitude': (values[0]**2 + values[1]**2 + values[2]**2)**0.5
        }
    
    acc = get_acceleration()
    print(f"X: {acc['x']:.2f}, Y: {acc['y']:.2f}, Z: {acc['z']:.2f}")
    print(f"Total magnitude: {acc['magnitude']:.2f} m/s²")

---

[SECTION 8: FINGERPRINT API - 16:30 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Fingerprint API aapko biometric authentication use karne deti hai.

    termux-fingerprint

Ye command fingerprint scanner activate karega:

Output success pe:

    {
      "auth_result": "AUTH_RESULT_SUCCESS",
      "auth_result_reason": "Fingerprint recognized.",
      "errors": []
    }

Failed pe:

    {
      "auth_result": "AUTH_RESULT_FAILURE",
      "auth_result_reason": "Fingerprint not recognized.",
      "errors": []
    }

Cancel pe:

    {
      "auth_result": "AUTH_RESULT_FAILURE", 
      "auth_result_reason": "User canceled.",
      "errors": []
    }

Fingerprint in script:

    #!/bin/bash
    echo "Please authenticate with fingerprint..."
    RESULT=$(termux-fingerprint | jq -r '.auth_result')
    
    if [ "$RESULT" = "AUTH_RESULT_SUCCESS" ]; then
        echo "Authentication successful!"
        # Your protected commands here
    else
        echo "Authentication failed!"
        exit 1
    fi

Use cases:
• Script ko secure karna
• Sensitive data access control
• Custom authentication system
• App-like security in Termux

Note: Fingerprint API Android 6.0+ pe kaam karti hai aur device 
mein fingerprint scanner hona chahiye.

---

[SECTION 9: LOCATION API - 18:00 to 20:00]
─────────────────────────────────────────────────────────────────────────────

Location API aapko GPS coordinates deti hai.

    termux-location

Default network-based location (faster but less accurate).

GPS provider:

    termux-location -p gps

Output:

    {
      "latitude": 28.6139,
      "longitude": 77.2090,
      "altitude": 216.0,
      "accuracy": 15.0,
      "bearing": 0.0,
      "speed": 0.0,
      "elapsedMs": 1523,
      "provider": "gps"
    }

Fields:
• latitude - Latitude in degrees
• longitude - Longitude in degrees
• altitude - Altitude in meters
• accuracy - Accuracy in meters (lower is better)
• bearing - Direction in degrees
• speed - Speed in m/s
• provider - gps or network

Location to address (reverse geocoding):

    termux-location -p gps | python -c "
import sys, json, urllib.request

data = json.load(sys.stdin)
lat, lon = data['latitude'], data['longitude']

url = f'https://nominatim.openstreetmap.org/reverse?lat={lat}&lon={lon}&format=json'
req = urllib.request.Request(url, headers={'User-Agent': 'Termux/1.0'})
response = urllib.request.urlopen(req)
address = json.loads(response.read())
print(f'Address: {address[\"display_name\"]}')
"

Location tracking script:

    #!/bin/bash
    while true; do
        termux-location -p network > /tmp/loc.json
        LAT=$(jq -r '.latitude' /tmp/loc.json)
        LON=$(jq -r '.longitude' /tmp/loc.json)
        echo "$(date): $LAT, $LON" >> location_log.txt
        sleep 60
    done

---

[SECTION 10: CREATING DEVICE INFO SCRIPT - 20:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Ab ek complete device info extraction script banate hain:

    #!/bin/bash
    # device_info.sh - Complete Device Information Extractor
    # Author: T3rmuxk1ng
    
    echo "╔════════════════════════════════════════════╗"
    echo "║     DEVICE INFORMATION EXTRACTOR v1.0      ║"
    echo "║           Created by T3rmuxk1ng            ║"
    echo "╚════════════════════════════════════════════╝"
    echo ""
    
    # Battery Info
    echo "📊 BATTERY STATUS"
    echo "─────────────────"
    termux-battery-status | jq -r '
        "Health: \(.health)",
        "Level: \(.percentage)%",
        "Status: \(.status)",
        "Temperature: \(.temperature)°C"
    '
    echo ""
    
    # Telephony Info
    echo "📱 TELEPHONY INFO"
    echo "─────────────────"
    termux-telephony-deviceinfo | jq -r '
        "IMEI: \(.imei // "N/A")",
        "SIM: \(.sim_operator_name // "N/A")",
        "Network: \(.network_type // "N/A")",
        "Roaming: \(.network_roaming)"
    '
    echo ""
    
    # WiFi Info
    echo "📶 WIFI STATUS"
    echo "─────────────────"
    termux-wifi-connectioninfo | jq -r '
        "SSID: \(.ssid // "Not connected")",
        "IP: \(.ip // "N/A")",
        "Signal: \(.rssi) dBm",
        "Speed: \(.link_speed_mbps) Mbps"
    '
    echo ""
    
    # Location (if GPS available)
    echo "📍 LOCATION"
    echo "─────────────────"
    termux-location -p network -r 5 2>/dev/null | jq -r '
        "Latitude: \(.latitude)",
        "Longitude: \(.longitude)",
        "Accuracy: \(.accuracy)m"
    ' || echo "Location unavailable"
    echo ""
    
    echo "═══════════════════════════════════════════"
    echo "Report generated at: $(date)"

Ye script run karein:

    chmod +x device_info.sh
    ./device_info.sh

Output save karein:

    ./device_info.sh > device_report.txt

JSON output mein:

    ./device_info.sh | jq -Rs . > report.json

---

[SECTION 11: JSON PARSING TECHNIQUES - 22:00 to 23:30]
─────────────────────────────────────────────────────────────────────────────

Termux APIs JSON output deti hain. Isse efficiently parse karna zaroori hai.

Method 1: Using jq (recommended)

    # Install jq
    pkg install jq -y
    
    # Get specific value
    termux-battery-status | jq -r '.percentage'
    
    # Multiple values
    termux-battery-status | jq -r '"\(.percentage)% - \(.status)"'
    
    # Nested values
    termux-sensor -s accelerometer -n 1 | jq '.accelerometer.values[0]'

Method 2: Using Python

    # Single value
    termux-battery-status | python -c "import sys,json; print(json.load(sys.stdin)['percentage'])"
    
    # Multiple values
    termux-battery-status | python -c "
import sys,json
d=json.load(sys.stdin)
print(f\"Battery: {d['percentage']}%\")
print(f\"Status: {d['status']}\")
"

Method 3: Using grep/sed (quick & dirty)

    termux-battery-status | grep -o '"percentage": [0-9]*' | grep -o '[0-9]*'

Method 4: Python script for complex parsing

    #!/usr/bin/env python3
    import subprocess
    import json
    
    def get_battery():
        result = subprocess.run(['termux-battery-status'], 
                              capture_output=True, text=True)
        return json.loads(result.stdout)
    
    def get_wifi():
        result = subprocess.run(['termux-wifi-connectioninfo'],
                              capture_output=True, text=True)
        return json.loads(result.stdout)
    
    battery = get_battery()
    wifi = get_wifi()
    
    print(f"Battery: {battery['percentage']}%")
    print(f"WiFi: {wifi.get('ssid', 'Not connected')}")

---

[SECTION 12: PYTHON INTEGRATION - 23:30 to 25:00]
─────────────────────────────────────────────────────────────────────────────

Complete Python library for Termux APIs:

    #!/usr/bin/env python3
    # termux_device.py - Python wrapper for Termux Device APIs
    
    import subprocess
    import json
    from typing import Dict, Optional, List
    
    class TermuxDevice:
        """Python wrapper for Termux Device Information APIs"""
        
        @staticmethod
        def _run_command(cmd: List[str]) -> Optional[Dict]:
            """Execute termux command and return JSON output"""
            try:
                result = subprocess.run(cmd, capture_output=True, text=True, timeout=30)
                if result.returncode == 0:
                    return json.loads(result.stdout)
                return None
            except:
                return None
        
        @staticmethod
        def get_battery() -> Dict:
            """Get battery status"""
            return TermuxDevice._run_command(['termux-battery-status'])
        
        @staticmethod
        def set_brightness(level: int) -> bool:
            """Set screen brightness"""
            try:
                subprocess.run(['termux-brightness', str(level)], check=True)
                return True
            except:
                return False
        
        @staticmethod
        def get_volume(stream: str = 'notification') -> Dict:
            """Get volume level for a stream"""
            return TermuxDevice._run_command(['termux-volume', stream])
        
        @staticmethod
        def set_volume(stream: str, level: int) -> bool:
            """Set volume level"""
            try:
                subprocess.run(['termux-volume', stream, str(level)], check=True)
                return True
            except:
                return False
        
        @staticmethod
        def get_device_info() -> Dict:
            """Get telephony device information"""
            return TermuxDevice._run_command(['termux-telephony-deviceinfo'])
        
        @staticmethod
        def get_cell_info() -> Dict:
            """Get cell tower information"""
            return TermuxDevice._run_command(['termux-telephony-cellinfo'])
        
        @staticmethod
        def get_wifi_info() -> Dict:
            """Get WiFi connection information"""
            return TermuxDevice._run_command(['termux-wifi-connectioninfo'])
        
        @staticmethod
        def get_sensor(sensor: str, samples: int = 1) -> Dict:
            """Get sensor data"""
            return TermuxDevice._run_command(['termux-sensor', '-s', sensor, '-n', str(samples)])
        
        @staticmethod
        def get_location(provider: str = 'network') -> Dict:
            """Get device location"""
            return TermuxDevice._run_command(['termux-location', '-p', provider])
        
        @staticmethod
        def check_fingerprint() -> Dict:
            """Check fingerprint authentication"""
            return TermuxDevice._run_command(['termux-fingerprint'])
        
        @staticmethod
        def get_full_report() -> Dict:
            """Get complete device report"""
            return {
                'battery': TermuxDevice.get_battery(),
                'telephony': TermuxDevice.get_device_info(),
                'wifi': TermuxDevice.get_wifi_info(),
                'location': TermuxDevice.get_location('network')
            }
    
    
    # Usage Example
    if __name__ == '__main__':
        device = TermuxDevice()
        
        # Battery info
        battery = device.get_battery()
        print(f"Battery: {battery.get('percentage', 'N/A')}%")
        
        # WiFi info
        wifi = device.get_wifi_info()
        print(f"WiFi: {wifi.get('ssid', 'Not connected')}")
        
        # Location
        location = device.get_location()
        if location:
            print(f"Location: {location['latitude']}, {location['longitude']}")
        
        # Full report
        import pprint
        pprint.pprint(device.get_full_report())

Usage:

    python termux_device.py

---

[SECTION 13: SUMMARY & NEXT PREVIEW - 25:00 to 26:30]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 18 complete! Let's summarize:

✅ termux-battery-status - Battery health, percentage, temperature
✅ termux-brightness - Screen brightness get/set
✅ termux-volume - Volume control for all streams
✅ termux-telephony-deviceinfo - IMEI, SIM, network info
✅ termux-telephony-cellinfo - Cell tower information
✅ termux-wifi-connectioninfo - WiFi details and signal
✅ termux-sensor - Accelerometer, gyroscope, magnetometer
✅ termux-fingerprint - Biometric authentication
✅ termux-location - GPS coordinates
✅ JSON parsing with jq and Python
✅ Complete Python wrapper class

Important Commands:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 18 - KEY COMMANDS                             │
├─────────────────────────────────────────────────────────────────────────┤
│ termux-battery-status         │ Battery information                      │
│ termux-brightness [level]     │ Get/set screen brightness                │
│ termux-volume [stream] [lvl]  │ Volume control                           │
│ termux-telephony-deviceinfo   │ Phone/SIM information                    │
│ termux-telephony-cellinfo     │ Cell tower information                   │
│ termux-wifi-connectioninfo    │ WiFi connection details                  │
│ termux-sensor -s [name] -n 1  │ Single sensor reading                    │
│ termux-sensor -s [name] -d ms │ Continuous sensor monitoring             │
│ termux-fingerprint            │ Biometric authentication                 │
│ termux-location -p gps        │ GPS location                             │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 19 mein hum seekhenge:
- Camera API - Photo aur video capture
- Media playback and recording
- Audio recording
- Media file handling

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Thank you for watching! See you in Chapter 19!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Device Information APIs Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX DEVICE INFORMATION APIs                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                    Hardware Access Layer                         │    │
│   │                                                                  │    │
│   │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │    │
│   │  │ Battery      │  │ Brightness   │  │ Volume       │         │    │
│   │  │ API          │  │ API          │  │ API          │         │    │
│   │  └──────────────┘  └──────────────┘  └──────────────┘         │    │
│   │                                                                  │    │
│   │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │    │
│   │  │ Telephony    │  │ WiFi         │  │ Sensors      │         │    │
│   │  │ API          │  │ API          │  │ API          │         │    │
│   │  └──────────────┘  └──────────────┘  └──────────────┘         │    │
│   │                                                                  │    │
│   │  ┌──────────────┐  ┌──────────────┐                            │    │
│   │  │ Fingerprint  │  │ Location     │                            │    │
│   │  │ API          │  │ API          │                            │    │
│   │  └──────────────┘  └──────────────┘                            │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                              │                                          │
│                              ▼                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                    Termux:API App Bridge                         │    │
│   │   (Android Service with BIND_AUTO_CREATE)                       │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                              │                                          │
│                              ▼                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │                    Android System APIs                           │    │
│   │   BatteryManager, TelephonyManager, WifiManager,                │    │
│   │   SensorManager, FingerprintManager, LocationManager            │    │
│   └────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. API Response Formats

All Device Information APIs return JSON:

```json
// Battery Status
{
  "health": "GOOD|OVERHEAT|DEAD|OVER_VOLTAGE|UNSPECIFIED_FAILURE|COLD",
  "percentage": 85,
  "plugged": "PLUGGED_AC|PLUGGED_USB|PLUGGED_WIRELESS|UNPLUGGED",
  "status": "CHARGING|DISCHARGING|FULL|NOT_CHARGING|UNKNOWN",
  "temperature": 32.0,
  "current": -450
}

// Telephony Device Info
{
  "device_id": "string",
  "imei": "string",
  "meid": "string",
  "sim_country": "string",
  "sim_operator": "string",
  "sim_operator_name": "string",
  "sim_serial_number": "string",
  "sim_subscriber_id": "string",
  "sim_state": "READY|ABSENT|LOCKED|NETWORK_LOCKED|NOT_READY|UNKNOWN",
  "phone_type": "GSM|CDMA|SIP|NONE",
  "network_type": "UNKNOWN|GPRS|EDGE|UMTS|CDMA|EVDO_0|LTE|etc",
  "network_country": "string",
  "network_operator": "string",
  "network_operator_name": "string",
  "network_roaming": boolean,
  "software_version": "string"
}

// WiFi Connection Info
{
  "bssid": "string (MAC)",
  "frequency_mhz": number,
  "ip": "string",
  "link_speed_mbps": number,
  "mac_address": "string",
  "network_id": number,
  "rssi": number,
  "ssid": "string",
  "ssid_hidden": boolean,
  "supplicant_state": "string"
}

// Location
{
  "latitude": number,
  "longitude": number,
  "altitude": number,
  "accuracy": number,
  "bearing": number,
  "speed": number,
  "elapsedMs": number,
  "provider": "gps|network|passive"
}

// Sensor Data
{
  "sensor_name": {
    "values": [x, y, z],
    "timestamp": number
  }
}

// Fingerprint
{
  "auth_result": "AUTH_RESULT_SUCCESS|AUTH_RESULT_FAILURE",
  "auth_result_reason": "string",
  "errors": []
}
```

### 3. Sensor Types Reference

| Sensor | Type | Values | Description |
|--------|------|--------|-------------|
| accelerometer | Motion | [x, y, z] m/s² | Linear acceleration |
| gyroscope | Rotation | [x, y, z] rad/s | Angular velocity |
| magnetometer | Magnetic | [x, y, z] µT | Magnetic field |
| light | Light | [lux] | Ambient light |
| proximity | Distance | [cm] | Object proximity |
| pressure | Barometric | [hPa] | Atmospheric pressure |
| temperature | Temp | [°C] | Device temperature |
| humidity | Humidity | [%] | Relative humidity |
| gravity | Gravity | [x, y, z] m/s² | Gravity vector |
| linear_acceleration | Motion | [x, y, z] m/s² | Linear motion (gravity removed) |
| rotation_vector | Rotation | [x, y, z, w] | Device orientation |
| step_counter | Activity | [steps] | Step count |
| step_detector | Activity | [1] | Step detected |

### 4. Volume Streams Reference

| Stream | Description | Typical Range |
|--------|-------------|---------------|
| stream_notification | Notification sounds | 0-7 |
| stream_ring | Ringtone | 0-7 |
| stream_music | Media playback | 0-15 |
| stream_alarm | Alarms | 0-7 |
| stream_system | System sounds | 0-7 |
| stream_voice_call | Call volume | 0-5 |
| stream_dtmf | DTMF tones | 0-15 |

### 5. Location Providers Comparison

| Provider | Accuracy | Battery | Speed |
|----------|----------|---------|-------|
| gps | High (5-10m) | High drain | Slow (cold start) |
| network | Medium (50-500m) | Low drain | Fast |
| passive | Varies | Minimal | Instant (cached) |

---

## 🔧 API COMMANDS REFERENCE

### Battery Status

```bash
# Get battery information
termux-battery-status

# Parse battery percentage
termux-battery-status | jq -r '.percentage'

# Check if charging
termux-battery-status | jq -r '.plugged'

# Get battery temperature
termux-battery-status | jq -r '.temperature'

# Battery health check
termux-battery-status | jq -r '.health'

# Create battery monitor script
cat > battery_monitor.sh << 'EOF'
#!/bin/bash
while true; do
    BATTERY=$(termux-battery-status | jq -r '.percentage')
    STATUS=$(termux-battery-status | jq -r '.status')
    TEMP=$(termux-battery-status | jq -r '.temperature')
    echo "[$(date +%H:%M:%S)] Battery: ${BATTERY}% | ${STATUS} | ${TEMP}°C"
    sleep 60
done
EOF
```

### Brightness Control

```bash
# Get current brightness
termux-brightness

# Set brightness (0-255 or 0-100 depending on device)
termux-brightness 100

# Set maximum brightness
termux-brightness 255

# Set minimum brightness
termux-brightness 0

# Brightness adjustment script
cat > brightness_control.sh << 'EOF'
#!/bin/bash
case "$1" in
    "max") termux-brightness 255 ;;
    "min") termux-brightness 10 ;;
    "dim") termux-brightness 50 ;;
    "medium") termux-brightness 128 ;;
    *) echo "Usage: $0 {max|min|dim|medium}" ;;
esac
EOF

# Auto brightness based on time
cat > auto_brightness.sh << 'EOF'
#!/bin/bash
HOUR=$(date +%H)
if [ $HOUR -ge 20 ] || [ $HOUR -lt 6 ]; then
    termux-brightness 30  # Night
elif [ $HOUR -ge 6 ] && [ $HOUR -lt 9 ]; then
    termux-brightness 100 # Morning
else
    termux-brightness 150 # Day
fi
EOF
```

### Volume Control

```bash
# Get notification volume
termux-volume

# Get specific stream volume
termux-volume stream_music
termux-volume stream_ring
termux-volume stream_alarm
termux-volume stream_notification

# Set volume
termux-volume stream_music 10
termux-volume stream_ring 5
termux-volume stream_notification 3

# Mute streams
termux-volume stream_ring 0
termux-volume stream_notification 0

# Volume control script
cat > volume_control.sh << 'EOF'
#!/bin/bash
case "$1" in
    "mute")
        termux-volume stream_ring 0
        termux-volume stream_notification 0
        termux-volume stream_music 0
        echo "All volumes muted"
        ;;
    "unmute")
        termux-volume stream_ring 5
        termux-volume stream_notification 5
        termux-volume stream_music 10
        echo "Volumes restored"
        ;;
    "max")
        termux-volume stream_music 15
        termux-volume stream_ring 7
        echo "Maximum volume"
        ;;
    *) echo "Usage: $0 {mute|unmute|max}" ;;
esac
EOF
```

### Telephony Device Info

```bash
# Get complete device info
termux-telephony-deviceinfo

# Extract IMEI
termux-telephony-deviceinfo | jq -r '.imei'

# Get SIM operator name
termux-telephony-deviceinfo | jq -r '.sim_operator_name'

# Check network type
termux-telephony-deviceinfo | jq -r '.network_type'

# Get SIM serial number (ICCID)
termux-telephony-deviceinfo | jq -r '.sim_serial_number'

# Check if roaming
termux-telephony-deviceinfo | jq -r '.network_roaming'

# Get IMSI
termux-telephony-deviceinfo | jq -r '.sim_subscriber_id'

# Device info summary
termux-telephony-deviceinfo | jq -r '
"Device: \(.imei // "N/A")",
"SIM: \(.sim_operator_name // "N/A")",
"Network: \(.network_type // "N/A")",
"Phone Type: \(.phone_type // "N/A")"
'
```

### Telephony Cell Info

```bash
# Get cell tower information
termux-telephony-cellinfo

# Extract cell ID
termux-telephony-cellinfo | jq -r '.cid'

# Get signal strength
termux-telephony-cellinfo | jq -r '.dbm'

# Get location area code
termux-telephony-cellinfo | jq -r '.lac'

# Cell info formatted
termux-telephony-cellinfo | jq -r '
"Cell ID: \(.cid)",
"LAC: \(.lac)",
"MCC/MNC: \(.mcc)/\(.mnc)",
"Signal: \(.dbm) dBm",
"Quality: \(.asu) ASU"
'
```

### WiFi Connection Info

```bash
# Get WiFi connection details
termux-wifi-connectioninfo

# Extract SSID
termux-wifi-connectioninfo | jq -r '.ssid'

# Get IP address
termux-wifi-connectioninfo | jq -r '.ip'

# Get signal strength
termux-wifi-connectioninfo | jq -r '.rssi'

# Get BSSID (router MAC)
termux-wifi-connectioninfo | jq -r '.bssid'

# Get link speed
termux-wifi-connectioninfo | jq -r '.link_speed_mbps'

# WiFi info formatted
termux-wifi-connectioninfo | jq -r '
"SSID: \(.ssid // "Not connected")",
"IP: \(.ip // "N/A")",
"Signal: \(.rssi) dBm",
"Speed: \(.link_speed_mbps) Mbps",
"Frequency: \(.frequency_mhz) MHz"
'

# Signal strength indicator
cat > wifi_signal.sh << 'EOF'
#!/bin/bash
RSSI=$(termux-wifi-connectioninfo | jq -r '.rssi')
if [ "$RSSI" = "null" ]; then
    echo "Not connected to WiFi"
    exit 1
fi

if [ $RSSI -gt -50 ]; then
    QUALITY="Excellent"
    BARS="▂▄▆█"
elif [ $RSSI -gt -60 ]; then
    QUALITY="Good"
    BARS="▂▄▆_"
elif [ $RSSI -gt -70 ]; then
    QUALITY="Fair"
    BARS="▂▄__"
else
    QUALITY="Weak"
    BARS="▂___"
fi

echo "WiFi Signal: $BARS $QUALITY ($RSSI dBm)"
EOF
```

### Sensor Data

```bash
# List all available sensors
termux-sensor -l
termux-sensor -s list

# Get accelerometer data (single reading)
termux-sensor -s accelerometer -n 1

# Get gyroscope data
termux-sensor -s gyroscope -n 1

# Get magnetometer (compass) data
termux-sensor -s magnetometer -n 1

# Get light sensor data
termux-sensor -s light -n 1

# Get proximity sensor data
termux-sensor -s proximity -n 1

# Get barometer data
termux-sensor -s pressure -n 1

# Multiple sensors at once
termux-sensor -s "accelerometer,gyroscope,magnetometer" -n 1

# Continuous monitoring (every 1000ms)
termux-sensor -s accelerometer -d 1000

# Continuous multiple sensors (every 500ms)
termux-sensor -s "accelerometer,gyroscope" -d 500

# Parse accelerometer values
termux-sensor -s accelerometer -n 1 | jq '.accelerometer.values'

# Accelerometer X value
termux-sensor -s accelerometer -n 1 | jq '.accelerometer.values[0]'

# Create compass script
cat > compass.sh << 'EOF'
#!/bin/bash
DATA=$(termux-sensor -s magnetometer -n 1)
X=$(echo $DATA | jq '.magnetometer.values[0]')
Y=$(echo $DATA | jq '.magnetometer.values[1]')
AZIMUTH=$(echo "scale=0; ($Y>0?360:0) + (a($X/$Y) * 180 / 3.14159)" | bc -l)
echo "Compass: ${AZIMUTH%.*}°"
EOF
```

### Fingerprint Authentication

```bash
# Trigger fingerprint scan
termux-fingerprint

# Check result
termux-fingerprint | jq -r '.auth_result'

# Get reason
termux-fingerprint | jq -r '.auth_result_reason'

# Fingerprint guard script
cat > fingerprint_guard.sh << 'EOF'
#!/bin/bash
echo "🔐 Fingerprint authentication required..."
RESULT=$(termux-fingerprint)
AUTH=$(echo $RESULT | jq -r '.auth_result')

if [ "$AUTH" = "AUTH_RESULT_SUCCESS" ]; then
    echo "✅ Authentication successful!"
    # Add your protected commands here
else
    REASON=$(echo $RESULT | jq -r '.auth_result_reason')
    echo "❌ Authentication failed: $REASON"
    exit 1
fi
EOF
```

### Location (GPS)

```bash
# Get network-based location (faster, less accurate)
termux-location

# Get GPS location (slower, more accurate)
termux-location -p gps

# Get passive location (cached, instant)
termux-location -p passive

# Extract coordinates
termux-location | jq -r '"\(.latitude), \(.longitude)"'

# Get latitude only
termux-location | jq -r '.latitude'

# Get longitude only
termux-location | jq -r '.longitude'

# Get accuracy
termux-location | jq -r '.accuracy'

# Location with GPS and timeout
termux-location -p gps -r 10

# Google Maps link
termux-location | jq -r '"https://maps.google.com/?q=\(.latitude),\(.longitude)"'

# Location logger
cat > location_logger.sh << 'EOF'
#!/bin/bash
LOG_FILE="location_history.csv"
echo "timestamp,latitude,longitude,accuracy,provider" > $LOG_FILE

while true; do
    LOC=$(termux-location -p network 2>/dev/null)
    if [ $? -eq 0 ]; then
        LAT=$(echo $LOC | jq -r '.latitude')
        LON=$(echo $LOC | jq -r '.longitude')
        ACC=$(echo $LOC | jq -r '.accuracy')
        PROV=$(echo $LOC | jq -r '.provider')
        echo "$(date -Iseconds),$LAT,$LON,$ACC,$PROV" >> $LOG_FILE
        echo "Location logged: $LAT, $LON"
    fi
    sleep 300  # Every 5 minutes
done
EOF
```

---

## 💻 PRACTICAL EXAMPLES (20+)

### Example 1: Battery Health Monitor

```bash
#!/bin/bash
# battery_health.sh - Monitor battery health and send alerts

check_battery() {
    DATA=$(termux-battery-status)
    PERCENT=$(echo $DATA | jq -r '.percentage')
    HEALTH=$(echo $DATA | jq -r '.health')
    TEMP=$(echo $DATA | jq -r '.temperature')
    STATUS=$(echo $DATA | jq -r '.status')
    
    echo "━━━━━━━━━━━━━━━━━━━━━━━━━━"
    echo "🔋 BATTERY STATUS"
    echo "━━━━━━━━━━━━━━━━━━━━━━━━━━"
    echo "Level:     ${PERCENT}%"
    echo "Health:    $HEALTH"
    echo "Temp:      ${TEMP}°C"
    echo "Status:    $STATUS"
    echo "━━━━━━━━━━━━━━━━━━━━━━━━━━"
    
    # Alert conditions
    if [ $PERCENT -lt 15 ]; then
        termux-notification --title "⚠️ Low Battery" --content "Battery at ${PERCENT}%"
        termux-vibrate
    fi
    
    if [ $(echo "$TEMP > 40" | bc) -eq 1 ]; then
        termux-notification --title "🔥 Overheating" --content "Battery temp: ${TEMP}°C"
    fi
}

check_battery
```

### Example 2: Smart Brightness Automation

```bash
#!/bin/bash
# smart_brightness.sh - Automatic brightness based on conditions

auto_brightness() {
    HOUR=$(date +%H)
    BATTERY=$(termux-battery-status | jq -r '.percentage')
    
    # Night mode (8 PM - 6 AM)
    if [ $HOUR -ge 20 ] || [ $HOUR -lt 6 ]; then
        termux-brightness 30
        echo "🌙 Night mode: Low brightness"
        return
    fi
    
    # Low battery mode
    if [ $BATTERY -lt 20 ]; then
        termux-brightness 80
        echo "🔋 Power saving: Medium brightness"
        return
    fi
    
    # Day mode
    termux-brightness 180
    echo "☀️ Day mode: High brightness"
}

auto_brightness
```

### Example 3: Meeting Mode Script

```bash
#!/bin/bash
# meeting_mode.sh - Toggle meeting mode

STATE_FILE="/tmp/meeting_mode"

if [ -f "$STATE_FILE" ]; then
    # Restore previous volumes
    source $STATE_FILE
    termux-volume stream_ring $RING_VOL
    termux-volume stream_notification $NOTIF_VOL
    termux-volume stream_music $MUSIC_VOL
    rm $STATE_FILE
    termux-notification --title "Meeting Mode OFF" --content "Volumes restored"
else
    # Save current volumes and mute
    RING_VOL=$(termux-volume stream_ring | jq -r '.volume')
    NOTIF_VOL=$(termux-volume stream_notification | jq -r '.volume')
    MUSIC_VOL=$(termux-volume stream_music | jq -r '.volume')
    
    echo "RING_VOL=$RING_VOL" > $STATE_FILE
    echo "NOTIF_VOL=$NOTIF_VOL" >> $STATE_FILE
    echo "MUSIC_VOL=$MUSIC_VOL" >> $STATE_FILE
    
    termux-volume stream_ring 0
    termux-volume stream_notification 0
    termux-volume stream_music 0
    
    termux-notification --title "Meeting Mode ON" --content "Phone muted"
fi
```

### Example 4: Device Info Reporter

```bash
#!/bin/bash
# device_report.sh - Generate comprehensive device report

generate_report() {
    echo "╔════════════════════════════════════════════════╗"
    echo "║         DEVICE INFORMATION REPORT              ║"
    echo "╚════════════════════════════════════════════════╝"
    echo ""
    
    # Battery
    echo "┌─────────────────────────────────────────────────┐"
    echo "│ 🔋 BATTERY                                       │"
    echo "├─────────────────────────────────────────────────┤"
    termux-battery-status | jq -r '
    "│ Level:       \(.percentage)%                      ",
    "│ Health:      \(.health)                           ",
    "│ Temperature: \(.temperature)°C                    ",
    "│ Status:      \(.status)                           "'
    echo "└─────────────────────────────────────────────────┘"
    echo ""
    
    # Telephony
    echo "┌─────────────────────────────────────────────────┐"
    echo "│ 📱 TELEPHONY                                     │"
    echo "├─────────────────────────────────────────────────┤"
    termux-telephony-deviceinfo | jq -r '
    "│ IMEI:        \(.imei // "N/A")                    ",
    "│ SIM:         \(.sim_operator_name // "N/A")       ",
    "│ Network:     \(.network_type // "N/A")            ",
    "│ Roaming:     \(.network_roaming)                  "'
    echo "└─────────────────────────────────────────────────┘"
    echo ""
    
    # WiFi
    echo "┌─────────────────────────────────────────────────┐"
    echo "│ 📶 WIFI                                          │"
    echo "├─────────────────────────────────────────────────┤"
    termux-wifi-connectioninfo | jq -r '
    "│ SSID:        \(.ssid // "Not connected")          ",
    "│ IP:          \(.ip // "N/A")                      ",
    "│ Signal:      \(.rssi) dBm                         ",
    "│ Speed:       \(.link_speed_mbps) Mbps             "'
    echo "└─────────────────────────────────────────────────┘"
    echo ""
    
    echo "Report generated: $(date)"
}

generate_report
```

### Example 5: WiFi Signal Analyzer

```bash
#!/bin/bash
# wifi_analyzer.sh - Continuous WiFi signal monitoring

monitor_wifi() {
    echo "WiFi Signal Monitor (Ctrl+C to stop)"
    echo "===================================="
    
    while true; do
        DATA=$(termux-wifi-connectioninfo 2>/dev/null)
        SSID=$(echo $DATA | jq -r '.ssid // "N/A"')
        RSSI=$(echo $DATA | jq -r '.rssi // 0')
        SPEED=$(echo $DATA | jq -r '.link_speed_mbps // 0')
        
        # Signal quality indicator
        if [ $RSSI -gt -50 ]; then
            BARS="████"
            QUALITY="Excellent"
        elif [ $RSSI -gt -60 ]; then
            BARS="███░"
            QUALITY="Good"
        elif [ $RSSI -gt -70 ]; then
            BARS="██░░"
            QUALITY="Fair"
        else
            BARS="█░░░"
            QUALITY="Weak"
        fi
        
        echo "\r[$(date +%H:%M:%S)] $SSID | [$BARS] $QUALITY ($RSSI dBm) | $SPEED Mbps"
        sleep 2
    done
}

monitor_wifi
```

### Example 6: Motion Detector

```bash
#!/bin/bash
# motion_detector.sh - Detect phone movement using accelerometer

detect_motion() {
    THRESHOLD=0.5
    
    # Get baseline
    BASE=$(termux-sensor -s accelerometer -n 1)
    BASE_X=$(echo $BASE | jq '.accelerometer.values[0]')
    BASE_Y=$(echo $BASE | jq '.accelerometer.values[1]')
    BASE_Z=$(echo $BASE | jq '.accelerometer.values[2]')
    
    echo "Baseline established. Monitoring for motion..."
    
    while true; do
        CURRENT=$(termux-sensor -s accelerometer -n 1)
        CUR_X=$(echo $CURRENT | jq '.accelerometer.values[0]')
        CUR_Y=$(echo $CURRENT | jq '.accelerometer.values[1]')
        CUR_Z=$(echo $CURRENT | jq '.accelerometer.values[2]')
        
        # Calculate difference
        DIFF_X=$(echo "scale=2; $CUR_X - $BASE_X" | bc)
        DIFF_Y=$(echo "scale=2; $CUR_Y - $BASE_Y" | bc)
        DIFF_Z=$(echo "scale=2; $CUR_Z - $BASE_Z" | bc)
        
        # Check if movement exceeds threshold
        ABS_DIFF=$(echo "scale=2; sqrt($DIFF_X^2 + $DIFF_Y^2 + $DIFF_Z^2)" | bc)
        
        if [ $(echo "$ABS_DIFF > $THRESHOLD" | bc) -eq 1 ]; then
            echo "🚨 Motion detected! Magnitude: $ABS_DIFF"
            termux-vibrate -d 100
        fi
        
        sleep 0.5
    done
}

detect_motion
```

### Example 7: Compass Application

```bash
#!/bin/bash
# compass.sh - Digital compass using magnetometer

get_direction() {
    AZIMUTH=$1
    
    if [ $(echo "$AZIMUTH >= 337.5 || $AZIMUTH < 22.5" | bc) -eq 1 ]; then
        echo "N"
    elif [ $(echo "$AZIMUTH >= 22.5 && $AZIMUTH < 67.5" | bc) -eq 1 ]; then
        echo "NE"
    elif [ $(echo "$AZIMUTH >= 67.5 && $AZIMUTH < 112.5" | bc) -eq 1 ]; then
        echo "E"
    elif [ $(echo "$AZIMUTH >= 112.5 && $AZIMUTH < 157.5" | bc) -eq 1 ]; then
        echo "SE"
    elif [ $(echo "$AZIMUTH >= 157.5 && $AZIMUTH < 202.5" | bc) -eq 1 ]; then
        echo "S"
    elif [ $(echo "$AZIMUTH >= 202.5 && $AZIMUTH < 247.5" | bc) -eq 1 ]; then
        echo "SW"
    elif [ $(echo "$AZIMUTH >= 247.5 && $AZIMUTH < 292.5" | bc) -eq 1 ]; then
        echo "W"
    else
        echo "NW"
    fi
}

compass_loop() {
    echo "🧭 Digital Compass (Ctrl+C to stop)"
    echo "=================================="
    
    while true; do
        DATA=$(termux-sensor -s magnetometer -n 1 2>/dev/null)
        X=$(echo $DATA | jq '.magnetometer.values[0]')
        Y=$(echo $DATA | jq '.magnetometer.values[1]')
        
        # Calculate azimuth
        AZIMUTH=$(echo "scale=0; (a($Y/$X) * 180 / 3.14159 + 360) % 360" | bc -l)
        DIR=$(get_direction $AZIMUTH)
        
        printf "\r        🧭 %3d° %s   " ${AZIMUTH%.*} $DIR
        sleep 0.2
    done
}

compass_loop
```

### Example 8: Location Tracker

```bash
#!/bin/bash
# location_tracker.sh - Track and log GPS location

TRACK_FILE="gps_track_$(date +%Y%m%d_%H%M%S).gpx"

start_tracking() {
    echo '<?xml version="1.0"?>' > $TRACK_FILE
    echo '<gpx version="1.1">' >> $TRACK_FILE
    echo '<trk><trkseg>' >> $TRACK_FILE
    
    echo "📍 GPS Tracking started (Ctrl+C to stop)"
    echo "   Log file: $TRACK_FILE"
    
    while true; do
        LOC=$(termux-location -p network 2>/dev/null)
        LAT=$(echo $LOC | jq -r '.latitude')
        LON=$(echo $LOC | jq -r '.longitude')
        ELE=$(echo $LOC | jq -r '.altitude')
        TIME=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
        
        echo "<trkpt lat=\"$LAT\" lon=\"$LON\"><ele>$ELE</ele><time>$TIME</time></trkpt>" >> $TRACK_FILE
        
        echo "📍 $LAT, $LON @ $TIME"
        sleep 10
    done
}

stop_tracking() {
    echo '</trkseg></trk>' >> $TRACK_FILE
    echo '</gpx>' >> $TRACK_FILE
    echo "Tracking stopped. GPX file saved: $TRACK_FILE"
}

trap stop_tracking EXIT
start_tracking
```

### Example 9: Secure Script Launcher

```bash
#!/bin/bash
# secure_launch.sh - Biometric-protected script launcher

authenticate() {
    echo "🔐 Fingerprint authentication required..."
    RESULT=$(termux-fingerprint 2>/dev/null)
    AUTH=$(echo $RESULT | jq -r '.auth_result')
    
    if [ "$AUTH" = "AUTH_RESULT_SUCCESS" ]; then
        echo "✅ Authentication successful!"
        return 0
    else
        REASON=$(echo $RESULT | jq -r '.auth_result_reason')
        echo "❌ Authentication failed: $REASON"
        return 1
    fi
}

# Main script
if authenticate; then
    # Protected code here
    echo "Running protected operations..."
    # Your sensitive commands here
else
    exit 1
fi
```

### Example 10: Phone Status Dashboard

```bash
#!/bin/bash
# status_dashboard.sh - Real-time phone status display

draw_dashboard() {
    clear
    echo "╔════════════════════════════════════════════════════╗"
    echo "║          📱 PHONE STATUS DASHBOARD                  ║"
    echo "╠════════════════════════════════════════════════════╣"
    
    # Battery
    BAT=$(termux-battery-status)
    BAT_PCT=$(echo $BAT | jq -r '.percentage')
    BAT_STATUS=$(echo $BAT | jq -r '.status')
    BAT_TEMP=$(echo $BAT | jq -r '.temperature')
    
    BAR=""
    for i in $(seq 1 10); do
        if [ $((i*10)) -le $BAT_PCT ]; then
            BAR="${BAR}█"
        else
            BAR="${BAR}░"
        fi
    done
    
    echo "║ 🔋 Battery: [$BAR] ${BAT_PCT}%   "
    echo "║    Status: $BAT_STATUS | Temp: ${BAT_TEMP}°C"
    echo "╠════════════════════════════════════════════════════╣"
    
    # WiFi
    WIFI=$(termux-wifi-connectioninfo 2>/dev/null)
    SSID=$(echo $WIFI | jq -r '.ssid // "Not connected"')
    RSSI=$(echo $WIFI | jq -r '.rssi // 0')
    IP=$(echo $WIFI | jq -r '.ip // "N/A"')
    
    if [ $RSSI -gt -60 ]; then
        WIFI_QUAL="Good"
    elif [ $RSSI -gt -70 ]; then
        WIFI_QUAL="Fair"
    else
        WIFI_QUAL="Weak"
    fi
    
    echo "║ 📶 WiFi: $SSID"
    echo "║    IP: $IP | Signal: $WIFI_QUAL ($RSSI dBm)"
    echo "╠════════════════════════════════════════════════════╣"
    
    # Network
    NET=$(termux-telephony-deviceinfo 2>/dev/null)
    CARRIER=$(echo $NET | jq -r '.sim_operator_name // "N/A"')
    NET_TYPE=$(echo $NET | jq -r '.network_type // "N/A"')
    
    echo "║ 📡 Carrier: $CARRIER"
    echo "║    Network: $NET_TYPE"
    echo "╠════════════════════════════════════════════════════╣"
    
    # Time
    echo "║ 🕐 $(date '+%Y-%m-%d %H:%M:%S')"
    echo "╚════════════════════════════════════════════════════╝"
    echo ""
    echo "Press Ctrl+C to exit"
}

# Continuous update
while true; do
    draw_dashboard
    sleep 2
done
```

### Example 11: Battery Saver Mode

```bash
#!/bin/bash
# battery_saver.sh - Activate battery saving measures

activate_saver() {
    echo "🔋 Activating Battery Saver Mode..."
    
    # Dim screen
    termux-brightness 50
    echo "  ✓ Brightness reduced"
    
    # Lower volumes
    termux-volume stream_music 5
    termux-volume stream_notification 3
    echo "  ✓ Volumes lowered"
    
    # Show status
    BAT=$(termux-battery-status | jq -r '.percentage')
    termux-notification --title "Battery Saver" --content "Activated at ${BAT}%"
    
    echo "  ✓ Battery Saver Mode active"
}

deactivate_saver() {
    echo "🔋 Deactivating Battery Saver Mode..."
    
    # Restore settings
    termux-brightness 150
    termux-volume stream_music 10
    termux-volume stream_notification 5
    
    termux-notification --title "Battery Saver" --content "Deactivated"
    echo "  ✓ Normal mode restored"
}

case "$1" in
    on) activate_saver ;;
    off) deactivate_saver ;;
    *) echo "Usage: $0 {on|off}" ;;
esac
```

### Example 12: Network Info Collector

```bash
#!/bin/bash
# network_info.sh - Collect network information

collect_network_info() {
    echo "═══════════════════════════════════════"
    echo "       NETWORK INFORMATION             "
    echo "═══════════════════════════════════════"
    echo ""
    
    # WiFi Info
    echo "📶 WIFI INFORMATION"
    echo "───────────────────"
    WIFI=$(termux-wifi-connectioninfo 2>/dev/null)
    echo "$WIFI" | jq -r '
    "SSID:         \(.ssid // "Not connected")",
    "BSSID:        \(.bssid // "N/A")",
    "IP Address:   \(.ip // "N/A")",
    "Frequency:    \(.frequency_mhz // "N/A") MHz",
    "Link Speed:   \(.link_speed_mbps // "N/A") Mbps",
    "Signal:       \(.rssi // "N/A") dBm",
    "Hidden:       \(.ssid_hidden)"
    '
    echo ""
    
    # Cell Info
    echo "📡 CELL INFORMATION"
    echo "───────────────────"
    CELL=$(termux-telephony-cellinfo 2>/dev/null)
    echo "$CELL" | jq -r '
    "Type:         \(.type // "N/A")",
    "MCC:          \(.mcc // "N/A")",
    "MNC:          \(.mnc // "N/A")",
    "LAC:          \(.lac // "N/A")",
    "Cell ID:      \(.cid // "N/A")",
    "Signal:       \(.dbm // "N/A") dBm"
    '
    echo ""
    
    # Telephony
    echo "📱 TELEPHONY INFORMATION"
    echo "───────────────────"
    TELEPHONY=$(termux-telephony-deviceinfo 2>/dev/null)
    echo "$TELEPHONY" | jq -r '
    "Carrier:      \(.sim_operator_name // "N/A")",
    "Network:      \(.network_type // "N/A")",
    "Country:      \(.network_country // "N/A")",
    "Roaming:      \(.network_roaming)",
    "Phone Type:   \(.phone_type // "N/A")"
    '
    echo ""
    
    echo "═══════════════════════════════════════"
}

collect_network_info
```

### Example 13: Sensor Data Logger

```bash
#!/bin/bash
# sensor_logger.sh - Log sensor data to file

LOG_DIR="sensor_logs"
mkdir -p $LOG_DIR

log_sensor() {
    SENSOR=$1
    FILE="$LOG_DIR/${SENSOR}_$(date +%Y%m%d).csv"
    
    # Create header if new file
    if [ ! -f $FILE ]; then
        echo "timestamp,x,y,z" > $FILE
    fi
    
    DATA=$(termux-sensor -s $SENSOR -n 1 2>/dev/null)
    X=$(echo $DATA | jq ".${SENSOR}.values[0]")
    Y=$(echo $DATA | jq ".${SENSOR}.values[1]")
    Z=$(echo $DATA | jq ".${SENSOR}.values[2]")
    
    echo "$(date -Iseconds),$X,$Y,$Z" >> $FILE
}

echo "Logging sensors... (Ctrl+C to stop)"

while true; do
    log_sensor "accelerometer"
    log_sensor "gyroscope"
    log_sensor "magnetometer"
    echo "[$(date +%H:%M:%S)] Data logged"
    sleep 5
done
```

### Example 14: Anti-Theft Detector

```bash
#!/bin/bash
# anti_theft.sh - Detect unauthorized movement

ALERT_THRESHOLD=2.0

echo "🔒 Anti-Theft Mode Active"
echo "   Place phone on stable surface..."

# Get baseline
sleep 2
BASE=$(termux-sensor -s accelerometer -n 1)
BASE_X=$(echo $BASE | jq '.accelerometer.values[0]')
BASE_Y=$(echo $BASE | jq '.accelerometer.values[1]')
BASE_Z=$(echo $BASE | jq '.accelerometer.values[2]')

echo "   Baseline set. Monitoring..."

while true; do
    CURRENT=$(termux-sensor -s accelerometer -n 1)
    CUR_X=$(echo $CURRENT | jq '.accelerometer.values[0]')
    CUR_Y=$(echo $CURRENT | jq '.accelerometer.values[1]')
    CUR_Z=$(echo $CURRENT | jq '.accelerometer.values[2]')
    
    # Calculate magnitude change
    DIFF=$(echo "scale=2; sqrt(($CUR_X-$BASE_X)^2 + ($CUR_Y-$BASE_Y)^2 + ($CUR_Z-$BASE_Z)^2)" | bc)
    
    if [ $(echo "$DIFF > $ALERT_THRESHOLD" | bc) -eq 1 ]; then
        echo "🚨 ALERT! Movement detected!"
        
        # Trigger alarm
        for i in {1..5}; do
            termux-vibrate -d 500
            termux-volume stream_alarm 7
            sleep 0.5
        done
        
        # Send notification
        termux-notification --title "🚨 ANTI-THEFT ALERT" --content "Phone movement detected!" --priority high
        
        # Take photo if available
        # termux-camera-photo theft_alert.jpg
        
        break
    fi
    
    sleep 0.5
done
```

### Example 15: Location-Based Automation

```bash
#!/bin/bash
# location_automation.sh - Trigger actions based on location

HOME_LAT="28.6139"
HOME_LON="77.2090"
RADIUS="0.001"  # ~100m

calculate_distance() {
    LAT1=$1
    LON1=$2
    LAT2=$3
    LON2=$4
    
    # Simple approximation
    echo "scale=6; sqrt(($LAT1-$LAT2)^2 + ($LON1-$LON2)^2)" | bc
}

check_location() {
    LOC=$(termux-location -p network 2>/dev/null)
    CUR_LAT=$(echo $LOC | jq -r '.latitude')
    CUR_LON=$(echo $LOC | jq -r '.longitude')
    
    DIST=$(calculate_distance $CUR_LAT $CUR_LON $HOME_LAT $HOME_LON)
    
    if [ $(echo "$DIST < $RADIUS" | bc) -eq 1 ]; then
        echo "🏠 Home detected!"
        # Home actions
        termux-volume stream_ring 7
        termux-volume stream_notification 5
        termux-brightness 150
    else
        echo "📍 Away from home"
        # Away actions
        termux-volume stream_ring 3
        termux-volume stream_notification 3
    fi
}

echo "Location automation active..."
while true; do
    check_location
    sleep 60
done
```

### Example 16: Device Fingerprint Collector

```bash
#!/bin/bash
# device_fingerprint.sh - Collect unique device identifiers

collect_fingerprint() {
    echo "═════════════════════════════════════════════════"
    echo "        DEVICE FINGERPRINT COLLECTOR             "
    echo "═════════════════════════════════════════════════"
    
    # Telephony
    TEL=$(termux-telephony-deviceinfo 2>/dev/null)
    IMEI=$(echo $TEL | jq -r '.imei // "N/A"')
    IMSI=$(echo $TEL | jq -r '.sim_subscriber_id // "N/A"')
    ICCID=$(echo $TEL | jq -r '.sim_serial_number // "N/A"')
    
    # WiFi MAC (may be randomized on Android 10+)
    WIFI=$(termux-wifi-connectioninfo 2>/dev/null)
    MAC=$(echo $WIFI | jq -r '.mac_address // "N/A"')
    
    # Android ID
    ANDROID_ID=$(settings get secure android_id 2>/dev/null || echo "N/A")
    
    echo ""
    echo "📱 UNIQUE IDENTIFIERS:"
    echo "─────────────────────"
    echo "  IMEI:        $IMEI"
    echo "  IMSI:        $IMSI"
    echo "  ICCID:       $ICCID"
    echo "  WiFi MAC:    $MAC"
    echo "  Android ID:  $ANDROID_ID"
    echo ""
    
    # Generate hash
    HASH=$(echo -n "${IMEI}${IMSI}${ICCID}" | md5sum | cut -d' ' -f1)
    echo "🔑 Device Hash: $HASH"
    echo "═════════════════════════════════════════════════"
}

collect_fingerprint
```

### Example 17: Step Counter

```bash
#!/bin/bash
# step_counter.sh - Count steps using step counter sensor

count_steps() {
    echo "👣 Step Counter"
    echo "─────────────────"
    
    # Check if step counter sensor exists
    SENSORS=$(termux-sensor -l 2>/dev/null)
    
    if echo "$SENSORS" | grep -q "step_counter"; then
        DATA=$(termux-sensor -s step_counter -n 1 2>/dev/null)
        STEPS=$(echo $DATA | jq '.step_counter.values[0]')
        echo "Total steps: $STEPS"
    else
        echo "Step counter sensor not available on this device"
        echo "Using accelerometer-based detection..."
        
        # Fallback to accelerometer
        THRESHOLD=12.0
        STEPS=0
        
        PREV_MAG=0
        
        while true; do
            ACC=$(termux-sensor -s accelerometer -n 1 2>/dev/null)
            X=$(echo $ACC | jq '.accelerometer.values[0]')
            Y=$(echo $ACC | jq '.accelerometer.values[1]')
            Z=$(echo $ACC | jq '.accelerometer.values[2]')
            
            MAG=$(echo "scale=2; sqrt($X^2 + $Y^2 + $Z^2)" | bc)
            
            # Detect step (magnitude spike)
            DIFF=$(echo "scale=2; $MAG - $PREV_MAG" | bc)
            ABS_DIFF=${DIFF#-}
            
            if [ $(echo "$ABS_DIFF > $THRESHOLD" | bc) -eq 1 ]; then
                STEPS=$((STEPS + 1))
                printf "\rSteps: $STEPS    "
            fi
            
            PREV_MAG=$MAG
            sleep 0.1
        done
    fi
}

count_steps
```

### Example 18: Brightness Schedule

```bash
#!/bin/bash
# brightness_schedule.sh - Automated brightness schedule

set_scheduled_brightness() {
    HOUR=$(date +%H)
    
    case $HOUR in
        00|01|02|03|04|05)
            # Night: Very dim
            termux-brightness 20
            LEVEL="Night (dim)"
            ;;
        06|07|08)
            # Early morning: Medium
            termux-brightness 80
            LEVEL="Morning (medium)"
            ;;
        09|10|11|12|13|14|15|16)
            # Day: Bright
            termux-brightness 200
            LEVEL="Day (bright)"
            ;;
        17|18|19)
            # Evening: Medium
            termux-brightness 120
            LEVEL="Evening (medium)"
            ;;
        20|21|22|23)
            # Night: Dim
            termux-brightness 40
            LEVEL="Night (dim)"
            ;;
    esac
    
    echo "[$(date +%H:%M)] Brightness set: $LEVEL"
}

# Run as daemon
echo "Brightness scheduler running..."
while true; do
    set_scheduled_brightness
    sleep 300  # Check every 5 minutes
done
```

### Example 19: WiFi Change Alert

```bash
#!/bin/bash
# wifi_change_alert.sh - Alert on WiFi network changes

PREV_SSID=""

monitor_wifi_changes() {
    echo "📶 WiFi Change Monitor active..."
    
    while true; do
        CURRENT=$(termux-wifi-connectioninfo 2>/dev/null)
        SSID=$(echo $CURRENT | jq -r '.ssid // "Not connected"')
        
        if [ "$SSID" != "$PREV_SSID" ] && [ -n "$PREV_SSID" ]; then
            termux-notification --title "📶 WiFi Changed" \
                --content "Connected to: $SSID (was: $PREV_SSID)"
            echo "[$(date)] WiFi changed: $PREV_SSID → $SSID"
        fi
        
        PREV_SSID=$SSID
        sleep 5
    done
}

monitor_wifi_changes
```

### Example 20: Complete Phone Info Python Script

```python
#!/usr/bin/env python3
"""
phone_info.py - Complete phone information extraction
Author: T3rmuxk1ng
"""

import subprocess
import json
import sys
from datetime import datetime

def run_termux_command(cmd):
    """Execute termux command and return JSON output"""
    try:
        result = subprocess.run(
            cmd.split(),
            capture_output=True,
            text=True,
            timeout=30
        )
        if result.returncode == 0:
            return json.loads(result.stdout)
        return None
    except Exception as e:
        return None

def get_battery_info():
    """Get battery information"""
    return run_termux_command('termux-battery-status')

def get_telephony_info():
    """Get telephony information"""
    return run_termux_command('termux-telephony-deviceinfo')

def get_wifi_info():
    """Get WiFi connection information"""
    return run_termux_command('termux-wifi-connectioninfo')

def get_cell_info():
    """Get cell tower information"""
    return run_termux_command('termux-telephony-cellinfo')

def get_location():
    """Get device location"""
    return run_termux_command('termux-location -p network')

def get_sensor_data(sensor='accelerometer'):
    """Get sensor data"""
    return run_termux_command(f'termux-sensor -s {sensor} -n 1')

def get_wifi_signal_quality(rssi):
    """Convert RSSI to quality description"""
    if rssi > -50:
        return "Excellent"
    elif rssi > -60:
        return "Good"
    elif rssi > -70:
        return "Fair"
    else:
        return "Weak"

def generate_report():
    """Generate comprehensive phone report"""
    print("╔" + "═"*50 + "╗")
    print("║" + "PHONE INFORMATION REPORT".center(50) + "║")
    print("║" + f"Generated: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}".center(50) + "║")
    print("╚" + "═"*50 + "╝")
    print()
    
    # Battery
    print("┌" + "─"*50 + "┐")
    print("│ 🔋 BATTERY INFORMATION")
    print("├" + "─"*50 + "┤")
    battery = get_battery_info()
    if battery:
        print(f"│ Level:       {battery.get('percentage', 'N/A')}%")
        print(f"│ Health:      {battery.get('health', 'N/A')}")
        print(f"│ Status:      {battery.get('status', 'N/A')}")
        print(f"│ Temperature: {battery.get('temperature', 'N/A')}°C")
        print(f"│ Plugged:     {battery.get('plugged', 'N/A')}")
    else:
        print("│ Unable to get battery info")
    print("└" + "─"*50 + "┘")
    print()
    
    # WiFi
    print("┌" + "─"*50 + "┐")
    print("│ 📶 WIFI INFORMATION")
    print("├" + "─"*50 + "┤")
    wifi = get_wifi_info()
    if wifi:
        rssi = wifi.get('rssi', 0)
        quality = get_wifi_signal_quality(rssi)
        print(f"│ SSID:        {wifi.get('ssid', 'Not connected')}")
        print(f"│ IP:          {wifi.get('ip', 'N/A')}")
        print(f"│ BSSID:       {wifi.get('bssid', 'N/A')}")
        print(f"│ Signal:      {rssi} dBm ({quality})")
        print(f"│ Speed:       {wifi.get('link_speed_mbps', 'N/A')} Mbps")
        print(f"│ Frequency:   {wifi.get('frequency_mhz', 'N/A')} MHz")
    else:
        print("│ Not connected to WiFi")
    print("└" + "─"*50 + "┘")
    print()
    
    # Telephony
    print("┌" + "─"*50 + "┐")
    print("│ 📱 TELEPHONY INFORMATION")
    print("├" + "─"*50 + "┤")
    telephony = get_telephony_info()
    if telephony:
        print(f"│ IMEI:        {telephony.get('imei', 'N/A')}")
        print(f"│ SIM:         {telephony.get('sim_operator_name', 'N/A')}")
        print(f"│ Network:     {telephony.get('network_type', 'N/A')}")
        print(f"│ Phone Type:  {telephony.get('phone_type', 'N/A')}")
        print(f"│ Roaming:     {telephony.get('network_roaming', False)}")
    else:
        print("│ Unable to get telephony info")
    print("└" + "─"*50 + "┘")
    print()
    
    # Location
    print("┌" + "─"*50 + "┐")
    print("│ 📍 LOCATION")
    print("├" + "─"*50 + "┤")
    location = get_location()
    if location:
        lat = location.get('latitude', 'N/A')
        lon = location.get('longitude', 'N/A')
        acc = location.get('accuracy', 'N/A')
        print(f"│ Latitude:    {lat}")
        print(f"│ Longitude:   {lon}")
        print(f"│ Accuracy:    {acc}m")
        print(f"│ Maps:        https://maps.google.com/?q={lat},{lon}")
    else:
        print("│ Location unavailable")
    print("└" + "─"*50 + "┘")

if __name__ == '__main__':
    generate_report()
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Battery Monitor

```bash
# Task: Create a battery monitoring script
# Requirements:
# 1. Check battery every minute
# 2. Alert if below 20%
# 3. Alert if temperature above 40°C
# 4. Log to file with timestamp

cat > battery_monitor.sh << 'EOF'
#!/bin/bash
LOG_FILE="battery_log.txt"

while true; do
    BAT=$(termux-battery-status)
    PCT=$(echo $BAT | jq -r '.percentage')
    TEMP=$(echo $BAT | jq -r '.temperature')
    STATUS=$(echo $BAT | jq -r '.status')
    
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')
    echo "$TIMESTAMP | $PCT% | ${TEMP}°C | $STATUS" >> $LOG_FILE
    
    if [ $PCT -lt 20 ]; then
        termux-notification --title "⚠️ Low Battery" --content "${PCT}% remaining"
        termux-vibrate
    fi
    
    if [ $(echo "$TEMP > 40" | bc) -eq 1 ]; then
        termux-notification --title "🔥 Overheating" --content "Battery temp: ${TEMP}°C"
    fi
    
    sleep 60
done
EOF

chmod +x battery_monitor.sh
```

### Exercise 2: WiFi Analyzer

```bash
# Task: Analyze WiFi signal strength
# Requirements:
# 1. Get WiFi info
# 2. Calculate signal quality
# 3. Display with visual indicator
# 4. Log signal history

cat > wifi_analyzer.sh << 'EOF'
#!/bin/bash

analyze_signal() {
    RSSI=$1
    if [ $RSSI -gt -50 ]; then
        echo "Excellent ▂▄▆█"
    elif [ $RSSI -gt -60 ]; then
        echo "Good ▂▄▆_"
    elif [ $RSSI -gt -70 ]; then
        echo "Fair ▂▄__"
    else
        echo "Weak ▂___"
    fi
}

echo "WiFi Signal Analyzer"
echo "===================="

while true; do
    WIFI=$(termux-wifi-connectioninfo 2>/dev/null)
    SSID=$(echo $WIFI | jq -r '.ssid // "Not connected"')
    RSSI=$(echo $WIFI | jq -r '.rssi // 0')
    QUALITY=$(analyze_signal $RSSI)
    
    echo "\r[$(date +%H:%M:%S)] $SSID | $QUALITY ($RSSI dBm)   "
    sleep 2
done
EOF

chmod +x wifi_analyzer.sh
```

### Exercise 3: Device Info Exporter

```bash
# Task: Export device info to JSON file
# Requirements:
# 1. Collect all device information
# 2. Format as proper JSON
# 3. Save to file with timestamp

cat > export_device_info.sh << 'EOF'
#!/bin/bash
OUTPUT="device_info_$(date +%Y%m%d_%H%M%S).json"

jq -n \
    --argjson battery "$(termux-battery-status)" \
    --argjson telephony "$(termux-telephony-deviceinfo 2>/dev/null || echo '{}')" \
    --argjson wifi "$(termux-wifi-connectioninfo 2>/dev/null || echo '{}')" \
    --argjson cell "$(termux-telephony-cellinfo 2>/dev/null || echo '{}')" \
    --arg timestamp "$(date -Iseconds)" \
    '{
        timestamp: $timestamp,
        battery: $battery,
        telephony: $telephony,
        wifi: $wifi,
        cell: $cell
    }' > "$OUTPUT"

echo "Device info exported to: $OUTPUT"
cat "$OUTPUT" | jq .
EOF

chmod +x export_device_info.sh
```

### Exercise 4: Fingerprint-Protected Notes

```bash
# Task: Create fingerprint-protected note viewer
# Requirements:
# 1. Require fingerprint to view notes
# 2. Store notes in encrypted file
# 3. Decrypt only after authentication

cat > secure_notes.sh << 'EOF'
#!/bin/bash
NOTES_FILE="$HOME/.secure_notes.enc"

view_notes() {
    echo "🔐 Fingerprint required to view notes..."
    AUTH=$(termux-fingerprint | jq -r '.auth_result')
    
    if [ "$AUTH" = "AUTH_RESULT_SUCCESS" ]; then
        echo "✅ Authentication successful!"
        if [ -f "$NOTES_FILE" ]; then
            openssl enc -aes-256-cbc -d -in "$NOTES_FILE" -pass pass:fingerprint 2>/dev/null
        else
            echo "No notes found."
        fi
    else
        echo "❌ Authentication failed!"
    fi
}

add_note() {
    echo "🔐 Fingerprint required to add note..."
    AUTH=$(termux-fingerprint | jq -r '.auth_result')
    
    if [ "$AUTH" = "AUTH_RESULT_SUCCESS" ]; then
        echo -n "Enter note: "
        read NOTE
        echo "$(date): $NOTE" | openssl enc -aes-256-cbc -a -out "$NOTES_FILE" -pass pass:fingerprint
        echo "Note saved!"
    fi
}

case "$1" in
    view) view_notes ;;
    add) add_note ;;
    *) echo "Usage: $0 {view|add}" ;;
esac
EOF

chmod +x secure_notes.sh
```

### Exercise 5: Motion-Activated Camera

```bash
# Task: Take photo when motion is detected
# Requirements:
# 1. Monitor accelerometer
# 2. Detect significant movement
# 3. Capture photo on movement
# 4. Save with timestamp

cat > motion_camera.sh << 'EOF'
#!/bin/bash
THRESHOLD=3.0
PHOTO_DIR="$HOME/motion_photos"
mkdir -p "$PHOTO_DIR"

echo "📸 Motion-Activated Camera"
echo "   Threshold: $THRESHOLD"
echo "   Photos saved to: $PHOTO_DIR"

# Get baseline
BASE=$(termux-sensor -s accelerometer -n 1)
BASE_X=$(echo $BASE | jq '.accelerometer.values[0]')
BASE_Y=$(echo $BASE | jq '.accelerometer.values[1]')
BASE_Z=$(echo $BASE | jq '.accelerometer.values[2]')

echo "   Baseline set. Monitoring..."

while true; do
    CUR=$(termux-sensor -s accelerometer -n 1)
    CUR_X=$(echo $CUR | jq '.accelerometer.values[0]')
    CUR_Y=$(echo $CUR | jq '.accelerometer.values[1]')
    CUR_Z=$(echo $CUR | jq '.accelerometer.values[2]')
    
    DIFF=$(echo "scale=2; sqrt(($CUR_X-$BASE_X)^2 + ($CUR_Y-$BASE_Y)^2 + ($CUR_Z-$BASE_Z)^2)" | bc)
    
    if [ $(echo "$DIFF > $THRESHOLD" | bc) -eq 1 ]; then
        TIMESTAMP=$(date +%Y%m%d_%H%M%S)
        PHOTO="$PHOTO_DIR/motion_$TIMESTAMP.jpg"
        termux-camera-photo "$PHOTO" 2>/dev/null
        echo "[$(date)] Motion detected! Photo: $PHOTO"
        termux-notification --title "Motion Detected" --content "Photo captured"
        sleep 5  # Cooldown
    fi
    
    sleep 0.5
done
EOF

chmod +x motion_camera.sh
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: termux-battery-status returns null

```bash
# Cause: Termux:API app not installed or not running

# Solution 1: Check if termux-api package is installed
pkg list-installed | grep termux-api

# If not installed:
pkg install termux-api -y

# Solution 2: Check Termux:API app
# Go to Android Settings → Apps → Termux:API
# Make sure it's installed and not disabled

# Solution 3: Check if Termux:API service is running
# Open Termux:API app once to start the service

# Solution 4: Grant battery optimization exemption
# Settings → Apps → Termux:API → Battery → Unrestricted
# Settings → Apps → Termux → Battery → Unrestricted
```

### Problem 2: termux-telephony-deviceinfo returns empty

```bash
# Cause: Missing permissions or no SIM card

# Solution 1: Check if SIM is inserted
# Physical check or:
termux-telephony-deviceinfo | jq '.sim_state'
# Should show "READY" not "ABSENT"

# Solution 2: Grant phone permissions
# Settings → Apps → Termux → Permissions → Phone → Allow
# Settings → Apps → Termux:API → Permissions → Phone → Allow

# Solution 3: Check if phone type is supported
termux-telephony-deviceinfo | jq '.phone_type'
# GSM or CDMA should work, NONE means no telephony

# Solution 4: Try airplane mode toggle
# Sometimes toggling airplane mode helps refresh telephony state
```

### Problem 3: termux-location times out

```bash
# Cause: GPS not available or location services disabled

# Solution 1: Enable location services
# Settings → Location → On
# Mode: High accuracy recommended

# Solution 2: Use network provider instead of GPS
termux-location -p network
# Network is faster but less accurate

# Solution 3: Increase timeout
# Default is 10 seconds, try with passive provider:
termux-location -p passive

# Solution 4: Check location permission
# Settings → Apps → Termux → Permissions → Location → Allow
# Settings → Apps → Termux:API → Permissions → Location → Allow

# Solution 5: Test with app
# Open Google Maps to verify GPS is working
```

### Problem 4: termux-sensor returns no data

```bash
# Cause: Sensor not available or permission issue

# Solution 1: List available sensors
termux-sensor -l
# Or:
termux-sensor -s list

# Solution 2: Check sensor name spelling
# Names are case-sensitive, use exact names from list

# Solution 3: Wait for sensor initialization
# Some sensors need time to warm up
termux-sensor -s accelerometer -n 3 -d 1000

# Solution 4: Check sensor in other apps
# Use a sensor testing app to verify hardware is working

# Solution 5: Restart Termux:API service
# Force stop Termux:API app and open again
```

### Problem 5: termux-fingerprint fails immediately

```bash
# Cause: No fingerprint enrolled or hardware issue

# Solution 1: Enroll fingerprints in Android settings
# Settings → Security → Fingerprint
# Add at least one fingerprint

# Solution 2: Check Android version
# Fingerprint API requires Android 6.0+
getprop ro.build.version.release

# Solution 3: Check for fingerprint hardware
# Settings → Security → should show Fingerprint option

# Solution 4: Try alternative biometric
# Some devices use face unlock instead
```

### Problem 6: termux-brightness doesn't change

```bash
# Cause: Missing permission or system restriction

# Solution 1: Grant "Modify system settings" permission
# Settings → Apps → Termux → Modify system settings → Allow
# Settings → Apps → Termux:API → Modify system settings → Allow

# Solution 2: Check if adaptive brightness is interfering
# Settings → Display → Adaptive brightness → Turn off temporarily

# Solution 3: Use valid brightness range
# Check current brightness first:
termux-brightness
# Some devices use 0-255, others 0-100

# Solution 4: Check for screen filter apps
# Some screen filter apps override system brightness
```

### Problem 7: JSON parsing errors

```bash
# Cause: API returning null or malformed data

# Solution 1: Check raw output first
termux-battery-status
# If empty or error, fix API issue first

# Solution 2: Handle null values in jq
termux-wifi-connectioninfo | jq -r '.ssid // "Not connected"'

# Solution 3: Validate JSON
termux-battery-status | jq .

# Solution 4: Check for stderr output
termux-battery-status 2>&1

# Solution 5: Use Python for robust parsing
termux-battery-status | python -c "
import sys, json
try:
    data = json.load(sys.stdin)
    print(data.get('percentage', 'N/A'))
except:
    print('Error parsing JSON')
"
```

### Problem 8: Permission denied errors

```bash
# Cause: Missing Android permissions

# Solution: Grant all necessary permissions
# For Termux app:
# Settings → Apps → Termux → Permissions
# - Storage / Files and media: Allow
# - Location: Allow
# - Phone: Allow
# - Camera: Allow (for camera APIs)
# - Microphone: Allow (for audio APIs)

# For Termux:API app:
# Settings → Apps → Termux:API → Permissions
# - Same permissions as Termux

# Additional permissions in Special access:
# - Modify system settings: Allow
# - Appear on top: Allow
# - Battery optimization: Don't optimize
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   📱 DEVICE INFO API               │
│   Complete Phone Extraction        │
│                                    │
│   ✓ Battery & Sensors              │
│   ✓ GPS & WiFi                     │
│   ✓ IMEI & Telephony               │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Feature Showcase**
```
┌────────────────────────────────────┐
│  🔋 📶 📍 📱 🧭                    │
│  ─────────────────────────────────│
│  TERMUX DEVICE APIs               │
│                                    │
│  Battery | WiFi | GPS             │
│  Sensors | Fingerprint            │
│                                    │
│  Complete Guide | Ch 18            │
└────────────────────────────────────┘
```

**Option C: Code-Focused**
```
┌────────────────────────────────────┐
│  $ termux-battery-status           │
│  { "percentage": 85 }              │
│                                    │
│  $ termux-location -p gps          │
│  { "lat": 28.6, "lon": 77.2 }      │
│                                    │
│  DEVICE INFO EXTRACTIVE            │
│  [T3rmuxk1ng Course]               │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📱 Termux Full Course - Chapter 18: Device Information API | Phone Info Extract Karne Ka Tarika

🔥 In this video you'll learn:
• Battery status monitoring and alerts
• Brightness and volume control APIs
• Telephony info - IMEI, SIM, network details
• WiFi connection information
• Sensors - accelerometer, gyroscope, magnetometer
• Fingerprint authentication
• GPS location extraction
• JSON parsing with jq and Python
• 20+ practical automation scripts

⏱️ Timestamps:
0:00 - Introduction
0:45 - Prerequisites & Setup
2:30 - Battery Status API
5:00 - Brightness Control API
7:30 - Volume Control API
10:00 - Telephony Device Info
12:00 - WiFi Connection Info
14:00 - Sensors API
16:30 - Fingerprint API
18:00 - Location (GPS) API
20:00 - Creating Device Info Script
22:00 - JSON Parsing Techniques
23:30 - Python Integration
25:00 - Summary

📝 Commands from this video:
termux-battery-status
termux-brightness 100
termux-volume stream_music 10
termux-telephony-deviceinfo
termux-wifi-connectioninfo
termux-sensor -s accelerometer -n 1
termux-fingerprint
termux-location -p gps

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #TermuxAPI #DeviceInfo #TermuxCourse #T3rmuxk1ng #AndroidHacking #PhoneInfo #GPS #Sensors #EthicalHacking

---
⚠️ Disclaimer: This video is for educational purposes. Only access information from your own devices or with proper authorization.
```

### Tags List

```
termux, termux api, termux device info, termux battery status, 
termux gps, termux wifi info, termux sensors, termux fingerprint,
termux telephony, termux imei, termux location, termux brightness,
termux volume, termux course, termux tutorial, termux hindi,
phone info extractor, device information android, termux scripts,
android sensors, accelerometer termux, gps location termux,
t3rmuxk1ng, termux full course, ethical hacking, mobile hacking
```

### Hashtags

```
#Termux #TermuxAPI #DeviceInfo #TermuxCourse #T3rmuxk1ng 
#AndroidHacking #PhoneInfo #GPSTracking #Sensors 
#EthicalHacking #MobileSecurity #TermuxHindi #TermuxTutorial
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| Termux API Wiki | https://wiki.termux.com/wiki/Termux:API |
| Termux API GitHub | https://github.com/termux/termux-api |
| Android Sensor Types | https://developer.android.com/guide/topics/sensors/sensors_overview |
| Android TelephonyManager | https://developer.android.com/reference/android/telephony/TelephonyManager |

### Related Commands

```bash
# Additional useful commands
termux-wifi-enable          # Enable WiFi
termux-wifi-disable         # Disable WiFi
termux-wifi-scaninfo        # Scan WiFi networks

# Information commands
getprop                    # Android system properties
dumpsys battery            # Detailed battery info
dumpsys telephony.registry # Telephony state
dumpsys wifi               # WiFi state
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 19, verify:

- [ ] Termux:API app installed from F-Droid
- [ ] `pkg install termux-api` completed
- [ ] `termux-battery-status` returns valid JSON
- [ ] `termux-wifi-connectioninfo` works when connected
- [ ] `termux-sensor -l` shows available sensors
- [ ] `termux-location -p network` returns coordinates
- [ ] `jq` installed for JSON parsing
- [ ] Understood JSON output structure
- [ ] Created at least one automation script
- [ ] Tested Python integration

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 19: Camera & Media APIs**

- termux-camera-photo - Capture photos
- termux-camera-info - Camera information
- termux-media-player - Media playback control
- termux-media-scan - Media library scanning
- termux-audio-info - Audio information
- Audio recording and playback
- Video processing with ffmpeg
- Creating surveillance scripts

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
