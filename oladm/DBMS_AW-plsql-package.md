The DBMS_AW PL/SQL package provides procedures and functions for interacting with analytic workspaces.

This appendix contains the following topics:

- Managing Analytic Workspaces

- Embedding OLAP DML in SQL Statements

- Using the Sparsity Advisor

- Using the Aggregate Advisor

- Summary of DBMS_AW Subprograms

- One reference topic for each DBMS_AW subprogram

### B.1 Managing Analytic Workspaces

To interact with Oracle OLAP, you must attach an analytic workspace to your session. When you have DBMS_AW PL/SQL package installed you can perform this task from within SQL\*Plus. For example, you can use the following command to attach an analytic workspace with read-only access.

    EXECUTE dbms_aw.aw_attach ('awname');

Each analytic workspace is associated with a list of analytic workspaces. The read-only workspace `EXPRESS.AW`, which contains the OLAP engine code, is always attached last in the list. When you create a workspace, it is attached first in the list by default.

You can reposition an analytic workspace within the list by using keywords such as `FIRST` and `LAST`. For example, the following commands show how to move an analytic workspace called `MYAW.TEST2` from the second position to the first position on the list.

    EXECUTE dbms_aw.execute ('AW LIST');

    TEST1 R/O UNCHANGED GLOBAL.TEST1
    TEST2 R/O UNCHANGED GLOBAL.TEST2
    EXPRESS R/O UNCHANGED SYS.EXPRESS

    EXECUTE dbms_aw.aw_attach ('test2', FALSE, FALSE, 'FIRST');
    EXECUTE dbms_aw.execute ('AW LIST');

    TEST2 R/O UNCHANGED GLOBAL.TEST2
    TEST1 R/O UNCHANGED GLOBAL.TEST1
    EXPRESS R/O UNCHANGED SYS.EXPRESS

From within SQL\*Plus, you can rename workspaces and make copies of workspaces. If you have an analytic workspace attached with read/write access, you can update the workspace and save your changes in the permanent database table where the workspace is stored. You must do a SQL `COMMIT` to save the workspace changes within the database.

The following commands make a copy of the objects and data in workspace `test2` in a new workspace called `test3`, update `test3`, and commit the changes to the database.

    EXECUTE dbms_aw.aw_copy('test2', 'test3');
    EXECUTE dbms_aw.aw_update('test3');
    COMMIT;

### B.2 Embedding OLAP DML in SQL Statements

With the `DBMS_AW` package you can perform the full range of OLAP processing within analytic workspaces. You can import data from legacy workspaces, relational tables, or flat files. You can define OLAP objects and perform complex calculations.

**Note:**

If you use the `DBMS_AW` package to create analytic workspaces from scratch, you may not be able to use OLAP utilities, such as Analytic Workspace Manager and the `DBMS_AW` Aggregate Advisor, which require analytic workspaces of a particular structure.

#### B.2.1 Methods for Executing OLAP DML Commands

The `DBMS_AW` package provides several procedures for executing ad hoc OLAP DML commands. Using the `EXECUTE` or `INTERP_SILENT` procedures or the `INTERP` or `INTERCLOB` functions, you can execute a single OLAP DML command or a series of commands separated by semicolons.

Which procedures you use depends on how you want to direct output and on the size of the input and output buffers. For example, the `EXECUTE` procedure directs output to a printer buffer, the `INTERP_SILENT` procedure suppresses output, and the `INTERP` function returns the session log.

The `DBMS_AW` package also provides functions for evaluating OLAP expressions. The `EVAL_TEXT` function returns the result of a text expression, and `EVAL_NUMBER` returns the result of a numeric expression.

**Note:**

Do not confuse the `DBMS_AW` functions `EVAL_NUMBER` and `EVAL_TEXT` with the SQL function `OLAP_EXPRESSION`. See "[OLAP_EXPRESSION](OLAP_TABLE-sql-functions.md)" for more information.

#### B.2.2 Guidelines for Using Quotation Marks in OLAP DML Commands

The SQL processor evaluates the embedded OLAP DML commands, either in whole or in part, before sending them to Oracle OLAP for processing. Follow these guidelines when formatting the OLAP DML commands in the `olap-commands` parameter of `DBMS_AW` procedures:

- Wherever you would normally use a single quote (`'`) in an OLAP DML command, use two single quotes (`''`). The SQL processor strips one of the single quotes before it sends the OLAP DML command to Oracle OLAP.

- In the OLAP DML, a double quote (`"`) indicates the beginning of a comment.

### B.3 Using the Sparsity Advisor

Data can be stored in several different forms in an analytic workspace, depending on whether it is dense, sparse, or very sparse. The Sparsity Advisor is a group of subprograms in `DBMS_AW` that you can use to analyze the relational source data and get recommendations for storing it in an analytic workspace.

#### B.3.1 Data Storage Options in Analytic Workspaces

Analytic workspaces analyze and manipulate data in a multidimensional format that allocates one cell for each combination of dimension members. The cell can contain a data value, or it can contain an `NA` (null). Regardless of its content, the cell size is defined by the data type, for example, every cell in a `DECIMAL` variable is 8 bytes.

Variables can be either dense (they contain 30% or more cells with data values) or sparse (less than 30% data values). Most variables are sparse and many are extremely sparse.

Although data can also be stored in the multidimensional format used for analysis, other methods are available for storing sparse variables that make more efficient use of disk space and improve performance. Sparse data can be stored in a variable defined with a composite dimension. A composite has as its members the dimension-value combinations (called tuples) for which there is data. When a data value is added to a variable dimensioned by a composite, that action triggers the creation of a composite tuple. A composite is an index into one or more sparse data variables, and is used to store sparse data in a compact form. Very sparse data can be stored in a variable defined with a compressed composite, which uses a different algorithm for data storage from regular composites.

#### B.3.2 Selecting the Best Data Storage Method

In contrast to dimensional data, relational data is stored in tables in a very compact format, with rows only for actual data values. When designing an analytic workspace, you may have difficulty manually identifying sparsity in the source data and determining the best storage method. The Sparsity Advisor analyzes the source data in relational tables and recommends a storage method. The recommendations may include the definition of a composite and partitioning of the data variable.

The Sparsity Advisor consists of these procedures and functions:

- SPARSITY_ADVICE_TABLE Procedure
- ADD_DIMENSION_SOURCE Procedure
- ADVISE_SPARSITY Procedure
- ADVISE_DIMENSIONALITY Function
- ADVISE_DIMENSIONALITY Procedure

The Sparsity Advisor also provides a public table type for storing information about the dimensions of the facts being analyzed. Three objects are used to define the table type:

- `DBMS_AW$_COLUMNLIST_T`
- `DBMS_AW$_DIMENSION_SOURCE_T`
- `DBMS_AW$_DIMENSION_SOURCES_T`

The following SQL `DESCRIBE` statements show the object definitions.

    DESCRIBE dbms_aw$_columnlist_t
    dbms_aw$_columnlist_t TABLE OF VARCHAR2(100)

    DESCRIBE dbms_aw$_dimension_source_t
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     DIMNAME                                            VARCHAR2(100)
     COLUMNNAME                                         VARCHAR2(100)
     SOURCEVALUE                                        VARCHAR2(32767)
     DIMTYPE                                            NUMBER(3)
     HIERCOLS                                           DBMS_AW$_COLUMNLIST_T
     PARTBY                                             NUMBER(9)

    DESCRIBE dbms_aw$_dimension_sources_t
    dbms_aw$_dimension_sources_t TABLE OF DBMS_AW$_DIMENSION_SOURCE_T

#### B.3.3 Using the Sparsity Advisor

Take these steps to use the Sparsity Advisor:

1.  Call `SPARSITY_ADVICE_TABLE` to create a table for storing the evaluation of the Sparsity Advisor.
2.  Call `ADD_DIMENSION_SOURCE` for each dimension related by one or more columns to the fact table being evaluated.
    The information that you provide about these dimensions is stored in a `DBMS_AW$_DIMENSION_SOURCES_T` variable.
3.  Call `ADVISE_SPARSITY` to evaluate the fact table.
    Its recommendations are stored in the table created by `SPARSITY_ADVICE_TABLE`. You can use these recommendations to make your own judgements about defining variables in your analytic workspace, or you can continue with the following step.
4.  Call the `ADVISE_DIMENSIONALITY` procedure to get the OLAP DML object definitions for the recommended composite, partitioning, and variable definitions.
    or

    Use the `ADVISE_DIMENSIONALITY` function to get the OLAP DML object definition for the recommended composite and the dimension order for the variable definitions for a specific partition.

#### B.3.4 Example: Evaluating Sparsity in the GLOBAL Schema

The following example provides a SQL script for evaluating the sparsity of the `UNITS_HISTORY_FACT` table in the `GLOBAL` schema. In the `GLOBAL` analytic workspace, `UNITS_HISTORY_FACT` defines the Units Cube and is the source for the `UNITS` variable. `UNITS_HISTORY_FACT` is a fact table with a primary key composed of foreign keys from four dimension tables. A fifth column contains the facts for Unit Sales.

The `CHANNEL_DIM` and `CUSTOMER_DIM` tables contain all of the information for the Channel and Customer dimensions in a basic star configuration. Three tables in a snowflake configuration provide data for the Time dimension: `MONTH_DIM`, `QUARTER_DIM`, and `YEAR_DIM`. The `PRODUCT_CHILD_PARENT` table is a parent-child table and defines the Product dimension.

