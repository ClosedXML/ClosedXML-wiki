![Web.jpg](images/Comments-Style-Web_Web.jpg "Web.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Web");

ws.Cell("A1").Comment.Style.Web.AlternateText = "The alternate text in case you need it.";

wb.SaveAs("CommentsWeb.xlsx");
```
