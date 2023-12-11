---

copyright:
  years: 1994, 2023
lastupdated: "2023-12-11"

keywords: IBM Cloud backup, Exchange, plug-in, plugin, EVault, Carbonite

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Getting started with the Exchange plug-in
{: #Exchangeplugin}

The Exchange plug-in is installed with the Windows&reg; Agent on the host. Through the Cloud Backup Portal, you can configure jobs, back up Exchange databases to a secure, remote vault, and restore Exchange databases. The plug-in integrates into the existing architecture.
{: shortdesc}

The plug-in provides the following capabilities:
- Ability to back up and restore MS Exchange databases.

## Installing the plug-in
{: #installExchangePlugin}

The Exchange plug-in is installed during the Windows&reg; Agent 64-bit installation. The plug-in can be installed at the same time as the Agent or it can be installed later, by rerunning the installation with the **Modify** selection.

Before you install the plug-in for your MS Windows&reg; server, stop both {{site.data.keyword.backup_notm}} services in `services.msc`.
{: tip}

When the installation is complete, check to ensure that both services are enabled and running. If Cloud Backup Portal is able to view and access the database, then the installation was successful.

## Downloading the user guide
{: #ExchangeUserGuide}

Connect to the {{site.data.keyword.cloud}} network with {{site.data.keyword.BluVPN}} so that you can access and download the user guide from the [Downloadable {{site.data.keyword.backup_notm}} Documentation](http://downloads.service.softlayer.com/evault/Documentation/){: external}. The guide describes how to back up and restore MS Exchange databases by using the Exchange plug-in. The guide also describes how to share a DR backup safe-set. With a DR backup safe-set, you can restore specific mailboxes, messages, or other objects to a .pst file by using the Granular Restore for Microsoft&reg; Exchange application.
