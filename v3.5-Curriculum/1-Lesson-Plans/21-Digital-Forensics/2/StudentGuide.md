## 21.2 Student Guide: Autopsy and iPhone Forensics
 
### Overview
 
In the second day of our introduction to digital forensics, students will use Autopsy to analyze an iPhone image. 

### Class Objectives
 
By the end of the lesson, you will be able to:
 
- Identify the methods used in smartphone forensics investigations.
- Navigate the database and file structure of the iPhone's flash drive.
- Locate identifiable evidence on the iPhone in order to establish ownership.
- Use Autopsy to view and tag evidence in an iPhone image.
- Extract image content for offline viewing in other applications (logs, text, pictures, video, audio).

### Lab Environment

<details><summary>Lab Details</summary>
<br>

In this module, you will use the Forensics lab environment located in Windows Azure Lab Services. RDP into the **Windows RDP host machine** using the following credentials:

  - Username: `azadmin`
  - Password: `p@ssw0rdp@ssw0rd`

Open Hyper-V Manager to access the nested machine:

**Kali Forensics machine:**
  - Username: `root`
  - Password: `toor`

**Today’s class**

You will use the following machine:
- Kali Forensics machine

</details>  

### Module Day 2 Contents

- [x] [01. Welcome and Overview](#01-welcome-and-overview)
- [x] [02. Activity: Mobile Evidence Analysis](#02-activity-mobile-evidence-analysis)
- [x] [03. Activity Review: Mobile Evidence Analysis](#03-activity-review-mobile-evidence-analysis)
- [x] [04. Break](#04-break)
- [x] [05. Tagging Evidence](#05-tagging-evidence)
- [x] [06. Activity: Tagging Evidence](#06-activity-tagging-evidence)
- [x] [07. Activity Review: Tagging Evidence Activity](#07-activity-review-tagging-evidence)
- [x] [08. Extracting Data for Offline Analysis](#08-extracting-data-for-offline-analysis)
- [x] [09. Activity: Extracting Data for Offline Analysis](#09-activity-extracting-data-for-offline-analysis)
- [x] [10. Activity Review: Extracting Data for Offline Analysis Activity](#10-activity-review-extracting-data-for-offline-analysis)
- [x] [11. Wrap-Up](#11-wrap-up)


### Slideshow
 
- Slides for today's lesson can be found on Google Drive here: [21.2 Slides](https://docs.google.com/presentation/d/1hQVAMQ5c5cb99iPAzuunVRBSANDMeHQQAum3ic4NHkg/edit).

---
 
### 01. Welcome and Overview 
 
Welcome to the second day of the digital forensics module.
 
In the last session, we covered:
 
- Basic principles of digital forensics methodologies.
- Various skill sets required for a career in digital forensics.
- The proper approach to collecting, preserving, analyzing, and reporting forensic evidence.
- How to conduct a preliminary review for a forensic case.
- How to preserve and document evidence using Autopsy.

Today we will focus on smartphone forensics and continue the Pure Gold Credit Union case by using Autopsy to view and tag evidence on an iPhone image. 
   
- You will also learn how to perform image searches without using the directory tree. Instead, they will use the following:

  - File Search by Attributes and Keyword Search.

  - Displaying text and file metadata. 

#### Where's the Data? File System and Data Storage
 
In this section, you will provide a high-level overview of the file structure and major directories of an iPhone.
  
An important aspect of mobile forensics is understanding where data is stored, how to access the data, and what data can be recovered.
 
- An iPhone does not have external storage. All data is stored in **flash memory** on the device.
 
  - Remember: Flash memory retains data without any external power and is used in SSDs and smartphones.

  - Flash memory on an iPhone exists until it is overwritten.
 
- Explain that data is first imaged using a **bit-level copy**. 

  - In an iPhone, this will recover deleted messages as well as GPS coordinates and cell tower locations.
 
- iPhones allow users to back up their data to the cloud, which can be another source of data in an investigation, especially when the device is not available.
 
#### Important Directories/Databases and Files
 
Now we'll look at directories, databases, and files in the iPhone image that students will investigate for evidence using Autopsy for the Pure Gold Credit Union case.
  
Since iPhone's iOS is based on Unix, the directory structure should generally be familiar. 
 
- Most information is in human-readable format within the Autopsy application.
 
- The iPhone stores user data in **SQL databases** and other files.

  - SQL stands for Structured Query Language and is a language used to create, read, update, and delete (commonly abbreviated as "CRUD") database files.
  
- These are the main databases that applications such as mail, SMS, calendar, and the address book use (***Note: Your Iphone image has been reduced in size for this class, and will not contain all of the below files***)
 
  - `AddressBook.sqlitedb` contains contact information and personal data like name, email address, etc.

  - `AddressBookImages.sqlitedb` contains images associated with saved contacts.

  - `Calendar.sqlitedb` contains calendar details and events information.

  - `Call_History.db` contains incoming and outgoing call logs, including phone numbers and time stamps.

  - `sms.db` contains text and multimedia messages along with their time stamps.

  - `voicemail.db` contains voicemail messages.

  - `Safari/Bookmarks.db` contains saved URL addresses.

  - `locationd` contains the geolocation data.
    
  - `Safari/History.db` contains internet browsing history.
 
 iPhones also have data stored in `plists`, or `property lists`. A `plist` typically stores configuration information.
 
  - `activation_record.plist` Model information - ICCID, IMEI, Serial Number
    
  - `data_ark.plist` File used for backup and restore, contains assortment of data including Host Name and OS Version

  - `Maps/Bookmarks.plist` contains maps and bookmarks.

#### Demonstration: Evidence Analysis with Autopsy

This demo will walk through various methods for obtaining digital evidence related to the Pure Gold Credit Union case:
 
1. Start the Kali VM.
 
2. Open a terminal and navigate to: `/root/autopsy-files/autopsy-4.10.0/bin`.
 
3. Launch Autopsy: 

   - Run `./autopsy`. 
 
4. Open the case created in the last class: 
 
   - Case name: `Pure-Gold-Credit-Union`
   - Case number: `1EZ215-P`
 
     ![An image of the "Welcome" window with the "Open Recent Case" option highlighted.](Images/a-images/1.png)

   - Point out the Autopsy files end with the .aut file extension.
 
     ![An image showing the file name ending with the .aut file extension.](Images/forensic2_1.png)
 
5. In the tree, you will see `Peter Iphone`, which is the iPhone image file.
  
   -  We'll spend most of our time exploring evidence in this directory tree.
 
 ![An image showing the file name ending with the .aut file extension.](Images/forensic2_2.png)

#### Examine Browsing History
 
This example shows how to navigate an evidence file without using the directory tree. 

Clicking through directory trees is a long and cumbersome process. Instead, Autopsy has a built-in feature that allows for quicker and more thorough searches.

You will need the file name or file extension to perform a search.
 
  1. From the **Keyword Search** menu, then select **Exact Match**.
  
  2. Type `History.db`.
  
  3. Click the **Search** button.
 
  4. Select `History.db` at the top of the **File Search Results 1** window.
 
      - The `History.db` stores iPhone browsing history from the Safari web browser.
 
  ![An image showing the "History.plist" file.](Images/forensic2_17.png)
 
5. Select the **Indexed Text** tab in the **Data Content** pane.
 
   - Here you will see a list of searches that the owner of the iPhone performed.
 
    ![An image showing the browsing history in the Indexed Text tab.](Images/forensic2_18.png)
 
Review how to view the text using the iPhone image file.
 
#### Autopsy Main Panes
 
* Review the main panes in the user interface: **Directory Tree**, **Listing**, and **Data Content**.
 
 ![An image showing the Directory Tree, Listing, and Data Content panes.](Images/forensic2_13.png)
 
#### File Metadata 
 
Next, we'll look at the file metadata. We need this information for our evidence reporting.
 
- Select the **File Metadata** tab in the **Data Content** pane.
 
- Point out the importance of capturing file metadata using the **File Metadata** tab in the **Data Content** pane. Here we can find lots of information relevant to our investigation, including:

    - Image name
    - MIME type
    - File size
    - Hash
 
  ![An image showing the "File Metadata" tab.](Images/forensic2_14.png)
 
#### Displaying Text
 
The **Indexed Text** tab is used to display human-readable text.
 
- This example displays the contents of one of Peter's emails.
- The path to the file is displayed in the **Listing** pane.
 
   ![The Indexed Text tab shows the contents of one of Peter's emails.](Images/forensic2_15.png)
 
#### File Search
  
- If you know the file name you're looking for, performing searches using the **File Search by Attributes** method is much faster than using the directory tree.
 
  - To get there, click **Tools** in the top menu bar and select **File Search by Attributes**.
 
  - Next to the **Keyword Search**, the **File Search by Attributes** function is a highly efficient method for searching through file images.
 
    ![An image showing the File Search by Attributes window.](Images/forensic2_16.png)
 
[<- Back to Module Contents](#module-day-2-contents)

---

### 02. Activity: Mobile Evidence Analysis
 
Note the following:
 
- In this activity, you will play the role of a digital forensics investigator.
 
- You are tasked with analyzing evidence and creating a spreadsheet that profiles the details of Peter's iPhone.
 
- This will serve as your preliminary documentation for the remaining activities.
 
- For this activity, you will practice your research skills using Autopsy's File Search by Attributes and Keyword Search functions.
 
- Refer to the following file for information on the main databases and files covered in the demonstration:
  - [iPhone Forensic Image: Important Databases and Files](https://docs.google.com/document/d/1MN4aTz8qsPh1SayR9LWKVNIGndLcSVrg1SPHj4NtVLs/edit)
 
- Fill out your findings in the following worksheet: 
  - [iPhone Details Worksheet](https://docs.google.com/document/d/1JWb0TA0Lw0AD4MM9fvbaVQAgCvA_Fkz7cgWocBTJot0/edit)
  - You will need to make yourself a copy in order to edit it.  
 
If you wish, you may work in small groups of two or three.  

Use the following activity file: 

- [Activity File: Mobile Evidence Analysis](Activities/02_Mobile_Evidence/Unsolved/README.md)
 
[<- Back to Module Contents](#module-day-2-contents)

---

### 03. Activity Review: Mobile Evidence Analysis
  
- [Solution Guide: Mobile Evidence Analysis](Activities/02_Mobile_Evidence/Solved/README.md)
 
[<- Back to Module Contents](#module-day-2-contents)

---

### 04. Break 
 
[<- Back to Module Contents](#module-day-2-contents)

---

### 05. Tagging Evidence 
 
We'll continue our investigation by using Autopsy to tag evidence.

- **Evidence tagging** is the process of bookmarking evidence to keep critical details organized and easily accessible.

- We'll be tagging evidence throughout our investigation to help categorize and organize all digital evidence pertinent to the Pure Gold Credit Union case.
 
Autopsy includes a built-in feature to tag evidence, which allows investigators to easily locate evidence contained within Autopsy.
 
- Autopsy contains a set of predefined tags that include:
 
  - Follow up
  - Notable item
  - Child exploitation
  - Uncategorized
  - Non-pertinent
 
- Custom tags can be created and added to the tag database.
 
  - Having the ability to create custom tags provides forensic investigators with the capability to categorize and organize their evidence image file database according to specific case criteria. 
  
  - This process makes it easy for team members to continue working on a file that was previously worked on by another investigator.
 
#### Demonstration: Evidence Tagging
 
Now we'll walk through how to tag and bookmark the SMS database. The SMS database contains sent and received iPhone messages.
  
First, we need to locate the `sms.db` file in the iPhone image using Files Search by Attributes.
 
  - Click on **Tools** on the top menu bar.
  - Select **Files Search by Attributes**.

![An image showing the file name ending with the .aut file extension.](Images/forensic2_3.png)

   - Check the **Name** box and enter `sms.db`. Then press Enter or click **Search**.
 
 ![An image showing the file name ending with the .aut file extension.](Images/forensic2_4.png)
 
   - Click the `sms.db` entry in the **Listings** pane to highlight it.
 
   - Right-click and select **Add Tag** > **Bookmark**. The line containing the `sms.db` entry will turn yellow in the Listing pane.
 
      ![An image showing the options to "add File Tag" and "Bookmark" after right-clicking the sms.db entry.](Images/forensic2_5.png)
  
      ![An image highlighting the sms.db line is yellow after selecting "Bookmark" and the tags in the directory tree.](Images/a-images/8.png)
  
The bookmark entry can be found in the **Directory Tree** under **Tags** > **Bookmark** > **File Tags**.
 
#### Creating Custom Tags
 
Organizations use various tagging schemes depending on the case they are investigating. Therefore, having the ability to create custom tags allows forensic investigators to categorize evidence according to specific criteria.
 
- Next, we'll preview how to create a new tag in the database.
 
   - Right-click on `sms.db` and select **Add File Tag** > **New Tag**.

     ![An image showing the options to "add File Tag" and "New Tag" after right-clicking the sms.db file.](Images/a-images/9.png)
 
   - The **Create Tag** window is displayed.
   - Enter the name of the new tag and provide a description. Click **OK**.   
 
     ![The Create Tag window showing the "Tag Name" and "Description" fields.](Images/a-images/10.png)
  
- After you add your custom tag to the `sms.db` file, you will see the new tag entry in the directory tree under **Tags**.
 
 - The next time you go to select a tag, you will see your custom tag listed as a selection.
 
   ![An image showing the custom tag listed as a selection.](Images/a-images/11.png)
 
[<- Back to Module Contents](#module-day-2-contents)

---

### 06. Activity: Tagging Evidence
 
Note the following:
 
- In this activity, you will tag the major databases and files in the iPhone image file.
 
- Tagging allows you to quickly find data in the Autopsy iPhone image and document the evidence.
 
- You will create new tags for evidence that is relevant to the case, such as mail, address book, and SMS.
 
- Be sure to tag as much relevant information as possible. It will be used in later activities as you build your case.
 
Use the following files:

- [Activity File: Tagging Evidence](Activities/06_Tag_Evidence/README.md)
- [iPhone Forensic Image: Important Databases and Files](https://docs.google.com/document/d/1MN4aTz8qsPh1SayR9LWKVNIGndLcSVrg1SPHj4NtVLs/edit) 
    - Use this file to select the content to tag. You can also bookmark and tag other files of interest.

[<- Back to Module Contents](#module-day-2-contents)

---

### 07. Activity Review: Tagging Evidence
  
There is no solution file. As with so many files, your answers will vary greatly. 

[<- Back to Module Contents](#module-day-2-contents)

---

### 08. Extracting Data for Offline Analysis 
 
Although Autopsy facilitates viewing information in the application, investigators may want to extract individual files or entire directory trees for offline viewing within other applications. This is because:
 
- Not all data types can be rendered in Autopsy.
 
- Other tools can analyze video, photo, and audio files in more depth.
 
   - For example, photos may need to be enlarged, audio may need voice recognition, and video may need to be enhanced for facial recognition.
 
- Database information may easily be transferred to spreadsheets or Word documents where it can be manipulated for reports.
 
In this section, we will cover how to extract files and entire directories for offline viewing, where data can be parsed for specific information.
 
- **Offline viewing** refers to the process of viewing files outside of the main program&mdash;in this case, Autopsy.
 
- The iPhone image contains files and directories that can be viewed or rendered with other applications contained within the Linux OS.
 
- When using the Extract File(s) feature to extract a single file, an entire directory, or the entire image, it will be exported as a Linux directory.
 
#### Demonstration: Single File Export
 
Launch Autopsy and load the case file.
 
- Perform a Keyword Search and search for the `AddressBook.sqlitedb` file.
 
- In the **Listing** window, select the `AddressBook.sqlitedb` database, then right-click and select **Extract Files**.
 
   ![An image showing the "Extract Files" option after right-clicking the selected database.](Images/forensic2_8.png)
 
- By default, files are placed in the **Export** directory.
 
- Accept the default settings and click **Save**.
 
   ![An image showing the default settings and the "Save" button at the bottom-right.](Images/autopsy_extract_example-1.png)
 
- The **Export** directory is located in the `/root/casedata/Pure-Gold-Credit-Union` directory.
 
- Open a terminal and navigate to the export directory.
   - Run `cd /root/casedata/Pure-Gold-Credit-Union/Export/`.
 
- The `.db` database files require a database reader program such as SQLite DB Browser (pre-installed in Kali) that can view these files types.
   - Run `sqlitebrowser AddressBook.sqlitedb`.

- We can see the database schema of `AddressBook.sqlitedb` using SQLite DB Browser.

   ![An image showing the database schema.](Images/forensic2_9.png)

- We can see the contacts in the ABRecent table by going to **Browse Data** > **ABPerson**.

  ![An image showing the database schema.](Images/forensic2_9b.png)

- This provides us with valuable information, such as the contact's name and phone. However, fields like **date** and **property** are in formats designed for the iPhone's operating system.  

[<- Back to Module Contents](#module-day-2-contents)

---

### 09. Activity: Extracting Data for Offline Analysis
 
Note the following:
 
- In this activity, you continue in your role as a digital forensics investigator working on the Pure Gold Credit Union case.
 
- Your task is to create export files for offline examination.
 
- The investigative team will use your file exports to identify and confirm Peter's web searches.
 
Use the following:
 
- [Activity File: Extracting Data for Offline Analysis](Activities/09_Extracting_Data/Unsolved/README.md)
 
[<- Back to Module Contents](#module-day-2-contents)

---

### 10. Activity Review: Extracting Data for Offline Analysis
  
- [Solution Guide: Extracting Data for Offline Analysis](Activities/09_Extracting_Data/Solved/README.md)
 
[<- Back to Module Contents](#module-day-2-contents)

---

### 11. Wrap-Up 
 
Here are the key takeaways from today's class:
 
- As a forensic investigator, you will work as part of a team that consists of a large collaborative effort.
 
- It's critical, as forensic investigators, to understand how to use tools such as Autopsy and how to export data so other team members can perform offline analysis of evidence.
 
- Tagging evidence helps categorize and label evidence that has already been screened. 

- This eliminates double work and helps other investigative team members continue your work if you become unavailable.
 
In the next class, we will continue our investigation by analyzing email messages, SMS messages, and more in order to tie Peter to the case.
 
[<- Back to Module Contents](#module-day-2-contents)

---
 
&copy; 2023 edX Boot Camps LLC. Confidential and Proprietary.   All Rights Reserved.
