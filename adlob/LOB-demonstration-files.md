## A  LOB Demonstration Files

This appendix describes files distributed with the database that demonstrate how LOBs are used in supported programmatic environments. This appendix contains these topics:

- PL/SQL LOB Demonstration Files

- OCI LOB Demonstration Files

- Java LOB Demonstration Files

<!-- -->

- PL/SQL LOB Demonstration Files
- OCI LOB Demonstration Files
- Java LOB Demonstration Files

### A.1 PL/SQL LOB Demonstration Files

The following table lists PL/SQL demonstration files. These files are installed in `$ORACLE_HOME/rdbms/demo/lobs/plsql/`. A driver program, `lobdemo.sql`, that calls these files is found in the same directory.

Table A-1 PL/SQL Demonstration Examples

| File Name      | Description                                                                                                  | Usage Information                                                                                           |
|:---------------|:-------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| `fclose_c.sql` | Closing a `BFILE` with `CLOSE`                                                                               | [Closing a BFILE with CLOSE](LOB-APIs-for-BFILE-operations.md)                                              |
| `fclose_f.sql` | Closing a `BFILE` with `FILECLOSE`                                                                           | [Closing a BFILE with FILECLOSE](LOB-APIs-for-BFILE-operations.md)                                          |
| `fclosea.sql`  | Closing all open `BFILE`s                                                                                    | [Closing All Open BFILEs with FILECLOSEALL](LOB-APIs-for-BFILE-operations.md)                               |
| `fcompare.sql` | Comparing all or parts of two `BFILE`s                                                                       | [Comparing All or Parts of Two BFILES](LOB-APIs-for-BFILE-operations.md)                                    |
| `fcopyloc.sql` | Copying a LOB locator for a `BFILE`                                                                          | [About Assigning a BFILE Locator](LOB-APIs-for-BFILE-operations.md)                                         |
| `fdisplay.sql` | Displaying `BFILE` data                                                                                      | [About Displaying BFILE Data](LOB-APIs-for-BFILE-operations.md)                                             |
| `fexists.sql`  | Checking if a `BFILE` exists                                                                                 | [Determining Whether a BFILE Exists](LOB-APIs-for-BFILE-operations.md)                                      |
| `ffilopen.sql` | Opening a `BFILE` with `FILEOPEN`                                                                            | [About Opening a BFILE with FILEOPEN](LOB-APIs-for-BFILE-operations.md)                                     |
| `ffisopen.sql` | Checking if the `BFILE` is `OPEN` with `FILEISOPEN`                                                          | [About Determining Whether a BFILE Is Open with FILEISOPEN](LOB-APIs-for-BFILE-operations.md)               |
| `fgetdir.sql`  | Getting the directory object name and filename of a `BFILE`                                                  | [Getting Directory Object Name and File Name of a BFILE](LOB-APIs-for-BFILE-operations.md)                  |
| `finsert.sql`  | Inserting row containing a `BFILE` by initializing a `BFILE` locator                                         | [About Inserting a Row Containing a BFILE](LOB-APIs-for-BFILE-operations.md)                                |
| `fisopen.sql`  | Checking if the `BFILE` is open with `ISOPEN`                                                                | [About Determining Whether a BFILE Is Open Using ISOPEN](LOB-APIs-for-BFILE-operations.md)                  |
| `flength.sql`  | Getting the length of a `BFILE`                                                                              | [Getting the Length of a BFILE](LOB-APIs-for-BFILE-operations.md)                                           |
| `floadlob.sql` | Loading a LOB with `BFILE` data                                                                              | [About Loading a LOB with BFILE Data](LOB-APIs-for-BFILE-operations.md)                                     |
| `fopen.sql`    | Opening a `BFILE` with `OPEN`                                                                                | [About Opening a BFILE with OPEN](LOB-APIs-for-BFILE-operations.md)                                         |
| `fpattern.sql` | Checking if a pattern exists in a `BFILE` using `instr`                                                      | [Checking If a Pattern Exists in a BFILE Using INSTR](LOB-APIs-for-BFILE-operations.md)                     |
| `fread.sql`    | Reading data from a `BFILE`                                                                                  | [About Reading Data from a BFILE](LOB-APIs-for-BFILE-operations.md)                                         |
| `freadprt.sql` | Reading portion of a `BFILE` data using `substr`                                                             | [About Reading a Portion of BFILE Data Using SUBSTR](LOB-APIs-for-BFILE-operations.md)                      |
| `fupdate.sql`  | Updating a `BFILE` by initializing a BFILE locator                                                           | [About Updating a BFILE by Initializing a BFILE Locator](LOB-APIs-for-BFILE-operations.md)                  |
| `lappend.sql`  | Appending one LOB to another                                                                                 | [About Appending One LOB to Another](using-LOB-APIs.md)                                                     |
| `lcompare.sql` | Comparing all or part of LOB                                                                                 | [Comparing All or Part of Two LOBs](using-LOB-APIs.md)                                                      |
| `lcopy.sql`    | Copying all or part of a LOB to another LOB                                                                  | [Copying All or Part of One LOB to Another LOB](using-LOB-APIs.md)                                          |
| `lcopyloc.sql` | Copying a LOB locator                                                                                        | [Copying All or Part of One LOB to Another LOB](using-LOB-APIs.md)                                          |
| `ldisplay.sql` | Displaying LOB data                                                                                          | [About Displaying LOB Data](using-LOB-APIs.md)                                                              |
| `lerase.sql`   | Erasing part of a LOB                                                                                        | [About Erasing Part of a LOB](using-LOB-APIs.md)                                                            |
| `linsert.sql`  | Inserting a row by initializing LOB locator bind variable                                                    | [Inserting a Row by Initializing a LOB Locator Bind Variable](DDL-DML-statements-with-LOBs.md)              |
| `linstr.sql`   | Seeing if pattern exists in LOB (`instr`)                                                                    | [Patterns: Checking for Patterns in a LOB Using INSTR](using-LOB-APIs.md)                                   |
| `lisopen.sql`  | Seeing if LOB is open                                                                                        | [Determining Whether a LOB is Open](using-LOB-APIs.md)                                                      |
| `listemp.sql`  | Seeing if LOB is temporary                                                                                   | [Determining Whether a LOB instance Is Temporary](using-LOB-APIs.md)                                        |
| `lldblobf.sql` | Using `DBMS_LOB.LOADBLOBFROMFILE` to load a `BLOB` with data from a `BFILE`                                  | [About Loading a BLOB with Data from a BFILE](using-LOB-APIs.md)                                            |
| `lldclobf.sql` | Using `DBMS_LOB.LOADCLOBFROMFILE` to load a `CLOB` or `NCLOB` with data from a `BFILE`                       | [Loading a CLOB or NCLOB with Data from a BFILE](using-LOB-APIs.md)                                         |
| `lldclobs.sql` | Using `DBMS_LOB.LOADCLOBFROMFILE` to load segments of a stream of data from a `BFILE` into different `CLOB`s | [Loading a CLOB or NCLOB with Data from a BFILE](using-LOB-APIs.md)                                         |
| `llength.sql`  | Getting the length of a LOB                                                                                  | [Length: Determining the Length of a LOB](using-LOB-APIs.md)                                                |
| `lloaddat.sql` | Loading a LOB with `BFILE` data                                                                              | [Loading a LOB with Data from a BFILE](using-LOB-APIs.md)                                                   |
| `lobuse.sql`   | Examples of LOB API usage.                                                                                   | [Creating Persistent and Temporary LOBs in PL/SQL](operations-specific-to-persistent-and-temporary-LOBs.md) |
| `lread.sql`    | Reading data from LOB                                                                                        | [About Reading Data from a LOB](using-LOB-APIs.md)                                                          |
| `lsubstr.sql`  | Reading portion of LOB (`substr`)                                                                            | [Reading a Portion of a LOB (SUBSTR)](using-LOB-APIs.md)                                                    |
| `ltrim.sql`    | Trimming LOB data                                                                                            | [About Trimming LOB Data](using-LOB-APIs.md)                                                                |
| `lwrite.sql`   | Writing data to a LOB                                                                                        | [About Writing Data to a LOB](using-LOB-APIs.md)                                                            |
| `lwriteap.sql` | Writing to the end of LOB (write append)                                                                     | [About Appending to a LOB](using-LOB-APIs.md)                                                               |

