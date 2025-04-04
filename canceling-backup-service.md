---

copyright:
  years: 1994, 2025
lastupdated: "2025-04-03"

keywords: IBM Cloud backup, cancel, cancellation, EVault, Carbonite, backup

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Canceling the {{site.data.keyword.backup_notm}} service
{: #cancelBackup}
{: help}
{: support}

You can cancel your {{site.data.keyword.backup_full}} service at any time. The cancellation deletes your vault with the backed-up data and you can't log in to the Cloud Backup Portal with the canceled credentials either.
{: shortdesc}

If you cancel the virtual or the Bare Metal Server that the {{site.data.keyword.backup_notm}} was provisioned for, the {{site.data.keyword.backup_notm}} service is also canceled. Your vault with the backed-up data is deleted automatically. You cannot keep your backups to be used with a different server later.
{: note}

## Cancel the service in the console
{: #cancelbackupUI}
{: ui}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
1. Click **Storage** > **Cloud Backup** to display the servers with backup service.
1. Click the name of the instance that you want to delete. This action displays the Backup service's details page.
1. Select **Actions** > **Delete**.
1. Choose to cancel **Immediately** or on the **Anniversary Date**.

   You can cancel the service anytime. However, when a backup vault is deleted before the end of the monthly billing cycle, you do not receive a refund.
   {: important}

1. Select **Continue**.
1. Acknowledge that cancellation might cause data loss in the future by checking the box. After that, click **Delete**.

## Cancel the service with Terraform
{: #cancelbackupterraform}
{: terraform}

Use the `terraform destroy` command to conveniently remove a remote object such as an instance of {{site.data.keyword.backup_notm}}. The following example deletes the vault that is defined by its ID.

```terraform
terraform destroy --target ibm_storage_evault.example.id
```
{: codeblock}

For more information, see the [terraform documentation](https://developer.hashicorp.com/terraform/cli/commands/destroy){: external}.

## Uninstall the Backup Agent from your server
{: #uninstallbackupagent}

### Removing the Backup Agent from a Windows Server
{: #uninstallbackupagentWin}

1. Establish a remote desktop session to your server.
2. Go to **Start**, and click **Control Panel**.
3. Select **Programs and Features**.
4. Right-click the **EVault Software Agent** and confirm the removal by clicking uninstall.
5. In the dialog box that appears, click **Yes**.
6. Select **Total uninstall** and confirm by clicking **Next >**.
7. Restart your server to make sure that the software is removed completely.

### Removing the Backup Agent from a Linux&reg; Server
{: #uninstallbackupagentLin}

1. Establish a Secure Shell connection (SSH) to your server.
2. From the command line, issue the following command.
    ```sh
    /opt/BUAgent/uninstall.sh
    ```
3. When prompted by the following question, press Y, then press Enter.
    ```sh
    VVAgent is still running. Do you wish to stop it? ([Y]/n)
    ```
4. At the next prompt, press Y. Then, press Enter again.
    ```sh
    This will remove jobs, settings, etc. (y/[N])
    ```
5. Restart your server at your earliest convenience to make sure that the software is removed completely.
