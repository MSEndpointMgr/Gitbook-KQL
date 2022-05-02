# pack

```
IntuneDevices
| where TimeGenerated > ago (30d)
        and isnotempty(OS)
| distinct  OS, JoinType
| extend p = pack(OS, JoinType)
```

![](<../../.gitbook/assets/image (27) (1).png>)
