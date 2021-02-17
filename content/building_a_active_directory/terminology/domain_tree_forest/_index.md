---
title: "The Domain, the Tree and the Forest"
date: 2021-02-16T11:39:08+01:00
draft: false
weight: 3
pre: "<b>2.4.3 </b>"
---

{{< figure src="wait_what.gif" title="Domains, Trees and Forests, what now ? I thought we where talking about donkeys and blueprints." >}}

Bare with me here, it might not fit into our last theme, but since this is the actual real terminology used by Microsoft I'd like to stick by them.

The Domain is basically the over al group that contains ALL the objects stored in the Active Directory database. A Domain can be hosted on 1 or multiple Domain Controllers (that thing we created previously). When using multiple Domain Controllers within 1 domain the changes to the [Active Directory Database (NTDS)](../ntds/) are replicated between all Domain Controllers.

{{< figure src="domain_tree_forest_01.png" title="This is a singular domain" >}}

Regardless of how big your AD becomes or on how many locations in the world its located, when possible ([the scalability/limits are pretty huge](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc756101(v=ws.10)).), and I can't stress this enough, you want use a singular Domain since it simplifies AD management a ton. However this sadly inst always possible duo support for other versions [Active Directory servers (Functional Levels)](../functional_levels/) or corporate shenanigans/politics.

{{% notice info %}}
Theres also this concept called a Enhanced Security Administrative Environment (ESEA), also known as a Red Forest which Microsoft released after NotPetya hit the world. If implemented correctly this greatly reduces known attack vectors in AD, but its way to complicated to cover during this stage of the guide.
{{% /notice %}}

### Child Domain

Lets say that 'Threepwood's Fine Leather Jackets and Pirate Paraphernalia' wants all the Office monkeys to work in their own Child Domain. Why they would want that ? I have no idea. Lets just settle it under 'Corporate Shenanigans'. This would look something like this.

{{< figure src="domain_tree_forest_02.png" title="This is a Root Domain with a Child Domain" >}}

### Tree

When you have a child domain within the same Root Domain it is referred to 'being in the same Tree'. They are however still separate domains. Each Domain needs at least 1 separate Domain Controller. This means that each Domain in a Tree has its own [Active Directory Database (NTDS)](#ntds) with its own objects such users, groups etc.

{{< figure src="domain_tree_forest_03.png" title="This is what the Tree looks like." >}}

A tree can consist of multiple child domains, they can even inherent from each other, but there can only be 1 Root Domain, this is also refered to as the Tree Root. The advantage of creating these child domains from the Tree Root is that there is a trust created between each of the domains. This means that users from `monkeys` child domain can access resources in the `pirates` child domain, if they would have the appropriate rights to that resource of course.

{{< figure src="domain_tree_forest_04.png" title="Domains can have multiple child domains, including child domains themselves" >}}

### Forest

Now lets say that over time the TFLJPP company grows and acquires another company, 'Wally B. Feed Cartography and Co'.
The acquired company already has a AD configured with their own Tree. You could migrate over all the users/systems from this over to your Tree, but this can be a daunting and time consuming task. So what we can do is add their Tree to our Forest. Doing this adds a trust between these two tree's. This means that, like with child domains, access to resources can now be shared cross company.

{{< figure src="domain_tree_forest_05.png" title="This is wat a Forest looks like with multiple Tree's" >}}

{{% notice note %}}
There are actually other types of trusts, such as shortcut, forest, external and realm trusts. Each with different characteristics (Transitive vs. Non-Transitive), direction types (One-way or Two-way) and authentication mechanism (Kerberos V5 or NTLM). I won't go into detail's here since if I where to cover it fully it would require a lot more of preexisting knowledge of AD internals such as NTLM and Kerberos, which are even heavy topics to cover on their own. Just remember that I generally recommend against multiple domains/tree's/forest and trusts due the added complexity and security risks, unless you truly understand what you are doing/are building a Red Forest.
{{% /notice %}}

### What we currently build

A forest can incases multiple domains and trees into 1 structure, but doesn't have to. We actually already created a Forest and a tree when we setup Active Directory. These are created automatically.

{{< figure src="domain_tree_forest_06.png" title="This what a setup with a singular domain a actually looks like." >}}
