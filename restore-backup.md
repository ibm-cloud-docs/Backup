---

copyright:
  years: 1994, 2021
lastupdated: "2021-07-28"

keywords: IBM Cloud backup, EVault, Carbonite, backup, restore

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}

# Restoring data from a backup
{: #simplerestore}

Use these steps to complete a File restore with {{site.data.keyword.backup_full}}. To restore a system image, follow the [Windows&reg; BMR](/docs/Backup?topic=Backup-restoreBMR#restoreBMR) instructions.
{: shortdesc}

## Starting Cloud Backup Portal
{: #startPortalsimple}

Remember to start your [{{site.data.keyword.BluVPN}}](https://www.ibm.com/cloud/vpn-access){: external} connection to get access to the {{site.data.keyword.cloud}} private network. The Cloud Backup Portal link doesn't work otherwise.
{: important}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} account.
4. Click **View backup portal** to start the portal in your browser.

## Restoring your data

1. On the navigation, click **Computers**. The computers page shows the registered computers and environments. Expand the server that you want to restore to a previous state.
2. Click **Jobs** to load the job options.
3. Click **Select job Task** and select **Restore*.
4. Confirm the vault, computer, and job information and click **Okay**.
5. Enter the encryption password of the previous backup.
6. The Restore Options window appears. By default, it displays the most recent safeset. To choose a different date, click the Calendar icon and view other safesets.
9. Select the files and directories that you want to include. Then, click **Include** to save your choices.

    Default restore options place the files in their original location. If files exist in the destination folder with the same name, the incoming file is renamed. These options can be changed and alternate restore location can be selected from Restore Destination options.
    {: note}

10. When your restore set is configured the way that you want it, click **Apply Now**.
12. Then, click **Run Restore**.
13. The files are restored when the Status displays **Restore completed** on the **Process Details** screen.
