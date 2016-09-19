## Accessing Named Ranges

If you have one or more [Named Ranges](wikipage@title=Named%2520Ranges&referringTitle=Accessing%2520Named%2520Ranges.html) you can access them in different ways:

*   A specific range/cell in the named range

```c#
    // worksheet scope
    var range = worksheet.Range("NameOfTheRange");
    var cell = worksheet.Cell("NameOfTheRange");
    // workbook scope
    var range = workbook.Range("NameOfTheRange");
    var cell = workbook.Cell("NameOfTheRange");
```

*   All ranges/cells specified in the named range (yes a named range can point to many ranges/cells)

```c#
    // worksheet scope
    var ranges = worksheet.Ranges("NameOfTheRange");
    var cells = worksheet.Cells("NameOfTheRange");
    // workbook scope
    var ranges = workbook.Ranges("NameOfTheRange");
    var cells = workbook.Cells("NameOfTheRange");
```

**Worksheet scope from the workbook**
One handy way to access named ranges is to access worksheet's range from the workbook.
For example:

```c#
    var range = workbook.Range("Sheet1!Result");
    var cell = workbook.Cell("Sheet1!Result");
```

**Scope:**
If you ask for a named range in a worksheet then ClosedXML will look on the worksheet and then the workbook if it can't find it.

For example, after creating a named range with workbook scope you can access it from either the workbook or worksheet (as long as there isn't one on the worksheet already.

```c#
    // Create a range with workbook scope (the default)
    worksheet.RangeUsed().AddToNamed("Result");

    // Access it from the workbook:
    var range = workbook.Range("Result");
    // Access it from the worksheet:
    // What happens here is that it will try to get the named range
    // on the worksheet, when it fails it then gets the named range
    // on the workbook
    var range = worksheet.Range("Result");
```

**Can't find it?**
A null is returned if the named range doesn't exist.