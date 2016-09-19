## Evaluating Formulas

If you call cell.Value ClosedXML will try to resolve the formula and give you the result.

For example:

```c#
    var wb = new XLWorkbook();
    var ws = wb.AddWorksheet("Sheet1");
    ws.Cell("A1").SetValue(1).CellBelow().SetValue(1);
    ws.Cell("B1").SetValue(1).CellBelow().SetValue(1);
    ws.Cell("C1").FormulaA1 = "\"The total value is: \" & SUM(A1:B2)";
    var r = ws.Cell("C1").Value;
    Assert.AreEqual("The total value is: 4", r.ToString());
    // It also works if you use: ws.Cell("C1").GetString()
```

You can even resolve your own formulas without using cells. For Example:

If you're not referencing a worksheet you can use:

```c#
  var sum = XLWorkbook.EvaluateExpr("SUM(1,2,3)");
  // sum = 6
  // SUM(Sheet1!A1:B2) will fail because it doesn't know which workbook to use
```

If you're not referencing a range without a worksheet you can use:

```c#
  var sum = workbook.Evaluate("SUM(Sheet1!A1:B2)");
  // SUM(A1:B2) will fail because it doesn't know which sheet to use
```

If you have the worksheet you can evaluate at your heart's content:

```c#
  var sum = worksheet.Evaluate("SUM(A1:B2)");
```

## Very important:

*   Not all formulas are included and you'll probably get a nasty error if the formula isn't supported or if there's an error in the formula. Please test your formulas before going to production.
*   we are adding new formulas all the time but if your formula isn't included please let me know via the Issue Tracker. I'll do my best to include the formula asap.

## Supported functions

