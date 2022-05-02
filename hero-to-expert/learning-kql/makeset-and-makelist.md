# makeset and makelist

```
AppInventory_CL
| where TimeGenerated > ago (7d)
| summarize arg_max(TimeGenerated, *) by ManagedDeviceID_g, AppName_s
| summarize  InstalledApps = make_set(AppName_s) by ManagedDeviceID_g, ComputerName_s
```

![](<../../.gitbook/assets/image (21).png>)
