# search

Use <mark style="color:red;">**search**</mark> when you know what are looking for, but don't know from where.&#x20;

For example, I know I have a device name that starts with **THINK**, I can't remember what exact name it is and I just want to see what data do I get

{% hint style="info" %}
A faster way to filter the data that you are looking for is to **** use "**where".** &#x20;
{% endhint %}

{% content-ref url="where.md" %}
[where.md](where.md)
{% endcontent-ref %}

### &#x20;🔍Search everything and not case sensitive

```
search "*think*"
```

This will return all the results that contain think (not case sensitive) from all columns and all tables

![search anything and not case sensitive](<../../.gitbook/assets/image (7).png>)

### 🔍Search matched words with case sensitive

```
search kind=case_sensitive "THINK460"
```

![Search matched words with case sensitive](<../../.gitbook/assets/image (19).png>)

### 🔍Search from specific tables

```
search in (IntuneDevices, UCClient) "THINK460"
```

![Search from specific tables](<../../.gitbook/assets/image (14).png>)

### 🔍Search the value from the specified columnIntu

```
// Some code
IntuneDevices
| search DeviceName: "THINK"
```

```
```

### 🔍Search begins with and starts with

```
// Search startswith
IntuneDevices
| search * startswith "THINK" 

//Search endswith
IntuneDevices
| search * endswith "01" 
```

### 🔍Search combined logically

```
IntuneDevices
| search * endswith "01" and ("Windows" or "iOS")
```

### 🔍Search with regex

```
IntuneDevices
| search DeviceName matches regex "[A-Z]-"
```
