---
title: "The what and why"
date: 2021-02-16T11:39:08+01:00
draft: false
pre: "<b>2.3.1 </b>"
---

During that installation process we saw a bunch of technical terms and options fly by. These things are actually rather important things to understand if you want to learn about Active Directory, so lets cover them now!

## Domain, Tree and Forest

![](domain_site_tree_forest.png)

Before we can cover Domains, Tree's and Forests we first need to cover what objects are and the things that come with them. 

This is the stuff about AD that makes it complicated, dull and sometimes hard to grasp. So let's try to have some fun with it.

### Objects, Attributes and Classes

A object in AD is just a basic element that represents something.

It could be a user, computer, group, folders, or even a printer attached to the network.

![](objects.png)

Theses objects have these things called attributes. These attributes define and describe the objects.

![](attributes.png)

For example a user object might include:

- Name;
- E-mail;
- Phone number.

Every object of the same type has the same set of attributes, some of which are mandatory while others are optional. Because of this fact we can classify them as objects part of the User class.

![](users.png)

For example, the name of the user is something that is mandatory, while their phone number is not. But regardless of that attribute being used or not, its still a object that belongs to the user class.

#### Leaves and Containers

Objects basically come in two flavours, Container objects Leaf objects:

- Container objects can contain other objects.  
  As an example, a Group object is an container. It can contain other objects such as users or even other groups.
- Leaf objects, on the other hand, are just a single things.  
  As an example, users and computers are leaf objects and can't contain other users or computers.

To make this a bit less abstract lets think of these objects and attributes as 'physical' things.

#### The Donkeys, Ogre's, Dragons and Castles

Everything (objects) has some defining features (attributes) that make it into what it is (class).

{{%expand "You know which mandatory defining features a donkey has and why it's different from a ogre, dragon or even a castle. But that does not mean that all other donkeys have to be precisely the same." %}}

![](layers.gif)

{{% /expand%}}

{{< figure src="donkey.webp" title="Lets take this donkey for example." >}}

All Donkeys walk on 4 legs, have fur all over their body and have a tail. These are the mandatory attributes that makes the donkey 'object', well, you known, a donkey. Because of this fact we can call this object by a class name, the Donkey class. 

Even though not all objects with the donkey class have the same height or weight (optional attributes), and in this particular example the ability to speak and sing, but they are all considered donkeys because they have the mandatory attributes for that class.

{{%expand "We also can't fit ogre's and dragons into a donkey." %}}

I know what you are thinking... no... we can't.

{{% /expand%}}

We can however fit all of those into a Castle. This is because a Castle is an Container Object and a Donkey is a Leaf Object.

### The Schema

So now that we know our Active Directory can contain Donkeys, Ogre's, Dragons and Castles we can talk about the Active Directory Schema. The schema of Active Directory defines the rules how a object class looks like, what attributes are mandatory and are which ones optional. It's basically a giant collection of blueprints for all objects classes in Active Directory.

![](blueprint.png)

The schema itself is shared between all domains and tree's in forest.

### Domain, Tree and Forest

So whats a Domain ?

