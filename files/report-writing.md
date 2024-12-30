# Report Writing

- general flow of the Report
  - Email header details, artifacts collected, and a description of the body content
  - Users affected and actions taken to notify them
  - Analysis process, tools used, and results
  - Defensive measures taken
  - Lessons learned

---

## Header, artifacts, content

- used to
  - link attacks together into campaigns
  - identify malicious actors behind the attacks
  - generate metrics
  - perform trend analysis
- must be included in a clear and concise way, so they can be found quickly, and other analysts can copy and paste them into different tools or services if needed

---

- **email header**
  - sending address
  - reply-to address
  - date and time
  - sending server IP
  - reverse DNS of the sending server IP
  - recipient
  - subject line
  - URLs (**sanitized**)
    - state if none
  - attachment
    - state if none
    - name + file extension
    - file hash
    - size

---

- **email body**
  - email file (`.eml`/`.msg`)
  - brief description
    - 1-2 sentences describing what the email looks like, and what it’s trying to get the recipient to do
  - screenshot

---

- **Examples**

    ```[txt]
    Artifacts Retrieved
    Sender: bobtom112233@gmail.com
    Reply-to: None
    Date: Monday 16th September 2019 17:33
    Sending Server IP: 209.85.167.42
    Reverse DNS: mail-lf1-f42.google.com
    Recipients: contact@dicksonunited.co.uk
    Subject: Hello
    URL: None
    Attachments: None

    Description: This email contains no malicious URLs or attachments and is attempting to get the recipient to respond, either to engage in a social engineering attack or to see if the recipient mailbox is in use so it can be targeted in future attacks. Email classed as Recon.
    ```

    ```[txt]
    Artifacts Retrieved
    Sender: amazonsupp0rt@outlook.com
    Reply-to: no-reply@amazon.co.uk
    Date: Monday 16th September 2019 19:25
    Sending Server IP: 209.85.167.91
    Reverse DNS: mail-lf1-f91.google.com
    Recipients: claire.shelley@dicksonunited.co.uk
    Subject: Suspicious Amazon Order Alert
    URL: hxxp://maliciousdomainexample[.]com/
    Attachments: None

    Description: This email from an Outlook mailbox is posing as Amazon using effective styling and asks the user to click a link to reset their password claiming that the user’s account has been hacked and used to purchase an order of £329.99. Using a sense of urgency is a common social engineer tactic, used to make the user rush and not think about what’s actually happening. The email contains a malicious URL, as it is not pointing to an Amazon-owned domain. Email classed as malicious / credential harvester.
    ```

## Analysis Process, Tools, and Results

- largest part of the report
- covers the analysis completed to assess the risk of any malicious artifacts (e.g., attachments or URLs)
- include the tools used and the results that they have provided
  - visualization tools
  - reputation check results
  - manually detonating malware in a virtual sandbox
  - you need to answer questions such as “is this URL malicious?” or “how damaging is this attachment?” whilst providing in-depth notes on the analysis methods and tools you used to investigate these artifacts
  - this will later provide justification for any defensive measures that you wish to take
  - there needs to be enough detail to allow senior analysts to come to the same conclusion that you have

- **Malicious URL example**
    ```[txt]
    URLs: https://maliciousdomainexample[.]com/index/2019/amazon/login.aspx

    WHOIS Analysis – Performing a WHOIS search shows that the domain was registered 3 days ago, with NameCheap as the domain registrar. There is no information about the site owner/domain registrant.

    VirusTotal Reputation – Searching for the full URL and the root domain on VT shows that it is currently not being flagged as malicious, likely the result of the domain being new, so security engines haven’t crawled it yet.

    URL2PNG Analysis – Using URL2PNG to view the link destination showed that the site was hosting a fake Amazon login portal, used to steal any credentials that are entered. Looking at the root domain “https://maliciousdomainexample[.]com” shows that the site doesn’t have a genuine homepage, a common sight when domains are used for purely malicious operations.
    ```

- **Malicious attachment example**

    ```[txt]
    Attachment Name: wallpaperHD.exe
    Attachment MD5 Hash: 0c4374d72e166f15acdfe44e9398d026
    Attachment SHA256 Hash: 240387329dee4f03f98a89a2feff9bf30dcba61fcf614cdac24129da54442762

    VirusTotal Upload – Uploading the file to VirusTotal shows that the file is extremely malicious and is detected by 61/71 engines. Link to VirusTotal page for this MD5 hash – https://www.virustotal.com/gui/file/240387329dee4f03f98a89a2feff9bf30dcba61fcf614cdac24129da54442762/detection

    [attach the screenshot]

    Talos File Reputation – Uploading the SHA256 hash to TFR confirmed what VirusTotal stated about the file being extremely malicious.
    ```

---

## Defensive Measures Taken

- defensive actions that you have taken or are requesting to be taken in order to protect the organization
  - clearly state what measures have been taken to provide an audit trail should anything go wrong
