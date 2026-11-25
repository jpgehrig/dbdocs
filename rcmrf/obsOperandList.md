## 4.17 obsOperandList

### Purpose

Use the `obsOperandList` subclause used to specify which criteria are used to mark backups as obsolete.

### Usage Notes

Using both `RECOVERY WINDOW` and `REDUNDANCY` in a single `REPORT OBSOLETE` or `DELETE OBSOLETE` command is not supported.

### Syntax

obsOperandList::=

![Description of obsoperandlist.eps follows](img/obsoperandlist.gif)
[Description of the illustration obsoperandlist.eps](img_text/obsoperandlist.md)

### Semantics

obsOperandList

| Syntax Element                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:--------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `RECOVERY WINDOW OF` `integer` `DAYS` | Reports as obsolete those backup sets and image copies that are not needed to recover the database to any point within the last `integer` days.<br>See Also: [`CONFIGURE`](CONFIGURE.md) for an explanation of the recovery window                                                                                                                                                                                                                                                                                                                                             |
| `REDUNDANCY` `integer`                | Specifies the minimum level of redundancy considered necessary for a backup set or image copy to be obsolete.<br>A data file copy is obsolete if there are at least `integer` more recent backup sets or image copies of this file; a data file backup set is obsolete if there are at least `integer` more recent backup sets or image copies of each data file contained in the backup set. For example, `REDUNDANCY``2` means that there must be at least two more recent backup sets or image copies of a data file for any other backup set or image copy to be obsolete. |

### Example

Example 4-33 Deleting Obsolete Backups

The following command deletes all backups and copies not needed to recover the database to an SCN within the last 30 days:

    DELETE OBSOLETE RECOVERY WINDOW OF 30 DAYS;
