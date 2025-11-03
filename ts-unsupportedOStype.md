---

copyright:
  years: 2021, 2025
lastupdated: "2025-11-03"

keywords: troubleshoot for backup agent, troubleshooting for Linux, question about backup agent, troubleshooting backup, backup auth error, server0, Server0.Password, PARS-E-05152

subcollection: Backup

content-type: troubleshoot

ai-gen-assist: wca
---

{{site.data.keyword.attribute-definition-list}}

# Why does my backup agent installation fail with an error message about an Unsupported OS super type?
{: #troubleshoot-unsupportedOStype}
{: troubleshoot}
{: support}

A backup agent installation fails on a Windows 2022 device and the error message indicates `Unsupported OS super type UNKNOWN`.
{: tsSymptoms}
{: shortdesc}

The current release of the Backup Portal requires that servers that use Windows 2022 connect with the backup agent version 9.0.
{: tsCauses}

To resolve this issue, install the backup agent version 9.0. 
{: tsResolve}

1. Follow the instructions in [Installing the backup client in Windows&reg;](/docs/Backup?topic=Backup-InstallinWindows)
1. Download the executable file for the {{site.data.keyword.backup_notm}} client for version 9.0 from your internal resources or repository.
1. Retry the backup agent installation.
