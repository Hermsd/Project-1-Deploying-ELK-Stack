## Activity File: Exploring Kibana

* You are a DevOps professional and have set up monitoring for one of your web servers. You are collecting all sorts of web log data and it is your job to review the data regularly to make sure everything is running smoothly. 

* Today, you notice something strange in the logs and you want to take a closer look.

* Your task: Explore the web server logs to see if there's anything unusual. Specifically, you will:

:warning: **Heads Up**: These sample logs are specific to the time you view them. As such, your answers will be different from the answers provided in the solution file. 

---

### Instructions

1. Add the sample web log data to Kibana.

2. Answer the following questions:

    - In the last 7 days, how many unique visitors were located in India?
      - Answer: In the last 7 days 248 unique visitors were located in India. 

    - In the last 24 hours, of the visitors from China, how many were using Mac OSX?
      - Answer: In the last 24 hours, of the visitors from China, 8 unique visitors were using Mac OSX.

    - In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?
      - Answer: In the last 2 days .05% (18 visitors) of visitors received 404 errors and .04% (13 visitors) received 503 errors. 
    - In the last 7 days, what country produced the majority of the traffic on the website?
      - Answer: In the last 7 days China produced the majority of the traffic on the website.
    - Of the traffic that's coming from that country, what time of day had the highest amount of activity?
      - Answer: Of the traffic that's coming from China, the time of day with the highest amount of activity was 3:00 PM.    
    - List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).
      - Answer: CSS files (Cascading Style Sheets), which are files taht describe how HTML elements are displayed. DEB files, which are debbian software pakcage files and are used mainly in Unix-based operating systems. GZ files are compressed archives that are created by the standard GNU compression algorithm and are the most common archive file formats on Unix and Linux systems. RPM files, which are Red Hat package manager files that are used to store installation packages on Linux operating systems. Zip files, which is a common file format used to compress one or more files together in a single location. 
3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.
     - Locate the time frame in the last 7 days with the most amount of bytes (activity).
     - In your own words, is there anything that seems potentially strange about this activity?
       - In the last 7 days the most amount of activity was on 02/27/2022 at 9:00PM and on 03/03/2022 at 3:00PM. The fact that on both those days is that on 02/27/2022 at 9:00PM there were only 3 visitors and on 03/03/2022 there were only 4 visitors, however despite having the lowest amount of visitors in the last 7 days, both of those days account for largest amount of activity.

4. Filter the data by this event.
     - What is the timestamp for this event?
     - What kind of file was downloaded?
     - From what country did this activity originate?
     - What HTTP response codes were encountered by this visitor?

5. Switch to the Kibana Discover page to see more details about this activity.
     - What is the source IP address of this activity?
     - What are the geo coordinates of this activity?
     - What OS was the source machine running?
     - What is the full URL that was accessed?
     - From what website did the visitor's traffic originate?

6. Finish your investigation with a short overview of your insights. 

     - What do you think the user was doing?
     - Was the file they downloaded malicious? If not, what is the file used for?
     - Is there anything that seems suspicious about this activity?
     - Is any of the traffic you inspected potentially outside of compliance guidlines?

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
