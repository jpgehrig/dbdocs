## ROUND and TRUNC Date Functions

Table 7-13 lists the format models you can use with the `ROUND` and `TRUNC` date functions and the units to which they round and truncate dates. The default model, 'DD', returns the date rounded or truncated to the day with a time of midnight.

Table 7-13 Date Format Models for the ROUND and TRUNC Date Functions

| Format Model                                                   | Rounding or Truncating Unit                                                                                     |
|:---------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------|
| `CC`<br>`SCC`                                                  | One greater than the first two digits of a four-digit year                                                      |
| `SYYYY`<br>`YYYY`<br>`YEAR`<br>`SYEAR`<br>`YYY`<br>`YY`<br>`Y` | Year (rounds up on July 1)                                                                                      |
| `IYYY`<br>`IY`<br>`IY`<br>`I`                                  | Year containing the calendar week, as defined by the ISO 8601 standard                                          |
| `Q`                                                            | Quarter (rounds up on the sixteenth day of the second month of the quarter)                                     |
| `MONTH`<br>`MON`<br>`MM`<br>`RM`                               | Month (rounds up on the sixteenth day)                                                                          |
| `WW`                                                           | Same day of the week as the first day of the year                                                               |
| `IW`                                                           | Same day of the week as the first day of the calendar week as defined by the ISO 8601 standard, which is Monday |
| `W`                                                            | Same day of the week as the first day of the month                                                              |
| `DDD`<br>`DD`<br>`J`                                           | Day                                                                                                             |
| `DAY`<br>`DY`<br>`D`                                           | Starting day of the week                                                                                        |
| `HH`<br>`HH12`<br>`HH24`                                       | Hour                                                                                                            |
| `MI`                                                           | Minute                                                                                                          |

The starting day of the week used by the format models DAY, DY, and D is specified implicitly by the initialization parameter `NLS_TERRITORY`.

**See Also:**

[Oracle Database Reference](../refrn/NLS_TERRITORY.md) and [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for information on this parameter
