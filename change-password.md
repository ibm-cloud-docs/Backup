---

copyright:
  years: 1994, 2023
lastupdated: "2023-03-20"

keywords: IBM Cloud backup, EVault, Carbonite, backup, password, password reset

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Managing username and password for the Cloud Backup service
{: #changePassword}

Each {{site.data.keyword.backup_full}} service has an associated password that is used to access the vault within the Cloud Backup Portal.
Changes that are made to the {{site.data.keyword.backup_notm}} password within the {{site.data.keyword.cloud_notm}} console are made to the service itself. When you change your password, keep in mind that it impacts your service directly.
{: shortdesc}

## Viewing the backup username and password
{: #viewBackupPW}
{: help}
{: support}

The username and password can be seen on the {{site.data.keyword.backup_notm}} instance's Overview page, the username is in the upper-left part of the screen. The Portal Password is on the Overview tab.

You can also see the username and password through the [Device list](https://cloud.ibm.com/gen1/infrastructure/devices){: external}. To view usernames and accounts that are associated with your Devices, click Devices > Device list, and click the Device name. On the left-side menu, click Passwords. The IBM Cloud Backup service is listed in the Software Name column as "Base Client".

Alternatively, you can click Devices > Manage > Passwords. The console displays the list of your devices and the associated software with the appropriate usernames and passwords. The service name is listed as "Base Client".

## Changing the backup password
{: #changeBackupPW}
{: help}
{: support}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the list of backup services.
3. Click the instance name of the backup vault where you want to change your password.
4. On the Overview page, you can see your Portal Password. Click the Pencil icon to modify the password.

   The IBM Cloud Backup username is displayed in the upper-left part of the console.
   {: note}

5. Enter the new password in the **Password** field.

   The password must be 8 - 12 characters in length. It must include at least one uppercase letter, at least one lowercase letter, at least one numeric character, and at least one of these special characters: `\!@\#%\^`. It can contain only letters, numerals, and these special characters: `\!@\#%\^`.
   {: important}

6. Press Enter to update the password.
