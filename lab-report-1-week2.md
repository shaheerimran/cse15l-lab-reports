# Remote Connection
By M. Shaheer Imran

Hello and welcome to CSE 15L, a course meant to teach you important tools developers in the real world use to make amazing software. This article covers how to to connect remotely to servers at UCSD from your personal computer at home alongside setting up a development environment with Visual Studio Code. 

## Installing Visual Studio Code
Visual Studio Code is a very popular text editor which includes a lot of neat features which makes software development quite convenient. Go to this [link](https://code.visualstudio.com/) and you should see a download page like this. 

![Screenshot#1](LabReport1Screenshots/Screenshot%231.png)

Download the appropriate version for your operating system and just follow the instructions shown to set get it up and running. 

## Remotely Connecting
Since you haven't selected a working directory yet when you open Visual Studio for the first time you won't see any files or text editing windows. That's ok. What we're focusing on right now is connecting to servers at UCSD. While you can connect to servers at UCSD using your student account which you use for emails, MyTritonLink, etc., in this course we want to use a course specific account. To find out your course specific account for CSE 15L, go to this [link](https://sdacs.ucsd.edu/~icc/index.php) here. Enter your main UCSD username and your student ID. You should see something like this: 
![Screenshot #2](LabReport1Screenshots/Screenshot%232.png)

As you can see, there's a grey box containing your CSE 15L username. All CSE 15L usernames for the Spring quarter of 2021-2022 start out with "cse15lsp" and what comes after that are characters unique to each account (I blocked mine in the screenshot). We plan on using this account to remotely connect and since it's your first time remotely connecting with this account we need to set/reset the password. To do so, go to the [Global Password Change Request](https://sdacs.ucsd.edu/~icc/password.php) page and enter in YOUR COURSE SPECIFIC account and then your school student ID. Then follow the instructions to change your password (note: when confirming your password change, press the enter key instead of "check password"). 

Ok, now that all that account business is took care of, lets go back to VSCode. On the top left under "Terminal", select the option for "New Terminal" and a new Terminal window should appear in VSCode kind of like this:

![Screenshot#4](LabReport1Screenshots/Screenshot%234.png)

In the new Terminal window, type the command `ssh cs15lsp22---@ieng6.ucsd.edu` and replace the `---` with your specific course account's characters. Since it's your first time logging in with this account a bunch of text might show up with a form at the end asking for you to type yes/no, don't worry about it and enter yes for now (you can learn about it later on as the course continues and your knowledge of computer science increases). After that you should be prompted to enter your password and if you do that, you should hopefully see some text talking about your last login, cpu usage, cluster status, etc. Congrats you've officially connected to the UCSD servers in the CSE basement.

## Trying Some Commands
The servers in the UCSD basement run on a Unix-based OS so general Unix commands should work on them. If you have no idea what I'm talking about, just think about an OS (or operating system) as the system for how a computer works and runs programs and Unix is a very famous type of this system. Unix commands are things you can type in the terminal of a Unix computer that do different things. For example, the command `ls` lists out all the files in the current folder your in. Type it out and see what you get. Here are some other commands you can try out (just some from the many you can find more about online):

    - `cd [Insert folder]` to move to a new folder
    - `mkdir [Insert folder name]` to make a new directory (folder)
    - `cp [INSERT FILE TO BE COPIED] [INSERT COPY NAME/DIRECTORY]` to copy a file 
    - `rm [INSERT FILE NAME]` to remove a file

![Screenshot #5](LabReport1Screenshots/Screenshot%235.png)

## Moving files with scp

Using scp, we can transfer files from our own computer to a remote server. To do so enter the command below on your own computer: 

`scp [INSERT FILE] [INSERT ACCOUNT]@ieng6.ucsd.edu:~/`

You should then be prompted to enter your password. Enter it and use `ls`, you should then hopefully see your file in the root directory.

![Screenshot #6](LabReport1Screenshots/Screenshot%236.png)

## Setting up an SSH Key
Even though it might not seem very time consuming at first, it would be a lot
easier if we could just SSH to the server without a password if we're logging
in from the same device as we normally do. Fortunately there's a solution in 
the form of SSH keys. Basically, you generate a public and a private "key" on 
your computer and scp the public key to the server. Then, when you want to login,
the public key and private key work together and you can login to the server
without having to enter in your password.