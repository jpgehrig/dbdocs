This appendix lists the Entity Framework canonical functions and the corresponding ODP.NET provider functions to which they map.

### Aggregate Canonical Functions

Table B-1 Mapping of Aggregate Canonical Functions and Oracle Functions

| Canonical Function            | Oracle Function          |
|:------------------------------|:-------------------------|
| `Avg (` `expression` `)`      | `AVG(``expression``)`    |
| `BigCount ( ``expression` `)` | `COUNT(``expression``)`  |
| `Count ( ``expression`` )`    | `COUNT(``expression``)`  |
| `Max (` `expression` `)`      | `MAX(``expression``)`    |
| `Min ( ``expression` `)`      | `MIN(``expression``)`    |
| `StDev (` `expression` `)`    | `STDDEV(``expression``)` |
| `StDevP( ``expression``)`     | `STDEVP(``expression``)` |
| `Sum (` `expression` `)`      | `SUM` `(``expression``)` |
| `Var(``expression``)`         | `VAR(``expression``)`    |
| `VarP(``expression``)`        | `VARP(``expression``)`   |

### Math Canonical Functions

Table B-2 Mapping of Math Canonical Functions and Oracle Functions

| Canonical Function                | Oracle Function                |
|:----------------------------------|:-------------------------------|
| `Abs (` `value` `)`               | `ABS (``value``)`              |
| `Ceiling (` `value` `)`           | `CEIL(``value``)`              |
| `Floor (` `value` `)`             | `FLOOR(``value``)`             |
| `Power(``value``,` `exponent``)`  | `POWER(``value`, `exponent``)` |
| `Round (` `value` `)`             | `ROUND(``value``)`             |
| `Round (` `value``,` `digits` `)` | `ROUND(``value`, `digits``)`   |
| `Truncate(``value``,` `digits``)` | `TRUNC(``value`, `digits``)`   |

### String Canonical Functions

Table B-3 Mapping of String Canonical Functions and Oracle Functions

| Canonical Function                                   | Oracle Function                                                                                                            |
|:-----------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| `Concat (` `string1`, `string2``)`                   | `CONCAT(``string1`, `string2``)`<br>or<br>`( (``string1``) || (``string2``))`                                              |
| `Contains(``string`, `target``)`                     | `INSTR(``string``,` `target``)`                                                                                            |
| `EndsWith(``string`, `target``)`                     | `INSTR(REVERSE(``string``), REVERSE(``target``))`                                                                          |
| Comparison operators<br>`(``<, <=, >, >=, <>, !=``)` | Comparison operators<br>`(<, <=, >, >=, <>, !=)`                                                                           |
| `IndexOf(` `target``,` `string``)`                   | `INSTR(``string2``,` `target``)`                                                                                           |
| `Left ( ``string1``,` `length``)`                    | `SUBSTR(``string1``,` `length``)`                                                                                          |
| `Length (` `string` `)`                              | `LENGTH(``string``)`                                                                                                       |
| `LTrim(` `string` `)`                                | `LTRIM(``string``)`                                                                                                        |
| `Replace (` `string1``,` `string2``,` `string3``)`   | `REPLACE(``string1``,` `string2``,` `string3``)`                                                                           |
| `Reverse (` `string` `)`                             | `REVERSE(`string`)`                                                                                                        |
| `Right ( ``string``,` `length``)`                    | `(CASE WHEN LENGTH(``string``) >= (``length``) THEN SUBSTR (``string``) ,-(``length``),` `length` `) ELSE ``string` `END)` |
| `RTrim(` `string` `)`                                | `RTRIM(``string``)`                                                                                                        |
| `Substring (` `string``,` `start``,` `length``)`     | `SUBSTR(( ``string``,` `start``,` `length``)`                                                                              |
| `StartsWith(``string`, `target``)`                   | `INSTR(``string, ``target``)`                                                                                              |
| `ToLower (` `string` `)`                             | `LOWER(``string``)`                                                                                                        |
| `ToUpper(` `string` `)`                              | `UPPER`                                                                                                                    |
| `Trim ( ``string` `)`                                | `LTRIM(RTRIM(``string``))`                                                                                                 |

### Date And Time Canonical Functions

Table B-4 Mapping of Date And Time Canonical Functions and Oracle Functions

