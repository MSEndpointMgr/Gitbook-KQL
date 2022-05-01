# project-away



```
IntuneDevices
| summarize arg_max(TimeGenerated, *) by SerialNumber
| where UserName has_any ("sandy", "jan", "maurice")
| project-away TimeGenerated, U*, D*, SerialNumber
```

![](<../../../.gitbook/assets/image (25).png>)
