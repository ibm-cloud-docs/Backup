---

copyright:
  years: 1994, 2020
lastupdated: "2020-09-08"

keywords: IBM Cloud backup, EVault, Carbonite, backup, upgrade agent, Windows

subcollection: Backup

---
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:support: data-reuse='support'}
{:help: data-hd-content-type='help'}

# Upgrading backup software agent for Windows
{: #UpgradeinWindows}
{: help}
{: support}

The most recent backup agent can be downloaded from your Cloud Backup Portal Dashboard quick links section.
{:tip}

Any agent that's older than the 8.32 version needs to be upgraded because they cannot connect with the Backup portal due to outdated, unsupported TLS functionality. Following the upgrade process ensures that you can upgrade your {{site.data.keyword.backup_notm}} agent without losing the registration.
{:shortdesc}

1. Remote control your {{site.data.keyword.cloud}} server that is in need of an {{site.data.keyword.backup_notm}} upgrade.
2. Open a browser, and go to the following address.
   ```
   http://downloads.service.softlayer.com/evault/
   ```
   {:pre}
3. Click the file that you want. (For example, Agent-Windows-x64-6-72-1072a.exe)

   The version number is in the file name. Choose the most recent. <br/>{{site.data.keyword.cloud}} offers separate 32-bit and 64-bit installers. If you have a 64-bit Operating System, download the file with x64 in its name.
   {:tip}
4. Click **Run** at the download screen, and again after it is downloaded.
5. Click **Yes** to upgrade **{{site.data.keyword.backup_notm}} Software Agent**.

   The installer might disappear for a minute while it's loading.
   {:note}
6. Select **Keep my current registration**, and click **next**.
7. Click **next**. The agent begins the upgrade process. It can take a few minutes.
8. At the completion screen, click **Finish**.
