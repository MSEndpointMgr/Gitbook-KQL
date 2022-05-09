# make\_bag

```
IntuneDevices
| where TimeGenerated > ago (30d)
        and isnotempty(OS)
| distinct  OS, JoinType
| extend p = pack(OS, JoinType)
| summarize  bag = make_bag(p)
```

![](<../../.gitbook/assets/image (4).png>)
