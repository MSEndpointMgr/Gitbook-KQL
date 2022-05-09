# extend

**extend** allow us to build calculated columns of our query results and append them to the result set. You can also extend custom text as well&#x20;

### 📲 Example: calculate Intune device free storage percentage, and convert storage from MB to GB

```
IntuneDevices
| where TimeGenerated > ago (30d) 
    and OS == 'Windows'
    and isnotempty(SerialNumber)
    and todatetime(LastContact) > ago(60d) //We need to convert LastContact to date time format
| summarize arg_max(TimeGenerated, *) by SerialNumber
| extend StorageTotalGB = round(todouble(StorageTotal)/1024, 3)
        ,StorageFreeGB = StorageFree /1024
        ,['Free Percentage'] = toreal(StorageFree) / toreal(StorageTotal) * 100
| project-reorder TimeGenerated, DeviceName, StorageTotalGB, StorageFreeGB, ['Free Percentage']
```

![](<../../.gitbook/assets/image (5).png>)

### 📲 Example: Get user sign-in details, extend information from device details

```
SigninLogs
| where TimeGenerated > ago (7d)
| extend OperatingSystem = tostring(DeviceDetail.operatingSystem)
| extend DeviceId = tostring(DeviceDetail.deviceId)
| extend Browser = tostring(DeviceDetail.browser)
| distinct UserPrincipalName, UserDisplayName, OperatingSystem, Browser, DeviceId, AppDisplayName
```

![](<../../.gitbook/assets/image (20).png>)
