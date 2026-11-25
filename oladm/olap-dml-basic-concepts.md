This chapter contains the following topics:

- What is the OLAP DML?

- Basic Syntactic Units of the OLAP DML

- How to Execute OLAP DML Statements

- Introduction to Analytic Workspaces

- Introduction to Analytic Workspace Data Objects

- OLAP DML Statements Apply to All of the Values of a Data Object

### 1.1 What is the OLAP DML?

The OLAP DML is the original language for defining Oracle OLAP objects and manipulating Oracle OLAP data.

There are two major types of OLAP DML statements:

- OLAP DML statements that work against Oracle OLAP cubes and cube dimensions that have been previously defined in the Oracle data dictionary using the OLAP API. For an introduction to these statements, see "Cube-Aware OLAP DML Statements".

- OLAP DML statements that create and manipulate lower-level OLAP objects that are defined and stored in an analytic workspace. For an introduction to these statements, see "OLAP DML Statements that Work Directly on Analytic Workspace Objects".

#### 1.1.1 Cube-Aware OLAP DML Statements

OLAP cubes are first-class Oracle OLAP objects and are defined in the Oracle data dictionary. Some OLAP DML statements work against cubes and other first-class OLAP objects.

**See Also:**

Oracle OLAP User's Guide for information on OLAP cubes and other first-level OLAP objects.

The following OLAP DML programs work with previously-defined OLAP cubes and cube dimensions.

- [ADD_CUBE_MODEL](olap-dml-commands-a-g.md)
- [ADD_DIMENSION_MEMBER](olap-dml-commands-a-g.md)
- [ADD_MODEL_DIMENSION](olap-dml-commands-a-g.md)
- [CREATE_LOGICAL_MODEL](olap-dml-commands-a-g.md)
- [REMOVE_CUBE_MODEL](olap-dml-commands-h-z.md)
- [REMOVE_DIMENSION_MEMBER](olap-dml-commands-h-z.md)
- [REMOVE_MODEL_DIMENSION](olap-dml-commands-h-z.md)
- [SET_INCLUDED_MODEL](olap-dml-commands-h-z.md)
- [SET_PROPERTY](olap-dml-commands-h-z.md)
- [UPDATE_ATTRIBUTE_VALUE](olap-dml-commands-h-z.md)
- [UPDATE_DIMENSION_MEMBER](olap-dml-commands-h-z.md)
-

Typically, these programs take, as input, the Oracle data dictionary name of an OLAP cube or cube dimension. When the programs execute they not only make the necessary changes to the cube or cube dimension, they also make changes to all of the analytic workspace objects that underlie these cubes and cube dimensions.

Also, you can use the [OBJORG](olap-dml-functions-l-z.md) function in OLAP DML statements that are not cube-aware to specify the analytic workspace objects that underlie OLAP cubes and cube dimensions.

#### 1.1.2 OLAP DML Statements that Work Directly on Analytic Workspace Objects

Historically, OLAP DML statements did not work against first-level OLAP objects as defined in the OLAP data dictionary. Instead, OLAP DML statements create and manipulate lower-level OLAP objects that are defined and stored in an analytic workspace. This remains the case for most OLAP DML statements today.

**Note:**

Unless otherwise stated, statements and information provided in this manual applies to OLAP DML statements that are not cube-aware (that is, OLAP DML statements work directly on analytic workspace objects).

For OLAP DML statements that work directly on analytic workspace objects, if an object name is needed as input to the statement, the object name is the name of an object as defined in the analytic workspace, not as defined in the Oracle data dictionary.

You can use these OLAP DML statements to create programs that analyze analytic workspace data without using SQL, Java, the OLAP API, or the Oracle OLAP tools. You can use the OLAP DML to define the analytic workspaces and the objects that are stored in analytic workspaces. For example, you can:

- Create an analytic workspace as described in "Defining a New Analytic Workspace".

- Define the multidimensional data objects in an analytic workspace using the [DEFINE](olap-dml-commands-a-g.md) command.

- Define calculation objects and programs that analyze the data as described in [Formulas, Models, Aggregations, and Allocations](formulas-models-aggregations-and-allocations.md).

- Populate and analyze the data in the multidimensional data objects.

### 1.2 Basic Syntactic Units of the OLAP DML

The basic syntactic units of the OLAP DML are options, properties, commands, functions, and programs. All of these are sometimes collectively referred to as OLAP DML statements.

#### OLAP DML Options

An OLAP DML option is a special type of analytic workspace object that specifies the characteristic of some aspect of how Oracle OLAP calculates or formats data or what Oracle OLAP operations are activated. Some options are read-only, while others are read/write options for which you can specify values. Read/write options have default values.

You cannot define your own options as part of an analytic workspace. However, you can use any of the options that are defined as part of the Oracle OLAP DML. The options are documented as reference topics in [OLAP DML Options](olap-dml-options.md).

#### OLAP DML Properties

A property is a named value that is associated with a definition of an analytic workspace object. You can name, create, and assign properties to an object using an OLAP DML PROPERTY command.

Properties that begin with a \$ (dollar sign) are recognized by Oracle OLAP as system properties. You cannot create system properties; however, in some cases you can assign system properties to objects. These system properties are documented as reference topics in [OLAP DML Properties](olap-dml-properties.md).

#### OLAP DML Functions

OLAP functions work in much the same way as commands in other programming languages. They initiate action and return a value. The one exception is the looping nature of OLAP DML functions as discussed in "OLAP DML Statements Apply to All of the Values of a Data Object".

Most of the OLAP DML functions are standard text and calculation functions. Other OLAP DML functions return more complex information.Additionally, you can augment the functionality of the OLAP DML by writing an OLAP DML program for use as a function.

The built-in OLAP DML functions are documented as reference topics in [OLAP DML Functions: A - K](olap-dml-functions-a-k.md) and [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md).

#### OLAP DML Commands

OLAP DML commands work in much the same way as commands in other programming languages—the one exception is the looping nature of OLAP DML commands as discussed in "OLAP DML Statements Apply to All of the Values of a Data Object".

Many OLAP DML commands perform complex actions. Some of these commands are data definition commands like the AW command which you use to create an analytic workspace and the DEFINE command which you use to define objects within an analytic workspace. Other OLAP DML commands are data manipulation commands. Some commands are recognized by Oracle OLAP as events that can trigger the execution of OLAP DML programs. (See "[Trigger Programs](olap-dml-programs.md)" for more information.) Additionally, you can augment the functionality of the OLAP DML by writing an OLAP DML program for use as a command.

