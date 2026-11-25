This appendix looks at the improvements and new features offered by the Oracle Precompilers Release 1.8. Designed to meet the practical needs of professional software developers, these features will help you build effective, reliable applications.

### A.1 About Fetching NULLs without Using Indicator Variables

With releases 1.5, 1.6, and 1.7 of the Oracle Precompilers, source files that `FETCH` data into host variables without associated indicator variables return an `ORA-01405` message at run time if a `NULL` is returned to the host variable. With release 1.8, when you specify `MODE=ORACLE` and `DBMS=V7`, you can disable the `ORA-01405` message by also specifying `UNSAFE_NULL=YES`.

When developing applications for the Oracle Database, the preferred practice is to include indicator variables for any host variable that might have a `NULL` returned to it. When migrating applications from Oracle Version 6 to Oracle database version 7, however, the `UNSAFE_NULL` option can significantly ease the process.

For more information, see "[UNSAFE_NULL](running-Oracle-precompilers.md)" and "[About Using Indicator Variables](using-embedded-SQL.md)".

#### A.1.1 About Using DBMS=V7 and MODE=ORACLE

Applications precompiled with `MODE=ORACLE` and `DBMS=V7` return the `ORA-01405` error at run time if a `NULL` is returned to a host variable when there is no associated indicator variable. When upgrading to Oracle database version 7 with these options specified, you will need to migrate your applications in one of two ways:

- Modify your source code to include the necessary indicator variables

- Specify `UNSAFE_NULL=YES` on the command line

If you are upgrading to Oracle database version 7 and use `DBMS=V7` when precompiling, or if you intend to use new Oracle database version 7 features that are different from Oracle Version 6, in most instances, the change requires minimal modification to your source files. However, if your application may `FETCH` null values into host variables without associated indicator variables, specify `UNSAFE_NULL``=YES` to disable the `ORA-01405` message and avoid adding the relevant indicator variables to your source files.

#### A.1.2 Related Error Messages

For information about precompile time messages associated with the `UNSAFE_NULL` option, see [Oracle Database Error Messages](../errmg/index.md).

### A.2 Additional Array Insert/Select Syntax

