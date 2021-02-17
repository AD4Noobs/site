---
title: "FSMO"
date: 2021-02-16T11:39:08+01:00
draft: false
weight: 9
pre: "<b>3.9 </b>"
---

Another thing we didn't see yet, but is closely related to the initial setup of AD, are 'flexible single masters of operation' or FSMO for short. FSMO consist of 5 roles and currently all reside on our newly created DC:

- Schema master  
  Schema master controls the Schema changes in any active directory forest.
- Domain naming master  
  Domain Naming master controls addition or deletion of domains in a forest.
- RID master  
  Every AD object that we create gets an RID (Relative Identifier) number which defines which DC the AD object belongs to. If any DC runs out of these RID numbers it contacts the RID Pool Manager and get new pool of RIDs for further distribution.
- PDC emulator  
  The PDC emulator is necessary to synchronize time across a network
- Infrastructure master  
  The infrastructure master is responsible for updating references from objects in its domain to objects in other domains.

Right now its not important to go into more detail about these roles, since you most likely never have to tinker with them. Except when you start phasing out older Domain Controllers.

![](fsmo_roles_bad_time.png)

Make sure you always check where the current FSMO roles reside before removing any Domain Controller from the domain. If they are currently hosted on the DC you want to phase out you need to move them over to another DC.
