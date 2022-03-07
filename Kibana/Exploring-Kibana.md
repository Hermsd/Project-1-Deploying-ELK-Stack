## Activity File: Exploring Kibana

* You are a DevOps professional and have set up monitoring for one of your web servers. You are collecting all sorts of web log data and it is your job to review the data regularly to make sure everything is running smoothly. 

* Today, you notice something strange in the logs and you want to take a closer look.

* Your task: Explore the web server logs to see if there's anything unusual. Specifically, you will:

:warning: **Heads Up**: These sample logs are specific to the time you view them. As such, your answers will be different from the answers provided in the solution file. 

---

### Instructions

1. Add the sample web log data to Kibana.
 ![Kibana_Add_Weblogs](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana_Add_Weblogs.png)
2. Answer the following questions:

    - In the last 7 days, how many unique visitors were located in India?
      - Answer: In the last 7 days 248 unique visitors were located in India. 
    ![Kibana_Visitors_from_IN_Last 7 days](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana_Visitors_from_IN_Last%207%20days.png)

    - In the last 24 hours, of the visitors from China, how many were using Mac OSX?
      - Answer: In the last 24 hours, of the visitors from China, 8 unique visitors were using Mac OSX.
      ![Kibana-Visitors in CH using Mac OSX-Last 24hrs](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-Visitors%20in%20CH%20using%20Mac%20OSX-Last%2024hrs.png)

    - In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?
      - Answer: In the last 2 days .05% (18 visitors) of visitors received 404 errors and .04% (13 visitors) received 503 errors. 
      ![Kibana-Last 2 days-404 errors](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-Last%202%20days-404%20errors.png)
      ![Kibana-Last 2 days-503 errors](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-Last%202%20days-503%20errors.png)
    - In the last 7 days, what country produced the majority of the traffic on the website?
      - Answer: In the last 7 days China produced the majority of the traffic on the website.
      ![Kibana-Last 7 days- Country with most traffic](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-Last%207%20days-%20Country%20with%20most%20traffic.png)
    - Of the traffic that's coming from that country, what time of day had the highest amount of activity?
      - Answer: Of the traffic that's coming from China, the time of day with the highest amount of activity was 3:00 PM. 
      ![Kibana-CH-Time of day with most amount of traffic](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-CH-Time%20of%20day%20with%20most%20amount%20of%20traffic.png)   
    - List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).
      - Answer: CSS files (Cascading Style Sheets), which are files taht describe how HTML elements are displayed. DEB files, which are debbian software pakcage files and are used mainly in Unix-based operating systems. GZ files are compressed archives that are created by the standard GNU compression algorithm and are the most common archive file formats on Unix and Linux systems. RPM files, which are Red Hat package manager files that are used to store installation packages on Linux operating systems. Zip files, which is a common file format used to compress one or more files together in a single location. 
3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.
     - Locate the time frame in the last 7 days with the most amount of bytes (activity).
     - In your own words, is there anything that seems potentially strange about this activity?
       - In the last 7 days the most amount of activity was on 02/27/2022 at 9:00PM and on 03/03/2022 at 3:00PM. The fact that on both those days is that on 02/27/2022 at 9:00PM there were only 3 visitors and on 03/03/2022 there were only 4 visitors, however despite having the lowest amount of visitors in the last 7 days, both of those days account for largest amount of activity.
       ![Kibana-Last 7 days with the most amount of bytes](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-Last%207%20days%20with%20the%20most%20amount%20of%20bytes.png)

4. Filter the data by this event.
     - What is the timestamp for this event?
     
     - What kind of file was downloaded?
     ![Kibana- kind of file downloaded](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-%20kind%20of%20file%20downloaded.png)
     
     - From what country did this activity originate?
       - United States of America
       - ![Kibana-what country did this activity originate(https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-what%20country%20did%20this%20activity%20originate.png)
     
     - What HTTP response codes were encountered by this visitor?
       - Answer: Response code 200
       
       ![Kibana-Src IP and more info](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/ca7e30dfa257a548156b949492d9cb13ec574dea/Images/Kibana-Src%20IP%20and%20more%20info.png)

5. Switch to the Kibana Discover page to see more details about this activity.
     - What is the source IP address of this activity?
     - What are the geo coordinates of this activity?
     - What OS was the source machine running?
     - What is the full URL that was accessed?
       - Answer: /kibana/kibana-6.3.2-linux-x86_64.tar.gz
     - From what website did the visitor's traffic originate?
       - Answer: artifacts.elastic.co 

6. Finish your investigation with a short overview of your insights. 

     - What do you think the user was doing?
     - Was the file they downloaded malicious? If not, what is the file used for?
     - Is there anything that seems suspicious about this activity?
     - Is any of the traffic you inspected potentially outside of compliance guidlines?

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
