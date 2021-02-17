---
title: "SYSVOL and NETLOGON"
date: 2021-02-16T11:39:08+01:00
draft: false
weight: 8
pre: "<b>2.4.8 </b>"
---

![](ntds.png)

SYSVOL is a folder that exists on all Domain Controllers. It a central place to store important Active Directory files, such as Group Policies (GPO's for short), ADMX files (Extra group policy templates) and logon/logoff/startup/shutdown scripts that each user and computer account in the domain should have access to. A service called `File Replication Service` or FRS for short, replications the contents of the SYSVOL folder among Domain Controllers in the Domain. This way if a new Logon scripts or GPO is added on 1 Domain Controller it gets replicated to all other Domain Controllers in the Domain.

{{% notice note %}}
As an attacker this a great place to search for information about the Domain. More often then not we can even find credentials stored in SYSVOL (and NETLOGON), even though this should not happen ([anymore](https://adsecurity.org/?p=2288)).
{{% /notice %}}
