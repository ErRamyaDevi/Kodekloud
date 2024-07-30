# Tasks 1: Custom Apache User Setup: Ref ID:64688003c1ff5e7e05478dca
## >>Kareem is User Name<<
## >>1351 is the ID needs to be assigned to user kareem<<

### thor@jumphost ~$ ssh tony@172.16.238.10
### tony@172.16.238.10's password: 
### [tony@stapp01 ~]$ sudo su
### [root@stapp01 tony]# id kareem [checking in root file whether the user is already present or not?]
##### id: ‘kareem’: no such user
### [root@stapp01 tony]# useradd -u 1351 kareem
### [root@stapp01 tony]# cat /etc/passwd |grep kareem [To view the Current directory where user is located]
##### kareem:x:1351:1351::/home/kareem:/bin/bash [Home directory]
### [root@stapp01 tony]# id kareem
##### uid=1351(kareem) gid=1351(kareem) groups=1351(kareem)
### [root@stapp01 tony]# usermod -d /var/www/kareem -m kareem [To change the directory given]
### [root@stapp01 tony]# cat /etc/passwd |grep kareem
##### kareem:x:1351:1351::/var/www/kareem:/bin/bash


# Task 2: Group Creation and User Assignment:- a. Create a group named nautilus_noc across all App servers within the Stratos Datacenter. b. Add the user mohammed into the nautilus_noc group on all App servers. If the user doesn't exist, create it as well.

### [root@stapp02 steve]# ssh banner@172.16.238.12
##### The authenticity of host '172.16.238.12 (172.16.238.12)' can't be established. ED25519 key fingerprint is SHA256:B19E1+vK5G2Qpiwg2kC67nppKfQn0mFLpfBMWGwZMpw. This key is not known by any other names.Are you sure you want to continue connecting (yes/no/[fingerprint])? yes  
##### Warning: Permanently added '172.16.238.12' (ED25519) to the list of known hosts.
### banner@172.16.238.12's password: 
### [banner@stapp03 ~]$ sudo su


### [sudo] password for banner: 
### [root@stapp03 banner]# useradd <name>mohammed [To add new user]
### [root@stapp03 banner]# id mohammed [To view the user ID]
##### uid=1002(mohammed) gid=1002(mohammed) groups=1002(mohammed)
### [root@stapp03 banner]# groupadd <name>nautilus_noc [To add Group]
### [root@stapp03 banner]# sudo tail /etc/group (to check group created and no.of users in it) [group_name : password : group-id : list-of-members]
##### systemd-journal:x:190:
##### systemd-coredump:x:997:
##### dbus:x:81:
##### ssh_keys:x:101:
##### sshd:x:74:
##### ansible:x:1000:
##### banner:x:1001:
##### sgx:x:996:
##### mohammed:x:1002:
##### nautilus_noc:x:1003:
### [root@stapp03 banner]# sudo usermod -a -G <groupname>nautilus_noc <username>mohammed [To add an user to a group]
### [root@stapp03 banner]# sudo tail /etc/group
##### systemd-journal:x:190:
##### systemd-coredump:x:997:
##### dbus:x:81:
##### ssh_keys:x:101:
##### sshd:x:74:
##### ansible:x:1000:
##### banner:x:1001:
##### sgx:x:996:
##### mohammed:x:1002:
##### nautilus_noc:x:1003:mohammed
### [root@stapp03 banner]# id mohammed
##### uid=1002(mohammed) gid=1002(mohammed) groups=1002(mohammed),1003(nautilus_noc)
### [root@stapp03 banner]# 
