This appendix contains reference documentation for the following SQL functions that you can use to extract multidimensional data from an analytic workspace and present it in the two-dimensional format of a relational table:

- Creating Relational Views Using OLAP_TABLE

- Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements

- OLAP_TABLE

- OLAP_CONDITION

- OLAP_EXPRESSION

- OLAP_EXPRESSION_BOOL

- OLAP_EXPRESSION_DATE

- OLAP_EXPRESSION_TEXT

### A.1 Creating Relational Views Using OLAP_TABLE

`OLAP_TABLE` is a SQL function that returns a table of objects that can be joined to relational tables and views, and to other tables of objects populated by `OLAP_TABLE`. Within a SQL statement, you can specify an `OLAP_TABLE` function call wherever you would provide the name of a table or view.

`OLAP_TABLE` uses a limit map to map dimensions and measures defined in an analytic workspace to columns in a logical table. The limit map combines with the `WHERE` clause of a SQL `SELECT` statement to generate a series of OLAP DML LIMIT commands that are executed in the analytic workspace.

`OLAP_TABLE` can use a limit map with a predefined logical table, or it can use the information in a limit map to dynamically generate a logical table at run time.

**See Also:**

- [LIMIT command](olap-dml-commands-h-z.md)

- The discussion of the "limit_map" parameter of OLAP_TABLE

- "Creating Logical Tables for Use by OLAP_TABLE"

- "Required OLAP DML Objects"

- "Creating Logical Tables for Use by OLAP_TABLE"

- "Creating Logical Tables for Use by OLAP_TABLE"

- "Creating Logical Tables for Use by OLAP_TABLE"

#### A.1.1 Required OLAP DML Objects

Several objects must be predefined within the analytic workspace to support the mapping of dimension hierarchies in the limit map:

- a parent relation, which identifies the parent of each dimension member within a hierarchy. See "[Parentrel Relation](olap-dml-basic-concepts.md)" for more information.

- a hierarchy dimension, which lists the hierarchies of a dimension. See "[Hierlist Dimension](olap-dml-basic-concepts.md)" for more information.

- an inhierarchy variable or valueset, which specifies which dimension members belong to each level of a hierarchy. See "[Inhier Valueset or Variable](olap-dml-basic-concepts.md)" for more information.

- a grouping ID variable, which identifies the depth within a hierarchy of each dimension member. See "[Gidrel Relation](olap-dml-basic-concepts.md)" for more information.

- a family relation, which provides the full parentage of each dimension member in a hierarchy. See "[Familyrel Relation](olap-dml-basic-concepts.md)" for more information.

- a level dimension, which lists the levels of a dimension. See "[Levellist Dimension](olap-dml-basic-concepts.md)" for more information.

#### A.1.2 Creating Logical Tables for Use by OLAP_TABLE

The logical table populated by `OLAP_TABLE` is actually a table type whose rows are user-defined object types, also known as Abstract Data Types or ADTs.

A user-defined object type is composed of attributes, which are equivalent to the columns of a table. The basic syntax for defining a row is as follows.

    CREATE TYPE object_name AS OBJECT (
       attribute1      datatype,
       attribute2      datatype,
       attributen      datatype);

A table type is a collection of object types; this collection is equivalent to the rows of a table. The basic syntax for creating a table type is as follows.

    CREATE TYPE table_name AS TABLE OF object_name;

`OLAP_TABLE` can use a limit map with a predefined logical table, or it can use the information in a limit map to dynamically generate a logical table at run time.

**See Also:**

- "Using OLAP_TABLE With Predefined ADTs"

- "Using OLAP_TABLE With Automatic ADTs"

- [About Object Types](../adobj/key-features-object-relational-model.md) in Oracle Database Object-Relational Developer's Guide for information about object types

- [CREATE TYPE](../sqlrf/CREATE-TYPE.md) in Oracle Database SQL Language Reference

##### A.1.2.1 Using OLAP_TABLE With Predefined ADTs

You can predefine the table of objects or generate it dynamically. When you create the table type in advance, it is available in the database for use by any invocation of `OLAP_TABLE`. Queries that use predefined objects typically perform better than queries that dynamically generate the objects.

##### Examples

Example A-1 Template for Creating a View Using Predefined ADTs

This example shows how to create a view of an analytic workspace using predefined ADTs.

    SET ECHO ON
    SET SERVEROUT ON

    DROP TYPE table_obj;
    DROP TYPE row_obj;

    CREATE TYPE row_obj AS OBJECT (
                column_first     datatype,
                column_next      datatype,
                column_n         datatype);
    /
    CREATE TYPE table_obj AS TABLE OF row_obj;
    /
    CREATE OR REPLACE VIEW view_name AS
       SELECT column_first, column_next, column_n
          FROM TABLE(OLAP_TABLE(
             'analytic_workspace',
             'table_obj',
             'olap_command',
             'limit_map'));
    /
    COMMIT;
    /
    GRANT SELECT ON view_name TO PUBLIC;

Example A-2 Sample View of the TIME Dimension Using Predefined ADTs

This example uses `OLAP_TABLE` with a predefined table type to create a relational view of the `TIME` dimension in an analytic workspace named `MYAW` in the `MYAW_AW` schema.

