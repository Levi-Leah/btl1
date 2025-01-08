# Intro to SEIM

* **Security Information Management (SIM)**
  * specialized security software that helps with the collection, monitoring, and analysis of data and event logs generated from all security devices in a network (IDS, IPS, Antivirus Software, Firewalls)
  * collect data and logs from devices within an organization, and may even collect information from some devices or sources outside the organization (such as public threat identification services and correlation networks), looking for patterns that will allow the system to understand the activity, operation and behavior of these devices
  * Some of the actions performed by a SIM are:
    * Monitoring of events in real-time
    * Sending and generating alerts and reports
    * Automatic response to incidents
    * Correlation of data from multiple sources to improve the quality of the information presented
    * Translation of event logs from different resources through XML files
  * Pros
    * Easy to deploy
    * They can store and analyze large volumes of data
    * They allow a fast and efficient analysis of all events in a system
    * They correlate logs and events to provide the most accurate overview of the system
    * They allow for easy threat management (assessment, containment, and analysis)
  * Cons
    * They can be very expensive tools
    * It is not completely certain that they can be properly adapted to the working environment
    * Some providers do not provide full technical support for this type of service

---

* **Security Event Management (SEM)**
  * security software specialized in the identification, collection, monitoring, evaluation, notification and correlation in real-time of events and alerts of a computer system (network devices, security systems (IDS, IPS, Firewall), specialized software (Antivirus), etc.), whose purpose is to identify “suspicious” behavior within the system
  * SEMs are mainly in charge of monitoring and analyzing in real-time the existing events in an IT system in search of any kind of anomalous behavior 
  * Some of the actions carried out by SEM software are as follows:
    * Real-time events monitoring
    * Obtaining security events in devices and applications within the system
    * Correlation of events to provide a clear picture of the information system
    * Analyze logs according to their level of importance
    * Real-time incident response
  * Pros
    * Centralization of information from different devices and network elements
    * Reduction of false positives and false negatives
    * Considerable improvement in response time to internal and external threats
  * Cons
    * They are hard to deploy
    * They have a high market cost
    * Can present failures that allow for false positives and negatives

---

* **Security Information and Event Management (SIEM)**
  * software solution that aggregates and analyzes activity from different resources across an organization’s entire IT infrastructure
  * combination of SIM and SEM
  * SIEM collects security data from network devices, servers, domain controllers, and more
  * it then stores, normalizes, aggregates, and applies analytics to that data
  * Setting up SIEM tools is a complex task
    * understand your infra, NT, and security stack
    * figure out how to collect relevant logs from them
    * plan for hardware/software as a service
    * write rules to detect events of interest and create reports to highlight key metrics on overall network risk
  * Pros
    * Advanced Threat Detection
      * SIEMs are capable of continuous real-time monitoring and correlation across the breadth and depth of the enterprise; therefore can help detect, mitigate, and prevent advanced threats
    * Forensics and Incident Response
      * SIEMs can help organizations in a forensics investigation by storing and protecting historical logs and providing tools to quickly navigate and correlate the data
    * Compliance Reporting and Auditing
      * SIEM is implemented in response to governmental compliance requirements
        * HIPAA, PCI/DSS, SOX, FERPA, and HITECH
      * can help organizations prove to auditors and regulators that certain requirements are being met
      * aggregates log data from across the organization and presents it in an audit-ready format
    * Other
      * data storage
      * gaining and maintaining certifications (such as ISO 27000, ISO 27001, ISO 27002, and ISO 27003)
      * log management and retention
      * case management ticketing systems
      * policy enforcement validation
      * policy violations

---

* **SIEM Platforms**
  * **Graylog**
    * two different SIEM products
      * Graylog Open Source which is 100% free
      * Graylog Enterprise
        * has a free limit and can be used by small organizations (less than 50 staff) that process less than 2 GB worth of events per day
  * **Arcsight**
    * ArcSight Enterprise Security Management or ESM
    * can integrate with a wide range of commercial security tools
    * offers Security Automation and Response (SOAR) workflows
    * claims to be the fastest way to detect threats from large datasets
  * **QRadar**
    * IBM
    * offers the ability to import data from threat intelligence feeds
    * when purchasing QRadar, clients can also opt-in to subscribe to the paid-for IBM Security X-Force Threat Intelligence
      * identifies malicious indicators, which can be used to provide investigation enrichment, or for immediate alerting
      * additional modules exist for QRadar that can assist security teams with incident response, risk management, and vulnerability management
  * **LogRhythm**
    * uses machine learning, Security Automation and Response (SOAR), End-Used Behavioural Analytics (UEBA), and Network Detection and Response (NDR)
  * **Splunk**
    * SIEM administrators can download and add “Apps” that provide additional functionality to Splunk, such as analytics, dashboards, improved searching, and data manipulation
    * Imported data can be searched using custom-written search queries, which can also be used to generate alerts, and create visual dashboards

---

* **Additional resources**
  * [What is SIEM Software? How it Works and How to Choose the Right Tool by CSO Online](https://www.csoonline.com/article/2124604/what-is-siem-software-how-it-works-and-how-to-choose-the-right-tool.html)
  * [What is SIEM? A Beginners Guide by Varonis](https://www.varonis.com/blog/what-is-siem/)
  * [SIEM Architecture: Technology, Process and Data by Exabeam](https://www.exabeam.com/siem-guide/siem-architecture/)
  * [Standards and Best Practices for SIEM Logging by AT&T](https://cybersecurity.att.com/blogs/security-essentials/what-kind-of-logs-for-effective-siem-implementation)
  * [SIEM Rules or Models for Threat Detection? by Exabeam](https://www.exabeam.com/siem/siem-threat-detection-rules-or-models/)
  * [Tune Down the Noise: How to Effectively Tune Your SIEM by RedLegg Blog](https://www.redlegg.com/blog/how-to-effectively-tune-your-siem)
  * [Detecting a Security Threat in Event Logs by Netwrix](https://blog.netwrix.com/2014/12/03/detecting-a-security-threat-in-event-logs/)
  * [Critical Log Review Checklist for Security Incidents by Lenny Zeltser](https://zeltser.com/security-incident-log-review-checklist/)
  * [Reddit Thread: What Windows Server Events are you Monitoring and Why?](https://www.reddit.com/r/sysadmin/comments/1sq955/what_windows_server_events_are_you_monitoring_and/)
