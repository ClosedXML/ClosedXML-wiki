## Set the active cell

```c#
var wb = new XLWorkbook();
var wsActiveCell = wb.AddWorksheet("Set Active Cell");
wsActiveCell.Cell("B2").SetActive();
```

![SelectCell.jpg](images/Selecting-Cells-and-Ranges_SelectCell.jpg "SelectCell.jpg")  

## Select cells and ranges

```c#
var wsSelectMisc = wb.AddWorksheet("Select Misc");
wsSelectMisc.Cell("B2").Select();
wsSelectMisc.Range("D2:E2").Select();
wsSelectMisc.Ranges("C3, D4:E5").Select();
```

![SelectRanges.jpg](images/Selecting-Cells-and-Ranges_SelectRanges.jpg "SelectRanges.jpg")  
