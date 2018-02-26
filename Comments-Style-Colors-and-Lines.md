![ColorsAndLines.jpg](images/Comments-Style-Colors-and-Lines_ColorsAndLines.jpg "ColorsAndLines.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Colors and Lines");

ws.Cell("A2").Comment
  .AddText("Now ")
  .AddText("THIS").SetBold().SetFontColor(XLColor.Red)
  .AddText(" is colorful!");

ws.Cell("A2").Comment.Style
  .ColorsAndLines.SetFillColor(XLColor.RichCarmine)
  .ColorsAndLines.SetFillTransparency(0.25) // 25% opaque
  .ColorsAndLines.SetLineColor(XLColor.Blue)
  .ColorsAndLines.SetLineTransparency(0.75) // 75% opaque
  .ColorsAndLines.SetLineDash(XLDashStyle.LongDash)
  .ColorsAndLines.SetLineStyle(XLLineStyle.ThickBetweenThin)
  .ColorsAndLines.SetLineWeight(7.5);

// Set all comments to visible
ws.CellsUsed(true, c => c.HasComment).ForEach(c => c.Comment.SetVisible());

wb.SaveAs("CommentsColorsAndLines.xlsx");
```
