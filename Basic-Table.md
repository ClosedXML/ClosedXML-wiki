## Basic Table

![BasicTable.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=165397 "BasicTable.jpg")  

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
ws.Cell("B6").Value = "Dagny";

// Last Names
ws.Cell("C3").Value = "LName";
ws.Cell("C4").Value = "Galt";
ws.Cell("C5").Value = "Rearden";
ws.Cell("C6").Value = "Taggart";
```

**Adding more data types**  
```c#
// Boolean
ws.Cell("D3").Value = "Outcast";
ws.Cell("D4").Value = true;
ws.Cell("D5").Value = false;
ws.Cell("D6").Value = false;

// DateTime
ws.Cell("E3").Value = "DOB";
ws.Cell("E4").Value = new DateTime(1919, 1, 21);
ws.Cell("E5").Value = new DateTime(1907, 3, 4);
ws.Cell("E6").Value = new DateTime(1921, 12, 15);

// Numeric
ws.Cell("F3").Value = "Income";
ws.Cell("F4").Value = 2000;
ws.Cell("F5").Value = 40000;
ws.Cell("F6").Value = 10000;
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
// Using OpenXML's predefined formats
rngDates.Style.NumberFormat.NumberFormatId = 15;

// Using a custom format
rngNumbers.Style.NumberFormat.Format = "$ #,##0";
```

**Formatting headers**  
```c#
var rngHeaders = rngTable.Range("A2:E2"); // The address is relative to rngTable (NOT the worksheet)
rngHeaders.Style.Alignment.Horizontal = XLAlignmentHorizontalValues.Center;
rngHeaders.Style.Font.Bold = true;
rngHeaders.Style.Fill.BackgroundColor = XLColor.Aqua;
```

**Adding grid lines**  
```c#
rngTable.Style.Border.BottomBorder = XLBorderStyleValues.Thin;
```

**Format title cell**  
```c#
rngTable.Cell(1, 1).Style.Font.Bold = true;
rngTable.Cell(1, 1).Style.Fill.BackgroundColor = XLColor.CornflowerBlue;
rngTable.Cell(1, 1).Style.Alignment.Horizontal = XLAlignmentHorizontalValues.Center;
```

**Merge title cells**  
```c#
rngTable.Row(1).Merge(); // We could've also used: rngTable.Range("A1:E1").Merge()
```

**Add thick borders**  
```c#
//Add a thick outside border
rngTable.Style.Border.OutsideBorder = XLBorderStyleValues.Thick;

// You can also specify the border for each side with:
// rngTable.FirstColumn().Style.Border.LeftBorder = XLBorderStyleValues.Thick;
// rngTable.LastColumn().Style.Border.RightBorder = XLBorderStyleValues.Thick;
// rngTable.FirstRow().Style.Border.TopBorder = XLBorderStyleValues.Thick;
// rngTable.LastRow().Style.Border.BottomBorder = XLBorderStyleValues.Thick;
```

**Adjust column widths to their content**  
```c#
ws.Columns(2, 6).AdjustToContents();
```

**Saving the workbook**  
```c#
wb.SaveAs("BasicTable.xlsx");
```