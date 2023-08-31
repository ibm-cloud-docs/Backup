---

copyright:
  years: 2023
lastupdated: "2023-05-22"

keywords: IBM Cloud backup, EVault, Carbonite, backup, restore, Backup Portal, portal

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Overview of the Backup Portal
{: #backupportalreference}

The Backup Portal provides a central access point for managing backups and restores for all of your servers. You can create and run backup jobs, restore data, monitor computer and processes; all within the Portal.
{: shortdesc}

## Starting Cloud Backup Portal
{: #startPortaloverview}

Remember to start your [{{site.data.keyword.BluVPN}}](/docs/iaas-vpn?topic=iaas-vpn-getting-started){: external} connection to get access to the {{site.data.keyword.cloud}} private network. The Cloud Backup Portal link doesn't work otherwise.
{: requirement}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
4. Click **View backup portal** to start the portal in your browser.

## Pages in the Portal
{: #pagesinportal}

The portal includes a series of pages where you can perform various tasks for managing backups and restores.

### Dashboard
{: #portaldashboard}

The Dashboard provides notifications and summary information about servers, backups, restores, and activity in your site. In the What’s new section, you can see the newest {{site.data.keyword.backup_full}} Announcements along with unconfigured agent information. Such a {{site.data.keyword.backup_notm}} agent can be configured by clicking the Configure Now link or by clicking the computers tab.

For more

### Computers
{: #portalcomputers}

On the Computers page, you can view server information, configure backup jobs, run jobs, and restore data. For more information about how to configure backup jobs, see [Configuring the backup agent and the backup schedule](/docs/Backup?topic=Backup-getting-started#configureagentschedule). For more information about how to run jobs, see [running your first backup job](/docs/Backup?topic=Backup-getting-started#runfirstbackup). For more information about restoring data, see [Restoring data from a backup](/docs/Backup?topic=Backup-simplerestore).

### Monitor
{: #portalmonitor}

On the Monitor page, you can view the most recent backup statuses for your jobs, monitor processes, and view logs. You can go from information on the Monitor page to related information on the Computers page or in the Logs window. If you click an online computer name or job name, you can view the computer’s record on the Computers page. If you click a job’s last backup status, you can view the job’s past logs in a separate window.

