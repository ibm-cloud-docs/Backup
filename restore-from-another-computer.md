---

copyright:
  years: 1994, 2019
lastupdated: "2019-11-14"

keywords: IBM Cloud backup,  EVault, Carbonite, backup, restore

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
{:term: .term}

# Restoring data from one server to another
{: #restorefromotherVSI}

Sometimes you might want to restore data to a different server in the same data center. This procedure applies to file-level restores of non-OS files only. To restore a system image, follow the [Windows BMR](/docs/infrastructure/Backup?topic=Backup-restoreBMR) instructions.
{:shortdesc}

The process includes reregistering the backup agent on the second server to access the vault location of the first server and completing a **Restore from another Computer**.

**Pre-requisites**

- Server1 and Server2 must have the same Operating System. Cross-platform restores aren't supported.
- Server1 and Server2 must have backup agents that were configured previously. For more information about configuring the backup agents, see [Configuring the backup agent in Cloud Backup Portal](/docs/infrastructure/Backup?topic=Backup-getting-started#getting-started).
- A backup job for Server1 that produced a backup to Server1's vault location.

Disable all Scheduled tasks on both servers to avoid any conflicts.
{:important}

## Starting Cloud Backup Portal of Server2
{: #startPortal}

Remember to start your {{site.data.keyword.BluVPN}} connection to get access to the {{site.data.keyword.cloud}} private network or the Cloud Backup Portal link doesn't work.
{:tip}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Select Server2. Click the expansion arrow to reveal the WebCC link.
4. Click **WebCC Login** to start the portal client in your browser.


## Editing the vault information
{: #changhingvault}

1. Click **Computers**, and click the server name to display its information.
2. Click **Vault Settings** and from the Action menu, select **Edit**.
2. Enter the Vault Name, which is the same as the unique vault name of Server1.
3. Enter credentials for Server1 to log in to the vault for Server1.
4. Click **Save**.

## Running the backup job from Server1 as the restore job on Server2
{: #runbackuprestore}

1. On the **Computer** tab, click **Jobs**.

   You might need to refresh the page to see the jobs that are defined on Server1 as accessible and synchronized under the Server2 **Jobs** tab.
   {:tip}
2. From the Action menu, select **Restore from Another Computer**.
3. Select the Vault, Computer, and Job from the drop-down menus.
3. Enter the encryption password.
4. The Restore window appears. By default, it displays the most recent safeset. To choose a different date, click the Calendar icon, and view other safesets.
9. Select the files and directories that you want to include. Then, click **Include** to save your choices.

   Default restore options place the files in their original location. If files exist in the destination folder with the same name, the incoming file is renamed. These options can be changed and alternate restore location can be selected from Restore Destination options.
   {:note}
10. When your restore set is configured the way that you want it, click **Apply Now**.
12. Then, click **Run Restore**.
13. The files are restored when the Status displays **Restore completed** on the **Process Details** screen. Click **Close** to close the window and return to the main Cloud Backup Portal screen.


## Verifying the restore
{: #verifyrestore}

1. Connect to the root of Server2 through [ssh](#x3574365){:term}.
2. List the files and all directory entries in a long format.
  ```
  ls -la
  ```
  {: pre}

3. Compare the output.

## Resuming normal backup schedule.
{: #resumeschedule}

1. When the restore is complete, remove the registration information of server1, where the data was restored from.
2. Enter the current server2 registration and enable Schedule tasks.
