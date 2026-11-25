## 6  DDL and DML Statements with LOBs

DDL and DML statements work with LOBs.

Topics:

- Creating a Table Containing One or More LOB Columns

- Creating a Nested Table Containing a LOB

- Inserting a Row by Selecting a LOB From Another Table

- Inserting a LOB Value Into a Table

- Inserting a Row by Initializing a LOB Locator Bind Variable

- Updating a LOB with EMPTY_CLOB() or EMPTY_BLOB()

- Updating a Row by Selecting a LOB From Another Table

<!-- -->

- Creating a Table Containing One or More LOB Columns
- Creating a Nested Table Containing a LOB
- Inserting a Row by Selecting a LOB From Another Table
- Inserting a LOB Value Into a Table
- Inserting a Row by Initializing a LOB Locator Bind Variable
  You can insert a row by initializing a LOB locator bind variable.
- Updating a LOB with EMPTY_CLOB() or EMPTY_BLOB()
- Updating a Row by Selecting a LOB From Another Table

**See Also:**

For guidelines on how to `INSERT` into a LOB when binds of more than 4000 bytes are involved, see the following sections in "[Binds of All Sizes in INSERT and UPDATE Operations](data-interface-for-persistent-LOBs.md)".

**Parent topic:** [Getting Started](getting-started.md)

### 6.1 Creating a Table Containing One or More LOB Columns

You can create a table containing one or more LOB columns.

When you use functions, `EMPTY_BLOB()` and `EMPTY_CLOB()`, the resulting LOB is initialized, but not populated with data. Also note that LOBs that are empty are not `NULL`.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-DROP-CONTEXT-to-DROP-JAVA.md)for a complete specification of syntax for using LOBs in `CREATE TABLE` and `ALTER TABLE` with:

- `BLOB`, `CLOB`, `NCLOB` and `BFILE` columns

- `EMPTY_BLOB` and `EMPTY_CLOB` functions

- LOB storage clause for persistent LOB columns, and LOB attributes of embedded objects

#### Scenario

These examples use the following Sample Schemas:

- Human Resources (`HR`)

- Order Entry (`OE`)

- Product Media (`PM`)

**Note:**

Note `HR` and `OE` schemas must exist before the `PM` schema is created.

**Note:**

