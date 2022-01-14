# Installing VScode

Install VSCode through the website in this link : 
[VS Code Download](https://code.visualstudio.com/) 

Run the installer and after it finishes installing open VS code

This should be the start screen

---

![Image](/report1Images/1.PNG)

---
# Remotely Connecting

Get your course specific account through this website
[Course account](https://sdacs.ucsd.edu/~icc/index.php)

It should be in the format cs15lwi22zz with the "zz" being different

I installed OpenSSH through the website in this link : 
[OpenSSH download](https://code.visualstudio.com/) 

Open VSC and type ssh cs15lwi22zz@ieng6.ucsd.edu in the terminal (replacing zz with your account)

A prompt will appear, type "yes" and a password prompt should appear next, type your password.

You should get this screen after logging in

---

![Image](/report1Images/2.PNG)

---

# Trying Some Commands

---

Now you can try some commands like

* cd (change directory)
* ls (list files in current directory)
* mkdir (make a folder)
* cat (concatenate)
* cp (copy)
* rm (remove)

For example in this picture I deleted a id_rsa.pub because I copied it to the wrong directory

---

![Image](/report1Images/3.PNG)

---

# Moving Files with scp
To move files from your local device to the server, you can use scp

For example "scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/" will copy a file WhereAmI.java to the home directory of the server

Make sure you run this command terminal from the directory where you made this file, alternatively you can do "scp directory cs15lwi22zz@ieng6.ucsd.edu:~/" where directory is the full directory of WhereAmI.java, for example "C:\JUNIT_WORKSPACE"

Now when you run WhereAmI.java, it should say Linux

---

![Image](/report1Images/4.PNG)

---

# Setting an SSH Key
To login to the remote server without having to type a password, you can use something called SSH-keygen. 

On your client type ssh-keygen. This should give you a directory prompt and then a password prompt (you can leave empty for no password)

Then it will give you a directory for the identification and public key as well as show the key's randomart image.

Login to the remote server and run the command mkdir .ssh, then logout

Back in the client type scp directory:~/.ssh/authorized_keys
where directory is the directory of your public key

For example "C:\Users\William\.ssh\id_rsa.pub"

Now when logging in to the remote server with "ssh cs15lwi22zz@ieng6.ucsd.edu" you should not be prompted for a password (if you left the password empty) or have a easier password to login with.

As you can see this picture I logged in with just my passphrase I set up when making the ssh key

---

![Image](/report1Images/5.PNG)

---

# Optimizing Remote Running

You can add a command at the end of "ssh cs15lwi22zz@ieng6.ucsd.edu" to login and run a command at the same time.

For example "ssh cs15lwi22zz@ieng6.ucsd.edu ls"

You can run multiple commands on the same line by using semicolons

 "cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI"

 You can use arrow keys to use the previous commands you used

---
 ![Image](/report1Images/6.PNG)