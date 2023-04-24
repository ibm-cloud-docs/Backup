---

copyright:
  years: 1994, 2023
lastupdated: "2023-04-24"

keywords: IBM Cloud backup, EVault, Carbonite, backup, expanding vault

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}


# Expanding vault capacity
{: #expandcapacity}

Current {{site.data.keyword.cloud}} users are able to expand the size of their vault up to 4000 GB. They don't need to create a duplicate or manually migrate data to a larger volume. The limit increase process does not cause any outage or lack of access.
{: shortdesc}

## Ordering an increase in the UI
{: #increasevault-ui}
{: ui}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Select the vault that you want to extend.
4. Click **Actions**, and select **Modify {{site.data.keyword.backup_notm}}**.
5. On the next screen, select the new size and click **Upgrade**.


## Ordering an increase with Terraform
{: #increasevault-terraform}
{: terraform}

To use Terraform, download the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in. For more information, see [Getting started with Terraform](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).
{: requirement}

Use the `ibm_storage_evault` resource to update your {{site.data.keyword.backup_full}} instance. The following example increases the vault capacity to 100 GB when it is applied. 

```terraform
resource "ibm_storage_evault" "test" {
  datacenter          = "dal13"
  capacity            = "100"
}
```
{: codeblock}

For more information about arguments and attributes, see [ibm_storage_evault](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/storage_evault){: external}.


## Billing
{: #changeinbilling}

Billing for the volume is automatically updated to add the pro-rated difference of the new price to the current billing cycle. Then, the full new amount is billed in the next billing cycle.

The same process can be used to downsize your {{site.data.keyword.backup_notm}}.
{: tip}
