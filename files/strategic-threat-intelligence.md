# Strategic Threat Intelligence

![](images/Screenshot%20from%202024-12-29%2010-41-54.png)

* Strategic Analysts tend to focus on the geopolitical activity of hostile nations, working to monitor if there is or will be an increased threat from that nation and their associated Advanced Persistent Threats (APTs) in the future
* **Information Sharing and Analysis Center (ISAC)**
  * typically industry-specific groups comprised of multiple organizations in order to share actionable intelligence such as indicators of compromise, precursors, and information about attacks and threats
  * can be extremely beneficial if members are active, regularly share intelligence, and have online meetings to discuss trends and strategic intelligence surrounding threats
* [ISAC members](https://www.nationalisacs.org/members)

---

* OSINT vs paid sources
  * OSINT
    * should be reviewed and verified, including sources
      * Spamhaus
      * URLhaus
      * AlienVault Open Threat Exchange
      * Virus Share
      * List of Free Threat Feeds
      * Anomali Weekly Threat Briefing
      * US Cybersecurity and Infrastructure Security Agency – Automated Indicator Sharing
      * SANS Internet Storm Center
      * Talos Intelligence – Free Version
    * Paid-For Intelligence
      * can be very expensive, and is likely not a viable option for small to medium organizations
      * it’s advised to identify what kind of intelligence the organization actually requires, based on the threats that have, or may target, the industries that the company operates in
        * FireEye
        * Recorded Future
        * CrowdStrike
        * Flashpoint
        * Intel471

---

> TIP: It’s still important to question and analyze everything, but once you have sources you know and trust, you can use this intelligence to power defenses, provide context, and take not just a reactive approach to security, but a proactive one.
> SW APT29

---

* **Traffic Light Protocol (TLP)**
  * a way of classifying information for sharing and is commonly used for security reports and threat intelligence
  * the purpose of TLP is to allow the author of the original information to state how they want their information to be circulated, such as sharing only with specific individuals, within an organization, within trusted communities, or in the public domain
  * **TLP classifications**
    * **Clear**
      * can be publicly shared, but copyright rules still apply
    * **Green**
      * may be shared within communities, such as ISACs
      * should not be shared outside of the intended communities, such as posting it publicly on the internet
    * **Amber**
      * may only be shared internally, or with clients of the organization, on a need-to-know basis
        * Penetration test reports, red team engagement reports, and vulnerability scan results are likely to be TLP AMBER
    * **Amber Strict**
      * may only be shared internally
    * **Red**
      * extremely sensitive
        * if an online or in-person meeting is classed as TLP RED then the information should not be shared with anyone that isn’t present in the meeting
        * if an email is TLP RED then only the listed recipients should be exposed to the material

---

<!-- TODO: look into PAP -->
* **Permissible Action Protocol (PAP)**
  * a framework designed to classify actions based on the potential exposure of sensitive data to malicious entities
  * **Clear**
    * information can be handled as desired provided they align with legal and licensing frameworks
  * **Green**
    * permits controlled, non intrusive actions with malicious sources
  * **Amber**
    * confined to passive data handling, ensuring actions remain undetected by malicious sources
  * **Red**
    * centered exclusively around detection and investigation of the threat actor