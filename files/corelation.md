# Corelation

* **Normalization**
  * merges events containing different data into a reduced format that contains common event attributes
    * most logs capture the same basic information – time, network address, operation performed, etc
  * different software, hardware, and devices produce their own format of logs, as there is no universal format
  * SIEM log normalization is the process of changing log formats into a format that is as similar as possible across all devices and log sources
* **Log Enrichment**
  * adding additional info that can make the overall data more beneficial when investigating alerts
    * lookup geo location for public IPs
* **Log Indexing**
  * SIEMs can hold an absolute ton of data; looking through them can be very slow
  * indexing attributes that are shared by a large number of logs can make searching for specific attributes across large data faster
* **Log Storage**
  * while alternatives to on-premises servers exist, such as Amazon Web Services S3 buckets or Hadoop, it is important for teams to consider all of their options, weighing in factors such as cost, ease-of-use, and scalability

---

* **SIEM Rules**
  * search queries that are looking for specific activity, looking at any imported or real-time data that is being fed into the SIEM solution
  * rule query matches a piece of data, different actions can be triggered, such as generating an alert, sending an email to a team, or recording the activity to a separate location
  * search queries can be running continuously (real-time detection), or set to run at specific scheduled times
  * can be provided by the SIEM provider as ‘out-the-box’ functionality to detect generic attacks and suspicious patterns
  * can be human-written rules that are developed by the defenders of the organization
  * examples:
    * **Authentication/Account Activity**
      * Failed logon attempts
      * Successful/failed login attempts to disabled accounts
      * Use of specific accounts
        * local administrator, administrator, domain administrator
      * SID (Security Identifier) changes to an account
        * a potential indicator of privilege escalation
    * **Process Execution**
      * Execution from unusual locations
        * such as temporary directories or browser caches
        * may indicate malware execution or persistence mechanisms
      * Suspicious process relationships
        * such as Microsoft Word spawning a child process of CMD or PowerShell window
        * potentially a malicious macro that is executing code
      * Known bad hashes
        * MD5, SHA1, SHA256 hashes that are generated from confirmed malicious files
    * **Network Activity**
      * Port scans
      * Service enumeration
      * Host discovery

---

* **False Positive Reduction and Tuning**
  * alerts that have been generated but do not actually represent a malicious event
    * e.g. monitoring Windows Event ID 4625 – ‘An account failed to log on’
    * Everyone has entered their password in wrong once or twice, so creating a rule that looks for single occurrences of login failures isn’t going to provide much value, and will be very noisy
    * We can set a rule threshold, so if an account fails to log in 10 times within 10 minutes, then generate an alert
  * In some cases the rule may need to be altered to specify that some values should be ignored
    * e.g. a rule that looks at firewall logs to identify network scanning activity where one source IP is sending traffic to a high number of internal systems
    * if you got a vulnerability scanner you can choose to exclude its source IP from the rule

---

* **Sigma**
  * generic and open signature format that allows you to describe relevant log events in a straightforward manner
    * essentially a yml file
  * rule format is very flexible, easy to write, and applicable to any type of log file
  * purpose of this project is to provide a structured form in which researchers or analysts can describe their detection methods and make them shareable with others
  * rules can be written in the Sigma language and then using a converter (Sigmac) they can be exported as rules in the correct format for a number of different SIEM platforms
    * can be done in reverse too
  * helps avoid vendor lock-in
    * you can flexibly change the SIEM solution without having to lose all of your custom rules
  * platforms that support sigma:
    * Splunk
    * QRadar
    * ArcSight
    * Elasticsearch (Elastalert, Query strings, DSL, Watcher, & Kibana)
    * Logpoint
  * [Sigma GitHub](https://github.com/SigmaHQ/sigma)
  * [Sigma rules dir GitHub](https://github.com/SigmaHQ/sigma/tree/master/rules)