## 11.2 Lesson Plan: Intrusion Detection, Snort, and Network Security Monitoring

### Overview

In today's class, students will build upon their knowledge of firewalls by using an intrusion detection systems (IDS) such as Snort IDS. Students will learn how to use network security monitoring (NSM) and the Snort IDS engine to analyze indicators of attack (IOA), indicators of compromise (IOC), perform network forensics, and acquire intelligence and situational awareness of their networks providing them with the necessary information required to defend against network attacks.

### Class Objectives

By the end of today's class, students will be able to:

- Interpret and define Snort rules and alerts.

- Explain how intrusion detection systems work and how they differ from firewalls. 

- Use Security Onion and its suite of network security monitoring tools to trace the path of network attacks.

- Collect and analyze indicators of attack (IOA) and indicators of compromise (IOC) using NSM tools.

- Apply knowledge of NSM, Snort rules, and Security Onion to establish situational awareness within a network.

### Instructor Notes

- On Days 11.2 and 11.3, we will begin class by logging into Azure and launching an instance of Security Onion. This will generate PCAP (packet capture) traffic that we will use to analyze and triage alert data.

### Lab Environment

<details><summary>Lab Details</summary>
<br>

In this module, you will use the NetSec lab environment located in Windows Azure Lab Services. RDP into the **Windows RDP host machine** using the following credentials:

  - Username: `azadmin`
  - Password: `p@ssw0rdp@ssw0rd`

Open Hyper-V Manager to access the below machines:

**Security Onion machine:**
  - Username: `sysadmin`
  - Password: `cybersecurity`

**UFW machine:**
  - Username: `sysadmin`
  - Password: `cybersecurity`

**firewalld machine:**
  - Username: `sysadmin`
  - Password: `cybersecurity`

In today's class, you will use the SecOnion machine.

</details>

### Online Classroom Strategies 

Refer to the following guidelines and best practices for conducting this class online: 

- [Cybersecurity Online Classroom Strategies](../../../00-Teaching-Staff-Prework/OnlineStrategies.md)

### Module Day 2 Contents

