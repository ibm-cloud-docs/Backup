---

copyright:
  years: 2021,
lastupdated: "2021-12-10"

keywords: troubleshoot for backup agent, troubleshooting for Linux, question about backup agent, troubleshooting backup, backup auth error, server0, Server0.Password, PARS-E-05152 

subcollection: Backup

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .note}
{:tip: .tip}
{:important: .important}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:external: target="_blank" .external}

# Why does my backup fail with a missing value for Server0.Password message?
{: #troubleshoot-missingServer0password}
{: troubleshoot}
{: support}

A backup fails immediately after startup with the following message in the log files: `PARS-E-05152 A value is required for Server0.Password`.
{: tsSymptoms}
{: shortdesc}

A configuration file (global.vvc) is missing the hash value for the vault password. Without this entry, the agent cannot authenticate to the vault system.
{: tsCauses}

Store the Vault password in the Backup Portal again, to do this go to "Vault Settings" and edit the existing configuration. 
{: tsResolve}

1. In the Backup Portal, click Computers, and click the server name to display its information.
2. Click Vault Settings and from the Action menu, select Edit.
3. Enter the Vault Name.
4. Enter credentials. 
   "Account" is the same as the "Account Name" in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/classic/storage/backup){: external}. Typically, it looks like "SLE[account ID]" or "IBME[account ID]". For more information about finding the user name or changing the backup password, see [Managing user name and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
   {: tip}

5. Click Save.

If this action does not fix the issue, remove the Backup agent from the server and install the newest version. Follow the instructions appropriate for your OS,
- [Installing the backup client in Linux&reg;](/docs/Backup?topic=Backup-InstallinLinux),
- [Installing the backup client in Windows&reg;](/docs/Backup?topic=Backup-InstallinWindows).


