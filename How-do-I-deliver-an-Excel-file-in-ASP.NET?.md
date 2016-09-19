## How do I deliver an Excel file in ASP.NET?

This is, without a doubt, the single most asked question...

```c#
// Create the workbook
XLWorkbook workbook = new XLWorkbook();
workbook.Worksheets.Add("Sample").Cell(1, 1).SetValue("Hello World");

// Prepare the response
HttpResponse httpResponse = Response;
httpResponse.Clear();
httpResponse.ContentType = "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet";
httpResponse.AddHeader("content-disposition", "attachment;filename=\"HelloWorld.xlsx\"");

// Flush the workbook to the Response.OutputStream
using (MemoryStream memoryStream = new MemoryStream())
{
    workbook.SaveAs(memoryStream);
    memoryStream.WriteTo(httpResponse.OutputStream);
    memoryStream.Close();
}

httpResponse.End();
```