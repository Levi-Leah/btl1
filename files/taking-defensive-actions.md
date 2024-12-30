# Taking Defensive Actions

## Preventative

- **Marking external emails**
  - you can alter the subject line or body text of an email address that is coming into the organization to alert the recipient that this email isn’t an internal communication on platforms like Microsoft Exchange or Office365
    - e.g., the subject line appended with a very short message, such as “[EXTERNAL]” or “[EXT]”

---

- **Anti-Spoofing Records**
  - DNS records can be used to set up anti-spoofing records
  - **Sender Policy Framework (SPF)**
    - type of DNS (TXT) record that can help prevent an email address from being forged
    - established to identify the hostnames or IP addresses that are allowed to send emails for your custom domain
    - having an SPF record specified on your domain helps prevent a malicious actor from spoofing it
    - contains three parts
      - the declaration of the record type
      - the IP addresses and external domains that can send on your domain’s behalf
      - an enforcement rule
    - Syntax:
      - `v=spf1 <IP> <enforcement rule>`
      - `v=spf1 a: include:mailgun.org protection.outlook.com -all`
  - **Domain Keys Identified Mail (DKIM)**
    - method of email authentication that cryptographically verifies if an email has been sent by its trusted servers and hasn’t been tampered with during transmission
    - How it works:
      - when the mail server sends an email, an encrypted hash of the email contents is generated using a private key and added to the email header as a DKIM signature
      - the receiving server will look up the corresponding public key in the domain's DNS records
      - the receiving mail server decrypts the email with the public key, calculates a new hash and verifies whether the original and the newly generated hash match
    - Syntax:
      - `V=DKIM1 <key type> <public key>`
  - **Domain-based Message Authentication, Reporting & Conformance (DMARC)**
    - email authentication, policy, and reporting protocol
    - built on SPF and DKIM concepts
    - allows the domain owner to specify what should happen if emails fail both SPF and DKIM checks
    - three basic options the mail server can take:
      - none
      - quarantine
      - reject
    - `v=DMARC1 <action> <report address>`
      - `v=DMARC1; p=quarantine; rua=mailto:contact@securityblue.team`

---

- **Spam filter**
  - 3 main types:
    - **Gateway Spam Filters**
      - sit behind an on-premises firewall of a network
    - **Hosted Spam Filters**
      - hosted within the cloud
      - able to update more quickly than some of the on-premises filters
    - **Desktop Spam Filters**
      - user-installed 
      - can sometimes be categorized as “Freeware
        - you don't fully know what the application is installing on your system
  - 3 types based on how they detect smap:
    - **Content Filters**
      - uses information in the email header and body to determine if the email is legitimate
      - filter can cross-reference the header with published blacklists or known spamming networks
      - filter scans the body of the message e.g. based on account preferences (e.g. block adult content)
    - **Rule-Based Filters**
      - allows for emails to be filtered based on predetermined criteria
      - e.g., if the subject or body contains “FREE OFFER” and the Sender is located Outside of the Organization, raise the likelihood of the message being spam
    - **Bayesian Filters**
    - most intelligent types of spam filters; utilizes machine learning
    - e.g. when the user marks an email as spam, it can analyze the characteristics of that message and block similar messages
    - the downside is you need a lot of spam to utilize the machine learning capabilities

---

- **Attachment Filtering**
  - before blocking a file type, consider
    - what file types are often used for malicious purposes
      - `.exe` (Executable)
      - `.vbs` (Visual Basic Script)
      - `.js` (JavaScript)
      - `.iso` (Optical Disk Image)
      - `.bat` (Windows Batch File)
      - `.ps`/`.ps1` (PowerShell Scripts)
      - `.htm`/`.html` (Web Pages / Hypertext MarkupLanguage)
      - `.zip`
      - `.doc`/`.docx`/`.docm`
      - `.pdf`
      - `.xls`/`.xlsx`/`.xlsm`
    - which file types the organization deals with on a regular basis, and if blocking them would have any negative impact on the business

---

- **Attachment sandboxing**
  - pre-defined rules and configurations are used to block specific file types or naming conventions
  - files that look legitimate (e.g., Microsoft Office docs) can still go through
  - w/ sandboxing, emails that include file attachments are extracted and analyzed, and files are detonated in a virtual environment
  - if malicious indicators are observed, the attachment is classed as malicious, and the email will not be delivered
  - advanced sandboxing products provide:
    - machine learning
      - retrieving information and behavioral analytics from millions of malicious emails and malware samples so that over time it can determine which emails to let through
    - virtual environments
    - reports

---

