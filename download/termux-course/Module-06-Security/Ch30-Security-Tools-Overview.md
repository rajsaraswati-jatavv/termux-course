# Chapter 30: Security Tools Overview

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   ███████╗████████╗██████╗ ███████╗ ██████╗████████╗██╗ ██████╗ ███╗   ██╗  ║
║   ██╔════╝╚══██╔══╝██╔══██╗██╔════╝██╔════╝╚══██╔══╝██║██╔═══██╗████╗  ██║  ║
║   ███████╗   ██║   ██████╔╝█████╗  ██║        ██║   ██║██║   ██║██╔██╗ ██║  ║
║   ╚════██║   ██║   ██╔══██╗██╔══╝  ██║        ██║   ██║██║   ██║██║╚██╗██║  ║
║   ███████║   ██║   ██║  ██║███████╗╚██████╗   ██║   ██║╚██████╔╝██║ ╚████║  ║
║   ╚══════╝   ╚═╝   ╚═╝  ╚═╝╚══════╝ ╚═════╝   ╚═╝   ╚═╝ ╚═════╝ ╚═╝  ╚═══╝  ║
║                                                                              ║
║              📖 CHAPTER 30: SECURITY TOOLS OVERVIEW 📖                       ║
║                      ⭐ Ethical Hacking Foundation ⭐                        ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 6 - Security  
> **Chapter:** 30 of 61  
> **Duration:** 20-25 Minutes  
> **Difficulty:** ⭐⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | Security tools, methodology, lab setup |
| Legal Framework | Ethics, scope, authorization |
| Commands Reference | All security tool commands |
| Practice Exercises | Hands-on security tasks |
| Troubleshooting | Common tool installation issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎮 INTERACTIVE QUIZ

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                        🧠 CHAPTER 30 QUIZ - SECURITY FOUNDATION              ║
║                              Test Your Knowledge!                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

**Q1: What is the PRIMARY difference between ethical hacking and malicious hacking?**
- A) Tools used
- B) Permission and authorization
- C) Operating system
- D) Internet speed

**Q2: Which section of the IT Act 2000 deals with computer hacking in India?**
- A) Section 65
- B) Section 66
- C) Section 67
- D) Section 68

**Q3: What is the key difference between Hydra and John the Ripper?**
- A) Hydra is faster
- B) John has more protocols
- C) Hydra is online, John is offline cracking
- D) No difference

**Q4: Which framework provides the Penetration Testing Execution Standard?**
- A) OWASP
- B) NIST
- C) PTES
- D) ISO

**Q5: Which tool requires actual ROOT access on Android for full functionality?**
- A) Nmap
- B) Hydra
- C) Aircrack-ng (injection mode)
- D) SQLMap

**Q6: What is the recommended minimum password length for strong security?**
- A) 8 characters
- B) 10 characters
- C) 12 characters
- D) 6 characters

**Q7: In the security testing lifecycle, which phase comes AFTER Scanning?**
- A) Reconnaissance
- B) Exploitation
- C) Reporting
- D) Scope Definition

**Q8: What is rockyou.txt?**
- A) A hacking tool
- B) A wordlist with 14.3 million passwords
- C) A scanning tool
- D) A Linux distribution

**Q9: Which command installs Kali Linux in Termux using proot?**
- A) `pkg install kali`
- B) `proot-distro install kali`
- C) `apt-get install kali`
- D) `sudo install kali`

**Q10: What is the correct order of penetration testing phases?**
- A) Exploit → Scan → Report → Recon
- B) Recon → Scan → Exploit → Report
- C) Report → Recon → Scan → Exploit
- D) Scan → Recon → Report → Exploit

**Q11: Which tool is primarily used for network port scanning?**
- A) John
- B) Hydra
- C) Nmap
- D) Crunch

**Q12: What should be obtained BEFORE starting any penetration test?**
- A) New tools
- B) Written authorization
- C) Social media accounts
- D) Employee information

**Q13: Which encryption type is considered BROKEN and should never be used?**
- A) WPA2
- B) WPA3
- C) WEP
- D) WPA

**Q14: What is the purpose of the post-exploitation phase?**
- A) Install tools
- B) Maintain access and gather more data
- C) Create reports
- D) Scan networks

**Q15: Which online platform is recommended for beginners in cybersecurity?**
- A) Dark web forums
- B) TryHackMe
- C) Torrent sites
- D) Random YouTube videos

<details>
<summary>📝 Click to Reveal Answers</summary>

| Q# | Answer | Explanation |
|----|--------|-------------|
| 1 | **B** | Ethical hacking requires explicit permission |
| 2 | **B** | Section 66 covers computer hacking offenses |
| 3 | **C** | Hydra attacks live services, John cracks hashes |
| 4 | **C** | PTES = Penetration Testing Execution Standard |
| 5 | **C** | Aircrack-ng injection needs kernel access |
| 6 | **C** | 12+ characters with complexity recommended |
| 7 | **B** | Order: Scope → Recon → Scan → Exploit → Report |
| 8 | **B** | Rockyou contains 14.3M leaked passwords |
| 9 | **B** | `proot-distro install kali` is correct |
| 10 | **B** | Recon → Scan → Exploit → Report |
| 11 | **C** | Nmap is the industry standard port scanner |
| 12 | **B** | Written authorization is legally required |
| 13 | **C** | WEP is completely broken, never use it |
| 14 | **B** | Post-exploitation maintains access and gathers data |
| 15 | **B** | TryHackMe offers guided beginner-friendly labs |

</details>

---

## 🎯 INTERVIEW QUESTIONS

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                    💼 SECURITY INTERVIEW PREPARATION                         ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

**Q1: Explain the difference between vulnerability assessment and penetration testing.**
<details>
<summary>Show Answer</summary>

**Vulnerability Assessment:**
- Automated scanning for known vulnerabilities
- Finds weaknesses but doesn't exploit them
- Broader scope, less depth
- Examples: Nessus, OpenVAS scans

**Penetration Testing:**
- Simulates real attacks to exploit vulnerabilities
- Manual testing with automated tools
- Deeper analysis, proof of exploitation
- Includes post-exploitation and reporting

**Key Difference:** Vulnerability assessment identifies, penetration testing validates and exploits.
</details>

**Q2: What are the 5 phases of penetration testing according to PTES?**
<details>
<summary>Show Answer</summary>

1. **Reconnaissance** - Information gathering (passive/active)
2. **Scanning** - Port scanning, service enumeration, vulnerability scanning
3. **Exploitation** - Gaining access through vulnerabilities
4. **Post-Exploitation** - Maintaining access, privilege escalation, data gathering
5. **Reporting** - Documentation, findings, recommendations

Additionally: Pre-engagement interactions and threat modeling before testing begins.
</details>

**Q3: What legal documents are required before conducting a penetration test?**
<details>
<summary>Show Answer</summary>

1. **Written Authorization/Contract** - Signed by authorized representative
2. **Scope Document** - Defines targets, tools, timelines
3. **Rules of Engagement** - Testing hours, emergency contacts, restrictions
4. **NDA (Non-Disclosure Agreement)** - Protects sensitive information
5. **Insurance Documentation** - Professional indemnity coverage
6. **Incident Response Plan** - What to do if something goes wrong

**Critical:** Never test without proper documentation!
</details>

**Q4: Explain the CIA triad in information security.**
<details>
<summary>Show Answer</summary>

**Confidentiality:**
- Data accessible only to authorized users
- Encryption, access controls, authentication
- Example: Password-protected files

**Integrity:**
- Data accuracy and trustworthiness
- Hashing, digital signatures, checksums
- Example: File integrity monitoring

**Availability:**
- Systems and data accessible when needed
- Redundancy, backups, DDoS protection
- Example: Load balancers, failover systems

All three must be balanced for effective security.
</details>

**Q5: What is OWASP Top 10 and why is it important?**
<details>
<summary>Show Answer</summary>

OWASP Top 10 is a list of the 10 most critical web application security risks:

1. Broken Access Control
2. Cryptographic Failures
3. Injection (SQL, Command, etc.)
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable Components
7. Authentication Failures
8. Software Integrity Failures
9. Logging Failures
10. SSRF (Server-Side Request Forgery)

**Importance:**
- Industry standard for web security
- Guides security testing priorities
- Helps developers write secure code
- Used in compliance requirements
</details>

**Q6: What is the difference between white box, black box, and gray box testing?**
<details>
<summary>Show Answer</summary>

**Black Box Testing:**
- No prior knowledge of the system
- Simulates external attacker
- Tests from outside perspective
- Time-consuming but realistic

**White Box Testing:**
- Full knowledge of system architecture
- Access to source code and documentation
- More thorough and faster
- Simulates insider threat

**Gray Box Testing:**
- Partial knowledge (credentials, some docs)
- Most common in real engagements
- Balanced approach
- Efficient and realistic
</details>

**Q7: How would you handle finding a critical vulnerability during a test?**
<details>
<summary>Show Answer</summary>

1. **STOP** - Don't continue exploitation
2. **Document** - Capture evidence (screenshots, logs)
3. **Notify** - Contact designated emergency contact immediately
4. **Assess Impact** - Determine scope of potential damage
5. **Recommend Remediation** - Provide immediate mitigation steps
6. **Continue** - Resume testing after client acknowledgment
7. **Report** - Include in final report with priority rating

**Critical Rule:** Never leave critical issues unreported until the end!
</details>

**Q8: What tools would you use for network reconnaissance?**
<details>
<summary>Show Answer</summary>

**Passive Reconnaissance:**
- WHOIS - Domain registration info
- Shodan - Internet-connected devices
- Google Dorks - Search engine reconnaissance
- Social Media - OSINT gathering
- DNSDumpster - DNS information

**Active Reconnaissance:**
- Nmap - Port scanning, service detection
- Masscan - Fast large-scale scanning
- Dnsenum - DNS enumeration
- Nbtscan - NetBIOS scanning
- Netdiscover - ARP scanning

**Best Practice:** Start passive, then move to active.
</details>

**Q9: Explain responsible disclosure.**
<details>
<summary>Show Answer</summary>

**Responsible Disclosure Process:**

1. **Discovery** - Find vulnerability ethically
2. **Documentation** - Record all details
3. **Vendor Contact** - Notify organization privately
4. **Wait Period** - Give reasonable time to fix (90 days standard)
5. **Coordination** - Work with vendor on timeline
6. **Public Disclosure** - Release details after fix
7. **Credit** - Acknowledgment for finding

**Key Principles:**
- Don't exploit for personal gain
- Protect user data
- Allow time for fixes
- Follow legal guidelines
</details>

**Q10: What certifications should a penetration tester pursue?**
<details>
<summary>Show Answer</summary>

**Entry Level:**
- CEH (Certified Ethical Hacker)
- eJPT (eLearnSecurity Junior Penetration Tester)
- CompTIA Security+

**Intermediate:**
- OSCP (Offensive Security Certified Professional) - **Most Valuable**
- eCPPT (Certified Professional Penetration Tester)
- GPEN (GIAC Penetration Tester)

**Advanced:**
- OSCE (Offensive Security Certified Expert)
- OSEE (Offensive Security Exploitation Expert)
- CRTO (Certified Red Team Operator)

**Specialized:**
- GWAPT (Web Application Penetration Tester)
- OSWP (Wireless Professional)
- CSSP (Cloud Security Professional)
</details>

---

## 🔥 REAL-WORLD SCENARIOS

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                       🌍 REAL-WORLD SECURITY SCENARIOS                       ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 📋 Scenario 1: Corporate Network Assessment

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  SCENARIO: A company hires you for a black-box penetration test             │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  SITUATION:                                                                  │
│  Company: TechCorp Inc. (500 employees)                                     │
│  Scope: External infrastructure only                                        │
│  Timeline: 2 weeks                                                          │
│  Goal: Identify vulnerabilities before malicious actors                     │
│                                                                              │
│  YOUR APPROACH:                                                              │
│  1. Phase 1 - Reconnaissance                                                │
│     • WHOIS lookup on techcorp.com                                          │
│     • DNS enumeration for subdomains                                        │
│     • Google dorking for exposed files                                      │
│     • Shodan search for public services                                     │
│                                                                              │
│  2. Phase 2 - Scanning                                                      │
│     • Nmap scan of public IP ranges                                         │
│     • Service version detection                                             │
│     • Vulnerability scanning with Nessus                                    │
│                                                                              │
│  3. Phase 3 - Exploitation                                                  │
│     • Test for weak credentials on services                                 │
│     • Check for known CVEs                                                  │
│     • Attempt SQL injection on web apps                                     │
│                                                                              │
│  4. Phase 4 - Reporting                                                     │
│     • Executive summary                                                      │
│     • Technical findings with PoC                                           │
│     • Remediation recommendations                                           │
│                                                                              │
│  KEY FINDINGS EXAMPLE:                                                       │
│  • SSH server with default credentials                                      │
│  • Outdated web server with known CVE                                       │
│  • Exposed admin panel without authentication                               │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### 📋 Scenario 2: Bug Bounty Discovery

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  SCENARIO: Testing a web application for bug bounty                         │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  TARGET: e-commerce website with user authentication                        │
│  PROGRAM: Private bug bounty on HackerOne                                   │
│                                                                              │
│  DISCOVERY PROCESS:                                                          │
│  1. Create test account                                                     │
│  2. Explore application functionality                                       │
│  3. Test parameter manipulation                                             │
│  4. Attempt authentication bypasses                                         │
│                                                                              │
│  VULNERABILITY FOUND:                                                        │
│  • IDOR (Insecure Direct Object Reference)                                  │
│  • URL: /api/user/123/profile                                               │
│  • Changing 123 to 124 reveals another user's data                          │
│                                                                              │
│  RESPONSIBLE DISCLOSURE:                                                     │
│  1. Document with screenshots                                               │
│  2. Create proof-of-concept script                                          │
│  3. Submit through HackerOne platform                                       │
│  4. Wait for vendor response                                                │
│  5. Provide additional details if requested                                 │
│                                                                              │
│  IMPACT: High - User data exposure                                          │
│  REWARD: $500 - $2000 (typical for IDOR)                                    │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### 📋 Scenario 3: Internal Security Audit

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  SCENARIO: Internal network security assessment                             │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  CONTEXT:                                                                    │
│  Organization wants to test internal security controls                      │
│  You have internal network access (gray box testing)                        │
│                                                                              │
│  TESTING CHECKLIST:                                                          │
│  □ Network segmentation validation                                          │
│  □ Active Directory security testing                                        │
│  □ Wireless network assessment                                              │
│  □ Endpoint security testing                                                │
│  □ Privilege escalation paths                                               │
│                                                                              │
│  COMMON FINDINGS:                                                            │
│  1. Weak password policies                                                  │
│  2. Unpatched systems                                                       │
│  3. Misconfigured shares                                                    │
│  4. Default credentials on devices                                          │
│  5. Lack of network segmentation                                            │
│                                                                              │
│  TOOLS USED:                                                                 │
│  • Nmap - Network discovery                                                 │
│  • Bloodhound - AD relationship mapping                                     │
│  • CrackMapExec - Credential testing                                        │
│  • Mimikatz - Credential extraction (with permission)                       │
│                                                                              │
│  DELIVERABLE:                                                                │
│  Comprehensive report with risk ratings and remediation roadmap             │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### 📋 Scenario 4: Social Engineering Assessment

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  SCENARIO: Testing human security awareness                                 │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  OBJECTIVE: Assess employee awareness to social engineering                 │
│                                                                              │
│  METHODS:                                                                    │
│  1. Phishing Campaign                                                        │
│     • Create realistic fake login page                                      │
│     • Send simulated phishing emails                                        │
│     • Track click rates and credential submissions                          │
│                                                                              │
│  2. Vishing (Voice Phishing)                                                │
│     • Call employees pretending to be IT support                            │
│     • Attempt to get credentials or sensitive info                          │
│                                                                              │
│  3. Physical Security                                                        │
│     • Attempt tailgating                                                    │
│     • Test badge security                                                   │
│     • Check for sensitive documents left out                                │
│                                                                              │
│  METRICS TRACKED:                                                            │
│  • Phishing click rate                                                      │
│  • Credential submission rate                                               │
│  • Reporting rate (employees reporting suspicious activity)                 │
│                                                                              │
│  REMEDIATION:                                                                │
│  • Security awareness training                                              │
│  • Simulated phishing exercises                                             │
│  • Clear reporting procedures                                               │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### 📋 Scenario 5: Incident Response

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  SCENARIO: Security breach discovered - assist in investigation             │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  SITUATION:                                                                  │
│  Company detected unusual network activity                                  │
│  Possible data breach in progress                                           │
│                                                                              │
│  RESPONSE PHASES:                                                            │
│  1. IDENTIFICATION                                                           │
│     • Analyze logs for malicious activity                                   │
│     • Identify affected systems                                             │
│     • Determine attack vector                                               │
│                                                                              │
│  2. CONTAINMENT                                                              │
│     • Isolate affected systems                                              │
│     • Block malicious IPs                                                   │
│     • Preserve evidence                                                     │
│                                                                              │
│  3. ERADICATION                                                              │
│     • Remove malware/backdoors                                              │
│     • Patch vulnerabilities exploited                                       │
│     • Reset compromised credentials                                         │
│                                                                              │
│  4. RECOVERY                                                                 │
│     • Restore from clean backups                                            │
│     • Monitor for re-infection                                              │
│     • Implement additional controls                                         │
│                                                                              │
│  5. LESSONS LEARNED                                                          │
│     • Document timeline                                                     │
│     • Identify gaps in security                                             │
│     • Update security procedures                                            │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## ⚠️ SECURITY BEST PRACTICES

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                       🛡️ SECURITY DO'S AND DON'TS                           ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### ✅ DO's (Best Practices)

