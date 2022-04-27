# set\_difference

```
let RequiredApps = toscalar (datatable (AppName: string) [
 "1Password",
 "Camtasia 2021",
 "Azure Monitor Agent"
]
| summarize  make_set(AppName));
AppInventory_CL
| where TimeGenerated > ago (7d)
| summarize arg_max(TimeGenerated, *) by ManagedDeviceID_g, AppName_s
| summarize  InstalledApps = make_set(AppName_s) by ManagedDeviceID_g, ComputerName_s
| extend  MissingApps= set_difference(RequiredApps, InstalledApps)
| where MissingApps <> '[]'
| project ComputerName_s, MissingApps

```

![](<../../.gitbook/assets/image (28).png>)
