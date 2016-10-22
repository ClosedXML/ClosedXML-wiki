![CustomAutoFilter1.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=301323 "CustomAutoFilter1.jpg")  

![CustomAutoFilter2.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=301324 "CustomAutoFilter2.jpg")  

![CustomAutoFilter3.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=301325 "CustomAutoFilter3.jpg")  

![CustomAutoFilter4.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=301326 "CustomAutoFilter4.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("AutoFilter");

// Add a bunch of strings to filter
ws.Cell("A1").SetValue("Strings")
  .CellBelow().SetValue("B")
  .CellBelow().SetValue("C")
  .CellBelow().SetValue("C")
  .CellBelow().SetValue("E")
  .CellBelow().SetValue("A")
  .CellBelow().SetValue("D");

// Add filters
ws.RangeUsed().SetAutoFilter().Column(1).Between("B", "D");

// Sort the filtered list
ws.AutoFilter.Sort(1, XLSortOrder.Descending);

wb.SaveAs("AutoFilter.xlsx");
```
