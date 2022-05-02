# union

```
UCClient
| summarize arg_max(TimeGenerated,Type)
| union (UCClientReadinessStatus
    | summarize arg_max(TimeGenerated,Type))
| union (UCClientUpdateStatus
    | summarize arg_max(TimeGenerated,Type))
| union (UCDeviceAlert
    | summarize arg_max(TimeGenerated,Type))
| union (UCServiceUpdateStatus
    | summarize arg_max(TimeGenerated,Type))
| union (UCUpdateAlert
    | summarize arg_max(TimeGenerated,Type))  
| where isnotempty(Type)
| project Type, TimeGenerated
| sort by TimeGenerated asc
```

![](<../../.gitbook/assets/image (14).png>)
