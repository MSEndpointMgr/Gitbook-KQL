# where

**where** is similar to search, but it limits based on conditions, rather than looking at all the data. This make the query run much faster than using **search**

You can read the search chapter again 👇

{% content-ref url="search.md" %}
[search.md](search.md)
{% endcontent-ref %}

### 🔍 Search from a column

```
//use where
IntuneDevices
| where DeviceName contains "THINK"

//Use search
IntuneDevices
| search DeviceName: "THINK*"
```

### 🔍 Search from any column at the start

```
// use where
IntuneDevices
| where * hasprefix "MVP"  // At the start

//use search
IntuneDevices
| search * startswith "MVP" // At the start
```

### 🔍Search from any column at the end

```
// use where
IntuneDevices
| where * hassuffix "460"  // At the end

// use search
IntuneDevices
| search * endswith "460"  // At the end
```

### 🔍Search with regax

```
// use where
IntuneDevices
| where DeviceName matches regex "[A-Z]-"

//use search
IntuneDevices
| search DeviceName matches regex "[A-Z]-"
```
