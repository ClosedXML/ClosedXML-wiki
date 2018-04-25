***
NOTE: Pivot table support is still very experimental.
***

In this example, we'll create a pivot table of monthly pastry sales. First, we'll need our Pastry class:  
```c#
public class Pastry
{
  public Pastry(string name, int amount, string month)
  {
    Month = month;
    Name = name;
    NumberOfOrders = amount;
  }

  public string Name { get; set; }
  public int NumberOfOrders { get; set; }
  public string Month { get; set; }
}
```

Next, we'll mock up some data:  
```c#
var pastries = new List<Pastry>
{
  new Pastry("Croissant", 150, "Apr"),
  new Pastry("Croissant", 250, "May"),
  new Pastry("Croissant", 134, "June"),
  new Pastry("Doughnut", 250, "Apr"),
  new Pastry("Doughnut", 225, "May"),
  new Pastry("Doughnut", 210, "June"),
  new Pastry("Bearclaw", 134, "Apr"),
  new Pastry("Bearclaw", 184, "May"),
  new Pastry("Bearclaw", 124, "June"),
  new Pastry("Danish", 394, "Apr"),
  new Pastry("Danish", 190, "May"),
  new Pastry("Danish", 221, "June"),
  new Pastry("Scone", 135, "Apr"),
  new Pastry("Scone", 122, "May"),
  new Pastry("Scone", 243, "June")
};
```

And then we'll create a worksheet with this data in a table:  
```c#
var workbook = new XLWorkbook();
var sheet = workbook.Worksheets.Add("PastrySalesData");

// Insert our list of pastry data into the "PastrySalesData" sheet at cell 1,1
var table = sheet.Cell(1, 1).InsertTable(pastries, "PastrySalesData", true);
```

Finally, we'll use that table as the source for our pivot table:  
```c#

// Add a new sheet for our pivot table
var ptSheet = workbook.Worksheets.Add("PivotTable");

// Create the pivot table, using the data from the "PastrySalesData" table
var pt = ptSheet.PivotTables.AddNew("PivotTable", ptSheet.Cell(1, 1), table.AsRange());

// The rows in our pivot table will be the names of the pastries
pt.RowLabels.Add("Name");

// The columns will be the months
pt.ColumnLabels.Add("Month");

// The values in our table will come from the "NumberOfOrders" field
// The default calculation setting is a total of each row/column
pt.Values.Add("NumberOfOrders");
```

This will create a pivot table with a row for each pastry, a column for each month, and sales numbers in the cells. Each column and row will be totaled.  

![](http://i.imgur.com/4NWd705.jpg)
