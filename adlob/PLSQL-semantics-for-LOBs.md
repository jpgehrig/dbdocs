## 8  PL/SQL Semantics for LOBs

Topics:

- PL/SQL Statements and Variables

- Implicit Conversions Between CLOB and VARCHAR2

- Explicit Conversion Functions

- PL/SQL Functions for Remote LOBs and BFILEs

<!-- -->

- PL/SQL Statements and Variables
- Implicit Conversions Between CLOB and VARCHAR2
- Explicit Conversion Functions
- PL/SQL Functions for Remote LOBs and BFILEs

**Parent topic:** [Value Semantics LOBs](value-semantic-LOBs.md)

### 8.1 PL/SQL Statements and Variables

In PL/SQL, semantic changes have been made.

**Note:**

Most discussions concerning PL/SQL semantics, and `CLOB`s and `VARCHAR2`s, also apply to `BLOB`s and `RAW`s, unless otherwise noted. In the text, `BLOB` and `RAW` are not explicitly mentioned.

PL/SQL semantics support is described in the following sections:

- Implicit Conversions Between CLOB and VARCHAR2

- Explicit Conversion Functions

- VARCHAR2 and CLOB in PL/SQL Built-In Functions

**Parent topic:** PL/SQL Semantics for LOBs

### 8.2 Implicit Conversions Between CLOB and VARCHAR2

Implicit conversions from `CLOB` to `VARCHAR2` and from `VARCHAR2` to `CLOB` data types are allowed in PL/SQL.

These conversions enable you to perform the following operations in your application:

- `CLOB` columns can be selected into `VARCHAR2` PL/SQL variables

- `VARCHAR2` columns can be selected into `CLOB` variables

- Assignment and parameter passing between `CLOB`s and `VARCHAR2`s

#### Accessing a CLOB as a VARCHAR2 in PL/SQL

The following example illustrates the way `CLOB` data is accessed when the `CLOB`s are treated as `VARCHAR2`s:

    declare
       myStoryBuf VARCHAR2(4001);
    BEGIN
       SELECT ad_sourcetext INTO myStoryBuf FROM print_media WHERE ad_id = 12001;
       -- Display Story by printing myStoryBuf directly
    END;
    /

#### Assigning a CLOB to a VARCHAR2 in PL/SQL

    declare
    myLOB CLOB;
    BEGIN
    SELECT 'ABCDE' INTO myLOB FROM print_media WHERE ad_id = 11001;
    -- myLOB is a temporary LOB.
    -- Use myLOB as a lob locator
      DBMS_OUTPUT.PUT_LINE('Is temp? '||DBMS_LOB.ISTEMPORARY(myLOB));
    END;
    /

**Parent topic:** PL/SQL Semantics for LOBs

### 8.3 Explicit Conversion Functions

In SQL and PL/SQL, the certain explicit conversion functions convert other data types to and from `CLOB`, `NCLOB`, and `BLOB` as part of the `LONG`-to-LOB migration:

- `TO_CLOB()`: Converting from `VARCHAR2`, `NVARCHAR2`, or `NCLOB` to a `CLOB`

- `TO_NCLOB()`: Converting from `VARCHAR2`, `NVARCHAR2`, or `CLOB` to an `NCLOB`

- `TO_BLOB()`: Converting from `RAW` to a `BLOB`

- `TO_CHAR()` converts a `CLOB` to a `CHAR` type. When you use this function to convert a character LOB into the database character set, if the LOB value to be converted is larger than the target type, then the database returns an error. Implicit conversions also raise an error if the LOB data does not fit.

- `TO_NCHAR()` converts an `NCLOB` to an `NCHAR` type. When you use this function to convert a character LOB into the national character set, if the LOB value to be converted is larger than the target type, then the database returns an error. Implicit conversions also raise an error if the LOB data does not fit.

- `CAST` does not directly support any of the LOB data types. When you use `CAST` to convert a `CLOB` value into a character data type, an `NCLOB` value into a national character data type, or a `BLOB` value into a `RAW` data type, the database implicitly converts the LOB value to character or raw data and then explicitly casts the resulting value into the target data type. If the resulting value is larger than the target type, then the database returns an error.

Other explicit conversion functions are not supported, such as, `TO_NUMBER()`, see [Table 7-1](SQL-semantics-and-LOBs.md).

**Note:**

LOBs do not support duplicate `LONG` binds.

- VARCHAR2 and CLOB in PL/SQL Built-In Functions

**See Also:**

[Migrating Columns from LONGs to LOBs](migrating-columns-from-LONGs-to-LOBs.md) for more information about conversion functions

**Parent topic:** PL/SQL Semantics for LOBs

#### 8.3.1 VARCHAR2 and CLOB in PL/SQL Built-In Functions

`CLOB` and `VARCHAR2` are two distinct types.

However, depending on the usage, a CLOB can be passed to SQL and PL/SQL `VARCHAR2` built-in functions, used exactly like a `VARCHAR2`. Or the variable can be passed into `DBMS_LOB` APIs, acting like a LOB locator. See the following combined example,"CLOB Variables in PL/SQL".

