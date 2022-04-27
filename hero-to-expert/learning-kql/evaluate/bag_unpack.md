# bag\_unpack

```
IntuneDevices
| where TimeGenerated > ago (30d)
        and isnotempty(OS)
| distinct  OS, JoinType
| extend p = pack(OS, JoinType)
| summarize  bag = make_bag(p)
| evaluate bag_unpack(bag)
```

![](<../../../.gitbook/assets/image (1).png>)

```
SigninLogs
| where TimeGenerated > ago(1d)
| evaluate bag_unpack(DeviceDetail)
| distinct UserPrincipalName, displayName, operatingSystem, trustType
```

![](<../../../.gitbook/assets/image (6).png>)
