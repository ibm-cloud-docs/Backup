---

copyright:
  years: 1994, 2026
lastupdated: "2026-06-08"

keywords: IBM Cloud backup, Exchange, plug-in, plugin, EVault, Carbonite

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.backup_notm}} Exchange plug-in
{: #Exchangeplugin}

Protect Microsoft Exchange databases with {{site.data.keyword.backup_notm}} Exchange plug-in to back up and restore databases through the Cloud Backup Portal.
{: shortdesc}

The Exchange plug-in can be installed with the Windows Agent on the host. The plug-in integrates into the existing architecture.

The plug-in provides the following capabilities:
- Ability to back up and restore MS Exchange databases.

## Installing the plug-in
{: #installExchangePlugin}

The Exchange plug-in is installed during the Windows Agent 64-bit installation. The plug-in can be installed at the same time as the Agent or it can be installed later, by rerunning the installation with the **Modify** option.

Before you install the plug-in for your MS Windows server, stop both {{site.data.keyword.backup_notm}} services in `services.msc`.
{: tip}

When the installation is complete, check to make sure that both services are enabled and running. If Cloud Backup Portal is able to view and access the database, then the installation was successful.
