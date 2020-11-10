---

copyright:
  years: 1994, 2020
lastupdated: "2020-11-10"

keywords: IBM Cloud backup, EVault, Carbonite, backup, getting started, setup, configure, run backup, billing, pricing,

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}
{:term: .term}

# Getting started with {{site.data.keyword.backup_notm}}
{: #getting-started}

Backups ensure that your data is safely stored outside of your device and stays protected. {{site.data.keyword.backup_full}} is an automated agent-based backup system that is managed through the Cloud Backup Portal browser-based management utility. {{site.data.keyword.backup_notm}} provides users with a method to back up data between servers in one or more data centers on the {{site.data.keyword.cloud}} network. Administrators can set backups to follow a daily, weekly, or custom schedule that targets full systems, specific directories, or even individual files. Extra plug-ins ensure compatibility with software like [MS Exchange](/docs/Backup?topic=Backup-Exchangeplugin), [MS SQL](/docs/Backup?topic=Backup-MSSQLplugin), [Oracle](/docs/Backup?topic=Backup-Oracleplugin#Oracleplugin), [VMware vSphere](/docs/Backup?topic=Backup-VRA), and enable users to complete a [Bare Metal Restore](/docs/Backup?topic=Backup-BMRplugin#BMRplugin), when necessary.
{:shortdesc}

## Before you begin
{: #prereqs}

You must have a valid license to use {{site.data.keyword.backup_notm}}. You can obtain the service in two ways.

- [Purchase backups when you Order a Server](/docs/Backup?topic=Backup-ordering#purchasingwithserver).
- [Purchase backups as an Upgrade](/docs/Backup?topic=Backup-ordering#purchasingasupgrade).

For more information about ordering, see [Provisioning {{site.data.keyword.backup_notm}}](/docs/Backup?topic=Backup-ordering).
For more information about pricing, see [{{site.data.keyword.backup_notm}}: Pricing](https://www.ibm.com/cloud/backup/pricing){: external}.


## Installing the {{site.data.keyword.backup_notm}} agent
{: #installagentgettingstarted}

{{site.data.keyword.backup_notm}} Agent is supported on the following Operating Systems.

**Windows** (Oldest supported version 8.32)
 - Windows Server 2019 (WebCC not supported, must use CentralControl)
 - Windows Server 2016
 - Windows Server 2012 R2
 - Windows Server 2012
 - Windows Server 2008 R2
 - Windows Server 2008

**Linux&reg;** (Oldest supported version 8.50)
 - CentOS 8.x (BMR backups are not supported)
 - CentOS 7.x
 - Debian GNU/Linux&reg; 9.x
 - Debian GNU/Linux&reg; 8.x
 - RHEL 8.x (BMR backups are not supported)
 - RHEL 7.x
 - Ubuntu Linux&reg; 18.04
 - Ubuntu Linux&reg; 16.04
 - Ubuntu Linux&reg; 14.04

Follow the instructions appropriate for your OS,
- [Installing the backup client in Linux&reg;](/docs/Backup?topic=Backup-InstallinLinux)
- [Installing the backup client in Windows](/docs/Backup?topic=Backup-InstallinWindows)

## Accessing the Cloud Backup Portal
{: #accessingPortal}

Cloud Backup Portal is used to interact with the {{site.data.keyword.backup_notm}} service that is offered by {{site.data.keyword.cloud}}. The Portal is a browser-based client that runs on the {{site.data.keyword.cloud}} private network and allows full control of any {{site.data.keyword.backup_notm}} service, including configuration and restores.

1. Access the Private Network over VPN.

   Cloud Backup Portal can't be accessed over the public network. A VPN connection must be established first.
   {:important}
2. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the username of the {{site.data.keyword.cloud_notm}} account. Click the expansion arrow to reveal the WebCC portal link.
4. Click **WebCC** to start the portal in your browser.

## Configuring the backup agent and the backup schedule
{: #configureagentschedule}

After you ordered your {{site.data.keyword.backup_notm}} and the agent is installed on the server, you can start creating backups of your data. Through the {{site.data.keyword.backup_notm}} portal, you can manage and monitor your backups. You can choose between manual or automatic backup agent configuration methods.

  - The automatic agent configuration creates a backup job of the complete C Drive (Windows OS) or ./ <root> directory (Linux OS) with Monthly and Daily Retention schemes.

    This job can be modified after it was configured.
    {:note}

    1. Create a password.
    2. Confirm the password.
    3. Add a password hint.
    4. Click **Configure automatically**.

  - If you choose to configure the {{site.data.keyword.backup_notm}} agent manually, the automatic settings are ignored and you can specify the folders and files to be kept with a retention scheme of your choice. For more information, see [Configuring simple file-level backup](/docs/Backup?topic=Backup-configureFileBackup).

      For more information about Retention Schemes, see the [FAQ](/docs/Backup?topic=Backup-faqs#faqs).
      {:tip}

      Archiving is not supported. When you create a retention scheme or modify an existing scheme, make sure that the Archiving option is **not** selected.
      {:important}

## Running your first backup job
{: #runfirstbackup}

1. The new job is displayed on the Computers tab. To start the job, click **Select Actions**, and click **Run Job**.
2. Verify that the destination and retention scheme appear correctly and click **Start Backup**. The Progress Detail page shows the job progress. This window can be closed if needed, the backup job keeps running in background.
3. When the backup job is complete, the Process ID Status shows "Finished". You can view the job history and logs of existing backup jobs on the Computer tab. Select the job that you want to view, click **Select Action**, and choose **History/Logs**.


## Accessing and viewing {{site.data.keyword.backup_notm}} storage details in the Console
{: #viewingdetailsinconsole}

The storage details of your service can be viewed in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/classic/storage/backup){: external} at any time. Details that can be viewed include the password, storage address, and usage that is associated with the selected {{site.data.keyword.backup_notm}} service.

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage**, and select **Backup** from the list.
2. Click anywhere on the row of the vault you want to view its storage details. From this view, the password isn't visible.
3. Click the **Show** check box next to the **Password** field to view the password for the selected {{site.data.keyword.backup_notm}} service.

Changes that are made to the {{site.data.keyword.backup_notm}} password within the {{site.data.keyword.cloud_notm}} console are made to the service itself. To reset your password, follow the steps in [Changing the password for the backup service](/docs/Backup?topic=Backup-changePassword).
{:important}

## Getting more online help
{: #onlinehelp}

Cloud Backup Portal's systems are fully documented and support for the application is accessible within the Portal. Click the white question mark in a blue circle for **Help**. Click any article or topic in the navigation bar to view more information.
