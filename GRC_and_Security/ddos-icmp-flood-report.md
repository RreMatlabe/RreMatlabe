# Incident Report: DDoS Attack (ICMP Flood)
**Framework Applied:** NIST Cybersecurity Framework (CSF)
**Severity:** High
**Impact:** Business Operations Halted (2 Hours)

## 1. Incident Summary
Our multimedia company experienced a Distributed Denial of Service (DDoS) attack that disrupted operations for approximately two hours.

**Root Cause:**
The incident originated when a junior staff member opened a malicious email, redirecting them to an external website. This action triggered a botnet to target our network.

**Technical Analysis:**
System logs revealed the network was overwhelmed by a massive flood of **ICMP packets** (Ping Flood). The attacker exploited an **unconfigured firewall**, using it as an entry point to inject traffic. This misconfiguration allowed the attacker to bypass safeguards and saturate the network, rendering critical resources unresponsive.

## 2. NIST Framework Analysis

| Function | Actions Taken |
| :--- | :--- |
| **IDENTIFY** | The incident management team conducted a thorough audit of systems and access policies. Logs confirmed the outage was caused by an ICMP flood that overwhelmed services. The audit identified the critical vulnerability: an **unconfigured firewall**. |
| **PROTECT** | To prevent recurrence, two key measures were implemented:<br>1. **Rate Limiting:** A new firewall rule now limits the rate of incoming ICMP packets.<br>2. **Source Verification:** Enabled source IP verification to detect and block spoofed packets. |
| **DETECT** | The network security team deployed **continuous network monitoring software** to detect abnormal traffic patterns early. Additionally, regular **vulnerability scanning** was introduced to identify weaknesses across servers and endpoints before they can be exploited. |
| **RESPOND** | An **IDS/IPS (Intrusion Detection/Prevention System)** was deployed to filter suspicious ICMP traffic immediately. The team executed the Incident Response Plan, ensuring structured containment, stakeholder communication, and coordination. |
| **RECOVER** | Network services were restored to a normal state within two hours. Recovery actions included blocking incoming ICMP packets and prioritizing critical services. The team verified service integrity and documented lessons learned to improve future firewall configurations. |

## 3. Reflections & Lessons Learned
*   **Human Factor:** The incident highlights the need for ongoing phishing awareness training, as the attack vector was initiated by a user action.
*   **Configuration Management:** The "unconfigured firewall" was a critical failure point. Regular audits of security configurations are now mandatory.
