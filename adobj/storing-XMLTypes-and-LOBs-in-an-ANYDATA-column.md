Beginning with Oracle Database 12c, you can use `ALTER` `TABLE` to store ADTs with `XMLTYPE`s and LOB attributes in `ANYDATA` columns. You can also do the same for standalone XMLTYPEs.

- Use the `modify_opaque_type` clause, which instructs the database to store these types unpacked. Otherwise, they cannot be stored in an `ANYDATA` column.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about `ALTER` `TABLE` used with the `modify_opaque_type` clause
