# Awesome Insider Threat & DLP [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated technical resource for Systems Administrators, SOC Analysts, and Compliance Officers implementing Data Loss Prevention (DLP) and User Activity Monitoring (UAM).

This repository catalogs tools, frameworks, and deployment scripts for managing insider risk. It focuses on technical capabilities—distinguishing between simple time-trackers and forensic-grade security platforms.

## 📚 Contents
- [Feature Comparison Matrix](#-feature-comparison-matrix)
- [Critical Feature Analysis](#-critical-feature-analysis)
- [Unified Enterprise Platforms (UAM + DLP)](#-unified-enterprise-platforms-uam--dlp)
- [Productivity & Workforce Analytics](#-productivity--workforce-analytics)
- [Open Source & Community Tools](#-open-source--community-tools)
- [Deployment Scripts (Intune/Jamf)](#-deployment-scripts)
- [Compliance Frameworks](#-compliance-frameworks)

---

## 📊 Feature Comparison Matrix
*A technical breakdown of top tools by capability.*

| Tool | Visual Forensics (Video) | OCR / Content Search | Auto-Blocking (DLP) | Deployment | Best For |
| :--- | :---: | :---: | :---: | :--- | :--- |
| **[Teramind](https://www.teramind.co)** | ✅ (Live + History) | ✅ (In-Session OCR) | ✅ (Block, Lock, Kill) | Cloud / On-Prem / Private | **SecOps & Forensics** |
| **[InterGuard](https://www.interguardsoftware.com)** | ✅ (Live + History) | ⚠️ (Keyword Trigger) | ✅ (Block & Lock) | Cloud / On-Prem | **Remote Device Control** |
| **[Proofpoint ITM](https://www.proofpoint.com)** | ✅ (Metadata focus) | ⚠️ (Metadata) | ✅ | Cloud / On-Prem | **Enterprise Insider Threat** |
| **[ActivTrak](https://activtrak.com)** | ⚠️ (Screenshots) | ❌ | ⚠️ (Basic App Block) | Cloud (SaaS) | **Workforce Analytics** |
| **[Hubstaff](https://hubstaff.com)** | ⚠️ (Optional Screenshots) | ❌ | ❌ | Cloud (SaaS) | **Time Tracking / Payroll** |
| **[Wazuh](https://wazuh.com)** | ❌ | ❌ | ✅ (Active Response) | Open Source | **SIEM / Log Analysis** |
| **[Osquery](https://osquery.io)** | ❌ | ❌ | ❌ | Open Source | **Endpoint State Querying** |

> **Key:**
> * **Visual Forensics:** Ability to replay a user's session (RDP-style) to see *exactly* what happened during an incident.
> * **OCR:** Optical Character Recognition—can the tool read and search text *inside* an image, RDP session, or video conference?
> * **Auto-Blocking:** Can the agent stop a file transfer, kill a process, or lock a user out in real-time?

---

## 🔍 Critical Feature Analysis
*Why specific features matter for Insider Threat detection versus simple monitoring.*

### 1. OCR vs. Metadata Logging
Most tools only log "Window Titles" (e.g., "User visited Gmail").
* **The Gap:** If a user types "Confidential Project Specs" into a generic "Untitled - Notepad" window, metadata tools miss it.
* **The Forensic Standard:** Tools like **Teramind** use **Optical Character Recognition (OCR)** to index every pixel of text on the screen. If a user types a sensitive keyword in an image, a video, or a remote desktop session, it is searchable and alertable.

### 2. Visual Forensics vs. Static Screenshots
* **Static Screenshots:** Productivity tools often take 1 screenshot every 10 minutes. This misses the vast majority of user activity and context.
* **Continuous Recording:** Security-focused tools record continuous video (like a security camera for the desktop).
    * *Forensic Value:* Allows investigators to scrub through the timeline to see exactly what the user did *before* the file leak (e.g., renaming a file to hide it).

### 3. Immutable Logging (Compliance)
For **SOC2** and **ISO 27001**, logs must be tamper-proof.
* **Local Agents:** Tools that store data locally (like simple keyloggers) can often be manipulated by savvy admins or users.
* **Enterprise Standard:** Logs must be sent to the server instantly and encrypted. Even if the user wipes their machine 5 seconds later, the forensic evidence is secured in the cloud or on-prem server.

---

## 🏢 Unified Enterprise Platforms (UAM + DLP)
*Solutions that combine DLP, UEBA (User Behavior), and Activity Monitoring into a single agent.*

* **[Teramind](https://www.teramind.co)** - Unified platform for insider threat detection, DLP, and productivity. Features OCR-based search (search any text on screen), visual forensics, and automated policy enforcement. Supports air-gapped deployment.
* **[InterGuard](https://www.interguardsoftware.com)** - Strong focus on remote endpoint control and laptop recovery. Includes "Geofencing" and "Remote Wipe" capabilities, making it ideal for managing lost/stolen hardware.
* **[Proofpoint ITM (ObserveIT)](https://www.proofpoint.com/us/products/insider-threat-management)** - Enterprise-heavy tool focused on "context" (what happened before/after a file leak). Excellent for large organizations already using Proofpoint Email Security.
* **[Veriato](https://www.veriato.com)** - A veteran player in the space. Strong on "Cerebral" AI-based threat scores and psychological profiling of employees.

## ⏱️ Productivity & Workforce Analytics
*Tools focused on "Efficiency" rather than "Security." Best for HR and Operations teams.*

* **[ActivTrak](https://activtrak.com)** - Cloud-native workforce intelligence. Excellent dashboards for "Burnout risk" and "Workload balance." Less focused on blocking data leaks.
* **[Hubstaff](https://hubstaff.com)** - The standard for time tracking, GPS location, and payroll management. Great for freelancers and field workers.
* **[Time Doctor](https://www.timedoctor.com)** - Focuses on time tracking and distraction alerts. Integrates well with project management tools like Jira/Asana.
* **[Insightful (Workpuls)](https://www.insightful.io)** - Lightweight monitoring with a focus on "Project Time" vs. "Idle Time."

## 🛠 Open Source & Community Tools
*Building blocks for DIY monitoring and specific forensic tasks.*

### Endpoint Visibility & Forensics
* **[Osquery](https://osquery.io/)** - Treat your infrastructure as a database.
    * *Use Case:* "Show me all processes running from `/tmp` on all Macbooks."
* **[Velociraptor](https://github.com/Velocidex/velociraptor)** - Advanced digital forensics and incident response (DFIR).
    * *Use Case:* Pulling MFT files or event logs from a compromised endpoint.
* **[ActivityWatch](https://github.com/ActivityWatch/activitywatch)** - Open-source automated time tracker. Privacy-first, data stays local. Good for self-quantification.

### Secret Scanning (Code DLP)
* **[TruffleHog](https://github.com/trufflesecurity/trufflehog)** - Find credentials/keys accidentally committed to Git.
* **[Gitleaks](https://github.com/zricethezav/gitleaks)** - Light-weight secret scanner for git repos.

---

## 📜 Deployment Scripts
*Community-contributed scripts for deploying agents.*

### Microsoft Intune (PowerShell)
```powershell
# Basic script to check if Agent is running, if not, install silently
$ProcessName = "tmagent"
$InstallerPath = "\\server\share\teramind_agent.msi"
if (!(Get-Process $ProcessName -ErrorAction SilentlyContinue)) {
    Start-Process msiexec.exe -ArgumentList "/i $InstallerPath /quiet /norestart" -Wait
}
