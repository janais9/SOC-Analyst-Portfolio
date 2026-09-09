# 🐾 Double-Extension File Creation Investigation

![Severity](https://img.shields.io/badge/Severity-High-red)
![Verdict](https://img.shields.io/badge/Verdict-Malicious-critical)
![Status](https://img.shields.io/badge/Status-Closed-success)
![MITRE](https://img.shields.io/badge/MITRE-T1036.008-blue)

> 📁 SOC Level 1 Alert Triage — Simulated environment (TryHackMe)

---

## 📋 Overview

This project documents the L1 SOC triage of a **High severity** alert triggered by the creation of a suspicious double-extension file on host `LPT-HR-009`, downloaded via `chrome.exe` by user `S.Conway`.

---

## 🚨 Alert Details

| Field | Value |
|---|---|
| **Alert Name** | Double-Extension File Creation |
| **Severity** | 🔴 High |
| **Host** | `LPT-HR-009` |
| **Process Name** | `chrome.exe` |
| **Process User** | `S.Conway` |
| **Target File** | `C:\Users\S.Conway\Downloads\cats2025.mp4.exe` |
| **File MotW (Source URL)** | `https://frecativideoshd.monster/cats2025.mp4.exe` |
| **MD5** | `14d8486f638375e93cfd240c5dc10b` |

---

## 🧭 Attack Chain

```mermaid
flowchart LR
    A[👤 User S.Conway] -->|Browses web| B[🌐 chrome.exe]
    B -->|Downloads file| C[frecativideoshd.monster]
    C -->|Serves payload| D[cats2025.mp4.exe]
    D -->|Double extension hides .exe| E[⚠️ File appears as video]
    E -->|If executed| F[💥 Potential Malware Execution]
    style F fill:#ff4d4d,stroke:#900,color:#fff
    style D fill:#ffcc00,stroke:#a67c00
    style C fill:#ffcc00,stroke:#a67c00
```

---

## 🔍 Investigation

### 1️⃣ File Analysis

- The target file `cats2025.mp4.exe` uses a **double extension** technique, relying on the fact that Windows Explorer hides *known file extensions* by default.
- To an average user, this file would visually appear as **`cats2025.mp4`** — a harmless video file — while it is, in reality, a **Windows executable (`.exe`)**.
- This is a classic **masquerading** technique used to trick users into executing malicious code disguised as media content.
- File location (`Downloads` folder, delivered via browser) is consistent with a drive-by / social-engineering download rather than a legitimate application install.

**Verdict for this indicator:** 🔴 Suspicious — strong masquerading indicator.

---

### 2️⃣ URL Analysis

- Source URL: `https://frecativideoshd.monster/cats2025.mp4.exe`
- The domain `frecativideoshd.monster`:
  - Uses the **`.monster`** TLD, frequently abused for low-cost, disposable malicious infrastructure.
  - Combines generic "video streaming" branding (`video`, `hd`) with a random-looking prefix — typical of scam/malware distribution sites impersonating pirated media or "video codec" download pages.
  - Directly serves an `.exe` file under a filename crafted to look like a video — matching the double-extension lure.
- No legitimate video streaming service would serve `.mp4` content as a `.exe` binary.

**Verdict for this indicator:** 🔴 Malicious — known pattern of malvertising / fake streaming site delivering malware.

---

### 3️⃣ Hash Analysis

- MD5: `14d8486f638375e93cfd240c5dc10b`
- The hash should be submitted to reputation/sandbox platforms (e.g. VirusTotal, Hybrid Analysis) for confirmation.
- Combined with the delivery method (fake video site) and the double-extension technique, this hash is consistent with a **generic malware dropper/loader** — commonly distributed through fake streaming or "codec download" campaigns.

**Verdict for this indicator:** 🔴 Malicious (pending/confirmed via threat intel lookup).

---

### 4️⃣ User and Host Analysis

- Host `LPT-HR-009` is a laptop, consistent with an HR department asset (naming convention suggests HR team).
- User `S.Conway` initiated the download via normal browsing activity in `chrome.exe` — no evidence of automated/scripted delivery, suggesting a **social engineering** vector (user searching for or clicking a link to "cat videos").
- No indication (within current evidence) that the file was executed — the alert fired on **file creation**, not process execution. This is a critical distinction for scoping impact.

---

## 🗺️ MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---|---|---|
| Defense Evasion | Masquerading: Double File Extension | `T1036.008` |
| Initial Access | Drive-by Compromise | `T1189` |
| User Execution | Malicious File (if executed) | `T1204.002` |

---

## ✅ Final Verdict

> ## 🔴 **MALICIOUS — True Positive**

The combination of:
- a double-extension filename designed to disguise an executable as a media file,
- a low-reputation, purpose-built malicious domain, and
- delivery through casual browsing consistent with social engineering,

confirms this alert as a **true positive malicious file download**, currently contained at the **file creation** stage (no confirmed execution).

---

## 🛠️ Recommended Actions

- [ ] **Isolate** host `LPT-HR-009` from the network immediately.
- [ ] **Quarantine/delete** the file `cats2025.mp4.exe` before execution.
- [ ] Confirm via EDR whether the file was **executed** — check process creation logs.
- [ ] Submit MD5 hash to VirusTotal / sandbox for full detonation analysis.
- [ ] Block domain `frecativideoshd.monster` at the proxy/firewall/DNS level.
- [ ] Search the environment for other hosts contacting the same domain (IOC sweep).
- [ ] Notify user `S.Conway` and provide security awareness reminder on double-extension lures.
- [ ] Update detection rule to alert on `.mp4.exe`, `.pdf.exe`, `.docx.exe`, etc. patterns organization-wide.

---

## 🎓 Lessons Learned

- Double-extension filenames remain an effective and low-effort social engineering technique because Windows hides known extensions by default.
- Free/uncommon TLDs (e.g. `.monster`, `.xyz`, `.click`) combined with generic "streaming/video" branding are a recurring pattern in malvertising campaigns.
- Alerting on **file creation** (rather than only execution) provides a valuable earlier detection point in the kill chain.
- Clear, structured documentation — indicators, verdict, MITRE mapping, and actions — is essential for SOC analyst handoffs and audit trails.

---

*Investigation conducted as part of a simulated SOC environment (TryHackMe).*
