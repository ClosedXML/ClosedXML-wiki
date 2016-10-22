## Other performance improvements

*   Call cells with numbers instead of strings. e.g. `Cell(1, 1)` instead of `Cell("A1")`. The difference is negligible on small sheets but they add up when dealing with tens of thousands of cells.
*   Don't insert/delete rows/columns inside a loop. It's much faster to calculate the number of rows/columns you'll need to insert and do it in one shot. This is because every time you do an insert/delete the library has to recalculate all formulas.

