```c#
var wb = new XLWorkbook();

var dataTable = GetTable("Information");

// Add a DataTable as a worksheet
wb.Worksheets.Add(dataTable);

wb.SaveAs("AddingDataTableAsWorksheet.xlsx");

```

![AddingDataTableAsWorksheet.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=243019 "AddingDataTableAsWorksheet.jpg")  

```c#
private DataTable GetTable(String tableName)
{
  DataTable table = new DataTable();
  table.TableName = tableName;
  table.Columns.Add("Dosage", typeof(int));
  table.Columns.Add("Drug", typeof(string));
  table.Columns.Add("Patient", typeof(string));
  table.Columns.Add("Date", typeof(DateTime));

  table.Rows.Add(25, "Indocin", "David", DateTime.Now);
  table.Rows.Add(50, "Enebrel", "Sam", DateTime.Now);
  table.Rows.Add(10, "Hydralazine", "Christoff", DateTime.Now);
  table.Rows.Add(21, "Combivent", "Janet", DateTime.Now);
  table.Rows.Add(100, "Dilantin", "Melanie", DateTime.Now);
  return table;
}
```
