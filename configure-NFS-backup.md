---

copyright:
  years: 1994, 2024
lastupdated: "2024-07-26"

keywords: IBM Cloud backup, EVault, Carbonite, backup, configuration, NFS

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Configuring NFS backups
{: #configureNFSBackup}

After you ordered your {{site.data.keyword.backup_full}} and the agent is installed on the server, you can start creating backups of your data. First, add the Linux&reg; client in the Backup Portal. Then, you can create a backup job for files and folders that are saved on the NFS shares that are attached to this server. The backup job specifies which folders and files to back up, and where to save the data.
{: shortdesc}

## Starting Cloud Backup Portal
{: #startPortalconfigNFS}
{: help}
{: support}

You need to be connected to the {{site.data.keyword.cloud}} private network to be able to start the Portal.
{: requirement}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the **menu** ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
4. Click **View backup portal** to start the portal in your browser.

   If the Portal doesn't start, you might have a problem with your VPN connection. You might also see a message that says that the form you’re sending isn’t secure. It is expected - proceed by sending the form.
   {: tip}

## Configuring an NFS backup job
{: #configureNFSBackupjob}
{: help}
{: support}

1. In the navigation, click **Computers**, then the expansion arrow to display the information of the selected Linux server.
1. Click the **Jobs** tab.
   If a valid vault connection is not available for the computer, you cannot access the Jobs tab.
   {: note}
   
1. From the Select Job Task menu, select **Create New NFS Files Job**.
    1. In the new window, enter a **Name** and a **Description**.
    1. In the **Destination** list, select the vault where you want to save the backup data. A vault appears in the list only if it is assigned to the user, or if the user added it on the computer’s Vault Settings.
    1. In the **Log File Options** list, select the level of detail for job logging.
    1. Enter the encryption password into the Password and Confirm Password fields. You can also add a Password Hint.

        You need this password to restore files from the backup. Without the password, you can't restore an encrypted backup. The lost password cannot be recovered in any way.
        {: important}

1. In the **Select Files and Folders for Backup** box, create the backup set by doing one or more of the following tasks.
   - To add one or more folders or files to the backup job, select the checkbox for each folder or file, and then click **Include**. The included folders or files appear in the Backup Set box. If you include a folder, the backup job includes all of the folder’s subdirectories and files by default. If you don't want to back up all of the subdirectories and files, you can add filters.
   - To exclude one or more folders or files from the backup job, select the checkbox for each folder or file, and then click **Exclude**. The excluded folders or files appear in the Backup Set box. If you exclude a folder, all of the folder’s subdirectories and files are excluded from the backup job by default. If you don't want to exclude all of the subdirectories and files, you can add filters.
   - To remove an inclusion or exclusion record from the Backup Set box, click **Delete** next to the folder or file record.
1. Click **Apply now** to confirm the backup set.
1. Click **Create Job**.
1. {{site.data.keyword.backup_notm}} offers three job retention schemes: Daily, Weekly, Monthly. In the new schedule window, select the appropriate retention period and click **Save**.

    Multiple retention schedules can be set up for same job but it’s important that they are NOT run at the same time. For more information about Retention Schemes, see the [FAQ](/docs/Backup?topic=Backup-faqs#faqs).
    {: important}

## Running a backup job
{: #runNFSBackupjob}
{: help}
{: support}

1. The new job is displayed on the Computers tab. To start the job, click **Select Actions** and click **Run Job**.
2. Verify that the destination and retention scheme appear correctly and click **Start Backup**. The Progress Detail page shows the job progress. This window can be closed if needed, and the backup job keeps running in the background.
3. When the backup job is complete, the Process ID Status shows "Finished". You can view the job history and logs of existing backup jobs on the Computer tab. Select the job that you want to view, click **Select Action**, and choose **History/Logs**.
