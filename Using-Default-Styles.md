## Using Default Styles

The XLWorkbook class has the following read-only static properties with the default information. Right now these options are hard coded, but in a future release I'll allow them to be defined in a config file.  

```c#
public static IXLStyle DefaultStyle { get; }
public static Double DefaultRowHeight { get; }
public static Double DefaultColumnWidth { get; }
public static IXLPageSetup DefaultPageOptions { get; }
```

The XLWorkbook and worksheet instances also have a similar set of properties which you can modify. In the case of a workbook these properties will be set to their defaults when you create a new workbook. All new worksheets will be initialized the style of the workbook.  

```c#
public IXLStyle Style { get; set; }
public Double RowHeight { get; set; }
public Double ColumnWidth { get; set; }
public IXLPageSetup PageOptions { get; set; }
```

**Example:**  

```c#
// The static default values are read-only so even if 
// you try to change a referenced type, the changes will be discarded.
var style = XLWorkbook.DefaultStyle;
style.Border.DiagonalUp = true;
style.Border.DiagonalDown = true;
style.Border.DiagonalBorder = XLBorderStyleValues.Thick;
style.Border.DiagonalBorderColor = XLColor.Red;

// Create our workbook
var workbook = new XLWorkbook();

// This worksheet will have the default style, row height, column width, and page setup
var ws1 = workbook.Worksheets.Add("Default Style");

// Change the default row height for all new worksheets in this workbook
workbook.RowHeight = 30;

var ws2 = workbook.Worksheets.Add("Tall Rows");

// Create a worksheet and change the default row height
var ws3 = workbook.Worksheets.Add("Short Rows");
ws3.RowHeight = 7.5;

workbook.SaveAs("DefaultStyles.xlsx");
```
