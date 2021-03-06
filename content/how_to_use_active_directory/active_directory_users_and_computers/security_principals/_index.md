---
title: "Security Principals"
date: 2021-02-17T14:53:36+01:00
draft: false
weight: 2
pre: "<b>4.2.3 </b>"
---

### Security Principals and SIDs

Security Principals are types of objects that can be used to gain access to something. To do this, the Security Principal needs to be able authenticate against the Operating System (OS). The OS then does an Access Control checks to see if this Security Principal has access to the requested resource. It then either allows or denies it access. Security Principals are not just used in Active Directory, but also by standalone version of Windows. To keep track of Security Principals each are assigned a unique security identifier (SID).

A couple of Security Principals you will often work with in Active Directory are Users Accounts, Groups and Computer Accounts.

{{% notice note %}}
If you ever see a string that starts with `S-1-5-21` you know it's a SID. ![](sid.png)
{{% /notice %}}

### Authentication and Access Control

For example, lets say if Guybrush Threepwood wants to access content on a file share called `pictures`. This file share is protected and requires people who want to access it to be part of the Active Directory group named `FOL_Pictures_R`. Guybrush's Active Directory account is member of this group.

Before Guybrush is able to access this file share he will need to authenticate. Since this share is protected by a group that is part of Active Directory he authenticates with his Username and Password. In this process he is proving he is actually Guybrush Threepwood, Mighty Pirate, and not some random Office Monkey.

After authenticating to Active Directory it will check if Guybrush's account is part of the `FOL_Pictures_R` Group. Since it is, Guybrush is allowed to access this file share.

{{% notice info %}}
This is a very simplified version of the internal authentication used by Active Directory. There are actually a bit more things involved and that will depend on what authentication method is used.
{{% /notice %}}
