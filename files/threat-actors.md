# Threat Actors

Threat actors can be categorized into 4 groups:

* **Cyber Criminals**
  * skill level may vary; includes skript kiddies
* **Nation-States**
  * also known as Advanced Persistent Threats (APTs)
* **Hacktivists**
  * DDoS and website defacement (changing the content on a website’s homepage to display a message or image) are common
* **Insider Threat**

---

## Motivations

* **Financial Motives**
  * Individual
  * Cyber crime
  * Government
    * Lazarus
* **Political Motives**
  * Cyberwar
  * Hacktivists
  * Disinformation campaigns
* **Social Motives**
  * making a statement and voicing your opinions on a subject that is important to you
  * trying to boost your reputation or social status
    * Script kiddies
    * Lizard Squad
      * disbanded group
      * known for conducting DDoS attacks against gaming companies, whilst tweeting on Twitter to gain attention
* **Unknown Motives**
  * can make attribution harder as we can’t use patterns to link the actor or actors to an established and documented threat group

---

## Actor Naming Conventions

* threat intelligence vendors or security firms use their own naming conventions
* some vendors may have multiple names for one single group
* threat actors tend to share tools, so that indicators from one group may be the same as multiple other groups
* some groups use infrastructure in other countries to throw security researchers off
* some are copying the tactics and techniques used by other groups.

---

### CrowdStrike

* nation-state adversaries are categorized based on the countries they operate in by using [animals](https://www.crowdstrike.com/adversaries/)
* Non-nation-state adversaries are categorized by intention

| **Adversary Type**          | **Country or Group**   | **Examples**             |
|-----------------------------|------------------------|--------------------------|
| 🐻 **Bear**                 | Russia                | Fancy Bear               |
| 🐃 **Buffalo**              | Vietnam               |                          |
| 🏇 **Chollima**             | North Korea           | Stardust Chollima        |
| 🐦 **Crane**                | South Korea           |                          |
| 🐱 **Kitten**               | Iran                  | Refined Kitten           |
| 🐆 **Leopard**              | Pakistan              | Mythic Leopard           |
| 🐼 **Panda**                | China                 | Goblin Panda             |
| 🐅 **Tiger**                | India                 | Viceroy Tiger            |
| 🦊 **Jackal** (Hacktivists) | Activist groups       |                          |
| 🕷️ **Spider** (Criminals)   | eCrime Groups         | Mummy Spider (Emotet)    |

---

### Mandiant/FireEye

* use the term “APTxx” where xx is a number, such as APT28 or APT39
* numbers are taken from internal country codes

* 🌏 **Nation-State-Based Adversaries**

  | **Adversary Type**        | **Group/Designation**                | **Details/Examples**                                        |
  |----------------------------|---------------------------------------|------------------------------------------------------------|
  | 🐼 **China**               | APT1, APT2, APT3, APT10, APT19, APT20, APT30, APT40, APT41 |                                                            |
  | 🐱 **Iran**                | APT33, APT34, APT35, APT39           |                                                            |
  | 🏇 **North Korea**         | APT37, APT38                         |                                                            |
  | 🐻 **Russia**              | APT28, APT29                         |                                                            |
  | 🐃 **Vietnam**             | APT32                                |                                                            |

* 💰 **Financially-Motivated Cybercrime Groups**

  | **Adversary Type**        | **Group/Designation**                | **Details/Examples**                                        |
  |----------------------------|---------------------------------------|------------------------------------------------------------|
  | 🕵️‍♂️ **FIN Groups**        | FIN4, FIN5, FIN6, FIN7, FIN8, FIN10  | Example: FIN7 targets U.S. retail, restaurant, and hospitality sectors. |
  | ❓ **Unclassified Groups** | UNC (Unclassified)                   | Groups under analysis or with unclear attribution.         |

---

## Tools, Techniques, Procedures

* TTPs are the actions that threat actors take when conducting cyber attacks
* MITRE’s ATT&CK Framework has over 260 different techniques mapped and split into 12 different categories: 
  * Initial Access
  * Execution
  * Persistence
  * Privilege Escalation
  * Defense Evasion
  * Credential Access
  * Discovery
  * Lateral Movement
  * Collection
  * Command and Control
  * Exfiltration
  * Impact
* if a threat actor follows a specific TTP path, you can see if any known APTs follow a similar path, and then to a reasonable degree attribute the attack to that group
* you can then start implementing defenses against other tactics and malware this group uses as a proactive measure