The built-in OLAP DML commands are documented as reference topics in Chapter 8, [OLAP DML Commands: A-G](olap-dml-commands-a-g.md) and [OLAP DML Commands: H-Z](olap-dml-commands-h-z.md).

#### OLAP DML Programs

Several OLAP DML programs are provided as part of the OLAP DML. Some of these programs produce reports that you can print or see online. Other programs provided as part of the OLAP DML perform standard calculations of use to programmers and database administrators. For more information on the programs delivered with the OLAP DML, see "[Programs Provided With the OLAP DML](olap-dml-programs.md)".

You can also write your own OLAP DML programs to augment the functionality of the OLAP DML as described in [OLAP DML Programs](olap-dml-programs.md).

### 1.3 How to Execute OLAP DML Statements

The simplest way to execute OLAP DML statement is by using the OLAP Worksheet. The OLAP Worksheet is delivered as part of the Analytic Workspace Manager. To open the OLAP worksheet from within the Analytic Workspace Manager:

1.  Connect to an Oracle Database instance.
2.  Select a Schema.
3.  Select Tools, then OLAP Worksheet.

You can also execute OLAP DML statements in SQL and Java:

- Using the PL/SQL `DBMS_AW` package you can execute OLAP DML statements as described in the Oracle OLAP DML Reference manual.

- Using `SPL_Executor` delivered as part of Oracle OLAP Java API you can embed OLAP DML statements within a Java program.

  **See Also:**

  Oracle OLAP Java API Reference

### 1.4 Introduction to Analytic Workspaces

Conceptually, an analytic workspace is that portion of Oracle Database that is used by Oracle OLAP to perform OLAP analysis. Physically, an analytic workspace is stored in the database as LOBs in a table named `AW$``workspacename`.

An analytic workspace also contains the following types of objects and the OLAP DML definitions for these objects:

- Multidimensional data objects that contain the data to analyze and the results of the analysis.

- Calculation objects (that is, formulas, models, aggregations, and allocations) that contain OLAP DML statements that specify the analysis.

- OLAP DML programs that perform complex analysis.

**See Also:**

"Introduction to Analytic Workspace Data Objects", [Formulas, Models, Aggregations, and Allocations](formulas-models-aggregations-and-allocations.md) and [OLAP DML Programs](olap-dml-programs.md)

#### 1.4.1 Privileges Needed to Create and Delete Analytic Workspaces

Because an analytic workspace is physically stored as a table in an Oracle Database instance, you need SQL GRANT privileges to work with an analytic workspace. The privileges you need vary depending on whether the analytic workspace is in a schema that you own or in a schema that you do not own:

- When you are the owner of the schema, you only need SQL GRANT privileges when you want to create an analytic workspace or attach an analytic workspace. The privileges you must be granted to perform these tasks and the OLAP DML commands that relate to these tasks are outlined in the following table.

  | Task                               | OLAP DML Command                                        | SQL GRANT Privileges Needed |
  |:-----------------------------------|:--------------------------------------------------------|:----------------------------|
  | Create an analytic workspace       | [AW CREATE](olap-dml-commands-a-g.md)                   | CREATE TABLE                |
  | Attach an analytic workspace AS OF | [AW ATTACH](olap-dml-commands-a-g.md) with ASOF keyword | FLASHBACK TABLE             |

- When you are not the owner of the schema, you need SQL GRANT privileges to create an analytic workspace, to attach an analytic workspace in ASOF mode, to drop an analytic workspace, and to truncate an analytic workspace as shown in the following table.

  | Task                               | OLAP DML Command                                        | SQL GRANT Privileges Needed                          |
  |:-----------------------------------|:--------------------------------------------------------|:-----------------------------------------------------|
  | Create an analytic workspace       | [AW CREATE](olap-dml-commands-a-g.md)                   | CREATE ANY TABLE, SELECT ANY TABLE, UPDATE ANY TABLE |
  | Attach an analytic workspace AS OF | [AW ATTACH](olap-dml-commands-a-g.md) with ASOF keyword | FLASHBACK ANY TABLE                                  |
  | Delete an analytic workspace       | [AW DELETE](olap-dml-commands-a-g.md)                   | DROP ANY TABLE                                       |
  | Truncate an analytic workspace     | [AW TRUNCATE](olap-dml-commands-a-g.md)                 | TRUNCATE ANY TABLE                                   |

Note that Oracle Database does not turn on roles when you run a named PL/SQL procedure. In this case, the you must have the CREATE TABLE privilege directly.

#### 1.4.2 Defining a New Analytic Workspace

You can use the OLAP DML to create analytic workspaces. To create an analytic workspace, issue an AW command with the CREATE keyword, followed by an UPDATE statement and a COMMIT statement.

#### 1.4.3 Working with Previously-Defined Analytic Workspaces

Before you can work with a previously-defined analytic workspace, you must first attach the analytic workspace by issuing an AW ATTACH statement. You can attach an analytic workspace in any of the following attachment modes:

- Read-only: Users can make private changes to the data in the workspace to perform what-if analysis but cannot commit any of these changes. Any number of users can be attached in Read Only mode.

- Read/write access mode: Only one user can have an analytic workspace open in read/write at a time. The user has to commit either all or none of the changes made to the workspace.

- Read/write exclusive access mode: The read/write exclusive attach mode is not compatible with any other access modes. A user cannot attach an analytic workspace in read/write exclusive mode when another user has it attached in any mode. Only one user can have an analytic workspace open in read/write exclusive at a time. The user has to commit either all or none of the changes made to the workspace.

- Multiwriter access mode: An analytic workspace that is attached in multiwriter mode can be accessed simultaneously by several sessions. In multiwriter mode, users can simultaneously modify the same analytic workspace in a controlled manner by specifying the attachment mode (read-only or read/write) for individual variables, relations, valuesets, and dimensions.

For more information on the various attachment modes, see the syntax and notes for the [AW ATTACH](olap-dml-commands-a-g.md) statement.

#### 1.4.4 Viewing Information About an Analytic Workspace

The following table lists the OLAP DML statements that you can use to view information about an analytic workspace

Table 1-1 Statements for Viewing Information About an Analytic Workspace