Example B-1 Sparsity Advisor Script for GLOBAL

    CONNECT global/global
    SET ECHO ON
    SET LINESIZE 300
    SET PAGESIZE 300
    SET SERVEROUT ON FORMAT WRAPPED

    -- Define and initialize an advice table named AW_SPARSITY_ADVICE
    BEGIN
         dbms_aw.sparsity_advice_table();
    EXCEPTION
         WHEN OTHERS THEN NULL;
    END;
    /

    TRUNCATE TABLE aw_sparsity_advice;

    DECLARE
         dimsources dbms_aw$_dimension_sources_t;
         dimlist VARCHAR2(500);
         sparsedim VARCHAR2(500);
         defs CLOB;
    BEGIN
    -- Provide information about all dimensions in the cube
         dbms_aw.add_dimension_source('channel', 'channel_id', dimsources,
             'channel_dim', dbms_aw.hier_levels,
              dbms_aw$_columnlist_t('channel_id', 'total_channel_id'));
         dbms_aw.add_dimension_source('product', 'item_id', dimsources,
              'product_child_parent', dbms_aw.hier_parentchild,
               dbms_aw$_columnlist_t('product_id', 'parent_id'));
         dbms_aw.add_dimension_source('customer', 'ship_to_id', dimsources,
             'customer_dim', dbms_aw.hier_levels,
              dbms_aw$_columnlist_t('ship_to_id', 'warehouse_id', 'region_id',
                   'total_customer_id'));
         dbms_aw.add_dimension_source('time', 'month_id', dimsources,
               'SELECT m.month_id, q.quarter_id, y.year_id
                    FROM time_month_dim m, time_quarter_dim q, time_year_dim y
                    WHERE m.parent=q.quarter_id AND q.parent=y.year_id',
                dbms_aw.hier_levels,
                dbms_aw$_columnlist_t('month_id', 'quarter_id', 'year_id'));

    -- Analyze fact table and provide advice without partitioning
         dbms_aw.advise_sparsity('units_history_fact', 'units_cube',
              dimsources, dbms_aw.advice_default, dbms_aw.partby_none);

    COMMIT;

    -- Generate OLAP DML for composite and variable definitions
    dimlist := dbms_aw.advise_dimensionality('units_cube', sparsedim,
               'units_cube_composite');
    dbms_output.put_line('Dimension list:  ' || dimlist);
    dbms_output.put_line('Sparse dimension:  ' || sparsedim);
    dbms_aw.advise_dimensionality(defs, 'units_cube');
    dbms_output.put_line('Definitions:  ');
    dbms_aw.printlog(defs);

    END;
    /

##### B.3.4.1 Advice from Sample Program

The script in Example B-1 generates the following information.

    Dimension list:  <channel units_cube_composite<product customer time>>
    Sparse dimension:  DEFINE units_cube_composite COMPOSITE <product customer time>
    Definitions:
    DEFINE units_cube.cp COMPOSITE <product customer time>
    DEFINE units_cube NUMBER VARIABLE <channel units_cube.cp<product customer time>>
    PL/SQL procedure successfully completed.

##### B.3.4.2 Information Stored in AW_SPARSITY_ADVICE Table

This SQL `SELECT` statement shows some columns from the `AW_SPARSITY_ADVICE` table, which is the basis for the recommended OLAP DML object definitions.

    SELECT fact, dimension, dimcolumn, membercount nmem, leafcount nleaf,
         advice, density
         FROM aw_sparsity_advice
         WHERE cubename='units_cube';


This query returns the following result set:

    FACT                 DIMENSION    DIMCOLUMN     NMEM  NLEAF ADVICE        DENSITY
    -------------------- ------------ ------------ ----- ------ ------------ --------
    units_history_fact   channel      channel_id       3      3 DENSE          .46182
    units_history_fact   product      item_id         48     36 SPARSE         .94827
    units_history_fact   customer     ship_to_id      61     61 SPARSE         .97031
    units_history_fact   time         month_id        96     79 SPARSE         .97664

### B.4 Using the Aggregate Advisor

The management of aggregate data within analytic workspaces can have significant performance implications. To determine an optimal set of dimension member combinations to preaggregate, you can use the `ADVISE_REL` and `ADVISE_CUBE` procedures in the `DBMS_AW` package. These procedures are known together as the Aggregate Advisor.

Based on a percentage that you specify, `ADVISE_REL` suggests a set of dimension members to preaggregate. The `ADVISE_CUBE` procedure suggests a set of members for each dimension of a cube.

#### B.4.1 Aggregation Facilities within the Workspace

Instructions for storing aggregate data are specified in an analytic workspace object called an aggmap. The OLAP DML `AGGREGATE` command uses the aggmap to preaggregate the data. Any data that is not preaggregated is aggregated dynamically by the `AGGREGATE` function when the data is queried.

Choosing a balance between static and dynamic aggregation depends on many factors including disk space, available memory, and the nature and frequency of the queries that run against the data. After weighing these factors, you may arrive at a percentage of the data to preaggregate.

Once you have determined the percentage of the data to preaggregate, you can use the Aggregate Advisor. These procedures analyze the distribution of dimension members within hierarchies and identify an optimal set of dimension members to preaggregate.

#### B.4.2 Example: Using the ADVISE_REL Procedure

Based on a precompute percentage that you specify, the `ADVISE_REL` procedure analyzes a family relation, which represents a dimension with all its hierarchical relationships, and returns a list of dimension members.

`ADVISE_CUBE` applies similar heuristics to each dimension in an aggmap for a cube.

**See Also:**

- "ADVISE_REL Procedure"

- ADVISE_CUBE Procedure

Example B-2 uses the following sample Customer dimension to illustrate the `ADVISE_REL` procedure.

##### Sample Dimension: Customer in the Global Analytic Workspace

The Customer dimension in `GLOBAL_AW.GLOBAL` has two hierarchies: `SHIPMENTS_ROLLUP` with four levels, and `MARKET_ROLLUP` with three levels. The dimension has 106 members. This number includes all members at each level and all level names.

The members of the Customer dimension are integer keys whose text values are defined in long and short descriptions.

The following OLAP DML commands show information about the representation of the Customer dimension, which is in database standard form.

    SET serveroutput ON
    ---- Number of members of Customer dimension
    EXECUTE dbms_aw.execute('SHOW STATLEN(customer)')
    106

    ---- Hierarchies in Customer dimension;
    EXECUTE dbms_aw.execute('REPORT W 40 customer_hierlist');
    CUSTOMER_HIERLIST
    ----------------------------------------
    MARKET_ROLLUP
    SHIPMENTS_ROLLUP

    ---- Levels in Customer dimension
    EXECUTE dbms_aw.execute('REPORT W 40 customer_levellist');

    CUSTOMER_LEVELLIST
    ----------------------------------------
    TOTAL_CUSTOMER
    REGION
    WAREHOUSE
    TOTAL_MARKET
    MARKET_SEGMENT
    ACCOUNT
    SHIP_TO
    ---- Levels in each hierarchy from leaf to highest
    EXECUTE dbms_aw.execute('REPORT W 20 customer_hier_levels');

    CUSTOMER_HIERL
    IST            CUSTOMER_HIER_LEVELS
    -------------- --------------------
    SHIPMENTS      SHIP_TO
                   WAREHOUSE
                   REGION
                   TOTAL_CUSTOMER
    MARKET_SEGMENT SHIP_TO
                   ACCOUNT
                   MARKET_SEGMENT
                   TOTAL_MARKET

    ---- Parent relation showing parent-child relationships in the Customer dimension
    ---- Only show the last 20 members
    EXECUTE dbms_aw.execute('LIMIT customer TO LAST 20');
    EXECUTE dbms_aw.execute('REPORT W 10 DOWN customer W 20 customer_parentrel');

               -----------CUSTOMER_PARENTREL------------
               ------------CUSTOMER_HIERLIST------------
    CUSTOMER      MARKET_ROLLUP       SHIPMENTS_ROLLUP
    ---------- -------------------- --------------------
    103        44                   21
    104        45                   21
    105        45                   21
    106        45                   21
    7          NA                   NA
    1          NA                   NA
    8          NA                   1
    9          NA                   1
    10         NA                   1
    11         NA                   8
    12         NA                   10
    13         NA                   9
    14         NA                   9
    15         NA                   8
    16         NA                   9
    17         NA                   8
    18         NA                   8
    19         NA                   9
    20         NA                   9
    21         NA                   10

    ---- Show text descriptions for the same twenty dimension members
    EXECUTE dbms_aw.execute('REPORT W 15 DOWN customer W 35 ACROSS customer_hierlist: <customer_short_description>');

    ALL_LANGUAGES: AMERICAN_AMERICA
                    ---------------------------CUSTOMER_HIERLIST---------------------------
                    -----------MARKET_ROLLUP----------- ---------SHIPMENTS_ROLLUP----------
    CUSTOMER            CUSTOMER_SHORT_DESCRIPTION          CUSTOMER_SHORT_DESCRIPTION
    --------------- ----------------------------------- -----------------------------------
    103             US Marine Svcs Washington           US Marine Svcs Washington
    104             Warren Systems New York             Warren Systems New York
    105             Warren Systems Philladelphia        Warren Systems Philladelphia
    106             Warren Systems Boston               Warren Systems Boston
    7               Total Market                        NA
    1               NA                                  All Customers
    8               NA                                  Asia Pacific
    9               NA                                  Europe
    10              NA                                  North America
    11              NA                                  Australia
    12              NA                                  Canada
    13              NA                                  France
    14              NA                                  Germany
    15              NA                                  Hong Kong
    16              NA                                  Italy
    17              NA                                  Japan
    18              NA                                  Singapore
    19              NA                                  Spain
    20              NA                                  United Kingdom
    21              NA                                  United States

The returned Customer members with their text descriptions, related levels, and related hierarchies, are shown as follows.

| Customer Member | Description        | Hierarchy          | Level            |
|:----------------|:-------------------|:-------------------|:-----------------|
| `31`            | `Kosh Enterprises` | `MARKET_ROLLUP`    | `ACCOUNT`        |
| `2`             | `Consulting`       | `MARKET_ROLLUP`    | `MARKET_SEGMENT` |
| `4`             | `Government`       | `MARKET_ROLLUP`    | `MARKET_SEGMENT` |
| `5`             | `Manufacturing`    | `MARKET_ROLLUP`    | `MARKET_SEGMENT` |
| `6`             | `Reseller`         | `MARKET_ROLLUP`    | `MARKET_SEGMENT` |
| `7`             | `TOTAL_MARKET`     | `MARKET_ROLLUP`    | `TOTAL_MARKET`   |
| `1`             | `TOTAL_CUSTOMER`   | `SHIPMENTS_ROLLUP` | `TOTAL_CUSTOMER` |
| `8`             | `Asia Pacific`     | `SHIPMENTS_ROLLUP` | `REGION`         |
| `9`             | `Europe`           | `SHIPMENTS_ROLLUP` | `REGION`         |
| `20`            | `United Kingdom`   | `SHIPMENTS_ROLLUP` | `WAREHOUSE`      |
| `21`            | `United States`    | `SHIPMENTS_ROLLUP` | `WAREHOUSE`      |

Example B-2 ADVISE_REL: Suggested Preaggregation of the Customer Dimension

This example uses the `GLOBAL` Customer dimension described in Sample Dimension: Customer in the Global Analytic Workspace.

