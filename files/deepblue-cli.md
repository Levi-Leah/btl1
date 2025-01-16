# DeepBlueCLI

* DeepBlueCLI is a PowerShell script that was created by SANS to aid with the investigation and triage of Windows Event logs
* This tool is able to identify a range of attacks
  * User creation
  * Users being added to groups
  * Password guessing
  * Password spraying
  * Bloodhound offensive tool usage
  * Obfuscated commands
  * PowerShell used to download remote files
  * Suspicious service creation
  * Mimikatz used to dump LSASS.exe for credential collection
* To run:
  * admin PowerShell
  * `Set-ExecutionPolicy Bypass -Scope CurrentUser`
    * the PowerShell script is not digitally signed, Windows is blocking it from executing so we need to disable it
  * `./DeepBlue.ps1 ../Log1.evtx`
  * for local system:
    * `./DeepBlue.ps1 -log security`
    * `./DeepBlue.ps1 -log system`