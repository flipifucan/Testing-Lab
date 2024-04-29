### Tabletop Exercise: Network Security Team Student Guide

#### Role Overview

As the Network Security Team for Rekall during Operation Silent Breach, you are tasked with securing the organization's network infrastructure against the current ransomware attack. Your responsibilities include identifying the attack vectors, containing the breach, and preventing further unauthorized access by leveraging network security tools and protocols to protect Rekall's assets.

**Key Responsibilities**

- **Traffic Analysis and Monitoring:** Scrutinize network traffic to pinpoint malicious activities. Utilize intrusion detection systems (IDS) and network monitoring tools to detect anomalies that suggest unauthorized access or data exfiltration.
- **Containment and Segmentation:** Apply network segmentation and update firewall rules to isolate compromised segments of the network, halting the spread of ransomware. Implement access control lists (ACLs) to restrict traffic to sensitive areas of the network.
- **Collaboration and Communication:** Work closely with the Endpoint Security Team and IR Team, providing them with critical network insights and data to aid in the overall incident response effort. Ensure effective communication channels are maintained for the swift exchange of information.
- **Recovery and Resilience Enhancement:** Aid in the restoration of network services and fortify network defenses to bolster resilience against future cyber threats. This includes revising network security policies and implementing stronger encryption protocols.

**Initial Information Provided**

As Network Security Administrators tasked with managing the aftermath of Operation Silent Breach at Rekall, you have access to a range of detailed information and data points critical for analyzing the incident. This guide provides a structured overview of the specifics you need to track the attackers' activities within the network, understand the scope of the attack, and formulate an effective containment and eradication strategy.

**Incident Overview:**

- **Date and Time of Initial Breach Detection:** July 15, 2023, at approximately 10:42 AM GMT.
- **Method of Discovery:** Anomaly detection tool flagged unusual outbound traffic patterns.

**Phishing Email Details:**

- **Date Sent:** July 14, 2023
- **Approximate Time:** Between 08:30 AM and 09:15 AM GMT
- **Sender:** "it.support@rekalltech.com" (Note: This is a spoofed email address.)
- **Subject Line:** "Immediate Action Required: Secure Your Account"
- **Attachment/Link:** A malicious link directed users to a fake login page designed to harvest credentials. The URL was "hxxp://rekall-secure-login.com".

**Network Intrusion Details:**

- **Initial Compromise IP Address:** 192.0.2.45 was identified as the source of the phishing email and initial access point.
- **Command and Control (C2) Server IPs:** 
  - Primary: 203.0.113.10
  - Secondary: 198.51.100.25
- **Suspected Lateral Movement**: Multiple SSH (Secure Shell) connections were made from a compromised internal workstation, IP 10.1.2.15, to critical servers within the network.
- **Timestamps of Notable Activities:** 
  - Lateral movement attempts began on July 15, 2023, around 11:30 AM GMT.
  - Increased outbound traffic to C2 servers started July 15, 2023, at 12:05 PM GMT.

**Ransomware Deployment Details:**

- **Binary Name:** "SecurityUpdate.exe"
- **MD5 Hash:** 4d1718f3eaa17f65746e6c5d3d5013a2
- **Affected Servers and Systems:** Critical financial and HR servers showing signs of encryption activity from July 15, 2023, at 12:45 PM GMT
- **Ransom Note Location:** Desktops and root directories of affected servers, named "README_FOR_DECRYPT.txt"

**Network Traffic Anomalies and Log Excerpts:**

- **Unusual Outbound Traffic:** Significant data packets sent to 203.0.113.10 and 198.51.100.25, bypassing normal traffic patterns.
- **Log Excerpt Example:** 
  ```
  [July 15, 2023, 12:05 PM GMT] Outbound traffic spike detected. Source: 10.1.2.15 Destination: 203.0.113.10 Protocol: HTTPS Amount: 3GB
  ```
- **SSH Lateral Movement Attempts:**
  ```
  [July 15, 2023, 11:33 AM GMT] SSH login attempt. Source: 10.1.2.15 Destination: 10.2.3.22 Status: Successful
  ```
  
 ---

© 2024 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.    
