## 13.1 Lesson Plan: Introduction To Cloud Computing

### Class Overview

Today's class is the beginning of the Cloud Security and Virtualization module. It will introduce students to cloud computing service models, cloud networking, firewalls, and virtual computing.

Over these next four classes, students will build a basic cloud network using VMs and containers.

### Class Objectives

By the end of class, students should be able to:

- Distinguish between cloud services and identify an appropriate service depending on an organization's needs.

- Set up a virtual private cloud network.

- Protect their cloud network with a firewall.

- Deploy a virtual computer to their cloud network.

#### Instructor Notes

|:warning: **Important Note About This Week** :warning:|
|:-:|
| This week is a cumulative lesson. Students cannot miss one day and then continue to the next lesson. If a student is absent during one of the four days, they will receive assistance from the instructional staff to catch up.|
|Use this checklist to ensure that each student has completed each day's tasks: [Module 13 Daily Checklist](../Resources/Checklist.md). |
|As Azure interfaces can change frequently, please notify the curriculum team immediately as you're prepping if instructions or screenshots are out of date. Do NOT attempt to adjust settings or perform other workarounds without first consulting the curriculum team, as these workarounds may cut into the $200 credit.|

Over the next week, students will build out cloud infrastructure that includes a jump-box and 2 webservers running docker containers.

- Throughout this setup, we will follow the principle of least privilege and start with setting up a secure virtual network, before deploying machines to that network.

- Machines that are deployed will not have any access until firewall rules are put in place to access a specific service or machine.

- Each step and firewall rule is covered throughout the activities in a real-world development progression.

- Students should have a theoretical understanding of much of the networking portions of this week, but here they will get a chance to put everything together using real VMs and Cloud infrastructure.

Students will build and document a network similar to the network in this diagram:

![](Images/Final-Cloud-Diagram.png)

**Note:** The final solution may have 2 or 3 DVWA Servers.

Note that this module is four classes. This extended length will ensure that students have ample time to complete the required activities for the week. What students set up this week will lead into the setup for Project Week.

- Day 4 has optional activities if you are able to complete the required activities ahead of time.

- Otherwise, please feel free to extend the suggested times in the first three days as you will have time in Day 4 to catch up.

Azure has limited the free trial to only allow four machines to be deployed per region.

**Azure Changes:** Azure makes regular updates to their user interface so you may notice slight differences that come up. If you notice something that has changed or deviates from our included screen shots, please notify the curriculum team as soon as possible so we can apply a patch to the curriculum.

- Remind students that they need to shut off their labs. This is going to be especially important during this module and the Project 1 module. Students may be charged by Azure if they leave their labs on and exceed their $200 credit. While we can add quota hours to our Azure Lab Services environment, we will not be able to do anything for students who exceed the $200 limit on their personal Azure accounts.

After the cloud section of the course is over, students will want to destroy all of the virtual machines (VMs) that they have created with their account. Otherwise, Azure will eventually charge for storage space.

### Azure Lab Environment 

<details><summary>Lab Details</summary>
<br>

For the majority of the demonstrations and activities, the class will use Microsoft Azure cloud services and the Azure cloud portal.

You will **not** be using any of the Azure lab environments. Instead, you and the students will be using personal Azure accounts.

