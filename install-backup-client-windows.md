---

copyright:
  years: 1994, 2025
lastupdated: "2025-04-07"

keywords: IBM Cloud backup, EVault, Carbonite, backup, install agent, Windows

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Installing the backup client in Windows
{: #InstallinWindows}

You can install the {{site.data.keyword.backup_full}} client through a series of interactions on the server that is designated for the {{site.data.keyword.backup_notm}} service.
{: shortdesc}

## Logging in to the target device server
{: #logintargetWin}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
2. Select **Devices** > **Device List** from the main menu to see the list of available servers.
3. Find the device for which you purchased the {{site.data.keyword.backup_notm}} service, and make note of its public IP address.
4. Click **Passwords** to display the Password manager, and see the usernames and the passwords that are associated with the account.
5. Log in to the target device by using Remote Desktop Connection.

## Downloading the backup client
{: #downloadclient}

1. On the target server, open a browser session and enter the following URL to download the executable file for the {{site.data.keyword.backup_notm}} client.
   ```sh
   http://downloads.service.softlayer.com/evault/
   ```
   {: pre}

   The version number is in the file name. Choose the most recent.
   {{site.data.keyword.cloud}} offers separate 32-bit and 64-bit installers. If you have a 64-bit Operating System, download the file with x64 in its name. (For example, Agent-Windows-x64-8-32-7901.exe.)
   {: tip}

2. Double-click the downloaded file.
3. Click **Run**.

## Installing and Registering the Backup Agent
{: #registeragent}

1. Enter the Network address.
   ```sh
   cloudbackupregister.service.softlayer.com
   ```
   {: pre}

2. Enter the username in the **user name** field.
   For more information about viewing the username or changing the backup password, see [Managing the username and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
   {: tip}

3. Enter the password in the **password** field.
4. Click **Next**.
5. Click **Install** to complete the installation.

Your servers must communicate with the Cloud Backup Portal and all AMP proxy servers for Cloud Backup Portal to work correctly, regardless of the data center's location. TCP Port 8086, 8087 must have access to `10.0.0.0/8`. For more information about port settings, see [Configuring Ports to allow communication between the backup agent and Cloud Backup Portal](/docs/Backup?topic=Backup-portinfo).

## Configuring backup agents
{: #configureagent}

Log in to Cloud Backup Portal to configure and manage your backup agents. For more information, see the [Getting started tutorial](/docs/Backup?topic=Backup-getting-started#getting-started).
