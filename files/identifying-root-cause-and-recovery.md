# Identifying Root Cause and Recovery

* **Identifying the Root Cause**
  * sometimes obvious, sometimes not so much
  * By taking forensic images of any affected systems, analysts can spend time analyzing the data with the goal of uncovering the actions taken by the malicious actor during the attack
  * important to identify the root cause or it can result in the initial entry point being left open, potentially allowing the attacker to regain access
* **Incident Recovery**
  * fix any systems that were affected by the incident or display similar weaknesses
    * Patching systems with program, operating system, and security updates to ensure that any vulnerabilities are fixed
      * Manual testing should be conducted after patching to ensure the fix has worked
    * Disabling services that are not needed on a system
    * Update endpoint detection and response (EDR), anti-virus (AV), intrusion detection and prevention system (IDPS), and SIEM rules to allow alerting of similar activity that occurred during the incident
    * Share intelligence regarding the incident externally
