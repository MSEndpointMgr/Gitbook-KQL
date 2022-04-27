# series\_outliers

Quote from Microsoft Doc: [https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/series-outliersfunction](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/series-outliersfunction)

> Scores anomaly points in a series.
>
> The function takes an expression with a dynamic numerical array as input, and generates a dynamic numeric array of the same length. Each value of the array indicates a score of a possible anomaly, using ["Tukey's test"](https://en.wikipedia.org/wiki/Outlier#Tukey%27s\_fences). A value greater than 1.5 in the same element of the input indicates a rise or decline anomaly. A value less than -1.5, indicates a decline anomaly.

This is very useful for hunting or monitorying for security related events, for example unusual sigin in events
