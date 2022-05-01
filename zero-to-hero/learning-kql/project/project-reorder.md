# project-reorder

```
IntuneDevices
| summarize arg_max(TimeGenerated, *) by SerialNumber
| where UserName has_any ("sandy", "jan", "maurice")
| project-reorder TimeGenerated, U* asc, D* 
```

![](<../../../.gitbook/assets/image (4).png>)
