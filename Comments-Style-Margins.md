![Margins.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=320487 "Margins.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Margins");

ws.Cell("A2").Comment
  .SetVisible()
  .AddText("Lorem ipsum dolor sit amet, adipiscing elit. ").AddNewLine()
  .AddText("Nunc elementum, sapien a ultrices, commodo nisl. ").AddNewLine()
  .AddText("Consequat erat lectus a nisi. Aliquam facilisis.");

ws.Cell("A2").Comment.Style
  .Margins.SetAll(0.25)
  .Size.SetAutomaticSize();

wb.SaveAs("CommentsMargins.xlsx");
```
