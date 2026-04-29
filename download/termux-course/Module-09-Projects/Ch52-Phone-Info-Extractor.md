# 📱 Chapter 52: Project 2 - Phone Info Extractor

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ██████╗  ██████╗ ███████╗ █████╗  ██████╗ ██╗    ██╗                      ║
║   ██╔══██╗██╔═══██╗██╔════╝██╔══██╗██╔════╝ ██║    ██║                      ║
║   ██████╔╝██║   ██║███████╗███████║██║  ███╗██║ █╗ ██║                      ║
║   ██╔══██╗██║   ██║╚════██║██╔══██║██║   ██║██║███╗██║                      ║
║   ██║  ██║╚██████╔╝███████║██║  ██║╚██████╔╝╚███╔███╔╝                      ║
║   ╚═╝  ╚═╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝ ╚═════╝  ╚══╝╚══╝                       ║
║                                                                              ║
║              📱 PHONE INFO EXTRACTOR 📱                                      ║
║                    by T3rmuxk1ng                                             ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 9 - Projects  
> **Chapter:** 52 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐ Intermediate

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Project architecture & implementation |
| Source Code | Complete Python implementation |
| Output Formats | JSON, Text, HTML exports |
| Practice Exercises | Hands-on tasks |
| Troubleshooting | Common issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 52
Title: Phone Info Extractor | Complete Device Information Tool | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome to Chapter 52 of Termux Full Course!

Main aapka host hoon aur aaj ek bahut useful project banayenge - Phone 
Info Extractor!

Ye tool aapke Android phone ki complete information extract karega:
- Device model aur manufacturer
- Android version aur build details
- Battery status aur health
- Storage information
- Network details
- WiFi information
- IP addresses
- Installed apps list
- CPU aur memory info
- Aur bahut kuch!

Sab kuch ek single Python script mein - automated, formatted, aur 
exportable!

Ye project practical hai - security auditors, developers, ya koi bhi 
jo apne device ki details chahiye, ye tool use kar sakte hain.

To chaliye shuru karte hain!

Play button dabaiye, video like karein, subscribe karein.

---

