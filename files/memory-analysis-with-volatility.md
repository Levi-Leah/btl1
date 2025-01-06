# Memory Analysis With Volatility

* open-source memory forensics framework for incident response and malware analysis
* written in Python and supports Microsoft Windows, Mac OS X, and Linux
* you can
  * List all processes that were running
  * List active and closed network connections
  * View internet history (IE)
  * Identify files on the system and retrieve them from the memory dump
  * Read the contents of notepad documents.
  * Retrieve commands entered into the Windows Command Prompt (CMD)
  * Scan for the presence of malware using YARA rules
  * Retrieve screenshots and clipboard contents
  * Retrieve hashed passwords
  * Retrieve SSL keys and certificates

---

## Volatility 2

* Volatility needs profiles to work
  ![](images/Screenshot%20from%202025-01-06%2016-09-01.png)
* Run Volatility to identify the system the memory image was taken from, including the operating system, version, and architecture
  * `volatility -f memdump.mem imageinfo`
* When running other commands on the memory image you need to provide the profile
  * e.g., `--profile=WinXPSP2x86`

---

### Common CLI options (Volatility 2)

| Command Purpose                        | Volatility 2 Command                                      |
|----------------------------------------|----------------------------------------------------------|
| Determines the profile                 | `volatility -f memdump.mem imageinfo`                   |
| Prints a list of processes             | `volatility -f memdump.mem --profile=PROFILE pslist`     |
| Prints a process tree                  | `volatility -f memdump.mem --profile=PROFILE pstree`     |
| Prints all available processes         | `volatility -f memdump.mem --profile=PROFILE psscan`     |
| Combines `pslist` and `psscan`         | `volatility -f memdump.mem --profile=PROFILE psxview`    |
| Identifies network connections         | `volatility -f memdump.mem --profile=PROFILE netscan`    |
| Creates a timeline of events           | `volatility -f memdump.mem --profile=PROFILE timeliner`  |
| Extracts internet browsing history     | `volatility -f memdump.mem --profile=PROFILE iehistory`  |
| Identifies files on the system         | `volatility -f memdump.mem --profile=PROFILE filescan`   |
| Retrieves files to a specified dir     | `volatility -f memdump.mem --profile=PROFILE dumpfiles -n --dump-dir=<DIR>` |
| Retrieves command-line arguments       | `volatility -f memdump.mem --profile=PROFILE cmdline -p <PID>` |
| Saves a process as a file              | `volatility -f memdump.mem --profile=PROFILE procdump -p <PID> --dump-dir=./` |


---

## Volatility 3

* profiles are no longer required
* plugins have been changed to be OS-specific
  * `pstree` > `windows.pstree`, `linux.pstree`, `mac.pstree`
* [volatility cheat sheet](https://blog.onfvp.com/post/volatility-cheatsheet/)

    | Command Purpose                 | Volatility 2 Command                                   | Volatility 3 Command                                 |
    |----------------------------------|------------------------------------------------------|-----------------------------------------------------|
    | Get process tree                | `volatility --profile=PROFILE pstree -f file.dmp`    | `python3 vol.py -f file.dmp windows.pstree`         |
    | List services                   | `volatility --profile=PROFILE svcscan -f file.dmp`   | `python3 vol.py -f file.dmp windows.svcscan`        |
    | List available registry hives   | `volatility --profile=Win7SP1x86_23418 -f file.dmp hivelist` | `python3 vol.py -f file.dmp windows.registry.hivelist` |
    | Print cmd commands              | `volatility --profile=PROFILE cmdline -f file.dmp`   | `python3 vol.py -f file.dmp windows.cmdline`        |

---

### Volatility Workbench

* GUI
* available on Win and Mac
![](images/Screenshot%20from%202025-01-06%2020-04-36.png)