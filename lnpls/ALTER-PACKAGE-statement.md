## 14.3 ALTER PACKAGE Statement

The `ALTER` `PACKAGE` statement explicitly recompiles a package specification, body, or both. Explicit recompilation eliminates the need for implicit runtime recompilation and prevents associated runtime compilation errors and performance overhead.

Because all objects in a package are stored as a unit, the `ALTER` `PACKAGE` statement recompiles all package objects. You cannot use the `ALTER` `PROCEDURE` statement or `ALTER` `FUNCTION` statement to recompile individually a procedure or function that is part of a package.

**Note:**

This statement does not change the declaration or definition of an existing package. To redeclare or redefine a package, use the "[CREATE PACKAGE Statement](CREATE-PACKAGE-statement.md)", or the "[CREATE PACKAGE BODY Statement](CREATE-PACKAGE-BODY-statement.md)" with the `OR` `REPLACE` clause.

### Topics

- Prerequisites

- Syntax

- Semantics

- Examples

- Related Topics

### Prerequisites

If the package is in the `SYS` schema, you must be connected as `SYSDBA`. Otherwise, the package must be in your schema or you must have `ALTER` `ANY` `PROCEDURE` system privilege.

### Syntax

### alter_package ::=

![Description of alter_package.eps follows](img/alter_package.gif)
[Description of the illustration alter_package.eps](img_text/alter_package.md)

### package_compile_clause ::=

![Description of package_compile_clause.eps follows](img/package_compile_clause.gif)
[Description of the illustration package_compile_clause.eps](img_text/package_compile_clause.md)

([compiler_parameters_clause ::=](COMPILE-clause.md))

### Semantics

### alter_package

IF EXISTS

Alters the package if it exists. If no such package exists, the statement is ignored without error.

schema

Name of the schema containing the package. Default: your schema.

package_name

Name of the package to be recompiled.

{ EDITIONABLE \| NONEDITIONABLE }

Specifies whether the package becomes an editioned or noneditioned object if editioning is later enabled for the schema object type `PACKAGE` in `schema`. Default: `EDITIONABLE`. For information about altering editioned and noneditioned objects, see [Oracle Database Development Guide](../adfns/editions.md).

### package_compile_clause

Recompiles the package specification, body, or both.

See [compile_clause](COMPILE-clause.md) and [compiler_parameters_clause](COMPILE-clause.md) semantics.

### Examples

Example 14-3 Recompiling a Package

This statement explicitly recompiles the specification and body of the `hr.emp_mgmt` package.

See "[CREATE PACKAGE Statement](CREATE-PACKAGE-statement.md)" for the example that creates this package.

    ALTER PACKAGE emp_mgmt COMPILE PACKAGE;

If the database encounters no compilation errors while recompiling the `emp_mgmt` specification and body, then `emp_mgmt` becomes valid. The user `hr` can subsequently invoke or reference all package objects declared in the specification of `emp_mgmt` without runtime recompilation. If recompiling `emp_mgmt` results in compilation errors, then the database returns an error and `emp_mgmt` remains invalid.

The database also invalidates all objects that depend upon `emp_mgmt`. If you subsequently reference one of these objects without explicitly recompiling it first, then the database recompiles it implicitly at run time.

To recompile the body of the `emp_mgmt` package in the schema `hr`, issue this statement:

    ALTER PACKAGE hr.emp_mgmt COMPILE BODY;

If the database encounters no compilation errors while recompiling the package body, then the body becomes valid. The user `hr` can subsequently invoke or reference all package objects declared in the specification of `emp_mgmt` without runtime recompilation. If recompiling the body results in compilation errors, then the database returns an error message and the body remains invalid.

Because this statement recompiles the body and not the specification of `emp_mgmt`, the database does not invalidate dependent objects.

### Related Topics

- "[CREATE PACKAGE Statement](CREATE-PACKAGE-statement.md)"

- "[DROP PACKAGE Statement](DROP-PACKAGE-statement.md)"
