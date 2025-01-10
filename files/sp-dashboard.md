# Splunk dashboard

* **Dashboards**
  * the information shown on SOC dashboards will vary depending on their focus areas
  * the following information is typically valuable to analysts to have
    * **Firewall graph**
      * showing firewall denies and firewall allows
      * helps analysts spot spikes in firewall denies, that could represent a distributed denial-of-service attack, or a network issue
    * **Number of alerts/offences**
      * showing how many alerts are currently under investigation or pending investigation
    * **Number of alerts closed in the last 24 h**
      * shows how efficiently the team is dealing with security events
    * **Traffic flow going into each SIEM collector**
      * can help security teams identify if a collector stops responding so engineers can investigate the outage
    * **An attack map**
      * that correlates the source IP addresses from alerts, and plots them on a world map
    * **Pie chart showing the event types per alert over the last 24 hours**
      * can help analysts to see which attacks have occurred more recently
  * Dashboards in Splunk are unique to Apps
    * if we create a dashboard for the default Search and Reporting App, then the information will be associated with this application and it’s functionality
    * allows us to create different dashboards for different Apps
  * To create dashboards you need to first create a report
    * used to create panels on a dashboard
    * Whenever you perform a search you can select ‘Save As’ and save it as a ‘Report’
    * Splunk’s documentation recommended naming convention:
      * `group>_<object>_<description>`
        * `group`
          * the name of the group or department using the knowledge object
          * e.g., sales, IT, finance, etc.
        * **object**
          * e.g., report, dashboard, macro, etc.
        * **description**
          * e.g., WeeklySales, FailedLogins, etc.
    * **Dashboard Title**
      * Set an optional human-readable name for the dashboard.
    * **Dashboard ID**
      * Set an identification number for the dashboard.
    * **Dashboard Description**
      * Set an optional description of what the dashboard’s intended purpose is.
    * **Dashboard Permissions**
      * It’s usually a good idea to keep the permissions set to Private until the dashboard has been tested.
    * **Panel Title**
      * Set an optional name for the panel within a dashboard.
    * **Panel Powered By**
      * Select the search query that powers the panel, either by writing a query in the ‘Inline Search’ box, or clicking on ‘Report’ and finding your saved report.