# Security Incident Report: Network Traffic Analysis (DNS Spoofing)

**Date:** January 2026
**Analyst:** Katlego Matlabe
**Status:** Closed

## 1. Executive Summary
This report documents a network security incident involving the redirection of user traffic via DNS spoofing. The analysis of network logs confirms that a user attempting to access a legitimate domain was redirected to a malicious IP address through a manipulated DNS resolution process.

## 2. Protocol Identification
The following network protocols were identified as active during the incident:
*   **TCP (Transmission Control Protocol):** Initiated the handshake process to establish connections between the source machine and the destination servers.
*   **HTTP (Hypertext Transfer Protocol):** Used as the application layer protocol for communication between the client and the web server (Port 80).
*   **DNS (Domain Name System):** The primary vector for this incident; used to translate domain names into IP addresses.

## 3. Incident Documentation & Log Analysis
**Timestamp:** 14:18:32 - 14:20:00

**Sequence of Events:**
1.  **Initial Request:** The source computer (`your.machine.52444`) sent a DNS resolution request for `yummyrecipesforme.com`.
2.  **Legitimate Response:** The DNS server initially resolved this to the correct IP (`203.0.113.22`).
3.  **Connection Established:** The source computer successfully connected to the legitimate site via HTTP (Port 80) at 14:18:36.
4.  **The Attack Vector:** Approximately two minutes later, a second DNS request was initiated. This time, the DNS server directed traffic to a **new, unrecognized IP address** (`192.0.2.172`).
5.  **Redirection:** This new IP is associated with a spoofed URL (`greatrecipesforme.com`).
6.  **Confirmation:** The change in destination IP and the redirection to a similar-sounding but incorrect domain confirms a DNS Spoofing/Cache Poisoning attack.

## 4. Remediation Recommendations
*   **Immediate Action:** Flush DNS cache on affected machines and verify DNS server integrity.
*   **Brute Force Prevention:** To prevent attackers from gaining initial access to modify DNS records or compromise accounts, we recommend implementing **Multi-Factor Authentication (MFA)**. Ensuring employees use MFA for logging in (via SMS or Email OTP) significantly reduces the risk of credential compromise.
