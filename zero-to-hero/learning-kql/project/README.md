# project

```
IntuneDevices
| summarize arg_max(TimeGenerated, *) by SerialNumber
| where UserName has "sandy"
| project TimeGenerated, UserName, Manufacturer, DeviceName, Model
```

![](<../../../.gitbook/assets/image (26).png>)
