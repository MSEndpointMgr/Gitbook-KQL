# arg\_max

Let's try useing the **IntuneDevices** table to count how many devices we have per Operating Systems

{% hint style="danger" %}
This is an example of a wrong query. The bellow query is getting data that are generated for the past 7 days, returns a count of the records per summarization group by **OS** column. The problem with this query is IntuneDevices table gets all the devices' data once per day, which means there are duplicate rows.&#x20;
{% endhint %}

```
IntuneDevices
| where TimeGenerated > ago (7d) and isnotempty(OS)
| summarize count() by OS
```

![Example of a wrong query](<../../../.gitbook/assets/image (4) (1) (1).png>)

{% hint style="success" %}
Let fixed the above query. I will use **arg\_max()** aggregation to maximized TimeGenerated (means latest data in this case), return OS for each device's SerialNumber. I use SerialNumber instead DeviceName because sometime we might reinstall the same device again using a different device name, I don't want to have duplicated data result
{% endhint %}

```
IntuneDevices
| where TimeGenerated > ago (7d) and isnotempty(OS) //Get data that are generated in 7 days. and only if OS information is not empty
| summarize arg_max(TimeGenerated, OS) by SerialNumber //returun latest generated data of OS information based on device's serial number
| summarize count() by OS // Total count OS based on OS
```

![Correct query exampl](<../../../.gitbook/assets/image (3).png>)

{% hint style="info" %}
An even better query, we filter out those devices that haven't contacted Intune for over 60 days.
{% endhint %}

```
IntuneDevices
| where TimeGenerated > ago (7d) 
    and isnotempty(OS)
    and todatetime(LastContact) > ago(60d) //We need to convert LastContact to date time format
| summarize arg_max(TimeGenerated, OS) by SerialNumber
| summarize count() by OS

```

![](<../../../.gitbook/assets/image (23) (1) (1).png>)
