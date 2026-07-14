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

1. `whoami` which displayed the current username of "griffinv"
2. `hostname` which displays the name of the device, in this case "homearchive"
3. `pwd` which displays the path name of the current working directory, "/home/griffinv"
4. `groups` which displayed the current group memberships of the user I was logged in as: "griffinv, adm, cdrom, sudo, dip, plugdev, users, lxd"
5. `id` which printed more details regarding user and group information

I then used `cat /etc/passwd` to view all the accounts on the system, and took note of accounts such as "root", "daemon", and "www-data" which is an account sometimes found on webservers.

Following that, I used `sudo adduser labuser` to add a new user in addition to the root griffinv user I initally installed the OS with.  I created a password for the user, and left all the optional user information (Full Name, Roomer Number, Work/Home Phone, Other) as their defaults.  I used `id labuser` to confirm the creation of the new user, then `su - labuser` to switch to the newly created user after it asked for the password.  To explore and more fully verify the functionality of the user, I then used:

1. `whoami` to display the current user again
2. `pwd`to display the working directory "/home/labuser"
3. `groups` which displayed "labuser users" as the current groups
4. `touch test.exe` to create a file called text.exe
5. `mv test.exe test.txt` to rename that new file to test.txt
6. `ls` to view the contents of the current folder and confirm the file is there and is named correctly.

I then cleared the screen again (`clear`), and used `sudo usermod -aG sudo labuser` to attempt to add the labuser to the sudo group.  However, because I was still logged in as the labuser, it wasn't allowed and I had to switch to the root user and redo the command to add the "labuser" user to the sudo group.  I switched back to the labuser user and ran sudo apt update which asked for the password of labuser and not griffinv (because labuser now had sudo group permissions and was running a command under its authority rather than griffinv's).