***
```c#
* ce.RegisterFunction("DATE", 3, Date); // Returns the serial number of a particular date
* ce.RegisterFunction("DATEVALUE", 1, Datevalue); // Converts a date in the form of text to a serial number
* ce.RegisterFunction("DAY", 1, Day); // Converts a serial number to a day of the month
* ce.RegisterFunction("DAYS360", 2, 3, Days360); // Calculates the number of days between two dates based on a 360-day year
* ce.RegisterFunction("EDATE", 2, Edate); // Returns the serial number of the date that is the indicated number of months before or after the start date
* ce.RegisterFunction("EOMONTH", 2, Eomonth); // Returns the serial number of the last day of the month before or after a specified number of months
* ce.RegisterFunction("HOUR", 1, Hour); // Converts a serial number to an hour
* ce.RegisterFunction("MINUTE", 1, Minute); // Converts a serial number to a minute
* ce.RegisterFunction("MONTH", 1, Month); // Converts a serial number to a month
* ce.RegisterFunction("NETWORKDAYS", 2, 3, Networkdays); // Returns the number of whole workdays between two dates
* ce.RegisterFunction("NOW", 0, Now); // Returns the serial number of the current date and time
* ce.RegisterFunction("SECOND", 1, Second); // Converts a serial number to a second
* ce.RegisterFunction("TIME", 3, Time); // Returns the serial number of a particular time
* ce.RegisterFunction("TIMEVALUE", 1, Timevalue); // Converts a time in the form of text to a serial number
* ce.RegisterFunction("TODAY", 0, Today); // Returns the serial number of today's date
* ce.RegisterFunction("WEEKDAY", 1, 2, Weekday); // Converts a serial number to a day of the week
* ce.RegisterFunction("WEEKNUM", 1, 2, Weeknum); // Converts a serial number to a number representing where the week falls numerically with a year
* ce.RegisterFunction("WORKDAY", 2, 3, Workday); // Returns the serial number of the date before or after a specified number of workdays
* ce.RegisterFunction("YEAR", 1, Year); // Converts a serial number to a year
* ce.RegisterFunction("YEARFRAC", 2, 3, Yearfrac); // Returns the year fraction representing the number of whole days between start_date and end_date
* ce.RegisterFunction("AND", 1, int.MaxValue, And);
* ce.RegisterFunction("OR", 1, int.MaxValue, Or);
* ce.RegisterFunction("NOT", 1, Not);
* ce.RegisterFunction("IF", 3, If);
* ce.RegisterFunction("TRUE", 0, True);
* ce.RegisterFunction("FALSE", 0, False);
* ce.RegisterFunction("ABS", 1, Abs);
* ce.RegisterFunction("ACOS", 1, Acos);
* ce.RegisterFunction("ACOSH", 1, Acosh);
* ce.RegisterFunction("ASIN", 1, Asin);
* ce.RegisterFunction("ASINH", 1, Asinh);
* ce.RegisterFunction("ATAN", 1, Atan);
* ce.RegisterFunction("ATAN2", 2, Atan2);
* ce.RegisterFunction("ATANH", 1, Atanh);
* ce.RegisterFunction("CEILING", 1, Ceiling);
* ce.RegisterFunction("COMBIN", 2, Combin);
* ce.RegisterFunction("COS", 1, Cos);
* ce.RegisterFunction("COSH", 1, Cosh);
* ce.RegisterFunction("DEGREES", 1, Degrees);
* ce.RegisterFunction("EVEN", 1, Even);
* ce.RegisterFunction("EXP", 1, Exp);
* ce.RegisterFunction("FACT", 1, Fact);
* ce.RegisterFunction("FACTDOUBLE", 1, FactDouble);
* ce.RegisterFunction("FLOOR", 1, Floor);
* ce.RegisterFunction("GCD", 1, 255, Gcd);
* ce.RegisterFunction("INT", 1, Int);
* ce.RegisterFunction("LCM", 1, 255, Lcm);
* ce.RegisterFunction("LN", 1, Ln);
* ce.RegisterFunction("LOG", 1, 2, Log);
* ce.RegisterFunction("LOG10", 1, Log10);
* ce.RegisterFunction("MDETERM", 1, MDeterm);
* ce.RegisterFunction("MINVERSE", 1, MInverse);
* ce.RegisterFunction("MMULT", 2, MMult);
* ce.RegisterFunction("MOD", 2, Mod);
* ce.RegisterFunction("MROUND", 2, MRound);
* ce.RegisterFunction("MULTINOMIAL", 1, 255, Multinomial);
* ce.RegisterFunction("ODD", 1, Odd);
* ce.RegisterFunction("PI", 0, Pi);
* ce.RegisterFunction("POWER", 2, Power);
* ce.RegisterFunction("PRODUCT", 1, 255, Product);
* ce.RegisterFunction("QUOTIENT", 2, Quotient);
* ce.RegisterFunction("RADIANS", 1, Radians);
* ce.RegisterFunction("RAND", 0, Rand);
* ce.RegisterFunction("RANDBETWEEN", 2, RandBetween);
* ce.RegisterFunction("ROMAN", 1, 2, Roman);
* ce.RegisterFunction("ROUND", 2, Round);
* ce.RegisterFunction("ROUNDDOWN", 2, RoundDown);
* ce.RegisterFunction("ROUNDUP", 1, 2, RoundUp);
* ce.RegisterFunction("SERIESSUM", 4, SeriesSum);
* ce.RegisterFunction("SIGN", 1, Sign);
* ce.RegisterFunction("SIN", 1, Sin);
* ce.RegisterFunction("SINH", 1, Sinh);
* ce.RegisterFunction("SQRT", 1, Sqrt);
* ce.RegisterFunction("SQRTPI", 1, SqrtPi);
* ce.RegisterFunction("SUBTOTAL", 2, 255, Subtotal);
* ce.RegisterFunction("SUM", 1, int.MaxValue, Sum);
* ce.RegisterFunction("SUMIF", 2, 3, SumIf);
* ce.RegisterFunction("SUMSQ", 1, 255, SumSq);
* ce.RegisterFunction("TAN", 1, Tan);
* ce.RegisterFunction("TANH", 1, Tanh);
* ce.RegisterFunction("TRUNC", 1, Trunc);
* ce.RegisterFunction("AVERAGE", 1, int.MaxValue, Average);
* ce.RegisterFunction("AVERAGEA", 1, int.MaxValue, AverageA);
* ce.RegisterFunction("COUNT", 1, int.MaxValue, Count);
* ce.RegisterFunction("COUNTA", 1, int.MaxValue, CountA);
* ce.RegisterFunction("COUNTBLANK", 1, int.MaxValue, CountBlank);
* ce.RegisterFunction("COUNTIF", 2, CountIf);
* ce.RegisterFunction("MAX", 1, int.MaxValue, Max);
* ce.RegisterFunction("MAXA", 1, int.MaxValue, MaxA);
* ce.RegisterFunction("MIN", 1, int.MaxValue, Min);
* ce.RegisterFunction("MINA", 1, int.MaxValue, MinA);
* ce.RegisterFunction("STDEV", 1, int.MaxValue, StDev);
* ce.RegisterFunction("STDEVA", 1, int.MaxValue, StDevA);
* ce.RegisterFunction("STDEVP", 1, int.MaxValue, StDevP);
* ce.RegisterFunction("STDEVPA", 1, int.MaxValue, StDevPA);
* ce.RegisterFunction("VAR", 1, int.MaxValue, Var);
* ce.RegisterFunction("VARA", 1, int.MaxValue, VarA);
* ce.RegisterFunction("VARP", 1, int.MaxValue, VarP);
* ce.RegisterFunction("VARPA", 1, int.MaxValue, VarPA);
* ce.RegisterFunction("ASC", 1, Asc); // Changes full-width (double-byte) English letters or katakana within a character string to half-width (single-byte) characters
* ce.RegisterFunction("CHAR", 1, _Char); // Returns the character specified by the code number
* ce.RegisterFunction("CLEAN", 1, Clean); // Removes all nonprintable characters from text
* ce.RegisterFunction("CODE", 1, Code); // Returns a numeric code for the first character in a text string
* ce.RegisterFunction("CONCATENATE", 1, int.MaxValue, Concat); // Joins several text items into one text item
* ce.RegisterFunction("DOLLAR", 1, 2, Dollar); // Converts a number to text, using the $ (dollar) currency format
* ce.RegisterFunction("EXACT", 2, Exact);
* ce.RegisterFunction("VLOOKUP", 4, Vlookup); // (new after 0.81.0) Looks in the first column of an array and moves across
* ce.RegisterFunction("HLOOKUP", 4, Hlookup); // (new after 0.81.0)Looks in the top row of an array and returns the value of the indicated cell

```