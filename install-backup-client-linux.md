---

copyright:
  years: 1994, 2025
lastupdated: "2025-04-07"

keywords: IBM Cloud backup, EVault, Carbonite, backup, install agent, Linux

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Installing the backup client in Linux
{: #InstallinLinux}

You can install the {{site.data.keyword.backup_full}} client on a Linux&reg;-based operating system through a series of commands in the shell or terminal within the OS.
{: shortdesc}

This procedure outlines the steps that are required to install the client on any of the following operating systems:
* Red Hat Enterprise Linux&reg;
* CentOS Stream
* CloudLinux&reg;

After you completed the procedure, the automated process registers the Agent service with Cloud Backup Portal, then downloads and installs the files that are needed to run the service.

If you purchased {{site.data.keyword.backup_notm}} when you ordered a server through the [{{site.data.keyword.cloud_notm}} catalog](/catalog){: external} or the {{site.data.keyword.cloud_notm}} console, then the software is automatically installed for you. You don't need to use the procedures that are described in this document.
{: tip}

If you purchased {{site.data.keyword.backup_notm}} as an upgrade in the {{site.data.keyword.cloud_notm}} console, follow these steps to install the software.

## Logging in to the target device server
{: #logintargetLin}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
2. Select **Devices** > **Device List** from the main menu to see the list of available server devices.
3. Find the device for which you purchased the {{site.data.keyword.backup_notm}} service, and make a note of its public IP address.
   - This IP address is to be used when you log in to the device from the command line. In the command that is shown in Step 5, replace `<publicIpAddress>` with the actual public IP address.
4. Click Passwords to display the Password manager, and see the usernames and the passwords that are associated with the account.
5. Log in to the target device by entering the following command from the command line.
    ```sh
    ssh <user name>@<publicIpAddress>
    ```
    {: pre}

    If you didn't log in to this server with this username before, you are presented a message about the authenticity of the host. You are also asked whether you want to continue. Reply with **yes** to continue.
    {: note}

6. You are prompted to enter the password unless you set up ssh keys for accessing this server before.

## Updating the OS to prepare for the installation (RHEL only)
{: #updateOSRHEL}

This step is required for RHEL, but optional for other distributions.
{: tip}

- Run the following command at the server prompt.
   ```sh
   yum update
   ```
   {: pre}

   If you're prompted, confirm that the download size is okay. The update proceeds and displays a "Complete" message when it finishes.

## Getting the installation script
{: #downloadscript}

- Run the following command at the server prompt.
   ```sh
   wget -N http://downloads.service.softlayer.com/evault/evault_manual.sh
   ```
   {: pre}

## Running the installation Script
{: #executescript}

1. Run the following command at the server prompt.
   ```sh
   sh ./evault_manual.sh
   ```
   {: pre}

2. Enter your Cloud Backup Portal username and password.

    For more information about viewing the username or changing the backup password, see [Managing the username and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
    {: tip}

3. After the username and password, no further input is required. The prompts that are written to the screen as the installation proceeds can be safely ignored.

    They are produced by a subscript, which is started by the `evault_manual.sh` script. The `evault_manual.sh` script provides the input for these prompts.
    {: note}

4. The installation is complete when the following messages appear.

    ```sh
    Starting VVAgent: [ OK ]
    Starting buagent: [ OK ]
    ```
    {: codeblock}

## Verifying that the installation succeeded
{: #verifyinstall}

1. Verify that the message `Registered to The Portal` appears in the installation output. The verification can be done by looking for the message on screen or by inspecting the output of the following command.
    ```sh
    grep 'Registered' /opt/BUAgent/Install.log
    ```
    {: pre}

2. Run the following command and observe the output.
    - For backup agent 9.21, use the following command.

    ```sh
    etc/rc.d/vvagent status
    ```
    {: pre}

    - For previous versions, use the following command.

    ```sh
    service vvagent status
    ```
    {: pre}

    The following messages are displayed.
    ```sh
    VVAgent is running (PID xxxxx).
    buagent is running (PID xxxxx).
    ```
    {: codeblock}

   The process IDs that are represented by `xxxxx` vary with each installation.
   {: tip}

## Next steps
{: #afterinstalllin}

Log in to Cloud Backup Portal to configure and manage your backup agents. For more information, see the [Getting Started Tutorial](/docs/Backup?topic=Backup-getting-started#getting-started) and [Configuring a simple file-level backup](/docs/Backup?topic=Backup-configureFileBackup).
