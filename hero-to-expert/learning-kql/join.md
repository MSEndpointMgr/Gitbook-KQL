# join data

```
let IntuneData = IntuneDevices
| where OS == 'Windows' and UserName has "Sandy"
| summarize arg_max(TimeGenerated, *) by SerialNumber
| distinct ReferenceId, UPN;
UCClient
| where TimeGenerated > ago (3d)
| join kind=innerunique   IntuneData on $left.AzureADDeviceId == $right.ReferenceId
| project TimeGenerated, DeviceName, OSEdition, OSVersion, OSServicingChannel, UPN
```

![](<../../.gitbook/assets/image (28).png>)