- three main types of actions:
  - Email artifact blocking (subject line, sending address, sending server IP)
  - Web artifact blocking (URL, domain, IP)
  - File artifact blocking (file name, file hash)

- **Example where the analyst has the ability to take defensive measures**

  ```[txt]
  Sender: contact@dhl.com
  Sending Server IP: 209.85.167.42
  Reverse DNS: mail-lf1-f42.google.com
  Subject: “Failed Delivery DHL RESPOND NOW – URGENT!!”
  URL: hxxps://dhl-faileddelivery.shanepppalkkbc.com (Example Value)

  [1] The sending address was successfully spoofing contact@dhl.com, however, the sending IP revealed it was actually a Gmail address, and therefore not from DHL. [2] We are unable to block the sending server IP, as it belongs to Gmail, and would have a negative impact on the business as legitimate emails would be blocked. [3] Blocking the sender “contact@dhl.com” is also not appropriate, as legitimate emails coming from that address will be blocked. [4] I have blocked the subject line on the email gateway, as it is highly unlikely legitimate DHL emails would use it. [5] There would be no negative impact to the business, and this action would prevent any more emails in this attack being delivered to employee mailboxes.

  * [6] Subject Line Block (Email Gateway) “Failed Delivery DHL RESPOND NOW – URGENT!!” on 22nd December at 12:03 PM by Jane Smith.
  
  [7] The URL used within the credential harvester is a malicious domain “shanepppalkkbc[.]com” that utilizes a subdomain “dhl-faileddelivery” to look more effective when glancing at the link. [8] After investigating the domain, it was created purely for malicious purposes, and there is no business justification for employees to visit it, and we can block the entire domain to prevent users from visiting the existing malicious link, or any others that are hosted on the site.

  * [9] Domain Block (Web Proxy) “shanepppalkkbc[.]com” on 22nd December at 12:07 PM by Jane Smith
  ```

- **Recap**:
  1. Summarizes that the email sender has been spoofed, and the message actually came from Gmail.
  2. Understands and states blocking a Google sending IP would most likely have negative consequences.
  3. Explains the spoofed sending address value can’t be blocked, as it is used legitimately by DHL.
  4. States the action they are taking and provides justification for this decision.
  5. Understands and states there would be no negative impact to the business by blocking the unusual subject line.
  6. Lists the type of block taken, the value that was blocked, the time and date of the action, and who took the action (provides accountability).
  7. Summarizes that the URL is malicious and not owned by DHL. Quickly covers tactics used.
  8. States the action they are taking and provides justification for this decision.
  9. List the type of block taken, the value that was blocked, the time and date of the action, and who took the action (provides accountability).

---

- **Example where the analyst must contact a senior analysts**

  ```[txt]
  [1] The sending address comes from the sending domain @govpayments.net, which is not a legitimate website used by the UK government and HMRC. [2] Although we are able to block the sending domain as it is attempting to pose as a legitimate domain owned by the government, we have only received emails from one sending mailbox, and blocking the domain at this point may be excessive. [3] Blocking the sender “HMRC-0fficial@govpayments.net” would stop more malicious emails being delivered by this sender. [4] There would be no negative impact to the business by blocking this malicious sending address.

  * [5] Sending Address Block (Email Gateway) “HMRC-0fficial@govpayments.net” on 1st March at 3:37 PM by Chris C.
  
  [6] The URL used within the email is used to download the same Emotet payload as the attachment. [7] After investigating the domain, it was created purely for malicious purposes, and there is no business justification for employees to visit it, and we can block the entire domain to prevent users from visiting the existing malicious link, or any others that are hosted on the site.

  * [8] Domain Block (Web Proxy) “hmrc.announcementsgov.com” on 1st March at 3:41 PM by Chris C
  ```

- **Recap**:
  1. Summarises that the email sending domain is not a legitimate domain used by the government, and is attempting to make itself look somewhat legitimate.
  1. Explains that blocking the sending domain, although malicious, is excessive as currently only one sending mailbox has been observed sending malicious emails.
  1. Explains that blocking the sending address would prevent more emails from being delivered.
  1. Understands and states there would be no negative impact to the business by blocking the sending address.
  1. Lists the type of block taken, the value that was blocked, the time and date of the action, and who took the action (provides accountability).
  1. Summarises that the URL is malicious and used to download the same file that is included as an email attachment, and that it is Emotet malware.
  1. States the domain is malicious and operating with purely malicious intent, and there is no legitimate reason for employees to visit the domain.
  1. List the type of block taken, the value that was blocked, the time and date of the action, and who took the action (provides accountability).

---

## Artifact sanitization

- you MUST sanitize/defang any URLs or IP Addresses
- `.` => `[.]`
  - `8.8.8.8 ` to `8[.]8[.]8[.]8`
- `tt` => `xx`, `://` => `[://]`
  - `https://hello.example.com` to `hxxp[://]hello[.]example[.]com`
- can be automated w/ CyberChef’s Defang IP Addresses and Defang URL
  ![](images/Screenshot%20from%202024-12-24%2018-48-45.png)