**Parent topic:** LOB Demonstration Files

### A.2 OCI LOB Demonstration Files

The following table lists OCI demonstration files. These files are installed in `$ORACLE_HOME/rdbms/demo/lobs/oci/`. A driver program, `lobdemo.c`, that calls these files is found in the same directory, as is the header file `lobdemo.h`.

Table A-2 OCI Demonstration Examples

| File Name     | Description                                                              | Usage Information                                                                              |
|:--------------|:-------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------|
| `fclose_c.c`  | Closing a `BFILE` with `CLOSE`                                           | [Closing a BFILE with CLOSE](LOB-APIs-for-BFILE-operations.md)                                 |
| `fclose_f.c`  | Closing a `BFILE` with `FILECLOSE`                                       | [Closing a BFILE with FILECLOSE](LOB-APIs-for-BFILE-operations.md)                             |
| `fclosea.c`   | Closing all open `BFILE`s                                                | [Closing All Open BFILEs with FILECLOSEALL](LOB-APIs-for-BFILE-operations.md)                  |
| `fcopyloc.c`  | Copying a LOB locator for a `BFILE`                                      | [About Assigning a BFILE Locator](LOB-APIs-for-BFILE-operations.md)                            |
| `fdisplay.c`  | Displaying `BFILE` data                                                  | [About Displaying BFILE Data](LOB-APIs-for-BFILE-operations.md)                                |
| `fexists.c`   | Checking if a `BFILE` exists                                             | [Determining Whether a BFILE Exists](LOB-APIs-for-BFILE-operations.md)                         |
| `ffilopen.c`  | Opening a BFILE with `FILEOPEN`                                          | [About Opening a BFILE with FILEOPEN](LOB-APIs-for-BFILE-operations.md)                        |
| `ffisopen.c`  | Checking if the `BFILE` is `OPEN` with `FILEISOPEN`                      | [About Determining Whether a BFILE Is Open with FILEISOPEN](LOB-APIs-for-BFILE-operations.md)  |
| `fgetdir.c`   | Getting the directory object name and filename of a `BFILE`              | [Getting Directory Object Name and File Name of a BFILE](LOB-APIs-for-BFILE-operations.md)     |
| `finsert.c`   | Inserting row containing a `BFILE` by initializing a `BFILE` locator     | [About Inserting a Row Containing a BFILE](LOB-APIs-for-BFILE-operations.md)                   |
| `fisopen.c`   | Checking if the `BFILE` is open with `ISOPEN`                            | [About Determining Whether a BFILE Is Open Using ISOPEN](LOB-APIs-for-BFILE-operations.md)     |
| `flength.c`   | Getting the length of a `BFILE`                                          | [Getting the Length of a BFILE](LOB-APIs-for-BFILE-operations.md)                              |
| `floadlob.c`  | Loading a LOB with `BFILE` data                                          | [About Loading a LOB with BFILE Data](LOB-APIs-for-BFILE-operations.md)                        |
| `fopen.c`     | Opening a `BFILE` with `OPEN`                                            | [About Opening a BFILE with OPEN](LOB-APIs-for-BFILE-operations.md)                            |
| `fread.c`     | Reading data from a `BFILE`                                              | [About Reading Data from a BFILE](LOB-APIs-for-BFILE-operations.md)                            |
| `fupdate.c`   | Updating a `BFILE` by initializing a BFILE locator                       | [About Updating a BFILE by Initializing a BFILE Locator](LOB-APIs-for-BFILE-operations.md)     |
| `lappend.c`   | Appending one LOB to another                                             | [About Appending One LOB to Another](using-LOB-APIs.md)                                        |
| `lcopy.c`     | Copying all or part of a LOB to another LOB                              | [Copying All or Part of One LOB to Another LOB](using-LOB-APIs.md)                             |
| `lcopyloc.c`  | Copying a LOB locator                                                    | [Copying All or Part of One LOB to Another LOB](using-LOB-APIs.md)                             |
| `ldisplay.c`  | Displaying LOB data                                                      | [About Displaying LOB Data](using-LOB-APIs.md)                                                 |
| `lequal.c`    | Seeing if one LOB locator is equal to another                            | [Equality: Checking If One LOB Locator Is Equal to Another](using-LOB-APIs.md)                 |
| `lerase.c`    | Erasing part of a LOB                                                    | [About Erasing Part of a LOB](using-LOB-APIs.md)                                               |
| `lgetchar.c`  | Getting character set id                                                 | [About Determining Character Set ID](using-LOB-APIs.md)                                        |
| `lgetchfm.c`  | Getting character set form of the foreign language ad text, `ad_fltextn` | [About Determining Character Set Form](using-LOB-APIs.md)                                      |
| `linit.c`     | Seeing if a LOB locator is initialized                                   | [About Determining Whether LOB Locator Is Initialized](using-LOB-APIs.md)                      |
| `linsert.c`   | Inserting a row by initializing LOB locator bind variable                | [Inserting a Row by Initializing a LOB Locator Bind Variable](DDL-DML-statements-with-LOBs.md) |
| `lisopen.c`   | Seeing if LOB is open                                                    | [Determining Whether a LOB is Open](using-LOB-APIs.md)                                         |
| `listemp.c`   | Seeing if LOB is temporary                                               | [Determining Whether a LOB instance Is Temporary](using-LOB-APIs.md)                           |
| `llength.c`   | Getting the length of a LOB                                              | [Length: Determining the Length of a LOB](using-LOB-APIs.md)                                   |
| `lloaddat.c`  | Loading a LOB with `BFILE` data                                          | [Loading a LOB with Data from a BFILE](using-LOB-APIs.md)                                      |
| `lread.c`     | Reading data from LOB                                                    | [About Reading Data from a LOB](using-LOB-APIs.md)                                             |
| `lreadarr.c`  | Reading data from an array of LOB locators                               | [About LOB Array Read](using-LOB-APIs.md)                                                      |
| `ltrim.c`     | Trimming LOB data                                                        | [About Trimming LOB Data](using-LOB-APIs.md)                                                   |
| `lwrite.c`    | Writing data to a LOB                                                    | [About Writing Data to a LOB](using-LOB-APIs.md)                                               |
| `lwritearr.c` | Writing data into an array of LOB locators                               | [LOB Array Write](using-LOB-APIs.md)                                                           |
| `lwriteap.c`  | Writing to the end of LOB (write append)                                 | [About Appending to a LOB](using-LOB-APIs.md)                                                  |

