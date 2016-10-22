```c#
var workbook = new XLWorkbook("BasicTable.xlsx");
var ws = workbook.Worksheet(1);

// Define a range with the data
var firstTableCell = ws.FirstCellUsed();
var lastTableCell = ws.LastCellUsed();
var rngData = ws.Range(firstTableCell.Address, lastTableCell.Address);

// Copy the table to another worksheet
var wsCopy = workbook.Worksheets.Add("Contacts Copy");
wsCopy.Cell(1,1).Value = rngData;

workbook.SaveAs("CopyingRanges.xlsx");
```
