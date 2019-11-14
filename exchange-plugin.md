---

copyright:
  years: 1994, 2019
lastupdated: "2019-11-14"

keywords: IBM Cloud backup, Exchange, plug-in, plugin, EVault, Carbonite

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}

# Learn about the Exchange plug-in
{: #Exchangeplugin}

The Exchange plug-in is installed with the Windows Agent on the host. Through the Cloud Backup Portal, you can configure jobs, back up Exchange databases to a secure, remote vault, and restore Exchange databases. The plug-in integrates into the existing architecture.
{:shortdesc}

**Capabilities provided**

- Ability to back up and restore Microsoft Exchange databases.

## Installing the plug-in
{: #installExchangePlugin}

The Exchange plug-in is installed during the Windows Agent 64-bit installation. The plug-in can be installed at the same time as the Agent or it can be installed later, by rerunning the installation with the **Modify** selection.

Before you install the plug-in for your MS Windows server, stop both {{site.data.keyword.backup_notm}} services in `services.msc`.
{:tip}

1. Browse to `c:\installs\{{site.data.keyword.backup_notm}}` folder and run the .exe file with the higher revision number.
2. At the language screen, click **OK**
3. At the welcome screen, click **Next**
4. Select the **Modify installation**, and click **Next**.
5. Select the **Leave Unchanged**, and click **Next**.
6. At the custom setup screen, select each plug-in that you purchased.
7. Select **This feature will be installed on ...**, then click **Next**.
8. Select **Keep my current registration**, and click **Next**.
9. Click **Install**.
10. When installed, check to ensure that both services are enabled and running.
11. If Cloud Backup Portal is able to access or view the database, then the installation was successful.

## Downloading the user guide
{: #ExchangeUserGuide}

Connect to the {{site.data.keyword.cloud}} network with {{site.data.keyword.BluVPN}} so that you can access and download the user guide from the [Downloadable {{site.data.keyword.backup_notm}} Documentation](http://downloads.service.softlayer.com/evault/Documentation/){: external}. The guide describes how to back up and restore MS Exchange databases by using the Exchange plug-in. The guide also describes how to share a DR backup safe-set. With a DR backup safe-set, you can restore specific mailboxes, messages, or other objects to a .pst file by using the Granular Restore for Microsoft Exchange application.
