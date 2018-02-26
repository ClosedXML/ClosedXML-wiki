![AutoFilter1.jpg](images/Adding-an-AutoFilter-to-a-Range_AutoFilter1.jpg "AutoFilter1.jpg")

![AutoFilter2.jpg](images/Adding-an-AutoFilter-to-a-Range_AutoFilter2.jpg "AutoFilter2.jpg")

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("AutoFilter");
ws.Cell("A1").Value = "Names";
ws.Cell("A2").Value = "John";
ws.Cell("A3").Value = "Hank";
ws.Cell("A4").Value = "Dagny";

ws.RangeUsed().SetAutoFilter();

// Your can turn off the autofilter by:
// 1) worksheet.AutoFilter.Clear()
// 2) worksheet.SetAutoFilter(false)
// 3) Pick any range in the worksheet and call the above methods on the range

wb.SaveAs("AutoFilter.xlsx");
```
