---

copyright:
  years: 1994, 2019
lastupdated: "2019-11-05"

keywords: IBM Cloud backup, EVault, Carbonite, backup, port information, configure, configuring,

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:term: .term}

# Configuring Ports to allow communication between the backup agent and Cloud Backup Portal
{: #portinfo}

The {{site.data.keyword.backup_full}} agent that is installed on your server needs to be able to communicate with the vault that you purchased. The Director host information for an {{site.data.keyword.backup_notm}} user account can be found in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/classic/storage/backup){: external}. The following list provides some examples, and the host name depends on the Data Center that the Director is in.

* ev-director01.service.softlayer.com TCP/2546
* ev-director201.service.softlayer.com TCP/2546
* ev-director301.service.softlayer.com TCP/2546
* ev-vaultlon0201.service.softlayer.com TCP/2546
* ev-vaulthkg0201.service.softlayer.com TCP/2546

Always register agents to the Cloud Backup Portal and the directors by using the FQDN because the IP addresses for these services might change.
{:important}

## Recommended {{site.data.keyword.backup_notm}} Portal settings

Your servers must communicate with the Cloud Backup Portal and all AMP proxy servers for Cloud Backup Portal to work correctly, regardless of the [data centers](#x2052913){:term} location.

{{site.data.keyword.backup_notm}} Portal Registration Service: 

```
cloudbackupregister.service.softlayer.com TCP Port 8086. 
```

Other AMP proxy servers can be added as needed to handle more {{site.data.keyword.backup_notm}} agents that are registered to the Cloud Backup Portal.

TCP Port **8086**, **8087** must have access to **10.0.0.0/8**.
{:important}

If you need to use more restrictive firewall rules, you might lose access to the Cloud Backup Portal as the infrastructure is expanded. 

## Minimum Port Requirements

Currently, at minimum, your servers must allow access to the **10.0.82.0/24** and **10.2.118.0/24** subnets for TCP ports **8086**, **8087**. Other subnets might be used in the future as needed.

## Commercial Portal Servers

Cloud Backup Portal Website
- ibmcloudbackup.service.softlayer.com [10.200.86.22] TCP 443

Cloud Backup Portal Agent Registration
- cloudbackupregister.service.softlayer.com [10.200.86.22] TCP 8086


## Commercial AMP Proxy Servers

The following list contains all of the current AMP proxy servers.

Agents must have connectivity to all proxy servers. New proxy servers might be added to the subnet 10.2.118.0/24 without notification.
{:note}

* evwebamp0901.service.softlayer.com [10.2.118.12] TCP 8087
* evwebamp0902.service.softlayer.com [10.2.118.13] TCP 8087
* evwebamp0903.service.softlayer.com [10.2.118.14] TCP 8087
* evwebamp0904.service.softlayer.com [10.2.118.15] TCP 8087
* evwebamp0905.service.softlayer.com [10.2.118.16] TCP 8087
* evwebamp0906.service.softlayer.com [10.2.118.17] TCP 8087
* evwebamp0907.service.softlayer.com [10.2.118.18] TCP 8087
* evwebamp0908.service.softlayer.com [10.2.118.19] TCP 8087


## Federal Portal Servers

*Cloud Backup Portal and AMP proxy*

- webcc.service.usgov.softlayer.com [100.100.6.20] 8086, 8087

The agent must allow the TCP port 2548 inbound on the private network. This setting allows Central Control and Cloud Backup Portal to connect into the agent to manage it. Older versions of EVault used port 808.

The {{site.data.keyword.backup_notm}} management port (2548) can be changed by updating the registry key at: `HKLM\SOFTWARE\EVault\InfoStage\Agent\AgentPortNumber` (which is a `dword`) in Windows operating systems.

When it comes to connection settings, the difference between desktop Central Control and the Agent is often a point of confusion. The server-resident Agent connects to the {{site.data.keyword.backup_notm}} servers, while the desktop-utilized Central Control connects to your server, by using its address and the server's credentials to access it.
{:tip}
