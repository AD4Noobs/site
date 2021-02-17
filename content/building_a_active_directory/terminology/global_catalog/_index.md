---
title: "Global Catalog"
date: 2021-02-16T11:39:08+01:00
draft: false
weight: 4
pre: "<b>2.4.4 </b>"
---

![](gc.png)

During the installation process there was this thing called a Global Catalog (GC) that showed up.

The GC's job is to create an index of all objects from all the domains in the forest. This is needed because Domain Controllers only store information about objects from inside of their own Domain. They don't know anything about objects from other Domains. If they would need to lookup information from a object outside of their own Domain they would ask the GC for help. Any Domain Controller in a Domain can become a GC and each Domain should have at least 1 of them.

{{% notice note %}}
For now thats all you need to know, just remember that a GC and its placement can get more complicated in large complex enterprise environments which require multiple domains, trees and forests.
{{% /notice %}}
