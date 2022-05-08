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

Now that my ieng6 is linked to Github, I can make some git commands work through ieng6! For example, I can do the normal `git commit` and `git push` for a file from Lab Report 1 (which was copied over to my ieng6) to Github.

![ieng6_git](screenshots\ieng6_git.png)

We can see here from Github that these pushes were received! 

![github_received](screenshots\github_received_ieng6.png)

This is the corresponding link to that push on [Github](https://github.com/ima-quack/cse15l-lab-reports/commit/14e9c788d7ebf163de358e296e5e62899a87e843).

# Copy whole directories with scp -r 

Now with quick and easy ieng6 access along with Github being available from my ieng6 account, I can do things such as copying over an entire repository from Github to my ieng6!

![scp_repo](screenshots\scp_alias.png)

From here, I can check my ieng6 account and try running and compiling the tests from ieng6 rather than my client computer.

![ieng6_test](screenshots\ieng6_test.png)

However, that was still quite a lot of steps. So, instead I could do everything from one command line prompt where I copy over a whole repository and run the commands to compile and run the tests from ieng6!

The command is slightly long due to the current ieng6 server running an older version of Java, but the command to run everything is as follows: 

```scp -r . cslab:~/markdown-parser ; ssh cslab "cd markdown-parser ; /software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java ; /software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar:. org.junit.runner.JUnitCore MarkdownParseTest"```

![all_in_one](screenshots\allinone1.png)
![all_in_one_2](screenshots\allinone2.png)