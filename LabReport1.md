# Lab Report 1
## Tutorial for incoming 15L students about how to log into a course specific account on ieng6  

There are three steps  

* **Installing VScode**
*  **Remotely Connecting**
*  **Trying Some Commands**

I will go down the list

---

# Installing VScode

If you are on a lab computer VScode should already be installed, but if you are using a personal computer without it
you must download the application

Luckily, it is straightforward

Step 1: Go to Visual Studio Code Website [https://code.visualstudio.com/](https://code.visualstudio.com/)

Step 2: Download whatcha need for your OS

---

After it is installed, open the application, it should look something like

![image](https://user-images.githubusercontent.com/130080241/230442780-0cefbdcb-b17c-4f5d-bfff-c522212902c5.png)

---

# Remotely Connecting

The point of this section is to connect to a remote computer by way of the Internet

First, make sure to download git for Windows if you are on Windows and do not have it installed

---

[git for Windows](https://gitforwindows.org/)

![image](https://user-images.githubusercontent.com/130080241/230443663-d46e105a-a958-42d5-8f5d-e96547fc7b4f.png)

---

Once installed, use the git bash terminal in VScode

Set Bash terminal as default in VScode following these [instructions](https://stackoverflow.com/a/50527994)

Open a terminal in VScode using the shortcut ```` Ctrl or Command + ` ```` , type in the command `#ssh cs15lsp23zz@ieng6.ucsd.edu` , replacing `zz` with the two letters in your username

Since this is the first time sshing into the server, you should get a message like this

```
ssh cs15lsp23zz@ieng6.ucsd.edu
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 

```
Just have some faith, type 'yes', press enter

Then, the terminal will prompt you for a password. You cannot see the password as you enter it in, so maybe copy and paste it in. The final interaction should look something like this after inputting the correct password for your account: 

```
# On your client
⤇ ssh cs15lsp23zz@ieng6.ucsd.edu
The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
Password: 
Hello cs15lsp23zz, you are currently logged into ieng6-202.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   11:05:01   9  0.08,  0.09,  0.12
ieng6-202   11:05:01   5  0.02,  0.15,  0.15
ieng6-203   11:05:02   6  0.05,  0.14,  0.21

 
Fri Apr 07, 2023 11:08am - Prepping cs15lsp23

```

At this point, you have succesfully remotely connected to the server!!! :joy:

---

# Trying Some Commands










