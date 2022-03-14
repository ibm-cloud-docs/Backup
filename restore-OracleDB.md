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

# Restoring Oracle DB
{: #restoreOracleBackup}

After backing up an Oracle database using the Oracle Plug-in, you can restore the database. An Oracle restore process is performed by a Database Administrator. Briefly, the steps are:
1. Shut down the database.
2. Restore the files.
3. If necessary, reset the control information for the database.
4. Start and recover the database.
5. Re-open the database for use.
The Plug-in does not do table-level restores. 
{: shortdesc}

You might also need to recover the entire system, by performing a “bare metal restore” (installing the OS, applications, and then the full database (plus any transaction logs) onto a new system).

If there is an Oracle backup and a full-system backup:
1. Restore the system (putting back the contents of ORACLE_HOME – specifically the database installation). If you'd like, you can exclude the data files and archive logs that are backed up by the plug-in.
2. Restore the Oracle backup, and then copy the required components to the appropriate directories. Follow the standard user-managed Oracle recovery procedure from the Oracle backup and recovery guide (available from Oracle) that is appropriate for the operating system.

## Restoring an Oracle database
{: #restoreODB}


1. On the navigation bar, click Computers. A grid lists available computers.
2. Find the computer with the Oracle database that you want to restore, and expand its view by clicking the row for the computer.
3. Click the Jobs tab.
4. Find the job with the database that you want to restore, and click Restore in the Select Action menu for the job. The Restore dialog box shows the most recent safeset for the job.
5. To restore the database from an older safeset, or from SSI (safeset image) files, do one of the following:
   - To restore data from an older safeset, click the calendar button. In the calendar that appears, click the date of the safeset from which you want to restore. To the right of the calendar, click the specific safeset that you want to use.
   - To restore data from SSI (safeset image) files on disk, select Directory on disk from the Source Device list. Click the folder. In the Select Folder dialog box, select the directory where the files are located, and click Okay. 
   SSI files are full backups exported from the vault or backed up from a computer to disk instead of to a vault. It can be quicker to save backup files on physical media and transport them to a location for a restore, than to restore data from a vault in a remote datacenter. You cannot restore from backups to disk (SSI files) until the safeset is imported into the vault and the IBM Cloud Backup Agent is synchronized with the vault.
   {: note}

6. In the Files to Restore box, select the items that you want to restore.
7. Select a Restore Destination option.
   - To restore files and folders to the location where they were backed up, select Restore files to their original location.
   - To restore files and folders to a different location, select Restore files to an alternate location. Click the folder. In the Select Folder dialog box, select the location where you want to restore, and click Okay.
8. Select a File Overwrite option. This option specifies how to restore a file to a location where there is a file with the same name.
   - To overwrite existing files with restored files, select Overwrite existing files.
   If you try to restore multiple files with the same name to an alternate location and select Overwrite existing files, only the last file restored will remain. Other files with the same name will be overwritten.
   {: note}

   - To add a numeric extension (for example, .0001) to a restored file name, select Do not overwrite existing files. For example, if you restore a file named “filename.txt” to a location where there is a file with the same name, an extension is added to the restored file name (“filename.txt.0001”).
   - To add a numeric extension (for example, .0001) to an existing file name, select Rename existing files. For example, if you restore a file named “filename.txt” to a location where there is a file with the same name, an extension is added to the existing file name (“filename.txt.0001”). The name of the restored file continues to be “filename.txt”.
9. To change the log detail level or bandwidth settings, click Advanced Restore Options. Specify settings in the Advanced Restore Options dialog box, and click Okay. See [Advanced restore options](#advancedODBRestoreOp).
10. Click Run Restore. The Process Details dialog box shows the restore progress and indicates when the restore is completed. Other recent job processes might also be listed in the dialog box. See View current process information for a job.
11. To close the Process Details dialog box, click Close. Closing the window does not affect the restore process, it continues to run.
   For a full disaster recovery (in which the full database instance is restored), be careful when you recover the database because the plug-in does not back up TEMPORARY tablespaces.
   {: note}

## Advanced Restore Options
{: #advancedODBRestoreOpt}

When you restore Oracble data, you can specify the following options.

### Log Options

Select one of the following job logging levels from the list:
- Files — Provides the most detailed information, and is typically used for troubleshooting. Provides information about files that are backed up.
- Directory — Provides less detail than the Files logging level. Provides information about folders that are backed up.
- Summary — Provides high-level information, including the vault and IBM Cloud Backup Agent version, and backup sizes.
- Minimal — Provides high-level information, including the vault and IBM Cloud Backup Agent version.
Changing the logging level only affects log files that are created from that point and after. It does not affect previously-created log files.

### Performance Options

Bandwidth throttling settings specify the amount of bandwidth consumed by an IBM Cloud Backup Agent for backups. For example, you might want to restrict the amount of bandwidth used for daytime backups so that online users are not affected, and allow unlimited bandwidth usage at night so that scheduled backups run as fast as possible.

Bandwidth settings include:
- Maximum bandwidth (upper limit), in megabits per second, to be consumed by the IBM Cloud Backup Agent for all backups and restores
- Period of time during the day that throttling is in effect. Only one time window can be specified. Outside the window, no throttling takes place.
- Days of the week that throttling is in effect
If the bandwidth throttling time period begins when a backup is underway, the maximum bandwidth is applied dynamically to the running backup. Similarly, if the bandwidth throttling time period ends when a backup is running, bandwidth throttling is ended for the backup.
If you edit an IBM Cloud Backup Agent’s bandwidth settings while a backup is running, the new IBM Cloud Backup Agent settings do not affect the backup that is running. Bandwidth settings are applied when a backup starts, and are not applied to backups that are already running.



