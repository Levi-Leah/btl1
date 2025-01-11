# Introduction to incident response

* Incident response is the methodology an organization uses to respond to and manage a cyber attack
* **Security Events**
  * anything that could have a security implication, such as causing damage or disruption
  * happen constantly, and are typically dealt with by automated security controls or simply logged in case they evolve into security incidents
    * spam emails
    * vulnerability scans
    * recon scan
    * explained anomaly
      * an unusual circumstance, but the cause is identified and it is not malicious
      * e.g., disruption on the network caused by a misconfiguration
    * user downloading software
    * brute-force attack
* **Security Incidents**
  * security events that have resulted in damage to the organization
    * all the same points apply as for security events but thewy got damage
    * except it's an **un**explained anomaly
      * an unusual circumstance, where the root cause has not yet been identified
      * classed as an incident, as until this has been properly scoped, there is the potential for malicious activity
* **Security Events vs Security Incidents**
  * security events will typically be dealt with by security analysts 
  * security incidents are often handled by specialist incident responders

---

* **Incident Response Lifecycle**
  * most Incident Response Plans (IRPs) are based on [NIST SP 800-61r2 - Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)
  * Incident Response Lifecycle is split into 4 different categories
  ![](images/Screenshot%20from%202025-01-12%2003-12-16.png)
    * **Preparation**
      * **being prepared for incidents**
        * Contact Information for all stakeholders
        * Having a war room for central communication and coordination
        * Documentation
        * Baselines for running systems
        * Equipment that can be used in an IR scenario, such as digital forensic toolkits
      * **actively preventing incidents**
        * Having current risk assessments
        * Utilizing Client and Server security
        * Having a user awareness and training program established
    * **Detection and Analysis**
      * **detections**
        * having intrusion detection and prevention systems (IDPs), antivirus/antispam/antimalware software, and log monitoring solutions set up to alert the appropriate team when incidents are detected
        * **analysis**
          * involves finding how the initial attack took place and how it moves throughout the network
      * responder needs to be able to effectively document their finding when analyzing the attack, as well as prioritize actions that need to be taken place, and then the IR team needs to notify the proper authorities (Communication Plan)
    * **Containment, Eradication, Recovery**
      * **containment**
        * Potential damage to and theft of resources
        * Need for evidence preservation
        * Service availability
        * Time and resources needed
        * Effectiveness
        * Duration of the solution
      * **eradication and recovery**
        * returning your systems back to normal
          * rebuilding machines from known good backups, deleting a malware, or resetting credentials on compromised accounts
        * could also include eliminating any vulnerabilities that were exploited in the attack, as well as changing passwords, installing patches, tightening network security, etc.
    * **Lessons Learned**
      * NIST recommends holding a “lessons learned” meeting that could address the following questions:
        * Exactly what happened and when did it happen?
        * How well did staff and management perform in dealing with the incident?
        * What information was needed sooner?
        * Were any steps or actions taken that might have inhibited the recovery?
        * What would staff and management do differently the next time a similar incident occurs?
        * How could information sharing with other organizations have been improved?
        * What corrective actions can be taken?
        * What indicators should be watched for in the future?
        * What additional tools or resources are needed to mitigate future incidents?

---

* **CSIRT and CERT**
  * Cyber Emergency Response Team (CERT) or Cyber Security Incident Response Team (CSIRT)
  * The term CSIRT is more often associated with teams that businesses adopt for internal cybersecurity breaches and are not designated as nationally recognized response teams
  * core responsibilities are coordinating and responding to IT security incidents and determining how these incidents can impact the organization or government entity
  * CSIRTs often contain key stakeholders from different business units, such as; infrastructure, networking, legal and public relations, communications, security, and more, providing the CSIRT the ability to address all aspects of the company in an emergency

---

## Incident Response Resources

* Incident Response Consortium | The First & Only IR Community

* [Incident Response Resources From Infosec Institute](https://resources.infosecinstitute.com/category/incident-response-resources/)

* [A Curated List of Tools for Incident Response](https://github.com/meirwah/awesome-incident-response)

* [Incident Response Tools by AT&T Cybersecurity](https://cybersecurity.att.com/resource-center/ebook/insider-guide-to-incident-response/incident-response-tools)

* [Proactive Incident Response by Secureworks](https://www.secureworks.com/centers/proactive-incident-response)

* [Incident Handler’s Handbook by SANS](https://www.sans.org/reading-room/whitepapers/incident/paper/33901)

* [Ultimate Guide to Cybersecurity Incident Response by TechTarget](https://searchsecurity.techtarget.com/Ultimate-guide-to-incident-response-and-management)

* [A Beginners Guide to Open Source Incident Response Tools and Resources by Cybersecurity Insiders](https://www.cybersecurity-insiders.com/beginners-guide-to-open-source-incident-response-tools-and-resources/)
