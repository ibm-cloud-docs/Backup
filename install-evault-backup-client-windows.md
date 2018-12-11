---

copyright:
  years: 1994, 2018
lastupdated: "2018-11-13"

---
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}

# Installing the EVault backup Client in Windows

Installing the EVault backup client in Windows is completed through a series of interactions on the server that is designated for the EVault backup service.

Windows 2016 isn't supported currently. Refer to instructions for [Windows 2016](install-evault-windows2016.html).
{:important}

## Logging in to the target device server

1. Log in to the [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}, and select **Devices** > **Device List** from the main menu to see the list of available servers.
2. Find the device for which you purchased the EVault service, and make note of its public IP address.
3. Click the right-pointing arrow to expand and show more information about the device, including the user name and password. If the password isn't displayed, clicking **Show Password** reveals it.
4. Log in to the target device by using Remote Desktop Connection.

## Downloading the EVault client

1. On the target server, open a browser session and enter the following URL to download the executable file for the backup client. <br/>
  ```
  http://downloads.service.softlayer.com/evault/
  ```
  {:pre}

2. Double-click the downloaded file.
3. Click **Run**.


## Installing and Registering the agent

1. Enter the Network address: <br />
  ```
  https://ev-webcc01.service.softlayer.com
  ```
  {: pre}

2. Enter the EVault user name and password.
3. Click **Next**
4. Click **Install** to complete the installation.

## Configuring backup Agents

Log in to WebCC to configure and manage your backup agents. Refer to the [Getting started tutorial](index.html#configuring-backup-agent-in-webcc) for instructions.
