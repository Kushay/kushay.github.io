---
layout: default
---

# Building a home SOC with Microsoft Azure

* * * 

### Creating a VM and integrating Microsoft Sentinel to monitor for RDP sign ins
![new VM with RDP](../images/new-vm-with-rdp)

Since I'm eventually going to try to set up Active Directory, I decided to make a Windows 10 VM with RDP open to test the SIEM I'll be setting up.

![setting up Azure Monitor Agent](../images/add-collection-rule)

To configure Microsoft Sentinel to collect event data from my VM, I had to add a data connector to listen to Windows Security events via Azure Monitor Agent. After everything was installed and deployed, I looked at the security event logs that were already generating. Since I wasn't too familar with all the fields I looked at each field and value of the security event logs and decided to filter out what I didn't need, which was the system notifications. 
