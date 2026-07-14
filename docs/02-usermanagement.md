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

`sudo passwd labuser` was run to change the password of labuser, then `sudo passwd -l labuser` to lock the account and `sudo passwd -u labuser` to unlock it, all to practice effective account management without deleting anything.  

Once I was done with that though, I ran `sudo deluser --remove-home labuser` to not only delete the user "labuser", but also to remove it's home directory as well.  However, I ran into a problem and wasn't sure why exactly the command wasn't working at first other than that it was still running a process.  I logged in as the root user instead thinking maybe the process was due to me still being logged in as labuser, but it still wouldn't remove the user.  I then used `ps -u labuser` as the root user to show what processes the user might still be running, and I saw processes related to bash.  I then used `who` to confirm if labuser still had an active session, which they did not since the command returned nothing.  I ran `sudo killall -u labuser` to terminate all processes related to the account, ran `ps -u labuser` to confirm it worked, then ran `sudo deluser --remove-home labuser` again to delete the account before confirming account deletion with `grep labuser /etc/passwd`.  Linux threw this error when I tried to delete the account because if that was an actual user possibly editing an important file, it wouldn't be a good idea to delete the account while that user is still running that process and so Linux activated this saftey feature in response, stopping the deletion from happening.