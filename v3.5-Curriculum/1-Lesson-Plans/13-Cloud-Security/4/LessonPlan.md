## 13.4 Lesson Plan: Testing Redundant Systems

### Class Overview

If there are cloud security topics that you didn't have time to cover in previous days, you can use time today to catch up.

In today's class, we'll complete the module by implementing redundant systems.

### Class Objectives

By the end of today's class, students should be able to:

- Verify redundancy by turning off one or more virtual machines used in the infrastructure.

### Instructor Notes

- Use today as a catch-up and review day for students. The majority of programs that have run this module have reported needing four days to get through the activities for this week.

- All activities after the break are optional. We recommend assigning them to advanced students while ensuring that other students completed all activities up through today's `03. Student Do: Redundancy Testing`.

- Please announce and explain the Challenge assignment before dismissing class.

- Please make sure that you are using your personal Azure account for the lab demonstrations and activities.

- Remind students that they need to shut off their labs.

### Lab Environment 

<details><summary>Lab Details</summary>
<br>

For demonstrations, activities, and reviews, you will use your free Azure account.

- [Azure Setup Guide](https://docs.google.com/document/d/1gs_09b7eotl7hzTL82xlqPt-OwOd0aWA78qcQxtMr6Y/edit)

- [Azure Free Tier FAQs](https://azure.microsoft.com/en-us/free/free-account-faq/)

### Lab References

- [Ansible](https://ansible.com)
- [Docker](https://docker.com)
- [YAML](https://yaml.org/spec/1.2/spec.html#Introduction)

</details>

### Slideshow

The slides for today can be viewed on Google Drive here: [13.4 Slides](https://docs.google.com/presentation/d/1i-wxjzPV3E0HwAgwBYQG5Hmcu2LQwHxdK0f4egJ3Blw/edit).

- To add slides to the student-facing repository, download the slides as a PDF by navigating to File > "Download as" and choose "PDF document." Then, add the PDF file to your class repository along with other necessary files.

- **Note:** Editing access is not available for these documents. If you or your students wish to modify the slides, please create a copy by navigating to File > "Make a copy...".

### Time Tracker

The time tracker for today's lesson can be viewed on Google Drive here: [13.4 Time Tracker](https://docs.google.com/spreadsheets/d/1D-rEaPZXDy-9Ly9LHGakfGXP0gJdBRHAiSXFw8u7Udo/edit#gid=742113232).

### Student Guide

Distribute the student-facing version of the lesson plan: [13.4 Student Guide](StudentGuide.md).

---

### 01. Instructor Do: Welcome and Overview (0:05)

Welcome students to the last day of the cloud security module.

Note what they have accomplished so far:

- Created a virtual network.

- Protected the network with a firewall and completed several firewall rules.

- Deployed a jump box to the network.

- Deployed two identical VMs to the network.

- Used Docker containers to run a website and Ansible.

- Used Ansible to configure their VMs with code (infrastructure as code).

- Configured a load balancer to distribute traffic among the VMs.

---
|:warning: **CHECKPOINT** :warning:|
|:-:|
| Using the [Daily Checklist](../Resources/Checklist.md), verify that students have completed all Day 3 critical tasks and are ready to continue to today's activities. |

---

### 02. Instructor Do: Redundancy Testing (0:10)

In this section, you will briefly show students how to test a redundant system.

- Begin by opening your Azure portal and navigating to VMs.

- Click on a VM to see its details. Point out the **Stop** button.

    ![](Images/vm-details.png)

- Explain that with your current setup, you can simulate one of the VMs going offline by stopping it.

In the next activity, students will stop one VM and check whether or not they still have access to the site.

Ask if there are any questions about stopping the machines.

### 03. Student Do: Redundancy Testing (0:25)

Explain the following to students:

- Over the last few days, you configured a vulnerable web application server for XCorp's Red Team to train new hires and use for general testing.

- In this activity, you will finalize this setup by putting a third VM behind your load balancer and testing for redundancy.

- You are tasked with adding your latest VM to the backend pool for your load balancer and testing whether the website continues working if one of your VMs has a problem.

:globe_with_meridians: This activity will use **breakout rooms**. Assign students into groups of 3–5 and move them into breakout rooms.

Send students the following file:

- [Activity File: Redundancy Testing](Activities/03_Redundancy_Testing/Unsolved/README.md)

### 04. Instructor Review: Redundancy Testing Activity (0:15)

:bar_chart: Run a comprehension check poll before reviewing the activity. 

Point out that the goal of this activity was to verify that students' VMs have a working, high availability setup. If one VM has an issue, the site stays active.

Use the following file to guide your walkthrough:

- [Solution Guide: Redundancy Testing](Activities/03_Redundancy_Testing/Solved/README.md)

---

### 05. Break (0:15)

---

### 06. Instructor Do: Alternate Hostname Activity Demonstration (**OPTIONAL**)

**NOTE:** This activity can be skipped if you run out of time. It can also be given to the more advanced students if they would like to go further.

Explain that DVWA has a vulnerability that will allow us to see the "hostname" of the machine. For Docker, the hostname will be the docker container identifier.

Using this vulnerability, we can see what machine we are connected to, and when one machine goes offline, we should be able to see the hostname change.

Point out that you will walk them through setting up DVWA and using this exploit.

Navigate to your DVWA setup with `http://[load-balancer-ip]/setup.php.

![](Images/dvwa/Reset.png)

Scroll to the bottom of the page and click on `Create/Reset Database`.

You should see the following information:

![](Images/dvwa/info.png)

Click on `Login` to get the login screen.

Login with the credentials `admin:password`.

![](Images/dvwa/Login.png)

Once logged in, click on `Command Injection`.

Explain that command injection is a vulnerability where we have an opportunity to send command line commands directly to the server and have their output be displayed on the screen.

Explain that we will go over command injection again later in the course, but here we will have a quick introduction.

Point out the box that says "Ping an IP address" and explain that this function is essentially taking your input, running it with the `ping` command on the command line, and then returning the output.

Enter `8.8.8.8` in the box and point out that this is a well known google DNS server.

Remind the students that our security group is blocking traffic so we should get an error here:

![](Images/dvwa/ping.png)

Explain that using the ping function is not what we want to do. Instead, ask the students if they remember how to chain commands together from the Linux weeks.

Take a few answers.

Point out that **if** we use one of our command chaining techniques, we should be able to get a **second** command to run **after** the ping command runs.

Quickly remind students of the following:

- `;` runs a command after the first command, regardless if the first command is successful.

- `&&` runs a command **only** if the first command is successful.

- `||` runs a command **only** if the first command fails.

We can use any of these to **inject** a second command to run after the ping command runs.

Enter `8.8.8.8 ; whoami`

Break down the syntax:

- `8.8.8.8` goes to the ping command to complete `ping 8.8.8.8` in the background.
- `;` says to run another command.
- `whoami` is the second **injected** command.

![](Images/dvwa/whoami.png)

Point out that we can see our second command output `www-data` at the bottom.

Point out further that we can use the `||` command to clean up the output.

Enter `|| whoami`.

Break down the syntax:

- `||` says that if the first command fails, run the next command. Point out that we are not giving the `ping` command **any** IP address to ping, so it **will** fail. This way we will only see the second command's output.
- `whoami` is our second **injected** command.

![](Images/dvwa/or.png)

Explain that in the next activity, students will use this exploit to see the hostname of the machine they are connected to. This will further illustrate what happens when one host goes down because they can clearly see what host they are connected to.

### 07. Student Do: Alternate Hostname Testing Activity

Explain the following to the students:

- The XCorp Red Team has been using the new DVWA setup to train new hires and use for general testing.

- You have been asked to test the load balancer once more to make sure traffic is being distributed among all three of your VMs.

- In this activity, you will exploit a vulnerability in DVWA to determine what machine you are connected to.

- You are tasked with collecting the hostnames for each DVWA container and then verifying that the load balancer is sending traffic to different containers as needed.

:globe_with_meridians: Students should stay in the same **breakout room** groups as the previous activity.

Send students the following file:

- [Activity File: Hostname Exploit Testing](Activities/08_Hostname_Vuln/Unsolved/README.md)

### 08. Instructor Review: Alternate Hostname Testing Activity Walkthrough

:bar_chart: Run a comprehension check poll before reviewing the activity. 

Point out that the goal of this activity was to get further insight into which machine they are connected to using a vulnerability in DVWA.

USe the following file to guide your walkthrough:

- [Solution Guide: Hostname Exploit Testing Solutions](Activities/08_Hostname_Vuln/Solved/README.md)

### 09. Instructor Do: Announce Cloud Security Challenge (0:10)

Explain to the class that we have concluded the cloud security class material. In the next module, for the first project, students will continue to work in their personal Azure accounts to develop and secure their personal web applications!

Introduce the assignment by explaining the following:

- During the last week, you created a highly available web server for XCorp's Red Team to use for testing and training.

- Your lead cloud administrator has asked for a diagram of the network you created to keep for documentation and company records.

- Your task: Use [app.diagrams.net](https://app.diagrams.net/) to create a detailed diagram of your cloud infrastructure.

---

© 2023 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.
