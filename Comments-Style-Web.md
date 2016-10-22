![Web.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=320488 "Web.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Web");

ws.Cell("A1").Comment.Style.Web.AlternateText = "The alternate text in case you need it.";

wb.SaveAs("CommentsWeb.xlsx");
```
