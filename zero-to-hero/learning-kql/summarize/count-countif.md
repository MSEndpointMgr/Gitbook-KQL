# count, countif

### count

```
IntuneDevices
| where TimeGenerated > ago (30d)
        and isnotempty(OS)
| summarize arg_max(TimeGenerated, *) by SerialNumber
| summarize count() by OS, SkuFamily, JoinType
```

![](<../../../.gitbook/assets/image (11).png>)

### count

```
IntuneDevices
| where TimeGenerated > ago (30d)
        and isnotempty(OS)
| summarize arg_max(TimeGenerated, *) by SerialNumber
| summarize Count = count()
```

![](<../../../.gitbook/assets/image (9).png>)

### countif

```
IntuneDevices
| where TimeGenerated > ago (30d)
        and isnotempty(OS)
| summarize arg_max(TimeGenerated, *) by SerialNumber
| summarize Count = countif(OS != 'Windows')
```

![](<../../../.gitbook/assets/image (26) (1) (1).png>)
