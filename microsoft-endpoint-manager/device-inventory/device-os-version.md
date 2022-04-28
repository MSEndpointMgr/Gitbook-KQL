# Device OS version

## Using SigninLogs

You might ask a question here, why use **SigninLogs** table, not **IntuneDevices** table? Because IntuneDevices table only gives details of devices that are managed by Intune.&#x20;

Let's say you want to use Intune managed mobile devices, both MDM and MAM, we know Intune doesn't support all operating systems, there are some requirements, therefore your might need a list of devices' operating system version and users, so that maybe some of the lucky users will get a new phone:smile:.  &#x20;

See Intune supported operating system details on Microsoft Doc [https://docs.microsoft.com/en-us/mem/intune/fundamentals/supported-devices-browsers](https://docs.microsoft.com/en-us/mem/intune/fundamentals/supported-devices-browsers)

Quote from Microsoft Doc (Updated Jan.13, 2022)

{% hint style="info" %}
### Intune supported operating systems <a href="#intune-supported-operating-systems" id="intune-supported-operating-systems"></a>



#### Apple <a href="#apple" id="apple"></a>

* Apple iOS 13.0 and later
* Apple iPadOS 13.0 and later
* macOS 10.15 and later

#### &#x20;Google <a href="#google" id="google"></a>

* Android 6.0 and later (including Samsung KNOX Standard 2.4 and higher: [requirements](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+))
* Android enterprise: [requirements](https://support.google.com/work/android/topic/9428066)
{% endhint %}

{% hint style="warning" %}
Intune requires Android 6.x or higher for device enrollment scenarios. For Intune app protection policies, Intune requires Android 9.0 or higher. This requirement does NOT apply to Polycom Android-based Teams devices running 4.4. These devices will continue to be supported.
{% endhint %}

### 📳 Example: Android OS versions

So how can we get a list of devices' operating system versions that users are using to access organization data?  Let's use **SigninLogs** to find out what iOS versions we have

```
SigninLogs
| where TimeGenerated > ago (180d)
| summarize arg_max(TimeGenerated, *) by UserPrincipalName,  AppDisplayName
| extend OperatingSystem = tostring(DeviceDetail.operatingSystem)
| where OperatingSystem contains "Android"
    and UserPrincipalName has '@'
     and AppDisplayName == "Outlook Mobile"
| extend UserAgent = split(UserAgent, "; ")
| extend OSVersion = tostring(UserAgent[1])
| project TimeGenerated, UserPrincipalName, OSVersion, OperatingSystem
```

![](<../../.gitbook/assets/image (28).png>)

### 📌 Example #2: Sign-in location details

This query tells you users' sign-in location details, IP address, Operating System

```
SigninLogs
| where TimeGenerated > ago (180d)
| extend OperatingSystem = tostring(DeviceDetail.operatingSystem)
        , DeviceId = tostring(DeviceDetail.deviceId)
        , City = tostring(LocationDetails.city)
        , CountryOrRegion = tostring(LocationDetails.countryOrRegion)
        , State = tostring(LocationDetails.state)
| distinct UserPrincipalName, DeviceId, OperatingSystem, IPAddress, City, CountryOrRegion, State
| project UserPrincipalName, DeviceId, OperatingSystem, IPAddress, CountryOrRegion, State, City
```

![Sigin details with Operating System, IP address, Location Details](<../../.gitbook/assets/image (12).png>)

