![Showcase.jpg](images/Showcase_Showcase.jpg "Showcase.jpg")

**Creating a new workbook**

```c#
var wb = new XLWorkbook();
```

**Adding a worksheet**

```c#
var ws = wb.Worksheets.Add("Contacts");
```

**Adding text**

```c#
// Title
ws.Cell("B2").Value = "Contacts";

// First Names
ws.Cell("B3").Value = "FName";
ws.Cell("B4").Value = "John";
ws.Cell("B5").Value = "Hank";
ws.Cell("B6").SetValue("Dagny"); // Another way to set the value

// Last Names
ws.Cell("C3").Value = "LName";
ws.Cell("C4").Value = "Galt";
ws.Cell("C5").Value = "Rearden";
ws.Cell("C6").SetValue("Taggart"); // Another way to set the value
```

**Adding more data types**

```c#
// Boolean
ws.Cell("D3").Value = "Outcast";
ws.Cell("D4").Value = true;
ws.Cell("D5").Value = false;
ws.Cell("D6").SetValue(false); // Another way to set the value

// DateTime
ws.Cell("E3").Value = "DOB";
ws.Cell("E4").Value = new DateTime(1919, 1, 21);
ws.Cell("E5").Value = new DateTime(1907, 3, 4);
ws.Cell("E6").SetValue(new DateTime(1921, 12, 15)); // Another way to set the value

// Numeric
ws.Cell("F3").Value = "Income";
ws.Cell("F4").Value = 2000;
ws.Cell("F5").Value = 40000;
ws.Cell("F6").SetValue(10000); // Another way to set the value
```

**Defining ranges**

```c#
// From worksheet
var rngTable = ws.Range("B2:F6");

// From another range
var rngDates = rngTable.Range("D3:D5"); // The address is relative to rngTable (NOT the worksheet)
var rngNumbers = rngTable.Range("E3:E5"); // The address is relative to rngTable (NOT the worksheet)
```

**Formatting dates and numbers**

```c#
// Using a OpenXML's predefined formats
rngDates.Style.NumberFormat.NumberFormatId = 15;

// Using a custom format
rngNumbers.Style.NumberFormat.Format = "$ #,##0";
```

**Format title cell in one shot**

```c#
rngTable.FirstCell().Style
  .Font.SetBold()
  .Fill.SetBackgroundColor(XLColor.CornflowerBlue)
  .Alignment.SetHorizontal(XLAlignmentHorizontalValues.Center);
```

**Merge title cells**

```c#
rngTable.FirstRow().Merge(); // We could've also used: rngTable.Range("A1:E1").Merge() or rngTable.Row(1).Merge()
```

**Formatting headers**

```c#
var rngHeaders = rngTable.Range("A2:E2"); // The address is relative to rngTable (NOT the worksheet)
rngHeaders.Style.Alignment.Horizontal = XLAlignmentHorizontalValues.Center;
rngHeaders.Style.Font.Bold = true;
rngHeaders.Style.Font.FontColor = XLColor.DarkBlue;
rngHeaders.Style.Fill.BackgroundColor = XLColor.Aqua;
```

**Create an Excel table with the data portion**

```c#
var rngData = ws.Range("B3:F6");
var excelTable = rngData.CreateTable();

// Add the totals row
excelTable.ShowTotalsRow = true;
// Put the average on the field "Income"
// Notice how we're calling the cell by the column name
excelTable.Field("Income").TotalsRowFunction = XLTotalsRowFunction.Average;
// Put a label on the totals cell of the field "DOB"
excelTable.Field("DOB").TotalsRowLabel = "Average:";
```

**Add thick borders**

```c#
// Add thick borders to the contents of our spreadsheet
ws.RangeUsed().Style.Border.OutsideBorder = XLBorderStyleValues.Thick;

// You can also specify the border for each side:
// contents.FirstColumn().Style.Border.LeftBorder = XLBorderStyleValues.Thick;
// contents.LastColumn().Style.Border.RightBorder = XLBorderStyleValues.Thick;
// contents.FirstRow().Style.Border.TopBorder = XLBorderStyleValues.Thick;
// contents.LastRow().Style.Border.BottomBorder = XLBorderStyleValues.Thick;
```

**Adjust column widths to their content**

```c#
ws.Columns().AdjustToContents(); // You can also specify the range of columns to adjust, e.g.
// ws.Columns(2, 6).AdjustToContents(); or ws.Columns("2-6").AdjustToContents();
```

**Saving the workbook**

```c#
wb.SaveAs("Showcase.xlsx");
```
