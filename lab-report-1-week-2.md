![screenshot](umicry.jpg)

# Lab Report 1
Description: learning how to access the UCSD lab remote desktops through SSH

---

## Installing VSCode
Installing Visual Studio Code was something that I did for a previous class but I'll just quickly run through the process that I did at that time. 

The VSCode download and installer is fairly simple. The only real difficulty came with making sure that java was installed properly. To do this all you have to do is go into the the command console and run 

$java -version

![javaver](lab1ss/javaversion_screenshot.png)

If it says `java version "##"` then java is installed properly. Java 8 or higher should be up to date enough for our purposes. If this does not appear, then you would have to install java and modify the system environment path variable.

---

## Remotely Connecting

Aside from the password pains, logging in through the ssh to the remote computer wasn't too difficult. By entering `ssh cs15lwi22amb@ieng6.ucsd.edu` (the 3 characters after wi22 varies person to person) and inputting a password we get logged in. This simply allows us to access the remote desktop through our terminal

![sshlogin](lab1ss/ssh_screenshot.png)

## Trying Some Commands

List of some commands we used and their use

- ls: lists the files and folders in the current directory
- ls -a: lists all files and folders including the hidden ones in current directory
- ls -l: gives a long description of all files and folders in the current directory
- pwd: gives the directory path of the current directory
- cd *directory*: changes the directory to the specified directory
- mkdir *new folder*: creates a new folder in the current directory with specified name
- mv *file* *folder*: moves secified file in the directory to the specified folder in the directory
- rm *file*: removes/deletes specified file

ssh commands
- ssh *remote id*: connects to the computer with the specified id
- scp *file* *remote id + directory*: copies specified file to the remote computer in specified directory

![command](lab1ss/command_screenshots.png)

## Moving files with `scp`

In order to run files on the remote computer, we must copy the file from our system to the remote system. To do this we run the command

`scp *file* cs15lwi22amb@ieng6.ucsd.edu:~/`

again the 3 characters following the wi22 will vary from person to person.

![scpexample](lab1ss/scp_screenshot.png)

By logging in through `ssh` and using the `ls` command we can indeed see that the file has been copied into the remote computer.

## Setting an SSH Key
