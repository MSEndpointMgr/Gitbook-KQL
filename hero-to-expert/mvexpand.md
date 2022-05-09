# mvexpand

```
SigninLogs
| project TimeGenerated, UserPrincipalName, ConditionalAccessPolicies
| mv-expand ConditionalAccessPolicies
```

![](<../.gitbook/assets/image (30).png>)

```
SigninLogs
| project TimeGenerated, UserPrincipalName, ConditionalAccessPolicies
| mv-expand ConditionalAccessPolicies
| evaluate bag_unpack(ConditionalAccessPolicies)
| mv-expand enforcedGrantControls
| project TimeGenerated, UserPrincipalName, displayName, enforcedGrantControls, result
```

![](<../.gitbook/assets/image (33).png>)
