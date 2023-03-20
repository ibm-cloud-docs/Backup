---

copyright:
  years: 1994, 2023
lastupdated: "2023-01-11"

keywords: IBM Cloud backup, EVault, Carbonite, backup, upgrade agent, Linux

subcollection: Backup

---
{{site.data.keyword.attribute-definition-list}}

# Upgrading backup software agent for Linux
{: #UpgradeinLinux}
{: help}
{: support}

Any agent that's older than the 8.63 version needs to be upgraded. Agents that are older than the 8.63 version cannot connect with the Backup portal due to outdated, unsupported TLS version. Following the upgrade process ensures that you can upgrade your {{site.data.keyword.backup_notm}} agent without losing the registration.
{: shortdesc}

The most recent backup agent can be downloaded from your Cloud Backup Portal Dashboard quick links section.
{: tip}

1. Log in to your host at root level.
2. Download the latest version of the agent.
    ```sh
    wget -N downloads.service.softlayer.com/evault/Agent-Linux-x64-8.83.8124.tar.gz
    ```
    {: pre}

3. Extract the contents of the downloaded file.
    ```sh
    tar -xzvf Agent-Linux-x64-8.83.8124.tar.gz
    ```
    {: pre}

4. Go to the recent installation directory.
    ```sh
    cd Agent-Linux-x64-8.83.8124/
    ```
    {: pre}

5. Run installation script.
    ```sh
    ./install.sh
    ```
    {: pre}

6. Answer the first prompt by selecting your language. Then, if the current agent is registered in the Backup portal, select `N` for not registering the computer as a new host. If the current agent is not registered in the Backup portal, select `Y` complete the registration and provide the [Portal address](/docs/Backup?topic=Backup-portinfo#commercial-portal-servers), {{site.data.keyword.backup_notm}} user ID and password. Lastly, select `A` to encrypt data by using the Integrated encryption method.

7. If the installation is successful, it is recorded in `/opt/BUAgent/Install.log`.
