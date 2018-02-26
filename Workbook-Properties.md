```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Workbook Properties");
```

**Predefined Properties:**  

![WorkbookProperties.jpg](images/Workbook-Properties_WorkbookProperties.jpg "WorkbookProperties.jpg")  

```c#
wb.Properties.Author = "theAuthor";
wb.Properties.Title = "theTitle";
wb.Properties.Subject = "theSubject";
wb.Properties.Category = "theCategory";
wb.Properties.Keywords = "theKeywords";
wb.Properties.Comments = "theComments";
wb.Properties.Status = "theStatus";
wb.Properties.LastModifiedBy = "theLastModifiedBy";
wb.Properties.Company = "theCompany";
wb.Properties.Manager = "theManager";
```

**Custom Properties:**  

![WorkbookProperties1.jpg](images/Workbook-Properties_WorkbookProperties1.jpg "WorkbookProperties1.jpg")  

```c#
wb.CustomProperties.Add("theText", "XXX");
wb.CustomProperties.Add("theDate", new DateTime(2011, 1, 1));
wb.CustomProperties.Add("theNumber", 123.456);
wb.CustomProperties.Add("theBoolean", true);
```

**Save Workbook:**  

```c#
wb.SaveAs("WorkbookProperties.xlsx");
```
