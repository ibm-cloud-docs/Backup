---

copyright:
  years: 1994, 2019
lastupdated: "2019-02-05"

keywords: IBM Cloud backup, EVault, Carbonite, backup, restore

subcollection: Backup

---
{:deprecated: .deprecated}

# Restoring a job from another computer on Windows 2016
{: #restorefromother2016}

This article is deprecated because the content applies to our Federal environment only. All commercial customers can follow the instructions in [Restoring from a backup](/docs/Backup?topic=Backup-simplerestore) or [Restoring data from one server to another](/docs/Backup?topic=Backup-restorefromotherVSI).
{:deprecated}

Use these steps to complete a file restore from another computer by using the Windows Central Control.

1. Remote control your Windows 2016 server through RDP.
2. Open CentralControl.
3. Right-click **Agent**, and click **Agent Configuration**.
4. Remove current Vault settings from CentralControl by selecting the entry and clicking **Delete**.
5. Click **New**, and on the next screen, select **Re-register previously registered computer**. Click **Next**.
6. Enter network address, and click **Add**, then click **Next**.
7. Enter the new port values, and click **Add**, then **Next**.
8. In the Connection Settings screen, enter the number of seconds/minutes that you want.
9. In the Authentication screen, enter your credentials, and click **Next**.
10. Registered Computers window displays the host name of your server. Click **Next**.
11.	When the Vault Configuration Wizard finishes collecting your information, click **Finish** to complete the registration.
12. When prompted, confirm that you want to proceed with the reregistration.
13. When registration is complete, click **Restore** from the menu bar.
9.	Select the appropriate safe-set and enter the encryption password. Click **Next**.
10.	Select the files that you want to restore, and select default options, and click **Finish**.
11.	When the restore is complete, remove the vault registration, and reregister with current vault account information.
