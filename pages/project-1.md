---
layout: default
---

# Building a home SOC with Microsoft Azure

* * * 

### Creating a VM and integrating Microsoft Sentinel to build a simple RDP honeypot 
![new VM with RDP](../images/new-vm-with-rdp)

Since I'm eventually going to try to set up Active Directory, I decided to make a Windows 10 VM with RDP open to test the SIEM I'll be setting up.

![setting up Azure Monitor Agent](../images/add-collection-rule)

To configure Microsoft Sentinel to collect event data from my VM, I had to add a data connector to listen to Windows Security events via Azure Monitor Agent. After everything was installed and deployed, I looked at the security event logs that were already generating. Since I wasn't too familiar with all the fields, I looked at each field and value of the security event logs and decided to filter out what I didn't need, which was the system notifications. 

![query](../images/log-query)
I created this query to not only filter for successful events, such as a successful logon, but to filter out any unnecessary noise, like the system logs. Since I have not yet logged on to the VM, the query yielded no results. All that was left to do after this was to add this to an alert rule on Sentinel and have it periodically check and add to an incident when it detects anything that corresponds with the query. 

![query](../images/rdp-logon) ![query](../images/sentinel-alert)

As expected, when I log in with RDP on my local machine, it generates an incident alert on Sentinel. 

### Creating a threat intelligence feed 
To pull in threat intelligence without relying on already existing Microsoft tools, I had to add another data connector to Sentinel, which was MISP, an open-source threat intelligence platform.  
