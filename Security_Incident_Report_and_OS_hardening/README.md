# Portfolio Project: Security Incident Report & OS Hardening

## Overview
This incident report documents the investigation of a security breach affecting the e-commerce and recipe website **yummyrecipesforme.com**. The investigation covers network protocol analysis, attack vector identification, incident documentation, and recommended remediation strategies to prevent unauthorized access and malware distribution.

---

## Section 1: Network Protocols Identified
During the sandbox investigation and analysis of the traffic logs using `tcpdump`, several core network protocols were identified at various layers of the TCP/IP model:

* **Internet Protocol (IP):** Managed the underlying packet routing and addressing between the user sandbox machine and external web servers.
* **Domain Name System (DNS):** Translated human-readable domain names (`yummyrecipesforme.com` and the malicious redirect `greatrecipesforme.com`) into numerical IP addresses.
* **Transmission Control Protocol (TCP):** Established reliable, connection-oriented sessions using port numbers and control flags (such as `[S]` SYN, `[S.]` SYN-ACK, and `[.]` ACK).
* **Hypertext Transfer Protocol (HTTP):** The unencrypted application-layer protocol utilized over port 80 to request web pages and trigger file downloads.

---

## Section 2: Incident Documentation

### Incident Summary
* **Target:** `yummyrecipesforme.com` web server and its administrative panel.
* **Actor:** A disgruntled former employee leveraging internal knowledge.
* **Discovery Method:** Multiple customer complaints submitted to the helpdesk reporting slow computer performance and forced file download prompts when attempting to access free recipes.

### Attack Lifecycle & Execution
1. **Initial Access (Brute Force):** The attacker successfully compromised the administrative account by guessing weak default passwords through repeated automated login attempts, as no rate-limiting or brute-force protections were active.
2. **Privilege Abuse & Modification:** Once authenticated, the attacker accessed the admin panel, altered the administrative password to lock out legitimate owners, and modified the web server's source code.
3. **Malware Distribution & Redirection:** The attacker embedded a malicious JavaScript function into the webpage source code. When visitors loaded the site, their browsers were prompted to download an executable file disguised as a browser update, which subsequently redirected traffic to a rogue domain (`greatrecipesforme.com`) hosting malware.
4. **Verification:** Cybersecurity analysts replicated the event in a secure sandbox environment using `tcpdump`, observing the sequence of DNS lookups, HTTP requests, file downloads, and the unauthorized redirection to the malicious server.

---

## Section 3: Remediation & Brute-Force Prevention

To secure the administrative panel and prevent future brute-force compromises, the organization must implement the following key remediation measure:

* **Enforce Multi-Factor Authentication (MFA):** 
  * **Why it is effective:** Requiring MFA (such as time-based one-time passwords or hardware security keys) ensures that even if an attacker successfully guesses or cracks an administrative password via brute force, they cannot gain access without the secondary authentication factor. 
  * **Complementary Controls:** This should be paired with **account lockout policies** (automatically locking accounts after a set number of failed login attempts) and strict **strong password complexity requirements** to eliminate default or weak credentials across all enterprise systems.
