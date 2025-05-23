---

copyright:
  years: 2019, 2025
lastupdated: "2025-03-11"

keywords: IBM Cloud backup, oracle, plug-in, plugin, EVault, Carbonite

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Getting started with the Oracle plug-in
{: #Oracleplugin}

The Oracle plug-in is an add-on that you can install with the Backup Agent on the Oracle Database host. Through the Cloud Backup Portal, you can configure jobs, back up Oracle Databases to a secure, remote vault, and restore Oracle Databases. The Oracle plug-in integrates into the existing architecture.
{: shortdesc}

## Capabilities provided
{: #Oraclecapabilities}

- Support for Oracle Database backup and recovery.
- The Oracle plug-in provides ARCHIVELOG-based, non-RMAN backups of whole online database instances. All nontemporary table spaces and instance parameter files are automatically backed up. Oracle Corporation recommends that backups take place in periods of low database activity.
- Full and partial databases are restored through normal user-managed Oracle recovery mechanisms.

## Limitations
{: #Oraclelimitations}

- Only local, single-instance, disk-based databases are backed up.
- Database clusters are not backed up.
- Raw devices are not backed up.
- Remote databases are not backed up.
- The database must run in ARCHIVELOG mode, and the user under which the backup is configured must have SYSDBA privileges.
- Database passwords are encrypted for enhanced security over script-based methods.

## Installing the plug-in for Windows
{: #installOracleWin}

The Oracle plug-in is installed with the 32-bit or 64-bit Windows Agent. To install the plug-in, run the Agent installation kit with the **Modify** selection. The plug-in appears as an option on the **Custom setup** page. For more information, see [Installing the {{site.data.keyword.backup_notm}} Client in Windows](/docs/Backup?topic=Backup-InstallinWindows).

Before you install the plug-in, stop both {{site.data.keyword.backup_notm}} services in `services.msc`.
{: tip}

When the installation is complete, check to make sure that both services are enabled and running. If Cloud Backup Portal is able to view and access the database, then the installation was successful.

## Installing the plug-in for Linux
{: #installOracleLin}

The Oracle plug-in is an add-on to the Linux&reg; Agent and is installed with the Agent on the database host. The Linux&reg; Agent application must be installed before the plug-in installation occurs. The agent is available as a 32-bit application and a 64-bit application. For more information, see [Installing the {{site.data.keyword.backup_notm}} Client in Linux&reg;](/docs/Backup?topic=Backup-InstallinLinux).

The Oracle plug-in installation kit is available in a tar.gz file.

1. On the host, download the installation package.
   ```sh
   http://downloads.softlayer.com/evault/Oracle-Plugin-Linux-x64-8.10.5249.tar.gz
   ```
   {: pre}

2. Extract the files from the package.
   ```sh
   # cd /tmp
   # tar xvf Oracle-Plugin-Linux-x64-8.10.5249.tar
   ```
   {: pre}

3. Go to the folder.
   ```sh
   # cd Oracle-Plugin-Linux-x64-8.10.5249.xxxx
   ```
   {: pre}

4. Run the installation script.
   ```sh
   # ./install.sh
   ```
   {: pre}

5. Follow the installation instructions on the screen.

The Oracle plug-in performs an "inconsistent" whole database backup. It requires that the database runs in ARCHIVELOG mode. The DBA needs to make sure that the database is in ARCHIVELOG mode before the backups are started.
{: important}

## Configuring an Oracle DB backup job
{: #configODBbackup}

For more information, see [Configuring Oracle DB backups](/docs/Backup?topic=Backup-configureOracleBackup).

## Restoring an Oracle DB
{: #restoringODBbackup}

For more information, see [Restoring Oracle DB](/docs/Backup?topic=Backup-restoreOracleDB).