| Statement                                      | Description                                                                                                                      |
|:-----------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| [AW function](olap-dml-functions-a-k.md)       | Returns information about currently attached workspaces.                                                                         |
| [AWDESCRIBE](olap-dml-commands-a-g.md) program | Sends information about the current analytic workspace to the current outfile.                                                   |
| [EXISTS](olap-dml-functions-a-k.md) function   | Returns a value that indicates whether an object is defined in any attached workspace.                                           |
| [LISTBY](olap-dml-commands-h-z.md) program     | Lists all objects in an analytic workspace that are dimensioned by or related to one or more specified dimensions or composites. |
| [LISTNAMES](olap-dml-commands-h-z.md) program  | Lists the names of the objects in an analytic workspace.                                                                         |
| [OBJ](olap-dml-functions-l-z.md) function      | Returns information about an analytic workspace object.                                                                          |
| [OBJLIST](olap-dml-functions-l-z.md) function  | Lists the objects that are in one or more workspaces that you specify.                                                           |
| [DESCRIBE](olap-dml-commands-a-g.md) command   | Lists the simple definition of one or more workspace objects.                                                                    |
| [FULLDSC](olap-dml-commands-a-g.md) program    | Lists the complete definition of one or more workspace objects, including the properties and triggers of the object(s).          |

### 1.5 Introduction to Analytic Workspace Data Objects

A relational database typically stores data values in tables that represent third normal form data. In this type of implementation, the values of key columns of a relational database table are unique values of a single level of data. For example, at one level in the relational database you might have a table with a key column named City that contains the names of cities and at the next highest level in the database a table with a key column named state that contains the names of states, and so on and so on.

In an analytic workspace the objects that hold the data to analyze are arrays called variables. The keys into variables are stored in other objects which act as the dimensions of the variables. To support performant OLAP analysis, values from multiple levels are stored within a single dimension called a hierarchical dimension. For example, an analytic workspace might have a hierarchical dimension named geog that had as values the names of both cities and states.

The objects that store values that relate values of two or more dimensions are called relations. Thus the one-to-many relationship between values of different levels in a hierarchical dimension are stored in an analytic workspace. For example, the relationship between the city and state values in a hierarchical geog dimension would be stored in an analytic workspace relation typically called a parentrel relation. (See "Parentrel Relation" for more information.)

Additional analytic workspace objects are typically defined to keep additional information about the hierarchical dimension. Several important OLAP DML commands and functions (such as the LIMIT command) presume the existences of these objects in your analytic workspace as the name of these objects is one argument in the syntax of the statement.

The data objects that you define using the OLAP DML are multidimensional objects that are stored in an analytic workspace. When you use OLAP DML statements to perform operations against these multidimensional data objects, those operations apply all at once to entire set of values contained by these objects.

**See Also:**

"Types of Analytic Workspace Data Objects" and"Objects that Support the Use of Hierarchies".

#### 1.5.1 Types of Analytic Workspace Data Objects

The OLAP DML supports the use of the following types of analytic workspace data objects:

- Variables
- Simple Dimensions
- Concat Dimensions
- Composites
- Partition Templates
- Alias Dimensions
- Relations
- Valueset and Surrogate Objects

**Tip:**

You can use the [OBJORG](olap-dml-functions-l-z.md) function to specify analytic workspace objects that underlie cubes and cube dimensions.

##### 1.5.1.1 Variables

The most important data object in an analytic workspace is the variable. A variable is an object that stores data. All of the data in a variable must have the same data type. Typically, you use variables to contain data values that quantify a particular aspect of your business For example, your business might have several categories of transactions (measured in dollars, units, percentages, and so on) and each category is stored in its own variable. For example, you might record sales data in dollars (a sales variable) and units (a units variable).

Because the OLAP DML is a multidimensional programming language, variables are multidimensional and correspond to what other OLAP languages sometimes call measures. Conceptually, you can think of a variable with two dimensions as a table, a variable with three dimensions as a cube, and so on. Physically, variables are stored as multidimensional arrays with the actual structure of the arrays determined by the object by which the variable is dimensioned.

The scope and permanence of a variable can vary. A permanent variable is a variable for which both the variable values and definitions are stored in an analytic workspace. Temporary variables have values only during the current session. When you update and commit the analytic workspace, only the definitions of temporary variables are saved. When you exit from the analytic workspace, the data values are discarded. You can also define variables in programs.

You can define scalar variables in programs, but most variables that you define using the OLAP DML are dimensioned variables. Dimensioned variables are arrays that hold multiple values. The indexes or dimensions of the variable provide the organization for the variable. The values of the dimension are similar to keys in a relational table, in that they uniquely identify a data value. For example, if you have a sales variable that is dimensioned by time, geography, and product dimensions, then each combination of the values of time, geography, and product identifies a value in sales. (Note that the indexes of variables are not actually the values of the dimension, but, instead, are the INTEGER positions of the values in the dimension.)

Variables can be dimensioned by either flat or hierarchical dimensions. A flat dimension exists when the values within a dimension are all at the same level; no value is the child or parent of another value. A hierarchical dimension exists when the values with a single dimension are in a one-to-many (parent-to-child) relationship with each other.

A hierarchical dimension is a means of organizing and structuring this type of data within a single dimension. You can then use it to dimension a variable that contains data for all the levels. Some dimensions have multiple hierarchies. You specify the parent-to-child relationships of the dimension values by creating a self-relation.You use a hierarchical dimension to define a variable that contains data of varying levels of aggregation within a single variable. Storing all of these values in a single variable affords a quicker response time for users who want to view the data, particularly when the variable is large.

Frequently, the cells in the variable that correspond to upper level values in the hierarchical dimension contain the sum or total of the values in the cells of the variable that correspond to the lower level dimension values. For example, in a sales variable that is defined with a hierarchical dimension representing time, the cells of the variable for each quarter might represent the total sales for the months in the quarter.

After you have defined a variable with hierarchical dimensions, you can add variable data to the lowest level of the hierarchy, and then calculate or aggregate the values for the higher levels of the hierarchy. Conversely, you can distribute or allocate data from higher levels to lower levels of the hierarchy.

**See:**

[DEFINE VARIABLE](olap-dml-commands-a-g.md)

##### 1.5.1.2 Objects that Can Dimension Variables

How variable and relation data is actually structured and stored is dependent on what type of object you use to dimension the variable or relation and the order in which those objects appear in the definition of the variable or relation. Variables can be dimensioned by simple dimensions, concat dimensions, composites, partition templates, and alias dimensions. The object by which you choose to dimension a variable determines how the data of the variable is stored.

