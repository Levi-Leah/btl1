# CMD and PowerShell For Incident Response

* **CMD**
  * run all as admin
  * `ipconfig /all`
    * get network configuration information from the local system, including the assigned IP address and the device’s MAC address
  * `tasklist`
    * check running processes and programs
    * Image (process) name, PID, session, memory usage
  * `wmic process get description, executablepath`
    * display running processes and the associated binary file that was executed to create the process
    * use this command to identify unusual process names and identify where the executable file is so we can analyze it
    * Processes that are running out of unusual locations such as `/tmp/` and `/Downloads/` are definitely worth investigating further
  * `net user`
    * will print a list of all system users, regardless of usergroup
  * `net localgroup administrators`
    * will list all users that are in the administrators user group
    * replace “administrators” with any local group that we want to enumerate
    * `net localgroup`
    * list of all groups
  * `sc query | more`
    * list all services and detailed information about each one
  * `netstat -ab`
    * list open ports on a system

---

* **PowerShell**
  * `Get-NetIPConfiguration` and `Get-NetIPAddress`
    * Similar to ifconfig in CMD,
    * get network-related information from the system
  * `Get-LocalUser`
    * list all local users on the system
    * `Get-LocalUser -Name BTLO | select *`
      * provide a specific user to the command to only get information about them
    * `Get-Service | Where Status -eq "Running" | Out-GridView`
      * identify running services on the system
      * `Out-GridView` is telling PowerShell to show the results in GUI window
    * `Get-Process | Format-Table -View priority`
      * group running processes by their priority value
    * `Get-Process -Id 'idhere' | Select *` or `Get-Process -Name 'cmd' | Select *`
      * dump info on a service by including the ID/name
    * `Get-ScheduledTask`
      * Scheduled Tasks are often abused and utilized a common persistence technique
      * list tasks that are set to run after certain conditions are met
      *  `Get-ScheduledTask -TaskName 'PutANameHere' | Select *`

---

```[cmd]
Get-Service | Where Status -eq "Running" | Out-GridView
Get-ScheduledTask | Where State -eq "Ready"
```