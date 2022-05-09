# make\_set, make\_list

```
let Apps = datatable (User:string, AppName: string) [
 "User01", "1Password",
 "User01", "Camtasia 2021",
 "User02", "Camtasia 2021",
 "User03", "Microsoft Visio - en-us",
 "User03", "Microsoft Visio - en-us"
];
Apps
| summarize  make_set(AppName) by User
```

![](<../../.gitbook/assets/image (15).png>)

```
let Apps = datatable (User:string, AppName: string) [
 "User01", "1Password",
 "User01", "Camtasia 2021",
 "User02", "Camtasia 2021",
 "User03", "Microsoft Visio - en-us",
 "User03", "Microsoft Visio - en-us"
];
Apps
| summarize  make_list(AppName) by User
```

![](<../../.gitbook/assets/image (28).png>)

```
AppInventory_CL
| where TimeGenerated > ago (7d)
| summarize arg_max(TimeGenerated, *) by ManagedDeviceID_g, AppName_s
| summarize  InstalledApps = make_set(AppName_s) by ManagedDeviceID_g, ComputerName_s
```

![](<../../.gitbook/assets/image (11).png>)
