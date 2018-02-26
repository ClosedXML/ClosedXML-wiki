![Signatures.jpg](images/Comments-Signatures_Signatures.jpg "Signatures.jpg")  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Signatures");

// By default the signature will be with the logged user
// ws.Cell("A2").Comment.AddSignature().AddText("Hello World!");

// You can override this by specifying the comment's author:
ws.Cell("A2").Comment
  .SetAuthor("MDeLeon")
  .AddSignature()
  .AddText("Hello World!");

// Set all comments to visible
ws.CellsUsed(true, c => c.HasComment).ForEach(c => c.Comment.SetVisible());

wb.SaveAs("CommentsSignatures.xlsx");
```