**See Also:**

"Objects that Support the Use of Hierarchies"

##### Simple Dimensions

The members of a simple dimension are data values that all have the same data type. When a variable is dimensioned by a simple dimension, there is one cell in the variable for every member of the dimension. When there is a dimension member for which the variable has no data, Oracle OLAP stores an NA value in the variable for that empty value. If storing such NA values would result in a full page of NA values, then Oracle OLAP does not actually store the NA values.

**See:**

[DEFINE DIMENSION (simple)](olap-dml-commands-a-g.md)

##### Concat Dimensions

You define concat dimensions over previously-defined simple dimensions or conjoint dimensions. Consequently, the base dimensions of a concat dimension can be of different data types. You can represent a hierarchy with a concat dimension that has two or more simple flat dimensions among its base dimensions. You can use concat dimensions to easily map dimensions in an analytic workspace to columns in relational tables and thereby promote more efficient loading of data from the relational structures into the analytic workspace structures.

**See:**

[DEFINE DIMENSION CONCAT](olap-dml-commands-a-g.md)

##### Composites

You define composites over previously-defined dimensions. Conceptually, you can think of a composite consisting of two structures:

- The composite object itself. The composite contains the dimension-value combinations (that is, the composite tuples) that Oracle OLAP uses to determine the structure of any variables that are dimensioned by the composite.

- An index between the composite values and its base dimension values.

For a variable that is dimensioned by a composite, Oracle OLAP does not create a cell for every value in the base dimensions as it would if the variable was dimensioned by a simple dimension. Instead, it creates array elements (that is, variable cells) only for those dimension values that are stored in the tuples of the composite. Data for the variable is stored in order, cell by cell, for each tuple in the composite. From the perspective of data storage, each combination of base dimension values in a composite is treated like the value of a regular dimension. Consequently, when you define a variable with one regular dimension and one composite, the data for the variable is stored as though it was a two-dimensional variable. Using composites to reduce the number of elements created for a variable results in more efficient data storage.

**See:**

[DEFINE COMPOSITE](olap-dml-commands-a-g.md)

##### Partition Templates

You define a partition template over previously-defined dimensions or composites. A partition template is a specification for the partitions of a partitioned variable. A partitioned variable is stored as multiple rows in the relational table of LOBs that is the analytic workspace—each partition is a row in the table.

**See:**

[DEFINE PARTITION TEMPLATE](olap-dml-commands-a-g.md)

##### Alias Dimensions

An alias dimension is an alias for a simple dimension. An alias dimension has the same type and values as its base dimension. Typically, you define an alias dimension when you want to dimension a variable by the same dimension twice.

**See:**

[DEFINE DIMENSION ALIASOF](olap-dml-commands-a-g.md)

##### 1.5.1.3 Relations

A relation is an object that establishes a correspondence between the values of a given dimension and the values of that same dimension or other dimensions in the analytic workspace. Relations are dimensioned arrays. Each cell in a relation holds the index of the value of a dimension. You can define relations between two or more dimensions, multiple relations between a set of dimensions, or a dimension with itself (a self-relation).

Most frequently, a relation is a self-relation for a hierarchical dimension. By creating a relation between values in a dimension that participate in a one-to-many (parent-to-child) relationship, you can organize your data by the child values and view aggregates of data by the parent values. For example, you can create a `geog.parent` relation for a `geography` dimension to define the relationships between the city and state values in `geography`. In this way you can organize the data by city and view the aggregates of data by state.

**See Also:**

[DEFINE RELATION](olap-dml-commands-a-g.md)

##### 1.5.1.4 Valueset and Surrogate Objects

The OLAP DML provides the following special data objects that you use not when you are defining your variables, but instead, when you are querying them,

##### Valueset Objects

A valueset is a list of dimension values for one or more previously-defined dimensions. You use a valueset to save dimension status lists across sessions.

**See:**

[DEFINE VALUESET](olap-dml-commands-a-g.md)

##### Surrogates

A dimension surrogate is an alternative set of values for a previously-defined dimension. You cannot dimension a variable by a surrogate, but you can use a surrogate rather than a dimension in a model, in a LIMIT command, in a qualified data reference, or in data loading with statements such as FILEREAD, FILEVIEW, SQL FETCH, and SQL IMPORT.

**See:**

[DEFINE SURROGATE](olap-dml-commands-a-g.md)

#### 1.5.2 Objects that Support the Use of Hierarchies

Typically, variables are dimensioned by hierarchical objects. For example, you might have a sales variable that is dimensioned by geog, time, and product. The geog dimension might have two hierarchies (one for political divisions and another for sales regions) and each of these hierarchies could have several levels with the top level of the political geography hierarchy being All Country and the top level of the sales geography hierarchy being All Regions. Example 1-1 illustrates defining and populating this type of hierarchical geography dimension.

Typically, after you define a hierarchical dimension, you define the following objects for that dimension:

- hierlist dimension that lists the names of the hierarchies for the dimension. See "Hierlist Dimension" for more information and an example.

- parentrel relation that defines the hierarchies. A dimension is only a hierarchical dimension when it has a parentrel defined for it. See "Parentrel Relation" for more information and an example.

- levellist relation that lists the names of all of the levels of all of the hierarchies. See "Levellist Dimension" for more information and an example.

- hierlevels valueset that is the values of the levels of each hierarchy. See "Hierlevels Valueset" for more information and an example.

- inhier valueset or variable that identifies the values of each hierarchy. See "Inhier Valueset or Variable" for more information and examples.

- levelrel relation that relates each value of the hierarchical dimension to its level in the hierarchy. See "Levelrel Relation" for more information and an example.

- familyrel relation that is each hierarchical dimension value and its related values. See "Familyrel Relation" for more information and an example.

- gidrel relation that is the grouping ids of each value within each hierarchy. See "Gidrel Relation" for more information and an example.

