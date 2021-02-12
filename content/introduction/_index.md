---
title: "Introduction"
date: 2021-02-11T15:39:11+01:00
draft: false
pre: "<b>1. </b>"
---

So by now you must have seen this thing called 'Active Directory' (or AD for short) been referenced everywhere in this guide. So far it's been never explained what it actually is, so I would not blame you if you have no idea what it is.

{{< figure src="is_this_a_active_directory.png" title="You probably right now" >}}

## The company

So let's imagine you need to run 'The IT' for a fictitious company called 'Threepwood's Fine Leather Jackets and Pirate Paraphernalia' (or TFLJPP for short) a company that sells all kinds of pirate merchandise. This company has around 150 employees with jobs ranging form all kinds of different functions:

- Store clerks
- Store managers
- HR
- Marketing
- (il)legal department
- Paper pushing office monkeys
- {{%expand "Management" %}} Don't let them catch you call them that. They liked to be referred to as Pirate Lords. You don't want to find out what happens when you do and are send to Big Whoop. {{% /expand%}}

To function as a company all these people with different functions need a way to work together. As you can might imagine some of these people need access to specific files or systems in 'The IT' infrastructure while others just need to be able to manage the register. There's also the fact that someone in HR might need a specific program installed on their system or that the office monkeys work in a 'Flexspace', meaning they just walk up to a random computer, mash in their user credentials and expect the computer to be configured in a specific way.

{{< figure src="monkey.gif" title="Here's only login on right now." >}}

So in order to provide this segmented access within the company Active Directory Services comes in. Active Directory Services is a combined name for multiple different kind of services, one of which is Active Directory Domain Services. Right now where not going to talk about the these other services but if you are interested here are a [couple](https://www.youtube.com/watch?v=J8y4G0dD-hg) [of](https://www.youtube.com/watch?v=ewn6TaG5GDg) [video's](https://www.youtube.com/watch?v=x0HXDL7i0Wo).

{{% notice note %}}
Active Directory Domain Services is commonly abbreviated as AD DS or if you are really lazy like me, simply AD.

{{% /notice %}}

## Active Directory Domain Services

AD is the cornerstone of pretty much every Windows domain network. It does things such as:

- Store information about members of the domain (such as devices and users);
- Providers central authentication for the network;
- Allows or restricts access to resources/applications in the network;
- Enforce the appropriate configuration/policy of user or computer settings.

This is why most companies use it. From a functional point of view it does a lot, if not everything, a company needs in order to create a function work environment, so its often been the goto solution.

