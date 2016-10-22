## Styles - Fill

![Styles_Fill.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=147905 "Styles_Fill.jpg")  

```c#
var workbook = new XLWorkbook();
var ws = workbook.Worksheets.Add("Style Fill");

var co = 2;
var ro = 1;

ws.Cell(++ro, co + 1).Value = "BackgroundColor = Red";
ws.Cell(ro, co).Style.Fill.BackgroundColor = XLColor.Red;

ws.Cell(++ro, co + 1).Value = "PatternType = DarkTrellis; PatternColor = Orange; PatternBackgroundColor = Blue";
ws.Cell(ro, co).Style.Fill.PatternType = XLFillPatternValues.DarkTrellis;
ws.Cell(ro, co).Style.Fill.PatternColor = XLColor.Orange;
ws.Cell(ro, co).Style.Fill.PatternBackgroundColor = XLColor.Blue;

workbook.SaveAs(Styles_Fill);
```