Example 1-1 Defining and Populating a Hierarchical Dimension Named geog

    DEFINE geog DIMENSION TEXT
    LD A dimension with two hierarchies for geography
    "Populate the dimension with City, State, Region, and Country values
    MAINTAIN geog ADD 'Boston' 'Springfield' 'Hartford' 'Mansfield' 'Montreal' 'Walla Walla' 'Portland' 'Oakland' 'San Diego' 'MA' 'CT' 'WA' 'CA' 'Quebec' 'East' 'West' 'All Regions' 'USA' 'Canada' 'All Country'

    "Display the values in geog

    REPORT geog

    GEOG
    --------------
    Boston
    Springfield
    Hartford
    Mansfield
    Montreal
    Walla Walla
    Portland
    Oakland
    San Diego
    MA
    CT
    WA
    CA
    Quebec
    East
    West
    All Regions
    USA
    Canada
    All Country


##### 1.5.2.1 Hierlist Dimension

A hierlist dimension is a `TEXT` dimension in the analytic workspace that has as values the names of the hierarchies of a hierarchical dimension. For example, if the company has a different calendar and fiscal year, the time dimension for that company would have two hierarchies: one for calendar and another for year. The hierlist dimension that supported that time hierarchy would have two values: Calendar and Fiscal.

For consistency's sake, analytic workspaces include a hierlist dimension for every hierarchical dimension -- even when that hierarchical dimension has only one hierarchy.

Example 1-2 Defining and Populating a hierlist Dimension Named geog_hierlist

This example illustrates defining and populating this type of dimension.

    DEFINE geog_hierlist DIMENSION TEXT
    LD List of Hierarchies for geog dimension
    "Populate the geog_hierlist dimension
    MAINTAIN geog_hierlist ADD 'Political_Geog' 'Sales_Geog'
    "Display the values of the geog_hierlist dimension
    REPORT geog_hierlist

    GEOG_HIERLIST
    --------------
    Political_Geog
    Sales_Geog

##### 1.5.2.2 Parentrel Relation

A parentrel relation is a relation between the hierarchical dimension and itself (a self-relation) and the hierlist dimension. It identifies the parent of each dimension member within a hierarchy.

Example 1-3 Defining and Populating a parentrel Relation named geog_parentrel

This example illustrates defining and populating this type of relation.

    "Define the relation
    DEFINE geog_parentrel RELATION geog <geog geog_hierlist>
    LD Self-relation for geog showing parents of each value
    "Populate each cell in the relation "with the parent of the geog value
    "This example using assignment statement with QDRs to do that
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Boston') = 'MA'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Hartford') = 'CT'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Springfield') = 'MA'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Mansfield') = 'CT'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog  'Montreal') = 'Quebec'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Walla Walla') = 'WA'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Portland') = 'WA'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Oakland') = 'CA'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'San Diego') = 'CA'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'CT') = 'East'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'MA') = 'East'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'WA') = 'West'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'CA') = 'West'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'Quebec') = 'East'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'East') = 'All Regions'
    geog_parentrel (geog_hierlist 'Sales_Geog' geog 'West') = 'All Regions'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Boston') = 'MA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Hartford') = 'CT'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Springfield') = 'MA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Mansfield') = 'CT'
    geog_parentrel (geog_hierlist 'Political_Geog' geog  'Montreal') = 'Quebec'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Walla Walla') = 'WA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Portland') = 'WA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Oakland') = 'CA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'San Diego') = 'CA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'CT') = 'USA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'MA') = 'USA'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'WA') = 'USA'
    geog_parentrel (geog_hierlist 'Political_Geog'  geog 'CA') = 'USA'
    geog_parentrel (geog_hierlist 'Political_Geog'  geog 'Quebec') = 'Canada'
    geog_parentrel (geog_hierlist 'Political_Geog'  geog 'USA') = 'All Country'
    geog_parentrel (geog_hierlist 'Political_Geog' geog 'Canada') = 'All Country'

    "Display the values of geog_parentrel
    REPORT DOWN geog W 20 geog_parentrel
                   -------------GEOG_PARENTREL--------------
                   --------------GEOG_HIERLIST--------------
    GEOG              Political_Geog         Sales_Geog
    -------------- -------------------- --------------------
    Boston         MA                   MA
    Springfield    MA                   MA
    Hartford       CT                   CT
    Mansfield      CT                   CT
    Montreal       Quebec               Quebec
    Walla Walla    WA                   WA
    Portland       WA                   WA
    Oakland        CA                   CA
    San Diego      CA                   CA
    MA             USA                  East
    CT             USA                  East
    WA             USA                  West
    CA             USA                  West
    Quebec         Canada               East
    East           NA                   All Regions
    West           NA                   All Regions
    All Regions    NA                   NA
    USA            All Country          NA
    Canada         All Country          NA
    All Country    NA                   NA


##### 1.5.2.3 Levellist Dimension

A levellist dimension is a TEXT dimension that has as values the names all of the levels of the hierarchies of a hierarchical dimension.

Example 1-4 Defining and Populating a levellist Dimension Named geog_levellist

This example illustrates defining and populating this type of dimension.

    DEFINE geog_levellist DIMENSION TEXT
    LD List of levels used by hierarchies of the geog dimension
    "Populate the geog_levellist dimension with the names of the levels of both the
    "Political_Geog and Sales_Geog hierarchies
    MAINTAIN geog_levellist ADD 'All Country' 'Country' 'All Regions' 'Region' MAINTAIN geog_levellist ADD 'State-Prov' 'City'
    "Display the values of the geog_levellist dimension

    REPORT geog_levellist

    GEOG_LEVELLIST
    --------------
    All Country
    Country
    All Regions
    Region
    State-Prov
    City

##### 1.5.2.4 Hierlevels Valueset

A hierlevels valueset is those values of the hierlevels dimension (typically ordered from bottom to top) that are included in each hierarchy of the hierarchical dimension.

Example 1-5 Defining and Populating a hierlevels Valueset named geog_hierlevels

This example illustrates defining and populating this type of valueset.

    DEFINE geog_hierlevels VALUESET geog_levellist <geog_hierlist>
    "Using LIMIT populate the valueset with the appropriate values for each hierarchy
    LIMIT geog_hierlevels TO ALL

    LIMIT geog_hierlevels (geog_hierlist 'Political_Geog') TO 'City' 'State-Prov' 'Country' 'All Country'

    LIMIT geog_hierlevels (geog_hierlist 'Sales_Geog') TO 'City' 'State-Prov' 'Region' 'All Regions'

    "Display the values in the valueset
    REPORT W 22 geog_hierlevels

    GEOG_HIERLIST     GEOG_HIERLEVELS
    -------------- ----------------------
    Political_Geog City
                   State-Prov
                   Country
                   All Country
    Sales_Geog     City
                   State-Prov
                   Region
                   All Regions


