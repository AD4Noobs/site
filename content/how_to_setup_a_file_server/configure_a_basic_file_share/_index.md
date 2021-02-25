---
title: "Configure a basic file share"
date: 2021-02-25T14:35:45+01:00
draft: false
pre: "<b>5.3 </b>"
---

3 share groups (domain local)

- share_shared_data_r
- share_shared_data_rw
- share_shared_data_fc

9 fol groups (domain local)

- fol_shared_data_l
- fol_shared_data_office_monkeys_r
- fol_shared_data_office_monkeys_rw
- fol_shared_data_marketing_r
- fol_shared_data_marketing_rw
- fol_shared_data_illegal_r
- fol_shared_data_illegal_rw
- fol_shared_data_mighty_pirates_r
- fol_shared_data_mighty_pirates_rw

Add extra disk to file server  
format NTFS  
add folder shared_data  
share folder without $  
disable cache  
for share rights use groups  
setup list rights on shared_data folder  
create 4 folder  

- illegal  
- marketing  
- office monkeys  
- mighty pirates  
  
show what it looks like  
add $ to share name  
show that it is now hidden from being listed (add note that it can be listed using offensive tooling)  
temporally add user directly to share and list group.  
log of and on.  
show the share working  
show effective access

setup rights on folders (make note of RW = modify.)  
Add user to read group of one folder, write on the other.  
show it working  
switch over to ABE  
show what it does  
remove user from groups  
setup function profiles  
show it working  
explain it can be simplified with less groups in func groups.  
create func_all  
add all other function groups to func_all  
add func_all to fol_shared_data_l and share_shared_data_r  
add func_mighty_pirates to fol_shared_data_mighty_pirates_rw  
show it working  

recap  
share is made hidden with the use of $  
minimum needed to access share  
    Share Rights  
    list folder contents on the shared data folder  
The minimum rights are given to all the function groups through the func_all group.  
each folder gets a minimum of 2 fol groups, 1 for read and 1 for read write.  
these fol groups are added to func groups.  
users are then added to these func groups.  
To hide folders user don't have access to ABE is used  
