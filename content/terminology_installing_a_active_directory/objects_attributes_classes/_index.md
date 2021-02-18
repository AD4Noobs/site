---
title: "Objects, Attributes and Classes"
date: 2021-02-16T11:39:08+01:00
draft: false
weight: 1
pre: "<b>3.1 </b>"
---

An object in AD is just a basic element that represents something.

It could be a user, computer, group, folders, or even a printer attached to the network.

![](objects.png)

These objects have these things called attributes. These attributes define and describe the objects.

![](attributes.png)

For example a user object might include:

- Name;
- E-mail;
- Phone number.

Every object of the same type has the same set of attributes, some of which are mandatory while others are optional. Because of this fact we can classify them as objects part of the User class.

![](users.png)

For example, the name of the user is something that is mandatory, while their phone number is not. But regardless of that attribute being used or not, it's still an object that belongs to the user class.

#### Leaves and Containers

Objects basically come in two flavors, Container objects Leaf objects:

- Container objects can contain other objects.  
  As an example, a Group object is a container. It can contain other objects such as users or even other groups.
- Leaf objects, on the other hand, are just a single thing.  
  As an example, users and computers are leaf objects and cannot contain other users or computers.

To make this a bit less abstract let's think of these objects and attributes as 'physical' things.

#### The Donkeys, Ogre's, Dragons and Castles

Everything (objects) has some defining features (attributes) that make it into what it is (class).

{{%expand "You know which mandatory defining features a donkey has and why it's different from an ogre, dragon or even a castle. But that does not mean that all other donkeys have to be precisely the same." %}}

![](layers.gif)

{{% /expand%}}

{{< figure src="donkey.webp" title="Let's take this donkey for example." >}}

All Donkeys walk on 4 legs, have fur all over their body and have a tail. These are the mandatory attributes that makes the donkey 'object', well, you known, a donkey. Because of this fact we can call this object by a class name, the Donkey class.

Even though not all objects with the donkey class have the same height or weight (optional attributes), and in this example the ability to speak and sing, they are all considered donkeys because they have the mandatory attributes for its species (class).

{{%expand "Now regarding Leaves and Containers. We all known that we cannot fit ogre's and dragons into a donkey. We can however fit all of those into a building, for example a Castle. This is because a Castle is a Container Object, it has the ability to store other things inside of it. A Donkey does not, so it's a Leaf Object." %}}
I know what you are thinking you little defiant.  
No... we can't, and we shouldn't.
{{% /expand%}}
