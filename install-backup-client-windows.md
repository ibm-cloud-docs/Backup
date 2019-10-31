---

copyright:
  years: 1994, 2019
lastupdated: "2019-10-31"

keywords: IBM Cloud backup, EVault, Carbonite, backup, install agent, Windows

subcollection: Backup

---
{:pre: .pre}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}

# Installing the backup client in Windows
{: #InstallinWindows}

Installing the {{site.data.keyword.backup_full}} client in Windows is completed through a series of interactions on the server that is designated for the {{site.data.keyword.backup_notm}} service.
{:shortdesc}

For more information about backups for Windows 2016 servers, see [Configuring {{site.data.keyword.backup_notm}} on Windows 2016](/docs/infrastructure/Backup?topic=Backup-InstallinWindows2016).
{:tip}

## Logging in to the target device server
{: #logintargetWin}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational Menu, select **Classic Infrastructure**.
2. Select **Devices** > **Device List** from the main menu to see the list of available servers.
3. Find the device for which you purchased the {{site.data.keyword.backup_notm}} service, and make note of its public IP address.
4. Click the arrow to expand and show more information about the device, including the user name and password. If the password isn't displayed, clicking **Show Password** reveals it.
5. Log in to the target device by using Remote Desktop Connection.

## Downloading the backup client

1. On the target server, open a browser session and enter the following URL to download the executable file for the {{site.data.keyword.backup_notm}} client. <br/>
  ```
  http://downloads.service.softlayer.com/evault/
  ```
  {:pre}

2. Double-click the downloaded file.
3. Click **Run**.


## Installing and Registering the Backup Agent

1. Enter the Network address: <br />
  ```
  ev-webcc01.service.softlayer.com
  ```
  {: pre}

2. Enter the user name in the **user name** field.
3. Enter the password in the **password** field.
6. Click **Next**
7. Click **Install** to complete the installation.

## Configuring backup agents

Log in to Cloud Backup Portal to configure and manage your backup agents. For more information, see the [Getting started tutorial](/docs/infrastructure/Backup?topic=Backup-getting-started#getting-started).
