---
title: "How to add a Computer to the Domain"
date: 2021-02-17T14:55:30+01:00
draft: false
weight: 3
pre: "<b>4.3 </b>"
---

Click on the VM and then click on Clone.

Rename the VM to `pc01.ad.tfljpp.test` and ensure `Linked Clone` is selected, then click on Clone.

After cloning, right click on the VM and click on settings, then go the network and change the `Attached to` to `NAT Network`. This should automatically select the newly created VirtualBox Network.

![](create_new_pc.gif)

Like we did before, we need to change the computer name and set a static IP.

Open the file explorer and click on `This PC`. Now click anywhere in the white space to the right and choose `Properties`. Then click on `Change Settings` and `Change`. Here you can update the computer name to PC01. Now click on Ok twice and close. You will then be prompted to reboot the workstation.

![](rename_pc.gif)

Open the file explorer and right click on `Network` and choose `Properties`.
Then click on `Ethernet`, choose `Properties`, `Internet Protocol Version 4 (TCP/IPv4)` and enter the following information.

| IP Address   | Subnet Mask   | Gateway    | DNS         |
| ------------ | ------------- | ---------- | ----------- |
| 10.11.12.100 | 255.255.255.0 | 10.11.12.1 | 10.11.12.10 |

{{% notice note %}}
These settings depend on how you setup the Virtual Network properly according to this guide. To verify what your current network settings; Click on start and search for CMD. Then type `ipconfig` and press enter.
{{% /notice %}}

![](network_settings.gif)

After changing the settings, we can verify if everything is setup correctly by sending a ping to `dc01.ad.tfljpp.test`.
Click on start and search for CMD. Then type `ping dc01.ad.tfljpp.test` and press enter. It should then ping and reply 4 times.

![](test_network_settings.gif)

Now that we have a static IP and setup our DNS correctly we can add this machine to the domain.

Open the file explorer and right click on `This PC` and choose `Properties`. Then click on `Change Settings` and `Change`. Here you can select `Domain` and enter the correct domain. This is our root domain `ad.tfljpp.test`. After pressing enter you will be prompted to enter credentials. Login using the Administrator account.

{{% notice warning %}}
During this part of the guide we will be using the Domain Administrator to add a computer to the domain and login to the computer. You should **NEVER** do this in a production environment. You should have dedicated Tiered and Hardened Admin accounts to logon to workstations. You should also use a lockeddown and dedicated account to add computers to the Domain. At this point where still explaining the basics of AD, so we haven't configured this yet (and shown why this is important).
{{% /notice %}}

Now click on Ok three times and close. You will then be prompted to reboot the workstation.

![](add_pc_to_domain.gif)

After the reboot you are able to login using a Domain joined account. The first time doing this you will need to clock on 'Other user' and supply the NetBIOS domain name `TFLJPP\` followed by administrator, or login using `administrator@ad.tfljpp.test`.

![](logon_into_domain.gif)

If you now open the default computer ou in ADUC you can see the new computer here. Move this computer to our custom Computers OU.

![](move_from_default_ou.gif)