The first parameter in the `OLAP_TABLE` call is the name of the analytic workspace. The second is the name of the predefined table type. The fourth is the limit map that specifies how to map the workspace dimension to the columns of the predefined table type. The third parameter is not specified.

    CREATE TYPE time_cal_row AS OBJECT (
                time_id           varchar2(32),
                cal_short_label   varchar2(32),
                cal_end_date      date,
                cal_timespan      number(6));

    CREATE TYPE time_cal_table AS TABLE OF time_cal_row;

    CREATE OR REPLACE VIEW time_cal_view AS
       SELECT time_id, cal_short_label, cal_end_date, cal_timespan
          FROM TABLE(OLAP_TABLE(
             'myaw_aw.myaw duration session',
             'time_cal_table',
              '',
             'DIMENSION time_id from time with
                HIERARCHY time_parentrel
                   INHIERARCHY time_inhier
                ATTRIBUTE cal_short_label from time_short_description
                ATTRIBUTE cal_end_date    from time_end_date
                ATTRIBUTE cal_timespan    from time_time_span'));

##### A.1.2.2 Using OLAP_TABLE With Automatic ADTs

If you do not supply the name of a table type as an argument, `OLAP_TABLE` uses information in the limit map to generate the logical table automatically. In this case, the table type is only available at run time within the context of the calling SQL `SELECT` statement.

##### Examples

Example A-3 Template for Creating a View Using Automatic ADTs

This example shows how to create a view of an analytic workspace using automatic ADTs.

    SET ECHO ON
    SET SERVEROUT ON

    CREATE OR REPLACE VIEW view_name AS
       SELECT column_first, column_next, column_n
          FROM TABLE(OLAP_TABLE(
             'analytic_workspace',
             '',
             'olap_command',
             'limit_map'));
    /
    COMMIT;
    /
    GRANT SELECT ON view_name TO PUBLIC;

Example A-4 View of the TIME Dimension Using Automatic ADTs

This example creates the same view produced by the previous example, but it automatically generates the ADTs instead of using a predefined table type. It uses `AS` clauses in the limit map to specify the data types of the target columns.

    CREATE OR REPLACE VIEW time_cal_view AS
       SELECT time_id, cal_short_label, cal_end_date, cal_timespan
          FROM TABLE(OLAP_TABLE(
            'myaw_aw.myaw duration session',
            null,
            null,
            'DIMENSION time_id AS varchar2(32) FROM time WITH
               HIERARCHY time_parentrel
                  INHIERARCHY time_inhier
               ATTRIBUTE cal_short_label AS VARCHAR2(32) from time_short_description
               ATTRIBUTE cal_end_date AS DATE            from time_end_date
               ATTRIBUTE cal_timespan AS NUMBER(6)       from time_time_span'));

When automatically generating ADTs, `OLAP_TABLE` uses default relational data types for the target columns unless you override them with `AS` clauses in the limit map. The default data type conversions used by `OLAP_TABLE` are described in Table A-2.

#### A.1.3 Adding Calculated Columns to the Relational View

`OLAP_TABLE` uses a limit map to present the multidimensional data from an analytic workspace in tabular form. The limit map specifies the columns of the logical table. You can add a calculated column to your relational view by specifying the `OLAP_EXPRESSION` function or a related Boolean, text, or date function in the select list of the query. When you specify one of these functions in the select list, `OLAP_TABLE` generates additional columns for the results of the function.

Before you use one of these expressions, you must specify a `ROW2CELL` clause in the limit map used by `OLAP_TABLE` to identifies the `RAW` column that `OLAP_TABLE` populates with information used by the OLAP single-row functions.

**See Also:**

"Using OLAP DML Expressions as Single-Row Functions" and "ROW2CELL Clause"

### A.2 Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements

You can use OLAP DML commands within your SELECT FROM OLAP_TABLE statements as described in:

- "Using OLAP DML Expressions as Single-Row Functions"

- "Modifying an Analytic Workspace From Within a SELECT FROM OLAP_TABLE Statement"

#### A.2.1 Using OLAP DML Expressions as Single-Row Functions

SQL functions are typically single-row functions that return a single result row for every row of a queried table or view. Oracle supports several predefined SQL single-row functions, for example `COS`, `LOG`, and `ROUND`, which return numeric data, and `UPPER` and `LOWER`, which return character data.

Within the context of a `SELECT FROM OLAP_TABLE` statement, there are four SQL functions that you can use to wrap OLAP DML functions so that the OLAP DML function acts as a single-row function. There are four functions that return the results of expressions of different OLAP DML data types: OLAP_EXPRESSION for Oracle OLAP numeric expressions, OLAP_EXPRESSION_BOOL for Oracle OLAP Boolean expressions, OLAP_EXPRESSION_DATE for Oracle OLAP datetime expressions, and OLAP_EXPRESSION_TEXT for Oracle OLAP text expressions. One argument of each of these SQL functions is an OLAP DML function.

You can specify the OLAP_EXPRESSION function and its variants in the same way you specify other Oracle single-row functions, notably in the select list, `WHERE`, and `ORDER BY` clauses.

#### A.2.2 Modifying an Analytic Workspace From Within a SELECT FROM OLAP_TABLE Statement

There are several mechanisms for modifying an analytic workspace on the fly during the execution of `OLAP_TABLE`.

You can use the `OLAP_CONDITION` SQL function modifies an analytic workspace within the context of a `SELECT FROM OLAP_TABLE` statement. You can specify `OLAP_CONDITION` like other Oracle functions, typically in the `WHERE` clause. Using the `OLAP_CONDITION`, you can set an option, execute a `LIMIT` command, execute an OLAP model or forecast, or run a program. The changes made to the workspace can be transitory or they can persist in your session upon completion of the query.

In addition to `OLAP_CONDITION`, you can use syntax supported by the `OLAP_TABLE` function itself: The `PREDMLCMD` and `POSTDMLCMD` clauses in the limit map, and the olap_command parameter. `OLAP_CONDITION` has the advantage of portability, because it is not embedded within `OLAP_TABLE`, and versatility, because it can be applied at different entry points.

`OLAP_TABLE` saves the status of dimensions in the limit map before executing the `LIMIT` commands that generate the result set for the query. After the data is fetched, `OLAP_TABLE` restores the status of the dimensions. You can specify a `PREDMLCMD` clause in the limit map to cause an OLAP DML command to execute before the dimension status is saved. Modifications resulting from the `PREDMLCMD` clause remain in the workspace after execution of `OLAP_TABLE`, unless reversed with a `POSTDMLCMD` clause. For more information, see "limit_map".

The olap_command parameter of `OLAP_TABLE` specifies an OLAP DML command that executes immediately before the result set is fetched. In some circumstances, the olap_command parameter may contain an OLAP DML [FETCH](olap-dml-commands-a-g.md) command, which itself manages the fetch. Limits set by the olap_command parameter are only in effect during the execution of `OLAP_TABLE`. For more information, see "olap_command".

### A.3 OLAP_TABLE

`OLAP_TABLE` is a SQL function that extracts multidimensional data from an analytic workspace and presents it in the two-dimensional format of a relational table.

**See Also:**

"Creating Relational Views Using OLAP_TABLE" and "Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements"

The `OLAP_TABLE` function returns multidimensional data in an analytic workspace as a logical table.

The order in which `OLAP_TABLE` processes information specified in its input parameters is described in "Order of Processing in OLAP_TABLE".

`OLAP_TABLE` is the fundamental mechanism in the database for querying an analytic workspace. Within a SQL statement, you can specify an `OLAP_TABLE` function call wherever you would provide the name of a table or view.

`OLAP_TABLE` returns a table of objects that can be joined to relational tables and views, and to other tables of objects populated by `OLAP_TABLE`.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL Worksheet.

#### Returns

A table type whose rows are objects (ADTs) that identify the selected workspace data. See "Creating Relational Views Using OLAP_TABLE".

#### Syntax

    OLAP_TABLE(
            analytic_workspace    IN   VARCHAR2,
            table_object          IN   VARCHAR2,
            olap_command          IN   VARCHAR2,
            limit_map1            IN   VARCHAR2,
            limit_map2            IN   VARCHAR2,
                  .
                  .
                  .
            limit_map8            IN   VARCHAR2)
         RETURN TYPE;

#### Parameters

analytic_workspace
Provides the name of the analytic workspace where the source data is stored. It also specifies how long the analytic workspace is attached to your OLAP session, which opens on your first call to `OLAP_TABLE`.

This parameter is always required by `OLAP_TABLE`.

The syntax of this parameter is:

    '[owner.]aw_name DURATION QUERY | SESSION'

For example:

    'olapuser.xademo DURATION SESSION'

- owner

  Specify owner whenever you are creating views to be accessed by other users. Otherwise, you can omit the owner if you own the analytic workspace. It is required only when you are logged in under a different user name than the owner.

- QUERY

  Attaches an analytic workspace for the duration of a single query. Use `QUERY` only when you must see updates to the analytic workspace made in other sessions.

- SESSION

  Attaches an analytic workspace and keeps it attached after the query. It provides better performance than `QUERY` because it keeps the OLAP session open. This performance difference is significant when the function is called without either a table_object parameter or `AS` clauses in the limit map; in this case, the `OLAP_TABLE` function must determine the appropriate table definition. See "Using OLAP_TABLE With Automatic ADTs".

table_object
The name of a predefined table of objects, as described in "Using OLAP_TABLE With Predefined ADTs".

This parameter is optional. Omit this parameter when you are using automatic ADTs.

The syntax of this parameter is:

    'table_name'

For example:

    'product_dim_tbl'

When you specify the table_name parameter, the column data types for the returned data are predefined. In this case you cannot use `AS` clauses in the limit map.

When you omit the table_name parameter, the column data types for the returned data are generated at run time. You can either provide the target data types with `AS` clauses in the limit map, or you can use the default data types described in Table A-2. See "Using OLAP_TABLE With Automatic ADTs".

olap_command
A single OLAP DML command. To execute multiple commands, create a program in your analytic workspace and call the program in this parameter. The power and flexibility of this parameter comes from its ability to process virtually any data manipulation commands available in the OLAP DML.

The order in which `OLAP_TABLE` processes the olap_command parameter is specified in "Order of Processing in OLAP_TABLE".

The syntax of this parameter is:

    'olap_command'

There are two distinct ways of using the olap_command parameter:

- To make changes in the workspace session immediately before the data is fetched (after all the limits have been applied) as described in "Using FETCH in the olap_command Parameter".

- To specify the source data directly instead of using a limit map as described in "Using olap_command with a Limit Map".

limit_map
Maps workspace objects to relational columns and identifies the role of each one. See "Creating Relational Views Using OLAP_TABLE".

The limit map can also specify special instructions to be executed by `OLAP_TABLE`. For example: It can cause an OLAP DML command to execute before or after the limit map is processed; it can specify a `ROW2CELL` column for the `OLAP_CONDITION` and `OLAP_EXPRESSION` functions. (See "OLAP_CONDITION" and "OLAP_EXPRESSION".)

The order in which `OLAP_TABLE` processes information in the limit map is specified in "Order of Processing in OLAP_TABLE".

The limit map parameter is generally a required parameter. It can only be omitted when you specify a `FETCH` command in the olap_command parameter. See the discussion of "olap_command".

You can supply the entire text of the limit map as a parameter to `OLAP_TABLE`, or you can store all or part of the limit map in a text variable in the analytic workspace and reference it using ampersand substitution. For example, the following `OLAP_TABLE` query uses a limit map stored in a variable called `limitmapvar` in the `MYAW` analytic workspace of the `MYAW_AW` schema.

    SELECT * FROM TABLE(OLAP_TABLE(
              'myaw_aw.myaw DURATION SESSION',
              '',
              '',
              '&(myaw_aw.myaw!limitmapvar)');

If you supply the limit map as text within the call to `OLAP_TABLE`, then it has a maximum length of 4,000 characters, which is imposed by PL/SQL. If you store the limit map in the analytic workspace, then the limit map has no maximum length.

**Note:**

Several analytic workspace objects must be predefined within the workspace to support the mapping of dimension hierarchies in the limit map. For more information, see "Required OLAP DML Objects".

The syntax of the limit map has numerous clauses, primarily for defining dimension hierarchies. Pay close attention to the presence or absence of commas, because syntax errors prevents your limit map from being parsed.

    '[MEASURE column [AS datatype] FROM {measure | AW_EXPR expression}]
               .
               .
     DIMENSION [column [AS datatype] FROM] dimension
        [WITH
           [HIERARCHY [column [AS datatype] FROM] parent_relation
              [(hierarchy_dimension ''hierarchy_name'')]
              [INHIERARCHY inhierarchy_obj]
              [GID column [AS datatype] FROM gid_relation]
              [PARENTGID column [AS datatype] FROM gid_relation]
              [FAMILYREL column1 [AS datatype],
                         column2 [AS datatype],
                          ... columnn [AS datatype]
                         FROM {expression1, expression2, ... expressionn |
                               family_relation USING level_dimension }
                         [LABEL label_variable]]
              [HATTRIBUTE column [AS datatype] FROM hier_attribute_variable]
               .
               .
           ]
           [ATTRIBUTE column [AS datatype] FROM attribute_variable]
               .
               .
        ]
     [ROW2CELL column]
     [LOOP  loop-clause]
     [PREDMLCMD olap_command]
     [POSTDMLCMD olap_command]'

Where:

column is the name of a column in the target table.

datatype is the data type of column.

measure is a variable, formula, or relation in the analytic workspace.

expression is a formula or qualified data reference for objects in the analytic workspace.

dimension is a dimension in the analytic workspace.

parent_relation is a self-relation in the analytic workspace that defines the hierarchies for dimension. See "[Parentrel Relation](olap-dml-basic-concepts.md)" for more information.

hierarchy_dimension is a dimension in the analytic workspace that contains the names of the hierarchies for dimension. See "[Hierlist Dimension](olap-dml-basic-concepts.md)" for more information

hierarchy_name is a member of hierarchy_dimension.

inhierarchy_obj is a variable or valueset in the analytic workspace that identifies which dimension members are in each level of the hierarchy. See "[Inhier Valueset or Variable](olap-dml-basic-concepts.md)" for more information

gid_relation is a relation in the analytic workspace that contains the grouping ID of each dimension member in the hierarchy. See "[Gidrel Relation](olap-dml-basic-concepts.md)" for more information

family_relation is a self-relation that provides the full parentage of each dimension member in the hierarchy. See "[Familyrel Relation](olap-dml-basic-concepts.md)" for more information

level_dimension is a dimension in the analytic workspace that contains the names of the levels for the hierarchy. See "[Levellist Dimension](olap-dml-basic-concepts.md)" for more information

label_variable is a variable in the analytic workspace that contains descriptive text values for dimension.

hier_attribute_variable is a variable in the analytic workspace that contains attribute values for hierarchy_name.

attribute_variable is a variable in the analytic workspace that contains attribute values for dimension.

loop_clause specifies how Oracle OLAP determines how it loops through data values and what rows to create in the relational table. When you exclude a LOOP clause, Oracle OLAP loops through all of the data values that are identified by the dimensions in the DIMENSION clauses in the limit map.

For the complete syntax of the LOOP clause see "LOOP Clause".

olap_command is an OLAP DML command.

Detailed syntax for each of the clauses of the limit-map parameter follows.

- MEASURE Clause

  The `MEASURE` clause maps a variable, formula, or relation in the analytic workspace to a column in the target table. You can list any number of `MEASURE` clauses. This clause is optional when, for example, you want to create a dimension view.

  The `AS` subclause specifies the data type of the target column. You can specify an `AS` subclause when the table of objects has not been predefined. See "Using OLAP_TABLE With Automatic ADTs".

  In the `FROM` subclause, you can either specify the name of a variable, formula, or relation or an OLAP expression that evaluates to one of these objects. For example:

      AW_EXPR analytic_cube_sales - analytic_cube_cost
      or
      AW_EXPR LOGDIF(analytic_cube_sales, 1, time, LEVELREL time.lvlrel)

- DIMENSION Clause

  The `DIMENSION` clause identifies a dimension or conjoint in the analytic workspace that dimensions one or more measures or attributes, or provides the dimension members for one or more hierarchies in the limit map.

  The column subclause is optional when you do not want the dimension members themselves to be represented in the table. In this case, include a dimension attribute that can be used for data selection.

  For a description of the `AS` subclause, see "MEASURE Clause".

  Every limit map should have at least one `DIMENSION` clause. If the limit map contains `MEASURE` clauses, then it should also contain a single `DIMENSION` clause for each dimension of the measures, unless a dimension is being limited to a single value. If the measures are dimensioned by a composite, then you must identify each dimension in the composite with a `DIMENSION` clause. For the best performance when fetching a large result set, identify the composite in a `LOOP` clause. See "LOOP Clause".

  A dimension can be named in only one `DIMENSION` clause. Subclauses of the `DIMENSION` clause identify the dimension hierarchies and attributes.

  - WITH Subclause for Dimension Hierarchies and Attributes

    The `WITH` subclause introduces a `HIERARCHY` or `ATTRIBUTE` subclause. If you do not specify hierarchies or attributes, then omit the `WITH` keyword. If you specify both hierarchies and attributes, then precede them with a single `WITH` keyword.

  - WITH HIERARCHY Subclause

    The `HIERARCHY` subclause identifies the parent self-relation in the analytic workspace that defines the hierarchies for the dimension. See "[Parentrel Relation](olap-dml-basic-concepts.md)" for more information,

    The `HIERARCHY` subclause is optional when the dimension does not have a hierarchy, or when the status of the dimension has been limited to a single level of the hierarchy. When a dimension has multiple hierarchies, specify a `HIERARCHY` subclause for each one and specify a hierarchy_dimension phrase. The hierarchy_dimension identifies a dimension in the analytic workspace which holds the names of the hierarchies for this dimension. See "[Hierlist Dimension](olap-dml-basic-concepts.md)" for more information.

    hierarchy_name is a member of hierarchy_dimension. The hierarchy dimension is limited to hierarchy_name for all workspace objects that are referenced in subsequent subclauses for this hierarchy (that is, `INHIERARCHY`, `GID`, `PARENTGID`, `FAMILYREL`, and `HATTRIBUTE`).

    For a description of the column subclause, see "DIMENSION Clause".

    The following table lists the keywords in the `HIERARCHY` subclause:

    Table A-1 Keywords of the HIERARCHY Subclause

    | Keyword       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `INHIERARCHY` | The `INHIERARCHY` subclause identifies a boolean variable or a valueset in the analytic workspace that identifies the dimension members in each level of the hierarchy. See "[Inhier Valueset or Variable](olap-dml-basic-concepts.md)" for more information.<br>It is good practice to include an `INHIERARCHY` subclause, because `OLAP_TABLE` saves the status of all dimensions with `INHIERARCHY` subclauses during the processing of the limit map. It is required when there are members of the dimension that are omitted from the hierarchy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `GID`         | The `GID` subclause maps an integer variable in the analytic workspace, which contains the grouping ID for each dimension member, to a column in the target table. The grouping ID variable is populated by the OLAP DML [GROUPINGID command](olap-dml-commands-a-g.md). See "[Gidrel Relation](olap-dml-basic-concepts.md)" for more information.<br>The `GID` subclause is required for Java applications that use the OLAP API.<br>For a description of the `AS` subclause, see "MEASURE Clause".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `PARENTGID`   | The `PARENTGID` subclause calculates the grouping IDs for the parent relation using the GID variable in the analytic workspace. The parent GIDs are not stored in an analytic workspace object. Instead, you specify the same GID variable for the PARENTGID clause that you used in the GID clause. The PARENTGID clause is recommended for Java applications that use the OLAP API.<br>For a description of the `AS` subclause, see "MEASURE Clause".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `FAMILYREL`   | The `FAMILYREL` subclause is used primarily to map a family relation in the analytic workspace to multiple columns in the target table. See "[Familyrel Relation](olap-dml-basic-concepts.md)" for more information. You can use multiple `FAMILYREL` clauses for each hierarchy.<br>List the columns in the order of level_dimension which is a dimension in the analytic workspace that holds the names of all the levels for the dimension. See "[Levellist Dimension](olap-dml-basic-concepts.md)" for more information.<br>If you do not want a particular level included, then specify null for the target column. For a description of the `AS` subclause, see "MEASURE Clause".<br>The `LABEL` keyword identifies a text attribute that provides more meaningful names for the dimension members.<br>The tabular data resulting from a `FAMILYREL` clause is in rollup form, in which each level of the hierarchy is represented in a separate column, and the full parentage of each dimension member is identified within the row. See Example A-7. |
    | `HATTRIBUTE`  | The `HATTRIBUTE` subclause maps a hierarchy-specific attribute variable, dimensioned by hierarchy_dimension in the analytic workspace, to a column in the target table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

  - WITH ATTRIBUTE Subclause

    The `ATTRIBUTE` subclause maps an attribute variable in the analytic workspace to a column in the target table.

    If attribute_variable has multiple dimensions, then values are mapped for all members of dimension, but only for the first member in the current status of additional dimensions. For example, if your attributes have a language dimension, then you must set the status of that dimension to a particular language. You can set the status of dimensions in a `PREDMLCMD` clause.

- ROW2CELL Clause

  The `ROW2CELL` clause creates a `RAW` column, between 16 and 32 characters wide, in the target table and populates it with information that is used by the OLAP expression functions. The `OLAP_CONDITION` function also uses the `ROW2CELL` column. Specify a `ROW2CELL` column when creating a view to be used by these functions. See "Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements" and "Adding Calculated Columns to the Relational View".

- LOOP Clause

  The `LOOP` clause specifies how Oracle OLAP loops through the data when retrieving values. When you omit a LOOP clause in a limit map, Oracle OLAP uses the DIMENSION clauses in that limit map to determine the values to loop over. Oracle OLAP loops over only those tuples that identify measure cells that do not contain NA or null. When you include a LOOP clause, you specify one of the following types of subclauses: the optimized_subclause or the union_subclause.

  The optimized_subclause specifies that Oracle OLAP automatically create the union_subclause by which it loops through the data. The union_subclause created never includes any DENSE phrases. Consequently, when you specify the optimized_subclause, Oracle OLAP loops over only those tuples that identify measure cells that do not contain NA or null. The optimized_subclause has the following syntax.

  OPTIMIZED \[MEASURES\]

  where the optional MEASURES keyword specifies that after identifying the tuples to loop through, Oracle OLAP remove any values that are dimension values that are not dimensions of the objects identified in the MEASURES clauses of the limit map.

  **Tip:**

  You can use the [\$LOOP_AGGMAP](olap-dml-properties.md), [\$LOOP_DENSE](olap-dml-properties.md), and [\$LOOP_VAR](olap-dml-properties.md) properties, to specify more information as to how OLAP_TABLE loops over a formula.

  The union_subclause specifies exactly how Oracle OLAP determines which base dimensions it uses to identify what data values to loop through. For a successful union to occur, the objects that are referenced in this subclause must have the same base dimensions. The union_subclause has the following syntax.

         \[ignore_phrase\] \[dense_phrase\] UNION ({aggmap_phrase  \| list_phrase }...)\]

  where:

  aggmap_phrase specifies how Oracle OLAP loops through the values of an aggregated variable. It has the following syntax.

               AGGMAP (ignore_phrase\] \[dense_phrase\] aggmap {variable \| dimension_list})

  list_phrase specifies how Oracle OLAP loops through the values of a composite, partition template, or dimension. It has the following syntax.

               LIST (\[ignore_phrase\] \[dense_phrase\]  dimension_list)

  - ignore_phrase specifies the dimension values that you do not want Oracle OLAP to loop over. It has the following syntax.

    IGNORE (ignore_list )

    For ignore_list you can specify one or more of the following separated by commas.

          dimension_name
          valueset_name
          COMPLEMENT (valueset_name)

    Within a single ignore_list you cannot specify a dimension in multiple ways. In other words, you cannot specify both a dimension and a valueset for that same dimension; you cannot specify two valuesets for the same dimension.

    **Note:**

    The result of specifying IGNORE valueset-name is similar to specifying LIMIT REMOVE valueset-name (see [LIMIT command](olap-dml-commands-h-z.md)).

  - dense_phrase specifies values that Oracle OLAP loops over even when the measure cells identified by those values contain NA or null. Specifying a dimension in a DENSE phrase is similar to requesting a relational outer join. Typically, you include dimension values in a DENSE phrase to perform time-series processing (for example, to lag over time). A DENSE phrase has the following syntax.

    DENSE (dense_list )

    For dense_list you can specify one or more of the following separated by commas.

          dimension_name
          valueset_name
          COMPLEMENT (valueset_name)

    Within a single dense_list you cannot specify a dimension in multiple ways. In other words, you cannot specify both a dimension and a valueset for that same dimension; you cannot specify two valuesets for the same dimension.

    However, you can have one valueset for a dimension in the outer `DENSE` phrase and another valueset for the same dimension in an inner `DENSE` phrase. If a dimension or a valueset of a dimension is specified in both an inner and outer `DENSE` phrase, Oracle OLAP loops densely over the union of the dense regions. If the dimension, itself, appears in either place, Oracle OLAP loops densely over the whole dimension.

  - aggmap is the name of an aggmap object. When you specify only the name of an aggmap object, Oracle OLAP uses the values in the PRECOMPUTE phrases of the aggmap to identify the values to loop

  - variable is the name of the variable aggregated by aggmap_name.

  - dimension_list is a list of one or more composites, partition templates, or dimensions.

- PREDMLCMD Clause

  The `PREDMLCMD` clause specifies an OLAP DML command that is executed before the data is fetched from the analytic workspace into the target table. It can be used, for example, to execute an OLAP model or forecast whose results will be fetched into the table. The results of the command are in effect during execution of the limit map, and continue into your session after execution of `OLAP_TABLE` is complete. See "Order of Processing in OLAP_TABLE".

- POSTDMLCMD Clause

  The `POSTDMLCMD` clauses specifies an OLAP DML command that is executed after the data is fetched from the analytic workspace into the target table. It can be used, for example, to delete objects or data that were created by commands in the `PREDMLCMD` clause, or to restore the dimension status that was changed in a `PREDMLCMD` clause. See "Order of Processing in OLAP_TABLE" .

#### Usage Notes

Limit Maps

`OLAP_TABLE` uses a limit map to map dimensions and measures defined in an analytic workspace to columns in a logical table. The limit map combines with the `WHERE` clause of a SQL `SELECT` statement to generate a series of OLAP DML [LIMIT command](olap-dml-commands-h-z.md)s that are executed in the analytic workspace.

`OLAP_TABLE` can use a limit map with a predefined logical table, or it can use the information in a limit map to dynamically generate a logical table at run time.

**See Also:**

The discussion of the "limit_map" parameter.

Logical Tables

The logical table populated by `OLAP_TABLE` is actually a table type whose rows are user-defined object types, also known as Abstract Data Types or ADTs.

A user-defined object type is composed of attributes, which are equivalent to the columns of a table. The basic syntax for defining a row is as follows.

    CREATE TYPE object_name AS OBJECT (
       attribute1      datatype,
       attribute2      datatype,
       attributen      datatype);

A table type is a collection of object types; this collection is equivalent to the rows of a table. The basic syntax for creating a table type is as follows.

    CREATE TYPE table_name AS TABLE OF object_name;

**See Also:**

- [About Object Types](../adobj/key-features-object-relational-model.md) in Oracle Database Object-Relational Developer's Guide for information about object types

- [CREATE TYPE](../sqlrf/CREATE-TYPE.md) in Oracle Database SQL Language Reference

Using OLAP_TABLE With Predefined ADTs

You can predefine the table of objects or generate it dynamically. When you create the table type in advance, it is available in the database for use by any invocation of `OLAP_TABLE`. Queries that use predefined objects typically perform better than queries that dynamically generate the objects. See "Using OLAP_TABLE With Predefined ADTs".

Using OLAP_TABLE With Automatic ADTs

If you do not supply the name of a table type as an argument, `OLAP_TABLE` uses information in the limit map to generate the logical table automatically. In this case, the table type is only available at run time within the context of the calling SQL `SELECT` statement. See "Using OLAP_TABLE With Automatic ADTs".

When automatically generating ADTs, `OLAP_TABLE` uses default relational data types for the target columns unless you override them with `AS` clauses in the limit map. The default data type conversions used by `OLAP_TABLE` are described in the following table:

Table A-2 Default Data Type Conversions

| Analytic Workspace Data Type              | SQL Data Type     |
|:------------------------------------------|:------------------|
| `ID`                                      | `CHAR(8)`         |
| `TEXT`                                    | `VARCHAR2(4000)`  |
| `TEXT``(n)`                               | `VARCHAR2``(n)`   |
| `NTEXT`                                   | `NVARCHAR2(4000)` |
| `NTEXT``(n)`                              | `NVARCHAR2``(n)`  |
| `NUMBER`                                  | `NUMBER`          |
| `NUMBER``(p,s)`                           | `NUMBER``(p,s)`   |
| `LONGINTEGER`                             | `NUMBER(19)`      |
| `INTEGER`                                 | `NUMBER(10)`      |
| `SHORTINTEGER`                            | `NUMBER(5)`       |
| `INTEGER WIDTH 1`                         | `NUMBER(3)`       |
| `BOOLEAN`                                 | `NUMBER(1)`       |
| `DECIMAL`                                 | `BINARY_DOUBLE`   |
| `SHORTDECIMAL`                            | `BINARY_FLOAT`    |
| `DATE`                                    | `DATE`            |
| `DAY`, `WEEK`, `MONTH`, `QUARTER`, `YEAR` | `DATE`            |
| `DATETIME`                                | `TIMESTAMP`       |
| `COMPOSITE`                               | `VARCHAR2(4000)`  |
| Other                                     | `VARCHAR2(4000)`  |

Using olap_command with a Limit Map

You may want your application to modify the analytic workspace on the fly during the execution of `OLAP_TABLE`.

A common use of the olap_command parameter is to limit one or more dimensions. If you limit any of the dimensions that have `INHIERARCHY` clauses in the limit map, then the status of those dimensions is changed only during execution of this call to `OLAP_TABLE`; the limits do not affect the rest of your OLAP session. However, other commands (for example, commands that limit dimensions not referenced with `INHIERARCHY` clauses) can affect your session.

If you want a limit on a dimension in the limit map to stay in effect for the rest of your session, and not just during the command, specify it in the `PREDMLCMD` clause of the limit map or specify an `OLAP_CONDITION` function in the `SQL SELECT` statement.

The following is an example of a `LIMIT` command in the olap_command parameter.

    'LIMIT product TO product_member_levelrel ''L2'''

**See Also:**

"OLAP_CONDITION"

Using FETCH in the olap_command Parameter

If you specify an OLAP DML [FETCH](olap-dml-commands-a-g.md) command in the olap_command parameter, `OLAP_TABLE` uses it, instead of the instructions in the limit map, to fetch the source data for the table object. Because of this usage, the olap_command parameter is sometimes referred to as the data map. In general, do not specify a limit map if you specify a `FETCH` command.

**Note:**

Normally, use the `FETCH` command with `OLAP_TABLE` only if you are upgrading an Express application that used the `FETCH` command for SNAPI. If you are upgrading, note that the full syntax is the same in Oracle as in Express 6.3. You can use the same `FETCH` commands in `OLAP_TABLE` that you used previously in SNAPI. For the syntax of the `FETCH` command, see "[FETCH](olap-dml-commands-a-g.md)".

`FETCH` specifies explicitly how analytic workspace data is mapped to a table object. The basic syntax is:

    FETCH expression...

Enter one expression for each target column, listing the expressions in the same order they appear in the row definition. Separate expressions with spaces or commas.You must enter the entire statement on one line, without line breaks or continuation marks of any type.

**See Also:**

"Using FETCH in the olap_command Parameter"

Order of Processing in OLAP_TABLE

The following list identifies the order in which the `OLAP_TABLE` function processes instructions in the limit map that can change the status of dimensions in the analytic workspace.

1.  Execute any OLAP DML command specified in the `PREDMLCMD` parameter of the limit map.

2.  Save the current status of all dimensions in the limit map so that it can be restored later (`PUSH` status).

3.  Keep in status only those dimension members specified by `INHIERARCHY` subclauses in the limit map (`LIMIT KEEP`).

4.  Within the status set during step 3, keep only those dimension members that satisfy the `WHERE` clause of the SQL `SELECT` statement containing the `OLAP_TABLE` function (`LIMIT KEEP`).

5.  Execute any OLAP DML command specified in the olap_command parameter of the `OLAP_TABLE` function. (If olap_command includes a `FETCH`, fetch the data.)

6.  Fetch the data (unless an OLAP DML `FETCH` command was specified in the olap_command parameter).

7.  Restore the status of all dimensions in the limit map (`POP` status).

8.  Execute any OLAP DML command specified in the `POSTDMLCMD` parameter of the limit map.

#### Examples

Because different applications have different requirements, several different formats are commonly used for fetching data into SQL from an analytic workspace. The examples in this section show how to create views using a variety of different formats.

Although these examples are shown as views, the `SELECT` statements can be extracted from them and used directly to fetch data from an analytic workspace into an application.

**Note:**

The examples in this section use predefined ADTs. You could modify them to use automatic ADTs. See "Using OLAP_TABLE With Automatic ADTs".

Example A-5 Script for an Embedded Total Dimension View Using OLAP_TABLE

This example shows the PL/SQL script used to create an embedded total view of the `TIME` dimension in an analytic workspace named MYAW. This view is similar to the view in Example A-2, but it specifies both a Calendar and a Fiscal hierarchy, and it includes `HATTRIBUTE` subclauses for hierarchy-specific End Date attributes.

The `INHIERARCHY` subclause identifies a valueset in the analytic workspace that lists all the dimension members in each hierarchy of a dimension. `OLAP_TABLE` saves the status of all dimensions in the limit map that have `INHIERARCHY` subclauses during the processing of the limit map. See "Order of Processing in OLAP_TABLE".

    CREATE TYPE awtime_row AS OBJECT (
                 awtime_id               VARCHAR2(12),
                 awtime_short_label      VARCHAR2(12),
                 awtime_cal_end_date     DATE,
                 awtime_fis_end_date     DATE);
    /
    CREATE TYPE awtime_table AS TABLE OF awtime_row;
    /
    CREATE OR REPLACE VIEW awtime_view AS
       SELECT awtime_id, awtime_short_label,
              awtime_cal_end_date, awtime_fis_end_date
          FROM TABLE(OLAP_TABLE(
             'myaw DURATION SESSION',
             'awtime_table',
             '',
             'DIMENSION awtime_id FROM time WITH
                 HIERARCHY time_parentrel
                    (time_hierlist ''CALENDAR'')
                    INHIERARCHY time_inhier
                    HATTRIBUTE awtime_cal_end_date  FROM time_cal_end_date
                 HIERARCHY time_parentrel
                    (time_hierlist ''FISCAL'')
                    INHIERARCHY time_inhier
                    HATTRIBUTE awtime_fis_end_date  FROM time_fis_end_date
              ATTRIBUTE awtime_short_label  FROM time_short_description'));
    /
    SQL>SELECT * FROM awtime_view;

    AWTIME_ID  AWTIME_SHORT_LABEL  AWTIME_CAL_END_DATE  AWTIME_FIS_END_DATE
    ---------  ------------------  -------------------  -------------------
    19         Jan-98              31-JAN-98            31-JAN-98
    20         Feb-98              28-FEB-98            28-FEB-98
    21         Mar-98              31-MAR-98            31-MAR-98
    22         Apr-98              30-APR-98            30-APR-98
    23         May-98              31-MAY-98            31-MAY-98
    24         Jun-98              30-JUN-98            30-JUN-98
    .
    .
    .
    .
    98         Q1-03               31-MAR-03            30-SEP-03
    99         Q2-03               30-JUN-03            31-DEC-03
    1          1998                31-DEC-98            30-JUN-99
    102        2003                31-DEC-03            30-JUN-04
    119        2004                31-DEC-04            30-JUN-05
    2          1999                31-DEC-99            30-JUN-00
    3          2000                31-DEC-00            30-JUN-01
    4          2001                31-DEC-01            30-JUN-02
    85         2002                31-DEC-02            30-JUN-03

Note that you must be sure to verify that you have created the views correctly by issuing `SELECT` statements against them. Only at that time do any errors in the call to `OLAP_TABLE` appear.

Example A-6 Creating a View of an Embedded Total Measure Using OLAP_TABLE

In a star schema, a separate measure view is needed with columns that can be joined to each of the dimension views. This example shows the PL/SQL script used to create a measure view with a column populated by a `ROW2CELL` clause to support custom measures. For information on ROW2CELL, "ROW2CELL Clause".

    CREATE TYPE awunits_row AS OBJECT (
                 awtime                  VARCHAR2(12),
                 awcustomer              VARCHAR2(30),
                 awproduct               VARCHAR2(30),
                 awchannel               VARCHAR2(30),
                 awunits                 NUMBER(16),
                 r2c                     RAW(32));
    /
    CREATE TYPE awunits_table AS TABLE OF awunits_row;
    /
    CREATE OR REPLACE VIEW awunits_view AS
       SELECT awunits,
              awtime, awcustomer, awproduct, awchannel, r2c
          FROM TABLE(OLAP_TABLE(
             'myaw DURATION SESSION',
             'awunits_table',
             '',
             'MEASURE awunits FROM units_cube_units
              DIMENSION awtime FROM time WITH
                 HIERARCHY time_parentrel
              DIMENSION awcustomer FROM customer WITH
                 HIERARCHY customer_parentrel
                           (customer_hierlist ''MARKET_ROLLUP'')
                    INHIERARCHY customer_inhier
              DIMENSION awproduct FROM product WITH
                 HIERARCHY product_parentrel
              DIMENSION channel WITH
                 HIERARCHY channel_parentrel
                 ATTRIBUTE  awchannel FROM channel_short_description
              ROW2CELL r2c'))
          WHERE awunits IS NOT NULL;

    SQL>SELECT awchannel, awunits FROM awunits_view
         WHERE    awproduct = '1'
         AND      awcustomer = '7'
         AND      awtime = '4';

    AWCHANNEL            AWUNITS
    ---------            -------
    All Channels         415392
    Direct Sales         43783
    Catalog              315737
    Internet             55872

Example A-7 Script for a Rollup View of Products Using OLAP_TABLE

Rollup form uses a column for each hierarchy level to show the full parentage of each dimension member. The only difference between the syntax for rollup form and the syntax for embedded total form is the addition of a `FAMILYREL` clause in the definition of each dimension in the limit map. For information on `FAMILYREL`, see "WITH HIERARCHY Subclause".

This example shows the PL/SQL script used to create a rollup view of the `PRODUCT` dimension. It shows a dimension view to highlight the differences in the syntax of the limit map from the one used for the embedded total form, as shown in Example A-5. Note that the target columns for these levels are listed in the `FAMILYREL` clause from most aggregate (`CLASS`) to least aggregate (`ITEM`), which is the order they are listed in the level list dimension. The family relation returns four columns. The most aggregate level (all products) is omitted from the view by mapping it to null.

Example A-8 shows the alternate syntax for the `FAMILYREL` clause, which uses QDRs to identify exactly which columns are mapped from the family relation.

The limit maps in Example A-7 and Example A-8 generate identical views.

    CREATE TYPE awproduct_row AS OBJECT (
                class       VARCHAR2(50),
                family      VARCHAR2(50),
                item        VARCHAR2(50));
    /
    CREATE TYPE awproduct_table AS TABLE OF awproduct_row;
    /
    CREATE OR REPLACE VIEW awproduct_view AS
       SELECT class, family, item
          FROM TABLE(OLAP_TABLE(
             'myaw DURATION QUERY',
             'awproduct_table',
             '',
             'DIMENSION product WITH
                HIERARCHY product_parentrel
                   FAMILYREL null, class, family, item
                      FROM product_familyrel USING product_levellist
                      LABEL product_short_description'));

    SQL> SELECT * FROM awproduct_view
                  ORDER BY class, family, item;

    CLASS            FAMILY             ITEM
    --------------   ----------------   ------------------------
    Hardware          CD-ROM             Envoy External 6X CD-ROM
    Hardware          CD-ROM             Envoy External 8X CD-ROM
    Hardware          CD-ROM             External 6X CD-ROM
    Hardware          CD-ROM             External 8X CD-ROM
    Hardware          CD-ROM             Internal 6X CD-ROM
    Hardware          CD-ROM             Internal 8X CD-ROM
    Hardware          CD-ROM
    Hardware          Desktop PCs        Sentinel Financial
    Hardware          Desktop PCs        Sentinel Multimedia
    .
    .
    .
    Software/Other   Operating Systems  UNIX/Windows 1-user pack
    Software/Other   Operating Systems  UNIX/Windows 5-user pack
    Software/Other   Operating Systems
    Software/Other

Example A-8 Script Using QDRs in the FAMILYREL Clause of OLAP_TABLE

    CREATE OR REPLACE TYPE awproduct_row AS OBJECT (
                 class       VARCHAR2(50),
                 family      VARCHAR2(50),
                 item        VARCHAR2(50));
    /
    CREATE TYPE awproduct_table AS TABLE OF awproduct_row;
    /
    CREATE OR REPLACE VIEW awproduct_view AS
       SELECT class, family, item
          FROM TABLE(OLAP_TABLE(
             'myaw DURATION QUERY',
             'awproduct_table',
             '',
             'DIMENSION product WITH
                HIERARCHY product_parentrel
                   FAMILYREL class, family, item FROM
                      product_familyrel(product_levellist ''CLASS''),
                      product_familyrel(product_levellist ''FAMILY''),
                      product_familyrel(product_levellist ''ITEM'')
                      LABEL product_short_description'));

    SQL> SELECT * FROM awproduct_view
                  ORDER BY by class, family, item;

    CLASS            FAMILY             ITEM
    --------------   ----------------   ------------------------
    Hardware          CD-ROM             Envoy External 6X CD-ROM
    Hardware          CD-ROM             Envoy External 8X CD-ROM
    Hardware          CD-ROM             External 6X CD-ROM
    Hardware          CD-ROM             External 8X CD-ROM
    Hardware          CD-ROM             Internal 6X CD-ROM
    Hardware          CD-ROM             Internal 8X CD-ROM
    Hardware          CD-ROM
    Hardware          Desktop PCs        Sentinel Financial
    Hardware          Desktop PCs        Sentinel Multimedia
    .
    .
    .
    Software/Other   Operating Systems  UNIX/Windows 1-user pack
    Software/Other   Operating Systems  UNIX/Windows 5-user pack
    Software/Other   Operating Systems
    Software/Other

Example A-9 Script Using FETCH with OLAP_TABLE

Oracle Express Server applications that are being revised for use with Oracle Database can use an OLAP DML [FETCH](olap-dml-commands-a-g.md) command instead of a limit map to map workspace objects to relational columns.

The `FETCH` command is supplied in the third parameter of `OLAP_TABLE`, which specifies a single OLAP DML command. See "olap_command".

The script that follows fetches data from two variables (`SALES` and `COST`) in an analytic workspace named `MYAW`, and calculates two custom measures (`COST_PRIOR_PERIOD` and `PROFIT`). This example also shows the use of `OLAP_TABLE` directly by an application, without creating a view.

Note that the `FETCH` statement in the following example is formatted with indentation for readability. In reality, the entire `FETCH` statement must be entered on one line, without line breaks or continuation characters

    CREATE TYPE measure_row AS OBJECT (
                 time                       VARCHAR2(20),
                 geography                  VARCHAR2(30),
                 product                    VARCHAR2(30),
                 channel                    VARCHAR2(30),
                 sales                      NUMBER(16),
                 cost                       NUMBER(16),
                 cost_prior_period          NUMBER(16),
                 profit                     NUMBER(16));
    /
    CREATE TYPE measure_table AS TABLE OF measure_row;
    /
    SELECT time, geography, product, channel,
           sales, cost, cost_prior_period, profit
              FROM TABLE(OLAP_TABLE(
                 'xademo DURATION SESSION',
                 'measure_table',
                 'FETCH time, geography, product, channel, analytic_cube_f.sales,
                        analytic_cube_f.costs,
                        LAG(analytic_cube_f.costs, 1, time, LEVELREL time_member_levelrel),
                        analytic_cube_f.sales - analytic_cube_f.costs',
                 ''))
              WHERE channel =    'STANDARD_2.TOTALCHANNEL' AND
                    product =    'L1.TOTALPROD' AND
                    geography =  'L1.WORLD'
              ORDER BY time;

This SQL `SELECT` statement returns the following result set:

    TIME      GEOGRAPHY PRODUCT      CHANNEL                 SALES       COST    COST_PRIOR_PERIOD    PROFIT
    --------- --------- ------------ ----------------------- --------- --------- ------------------ --------
    L1.1996   L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL 118247112   2490243                   115756869
    L1.1997   L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL  46412113   1078031          2490243   45334082
    L2.Q1.96  L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL  26084848    560379                    25524469
    L2.Q1.97  L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL  26501765    615399           560379   25886367
    L2.Q2.96  L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL  30468054    649004           615399   29819049
    L2.Q2.97  L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL  19910347    462632           649004   19447715
    L2.Q3.96  L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL  27781702    582693           462632   27199009
    L2.Q4.96  L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL  33912508    698166           582693   33214342
    L3.APR96  L1.WORLD  L1.TOTALPROD STANDARD_2.TOTALCHANNEL   8859808    188851                     8670957
                                                  .
                                                  .
                                                  .
    27 rows selected.

### A.4 OLAP_CONDITION

`OLAP_CONDITION` is a SQL function that dynamically executes an OLAP DML command during a query of an analytic workspace.

**See Also:**

OLAP_TABLE and "Modifying an Analytic Workspace From Within a SELECT FROM OLAP_TABLE Statement"

The `OLAP_CONDITION` function executes an OLAP DML command at one of three entry points in the limit map used in a call to `OLAP_TABLE` as described in "Entry Points for OLAP_CONDITION in the OLAP_TABLE Limit Map".

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL Worksheet.

#### Returns

The number `1` to indicate a successful invocation of `OLAP_CONDITION`.

#### Syntax

    OLAP_CONDITION(
              r2c          IN   RAW(32),
              expression   IN   VARCHAR2,
              event        IN   NUMBER DEFAULT 1);
          RETURN NUMBER;

#### Parameters

r2c
The name of a column specified by a `ROW2CELL` clause in the limit map. This parameter is used by `OLAP_CONDITION` to identify a particular invocation of `OLAP_TABLE`.

The `ROW2CELL` column is used in the processing of the single-row functions. (See "OLAP_EXPRESSION") `OLAP_CONDITION` simply uses it as an identifier.

For information on creating a `ROW2CELL` column, see "ROW2CELL Clause".

expression
A single OLAP DML command to be executed within the context of the `OLAP_TABLE` function identified by the r2c parameter

event
The event during `OLAP_TABLE` processing that triggers the execution of the OLAP DML command specified by the expression parameter. This parameter can have the value 0, 1, or 2, as described in Table A-3

#### Usage Notes

Entry Points for OLAP_CONDITION in the OLAP_TABLE Limit Map

Parameters of `OLAP_CONDITION` identify an invocation of `OLAP_TABLE`, specify an entry point in the limit map, and provide the OLAP DML command to be executed at that entry point.

The target limit map must include a `ROW2CELL` column. `OLAP_CONDITION` uses this column to identify an instance of `OLAP_TABLE`. Within that instance `OLAP_CONDITION` executes the OLAP DML command at one of three possible entry points. The entry point that you specify determines whether the condition affects the data returned by the query and whether the condition remains in effect upon completion of the query.

`OLAP_CONDITION` can be triggered at any of the following points:

- Before the status of the dimensions in the limit map is saved (which occurs before the result set is calculated).

- After the result set has been calculated and before it is fetched. (Default)

- After the result set has been fetched and the status of the dimensions in the limit map has been restored.

The entry points for `OLAP_CONDITION` are described in the following table. Refer to "Order of Processing in OLAP_TABLE" to determine where each entry point occurs.

Table A-3 Entry Points for OLAP_CONDITION in the OLAP_TABLE Limit Map

| Entry Point | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0           | Execute the OLAP DML command after the `PREDMLCMD` clause of the limit map is processed and before the status of the dimensions in the limit map is saved.<br>The entry point is between steps 1 and 2 in "Order of Processing in OLAP_TABLE".<br>If `OLAP_CONDITION` limits any of the dimensions in the limit map, the limits remain in the workspace after the execution of `OLAP_TABLE` (unless a command in the `POSTDMLCMD` clause of the limit map changes the status).                                                                                                                                                                                                                                          |
| 1           | Execute the OLAP DML command after the conditions of the `WHERE` clause are satisfied and before the data is fetched. (Default.)<br>The entry point is between steps 4 and 5 in "Order of Processing in OLAP_TABLE".<br>If an OLAP DML command (other than `FETCH`) is specified in the olap_command parameter of `OLAP_TABLE`, it is executed after `OLAP_CONDITION` and before the data is fetched. (The use of a `FETCH` command in the olap_command parameter, or in `OLAP_CONDITION` itself, is not generally recommended. See "Using FETCH in the olap_command Parameter".)<br>If `OLAP_CONDITION` limits any of the dimensions in the limit map, the limits remain in effect for the duration of the query only. |
| 2           | Execute the OLAP DML command after the data is fetched and the status of dimensions in the limit map has been restored.<br>The entry point is after step 8 in "Order of Processing in OLAP_TABLE".<br>If `OLAP_CONDITION` limits any dimensions, the limits remain in the analytic workspace after the query completes.                                                                                                                                                                                                                                                                                                                                                                                                 |

#### Examples

Several sample queries using `OLAP_CONDITION` are shown in Example A-11. These examples use the `PRICE_CUBE` in an analytic workspace named`MYAW`. The cube has a time dimension, a product dimension, and measures for unit cost and unit price.

The examples are based on a view called `unit_cost_price_view`. The SQL for creating this view is shown in Example A-10. For information about creating views of analytic workspaces, see "Creating Relational Views Using OLAP_TABLE".

Example A-10 View of PRICE_CUBE

    -- Create the logical row
    SQL>CREATE TYPE unit_cost_price_row AS OBJECT (
                aw_unit_cost          NUMBER,
                aw_unit_price         NUMBER,
                aw_product            VARCHAR2(50),
                aw_product_gid        NUMBER(10),
                aw_time               VARCHAR2(20),
                aw_time_gid           NUMBER(10),
                r2c                   RAW(32));

    -- Create the logical table
    SQL>CREATE TYPE unit_cost_price_table AS TABLE OF unit_cost_price_row;

    -- Create the view
    SQL>CREATE OR REPLACE VIEW unit_cost_price_view AS
        SELECT aw_unit_cost, aw_unit_price, aw_product, aw_product_gid,
               aw_time, aw_time_gid, r2c
          FROM TABLE(OLAP_TABLE(
             'myaw DURATION SESSION',
             'unit_cost_price_table',
             '',
             'MEASURE aw_unit_cost  FROM price_cube_unit_cost
              MEASURE aw_unit_price FROM price_cube_unit_price
              DIMENSION product WITH
                 HIERARCHY product_parentrel
                    INHIERARCHY product_inhier
                    GID aw_product_gid FROM product_gid
                 ATTRIBUTE aw_product FROM product_short_description
              DIMENSION time WITH
                 HIERARCHY time_parentrel
                    INHIERARCHY time_inhier
                    GID aw_time_gid FROM time_gid
                 ATTRIBUTE aw_time FROM time_short_description
              ROW2CELL r2c'));

    -- query the view
    SQL>SELECT * FROM unit_cost_price_view
                 WHERE aw_product = 'Hardware'
                 AND aw_time in ('2000', '2001', '2002', '2003')
                 ORDER BY aw_time;

    AW_UNIT_COST AW_UNIT_PRICE AW_PRODUCT AW_PRODUCT_GID AW_TIME AW_TIME_GID R2C
    ------------ ------------- ---------- -------------- ------- ----------- -----
       211680.12    224713.71  Hardware                3 2000             3  00...
       195591.60    207513.16  Hardware                3 2001             3  00...
       184413.05    194773.78  Hardware                3 2002             3  00...
        73457.31     77275.06  Hardware                3 2003             3  00...

Example A-11 Queries of UNIT_COST_PRICE_VIEW Using OLAP_CONDITION

The queries in this example use `OLAP_CONDITION` to modify the query of `UNIT_COST_PRICE_VIEW` in Example A-10. In each query, `OLAP_CONDITION` uses a different entry point to limit the `TIME` dimension to the year 2000.

In the first query, `OLAP_CONDIITON` uses entry point 0. The limited data is returned by `OLAP_TABLE`, and the limit remains in effect in the analytic workspace.

    SQL>SELECT * FROM unit_cost_price_view
                 WHERE aw_product = 'Hardware'
                 AND aw_time in ('2000', '2001', '2002', '2003')
                 AND OLAP_CONDITION(r2c,
                           'limit time to time_short_description eq ''2000''', 0)=1
                 ORDER BY aw_time;

    AW_UNIT_COST AW_UNIT_PRICE AW_PRODUCT AW_PRODUCT_GID AW_TIME AW_TIME_GID R2C
    ------------ ------------- ---------- -------------- ------- ----------- -----
       211680.12    224713.71  Hardware                3 2000             3  00...

    --Check status in the analytic workspace
    SQL>exec dbms_aw.execute('rpr time_short_description');

    TIME     TIME_SHORT_DESCRIPTION
    ----     ----------------------
      3      2000

    -- Reset status
    SQL>exec dbms_aw.execute('allstat');

In the next query, `OLAP_CONDIITON` uses entry point 1. The limited data is returned by `OLAP_TABLE`, but the limit does not remain in effect in the analytic workspace.

Note that the third parameter is not required in this case, because entry point 1 is the default.

    SQL>SELECT * FROM unit_cost_price_view
                 WHERE aw_product = 'Hardware'
                 AND aw_time in ('2000', '2001', '2002', '2003')
                 AND OLAP_CONDITION(r2c,
                           'limit time to time_short_description eq ''2000''', 1)=1
                 ORDER BY aw_time;

    AW_UNIT_COST AW_UNIT_PRICE AW_PRODUCT AW_PRODUCT_GID AW_TIME AW_TIME_GID R2C
    ------------ ------------- ---------- -------------- ------- ----------- -----
       211680.12    224713.71  Hardware                3 2000             3  00...

    --Check status in the analytic workspace
    SQL>exec dbms_aw.execute('rpr time_short_description');

    TIME     TIME_SHORT_DESCRIPTION
    ----     ----------------------
     19      Jan-98
     20      Feb-98
     21      Mar-98
     22      Apr-98
    .
    .
    .
      1      1998
      2      1999
      3      2000
      4      2001
     85      2002
    102      2003
    119      2004

    -- Reset status
    SQL>exec dbms_aw.execute('allstat');

In the final query, `OLAP_CONDIITON` uses entry point 2. The limit does not affect the data returned by `OLAP_TABLE`, but the limit remains in effect in the analytic workspace.

    SQL>SELECT * FROM unit_cost_price_view
                 WHERE aw_product = 'Hardware'
                 AND aw_time in ('2000', '2001', '2002', '2003')
                 AND OLAP_CONDITION(r2c,
                           'limit time to time_short_description eq ''2000''', 2)=1
                 ORDER BY aw_time;

    AW_UNIT_COST AW_UNIT_PRICE AW_PRODUCT AW_PRODUCT_GID AW_TIME AW_TIME_GID R2C
    ------------ ------------- ---------- -------------- ------- ----------- -----
       211680.12    224713.71  Hardware                3 2000             3  00...
       195591.60    207513.16  Hardware                3 2001             3  00...
       184413.05    194773.78  Hardware                3 2002             3  00...
        73457.31     77275.06  Hardware                3 2003             3  00...

    --Check status in the analytic workspace
    SQL>exec dbms_aw.execute('rpr time_short_description');

    TIME     TIME_SHORT_DESCRIPTION
    ----     ----------------------
      3      2000

### A.5 OLAP_EXPRESSION

`OLAP_EXPRESSION` is a SQL function that dynamically executes an OLAP DML boolean expression within the context of an `OLAP_TABLE` function. In addition to returning a custom measure, you can use this function in the `WHERE` and `ORDER BY` clauses to modify the result set of the query of the analytic workspace.

**See Also:**

"Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements" and "Adding Calculated Columns to the Relational View"

`OLAP_EXPRESSION_TEXT` returns character data. To return text, boolean, or date data, use OLAP_EXPRESSION_TEXT, OLAP_EXPRESSION_BOOL, or OLAP_EXPRESSION_DATE SQL functions.

Before you use this function, you must specify a `ROW2CELL` clause in the limit map used by `OLAP_TABLE`. `ROW2CELL` identifies a `RAW` column that `OLAP_TABLE` populates with information used by the OLAP single-row functions.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL Worksheet.

#### Returns

An evaluation of numeric_expression for each row of the table object returned by the `OLAP_TABLE` function.

`OLAP_EXPRESSION` returns numeric data. To return text, boolean, or date data, use the `OLAP_EXPRESSION_TEXT`, `OLAP_EXPRESSION_BOOL`, or `OLAP_EXPRESSION_DATE` functions.

#### Syntax

    OLAP_EXPRESSION(
              r2c                  IN   RAW(32),
              numeric_expression   IN   VARCHAR2)
          RETURN NUMBER;

#### Parameters

r2c
The name of a column specified by a `ROW2CELL` clause in the limit map. See "ROW2CELL Clause" of OLAP_TABLE.

numeric_expression
An OLAP DML expression that returns a numeric result.

**See Also:**

"[Numeric Expressions](data-types-operators-and-expressions.md)", [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md), and "[Guidelines for Using Quotation Marks in OLAP DML Commands](DBMS_AW-plsql-package.md)"

#### Examples

The following script was used to create the view `unit_cost_price_view`, which is used in Example A-12 and Example A-13 to illustrate the use of `OLAP_EXPRESSION`. For information about creating views of analytic workspaces, see "Creating Relational Views Using OLAP_TABLE".

Sample View: MYAW.UNIT_COST_PRICE_VIEW

    -- Create the logical row
    CREATE TYPE unit_cost_price_row AS OBJECT (
                aw_unit_cost          NUMBER,
                aw_unit_price         NUMBER,
                aw_product            VARCHAR2(50),
                aw_time               VARCHAR2(20),
                r2c                   RAW(32));
    /
    -- Create the logical table
    CREATE TYPE unit_cost_price_table AS TABLE OF unit_cost_price_row;
    /
    -- Create the view
    CREATE OR REPLACE VIEW unit_cost_price_view AS
        SELECT aw_unit_cost, aw_unit_price, aw_product, aw_time, r2c
          FROM TABLE(OLAP_TABLE(
             'myaw DURATION SESSION',
             'unit_cost_price_table',
             '',
             'MEASURE aw_unit_cost  FROM price_cube_unit_cost
              MEASURE aw_unit_price FROM price_cube_unit_price
              DIMENSION product WITH
                 HIERARCHY product_parentrel
                    INHIERARCHY product_inhier
                 ATTRIBUTE aw_product FROM product_short_description
              DIMENSION time WITH
                 HIERARCHY time_parentrel
                    INHIERARCHY time_inhier
                 ATTRIBUTE aw_time FROM time_short_description
              ROW2CELL r2c'));
    /

The following query shows some aggregate data in the view.

    SQL>SELECT * FROM unit_cost_price_view
                 WHERE aw_product = 'Hardware'
                 AND aw_time in ('2000', '2001', '2002', '2003')
                 ORDER BY aw_time;

    AW_UNIT_COST    AW_UNIT_PRICE    AW_PRODUCT    AW_TIME    R2C
    ------------    -------------    ----------    -------    -----
       211680.12        224713.71      Hardware       2000    00...
       195591.60        207513.16      Hardware       2001    00...
       184413.05        194773.78      Hardware       2002    00...
        73457.31         77275.06      Hardware       2003    00...

Example A-12 OLAP_EXPRESSION: Time Series Function in a WHERE Clause

This example uses the view described in "Sample View: MYAW.UNIT_COST_PRICE_VIEW".

The following `SELECT` statement calculates an expression with an alias of `PERIODAGO`, and limits the result set to calculated values greater than 50,000. The calculation uses the `LAG` function to return the value of the previous time period.

    SQL>SELECT aw_time time, aw_unit_cost unit_cost,
                OLAP_EXPRESSION(r2c,
                               'LAG(price_cube_unit_cost, 1, time,
                                    LEVELREL time_levelrel)') periodago
            FROM unit_cost_price_view
            WHERE aw_product = 'Hardware'
            AND OLAP_EXPRESSION(r2c,
                               'LAG(price_cube_unit_cost, 1, time,
                                    LEVELREL time_levelrel)') > 50000;

This `SELECT` statement produces these results.

    TIME                  UNIT_COST  PERIODAGO
    -------------------- ---------- ----------
    2003                   73457.31  184413.05
    2004                              73457.31
    1999                   231095.4  162526.92
    2000                  211680.12   231095.4
    2001                   195591.6  211680.12
    2002                  184413.05   195591.6
    Q2-99                  57587.34   57856.76
    Q3-99                  59464.25   57587.34
    Q4-99                  56187.05   59464.25
    Q1-00                  53982.32   56187.05
    Q2-00                  53629.74   53982.32
    Q3-00                  53010.65   53629.74
    Q4-00                  51057.41   53010.65
    Q1-01                  49691.22   51057.41

Example A-13 OLAP_EXPRESSION: Numeric Calculation in an ORDER BY CLause

This example uses the view described in "Sample View: MYAW.UNIT_COST_PRICE_VIEW".

This example subtracts costs from price, and gives this expression an alias of `MARKUP`. The rows are ordered by markup from highest to lowest.

    SQL>SELECT aw_time time, aw_unit_cost unit_cost, aw_unit_price unit_price,
                OLAP_EXPRESSION(r2c,
                          'PRICE_CUBE_UNIT_PRICE - PRICE_CUBE_UNIT_COST') markup
         FROM unit_cost_price_view
         WHERE aw_product = 'Hardware'
         AND aw_time in ('1998', '1999', '2000', '2001')
         ORDER BY OLAP_EXPRESSION(r2c,
                          'PRICE_CUBE_UNIT_PRICE - PRICE_CUBE_UNIT_COST') DESC;

This `SELECT` statement produces these results.

    TIME                  UNIT_COST   UNIT_PRICE  MARKUP
    -------------------- ----------  ----------  ---------
    1999                  231095.40   245412.91   14317.51
    2000                  211680.12   224713.71   13033.59
    2001                  195591.60   207513.16   11921.56
    1998                  162526.92   173094.41   10567.49

### A.6 OLAP_EXPRESSION_BOOL

`OLAP_EXPRESSION_BOOL` is a SQL function that dynamically executes an OLAP DML boolean expression within the context of an `OLAP_TABLE` function. In addition to returning a custom measure, you can use this function in the `WHERE` and `ORDER BY` clauses to modify the result set of the query of the analytic workspace.

**See Also:**

"Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements" and "Adding Calculated Columns to the Relational View"

`OLAP_EXPRESSION_TEXT` returns character data. To return numeric, text, or date data, use OLAP_EXPRESSION, OLAP_EXPRESSION_TEXT, or OLAP_EXPRESSION_DATE SQL functions.

Before you use this function, you must specify a `ROW2CELL` clause in the limit map used by `OLAP_TABLE`. `ROW2CELL` identifies a `RAW` column that `OLAP_TABLE` populates with information used by the OLAP single-row functions.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL Worksheet.

#### Returns

An evaluation of boolean_expression for each row of the table object returned by the `OLAP_TABLE` function.

`OLAP_EXPRESSION_BOOL` returns boolean data in the form 0 for false and 1 for true. To return numeric, date, or text data, use the `OLAP_EXPRESSION`, `OLAP_EXPRESSION_DATE`, or `OLAP_EXPRESSION_TEXT` functions.

#### Syntax

    OLAP_EXPRESSION_BOOL(
              r2c                  IN   RAW(32),
              boolean_expression   IN   VARCHAR2)
          RETURN NUMBER;

#### Parameters

r2c
The name of a column specified by a `ROW2CELL` clause in the limit map. See "ROW2CELL Clause" of OLAP_TABLE

boolean_expression
An OLAP DML expression that returns a Boolean result.

**See Also:**

"[Boolean Expressions](data-types-operators-and-expressions.md)", [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md), and "[Guidelines for Using Quotation Marks in OLAP DML Commands](DBMS_AW-plsql-package.md)"

#### Examples

The following script was used to create the view `awunits_view`, which is used in Example A-14 to illustrate the use of `OLAP_EXPRESSION_BOOL`.

Sample View: MYAW_AW.AWUNITS_VIEW

    -- Create the logical row
    CREATE TYPE awunits_row AS OBJECT (
                 awtime                  VARCHAR2(12),
                 awcustomer              VARCHAR2(30),
                 awproduct               VARCHAR2(30),
                 awchannel               VARCHAR2(30),
                 awunits                 NUMBER(16),
                 r2c                     RAW(32));
    /
    -- Create the logical table
    CREATE TYPE awunits_table AS TABLE OF awunits_row;
    /
    -- Create the view
    CREATE OR REPLACE VIEW awunits_view AS
       SELECT awunits,
              awtime, awcustomer, awproduct, awchannel, r2c
          FROM TABLE(OLAP_TABLE(
             'myaw_aw.myawaw DURATION SESSION',
             'awunits_table',
             '',
             'MEASURE awunits FROM units_cube_aw_units_aw
              DIMENSION awtime FROM time_aw WITH
                 HIERARCHY time_aw_parentrel
              DIMENSION awcustomer FROM customer_aw WITH
                 HIERARCHY customer_aw_parentrel
                           (customer_aw_hierlist ''MARKET_ROLLUP_AW'')
                    INHIERARCHY customer_aw_inhier
              DIMENSION awproduct FROM product_aw WITH
                 HIERARCHY product_aw_parentrel
              DIMENSION channel_aw WITH
                 HIERARCHY channel_aw_parentrel
                 ATTRIBUTE  awchannel FROM channel_aw_short_description
              ROW2CELL r2c'))
          WHERE awunits IS NOT NULL;
    /

The following query shows some aggregate data in the view. For all products in all markets during the year 2001, it shows the number of units sold through each channel.

    SQL> SELECT awchannel, awunits FROM awunits_view
         WHERE    awproduct = '1'
         AND      awcustomer = '7'
         AND      awtime = '4';

    AWCHANNEL            AWUNITS
    ---------            -------
    All Channels         415392
    Direct Sales         43783
    Catalog              315737
    Internet             55872

The following statements show the descriptions of the Product, Customer, and Time dimension members used in the query.

    SQL>execute dbms_aw.execute('limit product_aw to ''1''');
    SQL>execute dbms_aw.execute('rpr product_aw_short_description');

    PRODUCT_AW                 PRODUCT_AW_SHORT_DESCRIPTION
    --------------- --------------------------------------------------
    1               Total Product

    SQL>execute dbms_aw.execute('limit customer_aw to ''7''');
    SQL>execute dbms_aw.execute('rpr customer_aw_short_description');

    CUSTOMER_AW               CUSTOMER_AW_SHORT_DESCRIPTION
    --------------- --------------------------------------------------
    7               Total Market

    SQL>execute dbms_aw.execute('limit time_aw to ''4''');
    SQL>execute dbms_aw.execute('rpr time_aw_short_description');

    TIME_AW                     TIME_AW_SHORT_DESCRIPTION
    --------------- --------------------------------------------------
    4               2001

Example A-14 OLAP_EXPRESSION_BOOL Function in a SELECT List

This example uses the view described in "Sample View: MYAW_AW.AWUNITS_VIEW". The following `SELECT` statement calculates an expression with an alias of `lowest_units`, which indicates whether or not the number of units of each product was less than 500.

    SQL>SELECT awproduct products,
           olap_expression_bool(r2c, 'units_cube_aw_units_aw le 500') lowest_units
              FROM awunits_view
                   WHERE     awproduct > 39
                   AND       awproduct < 46
                   AND       awcustomer = '7'
                   AND       awchannel = 'Internet'
                   AND       awtime = '4';

    PRODUCTS        LOWEST_UNITS
    --------------- ------------
    40              0
    41              1
    42              1
    43              1
    44              1
    45              0

This query shows that products 41-44 all had less than 500 units. These products are the documentation sets in German, French, Spanish, and Italian. The selected products are shown as follows.

    SQL>execute dbms_aw.execute
               ('limit product_aw to product_aw gt 39 and product_aw lt 46');
    SQL>execute dbms_aw.execute('rpr product_aw_short_description');

    PRODUCT_AW                 PRODUCT_AW_SHORT_DESCRIPTION
    --------------- --------------------------------------------------
    40              O/S Documentation Set - English
    41              O/S Documentation Set - German
    42              O/S Documentation Set - French
    43              O/S Documentation Set - Spanish
    44              O/S Documentation Set - Italian
    45              O/S Documentation Set - Kanji

### A.7 OLAP_EXPRESSION_DATE

`OLAP_EXPRESSION_DATE` is a SQL function that dynamically executes an OLAP DML datetime expression within the context of an `OLAP_TABLE` function. In addition to returning a custom measure, you can use this function in the `WHERE` and `ORDER BY` clauses to modify the result set of the query of the analytic workspace.

**See Also:**

"Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements" and "Adding Calculated Columns to the Relational View"

`OLAP_EXPRESSION_TEXT` returns character data. To return numeric, boolean, or text data, use OLAP_EXPRESSION, OLAP_EXPRESSION_BOOL, or OLAP_EXPRESSION_TEXT SQL functions.

Before you use this function, you must specify a `ROW2CELL` clause in the limit map used by `OLAP_TABLE`. `ROW2CELL` identifies a `RAW` column that `OLAP_TABLE` populates with information used by the OLAP single-row functions.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL Worksheet.

#### Returns

An evaluation of date_expression for each row of the table object returned by the `OLAP_TABLE` function.

`OLAP_EXPRESSION_DATE` returns date data. To return numeric, boolean, or text data, use the `OLAP_EXPRESSION`, `OLAP_EXPRESSION_BOOL`, or `OLAP_EXPRESSION_TEXT` functions.

#### Syntax

    OLAP_EXPRESSION_DATE(
              r2c               IN   RAW(32),
              date_expression   IN   VARCHAR2)
          RETURN NUMBER;

#### Parameters

r2c
The name of a column specified by a `ROW2CELL` clause in the limit map. See "ROW2CELL Clause" of OLAP_TABLE

date_expression
An OLAP DML expression that returns an OLAP DML datetime result.

**See Also:**

"[Datetime and Interval Expressions](data-types-operators-and-expressions.md)", [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md), and "[Guidelines for Using Quotation Marks in OLAP DML Commands](DBMS_AW-plsql-package.md)"

#### Examples

Refer to the examples in OLAP_EXPRESSION and OLAP_EXPRESSION_BOOL for examples of OLAP single-row functions.

### A.8 OLAP_EXPRESSION_TEXT

`OLAP_EXPRESSION_TEXT` is a SQL function that dynamically executes an OLAP DML text expression within the context of an `OLAP_TABLE` function. In addition to returning a custom measure, you can use this function in the `WHERE` and `ORDER BY` clauses to modify the result set of the query of the analytic workspace.

**See Also:**

"Using OLAP DML Expressions in SELECT FROM OLAP_TABLE Statements" and "Adding Calculated Columns to the Relational View"

`OLAP_EXPRESSION_TEXT` returns character data. To return numeric, boolean, or date data, use OLAP_EXPRESSION, OLAP_EXPRESSION_BOOL, or OLAP_EXPRESSION_DATE SQL functions.

Before you use this function, you must specify a `ROW2CELL` clause in the limit map used by `OLAP_TABLE`. `ROW2CELL` identifies a `RAW` column that `OLAP_TABLE` populates with information used by the OLAP single-row functions.

**Note:**

You cannot execute this function from within the OLAP Worksheet. You must execute it in a SQL tool such as SQL Worksheet.

#### Returns

An evaluation of text_expression for each row of the table object returned by the `OLAP_TABLE` function.

#### Syntax

    OLAP_EXPRESSION_TEXT(
              r2c               IN   RAW(32),
              text_expression   IN   VARCHAR2)
          RETURN NUMBER;

#### Parameters

r2c
The name of a column specified by a `ROW2CELL` clause in the limit map. See "ROW2CELL Clause" of OLAP_TABLE

text_expression
An OLAP DML expression that returns a text result.

**See Also:**

"[Text Expressions](data-types-operators-and-expressions.md)", [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md), and "[Guidelines for Using Quotation Marks in OLAP DML Commands](DBMS_AW-plsql-package.md)"

#### Example

Refer to the examples in OLAP_EXPRESSION and OLAP_EXPRESSION_BOOL for examples of OLAP single-row functions.
