# distinct

I often use distinct to look for the value that I want to use later as filters or parameters in workbooks. For example, I see IntuneDevices table has a column called ManageBy, but I have no ideas what data we have in this column.

```
IntuneDevices
| where Result == 'None'
| where TimeGenerated > ago (30d)
| distinct OS, JoinType,Ownership, ManagedBy, DeviceRegistrationState
```

![](<../../.gitbook/assets/image (17).png>)

Now that I know that I have "Intune" and "Co-managed" values in ManagedBy, if I want to know what devices are Co-managed, I can run the following query

```
IntuneDevices
| where TimeGenerated > ago (7d) 
    and todatetime(LastContact) > ago(60d) //We need to convert LastContact to date time format
    and ManagedBy == 'Co-managed' //filter device are Co-managed
| summarize arg_max(TimeGenerated, *) by SerialNumber
```
