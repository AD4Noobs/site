---
title: "Deploy a new file server"
date: 2021-02-23T14:27:22+01:00
draft: false
weight: 2
pre: "<b>5.2 </b>"
---

By now you should know how to deploy a VM using the templates and add it to the Domain so I won't explain it again in full details.

Do the following:
- Create a new Server 2019 VM named fs01.ad.tfljpp.test.
  - Ensure you update the network to our custom NAT Network
- Rename the Server to FS01
- Give the the following network configuration

| What    | value         |
| ------- | ------------- |
| IP      | 10.11.12.50   |
| Mask    | 255.255.255.0 |
| Gateway | 10.11.12.1    |
| DNS     | 10.11.12.10   |

- Add server to the domain.
- Create a Servers OU
  - Create a FS OU
  - Place the computer object in the `TFLJPP\Servers\FS` OU.