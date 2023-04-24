---

copyright:
  years: 1994, 2023
lastupdated: "2023-04-24"

keywords: IBM Cloud backup, EVault, Carbonite, IBM Cloud backup, Enterprise backup, billing, pricing,

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Provisioning {{site.data.keyword.backup_notm}}
{: #ordering}

Backups ensure that your data is safely stored outside of your device and stays protected. {{site.data.keyword.backup_full}} is an automated agent-based backup system that is managed through the Cloud Backup Portal browser-based management utility. You can provision your {{site.data.keyword.backup_full}} instance in the UI, from the CLI, with the API, or Terraform.
{: shortdesc}

Each server must have its own {{site.data.keyword.backup_notm}} account. One {{site.data.keyword.backup_notm}} license cannot be used for multiple servers.
{: important}

## Provisioning {{site.data.keyword.backup_notm}} in the UI
{: #ordering-ui}
{: ui}

You can provision {{site.data.keyword.backup_notm}} service in two ways in the console.
* [Provision backup space when you order a server](#purchasingwithserver).
* [Provision backup space as an upgrade](#purchasingasupgrade).

### Purchasing {{site.data.keyword.backup_notm}} when you order a server
{: #purchasingwithserver-ui}

1. Log in to the [{{site.data.keyword.cloud_notm}} catalog](/catalog){: external}.
2. Order a monthly Bare Metal Server. For more information about ordering bare metal servers, see [Building a custom Bare Metal Server](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server){: external}.
   1. Select quantity, billing option. Enter host and domain names. You can choose any hostname and domain that you like.

      {{site.data.keyword.backup_notm}} service isn't available when you're ordering an hourly billed server. However, the service can be added later as an upgrade.
      {: tip}

   2. Select location.
   3. Select Server configuration and OS Image type. You can also choose multiple add-ons.
   4. Under the **Storage Disks** section, click **Add-ons**, and select **{{site.data.keyword.backup_notm}}**. Choose the option that matches what you need.
   5. Under **Network Interface**, select the Uplink Port Speed and any add-ons that you want.
3. Next, review your order summary.
4. Review your order, and read the service agreements. If you agree with the terms, check the box.
5. Click **Provision**. You are redirected to a screen with your provisioning order number. You can print the screen because it's also your provisioning order receipt.

You can also save the order without purchasing by clicking **Save as Quote**.
{: tip}

A series of emails is sent to your administrator: Acknowledgment of the provisioning order, Provisioning order approval and processing, and Provisioning complete. The Provisioning complete email includes a link to your *Device Details* page, that you can access after you log in to {{site.data.keyword.cloud_notm}}. You can also log directly in to the {{site.data.keyword.cloud_notm}} console.

#### Confirming the {{site.data.keyword.backup_notm}} purchase
{: #confirmpurchase1}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Device** > **Device List**.
3. Locate the new server that you ordered.
    - If you see a clock icon next to the url, you need to wait to continue with the {{site.data.keyword.backup_notm}} purchase confirmation. You can refresh the page to see an updated status on your new server. When the clock icon is no longer present, you can proceed with the next steps to confirm the purchase.
    - When the clock icon is no longer showing for your server, click the link (the server's url) to go to the **Device Details** page.
4. Click the **Storage** tab to display the {{site.data.keyword.backup_notm}} information.
5. Inspect the information, and verify that the size that was selected during the purchase process is displayed.

### Purchasing {{site.data.keyword.backup_notm}} as an upgrade
{: #purchasingasupgradeui}

#### Select a server on which to install {{site.data.keyword.backup_notm}}
{: #selectbaseserver}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Select **Devices** > **Device List** from the main menu. Find the device for which you want to add the backup service.
3. Click the Device name to go to the **Device Details** page.

#### Adding {{site.data.keyword.backup_notm}} service
{: #addbackupservice}

1. Click the **Storage** tab, and scroll down to locate the {{site.data.keyword.backup_notm}} section.
2. Click the **Add** link.
3. In the window, select a location, and select a size.
4. Select Payment type, and click **Continue**.
5. Enter the **Promo Code** if you have one, and click **Recalculate**.
6. Review your order, and click the link to read the terms and conditions.
7. Click the checkbox if you agree with the terms and conditions.
8. Click **Place Order**.

#### Confirming the {{site.data.keyword.backup_notm}} upgrade
{: #confirmpurchase2}

1. Refresh the **Device Details** page, and ensure that the **Storage** tab is selected.
2. Inspect the {{site.data.keyword.backup_notm}} section and verify that the size that was selected during the purchase process is displayed.

   If the backup storage size continues to show a capacity of zero, a second page refresh might be needed.
   {: tip}

## Provisioning {{site.data.keyword.backup_notm}} from the CLI
{: #ordering-cli}
{: cli}

Before you begin, you must install the IBM Cloud CLI. For more information, see [Getting started with the IBM Cloud CLI](https://cloud.ibm.com/docs/cli?topic=cli-getting-started).
{: requirement}

You can provision backup space when you order a server, and you can order the {{site.data.keyword.backup_notm}} service as an upgrade. The following example command orders a monthly VSI with 4 CPU, 16 GB RAM, 100 GB SAN disk, Ubuntu 18.04, and 1 Gbps public and private uplink in data center DAL13. It also provisions 20 GB of vault space for backups. The system prompts for confirmation as this action incurs charges. Type `y` and press enter to continue.

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

To use Terraform, download the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in. For more information, see [Getting started with Terraform](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).
{: requirement}

Use the `ibm_storage_evault` resource to create or update your {{site.data.keyword.backup_full}} instance. The following example creates a 20-GB vault in DAL13 data center. The `virtual_instance_id` defines the server that is going to be backed up in this vault.

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

When you're ready, install the software agent on the server and set up your backup schedule in the Cloud Backup Portal. For more information, see [Getting started tutorial](/docs/Backup?topic=Backup-getting-started#getting-started).
