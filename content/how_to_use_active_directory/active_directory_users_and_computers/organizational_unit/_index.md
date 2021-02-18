---
title: "Organizational Unit"
date: 2021-02-17T14:54:19+01:00
draft: false
weight: 1
pre: "<b>4.2.1 </b>"
---

Lets us start with creating our first OU. I recommend that for any AD environment you create you start with 1 OU that houses all the objects you are going to create. I usually use a abbreviation of the company name, most lickely the same one I used for the NetBIOS domain name (**TFLJPP**\username).

To create an OU open ADUC, click on your FQDN and then right click in the main window.

This should give you a menu that allows you to select `New >`. This will span a second menu that allows you to create new AD Objects. Here you choose 'Organizational Unit'.

Now give this OU a name, in this case `TFLJPP` and click on OK (or if you are lazy, press Enter).

Now open this newly created OU and create 3 more OU's. `Users`, `Computers` and `Groups`.

![](create_ou.gif)