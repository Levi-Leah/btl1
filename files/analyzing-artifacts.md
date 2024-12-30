# Analyzing Artifacts

- you should always include the reputation checks you performed in your report

## Manual Analysis

### URL Visualization Tools

- give u a screenshot of what the webpage looks like
- it's not required to attach a visual to your report but it's nice
  - **URL2PNG**
    ![](images/Screenshot%20from%202024-12-23%2019-09-15.png)
  - **URLScan**
  - ![](images/Screenshot%20from%202024-12-23%2019-08-15.png)
    - apart from screenshot gives you some other stats too
      - e.g., verdict if the webpage is malicious
      - information can be useful during high-profile investigations, typically using URL2PNG for visualization will be enough

### URL Reputation Tools

- if something is not being identified as malicious by online reputation tools, it does not mean it is safe
- assume that suspicious sites are malicious until you can prove otherwise
- reputation sites can be a good resource, but they are not always effective, and further analysis is always needed
- targeted and unique attacks will not have been analyzed by other security professionals, therefore URLs could come back with no negative comments

- reputation tools:
  - **VirusTotal**
  - **URLScan.io** (same as the visualization tool)
- **Threat Feeds**
  - [**URLhaus**](https://urlhaus.abuse.ch/browse/)
    - a huge collection of malicious URLs reported by researchers
    - includes:
      - the date the URL was added to the database
      - the malicious URL
      - the status showing whether this resource is still available on the internet
      - tags that show what the malware is
      - which user reported these URLs
    - [threat feeds](https://urlhaus.abuse.ch/feeds/) can be used to generate blacklists of malicious URLs that can be blocked proactively 
  - [**PhishTank**](https://www.phishtank.com/)
    - allows users to submit phishing artifacts which are then verified by the wider community

### File Reputation Tools

- **VirusTotal**
  - platform where you can upload files, search for IP addresses, domains, URLs, and other artifacts to retrieve a community-generated reputation value
- **Talos File Reputation (TFR)**
  - offered by Cisco
  - allows you to search for SHA256 strings against their reputation database
  - also provided with the file size, the type of file, the name used for detection, and other aliases used to track this specific piece of malware

### Malware Sandboxing

- the process of detonating (running/executing) a piece of malware in a contained environment, and closely monitoring exactly what the software does, allowing security teams to collect indicators of compromise
  - e.g., monitoring the network traffic to see if the malware tries to communicate with a command-and-control (C2) server or download additional modules
- by understanding how the malware operates, it becomes easier to create defenses that can detect similar activity
- security teams usually have their own environment but you can use [**Hybrid Analysis**](https://www.hybrid-analysis.com/)
  - online malware analysis platform that lets you upload malware for instant cloud-based analysis
  - provides a detailed report about the observed activity
  - ![](images/Screenshot%20from%202024-12-23%2019-33-03.png)

## Automated Analysis

### PhishTool

- will automatically retrieve the file name and MD5 hash from any email attachments
  - console has a button that allows us to search for the hash value in VirusTotal straight from the console
- if an email is submitted that includes any URLs, a web capture can be viewed by clicking on the URL and selecting Web Capture
  - also provides the HTTP requests made, and headers from the site
- WHOIS lookup can be done too
  - where it’s hosted
  - who owns the domain
  - how long it has been alive for
  - contact information
