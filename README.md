
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


# Project Architecture

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


