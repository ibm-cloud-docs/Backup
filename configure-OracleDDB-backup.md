---

copyright:
  years: 2021, 2022
lastupdated: "2022-03-14"

keywords: IBM Cloud backup, EVault, Carbonite, backup, configuration,

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:support: data-reuse='support'}

# Configuring Oracle DB backups
{: #configureOracleBackup}

To protect Oracle&reg; databases, install the Oracle&reg; plug-in with the {{site.data.keyword.backup_full}} agent on the Oracle&reg; database server. You can then add and run backup jobs that specify which databases to back up, and where to save the backup data. The plug-in provides ARCHIVELOG-based, non-RMAN backups of whole online database instances. All nontemporary tablespaces and instance parameter files are automatically backed up. Full and partial databases are restored through normal user-managed Oracle recovery mechanisms. Database passwords are encrypted for enhanced security over script-based methods.
{: shortdesc}

The Oracle plug-in performs what the Oracle Corporation deems an “inconsistent” whole database backup that requires that the database is run in ARCHIVELOG mode. During a live backup, any changes to the database are written to archive logs. The database administrator must ensure that the database is in ARCHIVELOG mode.
{: important}

## Starting Cloud Backup Portal
{: #startPortalconfigODB}
{: help}

You need to be connected to the {{site.data.keyword.cloud}} private network to be able to start the Portal.
{: important}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} account.
4. Click **View backup portal** to start the portal in your browser.

   If the Portal doesn't start, you might have a problem with your VPN connection. You might also see a message that says that the form you’re sending isn’t secure. It is expected - proceed by sending the form.
   {: tip}

## Configuring a backup job
{: #configureBackupjobODB}
{: help}

Through the {{site.data.keyword.backup_notm}} portal, you can manage and monitor your backups. You can create a backup job for one or more Oracle databases. The backup job specifies which databases to back up, and where to save the backup data. When you create an Oracle database backup job, you must specify credentials for the {{site.data.keyword.backup_notm}} Agent to use to connect to the Oracle server.

To add an Oracle database backup job:
1. On the navigation bar, click **Computers**. The Computers page shows registered servers.
2. Find a server with the Oracle plug-in, and expand its view by clicking the computer row.
3. Click the **Jobs** tab.
   
   If the server doesn't have a valid vault connection, then you can't access the Jobs tab.
   {: note}

4. In the Select Job Task menu, click **Create New Oracle Job**.
5. In the Connect to Oracle Server dialog box, provide the following information.
   - In the Database Service Name box, type the database instance.
   - In the User Name box, type the name of a user who has sysdba privileges.
   - In the Password box, type the password for the specified user.
6. Click **Connect**.
7. In the Create New Job dialog box, specify the following information.
   - In the Name box, type a name for the backup job.
   - In the Description box, optionally type a description for the backup job.
   - In the Destination list, select the vault where you want to save the backup data.

     A vault appears in the list if it is assigned to the user, or if the user added it in the computer’s Vault Settings.
     {: tip}

   - In the Log File Options list, select the level of detail for job logging. For more information, see [Log file options](#ODBLogfile).
   - For new backup jobs, the encryption method is AES 256 bit. Existing jobs can have other encryption methods. For more information, see [Encryption settings](#ODBEncrypt).
   - In the Password and Confirm Password boxes, enter an encryption password. You can also enter a password hint in the Password Hint box.
8. In the Include in Backup box, select the database that you want to back up.
9. Click **Save**. The job is now created, and the View/Add Schedule dialog box appears. Next, you can create a schedule for running the backup. Click Cancel if you don't want to create a schedule at this time.


## Scheduling the backup job
{: #ODBSchedulejob}

1. In the View/Add Schedule dialog box, click **Add Schedule**.
2. In the new schedule row, in the Retention list, click a retention type.
3. In the Schedule box, click the arrow.
4. In the Configure Job Schedule dialog box, choose one of the following options.
     - To run the backup on specific days each week, in the Schedule View list, click **Days of Week**. Select the days when you want to run the job. Then, use the At field to specify the time when you want to run the job.
     -  To run the backup on specific dates each month, click **Days of Month** in the Schedule View list. On the calendar, select the dates when you want to run the job. Then, use the At field to specify the time when you want to run the job.
     - To create a custom schedule, click **Custom** in the Schedule View list. In the Custom Cycle dialog box, enter a custom schedule. Be sure to follow the format and notation as described.
5. Click **Okay**. The schedule appears in the Schedule box.
6. In the Compression list, click a compression level for the backup data. Compression levels optimize the volume of data sent against the speed of processing.
7. Deferring: select one of the following options.
    - To allow the backup job to run without a time limit, click None in the Deferring list.
    - To specify a maximum amount of time that the backup job can run, click **Minutes** or **Hours** in the Deferring list. In the adjacent box, type the maximum number of minutes or hours that the job can run.
    
    When you use the deferring option, the backup job doesn't back up any new data after the specified amount of time, even if some data is not backed up. Changes to data that was previously backed up are still backed up, regardless of the amount of time specified.
    {: note}

8. To run the job on the specified schedule, select the Enable check box near the end of the row.
9. Click **Save**.


## Log file Options
{: #ODBLogfile}

When you create or edit a backup job, you can specify the level of detail for job logging. Select one of the following job logging levels from the list.
- Files: This setting provides the most detailed information, and is typically used for troubleshooting. Provides information about files that are backed up.
- Directory: This setting provides less detail than the Files logging level. Provides information about folders that are backed up.
- Summary: This setting provides high-level information, including the vault and {{site.data.keyword.backup_notm}} Agent version, and backup sizes.
- Minimal: This setting provides high-level information, including the vault and {{site.data.keyword.backup_notm}} Agent version.

Changing the logging level only affects log files that are created at that point and after. It does not affect previously created log files.
{: important}

## Encryption settings and password
{: #ODBEncrypt}

Encryption settings specify the encryption type for backup data at rest on the vault. AES 256-bit encryption is the default encryption type available for new backup jobs. When you create a backup job, you must enter a password for the encrypted data. The password is case-sensitive. To recover the data, you must provide the encryption password that was entered when the files were backed up.
You can also enter a password hint. When you want to restore data, you can view the password hint to remind you of the encryption password for this job.

If you forget the encryption password, you lose access to the data. You cannot retrieve the password from the system.
{: important}

## Downloading the user guide
{: #OracleConfigUserGuide}

Connect to the {{site.data.keyword.cloud}} network with [{{site.data.keyword.BluVPN}}](https://www.ibm.com/cloud/vpn-access){: external} so that you can download the user guides from the [Downloadable {{site.data.keyword.backup_notm}} Documentation](http://downloads.service.softlayer.com/evault/Documentation/){: external}.
