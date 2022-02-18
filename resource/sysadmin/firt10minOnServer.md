---
tags: sysadmin linux server
---
> [context](https://sollove.com/2013/03/03/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers/) 
# linux server security on new system

    tldr how to keep servers safe in corpo env or just super paranoid

# reasoning bh article
when growing adding more servers and and devolpers use admin gets harder to maintain accses to server.

# configed with 2 accoutns 
server uses **2 account** root and deploy. **deploy has sudo** with long arb password dev log in with pub key. **root over ssh disabled** and user can only use **local ip block**.

# passwd
change root password to **long and complex** store somewhere safe. only if you lose login over ssh or lose sudo pass

# fail2ban
deamon that log login attempt and block sus

# deply user
 ```
useradd deploy
mkdir /home/deploy
mkdir /home/deploy/.ssh
chmod 700 /home/deploy/.ssh 
```
and require it to use **pubkey** logoin
> vim /home/deploy/.ssh/authorized_keys
> chmod 400 /home/deploy/.ssh/authorized_keys
> chown deploy:deploy /home/deploy -R
add all user that need key accses aswell

# enable sudo 
> passwd deploy

give account **sudo access** with password 
to deploy with 

>root    ALL=(ALL) ALL
deploy  ALL=(ALL) ALL

# lockdown ssh 
change so  no password and root login and **lock** ssh to particular ip. 
> vim /etc/ssh/sshd_config

    PermitRootLogin no
    PasswordAuthentication no
    AllowUsers deploy@(your-ip) deploy@(another-ip-if-any)
> service ssh restart

# firewall
use buildtin linux firewall add ports for services or **applic the server uses** ex: 3306 for mysql
```
ufw allow from {your-ip} to any port 22
ufw allow 80
ufw allow 443
ufw enable
```

# auto sec update
good praxis to have it on long running servers
>apt-get install unattended-upgrades
vim /etc/apt/apt.conf.d/10periodic

    APT::Periodic::Update-Package-Lists "1";
    APT::Periodic::Download-Upgradeable-Packages "1";
    APT::Periodic::AutocleanInterval "7";
    APT::Periodic::Unattended-Upgrade "1";

change so its only sec update 
> vim /etc/apt/apt.conf.d/50unattended-upgrades

    Unattended-Upgrade::Allowed-Origins {
            "Ubuntu lucid-security";
    //      "Ubuntu lucid-updates";
    };

# Logwatch 
Logwatch is a daemon that monitors your logs and emails them to you. This is useful for tracking and **detecting intrusion**. **Email** activity on server incase hacker alter on server docs
>apt-get install logwatch
vim /etc/cron.daily/00logwatch

## add line
    /usr/sbin/logwatch --output mail --mailto
    test@gmail.com --detail high