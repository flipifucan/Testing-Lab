## 19.1 Lesson Plan: Tabletop Exercise

### Overview

A Tabletop Exercise is a discussion-based session where team members, or us as a classroom, meet to discuss roles, responsibilities, and reactions in the face of a hypothetical scenario. In the context of cybersecurity, this exercise is crucial for preparing organizations to effectively respond to real-world cyber threats and breaches. It allows participants to simulate the decision-making process in a risk-free environment, fostering a deeper understanding of their incident response plan and identifying any gaps or weaknesses in their current strategies. For today, we will work through the exercise together as a class.

#### Objectives of a Tabletop Exercise

- **Enhance Preparedness:** Improve the readiness of the IR Team and relevant stakeholders to respond to cybersecurity incidents efficiently and effectively.
- **Identify Gaps:** Discover any deficiencies in the current incident response plan and cybersecurity measures.
- **Improve Coordination:** Strengthen coordination and communication within the IR Team and between different organizational departments.
- **Educational Opportunity:** Serve as a valuable learning experience for students to understand the dynamics of real-world cyber incident response.

#### Conducting Operation Silent Breach at Rekall: A Classroom Walkthrough

**1. Pre-Exercise Preparation**
- **Participants:** Break the classroom out into three groups, then assign each group a role in the exercise (IR Team, Endpoint Security Team, Network Security Team).
- **Materials:** Distribute the scenario overview and any relevant background materials to students ahead of time to allow for preparation.
- **Facilitator:** You, the instructor, will be the facilitator. Your job is to guide the discussion, introduce injects (new information or developments), and keep the exercise on track.

**2. Introduction**
- Introduce the scenario, outlining the background of Rekall's situation and the objectives of the exercise. 

**3. Scenario Walkthrough**
- **Initial Briefing:** Students will review the initial situation as described in the scenario introduction.
- **Incident Detection and Analysis:** Discuss the steps for identifying the scope of the breach and the initial response actions.
- **Containment and Eradication:** Explore strategies for containing the breach and eradicating the threat from the network.
- **Recovery and Communication:** Debate recovery priorities and the approach to internal and external communication.
- **Post-Incident Review:** Consider the steps for conducting a thorough review of the incident, reporting findings, and implementing recommendations.

**4. Discussion and Feedback**
- Throughout the exercise, encourage students to discuss their proposed actions, justify their decision-making process, and consider alternative approaches.
- You can introduce new injects to simulate real-world complexities and test the students' adaptability.
- After completing the scenario walkthrough, you will lead a debriefing session to discuss what was learned, identify strengths and areas for improvement, and determine how these insights can be applied to enhance the organization's cybersecurity posture.

**5. Conclusion**
- The exercise concludes with a summary of key takeaways and an action plan for addressing identified gaps in the incident response plan and cybersecurity measures.

#### Key Takeaways

This Tabletop Exercise is an invaluable tool for developing the practical skills and strategic thinking necessary for cybersecurity incident response. By simulating a realistic cyber attack scenario, students gain hands-on experience in navigating the complexities of cyber threats, which enhances their ability to protect and respond effectively in the event of a real incident.

### Introduction to Operation Silent Breach at Rekall: Consultant Briefing

#### Background

Rekall, a global financial services firm, prides itself on its robust security measures and cutting-edge technological infrastructure. However, the digital landscape's evolving nature presents a constant battle against cyber threats. Recently, Rekall has fallen victim to a sophisticated cyber attack. Preliminary investigations reveal that an attacker has successfully breached the internal network through a phishing campaign. Having gained a foothold, the attacker has initiated a multistage attack, culminating in the upload of ransomware to several critical servers.

#### Scenario Details

**Initial Breach:** The attacker gains initial access to the network through a targeted phishing campaign, deceiving a high-privileged user into executing malicious code.

**Lateral Movement:** Once inside, the attacker uses the compromised credentials to move laterally within the network, seeking out servers that host critical financial data and internal communication tools.

**Establishing Persistence:** The attacker establishes backdoors in the network, ensuring continued access even as they begin to deploy ransomware across targeted servers.

**Ransomware Deployment:** The ransomware, which has been designed to evade detection by traditional antivirus solutions, begins encrypting files on several critical servers, including those handling client transactions, internal communications, and data storage.

**Denial of Service:** The encryption process and subsequent demands for ransom cause a massive denial of service (DoS) within Rekall's operations. Essential services become unavailable, leading to a halt in client transactions, disrupted internal communications, and a significant loss of client trust.

**Exfiltration Attempt:** Before deploying the ransomware, the attacker attempts to exfiltrate sensitive data, targeting personal client information, financial records, and proprietary company data. This action suggests the attack's motive may extend beyond financial gain, hinting at espionage or a competitive sabotage effort.

