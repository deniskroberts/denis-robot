# OA Robot Definitions

**Denis Robot.xlsx** contains definitions for:

[4 Robot Commands](#command-definitions)  
[5 Robot Texts](#text-definitions)  

  

## Available Robot Commands

| Name | Description |
| --- | --- |
| [Ordinal Date](#ordinal-date) | Convert dates into long format including the ordinal suffixes "th", "st", "nd" and "rd" |
| [Ordinal Number](#ordinal-number) | Convert selected numbers to text including the ordinal suffixes "th", "st", "nd" and "rd" |
| [Ordinal Suffix](#ordinal-suffix) | Get the Ordinal suffixes (st, nd, rd, th) for selected numbers |
| [Show Formulas](#show-formulas) | Apply ShowFormulas lambda function to active cell. |

  

## Available Robot Texts

| Name | Description |
| --- | --- |
| [GetOrdinalSuffix.lambda](#getordinalsuffix.lambda) | Definition of GetOrdinalSuffix lambda function. |
| [OrdinalDate.lambda](#ordinaldate.lambda) | Definition of OrdinalDate lambda function. |
| [OrdinalNumber.lambda](#ordinalnumber.lambda) | Definition of OrdinalNumber lambda function. |
| [OrdinalSuffix.lambda](#ordinalsuffix.lambda) | Definition of OrdinalSuffix lambda function. |
| [ShowFormulas.lambda](#showformulas.lambda) | Definition of ShowFormulas lambda function. |

  

## Command Definitions

  

### Ordinal Date

*Convert dates into long format including the ordinal suffixes "th", "st", "nd" and "rd"*

`@Denis Robot.xlsx` `!Excel Formula Command`  

| Property | Value |
| --- | --- |
| Formula | ``` =OrdinalDate([[ActiveCell::Formula]]) ``` |
| Formula Dependencies | 1. [OrdinalDate.lambda](#ordinaldate.lambda) 2. [GetOrdinalSuffix.lambda](#getordinalsuffix.lambda) |

[^Top](#oa-robot-definitions)

  

### Ordinal Number

*Convert selected numbers to text including the ordinal suffixes "th", "st", "nd" and "rd"*

`@Denis Robot.xlsx` `!Excel Formula Command`  

| Property | Value |
| --- | --- |
| Formula | ``` =OrdinalNumber([[ActiveCell::Formula]]) ``` |
| Formula Dependencies | 1. [OrdinalNumber.lambda](#ordinalnumber.lambda) 2. [OrdinalSuffix.lambda](#ordinalsuffix.lambda) |

[^Top](#oa-robot-definitions)

  

### Ordinal Suffix

*Get the Ordinal suffixes (st, nd, rd, th) for selected numbers*

`@Denis Robot.xlsx` `!Excel Formula Command`  

| Property | Value |
| --- | --- |
| Formula | ``` =OrdinalSuffix([[Selection]]) ``` |

[^Top](#oa-robot-definitions)

  

### Show Formulas

*Apply ShowFormulas lambda function to active cell.*

`@Denis Robot.xlsx` `!Excel Formula Command`  

| Property | Value |
| --- | --- |
| Formula | ``` =ShowFormulas([[ActiveCell::Formula]]) ``` |
| Formula Dependencies | [ShowFormulas.lambda](#showformulas.lambda) |

[^Top](#oa-robot-definitions)

  

## Text Definitions

  

### GetOrdinalSuffix.lambda

*Definition of GetOrdinalSuffix lambda function.*

`@Denis Robot.xlsx` `!Excel Name Text`  

| Property | Value |
| --- | --- |
| Text | [GetOrdinalSuffix.lambda](./Text/GetOrdinalSuffix.lambda.txt) |
| Value | Could not fully resolve Location: [GetOrdinalSuffix] Range Name: [GetOrdinalSuffix] |
| Content Type | ExcelFormula |
| Location | ``` GetOrdinalSuffix ``` |

[^Top](#oa-robot-definitions)

  

### OrdinalDate.lambda

*Definition of OrdinalDate lambda function.*

`@Denis Robot.xlsx` `!Excel Name Text`  

| Property | Value |
| --- | --- |
| Text | [OrdinalDate.lambda](./Text/OrdinalDate.lambda.txt) |
| Value | ``` /*Convert any date or range of date values into a date in long format, including "th" suffixes. */ OrdinalDate = LAMBDA(dates, LET( \\LambdaName, "OrdinalDate", \\CommandName, "Ordinal Date", \\Description, "Convert any date or range of date values into a date in long format, including ""th"" suffixes", TEXT(dates, "dddd d") & OrdinalSuffix(DAY(dates)) & TEXT(dates, " mmmm yyyy") )); ``` |
| Content Type | ExcelFormula |
| Location | ``` OrdinalDate ``` |

[^Top](#oa-robot-definitions)

  

### OrdinalNumber.lambda

*Definition of OrdinalNumber lambda function.*

`@Denis Robot.xlsx` `!Excel Name Text`  

| Property | Value |
| --- | --- |
| Text | [OrdinalNumber.lambda](./Text/OrdinalNumber.lambda.txt) |
| Value | ``` OrdinalNumber = LAMBDA(number, LET(\\LambdaName, "MakeOrdinalNumber", number & OrdinalSuffix(number))); ``` |
| Content Type | ExcelFormula |
| Location | ``` OrdinalNumber ``` |

[^Top](#oa-robot-definitions)

  

### OrdinalSuffix.lambda

*Definition of OrdinalSuffix lambda function.*

`@Denis Robot.xlsx` `!Excel Name Text`  

| Property | Value |
| --- | --- |
| Text | [OrdinalSuffix.lambda](./Text/OrdinalSuffix.lambda.txt) |
| Value | ``` OrdinalSuffix = LAMBDA(number, LET( \\LambdaName, "OrdinalSuffix", IF( (MOD(number, 100) > 10) * (MOD(number, 100) < 14), "th", SWITCH(MOD(number, 10), 1, "st", 2, "nd", 3, "rd", "th") ) )); ``` |
| Content Type | ExcelFormula |
| Location | ``` OrdinalSuffix ``` |

[^Top](#oa-robot-definitions)

  

### ShowFormulas.lambda

*Definition of ShowFormulas lambda function.*

`@Denis Robot.xlsx` `!Excel Name Text`  

| Property | Value |
| --- | --- |
| Text | [ShowFormulas.lambda](./Text/ShowFormulas.lambda.txt) |
| Value | ``` ShowFormulas = LAMBDA(Reference, LET( \\LambdaName, "ShowFormulas", \\CommandName, "Show Formulas", c, Reference, f, TOCOL(ADDRESS(ROW(c), COLUMN(c), 4) & ": " & FORMULATEXT(c), 3), r, DROP(REDUCE({""}, f, LAMBDA(s,x, VSTACK(s, TEXTSPLIT(x, , " ")))), 1), r )); ``` |
| Content Type | ExcelFormula |
| Location | ``` ShowFormulas ``` |

[^Top](#oa-robot-definitions)