The following PL/SQL statements assume that you want to preaggregate 25% of the Customer dimension. `ADVISE_REL` returns the suggested set of members in a valueset.

    SET serveroutput ON
    EXECUTE dbms_aw.execute('AW ATTACH global_aw.global');
    EXECUTE dbms_aw.execute('DEFINE customer_preagg VALUESET customer');
    EXECUTE dbms_aw.advise_rel('customer_parentrel', 'customer_preagg', 25);
    EXECUTE dbms_aw.execute('SHOW VALUES(customer_preagg)');
    31
    2
    4
    5
    6
    7
    1
    8
    9
    20
    21

### B.5 Summary of DBMS_AW Subprograms

The following table describes the subprograms provided in `DBMS_AW`.

Table B-1 DBMS_AW Subprograms

| Subprogram                             | Description                                                                                                                                                                                 |
|:---------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ADD_DIMENSION_SOURCE Procedure         | Populates a table type named `DBMS_AW$_DIMENSION_SOURCES_T` with information provided in its parameters about the dimensions of the cube.                                                   |
| ADVISE_CUBE Procedure                  | Suggests how to preaggregate a cube, based on a specified percentage of the cube's data.                                                                                                    |
| ADVISE_DIMENSIONALITY Function         | Returns a recommended composite definition for the cube and a recommended dimension order.                                                                                                  |
| ADVISE_DIMENSIONALITY Procedure        | Generates the OLAP DML commands for defining the recommended composite and measures in a cube.                                                                                              |
| ADVISE_PARTITIONING_DIMENSION Function | Identifies the dimension that the Sparsity Advisor partitioned over.                                                                                                                        |
| ADVISE_PARTITIONING_LEVEL Function     | Returns the level used by the Sparsity Advisor for partitioning over a dimension.                                                                                                           |
| ADVISE_REL Procedure                   | Suggests how to preaggregate a dimension, based on a specified percentage of the dimension's members.                                                                                       |
| ADVISE_SPARSITY Procedure              | Analyzes a fact table for sparsity and populates a table with the results of its analysis.                                                                                                  |
| AW_ATTACH Procedure                    | Attaches an analytic workspace to a session.                                                                                                                                                |
| AW_COPY Procedure                      | Creates a new analytic workspace and populates it with the object definitions and data from another analytic workspace.                                                                     |
| AW_CREATE Procedure                    | Creates a new, empty analytic workspace.                                                                                                                                                    |
| AW_DELETE Procedure                    | Deletes an analytic workspace                                                                                                                                                               |
| AW_DETACH Procedure                    | Detaches an analytic workspace from a session.                                                                                                                                              |
| AW_RENAME Procedure                    | Changes the name of an analytic workspace.                                                                                                                                                  |
| AW_TABLESPACE Function                 | Returns the name of the tablespace in which a particular analytic workspace is stored.                                                                                                      |
| AW_UPDATE Procedure                    | Saves changes made to an analytic workspace.                                                                                                                                                |
| CONVERT Procedure                      | Converts an analytic workspace from 9i to 10g storage format.                                                                                                                               |
| EVAL_NUMBER Function                   | Returns the result of a numeric expression in an analytic workspace.                                                                                                                        |
| EVAL_TEXT Function                     | Returns the result of a text expression in an analytic workspace.                                                                                                                           |
| EXECUTE Procedure                      | Executes one or more OLAP DML commands. Input and output is limited to 4K. Typically used in an interactive session using an analytic workspace.                                            |
| GETLOG Function                        | Returns the session log from the last execution of the `INTERP` or `INTERPCLOB` functions.                                                                                                  |
| INFILE Procedure                       | Executes the OLAP DML commands specified in a file.                                                                                                                                         |
| INTERP Function                        | Executes one or more OLAP DML commands. Input is limited to 4K and output to 4G. Typically used in applications when the 4K limit on output for the `EXECUTE` procedure is too restrictive. |
| INTERPCLOB Function                    | Executes one or more OLAP DML commands. Input and output are limited to 4G. Typically used in applications when the 4K input limit of the `INTERP` function is too restrictive.             |
| INTERP_SILENT Procedure                | Executes one or more OLAP DML commands and suppresses the output. Input is limited to 4K and output to 4G.                                                                                  |
| OLAP_ON Function                       | Returns a boolean indicating whether or not the OLAP option is installed in the database.                                                                                                   |
| OLAP_RUNNING Function                  | Returns a boolean indicating whether or not the OLAP option has been initialized in the current session.                                                                                    |
| PRINTLOG Procedure                     | Prints a session log returned by the `INTERP`, `INTERCLOB`, or `GETLOG` functions.                                                                                                          |
| RUN Procedure                          | Executes one or more OLAP DML commands.                                                                                                                                                     |
| SHUTDOWN Procedure                     | Shuts down the current OLAP session.                                                                                                                                                        |
| SPARSITY_ADVICE_TABLE Procedure        | Creates a table which the `ADVISE_SPARSITY` procedure uses to store the results of its analysis.                                                                                            |
| STARTUP Procedure                      | Starts an OLAP session without attaching a user-defined analytic workspace.                                                                                                                 |

### B.6 ADD_DIMENSION_SOURCE Procedure

The `ADD_DIMENSION_SOURCE` procedure populates a table type named `DBMS_AW$_DIMENSION_SOURCES_T` with information about the dimensions of a cube. This information is analyzed by the `ADVISE_SPARSITY` procedure.

**See Also:**

"Using the Sparsity Advisor"

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    ADD_DIMENSION_SOURCE (
              dimname  IN      VARCHAR2,
              colname  IN      VARCHAR2,
              sources  IN OUT  dbms_aw$_dimension_sources_t,
              srcval   IN      VARCHAR2     DEFAULT NULL,
              dimtype  IN      NUMBER       DEFAULT NO_HIER,
              hiercols IN      columnlist_t DEFAULT NULL,
              partby   IN      NUMBER       DEFAULT PARTBY_DEFAULT);

#### Parameters

Table B-2 ADD_DIMENSION_SOURCE Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `dimname`  | A name for the dimension. For clarity, use the logical name of the dimension in the analytic workspace.                                                                                                                                                                                                                                                                                                                                                                                                               |
| `colname`  | The name of the column in the fact table that maps to the dimension members for dimname.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `sources`  | The name of an object (such as a PL/SQL variable) defined with a data type of `DBMS_AW$_DIMENSION_SOURCES_T`, which are used to store the information provided by the other parameters.                                                                                                                                                                                                                                                                                                                               |
| `srcval`   | The name of a dimension table, or a SQL statement that returns the columns that define the dimension. If this parameter is omitted, then colname is used.                                                                                                                                                                                                                                                                                                                                                             |
| `dimtype`  | One of the following hierarchy types:<br>• `DBMS_AW.HIER_LEVELS ` Level-based hierarchy<br>• `DBMS_AW.HIER_PARENTCHILD` Parent-child hierarchy<br>• `DBMS_AW.MEASURE ` Measure dimension<br>• `DBMS_AW.NO_HIER ` No hierarchy                                                                                                                                                                                                                                                                                         |
| `hiercols` | The names of the columns that define a hierarchy.<br>For level-based hierarchies, list the base-level column first and the topmost-level column last. If the dimension has multiple hierarchies, choose the one you predict will be used the most frequently; only list the columns that define the levels of this one hierarchy.<br>For parent-child hierarchies, list the child column first, then the parent column.<br>For measure dimensions, list the columns in the fact table that becomes dimension members. |
| `partby`   | A keyword that controls partitioning. Use one of the following values:<br>• `DBMS_AW.PARTBY_DEFAULT` Allow the Sparsity Advisor to determine whether or not partitioning is appropriate for this dimension.<br>• `DBMS_AW.PARTBY_NONE` Do not allow partitioning on this dimension.<br>• `DBMS_AW.PARTBY_FORCE` Force partitioning on this dimension.<br>• Important: Do not force partitioning on multiple dimensions.<br>• An integer value for the number of partitions you want created for this dimension.       |

#### Example

The following PL/SQL program fragment provides information about the `TIME` dimension for use by the Sparsity Advisor. The source data for the dimension is stored in a dimension table named `TIME_DIM`. Its primary key is named `MONTH_ID`, and the foreign key column in the fact table is also named `MONTH_ID`. The dimension hierarchy is level based as defined by the columns `MONTH_ID`, `QUARTER_ID`, and `YEAR_ID`.

The program declares a PL/SQL variable named `DIMSOURCES` with a table type of `DBMS_AW$_DIMENSION_SOURCES_T` to store the information.

    DECLARE
         dimsources dbms_aw$_dimension_sources_t;
    BEGIN
         dbms_aw.add_dimension_source('time', 'month_id', dimsources,
              'time_dim', dbms_aw.hier_levels,
              dbms_aw$_columnlist_t('month_id', 'quarter_id', 'year_id'));
                       .
                       .
                       .
    END;
    /

### B.7 ADVISE_CUBE Procedure

The `ADVISE_CUBE` procedure helps you determine how to preaggregate a cube in an analytic workspace. When you specify a percentage of the cube's data to preaggregate, `ADVISE_CUBE` recommends a set of members to preaggregate from each of the cube's dimensions.

The `ADVISE_CUBE` procedure takes an aggmap and a precompute percentage as input. The aggmap must have a precompute clause in each of its `RELATION` statements. The precompute clause must consist of a valueset. Based on the precompute percentage that you specify, `ADVISE_CUBE` returns a set of dimension members in each valueset.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Aggregate Advisor"

#### Syntax

    ADVISE_CUBE (
              aggmap_name             IN   VARCHAR2,
              precompute_percentage   IN   INTEGER DEFAULT 20,
              compressed              IN   BOOLEAN DEFAULT FALSE);

#### Parameters

Table B-3 ADVISE_CUBE Procedure Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                    |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `aggmap_name`           | The name of an aggmap associated with the cube.<br>Each `RELATION` statement in the aggmap must have a precompute clause containing a valueset. `ADVISE_CUBE` returns a list of dimension members in each valueset. If the valueset is not empty, `ADVISE_CUBE` deletes its contents before adding new values. |
| `precompute_percentage` | A percentage of the cube's data to preaggregate. The default is 20%.                                                                                                                                                                                                                                           |
| `compressed`            | Controls whether the advice is for a regular composite (`FALSE`) or a compressed composite (`TRUE`).                                                                                                                                                                                                           |

#### Example