PL/SQL `VARCHAR2` functions and operators can take `CLOB`s as arguments or operands.

When the size of a `VARCHAR2` variable is not large enough to contain the result from a function that returns a `CLOB`, or a `SELECT` on a `CLOB` column, an error is raised and no operation is performed. This is consistent with `VARCHAR2` semantics.

##### CLOB Variables in PL/SQL

    1 declare
    2   myStory CLOB;
    3   revisedStory CLOB;
    4   myGist VARCHAR2(100);
    5   revisedGist VARCHAR2(100);
    6 BEGIN
    7  -- select a CLOB column into a CLOB variable
    8  SELECT Story INTO myStory FROM print_media WHERE product_id=10;
    9  -- perform VARCHAR2 operations on a CLOB variable
    10 revisedStory := UPPER(SUBSTR(myStory, 100, 1));
    11 -- revisedStory is a temporary LOB
    12 -- Concat a VARCHAR2 at the end of a CLOB
    13 revisedStory := revisedStory || myGist;
    14 -- The following statement raises an error because myStory is
    15 -- longer than 100 bytes
    16 myGist := myStory;
    17 END;

Please note that in line 10 of "CLOB Variables in PL/SQL", a temporary `CLOB` is implicitly created and is pointed to by the `revisedStory` `CLOB` locator. In the current interface the line can be expanded as:

    buffer VARCHAR2(32000)
    DBMS_LOB.CREATETEMPORARY(revisedStory);
    buffer := UPPER(DBMS_LOB.SUBSTR(myStory,100,1));
    DBMS_LOB.WRITE(revisedStory,length(buffer),1, buffer);

In line 13, `myGist` is appended to the end of the temporary LOB, which has the same effect of:

    DBMS_LOB.WRITEAPPEND(revisedStory, myGist, length(myGist));

In some occasions, implicitly created temporary LOBs in PL/SQL statements can change the representation of LOB locators previously defined. Consider the next example.

##### Change in Locator-Data Linkage

    1 declare
    2 myStory CLOB;
    3 amt number:=100;
    4 buffer VARCHAR2(100):='some data';
    5 BEGIN
    6 -- select a CLOB column into a CLOB variable
    7 SELECT Story INTO myStory FROM print_media WHERE product_id=10;
    8 DBMS_LOB.WRITE(myStory, amt, 1, buf);
    9 -- write to the persistent LOB in the table
    10
    11 myStory:= UPPER(SUBSTR(myStory, 100, 1));
    12 -- perform VARCHAR2 operations on a CLOB variable, temporary LOB created.
    13 -- Changes are not reflected in the database table from this point on.
    14
    15 update print_media set Story = myStory WHERE product_id = 10;
    16 -- an update is necessary to synchronize the data in the table.
    17 END;

After line 7, `myStory `represents a persistent LOB in `print_media`.

The `DBMS_LOB.WRITE` call in line 8 directly writes the data to the table.

No `UPDATE` statement is necessary. Subsequently in line 11, a temporary LOB is created and assigned to `myStory` because `myStory` is now used like a local `VARCHAR2` variable. The LOB locator `myStory` now points to the newly-created temporary LOB.

Therefore, modifications to `myStory` are no longer reflected in the database. To propagate the changes to the database table, an `UPDATE` statement becomes necessary now. Note again that for the previous persistent LOB, the `UPDATE` is not required.

**Note:**

If the SQL statement returns a LOB or a LOB is an `OUT` parameter for a PL/SQL function or procedure, you must test if it is a temporary LOB, and if it is, then free it after you are done with it.

##### Freeing Temporary LOBs Automatically and Manually

Temporary LOBs created in a program block as a result of a `SELECT` or an assignment are freed automatically at the end of the PL/SQL block or function or procedure. You must also free the temporary LOBs that were created with `DBMS_LOB.CREATETEMPORARY` to reclaim system resources and temporary tablespace. Do this by calling `DBMS_LOB.FREETEMPORARY` on the `CLOB` variable.

    declare
       Story1 CLOB;
       Story2 CLOB;
       StoryCombined CLOB;
       StoryLower CLOB;
    BEGIN
       SELECT Story INTO Story1 FROM print_media WHERE product_ID = 1;
       SELECT Story INTO Story2 FROM print_media WHERE product_ID = 2;
       StoryCombined := Story1 || Story2; -- StoryCombined is a temporary LOB
       -- Free the StoryCombined manually to free up space taken
       DBMS_LOB.FREETEMPORARY(StoryCombined);
       StoryLower := LOWER(Story1) || LOWER(Story2);
    END; -- At the end of block, StoryLower is freed.

**Parent topic:** Explicit Conversion Functions

### 8.4 PL/SQL Functions for Remote LOBs and BFILEs

**See Also:**

[PL/SQL Functions for Remote LOBs and BFILEs](distributed-LOBs.md) for PL/SQL functions that support remote `LOBs` and `BFILEs`

**Parent topic:** PL/SQL Semantics for LOBs
