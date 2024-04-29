# Introduction to Module 5


### Archiving and Logging Data

In this module, we will continue to learn system administration fundamentals by working in Linux environments to back up and recover data, preserving integrity and availability. 

- We will use the `tar` command to create, list, and extract data from archives. Creating archives ensures the availability of users’ data and configuration files.
 
- We will use the `cron` utility to automate computing tasks and schedule regular, automatic execution of important maintenance and security operations.
 
- We will learn about Linux log management by performing log file management tasks and tracing a series of historical events to determine whether a breach has occurred. We will then audit logs that provide critical insight into an attacker’s tactics, techniques, and procedures.
 
- We will learn how to investigate suspicious network activity to manage log sizes and enable, troubleshoot, monitor, and audit logs using `journalctl`, `logrotate`, and `auditd`.


### What to Be Aware Of

- When editing crontabs in Day 2, you may not be able to save the settings properly. This is because the file defaults to DOS mode when saved. This issue typically only occurs on Windows machines. To make sure the file does not save in DOS mode, press Alt+M when saving a file in Nano. 

### Security+ Domains

This module covers portions of the following domains on the Security+ exam:

- 3.0 Security Architecture
- 4.0 Security Operations
- 5.0 Security Program Management and Oversight


For more information about these Security+ domains, refer to the following resource: 
  - [Security+ Exam Objectives](https://assets.ctfassets.net/82ripq7fjls2/6TYWUym0Nudqa8nGEnegjG/0f9b974d3b1837fe85ab8e6553f4d623/CompTIA-Security-Plus-SY0-701-Exam-Objectives.pdf)

### This Week’s Lab Environment

In this module, you'll continue using the web lab that we used in the previous module. 

### Preview This Week’s Challenge

For this week's Challenge assignment, you will play the role of a security analyst at a financial institution. The bank has developed a log management system, but in this Challenge, you will expand and enhance the bank's log management system by learning new tools, adding advanced features, and researching additional concepts.

### Looking Forward

In Module 6, we'll expand on the skills that you've learned so far and cover Bash scripting and programming. You will work through a series of exercises where you'll create custom commands and Bash scripts to collect evidence, perform system audits, reconfigure a Linux installation, and take the necessary steps to harden Linux systems.

- Make sure to pull the latest builds before starting the Module 6 Challenge assignment. 

### Further Reading and Resources

- :books: [The Linux Command Line, 2nd Edition ](http://linuxcommand.org/tlcl.php) by William Shotts, pages 230&ndash;235.

- :books: Linux Essentials Manual, The LPI Introductory Programme, pages 145&ndash;152.
  - [Downloadable PDF](https://golinski.faculty.wmi.amu.edu.pl/sop-en/linux-esentials-manual.pdf)

**Day 1 Resources**

- [GeeksforGeeks: How to Compress and Extract Files Using the tar Command on Linux](https://www.geeksforgeeks.org/how-to-compress-and-extract-files-using-the-tar-command-on-linux/)
 
**Day 2 Resources**

- [Crontab Generator](https://crontab-generator.org)
 
**Day 3 Resources**

- [Baeldung: How to Use journalctl to Read Linux System Logs](https://www.baeldung.com/linux/journalctl-check-logs)

- [Network World: How log rotation works with logrotate](https://www.networkworld.com/article/3218728/how-log-rotation-works-with-logrotate.html)
