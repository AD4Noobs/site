---
title: "PDC"
date: 2021-02-15T14:32:31+01:00
draft: false
weight: 3
pre: "<b>2.3 </b>"
---

## Features and Roles

Now it's time the first Windows Role, AD DS. Before installing this Role lets first talk about what Roles and Features actually means.

Windows Roles and Features are basically programs builtin into windows server itself. These Roles and Features can be installing and uninstalling as you desire and your use case. Whether you want a server to be a file server, a print server, or a web server it all starts with installing a Role or Feature.

If you ever worked with a Linux distribution before, it's kinda similar to a package repository, only these packages are already included in the OS.

{{< figure src="roles.png" title="These are the roles included in Server 2019." >}}

## Install the AD DS Role

![](install_adds_role.gif)

## Promote to Domain Controller

![](promote_to_dc_01.gif)

![](promote_to_dc_02.gif)

![](promote_to_dc_03.gif)

![](promote_to_dc_04.gif)