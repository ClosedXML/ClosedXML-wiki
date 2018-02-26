![MultipleSheets.jpg](images/Creating-Multiple-Worksheets_MultipleSheets.jpg "MultipleSheets.jpg")  

```c#
var workbook = new XLWorkbook();
foreach (var wsNum in Enumerable.Range(1, 5))
{
  var ws = workbook.Worksheets.Add("Sheet " + wsNum.ToString());
}

workbook.SaveAs("MultipleSheets.xlsx");
```
