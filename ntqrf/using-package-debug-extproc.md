To help you debug external procedures, PL/SQL provides the utility package `DEBUG_``EXTPROC`.

To install the package, run the script `dbgextp.sql`, which you can find in the PL/SQL demo directory.

To use the package, follow instructions in `dbgextp.sql`. Your Oracle Database account must have `EXECUTE` privileges on the package and `CREATE` `LIBRARY` privileges.

To debug external procedures:

1.  From Windows Task Manager, in the Processes dialog, select ExtProc.exe.
2.  Right click, and select Debug.
3.  Click OK in the message window.
    If you have built your DLL in a debug fashion with Microsoft Visual C++, then Visual C++ is activated.
4.  In the Visual C++ window, select Edit `>` Breakpoints.
    Use the breakpoint identified in `dbgextp.sql` in the PL/SQL demo directory.

    **See Also:**

    - `ORACLE_HOME``\rdbms\extproc\readme.doc` (explains how to run the sample and provides debugging advice)

    - [Oracle Database PL/SQL Language Reference](../lnpls/CREATE-LIBRARY-statement.md)

    - [Oracle Database Development Guide](../adfns/design_basics.md) for more information about "Calling External Procedures"

    - [Oracle Database Data Cartridge Developer's Guide](../addci/implementing-data-cartridges-in-C-CPP-and-java.md)

**Parent topic:** [About Debugging External Procedures](about-debugging-external-procedures.md)
