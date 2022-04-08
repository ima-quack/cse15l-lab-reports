# **Week 2 Lab Report**

This is a lab report written up by Nhan Quach part of the Axolytyl Group led by Elias.

Axolytyl Group Members
| Nhan | Tyler | Kayla | Diego | Jas | Snehal 
| --- | --- | --- | --- | --- | --- |
---
## Installing VSCode
![Visual Studio Code](https://code.visualstudio.com/assets/home/home-screenshot-mac.png)

To get started with setting up for the class and other programming work:
* Head to [Visual Studio Code](https://code.visualstudio.com/Download)!
    * Download the version of VSCode appropriate for your computer (e.g. Windows, Mac, Linux)
* Download any other languages which you would want to code with.
    * For example: :snake: [Python](https://www.python.org/downloads/) or :coffee: [Java](https://www.oracle.com/java/technologies/downloads/) 
---

## Remotely Connecting
![Password](PasswordChange.png)

Odds are, you are a UCSD student if you are looking for this tutorial! 
One of the kinks which UCSD currently has is that lab login accounts for the Computer Science basement is a bit wonky, so you will need to change your password.
* Head to UCSD's [Educational Technology Services Account Lookup](https://sdacs.ucsd.edu/~icc/index.php) to get started with the process.
* Once you get into the **Account Lookup Results**, you'll see a section for *Additional Accountss* and a button which should say something along the lines of `cs15l<quarter><asc>`. 
    * This is your unique "computer" or sign-in for CS15L.
    * Press on that button.
* Click on `change your password` and go ahead and change your password.
    * Note this may take some time (up to 15 minutes).
    * This will also change your password for ***all*** your related UCSD-based accounts.

## Actually Connecting

Once you get through that far, you can actually start to remotely connect to the server!
![Connect](Remote.png)
* Open up your command terminal
    * You can either do this through your computer itself, or through Visual Studio Code 
* Type in `ssh cs15l\<quarter>\<asd>`
* Type in your password.
    * You'll notice that you won't be able to see anything actually get typed up!
    * Don't worry about that, this is just another level of security.
* This is what you should see once you get in:
![Remote](RemoteConnect.png)

---
## Trying Some Commands
![Commands](Commands.png)
---
Now that you're on the Remote Client and in the terminal, you can try out some commands!
* cd \<directory name>: Enables you to move through directories.
* ls: Prints out the contents of the directory
* pwd: Prints out the contents of the directory

You can find more commands on what to do with the Command Prompt and Remote Client through [Googling](https://www.thomas-krenn.com/en/wiki/Cmd_commands_under_Windows)!

---
## Moving Files with `scp`
![Copy](Copy.png)
One powerful command available to you when you have access to a remote computer is to copy one file from you local client -- the computer you are actively using -- and the remote!
* Within your terminal type in the command `scp` while also specifying the file and location of where you can to copy something over to.
    * For example, `scp <file> cs15l<quarter><asd>@ieng6.ucsd.edu`
* You'll need to type in your password for the file to copy over, but in the next step we'll be able to get around that!

---
## Setting an SSH Key

---
## Optimizing Remote Running




[Lab Report 1](lab-report-1-week-2.html)
[Lab Report 1](https://ima-quack.github.io/cse15l-lab-reports/lab-report-1-week2.html)
