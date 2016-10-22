![Position.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=320480 "Position.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Position");

ws.Columns().Width = 10;

ws.Cell("A1").Comment.AddText("This is an unusual place for a comment...");
ws.Cell("A1").Comment.Position
  .SetColumn(3) // Starting from the third column
  .SetColumnOffset(5) // The comment will start in the middle of the third column
  .SetRow(5) // Starting from the fifth row
  .SetRowOffset(7.5); // The comment will start in the middle of the fifth row

// Set all comments to visible
ws.CellsUsed(true, c => c.HasComment).ForEach(c => c.Comment.SetVisible());

wb.SaveAs("CommentsPosition.xlsx");
```
