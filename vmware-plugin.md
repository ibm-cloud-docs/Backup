---

copyright:
  years: 1994, 2019
lastupdated: "2019-11-14"

keywords: IBM Cloud Backup, VMware, VRA, vSphere Recovery Agent, plug-in, plugin, EVault, Carbonite, vSphere

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}

# Learn about the vSphere Recovery Agent
{: #VRA}

The vSphere Recovery Agent (VRA) is a Windows application, which can back up and restore VMDKs up to 10 TB. You can install the vSphere Recovery Agent on a physical or virtual machine that has local network access to the vCenter that you want to protect. For best performance, install the VRA on a machine that is in the same subnet as the vCenter. To distribute the workload, up to five VRAs can protect VMs that are attached to a single vCenter.
{:shortdesc}

In a vSAN stretched cluster, each VM has a preferred site. Ideally, one local VRA is installed in each site that backs up preferred VMs of that site. If a VM is moved to a different site (because of maintenance or failures), backup performance can be degraded but remain acceptable.

## Installing the plug-in
{: #installVRAPlugin}

Ensure that power management is disabled on the server where you install the VRA.
{: important}

1. Download the installation kit from `http://downloads.service.softlayer.com/evault/`. Then, double-click the installation kit.
2. On the confirmation message, click **YES**.
3. On the welcome page, click **Next**.
4. On the End-User-License Agreement page, read the license agreement. If you agree to the terms, click **I accept the terms in the License Agreement**, and then click **Next**.
5. On the Destination Folder page, take one of the following actions.
   * To install the VRA in the default location, click **Next**.
   * To install the VRA in another location, click **Change**. In the Change destination folder dialog box, browse to the new installation folder, or type it in the Folder name box. Click **OK**. On the Destination Folder page, click **Next**.
6. On the Register Agent with Portal Page, specify the following information.
   * In the **Network address** field, type `cloudbackupregister.service.softlayer.com`.
   * In the **Port** field, type `8086`.
   * In **Username** field, type the {{site.data.keyword.backup_notm}} user name for managing the VRA.
   * In **Password** field, type the password of the specified {{site.data.keyword.backup_notm}} user.
7.	Click **Next**. When the installation is complete, click **Finish**.

## Configuring the vSphere Recovery Agent
{: #configureVRA}

After VRA is installed, you need to configure it in the Cloud Backup Portal.

1. Log in to the Portal. For more information about how to access the Portal, see the [Getting started tutorial](/docs/Backup?topic=Backup-getting-started#accessingPortal).
2. On the Computers Tab, select the server that you want to back up.
3. Configure your vault information.

   Vault information can be configured in two ways: **Automatically** or **Manually**.<br/>If the agent is being configured for the first time, then it can be configured by using the [Automatic configuration](#VRAautoconfig) option.<br/>If the computer was previously registered with a Vault, then the automatic configuration doesn't work and the vault needs to be [configured manually](#VRAmanualconfig).
   {: tip}

4. Configure the [vCenter Settings](#vCenterSettingsconfig).   

### Configuring the Vault Automatically
{: #VRAautoconfig}

To configure the vault settings automatically, click **Configure Automatically**. The configuration Wizard runs and configures the Vault settings for you. When it is completed, click **Go To Agent** to verify the information in **Vault Settings** Tab.
 

### Configuring the Vault Manually
{: #VRAmanualconfig}

To configure the vault settings manually, click **Configure Manually**.   
1. Click **Vault Settings**.
2. Click **Add Vault**. The Vault Settings window appears. From the **Vault Profile** options, select the appropriate vault.
   If the computer was previously registered with an {{site.data.keyword.backup_notm}} vault, then all information is auto-populated when the Vault is selected from the Vault Profile.
   {:note}

3. Verify all the information in the Vault settings page, and click **Save**.
4. When you save the vault settings, the vault information becomes visible in the **Vault Settings** Tab.


### Configuring vCenter Agent settings
{: #vCenterSettingsconfig}

After the successful vault registration, the vCenter Settings need to be configured before you can create and run any backup jobs.

1. Click the **vCenter Settings** Tab.
2. Provide the vCenter IP address, domain name, and credentials for the vCenter that you want to protect.
   The user must have administrative access to the vCenter to perform this task successfully.
   {:note}

3. Disable Change Block Tracking (CBT) by removing the check mark. CBT is a VMware feature that tracks changed disk sectors and improves the performance of VM backups, and it is automatically enabled by the vSphere Agent.
4. Click **Test vCenter Connection**. A new window displays the results. If the provided login information is correct, “The vCenter credentials have been validated successfully” message appears.
5. Click **Save** to save the settings.

## Configuring a vSphere backup job
{: #configvmwarebackup}

For more information, see [Configure, schedule, and run a backup job](/docs/Backup?topic=Backup-ConfigureVRA#ConfigureVRA).

## Restoring vSphere data
{: #restoringvSphereData}

For more information, see [Restore vSphere data](/docs/Backup?topic=Backup-VRARestore#VRARestore).


Connect to the {{site.data.keyword.cloud}} network with {{site.data.keyword.BluVPN}} so that you can access and download the user guide from the [Downloadable {{site.data.keyword.backup_notm}} Documentation](http://downloads.service.softlayer.com/evault/Documentation/){: external}.
{:tip}
