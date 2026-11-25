After writing your external procedures in a third-generation programming language, use the appropriate compiler and linker to build a DLL, making sure to export the external procedures as noted previously.

See your compiler and linker documentation for instructions on building a DLL and exporting its functions.

You can build the external procedure `FIND_MAX`, created in "Writing an External Procedure", into a DLL called `extern.dll` by going to `ORACLE_HOME``\rdbms\extproc` and typing `make`. After building the DLL, you can move it to any directory on your system.

The default behavior of `EXTPROC` is to load DLLs only from `ORACLE_HOME``\bin` or `ORACLE_HOME``\lib`. To load DLLs from other directories, you must set environment variable `EXTPROC_DLLS` to a colon (:) separated list (semicolon-separated on Windows systems) of the DLL names qualified with their complete paths. The preferred way to set this environment variable is through the `ENVS` parameter in `listener.ora`.

**See Also:**

[Oracle Database Development Guide](../adfns/design_basics.md) for more information on `EXTPROC`

**Parent topic:** [About Building External Procedures](about-building-external-procedures.md)
