
# Types of Phishing Emails

## Recon

- observed daily by large organizations
- typically always make it through the email gateway as they do not contain any malicious indicators
- typical will only contain body content, more advanced emails could utilize social engineering techniques and tracking pixels to collect more information on their targets
- email addresses that are discovered to be active can be sold to other malicious actors to conduct phishing attacks or can be targeted by the original actor to send further malicious emails

- checks if the destination mailbox is in use
  - used to get a response from the recipient
    - email back, email delivered, email opened
  - **3 main types**
    - **spam**
      - contains random letters
    - **email w/ social engineering component**
      - trying to get you to respond
      - posing as a friend/acquaintance, creating sense of urgency, impersonating an authority figure (BEC)
    - **tracking pixels**
      - track pixels to see if the email was viewed in an email client
      - **tracking pixel** is an HTML code snippet that is loaded when a user visits a website or opens an email
      - very useful for tracking user behavior and preference or for *data harvesting*
      - **Tracking Pixel Recon Emails**
        - follow the format of either a spam recon email, or a social engineering email
        - **How it works**
          - HTML code in the email body
          - contains an external link to a pixel server
          - the email recipient opens the email, the client or webmail provider will load the HTML code, sending a message back to the server
        - help attackers understand how active the mailbox is
        - **Data that can be acquired**
          - the time from email being sent to being opened
          - OS
          - type of website/email used (mobile/desktop)
          - type of client (browser/webmail or mail program/client)
          - screen resolution
          - date and time when email was read
          - IP address

---

## Credential harvester

- the most common phishing emails out there
- target human weaknesses to attempt to retrieve valid credentials which can potentially be used to gain access to numerous services and accounts as a result of credential stuffing attacks
- **How it works**
  - email is styled to look like it is from a legitimate company, impersonating some of the most popular online services and retailers such as Outlook, Amazon, and DHL
    - Credentials harvesters are sometimes tailored to impersonate login portals for the organization that is being targeted
      - Logos and other branding material can often easily be retrieved from a company's website, or search engine results
    - email will tell the recipient to click a button or URL, where they will typically be presented with a real-looking login portal
    - any credentials entered are either stored on the site in an inaccessible directory, or emailed to a dummy account, typically utilizing free online mail services such as Gmail, Hotmail, and Outlook, where the attacker can log in and collect them
- The main giveaway is typically the URL
  - e.g., the URL in the email is using an IP address instead of a domain name
- **Key Points**
  - Imitates commonly-used websites and services (e.g., Outlook, Amazon, HMRC, DHL, FedEx).  
  - Entices the recipient to enter credentials into a fake login portal.  
  - Uses social engineering tactics, such as:  
    - Creating a sense of **urgency**.  
    - Using **false authority**.  
  - URLs may be:  
    - Completely random.  
    - Designed to mimic the legitimate domain of the targeted organization.  
  - Often contains small spelling or styling mistakes, which are extremely rare in legitimate emails from well-known brands.  

---

## Social Engineering

- using psychological methods in order to get people to complete actions that they wouldn't normally
  - disclosing confidential information
  - allowing someone into a restricted area without proper authorization
  - transferring money to an unverified account
- all phishing emails will utilize some social engineering techniques
  - attacks aren't trying to exploit or hack technical systems, they're going after the human behind the screen
- **Common Social Engineering Tactics in Phishing Emails**
  - **Recon Emails**: Convince the recipient to reply to the attacker's initial email to confirm the mailbox is active.  
  - **Impersonation of Executives**: Convince the recipient to transfer money by posing as the CEO, CTO, CFO, or other executive board members.  
  - **Confidential Information Requests**: Convince the recipient to disclose confidential or private information by impersonating:  
    - The data subject (e.g., an employee or client).  
    - Someone in a higher position within the company.  

---

## Smishing

- phishing through text messages
- generic victim profile or target group; msg can be sent out in bulk
- mostly targets PII or PCI
- best way to defend is awareness training and not clicking links

## Vishing

- phishing through phone call
- relies heavily on the social engineering
- victim are often people in the organization that would have access to sensitive information
  - one or two levels below the “C” level executive
- mostly target financial information or corporate accounts that could give access to the network
- best way to defend is security awareness training or blocking auto callers
  - or having internal authorization codes/separation of duties

---

## Whaling

- highly-targeted phishing attack that looks to targets C-level executive
- emails are refined using OSINT to make it believable
- most difficult types of phishing to detect because they are sent in very small volumes and are tailored to appear legitimate and not generate red flags that could alert the security
- prevention could be marking external emails by appending the subject line or email body text

---

## Malicious file

- emails w/ malicious file are the most common amongst credential harvesters
- common methods to deliver malicious files are:
  - malicious attachment
    - most email providers prevent you from sending attachments w/ certain file types and can conduct malware scans before you even send it
    - word or excel files are common cause not as sus
    - Microsoft office macros
      - macros are a series of commands and instructions that can run automatically if enabled
      - was common a few years ago but now macros are disabled by default
      - as a workaround, malware authors show a fake warning to get you to enable it
      ![](images/Screenshot%20from%202024-12-19%2022-06-37.png)
      - when you run a macro like this it can connect to domains and download malware
    - general rules from Microsoft:
      - disable macros by default (preferably on admin level)
      - don't open sus emails
      - delete sus emails
      - use [Attack surface reduction (ASR)](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction) rules at enterprise level to prevent prevent macro malware from running executable content
  - hosted malwre
    - host malware on a website and trick users into clicking a hyperlink, download a file, then run it
      - malicious domains are easy and cheap to create
      ![](images/Screenshot%20from%202024-12-19%2022-16-55.png)
      - compromised domains are also common; the original site is often left intact so that users or owners don't realize smth is wrong
      ![](images/Screenshot%20from%202024-12-19%2022-18-30.png)

---

## Spam

- messages that are unsolicited, unwanted, or unexpected but are not necessarily malicious in nature; you should still be cautious and not click anything
  - newsletters, marketing emails, company announcements
- Malicious spam emails are malicious messages that are sent on a mass scale (as opposed to being targeted at an individual or organization)
- Spam emails can also be utilized as a form of reconnaissance
  - if users click on an unsubscribe link
  - link takes them to a website, which leads to system fingerprinting
  - confirms that the mailbox is in use

---

## False positive

- not malicious but reported as such
- can be due to
  - bad formatting
  - users believe it's malicious and report it
  - unexpected and asks to complete an action (click button, contact someone, transfer funds, etc.)