This example illustrates the `ADVISE_CUBE` procedure with a cube called `UNITS` dimensioned by `PRODUCT` and `TIME`. `ADVISE_CUBE` returns the dimension combinations to include if you want to preaggregate 40% of the cube's data.

    SET SERVEROUTPUT ON
    --- View valuesets
    EXECUTE dbms_aw.execute('describe prodvals');
         DEFINE PRODVALS VALUESET PRODUCT
    EXECUTE dbms_aw.execute('describe timevals');
         DEFINE TIMEVALS VALUESET TIME
    --- View aggmap
    EXECUTE dbms_aw.execute ('describe units_agg');
         DEFINE UNITS_AGG AGGMAP
              RELATION product_parentrel PRECOMPUTE (prodvals)
              RELATION time_parentrel PRECOMPUTE (timevals)
    EXECUTE dbms_aw.advise_cube ('units_agg', 40);

    ---- The results are returned in the prodvals and timevals valuesets

### B.8 ADVISE_DIMENSIONALITY Function

The `ADVISE_DIMENSIONALITY` function returns an OLAP DML definition of a composite dimension and the dimension order for variables in the cube, based on the sparsity recommendations generated by the `ADVISE_SPARSITY` procedure for a particular partition.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Sparsity Advisor"

#### Syntax

    ADVISE_DIMENSIONALITY (
              cubename   IN     VARCHAR2,
              sparsedfn  OUT    VARCHAR2
              sparsename IN     VARCHAR2 DEFAULT NULL,
              partnum    IN     NUMBER DEFAULT 1,
              advtable   IN     VARCHAR2 DEFAULT NULL)
         RETURN VARCHAR2;

#### Parameters

Table B-4 ADVISE_DIMENSIONALITY Function Parameters

| Parameter    | Description                                                                                                     |
|:-------------|:----------------------------------------------------------------------------------------------------------------|
| `cubename`   | The same cubename value provided in the call to `ADVISE_SPARSITY`.                                              |
| `sparsedfn`  | The name of an object (such as a PL/SQL variable) in which the definition of the composite dimension is stored. |
| `sparsename` | An object name for the composite. The default value is `cubename``.cp`.                                         |
| `partnum`    | The number of a partition. By default, you see only the definition of the first partition.                      |
| `advtable`   | The name of a table created by the `SPARSITY_ADVICE_TABLE` procedure for storing the results of analysis.       |

#### Example

The following PL/SQL program fragment defines two variables to store the recommendations returned by the `ADVISE_DIMENSIONALITY` function. `SPARSEDIM` stores the definition of the recommended composite, and `DIMLIST` stores the recommended dimension order of the cube.

    DECLARE
         sparsedim VARCHAR2(500);
         dimlist VARCHAR2(500);
    BEGIN
    -- Calls to ADD_DIMENSION_SOURCE and ADVISE_SPARSITY omitted here
              .
              .
              .
    dimlist := dbms_aw.advise_dimensionality('units_cube', sparsedim);
    dbms_output.put_line('Sparse dimension:  ' || sparsedim);
    dbms_output.put_line('Dimension list:  ' || dimlist);
    END;
    /

The program uses `DBMS_OUTPUT.PUT_LINE` to display the results of the analysis. The Sparsity Advisor recommends a composite dimension for the sparse dimensions, which are `PRODUCT`, `CUSTOMER`, and `TIME`. The recommended dimension order for `UNITS_CUBE` is `CHANNEL` followed by this composite.

    Sparse dimension:  DEFINE units_cube.cp COMPOSITE <product customer time>
    Dimension list:  channel units_cube.cp<product customer time>

The next example uses the Sparsity Advisor to evaluate the `SALES` table in the Sales History sample schema. A `WHILE` loop displays the recommendations for all partitions.

    DECLARE
         dimlist VARCHAR2(500);
         sparsedim VARCHAR2(500);
         counter NUMBER(2) := 1;
         maxpart NUMBER(2);
    BEGIN
    -- Calls to ADD_DIMENSION_SOURCE and ADVISE_SPARSITY omitted here
              .
              .
              .

    SELECT MAX(partnum) INTO maxpart FROM sh_sparsity_advice;
    WHILE counter <= maxpart LOOP
    dimlist := dbms_aw.advise_dimensionality('sales_cube', sparsedim,
       'sales_cube_composite', counter, 'sh_sparsity_advice');
    dbms_output.put_line('Dimension list:  ' || dimlist);
    dbms_output.put_line('Sparse dimension:  ' || sparsedim);
    counter := counter+1;
    END LOOP;
    dbms_aw.advise_dimensionality(defs,'sales_cube', 'sales_cube_composite',
       'DECIMAL', 'sh_sparsity_advice');
    dbms_output.put_line('Definitions:  ');
    dbms_aw.printlog(defs);
    END;
    /

The Sparsity Advisor recommends 11 partitions; the first ten use the same composite. The last partition uses a different composite. (The `SH_SPARSITY_ADVICE` table shows that `TIME_ID` is dense in the last partition, whereas it is very sparse in the other partitions.)

    Dimension list:  sales_cube_composite<time channel product promotion customer>
    Sparse dimension:  DEFINE sales_cube_composite COMPOSITE COMPRESSED <time channel product promotion customer>
    Dimension list:   sales_cube_composite<time channel product promotion customer>
    Sparse dimension:  DEFINE sales_cube_composite COMPOSITE COMPRESSED <time channel product promotion customer>
                       .
                       .
                       .
    Dimension list:  time sales_cube_composite<channel product promotion customer>
    Sparse dimension:  DEFINE sales_cube_composite COMPOSITE COMPRESSED <channel product promotion customer>

### B.9 ADVISE_DIMENSIONALITY Procedure

The `ADVISE_DIMENSIONALITY` procedure evaluates the information provided by the `ADVISE_SPARSITY` procedure and generates the OLAP DML commands for defining a composite and a variable in the analytic workspace.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Sparsity Advisor"

#### Syntax

    ADVISE_DIMENSIONALITY (
              output     OUT    CLOB,
              cubename   IN     VARCHAR2,
              sparsename IN     VARCHAR2 DEFAULT NULL,
              dtype      IN     VARCHAR2 DEFAULT 'NUMBER',
              advtable   IN     VARCHAR2 DEFAULT NULL);

#### Parameters

Table B-5 ADVISE_DIMENSIONALITY Procedure Parameters

| Parameter    | Description                                                                                                             |
|:-------------|:------------------------------------------------------------------------------------------------------------------------|
| `output`     | The name of an object (such as a PL/SQL variable) in which the recommendations of the procedure is stored.              |
| `cubename`   | The same cubename value provided in the call to `ADVISE_SPARSITY`.                                                      |
| `sparsename` | An object name for the sample composite. The default value is `cubename``.cp`.                                          |
| `dtype`      | The OLAP DML data type of the sample variable.                                                                          |
| `advtable`   | The name of the table created by the `SPARSITY_ADVICE_TABLE` procedure in which the results of the analysis are stored. |

#### Example

The following PL/SQL program fragment defines a variable named `DEFS` to store the recommended definitions.

    DECLARE
         defs CLOB;
    BEGIN
    -- Calls to ADD_DIMENSION_SOURCE and ADVISE_SPARSITY omitted here
              .
              .
              .
    dbms_aw.advise_dimensionality(defs, 'units_cube_measure_stored',
         'units_cube_composite', 'DECIMAL');
    dbms_output.put_line('Definitions:  ');
    dbms_aw.printlog(defs);
    END;
    /

The program uses the `DBMS_OUTPUT.PUT_LINE` and `DBMS_AW.PRINTLOG` procedures to display the recommended object definitions.

    Definitions:
    DEFINE units_cube.cp COMPOSITE <product customer time>
    DEFINE units_cube NUMBER VARIABLE <channel units_cube.cp<product customer time>>

In contrast to the Global schema, which is small and dense, the Sales cube in the Sales History sample schema is large and very sparse, and the Sparsity Advisor recommends 11 partitions. The following excerpt shows some additional OLAP DML definitions for defining a partition template and moving the `TIME` dimension members to the various partitions.

    Definitions:
    DEFINE sales_cube_composite_p1 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p2 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p3 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p4 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p5 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p6 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p7 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p8 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p9 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p10 COMPOSITE COMPRESSED <time channel product promotion customer>
    DEFINE sales_cube_composite_p11 COMPOSITE <channel product promotion customer>
    DEFINE sales_cube_pt PARTITION TEMPLATE <time channel product promotion customer> -
      PARTITION BY LIST (time) -
       (PARTITION p1 VALUES () <sales_cube_composite_p1<>> -
        PARTITION p2 VALUES () <sales_cube_composite_p2<>> -
        PARTITION p3 VALUES () <sales_cube_composite_p3<>> -
        PARTITION p4 VALUES () <sales_cube_composite_p4<>> -
        PARTITION p5 VALUES () <sales_cube_composite_p5<>> -
        PARTITION p6 VALUES () <sales_cube_composite_p6<>> -
        PARTITION p7 VALUES () <sales_cube_composite_p7<>> -
        PARTITION p8 VALUES () <sales_cube_composite_p8<>> -
        PARTITION p9 VALUES () <sales_cube_composite_p9<>> -
        PARTITION p10 VALUES () <sales_cube_composite_p10<>> -
        PARTITION p11 VALUES () <time sales_cube_composite_p11<>>)
    MAINTAIN sales_cube_pt MOVE TO PARTITION p1 -
       '06-JAN-98', '07-JAN-98', '14-JAN-98', '21-JAN-98', -
       '24-JAN-98', '28-JAN-98', '06-FEB-98', '07-FEB-98', -
       '08-FEB-98', '16-FEB-98', '21-FEB-98', '08-MAR-98', -
       '20-MAR-98', '03-JAN-98', '26-JAN-98', '27-JAN-98'
    MAINTAIN sales_cube_pt MOVE TO PARTITION p1 -
       '31-JAN-98', '11-FEB-98', '12-FEB-98', '13-FEB-98', -
       '15-FEB-98', '17-FEB-98', '14-MAR-98', '18-MAR-98', -
       '26-MAR-98', '30-MAR-98', '05-JAN-98', '08-JAN-98', -
       '10-JAN-98', '16-JAN-98', '23-JAN-98', '01-FEB-98'
    MAINTAIN sales_cube_pt MOVE TO PARTITION p1 -
       '14-FEB-98', '28-FEB-98', '05-MAR-98', '07-MAR-98', -
       '15-MAR-98', '19-MAR-98', '17-JAN-98', '18-JAN-98', -
       '22-JAN-98', '25-JAN-98', '03-FEB-98', '10-FEB-98', -
       '19-FEB-98', '22-FEB-98', '23-FEB-98', '26-FEB-98'
              .
              .
              .