##### 1.5.2.5 Inhier Valueset or Variable

An inhier valueset is those values of the inhier dimension that are in each hierarchy.

An inhier variable is a BOOLEAN variable that is dimensioned by the hierarchical dimension and the hierlist dimension. For each hierarchy, it has a TRUE value for each dimension value that is in that hierarchy.

Example 1-6 Defining and Populating an inhier Valueset Named geog_inhier

This example illustrates defining and populating inhier valueset.

    "Define the valueset
    DEFINE geog_inhier VALUESET geog <geog_hierlist>
    "Using LIMIT commands, populate the valueset
    LIMIT geog_inhier (geog_hierlist 'Political_Geog') REMOVE 'East' 'West' 'All Regions'
    LIMIT geog_inhier (geog_hierlist 'Sales_Geog') REMOVE 'Canada' 'USA' 'All Country'
    "Display the values in the valueset

    REPORT W 20 geog_inhier

    GEOG_HIERLIST      GEOG_INHIER
    -------------- --------------------
    Political_Geog Boston
                   Springfield
                   Hartford
                   Mansfield
                   Montreal
                   Walla Walla
                   Portland
                   Oakland
                   San Diego
                   MA
                   CT
                   WA
                   CA
                   Quebec
                   USA
                   Canada
                   All Country
    Sales_Geog     Boston
                   Springfield
                   Hartford
                   Mansfield
                   Montreal
                   Walla Walla
                   Portland
                   Oakland
                   San Diego
                   MA
                   CT
                   WA
                   CA
                   Quebec
                   East
                   West
                   All Regions


Example 1-7 Defining and Populating an inhier Variable Named geog_inhiervar

This example illustrates defining and populating an inhier variable valueset.

    DEFINE geog_inhiervar VARIABLE BOOLEAN <geog geog_hierlist>

    "Using LIMIT commands and assignment statements, populate
    " the variable
    LIMIT geog_hierlist TO ALL
    LIMIT geog_hierlist TO 'Political_Geog'
    LIMIT geog TO 'East' 'West' 'All Regions'
    geog_inhiervar = FALSE
    LIMIT geog COMPLEMENT
    geog_inhiervar = TRUE
    LIMIT geog_hierlist TO ALL
    LIMIT geog_hierlist TO 'Sales_Geog'
    LIMIT geog TO ALL
    LIMIT geog TO 'Canada' 'USA' 'All Country'
    geog_inhiervar = FALSE
    LIMIT geog COMPLEMENT
    geog_inhiervar = TRUE
    LIMIT geog TO ALL
    LIMIT geog_hierlist TO ALL

    "Display the values of the variable
    REPORT DOWN geog geog_inhiervar

                   ---GEOG_INHIERVAR----
                   ----GEOG_HIERLIST----
                   Political_
    GEOG              Geog    Sales_Geog
    -------------- ---------- ----------
    Boston                yes        yes
    Springfield           yes        yes
    Hartford              yes        yes
    Mansfield             yes        yes
    Montreal              yes        yes
    Walla Walla           yes        yes
    Portland              yes        yes
    Oakland               yes        yes
    San Diego             yes        yes
    MA                    yes        yes
    CT                    yes        yes
    WA                    yes        yes
    CA                    yes        yes
    Quebec                yes        yes
    East                   no        yes
    West                   no        yes
    All Regions            no        yes
    USA                   yes         no
    Canada                yes         no
    All Country           yes         no

##### 1.5.2.6 Levelrel Relation

A levelrel relation is a relation between the levellist and hierlist dimensions that records the level for each member of the hierarchical dimension

Example 1-8 Defining and Populating a levelrel Relation named geog_levelrel

This example illustrates defining and populating this type of relation.

    "Define the relation
    DEFINE geog_levelrel RELATION geog_levellist <geog geog_hierlist>
    LD Level of each dimension member for geog

    "Populate the relation
    "This example uses assignment statements with QDRs to populate
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Boston') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Hartford') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Springfield') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Mansfield') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog  'Montreal') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Walla Walla') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Portland') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Oakland') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'San Diego') = 'City'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'CT') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'MA') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'WA') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'CA') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'Quebec') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'East') = 'Region'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'West') = 'Region'
    geog_levelrel (geog_hierlist 'Sales_Geog' geog 'All Regions') = 'All Regions'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Boston') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Hartford') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Springfield') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Mansfield') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog  'Montreal') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Walla Walla') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Portland') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Oakland') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'San Diego') = 'City'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'CT') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'MA') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'WA') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Political_Geog'   geog 'CA') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Political_Geog'  geog 'Quebec') = 'State-Prov'
    geog_levelrel (geog_hierlist 'Political_Geog'  geog 'USA') = 'Country'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'Canada') = 'Country'
    geog_levelrel (geog_hierlist 'Political_Geog' geog 'All Country') = 'All Country'

    "Display the values
    REPORT DOWN geog W 20 geog_levelrel

                   --------------GEOG_LEVELREL--------------
                   --------------GEOG_HIERLIST--------------
    GEOG              Political_Geog         Sales_Geog
    -------------- -------------------- --------------------
    Boston         City                 City
    Springfield    City                 City
    Hartford       City                 City
    Mansfield      City                 City
    Montreal       City                 City
    Walla Walla    City                 City
    Portland       City                 City
    Oakland        City                 City
    San Diego      City                 City
    MA             State-Prov           State-Prov
    CT             State-Prov           State-Prov
    WA             State-Prov           State-Prov
    CA             State-Prov           State-Prov
    Quebec         State-Prov           State-Prov
    East           NA                   Region
    West           NA                   Region
    All Regions    NA                   All Regions
    USA            Country              NA
    Canada         Country              NA
    All Country    All Country          NA

##### 1.5.2.7 Familyrel Relation

The familyrel relation is a relation between the hierarchical dimension and the levellist and hierlist dimensions that provides the full parentage of each dimension member in the hierarchy.

Example 1-9 Defining and Populating a familyrel Relation named geog_familyrel

