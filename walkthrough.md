Given our IP-address of 192.168.222.107 using the tool nmap to scan for open ports

<img width="820" height="264" alt="image" src="https://github.com/user-attachments/assets/2e8aba2d-5db0-4cd0-a373-a1bbbc08ef3e" />


We get two open three open ports 21 with ftp service, 22 with ssh service and 80 with http service.Taking a look at the website and its page source below

<img width="1100" height="555" alt="image" src="https://github.com/user-attachments/assets/42492641-00ea-4600-a363-f408f3109f0f" />


I didn’t find anything interesting,so i tried accessing the ftp server and surprisingly to me using username as anonymous and leaving the password prompt back i was able to login into the server

<img width="810" height="297" alt="image" src="https://github.com/user-attachments/assets/c1f951f6-39cc-41c6-8bd9-2c18fa4206ee" />


And first thing i did was to see its contents using the ls command

<img width="810" height="297" alt="image" src="https://github.com/user-attachments/assets/45517b50-11bb-418c-a42a-a9020f88fba1" />


We see many zip files and a welcome.msg. So i Tried to get the message using command “ get welcome.msg” and in my machines directory which i was at i opened it but didn't get any interesting info.I moved ahead and downloaded all the zip files, see below

<img width="566" height="366" alt="image" src="https://github.com/user-attachments/assets/51e9c971-4fd6-4ac5-ac8e-f9dbe0272fbf" />


After the transfer was complete, i tried to unzip the anna.zip file but it was unsuccessful since it required id_rsa password shown below

<img width="569" height="160" alt="image" src="https://github.com/user-attachments/assets/a95cebd2-98c8-436a-a0d5-b79e65b64d63" />

So i had to use the fcrackzip tool and the rockyou.txt file to crack the password to unzip tom.zip and it was sucessful

<img width="563" height="103" alt="image" src="https://github.com/user-attachments/assets/2e0f462b-5521-4405-933d-8c32717b9f04" />


We got the password to successfully unzip tom.zip shown below,with its contents

<img width="563" height="103" alt="image" src="https://github.com/user-attachments/assets/3e3b30fc-bb70-4432-806d-c96dd577f892" />

of id_rsa which contained a private_key which we are going to use to login to the open ssh port with username tom,the target-IP and the id_rsa key

<img width="667" height="618" alt="image" src="https://github.com/user-attachments/assets/df08f718-dcea-4f4c-a9e3-1d2c7bb74d61" />

And we were successfully logged in into the funbox2, and firstly we see what it contains using ls command and we find file to our first flag local.txt

<img width="683" height="86" alt="image" src="https://github.com/user-attachments/assets/8a07bca9-7b1c-4b88-b20c-e37f0a321296" />

First flag capturedd!! Moving to the next we need to perform a privilege escalation. And first on listing all available files in our directory we find an interesting mysql_history file and on looking at its content we find the password which could possibly be tom’s root password
<img width="694" height="288" alt="image" src="https://github.com/user-attachments/assets/91294630-cc71-449e-815b-4e72dccbdfa4" />


So on trying again sudo -l command we enter the password we got from above and we see that now tom can run all commands
<img width="694" height="146" alt="image" src="https://github.com/user-attachments/assets/ca15d766-d9de-4239-b8bf-08af8c33817a" />



Next we run script /dev/null -c bash command to get an interactive shell and now we have root privileges and have performed privilege escalation.And i searched for the proof.txt file which was present and we looked onto its content and found the last flag for our lab!

<img width="694" height="81" alt="image" src="https://github.com/user-attachments/assets/870abf19-5a50-4979-9488-e9768f71f9e8" />

Hopefully you were also successful to get the flag. Please follow for more contents like this