### B.10 ADVISE_PARTITIONING_DIMENSION Function

The `ADVISE_PARTITIONING_DIMENSION` function identifies the dimension that the Sparsity Advisor partitioned over, if any. It returns `NULL` when the Sparsity Advisor did not partition the cube.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Sparsity Advisor"

#### Syntax

    ADVISE_PARTITIONING_DIMENSION (
              cubename   IN  VARCHAR2,
              sources    IN  dbms_aw$_dimension_sources_t,
              advtable   IN  VARCHAR2 DEFAULT NULL)
         RETURN VARCHAR2;

#### Parameters

Table B-6 ADVISE_PARTITIONING_DIMENSION Function Parameters

| Parameter  | Description                                                                                                                                                                               |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cubename` | The same cubename value provided in the call to `ADVISE_SPARSITY`.                                                                                                                        |
| `sources`  | The name of an object (such as a PL/SQL variable) defined with a data type of `DBMS_AW$_DIMENSION_SOURCES_T`, which was populated by `ADD_DIMENSION_SOURCE` for use by `ADVISE_SPARSITY`. |
| `advtable` | The name of a table created by the `SPARSITY_ADVICE_TABLE` procedure for storing the results of analysis.                                                                                 |

#### Example

The following program fragment shows the `ADVISE_PARTITIONING_DIMENSION` function being used to query the results after using the Sparsity Advisor.

    DECLARE
         dimsources dbms_aw$_dimension_sources_t;
    BEGIN
    -- Calls to ADD_DIMENSION_SOURCE and ADVISE_SPARSITY omitted here
         .
         .
         .
    dbms_output.put_line('Partitioning Dimension: ' ||
         dbms_aw.advise_partitioning_dimension('units_cube', dimsources,
        'aw_sparsity_advice'));
    END;
    /

The program uses `DBMS_OUTPUT` to display the partitioning dimension, which in this case is the `TIME` dimension.

    Partitioning Dimension: time

### B.11 ADVISE_PARTITIONING_LEVEL Function

The `ADVISE_PARTITIONING_LEVEL` function returns the level used by the Sparsity Advisor for partitioning over a dimension. It returns `NULL` if the Sparsity Advisor did not partition the cube, and raises an exception if the dimension hierarchy is not level-based.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Sparsity Advisor"

#### Syntax

    ADVISE_PARTITIONING_LEVEL (
              cubename   IN  VARCHAR2,
              sources    IN  dbms_aw$_dimension_sources_t,
              advtable   IN  VARCHAR2 DEFAULT NULL)
         RETURN VARCHAR2;

#### Parameters

Table B-7 ADVISE_PARTITIONING_LEVEL Function Parameters

| Parameter  | Description                                                                                                                                                                               |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cubename` | The same cubename value provided in the call to `ADVISE_SPARSITY`.                                                                                                                        |
| `sources`  | The name of an object (such as a PL/SQL variable) defined with a data type of `DBMS_AW$_DIMENSION_SOURCES_T`, which was populated by `ADD_DIMENSION_SOURCE` for use by `ADVISE_SPARSITY`. |
| `advtable` | The name of a table created by the `SPARSITY_ADVICE_TABLE` procedure for storing the results of analysis.                                                                                 |

#### Example

The following program fragment shows the `ADVISE_PARTITIONING_LEVEL` function being used to query the results after using the Sparsity Advisor.

    DECLARE
         dimsources dbms_aw$_dimension_sources_t;
    BEGIN
    -- Calls to ADD_DIMENSION_SOURCE and ADVISE_SPARSITY omitted here
         .
         .
         .
    dbms_output.put_line('Partitioning Level: ' ||
         dbms_aw.advise_partitioning_level('units_cube', dimsources,
        'aw_sparsity_advice'));
    END;
    /

The program uses `DBMS_OUTPUT` to display the partitioning level, which in this case is `YEAR`.

    Partitioning Level: year

### B.12 ADVISE_REL Procedure

The `ADVISE_REL` procedure helps you determine how to preaggregate a dimension in an analytic workspace. When you specify a percentage of the dimension to preaggregate, `ADVISE_REL` recommends a set of dimension members.

The `ADVISE_REL` procedure takes a family relation, a valueset, and a precompute percentage as input. The family relation is an object that specifies the hierarchical relationships between the members of a dimension. The valueset must be defined from the dimension to be analyzed. Based on the precompute percentage that you specify, `ADVISE_REL` returns a set of dimension members in the valueset.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Aggregate Advisor"

#### Syntax

    ADVISE_REL (
              family_relation_name    IN   VARCHAR2,
              valueset_name           IN   VARCHAR2,
              precompute_percentage   IN   INTEGER DEFAULT 20,
              compressed              IN   BOOLEAN DEFAULT FALSE);

#### Parameters

Table B-8 ADVISE_REL Procedure Parameters

| Parameter               | Description                                                                                                                                                                                                                       |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `family_relation_name`  | The name of a family relation, which specifies a dimension and the hierarchical relationships between the dimension members.                                                                                                      |
| `valueset_name`         | The name of a valueset to contain the results of the procedure. The valueset must be defined from the dimension in the family relation. If the valueset is not empty, `ADVISE_REL` deletes its contents before adding new values. |
| `precompute_percentage` | A percentage of the dimension to preaggregate. The default is 20%.                                                                                                                                                                |
| `compressed`            | Controls whether the advice is for a regular composite (`FALSE`) or a compressed composite (`TRUE`).                                                                                                                              |

### B.13 ADVISE_SPARSITY Procedure

The `ADVISE_SPARSITY` procedure analyzes a fact table for sparsity using information about its dimensions provided by the `ADD_DIMENSION_SOURCE` procedure. It populates a table created by the `SPARSITY_ADVICE_TABLE` procedure with the results of its analysis.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Sparsity Advisor"

#### Output Description

The following table describes the information generated by `ADVISE_SPARSITY`:

Table B-9 Output Column Descriptions

| Column        | Data Type        | NULL       | Description                                                                                                                                                                    |
|:--------------|:-----------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CUBENAME`    | `VARCHAR2(100)`  | `NOT NULL` | The values of cubename in calls to `ADVISE_SPARSITY`, typically the name of the logical cube.                                                                                  |
| `FACT`        | `VARCHAR2(4000)` | `NOT NULL` | The values of fact in calls to `ADVISE_SPARSITY`; the name of the fact table that provides the source data for one or more analytic workspace variables.                       |
| `DIMENSION`   | `VARCHAR2(100)`  | `NOT NULL` | The logical names of the cube's dimensions; the dimensions described in calls to `ADVISE_DIMENSIONALITY`.                                                                      |
| `DIMCOLUMN`   | `VARCHAR2(100)`  |            | The names of dimension columns in fact (the source fact table), which relate to a dimension table.                                                                             |
| `DIMSOURCE`   | `VARCHAR2(4000)` |            | The names of the dimension tables.                                                                                                                                             |
| `MEMBERCOUNT` | `NUMBER(12,0)`   |            | The total number of dimension members at all levels.                                                                                                                           |
| `LEAFCOUNT`   | `NUMBER(12,0)`   |            | The number of dimension members at the leaf (or least aggregate) level.                                                                                                        |
| `ADVICE`      | `VARCHAR2(10)`   | `NOT NULL` | The sparsity evaluation of the dimension: `DENSE`, `SPARSE`, or `COMPRESSED`.                                                                                                  |
| `POSITION`    | `NUMBER(4,0)`    | `NOT NULL` | The recommended order of the dimensions.                                                                                                                                       |
| `DENSITY`     | `NUMBER(11,8)`   |            | A number that provides an indication of sparsity relative to the other dimensions. The larger the number, the more sparse the dimension.                                       |
| `PARTNUM`     | `NUMBER(6,0)`    | `NOT NULL` | The number of the partition described in the `PARTBY` and `PARTTOPS` columns. If partitioning is not recommended, then `1` is the maximum number of partitions.                |
| `PARTBY`      | `CLOB`           |            | A list of all dimension members that should be stored in this partition. This list is truncated in SQL\*Plus unless you significantly increase the size of the `LONG` setting. |
| `PARTTOPS`    | `CLOB`           |            | A list of top-level dimension members for this partition.                                                                                                                      |

#### Syntax

    ADVISE_SPARSITY (
              fact       IN      VARCHAR2,
              cubename   IN      VARCHAR2,
              dimsources IN      dbms_aw$_dimension_sources_t,
              advmode    IN      BINARY_INTEGER DEFAULT ADVICE_DEFAULT,
              partby     IN      BINARY_INTEGER DEFAULT PARTBY_DEFAULT,
              advtable   IN      VARCHAR2 DEFAULT NULL);

#### Parameters

Table B-10 ADVISE_SPARSITY Procedure Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                                    |
|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `fact`       | The name of the source fact table.                                                                                                                                                                                                                                                             |
| `cubename`   | A name for the facts being analyzed, such as the name of the logical cube in the analytic workspace.                                                                                                                                                                                           |
| `dimsources` | The name of the object type where the `ADD_DIMENSION_SOURCE` procedure has stored information about the cube's dimensions.                                                                                                                                                                     |
| `advmode`    | The level of advise you want to see. Select one of the following values:<br>• `DBMS_AW.ADVICE_DEFAULT`<br>• `DBMS_AW.ADVICE_FAST`<br>• `DBMS_AW.ADVICE_FULL`                                                                                                                                   |
| `partby`     | A keyword that controls partitioning. Use one of the following values:<br>• `DBMS_AW.PARTBY_DEFAULT` Allow the Sparsity Advisor to determine whether or not partitioning is appropriate.<br>• `DBMS_AW.PARTBY_NONE` Do not allow partitioning.<br>• `DBMS_AW.PARTBY_FORCE` Force partitioning. |
| `advtable`   | The name of a table created by the procedure for storing the results of analysis.                                                                                                                                                                                                              |

#### Example

The following PL/SQL program fragment analyzes the sparsity characteristics of the `UNITS_HISTORY_FACT` table.

    DECLARE
         dimsources dbms_aw$_dimension_sources_t;
    BEGIN
    -- Calls to ADD_DIMENSION_SOURCE for each dimension in the cube
                    .
                    .
                    .
         dbms_aw.advise_sparsity('units_history_fact', 'units_cube', dimsources,
              dbms_aw.advice_default);

    END;
    /

The following `SELECT` command displays the results of the analysis, which indicate that there is one denser dimension (`CHANNEL`) and three comparatively sparse dimensions (`PRODUCT`, `CUSTOMER`, and `TIME`).

    SELECT fact, dimension, dimcolumn, membercount nmem, leafcount nleaf, advice, density
         FROM aw_sparsity_advice
         WHERE cubename='units_cube';

    FACT                 DIMENSION    DIMCOLUMN     NMEM  NLEAF ADVICE          DENSITY
    -------------------- ------------ ------------ ----- ------ ------------ ----------
    units_history_fact   channel      channel_id       3      3 DENSE         .86545382
    units_history_fact   product      item_id         36     36 SPARSE        .98706809
    units_history_fact   customer     ship_to_id      61     62 SPARSE        .99257713
    units_history_fact   time         month_id        96     80 SPARSE        .99415964

### B.14 AW_ATTACH Procedure

The `AW_ATTACH` procedure attaches an analytic workspace to your SQL session so that you can access its contents. The analytic workspace remains attached until you explicitly detach it, or you end your session.

`AW_ATTACH` can also be used to create an analytic workspace, but the `AW_CREATE` procedure is provided specifically for that purpose.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Managing Analytic Workspaces"

#### Syntax

    AW_ATTACH (
              awname        IN VARCHAR2,
              forwrite      IN BOOLEAN DEFAULT FALSE,
              createaw      IN BOOLEAN DEFAULT FALSE,
              attargs       IN VARCHAR2 DEFAULT NULL,
              tablespace    IN VARCHAR2 DEFAULT NULL);

    AW_ATTACH (
              schema        IN VARCHAR2,
              awname        IN VARCHAR2,
              forwrite      IN BOOLEAN DEFAULT FALSE,
              createaw      IN BOOLEAN DEFAULT FALSE,
              attargs       IN VARCHAR2 DEFAULT NULL,
              tablespace    IN VARCHAR2 DEFAULT NULL);

#### Parameters

Table B-11 AW_ATTACH Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                 |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema`   | The schema that owns awname.                                                                                                                                                                                |
| `awname`   | The name of an existing analytic workspace, unless createaw is specified as `TRUE`. See the description of createaw.                                                                                        |
| `forwrite` | `TRUE` attaches the analytic workspace in read/write mode, giving you exclusive access and full administrative rights to the analytic workspace. `FALSE` attaches the analytic workspace in read-only mode. |
| `createaw` | `TRUE` creates an analytic workspace named awname. If awname already exists, then an error is generated. `FALSE` attaches an existing analytic workspace named awname.                                      |
| `attargs`  | Keywords for attaching an analytic workspace, such as `FIRST` or `LAST`, as described in [AW command](olap-dml-commands-a-g.md).                                                                            |

