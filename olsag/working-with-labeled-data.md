You can manage labeled data, view that data of security attributes for a session, and change the value of session attributes.

**Note:**

Many of the examples in this guide use the `HUMAN_RESOURCES` sample policy. Its policy name is `HR` and its policy label column is `HR_LABEL`. Unless otherwise noted, the examples assume that the SQL statements are performed on rows within the user's authorization and with full Oracle Label Security policy enforcement in effect.

- How Policy Label Column and Label Tags Work
  You should understand how policy label columns in a table or schema are created and filled.
- Assignments of Labels to Data Rows
  For existing data rows, labels can be assigned by a labeling function that you create.
- Presenting the Label
  When you retrieve labels, you do not automatically obtain the character string value.
- Filtration of Data Using Labels
  When SQL statements are processed, Oracle Label Security makes calls to the security policies defined in the database by create-and-apply procedures.
- Inserting Labeled Data
  You can insert labeled data in a variety of situations.
- Changing Session and Row Labels
  During a session, a user can change labels based on the authorizations an administrator sets.

**Parent topic:** [Using Oracle Label Security Functionality](part2.md)

### 6.1 How Policy Label Column and Label Tags Work

You should understand how policy label columns in a table or schema are created and filled.

- The Policy Label Column
  You should understand how to use policy label columns.
- Label Tags
  You can create label tags, either manually or automatically generating them, that define the label components.

**Parent topic:** Working with Labeled Data

#### 6.1.1 The Policy Label Column

You should understand how to use policy label columns.

- About the Policy Label Column
  Each policy that is applied to a table creates a column in the database.
- Hiding the Policy Label Column
  You can choose not to display the column representing a policy.

**Parent topic:** How Policy Label Column and Label Tags Work

##### 6.1.1.1 About the Policy Label Column

Each policy that is applied to a table creates a column in the database.

By default, the data type of the `NUMBER`.

Each row's label for that policy is represented by a tag in that column, using the numeric equivalent of the character-string label value. The label tag is automatically generated when the label is created, unless the administrator specifies the tag manually at that time.

The automatic label generation follows the rules established by the administrator while defining the label components, as described in [Understanding Data Labels and User Labels](understanding-data-labels-and-user-labels.md).

**Note:**

The act of creating a policy does not in itself have any effect on tables or schemas. It only applies the policy to a table or schema.

**Parent topic:** The Policy Label Column

##### 6.1.1.2 Hiding the Policy Label Column

You can choose not to display the column representing a policy.

**Note:**

You cannot hide columns in materialized views.

- To hide the display of a column, apply the `HIDE` option to the table.
  After a policy using `HIDE` is applied to a table, a user running a `SELECT *` or performing a `DESCRIBE` operation will not see the policy label column. If the policy label column is not hidden, then the label tag is displayed as data type `NUMBER`.
  The following example shows the output of the `EMP` table, with the `HR_LABEL` column showing:

      DESCRIBE EMP;
       Name                                      Null?    Type
       ----------------------------------------- -------- --------
       EMPNO                                     NOT NULL NUMBER(4)
       ENAME                                              CHAR(10)
       JOB                                                CHAR(9)
       MGR                                                NUMBER(4)
       SAL                                                NUMBER(7,2)
       DEPTNO                                    NOT NULL NUMBER(2)
       HR_LABEL                                           NUMBER(10)

  Here is how the same table appears with the `HR_LABEL` column hidden:

      DESCRIBE EMP;
       Name                                      Null?    Type
       ----------------------------------------- -------- --------
       EMPNO                                     NOT NULL NUMBER(4)
       ENAME                                              CHAR(10)
       JOB                                                CHAR(9)
       MGR                                                NUMBER(4)
       SAL                                                NUMBER(7,2)
       DEPTNO                                    NOT NULL NUMBER(2)

**Related Topics**

- [How the HIDE Policy Column Option Works](implementing-policy-enforcement-options-and-labeling-functions.md)

**Parent topic:** The Policy Label Column

#### 6.1.2 Label Tags

You can create label tags, either manually or automatically generating them, that define the label components.

- About Label Tags
  The administrator first defines a set of label components to be used in a policy.
