# set\_differenc



```
let Apps = datatable (AppName: string) [
 "1Password",
 "Camtasia 2021",
 "Microsoft Visio - en-us"
]
| summarize  a1 = make_set(AppName);
AppInventory_CL
| where TimeGenerated > ago (7d)
| summarize arg_max(TimeGenerated, *) by ManagedDeviceID_g, AppName_s
| project ManagedDeviceID_g, AppName_s, ComputerName_s
| join kind=inner ( IntuneDevices 
    | where OS has "Windows" 
        and todatetime( LastContact) > ago (30d)
    | summarize arg_max(TimeGenerated, *) by SerialNumber
    | project TimeGenerated, DeviceName, DeviceId, LastContact
    ) on $left.ManagedDeviceID_g == $right.DeviceId
| summarize  a2 = make_set(AppName_s) by DeviceName, TimeGenerated, LastContact
| extend a1 = toscalar(Apps)
| project TimeGenerated, LastContact, DeviceName, MissingApps = set_difference(a1, a2)
| where MissingApps != '[]'
```

![](<../../.gitbook/assets/image (25).png>)
