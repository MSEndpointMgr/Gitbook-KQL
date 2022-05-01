# project-keep

```
IntuneDevices
| summarize arg_max(TimeGenerated, *) by SerialNumber
| where UserName has "sandy"
| project-keep TimeGenerated, U*
```

![](<../../../.gitbook/assets/image (24).png>)
