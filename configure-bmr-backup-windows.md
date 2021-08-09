---

copyright:
  years: 1994, 2021
lastupdated: "2021-07-28"

keywords: IBM Cloud backup, EVault, Carbonite, backup, configure BMR, bmr plug-in, bmr plugin, configuration

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:term: .term}

# Configuring BMR backup job
{: #configureBMR}

You need to purchase the BMR plug-in to create a BMR backup. BMR is available only for Windows&reg; Bare Metal Servers. No BMR option is available for VSI. For more information, see [Learn about the Bare Metal Restore plug-in](/docs/Backup?topic=Backup-BMRplugin#BMRplugin).
{: important}

## Starting Cloud Backup Portal
{: #startPortalBMR}

You need to be connected to the {{site.data.keyword.cloud}} private network to be able to start the Portal.
{: important}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
3. Click **Storage** > **Cloud Backup** to display the backup services.
4. Select the instance name of the {{site.data.keyword.cloud_notm}} account.
5. Click **View backup portal** to start the portal in your browser.

   If the Portal doesn't start, you might have a problem with your VPN connection. You might also see a message that says that the form you’re sending isn’t secure. It is expected - proceed by sending the form.
   {: tip}

## Configuring a BMR backup job

1. In the navigation, click **Computers**, then the expansion arrow to display the information of the selected server.
2. Click **Configure Manually**. The vault settings page is loaded.
3. Click **Add Vault**.
4. Expand the Vault Profile menu and select the vault. All values auto-populate.
5. Click **Save**.
6. Click the **Jobs** tab.
7. From the Select Job Task menu, select **Create Bare Metal Restore Job**.
8. In the Create New Job window, enter a Job Name and a Job Description.
9. Select the files and folders you want to include in the backup.
10. Enter the encryption password into the Password and Confirm Password fields. You can also add a Password Hint.

  You need this password to restore files from the backup. Without the password, you can't restore an encrypted backup and there's no way to recover a lost password.
  {: important}
11. Click **Apply now** to confirm the backup sets.
12. You can leave the Advanced Backup Options with their default settings. If you want detailed log files for the backup job, you can enable them by expanding the *Log Detail Level* menu and selecting **File**.
13. Click **Create Job**. The View/Add Schedule window is loaded.
14. {{site.data.keyword.backup_notm}} offers 3 job retention schemes: Daily, Weekly, Monthly. Select the appropriate retention period and click **Save**.

   For more information about Retention Schemes, see the [FAQ](/docs/Backup?topic=Backup-faqs#faqs).
   {: tip}


## Running a BMR backup job

  - If you scheduled a time-based backup job, you don't need to do anything else. Your job runs automatically as scheduled.
  - If you set up a manual job (without a time-based schedule), you can run it by selecting its row in the job list and click **Run backup**. <br/> As with time-based jobs, you can choose the **Retention Scheme** and the **Advanced backup options**. After you made your configuration choices, click **Start backup** to start the job.
