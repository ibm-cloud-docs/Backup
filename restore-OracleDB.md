---

copyright:
  years: 2021, 2022
lastupdated: "2022-03-17"

keywords: IBM Cloud backup, EVault, Carbonite, backup, configuration,

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Restoring Oracle DB
{: #restoreOracleDB}

After you backed up an Oracle&reg; database by using the Oracle&reg; plug-in, you can restore the database. An Oracle&reg; restore process is performed by a Database Administrator. Briefly, the steps are:
1. Shut down the database.
2. Restore the files.
3. If necessary, reset the control information for the database.
4. Start and recover the database.
5. Reopen the database for use.
{: shortdesc}

The plug-in does not do table-level restores.
{: note}

You might also need to recover the entire system, by performing a [bare metal restore](/docs/Backup?topic=Backup-restoreBMR) (installing the OS, applications, and then the full database (plus any transaction logs) on to a new system).

If there is an Oracle&reg; backup and a full-system backup, then the following steps apply.
1. Restore the system (putting back the contents of ORACLE_HOME – specifically the database installation). If you'd like, you can exclude the data files and archive logs that are backed up by the plug-in.
2. Restore the Oracle&reg; backup, and then copy the required components to the appropriate directories. Follow the standard user-managed Oracle&reg; recovery procedure from the Oracle&reg; backup and recovery guide (available from Oracle) that is appropriate for the operating system.

## Restoring an Oracle database
{: #restoreODB}

1. On the navigation bar, click Computers. A grid lists available servers.
2. Find the computer with the Oracle&reg; database that you want to restore, and expand its view by clicking the row for the computer.
3. Click the Jobs tab.
4. Find the job with the database that you want to restore, and click Restore in the Select Action menu for the job. The Restore dialog box shows the most recent safe set for the job.
5. To restore the database from an older safe set, or from SSI (safe set image) files, follow one of these steps.
   - To restore data from an older safe set, click the calendar button. In the calendar that appears, click the date of the safe set from which you want to restore. To the right of the calendar, click the specific safe set that you want to use.
   - To restore data from SSI files on disk, select Directory on disk from the Source Device list. Click the folder. In the Select Folder dialog box, select the directory where the files are located, and click Okay.

   SSI files are full backups that are exported from the vault or backed up from a computer to disk instead of to a vault. It can be quicker to save backup files on physical media and transport them to a location for a restore than to restore data from a vault in a remote datacenter. You cannot restore from backups to disk (SSI files) until the safe set is imported into the vault and the {{site.data.keyword.backup_full}} Agent is synchronized with the vault.
   {: note}

6. In the Files to Restore box, select the items that you want to restore.
7. Select a Restore Destination option.
   - To restore files and folders to the location where they were backed up, select Restore files to their original location.
   - To restore files and folders to a different location, select Restore files to an alternate location. Click the folder. In the Select Folder dialog box, select the location where you want to restore, and click Okay.

8. Select a File Overwrite option. This option specifies how to restore a file to a location where a file with the same name exists.
   - To overwrite existing files with restored files, select Overwrite existing files.

   If you try to restore multiple files with the same name to an alternate location and select Overwrite existing files, only the last file remains. Other files with the same name are overwritten.
   {: note}

   - To add a numeric extension (for example, .0001) to a restored file name, select Do not overwrite existing files. For example, if you restore a file named “filename.txt” to a location where a file with the same name resides, an extension is added to the restored file name (“filename.txt.0001”).
   - To add a numeric extension (for example, .0001) to an existing file name, select Rename existing files. For example, if you restore a file named “filename.txt” to a location where a file with the same name exists, an extension is added to the existing file name (“filename.txt.0001”). The name of the restored file continues to be “filename.txt”.

9. To change the log detail level or bandwidth settings, click Advanced Restore Options. Specify settings in the Advanced Restore Options dialog box, and click Okay. See [Advanced restore options](#advancedODBRestoreOp).
10. Click Run Restore. The Process Details dialog box shows the restore progress and indicates when the restore is completed. Other recent job processes might also be listed in the dialog box. See View current process information for a job.
11. To close the Process Details dialog box, click Close. Closing the window does not affect the restore process.

   For a full disaster recovery (in which the full database instance is restored), be careful when you recover the database because the plug-in does not back up TEMPORARY tablespaces.
   {: note}
