## Module 19 Challenge Submission File
**Let’s Go Splunking!**

**Step 1: The Need for Speed**

Background: As the worldwide leader of importing and exporting, Vandalay Industries has been the target of many adversaries attempting to disrupt their online business. Recently, Vandalay has been experiencing DDOS attacks against their web servers.

Not only were Vandalay web servers taken offline by a DDOS attack, but upload and download speed were also significantly impacted after the outage. Your networking team provided results of a network speed run around the time of the latest DDOS attack.

Your Task: Create a report to determine the impact of the DDOS attack on upload and download speed. Create an additional field to calculate the ratio of the upload speed to the download speed. To do so, complete the following steps:

```
First, upload the server_speedtest.csv file to Splunk.
```

Using the eval command, create a field called ratio that shows the ratio between the upload and download speeds.
![1](https://user-images.githubusercontent.com/113793122/219987532-f13ace85-0a5f-4cbc-84bb-7bd09a199e13.png)
![2](https://user-images.githubusercontent.com/113793122/219987583-6bdf0eed-dd76-4305-9913-60ba4a795d0d.png)

Create a report using Splunk's table command to display the following fields in a statistics report:

-_time

-IP_ADDRESS

-DOWNLOAD_MEGABITS

-UPLOAD_MEGABITS

-ratio

1. Based on the report you created, what is the approximate date and time of the
    attack?
```
02/23/2020 at 2:30 PM.
```

2. How long did it take your systems to recover?
```
11:30 PM or 9 hours until speeds recovered.
```
3. Provide a screenshot of your report:
![3](https://user-images.githubusercontent.com/113793122/219987866-6dea6575-a9fd-4347-8ff9-9a60ecb1753e.png)

**Step 2: Are We Vulnerable?**

Background: Due to the frequency of attacks, your manager needs to be sure that sensitive customer data on their servers is not vulnerable. Since Vandalay uses Nessus vulnerability scanners, you have pulled the last 24 hours of scans to see if there are any critical vulnerabilities.

Your Task: Create a report determining how many critical vulnerabilities exist on the customer data server. Then, build an alert to notify your team if a critical vulnerability reappears on this server. To do so, complete the following steps:

```
First, upload the nessus_logs.csv file to Splunk.
```
Create a report that shows the count of critical vulnerabilities from the customer database server.

The database server IP is 10.11.36.23.
The field that identifies the level of vulnerabilities is severity.

Provide a screenshot of your report:
![4](https://user-images.githubusercontent.com/113793122/219988179-5ff4077e-6350-4bcf-b783-f9a16091562a.png)
![5](https://user-images.githubusercontent.com/113793122/219988182-59d6ea31-4e41-48ae-87e7-36c003b83a08.png)

Build an alert that monitors every day to see if this server has any critical vulnerabilities. If a vulnerability exists, have an alert emailed to soc@vandalay.com.

Provide a screenshot showing that the alert has been created:
![6](https://user-images.githubusercontent.com/113793122/219988345-e1df18cd-e50a-4721-829b-b67cfd3284d8.png)


**Step 3: Drawing the (Base)line**
Background: A Vandaly server is also experiencing brute force attacks into their administrator account. Management would like you to set up monitoring to notify the SOC team if a brute force attack occurs again.

Your Task: Analyze administrator logs that document a brute force attack. Then, create a baseline of the ordinary amount of administrator bad logins and determine a threshold to indicate if a brute force attack is occurring. To do so, complete the following steps:

```
First, upload the Administrator_logs.csv file to Splunk.
```

1. When did the brute force attack occur?
![7](https://user-images.githubusercontent.com/113793122/219988658-a8961244-05d5-466e-a58b-8f833554bb22.png)

```
02/21/2020 from 9AM - 1PM.
```
![8](https://user-images.githubusercontent.com/113793122/219988700-2cbf84ab-83fd-405e-8ae3-e6d65ddca8d5.png)

2. Determine a baseline of normal activity and a threshold that would alert if a brute
force attack is occurring: 
![9](https://user-images.githubusercontent.com/113793122/219988708-53f08712-2ec5-4875-9f81-84757a1861a5.png)
![10](https://user-images.githubusercontent.com/113793122/219988711-615810b1-2cf6-4e7c-b8b6-65a4780247fa.png)

```
Using this data, we can determine that less than 50 an hour or less than 500
a day would work as a baseline. Since the response needs to be swift, we
will use the hourly baseline to set up our alert.
```
3. Design an alert to check the threshold every hour and email the SOC team at SOC@vandalay.com if triggered. Provide a screenshot showing that the alert has been created:
![11](https://user-images.githubusercontent.com/113793122/219988723-f81ea5bd-c33b-4d52-bb0b-f04bed6643cc.png)

© 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.



