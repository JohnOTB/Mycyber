# Portfolio Project: Network Attack Analysis & Incident Report

## Overview
As a security analyst for a travel agency, I investigated an unexpected service interruption where employees and customers experienced connection timeout errors when trying to access the company's sales and promotions website. Using packet analysis (`tcpdump`/Wireshark logs), I identified the incident as a malicious Denial of Service (DoS) attack targeting the web server's connection resources.

---

## Part 1: Attack Identification & Log Analysis

### Incident Summary
* **Symptom:** Web browsers reported connection timeout errors when attempting to load the sales webpage.
* **Log Findings:** Packet captures revealed an abnormally large volume of **TCP SYN requests** flooding the server from an unfamiliar external IP address.
* **Attack Type Identified:** **TCP SYN Flood (Denial of Service - DoS)**.

### Technical Characteristics of the Attack
1. **The Three-Way Handshake Disruption:** Normal TCP connections rely on a 3-way handshake (`SYN`, `SYN-ACK`, `ACK`). In this attack, the malicious actor bombards the server with `SYN` requests but never responds with the final `ACK`.
2. **Resource Exhaustion:** The web server allocates memory and resources waiting for the handshake to complete, quickly filling its connection tables and becoming unable to respond to legitimate user traffic.

---

## Part 2: Impact, Consequences & Mitigation

### Organizational Impact
* **Operational Disruption:** Employees could not access promotional packages, and customers faced a dead website, halting online sales.
* **Reputational Risk:** Extended downtime leads to lost revenue and diminished customer trust in the company's digital reliability.

### Actions Taken (Response)
1. **Immediate Containment:** Temporarily took the web server offline to allow the machine to purge hanging connections and recover normal operating status.
2. **Firewall Rule Update:** Configured the company firewall to block the offending IP address sending the abnormal flood of SYN packets.

### Long-Term Prevention & Recommendations
Since simple IP blocking is easily bypassed via IP spoofing, the following engineering controls are recommended to prevent future incidents:
* **Enable SYN Cookies:** Allows the server to handle incoming connections without allocating memory until the handshake is fully verified.
* **Rate Limiting & Traffic Shaping:** Restrict the number of incoming connection requests from a single source within a given timeframe.
* **Deploy a Web Application Firewall (WAF) / DDoS Mitigation Service:** Utilize third-party scrubbing services (e.g., Cloudflare or AWS Shield) to filter out malicious traffic before it ever hits the primary web server.
