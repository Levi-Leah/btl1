# Security controls

## Physical Security

Physical security prevents unauthorized access to buildings or areas using:

- **Deterrents**:
  - Warning signs
  - Fences
  - Guard dogs
  - Security lighting (to improve visibility in dark areas)
  - CCTV
- **Monitoring**:
  - CCTV (dual-purpose for deterrence and evidence)
  - Security guards
  - Intrusion detection systems (IDS)
- **Access Controls**:
  - Restricted access to secure areas using:
    - RFID badges
    - Mantraps
    - Turnstiles
    - Gates
    - Electronic doors

---

## Endpoint Security

- **Host Intrusion Detection System (HIDS)**:
  - Monitors activity against rules to detect suspicious patterns.
  - Generates alerts and forwards them to SIEM platforms.
- **Host Intrusion Prevention System (HIPS)**:
  - Similar to HIDS but can autonomously act to prevent malicious activity.
- **Antivirus (AV)**:
  - **Signature-based**: Matches malware signatures to known threats.
  - **Behavior-based**: Monitors deviations from normal activity.
- **Endpoint Detection and Response (EDR)**:
  - Logs and monitors endpoint activity.
  - Enables threat investigation through centralized platforms.
- **Log Monitoring**:
  - Sends endpoint logs to SIEM for analysis and threat detection.
- **Vulnerability Scans**:
  - **External**: Simulates an attacker’s view of internet-facing systems.
  - **Internal**: Reviews internal systems but doesn’t reflect external attack vectors.
  - **Credentialed**: Provides detailed configuration insights.
  - **Non-credentialed**: Simulates an attacker’s perspective to prioritize vulnerabilities.
- **Compliance Scanning**:
  - Ensures endpoints meet regulatory security standards using pre-configured scanner profiles.

---

## Email Security

- **Phishing**: The most common attack vector.
- **Spam Filters**:
  - Block suspicious or malicious emails based on predefined patterns.
- **Data Loss Prevention (DLP)**:
  - Monitors outgoing emails for sensitive data in headers, body, or attachments.
  - Blocks potentially harmful emails using keywords, regex, or predefined rules.
- **Email Scanning**:
  - Identifies malicious links or attachments using blacklists, patterns, and signatures.
  - Quarantines suspicious emails.
- **Security Awareness Training**:
  - Educates employees to identify phishing attempts.

---

## Network Security

- **Network Intrusion Detection System (NIDS)**:
  - **Passive**: Monitors traffic through mirrored SPAN ports.
  - **Inline**: Sits directly in traffic paths; can act as a Network Intrusion Prevention System (NIPS).
  - **Network Tap**: Directly taps into network cables to monitor traffic.
- **Network Intrusion Prevention System (NIPS)**:
  - Automatically blocks malicious activity.
- **Firewalls**:
  - **Standard**: Dedicated hardware separating network zones.
  - **Local**: Software firewalls on endpoints (e.g., Windows Firewall).
  - **Web Application Firewall (WAF)**: Protects internet-facing applications.
- **Log Monitoring**:
  - **Web Proxy Logs**: Tracks employee web activity and flags malicious sites.
  - **Perimeter Firewalls**: Detects scans, DDoS attempts, or other anomalies.
- **Network Access Controls (NAC)**:
  - Enforces security policies (e.g., patches, AV) for BYOD or guest devices.

---

## AAA Control Methods

The **AAA framework** ensures access is restricted to authorized users while monitoring actions:

- **Authentication**:
  - Verifies user identity through:
    - Something you know (password, PIN).
    - Something you have (RFID badge, key).
    - Something you are (biometric systems).
  - Multi-factor authentication (MFA) uses two or more factors.
- **Authorization**:
  - Grants access based on the Principle of Least Privilege (minimum required access for the job).
- **Accountability**:
  - Tracks actions for auditing and evidence during incidents.

---
