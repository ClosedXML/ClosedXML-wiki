## Hello World

![Hello_World.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=147085 "Hello_World.jpg")  

```c#
var workbook = new XLWorkbook();
var worksheet = workbook.Worksheets.Add("Sample Sheet");
worksheet.Cell("A1").Value = "Hello World!";
workbook.SaveAs("HelloWorld.xlsx");
```
