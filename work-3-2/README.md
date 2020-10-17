# Live Project work 3-2

This folder contains the configuration file to use to set up a VPN where a AWS EC2 instance works as server.

Public IP of EC2 onstance : **3.250.166.154**

## Server configuration

Folder [server](server) contains the wireguard configuration file ( server side ) and the export FS setting


## Client configuration

Folder [client](client) contains the wireguard configuration file ( client side )

## Test

### SSH connection

User can log in on server ```10.0.0.1``` using that **SAME** private key that he uses to log in using the public IP of EC2 instance.

```
$  ssh -i /home/piccio/.ssh/liveProject.pem ubuntu@10.0.0.1
Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-1024-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sat Oct 17 16:20:43 UTC 2020

  System load:  0.0               Processes:             122
  Usage of /:   18.7% of 7.69GB   Users logged in:       1
  Memory usage: 25%               IPv4 address for eth0: 172.31.33.53
  Swap usage:   0%                IPv4 address for wg0:  10.0.0.1


69 updates can be installed immediately.
34 of these updates are security updates.
To see these additional updates run: apt list --upgradable

Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings


Last login: Sat Oct 17 15:04:23 2020 from 151.61.0.1
```


### Access to shared folder

On server ```10.0.0.1```, as root, create the shared folder ```/nfs/shared```

```
# create -p /nfs/shared
```

On clients, as root, as root, create the shared folder ```/nfs/shared``` and mount the folder shader by server

```
# mount 10.0.0.1:/nfs/share /nfs/share
```

Now, user ( as root ) can write a file on the mounted folder

```
# touch  /nfs/share/test.dat
# ls  /nfs/share
test.dat
```