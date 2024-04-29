## Activity File: The Final Report

Just as in a real-world scenario, you will complete a final report to present your findings. You will work with your team to fill out the report.

 - You will submit the final report as your Challenge deliverable for this week. Everything your group has completed in class should be included. What you do not finish today can be continued at home. 
 
 - Use the [Final Case Report](https://docs.google.com/document/d/1wUvR5F-KBDbazg4-upPxBuSPORWqMmAaYv5RXm0dWzM/edit) Google Doc template to complete your report. Before beginning, make a copy of this template. To allow everyone in the group to access and work on the document at the same time, give every student editing access. (**Note:** While you should complete this report as a group, each student must submit their own copy of the report for this week's Challenge deliverable.)

  - Use the following resource to help guide your work:

     - [iPhone Forensics - Important Files and Databases](https://docs.google.com/document/d/1MN4aTz8qsPh1SayR9LWKVNIGndLcSVrg1SPHj4NtVLs/edit) 

### Instructions

You've examined and documented quite a bit of information from the iPhone image file. Now, you will use that documentation to build a final report. 

1. Before you complete your report, there is still some additional evidence to analyze. Since the internal investigators knew that Peter was close with Rosie, they collected Rosie's phone for your to analyze to determine if she in fact a co-conspirator.

2. Within Autopsy, on the top left, select the option "Add Data Source".

3. Add Rosie's iphone image using the same process as Peter.

4. Analyze the following evidence on Rosie's phone.

5. **View SMS messages** 
   - Are there any additional sms messages which correlate Rosie to the crime?

6. **Export attachments on SMS messages**
   - Expand the attachments folder under `sms` until you find a .HEIC file and a .MOV file
   - Export those 2 files

7.  **Analyze the .MOV file**
   - Access the .MOV file from your terminal, and run the following command `xdg-open   <filename>.MOV`.
   - Did this file contain any evidence?

8.  **Determine Geographic Data on the HEIC file**
   - Note: HEIC is Apple’s proprietary file type for photos.
   - Open a webbrowser within your Kali Terminal.
   - Browse to https://onlineexifviewer.com/ and upload the .HEIC file.
   - Analyze the data and determine the location where the photo was taken.
     
### Bonus - Determining the Ring Leader of the Operation

Throughout the week, there were mentions that there was a ring leader secretly behind the operations of this crime. Additionally, there are rumors this person is called `Mr X.`  Can you determine who is Mr X?
  - **Hint** - You may have to listen to this evidence on your local computer as Kali doesn't always play sound.

----

&copy; 2023 edX Boot Camps LLC. Confidential and Proprietary.   All Rights Reserved.
