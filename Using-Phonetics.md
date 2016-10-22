![UsingPhonetics.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=253930 "UsingPhonetics.jpg")  

Phonetics are implemented as part of the Rich Text functionality. For more information see [Using Rich Text](Using-Rich-Text)  

```c#
var wb = new XLWorkbook();
var ws = wb.Worksheets.Add("Using Phonetics");

var cell = ws.Cell(1, 1);

// First we add the text.
cell.RichText.AddText("みんなさんはお元気ですか。").SetFontSize(16);

// And then we add the phonetics
cell.RichText.Phonetics.SetFontSize(8);
cell.RichText.Phonetics.Add("げん", 7, 1);
cell.RichText.Phonetics.Add("き", 8, 1);

wb.SaveAs("UsingPhonetics.xlsx");
```
