---

copyright:
  years: 1994, 2024
lastupdated: "2024-07-23"

keywords: IBM Cloud backup,  EVault, Carbonite, backup, restore

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Restoring data from one server to another
{: #restorefromotherVSI}

Sometimes you might want to restore data to a different server in the same data center. This procedure applies to file-level restores of non-OS files only. To restore a system image, follow the [Windows BMR](/docs/Backup?topic=Backup-restoreBMR) instructions.
{: shortdesc}

The process includes reregistering the backup agent on the second server to access the vault location of the first server and completing a **Restore from another Computer**.

## Before you begin
{: #prereqsrestore1}

- Server 1 and Server 2 must have the same Operating System. Cross-platform restores aren't supported.
- Server 1 and Server 2 must have backup agents that were configured previously. For more information about configuring the backup agents, see [Configuring the backup agent in Cloud Backup Portal](/docs/Backup?topic=Backup-getting-started#getting-started).
- A backup job for Server 1 that produced a backup to Server 1's vault location.

Disable all Scheduled tasks on both servers to avoid any conflicts.
{: important}

## Starting Cloud Backup Portal of Server 2
{: #startPortal}

Remember to start your [{{site.data.keyword.BluVPN}}](/docs/iaas-vpn?topic=iaas-vpn-getting-started){: external} connection to get access to the {{site.data.keyword.cloud}} private network or the Cloud Backup Portal link doesn't work.
{: tip}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Click Server 2.
4. Click **View backup portal** to start the portal in your browser.


## Editing the vault information
{: #changhingvault}

1. Click **Computers**, and click the server name to display its information.
2. Click **Vault Settings** and from the Action menu, select **Edit**.
3. Enter the Vault Name, which is the same as the unique vault name of Server 1.
4. Enter credentials for Server 1 to log in to the vault.
5. Click **Save**.

## Running the backup job from Server 1 as the restore job on Server 2
{: #runbackuprestore}

1. On the **Computer** tab, click **Jobs**.
   You might need to refresh the page to see the jobs that are defined on Server 1 as accessible and synchronized under the Server 2 **Jobs** tab.
   {: tip}

2. From the Action menu, select **Restore from Another Computer**.
3. Select the Vault, Computer, and Job from menus.
4. Enter the encryption password.
5. The Restore window appears. By default, it displays the most recent safe set. To choose a different date, click the Calendar icon, and view other safe sets.
6. Select the files and directories that you want to include. Then, click **Include** to save your choices.
   Default restore options place the files in their original location. If files exist in the destination folder with the same name, the incoming file is renamed. These options can be changed and an alternative restore location can be selected from Restore Destination options.
   {: note}

7. When your restore set is configured the way that you want it, click **Apply Now**.
8. Then, click **Run Restore**.
9. The files are restored when the Status displays **Restore completed** on the **Process Details** screen. Click **Close** to close the window and return to the main Cloud Backup Portal screen.


## Verifying the restore
{: #verifyrestore}

1. Connect to the root of Server 2 through ssh.
2. List the files and all directory entries in a long format.
    ```sh
    ls -la
    ```
    {: pre}

3. Compare the output.

## Resuming normal backup schedule.
{: #resumeschedule}

1. When the restore is complete, remove the registration information of server1, where the data was restored from.
2. Enter the current server2 registration and enable Schedule tasks.
