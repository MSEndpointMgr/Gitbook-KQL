# summarize

**summarize** operator is complicated in my opinion.  :smile: And often I still forgot how to use it and even got it all wrong. Because summarize is used with many aggregation funcions. Here is the full list

### 📃[List of aggregation functions](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/summarizeoperator#list-of-aggregation-functions) <a href="#list-of-aggregation-functions" id="list-of-aggregation-functions"></a>

| Function                                                                                                                       | Description                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| [arg\_max()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/arg-max-aggfunction)                             | Returns one or more expressions when the argument is maximized               |
| [arg\_min()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/arg-min-aggfunction)                             | Returns one or more expressions when the argument is minimized               |
| [avg()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/avg-aggfunction)                                      | Returns an average value across the group                                    |
| [avgif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/avgif-aggfunction)                                  | Returns an average value across the group (with predicate)                   |
| [binary\_all\_and](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/binary-all-and-aggfunction)                | Returns aggregated value using the binary `AND` of the group                 |
| [binary\_all\_or](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/binary-all-or-aggfunction)                  | Returns aggregated value using the binary `OR` of the group                  |
| [binary\_all\_xor](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/binary-all-xor-aggfunction)                | Returns aggregated value using the binary `XOR` of the group                 |
| [buildschema()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/buildschema-aggfunction)                      | Returns the minimal schema that admits all values of the `dynamic` input     |
| [count()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/count-aggfunction)                                  | Returns a count of the group                                                 |
| [countif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/countif-aggfunction)                              | Returns a count with the predicate of the group                              |
| [dcount()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/dcount-aggfunction)                                | Returns an approximate distinct count of the group elements                  |
| [dcountif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/dcountif-aggfunction)                            | Returns an approximate distinct count of the group elements (with predicate) |
| [make\_bag()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/make-bag-aggfunction)                           | Returns a property bag of dynamic values within the group                    |
| [make\_bag\_if()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/make-bag-if-aggfunction)                    | Returns a property bag of dynamic values within the group (with predicate)   |
| [make\_list()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/makelist-aggfunction)                          | Returns a list of all the values within the group                            |
| [make\_list\_if()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/makelistif-aggfunction)                    | Returns a list of all the values within the group (with predicate)           |
| [make\_list\_with\_nulls()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/make-list-with-nulls-aggfunction) | Returns a list of all the values within the group, including null values     |
| [make\_set()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/makeset-aggfunction)                            | Returns a set of distinct values within the group                            |
| [make\_set\_if()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/makesetif-aggfunction)                      | Returns a set of distinct values within the group (with predicate)           |
| [max()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/max-aggfunction)                                      | Returns the maximum value across the group                                   |
| [maxif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/maxif-aggfunction)                                  | Returns the maximum value across the group (with predicate)                  |
| [min()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/min-aggfunction)                                      | Returns the minimum value across the group                                   |
| [minif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/minif-aggfunction)                                  | Returns the minimum value across the group (with predicate)                  |
| [percentiles()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/percentiles-aggfunction)                      | Returns the percentile approximate of the group                              |
| [percentiles\_array()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/percentiles-aggfunction)               | Returns the percentiles approximates of the group                            |
| [percentilesw()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/percentiles-aggfunction)                     | Returns the weighted percentile approximate of the group                     |
| [percentilesw\_array()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/percentiles-aggfunction)              | Returns the weighted percentiles approximates of the group                   |
| [stdev()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/stdev-aggfunction)                                  | Returns the standard deviation across the group                              |
| [stdevif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/stdevif-aggfunction)                              | Returns the standard deviation across the group (with predicate)             |
| [sum()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/sum-aggfunction)                                      | Returns the sum of the elements within the group                             |
| [sumif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/sumif-aggfunction)                                  | Returns the sum of the elements within the group (with predicate)            |
| [take\_any()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/take-any-aggfunction)                           | Returns a random non-empty value for the group                               |
| [take\_anyif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/take-anyif-aggfunction)                       | Returns a random non-empty value for the group (with predicate)              |
| [variance()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/variance-aggfunction)                            | Returns the variance across the group                                        |
| [varianceif()](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/varianceif-aggfunction)                        | Returns the variance across the group (with predicate)                       |