| Category | Best Practice | Why It Matters |
|----------|--------------|----------------|
| **Authorization** | Always get written permission | Legal protection |
| **Scope** | Define clear boundaries | Prevent scope creep |
| **Documentation** | Document everything | Professional accountability |
| **Communication** | Report critical issues immediately | Minimize damage |
| **Tools** | Use only approved tools | Avoid legal issues |
| **Data** | Handle sensitive data securely | Protect client privacy |
| **Cleanup** | Remove all test artifacts | Prevent future exploitation |
| **Ethics** | Follow code of conduct | Professional integrity |
| **Learning** | Stay updated with new techniques | Effective testing |
| **Reporting** | Provide actionable recommendations | Client value |

### ❌ DON'Ts (What to Avoid)

| Category | What NOT to Do | Consequences |
|----------|---------------|--------------|
| **Testing** | Test without authorization | Legal prosecution |
| **Scope** | Exceed defined boundaries | Contract termination |
| **Data** | Access or copy sensitive data unnecessarily | Privacy violations |
| **Disclosure** | Share findings publicly without approval | Loss of trust |
| **Tools** | Use malicious tools or techniques | Ethical violation |
| **Evidence** | Destroy logs or artifacts | Loss of proof |
| **Communication** | Discuss ongoing tests publicly | Compromise test |
| **Cleanup** | Leave backdoors or tools behind | Security risk |
| **Attitude** | Be overconfident or dismissive | Poor relationships |
| **Payment** | Accept bribes or extort clients | Criminal charges |

### 🔐 Personal Security Habits

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                     DAILY SECURITY HABITS FOR PENTESTERS                     │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ✓ Use separate VMs for different clients                                   │
│  ✓ Encrypt all sensitive data                                               │
│  ✓ Use password manager with strong master password                         │
│  ✓ Enable 2FA on all accounts                                               │
│  ✓ Regular security updates for all tools                                   │
│  ✓ Use VPN for internet access                                              │
│  ✓ Secure deletion of test data after engagement                            │
│  ✓ Regular backup of important configurations                               │
│  ✓ Physical security of devices                                             │
│  ✓ Legal consultation when in doubt                                         │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 ARCHITECTURE DIAGRAMS

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                        🏗️ SECURITY ARCHITECTURE DIAGRAMS                    ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Diagram 1: Penetration Testing Workflow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    PENETRATION TESTING WORKFLOW                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌────────────┐     ┌────────────┐     ┌────────────┐     ┌────────────┐   │
│  │   PHASE 1  │────▶│   PHASE 2  │────▶│   PHASE 3  │────▶│   PHASE 4  │   │
│  │    SCOPE   │     │   RECON    │     │   SCAN     │     │  EXPLOIT   │   │
│  │            │     │            │     │            │     │            │   │
│  │ • Contract │     │ • Passive  │     │ • Nmap     │     │ • Vulns    │   │
│  │ • Scope    │     │ • Active   │     │ • Vuln     │     │ • Payloads │   │
│  │ • Rules    │     │ • OSINT    │     │   Scanners │     │ • Access   │   │
│  └────────────┘     └────────────┘     └────────────┘     └─────┬──────┘   │
│                                                                   │          │
│                                                                   ▼          │
│  ┌────────────┐     ┌────────────┐     ┌────────────┐     ┌────────────┐   │
│  │   REPORT   │◀────│  CLEANUP   │◀────│  POST-EXP  │◀────│  ACCESS    │   │
│  │            │     │            │     │            │     │  GAINED    │   │
│  │ • Summary  │     │ • Remove   │     │ • Persist  │     │            │   │
│  │ • Findings │     │   Tools    │     │ • Escalate │     │ • Shell    │   │
│  │ • Fixes    │     │ • Evidence │     │ • Gather   │     │ • Data     │   │
│  └────────────┘     └────────────┘     └────────────┘     └────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: Security Tools Ecosystem

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    SECURITY TOOLS ECOSYSTEM                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│                          ┌─────────────────┐                                │
│                          │   PENTESTER     │                                │
│                          │   (You)         │                                │
│                          └────────┬────────┘                                │
│                                   │                                          │
│           ┌───────────────────────┼───────────────────────┐                 │
│           │                       │                       │                 │
│           ▼                       ▼                       ▼                 │
│  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐          │
│  │   RECON TOOLS   │    │   ATTACK TOOLS  │    │  POST-EXP TOOLS │          │
│  ├─────────────────┤    ├─────────────────┤    ├─────────────────┤          │
│  │ • Nmap          │    │ • Metasploit    │    │ • Mimikatz      │          │
│  │ • Shodan        │    │ • Hydra         │    │ • PowerSploit   │          │
│  │ • Maltego       │    │ • SQLMap        │    │ • Empire        │          │
│  │ • theHarvester  │    │ • Burp Suite    │    │ • Netcat        │          │
│  │ • DNSenum       │    │ • John          │    │ • Weevely       │          │
│  └─────────────────┘    └─────────────────┘    └─────────────────┘          │
│           │                       │                       │                 │
│           └───────────────────────┼───────────────────────┘                 │
│                                   ▼                                          │
│                          ┌─────────────────┐                                │
│                          │    REPORTING    │                                │
│                          │ • Dradis        │                                │
│                          │ • CherryTree    │                                │
│                          │ • Markdown      │                                │
│                          └─────────────────┘                                │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: Attack Surface Model

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    ORGANIZATIONAL ATTACK SURFACE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│                        ╔═════════════════════╗                              │
│                        ║   ORGANIZATION      ║                              │
│                        ╚════════╤════════════╝                              │
│                                 │                                            │
│        ┌────────────────────────┼────────────────────────┐                  │
│        │                        │                        │                  │
│        ▼                        ▼                        ▼                  │
│  ┌───────────┐           ┌───────────┐           ┌───────────┐             │
│  │  NETWORK  │           │    WEB    │           │   HUMAN   │             │
│  │  LAYER    │           │   LAYER   │           │   LAYER   │             │
│  ├───────────┤           ├───────────┤           ├───────────┤             │
│  │ • Ports   │           │ • Web App │           │ • Phishing│             │
│  │ • Services│           │ • API     │           │ • Vishing │             │
│  │ • WiFi    │           │ • Cookies │           │ • Imperson│             │
│  │ • VPN     │           │ • Sessions│           │ • Social  │             │
│  └───────────┘           └───────────┘           └───────────┘             │
│        │                        │                        │                  │
│        ▼                        ▼                        ▼                  │
│  ┌───────────┐           ┌───────────┐           ┌───────────┐             │
│  │   TOOLS   │           │   TOOLS   │           │   TOOLS   │             │
│  │ • Nmap    │           │ • Burp    │           │ • SET     │             │
│  │ • Masscan │           │ • OWASP   │           │ • Gophish │             │
│  │ • Netcat  │           │ • SQLMap  │           │ • Social  │             │
│  └───────────┘           └───────────┘           └───────────┘             │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                          📚 CHAPTER NAVIGATION                               ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

| Previous Chapter | Current Chapter | Next Chapter |
|-----------------|-----------------|--------------|
| Ch29: Python Automation | **Ch30: Security Tools Overview** | Ch31: Hydra Password Cracking |

### Related Topics in This Module

| Chapter | Topic | Relevance |
|---------|-------|-----------|
| Ch31 | Hydra Password Cracking | Online brute-force tool |
| Ch32 | Hydra Advanced | Advanced Hydra techniques |
| Ch33 | John the Ripper | Offline hash cracking |
| Ch34 | SQLMap Basics | SQL injection automation |
| Ch35 | Metasploit Framework | Exploitation framework |
| Ch36 | PhoneSploit & ADB | Mobile security testing |
| Ch37 | Social Engineering Toolkit | Human layer attacks |
| Ch38 | WiFi Security Tools | Wireless penetration testing |

### Prerequisites from Other Modules

| Module | Chapter | Why It's Needed |
|--------|---------|-----------------|
| Module 1 | Termux Basics | Terminal fundamentals |
| Module 2 | Linux Commands | Command-line proficiency |
| Module 3 | Networking Basics | Network protocols understanding |
| Module 4 | Python Programming | Scripting for automation |

---

## 🏆 BONUS ADVANCED CONTENT

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                        🚀 ADVANCED SECURITY TECHNIQUES                       ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 🔥 Technique 1: Building a Custom Security Lab

```bash
# Complete Lab Setup Script
#!/bin/bash
# security_lab_setup.sh - Automated security lab setup

echo "[*] Setting up Security Lab Environment..."

# Update system
pkg update && pkg upgrade -y

# Install essential security tools
pkg install -y nmap hydra john sqlmap netcat curl wget git python

# Create directory structure
mkdir -p ~/security_lab/{tools,wordlists,scans,reports,loot}

# Download essential wordlists
cd ~/security_lab/wordlists
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
tar -xzf rockyou.txt.tar.gz

# Install additional tools via pip
pip install impacket requests beautifulsoup4

# Create aliases for quick access
cat >> ~/.bashrc << 'EOF'
# Security Lab Aliases
alias lab='cd ~/security_lab'
alias scan='nmap -sV -sC'
alias crack='hydra -l admin -P ~/security_lab/wordlists/rockyou.txt'
alias sql='sqlmap --batch --random-agent'
EOF

source ~/.bashrc

echo "[+] Security Lab Setup Complete!"
echo "[+] Lab location: ~/security_lab"
```

**Key Benefits:**
- Organized directory structure
- Pre-downloaded wordlists
- Quick-access aliases
- Ready for testing

### 🔥 Technique 2: Automated Reconnaissance Script

```bash
#!/bin/bash
# recon.sh - Automated reconnaissance script

TARGET=$1

if [ -z "$TARGET" ]; then
    echo "Usage: ./recon.sh <domain>"
    exit 1
fi

echo "[*] Starting reconnaissance for: $TARGET"

# Create output directory
mkdir -p ~/security_lab/scans/$TARGET

# DNS Enumeration
echo "[*] DNS Enumeration..."
dig $TARGET +short > ~/security_lab/scans/$TARGET/dns.txt
dig $TARGET ANY +noall +answer >> ~/security_lab/scans/$TARGET/dns.txt

# WHOIS Information
echo "[*] WHOIS Lookup..."
whois $TARGET > ~/security_lab/scans/$TARGET/whois.txt

# Subdomain Enumeration (basic)
echo "[*] Checking common subdomains..."
for sub in www mail ftp admin blog dev staging; do
    if host $sub.$TARGET &>/dev/null; then
        echo "$sub.$TARGET" >> ~/security_lab/scans/$TARGET/subdomains.txt
    fi
done

# Port Scanning
echo "[*] Port Scanning..."
nmap -T4 -F $TARGET > ~/security_lab/scans/$TARGET/nmap_quick.txt

# Technology Detection
echo "[*] Technology Detection..."
curl -sI https://$TARGET | grep -i "server\|x-" > ~/security_lab/scans/$TARGET/headers.txt

echo "[+] Reconnaissance complete!"
echo "[+] Results saved to: ~/security_lab/scans/$TARGET/"
```

**Usage:**
```bash
chmod +x recon.sh
./recon.sh example.com
```

### 🔥 Technique 3: Professional Report Template

```markdown
# Penetration Test Report

## Executive Summary
- **Client:** [Client Name]
- **Date:** [Testing Date]
- **Scope:** [Scope Description]
- **Overall Risk Rating:** [Critical/High/Medium/Low]

## Key Findings Summary
| Finding | Severity | Status |
|---------|----------|--------|
| [Finding 1] | Critical | Open |
| [Finding 2] | High | Open |

## Detailed Findings

### Finding 1: [Title]
**Severity:** Critical  
**CVSS Score:** 9.8  
**Affected Systems:** [List]

**Description:**
[Detailed description of the vulnerability]

**Proof of Concept:**
```
[Commands/screenshots demonstrating the vulnerability]
```

**Impact:**
[Business impact analysis]

**Remediation:**
[Step-by-step fix recommendations]

## Methodology
- Reconnaissance
- Scanning
- Exploitation
- Post-Exploitation
- Reporting

## Tools Used
| Tool | Purpose | Version |
|------|---------|---------|
| Nmap | Port Scanning | 7.94 |
| Burp Suite | Web Testing | 2023.x |

## Appendix
- Full Scan Results
- Screenshots
- Tool Outputs
```

**Report Best Practices:**
1. Clear executive summary
2. Actionable recommendations
3. Evidence-based findings
4. Risk prioritization
5. Professional formatting

---

## 📝 CHAPTER SUMMARY CHECKLIST

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                      ✅ CHAPTER 30 COMPLETION CHECKLIST                      ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### Knowledge Checkpoints

- [ ] Understand ethical hacking definition and legal requirements
- [ ] Know the difference between white hat, black hat, and gray hat hackers
- [ ] Familiar with PTES and OWASP frameworks
- [ ] Understand the 5 phases of penetration testing
- [ ] Know tool categories: recon, scanning, exploitation, post-exploitation
- [ ] Understand which tools work in Termux vs need proot/root
- [ ] Know how to set up a security lab environment
- [ ] Understand wordlists and their importance
- [ ] Know legal requirements for penetration testing
- [ ] Understand documentation and reporting requirements

### Practical Tasks

- [ ] Install all basic security tools (Nmap, Hydra, John, SQLMap)
- [ ] Download and set up rockyou.txt wordlist
- [ ] Create organized directory structure for security work
- [ ] Set up account on TryHackMe or HackTheBox
- [ ] Complete at least one beginner room/challenge
- [ ] Practice Nmap basic scans
- [ ] Create a sample penetration test report template
- [ ] Document your lab setup for future reference

### Before Moving to Chapter 31

- [ ] Completed interactive quiz with 80%+ score
- [ ] Attempted at least 2 real-world scenarios
- [ ] Set up security tools environment
- [ ] Registered on practice platform
- [ ] Understood legal and ethical boundaries

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 30
Title: Security Tools Overview | Ethical Hacking Introduction | T3rmuxk1ng
Duration: 20-25 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 1:00]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Aaj hum shuru kar rahe hain Module 6 - Security! Ye module bahut 
important hai kyunki isme hum seekhenge ethical hacking tools, 
security testing, aur penetration testing - sab kuch Termux pe.

Ye chapter ek FOUNDATION hai. Isme hum cover karenge:
- Ethical hacking kya hai
- Security testing methodology
- Tools categories
- Kya tools Termux mein kaam karte hain
- Kya tools ke liye proot chahiye
- Lab environment kaise setup karein
- Legal considerations

Agar aap cybersecurity mein career banana chahte ho, ye chapter 
 bahut important hai. Play button dabaiye, video like karein, 
aur channel subscribe karein!

---

