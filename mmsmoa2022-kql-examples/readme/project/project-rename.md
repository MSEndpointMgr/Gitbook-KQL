# project-rename

```
IntuneDevices
| summarize arg_max(TimeGenerated, *) by SerialNumber
| where UserName has_any ("sandy", "jan", "maurice")
| project-rename ['User Name'] = UserName
| project TimeGenerated, ['User Name'], DeviceName
```

![](<../../../.gitbook/assets/image (1).png>)
