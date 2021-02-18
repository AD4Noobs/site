---
title: "Organizational Unit"
date: 2021-02-17T14:54:19+01:00
draft: false
weight: 1
pre: "<b>4.2.1 </b>"
---

When you first open your Domain in ADUC you will be greeted with a couple of default objects.

{{< figure src="overview.png" title="Default Objects">}}

As you might notice some of these have the type 'Container' while others have the type 'Organizational Unit' (OU's), even though they almost look the same and they all have the description 'Default container for...' they are different things. As is with most things in the '[Microsoft World](https://www.youtube.com/watch?v=UQvm5_OweF8)', whenever this is the case it most likely has to do with backswords compatibility.

In this case the 'Containers' are generic Active Directory containers. Both OU's and Containers have the ability to house other objects, such as users and computers, and are thus considered Container Objects (instead of Leaf objects). The main difference between Containers and OU's is that Containers can't be used with  Group Policy Object (GPO's) or delegation.

Well what are GPO's you might ask ? Well that is a topic we need to tackle on it owns. To give a really basic explanation, GPO's allow administrators to configure settings and preferences for users and computers, like setting a default home page in a webbrowser. Pretty much any modern AD environment uses GPO's in some form.

{{% notice info %}}
**TL:DR** Containers are Old. Organizational Units are new. Both can house other objects. You want to use OU's because they work with GPO's.
{{% /notice %}}


![](create_ou.gif)