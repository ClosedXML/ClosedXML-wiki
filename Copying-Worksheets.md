```c#
var wb = new XLWorkbook("BasicTable.xlsx");
var wsSource = wb.Worksheet(1);
// Copy the worksheet to a new sheet in this workbook
wsSource.CopyTo("Copy");

// We're going to open another workbook to show that you can
// copy a sheet from one workbook to another:
var wbSource = new XLWorkbook("BasicTable.xlsx");
wbSource.Worksheet(1).CopyTo(wb, "Copy From Other");

// Save the workbook with the 2 copies
wb.SaveAs("CopyingWorksheets.xlsx");
```