This example illustrates defining and populating this type of relation.

    "Define the relation
    DEFINE geog_familyrel RELATION geog <geog geog_levellist geog_hierlist>
    LD FEATURES Family/Ancestry structure for the geog dimension

    "Populate the relation using the HIERHEIGHT command
    HIERHEIGHT geog_parentrel INTO geog_familyrel USING geog_levelrel

    "Display the values of the familyrel relation
    "First the values for the Political_Geog hierarchy are displayed
    "Then the values for the Sales_Geog hierarchy
    REPORT DOWN geog W 12 geog_familyrel

    GEOG_HIERLIST: Political_Geog
                   -------------------------------GEOG_FAMILYREL--------------------------------
                   -------------------------------GEOG_LEVELLIST--------------------------------
    GEOG            All Country  Country    All Regions     Region     State-Prov      City
    -------------- ------------ ------------ ------------ ------------ ------------ ------------
    Boston         All Country  USA          NA           NA           MA           Boston
    Springfield    All Country  USA          NA           NA           MA           Springfield
    Hartford       All Country  USA          NA           NA           CT           Hartford
    Mansfield      All Country  USA          NA           NA           CT           Mansfield
    Montreal       All Country  Canada       NA           NA           Quebec       Montreal
    Walla Walla    All Country  USA          NA           NA           WA           Walla Walla
    Portland       All Country  USA          NA           NA           WA           Portland
    Oakland        All Country  USA          NA           NA           CA           Oakland
    San Diego      All Country  USA          NA           NA           CA           San Diego
    MA             All Country  USA          NA           NA           MA           NA
    CT             All Country  USA          NA           NA           CT           NA
    WA             All Country  USA          NA           NA           WA           NA
    CA             All Country  USA          NA           NA           CA           NA
    Quebec         All          Canada       NA           NA           Quebec       NA
                   Countries
    East           NA           NA           NA           NA           NA           NA
    West           NA           NA           NA           NA           NA           NA
    All Regions    NA           NA           NA           NA           NA           NA
    USA            All Country  USA          NA           NA           NA           NA
    Canada         All Country  Canada       NA           NA           NA           NA
    All Country    All Country  NA           NA           NA           NA           NA

    GEOG_HIERLIST: Sales_Geog
                   -------------------------------GEOG_FAMILYREL--------------------------------
                   -------------------------------GEOG_LEVELLIST--------------------------------
    GEOG            All Country Country    All Regions     Region     State-Prov      City
    -------------- ------------ ------------ ------------ ------------ ------------ ------------
    Boston         NA           NA           All Regions  East         MA           Boston
    Springfield    NA           NA           All Regions  East         MA           Springfield
    Hartford       NA           NA           All Regions  East         CT           Hartford
    Mansfield      NA           NA           All Regions  East         CT           Mansfield
    Montreal       NA           NA           All Regions  East         Quebec       Montreal
    Walla Walla    NA           NA           All Regions  West         WA           Walla Walla
    Portland       NA           NA           All Regions  West         WA           Portland
    Oakland        NA           NA           All Regions  West         CA           Oakland
    San Diego      NA           NA           All Regions  West         CA           San Diego
    MA             NA           NA           All Regions  East         MA           NA
    CT             NA           NA           All Regions  East         CT           NA
    WA             NA           NA           All Regions  West         WA           NA
    CA             NA           NA           All Regions  West         CA           NA
    Quebec         NA           NA           All Regions  East         Quebec       NA
    East           NA           NA           All Regions  East         NA           NA
    West           NA           NA           All Regions  West         NA           NA
    All Regions    NA           NA           All Regions  NA           NA           NA
    USA            NA           NA           NA           NA           NA           NA
    Canada         NA           NA           NA           NA           NA           NA
    All Country    NA           NA           NA           NA           NA           NA


##### 1.5.2.8 Gidrel Relation

A gidrel relation is a relation between a NUMBER dimension, the hierarchical dimension, and the hierlist dimension that contains the grouping ID of each dimension member in each hierarchy of the hierarchical dimension. It also has a \$GID_DEPTH property that identifies the depth within a hierarchy of each dimension member.

Example 1-10 Defining and Populating a gidrel Relation named geog_gidrel

This example illustrates defining and populating this type of relation.

    "Create a dimension that has values that are numbers
    DEFINE gid_dimension DIMENSION NUMBER (38,0)"Add values to that dimension
    "This example uses MAINTAIN ADD to add a few numbers
    MAINTAIN gid_dimension ADD 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26

    "Define the gidrel relation
    DEFINE geog_gidrel RELATION gid_dimension <geog geog_hierlist>
    "Display the complete definition of the geog_gidrel relation
    "Note that it has no properties
    DEFINE GEOG_GIDREL RELATION GID_DIMENSION <GEOG GEOG_HIERLIST>
    "Populate the gidrel relation using the GROUPINGID command
    GROUPINGID geog_parentrel INTO geog_gidrel USING geog_levelrel INHIERARCHY geog_inhier
    "Display the values of the geog_gidrel relation

    REPORT down geog w 20 geog_gidrel

                   ---------------GEOG_GIDREL---------------
                   --------------GEOG_HIERLIST--------------
    GEOG              Political_Geog         Sales_Geog
    -------------- -------------------- --------------------
    Boston         0                    0
    Springfield    0                    0
    Hartford       0                    0
    Mansfield      0                    0
    Montreal       0                    0
    Walla Walla    0                    0
    Portland       0                    0
    Oakland        0                    0
    San Diego      0                    0
    MA             1                    1
    CT             1                    1
    WA             1                    1
    CA             1                    1
    Quebec         1                    1
    East           NA                   3
    West           NA                   3
    All Regions    NA                   7
    USA            3                    NA
    Canada         3                    NA
    All Country    7                    NA

    "Display the complete definition of the geog_gidrel relation
    "Note that it now has a $GID_DEPTH property
    DEFINE GEOG_GIDREL RELATION GID_DIMENSION <GEOG GEOG_HIERLIST>
    PROPERTY '$GID_DEPTH' 4

### 1.6 OLAP DML Statements Apply to All of the Values of a Data Object

The OLAP DML is a multidimensional language. Consequently, operations in the OLAP DML apply all at once to an entire set of values. Again, conceptually, you can think of these operations as applying to the values in all of the cells in a variable; or, physically, you can think of these operations as applying to all of the elements in the array that is the variable. Consequently, if you use the OLAP DML assignment statement (that is, [SET](olap-dml-commands-h-z.md) or =), then you do not need to code explicit loops to assign values to all of the elements in a variable. Instead, when you issue a statement against an object that has one or more dimensions, the statement loops over the values in status for each dimension of the object and performs the requested operation.

