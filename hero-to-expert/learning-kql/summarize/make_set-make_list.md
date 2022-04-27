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

![](<../../../.gitbook/assets/image (5).png>)

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

![](<../../../.gitbook/assets/image (23).png>)
