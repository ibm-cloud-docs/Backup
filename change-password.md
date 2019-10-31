---

copyright:
  years: 1994, 2019
lastupdated: "2019-10-31"

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

# Changing the password for the backup service
{: #changePassword}

Each {{site.data.keyword.backup_full}} service has an associated password that is used to access the vault within the Cloud Backup Portal.

For many {{site.data.keyword.cloud}} products and services, the password storage feature within the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/classic){: external} is used solely for the tracking of the password. For those products and services, the changes that are made to the password within the {{site.data.keyword.cloud_notm}} console aren't applied to the product or service. It's **not** the case for {{site.data.keyword.backup_notm}}.
{:shortdesc}

Changes that are made to the {{site.data.keyword.backup_notm}} password within the {{site.data.keyword.cloud_notm}} console are made to the service itself. When you change your password, keep in mind that it impacts your service directly.
{:important}

## Changing the password

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational Menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Click anywhere on the row of the vault to expand the view.
4. Click **Show** to view the current password.
5. Enter the new password in the **Password** field.
6. Click **Update**.