Because you can use SQL DDL directly to create a table containing one or moreLOBcolumns, it is not necessary to use the `DBMS_LOB` package.

    /*  Setup script for creating Print_media,
        Online_media and associated structures
    */

    DROP USER pm CASCADE;
    DROP DIRECTORY ADPHOTO_DIR;
    DROP DIRECTORY ADCOMPOSITE_DIR;
    DROP DIRECTORY ADGRAPHIC_DIR;
    DROP INDEX onlinemedia CASCADE CONSTRAINTS;
    DROP INDEX printmedia CASCADE CONSTRAINTS;
    DROP TABLE online_media CASCADE CONSTRAINTS;
    DROP TABLE print_media CASCADE CONSTRAINTS;
    DROP TYPE textdoc_typ;
    DROP TYPE textdoc_tab;
    DROP TYPE adheader_typ;
    DROP TABLE adheader_typ;
    CREATE USER pm identified by password;
    GRANT CONNECT, RESOURCE to pm;

    CREATE DIRECTORY ADPHOTO_DIR AS '/tmp/';
    CREATE DIRECTORY ADCOMPOSITE_DIR AS '/tmp/';
    CREATE DIRECTORY ADGRAPHIC_DIR AS '/tmp/';
    CREATE DIRECTORY media_dir AS '/tmp/';
    GRANT READ ON DIRECTORY ADPHOTO_DIR to pm;
    GRANT READ ON DIRECTORY ADCOMPOSITE_DIR to pm;
    GRANT READ ON DIRECTORY ADGRAPHIC_DIR to pm;
    GRANT READ ON DIRECTORY media_dir to pm;

    CONNECT pm/password  (or &pass);
    COMMIT;

    CREATE TABLE a_table (blob_col BLOB);

    CREATE TYPE adheader_typ AS OBJECT (
       header_name    VARCHAR2(256),
       creation_date  DATE,
       header_text    VARCHAR(1024),
       logo           BLOB );

    CREATE TYPE textdoc_typ AS OBJECT (
       document_typ   VARCHAR2(32),
       formatted_doc  BLOB);

    CREATE TYPE Textdoc_ntab AS TABLE of textdoc_typ;

    CREATE TABLE adheader_tab of adheader_typ (
    Ad_finaltext DEFAULT EMPTY_CLOB(), CONSTRAINT
    Take CHECK (Take IS NOT NULL),  DEFAULT NULL);

    CREATE TABLE online_media
    ( product_id  NUMBER(6),
    product_photo ORDSYS.ORDImage,
    product_photo_signature ORDSYS.ORDImageSignature,
    product_thumbnail ORDSYS.ORDImage,
    product_video ORDSYS.ORDVideo,
    product_audio ORDSYS.ORDAudio,
    product_text CLOB,
    product_testimonials ORDSYS.ORDDoc);

    CREATE UNIQUE INDEX onlinemedia_pk
      ON online_media (product_id);

    ALTER TABLE online_media
    ADD (CONSTRAINT onlinemedia_pk
    PRIMARY KEY (product_id), CONSTRAINT loc_c_id_fk
    FOREIGN KEY (product_id)  REFERENCES oe.product_information(product_id)
    );

    CREATE TABLE print_media
    (product_id NUMBER(6),
    ad_id NUMBER(6),
    ad_composite BLOB,
    ad_sourcetext CLOB,
    ad_finaltext CLOB,
    ad_fktextn NCLOB,
    ad_testdocs_ntab textdoc_tab,
    ad_photo BLOB,
    ad_graphic BFILE,
    ad_header adheader_typ,
    press_release LONG) NESTED TABLE ad_textdocs_ntab STORE AS textdocs_nestedtab;

    CREATE UNIQUE INDEX printmedia_pk
      ON print_media (product_id, ad_id);

    ALTER TABLE print_media
    ADD (CONSTRAINT printmedia_pk
    PRIMARY KEY (product_id, ad_id),
    CONSTRAINT printmedia_fk FOREIGN KEY (product_id)
    REFERENCES oe.product_information(product_id)
    );

**Parent topic:** DDL and DML Statements with LOBs

### 6.2 Creating a Nested Table Containing a LOB

You can create a nested table containing a LOB.

You must create the object type that contains the LOB attributes before you create a nested table based on that object type. In the example that follows, table `Print_media` contains nested table `ad_textdoc_ntab` that has type `textdoc_tab`. This type uses two LOB data types:

- `BFILE `- an advertisement graphic

- `CLOB `- an advertisement transcript

The actual embedding of the nested table is accomplished when the structure of the containing table is defined. In our example, this is effected by the `NESTED TABLE` statement when the `Print_media` table is created as shown in the following example:

    /* Create type textdoc_typ as the base type
       for the nested table textdoc_ntab,
       where textdoc_ntab contains a LOB:
    */
    CREATE TYPE textdoc_typ AS OBJECT
    (
       document_typ    VARCHAR2(32),
       formatted_doc   BLOB
    );
    /

    /* The type has been created. Now you need a */
    /* nested table of that type to embed in */
    /* table Print_media, so: */
    CREATE TYPE textdoc_ntab AS TABLE of textdoc_typ;
    /

    CREATE TABLE textdoc_ntable (
       id NUMBER,
       ntab_col textdoc_ntab)
    NESTED TABLE ntab_col STORE AS textdoc_nestedtab;

    DROP TYPE textdoc_typ force;
    DROP TYPE textdoc_ntab;
    DROP TABLE textdoc_ntable;

**See Also:**

- "Creating a Table Containing One or More LOB Columns"

