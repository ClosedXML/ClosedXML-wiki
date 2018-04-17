1. `IXLWorksheet.AddPicture` - add a picture to a worksheet
2. `IXLPicture.MoveTo` - move the picture where you want it to be

```c#
using (var wb = new XLWorkbook())
{
  var ws = wb.AddWorksheet("Sheet1");

  var imagePath = @"c:\path\to\your\image.jpg";

  var image = ws.AddPicture(ImageLocation)
      .MoveTo(ws.Cell("B3").Address)
      .Scale(0.5); // optional: resize picture
      
  wb.SaveAs("file.xlsx");
}
```

The ability to add pictures was added in v0.88 of ClosedXML