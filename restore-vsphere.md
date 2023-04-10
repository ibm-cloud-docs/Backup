---

copyright:
  years: 1994, 2023
lastupdated: "2023-04-10"

keywords: IBM Cloud Backup, VMware, VRA, vSphere Recovery Agent, plug-in, plugin, EVault, Carbonite, vSphere, backups

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Restoring vSphere data
{: #VRARestore}

When VMs are protected in vSphere environment, you can restore [vSphere virtual machines](#restoreVMs), and [restore files and folders]( #restoreFFVRA) with the vSphere Recovery Agent.
{: shortdesc}

## Restoring vSphere VMs
{: #restoreVMs}

1.	On the navigation bar, click **Computers**. A grid lists available computers.
2.	Find the vSphere environment with the VM that you want to restore, and expand its view by clicking the row.
3.	Click **Jobs**.
4.	Find the backup job with the VM that you want to restore, and click **Restore** in the job’s **Select Action** menu.
5.	In the **Choose what you want to restore** dialog box, select **Virtual machines**.
6.	Click **Continue**. The Restore dialog shows the most recent safe-set for the job.
    * To restore data from another source, click a source (vault) in the **Source Device** List.
    * To restore from an older safe-set, click **Browse safe sets**. In the calendar that appears, click the date of safe-sets from which you want to restore.
7.	In the **Items to Restore** panel, select each VM that you want to restore.
8.	In the **Encryption Password** field, type the data encryption password.
9.	In the **Destination Datastore** list, click the VMware datastore for the restored VMs.
10.	Select one of the following options for restoring VMs to the VMware datastore that you selected:
    * **Restore all selected virtual machines to the selected datastore only.**
    * **Restore to the selected datastore only when a virtual machine’s original datastore is not available.** If the VM's backup contains multiple VMDKs that resided on multiple VMware datastores, and not all of the datastores are available, the entire VM is restored to the selected VMware datastore.

    If you restore a VM or template to a vCenter, and the original VM is present, the VM is restored as a clone of the original with the following name: `<VMname>-vra-restored-<Date>`. The VM is restored as a clone if the original VM is powered on, off, or suspended. If the original VM is powered on, and uses a static IP address, you can encounter an IP address conflict when the restored, cloned VM is powered on.
    {: note}

11.	In the **Destination Host** list, click the host where you want to register the VMs. The list shows only the hosts that have access to the selected VMware datastore.
12.	Select one of the following options for registering the restored VMs with the hosts that you selected:
    * **Register all selected virtual machines with the selected hosts only.**
    * **Register with the selected hosts only when a virtual machine’s original hosts is not available.**
13.	To power on the VMs after they are restored, select **Power VMs on after restoring**.
14.	In **Performance options**, keep the default setting.
15.	Click **Run Restore**.

## Restoring files and folders
{: #restoreFFVRA}

You can restore file and folders from a protected Windows&reg; VM by using the vSphere Recovery Agent (VRA). You can restore files and folders from more than one VM at same time. You can't restore files and folders from Linux&reg; VMs with VRA.
{: important}

During a files and folder restore, volumes from the selected VM are mounted as drives on the server where the VRA is running. You can then share some or all of the mounted drives so that users can copy files and folders from the drives. You can also sign in to the VRA server, and copy files and folders from the mounted drives.

Files and folders on the disks are accessible to anyone on the VRA system, including non-Admin users. If you're concerned about security, secure the Agent server and prevent users from logging in to the server locally.
{: tip}

1. On the navigation bar, click **Computers**. The grid lists available computers.
2. Find the vSphere environment with the VM that you want to restore, and expand its view by clicking the row.
3. Click **Jobs**.
4. Find the backup job with the VM that you want to restore, and click **Restore** in the job’s **Select Action** menu.
5. In the **Choose what you want to restore** dialog, select **Files and Folders**.
6. Click **Continue**. The restore dialog shows the most recent safe-set for the job.
    * To restore data from another resource, click source in the Source Device list (Vault).
    * To restore from an older safe-set, click Browse safe sets. In the calendar that appears, click the date of the safe-set from which you want to restore. Then, click the specific safe-set from which you want to restore.
7. In the **Items to Restore** panel, select the VM with the files or folders that you want to restore.
8. In the **Encryption Password** field, enter the data encryption password.
9. In the **Idle Time field**, enter the number of minutes of inactivity after which the share drive is to automatically unshare. The Idle time can range 2 - 180 minutes.

    The drive does not unshare while new data is being copied. If you copy the same data from a shared drive more than once, the system might timeout because no new data is being read.
    {: note}

10.	In **Performance options**, select Use all available bandwidth.
11.	Click **Run Restore**.
12. The restored volumes from the selected VM are mapped as drives on the server where the VRA is running, and are available in a Restore Mount folder. Take one of the following steps.
    * Copy files and folders that you want to restore from mapped drives.
    * Share one or more mapped drives with other users. Users can then access the UNC share, and copy files and folders that they want to restore.
    * Share one or more directories from the Restore Mount folder on the VRA server. Users can then access the UNC share, and copy files and folders that they want to restore.
