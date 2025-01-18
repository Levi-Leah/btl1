# Lessons Learned

* **What Went Well?**
  * simply being given appraisal and feedback can prevent issues such as imposter syndrome and professional burnout
  * Qs to ask:
    * Who performed well?
    * Were any new tools or processes used that provided benefit?
    * Review the metrics that have been collected from the incident
    * Review the communication between different company departments

---

* **What Could be Improved?**
  * Qs to ask:
    * What limitations were there regarding tooling?
    * What limitations were there regarding procedures and guidelines?
    * Did any individuals or departments hinder the incident response? How?
    * Consider how each of the NIST Incident Response Lifecycle stages was weak, and how it can be improved in terms of resources, personnel, and documentation
  * it is important to ensure that there is actually change. There’s no point highlighting these issues if they won’t be fixed
  * fixes could include:
    * More budget for security personnel such as Forensic Analysts, Incident Responders, Incident Commanders, etc
    * More budget for personnel in other departments, such as Legal, Public Relations, Communications, or Human Resources
    * More budget for tools that can assist with incident response activities
    * Review of documentation such as run-books, policies, and procedures

---

* **Importance of Documentation**
  * maintaining an incident response plan (IRP) and response run-books for different scenarios is key to quick and straightforward responses
  * By recording every incident in detail, if a similar one occurs, analysts can refer to the documentation of the old incident for guidance
  * docs to update:
    * **Incident Response Case Notes**
      * Whatever tool the organization uses to record security investigation notes in (such as ServiceNow and IBM Resilient) should be completely updated to ensure that the case contains everything it should
        * e.g. information from all stages of the incident response lifecycle, artifacts should be included, such as file names, file hashes, IP addresses, domain names, etc.
        * Attachments should be added to the case, including emails sent to stakeholders, copies of malicious files, log files, and anything else deemed important to the investigation
    * **Incident Response Plan**
      * Maybe the overall response process could be improved, which should be discussed and any changes be implemented to the organization’s incident response plan (IRP)
      * could include changes to stakeholders that are part of the incident response team, new methods for secure communication, changes to contact numbers or email addresses, and other details that are consistent across all potential incidents
    * **Incident Run-Books**
      * Reviewing run-books for the type of incident that has occurred can help to improve future responses by guiding analysts that respond to the incident in the future
    * **Organization Policies**
      * maybe the incident occurred as a result of an action that wasn’t properly restricted by organizational policies
      * in this case policies should be updated

---

* **Incident Response Metrics**
  * can highlight areas where the team has responded efficiently or ineffectively
  * metrics can also help to identify trends in incidents that the organization is facing so they can be addressed
  * **Impact Metrics**
    * **Service Level Agreement (SLA)**
      * agreement between an organization and its customer that determines expectations for things such as uptime, responsiveness, and responsibilities of both parties
    * **Service Level Objective (SLO)**
      * agreement that exists within the SLA that determines that specific metric being measured, such as the uptime of a critical virtual machine
      * can hold both the organization and potentially the client liable
    * **Escalation Rate**
      * how often alerts in your SIEM are being assigned to the correct security team member
  * **Time-Based Metrics**
    * **Mean Time to Detect (MTTD)**
      * average amount of time it takes for the security team to notice that a security incident has occurred
    * **Mean Time to Response (MTTR)**
      * time from when something is detected, and when the security team can take action to address it
      * often one of the most important metrics to track because it can show how efficient the team was when responding to the incident and can help identify key areas where the response time could improve
    * **Incidents Over Time**
      * average number of incidents over a period of time to determine whether there is an increase or decrease of incidents
      * helps determine whether changes need to be made to allow for more security to prevent incidents or to determine if the lower incident count is correlating to another event.
    * **Remediation Time**
      * how long did it take the incident responders and appropriate stakeholders to remediate the situation, recovering all affected systems and returning to production status
  * **Incident Type Metrics**
    * **Cumulative Number of Incidents Per Types**
      * categorizing incidents based on their type and comparing the total number of each incident category
      * can provide security teams with an overview of where improvements need to be made
    * **Alerts Created per Incident**
      * help analyze how many alerts were created for the specific incident
      * can help see where in the Cyber Kill Chain process, you can improve your defenses
    * **Cost per Incident (CPI)**
      * analyzes the perceived cost of the incident at the affected company
      * could be analyzed in a few different ways
        * analyze the duration of the incident and multiply it by the cost of the security team and/or team members that worked on and resolved the case
        * analyzing the impact that the incident had on the business, such as a loss of sales made, productivity lost, or destruction of equipment or computers
      * can be most useful when a business impact analysis (BIA) has already been conducted with the client to establish the base costs of their organization