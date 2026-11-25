Usually, when an external procedure fails, its C prototype is faulty.

That is, the prototype does not match the one generated internally by PL/SQL. This can happen if you specify an incompatible C data type. For example, to pass an `OUT` parameter of type `REAL`, you must specify `float` `*`. Specifying `float`, `double` `*`, or any other C data type results in a mismatch.

In such cases, you get a `lost` `RPC` `connection` `to` `external` `procedure` `agent` error, which means that agent `extproc` terminated abnormally because the external procedure caused a core dump.

- [Using Package DEBUG_EXTPROC](using-package-debug-extproc.md)
  To help you debug external procedures, PL/SQL provides the utility package `DEBUG_``EXTPROC`.

**See Also:**

[Oracle Database Data Cartridge Developer's Guide.](../addci/implementing-data-cartridges-in-C-CPP-and-java.md) for information on how to avoid errors when declaring C prototype parameters

**Parent topic:** [Developing Applications for Windows](developing-applications-for-windows.md)
