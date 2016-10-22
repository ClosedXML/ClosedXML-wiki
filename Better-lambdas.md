Consider providing a predicate to the Cells/Rows/Columns methods instead of asking for all the object and then applying a .Where to them.  

**Not so good:**  
```c#
foreach (var row in worksheet.RowsUsed().Where(r => r.FirstCell().GetString() == "A"))
{
  // Do something with the row...
}
```

**Best way:**  
```c#
using (var rows = worksheet.RowsUsed(r => r.FirstCell().GetString() == "A"))
{
  foreach (var row in rows)
  {
    // Do something with the row...
  }
}
```

**Not so good:**  
```c#
var column = range.Columns().First(c => c.FirstCell().GetString() == "A");
```

**Best way:**  
```c#
var column = range.FirstColumnUsed(c => c.FirstCell().GetString() == "A");
```
