# Splunk alerts

* **Alerts**
  * **Search Query**
    * Rules in Splunk essentially search queries, so we need to work out what activity we want to detect, and how to write a search query that will identify it
  * **Search Timing**
    * we need to set how often Splunk is going to run the search query to look for any activity that makes the alert conditions
  * **Alert Triggers**
    * we can create thresholds within the alert
    * We can also combine thresholds with time ranges, so if an account fails to login 6 times within 5 minutes, generate an alert
  * **Alert Actions**
    * what actually happens when an alert triggers
      * Sending an email notification
        * typically used for high-profile events that need an immediate response from senior analysts
      * Adding an alert to the list of recently triggered alerts
        * this is how analysts can identify alerts and work to investigate them
      * Log and index searchable alert events
        * this actually allows analysts to quickly view all the information related to the alert that trigged
    * Splunk also has the ability to allow administrators to write their own custom actions using webhooks, so messages can be created in their own applications, such as a mobile app that informs analysts when a new alert has been triggered 