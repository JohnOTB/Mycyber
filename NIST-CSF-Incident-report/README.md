# NIST CSF Incident Report: ICMP Flood DoS Attack

An incident report analysis applying the NIST Cybersecurity Framework (CSF) to a denial of service attack on a multimedia company. Completed as part of the Google Cybersecurity Certificate.

## Summary
A multimedia company offering web design, graphic design, and social media marketing to small businesses suffered a DoS attack. A flood of ICMP pings entered through an unconfigured firewall and overwhelmed the internal network for two hours, so normal traffic couldn't reach any network resources. The incident team blocked incoming ICMP packets, took non-critical services offline, and restored the critical ones. The security team then added an ICMP rate-limiting rule, source IP verification, network monitoring, and an IDS/IPS.

## NIST CSF Analysis

**Identify**
The network was compromised by a DoS attack that stopped it responding for two hours. A flood of ICMP packets came in through an unconfigured firewall with no rules to filter or limit ICMP traffic. This disrupted daily operations and showed that the firewall configuration was not properly managed or reviewed.

**Protect**
A new firewall rule limits the rate of incoming ICMP packets, and source IP address verification checks for spoofed addresses. Recommended next steps: regularly review firewall configuration and apply least privilege by allowing only the traffic the business needs.

**Detect**
Network monitoring software watches for abnormal traffic patterns such as a sudden surge of ICMP packets, and an IDS/IPS filters suspicious ICMP traffic. Together they shorten the time between the start of an attack and the team's response.

**Respond**
The incident team blocked incoming ICMP packets, took non-critical services offline, and prioritized critical services. The security team then investigated, found the root cause (the unconfigured firewall), and applied fixes.

**Recover**
Critical services were restored first, and the network was fully back after two hours. Non-critical services returned once the network was stable and the new protections were confirmed in place. Recommended: keep tested backups and a recovery plan that sets restoration priorities.

## Reflection
Proper analysis of attacks helps a lot in handling, resolving, and protecting against them.

## Files
- [`incident-report-analysis.pdf`](./incident-report-analysis.pdf): full incident report

## Skills Demonstrated
NIST CSF, incident response, network security, DoS attack analysis, firewall configuration, IDS/IPS