| Canonical Function                                                                                   | Oracle Function                                                                                                                          |
|:-----------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| `AddNanoseconds(``expression``,` `number``)`                                                         | `(``expression``) + INTERVAL`                                                                                                            |
| `AddMicroseconds(``expression``,` `number``)`                                                        | `(``expression``) + INTERVAL`                                                                                                            |
| `AddMilliseconds(``expression``,` `number``)`                                                        | `(``expression``) + INTERVAL`                                                                                                            |
| `AddSeconds(``expression``,` `number``)`                                                             | `(``expression``) + INTERVAL`                                                                                                            |
| `AddMinutes(``expression``,` `number``)`                                                             | `(``expression``) + INTERVAL`                                                                                                            |
| `AddHours(``expression``,` `number``)`                                                               | `(``expression``) + INTERVAL`                                                                                                            |
| `AddDays(``expression``,` `number``)`                                                                | `(``expression``) + INTERVAL`                                                                                                            |
| `AddMonths(``expression``,` `number``)`                                                              | `(``expression``) + INTERVAL`                                                                                                            |
| `AddYears(``expression``,` `number``)`                                                               | `(``expression``) + INTERVAL`                                                                                                            |
| `CreateDateTime(``year``,` `month``,` `day``,` `hour``,` `minute``,` `second``)`                     | `TO_TIMESTAMP`                                                                                                                           |
| `CreateDateTimeOffset(``year``,` `month``,` `day``,` `hour``,` `minute``,` `second``,` `tzoffset``)` | `TO_TIMESTAMP_TZ`                                                                                                                        |
| `CreateTime(``hour``,` `minute``,` `second``)`                                                       | Time literals are not supported in Oracle                                                                                                |
| `CurrentDateTime()`                                                                                  | `LOCALTIMESTAMP`                                                                                                                         |
| `CurrentDateTimeOffset()`                                                                            | `SYSTIMESTAMP`                                                                                                                           |
| `CurrentUtcDateTime()`                                                                               | `SYS_EXTRACT_UTC`<br>`(``LOCALTIMESTAMP``)`                                                                                              |
| `Day(``expression``)`                                                                                | `EXTRACT(DAY FROM ``expression``)`                                                                                                       |
| `DayOfYear(``expression``)`                                                                          | `TO_NUMBER(TO_CHAR(CAST(``expression` `AS TIMESTAMP), 'DDD'))`                                                                           |
| `DiffNanoseconds(``startExpression`, `endExpression``)`                                              | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffMilliseconds(``startExpression``,` `endExpression``)`                                           | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffMicroseconds(``startExpression``,` `endExpression``)`                                           | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffSeconds(``startExpression``,` `endExpression``)`                                                | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffMinutes(``startExpression``,` `endExpression``)`                                                | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffHours(``startExpression``,` `endExpression``)`                                                  | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffDays(``startExpression``,` `endExpression``)`                                                   | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffMonths(``startExpression``,` `endExpression``)`                                                 | `EXTRACT` and arithmetic operations                                                                                                      |
| `DiffYears(``startExpression``,` `endExpression`<br>`)`                                              | `EXTRACT` and arithmetic operations                                                                                                      |
| Comparison operators<br>`(<, <=, >, >=, <>, !=)`                                                     | `<, <=, >, >=, <>, !=` operators                                                                                                         |
| `GetTotalOffsetMinutes ( ``datetimeoffset` `)`                                                       | `(EXTRACT(TIMEZONE_HOUR FROM (``expression``))) * 60 + EXTRACT (TIMEZONE_MINUTE FROM(``expression``))`<br>(Require multiple operations.) |
| `Hour (``expression``)`                                                                              | `EXTRACT(HOUR FROM ``expression``)`                                                                                                      |
| `Millisecond(``expression``)`                                                                        | `NVL(TO_NUMBER(SUBSTR(TO_CHAR(CAST(``expression` `AS TIMESTAMP), 'DD-`<br>`MON-RR HH24:MI:SSXFF'), 20, 3)), 0)`                          |
| `Minute(``expression``)`                                                                             | `EXTRACT(MINUTE FROM` `expression``)`                                                                                                    |
| `Month (``expression``)`                                                                             | `EXTRACT(MONTH FROM` `expression``)`                                                                                                     |
| `Second(``expression``)`                                                                             | `EXTRACT (SECOND FROM` `expression``)`                                                                                                   |
| `TruncateDate(``expression``)`                                                                       | `TRUNC(``expression``)`                                                                                                                  |
| `Year(``expression``)`                                                                               | `EXTRACT(YEAR FROM` `expression``)`                                                                                                      |

### Bitwise Canonical Functions

Table B-5 Mapping of Bitwise Canonical Functions and Oracle Functions

| Canonical Function                       | Oracle Function                                            |
|:-----------------------------------------|:-----------------------------------------------------------|
| `BitWiseAnd (` `value1` , `value2` `)`   | `BITAND(``value1`, `value2``)`                             |
| `BitWiseNot (` `value` `)`               | `( 0 - ``value``) - 1`                                     |
| `BitWiseOr (` `value1` `,` `value2` `)`  | `Value1` - `BITAND(``value1``,` `value2``) + ``value2`     |
| `BitWiseXor ( ``value1` `,` `value2` `)` | `Value1` `- 2 * BITAND(``value1``,` `value2``) + ``value2` |

### Other Canonical Functions

Table B-6 Mapping of Other Canonical Functions and Oracle Functions

| Canonical Function | Oracle Function |
|:-------------------|:----------------|
| `NewGuid()`        | `SYS_GUID`      |
