# Windows Investigations

## Windows Artifacts - Programs

* seeing what files have been run on the system can provide valuable evidence
  * how many times a file has been run
  * when it was last run
  * when it was created
  * full file paths, etc.

---

* **LNK Files / Shortcut Analysis**
  * used by the Windows OS to link one file to another
  * can collect valuable metadata from LNK files such as the location of the folder it is linked to, the date the LNK file was created, modified, last accessed, the file size, and more
  * LNK files can be found at `C:\Users\$USER$\AppData\Roaming\Microsoft\Windows\Recent`
  * Windows File Analyzer is used to view these files in a human-readable format
    * File > Analyze Shortcuts

---

* **Prefetch Files**
  * provides info on programs
    * name of the application, the path to the executable file, when the program was last run, and when the program was created/installed
  * prefetch files can be found at `C:\Windows\Prefetch`
  * `Prefetch Explorer Command Line` also known as `PECmd.exe` is used to view these files in a human-readable format
    * `PECmd.exe -f <PREFETCH_FILE.pf>`
    ![](images/Screenshot%20from%202025-01-04%2020-51-07.png)
      * If you're using `-d` option use absolute path to dir cause windows hates you
      * use `-k` before `-d` cause fuck you

---

* **Jump List**
  * `automaticDestination-ms` and `customDestination-ms`
    * contain information about applications that are pinned to the taskbar
      * file path, timestamps, and application identifiers (AppIDs)
  * Jump List files can be found at: `C:\Users\% USERNAME%\AppData\ Roaming\Microsoft\Windows\Recent\AutomaticDestinations` and `C:\Users\%USERNAME%\AppData\ Roaming\Microsoft\Windows\Recent\CustomDestinations`
  * `JumpList Explorer` is used to view these files in a human-readable format
    * File > Load jump list > FILE_PATH

---

## Windows Artifacts - Browsers

* you can find websites that have been visited when they were last visited, what the user did on the websites, files that have been downloaded, search form strings, autofill usernames and password, and lots more
* **KAPE**
  * select browsers as targets
* **Browser History Capturer (BHC)** and **Browser History Viewer (BHV)**
  * you can run BHV on it's own but if you’re running it on the system you’re investigating, it will fail at trying to retrieve Microsoft Edge files, even if it is run with elevated admin privileges; that's where BVC comes in
    * you can forcefully retrieve all important files for browser forensics, and then import it into BHV
  * you can see browsing history, when sites were accessed, visit counts, cached webpages, and cached images
* BHC
  1. Select user profile
  2. Choose destination location
* BHV
  1. File > Load History > Load history captured using the Browser History Capturer tool > Browse and select the BHC dir you've created w/ BHC

## Windows Artifacts - Logon Events

* identifying what user accounts have logged into a system, and at what time
* Windows Event Logs are stored at `C:\Windows\System32\winevt\Logs`, specifically in `\Security` folder
* Windows Event Viewer can be used to view these logs
  * or SIEM/Microsoft Excel,

---
* **Event ID 4624 (Successful Logon)**
  * **2 – Interactive**
    * interactively logged on, meaning a physical logon to the device
  * **3 – Network**
    * accessed system via network
  * **4 – Batch**
    * started as an automated batch job
  * **5 – Service**
    * a Windows service started by service controller
  * **6 – Proxy**
    * proxy logon; not used in Windows NT or Windows 2000
  * **7 – Unlock**
    * unlock workstation - think Interactive logon, but unlocking to resume a previous session
  * **8 – NetworkCleartext**
    * network logon with cleartext credentials
  * **9 – NewCredentials**
    * used by RunAs when the `/netonly` option is used

---

* **ID 4672 (Special Logon)**
  ![](images/Screenshot%20from%202025-01-05%2002-40-53.png)
  * when a user with administrative privileges logs into the system
  * **Account name**
    * Displays the account logging in. For Microsoft accounts, it shows the email address
  * **Security ID**
    * computer name, followed by the username
  * **Logon ID**
    * unique, randomly generated value for the session
    * to find the associated logoff for a session, look for the same Logon ID (e.g., `0x25A036D`) in a Logoff log
  * **Logged**
    * timestamp

---

* **ID 4625 (Failed Logon)**
  * contain error codes, which help us to understand exactly why the logon attempt failed
    | **NETLOGON LOG ERROR CODE** | **DESCRIPTION**                                              |
    |-----------------------------|--------------------------------------------------------------|
    | 0xC0000064                 | The specified user does not exist                            |
    | 0xC000006A                 | The value provided as the current password is not correct    |
    | 0xC000006C                 | Password policy not met                                      |
    | 0xC000006D                 | The attempted logon is invalid due to a bad user name        |
    | 0xC000006E                 | User account restriction has prevented successful login      |
    | 0xC000006F                 | The user account has time restrictions and may not log on at this time |
    | 0xC0000070                 | The user is restricted and may not log on from the source workstation |
    | 0xC0000071                 | The user account’s password has expired                     |
    | 0xC0000072                 | The user account is currently disabled                      |
    | 0xC000009A                 | Insufficient system resources                               |
    | 0xC0000193                 | The user’s account has expired                              |
    | 0xC0000224                 | User must change his password before he logs on the first time |
    | 0xC0000234                 | The user account has been automatically locked             |

---

* **ID 4634 (Logoff)**
  * logoff from the current session

## 