- **Security awareness training**
  - users should be put through a training course that teaches them how to spot phishing emails, and the actions they should take, preferably during the onboarding process
  - indicators include:
    - Coming from an unknown sending address
    - Improper grammar and spelling mistakes
    - Poor styling
    - Trying to get the recipient to click on a button or complete an action
    - Suspicious URLs and attachments
  - **Simulated Phishing Attacks** can be use to determine the effectiveness of the training
    - should be conducted every few months to test employees and identify any that are consistently falling for phishing emails so that they can receive additional training

## Reactive

- **Immediate Response Process**
  - steps the investigating analyst should take once they have identified a phishing email (from detection through to writing the report)
    - Retrieve an original copy of the phishing email
    - Gather artifacts from the phishing email
    - Inform the recipients that received the email
      - The date and time the email was sent
      - The subject line of the malicious email
      - Clear instructions on what to do with the email
      - Contact details for if the recipient is unsure what to do
    - Investigate malicious artifacts to collect indicators of compromise that can be blocked to protect the organization
    - Take defensive measures
    - Complete the investigation report, documenting all of the above steps

---

- **Blocking Email Artifacts**
  - email sender
    - can be bi-directional, and prevent emails from inside being sent to the malicious sender
  - sender domain
    - step-up from blocking the sender
    - only done when the sending domain is purely malicious or is using a large number of mailboxes to send malicious emails
  - sender server IP
    - not conducted unless it is absolutely necessary
    - will drop any emails coming from the specified IP
    - a domain may use multiple sending servers, so this would be less effective than domain blocking
    - used for rogue IPs that have been compromised or set up to send malicious emails
  - subject line
    - phishing attacks will typically use one subject line
    - instead of blocking multiple senders, you can block anything w/ the subject line

---

- **Blocking Web Artifacts**
  - malicious sites can be neutralized so that even if an employee does click on a link, their request will not be allowed out of the organization’s network
  - you can use:
    - rules within the web proxy
      - a device that sits on the perimeter and allows or disallows connections
    - perimeter firewall blocks
      - prevents employees from connecting to a malicious IP
      - usually rare; a proxy block will be enough to prevent any connections
  - **Blocks on a web proxy**
    - **URL block**
      - extremely specific, and will only block the URL that has been provided
      - can be ineffective if URLs are dynamically generated for specific recipients
        - e.g., URLs that auto-fill the email address per phishing email
          - URL will end in `=john.smith@domain.com` r similar
      - URLs can be blocked at a specific point, in order to be more effective
        - we could block the first directory that looks suspicious
          - e.g., in `hxxp://elephantsanctuary[.]com/index/2019/hgasdf/11/outlook/owa.php?` we can block anything that comes after the `domain[.]com/index2019/hgasdf` directory
      - when deciding on a URL block, work out if the full URL is static and would work for all recipients, or if there is an obviously malicious directory where the URL block can end.
    - **domain block**
      - blocks an entire domain, preventing web requests from going out, including any subdomains or any URLs
        - e.g., `elephantsanctuary[.]com`
  - **DNS Blackholing**
    - the process of creating a fake DNS entry so that if an employee tries to access `hxxp://thisisreallymalicious.com` they will actually be sent to another site, telling them they just clicked a malicious URL
  - **Firewall**
    - when there are multiple malicious sites being hosted on the same IP, we can block that server to prevent access to any of the sites on it
    - extreme measure; typically not used regarding phishing
    - often used to block IPs that are scanning or attacking the organization
    - IP addresses are the second easiest indicator for malicious actors to change, so it is likely that IP blocks will be countered by simply using a new IP

  - **Making decisions**
    - **situation**: domain has been created for purely malicious intent
      - **indicators**:
        - young age
        - no legitimate content
        - malicious content present
      - **action**: web proxy or domain block
    - **situation**: domain has been compromised
      - **consideration**: decide if employees need to visit it for business purposes
        - **no**:
          - **action**: web proxy or domain block
        - **yes**:
          - **action** URL block

---

- **Blocking File Artifacts**
  - **Blocking Hashes**
    - blocks the MD5, SHA1, or SHA256 hash within the organization’s EDR tool
      - due to hash collisions, MD5 and SHA1 have been widely deprecated
      - SHA256 is the current standard for file hashing
    - if the organization’s anti-virus (AV) solution isn’t flagging the malicious file, the hash can be submitted to the vendor
    - commodity malware (frequently sold online) and more advanced polymorphic malware can edit itself, or write trash data to its code, altering the file hash
  - **Blocking Names**
    - typically not a good idea unless the file has an extremely unique file name
    - filenames are rarely used to block
    - can instead be used to generate watchlists