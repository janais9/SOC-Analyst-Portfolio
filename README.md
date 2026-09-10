# 🛡️ SOC Analyst Portfolio

![Focus](https://img.shields.io/badge/Focus-SOC%20Analysis-blue)
![Level](https://img.shields.io/badge/Level-SOC%20L1-green)
![Environment](https://img.shields.io/badge/Environment-Simulated-orange)
![Status](https://img.shields.io/badge/Portfolio-Active-success)

> 🔐 A hands-on cybersecurity portfolio focused on SOC alert triage, investigation, threat analysis, and incident documentation.

---

## 👩‍💻 About This Portfolio

This repository documents my hands-on journey toward becoming a **SOC Analyst**.

The goal of this portfolio is to demonstrate practical skills in:

- 🔎 Security Alert Triage
- 🧠 Alert Investigation
- 🛡️ Threat Intelligence
- 🚨 Incident Analysis
- 🗺️ MITRE ATT&CK Mapping
- 📝 SOC Investigation Documentation
- 🎯 True Positive / False Positive Classification
- 🔄 SOC L1 Investigation Workflow

Rather than documenting only theoretical knowledge, this portfolio focuses on **practical investigations and evidence-based analysis**.

---

## 🎯 Career Goal

My current focus is developing the skills required for a:

**SOC Analyst L1 → SOC Analyst L2**

The portfolio is being built progressively through hands-on security investigations, simulated SOC environments, and practical cybersecurity projects.

---

## 🧰 Skills & Areas of Practice

| Area | Skills |
|---|---|
| 🚨 Alert Triage | Alert prioritization, assignment, investigation, closure |
| 🔍 Investigation | Alert analysis, contextual analysis, evidence review |
| 🌐 Network Analysis | Source/destination analysis, traffic context |
| 🦠 Threat Analysis | Suspicious files, URLs, hashes, malicious indicators |
| 🧠 Threat Intelligence | IOC reputation checks and contextual validation |
| 🗺️ MITRE ATT&CK | Technique identification and mapping |
| 📝 Documentation | Investigation summaries, analyst comments, recommendations |
| 🎯 Alert Classification | True Positive / False Positive |
| 🔄 SOC Workflow | L1 triage, escalation considerations, closure |

---

# 📂 Projects

## 01 — Double-Extension File Creation

**Alert Type:** Suspicious File Creation  
**Severity:** 🔴 High  
**Verdict:** 🟢 True Positive  
**Status:** 🟢 Closed

### Investigation Focus

Investigation of a suspicious executable using a double-extension filename:

```text
cats2025.mp4.exe
```

The investigation included:

- Alert triage
- Host and user identification
- Process analysis
- File analysis
- URL analysis
- MD5 hash analysis
- Threat intelligence checks
- MITRE ATT&CK mapping
- Final verdict and documentation

### Key Finding

The alert correctly identified suspicious double-extension file creation activity.

**Confirmed scope:** File creation  
**Execution:** Not confirmed

📁 **Project:** `01-Double-Extension-File-Creation`

---

## 02 — Potential Data Exfiltration

**Alert Type:** High-Volume Network Traffic  
**Severity:** 🔴 Critical  
**Verdict:** 🟠 False Positive  
**Status:** 🟢 Closed

### Investigation Focus

Investigation of an alert triggered by more than **5 GB of outbound traffic** from a single source to a single destination.

Key investigation data included:

```text
Source IP      → 192.168.45.66
Source Network → UK04/MEETINGROOM
Destination    → *.zoom.us
Sent Data      → 5.8 GB
Received Data  → 5.2 GB
```

The investigation focused on:

- Network traffic analysis
- Source and destination context
- Sent vs. received traffic
- Environmental context
- False positive identification
- Detection logic analysis
- SOC documentation

### Key Finding

The traffic was consistent with legitimate Zoom-related activity from a meeting-room network.

**Final classification:** False Positive

📁 **Project:** `02-Potential-Data-Exfiltration`

---

## 03 — Download from GitHub Repository

**Alert Type:** External Repository Activity  
**Severity:** 🟢 Low  
**Verdict:** 🟠 False Positive  
**Status:** 🟢 Closed

### Investigation Focus

Investigation of GitHub activity detected by a rule monitoring downloads from external repositories.

Key investigation data included:

```text
User          → G.Chandler
Host          → LPT-IT-063
Network       → VPN/DEVELOPERS
Repository    → github.com/facebook/react
```

The investigation focused on:

- Repository identification
- User context
- Host context
- Source network analysis
- Developer activity assessment
- False positive classification
- SOC documentation

### Key Finding

The activity was consistent with legitimate developer activity involving the `facebook/react` repository.

**Final classification:** False Positive

📁 **Project:** `03-Download-from-GitHub-Repository`

---

# 📊 Investigation Summary

| # | Alert | Severity | Verdict | Status |
|---|---|---|---|---|
| 01 | Double-Extension File Creation | 🔴 High | 🟢 True Positive | 🟢 Closed |
| 02 | Potential Data Exfiltration | 🔴 Critical | 🟠 False Positive | 🟢 Closed |
| 03 | Download from GitHub Repository | 🟢 Low | 🟠 False Positive | 🟢 Closed |

---

# 🧠 Investigation Methodology

Each investigation follows a structured SOC L1 triage process:

```text
                    🚨 ALERT
                       │
                       ▼
              Prioritize the Alert
                       │
                       ▼
              Assign to L1 Analyst
                       │
                       ▼
                 In Progress
                       │
                       ▼
              Review Alert Details
                       │
                       ▼
              Identify Key Indicators
                       │
                       ▼
             Investigate the Activity
                       │
                       ▼
             Threat Intelligence
                       │
                       ▼
               Determine Verdict
                 /            \
                /              \
       🟢 True Positive    🟠 False Positive
                \              /
                 \            /
                  ▼          ▼
                 Analyst Comment
                       │
                       ▼
                     Closed
```

---

# 🔬 Evidence-Based Analysis

A key principle followed throughout this portfolio is:

> **Do not overclaim. Document what the available evidence supports.**

Investigations distinguish between:

- **Observed activity**
- **Suspicious indicators**
- **Confirmed findings**
- **Inconclusive results**
- **Potential impact**
- **Recommended follow-up actions**

This approach helps ensure that investigation conclusions are based on evidence rather than assumptions.

---

# 🗺️ MITRE ATT&CK

MITRE ATT&CK techniques are mapped where applicable to the observed behavior.

Current investigations include examples such as:

| Technique | ID | Investigation |
|---|---|---|
| Masquerading: Double File Extension | `T1036.008` | Double-Extension File Creation |
| Malicious File | `T1204.002` | Potential mapping where execution would be confirmed |
| Ingress Tool Transfer | `T1105` | Potential relevance to external file downloads |

> MITRE mappings are treated carefully and are not presented as confirmed when the underlying behavior has not been established by available evidence.

---

# 🛠️ Tools & Platforms

The portfolio currently uses hands-on simulated SOC environments and security analysis workflows.

### Security Platforms

- TryHackMe SOC environments
- SIEM-based alert investigation
- Threat Intelligence platforms

### Investigation Techniques

- IOC analysis
- URL reputation checks
- Hash reputation checks
- Network context analysis
- User and host analysis
- Alert correlation
- Evidence-based verdict determination

---

# 📈 Portfolio Progress

```text
SOC Analyst L1
     │
     ├── Alert Triage              ✅
     ├── Alert Prioritization      ✅
     ├── True Positive Analysis    ✅
     ├── False Positive Analysis   ✅
     ├── Threat Intelligence       ✅
     ├── IOC Analysis              ✅
     ├── MITRE ATT&CK              ✅
     ├── Investigation Reporting   ✅
     │
     └── More Projects             🚧 In Progress
```

---

# 🚀 Upcoming Projects

The portfolio will continue expanding with additional practical security investigations and SOC-focused projects.

Planned areas include:

- 📧 Phishing Email Investigation
- 🔐 Authentication / Brute Force Investigation
- ⚡ Suspicious PowerShell Activity
- 🦠 Malware Investigation
- 🌐 Network-Based Threat Investigation
- 🔎 Threat Hunting
- 🚨 Incident Response

---

# 📚 Learning Path

Current learning is focused on progressing through practical SOC training and gradually expanding from:

```text
SOC Fundamentals
       ↓
Alert Triage
       ↓
SOC Analyst L1
       ↓
Threat Investigation
       ↓
Threat Hunting
       ↓
Incident Response
       ↓
SOC Analyst L2
```

---

# 📌 Portfolio Philosophy

This portfolio is built around three principles:

### 1️⃣ Investigate

Understand **what happened** before making a decision.

### 2️⃣ Validate

Use available evidence and threat intelligence to support or challenge the initial assumption.

### 3️⃣ Document

Clearly explain **what was observed, what was confirmed, what remains unknown, and why the alert was closed**.

---

# ⚠️ Disclaimer

All investigations documented in this repository are performed in **simulated cybersecurity training environments** unless explicitly stated otherwise.

No real organizational data, credentials, or confidential information is included.

---

# 👩‍💻 Author

**Jana Ismail**

Cybersecurity / SOC Analyst Track

Focused on developing practical skills in:

**SOC Analysis • Threat Detection • Incident Investigation • Threat Intelligence**

---

⭐ *This portfolio is continuously evolving as new investigations and cybersecurity projects are completed.*
