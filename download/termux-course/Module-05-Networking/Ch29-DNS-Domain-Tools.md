# Chapter 29: DNS & Domain Tools

> **Module:** 5 - Networking  
> **Chapter:** 29 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | DNS fundamentals, tools, record types |
| Commands Reference | 25+ dig, nslookup, whois commands |
| Practice Exercises | Hands-on DNS enumeration tasks |
| Troubleshooting | Common DNS issues and solutions |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 29
Title: DNS & Domain Tools | Complete DNS Enumeration Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:50]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum seekhenge DNS aur Domain Tools - jo ki networking aur 
security testing ka ek bahut important part hai.

DNS - Domain Name System - Internet ka phonebook hai. Jab aap 
google.com type karte ho, DNS usko IP address mein convert karta hai.

Reconnaissance phase mein DNS enumeration sabse pehla step hota hai.
Target domain ke baare mein kitna information nikal sakte ho - 
subdomains, mail servers, nameservers, DNS records - sab kuch.

Is chapter mein hum cover karenge:
- DNS fundamentals
- dig command - advanced DNS lookup
- nslookup - classic DNS tool
- host command - simple DNS queries
- whois - domain registration info
- DNS record types - A, AAAA, MX, TXT, NS, CNAME, SOA
- Reverse DNS lookup
- Subdomain discovery
- Zone transfer attempts
- DNS troubleshooting

Play button dabaiye, video like karein, channel subscribe karein!

---

