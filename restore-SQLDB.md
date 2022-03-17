---

copyright:
  years: 2021, 2022
lastupdated: "2022-03-16"

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

# Restoring MSSQL Database
{: #restoreMSSQLDB}

After backing up SQL Server databases by using the SQL Server plug-in, you can restore databases directly to an SQL Server instance, or restore databases to flat files. When you want to restore an SQL Server database in an Always On Availability Group, you must always restore the database to the primary replica.
{: shortdesc}

## Restoring databases directly to an SQL Server.
{: #restoreDBSQLdirect}

After backing up SQL Server databases using the SQL Server plug-in, you can restore databases directly to an SQL Server instance.
If transaction logs have been backed up using an alternative method (for example, native SQL Server backup), you can restore a database in the restoring state so that you can apply transaction logs to the database after the restore.
When restoring system databases, the master database must be restored first, by itself. Other system databases can then be restored.
You must specify a Windows or SQL Server administrator account for connecting to SQL Server during a restore.
After restoring an SQL Server 2016 database that is stretched to Microsoft Azure, you must run a stored procedure (sys.sp_rda_reauthorize_db) to reconnect the local restored database to the remote Azure data. See “Restore the connection between the SQL Server database and the remote Azure database” on the Microsoft Developer Network website: https://msdn.microsoft.com/en-us/library/mt733205.aspx#reconnect

To restore a database directly to SQL Server:
1. On the navigation bar, click Computers. A grid lists available computers.
2. Find the server with the SQL Server database backup that you want to restore, and expand its view by clicking the row for the computer.
3. Click the Jobs tab.
4. Find the job with the database that you want to restore. In the job’s Select Action menu, click Restore.
5. In the Choose how to restore dialog box, select Restore database to an SQL Server instance.
6. In the Instance list, click the SQL Server instance where you want to restore the database.
7. Connect to the instance by using one of the following methods. 
   - To connect to the instance using a Windows administrator account, select Windows authentication. Enter the user name, password, and domain in the appropriate fields.
   - To connect to the instance using an SQL Server administrator account, select SQL Server authentication. Enter the user name and password in the appropriate fields.
8. Click Continue. The SQL Server Restore dialog box shows the most recent safeset for the job.
9. To restore data from an older safeset, or from SSI (safeset image) files, take one of the following steps.
   - To restore data from an older safeset, click the calendar button. In the calendar that appears, click the date of the safeset from which you want to restore. To the right of the calendar, click the specific safeset that you want to use.
   - To restore data from SSI (safeset image) files on disk, select Directory on disk from the Source Device list. Click the folder button. In the Select Folder dialog box, select the directory where the files are located, and click Okay.

   SSI files are full backups exported from the vault or backed up from a computer to disk instead of to a vault. It can be quicker to save backup files on physical media and transport them to a location for a restore, than to restore data from a vault in a remote datacenter. Note: You cannot restore from backups to disk (SSI files) until the safeset is imported into the vault and the {{site.data.keyword.backup_full}} Agent is synchronized with the vault.
   {: note}

10. In the Database Selection box, select the check box for each database that you want to restore.
11. In the Encryption Password field, enter the data encryption password. To view the password hint, click the Hint button.
12. Select a database name.
    - To restore one or more databases with their original names, select Original Database Names.
    - To restore one database with a new name, select Alternate Database Name. In the field that appears, enter the new name for the restored database.
   
    You can only restore one database if Alternate Database Name is selected.
    {: note}

13. Select the appropriate setting for overwrites.
    - To overwrite the existing database if you restore a database with the same name as the existing database, select Overwrite existing databases.
    - To fail the restore if a database with the same name already exists, clear Overwrite existing databases. If Overwrite existing databases is not selected, and you are restoring multiple databases, the restore fails for all databases if even one database has the same name as an existing database.
14. To restore the database in restoring state, select Restore using No Recovery option. If this option is selected, and transaction logs have been backed up by using an alternative method (for example, a native SQL Server backup), you can apply transaction logs to the database after it is restored.
15. To specify an alternate location for database files, select Alternate Path. Click the folder button. In the Select Folder dialog box, select the alternate file location, and click Okay.

    The alternate file location is only used if the original location for database files is not available.
    {: note}

16. To change the log detail level, bandwidth throttling setting or hard recovery option, click Advanced Restore Options. In the dialog box, select the following:
    - In the Log Level Detail list, select the level of detail for job logging.
    - Select or clear the Use all available bandwidth option.
17. Click Run Restore. The Process Details dialog shows the restore progress and indicates when the restore is completed. Other recent job processes might also be listed in the dialog window. To close the Process Details screen, click Close. Closing the window does not affect the restore process.

## Restoring databases to Flat Files
{: #restoreSQLDBFlatFile}

After backing up SQL Server databases using the SQL Server plug-in, you can restore an SQL Server database to flat files. SQL Server tools can then be used to bring the data into a database.
To restore an SQL Server database to flat files:
1. On the navigation bar, click Computers. A grid lists available servers.
2. Find the computer with the SQL Server database backup that you want to restore, and expand its view by clicking the row for the computer.
3. Click the Jobs tab.
4. Find the job with the database that you want to restore, and click Restore in the Select Action menu for the job.
5. In the Choose how to restore dialog, select Restore to folder.
6. Click Continue. The SQL Server Restore dialog shows the most recent safeset for the job.
7. To restore data from an older safeset, or from SSI (safeset image) files, take one of the following steps.
   - To restore data from an older safeset, click the calendar button. In the calendar that appears, click the date of the safeset from which you want to restore. To the right of the calendar, click the specific safeset that you want to use.
   - To restore data from SSI (safeset image) files on disk, select Directory on disk from the Source Device list. Click the folder button. In the Select Folder dialog, select the directory where the files are located, and click Okay.

   SSI files are full backups exported from the vault or backed up from a computer to disk instead of to a vault. It can be quicker to save backup files on physical media and transport them to a location for a restore, than to restore data from a vault in a remote datacenter. Note: You cannot restore from backups to disk (SSI files) until the safeset is imported into the vault and the {{site.data.keyword.backup_notm}} Agent is synchronized with the vault.
   {: note}

8. In the Database Selection, select the check box for each database that you want to restore.
9. In the Encryption Password field, enter the data encryption password. To view the password hint, click the Hint button.
10. Under Restore Destination, enter a path for the destination, or click the folder button. In the Select Folder dialog box, select the location where you want to restore, and click Okay.
11. To change the log detail level, bandwidth throttling setting or hard recovery option, click Advanced Restore Options. In the dialog box, you can do the following:
    - In the Log Level Detail list, select the level of detail for job logging.
    - Select or clear the Use all available bandwidth option.

12. Click Run Restore. The Process Details dialog shows the restore progress and indicates when the restore is completed. Other recent job processes might also be listed in the dialog. To close the Process Details screen, click Close. Closing the window does not affect the restore process.


## Restoring databases in AlwaysOn Availability groups
{: #restoreSQLDBAlwaysOn}

You must always restore an SQL Server database to the primary replica in an AlwaysOn Availability Group. If a Windows {{site.data.keyword.backup_notm}} Agent and plug-in are not installed on the primary replica server, you must fail over to a server where the {{site.data.keyword.backup_notm}} Agent and plug-in are installed before restoring the database.
After restoring a database to the primary replica and adding the database back into the AlwaysOn Availability Group, it will be replicated to the secondary replicas. To reduce the amount of replication traffic after a restore, you can run a “Restore from another computer” on any secondary replica server where the Windows {{site.data.keyword.backup_notm}} Agent and plug-in are installed.

### Restoring a primary database in an AlwaysOn Availability Group
{: #restorePrimaryAAG}

1. If the {{site.data.keyword.backup_notm}} Agent and plug-in are not installed on the primary replica server, fail over to the secondary database instance where the {{site.data.keyword.backup_notm}} Agent is installed. The formerly secondary replica where you backed up the database becomes the primary replica.
2. Remove the primary database from the AlwaysOn Availability Group.
3. Delete the database from all secondary replicas.
4. Restore the primary database to the original database name using the Overwrite Existing Databases option.
5. Add the restored primary database to the AlwaysOn Availability Group using the Full Synchronization option. After restoring an SQL Server database to the primary replica, to reduce the amount of required replication traffic, you can restore the database to secondary replica servers.

### Restoring a secondary database in an AlwaysOn Availability Group
{: #restoreSecondaryAAG}

1. If you didn't delete the database from all secondary replicas when you restored the primary database, remove the secondary database from the AlwaysOn Availability Group.
2. On a secondary replica server where the {{site.data.keyword.backup_notm}} Agent and plug-in are installed, restore the database by running a Restore From Another Computer by using the No Recovery option.
3. Add the restored secondary database to the AlwaysOn Availability Group using the Join option.

## Restoring items from an SQL server or SharePoint database
{: #restoreSQLDBitems}

If a Microsoft SharePoint 2010 or 2013 database is backed up using the SQL Server plug-in, you can restore items such as site collections, websites, lists and documents from the backup. If a Microsoft SQL Server database is backed up using the SQL Server plug-in or Image plug-in, you can restore specific tables and objects from the backup.

To restore items from a database backup, you must first use Portal to expose the safeset as a shared resource. You can then use a Granular Restore application to find and restore items from the backup. To restore items from a SharePoint database backup, use Granular Restore for Microsoft SharePoint. To restore items from an SQL Server database backup, use Granular Restore for Microsoft Exchange and SQL. For more information, or to obtain a Granular Restore application, contact your service provider.

To restore items from an SQL Server or SharePoint database:
1. On the navigation bar, click Computers. A grid lists available servers.
2. Find the computer with the safeset with SharePoint or SQL Server data that you want to restore, and expand its view by clicking the computer row.
3. Click the Jobs tab.
4. Find the job with the SharePoint data that you want to restore, and click Restore in the Select Action menu for the job. The Choose how to restore dialog box appears.
5. Select Restore items to a SharePoint or SQL Server database, and click Continue. The SQL Server Restore dialog box shows the most recent safeset for the job.
6. To restore data from an older safeset, click the calendar button. In the calendar, click the date of the safeset from which you want to restore. Then, click the specific safeset that you want to use.
7. In the Encryption Password field, enter the data encryption password. To view the password hint, click the Hint button.
8. In the Idle Time field, enter the number of minutes of inactivity after which the share should automatically stop. The value can range from 2 to 180 minutes.
9. Select or clear the Use all available bandwidth option.
10. Click Share. The Process Details dialog shows the status of the share process. When the share is available, the share path appears next to the dialog box.
11. Click the Copy Path to Clipboard button. The path is now available for you to paste into the Granular Restore application.
12. Launch the granular restore.
    - To restore SharePoint items, launch the Granular Restore for Microsoft SharePoint application on a SharePoint 2010 or 2013 system.
    - To restore SQL Server database items, launch the Granular Restore for Microsoft Exchange and SQL application on an SQL Server system.
13. Paste the path for the SQL safeset share into the Granular Restore application.
14. Select and restore your data.
15. When you no longer need to share the safeset, click Stop. When you click Stop or the share idle time is reached, the Process Details dialog shows that the share is no longer available.