#### Example

The following commands create an analytic workspace named `GLOBAL_TRACKING` and copies the contents of `GLOBAL` into it. The workspace is stored in a table named `AW$GLOBAL_TRACKING`, which has three partitions and is stored in the user's default tablespace.

    EXECUTE dbms_aw.aw_attach('global');
    EXECUTE dbms_aw.aw_copy('global', 'global_tracking', NULL, 3);

### B.15 AW_COPY Procedure

The `AW_COPY` procedure copies the object definitions and data from one analytic workspace into a new analytic workspace.

`AW_COPY` detaches the original workspace and attaches the new workspace first with read/write access.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Managing Analytic Workspaces"

#### Syntax

    AW_COPY (
              oldname         IN VARCHAR2,
              newname         IN VARCHAR2,
              tablespace      IN VARCHAR2 DEFAULT NULL,
              partnum         IN NUMBER DEFAULT 8);

#### Parameters

Table B-12 AW_COPY Procedure Parameters

| Parameter    | Description                                                                                                                                                 |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `oldname`    | The name of an existing analytic workspace that contains object definitions. The workspace cannot be empty.                                                 |
| `newname`    | A name for the new analytic workspace that is a copy of oldname.                                                                                            |
| `tablespace` | The name of a tablespace in which newname is stored. If this parameter is omitted, then the analytic workspace is created in the user's default tablespace. |
| `partnum`    | The number of partitions that are created for the `AW$`newname table.                                                                                       |

#### Example

The following commands create an analytic workspace named `GLOBAL_TRACKING` and copies the contents of `GLOBAL` into it. The workspace is stored in a table named `AW$GLOBAL_TRACKING`, which has three partitions and is stored in the user's default tablespace.

    EXECUTE dbms_aw.aw_attach('global');
    EXECUTE dbms_aw.aw_copy('global', 'global_tracking', NULL, 3);

### B.16 AW_CREATE Procedure

The `AW_CREATE` procedure creates a new, empty analytic workspace and makes it the current workspace in your session.

The current workspace is first in the list of attached workspaces.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    AW_CREATE (
               awname        IN VARCHAR2 ,
               tablespace    IN VARCHAR2 DEFAULT NULL ,
               partnum       IN NUMBER DEFAULT 8 );

    AW_CREATE (
               schema        IN VARCHAR2 ,
               awname        IN VARCHAR2 ,
               tablespace    IN VARCHAR2 DEFAULT NULL);

#### Parameters

Table B-13 AW_CREATE Procedure Parameters

| Parameter    | Description                                                                                                                                                                                                         |
|:-------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema`     | The schema that owns awname.                                                                                                                                                                                        |
| `awname`     | The name of a new analytic workspace. The name must comply with the naming requirements for a table in Oracle Database. This procedure creates a table named AW\$awname, in which the analytic workspace is stored. |
| `tablespace` | The tablespace in which the analytic workspace is created. If you omit this parameter, the analytic workspace is created in your default tablespace.                                                                |
| `partnum`    | The number of partitions that are created for the `AW$`awname table.                                                                                                                                                |

#### Example

The following command creates a new, empty analytic workspace named `GLOBAL_FINANCE`. The new analytic workspace is stored in a table named `AW$GLOBAL_FINANCE` with eight partitions in the user's default tablespace.

    EXECUTE dbms_aw.aw_create('global_finance');

The next command creates an analytic workspace named `DEMO` in the `GLOBAL` schema. `AW$DEMO` has two partitions and is stored in the `GLOBAL` tablespace.

    EXECUTE dbms_aw.aw_create('global.demo', 'global', 2);

### B.17 AW_DELETE Procedure

The `AW_DELETE` procedure deletes an existing analytic workspace.

#### Syntax

    AW_DELETE (
        awname        IN VARCHAR2);

    AW_DELETE (
        schema        IN VARCHAR2,
        awname        IN VARCHAR2);

#### Parameters

Table B-14 AW_DELETE Procedure Parameters

| Parameter | Description                                                                                                                                                                                                                                                                |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema`  | The schema that owns awname.                                                                                                                                                                                                                                               |
| `awname`  | The name of an existing analytic workspace that you want to delete along with all of its contents. You must be the owner of awname or have DBA rights to delete it, and it cannot currently be attached to your session. The AW\$awname file is deleted from the database. |

#### Example

The following command deletes the `SALES_DEMO` analytic workspace in the user's default schema.

    EXECUTE dbms_aw.aw_delete('sales_demo');

### B.18 AW_DETACH Procedure

The `AW_DETACH` procedure detaches an analytic workspace from your session so that its contents are no longer accessible. All changes that you have made since the last update are discarded. Refer to "AW_UPDATE Procedure" for information about saving changes to an analytic workspace.

#### Syntax

    AW_DETACH (
              awname        IN VARCHAR2);

    AW_DETACH (
              schema        IN VARCHAR2,
              awname        IN VARCHAR2);

#### Parameters

Table B-15 AW_DETACH Procedure Parameters

| Parameter | Description                                                                           |
|:----------|:--------------------------------------------------------------------------------------|
| `schema`  | The schema that owns awname.                                                          |
| `awname`  | The name of an attached analytic workspace that you want to detach from your session. |

#### Example

The following command detaches the `GLOBAL_FINANCE` analytic workspace.

    EXECUTE dbms_aw.aw_detach('global_finance');

The next command detaches the `SALES_HISTORY` analytic workspace in the `SH_AW` schema.

    EXECUTE dbms_aw.aw_detach('sh_aw', 'sales_history');

### B.19 AW_RENAME Procedure

The `AW_RENAME` procedure changes the name of an analytic workspace.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    AW_RENAME (
              oldname       IN VARCHAR2,
              newname       IN VARCHAR2 );

#### Parameters

Table B-16 AW_RENAME Procedure Parameters

| Parameter | Description                                                                                           |
|:----------|:------------------------------------------------------------------------------------------------------|
| `oldname` | The current name of the analytic workspace. The analytic workspace cannot be attached to any session. |
| `newname` | The new name of the analytic workspace.                                                               |

#### Example

The following commands detach the `DEMO` analytic workspace and change its name to `SALES_DEMO`.

    EXECUTE dbms_aw.aw_detach('demo');
    EXECUTE dbms_aw.aw_rename('demo', 'sales_demo');

### B.20 AW_TABLESPACE Function

The `AW_TABLESPACE` function returns the name of the tablespace in which a particular analytic workspace is stored.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    AW_TABLESPACE (
              awname        IN VARCHAR2)
         RETURN VARCHAR2;

    AW_TABLESPACE (
              schema        IN VARCHAR2,
              awname        IN VARCHAR2)
         RETURN VARCHAR2;

#### Returns

Name of a tablespace.

#### Parameters

Table B-17 AW_TABLESPACE Function Parameters

| Parameter | Description                        |
|:----------|:-----------------------------------|
| `schema`  | The schema that owns awname.       |
| `awname`  | The name of an analytic workspace. |

#### Example

The following example shows the tablespace in which the `GLOBAL` analytic workspace is stored.

    SET serveroutput ON

    EXECUTE dbms_output.put_line('Sales History is stored in tablespace ' ||
         dbms_aw.aw_tablespace('sh_aw', 'sales_history'));

This command generates the following statement:

    Sales History is stored in tablespace SH_AW

### B.21 AW_UPDATE Procedure

The `AW_UPDATE` procedure saves the changes made to an analytic workspace in its permanent database table. For the updated version of this table to be saved in the database, you must issue a SQL `COMMIT` statement before ending your session.

If you do not specify an analytic workspace to update, `AW_UPDATE` updates all the user-defined workspaces that are currently attached with read/write access.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Managing Analytic Workspaces"

#### Syntax

    AW_UPDATE (
              awname     IN VARCHAR2 DEFAULT NULL);

    AW_UPDATE (
              schema     IN VARCHAR2 DEFAULT NULL,
              awname     IN VARCHAR2 DEFAULT NULL);

