---

copyright:
  years: 1994, 2023
lastupdated: "2023-08-31"

keywords: IBM Cloud backup, EVault, Carbonite, backup, restore

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Restoring data from one VSI to another in a different Data Center
{: #restoreVSIotherlocation}

Sometimes you want to restore data to a different server. This procedure applies to file-level restores of non-OS files only. To restore a system image, follow the [Windows&reg; BMR](/docs/Backup?topic=Backup-restoreBMR) instructions.
{: shortdesc}

The process includes reregistering the backup agent on the second server to access the vault location of the first server and completing a **Restore from another Computer**.

## Pre-requisites
{: #prereqsrestore2}

- Server 1 and Server 2 must have the same Operating System. Cross-platform restores aren't supported.
- Server 1 and Server 2 must have backup agents that were configured previously. For more information about configuring the backup agents, see [Configuring the Backup agent in Cloud Backup Portal](/docs/Backup?topic=Backup-getting-started#getting-started).
- A backup job for Server 1 that produced a backup to Server 1's vault location.

Disable all Scheduled tasks on both servers to avoid any conflicts.
{: important}

## Starting Cloud Backup Portal of Server 2
{: #startPortalotherDC}

Remember to start your [{{site.data.keyword.BluVPN}}](/docs/iaas-vpn?topic=iaas-vpn-getting-started){: external} connection to get access to the {{site.data.keyword.cloud}} private network or the Cloud Backup Portal link doesn't work.
{: tip}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
4. Click **View backup portal** to start the portal in your browser.

If current backup jobs are registered for Server 2, they must be removed. You can delete existing jobs on the Computers > Jobs page by selecting the **Delete Job** action. Then, you're prompted to confirm the deletion. Type **CONFIRM** and click **Confirm Deletion**.

 Deleting a job in the Portal doesn't delete the job from the Backup Vaults. Jobs can be recovered by reregistering the agent to its own vault location after the files are recovered from another computer.
 {: note}

 If a current backup vault is registered to Server 2, it can be deleted on the **Computers** > **Vault Settings** screen by selecting **Remove** from the Action menu.

## Reregistering the vault
{: #reregistervaultotherDC}

1. When the Vault Settings screen is blank, click **Re-register**. On the next screen, for the **Use a Vault Profile** entry, select **Enter Vault Settings**.
2. Enter the Vault Name, which is the same as the vault name of Server 1.
3. Enter credentials for Server 1 to log in to the vault for Server 1.
4. Click **Load Computers**, this action displays the servers that are attached to the vault location.
5. Click **Save**.
6. When prompted, click **Yes** to confirm the reregistration of the vault.

## Running the backup job from Server 1 as the restore job on Server 2
{: #runbackuprestoreotherDC}

1. Click **Jobs**.

   You might need to refresh the page to see the jobs that are defined on Server 1 as accessible and synchronized on the Server 2 **Jobs** screen.
   {: tip}

2. From the Action menu, select **Restore**.
3. Enter the encryption password.
4. The Restore window appears. By default, it displays the most recent safe set. To choose a different date, click the Calendar icon, and view other safe sets.
5. Select the files and directories that you want to include. Then, click **Include** to save your choices.

    Default restore options place the files in their original location. If files exist in the destination folder with the same name, the incoming file is renamed. These options can be changed and an alternative restore location can be selected from Restore Destination options.
    {: note}

6. When your restore set is configured the way that you want it, click **Apply Now**.
7. Then, click **Run Restore**.
8. The files are restored when the Status displays **Restore completed** on the **Process Details** screen. Click **Close** to close the window and return to the main Cloud Backup Portal screen.

## Verifying the restore
{: #verifyrestoreotherDC}

1. Connect to the root of Server 2 through ssh.
2. List the files and all directory entries in a long format.
    ```sh
    ls -la
    ```
    {: pre}

3. Compare the output.

## Resuming normal backup schedule.
{: #resumescheduleotherCD}

1. When the restore is complete, remove the registration information of server1, where the data was restored from.
2. Enter the current server2 registration and enable Schedule tasks.