- Manually Defined Label Tags to Order Labels
  By manually defining label tags, you can implement a data manipulation strategy that permits labels to be meaningfully sorted and compared.
- Manually Defined Label Tags to Manipulate Data
  An administratively defined label tag is a convenient way to reference a complete label string (that is, a combination of label components).
- Automatically Generated Label Tags
  Dynamically generated label tags have 10 digits, with no relationship to numbers assigned to any label component.

**Parent topic:** How Policy Label Column and Label Tags Work

##### 6.1.2.1 About Label Tags

The administrator first defines a set of label components to be used in a policy.

When creating labels, the administrator specifies the set of valid combinations of components that can make up a label, that is, a level optionally combined with one or more groups or compartments.

Each such valid label within a policy is uniquely identified by an associated numeric tag assigned by the administrator or generated automatically upon its first use. Manual definition has the advantage of allowing the administrator to control the ordering of label values when they are sorted or logically compared.

However, label tags must be unique across all policies in the database. When you use multiple policies in a database, you cannot use the same numeric label tag in different policies. Remember that each label tag uniquely identifies one label, and that numeric tag is what is stored in the data rows, not the label's character-string representation.

**Parent topic:** Label Tags

##### 6.1.2.2 Manually Defined Label Tags to Order Labels

By manually defining label tags, you can implement a data manipulation strategy that permits labels to be meaningfully sorted and compared.

To do this, you must predefine all of the labels to be associated with protected data, and assigns to each label a meaningful label tag value. Manually assigned label tags can have up to eight digits. The value of a label tag must be greater than zero.

It may be advantageous to implement a strategy in which label tag values are related to the numeric values of label components. In this way, you can use the tags to group data rows in a meaningful way. This approach, however, is not mandatory. It is good practice to set tags for labels of higher sensitivity to a higher numeric value than tags for labels of lower sensitivity.

Table 6-1 illustrates a set of label tags that have been assigned. Notice that, in this example, the administrator has based the label tag value on the numeric form of the levels, compartments, and rows that were discussed in [Understanding Data Labels and User Labels](understanding-data-labels-and-user-labels.md).

Table 6-1 Administratively Defined Label Tags (Example)

| Label Tag | Label String |
|:----------|:-------------|
| 10000     | P            |
| 20000     | C            |
| 21000     | C:FNCL       |
| 21100     | C:FNCL,OP    |
| 30000     | S            |
| 31110     | S:OP:WR      |
| 40000     | HS           |
| 42000     | HS:OP        |

In this example, labels with a level of `PUBLIC` begin with "1", labels with a level of `CONFIDENTIAL` begin with "2", labels with a level of `SENSITIVE` begin with "3", and labels with a level of `HIGHLY_SENSITIVE` begin with "4".

Labels with the `FINANCIAL` compartment then come in the 1000 range, labels with the compartment `OP` are in the 1100 range, and so on. The tens place is used to indicate the group `WR`, for example.

Another strategy might be completely based on groups, where the tags might be 3110, 3120, 3130, and so on.

Note, however, that label tags identify the whole label, independent of the numeric values assigned for the individual label components. The label tag is used as a whole integer, not as a set of individually evaluated numbers.

**Parent topic:** Label Tags

##### 6.1.2.3 Manually Defined Label Tags to Manipulate Data

An administratively defined label tag is a convenient way to reference a complete label string (that is, a combination of label components).

As illustrated in Table 6-1, for example, the tag "31110" could stand for the complete label string "S:OP:WR".

Label tags can be used as a convenient way to partition data. For example, all data with labels in the range 1000 - 1999 could be placed in tablespace A, all data with labels in the range 2000 - 2999 could be placed in tablespace B, and so on.

This simplified notation also comes in handy when there is a finite number of labels and you need to perform various operations upon them. Consider a situation in which one company hosts a human resources system for many other companies. Assume that all users from Company Y have the label "C:ALPHA:CY", for which the tag "210" has been set. To determine the total number of application users from Company Y, the host administrator can enter:

    SELECT * FROM tab1
      WHERE hr_label = 210;

**Parent topic:** Label Tags

##### 6.1.2.4 Automatically Generated Label Tags

