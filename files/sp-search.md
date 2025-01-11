# Splunk search

* **Search Queries**
  * e.g., `index="botsv1" earliest=0`, `search src="10.10.10.50" OR dst="10.10.10.50"`, `index="botsv1" earliest=0 Image="*\\cmd.exe" | stats values(CommandLine) by host`
    * `botsv1` is the dataset
    * `earliest=0` tells Splunk to start looking at the first event in the dataset
  * We can combine text strings, file names, process names, IP addresses, operators and lots more to look for specific data in our index
  * **sampling**
    ![](images/Screenshot%20from%202025-01-10%2017-56-12.png)
    * e.g. show 1 out of 100 events
    * we can fine tune of our search query then turn event sampling off
  * **SELECTED FIELDS** and **INTERESTING FIELDS**
    * information that has been extracted from the raw data, and sorted by Splunk
  * [Splunk docs](https://docs.splunk.com/Documentation/Splunk/9.0.1/SearchTutorial/Startsearching)
  * [Splunk YT](https://www.youtube.com/watch?v=xtyH_6iMxwA&ab_channel=SplunkHow-To)
  * **Sort**
    * `| sort time asc`
      * sort by time ascending (chronological)
      * `desc`
    * `| sort limit=2 time asc`
      * will show only first 2 events
  * **Stats**
    * `stats count by desc`
      * the most frequent value at the top
  * **Table**
    * `| table date, time, srcip, dstport, action, msg`
      * will display table w/ specified values and exclude anything else
  * **Uniq/dedup**
    * `| table srcip | uniq` | `| table action | dedup action`

```[cmd]
index="botsv1" sourcetype="stream:http" http_method=POST uri="/joomla/administrator/index.php" src_i
index="botsv1" sourcetype="stream:http" http_method=POST uri="/joomla/administrator/index.php" src_i
curl ipinfo.io/40.80.148.4
url_domain="imreallynotbatman.com"

index="botsv1" sourcetype="xmlwineventlog" *.exe | rex field=_raw "(?<exe_name>\b[\w-]+\.exe\b)" | stats count by exe_name| sort exe_name

we8105desk.waynecorpinc.local, 192.168.250.100, bob.smith

index="botsv1" sourcetype="xmlwineventlog" Image="C:\\Users\\bob.smith.WAYNECORPINC\\AppData\\Roaming\\{35ACA89F-933F-6A5D-2776-A3589FB99832}\\osk.exe" DestinationPort=6892 | stats count by DestinationIp | uniq

 Fortigate_UTM log; internal IP address is in the ‘dstip’ field
 suricata source "signature":"ET SCAN Acunetix Version 6 (Free Edition) Scan Detected"
 index=* sourcetype=suricata event_type=alert | stats count by severity
```
