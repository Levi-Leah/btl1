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