![Hello_World.jpg](images/Hello-World_Hello_World.jpg "Hello_World.jpg")  

```c#
var workbook = new XLWorkbook();
var worksheet = workbook.Worksheets.Add("Sample Sheet");
worksheet.Cell("A1").Value = "Hello World!";
workbook.SaveAs("HelloWorld.xlsx");
```
