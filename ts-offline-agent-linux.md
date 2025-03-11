---

copyright:
  years: 2020, 2025
lastupdated: "2025-03-11"

keywords: troubleshoot for backup agent, troubleshooting for Linux, question about backup agent, troubleshooting backup, backup agent offline

subcollection: Backup

---

{{site.data.keyword.attribute-definition-list}}

# Why does my Linux Backup Agent appear offline?
{: #troubleshoot-LinuxAgent}
{: troubleshoot}
{: support}

The Linux&reg; backup agent might appear offline in the portal for multiple reasons. Follow the steps to rule out issues with firewall port settings, registration, and the `buagent` process on the server.
{: shortdesc}

Linux&reg; agent shows as offline in Portal.
{: tsSymptoms}

## Possible firewall issue
{: #ts-LinuxAgentFW}

Currently, at minimum, your servers must allow access to the **`10.200.86.0/24`** and **`10.2.118.0/24`** subnets for TCP ports **8086**, **8087**. If the port settings are incorrect, traffic is blocked, and the agent cannot communicate with the Cloud Backup Portal.
{: tsCauses}

Check firewall ports - 8086 & 8087. For more information, see [Configuring Ports to allow communication between the backup agent and Cloud Backup Portal](/docs/Backup?topic=Backup-portinfo).
{: tsResolve}

## BUAgent service isn't running
{: #ts-LinuxAgentbua}

When the `BUAgent` process is no longer active on the server, the Linux&reg; Agent appears offline in the Cloud Backup Portal.
{: tsCauses}

Make sure that the BUAgent is running by issuing the following command on the Linux&reg; system.
{: tsResolve}

```sh
/etc/init.d/vvagent status
```
{: pre}

The output shows whether the BUAgent is running.
```sh
VVAgent is running (PID: )
BUAgent is running (PID: )
```

* If the BUAgent is not running, start it with the following command.
   ```sh
   /etc/init.d/vvagent start
   ```
   {: pre}

* If the BUAgent appears to be running, restart the service with the following command.
   ```sh
   /etc/init.d/vvagent restart
   ```
   {: pre}

## The agent needs to be reregistered to the Cloud Backup portal
{: #reregistagentinportal}

If it still shows that the Agent is offline after a refresh of the Portal page, then the Agent needs to be registered again.
{: tsCauses}

Registering an Agent to the Portal retains all existing jobs, schedules, and configurations as-is. Go to the Agent installation directory, then run the register command.
{: tsResolve}

```sh
cd opt/BUAgent
./register
```

Answer the following prompts.
* What is the web-based Agent Console address? `cloudbackupregister.service.softlayer.com` or `cloudbackupregister.service.usgov.softlayer.com`
* What is the web-based Agent Console connection port [8086]? Press enter, 8086 is the correct port.
* What is the web-based Agent Console username? The answer is the same username that is used to log in to Portal.
* What is the web-based Agent Console password? The answer is the same password that is used to log in to Portal.

For more information about viewing or changing the backup password, see [Managing the username and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
{: tip}

If the previous steps don't work, pull up and review the most recent BUAgent-X.XLOG.

1. Go to `opt/BUAgent`.
   ```sh
   cd /opt/BUAgent
   ```
   {: pre}

2.  List the contents and sort them by date.
    ```sh
    ls -lrth
    ```
    {: pre}

3. Find the name of the most recent `BUAgent-x.XLOG` and open it with `/opt/BUAgent/xlogcat`. It can't be opened with `cat` or `vim`.
   ```sh
   ./xlogcat BUAgent-1.XLOG
   ```
   {: pre}

4. Review the log and determine the issue.

If your service plan covers it, you can get help by creating a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external}.
