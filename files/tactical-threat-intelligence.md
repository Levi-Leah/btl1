# Tactical Threat Intelligence

* **Exposure Checks**
  * when an analyst uses multiple tools such as SIEM and EDR to look for the presence of any indicators of compromise they have retrieved from intelligence vendors, information sharing partners, government alerts, or OSINT sources
    * e.g., searching if known malicious IPs have been scanning org's ports
  * requires a deep technical understanding

---

* **Watchlists/IOC Monitoring**
  * IOC monitoring for the presence of any precursors or indicators of compromise across the environment
  * Watchlists are typically created in either the SIEM or EDR platform (or both)
  * allows Threat Exposure Checks (TECs) to be conducted continuously without a need for a human analyst
    * e.g., create a watchlist within the SIEM platform to generate an alert whenever a malicious IP address is observed as either the Source or Destination IP

---

* **Public Exposure Checks**
  * the process a threat intelligence analyst takes to determine what information is publicly available online about their organization, and if this can be exploited in any way to cause damage
  * ranges from employees posting pictures of them in the office on social media to employee credentials in data breach dumps for sale on the dark web

---

* **Threat Intelligence Platforms (TIPs)**
  * can be deployed as Software-as-a-Service or an on-premises solution to manage a large volume of cyber threat intelligence
    * actors
    * campaigns
    * signatures
    * bulletins
    * TTPs
  * provide the following functionality
    * Aggregation and normalization of intelligence collected from multiple sources
    * Integration with existing security controls such as firewalls and IPS
    * Analysis and sharing of threat intelligence
  * TIPs automatically collects and reconciles data from various sources and formats
  * **TIP Sources**
    * Open-source
    * 3rd party paid
    * Government
    * Trusted Sharing Communities (ISACs)
    * Internal
  * **TIP Formats**
    * STIX/TAXII
    * JSON and XML
    * Email
    * .csv, .txt, PDF, Word document
  * **TIP Products**
    * **Malware Information Sharing Platform (MISP)**
      * open-source, community-ran project
    * **ThreatConnect**
      * can completely automate the intelligence collection process, regardless of the source format
      * provides automation in the form of runbooks
    * **Anomali**
      * offers the ability for an organization to quickly and easily create its own Information Sharing and Analysis Center (ISAC), allowing other organizations to partner together and share intelligence together
      * offers an “app store” where organizations can purchase integrations and threat feeds to boost the capabilities or the TIP
    * **ThreatQ**
      * allowing security teams to “prioritize based on threat and risk, collaborate across teams, automate actions and workflows and integrate point products into a single security infrastructure”
      * can assist with security practices such as Vulnerability Management, Spear Phishing, Incident Response, and Threat Hunting

---

* **Malware Information Sharing Platform (MISP)**
  * 