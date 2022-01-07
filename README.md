[comment]: # "Auto-generated SOAR connector documentation"
# Arbor Sightline

Publisher: Splunk Community  
Connector Version: 1\.0\.1  
Product Vendor: Arbor Networks  
Product Name: Arbor Sightline  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.6\.19142  

This app implements ingest action to integrate with Arbor Sightline for retrieving alerts details

[comment]: # " File: readme.md"
[comment]: # "  Copyright (c) 2020 Splunk Inc."
[comment]: # ""
[comment]: # "  Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
### Poll Now

It should be used to get a sense of the containers and artifacts that are created by the app. It
makes use of asset configuration parameter `     max_containers    ` , that can be:

-   **enabled**

    Window *Poll Now* allows the user to set the *Maximum containers* that should be ingested at
    this instance. Since a single container is created for each alert, this value equates to the
    maximum alerts that are ingested by the app. All remaining alerts would be ignored.

-   **disabled**

    Any *Maximum containers* value set in window *Poll Now* will be ignored. The system will ingest
    all alerts found with `       start_time      ` greater than 5 days ago.

### Scheduled Polling

This mode is used to schedule a polling action on the asset at regular intervals, configured via
asset tab *Ingest Settings* .

In the case of Scheduled Polling, on every poll, the app remembers the last time of successful
ingestion and will pickup filtering alerts based on `     start_time    ` greater than this value in
the next scheduled poll.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Arbor Sightline asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | Server URL \(e\.g\. https\://10\.10\.10\.10\)
**verify\_server\_cert** |  optional  | boolean | Verify Server Certificate
**auth\_token** |  required  | password | Sightline API Token
**max\_containers** |  optional  | boolean | Disable Maximum Containers for Polling Now

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[on poll](#action-on-poll) - Action handler for the ingest functionality  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'on poll'
Action handler for the ingest functionality

Type: **ingest**  
Read only: **True**

Ingest DOS alerts from Arbor Sightline\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**start\_time** |  optional  | Start of time range, in epoch time \(milliseconds\) | numeric | 
**end\_time** |  optional  | End of time range, in epoch time \(milliseconds\) | numeric | 
**container\_count** |  optional  | Maximum number of alerts to ingest | numeric | 

#### Action Output
No Output