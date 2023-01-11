---

copyright:
  years: 2019, 2023
lastupdated: "2023-01-11"

keywords: IBM Cloud backup, mssql, sql database, plug-in, plugin, EVault, Carbonite, restore SQL

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Learn about the SQL Server plug-in
{: #MSSQLplugin}

The SQL Server plug-in is installed with the Windows&reg; Agent on the SQL database host. Through the Cloud Backup Portal, you can configure jobs, back up SQL databases to a secure, remote vault, and restore SQL databases.
{: shortdesc}

## Capabilities provided
{: #sqlcapabilities}

- You can run full database backups, full database with transaction logs backups, or transaction logs only backup.
- You can run multiple backups at the same time.
- You can restore SQL databases to the same SQL instance or to a different SQL instance,
- You can restore databases with the original database names, overwrite existing databases, and restore by using the No Recovery option.

## Main features
{: #main-features}

- Ability to specify the names of databases to include and exclude in SQL Server backup jobs by using wildcard characters (asterisks and question marks). New databases with names that match a backup job's filters are automatically included or excluded when the job runs.
- Ability to protect secondary databases in AlwaysOn Availability Groups by using the 64-bit Agent and SQL Server plug-in.
- Ability to share SQL safe-sets that contain SharePoint 2010/2013 content databases for use with the Granular Restore for Microsoft&reg; SharePoint application. After the safe-set is shared, the Granular Restore application can be used to restore site collections, websites, lists, libraries, folders, list items, or documents.
- Support for Delta-friendly backup of databases that are on spanned volumes.
- Ability to protect databases in full recovery model with a single schedule entry. This option allows protecting databases and managing truncation of transaction logs in a single schedule entry.
- The SQL Server plug-in supports Full, Full with Include Transaction Logs, and Transaction Log backups (updated terminology to align with SQL Server terminology). The application continues to support the Single Pass Restore function that allows the customer to select a point in time “transaction log” backup. {{site.data.keyword.backup_notm}} restores the full database and all transaction logs necessary to restore the database to the selected point in time.
- A backup job can contain one or more databases from the same single SQL Server instance. A separate Job can be created to back up other databases from a different SQL Server instance, which can be run simultaneously if wanted.
- Ability to restore databases with "No Recovery" to provide more recovery options through the SQL Server Management Studio.
- Alternate restore option supports restore to files, which allows the database administrator to mount the databases through the SQL System Manager.
- Alternate restore includes the ability to direct the restore of one database into another even when the logical database names are not matching. For mismatched objects, the plug-in creates databases in the default database location for the instance.
- Support for Transparent Data Encryption (TDE) with 64-bit SQL Server 2008 R2 (SP1) and SQL Server 2012.
- If an SQL Server host is lost, the SQL Server software can be installed, and the database can be restored. (The Master database must be restored first.)
- When the backup starts, the backup occurs with or without running database services.
- Restores are supported to original database names (with or without overwrite existing databases), restore over an existing database, or to files on disk.

## Installing the MSSQL plug-in
{: #installSQLPlugin}

To install the plug-in, run the Agent installation kit. The plug-in appears as an option on the **Custom Setup** page.

Before you install the MSSQL plug-in for your Microsoft&reg; Windows&reg; server, stop both {{site.data.keyword.backup_notm}} services in `services.msc`.
Review the Release Notes to ensure that the Backup agent version is compatible with the SQL version of your database.
{: tip}

1. Run the Agent installation package.
2. At the language screen, click **OK**.
3. At the welcome screen, click **Next**.
4. Select the **Modify installation**, and click **Next**.
5. Select the **Leave Unchanged**, and click **Next**.
6. At the custom setup screen, select each plug-in that you purchased.
7. Select **This feature will be installed on ...**, then click **Next**.
8. Select **Keep my current registration** and click **Next**.
9. Click **Install**.
10. When installed, check to ensure that both services are enabled and running.
11. If Cloud Backup Portal is able to view and access the database, then the installation was successful.


## Configuring an MSSQL DB backup job
{: #configSQLDBbackup}

The SQL Server plug-in can back up databases that span volumes, databases that have Transparent Data Encryption (TDE) enabled and databases in AlwaysOn Availability Groups. The plug-in can also back up BLOB data from filestream-enabled databases. You can run full database backups, full database with transaction logs backups or transaction log only backups. When it is installed with the Cluster Support plug-in, the SQL Server plug-in can protect databases on SQL Server clusters. For more information, see [Configuring MSSQL database backups](/docs/Backup?topic=Backup-configureMSSQLBackup).

## Restoring an MSSQL DB
{: #restoringSQLDBBbackup}

After you backed up the SQL Server databases by using the SQL Server plug-in, you can restore databases directly to an SQL Server instance, or restore databases to flat files. When you want to restore an SQL Server database in an Always On Availability Group, you must always restore the database to the primary replica.
For more information, see [Restoring MSSQL Database](/docs/Backup?topic=Backup-restoreMSSQLDB).

Connect to the {{site.data.keyword.cloud}} network with [{{site.data.keyword.BluVPN}}](https://www.ibm.com/cloud/vpn-access){: external} so that you can download the user guides in PDF format from the [Downloadable {{site.data.keyword.backup_notm}} Documentation](http://downloads.service.softlayer.com/evault/Documentation/){: external}.
{: tip}
