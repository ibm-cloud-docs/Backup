---

copyright:
  years: 1994, 2024
lastupdated: "2024-04-30"

keywords: IBM Cloud backup, EVault, Carbonite, backup, backup frequency, backup types, backup retention scheme, plugins, delta technology, open files, pricing

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# FAQs
{: #faqs}

## Where can I find my username for the service?
{: faq}
{: #backup-username}
{: support}

The username and password can be seen on the {{site.data.keyword.backup_notm}} instance's Overview page.

You can also see the username and password through the console. To view usernames and accounts that are associated with your Devices, click **Devices > Device list**, and click the device name. Then, click **Passwords**. The {{site.data.keyword.backup_notm}} service is listed in the Software Name column as "Base Client".

Alternatively, you can click **Devices > Manage > Passwords**. The console displays the list of your devices and the associated software with the appropriate usernames and passwords. The service name is listed as "Base Client".

## How can I change my password for the service?
{: faq}
{: #change-pw}
{: support}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the list of backup services.
3. Click the instance name of the backup vault where you want to change your password.
4. On the Overview page, you can see your Portal Password. Click the Pencil icon to modify the password.
5. Enter the new password in the **Password** field.

   The password must be 8 - 12 characters in length. It must include at least one uppercase letter, at least one lowercase letter, at least one numeric character, and at least one of these special characters: `\!@\#%\^`. It can contain only letters, numerals, and these special characters: `\!@\#%\^`.
   {: important}

6. Press Enter to update the password.

## What kind of applications can be backed up?
{: faq}
{: #what-backup}
{: support}

{{site.data.keyword.backup_full}} can be used to back up various applications. {{site.data.keyword.cloud}} also offers software agents for some of the more common software systems that are backed up, which include the following plug-ins.

- [Bare Metal Restore](/docs/Backup?topic=Backup-BMRplugin)
- [Microsoft&reg; Exchange](/docs/Backup?topic=Backup-Exchangeplugin)
- [Microsoft&reg; SQL](/docs/Backup?topic=Backup-MSSQLplugin#MSSQLplugin)
- [Oracle](/docs/Backup?topic=Backup-Oracleplugin#Oracleplugin)
- [VMware&reg; VRA](/docs/Backup?topic=Backup-VRA#VRA)

The plug-ins that are listed here are only compatible with Windows&reg; servers, except for the Oracle or VMware&reg; plug-ins. Each agent is available as an add-on to your backup service at no cost.

## How frequently can we back up the data?
{: faq}
{: #frequency}
{: support}

Within Cloud Backup Portal, backups can be made manually, or can be scheduled as a single instance, or to be recurring. Recurring backups can be made daily, weekly, monthly or on a custom schedule and can be updated or canceled at any time.

Highly frequent backups that run several times daily or hourly can cause backup jobs to become corrupted. This corruption occurs because the backup vault does not get enough time to run required background maintenance tasks. Backup Jobs take precedence over maintenance tasks. So when backups are done with high frequency, the vault continues to run the backup jobs and cause the number of safe-sets to grow.
{: note}

## How do the retention schemes work?
{: faq}
{: #retention}
{: support}

{{site.data.keyword.backup_notm}} allows for data-retention depending on how long you want to roll back to. **Daily** retention schemes hold data for seven days, while **weekly** schemes hold data for one month and **monthly** schemes hold data for one year. At the end of each period, the oldest data set gets rotated out, and the first "delta backup" that was made becomes the oldest available restore point.

You can modify default retention schemes and can create custom retention schemes. It's best to use the default retention schemes as a starting point. When you create a new retention scheme or modify an existing retention, make sure that the Archiving option is not selected. Archiving is not supported.
{: tip}

## What is Delta Technology?
{: faq}
{: #delta}
{: support}

The first backup is a "seed" (a complete, full backup), the next and subsequent ones are "deltas" (that is, changes only), but they are equivalent to, and still considered a "full backup". That is, you're able to restore all or any files from it. With this technology, "full backups" are created at each session, but it saves enormous amounts of space on the vault and decreases the amount of time each subsequent backup takes to complete.

## Are the backups secure?
{: faq}
{: #secure}
{: support}

By default all encryption over the wire (OTW) is encrypted with AES 256-bit encryption. You can also choose to store data in encrypted format by using AES 256-bit.

You must remember your encryption password. Your data can't be restored without your password. If you lose your password, you can't get your data back.
{: important}

Compression ratios allow for zero compression to a maximum ratio compression that, depending on file type, might be compressed anywhere from 20 percent to 30 percent.

## What information is stored with system state backups?
{: faq}
{: #system-state}
{: support}

The system state backups include, but aren't limited to COM + class registration database, registry, boot files, system files, performance counter. It's all dependent on your system. System files vary by system O/S and service packs. Usually there are several thousand of them. MS Windows makes a dynamic list of these DLLs when you include them in the backup. By including the system files, you can recover from corrupted system files, or if you accidentally remove some service packs, or want to recover with a bare-metal restore. You can return to the state of the backup without having to reinstall the O/S from the installation kit, and then installing each service pack separately.

No user data file is included in System state backup. A system-state backup job must be configured as a stand-alone job. There mustn't be any other data source that is included in the System State backup job.
{: important}

## What happens to open files?
{: faq}
{: #open-files}
{: support}

By default, the base client has a state-of-the-art technology to handle most open files that are running on the OS.

## What does VSS (Volume Shadow Copy Services) do?
{: faq}
{: #vss}
{: support}

The current version of the SQL Server plug-in uses VSS (Volume Shadow Copy Services) to complete backups. By using VSS, the SQL Server plug-in effectively backs up SQL databases, even SQL databases that span volumes. Backups can be completed while applications continue to write to a volume. The SQL Server plug-in provides data consistency within and across databases. VSS allows multiple backups to run at the same time.

## Where can I find information about pricing?
{: #pricing}
{: faq}
{: support}

The pricing information for your system resources is shown on the side of the provisioning window, and it shows all of your resource costs. To view the cost estimates for your organization on a per user basis, use the [pricing calculator](https://cloud.ibm.com/cloud-storage/backup/order).

## Can the {{site.data.keyword.backup_notm}} capacity be increased or decreased without compromising the backups?
{: faq}
{: #capacity}
{: support}

You can increase or decrease the size of your vault through the [{{site.data.keyword.cloud_notm}} console](/login){: external}. The modification to the capacity does not affect the integrity of the data that is stored in the vault. For more information, see [expanding vault capacity](/docs/Backup?topic=Backup-expandcapacity#expandcapacity).

## What happens when the {{site.data.keyword.backup_notm}} capacity is exceeded?
{: faq}
{: #exceed-capacity}
{: support}

You can still save and retrieve your backups even if you reached the limit of the capacity that you purchased previously. However, you are going to receive an extra charge for every additional GB that was used in the next billing statement.

## How can I set up notifications in the Cloud Backup Portal that can alert me if a backup fails?
{: faq}
{: #fail-alerts}
{: support}

Notifications can be set up on the Advanced tab. Follow the instructions that you can find in **Quick Links** in the Portal.

## When we use the BMR plug-in, can we move from a single disk to a raid array?
{: faq}
{: #bmr-move}
{: support}

Yes, that works. However, you need to select a large capacity device due to the size decrease that the raid array causes.

## What happens when the disk image is restored to a larger disk than the original volume?
{: faq}
{: #bmr-restore-size}
{: support}

If you restore the image to a larger disk than the original volume, the leftover space is deallocated. So for example - when you have a 500-GB drive and restore its data to a 1-TB disk, you end up with 500 GB of deallocated disk space. With Windows 2008 and newer versions, you can use the built-in disk utility to grow the primary partition.

## Can BMR be used for regular backup?
{: faq}
{: #bmr-regular}
{: support}

BMR backup isn't a disk image, but a system volume image backup system. The system isn't intended to be used for regular backups, but along with them.

## Can BMR be used for database backups?
{: faq}
{: #bmr-backups}
{: support}

Database backups must be made separately with the normal {{site.data.keyword.backup_notm}} methods. BMR doesn't replace the need for SQL or Oracle plug-ins. Though BMR uses the VSS technology to backup open files, it can't always be guaranteed that the backed-up files are transaction consistent. The recommendation for these types of specialized applications is that you create two backup jobs: one to back up OS and application binary files and another one for application data.

## What kind of restorations can be run with BMR?
{: faq}
{: #bmr-restore}
{: support}

You can either do a whole system restore, or you can pick individual files from the backup to restore. The BMR backup job can replace your current file backup job. The restore process is done inside the OS, just like a traditional backup job.

## Does BMR have open file back up capabilities?
{: faq}
{: #bmr-open-backup}
{: support}

BMR has open file back up capabilities. However, BMR doesn't replace the need for SQL or Oracle plug-ins. Click [here](/docs/Backup?topic=Backup-MSSQLplugin) for the MSSQL plug-in installation instructions.

## How much disk space and time does a BMR restore take?
{: faq}
{: #bmr-restore-time}
{: support}

A backup that is made from a default installation uses about 6 GB. Such a restore takes around 15 minutes on a 1-GB port. This process is also affected by private port speed. If you need faster backups and restore, a port speed increase might be needed.

## Is the 32-bit version of EVault for Windows&reg; 8 still supported?
{: faq}
{: #evault}
{: support}

No. The 32-bit version of the backup software agent was retired along with Windows&reg; Server 2008 Standard and data center Editions in March 2017.

## Why does my backup agent show as offline in the WebCC?
{: faq}
{: #agent-offline}
{: support}

If you registered the backup agent to the WebCC but it shows as offline within the Computers section of the WebCC, then the agent cannot communicate with the WebCC. To resolve, make sure you apply the information in [Configuring Ports to allow communication between the backup agent and Cloud Backup Portal](/docs/Backup?topic=Backup-portinfo). For more information, see the troubleshooting section:

* [Why does my Linux&reg; Backup Agent appear offline?](/docs/Backup?topic=Backup-troubleshoot-LinuxAgent)
* [Why does my Windows&reg; Backup Agent appear offline?](/docs/Backup?topic=Backup-troubleshoot-WinAgent)

## Why is my agent Status showing as unconfigured in the WebCC?
{: faq}
{: #agent-unconfigured}
{: support}

If the backup agent appears as `unconfigured` in the WebCC or Portal, confirm that you set up the backup job for your server as it is described in [Configuring simple file-level backups](/docs/Backup?topic=Backup-configureFileBackup).

## I made a mistake in the agent installation process. How can I remove the Backup Agent from the server?
{: faq}
{: #agent-uninstall}
{: support}

You can remove the backup agent either through the command line on a Linux server or through the Control Panel of a Windows&reg; server.
For more information, see the following topics.
- [Uninstalling the Backup Agent from a Windows&reg; Server](/docs/Backup?topic=Backup-cancelBackup#uninstallbackupagentWin)
- [Uninstalling the Backup Agent from a Linux&reg; Server](/docs/Backup?topic=Backup-cancelBackup#uninstallbackupagentLin)

## Can I back up NFS File Shares?
{: faq}
{: #nfs-share-backup}
{: support}

Yes. First, add the Linux&reg; system in the Backup Portal. Then, you can create a backup job for files and folders that are saved on the NFS shares that are attached to this server. The backup job specifies which folders and files to back up, and where to save the data. For more information, see [Configuring NFS backups](/docs/Backup?topic=Backup-configureNFSBackup).

NFS Backups are not supported in Windows.
{: attention}

## Can I see what is backed up and sent to the vault when my agent is offline?
{: faq}
{: #offlineagentdatacheck}
{: support}

Yes. Backup job results can be obtained from the `/opt/BUAgent/xlogcat utility`.

First, go to the directory of the Backup Agent.

```sh
cd /opt/BUAgent
```
{: pre}

Then, use the following syntax to show all backup job results.

```sh
for i in $(ls -d /); do echo "backup history of $i"; find $i -name ".XLOG" ! -name "Agent" -print -exec /opt/BUAgent/xlogcat {} \; | grep -A 17 "errors encountered"; done

backup history of test/
11-May 19:30:36 -0500 BKUP-I-00001 errors encountered: 0 11-May 19:30:36 -0500 BKUP-I-00002 warnings encountered: 0
11-May 19:30:36 -0500 BKUP-I-00003 files/directories examined: 108
11-May 19:30:36 -0500 BKUP-I-00004 files/directories filtered: 104
11-May 19:30:36 -0500 BKUP-I-00006 files/directories deferred: 0
11-May 19:30:36 -0500 BKUP-I-00007 files/directories backed-up: 4
11-May 19:30:36 -0500 BKUP-I-00008 files backed-up: 2
11-May 19:30:36 -0500 BKUP-I-00009 directories backed-up: 2
11-May 19:30:36 -0500 BKUP-I-00010 data stream bytes processed: 146 (146 bytes)
11-May 19:30:36 -0500 BKUP-I-00011 all stream bytes processed: 864 (864 bytes)
11-May 19:30:36 -0500 BKUP-I-00012 pre-delta bytes processed: 345 (345 bytes)
11-May 19:30:36 -0500 BKUP-I-00013 deltized bytes processed: 0 (0 bytes)
11-May 19:30:36 -0500 BKUP-I-00014 compressed bytes processed: 0 (0 bytes)
11-May 19:30:36 -0500 BKUP-I-00015 approximate bytes deferred: 0 (0 bytes)
11-May 19:30:36 -0500 BKUP-I-00016 reconnections on recv fail: 0
11-May 19:30:36 -0500 BKUP-I-00017 reconnections on send fail: 0
11-May 19:30:36 -0500 BKUP-I-04128 job completed at 11-May-2022 19:30:36 -0500
11-May 19:30:36 -0500 BKUP-I-04129 elapsed time 00:00:10 ...
```
{: screen}

You can use the following syntax to show only the backup data size.
```sh
for i in $(ls -d /); do echo "backup history of $i"; find $i -name ".XLOG" ! -name "Agent" -print -exec /opt/BUAgent/xlogcat {} ; | grep -A 1 "deltized bytes processed"; done

backup history of AgtUpgd.backup/
backup history of Languages/
backup history of test/
13-May 19:30:31 -0500 BKUP-I-00013 deltized bytes processed: 0 (0 bytes)
13-May 19:30:31 -0500 BKUP-I-00014 compressed bytes processed: 0 (0 bytes)
11-May 19:30:36 -0500 BKUP-I-00013 deltized bytes processed: 0 (0 bytes)
11-May 19:30:36 -0500 BKUP-I-00014 compressed bytes processed: 0 (0 bytes)
10-May 19:30:15 -0500 BKUP-I-00013 deltized bytes processed: 0 (0 bytes)
10-May 19:30:15 -0500 BKUP-I-00014 compressed bytes processed: 0 (0 bytes)
```
{: screen}

## I'd like to free up space in my vault, how can I remove a specific safe set?
{: faq}
{: #deletesafeset}
{: support}

Customers cannot delete specific backup safe sets. If you want to remove a specific safe set, create a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} so that the {{site.data.keyword.cloud_notm}} Backup Admins can erase it on the backend.

When a Backup deletion request is submitted to the vaults, the data is automatically deleted from the associated vaults. Because backup deletion requests are submitted and processed by the vaults immediately, backup deletion requests cannot be canceled.
{: important}

Backup data deletion is permanent. After the data is deleted from vaults, it cannot be recovered or restored.
{: attention}

If you want to remove all the backups that were created for a server, you can follow the instructions in [Deleting backup tasks](/docs/Backup?topic=Backup-deletetasks&interface=ui).

## Can I move or migrate backup data to another DC or another account?
{: faq}
{: #migratebackups}
{: support}

No, backup data cannot be transferred or migrated to other backup accounts. You can opt to configure [multivaulting](/docs/Backup?topic=Backup-multivault) and store your backups in more than one data center location, but you can't copy data from one vault to another.

## What happens to backups when the Backup service is canceled?
{: faq}
{: #canceledbackup}
{: support}

When the Backup service is canceled, your vault with the backed-up data is deleted. So you can't keep the backups for later use and restore to another server. You can't log in to the Cloud Backup Portal with the canceled credentials either. For more information, see [Canceling the IBM Cloud Backup service](/docs/Backup?topic=Backup-cancelBackup).