[SECTION 1: ETHICAL HACKING INTRODUCTION - 1:00 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle sawal - Ethical Hacking kya hai?

Simple shabdon mein - Ethical Hacking wo hacking hai jo PERMISSION 
ke saath ki jaati hai. Purpose? Security dhundhna, vulnerabilities 
identify karna, aur systems ko secure banana.

┌─────────────────────────────────────────────────────────────────────────┐
│                    ETHICAL HACKER VS MALICIOUS HACKER                    │
├────────────────────────┬────────────────────────────────────────────────┤
│ Ethical Hacker (White) │ Malicious Hacker (Black Hat)                   │
├────────────────────────┼────────────────────────────────────────────────┤
│ ✅ Permission le ke    │ ❌ Bina permission ke attack karta hai         │
│ ✅ Security test karta │ ❌ Data churata hai, damage karta hai          │
│ ✅ Report banata hai   │ ❌ Apni gain ke liye kaam karta hai            │
│ ✅ Legal hai           │ ❌ Illegal hai, jail ho sakti hai              │
│ ✅ Certified (CEH, etc)│ ❌ Koi certification nahi                       │
│ ✅ Company hire karti  │ ❌ Police dhundti hai                          │
└────────────────────────┴────────────────────────────────────────────────┘

Ethical Hacker kehte hain - White Hat Hacker. Ye wo log hain jo 
companies ke liye security test karte hain, bugs dhundhte hain, 
aur report dete hain taaki company apni security improve kar sake.

Bug Bounty programs aaj kal bahut popular hain. Companies like 
Google, Facebook, Microsoft - ye sab bug bounty programs chalate 
hain jisme aap vulnerability dhundh ke PAISE kama sakte ho!

Ethical Hacking ki process ye hai:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SECURITY TESTING LIFECYCLE                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌──────┐ │
│   │ SCOPE   │───▶│ RECON   │───▶│ SCAN    │───▶│ EXPLOIT │───▶│REPORT│ │
│   │ DEFINE  │    │ NAIS-   │    │ VULN    │    │ ACCESS  │    │ DOC  │ │
│   └─────────┘    └─────────┘    └─────────┘    └─────────┘    └──────┘ │
│       │              │              │              │             │      │
│       ▼              ▼              ▼              ▼             ▼      │
│   Written        Passive/        Active        Controlled    Detailed   │
│   Permission     Active          Scanning      Exploit      Report      │
│   Scope          Info            Ports         Access       Fixes      │
│   Boundaries     Gathering       Services      Maintain     Timeline   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Ye cycle har penetration test mein follow hoti hai.

---

[SECTION 2: SECURITY TESTING METHODOLOGY - 5:00 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Ab baat karte hain METHODOLOGY ki. Ye bahut important hai samajhna.

Professional security testing mein kuch standard frameworks use 
hote hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    PENETRATION TESTING FRAMEWORKS                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. PTES (Penetration Testing Execution Standard)                       │
│     - Pre-engagement Interactions                                       │
│     - Intelligence Gathering                                            │
│     - Threat Modeling                                                   │
│     - Vulnerability Analysis                                            │
│     - Exploitation                                                      │
│     - Post Exploitation                                                 │
│     - Reporting                                                         │
│                                                                          │
│  2. OWASP (Open Web Application Security Project)                       │
│     - Web application testing standard                                  │
│     - OWASP Top 10 vulnerabilities                                      │
│     - Testing guide with 90+ test cases                                 │
│                                                                          │
│  3. NIST Cybersecurity Framework                                        │
│     - Identify, Protect, Detect, Respond, Recover                       │
│     - Enterprise-level security                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Practical testing phases ye hote hain:

PHASE 1: RECONNAISSANCE (Information Gathering)
───────────────────────────────────────────────
Ye first step hai. Target ke baare mein jitna info ekatha 
kar sakte ho.

Types:
- Passive Recon - Direct contact nahi, public info collect
  • WHOIS lookup
  • Google dorking
  • Social media
  • DNS enumeration

- Active Recon - Direct interaction with target
  • Port scanning
  • Service enumeration
  • Network mapping

PHASE 2: SCANNING & ENUMERATION
────────────────────────────────
Target ko actively scan karna:

- Port Scanning (Nmap)
  • Open ports dhundhna
  • Services identify karna
  • OS detection

- Vulnerability Scanning
  • Known CVEs check karna
  • Misconfigurations dhundhna
  • Weak points identify

PHASE 3: EXPLOITATION
─────────────────────
Vulnerabilities ka faayda uthana - ETHICALLY!

- Exploit development/use
- Payload delivery
- Gaining access
- Privilege escalation

PHASE 4: POST-EXPLOITATION
──────────────────────────
Access ke baad kya?

- Data collection
- Persistence maintain
- Lateral movement
- Evidence collection

PHASE 5: REPORTING
──────────────────
Sabse important phase!

- Executive summary
- Technical details
- Vulnerability description
- Remediation steps
- Risk rating

---

[SECTION 3: LEGAL CONSIDERATIONS - 9:00 to 12:00]
─────────────────────────────────────────────────────────────────────────────

AB SABSE IMPORTANT TOPIC - LEGAL ASPECTS!

⚠️ YEHAN DHYAN DO - YE BAHUT IMPORTANT HAI! ⚠️

┌─────────────────────────────────────────────────────────────────────────┐
│                    ⛔ LEGAL WARNING ⛔                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Unauthorized hacking ILLEGAL hai!                                       │
│                                                                          │
│  India mein:                                                             │
│  • IT Act 2000, Section 66 - Computer hacking                           │
│  • Section 66A - Punishment for sending offensive messages              │
│  • Section 66C - Identity theft                                          │
│  • Section 66D - Cheating by personation                                │
│  • Section 67 - Publishing obscene information                          │
│                                                                          │
│  Punishment:                                                             │
│  • Imprisonment up to 3 years                                           │
│  • Fine up to ₹5 lakh                                                   │
│  • Criminal record for life                                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Sahi tareeka ye hai:

✅ WRITTEN PERMISSION
   - Always get written authorization
   - Define scope clearly
   - Get signed NDA

✅ SCOPE DOCUMENT
   - IP ranges to test
   - Domains included
   - Tools allowed
   - Time window
   - What NOT to test

✅ RULES OF ENGAGEMENT
   - Testing hours
   - Communication protocol
   - Emergency contacts
   - Data handling rules

✅ LEGAL PROTECTION
   - Professional indemnity insurance
   - Contract with liability clauses
   - Data protection compliance

┌─────────────────────────────────────────────────────────────────────────┐
│                    ✅ ETHICAL HACKING CHECKLIST                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Test se PEHLE:                                                          │
│  □ Written permission signed                                            │
│  □ Scope clearly defined                                                │
│  □ Start and end dates mentioned                                        │
│  □ Emergency contact list                                               │
│  □ Legal documents reviewed                                             │
│                                                                          │
│  Test ke DURAN:                                                          │
│  □ Stay within scope                                                    │
│  □ Document everything                                                  │
│  □ Don't destroy data                                                   │
│  □ Report critical issues immediately                                   │
│                                                                          │
│  Test ke BAAD:                                                           │
│  □ Submit detailed report                                               │
│  □ Remove all access/tools                                              │
│  □ Securely delete test data                                            │
│  □ Follow up on fixes                                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 4: SECURITY TOOLS CATEGORIES - 12:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

Ab baat karte hain tools ki. Security tools ko categories 
mein divide karte hain:

┌─────────────────────────────────────────────────────────────────────────┐
│                    SECURITY TOOLS CATEGORIES                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. INFORMATION GATHERING (Reconnaissance)                              │
│  ───────────────────────────────────────────                            │
│  • Nmap - Network scanning, port scanning                               │
│  • whois - Domain information                                           │
│  • dig, nslookup - DNS queries                                          │
│  • theHarvester - Email and subdomain enumeration                       │
│  • Maltego - OSINT framework                                            │
│  • Shodan - Internet-connected devices search                           │
│                                                                          │
│  2. VULNERABILITY SCANNING                                              │
│  ──────────────────────────                                             │
│  • Nessus - Professional vulnerability scanner                          │
│  • OpenVAS - Open source vulnerability scanner                          │
│  • Nikto - Web server scanner                                           │
│  • WPScan - WordPress vulnerability scanner                             │
│  • SQLMap - SQL injection detection                                     │
│                                                                          │
│  3. PASSWORD CRACKING                                                   │
│  ───────────────────────                                                │
│  • John the Ripper - Password hash cracker                              │
│  • Hydra - Network logon cracker                                        │
│  • Hashcat - Advanced GPU-based cracker                                 │
│  • Ophcrack - Rainbow table cracker                                     │
│  • Crunch - Wordlist generator                                          │
│                                                                          │
│  4. EXPLOITATION                                                        │
│  ─────────────                                                          │
│  • Metasploit Framework - Exploitation framework                        │
│  • ExploitDB - Exploit database                                         │
│  • Searchsploit - Local exploit search                                  │
│  • BeEF - Browser exploitation                                          │
│  • Social Engineering Toolkit (SET)                                     │
│                                                                          │
│  5. POST-EXPLOITATION                                                   │
│  ───────────────────────                                                │
│  • Empire - Post-exploitation framework                                 │
│  • Mimikatz - Credential extraction                                     │
│  • PowerSploit - PowerShell framework                                   │
│  • Netcat - Reverse shells, file transfer                              │
│  • Weevely - Web shell                                                  │
│                                                                          │
│  6. WIRELESS SECURITY                                                   │
│  ─────────────────────                                                  │
│  • Aircrack-ng - WiFi security suite                                    │
│  • Wifite - Automated wireless attacks                                  │
│  • Kismet - Wireless detector                                           │
│  • Reaver - WPS attacks                                                 │
│                                                                          │
│  7. WEB APPLICATION SECURITY                                            │
│  ───────────────────────────                                            │
│  • Burp Suite - Web application proxy                                   │
│  • OWASP ZAP - Free alternative to Burp                                 │
│  • Gobuster - Directory brute forcing                                   │
│  • Dirb - Directory enumeration                                         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 5: TOOLS IN TERMUX VS PROOT - 16:00 to 19:00]
─────────────────────────────────────────────────────────────────────────────

Ab important sawal - Kaun se tools Termux mein directly kaam 
karte hain, aur kaun se tools ke liye proot ya root chahiye?

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX NATIVE TOOLS (No Root Required)                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✅ DIRECTLY WORKS IN TERMUX:                                            │
│                                                                          │
│  Information Gathering:                                                  │
│  ├── nmap         - pkg install nmap                                    │
│  ├── whois        - pkg install whois                                   │
│  ├── dig          - pkg install dnsutils                                │
│  ├── curl         - pkg install curl                                    │
│  └── git          - pkg install git                                     │
│                                                                          │
│  Password Tools:                                                         │
│  ├── hydra        - pkg install hydra                                   │
│  ├── john         - pkg install john                                    │
│  ├── crunch       - pkg install crunch                                  │
│  └── hashcat     - Limited, needs specific setup                        │
│                                                                          │
│  Network Tools:                                                          │
│  ├── netcat       - pkg install netcat                                  │
│  ├── wget         - pkg install wget                                    │
│  ├── openssl      - pkg install openssl                                 │
│  └── proxychains  - pkg install proxychains                             │
│                                                                          │
│  Web Tools:                                                              │
│  ├── sqlmap       - pip install sqlmap                                  │
│  ├── nikto        - pkg install nikto                                   │
│  └── whatweb      - pkg install whatweb                                 │
│                                                                          │
│  Programming:                                                            │
│  ├── python       - pkg install python                                  │
│  ├── nodejs       - pkg install nodejs                                  │
│  ├── ruby         - pkg install ruby                                    │
│  └── perl         - pkg install perl                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│                    TOOLS REQUIRING PROOT/ROOT                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ⚠️ NEED PROOT-DISTRO (Kali/Ubuntu in Termux):                          │
│                                                                          │
│  ├── metasploit-framework   - Full framework, heavy                     │
│  ├── burp-suite            - Java-based, needs GUI                      │
│  ├── aircrack-ng           - Wireless injection (needs root)            │
│  ├── wireshark             - Packet capture                             │
│  ├── maltego               - GUI-based OSINT                            │
│  ├── armitage              - Metasploit GUI                             │
│  └── beef-xss              - Browser exploitation                       │
│                                                                          │
│  ⚠️ NEED ACTUAL ROOT (Superuser):                                       │
│                                                                          │
│  ├── aircrack-ng (injection mode)                                       │
│  ├── bettercap               - Network attack tool                      │
│  ├── wireshark (live capture)                                           │
│  ├── iptables modifications  - Firewall manipulation                    │
│  └── kernel-level tools                                                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Proot-distro kya hai? Ye Termux ke andar ek full Linux distro 
run karne ka tareeka hai - bina root ke. Isme aap Kali Linux, 
Ubuntu, Debian install kar sakte ho.

Installation:
    pkg install proot-distro
    proot-distro install kali
    proot-distro login kali

---

[SECTION 6: SETTING UP LAB ENVIRONMENT - 19:00 to 22:00]
─────────────────────────────────────────────────────────────────────────────

Practice ke liye aapko LAB ENVIRONMENT chahiye. Ye bahut 
important hai - kabhi bhi real systems pe practice NA KAREIN 
bina permission ke!

┌─────────────────────────────────────────────────────────────────────────┐
│                    SECURITY LAB SETUP OPTIONS                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  OPTION 1: VULNERABLE VIRTUAL MACHINES                                  │
│  ─────────────────────────────────────                                  │
│  • Metasploitable 2/3 - Intentionally vulnerable Linux                  │
│  • DVWA (Damn Vulnerable Web App) - Web security practice               │
│  • OWASP WebGoat - Web application security                             │
│  • VulnHub - Hundreds of vulnerable VMs                                 │
│  • HackTheBox - Online practice platform                                │
│  • TryHackMe - Beginner-friendly labs                                   │
│                                                                          │
│  OPTION 2: LOCAL DOCKER CONTAINERS                                      │
│  ──────────────────────────────                                         │
│  Docker pe vulnerable apps run kar sakte ho:                            │
│                                                                          │
│  # DVWA                                                                 │
│  docker run --rm -it -p 80:80 vulnerables/web-dvwa                      │
│                                                                          │
│  # OWASP Juice Shop                                                     │
│  docker run --rm -p 3000:3000 bkimminich/juice-shop                    │
│                                                                          │
│  OPTION 3: TERMUX LOCALHOST PRACTICE                                    │
│  ─────────────────────────────────                                      │
│  Termux pe bhi local vulnerable apps host kar sakte ho:                 │
│                                                                          │
│  # Simple PHP vulnerable app                                            │
│  pkg install php apache2                                                │
│  # Setup DVWA locally                                                   │
│                                                                          │
│  OPTION 4: ONLINE PLATFORMS (Recommended for Beginners)                 │
│  ─────────────────────────────────────────────                          │
│  • TryHackMe.com - Free rooms, guided learning                          │
│  • HackTheBox.com - More advanced, real-world scenarios                 │
│  • PortSwigger Academy - Web security labs (FREE)                       │
│  • OverTheWire.org - Wargames, CLI practice                             │
│  • PicoCTF.org - CTF for beginners                                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Metasploitable setup (for PC):
    1. Download Metasploitable 2 (FREE)
    2. Install VirtualBox or VMware
    3. Import the VM
    4. Network: Host-only or NAT
    5. IP address: Usually 192.168.x.x

---

[SECTION 7: WORDLISTS - 22:00 to 24:00]
─────────────────────────────────────────────────────────────────────────────

Password cracking aur brute forcing ke liye WORDLISTS chahiye.

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMMON WORDLISTS                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ROCKYOU.TXT (Most Famous)                                              │
│  ─────────────────────────                                              │
│  • 14.3 million passwords                                               │
│  • From 2009 RockYou data breach                                        │
│  • Size: ~134 MB compressed, 134 MB uncompressed                        │
│  • Good for common passwords                                            │
│                                                                          │
│  Download:                                                               │
│  wget https://github.com/brannondorsey/naive-hashcat/                  │
│       releases/download/data/rockyou.txt                               │
│                                                                          │
│  SECLISTS (Comprehensive Collection)                                    │
│  ─────────────────────────────────                                      │
│  • Multiple wordlists                                                   │
│  • Usernames, passwords, directories, etc.                              │
│  • Size: ~735 MB                                                        │
│                                                                          │
│  pkg install seclists                                                   │
│  # Lists located at: $PREFIX/share/seclists/                           │
│                                                                          │
│  OTHER POPULAR WORDLISTS:                                                │
│  ─────────────────────────                                              │
│  • crackstation.txt - 1.5 billion passwords                            │
│  • darkweb2017.txt - From dark web leaks                               │
│  • probable-v2-top1575.txt - Most common passwords                     │
│  • dirb wordlists - Directory enumeration                              │
│  • raft-* wordlists - Various categories                               │
│                                                                          │
│  GENERATE CUSTOM WORDLISTS:                                              │
│  ──────────────────────────                                             │
│  crunch 8 8 -t hacker@@ -o custom.txt                                  │
│  # Creates 8-char passwords starting with "hacker"                     │
│                                                                          │
│  cewl http://target.com -w wordlist.txt                                │
│  # Generate wordlist from website content                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 8: INSTALLING SECURITY TOOLS - 24:00 to 27:00]
─────────────────────────────────────────────────────────────────────────────

Ab dekhte hain kuch common tools kaise install karte hain Termux mein:

[SCREEN: Termux Terminal]

# First, update everything
pkg update && pkg upgrade -y

# Install essential tools
pkg install git wget curl python -y

# Install Nmap
pkg install nmap -y

# Install Hydra
pkg install hydra -y

# Install John the Ripper
pkg install john -y

# Install SQLMap
pip install sqlmap

# Install Netcat
pkg install netcat -y

# Install additional tools
pkg install ncat nikto whatweb -y

# Install crunch for wordlist generation
pkg install crunch -y

# Install hashcat (may need specific setup)
# pkg install hashcat

After installation, verify:
    nmap --version
    hydra -h
    john --help
    sqlmap --version

---

[SECTION 9: DOCUMENTATION & REPORTING - 27:00 to 29:00]
─────────────────────────────────────────────────────────────────────────────

Security testing mein DOCUMENTATION bahut important hai.

┌─────────────────────────────────────────────────────────────────────────┐
│                    PENETRATION TEST REPORT STRUCTURE                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. EXECUTIVE SUMMARY                                                   │
│     - High-level overview for management                                │
│     - Risk assessment summary                                           │
│     - Key findings                                                      │
│                                                                          │
│  2. SCOPE & METHODOLOGY                                                 │
│     - What was tested                                                   │
│     - Tools used                                                        │
│     - Testing dates                                                     │
│                                                                          │
│  3. TECHNICAL FINDINGS                                                  │
│     - Detailed vulnerability descriptions                               │
│     - Severity ratings (Critical/High/Medium/Low)                      │
│     - Evidence (screenshots, logs)                                      │
│                                                                          │
│  4. EXPLOITATION DETAILS                                                │
│     - How vulnerabilities were exploited                                │
│     - Impact assessment                                                 │
│     - Steps to reproduce                                                │
│                                                                          │
│  5. REMEDIATION RECOMMENDATIONS                                         │
│     - How to fix each vulnerability                                     │
│     - Priority order                                                    │
│     - References                                                        │
│                                                                          │
│  6. APPENDICES                                                          │
│     - Tool outputs                                                      │
│     - Full scan results                                                 │
│     - Additional notes                                                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

Tools for documentation:
- CherryTree - Note taking
- Obsidian - Markdown notes
- Dradis - Reporting framework
- Markdown + Git - Version controlled reports

---

[SECTION 10: CONTINUING EDUCATION - 29:00 to 31:00]
─────────────────────────────────────────────────────────────────────────────

Cybersecurity field bahut dynamic hai. Har din naye vulnerabilities 
aate hain, new tools release hote hain.

┌─────────────────────────────────────────────────────────────────────────┐
│                    LEARNING RESOURCES                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  FREE PLATFORMS:                                                         │
│  ├── TryHackMe.com - Beginner to advanced                              │
│  ├── HackTheBox.com - Real-world challenges                            │
│  ├── PortSwigger Academy - Web security                                │
│  ├── OverTheWire.org - Wargames                                        │
│  ├── PicoCTF.org - CTF practice                                        │
│  └── Cybrary.it - Free courses                                         │
│                                                                          │
│  CERTIFICATIONS:                                                         │
│  ├── CEH (Certified Ethical Hacker)                                    │
│  ├── OSCP (Offensive Security Certified Professional)                   │
│  ├── CompTIA Security+                                                  │
│  ├── eJPT (eLearnSecurity Junior Penetration Tester)                   │
│  └── PNPT (Practical Network Penetration Tester)                       │
│                                                                          │
│  YOUTUBE CHANNELS:                                                       │
│  ├── NetworkChuck                                                       │
│  ├── IppSec (HackTheBox walkthroughs)                                   │
│  ├── LiveOverflow                                                       │
│  ├── John Hammond                                                       │
│  └── The Cyber Mentor                                                   │
│                                                                          │
│  NEWS & UPDATES:                                                         │
│  ├── TheHackerNews.com                                                  │
│  ├── KrebsOnSecurity.com                                                │
│  ├── SecurityWeek.com                                                   │
│  └── Reddit r/netsec, r/AskNetsec                                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

---

[SECTION 11: SUMMARY - 31:00 to 33:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 30 complete! Let's summarize:

✅ Ethical Hacking kya hai - Permission-based security testing
✅ Security Testing Methodology - Phases of testing
✅ Legal Considerations - IT Act, authorization, scope
✅ Tools Categories - Recon, scanning, exploitation, etc.
✅ Termux Native Tools - Nmap, Hydra, John, SQLMap
✅ Tools Needing Proot - Metasploit, Aircrack, etc.
✅ Lab Environment - VMs, Docker, online platforms
✅ Wordlists - Rockyou, SecLists, custom generation
✅ Documentation - Report structure, tools
✅ Continuing Education - Platforms, certifications

Important commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 30 - KEY COMMANDS                             │
├─────────────────────────────────────────────────────────────────────────┤
│ pkg install nmap hydra john          │ Install security tools         │
│ pip install sqlmap                   │ Install SQLMap via pip         │
│ proot-distro install kali            │ Install Kali in Termux         │
│ proot-distro login kali              │ Login to Kali environment      │
│ nmap -sV <target>                    │ Service version scan           │
│ hydra -l user -P wordlist <target>   │ Brute force attack             │
│ john --wordlist=rockyou.txt hash     │ Password cracking              │
│ sqlmap -u <url>                      │ SQL injection test             │
│ wget <wordlist-url>                  │ Download wordlist              │
└─────────────────────────────────────────────────────────────────────────┘

Next chapters mein hum detail mein seekhenge:
- Chapter 31: Hydra Password Cracking
- Chapter 32: Hydra Advanced Techniques
- Chapter 33: John the Ripper
- Chapter 34: SQLMap Basics
- Chapter 35: Metasploit Framework

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 31!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. Ethical Hacking Framework

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ETHICAL HACKING LIFECYCLE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                        ┌──────────────────┐                             │
│                        │   PRE-ENGAGEMENT  │                             │
│                        │  • Scope Define   │                             │
│                        │  • Contracts      │                             │
│                        │  • Legal Review   │                             │
│                        └────────┬─────────┘                             │
│                                 │                                        │
│                                 ▼                                        │
│    ┌──────────────────────────────────────────────────────────┐         │
│    │                    INTELLIGENCE GATHERING                │         │
│    │  ┌─────────────────┐        ┌─────────────────┐         │         │
│    │  │  PASSIVE RECON  │        │  ACTIVE RECON   │         │         │
│    │  │  • OSINT        │        │  • Port Scans   │         │         │
│    │  │  • WHOIS        │        │  • Service Enum │         │         │
│    │  │  • Social Media │        │  • Banner Grab  │         │         │
│    │  └─────────────────┘        └─────────────────┘         │         │
│    └──────────────────────────────────────────────────────────┘         │
│                                 │                                        │
│                                 ▼                                        │
│    ┌──────────────────────────────────────────────────────────┐         │
│    │                  VULNERABILITY ANALYSIS                   │         │
│    │  • Automated Scanning (Nessus, OpenVAS)                  │         │
│    │  • Manual Testing                                        │         │
│    │  • CVE Database Lookup                                   │         │
│    │  • Configuration Review                                  │         │
│    └──────────────────────────────────────────────────────────┘         │
│                                 │                                        │
│                                 ▼                                        │
│    ┌──────────────────────────────────────────────────────────┐         │
│    │                      EXPLOITATION                         │         │
│    │  • Exploit Development/Selection                         │         │
│    │  • Payload Delivery                                      │         │
│    │  • Gaining Access                                        │         │
│    │  • Privilege Escalation                                  │         │
│    └──────────────────────────────────────────────────────────┘         │
│                                 │                                        │
│                                 ▼                                        │
│    ┌──────────────────────────────────────────────────────────┐         │
│    │                  POST-EXPLOITATION                        │         │
│    │  • Information Gathering                                 │         │
│    │  • Persistence Mechanisms                                │         │
│    │  • Lateral Movement                                      │         │
│    │  • Data Exfiltration (Proof)                             │         │
│    └──────────────────────────────────────────────────────────┘         │
│                                 │                                        │
│                                 ▼                                        │
│                        ┌──────────────────┐                             │
│                        │    REPORTING     │                             │
│                        │  • Findings      │                             │
│                        │  • Evidence      │                             │
│                        │  • Remediation   │                             │
│                        └──────────────────┘                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Security Tools by Category

#### Information Gathering Tools

| Tool | Purpose | Termux Native | Install Command |
|------|---------|---------------|-----------------|
| Nmap | Network/port scanning | ✅ Yes | `pkg install nmap` |
| whois | Domain info lookup | ✅ Yes | `pkg install whois` |
| dig | DNS queries | ✅ Yes | `pkg install dnsutils` |
| theHarvester | OSINT gathering | ✅ Yes | `pip install theHarvester` |
| DNSenum | DNS enumeration | ✅ Yes | `pip install dnspython` |
| Sublist3r | Subdomain enumeration | ✅ Yes | `pip install sublist3r` |
| WhatWeb | Web technology identification | ✅ Yes | `pkg install whatweb` |

#### Vulnerability Scanning Tools

| Tool | Purpose | Termux Native | Install Command |
|------|---------|---------------|-----------------|
| Nikto | Web server scanner | ✅ Yes | `pkg install nikto` |
| WPScan | WordPress scanner | ✅ Yes | `gem install wpscan` |
| SQLMap | SQL injection | ✅ Yes | `pip install sqlmap` |
| Nuclei | Vulnerability scanner | ✅ Yes | `pkg install nuclei` |
| OpenVAS | Full vulnerability scanner | ❌ Proot | `apt install openvas` |

#### Password Cracking Tools

| Tool | Purpose | Termux Native | Install Command |
|------|---------|---------------|-----------------|
| Hydra | Network logon cracker | ✅ Yes | `pkg install hydra` |
| John | Password hash cracker | ✅ Yes | `pkg install john` |
| Hashcat | GPU-based cracker | ⚠️ Limited | Special setup |
| Crunch | Wordlist generator | ✅ Yes | `pkg install crunch` |
| CeWL | Custom wordlist from URL | ✅ Yes | `gem install cewl` |

#### Exploitation Tools

| Tool | Purpose | Termux Native | Install Command |
|------|---------|---------------|-----------------|
| Metasploit | Exploitation framework | ❌ Proot | See Chapter 35 |
| Searchsploit | Local exploit search | ✅ Yes | `pkg install exploitdb` |
| Netcat | Reverse shells | ✅ Yes | `pkg install netcat` |
| Netcat-alt | Alternative netcat | ✅ Yes | `pkg install ncat` |
| Weevely | Web shell | ✅ Yes | `pip install weevely3` |

### 3. Lab Environment Setup

#### Option A: Vulnerable VMs

```bash
# Download Metasploitable 2
# URL: https://sourceforge.net/projects/metasploitable/

# In VirtualBox:
1. Create new VM
2. Type: Linux, Version: Ubuntu (32-bit)
3. RAM: 512 MB minimum
4. Use existing VMDK file
5. Network: Host-Only Adapter

# Default credentials:
Username: msfadmin
Password: msfadmin
```

#### Option B: Docker Containers

```bash
# Install Docker on PC first
# Then run vulnerable containers:

# DVWA (Damn Vulnerable Web App)
docker run --rm -it -p 80:80 vulnerables/web-dvwa

# OWASP Juice Shop
docker run --rm -p 3000:3000 bkimminich/juice-shop

# OWASP WebGoat
docker run --rm -p 8080:8080 -p 9090:9090 webgoat/webgoat

# Vulnerable WordPress
docker run --rm -p 80:80 wpscan/vulnerablewordpress
```

#### Option C: Termux Local Practice

```bash
# Install PHP and Apache in Termux
pkg install php apache2

# Start Apache
apachectl start

# Download DVWA
git clone https://github.com/digininja/DVWA.git
cd DVWA
# Configure and access via localhost
```

### 4. Wordlist Management

```bash
# Create wordlists directory
mkdir -p ~/wordlists
cd ~/wordlists

# Download Rockyou
wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt

# Download SecLists (via package)
pkg install seclists
ls $PREFIX/share/seclists/

# Common SecLists paths:
# Passwords: $PREFIX/share/seclists/Passwords/
# Usernames: $PREFIX/share/seclists/Usernames/
# Discovery: $PREFIX/share/seclists/Discovery/

# Generate custom wordlist with Crunch
crunch 6 8 -t pass@@@ -o custom_passwords.txt
# Creates 6-8 char passwords starting with "pass"

# Generate from website content
cewl http://example.com -m 6 -w site_words.txt
# -m: minimum word length
```

### 5. Legal Compliance Checklist

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PRE-ENGAGEMENT CHECKLIST                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  DOCUMENTATION REQUIRED:                                                 │
│                                                                          │
│  □ Rules of Engagement (RoE) Document                                   │
│    ├── Testing scope (IP ranges, domains, applications)                │
│    ├── Testing timeline (start/end dates, times)                       │
│    ├── Testing types allowed (black/gray/white box)                    │
│    ├── Tools restrictions                                               │
│    ├── Communication protocols                                          │
│    └── Emergency procedures                                             │
│                                                                          │
│  □ Authorization Letter                                                  │
│    ├── Company letterhead                                               │
│    ├── Signed by authorized personnel                                   │
│    ├── Specific systems authorized for testing                          │
│    ├── Duration of authorization                                        │
│    └── Contact information                                              │
│                                                                          │
│  □ Non-Disclosure Agreement (NDA)                                       │
│    ├── Confidentiality terms                                            │
│    ├── Data handling requirements                                       │
│    ├── Return/destruction of data                                       │
│    └── Legal remedies for breach                                        │
│                                                                          │
│  □ Scope Document                                                        │
│    ├── In-scope targets                                                 │
│    ├── Out-of-scope targets                                             │
│    ├── Testing limitations                                              │
│    ├── Third-party notifications required                               │
│    └── Service level agreements                                         │
│                                                                          │
│  BEFORE TESTING:                                                         │
│  □ Verify authorization is current                                      │
│  □ Confirm testing window                                               │
│  □ Set up communication channels                                        │
│  □ Prepare incident response plan                                       │
│  □ Document baseline system state                                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 COMMANDS REFERENCE

### Tool Installation Commands

```bash
# Update Termux first
pkg update && pkg upgrade -y

# Install essential packages
pkg install git wget curl python -y

# Information Gathering Tools
pkg install nmap -y           # Network scanner
pkg install whois -y          # Domain information
pkg install dnsutils -y       # DNS tools (dig, nslookup)
pkg install net-tools -y      # Network utilities
pkg install netcat -y         # Netcat
pkg install whatweb -y        # Web technology identification

# Password Tools
pkg install hydra -y          # Network logon cracker
pkg install john -y           # Password cracker
pkg install crunch -y         # Wordlist generator

# Web Security Tools
pkg install nikto -y          # Web server scanner
pip install sqlmap            # SQL injection tool

# Exploitation Tools
pkg install exploitdb -y      # Searchsploit
pkg install ncat -y           # Ncat (improved netcat)

# Additional Tools
pkg install openssl -y        # SSL/TLS toolkit
pkg install proxychains-ng -y # Proxy chaining
pkg install hydra -y          # Already mentioned

# Install SecLists wordlists
pkg install seclists
```

### Nmap Scanning Commands

```bash
# Basic scan
nmap 192.168.1.1

# Scan multiple targets
nmap 192.168.1.1 192.168.1.2 192.168.1.3

# Scan a range
nmap 192.168.1.1-254

# Scan a subnet
nmap 192.168.1.0/24

# Port scanning
nmap -p 80 192.168.1.1           # Specific port
nmap -p 80,443,22 192.168.1.1    # Multiple ports
nmap -p 1-1000 192.168.1.1       # Port range
nmap -p- 192.168.1.1             # All 65535 ports

# Service detection
nmap -sV 192.168.1.1             # Service versions
nmap -sV -sC 192.168.1.1         # With default scripts

# OS detection
nmap -O 192.168.1.1

# Aggressive scan
nmap -A 192.168.1.1

# Scan types
nmap -sS 192.168.1.1    # SYN scan (stealth)
nmap -sT 192.168.1.1    # TCP connect scan
nmap -sU 192.168.1.1    # UDP scan

# Output options
nmap -oN scan.txt 192.168.1.1      # Normal output
nmap -oX scan.xml 192.168.1.1      # XML output
nmap -oA scan 192.168.1.1          # All formats

# Fast scan
nmap -F 192.168.1.1                # Top 100 ports

# Verbose output
nmap -v 192.168.1.1
nmap -vv 192.168.1.1
```

### Hydra Commands

```bash
# SSH brute force
hydra -l username -P wordlist.txt ssh://192.168.1.1

# FTP brute force
hydra -l username -P wordlist.txt ftp://192.168.1.1

# HTTP POST form
hydra -l username -P wordlist.txt 192.168.1.1 http-post-form \
    "/login:user=^USER^&pass=^PASS^:Invalid"

# Multiple usernames
hydra -L users.txt -P wordlist.txt ssh://192.168.1.1

# Specific port
hydra -l username -P wordlist.txt -s 2222 ssh://192.168.1.1

# Verbose output
hydra -V -l username -P wordlist.txt ssh://192.168.1.1

# Show help
hydra -h
```

### John the Ripper Commands

```bash
# Basic cracking
john --wordlist=rockyou.txt hashes.txt

# Show cracked passwords
john --show hashes.txt

# Incremental mode (brute force)
john --incremental hashes.txt

# Specific format
john --format=raw-md5 --wordlist=rockyou.txt hashes.txt

# List available formats
john --list=formats

# Benchmark
john --test
```

### SQLMap Commands

```bash
# Basic test
sqlmap -u "http://example.com/page?id=1"

# Specify parameter
sqlmap -u "http://example.com/page?id=1&cat=2" -p id

# POST request
sqlmap -u "http://example.com/login" --data="user=admin&pass=test"

# With cookies
sqlmap -u "http://example.com/page?id=1" --cookie="PHPSESSID=abc123"

# Specify database
sqlmap -u "http://example.com/page?id=1" --dbs

# Get tables
sqlmap -u "http://example.com/page?id=1" -D database_name --tables

# Get columns
sqlmap -u "http://example.com/page?id=1" -D database_name -T table_name --columns

# Dump data
sqlmap -u "http://example.com/page?id=1" -D database_name -T table_name --dump

# Risk and level
sqlmap -u "http://example.com/page?id=1" --risk=3 --level=5
```

### Proot-Distro Commands

```bash
# Install proot-distro
pkg install proot-distro

# List available distros
proot-distro list

# Install a distro
proot-distro install kali
proot-distro install ubuntu
proot-distro install debian
proot-distro install arch

# Login to distro
proot-distro login kali

# Login with shared storage
proot-distro login --shared-tmp kali

# Remove a distro
proot-distro remove kali

# Backup a distro
proot-distro backup kali

# Restore a distro
proot-distro restore kali-backup.tar.gz
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Install Security Tools

```bash
# Task: Install and verify all basic security tools

# Step 1: Update Termux
pkg update && pkg upgrade -y

# Step 2: Install core tools
pkg install git wget curl python -y

# Step 3: Install network tools
pkg install nmap netcat whois dnsutils -y

# Step 4: Install password tools
pkg install hydra john crunch -y

# Step 5: Install web tools
pkg install nikto whatweb -y
pip install sqlmap

# Step 6: Verify installations
nmap --version
hydra -h | head -5
john --help | head -5
sqlmap --version
nikto -help | head -5

# Expected: All tools should show version/help without errors
```

### Exercise 2: Nmap Local Scanning

```bash
# Task: Scan your local network

# Step 1: Find your IP range
ifconfig 2>/dev/null || ip addr

# Step 2: Scan localhost
nmap localhost

# Step 3: Quick scan of local network
# Replace 192.168.1 with your network
nmap -F 192.168.1.0/24

# Step 4: Service detection on a host
# Replace IP with one found above
nmap -sV -sC <discovered-ip>

# Step 5: Save results
nmap -oN scan_results.txt -F 192.168.1.0/24

# Expected: List of hosts and services
```

### Exercise 3: Wordlist Setup

```bash
# Task: Set up wordlists for password testing

# Step 1: Create directory
mkdir -p ~/wordlists
cd ~/wordlists

# Step 2: Download rockyou
wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt

# Step 3: Check the file
wc -l rockyou.txt
head -20 rockyou.txt

# Step 4: Install SecLists
pkg install seclists -y

# Step 5: Explore SecLists
ls $PREFIX/share/seclists/
ls $PREFIX/share/seclists/Passwords/
ls $PREFIX/share/seclists/Usernames/

# Step 6: Generate custom wordlist
crunch 8 8 -t pass@@@ -o custom_pass.txt
cat custom_pass.txt

# Expected: Multiple wordlists ready for use
```

### Exercise 4: Proot-Distro Setup

```bash
# Task: Set up Kali Linux in Termux

# Step 1: Install proot-distro
pkg install proot-distro -y

# Step 2: Update proot-distro
proot-distro update

# Step 3: Install Kali
proot-distro install kali

# Wait for installation (may take several minutes)

# Step 4: Login to Kali
proot-distro login kali

# Step 5: Update Kali
apt update && apt upgrade -y

# Step 6: Install a tool (example: metasploit)
apt install metasploit-framework -y

# Step 7: Exit Kali
exit

# Expected: Working Kali environment in Termux
```

### Exercise 5: Create Test Hash

```bash
# Task: Create and crack a test hash with John

# Step 1: Create test hash (MD5 of "password")
echo -n "password" | md5sum | awk '{print $1}' > test_hash.txt
echo "Hash created: $(cat test_hash.txt)"

# Step 2: Format for John
# John needs username:hash format
echo "testuser:$(cat test_hash.txt)" > hash_for_john.txt
cat hash_for_john.txt

# Step 3: Crack with John
john --format=raw-md5 --wordlist=~/wordlists/rockyou.txt hash_for_john.txt

# Step 4: Show results
john --show hash_for_john.txt

# Expected: Should crack and show "password"
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "Unable to locate package" for security tools

```bash
# Cause: Package not in default repository

# Solution 1: Update repositories
pkg update

# Solution 2: Search for alternative name
pkg search <toolname>

# Solution 3: Use pip for Python tools
pip install <toolname>

# Solution 4: Install from source
git clone <repository-url>
cd <repository>
pip install -r requirements.txt
python setup.py install
```

### Problem 2: Nmap not finding hosts

```bash
# Cause: Network configuration or permissions

# Solution 1: Check network connectivity
ping -c 3 8.8.8.8

# Solution 2: Use different scan technique
nmap -sT <target>  # TCP connect scan instead of SYN

# Solution 3: Check if nmap is installed correctly
which nmap
nmap --version

# Solution 4: Try localhost first
nmap localhost
```

### Problem 3: Hydra connection issues

```bash
# Cause: Target not reachable or service not running

# Solution 1: Verify target is up
ping <target>

# Solution 2: Verify service is running
nmap -p <port> <target>

# Solution 3: Use verbose mode
hydra -V -l user -P wordlist ssh://<target>

# Solution 4: Check for firewall
# Try different port if non-standard
hydra -s 2222 -l user -P wordlist ssh://<target>
```

### Problem 4: John not cracking hashes

```bash
# Cause: Wrong format or weak wordlist

# Solution 1: Verify hash format
john --list=formats | grep -i <format>

# Solution 2: Use correct format flag
john --format=raw-sha256 --wordlist=rockyou.txt hash.txt

# Solution 3: Try incremental mode
john --incremental hash.txt

# Solution 4: Verify hash is correct
cat hash.txt
# Should be in format: username:hash
```

### Problem 5: SQLMap not detecting injection

```bash
# Cause: Parameter not injectable or WAF blocking

# Solution 1: Increase level and risk
sqlmap -u "<url>" --level=5 --risk=3

# Solution 2: Try different technique
sqlmap -u "<url>" --technique=BEUST

# Solution 3: Use random user agent
sqlmap -u "<url>" --random-agent

# Solution 4: Check with tamper scripts
sqlmap -u "<url>" --tamper=space2comment

# Solution 5: Increase timeout
sqlmap -u "<url>" --timeout=30
```

### Problem 6: Proot-distro installation fails

```bash
# Cause: Network issues or storage

# Solution 1: Check storage
df -h
# Clear cache if needed
pkg clean

# Solution 2: Check network
ping -c 3 github.com

# Solution 3: Try different mirror
# Edit sources if needed

# Solution 4: Reinstall proot-distro
pkg uninstall proot-distro
pkg install proot-distro

# Solution 5: Use specific version
proot-distro install --override-alias ubuntu ubuntu
```

### Problem 7: Tool requires root

```bash
# Cause: Tool needs elevated privileges

# Solution 1: Check if proot version exists
pkg search <toolname>

# Solution 2: Use proot-distro
proot-distro login kali
apt install <toolname>

# Solution 3: Find alternative
# Many tools have alternatives that work without root

# Solution 4: Check if features can be disabled
<toolname> --help | grep -i root
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Professional Style**
```
┌────────────────────────────────────┐
│  [Dark Background with Matrix]     │
│                                    │
│   🔒 SECURITY TOOLS                │
│   COMPLETE OVERVIEW                │
│                                    │
│   ✓ Nmap • Hydra • John            │
│   ✓ Metasploit • SQLMap            │
│   ✓ Lab Setup Guide                │
│                                    │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Tools Showcase**
```
┌────────────────────────────────────┐
│  TERMUX SECURITY ARSENAL           │
│  ─────────────────────────────     │
│                                    │
│  [Nmap]  [Hydra]  [John]           │
│  [SQLMap] [Metasploit]             │
│                                    │
│  🛡️ ETHICAL HACKING GUIDE 🛡️       │
│                                    │
│  Chapter 30 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

**Option C: Warning Style**
```
┌────────────────────────────────────┐
│  ⚠️ BEFORE YOU HACK ⚠️             │
│                                    │
│  LEGAL GUIDE + TOOLS SETUP         │
│                                    │
│  📋 Scope & Authorization          │
│  🛠️ Tool Installation              │
│  🎯 Lab Environment                │
│                                    │
│  WATCH NOW → Chapter 30            │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
🔒 Termux Full Course - Chapter 30: Security Tools Overview | Ethical Hacking Introduction

🔥 In this video you'll learn:
• Ethical hacking kya hai
• Security testing methodology phases
• Legal considerations aur IT Act
• Security tools categories
• Termux mein kaun se tools kaam karte hain
• Proot-distro setup for advanced tools
• Lab environment setup
• Wordlists download aur management
• Documentation aur reporting basics

⏱️ Timestamps:
0:00 - Introduction
1:00 - Ethical Hacking Introduction
5:00 - Security Testing Methodology
9:00 - Legal Considerations
12:00 - Security Tools Categories
16:00 - Termux Native vs Proot Tools
19:00 - Lab Environment Setup
22:00 - Wordlists Management
24:00 - Installing Security Tools
27:00 - Documentation & Reporting
29:00 - Continuing Education
31:00 - Summary

📥 Commands from this video:
pkg install nmap hydra john
pip install sqlmap
proot-distro install kali
wget https://rockyou.txt

📚 Full Course Playlist:
[PLAYLIST LINK]

🔗 Resources:
• TryHackMe: https://tryhackme.com
• HackTheBox: https://hackthebox.com
• OWASP: https://owasp.org
• SecLists: https://github.com/danielmiessler/SecLists

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #SecurityTools #EthicalHacking #T3rmuxk1ng #PenetrationTesting #CyberSecurity #TermuxHindi #Nmap #Hydra #Metasploit

---
⚠️ Disclaimer: This video is for educational purposes only. Always obtain proper written authorization before testing any systems. Unauthorized hacking is illegal. Use these skills responsibly and ethically.
```

### Tags List

```
termux, termux security tools, ethical hacking, penetration testing, 
cybersecurity, termux hacking, nmap tutorial, hydra password cracking, 
john the ripper, sqlmap tutorial, metasploit termux, security tools overview,
termux course, termux hindi, termux tutorial, hacking tools, 
security testing methodology, proot distro, kali linux termux,
vulnerability scanning, password cracking, information gathering,
osint tools, bug bounty, ctf, hacking lab, t3rmuxk1ng,
ethical hacking course, cyber security career, penetration testing guide
```

### Hashtags

```
#Termux #EthicalHacking #PenetrationTesting #CyberSecurity #SecurityTools 
#Nmap #Hydra #JohnTheRipper #SQLMap #Metasploit #TermuxCourse #HindiTutorial 
#BugBounty #CTF #InfoSec #HackingTools #TermuxHindi #T3rmuxk1ng
```

---

## 📚 ADDITIONAL RESOURCES

### Online Practice Platforms

| Platform | Level | Cost | Focus |
|----------|-------|------|-------|
| TryHackMe | Beginner-Advanced | Free/Paid | Guided learning |
| HackTheBox | Intermediate-Advanced | Free/Paid | Real-world scenarios |
| PortSwigger Academy | All levels | Free | Web security |
| OverTheWire | Beginner-Intermediate | Free | Linux/CLI |
| PicoCTF | Beginner | Free | CTF basics |
| VulnHub | Intermediate | Free | Vulnerable VMs |

### Certifications Path

```
Entry Level:
├── CompTIA Security+
├── eJPT (eLearnSecurity)
└── CEH (EC-Council)

Intermediate:
├── OSCP (Offensive Security)
├── eCPPT (eLearnSecurity)
└── PNPT (TCM Security)

Advanced:
├── OSWE (Offensive Security)
├── OSEE (Offensive Security)
└── CRTO (Certified Red Team Operator)
```

### Useful GitHub Repositories

```bash
# Awesome Security
git clone https://github.com/sbilly/awesome-security

# Payloads All The Things
git clone https://github.com/swisskyrepo/PayloadsAllTheThings

# SecLists
git clone https://github.com/danielmiessler/SecLists

# Penetration Testing Guide
git clone https://github.com/owasp/owasp-testing-guide

# GTFOBins
# Visit: https://gtfobins.github.io/
```

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

**Q1: What is the primary difference between ethical hacking and malicious hacking?**
- A) Tools used
- B) Permission and authorization
- C) Operating system
- D) Network type

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) Permission and authorization**

Ethical hacking is performed with explicit written permission from the system owner, while malicious hacking is unauthorized and illegal. The tools and techniques may be identical, but the legal authorization makes all the difference.
</details>

---

**Q2: Which Indian IT Act section deals with computer hacking?**
- A) Section 65
- B) Section 66
- C) Section 67
- D) Section 68

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) Section 66**

Section 66 of the IT Act 2000 specifically deals with computer hacking and prescribes punishment of imprisonment up to 3 years and/or fine up to ₹5 lakh.
</details>

---

**Q3: What type of tool is John the Ripper?**
- A) Network scanner
- B) Web vulnerability scanner
- C) Offline password hash cracker
- D) WiFi cracker

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: C) Offline password hash cracker**

John the Ripper is an offline password cracking tool that works on password hashes, unlike Hydra which is an online cracker that tests passwords against live services.
</details>

---

**Q4: What does PTES stand for in security testing?**
- A) Penetration Testing Execution Standard
- B) Professional Testing Essential Standard
- C) Penetration Tool Execution System
- D) Privacy Testing Essential Standard

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: A) Penetration Testing Execution Standard**

PTES is a standard framework for conducting penetration tests, covering pre-engagement, intelligence gathering, threat modeling, vulnerability analysis, exploitation, post-exploitation, and reporting.
</details>

---

**Q5: Which tool requires actual root access (not just proot) on Android?**
- A) Nmap
- B) Hydra
- C) Aircrack-ng (injection mode)
- D) SQLMap

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: C) Aircrack-ng (injection mode)**

While basic tools like Nmap, Hydra, and SQLMap work in Termux without root, aircrack-ng's packet injection mode requires actual kernel-level access that only true root (superuser) provides.
</details>

---

**Q6: What is the minimum recommended password length for WiFi security?**
- A) 8 characters
- B) 10 characters
- C) 12 characters
- D) 6 characters

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: C) 12 characters**

A minimum of 12 characters with mixed case, numbers, and symbols is recommended for WPA2/WPA3 networks. Shorter passwords are vulnerable to dictionary and brute-force attacks.
</details>

---

**Q7: In the security testing lifecycle, which phase comes after scanning?**
- A) Reporting
- B) Exploitation
- C) Reconnaissance
- D) Scope Definition

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) Exploitation**

The typical penetration testing lifecycle follows: Scope Definition → Reconnaissance → Scanning → Exploitation → Post-Exploitation → Reporting.
</details>

---

**Q8: What is rockyou.txt?**
- A) A network scanning tool
- B) A wordlist with 14.3 million passwords
- C) An encryption algorithm
- D) A security framework

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) A wordlist with 14.3 million passwords**

rockyou.txt is the most famous password wordlist, created from the 2009 RockYou data breach. It contains 14,344,391 real passwords and is essential for password cracking practice.
</details>

---

**Q9: How do you install Kali Linux in Termux using proot?**
- A) `apt install kali`
- B) `proot-distro install kali`
- C) `pkg install kali-linux`
- D) `git clone kali`

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) `proot-distro install kali`**

First install proot-distro with `pkg install proot-distro`, then use `proot-distro install kali` to set up the Kali environment, and finally `proot-distro login kali` to access it.
</details>

---

**Q10: What is the correct order of penetration testing phases?**
- A) Exploit → Scan → Report → Recon
- B) Recon → Scan → Exploit → Report
- C) Report → Recon → Scan → Exploit
- D) Scan → Recon → Report → Exploit

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) Recon → Scan → Exploit → Report**

The standard penetration testing methodology follows this order: Reconnaissance (information gathering) → Scanning (identifying vulnerabilities) → Exploitation (testing vulnerabilities) → Reporting (documenting findings).
</details>

---

**Q11: Which tool is primarily used for network port scanning?**
- A) John
- B) Hydra
- C) Nmap
- D) Crunch

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: C) Nmap**

Nmap (Network Mapper) is the industry-standard tool for network discovery and security auditing. It can perform port scanning, service detection, OS fingerprinting, and vulnerability detection.
</details>

---

**Q12: What should be obtained BEFORE starting any penetration test?**
- A) New tools
- B) Written authorization
- C) Social media accounts
- D) Employee information

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) Written authorization**

Written authorization is absolutely mandatory before any penetration test. Testing without permission is illegal and can result in criminal charges, regardless of your intentions.
</details>

---

**Q13: What does OWASP stand for?**
- A) Open Web Application Security Project
- B) Online Web Application Security Protocol
- C) Organization for Web Application Security Practices
- D) Offensive Web Application Security Platform

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: A) Open Web Application Security Project**

OWASP is a nonprofit foundation that works to improve software security. Their OWASP Top 10 list is essential knowledge for web application security testing.
</details>

---

**Q14: Which tool would you use to create custom password wordlists?**
- A) Nmap
- B) Hydra
- C) Crunch
- D) Ncat

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: C) Crunch**

Crunch is a wordlist generator that creates custom wordlists based on specified character sets, patterns, and length requirements. It's essential for targeted password attacks.
</details>

---

**Q15: What is a CVE?**
- A) Common Vulnerabilities Enumeration
- B) Common Vulnerabilities and Exposures
- C) Computer Vulnerability Evaluation
- D) Certified Vulnerability Expert

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer: B) Common Vulnerabilities and Exposures**

CVE is a dictionary of publicly disclosed cybersecurity vulnerabilities. Each CVE has a unique identifier (like CVE-2021-44228 for Log4Shell) used to track and reference vulnerabilities.
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

**Q1: What is the difference between vulnerability assessment and penetration testing?**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
- **Vulnerability Assessment** is an automated process that identifies and reports known vulnerabilities without actively exploiting them. It provides a broad view of potential weaknesses.

- **Penetration Testing** goes further by actively exploiting vulnerabilities to determine real-world risk. It validates findings, tests security controls, and demonstrates business impact.

**Follow-up:** Which would you recommend for a company with limited security budget?

A vulnerability assessment is more cost-effective for initial assessment, but penetration testing provides actionable proof of vulnerabilities that can help justify security investments.
</details>

---

**Q2: Explain the concept of "defense in depth" in cybersecurity.**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
Defense in depth is a layered security approach where multiple security controls are placed throughout an IT system. If one layer fails, others provide protection.

**Layers include:**
1. Physical security (locks, access cards)
2. Network security (firewalls, IDS/IPS)
3. Host security (antivirus, patching)
4. Application security (input validation, encryption)
5. Data security (encryption, backups)

**Follow-up:** How would you apply this to a web application?

Use WAF, input validation, parameterized queries, encryption, access controls, logging, and regular security testing.
</details>

---

**Q3: What is the CIA triad? Explain each component.**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
- **Confidentiality:** Ensuring data is accessible only to authorized individuals. Implemented through encryption, access controls, and authentication.

- **Integrity:** Maintaining data accuracy and trustworthiness. Implemented through hashing, digital signatures, and access controls.

- **Availability:** Ensuring systems and data are accessible when needed. Implemented through redundancy, backups, and DDoS protection.

**Follow-up:** Which is most important for a hospital database?

All three are critical, but availability could be prioritized as life-saving systems need to be accessible 24/7, followed by integrity (correct patient data) and confidentiality (privacy).
</details>

---

**Q4: What is a zero-day vulnerability?**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
A zero-day vulnerability is a software security flaw unknown to the vendor and has no available patch. "Zero-day" refers to the number of days the vendor has known about the vulnerability.

**Risk factors:**
- No patch available
- Attackers may actively exploit it
- Organizations must rely on workarounds

**Mitigation strategies:**
- Virtual patching (WAF rules)
- Network segmentation
- Behavior-based detection
- Application whitelisting

**Follow-up:** How would you protect against zero-days?

Defense in depth, behavior monitoring, network segmentation, and rapid incident response capabilities.
</details>

---

**Q5: Explain the difference between symmetric and asymmetric encryption.**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**

| Aspect | Symmetric | Asymmetric |
|--------|-----------|------------|
| Keys | Same key for encrypt/decrypt | Different keys (public/private) |
| Speed | Faster | Slower |
| Key Distribution | Challenging | Easier |
| Examples | AES, DES, RC4 | RSA, ECC, Diffie-Hellman |

**Use cases:**
- Symmetric: Bulk data encryption, file encryption
- Asymmetric: Key exchange, digital signatures, SSL/TLS

**Follow-up:** Which is used for HTTPS?

Both! Asymmetric encryption (RSA/ECC) establishes the secure connection and exchanges keys, then symmetric encryption (AES) encrypts the actual data for performance.
</details>

---

**Q6: What is SQL injection and how do you prevent it?**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
SQL injection occurs when untrusted user input is concatenated into SQL queries, allowing attackers to manipulate database queries.

**Prevention methods:**
1. **Parameterized queries (Prepared statements)** - Primary defense
2. **Input validation** - Whitelist acceptable characters
3. **Least privilege** - Restrict database user permissions
4. **Stored procedures** - Encapsulate database logic
5. **ORM frameworks** - Abstract SQL queries

**Example vulnerable code:**
```python
# Vulnerable
query = "SELECT * FROM users WHERE id = " + user_input

# Secure
query = "SELECT * FROM users WHERE id = ?"
cursor.execute(query, (user_input,))
```

**Follow-up:** How would you test for SQL injection?

Use SQLMap for automated testing or manual injection attempts like `' OR '1'='1` and `' UNION SELECT`.
</details>

---

**Q7: What is a false positive and false negative in security testing?**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
- **False Positive:** A reported vulnerability that doesn't actually exist. This wastes time investigating non-issues.

- **False Negative:** An actual vulnerability that goes undetected. This leaves systems at risk.

**Impact:**
- False positives → Alert fatigue, wasted resources
- False negatives → Undetected risks, potential breaches

**Balancing:**
Most organizations prefer more false positives over false negatives for security-critical systems. Tuning scanners and validating findings manually helps reduce both.

**Follow-up:** How do you minimize false positives?

Manual verification, tool tuning, using multiple tools, and correlating results from different sources.
</details>

---

**Q8: What is the difference between black box, white box, and gray box testing?**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**

| Type | Knowledge Level | Advantage |
|------|-----------------|-----------|
| Black Box | No internal knowledge | Simulates real attacker |
| White Box | Full source code access | Comprehensive coverage |
| Gray Box | Partial knowledge | Balanced approach |

**Use cases:**
- Black Box: External penetration testing
- White Box: Code review, security audit
- Gray Box: Authenticated testing with limited documentation

**Follow-up:** Which would be most effective for finding logic flaws?

White box testing provides source code access, making it easier to identify business logic vulnerabilities that might be missed in black box testing.
</details>

---

**Q9: What is privilege escalation? Name two types.**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
Privilege escalation is the act of exploiting vulnerabilities to gain elevated access beyond what was initially granted.

**Types:**
1. **Vertical Escalation:** Gaining higher privileges (user → admin → root)
2. **Horizontal Escalation:** Accessing other users' data at same privilege level

**Common techniques:**
- Kernel exploits
- Misconfigured sudo permissions
- SUID binaries
- Credential reuse
- Unpatched vulnerabilities

**Follow-up:** How do you prevent privilege escalation?

Principle of least privilege, regular patching, proper configuration, monitoring, and privilege separation.
</details>

---

**Q10: What is the purpose of a Web Application Firewall (WAF)?**

<details>
<summary>📝 Click to Reveal Answer</summary>

**Answer:**
A WAF protects web applications by filtering and monitoring HTTP traffic between the web application and the Internet.

**Protection against:**
- SQL injection
- Cross-site scripting (XSS)
- Cross-site request forgery (CSRF)
- Session hijacking
- Directory traversal

**Types:**
- Network-based WAF (hardware)
- Host-based WAF (software)
- Cloud-based WAF (service)

**Limitations:**
- Cannot fix application vulnerabilities
- May impact performance
- Requires tuning to avoid false positives

**Follow-up:** Can a WAF replace secure coding?

No. WAF provides defense in depth but should not replace secure coding practices. Applications should be secure by design.
</details>

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Setting Up Your First Security Lab

```
╔════════════════════════════════════════════════════════════════╗
║                    🏗️ SECURITY LAB SETUP                       ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  Situation: You want to practice ethical hacking legally      ║
║                                                                ║
║  Solution: Set up a vulnerable lab environment               ║
║                                                                ║
║  Commands:                                                     ║
║  ─────────────────────────────────────────────────────────── ║
║  # Install Docker in proot                                    ║
║  pkg install proot-distro                                     ║
║  proot-distro install ubuntu                                  ║
║  proot-distro login ubuntu                                    ║
║  apt install docker.io                                        ║
║                                                                ║
║  # Run DVWA (Damn Vulnerable Web App)                        ║
║  docker run --rm -it -p 80:80 vulnerables/web-dvwa           ║
║                                                                ║
║  # Access at http://localhost                                 ║
║  # Login: admin / password                                    ║
║                                                                ║
║  Benefits: Safe, legal, educational environment              ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

---

### Scenario 2: Performing Basic Network Reconnaissance

```
╔════════════════════════════════════════════════════════════════╗
║                    🔍 NETWORK RECONNAISSANCE                    ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  Situation: You need to discover hosts on your network       ║
║                                                                ║
║  Solution: Use Nmap for network discovery                    ║
║                                                                ║
║  Commands:                                                     ║
║  ─────────────────────────────────────────────────────────── ║
║  # Install Nmap                                               ║
║  pkg install nmap                                             ║
║                                                                ║
║  # Ping sweep to find live hosts                             ║
║  nmap -sn 192.168.1.0/24                                      ║
║                                                                ║
║  # Quick port scan                                            ║
║  nmap -F 192.168.1.1                                          ║
║                                                                ║
║  # Service version detection                                  ║
║  nmap -sV 192.168.1.1                                         ║
║                                                                ║
║  # Save results to file                                       ║
║  nmap -sV -oN scan_results.txt 192.168.1.1                   ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

---

### Scenario 3: Password Strength Testing

```
╔════════════════════════════════════════════════════════════════╗
║                    🔐 PASSWORD STRENGTH TEST                    ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  Situation: Testing password security of your own SSH server  ║
║                                                                ║
║  Solution: Use Hydra for authorized password testing          ║
║                                                                ║
║  Commands:                                                     ║
║  ─────────────────────────────────────────────────────────── ║
║  # Install Hydra                                              ║
║  pkg install hydra                                            ║
║                                                                ║
║  # Create a small test wordlist                               ║
║  echo -e "admin\npassword\n123456\ntest" > test_words.txt    ║
║                                                                ║
║  # Test your own SSH (with permission!)                      ║
║  hydra -l testuser -P test_words.txt ssh://localhost         ║
║                                                                ║
║  # Check for null passwords                                  ║
║  hydra -l admin -e n ssh://your-server-ip                    ║
║                                                                ║
║  Result: Identify weak passwords before attackers do         ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

---

### Scenario 4: Documenting Security Findings

```
╔════════════════════════════════════════════════════════════════╗
║                    📋 SECURITY DOCUMENTATION                    ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  Situation: Creating a penetration test report template       ║
║                                                                ║
║  Solution: Use structured markdown documentation             ║
║                                                                ║
║  Template Structure:                                           ║
║  ─────────────────────────────────────────────────────────── ║
║  # Executive Summary                                          ║
║  - Risk Rating: Critical/High/Medium/Low                     ║
║  - Summary of findings                                        ║
║  - Business impact                                           ║
║                                                                ║
║  # Technical Findings                                         ║
║  - Vulnerability name                                        ║
║  - CVE reference (if applicable)                             ║
║  - Affected systems                                          ║
║  - Proof of concept                                          ║
║  - Remediation steps                                         ║
║                                                                ║
║  # Tools Used                                                 ║
║  - nmap -sV target                                           ║
║  - hydra -l user -P wordlist ssh://target                    ║
║                                                                ║
║  Save as: pentest_report_YYYY-MM-DD.md                       ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

---

### Scenario 5: Wordlist Management

```
╔════════════════════════════════════════════════════════════════╗
║                    📚 WORDLIST MANAGEMENT                       ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  Situation: Building and organizing password wordlists        ║
║                                                                ║
║  Solution: Download and create custom wordlists              ║
║                                                                ║
║  Commands:                                                     ║
║  ─────────────────────────────────────────────────────────── ║
║  # Create wordlist directory                                 ║
║  mkdir -p ~/wordlists && cd ~/wordlists                      ║
║                                                                ║
║  # Download rockyou.txt                                      ║
║  wget https://github.com/danielmiessler/SecLists/...         ║
║       raw/master/Passwords/Leaked-Databases/rockyou.txt      ║
║                                                                ║
║  # Install seclists package                                  ║
║  pkg install seclists                                        ║
║                                                                ║
║  # Generate custom wordlist with Crunch                      ║
║  pkg install crunch                                          ║
║  crunch 8 8 -t company@@ -o company_passwords.txt           ║
║                                                                ║
║  # Count passwords in wordlist                               ║
║  wc -l rockyou.txt                                           ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

---

## ⚠️ SECURITY BEST PRACTICES

### ✅ DO's for Ethical Hacking

| Practice | Description |
|----------|-------------|
| ✅ **Get written permission** | Always obtain explicit authorization before testing |
| ✅ **Define clear scope** | Document exactly what you will and won't test |
| ✅ **Document everything** | Keep detailed logs of all activities |
| ✅ **Stay within scope** | Don't test systems outside the agreement |
| ✅ **Report responsibly** | Disclose findings to authorized parties only |
| ✅ **Clean up after testing** | Remove tools, shells, and test data |
| ✅ **Maintain confidentiality** | Protect sensitive data discovered during testing |
| ✅ **Follow responsible disclosure** | Give vendors time to fix before public disclosure |
| ✅ **Keep tools updated** | Use latest versions for accurate results |
| ✅ **Practice in labs** | Test tools and techniques in safe environments |
| ✅ **Maintain certifications** | Keep CEH, OSCP, etc. current |
| ✅ **Follow the law** | Comply with local and international regulations |

### ❌ DON'Ts for Ethical Hacking

| Practice | Consequence |
|----------|-------------|
| ❌ **Test without permission** | Criminal charges, jail time |
| ❌ **Exceed scope** | Legal liability, contract breach |
| ❌ **Share credentials** | Privacy violation, legal action |
| ❌ **Destroy data** | Criminal charges, civil liability |
| ❌ **Install backdoors** | Criminal charges, reputation damage |
| ❌ **Publicize vulnerabilities** | Ethical violation, legal issues |
| ❌ **Use production systems** | Service disruption, legal liability |
| ❌ **Ignore findings** | Professional negligence |
| ❌ **Forget documentation** | Lost evidence, credibility issues |
| ❌ **Trust blindly** | Verify all authorizations in writing |

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: Security Testing Lifecycle

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        SECURITY TESTING LIFECYCLE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌──────────────┐     ┌──────────────┐     ┌──────────────┐               │
│   │   PLANNING   │────▶│ RECONNAISSANCE│────▶│   SCANNING   │               │
│   │              │     │              │     │              │               │
│   │ • Scope      │     │ • Passive    │     │ • Ports      │               │
│   │ • Rules      │     │ • Active     │     │ • Services   │               │
│   │ • Timeline   │     │ • OSINT      │     │ • Vulns      │               │
│   └──────────────┘     └──────────────┘     └──────────────┘               │
│          │                                          │                        │
│          │                                          ▼                        │
│   ┌──────────────┐     ┌──────────────┐     ┌──────────────┐               │
│   │  REPORTING   │◀────│POST-EXPLOIT  │◀────│ EXPLOITATION │               │
│   │              │     │              │     │              │               │
│   │ • Executive  │     │ • Maintain   │     │ • Exploit    │               │
│   │ • Technical  │     │ • Escalate   │     │ • Access     │               │
│   │ • Fixes      │     │ • Evidence   │     │ • Payload    │               │
│   └──────────────┘     └──────────────┘     └──────────────┘               │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### Diagram 2: Termux Security Tools Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     TERMUX SECURITY TOOLS ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                      NATIVE TERMUX (No Root)                         │   │
│   │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐       │   │
│   │  │  Nmap   │ │  Hydra  │ │  John   │ │ SQLMap  │ │ Netcat  │       │   │
│   │  └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘       │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                      │                                       │
│                                      ▼                                       │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    PROOT-DISTRO (Linux Environment)                  │   │
│   │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐   │   │
│   │  │ Metasploit  │ │  Burp Suite │ │ Aircrack-ng │ │   SET       │   │   │
│   │  │ (in Kali)   │ │ (in Kali)   │ │ (Monitor)   │ │ (Phishing)  │   │   │
│   │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                      │                                       │
│                                      ▼                                       │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                      ROOT REQUIRED (Superuser)                       │   │
│   │  ┌───────────────┐ ┌───────────────┐ ┌───────────────┐              │   │
│   │  │ Aircrack-ng   │ │   Bettercap   │ │    Wireshark  │              │   │
│   │  │ (Injection)   │ │  (MITM/ARP)   │ │ (Live Capture)│              │   │
│   │  └───────────────┘ └───────────────┘ └───────────────┘              │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### Diagram 3: Vulnerability Severity Classification

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    VULNERABILITY SEVERITY MATRIX                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   SEVERITY    │ CVSS SCORE │ IMPACT              │ EXAMPLES                 │
│   ────────────┼────────────┼─────────────────────┼───────────────────────── │
│   🔴 CRITICAL │ 9.0 - 10.0 │ System compromise   │ RCE, SQLi w/ file write  │
│               │            │ No user interaction │ Auth bypass, Root shell  │
│   ────────────┼────────────┼─────────────────────┼───────────────────────── │
│   🟠 HIGH     │ 7.0 - 8.9  │ Significant impact  │ SQLi, Privilege esc.     │
│               │            │ Requires user action│ Stored XSS, LFI          │
│   ────────────┼────────────┼─────────────────────┼───────────────────────── │
│   🟡 MEDIUM   │ 4.0 - 6.9  │ Limited impact      │ Reflected XSS, CSRF      │
│               │            │ Workaround exists   │ Info disclosure          │
│   ────────────┼────────────┼─────────────────────┼───────────────────────── │
│   🟢 LOW      │ 0.1 - 3.9  │ Minimal impact      │ Clickjacking             │
│               │            │ Barely exploitable  │ Verbose errors           │
│   ────────────┼────────────┼─────────────────────┼───────────────────────── │
│   ⚪ INFO     │ 0.0        │ No security impact  │ Missing security headers │
│               │            │ Best practice       │ Cookie flags missing     │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relationship |
|---------|-------|--------------|
| **Ch 25-29** | Network Tools | Prerequisite - Network basics |
| **Ch 31** | Hydra Password Cracking | Next - Password attack tool |
| **Ch 32** | Hydra Advanced | Next - Advanced techniques |
| **Ch 33** | John the Ripper | Next - Hash cracking |
| **Ch 34** | SQLMap Basics | Next - SQL injection |
| **Ch 35** | Metasploit Framework | Next - Exploitation |
| **Ch 36** | PhoneSploit & ADB | Next - Mobile security |
| **Ch 37** | Social Engineering Toolkit | Next - SE attacks |
| **Ch 38** | WiFi Security Tools | Next - Wireless security |
| **Ch 39+** | Advanced Modules | Future learning path |

### Learning Path:
```
Ch 30 (Overview) → Ch 31 (Hydra) → Ch 33 (John) → Ch 34 (SQLMap) → Ch 35 (Metasploit)
```

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Custom Nmap NSE Scripts

```bash
# Nmap Scripting Engine (NSE) allows custom security checks
# Location: /usr/share/nmap/scripts/

# Run all vulnerability scripts
nmap --script vuln 192.168.1.1

# Run specific category
nmap --script "safe and vuln" 192.168.1.1

# Custom script example (save as my-script.nse):
-- description = "Custom port check"
portrule = shortport.port_or_service(80, "http")
action = function(host, port)
    return "HTTP service found on " .. host.ip
end

# Run custom script
nmap --script my-script.nse 192.168.1.1
```

---

### Advanced Technique 2: Building Custom Wordlists

```bash
# Using Crunch for targeted wordlists
# Pattern: @ = lowercase, , = uppercase, % = digits, ^ = symbols

# Company-based: company + 2 digits
crunch 10 10 -t company%% -o company_pass.txt

# Year-based: word + year (common pattern)
crunch 12 12 -t password%%%% -o year_pass.txt

# Leetspeak variations
crunch 8 8 -t p@ssw0rd -o leet_pass.txt

# Using CeWL to generate from website
cewl http://target-site.com -w site_words.txt -m 6

# Combining wordlists
cat wordlist1.txt wordlist2.txt | sort -u > combined.txt
```

---

### Advanced Technique 3: Network Pivoting and Tunneling

```bash
# SSH Tunneling for pivoting

# Local port forwarding (access remote service locally)
ssh -L 8080:internal-server:80 user@jump-host

# Dynamic SOCKS proxy (full network access)
ssh -D 9050 user@jump-host

# Using Proxychains with SSH tunnel
# Edit /etc/proxychains.conf:
# socks5 127.0.0.1 9050

proxychains nmap -sT -Pn internal-network/24

# Through Termux with proot:
proot-distro login kali
# Then use SSH tunneling for advanced network testing
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### What You Learned:

- [ ] **Ethical Hacking Fundamentals**
  - [ ] Difference between ethical and malicious hacking
  - [ ] Importance of written permission
  - [ ] Legal requirements and consequences

- [ ] **Security Testing Methodology**
  - [ ] PTES framework phases
  - [ ] OWASP testing standards
  - [ ] NIST cybersecurity framework

- [ ] **Security Tools Categories**
  - [ ] Information gathering tools
  - [ ] Vulnerability scanning tools
  - [ ] Password cracking tools
  - [ ] Exploitation frameworks
  - [ ] Wireless security tools

- [ ] **Termux vs Proot Tools**
  - [ ] Native Termux tools (no root)
  - [ ] Proot-distro tools
  - [ ] Root-required tools

- [ ] **Lab Environment Setup**
  - [ ] Vulnerable VM options
  - [ ] Docker containers
  - [ ] Online practice platforms

- [ ] **Wordlist Management**
  - [ ] rockyou.txt and SecLists
  - [ ] Custom wordlist generation with Crunch

- [ ] **Documentation Skills**
  - [ ] Report structure
  - [ ] Evidence collection

- [ ] **Legal & Ethical Framework**
  - [ ] IT Act sections
  - [ ] Rules of engagement
  - [ ] Scope documentation

---

## 💡 PRO TIPS BOX

> 💡 **Pro Tip #1:** Always start with passive reconnaissance before active scanning. You'd be surprised how much information is publicly available without touching the target.

> 💡 **Pro Tip #2:** Document EVERYTHING from day one. Use tools like CherryTree or Obsidian to maintain detailed notes. Your future self will thank you during report writing.

> 💡 **Pro Tip #3:** Create a dedicated "tools" directory in your Termux setup with organized subdirectories for wordlists, scripts, payloads, and scan results.

> 💡 **Pro Tip #4:** Before using any tool on a target, test it in your lab environment first. Understand its output format, options, and potential impact.

> 💡 **Pro Tip #5:** Use `tmux` or `screen` in Termux for persistent sessions. Long-running scans won't be lost if Termux crashes or you need to switch apps.

> 💡 **Pro Tip #6:** Keep your tools updated! Run `pkg update && pkg upgrade` weekly, and check GitHub repos for the latest versions.

> 💡 **Pro Tip #7:** Build your own wordlist by combining rockyou.txt with target-specific words. Use tools like CUPP (Common User Passwords Profiler).

> 💡 **Pro Tip #8:** Learn to read source code! Many tools have options not documented in help menus. Check the source on GitHub.

> 💡 **Pro Tip #9:** Set up aliases for frequently used commands in your `~/.bashrc`. Save keystrokes and time.

> 💡 **Pro Tip #10:** Join security communities on Discord, Reddit, and Twitter. The field moves fast - stay connected to learn about new tools and techniques.

---

## 🔥 REAL WORLD APPLICATIONS

### Bug Bounty Scenarios

**Scenario 1: Reconnaissance for Bug Bounty**
```bash
# Step 1: Subdomain enumeration
subfinder -d target.com -o subdomains.txt

# Step 2: Check live subdomains
cat subdomains.txt | httprobe | tee live_subdomains.txt

# Step 3: Scan with Nmap
nmap -iL live_subdomains.txt -sV -oA scan_results

# Step 4: Identify technologies
whatweb -i live_subdomains.txt

# Step 5: Check for common vulnerabilities
nikto -host target.com
```

**Scenario 2: Pre-engagement Scope Documentation**
```
PENETRATION TEST SCOPE DOCUMENT
================================
Client: [Company Name]
Date: [Start Date] to [End Date]

AUTHORIZED TARGETS:
- IP Range: 192.168.1.0/24
- Domains: target.com, api.target.com
- Applications: Web Portal, Mobile App

OUT OF SCOPE:
- Production databases
- Third-party services
- Social engineering attacks

TOOLS AUTHORIZED:
- Nmap, Hydra, SQLMap
- Burp Suite
- Custom scripts

EMERGENCY CONTACT:
- Name: [Contact Person]
- Phone: [Number]
- Email: [Email]
```

### Penetration Testing Workflow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PROFESSIONAL PENTEST WORKFLOW                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   PHASE 1: PRE-ENGAGEMENT                                               │
│   ├── Sign contract and NDA                                             │
│   ├── Define scope document                                             │
│   ├── Get written authorization                                         │
│   └── Set up testing environment                                        │
│                                                                          │
│   PHASE 2: RECONNAISSANCE (1-2 days)                                    │
│   ├── Passive OSINT gathering                                           │
│   ├── Active scanning with Nmap                                         │
│   ├── Service enumeration                                               │
│   └── Technology fingerprinting                                         │
│                                                                          │
│   PHASE 3: VULNERABILITY ANALYSIS (2-3 days)                            │
│   ├── Automated vulnerability scanning                                  │
│   ├── Manual testing                                                    │
│   ├── False positive verification                                       │
│   └── Vulnerability prioritization                                      │
│                                                                          │
│   PHASE 4: EXPLOITATION (2-4 days)                                      │
│   ├── Develop/identify exploits                                         │
│   ├── Test exploits in lab                                              │
│   ├── Execute authorized exploits                                       │
│   └── Document evidence                                                 │
│                                                                          │
│   PHASE 5: POST-EXPLOITATION (1-2 days)                                 │
│   ├── Privilege escalation                                              │
│   ├── Lateral movement (if authorized)                                  │
│   ├── Data collection                                                   │
│   └── Clean up                                                          │
│                                                                          │
│   PHASE 6: REPORTING (2-3 days)                                         │
│   ├── Executive summary                                                 │
│   ├── Technical findings                                                │
│   ├── Risk assessment                                                   │
│   └── Remediation recommendations                                       │
│                                                                          │
│   PHASE 7: RE-TESTING (after fixes)                                     │
│   ├── Verify patches                                                    │
│   ├── Document remaining issues                                         │
│   └── Final report delivery                                             │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## ⚡ QUICK REFERENCE CARD

### Essential Security Tool Commands

| Tool | Purpose | Quick Command |
|------|---------|---------------|
| **Nmap** | Port Scanner | `nmap -sV -sC target.com` |
| **Hydra** | Password Cracker | `hydra -l user -P wordlist.txt ssh://target` |
| **John** | Hash Cracker | `john --wordlist=rockyou.txt hash.txt` |
| **SQLMap** | SQL Injection | `sqlmap -u "url?id=1" --dbs` |
| **Netcat** | Network Tool | `nc -lvnp 4444` |
| **Gobuster** | Dir Brute Force | `gobuster dir -u url -w wordlist.txt` |
| **Nikto** | Web Scanner | `nikto -h target.com` |
| **Crunch** | Wordlist Gen | `crunch 8 8 -t pass@@@ -o list.txt` |
| **Searchsploit** | Exploit Search | `searchsploit apache 2.4` |
| **Ncat** | Advanced Netcat | `ncat --ssl target 443` |

### Termux Security Tool Installation

```bash
# Update & Upgrade
pkg update && pkg upgrade -y

# Essential Tools
pkg install nmap hydra john netcat git wget curl python -y

# Web Tools
pkg install nikto whatweb gobuster -y

# Wordlists
pkg install seclists -y
pip install sqlmap

# Proot for Advanced Tools
pkg install proot-distro -y
proot-distro install kali
```

### Common Port Reference

| Port | Service | Security Focus |
|------|---------|----------------|
| 21 | FTP | Anonymous access, brute force |
| 22 | SSH | Brute force, key theft |
| 23 | Telnet | Cleartext credentials |
| 25 | SMTP | Email spoofing, relay |
| 80 | HTTP | Web vulnerabilities |
| 443 | HTTPS | SSL/TLS issues |
| 3306 | MySQL | SQL injection, brute force |
| 3389 | RDP | BlueKeep, brute force |
| 5432 | PostgreSQL | SQL injection |
| 8080 | HTTP Proxy | Web vulnerabilities |

### HTTP Status Codes for Security

| Code | Meaning | Security Implication |
|------|---------|---------------------|
| 200 | OK | Successful request |
| 301/302 | Redirect | Check redirect targets |
| 401 | Unauthorized | Authentication bypass attempt |
| 403 | Forbidden | Directory traversal, IDOR |
| 404 | Not Found | Hidden files/directories |
| 500 | Server Error | Information disclosure |
| 502/503 | Gateway Error | DoS possible |

---

## 🏆 BONUS: ADVANCED EXPLOITATION

### Setting Up Advanced Lab Environment

```bash
# Install Docker in proot environment
proot-distro login ubuntu
apt install docker.io -y
systemctl start docker

# Run vulnerable web applications
docker run -d -p 80:80 vulnerables/web-dvwa
docker run -d -p 3000:3000 bkimminich/juice-shop
docker run -d -p 8080:8080 webgoat/webgoat

# Access locally
# DVWA: http://localhost
# Juice Shop: http://localhost:3000
# WebGoat: http://localhost:8080/WebGoat
```

### Additional Powerful Tools

| Tool | Description | Installation |
|------|-------------|--------------|
| **Aircrack-ng** | WiFi Security Suite | `pkg install aircrack-ng` |
| **Bettercap** | Network Attack Tool | Requires root |
| **Metasploit** | Exploitation Framework | Via proot-distro |
| **Burp Suite** | Web Proxy | Requires GUI/Java |
| **Wireshark** | Packet Analysis | Requires root |
| **Nuclei** | Vulnerability Scanner | `go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest` |
| **Amass** | Subdomain Enumeration | `go install -v github.com/OWASP/Amass/v3/...@master` |
| **FFUF** | Web Fuzzer | `go install github.com/ffuf/ffuf@latest` |
| **Subfinder** | Subdomain Finder | `go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest` |

### Advanced Reconnaissance Automation Script

```bash
#!/bin/bash
# Auto-Recon Script for Bug Bounty
# Usage: ./autorecon.sh target.com

TARGET=$1
mkdir -p ~/recon/$TARGET
cd ~/recon/$TARGET

echo "[*] Starting reconnaissance for: $TARGET"

# Subdomain enumeration
echo "[+] Enumerating subdomains..."
subfinder -d $TARGET -o subdomains.txt
amass enum -passive -d $TARGET >> subdomains.txt
sort -u subdomains.txt -o subdomains.txt

# Check live hosts
echo "[+] Checking live hosts..."
cat subdomains.txt | httprobe | tee live_hosts.txt

# Port scanning
echo "[+] Scanning ports..."
nmap -iL live_hosts.txt -sV -T4 -oA nmap_scan

# Technology detection
echo "[+] Detecting technologies..."
whatweb -i live_hosts.txt | tee tech_detection.txt

# Screenshot (requires aquatone)
echo "[+] Taking screenshots..."
cat live_hosts.txt | aquatone -out screenshots/

echo "[!] Reconnaissance complete!"
echo "[*] Results saved in: ~/recon/$TARGET"
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### Key Concepts Mastered

- ✅ **Ethical Hacking Fundamentals**: Understanding the difference between white hat and black hat hackers, legal requirements, and authorization
- ✅ **Security Testing Methodology**: PTES, OWASP, NIST frameworks and the complete testing lifecycle
- ✅ **Tool Categories**: Information gathering, vulnerability scanning, password cracking, exploitation, and more
- ✅ **Termux vs Proot**: Which tools work natively vs which need additional setup
- ✅ **Lab Environment Setup**: Vulnerable VMs, Docker containers, and online platforms
- ✅ **Wordlists Management**: rockyou.txt, SecLists, and custom wordlist generation
- ✅ **Documentation**: Penetration test report structure and best practices

### Key Takeaways

1. **Permission is Non-Negotiable**: Never test without written authorization
2. **Documentation is Critical**: If it's not documented, it didn't happen
3. **Lab Practice First**: Always test tools in controlled environments
4. **Stay Updated**: Security field evolves rapidly, continuous learning is essential
5. **Legal Compliance**: Understand your local laws (IT Act 2000 for India)
6. **Ethics Matter**: Responsible disclosure protects everyone

---

## 🛡️ DEFENSIVE SECURITY: Protecting Against Attacks

### Network Security Hardening

```bash
# Firewall Configuration (Linux)
sudo ufw enable
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https

# Check open ports
sudo netstat -tulpn
sudo ss -tulpn

# Disable unnecessary services
sudo systemctl disable telnet
sudo systemctl disable ftp
```

### Password Security Best Practices

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PASSWORD SECURITY GUIDELINES                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ✅ DO:                                                                 │
│  ├── Minimum 12+ characters                                             │
│  ├── Mix uppercase, lowercase, numbers, symbols                        │
│  ├── Use password managers (Bitwarden, KeePass)                        │
│  ├── Enable 2FA everywhere possible                                     │
│  ├── Use unique passwords for each account                             │
│  └── Change passwords after breach notifications                       │
│                                                                          │
│  ❌ DON'T:                                                              │
│  ├── Use dictionary words                                               │
│  ├── Use personal information (birthdays, names)                       │
│  ├── Reuse passwords across accounts                                    │
│  ├── Share passwords via email/messaging                                │
│  ├── Write passwords on sticky notes                                    │
│  └── Use default passwords                                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### System Hardening Checklist

- [ ] Change default credentials on all devices
- [ ] Disable unused services and ports
- [ ] Enable firewall (UFW/iptables)
- [ ] Install and configure fail2ban
- [ ] Enable automatic security updates
- [ ] Configure SSH key authentication
- [ ] Disable root login via SSH
- [ ] Install intrusion detection system (OSSEC, Wazuh)
- [ ] Enable logging and monitoring
- [ ] Regular security audits

---

## 📋 METHODOLOGY: Step-by-Step Attack Framework

### Standard Penetration Testing Methodology

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PTES-BASED ATTACK METHODOLOGY                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  STEP 1: PRE-ENGAGEMENT                                                 │
│  ─────────────────────                                                  │
│  □ Sign contract and NDA                                                │
│  □ Define scope (IPs, domains, applications)                           │
│  □ Establish rules of engagement                                        │
│  □ Set communication channels                                           │
│  □ Agree on timeline and deliverables                                   │
│                                                                          │
│  STEP 2: INFORMATION GATHERING                                          │
│  ─────────────────────────                                              │
│  □ WHOIS lookup                                                         │
│  □ DNS enumeration (dig, nslookup)                                      │
│  □ Google dorking                                                       │
│  □ Social media reconnaissance                                          │
│  □ Subdomain enumeration                                                │
│  □ Technology fingerprinting                                            │
│                                                                          │
│  STEP 3: THREAT MODELING                                                │
│  ─────────────────────                                                  │
│  □ Identify assets                                                      │
│  □ Map attack surface                                                   │
│  □ Prioritize targets                                                   │
│  □ Identify potential attack vectors                                    │
│                                                                          │
│  STEP 4: VULNERABILITY ANALYSIS                                         │
│  ──────────────────────────────                                         │
│  □ Port scanning (Nmap)                                                 │
│  □ Service enumeration                                                  │
│  □ Vulnerability scanning (Nessus, OpenVAS)                            │
│  □ Manual testing                                                       │
│  □ False positive verification                                          │
│                                                                          │
│  STEP 5: EXPLOITATION                                                   │
│  ────────────────                                                       │
│  □ Identify applicable exploits                                         │
│  □ Test exploits in lab                                                 │
│  □ Execute exploits (with authorization)                               │
│  □ Bypass security controls                                             │
│  □ Document evidence                                                    │
│                                                                          │
│  STEP 6: POST-EXPLOITATION                                              │
│  ───────────────────────                                                │
│  □ Privilege escalation                                                 │
│  □ Lateral movement                                                     │
│  □ Data exfiltration (authorized)                                       │
│  □ Persistence mechanisms                                               │
│  □ Evidence collection                                                  │
│                                                                          │
│  STEP 7: REPORTING                                                      │
│  ──────────────                                                         │
│  □ Executive summary                                                    │
│  □ Technical details                                                    │
│  □ Risk scoring (CVSS)                                                  │
│  □ Remediation recommendations                                          │
│  □ Supporting evidence                                                  │
│                                                                          │
│  STEP 8: CLEANUP & RE-TEST                                              │
│  ─────────────────────────                                              │
│  □ Remove all tools and access                                          │
│  □ Clean up test accounts                                               │
│  □ Delete collected data                                                │
│  □ Re-test after remediation                                            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Penetration Test Report Template

```markdown
# PENETRATION TEST REPORT
## [Company Name]
### [Date Range]

---

## 1. EXECUTIVE SUMMARY

### Overview
[2-3 paragraph summary for management]

### Risk Summary
| Severity | Count |
|----------|-------|
| Critical | X |
| High | X |
| Medium | X |
| Low | X |

### Key Findings
1. [Finding 1]
2. [Finding 2]
3. [Finding 3]

---

## 2. SCOPE AND METHODOLOGY

### Scope
- IP Addresses: [List]
- Domains: [List]
- Applications: [List]

### Methodology
- Framework: PTES/OWASP
- Tools: [List]
- Testing Period: [Dates]

---

## 3. TECHNICAL FINDINGS

### Finding 1: [Title]
**Severity:** Critical/High/Medium/Low
**CVSS Score:** X.X
**Affected Systems:** [List]

**Description:**
[Detailed description]

**Evidence:**
[Screenshots, logs]

**Remediation:**
[Fix recommendations]

**References:**
[CVE, CWE, etc.]

---

## 4. APPENDICES
- Full scan results
- Tool outputs
- Screenshots
```

---

## ⚠️ LEGAL & ETHICS: Detailed Framework

### Indian IT Act 2000 - Relevant Sections

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    INDIAN CYBER LAW - KEY SECTIONS                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  SECTION 66: COMPUTER OFFENCES                                          │
│  ─────────────────────────────                                          │
│  • Hacking with intent to cause damage                                  │
│  • Punishment: Up to 3 years imprisonment + ₹5 lakh fine               │
│                                                                          │
│  SECTION 66A: OFFENSIVE MESSAGES                                        │
│  ─────────────────────────────                                          │
│  • Sending offensive messages via communication devices                 │
│  • Punishment: Up to 3 years + fine                                    │
│  (Note: Partly struck down by Supreme Court)                            │
│                                                                          │
│  SECTION 66C: IDENTITY THEFT                                            │
│  ─────────────────────────                                              │
│  • Fraudulently using someone's identity                                │
│  • Punishment: Up to 3 years + ₹1 lakh fine                            │
│                                                                          │
│  SECTION 66D: CHEATING BY PERSONATION                                   │
│  ───────────────────────────────                                        │
│  • Cheating using computer resources                                    │
│  • Punishment: Up to 3 years + ₹1 lakh fine                            │
│                                                                          │
│  SECTION 67: OBSCENE CONTENT                                            │
│  ─────────────────────────                                              │
│  • Publishing obscene material electronically                           │
│  • Punishment: Up to 5 years + ₹10 lakh fine                           │
│                                                                          │
│  SECTION 70: PROTECTED SYSTEMS                                          │
│  ─────────────────────────────                                          │
│  • Unauthorized access to protected systems                             │
│  • Punishment: Up to 10 years + fine                                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Scope of Authorization Document Template

```
PENETRATION TEST AUTHORIZATION
================================

CLIENT INFORMATION:
Company: _________________________
Address: _________________________
Contact: _________________________
Email: ___________________________

TESTER INFORMATION:
Name: ___________________________
Company: _________________________
Contact: _________________________
Email: ___________________________

AUTHORIZED SCOPE:
IP Addresses: ____________________
Domains: _________________________
Applications: ____________________
Time Period: _____________________

EXPLICIT PERMISSION:
I, [Name], authorize [Tester Name] to conduct penetration testing 
on the systems defined in this scope. I confirm that I have the 
authority to grant this permission.

PROHIBITED ACTIVITIES:
- Denial of Service attacks
- Social engineering (unless specified)
- Data exfiltration
- [Other restrictions]

EMERGENCY CONTACT:
Name: ___________________________
Phone: __________________________

CLIENT SIGNATURE: ________________  Date: ____________

TESTER SIGNATURE: ________________  Date: ____________

WITNESS (if required): ____________  Date: ____________
```

### Responsible Disclosure Guidelines

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    RESPONSIBLE DISCLOSURE PROCESS                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  STEP 1: DISCOVERY                                                      │
│  ├── Find vulnerability through authorized testing                     │
│  ├── Document findings thoroughly                                       │
│  └── Prepare proof of concept (harmless)                               │
│                                                                          │
│  STEP 2: PRIVATE DISCLOSURE                                             │
│  ├── Contact vendor/company security team                              │
│  ├── Provide detailed vulnerability report                             │
│  ├── Allow reasonable time for fix (30-90 days)                        │
│  └── Maintain confidentiality                                          │
│                                                                          │
│  STEP 3: COORDINATED DISCLOSURE                                         │
│  ├── Work with vendor on timeline                                      │
│  ├── Confirm patch effectiveness                                       │
│  └── Agree on public disclosure date                                   │
│                                                                          │
│  STEP 4: PUBLIC DISCLOSURE (After Fix)                                  │
│  ├── Publish findings responsibly                                       │
│  ├── Credit vendor for cooperation                                     │
│  └── Help community learn from findings                                │
│                                                                          │
│  NEVER:                                                                 │
│  ├── Publicly disclose before fix                                      │
│  ├── Exploit vulnerability for personal gain                           │
│  ├── Demand payment (unless bug bounty program)                        │
│  └── Threaten vendor                                                    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

### Prerequisites
- **Chapter 1-10**: Termux Basics, Navigation, Package Management
- **Chapter 11-20**: Linux Commands, Scripting, Network Basics

### Next Chapters in This Module
| Chapter | Title | Focus |
|---------|-------|-------|
| **31** | Hydra Password Cracking | SSH, FTP, HTTP brute force |
| **32** | Hydra Advanced | Proxies, multiple targets, optimization |
| **33** | John the Ripper | Hash cracking, extraction tools |
| **34** | SQLMap Basics | SQL injection automation |
| **35** | Metasploit Framework | Exploitation framework |
| **36** | PhoneSploit & ADB | Android device security |
| **37** | Social Engineering Toolkit | Phishing, credential harvesting |
| **38** | WiFi Security Tools | Aircrack-ng, wireless attacks |

### Related Modules
- **Module 7**: Advanced Security Techniques
- **Module 8**: Automation & Scripting for Security
- **Module 9**: CTF & Bug Bounty Preparation

---

## 🎮 INTERACTIVE QUIZ

### Test Your Knowledge

**Q1: What is the primary difference between ethical hacking and malicious hacking?**
- A) Tools used
- B) Permission and authorization
- C) Operating system
- D) Programming skills

**Q2: Which Indian IT Act section specifically deals with computer hacking?**
- A) Section 65
- B) Section 66
- C) Section 67
- D) Section 68

**Q3: Which tool is used for offline password hash cracking?**
- A) Hydra
- B) Nmap
- C) John the Ripper
- D) SQLMap

**Q4: What does PTES stand for?**
- A) Penetration Testing Execution Standard
- B) Professional Testing and Evaluation System
- C) Penetration Test Enterprise Solution
- D) Private Testing Execution Standard

**Q5: Which of these tools requires root access for full functionality?**
- A) Nmap
- B) Hydra
- C) Aircrack-ng (injection mode)
- D) SQLMap

**Q6: What is the recommended minimum password length?**
- A) 6 characters
- B) 8 characters
- C) 12 characters
- D) 4 characters

**Q7: Which phase comes immediately after vulnerability scanning?**
- A) Reporting
- B) Exploitation
- C) Reconnaissance
- D) Post-exploitation

**Q8: What is rockyou.txt?**
- A) A hacking tool
- B) A wordlist with 14.3 million passwords
- C) A vulnerability database
- D) An exploit framework

**Q9: Which proot command installs Kali Linux in Termux?**
- A) `pkg install kali`
- B) `proot-distro install kali`
- C) `apt-get install kali`
- D) `sudo install kali`

**Q10: What is the correct order of penetration testing phases?**
- A) Exploit → Scan → Report → Recon
- B) Recon → Scan → Exploit → Report
- C) Report → Recon → Scan → Exploit
- D) Scan → Recon → Report → Exploit

**Q11: Which tool is primarily used for network port scanning?**
- A) John
- B) Hydra
- C) Nmap
- D) Crunch

**Q12: What should be obtained BEFORE starting any penetration test?**
- A) New tools
- B) Written authorization
- C) Social media accounts
- D) Employee information

<details>
<summary>📝 Click to Reveal Answers</summary>

1. **B** - Permission and authorization
2. **B** - Section 66 (Computer hacking)
3. **C** - John the Ripper (offline hash cracking)
4. **A** - Penetration Testing Execution Standard
5. **C** - Aircrack-ng (injection mode)
6. **C** - 12 characters minimum
7. **B** - Exploitation
8. **B** - A wordlist with 14.3 million passwords
9. **B** - `proot-distro install kali`
10. **B** - Recon → Scan → Exploit → Report
11. **C** - Nmap
12. **B** - Written authorization
</details>

---

## 🎯 ETHICAL HACKING CHALLENGES

### Challenge 1: Lab Setup
- [ ] Set up DVWA in Docker or local environment
- [ ] Install all basic security tools in Termux
- [ ] Create organized directory structure for tools and wordlists
- [ ] Document your lab setup process

### Challenge 2: Reconnaissance
- [ ] Perform passive reconnaissance on your own website
- [ ] Use WHOIS to find domain registration details
- [ ] Enumerate subdomains using online tools
- [ ] Document all findings in a structured report

### Challenge 3: Tool Mastery
- [ ] Master Nmap basic scans (TCP, UDP, Service detection)
- [ ] Create a custom wordlist using Crunch
- [ ] Practice with Hydra on your local SSH server
- [ ] Document 10 useful options for each tool

### Challenge 4: Documentation
- [ ] Create a penetration test report template
- [ ] Write a sample executive summary
- [ ] Practice documenting findings with evidence
- [ ] Review and improve your notes organization

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 31, verify:

- [ ] Understood ethical hacking vs malicious hacking
- [ ] Know the legal requirements (authorization, scope)
- [ ] Familiar with security testing phases
- [ ] Installed basic security tools (Nmap, Hydra, John)
- [ ] Set up wordlists directory
- [ ] Understood which tools need proot
- [ ] Explored lab environment options
- [ ] Registered on at least one practice platform
- [ ] Understood documentation requirements
- [ ] Completed the interactive quiz
- [ ] Attempted at least 2 challenges

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 31: Hydra Password Cracking**

- Hydra architecture and protocols
- Installing and configuring Hydra
- SSH brute forcing
- FTP brute forcing
- HTTP form attacks
- Custom wordlists
- Optimizing attacks
- Saving and analyzing results

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*