[SECTION 1: PROJECT OVERVIEW - 1:00 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle samjhte hain ki ye project kya hai aur kyun useful hai.

Phone Info Extractor ek Python-based tool hai jo:
1. Termux APIs ka use karta hai
2. System files se information read karta hai
3. Sab kuch formatted output mein deta hai
4. Multiple formats mein export kar sakta hai

Real-world use cases:

✓ Security Auditing - Device fingerprinting
✓ App Development - Device compatibility check
✓ Troubleshooting - System diagnostics
✓ Inventory Management - Device documentation
✓ Forensics - Device information collection

Termux APIs jo hum use karenge:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX APIs FOR PHONE INFO                            │
├──────────────────────┬──────────────────────────────────────────────────┤
│ API                  │ Information Provided                             │
├──────────────────────┼──────────────────────────────────────────────────┤
│ termux-battery-status│ Battery level, status, health, temperature      │
│ termux-telephony-deviceinfo │ Device ID, IMEI, phone number        │
│ termux-wifi-connectioninfo │ WiFi SSID, BSSID, IP, speed           │
│ termux-notification  │ Status notifications                            │
└──────────────────────┴──────────────────────────────────────────────────┘

System files se information:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SYSTEM FILES FOR DEVICE INFO                          │
├──────────────────────┬──────────────────────────────────────────────────┤
│ File                 │ Information                                      │
├──────────────────────┼──────────────────────────────────────────────────┤
│ /proc/cpuinfo        │ CPU details, cores, model                        │
│ /proc/meminfo        │ RAM information                                  │
│ /proc/version        │ Kernel version                                   │
│ getprop commands     │ Android properties                               │
│ /system/build.prop   │ Build information                                │
└──────────────────────┴──────────────────────────────────────────────────┘

Is project se aap seekhoge:
- Python subprocess module ka use
- JSON parsing aur manipulation
- File handling in Termux
- HTML report generation
- Command-line argument parsing
- Error handling best practices

---

[SECTION 2: PREREQUISITES - 4:00 to 6:00]
─────────────────────────────────────────────────────────────────────────────

Project start karne se pehle ye cheezein chahiye:

[REQUIREMENT 1: Termux:API App]

Termux:API app install hona zaruri hai. F-Droid se install karein:
- Termux:API - Main API app

[REQUIREMENT 2: Python Packages]

Python packages install karein:

    pkg install python -y
    pip install colorama

colorama - Colored terminal output ke liye

[REQUIREMENT 3: Termux API Package]

    pkg install termux-api -y

Ye package command-line tools deta hai jo Termux:API app se 
communicate karte hain.

[REQUIREMENT 4: Storage Permission]

    termux-setup-storage

Storage access ke liye - reports save karne ke liye.

[VERIFICATION]

Sab kuch sahi se installed hai ya nahi, check karein:

    termux-battery-status

Agar JSON output aaya - sab theek hai!
Agar error aaya - Termux:API app install nahi hai.

    getprop ro.product.model

Device model dikhna chahiye.

    cat /proc/cpuinfo

CPU information dikhni chahiye.

---

[SECTION 3: DEVICE INFORMATION METHODS - 6:00 to 10:00]
─────────────────────────────────────────────────────────────────────────────

Ab samjhte hain ki different types ki information kaise 
extract karte hain.

[METHOD 1: getprop Commands]

Android properties - device ki basic info:

    # Device Model
    getprop ro.product.model
    
    # Manufacturer
    getprop ro.product.manufacturer
    
    # Android Version
    getprop ro.build.version.release
    
    # SDK Version
    getprop ro.build.version.sdk
    
    # Build ID
    getprop ro.build.id
    
    # Brand
    getprop ro.product.brand
    
    # Device Name
    getprop ro.product.device
    
    # Product Name
    getprop ro.product.name
    
    # Board
    getprop ro.product.board
    
    # Hardware
    getprop ro.hardware
    
    # Serial Number
    getprop ro.serialno
    
    # Bootloader
    getprop ro.bootloader
    
    # Fingerprint
    getprop ro.build.fingerprint

Ye sab commands se hum device ki unique identity mil jaati hai.

[METHOD 2: Termux API Commands]

Battery status:

    termux-battery-status

Output (JSON):
{
  "health": "GOOD",
  "percentage": 85,
  "plugged": "UNPLUGGED",
  "status": "DISCHARGING",
  "temperature": 32.0,
  "current": 450
}

WiFi connection info:

    termux-wifi-connectioninfo

Output (JSON):
{
  "bssid": "aa:bb:cc:dd:ee:ff",
  "frequency_mhz": 2437,
  "ip": "192.168.1.100",
  "link_speed_mbps": 65,
  "mac_address": "11:22:33:44:55:66",
  "network_id": 1,
  "rssi": -45,
  "ssid": "MyWiFi",
  "ssid_hidden": false
}

Telephony device info:

    termux-telephony-deviceinfo

Output (JSON):
{
  "device_id": null,
  "imei": "123456789012345",
  "phone_count": 2,
  "phone_type": "GSM",
  "network_country": "IN",
  "network_operator": "404xx",
  "network_operator_name": "Jio",
  "network_type": "LTE",
  "sim_country": "IN",
  "sim_operator": "404xx",
  "sim_operator_name": "Jio",
  "sim_serial_number": "8991...",
  "sim_state": "READY"
}

[METHOD 3: System Files]

CPU Information:

    cat /proc/cpuinfo

Contents include:
- Processor type
- CPU cores
- CPU features
- Clock speed
- Hardware name

Memory Information:

    cat /proc/meminfo

Contents include:
- MemTotal (Total RAM)
- MemFree (Free RAM)
- MemAvailable
- Buffers
- Cached
- SwapTotal
- SwapFree

Kernel Version:

    cat /proc/version

Storage Information:

    df -h

Network interfaces:

    ifconfig
    ip addr

---

[SECTION 4: IMPLEMENTATION - PART 1 - 10:00 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Ab Python code shuru karte hain. Main step by step explain karunga.

[STEP 1: Import Required Modules]

    #!/usr/bin/env python3
    """
    Phone Info Extractor - Complete Device Information Tool
    Author: T3rmuxk1ng
    """
    
    import subprocess
    import json
    import os
    import sys
    import platform
    from datetime import datetime
    from colorama import Fore, Style, init

Ye modules hum use karenge:
- subprocess: Commands run karne ke liye
- json: JSON parsing ke liye
- os: File operations ke liye
- sys: System functions ke liye
- platform: Platform info ke liye
- datetime: Timestamp ke liye
- colorama: Colored output ke liye

[STEP 2: Helper Functions]

    def run_command(cmd):
        """Run shell command and return output"""
        try:
            result = subprocess.run(
                cmd,
                shell=True,
                capture_output=True,
                text=True,
                timeout=10
            )
            return result.stdout.strip()
        except Exception as e:
            return f"Error: {str(e)}"
    
    def run_json_command(cmd):
        """Run command that returns JSON output"""
        try:
            result = subprocess.run(
                cmd,
                shell=True,
                capture_output=True,
                text=True,
                timeout=10
            )
            return json.loads(result.stdout)
        except:
            return None

Ye helper functions repeated code ko simplify karte hain.

[STEP 3: Get Device Properties]

    def get_device_info():
        """Get basic device information using getprop"""
        properties = {
            "model": run_command("getprop ro.product.model"),
            "manufacturer": run_command("getprop ro.product.manufacturer"),
            "brand": run_command("getprop ro.product.brand"),
            "device": run_command("getprop ro.product.device"),
            "product": run_command("getprop ro.product.name"),
            "board": run_command("getprop ro.product.board"),
            "hardware": run_command("getprop ro.hardware"),
            "serial": run_command("getprop ro.serialno"),
            "bootloader": run_command("getprop ro.bootloader"),
            "fingerprint": run_command("getprop ro.build.fingerprint")
        }
        return properties

Ye function device ki hardware properties collect karta hai.

[STEP 4: Get Android Version Info]

    def get_android_info():
        """Get Android version and build information"""
        info = {
            "android_version": run_command("getprop ro.build.version.release"),
            "sdk_version": run_command("getprop ro.build.version.sdk"),
            "build_id": run_command("getprop ro.build.id"),
            "build_display": run_command("getprop ro.build.display.id"),
            "build_type": run_command("getprop ro.build.type"),
            "build_tags": run_command("getprop ro.build.tags"),
            "build_date": run_command("getprop ro.build.date"),
            "security_patch": run_command("getprop ro.build.version.security_patch"),
            "incremental": run_command("getprop ro.build.version.incremental"),
            "codename": run_command("getprop ro.build.version.codename")
        }
        return info

Android version aur build details.

---

[SECTION 5: IMPLEMENTATION - PART 2 - 14:00 to 18:00]
─────────────────────────────────────────────────────────────────────────────

[STEP 5: Get Battery Information]

    def get_battery_info():
        """Get battery status using Termux API"""
        battery = run_json_command("termux-battery-status")
        if battery:
            return {
                "percentage": battery.get("percentage", "N/A"),
                "status": battery.get("status", "N/A"),
                "health": battery.get("health", "N/A"),
                "plugged": battery.get("plugged", "N/A"),
                "temperature": f"{battery.get('temperature', 0)}°C",
                "current": f"{battery.get('current', 0)} mA"
            }
        return {"error": "Unable to get battery info"}

Battery details Termux API se.

[STEP 6: Get CPU Information]

    def get_cpu_info():
        """Get CPU information from /proc/cpuinfo"""
        cpu_info = {}
        try:
            with open("/proc/cpuinfo", "r") as f:
                content = f.read()
            
            # Parse CPU info
            lines = content.split("\n")
            processors = []
            current_proc = {}
            
            for line in lines:
                if line.strip():
                    try:
                        key, value = line.split(":", 1)
                        key = key.strip()
                        value = value.strip()
                        if key == "processor":
                            if current_proc:
                                processors.append(current_proc)
                            current_proc = {"id": value}
                        else:
                            current_proc[key] = value
                    except:
                        pass
            if current_proc:
                processors.append(current_proc)
            
            cpu_info["cores"] = len(processors)
            if processors:
                cpu_info["hardware"] = processors[0].get("Hardware", "Unknown")
                cpu_info["model"] = processors[0].get("model name", "Unknown")
                cpu_info["features"] = processors[0].get("Features", "N/A")
        except Exception as e:
            cpu_info["error"] = str(e)
        
        return cpu_info

CPU cores, hardware, features.

[STEP 7: Get Memory Information]

    def get_memory_info():
        """Get memory information from /proc/meminfo"""
        memory = {}
        try:
            with open("/proc/meminfo", "r") as f:
                content = f.read()
            
            # Parse memory values
            def get_mem_value(key):
                import re
                match = re.search(rf"{key}:\s+(\d+)", content)
                if match:
                    return int(match.group(1))
                return 0
            
            mem_total = get_mem_value("MemTotal")
            mem_free = get_mem_value("MemFree")
            mem_available = get_mem_value("MemAvailable")
            swap_total = get_mem_value("SwapTotal")
            swap_free = get_mem_value("SwapFree")
            
            memory = {
                "total_ram": f"{mem_total // 1024} MB",
                "free_ram": f"{mem_free // 1024} MB",
                "available_ram": f"{mem_available // 1024} MB",
                "used_ram": f"{(mem_total - mem_available) // 1024} MB",
                "ram_usage_percent": f"{((mem_total - mem_available) / mem_total) * 100:.1f}%",
                "total_swap": f"{swap_total // 1024} MB",
                "free_swap": f"{swap_free // 1024} MB"
            }
        except Exception as e:
            memory["error"] = str(e)
        
        return memory

RAM aur Swap details.

[STEP 8: Get Storage Information]

    def get_storage_info():
        """Get storage information using df command"""
        storage = {"partitions": []}
        try:
            output = run_command("df -h")
            lines = output.split("\n")[1:]  # Skip header
            
            for line in lines:
                if line.strip():
                    parts = line.split()
                    if len(parts) >= 6:
                        partition = {
                            "filesystem": parts[0],
                            "size": parts[1],
                            "used": parts[2],
                            "available": parts[3],
                            "use_percent": parts[4],
                            "mounted_on": parts[5]
                        }
                        storage["partitions"].append(partition)
        except Exception as e:
            storage["error"] = str(e)
        
        return storage

Disk partitions aur usage.

[STEP 9: Get Network Information]

    def get_network_info():
        """Get network and WiFi information"""
        network = {}
        
        # WiFi info from Termux API
        wifi = run_json_command("termux-wifi-connectioninfo")
        if wifi:
            network["wifi"] = {
                "ssid": wifi.get("ssid", "N/A"),
                "bssid": wifi.get("bssid", "N/A"),
                "ip": wifi.get("ip", "N/A"),
                "frequency": f"{wifi.get('frequency_mhz', 0)} MHz",
                "link_speed": f"{wifi.get('link_speed_mbps', 0)} Mbps",
                "rssi": f"{wifi.get('rssi', 0)} dBm",
                "mac_address": wifi.get("mac_address", "N/A")
            }
        
        # IP addresses
        network["ip_addresses"] = {
            "local": run_command("ip route | awk '/src/ {print $7}' | head -1"),
            "public": run_command("curl -s ifconfig.me 2>/dev/null || echo 'N/A'")
        }
        
        # Network interfaces
        interfaces = []
        output = run_command("ip link show")
        for line in output.split("\n"):
            if ": " in line:
                iface = line.split(": ")[1].split("@")[0]
                if iface != "lo":
                    interfaces.append(iface)
        network["interfaces"] = interfaces
        
        return network

WiFi, IP addresses, interfaces.

---

[SECTION 6: IMPLEMENTATION - PART 3 - 18:00 to 21:00]
─────────────────────────────────────────────────────────────────────────────

[STEP 10: Get Telephony Information]

    def get_telephony_info():
        """Get telephony information using Termux API"""
        telephony = run_json_command("termux-telephony-deviceinfo")
        if telephony:
            return {
                "phone_type": telephony.get("phone_type", "N/A"),
                "network_operator": telephony.get("network_operator_name", "N/A"),
                "network_type": telephony.get("network_type", "N/A"),
                "network_country": telephony.get("network_country", "N/A"),
                "sim_operator": telephony.get("sim_operator_name", "N/A"),
                "sim_country": telephony.get("sim_country", "N/A"),
                "sim_state": telephony.get("sim_state", "N/A"),
                "phone_count": telephony.get("phone_count", "N/A")
            }
        return {"error": "Unable to get telephony info"}

SIM aur network operator details.

[STEP 11: Get Kernel Information]

    def get_kernel_info():
        """Get kernel information"""
        kernel = {}
        try:
            with open("/proc/version", "r") as f:
                version = f.read().strip()
            
            kernel["version"] = version
            kernel["release"] = platform.release()
            kernel["system"] = platform.system()
            kernel["node"] = platform.node()
            kernel["machine"] = platform.machine()
        except Exception as e:
            kernel["error"] = str(e)
        
        return kernel

Kernel version aur system info.

[STEP 12: Get Installed Apps]

    def get_installed_apps():
        """Get list of installed packages"""
        apps = {"total": 0, "packages": []}
        try:
            output = run_command("pm list packages -3")
            packages = []
            for line in output.split("\n"):
                if line.startswith("package:"):
                    pkg = line.replace("package:", "").strip()
                    packages.append(pkg)
            
            apps["total"] = len(packages)
            apps["packages"] = packages[:50]  # Limit to 50 for readability
            apps["note"] = f"Showing first 50 of {len(packages)} packages"
        except Exception as e:
            apps["error"] = str(e)
        
        return apps

Installed third-party apps.

[STEP 13: Get Termux Info]

    def get_termux_info():
        """Get Termux-specific information"""
        termux = {}
        
        termux["version"] = os.environ.get("TERMUX_VERSION", "N/A")
        termux["prefix"] = os.environ.get("PREFIX", "N/A")
        termux["home"] = os.environ.get("HOME", "N/A")
        termux["path"] = os.environ.get("PATH", "N/A")
        termux["shell"] = os.environ.get("SHELL", "N/A")
        termux["user"] = os.environ.get("USER", "N/A")
        
        # Package count
        pkg_list = run_command("pkg list-installed | wc -l")
        termux["installed_packages"] = pkg_list if pkg_list else "0"
        
        return termux

Termux environment details.

---

[SECTION 7: OUTPUT FORMATTING - 21:00 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Ab output formatting ka code:

[TEXT OUTPUT]

    def format_text_output(data):
        """Format data as readable text"""
        output = []
        output.append("=" * 60)
        output.append("       PHONE INFO EXTRACTOR - DEVICE REPORT")
        output.append("=" * 60)
        output.append(f"Generated: {data['timestamp']}")
        output.append("")
        
        # Device Info
        output.append("[DEVICE INFORMATION]")
        output.append("-" * 40)
        for key, value in data["device"].items():
            output.append(f"  {key.replace('_', ' ').title():<20}: {value}")
        output.append("")
        
        # Android Info
        output.append("[ANDROID VERSION]")
        output.append("-" * 40)
        for key, value in data["android"].items():
            output.append(f"  {key.replace('_', ' ').title():<20}: {value}")
        output.append("")
        
        # Battery
        output.append("[BATTERY STATUS]")
        output.append("-" * 40)
        for key, value in data["battery"].items():
            output.append(f"  {key.replace('_', ' ').title():<20}: {value}")
        output.append("")
        
        # CPU
        output.append("[CPU INFORMATION]")
        output.append("-" * 40)
        for key, value in data["cpu"].items():
            output.append(f"  {key.replace('_', ' ').title():<20}: {value}")
        output.append("")
        
        # Memory
        output.append("[MEMORY INFORMATION]")
        output.append("-" * 40)
        for key, value in data["memory"].items():
            output.append(f"  {key.replace('_', ' ').title():<20}: {value}")
        output.append("")
        
        # Storage
        output.append("[STORAGE INFORMATION]")
        output.append("-" * 40)
        for partition in data["storage"].get("partitions", [])[:5]:
            output.append(f"  {partition['mounted_on']}: {partition['size']} ({partition['use_percent']} used)")
        output.append("")
        
        # Network
        output.append("[NETWORK INFORMATION]")
        output.append("-" * 40)
        if "wifi" in data["network"]:
            output.append("  WiFi:")
            for key, value in data["network"]["wifi"].items():
                output.append(f"    {key.replace('_', ' ').title():<18}: {value}")
        output.append(f"  Local IP: {data['network']['ip_addresses'].get('local', 'N/A')}")
        output.append(f"  Public IP: {data['network']['ip_addresses'].get('public', 'N/A')}")
        output.append("")
        
        # Termux
        output.append("[TERMUX INFORMATION]")
        output.append("-" * 40)
        for key, value in data["termux"].items():
            output.append(f"  {key.replace('_', ' ').title():<20}: {value}")
        output.append("")
        
        output.append("=" * 60)
        output.append("           Report Generated by Phone Info Extractor")
        output.append("=" * 60)
        
        return "\n".join(output)

[JSON OUTPUT]

    def format_json_output(data):
        """Format data as JSON"""
        return json.dumps(data, indent=2, default=str)

[HTML OUTPUT]

    def format_html_output(data):
        """Format data as HTML report"""
        html = []
        html.append("<!DOCTYPE html>")
        html.append("<html><head>")
        html.append("<title>Phone Info Report</title>")
        html.append("<style>")
        html.append("body { font-family: Arial, sans-serif; margin: 20px; background: #1a1a2e; color: #eee; }")
        html.append(".container { max-width: 800px; margin: 0 auto; }")
        html.append(".section { background: #16213e; margin: 10px 0; padding: 15px; border-radius: 10px; }")
        html.append(".section h2 { color: #00ff88; border-bottom: 2px solid #00ff88; padding-bottom: 10px; }")
        html.append(".info-row { display: flex; padding: 5px 0; border-bottom: 1px solid #333; }")
        html.append(".info-label { flex: 1; color: #888; }")
        html.append(".info-value { flex: 2; color: #fff; }")
        html.append(".header { text-align: center; padding: 20px; }")
        html.append(".header h1 { color: #00ff88; }")
        html.append(".timestamp { color: #888; font-size: 0.9em; }")
        html.append("</style>")
        html.append("</head><body>")
        html.append("<div class='container'>")
        html.append("<div class='header'>")
        html.append("<h1>📱 Phone Info Report</h1>")
        html.append(f"<p class='timestamp'>Generated: {data['timestamp']}</p>")
        html.append("</div>")
        
        # Device Section
        html.append("<div class='section'>")
        html.append("<h2>📟 Device Information</h2>")
        for key, value in data["device"].items():
            html.append(f"<div class='info-row'>")
            html.append(f"<span class='info-label'>{key.replace('_', ' ').title()}</span>")
            html.append(f"<span class='info-value'>{value}</span>")
            html.append("</div>")
        html.append("</div>")
        
        # Android Section
        html.append("<div class='section'>")
        html.append("<h2>🤖 Android Version</h2>")
        for key, value in data["android"].items():
            html.append(f"<div class='info-row'>")
            html.append(f"<span class='info-label'>{key.replace('_', ' ').title()}</span>")
            html.append(f"<span class='info-value'>{value}</span>")
            html.append("</div>")
        html.append("</div>")
        
        # Battery Section
        html.append("<div class='section'>")
        html.append("<h2>🔋 Battery Status</h2>")
        for key, value in data["battery"].items():
            html.append(f"<div class='info-row'>")
            html.append(f"<span class='info-label'>{key.replace('_', ' ').title()}</span>")
            html.append(f"<span class='info-value'>{value}</span>")
            html.append("</div>")
        html.append("</div>")
        
        # CPU Section
        html.append("<div class='section'>")
        html.append("<h2>💻 CPU Information</h2>")
        for key, value in data["cpu"].items():
            html.append(f"<div class='info-row'>")
            html.append(f"<span class='info-label'>{key.replace('_', ' ').title()}</span>")
            html.append(f"<span class='info-value'>{value}</span>")
            html.append("</div>")
        html.append("</div>")
        
        # Memory Section
        html.append("<div class='section'>")
        html.append("<h2>🧠 Memory Information</h2>")
        for key, value in data["memory"].items():
            html.append(f"<div class='info-row'>")
            html.append(f"<span class='info-label'>{key.replace('_', ' ').title()}</span>")
            html.append(f"<span class='info-value'>{value}</span>")
            html.append("</div>")
        html.append("</div>")
        
        # Network Section
        html.append("<div class='section'>")
        html.append("<h2>🌐 Network Information</h2>")
        if "wifi" in data["network"]:
            html.append("<h3>WiFi</h3>")
            for key, value in data["network"]["wifi"].items():
                html.append(f"<div class='info-row'>")
                html.append(f"<span class='info-label'>{key.replace('_', ' ').title()}</span>")
                html.append(f"<span class='info-value'>{value}</span>")
                html.append("</div>")
        html.append("<h3>IP Addresses</h3>")
        html.append(f"<div class='info-row'>")
        html.append(f"<span class='info-label'>Local IP</span>")
        html.append(f"<span class='info-value'>{data['network']['ip_addresses'].get('local', 'N/A')}</span>")
        html.append("</div>")
        html.append(f"<div class='info-row'>")
        html.append(f"<span class='info-label'>Public IP</span>")
        html.append(f"<span class='info-value'>{data['network']['ip_addresses'].get('public', 'N/A')}</span>")
        html.append("</div>")
        html.append("</div>")
        
        # Termux Section
        html.append("<div class='section'>")
        html.append("<h2>📲 Termux Information</h2>")
        for key, value in data["termux"].items():
            html.append(f"<div class='info-row'>")
            html.append(f"<span class='info-label'>{key.replace('_', ' ').title()}</span>")
            html.append(f"<span class='info-value'>{value}</span>")
            html.append("</div>")
        html.append("</div>")
        
        html.append("</div>")
        html.append("</body></html>")
        
        return "\n".join(html)

---

[SECTION 8: MAIN FUNCTION & CLI - 23:00 to 24:30]
─────────────────────────────────────────────────────────────────────────────

[MAIN FUNCTION]

    def collect_all_info():
        """Collect all device information"""
        print(f"{Fore.CYAN}Collecting device information...{Style.RESET_ALL}")
        
        data = {
            "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
            "device": get_device_info(),
            "android": get_android_info(),
            "battery": get_battery_info(),
            "cpu": get_cpu_info(),
            "memory": get_memory_info(),
            "storage": get_storage_info(),
            "network": get_network_info(),
            "telephony": get_telephony_info(),
            "kernel": get_kernel_info(),
            "apps": get_installed_apps(),
            "termux": get_termux_info()
        }
        
        return data

[MAIN ENTRY POINT]

    def main():
        """Main function"""
        init()  # Initialize colorama
        
        print(f"{Fore.GREEN}")
        print("=" * 60)
        print("       PHONE INFO EXTRACTOR v1.0")
        print("       by T3rmuxk1ng")
        print("=" * 60)
        print(f"{Style.RESET_ALL}")
        
        # Collect information
        data = collect_all_info()
        
        # Display text output
        print(f"\n{format_text_output(data)}")
        
        # Save to files
        save_dir = "~/storage/downloads/phone_info"
        os.makedirs(os.path.expanduser(save_dir), exist_ok=True)
        
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        
        # Save JSON
        json_file = f"{save_dir}/phone_info_{timestamp}.json"
        with open(os.path.expanduser(json_file), "w") as f:
            f.write(format_json_output(data))
        print(f"\n{Fore.GREEN}JSON report saved: {json_file}{Style.RESET_ALL}")
        
        # Save HTML
        html_file = f"{save_dir}/phone_info_{timestamp}.html"
        with open(os.path.expanduser(html_file), "w") as f:
            f.write(format_html_output(data))
        print(f"{Fore.GREEN}HTML report saved: {html_file}{Style.RESET_ALL}")
        
        # Save Text
        text_file = f"{save_dir}/phone_info_{timestamp}.txt"
        with open(os.path.expanduser(text_file), "w") as f:
            f.write(format_text_output(data))
        print(f"{Fore.GREEN}Text report saved: {text_file}{Style.RESET_ALL}")
        
        print(f"\n{Fore.CYAN}All reports saved to: {save_dir}{Style.RESET_ALL}")

    if __name__ == "__main__":
        main()

---

[SECTION 9: RUNNING THE TOOL - 24:30 to 25:30]
─────────────────────────────────────────────────────────────────────────────

Tool ko run karna simple hai:

    python phone_info_extractor.py

Output:
- Terminal pe formatted text
- JSON file saved
- HTML file saved  
- Text file saved

Files location:
~/storage/downloads/phone_info/

Aap HTML file ko browser mein open kar sakte ho - beautiful report 
dikhegi!

Command line options bhi add kar sakte ho:

    python phone_info_extractor.py --json    # JSON only
    python phone_info_extractor.py --html    # HTML only
    python phone_info_extractor.py --text    # Text only
    python phone_info_extractor.py --all     # All formats

---

[SECTION 10: SUMMARY & NEXT PREVIEW - 25:30 to 27:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 52 complete! Let's summarize:

✅ Phone Info Extractor project banaya
✅ Termux APIs ka use kiya - battery, wifi, telephony
✅ System files se info extract ki - CPU, memory, storage
✅ getprop commands se device properties
✅ Multiple output formats - JSON, HTML, Text
✅ File export to downloads folder
✅ Beautiful terminal output with colorama

Key concepts seekhe:
- subprocess module for command execution
- JSON parsing with json module
- File handling in Python
- HTML report generation
- Error handling best practices
- Modular code organization

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 52 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install termux-api           │ Install Termux API tools             │
│ pip install colorama             │ Install colorama for colors          │
│ termux-battery-status            │ Get battery info (JSON)              │
│ termux-wifi-connectioninfo       │ Get WiFi connection info             │
│ termux-telephony-deviceinfo      │ Get phone/SIM info                   │
│ getprop ro.product.model         │ Get device model                     │
│ getprop ro.build.version.release │ Get Android version                  │
│ cat /proc/cpuinfo                │ Get CPU information                  │
│ cat /proc/meminfo                │ Get memory information               │
│ df -h                            │ Get storage information              │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 53 mein hum WiFi Analyzer project banayenge:
- WiFi network scanning
- Signal strength analysis
- Network security assessment
- Channel optimization

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 53!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

### Test Your Phone Info Extractor Knowledge!

<details>
<summary>❓ Question 1: Which Termux API command returns battery status in JSON format?</summary>

**Answer:** `termux-battery-status`

**Explanation:** The `termux-battery-status` command returns a JSON object containing battery information including percentage, health, charging status, and temperature. This requires the Termux:API app to be installed alongside Termux.

```bash
termux-battery-status
# Output: {"health": "GOOD", "percentage": 85, "plugged": "UNPLUGGED", ...}
```
</details>

<details>
<summary>❓ Question 2: What Android command retrieves device properties like model and manufacturer?</summary>

**Answer:** `getprop`

**Explanation:** The `getprop` command reads system properties from Android's property service. You can retrieve specific properties like `getprop ro.product.model` for device model, or `getprop ro.build.version.release` for Android version.

```bash
getprop ro.product.model      # Device model
getprop ro.build.version.release  # Android version
getprop ro.serialno           # Serial number
```
</details>

<details>
<summary>❓ Question 3: Which file contains CPU information in Linux/Android?</summary>

**Answer:** `/proc/cpuinfo`

**Explanation:** The `/proc/cpuinfo` file contains detailed CPU information including processor type, core count, features, and clock speed. It's a virtual file provided by the kernel.

```bash
cat /proc/cpuinfo
# Shows: processor, model name, cache size, flags, etc.
```
</details>

<details>
<summary>❓ Question 4: How do you parse JSON output in Python?</summary>

**Answer:** Using the `json` module's `loads()` or `load()` functions

**Explanation:** Python's built-in `json` module provides functions to parse JSON strings. Use `json.loads()` for strings and `json.load()` for file objects.

```python
import json
data = '{"name": "test", "value": 123}'
parsed = json.loads(data)
print(parsed['name'])  # Output: test
```
</details>

<details>
<summary>❓ Question 5: What is the purpose of `subprocess.run()` in this project?</summary>

**Answer:** To execute shell commands and capture their output

**Explanation:** `subprocess.run()` is used to execute Termux API commands and system commands, capturing their output for processing. The `capture_output=True` parameter captures stdout and stderr.

```python
result = subprocess.run(
    ['termux-battery-status'],
    capture_output=True,
    text=True
)
output = result.stdout
```
</details>

<details>
<summary>❓ Question 6: Which Termux API provides WiFi connection details?</summary>

**Answer:** `termux-wifi-connectioninfo`

**Explanation:** This command returns JSON containing WiFi details like SSID, BSSID, IP address, link speed, signal strength (RSSI), and MAC address.

```bash
termux-wifi-connectioninfo
# Output: {"ssid": "MyWiFi", "ip": "192.168.1.100", "rssi": -45, ...}
```
</details>

<details>
<summary>❓ Question 7: What does `/proc/meminfo` contain?</summary>

**Answer:** System memory information including total, free, and available RAM

**Explanation:** The `/proc/meminfo` file provides detailed memory statistics including MemTotal, MemFree, MemAvailable, Buffers, Cached, SwapTotal, and more.

```bash
cat /proc/meminfo
# MemTotal:        4096000 kB
# MemFree:          512000 kB
# MemAvailable:    2048000 kB
```
</details>

<details>
<summary>❓ Question 8: How do you get the public IP address in Termux?</summary>

**Answer:** Using `curl ifconfig.me` or similar services

**Explanation:** External services like ifconfig.me, icanhazip.com, or ipify.org return your public IP address when queried via curl or wget.

```bash
curl -s ifconfig.me
# Output: 123.45.67.89 (your public IP)
```
</details>

<details>
<summary>❓ Question 9: Which Termux API provides SIM and network operator information?</summary>

**Answer:** `termux-telephony-deviceinfo`

**Explanation:** This command returns telephony information including IMEI, network operator, SIM operator, phone type, and SIM state.

```bash
termux-telephony-deviceinfo
# Returns: IMEI, network operator name, SIM details, etc.
```
</details>

<details>
<summary>❓ Question 10: What is the purpose of `os.path.expanduser()` in file paths?</summary>

**Answer:** To expand the `~` symbol to the user's home directory

**Explanation:** `os.path.expanduser()` converts paths containing `~` to the actual home directory path, making paths portable across different users and systems.

```python
import os
path = "~/storage/downloads"
expanded = os.path.expanduser(path)
# Result: /data/data/com.termux/files/home/storage/downloads
```
</details>

<details>
<summary>❓ Question 11: How do you get installed package list in Termux?</summary>

**Answer:** Using `pkg list-installed` or `pm list packages`

**Explanation:** `pkg list-installed` shows Termux packages, while `pm list packages` shows all Android packages. Use `-3` flag with pm for third-party apps only.

```bash
pkg list-installed      # Termux packages
pm list packages -3     # Third-party Android apps
```
</details>

<details>
<summary>❓ Question 12: What does the `df -h` command show?</summary>

**Answer:** Disk space usage in human-readable format

**Explanation:** `df` (disk free) shows filesystem disk space usage. The `-h` flag makes output human-readable (MB, GB instead of blocks).

```bash
df -h
# Filesystem    Size  Used Avail Use% Mounted on
# /dev/block    32G   15G   17G  47% /
```
</details>

<details>
<summary>❓ Question 13: How do you format Python datetime for filenames?</summary>

**Answer:** Using `strftime()` format codes

**Explanation:** `strftime()` formats datetime objects into strings using format codes like `%Y` for year, `%m` for month, `%d` for day, `%H%M%S` for time.

```python
from datetime import datetime
timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
# Result: "20241215_143000"
```
</details>

<details>
<summary>❓ Question 14: What is the purpose of error handling in the phone info extractor?</summary>

**Answer:** To gracefully handle missing APIs, permissions, or unavailable data

**Explanation:** Not all devices have all features (e.g., some lack telephony), and APIs might fail. Try-except blocks ensure the script continues even if some information can't be retrieved.

```python
try:
    battery = run_json_command("termux-battery-status")
except Exception as e:
    battery = {"error": str(e)}
```
</details>

<details>
<summary>❓ Question 15: Which HTML tags are used to create styled reports?</summary>

**Answer:** `<div>`, `<span>`, `<style>`, and CSS classes

**Explanation:** HTML reports use div containers for sections, spans for individual items, and embedded CSS for styling. The style tag contains all formatting rules.

```html
<div class='section'>
  <h2>Device Information</h2>
  <span class='info-label'>Model:</span>
  <span class='info-value'>Pixel 7</span>
</div>
```
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Device Information & System Programming Interview Questions

<details>
<summary>🎤 Q1: How would you design a device inventory system for enterprise management?</summary>

**Answer:**
An enterprise device inventory system would include:
1. **Agent-based collection**: Lightweight agents running on each device
2. **Centralized database**: Store device info with unique identifiers
3. **Scheduled reporting**: Daily/weekly automatic updates
4. **Change detection**: Alert on hardware/software changes
5. **API endpoints**: For integration with ITSM tools
6. **Compliance checking**: Verify against security policies

**Follow-up:** How would you handle devices that are offline or behind firewalls?
</details>

<details>
<summary>🎤 Q2: Explain how you would secure the collection and transmission of device information.</summary>

**Answer:**
Security measures would include:
1. **Encryption in transit**: TLS/SSL for all communications
2. **Authentication**: API keys or certificates for device identity
3. **Data minimization**: Only collect necessary information
4. **Anonymization**: Hash sensitive identifiers when possible
5. **Access control**: Role-based access to inventory data
6. **Audit logging**: Track who accessed what data

**Follow-up:** How would you handle GDPR/privacy concerns with device tracking?
</details>

<details>
<summary>🎤 Q3: How would you implement cross-platform device information collection?</summary>

**Answer:**
Cross-platform implementation requires:
1. **Abstraction layer**: Common interface for all platforms
2. **Platform-specific modules**: OS-specific implementations
3. **Feature detection**: Check what's available on each platform
4. **Graceful degradation**: Handle missing features gracefully
5. **Standardized output**: Common JSON schema regardless of platform

```python
class DeviceInfoCollector:
    def __init__(self):
        self.platform = platform.system()
        
    def get_info(self):
        if self.platform == "Linux":
            return LinuxInfoCollector().collect()
        elif self.platform == "Android":
            return AndroidInfoCollector().collect()
```

**Follow-up:** What are the key differences between Android and desktop Linux for device info?
</details>

<details>
<summary>🎤 Q4: How would you optimize device info collection for performance?</summary>

**Answer:**
Performance optimization strategies:
1. **Caching**: Cache slow-changing information
2. **Parallel collection**: Use threading for independent calls
3. **Lazy loading**: Only collect info when requested
4. **Selective collection**: Option to skip expensive operations
5. **Timeout handling**: Don't hang on unresponsive APIs

```python
from concurrent.futures import ThreadPoolExecutor

def collect_all_info():
    with ThreadPoolExecutor(max_workers=5) as executor:
        futures = {
            executor.submit(get_battery_info): 'battery',
            executor.submit(get_cpu_info): 'cpu',
            executor.submit(get_memory_info): 'memory',
        }
        results = {}
        for future, key in futures.items():
            try:
                results[key] = future.result(timeout=5)
            except TimeoutError:
                results[key] = {'error': 'timeout'}
        return results
```

**Follow-up:** How would you benchmark and identify bottlenecks in the collection process?
</details>

<details>
<summary>🎤 Q5: Explain how you would implement a device fingerprinting system.</summary>

**Answer:**
Device fingerprinting combines multiple identifiers:
1. **Hardware identifiers**: IMEI, serial number, MAC addresses
2. **Software identifiers**: Android ID, app signatures
3. **Configuration fingerprints**: Installed apps, settings hash
4. **Behavioral patterns**: Usage patterns, timing analysis
5. **Consistent hashing**: Generate stable fingerprint across reboots

```python
def generate_fingerprint():
    components = [
        getprop('ro.serialno'),
        getprop('ro.build.fingerprint'),
        get_mac_address(),
        get_android_id(),
        hash_installed_apps()
    ]
    combined = '|'.join(components)
    return hashlib.sha256(combined.encode()).hexdigest()
```

**Follow-up:** What are the privacy implications and how would you address them?
</details>

<details>
<summary>🎤 Q6: How would you implement change detection for device monitoring?</summary>

**Answer:**
Change detection implementation:
1. **Baseline storage**: Store initial state snapshot
2. **Periodic comparison**: Compare current state with baseline
3. **Delta calculation**: Identify specific changes
4. **Change logging**: Maintain audit trail of changes
5. **Alerting**: Notify on significant changes

```python
class DeviceMonitor:
    def __init__(self, baseline_file):
        self.baseline = self.load_baseline(baseline_file)
        
    def check_changes(self):
        current = collect_all_info()
        changes = {}
        for key in current:
            if current[key] != self.baseline.get(key):
                changes[key] = {
                    'old': self.baseline.get(key),
                    'new': current[key]
                }
        return changes
```

**Follow-up:** How would you handle false positives from normal system updates?
</details>

<details>
<summary>🎤 Q7: How would you design a reporting system for device metrics?</summary>

**Answer:**
A reporting system would include:
1. **Template engine**: Customizable report formats
2. **Multiple output formats**: PDF, HTML, JSON, CSV
3. **Scheduling**: Automated report generation
4. **Distribution**: Email, webhook, dashboard delivery
5. **Historical comparisons**: Trend analysis
6. **Conditional formatting**: Highlight issues automatically

**Follow-up:** How would you implement real-time dashboards vs. scheduled reports?
</details>

<details>
<summary>🎤 Q8: Explain how you would handle API rate limiting and retries.</summary>

**Answer:**
Rate limiting and retry strategies:
1. **Exponential backoff**: Increasing delay between retries
2. **Circuit breaker**: Stop retrying after threshold
3. **Request queuing**: Buffer requests when rate limited
4. **Token bucket**: Control request rate
5. **Fallback mechanisms**: Use cached data when unavailable

```python
import time
from functools import wraps

def retry_with_backoff(max_retries=3, base_delay=1):
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(max_retries):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    if attempt == max_retries - 1:
                        raise
                    delay = base_delay * (2 ** attempt)
                    time.sleep(delay)
        return wrapper
    return decorator
```

**Follow-up:** How would you differentiate between rate limiting and actual errors?
</details>

<details>
<summary>🎤 Q9: How would you implement device info collection without Termux:API?</summary>

**Answer:**
Alternative methods without Termux:API:
1. **Direct file reading**: `/proc/` and `/sys/` filesystems
2. **System commands**: `getprop`, `dumpsys`, `settings`
3. **Native APIs**: Using JNI to call Android APIs
4. **ADB commands**: If ADB access is available
5. **Package manager**: `pm` and `cmd package` commands

```python
def get_battery_without_api():
    # Read from /sys/class/power_supply/
    with open('/sys/class/power_supply/battery/capacity') as f:
        percentage = f.read().strip()
    with open('/sys/class/power_supply/battery/status') as f:
        status = f.read().strip()
    return {'percentage': int(percentage), 'status': status}
```

**Follow-up:** What limitations exist compared to using Termux:API?
</details>

<details>
<summary>🎤 Q10: How would you implement a distributed device info collection system?</summary>

**Answer:**
Distributed system architecture:
1. **Master-worker model**: Central coordinator, distributed collectors
2. **Message queue**: RabbitMQ/Redis for task distribution
3. **API gateway**: REST/gRPC endpoints for collection
4. **Database sharding**: Distribute storage by region/device type
5. **Consistent hashing**: For load balancing and caching

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Client 1  │     │   Client 2  │     │   Client N  │
└──────┬──────┘     └──────┬──────┘     └──────┬──────┘
       │                   │                   │
       └───────────────────┼───────────────────┘
                          │
                    ┌─────▼─────┐
                    │    API    │
                    │  Gateway  │
                    └─────┬─────┘
                          │
                    ┌─────▼─────┐
                    │   Queue   │
                    └─────┬─────┘
                          │
       ┌──────────────────┼──────────────────┐
       │                  │                  │
 ┌─────▼─────┐     ┌─────▼─────┐     ┌─────▼─────┐
 │  Worker 1 │     │  Worker 2 │     │  Worker N │
 └───────────┘     └───────────┘     └───────────┘
```

**Follow-up:** How would you handle network partitions and eventual consistency?
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Device Onboarding for IT Department

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    🖥️ DEVICE ONBOARDING SCENARIO                          │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: IT department needs to document a new employee's device     │
│  for asset management and security compliance.                           │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Run the phone info extractor                                          │
│  python phone_info_extractor.py --full-report                            │
│                                                                          │
│  # The tool will generate:                                               │
│  # - JSON report with all device details                                 │
│  # - HTML report for HR documentation                                    │
│  # - Text summary for quick reference                                    │
│                                                                          │
│  Sample output:                                                          │
│  ──────────────                                                          │
│  Device: Samsung Galaxy S23 (SM-S911B)                                   │
│  Serial: R5CT50XXXXX                                                     │
│  Android: 14 (API 34)                                                    │
│  IMEI: 352XXXXXXXXXXXX                                                   │
│  Storage: 128GB (45GB used)                                              │
│  Security Patch: 2024-01-01                                              │
│                                                                          │
│  ✅ Reports saved to ~/storage/downloads/phone_info/                     │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 2: Troubleshooting Slow Performance

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    🔧 PERFORMANCE TROUBLESHOOTING                         │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: User reports phone is running slow. Need to diagnose.       │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Check memory usage                                                    │
│  cat /proc/meminfo | grep -E "MemTotal|MemFree|MemAvailable"             │
│                                                                          │
│  # Check storage space                                                   │
│  df -h                                                                   │
│                                                                          │
│  # Check CPU temperature and battery                                     │
│  termux-battery-status                                                   │
│                                                                          │
│  # Check running processes                                               │
│  ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head -10                  │
│                                                                          │
│  Diagnosis output:                                                       │
│  ─────────────────                                                       │
│  Memory: 6GB total, 4.2GB used (70% - Moderate usage)                    │
│  Storage: 64GB total, 58GB used (90% - Near capacity!)                   │
│  Battery: 45°C (Running hot!)                                            │
│  Top process: com.app.chrome - 800MB RAM                                 │
│                                                                          │
│  💡 Recommendation: Clear cache, delete unused files, check for         │
│     background apps. Storage is nearly full!                             │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 3: Security Audit Data Collection

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    🔒 SECURITY AUDIT DATA COLLECTION                      │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Security auditor needs device information for compliance.   │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Generate comprehensive security report                                │
│  python phone_info_extractor.py --security-audit                        │
│                                                                          │
│  Key data collected:                                                     │
│  ──────────────────                                                      │
│  • Android version & security patch level                                │
│  • Device encryption status                                              │
│  • Installed applications list                                           │
│  • Network configuration                                                 │
│  • Developer options status                                              │
│  • USB debugging status                                                  │
│  • Screen lock type                                                      │
│                                                                          │
│  Security Checklist:                                                     │
│  ──────────────────                                                      │
│  ✅ Android 14 (Up to date)                                              │
│  ✅ Security Patch: January 2024                                         │
│  ✅ Device Encrypted                                                     │
│  ⚠️ USB Debugging: ENABLED (Risk)                                        │
│  ⚠️ Root Access: DETECTED (Risk)                                         │
│  ❌ Screen Lock: None (Critical Risk)                                    │
│                                                                          │
│  📋 Report generated: security_audit_20241215.json                       │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 4: App Compatibility Check

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📲 APP COMPATIBILITY CHECK                             │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: Developer needs to verify device meets app requirements.    │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Quick device spec check                                               │
│  echo "Model: $(getprop ro.product.model)"                               │
│  echo "Android: $(getprop ro.build.version.release)"                     │
│  echo "SDK: $(getprop ro.build.version.sdk)"                             │
│  echo "RAM: $(cat /proc/meminfo | head -1)"                              │
│  echo "CPU Cores: $(cat /proc/cpuinfo | grep processor | wc -l)"         │
│                                                                          │
│  Output:                                                                 │
│  ────────                                                                │
│  Model: Pixel 7 Pro                                                      │
│  Android: 14                                                             │
│  SDK: 34                                                                 │
│  RAM: MemTotal: 11853884 kB (12GB)                                       │
│  CPU Cores: 8                                                            │
│                                                                          │
│  App Requirements Check:                                                 │
│  ────────────────────                                                    │
│  App: NewGame Pro                                                        │
│  Minimum: Android 11 (SDK 30), 4GB RAM                                   │
│  ✅ Device EXCEEDS requirements!                                         │
│  Performance expectation: Excellent                                      │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 5: Network Troubleshooting

```
┌──────────────────────────────────────────────────────────────────────────┐
│                    📶 NETWORK TROUBLESHOOTING                             │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Situation: User reports WiFi connectivity issues.                       │
│                                                                          │
│  Commands to use:                                                        │
│  ──────────────────                                                      │
│                                                                          │
│  # Check WiFi connection                                                 │
│  termux-wifi-connectioninfo                                              │
│                                                                          │
│  # Check IP addresses                                                    │
│  ip addr show wlan0                                                      │
│                                                                          │
│  # Test connectivity                                                     │
│  ping -c 4 google.com                                                    │
│  ping -c 4 8.8.8.8                                                       │
│                                                                          │
│  # Check DNS                                                             │
│  nslookup google.com                                                     │
│                                                                          │
│  Diagnostic output:                                                      │
│  ─────────────────                                                       │
│  WiFi: Connected to "MyWiFi"                                             │
│  Signal: -72 dBm (Weak)                                                  │
│  Local IP: 192.168.1.105                                                 │
│  Public IP: Timeout (No internet!)                                       │
│  DNS: 192.168.1.1 (Router)                                               │
│                                                                          │
│  🔍 Issue: Weak signal (-72 dBm) + DNS resolution failing                │
│  💡 Recommendation: Move closer to router or check DNS settings          │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 PROJECT ARCHITECTURE DIAGRAMS

### Phone Info Extractor Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PHONE INFO EXTRACTOR ARCHITECTURE                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                         DATA SOURCES                                  │    │
│  │                                                                        │    │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐    │    │
│  │  │Termux APIs  │ │System Files │ │  Commands   │ │ Environment │    │    │
│  │  │             │ │ /proc/*     │ │ getprop     │ │ Variables   │    │    │
│  │  │• Battery    │ │ /sys/*      │ │ pm          │ │ HOME, PATH  │    │    │
│  │  │• WiFi       │ │ cpuinfo     │ │ df          │ │ etc.        │    │    │
│  │  │• Telephony  │ │ meminfo     │ │ ip          │ │             │    │    │
│  │  └──────┬──────┘ └──────┬──────┘ └──────┬──────┘ └──────┬──────┘    │    │
│  │         │               │               │               │             │    │
│  └─────────┼───────────────┼───────────────┼───────────────┼────────────┘    │
│            │               │               │               │                  │
│            ▼               ▼               ▼               ▼                  │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                        COLLECTION LAYER                               │    │
│  │                                                                        │    │
│  │  ┌──────────────────────────────────────────────────────────────┐    │    │
│  │  │                     run_command()                             │    │    │
│  │  │  • Execute shell commands                                     │    │    │
│  │  │  • Capture output                                              │    │    │
│  │  │  • Handle errors                                               │    │    │
│  │  └──────────────────────────────────────────────────────────────┘    │    │
│  │                                                                        │    │
│  │  ┌──────────────────────────────────────────────────────────────┐    │    │
│  │  │                   run_json_command()                          │    │    │
│  │  │  • Execute command                                             │    │    │
│  │  │  • Parse JSON response                                         │    │    │
│  │  │  • Return Python dict                                          │    │    │
│  │  └──────────────────────────────────────────────────────────────┘    │    │
│  │                                                                        │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                │                                            │
│                                ▼                                            │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                      PROCESSING LAYER                                 │    │
│  │                                                                        │    │
│  │  ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐            │    │
│  │  │ get_device│ │get_battery│ │ get_cpu   │ │get_network│            │    │
│  │  │ _info()   │ │ _info()   │ │ _info()   │ │ _info()   │            │    │
│  │  └───────────┘ └───────────┘ └───────────┘ └───────────┘            │    │
│  │                                                                        │    │
│  │  ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐            │    │
│  │  │get_memory │ │get_storage│ │get_telepho│ │get_termux │            │    │
│  │  │ _info()   │ │ _info()   │ │ ny_info() │ │ _info()   │            │    │
│  │  └───────────┘ └───────────┘ └───────────┘ └───────────┘            │    │
│  │                                                                        │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                │                                            │
│                                ▼                                            │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                        OUTPUT LAYER                                   │    │
│  │                                                                        │    │
│  │  ┌───────────────┐  ┌───────────────┐  ┌───────────────┐            │    │
│  │  │ format_text   │  │ format_json   │  │ format_html   │            │    │
│  │  │ _output()     │  │ _output()     │  │ _output()     │            │    │
│  │  └───────┬───────┘  └───────┬───────┘  └───────┬───────┘            │    │
│  │          │                  │                  │                      │    │
│  │          ▼                  ▼                  ▼                      │    │
│  │    [Console]           [.json]             [.html]                   │    │
│  │                                                                        │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Data Collection Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    DATA COLLECTION FLOW                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   START                                                                      │
│     │                                                                        │
│     ▼                                                                        │
│   ┌─────────────────────────────────────────┐                              │
│   │         collect_all_info()               │                              │
│   │                                         │                              │
│   │  Coordinates all information gathering   │                              │
│   └───────────────────┬─────────────────────┘                              │
│                       │                                                      │
│     ┌─────────────────┼─────────────────┬─────────────────┐                │
│     │                 │                 │                 │                │
│     ▼                 ▼                 ▼                 ▼                │
│   ┌───────┐       ┌───────┐       ┌───────┐       ┌───────┐              │
│   │Device │       │Battery│       │  CPU  │       │Memory │              │
│   │ Info  │       │ Info  │       │ Info  │       │ Info  │              │
│   └───┬───┘       └───┬───┘       └───┬───┘       └───┬───┘              │
│       │               │               │               │                    │
│       │ getprop       │ termux-api    │ /proc/        │ /proc/            │
│       │ commands      │ commands      │ cpuinfo       │ meminfo           │
│       │               │               │               │                    │
│   ┌───┴───┐       ┌───┴───┐       ┌───┴───┐       ┌───┴───┐              │
│   │Storage│       │Network│       │Telephony│     │Termux │              │
│   │ Info  │       │ Info  │       │  Info   │      │ Info  │              │
│   └───┬───┘       └───┬───┘       └───┬────┘       └───┬───┘              │
│       │               │               │               │                    │
│       │ df -h         │ termux-wifi   │ termux-       │ env vars          │
│       │               │ connectioninfo│ telephony     │ pkg list          │
│       │               │               │               │                    │
│       └───────────────┴───────────────┴───────────────┘                    │
│                               │                                            │
│                               ▼                                            │
│   ┌─────────────────────────────────────────┐                              │
│   │              Data Dictionary              │                              │
│   │                                         │                              │
│   │  {                                      │                              │
│   │    "timestamp": "2024-12-15 14:30:00",  │                              │
│   │    "device": {...},                     │                              │
│   │    "battery": {...},                    │                              │
│   │    "cpu": {...},                        │                              │
│   │    "memory": {...},                     │                              │
│   │    "network": {...},                    │                              │
│   │    "telephony": {...}                   │                              │
│   │  }                                      │                              │
│   └───────────────────┬─────────────────────┘                              │
│                       │                                                      │
│     ┌─────────────────┼─────────────────┐                                  │
│     │                 │                 │                                    │
│     ▼                 ▼                 ▼                                    │
│  [TEXT]            [JSON]           [HTML]                                  │
│   Output            Report          Report                                  │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

### Chapter Dependencies and Navigation

| Category | Chapter | Topic | Connection |
|----------|---------|-------|------------|
| **Prerequisites** | Ch47 | Python Basics | File I/O, JSON parsing |
| | Ch48 | Advanced Python | subprocess module |
| | Ch50 | Termux API | API commands |
| **Related Projects** | Ch51 | Password Generator | Security tools |
| | Ch53 | WiFi Analyzer | Network diagnostics |
| | Ch55 | Port Scanner | Network security |
| **Next Steps** | Ch57 | Backup Automation | Device backup |
| | Ch61 | Security Best Practices | Device hardening |

### Learning Path

```
Module 9 Projects Flow:
═══════════════════════

Ch51 Password Generator ──▶ Ch52 Phone Info ──▶ Ch53 WiFi Analyzer
         │                        │                     │
         ▼                        ▼                     ▼
    [Security]              [Diagnostics]        [Network Security]
         │                        │                     │
         └────────────────────────┼─────────────────────┘
                                  │
                                  ▼
                         Ch54-57 More Projects
```

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Remote Device Monitoring

```python
import requests
import json
from datetime import datetime

class RemoteDeviceMonitor:
    """
    Send device info to remote server for monitoring
    """
    def __init__(self, server_url, api_key):
        self.server_url = server_url
        self.api_key = api_key
    
    def send_report(self, device_info):
        """Send device info to monitoring server"""
        payload = {
            'device_id': self._generate_device_id(),
            'timestamp': datetime.now().isoformat(),
            'data': device_info
        }
        
        headers = {
            'Authorization': f'Bearer {self.api_key}',
            'Content-Type': 'application/json'
        }
        
        try:
            response = requests.post(
                f'{self.server_url}/api/device/report',
                json=payload,
                headers=headers,
                timeout=10
            )
            return response.status_code == 200
        except requests.RequestException as e:
            print(f"Failed to send report: {e}")
            return False
    
    def _generate_device_id(self):
        """Generate unique device identifier"""
        import hashlib
        serial = run_command("getprop ro.serialno")
        model = run_command("getprop ro.product.model")
        unique = f"{serial}:{model}"
        return hashlib.md5(unique.encode()).hexdigest()[:12]
```

### Advanced Technique 2: Automated Report Scheduling

```python
import schedule
import time
from threading import Thread

class ScheduledReporter:
    """
    Schedule automatic device info collection
    """
    def __init__(self, output_dir):
        self.output_dir = output_dir
        self.running = False
    
    def start(self, interval_hours=24):
        """Start scheduled reporting"""
        schedule.every(interval_hours).hours.do(self._collect_and_save)
        
        # Also run at startup
        self._collect_and_save()
        
        self.running = True
        thread = Thread(target=self._run_scheduler, daemon=True)
        thread.start()
    
    def stop(self):
        """Stop scheduled reporting"""
        self.running = False
        schedule.clear()
    
    def _run_scheduler(self):
        while self.running:
            schedule.run_pending()
            time.sleep(60)
    
    def _collect_and_save(self):
        """Collect info and save to file"""
        from datetime import datetime
        
        data = collect_all_info()
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        filename = f"device_info_{timestamp}.json"
        filepath = os.path.join(self.output_dir, filename)
        
        with open(filepath, 'w') as f:
            json.dump(data, f, indent=2, default=str)
        
        print(f"Report saved: {filepath}")
        
        # Send notification
        os.system(f'termux-notification --title "Device Report" '
                  f'--content "Saved: {filename}"')

# Usage
reporter = ScheduledReporter("~/reports")
reporter.start(interval_hours=24)  # Daily reports
```

### Advanced Technique 3: Device Comparison Tool

```python
import json
from difflib import unified_diff

class DeviceComparator:
    """
    Compare device info between two snapshots or devices
    """
    def compare_snapshots(self, file1, file2):
        """Compare two device info snapshots"""
        with open(file1) as f:
            data1 = json.load(f)
        with open(file2) as f:
            data2 = json.load(f)
        
        differences = {}
        
        for category in data1:
            if category == 'timestamp':
                continue
            
            if category in data2:
                diff = self._compare_dicts(data1[category], data2[category])
                if diff:
                    differences[category] = diff
        
        return differences
    
    def _compare_dicts(self, dict1, dict2, path=""):
        """Recursively compare dictionaries"""
        differences = []
        
        all_keys = set(dict1.keys()) | set(dict2.keys())
        
        for key in all_keys:
            current_path = f"{path}.{key}" if path else key
            
            if key not in dict1:
                differences.append({
                    'path': current_path,
                    'change': 'ADDED',
                    'value': dict2[key]
                })
            elif key not in dict2:
                differences.append({
                    'path': current_path,
                    'change': 'REMOVED',
                    'value': dict1[key]
                })
            elif dict1[key] != dict2[key]:
                if isinstance(dict1[key], dict) and isinstance(dict2[key], dict):
                    nested = self._compare_dicts(dict1[key], dict2[key], current_path)
                    differences.extend(nested)
                else:
                    differences.append({
                        'path': current_path,
                        'change': 'MODIFIED',
                        'old': dict1[key],
                        'new': dict2[key]
                    })
        
        return differences
    
    def generate_diff_report(self, differences):
        """Generate human-readable diff report"""
        report = []
        report.append("=" * 60)
        report.append("DEVICE INFO CHANGE REPORT")
        report.append("=" * 60)
        
        for category, changes in differences.items():
            report.append(f"\n[{category.upper()}]")
            report.append("-" * 40)
            for change in changes:
                if change['change'] == 'ADDED':
                    report.append(f"  + {change['path']}: {change['value']}")
                elif change['change'] == 'REMOVED':
                    report.append(f"  - {change['path']}: {change['value']}")
                else:
                    report.append(f"  ~ {change['path']}:")
                    report.append(f"      Old: {change['old']}")
                    report.append(f"      New: {change['new']}")
        
        return "\n".join(report)

# Usage
comparator = DeviceComparator()
diff = comparator.compare_snapshots(
    "device_info_20241201.json",
    "device_info_20241215.json"
)
print(comparator.generate_diff_report(diff))
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### What You Should Have Learned

- [ ] Understanding of Termux API commands for device info
- [ ] Using `getprop` to retrieve Android system properties
- [ ] Reading system files from `/proc/` filesystem
- [ ] JSON parsing in Python with the `json` module
- [ ] Using `subprocess` to execute shell commands
- [ ] HTML report generation with embedded CSS
- [ ] File handling and path manipulation with `os` and `pathlib`
- [ ] Error handling for missing APIs and permissions
- [ ] Creating formatted text, JSON, and HTML outputs
- [ ] Battery, WiFi, telephony API usage

### Skills Acquired

| Skill | Level | Description |
|-------|-------|-------------|
| API Integration | ⭐⭐⭐ | Using Termux APIs for data collection |
| System Programming | ⭐⭐⭐ | Reading /proc and executing commands |
| JSON Processing | ⭐⭐⭐ | Parsing and generating JSON data |
| Report Generation | ⭐⭐ | Creating multi-format reports |
| Error Handling | ⭐⭐ | Graceful handling of failures |

---

## 🚀 PROJECT CHALLENGES

### Challenge 1: Real-time Device Dashboard

**Task:** Create a web-based dashboard that displays device information in real-time with auto-refresh.

**Requirements:**
- Use Flask or FastAPI for the web server
- Auto-refresh every 30 seconds
- Visual indicators for battery, storage, memory
- Historical charts for resource usage

**Hint:** Store data in SQLite and use Chart.js for visualization.

```bash
# Expected usage:
python dashboard.py --port 8080
# Open browser to http://localhost:8080
```

### Challenge 2: Device Fingerprinting System

**Task:** Implement a device fingerprinting system that can uniquely identify devices across sessions.

**Requirements:**
- Combine multiple identifiers (IMEI, serial, MAC)
- Generate consistent hash across runs
- Detect device changes (new apps, settings)
- Alert on significant changes

**Hint:** Use hashlib for consistent fingerprinting.

```bash
# Expected usage:
python fingerprint.py --generate
python fingerprint.py --verify
```

### Challenge 3: Multi-Device Inventory System

**Task:** Build a system to collect and manage info from multiple devices.

**Requirements:**
- Central server to receive device reports
- Device registration and authentication
- Web UI to view all devices
- Alert system for policy violations

**Hint:** Use a simple REST API with token authentication.

```bash
# Expected usage:
# On each device:
python reporter.py --server http://inventory.local --token DEVICE_TOKEN

# On server:
python inventory_server.py --port 5000
```

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always verify Termux:API app is installed before running - use `termux-battery-status` as a quick test!

> 💡 **Pro Tip #2:** Use JSON output format (`--json`) for easy parsing in automation scripts and CI/CD pipelines!

> 💡 **Pro Tip #3:** The HTML report can be styled with custom CSS - check the `format_html_output()` function!

> 💡 **Pro Tip #4:** For security audits, combine this with Ch51 Password Generator to get device info AND generate secure passwords!

> 💡 **Pro Tip #5:** `/proc/cpuinfo` shows ALL CPU cores - count them to know your device's processing power!

> 💡 **Pro Tip #6:** Use `getprop` commands in other scripts too - they work without Termux:API app!

> 💡 **Pro Tip #7:** Battery temperature above 40°C indicates heavy load or charging issues - monitor it!

> 💡 **Pro Tip #8:** Save reports with timestamps for device history tracking - useful for diagnostics!

> 💡 **Pro Tip #9:** The `get_installed_apps()` function can be modified to show ALL packages, not just third-party!

> 💡 **Pro Tip #10:** Combine with cloud upload for remote device inventory management!

---

## 🔥 REAL WORLD USE CASES

### Real World Applications of Phone Info Extractor

**1. IT Support & Helpdesk**
- Quick device diagnostics for troubleshooting
- Remote device identification without physical access
- Software compatibility checks based on Android version

**2. Security Auditing**
- Device fingerprinting for compliance
- Inventory management for corporate devices
- Security patch level verification

**3. App Development**
- Testing app compatibility across devices
- Gathering device specs for bug reports
- Performance benchmarking baseline

**4. Device Resale/Trade-in**
- Complete device specification for listings
- Verify device authenticity
- Document device condition before sale

**5. Forensics & Investigation**
- Digital evidence collection
- Device identification in legal cases
- Timeline reconstruction with timestamps

**6. Personal Use**
- Know your device inside out
- Check battery health over time
- Monitor storage and memory usage

---

## ⚡ QUICK REFERENCE CARD

### Phone Info Extractor Quick Reference

| Function | Description | Returns |
|----------|-------------|---------|
| `get_device_info()` | Device model, manufacturer, serial | Dict with 10 keys |
| `get_android_info()` | Android version, build info | Dict with 11 keys |
| `get_battery_info()` | Battery status, health, temp | Dict with 6 keys |
| `get_cpu_info()` | CPU cores, hardware, features | Dict with core count |
| `get_memory_info()` | RAM total, free, usage % | Dict with 7 keys |
| `get_storage_info()` | Disk partitions, usage | Dict with partitions list |
| `get_network_info()` | WiFi, IP addresses, interfaces | Dict with network data |
| `get_telephony_info()` | SIM, carrier, phone type | Dict with 8 keys |
| `get_kernel_info()` | Kernel version, platform | Dict with 5 keys |
| `get_installed_apps()` | Third-party apps list | Dict with packages |
| `get_termux_info()` | Termux environment details | Dict with 7 keys |

### Key Termux API Commands

| Command | Purpose |
|---------|---------|
| `termux-battery-status` | Battery information (JSON) |
| `termux-wifi-connectioninfo` | WiFi connection details |
| `termux-telephony-deviceinfo` | Phone/SIM information |
| `termux-notification` | Send notification |

### Key getprop Commands

| Command | Returns |
|---------|---------|
| `getprop ro.product.model` | Device model |
| `getprop ro.build.version.release` | Android version |
| `getprop ro.build.version.sdk` | SDK version |
| `getprop ro.product.manufacturer` | Manufacturer |

---

## 🏆 BONUS CONTENT

### Bonus: Advanced Features to Add

**Feature 1: Device Benchmarking**
```python
import time
def benchmark_cpu():
    """Simple CPU benchmark"""
    start = time.time()
    # Perform calculations
    for _ in range(1000000):
        _ = 2 ** 20
    return time.time() - start
```

**Feature 2: Battery Health Tracker**
```python
def track_battery_history():
    """Track battery health over time"""
    history_file = "battery_history.json"
    # Save daily readings and calculate trends
```

**Feature 3: Network Speed Test**
```python
def test_network_speed():
    """Simple network speed test"""
    import urllib.request
    start = time.time()
    urllib.request.urlopen("http://speedtest.net")
    return time.time() - start
```

**Feature 4: Device Comparison**
```python
def compare_devices(current, baseline):
    """Compare current device with baseline"""
    # Highlight differences
    # Identify upgrades/downgrades
```

**Feature 5: QR Code Device Card**
```python
def generate_device_qr(device_info):
    """Generate QR code with device details"""
    import qrcode
    qr = qrcode.make(str(device_info))
    qr.save("device_card.png")
```

---

## 📝 CHAPTER SUMMARY

### What You Learned

- ✅ **Termux API Integration** - Using Termux:API for device information
- ✅ **System File Reading** - Parsing `/proc/` filesystem for hardware info
- ✅ **getprop Commands** - Extracting Android system properties
- ✅ **JSON Parsing** - Processing API responses in Python
- ✅ **HTML Report Generation** - Creating beautiful reports from data
- ✅ **Modular Code Design** - Organizing functions by information type
- ✅ **Error Handling** - Graceful handling of missing APIs
- ✅ **File Export** - Multiple output formats (JSON, HTML, TXT)

### Key Takeaways

1. **Termux APIs are powerful** - Much device info available without root
2. **System files reveal secrets** - `/proc/` contains detailed hardware info
3. **Multiple export formats** - Always provide options for users
4. **Error handling is critical** - APIs may not be available on all devices

---

## 🚀 PROJECT EXTENSIONS

### 5+ Ideas to Extend This Project

**Extension 1: Remote Device Dashboard** ⭐⭐⭐⭐
- Upload device info to a central server
- Web dashboard to view all devices
- **Steps:** Create Flask backend, build dashboard UI

**Extension 2: Automated Inventory System** ⭐⭐⭐
- Schedule regular device info collection
- Track device changes over time
- **Steps:** Add cron job, create database storage

**Extension 3: Device Health Monitor** ⭐⭐⭐
- Monitor battery degradation
- Alert on storage running low
- **Steps:** Add thresholds, implement notifications

**Extension 4: Security Compliance Checker** ⭐⭐⭐⭐
- Check security patch level
- Verify encryption status
- **Steps:** Add compliance rules engine

**Extension 5: Device Comparison Tool** ⭐⭐⭐
- Compare multiple devices side-by-side
- Identify performance bottlenecks
- **Steps:** Create comparison UI, benchmark tests

**Extension 6: Export to PDF Report** ⭐⭐⭐
- Professional PDF documents
- Include charts and graphs
- **Steps:** Use reportlab or weasyprint

---

## 🔧 CODE WALKTHROUGH

### Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PHONE INFO EXTRACTOR FLOW                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   DATA SOURCES              PROCESSING              OUTPUT           │
│   ────────────              ──────────              ──────           │
│                                                                      │
│   ┌─────────────┐      ┌─────────────┐       ┌─────────────┐        │
│   │ Termux APIs │ ───► │   JSON      │ ───►  │   Display   │        │
│   │             │      │   Parser    │       │   (Console) │        │
│   └─────────────┘      └─────────────┘       └─────────────┘        │
│         │                    │                                      │
│         │ battery-status     │ Parsed                               │
│         │ wifi-connection    │ Data                                 │
│         │ telephony          │                                      │
│         │                    ▼                                      │
│   ┌─────────────┐      ┌─────────────┐       ┌─────────────┐        │
│   │ System Files│ ───► │   Text      │ ───►  │   Export    │        │
│   │ /proc/*     │      │   Parser    │       │   (Files)   │        │
│   └─────────────┘      └─────────────┘       └─────────────┘        │
│         │                    │                    │                  │
│         │ cpuinfo            │ Formatted          │ JSON            │
│         │ meminfo            │ Data               │ HTML            │
│         │ version            │                    │ TXT             │
│         │                    ▼                                      │
│   ┌─────────────┐      ┌─────────────┐                             │
│   │ getprop     │ ───► │   Data      │                             │
│   │ Commands    │      │   Aggregator│                             │
│   └─────────────┘      └─────────────┘                             │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Key Function Explanation

```python
def run_json_command(cmd):
    """
    Run Termux API command and parse JSON response.
    
    Flow:
    1. subprocess.run() - Execute shell command
    2. capture_output=True - Capture stdout/stderr
    3. json.loads() - Parse JSON response
    4. Return Python dictionary
    
    Error handling:
    - Returns None on failure
    - Handles missing APIs gracefully
    """
```

---

## 📦 DEPLOYMENT GUIDE

### How to Deploy and Share This Project

**1. Create Standalone Script**
```bash
# The script is already standalone!
# Just copy phone_info_extractor.py
```

**2. Create Installation Script**
```bash
cat > install.sh << 'EOF'
#!/bin/bash
pkg install python termux-api -y
pip install colorama
echo "Installation complete!"
echo "Run: python phone_info_extractor.py"
EOF
chmod +x install.sh
```

**3. Share via GitHub**
```bash
git init
git add phone_info_extractor.py install.sh README.md
git commit -m "Phone Info Extractor - Complete device information tool"
git push origin main
```

**4. Create Requirements File**
```
colorama>=0.4.0
```

**5. Usage in Other Projects**
```python
# Import as module
from phone_info_extractor import get_device_info, get_battery_info

device = get_device_info()
battery = get_battery_info()
print(f"Device: {device['model']}")
print(f"Battery: {battery['percentage']}%")
```

---

## 🔗 RELATED CHAPTERS

### Cross-Reference to Related Chapters

| Chapter | Topic | Connection |
|---------|-------|------------|
| **Ch51** | Password Generator | Security tools family |
| **Ch53** | WiFi Analyzer | Uses similar Termux APIs |
| **Ch55** | Port Scanner | Network security tools |
| **Ch57** | Backup Automation | Device info for backup config |
| **Ch47** | Python Basics | Foundation for this project |
| **Ch50** | Termux API Deep Dive | API commands reference |

### Prerequisite Chapters
- 📖 **Ch47: Python Basics** - Python fundamentals
- 📖 **Ch50: Termux API** - Understanding Termux APIs
- 📖 **Ch48: File Operations** - Reading system files

### Next Steps
- ➡️ **Ch53: WiFi Analyzer** - Network information tool
- ➡️ **Ch54: YouTube Downloader** - Media automation project

---

## 🎮 INTERACTIVE ELEMENTS

### Quiz: Test Your Phone Info Extractor Knowledge!

**Question 1:** Which Termux API command returns battery status?
- a) `termux-battery` 
- b) `termux-battery-status` ✓
- c) `termux-power`
- d) `termux-device-battery`

**Question 2:** What does `getprop ro.product.model` return?
- a) Manufacturer name
- b) Android version
- c) Device model name ✓
- d) Serial number

**Question 3:** Which file contains CPU information in Android?
- a) `/proc/cpu` 
- b) `/proc/cpuinfo` ✓
- c) `/sys/cpu`
- d) `/dev/cpu`

**Question 4:** What is the minimum required for Termux API commands?
- a) Root access
- b) Termux:API app ✓
- c) Android 10+
- d) Special permissions

**Question 5:** Which function returns RAM information?
- a) `get_cpu_info()`
- b) `get_memory_info()` ✓
- c) `get_storage_info()`
- d) `get_system_info()`

**Question 6:** What format does termux-battery-status output?
- a) XML
- b) Plain text
- c) JSON ✓
- d) CSV

**Question 7:** Which command shows installed packages?
- a) `pm list packages -3` ✓
- b) `apt list`
- c) `pkg show`
- d) `dpkg -l`

**Question 8:** What file shows kernel version?
- a) `/proc/version` ✓
- b) `/proc/kernel`
- c) `/sys/version`
- d) `/etc/kernel`

**Question 9:** Which output format includes styling?
- a) JSON
- b) TXT
- c) HTML ✓
- d) CSV

**Question 10:** What does `get_termux_info()` return?
- a) Device info
- b) Termux environment details ✓
- c) App info
- d) System info

**Question 11:** Which function gets WiFi connection details?
- a) `get_network_info()` ✓
- b) `get_wifi_info()`
- c) `get_connection_info()`
- d) `get_internet_info()`

**Question 12:** What permission is needed for WiFi scan?
- a) Storage
- b) Location ✓
- c) Phone
- d) Camera

---

### Extend the Project Challenges

**Challenge 1:** Add sensor information extraction
```python
# Hint: Read from /sys/class/sensors/
def get_sensor_info():
    # List all available sensors
    # Read sensor values
    pass
```

**Challenge 2:** Implement device comparison feature
```python
# Compare current device with saved baseline
def compare_with_baseline(current, baseline_file):
    # Highlight differences
    # Show improvements/degradations
    pass
```

**Challenge 3:** Add real-time monitoring mode
```python
# Continuously monitor and log changes
def monitor_mode(interval=60):
    # Check battery, memory, storage
    # Alert on significant changes
    pass
```

### Bug Fixing Exercises

**Bug 1:** Why might `get_battery_info()` fail?
```python
def get_battery_info():
    battery = run_json_command("termux-battery-status")
    if battery:
        return {...}
    return {"error": "Unable to get battery info"}
```
*Issue: Termux:API app might not be installed. Add error handling.*

**Bug 2:** Memory calculation seems wrong:
```python
memory["total_ram"] = f"{mem_total // 1024} MB"  # Shows less than actual
```
*Issue: MemTotal is already in kB, division is correct. Check if it's MemAvailable you need.*

**Bug 3:** Installed apps list is empty:
```python
output = run_command("pm list packages -3")  # Only third-party apps
```
*Fix: Use "pm list packages" for all apps, or check if pm command is available*

---

## 📖 TECHNICAL GUIDE

### 1. Project Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PHONE INFO EXTRACTOR ARCHITECTURE                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Information Sources                           │   │
│   │                                                                   │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │   │
│   │   │ Termux APIs │  │ System Files│  │ getprop     │             │   │
│   │   │             │  │             │  │ Commands    │             │   │
│   │   │ - battery   │  │ - /proc/    │  │ - model     │             │   │
│   │   │ - wifi      │  │ - cpuinfo   │  │ - version   │             │   │
│   │   │ - telephony │  │ - meminfo   │  │ - build     │             │   │
│   │   └──────┬──────┘  └──────┬──────┘  └──────┬──────┘             │   │
│   │          │                │                │                     │   │
│   └──────────┼────────────────┼────────────────┼─────────────────────┘   │
│              │                │                │                         │
│              ▼                ▼                ▼                         │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Python Script                                 │   │
│   │                                                                   │   │
│   │   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │   │
│   │   │ Collectors  │  │ Processors  │  │ Formatters  │             │   │
│   │   │             │  │             │  │             │             │   │
│   │   │ - device    │  │ - JSON      │  │ - Text      │             │   │
│   │   │ - battery   │  │ - Dict      │  │ - JSON      │             │   │
│   │   │ - cpu       │  │ - Parsing   │  │ - HTML      │             │   │
│   │   │ - memory    │  │             │  │             │             │   │
│   │   │ - network   │  │             │  │             │             │   │
│   │   └─────────────┘  └─────────────┘  └─────────────┘             │   │
│   │                                                                   │   │
│   └───────────────────────────────┬─────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    Output                                        │   │
│   │                                                                   │   │
│   │   ┌───────────┐  ┌───────────┐  ┌───────────┐                   │   │
│   │   │ Terminal  │  │ JSON File │  │ HTML File │                   │   │
│   │   │ (colored) │  │ (.json)   │  │ (.html)   │                   │   │
│   │   └───────────┘  └───────────┘  └───────────┘                   │   │
│   │                                                                   │   │
│   │   ┌───────────┐                                                  │   │
│   │   │ Text File │                                                  │   │
│   │   │ (.txt)    │                                                  │   │
│   │   └───────────┘                                                  │   │
│   │                                                                   │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Information Sources Matrix

| Category | Source | Method | Access Required |
|----------|--------|--------|-----------------|
| Device Model | getprop | subprocess | None |
| Android Version | getprop | subprocess | None |
| Battery Status | termux-battery-status | Termux API | Termux:API app |
| WiFi Info | termux-wifi-connectioninfo | Termux API | Location permission |
| Telephony | termux-telephony-deviceinfo | Termux API | Phone permission |
| CPU Info | /proc/cpuinfo | File read | None |
| Memory Info | /proc/meminfo | File read | None |
| Storage | df command | subprocess | Storage permission |
| IP Address | ip route / curl | subprocess | Network |
| Kernel | /proc/version | File read | None |
| Apps | pm list packages | subprocess | None |

### 3. Termux API Requirements

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX API SETUP REQUIREMENTS                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Required Apps:                                                         │
│   ├── Termux (main app)                                                 │
│   ├── Termux:API (API bridge app)                                       │
│   └── Both from F-Droid (NOT Play Store)                                │
│                                                                          │
│   Required Packages:                                                     │
│   ├── termux-api (command-line tools)                                   │
│   └── pkg install termux-api                                            │
│                                                                          │
│   Required Permissions:                                                  │
│   ├── Storage - for saving reports                                      │
│   ├── Location - for WiFi scanning                                      │
│   ├── Phone - for telephony info                                        │
│   └── termux-setup-storage                                              │
│                                                                          │
│   API Commands Available:                                                │
│   ├── termux-battery-status                                             │
│   ├── termux-call-log                                                   │
│   ├── termux-camera-info                                                │
│   ├── termux-camera-photo                                               │
│   ├── termux-clipboard-get                                              │
│   ├── termux-clipboard-set                                              │
│   ├── termux-contact-list                                               │
│   ├── termux-download                                                   │
│   ├── termux-fingerprint                                                │
│   ├── termux-infrared-frequencies                                       │
│   ├── termux-infrared-transmit                                          │
│   ├── termux-location                                                   │
│   ├── termux-media-player                                               │
│   ├── termux-media-scan                                                 │
│   ├── termux-notification                                               │
│   ├── termux-sensor                                                     │
│   ├── termux-share                                                      │
│   ├── termux-sms-list                                                   │
│   ├── termux-sms-send                                                   │
│   ├── termux-storage-get                                                │
│   ├── termux-telephony-call                                             │
│   ├── termux-telephony-cellinfo                                         │
│   ├── termux-telephony-deviceinfo                                       │
│   ├── termux-toast                                                      │
│   ├── termux-torch                                                      │
│   ├── termux-tts-engines                                                │
│   ├── termux-tts-speak                                                  │
│   ├── termux-vibrate                                                    │
│   ├── termux-volume                                                     │
│   ├── termux-wifi-connectioninfo                                        │
│   ├── termux-wifi-enable                                                │
│   └── termux-wifi-scaninfo                                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4. Android Properties Reference

```bash
# Device Information
ro.product.model           # Device model name
ro.product.manufacturer    # Device manufacturer
ro.product.brand           # Device brand
ro.product.device          # Device codename
ro.product.name            # Product name
ro.product.board           # Board name
ro.product.cpu.abi         # CPU ABI (arm64-v8a, armeabi-v7a)
ro.hardware                # Hardware identifier
ro.serialno                # Serial number

# Build Information
ro.build.id                # Build ID
ro.build.display.id        # Display build ID
ro.build.version.release   # Android version (11, 12, 13, 14)
ro.build.version.sdk       # SDK version (30, 31, 33, 34)
ro.build.version.codename  # Codename (REL, Tiramisu, UpsideDownCake)
ro.build.version.incremental # Incremental version
ro.build.version.security_patch # Security patch date
ro.build.type              # Build type (user, userdebug, eng)
ro.build.tags              # Build tags (release-keys, test-keys)
ro.build.fingerprint       # Full build fingerprint
ro.build.date              # Build date

# Boot Information
ro.bootloader              # Bootloader version
ro.bootmode                # Boot mode

# Locale
ro.product.locale          # Locale setting
ro.product.locale.language # Language
ro.product.locale.region   # Region

# UI Information
ro.build.characteristics   # Device characteristics (nosdcard, phone, tablet)
```

### 5. System Files Reference

```
/proc/cpuinfo
├── processor    - CPU core number
├── model name   - CPU model name
├── Hardware     - Hardware identifier
├── Features     - CPU features (NEON, VFP, etc.)
├── CPU implementer - CPU manufacturer
├── CPU architecture - Architecture version
├── CPU variant  - CPU variant
├── CPU part     - CPU part number
└── BogoMIPS     - Bogus MIPS rating

/proc/meminfo
├── MemTotal     - Total usable RAM
├── MemFree      - Free RAM
├── MemAvailable - Available RAM for new allocations
├── Buffers      - Buffer cache memory
├── Cached       - Page cache memory
├── SwapCached   - Swap cache
├── Active       - Active memory
├── Inactive     - Inactive memory
├── SwapTotal    - Total swap space
└── SwapFree     - Free swap space

/proc/version
├── Linux version - Kernel version
├── Build info    - Build information
└── Compiler      - GCC version

/proc/net/
├── dev          - Network device statistics
├── route        - Routing table
├── tcp          - TCP connections
└── udp          - UDP connections

/system/build.prop
├── All system properties
└── Requires root access on newer Android
```

---

## 💻 COMPLETE SOURCE CODE

### phone_info_extractor.py

```python
#!/usr/bin/env python3
"""
Phone Info Extractor - Complete Device Information Tool
========================================================
A comprehensive tool to extract and display Android device information
using Termux APIs and system files.

Author: T3rmuxk1ng
Version: 1.0.0
License: MIT

Usage:
    python phone_info_extractor.py          # Run with all outputs
    python phone_info_extractor.py --json   # Output as JSON only
    python phone_info_extractor.py --html   # Output as HTML only
    python phone_info_extractor.py --text   # Output as Text only
    python phone_info_extractor.py --quiet  # No terminal output
    python phone_info_extractor.py -o /path # Custom output directory
"""

import subprocess
import json
import os
import sys
import platform
import re
import argparse
from datetime import datetime
from pathlib import Path

# Try to import colorama, fallback if not available
try:
    from colorama import Fore, Style, init
    HAS_COLORAMA = True
    init()
except ImportError:
    HAS_COLORAMA = False
    # Create dummy color codes
    class Fore:
        GREEN = RED = CYAN = YELLOW = BLUE = MAGENTA = ""
    class Style:
        RESET_ALL = BRIGHT = ""

# ============================================================================
# CONSTANTS
# ============================================================================

VERSION = "1.0.0"
AUTHOR = "T3rmuxk1ng"

# Output directory
DEFAULT_OUTPUT_DIR = "~/storage/downloads/phone_info"

# ============================================================================
# HELPER FUNCTIONS
# ============================================================================

def run_command(cmd, timeout=10):
    """
    Run shell command and return output.
    
    Args:
        cmd (str): Command to execute
        timeout (int): Timeout in seconds
    
    Returns:
        str: Command output or error message
    """
    try:
        result = subprocess.run(
            cmd,
            shell=True,
            capture_output=True,
            text=True,
            timeout=timeout
        )
        return result.stdout.strip()
    except subprocess.TimeoutExpired:
        return "Timeout"
    except Exception as e:
        return f"Error: {str(e)}"


def run_json_command(cmd, timeout=10):
    """
    Run command that returns JSON output.
    
    Args:
        cmd (str): Command to execute
        timeout (int): Timeout in seconds
    
    Returns:
        dict: Parsed JSON or None on error
    """
    try:
        result = subprocess.run(
            cmd,
            shell=True,
            capture_output=True,
            text=True,
            timeout=timeout
        )
        if result.returncode == 0 and result.stdout.strip():
            return json.loads(result.stdout)
        return None
    except subprocess.TimeoutExpired:
        return None
    except json.JSONDecodeError:
        return None
    except Exception:
        return None


def getprop(prop_name):
    """Get Android property using getprop command."""
    return run_command(f"getprop {prop_name}")


def format_size_kb(kb):
    """Format size in KB to human readable format."""
    if kb >= 1024 * 1024:
        return f"{kb / (1024 * 1024):.1f} GB"
    elif kb >= 1024:
        return f"{kb / 1024:.1f} MB"
    else:
        return f"{kb} KB"


def print_status(message, status="info"):
    """Print colored status message."""
    if not HAS_COLORAMA:
        print(f"[{status.upper()}] {message}")
        return
    
    colors = {
        "info": Fore.CYAN,
        "success": Fore.GREEN,
        "warning": Fore.YELLOW,
        "error": Fore.RED
    }
    color = colors.get(status, Fore.WHITE)
    print(f"{color}[{status.upper()}]{Style.RESET_ALL} {message}")


# ============================================================================
# INFORMATION COLLECTORS
# ============================================================================

def get_device_info():
    """Get basic device information using getprop."""
    print_status("Collecting device information...", "info")
    
    properties = {
        "model": getprop("ro.product.model"),
        "manufacturer": getprop("ro.product.manufacturer"),
        "brand": getprop("ro.product.brand"),
        "device": getprop("ro.product.device"),
        "product": getprop("ro.product.name"),
        "board": getprop("ro.product.board"),
        "hardware": getprop("ro.hardware"),
        "serial": getprop("ro.serialno") or "Unavailable",
        "bootloader": getprop("ro.bootloader"),
        "fingerprint": getprop("ro.build.fingerprint"),
        "cpu_abi": getprop("ro.product.cpu.abi"),
        "characteristics": getprop("ro.build.characteristics")
    }
    
    # Clean empty values
    return {k: v if v else "N/A" for k, v in properties.items()}


def get_android_info():
    """Get Android version and build information."""
    print_status("Collecting Android information...", "info")
    
    info = {
        "android_version": getprop("ro.build.version.release"),
        "sdk_version": getprop("ro.build.version.sdk"),
        "build_id": getprop("ro.build.id"),
        "build_display": getprop("ro.build.display.id"),
        "build_type": getprop("ro.build.type"),
        "build_tags": getprop("ro.build.tags"),
        "build_date": getprop("ro.build.date"),
        "security_patch": getprop("ro.build.version.security_patch"),
        "incremental": getprop("ro.build.version.incremental"),
        "codename": getprop("ro.build.version.codename"),
        "locale": getprop("ro.product.locale")
    }
    
    return {k: v if v else "N/A" for k, v in info.items()}


def get_battery_info():
    """Get battery status using Termux API."""
    print_status("Collecting battery information...", "info")
    
    battery = run_json_command("termux-battery-status")
    
    if battery:
        temp = battery.get("temperature", 0)
        return {
            "percentage": f"{battery.get('percentage', 'N/A')}%",
            "status": battery.get("status", "N/A"),
            "health": battery.get("health", "N/A"),
            "plugged": battery.get("plugged", "N/A"),
            "temperature": f"{temp}°C" if temp else "N/A",
            "current": f"{battery.get('current', 'N/A')} mA"
        }
    
    return {"error": "Unable to get battery info. Is Termux:API installed?"}


def get_cpu_info():
    """Get CPU information from /proc/cpuinfo."""
    print_status("Collecting CPU information...", "info")
    
    cpu_info = {"cores": 0, "processors": []}
    
    try:
        with open("/proc/cpuinfo", "r") as f:
            content = f.read()
        
        lines = content.split("\n")
        current_proc = {}
        processor_count = 0
        
        for line in lines:
            if not line.strip():
                if current_proc:
                    cpu_info["processors"].append(current_proc)
                    current_proc = {}
                continue
            
            try:
                key, value = line.split(":", 1)
                key = key.strip()
                value = value.strip()
                
                if key == "processor":
                    processor_count += 1
                    current_proc["id"] = value
                else:
                    current_proc[key.lower().replace(" ", "_")] = value
            except ValueError:
                pass
        
        if current_proc:
            cpu_info["processors"].append(current_proc)
        
        cpu_info["cores"] = processor_count
        
        # Extract common info from first processor
        if cpu_info["processors"]:
            first = cpu_info["processors"][0]
            cpu_info["hardware"] = first.get("hardware", "Unknown")
            cpu_info["model_name"] = first.get("model_name", "Unknown")
            cpu_info["features"] = first.get("features", "N/A")
            cpu_info["cpu_implementer"] = first.get("cpu_implementer", "N/A")
            cpu_info["cpu_architecture"] = first.get("cpu_architecture", "N/A")
            cpu_info["cpu_variant"] = first.get("cpu_variant", "N/A")
            cpu_info["cpu_part"] = first.get("cpu_part", "N/A")
        
        # Remove detailed processor list for summary
        cpu_info["core_summary"] = f"{processor_count} cores detected"
        del cpu_info["processors"]
        
    except FileNotFoundError:
        cpu_info["error"] = "/proc/cpuinfo not found"
    except Exception as e:
        cpu_info["error"] = str(e)
    
    return cpu_info


def get_memory_info():
    """Get memory information from /proc/meminfo."""
    print_status("Collecting memory information...", "info")
    
    memory = {}
    
    try:
        with open("/proc/meminfo", "r") as f:
            content = f.read()
        
        def get_mem_value(key):
            match = re.search(rf"{key}:\s+(\d+)", content)
            return int(match.group(1)) if match else 0
        
        mem_total = get_mem_value("MemTotal")
        mem_free = get_mem_value("MemFree")
        mem_available = get_mem_value("MemAvailable")
        buffers = get_mem_value("Buffers")
        cached = get_mem_value("Cached")
        swap_total = get_mem_value("SwapTotal")
        swap_free = get_mem_value("SwapFree")
        active = get_mem_value("Active")
        inactive = get_mem_value("Inactive")
        
        used_ram = mem_total - mem_available
        
        memory = {
            "total_ram": format_size_kb(mem_total),
            "free_ram": format_size_kb(mem_free),
            "available_ram": format_size_kb(mem_available),
            "used_ram": format_size_kb(used_ram),
            "ram_usage_percent": f"{(used_ram / mem_total) * 100:.1f}%" if mem_total > 0 else "N/A",
            "buffers": format_size_kb(buffers),
            "cached": format_size_kb(cached),
            "total_swap": format_size_kb(swap_total),
            "free_swap": format_size_kb(swap_free),
            "used_swap": format_size_kb(swap_total - swap_free),
            "active": format_size_kb(active),
            "inactive": format_size_kb(inactive),
            "total_ram_kb": mem_total,
            "total_ram_gb": f"{mem_total / (1024 * 1024):.2f} GB"
        }
        
    except FileNotFoundError:
        memory["error"] = "/proc/meminfo not found"
    except Exception as e:
        memory["error"] = str(e)
    
    return memory


def get_storage_info():
    """Get storage information using df command."""
    print_status("Collecting storage information...", "info")
    
    storage = {"partitions": [], "total_storage": "N/A", "total_used": "N/A"}
    
    try:
        output = run_command("df -h")
        lines = output.split("\n")[1:]  # Skip header
        
        total_size = 0
        total_used = 0
        
        for line in lines:
            if not line.strip():
                continue
            
            parts = line.split()
            if len(parts) >= 6:
                # Parse size values
                size_str = parts[1]
                used_str = parts[2]
                
                def parse_size(s):
                    s = s.upper()
                    if 'G' in s:
                        return float(s.replace('G', ''))
                    elif 'M' in s:
                        return float(s.replace('M', '')) / 1024
                    elif 'K' in s:
                        return float(s.replace('K', '')) / (1024 * 1024)
                    return 0
                
                partition = {
                    "filesystem": parts[0],
                    "size": parts[1],
                    "used": parts[2],
                    "available": parts[3],
                    "use_percent": parts[4],
                    "mounted_on": parts[5]
                }
                
                storage["partitions"].append(partition)
                
                # Calculate totals for main storage
                if parts[5] in ["/", "/storage/emulated/0", "/sdcard", "/data"]:
                    total_size += parse_size(size_str)
                    total_used += parse_size(used_str)
        
        if total_size > 0:
            storage["total_storage"] = f"{total_size:.1f} GB"
            storage["total_used"] = f"{total_used:.1f} GB ({(total_used/total_size)*100:.1f}%)"
        
    except Exception as e:
        storage["error"] = str(e)
    
    return storage


def get_network_info():
    """Get network and WiFi information."""
    print_status("Collecting network information...", "info")
    
    network = {"wifi": {}, "ip_addresses": {}, "interfaces": []}
    
    # WiFi info from Termux API
    wifi = run_json_command("termux-wifi-connectioninfo")
    if wifi:
        network["wifi"] = {
            "ssid": wifi.get("ssid", "N/A"),
            "bssid": wifi.get("bssid", "N/A"),
            "ip": wifi.get("ip", "N/A"),
            "frequency": f"{wifi.get('frequency_mhz', 0)} MHz",
            "link_speed": f"{wifi.get('link_speed_mbps', 0)} Mbps",
            "rssi": f"{wifi.get('rssi', 0)} dBm",
            "mac_address": wifi.get("mac_address", "N/A"),
            "network_id": wifi.get("network_id", "N/A"),
            "signal_strength": "Excellent" if wifi.get('rssi', -100) > -50 else 
                              "Good" if wifi.get('rssi', -100) > -60 else
                              "Fair" if wifi.get('rssi', -100) > -70 else "Weak"
        }
    else:
        network["wifi"] = {"error": "Not connected to WiFi or Termux:API unavailable"}
    
    # Local IP addresses
    local_ip = run_command("ip route | awk '/src/ {print $7}' | head -1")
    network["ip_addresses"]["local"] = local_ip if local_ip else "N/A"
    
    # Public IP (with timeout)
    print_status("Fetching public IP address...", "info")
    public_ip = run_command("curl -s --connect-timeout 5 ifconfig.me 2>/dev/null", timeout=8)
    network["ip_addresses"]["public"] = public_ip if public_ip and not public_ip.startswith("Error") else "N/A"
    
    # Network interfaces
    interfaces_output = run_command("ip link show")
    interfaces = []
    for line in interfaces_output.split("\n"):
        if ": " in line:
            iface = line.split(": ")[1].split("@")[0]
            if iface != "lo" and iface not in interfaces:
                interfaces.append(iface)
    network["interfaces"] = interfaces
    
    # DNS servers
    try:
        with open("/proc/net/route", "r") as f:
            routes = f.read()
        network["has_default_route"] = "wlan0" in routes or "rmnet" in routes
    except:
        network["has_default_route"] = "Unknown"
    
    return network


def get_telephony_info():
    """Get telephony information using Termux API."""
    print_status("Collecting telephony information...", "info")
    
    telephony = run_json_command("termux-telephony-deviceinfo")
    
    if telephony:
        return {
            "phone_type": telephony.get("phone_type", "N/A"),
            "network_operator": telephony.get("network_operator_name", "N/A"),
            "network_type": telephony.get("network_type", "N/A"),
            "network_country": telephony.get("network_country", "N/A"),
            "sim_operator": telephony.get("sim_operator_name", "N/A"),
            "sim_country": telephony.get("sim_country", "N/A"),
            "sim_state": telephony.get("sim_state", "N/A"),
            "phone_count": telephony.get("phone_count", "N/A"),
            "network_mcc_mnc": telephony.get("network_operator", "N/A"),
            "sim_mcc_mnc": telephony.get("sim_operator", "N/A")
        }
    
    return {"error": "Unable to get telephony info. Check Termux:API and permissions."}


def get_kernel_info():
    """Get kernel information."""
    print_status("Collecting kernel information...", "info")
    
    kernel = {}
    
    try:
        with open("/proc/version", "r") as f:
            version = f.read().strip()
        
        kernel["version"] = version
        kernel["release"] = platform.release()
        kernel["system"] = platform.system()
        kernel["node"] = platform.node()
        kernel["machine"] = platform.machine()
        kernel["processor"] = platform.processor()
        
        # Parse kernel version
        parts = version.split()
        for part in parts:
            if part.startswith("Linux"):
                kernel["linux_version"] = parts[parts.index(part) + 1] if parts.index(part) + 1 < len(parts) else "N/A"
                break
        
    except FileNotFoundError:
        kernel["error"] = "/proc/version not found"
    except Exception as e:
        kernel["error"] = str(e)
    
    return kernel


def get_installed_apps():
    """Get list of installed packages."""
    print_status("Collecting installed apps...", "info")
    
    apps = {"total": 0, "third_party": [], "system_count": 0}
    
    try:
        # Third-party apps
        output = run_command("pm list packages -3")
        third_party = []
        for line in output.split("\n"):
            if line.startswith("package:"):
                pkg = line.replace("package:", "").strip()
                third_party.append(pkg)
        
        apps["third_party"] = third_party[:100]  # Limit for readability
        apps["total_third_party"] = len(third_party)
        
        # All packages count
        all_output = run_command("pm list packages")
        all_count = len([l for l in all_output.split("\n") if l.startswith("package:")])
        apps["total"] = all_count
        apps["system_count"] = all_count - len(third_party)
        
        if len(third_party) > 100:
            apps["note"] = f"Showing first 100 of {len(third_party)} third-party apps"
        
    except Exception as e:
        apps["error"] = str(e)
    
    return apps


def get_termux_info():
    """Get Termux-specific information."""
    print_status("Collecting Termux information...", "info")
    
    termux = {}
    
    termux["version"] = os.environ.get("TERMUX_VERSION", "N/A")
    termux["prefix"] = os.environ.get("PREFIX", "N/A")
    termux["home"] = os.environ.get("HOME", "N/A")
    termux["path"] = os.environ.get("PATH", "N/A")
    termux["shell"] = os.environ.get("SHELL", "N/A")
    termux["user"] = os.environ.get("USER", "N/A")
    termux["term"] = os.environ.get("TERM", "N/A")
    termux["lang"] = os.environ.get("LANG", "N/A")
    
    # Package count
    pkg_list = run_command("pkg list-installed 2>/dev/null | wc -l")
    termux["installed_packages"] = pkg_list.strip() if pkg_list else "0"
    
    # Termux uptime
    try:
        with open("/proc/uptime", "r") as f:
            uptime = float(f.read().split()[0])
            hours = int(uptime // 3600)
            minutes = int((uptime % 3600) // 60)
            termux["system_uptime"] = f"{hours}h {minutes}m"
    except:
        termux["system_uptime"] = "N/A"
    
    return termux


# ============================================================================
# OUTPUT FORMATTERS
# ============================================================================

def format_text_output(data):
    """Format data as readable text."""
    output = []
    
    # Header
    output.append("")
    output.append("=" * 70)
    output.append("              📱 PHONE INFO EXTRACTOR - DEVICE REPORT")
    output.append("=" * 70)
    output.append(f"    Generated: {data['timestamp']}")
    output.append(f"    Version: {VERSION} by {AUTHOR}")
    output.append("")
    
    # Device Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  📟 DEVICE INFORMATION" + " " * 44 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["device"].items():
        label = key.replace("_", " ").title()
        output.append(f"│  {label:<25}: {str(value):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Android Version
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  🤖 ANDROID VERSION" + " " * 48 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["android"].items():
        label = key.replace("_", " ").title()
        output.append(f"│  {label:<25}: {str(value):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Battery Status
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  🔋 BATTERY STATUS" + " " * 49 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["battery"].items():
        label = key.replace("_", " ").title()
        output.append(f"│  {label:<25}: {str(value):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # CPU Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  💻 CPU INFORMATION" + " " * 48 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["cpu"].items():
        label = key.replace("_", " ").title()
        output.append(f"│  {label:<25}: {str(value):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Memory Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  🧠 MEMORY INFORMATION" + " " * 45 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["memory"].items():
        if key.endswith("_kb") or key.endswith("_gb"):
            continue  # Skip raw values
        label = key.replace("_", " ").title()
        output.append(f"│  {label:<25}: {str(value):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Storage Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  💾 STORAGE INFORMATION" + " " * 44 + "│")
    output.append("├" + "─" * 68 + "┤")
    output.append(f"│  {'Total Storage':<25}: {str(data['storage'].get('total_storage', 'N/A')):<39}│")
    output.append(f"│  {'Total Used':<25}: {str(data['storage'].get('total_used', 'N/A')):<39}│")
    output.append("├" + "─" * 68 + "┤")
    output.append("│  Partitions:" + " " * 55 + "│")
    for partition in data["storage"].get("partitions", [])[:8]:
        mount = partition['mounted_on'][:30]
        output.append(f"│    {mount:<32}: {partition['size']:>6} ({partition['use_percent']})   │")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Network Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  🌐 NETWORK INFORMATION" + " " * 44 + "│")
    output.append("├" + "─" * 68 + "┤")
    if "ssid" in data["network"]["wifi"]:
        output.append("│  WiFi Connected:" + " " * 51 + "│")
        for key, value in data["network"]["wifi"].items():
            label = key.replace("_", " ").title()
            output.append(f"│    {label:<23}: {str(value):<39}│")
    else:
        output.append(f"│  WiFi: {str(data['network']['wifi'].get('error', 'N/A')):<60}│")
    output.append("├" + "─" * 68 + "┤")
    output.append(f"│  {'Local IP':<25}: {str(data['network']['ip_addresses'].get('local', 'N/A')):<39}│")
    output.append(f"│  {'Public IP':<25}: {str(data['network']['ip_addresses'].get('public', 'N/A')):<39}│")
    output.append(f"│  {'Interfaces':<25}: {', '.join(data['network']['interfaces'][:5]):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Telephony Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  📞 TELEPHONY INFORMATION" + " " * 42 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["telephony"].items():
        label = key.replace("_", " ").title()
        output.append(f"│  {label:<25}: {str(value):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Kernel Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  🐧 KERNEL INFORMATION" + " " * 45 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["kernel"].items():
        if key == "version":
            continue  # Skip full version string
        label = key.replace("_", " ").title()
        output.append(f"│  {label:<25}: {str(value):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Termux Information
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  📲 TERMUX INFORMATION" + " " * 46 + "│")
    output.append("├" + "─" * 68 + "┤")
    for key, value in data["termux"].items():
        label = key.replace("_", " ").title()
        value_str = str(value)
        if len(value_str) > 37:
            value_str = value_str[:34] + "..."
        output.append(f"│  {label:<25}: {value_str:<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Installed Apps Summary
    output.append("┌" + "─" * 68 + "┐")
    output.append("│  📦 INSTALLED APPS SUMMARY" + " " * 41 + "│")
    output.append("├" + "─" * 68 + "┤")
    output.append(f"│  {'Total Packages':<25}: {str(data['apps']['total']):<39}│")
    output.append(f"│  {'Third-Party Apps':<25}: {str(data['apps'].get('total_third_party', 'N/A')):<39}│")
    output.append(f"│  {'System Apps':<25}: {str(data['apps'].get('system_count', 'N/A')):<39}│")
    output.append("└" + "─" * 68 + "┘")
    output.append("")
    
    # Footer
    output.append("=" * 70)
    output.append("           Report Generated by Phone Info Extractor")
    output.append(f"                    v{VERSION} by {AUTHOR}")
    output.append("=" * 70)
    
    return "\n".join(output)


def format_json_output(data):
    """Format data as JSON."""
    return json.dumps(data, indent=2, default=str, ensure_ascii=False)


def format_html_output(data):
    """Format data as HTML report."""
    html = []
    
    html.append("<!DOCTYPE html>")
    html.append("<html lang='en'>")
    html.append("<head>")
    html.append("    <meta charset='UTF-8'>")
    html.append("    <meta name='viewport' content='width=device-width, initial-scale=1.0'>")
    html.append("    <title>Phone Info Report</title>")
    html.append("    <style>")
    html.append("        * { margin: 0; padding: 0; box-sizing: border-box; }")
    html.append("        body { font-family: 'Segoe UI', Tahoma, sans-serif; background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%); color: #eee; min-height: 100vh; padding: 20px; }")
    html.append("        .container { max-width: 900px; margin: 0 auto; }")
    html.append("        .header { text-align: center; padding: 30px 20px; background: linear-gradient(135deg, #0f3460 0%, #16213e 100%); border-radius: 15px; margin-bottom: 20px; box-shadow: 0 10px 40px rgba(0,0,0,0.3); }")
    html.append("        .header h1 { color: #00ff88; font-size: 2em; margin-bottom: 10px; text-shadow: 0 0 20px rgba(0,255,136,0.3); }")
    html.append("        .header .subtitle { color: #888; font-size: 0.9em; }")
    html.append("        .timestamp { color: #00ff88; font-size: 0.85em; margin-top: 15px; }")
    html.append("        .section { background: #16213e; margin: 15px 0; padding: 25px; border-radius: 12px; box-shadow: 0 5px 25px rgba(0,0,0,0.2); border-left: 4px solid #00ff88; }")
    html.append("        .section h2 { color: #00ff88; border-bottom: 2px solid #0f3460; padding-bottom: 12px; margin-bottom: 20px; font-size: 1.3em; display: flex; align-items: center; gap: 10px; }")
    html.append("        .info-row { display: flex; padding: 10px 0; border-bottom: 1px solid #0f3460; transition: background 0.2s; }")
    html.append("        .info-row:hover { background: rgba(0,255,136,0.05); padding-left: 10px; }")
    html.append("        .info-label { flex: 1; color: #888; font-size: 0.9em; }")
    html.append("        .info-value { flex: 2; color: #fff; font-weight: 500; word-break: break-word; }")
    html.append("        .error { color: #ff6b6b; }")
    html.append("        .partition { background: #0f3460; padding: 10px; margin: 5px 0; border-radius: 8px; }")
    html.append("        .footer { text-align: center; padding: 30px; color: #666; font-size: 0.85em; }")
    html.append("        .footer a { color: #00ff88; text-decoration: none; }")
    html.append("        .emoji { font-size: 1.2em; }")
    html.append("        @media (max-width: 600px) { .info-row { flex-direction: column; } .info-label { margin-bottom: 5px; } }")
    html.append("    </style>")
    html.append("</head>")
    html.append("<body>")
    html.append("    <div class='container'>")
    
    # Header
    html.append("        <div class='header'>")
    html.append("            <h1><span class='emoji'>📱</span> Phone Info Report</h1>")
    html.append("            <div class='subtitle'>Complete Device Information Extractor</div>")
    html.append(f"            <div class='timestamp'>Generated: {data['timestamp']}</div>")
    html.append("        </div>")
    
    # Helper function for sections
    def add_section(title, emoji, info_dict, exclude_keys=None):
        exclude_keys = exclude_keys or []
        html.append(f"        <div class='section'>")
        html.append(f"            <h2><span class='emoji'>{emoji}</span> {title}</h2>")
        for key, value in info_dict.items():
            if key in exclude_keys:
                continue
            if key == "error":
                html.append(f"            <div class='info-row'>")
                html.append(f"                <span class='info-label'>Status</span>")
                html.append(f"                <span class='info-value error'>{value}</span>")
                html.append("            </div>")
            else:
                label = key.replace("_", " ").title()
                html.append(f"            <div class='info-row'>")
                html.append(f"                <span class='info-label'>{label}</span>")
                html.append(f"                <span class='info-value'>{value}</span>")
                html.append("            </div>")
        html.append("        </div>")
    
    # Sections
    add_section("Device Information", "📟", data["device"])
    add_section("Android Version", "🤖", data["android"])
    add_section("Battery Status", "🔋", data["battery"])
    add_section("CPU Information", "💻", data["cpu"])
    add_section("Memory Information", "🧠", data["memory"], ["total_ram_kb", "total_ram_gb"])
    
    # Storage Section
    html.append("        <div class='section'>")
    html.append("            <h2><span class='emoji'>💾</span> Storage Information</h2>")
    html.append(f"            <div class='info-row'><span class='info-label'>Total Storage</span><span class='info-value'>{data['storage'].get('total_storage', 'N/A')}</span></div>")
    html.append(f"            <div class='info-row'><span class='info-label'>Total Used</span><span class='info-value'>{data['storage'].get('total_used', 'N/A')}</span></div>")
    html.append("            <h3 style='margin-top: 20px; color: #00ff88; font-size: 1em;'>Partitions</h3>")
    for partition in data["storage"].get("partitions", [])[:10]:
        html.append(f"            <div class='partition'>")
        html.append(f"                <strong>{partition['mounted_on']}</strong>: {partition['size']} ({partition['use_percent']} used)")
        html.append("            </div>")
    html.append("        </div>")
    
    # Network Section
    html.append("        <div class='section'>")
    html.append("            <h2><span class='emoji'>🌐</span> Network Information</h2>")
    if "ssid" in data["network"]["wifi"]:
        html.append("            <h3 style='color: #00ff88; margin-bottom: 10px;'>WiFi</h3>")
        for key, value in data["network"]["wifi"].items():
            label = key.replace("_", " ").title()
            html.append(f"            <div class='info-row'><span class='info-label'>{label}</span><span class='info-value'>{value}</span></div>")
    html.append("            <h3 style='color: #00ff88; margin: 15px 0 10px;'>IP Addresses</h3>")
    html.append(f"            <div class='info-row'><span class='info-label'>Local IP</span><span class='info-value'>{data['network']['ip_addresses'].get('local', 'N/A')}</span></div>")
    html.append(f"            <div class='info-row'><span class='info-label'>Public IP</span><span class='info-value'>{data['network']['ip_addresses'].get('public', 'N/A')}</span></div>")
    html.append("        </div>")
    
    add_section("Telephony Information", "📞", data["telephony"])
    add_section("Kernel Information", "🐧", data["kernel"], ["version"])
    add_section("Termux Information", "📲", data["termux"])
    
    # Apps Summary
    html.append("        <div class='section'>")
    html.append("            <h2><span class='emoji'>📦</span> Installed Apps Summary</h2>")
    html.append(f"            <div class='info-row'><span class='info-label'>Total Packages</span><span class='info-value'>{data['apps']['total']}</span></div>")
    html.append(f"            <div class='info-row'><span class='info-label'>Third-Party Apps</span><span class='info-value'>{data['apps'].get('total_third_party', 'N/A')}</span></div>")
    html.append(f"            <div class='info-row'><span class='info-label'>System Apps</span><span class='info-value'>{data['apps'].get('system_count', 'N/A')}</span></div>")
    html.append("        </div>")
    
    # Footer
    html.append("        <div class='footer'>")
    html.append(f"            <p>Generated by <a href='#'>Phone Info Extractor</a> v{VERSION}</p>")
    html.append(f"            <p>Created by {AUTHOR}</p>")
    html.append("        </div>")
    
    html.append("    </div>")
    html.append("</body>")
    html.append("</html>")
    
    return "\n".join(html)


# ============================================================================
# MAIN FUNCTIONS
# ============================================================================

def collect_all_info():
    """Collect all device information."""
    print(f"{Fore.CYAN}{'='*60}{Style.RESET_ALL}")
    print(f"{Fore.CYAN}  Phone Info Extractor v{VERSION}{Style.RESET_ALL}")
    print(f"{Fore.CYAN}  by {AUTHOR}{Style.RESET_ALL}")
    print(f"{Fore.CYAN}{'='*60}{Style.RESET_ALL}")
    print()
    
    data = {
        "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
        "version": VERSION,
        "device": get_device_info(),
        "android": get_android_info(),
        "battery": get_battery_info(),
        "cpu": get_cpu_info(),
        "memory": get_memory_info(),
        "storage": get_storage_info(),
        "network": get_network_info(),
        "telephony": get_telephony_info(),
        "kernel": get_kernel_info(),
        "apps": get_installed_apps(),
        "termux": get_termux_info()
    }
    
    print()
    print_status("Information collection complete!", "success")
    print()
    
    return data


def save_reports(data, output_dir, formats=None):
    """Save reports to files."""
    formats = formats or ["json", "html", "text"]
    
    # Expand output directory
    output_dir = os.path.expanduser(output_dir)
    
    # Create directory if not exists
    os.makedirs(output_dir, exist_ok=True)
    
    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
    saved_files = []
    
    if "json" in formats:
        json_file = os.path.join(output_dir, f"phone_info_{timestamp}.json")
        with open(json_file, "w", encoding="utf-8") as f:
            f.write(format_json_output(data))
        saved_files.append(("JSON", json_file))
        print_status(f"JSON report saved: {json_file}", "success")
    
    if "html" in formats:
        html_file = os.path.join(output_dir, f"phone_info_{timestamp}.html")
        with open(html_file, "w", encoding="utf-8") as f:
            f.write(format_html_output(data))
        saved_files.append(("HTML", html_file))
        print_status(f"HTML report saved: {html_file}", "success")
    
    if "text" in formats:
        text_file = os.path.join(output_dir, f"phone_info_{timestamp}.txt")
        with open(text_file, "w", encoding="utf-8") as f:
            f.write(format_text_output(data))
        saved_files.append(("Text", text_file))
        print_status(f"Text report saved: {text_file}", "success")
    
    return saved_files


def main():
    """Main entry point."""
    parser = argparse.ArgumentParser(
        description="Phone Info Extractor - Extract complete device information",
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog="""
Examples:
    python phone_info_extractor.py              # Full output (all formats)
    python phone_info_extractor.py --json       # JSON only
    python phone_info_extractor.py --html       # HTML only  
    python phone_info_extractor.py --text       # Text only
    python phone_info_extractor.py --quiet      # No terminal output
    python phone_info_extractor.py -o ~/reports # Custom output directory
        """
    )
    
    parser.add_argument("--json", action="store_true", help="Output as JSON")
    parser.add_argument("--html", action="store_true", help="Output as HTML")
    parser.add_argument("--text", action="store_true", help="Output as Text")
    parser.add_argument("--all", action="store_true", help="Output all formats (default)")
    parser.add_argument("--quiet", "-q", action="store_true", help="Suppress terminal output")
    parser.add_argument("--output", "-o", default=DEFAULT_OUTPUT_DIR, help="Output directory")
    parser.add_argument("--no-save", action="store_true", help="Don't save files")
    parser.add_argument("--version", "-v", action="version", version=f"Phone Info Extractor v{VERSION}")
    
    args = parser.parse_args()
    
    # Determine output formats
    if args.json or args.html or args.text:
        formats = []
        if args.json:
            formats.append("json")
        if args.html:
            formats.append("html")
        if args.text:
            formats.append("text")
    else:
        formats = ["json", "html", "text"]
    
    # Collect information
    data = collect_all_info()
    
    # Display output
    if not args.quiet:
        print(format_text_output(data))
    
    # Save files
    if not args.no_save:
        print()
        print_status(f"Saving reports to: {args.output}", "info")
        save_reports(data, args.output, formats)
        print()
        print_status(f"All reports saved!", "success")
    
    return 0


if __name__ == "__main__":
    sys.exit(main())
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic Setup and Run

```bash
# Task: Set up and run Phone Info Extractor

# Step 1: Ensure Termux:API is installed
pkg install termux-api -y

# Step 2: Install Python and colorama
pkg install python -y
pip install colorama

# Step 3: Create project directory
mkdir -p ~/projects/phone-info
cd ~/projects/phone-info

# Step 4: Create the script (copy the source code above)
nano phone_info_extractor.py
# Paste the complete source code
# Ctrl+O to save, Ctrl+X to exit

# Step 5: Make executable
chmod +x phone_info_extractor.py

# Step 6: Run the tool
python phone_info_extractor.py

# Step 7: Check generated files
ls ~/storage/downloads/phone_info/

# Expected: JSON, HTML, and TXT files with timestamps
```

### Exercise 2: Output Format Options

```bash
# Task: Use different output format options

# Step 1: JSON only output
python phone_info_extractor.py --json

# Step 2: HTML only output
python phone_info_extractor.py --html

# Step 3: Text only output
python phone_info_extractor.py --text

# Step 4: All formats (default)
python phone_info_extractor.py --all

# Step 5: Quiet mode (no terminal output)
python phone_info_extractor.py --quiet

# Step 6: Custom output directory
python phone_info_extractor.py -o ~/my_reports

# Step 7: No file saving
python phone_info_extractor.py --no-save

# Step 8: Check version
python phone_info_extractor.py --version
```

### Exercise 3: Analyzing the Output

```bash
# Task: Analyze and understand the collected data

# Step 1: View JSON output
cd ~/storage/downloads/phone_info
cat phone_info_*.json | python -m json.tool | head -50

# Step 2: Extract specific information from JSON
cat phone_info_*.json | python -c "
import json, sys
data = json.load(sys.stdin)
print(f\"Device: {data['device']['manufacturer']} {data['device']['model']}\")
print(f\"Android: {data['android']['android_version']}\")
print(f\"Battery: {data['battery']['percentage']}\")
print(f\"RAM: {data['memory']['total_ram']}\")
"

# Step 3: Open HTML report in browser
# Copy the HTML file to a location accessible by browser
cp phone_info_*.html ~/storage/downloads/
# Open from file manager or browser

# Step 4: Compare with system commands
# Compare collected info with direct commands
getprop ro.product.model
getprop ro.build.version.release
cat /proc/meminfo | head -5
```

### Exercise 4: Extending the Tool

```python
# Task: Add a new information collector

# Step 1: Create extended version
cat > phone_info_extended.py << 'EOF'
#!/usr/bin/env python3
"""Extended Phone Info Extractor with additional collectors"""

import subprocess

def get_sensor_info():
    """Get available sensors"""
    try:
        output = subprocess.run(
            "termux-sensor -s all -l 2>/dev/null || echo 'Sensors unavailable'",
            shell=True, capture_output=True, text=True, timeout=5
        )
        return {"available": output.stdout.strip()}
    except:
        return {"error": "Sensor info requires Termux:API"}

def get_location_info():
    """Get last known location"""
    try:
        output = subprocess.run(
            "termux-location --last-known 2>/dev/null || echo 'Location unavailable'",
            shell=True, capture_output=True, text=True, timeout=10
        )
        return {"last_known": output.stdout.strip()[:200]}  # Truncate
    except:
        return {"error": "Location info requires GPS permission"}

# Add these to the main data collection
print("Sensors:", get_sensor_info())
print("Location:", get_location_info())
EOF

# Step 2: Run extended version
python phone_info_extended.py
```

### Exercise 5: Custom Report Generator

```bash
# Task: Create a custom report generator

# Step 1: Create custom report script
cat > custom_report.py << 'EOF'
#!/usr/bin/env python3
"""Generate custom report from collected data"""
import json
import sys
from datetime import datetime

def load_data(json_file):
    with open(json_file, 'r') as f:
        return json.load(f)

def generate_summary(data):
    """Generate a concise summary"""
    summary = []
    summary.append("=" * 50)
    summary.append("DEVICE QUICK SUMMARY")
    summary.append("=" * 50)
    summary.append(f"Device: {data['device']['manufacturer']} {data['device']['model']}")
    summary.append(f"Android: {data['android']['android_version']} (SDK {data['android']['sdk_version']})")
    summary.append(f"Security Patch: {data['android']['security_patch']}")
    summary.append("")
    summary.append(f"CPU: {data['cpu'].get('cores', 'N/A')} cores ({data['cpu'].get('hardware', 'Unknown')})")
    summary.append(f"RAM: {data['memory'].get('total_ram', 'N/A')} ({data['memory'].get('ram_usage_percent', 'N/A')} used)")
    summary.append("")
    summary.append(f"Battery: {data['battery'].get('percentage', 'N/A')} ({data['battery'].get('status', 'N/A')})")
    
    if 'ssid' in data['network']['wifi']:
        summary.append(f"WiFi: {data['network']['wifi']['ssid']} ({data['network']['wifi']['signal_strength']})")
    
    summary.append("")
    summary.append(f"Local IP: {data['network']['ip_addresses'].get('local', 'N/A')}")
    summary.append(f"Public IP: {data['network']['ip_addresses'].get('public', 'N/A')}")
    summary.append("")
    summary.append(f"Installed Apps: {data['apps']['total']} total, {data['apps'].get('total_third_party', 'N/A')} third-party")
    summary.append("=" * 50)
    
    return "\n".join(summary)

def generate_comparison_report(old_data, new_data):
    """Compare two data sets"""
    changes = []
    changes.append("CHANGES DETECTED:")
    changes.append("-" * 40)
    
    # Battery change
    old_batt = old_data['battery'].get('percentage', '0%')
    new_batt = new_data['battery'].get('percentage', '0%')
    if old_batt != new_batt:
        changes.append(f"Battery: {old_batt} -> {new_batt}")
    
    # WiFi change
    old_wifi = old_data['network']['wifi'].get('ssid', 'None')
    new_wifi = new_data['network']['wifi'].get('ssid', 'None')
    if old_wifi != new_wifi:
        changes.append(f"WiFi: {old_wifi} -> {new_wifi}")
    
    # App count change
    old_apps = old_data['apps'].get('total', 0)
    new_apps = new_data['apps'].get('total', 0)
    if old_apps != new_apps:
        diff = new_apps - old_apps
        changes.append(f"Apps: {old_apps} -> {new_apps} ({'+' if diff > 0 else ''}{diff})")
    
    return "\n".join(changes) if len(changes) > 2 else "No significant changes detected"

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print("Usage: python custom_report.py <json_file>")
        sys.exit(1)
    
    data = load_data(sys.argv[1])
    print(generate_summary(data))
    
    # If two files provided, compare them
    if len(sys.argv) >= 3:
        old_data = load_data(sys.argv[2])
        print("\n" + generate_comparison_report(data, old_data))
EOF

# Step 2: Run custom report
python custom_report.py ~/storage/downloads/phone_info/phone_info_*.json

# Step 3: Compare two reports (if you have multiple)
# First, generate a new report
python phone_info_extractor.py --quiet

# Then compare
python custom_report.py phone_info_new.json phone_info_old.json
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "termux-battery-status: command not found"

```bash
# Cause: Termux:API not installed

# Solution 1: Install termux-api package
pkg install termux-api -y

# Solution 2: Install Termux:API app from F-Droid
# Download from: https://f-droid.org/packages/com.termux.api/

# Solution 3: Verify installation
which termux-battery-status
# Should output: /data/data/com.termux/files/usr/bin/termux-battery-status

# Test API
termux-battery-status
# Should output JSON with battery info
```

### Problem 2: "Permission denied" errors

```bash
# Cause: Missing permissions

# Solution 1: Grant storage permission
termux-setup-storage
# Press "Allow" on the popup

# Solution 2: Grant location permission (for WiFi info)
# Go to: Settings → Apps → Termux → Permissions
# Enable: Location

# Solution 3: Grant phone permission (for telephony info)
# Go to: Settings → Apps → Termux → Permissions
# Enable: Phone

# Solution 4: Check if storage access works
ls ~/storage/
# Should show: dcim, downloads, music, pictures, etc.
```

### Problem 3: JSON parsing errors

```bash
# Cause: API commands not returning valid JSON

# Solution 1: Check API output directly
termux-battery-status
# If output is not JSON, Termux:API app may not be running

# Solution 2: Restart Termux
exit
# Open Termux again

# Solution 3: Reinstall Termux:API
pkg uninstall termux-api
pkg install termux-api -y

# Solution 4: Check Termux:API app is installed
pm list packages | grep termux
# Should show: package:com.termux.api
```

### Problem 4: Public IP not showing

```bash
# Cause: No internet or blocked service

# Solution 1: Check internet connection
ping -c 3 google.com

# Solution 2: Try alternative IP service
curl -s icanhazip.com
curl -s ipecho.net/plain
curl -s api.ipify.org

# Solution 3: Use VPN if service is blocked
# The script has a timeout, so it won't hang

# Solution 4: Check DNS
nslookup ifconfig.me
```

### Problem 5: WiFi info not available

```bash
# Cause: Not connected to WiFi or permission issue

# Solution 1: Ensure WiFi is connected
termux-wifi-connectioninfo

# Solution 2: Grant location permission
# WiFi info requires location permission on Android
# Settings → Apps → Termux → Permissions → Location

# Solution 3: Check WiFi is enabled
# Settings → WiFi → Enable

# Solution 4: Some devices need location services enabled
# Settings → Location → Enable
```

### Problem 6: Script runs but saves nothing

```bash
# Cause: Storage permission or path issue

# Solution 1: Check storage permission
termux-setup-storage

# Solution 2: Create directory manually
mkdir -p ~/storage/downloads/phone_info
ls ~/storage/downloads/

# Solution 3: Use different path
python phone_info_extractor.py -o ~/

# Solution 4: Check for errors in output
python phone_info_extractor.py 2>&1 | tail -20

# Solution 5: Verify script has write permission
touch ~/storage/downloads/test.txt && rm ~/storage/downloads/test.txt && echo "OK"
```

### Problem 7: Colorama colors not showing

```bash
# Cause: Colorama not installed

# Solution 1: Install colorama
pip install colorama

# Solution 2: If pip fails, use pkg
pkg install python-colorama

# Solution 3: Script works without colorama (falls back to plain text)
# Output will just be uncolored
```

### Problem 8: Slow execution

```bash
# Cause: Public IP fetch timeout

# Solution 1: Use --quiet to skip terminal output
python phone_info_extractor.py --quiet

# Solution 2: Check if curl is slow
time curl -s ifconfig.me

# Solution 3: Use faster DNS
# Edit /etc/resolv.conf (if you have root)
# Or use VPN

# Solution 4: Script has 8 second timeout for public IP
# If your connection is slower, it will return "N/A"
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark gradient background]        │
│                                    │
│   📱 PHONE INFO EXTRACTOR          │
│   ─────────────────────────        │
│                                    │
│   ✓ Device Info                    │
│   ✓ Battery Status                 │
│   ✓ Network Details                │
│   ✓ Export to JSON/HTML            │
│                                    │
│   [Python + Termux logos]          │
│   T3rmuxk1ng | Chapter 52          │
└────────────────────────────────────┘
```

**Option B: Code Style**
```
┌────────────────────────────────────┐
│  [Terminal background with code]   │
│                                    │
│   $ python phone_info.py           │
│                                    │
│   📱 Device: Samsung Galaxy S21    │
│   🔋 Battery: 85% (Good)           │
│   📶 WiFi: MyNetwork (Excellent)   │
│   💾 Storage: 64GB Used / 128GB    │
│                                    │
│   [Complete Info Extraction]       │
│   T3rmuxk1ng                       │
└────────────────────────────────────┘
```

**Option C: Feature Highlight**
```
┌────────────────────────────────────┐
│  📱 ← 📊 ← 🐍                      │
│                                    │
│   EXTRACT COMPLETE                 │
│   PHONE INFORMATION                │
│                                    │
│   ┌──────────────────────────┐     │
│   │ JSON  HTML  TXT Export   │     │
│   └──────────────────────────┘     │
│                                    │
│   Project #2 | Termux Course       │
│   by T3rmuxk1ng                    │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📱 Termux Full Course - Chapter 52: Phone Info Extractor | Complete Device Information Tool

🔥 In this video you'll learn:
• How to extract complete device information
• Using Termux APIs for battery, WiFi, telephony
• Reading system files (cpuinfo, meminfo)
• Python subprocess for command execution
• Multiple output formats (JSON, HTML, Text)
• File export and reporting

⏱️ Timestamps:
0:00 - Introduction
1:00 - Project Overview
4:00 - Prerequisites Setup
6:00 - Device Information Methods
10:00 - Implementation Part 1
14:00 - Implementation Part 2
18:00 - Implementation Part 3
21:00 - Output Formatting
23:00 - Main Function & CLI
24:30 - Running the Tool
25:30 - Summary

📥 Commands from this video:
pkg install termux-api -y
pip install colorama
python phone_info_extractor.py

📂 Source Code:
Available in description/comments

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #PhoneInfo #Python #TermuxProject #DeviceInformation #T3rmuxk1ng #TermuxCourse #AndroidHacking #PythonScripting

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on devices you own or have permission to analyze.
```

### Tags List

```
termux, phone info extractor, device information, android device info,
termux api, python termux, termux project, device fingerprint,
battery status, wifi info, cpu info, memory info, system information,
android hacking, termux python, termux course, t3rmuxk1ng,
phone information tool, device reporter, json report, html report,
termux tutorial, android terminal, mobile hacking, security tools,
device profiling, system diagnostics, termux scripts
```

### Hashtags

```
#Termux #PhoneInfoExtractor #Python #TermuxProject #DeviceInfo
#AndroidHacking #TermuxTutorial #T3rmuxk1ng #TermuxCourse
#SecurityTools #MobileSecurity #PythonScripting #DeviceInfo
#BatteryStatus #WiFiInfo #SystemInfo #AndroidTerminal
```

---

## 📚 ADDITIONAL RESOURCES

### Related Documentation

| Resource | Link |
|----------|------|
| Termux API Wiki | https://wiki.termux.com/wiki/Termux:API |
| Android getprop | https://developer.android.com/reference/android/os/SystemProperties |
| /proc filesystem | https://man7.org/linux/man-pages/man5/proc.5.html |
| Python subprocess | https://docs.python.org/3/library/subprocess.html |

### Termux API Commands Reference

| Command | Purpose |
|---------|---------|
| `termux-battery-status` | Battery information |
| `termux-wifi-connectioninfo` | Current WiFi connection |
| `termux-wifi-scaninfo` | WiFi scan results |
| `termux-telephony-deviceinfo` | Phone/SIM info |
| `termux-telephony-cellinfo` | Cell tower info |
| `termux-location` | GPS location |
| `termux-sensor` | Sensor data |
| `termux-notification` | Create notification |
| `termux-clipboard-get` | Get clipboard |
| `termux-clipboard-set` | Set clipboard |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 53, verify:

- [ ] Termux:API app installed from F-Droid
- [ ] `pkg install termux-api` completed
- [ ] Python and colorama installed
- [ ] `termux-setup-storage` executed
- [ ] Phone Info Extractor script created and tested
- [ ] JSON, HTML, and Text reports generated successfully
- [ ] Understood how Termux APIs work
- [ ] Understood system file information sources
- [ ] Practiced with different output format options
- [ ] Can troubleshoot common issues

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 53: Project 3 - WiFi Analyzer**

- WiFi network scanning
- Signal strength analysis
- Channel optimization
- Security assessment
- Network mapping
- Interference detection

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
