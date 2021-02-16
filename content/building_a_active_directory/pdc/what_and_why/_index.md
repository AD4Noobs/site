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

The Domain is basically the over al group that contains ALL the objects stored in the Active Directory database.
Regardless of how big your AD becomes or on how many locations in the world its located, when possible you want use a singular Domain since it simplifies AD management (and security for that mater) a ton.

{{% notice info %}}
There is this concept called Enhanced Security Administrative Environment (ESEA), also known as a Red Forest which Microsoft released after NotPetya hit the world. If implemented correctly this greatly reduces known attack vectors in AD, but its way to complicated to cover during this stage of the guide and is something to cover during a later date.
{{% /notice %}}

However this sadly inst always possible duo support for other versions Active Directory servers (Functional Levels) or corporate shenanigans.

### Global Catalog

![](gc.png)

## Functional Levels

![](functional_levels.png)



## RODC

![](gc.png)

## NTDS

![](ntds.png)

## SYSVOL

![](ntds.png)
