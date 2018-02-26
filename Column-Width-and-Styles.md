![ColumnSettings.jpg](images/Column-Width-and-Styles_ColumnSettings.jpg "ColumnSettings.jpg")  

```c#
var workbook = new XLWorkbook();
var ws = workbook.Worksheets.Add("Column Settings");

var col1 = ws.Column("B");
col1.Style.Fill.BackgroundColor = XLColor.Red;
col1.Width = 20;

var col2 = ws.Column(4);
col2.Style.Fill.BackgroundColor = XLColor.DarkOrange;
col2.Width = 5;

workbook.SaveAs("ColumnSettings.xlsx");
```
