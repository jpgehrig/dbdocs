<table class="oac_no_warn" data-border="0" data-cellpadding="1" data-cellspacing="0" data-summary="Layout table... probably." width="100%">
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Overview </td>
<td style="text-align: right;" data-valign="top"><em><strong>Oracle® OLAP Java API Reference<br />
19c</strong><br />
E96404-01</em></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

**Possible Data Types Returned by getSQLDataType**

| Automatic Changing<br>of Data Type<br>Is Allowed | Attribute or<br>Measure Is<br>Mapped | SQL Data Type<br>Is Specified | Data Type           |
|:------------------------------------------------:|:------------------------------------:|:-----------------------------:|---------------------|
|                       Yes                        |                 Yes                  |              Yes              | Mapped data type    |
|                       Yes                        |                 Yes                  |              No               | Mapped data type    |
|                       Yes                        |                  No                  |              Yes              | Specified data type |
|                       Yes                        |                  No                  |              No               | Default data type   |
|                        No                        |                 Yes                  |              Yes              | Specified data type |
|                        No                        |                 Yes                  |              No               | Mapped data type    |
|                        No                        |                  No                  |              Yes              | Specified data type |
|                        No                        |                  No                  |              No               | Default data type   |

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
