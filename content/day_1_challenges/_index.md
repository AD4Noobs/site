---
title: "Day 1 Challanges"
date: 2021-02-17T11:47:25+01:00
draft: False
weight: 6
pre: "<b>5. </b>"
---

## What we build today

Install Active Directory  
- root domain: `ad.tfljpp.test`  
- netbios: `TFLJPP\`
- hostname: `DC01`  
- IP: `10.11.12.10`  

Add a PC called PC01 to Domain.  
- hostname: `PC01`  
- IP: `10.11.12.100`  

## ADUC Challenges

Move PC01 to the Computer OU.  

Create OU's for:  
- `Users`, `Groups` and `Computers`.  

Create the following users in the OU:  
- `Guybrush Threepwood`  
- `Elaine Marley`  
- `Griswold Goudsoup`  
- `Eduard Van Helgen`  
- `Hagis McMutton`  
- `Cutthroat Bill`  
- `Monkey No.11`  
- `Monkey No.98`  
- `Monkey No.55`  
- `Monkey No.21`  

 Create the following groups:
 - `mighty pirates`
    - Add `Guybrush Threepwood`, `Eduard Van Helgen`, `Hagis McMutton` and `Cutthroat Bill` to this group.
 - illegal department
    - Add `Elaine Marley` and `Griswold Goudsoup` to this group.
  - office monkeys
    -  Add all the `Monkeys` to this group.

## GPO Challenges

Group Policy Objects allow you to customize the environment. Below are some challenges for you to try.

### Change the internet explorer home page for all the users (Easy)

- Create a GPO changes the Internet Explorer home page to www.google.nl and apply it to the user OU.
{{%expand "Tip" %}} If its red, press `F5`{{% /expand%}}

### Enable verbose login information (Medium)

- Create a GPO that enables `Display highly detailed status messages` and apply it to the computer OU.
{{%expand "Tip" %}} `gpupdate /force /sync /boot` {{% /expand%}}

### Change users internet home page for a group (Hard)

- Create a GPO changes the Internet Explorer home page to scummbar.com and apply it to the user OU but also ensure its only applied to users who are part of the `mighty pirates` 
{{%expand "Tip" %}} Deny `Apply group policy` for `Authenticated Users`, don`t remove it; Try Googling `GPO conflicts`{{% /expand%}}

### Deploy a new Password and Lockout Policy (Hard)

- Create a copy of the original `Default Domain Policy`
    {{%expand "Tip" %}}  Copy it. You don`t have to add all the settings by hand{{% /expand%}}
- Rename the copy to `[BACKUP] - Default Domain Policy`
- Create a new GPO called `[SECURITY] - Password Policy (Computer Policy)` that enforces the following Password Policy.
    - Password History: 24 passwords remembered
    - Max password age: 42 days
    - Min password age: 1 days
    - Min password length: 9
    - Password must meet complexity requirements: true
    - Store password using reversible encryption: false
- Create a new GPO called `[SECURITY] - Account lockout (Computer Policy)` that enforces the following Lockout Policy.
    - Account lockout threshold : 5 invalid login attempts
    - Account lockout duration : 30 Min
    - Reset account lockout after: 30 Min
- Link the `[SECURITY] - Account lockout (Computer Policy)` and `[SECURITY] - Password Policy (Computer Policy)` GPO's in the same place as the `Default Domain Policy`.
- Edit the original `Default Domain Policy` and disable the following settings:
    - Password History
    - Max password age
    - Min password age
    - Min password length
    - Password must meet complexity requirements
    - Store password using reversible encryption
- Create proof that this was applied.
    {{%expand "Tip" %}}  `gpupdate & gpresult` {{% /expand%}}
- Test if it was applied by creating a user with a weak (7 char) password.