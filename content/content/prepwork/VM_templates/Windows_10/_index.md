---
title: "Windows 10"
date: 2021-02-08T15:34:40+01:00
draft: false
weight: 1
---

## Creating the VM

Click on `New`

![](new_vm_01.png)

Change the name to `WIndows 10 Template` and the version to `Windows 10 64-bit` and click Next.

![](new_vm_02.png)

Set the memory size to a minimum of 2048MB

![](new_vm_03.png)

Choose `Create a virutal had disk now` and click Next.

![](new_vm_04.png)

Choose `VDI (VirutalBox Disk Image)` and click Next.

![](new_vm_05.png)

Choose `Dynamically allocated` and click Next.

![](new_vm_06.png)

Use at least `60GB` of disk space and click create.

**Note:** This space is Dynamically allocated, meanings it won't take up the full 60GB at the start.
Your virtual hard disk will grow on your pyhiscial harddisk when start using the space inside on your VM.

![](new_vm_07.png)

Click on your new `WIndows 10 Template` VM and then on `Settings`.

![](new_vm_08.png)

From here go to `Storage` , click on `Empty`, select `Live CD/DVD` and then click on the CD/DVD icon and `Choose a disk file...`.

![](new_vm_09.png)

Go to the location where you stored the Windows ISO's we downloaded previously and select the Windows 10 ISO, then click on OK.

**Note:** It probably has something like `CLIENTENTERPRISEEVAL` in its name.

![](new_vm_10.png)

## Installing Windows 10

To start your VM double click on `Windows 10 Template`.

![](new_vm_08.png)

When you start the VM this prompt should pop up. If it does click on Cancel.

![](new_vm_11.png)

Now you should be greeted with the Windows 10 installation. Leave all the options on this screen on English/US and click on Next.

![](new_vm_12.png)

Now here you need to accept the license terms. You can read them if you want to, or just simply accept the fact that you need to accept them anyhow if you want to use the product and click on Next.

![](new_vm_13.png)

Here we need to select how we are going to install Windows. Click on `Custom: Install Windows only (advanced)`

![](new_vm_14.png)

Now click on `Drive 0 Unallocated Space` (this is your virtual harddisk) and click on Next.

![](new_vm_15.png)

Now wait for the installation process to complete.

![](new_vm_16.png)

## Post installation configuration

Once the installation is completed you will be created with this screen. Here we need todo some post installation configuration.

Select `United States` and click on Yes.

![](new_vm_17.png)

Again, select US and click on Yes.

![](new_vm_18.png)

Here simply click on Skip.

![](new_vm_19.png)

Now we are prompted to choose our account type.Since we are using these templates for testing purposes we don't want to link them to a online account, so click on `Domain join instead`

{{% notice info %}}
On previous iterations of the windows installer you had the option to create a `Local Account`, this option has been renamed to `Domain join instead`.
{{% /notice %}}

![](new_vm_20.png)

Enter `user` as the username

![](new_vm_21.png)

Enter `Password01!` as the password.

{{% notice warning %}}
You should **not** use a weak password like this in a production environment. For **local testing purposes** (i.e. not connected to the public internet and segmented in a virtual network)  this should be fine.
{{% /notice %}}

![](new_vm_23.png)

Now confirm the password.

{{% notice warning %}}
Again, please don't use these weak password in production. Sadly I still find passwords like these on almost all my internal assessments.
{{% /notice %}}

![](new_vm_24.png)

{{% notice info %}}
I always add save the login credentials to the descriptions of my **local testing** VMs so I can't forget. I recommend you do this also.
{{% /notice %}}

![](creds_virtualbox.png)

Now you need enter 3 security questions. You can just use bogus answers. We can always reset the password using multiple other methods, If we even manage to forget this easy password in the first place.

![](new_vm_25.png)

Now we have to go through somethings i'd like to call `MicroSpyingSoft` settings. Just disable every option and click on accept.

![](new_vm_28.png)

{{%expand "On the next screen it will ask you to active cortana, just click on not now." %}} Unless you are a wierdo and want to talk to your pc. You wierdo.{{% /expand%}}

![](new_vm_29.png)

Now simply do as Microsoft says and let them handle things. Just sit back and relax while Windows is being setup.

![](new_vm_30.png)

![](new_vm_31.png)

![](new_vm_32.png)

![](new_vm_33.png)

![](new_vm_34.png)

![](new_vm_35.png)

If the time is incorrect after changing the time zone, turn of and on 'set time automatically'.

![](new_vm_36.png)

Once you are done updating your VM go to "Devices -> 'Insert guest additions CD image'" in virtualbox

![](new_vm_37.png)

![](new_vm_38.png)

![](new_vm_39.png)

![](new_vm_40.png)

![](new_vm_41.png)

![](new_vm_42.png)

keep clicking next untill the installation ask you to install a device.

![](new_vm_43.png)

click install

![](new_vm_44.png)
