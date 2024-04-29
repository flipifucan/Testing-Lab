### Tabletop Exercise: Endpoint Security Team Student Guide

#### Role Overview

As part of the Endpoint Security Team in the Operation Silent Breach scenario at Rekall, you are on the front lines of defense against the ransomware attack affecting the organization. Your role is crucial for identifying, isolating, and remediating compromised endpoints to mitigate the spread of the attack and assist in the recovery process.

#### Objective

Your primary objective is to secure the endpoints within Rekall's network, ensuring that the ransomware does not spread further and that any compromised devices are quickly identified and remediated. You'll work closely with the Network Security and Incident Response (IR) Teams to provide a comprehensive defense and recovery strategy.

#### Key Responsibilities

- **Detailed Analysis:** Investigate signs of compromise, including unauthorized account usage, suspicious process activity, and unexpected network connections.
- **Containment and Isolation:** Quickly isolate affected endpoints to curtail the ransomware's propagation across the network.
- **Eradication and Recovery:** Work on eradicating the ransomware from compromised endpoints and facilitating the recovery of encrypted files.
- **Collaboration:** Communicate effectively with the Network Security Team and IR Team, sharing insights and coordinating on broader containment and eradication strategies.

#### Detailed Incident Information

**Compromised Accounts and Initial Entry Points:**
- **Account Names:** 
  - JohnDoe_Finance (initial entry via phishing email)
  - AlexR_HR (subsequent compromise through lateral movement)

**Compromised Endpoints:**
- **Finance Department:**
  - **Endpoint Names:** FIN-SRV-01, FIN-WS-02
  - **Signs of Compromise:** Execution of "SecurityUpdate.exe" followed by file encryption activities and ransom note creation.
- **HR Department:**
  - **Endpoint Names:** HR-WS-03, HR-SRV-04
  - **Method of Compromise:** Utilization of compromised credentials from JohnDoe_Finance to access HR systems and deploy ransomware.

**Lateral Movement Details:**
- **Techniques Used:** Pass-the-hash attack leveraging JohnDoe_Finance's credentials to gain unauthorized access to AlexR_HR's workstation (HR-WS-03)
- **Logs Excerpt:** 
  - Date: March 15th, 09:15 AM
  - Entry: "Successful login for AlexR_HR from IP 10.10.1.5 (FIN-WS-02) using SMB protocol."
  - Implication: The attacker used JohnDoe_Finance's compromised workstation to move laterally into the HR department's network segment.

**Indicators of Compromise (IoCs):**
- **Suspicious Processes:**
  - Name: svchost.exe (mimicking legitimate Windows process)
  - Path: C:\Windows\Temp\svchost.exe
  - MD5: 4d1718f3eaa17f65746e6c5d3d5013a2
- **Registry Changes:**
  - Key: HKCU\Software\Microsoft\Windows\CurrentVersion\Run\security_update
  - Value: C:\Users\JohnDoe_Finance\Downloads\SecurityUpdate.exe


---

© 2024 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.    
