# mvexpand

```
SigninLogs
| project TimeGenerated, UserPrincipalName, ConditionalAccessPolicies
| mv-expand ConditionalAccessPolicies
```

![](<../../.gitbook/assets/image (19).png>)

```
SigninLogs
| project TimeGenerated, UserPrincipalName, ConditionalAccessPolicies
| mv-expand ConditionalAccessPolicies
| evaluate bag_unpack(ConditionalAccessPolicies)
| mv-expand enforcedGrantControls
| project TimeGenerated, UserPrincipalName, displayName, enforcedGrantControls, result
```

![](<../../.gitbook/assets/image (7).png>)
