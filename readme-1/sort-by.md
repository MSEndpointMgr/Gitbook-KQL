# sort by

Sort the rows of the input table into order by one or more columns. Default is **descending order**

### 🦄 Example: Intune audit log for the past 7 days

&#x20;Sort by TimeGenerated column in ascending order.&#x20;

```
IntuneAuditLogs 
| where TimeGenerated > ago (7d)
| sort by TimeGenerated asc 
```

![](<../../.gitbook/assets/image (21) (1).png>)
