```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Data Validation");
```

**Decimal between 1 and 5**  

[image:DataValidation1.jpg]  

```c#
ws.Cell(1, 1).DataValidation.Decimal.Between(1, 5);
```

**Whole number equals 2, use an error message**  

[image:DataValidation2.jpg]  

```c#
var dv1 = ws.Range("A2:A3").DataValidation;
dv1.WholeNumber.EqualTo(2);

dv1.ErrorStyle = XLErrorStyle.Warning;
dv1.ErrorTitle = "Number out of range";
dv1.ErrorMessage = "This cell only allows the number 2.";
```

**Date after the millenium, use an input message**  

[image:DataValidation3.jpg] [image:DataValidation5.jpg]  

```c#
var dv2 = ws.Cell("A4").DataValidation;
dv2.Date.EqualOrGreaterThan(new DateTime(2000, 1, 1));

dv2.InputTitle = "Can't party like it's 1999.";
dv2.InputMessage = "Please enter a date in this century.";
```

**From a list**  

[image:DataValidation4.jpg]  

```c#
ws.Cell("C1").Value = "Yes";
ws.Cell("C2").Value = "No";
ws.Cell("A5").DataValidation.List(ws.Range("C1:C2"));
```
