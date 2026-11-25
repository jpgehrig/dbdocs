This chapter provides reference topics for the second set (in alphabetical order) of the OLAP DML commands. There is one topic for each of the OLAP DML commands that begins with the letters H-Z, beginning with HEADING.

Alphabetical and categorical listings of the OLAP DML commands and reference topics for the remaining OLAP DML commands appear in [OLAP DML Commands: A-G](olap-dml-commands-a-g.md).

For other OLAP DML reference topics, see [OLAP DML Properties](olap-dml-properties.md), [OLAP DML Options](olap-dml-options.md), [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), and [OLAP DML Functions: L - Z](olap-dml-functions-l-z.md).

**Tip:**

Many OLAP DML statements can be coded as a 3-character abbreviation that consists of the first letter of the statement plus the next two consonants.

### 10.1 HEADING

The HEADING command produces titles and column headings for a report. The heading output is sent to the current outfile. The form of the HEADING command is the same as that of the ROW command. When you use HEADING, however, Oracle OLAP does not add any numeric values from the heading to column subtotals or grand totals.

Frequently, HEADING statements are used in a PAGEPRG program to produce titles or column headings on each page of a report.

**Tip:**

When you know ahead of time that you do not need the subtotaling capability of the ROW command, use the HEADING command instead of ROW to produce the lines of your report can provide a time savings, because, in this case, Oracle OLAP does not keep track of subtotals.

#### Syntax

HEADING \[attribs\] {expression1\|SKIP}, \[attribs\] {expressionN\|SKIP}

#### Parameters

attribs
The attributes that specify the format for each column. (See the ROW command for a list and detailed explanation of the available attributes.)

expression
The text to be used as a column heading. To use literal text for a column heading, enclose the text in single quotes. (See the ROW command for more information on using expressions, attributes, and ACROSS groups to produce columns.)

SKIP
Used instead of an expression to indicate that the column is to be left blank.

#### Usage Notes

The notes for the ROW command also apply to the HEADING command (except for the note on row and column arithmetic in ROW).

Creating Titles Using Heading

To create a title or subtitle in a report, use HEADING to produce a single "column" with a width equal to the setting of the LSIZE option. You can then center your text within this "column" to produce a centered title.

Maximum Heading Width

The maximum width of any line in a report, including a heading line, is 4,000 characters.

#### Examples

Example 10-1 Producing Column Headings

In a report, you want to have headings for your columns. You can use a HEADING statement such as the following in your program.

    HEADING UNDER '-' CENTER <WIDTH 15 'Product' -
       ACROSS district FIRST 3: district>

This statement produces the following result.

        Product      Atlanta     Boston    Chicago
    --------------- ---------- ---------- ----------

### 10.2 HIDE

The HIDE command hides the text of a program, so that you cannot display it using a DESCRIBE, EDIT, or OBJ statement. You can perform all other actions on the program, including executing, compiling, renaming, or exporting.

When you hide a program, you supply a seed expression, which Oracle OLAP uses to encode the program text. You can use this seed expression later using an UNHIDE statement to make the text visible.

**Note:**

This command performs simple encoding. For information on using secure encryption and other security features in Oracle, see [About Oracle Database Security](../dbseg/introduction-to-oracle-database-security.md) in Oracle Database Security Guide.

#### Syntax

HIDE prog-name seed-exp

#### Parameters

prog-name
The name of the program whose text you want to hide. Do not enclose the program name in quotes.

seed-exp
A single-line text expression to be used as a seed value when encoding of the program text. Do not specify `NA` for this value.

Keep a record of this seed expression, so that you can use it later with an UNHIDE statement. The seed expression you specify in the UNHIDE statement must be byte-for-byte the same value as you used in this HIDE statement. Also, the seed expression is case-sensitive, so record uppercase and lowercase characters carefully.

#### Usage Notes

Exporting and Importing with the Seed

When you export and import a hidden program, the text remains hidden in the analytic workspace in which it is imported. It retains the same seed expression for use with the UNHIDE command.

#### Examples

Example 10-2 Hiding Program Text

The following example hides the text of a program called `sales_rpt`.

    HIDE sales_rpt 'Crystal'

### 10.3 HIERDEPTH

For each hierarchy of relation, the HIERDEPTH command calculates the depth of that hierarchy from the top of all of the hierarchies and stores that value in a previously-defined relation sometimes called the depth relation.

#### Syntax

HIERDEPTH parent-rel \[(qdr-list)\] INTO depth-rel \[INHIERARCHY inh-valueset \]

#### Parameters

parent-rel
A child-parent self-relation for the hierarchical dimension. See "[Parentrel Relation](olap-dml-basic-concepts.md)" for more information.

qdr-list
A list of QDRs that limits the values of parentrel. Specify the QDRs as described in "[Syntax of a Qualified Data Reference](data-types-operators-and-expressions.md)". When you do not specify a value for qdrlist, HIERHEIGHT uses the values of parentrel that are in current status.

depth-rel
A previously -defined relation that the HIERDEPTH command populates when it executes. This relation can have multiple dimensions; however, it must be dimensioned by the dimensions of parentrel and one other `NUMBER` dimension that represents the depth of the hierarchical dimension.

For example, assuming that parent-rel has two dimensions, dim1 and dim2, the following lines of code define a `NUMBER` dimension named numdim with 3 values and, then, define a depth relation named depthrel which is dimensioned by dim1 and dim2 that has as its values the values of numdim.

    DEFINE numdim dimension NUMBER(3)
    DEFINE depthrel RELATION numdim <dim1 dim2>

inh-valueset
The name of a valueset object whose values are the hierarchical dimension values to be considered when creating grouping ids. Values not included in the valueset are ignored. See "[Inhier Valueset or Variable](olap-dml-basic-concepts.md)" for more information.

#### Examples

Example 10-3 Creating and Populating a Depth Relation for Hierarchies

Assume that your analytic workspace contains the `geog`, `geog_hierlist`, and `geog_parentrel` objects described in [Example 9-145](olap-dml-commands-a-g.md). You can create a depth relation for the hierarchies represented by these objects by issuing the following DML code.

    "   Define the number dimension for the depthrel
    DEFINE numdepth DIMENSION NUMBER (3)
    "   Define the depth relation
    "   Populate the depth relation
    HIERDEPTH geog_parentrel INTO depthrel
    REPORT DOWN geog depthrel

                   ------------------DEPTHREL-------------------
                   ----------------GEOG_HIERLIST----------------
    GEOG               Political_Geog           Sales_Geog
    -------------- ---------------------- ----------------------
    Boston         3                      3
    Springfield    3                      3
    Hartford       3                      3
    Mansfield      3                      3
    Montreal       3                      3
    Walla Walla    3                      3
    Portland       3                      3
    Oakland        3                      3
    San Diego      3                      3
    MA             2                      2
    CT             2                      2
    WA             2                      2
    CA             2                      2
    Quebec         2                      2
    East           0                      1
    West           0                      1
    All Regions    0                      0
    USA            1                      0
    Canada         1                      0
    All Countries  0                      0

### 10.4 HIERHEIGHT command

The HIERHEIGHT command populates a previously-defined relation with the values of a specified hierarchical dimension by level. Typically, you use the HIERHEIGHT command when you are preparing an analytic workspace for access using the `OLAP_TABLE` function.

To retrieve the value of a node (by level) for the value of a hierarchical dimension, use the [HIERHEIGHT](olap-dml-functions-a-k.md).

**See Also:**

See "[Familyrel Relation](olap-dml-basic-concepts.md)"

#### Syntax

HIERHEIGHT parentrelation \[(qdrlist)\] INTO{familyrel-        \[USING level-relation \| A \| D\] \[INHIERARCHY { inh-variable \| inh-valueset}\]

#### Parameters

parentrel
A child-parent self-relation for the hierarchical dimension. See "[Parentrel Relation](olap-dml-basic-concepts.md)" for more information.

qdrlist
A list of QDRs that limits the values of parentrel. Specify the QDRs as described in "[Syntax of a Qualified Data Reference](data-types-operators-and-expressions.md)". When you do not specify a value for qdrlist, HIERHEIGHT uses the values of parentrel that are in current status.

familyrel
A previously -defined relation that the HIERHEIGHT command populates when it executes. This relation can have multiple dimensions; however, it must be dimensioned by the dimensions of parentrel and one other dimension that represents the levels of the hierarchical dimension. The actual construct of the dimension that represents the levels of the hierarchical dimension varies depending on whether or not the HIERHEIGHT statement includes the USING phrase:

- When the statement includes the USING phrase, the dimension that represents the levels of the hierarchical dimension is a dimension that contains the names of the levels.

- When the statement does not include the USING phrase, the dimension that represents the levels of the hierarchical dimension is an INTEGER dimension that has as values the depth of the level.

When familyrel is populated before a HIERHEIGHT statement executes, the HIERHEIGHT statement depopulates it before computing new values.

USING levelrel
Specifies that the relation is populated using the specified levelrel. See "[Levelrel Relation](olap-dml-basic-concepts.md)" for more information.

A
Specifies that the relation is populated in ascending order.

D
(Default) Specifies that the relation is populated in descending order.

inh-variable
A BOOLEAN variable that is dimensioned by the hierarchical dimension and, when the hierarchical dimension is a multi-hierarchical dimension, by a dimension that is the names of the hierarchies. The values of the variable are `TRUE` when the dimension value is in a hierarchy and `FALSE` when it is not.

inh-valueset
The name of a valueset object whose values are the hierarchical dimension values to be considered when creating grouping ids. Values not included in the valueset are ignored. See "[Inhier Valueset or Variable](olap-dml-basic-concepts.md)" for more information.

#### Usage Notes

HIERHEIGHT with the OLAP_TABLE Function

Typically, you use a HIERHEIGHT statement when you are preparing an analytic workspace for access using the `OLAP_TABLE` function.

#### Examples

Example 10-4 Creating a Relational Representation of a Geography Hierarchy

Assume that there is an analytic workspace named `myaw` that has a Geography hierarchy defined with analytic objects with the following definitions.

    DEFINE geog.hierdim DIMENSION TEXT
    LD Hierarchy names for Geography hierarchies

    DEFINE geog.leveldim DIMENSION TEXT
    LD List of levels for GEOGRAPHY hierarchies

    DEFINE geography DIMENSION TEXT WIDTH 12
    LD Values for the Geography hierarchies

    DEFINE geog.levelrel RELATION geog.leveldim <geography geog.hierdim>
    LD Level of each value in the Geography hierarchies

    DEFINE geog.parent RELATION geography <geography geog.hierdim>
    LD Child-parent relation for the Geography hierarchies

    DEFINE geog.familyrel RELATION geography <geography geog.leveldim geog.hierdim>
    LD Geography values by level and hierarchy

These objects have the following structures.

    GEOGRAPHY
    ------------------
    World
    Americas
    Canada
    USA
    Toronto
    Montreal
    Boston
    LosAngeles

    GEOG.HIERDIM
    ------------------
    Standard
    Consolidated

    GEOG.LEVELDIM
    ------------------
    World
    Continent
    Country
    City
    Consolidated
    Continent
    Consolidated
    Country

                       ------------GEOG.LEVELREL------------
                       ------------GEOG.HIERDIM-------------
    GEOGRAPHY               Standard         Consolidated
    ------------------ ------------------ ------------------
    World              World              NA
    Americas           Continent          Consolidated
                                          Continent
    Canada             Country            Consolidated
                                          Country
    USA                Country            Consolidated
                                          Country
    Toronto            City               NA
    Montreal           City               NA
    Boston             City               NA
    LosAngeles         City               NA

                       -------------GEOG.PARENT-------------
                       ------------GEOG.HIERDIM-------------
    GEOGRAPHY               Standard         Consolidated
    ------------------ ------------------ ------------------
    World              NA                 NA
    Americas           World              NA
    Canada             Americas           Americas
    USA                Americas           Americas
    Toronto            Canada             NA
    Montreal           Canada             NA
    Boston             USA                NA
    LosAngeles         USA                NA

To create a family relation of the Geography hierarchy you define an analytic workspace object with the following definition.

    DEFINE geog.familyrel RELATION geography <geography geog.leveldim geog.hierdim>
    LD Geography values by level and hierarchy

Then you use a HIERHEIGHT statement as illustrated in the following statement to populate the object.

    HIERHEIGHT geog.parent INTO geog.familyrel USING geog.levelrel

By issuing a REPORT statement, you can display the relational representations of both the `Standard` and `Consolidated` hierarchies of the `geography` dimension.

    REPORT DOWN geography geog.familyrel

    GEOG.HIERDIM: Standard
                 -------------------------------GEOG.FAMILYREL--------------------------------
                 --------------------------------GEOG.LEVELDIM--------------------------------
                                                                     Consolidated Consolidated
    GEOGRAPHY       World      Continent     Country        City      Continent     Country
    ------------ ------------ ------------ ------------ ------------ ------------ ------------
    World        World        NA           NA           NA           NA           NA
    Americas     World        Americas     NA           NA           NA           NA
    Canada       World        Americas     Canada       NA           NA           NA
    USA          World        Americas     USA          NA           NA           NA
    Toronto      World        Americas     Canada       Toronto      NA           NA
    Montreal     World        Americas     Canada       Montreal     NA           NA
    Boston       World        Americas     USA          Boston       NA           NA
    LosAngeles   World        Americas     USA          LosAngeles   NA           NA

    GEOG.HIERDIM: Consolidated
                 -------------------------------GEOG.FAMILYREL--------------------------------
                 --------------------------------GEOG.LEVELDIM--------------------------------
                                                                     Consolidated Consolidated
    GEOGRAPHY       World      Continent     Country        City      Continent     Country
    ------------ ------------ ------------ ------------ ------------ ------------ ------------
    World        NA           NA           NA           NA           NA           NA
    Americas     NA           NA           NA           NA           Americas     NA
    Canada       NA           NA           NA           NA           Americas     Canada
    USA          NA           NA           NA           NA           Americas     USA
    Toronto      NA           NA           NA           NA           NA           NA
    Montreal     NA           NA           NA           NA           NA           NA
    Boston       NA           NA           NA           NA           NA           NA
    LosAngeles   NA           NA           NA           NA           NA           NA

### 10.5 IF...THEN...ELSE command

Within an OLAP DML program, the IF...THEN...ELSE command executes one or more statements in a program when a specified condition is met. Optionally, it also executes an alternative statement or group of statements when the condition is not met.

**Note:**

You can also use IF as a conditional operator in an expression. See "[IF...THEN...ELSE expression](data-types-operators-and-expressions.md)"

#### Syntax

IF boolean-expression    THEN statement1    \[ELSE statement2\]

#### Parameters

boolean-expression
Any valid Boolean expression that returns either `TRUE` or `FALSE`.

THEN statement1
Oracle OLAP executes the statement1 argument when the Boolean expression is `TRUE`. The statement1 must be on the same line as THEN.

ELSE statement2
Oracle OLAP executes the statement2 argument when the Boolean expression is `FALSE`. The statement2 must be on the same line as ELSE. When you omit the ELSE phrase, execution continues with the statement after the whole IF...THEN... statement in the program.

#### Usage Notes

IF with DO

You can use an IF statement for conditional execution of two or more statements by following the THEN or ELSE (or both) keywords with a DO ... DOEND sequence. See Example 10-5.

Single or Multiple Lines

When IF is used as an expression, the THEN and ELSE keywords must be on the same line as IF. When IF is used as a command, THEN and ELSE must be on separate lines.

#### Examples

Example 10-5 Using IF...THEN...ELSE

The following lines from a program illustrate the use of IF...THEN...ELSE.... When the Boolean expression `ANY(DOLLARS LT 200000)` is `TRUE`, the statements following THEN (`statement group 1`) are executed. When the expression is `FALSE`, the statements following ELSE (`statement group 2`) are executed instead.

    IF ANY(DOLLARS LT 200000)
    THEN DO
      ... " (statement group 1)
      DOEND
    ELSE DO
      ... "(statement group 2)
       DOEND

Example 10-6 Using IF as a Conditional Operator

In a program that produces a report, you would like to report a previous year's actual expenses or the current year's budget, depending on the year passed to the program as an argument. A conditional expression in a JOINCHARS function produces a heading with the word Actual or Budget. Another conditional expression selects the variable to report. The program would include the following lines.

    ARGUMENT cur.year year
     
    LIMIT month TO year cur.year
    REPORT -
       HEADING JOINCHARS( 'Expenses: ' -
                            IF cur.year LT 'Yr95' -
                            THEN 'Actual FOR ' -
                            ELSE 'Budget FOR ', -
                           cur.year ) -
       IF cur.year LT 'Yr95' THEN actual ELSE budget

### 10.6 IMPORT

The IMPORT command transfers data to an analytic workspace from a text file, a spreadsheet, or another analytic workspace from an EIF file.

Because the syntax of the IMPORT command is different depending on where the data to be imported is located, separate topics are provided for different types of source files:

- IMPORT (EIF)

- IMPORT (text)

- IMPORT (spreadsheet)

#### 10.6.1 IMPORT (EIF)

You can use the IMPORT (from EIF) command to copy data and definitions into your Oracle OLAP analytic workspace from an EIF file. IMPORT also copies any dimensions of the imported data that do not already exist in your workspace, even when you do not specify them in the command.

**Tip:**

Several options that determine how EIF files are imported and exported. These options are listed in "[EIF Options](olap-dml-options.md)".

IMPORT (from EIF) is commonly used with [EXPORT (EIF)](olap-dml-commands-a-g.md) to copy parts of one Oracle OLAP analytic workspace to another; you export objects from the source workspace to an EIF file and then import the objects from the EIF file into the target workspace. The source and target workspaces can reside on the same platform or on different platforms. When you transfer an EIF file between computers, you use a binary transfer to overcome file-format incompatibilities between platforms. The EIF file must have been created with the EIFVERSION set to a version that is less than or equal to the version number of the target workspace. Use EVERSION to verify the target version number.

You can also use IMPORT to store information in the EIFNAMES and EIFTYPES options.

##### Syntax

IMPORT import_item FROM EIF FILE file-id \[INTO workspace\] -    \[MATCH \[STATUS\]\|APPEND\|REPLACE \[DELETE\]\] \[LIST \[ONLY\]\] \[DATA\] -    \[DFNS\] \[UPDATE\] \[NOPROP\] \[NASKIP\] \[NLS_CHARSET charset-exp\] -    \[API \|  NOAPI\]

where `import_item` is one of the following:

- `name ``[AS ``newname``]`
- `ALL`

##### Parameters

name \[AS newname\]
The name of an analytic workspace object to be imported from an EIF file to an attached workspace. You cannot specify a qualified object name for the object, because the object is not yet in any workspace. You can list multiple names at a time. See the INTO workspace argument for information about where the object is imported.

AS newname can be used to rename any type of object being imported except dimensions.

When you have exported a multidimensional object as separate variables, list all the variable names. (See the SCATTER AS keyword in the [EXPORT (EIF)](olap-dml-commands-a-g.md).)

ALL
(Default) Indicates that you want to import all the objects contained in the EIF file. See the INTO workspace argument for information about where the objects is imported.

INTO workspace
an analytic workspace name that identifies the attached workspace into which objects is imported. When the objects exist in the specified workspace, then their data is overwritten by the imported data. When the objects do not already exist, IMPORT creates them it in the specified workspace. IMPORT ignores identically named objects when they exist in other attached workspaces.

When you do not specify this argument, then Oracle OLAP does the following:

- When you have not previously defined the objects being imported in an attached workspace, then IMPORT defines them automatically in the current workspace.

- When the objects already exist in any attached workspace, then IMPORT overwrites the data they contain with the imported data.

FROM EIF FILE file-id
Identifies the file you want to import. File-id is a text expression that represents the name of the file. The name must be in a standard format for a file identifier.

MATCH \[STATUS\]
Indicates that the IMPORT command should bring in only the data associated with dimension values that match those already in the target workspace. For dimensions other than time dimensions, ensure that corresponding dimension values are spelled and capitalized identically in the EIF file and your target workspace when you want them to match; for example, `Tents` does not match `TENTS`. For time dimensions, Oracle OLAP identifies dimension values by the dates they represent rather than by the way they are displayed. Therefore, time dimension values in the EIF file automatically matches time dimension values in your workspace when they represent the same time periods. When you specify MATCH STATUS, IMPORT only imports data associated with the values included in the current status of that dimension. When the dimension is limited in the target workspace, Oracle OLAP ignores any data in the EIF file associated with the values excluded from the status.

APPEND
(Default) Indicates that the IMPORT command should bring in all the dimension values, along with associated data, regardless of whether or not the dimension values match those already present in the target workspace. APPEND adds those that do not match to those already present; it adds new values to the end of the list of dimension values. For time dimensions, APPEND also adds dimension values to fill in any gaps between the dimension values in your target workspace and the new ones.

REPLACE \[DELETE\]
Indicates that, for objects already defined in the workspace, IMPORT should keep the existing dimension values that match the dimension values in the EIF file. IMPORT deletes dimension values (and their data) that do not match dimension values in the EIF file. IMPORT replaces the associated data for the dimension values kept as part of the new dimension when the associated data variables are included in the EIF file. For text dimensions, the order of the dimension values in the EIF file is also adapted.

When you specify REPLACE DELETE, no matching takes place. Before importing a dimension, Oracle OLAP performs a MAINTAIN DELETE ALL, which discards all data associated with the existing dimension and the dimension values.

**Note:**

Be careful when using the REPLACE keyword. When you replace the values of a dimension, all variables and relations in the target workspace dimensioned by it are affected. When a variable or relation is not being imported at the same time, replacing the values of one of its dimensions could result in the loss of its data.

LIST
LIST ONLY
Produces a list of the definitions. For dimensions, the output lists the number of values in each dimension, as they are imported into the target workspace. For composites, the output lists the number of dimension value combinations. IMPORT also indicates the number of bytes read and the elapsed time every two minutes or, in any case, after the import procedure.

When you define a conjoint or composite that uses an index type other than the default, the IMPORT LIST command displays the index type. When you use the default index type (HASH for conjoints, BTREE for composites), that information is not displayed.

[EXPORT (EIF)](olap-dml-commands-a-g.md) sends the list to the current outfile. When you specify LIST ONLY, you get only the listing without actually importing anything.

ONLY
Causes Oracle OLAP to place the correct values in the EIFNAMES and EIFTYPES options without actually importing them. However, Oracle OLAP does not produce a full listing of the object definitions. To produce the list, specify the LIST keyword before the ONLY keyword.

DATA
Indicates that, for objects that already exist in the target workspace, IMPORT should update only the data associated with those objects. For formulas that already exist, IMPORT updates their EQ expressions. Objects that IMPORT creates in the target workspace are created with their full definitions and any associated data. You can specify both DATA and DFNS, but when neither is specified, the default is DATA.

DFNS
Indicates that, for objects that already exist in the target workspace, IMPORT should just update definitions and leave data unchanged. The components of the definition affected by IMPORT DFNS are: LD Command, VNF, and PROPERTY. Objects that IMPORT creates in the target workspace still get their data. You can specify both DATA and DFNS, but when neither is specified, the default is DATA.

UPDATE
Indicates that IMPORT should execute an UPDATE statement after importing each object which can be useful when importing large EIF files that would otherwise cause Oracle OLAP to run out of memory. To control the frequency of updates, use the EIFUPDBYTES option.

NOPROP
Prevents any properties that you have assigned to each object from being read from the EIF file.

NASKIP
Specifies that composite tuples (indexes) that contain only `NA` data should not be imported into the target workspace. This argument has no effect on tuples that already exist in the workspace.

NLS_CHARSET charset-exp
Specifies the character set that Oracle OLAP uses when importing text data from the file specified by file-id. Normally, an EIF file contains its own specification of its character set, so that this argument is not needed. However, when the EIF file specifies the character set incorrectly or is missing the character set specification, then you must use this argument to specify the character set correctly.

For information about the character sets that you can specify, see [Choosing a Character Set](../nlspg/choosing-character-set.md) in Oracle Database Globalization Support Guide.

This argument must be the last one specified. When this argument is omitted, and Oracle OLAP cannot determine the character set from the EIF file itself, then Oracle OLAP imports the data using the database character set, which is recorded in the NLS_LANG option.

API
(Default) When the EIF file was created using an [EXPORT (EIF)](olap-dml-commands-a-g.md) command with the API keyword, import any cube metadata defined for the specified items.

**Note:**

Oracle OLAP automatically executes an UPDATE and a COMMIT after executing this type of import.

NOAPI
Even if the EIF file was created using an [EXPORT (EIF)](olap-dml-commands-a-g.md) command with the API keyword, do not import any cube metadata defined for the specified items. When you specify this keyword, Oracle OLAP does not automatically execute an UPDATE and a COMMIT after executing the IMPORT command.

##### Usage Notes

Separate IMPORT Statements

The MATCH, APPEND, REPLACE, DATA, and DFNS arguments you specify affect all the objects you name to be imported. When you want to treat different objects in different ways, use separate IMPORT statements.

Importing and Exporting Hidden Programs

Importing Relations

When you are importing a relation, IMPORT also brings in the definition and values for the related dimension as well.

Importing Concat Dimensions

When you import a concat dimension into an analytic workspace and the concat dimension and none of its component dimensions already exist in the analytic workspace, then Oracle OLAP imports the concat dimension, its component dimensions, and the definitions of all of the dimensions.

When you import a concat dimension that does not already exist but one or more of its component dimensions already exist in the analytic workspace, then Oracle OLAP imports the concat dimension and any new component dimensions and their definitions. For the component dimensions that already exist in the analytic workspace, Oracle OLAP imports the component dimensions as it does other dimensions, obeying any MATCH, APPEND, REPLACE specifications in the IMPORT statement.

When you import a concat dimension with a name and a definition of a concat dimension that already exists in the analytic workspace, then Oracle OLAP imports the concat dimension as it does other dimension.

When you import a concat dimension with the same name as one that already exists in the analytic workspace but the definition of the imported concat dimension is different than the definition of the existing concat dimension, then the definition of the existing concat dimension does not change and the definitions of the component dimensions of the existing concat dimension do not change. Only the component dimensions of the imported concat dimension that are also component dimensions of the existing concat dimension are imported. When the imported concat dimension does not share any component dimensions with the existing concat dimension, an error condition occurs. When you are importing any objects that are dimensioned by the concat dimension, then Oracle OLAP imports only the values of the object that correspond to the values of the imported dimensions.

Importing and Exporting Dimension Surrogates

You can import or export a dimension surrogate to or from an Express Interchange File (EIF). In those operations, a dimension surrogate behaves like a variable that is dimensioned by the dimension of the surrogate. In an EXPORT operation, the dimension for which the surrogate is defined is also exported. In an IMPORT operation, the dimension for which the surrogate is defined is imported but you can use the MATCH, STATUS, DATA, DFNS, APPEND, and REPLACE keywords to affect which values are imported.

Importing a dimension surrogates also imports the definition and values for the dimension for which it is a surrogate. When a dimension with the same definition already exists in the current analytic workspace, then the effects of the IMPORT keywords such as MATCH, APPEND, REPLACE, DATA, and DFNS are the same for the surrogate as they would be for a variable dimensioned by the dimension. When the name and definition of the imported surrogate is the same as a dimension surrogate that already exists in the current analytic workspace and when the imported surrogate has a value that is identical to a value in the existing surrogate, an error condition occurs.

You can import an INTEGER dimension surrogate when no object of the same name exists in the current analytic workspace or when you use the DFNS keyword. Importing an INTEGER dimension surrogate affects existing INTEGER dimension surrogates when the implicit importing of the dimension of the imported surrogate changes the values of the existing dimension.

APPEND Versus REPLACE

When you are importing an INTEGER dimension that already exists in your target workspace, the following considerations apply.

- When the imported INTEGER dimension is larger than the existing one, APPEND and REPLACE have the same effect. The dimension ends up with the number of values in the larger, imported dimension.

- When the imported INTEGER dimension is smaller, REPLACE drops the appropriate dimension values from the end of the dimension, along with any associated data, while APPEND leaves the existing dimension values alone.

INTEGER and SHORTINTEGER Data Types

The IMPORT command translates between the INTEGER and SHORTINTEGER data types. When you are importing a variable with one of these data types from an EIF file and it already exists in your workspace as the other type, Oracle OLAP converts the data automatically. The maximum SHORTINTEGER value is `32,767` and the minimum is `-32,767`. When you import an INTEGER value that exceeds these limits into a SHORTINTEGER variable, the result is `NA`.

TEXT and ID Data Types

When the EIF file you are importing contains ID data that you want to import into TEXT dimensions, variables, relations, or valuesets, Oracle OLAP automatically converts the ID data to text during the import process.

Existing Programs and Models

When you are importing a program or model that already exists in your workspace, you must specify DFNS. A program or a model is a definition only; it does not have any data. The default option DATA does not import the source code when it already exists.

When you define a program, you may specify a data type or a dimension name, which is used when the program is called as a function. When you specify a data type, it determines the data type of the return value. When you specify a dimension name, the return value is a single value of that dimension. When you import an existing program, the data type or the dimension in the imported program definition and the existing program definition must match. Otherwise, Oracle OLAP produces an error message.

PERMIT Statements

The PERMIT statements associated with an object are imported with the object definition. You can see them when you describe the object. However, permission conditions are not evaluated when the object is imported.

When an object with the same name already exists in the target workspace and you specify the DFNS keyword, the PERMIT statements for the object are updated. However, you must execute a PERMITRESET to put the new permission into effect. When an object with the same name already exists in the target workspace and you do not specify the DFNS keyword, the PERMIT statements for the object are not updated. When there is no pre-existing object in the target workspace, and you import with or without the DFNS keyword, the PERMIT statements for the object are updated, but you must execute a PERMITRESET to put the new permission into effect. (See the PERMIT command.)

When you export and import an entire workspace, then update, detach, and reattach the workspace, Oracle OLAP ensures that all the permissions that were in effect before exporting are in place in the target workspace.

Reducing Workspace Size

You can use IMPORT with an EXPORT statement to compact an entire workspace at once. To do this, first export the workspace and then import it under a different name. You can then delete the old workspace and rename the new one with the original name.

Preserving Conjoint Type

When you export a HASH, BTREE, or NOHASH conjoint dimension to an EIF file, the conjoint type is exported along with the definition in the EIF file. When you then import the conjoint dimension into an analytic workspace, Oracle OLAP preserves the conjoint type when you import into a new dimension or a dimension already using that conjoint type. When you import the dimension into an existing dimension that does not use the same conjoint type, Oracle OLAP does not preserve the original conjoint type that was saved in the EIF file.

EIFBYTES, EIFNAMES, and EIFTYPES

You can use the EIFBYTES option to learn the number of bytes read or written by the most recent IMPORT (EIF File) statement. You can use the EIFNAMES option to get a list of the names of all the objects imported by the most recent IMPORT statement and use the EIFTYPES option to learn the types of objects in that list.

The following format causes IMPORT to store information about the specified objects into the EIFNAMES and EIFTYPES options without actually importing the objects. IMPORT places a list of the object names specified by the IMPORT command in the EIFNAMES option. IMPORT also places a list of the type of each object listed in EIFNAMES into the EIFTYPES option. You may use the LIST keyword to send to the current outfile a full listing of the object definitions.

IMPORT name FROM EIF FILE file-id \[LIST\] ONLY

For more information, see the entries for [EIFBYTES](olap-dml-options.md), [EIFNAMES](olap-dml-options.md), and [EIFTYPES](olap-dml-options.md) options.

Importing Unnamed Composites

When you define variables or other objects with the SPARSE keyword in the dimension list, Oracle OLAP creates an unnamed composite that corresponds to the SPARSE dimension list. When you export or import an object with the unnamed composite in its definition, the composite is automatically exported or imported with the object. Because the unnamed composite is not a regular workspace object, you cannot import or export it independently.

Variable Segments Specified with SEGWIDTH

When you use a CHGDFN statement with the SEGWIDTH keyword to specify the length of variable segments, segment information cannot be exported and imported automatically. You can save your SEGWIDTH settings by exporting the entire workspace, creating a new workspace, importing only the workspace objects into the new workspace, specifying segmentation, and then importing the variable data into the new workspace.

Importing TEXT and NTEXT Values

You can export and import TEXT and NTEXT values. Both data types can be exported to a single EIF file.

- Exported TEXT values are stored in the EIF file using the character set specified for the file in the [EXPORT (EIF)](olap-dml-commands-a-g.md).

- Exported NTEXT values are stored in the EIF file as NTEXT (UTF8 Unicode).

- NTEXT values imported into TEXT objects are converted into the database character set which can result in data loss when the NTEXT values cannot be represented in the database character set.

- TEXT values imported into NTEXT objects are converted into the NTEXT (UTF8 Unicode) character set.

##### Examples

Example 10-7 Importing Dimensions from an EIF File

This example shows how to import the contents and dimensions of two variables into the current Oracle OLAP workspace from a disk file called `finance.eif` in the current directory object.

    IMPORT actual budget FROM EIF FILE 'finance.eif'

Example 10-8 IIMPORTING a Concat Dimension

This example shows the result of importing a concat dimension that has a definition that is different than a concat dimension that already exists in the current analytic workspace. Suppose that a DESCRIBE statement returns the following definitions for dimensions and variables in the current analytic workspace.

    DEFINE city TEXT DIMENSION
    DEFINE state TEXT DIMENSION
    DEFINE country TEXT DIMENSION
    DEFINE locality DIMENSION CONCAT (city, state)
    DEFINE geog DIMENSION CONCAT (locality, country)
    DEFINE sales INTEGER VARIABLE <geog>

The following statement reports the `sales` data.

    REPORT sales

The preceding statement produces the following results.

    GEOG                SALES
    ------------------- -----
    <city: Boston>       1000
    <city: Springfield>  2000
    <state: Ma>          3000
    <country: Usa>       4000

A DESCRIBE statement returns the following definitions for dimensions and variables in the `diffconcat.eif` file.

    DEFINE CITY TEXT DIMENSION
    DEFINE REGION TEXT DIMENSION
    DEFINE COUNTRY TEXT DIMENSION
    DEFINE GEOG DIMENSION CONCAT (CITY, REGION, COUNTRY)
    DEFINE SALES INTEGER VARIABLE <GEOG>

The following statement reports the `sales` data for the dimension values in the analytic workspace from which you exported the concat dimension that is in the `diffconcat.eif` file.

    REPORT sales

The preceding statement produces the following results.

    GEOG               SALES
    ------------------ -----
    <city: Boston>      1111
    <city: Worcester>   2222
    <region: East>      3333
    <country: Usa>      4444

The following statement imports the `sales` variable from the `diffconcat.eif` file and implicitly imports the concat dimension `geog`. The APPEND keyword causes Oracle OLAP to add the value `Worcester` to the `city` dimension. After that, it imports new values for `sales` that correspond to `<city: Boston>`, `<city: Worcester>`, and `<country: Usa>`.

    IMPORT sales FROM EIF FILE diffconcat.eif APPEND

After the import operation, reporting the SALES values produces the following results.

    GEOG                SALES
    ------------------- -----
    <city: Boston>       1111
    <city: Springfield>  2000
    <city: Worcester>    2222
    <state: Ma>          3000
    <country: Usa>       4444

#### 10.6.2 IMPORT (text)

You can use the IMPORT (from text) command to copy data from a text file into an Oracle OLAP worksheet object. A worksheet's rows are similar to the lines of a text file.

IMPORT is commonly used to copy text files into an analytic workspace from other software products.

Typically, you use a FILEREAD statement for text files instead of IMPORT. FILEREAD is more efficient and does not require a worksheet object or separate handling of each column of data.

##### Syntax

IMPORT worksheetname FROM \[TEXT\|STRUCTURED\|RULED \[RULER ruler-exp\] -    PRN FILE file-id \[STOPAFTER n\] \[TEXTSTART schar\] \[TEXTEND echar\] -   \[DELIMITER dchar\] \[NLS_CHARSET charset-exp\]

##### Parameters

worksheetname
A text expression that specifies the name of an Oracle OLAP worksheet object. When you have not previously defined worksheetname in your workspace, IMPORT defines it for you automatically, using the default dimensions `WKSCOL` and `WKSROW`. Any previous contents of worksheetname are overwritten. In any one IMPORT statement, you can import only one worksheetname from one text file.

FROM . . . PRN
Indicates that you want to import your Oracle OLAP worksheet from a text file.

TEXT
Imports a whole source file as-is into an Oracle OLAP worksheet on a line-by-line basis. The source file is copied into a single wide worksheet column with a data type of TEXT. The column is always column 1 of the worksheet. Each line in the source file is imported into a separate cell on a separate row in the first column, using as many rows as there are lines in the source file. A blank line in the source file produces a TEXT value with zero characters (a null) in the corresponding row of the worksheet's first column. (TEXT is the default.)

STRUCTURED
Imports a source file into a target worksheet on a cell-by-cell basis, automatically performing three functions:

1.  Each line of characters in the source file is copied into a single row of the target worksheet.

2.  Each group of characters on a line in the source file is copied into a separate TEXT cell on the target worksheet row. A group of characters is defined by two conditions: an uninterrupted (except by a decimal point) sequence of numbers, or enclosure in double quotes. Consequently, numbers containing commas to mark off thousands are split up into different cells unless the commas are first removed.

3.  Any non-numeric characters not enclosed in double quotes are ignored, except minus signs that immediately precede numbers and so are copied into the same TEXT cell along with the numbers. (Be sure there are no spaces between a minus sign and its number in the source file.)

A blank line in the source file results in an `NA` in the first cell of the corresponding worksheet row.

When your file format does not conform to the pattern described here, you can use the TEXTSTART, TEXTEND, and DELIMITER keywords. These arguments let you customize the delimiters IMPORT uses to identify the start and end of each field.

RULED
Indicates import of a file on a column-by-column basis into worksheet cells of various data types. Every line in the source file must follow the same pattern of data along its length as every other line in the file. You describe this data pattern to Oracle OLAP in the one-line ruler-exp using the RULER keyword. IMPORT loops over each line in the source file and copies its contents into a corresponding pattern of cells on a row of the target worksheet, one row for each line. As ruler-exp loops over successive lines in the source file, it adds row after row to the target worksheet, building vertical columns of similar cells as it goes along. Status messages are sent to the current outfile every 20 rows, starting with the message `20 rows processed`.

When the source file contains records that follow several different patterns of character groups, use the less exacting options, STRUCTURED or TEXT, to import the data.

RULER ruler-exp
Used only with the RULED keyword to specify the data type, length, and repeat count of each character group in the record pattern of the source file. Ruler-exp consists of a list of character-group specifications. Each character-group specification must be separated by a comma (`,`), by backslash N (`\n`), or by a space(` `). You do not have to include enough specifications to account for all the characters in the basic record pattern (or line pattern) of the source file; RULER steps to the next record as soon as it runs out of specifications on each line, regardless of how far it is from the end of the current record. Remember to enclose literal text in single quotes.

The specifications for groups of characters are of three types: `T` for TEXT, `A` for numeric (INTEGER or DECIMAL), and `S` for skip or ignore. The formats for these types are shown in the following table:

Table 10-1 Character-Group Specifications for IMPORT from Text

| Format          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \[mm\]`T`nn     | Specifies that Oracle OLAP should copy mm groups (default = 1) of nn characters (bytes) apiece as TEXT. Specifying a group (or groups) of 0 characters leaves an empty cell(s) in the corresponding position in the worksheet. Each group may consist of up to 498 characters. Trailing blanks are stripped.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| \[mm\]`A`nn     | Specifies that Oracle OLAP should copy mm groups (default = `1`) of nn characters (bytes) apiece and try to convert each group to a number. When a character group cannot be converted to a number, it is copied into a TEXT cell and any trailing blanks are stripped. A valid number includes anything you can type for a GET(DECIMAL) function except `NA`.<br>Commas embedded in a number before a period (decimal point) are ignored. Consequently, multiple numbers separated only by commas or two numbers separated only by a single period are treated as parts of a single number (when you want the numbers treated separately, insert spaces between them in the source file). Leading dollar signs (`$`) and trailing percent signs (`%`) are ignored, and leading and trailing spaces are stripped. Multiple periods are treated as excess decimal points and ignored (to undo the effects of dotfill). For example,`...17...` is treated as though the field is `17`.<br>Numbers preceded by a hyphen, or a hyphen and spaces, and numbers enclosed in parentheses, are treated as negative. Specifying a group (or groups) of `0` (zero) characters leaves an empty cell (or cells) in the corresponding position in the worksheet. Each group may consist of up to 4,000 characters. |
| \[`mm`\]`S``nn` | Specifies that Oracle OLAP should skip or ignore mm groups of nn characters (bytes). The limit for nn is 32,767. (You would probably only use mm to expand this limit to handle a very long record.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

FILE file-id
Identifies the file you want to import. File-id is a text expression that represents the name of the file. The name must be in a standard format for a file identifier.

STOPAFTER n
Specifies that no more than n records should be read from the file. When STOPAFTER is omitted, Oracle OLAP reads the whole file.

TEXTSTART schar
The schar argument is a text expression that specifies a single character that you want Oracle OLAP to interpret as the start of a text field in a structured file. The default character is a double quote (`"`).

TEXTEND echar
The echar argument is a text expression that specifies a single character that you want Oracle OLAP to interpret as the end of a text field in a structured file. The default character is a double quote (`"`).

DELIMITER dchar
The dchar argument is a text expression that specifies a single character that you want Oracle OLAP to interpret as the general field delimiter in a structured file. Oracle OLAP uses the general field delimiter to identify both numeric and text fields. The default character is a comma (`,`).

NLS_CHARSET charset-exp
Specifies the character set that Oracle OLAP uses when importing text data from the file specified by file-id which allows Oracle OLAP to convert the data accurately from that character set. This argument must be the last one specified. When this argument is omitted, and Oracle OLAP cannot determine the character set from the file itself, then Oracle OLAP imports the data in the database character set, which is recorded in the NLS_LANG option.

##### Usage Notes

WKSROW and WKSCOL Dimensions

The `WKSROW` (the default worksheet row) dimension of an Oracle OLAP worksheet object corresponds to the lines of a text file. The `WKSCOL` (the default worksheet column) dimension of a worksheet divides each row into cells that can be used to separate data types when there are potentially several types on each line of the source file. `WKSROW` and `WKSCOL` are INTEGER dimensions with values of `1`, `2`, `3`, and so on.

Minimum Worksheet Size

Oracle OLAP sets up a minimum-size worksheet that is 63 cells square, regardless of whether or not all the cells are used. When the source text file requires an Oracle OLAP worksheet larger than the minimum, IMPORT automatically increases the dimension values of `WKSCOL` and `WKSROW` as needed.

Importing Numbers

When importing a number from a text file, IMPORT gives it an INTEGER data type.

File Transfer to Another Computer

When the file you are importing originated on another computer, ensure that its character set is appropriate. When you transfer a text file to another computer, the communications program handling the transfer makes any necessary character translations; for example, from ASCII to EBCDIC. Set the parameters of the transfer program so that the resulting file is in the correct character set for the receiving computer.

##### Examples

Example 10-9 Importing Columns Without the RULER Keyword

Suppose you have a file named `abctxt` in your current directory. It has 10 five-digit groups of `INTEGER` values, followed by a group of 20 characters of text. To import this file into an Oracle OLAP worksheet called `sheet1`, use the following statement.

    IMPORT sheet1 FROM RULED PRN FILE 'abctxt' ruler '10a5, t20'

The actual format for the file name must follow the conventions for your operating system.

Example 10-10 Importing Columns with the RULER Keyword

Suppose a file called `mix` has no line delimiters, with records containing 100 characters apiece. Each record has the character distribution illustrated in the following table.

| Character | Content                   |
|:----------|:--------------------------|
| 1 - 10    | To be ignored             |
| 11 - 17   | Decimal number            |
| 18 - 28   | To be ignored             |
| 29 - 30   | Two single-character code |
| 31 - 35   | Integer                   |
| 36 - 100  | To be ignored             |

To import this file into an Oracle OLAP worksheet called `sheet2`, use the following statement.

    DEFINE sheet2 WORKSHEET temp
    IMPORT sheet2 FROM RULED PRN FILE 'mix' RULER -
       's10, a7, s11, 2t1, a5'

#### 10.6.3 IMPORT (spreadsheet)

You can use the IMPORT (from spreadsheet) command to copy data (not formulas) from a spreadsheet file into an Oracle OLAP worksheet object. A worksheet's dimensions are similar to the columns and rows of a spreadsheet. IMPORT always copies an entire spreadsheet file at a time.

IMPORT is commonly used to copy data from other software products (for example, a Lotus spreadsheet) into an Oracle OLAP workspace.

##### Syntax

IMPORT worksheetname FROM source \[INTO workspace\]

where `source` is one of the following:

- `WKS FILE ``file-id ``[NLS_CHARSET ``charset-exp``]`
- `WK1 FILE ``file-id ``[NLS_CHARSET ``charset-exp``]`
- `WRK FILE ``file-id ``[NLS_CHARSET ``charset-exp``]`
- `WR1 FILE ``file-id ``[NLS_CHARSET ``charset-exp``]`
- `DIF FILE ``file-id ``[NLS_CHARSET ``charset-exp``]`
- `CSV FILE ``file-id ``[STOPAFTER ``n``|DELIMITER ``dchar``|NLS_CHARSET ``charset-exp``]`

##### Parameters

worksheetname
An Oracle OLAP worksheet object. In any one IMPORT statement, you can import only one worksheetname from one spreadsheet file. You can specify a qualified object name for the worksheet; however, when you specify the INTO worksheet argument, the target workspace specified must be identical. See the INTO workspace argument for information about where the worksheet object is imported.

FROM WKS
FROM WK1
FROM WRK
FROM WR1
FROM DIF
Indicates that you want to import your Oracle OLAP worksheet from a 1-2-3 file, Version 1 (`WKS`) or Version 2 (`WK1`); a Symphony file, Version 1.0 (`WRK`) or Version 1.1 (`WR1`); or a data interchange format file (`DIF`).

Oracle OLAP does not recognize numbers in E format (exponential notation) in `DIF` files.

INTO workspace
An analytic workspace name that identifies the attached workspace into which data is imported. When worksheetname exists in the specified workspace, then its data is overwritten by the imported data. When worksheetname does not already exist, IMPORT creates it in the specified workspace. IMPORT ignores an identically named worksheet when it exists in another attached workspace.

When you do not specify this argument, then Oracle OLAP does the following:

- When you have not previously defined worksheetname in an attached workspace, IMPORT defines it automatically in the current workspace using the default dimensions `WKSCOL` and WKSROW.

- When worksheetname already exists in any attached workspace, IMPORT overwrites the data it contains with the imported data.

FILE file-id
Identifies the file you want to import. The file-id argument is a text expression that represents the name of the file. The name must be in a standard format for a file identifier.

NLS_CHARSET charset-exp
Specifies the character set that Oracle OLAP uses when importing text data from the file specified by file-id which allows Oracle OLAP to convert the data accurately from that character set. This argument must be the last one specified. When this argument is omitted, and Oracle OLAP cannot determine the character set from the worksheet itself, then Oracle OLAP imports the data in the database character set, which is recorded in the NLS_LANG option.

**Note:**

The NTEXT data type is not supported in worksheets.

FROM CSV FILE file-id \[STOPAFTER n\] \[DELIMITER dchar\]
Indicates that you want to import from a source file on a cell-by-cell basis. See "CSV Import".

STOPAFTER n specifies that no more than n records should be read from the file. When STOPAFTER is omitted, Oracle OLAP reads the whole file.

DELIMITER dchar identifies the single character (dchar) that you want Oracle OLAP to interpret as the general field delimiter. The default value is comma.

##### Usage Notes

Default Dimensions of an Oracle OLAP worksheet object

The default dimensions of an Oracle OLAP worksheet are `WKSCOL` and WKSROW, which correspond to the columns and rows of a spreadsheet. `WKSCOL` and WKSROW are INTEGER dimensions with values of 1, 2, 3, and so on. When these dimensions already exist in an attached workspace but not in the current workspace, the IMPORT statement fails when it tries to create these dimensions. You can prevent this problem by first defining the worksheet with different dimensions. (See "[Worksheet Dimensions](olap-dml-commands-a-g.md)" for more information.)

Addition of Cells when Needed

When the source spreadsheet contains more cells than are defined by the dimensions of the worksheet, IMPORT automatically adds dimension values to provide the required number of cells.

Empty and NA Cells

IMPORT merges the source file with the worksheet on a cell-by-cell basis. Cells from the source file that are not empty, even when they just contain `NA`, overwrite the contents of the corresponding cells in the worksheet; empty cells in the source file do not overwrite the worksheet; source-file cells beyond the end of the current worksheet are appended to it so that no data is discarded.

Numbers in DIF Files

When importing any number from DIF files, IMPORT gives it a DECIMAL data type.

CSV Import

The CSV import option automatically performs the following functions when importing from a source file into the cells of a worksheet:

- Each line of characters in the source file is copied into a single row in the target worksheet.

- Each group of characters on a line in the source file is copied into a separate TEXT cell in the target worksheet row, and groups are separated by the delimiter character.

When a group of characters is inside double quotation marks:

- A delimiter character found in this group is treated as a literal.

- When a double quotation mark occurs within this group, it must be followed by another double quotation mark.

- A linefeed (`\n`) found within the group is ignored.

- Spaces or tabs found before a starting quotation mark and after an end quotation mark are ignored.

##### Examples

Example 10-11 Importing a DIF File

This example shows how to import a spreadsheet in DIF format in a file called `mortgage.dif`. We define the worksheet first as a temporary object, which saves memory and storage space. IMPORT would define the worksheet sheet1 automatically when it did not already exist. When it had already been used in a previous IMPORT statement, any data in it would be overwritten with new data.

    DEFINE sheet1 WORKSHEET TEMP
    IMPORT sheet1 FROM DIF FILE 'mortgage.dif'

### 10.7 INFILE

The INFILE command causes Oracle OLAP to read statement input from a specified file.

**See Also:**

"[File Reading and Writing Options](olap-dml-options.md)"

#### Syntax

INFILE {file-id\|EOF} \[NOW\] \[NLS_CHARSET charset-exp\] 

#### Parameters

file-id
The name of a file from which to read input. File-id is a text expression that represents the name of the file. The name must be in a standard format for a file identifier.

The input file must contain only OLAP DML statements, along with appropriate responses to any prompts generated by the statements. Each statement or response must appear on a separate line in the file.

EOF
Terminates the reading of input from the current file and causes Oracle OLAP to resume reading input from the location from which the INFILE statement was executed. Use of INFILE EOF is optional. See "About the Input File"and "INFILE with Both NOW and EOF".

NOW
Indicates that Oracle OLAP should open the input file specified in the INFILE and read its statements immediately upon encountering the INFILE instead of waiting until the program containing the INFILE is finished which has the effect of nesting the input file's statements within the program. See "INFILE with Both NOW and EOF". This argument must be specified after file-id.

NLS_CHARSET charset-exp
Specifies the character set that Oracle OLAP uses when reading data from the file specified by file-id which allows Oracle OLAP to convert the data accurately into the current character set, as identified by the NLS_LANG option. This argument must be specified after file-id. When this argument is omitted, then Oracle OLAP handles the data in the file as having the database character set, which is recorded in the NLS_LANG option.

#### Usage Notes

About the Input File

When the end of the input file is reached, Oracle OLAP resumes reading input from the location from which the INFILE statement was executed (which could be another input file). You do not have to end the input file with the statement INFILE EOF.

INFILE ignores trailing blanks at the end of a line, or between the last text on a line and a continuation mark. INFILE also ignores blank lines.

When you use the NOW keyword and the input file ends with a continued statement, the statement is ignored. For example, if the file ends with "show - ," Oracle OLAP ignores a SHOW statement.

Using INFILE in a Program

When you include an INFILE statement without the NOW keyword in a program, the INFILE statement is not executed until the program has finished executing. In a nested program, it is not executed until all the programs involved have finished executing. Also, when several INFILE commands have been executed by a program, the input files are read in the opposite order from which they were specified.

For example, assume that `program.a` calls `program.b` which calls `program.c`, and each program contains two INFILE commands, one before and one after the call to the next program (as illustrated in the following code). In this case, the order of execution is: `a2`, `b2`, `c2`, `c1`, `b1`, `a1`.

    program.a
       INFILE a1
       "
            program.b
               INFILE b1
               "
                    program.c
                       INFILE c1
                       INFILE c2
               "
               INFILE b2
       "
       INFILE a2

When you include an INFILE statement in a program with the NOW keyword, the INFILE statement executes immediately. However, INFILE with the NOW keyword requires more space than usual on the program stack. To conserve stack space, use the NOW keyword only when it is necessary.

INFILE with NOW Outside of Programs

The NOW keyword is intended for use within programs, but you can use it at any time. When you use it when the input file would not ordinarily be deferred, the NOW keyword has no visible effect. However, because NOW requires extra stack space, do not use it in these situations.

INFILE with Both NOW and EOF

When you use both the NOW and EOF keywords, the NOW keyword is ignored.

Displaying Infiled Statements and Responses

When you want the statements from a disk file to be copied to a debugging file as they are executed, see the [DBGOUTFILE](olap-dml-commands-a-g.md) command.

#### Examples

Example 10-12 Reading the Input File Immediately

The following line of code in a program causes the file called `newdefs` to be read in immediately.

    INFILE 'newdefs' NOW

### 10.8 LD

The LD command adds the description to the current object definition. The description consists of text that you specify to describe the object. You can assign a description to any type of definition.

**Tip:**

The current object definition is the definition of the object that has been most recently defined or considered during the current session. To make an object definition the current definition, use a CONSIDER statement.

#### Syntax

LD \[text\]

#### Parameters

text
The text of the description you want to assign to the definition. When text is omitted, any existing description for the current definition is deleted.

You can create a multiline description by using a hyphen as a continuation character. However, you cannot create a description with an initial blank line with an LD statement.

#### Examples

Example 10-13 Adding a Description to the Definition of a Variable

This example changes the description associated with the variable `units`. First, execute the CONSIDER statement to make `units` the current definition. Then use a LD statement to assign a new description. The `units` variable has the following definition.

    DEFINE units VARIABLE INTEGER <month product district>
    LD Actual Unit Shipments

The statements

    CONSIDER units
    ld Actual Unit Shipments for Each Division
    DESCRIBE units

produce the following definition for `units`.

    DEFINE units VARIABLE INTEGER <month product district>
    LD Actual Unit Shipments for Each Division

### 10.9 LIMIT command

The LIMIT command sets the current status list of a dimension and its dimension surrogates, or assigns values to a valuesets the current status list of a dimension and its dimension surrogates, or assigns values to a valueset. You use LIMIT to restrict the data values you are working on by temporarily limiting the range of the dimensions of the data. Using LIMIT, you create acurrent status list for a dimension. The current status list of a dimension is an ordered list of currently accessible values for the dimension. Values that are in the current status list of a dimension are said to be "in status." For more information on dimension status and its importance when working with analytic workspace data, see "[How to Specify the Set of Data that OLAP DML Operations Work Against](olap-dml-basic-concepts.md)".

**Tip:**

You set the current status list of one or more base dimensions of a composite, conjoint dimension, concat dimension, or a partition template based on the selected values of that object, see the LIMIT BASEDIMS command.

**See Also:**

[LIMIT function](olap-dml-functions-l-z.md), [DEFINE VALUESET](olap-dml-commands-a-g.md)

#### Syntax

LIMIT {dimension \| valueset } \[concat-component\] limit-type \[limit-clause\] \[IFNONE label\]

where `limit-type` is one of the following keywords that specify how Oracle OLAP should modify the current status list:

- `TO`
- `ADD`
- `INSERT [FIRST|LAST|BEFORE` `position``|AFTER` position`]`
- `KEE`
- `REMOVE`
- `KEEP REORDER`
- `COMPLEMENT`
- `SORT [NAFIRST]`

#### Parameters

dimension
The name of the dimension or dimension surrogate for which you are setting status.

valueset
The name of the valueset for which you are assigning values.

concat-component
Specifies the name of the component of the concat dimension whose values are used to determine the limit. When you specify a value for concat-component, the limit sets the status of the specified concat dimension using the values of dimension which is a component of the concat dimension. This limit-clause applies only when dimension is a concat dimension. The status of a concat dimension and of its component dimensions are not shared. Changing the status of a component dimension after you have used that dimension as the limit-clause in setting the status of a concat dimension does not change the status of the concat dimension.

TO
Replaces the status of a dimension or valueset with the values specified by the limit-clause arguments. The TO keyword selects values from the default status of a dimension in the same order as they appear in the LIMIT statement or in the order implied by the valuelist argument. When you use arguments that imply ordering, the ordering of the values is based on their positions in the default status.

ADD
Expands the status of a dimension or valueset by adding the values specified by the limit-clause arguments that are not already in status. The ADD keywords selects values from the default status of a dimension in the same order as they appear in the LIMIT statement or in the order implied by the valuelist argument. When you use arguments that imply ordering, the ordering of the values is based on their positions in the default status. ADD adds unique dimension values in the specified order after the current status list or valueset list.

INSERT
Expands the status of a dimension or valueset by inserting the values specified by the limit-clause arguments in a specified position in the current status. The INSERT keyword selects values from the default status of a dimension in the same order as they appear in the LIMIT statement or in the order implied by the valuelist argument.

When you use arguments that imply ordering (for example,`value1` `TO` `value2`), the ordering of the values is based on their positions in the default status. INSERT adds values to a specified position in the current status. When an added value is already in status, it is removed from its position in the current status and added in the order in which it appears in the valuelist, preserving the order of the added values.

FIRST
Inserts the new values before the first value in status.

LAST
Inserts new values after the last value in status.

BEFORE
AFTER
Specifies whether new values Oracle OLAP inserts new values before or after position in the current status.

position
A dimension value in the current status, a character expression whose value is a dimension value in the current status, or an `INTEGER` expression whose value represents the position of a dimension value in the default status.

KEEP
Reduces the status of a dimension or valueset by keeping only the values specified by the limit-clause arguments. Oracle OLAP performs the selection based on the current dimension status. KEEP preserves the current order of values among the values that remain in the status.

KEEP REORDER
Like a simple KEEP, KEEP REORDER reduces the status of a dimension or valueset by keeping only the values specified by the limit-clause arguments. Oracle OLAP performs the selection based on the current dimension status. However, KEEP REORDER orders the result in the order of the selection arguments (that is, the limit-clause arguments) rather than by the current status order.

REMOVE
Reduces the status of a dimension or a valueset by removing the values specified by the limit-clause arguments. Oracle OLAP performs the selection based on the current dimension status. KEEP preserves the current order of values among the values that remain in the status.

COMPLEMENT
Replaces the status of a dimension or valueset with the values that are not specified by the limit-clause arguments. When you do not specify any arguments after COMPLEMENT, status is replaced by all values not now in status. Oracle OLAP performs the selection based on the current dimension status. COMPLEMENT leaves dimension values that remain in their default order. (Abbreviated COMP)

SORT
Sorts the values of a dimension or valueset according to the limit-clause arguments. LIMIT creates a temporary list of values based on the limit-clause arguments, and uses this list to sort the current status list. Any values not present in the temporary list are moved to the end of the current status list.

NAFIRST
Specifies that `NA` values are placed first in the sort list rather than last.

limit-clause
Specifies the values to use for the limit. The syntax is quite complex and, consequently, has been divided into the following topics:

- LIMIT (using values) command
- LIMIT using LEVELREL command
- LIMIT (using related dimension) command
- LIMIT (using parent relation)
- LIMIT NOCONVERT command
- LIMIT command (using POSLIST)

IFNONE
(For use only within an OLAP DML program) Specifies that program execution should branch to label when the requested status has null status or is based on a related dimension that turns out to have null status (that is, to have no values). In either case, the null status is not put into effect when program execution branches. Instead, the original status, before the LIMIT statement was executed, is retained even when OKNULLSTATUS is `YES`. Within an OLAP DML program, you cannot use both IFNONE and NULL in the same statement.

label
The name of a label elsewhere in the program constructed following the "[Guidelines for Constructing a Label](olap-dml-commands-a-g.md)". Execution of the program branches to the line directly following the specified label.

Note that label, as specified in IFNONE, must not be followed by a colon. However, the actual label elsewhere in the program must end with a colon.

#### Usage Notes

Specifying a Value of a Concat Dimension

To specify a value of a nonunique concat dimension, use the following syntax.

\<base-dimension: value\>.

Default Status List

When you first attach an analytic workspace, the current status list of each dimension consists of all of the values of the dimension that have read permission, in the order in which the values are stored. This list of values is called the default status list for the dimension.

Unique Values

LIMIT selects only unique values of a dimension. When a value appears more than once in a LIMIT statement, it is placed in status in the order of its first appearance. For example, the following lines.

    LIMIT time TO 'Jan97', 'Feb97', 'Jan97'
    STATUS time

produce this output.

    The current status of TIME is:
    JAN97, FEB97 

Nonexistent Values

Oracle OLAP does not signal an error when you try to set the status of a dimension or valueset that has no values, unless you explicitly list values that do not exist. For example, assume that you have not added any values to a newly defined dimension WEEK. In this case, the statement `LIMIT week TO FIRST 10` does not cause an error. However, `LIMIT week TO 'Pete'` causes an error because `Pete` is not a value. Similarly, `LIMIT week TO 20` causes an error because `week` does not have a value at position `20`.

Setting the Status of a Dimension or Valueset to Null

Oracle OLAP allows the status of a dimension or valueset to be set to null (empty status) only when you have explicitly specified that you want null status to be permitted. You can give this permission in either of two ways:

- Set the OKNULLSTATUS option to `YES`. This specification indicates that null status should be allowed whenever it occurs (unless the IFNONE argument is present in a LIMIT statement).

- Use the NULL keyword in a LIMIT statement to set the status of a particular dimension or valueset to null. You can do this by specifying TO NULL or KEEP NULL. This specification indicates that null status should be allowed for this LIMIT statement only.

When you have not used either of these two methods to give permission for null status and you execute a LIMIT statement that would result in null status, Oracle OLAP does not change the status to null when it executes the statement. Instead, Oracle OLAP leaves the status as it was before the statement was issued and either signals an error (when IFNONE is not present) or branches to the IFNONE label (when IFNONE is present).

An IFNONE argument indicates that you do not want program execution to take its normal course when a dimension's status were to be set to null. Therefore, when IFNONE is present, Oracle OLAP branches to the IFNONE label and does not set the status to null, even when OKNULLSTATUS is `YES`. When the NULL keyword is present with IFNONE, Oracle OLAP signals the inconsistency with an error.

IFNONE requires the use of unstructured programming techniques. Oracle OLAP now provides alternative structured techniques, so the use of IFNONE is discouraged. IFNONE has been retained for compatibility with previous versions of Oracle OLAP.

Limiting a Conjoint

To limit a conjoint dimension to a value list, you can use the following constructions:

- Specify the actual values, surrounding each combination with angle brackets

      LIMIT proddist TO '<Tents, Boston>' -
         '<Footwear, Denver>'

<!-- -->

- Use a variable name for the values, surrounding the combination with angle brackets.

      prodname = 'Canoes'
      distname = 'Seattle'
      LIMIT proddist To <prodname, distname>

- Create a multiline list, where each line is a combination surrounded by angle brackets.

      namelist = '<Tents Boston>\n<Footwear, -
         Denver>\n <Canoes, Seattle>'
      LIMIT proddist TO namelist

<!-- -->

- Use the implicit relation between a conjoint dimension and its base dimension to limit the conjoint dimension. For example, use the following statement to limit PRODDIST to all conjoint values having "Canoes" as one of its base values.

      LIMIT proddist TO product 'Canoes'

  **Note:**

  You can use logical position numbers for base dimension values in a conjoint dimension. "[Example 7-125](olap-dml-functions-a-k.md)" illustrates using logical position numbers

For an example of how you can limit a conjoint dimension that has a concat base dimension, see Example 10-25.

Limiting a Concat

You can define a concat dimension using simple dimensions, conjoint dimensions, and other concat dimensions as the base dimensions of the concat. The syntax for limiting a concat dimension to one of its values is the following.

LIMIT concatdim TO \<base-dim: value\>

For example, the concat dimension `reg.dist.ccdim` has the simple dimensions `region` and `district` as its base dimensions. The following statement sets the status of `reg.dist.ccdim` to two of its values, `region: East` and `district: Atlanta`.

    LIMIT reg.dist.ccdim TO <region: 'East'> <district: 'Atlanta'>

For other methods of setting the status of a concat dimension, see Example 10-16.

Alternative to Branching Using an IFNONE Label

As an alternative to branching to an `IFNONE` label, you can also handle null status for a dimension with the OKNULLSTATUS option. When you set OKNULLSTATUS to `YES`, then you are allowed to set the status of a dimension to null. You can then check for null status and execute appropriate commands with an IF...THEN...ELSE command, or you can handle null status as a case in a SWITCH command.

    OKNULLSTATUS = YES
    LIMIT month TO sales GT salesnum
    IF STATLEN(month) LT 1
       THEN GOTO showerr

#### Examples

Example 10-14 Adding and Removing Values

These lines add values to the status for the `month` dimension.

    LIMIT month TO 'Jan96' TO 'Jun96'
    LIMIT month ADD 'Jul96' 'Sep96'

Issuing a `STATUS month` statement produces this output.

    The current status of MONTH is:
    Jan96 TO Jul96, Sep96

This line removes values from the status for the `month` dimension.

    LIMIT month REMOVE 'Jan96' TO 'Mar96'

Now, issuing a `STATUS month` statement produces this output

    The current status of MONTH is:
    Apr96 TO Jul96, Sep96

Example 10-15 Limiting with a Dimension Surrogate

A dimension and any dimension surrogates for it share the same status.

For example, assume that there is a `NUMBER` dimension named `store_id` that has the values` 25`, `410`, `150`, `205`, `310`, and `10`. It also uses `storepos`, an INTEGER dimension surrogate for `store_id`. The dimension surrogate `storepos` has the values `1`, `2`, `3`, `4`, `5`, and `6`. A TEXT dimension surrogate for `store_id` is `storename`. It has the text values `Raoul's - Boston`, `Poldy's Potpourri`, `Molly's Emporium`, `Raoul's - Atlanta`, `Kinch's Kitchen Supplies`, and `Raoul's - Chicago`. The following statements are equivalent.

    LIMIT store_id TO 25 410 150
    LIMIT store_id TO storepos 1 2 3
    LIMIT storepos TO 1 TO 3
    LIMIT storepos TO first 3
    LIMIT storename TO first 3
    LIMIT storename TO 'Raoul\'s - Boston' TO 'Molly\'s Emporium'
    LIMIT store_id TO storename storepos 1 2 3
    LIMIT storename TO store_id 25 TO 150

The following statements set the status of the `store_id` dimension by limiting `storename`, which is a TEXT dimension surrogate for `store_id`, and report the values of `store_id`.

    LIMIT storename TO 'Raoul\'s Sweets' TO 'Henry\'s Flowers'
    REPORT store_id

The preceding statement produces the following output.

    STORE_ID
    --------------
    10
    20
    30

Example 10-16 Limiting a Concat Dimension

In the following examples, the concat dimension `reg.dist.ccdim` has the simple dimensions `region` and `district` as its base dimensions. A concat dimension has an implicit relation to each of its component dimensions.

- The following statement sets the status of the concat dimension using the related dimension syntax and specifying the positions of the component (related) dimension.

      LIMIT reg.dist.ccdim TO district 1, 4, 5

  Issuing a `STATUS reg.dist.ccdim` statement produces the following output.

      The current status of REG.DIST.CCDIM is:
      <DISTRICT: BOSTON>, <DISTRICT: DALLAS>, <DISTRICT: DENVER>

- The following statement limits the concat dimension directly to the values specified by positions of the concat dimension.

      LIMIT reg.dist.ccdim TO 1, 4, 5

  Issuing a `STATUS reg.dist.ccdim` statement produces the following output.

      The current status of REG.DIST.CCDIM is:
      <REGION: EAST>, <DISTRICT: BOSTON>, <DISTRICT: ATLANTA>

- The following statements set the status of `district` and then limit `reg.dist.ccdim` to the status of `district`.

      LIMIT district TO LAST 3
      LIMIT reg.dist.ccdim TO district

  Issuing a `REPORT reg.dist.ccdim` statement produces the following output.

      REG.DIST.CCDIM
      ----------------------
      <district: Dallas>
      <district: Denver>
      <district: Seattle>

- In the following statement, the limit-clause argument is a list of values of the concat dimension.

      LIMIT reg.dist.ccdim TO <region: 'East'> <district:  'Boston'> <district: 'Atlanta'>

- The following statements define a valueset for `reg.dist.ccdim`, store the current status of the concat dimension in the valueset, reset the status of the concat to `ALL`, and then limit the concat to the valueset and report the values of the concat in status.

      DEFINE regdist.vset VALUESET reg.dist.ccdim
      LIMIT regdist.vset TO reg.dist.ccdim
      LIMIT reg.dist.ccdim TO ALL
      LIMIT reg.dist.ccdim TO regdist.vset
      RPR W 22 reg.dist.ccdim

  The preceding statements produce the following result.

      REG.DIST.CCDIM
      ----------------------
      <region: East>
      <district: Boston>
      <district: Atlanta>

You can also limit a concat dimension using a valueset of one of its component dimensions:

- When the component dimensions contain identical values, you can limit the concat dimension to those values by using a Boolean expression. When the `district` and `region` dimensions both have `New` `York` as a value, then the following statement limits the `reg.dist.ccdim` to those values.

      LIMIT reg.dist.ccdim TO BASEVAL(reg.dist.ccdim) EQ 'New York'

- In the following example, the concat dimension `geog` has the simple dimension `region` and the conjoint dimension `cityandstate` as its base dimensions. The following statement sets the status of the concat dimension by limiting the conjoint base dimension.

      LIMIT geog TO cityandstate <'Princeton' 'New Jersey'> -
         <'Patterson' 'New Jersey'>

  Issuing a `STATUS geog` statement produces the following output.

      The current status of GEOG is:
      <CITYANDSTATE: <PRINCETON, NEW JERSEY>, <CITYANDSTATE: <PATTERSON, NEW JERSEY>>

- The following statements sets the status of the concat dimension by limiting the conjoint base dimension by specifying a value of a base dimension of the conjoint dimension.

      LIMIT geog TO cityandstate city 'Princeton'
      RPR W 30 geog

  The preceding statement produces the following output.

      GEOG
      ------------------------------
      <cityandstate: <Princeton, New Jersey>>
      <cityandstate: <Princeton, Indiana>>

Example 10-17 Limiting with a Worksheet

This example shows how to limit a dimension to the values that are contained in a column of a worksheet. Here the dimension `month` is limited to the values that are contained in the first column of the worksheet `workitem`. The following statements produce a `workitem` report, which is shown following the statements.

    LIMIT month TO ALL
    LIMIT wkscol TO 1
    LIMIT wksrow TO workitem NE NA
    REPORT workitem
                   -WORKITEM-
                   --WKSCOL--
    WKSROW             1
    -------------- ----------
                 1 Jan96
                 2 Feb96
                 3 Mar96
                 4 Apr96
                 5 May96
                 6 Jun96
                 7 Jul96
                 8 Aug96
                 9 Sep96
                10 Oct96
                11 Nov96
                12 Dec96

The following statement limits the `month` dimension to the values that are listed in the first column of `workitem`.

    LIMIT month TO CHARLIST(workitem)

Issuing a `STATUS month` statement produces the following output.

    The current status of MONTH is:
    Jan96 TO Dec96

Example 10-18 Using Ampersand Substitution with LIMIT

Assume that you want to specify exactly two products for a program named `product.rpt`. In this case, you could declare two dimension-value arguments to handle them. But when you want to be able to specify any number of products using LIMIT commands, then you can use a single argument with ampersand substitution.

Suppose you use the following commands in your program.

    ARGUMENT natext TEXT
    ARGUMENT widthamt INTEGER
    ARGUMENT rptprod TEXT
        ...
    LIMIT product TO &rptprod

You can run the program and specify that you want the first three products in the report.

    CALL product.rpt ('Missing' 8 'first 3')

The single quotation marks are necessary to indicate that "first 3" should be taken as a single argument, rather than two separate arguments separated by a space. The ampersand causes the LIMIT command to interpret `'first 3'` as a keyword expression rather than as a dimension value.

Example 10-19 Branching on Null Status

Your program might try to set or refine the status of the `product` dimension to include only the products for which unit sales are greater than 500. When no products have unit sales of more than 500, then you can use the `IFNONE` keyword to specify that execution branch to the `novals` label.

    LIMIT product KEEP units GT 500 IFNONE novals

In the commands following the `novals` label, you can handle the special situation in which no products have units sales greater than 500.

#### 10.9.1 LIMIT (using values) command

A LIMIT command with a using values limit clause assigns values to a valueset or sets the current status list of a dimension or dimension surrogates to:

- Specified value or values. The values can be any of the following:

  - Dimension values, expressed as literal values separated by commas, or as a multiline text expression, each line of which is a value of the dimension.

  - Ranges of dimension values, expressed as `value1` `TO` `value2`.

  - Integer values that represent the logical positions of dimension values, expressed as comma-delimited `INTEGER` values.

  - Ranges of INTEGER values that represent the logical positions of dimension values, expressed as `value1` `TO` `value2`.

  - Valuesets.

- Values for which a Boolean expression is `TRUE`.

- The top or bottom performers of a dimension based on a criterion

- The top or bottom performers of a dimension, by percentage, based on a criterion represented as an expression

##### Syntax

LIMIT {dimension \| valueset} \[concat-component\] limit-type -

     {inclusive-val-args....\| exclusive-val-args} \[IFNONE label\]

where:

- `inclusive-val-args` is one or more of the following constructs:

  -      `intvaluelist` 
  -      `text-expression`
  -      `value1 ``TO ``value2`
  -      `valuelist`
  -      `valueset`
  -

- `exclusive-val-args` is one of the following constructs:

  - `     ALL`
  -      `boolean-expression`
  - `     {BOTTOM|TOP} ``n ``BASEDON ``expression`
  - `     {BOTTOM|TOP} ``n-percent ``PERCENTOF ``expression`
  - `     {FIRST|LAST} ``n`
  - `     NTH {``n` \|n TO n}...
  - `     LONGLIST`
  - `     LONGLIST`
  - ` SESSION`
  - `STATUS`
  - `     NULL`
  -

##### Parameters

dimension
The name of the dimension or dimension surrogate for which you are setting status.

valueset
The name of the valueset for which you are assigning values.

concat-component
The name of the component of the concat dimension whose values are used to determine the limit. (See the main entry for LIMIT command for complete description of this argument.)

limit-type
A keyword that specifies how Oracle OLAP should modify the current status list. (See the main entry for LIMIT command for a list and descriptions of these keywords.)

intvaluelist
A list of one or more `INTEGER` values, or the name of a single-cell variable that holds a numeric value. Separate the values with commas (`,`). Numeric values with decimal places (SHORTDECIMAL or DECIMAL values) are automatically truncated to `INTEGER` values before being used as dimension values. An `INTEGER` specifies a dimension value by its logical position in the full set of dimension values. You cannot specify a `NUMBER` dimension value by an `INTEGER` position. When the values of the `NUMBER` dimension are `INTEGER` values, then you can set the status of the dimension by specifying dimension values, as in intvalue1, intvalue2 and so on.

text-expression
A multiline text expression, each line of which is a value of dimension.

value1 TO value2
Specifies a range of dimension values where value1 and value2 can be either `INTEGER` values or dimension values. Such a range can be increasing (for example, 1 to 10) or decreasing (for example, 10 to 1). When you specify an `INTEGER` value, that value is the logical position of a value in the default status list for the dimension. When you specify a dimension value, the command convertsthe value to the logical position of the value in the default status list for the dimensioon. The current status of the dimension or valueset is assigned accordingly.

**Tip:**

You cannot specify the values of a `NUMBER` dimension using INTEGER positions. Instead, define an `INTEGER` dimension surrogate for the `NUMBER` dimension and limit the dimension by the positions of the surrogate.

valuelist
A list of one or more values of dimension. A dimension value can be specified as a text expression whose value is a valid dimension value. For a `NUMBER` dimension, dimension values are numbers. For dimensions with a type of DAY, WEEK, MONTH, QUARTER, or YEAR, dimension values can also be specified as `DATE` expressions.

valueset
An analytic workspace valueset object that is a saved list that holds the values for the dimension whose status is being set. You cannot define a valueset for a dimension surrogate, therefore you cannot specify a valueset when setting the status of a dimension surrogate. However, when you limit a dimension with a valueset, then you automatically limit to the same set any dimension surrogates of that dimension. You can also specify a [LIMIT function](olap-dml-functions-l-z.md).

ALL
Specifies that all dimension values in the default status are to be included in the status. The default status is made up of all dimension values for which read permission is granted, in the same order as when the dimension was last maintained. When you start up an analytic workspace, the status for each dimension in your analytic workspace is the default status. Changing the read permission for a dimension with PERMIT or PERMITRESET statement changes the default status for the dimension.

boolean-expression
An expression whose TRUE values are used by Oracle OLAP when limiting the dimension or status. The boolean-expression must be dimensioned by the dimension whose status is being set. For a dimension surrogate, the Boolean expression is evaluated over the dimension for which it is a surrogate. The data types of the expressions you are comparing in the Boolean expression must be similar. See the [CONVERT](olap-dml-functions-a-k.md) function for information on converting data types. To correctly use LIMIT with a Boolean expression you must understand how it works with a Boolean expression that has with multiple dimensions, see "How LIMIT Handles Boolean Expressions With More Than One Dimension" for details.

BOTTOM  n BASEDON expression
TOP n BASEDON expression
Specifies that the status of a dimension or valueset is set based on a criterion, where n is the number of values to select and expression is the criterion on which to base the selection. All dimensions of expression other than the one whose status is being set must be limited to a single value. TOP results in the status sorted in descending order, BOTTOM results in the status sorted in ascending order. You cannot use a composite after the BASEDON keyword. When you attempt to do so, an error message is displayed.

BOTTOM n-percent PERCENTOF expression
TOP n-percent PERCENTOF expression
Specifies that the status of a dimension or valueset is set by finding the top or bottom performers based on a criterion represented as an expression. This construction sorts values and adds them to the status that is based on their contribution, by percentage, to an expression.

For example, the following statement sorts products in descending order by each product's contribution to `TOTAL(sales)` and then add values to the status, starting from the top, until the cumulative total of `sales` by `product` reaches or exceeds 30 percent of all sales.

    LIMIT product TO TOP 30 PERCENTOF TOTAL(sales, product)

**Note:**

Do not use a criterion expression that causes a side effect or changes its own value.

FIRST n
LAST n
Specifies the first n, last n values in the dimension's full set of values when used with TO, ADD, COMPLEMENT, or INSERT. When used with KEEP or REMOVE, specifies the first n, last n or nth values in the current status.

**Note:**

It can happen that the last item in status, based on a PERCENTOF criterion, is one of several dimension values having the same associated criterion value. In this case, LIMIT includes all dimension values with that criterion value in the resulting status, even when that causes the total of the criterion value to far exceed the specified percentage.

NTH {n \|n TO n}
Specifies the n values in the dimension's full set of values when used with TO, ADD, COMPLEMENT, or INSERT. When used with KEEP or REMOVE, specifies the n values in the current status. You can specify any number of values or range of values.

LONGLIST
Indicates that there can be up to 2,000 arguments in the LIMIT statement. When there are less than 300 arguments, LONGLIST is not needed.

SESSION
Specifies that Oracle OLAP use only those dimension members that were created using a MAINTAIN ADD SESSION statement when performing the limit.

STATUS
Specifies that Oracle OLAP use the values that are presently in status when performing the limit. Specifying this keyword is equivalent to (but more efficient than) using a VALUES (dimname) statement.

NULL
Indicates an empty dimension or valueset list. Using this keyword with the TO or KEEP arguments removes all values from the current status, leaving an empty dimension or valueset list, even when OKNULLSTATUS is `NO`. You cannot use IFNONE and NULL in the same LIMIT statement. ADD, INSERT, and REMOVE NULL leave status unchanged. COMPLEMENT NULL places all values in status.

IFNONE label
Specifies that program execution should branch to label when the requested status has null status or is based on a related dimension that turns out to have null status (that is, to have no values). (See the main entry for LIMIT command for complete description of this phrase.)

##### Usage Notes

Considerations When Specifying Values

Keep the following points in mind when specifying values in limit-clause:

- The setting of the LIMITSTRICT option determines how Oracle OLAP behaves when a list of values in a LIMIT command, a LIMIT function, or a QDR contains a nonexistent value. By default, when you specify a nonexistent value, Oracle OLAP treats the nonexistent value as an invalid value and stops executing the limit and issues an error. If, instead, you want Oracle OLAP to treat a nonexistent value as an` NA` value, set the value of LIMITSTRICT to `NO`.

- You can embed a quoted string within a quoted string, which is necessary when there are special characters in a base dimension value of a composite or conjoint dimension, such as `Joe's Deli`. See the "[Text Literals](data-types-operators-and-expressions.md)".

- When the dimension has the NTEXT data type and an argument that represents a dimension value has the TEXT data type, LIMIT converts the argument value to NTEXT. Similarly, when the dimension has the TEXT data type and an argument that represents a dimension value has the NTEXT data type, LIMIT converts the argument value to TEXT; however, in this case, the conversion can result in data loss when the NTEXT value cannot be represented in the database character set.

- When you specify a value of a dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR, the value can be in the format specified by the VNF (value name format) for the dimension (or in the default VNF for the type of dimension you are limiting when the dimension does not have a VNF) or in a valid input style for DATE values.

  You must only provide the date components that are relevant for the type of dimension you are limiting. For a DAY or WEEK dimension, you must supply the day, month, and year components. For a MONTH or QUARTER dimension, you must only supply the month and year (for example, `Jun95` or `0695` for June 1995). For a YEAR dimension, you must only specify the year (for example, `95` for 1995). The valid input styles for dates are discussed in DATEORDER.

  When you specify a DATE expression or a text value that represents a complete date, you can specify any date that falls within the time period that is represented by the desired dimension value. Oracle OLAP uses the DATEORDER option to resolve any ambiguities.

How LIMIT Handles Boolean Expressions With More Than One Dimension

When you have used this type of LIMIT command (or LIMIT function) to limit only one dimension of a multi-dimensional Boolean expression, you effectively limit that expression to the values of limited dimension and only the current values of the unlimited dimensions.

For example, assume that you you have a `sales` variable is dimensioned by three dimensions: `product`, `district`, and `month`.

Let's look first at what happens when you explicitly limit `district` and `month` dimensions to single values and then limit `product` using a Boolean expression.

    LIMIT month TO 'Jan95'
    LIMIT district TO 'Boston'
    LIMIT product TO sales GT 90000
    STATUS product

The STATUS statement produces the following output.

    The current status of PRODUCT is:
    Footwear

In this case, the resulting status is all of the products whose sales exceed \$90,000 for the month of January 1995 in the Boston district, which is only Footwear.

Now consider the following example in which the MONTH dimension is not limited to a single value.

    LIMIT product TO ALL
    LIMIT month TO 'Jan95' 'Feb95' 'Mar95'
    LIMIT district TO 'Boston'

When you execute a REPORT `sales` statement, you can see the BOSTON sales figures for three months.

    DISTRICT: BOSTON
                   -------------SALES--------------
                   -------------MONTH--------------
    PRODUCT          Jan95      Feb95      Mar95
    -------------- ---------- ---------- ----------
    Tents           32,153.52  32,536.30  43,062.75
    Canoes          66,013.92  76,083.84  91,748.16
    Racquets        52,420.86  56,837.88  58,838.04
    Sportswear      53,194.70  58,913.40  62,797.80
    Footwear        91,406.82  86,827.32 100,199.46

However, the following LIMIT and STATUS commands produce the output shown following them. Again, only Footwear is in the status for `month`.

    LIMIT product TO sales GT 90000
    STATUS product
     
    The current status of PRODUCT is:
    Footwear

In this case, each product has three sales figures, one for each month. For each product, LIMIT evaluates the sales data for only the first month in status. A product is added to the status when its sales data exceeds \$90,000 in that month.

When you would like all months evaluated for each product, you can use the EVERY, ANY, or NONE functions. For example, the following LIMIT statement adds a product to the status when any of its months has a sales figure that exceeds \$90,000.

    LIMIT product TO ANY(sales GT 90000, product)

In this case a `STATUS product` statement produces the following output.

    The current status of product is:
    Canoes, Footwear

Limiting Using Implicit Relations

Every dimension with a type of DAY, WEEK, MONTH, QUARTER, or YEAR is related to all other dimensions of this type through an implicit relation. When you limit the values of one DAY, WEEK, MONTH, QUARTER, or YEAR dimension by specifying another DAY, WEEK, MONTH, QUARTER, or YEAR dimension as the related-dimension, Oracle OLAP uses the implicit relation by default. However, when an explicit relation is defined between the two of these types of dimensions, you can override the default by specifying the name of the explicit relation as the related-dimension. For example, you can issue the following statement.

    LIMIT month TO quarter year

This statement temporarily limits `quarter` to `year`, then limits `month` to `quarter`, and finally, restores `quarter` to its original status.

##### Examples

Example 10-20 Using LIMIT to Partially Populate Variables

    DEFINE GEOG DIMENSION TEXT
    DEFINE PRODUCTS DIMENSION TEXT
    DEFINE SALES VARIABLE DECIMAL <PRODUCTS GEOG>
    DEFINE COSTS VARIABLE DECIMAL <PRODUCTS GEOG>

Assume also as shown by the following reports that you have populated the dimensions but not the variables. All of the elements of the `costs` and `sales` variables appear in the report and all have the value of `NA`.

    PRODUCTS
    ------------
    TVs
    Radios
    Skis
    Bikes

    GEOG
    ------------
    Boston
    Springfield
    New Orleans
    Baton Rouge
    Quebec City
    Montreal
    Toronto
    Norfolk

                 -------------------SALES-------------------
                 -----------------PRODUCTS------------------
    GEOG            TVs       Radios      Skis      Bikes
    ------------ ---------- ---------- ---------- ----------
    Boston               NA         NA         NA         NA
    Springfield          NA         NA         NA         NA
    New Orleans          NA         NA         NA         NA
    Baton Rouge          NA         NA         NA         NA
    Quebec City          NA         NA         NA         NA
    Montreal             NA         NA         NA         NA
    Toronto              NA         NA         NA         NA
    Norfolk              NA         NA         NA         NA

                 -------------------COSTS-------------------
                 -----------------PRODUCTS------------------
    GEOG            TVs       Radios      Skis      Bikes
    ------------ ---------- ---------- ---------- ----------
    Boston               NA         NA         NA         NA
    Springfield          NA         NA         NA         NA
    New Orleans          NA         NA         NA         NA
    Baton Rouge          NA         NA         NA         NA
    Quebec City          NA         NA         NA         NA
    Montreal             NA         NA         NA         NA
    Toronto              NA         NA         NA         NA
    Norfolk              NA         NA         NA         NA


Now you issue the following LIMIT command so that only values indexed by Boston and Springfield values of the geog dimension are accessible to Oracle OLAP.

    LIMIT geog TO 'Boston' 'Springfield'


Now you issue new reports for `geog`, costs, and `sales`. For the `geog` dimension only the Boston and Springfield elements values appear. Also, only the elements of the `costs` and `sales` variables that are indexed by Boston and Springfield appear in the report.

    GEOG
    ------------
    Boston
    Springfield

                 -------------------SALES-------------------
                 -----------------PRODUCTS------------------
    GEOG            TVs       Radios      Skis      Bikes
    ------------ ---------- ---------- ---------- ----------
    Boston               NA         NA         NA         NA
    Springfield          NA         NA         NA         NA

                 -------------------COSTS-------------------
                 -----------------PRODUCTS------------------
    GEOG            TVs       Radios      Skis      Bikes
    ------------ ---------- ---------- ---------- ----------
    Boston               NA         NA         NA         NA
    Springfield          NA         NA         NA         NA


Now you issue two assignment statements that use the RANDOM function to populate the `costs` and `sales` variables, followed by the LIMIT command that sets the status of the geog dimension to its default status of ALL.


    sales = RANDOM (200)
    costs = RANDOM (100)
    LIMIT geog to ALL


Now you issue new reports for `geog`, costs, and `sales`. All of the values of the `geog` dimension and all of the elements of the `costs` and `sales` variables appear. However, only the elements of the `costs` and `sales` variables that are indexed by Boston and Springfield have non-NA values.


    GEOG
    ------------
    Boston
    Springfield
    New Orleans
    Baton Rouge
    Quebec City
    Montreal
    Toronto
    Norfolk

                 -------------------SALES-------------------
                 -----------------PRODUCTS------------------
    GEOG            TVs       Radios      Skis      Bikes
    ------------ ---------- ---------- ---------- ----------
    Boston           199.97     133.82      10.07     148.17
    Springfield      173.94      27.56      32.21      47.40
    New Orleans          NA         NA         NA         NA
    Baton Rouge          NA         NA         NA         NA
    Quebec City          NA         NA         NA         NA
    Montreal             NA         NA         NA         NA
    Toronto              NA         NA         NA         NA
    Norfolk              NA         NA         NA         NA

                 -------------------COSTS-------------------
                 -----------------PRODUCTS------------------
    GEOG            TVs       Radios      Skis      Bikes
    ------------ ---------- ---------- ---------- ----------
    Boston            43.52      25.32      68.68      10.38
    Springfield        9.49      27.96      61.76      16.12
    New Orleans          NA         NA         NA         NA
    Baton Rouge          NA         NA         NA         NA
    Quebec City          NA         NA         NA         NA
    Montreal             NA         NA         NA         NA
    Toronto              NA         NA         NA         NA
    Norfolk              NA         NA         NA         NA

Example 10-21 Limiting with a Boolean Expression

You can limit a dimension or valueset according to the values of a Boolean expression. In this example, the values of the TOTALL function are broken out by `product` and compared to a constant. The LIMIT statement sets the status to all the products whose sales, totaled for all months and districts, are greater than 12 million.

    LIMIT product TO TOTAL(sales product) GT 12000000

Example 10-22 Limiting with a Formula

When you use the same criterion frequently to limit a dimension, you can save the expression as a formula and use the name of the formula as the limit expression.

    DEFINE criterion FORMULA TOTAL(sales product) GT 12000000
    LIMIT product TO criterion

Example 10-23 Limiting with a Valueset

You can save a status list in a valueset and use those values later to limit the status. When it takes several LIMIT commands to produce the status list you want, the valueset keeps you from having to repeat those LIMIT commands each time you need the same list. The following statements limit `district` to the districts in which sportswear sales exceeded \$1,000,000 in 1996. The status is saved in the valueset `sports.district`, and you can limit `district` to the same list with one LIMIT statement.

    DEFINE sports.district VALUESET district
    LIMIT product TO 'Sportswear'
    LIMIT month TO year 'Yr96'
    LIMIT sports.district TO TOTAL(sales district) GT 1000000
    LIMIT district TO sports.district

Issuing a `STATUS district` statement produces this output.

    The current status of DISTRICT is:
    ATLANTA TO DENVER

Example 10-24 Limiting with a Variable

Here the TOP and BASEDON keywords are used to limit the status of a dimension, using the values of a variable as a criterion. The status list is sorted in descending order according to the values of `sales`.

    LIMIT product TO 'Sportswear'
    LIMIT month TO 'Jul96'
    LIMIT district TO TOP 2 BASEDON sales

The following REPORT statement

    REPORT DOWN district sales

produces this output, which shows the results of the LIMIT commands.

    PRODUCT: SPORTSWEAR
                   --SALES---
                   --MONTH---
    DISTRICT         Jul96
    -------------- ----------
    Dallas         220,416.81
    Atlanta        211,666.14

Example 10-25 Limiting a Conjoint Dimension with a Concat Base Dimension

Assume that your analytic workspace contains a conjoint dimension named `prod.regdist` that has the `product` simple dimension and the `reg.dist.ccdim` concat dimension as its base dimensions. The conjoint dimension `prod.regdist` has the following values.

    Tents   <region: East>
    Tents   <region: West>
    Canoes  <region: East>
    Canoes  <region: West>
    Tents   <district: Boston>
    Tents   <district: Atlanta>
    Tents   <district: Denver>
    Canoes  <district: Atlanta>
    Canoes  <district: Seattle>

There are two different ways that you can set the status of a conjoint dimension that has a concat dimension as a base dimension:

- By specifying the concat dimension, one of its component dimensions, and a value of the component dimension. The following LIMIT statement sets the status of `prod.regdist` in this manner.

      LIMIT prod.regdist TO reg.proddist.ccdim district 'Atlanta'
      RPR W 20 prod.regdist

  The preceding statement produces the following output.

      --------------PROD.REGDIST---------------
            PRODUCT           REG.DIST.CCDIM
      -------------------- --------------------
      Tents                <district: Atlanta>
      Canoes               <district: Atlanta>

- You can also set the status of the conjoint by specifying its values. The following LIMIT statement sets the status of `prod.regdist` in this manner.

      LIMIT prod.regdist TO <'Tents' '<region: East>'> <'Tents' '<district: Boston>'>
      RPR W 20 prod.regdist

  The preceding statement produces the following output.

      --------------PROD.REGDIST---------------
            PRODUCT           REG.DIST.CCDIM
      -------------------- --------------------
      Tents                <region: East>
      Tents                <district: Boston>

#### 10.9.2 LIMIT using LEVELREL command

A LIMIT command that uses only dimension values that are at the same level as the current level of the hierarchical dimension or dimension surrogate when setting status or assigning values to a valueset.

##### Syntax

LIMIT {dimension \| valueset} \[concat-component\] limit-type-

     LEVELREL level-relation-clause \[IFNONE label\]

where the syntax of `level-relation-clause` varies depending on the dimensionality of the object you want to specify:

- To specify a level relation which is multidimensional you use the following syntax:

  RELATION level-relation-name \[QUALIFY relation-dimension-name \[inclusive-val-args...\]...\]

  (You can also use this syntax when the level relation is one-dimensional.)

- To specify a level relation which is one-dimensional, you can use the following simplified syntax:

   level-relation-name \[valueset2\]   

##### Parameters

dimension
The name of the dimension or dimension surrogate for which you are setting status.

valueset
The name of the valueset for which you are assigning values; or a [LIMIT function](olap-dml-functions-l-z.md).

concat-component
The name of the component of the concat dimension whose values are used to determine the limit. (See the main entry for LIMIT command for complete description of this argument.)

limit-type
A keyword that specifies how Oracle OLAP should modify the current status list. (See the main entry for LIMIT command for a list and descriptions of these keywords.)

LEVELREL
Sets the status of a hierarchical dimension to all of the values of the hierarchical dimension that are at the same level as the current value of the dimension; or, that limits a hierarchical dimension to those values of the hierarchical dimension that are at the same level as the current value of the dimension and that are also in a specified valueset.

RELATION
Specifies that Oracle OLAP performs the limit based on the values of the relation specified by level-relation-name. Specify this keyword if level-relation-name is a multidimensional relation.

level-relation-name
Specifies the name of a level relation for the hierarchical dimension you want to limit. See "[Levelrel Relation](olap-dml-basic-concepts.md)" for more information.

QUALIFY relation-dimension-name \[inclusive-val-args\]
Identifies the values by which Oracle OLAP performs the limit.

- `relation-dimension-name` is the name of a dimension of the relation specified by level-relation-name.

- `inclusive-val-args` specifies the values of relation-dimension-name to use when determining the values of level-relation-name by which to perform the limit. You can specify any inclusivevaluelist argument as described in the syntax of the inclusive-val-args argument for the valuelist clause for LIMIT command. (See LIMIT (using values) command for detailed syntax.) When you omit this argument, Oracle OLAP uses the current status of the dimension when performing the limit.

valueset2
Specifies the name of a valueset object is dimensioned by the level dimension for the hierarchical dimension that you want to limit. The result of using this argument is the individual valueset that corresponds to the level value of the current position of the dimensions.

You can also specify a[LIMIT function](olap-dml-functions-l-z.md).

IFNONE label
Specifies that program execution should branch to label when the requested status has null status or is based on a related dimension that turns out to have null status (that is, to have no values). (See the main entry for LIMIT command for complete description of this phrase.)

##### Examples

Example 10-26 Limiting to a Single Time Period of a Hierarchical Time Dimension

Assume that you have defined a hierarchical text dimension named `time`, a level dimension named `timelevels` that has `Month` and `Year` as values, and a relation named `timelevelsrel` that is dimensioned by `time` and that has `timelevels` as a related dimension (that is, for each value of the `time` dimension, `timelevelsre` contains a value of either `Month` or `Year`) When you want to limit the values of `time` that are already in status to only those values that are at the same level as `Jan99`, you can issue the following statement.

    LIMIT time TO LEVELREL timelevelsrel

This is equivalent to issuing the following statement

    LIMIT time TO RELATION timelevelsrel QUALIFY time CURRENT

#### 10.9.3 LIMIT (using related dimension) command

A LIMIT command with a related-dimension limit clause that uses the values of a different related dimension to assign values to a valueset or to set the status of a dimension or a dimension surrogate.

##### Syntax

LIMIT {dimension \| valueset} limit-type related-dim-clause \[IFNONE label\]

where the syntax of `related-dim-clause `varies depending on the type of object being specified:

- When you want to specify a relation, the syntax is:

  RELATION relation-name \[QUALIFY relation-dimension-name \[inclusive-val-args...\]...\]

- When you want to specify a dimension that is related to the dimension being limited, the syntax is:

   related-dimension-name \[related-dimension-valuelist\]   

  (You can also use this simplified syntax when the object is a one-dimensional relation.)

##### Parameters

dimension
The name of the dimension or dimension surrogate for which you are setting status.

valueset
The name of the valueset for which you are assigning values; or a [LIMIT function](olap-dml-functions-l-z.md).

concat-component
The name of the component of the concat dimension whose values are used to determine the limit. (See the main entry for LIMIT command for complete description of this argument.)

limit-type
A keyword that specifies how Oracle OLAP should modify the current status list. (See the main entry for LIMIT command for a list and descriptions of these keywords.)

RELATION relation-name
Specifies that Oracle OLAP performs the limit based on the values of the relation specified by relation-name. Specify this keyword if relation-name is a multidimensional relation. Also, when there are multiple relations between the dimension being limited and the dimension specified by related-dimension-name, you can use this phrase to identify which relation Oracle OLAP uses to perform the limit.

QUALIFY relation-dimension-name \[inclusive-val-args\]
Identifies the values by which Oracle OLAP performs the limit, where:

- `relation-dimension-name` is the name of a dimension of the relation specified by relation-name.

- `inclusive-val-args` specifies the values of relation-dimension-name to use when determining the parent values. You can specify any inclusivevaluelist argument as described in the syntax of the inclusive-val-args argument for the valuelist clause for LIMIT command. See LIMIT (using values) command for detailed syntax. When you omit this argument, Oracle OLAP uses the current status list of the related dimensions when performing the limit.

related-dimension-name
Specifies the name of a one-dimensional relation or a dimension that is related to the dimension being limited. For related-dimension-name, you can also specify a dimension surrogate for the dimension you are limiting, or a dimension surrogate of the related dimension. For example, `dimsurr` is a dimension surrogate of `dim2` and `dim2` is related to `dim1`. The dimension surrogate `dimsurr` has the values `Dsv1`, `Dsv2`, `Dsv3` and `Dsv4`. The following statement limits `dim1` by specifying values of `dimsurr`.

    LIMIT dim1 TO dimsurr dsv1 dsv3

related-dimension-valuelist
The values of the related dimension or a dimension surrogate for the related dimension or the dimension specified using the syntax shown in LIMIT command. See LIMIT (using values) command for detailed syntax. When this argument is present in a LIMIT statement, status is obtained by selecting the values of the dimension being limited, which are related to the related-dimension values. When valuelist is omitted, the current status value of related-dimension is used.

IFNONE label
Specifies that program execution should branch to label when the requested status has null status or is based on a related dimension that turns out to have null status (that is, to have no values). (See the main entry for LIMIT command for complete description of this phrase.)

##### Usage Notes

Limiting to a Related Dimension Is a Two-Step Process

When you limit a dimension or valueset to a related dimension, the resulting status is determined in a two-step process:

1.  The dimension values are arranged in the order of the values of the related dimension.

2.  When there are multiple values of the dimension for any value of the related dimension, those values are arranged in the order of their default status.

Suppressing the Sort When Limiting to a Related Dimension

You can suppress the sort that occurs when you limit a dimension or valueset to a related dimension by setting LIMITSORTREL to `NO` which can significantly improve performance when the dimension you are limiting is large.

**Note:**

When LIMIT.SORTREL is `NO`, printed output of a dimension may not appear in logical order.

##### Examples

Example 10-27 Limiting with a Related Dimension

Here the status of a dimension is limited using a related dimension. This statement limits `district` to `Boston` and `Atlanta`, which are in the `East` region.

    LIMIT district TO region 'East'

This statement limits `product` to `Sportswear` and `Footwear`, which are in the division that appears last in the list of `division` values.

    LIMIT product TO division LAST 1

#### 10.9.4 LIMIT (using parent relation)

A LIMIT command that uses a parent relation in its limit clause to set the status of a hierarchical dimension or its dimension surrogate, or assigns values to a valueset, based on family relationships within the hierarchy.

**See:**

"Looping Behavior of LIMIT (using parent relation)"

##### Syntax

LIMIT {dimension \| valueset} \[concat-component\] limit-type-

     \[family-keyword \] USING parent-relation-clause \[IFNONE label\]

where:

- `family-keyword` has one of the following constructs:

  -      `PARENTS`
  -      `CHILDREN`
  -       `ANCESTORS` `[DISTANCE` `generation`` ]`
  -       `DESCENDANTS` `[DISTANCE` `generation`` ]`
  -       `SIBLINGS`
  - `TOPANCESTORS`
  - `BOTTOMDESCENDANTS`
  -       `HIERARCHY [INVERTED] [NOORIGIN] [SKIP` `n``] [DEPTH ``n``] [RUN ``textexp``]] `
  -

- The syntax for `parent-relation-clause `varies depending on its dimensionality of the object you want to specify:

  - When the parent relation is multidimensional, use the following syntax:

    RELATION parentrel \[QUALIFY relation-dimension-name \[inclusive-val-args... \| CURRENT\]...\]

    (You can also use this syntax when the parent relation is one-dimensional.)

  - When the parent relation is one-dimensional, you can use the following simplified syntax:

     parentrel \[inclusive-val-args \| CURRENT\] 

##### Parameters

dimension
The name of the dimension or dimension surrogate for which you are setting status.

valueset
The name of the valueset for which you are assigning values; or a [LIMIT function](olap-dml-functions-l-z.md).

concat-component
The name of the component of the concat dimension whose values are used to determine the limit. (See the main entry for LIMIT command for complete description of this argument.)

limit-type
A keyword that specifies how Oracle OLAP should modify the current status list. (See the main entry for LIMIT command for a list and descriptions of these keywords.)

PARENTS
Finds the parent of each value in valuelist. For a dimension, when there is no valuelist, finds the parent for each value in status. For a valueset, when there is no valuelist, it finds the parent of each value in the valueset. It uses the parent-relation to look up the parent.

CHILDREN
Finds the children of each value in valuelist. For a dimension, when there is no valuelist, finds the children for each value in status. For a valueset, when there is no valuelist, it finds the children of each value in the valueset. It uses the parent-relation to look up the children.

ANCESTORS \[DISTANCE generation\]
When you do not include the DISTANCE phrase:

- Finds the ancestors (that is, parents, grandparents, and so on) of each value in valuelist. For a dimension, when there is no valuelist, it finds the ancestors of each value in status.

- For a valueset, when there is no valuelist, it finds the ancestors of each value in the valueset. In other words it finds "parents" for the values and the "parents of the parents" until there are no new parents.

When you include the DISTANCE phrase, limits to the ancestors who are members of the generation specified by generation:

- For generation, specify 0 for the current generation, 1 for parents, 2 for grandparents, 3 for great grandparents, and so on.

- For negative values, the command returns descendant generations (that is -1 returns children, -2 returns grandchildren, and so on).

DESCENDANTS \[DISTANCE generation\]
When you do not include the DISTANCE phrase:

- Finds the descendants (that is, children, grandchildren, and so on) of each value in valuelist. For a dimension, when there is no valuelist, it finds descendants for each value in status.

- For a valueset, when there is no valuelist, it finds the descendants of each value in the valueset. In other words, it finds the children of the values and the children of the children until there are no new children.

When you include the DISTANCE phrase, limits to the descendants who are members of the generation specified by generation:

- For generation, specify 0 for the current generation, 1 for children, 2 for grandchildren, 3 for great grandchildren, and so on.

- For negative, the command returns ancestor generations (that is -1 returns parents, -2 returns grandparents, and so on).

SIBLINGS
Finds all siblings of each value in valuelist, including the valuelist values, themselves. Issuing one LIMIT statement with the SIBLIGS keyword is the same as issuing two consecutive LIMIT statements: 1) LIMIT with PARENTS, 2) LIMIT with CHILDREN. For a dimension, when there is no valuelist, it finds siblings for each value in status. For a valueset, when there is no valuelist, it finds the siblings of each value in the valueset.

TOPANCESTORS
(Abbreviated TOPANC) Finds those members that are at the top of the hierarchy; that is, those members that do not have any ancestors which is equivalent to issuing the following two LIMIT commands.

       LIMIT dimension to ANCESTORS ....
       LIMIT dimension REMOVE DESCENDANTS....

BOTTOMDESCENDANTS
(Abbreviated BOTTOMDESC) Finds those members that are at the bottom of the hierarchy; that is, those members that do not have any descendants.

HIERARCHY
Finds the descendants (that is, children, grandchildren, and so on) based on a particular parent-relation. The difference is the order of the values. DESCENDANTS groups the values by level (all children, then all grandchildren, and so on); HIERARCHY places each group of children next to its parent. HIERARCHY includes the original values (that is, those in status before the LIMIT statement was executed) in status.

INVERTED
Indicates that children should be listed before their parents. By default, children are listed after their parents.

NOORIGIN
Excludes the original values from the status. The default is to include original values.

SKIP
Skips n generations for each value in valuelist. For dimensions, when there is no valuelist, it skips n generations for each value in status. For a valueset, when there is no valuelist, it skips n generations for each value in the valueset. This keyword, in combination with DEPTH, is helpful when drilling down; see Example 10-29.

DEPTH
Includes n generations down from each value of valuelist. For dimensions, when there is no valuelist, it includes n generations for each value in status. For a valueset, when there is no valuelist, it includes n generations of each value in the valueset. The default depth value is 99. This keyword, in combination with SKIP, is helpful when drilling down on values.

RUN
Executes a statement, represented as a text expression, every time a group of children is constructed. For example, you can sort each group of children based on information stored in an Oracle OLAP variable. In the following statement, markets are sorted in increasing order based on unit sales every time a group of children is constructed.

    LIMIT market TO HIERARCHY RUN 'SORT market a unit.m' USING -

      market.market

**Note:**

In this example, when you use KEEP or REMOVE instead of TO in your LIMIT statement, the SORT statement would have no effect.

USING 
Specifies the values to use when determining parent values.

parentrel
Specifies the name of the parent relation for the dimension.

**See Also:**

"[Parentrel Relation](olap-dml-basic-concepts.md)" and "Looping Behavior of LIMIT (using parent relation)"

To limit a dimension surrogate, use the parent relation for the dimension for which it is a surrogate.

RELATION  
Identifies the beginning of the parent-relation-clause. You use this keyword when parentrel is a multidimensional relation.

QUALIFY relation-dimension-name 
Specifies the name of a dimension of parentrel. The use of this clause varies depending on whether you are coding a LIMIT command or a LIMIT function as described in "Looping Behavior of LIMIT (using parent relation)".

inclusive-val-args
Specifies the values to use when determining the parent values. You can specify any inclusivevaluelist argument as described in the syntax of the inclusive-val-args argument for the valuelist clause for LIMIT command. See LIMIT (using values) command for detailed syntax.

CURENT
Specifies that you want to limit to the values of the children of the current value of the dimension. (This is the same as specifying `dimension_name` `+0`.)

IFNONE label
Specifies that program execution should branch to label when the requested status has null status or is based on a related dimension that turns out to have null status (that is, to have no values). (See the main entry for LIMIT command for complete description of this phrase.)

##### Usage Notes

Looping Behavior of LIMIT (using parent relation)

When you do not include a QUALIFY clause, the set of values that this LIMIT puts into status when parentrel is multi-dimensional varies depending on whether or not you are issuing a LIMIT command or a LIMIT function:

- LIMIT command. All of the in-status values of the related dimensions of parentrel are included in the set of in-status values. If you only want the current values of the related dimensions of parentrel to be included in the set of in-status values, specify a QUALIFY related-dimension CURRENT clause for each of the related dimensions of parentrel.

- LIMIT function. Only the current values of the related dimensions of parentrel are included in the set of in-status values. If you want all of the in-status values of the related dimensions of parentrel to be included in the set of in-status values, specify a QUALIFY related-dimension related-dimension clause for each of the related dimensions of parentrel.

##### Examples

Example 10-28 A Simple Drill Down

This example drills down on districts from the region level of the market dimension. First, the market dimension, which has embedded totals at the district, region, and total U.S. level, is limited to the region level data. This LIMIT is done using the relation `mlv.market`, which is a relation between `marke`t and `market.level`.

Issuing a `REPORT mlv.market` statement produces the following output, which shows the values of `mlv.market`.

    MARKET         MLV.MARKET
    -------------- ----------
    Totus          Totus
    East           Region
    Boston         District
    Atlanta        District
    Central        Region
    Chicago        District
    Dallas         District
    West           Region
    Denver         District
    Seattle        District

The following LIMIT statement limits the values of `MARKET`, and the STATUS statement produces the values currently in status. The output of STATUS is shown following the statements.

    LIMIT market TO mlv.market 'Region'
    STATUS market
     
    The current status of MARKET is:
    EAST, CENTRAL, WEST

To drill down on the district level data from the region level, you can use LIMIT with the CHILDREN keyword. The following example uses a parent-relation called `market.market` to perform the drill down. For each value of the `market` dimension, this relation contains the name of its parent.

    DEFINE market.market RELATION market <market>
    LD Self-relation for the Market Dimension

A report of `market.market` produces the following output.

    MARKET         MARKET.MARKET
    -------------- -------------
    Totus          NA
    East           Totus
    Boston         Central
    Atlanta        East
    Central        Totus
    Chicago        Central
    Dallas         Central
    West           Totus
    Denver         West
    Seattle        West

You can limit `market` to the children of the `East`, `Central`, and `West` regions by using the CHILDREN keyword with LIMIT.

    LIMIT market TO mlv.market 'Region'
    Limit market TO CHILDREN USING market.market

A report of `market` produces the following output.

    MARKET
    -------------
    Boston
    Atlanta
    Chicago
    Dallas
    Denver
    Seattle

Example 10-29 Drilling Down Using SKIP and DEPT

Consider the following statement.

    LIMIT market TO HIERARCHY DEPTH 2 SKIP 1 USING market.market 'Totus'

Oracle OLAP looks in the child-parent relation (`market.market`) to find the children and the grandchildren (`DEPTH 2`) of `Totus `and it discards the first generation (`SKIP 1`). The resulting status follows.

    Totus
    Boston
    Atlanta
    Chicago
    Dallas
    Denver
    Seattle

Note that `Totus` is included in status. With HIERARCHY, the original values are included in status.

#### 10.9.5 LIMIT NOCONVERT command

The LIMIT command sets the current status list of a dimension and its dimension surrogates, or assigns values to a valueset.

A LIMIT command with the NOCONVERT keyword sets the status of one dimension based on the numeric position of values in a different dimension.

##### Syntax

LIMIT{dimension \| valueset} \[concat-component\] limit-type -

     NOCONVERT \[{unrelated-dimension\|numeric-valueset}\] -      \[IFNONE label\]

##### Parameters

dimension
The name of the dimension or dimension surrogate for which you are setting status.

valueset
The name of the valueset for which you are assigning values; or a [LIMIT function](olap-dml-functions-l-z.md).

concat-component
The name of the component of the concat dimension whose values are used to determine the limit. (See the main entry for LIMIT command for complete description of this argument.)

limit-type
A keyword that specifies how Oracle OLAP should modify the current status list. (See the main entry for LIMIT command for a list and descriptions of these keywords.)

NOCONVERT
Sets the status of a dimension based on the numeric position of the specified values in the status list of an another dimension.

unrelated-dimension
Specifies the name of a dimension not related to the dimension being limited. Using this argument specifies that the status of a dimension or valueset is set based on the numeric position of each value in status of the unrelated-dimension. Setting status based on in status values in unrelated dimensions is particularly useful when the two dimensions are in different analytic workspaces (for example, when a one-to-one correspondence exists between the product dimension in two analytic workspaces).

numeric-valueset
Specifies a numeric valueset. When you use this argument, NOCONVERT sets the status based on the numeric values in the valueset. The numeric values represent the positions of the values in the default status of the dimension.

IFNONE label
(For use only within an OLAP DML program) Specifies that program execution should branch to label when the requested status has null status or is based on a related dimension that turns out to have null status (that is, to have no values). (See the main entry for LIMIT command for complete description of this phrase.)

#### 10.9.6 LIMIT command (using POSLIST)

The LIMIT command sets the current status list of a dimension and its dimension surrogates, or assigns values to a valueset.

A LIMIT command with the POSLIST keyword sets the status of a dimension based on the position of the values within that dimension.

##### Syntax

LIMIT {dimension \| valueset} \[concat-component\] limit-type -

     POSLIST poslist-exp \[IFNONE label\]

##### Parameters

dimension
The name of the dimension or dimension surrogate for which you are setting status.

valueset
The name of the valueset for which you are assigning values; or a [LIMIT function](olap-dml-functions-l-z.md).

concat-component
The name of the component of the concat dimension whose values are used to determine the limit. (See the main entry for LIMIT command for complete description of this argument.)

limit-type
A standard keyword (documented in the main entry for LIMIT command) that specifies how Oracle OLAP should modify the current status list.

POSLIST poslist-textexp
Sets the status of a dimension based on the position of a value within a dimension. poslist-textexp is a text expression, each line of which is a numeric value that evaluates to a numeric position of the dimension being limited.

IFNONE label
Specifies that program execution should branch to label when the requested status has null status or is based on a related dimension that turns out to have null status (that is, to have no values). (See the main entry for LIMIT command for complete description of this phrase.)

### 10.10 LIMIT BASEDIMS

The LIMIT BASEDIMS command sets the current status list of one or more base dimensions of a composite, conjoint dimension, concat dimension, or a partition template based on the selected values of that object.

You use LIMIT BASEDIMS to produce a status of dimension values for each dimension that exists in the sparse object's tuples, possibly filtered by some arbitrary input status. You can also use the this command to assign a value to one or more valuesets for the base dimensions.

Values that are in the current status list of a dimension are said to be "in status." The status of the base dimensions of a composite, conjoint dimension, concat dimension, or a partition template is determined by the current status of its base dimensions.

**See Also:**

For more information on working with dimension status, see "[OLAP DML Statements Apply to All of the Values of a Data Object](olap-dml-basic-concepts.md)" and LIMIT command

#### Syntax

LIMIT BASEDIMS {\<dimlist\>}TO object \[ \[KEEP\] limit-clause \]

#### Parameters

dimlist
A space-delimited list of objects that identifies the base dimensions for which you want Oracle OLAP to change status and the valuesets for which you want Oracle OLAP to add values. Within dimlist, you can specify the following values:

- `base-dimension-name`
- The name of a base dimension of object.
- `relation-name`
- The name of a relation. When you specify a relation, Oracle OLAP sets the status of the related dimension.
- `valueset-name`
- The name of a valueset for a base dimension; or a [LIMIT function](olap-dml-functions-l-z.md). When you specify the name of a valueset, Oracle OLAP assigns a single value to the specified valueset.

The default value of dimlist is the completely expanded list of the base dimensions of object.

object
The name of a composite, a conjoint dimension, a concat dimension, or a partition template object.

KEEP
Specifies that Oracle OLAP performs the selection based on the current dimension status of the base dimensions of the object. KEEP preserves the current order of values among the values that remain in the status.

limit-clause
Specifies how Oracle OLAP should select values from object to modify the current status lists of the base dimensions.

The syntax of limit-clause is the same syntax as any of the non-positional limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see LIMIT (using values) command, LIMIT using LEVELREL command, LIMIT (using parent relation), LIMIT (using related dimension) command, LIMIT NOCONVERT command, and LIMIT command (using POSLIST).

When this optional argument is not specified, Oracle OLAP sets the status of the base dimensions to the current status of the dimensions.

### 10.11 LISTBY

The LISTBY program produces a report of the names of all objects in an analytic workspace that are dimensioned by or related to one or more specified dimensions or composites. You can use LISTBY with a dimension or composite in any attached workspace.

#### Syntax

LISTBY dimensions

#### Parameters

dimensions
A list of one or more dimensions or composites, separated by spaces. When you list multiple dimensions, all the dimensions must be in the same workspace. LISTBY returns a list of objects that are dimensioned by all the dimensions you specify. When you specify an unnamed composite, use the following format:

LISTBY SPARSE dim1 dim2 ...

#### Usage Notes

Composites and Conjoint Dimensions

The report produced by LISTBY includes any named or unnamed composite, or conjoint dimension, whose base dimension list includes the dimensions you specify.

The report also includes any object whose dimension list includes a named or unnamed composite that in turn has the specified dimensions as base dimensions.

#### Examples

Example 10-30 Using LISTBY

LISTBY is used here to list the name of every object that is dimensioned by or related to `product`. The statement `LISTBY product `produces the following output.

    15 objects dimensioned by or related to PRODUCT
    ----------------------------------------------------------------
    ADVERTISING          DIVISION.PRODUCT     EXPENSE
    INDUSTRY.SALES       NAME.PRODUCT         NATIONAL.SALES
    PRICE                PRODUCT.MEMO         PRODUCTSET
    SALES                SALES.FORECAST       SALES.PLAN
    SHARE                UNITS                UNITS.M

Example 10-31 Specifying More Than One Dimension

In this example LISTBY is used to list the name of every object that is dimensioned by or related to both `product` and `market`.

    LISTBY product market

    1 objects dimensioned by or related to PRODUCT, MARKET
    ----------------------------------------------------------
    UNITS.M

### 10.12 LISTFILES

The LISTFILES command lists all the open files that can be referenced by the FILEQUERY function which includes all files opened by FILEOPEN, OUTFILE, and LOG command.

#### Syntax

LISTFILES

#### Examples

Example 10-32 Listing Open Files

The following example shows how to use LISTFILES to see which open files can be referenced by the FILEQUERY function.

    DEFINE fil.unit VARIABLE INTEGER
    fil.unit = FILEOPEN('report' WRITE)
    LISTFILES

These statements produce the following output.

    10 w  D:\WINNT35\SYSTEM32\report

### 10.13 LISTNAMES

The LISTNAMES program produces a report that lists the names of the objects in an analytic workspace. You can limit the list to particular types of objects, and you can have the names for each type of object listed in alphabetical order.

#### Syntax

LISTNAMES \[AW workspace\|'\*'\] \[objtype-list\|ALL\] -      \[SORTED\|UNSORTED\] \[LIKE 'pattern'\]

#### Parameters

AW workspace
AW '\*'
Specifies the name of an attached workspace whose objects you want to list. When you omit the workspace name, LISTNAMES lists the objects in the current workspace. When you use the `'*'` (asterisk) argument instead of an analytic workspace name, LISTNAMES produces a separate report for each attached workspace.

objtype-list
ALL
Specifies one or more of the following types of objects whose names you want to list: AGGMAP, COMPOSITE, DIMENSION, FORMULA, MODEL, OPTION, PROGRAM, RELATION, VALUESET, VARIABLE, and WORKSHEET. You can include a trailing "S" on any object type, for example, `DIMENSIONS`. You can list these object types in any order. ALL (the default) specifies that the names of objects of all these types should be listed.

SORTED
UNSORTED
SORTED (the default, abbreviated SORT) specifies that the object names should be sorted alphabetically. UNSORTED (abbreviated UNSORT) specifies that the object names should not be sorted alphabetically.

LIKE 'pattern'
Compares the names of the definitions in an analytic workspace to the text pattern you specify and lists the names that match. A definition name is like a text pattern when corresponding characters match. Besides literal matching, LIKE lets you use wildcard characters to match multiple characters in a string. An underscore (`_`) character in a pattern matches any single character. A percent (`%`) character in a pattern matches zero or more characters.

#### Usage Notes

NAME Dimension

NAME is a special dimension that is used by Oracle OLAP to organize the list of objects in an analytic workspace. Its values are the names of the objects defined in the current workspace. (

You cannot explicitly change the values of the NAME dimension. Instead the values are changed as DEFINE, DELETE, MOVE, or RENAME statements execute. Also, you cannot use a qualified object name to specify the NAME dimension of an analytic workspace that is not the current workspace.

**See Also:**

LISTNAMES program

Example 10-33 Listing Dimensions

Suppose you want a list of all the dimensions in an analytic workspace. First, use a LIMIT command and the OBJ function to limit the status of the NAME dimension. Then use a STATUS statement to produce a list of dimensions. Because the values returned by `OBJ(TYPE)` are always in uppercase, you must use `'DIMENSION'` (not `'dimension'`) in the LIMIT statement to get a match. The statements

    LIMIT NAME TO OBJ(TYPE) EQ 'DIMENSION'
    STATUS NAME

produce the following output.

    The current status of NAME is:
    PRODUCT, DISTRICT, DIVISION, LINE, REGION, MARKETLEVEL, MARKET,
    MONTH, YEAR, QUARTER

Example 10-34 Listing Relations

Suppose you want to see the definitions of all the relations in an analytic workspace. Use the LIMIT command and the OBJ function to select these names. Then use DESCRIBE to produce a list of their definitions. The statements

    LIMIT NAME TO OBJ(TYPE) EQ 'RELATION'
    DESCRIBE

produce the following output.

    DEFINE REGION.DISTRICT RELATION REGION <DISTRICT>
    LD REGION for each DISTRICT
     
    DEFINE DIVISION.PRODUCT RELATION DIVISION <PRODUCT>
    LD DIVISION for each PRODUCT
     
    DEFINE MLV.MARKET RELATION MARKETLEVEL <MARKET>
     
    DEFINE MARKET.MARKET RELATION MARKET <MARKET>
    LD Self-relation for the Market Dimension

#### Examples

Example 10-35 Listing of DEMO Workspace Objects

This example lists the dimensions, variables, and relations in the current workspace. The statement

    LISTNAMES dimension variable relation

produces the following output for the DEMO workspace.

    10 DIMENSIONs      18 VARIABLEs       4 RELATIONs
    ----------------   ----------------   ----------------
    DISTRICT           ACTUAL             DIVISION.PRODUCT
    DIVISION           ADVERTISING        MARKET.MARKET
    LINE               BUDGET             MLV.MARKET
    MARKET             DEMOVER            REGION.DISTRICT
    MARKETLEVEL        EXPENSE
    MONTH              FCST
    PRODUCT            INDUSTRY.SALES
    QUARTER            NAME.LINE
    REGION             NAME.PRODUCT
    YEAR               NATIONAL.SALES
                       PRICE
                       PRODUCT.MEMO
                       SALES
                       SALES.FORECAST
                       SALES.PLAN
                       SHARE
                       UNITS
                       UNITS.M

### 10.14 LOAD

The LOAD command loads the definition of a program, formula, or model into memory. It is usually used in startup programs, to save time when a program is first used in a session.

#### Syntax

LOAD object. . .

#### Parameters

object. . .
The name of a program, formula, or model.

#### Usage Notes

Definitions Loaded on First Use

All of the objects in an analytic workspace (except for programs, formulas, and models) are loaded into memory when the analytic workspace is attached. Programs, models, and formulas are loaded into memory when first used or when requested using the LOAD command. The time required for loading is small but perceptible, and an application builder fine-tuning a system might want to preload objects in a startup program so that the application runs up to speed from the beginning of a session.

Effect of Loading Many Objects

Loading too many objects into memory can cause Oracle OLAP to run out of memory when it processes a long statement. It is best to use LOAD sparingly, choosing the objects for maximum effect.

LOAD Does Not Compile Programs

When a program is not compiled, LOAD does not automatically compile it. For best performance, always compile the program and save the compiled code by updating your workspace. Then when you load the program in another session (for example, with an AUTOGO program), the program is ready to run. See the [COMPILE](olap-dml-commands-a-g.md) command for more information about compilation.

#### Examples

Example 10-36 Loading Two Programs

The following statement loads the two programs `choose.months `and `sales.rpt`.

    LOAD choose.months sales.rpt

Example 10-37 Loading All the Programs in an analytic workspace

The following statements load all the programs in the analytic workspace.

    LIMIT NAME TO OBJ(TYPE) EQ 'program'
    LOAD &VALUES(NAME)

### 10.15 LOG command

The LOG command starts or stops the recording of a session to a disk file. All lines of input and output are recorded.

**Note:**

Do not confuse the LOG command with the function of the same name which is a mathematical function.

#### Syntax

LOG EOF \| TRACEFILE \| SAVE \| {\[APPEND\] file-name}

#### Parameters

EOF
Stops recording of the session and closes any opened log record file.

TRACEFILE
Specifies that the session information should be directed to the Oracle trace file, which is identified by the TRACEFILEUNIT option.

SAVE
Forces Oracle OLAP to update the log file. Lines of input and output are not always written to disk as they are generated. Instead, the lines are stored temporarily then written to disk periodically. `LOG` `SAVE` effectively issues the `LOG` `EOF` and `LOG APPEND` `file-name` commands which ensures that all appropriate lines are written to disk by closing the log file and reopening it. Additional lines of input and output are appended to the file.

APPEND
Specifies that the record of your session should be added to the end of an existing disk file. When you omit this argument, the new output replaces the current contents of the file.

file-name
A text expression that is the name of the file to which session information should be written. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use a CDA statement to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

#### Usage Notes

Automatic Closing of a Log File

When you use `LOG``file-name` to start recording in a disk file, LOG closes any log record file that is currently open. LOG issues this close even when the new file is not actually opened (as when you specify an invalid file name in the LOG statement).

#### Examples

Example 10-38 Keeping a Log File

To record your session in a file called `session.log`, use a statement like the following.

    LOG 'session.log'

### 10.16 MAINTAIN

The MAINTAIN command enters and maintains the values of dimensions, composites, and partition template objects.

**Note:**

You can also issue a MAINTAIN statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

#### Syntax

MAINTAIN object {ADD\|DELETE\|RENAME\|MOVE\|MERGE} args

The keywords that you can use with the MAINTAIN command varies by object:

- `MAINTAIN ``dimension` `{ADD|DELETE|RENAME|MOVE|MERGE} ``args`

  The keyword that you can use varies by the type of dimension that you want to maintain:

  - With a non-concat dimension, you can use the ADD, DELETE, RENAME, MOVE, or MERGE keywords to add, delete, rename, move, or merge non-concat dimension values. You can also use the ADD keyword to add temporary calculated members to a dimension.

  - With a concat dimension, you can only use the MOVE keyword to move concat dimension values.

- `MAINTAIN` `composite ``{ADD|DELETE|MERGE}`` args`

- `MAINTAIN` `partition-template` `{ADD|DELETE|MOVE}` `args`

The specific syntax varies by keyword. Consequently, there are separate topics for each keyword of the MAINTAIN command:

- MAINTAIN ADD
- MAINTAIN DELETE
- MAINTAIN MERGE
- MAINTAIN MOVE
- MAINTAIN RENAME

For information that applies to the MAINTAIN command in general, see the Usage Notes in this topic.

#### Usage Notes

Triggering Program Execution When MAINTAIN Executes

Using the TRIGGER command, you can make the execution of a MAINTAIN statement an event that automatically executes an OLAP DML program. See "[Trigger Programs](olap-dml-programs.md)" for more information.

Automatic Status Reset

When you use the ADD, DELETE, MERGE, or MOVE keyword to maintain a dimension or composite whose status is not currently ALL, the MAINTAIN command automatically resets status to ALL before performing the maintenance function. However, when you use the RENAME keyword to maintain a dimension whose status is not currently ALL, the MAINTAIN command does not change the status of the dimension.

Maintain Permission

You cannot perform maintenance on a dimension when a PERMIT MAINTAIN statement denies maintain permission for the dimension. Maintain permission is implicitly denied whenever read permission is restricted for a dimension, even when you specify maintain permission for the dimension. (See the PERMIT command.)

Maintaining Dimensions in Multiwriter Analytic Workspaces

Keep the following points in mind when maintaining dimensions in an analytic workspace that is attached in multiwriter mode:

- You cannot update a variable when any of its dimensions have been acquired and modified.

- Reverting a dimension after adding dimension values is not recommended because it can result in suboptimal space allocation for variables dimensioned by the dimension.

- When an acquired variable is dimensioned by an acquired dimension that has been maintained, you cannot update the variable until the dimension is updated or released.

- You do not have to acquire composites in order for them to be maintained, Oracle OLAP automatically performs concurrent dimension maintenance for the composite dimensions.

Also, before you can maintain dimensions in an analytic workspace that is attached in multiwriter mode, you must first acquire the dimension using an ACQUIRE statement.

For example, assume that user A and user B both have to perform what-if computations on both `actuals` and `budget`. After performing the what-if computations, user A needs to modify `actuals` and B needs to modify `budget`. Finally, both user A and user B have to add a new `time` dimension value and add data corresponding to that new dimension value to `actuals` or `budget`.

User A issues the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ...make modifications
    ACQUIRE actuals
    ...make more modifications
    ACQUIRE time
    MAINTAIN time ADD 'Y2002'
    actuals (time 'Y2002', ...) = ...
    UPDATE MULTI actuals, time
    COMMIT
    RELEASE actuals, time
    AW DETACH myworkspace

User B issues the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ...make modifications
    ACQUIRE budget
    ...make more modifications
    ACQUIRE time--> failed
    ACQUIRE RESYNC time WAIT
    MAINTAIN time ADD 'Y2003'
    budget (time 'Y2003', ...) = ...
    UPDATE MULTI budget, time
    COMMIT
    RELEASE budget, time
    AW DETACH myworkspace

MAINTAIN and Dimension Surrogates

You cannot use a MAINTAIN statement on a dimension surrogate. You can only use MAINTAIN to add values to or delete them from a dimension. However, when you add or delete a dimension value, then Oracle OLAP adds or removes a position from surrogates of that dimension. When you add a position to a dimension, the corresponding position in a surrogate for that dimension receives an `NA` value.

Maintaining a Concat Dimension

A concat dimension contains the values of its component dimensions. You do not directly add, merge, or delete the values of a concat dimension using MAINTAIN statements. Instead, when you add, merge, or delete values from a component dimension of the concat, Oracle OLAP automatically adds or deletes the values from the concat dimension. You can use the MOVE keyword of the MAINTAIN command to change the order of the values of a concat dimension.

#### 10.16.1 MAINTAIN ADD

The MAINTAIN command with the ADD keyword adds new TEXT, ID, and INTEGER values to a non-concat dimension, composite, or partition; or adds a new temporary calculated member to a dimension.

**Note:**

You can also issue a MAINTAIN ADD for TEXT, ID, and INTEGER Values statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program one time for each value; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

##### Syntax

The syntax for using the MAINTAIN command with the ADD keyword depends on the type of the object being maintained and whether you are adding a permanent or temporary member.

For this reason, the following separate entries are provided for MAINTAIN ADD:

- MAINTAIN ADD for TEXT, ID, and INTEGER Values

- MAINTAIN ADD for DAY, WEEK, MONTH, QUARTER, and YEAR Values

- MAINTAIN ADD SESSION

- MAINTAIN ADD TO PARTITION

##### 10.16.1.1 MAINTAIN ADD for TEXT, ID, and INTEGER Values

The MAINTAIN command with the ADD keyword adds new TEXT, ID, or INTEGER values to a non-concat dimension or composite.

**Note:**

You can also issue this MAINTAIN ADD statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program one time for each value in valuelist; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

##### Syntax

MAINTAIN composite\|dimension ADD valuelist \[FIRST\|LAST\|BEFORE position\|AFTER position\]

##### Parameters

dimension
A non-concat dimension, already defined in an attached analytic workspace.

composite
A composite. When the composite is a named composite, it must be defined in an attached analytic workspace. When the composite is unnamed, it must have been used in defining an object in an attached analytic workspace. Use the SPARSE keyword to refer to an unnamed composite (for example, `SPARSE <market product>`).

ADD valuelist
Specifies that the values in valuelist are to be added to the dimension or composite:

- When you use this argument to add values to a composite or a dimension of type TEXT or ID, the valuelist can be text literals or a TEXT or ID expression. When it is a multiline text expression, each element (line) is treated as a separate value.Do not add null dimension values (empty single quotes) or values that consists of spaces only, because there is no way you can refer to such values in the future.

- When dimension is INTEGER, valuelist can be an `INTEGER` quantity, such as 5 or 100.

FIRST
LAST
Specify the logical position at which dimension values are added. FIRST indicates that the new values are inserted before any existing values. LAST indicates that new values are added after the current values. LAST is the default. When you are adding a certain quantity of `INTEGER` values to an INTEGER dimension, that quantity of `INTEGER` values are added before or after any existing `INTEGER` values (depending on your specification), and all the `INTEGER` values in the resulting series are automatically adjusted into simple numeric order.

All values specified before the keyword FIRST or LAST are placed in that position, not just the one value immediately preceding the keyword in your statement.

BEFORE position
AFTER position
Specify a position before or after which the dimension values are to be added. For position you can specify an existing dimension value, a character expression whose value is an existing dimension value, or an `INTEGER` expression whose value represents the position of a dimension value. When you are adding a certain quantity of `INTEGER` values to an INTEGER dimension, that quantity of `INTEGER` values are added before or after the `INTEGER` position you specify, and the `INTEGER` values in the whole of the resulting series are automatically adjusted into simple numeric order.

All values specified before the keywords BEFORE or AFTER are placed in that position, not just the one value immediately preceding the keyword in your statement.

##### Usage Notes

Performance When Using MAINTAIN ADD BEFORE or AFTER position

The cost performance of using MAINTAIN ADD BEFORE or MAINTAIN MOVE AFTER statements depends on the number of values in the dimension rather than the number of values being added. Consequently, instead of issuing many of these statements one after another:

1.  Add the values using simple MAINTAIN ADD statements

2.  Set the status of the dimension status to the values you are concerned with.

3.  Order the added values, by issuing a single MAINTAIN MOVE dimension value statement

Adding Values to an INTEGER Dimension

When you use MAINTAIN to add values in an INTEGER dimension, the values are renumbered to keep the normal sequence of `INTEGER` values (1, 2, 3, ...).

Conjoint Dimensions and Composites

Each value of a conjoint dimension or composite is a combination of values from each of the dimensions (and composites, if any) in its dimension list. To add values to a conjoint dimension or composite, specify each value combination enclosed in angle brackets. The values in a given combination must be in the same order as the dimensions and composites in the definition of the conjoint dimension or composite. Each dimension value in the combination must already exist as a value in the corresponding base dimension. However, when a composite value in the combination does not exist, Oracle OLAP automatically adds the value to the appropriate composite.

##### Examples

Example 10-39 Adding Values to a TEXT Dimension

This statement adds `Omaha` and `Seattle` to the end of the dimension values for the `city` dimension.

    MAINTAIN city ADD 'Omaha' 'Seattle'

This statement adds `Atlanta` at the beginning of the list of cities and inserts `Peoria` after `Omaha`.

    MAINTAIN city ADD 'Atlanta' FIRST, 'Peoria' AFTER 'Omaha'

Here the value of the TEXT variable `textvar` is inserted before the fifth dimension value of `city`. When you assign the value `Columbus` to `textvar`, you must make sure it is in mixed case, because you want the dimension value to be in mixed case.

    textvar = 'Columbus'
    MAINTAIN city ADD textvar BEFORE 5

Example 10-40 Adding Values to a Conjoint Dimension

The following is an example of adding values to a conjoint dimension.

    DEFINE proddist DIMENSION <product, district>
    MAINTAIN proddist ADD <'Tents' 'Boston'> <'Footwear' 'Denver'>

You can also assign a value of a base dimension to a text variable and use the name of the variable inside the angle brackets.

    prodname = 'Canoes'
    distname = 'Seattle'
    MAINTAIN proddist ADD <prodname, distname>

##### 10.16.1.2 MAINTAIN ADD for DAY, WEEK, MONTH, QUARTER, and YEAR Values

The MAINTAIN command with the ADD keyword adds new values to a dimension of type DAY, WEEK, MONTH, QUARTER, and YEAR.

##### Syntax

MAINTAIN dimension ADD {valuelist\|{n PERIODS FIRST}\|{n PERIODS LAST}}

##### Parameters

dimension
A non-concat dimension, already defined in an attached analytic workspace.

ADD valuelist
Specifies that the values in valuelist are to be added to the dimension. When dimension is of type DAY, WEEK, MONTH, QUARTER, or YEAR, then valuelist can be text constants or a TEXT, ID, or DATE expression. When the values are TEXT, they can be in the format specified by the VNF (value name format) for the dimension (or in the default format for the type of dimension you are maintaining when the dimension does not have a VNF) or in a valid input style for date values. When the values are specified as a TEXT expression, each element or line is treated as a separate value.

When the values are in the format specified by the VNF or in the default format for this type of dimension, each value explicitly indicates the time period you want to add. For example, assume that the VNF for a `month` dimension is `'<MTXT><YY>'`. In this case, the value `JAN99` represents the month January 1999.

When you specify a value for a DAY, WEEK, MONTH, QUARTER, or YEAR dimension as a date, you must provide only the date components that are relevant for the type of dimension you are maintaining. For a DAY or WEEK dimension, you must supply the day, month, and year components. For a MONTH or QUARTER dimension, you must supply only the month and year (for example, `'JUN98'` or `'0698'` for June 1998). For a YEAR dimension, you must specify only the year (for example, `'98'` for 1998). For information about the valid input styles for dates, see the [DATEORDER](olap-dml-options.md) option.

When you add a dimension value by specifying a DATE expression or a TEXT value that represents a complete date, you can specify any date that falls within the time period you want to add. For example, to add the month January 1999, you can specify any date from` '01JAN99'` through `'31JAN99`'. Oracle OLAP uses the DATEORDER option to resolve any ambiguities.

When adding values to a DAY, WEEK, MONTH, QUARTER, or YEAR dimension that does not yet have values, you must specify only the first and last values you want to add for the dimension. Oracle OLAP automatically fills in the gaps with appropriate values for the intervening time periods.

When a DAY, WEEK, MONTH, QUARTER, or YEAR dimension already has values, you can add values only at the beginning or the end of the existing list. To add values, you must specify only the first or last value you want to add. Oracle OLAP automatically fills in the gap between the existing list and the value you specify.

n PERIODS FIRST
n PERIODS LAST
Specifies the number of periods to add at the beginning or end of an existing list of dimension values.

##### Examples

Example 10-41 Adding Values to Dimension of Type QUARTER

In this example you define a new QUARTER dimension, called` qtr`, and you add dimension values for the quarters in 1998 and 1999. You must only add the first and last dimension values you want. Oracle OLAP fills in the intervening values. To add the first and last quarters, you can specify any dates that fall within those quarters.

    DEFINE qtr DIMENSION QUARTER
    MAINTAIN qtr ADD '01jan98' '31dec99'

##### 10.16.1.3 MAINTAIN ADD SESSION

The MAINTAIN command with the ADD SESSION keywords adds a temporary calculated member to a dimension and applies it to the specified objects; or applies a previously-defined calculated member to the specified objects. The calculated member and its definition do not persist from session to session; both are deleted after the session in which they are created.

##### Syntax

MAINTAIN dimension ADD SESSION member_name \[= calculation\] -       \[STEP DIMENSION (stepdim...)\]\[apply-to\]

where:

- `calculation` is one of the following:

  - `model-equation`
  - `AGGREGATION (``dimension-members``....)`
  -

- `apply-to` specifies the basis on which the custom aggregation is added using one of the following phrases:

  - `APPLY TO AGGMAP ``aggmaps`
  - `APPLY FOR VARIABLE ``variables`
  - `APPLY WITH RELATION ``relations`

##### Parameters

dimension
A dimension that is already defined in an attached analytic workspace. You can specify any type of dimension for dimension except a non-unique concat dimension or a base dimension of either a unique or non-unique concat dimension.

ADD SESSION
ADD SESSION indicates maintenance of a temporary calculated member.

member-name
Specifies the name of the temporary calculated member.

=
Indicates that you are defining a new calculated member.

model-equation
A text expression that specifies the calculation used as a dynamic model to calculate custom member values. (See the SET command for more information about model equations.)

AGGREGATION
Indicates that the temporary calculated member is added as a custom aggregation using the specified dimension members. This clause effectively modifies the RELATION statement of aggmap objects that are the aggregation specification for variables dimensioned by dimension. Consequently, a MAINTAIN ADD SESSION statement that contains an AGGREGATION clause must also contain an APPLY WITH RELATION clause.

dimension-members
A text expression that specifies one or more dimension values to be used by the custom aggregation. When using a literal to specify multiple dimension members, separate the values with commas

STEP DIMENSIONS
Indicates that the calculation is a time-series function.

stepdim
A text expression that specifies the dimension along which the time-series function is calculated. When using a literal to specify multiple dimension names, separate the names with commas.

APPLY TO AGGMAP
Indicates that the calculated temporary member is added only to dimensions used by the specified aggmap objects.

aggmaps
A text expression that specifies the name of one or more aggmap objects to which the temporary calculated member is added. When using a literal to specify multiple aggmap objects, separate the names with commas. The temporary calculated member is added to each of the specified aggmap objects.

APPLY FOR VARIABLE
Indicates that the temporary calculated member is added only to dimensions used by the default aggmap objects for the specified variables.

variables
A text expression that specifies the one or more variable names for which the temporary calculated member is added to. When using a literal to specify multiple variable names, separate the names with commas. The temporary calculated member is added to the default aggmap object of each specified variable.

**Note:**

When a specified variable does not have a default aggmap, using this clause generates an error. Use AGGMAP SET or \$AGGMAP to specify a default aggmap for the variable.

APPLY WITH RELATION
Indicates that the temporary calculated member is added dimensions used by the aggregation specifications that contain a RELATION statement for the specified relation.

relation
A text expression that specifies the name of the relation for which there must be a RELATION statement in the AGGMAP statement.

##### Usage Notes

Finding Out Information About Temporary Calculated Members

Once you have added a temporary calculated member using a MAINTAIN statement, you can use AGGMAPINFO to discover the temporary calculated members you have added, the equations used to calculate members, and the dimension members used in the right-hand side of equations used to calculate custom members.

##### Examples

Example 10-42 Creating Calculated Dimension Members with Aggregated Values

Assume that an analytic workspace has a dimension named `letter` and a variable named `my_quantity` with the following definitions and permanent values.

    DEFINE letter DIMENSION TEXT
    DEFINE my_quantity VARIABLE DECIMAL <letter>

    LETTER                  MY_QUANTITY
    -------------- ------------------------------
    A                                       10.00
    B                                      100.00

You can define temporary dimension members for the `letter` dimension and aggregate data in `my_quantity` for those members following these steps:

1.  Determine the aggregation that you want to perform and define and populate the necessary supporting objects.

    1.  Create an empty child-parent relation for the `letter` dimension

            DEFINE letter.parentrel RELATION letter <letter>

            LETTER                LETTER.PARENTREL
            -------------- ------------------------------
            A              NA
            B              NA

    2.  Define a simple model to be used to calculate values associated with the `letter `dimension

            DEFINE my_model MODEL
            MODEL
              DIMENSION letter
             END

    3.  Define and compile a simple aggmap to be used to calculate `my_quantity` values associated with the `letter` dimension

            DEFINE my_aggmap AGGMAP
            AGGMAP
               RELATION letter.parentrel PRECOMPUTE(NA)
               MODEL my_model PRECOMPUTE(NA)
              END

            COMPILE my_aggmap

    4.  Define a variable to contain the definition for the custom aggregation, This new variable is the same as `my_quantity` except that has `my_aggmap` as its default aggmap.

            DEFINE my_quantity_definition VARIABLE DECIMAL <letter>

            CONSIDER my_quantity_definition
            PROPERTY '$AGGMAP' 'my_aggmap'

            REPORT my_quantity_definition

            LETTER             MY_QUANTITY_DEFINITION
            -------------- ------------------------------
            A                                          NA
            B                                          NA

2.  Add temporary members to the `letter` dimension and specify how variable values for those members are to be calculated.

        MAINTAIN letter ADD SESSION 'C' = 'A' * 'B'
        MAINTAIN letter ADD SESSION 'D' = AGGREGATION('A', 'B') -
            APPLY TO AGGMAP my_aggmap
        MAINTAIN letter ADD SESSION 'E' = 'C' + 'D' -
            APPLY WITH RELATION letter.parentrel
        MAINTAIN letter ADD SESSION 'F' = 10 * 'E' -
            APPLY FOR VARIABLE my_quantity_definition

    A report of the `letter` dimension shows the new dimension members.

        LETTER
        --------------
        A
        B
        C
        D
        E
        F

3.  Aggregate `my_quantity` using the aggmap object named `my_aggmap`.

        REPORT AGGREGATE(my_quantity USING my_aggmap)

                        AGGREGATE(MY_QUANTITY USING
        LETTER                   MY_AGGMAP)
        -------------- ------------------------------
        A                                       10.00
        B                                      100.00
        C                                    1,000.00
        D                                      110.00
        E                                    1,110.00
        F                                   11,100.00

Assume now that you issue the UPDATE and COMMIT statements to update and commit your analytic workspace. Then you detach the analytic workspace and end your session.

Later you start a new session and attach the same analytic workspace. When you ask for a description of the analytic workspace you can see that all of the objects that were in the analytic workspace when the UPDATE was issued still exist.

    DEFINE LETTER DIMENSION TEXT

    DEFINE LETTER.PARENTREL RELATION LETTER <LETTER>

    DEFINE MY_QUANTITY VARIABLE DECIMAL <LETTER>

    DEFINE MY_MODEL MODEL
    MODEL
    DIMENSION letter
    END

    DEFINE MY_AGGMAP AGGMAP
    AGGMAP
    RELATION letter.parentrel PRECOMPUTE(NA)
    MODEL my_model PRECOMPUTE(NA)
    END

    DEFINE MY_QUANTITY_DEFINITION VARIABLE DECIMAL <LETTER>

However, when you report on the `letter` dimension and the `my_quantity` variable, the temporary dimension members that you added in the previous session and their related values in the `my_quantity` variable do not exist.

    LETTER
    --------------
    A
    B

    REPORT letter.parentrel

    LETTER                LETTER.PARENTREL
    -------------- ------------------------------
    A              NA
    B              NA

    REPORT my_quantity

    LETTER                  MY_QUANTITY
    -------------- ------------------------------
    A                                       10.00
    B                                      100.00

    LETTER             MY_QUANTITY_DEFINITION
    -------------- ------------------------------
    A                                          NA
    B                                          NA

    REPORT AGGREGATE(my_quantity USING my_aggmap)

                    AGGREGATE(MY_QUANTITY USING
    LETTER                   MY_AGGMAP)
    -------------- ------------------------------
    A                                       10.00
    B                                      100.00

##### 10.16.1.4 MAINTAIN ADD TO PARTITION

The MAINTAIN ADD TO PARTITION statement adds previously-populated dimension or composite values to a partition of a previously-defined partition template object.

**Tip:**

Use MAINTAIN MOVE TO PARTITION to maintain partition values when you have already populated a partitioned variable.

##### Syntax

MAINTAIN partition-template ADD TO PARTITION partition valuelist

##### Parameters

partition-template
A text expression that is the name of a previously-defined partition template object.

ADD TO PARTITION
Specifies that values are to be added to the partition.

partition
A text expression that is the name of a previously-defined partition in the partition template specified by partition-template.

valuelist
Text literals or a TEXT or ID expression specifying the values to be added. When it is a TEXT expression, each element (line) is treated as a separate value. The values in the expression are added exactly as they are typed.

For a concat dimension, you can specify a value of the concat dimension, or the name of a component dimension and a value or position of that dimension. You can use the values of a dimension surrogate as the values of value.

Note that you cannot partition along an `INTEGER` dimension.

TO
Indicates a range of values.

##### Examples

For an example of adding values to a partition, see Example 10-48.

#### 10.16.2 MAINTAIN DELETE

The MAINTAIN command with the DELETE keyword deletes members from non-concat dimensions and composites; or deletes the data of previously-partitioned variables from one partition to another as it changes the dimension or composite values defined for a partition in the partition template which the variables are dimensioned.

**Note:**

You can also issue a MAINTAIN DELETE statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

##### Syntax

The syntax for using the DELETE keyword of the MAINTAIN command to delete members varies depending on the type of object from which you are deleting the members. For this reason, the following separate entries are provided for MAINTAIN DELETE:

- MAINTAIN DELETE dimension

- MAINTAIN DELETE composite

- MAINTAIN DELETE FROM PARTITION

##### 10.16.2.1 MAINTAIN DELETE dimension

The MAINTAIN command with the DELETE keyword deletes dimension members from non-concat dimensions.

**Note:**

You can also issue a MAINTAIN DELETE statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

**See Also:**

MAINTAIN DELETE composite

##### Syntax

MAINTAIN dimension DELETE limit-clause

##### Parameters

dimension
A non-concat dimension, already defined in an attached analytic workspace, whose values are to be deleted.

**Note:**

You cannot use a dimension surrogate as the dimension argument of a MAINTAIN DELETE command. However, you can use a dimension surrogate as a value within the limit-clause parameter.

limit-clause
Specifies the values to delete from the dimension.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see LIMIT (using values) command, LIMIT using LEVELREL command, LIMIT (using parent relation), LIMIT (using related dimension) command, LIMIT NOCONVERT command, and LIMIT command (using POSLIST).

##### Usage Notes

Deleting Temporary Calculated Members From Dimensions

When you use a MAINTAIN DELETE statement to delete a temporary calculated member, Oracle OLAP:

1.  Deletes the member from the dimension.

2.  Removes the calculation from all aggmap objects that currently contain the corresponding calculation.

Deleting Values in an Integer Dimension

When you use MAINTAIN to delete values in an INTEGER dimension, the values are renumbered to keep the normal sequence of `INTEGER` values (1, 2, 3, ...).

##### Examples

Example 10-43 Deleting Dimension Values by Value

This statement deletes `Omaha` and `Newark` from the values for `city`.

    MAINTAIN city DELETE 'Omaha' 'Newark'

Example 10-44 Deleting the First Five Values of a Dimension

In this example, you use the INTEGER variable `intvar` to remove the first five cities from the dimension` city`.

    intvar = 5
    MAINTAIN city DELETE FIRST intvar

Example 10-45 Deleting Dimension Values Based on a Boolean Expression

Here you remove from `city` all those cities with a population of less than 75,000 people. You use the variable `population.c`, which contains the population for each city.

    MAINTAIN city DELETE population.c LT 75000

Example 10-46 Deleting Dimension Values Using Surrogate to Specify Values

Assume that `prodid` is a `NUMBER` dimension and `prodtype` is a `TEXT `dimension surrogate for `prodid`. Assume also that the values of `prodid` are `17`, `40`, and `56`. The values of `prodtype` are `Two-Person Tent`, `Three-person Tent`, and `Four-person Tent`. The following statement deletes a value from `prodid` and from its surrogate.

    MAINTAIN prodid DELETE prodid(prodtype 'Three-Person Tent')

Example 10-47 Deleting Related MONTH Values

In this example, you use the related dimension `quarter` to remove values of the dimension `month`. All months related to the values of `quarter` currently in the status are deleted.

    LIMIT quarter TO FIRST 1

MAINTAIN month DELETE quarter

##### 10.16.2.2 MAINTAIN DELETE composite

The MAINTAIN command with the DELETE keyword deletes dimension members from composites.

**See Also:**

MAINTAIN DELETE dimension

##### Syntax

MAINTAIN composite DELETE comp-arg

where `comp-arg` is one of the following constructs:

- `valuelist`
- `ALL`
- `base-dim ``[``valuelist``]`
- `boolean-expression`
- `{TOP | BOTTOM} ``n ``BASEDON ``exp`
- `{TOP | BOTTOM} ``n-percent ``PERCENTOF ``expression`
- `LONGLIST`

##### Parameters

composite
A composite whose values are to be deleted. When the composite is a named composite, it must be defined in an attached analytic workspace. When the composite is unnamed, it must have been used in defining an object in an attached analytic workspace.

Use the SPARSE keyword to refer to an unnamed composite (for example, `SPARSE <market product>`).

valuelist
Specifies one or more values to be deleted from the composite. The valuelist can be text constants or a text expression.

ALL
Deletes all composite values, but does not delete the definition of the composite itself.

base-dim \[valuelist\]
Deletes the values that include the listed values of a base dimension of the composite. The argument valuelist can be one value, a list of values, or a range of values (using TO to specify an inclusive range). You cannot use position numbers to specify a range of values. When you omit valuelist, Oracle OLAP deletes all values that include base-dim values currently in status.

boolean-expression
Deletes all composite values for which the Boolean expression is `TRUE`. The boolean-expression must be dimensioned by the dimension or the composite from which you the values deleted. When it has additional dimensions, their status must each be limited to one value.

TOP n BASEDON exp
BOTTOM n BASEDON exp
Deletes the top or bottom n values based on the highest (TOP) or lowest (BOTTOM) values in exp. The expression must be dimensioned by the composite from which you the values deleted. When it has additional dimensions, their status must each be limited to one value.

BOTTOM n-percent PERCENTOF expression
TOP n-percent PERCENTOF expression
Deletes values by finding the top or bottom performers based on a criterion. This construction sorts values and deletes them based on their contribution, by percentage, to an expression.

LONGLIST
Indicates a long list (up to 2,000 values) of individual values to delete. When there are fewer than 300 values, LONGLIST is not needed.

##### 10.16.2.3 MAINTAIN DELETE FROM PARTITION

The MAINTAIN DELETE FROM PARTITION command deletes the data of previously-partitioned variables from one partition to another as it changes the dimension or composite values defined for a partition in the partition template which the variables are dimensioned.

**Tip:**

Use MAINTAIN MOVE TO PARTITION to maintain partition values when you have already populated a partitioned variable.

##### Syntax

MAINTAIN partition-template DELETE FROM PARTITION partition { dim-arg\| comp-arg}

##### Parameters

partition-template
A text expression that is the name of a previously-defined partition template object.

partition
A text expression that is the name of a previously-defined partition in the partition template specified by partition-template.

DELETE FROM PARTITION
Specifies that values are to be deleted from the partition and from partitioned variables dimensioned using a partition template that includes the partition.

dim-args
Specifies the values of a dimension that to use when deleting partitioned variable values and when redefining the values that are in the partition You can use any of the constructs specified for the dim-arg argument in MAINTAIN DELETE dimension.

comp--args
Specifies the values of a composite to use when deleting partitioned variable values and when redefining the values that are in the partition You can use any of the constructs specified for the comp-arg argument in MAINTAIN DELETE composite.

##### Examples

Example 10-48 Adding and Deleting Partition Values

Assume that you have defined the following objects in your analytic workspace. on

    DEFINE time DIMENSION TEXT
    DEFINE time_parentrel RELATION time <time>
    DEFINE product DIMENSION TEXT
    DEFINE partition_sales_by_year PARTITION TEMPLATE <time product> -
       PARTITION BY LIST (time) -
        (PARTITION time_2004 VALUES ('2004', 'Dec2004', 'Jan2004', '31Dec2004', -
              '01Dec2004', '31Jan2004', '01Jan2004') <TIME PRODUCT> -
         PARTITION time_2003 VALUES ('2003', 'Dec2003', 'Jan2003', '31Dec2003', -
             '01Dec2003', '31Jan2003', '01Jan2003') <TIME PRODUCT> -
         PARTITION time_2002 VALUES ('2002', 'Dec2002', 'Jan2002', '31Dec2002', -
             '01Dec2002', '31Jan2002', '01Jan2002') <TIME PRODUCT>)

Assume that instead of having all sales values dimensioned levels by all time values of a year in a partition, you want to have partitions by days and by summary time values (month and year). To change `partition_sales_by_year `to reflect this new partitioning scheme, you issue the following statements.

    "Create the new partition
    CHGDFN partition_sales_by_year DEFINE -
             (PARTITION partition_month_years VALUES () <time product>)
    "Delete the values for months and years from the partitions for years
    MAINTAIN partition_sales_by_year DELETE FROM PARTITION time_2004 '2004'-
            'Dec2004' 'Jan2004'
    MAINTAIN partition_sales_by_year DELETE FROM PARTITION time_2003 '2003'-
            'Dec2003''Jan2003'
    MAINTAIN partition_sales_by_year DELETE FROM PARTITION time_2002 '2002'-
           'Dec2002' 'Jan2002'
    "Add the month and year values to the new partition for summary values
    MAINTAIN partition_sales_by_year ADD TO PARTITION partition_month_years '2004'-
          'Dec2004' 'Jan2004' '2003' 'Dec2003''Jan2003' '2002' 'Dec2002' 'Jan2002'

The `partition_sales_by_year ` partition template object now has the following definition.

    DEFINE PARTITION_SALES_BY_YEAR PARTITION TEMPLATE <TIME PRODUCT> -
       PARTITION BY LIST (TIME) -
        (PARTITION TIME_2004 VALUES ('31Dec2004', '01Dec2004', '31Jan2004', -
           '01Jan2004') <TIME PRODUCT> -
         PARTITION TIME_2003 VALUES ('31Dec2003', '01Dec2003', '31Jan2003', -
           '01Jan2003') <TIME PRODUCT> -
         PARTITION TIME_2002 VALUES ('31Dec2002', '01Dec2002', '31Jan2002', -
           '01Jan2002') <TIME PRODUCT> -
         PARTITION PARTITION_MONTH_YEARS VALUES ('2004', 'Dec2004', 'Jan2004', -
           '2003', 'Dec2003', 'Jan2003', '2002', 'Dec2002', 'Jan2002')-
             <TIME PRODUCT>)

#### 10.16.3 MAINTAIN MERGE

The MAINTAIN command with the MERGE keyword provides a quick way to make sure all dimension or composite values on a separate list are included in a non-concat dimension or composite. Using the MERGE keyword with the MAINTAIN command automatically adds the new values from the list and ignores the duplicates. This method of entering dimension values can save a significant amount of time when you have a large number of values to enter.

You can use MERGE with dimensions of any data type, including DAY, WEEK, MONTH, QUARTER, and YEAR dimensions. However, because Oracle OLAP provides a quick way of adding values of DAY, WEEK, MONTH, QUARTER, and YEAR dimensions through the ADD keyword, the MERGE keyword may not be as useful with DAY, WEEK, MONTH, QUARTER, and YEAR dimensions as it is with TEXT or ID dimensions.

At the same time as you are merging values into a dimension, you can also update a relation that involves that dimension.

**Note:**

You can also issue this MAINTAIN MERGE statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program one time for each value in exp; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

##### Syntax

MAINTAIN dimension\|composite MERGE exp \[RELATE relation\]

dimension
A non-concat dimension, already defined in an attached analytic workspace, whose values are to be entered or changed.

composite
A composite whose values are to be added, deleted, or merged. When the composite is a named composite, it must be defined in an attached analytic workspace. When the composite is unnamed, it must have been used in defining an object in an attached analytic workspace. Use the SPARSE keyword to refer to an unnamed composite (for example, `SPARSE <market product>`).

exp
Specifies an expression whose values are to be merged with dimension; for example, the name of a dimensioned text variable that contains dimension values, or a single-cell text variable whose value is a multiline list of dimension values. MAINTAIN MERGE ignores any NAs in exp. When dimension is an INTEGER dimension, then exp specifies the number of values that you want in the dimension. When the actual total is less, MAINTAIN MERGE adds enough values to reach the specified total. For example, when an INTEGER dimension has 10 positions, `MERGE` `5` has no effect; but `MERGE` `15` would add 5 values.

RELATE relation
Specifies a relation to be updated as new values from exp are merged into dimension. At least one dimension of exp must also appear in the definition of relation. When exp is a single-cell value, you cannot use the RELATE phrase.

##### Examples

Example 10-49 Using the MERGE Keyword with Composites

Suppose you want to define a composite that is made up of all combinations of the first three values of the `product` dimension and the first five values of the `district` dimension. You can efficiently include all 15 values with the following statements.

    DEFINE comp_proddist COMPOSITE <product district>
    LIMIT product TO FIRST 3
    LIMIT district TO FIRST 5
    MAINTAIN comp_proddist MERGE <product district>

This method works with conjoint dimensions as well.

#### 10.16.4 MAINTAIN MOVE

A MAINTAIN command with the MOVE keyword has different effects depending on the object on which it operates:

- When maintaining a dimension, MAINTAIN MOVE changes the position of one or more values in a non-concat dimension or a dimension of type TEXT, ID, or INTEGER or adds previously-populated dimension or composite values to a partition

  **Note:**

  You can also issue a MAINTAIN MOVE dimension value statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

- When maintaining a partition, MAINTAIN MOVE moves the data of a previously-partitioned variables from one partition to another as it changes the dimension or composite values defined for a partition in the partition template which the variables are dimensioned.

##### Syntax

The syntax for using the MAINTAIN command with the MOVE keyword depends on the type of the object being maintained.

For this reason, the following separate entries are provided for MAINTAIN MOVE:

- MAINTAIN MOVE dimension value

- MAINTAIN MOVE TO PARTITION

##### 10.16.4.1 MAINTAIN MOVE dimension value

A simple MAINTAIN MOVE statement changes the position of one or more values in a non-concat dimension or a dimension of type TEXT, ID, or INTEGER. You cannot use the MOVE keyword of the MAINTAIN command with composites or with dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR.

**Note:**

You can also issue a MAINTAIN MOVE statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

##### Syntax

MAINTAIN dimension MOVE limit-clause

##### Parameters

dimension
A non-concat dimension, already defined in an attached analytic workspace, whose values are to be entered or changed. The dimension must be of type TEXT, ID, or INTEGER. You cannot specify a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR.

limit-clause
Specifies the values you want to move.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see LIMIT (using values) command, LIMIT using LEVELREL command, LIMIT (using parent relation), LIMIT (using related dimension) command, LIMIT NOCONVERT command, and LIMIT command (using POSLIST).

##### Usage Notes

What Effects Performance of MAINTAIN MOVE

The performance cost of issuing a MAINTAIN MOVE command is dependent on the length of the dimension, not on the number of values being moved. Consequently, when moving values in a large dimension, do not issue several MAINTAIN MOVE statements one after another; instead, set up the dimension status to what you want and then issue a single MAINTAIN MOVE command.

Reordering or Sorting Values within a Dimension

When you want to reorder or sort dimension values using a MAINTAIN MOVE statement, to specify that you want to use all of the dimension values that are in status, use the STATUS keyword of the limit-clause argument of LIMIT (using values) command rather than a VALUES command.

##### Examples

Example 10-50 Moving a Dimension Value to a Specific Position

This statement moves the position of the city `Houston` to the position following the fifth dimension value.

    MAINTAIN city MOVE 'Houston' AFTER 5

Example 10-51 Moving a Dimension Value to the End of the Status List

In this example, you use the TEXT variable `textvar` to move `Seattle` to the end of the list of cities.

    textvar = 'Seattle'
    MAINTAIN city MOVE textvar LAST

Example 10-52 Moving Values of Concat Dimensions

The following statement moves the `reg.dist.ccdim` concat dimension value `<district: 'Denver'>` after the concat dimension value `<region: 'West'>`.

    MAINTAIN reg.dist.ccdim MOVE <district: 'Denver'> AFTER <region: 'West'>

The following statement moves the concat dimension value `<district: 'Denver'>` after the position that corresponds to the first value of the component `district` dimension. If the first value in the status of `district `is `Atlanta`, then `<district: 'Denver'>` moves after the value `<district: 'Atlanta'>` in the concat dimension.

    MAINTAIN reg.dist.ccdim MOVE <district: 'Denver'> AFTER <district: 1>

The following statement moves the concat dimension value `<district: 'Dallas'>` after the third value of the concat dimension.

    MAINTAIN reg.dist.ccdim MOVE <district: 'Dallas'> AFTER 3

##### 10.16.4.2 MAINTAIN MOVE TO PARTITION

A MAINTAIN MOVE TO PARTITION statement combines both add and move capabilities. You can use a MAINTAIN MOVE TO PARTITION statement to:

- Add previously-populated dimension or composite values to a partition in the same manner as MAINTAIN ADD TO PARTITION

- Change the dimension or composite values defined for a partition in the partition template by which the variables are dimensioned and, at the same time, move the data of a previously-partitioned variables dimensioned by those dimensions and composites from one partition to another.

##### Syntax

MAINTAIN partition-template MOVE TO PARTITION partition value \[TO value\]

##### Parameters

partition-template
A text expression that is the name of a previously-defined partition template object.

MOVE TO PARTITION
Specifies that values are to be added to the partition or moved from one partition to another.

partition
A text expression that is the name of a previously-defined partition in the partition template specified by partition-template.

value
Specifies one or more values of a previously-populated dimension or composite. You can specify these values as:

- A literal value.

- An expression whose value is a dimension value.

- For all dimensions except `NUMBER` dimensions, an `INTEGER` expression whose value represents the position of a dimension value.

- A valueset; or a [LIMIT function](olap-dml-functions-l-z.md).

For a concat dimension, you can specify a value of the concat dimension, or the name of a component dimension and a value or position of that dimension. You can use the values of a dimension surrogate as the values of value.

TO
Indicates a range of values.

##### Examples

Example 10-53 Specifying the Values of a Partition Using Valuesets

Assume that you have defined a partition template object with the following definition that does not specify the actual dimension values for each partition.

    DEFINE PARTITION_SALES_BY_YEAR PARTITION TEMPLATE <TIME PRODUCT> -
       PARTITION BY LIST (TIME) -
        (PARTITION TIME_2004 VALUES () <TIME PRODUCT> -
         PARTITION TIME_2003 VALUES () <TIME PRODUCT> -
         PARTITION TIME_2002 VALUES () <TIME PRODUCT>)

To specify the values of each partition using valuesets, you take the following steps:

1.  Define a valueset for each year's values.

        DEFINE vs_2004 VALUESET time
        LIMIT vs_2004 to '01Dec2004' '31Dec2004' '01Jan2004''31Jan2004' -
             'Jan2004' 'Dec2004' '2004'
        DEFINE vs_2003 VALUESET time
        LIMIT vs_2003 to '01Dec2003' '31Dec2003' '01Jan2003''31Jan2003' -
             'Jan2003' 'Dec2003' '2003'
        DEFINE vs_2002 VALUESET time
        LIMIT vs_2002 to '01Dec2002' '31Dec2002' '01Jan2002''31Jan2002' -
             'Jan2002' 'Dec2002' '2002'

2.  Using MAINTAIN MOVE statements, specify values for the partitions of the partition template.

        MAINTAIN partition_sales_by_year MOVE TO PARTITION time_2004 vs_2004
        MAINTAIN partition_sales_by_year MOVE TO PARTITION time_2003 vs_2003
        MAINTAIN partition_sales_by_year MOVE TO PARTITION time_2002 vs_2002

When you issue a DESCRIBE statement, you can see that the description of the `partition_sales_by_year` partition template now includes the appropriate values of `time` in each partition definition.

    DEFINE PARTITION_SALES_BY_YEAR PARTITION TEMPLATE <TIME PRODUCT> -

        PARTITION BY LIST (TIME) -
        (PARTITION TIME_2004 VALUES -
    ('2004','Dec2004','Jan2004', 31Dec2004',01Dec2004','31Jan2004','01Jan2004')-
         PARTITION TIME_2003 VALUES -
    ('2003','Dec2003','Jan2003', 31Dec2003',01Dec2003','31Jan2003','01Jan2003')-
          PARTITION TIME_2002 VALUES -
                         ('2002','Dec2002','Jan2002', 31Dec2002',01Dec2002','31Jan2002','01Jan2002'))

#### 10.16.5 MAINTAIN RENAME

The MAINTAIN command with the RENAME keyword changes the spelling of one or more dimension values. You cannot use RENAME keyword with a composite or with dimensions of type INTEGER, DAY, WEEK, MONTH, QUARTER, or YEAR.

**Note:**

You can also issue a MAINTAIN RENAME statement for a surrogate dimension that has a Maintain trigger. In this case, Oracle OLAP only executes the Maintain trigger program; no other action occurs. See "[Trigger Programs](olap-dml-programs.md)" for more information for more information. Issuing a MAINTAIN statement for a surrogate dimension that does not have a Maintain trigger, returns an error.

##### Syntax

MAINTAIN dimension RENAME {value new-value}...

##### Parameters

dimension
A non-concat dimension of type TEXT or ID that is already defined in an attached analytic workspace and whose values are to be renamed. You cannot specify a dimension of type INTEGER, DAY, WEEK, MONTH, QUARTER, or YEAR.

value
Specifies an existing dimension value to be renamed. You can specify a dimension value, a character expression whose value is a dimension value, or an `INTEGER` expression whose value represents the position of a dimension value.

new-value
A text constant or a TEXT or ID expression that is the new spelling for the dimension value.

##### Examples

Example 10-54 Renaming Values of a TEXT Dimension

This statement changes the spelling of the cities `Chic` and `Bost` to `Chicago` and `Boston`.

    MAINTAIN city RENAME 'Chic' 'Chicago' 'Bost' 'Boston'

In this example you use the TEXT variable `textvar` to change the second city to `Atlanta`.

    textvar = 'Atlanta'
    MAINTAIN city RENAME 2 textvar

### 10.17 MODEL

The MODEL command enters a completely new specification into a new or existing model object. When the model already has a specification, Oracle OLAP overwrites it. To use MODEL to assign an model specification to a model object, the definition must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER statement to make it the current definition.

An alternative to a MODEL statement is an EDIT MODEL statement, which is available only in OLAP Worksheet. An EDIT MODEL statement opens an Edit window in which you can add, delete, or change the specification for a model object.

Adding a specification to a model object is just one step in modeling data. For more information on models, see "[OLAP DML Model Objects](formulas-models-aggregations-and-allocations.md)".

#### Syntax

MODEL specification

#### Parameters

specification
A multiline text expression that contains one or more of the following OLAP DML statements:

- SET (=) command     
- DIMENSION (in models) statement
- INCLUDE statement

The maximum number of lines you can have in a model is 4,000. Each statement is a line of the multiline text expression. When coding an ALLOCMAP statement at the command line level, separate statements with newline delimiters (`\n`), or use JOINLINES.

For a discussion of designing a model specification, see "Model Specification".

#### Usage Notes

Model Specification

The model specification consists of the following OLAP DML statements:

1.  One of the following:

    - Exactly one INCLUDE statement that specifies the name of another model to include. See "[Nesting Models](formulas-models-aggregations-and-allocations.md)" for more information.

    - One or more DIMENSION (in models) statements coded following the "Guidelines for Writing DIMENSION Statements in a Model".

      **Note:**

      When a model contains an INCLUDE statement, then it cannot contain any DIMENSION statements. However, the model referenced in the INCLUDE statement or the root model in a hierarchy must contain the DIMENSION statements needed by the parent model(s).

2.  One or more SET commands or equations written following the "Rules for Equations in Models".

    **See Also:**

    "[Dimension Status and Model Equations](formulas-models-aggregations-and-allocations.md)" for information on how Oracle OLAP processes equations in a model

3.  A final END statement that indicates the end of the model specification. (Omit when coding the specification in an Edit window of the OLAP Worksheet.)

The maximum number of lines you can have in a model is 32,000.

MODEL Statement in an Aggregation Specification

Within an aggmap, you can use a special MODEL statement to execute a predefined model. (See the [MODEL (in an aggregation)](olap-dml-commands-a-g.md) statement under the AGGMAP command for more information.

Methods of Calculating Data Within a Variable

Both models and aggmap objects calculate data values within a variable based on relationships among dimension members. When a parent-child relationship exists among dimension members (that is, the dimension has a hierarchical structure) and all aggregate values can be calculated using the same method, then you can use a RELATION statement within an aggregation specification to calculate the values. However, when the dimension is not hierarchical and different equations are needed to calculate the values, then you must define a model. You can use a [MODEL (in an aggregation)](olap-dml-commands-a-g.md) to execute the MODEL within an aggregation specification or you can run a model at the command line using the syntax shown in "[Running a Model](formulas-models-aggregations-and-allocations.md)".

Deleting a Model Specification

You can remove the specification of a model without deleting the model definition. Consider the model with a CONSIDER statement. Then issue a MODEL statement and enter the word END as the model specification.

#### Examples

Example 10-55 Model Specified in a Program

In the following example, a simple model is created (or overwritten) in a program called `myprog`. The first line in the program defines or considers the model. The second line contains the MODEL statement, which provides the lines of the model.

This model calculates the line items in a budget. The model equations are based on a `line` dimension.

    DEFINE myprog PROGRAM
    PROGRAM
    IF NOT EXISTS('myModel')
      THEN DEFINE myModel
      ELSE CONSIDER myModel
    MODEL JOINLINES(-
      'DIMENSION line month' -
      'Opr.Income = Gross.Margin - Marketing' -
      'Gross.Margin = Revenue - Cogs' -
      'Revenue = LAG(Revenue, 1, month) * 1.02' -
      'Cogs = LAG(Cogs, 1, MONTH) * 1.01' -
      'Marketing = LAG(Opr.Income, 1, month) * 0.20' -
      'END')
    END

Example 10-56 Model from an Input File

This example presents the text of the same simple model, but it is stored in an ASCII disk file called `budget.txt`.

    DEFINE income.budget MODEL
    MODEL
    DIMENSION line month
    Opr.Income = Gross.Margin - Marketing
    Gross.Margin = Revenue - Cogs
    Revenue = LAG(Revenue, 1, month) * 1.02
    Cogs = LAG(Cogs, 1, month) * 1.01
    Marketing = LAG(Opr.Income, 1, month) * 0.20
    END

To include the `income.budget` model in your analytic workspace, execute the following statement in which `myinpfiles` is a directory object.

    INFILE 'myinpfiles/budget.txt'

Example 10-57 Creating a Model

Suppose that you define a model, called `income.calc`, that calculates line items in the income statement.

    define income.calc model
    ld Calculate line items in income statement

After defining the model, you can use a `MODEL` statement or the OLAP Worksheet editor to enter the specification for the model. A model specification can contain `DIMENSION` commands, assignment statements and comments. All the `DIMENSION` commands must come before the first equation. For the current example, you can specify the lines shown in the following model.

    DEFINE INCOME.CALC MODEL
    LD Calculate line items in income statement
    MODEL
    DIMENSION line
    net.income = opr.income ‐ taxes
    opr.income = gross.margin ‐ (marketing + selling + r.d)
    gross.margin = revenue ‐ cogs
    END

When you write the equations in a model, you can place them in any order. When you compile the model, either by issuing a `COMPILE` statement or by running the model, Oracle OLAP identifies the logical order in which the model equations are solved. When the calculated results of one equation are used as input to another equation, then the equations are solved in the order in which they are needed.

To run the `income.calc` model and use `actual` as the solution variable, you execute the following statement.

    income.calc actual

When the solution variable has dimensions other than the dimensions on which model equations are based, then a loop is performed automatically over the current status list of each of those dimensions. For example, `actual` is dimensioned by `month` , `division`, and `line`. When `division` is limited to `ALL`, and `month` is limited to `OCT96` to `DEC96`, then the `income.calc` model is solved for the three months in the status for each of the divisions.

Example 10-58 Building a Scenario Model

Suppose, for example, you want to calculate profit figures based on optimistic, pessimistic, and best-guess revenue figures for each division. The steps for building this scenario model are explained in the following example.

You can call the scenario dimension `scenario` and give it values that represent the scenarios you want to calculate.

These commands give `scenario` the values `optimistic`, `pessimistic` and `bestguess`.

    DEFINE scenario DIMENSION TEXT
    LD Names of scenarios
    MAINTAIN scenario ADD optimistic pessimistic bestguess

These commands create a variable named `plan` dimensioned by three other dimensions (`month`, `line`, and `division`) in addition to the `scenario` dimension.

    DEFINE plan DECIMAL <month line division scenario>
    LD Scenarios for financials

For this example, you must enter input data, such as revenue and cost of goods sold, into the `plan` variable.

For the best-guess data, you can use the data in the `budget` variable. Limit the `line` dimension to the input line items, and then copy the `budget` data into the `plan` variable.

    LIMIT scenario TO 'BESTGUESS'
    LIMIT line TO 'REVENUE' 'COGS' 'MARKETING' 'SELLING' 'R.D'
    plan = budget

You might want to base the optimistic and pessimistic data on the best-guess data. For example, optimistic data might be fifteen percent higher than best-guess data, and pessimistic data might be twelve percent less than best-guess data. With `line` still limited to the input line items, execute the following commands.

    plan(scenario 'OPTIMISTIC') = 1.15 * plan(scenario 'BESTGUESS')
    plan(scenario 'PESSIMISTIC') = .88 * plan(scenario 'BESTGUESS')

The final step in building a scenario model is to write a model that calculates results based on input data. The model might contain calculations very similar to those in the `budget.calc` model shown earlier in this chapter.

You can use the same equations for each scenario or you can use different equations. For example, you might want to calculate the cost of goods sold and use a different constant factor in the calculation for each scenario. To use a different constant factor for each scenario, you can define a variable dimensioned by `scenario` and place the appropriate values in the variable. When the name of your variable is `cogsval`, then your model might include the following equation for calculating the `cogs` line item.

    cogs = cogsval * revenue

By using variables dimensioned by `scenario`, you can introduce a great deal of flexibility into your scenario model.

Similarly, you might want to use a different constant factor for each division. You can define a variable dimensioned by `division` to hold the values for each division. For example, when labor costs vary from division to division, then you might dimension `cogsval` by `division` and by `scenario`.

When you run your model, you specify `plan` as the solution variable. For example, when your model is called `scenario.calc`, then you solve the model with this statement.

    scenario.calc plan

A loop is performed automatically over the current status list of each of the dimensions of `plan`. Therefore, when the `scenario` dimension is limited to `ALL` when you run the `scenario.calc` model, then the model is solved for all three scenarios: `optimistic`, `pessimistic`, and `bestguess`.

#### 10.17.1 DIMENSION (in models)

The DIMENSION statement at the beginning of a model tells Oracle OLAP the names of one or more dimensions to which the model assigns data or to which it refers in dimension-based equations. A dimension-based equation assigns the results of a calculation to a target that is represented by one or more values of a dimension.

##### Syntax

DIMENSION dimension1 \[, dimensionN\]

##### Parameters

dimension
One or more dimensions, including base dimensions of composites, on which model equations are based. You can specify the name of a dimension surrogate instead of the dimension for which is a surrogate. You can then use the values of the surrogate instead of the values of the dimension.

##### Usage Notes

Dimension-Based Equations in Models

When an equation (SET) assigns data to a dimension value or refers to dimension values in its calculations, it is called a dimension-based equation. Note that a dimension-based equation does not have to refer to the dimension itself, but only to the values of the dimension. Therefore, when the model contains any dimension-based equations, you must specify the name of each of these dimensions in a DIMENSION statement at the beginning of the model s that Oracle OLAP can determine the dimension to which each dimension value belongs. You can specify the name of a dimension surrogate instead of the dimension for which it is a surrogate. You can then use the values of the surrogate instead of the values of the dimension.

In addition, when a model contains any dimension-based equations, you must supply the name of a solution variable when you run the model. The solution variable is both the source and the target of data for the model. It holds the input data used in dimension-based calculations, and Oracle OLAP stores the calculation results in designated values of the solution variable. The solution variable is generally dimensioned by all the dimensions on which the model equations are based. For example, in a financial application, the model might be based on the `line` dimension, and the solution variable might be `actual`, which has `line` as one of its dimensions.

Dimension-based equations provide flexibility in modeling. Because you do not have to specify the modeling variable until you solve a model, you can run the same model with different solution variables. For example, you might run the same model with the `actual` variable, with a "best case" budget variable, and with a "worst case" budget variable.

A dimension must be specified in a DIMENSION statement when a dimension-based equation refers to a value of the dimension either as a source of the data used in the calculation or as the target to which the results are assigned. In the following example, `Gross.Margin`, `Revenue`, and `Cogs` are values of the `line` dimension, so `line` is specified in a DIMENSION statement.

    DIMENSION line
    Gross.Margin = Revenue - Cogs

Dimension is a Function Argument

A dimension must be specified in a DIMENSION statement when the dimension is an argument to a function that uses a dimension value as its data source. In the following example, `month` must be specified in a DIMENSION statement.

    DIMENSION line, month
    Revenue = lag(Revenue, 1, month) * 1.05

The writer of the preceding model expects to use a solution variable that is dimensioned by `line` and `month`. Therefore, when the model is run, the LAG function operates on a solution variable that has the specified time dimension (`month`) as one of its dimensions. However, because the model compiler cannot anticipate the time dimension of the solution variable, you must specify it in a DIMENSION statement. When you fail to include `month` in a DIMENSION statement, an error occurs when you attempt to compile the model.

In a function that operates on time-series data (such as MOVINGTOTAL or LAG), the dimension argument is optional when the dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. For example, you can omit `month` from the LAG function in the preceding example. However, you must still specify the appropriate time dimension in a DIMENSION statement.

Solution Variable

When you run a model that contains dimension-based equations, you specify a solution variable, which is both the source and the target of data for the model. The solution variable is generally dimensioned by all the dimensions that are listed in the DIMENSION commands used in the model. Or, when a solution variable is dimensioned by a composite, the DIMENSION commands can list base dimensions of the composite. The DIMENSION commands can be explicit in the model or inherited through an included model. See "Incompatibility with INCLUDE".

Working with Composites

When you expect to run a model with a solution variable that has a composite in its dimension list, you can specify a base dimension of the composite in a DIMENSION statement. Your model equations assign results to values of the base dimension. Oracle OLAP automatically creates any new values that are needed in the composite.

Multiple DIMENSION Commands

You can include a separate DIMENSION statement for every dimension referred to or used in dimension-based equations, or you can specify all the dimensions in a single DIMENSION statement.

Location of Commands

You must place all the DIMENSION commands at the beginning of the model, before any equations.

Incompatibility with INCLUDE

When a model contains an INCLUDE statement, it cannot contain any DIMENSION commands. The INCLUDE statement specifies another model to include in the current model. In this case, the current model inherits its DIMENSION commands, if any, from the included model. For more information in including models, see the INCLUDE statement under the MODEL command.

Inherited DIMENSION commands must satisfy all the requirements specified for explicit DIMENSION commands. See "Guidelines for Writing DIMENSION Statements in a Model".

Dimension Order

When multiple dimensions are specified by the DIMENSION commands in a model, the order in which the dimensions are listed is important:

- When a model equation contains a name that might be a dimension value, Oracle OLAP searches through the dimensions that appear in the model's explicit or inherited DIMENSION commands, in the order you list the dimensions, to determine whether the name matches a dimension value of a listed dimension. The search concludes as soon as a match is found. Therefore, when two or more listed dimensions have a dimension value with the same name, Oracle OLAP assumes that the value belongs to the dimension specified earliest in a DIMENSION statement. When the name does not match a value of a listed dimension, Oracle OLAP then searches through the variables in the attached workspaces to find a match.

- When model equations assign results to values of a target dimension, Oracle OLAP constructs code that loops over the values of the other, non-target, dimensions listed in the DIMENSION commands. The non-target dimension listed first in the DIMENSION commands is treated as the slowest-varying dimension. For example, when MONTH is the first non-target dimension listed in a DIMENSION statement and DIVISION is the second, Oracle OLAP loops through all the divisions for the first month, then all the divisions for the second month, and so on.

Guidelines for Writing DIMENSION Statements in a Model

When you write `DIMENSION` statements, keep these points in mind:

- In the `DIMENSION` statements, you must list the names of all the dimensions on which model equations are based. In the following example, `gross.margin`, `revenue`, and `cogs` are values of the `line` dimension, so `line` is specified in a `DIMENSION` statement.

      DIMENSION line
      gross.margin = revenue - cogs

<!-- -->

- `DIMENSION` statements must also list any dimension that is an argument to a function that refers to a dimension value. In the following example, `month` must be specified in a `DIMENSION` statement.

      DIMENSION line, month
      revenue = LAG(revenue, 1, month) * 1.05

<!-- -->

- When a model equation assigns results to a dimension value, then code is constructed that loops over the values of any of the other nontarget dimensions listed in the `DIMENSION` statements. The nontarget dimension listed first in the `DIMENSION` statements is treated as the slowest-varying dimension.

- A model executes most efficiently when you observe the following guidelines for coordinating the dimensions in `DIMENSION` statements and the dimensions of the solution variable:

  - List the target dimension of the model as the first dimension in the `DIMENSION` statements and as the last dimension in the definition of the solution variable.

  - In `DIMENSION` statements, list the nontarget dimensions in the reverse order of their appearance in the definition of the solution variable. Consequently, the fastest-varying and slowest-varying nontarget dimensions are in the same order in the model and in the solution variable.

- When the solution variable has dimensions that are not used or referred to in model equations, then do not include them in `DIMENSION` statements.

- When your analytic workspace contains a variable whose name is the same as a dimension value, or when the same dimension value exists in two different dimensions, then there could be ambiguities in your model equations. Because you can use a variable and a dimension value in the same way in a model equation, a name might be the name of a variable, or it might be a value of any dimension in your analytic workspace.

- Your `DIMENSION` statements are used to determine whether each name reference in an assignment statement is a variable or a dimension value. "[Compiling Models](formulas-models-aggregations-and-allocations.md)" explains how the name references are resolved.

  **See Also:**

  "[OLAP DML Model Objects](formulas-models-aggregations-and-allocations.md)", SET, and MODEL for information on:

  - Entering statements in a model

  - How to refer to values of dimensions

  - Explanation of how Oracle OLAP constructs code from the statements

  - Explanation of how Oracle OLAP handles the situation in which the solution variable has more dimensions or fewer dimensions than are listed in DIMENSION commands

##### Examples

Example 10-59 Simplified Model for Budget Estimates

The following statements define a simplified model that estimates budget values for the items on an income statement.

    DEFINE income.budget MODEL
    LD Model for estimating budget line items
    MODEL
    dimension line, month
    Revenue = 1.05 * LAG(Revenue 1 month)
    Gross.Margin = Revenue - Cogs
    Opr.Income = Gross.Margin - (Marketing + Selling + R.D)
    Net.Income = Opr.Income - Taxes
    END

The model equations are based on the `line` dimension, so `line` is specified in the DIMENSION statement. The dimension `month` is the time dimension in the LAG function that operates on REVENUE values, so `month` is also specified in the DIMENSION statement.

When you run the model, Oracle OLAP loops over the values in the current status of the `month` dimension.

#### 10.17.2 INCLUDE

The INCLUDE statement includes one model within another model. You can use the INCLUDE statement only within models.

Use INCLUDE to create modular models by placing equations that are common to several models, in a separate model for inclusion on other models as needed. The INCLUDE statement also facilitates what-if analyses. An experimental model can draw equations from a base model and selectively replace them with new equations

##### Syntax

INCLUDE model

##### Parameters

model
The name of a model to include in the current model. The current model is referred to as the parent model. The model that you include is referred to as the base model.

##### Usage Notes

Guidelines for Coding INCLUDE Statements in a Model

Follow these guidelines for using INCLUDE statements in models:

- A model can contain only one INCLUDE statement.

- The INCLUDE statement must be before any equations in the model.

- A model that contains an INCLUDE statement cannot contain any DIMENSION statements.

How to Nest Models

You can nest models by placing an INCLUDE statement in a base model. For example, model `myModel1` can include model `myModel2`, and model `myModel2` can include model `myModel3`. The nested models form a hierarchy. In this example, `myModel1` is at the top of the hierarchy, and `myModel3` is at the root. A base model cannot include a model at a higher level in the hierarchy. In the preceding example, `myModel2` cannot include `myModel1`, and `myModel3` cannot include `myModel1` or `myModel2`.

Dependencies Among Equations

When compiling a model that contains an INCLUDE statement, the compiler considers the dependencies among the equations from all the included models when it orders and blocks the equations. Therefore, when you run the `MODEL.COMPRPT` program to examine the results of the compilation or when you set the MODTRACE option to `YES` before running the parent model, you might find that equations from different levels in the hierarchy of included models are interspersed. See Example 10-61.

When the compiler finds no dependencies among the equations from the included models, it executes the equations in the root model first and the equations in the parent model last.

Compiling a Parent Model

When you compile a parent model, the compiler compiles all the base models under it in the included hierarchy when compiled code does not already exist. When the compiler detects an error in an included model, neither it nor any model above it in the hierarchy is compiled. When the root model of the included hierarchy contains an error, the higher-level models are unable to inherit any DIMENSION statements from the root model. In this case, the compiler might report an error in a parent model when the source of the error is actually in the root model. For example, the compiler might report that a target dimension value does not exist in any attached analytic workspace. On the other hand, when the compiler detects an error in a parent model but finds no errors in the included models, the included models are compiled even though the parent model is not.

Masking Equations

To support what-if analyses, Oracle OLAP allows equations in a model to mask previous equations. The previous equations can come from the same model or from included models. A masked equation is not executed. When you run the `MODEL.COMPRPT` program after compiling the model, the masked equation is not shown in the report on the compiled model.

Masking can take place when an equation assigns a value to a variable or dimension value that is also the target of a previous equation. The masking rules are as follows:

- When the target in the earlier equation is qualified the same as the target in the later equation, the earlier equation is masked and the later equation is executed. The following example illustrates two equations with targets that are identically qualified.

      Equation from a base model:      BUDGET(LINE REVENUE) = 5000
      Equation from the parent model:  BUDGET(LINE REVENUE) = 3500

  In this example, the equation from the base model is masked and the equation from the parent model is executed.

- When the target in the earlier equation is more qualified than the target in the later equation, the earlier equation is masked. The later equation is executed.

  The target that is more qualified is the one that affects the fewest dimension values. Consider the following equations from a base model and a parent model.

      Equation from a base model:      BUDGET(LINE REVENUE) = 2500
      Equation from the parent model:  BUDGET = 4000

  The equation from the base model is more qualified because it assigns data only for the REVENUE value of the LINE dimension. The equation from the parent model assigns data to all the values of the LINE dimension. In this example, the equation from the base model is masked and the equation from the parent model is executed.

- When the target in the earlier equation is less qualified than the target in the later equation, no masking takes place. Both equations are executed.

  Consider the following equations from a base model and a parent model.

      Equation from a base model:      BUDGET = LAG(ACTUAL, 1, MONTH)
      Equation from the parent model:  BUDGET(LINE REVENUE) = 6500
      Equation from the parent model:  BUDGET(LINE COGS) = 4000

  The equation from the base model assigns data to all the values of the LINE dimension. The equations from the parent model are more qualified because each assigns data only for a single value of the LINE dimension. In this example, the equation from the base model is executed first, and then the equations from the parent model are executed.

  This functionality enables you to assign a large number of values with one equation and use subsequent equations to replace or test individual values.

- When the target in the earlier equation is qualified differently from the target in the later equation, no masking takes place. Both equations are executed. In the following example, both equations are executed.

      Equation from a base model:      BUDGET(LINE REVENUE) = 5000
      Equation from the parent model:  BUDGET(LINE COGS) = 4500

##### Examples

Example 10-60 Including a Model

This example shows a parent model named `income.plan` that includes a base model named `base.lines`.

    DEFINE income.plan MODEL
    MODEL
    INCLUDE base.lines
    revenue = LAG(revenue, 1, month) * 1.02
    cogs = LAG(cogs, 1, month) * 1.01
    taxes = 0.3 * opr.income
    END
     
    DEFINE BASE.LINES MODEL
    MODEL
    DIMENSION line month
    net.income = opr.income - taxes
    opr.income = gross.margin - marketing
    gross.margin = revenue - cogs
    END

Example 10-61 Producing a Compilation Report

The following statements compile the parent model and produce a compilation report.

    COMPILE income.plan
    MODEL.COMPRPT income.plan

These statements produce the following output.

    MODEL INCOME.PLAN <LINE MONTH>
                          BLOCK 1 (SIMPLE)
    INCOME.PLAN     2:    revenue = lag(revenue, 1, month) * 1.02
    INCOME.PLAN     3:    cogs = lag(cogs, 1, month) * 1.01
    BASE.LINES      4:    gross.margin = revenue - cogs
    BASE.LINES      3:    opr.income = gross.margin - marketing
    INCOME.PLAN     4:    taxes = 0.3 * opr.income
    BASE.LINES      2:    net.income = opr.income - taxes
                          END BLOCK 1

### 10.18 MODEL.COMPRPT

The MODEL.COMPRPT program produces a report that shows how model equations are grouped into blocks. For step blocks and for simultaneous blocks with a cross-dimensional dependence, the report lists the dimensions involved in the dependence.

#### Syntax

MODEL.COMPRPT

#### Examples

Example 10-62 A Compilation Report for the income.budget Model

The MODEL.COMPRPT program produces a compilation report that shows the block structure of the model that you specify as the program argument and the order of equations within each block. Each equation is identified with the name of the model and its statement number within that model.

The following statements compile the model and invoke MODEL.COMPRPT.

    COMPILE income.budget
    MODEL.COMPRPT income.budget

The `MODEL.COMPRPT` statement produces the following compilation report.

    MODEL INCOME.BUDGET <LINE MONTH>
                       BLOCK 1 (SIMPLE)
    INCOME.BUDGET  4:  revenue = lag(revenue, 1, month) * 1.02
    INCOME.BUDGET  5:  cogs = lag(cogs, 1, month) * 1.01
    INCOME.BUDGET  3:  gross.margin = revenue - cogs
                        BLOCK 2 (STEP-FORWARD <MONTH>)
    INCOME.BUDGET  6:   marketing = lag(opr.income, 1, month) * 0.20
    INCOME.BUDGET  2:   opr.income = gross.margin - marketing
                        END BLOCK 2
                       END BLOCK 1

Example 10-63 A Compilation Report for the income.est Model

The following statement runs the `MODEL.COMPRPT` program, which produces a compilation report for a model named `income.est`.

    MODEL.COMPRPT income.est

The compilation report contains the following output.

    MODEL INCOME.EST <LINE MONTH>
                  BLOCK 1 (STEP-FORWARD <MONTH>)
    INCOME.EST 5: revenue = lag(revenue,1,month)+2*lag(marketing,1,month)
    INCOME.EST 4: gross.margin = revenue - cogs
                   BLOCK 2 (SIMULTANEOUS)
    INCOME.EST 2:  net.income = opr.income - taxes
    INCOME.EST 3:  opr.income = gross.margin - marketing - selling - r.d
    INCOME.EST 6:  marketing = .15 * net.income
    INCOME.EST 7:  taxes = .3 * opr.income
                   END BLOCK 2
                  END BLOCK 1

### 10.19 MODEL.DEPRT

The MODEL.DEPRPT program produces a report that lists the variables and dimension values on which each model equation depends. When a dependence is dimensional, the report gives the name of the dimension.

#### Syntax

MODEL.DEPRT

#### Examples

Example 10-64 Producing a Dependency Report

The MODEL.DEPRPT program produces a dependency report that lists the variables and dimension values that are the assignment target and data sources for each model equation. For each equation, the assignment target and each data source is listed on a separate line. When a target or data source is a dimension value, its line is marked by an asterisk enclosed in square brackets (`[*]`).

When a target or data source depends on a qualifier, the report specifies the dimension of the qualifier and indicates the type of dependence. The type of dependence can be any of the following:

- LAG -- One-way dependence on previous dimension values

- LEAD -- One-way dependence on later dimension values

- BOTH -- Two-way dependence on both previous and later values

- VARIABLE -- Dependence on either previous or later values, depending on the value of a variable when the model is run

- QDR -- Qualified data reference

Assume that you want to produce a dependency report for the `income.budget` model. The following statement and report illustrate this process.

    MODEL.DEPRPT income.budget

    MODEL INCOME.BUDGET <LINE MONTH>
    2    [*](LINE OPR.INCOME):
           [*](LINE GROSS.MARGIN)
           [*](LINE MARKETING)
    3    [*](LINE GROSS.MARGIN):
           [*](LINE REVENUE)
           [*](LINE COGS)
    4    [*](LINE REVENUE):
           [*](LINE REVENUE)(LAG <MONTH>)
    5    [*](LINE COGS):
           [*](LINE COGS)(LAG <MONTH>)
    6    [*](LINE MARKETING):
           [*](LINE OPR.INCOME)(LAG <MONTH>)

The data sources in statements 4, 5, and 6 have a LAG dependence on the `month` dimension.

### 10.20 MODEL.XEQRPT

The MODEL.XEQRPT program produces a report about the execution of the model. The report specifies the block where the solution failed and shows the values of the model options that were used in solving simultaneous blocks.

#### Syntax

MODEL.XEQRPT

#### Usage Notes

Running MODEL.XEQRPT

Before you can run the MODEL.XEQRPT program, you must

1.  Set the [MODERROR](olap-dml-options.md) option to STOP or CONTINUE.

2.  Execute the model.

When the model halts because of an error, run the `MODEL.XEQRPT` program.

Effect of MODERROR on MODEL.XEQRPT

The results returned by MODEL.XEQRPT vary depending on the setting of the [MODERROR](olap-dml-options.md) option:

- When MODERROR is set to `STOP` and execution of the model halts because of an error, you can run the MODEL.XEQRPT program to produce a report about the execution of the model. The report specifies the block where the solution failed and shows the values of the model options that were used in solving simultaneous blocks.

- When MODERROR is set to `CONTINUE` and one block in the model is a simultaneous block that either diverges or fails to converge, Oracle OLAP executes any remaining blocks in the model.

  Moreover, Oracle OLAP executes the model for the remaining values in the status of any additional dimensions of the solution variable that are not dimensions of the model. In this case, when you run the MODEL.XEQRPT program when Oracle OLAP finishes executing the model, a report on the solution for the final values of the additional dimensions is produced.

  When the simultaneous blocks in the model converged when the model was executed for the final values of the additional dimensions, then `MODEL.XEQRPT` reports that the blocks were solved, even though an earlier execution of the model for another dimension value might have failed. When you want to see the `MODEL.XEQRPT` for the dimension values where the failure occurred, you can set MODERROR to `STOP` and rerun the model.

#### Examples

Example 10-65 Producing an Execution Report for the income.est Model

After running the income.est model, you can use the MODEL.XEQRPT program to produce a report on the execution of the model.

The following statement runs the MODEL.XEQRPT program, which produces an execution report for the model.

    MODEL.XEQRPT income.est

The execution report contains the following output.

    MODEL INCOME.EST <LINE MONTH>
    Solution status:     SOLVED
    Model options in use: 
       MODSIMULTYPE:     AITKENS
       MODMAXITERS:      50
       MODTOLERANCE:     3
       MODOVERFLOW:      3
       MODGAMMA:         1
    BLOCK 1 (STEP-FORWARD <MONTH>)
      Solution status:   SOLVED
    BLOCK 2 (SIMULTANEOUS)
      Solution status:   SOLVED
      Iterations:        15

The report shows the values of the model options that were used in solving the simultaneous blocks and indicates whether each block was solved.

### 10.21 MONITOR

The MONITOR command records data on the performance cost of each line in a specified program. To get meaningful information from MONITOR, your session must be the only one running in Oracle OLAP. Furthermore, the accuracy of the results of MONITOR decreases as more processes are started on the host computer.

You first use a MONITOR statement to specify a program for monitoring; then you run the program and use MONITOR again to obtain the results. When the program executes a given line repeatedly, MONITOR records the cumulative cost of all the executions on the single line of its monitor list that is devoted to that program line.

A line of code is considered to have a high performance cost when it takes a long time to execute. Use a TRACKPRG statement to identify programs that have relatively high costs and then use MONITOR to identify the time-consuming lines within those programs. When you want, you can use both TRACKPRG and MONITOR simultaneously.

#### Syntax

MONITOR ON \[programs\]  \| OFF \| INIT \| FILE \[\[APPEND\] file-name\] \| RESET

where `programs` is one of the following:

- `ALL [``awlist``]`
- `program-name`

#### Parameters

ON
Starts looking for the specified programs to be run so that Oracle OLAP can gather line-by-line timing data in a monitor list. (It continues the current monitoring process without interruption when monitoring is already on, or resumes with a gap when monitoring was off.)

When you do not specify a value for programs, the default is the program or programs specified in the last executed `MONITOR` `ON` statement. When there was no such statement in your current session, no data is collected and no error is produced.

ALL
Specifies that all of the programs in one or more analytic workspaces are monitored.

awlist
The name of one or more analytic workspaces (optionally separated by commas) whose programs you want monitored. When you omit this argument, Oracle OLAP monitors all of the programs in all of the attached analytic workspaces

program-name
The name of a specific program that you want monitored.

OFF
Stops monitoring programs and freezes any timing data currently in the monitor list which allows you send the list to the current outfile or to a text file either immediately, or later in your session.

RESET
(Useful only when monitoring is on.) Retains information about the programs that ares currently specified for monitoring and the Oracle OLAP memory that is allocated for the current monitor list, but discards any timing data currently in the list. In addition, RESET causes MONITOR to again begin waiting for you to run the same programs. When you do, MONITOR automatically gathers new timing data into a new monitor list for the same programs in the same memory allocation as before.

INIT
(Useful only when monitoring is on.) Initializes the monitoring environment. Initialization consists of discarding the program names and the timing data associated with the current monitor list, and releasing the Oracle OLAP memory previously used for that list so it can be used for other purposes or for collecting new data in a new monitor list.

FILE
Specifies that the timing data that is currently in the monitor list is sent to a file.

APPEND
Specifies that the timing data is appended to an existing file. When you omit this argument, the new output replaces the current contents of the file.

file-name
A text expression that is the name of the file to receive the output. Unless the file is in the current directory, you must include the name of the directory object in the name of the file. When file-name is specified, the data is sent to the named text file. FILE has no effect on the monitor list, so you can send the same list repeatedly to different destinations. When file-name is omitted, Oracle OLAP sends the timing data that is currently in the monitor list to the current outfile.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use a CDA statement to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

#### Usage Notes

Monitor List

Each entry (that is, line) in the monitor list focuses on the execution of a single program line, regardless of how many times it is executed. Each entry is divided into the following four sections:

- Cumulative total time of all executions in milliseconds rounded to the nearest 10 millisecond, in columns 1 through 11

- Number of times executed, in columns 12 through 18

- Line number, in columns 19 through 23

- Text of the line, in column 24 and subsequent columns

Here is a sample of MONITOR output with column numbers included for reference.

    12345678901234567890123456789012345678901234567890
     
    60              1    1 push name 
    30              1    2 trap on GETOUT noprint 
    51              1    3 limit name to obj(type) eq 'DIMENSION'
    0               1    4 for name 
    0               0    5    do 
    450             6    6    limit &name to ALL ifnone BYPASS 
    0               0    7 BYPASS: 
    0               0    8    doend 
    0               0    9 GETOUT: 
    0               1   10 pop name 

The following is the full description of the program used for the preceding output. Note that in the output, the line with the LIMIT command is truncated because it is too long to fit.

    DEFINE allstat PROGRAM
    LD Program to set the status of all dimensions in the analytic workspace to ALL
    PROGRAM
    PUSH NAME
    TRAP ON getout NOPRINT
    LIMIT NAME TO OBJ(TYPE) EQ 'Dimension' IFNONE getout
    FOR NAME
       DO
       LIMIT &NAME TO ALL IFNONE bypass
    bypass:
       DOEND
    getout:
    POP NAME
    END

Attaching, Detaching, and Reattaching Analytic Workspaces

When Oracle OLAP executes a program in an analytic workspace that has been attached, detached, a new block of data is collected.

Truncated Statement Lines

When a program line is too long, the MONITOR output truncates it. Continuation lines do not appear in the output.

Producing a Report

When you want to produce an Oracle OLAP report from the timing data in the MONITOR file, you can write a program that uses a FILEREAD statement to read the data into an Oracle OLAP variable, and then use Oracle OLAP reporting capabilities to produce a report. You can use the `TRACKREPORT` program as a model. However, keep in mind that the `TRACKREPORT` program was written to produce a report on TRACKPRG output, not MONITOR output.

Bracketing Lines

When you just want to time a particular line or group of lines in a program, you can insert `MONITOR` `ON` and `MONITOR` `OFF` statements in the program to bracket just the line or lines in which you are interested.

Using MONITOR for a Nested Programs

When you do not want to run a nested program by itself, you can specify its name in a `MONITOR` `ON` statement and then run the program that calls it. MONITOR gathers timing data only for the specified (nested) program. When the specified program is called more than once, for each program line, MONITOR accumulates the total seconds taken by all the times the line was run and provide the number of times it was run.

When you just want to time a particular execution of a nested program that is called more than once, you can insert `MONITOR` `ON` and `MONITOR` `OFF` statements in the calling program to bracket the single call in which you are interested.

Using MONITOR with Very Small Programs

You might not be able to reproduce the results exactly for very small programs. When the CPU interrupts processing to do other tasks, that time is a greater percentage of the total execution time.

Unit of Measure for MONITOR

The MONITOR and TRACKPRG commands use milliseconds as the unit for recording execution time. The execution time does not include time spent on I/O and time spent waiting for the next statement.

#### Examples

Example 10-66 Collecting Timing Data Using MONITOR

In this example, MONITOR is used to collect timing data on the execution of the individual lines of code in `prog1` and then to send the data to a text file. The `MONITOR` `ON` statement is then used to discard the `prog1` timing data and start collecting data on `prog2`. After the data for `prog2` is sent to a second file, `MONITOR` `INIT` is used to discard the current monitor list and release the memory used for it.

    MONITOR ON prog1
    prog1
    MONITOR FILE prog1.mon
    MONITOR ON prog2
    prog2
    MONITOR OFF
    MONITOR FILE prog2.mon
    MONITOR INIT

### 10.22 MOVE

The MOVE command moves an object name to a new position in the NAME dimension of an analytic workspace. The reorganizing effect of the MOVE command on the workspace is cosmetic. That is, no physical changes take place in workspace storage. Users often reorganize workspace objects so the output from DESCRIBE is easier to read.

#### Syntax

MOVE name... {FIRST\|LAST\|{BEFORE\|AFTER} name2} \[AW workspace\]

#### Parameters

name...
The names of one or more objects to move. You can specify the names individually, or use one of the following forms to specify a group of names:

- `name ``TO` `name`
- `FIRST` `n `
- `LAST` `n`
- `boolean-expression `(dimensioned by NAME)

You can specify a qualified object name to indicate the attached workspace in which the object resides. As an alternative, you can use the AW argument to specify the workspace. Do not use both.

When you do not use a qualified object name or the AW argument to specify an analytic workspace, Oracle OLAP looks for the object in the current workspace.

FIRST
LAST
The logical position in the NAME dimension to which Oracle OLAP moves the objects specified by the name argument. Specifying FIRST moves the objects to the beginning of the NAME dimension. Specifying LAST (the default) moves the names to the end of the NAME dimension.

BEFORE name2
AFTER name2
The position before or after a particular object (name2) to which Oracle OLAP moves the objects specified by the name argument.

AW workspace
The name of an attached workspace in which you want to move the object. When you do not use a qualified object name or the AW argument to specify an analytic workspace, objects are moved in the current workspace.

#### Usage Notes

Alphabetizing Your Objects

You can arrange your workspace objects alphabetically with the following statements, which work on the NAME dimension.

    SORT NAME A NAME
    MOVE CHARLIST(NAME) FIRST

#### Examples

Example 10-67 Moving a Relation

This example shows how to move the relation `desc.product` after `product`. The OLAP DML statement

    SHOW CHARLIST(NAME)

produces the following list (annotation has been added).

    product           <--- Position of product
    district
    division
    line
    region
    marketlevel
    market
    month
    year
    quarter
    desc.product      <--- Old position of desc.product
    region.district
    division.product
    ...

The following statements

    MOVE desc.product AFTER product
    SHOW CHARLIST(NAME)

change the workspace order and produce the following list (annotation has been added).

    product           <--- Position of product
    desc.product      <--- New position of desc.product
    district
    division
    line
    region
    marketlevel
    market
    month
    year
    quarter
    region.district
    division.product
    ...

### 10.23 OUTFILE

The OUTFILE command lets you redirect the text output of statements to a file.

**See Also:**

"[File Reading and Writing Options](olap-dml-options.md)"

#### Syntax

OUTFILE {EOF \| TRACEFILE \| \[APPEND\] file-name \[NOCACHE\] \[NLS_CHARSET charset-exp\]}

#### Parameters

EOF
The current outfile is closed and output is redirected to the default outfile.

TRACEFILE
Specifies that the output should be directed to the Oracle trace file, which is identified by the TRACEFILEUNIT option.

APPEND
Specifies that the output should be added to the end of an existing disk file. When you omit this argument, the new output replaces the current contents of the file.

file-name
A text expression that is the name of the file to which output should be written. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use a CDA statement to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

NOCACHE
Specifies that Oracle OLAP should write lines to the outfile as they are generated. Without this keyword, Oracle OLAP reduces file I/O activity by saving text and writing it periodically to the file. The NOCACHE keyword slows performance significantly, but it ensures that every line is immediately recorded in the outfile. This argument must be specified after file-name

NLS_CHARSET charset-exp
Specifies the character set that Oracle OLAP uses when writing data to the file specified by file-name which allows Oracle OLAP to convert the data accurately into that character set. This argument must be specified after file-name. When this argument is omitted, then Oracle OLAP writes the data to the file in the database character set, which is recorded in the NLS_LANG option.

#### Usage Notes

Outfiling a PERMIT_READ or PERMIT_WRITE Program

The contents of a [PERMIT_READ](olap-dml-programs.md) or a [PERMIT_WRITE](olap-dml-programs.md) program is emptied when outfiled. To successfully copy the contents of these programs to and from analytic workspaces, rename them before using OUTFILE; and then, after using INFILE to copy them into an analytic workspace, name them back to PERMIT_READ or PERMIT_WRITE.

Current Outfile Identifier

As a first step, every OUTFILE statement closes the current outfile. When OUTFILE opens a new outfile on disk, it automatically assigns to it an arbitrary `INTEGER` as its file unit number. The current file unit number is held in the OUTFILEUNIT option.

Appending to an Outfile

When you send output to a file and then send output to a second file, the first file does not remain open. To resume sending output to the first file, you must execute another OUTFILE statement and include the APPEND file-name phrase.

Automatic Closing of Outfile

When you use OUTFILE file-name to direct output to a disk file, OUTFILE closes any outfile currently open. OUTFILE issues a close even when the new file is not actually opened (as when you specify an invalid file-name in an OUTFILE statement).

Paging Options and Redirected Output

The paging options control the organization of text output in pages. Examples are: BMARGIN, LINENUM, LINELEFT, PAGESIZE, PAGENUM, PAGEPRG, PAGING, TMARGIN, and LSIZE. The paging options have a separate value for each separate outfile. When you set a paging option to control output to a disk file, the new value remains in effect until you use an OUTFILE statement again to redirect output. At this point, the paging option returns to its default value. Therefore, when you want a paging option to have a particular value for a disk file, you generally have set it after you execute an OUTFILE statement.

Current and Default Outfiles

The current outfile is the destination for the output of statements, such as REPORT and DESCRIBE, that produce text. When you have not used an OUTFILE statement to send output to a file, Oracle OLAP uses your default outfile.

#### Examples

Example 10-68 Sending a Report to an Output File

In this example, you want to send the output of a REPORT statement to an output file.

    OUTFILE 'budget.rpt'
    REPORT budget
    OUTFILE EOF

Example 10-69 Directing Output to a File

Suppose you have a program called `year.end.sales`, and you want to save the report it creates in a file. Type the following commands to write a file of the report. In this example, `userfiles` is a directory object and `yearend.txt` is the name of the file.

    OUTFILE 'userfiles/yearend.txt'
    year.end.sales
    OUTFILE EOF

Now the file contains the `year.end.sales` report. You can add more reports to the same file with the `APPEND` keyword for OUTFILE. Suppose you have another program called `year.end.expenses`. Add its report to the file with the following commands. Remember that without `APPEND`, an OUTFILE statement overwrites the expense report.

    OUTFILE APPEND 'userfiles/yearend.txt'
    year.end.expenses
    OUTFILE EOF

### 10.24 PAGE

The PAGE program forces a page break in output when PAGING is set to `YES`. An optional argument to PAGE specifies a conditional page break based on how many lines are left on the page.

The PAGE program is commonly used in report programs. It is meaningful only when PAGING is set to `YES` and only for output from statements such as REPORT and LISTNAMES.

#### Syntax

PAGE \[n\]

#### Parameters

n
A positive `INTEGER` expression that indicates that a page break should occur only when there are fewer than n lines left on the current page. When the number of lines left equals or exceeds n, no page break occurs. See Example 10-70.

#### Usage Notes

Top of Page

No page break occurs when you are already at the top of a page when a PAGE statement is executed.

Producing the Header

The PAGE program signals that further output should be produced on a new page, but it does not produce a header on the new page unless there is further output. When there is further output, Oracle OLAP produces the heading that is defined by the current PAGEPRG program and then starts producing the output.

#### Examples

Example 10-70 Keeping Lines Together

Suppose you have 12 lines of data that would be hard to read when interrupted by a page break, so you want to prevent such an interruption. Use the `PAGE` `12` statement immediately before the statements that produce the 12 lines of data. A page break occurs before the 12 lines of data only when there are less than 12 lines left on the page. When there are 12 lines or more left at that point, output continues on the same page.

Example 10-71 Forcing a Page Break

The following lines from a report program force a page break at the start of each loop for `district` which makes the report for each district start at the top of a page. (The report program uses a heading program called `report.head` to create a customized heading. See the [PAGEPRG](olap-dml-options.md) option for information on customized heading programs.)

    PUSH PAGING PAGEPRG
    PAGING = YES
    PAGEPRG = 'report.head'
    FOR district
       DO
       PAGE
       ROW district
       BLANK
       FOR month
          ROW WIDTH 8 month sales sales.plan
       DOEND
    PAGE
    POP PAGING PAGEPRG

### 10.25 PARSE

Use the PARSE command to parse a specified group of expressions. When the argument can be parsed, PARSE determines the number of expressions in it and their text, object type, data type, and the number and names of their dimensions. This information is stored internally by Oracle OLAP, but can be obtained with the INFO function.

A PARSE statement is especially useful when you want to accept expressions as arguments to a program.

#### Syntax

PARSE text-expression

#### Parameters

text-expression
A text expression that contains one or more smaller expressions to be parsed. When you are processing program arguments, you can specify an ARGS function as the text expression that contains all the arguments for the program.

#### Usage Notes

Obtaining Information Produced by a PARSE Statement

See the [INFO (PARSE)](olap-dml-functions-a-k.md) function for an explanation of how to obtain the information produced by a PARSE statement.

#### Examples

Example 10-72 Parsing the Arguments to a Program

In a simple report program, you want to specify the data to be reported as an argument to the program. You want to be able to specify an expression and the name of a data variable.

Suppose you want to display each of the arguments with a different column width, which means you must process the arguments individually. The ARGS function can only process them together. So you use PARSE and INFO to parse the arguments and produce individual columns for each of them. Here is a sample program.

    DEFINE report1 PROGRAM
    PROGRAM
    PUSH month product district DECIMALS
    DECIMALS = 0
    LIMIT month TO FIRST 2
    LIMIT product TO ALL
    LIMIT district TO 'Chicago'
    PARSE ARGS
    REPORT ACROSS month WIDTH 8 <&INFO(PARSE FORMULA 1) -
       WIDTH 13 &INFO(PARSE FORMULA 2)>
    POP month product district DECIMALS
    END

When you run the program, you can supply either the names of variables (such as `sales`) or expressions (such as` sales-expense`) or one of each as arguments. The following REPORT statement produces the illustrated report.

    report1 sales sales-expense
     
    DISTRICT: CHICAGO
                 --------------------MONTH--------------------
                 --------JAN95--------- --------FEB95---------
    PRODUCT       SALES   SALES-EXPENSE  SALES   SALES-EXPENSE
    ------------ -------- ------------- -------- -------------
    Tents          29,099         1,595   29,010         1,505
    Canoes         45,278           292   50,596           477
    Racquets       54,270         1,400   58,158         1,863
    Sportswear     72,123         7,719   80,072         9,333
    Footwear       90,288         8,117   96,539        13,847

### 10.26 PERMIT

The PERMIT command lets you grant or deny read-only and read/write access permission for workspace objects and for specific values of dimensions and dimensioned objects. You can also use PERMIT to grant or deny permission to maintain dimensions and to change permission for workspace objects.

In general, access permissions that you set for a dimension are meaningful not only for that dimension, but also for the objects dimensioned by that dimension as explained more fully in "How Dimension Permission Interacts with Permissions for Other Objects". Access permissions that you set for other objects are limited in scope to that particular object. Various conditions determine when permission changes take effect as discussed in "When Permission Changes Take Effect"

**See Also:**

"Important Considerations Before You Change the Permissions of an Object", "[Startup Programs](olap-dml-programs.md)", "[Permission Programs](olap-dml-programs.md)", [PERMITERROR](olap-dml-options.md) option, and PERMITRESET command

**Tip:**

The PERMIT command assigns permission to the object most recently defined or considered. When the definition of the object is not the current one, first use a CONSIDER statement before issuing PERMIT commands for the object

#### Syntax

PERMIT {READ\|WRITE\|MNT\|PERMIT} \[WHEN permission-condition...\]

#### Parameters

READ
Depending on the permission conditions, grants or restricts permission to read all of the values of an object or only certain values in a dimension or dimensioned object.

Note that restricting read permission for a dimension also restricts maintain permission for that dimension. Also, when you grant read permission for an object, write permission is also allowed for the values you can read, unless you deny it with an explicit PERMIT WRITE statement.

WRITE
Depending on the permission conditions, grants or restricts permission to modify any of the values of an object or only certain values of a dimensioned object.

Restricting write permission for an object does not necessarily mean that the object is totally unavailable. For example, when you have restricted write access to a calculation specification (that is, an aggmap object, program, model, or formula, you can still execute the object— you just cannot edit the contents of the calculation specification.

Oracle OLAP does not prevent you from granting write permission for values that you cannot read within a dimensioned object. When you have both a PERMIT READ and a PERMIT WRITE statement for a dimensioned object, and some values which satisfy the permission conditions for write do not fall within the subset of values which satisfy the permission conditions for read, then those values may be modified but not seen.

**Tip:**

Write permission is not meaningful for dimensions— except to provide write access to objects dimensioned by the dimension. To grant or restrict the ability to add values to a dimension, issue PERMIT MNT statements for the dimension instead.

**See Also:**

"When the only PERMIT Statement for an Object is a PERMIT WRITE Statement"

MNT
Depending on the permission conditions, grants or restricts permission to maintain a dimension.

Note that you cannot grant maintain permission to a dimension for which you have restricted read permission. Oracle OLAP automatically denies maintain permission for a dimension when there is restricted read permission for that dimension.

PERMIT
Depending on the permission conditions, grants or restricts permission to use the PERMIT command to change the read, write, maintain, or permit permission for the object.

Note that unless explicitly you explicitly deny permit permission for an object, permit permission is allowed for an object no matter what other permissions are set for that object.

WHEN permission-condition...
When you omit the WHEN clause and execute a PERMIT READ, PERMIT WRITE, or PERMIT MNT statement, Oracle OLAP restores full read, write, or maintain permission to the object.

When you include the WHEN clause, the conditions for granting read, write, maintain, or permit permission consist of one or more Boolean expressions depending on whether or not the object has dimensionality, the type of permission you are setting and, for read and write permissions, whether or not the object has dimensionality:

- When you are specifying permit permission, maintain permission, or read or write permission that applies to an object without dimensionality or when you want the read or write permissions to apply to all the values of a dimensioned object, specify the permission condition as a Boolean expression that evaluates to a single value. (Not that if you do specify a dimensioned Boolean expression to specify permissions for an object without dimensionality or when you are specifying permit or maintain permission, then PERMIT uses the first value in status.)

  **Tip:**

  Avoid specifying a Boolean value as a permission condition (for example, `YES` or `NO`) for a PERMIT PERMIT statement. Instead specify the permission condition as a Boolean variable, a function that returns a Boolean result, or a Boolean value calculated by comparison operators. In this way, when permit permission has been denied, you can restore it by setting the value of the Boolean and executing a PERMITRESET statement. If you ever do lock up an object and are unable to modify its permission, you can specify permit permission for it in the workspace permission program for that workspace, then detach and reattach the workspace.

- If you are specifying read or write permission that applies to individual dimension values or to slices of a dimensioned object, specify one permission condition for each dimension of interest. In this case, the WHEN clause has the following syntax and each dimensioned permission condition consists of a Boolean expression dimensioned by a dimension of the object.

  - `WHEN` `dimensioned_permission_condition1`
  - `    [BY ``dimensioned_permission_condition2`
  - `[UNION` `dimensioned_permission_condition2A`\]...

  Use the UNION phrase to efficiently access the union of several symmetric subcubes of a multidimensional variable.

  Note that if a Boolean expression for a dimensioned permission condition has any extra dimensions in addition to an object dimension, PERMIT takes the first value in status to determine which column of Boolean values to use. The intersection of the `YES` values for each dimension (a logical `AND` of the conditions) is the subset of values within the object to which the permission applies. When any of the object dimensions are not represented by a dimensioned permission condition, then Oracle OLAP assumes `YES` for all those dimension values.

#### Usage Notes

Important Considerations Before You Change the Permissions of an Object

Keep the following important considerations in mind before you change the permissions of an object:

- You must have permit permission for an object to issue PERMIT commands against it.

- Do not lock out the DBA user, who must always have access to everything in the workspace.

- Issuing PERMIT statements against an INTEGER dimension may result in undesired behavior. Dimensions with an INTEGER data type have values identified by their numeric position. PERMIT renumbers INTEGER dimensions to keep the normal sequence of `INTEGER` values (1, 2, 3, ...). When you must use PERMIT to change the default access rights for an INTEGER dimension and this behavior is not desirable, redefine the dimension with a different, non-integer data type.

When Permission Changes Take Effect

Within [PERMIT_READ](olap-dml-programs.md) and [PERMIT_WRITE](olap-dml-programs.md) programs, permissions ares only evaluated when you issue an explicit PERMIT or PERMITRESET statement and then reference the targeted object.

**Note:**

AW ATTACH automatically executes a PERMITRESET immediately after executing an analytic workspace permission program. Executing PERMITRESET causes the workspace to be attached with all permission implemented

Once an analytic workspace is attached and any PERMIT_READ and PERMIT_WRITE programs have executed, permission changes specified by a PERMIT statement take effect:

- When a PERMITRESET statement executes.

- When you are targeting any object (except a dimension), and the permission condition consists of a single Boolean variable, any changes to that Boolean variable affect the permission immediately. (You never have to execute a PERMITRESET in this case.)

- In other situations, if you do not issue a PERMITRESET statement, permission are evaluated upon next reference to the object.

  **Note:**

  The OBJ function is an exception to this rule. Because OBJ does not load the object into memory, it does not reflect any changes to the object's permission since the last time it was loaded. When you want OBJ to provide information based on new permission criteria, execute a LOAD statement before the OBJ statement.

When the only PERMIT Statement for an Object is a PERMIT WRITE Statement

When the only PERMIT statement for an object is a PERMIT WRITE, then read permission is provided by default for the object. The default read permission is provided independent of the value of the permission condition(s) for the PERMIT WRITE statement. Consequently, a PERMIT WRITE with a single-cell permission condition which evaluates to `NO` provides read-only access to an nondimensional object or to all the values of a dimensioned object.

When the only PERMIT statement for an object is a PERMIT WRITE with dimensioned permission conditions, it designates some values for read/write access and the remaining values for read-only access. See Example 10-73.

How Dimension Permission Interacts with Permissions for Other Objects

All dimensioned data is affected by the read permission on its dimensions. The dimension values that satisfy the read permission condition determine the default status for the dimension. The values of dimensioned objects that correspond to dimension values without read permission are inaccessible.

However, in order for write permission associated with a dimension to apply to other objects dimensioned by it, there must be at least one PERMIT statement associated with the dimensioned object.

- When you want a dimensioned object to inherit write permission from its dimensions, but you do not want it to have permission of its own, which could interact with the dimension permission, you can simply use a PERMIT READ with a single-cell permission condition that evaluates to `YES`.

- When you want a dimensioned object to inherit write permission from its dimensions, and you also want it to have permissions of its own, understand how dimension permission interacts with individual object permissions before setting them.

Dimension permission interacts with permission for most of the objects dimensioned by it in the following ways:

- The access permissions of a dimension apply to all dimension surrogates defined for that dimension. You cannot use a PERMIT statement on a dimension surrogate.

- When there is read or write permission associated with a dimension, but no permission restriction associated with an object dimensioned by that dimension, then the permission for the dimensioned object is the same as the dimension permission.

- When there is read permission associated with both the dimension and the dimensioned object, Oracle OLAP determines the values with read permission in the object by taking the intersection of the values with read permission in the dimension and the values with read permission in the object.

- When there is write permission associated with both the dimension and the dimensioned object, Oracle OLAP determines the values with write permission in the object by taking the intersection of the values with read permission in the dimension, the values with write permission in the dimension, and the values with write permission in the object.

However, this is not the case for relations and valuesets. When there is restricted write permission for a dimension of a relation or a valueset, it does not affect relations and valuesets dimensioned by that dimension.

Determining Permission

The permission associated with an object is provided, like an LD, when you describe it using a DESCRIBE statement. The only exception is when you are denied permit permission for the object. In this case, no permission is provided when you describe it.

Advantages of PERMIT Over LIMIT as a Tool for Scoping

As a tool for scoping within application programs, PERMIT has several advantages over the LIMIT command. To restrict the scope of a dimensioned object according to a Boolean expression, you have to use two LIMIT statements, a `LIMIT` and a LIMITKEEP. You only need one PERMIT statement to do the same thing. Moreover, application users cannot change the restricted scope set by PERMIT commands in application programs. Application users can easily change the scope set by LIMIT commands in application programs simply by executing more LIMIT commands.

Handling Permission Violations

You can use the PERMITERROR option to control the way Oracle OLAP handles attempted violations of the permission established by PERMIT commands for variables. The default value of PERMITERROR is `YES`, meaning that Oracle OLAP signals an error when a user attempts to access a value for which permission is denied. When you set PERMITERROR to `NO`, Oracle OLAP simply denies access without signaling an error condition which is useful when you want to do a report of a dimensioned variable for which you have partial permission without limiting the dimensions to the permitted values up front. With PERMITERROR set to `NO`, values for which you do not have read permission appear as `NA` values in the report.

#### Examples

Example 10-73 Variable Permission

For a variable `sales` dimensioned by `month`, `product`, and `district`, you might have three dimensioned permission conditions in the form of three variables as illustrated in the following report.

    MONTH.BOOL<MONTH>  PROD.BOOL<PRODUCT>  DISTRICT.BOOL<DISTRICT>
    -----------------  ------------------  -----------------------
    Jan95    NO        Tents     YES       Boston     NO
    Feb95    YES       Canoes    YES       Atlanta    NO
    Mar95    NO        Racquets   NO       Chicago    YES
    ...      ...       ...        ...      ...        ...

When the `YES` values shown in the preceding example are the only `YES` values in the permission conditions, the following PERMIT statement provides read/write access to `sales` data for tents and canoes sold in Chicago in Feb95. In the absence of a `PERMIT` `READ` statement for `sales`, Oracle OLAP provides read-only permission for all the other values of `sales`.

    PERMIT WRITE WHEN district.bool BY prod.bool BY month.bool

You can restore full write permission with the following PERMIT statement.

    PERMIT WRITE

When there is no restricted write permission for` sales`, the following PERMIT statement provides read/write access to sales data for tents and canoes sold in Chicago in Feb95, and it causes all other values of sales to be invisible.

    PERMIT READ WHEN district.bool BY prod.bool BY month.bool

Example 10-74 Dimensioned Permission Condition

To restrict access to the `product` dimension you need a permission condition dimensioned by `product`. However, when the permission condition has a second dimension, say `authority`, PERMIT selects the BOOLEAN values that pertain to `product` based on the first value in status of `authority`. When you restrict read permission on the `authority` dimension to one value, PERMIT uses that value to determine the BOOLEAN values of the permission condition for `product`. The REPORT commands produce the output that follows them.

    DEFINE authority DIMENSION TEXT
    MAINTAIN authority ADD OTHER DBA
    DEFINE prod_authority VARIABLE BOOLEAN <product authority>
    ...
    " Assign values to the variable
    ...
    REPORT prod_authority
     
                  -----------------PROD_AUTHORITY------------------
                  --------------------PRODUCT----------------------
    AUTHORITY     Tents   Canoes   Racquets   Sportswear   Footwear
    ---------     -----   ------   --------   ----------   --------
    Other            NO       NO        YES          YES        YES
    Dba             YES      YES        YES          YES        YES

    CONSIDER product
    PERMIT READ WHEN prod_authority
    PERMITERROR = NO
    RPEPORT product
     
    PRODUCT
    -------------
    Racquets
    Sportswear
    Footwear

    CONSIDER authority
    PERMIT READ WHEN AUTHORITY EQ 'dba'
    PERMITRESET
    Report product
     
    PRODUCT
    -------------
    Tents
    Canoes
    Racquets
    Sportswear
    Footwear

Example 10-75 User-Defined Boolean Function

In the following example, `usercheck` is a user-defined Boolean function that checks the current value of the variable `thisuser` against a list of user IDs. `usercheck` returns `NO` when the current value of `thisuser` is not in the list. The following PERMIT statement applied to the `sales` variable provides read-only access to all values of `sales` when `usercheck` returns `NO`. It provides read/write access to all values of `sales` when `usercheck` returns `YES`.

    PERMIT WRITE WHEN usercheck(thisuser)

The following PERMIT statement, applied to the variable `price`, provides full access to all values of `price` when `usercheck` returns `YES`. When it returns `NO`, it denies all access to the `price` variable.

    PERMIT READ WHEN usercheck(thisuser)

Example 10-76 Individual Cells

When you want to prevent access to one particular sales figure, say for racquets in Boston in March of 1997, you can create a Boolean variable and use it in a PERMIT statement as illustrated in the following statements.

    DEFINE sales.bool VARIABLE BOOLEAN <month product district>
    sales.bool = yes
    LIMIT month TO 'Mar97'
    LIMIT product TO 'Racquets'
    LIMIT district TO 'Boston'
    sales.bool = no
    CONSIDER sales
    PERMIT READ WHEN sales.bool

Example 10-77 Individual Dimension Values

The following PERMIT commands applied to the `district` dimension prevent access to all dimension values except `Boston` and `Atlanta`. They provide read/write access for all data related to `Boston` and read-only access for all data related to `Atlanta`. They also prevent anyone with a user ID not allowed by the function `usercheck` (see Example 10-75) from modifying the permission for `district`.

    PERMIT READ WHEN district EQ 'Boston' OR district EQ 'Atlanta'
    PERMIT WRITE WHEN district EQ 'Boston'
    PERMIT PERMIT WHEN usercheck(thisuser)

### 10.27 PERMITRESET

The PERMITRESET command causes the values of permission conditions to be reevaluated. Permission conditions consist of one or more Boolean expressions that designate the criteria used by PERMIT commands associated with an object.

When permission conditions are dimensioned, they indicate which values of a dimensioned object PERMIT targets for permission. A single-cell permission condition can indicate any Boolean criterion, such as whether or not a particular user may access the object.

When you want to keep the existing PERMIT commands for an object, but you want the permission conditions associated with them to be recalculated, issue a PERMITRESET statement. The permission for that object is based on the new values of the permission conditions the next time you use the object in an OLAP DML statement.

**See Also:**

"[Startup Programs](olap-dml-programs.md)", PERMIT command, and [PERMITERROR](olap-dml-options.md) option

#### Syntax

PERMITRESET  \[object_name\]  \[READ\|WRITE\]

#### Parameters

object_name
Specifies the name of an object for which permission conditions should be reevaluated. When you do not specify an object name, the permission conditions for all objects are reevaluated.

READ
Causes reevaluation of the permission conditions for `PERMIT` `READ` commands only, or for a `PERMIT` `READ` statement for the specified object.

WRITE
Causes reevaluation of the permission conditions for `PERMIT` `WRITE` commands only, or for a `PERMIT` `WRITE` statement for the specified object.

#### Examples

Example 10-78 Resetting Permission

In the following example, the user-defined Boolean function `usercheck` checks the current value of the variable `thisuser` and returns `YES` only when it is greater than `100`. Access to the variable `uservar` is only allowed when `thisuser` is greater than `100`. However, when you change the value of `thisuser` to a value less than or equal to `100` without resetting the permission for `uservar`, access is still permitted.

The statement

    DESCRIBE uservar

produces the following output.

    DEFINE USERVAR VARIABLE INTEGER
    PERMIT READ WHEN usercheck(thisuser)

The statement

    SHOW uservar

produces the following output.

    5

The statement

    DESCRIBE usercheck

produces the following output.

    DEFINE USERCHECK PROGRAM BOOLEAN
    PROGRAM
      ARG thisuser INT
      TRAP ON errorexit NOPRINT
      IF thisuser GT 100
              THEN RETURN YES
      ELSE RETURN NO
      errorexit:
           RETURN NO
    END

The statement

    DESCRIBE thisuser

produces the following output.

    DEFINE THISUSER VARIABLE INTEGER

The statement

    SHOW thisuser

produces the following output.

    101

The statements

    thisuser = 100
    SHOW uservar

produces the following output.

    5

The statements

    PERMITRESET luservar READ
    SHOW uservar 

produce the following error.

    ERROR: You do not have permission to read this value of USERVAR

### 10.28 POP

The POP command restores the status of a dimension (including the NAME dimension), the status of a valueset, or the value of an option or single-cell variable that was saved with a previous PUSH statement.

PUSH and POP are commonly used within a program to make changes to options and dimension status that apply only during the program's execution. Afterward, the options and status are the same as they were before the execution of the program.

**See Also:**

POPLEVEL, PUSH, PUSHLEVEL, and [CONTEXT command](olap-dml-commands-a-g.md)s

#### Syntax

POP name1 \[nameN\]

#### Parameters

name
The name of a dimension, valueset, variable, or option that was specified in a previous PUSH statement, whose saved value you want to restore.

#### Examples

For an example of using POP, see Example 10-84.

### 10.29 POPLEVEL

The POPLEVEL command (abbreviated PPL) restores all values saved with PUSH commands that were executed since the last POPLEVEL statement specifying the same marker.

You must use PUSHLEVEL to mark a starting point for a series of PUSH commands before you can use POPLEVEL to restore the saved values. POPLEVEL itself marks the end of the series. You can use POPLEVEL only within programs.

**See Also:**

"Considerations When Designing PUSHLEVEL and POPLEVEL Statements", POP, PUSH, PUSHLEVEL, and [CONTEXT command](olap-dml-commands-a-g.md)s

#### Syntax

POPLEVEL marker-expression \[DISCARD\]

#### Parameters

marker-expression
A text value used as a marker. This value must be the same as the value used in the corresponding PUSHLEVEL statement to mark the start of a series of saved values being popped.

DISCARD
Specifies that the pushed values for that level are discarded when you issue a POPLEVEL statement. When you do not specify DISCARD, the values that were pushed are used to reset the pushed objects.

#### Usage Notes

Possible Uses for POP LEVEL Statement

Two possible uses for POPLEVEL statements are:

- After a series of increasingly broadening or narrowing LIMIT commands, each with a corresponding PUSH.

- After a single extremely long and complicated PUSH statement, or a series of short ones given throughout a program, that may need a lot of editing. PUSHLEVEL and POPLEVEL allow you to edit the arguments for a long and complicated PUSH statement without also having to edit a corresponding long and complicated POP statement.

#### Examples

To see a sample program using POPLEVEL, see the example for the PUSHLEVEL command.

### 10.30 PROGRAM

The PROGRAM command enters completely new contents into a new or existing program. When the program already has lines of code, Oracle OLAP overwrites them.

To use PROGRAM to enter the contents of a program object, the program object definition must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER statement to make it the current definition.

An alternative to a PROGRAM statement is an EDIT PROGRAM statement, which is available only in OLAP Worksheet. An EDIT PROGRAM statement opens an Edit window in which you can add, delete, or change the specification for a program object.

**See Also:**

For a discussion of writing, compiling, and debugging OLAP DML programs, see [OLAP DML Programs](olap-dml-programs.md)

#### Syntax

PROGRAM \[contents\]

#### Parameters

contents
A text expression that is the OLAP DML statements that are the lines of the program. You can use most OLAP DML statements within a program. For a discussion of writing, compiling, and debugging OLAP DML programs, see [OLAP DML Programs](olap-dml-programs.md).

The maximum number of lines you can have in a program is 32,000.When coding a PROGRAM statement at the command line level, separate program lines with newline delimiters (`\n`), or use the JOINLINES function as shown in "Example 10-80".

#### Examples

Example 10-79 User-Defined Function with Arguments

Suppose your analytic workspace contains a variable called `units.plan`, which is dimensioned by the `product`, `district`, and `month` dimensions. The variable holds INTEGER data that indicates the number of product units that are expected to be sold.

Suppose also that you define a program named`units_goals_met`. This program is a user-defined function. It accepts three dimension-value arguments that specify a given cell of the `units.plan` variable, and it accepts a fourth argument that specifies the number of units that were actually sold for that cell. The program returns a Boolean value to the calling program. It returns `YES` when the actual figure comes up to within 10 percent of the planned figure; it returns `NO` when the actual figure does not.

The definition of the `units_goals_met` program is follows.

    DEFINE units_goal_met PROGRAM BOOLEAN
    LD Tests whether actual units met the planned estimate
    "Program Initialization
    ARGUMENT userprod  TEXT
    ARGUMENT userdist  TEXT
    ARGUMENT usermonth TEXT
    ARGUMENT userunits INTEGER
    VARIABLE answer boolean
    TRAP ON errorlabel
    PUSH product district month
    "Program Body
    LIMIT product TO userprod
    LIMIT district TO userdist
    LIMIT month TO usermonth
    IF (units.plan - userunits) / units.plan GT .10
       THEN answer = NO
       ELSE answer = YES
    "Normal Exit
    POP product district month
    RETURN answer
    "Abnormal Exit
    errorlabel:
    POP product district month
    SIGNAL ERRORNAME ERRORTEXT
    END

To execute the `units_goal_met` program and store the return value in a variable called `success`, you can use an assignment statement (SET).

    success = units_goal_met('TENTS' 'BOSTON' 'JUN96' 2000)

Example 10-80 Program On the Fly

This example creates a flexible report program "on the fly" to avoid the inefficiencies of a more conventional program using ampersand substitution. The conventional program would contain the following loop.

    FOR &dimname
       ROW &dimname &varname

To avoid ampersand substitution, define a program, for example, STANDARDREP, and leave it without any code in it, or with code that can be discarded. Then in your report program, insert lines such as the following.

    DEFINE myreport PROGRAM
    LD Program to produce my report
    PROGRAM
    ARGUMENT dimname TEXT
    ARGUMENT varname TEXT
    ...
    CONSIDER standardrep
    PROGRAM JOINLINES(JOINCHARS('FOR ', dimname) - 
       JOINCHARS('   ROW ', dimname, ' ', varname) )
    COMPILE standardrep
    standardrep
    ...

Example 10-81 Program from an Input File

This example presents the text of a simple program that is in an ASCII disk file called `salesrep.inf`. The first line in the file defines the program, the second line contains a PROGRAM statement, and the subsequent lines provide the lines of the program.

    DEFINE salesrep PROGRAM
    PROGRAM
    PUSH month product district
    TRAP ON haderror
    LIMIT month TO FIRST 3
    LIMIT product TO FIRST 3
    LIMIT district TO ALL
    REPORT grandtotals sales
    haderror:
    POP month product district
    END

To include the `salesrep` program in your analytic workspace, you can execute the following statement.

    INFILE 'salesrep.inf'

You can create an input file from an existing program using an OUTFILE statement

Example 10-82 Using OLAP Worksheet Instead of a PROGRAM Statement

When you use OLAP Worksheet to create a program, you can use an EDIT statement to display an Edit window where you can enter the contents. For example, use the following statements to define a new program named `salesrep` and display it in an Edit window.

    DEFINE salesrep PROGRAM
    EDIT salesrep

### 10.31 PROPERTY

The PROPERTY command adds or deletes properties to the most recently defined or considered object (see the [DEFINE PROGRAM](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands). A property is a named value that is associated with a given definition. You can assign one or more properties to any type of definition. For example, you can assign a property to an object so you know how many decimal places to use when preparing a report on the object.

#### Syntax

PROPERTY { name value \| DELETE {ALL \| name} }

#### Parameters

name
A text expression that contains the name of the property. The property name can be from 1 to 256 bytes long.

**Note:**

Do not create your own properties with names that begin with a `$` (dollar sign). Properties with names beginning with a `$` (dollar sign) are reserved for Oracle OLAP to use as "system" properties that Oracle OLAP interprets in predetermined ways.

Property names have the `TEXT` data type, unless you include a Unicode escape sequence in the value you specify for the name, or unless you explicitly convert the value you specify to `NTEXT` (using the CONVERT or TO_NCHAR functions).

value
An expression that contains the value of the property. The property value can have one of the following data types: `NUMBER`, I`NTEGER`, `LONGINTEGER`, `DECIMAL`, `SHORTDECIMAL`, `TEXT,` `NTEXT`, `ID`, `BOOLEAN`, `DATE`, or `DATETIME`. Oracle OLAP determines the data type based on the value that you specify. For example, when you specify `YES`, then Oracle OLAP assumes a type of `BOOLEAN`. When you specify a date value that is stored in a variable of type `DATE`, then Oracle OLAP assumes a type of `DATE` for the property.

DELETE ALL
DELETE name
Deletes either all of the properties of the object or only the property you specify for name. You can specify only one name at a time.

#### Usage Notes

Triggering Program Execution When PROPERTY Executes

Using the TRIGGER command, you can make a PROPERTY statement an event that automatically executes an OLAP DML program. See "[Trigger Programs](olap-dml-programs.md)" for more information

Changing a Property Value

When you execute a PROPERTY statement that assigns a new value to an existing property name, then the new value overwrites the previous one.

Determining Property Values with OBJ

To use properties with OLAP DML statements, you must obtain the values by using the property-related keywords of the OBJ function. For example, suppose a property called `decplace` stores the number of decimal places to use when reporting an object. When you execute a REPORT statement, you can use the OBJ function with the PROPERTY keyword to obtain the value of the `decplace` property and use that value with the REPORT statement's DECIMAL attribute.

Listing Property Values with FULLDSC

You can list the properties of an object by using a FULLDSC statement. You can use the output from FULLDSC to create new objects. See the [FULLDSC](olap-dml-commands-a-g.md) program for more information.

#### Examples

Example 10-83 Adding Properties to a Variable

The following statements add the properties `decplace` and `prgname` to the `actual` variable and assign the `decimal` `4` as the value for the `decplace` property and the text `repprg` as the value for the `prgname` property.

    CONSIDER actual
    PROPERTY 'decplace' 4
    PROPERTY 'prgname' 'repprg'

### 10.32 PUSH

The PUSH command saves the current status of a dimension (including the NAME dimension), the status of a valueset, or the value of an option or single-cell variable. You can then restore these saved values and status at a later time with a POP statement.

PUSH and POP are commonly used within a program to make changes to options and dimension status that apply only during the program's execution. Afterward, the options and status are the same as they were before the execution of the program.

**See Also:**

PPOP, POPLEVEL, PUSHLEVEL, and [CONTEXT command](olap-dml-commands-a-g.md)s

#### Syntax

PUSH name1 \[name\]

#### Parameters

name
The name of a dimension, valueset, option, or variable whose status or value you want to save.

#### Usage Notes

Effect of a MAINTAIN Statement on a Dimension's Pushed Status

Using a MAINTAIN statement with a dimension clears that dimension's pushed status lists. For example, suppose you have pushed the dimension `month` several times, with different limits each time. When you then use a MAINTAIN statement to perform any maintenance activity on the `month` dimension, Oracle OLAP resets the status of `month` to `ALL` (the default), and popping that dimension has no effect.

#### Examples

Example 10-84 Saving and Restoring Values

The following program uses PUSH and POP to produce sales figures without decimal places for a specific selection of products, districts, and months, and then restores the status settings and the value of DECIMALS to what they were before the program was run.

    DEFINE report1 PROGRAM
    PROGRAM
    TRAP ON cleanup
    PUSH DECIMALS product district month
     
    DECIMALS = 0
    LIMIT product TO 'Sportswear' 'Footwear'
    LIMIT district TO 'Atlanta' 'Dallas'
    LIMIT month TO 'Jan96' TO 'Jun96'
    REPORT sales
     
    cleanup:
    POP DECIMALS product district month
    END

### 10.33 PUSHLEVEL

The PUSHLEVEL command marks the start of a series of PUSH commands. You can then use a corresponding POPLEVEL statement to restore all the values saved by PUSH commands that are executed after PUSHLEVEL. POPLEVEL must specify the same marker as the PUSHLEVEL statement that starts the series. You can use PUSHLEVEL only within programs.

**See Also:**

"Considerations When Designing PUSHLEVEL and POPLEVEL Statements", POP, PUSH, POPLEVEL, and [CONTEXT command](olap-dml-commands-a-g.md)s

#### Syntax

PUSHLEVEL marker-expression

#### Parameters

marker-expression
A text value to mark the start of a series of PUSH commands all of whose saved values are to be popped at once. A POPLEVEL statement that specifies the exact same marker-expression restores the whole series of saved values.

#### Usage Notes

Considerations When Designing PUSHLEVEL and POPLEVEL Statements

Keep the following points in mind when coding pushlevel statements:

- You can nest PUSHLEVEL/POPLEVEL pairs, if you specify a different marker for each pair, as illustrated in the following code.

      PUSHLEVEL 'firstlevel'
      PUSH PAGESIZE DECIMALS       < saves values in FIRSTLEVEL
      ...
      PUSHLEVEL 'secondlevel'
      PUSH month product           < Saves values in SECONDLEVEL
      ...
      POPLEVEL 'secondlevel'       < Restores values in SECONDLEVEL
      ...
      POPLEVEL 'firstlevel'        < Restores values in FIRSTLEVEL

  You do not normally need multiple levels in a single program. However, Oracle OLAP automatically creates nested levels when one program calls another program and each program contains a set of PUSHLEVEL and POPLEVEL commands.

- When you specify the same marker for two or more PUSHLEVEL commands, a POPLEVEL statement specifying that same marker restores values that were saved only since the most recent PUSHLEVEL statement.

- When you specify a different marker for two or more PUSHLEVEL commands, a POPLEVEL statement that specifies the marker of any PUSHLEVEL statement restores all the values that were saved since that statement, including values that were saved after later PUSHLEVEL commands.

#### Examples

Example 10-85 Creating Level Markers

You can use a PUSHLEVEL statement to establish a level marker called `firstlevel`, and then use PUSH to save the current values.

    PUSHLEVEL 'firstlevel'
    PUSH month DECIMALS ZSPELL

The level marker can be any text that is enclosed in single quotation marks. It can also be the name of a single-cell `ID` or `TEXT` variable, whose value becomes the name of the level marker. In the exit sections of the program, you can then use a POPLEVEL statement to restore all the values you saved since establishing the `firstlevel` marker.

    POPLEVEL 'firstlevel'

Example 10-86 Nesting PUSHLEVEL and POPLEVEL Commands

You can nest PUSHLEVEL and POP LEVEL commands to save certain groups of values in one place in a program and other groups of values in another place in a program. The next example shows two sets of nested PUSHLEVEL and POPLEVEL commands.

    PUSHLEVEL 'firstlevel'
    PUSH PAGESIZE DECIMALS "Saves values in FIRSTLEVEL
            ...
    PUSHLEVEL 'secondlevel'
    PUSH month product     "Saves values in SECONDLEVEL
          ...
    POPLEVEL 'secondlevel' "Restores values in SECONDLEVEL
           ...
    POPLEVEL 'firstlevel'  "Restores values in FIRSTLEVEL

Normally, you do not use multiple sets of PUSHLEVEL and POPLEVEL` `commands in a single program. However, the nesting feature comes into play automatically when one program calls another program, and each program contains a set of PUSHLEVEL and POPLEVEL commands.

Example 10-87 One-Step Restoration and Nested Levels

The following program uses `PUSHLEVEL` `'rpt1'` to mark for one-step restoration the original value of DECIMALS and the original status of `month`, `product`, and `district`, even though these are pushed separately in the program.

To demonstrate nesting, the program includes a nested PUSHLEVEL-POPLEVEL pair with `'rpt2'` as its marker and some STATUS commands at various points. You can compare the program's output with the program to see how the status is affected.

    DEFINE sales.RPT PROGRAM
    PROGRAM
    STATUS month product district
     
    PUSHLEVEL 'rpt1'
    PUSH DECIMALS month
    DECIMALS = 0
    LIMIT month TO 'Jan96'
    REPORT WIDTH 8 DOWN district WIDTH 9 ACROSS product: expense
    PUSH product
    LIMIT product TO 'Racquets' 'Sportswear'
    REPORT DOWN district ACROSS product: advertising
     
    PUSHLEVEL 'rpt2'
    PUSH district
    LIMIT district TO 'Atlanta' 'Dallas' 'Chicago'
    REPORT DOWN district ACROSS product: sales
    BLANK
    STATUS month product district
    BLANK
     
    POPLEVEL 'rpt2'
    STATUS month product district
    BLANK
    POPLEVEL 'rpt1'
     
    STATUS month product district
    END

The `sales.rpt` program produces the following output.

    The current status of MONTH is:
    ALL
    The current status of PRODUCT is:
    ALL
    The current status of DISTRICT is:
    ALL
    MONTH: JAN96
             ---------------------EXPENSE---------------------
             ---------------------PRODUCT---------------------
    DISTRICT   Tents    Canoes   Racquets  Sportswear  Footwear
    -------- --------- --------- --------- ---------- ----------
    Boston      31,299    67,527    52,942     49,668    80,565
    Atlanta     41,139    53,186    57,159    108,047    99,758
    Chicago     27,768    45,621    53,756     65,055    81,639
    Dallas      47,063    34,072   118,807    113,629    19,785
    Denver      33,177    42,975    89,144     63,380    36,960
    Seattle     41,043    64,009    26,719     38,970    46,900
    Month: JAN96
                   -----ADVERTISING-----
                   -------PRODUCT-------
    DISTRICT        RAcquets  Sportswear
    -------------- ---------- ----------
    Boston              3,784      3,352
    Atlanta             4,384      9,509
    Chicago             3,351      5,283
    Dallas              8,700      8,340
    Denver              6,215      4,654
    Seattle             2,344      3,726
    MONTH: Jan96
                   --------SALES--------
                   -------PRODUCT-------
    DISTRICT        Racquets  Sportswear
    -------------- ---------- ----------
    Atlanta            61,895    129,616
    Dallas            125,880    128,115
    Chicago            58,649     77,490
    The current status of MONTH is:
    JAN96
    The current status of PRODUCT is:
    RACQUETS, SPORTSWEAR
    The current status of DISTRICT is:
    ATLANTA, DALLAS, CHICAGO
     
    The current status of MONTH is:
    JAN96
    The current status of PRODUCT is:
    RACQUETS, SPORTSWEAR
    The current status of DISTRICT is:
    ALL
     
    The current status of MONTH is:
    ALL
    The current status of PRODUCT is:
    ALL
    The current status of DISTRICT is:
    ALL

### 10.34 RECAP

The RECAP command sends statements that were previously entered during the current session to the current outfile or to a file that you specify. The statements are copied from the command log, which is a list of up to 256 statements that you have entered most recently during the current session.

**Note:**

RECAP statements are not included in the command log.

#### Syntax

RECAP \[number\|ALL\] \[ 'search-text' \] \[ FILE file-name \]

#### Parameters

number
A positive `INTEGER` that indicates the number of statements to be provided. When you specify search-text, RECAP provides this number of statements from the subset that contains the search-text string. When you do not specify search-text, RECAP provides this number of statements from the most recently executed portion of the command log. The default number is 10.

ALL
When you specify search-text, ALL requests every statement that meets the search requirements. When you do not specify search-text, ALL requests every statement in the command log.

search-text
A quoted text literal. When you specify this argument, RECAP searches the statements in the command log for the ones that contain search-text. The search is not case-sensitive. These statements then compose the subset from which RECAP provides number or ALL statements.

FILE file-name
Writes the output of a RECAP statement to the specified file For file-name specify a text expression that is the name of the file to which output should be written. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use a CDA statement to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

#### Usage Notes

Order of search-text Parameter

When you use both the search-text and the ALL or number arguments, you must specify search-text second.

RECAP with No Parameter

When you specify RECAP without an argument, the ten most recent statements are provided.

Re-Executing Statements

You can use the output of RECAP to edit a previously executed statement with REEDIT, or reexecute a previously executed statement with REDO.

Identifying Files and Directories

When specifying files and directories in OLAP DML statements, it is good practice to always enclose them in single quotes.

#### Examples

Example 10-88 Obtaining the Last Three Statements Containing "actual"

The following RECAP statement requests the three most recent statements that included the text literal "actual."

    RECAP 3 'actual'

This statement could produce the following output.

           COMMAND LOG
        3: dsc actual
        5: report total(actual)
        8: report average(actual)

### 10.35 REDO

The REDO command re-executes a statement that you entered earlier in your session. The statement is retrieved from the command log, which is a list of up to 256 statements that you have entered most recently during the current session. REDO enables you to changes in the statement before it is re-executed.

**Note:**

REDO statements themselves are not included in the command log; however, the statements re-executed by REDO are included.

#### Syntax

REDO \[number\|index\] 'original' 'replacement' \[specifier\] 

#### Parameters

number
A positive `INTEGER` that indicates the number of the statement to be re-executed. You can display the statements, with their numbers, using a RECAP statement.

index
A negative `INTEGER` or `0` (zero) that indicates the position of the statement to be re-executed relative to the end of the command log. The most recent statement is `0`, the one before that is `-1`, and so on. The default is `0`.

original
A text literal that is part of the statement to be re-executed.

replacement
A text literal that should replace original when the statement is re-executed.

specifier
A specifier listed in the following table. Each specifier indicates where text replacement should occur in the re-executed statement.

Table 10-2 Valid Values for REDO specifier

| Specifier | Meaning                                                                                                                             |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------|
| `FIRST`   | Indicates that only the first occurrence of original should be changed to replacement.                                              |
| `LAST`    | Indicates that only the last occurrence of original should be changed to replacement.                                               |
| `n`       | A number indicating which occurrence of original should be changed to replacement. For example, `3` indicates the third occurrence. |
| `ALL`     | Indicates that all occurrences of original should be changed to replacement                                                         |
| `*`       | Indicates that all occurrences of original should be changed to replacement.                                                        |

The default is ALL. When you do not provide a specifier, all occurrences of original are changed to replacement.

#### Usage Notes

REDO with No Argument

When you type REDO without an argument, the most recent statement are re-executed.

Case-Sensitivity

When matching original with the text of the statement to be re-executed, REDO ignores case differences. For example, assume you specify `AT` as original, REDO matches it with `at`, `At`, `aT`, or `AT` in the statement.

When replacing original with replacement, REDO retains the case of all characters in replacement. For example, assume you specify `ShOw` as replacement, that is exactly how it appears in the re-executed statement.

#### Examples

Example 10-89 Redoing a Report

The following output is the result of `recap 2` statement.

       COMMAND LOG
    6: fetch w 20 down division total(actual)
    7: listnames

The following REDO statement re-executes the FETCH statement with a different variable.

    REDO 6 'actual' 'budget'

### 10.36 REEDIT

The REEDIT command edits a statement that you entered earlier in your session. The statement is retrieved from the command log, which is a list of up to 256 statements that you have entered most recently during the current session. REEDIT enables you to change the statement without executing it, so you can edit it sequentially.

The REDO command is similar to REEDIT, except that the statement is executed after you edit it.

**Note:**

REEDIT statements themselves are not included in the command log; however the statements re-executed by REEDIT are included.

#### Syntax

REEDIT \[number\|index\] 'original' 'replacement' \[specifier\] 

#### Parameters

number
A positive `INTEGER` that indicates the number of the statement to be edited. You can display the statements, with their numbers, using a RECAP statement.

index
A negative `INTEGER` or `0` (zero) that indicates the position of the statement to be edited relative to the end of the command log. The most recent statement is` 0`, the one before that is `-1`, and so on. The default is `0`.

original
A text literal that is part of the statement to be edited.

replacement
A text literal that should replace original when the statement is edited.

specifier
A specifier listed in the following table. Each specifier indicates where text replacement should occur in the edited statement.

Table 10-3 Valid Values for REEDIT specifier

| Specifier | Meaning                                                                                                                             |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------|
| `FIRST`   | Indicates that only the first occurrence of original should be changed to replacement.                                              |
| `LAST`    | Indicates that only the last occurrence of original should be changed to replacement.                                               |
| `n`       | A number indicating which occurrence of original should be changed to replacement. For example, `3` indicates the third occurrence. |
| `ALL`     | Indicates that all occurrences of original should be changed to replacement                                                         |
| `*`       | Indicates that all occurrences of original should be changed to replacement.                                                        |

The default is ALL. When you do not provide a specifier, all occurrences of original are changed to replacement.

#### Usage Notes

REEDIT with No number or index Argument

When you type REEDIT without number or index, the most recent statement is edited.

Case-Sensitivity

When matching original with the text of the statement to be edited, REEDIT ignores case differences. For example, assume you specify `AT` as original, REEDIT matches it with `at`, `At`, `aT`, or `AT` in the statement.

When replacing original with replacement, REEDIT retains the case of all characters in replacement. For example, assume you specify `ShOw` as replacement, that is exactly how it appears in the edited statement.

#### Examples

Example 10-90 Editing Multiple Values in a LIMIT Command

The following example illustrates why it could be helpful to use a REEDIT statement to edit a statement several times before executing it. With REEDIT commands, you can edit multiple values in a LIMIT command before executing it. When you enter a REDO statement, the LIMIT command is executed.

The following output is the result of a `recap 1` statement.

       COMMAND LOG
    6: limit mydim to 1 to 10, 15 to 20, 24 to 28, 33 to 40

The statement

    REEDIT 6 '1' '2' FIRST

produces the following output.

    7: limit mydim to 2 to 10 , 15 to 20, 24 to 28, 33 to 40

The statement

    REEDIT 7 '15' '18'

produces the following output.

    8: limit mydim to 2 to 10 , 18 to 20, 24 to 28, 33 to 40
     

The statement

    REDO 8 '40' '41'

makes one more change and re-executes the LIMIT command with the new values. It also produces the following output.

    9: limit mydim to 2 to 10 , 18 to 20, 24 to 28, 33 to 41

### 10.37 REGRESS

The REGRESS command calculates a simple multiple linear regression. The optional WEIGHTBY keyword lets you calculate a weighted regression when some data points are more reliable than others.

You can then execute REGRESS.REPORT to produce a standard report of the regression. You can also use the INFO function to obtain portions of the results for use in your own customized reports or for further analysis.

**Tip:**

To performing more complex regression analysis use a forecasting context as discussed in "[Forecasting Programs](olap-dml-programs.md)".

#### Syntax

REGRESS \[NOINTERCEPT\] dependent independent... \[WEIGHTBY weight\]

#### Parameters

NOINTERCEPT
Directs Oracle OLAP to suppress the constant term (intercept) in the regression equation. The default is to calculate a constant term.

dependent
An expression to be used as the dependent variable in the regression.

In calculating the results, REGRESS loops over all the dimensions of the dependent and independent variables.

independent
One or more expressions to be used as the independent variables (regressors) in the regression.

WEIGHTBY weight
Specifies a weighted regression. The numeric expression weight supplies the weights for each data point (observation). Giving higher weights to more reliable observations results in a higher quality regression. WEIGHTBY must come last in the REGRESS command.

When weight is less than zero for any observation, an error occurs. When weight is equal to zero for any observation, that observation is ignored in the calculation. When WEIGHTBY is omitted, an unweighted regression is calculated.

#### Usage Notes

Ignoring NA Values

In performing its calculations, the REGRESS command ignores any observation that has an `NA` value.

Producing a Standard Report

The standard report for a regression shows the coefficient, standard error, and T-ratio for each independent variable; and the R-square, F-Statistic, number of observations, and standard error of estimate for the regression. To produce this report, type the following.

    REGRESS.REPORT

Obtaining Results

For information on how to obtain portions of the results of REGRESS for your own reports or further analysis, use an INFO statement.

#### Examples

Example 10-91 Simple Regression

The following statements limit the `product` dimension to `Canoes`, then use regression to investigate the influence of advertising, price, and expense on the sales of canoes.

    LIMIT product TO 'Canoes'
    REGRESS NOINTERCEPT sales advertising price expense

You can now execute REGRESS.REPORT as illustrated in Example 10-93 to see the results of the regression.

Example 10-92 Weighted Regression

The following statements use a weighted regression, in which districts are weighted using a variable called `reliability` that has the following definition and values.

    DEFINE reliability VARIABLE DECIMAL <district>

    DISTRICT       RELIABILITY
    -------------- -----------
    Boston                1.00
    Atlanta               0.90
    Chicago               1.00
    Dallas                0.80
    Denver                0.90
    Seattle               0.60

The following statements perform the regression.

    REGRESS NOINTERCEPT sales advertising price expense -
    WEIGHTBY reliability

You can now execute REGRESS.REPORT as illustrated in Example 10-93 to see the results of the regression.

### 10.38 REGRESS.REPORT

`The REGRESS.REPORT` program produces a standard report of a regression performed using the REGRESS command.

#### Syntax

REGRESS.REPORT

#### Examples

Example 10-93 Report for a Simple Regression

Assume that you have performed the simple regression illustrated in Example 10-91 . You can now execute REGRESS.REPORT to see the results of the regression.

                                  Regression Analysis
                                  ===================
     
           Dependent Variable: SALES
            WEIGHTBY Variable: NONE
     
    Regressor                Coefficient      Std. Error     T-ratio
    --------------------    ------------    ------------    --------
    ADVERTISING                     0.36            0.16        2.24
    PRICE                          -8.66            1.80       -4.82
    EXPENSE                         1.05            0.01       79.69
     
          Corrected R-square                   1.00
          F-Statistic (2, 141)                   NA
          Number of observations                144
          Standard error of estimate       1,477.16

Example 10-94 Report for a Weighted Regression

Assume that you have performed the simple regression illustrated in Example 10-92 . You can now execute REGRESS.REPORT to see the results of the regression.

                                  Regression Analysis
                                  ===================
     
           Dependent Variable: SALES
            WEIGHTBY Variable: RELIABILITY
     
    Regressor                Coefficient      Std. Error     T-ratio
    --------------------    ------------    ------------    --------
    ADVERTISING                     0.44            0.17        2.64
    PRICE                          -8.03            1.92       -4.19
    EXPENSE                         1.04            0.01       76.45
     
          Corrected R-square                   1.00
          F-Statistic (2, 141)                   NA
          Number of observations                144
          Standard error of estimate       1,373.15

### 10.39 RELATION command

The RELATION command identifies a relation as the default relation for a specified dimension of the current object; or removes the default relation information from the current object. For more information on default relations, see "[Using Related Dimensions in Expressions](data-types-operators-and-expressions.md)".

**Note:**

Do not confuse the RELATION command with the RELATION statements in AGGMAP or ALLOCMAP.

#### Syntax

RELATION {dimension-name relation-name }\| DELETE { ALL \| dimension-name}

#### Parameters

dimension-name
The name of a previously-defined dimension. The dimension specified by the dimension-name argument must be a dimension of the currently considered object for which you want to specify or delete a default relation.

**Note:**

The dimension specified by the dimension-name argument must be a dimension of the currently considered object. The current object is the object that has been most recently defined or considered during the current session. To make an object definition the current definition, use a CONSIDER statement.

relation-name
The name of a previously-defined relation that Oracle OLAP uses as the default relation for the dimension specified by dimension-name.

DELETE
Specifies removal of previously-specified default relation information.

ALL
Removes all previously-defined default relation information.

#### Usage Notes

How Oracle OLAP Chooses Between Multiple Relations

When there are multiple relations between the two dimensions and you attempt to perform calculation on one of those dimension based on related dimensions, Oracle OLAP chooses the relation to use when executing the statement as follows:

1.  Uses the relation specified in the statement, if any.

2.  Uses the default relation for the dimension. Oracle OLAP determines the default relation as follows:

    1.  When you have specified a default relation using the RELATION command, Oracle OLAP recognizes that relation as the default relation.

    2.  When you have not specified a default relation using the RELATION command, Oracle OLAP recognizes the first relation that you defined as the default relation.

Identifying Default Relations

Use the OBJ function with the RELATION keyword to identify the default relation information for an object.

Multiple RELATION Commands Against the Same Object

Unlike other statements that operate against the most recently considered object (for example, an LD statement), a new RELATION command does not replace previously-issued RELATION commands. Instead, issuing multiple RELATION commands against the same object has a cumulative effect.

#### Examples

Example 10-95 Specifying a Default Relation Using the Relation Command

Assume that you defined the following analytic workspace objects (in the following order).

    DEFINE CITY DIMENSION TEXT
    DEFINE DISTRICT DIMENSION TEXT
    DEFINE CITY_DISTRICT RELATION DISTRICT <CITY>
    DEFINE CITY_REDISTRICT_1 RELATION DISTRICT <CITY>

    REPORT city_district
    CITY                    CITY_DISTRICT
    -------------------- --------------------
    Annapolis            Southern
    Bethesda             Southern
    Charlotte            Southern
    Gettysburg           Southern
    Greensboro           Southern
    Raleigh              Southern
    Reston               Southern
    Rochester            Southern
    Virginia Beach       Southern
    Washington           Capital


    REPORT city_redistrict_1
    CITY                  CITY_REDISTRICT_1
    -------------------- --------------------
    Annapolis            Capital
    Bethesda             Capital
    Charlotte            Southern
    Gettysburg           Southern
    Greensboro           Southern
    Raleigh              Southern
    Reston               Southern
    Rochester            Southern
    Virginia Beach       Capital
    Washington           Capital

As the following OBJ statements illustrate, the `city_district `relation is the default relation between `city` and `district` because the `city_district `relation was the first relation defined between `city` and `district`t and a default relation has not been specified using a RELATION statement.

    SHOW OBJ (RELATION ACTUAL 'city' 'district')
    CITY_DISTRICT

    SHOW OBJ (RELATION SPECIFIED 'city' 'district')
    NA


Assume that you now issue the following statements to limit district to `Washington` and make the `city_redistrict_1` relation the default relation.


    LIMIT city TO district
    CONSIDER city
    RELATION city city_redistrict_1


As the following OBJ statements illustrate, now the `city_redistrict_1 `relation that you specified with the RELATION statement is the default relation between `city` and `district`.

    SHOW OBJ (RELATION ACTUAL 'city' 'district')
    CITY_REDISTRICT_1
    SHOW OBJ (RELATION SPECIFIED 'city' 'district')
    CITY_REDISTRICT_1


Also, as the following statements illustrate, when you limit city to district, you get the same results as limiting city to the city_redistrict_1 relation

    LIMIT city TO district

    REPORT city
    CITY
    --------------------
    Annapolis
    Bethesda
    Virginia Beach
    Washington


    LIMIT city to ALL
    LIMIT city to city_redistrict_1

    REPORT city
    CITY
    --------------------
    Annapolis
    Bethesda
    Virginia Beach
    Washington

### 10.40 RELEASE

When an analytic workspace is attached in multiwriter mode, the RELEASE command changes the access mode of the specified variables, relations, valuesets, dimensions, or one or more partitions in a variable from read/write (acquired) access to read-only access.

**Tip:**

"[Managing Analytic Workspaces Attached in Multiwriter Mode](olap-dml-commands-a-g.md)"

#### Syntax

RELEASE  objects

#### Parameters

objects
One or more variables, relations, valuesets, dimension names, or analytic workspace names, separated by commas, that you want to release. To specify individual partitions of a partitioned variable, use the following syntax.

     variable_name (PARTITION partition_name \[, PARTITION partition_name \]...)

Precede each analytic workspace name with AW using the following syntax:

`AW` `analytic workspace name`

When you specify an analytic workspace in this list, all acquired objects in that analytic workspace are released after all pending changes are made to them. All changes made to the variables, relations, valuesets, or dimensions before a RELEASE statement executes are preserved as private changes after the release statement.

#### Usage Notes

Releasing Non-Updated or Uncommitted Objects

Similarly to using an AW DETACH statement for analytic workspaces that has been updated. Using RELEASE for objects that have been updated does not allow others to acquire the object until you commit or roll back the transaction. It may still be useful to release an object that has been updated before a commit when one wants to make further what-if changes and later needs to use UPDATE to update all acquired variables.

Releasing a Dimension Causes the Dimension to Revert

When you release an acquired dimension, the dimension is automatically reverted (see the REVERT command for an explanation of what it means to revert a dimension).

As the following code illustrates, releasing an acquired dimension causes an automatic revert.

User A issues the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC time WAIT
    MAINTAIN time ADD 'Y2002'
    actuals (time 'Y2002', ...) = 37
    REPORT time --> ..., 'Y2002'
    ... report
    SHOW actuals (time 'Y2002', ...) --> 37
    RELEASE time
    REPORT time --> ... (no 'Y2002')
    AW ATTACH myworkspace MULTI
    ... report
    ACQUIRE RESYNC actuals, time WAIT
    MAINTAIN time ADD 'Y2002'
    actuals (time 'Y2002', ...) = 37
    REPORT time --> ..., 'Y2002'
    SHOW actuals (time 'Y2002', ...) --> 37
    ... report
    REVERT time
    REPORT time --> ... (no 'Y2002')
    MAINTAIN time ADD 'Y2002'
    ... report
    REPORT time --> ..., 'Y2002'
    SHOW actuals (time 'Y2002', ...) --> NA
    ... report

#### Examples

Example 10-96 Two Users Modifying Different Objects in the Same Analytic Workspace

A classic use of multiwriter attachment mode is to allow two users to modify two different objects in the same analytic workspace. For example, assume that an analytic workspace has two variables: `actuals` and `budget`. Assume also that one user (user A) wants to modify `actuals`, while another user (user B) wants to modify `budget`. In this case, after attaching the analytic workspace in the multiwriter mode, each user acquires the desired variable, performs the desired modification, updates, commits the changes, and then, either detaches the workspace or releases the acquired variable.

User A executes the following statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE actuals
    ... make modifications
    UPDATE MULTI actuals
    COMMIT
    RELEASE actuals
    AW DETACH myworkspace

While, at the same time, User B executes the following statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE budget
    ... make modifications
    UPDATE MULTI budget
    COMMIT
    RELEASE budget
    AW DETACH myworkspace

Example 10-97 Using RELEASE After UPDATE But Before COMMIT

Using a RELEASE statement does not always allow other users to acquire the released variable. For example, when you have updated a variable but have not committed the changes, the execution of a RELEASE statement has no effect on other users until a commit occurs. However, when you use a simple UPDATE to update all acquired variables, it can be useful to release a variable after updating it but before committing it. When a variable is released after the first update, it is not be included in the list of updated variables for the second update. The following code illustrates situations where user B1 releases `budget` at different times.

Assume that User B1 issues the following statements

    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT
    make changes C1
    RELEASE budget
    UPDATE
    make changes C2
    UPDATE
    COMMIT

User B2 could issue the following statements

    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT

User B2 gets `budget` and sees no changes and issues the following statements.

    ...
    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT
    make changes C1
    UPDATE
    RELEASE budget
    make changes C2
    UPDATE
    COMMIT
    ...
    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT

Alternatively, User B2 gets `budget` and sees changes C1 and issues the following statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT
    make changes C1
    UPDATE
    make changes C2
    RELEASE budget
    UPDATE
    COMMIT
    ...
    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT

Or, as another alternative, User B2 gets `budget` and sees changes C1 and issues the following statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT
    make changes C1
    UPDATE
    make changes C2
    UPDATE
    COMMIT
    RELEASE budget
    ...
    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget WAIT

At this point, User B2 gets `budget` and sees changes C2

### 10.41 REMOVE_CUBE_MODEL

Removes a [MODEL (in an aggregation)](olap-dml-commands-a-g.md) statement for a specified model that is a sub-object of the cube dimension from the aggregation map of that cube dimension. The changes made when this program executes are not transactional; an automatic COMMIT is executed as part of the program.

**Note:**

You cannot use this program to modify a cube dimension if a materialized view exists for that cube dimension or any cube in which it participates.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL REMOVE_CUBE_MODEL(logical_cube, logical_dim, model_name, is_static_model)

#### Parameters

CALL
Because REMOVE_CUBE_MODEL is an OLAP DML program with arguments, you invoke it using the OLAP DML [CALL](olap-dml-commands-a-g.md) statement.

logical_cube
A text expression that is the name of the cube as defined in the Oracle data dictionary.

**See Also:**

"[Guidelines for Specifying Values for the Names of Logical OLAP Objects](olap-dml-commands-a-g.md)"

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

model_name
A text expression that is the name of the logical model that is associated with logical_dim.

is_static_model
A Boolean expression that specifies whether the MODEL statement to be removed is before or after the [RELATION (for aggregation)](olap-dml-commands-a-g.md) statements in the aggmap for logical_cube.

The default value is `TRUE` which means that MODEL statement to be removed is before the RELATION statements (that is, model_name is a static model).

Specify `FALSE` if the MODEL statement you want to remove is after the RELATION statements (that is, model_name is a dynamic model).

### 10.42 REMOVE_DIMENSION_MEMBER

The REMOVE_DIMENSION_MEMBER program removes an OLAP cube dimension member from one or more hierarchies, or entirely removes an OLAP cube dimension member from a cube dimension.

**Note:**

You cannot use this program to modify a cube dimension if a materialized view exists for that cube dimension or any cube in which it participates.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL REMOVE_DIMENSION_MEMBER(member_id, logical_dim, hier_list, \[ auto_compile \])

#### Parameters

CALL
Because REMOVE_DIMENSION_MEMBER is an OLAP DML program with arguments, you invoke it using the OLAP DML [CALL](olap-dml-commands-a-g.md) statement.

member_id
A text expression that is the member that you want to remove from the cube dimension hierarchies.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

**See Also:**

"[Guidelines for Specifying Values for the Names of Logical OLAP Objects](olap-dml-commands-a-g.md)"

hier_list
A multi-line text expression consisting of the Oracle data dictionary names of all of the hierarchies from which you want to remove the cube dimension member. Specify one hierarchy name per line.

To entirely remove a member from the dimension, specify `NA`.

auto_compile
A Boolean expression that specifies whether or not you want related analytic workspace objects (for example, changes to the parent relation) to be updated immediately.

The default value is `TRUE` in which case all of the changes to the analytic workspace that are needed to remove the cube dimension member happen now.

Specify FALSE only when, for performance reasons, you want to make a bulk set of changes before issuing a compile. In this case, you need to explicitly compile the cube dimension before the values of the analytic workspace objects take effect as described in "[Explicitly Compiling a Cube Dimension](olap-dml-commands-a-g.md)".

**Note:**

Regardless of the value that you specify for this argument, the new member is always immediately removed from the dimension -- even when an error is signaled during compilation.

#### Examples

Example 10-98 Removing OLAP Cube Dimension Members From a Hierarchy

1.  Execute the following SQL statement that reports on the values of the `my_time` cube dimension.

        select dim_key||'  '||level_name||'  '||parent
           from my_time_lvl_hier_view
           order by dim_key asc;

    The values this statement returns are shown below.

        DIM_KEY||''||LEVEL_NAME||''||PARENT
        -------------------------------------------------------------------------------
        L1_0  L1
        L1_1  L1
        L1_2  L1
        L2_1  L2  L1_1
        L2_2  L2  L1_1
        L2_3  L2  L1_2
        L3_1  L3  L2_1
        L3_2  L3  L2_1
        L3_3  L3  L2_2
        L3_4  L3  L2_2
        L3_5  L3  L2_2
        L3_6  L3  L2_3

        12 rows selected.


2.  Execute the following SQL statement that calls a user-written program named `remove_12_1` OLAP DML program.

        exec dbms_aw.execute('call my_util_aw!remove_l2_1');

    The contents of the user-written `remove_12_1` program are shown below.

    **Note:**

    The program uses:

    - The [OBJORG](olap-dml-functions-l-z.md) function to specify the OLAP DML objects that physically implement the `my_time` cube dimension.

    - The REMOVE_DIMENSION_MEMBER program provided with the OLAP DML to remove L2_1 and its descendants from the `my_time` cube dimension.

    <!-- -->

        DEFINE REMOVE_L2_1 PROGRAM
        PROGRAM

          VARIABLE _aw_dim       text
          VARIABLE _parentrel    text
          VARIABLE _members      text
          VARIABLE _member       text
          VARIABLE _i            integer

          " Removes L2_1 and descendants
          _aw_dim = OBJORG(DIM 'my_time')
          _parentrel = OBJORG(PARENTREL 'my_time')

          LIMIT &_aw_dim TO 'L2_1'
          LIMIT &_aw_dim ADD DESCENDANTS USING &_parentrel
          _members = VALUES(&_aw_dim)
          _i = 1
          WHILE _i LE NUMLINES(_members)
          DO
            _member = EXTLINES(_members, _i, 1)
            _i = _i + 1
            CALL REMOVE_DIMENSION_MEMBER(_member, 'my_time', NA, NO)
          DOEND

          UPDATE
          COMMIT
        END


3.  Execute the following SQL statement (the same statement as in Step 1) that shows the values of the `my_time` cube dimension after removal.

        select dim_key||'  '||level_name||'  '||parent
            from my_time_lvl_hier_view
            order by dim_key asc;

    The values after removal are shown below.

        DIM_KEY||''||LEVEL_NAME||''||PARENT
        --------------------------------------------------------------------------------
        L1_0  L1
        L1_1  L1
        L1_2  L1
        L2_2  L2  L1_1
        L2_3  L2  L1_2
        L3_3  L3  L2_2
        L3_4  L3  L2_2
        L3_5  L3  L2_2
        L3_6  L3  L2_3

        9 rows selected.

### 10.43 REMOVE_MODEL_DIMENSION

The REMOVE_MODEL_DIMENSION program removes aDIMENSION (in models) statement from a cube dimension's model. The changes made when this program executes are not transactional; an automatic COMMIT is executed as part of the program.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL REMOVE_MODEL_DIMENSION(logical_dim, model_name, explicit_dim)

#### Parameters

CALL
Because REMOVE_MODEL_DIMENSION is an OLAP DML program with arguments, you invoke it using the OLAP DML [CALL](olap-dml-commands-a-g.md) statement.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

**See Also:**

"[Guidelines for Specifying Values for the Names of Logical OLAP Objects](olap-dml-commands-a-g.md)"

model_name
A text expression that is the name of the logical model that is associated with logical_dim.

explicit_dim
A text expression that is the identifier of the dimension that you want to remove from the cube dimension's model.

### 10.44 RENAME

The RENAME command changes the name of an object in an analytical workspace.

#### Syntax

RENAME oldname newname \[AW workspace\]

#### Parameters

oldname
The name of an existing object in an analytic workspace. You can specify a qualified object name to indicate the attached workspace in which the object resides. As an alternative, you can use the AW keyword to specify the workspace. Do not use both.

When you do not use a qualified object name or the AW keyword to specify an analytic workspace, the object is renamed in the current workspace.

For an unnamed composite, use the same syntax that was used to create it. See "Naming an Unnamed Composite".

newname
The new name. The new name of an analytic workspace object cannot duplicate any other name in the workspace in which the object exists. Choose a name according to the rules for naming analytic workspace objects (see the main entry for the [DEFINE](olap-dml-commands-a-g.md) command. To change a named composite to an unnamed composite, use the SPARSE keyword as the newname argument. See "Unnaming a Named Composite".

AW workspace
The name of an attached workspace in which you want to rename the object. When you do not use a qualified object name or the AW keyword to specify an analytic workspace, the object is renamed in the current workspace.

#### Usage Notes

Updating Associated Objects

When you change the name of a variable, objects that use that variable, such as formulas, are not automatically updated.

When you change the name of a dimension, the definitions of any objects that are dimensioned by that dimension are automatically updated. Additionally, any valuesets for the renamed dimension are automatically updated for the new name.

RENAME and PERMIT

You may not rename an object when a PERMIT statement denies you the right to change its permission. Renaming an object does not affect permission associated with it.

Naming an Unnamed Composite

You can name an unnamed composite with a RENAME statement. The following example assigns the name `m.prod` to an unnamed composite that is dimensioned by `market` and `product`.

    RENAME SPARSE <market product> m.prod

Unnaming a Named Composite

You can change a named composite to an unnamed composite when the composite has no properties or permission restrictions and when there is at least one object dimensioned by it. In addition, there cannot be an unnamed composite with the same dimensions in the same order as the named composite, and the named composite cannot be used in the dimension list of any unnamed composite. To change a named composite to an unnamed composite, use the SPARSE keyword as the newname argument. The following example changes the named composite `m.prod` to an unnamed composite.

    RENAME m.prod SPARSE

Restrictions on Renaming Composites

You cannot rename a composite when it is a base dimension of an unnamed composite, or when one of its base dimensions is an unnamed composite.

#### Examples

Example 10-99 Renaming a Program

This statement changes the name of the program `testreport` to `sales.report`.

    RENAME testreport sales.report

### 10.45 REPORT

The REPORT command produces a formatted report for one or more data expressions. REPORT automatically loops over the dimensions of the expression. REPORT sends the output to the current outfile.

#### Syntax

REPORT \[NOHEAD\] \[GRANDTOTALS\] \[\[SUBTOTALS\] {GROUP group-dimension}...\] -       \[\[SUBTOTALS\] \[attributes\] DOWN down-dimension\] -      \[\[ROWTOTALS\] { ACROSS across-dimension \[limit-clause\]: }... \] -      \[SUBTOTALS\] \[attributes\] expression(s)

#### Parameters

When you specify only the expression argument, REPORT produces a report with the layout described in "Default Layout". When you specify some but not all of the dimensions of an expression in GROUP, DOWN, or ACROSS phrases, REPORT follows the default layout as closely as possible with the unspecified dimensions.

NOHEAD
Specifies that the report should contain no initial blank line and no headings. NOHEAD overrides any HEADING arguments you specify for the attributes argument and suppresses all headings that the REPORT command normally generates automatically.

GRANDTOTALS
Includes a grand total for each numeric column at the end of your report.

SUBTOTALS
Includes subtotals for numeric columns. A row of dashes precedes each row of subtotals. When you specify SUBTOTALS for an expression or DOWN phrase, you get subtotals for each GROUP dimension (or composite). When you specify SUBTOTALS for a GROUP phrase, you get subtotals for the specified dimension and for any slower-varying GROUP dimensions. The subtotals for a group appear at the bottom of the last slice in the group.

GROUP
Produces a separate group, or two-dimensional slice, of the data for each value of group-dimension. You can use the GROUP phrase more than once to specify multiple GROUP dimensions (or composites). In this case, you produce a separate slice for each combination of the values of the GROUP dimensions.

group-dimension
The name of a dimension or composite from which to retrieve the values to use as group labels, or one or more `TEXT` expressions that are the actual values you want to use as group labels:

- When group-dimension is the name of a composite or a conjoint dimension, Oracle OLAP creates a separate group for each base dimension.

- When group-dimension is a `TEXT` expression, the expression must be dimensioned only by the desired GROUP dimension, and each value of the expression should be descriptive text that corresponds to its associated dimension value.

The dimensions that you specify in a GROUP phrase are not required to be relevant to the data they loop over. See "Default Layout".

DOWN
Specifies that the report includes row labels (that is, one or more columns on the left side of your report that label the other values). You can have only one DOWN phrase.

down-dimension
The name of a dimension or composite from which to retrieve the values to use as row labels, or one or more `TEXT` expressions that are the actual values you want to use as row labels.

- When down-dimension is the name of a non-conjoint dimension, REPORT produces only one column of row labels.

- When down-dimension is the name of a composite or a conjoint dimension, Oracle OLAP creates a separate column for each base dimension.

- When down-dimension is a `TEXT` expression, the expression must be dimensioned only by the desired DOWN dimension, and each value of the expression must be descriptive text that corresponds to its associated dimension value.

The dimensions that you specify in a DOWN phrase are not required to be relevant to the data they loop over. See "Specifying Extra Dimensions".

ROWTOTALS
Includes a column headed "TOTAL" at the right side of the report with a total for each numeric row. Including a row total in your report does not imply either column subtotals or a grand total.

ACROSS
Produces a row of column headings across the top of your report, one for each value in dimension. Under each heading, REPORT produces a column of data for the data expression you specify. You can have multiple ACROSS phrases (or composites) in the report.

across-dimension
The name of a dimension or composite from which to retrieve the values to use as column headings, or one or more `TEXT` expressions that are the actual values you want to use as column headings.

- When across-dimension is the name of a composite or a conjoint dimension, Oracle OLAP creates a separate heading column for each base dimension.

- When across-dimension is a TEXT expression, the expression must be dimensioned only by the desired across-dimension, and each value of the expression should be descriptive text that corresponds to its associated dimension value. For information on providing formatted labels for a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, see "Formatting DAY, WEEK, MONTH, QUARTER, and YEAR Dimension Values".

The dimensions that you specify in an ACROSS phrase are not required to be relevant to the data they loop over. See "Specifying Extra Dimensions".

limit-clause
When you specify a dimension in the ACROSS phrase, the temporary status of that dimension during the execution of the execution of the REPORT statement. (You cannot include a limit-clause argument when you specify a composite in the ACROSS phrase.)

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see LIMIT (using values) command, LIMIT using LEVELREL command, LIMIT (using parent relation), LIMIT (using related dimension) command, LIMIT NOCONVERT command, and LIMIT command (using POSLIST).

When the limits you specify result in an empty status for the dimension, an error occurs (regardless of the setting of the OKNULLSTATUS option). However, when you include the phrase IFNONE label, the error is suppressed and execution of your program branches to the specified label, where you can handle the error.

attributes
One or more format attributes from Table 10-4 that specify how to format the data. For information on providing formatted labels for a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, see "Formatting DAY, WEEK, MONTH, QUARTER, and YEAR Dimension Values".

**Tip:**

When a variable has a formatting property attached to its definition, you can use the OBJ function to obtain the value of that property and use it as the value of an attribute in a REPORT statement.

When you do not specify any attributes, Oracle OLAP formats the data values using the default format described in "Default Layout". In this case, Oracle OLAP automatically determines the width of the columns, the number of decimal places, whether commas are used to mark thousands in numeric values, and so on.

Table 10-4 Formal Attributes for Data Values in a Report

| Attribute       | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HEADING 'text'  | Specifies text to use instead of default column headings. When you use the HEADING attribute, the position of the heading you specify varies depending on how many expressions it must span in your report. Consequently, your heading may or may not replace a default heading. Also, when you use the HEADING attribute to specify a column title that is wider than the column width, the text of the title wraps within the width of its column.                                                                       |
| WIDTH n         | (Abbreviated: W.) Makes the column n spaces wide. The maximum width is 4,000 characters. Columns with a width of 0 (zero) are suppressed.(See also "Default Values for the Width Attribute".)                                                                                                                                                                                                                                                                                                                              |
| TRUNCATE        | (Abbreviated: TRUNC.) Truncates a character value to the column width when it does not fit in the column.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| NOTRUNCATE      | (Abbreviated: NOTRUNC) Creates additional lines when the character value does not fit in the column. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                            |
| CENTER          | (Abbreviated: C.) Centers the value within its column.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| LEFT            | (Abbreviated: L.) Left-justifies the value within its column. (Default for text data.)                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| RIGHT           | (Abbreviated: R.) Right-justifies the value within its column. (Default for numeric and Boolean data.)                                                                                                                                                                                                                                                                                                                                                                                                                     |
| SPACE n         | (Abbreviated: SP.) Precedes the column with the specified number of spaces.<br>(By default, REPORT precedes the first column by 0 spaces, and other columns by 1 space.)                                                                                                                                                                                                                                                                                                                                                   |
| FILL 'char'     | Puts char into unused positions in the column. (The default fill character is a space.)                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| COMMA           | Marks thousands and millions with commas or the character currently recorded in the THOUSANDSCHAR option. Overrides the setting of the COMMAS option.                                                                                                                                                                                                                                                                                                                                                                      |
| NOCOMMA         | Does not marks thousands and millions. Overrides the setting of the COMMAS option.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| PAREN           | Uses parentheses to indicate negative numbers. Overrides the setting of the PARENS option                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| NOPAREN         | Uses the minus sign to indicate negative numbers. Overrides the setting of the PARENS option.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| DECIMAL n       | (Abbreviated: D.) Shows n decimal places. Decimal places are separated using the character currently recorded in the DECIMALCHAR option. Overrides the value of the DECIMALS option.<br>Note: REPORT suppresses decimal places in row and column totals of integer data unless you specify the DECIMAL attribute for the totaled expression. Additionally, when you set the DECIMAL attribute to `0` and you use the NOLEADINGZERO keyword, any decimal values between `-1` and `1` that are rounded to `0` are not shown. |
| MDECIMAL n      | Shows n decimal places in numbers formatted with M-notation; n can be any number from 0 to 16, or 255.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| NODECIMAL       | Shows the number of decimal places specified by the setting of the DECIMALS option. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                                             |
| EDECIMAL n      | Shows n decimal places in numbers formatted with E-notation; n can be any number from 0 to 16, or 255.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ENOTATION       | Always uses scientific notation, also called exponential notation or E-notation (appends "E", and includes a sign before the exponent, for example, `.230E+2` or `.230E-2`).                                                                                                                                                                                                                                                                                                                                               |
| NOENOTATION     | Does not use E-notation; instead, uses to conditional M-notation.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| CENOTATION      | Conditionally uses E-notation, when needed to make a value fit in a column.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| MNOTATION       | Always uses M-notation (divides values by one million and appends "M").                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| NOMNOTATION     | Does not use M-notation; instead, uses asterisks for oversize values.                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| CMNOTATION      | Conditionally uses M-notation, when needed to make a value fit in a column. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| FOLDDOWN        | For a multiline character value, places the first line on the row with the other values, and places additional lines below the rest of the row; also strips any leading or trailing spaces. (Default.)                                                                                                                                                                                                                                                                                                                     |
| FOLDUP          | For a multiline character value, places all but the last line above the rest of the row, and the last line on the row with the other values; also strips any leading or trailing spaces.                                                                                                                                                                                                                                                                                                                                   |
| INDENT n        | Indents the value n spaces within its column. The default is 0.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| LEADINGZERO     | Puts a leading zero before decimal numbers between -1 and 1.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| NOLEADINGZERO   | Suppresses leading zeros before decimal numbers between -1 and 1.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| CNLEADINGZERO   | Puts a leading zero before decimal numbers between -1 and 1 when it does not cut off any significant digits. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                    |
| LSET 'text'     | Adds text to the left of the value. When you use LSET with an expression that contains `NA` values, the text you specify with LSET is not included to left of any `NA` value                                                                                                                                                                                                                                                                                                                                               |
| NOLSET          | Does not add anything to the left of the value. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| RSET 'text'     | Adds text to the right of the value. When you use RSET with an expression that contains `NA` values, the text you specify with RSET is not included to right of any `NA` value.                                                                                                                                                                                                                                                                                                                                            |
| NORSET          | Does not add anything to the right of the value. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| NASPELL 'text'  | Uses text instead of `NA` values. Overrides the setting of the NASPELL option.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| NONASPELL       | Spells `NA` values as indicated by the NASPELL option. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| YESSPELL 'text' | Uses text for `TRUE` Boolean values. The default is recorded in the YESSPELL option.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| NOSPELL 'text'  | Uses text for `FALSE` Boolean values. Overrides the setting of the NOSPELL option.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ZSPELL 'text'   | Uses text instead of zero numeric values. Overrides the setting of the ZSPELL option.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| NOZSPELL        | Spells zero numeric values as specified by the ZSPELL option. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| OVER textexp    | Overlines the value with the value of a character expression (textexp). When textexp is a literal value, it must be enclosed in single quotes. Useful literal values include: `'-'` to overline value or column, `'='` to double overline value or column, and `''` to indicate that a value or column is does not have an overline.<br>To overline only when a condition is met, for textexp use:<br>`IF ``boolean-expression`` THEN '-' ELSE ''`                                                                         |
| UNDER textexp   | Underlines the value with the value of a character expression (textexp). When textexp is a literal value, it must be enclosed in single quotes. Useful literal values include: `'-'` to underline value or column, `'='` to double underline value or column, and `'' `to indicate that a value or column is not underlined.<br>To underline only when a condition is met, for textexp use: `IF ``boolean-expression`` THEN '-' ELSE ''`                                                                                   |
| VALONLY         | Used with the UNDER and OVER attributes, underline or overline the value only.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| NOVALONLY       | Used with the UNDER and OVER attributes, underlines or overlines the entire width of the column. (Default.)                                                                                                                                                                                                                                                                                                                                                                                                                |

expression . . .
The data to be shown in the report. The way the data looks depends on its data type and the attributes you specify.

**Note:**

The REPORT command is not equipped to deal with NTEXT values. Do not include them in any part of a report.

You can specify multiple expressions and these expressions do not have to have the same dimensions:

- When you have several data expressions in your REPORT statement, you can specify different format attributes before each. When you want attributes to apply to two or more data expressions, enclose the expressions in angle brackets (`<` `>`).

  attributes \<expression1, expression2\>

- Attributes outside the brackets apply to all the expressions within the brackets. However, you can also specify attributes for only one expression (even an attribute that contradicts one that applies to the group) within the brackets by including them immediately before the expression.

  attributes0 \<attributes1 expression1, expression2\>

  In this case, attributes0 applies to both expression1 and expression2; while attributes1 only applies to expression1.

**Tip:**

To create running totals, use the RUNTOTAL function.

#### Usage Notes

Report Options

Several options effect reports created using the OLAP DML. These options are listed in "[Report Options](olap-dml-options.md)".

Default Layout

When you do not specify any of the layout phrases (GROUP, DOWN, or ACROSS), REPORT tries to format its output compactly (typically, a two-dimensional report of the data with one dimension down the side and the others across the top, much like a spreadsheet). Any additional dimensions of the data form "slices" or separate two-dimensional segments, like a series of spreadsheets. By default, REPORT uses the following rules to determine the layout:

- The fastest-varying dimension in an expression (the one that appears first in the definition of that expression) goes across, the next fastest goes down, and any remaining dimensions become GROUP slices.

- The order of dimensions in a list of two or more expressions is a simple combination of the dimensions that appear in the definitions of the component expressions. The original order is preserved as far as possible, subject to the rule that repeated mentions of the same dimension are dropped. For example, the dimensions of the combined variables `price` and `industry.sales`, where `price` has the dimensions `<month product>` and `industry.sales` has the dimensions `<quarter product region`\>, are `<month product quarter region>`.

When you produce a report of data for a variable dimensioned by a composite, REPORT automatically breaks out the data by the base dimensions of the composite that is used in the definition of the variable. When a particular combination of base dimension values does not exist in the composite, the report shows `NA` for the corresponding data cell. See Example 10-104.

Default Values for the Width Attribute

When you omit the WIDTH attribute for an ACROSS phrase, the default width is the value of the COLWIDTH option (default is 10).

When you omit the WIDTH attribute for a DOWN phrase or when you specify a simple dimension in the DOWN phrase, the default width is the value of the LCOLWIDTH option (default is `14`).

When you omit the WIDTH attribute for a DOWN phrase that specifies a conjoint dimension or a composite, the default label width is the width of the COLWIDTH option and there is a separate column for each base dimension. You can provide a different width for each base dimension column by using the KEY function. You can produce a label column for each base dimension with the KEY function and use a separate WIDTH attribute for each column. For example, assume that `proddist` is a composite with the base dimensions `product` and `district`. In this case, you can use a statement similar to the following one.

    REPORT DOWN < W 8 KEY(proddist, product) -
       W 12 KEY(proddist, district) > . . .

When you use the default line width of 80 characters (determined by the LSIZE option) and the default column width settings (with a single label column of 14 characters) a line of output can accommodate the labels column and six data columns.

The combined width of all the columns of a report cannot be greater than 4,000 characters.

When a numeric value is too large to fit into a data column, REPORT rounds it off to the nearest million with the symbol M at the right side of the cell. When a value is still too large, REPORT replaces the value with a series of asterisks.

Formatting DAY, WEEK, MONTH, QUARTER, and YEAR Dimension Values

When you use a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR as the dimension in an ACROSS, DOWN, or GROUP phrase, you can use the CONVERT function to override the dimension's VNF (or the default VNF) and provide your own format for the dimension value names. To override the VNF, use the CONVERT function with a vnf argument instead of the dimension argument to the ACROSS, DOWN, or GROUP keyword. For example, in a report of `units` data, you can format the labels for the `month` dimension by using the following statement.

    REPORT HEADING 'Month' DOWN -
       CONVERT(month TEXT '<mtextl> <yyyy>') units

Specifying Extra Dimensions

The REPORT command uses whatever dimensions you specify in laying out the report, regardless of whether the expressions to be shown are dimensioned by these dimensions. When an expression is not dimensioned by one or more of the dimensions specified, the values of that expression are repeated for each value of the extra dimension. This fact is sometimes useful for comparisons. See Example 10-103.

#### Examples

Example 10-100 Creating a Default Report

This example shows how to look at product prices for the first three months of 1996. You can use REPORT in its simplest form, without changing the default layout

    LIMIT month TO 'Jan96' TO 'Mar96'
    REPORT price

These statements produce the following output.

                    --------------PRICE-------------
                    --------------MONTH-------------
    PRODUCT           Jan96       Feb96      Mar96
    --------------- ---------- ---------- ----------
    Tents               165.50     165.75     165.13
    Canoes              200.25     200.09     200.05
    Racquets             55.02      55.03      55.00
    Sportswear           50.03      50.02      50.00
    Footwear             38.01      38.01      38.01

Example 10-101 Including Column Totals

This example looks at unit sales for three districts for the first half of 1996, with `district` across the report and a subtotal for each column. (By default, months would be arranged across the report, because `month` is the fastest-varying dimension of `units`.) To make the report more compact, specify a smaller column width of `8 `characters.

    LIMIT month TO 'Jan96' TO 'Jun96'
    LIMIT district TO 'Boston' 'Chicago' 'Dallas'
    REPORT SUBTOTALS W 8 DOWN month -
       ACROSS district: W 8 units

These statements produce the following output.

    PRODUCT: TENTS
             ----------UNITS-----------
             ---------DISTRICT---------
    MONTH    Boston   Chicago  Dallas
    -------- -------- -------- --------
    Jan96         307      189      308
    Feb96         209      190      324
    Mar96         277      257      436
    Apr96         372      318      560
    May96         525      433      744
    Jun96         576      466      838
    -------- -------- -------- --------
    TOTAL       2,266    1,853    3,210
       ...

REPORT produces a similar slice for each product.

Example 10-102 Comparing Two Variables

This example compares actual sportswear sales with the projected sales plan, looking only at whole-dollar figures. It reports the actual and planned values side-by-side for May and June, 1996, and provides a grand total of sales and planned sales for all districts.

    LIMIT product TO 'Sportswear'
    LIMIT month TO 'May96' 'Jun96'
    LIMIT district TO ALL
    REPORT GRANDTOTALS W 12 DOWN district ACROSS month: -
       DECIMAL 0 <sales sales.plan>

These statements produce the following output.

    PRODUCT: SPORTSWEAR
                 -------------------MONTH-------------------
                 --------May96-------- --------Jun96--------
    DISTRICT       SALES    SALES.PLAN   SALES    SALES.PLAN
    ------------ ---------- ---------- ---------- ----------
    Boston           72,617     69,623     79,630     73,569
    Atlanta         161,537    148,823    177,967    157,939
    Chicago         101,873     94,545    112,793     97,427
    Dallas          170,939    165,449    175,066    164,192
    Denver           89,971     91,880     97,237     94,729
    Seattle          57,713     55,905     60,323     56,808
                 ---------- ---------- ---------- ----------
                    654,651    626,224    703,017    644,664
                 ========== ========== ========== ==========

Example 10-103 Repeating Price Data

This example compares sales across three districts, and it includes the unit price beside each sales figure for close comparison within each district. The REPORT statement specifies two expressions, `sales` and `price`. Because `sales` has three dimensions, `month`, `product`, and `district`, the report shows these three dimensions. However, `price` is not dimensioned by `district`. Therefore, the report repeats the values of `price` for each `district`. The report for January 1995 shown.

    LIMIT district TO FIRST 3
    LIMIT product TO ALL
    LIMIT month TO 'Jan95'
    REPORT GROUP month W 10 DOWN product ACROSS district: -
       <W 9 sales W 6 price>

These statements produce the following output.

    MONTH: Jan95
               -------------------DISTRICT------------------------
               -----Boston-----  ----Atlanta----- -----Chicago----
    PRODUCT      SALES    PRICE   SALES    PRICE   SALES    PRICE 
    ---------- --------- ------  --------- ------ --------- ------
    Tents      32,153.52 160.77  40,674.20 160.77 29,098.94 160.77
    Canoes     66,013.92 190.24  49,462.88 190.24 45,277.56 190.24
    Racquets   52,420.86  52.84  54,798.82  52.84 54,270.39  52.84
    Sportswear 53,194.70  48.54 114,446.26  48.54 72,123.47  48.54
    Footwear   91,406.82  36.10 100,540.28  36.10 90,287.70  36.10

Example 10-104 Reporting Data Dimensioned by Composites

In this example, `d.sales` is a variable whose dimension list includes the dimension `month` and the unnamed composite `SPARSE` `<product` `district>`. The unnamed composite contains no values for the base dimension combinations for the `Boston` and `Chicago `districts and the `Tents`, `Racquets`, And `Footwear` products. When you use the default form of the REPORT command to produce a report of `d.sales` data, REPORT breaks out the report by `month` and by the base dimensions of the unnamed composite (`product` and `district`). For the combinations of base dimension values that do not exist in the composite, the report shows `NA` for the corresponding data cells.

    LIMIT month TO 'Jan96' TO 'Mar96'
    LIMIT district TO 'Boston' 'Chicago'
    REPORT d.sales

These statements produce the following output.

    DISTRICT: Boston
                   ------------D.SALES-------------
                   -------------MONTH--------------
    PRODUCT          Jan96      Feb96      Mar96
    -------------- ---------- ---------- ----------
    Tents                  NA         NA         NA
    Canoes             70,489     82,238     97,622
    Racquets               NA         NA         NA
    Sportswear         57,079     63,122     67,006
    Footwear               NA         NA         NA
     
    DISTRICT: Chicago
                   ------------D.SALES-------------
                   -------------MONTH--------------
    PRODUCT          Jan96      Feb96      Mar96
    -------------- ---------- ---------- ----------
    Tents                  NA         NA         NA
    Canoes             48,662     54,425     68,816
    Racquets               NA         NA         NA
    Sportswear         77,490     85,879     85,308
    Footwear               NA         NA         NA

By specifying the composite in an ACROSS, DOWN, or GROUP phrase, you can override the default format of REPORT and break out the `d.sales` data by its composite. In this case, the report only includes the data cells for which the composite contains values.

    REPORT DOWN SPARSE <product district> d.sales

This statement produces the following report.

                          ------------D.SALES-------------
                          -------------MONTH--------------
     PRODUCT    DISTRICT    Jan96      Feb96      Mar96
    ---------- ---------- ---------- ---------- ----------
    Canoes     Boston         70,489     82,238     97,622
    Sportswear Boston         57,079     63,122     67,006
    Canoes     Chicago        48,662     54,425     68,816
    Sportswear Chicago        77,490     85,879     85,308

### 10.46 RESYNC

When an analytic workspace is attached in multiwriter mode, the RESYNC command drops private changes for the specified read-only objects and retrieves the data from the latest visible generations.

RESYNC resynthesized read-only objects. Use ACQUIRE to resynchronize acquired objects

**Tip:**

"[Managing Analytic Workspaces Attached in Multiwriter Mode](olap-dml-commands-a-g.md)"

#### Syntax

RESYNC objects

#### Parameters

objects
A list of one or more variables, relations, valuesets, or dimension names, separated by commas, that you want to resynchronize. Oracle OLAP ignores any acquired objects in this list.

Use `Name `as a value in objects to specify that you want to resynchronize the newest objects defined by other users.

#### Usage Notes

Keeping Logical Relationship of Objects

When using RESYNC keep in mind the logical relationship of different objects to avoid losing the logical consistency of the data by promoting some objects, but not others to a new generation.

Resynchronizing Objects that Share a Composite Dimension

Objects that share a composite dimension can be resynchronized separately when all such objects that are not being resynchronized are either unchanged or acquired.

#### Examples

Example 10-105 Resynchronizing Objects

In this example, user A is periodically updating `actuals`, while user R needs to periodically check the latest view of the data. They could execute the following OLAP DML statements.

User A could execute the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ACQUIRE actuals
    ...make modifications
    UPDATE MULTI actuals
    COMMIT
    ...make modification
    UPDATE MULTI actuals
    COMMIT

At the same time, user R could execute the following OLAP DML statements.

    AW ATTACH myworkspace MULTI
    ...
    RESYNC actuals
    ...
    RESYNC actuals
    ...
    RESYNC actuals
    ...

### 10.47 RETURN

Within an OLAP DML program, the RETURN command terminates execution of a program before its last line. You can optionally specify a value that the program returns when the program is called as a function. The value should have the same data type or dimension that you specified when you defined the program.

**See Also:**

"[Creating User-Defined Functions](olap-dml-programs.md)" and the [ARGUMENT](olap-dml-commands-a-g.md), [CALL](olap-dml-commands-a-g.md), [DEFINE PROGRAM](olap-dml-commands-a-g.md) commands

#### Syntax

RETURN \[expression\]

#### Parameters

expression
The expression to be returned to the calling program when the called program terminates.

#### Usage Notes

Return Value Dimensionality

The value returned by a program is a single value, without any dimensions. However, within the context of the statement that calls a user-defined function, the function expression has the dimensions of its arguments. In this case, the program is called once for every combination of the dimension values of the function expression.

Return Value Data Type

When you specify a data type when you define a program, the return value has that data type. When you specify a dimension when you define a program, the return value is a single value in that dimension. When the expression in a RETURN statement does not match the declared data type or dimension, Oracle OLAP converts it to the declared data type.

When you do not specify a data type or dimension in the definition of a program, its return value is treated as worksheet data and Oracle OLAP converts any return value to the data type that is required by the calling context which may lead to unexpected results.

Dimension Location

When the program returns values of a dimension, the dimension must be declared in the same analytic workspace as the program. The program is in the output of the LISTBY program, and OBJ(ISBY) is `TRUE` for the dimension.

No Return Value

When a program has been invoked as a function, but it does not provide a return value, the value that is returned to the calling program is `NA`.

#### Examples

Example 10-106 Terminating a Program Early

In this example, suppose you want a report program that produces a report only when a variable called `newfigures` is present in the current analytic workspace. In your program, you can use an IF statement to check whether `newfigures` exists and a RETURN to stop execution when it does not.

    DEFINE sales.report PROGRAM
    PROGRAM
    IF NOT EXISTS('newfigures')
       THEN DO
              SHOW 'The new data is not yet available.'
              RETURN
            DOEND
    PUSH month
    TRAP ON cleanup
    LIMIT month TO LAST 3
    REPORT ACROSS month: newfigures
     
    cleanup:
    POP month
    END

Now when you run the program without `newfigures` in the analytic workspace, the program produces a message and the RETURN statement terminates execution of the program at that point.

Example 10-107 Returning a Value

The following program derives next year's budget figures from the `actual` variable. It is a temporary calculation. You could call this program in a REPORT statement, thus calculating and reporting the budget figures without storing them in an analytic workspace.

    DEFINE budget.growth PROGRAM DECIMAL
    PROGRAM
    VARIABLE growth DECIMAL
    VARIABLE factor DECIMAL
    growth = TOTAL(actual(year 'Yr97') year) - TOTAL(actual(year -
       'Yr96') year)
    factor = ( 1 + growth ) / TOTAL(actual(year 'Yr96') year)
    RETURN TOTAL(actual(year 'Yr97') year) * (factor * factor/2)
    END

### 10.48 REVERT

The REVERT command drops all changes made to the specified objects since they were last updated, resynchronized (using a RESYNC statement), acquired using ACQUIRE with the RESYNC phrase, or since the analytic workspace was attached.

**Tip:**

"[Managing Analytic Workspaces Attached in Multiwriter Mode](olap-dml-commands-a-g.md)"

#### Syntax

REVERT objects

#### Parameters

objects
A list of the names, separated by commas, of acquired variables, valuesets, relations, or dimensions in an analytic workspace attached in multiwriter mode or a list of variables, valuesets, relations, or dimensions in an analytic workspace attached in read-only mode.

#### Usage Notes

Reverting a Dimension After Adding Dimension Values

Reverting a dimension after adding dimension values is not recommended because it can result in suboptimal space allocation for variables dimensioned by that dimension.

#### Examples

Example 10-108 Using REVERT to Undo Modifications

Assume that you have a variable named `budget` in an analytic workspace named `myworkspace`. Assume, also, that you must modify `budge`t in several steps but do not want to update the analytic workspace data until all steps are completed. For each step, you want to run several models to find the one that produces desired results. To perform this task, take the following steps:

1.  Attach the analytic workspace in multiwriter mode.

2.  Acquire `budget`.

3.  For each step:

    1.  Run the appropriate models, performing revert operations between them until you finds the desired model

    2.  Update `budget`.

4.  Commit and release `budget`.

The following code accomplishes these tasks.

    AW ATTACH myworkspace MULTI
    ACQUIRE RESYNC budget
    ...try model 1a --> not acceptable
    REVERT budget
    ...try model 1b --> ok. Done with Step 1
    UPDATE MULTI budget
    ...try model 2a --> not acceptable
    REVERT budget
    ...try model 2b --> not acceptable
    REVERT budget
    ...try model 2c --> ok. Done with Step 2
    UPDATE MULTI budget
    ...try model 3a --> ok. Done with Step 3. Done with all steps.
    UPDATE MULTI budget
    COMMIT
    RELEASE budget
    AW DETACH myworkspace

### 10.49 ROW command

The ROW command produces a single line of data in cells, one after another in a single row. A series of ROW commands that produce corresponding cells are often used to build up columns of data. For this reason, we normally speak of the ROW command as producing a line of columns. Output from the ROW command is sent to the current outfile.

The ROW command is typically used with other commands, functions, and options that you can think of collectively as report-writing statements

The ROW command itself consists of a series of column descriptions that specify the data to be produced and, optionally, the output format of the data.

In addition, ROW has a versatile capability for doing row and column arithmetic. It can perform calculations and include the calculation results in the output. It can use any kind of calculated expression in the column descriptions; and it can take advantage of row and column totaling functions (see Table 10-6).

ROW is primarily used in report programs to produce the lines of the report. The maximum width of any row in a report is 4,000 characters.

**Tip:**

When you know ahead of time that you do not need the subtotaling capability of the ROW command, using a HEADING statement instead of ROW to produce the lines of your report can provide a time savings, because, in this case, Oracle OLAP does not keep track of subtotals.

**See Also:**

[ROW function](olap-dml-functions-l-z.md)

#### Syntax

ROW \[attributes\] \[ACROSS dimension \[limit-clause\]:\] {exp1\|SKIP } -      \[\[attributes\] \[ACROSS dimension \[limit-clause\]:\] {expn\|SKIP }\]

#### Parameters

ROW with no arguments produces a blank line.

attributes
One or more attributes for a column. Attributes are format specifications that determine how the data value is formatted within the column. There is no limit to the number of attributes that you can use to describe a column format. (See the SKIP parameter for an explanation of each of the available attributes.) The default for some format attributes is determined by the current setting of Oracle OLAP options (see Table 10-7 for a list of these options).

ACROSS
An ACROSS phrase lets you include multiple values of a dimensioned expression in a single row by looping over one dimension (or composite) of the expression. Typically, ROW shows only the value that corresponds to the first dimension value within the current limits. With an ACROSS phrase, ROW produces one data column for each dimension value currently in the status.

You can apply a single ACROSS phrase to multiple data expressions, or you can use separate ACROSS phrases for different data expressions. See "Multiple Expressions"and "Separate ACROSS Phrases".

dimension
The name of a dimension or composite over which the statement loops.

When you show data for a variable dimensioned by a composite and you do not include an ACROSS phrase, ROW shows output for all data cells that correspond to the base dimension values of the composite. When a particular combination of base dimension values does not exist in the composite, ROW shows `NA` for the corresponding data cell. Likewise, when you specify one composite's base dimension in an ACROSS phrase, ROW shows `NA` for a data cell for which the composite contains no value. However, when you specify a composite in the ACROSS phrase, ROW shows output only for data cells for which combinations of base dimension values exist in the composite which provides a more concise report that better reflects your data.

When the dimension specified in an ACROSS phrase has null status, ROW does not produce any data columns for that ACROSS phrase.

limit-clause
When you specify a dimension in the ACROSS phrase, a clause that enables you to temporarily change the status of that dimension during the execution of the ROW statement.

The syntax of limit-clause is the same syntax as any of the limit-clause arguments in the various forms of the LIMIT command (that is, the syntax of the LIMIT command after the limit-type argument such as "TO"). For the syntax of these arguments, see LIMIT (using values) command, LIMIT using LEVELREL command, LIMIT (using parent relation), LIMIT (using related dimension) command, LIMIT NOCONVERT command, and LIMIT command (using POSLIST).

The following example temporarily limits month to the last six values, no matter what the current status of month is.

          ACROSS month LAST 6: units

When the limits you specify result in empty status for the dimension, an error occurs. However, when you include the phrase IFNONE label, the error is suppressed and execution of your program branches to the specified label where you can handle the error.

**Note:**

When you specify a composite in the ACROSS phrase, you cannot include a limit-clause argument. You must limit the base dimensions of a composite to the desired values using a LIMIT command before you execute a ROW statement

SKIP
Used instead of an expression to indicate that the column is to be left blank.

Table 10-5 Column Attributes for ROW

| Attribute               | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| WIDTH n<br>(W n)        | Makes the column n spaces wide. The default width for the first column is the value of the LCOLWIDTH option. For other columns, it is the value of the COLWIDTH option. The maximum width is 4,000 characters. Columns with a width of `0` are suppressed.                                                                                                                                                                                                 |
| SPACE n<br>(SP n)       | Precedes the column with n spaces. The default for the first column is `0`; for other columns, `1`.                                                                                                                                                                                                                                                                                                                                                        |
| INDENT n                | Indents the value n spaces within its column. The default is 0.                                                                                                                                                                                                                                                                                                                                                                                            |
| LEFT<br>(L)             | Left-justifies the value within its column. (The default for TEXT data.)                                                                                                                                                                                                                                                                                                                                                                                   |
| RIGHT<br>(R)            | Right-justifies the value within its column. (The default for numeric and Boolean data.)                                                                                                                                                                                                                                                                                                                                                                   |
| CENTER<br>(C)           | Centers the value within its column.                                                                                                                                                                                                                                                                                                                                                                                                                       |
| LSET 'text'             | Adds text to the left of the value. When used with an expression that contains `NA` values, Oracle OLAP does not include the text you specify at the left of any `NA` values.                                                                                                                                                                                                                                                                              |
| NOLSET                  | Does not add anything to the left of the value.                                                                                                                                                                                                                                                                                                                                                                                                            |
| RSET 'text'             | Adds text to the right of the value. When used with an expression that contains `NA` values, Oracle OLAP does not include the text you specify at the right of any `NA` values                                                                                                                                                                                                                                                                             |
| NORSET                  | Does not add anything to the right of the value.                                                                                                                                                                                                                                                                                                                                                                                                           |
| FILL 'char'             | Puts char into unused positions in the column. The default fill character is a space.                                                                                                                                                                                                                                                                                                                                                                      |
| DECIMAL n<br>(D n)      | Shows n decimal places. Decimal places are separated by the character currently specified by the DECIMALCHAR option. The default number of decimal places is controlled by the DECIMALS option.                                                                                                                                                                                                                                                            |
| NODECIMAL               | Shows the number of decimal places indicated by the DECIMALS option.                                                                                                                                                                                                                                                                                                                                                                                       |
| COMMA                   | Marks thousands and millions with commas or the character currently recorded in the THOUSANDSCHAR option. The default is controlled by the COMMAS option.                                                                                                                                                                                                                                                                                                  |
| NOCOMMA                 | Does not mark thousands and millions.                                                                                                                                                                                                                                                                                                                                                                                                                      |
| PAREN                   | Uses parentheses to indicate negative numbers. The default is controlled by the PARENS option.                                                                                                                                                                                                                                                                                                                                                             |
| NOPAREN                 | Uses the minus sign to indicate negative numbers. The default is controlled by the PARENS option.                                                                                                                                                                                                                                                                                                                                                          |
| LEADINGZERO             | Puts a leading zero before decimal numbers between `-1` and `1`.                                                                                                                                                                                                                                                                                                                                                                                           |
| NOLEADINGZERO           | Suppresses leading zeros before decimal numbers between `-1` and `1`. (Note that when you set the DECIMAL attribute to `0` and you use the NOLEADINGZERO keyword, Oracle OLAP does not show any decimal values between `-1` and `1` that are rounded to 0.)                                                                                                                                                                                                |
| CNLEADINGZERO           | Puts a leading zero before decimal numbers between `-1` and 1 when it does not cut off any significant digits.                                                                                                                                                                                                                                                                                                                                             |
| MNOTATION               | Always uses M-notation (divides values by one million and appends `M`).                                                                                                                                                                                                                                                                                                                                                                                    |
| CMNOTATION              | Conditionally uses M-notation, when needed to make a value fit in a column.                                                                                                                                                                                                                                                                                                                                                                                |
| NOMNOTATION             | Does not use M-notation (uses asterisks for oversize values).                                                                                                                                                                                                                                                                                                                                                                                              |
| MDECIMAL n              | Shows n decimal places in numbers formatted with M-notation; n can be any number from 0 to 16, or 255.                                                                                                                                                                                                                                                                                                                                                     |
| ENOTATION               | Always uses scientific notation, also called exponential notation or E-notation (appends `E`, and includes a sign before the exponent, for example, `.230E+2` or `.230E-2`).                                                                                                                                                                                                                                                                               |
| CENOTATION              | Conditionally uses E-notation, when needed to make a value fit in a column.                                                                                                                                                                                                                                                                                                                                                                                |
| NOENOTATION             | Does not use E-notation (defaults to conditional M-notation).                                                                                                                                                                                                                                                                                                                                                                                              |
| EDECIMAL n              | Shows n decimal places in numbers formatted with E-notation; n can be any number from 0 to 16, or 255.                                                                                                                                                                                                                                                                                                                                                     |
| NASPELL 'text'          | Uses text instead of `NA` values. The default is controlled by the NASPELL option.                                                                                                                                                                                                                                                                                                                                                                         |
| NONASPELL               | Spells `NA` values as indicated by the NASPELL option.                                                                                                                                                                                                                                                                                                                                                                                                     |
| ZSPELL 'text'           | Uses text instead of zero numeric values. The default is controlled by the ZSPELL option.                                                                                                                                                                                                                                                                                                                                                                  |
| NOZSPELL                | Spells zero values as indicated by the ZSPELL option.                                                                                                                                                                                                                                                                                                                                                                                                      |
| YESSPELL 'text'         | Text used for `TRUE` Boolean values. The default is recorded in the YESSPELL option.                                                                                                                                                                                                                                                                                                                                                                       |
| NOSPELL 'text'          | Text used for `FALSE` Boolean values. The default is recorded in the NOSPELL option.                                                                                                                                                                                                                                                                                                                                                                       |
| TRUNCATE<br>(TRUNC)     | Truncates a character value to the column width when it does not fit in the column.                                                                                                                                                                                                                                                                                                                                                                        |
| NOTRUNCATE<br>(NOTRUNC) | Creates additional lines when the character value does not fit in the column.                                                                                                                                                                                                                                                                                                                                                                              |
| FOLDUP                  | For a multiline character value, places all but the last line above the rest of the row, and the last line on the row with the other values; also strips any leading or trailing spaces.                                                                                                                                                                                                                                                                   |
| FOLDDOWN                | For a multiline character value, places the first line on the row with the other values, and places additional lines below the rest of the row; also strips any leading or trailing spaces.                                                                                                                                                                                                                                                                |
| VALONLY                 | Underlines or overlines the value only. (Used with UNDER and OVER.)                                                                                                                                                                                                                                                                                                                                                                                        |
| NOVALONLY               | Underlines or overlines the entire width of the column. (Used with UNDER and OVER.)                                                                                                                                                                                                                                                                                                                                                                        |
| UNDER textexp           | Underlines the value or column with the value of a character expression (textexp). When textexp is a literal value, it must be enclosed in single quotes. Useful literal values include: `'-'` to underline value or column, `'='` to double underline value or column, and `'' `to indicate that a value or column is not underlined.<br>To underline only when a condition is met, for textexp use<br>`IF ``boolean-expression` `THEN '-' ELSE ''`       |
| OVER textexp            | Overlines the value or column with the value of a character expression (textexp). When textexp is a literal value, it must be enclosed in single quotes. Useful literal values include: `'-'` to overline value or column, `'='` to double overline value or column, and `''` to indicate that a value or column is does not have an overline<br>To overline only when a condition is met, for textexp use<br>`IF` `boolean-expression` `THEN '-' ELSE ''` |

Use the functions that are listed in the following table to perform calculations on the values generated so far in a report.

Table 10-6 Row and Column Arithmetic

| Function                                | Data Type | Value Returned                                                                                                                                                                                                    |
|:----------------------------------------|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COLVAL(n)                               | DECIMAL   | Value in the nth column of the current row. When n \> `0`, an absolute column number (from the left margin, moving to the right). When n \< `0`, a relative column number (from the current column, moving left). |
| RUNTOTAL(n)<br>where:<br>n = 1,2, ...32 | DECIMAL   | Total of all numbers generated in the current column since the last SUBTOTAL or ZEROTOTAL for n. Does not reset total for n to `0`.                                                                               |
| SUBTOTAL(n)<br>where:<br>n = 1,2, ...32 | DECIMAL   | Total of all numbers generated in the current column since the last SUBTOTAL or ZEROTOTAL for n. Resets total for n to `0`.                                                                                       |

The options that are listed in the following table affect the default format for a ROW command.

Table 10-7 Report-Related Options

| Option        | Meaning                                                                                                                                                                       |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COLWIDTH      | Column width for all but the first column when the WIDTH attribute is not used. The default is `10`.                                                                          |
| COMMAS        | Specifies whether a thousands group separator is used when neither the COMMA attribute nor the NOCOMMA attribute is used. The default is `YES` (uses a separator).            |
| DECIMALS      | Number of decimal places when the DECIMAL attribute is not used. The default is `2`.                                                                                          |
| LCOLWIDTH     | Column width for the first column when the WIDTH attribute is not used. The default is `14`.                                                                                  |
| LSIZE         | Defines the line size within which the STDHDR program centers the standard header. The default is `80` characters.                                                            |
| NASPELL       | Text used for `NA` values when the NASPELL attribute is not used. The default text is `NA`.                                                                                   |
| NLS_LANGUAGE  | Specifies the text used for `TRUE` and `FALSE` Boolean values. These values are reflected in the YESSPELL and NOSPELL options.                                                |
| NLS_TERRITORY | Specifies the character used for the decimal marker and the thousands group separator. These values are reflected in the DECIMALCHAR and THOUSANDSCHAR options.               |
| PARENS        | Parentheses usage for negative numbers when neither the PAREN attribute nor the NOPAREN attribute is used. The default is `NO` (does not use parentheses; uses a minus sign). |
| ZEROROW       | Controls generation or suppression of rows in which all numeric values are zero. The default is `NO` (generates zero rows).                                                   |
| ZSPELL        | Text used for zero values when the ZSPELL attribute is not used. The default text is `OFF`, which shows a zero (`0`).                                                         |

Use the statements that are listed in the following table with the ROW command.

Table 10-8 OLAP DML Statements That Are Compatible with the ROW Command

| Command                           | Action                                                                                                                   |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------|
| BLANK n                           | Produces n blank lines. The default is one line.                                                                         |
| HEADING column-<br>description(s) | Produces titles and column headings for a report. Numeric values in headings are not added to column totals.             |
| PAGE                              | Forces a page break in output when PAGING is set to `YES`.                                                               |
| ZEROTOTAL                         | Resets all 32 totals to `0` for all columns.                                                                             |
| ZEROTOTAL ALL col(s)              | Resets all 32 totals to `0` for the specified columns, or for all columns when there are no column arguments.            |
| ZEROTOTAL n col(s)                | Resets the indicated total (n) to `0` for the specified columns, or for all columns when there are no column arguments.  |

#### Usage Notes

Report-Writing Commands

The ROW command and its associated options and commands are referred to collectively as report-writing statements. Table 10-6 lists functions you can use for performing row and column arithmetic in reports. Table 10-7 lists report-related options that determine the default format for ROW output. Table 10-8 lists additional statements that are used in combination with ROW to create reports.You can use the PAGING option and associated paging-related options to produce your report program in a page-oriented format.

Labels for Composites and Conjoint Dimensions

When you produce a report of data that has a composite or a conjoint dimension in its dimension list, you can produce a label column for each base dimension by using the KEY function. You can also provide a separate WIDTH attribute for each label column. For example, when `proddist` is a composite with the base dimensions `product` and `district`, you can use statements similar to the following ones.

    FOR proddist
       ROW W 12 KEY(proddist district) W 8 KEY(proddist product) ...

Multiple Expressions

When you want the same format attribute or ACROSS phrase to apply to multiple data expressions, you can enclose the expressions in angle brackets (`<` `>`) and place the common attributes or ACROSS phrase immediately before the bracketed expressions.

attributes \<expression1, expression2, ...\> 

or

ACROSS dimension: \<expression1, expression2, ...\>

When you have attributes that apply to only one expression within the brackets, place the specific attributes immediately before the expression.

attributes1 \<expression1, attributes2 expression2\>

When an attribute inside angle brackets (specific to a column) conflicts with an attribute outside the brackets (common to several columns), the specific attribute overrides the common attribute.

You can nest brackets to any depth, if you have an equal number of right and left brackets.

Separate ACROSS Phrases

For data generated with an ACROSS phrase, you can produce all the columns for one expression and then all the columns for additional expressions by using separate ACROSS phrases.

ACROSS dim: expression1, ACROSS dim: expression2

You also can nest ACROSS phrases to show data columns for two or more dimensions of an expression across a row.

ACROSS dim1: ACROSS dim2: expression

Row and Column Arithmetic

See Table 10-6 for a list of the functions available for row and column arithmetic. You can use these functions to perform calculations on the values already generated in a report. Oracle OLAP maintains 32 running totals for each column, so you can include up to 32 levels of subtotals in a report. Note that when a numeric value is too large to fit into a data cell, ROW rounds it off to the nearest million with the symbol M at the right side of the cell. When a value is still too large, ROW replaces the value with asterisks.

#### Examples

Example 10-109 Labeling Data Values

In this example, ROW produces a line of output that contains a value of `sales`, along with the corresponding dimension values for `district`, `month`, and `product` that identify it.

    ROW W 8 district month product sales

The preceding statement produces the following row of output.

    Boston        Jan95      Tents  32,153.52

Example 10-110 Reporting Two Variables

The line of output produced by this ROW statement contains the current dimension value of `district`, followed by the values of `sales` and `sales.plan` for Sportswear for each of the first two months of 1996. 

    LIMIT month TO 'Jan96' 'Feb96'
    LIMIT product TO 'Sportswear'
    ROW W 8 district ACROSS month: <sales sales.plan>

These statements produce the following row of output.

    Boston    57,079.10  61,434.20  63,121.50  64,006.91

Example 10-111 Formatting and Labeling the Output

In this ROW statement, you want to see the actual and planned sales of tents for June 1996. You want to limit the status of `month` only for this one ROW statement, so you include the value `Jun96` in the ACROSS phrase. You format the values as whole dollar amounts, and you also add a dollar sign to the values, along with individual labels that identify the actual and planned figures.

    LIMIT product TO 'Tents'
    ROW WIDTH 15 name.product ACROSS month 'Jun96': -
       DECIMAL 0 LSET '$' W 18 -
       <RSET ' (actual)' sales -
       RSET ' (plan)' sales.plan>

These statements produce the following row of output.

    3-Person Tents    $95,121 (actual)     $80,138 (plan)

Example 10-112 Reporting on a Variable Dimensioned by a Composite

In this example, D.SALES is a variable whose dimension list includes the dimension `month` and the unnamed composite `SPARSE` `<product` `district>`. By specifying the composite in an ACROSS phrase of a ROW statement, you can produce a report that includes only the data cells for which the composite contains values.

    LIMIT product TO ALL
    LIMIT district TO 'Atlanta'
    LIMIT month TO 'Jan96'
    ROW ACROSS SPARSE <product district>: d.sales

### 10.50 SET

The SET command, also called an assignment statement or the = command, assigns one or more values to a variable, option, relation, or dimension surrogate. When an object has one or more dimensions, the SET command loops over the values in status for each dimension of the target object and assigns a data value to the corresponding cell of the target object.

When the target is an object defined with a composite in its dimension list, Oracle OLAP automatically creates any missing target cells that are being assigned non-`NA` values. This step also adds to the composite all the dimension value combinations that correspond to those new cells. Thus, both the target object and the composite might be larger after an assignment. When you want to assign values only to cells that already exist in the target, use the ACROSS keyword.

**Note:**

You can use UNRAVEL with SET to assign values of an expression into the cells of a variable when the dimensions of the expression are different from the dimensions of the variable

#### Syntax

\[SET\] target-name \[=\] expression \[ACROSS composite\]

#### Parameters

SET
SET is optional. It is an older command form of this functionality, and is included for compatibility.

target-name
The name of the target object where the data is assigned and stored. For a list of analytic workspace objects that can be a target object, see Table 10-9.

=
The = (assignment or equal) operator assigns one or more values to a variable, option, or relation. See also "[Assignment Operator](data-types-operators-and-expressions.md)".

expression
The source of the data values to be assigned to the object, see Table 10-9

ACROSS composite
When you are assigning data to a variable dimensioned by a composite the default behavior is to loop over all the values in status for each of the base dimensions of the object. Oracle OLAP automatically creates any missing target cells that are being assigned non-`NA` values, and it automatically adds the required dimension value combinations to the composite.

When you want to assign values only to existing cells of a variable defined with a composite, use the ACROSS keyword, which causes = to change the way it loops for those dimensions of the target that are part of the composite. Instead of looping over all possible combinations of the values in the status of those dimensions, = loops only over those combinations of the values in the status that already exist in the composite.

The ACROSS keyword is intended for specifying a composite. However, when you specify a base dimension of the composite instead, be aware that the assignment statement could add many values to your composite.

#### Usage Notes

Triggering Program Execution When an Assignment Statement Executes

Using the TRIGGER command, you can make a SET statement an event that automatically executes an OLAP DML program. See "[Trigger Programs](olap-dml-programs.md)" for more information

Dimensionality and Performance

When the target has multiple dimensions, the = statement loops over the dimension values in the order in which they were added, regardless of their logical order as reflected by the default status. In a multidimensional case, the looping is over the compound dimension. The first dimension listed in the definition varies the fastest. When you are setting the target to the values of an expression, Oracle OLAP performs much more efficiently when the source expression has the same dimensions, in the same order, as the target.

Differently Dimensioned Variables in an Expression

When an assignment statement involves several differently-dimensioned objects, the calculation can appear complicated. The following list outlines the process followed by a complicated assignment statement. When the statement is A = B, where A is the object being set to the expression B, Oracle OLAP first determines the dimensions of A. Then it determines the status of those dimensions. For each combination of dimension values in the status of those dimensions:

1.  Oracle OLAP determines which single value of A (sometimes called a cell) is going to be set.

2.  For each component of the expression B (each variable, formula, function, qualified data reference, or literal), Oracle OLAP determines the single value that corresponds to the cell of A that is being set. When a component of the expression is not dimensioned or is a literal, Oracle OLAP simply uses its value. When a component of the expression has dimensions different from A, Oracle OLAP uses the first value in the status of these dimensions.

3.  Oracle OLAP performs the specified calculation on the single values obtained in Step 2 and stores the result in the cell of A chosen in Step 1.

Using Objects in Assignment Statements

The following table outlines the objects that you can use in assignment statements and indicates whether you can use them as a target or source expression:

Table 10-9 Using Objects in Assignment Statements

| Object                                            | Target         | Source |
|:--------------------------------------------------|:---------------|:-------|
| Composite                                         | No             | Yes    |
| Dimension                                         | Only in models | Yes    |
| Formula                                           | Yes            | Yes    |
| Function (including OLAP DML program as function) | No             | Yes    |
| Relation                                          | Yes            | Yes    |
| Surrogate                                         | Yes            | Yes    |
| Valueset                                          | No             | Yes    |
| Variable                                          | Yes            | Yes    |
| Worksheet                                         | Yes            | Yes    |

**See Also:**

"Assigning Values to Variables", "Assigning Values to Relations", "Rules for Equations in Models", "Expressions Dimensioned Conjoint Dimensions", and "Assigning Values to Dimension Surrogates"

Assigning Values to Variables

When you use an = (SET) statement to assign the value of a single-cell expression to a single cell, a single value is stored. However, when you use an = statement to assign the value of a single-cell expression to a target variable that has one or more dimensions, then the assignment loops over the values in status for each dimension of the target variable and assigns a data value to the corresponding cells of the variable.

When you assign a multiline value to a fixed-width text variable, then the variable is set to the first line only. To assign a multiline value to a fixed-width text variable, you use the JOINCHARS function to make the multiline value one line long. For example, suppose you have a non-fixed-width text variable called `textvar`. The statement

    SHOW textvar

produces the following output, in which each line of the value in `textvar` is shown as a separate line.

    This is a variable
    that has a multiline
    text value.

To assign this value to a variable called `fixedtext` with a fixed width of 60 bytes and show the value, you would use the following statements.

    fixedtext = JOINCHARS(textvar)
    SHOW fixedtext

These statements produce the following output, in which the value of `textvar` is shown as a single line.

    This is a variable that has a multiline text value.

When the actual number of bytes in the `textvar` variable's value exceeds the width of the `fixedtext` variable, then the value of `textvar` is truncated when it is stored in `fixedtext`.

Assigning Values to Relations

You can assign values to a relation using a SET statement as illustrated in Example 10-114. When executing the assignment statement, a loop is performed over the values in status for each dimension of the target relation and assigns a data value to the corresponding cell of the target relation.

You can assign values to a relation with a text dimension by assigning one of the following:

- A text value of the dimension.

- An INTEGER that represents the position of the dimension value in the default status list of the dimension.

Assigning Values to Dimensions

The only time you use an = statement to assign a value to a dimension is when the result of a calculation in a model equation is numeric. In this situation, you can use the = operator to assign the results to a dimension value. However, equations (that is, expressions) in models differ in several ways from expressions used in other contexts. See "Rules for Equations in Models" for information on using the assignment statement within models. See the MAINTAIN command for information on how to add values to dimensions in all other cases.

Assigning Values to Dimension Surrogates

You assign values to a dimension surrogate with an = (SET) statement. For example, the following statements define the dimension surrogate `storename`, which is a `TEXT` type surrogate for the `NUMBER` type dimension `store_id`, assign a value to the fourth position of `storename`, and then report the value of the surrogate for the fourth value of `store_id`, which is `100`.

    DEFINE storename SURROGATE store_id TEXT
    storename(storename 4) = 'Molly\'s Emporium'
    REPORT W 25 storename(store_id 100)
     
    STORENAME(STORE_ID 100)
    -------------------------
    Molly's Emporium

For example, when you define the INTEGER dimension surrogate `intsurr` for a `NUMBER` dimension `numdim` that has five values, then a report of `intsurr` produces the following.

    INTSURR
    -------
          1
          2
          3
          4
          5

Like a dimension, the values of a dimension surrogate must be unique. However, unlike a dimension, a dimension surrogate can have `NA` values, unless it is an INTEGER type. The same value can be a value of the dimension and of any of its surrogates.

Using QDRs with the Target of an Assignment Statement

You can use a QDR with the target of an = (SET) statement which lets you assign a value to specific cells in a variable or relation.

The following example assigns the value 10200 to the data cell of the `sales` variable that is specified in the qualified data reference. When the variable named `sales` does not already have a value in the cell associated with `Boston`, `Tents`, and `Jan99`, then the value is assigned to the cell and thus it is added to the variable. When a value already exists in the cell, the value 10200 overwrites the previous value.

    sales(market 'Boston' product 'Tents' month 'Jan99')= 1020

Expressions Dimensioned Conjoint Dimensions

When an expression is dimensioned by a conjoint dimension, Oracle OLAP uses the dimension's relationship to its base dimension values to assign data to the correct cells. You can set the values of a variable dimensioned by a conjoint dimension to an expression dimensioned by one of its base dimensions. The converse is also true. See "Example 10-117".

Rules for Equations in Models

The equations in a model use an OLAP DML assignment statement to assign values to variables or dimension values. Equations in models differ in several ways from equations used in other contexts in Oracle OLAP:

- In a model equation, you can use the name of a dimension value anywhere you would normally use the name of a variable. You can base calculations on a dimension value, and you can assign the results of a calculation to a dimension value. When an equation refers directly to one or more dimension values, it is called a dimension-based equation.

- You cannot use ampersand substitution in model equations.

- You can include a program as a component in a calculation only when it is used as a function.

- Within a single dimension-based equation, all the dimension values must belong to the same dimension.

- When you assign the results of a calculation to a dimension value, the results must be numeric.

- Each dimension on which the model equations are based must be listed in a DIMENSION statement. When the model contains an INCLUDE statement, the appropriate DIMENSION statements must be inherited from the included model. When the model does not contain an INCLUDE statement, it must contain the appropriate DIMENSION statements. When you compile or run the model, Oracle OLAP searches through the dimensions listed in explicit or inherited DIMENSION statement to identify the dimension to which each dimension value belongs.

Dimension Status and Model Equations

When a model contains an assignment statement to assigns data to a dimension value, then the dimension is limited temporarily to that value, performs the calculation, and then restores the initial status of the dimension.

Formatting Conjoint Dimension Values

A special format is required when dimension-based equations refer to values of a conjoint dimension:

- Enclose the entire dimension value specification in angle brackets and then enclose this entire specification in single quotes; do not enclose the individual values in single quotes.

- Use the exact upper- and lowercase spellings for the base dimension values.

- When the specification includes a text value with an embedded blank, you must separate the dimension values with commas.

For example, assume that `item.org` is a conjoint dimension with base dimensions `item` and `org`. In this case, you use the following format to refer to values of `item.org`.

    '<Expenses, Direct Sales>'

Formatting Text Dimension Values

When dimension-based equations refer to text dimension values with embedded blanks or mixed upper- and lowercase letters, enclose the dimension value in single quotes. Use the exact upper- and lowercase spelling for the value.

For example, assume that a text dimension named `lineitem` contains a value with an embedded blank. In this case, you use the following format.

    'Software Revenue'

Specifying DAY, WEEK, MONTH, QUARTER, YEAR Values for a Model Equation

When a model equation is based on a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, you must use the dimension's VNF (value name format), rather than a date format, to specify the dimension's values. In addition, the VNF must format dimension values as follows:

- The value must start with a letter.

- The value can only contain letters, digits, underscores, and periods.

When the WEEK, MONTH, QUARTER, YEAR dimension of type does not have a VNF assigned to it, you can use the default VNF for the dimension. The entry for the VNF command lists the default VNF for each of these dimension types, and it explains how to assign a VNF to a dimension.

The default VNF for DAY dimensions is not acceptable because it specifies a digit as the first character of each dimension value. For a DAY dimension, specify the dimension name and enclose the value in parentheses and single quotes.

For example, for a DAY dimension named `daydim`, you can use the following format.

    daydim('01jul97')

Formatting INTEGER Dimension Values

When dimension-based equations refer to values of an INTEGER dimension, enclose the dimension value in single quotes.

For example, for an INTEGER dimension named `intdim`, use the following format to refer to the first dimension value.

    '1'

When the model is based on multiple dimensions, the model compiler might not be able to correctly identify the dimension to which a literal `INTEGER` value belongs. In this case, specify the name of the dimension and enclose the value in parentheses and single quotes as described in "Formatting Ambiguous Dimension Values".

Formatting Ambiguous Dimension Values

In some cases the model compiler might be unable to correctly identify the dimension to which a dimension value belongs. For instance, this can happen under the following circumstances:

- Two or more dimensions have a dimension value with the same name.

- A DAY dimension uses the default VNF (which starts with a digit).

- An `INTEGER` value could be interpreted either as a position within a dimension or as a literal `INTEGER` value of a dimension.

In cases such as these, you can avoid ambiguity in model-based equations by following these rules:

- Enclose the dimension value in single quotes.

- Enclose the quoted value in parentheses.

- Precede the parentheses with the name of the dimension.

For example, for an INTEGER dimension named `intdim`, use the following format to refer to the first dimension value.

    intdim('1')

#### Examples

Example 10-113 Assigning Values to a Variable

For the first example, suppose you have defined two variables, `units` and `price`, that are both dimensioned by `product`. The following example calculates dollar sales (`units` times `price`) for each value in the `product` dimension. Using an assignment statement, it stores the result in the variable `sales`, which is also dimensioned by `product`.

    sales = units*price

For another example, assume the `choicedesc` variable is dimensioned by `choice`. Before you enter data for the variable, the cells of the variable contain only NA values.

    CHOICE           CHOICEDESC
    -------------- --------------------
    Report         NA
    Graph          NA
    Analyze        NA
    Data           NA
    Quit           NA

Suppose you initialize the `choicedesc` variable using the following statement.

    choicedesc =  JOINCHARS ('Description for ' choice)

Now all of the `choicedesc` cells of the variable contain the appropriate values.

    CHOICE             CHOICEDESC
    -------------- -------------------------
    Report         Description for Report
    Graph          Description for Graph
    Analyze        Description for Analyze
    Data           Description for Data
    Quit           Description for Quit

The next example shows an expression that is dimensioned by `time`, `product`, and `district` and is assigned to a new variable. The expression calculates a 2002 sales plan based on unit sales in 2001.

    DEFINE units.plan INTEGER <month product district>
    LIMIT month TO 'DEC02'
    units.plan = LAG(units 12 month) * 1.15

Example 10-114 Assigning Values to a Relation

Assume that your analytic workspace contains the following definitions for a hierarchical dimension for Geography named `geog` and a relation named `geog_parentrel` that contains values that represent the child-parent relationships in the Geography hierarchy.

    DEFINE geog DIMENSION TEXT
    DEFINE geog_parentrel RELATION geog <geog>


You can use the following MAINTAIN ADD statements to populate the hierarchical dimension.

    " Populate the geog dimension with values for all levels
    MAINTAIN geog ADD 'North America' 'Europe' 'United States' 'Canada' 'France' 'Germany'
    MAINTAIN geog ADD 'Massachusetts' 'California' 'Quebec' 'Ontario'
    MAINTAIN geog ADD 'Boston''Springfield' 'San Francisco''Los Angeles' 'Toronto' 'Ottawa'
    MAINTAIN geog ADD 'Montreal''Quebec City' 'Paris' 'Marseilles' 'Bonn' 'Berlin'


You can use the following assignments statements to populate `geog_parentrel`. Note that you must limit `geog` to the appropriate values before you assign values to `geog_parentrel`.

    "  Limit geog (and therefore geog_parentrel) to countries and assign
    "   parent value (continent name) to those countries in geog_parentrel
    LIMIT geog to 'United States' 'Canada'
    geog_parentrel = 'North America'
    LIMIT geog to ALL
    LIMIT geog to 'France' 'Germany'
    geog_parentrel = 'Europe'

    "  Limit geog (and therefore geog_parentrel) to states or provinces and assign
    "   parent value (country name) to those states or provinces in geog_parentrel
    LIMIT geog to ALL
    LIMIT geog to 'Massachusetts' 'California'
    geog_parentrel = 'United States'
    LIMIT geog to ALL
    LIMIT geog to 'Quebec' 'Ontario'
    geog_OLAP DML Commands: A-G = 'Canada'

    "  Limit geog (and therefore geog_parentrel) to cities and assign
    "   parent value (state, province, or country) to those cities in geog_parentrel
    LIMIT geog to ALL
    LIMIT geog to 'Boston' 'Springfield'
    geog_parentrel = 'Massachusetts'
    LIMIT geog to ALL
    LIMIT geog to 'San Francisco' 'Los Angeles'
    geog_parentrel = 'California'
    LIMIT geog to ALL
    LIMIT geog to 'Montreal' 'Quebec City'
    geog_parentrel = 'Quebec'
    LIMIT geog to ALL
    LIMIT geog to 'Toronto' 'Ottawa'
    geog_parentrel = 'Ontario'
    LIMIT geog to ALL
    LIMIT geog to 'Paris' 'Marseilles'
    geog_parentrel = 'France'
    LIMIT geog to ALL
    LIMIT geog to 'Bonn' 'Berlin'
    geog_parentrel = 'Germany'
    LIMIT geog to ALL


A report of `geog_parentrel` shows the values have been assigned.

    COLWIDTH = 20
    REPORT geog_parentrel
    REPORT geog_parentrel

    GEOG                GEOG_PARENTREL
    ---------------- --------------------
    North America    NA
    Europe           NA
    United States    North America
    Canada           North America
    France           Europe
    Germany          Europe
    Massachusetts    United States
    California       United States
    Quebec           Canada
    Ontario          Canada
    Boston           Massachusetts
    Springfield      Massachusetts
    San Francisco    California
    Los Angeles      California
    Toronto          Ontario
    Ottawa           Ontario
    Montreal         Quebec
    Quebec City      Quebec
    Paris            France
    Marseilles       France
    Bonn             Germany
    Berlin           Germany

Example 10-115 Using a Qualified Data Reference

This example uses an assignment statement with a qualified data reference to assign values to the variable `budget`. The values assigned to one budget line item (`Net.Income`) are calculated as the difference between two other line items (`Opr.Income` and `Taxes`), so you have to use a qualified data reference to obtain the correct data values.

    budget(line Net.Income)= budget(line Opr.Income) - budget(line Taxes)

Example 10-116 Assigning Values to Variables with Composites

To have data assigned from `sales` only into existing data cells of `sparse_sales`, whose associated dimension values are in status, use the following statement.

    sparse_sales = sales ACROSS SPARSE<product market>

The `ACROSS` keyword is particularly helpful when the source expression is a single value. When there are no limits on the dimensions of `sparse_sales`, then an assignment statement like the following creates cells for every combination of dimension values because there are no cases where the source expression is NA.

    sparse_sales = 0

This defeats the purpose of a dimensioning a variable with a composite.

In contrast, the following statement sets only existing cells of `sparse_sales` to 0 (zero).

    sparse_sales = 0 ACROSS SPARSE<product market>

Example 10-117 Compacting Your Data

Suppose you only sell some of your products in each district. You currently have a variable `sales` that has data for certain combinations of districts and products and `NA` values for the rest. You can create a dense array of `sales` data by defining a composite or a conjoint dimension and using it as a dimension of a new variable. Use an assignment statement to assign the data directly to the new variable. When the values of the composite or conjoint dimension include all the combinations with data, you can then delete the original variable and save space in the analytic workspace.

    DEFINE proddist DIMENSION <product district>
    MAINTAIN proddist ADD <'Tents' 'Boston'> <'Canoes' 'Seattle'> -
       <'Sportswear' 'Atlanta'>
    DEFINE sales.dense DECIMAL <month proddist>
    sales.dense = sales
    LIMIT month TO FIRST 4

Issuing a `REPORT` `sales.dense` statement produces the following output.

                        ----------------SALES.DENSE----------------
    -----PRODDIST------ -------------------MONTH-------------------
    PRODUCT    DISTRICT   Jan95      Feb95      Mar95      Apr95
    -------- ---------- ---------- ---------- ---------- ----------
    Tents      Boston    32,153.52  32,536.30  43,062.75  57,608.39
    Canoes     Seattle   64,111.50  71,899.23  83,943.86  14,383.90
    Sportswear Atlanta  114,446.26 123,164.92 138,601.64 141,365.66

An alternative method would be to use a composite instead of a conjoint dimension. In this case, you could use the following statements.

    DEFINE sales.compact DECIMAL <month SPARSE <product district>>
    sales.compact = sales

Oracle OLAP automatically creates the unnamed composite when you define `sales.compact`, and it automatically adds dimension value combinations to the composite when you use an assignment statement. Oracle OLAP creates dimension value combinations only for the non-`NA` values of `sales`.

### 10.51 SET1

The SET1 command assigns a single value to a variable, option, relation, or dimension surrogate. When an object has one or more dimensions, the SET1 command assigns the value to the object cell that is in current status.

Because the SET1 command does not loop through a dimensioned object, you can use it in Assign trigger programs to assign a value to an object.

#### Syntax

SET1 target-name = expression 

#### Parameters

target-name
The name of the target object where the data is assigned and stored. For a list of analytic workspace objects that can be a target object, see Table 10-9.

expression
The source of the data values to be assigned to the object, see Table 10-9

#### Examples

For an example of using SET1, see Example 10-164.

### 10.52 SET_INCLUDED_MODEL

The SET_INCLUDED_MODEL program adds an INCLUDE model statement to a previously-defined cube dimension's model, or deletes an INCLUDE model statement from a previously-defined cube dimension's model. The changes made when this program executes are not transactional; an automatic COMMIT is executed as part of the program.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL SET_INCLUDED_MODEL(logical_dim, model_name, custom_model)

#### Parameters

CALL
Because SET_INCLUDED_MODEL is an OLAP DML program with arguments, you invoke it using the OLAP DML [CALL](olap-dml-commands-a-g.md) statement.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

**See Also:**

"[Guidelines for Specifying Values for the Names of Logical OLAP Objects](olap-dml-commands-a-g.md)"

model_name
A text expression that is the name of the logical model that is associated with the cube dimension.

custom_model
A text expression that is the OLAP DML-created model for which you want to add an INCLUDE statement.

**See:**

[CREATE_LOGICAL_MODEL](olap-dml-commands-a-g.md)

To remove an INCLUDE statement, specify `NA`.

#### Examples

Example 10-118 Creating Static and Dynamic Models for an OLAP Cube

Assume that you have created an OLAP cube dimension named `my_time` that dimensions an OLAP cube named `my_cube`. Within `my_cube` there are two measures: sales and moving_sales. Now you want to create static and dynamic models for `my_cube`.

1.  To create a static model, execute the following PL/SQL statement that executes a user-written OLAP DML program named `setup_pre_model`.

        exec dbms_aw.execute('call my_util_aw!setup_pre_model');

    As you can see from the following definition of the setup_pre_model program, the model is actually defined using the SET_INCLUDED_MODEL program and added using the ADD_CUBE_MODEL program, both of which are provided with the OLAP DML.

        DEFINE SETUP_PRE_MODEL PROGRAM
        PROGRAM

          VARIABLE _pre_model    text
          VARIABLE _aw_dim       text

          _pre_model = 'my_aw!my_pre_model'
          _aw_dim = OBJORG(DIM 'my_time')

          DEFINE &_pre_model model
          CONSIDER &_pre_model
          MODEL JOINLINES(JOINCHARS('dimension ' _aw_dim) -
                          JOINCHARS(_aw_dim '(\'L3_3\')=10') -
                          'end')

          CALL SET_INCLUDED_MODEL('my_time', 'pre_model', _pre_model)
          CALL ADD_CUBE_MODEL('my_cube', 'my_time', 'pre_model', YES)
        END

2.  Load the `my_time` dimension and load and solve `my_cube` by executing the following the PL/SQL statement.

        exec dbms_cube.build('MY_CUBE');

3.  You can now report on the initial values of sales and moving sales with the static model by issuing the following statement.

        select my_time||'  '||lpad(sales, 2)||'  '||lpad(moving_sales, 2)
        from my_cube_view
        order by my_time asc;

        MY_TIME||''||LPAD(SALES,2)||''||LPAD(MOVING_SALES,2)
        --------------------------------------------------------------------
        L1_1  14  14
        L2_1  12  12
        L2_2   2  14
        L3_1   1   1
        L3_2   1   2
        L3_3  10  11
        L3_4   1  11
        L3_5   1   2

        8 rows selected.


4.  To create a dynamic model where L1_2 = (L2_2' \* 2) execute the following PL/SQL statement that calls a user-written OLAP DML program named SETUP_POST_MODEL.

        exec dbms_aw.execute('call my_util_aw!setup_post_model');


    As you can see from the definition of the user-written `setup_post_model` program shown below, the model is actually defined using the SET_INCLUDED_MODEL program and added using the [ADD_CUBE_MODEL](olap-dml-commands-a-g.md) program, both of which are provided with the OLAP DML.

        DEFINE SETUP_POST_MODEL PROGRAM
        PROGRAM

          VARIABLE _post_model   text
          VARIABLE _aw_dim       text
          VARIABLE _start_date   text
          VARIABLE _timespan     text
          VARIABLE _member       text

          _post_model = 'my_aw!my_post_model'
          _aw_dim = OBJORG(DIM 'my_time')
          _start_date = OBJORG(ATTRIBUTE 'my_time' 'start_date')
          _timespan = OBJORG(ATTRIBUTE 'my_time' 'timespan')
          _member = 'L1_0'

          DEFINE &_post_model model
          CONSIDER &_post_model
          MODEL JOINLINES( -
                   JOINCHARS('dimension ' _aw_dim) -
                   JOINCHARS(_aw_dim '(\'' _member '\')=' _aw_dim '(\'L2_2\')*2') -
                   'end')

          CALL SET_INCLUDED_MODEL('my_time', 'post_model', _post_model)
          CALL ADD_CUBE_MODEL('my_cube', 'my_time', 'post_model', NO)

          " Add _member to the dimension
          CALL ADD_DIMENSION_MEMBER(_member, 'my_time', NA, 'L1', NA, NO)
          CALL UPDATE_ATTRIBUTE_VALEU(_member, 'my_time', 'start_date', -
                                      &_start_date(&_aw_dim 'L1_1')-365, NO)
          CALL UPDATE_ATTRIBUTE_VALUE(_member, 'my_time', 'timespan', -
                                      &_timespan(&_aw_dim 'L1_1'))
          UPDATE
          COMMIT
        END


5.  Execute the following statement to report on the new values of `my_time`, `sales` and `moving_sales`.


        select my_time||'  '||lpad(sales, 2)||'  '||lpad(moving_sales, 2)
            from my_cube_view
            order by my_time asc;

        MY_TIME||''||LPAD(SALES,2)||''||LPAD(MOVING_SALES,2)
        --------------------------------------------------------------------
        L1_0   4   4
        L1_1  14  18
        L2_1  12  12
        L2_2   2  14
        L3_1   1   1
        L3_2   1   2
        L3_3  10  11
        L3_4   1  11
        L3_5   1   2

        9 rows selected.

### 10.53 SET_PROPERTY

The SET_PROPERTY program modifies the values of the [\$LOOP_DENSE](olap-dml-properties.md) or [\$LOOP_VAR](olap-dml-properties.md) properties of a derived measure of a cube as defined in the Oracle data dictionary. The changes made when this program executes are not transactional; an automatic COMMIT is executed as part of the program.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL SET_PROPERTY(property_name, logical_cube, meas_name, property_value)

#### Parameters

CALL
Because SET_PROPERTY is an OLAP DML program with arguments, you invoke it using the OLAP DML [CALL](olap-dml-commands-a-g.md) statement.

property_name
A text expression that is either \$LOOP_VAR or \$LOOP_DENSE.

logical_cube
A text expression that is the Oracle data dictionary name of the cube that contains meas_name.

**See Also:**

"[Guidelines for Specifying Values for the Names of Logical OLAP Objects](olap-dml-commands-a-g.md)"

meas_name
A text expression that is the Oracle data dictionary name of the derived measure for which you want to modify the value of either the \$LOOP_VAR or \$LOOP_DENSE property.

property_value
A text expression that is a valid value for the property you specified in property_name. For valid values, see [\$LOOP_DENSE](olap-dml-properties.md) or [\$LOOP_VAR](olap-dml-properties.md).

### 10.54 SHOW

The SHOW command shows a single value of an expression. Normally, you would use SHOW to show the value of a single-cell variable or to show a message. SHOW is useful in programs when you want to generate an error-like message without creating an error condition. The output from SHOW is sent to the current outfile.

#### Syntax

SHOW expression \[NONL\]

#### Parameters

expression
The value you want to show. When expression is dimensioned, only the first value of the expression is shown, based on the current status of its dimensions. When you are showing a text literal, you must enclose the value in single quotes.

NONL
Indicates that a new line sequence should not be appended to the end of the value. By default, SHOW appends a new line sequence.

#### Usage Notes

Concatenating Output Lines

The NONL argument to SHOW is useful in programs. Using this argument you can concatenate several values into a single line of output. To accomplish this, include one or more SHOW commands with the NONL argument, followed by a single SHOW statement without the NONL argument. The values from all the SHOW commands are concatenated into a single output value, in the order specified. Depending on the length of the line, this value might actually produce multiple lines of output.

Generating Error Messages

SHOW can be used as an alternative to SIGNAL when you want to generate an error message from a program. Unlike SIGNAL, SHOW produces a message without signaling an error condition and thus halting execution of the program. Your error message may be most useful when you send it to a debugging file. When you use a DBGOUTFILE statement to direct messages to a debugging file, the output from SHOW is sent to the debugging file and to your current outfile.

Showing Values of Composites

When SHOW is used with a named or unnamed composite, an `NA` value is shown when the composite does not have a value that corresponds to the first values in the status for its base dimensions. For example, the statement

    SHOW SPARSE <market product>

produces an `NA` value when the combination of the current values of `market` and `product` does not exist in the composite.

Breaking Lines of Text

To break a text expression into two or more lines of output text, insert newline delimiters (\n) at the appropriate places in the text.

Using SHOW With NTEXT Values

The SHOW command converts NTEXT values to the character set of the outfile. When an NTEXT value cannot be represented in the outfile character set, the character is not displayed correctly.

#### Examples

Example 10-119 Showing the Value of an Option

This example uses SHOW to report the current value of the DECIMALS option. The OLAP DML statement

    SHOW DECIMALS

produces the following output.

    2

Example 10-120 Showing a Data Value

When you use SHOW to report the value of a dimensioned variable, only the first value of the variable, based on the current status of its dimensions, is shown. The OLAP DML statement

    SHOW JOINCHARS('Actual = ' actual)

produces the following output.

    Actual = 533,362,88

Example 10-121 Creating Error Messages Using SHOW

When you want to produce a warning message without branching to an error label, then you can use a `SHOW` statement.

    select:
    LIMIT month TO nummonths
    IF STATLEN(month) GT 9
       THEN DO
         SHOW 'You can select no more than 9 months.'
         GOTO finish
         DOEND
    REPORT DOWN district W 6 units
    finish:
    POP month
    RETURN

Example 10-122 Showing the Values of a Valueset

Suppose an analytic workspace contains a valueset called `monthset` that has the values `Jan95`, `May95`, and `Dec95`. You can use SHOW to list the values in that valueset.

    SHOW monthset
    Jan95
    May95
    Dec95

### 10.55 SIGNAL

The SIGNAL command produces a user-defined error message from within a program. When Oracle OLAP executes a SIGNAL statement when TRAP is ON, execution branches to the trap label. Any statements following the trap label in the program are then executed.When the program contains an active trap label, execution branches to the label. Without a trap label, execution of the program terminates and, when the program was called by another program, execution control returns to the calling program.

#### Syntax

SIGNAL {errname \[message\]\|STOP}

#### Parameters

errname
A TEXT expression that indicates the name of the error message to be produced. When Oracle OLAP executes a SIGNAL statement, it stores the errname in the ERRORNAME option. Normally, the name of the error does not appear in the error message. However, when you omit message, the error name (errname) appears along with a stock message as described in the message argument.

You can use the special name `PRGERR` to communicate to a calling program that an error has occurred. The statement `SIGNAL` `PRGERR` sets ERRORNAME to a blank value and passes an error condition to the calling program without causing another error message to be displayed. For a complete explanation of how to use SIGNAL to pass an error up a chain of nested programs, see the TRAP command.

message
A TEXT expression that specifies the error message to be produced. When you supply a long line as your error message, you must add your own line breaks to format the text. Type the newline escape sequence (\n) where you want each line to end. You can type up to a limit of 6 lines or 4,000 characters, whichever you reach first. An error occurs when you try to supply a single line longer than 4,000 characters.

When you omit this argument, SIGNAL produces the following message.

    ERROR: (errname) Please contact the administrator of your
       Oracle Oracle OLAP application.

When Oracle OLAP executes a SIGNAL statement, it stores message in the ERRORTEXT option.

STOP
Immediately stops execution of all currently running programs. No error message is produced. The error condition is not trapped by an active TRAP label.

#### Examples

Example 10-123 Signaling an Error

Suppose you have written a program that requires one argument. When no argument is supplied, there is no purpose in running the program. Therefore, the first thing the program does is check if an argument has been passed. When it has not, the program terminates after sending an error message to the current outfile.

The following program lines check for the argument and signal an error when it is not found.

    IF ARGS EQ ''
    THEN SIGNAL msg1 'You must supply an argument.'

SIGNAL sends the following message to the current outfile.

    ERROR: You must supply an argument.

Example 10-124 Signaling an Error When an Argument Value is Invalid

Suppose your program produces a report that can present from one to nine months of data. You can signal an error when the program is called with an argument value greater than nine. In this example, `nummonths` is the name of the argument that must be no greater than nine.

    select:
    TRAP ON error
    PUSH month
    LIMIT month TO nummonths
    IF STATLEN(month) GT 9
       THEN SIGNAL toomany -
         'You can specify no more than 9 months.'
    REPORT DOWN district W 6 units
    finish:
    POP month
    RETURN
    error:
    POP month
    IF ERRORNAME EQ 'TOOMANY'
       THEN SHOW 'No report produced'

### 10.56 SLEEP

Within an OLAP DML program, the SLEEP command suspends the program execution for at least the specified number of seconds.

**Note:**

SLEEP is rarely used in Oracle OLAP programs, because there is seldom a need to suspend program execution.

#### Syntax

SLEEP n

#### Parameters

n
A numeric expression that specifies the number of seconds for Oracle OLAP to "sleep." Program execution is suspended for at least this number of seconds.

#### Examples

Example 10-125 Suspending Program Execution

In a program, suppose you execute a statement that might take 10 seconds to complete. You can follow that statement with this SLEEP statement, which suspends program execution for 10 seconds.

    SLEEP 10

### 10.57 SORT command

The SORT command arranges the order of values in the current status list of a dimension or a dimension surrogate, or in a valueset.

**See Also:**

[SORT function](olap-dml-functions-l-z.md)

#### Syntax

SORT dimension \[byhierarchy\] \[bycriterion...\]

where:

- `byhierarchy` is an optional phrase that uses a parent relation to arrange the order of values in the current status list of a hierarchical dimension or its dimension surrogate, or to assign values to a valueset, based on family relationships within the hierarchy. You can include only one `byhierarchy` phrase in a SORT statement. It must be the first phrase in a SORT statement.

  `HIERARCHY` `parent-relation` ` [INVERT] [DEPTH` `n``] [SORTORPHANS] `

- `bycriterion` uses an explicit criterion to arrange the order of values in the current status list of a dimension or its dimension surrogate, or to assign values to a valueset. You can include as many `bycriterion` phrases as you want in a SORT statement.

  `{A|D} [NAFIRST] ``criterion`

#### Parameters

dimension
A text expression whose value is the name of a dimension, a dimension surrogate, or a valueset.

HIERARCHY
Specifies that Oracle OLAP is to sort dimension values based on the values position in parentrel.

parent-relation
Specifies the name of a child-parent self-relation for dimension. For each dimension value, the relation holds another value of the dimension which is its parent dimension value (the one immediately above it in a given hierarchy). This parent relation can have multiple dimensions.

**Tip:**

You can specify a QDR of parent-relation to specify a single value.

INVERT
Indicates that Oracle OLAP places the children in the hierarchy before their parents. (By default, children are placed after their parents.)

DEPTH n
Specifies the number of generations down from the top of the hierarchy that Oracle OLAP should place into status and. there, for the values that are included in the result. The default value of n is 99. When you do not want any values in the result (that is, when you want a `NULL` status), specify `-1` for n. When you only want the top of the hierarchy in status (that is, those dimension values that do not have parents), specify` 0` (zero).

SORTORPHANS
Specifies that all first cousins whose parents are not in status are sorted together. By default, Oracle OLAP preserves the hierarchical structure when sorting children even when their parents are not in status.

A
D
The order in which the values are to be sorted. `A` means ascending order (alphabetical when the sorting criterion is TEXT, ID, or a relation), and `D` means descending order (reverse alphabetical when the sorting criterion is TEXT, ID or a relation).

NAFIRST
Specifies that `NA` values are to placed first in the sort rather than last.

criterion
The expression to be used as a sorting criterion. Each criterion must be dimensioned by dimension. The first expression is the major sorting criterion. When the expression is multidimensional, SORT uses the first value in status for all dimensions other than the dimension being sorted. You cannot use a valueset as the sorting criterion.

#### Usage Notes

Sorting a Dimension and a Valueset

When Oracle OLAP sorts a dimension, it sorts the temporary status list of a dimension, not the data dimensioned by it. Because many OLAP DML statements operate on data according to the current status of its dimensions, sorting a dimension appears to have the effect of sorting data. A dimension and any dimension surrogates for it share the same status. Therefore, a SORT statement on a dimension or any of its surrogates sorts them all.

When Oracle OLAP sorts a valueset, it sorts the actual values within the valueset. When you execute UPDATE and COMMIT commands after sorting a valueset, the values in the valueset are stored in that sorted order.

Sorting Alphabetically

To sort a TEXT or ID dimension or its valueset in alphabetical order, use the dimension itself as the sorting criterion.

    SORT district A district

Sort Order for Textual Data

The sort order for textual data in an alphabetical sort is controlled by the NLS_SORT option.

Sorting a Time Dimension

The values of dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR are stored internally as numbers. Therefore, when you sort a dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR dimension or its valueset in ascending order, with the dimension itself as the sorting criterion, then the values in the status list or valueset are placed in chronological order. When you sort a dimensions of type DAY, WEEK, MONTH, QUARTER, and YEAR dimension or its valueset in descending order, then the values are placed in reverse chronological order.

Sorting Using a Relation as a Criterion

When you use a relation as your sorting criterion, then the sorting is done alphabetically; that is, the dimension or valueset is sorted according to an alphabetical list of the related dimension values. To use a relation as the sorting criterion and keep the related dimension values in their original order, you must use the following expression as your sorting criterion.

    CONVERT(relation, INTEGER)

See Example 10-126.

Sorting Conjoint Dimensions

You can sort a conjoint dimension or its valueset by criteria dimensioned by either the conjoint dimension itself or by one of its base dimensions.

Sorting Concat Dimensions

You can sort a concat dimension or its valueset by criteria dimensioned by either the concat dimension itself or by one of its component dimensions. See Example 10-127 and Example 10-128.

Sorting a Worksheet

You cannot use a worksheet as a sort criterion. You must first use CONVERT to specify the data type to which values of the worksheet should be converted.

#### Examples

Example 10-126 Sorting Using a Relation as the Criterion

This example sorts districts according to their unit sales of tents for July 1996. They are sorted first by the region to which they belong and then in descending order of dollar sales. Notice that in the following SORT statement, a relation is used as the primary sorting criterion. Consequently, the districts are sorted by regions listed alphabetically.

    LIMIT month TO 'Jul96'
    LIMIT product TO 'Tents'
    SORT district A Region.District D sales

Assume you issue the following REPORT statement.

    REPORT DOWN district HEADING 'Region' region.district sales

The preceding statement produces the following report that reflects the work of the SORT statement.

    PRODUCT: Tents
                   --------MONTH--------
                   --------JUL96--------
    DISTRICT         Region     SALES
    -------------- ---------- ----------
    Dallas         Central    154,914.23
    Chicago        Central     79,934.42
    Atlanta        East       140,711.00
    Boston         East        93,972.49
    Seattle        West       123,700.17
    Denver         West       100,413.49

In the following SORT statement, CONVERT is used to keep the regions in their original order.

    SORT district A CONVERT(region.district INTEGER) D sales

Assume that you issue the following REPORT statement.

    REPORT DOWN district HEADING 'Region' region.district sales

The preceding statement produces the following report that reflects the work of the last SORT statement.

    PRODUCT: Tents
                   --------MONTH--------
                   --------JUL96--------
    DISTRICT         Region     SALES
    -------------- ---------- ----------
    Atlanta        East       140,711.00
    Boston         East        93,972.49
    Dallas         Central    154,914.23
    Chicago        Central     79,934.42
    Seattle        West       123,700.17
    Denver         West       100,413.49

When you want the dimension to keep the sorted order of its values permanently, use a MAINTAIN statement after you sort the dimension.

    SORT district A district
    MAINTAIN district MOVE STATUS FIRST

Example 10-127 Sorting Based on a Concat

The following statements sort the concat dimension `reg.dist.ccdim` in ascending order based on all of its values and report the result.

    sort reg.dist.ccdim d reg.dist.ccdim
    report reg.dist.ccdim

The preceding statement produces the following results.

    REG.DIST.CCDIM
    --------------------
    <Region: West>
    <Region: East>
    <Region: Central>
    <District: Seattle>
    <District: Denver>
    <District: Dallas>
    <District: Chicago>
    <District: Boston>
    <District: Atlanta>

The following statements sort the concat dimension `reg.dist.ccdim` in ascending order based on all of its values and report the result.

    SORT reg.dist.ccdim A reg.dist.ccdim
    REPORT reg.dist.ccdim

The preceding statement produces the following results.

    REG.DIST.CCDIM
    --------------------
    <District: Atlanta>
    <District: Boston>
    <District: Chicago>
    <District: Dallas>
    <District: Denver>
    <District: Seattle>
    <Region: Central>
    <Region: East>
    <Region: West>

Example 10-128 Sorting Based on a Component

The following statements sort the concat dimension `reg.dist.ccdim` in ascending order based on the values of one of its base dimensions and in descending order based on the values of its other base dimension, and report the result.

    SORT reg.dist.ccdim A region D district
    REPORT reg.dist.ccdim

The preceding statement produces the following results.

    REG.DIST.CCDIM
    --------------------
    <REGION: CENTRAL>
    <REGION: EAST>
    <REGION: WEST>
    <DISTRICT: SEATTLE>
    <DISTRICT: DENVER>
    <DISTRICT: DALLAS>
    <DISTRICT: CHICAGO>
    <DISTRICT: BOSTON>
    <DISTRICT: ATLANTA>

Example 10-129 Sorting by Hierarchy

Assume that your analytic workspace has two dimensions (`geog` and `time`), one relation (`geogparent`) and one variable (`sales`) with the following definitions.

    DEFINE GEOG DIMENSION TEXT
    DEFINE TIME DIMENSION TEXT
    DEFINE GEOGPARENT RELATION GEOG <GEOG>
    DEFINE SALES VARIABLE INTEGER <TIME GEOG>


If you issue a REPORT statement for `sales` when all of the values of `geog` are in status, Oracle OLAP produces the following report. This report displays the values for `geog` in the order in which they were added to the analytic workspace.

    REPORT sales
                   --------SALES--------
                   --------TIME---------
    GEOG              2004       2005
    -------------- ---------- ----------
    USA                 1,300         NA
    Massachusetts       3,881         NA
    Florida             3,479         NA
    Boston              2,644         NA
    Orlando             4,398         NA
    Miami               3,294         NA
    Pembroke            4,268         NA
    California          1,899         NA
    Texas               2,115         NA
    Los Angeles         2,394         NA
    San Francisco       1,334         NA
    Dallas                839         NA
    Houston               997         NA


However, assume that you issue a SORT statement to sort the values of `geog` by (1) `geogparent `and (2) descending by `sales`. After this sort if you issue a REPORT statement for `sales`, Oracle OLAP produces the following report. This report displays the values for `geog` with the states in descending order by `sales`, but with the cities of each state under the appropriate state.

    SORT geog HIERARCHY geogparent D sales
    REPORT SALES

                   --------SALES--------
                   --------TIME---------
    GEOG              2004       2005
    -------------- ---------- ----------
    USA                 1,300         NA
    Massachusetts       3,881         NA
    Pembroke            4,268         NA
    Boston              2,644         NA
    Florida             3,479         NA
    Orlando             4,398         NA
    Miami               3,294         NA
    Texas               2,115         NA
    Houston               997         NA
    Dallas                839         NA
    California          1,899         NA
    Los Angeles         2,394         NA
    San Francisco       1,334         NA


Example 10-130 Sorting Orphans of a Hierarchy

Assume that you have the same objects described in Example 10-129. Assume also that the states of Florida and Massachusetts are not in status.

When you include the SORTORPHANS keyword in your SORT statement, the cities in Massachusetts and Florida are sorted together.

    SORT geog HIERARCHY geogparent SORTORPHANS D sales
    REPORT sales
                   ------------------SALES------------------
                   ------------------TIME-------------------
    GEOG                   2004                 2005
    -------------- -------------------- --------------------
    USA                           1,300                   NA
    Orlando                       4,398                   NA
    Pembroke                      4,268                   NA
    Miami                         3,294                   NA
    Boston                        2,644                   NA
    Texas                         2,115                   NA
    Houston                         997                   NA
    Dallas                          839                   NA
    California                    1,899                   NA
    Los Angeles                   2,394                   NA
    San Francisco                 1,334                   NA


However, if you exclude the SORTORPHANS keyword, Massachusetts cities and Florida cities are sorted separately.

    LIMIT geog COMPLEMENT 'Florida' 'Massachusetts'
    SORT geog HIERARCHY geogparent D sales
    REPORT SALES

                  --------SALES--------
                   --------TIME---------
    GEOG              2004       2005
    -------------- ---------- ----------
    USA                 1,300         NA
    Pembroke            4,268         NA
    Boston              2,644         NA
    Orlando             4,398         NA
    Miami               3,294         NA
    Texas               2,115         NA
    Houston               997         NA
    Dallas                839         NA
    California          1,899         NA
    Los Angeles         2,394         NA
    San Francisco       1,334         NA


### 10.58 SQL

The SQL command passes instructions written in Structured Query Language (SQL) to the relational manager from Oracle OLAP. Using the SQL command, you can insert and update data in relational tables, retrieve data from relational tables into analytic workspace objects, and execute stored procedures.

To use the SQL command, you must be familiar with SQL syntax and with the data structures in your relational database, and have the appropriate access rights to the relational tables that you want to use.

This entry describes the OLAP DML SQL command in general, and subsequent entries discuss the use of the OLAP DML SQL command for specific SQL statements:

- SQL CLEANUP

- SQL CLOSE

- SQL DECLARE CURSOR

- SQL EXECUTE

- SQL FETCH

- SQL IMPORT

- SQL OPEN

- SQL PREPARE

- SQL PROCEDURE

- SQL SELECT

#### Syntax

SQL sql-statement

#### Parameters

sql-statement
For sql-statement you can specify most SQL statements that can be executed dynamically and also several associated non-dynamic statements. You can also specify PROCEDURE for a stored procedure as described in SQL PROCEDURE. A SQL statement cannot exceed 128K bytes including the values of all non-textual OLAP DML input expressions.

You cannot specify the following SQL statements for sql-statement:

- `COMMIT` -- To commit your changes, issue the OLAP DML COMMIT statement.

- `ROLLBACK` -- You cannot rollback using the OLAP DML. When you specify SQL `ROLLBACK`, you receive an error message stating that `ROLLBACK` is not supported as an argument to an OLAP DML SQL statement.

  **Note:**

  When you use an OLAP DML SQL statement to request a rollback in some other fashion (for example, using SQL EXECUTE), Oracle OLAP issues a system error message, abnormally terminates the OLAP DML program that issued the statement. Oracle OLAP also detaches, in an indeterminate state, the analytic workspace that contains the OLAP DML program that made the rollback request and any other attached analytic workspaces with uncommitted updates.

Oracle OLAP evaluates some SQL statements before sending them to the relational manager. For example, Oracle OLAP evaluates SQL PREPARE and SQL EXECUTE, and SQL statements that copy data from relational tables into analytic workspace objects (See "Copying Relational Data into Analytic Workspace Objects" for a list of these statements).

#### Usage Notes

Copying Relational Data into Analytic Workspace Objects

You can copy relational data into analytic workspace objects using either an implicit cursor or an explicit cursor:

- To copy data from relational tables into analytic workspace objects using an implicit cursor, use a SQL SELECT statement. You can use this OLAP DML statement interactively in the OLAP Worksheet or within an OLAP DML program.

- To copy data from relational tables into analytic workspace objects using an explicit cursor, use the following commands within an OLAP DML program in the order indicated:

  1.  SQL DECLARE CURSOR to define a SQL cursor by associating it with a SELECT statement or procedure.

  2.  SQL OPEN to activate a SQL cursor.

  3.  SQL FETCH or SQL IMPORT to retrieve and process data specified by a cursor.

      **Tip:**

      SQL FETCH offers the most functionality; while SQL IMPORT offers improved performance when copying large amounts of data from relational tables into analytic workspace object.

  4.  SQL CLOSE to close a SQL cursor.

  5.  SQL CLEANUP to cancel all SQL cursor declarations and free the memory resources of an SQL cursor.

Oracle OLAP evaluates all of these statements before sending them to the relational manager.

For the syntax of these statements, see the individual topics. For the syntax of other SQL statements, refer to Oracle Database SQL Language Reference.

Inserting Data into a Relational Table

You can insert analytic workspace data into a relational table using SQL PREPARE statement for a SQL INSERT statement (typically with DIRECT= YES), and then executing the statement using SQL EXECUTE.

Options Related to the OLAP DML SQL Statements

Several options are available to you when embedding SQL into the OLAP DML. These options are listed in "[SQL Embed Options](olap-dml-options.md)".

Using OLAP DML Expressions in OLAP DML SQL Statements

You can use OLAP DML expressions (for example, OLAP DML variables) as arguments in many OLAP DML SQL statements. OLAP DML input expressions are values supplied by Oracle OLAP as parameters to a SQL statement. They specify the data to be selected or provide values for data that is being modified. You can use OLAP DML input expressions in SQL `WHERE` clauses, parameter list for procedures, `UPDATE` statements, and the value clause of `INSERT`.

Keep the following points in mind when using an OLAP DML expression in an OLAP DML SQL statement:

- OLAP DML expressions must be preceded by a colon (for example, `:myvar`).

- When you specify a dimension or a dimensioned variable as an OLAP DML input expression, the first value in status is used; no implicit looping occurs, although you can use a FOR or an ACROSS statement to loop through all of the values. An OLAP DML input expression can be any expression with an appropriate data type. The value of an OLAP DML input expression is taken when a cursor is opened, not when it is declared. See Example 10-131.

- To update or insert data in a relational table that has either the CLOB and NCLOB data type, you use `WIDE` in the OLAP DML input expression as described in "Inserting Large Text Values into a CLOB or NCLOB Column" .

Error Checking

Oracle OLAP can detect some syntax errors in the arguments to the SQL statement, but most errors are detected by the Oracle RDBMS. Error codes and messages are returned to Oracle OLAP. Check the value of SQLCODE after each SQL statement to determine when it resulted in an error. When it does cause an error (that is when `SQLCODE EQ -1`), check the value of SQLERRM for information about the cause of the error.

Converting Oracle RDBMS Data Types into Oracle OLAP DML Data Types

The following table shows which Oracle RDBMS data types can be automatically converted into Oracle OLAP DML data types. You must explicitly convert or cast other data types in the SELECT statement within a SQL DECLARE CURSOR statement.

Table 10-10 RDBMS Data Type Conversion to OLAP DML Data Types

| Oracle RDBMS Data Type                                    | OLAP DML Dimension Type                            | OLAP DML Variable Data Type                                                              |
|:----------------------------------------------------------|:---------------------------------------------------|:-----------------------------------------------------------------------------------------|
| `CHAR,` `NCHAR`, `NVARCHAR2`, `VARCHAR2`                  | `TEXT [WIDTH` `n``]`, `ID,` `NTEXT`                | `TEXT`, `NTEXT`                                                                          |
| `NUMBER`                                                  | `NUMBER`, `INTEGER`, `SHORTINTEGER`, `LONGINTEGER` | `NUMBER`, `INTEGER`, `BOOLEAN`, `SHORTINTEGER`, `LONGINTEGER`, `DECIMAL`, `SHORTDECIMAL` |
| `CLOB` (only within SQL FETCH and SQL SELECT statements)  | `TEXT`                                             | `TEXT`                                                                                   |
| `NCLOB` (only within SQL FETCH and SQL SELECT statements) | `NTEXT`                                            | `NTEXT`                                                                                  |
| `DATE`                                                    | \-                                                 | `DATE`, `DATETIME`                                                                       |

SQL UPDATE Statements

`SQL` `UPDATE` statements can contain a `WHERE` clause, which specifies a particular search condition. In addition to the search conditions typically used in SQL, the phrase `WHERE` `CURRENT` `OF` `cursor` is supported for single tables and views that include columns from only one table. The cursor must have been defined with the `FOR` `UPDATE` clause as described in SQL DECLARE CURSOR.

#### Examples

Example 10-131 Inserting Data in a Table

You can use SQL statements such as the following to create a table and add rows to that table. The SQL INSERT statement adds a row to the `sales` table using values from the dimension `salesperson` and the variable `dollars`. It adds one row using the first value of `salesperson` that is in status.

    SQL CREATE TABLE sales (name CHAR(12), dollars INTEGER)
    SQL INSERT INTO sales VALUES (:salesperson, :dollars)

#### 10.58.1 SQL CLEANUP

The SQL CLEANUP command cancels all SQL cursor declarations and frees the memory resources for all SQL cursors. You use the SQL CLEANUP command in combination with other SQL commands to copy data from relational tables into analytic workspace objects as outlined in "Copying Relational Data into Analytic Workspace Objects"

##### Syntax

SQL CLEANUP

##### Examples

For an example of the use of SQL CLEANUP, see Example 10-141.

#### 10.58.2 SQL CLOSE

The SQL CLOSE command closes a SQL cursor. You use the SQL OPEN command in combination with other SQL commands to copy data from relational tables into analytic workspace objects as outlined in "Copying Relational Data into Analytic Workspace Objects".

##### Syntax

SQL CLOSE cursor

##### Parameters

cursor
The name of a cursor previously opened with a SQL OPEN statement.

##### Usage Notes

Redefining the Result Set

You can change the result set associated with a cursor by closing the cursor, setting the value of an OLAP DML input expression, and issuing a new SQL OPEN statement. You do not have to free the cursor and redeclare it.

#### 10.58.3 SQL DECLARE CURSOR

The SQL DECLARE CURSOR command defines an explicit SQL cursor by associating it with a `SELECT` statement or procedure. The `SELECT` statement specifies the scope of the data (the rows and columns) selected by the cursor. You use the SQL DECLARE CURSOR command in combination with other SQL commands to use an explicit cursor to copy data from relational tables into analytic workspace objects as outlined in "Copying Relational Data into Analytic Workspace Objects".

Two pseudo procedures, `SQLTABLES` and `SQLCOLUMNS`, allow you to obtain information about tables and columns.

##### Syntax

SQL DECLARE cursor CURSOR FOR {select-statement \[FOR UPDATE\]\|table-info}

where `table-info` is one of the following:

- `PROCEDURE SQLTABLES [``owner``, ``table``]`
- `PROCEDURE SQLCOLUMNS [``owner``, ``table``, ``column``]`

**Note:**

You specify `table-info` only to declare a cursor when select-statement is a SQL FETCH statement.

##### Parameters

cursor
The name of the cursor you are defining. Cursor names can consist of 1 to 18 alphanumeric characters or the symbols `@`, `_`, `$`, or `#`. A name that contains symbols `@`, `$`, or `#` must be enclosed in single quotes. The first character cannot be a number or an underscore. Cursor names are internal to Oracle OLAP. Unless you have issued a SQL CLEANUP statement, when you try to declare a cursor with the same name as a previously declared cursor, but with a different SQL `SELECT` statement, an error is signaled.

select-statement
A SQL SELECT statement that identifies the data you want to associate with the cursor. For the syntax of an SQL SELECT statement, refer to Oracle Database SQL Language Reference.

**Tip:**

Because both OLAP DML syntax and SQL syntax allow you to use AND and OR, construct the clause clearly so that Oracle OLAP can identify the end of an OLAP DML input expression. Use parenthesis to clarify the syntax in these situations and when using a SQL operator that is unknown in Oracle OLAP.

FOR UPDATE
Indicates that SQL FETCH is used to write data to the table. This clause is required when the cursor is used in an `UPDATE` statement with a `WHERE` `CURRENT` `OF` `cursor` clause. The names of the columns to be updated can be listed in an `OF` clause (for example, `FOR` `UPDATE` `OF` `COL1,` `COL2,` `COL3`).

**Note:**

The FOR UPDATE clause is ignored by SQL IMPORT and SQL SELECT.

PROCEDURE SQLTABLES
When declaring a cursor for use by SQL FETCH, calls the pseudo procedure `SQLTABLES`, which returns the following values for each table that matches the search criterion as illustrated in Example 10-133:

- tableowner -- A text value identifying the owner of the table.

- tablename -- A text value identifying the name of the table.

- tabletype -- A text value identifying the type of table using one of the following: TABLE, VIEW, SYSTEM TABLE, ALIAS, SYNONYM, LOCAL TEMPORARY, GLOBAL TEMPORARY, or NA (indicating an unrecognized type).

When declaring a cursor for use by SQL IMPORT, you cannot use this clause.

PROCEDURE SQLCOLUMNS
When declaring a cursor for use by SQL FETCH, calls the pseudo procedure `SQLCOLUMNS`, which returns the following values for each column that matches the search criterion as illustrated in Example 10-134:

- tableowner -- A text value identifying the owner of the table.

- tablename -- A text value identifying the name of the table.

- colname -- A text value identifying the name of the column.

- coltype -- A text value identifying the data type of the column.

- olaptype -- A text value identifying the data type that most closely matches coltype.

- length -- An `INTEGER` value identifying the length of column values.

- precision -- An `INTEGER` value identifying the precision of numeric column values.

- scale -- An `INTEGER` value identifying the scale of column values.

- nullable -- A text value of `Y` or `N` indicating whether the column can contain null values.

When declaring a cursor for use by SQL IMPORT, you cannot use the PROCEDURE SQLCOLUMNS clause.

owner
Literal text or the name of an OLAP DML variable whose value specifies one or more owners. This expression acts as a filter to limit the results to only tables belonging to the specified owners. The keyword NULL or an OLAP DML variable with an `NA` value causes all table owners to be included in the results.

The expression can be specific, such as `'SCOTT'`, or it can contain wildcard characters such as `'S%T'` (all owners whose name begins with `S` and ends with `T`). The value retains its case when it is passed to the database, so be sure to enter the value with the appropriate use of upper- and lowercase letters. For example, Oracle relational databases by default store all values in uppercase and do not match `'scott'` or `'Scott'` with `'SCOTT'`.

table
Literal text or the name of an OLAP DML variable whose value specifies one or more tables. This expression acts as a filter to limit the results to only tables with the specified names. The keyword NULL or an OLAP DML variable with an `NA` value causes all tables to be included in the results.

The expression can be specific, such as `'PAYROLL',` or it can contain wildcard characters such as `'%ROLL'` (all tables whose name ends with `ROLL`). The value retains its case when it is passed to the database, so be sure to enter the value with the appropriate use of upper- and lowercase letters. For example, Oracle relational databases by default store all values in uppercase and do not match `'payroll'` or `'Payroll'` with `'PAYROLL'`.

column
Literal text or the name of an OLAP DML variable whose value specifies one or more columns. This expression acts as a filter to limit the results to only columns with the specified names. The keyword `NULL` or an OLAP DML variable with an NA value causes all tables to be included in the results.

The expression can be specific, such as `'SALARY'`, or it can contain wildcard characters such as `'SAL%'` (all columns whose name begins with `SAL`). The value retains its case when it is passed to the database, so be sure to enter the value with the appropriate use of upper- and lowercase letters. For example, Oracle relational databases by default store all values in uppercase and do not match `'salary'` or `'Salary'` with `'SALARY'`.

##### Usage Notes

General Restrictions that Apply to SQL DECLARE CURSOR

The following restrictions apply to the SQL DECLARE CURSOR command:

- You can use it only in a program.

- It cannot contain ampersand substitution.

Restrictions when Declaring a Cursor for Use by SQL IMPORT

When declaring a cursor to be used by a SQL IMPORT statement, you can only use the following simplified syntax.

SQL DECLARE cursor CURSOR FOR select-statement

where select-statement is a SQL `SELECT` statement that identifies the data you want to associate with the cursor. You cannot use the `FOR` `UPDATE` clause or the `table-info` clause.

Cursor's Result Set

A cursor's result set is determined at the time it is opened, and it is not updated later. Therefore, when you change the value of an OLAP DML input expression after you open its cursor, the change does not affect the cursor's result set. A cursor remains open until a SQL CLOSE statement is executed for that cursor or until a SQL CLEANUP statement closes all cursors. A cursor is not automatically closed at the termination of the program in which it was opened.

Optimizing Fetches

When fetching values into a multidimensional input variable, list the columns that correspond to the dimensions in an ORDER BY clause in the select-statement argument of a SQL DECLARE CURSOR statement, with the slowest-varying dimension first which optimizes performance.

##### Examples

Example 10-132 Testing for the Value of SQLCODE

Cursor `c1` is declared for three columns in the table `mkt`, which is owned by user `sqldba`. Values from the three columns are fetched into three analytic workspace objects. The first OLAP DML object is the `market` dimension, which is temporarily limited to the retrieved value. Because of the temporary status of `market`, the other column values are assigned to the appropriate cells of the other OLAP DML objects.

This example tests the value of SQLCODE in two places. A more complete program would do more error checking.

    DEFINE market DIMENSION TEXT
    DEFINE mkt.desc TEXT <market>
    DEFINE mkt.abbrev ID <market>
    DEFINE sql.market PROGRAM
    PROGRAM
    TRAP ON ERROR
    SQL DECLARE c1 cursor FOR -
       SELECT mktcode, mktabbrev, mktdesc FROM sqldba.mkt
    SQL OPEN c1
    IF SQLCODE NE 0
       THEN SIGNAL SQLERR 'open cursor failed.'
    WHILE SQLCODE EQ 0
       SQL FETCH c1 INTO :APPEND market, :mkt.abbrev, :mkt.desc
    SQL CLOSE c1
       ...
    RETURN
    error:
       ...
    END

Example 10-133 Discovering Information About Relational Tables

The following program fetches information about all tables owned by `Scott`. Notice that the value of the ownername variable is set after the SQL DECLARE cursor statement; it can be set any time before the SQL OPEN statement. The tablename variable is not set, but is initialized automatically to `NA`, which is passed as a null value.

    DEFINE ownername TEXT     "Search criteria
    DEFINE tablename TEXT     "Search criteria
    DEFINE tblowner TEXT      "Search results
    DEFINE tblname TEXT       "Search results
    DEFINE tbltype TEXT       "Search results
     
    SQL DECLARE c1 CURSOR FOR PROCEDURE sqltables(:ownername, :tablename)
    ownername = 'Scott'
    SQL OPEN c1
    WHILE SQLCODE EQ 0
       DO
       SQL FETCH c1 INTO :tblowner, :tblname, :tbltype
          ...     "Process fetched values
       DOEND

Example 10-134 Discovering Information About the Columns of a Relational Table

The following program fetches information about all columns in the `employee` table owned by `Scott`. Notice that `NULL` (and not `NA`) is used for the value of the third argument to `SQLCOLUMNS` because it is processed by the relational manager, not Oracle OLAP.

    DEFINE tblname TEXT             "Search results
    DEFINE tblowner TEXT            "Search results
    DEFINE colname TEXT             "Search results
    DEFINE coltype TEXT             "Search results
    DEFINE olaptype TEXT            "Search results
    DEFINE length INTEGER           "Search results
    DEFINE precision INTEGER        "Search results
    DEFINE scale INTEGER            "Search results
    DEFINE nullable TEXT            "Search results
     
    SQL DECLARE c1 CURSOR FOR PROCEDURE sqlcolumns('Scott', -
       'Employee', NULL)
    SQL OPEN c1
    WHILE SQLCODE EQ 0
       DO
       SQL FETCH c1 INTO :tblowner, :tblname, :colname, :coltype, -
       :olaptype, :length, :precision, :scale, :nullable
          ...  "Process fetched values
        DOEND

#### 10.58.4 SQL EXECUTE

The SQL EXECUTE command executes SQL statements that have been compiled using SQL PREPARE. Typically, the SQL statements that you precompile are statements that are executed repeatedly, particularly those involving OLAP DML input expressions, such as` INSERT`, `UPDATE`, and `DELETE`.

**Note:**

The SQL PREPARE and SQL EXECUTE commands can only be used within the same DML program.

##### Syntax

SQL EXECUTE statement-name

##### Parameters

statement-name
The name that you assigned to the executable code when you prepared it using SQL PREPARE.

##### Examples

Example 10-135 Updating a Relational Table Using Analytic Workspace Data

The next example shows a simple update of a table using data stored in Oracle OLAP. The market dimension is limited to one value at a time in the FOR loop. The SQL phrase `WHERE s.market=:market` specifies that the sales value in the row for that market is the value that is changed.

    FOR market
       SQL UPDATE mkt SET sales=:mkt.sales WHERE s.market=:market

An UPDATE statement should be used in a SQL PREPARE statement and executed in a FOR loop.

    SQL PREPARE s2 FROM UPDATE mkt -
       SET sales=:mkt.sales WHERE s.market=:market
    FOR market
       DO
          SQL EXECUTE s2
          IF SQLCODE NE 0
          THEN BREAK
       DOEND

#### 10.58.5 SQL FETCH

The SQL FETCH command retrieves and processes data specified by a named SQL cursor. SQL FETCH assigns the retrieved data to OLAP objects. You use the SQL FETCH command in combination with other SQL commands to copy data from relational tables into analytic workspace objects as outlined in "Copying Relational Data into Analytic Workspace Objects".

##### Syntax

SQL FETCH cursor \[LOOP \[loopcount\]\] -    INTO :targets... \[THEN action-statements...\]

where:

- `targets` is one or more of the following:

  - `[MATCH]` `dimension|surrogate`
  - `APPEND [``position``] ``dimension`
  - `ASSIGN ``surrogate`
  - `variable ``| ``qualified data reference ``|`` relation ``| ``composite`

- `position` is one of the following:

  - `AFTER ``dimension-value`
  - `BEFORE ``dimension-value`
  - `FIRST`
  - `LAST`

##### Parameters

cursor
The name of a declared and opened cursor.

LOOP
Specifies that Oracle OLAP should implicitly loop over the rows obtained from a relational table. For each row, Oracle OLAP copies the data in individual fields to objects specified as target analytic workspace objects. When you include a LOOP clause, SQL FETCH continues processing rows until it reaches the end of the active set specified by the cursor, or an error occurs, or loopcount is satisfied. In most cases, use the LOOP clause to improve the performance of SQL FETCH.

When you do not specify a LOOP clause and the cursor contains multiple rows in its active set, you must code the SQL FETCH statement within a WHILE loop. This loop must be based on the value of the SQLCODE option, which returns a nonzero value to indicate the end of the data or an error.

loopcount
Optional `INTEGER` argument to the LOOP keyword. Loopcount controls how SQL FETCH loops over the rows from a relational table. Loopcount can be a literal value, an OLAP DML variable, or `NA`. When loopcount is less than or equal to zero, no looping occurs and no data is fetched.

When you specify a LOOP clause without a value for loopcount, SQL FETCH continues reading rows and copying their contents to target analytic workspace objects until there are no more rows or an error occurs. Internally, each row is processed until SQLCODE is nonzero.

When you specify a literal value for loopcount, SQL FETCH processes the number of rows specified by loopcount or until SQLCODE is nonzero.

When you specify a variable for loopcount, it must be in the form of an OLAP DML variable (preceded by a colon). This variable acts as both an input and an output variable. The initial value of loopcount specifies the number of rows that SQL FETCH attempts to process. Upon completion of the SQL FETCH, loopcount contains the number of rows actually processed.

When you specify `NA` for loopcount, SQL FETCH processes rows until SQLCODE is nonzero. However, upon completion of the SQL FETCH, loopcount contains the number of rows actually processed.

targets
Identifies the analytic workspace objects in which you want to store data that is retrieved from a relational table. This list of target analytic workspace objects must correspond in number and data type with the list of table columns specified in the select-statement argument of the SQL DECLARE CURSOR command that declared cursor. A target can be a variable, a qualified data reference, a relation, a dimension, a composite, or a conjoint.

**Note:**

The order in which you specify the target analytic workspace objects affects dimension status. For each dimension value, Oracle OLAP temporarily limits the status of the dimension to the fetched value. Values are assigned to subsequent analytic workspace objects according to this temporary status. See "Conjoints as Target Analytic Workspace Objects" and "Composites as Target Analytic Workspace Objects".

A target must be preceded by a colon. When the target is a dimension, it can include the MATCH and APPEND keywords to specify dimension handling; in this case, the colon precedes the keywords.

\[MATCH\] {dimension\|surrogate}
(Default) Oracle OLAP does not perform dimension maintenance on the target dimension or surrogate. It uses the incoming values to align data that is being fetched into dimensioned objects. When a value from the relational database does not match any value in the dimension or surrogate, an error is signaled.

APPEND \[position\] dimension
Oracle OLAP performs dimension maintenance on the target dimension, adding new values to the dimension. It uses both old and new dimension values to align data being fetched into dimensioned objects. By default, new values are added to the end of a dimension or surrogate.

position is one of the following:

- `AFTER ``dimension-value`

  Any new values are added after dimension-value in the status list.

- `BEFORE ``dimension-value`

  Any new values are added immediately before dimension-value in the status list.

- `FIRST`

  Any new values are added to the beginning of the status list.

- `LAST`

  Any new values are added to the end of the status list.

The position can also be used to control how dimension values are processed in action statements.

ASSIGN surrogate
Assigns the values to the specified surrogate.

THEN action-statements...
Specifies any number of action-statements to be performed each time a row of data is fetched and assigned to target analytic workspace objects. An action-statement can be one of the following:

`assignment-statement` IF statement SELECT-statement ACROSS statement: action-statement \<action-statement-group\>

Refer to the SQL IMPORT command for a complete description of the syntax of action-statements.

##### Usage Notes

Effect of Order SQL FETCH Targets on Dimension Status

For each dimension value, Oracle OLAP temporarily limits the status of the dimension to the fetched value. Values are assigned to subsequent analytic workspace objects according to this temporary status.

Conjoints as Target Analytic Workspace Objects

You can use a conjoint dimension as a target analytic workspace object, but you must ensure that you select the same number of columns from the relational table as there are simple base dimensions. When Oracle OLAP executes a SQL FETCH statement for a target that is a conjoint dimension, it uses the dimension order that was specified when the conjoint was defined.

Composites as Target Analytic Workspace Objects

You can specify analytic workspace objects for composites just as you would for dimensioned variables. For example, to fetch data into a variable `var1` dimensioned by `dim1` and `dim2`, you would specify the following list of target analytic workspace objects.

    :dim1 :dim2 :var1

To fetch data into a variable `var2` dimensioned by a composite whose dimensions are `dim1` and `dim2`, you would specify the following list of target analytic workspace objects.

    :dim1 :dim2 :var2

Null Values

A null value in SQL is equivalent to an `NA` value in Oracle OLAP, so null values fetched into target analytic workspace objects are given `NA` values. Because Oracle OLAP handles null values in this way, the SQL command does not support` INDICATOR` variables in the INTO clause of a SQL FETCH statement. When fetching null values into a dimension, however, Oracle OLAP discards the values for the entire row.

Working with Boolean Variables as Input and Target Objects

You can use Boolean variables as input and target analytic workspace objects for OLAP SQL commands. In OLAP DML input expressions, Oracle OLAP treats Boolean values as `INTEGER` values with a value of `1` (`TRUE`) or `0` (`FALSE`).

As target analytic workspace objects, Boolean variables can receive values from any numeric (or bit) column in a relational table.

Fetching Text Data into DATE Variables

When fetching text data into a DATE variable, the current setting of the DATEORDER option is used to interpret the value. For example, a text value of `12-08-96` could be interpreted as December 8, 1996, or August 12, 1996, depending on the setting of DATEORDER.

Untransferable Data Types

You cannot transfer data with the following data types: LONG RAW, ROWID, UROWID, BLOB, and BFILE.

##### Examples

The `get_products_hier` program copies the data from the dimension tables into the base dimensions of the `aw_products` concat dimension using `SQL FETCH` commands with the `APPEND` keyword. As the base dimensions of `aw_products` are populated, Oracle OLAP automatically populates `aw_products`, itself. As the `THEN` clause of the `SQL FETCH` statement executes, Oracle OLAP fetches data into the child-parent self-relation for `aw_products`. This program also populates the `aw_supplier_id` dimension and its relation.

Example 10-136 Fetching Data From Relational Tables -- A Simple SQL FETCH

he following program fragment shows the basic steps of declaring and opening a cursor, and fetching the data. Relational data from the `Prod_ID` and `Prod_Name` columns of the `Products` table are fetched into the `prod` dimension and `prod_label` variable. The variable `prod_label` is dimensioned by `prod`. Notice that the SQL FETCH statement in this example does not include a LOOP clause; it therefore retrieves a single row of data each time it is called.

    VARIABLE set_price SHORT
    set_price = 20
         ...
    SQL DECLARE highprice CURSOR FOR SELECT Prod_ID, Prod_Name -
       FROM Products WHERE suggested_price > :set_price
    SQL OPEN highprice
    WHILE SQLCODE EQ 0
         SQL FETCH highprice INTO :prod, :prod_label

Example 10-137 Fetching Data From Relational Tables with a THEN Clause

The following program fragment shows the SQL FETCH statement from the previous example with the addition of the LOOP keyword and a THEN clause. Because of the LOOP keyword, this SQL FETCH statement does not have to run within a WHILE loop. The action statement following the THEN keyword copies any product names stored in `prod_label` that start with the letter `A` into a multiline text variable called `a_product`.

    SQL FETCH highprice LOOP INTO :prod, :prod_label -
       THEN IF UPCASE(EXTCHARS(prod_label, 1, 1)) EQ 'a' -
          THEN a_product = JOINLINES(a_product prod_label)

Example 10-138 Populating with Relational Data While Maintaining a Conjoint Dimension

In this example, a conjoint dimension (named `mpt`) is used as a target analytic workspace object. To populate a conjoint dimension, you must select values from the relational database for each of its base dimensions. Here, the three base dimensions are `market`, `product`, and `time`. Therefore, the` SELECT` statement specifies the three corresponding columns (`Mktcode`, `Prdcode`, and `Percode`). The program assumes that the `market`, `product`, and `time` dimensions are already populated with up-to-date values; Oracle OLAP does not update the base dimensions unless you explicitly specify them as target analytic workspace objects.

    DEFINE mpt DIMENSION <market product time>
    DEFINE sql.mpt PROGRAM
    PROGRAM
       ...
    SQL DECLARE c1 CURSOR FOR -
       SELECT Mktcode, Prdcode, Percode FROM Sqldba.Data
    IF SQLCODE NE 0
       THEN SIGNAL sqlerrm
    SQL OPEN c1
    SQL FETCH c1 LOOP INTO :append mpt
    SQL CLOSE c1
       ...
    END

Example 10-139 Populating Data While Maintaining Base and Conjoint Dimensions

To retrieve current values for the base and conjoint dimensions, or to retrieve the values for the first time, you can fetch the values for the base dimensions immediately before you fetch the values for the conjoint dimension. In the following example, the SQL DECLARE CURSOR and SQL FETCH commands have been edited to fetch both base and conjoint dimension values. Notice that the number of columns selected from the relational table must match the number of base dimensions fetched. There are six column specifications in the SELECT statement. The first three match the three base dimensions, and the last three match the conjoint dimension itself.

    SQL DECLARE c1 CURSOR FOR -
       SELECT Mktcode, Prdcode, Percode, Mktcode,  -
          Prdcode, Percode FROM Sqldba.Data
       ...
      SQL FETCH c1 LOOP INTO :APPEND market, :APPEND product, -
       :APPEND time, :APPEND mpt

Example 10-140 Populating Variables with Relational Table Data while Maintaining Dimensions

In the next example, variable `dollars.mpt` is dimensioned by the conjoint `mpt`, and its values are populated in the same SQL FETCH statement with the dimension values. The SQL DECLARE CURSOR and SQL FETCH commands have been edited again with the new column and target analytic workspace object added.

    DEFINE dollars.mpt DECIMAL <mpt>
    SQL DECLARE c1 CURSOR FOR -
       SELECT Mktcode, Prdcode, Percode, Mktcode, Prdcode, -
          Percode, Dollars FROM Sqldba.Data
       ...
    SQL FETCH c1 LOOP INTO :APPEND market, :APPEND product, -
       :APPEND time, :APPEND mpt, :DOLLARS.mpt

Example 10-141 Fetching Data into a Concat Dimension

Assume that a relational table has four columns of product data and that you decide to create a Product hierarchy with four levels in your analytic workspace to hold this data. The levels in the hierarchy (`prod_id`, `prod_subcategory`, `prod_category`, and `products_all`) map to columns in the `products` tables. The lowest level of the hierarchy is `prod_id` and the highest level is `products_all`. There is also a column with supplier information in the table.

To hold the data in the analytic workspace you define a dimension was defined for each level of the Product hierarchy, a concat dimension for the hierarchy itself, and a child-parent relation between the values in the hierarchy. You also define a dimension for the supplier data and a relation that holds the relationship between suppliers and products with the following definitions.

    DEFINE aw_prod_id DIMENSION NUMBER (6)
    DEFINE aw_prod_subcategory DIMENSION TEXT
    DEFINE aw_prod_category DIMENSION TEXT
    DEFINE aw_products_all DIMENSION TEXT
    DEFINE aw_products DIMENSION CONCAT (aw_products_all -
                                      aw_prod_category -
                                      aw_prod_subcategory -
                                      aw_prod_id)
    DEFINE aw_products.parents RELATION aw_products <aw_products>
    DEFINE aw_supplier_id DIMENSION NUMBER (6)
    DEFINE aw_prod_id.aw_supplier_id RELATION aw_supplier_id <aw_prod_id>

Assume that you write a program named `get_products_hier` that consists of the following code.

    ' get_products_hier Program
    ALLSTAT
    " Fetch values into the products hierarchy
    SQL DECLARE grabprods CURSOR FOR SELECT prod_total, -
                                            prod_category, -
                                            prod_subcategory, -
                                            prod_id -
                                       FROM sh.products
    SQL OPEN grabprods
    SQL IMPORT grabprods INTO :APPEND aw_products_all -
                                  :APPEND aw_prod_category -
                                  :APPEND aw_prod_subcategory -
                                  :APPEND aw_prod_id

    SQL CLOSE grabprods
    SQL CLEANUP
    " Update the analytic workspace and make the updates permanent
    UPDATE
    COMMIT
    " Fetch values into supplier_id
    SQL DECLARE grabsupid CURSOR FOR SELECT supplier_id -
                                     FROM sh.products
    SQL OPEN grabsupid
    SQL IMPORT grabsupid INTO :APPEND aw_supplier_id
    SQL CLOSE grabsupid
    SQL CLEANUP
    " Update the analytic workspace and make the updates permanent
    UPDATE
    COMMIT

    " Populate self-relation for concat dimension
    " and relation between aw_prod_id and aw_supplier_id
    SQL DECLARE makerels CURSOR FOR SELECT prod_total, -
                                           prod_category, -
                                           prod_subcategory, -
                                           prod_id, -
                                           supplier_id -
                                     FROM sh.products
    SQL OPEN makerels
    SQL FETCH makerels LOOP INTO :MATCH aw_products_all -
                                 :MATCH aw_prod_category -
                                 :MATCH aw_prod_subcategory -
                                 :MATCH aw_prod_id -
                                 :MATCH aw_supplier_id -
                THEN aw_products.parents(aw_products aw_prod_id) -
                    = aw_products(aw_prod_subcategory aw_prod_subcategory) -
                aw_products.parents(aw_products aw_prod_subcategory) -
                   = aw_products(aw_prod_category aw_prod_category) -
                aw_products.parents(aw_products aw_prod_category) -
                   = aw_products(aw_products_all aw_products_all) -
                aw_prod_id.aw_supplier_id = aw_supplier_id
    SQL CLOSE makerels
    SQL CLEANUP
    " Update the analytic workspace and make the updates permanent
    UPDATE
    COMMIT

#### 10.58.6 SQL IMPORT

The SQL IMPORT command retrieves and processes data specified by an explicit SQL cursor. SQL IMPORT assigns the retrieved data to OLAP objects. You use the SQL IMPORT command in combination with other SQL commands to copy data from relational tables into analytic workspace objects as outlined in "Copying Relational Data into Analytic Workspace Objects". SQL IMPORT is particularly effective in copying fact data from relational tables into analytic workspace variables.

**Note:**

You cannot transfer data with the following data types: LONG, BLOB, and BFILE.

##### Syntax

SQL IMPORT cursor \[:var-num-of-rows \|num-of-rows\[:var-num-of-processed-rows\]\]-        INTO :targets... \[THEN action-statements...\]

where:

- `targets` is one or more of the following:

  - `MATCH | MATCHSKIPERR [``position``] {``dimension ``| ``surrogate ``| ``valueset ``| ``relation``}`
  - `APPEND` `dimension`
  - `ASSIGN` `surrogate`
  - `variable ``| ``relation` `|` `qualified data reference`
  -

- `action-statements` is one of the following:

  - `assignment-statement`
  - `IF-statement`
  - `SELECT-statement`
  - `ACROSS-statement``: ``action-statement`
  - `<``action-statement-group``>`

##### Parameters

cursor
The name of a declared cursor.

var-num-of-rows
The name of a variable that specifies the number of rows that you want SQL IMPORT to attempt to import.

num-of-rows
A numeric constant that specifies the number of rows that you want SQL IMPORT to attempt to import.

var-num-of-processed-rows
When you include the MATCHSKIPERR keyword in the targets parameter, the name of a variable that specifies the actual number of rows that you want SQL IMPORT to import into analytic workspace objects.

targets
Identifies the analytic workspace objects in which you want to store data that is retrieved from a relational table. This list of target analytic workspace objects must correspond in number and data type with the list of table columns specified in the select-statement argument of the SQL DECLARE CURSOR command that declared cursor. A target can be a variable, a qualified data reference, a relation, a dimension, or a composite.

**Note:**

The order in which you specify the analytic workspace objects affects dimension status. For each dimension value, Oracle OLAP temporarily limits the status of the dimension to the fetched value. Values are assigned to subsequent analytic workspace objects according to this temporary status.

MATCH
(Default) Oracle OLAP does not copy values from the corresponding relational table column into the target dimension or surrogate. It only uses the values to align data that is being fetched into dimensioned objects. When a value from the relational database does not match any value in the dimension, an error is signaled.

MATCHSKIPERR
Oracle OLAP does not copy values from the corresponding relational table column into the target dimension or surrogate. It only uses the values to align data that is being fetched into dimensioned objects. When a value from the relational database does not match any value in the dimension, the value is ignored and processing continues without signaling an error.

position
The one-based logical position of the value.

APPEND
Oracle OLAP performs dimension maintenance on the target dimension, adding new values from the corresponding relational table column to the dimension. It uses both old and new dimension values to align data being fetched into dimensioned objects. New values are added to the end of a dimension.

ASSIGN
Oracle OLAP assigns the corresponding relational value to the specified surrogate.

dimension
The name of the analytic workspace dimension.

surrogate
The name of an analytic workspace surrogate.

valueset
The name of the analytic valueset.

relation
The name of the analytic workspace relation.

variable
The name of a variable.

qualified_data_reference
A QDR is a qualifier that limits one or more of the dimensions of a variable or a relation to a single value. Oracle OLAP evaluates QDRs in a SQL IMPORT statement, as follows:

- When the QDR includes an expression, the expression is evaluated only once before the data is retrieved. In other words, the expression is, in essence, a constant.

- When the QDR is specified as a relation name, the values of the QDR vary depending on the status of the dimensions of that relation.

THEN action-statements...
Specifies any number of action-statements to be performed each time a row of data is imported and assigned to analytic workspace objects. Action statements may contain simple assignment statements, conditional assignment statements, and assignments across dimensions.

Action statements allow you to examine and manipulate the fetched data on a row-by-row basis. For example, you may want to specify temporary objects as analytic workspace objects and only update your permanent objects once you have performed certain actions on the row of fetched data. However, action statements do not have to reference the imported data. For example, one of your action statements might be an assignment statement that executes a user-defined function (that is, a program) that performs complex processing and then simply increments a counter.

A THEN clause can improve SQL loading performance by eliminating the need for postprocessing upon completion of a SQL IMPORT.

**Note:**

The syntax of an action statement within SQL IMPORT is essentially the same as the syntax of an action statement within FILEREAD. Exceptions are in the syntax of an assignment statement and the use of the VALUE keyword. In SQL IMPORT action statements, assignments must be explicit; they must include a source, target, and equal sign. In FILEREAD action statements, assignments may be implicit and specify only the target. The VALUE keyword is supported in FILEREAD action statements, but not in SQL IMPORT action statements. When you have already specified action statements for use with FILEREAD, you can reuse the code with SQL IMPORT by simply adjusting the assignment statements and eliminating the VALUE keyword (if necessary). Most of the attributes listed in FILEREAD (except for the attributes that control dimension processing) are not meaningful for SQL loading and are ignored when executing within SQL IMPORT.

For best performance, within a THEN clause reference only the data within the imported row.

In your list of action statements, be sure to process dimensions before variables. Oracle OLAP processes each action statement from left to right for each row in the relational table. When an action statement performs dimension processing, the resulting status remains in effect for subsequent action statements. When you do not first specify action statements that limit a variable's dimensions, Oracle OLAP uses the first value in status to target a cell in the variable. Unless you specify an ACROSS phrase, Oracle OLAP assigns a single value from a row to a single cell in an Oracle OLAP variable. By default, Oracle OLAP does not loop over a variable's dimensions when assigning data to the variable.

assignment-statement
An assignment statement (SET) that assigns a value that is the result of an expression to an Oracle OLAP object.

IF-statement
An IF...THEN...ELSE command that performs some action depending on whether a Boolean expression is `TRUE` or `FALSE`.

SELECT-statement
A SQL SELECT statement lets you perform some action based on the value of an expression. A SELECT statement has the following form.

- `SELECT` `select-expression`
- `[WHEN` `expression1 action``]`
- `[WHEN` `expression2 action` `. . .]`
- `[ELSE` `action``]`

SELECT evaluates the SELECT expression and then sequentially compares the result with the WHEN expressions. When the first match is found, the associated action occurs. When no match is found, the ELSE action (if specified) occurs.

`ACROSS-statement`: action-statement
An ACROSS statement causes the following action statement to execute once for every value in status of the ACROSS dimension. When you want the looping to apply to multiple action statements, enclose the action statements in angle brackets. An ACROSS statement has the following form.

      ACROSS dimension \[limit\]:

       action-statement

In an ACROSS statement, limit temporarily change the status of dimension, if it is not in a FOR loop over dimension. The new status is in effect only for the duration of the SQL FETCH statement. The format of limit is as follows.

     \[ADD\|COMPLEMENT\|KEEP\|REMOVE\|TO\] limit-clause

To specify the temporary status, insert any of the LIMIT command keywords (the default is TO) along with an appropriate list of dimension values or related dimensions. You can use any valid limit clause (see the LIMIT command for further information). The following example limits `month` to the last six values, no matter what the current status of `month` is.

       ACROSS month last 6: units

\<action-statement-group\>
You can group several action statements by enclosing them in angle brackets. An action-statement-group has the following form.

   \<action-statement1 -

   \[action-statement2 . . .\]\>

A typical use for action statement groups is after an ACROSS statement. With the angle bracket syntax, you can cause multiple action statements to execute for every value in status of the ACROSS dimension.

##### Usage Notes

Effect of Order of SQL SELECT Targets on Dimension Status

For each dimension value, Oracle OLAP temporarily limits the status of the dimension to the fetched value. Values are assigned to subsequent analytic workspace objects according to this temporary status.

Working with Boolean Data Variables

You can use Boolean variables as input and target analytic workspace objects for OLAP SQL commands. In OLAP DML input expressions, Oracle OLAP treats Boolean values as `INTEGER` values with a value of `1` (TRUE) or `0` (FALSE).

As target analytic workspace objects, Boolean variables can receive values from any numeric (or bit) column in a relational table.

Importing Text Data into a DATE Variable

When importing text data into a DATE variable, the current setting of the DATEORDER option is used to interpret the value. For example, a text value of 12-08-96 could be interpreted as December 8, 1996, or August 12, 1996, depending on the setting of DATEORDER.

##### Examples

Example 10-142 Simple Import

The following program fragment shows the basic steps of declaring a cursor and importing the data. Values from the `Prod_ID` and `Prod_Name` columns of the `Products` relational table in the Sales -History (`sh`) database are fetched into the `prod_id` dimension and `prod_label` analytic workspace variable. The `prod_label` variable is dimensioned by `prod_id`.

    SQL DECLARE productcur CURSOR FOR SELECT Prod_ID, Prod_Name FROM sh.Products
    SQL OPEN productdur
    SQL IMPORT productcur INTO :prod_id, :prod_label
    SQL CLOSE productcur
    SQL CLEANUP

#### 10.58.7 SQL OPEN

The SQL OPEN command activates an explicitly-declared SQL cursor. When the cursor is opened, SQL examines any OLAP DML input expressions used in the definition of the specified cursor, determines the cursor's result set, and leaves the cursor in the open state for use by SQL FETCH or SQL IMPORT. The cursor is positioned before the first row of the result set.

You use the SQL OPEN command in combination with other SQL commands to copy data from relational tables into analytic workspace objects as outlined in "Copying Relational Data into Analytic Workspace Objects".

##### Syntax

SQL OPEN cursor

##### Parameters

cursor
The name of a cursor previously declared in the same program. You cannot use ampersand substitution.

##### Examples

Example 10-143 Opening a Cursor Using SQL OPEN

The following program fragment declares and opens a cursor named `geolabels`.

    SQL DECLARE geolabels CURSOR FOR -
       SELECT Store_ID, Store_Name, City FROM Stores
    IF SQLCODE NE 0
       THEN SIGNAL dclerror 'SQLERRM'
    SQL OPEN geolabels
    IF SQLCODE NE 0
       THEN SIGNAL operror 'SQLERRM'

#### 10.58.8 SQL PREPARE

Within a program, the SQL PREPARE command precompiles a SQL statement for later execution, in the same program using SQL EXECUTE. Typically, you use SQL PREPARE in programs to optimize the processing of SQL statements that are executed repeatedly, particularly those involving OLAP DML input expressions, such as INSERT, UPDATE, and DELETE.

##### Syntax

SQL PREPARE statement-name FROM sql-statement \[insert-options\]

##### Parameters

statement-name
A name that you assign to the executable code produced from sql-statement. You can redefine statement-name just by issuing another SQL PREPARE statement.

sql-statement
The SQL statement that you want to precompile for more efficient execution. It cannot contain ampersand substitution or variables that are undefined when the program is compiled.

insert-options
The following options are optional when sql-statement is an `INSERT` statement:

`DIRECT=YES|NO` specifies if the insert is a direct-path `INSERT`. This option must be the first option specified right aver the values phrase of the `INSERT` statement.

Setting this option to `YES` specifies that the insert is a direct-path `INSERT`. Direct-path `INSERT` enhances performance during `INSERT` operations and is similar to the functionality of Oracle's direct-path loader utility, SQL\*Loader. 

The default value is `NO` which specifies a normal `INSERT`.

`NOLOG=YES|NO` specifies if logging occurs. Setting this option to `YES` specifies that the redo information is not recorded in the redo log files which makes load-time faster. The default value is `NO` which specifies logging mode.

`PARTITION=``(sub)partition-name` specifies that only the segments related to the named partition or subpartition are locked. When you specify this option, another session can insert data to unrelated segments in the same table. When you do not specify this option (the default), other sessions cannot insert data into the same table.

##### Usage Notes

Using Direct-Path INSERT

When performing a direct-path `INSERT`, data is written directly into data files, bypassing the buffer cache, free space in the existing data is not reused, and the inserted data is appended after existing data in the table.

Restrictions When Using Direct-Path INSERT

Direct-path `INSERT` is subject to several restrictions. When executing a direct-path `INSERT` using the OLAP DML, transactions in the session issuing the direct-path `INSERT` must be committed for the `INSERT` to execute successfully. (You can use the SQL or OLAP DML COMMIT to commit transactions.)

Additionally, the general restrictions that apply to using direct-path `INSERT` in SQL apply to preparing a direct-path`INSERT` using OLAP DML PREPARE statements:

- The target table cannot be index organized or clustered.

- The target table cannot contain object type or LOB columns.

- The target table cannot have any triggers or referential integrity constraints defined on it.

For more information on restrictions when using a direct-path INSERT, see the discussion of the `INSERT` statement in Oracle Database SQL Language Reference.

Data Type Conversions During Direct-Path Insertion

The following table shows the automatic data type conversion performed during direct-path insertion:

Table 10-11 Automatic Data Type Conversion During Direct-Path Insertion

| Oracle RDBMS           | Oracle OLAP DML        |
|:-----------------------|:-----------------------|
| CHAR(n), VARCHAR(n)    | TEXT                   |
| LONG                   | TEXT with WIDE option  |
| CHAR(8), VARCHAR(8)    | ID                     |
| DATE                   | DATE                   |
| NUMBER(x,x)            | DECIMAL (SHORTDECIMAL) |
| INTEGER (or NUMBER(38) | INTEGER (SHORTINTEGER) |
| NUMBER(1)              | BOOLEAN                |

Inserting OLAP Text Data into a Column with a DATE Data Type

When inserting text data from Oracle OLAP into a column with a DATE data type, you must use the default date format of `DD` `MMM` `YY`. You can use slashes (`/`), hyphens (`-`), or spaces as separators. When the data is in a different format, you can use the Oracle `TO_DATE` function in a SQL `INSERT` statement.

Inserting Large Text Values into a CLOB or NCLOB Column

To insert more than 2K bytes of text data from an analytic workspace into a CLOB or NCLOB column, use the WIDE keyword before the name of the OLAP DML input expression. When the data type of the OLAP DML input expression is `TEXT`, then the target data type is CLOB. When the data type of the input expression is NTEXT, then the target data type is NCLOB.

The following is the syntax of an OLAP DML input expression with the WIDE keyword. See Example 10-146 for an example.

    :WIDE input-expression

See Example 10-146 for an example.

Note that the target table must conform to these guidelines:

- Any number and combination of CLOB and NCLOB columns

- No LONG columns

The RDBMS imposes some restrictions on large data types. Oracle OLAP does not signal an error when you violate these restrictions. However, you might get unexpected results. Refer to the Oracle Application Developer's Guide for restrictions on large data types.

Calculating the Number of Characters

You can calculate the number of characters that are sent to a database table from an Oracle OLAP variable by using the following formula.

    NUMCHARS(variable) + 2 * (NUMLINES(variable) - 1)

This formula counts the extra carriage return and line feed characters that Oracle OLAP inserts between lines when passing the text to the database.

##### Examples

Example 10-144 Preparing a FOR Loop

To automatically add all the sales people from the `salesperson` dimension to the relational table, you could write a program and put the SQL `INSERT` statement in a FOR loop.

    FOR salesperson
       SQL INSERT INTO Sales VALUES (:Salesperson, :Dollars) DIRECT=YES

When a statement includes OLAP DML input expressions and are executed repeatedly, such as in a FOR loop, you can make the statements more efficient by "preparing" the SQL statement first. The INSERT statement becomes part of a PREPARE statement.

    SQL PREPARE s1 FROM INSERT INTO Sales VALUES -
       (:Salesperson, :Dollars) DIRECT=YES
    FOR Salesperson
       DO
          SQL EXECUTE s1
          IF SQLCODE NE 0
          THEN BREAK
       DOEND

Example 10-145 Updating a Table

The next example shows a simple update of a table using data stored in an analytic workspace. The `market` dimension is limited to one value at a time in the FOR loop. The SQL phrase `WHERE S.Market=:market` specifies that the sales value in the row for that market is the value that is changed.

    FOR market
       SQL UPDATE Mkt SET Sales=:Mkt.Sales WHERE S.Market=:market

Like the INSERT statement in the previous example, an `UPDATE` statement should be used in a PREPARE statement and executed in an ACROSS statement or FOR loop.

    SQL PREPARE s2 FROM UPDATE mkt -
       SET Sales=:mkt.sales WHERE s.market=:market
    ACROSS market DO 'SQL EXECUTE s1'

Example 10-146 Using the WIDE Keyword

In both of the following statements, `WIDE` indicates that the target value is `CLOB` when `var1` is `TEXT`, or `NCLOB` when `var1` is `NTEXT`.

    SQL INSERT INTO CLOB_TEST values (:dim1 :WIDE var1)
    SQL UPDATE CLOB_TEXT SET clob_col = :WIDE var1 WHERE key = 1

#### 10.58.9 SQL PROCEDURE

The SQL PROCEDURE command executes procedures stored in the RDBMS.

**Note:**

You can also create SQL stored procedures using the OLAP DML. See:

- "Creating SQL Procedures using the OLAP DML"

- Example 10-147

##### Syntax

SQL PROCEDURE procedure-name (parameters)

where `parameters` is one or more of the following, separated by commas:

- `sql-parameter`
- `:``dml-parameter`

##### Parameters

procedure-name
The name of the SQL stored procedure.

sql-parameter
The name of a variable in the RDBMS.

:dml-parameter
An OLAP DML expressions such as an OLAP DML variable. See "Using OLAP DML Expressions in OLAP DML SQL Statements" for more information on using OLAP DML expressions in OLAP DML SQL statements.

##### Usage Notes

Creating SQL Procedures using the OLAP DML

To create a stored procedure using the OLAP DML, issue an OLAP DML SQL statement with a SQL `CREATE PROCEDURE` statement as its argument. The syntax for coding `CREATE PROCEDURE` as an argument within an OLAP DML SQL statement is slightly different than the syntax for coding `CREATE PROCEDURE` in SQL proper. When coded as an arguments to an OLAP DML statements, use a tilde (`~`) instead of a semicolon as a terminator, and two colons instead of one in an assignment statement. See Example 10-147.

Restrictions When Calling SQL Procedures using the OLAP DML

A stored procedure called using an OLAP DML SQL PROCEDURE statement cannot contain output variables or transactions.

##### Examples

Example 10-147 Creating a Stored Procedure

The following example shows the syntax for creating a procedure named `new_products`.

    SQL CREATE OR REPLACE PROCEDURE new_products -
       (id CHAR, name CHAR, cost NUMBER) AS -
          price NUMBER~ -
       BEGIN -
          price ::= cost * 2.5~ -
          INSERT INTO products -
             VALUES(id, name, price)~ -
       END~

Example 10-148 Executing a Stored Procedure

The following FOR loop executes a SQL stored procedure named `new_products` and inserts data stored in dimensions and variables into a relational table. In this example, `prod` is an Oracle OLAP dimension, and `labels.p` and `cost.p` are variables dimensioned by `prod`.

    FOR prod
       DO
          SQL PROCEDURE new_products(:prod, :labels.p, :cost.p)
          IF SQLCODE NE 0
             THEN BREAK
       DOEND

#### 10.58.10 SQL SELECT

The SQL SELECT command uses an implicit cursor to copy data from relational tables into analytic workspace objects. You use the SQL SELECT command to copy data from relational tables into analytic workspace objects using an implicit cursor. You can also use copy the data using an explicit cursor using the OLAP DML commands outlined in "Copying Relational Data into Analytic Workspace Objects".

##### Syntax

SQL SELECT expressions FROM tables -

    \[WHERE predicates\] \[GROUP BY expressions\] -     \[ORDER BY expressions\] \[HAVING predicates\] -     INTO :targets... \[THEN action-statements...\]

where `targets` is one or more of the following:

- `[MATCH] ``dimension``|``surrogate`
- `APPEND [``position``] ``dimension`
- `ASSIGN ``surrogate`
- `variable``|``qualified data reference``|``relation``|``composite`

##### Parameters

SELECT expressions FROM tables-
 \[WHERE predicates\] \[GROUP BY expressions\] -
\[ORDER BY expressions\] \[HAVING predicates\]
A SQL SELECT statement that identifies the data you want to associate with the cursor. For the syntax of an SQL SELECT statement, refer to Oracle Database SQL Language Reference.

targets
Identifies the analytic workspace objects in which you want to store data that is retrieved from a relational table. This list of target analytic workspace objects must correspond in number and data type with the list of table columns specified in the SELECT statement. A target can be a variable, a qualified data reference, a relation, a dimension, or a composite.

**Note:**

The order in which you specify the analytic workspace objects affects dimension status. For each dimension value, Oracle OLAP temporarily limits the status of the dimension to the fetched value. Values are assigned to subsequent analytic workspace objects according to this temporary status. See "Conjoints as Target Analytic Workspace Objects" and "Composites as Target Analytic Workspace Objects".

A target must be preceded by a colon. When the target is a dimension, it can include the MATCH and APPEND keywords to specify dimension handling; in this case, the colon precedes the keywords.

**Tip:**

Because both OLAP DML syntax and SQL WHERE clauses allow you to use AND and OR, construct the targets clause clearly so that Oracle OLAP can identify the end of an OLAP DML input expression.

\[MATCH\] {dimension\|surrogate}
(Default) Oracle OLAP does not perform dimension maintenance on the target dimension or surrogate. It uses the incoming values to align data that is being fetched into dimensioned objects. When a value from the relational database does not match any value in the dimension or surrogate, an error is signaled.

APPEND \[position\] dimension
Oracle OLAP performs dimension maintenance on the target dimension, adding new values to the dimension. It uses both old and new dimension values to align data being fetched into dimensioned objects. By default, new values are added to the end of a dimension or surrogate. The position can also be used to control how dimension values are processed in action statements.

ASSIGN surrogate
Assigns the values to the specified surrogate.

THEN action-statements
You may optionally include a THEN clause to specify any number of action-statements to be performed each time a row of data is fetched and assigned to analytic workspace objects. An action-statement can be one of the following:

- `assignment-statement`
- `IF-statement`
- `SELECT-statement`
- `ACROSS-statement``action-statement`
- `<``action-statement-group``>`

Refer to the SQL IMPORT command for a complete description of the syntax of action-statement.

##### Usage Notes

General Restrictions that APPLY to SQL SELECT

An SQL SELECT statement cannot contain ampersand substitution.

Optimizing Copies

When copying values from relational tables into a multidimensional input variable, list the columns that correspond to the dimensions in an ORDER BY clause in the select-statement argument of the SQL SELECT statement, with the slowest-varying dimension first which optimizes performance.

##### Examples

Example 10-149 Simple select

For example, assume that there is a relational table named `sales` with the following description.

    PROD_ID                     NOT NULL NUMBER(6)
    CUST_ID                     NOT NULL NUMBER
    TIME_ID                     NOT NULL DATE
    CHANNEL_ID                  NOT NULL CHAR(1)
    PROMO_ID                    NOT NULL NUMBER(6)
    QUANTITY_SOLD               NOT NULL NUMBER(3)
    AMOUNT_SOLD                 NOT NULL NUMBER(10,2)

Assume also that your analytic workspace contains the following definitions for corresponding analytic workspace objects.

    DEFINE aw_prod_id DIMENSION NUMBER (6)
    DEFINE aw_cust_id DIMENSION NUMBER (6)
    DEFINE aw_date DIMENSION TEXT
    DEFINE aw_channel_id DIMENSION TEXT
    DEFINE aw_promo_id DIMENSION NUMBER (6)
    DEFINE aw_sales_dims COMPOSITE <aw_prod_id aw_cust_id -
         aw_channel_id aw_promo_id>
    DEFINE aw_sales_quantity_sold VARIABLE NUMBER (3) <aw_date aw_sales_dims -
         <aw_prod_id aw_cust_id aw_date aw_channel_id aw_promo_id>>
    DEFINE aw_sales_amount_sold VARIABLE NUMBER (10,2) <aw_date aw_sales_dims -
         <aw_prod_id aw_cust_id aw_date aw_channel_id aw_promo_id>>

To copy the data for product 415 from the `sales` table into the analytic workspace objects, you execute the following statement in the OLAP worksheet.

    SQL SELECT prod_id cust_id time_id channel_id promo_id quantity_sold -

    amount_sold WHERE prod_id = 415 -
    INTO :aw_prod_id, :aw_cust_id, :aw_date,  -
    :aw_channel_id, :aw_promo_id, :aw_sales_quantity_sold, :aw_sales_amount_sold

### 10.59 STATUS

The STATUS program sends to the current outfile the status of one or more dimensions, dimension surrogates, or valuesets, or the status of all dimensions in an analytic workspace.

When you specify one or more dimension, dimension surrogate, or valueset names, Oracle OLAP produces the status of only those objects. When you use the AW keyword and specify the name of an attached analytic workspace, Oracle OLAP produces the status of every dimension in that analytic workspace. When you do not specify any argument, STATUS produces the current status of all the dimensions (not dimension surrogates or valuesets) in the current analytic workspace. However, STATUS does not display the status of the NAME dimension unless you specify `STATUS` `NAME`.

**Tip:**

Use STATLIST rather than STATUS when you want to control the width or placement of the display.

#### Return Value

TEXT

#### Syntax

STATUS name... \| AW \[workspace-name\]

#### Parameters

name
The name of a dimension or valueset in the analytic workspace. You can also specify the name of a dimensioned analytic workspace object, such as a variable, formula, relation, or named composite. In this case, the status of each dimension of name is produced, unless the dimension is included in an unnamed composite.

AW \[workspace-name\]
Specifies that STATUS should produce the status of every dimension in workspace-name; workspace-name is the name of an analytic workspace.

#### Usage Notes

STATUS Output

When all values of a dimension are in the current status or in a valueset, in the original order, STATUS displays `ALL`. STATUS shortens any series of three or more values in their original order to `value-1` `TO` `value-n`. In the case of the dimension NAME, however, STATUS does not shorten a series of three or more values.

Status When an Object Has No Values

When a dimension, dimension surrogate, or valueset has no values (for example, a recently defined object for which you have not yet supplied values), STATUS produces `NULL` for that dimension, dimension surrogate, or valueset. When you are in an analytic workspace in which no objects have been defined, STATUS produces the message, `There` `are` `no` `dimensions` `in` `your` `current` `analytic` `workspace`.

#### Examples

Example 10-150 Discovering the Current Status of Certain Dimensions

Use STATUS to produce the current status of the dimensions `month` and `district`.

The following statement

    STATUS month district

produces this output.

    The current status of MONTH is:
    Jan95 TO Dec96
    The current status of DISTRICT is:
    Boston, Chicago, Denver

Example 10-151 Discovering the Status of the Dimensions of a Variable

Use STATUS to produce the current status of all the dimensions of the variable `sales`.

The following statement

    STATUS sales

produces this output.

    The current status of MONTH is:
    Jan95 TO Dec96
    The current status of PRODUCT is:
    ALL
    The current status of DISTRICT is:
    Boston, Chicago, Denver

### 10.60 STDHDR

The STDHDR program generates the standard Oracle OLAP heading at the top of every page of report output.

The standard running page heading consists of two lines. The first line includes the date and time on the left and the page number on the right. The second line is blank.

The heading output is sent to the current outfile.

#### Syntax

STDHDR

#### Usage Notes

Setting LSIZE

LSIZE must be set to a value of at least `29` before you use STDHDR. Otherwise the heading does not look right. A value less than `26` produces an error. The default for LSIZE is `80`.

Creating a Custom Heading

When PAGING is set to `YES`, Oracle OLAP automatically inserts the standard heading at the top of each page of output. To get a different heading you must write a program that produces the heading and set the PAGEPRG option to the name of that program. To return to the standard heading, set PAGEPRG to `'STDHDR'`. (See the [PAGEPRG](olap-dml-options.md) option for more information.)

Using STDHDR in a Heading Program

When you use PAGEPRG to specify a heading program, you can still use the standard heading in your custom heading by executing STDHDR as part of your program. Generally, you place STDHDR before the statements that produce your customized heading. See Example 10-152.

The STDHDR Program

The STDHDR program uses the HEADING and CONVERT commands, as follows.

    HEADING L W 8 <CONVERT(TODAY, TEXT,'<DD><MTXTL><YY>') TOD> -
            R W LSIZE-25 'Page ' L W 6 D 0 PAGENUM
    BLANK

#### Examples

Example 10-152 Creating a Custom Heading for a Report

Suppose you would like each page of your report to include the standard header and also the customized title "Annual Sales Report." To accomplish this, define a small PAGEPRG program called report.head.

    DEFINE report.head PROGRAM
    PROGRAM
    CALL STDHDR
    HEADING WIDTH LSIZE CENTER 'Annual Sales Report'
    BLANK
    END

In your report program, set PAGING to `YES`, and specify the preceding program to execute after every page break by setting the PAGEPRG option to `'REPORT.HEAD'` (see the [PAGEPRG](olap-dml-options.md) option for further information). When you run the report, each page contains the following combination of the standard heading and your custom heading.

    18Jan97  15:05:16                                   PAGE 1
     
                       Annual Sales Report

### 10.61 SWITCH command

The SWITCH command provides a multipath branch in a program. The specific path taken during program execution depends on the value of the control expression that is specified with SWITCH. You can use a SWITCH statement only within programs.

**Note:**

Do not confuse the use of a single SWITCH command with the use of SWTICH as a conditional operator in an expression. See "[SWITCH Expressions](data-types-operators-and-expressions.md)".

#### Syntax

SWITCH control-expression    DO       CASE case-expression1:           statement 1.1            ...           statement 1.n            BREAK       CASE case-expression2:            statement 2.1            ...            statement 2.n            BREAK       \[DEFAULT:            statement n.1            ...            statement n.n            BREAK\]    DOEND

#### Parameters

control-expression
The control-expression argument determines the case label to which program control is transferred by the SWITCH statement. When the SWITCH statement is executed, control-expression is evaluated and compared with each of the CASE label expressions in the program. When a match is found, control is transferred to that case label. When no match is found, control transfers to the DEFAULT label (if present) or to the statement following the DOEND for SWITCH.

CASE case-expression1, CASE case-expression2, ...
The CASE labels whose expressions (case-expression1, case-expression2, ...) specify the different cases you want to handle. When control-expression matches case-expression, program control is transferred to that CASE label. The CASE label expressions are evaluated at the time the program is run, in the order they appear, until a match is found.

The DEFAULT label is optional. It identifies a special case to which control should be transferred when none of the case-expressions matches the control-expression. When you omit DEFAULT, and no match is found, control is transferred to the statement that follows the DOEND for SWITCH.

All the CASE labels (including DEFAULT) for a SWITCH statement must be included within a DO/DOEND bracket immediately following the SWITCH statement. Because case-expression is a label, it must be followed by a colon (:). The statements to be executed in a given case must follow the label. Normally, the last statement in a case should be BREAK, which transfers control from SWITCH to the statement that follows the DOEND for SWITCH.

When you omit BREAK (or RETURN, SIGNAL, and so on) at the end of a case, the program goes on to execute the statements for the next case as well. Normally, you do not want this to happen. However, when you plan to execute the same statements for two cases, you can use this to your advantage by placing both CASE labels before the statements.

#### Usage Notes

Control and Case Expressions

The SWITCH control-expression can have any data type, as can the case-expressions. The various case-expressions can have different data types. When you specify the name of a dimension (as a literal, non-quoted text expression) as the control-expression or case-expression, Oracle OLAP uses the first value in the dimension's current status list, not the dimension name, as it searches for a match. When the dimension has no values in the status list, Oracle OLAP uses the value `NA`. An `NA` control-expression matches the first `NA` case-expression.

Do Not Use Ampersand Substitution with SWITCH

Avoid using ampersand substitution in a SWITCH control-expression or in a CASE label case-expression. Ampersands produce unpredictable, and usually undesirable, results.

Multiple SWITCH Commands

You can include multiple SWITCH statements in a program. You can also nest SWITCH commands. When a program contains multiple SWITCH commands, each can have its own DEFAULT label, even when the SWITCH commands are nested.

Transferring Control

While BREAK is commonly used to transfer program control within a SWITCH statement, it is not the only such statement you can use. You can also use statements such as [CONTINUE](olap-dml-commands-a-g.md), [GOTO](olap-dml-commands-a-g.md), RETURN, and SIGNAL. Keep in mind that you can use CONTINUE only when the SWITCH statement is within a FOR or WHILE loop. See also the entries for these statements and for [DO ... DOEND](olap-dml-commands-a-g.md).

#### Examples

Example 10-153 Multipath Branching Using SWITCH in a Program

The following program lines produce one of several types of reports. Before the SWITCH statement, the program determines which type of report the user wants and places the value `Market` or `Finance` in the variable `userchoice`. The program switches to the case label that matches that name and produces the report. When the report finishes, the BREAK statement transfers control to the cleanup section after the DOEND.

    SWITCH userchoice
        DO
             CASE 'Market':
                ...
                BREAK
             CASE 'Finance':
                ...
                BREAK
             DEFAULT:
                ...
                BREAK
        DOEND
    cleanup:
    ...

### 10.62 TEMPSTAT

The TEMPSTAT command limits the dimension you are looping over, inside a FOR loop or inside a loop that is generated by a REPORT statement. Status is restored after the statement following TEMPSTAT. When a DO ... DOEND phrase follows TEMPSTAT, status is restored when the matched DOEND or a BREAK or GOTO statement is encountered. You can use TEMPSTAT only within programs.

#### Syntax

TEMPSTAT dimension...      statement block

#### Parameters

dimension(s)
One or more dimensions whose status you would like to temporarily change inside a FOR loop or an automatic loop that is generated by the REPORT statement.

statement block
One or more statements that change the status of the dimension. To execute multiple statements under the temporary status, enclose them between DO ... DOEND brackets.

#### Usage Notes

Nesting TEMPSTATE Statements

You can nest TEMPSTAT commands, one within another, and you can repeat the same dimension within the nested TEMPSTAT commands.

Placement of TEMPSTAT

When you want to be able to change the status of a dimension while REPORT is looping over it, you must place a TEMPSTAT statement inside that REPORT loop rather than before the REPORT statement. For example, suppose you have written a user-defined function called `monthly_sales`, which changes the status of `month`, and `monthly_sales` is part of a REPORT statement that is looping over `month`. In this case a TEMPSTAT statement must be inside the `monthly_sales` function in order for a status change to take place. (TEMPSTATE must be inside of monthly_sales even when the REPORT statement is given within TEMPSTAT DO/DOEND brackets within a FOR loop over MONTH.)

POP and POPLEVEL Commands

Within the DO/DOEND brackets of a TEMPSTAT statement block, you cannot use a POP statement to pop a dimension that is protected by TEMPSTAT on the block -- unless the matching PUSH statement is also within the block.

Similarly, within the DO/DOEND brackets of a TEMPSTAT statement block, you cannot use a POPLEVEL statement to pop a dimension that is protected by TEMPSTAT on the block -- unless one of two conditions is met: the matching PUSHLEVEL statement is also within the block, or the only pushes on the dimension since the PUSHLEVEL statement was given are also within the block.

Use Only LIMIT and CONTEXT Commands

Within the DO/DOEND brackets of a TEMPSTAT statement, the only way to change the status of a dimension within a loop over that dimension is with the LIMIT or CONTEXT APPLY commands. (See the LIMIT command and the [CONTEXT command](olap-dml-commands-a-g.md) for details.) You cannot change the status of the dimension using POP or POPLEVEL. You also cannot perform any operations that would add values to the dimension, because adding values also changes the status of the dimension to ALL. For example, MAINTAIN ADD, FILEREAD APPEND, and IMPORT (with new values in the EIF file) add values to a dimension.

#### Examples

TEMPSTAT in a FOR Loop

The following program excerpt uses a TEMPSTAT statement to limit the `market` dimension within the `FOR` `market` loop.

    FOR market
    DO
     TEMPSTAT market
      DO
       LIMIT market TO CHILDREN USING market.market
       REPORT market
      DOEND
    DOEND

### 10.63 TRACE

The TRACE command specifies whether or not information about the entry, exit, and execution of individual programs, models, and formulas is recorded in the current outfile during execution:

- For programs and models, it traces the entry, exit, and execution of individual lines of code and produces output similar to the output produced when the [PRGTRACE](olap-dml-options.md) or [MODTRACE](olap-dml-options.md) option is set to `YES`.

- For formulas, it outputs the name and dimension value on entry and the return value on exit.

#### Syntax

TRACE \[?\|{object-name\|\*} \[OFF\] \[begin-arguments\] \[end-arguments\] \[ TRACELINES \| NOTRACELINES\]\] where: begin-arguments requires the following syntax: IN \[ARGS \| NOARGS\] end-arguments requires the following syntax: OUT \[VALUE \| NOVALUE\]

#### Parameters

?
A ? (question mark) displays the current TRACE list, which includes the name of each program, model, and formula that will be traced when executed. In addition, if there is a global trace, TRACE ALL is listed. For each program, model, and formula, and for TRACE ALL, the list displays the current TRACE settings (the values of begin-arguments and end-arguments).

object_name
The unqualified name of the program, model, or formula that you want to trace. You can specify the name of a program, model, or formula even if it does not exist in an attached database. Without the OFF keyword, this argument turns on an object-specific trace, in which TRACE traces the execution of the named program, model, or formula whenever you run it. In order to change the TRACE settings of a program, model, or formula, you can turn on its object-specific trace several times. With the OFF keyword, this argument turns off the object-specific trace.

\*\[OFF\]
An\* (asterisk) is only used with programs and models:

- Without the OFF keyword, an \* (asterisk) adds TRACE ALL to the TRACE list and turns on a global trace. This means that TRACe traces the execution of every program and model that you run, including programs such as LISTNAMES that are part of express.db. If you have both an object-specific trace and a global trace specified, the settings for the object-specific trace take precedence when you run the given program or model.

- With the OFF keyword, an \* (asterisk), turns off the global trace by deleting all program names, model names, and TRACE ALL from the TRACE list, leaving the list empty.

ARGS
NOARGS
ARGS and NOARGS are used only with programs and formulas. These keywords indicate whether TRACE should display the values of arguments when entering a program or the dimension values of formulas. The default is ARGS.

VALUE
NOVALUE
VALUE and NOVALUE are used only with programs. These keywords indicate whether the return value of the program is displayed after executing its last line. If the program does not have a return value, no value is displayed. The default is VALUE.

TRACELINES
NOTRACELINES
TRACELINES and NOTRACELINES are used only with programs and models. These keywords indicate whether the program or model lines are printed. The default is TRACELINES.

#### Usage Notes

Nested Programs and Models

If you execute nested programs (in which one program calls another), and if you trace all the nested programs, TRACE will keep track of the nested levels. If one of the programs calls a model, you can also trace the model, and TRACE will keep track of the model within the stack of nested programs.

Changing TRACE Settings

You can change a TRACE setting for a program or model by executing a new TRACE command. If you only change one of the settings, the others remain set to the values they had before.

Tracing a Model

If a block of simultaneous equations in a model cannot be solved within a specified number of iterations, an error occurs. The value of the [MODERROR](olap-dml-options.md) option determines the action that TRACE takes in this event.

### 10.64 TRACKPRG

The TRACKPRG command tracks the performance cost of every program that runs while you have tracking turned on. To get meaningful information from TRACKPRG, your session must be the only one running in Oracle OLAP. Furthermore, the accuracy of the results of TRACKPRG decreases as more processes are started on the host computer.

You turn TRACKPRG on, run the programs you want to track, and use TRACKPRG again to obtain the results. Each time each program is executed, TRACKPRG stores its cost data as one entry in its tracking list. When you execute another program, a new entry is added to the list, which is maintained in Oracle OLAP memory (free storage).

A program or line of code is considered to have a high performance cost when it takes a long time to execute. Use TRACKPRG to identify programs that have relatively high costs and then use a MONITOR statement to identify the time-consuming lines within those programs. When you want, you can use both commands simultaneously.

#### Syntax

TRACKPRG {ON\|OFF\|file\|INIT}

where `file` has the following syntax:

- `FILE [APPEND] [``file-name`\]

#### Parameters

ON
Starts looking for programs to be run so it can gather their timing data in a tracking list. (Continues the current tracking process without interruption when tracking is already on, or resumes with a gap when tracking is off.)

OFF
Stops tracking programs and freezes any timing data currently in the tracking list which allows you to send the list to the current outfile or to a text file either immediately, or later in your session.

FILE
Specifies where to send the tracking list. TRACKPRG FILE has no effect on the tracking list, so you can send the same list repeatedly to different destinations.

APPEND
Specifies that Oracle OLAP adds the tracking list to the contents of the file indicated by file-name instead of replacing it.

file-name
A text expression to which Oracle OLAP sends the data. Unless the file is in the current directory, you must include the name of the directory object in the name of the file.

**Note:**

Directory objects are defined in the database, and they control access to directories and file in those directories. You can use a CDA statement to identify and specify a current directory object. Contact your Oracle DBA for access rights to a directory object where your database user name can read and write files.

When you omit file-name, Oracle OLAP sends the timing data currently in the tracking list to the current outfile

INIT
Discards the timing data in the current tracking list and releases the Oracle OLAP memory that was used for that list (useful when you want the memory for other purposes). Also, when tracking is on, resumes waiting for you to run programs so it can gather their data into a completely new tracking list.

#### Usage Notes

Single Execution

Each entry (that is, line) in the tracking list focuses on a single execution of a single program.

Depth of the Call

Each entry records the depth of the call, if any, to the current program; that is, how many program calls it has taken to get to the program reported on the current line. In TRACKPRG output, the depth of the call is indicated by the indentation of the program name. For each indented program, TRACKPRG also records the name of the program that called it at the end of the entry.

Types of Timing Data

In each entry, TRACKPRG records two types of timing data:

- Exclusive cost -- The time spent in this program, excluding the time spent on any programs that are called by this one.

- Inclusive cost -- The time spent in this program, including the time spent on any programs that are called by this one.

This gives you the option of generating a report on both types of cost.

Entry Sections

In TRACKPRG output, each entry (line) is divided into the following four sections:

- Program name, in character columns 1 through 38

- Exclusive time, in columns 39 through 49

- Inclusive time, in columns 50 through 60

- Name of calling program, in columns 61 through 77

Here is a sample of TRACKPRG output (for the MAIN program) with column numbers included for reference.

    1234567890123456789012345678901234567890123456789012345678901234567890
     
    MAIN                                  39.6198425 225.551453
     COMM                                  43.793808  185.93161 MAIN
      _C.SYS.INFO                         .112533569 .112533569 COMM
      _C.SYS.INFO                         .087173462 .087173462 COMM
      _C.MAIN                             61.414505  141.938095 COMM
       _C.CON                             66.7147064 80.5235901 _C.MAIN
        _C.SYS.DORETURN                   .032287598 .032287598 _C.CON

TRACKREPORT Program

When you want to use Oracle OLAP reporting capabilities to produce a report from the timing data in the text file that is created by TRACKPRG, you can use the TRACKREPORT program. It has the following syntax.

TRACKREPORT textfile-name

The textfile-name argument is the file name of the text file created by TRACKPRG from which you want to generate a report. TRACKREPORT uses a FILEREAD statement to read the data into an Oracle OLAP variable, and then it uses Oracle OLAP reporting capabilities to produce a report like the following sample.

                         Exclusive  Inclusive  Number of 
        Program name        cost       cost      calls   
    ____________________ __________ __________ __________
     
    COMM                 43.793808   185.93161          1
    MAIN                 39.6198425 225.551453          1
    _C.CON               66.7147064 80.5235901          1
    _C.ENV.PUTOPTS       1.15296936 1.15296936          1
    _C.ENV.XLATEIN       6.32765198 6.32765198          1
    _C.MAIN               61.414505 141.938095          1
    _C.SYS.DORETURN      .032287598 .032287598          1
    _C.SYS.INFO          .289932251 .289932251          3
    _C.SYS.NOF10         .038269043 .038269043          1
    _CONNECT              5.3609314 6.16748047          1
    _CONNNONE            .806549072 .806549072          1

When you want to further process the data from a TRACKPRG file, you can write your own program using the `TRACKREPORT` program as a model.

Excluded Subprograms

When you do not want separate performance data on all the subprograms called by the program you are timing, you can, within the overall program, turn tracking off before calling any subprograms you want to exclude and then turn it back on before calling any you want to include. You can do this repeatedly. Remember, however, that the time taken by any excluded subprograms is assigned to the total "exclusive" time for the overall program and to its "inclusive" time, because TRACKPRG has not individually tracked the excluded subprograms.

Using TRACKPRG with Very Small Programs

You might not be able to reproduce the results exactly for very small programs. When the CPU interrupts processing to do other tasks, that time is a greater percentage of the total execution time.

Unit of Measure for TRACKPRG

The MONITOR and TRACKPRG commands use milliseconds as the unit for recording execution time. The execution time does not include time spent on I/O and time spent waiting for the next statement.

#### Examples

Example 10-154 Collecting Timing Data USING TRCKPRG

In this example, timing data on the `mybjt` program and all the programs it calls is collected in a file called `mybjttim.dat`.

    TRACKPRG ON
    mybjt
    TRACKPRG OFF
    TRACKPRG FILE mybjttim.dat
    TRACKPRG INIT
    TRACKREPORT mybjttim.dat

Example 10-155 Using the INIT Keyword and TRACKREPORT

In this example, tracking is turned on to collect timing data about the execution of `prog1` and the data is sent to a file named `prog1.trk`. Then, the INIT keyword is used to discard the existing tracking list so the data for a second program can be collected and sent to a file. Throughout the procedure, tracking remains on. Finally, after tracking is turned off and the INIT keyword is used to release the memory that was used for the tracking list, the `TRACKREPORT` program is called to produce two reports generated from the data stored in the two files.

    TRACKPRG ON
    prog1
    TRACKPRG FILE prog1.trk
    TRACKPRG INIT
    prog2
    TRACKPRG FILE prog2.trk
    TRACKPRG OFF
    TRACKPRG INIT
    TRACKREPORT prog1.trk
    TRACKREPORT prog2.trk

### 10.65 TRAP

Within an OLAP DML program, the TRAP command causes program execution to branch to a label when an error occurs in a program or when the user interrupts the program. When execution branches to the trap label, that label is deactivated.

**See Also:**

"[Declarative Error](olap-dml-commands-a-g.md)" for a discussion of how Oracle OLAP handles declarative errors in programs and models

#### Syntax

TRAP {OFF\|ON errorlabel \[NOPRINT\|PRINT\]}

#### Parameters

OFF
Deactivates the trap label. Because only one trap label can be active at a time, you do not supply errorlabel when setting `TRAP` `OFF`. When you try to include a label with OFF, an error occurs.

**Note:**

When an error occurs in a program that contains a trap label, execution branches to the label and the trap is deactivated. You do not have to execute an explicit `TRAP` `OFF`  statement. Thus, an error occurring after execution has branched to the label does not cause execution to branch to the same label again.

ON errorlabel
Activates the trap label (errorlabel). When TRAP is active, any error in the program causes execution to branch to errorlabel.

errorlabel
The name of a label elsewhere in the program constructed following the "[Guidelines for Constructing a Label](olap-dml-commands-a-g.md)". Execution of the program branches to the line directly following the specified label.

**Note:**

Note that errorlabel, as specified in ON, must not be followed by a colon. However, the actual label elsewhere in the program must end with a colon.

When an actual trap label that corresponds to errorlabel does not exist elsewhere in the same program, execution stops with an error

NOPRINT
PRINT
Indicates whether to suppress output of the error message. NOPRINT suppresses the message. PRINT (default) means that the error message is sent to the current outfile before execution branches to the trap label. With the OFF keyword, NOPRINT and PRINT are meaningless and produce an error.

#### Examples

Example 10-156 Trapping a Program Error

The following program fragment uses a TRAP statement to direct control to a label where options and dimension status are set back to the values they had before the program was executed and an error is signaled.

    PUSH month DECIMALS LSIZE PAGESIZE
    TRAP ON haderror NOPRINT
    LIMIT month TO LAST 1
       ...
    POP month DECIMALS LSIZE PAGESIZE
    RETURN
     
    haderror:
    POP month DECIMALS LSIZE PAGESIZE
    SIGNAL ERRORNAME ERRORTEXT

Example 10-157 Producing a Program Error Message Immediately

To produce the error message immediately, use a TRAP statement in each nested program, but do not use the NOPRINT keyword. When an error occurs, an error message is produced immediately, and execution branches to the trap label.

At the trap label, perform whatever error-handling commands you want and restore the environment. Then execute a SIGNAL statement that includes the PRGERR keyword.

    SIGNAL PRGERR

When you use the PRGERR keyword in the SIGNAL statement, no error message is produced, and the name PRGERR is not stored in ERRORNAME. The SIGNAL  statement signals an error condition that is passed up to the program from which the current program was run. When the calling program contains a trap label, then execution branches to that label.

When each program in a chain of nested programs uses the TRAP and SIGNAL commands in this way, you can pass the error condition up through the entire chain. Each program has commands like these.

    TRAP ON error
       ...       "Body of program and normal exit commands
    RETURN
    error:
       ...       "Error-handling and exit commands
    SIGNAL PRGERR

Example 10-158 Producing a Program Error Message at the End of the Chain

To produce the error message at the end of a chain of nested programs, use a TRAP statement that includes the NOPRINT keyword. When an error occurs in a nested program, execution branches to the trap label, but the error message is suppressed.

At the trap label, perform whatever error-handling commands you want and restore the environment. Then execute the following SIGNAL statement.

    SIGNAL ERRORNAME ERRORTEXT

The preceding SIGNAL statement contains includes ERRORNAME and ERRORTEXT within it. The ERRORNAME option contains the name of the original error, and the ERRORTEXT option contains the error message for the original error. When the calling program contains a trap label, then execution branches to that label.Consequently, the SIGNAL statement passes the original error name and error text to the calling program.

When each program in a chain of nested programs uses the TRAP and SIGNAL commands in this way, the original error message is produced at the end of the chain. Each program has commands like the following.

    TRAP ON error NOPRINT
       ...       "Body of program and normal exit commands
    RETURN
    error:
       ...       "Error-handling and exit commands
    SIGNAL ERRORNAME ERRORTEXT

### 10.66 TRIGGER command

The TRIGGER command associates a previously-created program to an object and identifies the object event that automatically executes the program; or disassociates a trigger program from the object.

To assign a trigger program to an object, the object must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER statement to make it the current definition.

**See Also:**

"[Trigger Programs](olap-dml-programs.md)" and the [TRIGGER function](olap-dml-functions-l-z.md)

#### Syntax

TRIGGER {event-name \[program-name\] }... \| {DELETE event-name}... \| DELETE  ALL

where `event-name` is one of the following:

- `MAINTAIN`
- `DELETE`
- `PROPERTY`
- `ASSIGN`
- `BEFORE_UPDATE`
- `AFTER_UPDATE`

You can use the same keyword many times in a single TRIGGER statement; however, in this case, Oracle OLAP ignores all but the last occurrence of the keyword. See "Multiple Occurrences of the Same Keyword", for details.

#### Parameters

MAINTAIN
Specifies that the trigger for the program is a Maintain event. A Maintain event is the execution of the MAINTAIN statement. As outlined in [Table 8-19](olap-dml-functions-l-z.md), the Maintain event has several subevents that correspond to the major keywords of the MAINTAIN command. Exactly when a program triggered by a Maintain event is executed is dependent on the Maintain subevent that triggered the program and the object type for which the Maintain event is defined:.

- Programs triggered by Maintain Add and Maintain Merge events on dimensions and composites are executed after the entire MAINTAIN statement executes.

- Programs triggered by Maintain Add and Maintain Merge events on dimension surrogates are executed multiple times­—once after each value is added or merged.

- Programs triggered by other Maintain subevents are executed before the MAINTAIN statement is executed.

DELETE
Specifies that the trigger for the program is a Delete event. A Delete event is a DELETE statement for the object. Oracle OLAP executes the specified program immediately before a DELETE statement deletes the object.

PROPERTY
Specifies that Oracle OLAP executes the specified program in response to a Property event. A Property event is the execution of a PROPERTY statement to create, modify, or delete an object property. A program that is triggered by a Property event is executed before the statement that triggered it.

ASSIGN
Specifies that Oracle OLAP executes the specified program in response to an Assign event. An Assign event is executed when SET assigns values to variable, relation, worksheet object, or a formula. A program that is triggered by SET is executed each time Oracle OLAP assigns a value to the object for which the event was defined. Thus, a program triggered by an Assign event is often executed over and over again as the assignment statements loops through an object assigning values.

UPDATE
When the object has been acquired using ACQUIRE in an analytic workspace that is attached in multiwriter mode, specifies that Oracle OLAP executes the specified program immediately after the object is updated.

**Note:**

To specify processing when the entire analytic workspace is updated, create a TRIGGER_AFTER_UPDATE or TRIGGER_BEFORE_UPDATE program.

program-name
The name of the trigger program. When omitted for an event, the event does not trigger an action.

DELETE event-name
Deletes the triggers for the specified object events. Oracle OLAP disassociates the trigger program from the specified object event.

DELETE ALL
Deletes all of the triggers for the specified object. Oracle OLAP disassociates the trigger program from all events for object.

#### Usage Notes

Multiple Occurrences of the Same Keyword

You can use all of the keywords in a single TRIGGER statement. However, if you use the same keyword twice in a TRIGGER statement, then Oracle OLAP recognized the last occurrence of the keyword; other occurrences are ignored.

For example, assume that you code the following TRIGGER statement.

    TRIGGER PROPERTY progname1 PROPERTY progname2 PROPERTY progname3

When executing this TRIGGER statement, Oracle OLAP executes `progname3` immediately before a property of the object is created, modified, or deleted; Oracle OLAP does not execute `progname1` or `progname2`.

#### Examples

Example 10-159 Creating Triggers

Assume that your analytic workspace contains a `TEXT` dimension named `city` and that you want to create programs that automatically execute when a MAINTAIN statement executes against `city` or when a property is created or deleted for city. To create these triggers, you issue the following statements.

    "Define the trigger programs
    DEFINE trigger_maintain_move_city PROGRAM BOOLEAN
    DEFINE trigger_property_city PROGRAM BOOLEAN
    "Associate the trigger programs to events for the city dimension
    CONSIDER city
    TRIGGER PROPERTY trigger_property_city
    TRIGGER MAINTAIN trigger_maintain_move_city

Example 10-160 Describing Triggers

Assume that you have created the triggers for `city` as described in Example 10-159 . Later you want to see the description of the triggers, to do so you cannot issue a DESCRIBE statement for your analytic workspace. Instead, you must issue a FULLDSC statement.

    DEFINE CITY DIMENSION TEXT
    TRIGGER MAINTAIN TRIGGER_MAINTAIN_MOVE_CITY -
            PROPERTY TRIGGER_PROPERTY_CITY

    DEFINE TRIGGER_MAINTAIN_MOVE_CITY PROGRAM BOOLEAN

    DEFINE TRIGGER_PROPERTY_CITY PROGRAM BOOLEAN

Example 10-161 Deleting Triggers

Assume that you have created the triggers described in Example 10-159 . Now you want to delete the MAINTAIN trigger for `city`. To delete this trigger you issue the following statements.

    CONSIDER city
    TRIGGER DELETE MAINTAIN


When you issue a FULLDSC statement, you confirm that the MAINTAIN trigger for `city` has been deleted although the `trigger_maintain_move_city` program remains.

    DEFINE CITY DIMENSION TEXT
    TRIGGER PROPERTY TRIGGER_PROPERTY_CITY

    DEFINE TRIGGER_MAINTAIN_MOVE_CITY PROGRAM BOOLEAN

    DEFINE TRIGGER_PROPERTY_CITY PROGRAM BOOLEAN

To actually delete the `trigger_maintain_move_city` program you must issue the following statement.

    DELETE TRIGGER_MAINTAIN_MOVE_CITY

Example 10-162 A MAINTAIN Trigger Program

Assume that you have a dimension with the following definition in your analytic workspace.

    DEFINE CITY DIMENSION TEXT


To create a Maintain trigger for city, you take the following steps:

1.  Define the trigger program as a user-defined function. It can have any name that you want. The following statement defines a program named `trigger_maintain_city`.

        DEFINE trigger_maintain_city PROGRAM BOOLEAN


2.  Specify the content of the program.

        PROGRAM
        SHOW JOINCHARS ('calltype = ' CALLTYPE)
        SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
        SHOW JOINCHARS ('triggering subevent = ' TRIGGER(SUBEVENT))
        RETURN TRUE
        END


3.  Issue a TRIGGER statement to associate the trigger program with the `city` dimension as a program to be executed when a Maintain event occurs. Remember to use a CONSIDER statement to make the definition for `city` the current definition.

        CONSIDER city
        TRIGGER MAINTAIN TRIGGER_MAINTAIN_CITY

When you issue a FULLDSC statement to see a full description of your analytic workspace, you can see the definition of `city` (including its Maintain trigger) and the `trigger_maintain_city` program.

    DEFINE CITY DIMENSION TEXT
    TRIGGER MAINTAIN TRIGGER_MAINTAIN_CITY

    DEFINE TRIGGER_MAINTAIN_CITY PROGRAM BOOLEAN
    PROGRAM
    SHOW JOINCHARS ('calltype = ' CALLTYPE)
    SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
    SHOW JOINCHARS ('triggering subevent = ' TRIGGER(SUBEVENT))
    RETURN TRUE
    END


As illustrated in the following statements and output, when you issue MAINTAIN statements for city, the `trigger_maintain_city` program executes.

    MAINTAIN city ADD 'Boston' 'Houston' 'Dallas'

    calltype = TRIGGER
    triggering event = MAINTAIN
    triggering subevent = ADD

    REPORT city

    CITY
    --------------
    Boston
    Houston
    Dallas

    MAINTAIN city MOVE 'Dallas' to 2

    calltype = TRIGGER
    triggering event = MAINTAIN
    triggering subevent = MOVE

    REPORT city

    CITY
    --------------
    Boston
    Dallas
    Houston

Example 10-163 An ASSIGN Trigger on a Variable

Assume that your analytic workspace contains objects with the following definitions.

    DEFINE geog DIMENSION TEXT
    DEFINE sales VARIABLE DECIMAL <geog>
    DEFINE percent_sales VARIABLE INTEGER <geog>


The `sales` variable contains the following values.

    GEOG             SALES
    -------------- ----------
    North America        0.59
    Europe               9.35
    Asia                   NA

The `percent_sales` variable is empty.

Assume that you want specialized processing of values when you assign values to `percent_sales`. To handle this processing automatically, you can create an Assign trigger program for `percent_sales` by taking the following steps:

1.  Create a trigger program that executes each time you assign values to `percent_sales`.

        DEFINE TRIGGER_EQ PROGRAM BOOLEAN
        PROGRAM
        ARGUMENT datavalue WORKSHEET
        show 'description of triggering object = '
        FULLDESCRIBE &TRIGGER(NAME)
        SHOW JOINCHARS ('calltype = ' CALLTYPE)
        SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
        SHOW JOINCHARS ('triggering subevent = ' TRIGGER(SUBEVENT))
        SHOW JOINCHARS ('value being assigned = ' datavalue)
        SHOW '  '
        END


2.  Add an assign trigger to `percent_sales` using a TRIGGER statement. Remember to first issue a CONSIDER statement to make the definition for the `percent_sales` variable the current definition.

        CONSIDER percent_sales
        TRIGGER ASSIGN TRIGGER_EQ

3.  Assign values to `percent_sales`.

        percent_sales = (sales/TOTAL(sales))*100

    Assigning values to `percent_sales` triggers the execution of the `trigger_eq` program and produces the following output lines.

        description of triggering object =
        DEFINE PERCENT_SALES VARIABLE INTEGER <GEOG>
        TRIGGER ASSIGN TRIGGER_EQ
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value being assigned = 6

        description of triggering object =
        DEFINE PERCENT_SALES VARIABLE INTEGER <GEOG>
        TRIGGER ASSIGN TRIGGER_EQ
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value being assigned = 94

        description of triggering object =
        DEFINE PERCENT_SALES VARIABLE INTEGER <GEOG>
        TRIGGER ASSIGN TRIGGER_EQ
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value being assigned =

    **Note:**

    From the output you can see that Oracle OLAP called the `trigger_eq` program three times—each time it assigned a value to `percent_sales`.

4.  When you issue REPORT commands for `sales` and `percent_sales` you can see the result of the calculations. The `percent_sales` variable contains values that are the percent of sales for each continent.

        GEOG                  SALES
        -------------- --------------------
        North America                  0.59
        Europe                         9.35
        Asia                             NA

        GEOG              PERCENT_SALES
        -------------- --------------------
        North America                     6
        Europe                           94
        Asia                             NA

Example 10-164 Setting Values in an ASSIGN Trigger Program

Assume that you have the following objects in your analytic workspace.

    DEFINE GEOGRAPHY DIMENSION TEXT WIDTH 12
    LD Geography Dimension Values

    DEFINE PRODUCT DIMENSION TEXT WIDTH 12
    LD Product Dimension Values

    DEFINE TIME DIMENSION TEXT WIDTH 12
    LD Time Dimension Values

    DEFINE CHANNEL DIMENSION TEXT WIDTH 12
    LD Channel Dimension Values

    DEFINE F.MARGIN FORMULA DECIMAL <CHANNEL GEOGRAPHY PRODUCT TIME>
    LD Margin
    EQ f.sales-f.costs


    DEFINE F.COSTS VARIABLE SHORT <GEOGRAPHY PRODUCT CHANNEL TIME>
    LD Costs

    DEFINE F.SALES VARIABLE SHORT <GEOGRAPHY PRODUCT CHANNEL TIME>
    LD Sales


Note that `f.costs`, `f.sales`, and` f.margin` all have the same dimensions.

Now you add an Assign trigger to `f.margin` that executes a program named `t.margin`. The definition of `f.margin` is modified to the following definition.

    DEFINE F.MARGIN FORMULA DECIMAL <CHANNEL GEOGRAPHY PRODUCT TIME>
    LD Margin
    TRIGGER ASSIGN T.MARGIN
    EQ f.sales-f.costs

Now you actually write the t.margin program. When an expression is assigned to the `f.margin` formula, the program uses this value to compute new values for `f.costs` and `f.sales`.

    DEFINE T.MARGIN PROGRAM
    PROGRAM
    ARG newVal DECIMAL       " The value passed to the program by the Assign trigger
    VARIABLE t.valDiff DECIMAL     " Difference between newVal and old value
    VARIABLE t.costInc DECIMAL     " Amount the difference makes to costs
    "show the value of newVal
    SHOW 'newVal = ' NONL
    SHOW newVal
    " Compute the difference between the current value and the new one
    t.valDiff = newVal - f.margin
    " Now increase costs proportional to their existing amounts
    t.costInc = (newVal - f.margin) * (f.costs/f.sales)
    " Adjust the values of sales and costs to get the new value
    SET1 f.costs = f.costs + t.costInc

    SET1 f.sales =  f.sales + t.valDiff + t.costInc

    SHOW geography NONL
    SHOW ' ' NONL
    SHOW product NONL
    SHOW ' ' NONL
    SHOW channel NONL
    SHOW ' ' NONL
    SHOW time NONL
    SHOW ' f.costs = 'NONL
    SHOW f.costs NONL
    SHOW ' f.sales = 'NONL
    SHOW f.sales
    END


Now assume that you issue the following LIMIT statements to identify a subset of data and issue a REPORT statement to report on the values of f.margin.

    LIMIT t0.hierdim TO 'STANDARD'
    LIMIT time TO t0.levelrel EQ 'L2'
    LIMIT geography TO FIRST 1
    LIMIT channel TO FIRST 1
    LIMIT product TO FIRST 5
    REPORT DOWN time ACROSS product: f.margin

    GEOGRAPHY: WORLD
    CHANNEL: TOTALCHANNEL
                   -----------------------F.MARGIN-----------------------
                   -----------------------PRODUCT------------------------
    TIME           TOTALPROD   AUDIODIV  PORTAUDIO    PORTCD     PORTST
    -------------- ---------- ---------- ---------- ---------- ----------
    Q1.96          54,713,974 29,603,546  5,379,661  2,480,914  1,615,708
    Q2.96          63,919,784 34,594,087  6,331,848  2,869,265  1,931,785
    Q3.96          58,303,490 31,543,152  5,792,725  2,616,515  1,795,701
    Q4.96          71,197,892 38,383,878  7,059,581  3,163,804  2,232,880
    Q1.97          55,489,723 29,989,262  5,368,237  2,491,475  1,607,344
    Q2.97          41,687,908 22,532,979  4,070,725  1,855,992  1,245,161


Now you issue the following assignment statement that increase the value of `f.margin` by 10% and report it

    f.margin = f.margin * 1.1

The execution of this assignment statement triggers the execution of the Assign trigger program named `t.margin`. The output of that program follows.

    newVal = 60,185,371.40
    WORLD TOTALPROD TOTALCHANNEL Q1.96 f.costs = 1,298,474.00 f.sales = 61,483,840.00
    newVal = 32,563,900.67
    WORLD AUDIODIV TOTALCHANNEL Q1.96 f.costs = 664,226.90 f.sales = 33,228,130.00
    newVal = 5,917,626.67
    WORLD PORTAUDIO TOTALCHANNEL Q1.96 f.costs = 97,976.04 f.sales = 6,015,603.00
    newVal = 2,729,005.43
    WORLD PORTCD TOTALCHANNEL Q1.96 f.costs = 34,301.53 f.sales = 2,763,307.00
    newVal = 1,777,278.95
    WORLD PORTST TOTALCHANNEL Q1.96 f.costs = 25,160.72 f.sales = 1,802,440.00
    newVal = 70,311,762.13
    WORLD TOTALPROD TOTALCHANNEL Q2.96 f.costs = 1,504,051.00 f.sales = 71,815,820.00
    newVal = 38,053,495.70
    WORLD AUDIODIV TOTALCHANNEL Q2.96 f.costs = 768,788.10 f.sales = 38,822,280.00
    newVal = 6,965,032.86
    WORLD PORTAUDIO TOTALCHANNEL Q2.96 f.costs = 114,558.20 f.sales = 7,079,591.00
    newVal = 3,156,191.20
    WORLD PORTCD TOTALCHANNEL Q2.96 f.costs = 39,256.88 f.sales = 3,195,448.00
    newVal = 2,124,963.02
    WORLD PORTST TOTALCHANNEL Q2.96 f.costs = 29,780.54 f.sales = 2,154,744.00
    newVal = 64,133,838.86
    WORLD TOTALPROD TOTALCHANNEL Q3.96 f.costs = 1,350,733.00 f.sales = 65,484,570.00
    newVal = 34,697,467.06
    WORLD AUDIODIV TOTALCHANNEL Q3.96 f.costs = 691,887.10 f.sales = 35,389,360.00
    newVal = 6,371,997.63
    WORLD PORTAUDIO TOTALCHANNEL Q3.96 f.costs = 103,203.70 f.sales = 6,475,202.00
    newVal = 2,878,166.40
    WORLD PORTCD TOTALCHANNEL Q3.96 f.costs = 35,358.18 f.sales = 2,913,525.00
    newVal = 1,975,270.68
    WORLD PORTST TOTALCHANNEL Q3.96 f.costs = 27,339.77 f.sales = 2,002,611.00
    newVal = 78,317,681.06
    WORLD TOTALPROD TOTALCHANNEL Q4.96 f.costs = 1,618,915.00 f.sales = 79,936,590.00
    newVal = 42,222,265.94
    WORLD AUDIODIV TOTALCHANNEL Q4.96 f.costs = 826,923.40 f.sales = 43,049,190.00
    newVal = 7,765,539.34
    WORLD PORTAUDIO TOTALCHANNEL Q4.96 f.costs = 123,269.50 f.sales = 7,888,809.00
    newVal = 3,480,184.35
    WORLD PORTCD TOTALCHANNEL Q4.96 f.costs = 41,998.90 f.sales = 3,522,183.00
    newVal = 2,456,168.00
    WORLD PORTST TOTALCHANNEL Q4.96 f.costs = 33,357.19 f.sales = 2,489,525.00
    newVal = 61,038,695.03
    WORLD TOTALPROD TOTALCHANNEL Q1.97 f.costs = 1,423,963.00 f.sales = 62,462,660.00
    newVal = 32,988,187.65
    WORLD AUDIODIV TOTALCHANNEL Q1.97 f.costs = 679,477.80 f.sales = 33,667,660.00
    newVal = 5,905,060.56
    WORLD PORTAUDIO TOTALCHANNEL Q1.97 f.costs = 158,854.40 f.sales = 6,063,915.00
    newVal = 2,740,622.56
    WORLD PORTCD TOTALCHANNEL Q1.97 f.costs = 53,144.41 f.sales = 2,793,767.00
    newVal = 1,768,078.14
    WORLD PORTST TOTALCHANNEL Q1.97 f.costs = 40,784.62 f.sales = 1,808,863.00
    newVal = 45,856,698.46
    WORLD TOTALPROD TOTALCHANNEL Q2.97 f.costs = 1,070,465.00 f.sales = 46,927,160.00
    newVal = 24,786,276.35
    WORLD AUDIODIV TOTALCHANNEL Q2.97 f.costs = 512,435.60 f.sales = 25,298,710.00
    newVal = 4,477,797.64
    WORLD PORTAUDIO TOTALCHANNEL Q2.97 f.costs = 118,791.70 f.sales = 4,596,590.00
    newVal = 2,041,591.56
    WORLD PORTCD TOTALCHANNEL Q2.97 f.costs = 39,287.77 f.sales = 2,080,879.00
    newVal = 1,369,677.57
    WORLD PORTST TOTALCHANNEL Q2.97 f.costs = 30,038.08 f.sales = 1,399,716.00

Example 10-165 An ASSIGN Trigger on a Formula

The way Oracle OLAP handles assigning values to a formula varies depending on whether or not the formula has an Assign trigger as part of its definition.

Assume your analytic workspace contains objects with the following definitions and values.

    DEFINE geog.d DIMENSION TEXT
    DEFINE time.d DIMENSION TEXT
    DEFINE sales VARIABLE DECIMAL <time.d geog.d>
    DEFINE f_modified_sales FORMULA DECIMAL <time.d geog.d>
      EQ sales+20


A report of `sales`, shows the base values.

                   -------------------SALES-------------------
                   ------------------TIME.D-------------------
    GEOG.D          Jan2004    Feb2004    Mar2004      2004
    -------------- ---------- ---------- ---------- ----------
    Boston               4.00       4.66       5.91       NA
    Medford              4.37       5.80       4.45       NA
    San Diego            4.97       5.95       4.75       NA
    Sunnydale            5.85       5.26       4.08       NA

A report of `f_modified_sales` formula displays the following report that contains the values computed by the formula.

                   -------------F_MODIFIED_SALES--------------
                   ------------------TIME.D-------------------
    GEOG.D          Jan2004    Feb2004    Mar2004      2004
    -------------- ---------- ---------- ---------- ----------
    Boston              24.00      24.66      25.91         NA
    Medford             24.37      25.80      24.45         NA
    San Diego           24.97      25.95      24.75         NA
    Sunnydale           25.85      25.26      24.08         NA

The `f_modified_sales` formula does not presently have an Assign trigger on it. Consequently, as illustrated in the following code, any attempt to assign values to `f_modified_sales` results in an error.

    f_modified_sales = 3
    ORA-34142: You cannot assign values to a FORMULA.

To create an Assign trigger on `f_modified_sales` take the following steps:

1.  Define the trigger program

        DEFINE TRIGGER_ASSIGN_MODIFIED_SALES PROGRAM
        PROGRAM
        ARGUMENT datavalue NUMBER
        SHOW 'description of triggering object = '
        DESCRIBE &TRIGGER(NAME)
        SHOW JOINCHARS ('calltype = ' CALLTYPE)
        SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
        SHOW JOINCHARS ('value being assigned = ' datavalue)
        SHOW '  '
        END


2.  Add the Assign trigger to the definition of the formula using the following statements.

        CONSIDER f_modified_sales
        TRIGGER ASSIGN trigger_assign_modified_sales


    Issuing a `FULLDSC f_modified_sales` statement displays the new complete definition for `f_modified_sales`.

        DEFINE F_MODIFIED_SALES FORMULA DECIMAL <TIME.D GEOG.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        EQ sales+20

3.  Now when you issue the following statement to assign a value to `f_modified_sales`, an error does not occur. Instead, the `trigger_assign_modified_sales `trigger program executes 16 times, once for each dimension value of `sales`.

        f_modified_sales = 3

        description of triggering object =
        DEFINE F_MODIFIED_SALES FORMULA DECIMAL <TIME.D GEOG.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        EQ sales+20
        calltype = TRIGGER
        triggering event = ASSIGN
        value being assigned = 3.00
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...
        description of triggering object =
        ...


4.  However, as issuing a REPORT statement for` f_modified_sales` illustrates, the values calculated by a simple execution of the formula have not changed.

        report f_modified_sales

                       -------------F_MODIFIED_SALES--------------
                       ------------------TIME.D-------------------
        GEOG.D          Jan2004    Feb2004    Mar2004      2004
        -------------- ---------- ---------- ---------- ----------
        Boston              24.00      24.66      25.91         NA
        Medford             24.37      25.80      24.45         NA
        San Diego           24.97      25.95      24.75         NA
        Sunnydale           25.85      25.26      24.08         NA

### 10.67 TRIGGERASSIGN

Within a program triggered by an Assign event for an object, assigns a value to the triggering object.

**Note:**

The [USETRIGGERS](olap-dml-options.md) option must be set to its default value of `TRUE` for a TRIGGERASSIGN to execute

**Note:**

"[Trigger Programs](olap-dml-programs.md)"

#### Data Type

The data type of the object to which Oracle OLAP assigns the value.

#### Syntax

TRIGGERASSIGN value

#### Parameters

value
The value that you want assigned.

#### Examples

Example 10-166 Assigning an Alternative Value using an Assign Trigger

Assume that you have objects with the following descriptions in your analytic workspace.

    DEFINE GEOG.D DIMENSION TEXT
    DEFINE TIME.D DIMENSION TEXT
    DEFINE TIME.PARENTREL RELATION TIME.D <TIME.D>
    DEFINE SALES VARIABLE DECIMAL <GEOG.D TIME.D>
    DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>

Assume also that you have populated the `sales` variable with the values shown in the following report, but that you have not yet populated the `modified_sales` variable.

                 -----------------------SALES-----------------------
                 ----------------------GEOG.D-----------------------
    TIME.D          Boston      Medford     San Diego    Sunnydale
    ------------ ------------ ------------ ------------ ------------
    Jan76            1,000.00     2,000.00     3,000.00     4,000.00
    Feb76            2,000.00     4,000.00     6,000.00     8,000.00
    Mar76            3,000.00     6,000.00     9,000.00    12,000.00
    76Q1                   NA           NA           NA           NA


Now you want to assign values to the `modified_sales` variable using various expressions, however, you want to ensure that the values never are less than or equal to 1,000. You can assure this processing by taking the following steps:

1.  Create the following program that checks for values less than or equal to 1000 condition.

        DEFINE TRIGGER_ASSIGN_MODIFIED_SALES PROGRAM
        PROGRAM
        ARGUMENT datavalue DECIMAL
        IF datavalue LE 1000
         THEN TRIGGERASSIGN 1000
        show 'description of triggering object = '
        DESCRIBE &TRIGGER(NAME)
        SHOW JOINCHARS ('calltype = ' CALLTYPE)
        SHOW JOINCHARS ('triggering event = ' TRIGGER(EVENT))
        SHOW JOINCHARS ('triggering subevent = ' TRIGGER(SUBEVENT))
        SHOW JOINCHARS ('value passed to program = ' datavalue)
        SHOW '  '
        END


2.  Issue the following statements to add an Assign trigger to the `modified_sales` variable. The `trigger_assign_modified_sales` program is the trigger program.

        CONSIDER modified_sales
        TRIGGER ASSIGN trigger_assign_modified_sales

3.  Assign values to `modified_sales`.

        modified_sales = sales - 1000

4.  This statement triggers the execution of the `trigger_assign_modified_sales` program for each value that Oracle OLAP assigns.

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 0.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 1,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 2,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 3,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 1,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 3,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 5,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 7,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 2,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 5,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 8,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program = 11,000.00

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program =

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program =

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program =

        description of triggering object =
        DEFINE MODIFIED_SALES VARIABLE DECIMAL <GEOG.D TIME.D>
        TRIGGER ASSIGN TRIGGER_ASSIGN_MODIFIED_SALES
        calltype = TRIGGER
        triggering event = ASSIGN
        triggering subevent =
        value passed to program =

5.  The following report of `modified_sales` shows that all values are at least 1,000.


                     ------------------MODIFIED_SALES-------------------
                     ----------------------GEOG.D-----------------------
        TIME.D          Boston      Medford     San Diego    Sunnydale
        ------------ ------------ ------------ ------------ ------------
        Jan76            1,000.00     1,000.00     2,000.00     3,000.00
        Feb76            1,000.00     3,000.00     5,000.00     7,000.00
        Mar76            2,000.00     5,000.00     8,000.00    11,000.00
        76Q1                   NA           NA           NA           NA

### 10.68 UNHIDE

The UNHIDE command makes visible the text of a program that has been made invisible by a HIDE statement. To use UNHIDE, you must know the seed expression that was used with the HIDE statement when the program was hidden.

**Note:**

The HIDE command performs simple encoding. For information on using secure encryption and other security features in Oracle, see [About Oracle Database Security](../dbseg/introduction-to-oracle-database-security.md) in Oracle Database Security Guide.

#### Syntax

UNHIDE prog-name seed-exp

#### Parameters

prog-name
The name of a program whose text has been made invisible by using the HIDE statement. Do not enclose the program name in quotes.

seed-exp
The single-line text expression that was used in the HIDE statement when "prog-name" was hidden. The seed expression must be byte-for-byte the same value as you used in the HIDE statement. Also, because the seed expression is case-sensitive, specify uppercase and lowercase characters carefully.

#### Usage Notes

Forgetting the Seed Expression

When you want to use an UNHIDE statement on a program but you have forgotten the seed expression, you can call Oracle OLAP Products Technical Support for help in solving your problem. Before calling, make a connection to Oracle OLAP from OLAP Worksheet, and in Oracle OLAP, attach the analytic workspace that contains the hidden program.

#### Examples

Example 10-167 Unhiding Program Text

The following example makes visible the text of a program called `sales_rpt`. The seed expression `crystal` was used when the program was hidden using HIDE.

    UNHIDE sales_rpt 'crystal'

### 10.69 UPDATE

The UPDATE command moves analytic workspace changes from a temporary area to the database table in which the workspace is stored. Typically, you use an UPDATE statement when you are finished making changes in an analytic workspace; however, you can also specify UPDATE commands periodically as you go along.

Your changes are not saved until you execute a COMMIT statement, either from Oracle OLAP or from SQL. When you do not use the UPDATE and COMMIT commands, changes made to an analytic workspace during your session are discarded when you end your Oracle session.

**Note:**

You can detach and reattach an analytic workspace without losing updated changes, even though they are not committed because the detaching and reattaching occur within a single database session

#### Syntax

UPDATE \[MULTI \[acquired_objects\]\] \[analytic_workspaces\]

#### Parameters

When you do not specify any parameters, the command updates all analytic workspaces that are attached in read/write non-exclusive and read/write exclusive modes and all acquired objects (that is, all acquired variables, relations, valuesets, and dimensions) in all analytic workspaces that are attached in multiwriter mode.

acquired_objects
A list of the names of acquired objects, separated by commas, in analytic workspaces attached in multiwriter mode. These objects can be any object that you have acquired using an ACQUIRE statement.

To specify individual partitions of a partitioned variable, use the following syntax.

variable_name (PARTITION partition_name \[, PARTITION partition_name \]...)

**Note:**

you cannot update an object when it is dimensioned by an acquired and maintained dimension unless you update that dimension first.

workspaces
A list of names, separated by commas. of one or more workspaces attached in read/write or multiwriter mode.

#### Usage Notes

Automatic COMMIT

Many users execute DML statements using SQL\*Plus or OLAP Worksheet. Both of these tools automatically execute a COMMIT statement when you end your session.

Triggering Program Execution When UPDATE Executes

Using the TRIGGER command, you can make an UPDATE statement an event that automatically executes an OLAP DML program. See "[Trigger Programs](olap-dml-programs.md)" for more information

Shared Workspaces

When you have attached a shared workspace and another user has read/write access, that user's UPDATE and COMMIT commands do not affect your view of the workspace. Your view of the data remains the same as when you attached the workspace. When you want access to the changes, you can detach the workspace and reattach it.

Effect of a ROLLBACK Statement

The OLAP DML does not provide a way to issue a SQL `ROLLBACK` statement; however, you could execute one in your session from outside Oracle OLAP (for example, through PL/SQL). When a `ROLLBACK` statement is executed in your session, Oracle OLAP checks to see whether there are uncommitted updates in an attached workspace.

- When there are uncommitted updates (that is, you have made changes and executed an UPDATE statement, but you have not subsequently executed a COMMIT statement), then Oracle OLAP discards your changes and detaches the workspace.

- When you have no uncommitted updates, then Oracle OLAP takes no action in response to a `ROLLBACK` statement. Consequently, when you have not issued an UPDATE statement since your last COMMIT statement, Oracle OLAP takes no action and all your changes remain in the workspace during your session.

When you rollback to a savepoint and there are uncommitted updates that occurred after the savepoint, Oracle OLAP discards those updates and detaches the workspace. Uncommitted updates that occurred before the savepoint remain in the workspace, and you can see them when you reattach the workspace in the same session.

#### Examples

Example 10-168 Saving Analytic Workspace Changes

The following statement moves changes in the current workspace session to the database table in which the workspace is stored.

    UPDATE

To save the changes in the database, the UPDATE statement must be followed by a COMMIT statement.

### 10.70 UPDATE_ATTRIBUTE_VALUE

The UPDATE_ATTRIBUTE_VALUE program modifies the attributes of an OLAP cube dimension member.

This program is especially useful when updating the following kinds of attributes:

- For attributes with an underlying relation or indexed dimension, you need only to provide the dimension member and value. The indexed dimension is maintained along with setting the value in the relation.

- For spread attributes, if you set an attribute value on an attribute spanning all levels, then the values are spread down to lower levels on compile.

**Note:**

You cannot use this program to modify a cube dimension if a materialized view exists for that cube dimension or any cube in which it participates.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL UPDATE_ATTRIBUTE_MEMBER(dim_member_id, attribute_name, attribute_value -

           \[, auto_compile \])

#### Parameters

CALL
Because UPDATE_ATTRIBUTE_VALUE is an OLAP DML program with arguments, you invoke it using the OLAP DML [CALL](olap-dml-commands-a-g.md) statement.

dim_member_id
A text expression that is the value of the cube dimension member that you want to modify the attributes of.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension of which dim_member_id is a member.

**See Also:**

"[Guidelines for Specifying Values for the Names of Logical OLAP Objects](olap-dml-commands-a-g.md)"

attribute_name
A text expression that is the Oracle data dictionary name of the attribute.

attribute_value
A text expression that specifies the value of attribute_name.

auto_compile
A Boolean expression that specifies whether or not you want related analytic workspace objects to be updated immediately.

The default value is `TRUE` in which case all of the changes to the analytic workspace that are needed to update the attribute of the cube dimension member happen now.

Specify FALSE only when, for performance reasons, you want to make a bulk set of changes before issuing a compile. In this case, you need to explicitly compile the cube dimension before the values of the analytic workspace objects take effect as described in "[Explicitly Compiling a Cube Dimension](olap-dml-commands-a-g.md)".

**Note:**

Regardless of the value that you specify for this argument, the attribute of the dimension member is always immediately updated -- even when an error is signaled during compilation.

#### Examples

Example 10-169 Updating the Attributes of an OLAP Cube Dimension

This example uses the UPDATE_ATTRIBUTE_VALUE program provided with the OLAP DML to update attributes of the `my_time` cube dimension for the L1-2 and the descendants of L1-2. The calls to the UPDATE_ATTRIBUTE_VALUE program provided with the OLAP DML are within a user-written OLAP DML program named `ADD_L1_2_DATE`.

1.  Issue the following PL/SQL statement to execute the user-written OLAP DML program named `ADD_L1_2_DATE` to set `time` attribute values for `L1_2` and its descendants

        exec dbms_aw.execute('call my_util_aw!add_l1_2_dates');

    The definition of the user-written `ADD_L1_2_DATE` OLAP DML program is shown below. Notice the calls to the UPDATE_ATTRIBUTE_VALUE program provided with the OLAP DML.

        DEFINE ADD_L1_2_DATES PROGRAM
        PROGRAM
          VARIABLE _aw_dim       text
          VARIABLE _start_date   text
          VARIABLE _timespan     text

          _aw_dim = OBJORG(DIM 'my_time')
          _start_date = OBJORG(ATTRIBUTE 'my_time' 'start_date')
          _timespan = OBJORG(ATTRIBUTE 'MY_TIME' 'timespan')

          " Updates the time attribute of L1_2, L2_3, L3_6, but does not compile
          CALL UPDATE_ATTRIBUTE_VALUE('L1_2', 'my_time', 'start_date', -
                                      &_start_date(&_aw_dim 'L1_1')+365, NO)
          CALL UPDATE_ATTRIBUTE_VALUE('L1_2', 'my_time', 'timespan', -
                                      &_timespan(&_aw_dim 'L1_1'), NO)

          CALL UPDATE_ATTRIBUTE_VALUE('L2_3', 'my_time', 'start_date', -
                                      &_start_date(&_aw_dim 'L1_2'), NO)
          CALL UPDATE_ATTRIBUTE_VALUE('L2_3', 'my_time', 'timespan', -
                                      &_timespan(&_aw_dim 'L2_1'), NO)

          CALL UPDATE_ATTRIBUTE_VALUE('L3_6', 'my_time', 'start_date', -
                                      &_start_date(&_aw_dim 'L1_2'), NO)
          CALL UPDATE_ATTRIBUTE_VALUE('L3_6', 'my_time', 'timespan', -
                                      &_timespan(&_aw_dim 'L3_1'), NO)
          UPDATE
          COMMIT
        END

2.  Issue the following SQL statement to see what the attributes of the `my_time` cube dimension are.

        select dim_key||'  '||start_date||'  '||lpad(timespan, 3)
            from my_time_view
            order by dim_key asc;

        DIM_KEY||''||START_DATE||''||LPAD(TIMESPAN,3)
        ----------------------------------------------------------------------------
        L1_0  01-JAN-09  365
        L1_1  01-JAN-10  365
        L1_2  01-JAN-11  365
        L2_1  01-JAN-10   90
        L2_2  01-APR-10   61
        L2_3  01-JAN-11   90
        L3_1  01-JAN-10   31
        L3_2  01-FEB-10   28
        L3_3  01-MAR-10   31
        L3_4  01-APR-10   30
        L3_5  01-MAY-10   31
        L3_6  01-JAN-11   31

        12 rows selected.

3.  Issue the following SQL statement to report the values of the `sales` and `moving_sales` measures before the `my_time` cube dimension is compiled. Note that the calculation for the measures does not consider the new attributes of the `my_time` cube dimension.

        select my_time||'  '||lpad(sales, 2)||'  '||lpad(moving_sales, 2)
        from my_cube_view
        order by my_time asc;

        MY_TIME||''||LPAD(SALES,2)||''||LPAD(MOVING_SALES,2)
        --------------------------------------------------------------------
        L1_0  24  27
        L1_1  14  38
        L1_2   3   3
        L2_1   2   5
        L2_2  12  14
        L2_3   3   3
        L3_1   1   4
        L3_2   1   2
        L3_3  10  11
        L3_4   1  11
        L3_5   1   2
        L3_6   3   3

        12 rows selected.

4.  Issue the following SQL statement to compile the `my_time` cube dimension.

        exec dbms_cube.build('MY_TIME USING (COMPILE)');

5.  Issue the following SQL statement to report the values of the `sales` and `moving_sales` measures after the `my_time` cube dimension is compiled. Note that now the calculation for the measures considers the new attributes of the `my_time` cube dimension

        select my_time||'  '||lpad(sales, 2)||'  '||lpad(moving_sales, 2)
               from my_cube_view
               order by my_time asc;

        MY_TIME||''||LPAD(SALES,2)||''||LPAD(MOVING_SALES,2)
        --------------------------------------------------------------------
        L1_0  24  24
        L1_1  14  38
        L1_2   3  17
        L2_1   2   2
        L2_2  12  14
        L2_3   3  15
        L3_1   1   1
        L3_2   1   2
        L3_3  10  11
        L3_4   1  11
        L3_5   1   2
        L3_6   3   4

        12 rows selected.

### 10.71 UPDATE_DIMENSION_MEMBER

The UPDATE_DIMENSION_MEMBER program sets the level and the parent of an OLAP cube dimension member in one or more hierarchies.

**Note:**

You cannot use this program to modify a cube dimension if a materialized view exists for that cube dimension or any cube in which it participates.

**See Also:**

"[Cube-Aware OLAP DML Statements](olap-dml-basic-concepts.md)"

#### Syntax

CALL UPDATE_DIMENSION_MEMBER(member_id, logical_dim, hier_list,  level_name,  -

     parent-member_id \[, auto_compile \])

#### Parameters

CALL
Because UPDATE_DIMENSION_MEMBER is an OLAP DML program with arguments, you invoke it using the OLAP DML [CALL](olap-dml-commands-a-g.md) statement.

member_id
A text expression that is the member for which you want to set the level and parent information.

logical_dim
A text expression that is the Oracle data dictionary name of the cube dimension being modified.

**See Also:**

"[Guidelines for Specifying Values for the Names of Logical OLAP Objects](olap-dml-commands-a-g.md)"

hier_list
A multi-line text expression consisting of the Oracle data dictionary names of all of the hierarchies that you want to set the level and parent for the dimension member. Specify one hierarchy name per line.

When you want to specify information for the member in all hierarchies of the cube dimension, specify `NA`.

level_name
For level hierarchies, a text value that specifies the hierarchy level at which the program will set the member of the cube dimension. For level hierarchies, the value you specify for level_name must be:

- Compatible with the value you specify for parent_member_id

- At the same hierarchy level as the existing cube dimension member because a cube dimension member cannot be in two different levels across hierarchies.

When the member participates in a value hierarchy (that is, when there are no levels), specify `NA`.

**See Also:**

"[Invalid Level Names in Cube-Aware OLAP DML Statements](olap-dml-commands-a-g.md)"

parent_member_id
A text expression that specifies the value of the member which is the parent of the dimension member that you want to add to the hierarchy of the cube dimension. Specify `NA` when you want to add the dimension member as the top member.

auto_compile
A Boolean expression that specifies whether or not you want your changes to take effect immediately. The default value is `TRUE` in which case all of the changes to the analytic workspace that are needed to add the cube dimension member happen now. Specify FALSE only when, for performance reasons, you want to make a bulk set of changes before issuing a compile. In this case, you need to explicitly compile the cube dimension before the values of the analytic workspace objects take effect (for example, before attribute values are spread down or for time dimension valuesets to be updated), as described in "[Explicitly Compiling a Cube Dimension](olap-dml-commands-a-g.md)".

#### Examples

Example 10-170 Changing the Hierarchy of an OLAP Cube Dimension

Assume that you have a hierarchical cube dimension named `my_time` and you want to change its hierarchy by moving the value L3_2 from the top-level to being a child of L2_2.

1.  Execute the following SQL statement to report on the values of the `my_time` cube dimension before the move.

        select dim_key||'  '||level_name||'  '||parent
            from my_time_lvl_hier_view
            order by dim_key asc;

        DIM_KEY||''||LEVEL_NAME||''||PARENT
        --------------------------------------------------------------------------------
        L1_0  L1
        L1_1  L1
        L2_1  L2  L1_1
        L2_2  L2  L1_1
        L3_1  L3  L2_1
        L3_2  L3  L2_1
        L3_3  L3  L2_1
        L3_4  L3  L2_2
        L3_5  L3  L2_2

        9 rows selected.


2.  Issue the following PL/SQL statement that calls the user-written MOVE_L3_3 program to make the move.

        exec dbms_aw.execute('call my_util_aw!move_l3_3');

    As you can see from the following definition of the MOVE_L3_3 program, the actual move is performed by a CALL to the PDATE_DIMENSION_MEMBER program provided with the OLAP DML.

        DEFINE MOVE_L3_3 PROGRAM
        PROGRAM

          " Change the parent of L3_2 to L2_2
          CALL UPDATE_DIMENSION_MEMBER('L3_3', 'my_time', NA, 'L3', 'L2_2')
          UPDATE
          C0MMIT
        END

3.  Issue the following statement to report the values of the my_time dimension after the move

        select dim_key||'  '||level_name||'  '||parent
             from my_time_lvl_hier_view
             order by dim_key asc;

        DIM_KEY||''||LEVEL_NAME||''||PARENT
        --------------------------------------------------------------------------------
        L1_0  L1
        L1_1  L1
        L2_1  L2  L1_1
        L2_2  L2  L1_1
        L3_1  L3  L2_1
        L3_2  L3  L2_1
        L3_3  L3  L2_2
        L3_4  L3  L2_2
        L3_5  L3  L2_2

        9 rows selected.


4.  Issue the following statement to solve `my_cube` with new hierarchy of `my_time`.

        exec dbms_cube.build(script => 'MY_CUBE USING (SOLVE)', add_dimensions => false);


5.  Issue the following statement to report on the values of `sales` and `moving_sales` (the measures in `my_cube`) now that `my_time` has a new hierarchy.

        select my_time||'  '||lpad(sales, 2)||'  '||lpad(moving_sales, 2)
             from my_cube_view
             order by my_time asc;

        MY_TIME||''||LPAD(SALES,2)||''||LPAD(MOVING_SALES,2)
        --------------------------------------------------------------------
        L1_0  24  24
        L1_1  14  38
        L2_1   2   2
        L2_2  12  14
        L3_1   1   1
        L3_2   1   2
        L3_3  10  11
        L3_4   1  11
        L3_5   1   2

        9 rows selected.

### 10.72 VARIABLE

Within an OLAP DML program, the VARIABLE command declares a local variable or valueset for use within that program. A local variable cannot have any dimensions and exists only while the program is running.

**See Also:**

[DEFINE VARIABLE](olap-dml-commands-a-g.md) command

#### Syntax

VARIABLE name {datatype\|dimension\|VALUESET dim}

#### Parameters

name
The name for the local variable or valueset. When you use the same name as an existing analytic workspace object, the local variable or valueset takes precedence over the analytic workspace object. After you assign a value to the variable or valueset, its value is available within the program where the VARIABLE statement occurs. You name a variable or valueset according to the rules for naming analytic workspace objects (see the main entry for the [DEFINE](olap-dml-commands-a-g.md) command).

datatype
The data type of the variable, which indicates the kind of data to be stored. You can specify any of the data types that are listed and described in the DEFINE VARIABLE entry. Also, when you want to the program to be able to receive an argument without converting it to a specific data type, you can also specify `WORKSHEET` for the data type.

dimension
Indicates that name is a relation variable, which holds a single value of the specified dimension. The variable can hold a value of the dimension or a position (`INTEGER`) of the specified dimension. Assigning a value that does not currently exist in the dimension causes an error.

VALUESET dim
Indicates that name is a valueset. The dim argument is the name of the dimension for which the valueset holds values.

#### Usage Notes

Persistence of a Local Variable

A local variable or valueset exists only while the program that specified it is running. When the program terminates, the variable or valueset ceases to exist and its value is lost. A program can terminate when a RETURN statement, SIGNAL statement, or the last line of the program executes. When the program calls another program, the original program is temporarily suspended and the variable or valueset does exist when the called program ends and control returns to the original program. A program that calls itself recursively has separate local variable or valuesets for each running copy of the program.

Declarations at the Start Of A Program

You must specify all your local variables or valuesets at the beginning of a program, before any executable statements.

Initial Value of a Local Variable or Valueset

The value of a local variable or valueset is initially `NA`.

Duplicating the Name of an Analytic Workspace Object

When you give a local variable or valueset the same name as an analytic workspace object, Oracle OLAP assumes you are referring to the local variable or valueset within the program. The analytic workspace object has priority only when the statement requires an analytic workspace object as an argument.

Although the OBJ and EXISTS functions expect an analytic workspace object as an argument, you can use a local text variable or valueset to specify the name of an object.

Formulas and Models

You cannot use local variables or valuesets in a formula or model.

EXPORT and IMPORT Commands

In a program, you can use an [EXPORT (EIF)](olap-dml-commands-a-g.md) statement to store the value of a local variable or valueset in an EIF file. You must use the AS keyword to give the variable or valueset an analytic workspace object name. The name can be the same as the name of the local variable or valueset. When you use IMPORT (EIF) to retrieve the value, it is stored as an analytic workspace object. You cannot import the value into a local variable or valueset.

#### Examples

Example 10-171 Saving a File Unit Number

Suppose you want to write a program to read data from an input file with Data Reader statements. First you must open the file and save the value of the file unit number assigned to it. At the beginning of the program you can specify a local variable called `unit` to hold the file unit number.

    DEFINE read.file PROGRAM
    LD Read monthly sales data into the analytic workspace
    PROGRAM
    VARIABLE unit INTEGER
    TRAP ON error
    unit = FILEOPEN('sales.data' READ)
    ...

Example 10-172 Returning a Dimension Value from a Program

Suppose you want to write a program that analyzes sales for various districts and returns the name of the district in which sales were highest. For the purpose of analysis, the program defines a local variable to hold the district name. When the program ends, it returns the value of the local variable.

    DEFINE highsales PROGRAM
    PROGRAM
    VARIABLE districtname district
    ... "(statements that find the highest district)
    RETURN districtname
    END

### 10.73 VNF

The VNF command assigns a value name format (VNF) to the definition of an object with `DATE` -only data type, including dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR. A VNF is a template that controls the input and display format for `DATE` -only values. The template can include format specifications for any of the components that identify a time period (day, month, calendar year, fiscal year, and period within a fiscal year).

**Note:**

You can only use this statement with dimensions that have a data type of `DATE` (that is, dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR).You cannot use this statement for time dimensions that have a datetime data type that corresponds to a SQL datetime data type or dimensions that are implemented as hierarchical dimensions of type TEXT.

To assign a VNF to a definition, the definition must be the one most recently defined or considered during the current session. When it is not, you must first use a CONSIDER statement to make it the current definition.

#### Syntax

VNF \[template\]

#### Parameters

template
A text expression that specifies the format for entering and displaying the values of the current dimension. When template is omitted, any existing VNF for the current definition is deleted and the default VNF is used (see the Default VNFs for DWMQY Dimensions table in [Date-only Dimension Values](data-types-operators-and-expressions.md)).

**Note:**

When you enter a dimension value that does not conform to the VNF, Oracle OLAP attempts to interpret the value as a date. See "Entering Dimension Values as Dates"

A template contains a code for each component that you use to describe a time period in the current dimension. The code for each component must be preceded by a left angle bracket and followed by a right angle bracket. Basic information about coding a template is provided in Table 10-12, Table 10-13, and Table 10-14.

The following table lists the basic codes for the components of time periods. It uses a sample dimension called MYQTR, which is a QUARTER dimension that ends in June. The examples are from the quarter July 1, 1995 through September 30, 1995. The period code (`P`) specifies the numeric position of a time period within a fiscal year. You can use the `P` code with any dimension, but only when you use it along with the `FF` or `FFB` code. The `B` code specifies the beginning period.

Table 10-12 Basic Codes for Components in VNF Templates

| Code     | Meaning                                                                                                                  | Sample Values |
|:---------|:-------------------------------------------------------------------------------------------------------------------------|:--------------|
| `<D>`    | Day of the month on which the period ends                                                                                | `30`          |
| `<M>`    | Month in which the period end                                                                                            | `9`           |
| `<YY>`   | Calendar year in which the period ends                                                                                   | `95`          |
| `<FF>`   | Fiscal year that contains the period; the fiscal year is identified by the calendar year in which the fiscal year ends   | `96`          |
| `<DB>`   | Day of the month on which the period begins                                                                              | `1`           |
| `<MB>`   | Month in which the period begins                                                                                         | `7`           |
| `<YYB>`  | Calendar year in which the period begins                                                                                 | `95`          |
| `<FFB>`  | Fiscal year that contains the period; the fiscal year is identified by the calendar year in which the fiscal year begins | `95`          |
| `<P>`    | The period's numeric position within the fiscal year                                                                     | `1`           |
| `<NAME>` | Name of the dimension                                                                                                    | `MYQTR`       |

The following table lists the component combinations you can combine in a VNF for each type of dimensions of type DAY, WEEK, MONTH, QUARTER, or YEAR. Notice that you can use the fiscal year codes (`FF` or `FFB`) in a template for any dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR. However, the fiscal year codes have a special meaning for WEEK dimensions and for phased MONTH, QUARTER, and YEAR dimensions. For other dimensions, the fiscal year is identical to the calendar year. See "Fiscal Years for a Dimension of Type WEEK", "Fiscal Years for Dimensions of Type MONTH, QUARTER, or YEAR", and "Fiscal Years for Dimensions of Type DAY".

Table 10-13 Component Combinations Allowed in VNF Templates

| Type of Dimension               | Component Combinations                                                                | Sample Values                                            |
|:--------------------------------|:--------------------------------------------------------------------------------------|:---------------------------------------------------------|
| DAY, WEEK, MONTH, QUARTER, YEAR | `<D> <M> <YY>`<br>`<DB> <MB> <YYB>`<br>`<P> <FF>`<br>`<P> <FFB>`                      | `31 3 96`<br>`1 4 95`<br>`1 96`<br>`1 95`                |
| MONTH, QUARTER, YEAR            | `<M> <YY>`<br>`<MB> <YYB>`<br>`<M> <FF>`<br>`<M> <FFB>`<br>`<MB> <FF>`<br>`<MB <FFB>` | `3 96`<br>`4 95`<br>`3 96`<br>`3 95`<br>`4 96`<br>`4 95` |
| YEAR                            | `<YY>`<br>`<FF>`<br>`<FFB>`                                                           | `96`<br>`96`<br>`95`                                     |

Notice that instead of the basic codes listed in Table 10-13, you can substitute any of the format styles listed in Table 10-14. You can also include the `<NAME>` component with any of the component combinations listed in Table 10-13.

You cannot specify a template that includes too few or too many components. The VNF must allow you to input dimension values without ambiguity. See "Coding VNFs to Prevent Ambiguity".

However, if you include only the component combinations that are allowed for a particular type of dimension, and if the VNF permits unambiguous interpretation of input, you have considerable flexibility in specifying a VNF template:

- You can specify the components in any order.

- You can include text before, after, and between the components.

Instead of the basic codes for the day, month, calendar year, fiscal year, and period that were listed in Table 10-13, you can substitute the format styles listed in Table 10-14, Table 10-15, Table 10-16, and Table 10-17.

Table 10-14 Format Styles for Day Available in VNF Templates

| Format | Meaning                  | Jan 3, 1995 | Nov 12, 2051 |
|:-------|:-------------------------|:------------|:-------------|
| `<D>`  | One digit or two digits  | `3`         | `12`         |
| `<DD>` | Two digits               | `03`        | `12`         |
| `<DS>` | Space-padded, two digits | `3`         | `12`         |

Table 10-15 Format Styles for Month Available in VNF Templates

| Format     | Meaning                        | Jan 3, 1995 | Nov 12, 2051 |
|:-----------|:-------------------------------|:------------|:-------------|
| `<M>`      | One digit or two digits        | `1`         | `11`         |
| `<MM>`     | Two digits                     | `01`        | `11`         |
| `<MS>`     | Space-padded, two digits       | `1`         | `11`         |
| `<MTXT>`   | First three letters, uppercase | `JAN`       | `NOV`        |
| `<MTXTL>`  | First three letters, lowercase | `jan`       | `nov`        |
| `<MTEXT>`  | Full name, uppercase           | `JANUARY`   | `NOVEMBER`   |
| `<MTEXTL>` | Full name, lowercase           | `january`   | `november`   |

Note that for `MTXT`, `MTXTL`, `MTEXT`, and `MTEXTL`, the actual value displayed depends on the value specified for the MONTHNAMES option:

- For MTXT and MTEXT, when the name in the MONTHNAMES option is all lowercase, the entire name is converted to uppercase. Otherwise, the first letter is converted to uppercase and the second and subsequent letters remain in their original case.

- For MTXTL and MTEXTL, when the name in the MONTHNAMES option is all uppercase, the entire name is converted to lowercase. Otherwise the first letter is converted to lowercase and the second and subsequent letters remain in their original case.

Table 10-16 Format Styles for Year Available in VNF Templates

| Format   | Meaning                   | Jan 3, 1995 | Nov 12, 2051 |
|:---------|:--------------------------|:------------|:-------------|
| `<YY>`   | Two digits or four digits | `95`        | `2051`       |
| `<YYYY>` | Four digits               | `1995`      | `2051`       |
| `<FF>`   | Two digits or four digits | `95`        | `2051`       |
| `<FFFF>` | Four digits               | `1995`      | `2051`       |

Table 10-17 Format Styles for Period Available in VNF Templates

| Format  | Meaning                           | Jan 3, 1995 | Nov 12, 2051 |
|:--------|:----------------------------------|:------------|:-------------|
| `<P>`   | One, two, or three digits         | `3`         | `316`        |
| `<PP>`  | Two or three digits               | `03`        | `316`        |
| `<PS>`  | Space-padded, two or three digits | `3`         | `316`        |
| `<PPP>` | Three digits                      | `003`       | `316`        |
| `<PPS>` | Space-padded, three digits        | `3`         | `316`        |

#### Usage Notes

Discarding a VNF

When you want to discard a VNF for a dimension and return to using the default VNF, use a CONSIDER statement to make the dimension's definition the current one, and then use a VNF statement with no argument.

Specifying Angle Brackets as Text in a VNF Template

To include an angle bracket as additional text in a template, specify two additional angle brackets for each angle bracket to be included as text (for example, to display the entire value in angle brackets, specify `<<<D>` `<M>` `<YY>>>`).

Month Names

The names used in the month component for the `MTXT`, `MTXTL`, `MTEXT`, and `MTEXTL` formats are drawn from the current setting of the MONTHNAMES option.

Fiscal Year Codes

You can use a fiscal year code (`FF` or `FFB`) in a template for any dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR.

Fiscal Years for a Dimension of Type WEEK

For a dimension of type WEEK, a fiscal year starts on the beginning date of the first period (single-week or multiple-week) that ends in a new calendar year. The fiscal year ends on the final date of the final period that is wholly contained in the calendar year.

This definition holds true, regardless of any beginning or ending date you specify for a WEEK dimension when you define it. However, the fiscal year does take into account the beginning or ending day of the week that you specify (either as a day of the week or as a date).

For example, suppose you define a dimension of type WEEK, named `myweek`, with single-week periods ending on June 2, 1995 (a Friday). The fiscal year that contains June 2, 1995 begins on December 31, 1994 (a Saturday) and ends on December 29, 1995 (a Friday). When the VNF for `myweek` has the `FF` code, this fiscal year is identified as 1995. When the VNF has the `FFB` code, the fiscal year is identified as 1994.

Fiscal Years for Dimensions of Type MONTH, QUARTER, or YEAR

For a dimension of type MONTH, QUERTER, or YEAR with no beginning or ending phase, the fiscal year is identical to the calendar year.

For a MONTH, QUARTER, or YEAR dimension with a beginning or ending phase, each fiscal year for that dimension begins with the beginning month of the phase and ends with the ending month of the phase.

For example, assume you define a dimension of type MONTH, `mymonth`, with four-month periods ending in March, each fiscal year begins on April 1 and ends on March 31. When you use the `FF` code in a VNF for MYMONTH, the fiscal year that starts on April 1, 1995 and ends on March 31, 1996 is identified as 1996. When you use the `FFB` code, this fiscal year is identified as 1995.

Fiscal Years for Dimensions of Type DAY

For a dimension of type DAY, the fiscal year is identical to the calendar year.

Out-of-Range Years in a VNF

When a VNF specifies a `YY`, `YYB`, `FF`, or `FFB` format, and a year outside the range of 1950 to 2049 is to be displayed, the year is displayed in four digits. You must also supply all four digits when you enter the year as input.

Coding VNFs to Prevent Ambiguity

A VNF template must allow you to input dimension values unambiguously. To prevent ambiguity, you must observe the following restrictions when you code a VNF template:

- You cannot place a letter (either in a component code or in literal text) immediately after a text component of unspecified length (for example, `<MTEXT>`, which specifies a full month name of any length).

- You cannot place a digit (either in a component code or in literal text) immediately after a numeric component of unspecified length (for example, \<M\>, which can be one digit or two digits, or `<YY>`, which can be two digits or four digits).

Coding VNFs for Model Dimensions

When you define a model that contains equations based on a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, the VNF for the that dimension must specify dimension values with these format characteristics: the value must start with a letter, and it can contain only letters, digits, underscores, and periods.

Entering Dimension Values

Once you have assigned a VNF to a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, you cannot use the default VNF for entering values for that dimension. You must enter values in the format of your VNF or as dates.

Entering Dimension Values in VNF Format

When you enter dimension values in a VNF format, you have the following flexibility:

- Letters (either in a component or in literal text) can be either uppercase or lowercase, rather than matching the exact capitalization indicated by the VNF.

- When the template specifies `<MTXT>` or `<MTXTL>`, which indicate the first three letters of the month name, you can include as much of the month name as you want, from the first three letters to the full month name. When the template specifies `<MTEXT>` or `<MTEXTL>`, which indicate a month name of indeterminate length, you can include as much of the name as you want, from the first letter to the full month name. In all cases, however, you must provide enough letters to uniquely match a name in the MONTHNAMES option. For example, to distinguish April from August, you must type at least the first two letters of these names.

- You can include as many or as few spaces as you want between components or between text elements in a dimension value.

- When the template contains date components that are not essential for identifying a time period for a particular dimension, you can specify any date that falls within the desired time period. For example, the `<DD>` component of the template `<DD><MTXT><YY>` is not essential for identifying a period in a MONTH dimension. Therefore, for June 1995 you can specify any date from `01JUN95` through `30JUN95`.

Entering Dimension Values as Dates

When you enter a value of a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR as a date, you can use any of the input styles listed in the DATEORDER entry. When you specify a full date, Oracle OLAP uses the DATEORDER option to resolve any ambiguities. However, you must specify only the date components that are relevant for the type of dimension you are using:

- For a DAY or WEEK dimension, you must enter all the components (day, month, and year).

- For a MONTH or QUARTER dimension, you must only enter the month and year components. When you enter an ambiguous value, such as `'0106'`, Oracle OLAP uses the first two characters of the DATEORDER option to resolve the ambiguity. Therefore, the DATEORDER option must be `MYD` or `YMD` in this situation.

- For a YEAR dimension, you must only enter the year.

Overriding a VNF

For additional flexibility in displaying the values of a dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR, you can override the dimension's VNF (and the default VNF when the dimension has no VNF of its own) by using the CONVERT function with a VNF argument.

The VNF argument to CONVERT enables you to include all the template codes that are permitted in the template for a VNF statement, but it does not prevent you from specifying too few components or more components than are necessary for identifying a value. In addition, the VNF argument enables you to use additional codes that are not allowed in the VNF template.

#### Examples

Example 10-173 Assigning a VNF for a Dimension of Type MONTH

The following statements provide a VNF for the existing dimension of type MONTH named `month`.

    CONSIDER month
    VNF <mtextl>, <yyyy>

Example 10-174 Adding Values to a Dimension of Type Month

The following statements add dimension values in the style of the new VNF, using just enough letters to distinguish the month names rather than the full names that the `<MTEXTL>` code in the VNF specifies.

    MAINTAIN month ADD 'JA, 1995' 'MAR, 1995'
    Limit month TO LAST 3
    REPORT month

These statements produce the following output.

    MONTH
    --------------
    January, 1995
    February, 1995
    March, 1995

Note that Oracle OLAP automatically adds the time periods between the ones you specify in the MAINTAIN statement.

Example 10-175 Assigning a VNF for WEEK

The following statements define a dimension of type WEEK named `week`, add a VNF to the `week` definition, and add values to the `week` dimension.

    DEFINE week DIMENSION WEEK
    VNF Week <p>.<ff>
    MAINTAIN week ADD '01JAN95' '30JAN95'
    REPORT week

These statements produce the following output.

    WEEK
    --------------
    Week 1.95
    Week 2.95
    Week 3.95
    Week 4.95
    Week 5.95

When you use a MAINTAIN statement to add values to the `week` dimension, you can specify the new values as dates rather than as values that conform to the VNF. However, the VNF is used for displaying output in the desired format.

### 10.74 WHILE

The WHILE command repeatedly executes a statement while the value of a Boolean expression remains `TRUE`. You can only use WHILE within a program.

#### Syntax

WHILE boolean-expression     statement block

#### Parameters

boolean-expression
Serves as the criterion for statement execution. While the expression remains `TRUE`, statement is repeatedly executed. When the expression becomes `FALSE`, the execution of statement ceases, and the program continues with the next line. Ensure that something in the statement (or statements) eventually causes the Boolean expression to become `FALSE`; otherwise, the code becomes an endless loop.

statement block
One or more statements to be executed while the Boolean expression is `TRUE`. You can execute two or more statements by enclosing them within DO ... DOEND brackets. The DO statement should follow immediately after the WHILE statement.

#### Usage Notes

WHILE Compared to IF

The WHILE statement's main use is as an alternative to the IF...THEN...ELSE comand.When you want one or more statements in your program to execute repeatedly while a Boolean expression remains `TRUE`, you use WHILE. When you want them to execute only once when a Boolean expression is `TRUE`, you use IF.

Boolean Constant

You can specify a constant for the Boolean expression. When your statement is WHILE TRUE, make sure to include a BREAK, RETURN, or EXIT statement between DO ... DOEND so the program can finish the loop.

Branching in a Loop

You can use the BREAK, CONTINUE, and GOTO commands to branch within, or out of, a WHILE loop, thereby altering the sequence of statement execution.

#### Examples

Example 10-176 Using a WHILE Loop in a Program

In the following program lines, the statements following DO are executed when the Boolean expression `count` `LT` `10` is `TRUE`. Within the loop, the code searches for an instance of some condition and, when it finds one, it adds `1` to `count`. When `count` reaches `10`, the loop ends. The code in the loop must ensure that `count` will, at some time, reach `10`. Otherwise, the loop never ends.

    WHILE count LT 10
       DO
        ..." (statements)
        IF ....
          count = count + 1
       DOEND

### 10.75 ZEROTOTAL

The ZEROTOTAL command resets one or all subtotals of specified report columns to zero. You use the ZEROTOTAL command when you produce reports with the ROW command.

**Note:**

ZEROTOTAL affects the results returned by the RUNTOTAL and SUBSTR functions.

#### Syntax

ZEROTOTAL \[{n\|ALL} \[column1 columnN\]\]

#### Parameters

ZEROTOTAL with no arguments resets all subtotals in all columns to zero.

n
An `INTEGER` expression that specifies one of the 32 subtotals (1 to 32) Oracle OLAP accumulates for each numeric column in a report. For the specified columns, this subtotal is set to zero.

ALL
Sets all 32 subtotals to zero for the specified columns. ALL is the default when there are no arguments. To reset all the subtotals to zero for specific columns, you must include ALL in the statement.

    ZEROTOTAL ALL 1 4 7

column
The column number of a report column. Column number 1 refers to the left-most column in a report, regardless of the type of data it contains. When you do not supply any column number arguments, Oracle OLAP sets the specified subtotal (or all subtotals) to zero for all the columns in the report.

#### Usage Notes

Initializing Column Subtotals

When you use the ROW command to produce a report, use a ZEROTOTAL statement at the beginning of the report program to initialize all 32 subtotals for all columns to zero. The REPORT statement automatically resets all subtotals to zero before producing output.

Resetting Column Subtotals

You can also use ZEROTOTAL in a report program when you only want to reset some subtotals or when you want to start accumulating new subtotals without inserting the subtotals accumulated so far. A subtotal is automatically reset to zero after it is accessed with the SUBSTR function in its own column. However, a subtotal is not reset to zero after it is accessed with the RUNTOTALRUNTOTAL function.

#### Examples

Example 10-177 Resetting All Report Column Subtotals

In a report, you want to show a dollar sales total, followed by a detailed summary of unit sales for each district. You also want to show a total for unit sales at the end of the report, but you do not want the dollar sales figures included in that total. After generating the total dollar sales, use ZEROTOTAL to reset all your subtotals to zero. Then when you use `SUBTOTAL(1)` later in the report, it only totals the unit sales for each district.

Suppose you have these statement lines in your program.

    LIMIT product TO 'Footwear'
    LIMIT month TO 'Jul96' TO 'Sep96'
    ROW 'Total Dollar Sales' ACROSS month: -
       DECIMAL 0 TOTAL(sales month)
    BLANK
    ROW 'Unit Sales'
    ZEROTOTAL ALL
    FOR district
       ROW INDENT 5 district ACROSS month: units
    ROW 'Total Unit Sales' ACROSS month: -
       OVER '-' SUBTOTAL(1)

These statements produce the following output.

    Total Dollar Sales      607,552    581,229    658,850
     
    Unit Sales
         Boston               3,538      3,369      3,875
         Atlanta              4,058      3,866      4,251
         Chicago              3,943      3,509      4,058
         Dallas                 814        824        867
         Denver               1,581      1,532      1,667
         Seattle              2,053      2,193      2,617
                         ---------- ---------- ----------
    Total Unit Sales      15,987.00  15,293.00  17,335.00