The array INSERT and array SELECT syntax of the DB2 precompiler is now supported by the Oracle precompiler. The optional ROWSET and ROWSET STARTING AT clauses are used in the fetch-orientation (FIRST, PRIOR, NEXT, LAST, CURRENT, RELATIVE and ABSOLUTE). For more information about the new INSERT/SELECT syntax, please refer the [Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md) and [Pro\*C/C++ Programmer's Guide](../lnpcc/introduction-and-concepts.md).

### A.3 SQL99 Syntax Support

The SQL standard enables the portability of SQL applications across all conforming software products. Oracle features are compliant with the ANSI/ISO SQL99 standard, including ANSI compliant joins. Pro\*Cobol supports all SQL99 features that are supported by Oracle database, which means that the SQL99 syntax for the SELECT, INSERT, DELETE, and UPDATE statements and the body of the cursor in a DECLARE CURSOR statement are supported.

### A.4 About Fixing Execution Plans

To fix execution plans for SQL's used in Pro\*C/C++ or Pro\*Cobol development environment, you need to use the outline feature of Oracle at the time of precompiling. An outline is implemented as a set of optimizer hints that are associated with the SQL statement. If you enable the use of the outline for the statement, Oracle automatically considers the stored hints and tries to generate an execution plan in accordance with those hints. In this way, you can ensure that the performance is not affected when the modules are integrated or deployed into different environments.

You can use the following SQL statements to create outlines in Pro\*C/C++ and Pro\*Cobol:

- `SELECT`

- `DELETE`

- `UPDATE`

- `INSERT... SELECT`

- `CREATE TABLE... AS SELECT`

If the outline option is set, then the precompiler generates two files, a SQL file and a LOG file at the end of successful precompilation. Command line options `outline` and `outlnprefix` control the generation of the outlines.Each generated outline name is unique. Because the file names used in the application are unique, this information is used in generating the outline name. In addition, the category name is also prefixed.

**Note:**

Oracle allows only 30 bytes for the outline name. If you exceed the limit, the precompiler will flag an error. You can restrict the length of the outline name by using the `outlnprefix` option.

**See Also:**

- [Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)

- [Pro\*C/C++ Programmer's Guide](../lnpcc/introduction-and-concepts.md)

### A.5 About Using Implicit Buffered Insert

For improved performance, application developers can reference host arrays in their embedded SQL statements. This provides a means to execute an array of SQL statements with a single round-trip to the database. Despite the significant performance improvements afforded by array execution, some developers choose not to use this capability because it is not ANSI standard. For example, an application written to exploit array execution in Oracle cannot be precompiled using IBM's precompiler.

One workaround is to use buffered INSERT statements, which enable you to gain performance benefits while retaining ANSI standard embedded SQL syntax.

The command line option "max_row_insert" controls the number of rows to be buffered before executing the INSERT statement. By default it is zero and the feature is disabled. To enable this feature, specify any number greater than zero.

**See Also:**

For more information on using the implicit buffer insert feature, please refer to:

- [Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)

- [Pro\*C/C++ Programmer's Guide](../lnpcc/introduction-and-concepts.md)

### A.6 Dynamic SQL Statement Caching

Statement caching refers to the feature that provides and manages a cache of statements for each session. In the server, it means that cursors are ready to be used without the statement being parsed again. Statement caching can be enabled in the precompiler applications, which will help in the performance improvement of all applications that rely on the dynamic SQL statements. Performance improvement is achieved by removing the overhead of parsing the dynamic statements on reuse.

You can obtain this performance improvement by using a new command line option, `stmt_cache` (for the statement cache size), which will enable the statement caching of the dynamic statements. By enabling the new option, the statement cache will be created at session creation time. The caching is only applicable for the dynamic statements and the cursor cache for the static statements co-exists with this feature.

The command line option `stmt_cache` can be given any value in the range of 0 to 65535. Statement caching is disabled by default (value 0). The `stmt_cache` option can be set to hold the anticipated number of distinct dynamic SQL statements in the application.

Example A-1 Using the stmt_cache Option

This example demonstrates the use of the `stmt_cache` option. In this program, you insert rows into a table and select the inserted rows by using the cursor in the loop. When the stmt_cache option is used to precompile this program, the performance increases compared to a normal precompilation.

    /*
     *  stmtcache.pc
     *
     *  NOTE:
     *  When this program is used to measure the performance with and without
     *  stmt_cache option, do the following changes in the program,
     *  1. Increase ROWSCNT to high value, say 10000.
     *  2. Remove all the print statements, usually which comsumes significant
     *     portion of the total program execution time.
     *
     *  HINT: In Linux, gettimeofday() can be used to measure time.
     */

    #include <stdio.h>
    #include <string.h>
    #include <stdlib.h>
    #include <sqlca.h>
    #include <oraca.h>

    #define ROWSCNT 10

    char    *username = "aaaaa";
    char    *password = "bbbbb";

    /* Function prototypes */
    void sql_error(char *msg);
    void selectdata();
    void insertdata();

    int main()
    {
      EXEC SQL WHENEVER SQLERROR DO sql_error("Oracle error");

      /* Connect using the default schema aaaaa/bbbbb */
      EXEC SQL CONNECT :username IDENTIFIED BY :password;

      /* core functions to insert and select the data */
      insertdata();
      selectdata();

    /* Rollback pll the changes and disconnect from Oracle. */
      EXEC SQL ROLLBACK WORK RELEASE;

      exit(0);
    }

    /*Insert the data for ROWSCNT items into tpc2sc01 */
    void insertdata()
    {
      varchar dynstmt[80];
      int i;
      varchar ename[10];
      float comm;
      char *str;

      /* Allocates temporary buffer */
      str = (char *)malloc (11 * sizeof(char));

      strcpy ((char *)dynstmt.arr,
              "INSERT INTO bonus (ename, comm) VALUES (:ename, :comm)");
      dynstmt.len = strlen(dynstmt.arr);
      EXEC SQL PREPARE S FROM :dynstmt;

      printf ("Inserts %d rows into bonus table using dynamic SQL statement\n",
              ROWSCNT);
      for (i=1; i<=ROWSCNT; i++)
      {
        sprintf (str, "EMP_%05d",i);
        strcpy (ename.arr, str);
        comm = i;
        ename.len = strlen (ename.arr);
        EXEC SQL EXECUTE S USING :ename, :comm;
      }

      free(str);
    }

    /* Select the data using the cursor */
    void selectdata()
    {
      varchar dynstmt[80];
      varchar ename[10];
      float comm;
      int i;

      strcpy((char *)dynstmt.arr,
             "SELECT ename, comm FROM bonus WHERE comm = :v1");
      dynstmt.len = (unsigned short)strlen((char *)dynstmt.arr);

      printf ("Fetches the inserted rows using using dynamic SQL statement\n\n");
      printf ("  ENAME      COMMISSION\n\n");

      for (i=1; i<=ROWSCNT; i++)
      {
        /* Do the prepare in the loop so that the advantage of stmt_caching
           is visible*/
        EXEC SQL PREPARE S FROM :dynstmt;

        EXEC SQL DECLARE C CURSOR FOR S;
        EXEC SQL OPEN C USING :i;

        EXEC SQL WHENEVER NOT FOUND DO break;

        /* Loop until the NOT FOUND condition is detected. */
        for (;;)
        {
          EXEC SQL FETCH C INTO :ename, :comm;
          ename.arr[ename.len] = '\0';
          printf ("%10s    %7.2f\n", ename.arr, comm);
        }
        /* Close the cursor so that the reparsing is not required for stmt_cache */
        EXEC SQL CLOSE C;
      }
    }

    void sql_error(char *msg)
    {
        printf("\n%s", msg);
        sqlca.sqlerrm.sqlerrmc[sqlca.sqlerrm.sqlerrml] = '\0';
        oraca.orastxt.orastxtc[oraca.orastxt.orastxtl] = '\0';
        oraca.orasfnm.orasfnmc[oraca.orasfnm.orasfnml] = '\0';
        printf("\n%s\n", sqlca.sqlerrm.sqlerrmc);
        printf("in \"%s...\"\n", oraca.orastxt.orastxtc);
        printf("on line %d of %s.\n\n", oraca.oraslnr,
           oraca.orasfnm.orasfnmc);

       /* Disable ORACLE error checking to avoid an infinite loop
        * should another error occur within this routine.
        */
        EXEC SQL WHENEVER SQLERROR CONTINUE;

        /* Release resources associated with the cursor. */
        EXEC SQL CLOSE C;

        /* Roll back any pending changes and disconnect from Oracle. */
        EXEC SQL ROLLBACK WORK RELEASE;
        exit(1);
    }

### A.7 Scrollable Cursors

A scrollable cursor is a work area where Oracle executes SQL statements and stores information that is processed during execution.When a cursor is executed, the results of the query are placed into a a set of rows called the result set. The result set can be fetched either sequentially or non-sequentially. Non-sequential result sets are called scrollable cursors. A scrollable cursor enables users to access the rows of a database result set in a forward, backward, and random manner. This scrollable cursor enables the program to fetch any row in the result set. For more information about scrollable cursors, please see [Scrollable Cursors](../lnpcb/embedded-SQL.md).

### A.8 Platform Endianness Support

Oracle stored unicode data (UTF16) is always in big-endian form. Currently, client applications run on different platforms. Linux and Windows have little-endian representation and Solaris has big-endian representation. When UTF16 data is inserted or selected, Pro\*Cobol doesn't convert endian form between server and the client. This leads to corrupted UTF16 (UCS2) strings in the PIC N variable.

Platform endianness (Little-endian form for Linux and Windows, Big-endian form for Solaris) in PIC N variables can be maintained using the command line option `picn_endian`.

#### New Command Line Option

    picn_endian={BIG|OS}

If picn_endian=big, then PIC N variables are bound with character set ID AL16UTF16.

If picn_endian=os then PIC N variables are bound with character set ID UCS2.

The default value for this option is "big" to preserve the current behavior. This option is ignored if NLS_NCHAR is not AL16UTF16.

Character set form for PIC N variables can be set by using the existing Pro\*Cobol command line option:

    charset_picn={nchar_charset|db_charset}

### A.9 Flexible B Area Length

The length of B Area for a Pro\*Cobol program is limited to 72 when the format is set to ANSI. Cobol compilers now can support B Area length up to 253. This provides a programmer with the flexibility to type a line that is longer than 72 columns. Pro\*Cobol now supports B area length up to 253 when a Pro\*Cobol application is precompiled with the

`FORMAT=VARIABLE`

option.
