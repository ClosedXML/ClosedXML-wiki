![Alignment.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=320482 "Alignment.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Alignment");

// Automagically adjust the size of the comment to fit the contents
ws.Cell("A1").Comment.Style.Alignment.SetAutomaticSize();
ws.Cell("A1").Comment.AddText("Things are pretty tight around here");

// Default values
ws.Cell("A3").Comment
  .AddText("Default Alignments:").AddNewLine()
  .AddText("Vertical = Top").AddNewLine()
  .AddText("Horizontal = Left").AddNewLine()
  .AddText("Orientation = Left to Right");

// Let's change the alignments
ws.Cell("A8").Comment
  .AddText("Vertical = Bottom").AddNewLine()
  .AddText("Horizontal = Right");
ws.Cell("A8").Comment.Style
  .Alignment.SetVertical(XLDrawingVerticalAlignment.Bottom)
  .Alignment.SetHorizontal(XLDrawingHorizontalAlignment.Right);

// And now the orientation...
ws.Cell("D3").Comment.AddText("Orientation = Bottom to Top");
ws.Cell("D3").Comment.Style
  .Alignment.SetOrientation(XLDrawingTextOrientation.BottomToTop)
  .Alignment.SetAutomaticSize();

ws.Cell("E3").Comment.AddText("Orientation = Top to Bottom");
ws.Cell("E3").Comment.Style
  .Alignment.SetOrientation(XLDrawingTextOrientation.TopToBottom)
  .Alignment.SetAutomaticSize();

ws.Cell("F3").Comment.AddText("Orientation = Vertical");
ws.Cell("F3").Comment.Style
  .Alignment.SetOrientation(XLDrawingTextOrientation.Vertical)
  .Alignment.SetAutomaticSize();

// Set all comments to visible
ws.CellsUsed(true, c => c.HasComment).ForEach(c => c.Comment.SetVisible());

wb.SaveAs("CommentsAlignment.xlsx");
```
