---

copyright:
  years: 1994, 2025
lastupdated: "2025-03-21"

keywords: IBM Cloud backup, EVault, Carbonite, backup, password, password reset

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Managing the username and password for the {{site.data.keyword.backup_notm}} service
{: #changePassword}

Each {{site.data.keyword.backup_full}} service has an associated password that is used to access the vault within the Cloud Backup Portal.
{: shortdesc}

Changes that are made to the {{site.data.keyword.backup_notm}} password within the {{site.data.keyword.cloud_notm}} console are made to the service itself. When you change your password, keep in mind that it impacts your service directly.
{: important}

## Viewing the backup username and password in the console
{: #viewBackupPW-ui}
{: help}
{: support}
{: ui}

The username and password can be seen on the {{site.data.keyword.backup_notm}} instance's Overview page in the console.

You can also see the username and password through the [Device list](https://cloud.ibm.com/gen1/infrastructure/devices){: external}. To view usernames and accounts that are associated with your Devices, click **Devices > Device list**, and click the device name. Next, click **Passwords**. The IBM Cloud Backup service is listed in the Software Name column as "Base Client".

Alternatively, you can click **Devices > Manage > Passwords**. The console displays the list of your devices and the associated software with the appropriate usernames and passwords. The service name is listed as "Base Client".

## Viewing the backup username and password with Terraform
{: #viewBackupPW-terraform}
{: help}
{: support}
{: terraform}

To use Terraform, download the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in. For more information, see the [Getting started with Terraform](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started) tutorial.
{: requirement}

Use the `ibm_storage_evault` resource to create or update your {{site.data.keyword.backup_full}} instance. After the backup vault is provisioned, you can access the `username` and `password` attributes.

For more information about arguments and attributes, see [ibm_storage_evault](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/storage_evault){: external}.

## Changing the backup password in the console
{: #changeBackupPW}
{: help}
{: support}
{: ui}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the list of backup services.
3. Click the instance name of the backup vault where you want to change your password.
4. On the Overview page, you can see your Portal Password. Click the **Edit icon** ![Edit icon](../icons/edit-tagging.svg "Edit") to modify the password.
5. Enter the new password in the **Password** field.

   The password must be 8 - 12 characters in length. It must include at least one uppercase letter, at least one lowercase letter, at least one numeric character, and at least one of these special characters: `\!@\#%\^`. It can contain only letters, numerals, and these special characters: `\!@\#%\^`.
   {: important}

6. Press Enter to update the password.
