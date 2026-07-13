# Ubuntu Server Installation

## Goal

Learn how Linux manages local user accounts, groups, and admin privileges.

## Hardware

Laptop: Dell Latitude 5480

CPU: Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz

RAM: 14Gi

Storage: 465.8G HDD

## Screenshots

See the images in `/images/usermanagement/`.

## Proccess

First I logged in with the credentials I established during the installation of the Ubuntu Server OS which I did in the previous stage of this project.  Then I ran the following to get an idea of what exactly I was starting with:

1. `whoami` which displayed the current username of "griffinv".
2. `hostname` which displays the name of the device, in this case "homearchive".
3. `pwd` which displays the path name of the current working directory, "/home/griffinv"
4. `groups` which displayed the current group memberships of the user I was logged in as: "griffinv, adm, cdrom, sudo, dip, plugdev, users, lxd"
5. `id` which printed more details regarding user and group information.

I then used `cat /etc/passwd` to view all the accounts on the system, and took note of accounts such as "root", "daemon", and "www-data" which is an account sometimes found on webservers.