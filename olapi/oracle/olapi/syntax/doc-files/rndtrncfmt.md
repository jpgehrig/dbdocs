Skip navigation links

<table class="oac_no_warn" data-border="0" data-cellpadding="1" data-cellspacing="0" data-summary="Layout table... probably." width="100%">
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="text-align: right;" data-valign="top"><em><strong>Oracle® OLAP Java API Reference<br />
19c</strong><br />
E96404-01<br />
</em></td>
</tr>
</tbody>
</table>

# Formats for the Input Parameter for the round and trunc Methods

The following table lists the format models you can use with either the `round` or `trunc` method when you call that method on a `TypedExpression` that has a date value. The default model, 'DD', results in the date rounded or truncated to the day with a time of midnight.

**Input Parameter Format Models for the round and trunc Date Methods**

| Format Model                                                   | Rounding or Truncating Unit                                                 |
|:---------------------------------------------------------------|:----------------------------------------------------------------------------|
| `CC`<br>`SCC`                                                  | One greater than the first two digits of a four-digit year                  |
| `SYYYY`<br>`YYYY`<br>`YEAR`<br>`SYEAR`<br>`YYY`<br>`YY`<br>`Y` | Year (rounds up on July 1)                                                  |
| `IYYY`<br>`IY`<br>`IY`<br>`I`                                  | ISO Year                                                                    |
| `Q`                                                            | Quarter (rounds up on the sixteenth day of the second month of the quarter) |
| `MONTH`<br>`MON`<br>`MM`<br>`RM`                               | Month (rounds up on the sixteenth day)                                      |
| `WW`                                                           | Same day of the week as the first day of the year                           |
| `IW`                                                           | Same day of the week as the first day of the ISO year                       |
| `W`                                                            | Same day of the week as the first day of the month                          |
| `DDD`<br>`DD`<br>`J`                                           | Day                                                                         |
| `DAY`<br>`DY`<br>`D`                                           | Starting day of the week                                                    |
| `HH`<br>`HH12`<br>`HH24`                                       | Hour                                                                        |
| `MI`                                                           | Minute                                                                      |

The starting day of the week used by the format models DAY, DY, and D is specified implicitly by the Oracle Database initialization parameter `NLS_TERRITORY`.

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
