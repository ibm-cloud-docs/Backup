---

copyright:
  years: 1994, 2023
lastupdated: "2023-12-11"

keywords: IBM Cloud backup, EVault, Carbonite, backup, getting started, setup, configure, run backup, billing, pricing,

subcollection: Backup

content-type: tutorial
services:
account-plan: paid
completion-time: 2h

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.backup_notm}}
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-services=""}
{: toc-completion-time="2h"}

Backups ensure that your data is safely stored outside of your device and stays protected. {{site.data.keyword.backup_full}} is an automated agent-based backup system that is managed through the Cloud Backup Portal browser-based management utility. {{site.data.keyword.backup_notm}} provides users with a method to back up data between servers in one or more data centers on the {{site.data.keyword.cloud}} network. Administrators can set backups to follow a daily, weekly, or custom schedule that targets full systems, specific directories, or even individual files. Extra plug-ins ensure compatibility with software like [MS Exchange](/docs/Backup?topic=Backup-Exchangeplugin), [MS SQL](/docs/Backup?topic=Backup-MSSQLplugin), [Oracle](/docs/Backup?topic=Backup-Oracleplugin#Oracleplugin), [VMware vSphere&reg;](/docs/Backup?topic=Backup-VRA), and enable users to complete a [Bare Metal Restore](/docs/Backup?topic=Backup-BMRplugin#BMRplugin) on physical servers that run Windows&reg; OS, when necessary.
{: shortdesc}

## Before you begin
{: #prereqs}
{: step}

You must have a valid license to use {{site.data.keyword.backup_notm}}. You can provision the service when you order a server or you can provision the service as an upgrade. For more information, see [Provisioning {{site.data.keyword.backup_notm}}](/docs/Backup?topic=Backup-ordering).

Each server must have its own {{site.data.keyword.backup_notm}} Account. One {{site.data.keyword.backup_notm}} license cannot be used for multiple servers.
{: important}

## Installing the {{site.data.keyword.backup_notm}} agent
{: #installagentgettingstarted}
{: step}

{{site.data.keyword.backup_notm}} Agent is supported on the following Operating Systems.

[Windows]{: tag-windows} - Oldest supported version of the backup agent is 8.32.
- Windows&reg; Server 2019
- Windows&reg; Server 2016
- Windows&reg; Server 2012 R2
- Windows&reg; Server 2012
- Windows&reg; Server 2008 R2
- Windows&reg; Server 2008

Windows 2019 does successfully back up with the Windows agent version 8.60. However, the server shows up in the Backup Portal as Windows 2016. Full backup functions were tested with version 8.60. Do not upgrade to a higher version such as 8.70 because it disables the management of the agent until the Backup Portal is upgraded. The customer can also install Central Control to manage the backup agent. The latest version of Central Control is available to download from [here](http://downloads.service.softlayer.com/evault/CentralControl/){: external}. You must install .NET 3.5 before you install the Central Control application. .Net can be installed by using the Add Roles and Features Wizard from the Server Manager. Multiple.NET can be installed at the same time.
{: tip}

[Linux]{: tag-linux} - Oldest supported version of the backup agent is 8.50. BMR backups are not supported.
- CentOS 8.x (It requires backup agent version 8.83.)
- CentOS 7.x
- Debian GNU/Linux&reg; 9.x
- Debian GNU/Linux&reg; 8.x
- RHEL 8.x (It requires backup agent version 8.83.)
- RHEL 7.x
- Ubuntu Linux&reg; 18.04 (It requires backup agent version 8.62 or newer.)
- Ubuntu Linux&reg; 16.04
- Ubuntu Linux&reg; 14.04

Follow the instructions appropriate for your OS,
- [Linux]{: tag-linux} [Installing the backup client in Linux&reg;](/docs/Backup?topic=Backup-InstallinLinux)
- [Windows]{: tag-windows} [Installing the backup client in Windows&reg;](/docs/Backup?topic=Backup-InstallinWindows)

## Installing the plug-ins
{: #installpluginsgettingstarted}
{: step}

After the agent is installed, you can add plug-ins at any time. To install a plug-in, run the Agent installation kit. The plug-in appears as an option on the Custom Setup page.

1. Run the {{site.data.keyword.backup_notm}} Software Agent - InstallShield Wizard.
1. At the welcome screen, click **Next**.
1. Select **Modify**.
1. Select to leave the logon credentials for the agent services unchanged. Click **Next**.
1. From the list of plug-ins, select the one that you want to install. Then, select the option to install the feature on the local harddrive. Click **Next**.
1. Select **Keep my current registration**. Click **Next**.
1. Click **Install**.
1. When the installation is complete, click **Finish**.
1. Check to ensure that the services are enabled and running.

For more information about the available plug-ins, see the following topics.
- [Bare Metal Server plug-in](/docs/Backup?topic=Backup-BMRplugin)
- [Exchange plug-in](/docs/Backup?topic=Backup-Exchangeplugin)
- [SQL Server plug-in](/docs/Backup?topic=Backup-MSSQLplugin)
- [Oracle plug-in](/docs/Backup?topic=Backup-Oracleplugin)
- [vSphere Recovery Agent](/docs/Backup?topic=Backup-VRA)

## Accessing the Cloud Backup Portal
{: #accessingPortal}
{: step}

Cloud Backup Portal is used to interact with the {{site.data.keyword.backup_notm}} service that is offered by {{site.data.keyword.cloud}}. The Portal is a browser-based client that runs on the {{site.data.keyword.cloud}} private network and allows full control of any {{site.data.keyword.backup_notm}} service, including configuration and restores.

1. Access the Private Network over [{{site.data.keyword.BluVPN}}](/docs/iaas-vpn?topic=iaas-vpn-getting-started){: external}. The Cloud Backup Portal can't be accessed over the public network. A VPN connection must be established first.
2. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
3. Click **Storage** > **Cloud Backup** to display the backup services.
4. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
5. Click **View backup portal** to start the portal in your browser.

## Configuring the backup job and the backup schedule
{: #configureagentschedule}
{: step}

After you ordered your {{site.data.keyword.backup_notm}} and the agent is installed on the server, you can start creating backups of your data. Through the {{site.data.keyword.backup_notm}} portal, you can manage and monitor your backups. You can choose between manual or automatic backup job configuration methods.

- The automatic configuration creates a backup job of the complete C Drive in [Windows]{: tag-windows} or `./ <root>` directory in [Linux]{: tag-linux} with Monthly and Daily Retention schemes.

   This job can be modified after it was configured.
   {: note}

   1. Create a password.
   2. Confirm the password.
   3. Add a password hint.
   4. Click **Configure automatically**.

- If you choose to configure the job manually, the automatic settings are ignored. Then, you can specify the folders and files to be kept with a retention scheme of your choice. For more information, see [Configuring a simple file-level backup](/docs/Backup?topic=Backup-configureFileBackup).

For more information about Retention Schemes, see the [FAQ](/docs/Backup?topic=Backup-faqs#faqs).
{: tip}

Archiving is not supported. When you create a retention scheme or modify an existing scheme, make sure that the Archiving option is **not** selected.
{: important}

## Running your first backup job
{: #runfirstbackup}
{: step}

1. The new job is displayed on the Computers tab. To start the job, click **Select Actions**, and click **Run Job**.
2. Verify that the destination and retention scheme appear correctly and click **Start Backup**. The Progress Detail page shows the job progress. This window can be closed if needed, and the backup job keeps running in the background.
3. When the backup job is complete, the Process ID Status shows "Finished". You can view the job history and logs of existing backup jobs on the Computer tab. Select the job that you want to view, click **Select Action**, and choose **History/Logs**.

## Accessing and viewing {{site.data.keyword.backup_notm}} storage details in the Console
{: #viewingdetailsinconsole}
{: step}

The storage details of your service can be viewed in the [{{site.data.keyword.cloud_notm}} console](/cloud-storage/backup){: external} at any time. Details that can be viewed include the password, storage address, and usage that is associated with the selected {{site.data.keyword.backup_notm}} service.

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage**, and select **Backup** from the list.
3. Click anywhere on the row of the vault that you want to view its storage details. From this view, the password isn't visible.
4. Click the **Show** checkbox next to the **Password** field to view the password for the selected {{site.data.keyword.backup_notm}} service.

Changes that are made to the {{site.data.keyword.backup_notm}} password within the {{site.data.keyword.cloud_notm}} console are made to the service itself. To reset your password, follow the steps in [Managing the username and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
{: important}

## Getting more online help
{: #onlinehelp}
{: step}

Cloud Backup Portal's systems are fully documented and support for the application is accessible within the Portal. Click the question mark in a blue circle for **Help**. Click any article or topic in the navigation bar to view more information.
