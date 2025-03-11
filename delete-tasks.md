---

copyright:
  years: 1994, 2025
lastupdated: "2025-03-11"

keywords: IBM Cloud backup, EVault, Carbonite, backup, delete jobs

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Deleting backup tasks
{: #deletetasks}
{: help}
{: support}

A backup job specifies which data to back up on a system, specifies where to save the data, and contains other backup settings. A backup task is the data that is stored in the vault. You can delete backup jobs from online servers without deleting the job data from vaults from the Cloud Backup Portal, so you can use the data later to restore a server. To delete the entire task from the vault, follow these instructions.
{: shortdesc}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
1. Click **Storage** > **Cloud Backup** to display the backup services.
1. Select the instance name of the {{site.data.keyword.cloud_notm}} Account.
1. Click **Backup** on the Cloud Backup details page. Jobs and Tasks information is displayed. 

   For example, each virtual machine in a Hyper-V backup job is backed up as a separate task on the vault, and is automatically assigned a unique task name. To help you find each task on the vault, you can view the task name for each protected Hyper-V virtual machine in the Cloud Backup Portal. The task name for each virtual machine is shown on the virtual machines screen for a Hyper-V Agent. In previous Portal versions, the task name appeared in a tooltip if you pointed to the virtual machine name.
   {: note}

1. Locate the task that you want to delete from the vault. Click the Subtract icon ![Subtract icon](../icons/subtract-alt.svg "Subtract") to remove the data from the vault. 
   
   Backup data deletion is permanent. After the data is deleted from vaults, it cannot be recovered or restored.
   {: attention}

   If you want to delete a specific data set and not the entire task, you need to raise a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external}. For more information, see the [FAQs](/docs/Backup?topic=Backup-faqs&interface=ui#deletesafeset).
   {: tip}