- [ Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for further information on `CREATE` `TABLE`

**Parent topic:** DDL and DML Statements with LOBs

### 6.3 Inserting a Row by Selecting a LOB From Another Table

You can insert a row containing a LOB as `SELECT`.

**Note:**

Persistent LOB types `BLOB`, `CLOB`, and `NCLOB`, use copy semantics, as opposed to reference semantics that apply to `BFILE`s. When a `BLOB`, `CLOB`, or `NCLOB` is copied from one row to another in the same table or a different table, the actual LOB value is copied, not just the LOB locator.

For LOBs, one of the advantages of using an object-relational approach is that you can define a type as a common template for related tables. For instance, it makes sense that both the tables that store archival material and working tables that use those libraries, share a common structure.

For example, assuming `Print_media` and `Online_media` have identical schemas. The statement creates a new LOB locator in table `Print_media. It also` copies the LOB data from `Online_media` to the location pointed to by the new LOB locator inserted in table `Print_media`.

The following code fragment is based on the fact that the table `Online_media` is of the same type as `Print_media` referenced by the `ad_textdocs_ntab` column of table `Print_media`. It inserts values into the library table, and then inserts this same data into `Print_media` by means of a `SELECT`.

    /* Store records in the archive table Online_media: */
    INSERT INTO Online_media
       VALUES (3060, NULL, NULL, NULL, NULL,
               'some text about this CRT Monitor', NULL);

    /* Insert values into Print_media by selecting from Online_media: */
    INSERT INTO Print_media (product_id, ad_id, ad_sourcetext)
       (SELECT product_id, 11001, product_text
              FROM Online_media WHERE product_id = 3060);

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/INSERT.md) for more information on `INSERT`

- [Oracle Database Sample Schemas ](../comsc/introduction-to-sample-schemas.md)for a description of the PM Schema and the `Print_media` table used in this example

**Parent topic:** DDL and DML Statements with LOBs

### 6.4 Inserting a LOB Value Into a Table

You can insert a LOB value using `EMPTY_CLOB()` or `EMPTY_BLOB()`.

#### Usage Notes

Here are guidelines for inserting LOBs:

#### Before Inserting Make the LOB Column Non-Null

Before you write data to a persistent LOB, make the LOB column non-`NULL`; that is, the LOB column must contain a locator that points to an empty or populated LOB value. You can initialize a `BLOB` column value by using the function `EMPTY_BLOB()` as a default predicate. Similarly, a `CLOB` or `NCLOB` column value can be initialized by using the function `EMPTY_CLOB()`.

You can also initialize a LOB column with a character or raw string less than 4000 bytes in size. For example:

    INSERT INTO Print_media (product_id, ad_id, ad_sourcetext)
         VALUES (1, 1, 'This is a One Line Advertisement');

Note that you can also perform this initialization during the `CREATE` `TABLE` operation.

**See Also:**

Creating a Table Containing One or More LOB Columns

These functions are special functions in Oracle SQL, and are not part of the `DBMS_LOB` package.

    /* In the new row of table Print_media,
       the columns ad_sourcetext and ad_fltextn are initialized using EMPTY_CLOB(),
       the columns ad_composite and ad_photo are initialized using EMPTY_BLOB(),
       the column formatted-doc in the nested table is initialized using
       EMPTY_BLOB(),
       the column logo in the column object is initialized using EMPTY_BLOB(): */
    INSERT INTO Print_media
       VALUES (3060,11001, EMPTY_BLOB(), EMPTY_CLOB(),EMPTY_CLOB(),EMPTY_CLOB(),
       textdoc_tab(textdoc_typ ('HTML', EMPTY_BLOB())), EMPTY_BLOB(), NULL,
       adheader_typ('any header name', <any date>, 'ad header text goes here',
       EMPTY_BLOB()),
     'Press release goes here');

**Parent topic:** DDL and DML Statements with LOBs

