---

copyright:
  years: 1994, 2026
lastupdated: "2026-08-20"

keywords: IBM Cloud backup, EVault, Carbonite, backup, restore

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Restoring data from {{site.data.keyword.backup_notm}}
{: #simplerestore}

Restore files and folders from your {{site.data.keyword.backup_notm}} vault by using the Cloud Backup Portal to recover data from previous backup jobs.
{: shortdesc}

## Starting Cloud Backup Portal
{: #startPortalsimple}

Remember to start your [{{site.data.keyword.BluVPN}}](/docs/iaas-vpn?topic=iaas-vpn-getting-started){: external} connection to get access to the {{site.data.keyword.cloud}} private network. The Cloud Backup Portal link doesn't work otherwise.
{: important}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Click the instance name of the {{site.data.keyword.cloud_notm}} service to display the instance details, including your portal username and password.
4. Click **Backup portal login** to start the portal in your browser, then enter your username and password when prompted.

   The Cloud Backup Portal requires a [VPN connection](/docs/iaas-vpn?topic=iaas-vpn-getting-started){: external} to the IBM Cloud private network.
   {: tip}

## Restoring your data
{: #simplyrestore}

1. On the navigation, click **Computers**. The computers page shows the registered computers and environments. Expand the server that you want to restore to a previous state.
2. Click **Jobs** to load the job options.
3. Click **Select job Task** and select **Restore**.
4. Confirm the vault, computer, and job information and click **Okay**.
5. Enter the encryption password of the previous backup.
6. The Restore Options window appears. By default, it displays the most recent safe set. To choose a different date, click the Calendar icon and view other safe sets.
7. Select the files and directories that you want to include. Then, click **Include** to save your choices.

    Default restore options place the files in their original location. If files exist in the destination folder with the same name, the incoming file is renamed. These options can be changed and an alternative restore location can be selected from Restore Destination options.
    {: note}

8. When your restore set is configured the way that you want it, click **Apply Now**.
9. Then, click **Run Restore**.
10. The files are restored when the Status displays **Restore completed** on the **Process Details** screen.
