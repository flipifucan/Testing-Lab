## Solution Guide: Alert - C2 Beacon

The goals of this activity were to practice investigating a C2 beacon acknowledgement attack, and to and reinforce concepts related to Snort IDS, Security Onion, and network security monitoring.

### Solutions

Open Security Onion and look for `C2` and `Drilldown` to see the details. Filter the results for the source IP `192.168.3.35`

1. What rule triggered this alert?

    - `alert http $HOME_NET any -> $EXTERNAL_NET any`
    
2. According to the rule, what is the destination port?

     - `80`

3. Taking a closer look at the event fields, what is the rule category?

    - `Malware Command and Control Activity Detected`


4. What is the event module that triggered the alert?

    - `Suricata`

 (Use this link to answer the following questions: [A Look At The New Gameover Zeus Variant](https://www.zscaler.com/blogs/security-research/look-new-gameover-zeus-variant).)  

5. What type of threat is this?

    -  Botnet

6. Did this threat modify Windows registry keys?

    - Yes

7. Why does this threat modify Windows registry keys?

    - Ensure persistence upon system reboot.

9. What does C2 stand for and what is it?

    - Command and Control or CnC, a server that's used to establish and maintain communications with compromised systems on targeted networks. Attackers use C2 servers for sending commands to botnets.

9. What term is used to describe a computer that's under the control of a C2 server?

    - Zombie 

10. What is a sign that a computer may be under the control of a C2 server?

    - Slow internet speeds or slow computer

#### Bonus Questions

11. Name one of the most popular techniques an adversary uses to infect a host with a botnet.

    - Email phishing

12. What are two ways an organization can mitigate this type of a threat?

    - Blacklist the CnC server's IP address or install an intrusion prevention system (IPS) using a Snort rule that blocks these types of threat signatures.

13. How far up the cyber kill chain did this attack go?

    - All the way to Action on Objections

14. What process does this threat use to hide when it's discovered?

    - It deletes itself.

15. Why is this threat considered persistent?

    - Because it survives across system reboots

16. What tactic does this threat use to remain hidden and unnoticed?

    - It runs as a hidden background process and not inside of an open window on the user's screen.

17. Create a `new case` based off of your findings by clicking on the alert.

    - Add the title `Zbot Malware Discovery` 

    - Scroll down and click `ADD` to include this event as an `Observable`

---

© 2024 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.
