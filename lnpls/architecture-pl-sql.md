## 1.3 Architecture of PL/SQL

Basic understanding of the PL/SQL architecture is beneficial to PL/SQL programmers.

### Topics

- PL/SQL Engine

- PL/SQL Units and Compilation Parameters

### 1.3.1 PL/SQL Engine

The PL/SQL compilation and runtime system is an engine that compiles and runs PL/SQL units.

The engine can be installed in the database or in an application development tool, such as Oracle Forms.

In either environment, the PL/SQL engine accepts as input any valid PL/SQL unit. The engine runs procedural statements, but sends SQL statements to the SQL engine in the database, as shown in Figure 1-1.

Figure 1-1 PL/SQL Engine

![Description of Figure 1-1 follows](img/lnpls004.gif)
[Description of "Figure 1-1 PL/SQL Engine"](img_text/lnpls004.md)

Typically, the database processes PL/SQL units.

When an application development tool processes PL/SQL units, it passes them to its local PL/SQL engine. If a PL/SQL unit contains no SQL statements, the local engine processes the entire PL/SQL unit. This is useful if the application development tool can benefit from conditional and iterative control.

For example, Oracle Forms applications frequently use SQL statements to test the values of field entries and do simple computations. By using PL/SQL instead of SQL, these applications can avoid calls to the database.

### 1.3.2 PL/SQL Units and Compilation Parameters

PL/SQL units are affected by PL/SQL compilation parameters (a category of database initialization parameters). Different PL/SQL units—for example, a package specification and its body—can have different compilation parameter settings.

A PL/SQL unit is one of these:

- PL/SQL anonymous block

- `FUNCTION`

- `LIBRARY`

- `PACKAGE`

- `PACKAGE` `BODY`

- `PROCEDURE`

- `TRIGGER`

- `TYPE`

- `TYPE` `BODY`

Table 1-2 summarizes the PL/SQL compilation parameters. To display the values of these parameters for specified or all PL/SQL units, query the static data dictionary view `ALL_PLSQL_OBJECT_SETTINGS`. For information about this view, see [Oracle Database Reference](../refrn/ALL_PLSQL_OBJECT_SETTINGS.md).

Table 1-2 PL/SQL Compilation Parameters

| Parameter                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [`PLSCOPE_SETTINGS`](../refrn/PLSCOPE_SETTINGS.md)           | Controls the compile-time collection, cross-reference, and storage of PL/SQL source text identifier data. Used by the PL/Scope tool (see [Oracle Database Development Guide](../adfns/plscope.md)).<br>For more information about `PLSCOPE_SETTINGS`, see [Oracle Database Reference](../refrn/PLSCOPE_SETTINGS.md).                                                                                                                                                                                                                                                                                   |
| [`PLSQL_CCFLAGS`](../refrn/PLSQL_CCFLAGS.md)                 | Lets you control conditional compilation of each PL/SQL unit independently.<br>For more information about `PLSQL_CCFLAGS`, see "[How Conditional Compilation Works](conditional-compilation1.md)" and [Oracle Database Reference](../refrn/PLSQL_CCFLAGS.md).                                                                                                                                                                                                                                                                                                                                          |
| [`PLSQL_CODE_TYPE`](../refrn/PLSQL_CODE_TYPE.md)             | Specifies the compilation mode for PL/SQL units—`INTERPRETED` (the default) or `NATIVE`. For information about which mode to use, see "[Determining Whether to Use PL/SQL Native Compilation](compiling-pl-sql-units-native-execution.md)".<br>If the optimization level (set by `PLSQL_OPTIMIZE_LEVEL`) is less than 2:<br>• The compiler generates interpreted code, regardless of `PLSQL_CODE_TYPE`.<br>• If you specify `NATIVE`, the compiler warns you that `NATIVE` was ignored.<br>For more information about `PLSQL_CODE_TYPE`, see [Oracle Database Reference](../refrn/PLSQL_CODE_TYPE.md). |
| [`PLSQL_OPTIMIZE_LEVEL`](../refrn/PLSQL_OPTIMIZE_LEVEL.md)   | Specifies the optimization level at which to compile PL/SQL units (the higher the level, the more optimizations the compiler tries to make).<br>`PLSQL_OPTIMIZE_LEVEL=1` instructs the PL/SQL compiler to generate and store code for use by the PL/SQL debugger.<br>For more information about `PLSQL_OPTIMIZE_LEVEL`, see "[PL/SQL Optimizer](pl-sql-optimizer.md)" and [Oracle Database Reference](../refrn/PLSQL_DEBUG.md).                                                                                                                                                                        |
| [`PLSQL_WARNINGS`](../refrn/PLSQL_WARNINGS.md)               | Enables or disables the reporting of warning messages by the PL/SQL compiler, and specifies which warning messages to show as errors.<br>For more information about `PLSQL_WARNINGS`, see "[Compile-Time Warnings](compile-time-warnings.md)" and [Oracle Database Reference](../refrn/PLSQL_WARNINGS.md).                                                                                                                                                                                                                                                                                             |
| [`NLS_LENGTH_SEMANTICS`](../refrn/NLS_LENGTH_SEMANTICS.md)   | Lets you create `CHAR` and `VARCHAR2` columns using either byte-length or character-length semantics.<br>For more information about byte and character length semantics, see "[CHAR and VARCHAR2 Variables](sql-data-types.md)".<br>For more information about `NLS_LENGTH_SEMANTICS`, see [Oracle Database Reference](../refrn/NLS_LENGTH_SEMANTICS.md).                                                                                                                                                                                                                                              |
| [`PERMIT_92_WRAP_FORMAT`](../refrn/PERMIT_92_WRAP_FORMAT.md) | Specifies whether the 12.1 PL/SQL compiler can use wrapped packages that were compiled with the 9.2 PL/SQL compiler. The default value is `TRUE`.<br>For more information about wrapped packages, see [PL/SQL Source Text Wrapping](plsql-source-text-wrapping.md).<br>For more information about `PERMIT_92_WRAP_FORMAT`, see [Oracle Database Reference](../refrn/PERMIT_92_WRAP_FORMAT.md).                                                                                                                                                                                                         |

**Note:**

The compilation parameter `PLSQL_DEBUG`, which specifies whether to compile PL/SQL units for debugging, is deprecated. To compile PL/SQL units for debugging, specify `PLSQL_OPTIMIZE_LEVEL=1`.

The compile-time values of the parameters in Table 1-2 are stored with the metadata of each stored PL/SQL unit, which means that you can reuse those values when you explicitly recompile the unit. (A stored PL/SQL unit is created with one of the "[CREATE \[ OR REPLACE \] Statements](sql-statements-for-stored-plsql-units.md)". An anonymous block is not a stored PL/SQL unit.)

To explicitly recompile a stored PL/SQL unit and reuse its parameter values, you must use an `ALTER` statement with both the `COMPILE` clause and the `REUSE` `SETTINGS` clause. All `ALTER` statements have this clause. For a list of `ALTER` statements, see "[ALTER Statements](sql-statements-for-stored-plsql-units.md)".