- [x] [01. Everyone Do: Security Onion Setup](LessonPlan.md#01-everyone-do-security-onion-setup-010)
- [x] [02. Instructor Do: Welcome and Overview](LessonPlan.md#02-instructor-do-welcome-and-overview-010)
- [x] [03. Instructor Do: Introduction to Intrusion Detection Systems and Snort](LessonPlan.md#03-instructor-do-introduction-to-intrusion-detection-systems-and-snort-020)
- [x] [04. Student Do: Intrusion Detection Systems and Snort](LessonPlan.md#04-student-do-intrusion-detection-systems-and-snort-015)
- [x] [05. Instructor Review: Intro to Intrusion Detection Systems and Snort Activity](LessonPlan.md#05-instructor-review-intro-to-intrusion-detection-systems-and-snort-activity-010)
- [x] [06. Instructor Do: Network Security Monitoring and Security Onion](LessonPlan.md#06-instructor-do-network-security-monitoring-and-security-onion-020)
- [x] [07. Student Do: Security Onion and NSM](LessonPlan.md#07-student-do-security-onion-and-nsm-020)
- [x] [08. Instructor Review: Security Onion and NSM Overview Activity](LessonPlan.md#08-instructor-review-security-onion-and-nsm-overview-activity-010)
- [x] [09. Break](LessonPlan.md#09-break-015)
- [x] [10. Instructor Do: Alert - HTTP File Extraction](#10-instructor-do-alert---http-file-extraction-015)
- [x] [11. Student Do: Alert - FTP File Extraction](LessonPlan.md#11-student-do-alert---ftp-file-extraction-020)
- [x] [12. Instructor Review: Alert - FTP File Extraction](LessonPlan.md#12-instructor-review-alert---ftp-file-extraction-010)


### Lesson Slideshow 

The lesson slides are available on Google Drive here: [11.2 Slides](https://docs.google.com/presentation/d/18svqqLvbYawJSekt8RMKktsYQLPEJlDozoSIwfOTTug/edit)

- To add slides to the student-facing repository, download the slides as a PDF by navigating to File > "Download as" and choose "PDF document." Then, add the PDF file to your class repository along with other necessary files.

- **Note:** Editing access is not available for this document. If you or your students wish to modify the slides, please create a copy by navigating to File > "Make a copy..."

### Time Tracker

The time tracker is available on Google Drive here: [11.2 Time Tracker](https://docs.google.com/spreadsheets/d/1FZrOydH1-aV9-WboQLUgsSQMS6igxz5mfVwO8GM0AoA/edit#gid=1145703143)

### Student Guide

Distribute the student-facing version of the lesson plan: [11.2 Student Guide](StudentGuide.md)

---

### 01. Everyone Do: Security Onion Setup (0:10) 

Welcome students to class and let them know that today's lesson will introduce fundamental concepts and tools of network security monitoring, intrusion detection, and Snort.

Before we get started, we will need to log in to Azure and launch an instance of Security Onion. This will generate alert data that we'll use later in the class. Specifically, it will spin up an instance of Security Onion with loaded PCAPs.

- Review that PCAPs are snapshots of live traffic. In the networking modules, students loaded PCAPs into Wireshark. 

- Explain that, Security Onion will use the command `sudo so-test` to replay multiple PCAPS stored in the `/opt/so/samples` directory, which stores hundreds of PCAPs. 

- It's essential that network defenders know how to replay network traffic using PCAPS in order to analyze and triage alert data.

Send students the following file: 

- [Everyone Do: Security Onion Overview](Activities/01_Security_Onion_Setup/README.md)

Lead the class in the following demonstration.

1. We will all verify that our NSM tools are working before starting the labs. Select the **SecOnion VM** and right-click to **Connect**. This will launch you into the terminal of the **SecOnion VM**. From here, you will need to log into it with the **sysadmin** account.  Once logged into the terminal, type the following command:
   
    - `./sudo so-ipchange.sh`

       - Answer `Y` if it prompts you for a response. Otherwise, continue to the next step.

    - `sudo so-status`
      
       - `so-status`: Checks the status of currently installed NSM tools.
   
    - Output should look similar to below:
   
       ![NSM Status](Images/SO%20Status.png)
   
      - Ensure all statuses are listed as `running`.

      - If not, let the `so-status` command run for a few minutes. It can be slow.
   
    - If any of the statuses are not listed as `running` after a few minutes, restart the NSM tools with the following command:

       - `sudo reboot`
   
    - Run the `so-status` command again for a few minutes. All systems should be listed as `OK` after a few minutes.

    - Determine the IP address being used for Security Onion by entering `sudo ip a s eth0`
  
      - `ip a s eth0`: This command returns the IP address of the specified interface.
        
        - The `a` stands for `a`ddress and brings back the IPv4 or IPv6 address.

        - The `s` returns `s`tatistics on the interface made up of packets transferred and received.

    ![Security Onion IP Address](Images/SO%20IP%20Address.png)

    - **Note:** Your IP address may be different than the one depicted above.

2. Next, we need to log into the Security Onion Console (SOC) to generate alerts.

   - Connect to the SOC by opening up your web browser and typing in the IP address for the Security Onion VM

      - The example above would use https://172.17.90.99

   - Log into the Security Onion Console and click on the Grid Icon to the left.

      ![Click Security Onion Grid Icon](Images/SO%20Grid.png)
   
   - Expand the node details and click on the Replay button.

      ![Security Onion Replay](Images/SO%20Replay.png)

   - Run: `sudo so-test`.

      - `so-test` is the command used by Security Onion to "replay" all PCAP files from previously captured malware.

It can take the `replay` a few minutes for Security Onion to run all of the PCAPs. This will be running as we move into the first lecture. By the time we reach our first activity, the PCAP replay should be completed and Security Onion should be ready to go.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 02. Instructor Do: Welcome and Overview (0:10)

#### Network Security Recap

Explain that last class, students learned how firewalls play a critical role in establishing a perimeter defense. They protect networks by making decisions based on rules that are set by administrators. Firewalls are designed to allow traffic from trusted sources and block traffic from untrusted sources.

- While a good first step, firewalls are only one layer of defense.

- Firewalls do have their limitations. Advanced hackers can easily fool them through packet manipulation.

- For instance, an attacker can send malicious data through a firewall by hijacking or impersonating a trusted machine. This is why it's crucial to have a strong defense in depth methodology to help protect sensitive data.

Today, students will build upon the defense-in-depth methodology by using IDS. 
Today, students will build upon the defense-in-depth methodology by using IDS. 

- Explain that students will learn how to use NSM and the Snort IDS engine to defend against network attacks and perform the following:

   - Analyze indicators of attack (IOA) and indicators of compromise (IOC)
   - Perform network forensics
   - Basics of incident/case management
   - Acquire intelligence and situational awareness of their networks providing them with the necessary information required

- The first half of the day introduces intrusion detection and prevention systems. Students will learn how to physically interconnect IDS systems and how to read, write, and interpret Snort rules.

- The second half of the day will introduce Security Onion and the role NSM tools play in network security.

Answer any questions before proceeding. 

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 03. Instructor Do: Introduction to Intrusion Detection Systems and Snort (0:20)

Today, we'll explore the world of IDSs and how they differ from firewalls.

Remind students that a firewall is a device used in network security designed to filter inbound and outbound traffic, based upon a set of predetermined administratively defined rules. 

- Firewalls make decisions to either allow or block traffic based on the following:

   - Source and destination IP address

   - Source and destination port number

   - Protocol type

- Firewalls do have their limitations. They can easily be fooled through packet manipulation by clever hackers. 

   - For instance, attackers can send malicious data through a firewall by hijacking or impersonating a trusted machine.

- Unlike firewalls, intrusion prevention and detection systems monitor, detect, and alert about an attack depending upon the configuration.

**IDSs** are tools that can both analyze traffic and look for malicious signatures. An IDS is like a firewall that also reads the data in the packets it inspects, issues alerts or alarms, and blocks malicious traffic if configured to do so.

- Explain that there are many varieties of intrusion detection systems, but today's class will begin by focusing on **Snort**, the world's most popular open-source solution.

**NSM** is the process of identifying weaknesses within a network's defense. It also provides organizations with situational awareness of their network.

- Explain that there are a variety of NSM solutions. Security Onion is an NSM. It is based on a specific Linux distribution that's derived from Oracle Linux. 

Pause to answer questions before proceeding.

#### Intrusion Detection System Overview

Explain that an IDS is a passive device that performs packet captures of all traffic that passes through a network interface.

- Point out that IDSs are not designed to **respond** to an attack, but rather to document and log attacks for future analysis.

- Emphasize that IDSs help organizations establish situational awareness of their adversaries, which may include intent and end objectives. Organizations can use this information to harden their defenses.

#### IDS Types

Point out that there are two primary types of IDS:

- **Signature-based** IDS compares patterns of traffic to predefined signatures. It has the following characteristics:

   - Good for identifying well-known attacks

   - Requires regular updates as new attack signatures are released

   - Vulnerable to attacks through packet manipulation that tricks the IDS into believing malicious traffic is good

   - Unable to detect zero-day attacks
   
- **Anomaly-based** IDS compares patterns of traffic against a well-known baseline. It has the following characteristics:

   - Good for detecting all suspicious traffic that deviates from the well-known baseline

   - Prone to issuing false alerts

   - Assumes normal network behavior never deviates from the well-known baseline

   - Excellent at detecting when an attacker probes or sweeps a network

#### Intrusion Detection Architecture

Explain that IDSs have two basic architectures:

- **Network intrusion detection system** (**NIDS**) examines traffic on an entire subnet on a network.

   - Matches all traffic to a known library of attack signatures

   - Passively examines network traffic at the points it is deployed

   - Relatively easy to deploy and difficult to detect by attackers

- **Host-based intrusion detection system** (**HIDS**) runs locally on a host-based system or user’s workstation or server. It has the following characteristics:

   - Acts as a second line of defense against malicious traffic that successfully bypasses a NIDS

   - Examines entire file systems on a host, compares them to previous snapshots or a baseline, and generates an alert if there are significant differences between the two

**Intrusion Prevention System**

Explain that an **intrusion prevention system** (**IPS**) does everything that an IDS can do, but it can also respond to attacks. An IDS doesn’t alter or react to packets as they enter the network. An IPS does this by blocking malicious traffic and preventing it from being delivered to a host on the network.

Emphasize the two main differences between an IPS and IDS:

1. An IDS physically connects via a network test access port (TAP) or mirrored port, also known as a switched port analyzer (SPAN).
  
   - **Network TAP** is a hardware device that provides access to a network. Network taps transit both inbound and outbound data streams on separate channels at the same time, so all data will arrive at the monitoring device in real time.

   - **SPAN**, or **port mirroring**, sends a mirror image of all network data to another physical port, where the packets can be captured and analyzed.

   - An IDS requires an administrator to react to an alert by examining what has been flagged.

2. An IPS physically connects inline with the flow of data. An IPS is typically placed in between the firewall and network switch. 

   - This requires more robust hardware due to the amount of traffic flowing through it.
   
   - It automatically takes action by blocking and logging a threat, thus not requiring administrative intervention.

Point out that an IDS generates an alert when a Snort rule detects malicious traffic that matches a signature. An alert is a message that’s created and sent to the analyst’s console as an **IOA**.

Explain that there are two primary types of indicators:

1. **IOA** indicates attacks happening in real time.

   - It is a proactive approach to intrusion attempts.

   - It indicates that an attack is currently in progress but a full breach has not been determined or has not occurred yet.

   - It focuses on revealing the intent and end goal of the attacker regardless of the exploit or malware used in the attack.

2. **IOC** indicates previous malicious activity. 

   - It is a reactive approach to successful intrusions.

   - It indicates that an attack occurred, resulting in a breach.

   - It is used to establish an adversary's techniques, tactics, and procedures (TTPs).

   - It exposes all of the vulnerabilities used in an attack, giving network defenders the opportunity to revamp their defense as part of their mitigation strategy, and learn from an attack so it won't happen again.

#### Snort

Explain that Snort is a freely available open-source network intrusion detection and prevention system. It can perform real-time traffic analysis and log packets on a network. Snort is used to detect a wide variety of attacks.

- Configuration modes

   Explain that Snort can operate in three modes:

   - **Sniffer Mode:** Reads network packets and displays them on screen
   
   - **Packet Logger Mode:** Performs packet captures by logging all traffic to disk

   - **Network Intrusion Detection System Mode:** Monitors network traffic, analyzes it, and performs specific actions based on administratively defined rules

Most Snort deployments use all three modes of operation.

#### Snort Rules

Explain how Snort uses rules to detect and prevent intrusions. Snort operates by:

1. Reading a configuration file

2. Loading the rules and plugins

3. Capturing packets and monitoring traffic for patterns specified in the loaded rules

4. When traffic matches a rule pattern, generating an alert or logging the matching packet for later inspection

Rules can direct Snort to monitor the following information:

- OSI layer: Watches for IP vs. TCP data

- Source and destination address: Where the traffic is flowing from and to 

- Byte sequences: Patterns contained in data packets that might indicate malware, etc.

Present the following Snort rule: 

 - `alert ip any any -> any any {msg: "IP Packet Detected";}`
   
- This rule logs the message "IP Packet Detected" whenever it detects an IP packet.

Using the following example, explain each part of the rule: 

`alert tcp any 21 -> 10.199.12.8 any {msg: "TCP Packet Detected";}`
 
   - This rule triggers an alert whenever a TCP packet from port `21`, with any source IP address, is sent to the IP `10.199.12.8`. With each alert, it will print the message "TCP Packet Detected."

   - Rule Header

      - `alert` is the action that Snort will take when triggered. 

      - `tcp` applies the rule to all TCP packets.

      - `any` applies the rule to packets coming from any source IP address.

      - `21` applies the rule to packets from port `21`.

      - `->` indicates the direction of traffic.

      - `10.199.12.8` applies the rule to any packet with this destination IP address.

      - `any` applies the rule to traffic to any destination port.

  - Rule Option

    - `{msg: "TCP Packet Detected";}` is the message printed with the alert.

- Let students know that Snort provides many additional actions and protocols, which can be combined to design rules for almost any type of packet.

Take a moment to address questions before proceeding.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 04. Student Do: Intrusion Detection Systems and Snort (0:15)

Explain the following:

- In this activity, you will play the role of an SOC analyst for the California Department of Motor Vehicles (DMV).

- Your CISO has advised you to implement new security controls as an added layer of protection for the driving records of all state citizens.

- In this activity, you will strengthen your knowledge of the concepts related to Snort and IDSs.

:globe_with_meridians: This activity will use breakout rooms. Assign students into groups of 3–5 and move them into breakout rooms. 

Send students the following file:

- [Activity File: Intrusion Detection Systems and Snort](Activities/04_IDS_and_Snort/Unsolved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 05. Instructor Review: Intro to Intrusion Detection Systems and Snort Activity (0:10)

:bar_chart: Run a comprehension check poll before reviewing the activity. 

Remind students that the goal of this activity was to reinforce concepts related to Snort rules and IDSs. An understanding of these concepts is critical to gaining insight into an attacker’s TTPs.

- Emphasize that an IDS is a passive device that performs packet captures of all traffic that passes through a monitored network interface.

- IDS systems provide an additional layer of defense.

- Point out that an IDS generates alerts when a Snort rule detects malicious traffic matching a specific signature. An alert is a message that’s created and sent to the analyst’s console as an indicator of attack, or IOA.

- Explain that an IPS is like an IDS, with the added capability of responding to attacks. An IDS doesn’t alter or react to packets as they enter the network, while an IPS can act upon traffic by blocking it and preventing it from being delivered to a host.

Use the following solution guide to review the answers: 

- [Solution Guide: Intrusion Detection Systems and Snort](Activities/04_IDS_and_Snort/Solved/README.md)

Pause to ask if there are any questions before proceeding.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 06. Instructor Do: Network Security Monitoring and Security Onion (0:20)

Remind students that an **NSM** can be used to provide situational awareness for an entire network.  One particular **NSM** that will be reviewed in this course is Security Onion. It has a rule-based system similar to Snort, but Security Onion uses Suricata as its event-driven mechanism instead.  Suricata provides Security Onion with alerts based upon configured rules.

   - Suricata rules are similar to Snort rules and use a compatible data structure.

   - Suricata provides added features like examining TLS certificates, HTTP requests, and DNS transactions.

:warning: **Heads Up:** Each PCAP may not be imported in its exact sequence from the previous session. Therefore, the alert IDs in your demo may vary from the screenshots in this lesson plan. 

#### Network Security Monitoring Overview

Begin by providing the following case study: 

- On October 2023, hackers released confidential information from 23andMe that contained personally identifiable information (PII) for many of its users, including full names, home addresses, and genealogical information.

- The compromise was achieved by using a common technique referred to as "credential stuffing".

   - This technique involves using a known password that was possibly leaked from another data breach.

- It was later discovered that the compromise included account information beyond just the initial users.  

   - 23andMe uses a feature that allows users to share profile with DNA relatives.  This allowed hackers to view some personal information from users that opted in for that feature as well. 

- Upon further investigation, it appears that the hackers were able to retrieve data prior to the initial disclosure by about two months. 

- If 23andMe had put a network security monitoring program in place, they may have discovered the attack much sooner, perhaps within hours.

-  NSM would have allowed 23andMe to stop the attack immediately, while gaining a good understanding of the TTPs used by the adversary to penetrate the network. 

- This could have been accomplished by adding additional layers of defense in the form of an NIDS, NIPS, and HIDS as part of an NSM program.

Explain that network security monitoring highlights the failures of existing security controls through the use of data analysis tools. NSM is most useful when the front-end layers of defense are compromised. 

Point out that it takes time for intruders to achieve their objectives. In many cases, infiltrators spend hours, weeks, months, or even years inside of a network before achieving their final objectives. It’s during this critical time that NSM can work to slow down or eliminate threat-based attacks. 

- NSM is threat-centric. Its primary focus is the adversary, not the vulnerability.

- NSM is focused on visibility of an attack, not the response to the attack. 

- NSM also reveals statistical data related to specific IOAs and IOCs from attacks.

#### NSM Strengths

Point out that NSM can only protect against the adversarial tactics that it can detect. This detection process takes place when collected data is inspected and irregularities are identified.

NSM allows organizations to:

   - Track adversaries through a network and determine their intent

   - Acquire intelligence and situational awareness

   - Be proactive by identifying vulnerabilities

   - Be reactive through incident response and network forensics

   - Provide insights related to advanced persistent threats (APTs)

   - Uncover and track malware

#### NSM Weaknesses

It’s important for security administrators to know the limits of their defenses so they can better prepare new ones. NSM capabilities are extremely limited in the following situations:

   - Encrypted traffic and VPNs: NSM and IDS do not have the capability to read encrypted traffic. Adversaries will often use this tactic to bypass security defenses.

   - Underpowered hardware: NSM and IDS require adequate amounts of processing and memory to function well. Larger networks have more traffic, requiring more powerful hardware requirements and larger expenses.

   - Mobile communication platforms: Adversaries often use mobile radio communications to obfuscate their attacks because it's difficult for NSM and IDS to monitor radio transmission waves.

   - Legal and privacy issues: NSM is an invasive process that monitors and records all network data as it passes through. Therefore, there may be legal implications regarding certain types of data collected by an NSM.

   - Limited access to network taps: The placement of an NSM sensor can be limited at certain areas of the network.

#### NSM Stages and Processes

Explain that NSM operates under two distinct stages, each with two processes.

   1. **Detection:** In this stage, an alert is first generated in the Security Onion analyst's console. (Security Onion, which you'll learn about in a moment, is a tool that collects alert data from a Suricata IDS engine.)

      - **Collection:** The event is observed and the data is stored in a PCAP file. 
   
      - **Analysis:** The alert data is identified, validated, documented, and categorized according to its threat level.
   
   2. **Response:** In this stage, a security team responds to a security incident with two processes:

      - **Escalation:** All relevant individuals are notified about the incident.
   
      - **Resolution:** The process of containment, remediation, and any additional necessary response.

#### NSM Sensor Connectivity

Explain that IDSs are generally placed at strategic locations in a network where traffic is most vulnerable to attack. These devices are typically placed next to a router or switch that filters traffic.

Remind students that an IDS can be physically connected to a network in two ways:

   1. **Mirrored Port or SPAN:** A SPAN port is a function of an enterprise-level switch that allows you to mirror one or more physical switch ports to another port. A mirror image of all data will flow across both ports equally. This is what allows the IDS to perform packet captures on all inbound and outbound traffic within a network.

   2. **Network TAP:** TAPs allow us to access our network and send that data in real time to our monitoring systems. One example of a TAP is known as an aggregated TAP, in which a cable connects the TAP monitor port with the NIC on the sensor. This specific placement allows traffic to be monitored between the router and switch.  

#### Security Onion

Today we'll work with Security Onion, a network security monitoring platform that provides context, intelligence, and situational awareness of a network.

- Security Onion 2.4 is based upon Oracle Linux 9, this is an open source Linux distribution provided for free redistributation by Oracle.

- Security Onion contains a variety of NSM tools used to monitor and protect networks from attacks.

- Security Onion also contains a case management system, also referred to as incident management, to record, identify, and analyze security threats and incidents.

Point out that today we'll be using a few of these NSM tools to help us with an incident detection and response routine that will simulate a real world situation.

There are two ways to work with Security Onion. One is through the shell interface, but most of the actual Security Onion tools and workflow are handled through a web browser.

Security Onion has a few different ways to work. 

- One way involves incident detection that involves alert triage and case creation. 

- Another approach is to actively review and search through alerts that might indicate either an IOA or IOC event.  

There are tools built directly into the SOC interface these workflows.  These tools include Alerts, Dashboards, Hunt, Cases, and PCAP.  The other tools will launch into separate browser tabs.


Explain that the tools we will be using are:

   - **Alerts:** Pulls together alert data generated from Security Onion. It provides important context for alerts,  which we can use to complete more detailed analysis of the data. 

   - **Hunt:** Allows users to create custom queries to help find possible incidents.

   - **PCAP:** Provides a way to view details of captured TCP traffic, similar to using tools like Wireshark.

   - **Cases:** Allows you to monitor and analyze incidents by creating cases based off of suspicious findings for further investigation.

   - **NetworkMiner:** This performs advanced network traffic analysis. It extracts artifacts from PCAP files and provides an intuitive user interface with which to analyze them. It also allows the analyst to analyze, reassemble, and regenerate transmitted files and certificates from PCAP files.

#### Alert Data

Point out that Security Onion uses Suricata rules, similiar to those used by Snort, to watch and interpret network traffic and create messages when it sees something it is programmed to report. These alerts are based on patterns of bytes, counts of activity, or even more complicated options that look deeply into packets and streams. 

Let students know that we'll discuss the workflow using the Alerts in the Security Onion NSM suite. This is the interface that security analysts will use to gain a quick overview of events on their network. 

#### Alerts

Explain that the Alerts interface has six key functions that help NSM analysts with their work:

   1. It performs simple aggregation of alert data records.

   2. It makes certain types of metadata and related data available.

   3. It allows queries and review of alert data.

   4. It allows queries and review of session data.

   5. Allows easy transitions to drill down into the details of alerts.

   6. Provides a work flow that allows analysts to generate cases for further escalation and investigation.

Point out that the Security Onion Alerts Dashboard allows for the customization of how alerts will be displayed:

![Security Onion Alerts Options](Images/SO%20Alerts%20Description.png)

- **Alert Results:** Displays detailed alert data, including:

   1. Count displays the number of a events matching a specific rule set

   2. rule.name is the name of the rule that was triggered by the event

      - The Suricata rule that generated the alert, obtained from the IDS engine.

   3. event.module is the module that detected the event (Suricata)

   4. event.severity_label provides a rating for how severe an event should be considered

![Security Onion Alerts Panel](Images/SO%20Alerts.png)


- The alert panel has four default fields that we should look at:

   1. **ST or Status:** Colors indicate severity levels of "real-time" or "RT" events.
   
      - **Red:** Critical. There is a possible data breach in progress that must be resolved immediately.

      - **Orange:** Moderate. There is a high potential for data breach that requires immediate review.

      - **Yellow:** General. There is a low potential for data breach, and it requires review.

   2. **Alert Count:** The number of events created by Security Onion to itemize alert data.

   3. **Rule Name:** IP address of the source identified by the alert.

   4. **Event Severity Level:** The message generate by the Suricata rule option.

#### Security Onion Alert Panel Drilldown

Explain that, as shown in the screenshot, the generated alert can be further examined by clicking it and selecting `Drilldown`. The analyst then must decide if this is benign or malicious. This demonstration will focus on how to obtain data using these tools and the process to make this decision.

![Security Onion Alert Drilldown](Images/SO%20Drilldown.png)



#### Security Onion's Drilldown

The next screenshot is an example of a `Drilldown` on the rule set in Security Onion that activated this alert.

![Security Onion Drilldown Results](Images/SO%20Drilldown%202.png)

- **Suricata Rule:** In the top portion of the window, we see the Suricata NIDS engine that generated the alert data when traffic matched one of its rules. 

   - Alert data is an indicator of attack (IOA). An analyst may have to determine if it represents benign or malicious activity. 
   
- **Examine Event Fields:** Click on the arrow next to the event to review all of the details regarding the event.

![Security Onion Event Details](Images/SO%20Drilldown%20details.png)

   - Scroll down to review the rule that triggered the alert
   
![Security Onion Alert Rules](Images/SO%20Drilldown%20rule.png)

   - Rule names begin with text like "ET" (for Emerging Threats, an IDS rule source).
   

- **Add Event to a Case:** An incident like this probably requires further investigation.

   - Add this alert to a Case by clicking on it and select `Add to Case`

![Add alert to SO Case](Images/SO%20Case1.png)

   - A prompt will ask whether to create a new case or add it to an existing case.

![Add to Case Prompt](Images/SO%20Case%202.png)

   - Explain that once the case is created you will be prompted to add details like Case Title, comments, attachments, events, etc.

![Enter Case details](Images/SO%20Case%203.png)

   - Alternatively, you can quickly pivot by clicking on the blue triangle with an exclamation point (1) and click `Escalate to new case`.

      - This will populate a lot of the data for you automatically based off of the event.

![Pivot to Case Creation](Images/SO%20Case%201A.png)

- **PCAP Data:** The packets can be further examined by going into PCAP view. 
  - Click on `Alerts` on the left, select one of the alerts listed as malware
    - This example uses the alert `ET MALWARE Generic - POST To .php w/Extended ASCII Characters (Likely Zeus Derivative)`

   - When the results are filtered, click on one of the alerts and select PCAP from the dropdown

![PCAP Example](Images/SO%20PCAP1.png)

   - The PCAP option shows a more detailed view of the data capture. It includes more packet information and data streams presented in hex and text form. From here the actual packet capture can also be exported to allow it to be opened in other tools, like Wireshark, for further analysis.

![PCAP Details](Images/SO%20PCAP.png)

#### Analyzing PCAP Data

Explain that an analyst can use data found within packet captures to reveal identifying information about an attacker. This includes their domain name registries, and IP addresses.

- Other information may include the country of origin, and, ideally, the names, email addresses, or phone number of the DNS registrants.

Emphasize that analysts can utilize the data to formulate attacker profiles.

- Look at the example `Drilldown` below to see that the country of origin for this particular sample is the United States.

![PCAP Data](Images/SO%20PCAP%20Data.png)

Stop and ask if anyone has any questions before proceeding.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 07. Student Do: Security Onion and NSM (0:20)

Explain the following:

- In this activity, you will continue your role as an SOC analyst for the California DMV.

- It’s critical for your organization to understand the limits of what it can detect, adversarial tactics, and how to quickly apply lessons learned to mitigate newly discovered security vulnerabilities.

- For this activity, you will strengthen your knowledge of concepts related to Security Onion and network security monitoring.

:globe_with_meridians: This activity will use breakout rooms. Assign students into groups of 3–5 and move them into breakout rooms. 

Send students the following file:

- [Activity File: Security Onion and NSM Overview](Activities/07_Security_Onion_NSM/Unsolved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 08. Instructor Review: Security Onion and NSM Overview Activity (0:10)

:bar_chart: Run a comprehension check poll before reviewing the activity. 

Remind students that the goal of this activity was to reinforce concepts related to NSM and Security Onion. 

- An understanding of these concepts is critical for gaining insight into an attacker’s intent, tracking adversaries through a network, and acquiring intelligence and situational awareness.

Point out that the main tasks we needed to complete were:

- Reinforce concepts by answering questions.

- Analyze an IOA (Snort alert), and establish an attacker profile.

Use the following solution guide to review the activity: 

- [Solution Guide: Security Onion and NSM Overview](Activities/07_Security_Onion_NSM/Solved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 09. Break (0:15) 

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 10. Instructor Do: Alert - HTTP File Extraction (0:15)

Explain that there will be many times when an alert requires an analyst to do some data mining. A security analyst must have a thorough understanding of how NSM tools are integrated in order to do this. These skills help speed up incident and response efforts.

In the following walkthrough, we will explore the Security Onion interface, using it as the starting point for learning other NSM tools for security investigations.

:warning: **Heads Up:** The IP addresses used in the demos and activities need to be treated as prototypical rather than literal. The actual IP addresses will need to be determined before starting the exercises.

#### Security Onion Demo

The first thing we will do is search using a filter for the IP address from the IOA.

Launch an instance of Security Onion. Do the following steps:

   - Step 1. Click the Hunt icon on the left.
  
   - Step 2. Select HTTP from the dropdown to group the results by the HTTP command. 

Now, we will only see information related to our filtered alert data, as seen below.  

   ![Security Onion Hunt](Images/SO%20Hunt%201.png)


Next, scroll down to the bottom to review the results:

   - From this example, you can see there is a lot of HTTP traffic. Narrow down the results by filtering by local IP `192.168.3.35`.

   ![Security Onion Hunt Results](Images/SO%20Hunt%202.png)

Now, we can see from the results that this user downloaded a file from a website. Select the packet using the `GET` http.method, click on Actions and then on PCAP.

![Hunt to PCAP](Images/SO%20Hunt%203.png)

Once the PCAP page opens, click to download the PCAP file.

![Download PCAP](Images/SO%20Hunt%204.png)

- Explain that we will now take this PCAP file and open it using a new forensic tool.

- This tool can extract any files that were installed on the user's machine, and provide us with an attacker profile.

#### NetworkMiner

Explain that NetworkMiner is an NSM tool that's included as part of the Security Onion NSM suite of tools. 

   - NetworkMiner performs advanced network traffic analysis (NTA) of extracted artifacts, and presents them through an intuitive user interface. 

NetworkMiner by following the steps below. 

**Instructor Note:** Details may vary slightly from screenshot but the concepts still apply.

  - Click on **NetworkMiner** amd click file to the PCAP from your downloads folder.

![Network Miner Pivot](Images/NetworkMiner%201.png)

- On the NetworkMiner's interface. Pay attention to the tabs at the top. We'll focus on the **Files** tab next.

- Select the **Files (2)** tab as seen in the screenshot. This tells us that NetworkMiner was able to extract and reconstruct the two files from Security Onion's PCAP captures.

- Review the source port and protocol used.

- Review the protocols used during transmission.

![Network Minor Files](Images/NetworkMiner%202.png)

- Right-click on one of the files.

- Click on **Open folder**.

![Open Folder](Images/NetworkMiner%203.png)

- This will open the folder on the local hard disk where NetworkMiner stores the recompiled files.

![Files Folder View](Images/NetworkMiner%204.png)

- Next, open the Chrome Web Browser, navigate to www.virustotal.com, and select **File**.

- Explain that these are parts of the malware. We can click and select on any one of the files and get results. Select the `hohhveswgc.php` file for inspection.

![Select file to inspect](Images/VirusTotal%201.png)

Explain that this opens the VirusTotal search tool, which will attempt to match these files to any known malware signatures.

- Point out that VirusTotal returned the number of matches it discovered for well-known virus engines against this particular file.

- Explain that VirusTotal hashes the files, which establishes a malware signature used to look for a match and determine the common name for the malware.

- Point out that VirusTotal lists all of the common names for this specific malware.

Emphasize that security professionals, especially security researchers, use this website frequently when performing malware analysis and establishing the TTPs used by adversaries to infiltrate networks. This information contributes to what is commonly referred to in the industry as an "attacker profile." These help us know our enemies in order to better defend against future attacks.

![VirusTotal Results](Images/VirusTotal%20Results.png)

#### Summary

Remind students that the strength of NSM depends on knowing the limits of what you can see and detect, developing an understanding of adversarial tactics, and applying that knowledge to mitigate future attacks. This process happens when collected data is inspected and irregularities are identified.

Point out that NSM allows organizations to:

- Track adversaries through a network and determine their intent.

- Acquire intelligence and situational awareness.

- Be proactive by identifying vulnerabilities.

- Be reactive through incident response and network forensics.

- Provide insights related to APTs.

- Uncover and track malware.

Pause to answer any questions before proceeding.

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 11. Student Do: Alert - FTP File Extraction (0:20)

Explain the following:

- In this activity, you will continue your role as an SOC analyst for the California DMV.

- Immediately after deploying your new defenses, your organization experienced an attack.

- You need to examine an alert to determine if any systems were breached and if any data was supplanted or exfiltrated from the network.

:globe_with_meridians: This activity will use breakout rooms. Assign students into groups of 3–5 and move them into breakout rooms. 

In this activity, you will strengthen your knowledge of concepts related to the Detection and Response stages of the NSM process.

Send students the following file:

- [Activity File: Alert - FTP File Extraction ](Activities/11_(Alert)_FTP_File_Extraction/Unsolved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

### 12. Instructor Review: Alert - FTP File Extraction (0:10)

:bar_chart: Run a comprehension check poll before reviewing the activity. 

Remind students that the goal of this activity was to reinforce  concepts related to network security monitoring and the NSM Detection stage processes of Collection and Analysis. 

   - Note again that an understanding of these concepts is critical for gaining insight into an attacker’s intent, tracking adversaries through a network, and acquiring intelligence and situational awareness.

Point out that the main tasks we needed to complete were:

- Use Security Onion to analyze an indicator of attack (Suricata alert).

- Use NetworkMiner to perform network forensics by establishing an attacker profile and the intent behind the attack.

- Determine if a breach had occurred and whether or not any files were supplanted on or exfiltrated from the network.

Use the following solution guide to review the answer: 

- [Solution Guide: Alert - FTP File Extraction](Activities/11_(Alert)_FTP_File_Extraction/Solved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-2-contents)

---

© 2024 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.

