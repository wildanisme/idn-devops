# Simple Apps NodeJS

Created by: den
Created time: July 24, 2023 10:08 PM
Doc stage: New
Tags: Engineering

# RUNNING SIMPLE APPS WITH NODE JS

Provisioning Server Linux

- Network Static
- apt update
- Change hostname

## Connect GitHub on Linux Ubuntu Server with ssh key

On Linux 

```bash
root@devops:~# **ssh-keygen -t rsa**
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): **enter**
Enter passphrase (empty for no passphrase): **enter**
Enter same passphrase again: **enter**
Your identification has been saved in /root/.ssh/id_rsa
Your public key has been saved in /root/.ssh/id_rsa.pub
The key fingerprint is: **enter**
SHA256:h/u+hjEQEiyQ/tMnp8JqR5r95rb51lc9nmcEYHWxk6Y root@devops
The key's randomart image is: **enter**
+---[RSA 3072]----+
|.o ...       ...o|
|. . o .     o  .o|
|.  . . .   . . = |
| .    .  .    + .|
|  . .  .S .  E.. |
|   + o ooo   . o.|
|  * . = o+  . ..o|
| + = +...o..   oo|
|..o *=+. o=.   ..|
+----[SHA256]-----+
root@devops:~# 
root@devops:~# **cat .ssh/id_rsa.pub** 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCzVXWC7Ksmn4FOJQawRgVp5ztTnyHud+l/zTph+FEPFYkejVLWA/2EvBJXtm2FC0PjWEn94P9yx3AOa9bKtvqwOvJwOxx0uPNgfXEvsmfGtAIJ3jmvGuDGdUNQCl5ivmWtj1MT2qmAwQMJ5RRi5NFvSJNZ9Bielykm7z7ektlpvJ/Kih9Navz/lcaNsKHvGyZlxWp+/LBy0SP9oNnLzHmC7MBgUepNiLQvaLnp0cB5xz3sX8fBqpz4q1smtDDgcu4G+5W+fQ6qBKLoDThHz8OA2GGpIhFX2ffhcMltAPBNyPmH2H6GCyV3N9QxsvlFbZzjVIJYMN8Mwyvf7rjTNbNLJDmOOVeiZeX/Bb2Bn0Cmx6PyhQoVRErH1a+jyIsUQcNHL5gI2EBbhO1gq5VMItzTI+aODT6ytHRK3NZod0xaQ3AlRSZavDJ13lCeqi6XGE78Ipka2ei5M8LPVNvJKeBHpGXrNDpNifW4eqaMVQMABgPdHEQLkEfqqry5+p4V+UU= root@devops
root@devops:~#
```

Copy all text on file id_rsa.pub to ssh github

![Screenshot 2023-07-24 at 22.17.23.png](Simple%20Apps%20NodeJS%20894d3a901ba94ab189ffb3f1a595a555/Screenshot_2023-07-24_at_22.17.23.png)