[SECTION 1: DNS FUNDAMENTALS - 0:50 to 4:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle DNS ke basics samajhte hain.

DNS kya hai? Domain Name System. Ye ek distributed database hai jo
domain names ko IP addresses mein translate karta hai.

Kyun zaroori hai? Kyunki humans ko names yaad rehte hain - google.com,
facebook.com - lekin computers IP addresses samajhte hain - 
142.250.195.78.

┌─────────────────────────────────────────────────────────────────────────┐
│                    DNS RESOLUTION PROCESS                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   USER types "google.com"                                                │
│         │                                                                │
│         ▼                                                                │
│   ┌─────────────┐    Not Cached    ┌─────────────┐                      │
│   │ LOCAL CACHE │ ───────────────▶ │ RESOLVER    │                      │
│   │ (Browser/OS)│                  │ (ISP DNS)   │                      │
│   └─────────────┘                  └─────────────┘                      │
│         │ Cached                         │                              │
│         │                                ▼                              │
│         │                         ┌─────────────┐                       │
│         │                         │ ROOT SERVER │                       │
│         │                         │ (.)         │                       │
│         │                         └─────────────┘                       │
│         │                                │                              │
│         │                                ▼                              │
│         │                         ┌─────────────┐                       │
│         │                         │ TLD SERVER  │                       │
│         │                         │ (.com)      │                       │
│         │                         └─────────────┘                       │
│         │                                │                              │
│         │                                ▼                              │
│         │                         ┌─────────────┐                       │
│         │                         │ AUTHORITATIVE                      │
│         │                         │ NAMESERVER  │                       │
│         │                         │ (google.com)│                       │
│         │                         └─────────────┘                       │
│         │                                │                              │
│         ▼                                ▼                              │
│   ┌─────────────────────────────────────────────┐                       │
│   │ IP ADDRESS: 142.250.195.78                   │                       │
│   └─────────────────────────────────────────────┘                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

DNS Hierarchy samjhein:

ROOT LEVEL (.)
├── TLD (Top Level Domains)
│   ├── .com, .org, .net (gTLD - Generic)
│   ├── .in, .uk, .us (ccTLD - Country Code)
│   └── .gov, .edu, .mil (sTLD - Sponsored)
│
└── Second Level Domains
    ├── google.com, facebook.com
    └── Third Level: mail.google.com, drive.google.com

DNS Record Types:
──────────────────────────────────────────────────────────────────────────

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON DNS RECORD TYPES                               │
├──────────┬──────────────────────────────────────────────────────────────┤
│ Record   │ Purpose                                                      │
├──────────┼──────────────────────────────────────────────────────────────┤
│ A        │ Maps domain to IPv4 address                                  │
│ AAAA     │ Maps domain to IPv6 address                                  │
│ CNAME    │ Alias - points one domain to another                         │
│ MX       │ Mail Exchange - email servers                                │
│ NS       │ Nameserver - authoritative DNS servers                       │
│ TXT      │ Text records - SPF, DKIM, verification                       │
│ SOA      │ Start of Authority - zone information                        │
│ SRV      │ Service records - specific services                          │
│ PTR      │ Reverse DNS - IP to domain                                   │
│ DMARC    │ Email authentication policy                                  │
└──────────┴──────────────────────────────────────────────────────────────┘

---

[SECTION 2: DNS TOOLS INSTALLATION - 4:00 to 5:30]
─────────────────────────────────────────────────────────────────────────────

Chaliye Termux mein DNS tools install karte hain.

[SCREEN: Termux Terminal]

# Update first
pkg update && pkg upgrade -y

# Install DNS utilities
pkg install dnsutils -y     # dig, nslookup, host
pkg install whois -y        # whois command
pkg install netcat -y       # For zone transfer tests

# Verify installation
dig -v
nslookup -version
whois --version

dnsutils package mein ye tools aate hain:
- dig - Domain Information Groper (most powerful)
- nslookup - Name Server Lookup (classic tool)
- host - Simple DNS lookup utility

---

[SECTION 3: DIG COMMAND - 5:30 to 9:00]
─────────────────────────────────────────────────────────────────────────────

DIG command - Domain Information Groper - sabse powerful DNS tool hai.

Basic syntax:
    dig <domain>

[SCREEN: Basic dig command]

dig google.com

Output explain karta hoon:

; <<>> DiG 9.16.1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12345
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;google.com.            IN  A

;; ANSWER SECTION:
google.com.     299 IN  A   142.250.195.78

;; Query time: 15 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Jan 01 12:00:00 IST 2024
;; MSG SIZE  rcvd: 55

Output sections:
- HEADER: Query status, flags
- QUESTION: What was asked
- ANSWER: The response
- AUTHORITY: Nameservers (if any)
- ADDITIONAL: Extra records

IMPORTANT: ANSWER SECTION mein jo number hai (299) - wo TTL hai.
Time To Live - cache kitna time rahega.

Specific record type query karna:

dig google.com A        # IPv4 address
dig google.com AAAA     # IPv6 address
dig google.com MX       # Mail servers
dig google.com NS       # Nameservers
dig google.com TXT      # Text records
dig google.com SOA      # Start of Authority
dig google.com CNAME    # Alias records

SHORT OUTPUT:
dig +short google.com
# Output: 142.250.195.78

SPECIFIC DNS SERVER use karna:
dig @8.8.8.8 google.com
# Using Google's DNS server

REVERSE DNS LOOKUP:
dig -x 142.250.195.78
# IP se domain name dhundhna

ALL RECORD TYPES:
dig google.com ANY
# Shows all available records

TRACE DNS PATH:
dig +trace google.com
# Shows complete resolution path from root

---

[SECTION 4: NSLOOKUP COMMAND - 9:00 to 11:30]
─────────────────────────────────────────────────────────────────────────────

NSLOOKUP - Name Server Lookup - classic DNS tool. Windows pe bhi available hai.

Interactive mode aur non-interactive mode - dono mein kaam karta hai.

Basic usage:
nslookup google.com

Output:
Server:     192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 142.250.195.78

Specific record type:
nslookup -type=MX google.com
nslookup -type=NS google.com
nslookup -type=TXT google.com
nslookup -type=SOA google.com

Specific DNS server:
nslookup google.com 8.8.8.8
# Query Google's DNS

INTERACTIVE MODE:
nslookup
> server 8.8.8.8          # Change DNS server
> set type=MX             # Set query type
> google.com              # Query domain
> set type=ANY            # All records
> facebook.com            # Query another
> exit                    # Exit interactive mode

Reverse lookup:
nslookup 142.250.195.78

DEBUG mode:
nslookup -debug google.com
# Shows detailed query information

---

[SECTION 5: HOST COMMAND - 11:30 to 13:00]
─────────────────────────────────────────────────────────────────────────────

HOST command - simplest DNS lookup tool. Clean output deta hai.

Basic usage:
host google.com
# Output: google.com has address 142.250.195.78

Specific record types:
host -t A google.com      # A record
host -t AAAA google.com   # IPv6
host -t MX google.com     # Mail servers
host -t NS google.com     # Nameservers
host -t TXT google.com    # Text records
host -t SOA google.com    # Start of Authority
host -t CNAME www.google.com

ALL records:
host -a google.com
# Verbose output with all records

Reverse lookup:
host 142.250.195.78

Specific DNS server:
host google.com 8.8.8.8

List domain records:
host -l google.com
# Zone transfer attempt (usually blocked)

---

[SECTION 6: WHOIS COMMAND - 13:00 to 15:30]
─────────────────────────────────────────────────────────────────────────────

WHOIS command - domain registration information nikalta hai.

Isse pata chalta hai:
- Domain owner (Registrar)
- Registration date
- Expiry date
- Nameservers
- Contact information (if public)

Basic usage:
whois google.com

Output mein dhyaan do:
- Registrar: GoDaddy, Namecheap, etc.
- Creation Date: Kab register hua
- Expiry Date: Kab expire hoga
- Name Servers: DNS servers
- Status: Active, locked, etc.

[SCREEN: whois output]

Domain Name: google.com
Registry Domain ID: 2138514_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.markmonitor.com
Registrar URL: http://www.markmonitor.com
Updated Date: 2019-09-09T15:39:04Z
Creation Date: 1997-09-15T04:00:00Z
Registrar Registration Expiration Date: 2028-08-14T04:00:00Z
Registrar: MarkMonitor Inc.
Registrar IANA ID: 292
Registrar Abuse Contact Email: abusecomplaints@markmonitor.com
Registrar Abuse Contact Phone: +1.2083895740
Domain Status: clientDeleteProhibited
Domain Status: clientTransferProhibited
Domain Status: clientUpdateProhibited
Name Server: NS1.GOOGLE.COM
Name Server: NS2.GOOGLE.COM

IP WHOIS:
whois 142.250.195.78
# Shows IP block owner, ISP info

Specific registrar query:
whois -h whois.google.com google.com

---

[SECTION 7: DNS RECORD TYPES DEEP DIVE - 15:30 to 18:00]
─────────────────────────────────────────────────────────────────────────────

Ab DNS record types ko detail mein samajhte hain:

A RECORD (Address Record):
┌─────────────────────────────────────────────────────────────────────────┐
│ Domain Name        │ A Record       │ Purpose                          │
├────────────────────┼────────────────┼──────────────────────────────────┤
│ example.com        │ 93.184.216.34  │ Main website IPv4 address        │
│ www.example.com    │ 93.184.216.34  │ www subdomain                    │
│ mail.example.com   │ 93.184.216.35  │ Mail server IP                   │
└────────────────────┴────────────────┴──────────────────────────────────┘

AAAA RECORD (IPv6):
example.com. IN AAAA 2606:2800:220:1:248:1893:25c8:1946

MX RECORD (Mail Exchange):
┌─────────────────────────────────────────────────────────────────────────┐
│ Priority │ Server                  │ Note                              │
├──────────┼─────────────────────────┼───────────────────────────────────┤
│ 10       │ mail.example.com        │ Lower = Higher priority           │
│ 20       │ mail2.example.com       │ Backup mail server                │
│ 30       │ mail3.example.com       │ Third backup                      │
└──────────┴─────────────────────────┴───────────────────────────────────┘

TXT RECORD:
Common uses:
- SPF (Sender Policy Framework): "v=spf1 include:_spf.google.com ~all"
- DKIM: DomainKeys Identified Mail
- Domain verification
- Site verification

NS RECORD (Nameserver):
example.com. IN NS ns1.example.com.
example.com. IN NS ns2.example.com.

CNAME (Canonical Name):
www.example.com. IN CNAME example.com.
mail.example.com. IN CNAME ghs.googlehosted.com.

SOA RECORD (Start of Authority):
┌─────────────────────────────────────────────────────────────────────────┐
│ Field        │ Value                    │ Meaning                       │
├──────────────┼──────────────────────────┼───────────────────────────────┤
│ MNAME        │ ns1.example.com          │ Primary nameserver            │
│ RNAME        │ admin.example.com        │ Admin email (@ becomes .)     │
│ SERIAL       │ 2024010101               │ Zone version number           │
│ REFRESH      │ 3600                     │ Secondary refresh interval    │
│ RETRY        │ 1800                     │ Retry interval                │
│ EXPIRE       │ 604800                   │ Expire time                   │
│ MINIMUM      │ 86400                    │ Minimum TTL                   │
└──────────────┴──────────────────────────┴───────────────────────────────┘

PTR RECORD (Reverse DNS):
34.216.184.93.in-addr.arpa. IN PTR example.com.

---

[SECTION 8: REVERSE DNS LOOKUP - 18:00 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Reverse DNS ka matlab hai IP address se domain name dhundhna.

Normal DNS: domain → IP
Reverse DNS: IP → domain

Kyun useful hai?
- Email server verification
- Security analysis
- IP reputation check
- Network troubleshooting

Methods:

DIG method:
dig -x 142.250.195.78

NSLOOKUP method:
nslookup 142.250.195.78

HOST method:
host 142.250.195.78

Multiple IPs check:
for ip in 142.250.195.78 142.250.195.79; do
    echo "Checking $ip:"
    dig +short -x $ip
done

---

[SECTION 9: SUBDOMAIN DISCOVERY - 19:30 to 21:30]
─────────────────────────────────────────────────────────────────────────────

Subdomain discovery - reconnaissance ka important part.

Manual methods:
# Common subdomains check
host www.google.com
host mail.google.com
host ftp.google.com
host admin.google.com
host api.google.com
host dev.google.com
host staging.google.com

Using bash loop:
for sub in www mail ftp admin api dev staging blog shop vpn; do
    host $sub.google.com 2>/dev/null | grep "has address"
done

Using DIG:
dig google.com +short | head -1

Automated tools (future chapters):
- Sublist3r
- Subfinder
- Amass
- Gobuster

---

[SECTION 10: DNS ZONE TRANSFER - 21:30 to 23:00]
─────────────────────────────────────────────────────────────────────────────

Zone Transfer (AXFR) - DNS ka full record dump.

Ye security misconfiguration hai agar allow ho:

Check nameservers:
dig NS google.com +short

Attempt zone transfer:
dig AXFR @ns1.google.com google.com

Using host:
host -l google.com ns1.google.com

Using nslookup:
nslookup
> server ns1.google.com
> set type=any
> ls -d google.com

Most modern servers block zone transfer, but check karna chahiye.
Misconfigured servers expose all subdomains.

---

[SECTION 11: DNS TROUBLESHOOTING - 23:00 to 25:00]
─────────────────────────────────────────────────────────────────────────────

Common DNS issues aur unka solution:

1. DOMAIN NOT RESOLVING:
   - Check DNS servers: cat /etc/resolv.conf
   - Try different DNS: dig @8.8.8.8 domain.com
   - Check if domain exists: whois domain.com

2. SLOW RESOLUTION:
   - Use faster DNS: 8.8.8.8 (Google) or 1.1.1.1 (Cloudflare)
   - Check TTL values
   - Clear DNS cache

3. WRONG IP:
   - Check A record: dig domain.com A
   - Check for CNAME chains
   - Verify with authoritative server

4. EMAIL ISSUES:
   - Check MX records: dig domain.com MX
   - Check SPF: dig domain.com TXT
   - Verify mail server IP

5. DNS PROPAGATION:
   - Check globally: dig @ns1.google.com domain.com
   - Use online tools: whatsmydns.net
   - Wait for TTL

---

[SECTION 12: DNS LOOKUP SCRIPT - 25:00 to 27:00]
─────────────────────────────────────────────────────────────────────────────

Chaliye ek useful DNS enumeration script banate hain:

[SCREEN: Script creation]

cat > dns-lookup.sh << 'EOF'
#!/bin/bash

# DNS Lookup Script by T3rmuxk1ng

RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m'

if [ -z "$1" ]; then
    echo "Usage: $0 <domain>"
    exit 1
fi

DOMAIN=$1

echo -e "${YELLOW}========================================${NC}"
echo -e "${GREEN}DNS Enumeration for: $DOMAIN${NC}"
echo -e "${YELLOW}========================================${NC}"

echo -e "\n${GREEN}[+] A Record (IPv4):${NC}"
dig +short $DOMAIN A

echo -e "\n${GREEN}[+] AAAA Record (IPv6):${NC}"
dig +short $DOMAIN AAAA

echo -e "\n${GREEN}[+] MX Record (Mail Servers):${NC}"
dig +short $DOMAIN MX

echo -e "\n${GREEN}[+] NS Record (Name Servers):${NC}"
dig +short $DOMAIN NS

echo -e "\n${GREEN}[+] TXT Record:${NC}"
dig +short $DOMAIN TXT

echo -e "\n${GREEN}[+] SOA Record:${NC}"
dig +short $DOMAIN SOA

echo -e "\n${GREEN}[+] CNAME Record:${NC}"
dig +short www.$DOMAIN CNAME

echo -e "\n${YELLOW}========================================${NC}"
echo -e "${GREEN}WHOIS Information:${NC}"
echo -e "${YELLOW}========================================${NC}"
whois $DOMAIN 2>/dev/null | grep -E "(Registrar|Creation Date|Expiry|Name Server)"

echo -e "\n${GREEN}[+] DNS Server IP:${NC}"
dig +short $DOMAIN NS | while read ns; do
    echo "$ns: $(dig +short $ns)"
done

echo -e "\n${YELLOW}========================================${NC}"
echo -e "${GREEN}Enumeration Complete!${NC}"
echo -e "${YELLOW}========================================${NC}"
EOF

chmod +x dns-lookup.sh

./dns-lookup.sh google.com

---

[SECTION 13: SUMMARY & NEXT PREVIEW - 27:00 to 29:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 29 complete! Let's summarize:

✅ DNS fundamentals - Resolution process, hierarchy
✅ dig command - Advanced DNS queries
✅ nslookup - Classic DNS tool
✅ host command - Simple DNS lookup
✅ whois - Domain registration info
✅ DNS record types - A, AAAA, MX, TXT, NS, CNAME, SOA
✅ Reverse DNS lookup - IP to domain
✅ Subdomain discovery techniques
✅ Zone transfer attempts
✅ DNS troubleshooting
✅ DNS enumeration script

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 29 - IMPORTANT COMMANDS                       │
├─────────────────────────────────────────────────────────────────────────┤
│ dig domain.com           │ Basic DNS lookup                             │
│ dig +short domain.com    │ Short output (IP only)                       │
│ dig domain.com MX        │ Mail server records                          │
│ dig @8.8.8.8 domain.com  │ Use specific DNS server                      │
│ dig -x IP                │ Reverse DNS lookup                           │
│ dig +trace domain.com    │ Trace DNS resolution path                    │
│ nslookup domain.com      │ Classic lookup                               │
│ nslookup -type=MX domain │ Specific record type                         │
│ host domain.com          │ Simple DNS lookup                            │
│ host -t MX domain.com    │ Specific record with host                    │
│ whois domain.com         │ Domain registration info                     │
│ whois IP_ADDRESS         │ IP WHOIS info                                │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 30 mein hum seekhenge:
- Security Tools Overview
- Ethical hacking methodology
- Tools available in Termux
- Lab environment setup

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 30!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. DNS Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         DNS ARCHITECTURE                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                        ┌─────────────┐                                   │
│                        │ ROOT SERVER │                                   │
│                        │     (.)     │                                   │
│                        └──────┬──────┘                                   │
│                               │                                          │
│          ┌────────────────────┼────────────────────┐                    │
│          │                    │                    │                     │
│          ▼                    ▼                    ▼                     │
│   ┌─────────────┐     ┌─────────────┐     ┌─────────────┐               │
│   │  .com TLD   │     │  .org TLD   │     │   .in TLD   │               │
│   └──────┬──────┘     └─────────────┘     └─────────────┘               │
│          │                                                               │
│          ├──────────┬──────────┬──────────┐                             │
│          ▼          ▼          ▼          ▼                              │
│   ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐               │
│   │google.com │ │yahoo.com  │ │amazon.com │ │ other.com │               │
│   └─────┬─────┘ └───────────┘ └───────────┘ └───────────┘               │
│         │                                                                │
│         ├──────────┬──────────┬──────────┐                              │
│         ▼          ▼          ▼          ▼                               │
│   ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐                   │
│   │www.google│ │mail.google│ │api.google│ │drive.google│                │
│   └──────────┘ └──────────┘ └──────────┘ └──────────┘                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. DNS Record Types in Detail

| Record | Description | Example |
|--------|-------------|---------|
| A | Maps domain to IPv4 | `example.com. IN A 93.184.216.34` |
| AAAA | Maps domain to IPv6 | `example.com. IN AAAA 2606:2800:220:1:248:1893:25c8:1946` |
| CNAME | Domain alias | `www.example.com. IN CNAME example.com.` |
| MX | Mail server | `example.com. IN MX 10 mail.example.com.` |
| NS | Nameserver | `example.com. IN NS ns1.example.com.` |
| TXT | Text records | `example.com. IN TXT "v=spf1 -all"` |
| SOA | Start of Authority | `example.com. IN SOA ns1.example.com. admin.example.com. ...` |
| SRV | Service location | `_sip._tcp.example.com. IN SRV 10 60 5060 sipserver.example.com.` |
| PTR | Reverse DNS | `34.216.184.93.in-addr.arpa. IN PTR example.com.` |
| CAA | Certificate Authority | `example.com. IN CAA 0 issue "letsencrypt.org"` |

### 3. Common DNS Ports

| Port | Protocol | Purpose |
|------|----------|---------|
| 53/UDP | DNS | Standard queries |
| 53/TCP | DNS | Zone transfers, large responses |
| 853/UDP | DoT | DNS over TLS |
| 853/TCP | DoT | DNS over TLS |
| 443/TCP | DoH | DNS over HTTPS |

### 4. DNS Server Types

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    DNS SERVER TYPES                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. RECURSIVE RESOLVER (Caching)                                        │
│     ─────────────────────────────                                       │
│     • ISP's DNS server                                                  │
│     • Google DNS (8.8.8.8)                                              │
│     • Cloudflare DNS (1.1.1.1)                                          │
│     • Handles full resolution process                                   │
│     • Caches results for TTL duration                                   │
│                                                                          │
│  2. ROOT SERVER                                                         │
│     ───────────                                                         │
│     • 13 root servers worldwide (A-M)                                   │
│     • Directs to appropriate TLD server                                 │
│     • No caching, only referrals                                        │
│                                                                          │
│  3. TLD SERVER (Top Level Domain)                                       │
│     ────────────────────────────                                        │
│     • Manages .com, .org, .net, etc.                                    │
│     • Directs to authoritative nameservers                              │
│                                                                          │
│  4. AUTHORITATIVE NAMESERVER                                            │
│     ─────────────────────────                                           │
│     • Contains actual DNS records                                       │
│     • Provides definitive answers                                       │
│     • Source of truth for domain                                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### DIG Commands

```bash
# Basic DNS lookup
dig google.com

# Short output (IP only)
dig +short google.com

# Specific record types
dig google.com A          # IPv4 address
dig google.com AAAA       # IPv6 address
dig google.com MX         # Mail servers
dig google.com NS         # Nameservers
dig google.com TXT        # Text records
dig google.com SOA        # Start of Authority
dig google.com CNAME      # Alias records
dig google.com SRV        # Service records
dig google.com ANY        # All available records

# Use specific DNS server
dig @8.8.8.8 google.com           # Google DNS
dig @1.1.1.1 google.com           # Cloudflare DNS
dig @208.67.222.222 google.com    # OpenDNS

# Reverse DNS lookup
dig -x 142.250.195.78

# Trace DNS resolution path
dig +trace google.com

# Show only answer section
dig +noall +answer google.com

# Show question and answer
dig +noall +question +answer google.com

# Check DNSSEC
dig +dnssec google.com

# Batch queries
dig google.com facebook.com twitter.com

# Read queries from file
dig -f domains.txt

# Set query timeout
dig +time=5 google.com

# Set number of retries
dig +tries=3 google.com

# Show server used
dig +identify google.com

# Get all records from specific nameserver
dig @ns1.google.com google.com ANY

# Check for wildcards (compare multiple subdomains)
dig random123.google.com
dig another456.google.com
```

### NSLOOKUP Commands

```bash
# Basic lookup
nslookup google.com

# Specific DNS server
nslookup google.com 8.8.8.8

# Specific record type
nslookup -type=A google.com
nslookup -type=AAAA google.com
nslookup -type=MX google.com
nslookup -type=NS google.com
nslookup -type=TXT google.com
nslookup -type=SOA google.com
nslookup -type=CNAME www.google.com
nslookup -type=ANY google.com

# Reverse lookup
nslookup 142.250.195.78

# Debug mode
nslookup -debug google.com

# Interactive mode
nslookup
> server 8.8.8.8
> set type=MX
> google.com
> set type=ANY
> facebook.com
> exit

# Set timeout
nslookup -timeout=10 google.com

# Set retry count
nslookup -retry=3 google.com

# Use TCP instead of UDP
nslookup -vc google.com

# Set port (non-standard)
nslookup -port=5353 google.com
```

### HOST Commands

```bash
# Basic lookup
host google.com

# Specific record type
host -t A google.com
host -t AAAA google.com
host -t MX google.com
host -t NS google.com
host -t TXT google.com
host -t SOA google.com
host -t CNAME www.google.com
host -t SRV _sip._tcp.google.com

# All records (verbose)
host -a google.com

# Reverse lookup
host 142.250.195.78

# Use specific DNS server
host google.com 8.8.8.8

# Zone transfer attempt
host -l google.com ns1.google.com

# Verbose output
host -v google.com

# IPv4 only
host -4 google.com

# IPv6 only
host -6 google.com
```

### WHOIS Commands

```bash
# Domain WHOIS
whois google.com

# IP WHOIS
whois 142.250.195.78

# Specific WHOIS server
whois -h whois.verisign-grs.com google.com

# Get registrar WHOIS server
whois -h whois.iana.org google.com

# Suppress legal disclaimers
whois -H google.com

# Use specific port
whois -p 43 google.com

# Quick lookup (minimal output)
whois google.com | grep -E "(Registrar|Creation|Expiry|Name Server)"

# Extract specific info
whois google.com | grep "Registrar:"
whois google.com | grep "Creation Date"
whois google.com | grep "Name Server"
```

### DNS Enumeration Commands

```bash
# Get all DNS records
for type in A AAAA MX NS TXT SOA CNAME; do
    echo "=== $type Records ==="
    dig +short google.com $type
done

# Enumerate common subdomains
for sub in www mail ftp admin api dev staging blog shop vpn db mysql; do
    host $sub.google.com 2>/dev/null | grep "has address" &
done
wait

# Check nameserver IPs
for ns in $(dig +short google.com NS); do
    echo "$ns: $(dig +short $ns)"
done

# Attempt zone transfer on each nameserver
for ns in $(dig +short google.com NS); do
    echo "Trying AXFR on $ns..."
    dig AXFR @$ns google.com 2>/dev/null
done

# Check all mail servers
dig +short google.com MX | while read pri server; do
    echo "$server: $(dig +short $server A)"
done

# Reverse DNS for IP range
for i in $(seq 1 10); do
    dig +short -x 142.250.195.$i
done

# DNS timing analysis
time dig google.com
time dig @8.8.8.8 google.com
time dig @1.1.1.1 google.com
```

### Network DNS Commands

```bash
# Check current DNS servers
cat /etc/resolv.conf

# Test DNS connectivity
ping -c 3 8.8.8.8

# Check DNS port
nc -zv 8.8.8.8 53

# Query DNS over TCP
dig +tcp google.com

# Check DNS response time
dig google.com | grep "Query time"

# DNS over HTTPS (if curl available)
curl -H 'accept: application/dns-json' 'https://cloudflare-dns.com/dns-query?name=google.com&type=A'

# Check SPF record
dig +short google.com TXT | grep spf

# Check DMARC
dig +short _dmarc.google.com TXT

# Check DKIM (example)
dig +short default._domainkey.google.com TXT
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic DNS Lookups

```bash
# Task: Perform basic DNS queries for multiple domains

# Step 1: Create domains list
cat > domains.txt << 'EOF'
google.com
github.com
stackoverflow.com
termux.dev
EOF

# Step 2: Query all domains for A records
while read domain; do
    echo "=== $domain ==="
    dig +short $domain A
done < domains.txt

# Step 3: Query all record types for one domain
domain="google.com"
for type in A AAAA MX NS TXT SOA; do
    echo "=== $type ==="
    dig +short $domain $type
done

# Step 4: Compare results from different DNS servers
echo "Google DNS:"
dig @8.8.8.8 +short google.com
echo "Cloudflare DNS:"
dig @1.1.1.1 +short google.com
```

### Exercise 2: DNS Record Analysis

```bash
# Task: Analyze DNS records for a domain

cat > analyze-dns.sh << 'EOF'
#!/bin/bash

DOMAIN=$1

if [ -z "$DOMAIN" ]; then
    echo "Usage: $0 <domain>"
    exit 1
fi

echo "=========================================="
echo "DNS Analysis for: $DOMAIN"
echo "=========================================="

# A Records
echo -e "\n[+] A Records (IPv4):"
dig +noall +answer $DOMAIN A | awk '{print $5}'

# AAAA Records
echo -e "\n[+] AAAA Records (IPv6):"
dig +noall +answer $DOMAIN AAAA | awk '{print $5}'

# MX Records (sorted by priority)
echo -e "\n[+] MX Records:"
dig +noall +answer $DOMAIN MX | sort -n | awk '{print "Priority:", $5, "Server:", $6}'

# NS Records
echo -e "\n[+] Nameservers:"
dig +noall +answer $DOMAIN NS | awk '{print $5}'

# TXT Records
echo -e "\n[+] TXT Records:"
dig +noall +answer $DOMAIN TXT | awk '{for(i=5;i<=NF;i++) printf $i" "; print ""}'

# SOA Record
echo -e "\n[+] SOA Record:"
dig +noall +answer $DOMAIN SOA | awk '{print "Primary NS:", $5, "\nAdmin:", $6, "\nSerial:", $7}'

# CNAME for www
echo -e "\n[+] CNAME for www.$DOMAIN:"
dig +noall +answer www.$DOMAIN CNAME

echo -e "\n=========================================="
echo "Analysis Complete!"
echo "=========================================="
EOF

chmod +x analyze-dns.sh
./analyze-dns.sh google.com
```

### Exercise 3: Subdomain Enumeration

```bash
# Task: Discover subdomains using DNS

cat > subdomain-enum.sh << 'EOF'
#!/bin/bash

DOMAIN=$1

if [ -z "$DOMAIN" ]; then
    echo "Usage: $0 <domain>"
    exit 1
fi

# Common subdomain wordlist
SUBDOMAINS=(
    www
    mail
    ftp
    admin
    api
    dev
    staging
    blog
    shop
    vpn
    db
    mysql
    postgres
    redis
    mongo
    app
    mobile
    portal
    dashboard
    cdn
    static
    assets
    images
    video
    audio
    download
    upload
    secure
    login
    signin
    register
    support
    help
    docs
    wiki
    forum
    community
    news
    beta
    test
    qa
    old
    new
    m
    wap
    webmail
    email
    smtp
    imap
    pop
    ns1
    ns2
    dns
)

echo "Enumerating subdomains for $DOMAIN..."
echo "=========================================="

FOUND=0
for sub in "${SUBDOMAINS[@]}"; do
    RESULT=$(host $sub.$DOMAIN 2>/dev/null | grep "has address" | head -1)
    if [ -n "$RESULT" ]; then
        echo "[FOUND] $sub.$DOMAIN"
        echo "   $RESULT"
        ((FOUND++))
    fi
done

echo "=========================================="
echo "Found $FOUND subdomains"
EOF

chmod +x subdomain-enum.sh
./subdomain-enum.sh google.com
```

### Exercise 4: Zone Transfer Test

```bash
# Task: Test for DNS zone transfer vulnerability

cat > zone-transfer-test.sh << 'EOF'
#!/bin/bash

DOMAIN=$1

if [ -z "$DOMAIN" ]; then
    echo "Usage: $0 <domain>"
    exit 1
fi

echo "Testing Zone Transfer for: $DOMAIN"
echo "=========================================="

# Get nameservers
echo "[+] Getting nameservers..."
NAMESERVERS=$(dig +short $DOMAIN NS)

if [ -z "$NAMESERVERS" ]; then
    echo "[-] No nameservers found!"
    exit 1
fi

echo "$NAMESERVERS"

# Test each nameserver
for ns in $NAMESERVERS; do
    echo -e "\n[+] Testing $ns..."
    
    # Attempt AXFR
    RESULT=$(dig AXFR @$ns $DOMAIN 2>/dev/null)
    
    if echo "$RESULT" | grep -q "XFR size"; then
        echo "[!] ZONE TRANSFER SUCCESSFUL on $ns!"
        echo "$RESULT"
    else
        echo "[-] Zone transfer failed (good security)"
    fi
done

echo -e "\n=========================================="
echo "Zone Transfer Test Complete!"
EOF

chmod +x zone-transfer-test.sh
./zone-transfer-test.sh google.com
```

### Exercise 5: DNS Monitoring Script

```bash
# Task: Create a DNS monitoring script

cat > dns-monitor.sh << 'EOF'
#!/bin/bash

DOMAIN=$1
LOG_FILE="dns-monitor.log"

if [ -z "$DOMAIN" ]; then
    echo "Usage: $0 <domain>"
    exit 1
fi

echo "Starting DNS Monitor for: $DOMAIN"
echo "Press Ctrl+C to stop"
echo "Logging to: $LOG_FILE"

while true; do
    TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')
    
    # Get current A record
    CURRENT_IP=$(dig +short $DOMAIN A | head -1)
    
    # Get query time
    QUERY_TIME=$(dig $DOMAIN | grep "Query time" | awk '{print $4}')
    
    # Get DNS server used
    DNS_SERVER=$(dig $DOMAIN | grep "SERVER:" | awk '{print $3}' | tr -d '#')
    
    # Log the data
    echo "[$TIMESTAMP] IP: $CURRENT_IP | Query Time: ${QUERY_TIME}ms | DNS: $DNS_SERVER" >> $LOG_FILE
    echo "[$TIMESTAMP] IP: $CURRENT_IP | Query Time: ${QUERY_TIME}ms | DNS: $DNS_SERVER"
    
    # Check every 60 seconds
    sleep 60
done
EOF

chmod +x dns-monitor.sh
# ./dns-monitor.sh google.com  # Run to start monitoring
```

### Exercise 6: Complete DNS Enumeration Tool

```bash
# Task: Build a comprehensive DNS enumeration tool

cat > dns-enumerate.sh << 'EOF'
#!/bin/bash

# DNS Enumeration Tool by T3rmuxk1ng
# Usage: ./dns-enumerate.sh <domain>

DOMAIN=$1
OUTPUT_DIR="dns-enum-$DOMAIN"

if [ -z "$DOMAIN" ]; then
    echo "Usage: $0 <domain>"
    echo "Example: $0 google.com"
    exit 1
fi

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m'

# Create output directory
mkdir -p $OUTPUT_DIR

echo -e "${YELLOW}╔══════════════════════════════════════════╗${NC}"
echo -e "${YELLOW}║   DNS Enumeration Tool by T3rmuxk1ng     ║${NC}"
echo -e "${YELLOW}╚══════════════════════════════════════════╝${NC}"

echo -e "\n${BLUE}[*] Target: $DOMAIN${NC}"
echo -e "${BLUE}[*] Output: $OUTPUT_DIR/${NC}\n"

# 1. Basic DNS Records
echo -e "${GREEN}[1/8] Collecting DNS Records...${NC}"
dig +noall +answer $DOMAIN A > $OUTPUT_DIR/A.txt
dig +noall +answer $DOMAIN AAAA > $OUTPUT_DIR/AAAA.txt
dig +noall +answer $DOMAIN MX > $OUTPUT_DIR/MX.txt
dig +noall +answer $DOMAIN NS > $OUTPUT_DIR/NS.txt
dig +noall +answer $DOMAIN TXT > $OUTPUT_DIR/TXT.txt
dig +noall +answer $DOMAIN SOA > $OUTPUT_DIR/SOA.txt

# Display results
echo -e "${YELLOW}A Records:${NC}"
cat $OUTPUT_DIR/A.txt
echo -e "\n${YELLOW}MX Records:${NC}"
cat $OUTPUT_DIR/MX.txt
echo -e "\n${YELLOW}NS Records:${NC}"
cat $OUTPUT_DIR/NS.txt

# 2. Nameserver IPs
echo -e "\n${GREEN}[2/8] Nameserver IP Resolution...${NC}"
for ns in $(dig +short $DOMAIN NS); do
    ns_ip=$(dig +short $ns A | head -1)
    echo "$ns -> $ns_ip"
done | tee $OUTPUT_DIR/ns-ips.txt

# 3. Mail Server IPs
echo -e "\n${GREEN}[3/8] Mail Server IP Resolution...${NC}"
dig +short $DOMAIN MX | while read pri server; do
    server_ip=$(dig +short $server A | head -1)
    echo "Priority $pri: $server -> $server_ip"
done | tee $OUTPUT_DIR/mx-ips.txt

# 4. WHOIS Information
echo -e "\n${GREEN}[4/8] WHOIS Information...${NC}"
whois $DOMAIN 2>/dev/null > $OUTPUT_DIR/whois.txt
echo "Registrar: $(grep -m1 'Registrar:' $OUTPUT_DIR/whois.txt | cut -d: -f2-)"
echo "Created: $(grep -m1 'Creation Date' $OUTPUT_DIR/whois.txt | cut -d: -f2-)"
echo "Expires: $(grep -m1 'Expiry' $OUTPUT_DIR/whois.txt | cut -d: -f2-)"

# 5. Zone Transfer Test
echo -e "\n${GREEN}[5/8] Zone Transfer Test...${NC}"
ZONE_TRANSFER="FAILED"
for ns in $(dig +short $DOMAIN NS); do
    if dig AXFR @$ns $DOMAIN 2>/dev/null | grep -q "XFR size"; then
        ZONE_TRANSFER="SUCCESS on $ns"
        dig AXFR @$ns $DOMAIN > $OUTPUT_DIR/zone-transfer.txt
        break
    fi
done
echo "Zone Transfer: $ZONE_TRANSFER"

# 6. Subdomain Enumeration (top 20)
echo -e "\n${GREEN}[6/8] Subdomain Enumeration...${NC}"
SUBDOMAINS="www mail ftp admin api dev staging blog shop vpn app mobile portal cdn static assets m wap webmail"
FOUND_COUNT=0
for sub in $SUBDOMAINS; do
    result=$(host $sub.$DOMAIN 2>/dev/null | grep "has address" | head -1)
    if [ -n "$result" ]; then
        echo "[FOUND] $sub.$DOMAIN"
        echo "$sub.$DOMAIN" >> $OUTPUT_DIR/subdomains.txt
        echo "$result" >> $OUTPUT_DIR/subdomains.txt
        ((FOUND_COUNT++))
    fi
done
echo "Found $FOUND_COUNT subdomains"

# 7. Reverse DNS
echo -e "\n${GREEN}[7/8] Reverse DNS Lookups...${NC}"
for ip in $(dig +short $DOMAIN A); do
    reverse=$(dig +short -x $ip | head -1)
    echo "$ip -> $reverse"
done | tee $OUTPUT_DIR/reverse-dns.txt

# 8. DNSSEC Check
echo -e "\n${GREEN}[8/8] DNSSEC Check...${NC}"
DNSSEC=$(dig +dnssec $DOMAIN | grep "flags:" | grep -o "ad")
if [ -n "$DNSSEC" ]; then
    echo "DNSSEC: ENABLED"
else
    echo "DNSSEC: NOT ENABLED"
fi

# Summary
echo -e "\n${YELLOW}╔══════════════════════════════════════════╗${NC}"
echo -e "${YELLOW}║           ENUMERATION COMPLETE            ║${NC}"
echo -e "${YELLOW}╚══════════════════════════════════════════╝${NC}"
echo -e "${GREEN}Results saved to: $OUTPUT_DIR/${NC}"
echo -e "${GREEN}Files created:${NC}"
ls -la $OUTPUT_DIR/

echo -e "\n${BLUE}Next Steps:${NC}"
echo "1. Review TXT records for sensitive info"
echo "2. Test each subdomain for vulnerabilities"
echo "3. Check mail server security (SPF, DKIM, DMARC)"
echo "4. Verify zone transfer files for additional hosts"
EOF

chmod +x dns-enumerate.sh
./dns-enumerate.sh google.com
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "dig: command not found"

```bash
# Cause: dnsutils package not installed

# Solution:
pkg update && pkg upgrade -y
pkg install dnsutils -y

# Verify:
dig -v
```

### Problem 2: "whois: command not found"

```bash
# Cause: whois package not installed

# Solution:
pkg install whois -y

# Verify:
whois --version
```

### Problem 3: DNS queries timeout

```bash
# Cause: Network issues or DNS server unreachable

# Solution 1: Check network
ping -c 3 8.8.8.8

# Solution 2: Use different DNS server
dig @1.1.1.1 google.com

# Solution 3: Increase timeout
dig +time=10 google.com

# Solution 4: Use TCP instead of UDP
dig +tcp google.com

# Solution 5: Check DNS port
nc -zv 8.8.8.8 53
```

### Problem 4: "Connection refused" on zone transfer

```bash
# This is NORMAL - most servers block zone transfers
# It's a security measure, not an error

# Proper interpretation:
# - If zone transfer fails = Good security
# - If zone transfer succeeds = Misconfiguration (vulnerability)
```

### Problem 5: WHOIS rate limited

```bash
# Cause: Too many queries to WHOIS server

# Solution 1: Wait and retry
sleep 60 && whois google.com

# Solution 2: Use different WHOIS server
whois -h whois.verisign-grs.com google.com

# Solution 3: Use web-based WHOIS
# https://who.is / https://whois.net
```

### Problem 6: Inconsistent DNS results

```bash
# Cause: DNS caching, propagation, or different DNS servers

# Solution 1: Bypass cache with specific DNS
dig @8.8.8.8 google.com

# Solution 2: Check authoritative server directly
dig @$(dig +short google.com NS | head -1) google.com

# Solution 3: Check TTL
dig google.com | grep -A1 "ANSWER SECTION"

# Solution 4: Compare multiple DNS servers
for dns in 8.8.8.8 1.1.1.1 9.9.9.9; do
    echo "DNS: $dns"
    dig @$dns +short google.com
done
```

### Problem 7: IPv6 queries failing

```bash
# Cause: Network doesn't support IPv6

# Solution 1: Use IPv4-only queries
dig -4 google.com A

# Solution 2: Check IPv6 connectivity
ping6 -c 3 google.com

# Solution 3: Query AAAA record but don't use
dig +short google.com AAAA
```

### Problem 8: DNS over HTTPS/TLS not working

```bash
# Cause: Requires additional setup

# For DoH (DNS over HTTPS):
curl -H 'accept: application/dns-json' \
    'https://cloudflare-dns.com/dns-query?name=google.com&type=A'

# For DoT (DNS over TLS):
# Not directly supported in Termux dig
# Use stunnel or dedicated DoT client
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Clean & Professional**
```
┌────────────────────────────────────┐
│  [Dark Terminal Background]        │
│                                    │
│   🔍 DNS & DOMAIN TOOLS            │
│   COMPLETE GUIDE                   │
│                                    │
│   ✓ dig, nslookup, whois          │
│   ✓ DNS Enumeration               │
│   ✓ 25+ Commands                  │
│                                    │
│   [T3rmuxk1ng Logo]               │
└────────────────────────────────────┘
```

**Option B: Command Focus**
```
┌────────────────────────────────────┐
│  [Green on Black Terminal]         │
│                                    │
│   $ dig google.com                 │
│   $ nslookup ...                   │
│   $ whois ...                      │
│                                    │
│   DNS MASTERY                      │
│   Chapter 29                       │
│                                    │
│   [T3rmuxk1ng]                     │
└────────────────────────────────────┘
```

**Option C: Comparison Style**
```
┌────────────────────────────────────┐
│  DNS TOOLS COMPARISON              │
│  ───────────────────────────────── │
│  dig        ⭐⭐⭐⭐⭐ Most Powerful  │
│  nslookup   ⭐⭐⭐⭐ Classic         │
│  host       ⭐⭐⭐ Simple           │
│  whois      ⭐⭐⭐⭐ Domain Info     │
│                                    │
│  LEARN ALL! | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔍 Termux Full Course - Chapter 29: DNS & Domain Tools | Complete DNS Enumeration Guide

🔥 In this video you'll learn:
• DNS fundamentals aur resolution process
• dig command - advanced DNS queries
• nslookup - classic DNS tool
• host command - simple DNS lookup
• whois - domain registration information
• DNS record types (A, AAAA, MX, TXT, NS, CNAME, SOA)
• Reverse DNS lookup techniques
• Subdomain discovery methods
• DNS zone transfer testing
• DNS troubleshooting

⏱️ Timestamps:
0:00 - Introduction
0:50 - DNS Fundamentals
4:00 - DNS Tools Installation
5:30 - DIG Command Deep Dive
9:00 - NSLOOKUP Command
11:30 - HOST Command
13:00 - WHOIS Command
15:30 - DNS Record Types
18:00 - Reverse DNS Lookup
19:30 - Subdomain Discovery
21:30 - DNS Zone Transfer
23:00 - DNS Troubleshooting
25:00 - DNS Lookup Script
27:00 - Summary

📝 Commands from this video:
# Install tools
pkg install dnsutils whois -y

# Basic lookups
dig google.com
nslookup google.com
host google.com
whois google.com

# Specific records
dig google.com MX
dig google.com NS
dig +short google.com

# Reverse DNS
dig -x 142.250.195.78

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #DNS #DNSEnumeration #T3rmuxk1ng #TermuxCourse #DNSTools #DigCommand #Nslookup #Whois #NetworkSecurity #TermuxHindi #EthicalHacking

---
⚠️ Disclaimer: This video is for educational purposes. Use DNS tools responsibly and only on domains you have permission to analyze.
```

### Tags List

```
termux, dns tools, dig command, nslookup, whois, dns enumeration, 
termux dns, dns lookup, domain information, dns record types,
termux course, t3rmuxk1ng, dns tutorial, dns query, reverse dns,
subdomain enumeration, zone transfer, dns security, network tools,
termux networking, a record, mx record, dns troubleshooting,
domain lookup, ip lookup, dns server, nameserver, termux hindi
```

### Hashtags

```
#Termux #DNS #DNSTools #DigCommand #Nslookup #Whois #TermuxCourse 
#T3rmuxk1ng #DNSEnumeration #NetworkSecurity #TermuxHindi #DNSLookup 
#DomainTools #CyberSecurity #EthicalHacking #LearnTermux
```

---

## 📚 ADDITIONAL RESOURCES

### Public DNS Servers

| Provider | IPv4 Primary | IPv4 Secondary | IPv6 Primary |
|----------|--------------|----------------|--------------|
| Google | 8.8.8.8 | 8.8.4.4 | 2001:4860:4860::8888 |
| Cloudflare | 1.1.1.1 | 1.0.0.1 | 2606:4700:4700::1111 |
| OpenDNS | 208.67.222.222 | 208.67.220.220 | 2620:119:35::35 |
| Quad9 | 9.9.9.9 | 149.112.112.112 | 2620:fe::fe |
| AdGuard | 94.140.14.14 | 94.140.15.15 | 2a10:50c0::ad1:ff |

### Online DNS Tools

| Tool | URL | Purpose |
|------|-----|---------|
| DNS Checker | https://dnschecker.org | Global DNS propagation |
| WhatsMyDNS | https://whatsmydns.net | DNS propagation check |
| MXToolbox | https://mxtoolbox.com | MX, DNS, Email analysis |
| ViewDNS.info | https://viewdns.info | Comprehensive DNS tools |
| DNSdumpster | https://dnsdumpster.com | DNS reconnaissance |
| SecurityTrails | https://securitytrails.com | Historical DNS data |

### DNS Learning Resources

| Resource | Description |
|----------|-------------|
| RFC 1035 | DNS protocol specification |
| RFC 1912 | Common DNS operational errors |
| DNS BIND documentation | DNS server configuration |
| How DNS Works | https://howdns.works |

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 30, verify:

- [ ] Installed dnsutils and whois packages
- [ ] Understand DNS resolution process
- [ ] Can use dig for various DNS queries
- [ ] Know how to query specific record types (A, MX, NS, TXT)
- [ ] Can perform reverse DNS lookups
- [ ] Understand DNS zone transfer and its security implications
- [ ] Can enumerate subdomains using DNS
- [ ] Can use whois to get domain information
- [ ] Created and tested DNS enumeration scripts
- [ ] Understand common DNS troubleshooting techniques

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 30: Security Tools Overview**

- Ethical hacking introduction
- Security testing methodology
- Legal considerations and scope
- Tools available in Termux vs Proot
- Lab environment setup
- Wordlists and resources
- Documentation and reporting

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
