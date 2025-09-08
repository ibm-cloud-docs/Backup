---

copyright:
  years: 1994, 2025
lastupdated: "2025-09-08"

keywords: IBM Cloud backup, EVault, Carbonite, IBM Cloud backup, Enterprise backup, billing, pricing,

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Provisioning {{site.data.keyword.backup_notm}}
{: #ordering}

Backups make sure that your data is safely stored outside of your device and stays protected. {{site.data.keyword.backup_full}} is an automated agent-based backup system that is managed through the Cloud Backup Portal browser-based management utility. You can provision your {{site.data.keyword.backup_full}} instance in the console, from the CLI, with the API, or Terraform. The first 10 GB of vault space is provided at no cost to you.
{: shortdesc}

Each server must have its own {{site.data.keyword.backup_notm}} instance. One {{site.data.keyword.backup_notm}} license cannot be used for multiple servers.
{: important}

## Provisioning {{site.data.keyword.backup_notm}} in the console
{: #ordering-ui}
{: ui}

You can provision {{site.data.keyword.backup_notm}} service in two ways in the console.
* [Provision backup space when you order a server](#purchasingwithserver-ui).
* [Provision backup space as an upgrade](#purchasingasupgradeui).

### Provisioning {{site.data.keyword.backup_notm}} when you order a server
{: #purchasingwithserver-ui}

1. Log in to the [{{site.data.keyword.cloud_notm}} catalog](/catalog){: external}.
2. Order a monthly virtual server. For more information about {{site.data.keyword.BluVirtServers}}, see [Provisioning a virtual server](/docs/virtual-servers?topic=virtual-servers-getting-started-tutorial#provisioning-a-virtual-server-getting-started){: external}.
   1. Enter host and domain names. You can choose any hostname and domain that you like.
   1. Select quantity and billing option.

       {{site.data.keyword.backup_notm}} service isn't available when you're ordering an hourly billed server. However, the service can be added later as an upgrade.
       {: note}

   1. Select a location.
   1. Select Server profile and OS Image type. You can also choose multiple add-ons.
   1. Under **Network Interface**, select the Uplink Port Speed and any add-ons that you want.
   1. In the **Storage Disks** section, specify the size of the boot volume and add more disks if you want to.
   1. Under **Add-ons**, and select **{{site.data.keyword.backup_notm}}**. Choose the option that matches what you need.
   
      The first 10 GB of vault space is provided at no cost to you. If you don't know how much backup storage you need, provision 10 GB, and you can add more storage later.
      {: tip}

3. Review your order, and read the service agreements. If you agree with the terms, check the box.
4. Click **Create**. The Device list is displayed and in a few minutes, your virtual server is ready for use.
5. When your virtual server is provisioned, click the hostname to display the Device details page.
6. In the side navigation, click **Storage**. Then, scroll to {{site.data.keyword.backup_notm}} to see the details.

You can also save the order without purchasing by clicking **Save as Quote**.
{: note}

### Provisioning {{site.data.keyword.backup_notm}} as an upgrade
{: #purchasingasupgradeui}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Infrastructure**  ![VPC icon](../icons/vpc.svg) > **Classic Infrastructure**.
1. Select **Devices** > **Device List** from the main menu. Find the device for which you want to add the backup service.
1. Click the Device name to go to the **Device Details** page.
1. Click the **Storage** tab, and scroll down to locate the {{site.data.keyword.backup_notm}} section.
1. Click the **Add cloud backup** link.
1. In the window, select a location, and select a size.
1. Enter the **Promo Code** if you have one, and click **Recalculate**.
1. Review your order, and click the link to read the terms and conditions.
1. Click the checkbox if you agree with the terms and conditions.
1. Click **Create**.
1. Return to the Device details page of your server, and click **Storage**. The new vault is listed in the {{site.data.keyword.backup_notm}} section.

If the backup storage size continues to show a capacity of zero, a second page refresh might be needed.
{: tip}

## Provisioning {{site.data.keyword.backup_notm}} from the CLI
{: #ordering-cli}
{: cli}

Before you begin, you must install the IBM Cloud CLI. For more information, see the [Getting started with the IBM Cloud CLI](/docs/cli?topic=cli-getting-started) tutorial.
{: requirement}

You can provision backup space when you order a server, and you can order the {{site.data.keyword.backup_notm}} service as an upgrade. The following example command orders a monthly VSI with 4 CPU, 16 GB RAM, 100 GB SAN disk, Ubuntu 18.04, and 1 Gbps public and private uplink in data center DAL13. It also provisions 20 GB of vault space for backups. The system prompts for confirmation as this action incurs charges. Type `y` and press Enter to continue.

```sh
$ ibmcloud sl order place CLOUD_SERVER DALLAS13 GUEST_CORES_4,RAM_16_GB,REBOOT_REMOTE_CONSOLE,1_GBPS_PUBLIC_PRIVATE_NETWORK_UPLINKS,BANDWIDTH_0_GB_2,1_IP_ADDRESS,GUEST_DISK_100_GB_SAN,OS_UBUNTU_18_04_LTS_BIONIC_BEAVER_LAMP_64_BIT,MONITORING_HOST_PING,NOTIFICATION_EMAIL_AND_TICKET,AUTOMATED_NOTIFICATION,UNLIMITED_SSL_VPN_USERS_1_PPTP_VPN_USER_PER_ACCOUNT,NESSUS_VULNERABILITY_ASSESSMENT_REPORTING,EVAULT_20_GB --billing monthly --extras '{"virtualGuests": [{"hostname": "test", "domain": "softlayer.com"}]}' --complex-type SoftLayer_Container_Product_Order_Virtual_Guest
This action will incur charges on your account. Continue?> y
       
ID        105021440
Created   2023-04-24T20:04:57Z
Status    PENDING_AUTO_APPROVAL
```
{: codeblock}

For more information, see [ibmcloud sl order place](/docs/cli?topic=cli-sl-manage-classic-orders).

## Provisioning {{site.data.keyword.backup_notm}} with Terraform
{: #ordering-terraform}
{: terraform}

To use Terraform, download the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in. For more information, see the [Getting started with Terraform](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started) tutorial.
{: requirement}

Use the `ibm_storage_evault` resource to create or update your {{site.data.keyword.backup_full}} instance. The following example creates a 20-GB vault in the DAL13 data center. The `virtual_instance_id` defines the server that is going to be backed up in this vault.

```terraform
resource "ibm_storage_evault" "test" {
  datacenter          = "dal13"
  capacity            = "20"
  virtual_instance_id = "137028172"
}
```
{: codeblock}

For more information about arguments and attributes, see [ibm_storage_evault](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/storage_evault){: external}.

## Next Steps
{: #ordering-next-steps}

When you're ready, install the software agent on the server and set up your backup schedule in the Cloud Backup Portal. For more information, see the [Getting started tutorial](/docs/Backup?topic=Backup-getting-started#getting-started).
