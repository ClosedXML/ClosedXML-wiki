![Size.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=320484 "Size.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Size");

// Automatic size is a copy of the property comment.Style.Alignment.AutomaticSize
// I created the duplicate because it makes more sense for it to be in Size
// but Excel has it under the Alignment tab.
ws.Cell("A2").Comment.AddText("Things are very tight around here.");
ws.Cell("A2").Comment.Style.Size.SetAutomaticSize();

ws.Cell("A4").Comment.AddText("Different size");
ws.Cell("A4").Comment.Style
  .Size.SetHeight(30) // The height is set in the same units as row.Height
  .Size.SetWidth(30); // The width is set in the same units as row.Width

// Set all comments to visible
ws.CellsUsed(true, c => c.HasComment).ForEach(c => c.Comment.SetVisible());

wb.SaveAs("CommentsSize.xlsx");
```
