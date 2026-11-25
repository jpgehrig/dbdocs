This chapter describes how to build Oracle database applications with Pro\*C/C++ using the sample programs that are included with this release.

This chapter contains the following topics:

- Sample Program Descriptions

- Building the Demonstration Tables

- About Building the Sample Programs

### F.1 Sample Program Descriptions

When you install Pro\*C/C++, Oracle Universal Installer copies a set of Pro\*C/C++ sample programs to the `ORACLE_BASE\ORACLE_HOME``\precomp\demo\proc` directory. These sample programs are listed in Table F-1 and described in the subsequent section.

When built, the sample programs that Oracle provides produce `.exe` executables.

For some sample programs, as indicated in the Notes column of the table, you must run the SQL scripts in the sample directory before you precompile and run the sample program. The SQL scripts set up the correct tables and data so that the sample programs run correctly. These SQL scripts are located in the `ORACLE_BASE``\``ORACLE_HOME``\precomp\demo\sql` directory.

Oracle Corporation recommends that you build and run these sample programs to verify that Pro\*C/C++ has been installed successfully and operates correctly. You can delete the programs after you use them.

You can build the sample program by using a batch file called `pcmake.bat` or by using Microsoft Visual Studio.

**See Also:**

"About Building the Sample Programs"

Table F-1 Sample Programs

| Sample Program | Source Files                                         | Pro\*C/C++ GUI Project File | MSVC Compiler Project File | Notes                                                                         |
|:---------------|:-----------------------------------------------------|:----------------------------|:---------------------------|:------------------------------------------------------------------------------|
| `ANSIDYN1`     | `ansidyn1.pc`                                        | `ansidyn1.pre`              | `ansidyn1.dsp`             | \-                                                                            |
| `ANSIDYN2`     | `ansidyn2.pc`                                        | `ansidyn2.pre`              | `ansidyn2.dsp`             | \-                                                                            |
| `COLDEMO1`     | `coldemo1.h coldemo1.pc coldemo1.sql coldemo1.typ`   | `coldemo1.pre`              | `coldemo1.dsp`             | Run `coldemo1.sql` and the Object Type Translator before building `coldemo1`. |
| `CPDEMO1`      | `cpdemo1.pc`                                         | `cpdemo1.pre`               | `cpdemo1.dsp`              | \-                                                                            |
| `CPDEMO2`      | `cpdemo2.pc`                                         | `cpdemo2.pre`               | `cpdemo2.dsp`              | \-                                                                            |
| `CPPDEMO1`     | `cppdemo1.pc`                                        | `cppdemo1.pre`              | `cppdemo1.dsp`             | \-                                                                            |
| `CPPDEMO2`     | `cppdemo2.pc empclass.pc cppdemo2.sql empclass.h`    | `cppdemo2.pre`              | `cppdemo2.dsp`             | Run `cppdemo2.sql` before building `cppdemo2`.                                |
| `CPPDEMO3`     | `cppdemo3.pc`                                        | `cppdemo3.pre`              | `cppdemo3.dsp`             | \-                                                                            |
| `CVDEMO`       | `cv_demo.pc cv_demo.sql`                             | `cv_demo.pre`               | `cv_demo.dsp`              | Run `cv_demo.sql` before building `cv_demo`.                                  |
| `EMPCLASS`     | `cppdemo2.pc empclass.pc cppdemo2.sql empclass.h`    | `empclass.pre`              | `empclass.dsp`             | Run `cppdemo2.sql` before building `empclass`.                                |
| `LOBDEMO1`     | `lobdemo1.h lobdemo1.pc lobdemo1.sql`                | `lobdemo1.pre`              | `lobdemo1.dsp`             | Run `lobdemo1.sql` before building `lobdemo1`.                                |
| `MLTTHRD1`     | `mltthrd1.pc mltthrd1.sql`                           | `mltthrd1.pre`              | `mltthrd1.dsp`             | Run `mltthrd1.sql` before building `mltthrd1`.                                |
| `NAVDEMO1`     | `navdemo1.h navdemo1.pc navdemo1.sql navdemo1.typ`   | `navdemo1.pre`              | `navdemo1.dsp`             | Run `navdemo1.sql` and the Object Type Translator before building `navdemo1`. |
| `OBJDEMO1`     | `objdemo1.h objdemo1.pc objdemo1.sql objdemo1.typ`   | `objdemo1.pre`              | `objdemo1.dsp`             | Run `objdemo1.sql` and the Object Type Translator before building `objdemo1`. |
| `ORACA`        | `oraca.pc oracatst.sql`                              | `oraca.pre`                 | `oraca.dsp`                | Run `oracatst.sql` before building `oraca`.                                   |
| `PLSSAM`       | `plssam.pc`                                          | `plssam.pre`                | `plssam.dsp`               | \-                                                                            |
| `SAMPLE`       | `sample.pc`                                          | `sample.pre`                | `sample.dsp`               | \-                                                                            |
| `SAMPLE1`      | `sample1.pc`                                         | `sample1.pre`               | `sample1.dsp`              | \-                                                                            |
| `SAMPLE2`      | `sample2.pc`                                         | `sample2.pre`               | `sample2.dsp`              | \-                                                                            |
| `SAMPLE3`      | `sample3.pc`                                         | `sample3.pre`               | `sample3.dsp`              | \-                                                                            |
| `SAMPLE4`      | `sample4.pc`                                         | `sample4.pre`               | `sample4.dsp`              | \-                                                                            |
| `SAMPLE5`      | `sample5.pc exampbld.sql examplod.sql`               | `sample5.pre`               | `sample5.dsp`              | Run `exampbld.sql`, then run `examplod.sql`, before building `sample5`.       |
| `SAMPLE6`      | `sample6.pc`                                         | `sample6.pre`               | `sample6.dsp`              | \-                                                                            |
| `SAMPLE7`      | `sample7.pc`                                         | `sample7.pre`               | `sample7.dsp`              | \-                                                                            |
| `SAMPLE8`      | `sample8.pc`                                         | `sample8.pre`               | `sample8.dsp`              | \-                                                                            |
| `SAMPLE9`      | `sample9.pc calldemo.sql`                            | `sample9.pre`               | `sample9.dsp`              | Run `calldemo.sql` before building `sample9`.                                 |
| `SAMPLE10`     | `sample10.pc`                                        | `sample10.pre`              | `sample10.dsp`             | \-                                                                            |
| `SAMPLE11`     | `sample11.pc sample11.sql`                           | `sample11.pre`              | `sample11.dsp`             | Run `sample11.sql` before building `sample11`.                                |
| `SAMPLE12`     | `sample12.pc`                                        | `sample12.pre`              | `sample12.dsp`             | \-                                                                            |
| `SCDEMO1`      | `scdemo1.pc`                                         | `scdemo1.pre`               | `scdemo1.dsp`              | \-                                                                            |
| `SCDEMO2`      | `scdemo2.pc`                                         | `scdemo2.pre`               | `scdemo2.dsp`              | \-                                                                            |
| `SQLVCP`       | `sqlvcp.pc`                                          | `sqlvcp.pre`                | `sqlvcp.dsp`               | \-                                                                            |
| `WINSAM`       | `resource.h winsam.h winsam.ico winsam.pc winsam.rc` | `winsam.pre`                | `winsam.dsp`               | \-                                                                            |

The following subsections describe the functionality of the sample programs.

ANSIDYN1
Demonstrates using ANSI dynamic SQL to process SQL statements that are not known until runtime. This program is intended to demonstrate the simplest (though not the most efficient) approach to using ANSI dynamic SQL.

ANSIDYN2
Demonstrates using ANSI dynamic SQL to process SQL statements that are not known until runtime. This program uses the Oracle extensions for batch processing and reference semantics.

COLDEMO1
Fetches census information for California counties. This program demonstrates various ways to navigate through collection-typed database columns.

CPDEMO1
Demonstrates how the connection pool feature can be used. It also shows how different connection pool options can be used to optimize performance.

CPDEMO2
Demonstrates connection pool feature with relatively complex set of SQL statements and shows how performance gain depends on the kind of SQL statements used by the program.

CPPDEMO1
Prompts the user for an employee number, then queries the `emp` table for the employee's name, salary, and commission. This program uses indicator variables (in an indicator struct) to determine whether the commission is `NULL`.

CPPDEMO2
Retrieves the names of all employees in a given department from the `emp` table (dynamic SQL Method 3).

CPPDEMO3
Finds all salespeople and prints their names and total earnings (including commissions). This program is an example of C++ inheritance.

CVDEMO
Declares and opens a ref cursor.

EMPCLASS
The `EMPCLASS` and `CPPDEMO2` files were written to provide an example of how to write Pro\*C/C++ programs within a C++ framework. `EMPCLASS` encapsulates a specific query on the `emp` table and is implemented using a cursor variable. `EMPCLASS` instantiates an instance of that query and provides cursor variable functionality (that is: `open`, `fetch`, `close`) through C++ member functions that belong to the `emp` class. The `empclass.pc` file is not a standalone demo program. It was written to be used by the `cppdemo2` demo program. To use the `emp` class, you have to write a driver (`cppdemo2.pc`) which declares an instance of the `emp` class and issues calls to the member functions of that class.

LOBDEMO1
Fetches and adds crime records to the database based on the person's Social Security Number. This program demonstrates the mechanisms for accessing and storing large objects (LOBs) to tables and manipulating LOBs through the stored procedures available through the `DBMS_LOB` package.

MLTTHRD1
Shows how to use threading in conjunction with precompilers. The program creates as many sessions as there are threads.

**See Also:**

" [Multithreaded Applications](multithreaded-applications.md)"

NAVDEMO1
Demonstrates navigational access to objects in the object cache.

OBJDEMO1
Demonstrates the use of objects. This program manipulates the object types person and address.

ORACA
Demonstrates how to use ORACA to determine various performance parameters at runtime.

PLSSAM
Demonstrates the use of embedded PL/SQL blocks. This program prompts you for an employee name that already resides in a database. It then executes a PL/SQL block, which returns the results of four `SELECT` statements.

SAMPLE
Adds new employee records to the personnel database and checks database integrity. The employee numbers in the database are automatically selected using the current maximum employee number +10.

SAMPLE1
Logs on to an Oracle database, prompts the user for an employee number, queries the database for the employee's name, salary, and commission, and displays the result. The program continues until the user enters 0 as the employee number.

SAMPLE2
Logs on to an Oracle database, declares and opens a cursor, fetches the names, salaries, and commissions of all salespeople, displays the results, and closes the cursor.

SAMPLE3
Logs on to an Oracle database, declares and opens a cursor, fetches in batches using arrays, and prints the results using the `print_rows()` function.

SAMPLE4
Demonstrates the use of type equivalencies using the `LONG VARRAW` external datatype.

SAMPLE5
Prompts the user for an account number and a debit amount. The program verifies that the account number is valid and that there are sufficient funds to cover the withdrawal before it debits the account. This program shows the use of embedded SQL.

SAMPLE6
Creates a table, inserts a row, commits insert, and drops the table (dynamic SQL Method 1).

SAMPLE7
Inserts two rows into the `emp` table and deletes them (dynamic SQL Method 2).

SAMPLE8
Retrieves the names of all employees in a given department from the `emp` table (dynamic SQL Method 3).

SAMPLE9
Connects to an Oracle database using the `scott/tiger` account. The program declares several host arrays and calls a PL/SQL stored procedure (`GET_EMPLOYEES` in the `CALLDEMO` package). The PL/SQL procedure returns up to `ASIZE` values. The program keeps calling `GET_EMPLOYEES`, getting `ASIZE` arrays each time, and printing the values, until all rows have been retrieved.

SAMPLE10
Connects to an Oracle database using your username and password and prompts for a SQL statement. You can enter any legal SQL statement, but you must use regular SQL syntax, not embedded SQL. Your statement is processed. If the statement is a query, the rows fetched are displayed (dynamic SQL Method 4).

SAMPLE11
Fetches from the `emp` table, using a cursor variable. The cursor is opened in the stored PL/SQL procedure `open_cur`, in the `EMP_DEMO_PKG` package.

SAMPLE12
Demonstrates how to do array fetches using dynamic SQL Method 4.

SCDEMO1
Demonstrates how the scrollable cursor can be used with Oracle dynamic SQL Method 4. Scrollable cursor can also be used with ANSI dynamic SQL Method 4.

SCDEMO2
Demonstrates the use of scrollable cursor with host arrays.

SQLVCP
Demonstrates how you can use the `sqlvcp()` function to determine the actual size of a `VARCHAR` struct. The size is then used as an offset to increment a pointer that steps through an array of `VARCHARs`.

This program also demonstrates how to use the `SQLStmtGetText()` function to retrieve the text of the last SQL statement that was executed.

WINSAM
Adds new employee records to the personnel database and checks database integrity. You can enter as many employee names as you want and perform the SQL commands by selecting the appropriate buttons in the Employee Record dialog box. This is a GUI version of the sample program.

### F.2 Building the Demonstration Tables

To run the sample programs, you must have a database account with the username `scott` and the password `tiger`. Also, you must have a database with the sample tables `emp` and `dept.` This account is included in the starter database for your Oracle Database 10g server. If the account does not exist on your database, create the account before running the sample programs. If your database does not contain `emp` and `dept` tables, you can use the `demobld.sql` script to create them.

To build the sample tables:

1.  Start SQL\*Plus
2.  Connect as username `scott` with the password `tiger`.
3.  Run the `demobld.sql` script:
        SQL> @ORACLE_BASE\ORACLE_HOME\sqlplus\demo\demobld.sql;

**Related Topics**

- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/index.md)

### F.3 About Building the Sample Programs

You can build the sample programs in two ways:

- Using the `pcmake.bat` file provided

- Using Microsoft Visual Studio

#### F.3.1 Using pcmake.bat

The `pcmake.bat` file for compiling Pro\*C/C++ demos is found in the following location:

    ORACLE_BASE\ORACLE_HOME\precomp\demo\proc

This batch file is designed to illustrate how Pro\*C/C++ applications can be built at the command prompt.

In order to use this batch file, Microsoft Visual Studio must be installed. The environment variable `MSVCDir` must be set. Pro\*C/C++ command line options and linker options vary depending on your application.

You can use this file to build a demo, to build `sample1` for example:

1.  Navigate to the location of the demo file and enter the following at the command prompt:
        C:\> CD ORACLE_BASE\ORACLE_HOME\precomp\demo\proc\sample1
2.  Enter the following:
        % pcmake sample1

### F.4 Using Microsoft Visual Studio

Microsoft Visual Studio project files have an extension of`.dsp`. The`.dsp` files in the `ORACLE_BASE\ORACLE_HOME``\precomp\demo\proc` directory guide and control the steps necessary to precompile, compile, and link the sample programs.

Pro\*C/C++, SQL\*Plus, and the Object Type Translator have been integrated into the Microsoft Visual Studio sample project files. You do not have to run Pro\*C/C++, SQL\*Plus, and the Object Type Translator separately before compilation.

To build a sample program:

1.  Open a Microsoft Visual Studio project file, such as `sample1.dsp`.

2.  Check the paths in the project file to ensure that they correspond to the configuration of your system. If they do not, change the paths accordingly. Your system may produce error messages if the paths to all components are not correct.

    **Note:**

    All of the sample programs were created with `C:\oracle\ora92` as the default drive.

<!-- -->

1.  Select Build \> Rebuild All. Microsoft Visual Studio creates the executable.

**Related Topics**

- Setting the Path for the Sample .pre Files
- [The Object Type Translator](the-Object-type.md)

### F.5 Setting the Path for the Sample .pre Files

By default the sample `.pre` files search for their corresponding `.pc` files in the `C:\oracle\ora92` directory where `C:\` is the drive that you are using, and `oracle\ora92` represents the location of the Oracle home. If the Oracle base and Oracle home directories are different on your computer, you must change the directory path to the correct path.

To change the directory path for a sample .pre file:

1.  In Pro\*C/C++, open the `.pre` file.
2.  Double-click the filename in the Input File area to display the Input File dialog box.
3.  Change the directory path to the correct path.
4.  Click Open.
