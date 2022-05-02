# let

```
let n = 10;  // number
let computername = "cloudway";  // string
let Day = ago(30d); // datetime 
UCClient
| where TimeGenerated > Day
| where DeviceName has computername
| take n
```

![](<../../.gitbook/assets/image (20).png>)
