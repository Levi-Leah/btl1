# BLT1 Notes

[Cheat sheet](files/cheat-sheet.md)

## Security Fundamentals

[Security controls](files/security-controlls.md)

[Networking 101](files/networking-101.md)

[Management principles](files/management-principles.md)

[Active directory](files/active-directory.md)

## Phishing Analysis

<!-- overwritten -->
<!-- [Intro to Phishing and Emails](files/intro-to-phishing.md) -->

[Types of Phishing](files/types-of-phishing.md)

[Tactics and Techniques](files/tactics-and-techniques.md)

[Investigating a Phishing Email](files/investigating-a-phishing-email.md)

[Analyzing Artifacts](files/analyzing-artifacts.md)

[Taking Defensive Actions](files/taking-defensive-actions.md)

[Report Writing](files/report-writing.md)

## Threat Intelligence

[Introduction to Threat Intelligence](files/introduction-to-threat-intelligence.md)

[Threat Actors and APTs](files/threat-actors.md)

[Operational Threat Intelligence](files/operational-threat-intelligence.md)

[Tactical Threat Intelligence](files/tactical-threat-intelligence.md)

[Strategic Threat Intelligence](files/strategic-threat-intelligence.md)

## Digital Forensics

[Introduction to Digital Forensics](files/intro-to-digital-forensics.md)

[Digital Forensics Fundamentals](files/digital-forensics-fundamentals.md)

[Digital Evidence Collection](files/digital-evidence-collection.md)

[Windows Investigations](files/windows-investigations.md)

[Linux Investigations](files/linux-investigations.md)

[Memory Analysis With Volatility](files/memory-analysis-with-volatility.md)

## Security Information and Event Management

[Intro to SIEM](files/intro-to-siem.md)

[Logging and Aggregation](files/logging.md)

[Corelation](files/corelation.md)

## Splunk

[Splunk search](files/sp-search.md)

[Splunk alerts](files/sp-alerts.md)

[Splunk dashboards](files/sp-dashboard.md)

## Preparation Phase

[Introduction to incident response](files/intro-to-incident-response.md)

[Preparation phase](files/ir-prep.md)

## Detection and Analysis Phase

[Detection and Analysis Phase](files/ir-detection-and-analysis.md)

[Intro to Wireshark](files/intro-to-wireshark.md)

[CMD and PowerShell For Incident Response](files/powershell-and-cmd-for-ir.md)

[DeepBlueCLI](files/deepblue-cli.md)

## Case management

[Case management](files/case-management.md)

## Containment, Eradication, and Recovery Phase

[Incident Containment](files/incident-containment.md)

[Taking Forensic Images](files/taking-forensic-images.md)

[Identifying and Removing Malicious Artifacts](files/identifying-malicious-artifacts.md)

[Identifying Root Cause and Recovery](files/identifying-root-cause-and-recovery.md)

## Lessons Learned & Reporting

[Lessons Learned](files/lessons-learned.md)

[Reporting](files/reporting.md)

## MITRE ATT&CK Framework

* collection of tactics and techniques used by adversaries, which can be utilized by both blue and red team members to improve the security posture of an organization
* [MITRE ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/) for defensive roles
* [ATT&CK Training](https://attack.mitre.org/resources/learn-more-about-attack/training/)
* **HISTCONTROL**
  * Adversaries may configure HISTCONTROL to not log all command history. The HISTCONTROL environment variable keeps track of what should be saved by the history command and eventually into the ~/.bash_history file when a user logs out
* Hide your logs, ensure no one can tamper with them, and minimalize the time between a log being generated and it is forwarded to an aggregation point so it can be ingested by the SIEM. Once it’s stored there, the chance of it being modified or deleted by an adversary is extremely low
* [How to Crack Passwords using John The Ripper – Pentesting Tutorial](https://www.freecodecamp.org/news/crack-passwords-using-john-the-ripper-pentesting-tutorial/)
* [NIST SP 800-63B Digital Identity Guidelines](https://pages.nist.gov/800-63-3/sp800-63b.html#sec5)

