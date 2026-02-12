Given our IP-address of 192.168.222.107 using the tool nmap to scan for open ports

Press enter or click to view image in full size

We get two open three open ports 21 with ftp service, 22 with ssh service and 80 with http service.Taking a look at the website and its page source below

Press enter or click to view image in full size

I didn’t find anything interesting,so i tried accessing the ftp server and surprisingly to me using username as anonymous and leaving the password prompt back i was able to login into the server

Press enter or click to view image in full size

And first thing i did was to see its contents using the ls command

Press enter or click to view image in full size

We see many zip files and a welcome.msg. So i Tried to get the message using command “ get welcome.msg” and in my machines directory which i was at i opened it but didn't get any interesting info.I moved ahead and downloaded all the zip files, see below


After the transfer was complete, i tried to unzip the anna.zip file but it was unsuccessful since it required id_rsa password shown below


So i had to use the fcrackzip tool and the rockyou.txt file to crack the password to unzip tom.zip and it was sucessful


We got the password to successfully unzip tom.zip shown below,with its contents


of id_rsa which contained a private_key which we are going to use to login to the open ssh port with username tom,the target-IP and the id_rsa key


And we were successfully logged in into the funbox2, and firstly we see what it contains using ls command and we find file to our first flag local.txt


First flag capturedd!! Moving to the next we need to perform a privilege escalation. And first on listing all available files in our directory we find an interesting mysql_history file and on looking at its content we find the password which could possibly be tom’s rot password


So on trying again sudo -l command we enter the password we got from above and we see that now tom can run all commands


Next we run script /dev/null -c bash command to get an interactive shell and now we have root privileges and have performed privilege escalation.And i searched for the proof.txt file which was present and we looked onto its content and found the last flag for our lab!


Hopefully you were also successful to get the flag. Please follow for more contents like this
