# Incident Containment

* assists to limit and prevent further damage from happening along with ensuring that there is no destruction of forensic evidence that may be needed for legal actions against the attackers later
* **Short-Term Containment**
  * to prevent the asset or the user from causing further damage to the organization
    * usually blocking/isolating the affected system/account
  * does not fix the real reason  behind an incident
  * does not stop an incident from recurring
* **Long-Term Containment**
  * enterprise-wide fix that is a step short of complete remediation of an incident
    * Patching vulnerabilities
    * Implementing new security tools
    * Reevaluating account permissions
* **Containment Measures**
  * **Perimeter Containment**
    * Block inbound traffic and outbound traffic
    * IDS/IPS Filters to identify further malicious traffic and take automated actions, such as blocking active connections
    * Web Application Firewall policies, to detect and take action against web attacks
    * Null route DNS, to prevent DNS resolutions so internal hosts cannot find the IP address of a given domain name and establish a connection
  * **Network Containment**
    * Switch-based VLAN isolation, to restrict network access
    * Router-based segment isolation, to restrict network access
    * Port blocking, to prevent connections on specific ports
    * IP or MAC Address blocking, to restrict network access
    * Access Control Lists (ACLs), to provide rules that restrict what hosts on the network can and cannot do
  * **Endpoint Containment**
    * Disconnecting the infected system from any network connections (turning WiFi off, pulling ethernet cable)
    * Powering off the infected system
    * Blocking rules in the local firewall
    * Host intrusion prevention system (HIPS) actions, such as device isolation

---