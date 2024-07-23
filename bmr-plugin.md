---

copyright:
  years: 1994, 2024
lastupdated: "2024-07-23"

keywords: IBM Cloud backup, bare metal restore, bmr, plug-in, plugin, EVault, Carbonite, baremetal, point-in-time restore

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Getting started with the Bare Metal Restore plug-in
{: #BMRplugin}

Bare Metal Restore is a disaster recovery solution. You can use BMR to restore your server from a bare metal state after a disaster, such as an operating system or hardware failure. With BMR, you can quickly restore the system image from a safe, secure location that is managed by {{site.data.keyword.cloud}}.
{: shortdesc}

BMR is a Windows&reg;-only product on physical servers. It is not available for virtual servers. Bare Metal Restores for Linux&reg; distributions aren't supported.
{: important}

## Capabilities provided
{: #BMRcapabilities}

- Restore your system to a selected point in time.
- Restore your system from image or file-based backups.
- Restore your system from backups that are stored on the {{site.data.keyword.backup_notm}}.
- Start a recovery transaction that you can use to restore your data without a bootable system.

## Installing the BMR plug-in
{: #installingBMR}

The plug-in is installed during the Windows Agent installation. The plug-in can be installed at the same time as the Agent or it can be installed later, by rerunning the installation with the **Modify** selection.

## Configuring BMR backup job
{: #configBMRplugin}

For more information, see [Configuring BMR backup jobs](/docs/Backup?topic=Backup-configureBMR).

## Restoring a BMR system volume image
{: #restoringBMimage}

For more information, see [Restoring a BMR system volume image](/docs/Backup?topic=Backup-restoreBMR).