Dynamically generated label tags have 10 digits, with no relationship to numbers assigned to any label component.

You cannot group the data by label.

Table 6-2 describes how automatically generated label tags work.

Table 6-2 Generated Label Tags (Example)

| Label Tag   | Label String |
|:------------|:-------------|
| `100000020` | `P`          |
| `100000052` | `C`          |
| `100000503` | `C:FNCL`     |
| `100000132` | `C:FNCL,OP`  |
| `100000003` | `S`          |
| `100000780` | `S:OP:WR`    |
| `100000035` | `HS`         |
| `100000036` | `HS:OP`      |

**Parent topic:** Label Tags

### 6.2 Assignments of Labels to Data Rows

For existing data rows, labels can be assigned by a labeling function that you create.

In such a function, you specify the exact table and row conditions defining what label to insert. The function can be named in the call to apply a policy to a table or schema, or in an update by the administrator.

**Related Topics**

- Inserting Labeled Data
- [Labeling Functions](implementing-policy-enforcement-options-and-labeling-functions.md)
- [SA_POLICY_ADMIN.APPLY_TABLE_POLICY](oracle-label-security-pl-sql-packages.md)
- [SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Working with Labeled Data

### 6.3 Presenting the Label

When you retrieve labels, you do not automatically obtain the character string value.

By default, the label tag value is returned. Two label manipulation functions enable you to convert the label tag value to and from its character string representation.

- Converting a Character String to a Label Tag with CHAR_TO_LABEL
  The `CHAR_TO_LABEL` function converts character strings to a label tag, returning the label tag for the specified character string.
- Conversion of a Label Tag to a Character String, with LABEL_TO_CHAR
  You can convert label tags to character strings.

**Parent topic:** Working with Labeled Data

#### 6.3.1 Converting a Character String to a Label Tag with CHAR_TO_LABEL

The `CHAR_TO_LABEL` function converts character strings to a label tag, returning the label tag for the specified character string.

- To convert a character string to a label tab, use the following syntax for the `CHAR_TO_LABEL` function:

      FUNCTION CHAR_TO_LABEL (
           policy_name     IN VARCHAR2,
           label_string    IN VARCHAR2)
      RETURN NUMBER;

For example:

    INSERT INTO emp (empno,hr_label)
    VALUES (999, CHAR_TO_LABEL('HR','S:A,B:G5');

Here, `HR` is the label policy name, `S` is a sensitivity level, `A,B` compartments, and `G5` a group.

    FUNCTION CHAR_TO_LABEL (
         policy_name     IN VARCHAR2,
         label_string    IN VARCHAR2)
    RETURN NUMBER;

Here, `HR` is the label policy name, `S` is a sensitivity level, `A,B` compartments, and `G5` a group.

**Parent topic:** Presenting the Label

#### 6.3.2 Conversion of a Label Tag to a Character String, with LABEL_TO_CHAR

You can convert label tags to character strings.

- Converting a Label Tag to a Character String with LABEL_TO_CHAR
  The `LABEL_TO_CHAR` function returns a `VARCHAR2` string when it converts a label tag to a character string.
- LABEL_TO_CHAR Examples
  Oracle provides examples that illustrate the use of `LABEL_TO_CHAR`.
- Retrieving All Columns from a Table When the Policy Label Column Is Hidden
  If the policy label column is hidden, then it is not automatically returned when you execute `SELECT *` on the table.

**Parent topic:** Presenting the Label

##### 6.3.2.1 Converting a Label Tag to a Character String with LABEL_TO_CHAR

The `LABEL_TO_CHAR` function returns a `VARCHAR2` string when it converts a label tag to a character string.

When you query a table or view, you automatically retrieve all of the rows in the table or view that satisfy the qualifications of the query and are dominated by your label. If the policy label column is not hidden, then the label tag value for each row is displayed. You must use the `LABEL_TO_CHAR` function to display the character string value of each label.

Note that all conversions must be explicit. There is no automatic casting to and from tag and character string representations.

- To convert a label tag to a character string, use the following syntax for the `LABEL_TO_CHAR` function:

      FUNCTION LABEL_TO_CHAR (
           label IN NUMBER)
      RETURN VARCHAR2;

**Parent topic:** Conversion of a Label Tag to a Character String, with LABEL_TO_CHAR

##### 6.3.2.2 LABEL_TO_CHAR Examples

Oracle provides examples that illustrate the use of `LABEL_TO_CHAR`.

##### Example: Retrieving a Row Label from a Table or a View

To retrieve the label of a row from a table or view, specify the policy label column in the `SELECT` statement.

For example:

    SELECT label_to_char (hr_label) AS label, ename FROM tab1;
      WHERE ename = 'RWRIGHT';

This statement returns the following:

    LABEL          ENAME
    ------------   ----------
    S:A,B:G1       RWRIGHT

##### Example: Retrieving a Policy Label Column

You can also specify the policy label column in the `WHERE` clause of a `SELECT` statement.

The following statement displays all rows that have the policy label `S:A,B:G1`

    SELECT label_to_char (hr_label) AS label,ename FROM emp
      WHERE hr_label = char_to_label ('HR', 'S:A,B:G1');

This statement returns the following:

    LABEL           ENAME
    -------------   ---------
    S:A,B:G1        RWRIGHT
    S:A,B:G1        ESTANTON

Alternatively, you could use a more flexible statement to look up data that contains the string "S:A,B:G1" anywhere in the text of the `HR_LABEL` column:

    SELECT label_to_char (hr_label) AS label,ename FROM emp
      WHERE label_to_char (hr_label) like '%S:A,B:G1%';

If you do not use the `LABEL_TO_CHAR` function, then you will see the label tag.

##### Example: Retrieving a Numeric Column Data Type

The following example is with the numeric column data type (`NUMBER`) and dynamically generated label tags, but without using the `LABEL_TO_CHAR` function. If you do not use the `LABEL_TO_CHAR` function, then you will see the label tag.

    SQL> select empno, hr_label from emp
         where ename='RWRIGHT';

    EMPNO      HR_LABEL
    ---------- ----------
    7839       1000000562

**Parent topic:** Conversion of a Label Tag to a Character String, with LABEL_TO_CHAR

##### 6.3.2.3 Retrieving All Columns from a Table When the Policy Label Column Is Hidden

If the policy label column is hidden, then it is not automatically returned when you execute `SELECT *` on the table.

- To explicitly specify that you want to retrieve a label, use the `LABEL_TO_CHAR` function in the `SELECT` statement.

For example, to retrieve all columns from the `DEPT` table (including the policy label column in its character representation), enter the following:

    COLUMN LABEL FORMAT a10
    SELECT LABEL_TO_CHAR (hr_label) AS LABEL, DEPT.* FROM DEPT;

Running these SQL statements returns the following data:

Table 6-3 Data Returned from Sample SQL Statements re Hidden Column

| LABEL | DEPTNO | DNAME        | LOC        |
|:------|:-------|:-------------|:-----------|
| `L1`  | `10`   | `ACCOUNTING` | `NEW YORK` |
| `L1`  | `20`   | `RESEARCH`   | `DALLAS`   |
| `L1`  | `30`   | `SALES`      | `CHICAGO`  |
| `L1`  | `40`   | `OPERATIONS` | `BOSTON`   |

By contrast, if you do not explicitly specify the `HR_LABEL` column, the label is not displayed at all. Note that while the policy column name is on a policy basis, the `HIDE` option is on a table-by-table basis.

**Related Topics**

- [How the HIDE Policy Column Option Works](implementing-policy-enforcement-options-and-labeling-functions.md)

**Parent topic:** Conversion of a Label Tag to a Character String, with LABEL_TO_CHAR

### 6.4 Filtration of Data Using Labels

When SQL statements are processed, Oracle Label Security makes calls to the security policies defined in the database by create-and-apply procedures.

For `SELECT` statements, the policy filters the data rows that the user is authorized to see. For `INSERT`, `UPDATE`, and `DELETE` statements, Oracle Label Security permits or denies the requested operation, based on the user's authorizations.

- Use of Numeric Label Tags in WHERE Clauses
  There are different techniques of using numeric label tags in `WHERE` clauses of `SELECT` statements.
- Ordering Labeled Data Rows
  The `ORDER BY` clause of a `SELECT` statement can be used to order rows by the numeric label tag.
- Ordering by Character Representation of Label
  The `LABEL_TO_CHAR` function orders data rows by the character representation of the label.
- Determination of the Upper and Lower Bounds of Labels
  Oracle Label Security provides functions that determine the least upper bound or the greatest lower bound of two or more labels.
- Merging Labels with the MERGE_LABEL Function
  The `MERGE_LABEL` function merges two labels together.

**Parent topic:** Working with Labeled Data

#### 6.4.1 Use of Numeric Label Tags in WHERE Clauses

There are different techniques of using numeric label tags in `WHERE` clauses of `SELECT` statements.

When using labels in the `NUMBER` format, you can set up labels so that a list of your label tags distinguishes the different levels. Comparisons of these numeric label tags can be used for `ORDER BY` processing, and with the logical operators.

For example, if you have assigned all `UNCLASSIFIED` labels to the 1000 range, all `SENSITIVE` labels to the 2000 range, and all `HIGHLY_SENSITIVE` labels to the 3000 range, then you can list all `SENSITIVE` records.

    SELECT * FROM emp
    WHERE hr_label BETWEEN 2000 AND 2999;

To list all `SENSITIVE` and `UNCLASSIFIED` records, you can enter:

    SELECT * FROM emp
    WHERE hr_label <3000;

To list all `HIGHLY_SENSITIVE` records, you can enter:

    SELECT * FROM emp
    WHERE hr_label=3000;

**Note:**

Remember that such queries have meaning only if the administrator has applied a numeric ordering strategy to the label tags that he or she originally assigned to the labels. In this way, the administrator can provide for convenient dissemination of data. If, however, the label tag values are generated automatically, then there is no intrinsic relationship between the value of the tag and the order of the labels.

Alternatively, you can use dominance relationships to set up an ordering strategy.

**Related Topics**

- [Using Dominance Functions](advanced-topics-in-oracle-label-security.md)

**Parent topic:** Filtration of Data Using Labels

#### 6.4.2 Ordering Labeled Data Rows

The `ORDER BY` clause of a `SELECT` statement can be used to order rows by the numeric label tag.

- To perform the `ORDER BY` operation, use a `SELECT` statement similar to the following:

      SELECT * from emp
      ORDER BY hr_label;

Notice that no functions were necessary in this statement. The statement made use of label tags set up by the administrator.

**Note:**

Again, such queries have meaning only if the administrator has applied a numeric ordering strategy to the label tags originally assigned to the labels.

**Parent topic:** Filtration of Data Using Labels

#### 6.4.3 Ordering by Character Representation of Label

The `LABEL_TO_CHAR` function orders data rows by the character representation of the label.

- To order data rows by the character representation of a label, use a statement similar to the following, which returns all rows sorted by the text order of the label :

      SELECT * FROM emp
      ORDER BY label_to_char (hr_label);

**Parent topic:** Filtration of Data Using Labels

#### 6.4.4 Determination of the Upper and Lower Bounds of Labels

Oracle Label Security provides functions that determine the least upper bound or the greatest lower bound of two or more labels.

Two single-row functions operate on each row returned by a query. They return one result for each row.

**Note:**

In all functions that take multiple labels, the labels must all belong to the same policy.

- Finding Least Upper Bound with LEAST_UBOUND
  The `OLS_LEAST_UBOUND` (`OLS_LUBD`) function returns a character string label that is the least upper bound of `label1` and `label2:`.
- Finding Greatest Lower Bound with GREATEST_LBOUND
  The `OLS_GREATEST_LBOUND` (`OLS_GLBD`) standalone function determines the lowest label of the data that can be involved in an operation, given two different labels.

**Parent topic:** Filtration of Data Using Labels

##### 6.4.4.1 Finding Least Upper Bound with LEAST_UBOUND

The `OLS_LEAST_UBOUND` (`OLS_LUBD`) function returns a character string label that is the least upper bound of `label1` and `label2:`.

That is, the one label that dominates both. The least upper bound is the highest level, the union of the compartments in the labels, and the union of the groups in the labels.

For example, the least upper bound of `HIGHLY_SENSITIVE:ALPHA` and `SENSITIVE:BETA` is `HIGHLY_SENSITIVE:ALPHA,BETA.`

- To find the least upper bound, use the following syntax:

      FUNCTION OLS_LEAST_UBOUND (
           label1                    IN NUMBER,
           label2                    IN NUMBER)
      RETURN VARCHAR2;

The `OLS_LEAST_UBOUND` function is useful when joining rows with different labels, because it provides a high water mark label for joined rows.

The following query compares each employee's label with the label of his or her department, and returns the higher label, whether it be in the EMP table or the DEPT table.

    SELECT ename,dept.deptno,
      OLS_LEAST_UBOUND(emp.hr_label,dept.hr_label) as label
      FROM emp, dept
      WHERE emp.deptno=dept.deptno;

This query returns the following data:

Table 6-4 Data Returned from Sample SQL Statements re Least_UBound

| ENAME    | DEPTNO | LABEL    |
|:---------|:-------|:---------|
| `KING`   | 10     | L3:M:D10 |
| `BLAKE`  | 30     | L3:M:D30 |
| `CLARK`  | 10     | L3:M:D10 |
| `JONES`  | 20     | L3:M:D20 |
| `MARTIN` | 30     | L2:E:D30 |

**Note:**

The old OLS functions, `LEAST_UBOUND` and `LUBD` have been deprecated in Oracle Database 12c release 1 (12.1).

You can still use the old functions in this release, but Oracle recommends that you use the `OLS_LEAST_UBOUND` and `OLS_LUBD` functions instead. Using the new function names avoids potential name conflicts with other database components.

**Parent topic:** Determination of the Upper and Lower Bounds of Labels

##### 6.4.4.2 Finding Greatest Lower Bound with GREATEST_LBOUND

The `OLS_GREATEST_LBOUND` (`OLS_GLBD`) standalone function determines the lowest label of the data that can be involved in an operation, given two different labels.

This function returns a character string label that is the greatest lower bound of `label1` and `label2.` The greatest lower bound is the lowest level, the intersection of the compartments in the labels and the groups in the labels. For example, the greatest lower bound of `HIGHLY_SENSITIVE:ALPHA` and `SENSITIVE` is `SENSITIVE.`

- To find the greatest lower bound, use the following syntax:

      FUNCTION OLS_GREATEST_LBOUND (
           label1                  IN NUMBER,
           label2                  IN NUMBER)
      RETURN VARCHAR2;

**Note:**

The old OLS functions, `GREATEST_LBOUND` and `GLBD` were deprecated in Oracle Database 12c release 1 (12.1).

You can still use the old functions in this release, but Oracle recommends that you use the `OLS_GREATEST_LBOUND` and `OLS_GLBD` functions instead. Using the new function names avoids potential name conflicts with other database components.

**Parent topic:** Determination of the Upper and Lower Bounds of Labels

#### 6.4.5 Merging Labels with the MERGE_LABEL Function

The `MERGE_LABEL` function merges two labels together.

It accepts the character string form of two labels and the three-character specification of a merge format.

- To merge labels, use the following syntax:

      FUNCTION merge_label (label1 IN number,
                            label2 IN number,
                            merge_format IN VARCHAR2)
      RETURN number;

The valid merge format is specified with a three-character string:

`<highest level or lowest level><union or intersection of compartments><union or intersection of groups>`

- The first character indicates whether to merge using the highest level or the lowest level of the two labels.

- The second character indicates whether to merge using the union or the intersection of the compartments in the two labels.

- The third character indicates whether to merge using the union or the intersection of the groups in the two labels.

Table 6-5 defines the `MERGE_LABEL` format constants.

Table 6-5 MERGE_LABEL Format Constants

| Format Specification | Data Type                | Constant | Meaning                                                                                                         | Positions in Which Format Is Used        |
|:---------------------|:-------------------------|:---------|:----------------------------------------------------------------------------------------------------------------|:-----------------------------------------|
| `max_lvl_fmt`        | `CONSTANT` `varchar2(1)` | `H`      | Maximum level                                                                                                   | First (level)                            |
| `min_lvl_fmt`        | `CONSTANT` `varchar2(1)` | `L`      | Minimum level                                                                                                   | First (Level)                            |
| `union_fmt`          | `CONSTANT` `varchar2(1)` | `U`      | Union of the two labels                                                                                         | Second (compartments) and Third (groups) |
| `inter_fmt`          | `CONSTANT` `varchar2(1)` | `I`      | Intersection of the two labels                                                                                  | Second (compartments) and Third (groups) |
| `minus_fmt`          | `CONSTANT` `varchar2(1)` | `M`      | Remove second label from first label                                                                            | Second (compartments) and Third (groups) |
| `null_fmt`           | `CONSTANT` `varchar2(1)` | `N`      | If specified in compartments column, returns no compartments. If specified in groups column, returns no groups. | Second (compartments) and Third (groups) |

For example, `HUI` specifies the highest level of the two labels, union of the compartments, intersection of the groups.

The `MERGE_LABEL` function is particularly useful to developers if the `LEAST_UBOUND` function does not provide the intended result. The `LEAST_UBOUND` function, when used with two labels containing groups, may result in a less sensitive data label than expected. The `MERGE_LABEL` function enables you to compute an intersection on the groups, instead of the union of groups that is provided by the `LEAST_UBOUND` function.

For example, if the label of one data record contains the group `UNITED_STATES`, and the label of another data record contains the group `UNITED_KINGDOM`, and the `LEAST_UBOUND` function is used to compute the least upper bound of these two labels, then the resulting label would be accessible to users authorized for either the `UNITED_STATES` or the `UNITED_KINGDOM`.

If, by contrast, the `MERGE_LABEL` function is used with a format clause of `HUI`, then the resulting label would contain the highest level, the union of the compartments, and no groups. This is because `UNITED_STATES` and `UNITED_KINGDOM` do not intersect.

**Parent topic:** Filtration of Data Using Labels

### 6.5 Inserting Labeled Data

You can insert labeled data in a variety of situations.

- About Inserting Labeled Data
  When you insert data into a table protected by an Oracle Label Security policy, you must supply a numeric label value tag.
- Inserting Labels Using CHAR_TO_LABEL
  To insert a row label, you can specify the label character string and then transform it into a label using the `CHAR_TO_LABEL` function.
- Inserting Labels Using Numeric Label Tag Values
  You can insert data using the numeric label tag value of a label, rather than using the `CHAR_TO_LABEL` function.
- Inserting Data Without Specifying a Label
  There are two situations in which you do not need to specify a label in `INSERT` statements.
- Inserting Data When the Policy Label Column Is Hidden
  If the label column is hidden, then the existence of the column is transparent to the insertion of data.
- Inserting Labels Using TO_DATA_LABEL
  The `TO_DATA_LABEL` function can generate new labels dynamically.

**Parent topic:** Working with Labeled Data

#### 6.5.1 About Inserting Labeled Data

When you insert data into a table protected by an Oracle Label Security policy, you must supply a numeric label value tag.

Usually, you can insert this value in the `INSERT` statement itself.

To do this, you must explicitly specify the tag for the desired label or explicitly convert the character string representation of the label into the correct tag. Note that this does not mean generating new label tags, but referencing the correct tag. When Oracle Label Security is using Oracle Internet Directory, the only permissible labels (and corresponding tags) are those pre-defined by the administrator and already in Oracle Internet Directory.

The only times an `INSERT` statement may omit a label value are:

- If the `LABEL_DEFAULT` enforcement option was specified when the policy was applied, or

- If no enforcement options were specified when the policy was applied and `LABEL_DEFAULT` was specified when the policy was created

- If the statement applying the policy named a labeling function.

In the first two cases, the user's session default row label is used as the inserted row's label. In the third case, the inserted row's label is created by that labeling function.

**Related Topics**

- [Labeling Functions](implementing-policy-enforcement-options-and-labeling-functions.md)
- [Implementing Policy Enforcement Options and Labeling Functions](implementing-policy-enforcement-options-and-labeling-functions.md)

**Parent topic:** Inserting Labeled Data

#### 6.5.2 Inserting Labels Using CHAR_TO_LABEL

To insert a row label, you can specify the label character string and then transform it into a label using the `CHAR_TO_LABEL` function.

The `CHAR_TO_LABEL` function automatically creates a valid data label.

- To insert labels, use an `INSERT INTO` statement.

Using the definition for table `emp`, the following example shows how to insert data with explicit labels:

    INSERT INTO emp (ename,empno,hr_label)
    VALUES ('ESTANTON',10,char_to_label ('HR', 'SENSITIVE'));

**Parent topic:** Inserting Labeled Data

#### 6.5.3 Inserting Labels Using Numeric Label Tag Values

You can insert data using the numeric label tag value of a label, rather than using the `CHAR_TO_LABEL` function.

- To insert labels using numeric label tag values, use an `INSERT INTO` statement.

For example, if the numeric label tag for `SENSITIVE` is 3000, it would appear as follows:

    INSERT INTO emp (ename, empno, hr_label)
    VALUES ('ESTANTON', 10, 3000);

**Parent topic:** Inserting Labeled Data

#### 6.5.4 Inserting Data Without Specifying a Label

There are two situations in which you do not need to specify a label in `INSERT` statements.

If `LABEL_DEFAULT` is set, or if there is a labeling function applied to the table, then you do not need to specify a label in your `INSERT` statements. The label will be provided automatically.

- To insert data without specifying a label, use an `INSERT INTO` statement.

For example:

    INSERT INTO emp (ename, empno)
    VALUES ('ESTANTON', 10);

The resulting row label is set according to the default value (or by a labeling function).

**Parent topic:** Inserting Labeled Data

#### 6.5.5 Inserting Data When the Policy Label Column Is Hidden

If the label column is hidden, then the existence of the column is transparent to the insertion of data.

`INSERT` statements can be written that do not explicitly list the table columns and do not include a value for the label column.

The session's row label is used to label the data, or a labeling function is used if one was specified when the policy was applied to the table or schema.

You can insert into a table without explicitly naming the columns, as long as you specify a value for each non-hidden column in the table. The following example shows how to insert a row into the table described in working-with-labeled-data.html#GUID-62D8E07A-EC69-4EF7-A0B4-5FC69B476152\_\_BEIIGDED:

- To insert data when the policy label column is hidden, use the following syntax:

      INSERT INTO emp
      VALUES ('196','ESTANTON',Technician,RSTOUT,50000,10);

Its label will be one of the following three possibilities:

- The label you specify

- The label established by the `LABEL_DEFAULT` option of the policy being applied

- The label created by a labeling function named by the policy being applied

  **Note:**

  If the policy label column is not hidden, then you must explicitly include a label value (possibly null, indicated by a comma) in the `INSERT` statement.

**Parent topic:** Inserting Labeled Data

#### 6.5.6 Inserting Labels Using TO_DATA_LABEL

The `TO_DATA_LABEL` function can generate new labels dynamically.

This approach guarantees that the data labels are valid. However, be aware that when Oracle Label Security is installed to work with Oracle Internet Directory, dynamic label generation is not allowed, because labels are managed centrally in Oracle Internet Directory, using `olsadmintool` commands. Therefore, when Oracle Label Security is directory-enabled, this function, `TO_DATA_LABEL`, is not available and will generate an error message if used.

1.  Ensure that you have the `EXECUTE` privilege on the `TO_DATA_LABEL` function.

2.  Use the `TO_DATA_LABEL` as necessary, for example, in an `INSERT INTO` statement.

For example:

    INSERT INTO emp (ename, empno, hr_label)
    VALUES ('ESTANTON', 10, to_data_label ('HR', 'SENSITIVE'));

**Note:**

The `TO_DATA_LABEL` function must be explicitly granted to individuals, in order to be used. Its usage should be tightly controlled.

**Related Topics**

- [Command-line Tools for Label Security Using Oracle Internet Directory](command-line-tools-for-label-security-using-oracle-internet-directory.md)

**Parent topic:** Inserting Labeled Data

### 6.6 Changing Session and Row Labels

During a session, a user can change labels based on the authorizations an administrator sets.

**Related Topics**

- [SA_SESSION Session Management PL/SQL Package](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Working with Labeled Data
