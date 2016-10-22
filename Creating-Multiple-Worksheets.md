![MultipleSheets.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=149611 "MultipleSheets.jpg")  

```c#
var workbook = new XLWorkbook();
foreach (var wsNum in Enumerable.Range(1, 5))
{
  var ws = workbook.Worksheets.Add("Sheet " + wsNum.ToString());
}

workbook.SaveAs("MultipleSheets.xlsx");
```
