1. `IXLWorksheet.AddPicture` - add picture to worksheet
2. `IXLPicture.MoveTo` - move picture where you want it to be

``` csharp
void AddImage(XLWorkbook wb, string sheetName, int col, int row)
{
    if (!File.Exists(ImageLocation)) return;
    var ws = wb.Worksheet(sheetName);
    var image = ws.AddPicture(ImageLocation);
    image.MoveTo(ws.Cell(row, col).Address);
    image.Scale(.5); // optional: resize picture
    wb.Save();
}
```

Ability to add picture was added in v0.88