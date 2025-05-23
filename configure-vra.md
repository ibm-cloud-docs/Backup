---

copyright:
  years: 1994, 2025
lastupdated: "2025-03-11"

keywords: IBM Cloud Backup, VMware, VRA, vSphere Recovery Agent, plug-in, plugin, EVault, Carbonite, vSphere

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Configuring VRA backup jobs
{: #ConfigureVRA}

After the VMware&reg; vSphere environment is added in the Cloud Backup Portal, you can create a backup job. The backup job specifies the virtual machines (VMs) to be backed up, and where to save the backup data. You can run the backup job manually or schedule the backup job to run at specific times and intervals.
{: shortdesc}

You must configure vault settings and vCenter information before you can add a backup job.
{: important}

## Starting Cloud Backup Portal
{: #startPortalVRA}

You need to be connected to the {{site.data.keyword.cloud}} private network to be able to start the Portal.
{: requirement}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
4. Click **View backup portal** to start the portal in your browser.

   If the Portal doesn't start, you might have a problem with your VPN connection. You might also see a message that says that the form you’re sending isn’t secure. It is expected - proceed by sending the form.
   {: tip}

## Adding a vSphere backup job
{: #addvrajob}

1. On the navigation, click **Computers**. The computers page shows the registered computers and environments.
2. Click **Jobs**.
3. In the Select job Task menu, click **Create New VMware&reg; vCenter Job**.
4. Specify the following information.
   * In the **Name** field, type a name for the backup job.
   * In the **Description** field, optionally type a description for the backup job.
   * In the **Destination** list, select the vault where you want to save the backup data.
   * In the **Password** and **Confirm Password** fields, type an encryption password. You can also type a password hint in the Password Hint field.

   A vault appears in the list only if it is assigned to the user, or if the user added it to the computer’s Vault Settings.
   For new backup jobs, the encryption method is AES 256 bit. Existing jobs can have other encryption methods.
   {: note}

5.	In the **Include in Backup** field, take one or more of the following steps until the Backup Set field shows the virtual machines that you want to include in the backup job.
    * To add specific VMs to the backup job, select each virtual machine, and then click **Include**.
    * To exclude specific VMs from the backup job, select each virtual machine, and then click **Exclude**.
    * To add VMs to the backup job by name, check the virtual machines box, and then click **Include**.
    * To remove an inclusion or exclusion record from the Backup Set box, click **Delete** next to the record.

6. Click **Apply Now** to consolidate and simplify records in the Backup Set box, if changes need to be applied.
7. Click **Create Job**.

## Setting up a schedule
{: #setvraschedule}

After the backup job is created, you can add one or more schedules for running the job automatically.

1. When you click **Create Job**, the Schedule window appears and gives you an option to create a custom schedule for the backup job.

   By default Daily retention is selected for the job. Retention and Job schedule can be changed in this window, and multiple Retention schemes can also be assigned to the backup job.
   {: note}

2. Click **Save** to save the new schedule. The new job shows up under the Computers tab in the Jobs section. The Last backup status shows that the job never ran. The scheduled backup job runs automatically at the scheduled time.

## Running a scheduled job
{: #runvrajob}

Scheduled backup jobs can also be run immediately.

1. Click **Select Action**, and select **Run Job**. A new window appears and you can see information about the Destination Vault and Retention schemes that are assigned to the job.

   If multiple vaults and retention schemes are assigned to the job, these options can be changed in this window by clicking the Destination and Retention Scheme menu options.
   {: note}

2. Click **start Backup job** to issue the backup job immediately. In the progress window, you can see the status of the backup job and when the job is finished the job status changes from "Never Run" to "Completed".

To see the status of the last backup job that ran, click the Jobs tab. All job logs can be accessed from the action menu. Click **Action** and select **History/Logs**.
{: tip}

For more information about restoring virtual machines or Files and folders, see [Restoring vSphere data](/docs/Backup?topic=Backup-VRARestore#VRARestore).
