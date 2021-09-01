---

copyright:
  years: 1994, 2021
lastupdated: "2021-08-05"

keywords: IBM Cloud backup, EVault, Carbonite, backup, password, password reset

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

# Changing the password for the backup service
{: #changePassword}

Each {{site.data.keyword.backup_full}} service has an associated password that is used to access the vault within the Cloud Backup Portal.
Changes that are made to the {{site.data.keyword.backup_notm}} password within the {{site.data.keyword.cloud_notm}} console are made to the service itself. When you change your password, keep in mind that it impacts your service directly.
{: shortdesc}

## Viewing the  backup user name and password
{: #viewBackupPW}
{: help}
{: support}

The user name and password can be seen on the {{site.data.keyword.backup_notm}} instance's Overview page, the user name is in the upper-left corner. The Portal Password is on the Overview tab.
You can also see the user name and password through the [Device list](https://cloud.ibm.com/gen1/infrastructure/devices){: external}. To view user names and accounts that are associated with your Devices, click Devices > Device list, and click the Device name. On the left-side menu, click Passwords. The IBM Cloud Backup is listed in the Software Name column as "Base Client".
Alternatively, you can click Devices > Manage > Passwords. The console displays the list of your devices and the associated software with the appropriate user names and passwords. The software name is listed as "Base Client".

## Changing the backup password
{: #changeBackupPW}
{: help}
{: support}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the list of backup services.
3. Click the instance name of the backup vault where you want to change your password.
4. On the Overview page, you can see your Portal Password. Click the Pencil icon to modify the password.
   The IBM Cloud Backup username is displayed in the upper-left corner of the page.
   {: note}
5. Enter the new password in the **Password** field.
   The password must be: 8 - 12 characters in length, include at least 1 uppercase letter, include at least 1 lowercase letter, include at least 1 numeric character, include at least 1 of these special characters: `\!@\#%\^` and contain only letters, numerals, and these special characters: `\!@\#%\^`
   {: important}
6. Press Enter to update the password.
