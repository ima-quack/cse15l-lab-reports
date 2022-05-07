# Week 6: Lab Report 3

Welcome to my third lab report! This lab will be going over further optimization of ieng6 and github usage.

Just some reminders: 
- My name is Nhan Quach
- My group leader is Elias
- My team members are as follows:


| Member 1 | Member 2 | Member 3 | Member 4 | Member 5 | Member 6 |
| -------- | -------- | -------- | -------- | -------- | -------- |
| Nhan     | Tyler    | Kayla    | Diego    | Jas      | Snehal   |


---

# Streamlining ssh Configuration
![config](screenshots\ssh_config.png)
This is the `.ssh/config` file which I have utilized and created with VSCode to quickly access my ieng6 account.

You can see the different parts of the config file which makes the magic happen, but I want to elaborate on three parts in more detail.

* **Host**: This is the alias which can be used to quickly assess the remote client.
* **HostName**: This is the remote server or access point.
* **User**: This is our individual, identifying user name for the server.

I can change the alias to be something different _using VSCode_ and the changes should reflect near instantenously when I try to access the ieng6. 

![config_change](screenshots\ssh_config_edit.png)

Now that the alias/host has changed, I will try to access ieng6 using that alias.

![ssh_access](screenshots\ssh_edited_alias.png)

Not only does this make logging into ieng6 more useful, it makes commands such as **copying** with `scp` something over from my client computer over to the server more practical.

![scp](screenshots\scp_single_file.png)

This copy command would have been much more complicated had I needed to remember my full ieng6 login, but now it's simple and easy!

# Setup Github Access from ieng6

Access to Github itself from ieng6 can be possible and makes terminal editing and adjustments from ieng6 to Github practical!

The set up begins with generating a public/private key pair using the `ssh-keygen` command, except now within the ieng6 terminal rather than the client. 

![ieng6_ssh](screenshots\ieng6_private_keys.png)

This should generate a `.ssh` directory within ieng6 as seen above.

From there, I copied over my public key contents utilizing the `cat id_rsa.pub` command within the UNIX terminal to print out the contents and then copied them over to [Github](https://github.com/).

![github_keys](screenshots\github_keys.png)

The private key is within the same location as the public key which I have already provided a screenshot for, but just in case here it is again.

![ieng6_ssh](screenshots\ieng6_private_keys.png)

Show running git commands to commit and push a change to GitHub while logged into ieng6 account.

Show link for the resulting commit.

# Copy whole directories with scp -r 

Show copying whole markdown-parse directory to ieng6 account

Show logging into ieng6 account after doing this and compiling and runnign the tests for repository

Show combining scp, ;, and ssh to copy the whole directory and run the tests in one line. 
