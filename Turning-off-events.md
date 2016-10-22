By default ClosedXML keeps track of the inserts/deletes and adjusts the ranges accordingly.  

For example:  
```c#
var testRow = worksheet.Row(1);
worksheet.Row(1).InsertRowsAbove(1);
// testRow now points to the second row of the worksheet, not the first.
```

If you don't need this feature then you can turn it off to save memory and increase performance. Just open your workbook with the option XLEventTracking.Disabled.  

```c#
var wb = new XLWorkbook(XLEventTracking.Disabled);
```
