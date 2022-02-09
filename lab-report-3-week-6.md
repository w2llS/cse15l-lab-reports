# Streamlining ssh Configuration

Firstly, I navigated to my .ssh folder

```
C:\Users\William\.ssh
```

Then I made a new file called config.txt and edited it in notepad

![Image](/report3Images/1.PNG)

I changed the host to my name and the username to mine as well

Then I removed the .txt extension of config

![Image](/report3Images/2.PNG)

---

Now I can login simply by typing the command

```
ssh william
```
in the terminal

![Image](/report3Images/3.PNG)

---



I can also copy files over with scp easier with this command

```
scp WhereAmI.java william:~/
```

![Image](/report3Images/4.PNG)