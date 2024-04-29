# Module 6 Challenge

## Module 6 Challenge <assignment>

### Advanced Bash: Owning the System

Congratulations! You've made it to the end of the Linux module.

Over the past few weeks, you've played the role of a systems administrator responsible for diagnosing, securing, and automating the hardening of a compromised Linux host. In doing so, you've explored all of the following and more:

- The structure of the Linux file system.
- Processes and how to inspect them.
- How to create users and groups and editing their permissions.
- How to schedule regular jobs with `cron`.
- How to log, monitor, and log analysis.
- How to automate common tasks with bash scripts, compound commands, and other advanced features of the shell.

Getting this far is a real accomplishment. This is a huge amount of information, all of which is used by professional systems administrators almost every day.

### Scenario

For this week's Challenge, you will play the role of a criminal hacker. You will remotely access a victim's target machine, maintain access using a backdoor, and crack sensitive passwords in the `/etc` directory.

You will learn a lot of new concepts in this assignment, and you may need to do a bit of research. This Challenge should be a fun, engaging, and hands-on introduction to maintaining access to a compromised system. (You will learn about this in more depth during the pen testing modules. For now, read the following Privilege Escalation to better understand the setup and goal of this assignment.)

> **Note:** This activity is based on the "offense informs defense" philosophy. You will take on the role of a criminal hacker in order to better understand how exploits are carried out. Remember: To protect from attacks, you'll need to practice thinking like an attacker.

#### Privilege Escalation

When an attacker gains access to a machine, their first objective is always to escalate privileges to `root` (which you accomplished during your scavenger hunt activity). When they achieve `root` privileges, they can do anything they want to the system. Cybersecurity professionals describe the process of gaining access to a host and escalating to `root` privileges as **owning the system**.

While owning a system is a crucial piece of the process, it is only the first item on an experienced attacker's agenda. Two goals remain on the checklist: **maintaining access** and **exfiltrating data**.

After exploiting a machine, attackers must ensure that they will be able to reconnect later with the same escalated privileges they gained during the first assault. This is typically achieved by installing a backdoor. A **backdoor** is any mechanism that allows an attacker to secretly reconnect to a machine they've exploited.

### Lab Environment

- You will be completing this activity from your web lab, which represents the `attacker machine`.   
- You will be running a script to enable the `target machine`.
  - To start up the target machine, run the following command from anywhere inside your web lab:
    - `sudo /home/sysadmin/Documents/scavenger-hunt/target-machine-start.sh`
  

#### Access Setup 

Complete the following steps:

1. Open up a new tab on your web lab.

2. Begin an SSH session into the target machine by doing the following:

   - Open a terminal on the attacker machine and run `ssh sysadmin@192.168.6.105 -p 22`.

    This command will attempt to start an SSH session on your target machine.

    - Enter the password `passw0rd` when prompted.

3. After you've successfully logged into the `sysadmin` account on the target machine, you'll notice your prompt changes to `sysadmin:~\ $`.

    - Swap to the `root` user by entering `sudo -s` and reentering the password `passw0rd`.

You should now have the `root` prompt `root:~\ $` that you acquired during your scavenger hunt activity.

---

### Instructions

Your goal for this assignment is to maintain access to the target machine by installing a backdoor. You will then use the backdoor to crack sensitive passwords.

Complete this assignment by following the steps outlined below. Again, some of these steps will require you to research new tools and concepts. Any information you might need can be found using man pages and online searches. Remember: learning new tools on the job is a key skill for IT and security roles.

As you complete each step, make sure to take notes as you will use it to answer the questions in this quiz. 

IMPORTANT: Please review your answers carefully before submitting to ensure that they are free of spelling and spacing errors. Incorrect spelling or incorrect spacing syntax will be marked as incorrect answers.

> **Note** You can view the questions in this Challenge Quiz directly through your BCS course. 

#### Step 1: Shadow People

In this step, you'll create a "secret" user named `sysd`. Anyone examining `/etc/passwd` will assume that this is a service account, but in fact, you'll be using it to reconnect to the target machine for further exploitation.  

1. Create a `sysd` user.

2. Give your user a password (make sure you remember it).

3. Give your user a system UID (any UID below 1000).
4. Give your user a GID equal to this UID.
5. Give your user full `sudo` access without a password. 
  
    - Minimize exposure by ensuring that your secret user does not have a home folder.

6. Test that your `sysd` user can execute commands with `sudo` access without a password before moving on.

    - Try running `sudo -l` to test. If the terminal does not prompt you for a password, it was a success. Attempt any other commands that require elevated privileges and mark them in your Submission File.

    > **Note:** If a hacker can rapidly execute commands on a machine with elevated privileges, they can more quickly exfiltrate important data from the target machine.

#### Step 2: Smooth Sailing

In this step, you'll allow SSH access via port `2222`. SSH usually runs on port `22`, but opening port `2222` will allow you to log in as your secret `sysd` user without connecting to the standard (and well-guarded) port `22`.

1. Use Nano to update the `/etc/ssh/sshd_config` configuration file to allow SSH access via port `2222`:

    - When you open the configuration file, add a secondary SSH port line under port `22`.

    - This will require some research. Start by examining `/etc/ssh/sshd_config` and using online searches or man pages to learn more about the available configuration options.

#### Step 3: Testing Your Configuration Update

When you think you've configured things properly, test your solution by testing the new backdoor SSH port. Do the following steps on the target machine:

1. First, note that the IP address of the target machine is `192.168.6.105`. You'll need this for when you attempt to log back into the target machine.

  - Make sure to restart the SSH service.

2. Exit the `root` account and log off of the target machine (you'll know you're back in your attacker machine when the prompt turns green).

3. Use your attacking machine to test the new backdoor SSH port:

    - SSH back into the target machine as your `sysd` user, but this time change the port from `22` to `2222` using `ssh sysd@192.168.6.105 -p 2222`.

4.  Once you are connected to the target machine over SSH, use `sudo su` to switch back to the `root` user.

> **Note:** This is an important step. You were able to log out of your `root` account and then reestablish a remote session with escalated privileges through a different, un-guarded port.
>
>  - Company servers that house sensitive information will often use monitoring and hardening tools to closely watch key ports, such as `22` for SSH.
>  - It is also quite difficult for hackers, on their first breached connection, to know the locations of the most sensitive files in a system.
>      - For this reason, hackers must both attempt to mask their activity (as you are doing with your `sysd` user), and also ensure that they can discreetly revisit a system. This allows them to maximize the amount of data they can take from the target machine.

#### Step 4: Crack All the Passwords

Next, to strengthen our control of this system, we will attempt to crack as many passwords as we can.

Having access to all the accounts will also allow us to access the system if our other backdoors are closed.

1. Make sure that you have SSH-ed into the target machine using your `sysd` account.

2. Escalate your privileges to the `root` user. 
  
3. Use John to crack the entire `/etc/shadow` file.

    - You will not need to transfer the file, as John is already installed on the scavenger hunt VM.

> **Note:** Cracking passwords is a process that takes time. Now might be a good opportunity to take a break and let the computer do the work for you.



