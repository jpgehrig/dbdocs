Data in the rows of an object view may come from more than one table, but the object view still traverses the network in one operation. The instance appears in the client side object cache as a C or C++ structure or as a PL/SQL object variable. You can manipulate it like any other native structure.

You can refer to object views in SQL statements in the same way you refer to an object table. For example, object views can appear in a `SELECT` list, in an `UPDATE-SET` clause, or in a `WHERE` clause.

You can also define object views on object views.

You can access object view data on the client side using the same OCI calls you use for objects from object tables. For example, you can use `OCIObjectPin()` for [pinning](glossary.md) a `REF` and`OCIObjectFlush()` for flushing an object to the server. When you update or flush an object to the database in an object view, the database updates the object view.

**See Also:**

See [Oracle Call Interface Programmer's Guide](../lnoci/introduction.md) for more information about OCI calls.
