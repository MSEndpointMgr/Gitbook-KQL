# take\_any

**take\_any** will return a random row from the dataset

### Return only one random row

```
IntuneDevices
| summarize take_any(*)
```

![](<../../../.gitbook/assets/image (22) (1).png>)

### Return only one random row with specific columns

```
IntuneDevices
| summarize take_any(DeviceName, TimeGenerated, DeviceId)
```

![](<../../../.gitbook/assets/image (16).png>)

### Use with by, returns a random row for each distinct value from that column

```
IntuneDevices
| summarize take_any(DeviceId, OS, CompliantState) by DeviceName
```

![](<../../../.gitbook/assets/image (25) (1) (1).png>)
