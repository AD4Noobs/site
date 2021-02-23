---
title: "How to setup a File Server"
date: 2021-02-22T15:48:17+01:00
draft: False
weight: 6
pre: "<b>5. </b>"
---

During this chapter of the guide will be extending our current Lab with a file server. In doing so we can practically present how access control works in Active Directory without having to configure something to complicated/resource intensive.

- ~~Store information about members of the domain (such as devices and users);~~
- ~~Providers central authentication for the network;~~
- ***Allows or restricts access to resources/applications in the network;***
- Enforce the appropriate configuration/policy of user or computer settings.

{{% notice info %}}
If you are low on system resources you can also use `DC01` as the file server, however, since it's against best practices to mix and match services, especially on Domain Controllers, the guide will create a separate File Server.
{{% /notice %}}

![](tfljpp.png)
