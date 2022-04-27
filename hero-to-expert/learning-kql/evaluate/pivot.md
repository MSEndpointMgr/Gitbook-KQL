# pivot

```
IntuneDevices
| summarize arg_max(TimeGenerated, *) by SerialNumber
| where OS == 'Windows'
| project OSVersion, Manufacturer
| evaluate pivot(OSVersion)
```

![](<../../../.gitbook/assets/image (21).png>)
