<h1> Azure Logging & Monitoring</h1>

<h2>Objective</h2>
How to access logs in Azure and apply Kusto Query Language to filter and retrieves logs that need to be investigated for deeper analysis<br>

<h2>Environment</h2>
<ul>
 <li> Azure </li>
</ul>

<h2>Tasks Completed</h2>
<ul>
 <li>Carried out various searches using KQL language</li>
 <li>Analysed several logs and navigated my way through important information such as IP, Location, timestamp etc </li>
</ul>

<h2> Azure Logs & KQL</h2>

<h2>Screenshots</h2>

<p>
<img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/92d1c2938cdf6761f573eed56c7525c55806b515/Screenshot%202026-05-15%20at%2008.33.54.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/680d3d445693b5f1981e27b2f91cedd753a51161/Screenshot%202026-05-15%20at%2008.42.36.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/f0eea02a6cb8648ea98bc20be859a15597d7f68c/Screenshot%202026-05-15%20at%2009.05.50.png" width="300" height="300" /> 
</p>

<b>Screenshot1:</b> Shows how I analyse sign-in logs and use KQL to retrieve events that occurred within the last three hours.<br>
<b>Screenshot2:</b> Shows how I use KQL to retrieve select fields to narrow my search.<br>
<b>Screenshot3:</b> Shows how I use distinct to filter to return all the unqiue IP addresses that logged in.

<b>process:</b> `Azure - Search log Analytic Workspaces - New Query (KQL mode) - Run Query` 

<p>
<img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/3e3f8346cbaa7e99f9772793430f088fcba456bb/Screenshot%202026-05-15%20at%2009.28.43.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/201d3448659ba875b9841834d31bd3a226231856/Screenshot%202026-05-15%20at%2009.32.24.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/201d3448659ba875b9841834d31bd3a226231856/Screenshot%202026-05-15%20at%2009.32.24.png" width="300" height="300" /> 
</p>

<b>Screenshot1:</b> Shows how I use KQL to retrieve all logs from one single IP address.<br>
<b>Screenshot2:</b> Shows how I can export logs if I need to send the raw data to seniors.<br>
<b>Screenshot3:</b> Shows how I adjust the time range to make sure the search retrieves the correct data for a certain time period.<br>

<h2> Azure Activity Logs</h2>

<p>
<img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/c6f3d27f0953a8f5dd9b3f1ab5ad61462ecb46b1/Screenshot%202026-05-15%20at%2010.38.36.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src= "https://github.com/NickHoward1/Azure-Audit-Logs---KQL/blob/a3d47c74fab8ac25b0a975db152133f4f342c434/Screenshot%202026-05-15%20at%2011.09.41.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>



`// Someone deleting more than 10 resources
let resource_threshold = 10;
let time_threshold_in_minutes = 30m;
AzureActivity
| where TimeGenerated > ago(time_threshold_in_minutes) 
| where OperationNameValue endswith "DELETE" and ActivityStatusValue == "Success"
| summarize number_of_records = count() by Caller, ActivityStatusValue
| where number_of_records > resource_threshold`

<b>Screenshot1:</b> Shows how I search for <br>
<b>Screenshot2:</b> Shows how I break down the KQL to bring back the number of users that successfully deleted resources within the last 7 days.<br>

This search query can help me determine 


