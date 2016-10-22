## Conditional Formatting

**Range of numbers**  

![cfRange.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=363983 "cfRange.jpg")  
```c#
var workbook = new XLWorkbook();
var ws = workbook.AddWorksheet("Sheet1");

ws.FirstCell().SetValue(1)
  .CellBelow().SetValue(1)
  .CellBelow().SetValue(2)
  .CellBelow().SetValue(3)
  .CellBelow().SetValue(4);

ws.RangeUsed().AddConditionalFormat().WhenBetween(2, 3)
  .Fill.SetBackgroundColor(XLColor.Red);

```

**Color Scale**  

![cfColorScale.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=363980 "cfColorScale.jpg")  
```
var workbook = new XLWorkbook();
var ws = workbook.AddWorksheet("Sheet1");

ws.FirstCell().SetValue(1)
  .CellBelow().SetValue(1)
  .CellBelow().SetValue(2)
  .CellBelow().SetValue(3)
  .CellBelow().SetValue(4);

ws.RangeUsed().AddConditionalFormat().ColorScale()
  .LowestValue(XLColor.Red)
  .Midpoint(XLCFContentType.Percent, 50, XLColor.Yellow)
  .HighestValue(XLColor.Green);
```

![cfIconSet.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=363982 "cfIconSet.jpg")  
```
var workbook = new XLWorkbook();
var ws = workbook.AddWorksheet("Sheet1");

ws.FirstCell().SetValue(1)
  .CellBelow().SetValue(1)
  .CellBelow().SetValue(2)
  .CellBelow().SetValue(3)
  .CellBelow().SetValue(4);

ws.RangeUsed().AddConditionalFormat().IconSet(XLIconSetStyle.ThreeTrafficLights2)
  .AddValue(XLCFIconSetOperator.EqualOrGreaterThan, 0, XLCFContentType.Number)
  .AddValue(XLCFIconSetOperator.EqualOrGreaterThan, 2, XLCFContentType.Number)
  .AddValue(XLCFIconSetOperator.EqualOrGreaterThan, 3, XLCFContentType.Number);
```

![cfDataBar.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=363981 "cfDataBar.jpg")  
```
var workbook = new XLWorkbook();
var ws = workbook.AddWorksheet("Sheet1");

ws.FirstCell().SetValue(1)
  .CellBelow().SetValue(1)
  .CellBelow().SetValue(2)
  .CellBelow().SetValue(3)
  .CellBelow().SetValue(4);

ws.RangeUsed().AddConditionalFormat().DataBar(XLColor.Red)
  .LowestValue()
  .HighestValue();
```

**Using Formulas**  
Just put your match with an = sign. e.g.  
```c#
.AddConditionalFormat().WhenEquals("=B1")
```

If you need to start the string with an equal sign then put the entire string between quotes (`"\"=Hello\""`)  

