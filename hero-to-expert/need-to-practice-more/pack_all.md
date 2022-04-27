# pack\_all

```
let T1 = datatable (Key:string , Col2:string , Col3:string )
[
  "1", "b", "c",
  "2", "e", "f",
  "3", "h", "i"
] 
| project PackedRecord = todynamic(replace_regex(tostring(pack_all()), '"([a-zA-Z0-9_]*)":"', @'"T1_1":"'))
| evaluate bag_unpack(PackedRecord);
let T2 = datatable (Key:string , Col2:string , Col3:string )
[
  "1", "B", "C",
  "2", "E", "F",
  "4", "H", "I"
] 
| project PackedRecord = todynamic(replace_regex(tostring(pack_all()), '"([a-zA-Z0-9_]*)":"', @'"T2_1":"'))
| evaluate bag_unpack(PackedRecord);
let JoinTable = T1 | join kind=inner T2 on $left.T1_Key == $right.T2_Key;
JoinTable
```