#### Parameters

Table B-18 AW_UPDATE Procedure Parameters

| Parameter | Description                                                                                                                                                                         |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema`  | The schema that owns awname.                                                                                                                                                        |
| `awname`  | Saves changes to awname by copying them to a table named `AW$`awname. If this parameter is omitted, then changes are saved for all analytic workspaces attached in read/write mode. |

#### Example

The following commands save changes to the `GLOBAL` analytic workspace from the temporary to the permanent tablespace, then commit the change to the database.

    EXECUTE dbms_aw.aw_update('global');
    COMMIT;

### B.22 CONVERT Procedure

The `CONVERT` procedure converts an analytic workspace in 9i storage format to to 10g storage format. Note that you cannot execute this procedure from within the OLAP Worksheet; you must execute it in a SQL tool such as SQL\*Plus.

**Note:**

Issuing the `dbms_aw.convert` procedure is only one small step in upgrading Oracle 9i analytic workspaces to Oracle 10g workspaces. For the complete procedure for upgrading Oracle 9i analytic workspaces, see Oracle OLAP Application Developer's Guide, 10g Release 2 (10.2).

**See Also:**

[Upgrading Metadata from Oracle OLAP 10g](../olaug/getting-started-oracle-olap.md) in Oracle OLAP User’s Guide for information on converting an analytic workspace to Oracle 11g storage format

#### Syntax

    CONVERT (
              original_aw      IN VARCHAR2);

    CONVERT (
              original_aw      IN VARCHAR2,
              converted_aw     IN VARCHAR2,
              tablespace       IN NUMBER DEFAULT);

#### Parameters

Table B-19 CONVERT Procedure Parameters

| Parameter      | Description                                                                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `original_aw`  | The analytic workspace you want to convert.                                                                                                                                 |
| `converted_aw` | The converted analytic workspace.                                                                                                                                           |
| `tablespace`   | The name of a tablespace in which the converted workspace is stored. If this parameter is omitted, then the analytic workspace is created in the user's default tablespace. |

#### Example

This example performs the conversion in a single step, using the analytic workspace as both the source and the target of the conversion.

    EXECUTE dbms_aw.convert('global');

The next example performs the conversion in several steps. The converted workspace must have the same name as the original workspace, because the fully qualified names of objects in the workspace include the workspace name.

    EXECUTE dbms_aw.rename('global', 'global_temp');
    EXECUTE dbms_aw.convert('global_temp', 'global');
    EXECUTE dbms_aw.delete('global_temp');

### B.23 EVAL_NUMBER Function

The `EVAL_NUMBER` function evaluates a numeric expression in an analytic workspace and returns the resulting number.

You can specify the `EVAL_NUMBER` function in a `SELECT` from `DUAL` statement to return a numeric constant defined in an analytic workspace. For more information, see ["Selecting from the DUAL Table"](../sqlrf/Selecting-from-the-DUAL-Table.md) in Oracle Database SQL Language Reference.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    EVAL_NUMBER (
              olap_numeric_expression     IN    VARCHAR2)
         RETURN NUMBER;

#### Parameters

Table B-20 EVAL_NUMBER Function Parameters

| Parameter                 | Description                                                                                                                  |
|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------|
| `olap_numeric_expression` | An OLAP DML expression that evaluates to a number. Refer to [OLAP DML Expressions](data-types-operators-and-expressions.md). |

#### Example

The following example returns the value of the `DECIMALS` option in the current analytic workspace. The `DECIMALS` option controls the number of decimal places that are shown in numeric output. In this example, the value of `DECIMALS` is 2, which is the default.

    SET serveroutput ON
    SELECT dbms_aw.eval_number('decimals') "Decimals" FROM dual;

      Decimals
    ----------
             2

### B.24 EVAL_TEXT Function

The `EVAL_TEXT` function evaluates a text expression in an analytic workspace and returns the resulting character string.

You can specify the `EVAL_TEXT` function in a `SELECT` from `DUAL` statement to return a character constant defined in an analytic workspace. For more information, see ["Selecting from the DUAL Table"](../sqlrf/Selecting-from-the-DUAL-Table.md) in Oracle Database SQL Language Reference.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    EVAL_TEXT (
              olap_text_expression     IN    VARCHAR2)
        RETURN VARCHAR2;

#### Parameters

Table B-21 EVAL_TEXT Function Parameters

| Parameter              | Description                                                                                                                            |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `olap_text_expression` | An OLAP DML expression that evaluates to a character string. Refer to [OLAP DML Expressions](data-types-operators-and-expressions.md). |

#### Example

The following example returns the value of the `NLS_LANGUAGE` option, which specifies the current language of the session.

    SET serveroutput ON
    SELECT dbms_aw.eval_text('nls_language') "NLS Language" FROM dual;


The value of `NLS_LANGUAGE` in this example is `AMERICAN`.

    NLS Language
    ---------------
    AMERICAN

### B.25 EXECUTE Procedure

The `EXECUTE` procedure executes one or more OLAP DML commands and directs the output to a printer buffer. It is typically used to manipulate analytic workspace data within an interactive SQL session. In contrast to the RUN Procedure, `EXECUTE` continues to process commands after it gets an error.

When you are using SQL\*Plus, you can direct the printer buffer to the screen by issuing the following command:

    SET SERVEROUT ON

If you are using a different program, refer to its documentation for the equivalent setting.

Input and output is limited to 4K. For larger values, refer to the `INTERP` and `INTERPCLOB` functions in this package.

This procedure does not print the output of the DML commands when you have redirected the output by using the OLAP DML `OUTFILE` command.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    EXECUTE (
              olap_commands     IN    VARCHAR2
              text              OUT   VARCHAR2);

#### Parameters

Table B-22 EXECUTE Procedure Parameters

| Parameter       | Description                                                                                                             |
|:----------------|:------------------------------------------------------------------------------------------------------------------------|
| `olap-commands` | One or more OLAP DML commands separated by semicolons. See "Guidelines for Using Quotation Marks in OLAP DML Commands". |
| `text`          | Output from the OLAP engine in response to the OLAP commands.                                                           |

#### Example

The following example attaches the `GLOBAL` analytic workspace and shows the object definition of `TIME`.

    EXECUTE dbms_aw.aw_attach('global');
    EXECUTE dbms_aw.execute('DESCRIBE time');

    DEFINE TIME DIMENSION TEXT

The next example shows how `EXECUTE` continues to process commands after encountering an error:

    EXECUTE dbms_aw.execute('SHOW DECIMALS');
    2

    EXECUTE dbms_aw.execute('CALL nothing; DECIMALS=0');
    BEGIN dbms_aw.execute('CALL nothing; DECIMALS=0'); END;

    *
    ERROR at line 1:
    ORA-34492: Analytic workspace object NOTHING does not exist.
    ORA-06512: at "SYS.DBMS_AW", line 93
    ORA-06512: at "SYS.DBMS_AW", line 122
    ORA-06512: at line 1

    EXECUTE dbms_aw.execute('SHOW DECIMALS');
    0

The next example show how `EXECUTE` continues to process commands after encountering an error:

    SQL> execute dbms_aw.execute('call nothing; colwidth=20');
    BEGIN dbms_aw.execute('call nothing; colwidth=20'); END;

    *
    ERROR at line 1:
    ORA-34492: Analytic workspace object NOTHING does not exist.
    ORA-06512: at "SYS.DBMS_AW", line 90
    ORA-06512: at "SYS.DBMS_AW", line 119
    ORA-06512: at line 1


    SQL> execute dbms_aw.execute('show colwidth');
    20

    PL/SQL procedure successfully completed.

### B.26 GETLOG Function

This function returns the session log from the last execution of the `INTERP` or `INTERPCLOB` functions in this package.

To print the session log returned by this function, use the `DBMS_AW.PRINTLOG` procedure.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    GETLOG()
              RETURN CLOB;

#### Returns

The session log from the latest call to `INTERP` or `INTERPCLOB`.

#### Example

The following example shows the session log returned by a call to `INTERP`, then shows the identical session log returned by `GETLOG`.

    EXECUTE dbms_aw.printlog(dbms_aw.interp('AW ATTACH global; REPORT units_cube'));

    UNITS_CUBE
    --------------
    TIME
    CUSTOMER
    PRODUCT
    CHANNEL

    EXECUTE dbms_aw.printlog(dbms_aw.getlog());

    UNITS_CUBE
    --------------
    TIME
    CUSTOMER
    PRODUCT
    CHANNEL

### B.27 INFILE Procedure

The `INFILE` procedure evaluates the OLAP DML commands in the specified file and executes them in the current analytic workspace.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    INFILE (
              filename     IN   VARCHAR2);

#### Parameters

Table B-23 INFILE Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                               |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `filename` | The name of a file containing OLAP DML commands.<br>The file path must be specified in a current directory object for your OLAP session. Use the OLAP DML CDA command to identify or change the current directory object. |

#### Example

The following example executes the OLAP DML commands in the `finances.inf` file. The location of the file is identified by the `WORK_DIR` database directory.

    EXECUTE dbms_aw.infile('work_dir/finances.inf');

### B.28 INTERP Function

The `INTERP` function executes one or more OLAP DML commands and returns the session log in which the commands are executed. It is typically used in applications when the 4K limit on output for the `EXECUTE` procedure may be too restrictive.

Input to the `INTERP` function is limited to 4K. For larger input values, refer to the `INTERPCLOB` function of this package.

This function does not return the output of the DML commands when you have redirected the output by using the OLAP DML `OUTFILE` command.

You can use the `INTERP` function as an argument to the `PRINTLOG` procedure in this package to view the session log. See the example.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    INTERP (
              olap-commands     IN   VARCHAR2)
         RETURN CLOB;

#### Parameters

Table B-24 INTERP Function Parameters

| Parameter       | Description                                                                                                              |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------|
| `olap-commands` | One or more OLAP DML commands separated by semi-colons. See "Guidelines for Using Quotation Marks in OLAP DML Commands". |

#### Returns

The log file for the Oracle OLAP session in which the OLAP DML commands were executed.

#### Example

The following sample SQL\*Plus session attaches the `GLOBAL` analytic workspace and lists the members of `UNITS_CUBE`.

    SET serverout ON
    EXECUTE dbms_aw.printlog(dbms_aw.interp('AW ATTACH global; REPORT units_cube'));

    UNITS_CUBE
    --------------
    TIME
    CUSTOMER
    PRODUCT
    CHANNEL

### B.29 INTERPCLOB Function

The `INTERPCLOB` function executes one or more OLAP DML commands and returns the session log in which the commands are executed. It is typically used in applications when the 4K limit on input for the `INTERP` function may be too restrictive.

This function does not return the output of the OLAP DML commands when you have redirected the output by using the OLAP DML `OUTFILE` command.

You can use the `INTERPCLOB` function as an argument to the `PRINTLOG` procedure in this package to view the session log. See the example.

#### Syntax

    INTERPCLOB (
              olap-commands     IN   CLOB)
         RETURN CLOB;

#### Parameters

Table B-25 INTERPCLOB Function Parameters

| Parameter       | Description                                                                                                              |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------|
| `olap-commands` | One or more OLAP DML commands separated by semi-colons. See "Guidelines for Using Quotation Marks in OLAP DML Commands". |

#### Returns

The log for the Oracle OLAP session in which the OLAP DML commands were executed.

#### Example

The following sample SQL\*Plus session creates an analytic workspace named `ELECTRONICS`, imports its contents from an EIF file stored in the `dbs` directory object, and displays the contents of the analytic workspace.

    SET serverout ON size 1000000
    EXECUTE dbms_aw.printlog(dbms_aw.interpclob('AW ATTACH global; DESCRIBE'));

    DEFINE GEN_OBJ_ROLES DIMENSION TEXT

    DEFINE GEN_AW_OBJS VARIABLE TEXT <GEN_OBJ_ROLES>

    DEFINE ALL_DIMENSIONS DIMENSION TEXT

    DEFINE DIM_OBJ_LIST DIMENSION TEXT

    DEFINE DIM_AW_OBJS VARIABLE TEXT <ALL_DIMENSIONS DIM_OBJ_LIST>
         .
         .
         .

### B.30 INTERP_SILENT Procedure

The `INTERP_SILENT` procedure executes one or more OLAP DML commands and suppresses all output from them. It does not suppress error messages from the OLAP command interpreter.

Input to the `INTERP_SILENT` function is limited to 4K. To display the output of the OLAP DML commands, use the `EXECUTE` procedure, or the `INTERP` or `INTERPCLOB` functions.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    INTERP_SILENT (
              olap-commands     IN   VARCHAR2);

#### Parameters

Table B-26 INTERP_SILENT Function Parameters

| Parameter       | Description                                                                                                              |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------|
| `olap-commands` | One or more OLAP DML commands separated by semi-colons. See "Guidelines for Using Quotation Marks in OLAP DML Commands". |

#### Example

The following commands show the difference in message handling between `EXECUTE` and `INTERP_SILENT`. Both commands attach the `GLOBAL` analytic workspace in read-only mode. However, `EXECUTE` displays a warning message, while `INTERP_SILENT` does not.

    EXECUTE dbms_aw.execute('AW ATTACH global');
    IMPORTANT: Analytic workspace GLOBAL is read-only. Therefore, you will not be able to use the UPDATE command to save changes to it.

    EXECUTE dbms_aw.interp_silent('AW ATTACH global');

### B.31 OLAP_ON Function

The `OLAP_ON` function returns a boolean indicating whether or not the OLAP option is installed in the database.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    OLAP_ON ( )
        RETURN BOOLEAN;

#### Returns

The value of the `OLAP` parameter in the `V$OPTION` table.

#### Example

The following PL/SQL code tests the value returned by `OLAP_ON` and returns a status message.

    BEGIN
          IF dbms_aw.olap_on() = true
             THEN dbms_output.put_line('The OLAP option is installed');
          ELSE dbms_output.put_line('The OLAP option is not installed');
          END IF;
    END;
    /

    The OLAP option is installed

### B.32 OLAP_RUNNING Function

The `OLAP_RUNNING` function returns a boolean indicating whether or not the OLAP option has been initialized in the current session. Initialization occurs when you execute an OLAP DML command (either directly or by using an OLAP PL/SQL or Java package), query an analytic workspace, or execute the STARTUP Procedure.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    OLAP_RUNNING( )
        RETURN BOOLEAN;

#### Returns

`TRUE` if OLAP has been initialized in the current session, or `FALSE` if it has not.

#### Example

The following PL/SQL script tests whether the OLAP environment has been initialized, and starts it if not.

    BEGIN
         IF dbms_aw.olap_running() THEN
              dbms_output.put_line('OLAP is already running');
         ELSE
              dbms_aw.startup;
         IF dbms_aw.olap_running() THEN
              dbms_output.put_line('OLAP started successfully');
         ELSE
              dbms_output.put_line('OLAP did not start. Is it installed?');
         END IF;
     END IF;
    END;
    /

    OLAP started successfully

### B.33 PRINTLOG Procedure

This procedure sends a session log returned by the `INTERP`, `INTERPCLOB`, or `GETLOG` functions of this package to the print buffer, using the `DBMS_OUTPUT` package in PL/SQL.

When you are using SQL\*Plus, you can direct the printer buffer to the screen by issuing the following command:

    SET SERVEROUT ON SIZE 1000000

The `SIZE` clause increases the buffer from its default size of 4K.

If you are using a different program, refer to its documentation for the equivalent setting.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    PRINTLOG (
              session-log     IN   CLOB);

#### Parameters

Table B-27 PRINTLOG Procedure Parameters

| Parameter   | Description           |
|:------------|:----------------------|
| session-log | The log of a session. |

#### Example

The following example shows the session log returned by the `INTERP` function.

    SET serverout ON size 1000000

    EXECUTE dbms_aw.printlog(dbms_aw.interp('REPORT W 30 all_dimensions'));

    ALL_DIMENSIONS
    ------------------------------
    TIME.DIMENSION
    CUSTOMER.DIMENSION
    PRODUCT.DIMENSION
    CHANNEL.DIMENSION

### B.34 RUN Procedure

The `RUN` procedure executes one or more OLAP DML commands and directs the output to a printer buffer. It is typically used to manipulate analytic workspace data within an interactive SQL session. In contrast to the EXECUTE Procedure, `RUN` stops processing commands when it gets an error.

When you are using SQL\*Plus, you can direct the printer buffer to the screen by issuing the following command:

    SET SERVEROUT ON

If you are using a different program, refer to its documentation for the equivalent setting.

This procedure does not print the output of the DML commands when you have redirected the output by using the OLAP DML `OUTFILE` command.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    RUN (
              olap_commands     IN      STRING,
              silent            IN      BOOLEAN DEFAULT FALSE);
    RUN (
              olap_commands     IN      CLOB,
              silent            IN      BOOLEAN DEFAULT FALSE);
    RUN (
              olap_commands     IN      STRING,
              output            OUT     STRING);
    RUN (
              olap_commands     IN      STRING,
              output            IN OUT  CLOB);
    RUN (
              olap_commands     IN      CLOB,
              output            OUT     STRING);
    RUN (
              olap_commands     IN      CLOB,
              output            IN OUT  CLOB);

#### Parameters

Table B-28 EXECUTE Procedure Parameters

| Parameter       | Description                                                                                                                                                                              |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `olap-commands` | One or more OLAP DML commands separated by semicolons. See "Guidelines for Using Quotation Marks in OLAP DML Commands".                                                                  |
| `silent`        | A boolean value that signals whether the output from the OLAP DML commands should be suppressed. (Error messages from the OLAP engine are never suppressed, regardless of this setting.) |
| `output`        | Output from the OLAP engine in response to the OLAP commands.                                                                                                                            |

#### Example

The following sample SQL\*Plus session attaches an analytic workspace named `XADEMO`, creates a formula named `COST_PP` in `XADEMO`, and displays the new formula definition.

    EXECUTE dbms_aw.run('DESCRIBE time');

    DEFINE TIME DIMENSION TEXT

The next example shows how `RUN` stops executing commands after encountering an error.

    EXECUTE dbms_aw.run('SHOW DECIMALS');
    0

    EXECUTE dbms_aw.run('CALL nothing; DECIMALS=4');
    BEGIN dbms_aw.run('CALL nothing; DECIMALS=4'); END;

    *
    ERROR at line 1:
    ORA-34492: Analytic workspace object NOTHING does not exist.
    ORA-06512: at "SYS.DBMS_AW", line 58
    ORA-06512: at "SYS.DBMS_AW", line 134
    ORA-06512: at line 1

    EXECUTE dbms_aw.run('SHOW DECIMALS');
    0

### B.35 SHUTDOWN Procedure

The `SHUTDOWN` procedure terminates the current OLAP session.

By default, the `SHUTDOWN` procedure terminates the session only if there are no outstanding changes to any of the attached read/write workspaces. To terminate the session without updating the workspaces, specify the `force` parameter.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    SHUTDOWN (
              force     IN    BOOLEAN  DEFAULT NO);

#### Parameters

Table B-29 SHUTDOWN Procedure Parameters

| Parameter | Description                                                                                                                                       |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `force`   | When `YES`, this parameter forces the OLAP session to shutdown even though one or more attached workspaces has not been updated. Default is `NO`. |

#### Example

The following commands save all changes to the `GLOBAL` analytic workspace and close the user's OLAP session.

    EXECUTE dbms_aw.aw_update('global_finance');
    COMMIT;
    EXECUTE dbms_aw.shutdown();

### B.36 SPARSITY_ADVICE_TABLE Procedure

The `SPARSITY_ADVICE_TABLE` procedure creates a table for storing the advice generated by the `ADVISE_SPARSITY` procedure.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

**See Also:**

"Using the Sparsity Advisor"

#### Syntax

    SPARSITY_ADVICE_TABLE (
              tblname   IN    VARCHAR2 DEFAULT);

#### Parameters

Table B-30 SPARSITY_ADVICE_TABLE Procedure Parameters

| Parameter | Description                                                                                                                                                                      |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tblname` | The name of the table. The default name is `AW_SPARSITY_ADVICE`, which is created in your own schema. See ADVISE_SPARSITY Procedure for a description of the columns in tblname. |

#### Example

The following example creates a table named `GLOBAL_SPARSITY_ADVICE`.

    EXECUTE dbms_aw.sparsity_advice_table('global_sparsity_advice');

### B.37 STARTUP Procedure

The `STARTUP` procedure starts an OLAP session without attaching any user-defined workspaces.

`STARTUP` initializes the OLAP processing environment and attaches the read-only `EXPRESS` workspace, which contains the program code for the OLAP engine.

**Note:**

You cannot execute this procedure from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL\*Plus.

#### Syntax

    STARTUP ( );

#### Example

The following example starts an OLAP session.

    EXECUTE dbms_aw.startup();
