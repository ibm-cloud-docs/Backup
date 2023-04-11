---

copyright:
  years: 1994, 2023
lastupdated: "2023-01-11"

keywords: IBM Cloud backup, EVault, Carbonite, backup, multiple vaults, mulitple locations, disaster recovery

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}{{site.data.keyword.attribute-definition-list}}

# Multi-vaulting
{: #multivault}

Multi-vaulting is the ability for a client to connect a server to more than one vault location. It provides redundancy and peace of mind because backups are available even if one site fails.
{: shortdesc}

- **Key points**

   1. Multiple vaults can be managed through the same Cloud Backup Portal and they are handled the same way. The only difference is that you have different vault choices.
   2. The new vault needs to be manually added to the Cloud Backup Portal after each purchase.


- **{{site.data.keyword.backup_notm}} Vault Director locations**

   Multi-vaulting is available across all data centers without any geographical limitations in selecting a remote vault. When vaults are configured correctly, all the configured vaults appear in vault settings.

   Backing up to remote data center locations can take longer than backups to the same data center where your server is located.
   {: note}

## Adding a Remote Vault to an Account
{: #addremotevault}

You must add the new remote vault to the account before a new backup location can be added in the Cloud Backup Portal.
{: important}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Devices**.
3. Locate and click the link for the server in question.
4. Under **Device Details**, click **Storage**.
5. When the Storage section opens up, scroll down to **{{site.data.keyword.backup_notm}}**, and click **Add**.
6. In the **Order {{site.data.keyword.backup_notm}}** window, select the remote vault location.
7. Select the size of the storage, then click **Continue**.
8. Click the checkbox to show that you agree with the terms and conditions, and click **Place Order**.

The newly ordered vault is automatically added to the account. If not, contact Sales for help.

When the ordering process is complete, go to the **Storage** > **Backup** page to see the new vault.

## Adding an Extra Vault in Cloud Backup Portal
{: #addanothervault}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](/login){: external}. From the menu ![Menu icon](../icons/icon_hamburger.svg "Menu"), select **Classic Infrastructure** ![Classic icon](../icons/classic.svg "Classic").
2. Click **Storage** > **Cloud Backup** to display the backup services.
3. Select the instance name of the {{site.data.keyword.cloud_notm}} account.
4. Click **View backup portal** to start the portal in your browser.

   Cloud Backup Portal is only accessible through [{{site.data.keyword.BluVPN}}](https://www.ibm.com/cloud/vpn-access){: external}.
   {: tip}

5. On the navigation, click **Computers**. The computers page shows the registered computers and environments. Expand the computer that you want to back up to a second vault.
6. Click **Vault Settings**.
7. In the **Vault Settings** window, click **Add Vault**.
8. In the **New Vault** window,
   1. In the Vault Profile menu, choose **Enter Vault Settings** to create a new entry. Don't update the existing entry, it doesn't work.
   2. The vault name can't be the same as the other vault name. Try adding a `-2` tag to the end of it.

       The vault name field has a 15 character limit.
       {: important}

   3. In the IP address field, add the address of the second {{site.data.keyword.backup_notm}} vault location.

       You can look up the fully qualified domain name of the {{site.data.keyword.backup_notm}} vault in the [{{site.data.keyword.cloud_notm}} console](/login){: external}. You can either use the FQDN or the IP address of the server to connect to the vault. To get the IP address, ping the FQDN from the server that's going to be backed up. For example, if you want to connect to the vault in a data center located in Dallas, you can use `ev-vaultdal1201.service.softlayer.com` or its IP address `10.200.134.250`.
      {: tip}

   4. In the credentials field, enter the account ID, the {{site.data.keyword.backup_notm}} username for the selected vault, and the password for the selected vault.
      For more information about viewing the username or changing the backup password, see [Managing username and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
      {: tip}

   5. Click **Save**.

In a few seconds, the new vault is usable. If you get a connection failure, check your settings, and try again. Keep in mind that adding an extra vault presents you with an extra destination to choose for a job. It doesn't automatically run jobs against both vaults. You need to set up jobs to use the extra vault. For more information, see the [Getting Started Tutorial](/docs/Backup?topic=Backup-getting-started#getting-started).
