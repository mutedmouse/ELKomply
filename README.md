# ELKomply
## Caveats and Concerns
* This app is suitable for installation at any stage of your splunk architecture
  - disabling/enabling of features is highly recommended depending on installation location
  - FOR EXAMPLE:<br />
  calculated fields and aliases are not necessary on **INDEXERS** but are required on **SEARCH HEADS** and **ES NODES**<br /><br />
* This app currently requires two indexes to be created and accessible on **INDEXERS**:
  - host (create with `$SPLUNK_HOME/bin/splunk add index host`)
  - network (create with `$SPLUNK_HOME/bin/splunk add index network`
  - This requirement will be removed in future releases
* HEC (HTTP Event Collectors) are not currently configured for https
  - HEC Tokens are **disabled** by default on Splunk instance:
  - Enable on Settings -> Data Inputs -> HTTP Event Collector -> Global Settings
  - Select "Enabled"
  - Deselect "Enable SSL"<br /><br />
  - **SAMPLE** HEC tokens are configured in the $SPLUNK_HOME/etc/apps/Elcomply/default/inputs.conf for your convenience, please randomize these<br />
    This process will be completed automatically on install in the future releases<br /><br />
  - SSL HEC tokens are available but beyond the scope of this documentation:
  - REFERENCES:<br />
  https://docs.splunk.com/Documentation/Splunk/8.1.0/Admin/Inputsconf#http:_.28HTTP_Event_Collector.29<br />
  https://docs.splunk.com/Documentation/Splunk/latest/Security/Howtoself-signcertificates<br />
  https://docs.splunk.com/Documentation/Splunk/8.1.0/Security/HowtoprepareyoursignedcertificatesforSplunk<br />
  
## Currently Supported
### Platforms and Sources
* SecurityOnion 2.x
  - Zeek (metadata)
  - Suricata (alerts)
  
* SecurityOnion 16.x
  - Zeek (metadata)
  - Snort (alerts)
  - Suricata (alerts)
  
* HELK
  - winlogbeats (Sysmon and WinEventLogs)
  
### Datamodels
* Certificates (SecurityOnion 16.x)
* Endpoint (HELK)
* Intrusion Detection (SecurityOnion 2.x, SecurityOnion 16.x)
* Network Resolution (DNS) (SecurityOnion 2.x, SecurityOnion 16.x) 
* Network Traffic (SecurityOnion 16.x, HELK) 

## TODO
### Platforms and Sources
* SecurityOnion 2.x
  - Suricata (metadata)
  - Winlogbeat (Sysmon and WinEventLogs)
  
* RockNSM
  - Zeek (metadata)
  - Suricata (alerts)

* Moloch
  - Filebeat (metadata)
  
### Datamodels
* Authentication (HELK, SecurityOnion 2.x)
* Certificates (SecurityOnion 2.x)
* Network Traffic (SecurityOnion 2.x)
