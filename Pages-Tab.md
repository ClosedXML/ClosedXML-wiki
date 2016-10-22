## Page Tab Example 1

![PageTab1.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=151899 "PageTab1.jpg")  

```c#
var workbook = new XLWorkbook();
var ws1 = workbook.Worksheets.Add("Page Setup - Page1");
ws1.PageSetup.PageOrientation = XLPageOrientation.Landscape;
ws1.PageSetup.AdjustTo(80);
ws1.PageSetup.PaperSize = XLPaperSize.LegalPaper;
ws1.PageSetup.VerticalDpi = 600;
ws1.PageSetup.HorizontalDpi = 600;
```

For more information on the paper size enumeration please see the [Paper Size Lookup Table](Paper-Size-Lookup-Table)  

## Page Tab Example 2

![PageTab2.jpg](http://download-codeplex.sec.s-msft.com/Download?ProjectName=closedxml&DownloadId=151898 "PageTab2.jpg")  

```c#
var ws2 = workbook.Worksheets.Add("Page Setup - Page2");
ws2.PageSetup.PageOrientation = XLPageOrientation.Portrait;
ws2.PageSetup.FitToPages(2, 2); // Alternatively you can use 
// ws2.PageSetup.PagesTall = #
// and/or ws2.PageSetup.PagesWide = #

ws2.PageSetup.PaperSize = XLPaperSize.LetterPaper;
ws2.PageSetup.VerticalDpi = 600;
ws2.PageSetup.HorizontalDpi = 600;
ws2.PageSetup.FirstPageNumber = 5;

workbook.SaveAs("PageTab.xlsx");
```

For more information on the paper size enumeration please see the [Paper Size Lookup Table](Paper-Size-Lookup-Table)