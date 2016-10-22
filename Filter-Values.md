![RegularAutoFilter1.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=301320 "RegularAutoFilter1.jpg")  
->  
![RegularAutoFilter2.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=301321 "RegularAutoFilter2.jpg")  
->  
![RegularAutoFilter3.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=301322 "RegularAutoFilter3.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("AutoFilter");

// Add a bunch of strings to filter
ws.Cell("A1").SetValue("Numbers")
  .CellBelow().SetValue(2)
  .CellBelow().SetValue(3)
  .CellBelow().SetValue(3)
  .CellBelow().SetValue(5)
  .CellBelow().SetValue(1)
  .CellBelow().SetValue(4);

// Add filters
ws.RangeUsed().SetAutoFilter().Column(1).AddFilter(3)
  .AddFilter(1)
  .AddFilter(5);

// Sort the filtered list
ws.AutoFilter.Sort(1);

wb.SaveAs("AutoFilter.xlsx");
```
