## Freeze Panes

```c#
var wb = new XLWorkbook();
var wsFreeze = wb.Worksheets.Add("Freeze View");

// Freeze rows and columns in one shot
wsFreeze.SheetView.Freeze(3, 3);

// You can also be more specific on what you want to freeze
// For example:
// wsFreeze.SheetView.FreezeRows(3);
// wsFreeze.SheetView.FreezeColumns(3);

// To remove a split set SplitColumn and/or SplitRow to zero
// e.g.
// wsFreeze.SheetView.SplitRow = 0;
// wsFreeze.SheetView.SplitColumn = 0;

wb.SaveAs("FreezePanes.xlsx");
```
