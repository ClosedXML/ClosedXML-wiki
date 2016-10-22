# Simplifying your life

Here's a list of a methods that will probably save you time and sanity. Please let us know in a discussion if there's anything we can do to make your life easier.  

## Ranges

Getting the first/last row/column/cell is a common task. Instead of specifying it manually you can use any of the following methods:  

```c#
range.FirstCell();
range.FirstCellUsed();
range.FirstColumn();
range.FirstColumnUsed();
range.FirstRow();
range.FirstRowUsed();

range.LastCell();
range.LastCellUsed();
range.LastColumn();
range.LastColumnUsed();
range.LastRow();
range.LastRowUsed();
```

You also don't have to calculate the range used, just use the following. You can also use it's overloads to specify whether you want to count formats as cells used.  

```c#
worksheet.RangeUsed();
```
