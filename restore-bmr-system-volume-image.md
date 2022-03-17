---

copyright:
  years: 1994, 2021
lastupdated: "2021-10-20"

keywords: IBM Cloud backup,  EVault, Carbonite, backup, restore

subcollection: Backup

---
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:shortdesc: .shortdesc}

# Restoring a BMR system volume image
{: #restoreBMR}

If you need to restore a Bare Metal image backup from {{site.data.keyword.backup_full}}, you can quickly restore it from the BMR Rescue Kernel system. With BMR, you can restore the system without the need of a bootable operating system. It's useful when the operating system is no longer usable or the drives in the system were replaced.
{: shortdesc}

## Initiating the BMR Rescue Kernel system
{: #initiateBMR}

You can access the BMR Rescue Kernel system through the {{site.data.keyword.cloud_notm}} console.
1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}. From the Navigational menu, select **Classic Infrastructure**.
2. Click **Storage** > **Cloud Backup** to display the servers with backup service.
3. Click the **Arrow** next to the vault.
4. Click **Initiate Bare Metal Restore**. This action starts a transaction that takes a few minutes to complete. Afterward you can access the server by following the steps that are detailed here. You're going to be emailed when the system completes the boot process.


## Restoring from the BMR Rescue Kernel
{: #restorefromBMR}

1. When the BMR Rescue Kernel transaction loads, you can choose to access it in two different ways.
   - A VNC client and the private or public IP address of your server and the password that is listed in the {{site.data.keyword.cloud_notm}} console.
   - The KVM console of your IPMI card.
    Both of these ways work well.
2. Upon logging in to the BMR Rescue Kernel for the first time, you're greeted with the language selection screen. Select the time zone and keyboard language of your choice and click **Next**.
   ![Figure 1 - BMR time zone and keyboard language selections are displayed.](/images/bmr1.png){: caption="Figure 1. BMR time zone and keyboard language selections are displayed." caption-side="bottom"}
   The license agreement for the software is displayed.
3. If you accept the terms, select the check box, and click **Next** to continue. The main {{site.data.keyword.backup_notm}} system restore menu is presented.
4. Select **Restore My System**.
   ![Figure 2 - The BMR Main menu shows 4 options that are available to select.](/images/bmr2.png){: caption="Figure 2. The BMR Main menu shows 4 options that are available to select." caption-side="bottom"}
5. The system restore wizard appears. Select **Next** to continue.
   ![Figure 3 - BMR Wizard provides an overview of the 4 steps if the BMR restore process.](/images/bmr3.png){: caption="Figure 3. BMR Wizard provides an overview of the 4 steps if the BMR restore process." caption-side="bottom"}
6. Select a backup type to restore from. Select **EVault software** then click **Next** to continue.
7. On the **backup location** screen, select the vault, and enter in the vault address, account number, the user name, and password. Then, click **Next** to continue.
   ![Figure 4 - Choose backup location](/images/bmr4.png){: caption="Figure 4. Choose backup location." caption-side="bottom"}
   For more information about viewing the user name or changing the backup password, see [Managing user name and password for the Cloud Backup service](/docs/Backup?topic=Backup-changePassword).
   {: tip}

8. The next screen displays your system in the list. Make sure it is highlighted and click **Next**.
   ![Figure 5 - Choose your system](/images/bmr5.png){: caption="Figure 5. Choose your system.]" caption-side="bottom"}
9. On the **backup job selection** screen, select the Job that you want to restore from and click **Next**.
   ![Figure 6 - Choose your Restore point](/images/bmr6.png){: caption="Figure 6. Choose your Restore point." caption-side="bottom"}
10. From the **Select Restore Point** menu, select the restore point that you want and click **Next**.
   ![Figure 7 - Choose Restore Point](/images/bmr8.png){: caption="Figure 7. Choose Restore Point." caption-side="bottom"}
11. Select the source and destination volumes. To restore the source to the destination, drag the source volume onto the destination volume.
   ![Figure 8 - Select Source and Destination Volumes](/images/bmr9.png){: caption="Figure 8. Select Source and Destination Volumes." caption-side="bottom"}
12. On the format or merge data confirmation box, you can select from two options. Select **Format** for a clean restore that formats the disk. If you want to merge the data on the destination volume, select **Merge**.
   ![Figure 9 - Choose Merge](/images/bmr10.png){: caption="Figure 9. Choose Merge." caption-side="bottom"}
13. On the main source and destination volume screen, click **Next**.
14. On the restore plan summary screen, check the box to accept the plan and click **Next**.
   ![Figure 10 - Start the restore](/images/bmr11.png){: caption="Figure 10. Start the restore." caption-side="bottom"}
15. The restore progress screen appears and it shows you the progress of the restoration as it happens.
   ![Figure 11 - Restore Progress](/images/bmr12.png){: caption="Figure 11. Restore in Progress." caption-side="bottom"}
16. When complete, you receive a notification window that states that the restore was completed successfully. Click **OK**.
17. On the restore progress screen. Click **Next**.
18. On the final screen, check the box for restart system and select **Finish** and the server loads your restored volume image.
    The restoration is now complete.

    The first time the server restarts you might see the unexpected shutdown message. It's normal with this backup type and goes away after the first boot.
    {: tip}
