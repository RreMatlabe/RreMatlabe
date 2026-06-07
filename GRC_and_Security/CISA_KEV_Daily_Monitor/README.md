# CISA KEV Daily Monitor

## Automated Vulnerability Intelligence Alerting via n8n

**Portfolio Project | GRC & Security Automation**  
**Repository:** [RreMatlabe/GRC_and_Security](https://github.com/RreMatlabe/RreMatlabe/tree/main/GRC_and_Security)

---

## Overview

This project automates the daily monitoring of the **CISA Known Exploited Vulnerabilities (KEV) Catalogue** — the authoritative U.S. government source listing vulnerabilities actively exploited in the wild. Instead of manually checking the catalogue, this workflow runs automatically each day, filters for newly added CVEs, and delivers a structured alert email containing full remediation details.

In a real organisational context, this type of automation supports vulnerability management programmes, patch prioritisation decisions, and regulatory compliance obligations under frameworks such as NIST CSF 2.0.

---

## Business Problem

Manual vulnerability tracking is slow, inconsistent, and error-prone. Security and GRC teams that rely on periodic manual reviews of threat feeds risk missing newly disclosed exploited vulnerabilities within the critical remediation window. CISA's KEV catalogue is widely recognised as a high-signal, low-noise source — every entry represents a vulnerability with confirmed real-world exploitation, making it a priority monitoring target for any organisation managing cyber risk.

---

## Solution Architecture

The workflow is built in **n8n** and consists of four nodes:

```
Schedule Trigger → HTTP Request → Code in JavaScript → Send an Email
```

| Node | Function |
|------|----------|
| Schedule Trigger | Runs the workflow automatically once per day |
| HTTP Request (GET) | Fetches the full CISA KEV JSON feed from the official CISA endpoint |
| Code in JavaScript | Filters the dataset to return only CVEs added in the last 24 hours |
| Send an Email (SMTP) | Delivers one structured alert email per new CVE to the analyst inbox |

### CISA KEV API Endpoint
```
https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json
```
No authentication required. Updated continuously by CISA.

---

## Alert Email Fields

Each alert email contains the following fields drawn directly from the CISA KEV catalogue:

- **CVE ID** — Unique identifier (e.g. CVE-2026-28318)
- **Vendor / Project** — Affected vendor (e.g. SolarWinds)
- **Product** — Specific affected product (e.g. Serv-U)
- **Vulnerability Name** — Descriptive name
- **Date Added** — Date CISA added it to the KEV catalogue
- **Due Date** — Federal remediation deadline per BOD 22-01
- **Required Action** — CISA's mandated remediation guidance
- **Short Description** — Technical summary of the vulnerability
- **Known Ransomware Campaign Use** — Whether the CVE is linked to active ransomware campaigns

---

## Sample Output

**Email Subject:**
```
CISA KEV Alert — CVE-2026-28318
```

**Email Body:**
```
CVE ID: CVE-2026-28318
Vendor: SolarWinds
Product: Serv-U
Vulnerability: SolarWinds Serv-U Uncontrolled Resource Consumption Vulnerability
Date Added: 2026-06-05
Due Date: 2026-06-19
Required Action: Apply mitigations per vendor instructions, follow applicable 
BOD 22-01 guidance for cloud services, or discontinue use of the product if 
mitigations are unavailable.
Description: SolarWinds Serv-U contains an uncontrolled resource consumption 
vulnerability that allows specially crafted POST requests using the 
Content-Encoding: deflate header to crash the Serv-U service without authentication.
```

---

## GRC Framework Alignment

This automation directly supports the following **NIST Cybersecurity Framework (CSF) 2.0** functions and categories:

| CSF 2.0 Function | Category | How This Project Addresses It |
|-----------------|----------|-------------------------------|
| **DETECT (DE)** | Continuous Monitoring (DE.CM) | Automated daily polling of authoritative threat intelligence source |
| **DETECT (DE)** | Adverse Event Analysis (DE.AE) | Structured alerting on newly confirmed exploited vulnerabilities |
| **RESPOND (RS)** | Incident Management (RS.MA) | Remediation deadlines and required actions delivered automatically to analysts |
| **IDENTIFY (ID)** | Improvement (ID.IM) | Reduces manual effort and human error in vulnerability tracking processes |
| **GOVERN (GV)** | Risk Management Strategy (GV.RM) | Supports patch prioritisation aligned to confirmed exploitation evidence |

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| n8n (v2.8.4) | Workflow automation platform |
| CISA KEV API | Authoritative vulnerability intelligence source |
| JavaScript | Date filtering logic within the Code node |
| Gmail SMTP | Secure email delivery via App Password authentication |
| Ubuntu 24 (VirtualBox) | Local analyst lab environment |

---

## Relevance to GRC & SOC Roles

This project demonstrates practical competency in several areas directly relevant to junior GRC Analyst and SOC Analyst roles:

- **Vulnerability Management** — Understanding of CVE lifecycle, CISA KEV catalogue, and BOD 22-01 remediation requirements
- **Automation Thinking** — Ability to identify manual processes and replace them with reliable automated workflows
- **API Integration** — Consuming a public government REST API without authentication
- **Alert Engineering** — Structuring actionable alerts with the right fields for analyst decision-making
- **Framework Application** — Mapping technical controls to NIST CSF 2.0 governance functions

---

## How to Replicate

1. Install n8n locally (`npm install -g n8n` or via Docker)
2. Create a new workflow and add the four nodes in sequence
3. Configure the HTTP Request node with the CISA KEV endpoint (GET, no auth)
4. Add the JavaScript filter code to isolate CVEs from the last 24 hours
5. Configure Gmail SMTP credentials using a Google App Password
6. Set the Schedule Trigger to your preferred daily run time
7. Activate the workflow

---

## Author

**Katlego Matlabe**  
GRC & Cybersecurity Professional | Pretoria, South Africa  
[GitHub](https://github.com/RreMatlabe) | [LinkedIn](https://www.linkedin.com/in/katlego-matlabe-12157715b/)

*Part of an ongoing portfolio documenting practical GRC, SOC, and security automation work built in a self-directed analyst lab environment.*
