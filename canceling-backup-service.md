---

copyright:
  years: 1994, 2021
lastupdated: "2021-09-01"

keywords: IBM Cloud backup, cancel, cancellation, EVault, Carbonite, backup

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}
{:support: data-reuse='support'}
{:help: data-hd-content-type='help'}

# Canceling an {{site.data.keyword.backup_notm}} service
{: #cancelBackup}
{: help}
{: support}

You can cancel your {{site.data.keyword.backup_full}} service at any time. The cancellation deletes your vault with the backed-up data and you can't log in to the Cloud Backup Portal with the canceled credentials.
{: shortdesc}

## Cancel the service in the UI
{: #cancelbackupUI}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Select **Actions** > **Cancel {{site.data.keyword.backup_notm}}**.
4. Choose to cancel **Immediately** or on the **Anniversary Date**.

   You can cancel the service anytime. However, when a backup vault is deleted before the end of the monthly billing cycle, you do not receive a refund.
   {: important}

5. Select **Continue**.
6. Check that **I acknowledge that due to cancellation data loss may occur**. Then, select **Cancel {{site.data.keyword.backup_notm}}**.

## Uninstall the Backup Agent from your server
{: #uninstallbackupagent}

### Removing the Backup Agent from a Windows&reg; Server
{: #uninstallbackupagentWin}

1. Establish a remote desktop session to your server.
2. Go to Start, and click Control Panel.
3. Select Programs and Features.
4. Right-click the EVault Software Agent and confirm the removal by clicking Uninstall.
5. In the dialog box that appears, click Yes.
6. Select Total Uninstall and confirm by clicking Next >.
7. Reboot your server at your earliest convenience to ensure that the software is removed completely.

### Removing the Backup Agent from a Linux&reg; Server
{: #uninstallbackupagentLin}

1. Establish a Secure Shell connection (SSH) to your server.
2. From the command line, execute the following command:
    ```zsh
    /opt/BUAgent/uninstall.sh
    ```
3. When prompted by the following question, press Y, then press Enter.
    ```zsh
    VVAgent is still running. Do you wish to stop it? ([Y]/n)
    ````
4. At the next prompt, press Y, then, press Enter again.
    ```zsh
    This will remove jobs, settings, etc. (y/[N])
    ```
5. Reboot your server at your earliest convenience to ensure that the software is removed completely.
