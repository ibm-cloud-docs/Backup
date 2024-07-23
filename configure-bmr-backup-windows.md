---

copyright:
  years: 1994, 2024
lastupdated: "2024-07-23"

keywords: IBM Cloud backup, EVault, Carbonite, backup, configure BMR, bmr plug-in, bmr plugin, configuration

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Configuring BMR backup job
{: #configureBMR}

You need to purchase the BMR plug-in to create a BMR backup. BMR is available only for Windows Bare Metal Servers. No BMR option is available for VSI. For more information, see [Getting started with the Bare Metal Restore plug-in](/docs/Backup?topic=Backup-BMRplugin#BMRplugin).
{: important}

## Starting Cloud Backup Portal
{: #startPortalBMR}

You need to be connected to the {{site.data.keyword.cloud}} private network to be able to start the Portal.
{: requirement}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
4. Click **View backup portal** to start the portal in your browser.

   If the Portal doesn't start, you might have a problem with your VPN connection. You might also see a message that says that the form you’re sending isn’t secure. It is expected - proceed by sending the form.
   {: tip}

## Configuring a BMR backup job
{: #configBRMjob}

1. In the navigation, click **Computers**, then the expansion arrow to display the information of the selected server.
2. Click **Configure Manually**. The vault settings page is loaded.
3. Click **Add Vault**.
4. Expand the Vault Profile menu and select the vault. All values auto-populate.
5. Click **Save**.
6. Click the **Jobs** tab.
7. From the Select Job Task menu, select **Create Bare Metal Restore Job**.
8. In the Create New Job window, enter a Job Name and a Job Description.
9. Select the files and folders that you want to include in the backup.
10. Enter the encryption password into the Password and Confirm Password fields. You can also add a Password Hint.
   You need this password to restore files from the backup. Without the password, you can't restore an encrypted backup. The lost password cannot be recovered in any way.
   {: important}

11. Click **Apply now** to confirm the backup set.
12. You can leave the Advanced Backup Options with their default settings. If you want detailed log files for the backup job, you can enable them by expanding the *Log Detail Level* menu and selecting **File**.
13. Click **Create Job**.
14. {{site.data.keyword.backup_notm}} offers three job retention schemes: Daily, Weekly, Monthly. In the new window, select the appropriate retention period and click **Save**.

   For more information about Retention Schemes, see the [FAQ](/docs/Backup?topic=Backup-faqs#faqs).
   {: tip}

## Running a BMR backup job
{: #runningBMRjob}

- If you scheduled a time-based backup job, you don't need to do anything else. Your job runs automatically as scheduled.
- If you set up a manual job (without a time-based schedule), you can run it by selecting its row in the job list and click **Run backup**.
   As with time-based jobs, you can choose the **Retention Scheme** and the **Advanced backup options**. After you made your configuration choices, click **Start backup** to start the job.
