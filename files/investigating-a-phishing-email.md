
# Investigating a Phishing Email

## What to collect

- **Email artifacts**
  - **sending email address**
    - useful to find other emails that came from or were sent to this address
  - **subject line**
    - useful to find other emails or block em
  - **recipient email address**
    - inform recipients not to interact w/ the email
  - sending server IP and reverse DNS
    - helps identify if the sender address was spoofed
    - reverse DNS lookup will give us a hostname that'll provide more info on the server
  - **reply-to address**
    - sometimes is different from the sending address
  - **date & time**
    - can help find other emails that are part of the same attack
    - can help identify the times org receives the most malicious emails
- **File artifacts**
  - **attachment name and extension**
    - depending on the uniqueness of the name, it can possibly be blocked using an organization’s EDR
    - **size**
  - **sha256 hash value**
    - unique string generated from a file
    - can be used for reputation checks w/ `VirusTotal` and `Talos File Reputation`
    - MD5 and SHA1 hashes should no longer be used, as they have known hash collisions
    - SHA256 is the current security standard for file hashing
- **Web artifacts**
  - **full URLs**
  - **root domain**
    - often isn’t necessary if you have the full URL
    - sometimes the root domain can be an important as it can show if
      - the site has been created for malicious activity
      - is a legitimate site that has been compromised

## Manual Collection

- analysts should never analyze phishing emails on a corporate or personal system
- always use a virtual machine or a “dirty” system
  - e.g., an old laptop designed specifically for risky security tasks, such as malware analysis or investigating suspicious websites
- **Email artifacts**
  - you can get most artifacts from the email client
    - Sending Address
    - Subject Line
    - Recipients (Unless they’re in BCC)
    - Date + Time
  - other info can be obtained from `.eml` or `.msg` file
    - Sending Server IP
      - `X-Sender-IP`
      - perform reverse DNS lookup (`whois`)
        - `nslookup` 
    - Reply-to Address
      - `Reply to`
- **Web artifacts**
  - from email client
    - copy the full URL
  - from `.eml` or `.msg` file
    - search for `<a>`/`href` tags
  - it's better to not use the email client for this as u can accidentally click the URL
- **File artifacts**
  - MD5 and SHA1 hashes are enough to perform reputation searches online and take defensive measures
  - `Talos File Reputation` require SHA256 hashes to perform checks tho
  - via PowerShell
    - `get-filehash`
      - generates SHA256 hash by default
      - to retrieve MDA use `get-filehash -algorithm md5`
      - to retrieve SHA1 use `get-filehash -algorithm sha1`
    - via Bash
      - `sha256sum`
      - `sha1sum`
      - `md5sum`
    - get the **name**, **extension**, and **size** too

## Automated collection

- [PhishTool](https://www.phishtool.com/) can do artifact retrieval and analysis; can also generate reports