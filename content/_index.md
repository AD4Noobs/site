---
title: "AD4Noobs"
date: 2021-02-08T15:34:40+01:00
draft: false
weight: 1
---

# AD4Noobs

So you want to learn the in and outs of getting started with Active Directory ? Well then you came to the right place ! If you don't care about this preface stuff just click on the arrow on the right or use the navigation on the top left if you are on mobile. This will take you to the first needed steps to get started.

{{< figure src="explain_ad.png" title="Its not that complicated, not at all. Trust me!" >}}

## Why I created this

Over the last couple of years I came into contact with young people who want to enter the InfoSec field, most of which who don't have an background in IT. {{%expand "Whenever I or someone else brought up something about Active Directory almost no one knew what it was or what it was used for. The fact that most of the time a  general explication like 'Active Directory is like a database for users and computers' was given wasn't helping that." %}}
Probably because I used it a lot in my past jobs and since after I started doing 'the cybers' I like to [tinker](https://sensepost.com/blog/2020/ace-to-rce/) with it. {{% /expand%}}

After starting a job as an Ethical Hacker I came into contact with a lot of internal networks. Pretty much on all these internal assessments Active Directory (and everything that comes with it) was the weakest link or was heavily part of me gaining administrative access in the network. This leads me to believe that there is a general lack of Active Directory knowledge or it's missing from where it matters the most. I think this is perfectly backed up if you look at the current state of malware, and more specifically cryptoware/ransomware.

{{< figure src="ad_ransomware.png?width=25pc"  title="Just google 'ransomware active directory'" >}}

So when I got the chance to give a 2 day workshop on Active Directory I decided to create this, for lack of better words, guide. I personally think that the best way to learn this stuff is by doing it, though at some points some explication can help with the learning process and avoid common pitfalls.

The main goal of this guide is to get someone without any Active Directory knowledge up and running with the basics, though if possible I'd like to extend this to include common misconfigurations. The 'perfect endgoal' would be to have this guide fully cover known attack methods so I can also refer IT professionals to this site.
I would like to cover them along the following lines:

- How these are created/or why they exists by default in Active Directory;
- How they can be exploited;
- How someone can fix and/or prevent them from happening in the first place.

If you work in the IT/InfoSec field and feel inclined to help with this endeavour you can submit a [PR on github](https://github.com/AD4Noobs/site) or get in contact with me on [Twitter](https://twitter.com/justinperdok).
