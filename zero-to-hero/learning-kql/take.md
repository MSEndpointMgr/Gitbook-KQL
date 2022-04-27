# take

In the previous chapter, we talked about **search**, it often returns lots of rows in the result. It's useful to use **take** to get some examples of the results but not all of them. There is no guarantee which rows it will return or if they are exact same.&#x20;

```
IntuneDevices
| search DeviceName matches regex "[A-Z]-"
| take 10
```

