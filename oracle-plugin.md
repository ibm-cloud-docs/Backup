---

copyright:
  years: 1994, 2019
lastupdated: "2019-11-14"

keywords: IBM Cloud backup, oracle, plug-in, plugin, EVault, Carbonite

subcollection: Backup

---
{:pre: .pre}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}

# Learn about the Oracle plug-in
{: #Oracleplugin}

The Oracle plug-in is an add-on and is installed with the Backup Agent on the Oracle database host. Through the Cloud Backup Portal, you can configure jobs, back up Oracle databases to a secure, remote vault, and restore Oracle databases. The Oracle plug-in integrates into the existing architecture.
{:shortdesc}

## Capabilities provided
{: #Oraclecapabilities}

- Support for Oracle database backup and recovery.
- The Oracle plug-in provides ARCHIVELOG-based, non-RMAN backups of whole online database instances. All non-temporary table spaces and instance parameter files are automatically backed up. Oracle Corporation recommends that backups take place in periods of low database activity.
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

The Oracle plug-in is installed with the 32-bit or 64-bit Windows Agent. To install the plug-in, run the Agent installation kit. The plug-in appears as an option on the **Custom Setup** page. For more information, see  [Installing the {{site.data.keyword.backup_notm}} Client in Windows](/docs/infrastructure/Backup?topic=Backup-InstallinWindows)

Before you install the plug-in, stop both {{site.data.keyword.backup_notm}} services in `services.msc`.
{:tip}

1. Run the Agent installation package.
2. At the language screen, click **OK**
3. At the welcome screen, click **Next**
4. Select the **Modify installation**, and click **Next**.
5. Select the **Leave Unchanged**, and click **Next**.
6. At the custom setup screen, select each plug-in that you purchased, and select **This feature will be installed on ...**, then click **Next**.
7. Select **Keep my current registration**, and click **Next**.
8. Click **Install**.
9. When the installation is complete, check to ensure that both services are enabled and running.
10. If Cloud Backup Portal is able to access or view the database, then the installation was successful.

## Installing the plug-in for Linux
{: #installOracleLin}

The Oracle plug-in is an add-on to the Linux Agent and is installed with the Agent on the database host. The Linux Agent application must be installed before the plug-in installation occurs. The agent is available as a 32-bit application and a 64-bit application. For more information, see [Installing the {{site.data.keyword.backup_notm}} Client in Linux](/docs/infrastructure/Backup?topic=Backup-InstallinLinux).

The Oracle plug-in installation kit is available in a tar.gz file.

1. On the host, download the installation package.
   ```
   http://downloads.softlayer.com/evault/Oracle-Plugin-Linux-x64-8.10.5249.tar.gz
   ```
   {: pre}

2. Extract the files from the package.
   ```
   # cd /tmp
   # tar xvf Oracle-Plugin-Linux-x64-8.10.5249.tar
   ```
   {: pre}

3. Go to the folder.
   ```
   # cd Oracle-Plugin-Linux-x64-8.10.5249.xxxx
   ```
   {: pre}

4. Run the installation script.
   ```
   # ./install.sh
   ```
   {: pre}

5. Follow the installation instructions on the screen.

The Oracle plug-in performs an "inconsistent" whole database backup that requires that the database runs in ARCHIVELOG mode. The DBA needs to ensure that the database is in ARCHIVELOG mode before the backups are started. For more information, see the User Guide.
{:important}


## Downloading the user guide
{: #OracleUserGuide}

Connect to the {{site.data.keyword.cloud}} network with {{site.data.keyword.BluVPN}} so that you can download the user guides from the [Downloadable {{site.data.keyword.backup_notm}} Documentation](http://downloads.service.softlayer.com/evault/Documentation/){: external}
