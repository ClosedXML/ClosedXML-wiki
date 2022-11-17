When you set the .Value property of a cell, ClosedXML will call the .ToString() method of the object and proceed to interpret the value as a number, date, boolean, time stamp, or text.  

To insert a number as text you have the following options:  

1.  Use an apostrophe: `cell.Value = "**'**123"`;
2.  Use SetValue: `cell.SetValue("123"); // SetValue will not try to convert to the appropriate type.`
3.  Change the cell's data type to text after it has the numeric value: `cell.SetValue(123).SetDataType(XLDataType.Text);`
4.  Set the cell's format to "@" before setting the value: `cell.Style.NumberFormat.Format = "@"; cell.Value = "123";`

For more information see [Data Types](Data-Types)