Students should have created free accounts created on [Microsoft Azure](https://azure.microsoft.com/en-us/) **before** the beginning of class. Please make sure every student is signed into their own personal Azure account and **not** the lab environments. If any students still need to create their account, have them do so before you begin class.

Send out the [Setup Guide](https://docs.google.com/document/d/1gs_09b7eotl7hzTL82xlqPt-OwOd0aWA78qcQxtMr6Y/edit) for anyone who still needs it.

- Send out [Azure Free Tier FAQ's](https://azure.microsoft.com/en-us/free/free-account-faq/).

**Important:** During these classes, students will need to generate Seure Shell (SSH) keys. Please remind any students that are using a Windows machine that they should have downloaded and installed [GitBash](https://gitforwindows.org/) on their machine. GitBash should be used to follow all SSH instructions for these modules.

#### References

- [Microsoft Azure](https://azure.microsoft.com/en-us/)

- [Docker](https://www.docker.com/)

- [Ansible](https://www.ansible.com/)

- [Microsoft Azure phone app](https://apps.apple.com/us/app/microsoft-azure/id1219013620)

    - It is recommended to use the Azure web portal while completing class activities.

    - This phone app will **not** be covered in any class or activities. However, students may want to explore using it outside of class.

</details>


### Module Day 1 Contents

- [x] [01. Instructor Do: Introduction To Cloud Computing](LessonPlan.md#01-instructor-do-introduction-to-cloud-computing-005)
- [x] [02. Instructor Do: Cloud Service Models](LessonPlan.md#02-instructor-do-cloud-service-models-010)
- [x] [03. Instructor Do: Virtual Networking](LessonPlan.md#03-instructor-do-virtual-networking-015)
- [x] [04. Student Do: Virtual Networking Activity](LessonPlan.md#04-student-do-virtual-networking-activity-020)
- [x] [05. Instructor Review: Virtual Networking Activity](LessonPlan.md#05-instructor-review-virtual-networking-activity-015)
- [x] [06. Break](LessonPlan.md#06-break-010)
- [x] [07. Instructor Do: Security Groups](LessonPlan.md#07-instructor-do-security-groups-020)
- [x] [08. Student Do: Security Groups Activity](LessonPlan.md#08-student-do-security-groups-activity-020)
- [x] [09. Instructor Review: Security Groups Activity](LessonPlan.md#09-instructor-review-security-groups-activity-015)
- [x] [10. Instructor Do: Virtual Computing](LessonPlan.md#10-instructor-do-virtual-computing-020)
- [x] [11. Student Do: Virtual Computing](LessonPlan.md#11-student-do-virtual-computing-020)
- [x] [12. Instructor Review: Virtual Computing Activity](LessonPlan.md#12-instructor-review-virtual-computing-activity-010)


### Slideshow 

The slides for today can be viewed on Google Drive here: [13.1 Slides](https://docs.google.com/presentation/d/1yw3ZTT_8Hm9rhl1iy2wS5fHUywceJcZT2LKw3K_MKNw/edit).

- To add slides to the student-facing repository, download the slides as a PDF by navigating to File > "Download as" and choose "PDF document." Then, add the PDF file to your class repository along with other necessary files.

- **Note:** Editing access is not available for this document. If you or your students wish to modify the slides, please create a copy by navigating to File > "Make a copy...".

### Time Tracker

The time tracker for todays lesson can be viewed on Google Drive here: [13.1 Time Tracker](https://docs.google.com/spreadsheets/d/1D-rEaPZXDy-9Ly9LHGakfGXP0gJdBRHAiSXFw8u7Udo/edit#gid=0).

### Student Guide

Make sure to send class the student-facing version of the lesson plan located here: [13.1 Student Guide](StudentGuide.md).

---

### 01. Instructor Do: Introduction To Cloud Computing (0:05)

Welcome the students to class and give them a quick overview of what we'll cover today:

- Overview of cloud service models and the variety of cloud services available to organizations.

- Setting up a virtual cloud network that will run all of their systems during this module.

- Securing a cloud network with a firewall and creating firewall rules.

- Virtual computing, creating web VMs in the cloud instance, and a jump box.

#### The Rise of the Cloud

Explain that before the cloud, organizations set up their networks on devices that they owned and controlled. These setups are called **on-premises networks** because they live on machines owned and operated on the company's physical property.

Currently, the cloud and cloud services (vs. on-premises setups) dominate the computing industry. Many organizations are looking to move operations to a cloud provider, but they are also worried about the security of the cloud.

This concern is justified. Since both on-premises and cloud deployments are, essentially, just networks, many fundamental security concerns apply in both contexts. However, some concerns apply to the cloud and not to on-premises setups. These include:

- **Complex architecture:** Systems must be built to both ensure basic security and allow infrastructure personnel to securely monitor, reconfigure, and redeploy machines as needed. This is typically easier to do securely with on-premises machines, since these are not exposed to public networks unless they need to be. Since cloud deployments are remote, we must take extra steps to ensure they are only exposed to the relevant parties.

- **Extensive management:** The cloud offers much more flexibility than organizations are used to, giving them freedom to create many more machines. This flexibility is a good thing, but it also makes operations management more complex. Machines can appear and disappear seemingly at random, so properly tracking everything requires additional skills and techniques.

- **Different threats:** The cloud is exposed to public networks. Cloud providers handle certain aspects of security for an organization, which means security professionals have new and different things they must pay attention to. Malicious actors will execute escalation and lateral movement tactics differently on the cloud than on-premises.

- **Ensuring availability:** High availability of machines is a large part of security on the cloud. Ensuring availability and redundancy on the cloud is done differently than with on-premises environments.

Emphasize that protecting cloud deployments is not harder than protecting on-premises networks. However, it is distinctly different. Therefore, being able to protect cloud deployments is a valuable skill for a cybersecurity professional.

List some job roles in which these skills are used:

- **Cloud Security Analyst** or **Cloud Penetration Tester:** These roles need to understand cloud architecture in order to test the security settings for a given environment.

- **Cloud Architect:** This role builds out a cloud environment for an organization. They are expected to understand how to build-in security from the beginning.

- **DevSecOps:** These roles are responsible for maintaining production and testing environments for an organization's developer and QA testing teams. They are expected to build and maintain secure systems at every step of the development process.

Let students know that today's activities will take them through the basics of setting up a cloud environment protected by a firewall and hosting a few virtual machines.

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 02. Instructor Do: Cloud Service Models (0:10)

:warning: **Heads Up:** For all demos, you should be using your own personal Azure account. Please make sure that you are logged in at portal.azure.com.

Explain that students can think of the cloud in the same way they would think about an on-site data center or network. The cloud has all of the same equipment: servers, virtual machines, routers, firewalls, load balancers, etc. The difference is that, in the cloud, most of these items are virtualized, meaning they are software instead of hardware.

Emphasize that this allows a cloud administrator to create entire networks of computers, servers, and other equipment, all virtualized by software. An entire setup may only physically exist on a few powerful virtual servers.

The fact that cloud networks are virtualized and defined by software gives them numerous security benefits:

- **Ground-up security:** From a security perspective, the cloud presents an opportunity to build a secure system from the beginning, as opposed to trying to implement new security measures on old systems.

- **Easy configuration:** Instead of having to learn the many different tools that will be included on a network, an administrator can use the cloud service provider's website portal or command line to create all their needed items.

- **Quick turnaround:** Compromised and insecure machines can be discarded and replaced quickly, at no additional cost to the organization.

- **Personalized networks from cloud providers:** Software and configuration-as-code allows cloud providers to deploy the specific network that engineers need for their circumstances. Security specialists can define the secure network they need, and the cloud provider can create and test the deployments, making the networks more dependable.

- **High availability and fault tolerance:** Without their own physical data centers, engineers can focus on deploying their machines in multiple places, and the provider can maintain the data center. This way, cloud networks are more robust against power outages, DoS attacks, and other threats, as long as they are configured correctly.

- **Easy implementation:** Security controls can be implemented more easily because they only require modifications to software-defined networking patterns. No complicated rearrangements of physical wiring are necessary.

- **Affordability:** Organizations can use powerful machines that they would not be able to afford if they had to purchase and maintain them themselves. For example, GPU processing units, which are very expensive to buy and lose to an attacker.

#### Cloud Services

Reiterate that deploying cloud services securely is different from developing secure on-premises networks. We'll need to understand which services cloud providers make available, what each service does, and when to use each one.

Explain that all cloud services add the phrase "as a service" to the name of the service. For example: platform as a service (PaaS) and software as a service (SaaS). Students will see the "aaS" acronym on certification exams as well as in job requirements.

Explain the main cloud services:

**IaaS (Infrastructure as a Service):** A service provider offers pay-as-you-go access to storage, networking, servers, and other computing resources in the cloud.

- Security benefits include high availability, guarantees that base machines are up-to-date at the time of deployment, and provider-enforced security controls, such as basic access management.

- Organizations can focus on implementing functionality and security that is relevant only to their business concerns, and not worry about the basics of secure deployments.

- AWS, Azure, and Google Cloud all offer IaaS.

**PaaS (Platform as a Service):** A service provider offers access to a cloud-based environment in which users can build and deliver applications. The provider supplies the underlying infrastructure.

- Organizations can leverage powerful applications that are guaranteed to be secure and available, without having to properly implement security themselves.

- Azure Classroom Labs, on top of which this course's lab environments are deployed, is one example. It guarantees availability and provides access only to the ports necessary to connect to the labs.

**SaaS (Software as a Service):** A service provider delivers software and applications through the internet. Users subscribe to the software and access it through the web or vendor APIs.

- The software runs in environments that are guaranteed by the provider to be secure. Engineers do not need to worry about secure deployment.

- Cloud software such as the Microsoft 365 Cloud Office Suite and Apple's Cloud iWork are examples of SaaS.

**DaaS/DBaaS (Data as a Service/Database as a Service):** A service that provides a company's data product to the user on demand, regardless of geographic or organizational distance between provider and consumer.

- The main security advantages are high-availability and fault tolerance. DaaS ensures data is always available, even if there is a power outage at a single data center, and ensures that data is still deployed from a center as close to those consuming it in order to reduce latency.

- An example of a DaaS is a marketing company that keep databases of consumers categorized for many different industries.

**CaaS (Communications as a Service):** A service that provides an outsourced communications solution. Such communications can include Voice over IP (VoIP or Internet telephony), instant messaging (IM), and collaboration and video conference applications.

- CaaS guarantees security by ensuring that communications are not vulnerable to eavesdropping, and provides comprehensive monitoring/record-keeping for auditing purposes.

- Zoom, FaceTime, Skype, and GoToMeeting are all examples of CaaS.

**CSaaS (Cybersecurity as a Service):** A service that offers threat monitoring, detection, response, and mitigation, as delivered by specialized experts.

- CSaaS provides end-to-end cybersecurity solutions for businesses, including threat monitoring, attack mitigation, and incident response.

- Sophos Intercept X, McAfee MVISION Cloud, as well as Azure and AWS services are examples of CSaaS

**CCaaS (Cybercrime as a Service):** This refers to the practice where individuals or groups can purchase cybercrime tools and services from underground markets to launch attacks without needing their own expertise or resources. Examples include:

- **RaaS (Ransomware as a Service):** RaaS involves ransomware operators creating and renting out ransomware tools to affiliates who then distribute and deploy these tools to attack victims. The profits from ransom payments are shared between the affiliates and the ransomware operators.

- **DDoS as a Service:** DDoS as a Service allows individuals to hire attackers to launch Distributed Denial of Service (DDoS) attacks against targeted websites or online services. The goal is often to overwhelm the targets with a flood of internet traffic, making them inaccessible to users.

**XaaS (Anything as a Service):** This refers to cloud services providing any combination of the offerings mentioned so far.

Point out that these services are presented differently by different providers. Also, some providers offer simplified versions of these services to make them easier to implement.

Pause and ask if the students have any questions about these services so far.

Point out some pros and cons of using a pre-configured service as opposed to building a custom solution:

- A pre-configured service is faster to set up.

- A pre-configured service requires less training and research for a system administrator.

- A custom solution gives the organization complete control over the solution.

- A custom solution may be less expensive, but requires more internal training.

Note that cloud providers all have the same abilities, but may look different. Additionally, different providers offer different levels of pre-configured services. Which provider an organization chooses will depend on their specific needs.

- We use Azure in this class, but this module is meant to be provider-agnostic. In other words, students should be able to apply the same skills to other providers.

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 03. Instructor Do: Virtual Networking (0:15)

This week will focus on the IaaS (Infrastructure as a Service) offering from Microsoft's Azure.

- IaaS is the most fundamental cloud service. All other services are software-based and assume that the infrastructure is already set up.

- Focusing on IaaS will allow us to get some hands-on experience configuring a cloud networking environment, as well as configuring the servers inside the network.

#### Determining the region for your environment

Explain that when selecting the resources for your cloud environment, you will need to select a region indicating where the resource is  geographically located.

- It is important to keep all resources in the same geographic region, as resources work together more efficiently when they are located physically close to each other.

- Ideally all geographic regions would always be available. However, that is not the case with cloud providers, including Microsoft Azure. 

- Therefore, it is important to determine an available region **before** we create any cloud resources.

#### Available Region Walkthrough

In this walkthrough, students will follow along on their machines to determine the available region that they will use throughout the activities. 

⚠️**Instructor Note:** If you are **not** using a free trial like the students, you will see many more region options than the students. It is very important that students follow along on their machines in order to determine which regions are available.  

1. Open your Azure portal and search for "virtual machines."

2. Use the **+ Add** button or the **Create virtual machine** button to create a new VM.

    * ![](Images/VM/CreateVM-b.png)
    
3. Select **Azure Virtual Machine**.    

4. Explain that there are two parameters that we will have to review in order to determine which regions are available: **Region** and **Size**. 

5. Scroll down to the **Region** dropdown and select `(Asia Pacific) Australia East`. This region commonly has the highest availibility. 

 	* ![](Images/VM/region1.png)

6. Scroll down to the **Size** option and select `See all sizes`.

 	* ![](Images/VM/region2.png)

7. On this next page, select the cheapest option available (usually B1ls or B1s). Then, click on the `select` button to confirm.

 	* ![](Images/VM/region3.png)

8. As long as you don't receive an error like the one below, then you are good to go! What you selected will be the region you will use throughout the class when selecting each resource.

 	* ![](Images/VM/region4.png)

9. If you did receive this error or you were unable to pick a size, return back to the **Region** dropdown and continue selecting other regions until an option offers the available sizes.
 
10. Once you have determined your region, click the red `X` on the top right to cancel out of this page. You will be notified that your unsaved edits will be discarded. Click `OK`. You will return to VM creation later in class. 

     * ![](Images/VM/region5.png)

#### Creating an Environment

Now that we have determined our region, we will begin creating a cloud infrastructure environment that students will use for the remainder of the module, as well as for other modules, such as Web Vulnerabilities and Projects.

Remind students that finding resources on a virtualized network requires more than just locating the physical machine on which they're deployed. Keeping resources organized on the cloud is often more challenging than in an on-premises environment.

Explain that in Azure, **resource groups** allow engineers to sort related resources into different groups, each of which can be easily located by name.

- A resource group is a logical grouping of all resources used for a particular setup or project. The resource group will contain the network, firewalls, virtual computers, and other resources that are needed for setup.

- Different organizations use different naming conventions for resource groups and their contents. In class, we'll simply name resource groups based on the project or activity they correspond to. Emphasize to students that, when working in a professional setting, they should take note of how their employers name resource groups.

The first step to creating an environment in Azure is to create a resource group. Once we have a resource group, we can start adding items to it, the first of which will be a virtual network.

Explain that the Azure Portal is intuitive and easy to use. The easiest way to find what you need is to use the search bar.

- Open your Azure portal and search for "resource group" to demonstrate.

    ![](Images/ResourceGroups/Search-resource.png)

- Select **Resource groups** in the search results and point out the **+ Create** button at the top.

  - Use the region that you just determined in the previous walkthrough.
  - Use a Resource Group Name you can easily remember
  - **Note:** The examples will use Red Team as the resource name.

  - **Important:** Remember the Resource Group Name you choose. Unless specified otherwise, all future resources need to be a part of this group

  - Ignore all other tabs and click **Create**.

    ![](Images/ResourceGroupCreate.png)

At any time, you can click on the Notifications Bell to see if the resources have been created.

  ![](./Images/notifications.png)

Now that we have a resource group, we can add a virtual network.

Explain that a **virtual network** is just what it sounds like: a collection of virtual machines that can communicate with each other.

- Unlike physical networks, which need physical wiring to achieve connections and discovery, virtual networks are much more flexible. The VMs on a virtual network can live in completely different data centers, but perform as if they are wired, as well as provide improved availability.

- Virtual networks can be quickly and easily reconfigured by clicking a few buttons in the portal. This is much faster and safer than rewiring a physical network to improve segmentation. It also results in less human error.

Explain that in order for virtual networks to behave identically to physical ones, cloud providers use software to emulate everything a physical machine uses to interact with a network, including:

- **Virtual Network Interface Cards (vNICs):** Similar to physical machines, VMs have software versions of "normal" NICs. Just like physical machines, VMs can have multiple vNICs.

- **IP addresses:** VMs have IP addresses, just like physical computers. IP addresses are considered their own type of resource in Azure, AWS, and other cloud environments.

- **Subnets:** Like IP addresses, subnets are considered separate resources in the cloud, meaning they can be created independently of other resources. After creating a virtual network, we can create a new virtual subnet and add it to the existing network. We can also create a new public IP address resource and associate it with an existing virtual machine.

Point out that creating a virtual network creates all of these resources at the same time. Students will not create them independently in this lesson. However, it is crucial to understand that this can be done, as it is common practice when managing and reconfiguring real-world deployments.

Remind students that they should rely on the IP addressing structures that they learned during the module on networking.

- Private networks will use one of three IP schemes:

    - `192.168.x.x`

    - `172.16.x.x`

    - `10.x.x.x`

- We can also use CIDR notation when defining a network space:

    - `192.168.1.0/24`

Explain that when creating a network in Azure, we will define a large network as well as a subnet inside that network. For example:

- `10.0.0.0/16` for the large network.

- `10.10.1.0/24` for the first subnet.

Point out that these default values will be automatically populated and students do not need to change them.

Emphasize that we'll only need to define the boundaries of the network and we can use the default values. Azure does the rest. We will not need to configure a router or DHCP, as these are configured automatically.

- Cloud providers configure this functionality automatically and **securely**, making it difficult to attack routers and DHCP servers directly.

- Azure also automatically provides logging capabilities, so we can easily check the history of the DHCP lease.

From the search bar, type Virtual networks and click create.

:warning: Make certain that you select the same Resource Group created in the earlier step.

Give the virtual network a name that you can remember.

:warning: **Heads Up:** Make sure you do not check the `Azure Bastion`, `Azure Firewall`, or `Azure DDoS Network Protection` boxes as they can easily surpass the $200 credit provided.

![](Images/CreateVirtualNetwork.png)

Final VNet settings should be similar to:

![](Images/CreateVirtualNetworkFinal.png)

Ask if there are any questions about defining a network space before proceeding.

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 04. Student Do: Virtual Networking Activity (0:20)

:warning: **Heads Up:** Make sure that students are using their personal Azure account for every activity. They should be logged in at portal.azure.com (instead of labs.azure.com).

:warning: **Heads Up:** Remind students to **not** enable the DDoS protection. This will exceed the $200 credit quickly; students will not be able to complete the remainder of this module and Module 14. Please remember and remind students that the boot camp will not cover any costs students incur beyond the $200 free credit.

Explain the following to students:

- In this activity, you will be playing the role of an Azure cloud security engineer for XCorp.

- XCorp's Red Team has opened a ticket asking for a cloud server to be set up with a vulnerable web application. The Red Team will use this server to train new team members. It has been approved by the director of security.

    - Note: If "Red Team" is a new term for students, explain that it is part of a penetration testing team that acts as malicious in order to find vulnerabilities in the target.

- At this time, there are no cloud resources dedicated to the Red Team, so you will need to create everything from the ground up, starting with the network that the server will use.

- You are tasked with creating a resource group and a virtual network for the Red Team.

:globe_with_meridians: This activity will use **breakout rooms**. Assign students into groups of 3–5 and move them into breakout rooms.

Send students the following file:

- [Activity File: Virtual Networking](Activities/04_Virtual_Networking/Unsolved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 05. Instructor Review: Virtual Networking Activity (0:15)

:bar_chart: Run a comprehension check poll before reviewing the activity. 

Ask students if there are any questions about creating a VNet or resource group.

Use the following file to guide your walkthrough:

- [Solution Guide: Virtual Networking](Activities/04_Virtual_Networking/Solved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 06. Break (0:10)

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 07. Instructor Do: Security Groups (0:20)

Remind students that our goal is to have a VM running behind a firewall on their virtual network in the cloud by the end of the day.

Now that we have a virtual network set up, we want to protect it with a firewall.

- As a review: Firewalls block or allow network traffic depending on what rules are set.

- We can set rules on single or multiple ports, coming from and going to a single IP or multiple IPs.

Explain that on the Azure platform, our basic firewall is called a **network security group (NSG)**. We will use an NSG to block and allow traffic to our virtual network and between machines on that network.

As mentioned earlier, many resources can be created independently of any particular virtual network and then attached to a VNet after creation.

- NSGs are a good example of this concept. In this demonstration and the following activity, we will create an NSG that blocks all traffic to and from the network. We will then attach it to the VNet to secure it.

- This model, while seemingly complex, has the advantage of allowing security engineers to create NSGs for different traffic profiles, which they can then replicate and apply to any VNet.

- For example, one might create an NSG called Desktop Connections, which clears RDP and VNC traffic to and from the VNet. Engineers can then use this NSG as a template, clone it, and apply it to any new or existing VNet that requires this type of access.

:warning: **Heads Up:** Students will attach an NSG to each VM in the virtual network instead of attaching the security group to the network itself. This will provide students with additional practice of applying NSGs to Azure entities. This practice emphasizes that NSGs allow cloud security engineers to implement granular access controls on each device in their networks.

In this project, we are attaching the same NSG to each VM, because each VM should have the same access controls. However, in practice, one could attach different NSGs to each VM, allowing engineers to differentiate access control requirements for different machines.

While a similar effect could also be achieved by attaching the NSG to the network instead of individual VMs, we prefer to emphasize that NSGs can be applied on a per-asset basis for fine-grained implementation of access controls.

#### Network Security Group Demonstration

Begin by completing the following:

- Open your Azure portal and search for "Network security group."

**Heads Up:** Do not select the "Network security groups (classic) option."

- Use the **+ Create** button to add a network security group.

- Name the group something memorable.

- Once the group is created, click **Go to resource**.

- Click **Inbound rules** on the left side.

Point out the default rules and explain their purpose:

![](Images/Security-Group-Demo/Default-Rules.png)

- The first rule allows all traffic to flow inside the VNet with destination and source both set to "Internal Network."

	- This means that all machines deployed using this Security Group will be able to communicate with each other.

- The second rule allows all traffic coming from a load balancer.

	- This means that **if** there was a load balancer assigned to this security group, it could send traffic to all the resources on the internal network.

- The final rule blocks all other traffic.

	- This means that all traffic from the internet is automatically blocked to any resource you protect with this Security Group.

Point out that when a machine is deployed to your VNet using this security group, you will have to create a rule that allows access to that resource.

Explain that, as an example, you will create a rule that allows RDP on port `3389`.

Create a rule using the following settings:

- Source: This is the source computer. It can be a single IP, a range of addresses, an application security group, or a service tag.

    - An application security group is a kind of web application firewall that we won't be using.

    - A service tag will filter for a specific location or source of traffic.

    - For this rule, we will set the source to your external IP address.

		- Under Source, select "My IP address."

		- This will populate the Source IP address with your current external address

- Source Port Ranges: Source ports are generated randomly, so it's best to leave the wild card (*) here to signify all source ports.

- Destination: We can choose between Any, IP address(s), Service Tag, or an application security group. We'll choose **Service Tag**.
    - In the "Destination service tag" dropdown that appears, select "Virtual Network."

	- Note that **if** you wanted to send traffic to a specific machine, you would enter its **internal** IP address here.

- Service: We can choose the protocol RDP.

- Destination Port Ranges: RDP uses port `3389`, so this will automatically be selected.

- Protocol: We can choose TCP, UDP, or ICMP. In the image above, **TCP** was automatically chosen when we selected RDP.

- Action: Firewall rules are either denying traffic or allowing traffic. Here, we are going to choose **Allow**.

- Priority: Firewall rules are implemented in sequence. A priority number allows rules to be read and sorted based on their priority number, from lowest to highest. We can see that the default rules start with a priority of 100, so anything we set under 100 will be read first. In the example above, we've used 500.

- Name/Description: You can name a rule whatever you like, but it is a best practice to name it what it is and describe what it does. Here, we will name it "Allow-RDP" and add the description: "Allow RDP from external IP over port 3389."

![](Images/AddInboundSecurityRule.png)

**Note:** The external IP is not shown in the screen shot.

Save your new security group rule.

Ask students if they have any questions about creating a security group or a security group rule.

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 08. Student Do: Security Groups Activity (0:20)

Explain the following to students:

- In this activity, you will continue building out the resources needed for XCorp's Red Team.

- At this time, we have a dedicated resource group and network in place for the Red Team. Before we start launching servers and resources, we want to set up some network protection.

- You are tasked with creating a network security group to control access to any resources in the subnet that you created in the last activity.

- By default, the Azure Security Group rules allow traffic from a load balancer and between machines on the VNet.

- To completely secure the VNet, we will create a rule that blocks **all** traffic.

:globe_with_meridians: Students should stay in the same **breakout room** groups as the previous activity.


- [Activity File: Security Groups](Activities/09_Security_Groups/Unsolved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 09. Instructor Review: Security Groups Activity (0:15)

:bar_chart: Run a comprehension check poll before reviewing the activity. 

This activity had students setup a firewall in front of their VNet to block all network traffic. The main goal of this activity is to get the Security Group created and practice creating a rule.

Point out that this rule is blocking **all** traffic bypassing the default rules that are already created and giving you complete control over all traffic on the VNet.

Use the following solution guide as a walkthrough:

- [Solution Guide: Security Groups](Activities/09_Security_Groups/Solved/README.md)



Explain that this rule will stop all traffic on this VNet, unless we set other rules to allow the traffic we want. We are doing this to practice writing firewall rules and gain complete control over the SG traffic.

In total, so far we have created a cloud network secured by a firewall.

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 10. Instructor Do: Virtual Computing (0:20)

In the last section of today's class, we will deploy three computers onto our network.

- Virtual computing is very common in today's internet infrastructure. In fact, many of the servers that students interact with on a daily basis are actually virtual servers.

- Virtual computers have all the same components that physical computers have, but, as expected, they are defined by software.

Explain that when you set up a virtual machine, you often have to decide how powerful you need the machine to be and choose each of the main hardware components.

These components include:

- **RAM (Random Access Memory)** is the amount of memory dedicated to running computer operations. The computer uses RAM to temporarily store data that it needs to access quickly.

    - When an application runs, it runs on RAM. The computer puts all of the needed bits of the application into RAM and accesses them to complete the operation of the application.

    - The more RAM is on a computer, the more applications a computer can run simultaneously.

    - When the computer is restarted, the RAM is cleared and the process of loading applications to RAM is restarted.

    - RAM is measured in increments of 8 bytes. Today's common values are 8, 16, and 32 GB on personal computers, and much more (128+ GB) on servers.

- **Storage (HDD/SSD)** is the part of the computer that stores data permanently. This is data that you do not lose when the computer is turned off.

    - HDD (hard disk drive) is a magnetic disk that spins inside a casing. The disk is read with a small magnet attached to an arm, similar to the way a record player reads a record.

    - SSD (solid state drive) is a more technologically advanced form of storage. Because HDDs have moving parts, they eventually wear out and stop working. An SSD has no moving parts and is based on the same technology that RAM uses.

        - SSDs are faster and more reliable than HDDs but also more expensive. For now, both options still exist, and which you choose will depend on the needs of the computer and your budget. SSDs are great for data that needs to be accessed quickly and HDDs are great when you have very large amounts of data that do not need to be accessed often or quickly.

    - For virtual servers, long-term storage is essentially a database that the server or OS needs to read and write to.

        - For example: Information for user logins is stored in one database on either an HDD or an SSD, and the operating system is stored on a different HDD or SSD, depending on how the machine is set up.

        - Long-term storage is measured in gigabytes and terabytes.

- **Disks** attached to a VM fall into two general categories:

    1. OS disks contain the operating system, kernel, and everything required for the VM to function.

    2. Data disks contain data that the VM doesn't need in order to run, but which users need in order to do their jobs. This might include:

        - Virtual machine images, in the case of Azure classroom labs.

        - Text data, if you're using a cloud VM to do "normal work."

        - Forensic disk images, if you're using a cloud VM for investigative duties.

        - Audio, images, and video data, if you're using the machine to perform heavy-duty graphical processing, such as speech or facial recognition.

- Explain that cloud providers allow you to choose different kinds of disks, depending on your needs:

    - As mentioned above, you can use a simple HDD if all you need is persistent storage of basic information, such as text, spreadsheets, or forensic disk images.

    - Or you can choose a premium SSD if you need to be able to quickly run memory-intensive applications, such as FTK or Autopsy.

- The cloud provides users a ton of flexibility and choice, but some options are far more expensive than others. What you choose should depend on your specific needs.

    - It is affordable to use the cloud to experiment with high-performing hardware for short periods of time.

    - Threat intelligence professionals, for instance, often use powerful GPU-driven machines for machine learning and computationally intensive data analysis. This is because it's much cheaper to use these machines for short periods of time on the cloud than to purchase and maintain them.

    - However, premium storage and top-of-the-line machines are just as expensive for cloud providers to own and maintain as they would be for an individual or organization. Using them without first establishing cost controls can quickly result in massive expenses.

- **CPU (Central Processing Unit)** is like the brain of the computer. It's the part that actually computes all the ones and zeros. The CPU takes code and data out of the long-term storage, loads it into RAM, and performs the computations specified by an application.

    - When you are waiting for a computer to complete a task, such as installing software or copying data from one location to another, you are waiting for the CPU to complete the necessary computations.

    - The speed of a CPU is measured in hertz, which is the measurement of how many bits can be processed from a zero to a one per second. Today's CPUs are measured in gigahertz.

Explain that a virtual computer has a software version of these components. When we create a virtual computer, we define the "hardware," such as the amount of RAM, the storage space, and the CPU. Once it is defined, we install an operating system and use the VM as if it were a normal computer.

Point out that the physical servers located inside data centers have enormous amounts of RAM, storage space, and CPU power, so they can run many virtual computers at the same time. One physical server can easily run more than ten virtual machines, depending on the resources assigned to each VM. Virtual machines can even run other virtual machines.

Emphasize that, before working with devices on the cloud, we must **always** set budget limits and cost-control policies. Otherwise, we can accidentally exceed our employer's budgets.

- Azure provides cost-control tools as a free service, which students are encouraged to study before managing live cloud deployments. We will not be using such expensive tools in class as it falls outside the scope of the course. However, they offer crucial functionality for managing live deployments on the job.

Explain that in our next activity, we will create a new VM and add it to our network.

Before we start, we'll cover a few key components of the VM creation process.

- Navigate to your Azure portal, search for "Virtual" and select **Virtual machines**.

- Click **+ Create** to create a new VM.

    ![](../1/Images/VM/CreateVM-b.png)

- Point out the tabs across the top of the VM creation page. Today, we'll focus on the **Basics**, **Disks**, **Networking**, and **Review + Create** tabs. Don't worry about the **Management**, **Advanced**, and **Tags** tabs.

    ![](../1/Images/VM_admin/VM_basics.png)

- Name this VM "Jump-Box-Provisioner."

    - Explain to students that giving their VMs descriptive names will help them stay organized.

---

#### Regions and VM Availability

By default, Azure should populate a VM and Region. Be sure to select the same Region you have chosen for the previous resources.

![](Images/VMsetup.png)

Explain that under "Availability Options," we won't need redundancy for the jump box. This is because the jump box does not need to scale to handle a large number of connections&mdash;only one administrator will use it at a time.

Explain that the web servers, by contrast, must be designed to handle a large number of requests. This requires configuring them with an **Availability Set**, assigning each web server to that availability set, and selecting it for the web machines.

Explain that an Availability Set is a fault-tolerant group of VMs. An Availability Set consists of at least two VMs. Each must be located in the same region, but each of the two VMs is hosted in a **different** data center. Different data centers are called **Availability Zones**.

Explain that this ensures that, if one of the VMs in the availability set goes down, the other is (nearly) guaranteed to remain up. Even if an entire data center goes down, the redundant machine in the other Availability Zone will remain running.

Summarize by explaining that an **Availability Set** is a group of VMs, where each VM is in a different **Availability Zone**. If one of the Availability Zones goes down, the VM in the other zones pick up the workload.

Explain that students will setup one machine (a jump box) that does not need an Availability Set assigned to it. However, **all** of the web VMs that are created **must** be assigned to the same Availability Set so they can later be placed behind a load balancer.

**Note:** When selecting an image, choose `Ubuntu Server 20.04 LTS -x64 Gen2`.

**Note:** Azure limits free tier users to only four vCPUs per Region. Notice that the default machine will normally have 2 vCPUs and 8 GB of memory. For this jump box, the machine size should be changed to a smaller machine to conserve resources.

Click on "See all sizes."

![](Images/regions-avail/VM-Choose-Screen.png)

If possible, choose a machine that has 1 vCPU and 1 GB of Memory (B1s), but the least expensive option available will be sufficient.

![](Images/VM/region3.png)



#### SSH setup
Remind the students that accessing a server with SSH using a password is inherently weak: many programs can brute force an SSH password. Instead, we want to practice setting up secure systems from the beginning, so we will use an SSH key pair to access our new machine.

- Azure has a section on the Basics page where we can insert a public key and create an administrator name for our SSH access.

- First, we have to create a key.

We'll do this on the command line using the `ssh-keygen -t rsa` command.

:warning: **Heads Up:** Windows users should be running these commands in GitBash.

- Open a terminal and run `ssh-keygen -t rsa`.

- We will be prompted to save the SSH key into the default directory `~/.ssh/id_rsa`. DO NOT CHANGE THIS LOCATION. Press the Enter key.

- We will be prompted to enter a password for our new SSH key.

	- DO NOT ENTER A PASSWORD. Press the enter key twice to enter a blank password.

- Emphasize that students should not change the name or location of this key and they should not enter a password. They only need to use the default values and hit enter to accept them. If they set a password or change the location, it can cause issues later on in the week when we setup automation.

- Point out that the path to the key is displayed in the first line: `Enter file in which to save the key (/Users/cyber/.ssh/id_rsa)` as long as it isn't changed. In this case, the keys are saved in `/Users/cyber/.ssh/id_rsa` and `/Users/cyber/.ssh/id_rsa.pub`.

- Your output should be similar to the below:

    ```bash
    $ ssh-keygen -t rsa
    Generating public/private rsa key pair.
    Enter file in which to save the key (/Users/cyber/.ssh/id_rsa): <hit enter>
    Enter passphrase (empty for no passphrase): <hit enter>
    Enter same passphrase again: <hit enter>
    Your identification has been saved in id_rsa.
    Your public key has been saved in id_rsa.pub.
    The key fingerprint is:
    SHA256:r3aBFU50/5iQbbzhqXY+fOIfivRFdMFt37AvLJifC/0 cyber@2Us-MacBook-Pro.local
    The randomart image is:
    +---[RSA 2048]----+
    |         .. . ...|
    |          o. =..+|
    |         o .o *=+|
    |          o  +oB+|
    |        So o .*o.|
    |        ..+...+ .|
    |          o+++.+ |
    |        ..oo=+* o|
    |       ... ..=E=.|
    +----[SHA256]-----+
    ```

Explain that all SSH keys are stored in the user home folder under a hidden `.ssh` directory. Inside this directory, we can see our private key named `id_rsa`, which should never be shared. We can also see a public key named `id_rsa.pub`, which we can place on servers that we want to access using this key.

- Run `cat ~/.ssh/id_rsa.pub` to show our `id_rsa.pub` key:

    ```bash
    $ cat ~/.ssh/id_rsa.pub

    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDGG6dBJ6ibhgM09U+kn/5NE7cGc4CNHWXein0f+MciKElDalf76nVgFvJQEIImMhAGrtRRJDAd6itlPyBpurSyNOByU6LX7Gl6DfGQKzQns6+n9BheiVLLY9dtodp8oAXdVEGles5EslflPrTrjijVZa9lxGe34DtrjijExWM6hBb0KvwlkU4worPblINx+ghDv+3pdrkUXMsQAht/fLdtP/EBwgSXKYCu/
    ```

- Copy the SSH key string and paste it into the Administrator Account section on the Basics page for the VM in Azure.

    -**IMPORTANT:** Make sure you copy the entire SSH key!

    - For `SSH public key source`, select `Use existing public key` from the drop down.

- The username can be any name, but it must be something the students will not forget. The SSH public key must be copied from the machine.

- This is all we need to do to create an administrator account on the machine that will have SSH access.

    ![](../1/Images/VM_admin/VM_admin_acct-b.png)

Pause and ask if there are any questions here before moving on.

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 11. Student Do: Virtual Computing (0:20)

Explain the following to students:

- In our previous activities, we set up a secure VNet inside a resource group for the Red Team.

- In this activity, you will launch three new virtual machines to be used throughout the cloud portion of the course.

- To keep your connections to these machines secure, you want to only connect using SSH keys.

- You are tasked with setting up three new Ubuntu VMs inside the Red Team resource group to be used throughout the cloud section of the course.

	- A jump box and two web servers.

:globe_with_meridians: Students should stay in the same **breakout room** groups as the previous activity.

Send students the following file:

- [Activity File: Virtual Computing](Activities/12_Virtual_Computing/Unsolved/README.md)

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

### 12. Instructor Review: Virtual Computing Activity (0:10)

:bar_chart: Run a comprehension check poll before reviewing the activity. 

This activity has students set up their first three virtual machines inside their cloud network, protected by their network security group. They will use one of these machines as a jump box to access their cloud network and the other machines will be web servers.

Use the following file to guide your walkthrough:

- [Solution Guide: Virtual Networking](Activities/12_Virtual_Computing/Solved/README.md)


#### Summary

Students should now have a VNet that holds their jump box and two web machines protected by a firewall.

Let the students know that if they did not configure the public IP of the jump box to be **static**, it may change when they stop and restart it. This is ok and will not hinder any activities. They can obtain the IP address from the VM details page.

If the IP resets, they will see a message like this:

![](Images/Avail_Set/Ip-reset.png)

Even though we have added an SSH key to the VMs, we currently cannot connect to them. Emphasize that this is intentional: the NSG that students implemented earlier prevents all traffic from reaching the machines.

Therefore, the SSH key has no effect until the NSG is updated to allow inbound SSH connections.

Emphasize that this approach is an important best practice:

- We created the network and blocked all traffic before placing any VMs inside of it.

    - This ensures that it is truly impossible for an attacker to gain access during the configuration process.

- Then, we added an SSH key through secure methods, ensuring that only the user with the correct private key (you) will be able to connect to the machine.

    - Still, this private key is essentially useless until the NSG is updated to allow SSH traffic.

    - This further protects the machines on the network by ensuring they can't be accessed by the private key owner or any attacker who intercepted it, until the cloud administrator explicitly allows such access.

- In the next class, we'll update the NSG, following the principle of least privilege, to allow only inbound SSH traffic.

    - We will configure the NSG so it only allows one IP address to open connections. This will ensure that if an attacker steals the key remotely, they will only be able to connect to the VM if they **also** successfully compromise your development machine.

Explain that during the next class, we will continue to build out our cloud infrastructure to allow SSH access to our VNet via the jump box, provision containers, and more.

Remind students to stop all the VMs in their Azure account.

Ask if there are any questions about creating their first VM.

---

|:warning: **Checkpoint** :warning:|
|:-:|
| Use the [Daily Checklist](../Resources/Checklist.md) to verify that students are ready for the next class session. |

The critical items that need to be complete at the end of Day 1 are listed below:

- [ ] Created three web VMs: one jump box and two web VMs.

- [ ] Configured all three VMs with the same SSH key.

- [ ] SSH key has no password.

- [ ] Web VMs are created using the same availability set.

- [ ] Web VMs should have 2 GB of RAM.

- [ ] Jump box VM only needs 1 GB.

- [ ] All 3 VMs should only have 1 vCPU.

- [ ] All VMs are using the same security group and VNet.

Completion of these steps is **required** to proceed to the activities in the next class.

[<- Back to Module Contents](LessonPlan.md#module-day-1-contents)

---

© 2023 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.
