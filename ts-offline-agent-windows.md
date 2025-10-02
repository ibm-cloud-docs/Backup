---

copyright:
  years: 2020, 2025
lastupdated: "2025-10-01"

keywords: troubleshoot for Backup Agent, troubleshooting for Windows, question about Windows backup agent, troubleshooting backup, backup agent offline

subcollection: Backup

---

{{site.data.keyword.attribute-definition-list}}

# Why does my Windows Backup Agent appear offline?
{: #troubleshoot-WinAgent}
{: troubleshoot}
{: support}

The Windows backup agent might appear offline in the Portal for multiple reasons. Follow the steps to rule out issues with firewall port settings, and the `buagent` process on the server.
{: shortdesc}

Windows agent shows as offline in Portal.
{: tsSymptoms}

## Possible firewall issue
{: #ts-WinAgentFW}

Your servers must allow access to the `10.200.86.0/24` and `10.2.118.0/24` subnets for TCP ports **8086**, **8087**. If the port settings are incorrect, traffic is blocked, and the agent cannot communicate with the Portal.
{: tsCauses}

Check firewall ports - 8086 & 8087. For more information, see [Configuring Ports to allow communication between the backup agent and Cloud Backup Portal](/docs/Backup?topic=Backup-portinfo).
{: tsResolve}

1. Establish a Remote Desktop connection to the offline Agent server.
2. Then, run one of the following commands to check the ports.
   * Open CMD and run `telnet` to validate the connection. If TELNET is not yet installed, you can add the Telnet Client through the **Add Roles and Features**.

     ```sh
     telnet cloudbackupregister.service.softlayer.com 8086
     ```
     {: pre}

     If the port is open, the CMD shows a blank screen. If the port is not open, CMD returns the following message.

     ```sh
     Connecting to cloudbackupregister.service.softlayer.com… Could not open connection to the host, on port 8086: Connect failed
     ```
     {: screen}

     If so, you must contact your network team to update the firewall.

   * If you don't want to install Telnet, you can use `test-netconnection` in Powershell.
     1. Open Powershell as Administrator.
     2. Enter the following command.

       ```sh
       test-netconnection cloudbackupregister.service.softlayer.com -Port 8086
       ```
       {: pre}

       If the port is open, the last line shows the following.

       ```sh
       TcpTestSucceeded : True
       ```
       {: screen}

       If the port is not open, TcpTestSucceeded equals “False”.

       ```sh
       TcpTestSucceeded : False
       ```
       {: screen}

       If so, you must contact your network team to update the firewall.

## BUAgent isn't running
{: #ts-WinAgentbua}

When the `BUAgent` process is no longer active on the server, the Window Agent appears offline in the Portal.
{: tsCauses}

Restart the Carbonite EVault Server Backup BUAgent in Services.msc.
{: tsResolve}

1. Establish a Remote Desktop connection to the offline Agent server.
2. Open `Services.msc`.
3. Restart the BUAgent service.
4. Refresh the page on the Portal webpage and see whether the Agent is shown as _online_.

If the previous steps don't work, pull up and review the most recent BUAgent-X.XLOG.

1. Go to the backup Agent folder.

   ```sh
   C:\Program Files\Carbonite Server Backup\Agent\
   ```
   {: screen}

   Or
   
   ```sh
   C:\Program Files\Evault Software\Agent\
   ```
   {: screen}

2. Find the name of the most recent `BUAgent-x.XLOG`. The file doesn't open with Notepad or WordPad. You must open the file with the `LogViewer.exe` in the `Bin32` folder of the Agent install.
3. Right-click the most recent `BUAgent-.XLOG` and select **open with**.
4. Click **More Apps**, then click **open with another application**.
5. Scroll down and click **Look for another app on this PC**.
6. Select `LogViewer.exe` in the following Directory `C:\Program Files\Carbonite Server Backup\Agent\Bin32`. If it's an older Agent, the file might be under `Program Files\Evault Software`.
7. Review the log and determine the issue.

If your service plan covers it, you can get help by creating a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external}.
