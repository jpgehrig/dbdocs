## 4  Operations Specific to Persistent and Temporary LOBs

LOB operations between persistent and temporary LOB instances can differ.

Topics:

- Persistent LOB Operations

- Temporary LOB Operations

- Creating Persistent and Temporary LOBs in PL/SQL

- Freeing Temporary LOBs in OCI

<!-- -->

- Persistent LOB Operations
- Temporary LOB Operations
- Creating Persistent and Temporary LOBs in PL/SQL
- Freeing Temporary LOBs in OCI

**See Also:**

- [Using LOB APIs](using-LOB-APIs.md) gives details and examples of API usage for LOB APIs that can be used with either temporary or persistent LOBs.

- [LOB APIs for BFILE Operations](LOB-APIs-for-BFILE-operations.md) gives details and examples for usage of LOB APIs that operate on BFILEs.

**Parent topic:** [Getting Started](getting-started.md)

### 4.1 Persistent LOB Operations

This section describes operations that apply only to persistent LOBs.

- Inserting a LOB into a Table
- Selecting a LOB from a Table

**Parent topic:** Operations Specific to Persistent and Temporary LOBs

#### 4.1.1 Inserting a LOB into a Table

You can insert LOB instances into persistent LOB columns using by multiple methods.

**See Also:**

[DDL and DML Statements with LOBs](DDL-DML-statements-with-LOBs.md) for more information about the different methods available to insert LOB instances into persistent LOB columns

**Parent topic:** Persistent LOB Operations

#### 4.1.2 Selecting a LOB from a Table

You can select a persistent LOB from a table just as you would any other data type. In the following example, persistent LOB instances of different types are selected into PL/SQL variables.

    declare
      blob1 BLOB;
      blob2 BLOB;
      clob1 CLOB;
      nclob1 NCLOB;
    BEGIN
      SELECT ad_photo INTO blob1 FROM print_media WHERE Product_id = 2268
            FOR UPDATE;
      SELECT ad_photo INTO blob2 FROM print_media WHERE Product_id = 3106;

      SELECT ad_sourcetext INTO clob1 FROM Print_media
          WHERE product_id=3106 and ad_id=13001 FOR UPDATE;

      SELECT ad_fltextn INTO nclob1 FROM Print_media
          WHERE product_id=3060 and ad_id=11001 FOR UPDATE;

    END;
    /
    show errors;

**Parent topic:** Persistent LOB Operations

### 4.2 Temporary LOB Operations

This section describes operations that apply only to temporary LOB instances.

- Creating and Freeing a Temporary LOB

**Parent topic:** Operations Specific to Persistent and Temporary LOBs

#### 4.2.1 Creating and Freeing a Temporary LOB

To create a temporary LOB instance, you must declare a variable of the given LOB data type and pass the variable to the `CREATETEMPORARY` API.

The temporary LOB instance exists in your application until it goes out of scope, your session terminates, or you explicitly free the instance. Freeing a temporary LOB instance is recommended to free system resources.

The following example demonstrates how to create and free a temporary LOB in the PL/SQL environment using the DBMS_LOB package.

    declare
      blob1 BLOB;
      blob2 BLOB;
      clob1 CLOB;
      nclob1 NCLOB;
    BEGIN
      -- create temp LOBs
      DBMS_LOB.CREATETEMPORARY(blob1,TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(blob2,TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(clob1,TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(nclob1,TRUE, DBMS_LOB.SESSION);

      -- fill with data
      writeDataToLOB_proc(blob1);
      writeDataToLOB_proc(blob2);

      -- CHAR->LOB conversion
      clob1 := 'abcde';
      nclob1 := TO_NCLOB(clob1);

      -- Other APIs
      call_lob_apis(blob1, blob2, clob1, nclob1);

      -- free temp LOBs
      DBMS_LOB.FREETEMPORARY(blob1);
      DBMS_LOB.FREETEMPORARY(blob2);
      DBMS_LOB.FREETEMPORARY(clob1);
      DBMS_LOB.FREETEMPORARY(nclob1);

    END;
    /
    show errors;

**Parent topic:** Temporary LOB Operations

### 4.3 Creating Persistent and Temporary LOBs in PL/SQL

The code example that follows illustrates how to create persistent and temporary LOBs in PL/SQL. This code is in the demonstration file:

    $ORACLE_HOME/rdbms/demo/lobs/plsql/lobdemo.sql

This demonstration file also calls procedures in separate PL/SQL files that illustrate usage of other LOB APIs.

**See Also:**

[PL/SQL LOB Demonstration Files](LOB-demonstration-files.md) for a list of demonstration files and links for more information about related LOB APIs

    -----------------------------------------------------------------------------
    -------------------------  Persistent LOB operations ------------------------
    -----------------------------------------------------------------------------

    declare
      blob1 BLOB;
      blob2 BLOB;
      clob1 CLOB;
      nclob1 NCLOB;
    BEGIN
      SELECT ad_photo INTO blob1 FROM print_media WHERE Product_id = 2268
            FOR UPDATE;
      SELECT ad_photo INTO blob2 FROM print_media WHERE Product_id = 3106;

      SELECT ad_sourcetext INTO clob1 FROM Print_media
          WHERE product_id=3106 and ad_id=13001 FOR UPDATE;

      SELECT ad_fltextn INTO nclob1 FROM Print_media
          WHERE product_id=3060 and ad_id=11001 FOR UPDATE;

      call_lob_apis(blob1, blob2, clob1, nclob1);
      rollback;
    END;
    /
    show errors;

    -----------------------------------------------------------------------------
    -------------------------  Temporary LOB operations ------------------------
    -----------------------------------------------------------------------------

    declare
      blob1 BLOB;
      blob2 BLOB;
      clob1 CLOB;
      nclob1 NCLOB;
    BEGIN
      -- create temp LOBs
      DBMS_LOB.CREATETEMPORARY(blob1,TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(blob2,TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(clob1,TRUE, DBMS_LOB.SESSION);
      DBMS_LOB.CREATETEMPORARY(nclob1,TRUE, DBMS_LOB.SESSION);

      -- fill with data
      writeDataToLOB_proc(blob1);
      writeDataToLOB_proc(blob2);

      -- CHAR->LOB conversion
      clob1 := 'abcde';
      nclob1 := TO_NCLOB(clob1);

      -- Other APIs
      call_lob_apis(blob1, blob2, clob1, nclob1);

      -- free temp LOBs
      DBMS_LOB.FREETEMPORARY(blob1);
      DBMS_LOB.FREETEMPORARY(blob2);
      DBMS_LOB.FREETEMPORARY(clob1);
      DBMS_LOB.FREETEMPORARY(nclob1);

    END;
    /
    show errors;

**Parent topic:** Operations Specific to Persistent and Temporary LOBs

### 4.4 Freeing Temporary LOBs in OCI

Any time that your OCI program obtains a LOB locator from SQL or PL/SQL, check that the locator is temporary. If it is, free the locator when your application is finished with it. The locator can be from a define during a select or an out bind. A temporary LOB duration is always upgraded to session when it is shipped to the client side. The application must do the following before the locator is overwritten by the locator of the next row:

    OCILobIsTemporary(env, err, locator, is_temporary);
    if(is_temporary)
        OCILobFreeTemporary(svc, err, locator);

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/lob-functions.md) chapter 16, section "LOB Functions."

**Parent topic:** Operations Specific to Persistent and Temporary LOBs
