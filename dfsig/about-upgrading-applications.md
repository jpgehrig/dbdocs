Learn how to rebuild Application Programs in the following topics.

- Precompile and Compile Application Programs
- Link Application Programs
- Update ORAENV Files

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/upgrading-apps-after-oracle-db-upgrade.md)

### 5.1 Precompile and Compile Application Programs

You must change the Application code when APIs are deprecated or changed.

When you upgrade to the new release of Oracle Database software, ensure that you:

- Make the necessary code changes for APIs that are either deprecated or changed.
- Precompile and compile embedded SQL applications.
- Compile OCI applications with the new software.
- Relink the application using the libraries of the new release of Oracle Database.

By recompiling, you perform a syntax check of your application code. Some problems in the application code that were not detected by previous releases of the Oracle software can emerge when you precompile or compile with the new Oracle Database software. Precompiling and compiling with the latest release of Oracle Database software helps you to detect and correct problems in the application code that were previously unnoticed.

### 5.2 Link Application Programs

Statically-linked code can be incompatible with the upgraded Oracle Software.

It is very important that you relink statically-linked applications using the libraries of the new release of Oracle Database Software.

### 5.3 Update ORAENV Files

Check your `ORAENV` files, and if necessary, update the value of the `ORAUID`, `ORACLE_BASE`, and `ORACLE_HOME` environment variables.

The `ORAUID` environment variable must refer to the correct Oracle Database installation user ID and the `ORACLE_HOME` environment variable must refer to the corresponding Oracle home directory in the POSIX file system. Also check other environment variables and update them as required.

Use the `INSTALL.P.USER` procedure to create a template of an `ORAENV` file for the new release of Oracle Database.
