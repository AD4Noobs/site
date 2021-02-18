---
title: "Introduction"
date: 2021-02-11T15:39:11+01:00
draft: false
weight: 2
pre: "<b>1. </b>"
---

So, by now you must have seen this thing called 'Active Directory' (or AD for short) been referenced everywhere in this guide. So far, it's been never explained what it actually is, so I would not blame you if you have no idea what it is.

{{< figure src="is_this_a_active_directory.png" title="You probably right now" >}}

## The company

So, let's imagine you need to run 'The IT' for a fictitious company called 'Threepwood's Fine Leather Jackets and Pirate Paraphernalia' (or TFLJPP for short) a company that sells all kinds of pirate merchandise. This company has around 150 employees with jobs ranging form all kinds of different functions:

- Store clerks
- Store managers
- HR
- Marketing
- (il)legal department
- Paper pushing office monkeys
- {{%expand "Management" %}} Don't let them catch you call them that. They liked to be referred to as Pirate Lords. You do not want to find out what happens when you do and are send to Big Whoop. {{% /expand%}}

To function as a company all these people with different functions need a way to work together. As you might imagine some of these people need access to specific files or systems in 'The IT' infrastructure while others just need to be able to manage the cash register and read e-mails. There is also the fact that someone in HR might need a specific program installed on their system or that the office monkeys work in a 'Flexspace', meaning they just walk up to a random computer, mash in their user credentials and expect the computer to be configured in a specific way.

{{< figure src="monkey.gif" title="Here's one login on right now." >}}

So, in order to provide this segmented access within the company Active Directory Services comes in. Active Directory Services is a combined name for multiple different kind of services, one of which is Active Directory Domain Services. Right now, where not going to talk about the these other services but if you are interested here are a [couple](https://www.youtube.com/watch?v=J8y4G0dD-hg) [of](https://www.youtube.com/watch?v=ewn6TaG5GDg) [video's](https://www.youtube.com/watch?v=x0HXDL7i0Wo).

{{% notice note %}}
Active Directory Domain Services is commonly abbreviated as AD DS or if you are really lazy like me, simply AD.

{{% /notice %}}

## Active Directory Domain Services and the Windows eco system

AD is the cornerstone of pretty much every Windows domain network. It does things such as:

- Store information about members of the domain (such as devices and users);
- Providers central authentication for the network;
- Allows or restricts access to resources/applications in the network;
- Enforce the appropriate configuration/policy of user or computer settings.

This is why most companies use it. It lays a foundation to build something upon.

#### The positives

From a functional point of view it does a lot, if not everything, a company needs in order to create a function work environment, so it's often been the 'go to' solution. This also means that over the years most other corporate software/appliances now support integrating with AD, allowing products and users to work more seamlessly.

This includes Microsoft themselves. You might have heard of Office365 by now, but before the mighty cloud existed, they also build a mailing product called `Microsoft Exchange`. When you deploy Exchange in a environment it gets heavily integrated into Active Directory, as a requirement it even extends some parts of AD (the AD Schema).

{{% notice note %}}
Don't get me wrong, but a lot of companies still use Microsoft Exchange to this day instead of Office365. There are actually ways to integrate AD/Exchange with Office365/Microsoft Azure AD creating this unholy matrimony of hybrid on-premises and cloud.

{{% /notice %}}

{{%expand "Microsoft also developed these things called 'Roles and Features' which are part of Windows Servers, such as a Remote Desktop Server (RDS). This basically is a 'Remote Workspace/Computer' that a user can log on to access the corporate network, without AD in place it would be virtually impossible to deploy this in any form in a medium or large-scale deployment." %}} Technically speaking AD DS is also a role, but you will soon learn that. {{% /expand%}}

#### The negatives and the ugly truth about why most AD environments are laughably insecure

The downside of this that since everything is integrated it get complicated and messy pretty fast. In order for most external products to function they need some form of administrative access within AD and/or the network. Since traditionally IT has been underfunded and understaffed this sometimes results (Read most of the times) in a security being put in the back seat.

##### The mind set

*"I need to get things up and running so my office monkeys won't complain. They need to be able to work."* is the main driving force in most IT operations.

If there is an issue while deploying a 'new product' it needs to be solved ASAP. If that means a Hail Mary solution like *"Giving the product Full admin/'Domain Admin' rights"* fixes the issue it gets deployed like that.

Which can be fine if you are, for example, in a time crunch and it gets accepted as an *acceptable risk from a business operations perspective*, but only if the intent is to actually fix this on a later date. Which most of the time never happens. Since now there is this fear of *"If we touch it we might break it and invoke the wrath of the office monkeys"*.

Luckily duo changes in the industry security is getting more of a front row seat. Now it can cost a company a lot of money if they, for example, get hit with ransomware. But AD is such a fundamental piece of a corporate environment and a lot is connected to it. This means it can be really hard to clean up if its 'really messy' state or even start from a scratch.

##### Managing office monkeys

Speaking about paper pushing office monkeys, another big factor is managing them. Monkey just want to push **ALL THE** buttons, throw papers and eat banana's, they don't care about anything else. Which is fine, they are great at pushing buttons, but you don't want them to break things by for example clicking on that phishing e-mail link that promises *Free Banana's* and *totally won't install malware*. So, you start to locking things down, increase security and try to prevent bad things happening. But the monkeys start to notice, and they find it an annoyance. And boy can the monkeys complain if there is something they find an annoyance.

{{< figure src="monkey2.gif" title="Here's one after finding out he can't use 'Banana2021' as its password anymore." >}}

So, what can happen if we don't teach the monkeys or their managers why we do this? Security standards can get decreased. Meaning now there are hundreds of banana passwords in you AD. And believe me, you don't want banana's in your AD 🍌.
