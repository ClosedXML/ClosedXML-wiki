![Properties.jpg](images/Comments-Style-Properties_Properties.jpg "Properties.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Properties");

ws.Cell("A1").Comment.Style.Properties.Positioning = XLDrawingAnchor.Absolute;
ws.Cell("A2").Comment.Style.Properties.Positioning = XLDrawingAnchor.MoveAndSizeWithCells;
ws.Cell("A3").Comment.Style.Properties.Positioning = XLDrawingAnchor.MoveWithCells;

wb.SaveAs("CommentsProperties.xlsx");
```
