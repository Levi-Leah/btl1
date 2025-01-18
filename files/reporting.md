# Reporting

* **Reporting Format**
  * no standard format exists
  * **Executive Summary**
    * typically where the high-level overview of the incident will go, using non-technical terms to clearly state the business impact
    * easily readable and contains information that is important to executives
    * should ideally be one page and focus on areas such as business risks, financial costs, and damage that occurred and prevented
    * great place to really highlight the work of the security team and how they have prevented more damage and costs from happening
  * **Incident Timeline**
    * timeline will provide the date, time, and short descriptions of all key events throughout the incident
    * can either be in the order these actions were taken or discovered, or re-ordered to be in chronological order to make it easier to read exactly what has happened from start to finish
    * common to see security teams use either their local timezone (provided the incident has only affected one geographic location) or Universal Time Coordinated (UTC) if the incident affects users or systems across multiple timezones
  * **Incident Investigation**
    * bulk of the report, providing step-by-step documentation of actions that were conducted and the associated findings of the incident responders
    * All stages of the incident response lifecycle should be considered and reported on, with the exception of preparation
      * **Detection and Analysis**
        * How was the incident discovered?
        * How was this activity triaged to ensure it was an incident and not a false positive?
        * Screenshots should be used to show exactly what actions were taken, and what the investigating responders saw when performing analysis
      * **Containment, Eradication, and Recovery**
        * How was the incident scoped?
          * need to ensure we’ve found all affected systems to prevent reinfection at a later date
        * How did the security team remove the actor(s) from the networks?
        * What was the root cause?
      * **Post-Incident Activity**
        * What could have been done better?
        * Anything major should be included in the executive summary to ensure that it is seen by the top-level business decision-makers
  * **Appendix**
    * used as storage for the report, and will typically include images or figures (graphs, tables) that will be referenced in the main body of the report
  * **Report Templates**
    * no one size fits all

---

* **Reporting Considerations**
  * **Report Audience**
    * **Executive Summary**
      * should be short, sweet, and talk about the whole incident at a high-level
      * technical terms and phrases should be avoided and the incident should be explained using business risks
    * **Rest of the Report**
      * typically be aimed at technical staff so this should include a lot of detail, annotated screenshots, and should use technical language where appropriate
  * **Incident Investigation**
    * needs tp be very detailed
    * any points you make need to be backed up with evidence, otherwise it is just speculation
    * it’s helpful to also include the MITRE ATT&CK tactics that were used
  * **Screenshots and Captions**
    * great way to provide evidence
    * images should also be captioned with a short sentence or two, summarizing what is being shown in the screenshot