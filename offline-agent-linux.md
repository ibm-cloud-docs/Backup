---

copyright:
  years: 2020, 2020
lastupdated: "2020-07-29"

keywords: troubleshoot for Backup Agent, troubleshooting for Linux, question about Backup agent, troubleshooting Backup, Backup agent offline

subcollection: Backup

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .note}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Why does my Linux Backup Agent show offline?
{: #troubleshoot-LinuxAgent}
{: troubleshoot}
{: support}

There are multiple reasons why the Linux backup agent might appear offline in the Cloud Backup Portal. Follow the steps to rule out issues with firewall port settings, registration and the `buagent` process on the server.
{:shortdesc}

Linux agent shows as offline in Portal.
{: tsSymptoms}

## Check for firewall issues
{: #ts-LinuxAgentFW}

Currently, at minimum, your servers must allow access to the **10.200.86.0/24** and **10.2.118.0/24** subnets for TCP ports **8086**, **8087**. If the port settings are incorrect traffic is blocked and the agent cannot communicate with the Cloud Backup Portal.
{: tsCauses}

Check firewall ports - 8086 & 8087. For more information, see [Configuring Ports to allow communication between the backup agent and Cloud Backup Portal](/docs/Backup?topic=Backup-portinfo).
{: tsResolve}

## Ensure that the BUAgent is running
{: #ts-LinuxAgentbua}

When 'BUAgent' process is no longer active on the server, the Linux Agent appears offline in the Cloud Backup Portal.
{: tsCauses}

Ensure that the BUAgent is running by executing the following command on the Linux system.
: tsResolve}

```
/etc/init.d/vvagent status
```
{: pre}

The output shows whether the BUAgent is running.
```
VVAgent is running (PID: )
BUAgent is running (PID: )
```
{: screen}

* If the BUAgent is not running, start it with the following command.
  ```
  /etc/init.d/vvagent start
  ```
  {: pre}

* If the BUAgent is running, restart the services with the following command.
  ```
  /etc/init.d/vvagent restart
  ```
  {: pre}

## Register agent to the Cloud Backup portal

If after a refresh of the Portal page, it still shows the Agent is offline, the Agent needs to be registered again to Portal.
{: tsCauses}

Registering an Agent to the Portal retains all existing jobs, schedules and configurations as-is. Navigate to the Agent install directory, then run the register command.
: tsResolve}

```
cd opt/BUAgent
./register
```

Answer the following prompts.
* What is the Web-Based Agent Console address? `cloudbackupregister.service.softlayer.com`
* What is the Web-Based Agent Console connection port [8086]? Hit enter, 8086 is the correct port.
* What is the Web-Based Agent Console username? This is the username used to login to Portal.
* What is the Web-Based Agent Console password? This is the password used to login to Portal.

For more information about viewing or changing the Backup password, see [Changing the password for the backup service](/docs/Backup?topic=Backup-changePassword).

If the above steps don't work, pull up and review the most recent BUAgent-X.XLOG.

1. Navigate to `opt/BUAgent`.
```
cd /opt/BUAgent
```
2.  List the contents and sort them by date.
```
ls -lrth
```
3. Find the name of the most recent `BUAgent-x.XLOG` and open it with `/opt/BUAgent/xlogcat`. It can't be opened with `cat` or `vim`.
```
./xlogcat BUAgent-1.XLOG
```
{:pre}
4. Review the log and determine the issue.

If your service plan covers it, you can get help by creating a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external}.