lalu fork [dbyna/](https://github.com/IDN-Training/simple-apps)simple-apps & cloning

![Screenshot 2023-07-24 at 22.27.19.png](Simple%20Apps%20NodeJS%20894d3a901ba94ab189ffb3f1a595a555/Screenshot_2023-07-24_at_22.27.19.png)

![Screenshot 2023-07-24 at 22.27.59.png](Simple%20Apps%20NodeJS%20894d3a901ba94ab189ffb3f1a595a555/Screenshot_2023-07-24_at_22.27.59.png)

Cloning Simple Apps Repository user github ssh

```bash
root@devops:~# git clone git@github.com:IDN-Training/simple-apps.git
Cloning into 'simple-apps'...
The authenticity of host 'github.com (20.205.243.166)' can't be established.
ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,20.205.243.166' (ECDSA) to the list of known hosts.
remote: Enumerating objects: 290, done.
remote: Counting objects: 100% (61/61), done.
remote: Compressing objects: 100% (17/17), done.
remote: Total 290 (delta 50), reused 44 (delta 44), pack-reused 229
Receiving objects: 100% (290/290), 139.75 KiB | 307.00 KiB/s, done.
Resolving deltas: 100% (128/128), done.
root@devops:~#
```

Install NodeJS Version 18

```bash
root@devops:~# curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - &&\
> sudo apt-get install -y nodejs

## Installing the NodeSource Node.js 18.x repo...

## Populating apt-get cache...

+ apt-get update
Hit:1 http://id.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://id.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:3 http://id.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:4 http://id.archive.ubuntu.com/ubuntu focal-security InRelease
Reading package lists... Done

## Confirming "focal" is supported...

+ curl -sLf -o /dev/null 'https://deb.nodesource.com/node_18.x/dists/focal/Release'

## Adding the NodeSource signing key to your keyring...

+ curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | gpg --dearmor | tee /usr/share/keyrings/nodesource.gpg >/dev/null

## Creating apt sources list file for the NodeSource Node.js 18.x repo...

+ echo 'deb [signed-by=/usr/share/keyrings/nodesource.gpg] https://deb.nodesource.com/node_18.x focal main' > /etc/apt/sources.list.d/nodesource.list
+ echo 'deb-src [signed-by=/usr/share/keyrings/nodesource.gpg] https://deb.nodesource.com/node_18.x focal main' >> /etc/apt/sources.list.d/nodesource.list

## Running `apt-get update` for you...

+ apt-get update
Hit:1 http://id.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://id.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:3 http://id.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:4 http://id.archive.ubuntu.com/ubuntu focal-security InRelease
Get:5 https://deb.nodesource.com/node_18.x focal InRelease [4,583 B]
Get:6 https://deb.nodesource.com/node_18.x focal/main amd64 Packages [775 B]
Fetched 5,358 B in 1s (5,689 B/s) 
Reading package lists... Done

## Run `sudo apt-get install -y nodejs` to install Node.js 18.x and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
     echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 libxmlb1
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  nodejs
0 upgraded, 1 newly installed, 0 to remove and 63 not upgraded.
Need to get 28.9 MB of archives.
After this operation, 188 MB of additional disk space will be used.
Get:1 https://deb.nodesource.com/node_18.x focal/main amd64 nodejs amd64 18.17.0-deb-1nodesource1 [28.9 MB]
Fetched 28.9 MB in 5s (5,820 kB/s) 
Selecting previously unselected package nodejs.
(Reading database ... 108654 files and directories currently installed.)
Preparing to unpack .../nodejs_18.17.0-deb-1nodesource1_amd64.deb ...
Unpacking nodejs (18.17.0-deb-1nodesource1) ...
Setting up nodejs (18.17.0-deb-1nodesource1) ...
Processing triggers for man-db (2.9.1-1) ...
root@devops:~#
```

Install MariadDB-Server

```bash
root@devops:~# apt install mariadb-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 libxmlb1
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  galera-3 libcgi-fast-perl libcgi-pm-perl libconfig-inifiles-perl libdbd-mysql-perl libdbi-perl
  libencode-locale-perl libfcgi-perl libhtml-parser-perl libhtml-tagset-perl libhtml-template-perl
  libhttp-date-perl libhttp-message-perl libio-html-perl liblwp-mediatypes-perl libmysqlclient21 libsnappy1v5
  libterm-readkey-perl libtimedate-perl liburi-perl mariadb-client-10.3 mariadb-client-core-10.3
  mariadb-common mariadb-server-10.3 mariadb-server-core-10.3 mysql-common socat
Suggested packages:
  libclone-perl libmldbm-perl libnet-daemon-perl libsql-statement-perl libdata-dump-perl
  libipc-sharedcache-perl libwww-perl mailx mariadb-test tinyca
The following NEW packages will be installed:
  galera-3 libcgi-fast-perl libcgi-pm-perl libconfig-inifiles-perl libdbd-mysql-perl libdbi-perl
  libencode-locale-perl libfcgi-perl libhtml-parser-perl libhtml-tagset-perl libhtml-template-perl
  libhttp-date-perl libhttp-message-perl libio-html-perl liblwp-mediatypes-perl libmysqlclient21 libsnappy1v5
  libterm-readkey-perl libtimedate-perl liburi-perl mariadb-client-10.3 mariadb-client-core-10.3
  mariadb-common mariadb-server mariadb-server-10.3 mariadb-server-core-10.3 mysql-common socat
0 upgraded, 28 newly installed, 0 to remove and 63 not upgraded.
Need to get 21.5 MB of archives.
After this operation, 175 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://id.archive.ubuntu.com/ubuntu focal/main amd64 mysql-common all 5.8+1.0.5ubuntu2 [7,496 B]
Get:2 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 mariadb-common all 1:10.3.38-0ubuntu0.20.04.1 [15.9 kB]
Get:3 http://id.archive.ubuntu.com/ubuntu focal/universe amd64 galera-3 amd64 25.3.29-1 [898 kB]
Get:4 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libdbi-perl amd64 1.643-1ubuntu0.1 [730 kB]
Get:5 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libconfig-inifiles-perl all 3.000002-1 [40.6 kB]
Get:6 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libsnappy1v5 amd64 1.1.8-1build1 [16.7 kB]
Get:7 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 mariadb-client-core-10.3 amd64 1:10.3.38-0ubuntu0.20.04.1 [5,855 kB]
Get:8 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 mariadb-client-10.3 amd64 1:10.3.38-0ubuntu0.20.04.1 [1,129 kB]
Get:9 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 mariadb-server-core-10.3 amd64 1:10.3.38-0ubuntu0.20.04.1 [6,249 kB]
Get:10 http://id.archive.ubuntu.com/ubuntu focal/main amd64 socat amd64 1.7.3.3-2 [323 kB]
Get:11 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 mariadb-server-10.3 amd64 1:10.3.38-0ubuntu0.20.04.1 [4,203 kB]
Get:12 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libhtml-tagset-perl all 3.20-4 [12.5 kB]
Get:13 http://id.archive.ubuntu.com/ubuntu focal/main amd64 liburi-perl all 1.76-2 [77.5 kB]
Get:14 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libhtml-parser-perl amd64 3.72-5 [86.3 kB]
Get:15 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libcgi-pm-perl all 4.46-1 [186 kB]
Get:16 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libfcgi-perl amd64 0.79-1 [33.1 kB]
Get:17 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libcgi-fast-perl all 1:2.15-1 [10.5 kB]
Get:18 http://id.archive.ubuntu.com/ubuntu focal-updates/main amd64 libmysqlclient21 amd64 8.0.33-0ubuntu0.20.04.2 [1,326 kB]
Get:19 http://id.archive.ubuntu.com/ubuntu focal/universe amd64 libdbd-mysql-perl amd64 4.050-3 [82.8 kB]
Get:20 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libencode-locale-perl all 1.05-1 [12.3 kB]
Get:21 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libhtml-template-perl all 2.97-1 [59.0 kB]
Get:22 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libtimedate-perl all 2.3200-1 [34.0 kB]
Get:23 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libhttp-date-perl all 6.05-1 [9,920 B]
Get:24 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libio-html-perl all 1.001-1 [14.9 kB]
Get:25 http://id.archive.ubuntu.com/ubuntu focal/main amd64 liblwp-mediatypes-perl all 6.04-1 [19.5 kB]
Get:26 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libhttp-message-perl all 6.22-1 [76.1 kB]
Get:27 http://id.archive.ubuntu.com/ubuntu focal/main amd64 libterm-readkey-perl amd64 2.38-1build1 [24.6 kB]
Get:28 http://id.archive.ubuntu.com/ubuntu focal-updates/universe amd64 mariadb-server all 1:10.3.38-0ubuntu0.20.04.1 [12.7 kB]
Fetched 21.5 MB in 4s (5,757 kB/s)          
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 114344 files and directories currently installed.)
Preparing to unpack .../0-mysql-common_5.8+1.0.5ubuntu2_all.deb ...
Unpacking mysql-common (5.8+1.0.5ubuntu2) ...
Selecting previously unselected package mariadb-common.
Preparing to unpack .../1-mariadb-common_1%3a10.3.38-0ubuntu0.20.04.1_all.deb ...
Unpacking mariadb-common (1:10.3.38-0ubuntu0.20.04.1) ...
Selecting previously unselected package galera-3.
Preparing to unpack .../2-galera-3_25.3.29-1_amd64.deb ...
Unpacking galera-3 (25.3.29-1) ...
Selecting previously unselected package libdbi-perl:amd64.
Preparing to unpack .../3-libdbi-perl_1.643-1ubuntu0.1_amd64.deb ...
Unpacking libdbi-perl:amd64 (1.643-1ubuntu0.1) ...
Selecting previously unselected package libconfig-inifiles-perl.
Preparing to unpack .../4-libconfig-inifiles-perl_3.000002-1_all.deb ...
Unpacking libconfig-inifiles-perl (3.000002-1) ...
Selecting previously unselected package libsnappy1v5:amd64.
Preparing to unpack .../5-libsnappy1v5_1.1.8-1build1_amd64.deb ...
Unpacking libsnappy1v5:amd64 (1.1.8-1build1) ...
Selecting previously unselected package mariadb-client-core-10.3.
Preparing to unpack .../6-mariadb-client-core-10.3_1%3a10.3.38-0ubuntu0.20.04.1_amd64.deb ...
Unpacking mariadb-client-core-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Selecting previously unselected package mariadb-client-10.3.
Preparing to unpack .../7-mariadb-client-10.3_1%3a10.3.38-0ubuntu0.20.04.1_amd64.deb ...
Unpacking mariadb-client-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Selecting previously unselected package mariadb-server-core-10.3.
Preparing to unpack .../8-mariadb-server-core-10.3_1%3a10.3.38-0ubuntu0.20.04.1_amd64.deb ...
Unpacking mariadb-server-core-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Selecting previously unselected package socat.
Preparing to unpack .../9-socat_1.7.3.3-2_amd64.deb ...
Unpacking socat (1.7.3.3-2) ...
Setting up mysql-common (5.8+1.0.5ubuntu2) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Setting up mariadb-common (1:10.3.38-0ubuntu0.20.04.1) ...
update-alternatives: using /etc/mysql/mariadb.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mariadb-server-10.3.
(Reading database ... 114728 files and directories currently installed.)
Preparing to unpack .../00-mariadb-server-10.3_1%3a10.3.38-0ubuntu0.20.04.1_amd64.deb ...
Unpacking mariadb-server-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Selecting previously unselected package libhtml-tagset-perl.
Preparing to unpack .../01-libhtml-tagset-perl_3.20-4_all.deb ...
Unpacking libhtml-tagset-perl (3.20-4) ...
Selecting previously unselected package liburi-perl.
Preparing to unpack .../02-liburi-perl_1.76-2_all.deb ...
Unpacking liburi-perl (1.76-2) ...
Selecting previously unselected package libhtml-parser-perl.
Preparing to unpack .../03-libhtml-parser-perl_3.72-5_amd64.deb ...
Unpacking libhtml-parser-perl (3.72-5) ...
Selecting previously unselected package libcgi-pm-perl.
Preparing to unpack .../04-libcgi-pm-perl_4.46-1_all.deb ...
Unpacking libcgi-pm-perl (4.46-1) ...
Selecting previously unselected package libfcgi-perl.
Preparing to unpack .../05-libfcgi-perl_0.79-1_amd64.deb ...
Unpacking libfcgi-perl (0.79-1) ...
Selecting previously unselected package libcgi-fast-perl.
Preparing to unpack .../06-libcgi-fast-perl_1%3a2.15-1_all.deb ...
Unpacking libcgi-fast-perl (1:2.15-1) ...
Selecting previously unselected package libmysqlclient21:amd64.
Preparing to unpack .../07-libmysqlclient21_8.0.33-0ubuntu0.20.04.2_amd64.deb ...
Unpacking libmysqlclient21:amd64 (8.0.33-0ubuntu0.20.04.2) ...
Selecting previously unselected package libdbd-mysql-perl:amd64.
Preparing to unpack .../08-libdbd-mysql-perl_4.050-3_amd64.deb ...
Unpacking libdbd-mysql-perl:amd64 (4.050-3) ...
Selecting previously unselected package libencode-locale-perl.
Preparing to unpack .../09-libencode-locale-perl_1.05-1_all.deb ...
Unpacking libencode-locale-perl (1.05-1) ...
Selecting previously unselected package libhtml-template-perl.
Preparing to unpack .../10-libhtml-template-perl_2.97-1_all.deb ...
Unpacking libhtml-template-perl (2.97-1) ...
Selecting previously unselected package libtimedate-perl.
Preparing to unpack .../11-libtimedate-perl_2.3200-1_all.deb ...
Unpacking libtimedate-perl (2.3200-1) ...
Selecting previously unselected package libhttp-date-perl.
Preparing to unpack .../12-libhttp-date-perl_6.05-1_all.deb ...
Unpacking libhttp-date-perl (6.05-1) ...
Selecting previously unselected package libio-html-perl.
Preparing to unpack .../13-libio-html-perl_1.001-1_all.deb ...
Unpacking libio-html-perl (1.001-1) ...
Selecting previously unselected package liblwp-mediatypes-perl.
Preparing to unpack .../14-liblwp-mediatypes-perl_6.04-1_all.deb ...
Unpacking liblwp-mediatypes-perl (6.04-1) ...
Selecting previously unselected package libhttp-message-perl.
Preparing to unpack .../15-libhttp-message-perl_6.22-1_all.deb ...
Unpacking libhttp-message-perl (6.22-1) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../16-libterm-readkey-perl_2.38-1build1_amd64.deb ...
Unpacking libterm-readkey-perl (2.38-1build1) ...
Selecting previously unselected package mariadb-server.
Preparing to unpack .../17-mariadb-server_1%3a10.3.38-0ubuntu0.20.04.1_all.deb ...
Unpacking mariadb-server (1:10.3.38-0ubuntu0.20.04.1) ...
Setting up libconfig-inifiles-perl (3.000002-1) ...
Setting up libmysqlclient21:amd64 (8.0.33-0ubuntu0.20.04.2) ...
Setting up libhtml-tagset-perl (3.20-4) ...
Setting up liblwp-mediatypes-perl (6.04-1) ...
Setting up libencode-locale-perl (1.05-1) ...
Setting up libsnappy1v5:amd64 (1.1.8-1build1) ...
Setting up socat (1.7.3.3-2) ...
Setting up mariadb-server-core-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Setting up libio-html-perl (1.001-1) ...
Setting up galera-3 (25.3.29-1) ...
Setting up libtimedate-perl (2.3200-1) ...
Setting up mariadb-client-core-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Setting up libfcgi-perl (0.79-1) ...
Setting up libterm-readkey-perl (2.38-1build1) ...
Setting up liburi-perl (1.76-2) ...
Setting up libdbi-perl:amd64 (1.643-1ubuntu0.1) ...
Setting up libhttp-date-perl (6.05-1) ...
Setting up mariadb-client-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Setting up libdbd-mysql-perl:amd64 (4.050-3) ...
Setting up libhtml-parser-perl (3.72-5) ...
Setting up mariadb-server-10.3 (1:10.3.38-0ubuntu0.20.04.1) ...
Created symlink /etc/systemd/system/mysql.service → /lib/systemd/system/mariadb.service.
Created symlink /etc/systemd/system/mysqld.service → /lib/systemd/system/mariadb.service.
Created symlink /etc/systemd/system/multi-user.target.wants/mariadb.service → /lib/systemd/system/mariadb.service.
Setting up libhttp-message-perl (6.22-1) ...
Setting up libcgi-pm-perl (4.46-1) ...
Setting up libhtml-template-perl (2.97-1) ...
Setting up mariadb-server (1:10.3.38-0ubuntu0.20.04.1) ...
Setting up libcgi-fast-perl (1:2.15-1) ...
Processing triggers for systemd (245.4-4ubuntu3.20) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
root@devops:~#
```

edit file mariadb server untuk melisten 1 jaringanya 

```bash
root@devops:~# vim /etc/mysql/mariadb.conf.d/50-server.cnf
bind-address            = 10.23.0.113 # ip dirinya sendiri
root@devops:~# systemctl restart mariadb
```

setting database mariadb & import database

```bash
root@devops:~# mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 36
Server version: 10.3.38-MariaDB-0ubuntu0.20.04.1 Ubuntu 20.04

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> create database training;
Query OK, 1 row affected (0.000 sec)

MariaDB [(none)]> grant all privileges on training.* to 'peserta'@'%' identified by 'password';
Query OK, 0 rows affected (0.001 sec)

MariaDB [(none)]> flush privileges;
Query OK, 0 rows affected (0.000 sec)

MariaDB [(none)]> quit;
Bye
root@devops:~# cd simple-apps/
root@devops:~/simple-apps# mysql -u peserta -p training < database/training.sql
Enter password: 
root@devops:~/simple-apps# mysql -u peserta -p training -e "show tables;"
Enter password: 
+--------------------+
| Tables_in_training |
+--------------------+
| tb_data            |
+--------------------+
root@devops:~/simple-apps#
```

create file .env untuk koneksi dari applikasi ke database

```bash
root@devops:~/simple-apps# vim .env
DB_NAME = training
DB_HOST = 10.23.0.113
DB_USER = peserta
DB_PASS = password
APP_PORT = 3000

```

Install modul yang ada di file package json

```bash
root@devops:~/simple-apps# npm install

added 514 packages, and audited 515 packages in 28s

43 packages are looking for funding
  run `npm fund` for details

3 moderate severity vulnerabilities

To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.
npm notice 
npm notice New minor version of npm available! 9.6.7 -> 9.8.1
npm notice Changelog: https://github.com/npm/cli/releases/tag/v9.8.1
npm notice Run npm install -g npm@9.8.1 to update!
npm notice 
root@devops:~/simple-apps#
```

Jalankan aplikasi

```bash
root@devops:~/simple-apps# npm start

> simple-apps@1.0.0 start
> node app

Example app listening on port 3000
```

Verifikasi

![Screenshot 2023-07-24 at 22.53.23.png](Simple%20Apps%20NodeJS%20894d3a901ba94ab189ffb3f1a595a555/Screenshot_2023-07-24_at_22.53.23.png)

/app1

/app2

/users

3 buah testing

Unit testing = sangat Cepat, terisoloasi, efesiensi biaya, setiap function akan dicek (dev)
Service/integration = gak Cepat, dan gak lama = simple app, client -> apps -> database (dev)
Ui testing = penegecekan keseluruhan applikasi (qa)

perintah untuk melakukan integration testing/ unit testing, ini hanya mengcek functionnya jalan apa tidak

<aside>
💡 $ npm test

</aside>

[root@devops:~/simple-apps# npm test

> simple-apps@1.0.0 test
> jest --forceExit testing/

  console.log
    Example app listening on port 3000

      at Server.log (app.js:35:11)

  console.log
    http://127.0.0.1:41711/: 2023-07-24T23:10:32+07:00

      at log (middleware/logger.js:5:13)

  console.log
    http://127.0.0.1:41699/app1: 2023-07-24T23:10:32+07:00

      at log (middleware/logger.js:5:13)

  console.log
    http://127.0.0.1:35637/app2: 2023-07-24T23:10:32+07:00

      at log (middleware/logger.js:5:13)

  console.log
    http://127.0.0.1:44847/users: 2023-07-24T23:10:32+07:00

      at log (middleware/logger.js:5:13)

 PASS  testing/app.test.js
  Unit Test /
    ✓ should respond with index.html (108 ms)
  Unit Test /app1
    ✓ should respond with "Hello App1!" (14 ms)
  Unit Test /app2
    ✓ should respond with "Hello App2!" (10 ms)
  Integration Test Connect Database
    ✓ should respond with users data (22 ms)

Test Suites: 1 passed, 1 total
Tests:       4 passed, 4 total
Snapshots:   0 total
Time:        1.559 s
Ran all test suites matching /testing\//i.
Force exiting Jest: Have you considered using `--detectOpenHandles` to detect async operations that kept running after all tests finished?
root@devops:~/simple-apps#](https://www.notion.so/root-devops-simple-apps-npm-test-simple-apps-1-0-0-test-jest-forceExit-testing-console-5ab77608e1c944aab3fca11cc992d749?pvs=21)

test coverage lebih dalam lagi, walaupun di unit testing tidak ada masalah belum tentu kaidah penulisan sintak & algoritma itu sesuai dengan best practice.

- functionnya jalan apa gak
- statementnya jalan apa gak seperti if else nya sudah sesuai atau belum

tujuan dari test coverga ini misalkan ada variable yang sudah dibuat tetapi tidak digunakan, itu akan menjadi pertanyaa dan bisa2 memperlambat performa pada sebuah aplikasi

```bash
package.json 
--exitForce

root@devops:~/simple-apps# npm run test:coverage

> simple-apps@1.0.0 test:coverage
> jest --coverage --forceExit testing/

  console.log
    Example app listening on port 3000

      at Server.log (app.js:35:11)

  console.log
    http://127.0.0.1:46333/: 2023-07-24T23:22:30+07:00

      at log (middleware/logger.js:5:13)

  console.log
    http://127.0.0.1:39371/app1: 2023-07-24T23:22:30+07:00

      at log (middleware/logger.js:5:13)

  console.log
    http://127.0.0.1:46331/app2: 2023-07-24T23:22:30+07:00

      at log (middleware/logger.js:5:13)

  console.log
    http://127.0.0.1:46007/users: 2023-07-24T23:22:30+07:00

      at log (middleware/logger.js:5:13)

 PASS  testing/app.test.js
  Unit Test /
    ✓ should respond with index.html (107 ms)
  Unit Test /app1
    ✓ should respond with "Hello App1!" (18 ms)
  Unit Test /app2
    ✓ should respond with "Hello App2!" (10 ms)
  Integration Test Connect Database
    ✓ should respond with users data (22 ms)

------------------------|---------|----------|---------|---------|-------------------
File                    | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
------------------------|---------|----------|---------|---------|-------------------
All files               |   96.77 |       50 |     100 |   96.77 |                   
 simple-apps            |   95.45 |       50 |     100 |   95.45 |                   
  app.js                |   95.45 |       50 |     100 |   95.45 | 27                
 simple-apps/middleware |     100 |      100 |     100 |     100 |                   
  db_connect.js         |     100 |      100 |     100 |     100 |                   
  logger.js             |     100 |      100 |     100 |     100 |                   
------------------------|---------|----------|---------|---------|-------------------
Test Suites: 1 passed, 1 total
Tests:       4 passed, 4 total
Snapshots:   0 total
Time:        1.663 s, estimated 2 s
Ran all test suites matching /testing\//i.
Force exiting Jest: Have you considered using `--detectOpenHandles` to detect async operations that kept running after all tests finished?
root@devops:~/simple-apps#
```