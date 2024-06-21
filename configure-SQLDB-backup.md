---

copyright:
  years: 2021, 2024
lastupdated: "2024-06-20"

keywords: IBM Cloud backup, EVault, Carbonite, backup, configuration,

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Configuring MSSQL database backups
{: #configureMSSQLBackup}

To protect Microsoft&reg; SQL Server databases, install the SQL Server plug-in with the Windows&reg; {{site.data.keyword.backup_full}} Agent on the server where the SQL Server is running. Then, you can add and run backup jobs that specify which SQL Server databases to back up and where to save the backup data. The SQL Server plug-in can back up databases that span volumes, databases that have Transparent Data Encryption (TDE) enabled and databases in AlwaysOn Availability Groups. The plug-in can also back up BLOB data from filestream-enabled databases. You can run full database backups, full database with transaction log backups, or transaction log only backups. When it is installed with the Cluster Support plug-in, the SQL Server plug-in can protect databases on SQL Server clusters.
{: shortdesc}

You can back up transaction logs for databases only when they use the full or bulk-logged recovery model.
{: note}

The account that was specified during the {{site.data.keyword.backup_notm}} Agent and SQL Server plug-in installation must have the public server role to perform full SQL Server backups. The account must have the "sysadmin" role to perform transaction log backups.
{: requirement}

## Starting Cloud Backup Portal
{: #startPortalconfigSQLDB}
{: help}

You need to be connected to the {{site.data.keyword.cloud}} private network to be able to start the Portal.
{: important}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
4. Click **View backup portal** to start the portal in your browser.

   If the Portal doesn't start, you might have a problem with your VPN connection. You might also see a message that says that the form you’re sending isn’t secure. It is expected - proceed by sending the form.
   {: tip}

## Configuring an SQL backup job
{: #configureBackupjobSQLDB}
{: help}

Through the {{site.data.keyword.backup_notm}} portal, you can manage and monitor your backups. You can create a backup job for one or more databases in an SQL Server instance. The backup job specifies which databases to back up, and where to save the backup data. You can also back up a SharePoint 2013 or 2010 database with the SQL Server plug-in. However, an SQL Server backup job cannot include databases from multiple SQL Server instances.

When you create the backup job, you must specify the Windows&reg; administrator or SQL Server administrator credentials that allow the {{site.data.keyword.cloud_notm}} Agent to connect to the instance where the databases reside.

To back up the data, you can run the backup job manually or schedule the job to run. When you schedule or run a job, you can specify whether to back up the database, the transaction logs, or both.

To add an MSSQL database backup job, complete the following tasks.
1. On the navigation bar, click **Computers**. The Computers page shows registered servers.
2. Find a server with the MSSQL plug-in, and expand its view by clicking the computer row.
3. Click the **Jobs** tab.

   If the server doesn't have a valid vault connection, then you can't access the Jobs tab.
   {: note}

4. In the Select Job Task menu, click **Create New SQL Server Job**.
5. In the Connect to SQL Server dialog box, provide the following information.
   - In the Instance list, select the SQL Server instance where you want to back up databases.
   - To connect to the instance by using a Windows&reg; administrator account, select Windows&reg; authentication.
   - To connect to the instance by using an SQL Server administrator account, select SQL authentication.
   - In the User Name box, type the username for connecting to the instance.
   - In the Password box, type the password of the specified user.
   - If you selected Windows&reg; authentication, in the Domain box, type the domain of the specified account.
6. Click **Connect**.
7. In the Create New Job dialog box, specify the following information.
   - In the Name box, type a name for the backup job.
   - In the Description box, optionally type a description for the backup job.
   - In the Destination list, select the vault where you want to save the backup data.

     A vault appears in the list if it is assigned to the user, or if the user added it in the computer’s Vault Settings.
     {: tip}

   - In the Log File Options list, select the level of detail for job logging. For more information, see [Log file options](#SQLDBLogfile).
   - For new backup jobs, the encryption method is AES 256 bit. Existing jobs can have other encryption methods. For more information, see [Encryption settings](#SQLDBEncrypt).
   - In the Password and Confirm Password boxes, enter an encryption password. You can also enter a password hint in the Password Hint box.
8. In the Select Databases for Backup box, select the database that you want to back up.
   - To add specific databases to the backup job, select the checkbox for each database, and then click Include. The included databases appear in the Backup Set box.
   - To back up all databases in the selected SQL Server instance, select the checkbox for the instance, and then click Include. The included instances appear in the Backup Set box.

   When the job runs, newly added databases in the selected instance are automatically backed up.
   {: note}

   - To back up databases with names that match a filter when the job runs, select the checkbox for the SQL Server instance, and then click Include. An inclusion record with an asterisk (`*`) appears in the Backup Set box. In the Database Filter box, enter the names of databases to include. Separate multiple names with commas, and use asterisks (`*`) and question marks (`?`) as wildcard characters. Filters are applied when the backup job runs. New databases that match the specified filters are automatically backed up when the job runs.

   For example, to back up databases with names that end with “Management” or include the word “database” followed by a single character, enter the following filter: `*management, database?`.
   {: tip}

9. To exclude databases from the backup job, do one or more of the following in the Select Databases for Backup box:
   - To exclude specific databases from the backup job, select the checkbox for each database, and then click Exclude. The excluded databases appear in the Backup Set box with a minus sign.
   - To exclude databases with names that match a filter when the backup job runs, select the checkbox for the SQL Server instance, and then click Exclude. A record with an asterisk (`*`) appears in the Backup Set box. In the Database Filter box, enter the names of databases to exclude. Separate multiple names with commas, and use asterisks (`*`) and question marks (`?`) as wildcard characters. For example, to exclude databases if their names begin with “M”, enter the following filter: `m*`.

   Filters are applied when the backup job runs. New databases that match the specified filters are automatically excluded when the backup job runs. Filters are not case-sensitive.
   {: note}

10. To remove an inclusion or exclusion record from the Backup Set box, click Delete next to the record.
11. Click Apply Now to consolidate and simplify records in the Backup Set box, if changes need to be applied.
12. Click Create Job. The job is now created, and the View/Add Schedule dialog box appears. Next, you can create a schedule for running the backup. Click Cancel if you don't want to create a schedule now.


## Scheduling the SQL backup job
{: #SQLDBSchedulejob}

After you created a backup job, you can add one or more schedules for running the job automatically. You can create complex schedules for a job by creating multiple schedules. For example, you can schedule a backup job to run at midnight every Friday, and schedule the job to run at 8 PM on the first day of every month. When you schedule multiple SQL Server database jobs in the same instance, it's good practice to schedule the jobs so that their running times do not overlap. Simultaneous backups are supported, but are not recommended.

If a job is scheduled to start at the same time by multiple schedules, the job runs only once at the scheduled time. If the jobs have different retention types, the retention type of the schedule that is highest in the list is applied to the resulting safe set. For example, the job is scheduled to run at midnight each Saturday with the Weekly retention type, and every day at 12 midnight with the Daily retention type. On Saturdays, the job runs once at 12 midnight. Because the schedule with the Weekly retention type is higher in the list than the schedule with the Daily retention type, the Weekly retention type is applied to the safe set.

If a job is scheduled to run at slightly different times, the {{site.data.keyword.backup_notm}} Agent attempts to run the job according to each schedule. For example, if a job is scheduled to run at 11 PM by one schedule and 11:01 PM by another schedule, the {{site.data.keyword.backup_notm}} agent attempts to run the job twice. Try to avoid overlapping schedules. Problems can occur if a job is scheduled to run twice in a short period. In particular, try to avoid overlapping schedules for SQL Server database jobs in the same instance. Simultaneous backups in the same SQL Server instance are supported, but are not recommended.

1. In the View/Add Schedule dialog box, click **Add Schedule**.
2. In the new schedule row, in the Retention list, click a retention type.
3. Select the Backup Type:
   - To back up each database from the point in time when the backup starts, click **Full**.
   - To back up each database and its transaction logs from the point in time when the backup starts, click **Full with transaction logs**.
   - To back up the database transaction logs only from the point in time when the backup starts, click Transaction logs only. When **Transaction Logs only** is selected, the entire database and its transaction logs are backed up when the job first runs. In subsequent backups, only the transaction logs are backed up.

   After a transaction log backup, logs are marked for truncation. If you also back up databases by using another tool (for example, native SQL Server backup), use only one tool for truncating logs. Transaction logs can be backed up for databases only when they use the full or bulk-logged recovery model.
   {: note}

4. In the Schedule box, click the arrow.
5. In the Configure Job Schedule dialog box, choose one of the following options.
     - To run the backup on specific days each week, in the Schedule View list, click **Days of Week**. Select the days when you want to run the job. Then, use the At field to specify the time when you want to run the job.
     -  To run the backup on specific dates each month, click **Days of Month** in the Schedule View list. On the calendar, select the date when you want to run the job. Then, use the At field to specify the time when you want to run the job.
     - To create a custom schedule, click **Custom** in the Schedule View list. In the Custom Cycle dialog box, enter a custom schedule. Be sure to follow the format and notation as described.
6. Click **Okay**. The schedule appears in the Schedule box.
7. In the Compression list, click a compression level for the backup data. Compression levels optimize the volume of data sent against the speed of processing.
8. For deferring, select one of the following options.
    - To allow the backup job to run without a time limit, click None in the Deferring list.
    - To specify a maximum amount of time that the backup job can run, click **Minutes** or **Hours** in the Deferring list. In the adjacent box, type the maximum number of minutes or hours that the job can run.

    When you use the deferring option, the backup job doesn't back up any new data after the specified amount of time, even if some data is not backed up. Changes to data that was previously backed up are still backed up, regardless of the amount of time specified.
    {: note}

9. To run the job on the specified schedule, select the Enable checkbox near the end of the row.

   If more than one schedule row exists, you can use the Priority arrows to change the order of the schedule rows. Schedules higher in the list have a higher priority than schedules toward the end of the list. If a job is scheduled to run at the same time by multiple schedules, the job runs once at the scheduled time. If the schedules have different retention types, the job runs with the retention type of the schedule that is highest in the priority list.
   {: note}

10. Click **Save**.

## Protecting SQL databases in AlwaysOn Availability Groups
{: #configureBackupAlwaysOn}

You can protect SQL Server databases in AlwaysOn Availability Groups by using the Windows&reg; {{site.data.keyword.backup_notm}} Agent and SQL Server plug-in.
If you back up a database in a secondary replica, a copy-only backup of the database is performed. Copy-only backups do not affect the sequence of conventional SQL Server backups. Microsoft&reg; supports only copy-only backups of secondary databases. For more information, see [offload-supported backups to secondary replicas of an availability group](https://learn.microsoft.com/en-us/sql/database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups){: external}.

If a backup job includes secondary databases and databases that are not in a secondary replica, a copy-only backup is performed for all databases in the job. Do not include a secondary database in the same job as a stand-alone database.
{: note}

To protect SQL Server databases in AlwaysOn Availability Groups, you can choose one from the following options.
- Install the Windows&reg; {{site.data.keyword.backup_notm}} Agent and plug-in on the server where the primary replica is hosted. You can run a full backup of the primary databases, followed by full or transaction log backups. If the primary replica becomes a secondary replica after a failover, the {{site.data.keyword.backup_notm}} Agent automatically runs copy-only database backups instead of full backups. Transaction log backups remain the same.

- Install the Windows&reg; {{site.data.keyword.backup_notm}} Agent and plug-in on a server where a secondary replica is hosted. This backup strategy offloads backup processing to a nonprimary server. You can run a copy-only backup of the secondary database, followed by copy-only or transaction log backups. If the secondary replica becomes the primary replica after a failover, the {{site.data.keyword.backup_notm}} Agent automatically runs full backups instead of copy-only backups. Transaction log backups remain the same.

   If the availability mode of the secondary replica is asynchronous-commit, transaction logs on the secondary database might lag behind the primary replica database. If the secondary database is being backed up, data loss might occur.
   {: note}

- Install the Windows&reg; {{site.data.keyword.backup_notm}} Agent and plug-in on the primary replica server and on secondary replica servers. This strategy ensures that backups continue even if one of the replicas is down. You can run a full backup on the primary replica, followed by full or transaction log backups. You can also run copy-only backups on the secondary replicas, followed by copy-only or transaction log backups.

If an SQL database in an AlwaysOn Availability Group is hosted on an SQL Server Failover Cluster Instance, install the Agent, SQL Server plug-in, and Cluster plug-in on each physical node. Then, configure the jobs on the virtual node. Full backups run if the database is a primary database. Copy-only backups run if the database is a secondary database.
{: tip}

## Protecting SQL Server Clusters
{: #configureBackupSQLCluster}

To protect an SQL Server cluster, you must install the Windows&reg; {{site.data.keyword.backup_notm}} Agent with the Cluster Support plug-in and SQL Server plug-in on each node in the cluster. Then, you can register a virtual server for the SQL Server role in the Portal and create and run backup jobs on the virtual server. Backup jobs on a virtual server are automatically directed to the active cluster node and do not reseed after a failover.

To fully protect an SQL Server cluster, you must back up:
- The quorum disk,
- Each physical node in the cluster,
- Cluster volumes,
- The SQL Server databases to provide point-in-time database recovery.

When a cluster is fully protected, you can recover the cluster if components are lost, are corrupted, or fail.

## Advanced settings
{: #SQLDBBackupAdvanced}

### Log file options
{: #SQLDBLogfile}

When you create or edit a backup job, you can specify the level of detail for job logging. Select one of the following logging levels from the list.
- Files - this setting provides the most detailed information, and is typically used for troubleshooting. It provides information about files that are backed up.
- Directory - This setting provides less detail than the Files logging level. It provides information about folders that are backed up.
- Summary - This setting provides high-level information, including the vault and {{site.data.keyword.backup_notm}} Agent version, and backup sizes.
- Minimal - This setting provides high-level information, including the vault and {{site.data.keyword.backup_notm}} Agent version.

Changing the logging level affects only the log files that are created at that point and after. It does not affect previously created log files.
{: important}

### Encryption settings and password
{: #SQLDBEncrypt}

Encryption settings specify the encryption type for backup data at rest on the vault. AES 256-bit encryption is the default encryption type available for new backup jobs. When you create a backup job, you must enter a password for the encrypted data. The password is case-sensitive. To recover the data, you must provide the encryption password that was entered when the files were backed up.
You can also enter a password hint. When you want to restore data, you can view the password hint to remind you of the encryption password for this job.

If you forget the encryption password, you lose access to the data. You cannot retrieve the password from the system.
{: important}

