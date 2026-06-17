
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

