## Copying demo Directories to Oracle Base Home

In a read-only mode ORACLE_HOME, you must copy the `demo` directories listed in this topic from ORACLE_HOME to ORACLE_BASE_HOME.

Oracle Database contains various `demo` directories that include a variety of examples and product demonstrations that you can use to learn about the products, options, and features of Oracle Database. In a read-only mode ORACLE_HOME, you cannot use these `demo` directories in ORACLE_HOME because writes are performed to these `demo` directories when they are used.

Many of the demo directories are not available by default. You must install Oracle Database Examples to view and use the examples and product demonstrations.

Copy the respective `demo` directory to the corresponding location in ORACLE_BASE_HOME. Now, you can use this copy of the `demo` directory.

You must copy the following `demo` directories from ORACLE_HOME to ORACLE_BASE_HOME:

- `jdbc/demo`

- `odbc/demo`

- `ord/http/demo`

- `precomp/demo`

- `rdbms/demo`

- `sqlj/demo`

- `sqlplus/demo`

- `xdk/demo`

You must also create symbolic links for the `odbc/demo`, `precomp/demo`, `rdbms/demo`, and `xdk/demo` `demo` directories. See the "Creating Symbolic Links" section in this topic.

### Copying demo Directories

For example, to copy the `rdbms/demo` directory from ORACLE_HOME to ORACLE_BASE_HOME, perform the following:

1.  Login as the Oracle software owner user (`oracle`).

2.  Check if the `rdbms/demo` directory is copied to ORACLE_BASE_HOME.

        $ ls -l -d $(orabasehome)/rdbms/demo

3.  If the `rdbms/demo` directory has not been copied, then create it and copy it.

        $ mkdir -p $(orabasehome)/rdbms
        $ cp -r $ORACLE_HOME/rdbms/demo $(orabasehome)/rdbms/demo

Similarly, copy all the `demo` directories listed earlier from ORACLE_HOME to ORACLE_BASE_HOME.

### Creating Symbolic Links

You must create symbolic links for the `odbc/demo`, `precomp/demo`, `rdbms/demo`, and `xdk/demo` `demo` directories.

For `rdbms/demo`, replace `$ORACLE_HOME/rdbms/demo` with a symbolic link to the copy.

1.  Ensure that the symbolic link does not already exist.

        $ ls -l -d $ORACLE_HOME/rdbms/demo

2.  If `$ORACLE_HOME/rdbms/demo` is still the original `demo` directory, rename it and replace it with the symbolic link.

        $ cd $ORACLE_HOME/rdbms
        $ mv demo demo.installed
        $ ln -s $(orabasehome)/rdbms/demo $ORACLE_HOME/rdbms/demo

For `odbc/demo`, replace `$ORACLE_HOME/odbc/demo` with a symbolic link to the copy.

1.  Ensure that the symbolic link does not already exist.

        $ ls -l -d $ORACLE_HOME/odbc/demo

2.  If `$ORACLE_HOME/odbc/demo` is still the original `demo` directory, rename it and replace it with the symbolic link.

        $ cd $ORACLE_HOME/odbc
        $ mv demo demo.installed
        $ ln -s $(orabasehome)/odbc/demo $ORACLE_HOME/odbc/demo

For `precomp/demo`, replace `$ORACLE_HOME/precomp/demo` with a symbolic link to the copy.

1.  Ensure that the symbolic link does not already exist.

        $ ls -l -d $ORACLE_HOME/precomp/demo

2.  If `$ORACLE_HOME/precomp/demo` is still the original `demo` directory, rename it and replace it with the symbolic link.

        $ cd $ORACLE_HOME/precomp
        $ mv demo demo.installed
        $ ln -s $(orabasehome)/precomp/demo $ORACLE_HOME/precomp/demo

The `xdk/demo` directory requires a symbolic link at ` $ORACLE_HOME/xdk/include` pointing to `$(orabasehome)/xdk/include` after you copy the `xdk/demo` directory.

1.  Ensure that the symbolic link does not already exist:

        $ ls -l -d $ORACLE_HOME/xdk/include

2.  If the symbolic link does not exist, then, run the following command:

        $ ln -s $ORACLE_HOME/xdk/include $(orabasehome)/xdk/include

**Note:**

In the `plsql/demo` directory, `ncmpdemo.sql` is unusable in read-only mode.

### Copying the init.ora File

Copy the `init.ora` file from ORACLE_HOME to ORACLE_BASE_HOME.

1.  Login as the Oracle software owner user (`oracle`).

2.  Check if the `init.ora` file exists in ORACLE_BASE_HOME.

        $ ls $(orabasehome)/init.ora

    If an `init.ora` file exists in ORACLE_BASE_HOME, then update this `init.ora` file to be in-sync with the` $ORACLE_HOME/init.ora` file.

3.  If the `init.ora` file does not exist in ORACLE_BASE_HOME, then copy it from ORACLE_HOME.

        $ cp $ORACLE_HOME/init.ora $(orabasehome)/init.ora

**Related Topics**

- [Oracle Database Examples Installation Guide](../exmpl/index.md)

**Parent topic:** [Configuring Read-Only Oracle Homes](configuring-read-only-oracle-homes.md)
