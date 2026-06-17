
####  CST8919 Lab 2 – Building a Web App with Threat Detection using Azure Monitor and KQL

- Course: CST8919 – DevOps Security
- Lab: Lab 2 – Threat Detection using Azure Monitor and KQL
- Student: Hesheng Yang
  
#####  Technologies Used

- Python 3.12
- Flask
- Azure App Service
- Azure Monitor
- Azure Log Analytics Workspace
- Kusto Query Language (KQL)
- Azure Monitor Alerts
- Visual Studio Code
- REST Client Extension


#### Project Architecture

```

User
↓

Flask Web App

↓

Application Logs

↓

Azure Monitor Diagnostic Settings

↓

Log Analytics Workspace

↓

KQL Query

↓

Azure Monitor Alert Rule

↓

Email Notification

```

#### Code
https://github.com/hycst/CST8919-Lab2/blob/main/app.py


##### KQL Query

```kusto
AppServiceConsoleLogs
| where ResultDescription contains "LOGIN_FAILED"
| project TimeGenerated, ResultDescription
| order by TimeGenerated desc
```

#### Explanation for th KQU Query:

- Reads application console logs
- Filters failed login attempts
- Displays the timestamp and log message
- Sorts results from newest to oldest

---

##### App running:
<img width="2983" height="856" alt="image" src="https://github.com/user-attachments/assets/fc0c8f06-ec47-4db5-925e-dfae55da8aa7" />

<img width="527" height="160" alt="image" src="https://github.com/user-attachments/assets/fa0e2ded-8b12-41d3-90fe-5bdb26d0a209" />

##### Successful log and failed login:
<img width="1076" height="397" alt="image" src="https://github.com/user-attachments/assets/8e83e0cc-c9a9-43b8-b0ee-c4e87167e41b" />


<img width="954" height="484" alt="image" src="https://github.com/user-attachments/assets/ca2bf5d7-df2a-4a89-af76-d7b462bad36c" />

##### diagnostic-settings
<img width="2424" height="1405" alt="image" src="https://github.com/user-attachments/assets/67db5dcd-0de2-4443-be53-53c3326459c8" />


##### Create Alert rule:
<img width="2986" height="1528" alt="image" src="https://github.com/user-attachments/assets/5aee40c3-27f0-42a2-88b0-b84dba11c78f" />

<img width="2971" height="1527" alt="image" src="https://github.com/user-attachments/assets/756d42e0-e132-4b98-b069-7a50276a0254" />
<img width="2914" height="1508" alt="image" src="https://github.com/user-attachments/assets/e5c3ea3e-4376-4aad-a123-6ac487a84c9f" />


##### Alert setting:
<img width="2993" height="1541" alt="image" src="https://github.com/user-attachments/assets/7071a182-5829-4c6c-9fc5-61f202496665" />

##### Alter rule:
<img width="1904" height="437" alt="image" src="https://github.com/user-attachments/assets/242012ea-44b5-4724-ae87-fd90b814f834" />

##### Log Analytics Workplace,  KQL and Logs:
<img width="1894" height="940" alt="image" src="https://github.com/user-attachments/assets/ca015923-ba01-4014-bc65-e775a2dca21a" />


##### Alert email received:
<img width="1213" height="655" alt="image" src="https://github.com/user-attachments/assets/e60025d4-49bf-4199-92d2-4e57b21f2723" />






##### Azure Alert Configuration

| Setting | Value |
|----------|-------|
| Measure | Table rows |
| Threshold | Greater than 5 |
| Aggregation | 5 minutes |
| Evaluation Frequency | 1 minute |
| Severity | 3 |

The alert sends an email notification whenever more than five failed login attempts occur within five minutes.


##### What I Learned

While working for the lab2, I learned how to integrate Azure Monitor with an Azure App Service and Log Analytics Workspace, in order to collect and analyze application logs. 
I also using writing Kusto Query Language (KQL) queries to detect suspicious activities, for example, repeated failed login attempts. 
Additionally, I lconfigured Azure Monitor Alert Rules and Action Groups to automatically send email notifications, when predefined security conditions are met. 
This lab is for cloud monitoring and automated threat detection can improve application security.

---

##### Challenges

One challenge I med is, to create web app on sepficia region, but it reported had no available App Service quota. 
I resolved the issue by creating the App Service Plan in East US instead of West US 2. 

Another challenge was locating the correct alert configuration options because the Azure Portal interface has changed. 

Finally, I had to verify that diagnostic settings were correctly sending application logs to the Log Analytics Workspace before the KQL queries and alert rules could function properly.

##### Youtube Demo
https://youtu.be/SVAfEG4W9mQ