Assume, for example, that there is a dimension named `prodid` that has three values, `Prod01`, `Prod02`, and `Prod03`, and you have a variable named `quantity `that is dimensioned by prodid. As the following code snippet illustrates, if `Prod01`, `Prod02`, and `Prod03` are all in status, when you assign the value `3` to quantity, Oracle OLAP assigns the value `3` to all of the elements in quantity.

    quantity = 3
    REPORT quantity

    PRODID          QUANTITY
    -------------- ----------
    PROD01             3.00
    PROD02             3.00
    PROD03             3.00


Other OLAP DML statements (for example, REPORT, ROW, and FOR) also loop through all of the in status elements of a dimensioned object when they execute.

#### 1.6.1 Changing the Default Looping Behavior of Statements

By default, statements loop through the values of a dimensioned object using the order in which the dimensions of the object are listed in the definition of the object. Also, when a variable is dimensioned by a composite, most looping statements loop through the variable as though it was not dimensioned by a composite, but was, instead, dimensioned by the base dimensions of the composite.

The OLAP DML provides ways for you to change the default looping behavior or to explicitly request looping:

- ACROSS phrase—Some looping command (such as assignment statements that you use to assign values) have an ACROSS phrase that you can use to specify non-default looping behavior. For detailed documentation of the ACROSS phrase, see the [SET](olap-dml-commands-h-z.md) (=) command.

- ACROSS command—When an OLAP DML statement is not a looping statement or does not include an ACROSS phrase, you can request looping behavior by coding the DML statement as an argument of the [ACROSS](olap-dml-commands-a-g.md) command.

### 1.7 How to Specify the Set of Data that OLAP DML Operations Work Against

For each defined dimension, Oracle OLAP uses lists called status lists to keep track of the dimension values that are accessible to the user.

#### 1.7.1 About Status Lists

Oracle OLAP uses two kinds of status lists: default status lists and current status lists. The values in the current status lists of the dimensions in an analytic workspace determine the set of data that is available to the OLAP DML at any given moment in time.

##### 1.7.1.1 Default Status Lists

The default status list of a dimension is the list of all of the values of the dimension that have read permission, in the order in which the values are stored, when you first attach an analytic workspace. You can change the default status list of a dimension in the following ways:

- You can add, delete, move, merge, and rename values in a dimension by using the MAINTAIN command or adding dimension values in other ways (for example, using a SQL FETCH statement).

- You can change the read permission of values that are associated with a dimension by using a PERMIT or PERMITRESET statement.

##### 1.7.1.2 Current Status Lists

The current status list of a dimension is an ordered list of currently accessible values for the dimension. Values that are in the current status list of a dimension are said to be "in status." When you first attach an analytic workspace, the default and current status lists of each dimension are the same.

The current status list of a dimension determines the accessibility of the data in the analytic workspace:

- For dimensions, only those dimension values that are in the current status list are visible and accessible to OLAP DML expressions.

- For dimensioned objects like variables, only those data values that are indexed by dimension values in the current status list are visible and accessible to OLAP DML expressions. As a loop is performed through a dimensioned object, the order of the dimension values in the current status list is used to determine the order in which the values of the object are accessed.

Note that a dimension and any surrogate for that dimension share the same status. Setting the status of a dimension surrogate sets the status of its dimension and setting the status of a dimension sets the status of any dimension surrogates for it. Throughout this documentation, references to dimensions apply equally to dimension surrogates, except where noted. Additionally, composites are not dimensions, and therefore they do not have any independent status. The values of a composite that are in status are determined by the status of the base dimensions of the composite.

**Note:**

Whether or not a dimension value is in status merely restricts the OLAP DML's view of the value during a given session; it does not permanently affect the values that are stored in the analytic workspace.

#### 1.7.2 Changing the Current Status of a Dimension to Work with a Subset of Data

Because the current status list of a dimension determines the accessibility of the data in the analytic workspace, the way to work with a subset of analytic workspace data is to change the current status lists of one or more dimensions.

You change the values and the order of the values in the current status list of a dimension using the [LIMIT command](olap-dml-commands-h-z.md). The LIMIT command is a very complex OLAP DML command that lets you specify what values you want in the current status list by specifying the values explicitly or implicitly using relations. At it simplest level, [Example 10-20](olap-dml-commands-h-z.md) illustrates how you can use the LIMIT command to change the current status list of a dimension so you can work with a subset of data.

#### 1.7.3 Saving and Restoring Current Dimension Status

There are several different ways that you can save the current status of a dimension. The scope of each way is different:

- Any session—To save the current status for use in any session, create a named valueset with that status. Use a DEFINE VALUESET command to define the valueset. Use a LIMIT command to assign the values to the valueset.

- Current session—To save, access, or update the current status for use in the current session, use a named context. Use the CONTEXT command to define the context.

- Current program—To save the current status for use in the current program, then use the PUSHLEVEL and PUSH commands. You can restore the current status values using the POPLEVEL and POP commands.

#### 1.7.4 Using a Subset of Data Without Changing Status

Sometimes you want to have an individual OLAP DML statement or expression work against a subset of data without actually changing the current status list of a dimension. To support this need, some OLAP DML statements allow you to specify the name of a previously-defined valueset object instead of the name of a dimension. Additionally, on-the-fly, you can specify a data subset without changing the current status list of dimensions using one of the following:

- The [CHGDIMS](olap-dml-functions-a-k.md) function which, during the evaluation of expression, changes the dimensionality of an expression or changes the dimension status.

- The [LIMIT function](olap-dml-functions-l-z.md) which, during the evaluation of expression, returns the dimension or dimension surrogate values that result from a specified LIMIT command or a specified dimension status stack.

- Use a qualified data reference (QDR) which is a way of limiting one or more dimensions of an expression to a single value when you want to specify a single value of a data object without changing the current status.

### 1.8 Populating Multidimensional Hierarchical Data Objects

Frequently you first populate the base values of your variables from relational tables or from flat files. You then calculate other values from these base values using OLAP DML calculation objects. For example, you might define aggregation objects to aggregate the values that are higher up the hierarchy.

You can also assign values to variables, relations, and dimension surrogates using assignment statements (see [SET](olap-dml-commands-h-z.md) and [SET1](olap-dml-commands-h-z.md)) and add values to dimensions using [MAINTAIN](olap-dml-commands-h-z.md) statements.

**Tip:**

[Formulas, Models, Aggregations, and Allocations](formulas-models-aggregations-and-allocations.md)
