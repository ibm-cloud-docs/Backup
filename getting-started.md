---

copyright:
  years: 1994, 2025
lastupdated: "2025-12-08"

keywords: IBM Cloud backup, EVault, Carbonite, backup, getting started, set up, configure, run backup, billing, pricing,

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

Backups make sure that your data is safely stored outside of your device and stays protected. {{site.data.keyword.backup_full}} is an automated agent-based backup system that is managed through the Cloud Backup Portal browser-based management utility. {{site.data.keyword.backup_notm}} provides users with a method to back up data between servers in one or more data centers on the {{site.data.keyword.cloud}} network. Administrators can set backups to follow a daily, weekly, or custom schedule that targets full systems, specific directories, or even individual files. Extra plug-ins provide compatibility with software like [MS Exchange](/docs/Backup?topic=Backup-Exchangeplugin), [MS SQL](/docs/Backup?topic=Backup-MSSQLplugin), [Oracle](/docs/Backup?topic=Backup-Oracleplugin#Oracleplugin), [VMware vSphere&reg;](/docs/Backup?topic=Backup-VRA), and enable users to complete a [Bare Metal Restore](/docs/Backup?topic=Backup-BMRplugin#BMRplugin) on physical servers that run Windows OS, when necessary.
{: shortdesc}

## Before you begin
{: #prereqs}
{: step}

You must have a valid license to use {{site.data.keyword.backup_notm}}. You can provision the service when you order a server or you can provision the service as an upgrade. For more information, see [Provisioning {{site.data.keyword.backup_notm}}](/docs/Backup?topic=Backup-ordering).

Each server must have its own {{site.data.keyword.backup_notm}} instance. One {{site.data.keyword.backup_notm}} license cannot be used for multiple servers.
{: important}

## Installing the {{site.data.keyword.backup_notm}} agent
{: #installagentgettingstarted}
{: step}

{{site.data.keyword.backup_notm}} Agent is supported on the following Operating Systems.

[Windows]{: tag-windows} - Oldest supported version of the backup agent is 8.32.
- Windows 2022 - client must be on Agent version 9.00 or earlier.
- Windows Server 2019
- Windows Server 2016

Windows 2022 can be successfully backed up with Windows Agent version 9.00. However, the server shows up in Backup Portal as Windows 2019. Full backup functions were tested with version 9.00. Do not upgrade to a newer version such as 9.30 because it disables the management of the agent when the Backup Portal is upgraded.
{: tip}

[Linux]{: tag-linux} - Current version of Linux Agent is 9.40. BMR backups are not supported.
- Debian 12 (up to Update 5)
- Debian 11 (up to Update 9)
- Debian 10 (up to Update 13)
- openSUSE Linux 15 (up to Service Pack 5) 1
- Oracle Linux&reg; 9 (up to Update 4)
- Oracle Linux&reg; 8 (up to Update 10)
- Oracle Linux&reg; 7 (up to Update 9)
- Red Hat Enterprise Linux&reg; Server 9 (up to Update 4)
- Red Hat Enterprise Linux&reg; Server 8 (up to Update 10)
- Red Hat Enterprise Linux&reg; Server 7 (up to Update 9)
- Rocky Linux&reg; 9 (up to Update 4)
- Rocky Linux&reg; 8 (up to Update 10)
- SUSE Linux&reg; Enterprise Server 15 (up to Service Pack 5) 1
- SUSE Linux&reg; Enterprise Server 12 (up to Service Pack 5) 1 2
- Ubuntu Server 24.04
- Ubuntu Server 22.04
- Ubuntu Server 20.04
- Ubuntu Server 18.04

Follow the instructions appropriate for your OS,
- [Linux]{: tag-linux} [Installing the backup client in Linux&reg;](/docs/Backup?topic=Backup-InstallinLinux)
- [Windows]{: tag-windows} [Installing the backup client in Windows&reg;](/docs/Backup?topic=Backup-InstallinWindows)

## Installing the plug-ins
{: #installpluginsgettingstarted}
{: step}

After the agent is installed, you can add plug-ins at any time. To install a plug-in, run the Agent installation kit. The plug-in appears as an option on the Custom setup page.

1. Run the {{site.data.keyword.backup_notm}} Software Agent - installation program.
1. At the welcome screen, click **Next**.
1. Select **Modify**.
1. Keep the logon credentials for the agent services unchanged. Click **Next**.
1. From the list of plug-ins, select the one that you want to install. Then, select the option to install the feature on the local hard disk. Click **Next**.
1. Select **Keep my current registration**. Click **Next**.
1. Click **Install**.
1. When the installation is complete, click **Finish**.
1. Check to make sure that the services are enabled and running.

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
2. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
3. Click **Storage** > **Cloud Backup** to display the backup services. In the list of all backup service instances, you see the following information.

   | Field         | Description |
   |---------------|-------------|
   | Instance name | The autogenerated name of the vault that you provisioned. |
   | Status        | The status of the service in the Backup Portal. It shows 'Unconfigured' initially. After you complete the steps of configuring the backup jobs and schedules, the status can be 'Completed', 'Completed with warnings', or 'Failed'. It matches the status of the last backup job. |
   | Location      | The data center where the vault is located. For example, Dallas 10. |
   | Capacity      | Size of the vault in GBs.|
   | Last backup   | The date when the last backup job ran. |
   | Usage         | The percentage of capacity that is used by backed up data. This option is hidden by default. Click **Settings** ![Settings icon](../icons/settings.svg "Settings") to customize the list by selecting which columns you want to see. |
   | Source Device | The server that is backed up to the vault. |
   | Actions       | Click **Actions** ![Actions icon](../icons/action-menu-icon.svg "Actions") to display a menu of context-specific actions you can take.|
   {: caption="Details about the backup instances" caption-side="bottom"}

4. Click the instance name to display the details of the backup instance.
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

Archiving is not supported. When you create a retention scheme, or modify an existing scheme, make sure that the Archiving option is **not** selected.
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

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
2. Click **Storage**, and select **Backup** from the list.
3. Click anywhere on the row of the vault that you want to view its storage details. From this view, the password isn't visible.
4. Click the **Show** checkbox next to the **Password** field to view the password for the selected {{site.data.keyword.backup_notm}} service.

Changes that are made to the {{site.data.keyword.backup_notm}} password within the {{site.data.keyword.cloud_notm}} console are made to the service itself. To reset your password, follow the steps in [Managing the username and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
{: important}

## Next steps
{: #nextsteps}
{: step}

For redundancy and peace of mind, consider adding a second vault to your account. You can set up and manage multiple vaults for the same server through the Cloud Backup Portal. For more information, see [Multi-vaulting](/docs/Backup?topic=Backup-multivault).

Cloud Backup Portal's systems are fully documented, and support for the application is accessible within the Portal. Click the question mark in a blue circle for **Help**. Click any article or topic in the navigation bar to view more information.