**Parent topic:** LOB Demonstration Files

### A.3 Java LOB Demonstration Files

The following table lists Java demonstration files. These files are installed in `$ORACLE_HOME/rdbms/demo/lobs/java/`.

Table A-3 Java Demonstration Examples

| File Name                     | Description                                                          | Usage Information                                                                                                                                                                                                                                 |
|:------------------------------|:---------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Readme.txt`                  | `-`                                                                  | See [Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-getting-started.md) for information on setting up your system to be able to compile and run JDBC programs with the Oracle Driver                                                       |
| LobDemoConnectionFactory.java | \-                                                                   | As written `LobDemoConnectionFactory` uses the JDBC OCI driver with a local connection. You should edit the URL `"jdbc:oracle:oci8:@"` to match your setup. Again see [Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-getting-started.md). |
| `fclose_c.java`               | Closing a `BFILE` with `CLOSE`                                       | [Closing a BFILE with CLOSE](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                                    |
| `fclose_f.java`               | Closing a `BFILE` with `FILECLOSE`                                   | [Closing a BFILE with FILECLOSE](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                                |
| `fclosea.java`                | Closing all open `BFILE`s                                            | [Closing All Open BFILEs with FILECLOSEALL](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                     |
| `fcompare.java`               | Comparing all or parts of two `BFILE`s                               | [Comparing All or Parts of Two BFILES](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                          |
| `fexists.java`                | Checking if a `BFILE` exists                                         | [Determining Whether a BFILE Exists](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                            |
| `ffilopen.java`               | Opening a `BFILE` with `FILEOPEN`                                    | [About Opening a BFILE with FILEOPEN](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                           |
| `ffisopen.java`               | Checking if the `BFILE` is OPEN with `FILEISOPEN`                    | [About Determining Whether a BFILE Is Open with FILEISOPEN](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                     |
| `fgetdir.java`                | Getting the directory object name and filename of a `BFILE`          | [Getting Directory Object Name and File Name of a BFILE](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                        |
| `finsert.java`                | Inserting row containing a `BFILE` by initializing a `BFILE` locator | [About Inserting a Row Containing a BFILE](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                      |
| `fisopen.java`                | Checking if the `BFILE` is open with `ISOPEN`                        | [About Determining Whether a BFILE Is Open Using ISOPEN](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                        |
| `flength.java`                | Getting the length of a `BFILE`                                      | [Getting the Length of a BFILE](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                                 |
| `fopen.java`                  | Opening a `BFILE` with `OPEN`                                        | [About Opening a BFILE with OPEN](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                               |
| `fpattern.java`               | Checking if a pattern exists in a `BFILE` using `instr`              | [Checking If a Pattern Exists in a BFILE Using INSTR](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                           |
| `fread.java`                  | Reading data from a `BFILE`                                          | [About Reading Data from a BFILE](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                                               |
| `fupdate.java`                | Updating a `BFILE` by initializing a `BFILE` locator                 | [About Updating a BFILE by Initializing a BFILE Locator](LOB-APIs-for-BFILE-operations.md)                                                                                                                                                        |
| `lappend.java`                | Appending one LOB to another                                         | [About Appending One LOB to Another](using-LOB-APIs.md)                                                                                                                                                                                           |
| `lcompare.java`               | Comparing all or part of LOB                                         | [Comparing All or Part of Two LOBs](using-LOB-APIs.md)                                                                                                                                                                                            |
| `lcopy.java`                  | Copying all or part of a LOB to another LOB                          | [Copying All or Part of One LOB to Another LOB](using-LOB-APIs.md)                                                                                                                                                                                |
| `lerase.java`                 | Erasing part of a LOB                                                | [About Erasing Part of a LOB](using-LOB-APIs.md)                                                                                                                                                                                                  |
| `linsert.java`                | Inserting a row by initializing LOB locator bind variable            | [Inserting a Row by Initializing a LOB Locator Bind Variable](DDL-DML-statements-with-LOBs.md)                                                                                                                                                    |
| `linstr.java`                 | Seeing if pattern exists in LOB (`instr`)                            | [Patterns: Checking for Patterns in a LOB Using INSTR](using-LOB-APIs.md)                                                                                                                                                                         |
| `lisopen.java`                | Seeing if LOB is open                                                | [Determining Whether a LOB is Open](using-LOB-APIs.md)                                                                                                                                                                                            |
| `listempb.java`               | Seeing if LOB is temporary                                           | [Determining Whether a LOB instance Is Temporary](using-LOB-APIs.md)                                                                                                                                                                              |
| `listempc.java`               | Seeing if LOB is temporary                                           | [Determining Whether a LOB instance Is Temporary](using-LOB-APIs.md)                                                                                                                                                                              |
| `llength.java`                | Getting the length of a LOB                                          | [Length: Determining the Length of a LOB](using-LOB-APIs.md)                                                                                                                                                                                      |
| `lloaddat.java`               | Loading a LOB with BFILE data                                        | [Loading a LOB with Data from a BFILE](using-LOB-APIs.md)                                                                                                                                                                                         |
| `lread.java`                  | Reading data from LOB                                                | [About Reading Data from a LOB](using-LOB-APIs.md)                                                                                                                                                                                                |
| `lsubstr.java`                | Reading portion of LOB (`substr`)                                    | [Reading a Portion of a LOB (SUBSTR)](using-LOB-APIs.md)                                                                                                                                                                                          |
| `ltrim.java`                  | Trimming LOB data                                                    | [About Trimming LOB Data](using-LOB-APIs.md)                                                                                                                                                                                                      |
| `lwrite.java`                 | Writing data to a LOB                                                | [About Writing Data to a LOB](using-LOB-APIs.md)                                                                                                                                                                                                  |
| `lwriteap.java`               | Writing to the end of LOB (write append)                             | [About Appending to a LOB](using-LOB-APIs.md)                                                                                                                                                                                                     |

**Parent topic:** LOB Demonstration Files