The Domain is basically the over al group that contains ALL the objects stored in the Active Directory database. A Domain can be hosted on 1 or multiple Domain Controllers. When using multiple Domain Controllers within 1 domain the changes to the [Active Directory Database (NTDS)](#ntds) are replicated between them.

{{< figure src="domain_tree_forest_01.png" title="This is a singular domain" >}}

Regardless of how big your AD becomes or on how many locations in the world its located, when possible, and I can't stress this enough, you want use a singular Domain since it simplifies AD management a ton.

{{% notice info %}}
There is this concept called Enhanced Security Administrative Environment (ESEA), also known as a Red Forest which Microsoft released after NotPetya hit the world. If implemented correctly this greatly reduces known attack vectors in AD, but its way to complicated to cover during this stage of the guide.
{{% /notice %}}

However this sadly inst always possible duo support for other versions [Active Directory servers (Functional Levels)](#functional-levels) or corporate shenanigans/politics.

#### Child Domain

Lets say that 'Threepwood's Fine Leather Jackets and Pirate Paraphernalia' wants all the Office monkeys inside of their own Child Domain. Why they would want that ? I have no idea. Lets just settle it under 'Corporate Shenanigans'. This would look something like this.

{{< figure src="domain_tree_forest_02.png" title="This is a Root Domain with a Child Domain" >}}

#### Tree

When you have a child domain within the same Root Domain it is referred to 'being in the same Tree'. They are however still separate domains. Each Domain needs at least 1 separate Domain Controller. This means that each Domain in a Tree has its own [Active Directory Database (NTDS)](#ntds) with its own objects such users, groups etc.

{{< figure src="domain_tree_forest_03.png" title="This is what the Tree looks like." >}}

A tree can consist of multiple child domains, they can even inherent from each other, but there can only be 1 Root Domain, this is also refered to as the Tree Root. The advantage of creating these child domains is that there is a trust created between each domain because they are in the same tree. This means that users from monkeys child domain can access resources in the pirates child domain, if they would have the appropriate rights to that resource.

{{< figure src="domain_tree_forest_04.png" title="Domains can have multiple child domains, including child domains themselves" >}}

#### Forest

Now lets say that over time the TFLJPP company grows over time and acquires another company, 'Wally B. Feed Cartography and Co'.
The acquired company already has a AD configured with their own Tree. You could migrate over all the users/systems from this over to your Tree, but this can be a daunting and time consuming task. So what we can do is add their Tree to our Forest. Doing this adds a trust between these two tree's. This means that access to resources can now be shared cross company.

{{< figure src="domain_tree_forest_05.png" title="This is wat a Forest looks like with multiple Tree's" >}}

{{% notice note %}}
There are actually other types of trusts, such as shortcut, forest, external and realm trusts. Each with different characteristics (Transitive vs. Non-Transitive), direction types (One-way or Two-way) and authentication mechanism (Kerberos V5 or NTLM). I won't go into detail's here since if I where to cover it fully it would require a lot more of preexisting knowledge of AD internals such as NTLM and Kerberos, which are even heavy topics to cover on their own. Just remember that I generally recommend against multiple domains/tree's/forest and trusts due the added complexity and security risks, unless you truly understand what you are doing/are building a Red Forest.
{{% /notice %}}

#### What we currently build

A forest can incases multiple domains and trees into 1 structure, but doesn't have to. We actually already created a Forest and a tree when we setup Active Directory. These are created automatically.

{{< figure src="domain_tree_forest_06.png" title="This what a setup with a singular domain a actually looks like." >}}

### Global Catalog

![](gc.png)

During the installation process there was this thing called a Global Catalog (GC) that showed up. Any Domain Controller can become a GC and each Domain should have at least 1.

The GC's job is to create an index of objects from domains in the forest. It needs todo this since Domains only know about information from objects inside of their own domain. They don't know about objects from other domains. If they would need to lookup this information the GC helps them with this.  

{{% notice note %}}
For now thats all you need to know, just remember that a GC and its placement can get more complicated in large complex enterprise environments which require multiple domains, trees and forests.
{{% /notice %}}

## Functional Levels

As you might remember from earlier, roles are built in packages into Windows Server. This means that each release of Windows Server might have different version of the included Roles. The AD DS Role is a great example. Over the years with new releases of Windows Server new functionality has been consistently added to AD. This means however that you can run into issues if you where to support these new features while still having old Domain Controllers. This is where Functional Levels jump in. 

![](functional_levels.png)

Functional Levels determine which version of Windows Server are allowed to host the AD DS role in the domain. During the installation process we use a Domain Functional Level of Server 2016. This means that only we can only create Domain Controllers using at least Windows Server 2016. Any version lower, for example Server 2012R2, will not be able to be promoted to a Domain Controller is this domain.

{{% notice info %}}
The tech savvy among you probably already thought of a work around. Yes you could create new child domains for the purpose to support older or new versions of AD DS, though it is highly recommended phase out older Windows Servers running Domains Controllers in your domain in favor of newer version of Windows Server. This allows you to most recent functional level and make use of new features, a lot of which have been security focused.
{{% /notice %}}

## RODC

![](gc.png)

RODC are Read-Only Domain Controllers. Though we did not use it, i'd still like to cover it briefly.
Read-Only Domain Controllers can be used for some specific use cases such as branch offices where you would not want to host a full Domain Controller for security reasons since they could be physically less secure. By default, no AD account passwords are cached on a RODC and the domain does not allow no changes originating from a RODC's AD database, SYSVOL, or DNS.

A Read-Only Domain Controller would allow people in this branch office to still authenticate if, lets say, their VPN connection to the main office went down. [Though if RODCs are not deployed properly, it's possible that the RODC can create a scenario where an attacker could escalate privileges through the RODC up to and including full control of Active Directory.](https://adsecurity.org/?p=3592)

## NTDS

![](ntds.png)

NTDS.dit is the file that contains the Active Directory Database. It stores all the information about the Domain of which the current Domain Controller is part of.

{{% notice note %}}
As an attacker going after AD this is ***THE*** file we want to get our hands on. This file contains every user attribute, including normally protected and hidden attributes such as the users password (hash). After gaining access to this file we are able to start cracking user passwords or even create magic [GoldenTicket](http://blog.gentilkiwi.com/securite/mimikatz/golden-ticket-kerberos).
{{% /notice %}}

## SYSVOL

![](ntds.png)

SYSVOL is a folder that exists on all domain controllers. It a central place to store important Active Directory files. Once of which are group policies, ADMX files (Extra group policies) logon/logoff and startup/shutdown scripts. The File Replication Service or FRS allows the replication of the SYSVOL folder among domain controllers. Logon scripts and policies are delivered to each domain user via SYSVOL. SYSVOL stores all of the security related information of the AD.
