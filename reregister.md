---

copyright:
  years: 1994, 2019
lastupdated: "2019-10-31"

keywords: IBM Cloud backup, EVault, Carbonite, backup, reregister

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:shortdesc: .shortdesc}

# Reregistering a vault
{: #reregister}

Reregistering a vault is a task that is most commonly used after the Operating System of a server is reloaded. You can also use these steps to [use backups of one server to restore data on another server](/docs/infrastructure/Backup?topic=Backup-restorefromotherVSI).
{:shortdesc}

1. Start Cloud Backup Portal and log in. For more information, see the [Getting started tutorial](/docs/infrastructure/Backup?topic=Backup-getting-started#getting-started).

   Remember, Cloud Backup Portal is only accessible through {{site.data.keyword.BluVPN}}.
   {:tip}
2. On the navigation, click **Computers**. The computers page shows the registered computers and environments. Expand the computer you want to back up to second vault.
3. Click **Vault Settings**.
4. Click **Re-register**.
5. Complete the form.
  - Vault name
  - Vault address
  - Account

    "Account" is the equivalent of the "Account Name" in the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}/classic/storage/backup){: external}. Typically, it looks like "SLE[account ID]"
    {:tip}
  - User name
  - Password
6. Click **Load Computers**.
7. Click the computer name and click **Save**. A confirmation window appears, click **Yes** to confirm the reregistration of the computer.
8. Refresh the website to see the backup jobs associated with the computer.
9. Synchronize each backup job through the Action menu to restore safe-set history.

   If the backup jobs were created with an encryption password, you must enter the encryption password to restore data, or continue with backups.
   {:important}
10. Click **Close**.
