# Network Hardening Analysis

A security risk assessment for a social media company after a data breach that exposed customers' names and addresses. Completed as part of the Google Cybersecurity Certificate.

## Vulnerabilities Found
- Employees share passwords
- The database admin password is still the default
- Firewalls have no rules filtering incoming or outgoing traffic
- Multifactor authentication (MFA) is not used

## Hardening Methods Recommended

| Vulnerability | Method | Why it works | How often |
|---|---|---|---|
| Shared passwords | **Network access privileges** | Permits, limits, or blocks access to network assets by person, role, group, IP, or MAC address. Reduces unauthorized access to the internal network. | Set up once, revisit depending on social engineering risk |
| Default admin password | **Password policy** | Following current NIST standards stops attackers guessing passwords manually or with scripts using stolen credentials. | Ongoing, kept in line with the latest standards |
| No firewall rules | **Firewall maintenance** | Regularly checking and updating configurations, and adding rules after abnormal traffic events, protects against attacks such as DDoS. | Regularly, and after incidents |
| No MFA | **Multifactor authentication** | Requires two or more ways to verify identity (password, PIN, badge, OTP, fingerprint). Helps defend against brute force attacks. | Set up once, then maintained |

## Files
- [`Security-risk-assessment-report.docx`](./Security-risk-assessment-report.docx): full security risk assessment report

## Skills Demonstrated
Network hardening, access control, password policy, firewall management, MFA, security risk assessment 
