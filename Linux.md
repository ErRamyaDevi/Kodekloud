# Tasks 1: Custom Apache User Setup:

### thor@jumphost ~$ ssh tony@172.16.238.10
### tony@172.16.238.10's password: 
### [tony@stapp01 ~]$ sudo su
### [root@stapp01 tony]# id kareem
##### id: ‘kareem’: no such user
### [root@stapp01 tony]# useradd -u 1351 kareem
### [root@stapp01 tony]# cat /etc/passwd |grep kareem
##### kareem:x:1351:1351::/home/kareem:/bin/bash
### [root@stapp01 tony]# id kareem
##### uid=1351(kareem) gid=1351(kareem) groups=1351(kareem)
### [root@stapp01 tony]# usermod -d /var/www/kareem -m kareem
### [root@stapp01 tony]# cat /etc/passwd |grep kareem
##### kareem:x:1351:1351::/var/www/kareem:/bin/bash
