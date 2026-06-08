---

copyright:
  years: 1994, 2026
lastupdated: "2026-06-08"

keywords: IBM Cloud backup, bare metal restore, bmr, plug-in, plugin, EVault, Carbonite, baremetal, point-in-time restore, create bmr backup

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Getting started with the Bare Metal Restore plug-in
{: #BMRplugin}

Protect Windows bare metal servers with {{site.data.keyword.backup_notm}} Bare Metal Restore (BMR) plug-in for disaster recovery from OS or hardware failures.
{: shortdesc}

BMR is a Windows&reg;-only product on physical servers. It is not available for virtual servers. Bare metal restorations for Linux&reg; distributions aren't supported.
{: important}

## Capabilities provided
{: #BMRcapabilities}

- Restore your Windows system to a selected point in time.
- Restore your system from an image or file-based backups.
- Restore your system from backups that are stored on the {{site.data.keyword.backup_notm}}.
- Start a recovery transaction that you can use to restore your data without a bootable system.

## Installing the BMR plug-in
{: #installingBMR}

The plug-in is installed during the Windows Agent installation. The plug-in can be installed at the same time as the Agent or it can be installed later, by rerunning the installation with the **Modify** option.

## Configuring BMR backup job
{: #configBMRplugin}

For more information, see [Configuring Bare Metal Restore backup jobs](/docs/Backup?topic=Backup-configureBMR).

## Restoring a BMR system volume image
{: #restoringBMimage}

For more information, see [Restoring Bare Metal systems with {{site.data.keyword.backup_notm}}](/docs/Backup?topic=Backup-restoreBMR).
