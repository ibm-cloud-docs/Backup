---

copyright:
  years: 1994, 2024
lastupdated: "2024-07-23"

keywords: IBM Cloud backup, EVault, Carbonite, backup, configuration,

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Configuring simple file-level backups
{: #configureFileBackup}

After you ordered your {{site.data.keyword.backup_full}} and the agent is installed on the server, you can start creating backups of your data. The article provides the steps to configure your agent, retention schedule and start your first backup job.

## Starting Cloud Backup Portal
{: #startPortalconfigLin}
{: help}
{: support}

You need to be connected to the {{site.data.keyword.cloud}} private network to be able to start the Portal.
{: requirement}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
4. Click **View backup portal** to start the portal in your browser.

   If the Portal doesn't start, you might have a problem with your VPN connection. You might also see a message that says that the form you’re sending isn’t secure. It is expected - proceed by sending the form.
   {: tip}

## Configuring a backup job
{: #configureBackupjob}
{: help}
{: support}

Through the {{site.data.keyword.backup_notm}} portal, you can manage and monitor your backups. You can choose between manual or automatic backup agent configuration methods.

- The automatic agent configuration creates a backup job of the complete C Drive (Windows&reg; OS) or `./<root>` directory (Linux&reg; OS) with Monthly and Daily Retention schemes.

    This job can be modified after it was configured.
    {: note}

    1. Create a password.
    2. Confirm the password.
    3. Add a password hint.
    4. Click **Configure automatically**.

- If you choose to configure the {{site.data.keyword.backup_notm}} agent manually, the automatic settings are ignored. Then, you can specify the folders and files to be retained with a retention scheme of your choice.

    1. In the navigation, click **Computers**, then the expansion arrow to display the information of the selected server.
    2. Click **Configure Manually**. The vault settings page loads.
    3. Click **Add Vault**.
    4. Expand the Vault Profile menu, and select the vault. All values auto-populate.
    5. Click **Save**.
    6. Click the **Jobs** tab.
    7. From the Select Job Task menu, select **Create New Local System Job**.
    8. In the Create New Job window, enter a Job Name and a Job Description.
    9. Select the files and folders that you want to include and exclude in the backup. To exclude files, you must add an exclusion record. Select the directory that contains the file that you want to exclude and click **Exclude**. This action adds the file to the Backup Set with a red minus sign. From here, you can filter out a directory or specific file name from that directory that you want skipped during backup.
    10. Enter the encryption password into the Password and Confirm Password fields. You can also add a Password Hint.

        You need this password to restore files from the backup. Without the password, you can't restore an encrypted backup. The lost password cannot be recovered in any way.
        {: important}

    11. Click **Apply now** to confirm the backup set.
    12. You can leave the Advanced Backup Options with their default settings. If you want detailed log files for the backup job, you can enable them by expanding the *Log Detail Level* menu and selecting **File**.
    13. Click **Create Job**.
    14. {{site.data.keyword.backup_notm}} offers three job retention schemes: Daily, Weekly, Monthly. In the new schedule window, select the appropriate retention period and click **Save**.

    Multiple retention schedules can be set up for same job but it’s important that they are NOT run at the same time. For more information about Retention Schemes, see the [FAQ](/docs/Backup?topic=Backup-faqs#faqs).
    {: important}

## Running a backup job
{: #runBackupjob}
{: help}
{: support}

1. The new job is displayed on the Computers tab. To start the job, click **Select Actions** and click **Run Job**.
2. Verify that the destination and retention scheme appear correctly and click **Start Backup**. The Progress Detail page shows the job progress. This window can be closed if needed, and the backup job keeps running in the background.
3. When the backup job is complete, the Process ID Status shows "Finished". You can view the job history and logs of existing backup jobs on the Computer tab. Select the job that you want to view, click **Select Action**, and choose **History/Logs**.
