---

copyright:
  years: 1994, 2024
lastupdated: "2024-07-23"

keywords: IBM Cloud backup, EVault, Carbonite, backup, port information, configure, configuring,

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Configuring Ports to allow communication between the backup agent and Cloud Backup Portal
{: #portinfo}

The {{site.data.keyword.backup_full}} agent that is installed on your server needs to be able to communicate with the vault that you purchased. The Director host information for an {{site.data.keyword.backup_notm}} user account can be found in the [{{site.data.keyword.cloud_notm}} console](/cloud-storage/backup){: external}. The following list provides some examples, and the hostname depends on the data center that the director resides in.

* `ev-director301.service.softlayer.com TCP/2546`
* `ev-vaultdal1201.service.softlayer.com TCP/2546`
* `ev-vaultlon0201.service.softlayer.com TCP/2546`
* `ev-vaulthkg0201.service.softlayer.com TCP/2546`

Always register agents to the Cloud Backup Portal and the directors by using the FQDN because the IP addresses for these services might change.
{: important}

## Recommended {{site.data.keyword.backup_notm}} Port settings
{: #recommendedportsettings}

Your servers must communicate with the Cloud Backup Portal and all AMP proxy servers for Cloud Backup Portal to work correctly, regardless of the data center's location. TCP Port 8086, 8087 must have access to `10.0.0.0/8`.

{{site.data.keyword.backup_notm}} Portal Registration Service 
- `cloudbackupregister.service.softlayer.com TCP Port 8086`

If you need to use more restrictive firewall rules, you might lose access to the Cloud Backup Portal as the infrastructure is expanded.
{: important}

## Minimum Port Requirements
{: #minportreq}

Currently, at minimum, your servers must allow access to the `10.200.86.0/24` and `10.2.118.0/24` subnets for TCP ports **8086**, **8087**. Other subnets might be used in the future as needed.

## Commercial Portal Servers
{: #commercialportalservers}

Cloud Backup Portal website
- `ibmcloudbackup.service.softlayer.com [10.200.86.22] TCP 443`

Cloud Backup Portal Agent Registration
- `cloudbackupregister.service.softlayer.com [10.200.86.22] TCP 8086`


## Commercial AMP Proxy Servers
{: #commercialAMPservers}

The following list contains all of the current AMP proxy servers.

Agents must have connectivity to all proxy servers. New proxy servers might be added to the subnet `10.2.118.0/24` without notification.
{: note}

* `evwebamp0901.service.softlayer.com [10.2.118.12] TCP 8087`
* `evwebamp0902.service.softlayer.com [10.2.118.13] TCP 8087`
* `evwebamp0903.service.softlayer.com [10.2.118.14] TCP 8087`
* `evwebamp0904.service.softlayer.com [10.2.118.15] TCP 8087`
* `evwebamp0905.service.softlayer.com [10.2.118.16] TCP 8087`
* `evwebamp0906.service.softlayer.com [10.2.118.17] TCP 8087`
* `evwebamp0907.service.softlayer.com [10.2.118.18] TCP 8087`
* `evwebamp0908.service.softlayer.com [10.2.118.19] TCP 8087`
* `evwebamp0909.service.softlayer.com [10.2.118.20] TCP 8087`
* `evwebamp0910.service.softlayer.com [10.2.118.21] TCP 8087`


## Federal Portal Servers
{: #fedservers}

Cloud Backup Portal and AMP proxy 
- `webcc.service.usgov.softlayer.com [100.100.6.20] TCP 8086, 8087`

The agent must allow the TCP port 2548 inbound on the private network. This setting allows Central Control and Cloud Backup Portal to connect into the agent to manage it. Older versions of EVault used port 808.

The {{site.data.keyword.backup_notm}} management port (2548) can be changed by updating the registry key at: `HKLM\SOFTWARE\EVault\InfoStage\Agent\AgentPortNumber` (which is a `dword`) in Windows operating systems.

When it comes to connection settings, the difference between desktop Central Control and the Agent is often a point of confusion. The server-resident Agent connects to the {{site.data.keyword.backup_notm}} servers, while the client-based Central Control connects to your server, by using its address and the server's credentials to access it.
{: tip}
