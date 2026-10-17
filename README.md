Incident Response & SOC Analysis Case Study

Role: Cyber Security Intern

Domain: Security Operations Center (SOC) / Blue Team

🛡️ Project Overview

This repository contains a simulated Incident Response report detailing the detection, containment, and eradication of a cyber threat involving compromised credentials and malware execution. It demonstrates hands-on understanding of the incident response lifecycle and enterprise security tools.

🛠️ Tools & Technologies Simulated

SIEM: Splunk (Log analysis, brute-force detection)

EDR: CrowdStrike Falcon (Endpoint isolation, malware quarantine)

Firewall: Palo Alto Networks NGFW (Traffic analysis, IP blocking)

Identity Management: Microsoft Active Directory (Account suspension)

⏱️ Incident Timeline (Chronology of Events)

09:15 AM: SIEM triggers an alert for 50+ failed login attempts (Brute Force) on the corporate VPN gateway targeting the user account jsmith.

09:35 AM: Successful VPN login recorded for jsmith from an anomalous IP address outside the operating country.

10:05 AM: EDR triggers a high-severity alert indicating the execution of a suspicious payload named update_patch.exe on the jsmith-Workstation.

10:15 AM: Firewall logs detect unusual outbound network traffic from jsmith-Workstation to an unknown external IP address over port 443 (suspected C2 communication).

🔍 Incident Response Lifecycle

1. Identification & Classification

Category: Unauthorized Access & Malware Infection.

Root Cause: The attacker successfully brute-forced a weak VPN password (due to a lack of MFA) and deployed a malware payload to establish a reverse shell.

2. Containment Strategy

Endpoint Isolation: Placed jsmith-Workstation into "Network Containment" via CrowdStrike Falcon to sever corporate network access while maintaining a forensic channel.

Network Blocking: Blacklisted the malicious external C2 IP address globally on the Palo Alto Firewall.

Account Suspension: Disabled the jsmith account in Active Directory and terminated active sessions.

3. Eradication & Recovery

Malware Removal: Quarantined and deleted update_patch.exe and associated registry persistence keys via the EDR response shell.

Restoration: Mandated a complex password reset for the compromised user and lifted endpoint network containment after verifying a clean system state through a deep scan.

4. Lessons Learned & Preventive Actions

Enforce MFA: Implement Multi-Factor Authentication (e.g., Okta/Duo) for the corporate VPN to neutralize credential-based attacks.

Tune SIEM Alerting: Refine Splunk correlation rules to trigger alerts at lower failure thresholds (e.g., 10 failed logins/5 mins).

Geo-Blocking: Configure the firewall to drop authentication attempts from unapproved geographic regions.

Endpoint Execution Prevention: Update EDR policies to block the execution of unapproved, unsigned internet-downloaded binaries.

Disclaimer: This is a conceptual case study created as part of a Cyber Security Internship final project to demonstrate SOC methodologies.
