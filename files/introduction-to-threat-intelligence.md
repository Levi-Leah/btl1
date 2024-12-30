# Introduction to Threat Intelligence

- threat intelligence is information that an organization uses to understand the threats that are currently targeting them, or could target them in the future
- aims to provide information on more sophisticated threats
  - Advanced Persistent Threats (APTs)
  - zero-day vulnerabilities
  - global malware campaigns
- help the organization to understand who is/could be attacking them, why they’re doing it, and the tactics they use
- can be replicated in penetration tests, red team engagements, or inform defensive measures
- actual intelligence is shared in the form of indicators of compromise (IOCs)
  - artifacts that have been observed in relation to malicious activity:
    - email addresses that have been sending malicious emails
    - IP addresses that are hosting websites trying to steal user’s account details
    - file-based artifacts such as a malware file name, file size, or its’ hash value

---

## Threat Intelligence Lifecycle

- can vary depending on which organization you’re looking at, e.g. Recorded Future and CrowdStrike
- **Planning & Direction**
  - most crucial part
  - goals need to be set, and the stakeholders need to be clearly defined to not waste time and resources working on intelligence that is not important
- **Collection**
  - the team will go out and collect all of the data they need to achieve their end goal of creating actionable intelligence
    - e.g., scraping posts from forums, OSINT, etc.
  - mature threat intelligence teams typically use a centralized threat intelligence platform (e.g., MISP) to store IOCs from a range of public and private threat feeders
    - lists of actionable intelligence shared between organizations
- **Processing**
  - data needs to be transformed into a clear and readable format so that it can be analyzed
  - typically done by human threat intelligence analysts
  - can include translations
- **Analysis**
  - processed data is turned into actionable intelligence that can be used by a human analyst
  - the decisions might involve:
    - investigating a potential threat
    - what actions to take immediately to block an attack
    - how to strengthen security controls
    - how much investment in additional security resources is justified
  - information needs to be presented in an appropriate manner based on the audience
- **Dissemination**
  - getting the finished intelligence output to the places it needs to go
  - For each of these audiences, you need to ask:
    - What threat intelligence do they need, and how can external information support their activities?
    - How should the intelligence be presented to make it easily understandable and actionable for that audience?
    - How often should we provide updates and other information?
    - Through what media should the intelligence be disseminated?
    - How should we follow up if they have questions?
- **Feedback**
  - your audience should tell you:
    - What types of data to collect
    - How to process and enrich the data to turn it into useful information
    - How to analyze the information and present it as actionable intelligence
    - To whom each type of intelligence must be disseminated
    - How quickly it needs to be disseminated
    - How fast to respond to questions

---

## Types of Intelligence

- **SIGINT**
  - signal intelligence
  - interception of radio signals and broadcast communications to gather intelligence
  - came about during WWI
  - used in electronic warfare through surveillance drones, unmanned aerial vehicles (UAVs), and communications interceptions between foreign governments
  - falls under 2 categories:
    - **COMINT**
      - intelligence related to communications between people
      - used as a synonym for SIGINT but actually falls under SIGINT
    - **ELINT**
      - electronic intelligence collected from systems not used directly for communications
        - e.g., guidance communication for missile systems and radars
- **OSINT**
  - open-source intelligence
  - info gathered from public sources
  - e.g, driving records, telephone numbers, street addresses, social messaging and social network information, email addresses, domain names, etc.
  - double-edged sword as it can be used by threat actors as well
- **HUMINT**
  - human intelligence
  - info gathered from other humans
  - requires an understanding of how humans feel, think, and act
  - often gathered through in-person meetings, observation, document gathering, etc.
  - can be attained through espionage or open communications between diplomats
- **GEOINT**
  - geospatial intelligence
  - e.g., satellite imaging is highly used to provide intelligence personnel with targets, landmass structures, and whether they’re manmade or natural, where our militaries are and their enemies, to better coordinate attack and defense efforts
  - helpful during times of natural disasters, wartime, or through other major events, such as political turmoil

---

## Types of Threat Intelligence

- **Strategic Threat Intelligence**
  - high-level, typically non-technical information that can be understood by anyone
  - typically used to present to executives to aid with decisions such as budget spending and policy review or creation
  - can be very geographically and politically focused
  - often related to a specific industry the org operates in
  - tracks threat actors which have been linked to regions or countries that may pose a threat to the organization based on the industries it operates in
  - examples:
    - global events and their link to cyberattacks
      - increased phishing attacks during COVID
    - patterns of cyber attacks that the organization is facing over a period of time
      - org is receiving more DDoS attacks on Monday, and suggesting plans to mitigate this
    - informing internal security teams about activity related to threat actors that target organizations operating in the same industries
      - threat intelligence team in a bank monitoring for attacks against other banks
- **Operational Threat Intelligence**
  - studying threat actors that might target the organization and gain information about who they are, their motivations, and tactics, techniques, and procedures (TTPs)
  - helps build more effective defenses by actively monitoring techniques that are used by adversaries
  - is not easily automated and requires human analysts to track and research malicious groups
- **Tactical Threat Intelligence**
  - technical in nature and is of immediate value to an organization
  - typically shared in the form of IOCs
    - known malicious artifacts such as URLs, domains, email addresses, file hashes, IP addresses, and more
  - can either be used by human analysts to check for exposure or can be ingested by security tools via APIs or threat feeds

---

## Usefulness of Threat Intelligence

- **Cyber Threat Context**
  - allows the business to perform in-depth research on the threats that are out there, and use historic events and targeting to truly determine the risk
  - allows orgs to take proactive defense measures
    - give VM team context around vulnerabilities to prioritize patching, hence reducing the attack surface
- **Incident Prioritization**
  - threat intelligence can potentially give IRs the information to make informed decisions about which incident to prioritize
- **Investigation Enrichment**
  - example:
    - IPs scanning the org's public IP range is very common
    - these IPs are either blocked (if they are sending a high volume of requests) or left alone as the perimeter firewalls are actively blocking them
    - if the threat intelligence states that this IP has been utilized by APT, such as a foreign nation-state, this definitely needs more analysis to see exactly what the IPs in question are scanning for
- **Information Sharing**
  - you acn improve your org's security posture by simply seeing how other organizations manage their security and the tools they use

---

## The Future of Threat Intelligence

- CVEs, SBOMs, VEX, etc.
- predictive prioritization by Tenable
  - the company behind the Nessus vulnerability scanners and auditing tools

---
