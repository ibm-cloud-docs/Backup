---

copyright:
  years: 1994, 2019
lastupdated: "2019-11-11"

keywords: IBM Cloud backup, EVault, Carbonite, backup, expanding vault

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}


# Expanding vault capacity
{: #expandcapacity}

Current {{site.data.keyword.cloud}} users are able to expand the size of their vault up to 4000 GB. They don't need to create a duplicate or manually migrate data to a larger volume. The limit increase process does not cause any outage or lack of access.
{: shortdesc}

## Ordering an increase
{: #increasevault}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Select the vault that you want to extend.
4. Click **Actions**, and select **Modify {{site.data.keyword.backup_notm}}**.
5. On the next screen, select the new size and click **Upgrade**.

## Billing
{: #changeinbilling}

Billing for the volume is automatically updated to add the pro-rated difference of the new price to the current billing cycle. Then, the full new amount is billed in the next billing cycle.

The same process can be used to downsize your {{site.data.keyword.backup_notm}}.
{: tip}
