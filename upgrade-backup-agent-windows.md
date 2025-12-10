---

copyright:
  years: 2004, 2025
lastupdated: "2025-12-09"

keywords: IBM Cloud backup, EVault, Carbonite, backup, upgrade agent, Windows

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Upgrading backup software agent for Windows
{: #UpgradeinWindows}
{: help}
{: support}

The most recent supported version of the Windows Agent is v9.00. Any agent that is older than the 8.32 version needs to be upgraded. Any agent that's older than the 8.32 version cannot connect with the Backup portal due to the outdated, unsupported TLS version. Following the upgrade process makes sure that you can upgrade your {{site.data.keyword.backup_notm}} agent without losing the registration.
{: shortdesc}

The most recent backup agent can be downloaded from your Cloud Backup Portal Dashboard quick links section.
{: tip}

1. Remote control your {{site.data.keyword.cloud}} server that is in need of an {{site.data.keyword.backup_notm}} upgrade.
2. Open a browser, and go to the following address.

     ```sh
     http://downloads.service.softlayer.com/evault/
     ```
     {: pre}

3. Click the file that you want.

    The version number is in the file name. Choose the most recent.
    {{site.data.keyword.cloud}} offers separate 32-bit and 64-bit installers. If you have a 64-bit Operating System, download the file with x64 in its name. For example, `Agent-Windows-x64-9-30-1009.exe`.
    {: tip}

4. Click **Run** at the download screen, and again after it is downloaded.
5. Click **Yes** to upgrade **{{site.data.keyword.backup_notm}} Software Agent**.

    The installer might disappear for a minute while it's loading.
    {: note}

6. Select **Keep my current registration**, and click **next**.
7. Click **next**. The agent begins the upgrade process. It can take a few minutes.
8. At the completion screen, click **Finish**.
