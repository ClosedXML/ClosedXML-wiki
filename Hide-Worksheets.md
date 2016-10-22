```c#
var wb = new XLWorkbook();

wb.Worksheets.Add("Visible");
wb.Worksheets.Add("Hidden").Hide();
wb.Worksheets.Add("Unhidden").Hide().Unhide();
wb.Worksheets.Add("VeryHidden").Visibility = XLWorksheetVisibility.VeryHidden;

wb.SaveAs("HideWorksheets.xlsx");
```