#### Added Complications

- **Misleading Information:** The attacker uses sophisticated techniques to cover their tracks, including planting false indicators of compromise (IoCs) to mislead the IR Team.
  
- **Communication Challenges:** The internal communication tools are compromised, hampering the IR Team's ability to coordinate their efforts effectively.

- **Regulatory and Legal Implications:** The nature of the data at risk brings immediate regulatory and legal implications, adding pressure to the response efforts. The firm faces potential violations of data protection laws, such as GDPR or CCPA, leading to hefty fines and legal challenges.

- **Public Relations Crisis:** News of the attack leaks to the public, which causes a PR crisis. Rekall must manage its public image while addressing client concerns and maintaining transparency about the incident's impact.

#### Objectives for the IR Team

1. **Rapid Identification and Containment:** Quickly identify the extent of the breach and contain the ransomware's spread to prevent further encryption and service disruption.

2. **Eradication and Recovery:** Eradicate the attacker's presence from the network and recover encrypted data, prioritizing critical servers to resume normal operations as swiftly as possible.

3. **Communication and Coordination:** Establish secure lines of communication for the IR Team and coordinate with legal, PR, and regulatory teams to manage the fallout effectively.

4. **Long-term Mitigations:** Analyze the breach to understand how the attacker bypassed existing defenses, and implement long-term security enhancements to prevent future incidents.

5. **Stakeholder Management**: Manage communications with stakeholders, including employees, clients, regulators, and the public to maintain trust and transparency throughout the incident response process.

### Class Do: Tabletop Exercise 

Break the classroom into three groups and assign each group to one of three roles: IR Team, Endpoint Security Team, or Network Security Team. Once the groups and their respective roles have been decided, inform the students that their role-specific information is in the student guide that has their role's name (e.g., IRTeamStudentGuide.md)

### Intructor Notes:

If students get stuck during the activity, there are certain bits of information you can give them to move the activity forward. Sometimes information can be left out on purpose. In these cases, treat it as improv and have students (or you) create something at whim. For example, if the IR Team asks the Network Security Team for the originating country of an IP, make something up!

#### IR Team: 

The IR Team should be working to contain the threat as well as preventing it from happening again. Here are some suggestions on what they can do along the way:

1. **Blocklist IPs and Domains:** Immediately add the external attacker IP and C2 server IPs to the blocklist on all firewall and intrusion-prevention systems to prevent further communication with the attacker's infrastructure.

2. **Enhance Monitoring:** Increase the logging level and monitoring on network traffic, especially focusing on traffic to and from the finance and HR department servers. Use network analysis tools to track any lateral movement attempts or further data exfiltration efforts.

3. **Isolate Compromised Segments:** Utilize network segmentation to isolate compromised network segments, particularly those showing signs of ransomware activity or unauthorized access attempts. Implement strict ACLs to limit access to sensitive data.

4. **Collaborate with the Endpoint Security Team:** Provide network logs and traffic analysis reports to the Endpoint Security Team to aid in identifying and mitigating compromised endpoints.

5. **Prepare for Recovery:** Coordinate with the teams to plan for the safe recovery of network services, ensuring that backup data has not been compromised before restoration.

#### NetSec Team:

Ensure that the questions asked by the IR Team lead to the following actions:

1. **Block C2 Communication:** Immediately update firewall rules to block all traffic to and from the identified C2 server IPs.
2. **Isolate Compromised Systems:** Utilize the network infrastructure to isolate systems that have communicated with suspicious IPs or show signs of ransomware activity.
3. **Monitor for Further Lateral Movement:** Set up alerts for SSH connections that match the patterns of the lateral movement attempts.
4. **Collaborate with Incident Response:** Provide all relevant logs and findings to the IR Team for a coordinated response effort.

#### Endpoint Sec Team:

Ensure that the questions asked by the IR Team lead to the following actions:

**Isolation and Remediation Actions**:

- **Immediate Isolation:** Quarantine FIN-SRV-01, FIN-WS-02, HR-WS-03, and HR-SRV-04 by disconnecting them from the network and moving them to a secure VLAN for further analysis.
- **Forensic Analysis:** Conduct a deep dive into the forensic evidence on compromised endpoints to understand the ransomware's behavior, persistence mechanisms, and any data exfiltration attempts.
- **Collaboration for Recovery:** Coordinate with the IT department to restore affected systems from backups, prioritizing critical business operations.
- **Regular Updates:** Provide timely updates to the IR Team regarding the status of compromised endpoints, ongoing analysis findings, and progress in containment and remediation efforts.
- **Documentation:** Maintain detailed documentation of all investigative steps, findings, and remediation actions to inform the post-incident review and contribute to the improvement of incident response processes.

---

© 2024 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.    
