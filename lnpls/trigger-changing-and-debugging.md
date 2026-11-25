## 9.13 Trigger Changing and Debugging

To change a trigger, you must either replace or re-create it. (The `ALTER` `TRIGGER` statement only enables, disables, compiles, or renames a trigger.)

To replace a trigger, use the `CREATE` `TRIGGER` statement with the `OR` `REPLACE` clause.

To re-create a trigger, first drop it with the `DROP` `TRIGGER` statement and then create it again with the `CREATE` `TRIGGER` statement.

To debug a trigger, you can use the facilities available for stored subprograms. For information about these facilities, see [Oracle Database Development Guide](../adfns/coding-subprograms-and-packages.md).

**See Also:**

- "[CREATE TRIGGER Statement](CREATE-TRIGGER-statement.md)" for more information about the `CREATE` `TRIGGER` statement

- "[DROP TRIGGER Statement](DROP-TRIGGER-statement.md)" for more information about the `DROP` `TRIGGER` statement

- "[ALTER TRIGGER Statement](ALTER-TRIGGER-statement.md)" for more information about the `ALTER` `TRIGGER` statement
