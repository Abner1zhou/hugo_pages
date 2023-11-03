---
title: 更换Unraid U盘
slug: replace-the-unraid-u-disk-dk8dm
url: /post/replace-the-unraid-u-disk-dk8dm.html
date: '2023-11-03 15:08:58'
lastmod: '2023-11-03 17:33:39'
toc: true
tags:
  - Resources/Nas
categories:
  - daily note
  - '-11-03'
keywords: Resources/Nas
isCJKLanguage: true
---

# 更换Unraid U盘

> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [docs.unraid.net](https://docs.unraid.net/unraid-os/manual/changing-the-flash-device/)

> Replacing your Unraid USB Flash Device transfers the license to a new USB Flash Device. Once this is ......

caution

Replacing your Unraid USB Flash Device transfers the license to a new USB Flash Device. Once this is done, the previous Flash device is *blacklisted* and cannot be used with Unraid going forward. This action cannot be undone.

> 注意：一旦更换U盘，原来的U盘就会被加入黑名单

The USB flash device used to boot up Unraid contains the operating system and your configuration. If this device fails or is about to fail, you are at risk of losing data and your system configuration. It is important to understand when and how to replace your USB flash device. The process by which you replace your USB flash device and transfer its content, configuration, and your Unraid OS license is detailed in this article, along with recommendations on your choice of new USB flash device.

Why replace your USB flash boot device?

---

There are numerous reasons for which you may need to replace your USB flash device containing Unraid OS, preventing data loss and minimizing downtime for your Unraid server. The most common ones include:

> 为什么需要更换U盘？
>
> * U盘坏了
> * U盘丢了
> * U盘太慢了或者空间不足、空间太多（浪费空间了）

* The device is failing or has failed - the server refuses to boot, files are disappearing from the USB device, or the device repeatedly goes into read-only mode.
* The device has been lost or stolen - you have misplaced your USB flash device, or it has been stolen.
* The device is too slow or does not have enough storage - while 2 GB should be more than enough space, it is possible that your device fills up with data, or becomes increasingly slow to access.
* The device is physically too large - you want to replace the USB flash device with a smaller, more compact unit to fit a constrained space.

### What kind of USB device do I need?

USB flash devices have become almost universal across store shelves. They come in different capacities, have different USB protocols, read and write data at varying speeds, come in all shapes and sizes and, most importantly, have different lifespans.

Like most servers, this particular piece of hardware should focus on durability and reliability. Unlike most server hardware, speed is not a primary concern for Unraid, as it runs from RAM once booted. Based on our experience:

* USB 2.0 devices are typically recommended over USB 3.0 as they tend to be more reliable and universally recognized by computers.
* The USB device must contain a GUID in its programmable ROM.
* Capacity is not a key factor, but the USB device should have 2 GB minimum size, and 32 GB maximum, in the current version of Unraid.
* Physical size is only relevant when it comes to your server's physical location and setup.
* Using a reputable brand, from a reputable vendor, offers some reassurance of durability, but not every vendor is the same.

‍

### Before you replace your USB flash device

---

Before replacing the current flash device, it may be worthwhile to carry out some diagnostics.

Shut down your server, securely remove the flash device, and insert it into a Windows or Mac computer. Using Windows Scandisk or Disk Utilities on Mac, you should be able to try to identify errors or even repair the data on the device. A common scenario for this is if you recently experienced a power outage. A power outage will cause delayed write operations to be incomplete, resulting in misallocated data on the device. This can usually be fixed with the method above.

If the disk maintenance operation works, you may want to consider continuing the use of the flash device as it is not currently failing. However, if you've done this before and are still having issues with your flash device, then replacement is recommended.

### Recommendations on buying USB drives

The first step is to acquire a new USB flash device. We recommend that you always buy USB drives from reputable retailers and do your best to avoid internet marketplaces or use second-hand devices, as these do not offer the necessary guarantees that your device meets the criteria to boot and maintain Unraid operations over the course of time.

Even well-known brands have been the target of counterfeiting by malicious actors. Please see [this forum announcement](https://forums.unraid.net/topic/119052-psa-on-sandisk-usbs/) on the matter of counterfeit SanDisk USB drives on the market. Due to this, at this time, we cannot officially recommend SanDisk USBs due to the issue of generic GUIDs found in knock-off / counterfeit units.

Replace the USB flash device

---

There are two ways to swap out your USB flash device. If you are using a PC or Mac, you should use the [USB Flash Creator tool](https://unraid.net/download) for the easiest and most streamlined experience. The second method, if you are using a Linux system or if the USB Flash Creator tool is not working for some reason, is to [use the legacy method](#manual-method).

### Backing up your flash drive

The next step is to create a full backup of your original Unraid OS USB flash boot device. It is <span style="font-weight: bold;" data-type="strong">highly recommended</span> that you always have an up-to-date backup of your Unraid USB flash device.

> 先备份原来的设备，然后还原到新的U盘上面

#### Back up your USB device using the Unraid WebGUI

To back up your Flash drive in Unraid:

1. In the  <span style="font-weight: bold;" data-type="strong">_Main_</span>  tab select the <span style="font-weight: bold;" data-type="strong">Flash</span> device from the boot device list.
2. Under <span style="font-weight: bold;" data-type="strong">Flash Device Settings</span>, select the <span style="font-weight: bold;" data-type="strong">FLASH BACKUP</span> button to download a fully zipped backup of your current flash drive to your Mac or PC. ![](http://127.0.0.1:6806/assets/net-img-Backup_flash_drive-017807361dffbac915098b60d2a07116-20231103150918-vo54fw1.png)​

Alternatively, you can use [Unraid Connect](https://docs.unraid.net/connect/help/#restoring-flash-backup) to back up your Flash boot device.

#### What if I can't backup my device?

In the event that your flash device has failed and you do not have a backup, you can still reconfigure Unraid on a new flash device and transfer your registration key to that device.

1. Install Unraid to a new flash drive using the [USB Flash Creator](#using-the-usb-flash-creator).
2. Either install your old key file in  <span style="font-weight: bold;" data-type="strong">_Tools &gt; Registration_</span> , or simply copy it to the `\boot\config`​​ directory on your USB flash device. The server will notice a GUID mismatch and display a <span style="font-weight: bold;" data-type="strong">Replace Key</span> button on the  <span style="font-weight: bold;" data-type="strong">_Tools &gt; Registration_</span>  page.

    > 从硬盘中复制，在`\boot\config`​目录下
    >

To ensure no data loss after the server is booted, you will need to make sure you assign each disk to the array / cache exactly as it was prior to the failure. It is also a good idea to keep a screenshot of your drive setup, anytime you conclude a major change in the configuration of your Unraid server, for example, after the initial setup, or after adding/removing drives. If you do not know which disks were assigned where, create a post in the forum for further assistance.

‍

### Changing a flash device before purchasing a license

试用期更换u盘

If you're currently using a Trial key and you're ready to purchase, you may want to use a better flash drive for your paid license key. Perform the same steps in this guide for replacing the flash and, when done, purchase a registration key from the  <span style="font-weight: bold;" data-type="strong">_Tools &gt; Registration_</span>  page.

info

Once you transfer a Trial configuration to a new flash device, you will be unable to start the array until you purchase a valid registration key (Trial keys can only work on the original device to which they were registered).

### Using the USB Flash Creator

The second step in the process, is to use the Unraid USB Flash Creator tool to restore your backup to the new USB flash device. This can be downloaded for Windows or macOS here: [Download USB Creator](https://unraid.net/download)

​![](http://127.0.0.1:6806/assets/net-img-Usbcreator-570d904c896fac5296853634b65022d6-20231103150919-0bqcsxp.png)​

1. Obtain a new good quality USB flash device.
2. Plug it into your Mac or PC computer and then run the Unraid USB Creator software.
3. For the version, select <span style="font-weight: bold;" data-type="strong">Local Zip</span>, then browse to the location of the backup that you created earlier to select the ZIP file. ![](http://127.0.0.1:6806/assets/net-img-Selectversion-85d591f61c0456095ce33a9034e6325c-20231103150919-2i5zzpo.png)​
4. Next, make sure that you select your new USB Flash device for the destination, then select <span style="font-weight: bold;" data-type="strong">Write</span> and your backup will be restored to the new USB flash device.
5. Shutdown the server. Remove the original USB flash device and replace it with the new one you have just created. Power on the server.
6. Once booted the array will not start and you will see the message:

    > ​`Invalid, missing or expired registration Key`​
    >
7. Select <span style="font-weight: bold;" data-type="strong">Registration Key</span>.

​![](http://127.0.0.1:6806/assets/net-img-Invalidkey-50c3f3163a051b6275dbaef06ccbcb4b-20231103150920-ctcxpdi.png)​

8. if you are not restoring from a backup, which would contain a copy of your license key file, then copy your existing license key file into the `boot/config`​ folder on the flash drive. This lets Unraid know you want to switch your license to this new flash drive.
9. In  <span style="font-weight: bold;" data-type="strong">_Tools &gt; Registration_</span> , select <span style="font-weight: bold;" data-type="strong">REPLACE KEY</span> then enter the email address to which you would like to have the new key delivered to.
10. Select <span style="font-weight: bold;" data-type="strong">REPLACE KEY</span>.

​![](http://127.0.0.1:6806/assets/net-img-Replacekey-6ba2def31bd3519f5702d9a06a9441a3-20231103150920-ki4qz1t.png)​

11. Once you have received the email, copy the key file URL, then paste it into the box and select <span style="font-weight: bold;" data-type="strong">INSTALL KEY</span>.

Finished! You have replaced the USB flash device and the registration key. You will see a screen showing the date this key was registered and the next date on which your registration key will be eligible to be replaced again.

12. Select <span style="font-weight: bold;" data-type="strong">DONE</span>, to finish.

### Manual method

Prepare a new flash device using the procedure documented in the [Manual Install Method](https://docs.unraid.net/unraid-os/getting-started/manual-install-method/) guide.

1. Before removing the flash from the PC, copy the `boot/config`​ folder from the backup you made, into the flash drive, overwriting existing files.
2. Shut down the server. Remove the original USB flash device and replace it with the new one. Power on the server.
3. Once booted the array will not start and you will see the message:

    > ​`Invalid, missing or expired registration Key`​
    >
4. Select <span style="font-weight: bold;" data-type="strong">Registration Key</span>. ![](http://127.0.0.1:6806/assets/net-img-Invalidkey-50c3f3163a051b6275dbaef06ccbcb4b-20231103150921-telv3ml.png)​
5. In  <span style="font-weight: bold;" data-type="strong">_Tools &gt; Registration_</span> , select <span style="font-weight: bold;" data-type="strong">REPLACE KEY</span> then enter the email address to which you would like to have the new key delivered to.
6. Select <span style="font-weight: bold;" data-type="strong">REPLACE KEY</span>. ![](http://127.0.0.1:6806/assets/net-img-Replacekey-6ba2def31bd3519f5702d9a06a9441a3-20231103150921-zfm73x0.png)​
7. Once you have received the email, copy the key file URL, then paste it into the box and click 'INSTALL KEY'

Finished! You have replaced the USB flash device and the registration key. You will see a screen showing the date this key was registered and the next date on which your registration key will be eligible to be replaced again.

8. Select <span style="font-weight: bold;" data-type="strong">DONE</span>.

Notes about replacing your registration key

---

You may replace your original registration key at any time. After replacing your license key once, you may replace your key using the online automated method after a further period of 12 months.

Should you need to replace it again within that 12 month period, use the contact form at [https://unraid.net/contact](https://unraid.net/contact). For expedited service, please include in your message the old and new USB GUIDs, as well as the license and email address used at the moment of purchase.

info

We strive to manually replace licenses ASAP. If you cannot replace your registration key yourself (having done so more than once per year) and you need access to your server right away, it is recommended that you first [set up a new Unraid trial](https://unraid.net/download) with a new USB drive and then contact us to manually transfer your license.

What to do if you have no backup and do not know your disk assignments

---

If your Unraid boot device has failed, you have no recent backup and are not sure of their disk assignments it is very important that you do not assign a data disk as a parity drive as this will cause data loss. Unraid overwrites it with parity data, destroying its contents. It can also happen if you accidentally use an old backup, have increased the size of your parity drive, and have re-used the old parity drive from that time as a data drive.

Things to know:

* Any parity drive will not have a mountable file system so if you can identify which drive(s) have unmountable file systems then these are probably your parity drives.
* Data drives previously used by Unraid will not have their contents wiped if you reset the array configuration.

If you find you have more unmountable drives than you had parity drives then you should ask for help in the Unraid forums. In such a case the following steps can help you get your array drives back without data loss:

1. Create a fresh install of the Unraid flash drive as shown earlier.
2. Edit the file `/boot/config/disk.cfg`​ on the flash drive and if necessary change the `startArray="yes"`​ entry to `startArray="no"`​

This is to avoid any accidents that might result in a data drive getting overwritten with parity information. You can achieve the same effect from the Unraid GUI via the  <span style="font-weight: bold;" data-type="strong">_Settings &gt; Disk Settings_</span>  option.

3. Go to  <span style="font-weight: bold;" data-type="strong">_Tools &gt; New Config_</span>  and select the option to create a new array configuration. At this point there are two ways to proceed:

    * Assign all drives as data drives, then start the array. Once it has started, make a note of the serial numbers of drives showing as unmountable as these are most likely our parity drives.
    * Use the <span style="font-weight: bold;" data-type="strong">Unassigned Devices</span> plugin to try and mount each drive in turn to see which ones fail to mount. Then, make a note of the serial numbers of drives showing as unmountable as these are probably our parity drives.

Now that you have identified the parity drives then:

4. Go to  <span style="font-weight: bold;" data-type="strong">_Tools &gt; New Config_</span>  and select the option to create a new array configuration. This time it is advisable to use the option to retain all currently configured drives as this avoids the need to rearrange all drives (and thus reduces the chances of error).
5. Go to the  <span style="font-weight: bold;" data-type="strong">_Main_</span>  tab and assign the drives as required with the correct drive(s) assigned as parity.
6. If you only had a single (`parity1`​) drive then the order of the data drives is not important as far as parity is concerned. You can safely tick the <span style="font-weight: bold;" data-type="strong">Parity is Valid</span> checkbox. With dual parity then since the parity1 and parity2 drives use different calculations they are <span style="font-weight: bold;" data-type="strong">not</span> interchangeable so you will need to generate parity from scratch on both drives.
7. Start the array to commit the drive assignments and you should see all your data drives have mounted and their contents are intact.
8. If you ticked the <span style="font-weight: bold;" data-type="strong">Parity is Valid</span> checkbox then run a correcting parity check to make sure this was a valid assumption.

The above process will not necessarily mean the data drives are in the same order so if you have any shares that have specific drive include/exclude then you will need to look at the contents of the individual data drives to make sure these are as you want them (and correct them if not).