### 6.5 Inserting a Row by Initializing a LOB Locator Bind Variable

You can insert a row by initializing a LOB locator bind variable.

Examples for this use case are provided in several programmatic environments:

Topics:

- About Inserting Rows with LOB Locator Bind Variables

- PL/SQL: Inserting a Row by Initializing a LOB Locator Bind Variable

- C (OCI): Inserting a Row by Initializing a LOB Locator Bind Variable

- COBOL (Pro\*COBOL): Inserting a Row by Initializing a LOB Locator Bind Variable

- C/C++ (Pro\*C/C++): Inserting a Row by Initializing a LOB Locator Bind Variable

- Java (JDBC): Inserting a Row by Initializing a LOB Locator Bind Variable

<!-- -->

- SQL: [Oracle Database SQL Language Reference](../sqlrf/INSERT.md), the `INSERT` statement

- C (OCI): [Oracle Call Interface Programmer's Guide ](../lnoci/introduction-to-relational-functions.md)"Relational Functions"

- C++ (OCCI): [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

- COBOL (Pro\*COBOL)[Pro\*COBOL Programmer's Guide](../lnpcb/introduction-and-concepts.md)for information on LOBs, usage notes on LOB Statements, and embedded SQL and precompiler directives — `INSERT`.

- C/C++ (Pro\*C/C++):[ Pro\*C/C++ Programmer's Guide ](../lnpcc/embedded-SQL-statements-and-directives.md)`INSERT`

- Java (JDBC):[Oracle Database JDBC Developer's Guide](../jjdbc/LOBs-and-BFiles.md) "Working With LOBs" — Creating and Populating a `BLOB` or `CLOB` Colum

<!-- -->

- About Inserting Rows with LOB Locator Bind Variables
- PL/SQL: Inserting a Row by Initializing a LOB Locator Bind Variable
- C (OCI): Inserting a Row by Initializing a LOB Locator Bind Variable
- COBOL (Pro\*COBOL): Inserting a Row by Initializing a LOB Locator Bind Variable
- C/C++ (Pro\*C/C++): Inserting a Row by Initializing a LOB Locator Bind Variable
- Java (JDBC): Inserting a Row by Initializing a LOB Locator Bind Variable

**Parent topic:** DDL and DML Statements with LOBs

#### 6.5.1 About Inserting Rows with LOB Locator Bind Variables

You need to consider these points.

##### Preconditions

Before you can insert a row using this technique, the following conditions must be met:

- The table containing the source row must exist.

- The destination table must exist.

For details on creating tables containing LOB columns, see "[LOB Storage Parameters](LOB-storage-with-applications.md)".

##### Usage Notes

For guidelines on how to `INSERT` and `UPDATE` a row containing a LOB when binds of more than 4000 bytes are involved, see "[Binds of All Sizes in INSERT and UPDATE Operations](data-interface-for-persistent-LOBs.md)".

##### Syntax

Review these syntax references for details on using this operation in each programmatic environment:

**Parent topic:** Inserting a Row by Initializing a LOB Locator Bind Variable

#### 6.5.2 PL/SQL: Inserting a Row by Initializing a LOB Locator Bind Variable

You can insert a row by initializing a LOB locator bind variable in PL/SQL

    /* This file is installed in the following path when you install */
    /* the database: $ORACLE_HOME/rdbms/demo/lobs/plsql/linsert.sql */

    /* inserting a row through an insert statement */

    CREATE OR REPLACE PROCEDURE insertLOB_proc (Lob_loc IN BLOB) IS
    BEGIN
      /* Insert the BLOB into the row */
      DBMS_OUTPUT.PUT_LINE('------------ LOB INSERT EXAMPLE ------------');
      INSERT INTO print_media (product_id, ad_id, ad_photo)
            values (3106, 60315, Lob_loc);
    END;
    /

**Parent topic:** Inserting a Row by Initializing a LOB Locator Bind Variable

#### 6.5.3 C (OCI): Inserting a Row by Initializing a LOB Locator Bind Variable

You can insert a row by initializing a LOB locator bind variable in C (OCI).

    /* This file is installed in the following path when you install */
    /* the database: $ORACLE_HOME/rdbms/demo/lobs/oci/linsert.c */

    /* Insert the Locator into table using Bind Variables. */
    #include <oratypes.h>
    #include <lobdemo.h>
    void insertLOB_proc(OCILobLocator *Lob_loc, OCIEnv *envhp,
                        OCIError *errhp, OCISvcCtx *svchp, OCIStmt *stmthp)
    {
      int            product_id;
      OCIBind       *bndhp3;
      OCIBind       *bndhp2;
      OCIBind       *bndhp1;
      text          *insstmt =
       (text *) "INSERT INTO Print_media (product_id, ad_id, ad_sourcetext) \
                 VALUES (:1, :2, :3)";

      printf ("----------- OCI Lob Insert Demo --------------\n");
      /* Insert the locator into the Print_media table with product_id=3060 */
      product_id = (int)3060;

      /* Prepare the SQL statement */
      checkerr (errhp, OCIStmtPrepare(stmthp, errhp, insstmt, (ub4)
                                      strlen((char *) insstmt),
                                      (ub4) OCI_NTV_SYNTAX, (ub4)OCI_DEFAULT));

      /* Binds the bind positions */
      checkerr (errhp, OCIBindByPos(stmthp, &bndhp1, errhp, (ub4) 1,
                                    (void *) &product_id, (sb4) sizeof(product_id),
                                    SQLT_INT, (void *) 0, (ub2 *)0, (ub2 *)0,
                                    (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT));

      checkerr (errhp, OCIBindByPos(stmthp, &bndhp1, errhp, (ub4) 2,
                                    (void *) &product_id, (sb4) sizeof(product_id),
                                    SQLT_INT, (void *) 0, (ub2 *)0, (ub2 *)0,
                                    (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT));

      checkerr (errhp, OCIBindByPos(stmthp, &bndhp2, errhp, (ub4) 3,
                                    (void *) &Lob_loc, (sb4) 0,  SQLT_CLOB,
                                    (void *) 0, (ub2 *)0, (ub2 *)0,
                                    (ub4) 0, (ub4 *) 0, (ub4) OCI_DEFAULT));

      /* Execute the SQL statement */
      checkerr (errhp, OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4) 0,
                                      (CONST OCISnapshot*) 0, (OCISnapshot*) 0,
                                      (ub4) OCI_DEFAULT));
    }

**Parent topic:** Inserting a Row by Initializing a LOB Locator Bind Variable

#### 6.5.4 COBOL (Pro\*COBOL): Inserting a Row by Initializing a LOB Locator Bind Variable

You can insert a row by initializing a LOB locator bind variable in COBOL (Pro\*COBOL).

          * This file is installed in the following path when you install
          * the database: $ORACLE_HOME/rdbms/demo/lobs/procob/linsert.pco

           IDENTIFICATION DIVISION.
           PROGRAM-ID. INSERT-LOB.
           ENVIRONMENT DIVISION.
           DATA DIVISION.
           WORKING-STORAGE SECTION.

           01 BLOB1 SQL-BLOB.
           01  USERID   PIC X(11) VALUES "PM/password".
               EXEC SQL INCLUDE SQLCA END-EXEC.

           PROCEDURE DIVISION.
           INSERT-LOB.

               EXEC SQL WHENEVER SQLERROR DO PERFORM SQL-ERROR END-EXEC.
               EXEC SQL CONNECT :USERID END-EXEC.
          * Initialize the BLOB locator
               EXEC SQL ALLOCATE :BLOB1 END-EXEC.
          * Populate the LOB
               EXEC SQL WHENEVER NOT FOUND GOTO END-OF-BLOB END-EXEC.
               EXEC SQL
                  SELECT AD_PHOTO INTO :BLOB1 FROM PRINT_MEDIA
                   WHERE PRODUCT_ID = 2268 AND AD_ID = 21001 END-EXEC.

          * Insert the value with PRODUCT_ID of 3060
               EXEC SQL
                  INSERT INTO PRINT_MEDIA (PRODUCT_ID, AD_PHOTO)
                     VALUES (3060, 11001, :BLOB1)END-EXEC.

          * Free resources held by locator
           END-OF-BLOB.
               EXEC SQL WHENEVER NOT FOUND CONTINUE END-EXEC.
               EXEC SQL FREE :BLOB1 END-EXEC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               STOP RUN.

           SQL-ERROR.
               EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
               DISPLAY " ".
               DISPLAY "ORACLE ERROR DETECTED:".
               DISPLAY " ".
               DISPLAY SQLERRMC.
               EXEC SQL ROLLBACK WORK RELEASE END-EXEC.
               STOP RUN.

**Note:**

For simplicity in demonstrating this feature, this example does not perform the password management techniques that a deployed system normally uses. In a production environment, follow the Oracle Database password management guidelines, and disable any sample accounts. See [Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for password management guidelines and other security recommendations.

**Parent topic:** Inserting a Row by Initializing a LOB Locator Bind Variable

#### 6.5.5 C/C++ (Pro\*C/C++): Inserting a Row by Initializing a LOB Locator Bind Variable

You can insert a row by initializing a LOB locator bind variable in C/C++ (Pro\*C/C++).

    /* This file is installed in the following path when you install */
    /* the database: $ORACLE_HOME/rdbms/demo/lobs/proc/linsert.pc */

    #include <oci.h>
    #include <stdio.h>
    #include <sqlca.h>

    void Sample_Error()
    {
       EXEC SQL WHENEVER SQLERROR CONTINUE;
       printf("%.*s\n", sqlca.sqlerrm.sqlerrml, sqlca.sqlerrm.sqlerrmc);
       EXEC SQL ROLLBACK WORK RELEASE;
       exit(1);
    }

    void insertUseBindVariable_proc(Rownum, Lob_loc)
       int Rownum, Rownum2;
       OCIBlobLocator *Lob_loc;
    {
       EXEC SQL WHENEVER SQLERROR DO Sample_Error();
       EXEC SQL INSERT INTO Print_media (product_id, ad_id, ad_photo)
          VALUES (:Rownum, :Rownum2, :Lob_loc);
    }
    void insertBLOB_proc()
    {
       OCIBlobLocator *Lob_loc;

       /* Initialize the BLOB Locator: */
       EXEC SQL ALLOCATE :Lob_loc;

       /* Select the LOB from the row where product_id = 2268 and ad_id=21001: */
       EXEC SQL SELECT ad_photo INTO :Lob_loc
          FROM Print_media WHERE product_id = 2268 AND ad_id = 21001;

       /* Insert into the row where product_id = 3106 and ad_id = 13001: */
       insertUseBindVariable_proc(3106, 13001, Lob_loc);

       /* Release resources held by the locator: */
       EXEC SQL FREE :Lob_loc;
    }

    void main()
    {
       char *samp = "pm/password";
       EXEC SQL CONNECT :pm;
       insertBLOB_proc();
       EXEC SQL ROLLBACK WORK RELEASE;
    }

**Parent topic:** Inserting a Row by Initializing a LOB Locator Bind Variable

#### 6.5.6 Java (JDBC): Inserting a Row by Initializing a LOB Locator Bind Variable

You can insert a row by initializing a LOB locator bind variable in Java (JDBC).

    /* This file is installed in the following path when you install */
    /* the database: $ORACLE_HOME/rdbms/demo/lobs/java/linsert.java */

    // Core JDBC classes:
    import java.sql.DriverManager;
    import java.sql.Connection;
    import java.sql.Statement;
    import java.sql.PreparedStatement;
    import java.sql.ResultSet;
    import java.sql.SQLException;

    // Oracle Specific JDBC classes:
    import oracle.sql.*;
    import oracle.jdbc.driver.*;

    public class linsert
    {
      public static void main (String args [])
           throws Exception
      {
        // Load the Oracle JDBC driver
        DriverManager.registerDriver (new oracle.jdbc.driver.OracleDriver ());
        // Connect to the database:
        Connection conn =
           DriverManager.getConnection ("jdbc:oracle:oci8:@", "pm", "password");

        // It's faster when auto commit is off:
        conn.setAutoCommit (false);

        // Create a Statement:
        Statement stmt = conn.createStatement ();
        try
        {
           ResultSet rset = stmt.executeQuery (
      "SELECT ad_photo FROM Print_media WHERE product_id = 3106 AND ad_id = 13001");
           if (rset.next())
           {
              // retrieve the LOB locator from the ResultSet
              BLOB adphoto_blob = ((OracleResultSet)rset).getBLOB (1);
              OraclePreparedStatement ops =
              (OraclePreparedStatement) conn.prepareStatement(
    "INSERT INTO Print_media (product_id, ad_id, ad_photo) VALUES (2268, "
    + "21001, ?)");
              ops.setBlob(1, adphoto_blob);
              ops.execute();
              conn.commit();
              conn.close();
           }
        }
        catch (SQLException e)
        {
           e.printStackTrace();
        }
      }
    }

**Parent topic:** Inserting a Row by Initializing a LOB Locator Bind Variable

### 6.6 Updating a LOB with EMPTY_CLOB() or EMPTY_BLOB()

You can UPDATE a LOB with `EMPTY_CLOB()` or `EMPTY_BLOB()`.

**Note:**

Performance improves when you update the LOB with the actual value, instead of using `EMPTY_CLOB()` or `EMPTY_BLOB()`.

#### Preconditions

Before you write data to a persistent LOB, make the LOB column non-`NULL`; that is, the LOB column must contain a locator that points to an empty or populated LOB value. You can initialize a `BLOB` column value by using the function `EMPTY_BLOB()` as a default predicate. Similarly, a `CLOB` or `NCLOB` column value can be initialized by using the function `EMPTY_CLOB()`.

You can also initialize a LOB column with a character or raw string less than 4000 bytes in size. For example:

    UPDATE Print_media
              SET ad_sourcetext = 'This is a One Line Story'
              WHERE product_id = 2268;

You can perform this initialization during `CREATE` `TABLE `(see "Creating a Table Containing One or More LOB Columns") or, as in this case, by means of an `INSERT`.

The following example shows a series of updates using the `EMPTY_CLOB` operation to different data types.

    UPDATE Print_media SET ad_sourcetext = EMPTY_CLOB()
           WHERE product_id = 3060 AND ad_id = 11001;

    UPDATE Print_media SET ad_fltextn = EMPTY_CLOB()
           WHERE product_id = 3060 AND ad_id = 11001;

    UPDATE Print_media SET ad_photo = EMPTY_BLOB()
           WHERE product_id = 3060 AND ad_id = 11001;

**See Also:**

SQL: [Oracle Database SQL Language Reference](../sqlrf/UPDATE.md) for more information on `UPDATE`

**Parent topic:** DDL and DML Statements with LOBs

### 6.7 Updating a Row by Selecting a LOB From Another Table

You can use the SQL `UPDATE AS SELECT` statement to update a row containing a LOB column by selecting a LOB from another table.

To use this technique, you must update by means of a reference. For example, the following code updates data from `online_media`:

    Rem Updating a row by selecting a LOB from another table (persistent LOBs)

    UPDATE Print_media SET ad_sourcetext =
       (SELECT * product_text FROM online_media WHERE product_id = 3060);
        WHERE product_id = 3060 AND ad_id = 11001;

**Parent topic:** DDL and DML Statements with LOBs
