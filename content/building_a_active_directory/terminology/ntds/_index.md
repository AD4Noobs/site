---
title: "NTDS"
date: 2021-02-16T11:39:08+01:00
draft: false
weight: 7
pre: "<b>2.4.7 </b>"
---

## NTDS

![](ntds.png)

NTDS is the file that contains the Active Directory Database. It stores all the information about the Domain of which the current Domain Controller is part of.

{{% notice note %}}
As an attacker going after AD this is **the** file we want to get our hands on. This file contains every user attribute, including normally protected and hidden attributes such as the users password (hash). After gaining access to this file we are able to start cracking user passwords, create magic a [GoldenTicket](http://blog.gentilkiwi.com/securite/mimikatz/golden-ticket-kerberos) and do other 'fun' stuff.
{{% /notice %}}
