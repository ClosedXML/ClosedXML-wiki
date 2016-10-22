**Note:** The "using" keyword is not needed if you turn off event tracking on the workbook. Please see [Turning off events](Turning-off-events) for more details.  

You should use the "using" keyword whenever you get a hold of a range-like object inside a loop. That includes workbook, worksheet, row, rows, column, and columns.  

The following recommendations assume you're dealing with big files.  

**Not so good:**  
```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Sheet1");
for (int ro = 1; ro <= 1000000; ro++)
{
  ws.Row(ro).FirstCell().Value = ro;
}
```

**Best way:**  
```c#
using (var wb = new XLWorkbook())
{
  // No need to put the worksheet inside a "using" block because
  // the workbook will dispose of the sheets. The worksheet is not
  // created inside a loop and the workbook's dispose is being
  // called immediately after using the worksheet.
  var ws = wb.Worksheets.Add("Sheet1");
  for (int ro = 1; ro <= 1000000; ro++)
  {
    // Dispose of the row once we're done with it
    using(var row = ws.Row(ro))
    row.FirstCell().Value = ro;
  }
}
```

**Not so good:**  
```c#
var wb = new XLWorkbook();
for (int wsNum = 1; wsNum <= 10; wsNum++)
{
  var ws = wb.Worksheets.Add("Sheet" + wsNum);

  // Add stuff to the worksheet...
}
```

**Best way:**  
```c#
using (var wb = new XLWorkbook())
{
  for (int wsNum = 1; wsNum <= 10; wsNum++)
  {
    // Dispose the worksheet right away
    // (Don't wait for the workbook to do so)
    using (var ws = wb.Worksheets.Add("Sheet" + wsNum))
    {
      // Add stuff to the worksheet...
    }
  }
}
```
