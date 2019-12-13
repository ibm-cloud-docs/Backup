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

# Restoring data from one VSI to another in a different Data Center
{: #restoreVSIotherlocation}

Sometimes you want to restore data to a different server. This procedure applies to file-level restores of non-OS files only. To restore a system image, follow the [Windows BMR](/docs/infrastructure/Backup?topic=Backup-restoreBMR) instructions.
{:shortdesc}

The process includes reregistering the backup agent on the second server to access the vault location of the first server and completing a **Restore from another Computer**.

**Pre-requisites**

- Server1 and Server2 must have the same Operating System. Cross-platform restores aren't supported.
- Server1 and Server2 must have backup agents that were configured previously. For more information about configuring the backup agents, see [Configuring the Backup agent in Cloud Backup Portal](/docs/infrastructure/Backup?topic=Backup-getting-started#getting-started).
- A backup job for Server1 that produced a backup to Server1's vault location.

Disable all Scheduled tasks on both servers to avoid any conflicts.
{:important}

## Starting Cloud Backup Portal of Server2
{: #startPortalotherDC}

Remember to start your {{site.data.keyword.BluVPN}} connection to get access to the {{site.data.keyword.cloud}} private network or the Cloud Backup Portal link doesn't work.
{:tip}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Select Server2. Click the expansion arrow to reveal the WebCC link.
4. Click **WebCC** to start the Portal in your browser.

If current backup jobs are registered for Server2, they must be removed. You can delete existing jobs on the Computers > Jobs page by simply selecting the **Delete Job** action. Then, you're prompted to confirm the deletion. Type **CONFIRM** and click **Confirm Deletion**.

 Deleting a job in the Portal doesn't delete the job from the Backup Vaults. Jobs can be recovered by reregistering the agent to its own vault location after the files are recovered from another computer.
 {:note}

 If a current backup vault is registered to Server2, it can be deleted on the **Computers** > **Vault Settings** tab by selecting **Remove** from the Action menu.

## Reregistering the vault
{: #reregistervaultotherDC}

1. When the Vault Settings tab is blank, click **Re-register**. On the next screen, for the **Use a Vault Profile** entry, select **Enter Vault Settings**.
2. Enter the Vault Name, which is the same as the vault name of Server1.
3. Enter credentials for Server1 to log in to the vault for Server1.
4. Click **Load Computers**, this action displays the servers that are attached to the vault location.
5. Click **Save**.
6. When prompted, click **Yes** to confirm the reregistration of the vault.

## Running the backup job from Server1 as the restore job on Server2
{: #runbackuprestoreotherDC}

1. Click **Jobs**.

   You might need to refresh the page to see the jobs that are defined on Server1 as accessible and synchronized under the Server2 **Jobs** tab.
   {:tip}
2. From the Action menu, select **Restore**.
3. Enter the encryption password.
4. The Restore window appears. By default, it displays the most recent safeset. To choose a different date, click the Calendar icon, and view other safesets.
9. Select the files and directories that you want to include. Then, click **Include** to save your choices.

   Default restore options place the files in their original location. If files exist in the destination folder with the same name, the incoming file is renamed. These options can be changed and alternate restore location can be selected from Restore Destination options.
   {:note}
10. When your restore set is configured the way that you want it, click **Apply Now**.
12. Then, click **Run Restore**.
13. The files are restored when the Status displays **Restore completed** on the **Process Details** screen. Click **Close** to close the window and return to the main Cloud Backup Portal screen.

## Verifying the restore
{: #verifyrestoreotherDC}

1. Connect to the root of Server2 through ssh.
2. List the files and all directory entries in a long format.
  ```
  ls -la
  ```
  {: pre}

3. Compare the output.

## Resuming normal backup schedule.
{: #resumescheduleotherCD}

1. When the restore is complete, remove the registration information of server1, where the data was restored from.
2. Enter the current server2 registration and enable Schedule tasks.
