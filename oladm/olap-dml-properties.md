This chapter contains the following topics:

- About OLAP DML Properties

- System Properties: Alphabetical Listing

- System Properties by Category

- One topic for each of the OLAP DML system properties, arranged alphabetically beginning with \$AGGMAP.

For other reference topics for the OLAP DML, see [OLAP DML Options](olap-dml-options.md), [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), [OLAP DML Functions: A - K](olap-dml-functions-a-k.md), [OLAP DML Commands: A-G](olap-dml-commands-a-g.md), and [OLAP DML Commands: H-Z](olap-dml-commands-h-z.md).

### 4.1 About OLAP DML Properties

A property is a named value that is associated with a definition of an analytic workspace object. You can name, create, and assign properties to an object using an OLAP DML [PROPERTY](olap-dml-commands-h-z.md) command.

Properties that begin with a \$ (dollar sign) are recognized by Oracle OLAP as system properties. You cannot create system properties; however, in some cases you can assign system properties to objects. In particular, you can assign system properties that interact with the OLAP DML.

### 4.2 System Properties: Alphabetical Listing

- \$AGGMAP
- \$AGGREGATE_FORCECALC
- \$AGGREGATE_FORCEORDER
- \$AGGREGATE_FROM
- \$AGGREGATE_FROMVAR
- \$ALLOCMAP
- \$COUNTVAR
- \$DEFAULT_LANGUAGE
- \$GID_DEPTH
- \$GID_LIST
- \$GID_TYPE
- \$LOOP_AGGMAP
- \$LOOP_DENSE
- \$LOOP_TYPE
- \$LOOP_VAR
- \$NATRIGGER
- \$STORETRIGGERVAL
- \$VARCACHE

### 4.3 System Properties by Category

The OLAP DML provides system properties that set or retrieve values that influence how the OLAP DML performs the following:

- Aggregation Properties
- Allocation Property
- Grouping Id Properties
- Formula Properties
- Language Property
- NA Value Properties

#### Aggregation Properties

- \$AGGMAP
- \$AGGREGATE_FORCECALC
- \$AGGREGATE_FORCEORDER
- \$AGGREGATE_FROM
- \$AGGREGATE_FROMVAR
- \$COUNTVAR
- \$VARCACHE

#### Allocation Property

- \$ALLOCMAP

#### Grouping Id Properties

- \$GID_DEPTH
- \$GID_LIST
- \$GID_TYPE

#### Formula Properties

- \$LOOP_AGGMAP
- \$LOOP_DENSE
- \$LOOP_TYPE
- \$LOOP_VAR

#### Language Property

- \$DEFAULT_LANGUAGE

#### NA Value Properties

- \$NATRIGGER
- \$STORETRIGGERVAL
- \$VARCACHE

### 4.4 \$AGGMAP

The \$AGGMAP property specifies that Oracle OLAP use the identified aggmap to automatically aggregate non-precomputed data to substitute for NA values that are in the dimensioned variable, but not in the session cache for the variable (if any). Consequently, you do not need to explicitly use the AGGREGATE function to aggregate non-precomputed data in a variable that has an \$AGGMAP property.

Additionally, the aggmap specified in the \$AGGMAP property of a variable is the aggmap that Oracle OLAP uses when the variable is the target of an AGGREGATE command that does not include a USING phrase.

#### Syntax

You add or delete an \$AGGMAP property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$AGGMAP' agggmap-name

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$AGGMAP'

#### Parameters

aggmap-name
A `TEXT` expression that is the name of a previously defined aggmap object.

#### Examples

Example 4-1 Using \$AGGMAP To Dynamically Aggregate Data

Assume that you have a hierarchical dimension named `geog,`a simple dimension named `year`, and the following variable named `sales` which is dimensioned by both and which has data only at the detail level.

Assume that you want to explicitly specify the value of `8000` for the `sales` cell for Connecticut in 2005. To do this you issue the following assignment statement and a report of sales shows the value.

    sales (geog 'Connecticut' year '2005') = 8000
    REPORT sales;

                   -----------SALES-----------
                   -----------YEAR------------
    GEOG            2004   2005   2006   2007
    -------------- ------ ------ ------ ------
    Toronto         1,000  1,333  1,954  1,260
    Norfolk         1,131  1,867  1,843  1,767
    Montreal        1,571  1,754  1,316  1,905
    Quebec City     1,914  1,728  1,386  1,847
    Hartford        1,870  1,943  1,085  1,335
    New Haven       1,684  1,330  1,458  1,402
    Springfield     1,630  1,116  1,897  1,690
    Boston          1,780  1,310  1,368  1,581
    Ontario            NA     NA     NA     NA
    Quebec             NA     NA     NA     NA
    Connecticut        NA  8,000     NA     NA
    Massachusetts      NA     NA     NA     NA
    Canada             NA     NA     NA     NA
    USA                NA     NA     NA     NA
    All Geog           NA     NA     NA     NA

Now assume that you define an aggmap for `sales`. The aggmap has the following definition which specifies that only the upper-level data for Canada and the top level (`All Geog`) be aggregated by the AGGREGATE command.

    DEFINE MYAGGMAP AGGMAP
    AGGMAP
    RELATION geogParentrel PRECOMPUTE ('Quebec' 'Ontario' 'Canada' 'All Geog')
    END


Now assume you issue the following statements:

    CONSIDER sales
    PROPERTY '$AGGMAP' 'Myaggmap'


As a result of using the \$AGGMAP property to make `myaggmap` as the default aggmap for `sales`, a simple REPORT statement for `sales` causes Oracle OLAP to aggregate all of the data for the USA. (Note that only those values that were not specified as PRECOMPUTE and that previously had `NA` values are calculated. The 8,000 value for Connecticut in 2005 that was specifically assigned is not recalculated.)

    REPORT sales

                   -----------SALES-----------
                   -----------YEAR------------
    GEOG            2004   2005   2006   2007
    -------------- ------ ------ ------ ------
    Toronto         1,000  1,333  1,954  1,260
    Norfolk         1,131  1,867  1,843  1,767
    Montreal        1,571  1,754  1,316  1,905
    Quebec City     1,914  1,728  1,386  1,847
    Hartford        1,870  1,943  1,085  1,335
    New Haven       1,684  1,330  1,458  1,402
    Springfield     1,630  1,116  1,897  1,690
    Boston          1,780  1,310  1,368  1,581
    Ontario            NA     NA     NA     NA
    Quebec             NA     NA     NA     NA
    Connecticut     3,554  8,000  2,543  2,737
    Massachusetts   3,410  2,426  3,265  3,271
    Canada             NA     NA     NA     NA
    USA             6,964  5,699  5,808  6,008
    All Geog           NA     NA     NA     NA

Once you aggregate `sales` using the AGGREGATE command, Oracle OLAP aggregates values for all of the PRECOMPUTE cells in `sales`.

    REPORT sales

                   -----------SALES-----------
                   -----------YEAR------------
    GEOG            2004   2005   2006   2007
    -------------- ------ ------ ------ ------
    Toronto         1,000  1,333  1,954  1,260
    Norfolk         1,131  1,867  1,843  1,767
    Montreal        1,571  1,754  1,316  1,905
    Quebec City     1,914  1,728  1,386  1,847
    Hartford        1,870  1,943  1,085  1,335
    New Haven       1,684  1,330  1,458  1,402
    Springfield     1,630  1,116  1,897  1,690
    Boston          1,780  1,310  1,368  1,581
    Ontario         2,131  3,200  3,797  3,027
    Quebec          3,485  3,482  2,702  3,752
    Connecticut     3,554  8,000  2,543  2,737
    Massachusetts   3,410  2,426  3,265  3,271
    Canada          5,616  6,682  6,499  6,779
    USA             6,964  5,699  5,808  6,008
    All Geog       12,580 12,381 12,307 12,787

Example 4-2 The \$AGGMAP Property Effect on an AGGREGATE Command

\$AGGREGATE_FROM illustrates how the AGGREGATE command shown in [Example 9-13](olap-dml-commands-a-g.md) can be simplified to the following statement.

    AGGREGATE sales_by_revenue USING revenue_aggmap

You can further simplify the AGGREGATE command if you place an \$AGGMAP property on the `sales_by_revenue` variable. To define an \$AGGMAP property on the `sales_by_revenue` variable, issue the following statements.

    CONSIDER sales_by_revenue
    PROPERTY '$AGGMAP' 'revenue_aggmap'

Now you can aggregate the data by issuing the following AGGREGATE command that does not include a USING clause.

    AGGREGATE sales_by_revenue

### 4.5 \$AGGREGATE_FORCECALC

The \$AGGREGATE_FORCECALC property specifies the same behavior as that specified by the FORCECALC keyword in an AGGREGATE function. By adding an \$AGGREGATE_FORCECALC property to a variable you can ensure this behavior when the variable is aggregated using an AGGREGATE function, even when that function does not include the FORCECALC keyword.

The behavior specified by both the \$AGGREGATE_FORCECALC property and the FORCECALC keyword is that when an AGGREGATE function aggregates the variable, Oracle OLAP recalculates any value that is not specified in a PRECOMPUTE clause of a RELATION (for aggregation) statement in the aggmap of a variable, even when there is a value stored in the desired cell. Recalculating values that are not specified in a PRECOMPUTE clause is the desired behavior when you want users to be able to change detail data cells and see the changed values reflected in dynamically-computed aggregate cells.

#### Syntax

You add or delete an \$AGGREGATE_FORCECALC property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) by issuing a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$AGGREGATE_FORCECALC' 

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$AGGREGATE_FORCECALC'

### 4.6 \$AGGREGATE_FORCEORDER

The \$AGGREGATE_FORCEORDER property specifies the same behavior as that specified by the FORCEORDER keyword in an AGGREGATE command or an AGGREGATE function. By adding an \$AGGREGATE_FORCEORDER property to a variable you can ensure this behavior when the variable is aggregated, even when it is aggregated by an AGGREGATE statement does not include the FORCEORDER keyword.

The behavior specified by both the \$AGGREGATE_ORDER property and the FORCEORDER keyword is that the calculations must be performed in the order in which the RELATION (for aggregation) statements are listed in the aggmap used for the aggregation. Typically, you want this behavior when some values calculated through aggregation have changed because, otherwise, the optimization methods used by AGGREGATE may cause the modified values to be ignored. (Note, however, that forcing the order of execution can slow performance.)

#### Syntax

You add or delete an \$AGGREGATE_FORCEORDER property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) by issuing a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$AGGREGATE_FORCEORDER' 

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$AGGREGATE_FORCEORDER'

### 4.7 \$AGGREGATE_FROM

The \$AGGREGATE_FROM property specifies the same behavior as that specified by a FROM clause in an AGGREGATE command or an AGGREGATE function. By adding an \$AGGREGATE_FROM property to a variable you can ensure this behavior when the variable is aggregated, even when it is aggregated by an AGGREGATE statement does not include the FROM clause.

Both the \$AGGREGATE_FROM property and the FROM clause specify an object from which Oracle OLAP obtains the detail data for the aggregation.

**Note:**

[OLAP DML Commands: A-G](olap-dml-commands-a-g.md)

#### Syntax

You add or delete an \$AGGREGATE_FROM property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) by issuing a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$AGGREGATE_FROM' fromspec

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$AGGREGATE_FROM'

#### Parameters

fromspec
An arbitrarily dimensioned variable, formula, or relation from which the detail data for the aggregation is obtained.

#### Examples

Example 4-3 Using the \$AGGREGATE_FROM Property

[Example 9-15](olap-dml-commands-a-g.md) uses the following AGGREGATE command to populate the `total_sales_exclud_north` variable with aggregate values computed from the `sales` variable.

    AGGREGATE total_sales_exclud_north USING agg_sales_exclud_north FROM sales

You can place a \$AGGREGATE_FROM property on the `total_sales_exclud_north` variable by issuing the following statements.

    CONSIDER total_sales_exclud_north
    PROPERTY '$AGGREGATE_FROM' 'sales'

Now you can aggregate the data by issuing the following AGGREGATE command that does not include a FROM clause.

    AGGREGATE total_sales_exclud_north USING agg_sales_exclud_north

### 4.8 \$AGGREGATE_FROMVAR

The \$AGGREGATE_FROMVAR property specifies the same behavior as that specified by a FROMVAR clause in an AGGREGATE command or an AGGREGATE function. By adding an \$AGGREGATE_FROMVAR property to a variable you can ensure this behavior when the variable is aggregated, even when it is aggregated by an AGGREGATE statement that does not include the FROMVAR clause.

Both the \$AGGREGATE_FROMVAR property and the FROMVAR clause specify two or more objects from which Oracle OLAP obtains the detail data for the aggregation.

**Note:**

[OLAP DML Commands: A-G](olap-dml-commands-a-g.md)

#### Syntax

You add or delete an \$AGGREGATE_FROMVAR property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) by issuing a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$AGGREGATE_FROMVAR' textvar ACROSS dimname

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$AGGREGATE_FROMVAR'

#### Parameters

textvar
A `TEXT` expression that specifies an arbitrarily dimensioned variable or formula that specifies the names of the objects from which to obtain detail data when performing a capstone aggregation. Specify `NA` to indicate that a node does not need detail data to calculate the value.

ACROSS dimname
Specifies the dimension or a named composite that the aggregation loops over to discover the cells in the objects specified by textvar. Because the objects specified by textvar can be formulas, you can realize a significant performance advantage by supplying a looping dimension that eliminates the sparsity.

#### Examples

Example 4-4 Capstone Aggregation Using the \$AGGREGATE_FROMVAR Property

[Example 9-32](olap-dml-commands-a-g.md) uses the following AGGREGATE command to perform the final capstone aggregation.

    AGGREGATE sales_capstone76 USING capstone_aggmap FROMVAR capstone_source

As the following statements illustrate, you can omit the FROMVAR clause if you create the appropriate FROMVAR property on `sales-capstone76`.

    CONSIDER sales_capstone76
    PROPERTY '$AGGREGATE_FROMVAR'  'capstone_source'
    AGGREGATE sales_capstone76 USING capstone_aggmap

### 4.9 \$ALLOCMAP

The \$ALLOCMAP property specifies the default aggmap for allocation for a variable which is the aggmap that Oracle OLAP uses when the variable is the target variable of an ALLOCATE statement that does not include a USING phrase.

#### Syntax

You add or delete an \$ALLOCMAP property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$ALLOCMAP' aggmap-name

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$AALLOCMAP'

#### Parameters

aggmap-name
A `TEXT` expression that specifies the name of a previously defined ALLOCMAP type aggmap object.

#### Examples

Example 4-5 Using \$ALLOCMAP to Specify a Default Allocation Specification

The following statement allocates data in the `projbudget` variable using the `projbudgmap` allocation specification.

    ALLOCATE projbudget USING projbudgmap

You can specify that `projbudgmap` is the default allocation specification for the `projbudget` variable by issuing the following statements.

    CONSIDER projbudget
    PROPERTY '$ALLOCMAP' "projbugmap'

Now, by issuing the following statement, you can allocate data in the `projbudget` variable using the `projbudgmap` allocation specification.

    ALLOCATE projbudget

For other examples of using the \$ALLOCMAP property, see the ALLOCATE command.

### 4.10 \$COUNTVAR

The \$COUNTVAR property specifies the same behavior as that specified by a COUNTVAR clause in an AGGREGATE command or an AGGREGATE function. By adding an \$COUNTVAR property to a variable you can ensure this behavior when the variable is aggregated, even when it is aggregated by an AGGREGATE statement does not include the COUNTVAR clause.

The behavior specified by both the \$COUNTVAR property and the COUNTVAR clause is that Oracle OLAP uses a variable that you have previously-defined (sometimes called a Countvar variable) to store the non-NA counts of the number of leaf nodes that contributed to aggregate values calculated for RELATION (for aggregation) statements that have an AVERAGE, HAVERAGE, HWAVERAGE, or WAVERAGE operator.

**Note:**

Typically, you do not use a user-defined Countvar variable to store the counts for average aggregations; instead, you use an Oracle OLAP-created Aggcount variable. You cannot use a Countvar variable when the aggregation specification includes a RELATION (for aggregation) statement with an average operator is for a compressed composite. See "Aggcount Variables" in [DEFINE VARIABLE](olap-dml-commands-a-g.md) for more information.

#### Syntax

You add or delete a \$COUNTVAR property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$COUNTVAR' countvar

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$COUNTVAR'

#### Parameters

countvar
A `TEXT` expression that specifies the name of a previously defined Countvar variable. The Countvar variable must be an `INTEGER` variable with the same dimensions in the same order as the dimensions as the variable on which you add the \$COUNTVAR property.

#### Examples

Example 4-6 Using \$COUNTVAR

For a variable named `v1`, the following statements cause Oracle OLAP to count the number of leaf nodes that contributed to an aggregate value that is the result of the execution of the `myaggmap` aggmap object by an AGGREGATE function.

    CONSIDER v1
    PROPERTY '$COUNTVAR' 'mycountvar'

### 4.11 \$DEFAULT_LANGUAGE

\$DEFAULT_LANGUAGE property identifies a dimension as the language dimension for the analytic workspace in which it is defined and specifies the default language for that language dimension.

**Note:**

There can be only one language dimension in an analytic workspace and only that dimension can have a \$DEFAULT_LANGUAGE property.

**See Also:**

[LOCK_LANGUAGE_DIMS](olap-dml-options.md), [SESSION_NLS_LANGUAGE](olap-dml-options.md), and [STATIC_SESSION_LANGUAGE](olap-dml-options.md) options.

#### Syntax

Before you add or delete a \$DEFAULT_LANGUAGE property to your language dimension, you must make that dimension the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands). You add \$DEFAULT_LANGUAGE property using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$DEFAULT_LANGUAGE' language

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$DEFAULT_LANGUAGE'

#### Parameters

language
A `TEXT` expression that is a value in your language dimension, or an empty string.

#### Usage Notes

Working with Language Dimensions

A language dimension is a dimension that has a \$DEFAULT_LANGUAGE property defined for it. There can only be one language dimension in an analytic workspace. Working with language dimensions involves:

- Creating a Language Dimension

- Defining Multi-language Variables that are Dimensioned by the Language Dimension

- Working with Language Dimension Status

Creating a Language Dimension

To create a language dimension, take the following steps:

1.  Define a TEXT dimension using DEFINE DIMENSION.

2.  Populate the language dimension with the names of the languages you want to support. As language names, use valid values for [NLS_LANGUAGE](olap-dml-options.md).

3.  Add the \$DEFAULT_LANGUAGE property to the dimension thereby identifying the dimension to Oracle OLAP as the language dimension in the analytic workspace.

Defining Multi-language Variables that are Dimensioned by the Language Dimension

To create multi-language variables, you include the language dimension as a dimension of the variable as illustrated in Example 4-8.

Working with Language Dimension Status

When an analytic workspace with a language dimension is attached, Oracle OLAP initializes the status of the language dimension, as follows:

1.  Oracle OLAP limits the language dimension to the value of the SESSION_NLS_LANGUAGE option when the language dimension contains that value.

2.  If the language dimension does not contain value to which the SESSION_NLS_LANGUAGE option is set, then Oracle OLAP limits the language dimension to the language specified in the dimension's \$DEFAULT_LANGUAGE property when the \$DEFAULT_LANGUAGE property contains a value and when that value is a value of the language dimension.

3.  If the language dimension does not contain value to which the SESSION_NLS_LANGUAGE option is set and if the language dimension's \$DEFAULT_LANGUAGE property is empty or names a nonexistent value, Oracle OLAP limits the language dimension to the value of the language dimension to the first value in the dimension's default order.

By default, after initialization, the status of a language dimension cannot be changed. However, you can change this behavior by changing the value of the LOCK_LANGUAGE_DIMS option from TRUE to FALSE which changes the status of the language dimension to ALL and enables issuing LIMIT statements against the dimension.

Exporting Language Dimensions

When exporting an analytic workspace using EXPORT (EIF), Oracle OLAP takes the following steps to determine what values of the language dimension to export:

- If the value of the LOCK_LANGUAGE_DIMS option is FALSE when an EXPORT statement executes, Oracle OLAP honors the current status of the language dimension and performs the export accordingly.

- If the value of the LOCK_LANGUAGE_DIMS option is TRUE when an EXPORT statement executes, Oracle OLAP:

  1.  Changes the value of the LOCK_LANGUAGE_DIMS option to FALSE (thereby setting the status to ALL) before executing the EXPORT statement.

  2.  Executes the EXPORT statement. Oracle OLAP exports all of the values of the language dimension.

  3.  Changes the value of the LOCK_LANGUAGE_DIMS option to TRUE and resets the status of the language dimension according to the value of the SESSION_NLS_LANGUAGE option.

#### Examples

Example 4-7 Creating a Language Dimension

This example illustrates creating a language dimension named `mylangs` that supports the use of both French and American and that specifies that the default language is American.

    NLS_LANGUAGE = 'AMERICAN'
    DEFINE mylangs DIMENSION TEXT
    MAINTAIN mylangs ADD 'FRENCH' 'AMERICAN'
    CONSIDER mylangs
    PROPERTY '$DEFAULT_LANGUAGE' 'AMERICAN'

    SHOW OBJ(PROPERTY '$DEFAULT_LANGUAGE' 'mylangs')
    AMERICAN

    REPORT mylangs
    MYLANGS
    --------------
    FRENCH
    AMERICAN

Example 4-8 Attaching a Language Dimension

Assume that in an analytic workspace named `myaw` that you have created a language dimension named `mylangs` as described in Example 4-7. Assume also that you have created a `products` dimension and a `prod-desc` variable with the following definitions and values.

    DEFINE MYLANGS DIMENSION TEXT
    SHOW OBJ(PROPERTY '$DEFAULT_LANGUAGE' 'mylangs')
    AMERICAN

    DEFINE PRODUCTS DIMENSION TEXT
    DEFINE PROD_DESC VARIABLE TEXT <PRODUCTS MYLANGS>

    MYLANGS
    --------------
    FRENCH
    AMERICAN

    PRODUCTS
    --------------
    PROD01
    PROD02

                   ------PROD_DESC------
                   ------PRODUCTS-------
    MYLANGS          PROD01     PROD02
    -------------- ---------- ----------
    FRENCH         Pantalons  JupesAMERICAN       Trousers   Skirts


Assume that you attach the analytic workspace. By displaying the options for the analytic workspace and requesting a report of `mylangs` and `prod_desc`, shows that Oracle OLAP has limited the `mylangs` dimension to American which is the value of the SESSION_NLS_LANGUAGE option.

    SHOW NLS_LANGUAGE
    AMERICAN
    AW ATTACH myaw RW
    " Get the default language in our language dimension
    SHOW OBJ(PROPERTY '$DEFAULT_LANGUAGE' 'mylangs')
    AMERICAN
    SHOW SESSION_NLS_LANGUAGE
    AMERICAN
    SHOW LOCK_LANGUAGE_DIMS
    yes
    SHOW STATIC_SESSION_LANGUAGE
    no

    REPORT mylangs

    MYLANGS
    --------------
    AMERICAN

    REPORT prod_desc
                   ------PROD_DESC------
                   ------PRODUCTS-------
    MYLANGS          PROD01     PROD02
    -------------- ---------- ----------
    AMERICAN       Trousers   Skirts

Example 4-9 Changing NLS_LANGUAGE

Assume that you have attached the analytic workspace `myaw` as described in Example 4-8. Now you change the value of NLS_LANGUAGE to French. Because the value of STATIC_SESSION_LANGUAGE is set to NO, making this change effectively changes the value of the SESSION_NLS_LANGUAGE option to French. When the value of SESSION_NLS_LANGUAGE option is French, as a report of `mylangs` and `prod_desc` illustrates, Oracle OLAP limits the `mylangs` dimension to French.

    SET NLS_LANGUAGE= 'FRENCH'
    SHOW OBJ(PROPERTY '$DEFAULT_LANGUAGE' 'mylangs')
    AMERICAN
    SHOW NLS_LANGUAGE
    FRENCH
    SHOW SESSION_NLS_LANGUAGE
    FRENCH
    SHOW LOCK_LANGUAGE_DIMS
    oui
    SHOW STATIC_SESSION_LANGUAGE
    non

    REPORT mylangs
    MYLANGS
    --------------
    FRENCH

    REPORT prod_desc
                   ------PROD_DESC------
                   ------PRODUCTS-------
    MYLANGS          PROD01     PROD02
    -------------- ---------- ----------
    FRENCH         Pantalons  Jupes

Example 4-10 Setting NLS_LANGUAGE to a Value that is Not in a Language Dimension

Assume that in the analytic workspace named `myaw` (described in Example 4-9 ) the value of NLS_LANGUAGE is set first to American and then set to Spanish. As illustrated in the following code, because the language dimension, `mylangs`, does not include Spanish as one of its values, Oracle OLAP limits the `mylangs` dimension using the value of the \$DEFAULT_LANGUAGE property which is American.

    "Change the value of NLS_LANGUAGE to AMERICAN
    SET NLS_LANGUAGE= 'AMERICAN'
    "Change the value of NLS_LANGUAGE to SPANISH
    SET NLS_LANGUAGE= 'SPANISH'

    SHOW OBJ(PROPERTY '$DEFAULT_LANGUAGE' 'mylangs')
    AMERICAN

    SHOW NLS_LANGUAGE
    SPANISH

    SHOW SESSION_NLS_LANGUAGE
    SPANISH

    SHOW LOCK_LANGUAGE_DIMS
    sí

    SHOW STATIC_SESSION_LANGUAGE
    no

    REPORT mylangs
    MYLANGS
    --------------
    AMERICAN

    REPORT prod_desc
                   ------PROD_DESC------
                   ------PRODUCTS-------
    MYLANGS          PROD01     PROD02
    -------------- ---------- ----------
    AMERICAN       Trousers   Skirts

Assume that you had defined the `mylangs` language dimension without specifying a default language using the following code.

    DEFINE mylangs DIMENSION TEXT
    MAINTAIN mylangs ADD 'FRENCH' 'AMERICAN'
    CONSIDER mylangs
    PROPERTY '$DEFAULT_LANGUAGE' ''

In this case, when you set the value of NLS_LANGUAGE to Spanish, because the language dimension, `mylangs` does not have a value specified for its \$DEFAULT_LANGUAGE property, Oracle OLAP limits the `mylangs` dimension using the first value in the `mylangs` dimension which is French.

    NLS_LANGUAGE = 'SPANISH'
    SHOW OBJ(PROPERTY '$DEFAULT_LANGUAGE' 'mylangs')

    SHOW NLS_LANGUAGE
    SPANISH
    SHOW SESSION_NLS_LANGUAGE
    SPANISH
    SHOW LOCK_LANGUAGE_DIMS
    sí
    SHOW STATIC_SESSION_LANGUAGE
    no

    REPORT mylangs
    MYLANGS
    --------------
    FRENCH

    REPORT prod_desc
                   ------PROD_DESC------
                   ------PRODUCTS-------
    MYLANGS          PROD01     PROD02
    -------------- ---------- ----------
    FRENCH         Pantalons  Jupes

### 4.12 \$GID_DEPTH

The \$GID_DEPTH property specifies the number of levels of grouping ids in the grouping id relation to which it is added.

The \$GID_DEPTH property, which is automatically created and set when a [GROUPINGID command](olap-dml-commands-a-g.md) populates a grouping id relation, specifies the number of levels of grouping ids in the grouping id relation to which it is added.

#### Syntax

You cannot explicitly define a \$GID_DEPTH property. Oracle OLAP automatically creates a \$GID_DEPTH property on a grouping id relation when the execution of a GROUPIONGID command creates the relation.

\$GID_DEPTH = intlevels

#### Parameters

intlevels
An `INTEGER` value that specifies the number of levels of grouping ids.

For an example of using the \$GID_DEPTH property, see [Example 9-145](olap-dml-commands-a-g.md).

### 4.13 \$GID_LIST

The \$GID_LIST property contains the names of the levels used to create the grouping ids.

The \$GID_LIST property contains the names of the levels used to create the grouping ids in a relation created when the [GROUPINGID command](olap-dml-commands-a-g.md) with either the ROLLUP or GROUPSET keyword executes.

#### Syntax

You cannot explicitly define a \$GID_LIST property. Oracle OLAP automatically creates a \$GID_LIST property on a grouping id relation when the execution of a GROUPIONGID command with either the ROLLUP or GROUPSET keyword creates the relation.

\$GID_LIST = levels

#### Parameters

levels
A TEXT expression which is the levels, separated by hyphens (-), of the hierarchies of the dimension for which grouping ids were created.

### 4.14 \$GID_TYPE

\$GID_TYPE property specifies the grouping type of the grouping ids.

The \$GID_TYPE property, which is automatically created and set when a GROUPINGID command with either the ROLLUP or GROUPSET keyword populates a grouping id relation, specifies whether the grouping type of the grouping ids.

#### Syntax

You cannot explicitly define a \$GID_TYPE property. Oracle OLAP automatically creates a \$GID_TYPE property on a grouping id relation when the execution of a GROUPIONGID command with either the ROLLUP or GROUPSET keyword creates the relation.

\$GID_TYPE = ROLLUP \| GROUPSET

#### Parameters

ROLLUP
Specifies that the grouping ids are of the rollup type.

For more information on this type of grouping type, see the discussion of ROLLUP in the rollup cube clause of a SQL `SELECT` statement in Oracle Database SQL Language Reference.

GROUPSET
Specifies that the grouping ids are of the grouping set type.

For more information on this type of grouping type, see the discussion of grouping sets in the grouping sets clause of a SQL `SELECT` statement in Oracle Database SQL Language Reference.

### 4.15 \$LOOP_AGGMAP

The \$LOOP_AGGMAP property is used to determine how to loop the formula on which it is assigned when a SQL OLAP_TABLE function with the LOOP OPTIMIZED clause is executed. It specifies the name of an aggmap object to use when Oracle OLAP generates a UNION subclause that includes the formula. The value that you specify for this property overrides all other aggmaps associated with a variable (for example, aggmaps for which the variable has an \$AGGMAP property) and can be used to clarify which aggmap Oracle OLAP should use when the underlying variables of a formula are associated with different aggmaps.

#### Syntax

You add or delete a \$LOOP_AGGMAP property to the most recently defined or considered formula (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$LOOP_AGGMAP' agggmap-name

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$LOOP_AGGMAP'

#### Parameters

aggmap_name
The name of an aggmap object.

### 4.16 \$LOOP_DENSE

The \$LOOP_DENSE property is used to determine how to loop the formula on which it is assigned when an OLAP_TABLE SQL function with the LOOP OPTIMIZED clause is executed.

It specifies that Oracle OLAP loops densely over the formula (that is, that it loops over every tuple of the formula—even those member cells that do not have values).

**See Also:**

- Oracle OLAP DML Reference for information on looping in OLAP_TABLE

- [SET_PROPERTY](olap-dml-commands-h-z.md)

#### Syntax

You add or delete a \$LOOP_DENSE property to the most recently defined or considered formula (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$LOOP_DENSE' dimension_list

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$LOOP_DENSE'

#### Parameters

dimension_list
One or more names of the dimensions of the formula separated by commas.

### 4.17 \$LOOP_TYPE

The \$LOOP_TYPE property specifies how to loop over a formula that contains multiple variables when the formula is used in an OLAP_TABLE SQL function that has the LOOP OPTIMIZED clause.

The type of looping can impact performance and the number rows that are returned when the formula contains NA aware functions such as NVL or if NULL TRACKING is disabled. For information on null tracking, see "[NA2 Bits and Null Tracking](olap-dml-commands-a-g.md)".

#### Syntax

You add or delete a \$LOOP_TYPE property to the most recently defined or considered formula (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$LOOP_TYPE' {'DENSE' \| 'INNER' \| 'OUTER'}

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$LOOP_TYPE'

#### Parameters

DENSE
Returns variable values for all possible combinations of tuples. If null tracking is not specified for a composite, you get NA values for non-existent data as well as for intentionally null values.

DENSE is similar to a cross join in a SQL SELECT statement. It results in the Cartesian product of all of the base dimensions of the variables.

INNER
(Default) Returns variable values only when a tuple has data in all of the variables. NVL values are not included.

INNER is similar to a SQL inner join.

OUTER
Returns a variable value when the tuple has data in any of the variables. NVL values are included.

OUTER is similar to a SQL outer join.

### 4.18 \$LOOP_VAR

The \$LOOP_VAR property specifies that when an OLAP_TABLE SQL function with the LOOP OPTIMIZED clause is executed, the formula on which it is assigned is looped in the same manner as the variable or QDR specified in the property.

**See Also:**

- Oracle OLAP DML Reference for more information on looping in OLAP_TABLE

- [SET_PROPERTY](olap-dml-commands-h-z.md)

#### Syntax

You add or delete a \$LOOP_VAR property to the most recently defined or considered formula (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$LOOP_VAR' qdr \| variable

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$LOOP_VAR'

#### Parameters

qdr
A QDR for a dimension of the formula.

variable
A variable with the same dimensions as the formula.

### 4.19 \$NATRIGGER

The \$NATRIGGER property specifies values for Oracle OLAP to substitute for NA values that are in a dimensioned variable, but not in the session cache for the variable (if any).

To calculate the values, Oracle OLAP takes the steps described in "Usage Notes", \$NATRIGGER. The results of the calculation are either stored in the variable or cached in the session cache for the variable as described in "Usage Notes", [VARCACHE](olap-dml-options.md).

**Note:**

When you want to trigger the aggregation of a variable, you can use the \$AGGMAP property rather than the \$NATRIGGER property.

#### Syntax

You add or delete a \$NATRIGGER property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$NATRIGGER' value

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$NATRIGGER'

#### Parameters

value
A TEXT expression that is the value of the property. The text can be any expression that is valid for defining a formula.

#### Usage Notes

How Oracle OLAP Calculates Data for a Variable with NA Values

When calculating the data for a dimensioned variable, Oracle OLAP takes the following steps for each cell in the variable:

1.  Is there is a session cache for the variable.

    - Yes. Go to step 2.

    - No. Go to step 3.

2.  Does that cell in the session cache for the variable have an `NA` value.

    - Yes. Go to step 3.

    - No. Go to step 7.

3.  Does that cell in variable storage have an `NA` value.

    - Yes. Go to step 4.

    - No. Go to step 7.

4.  Does the variable have an \$AGGMAP property?

    - Yes. Aggregate the variable using the aggmap specified for the \$AGGMAP property and, then, go to step 5.

    - No. Go to step 6.

5.  What is the value of the cell after aggregating the variable?

    - NA, go to step 6.

    - Non-NA, go to step 7.

6.  Does the variable have a \$NATRIGGER property?

    - Yes. Execute the expression specified for the \$NATRIGGER property and, then, go to step 7.

    - No. Go to step 7.

7.  Calculate the data.

8.  Apply the NAFILL function or the NASKIP, NASKIP2, or NASPELL options, as appropriate.

Making NA Triggers Recursive or Mutually Recursive

You can make NA triggers recursive or mutually recursive by including triggered objects within the value expression. You must set the RECURSIVE option to `YES` before a formula, program, or other \$NATRIGGER expression can invoke a trigger expression again while it is executing. For limiting the number of triggers that can execute simultaneously, see the [TRIGGERMAXDEPTH](olap-dml-options.md) option.

Using \$NATRIGGER with Composites

You can set an `$NATRIGGER` expression on a variable that is dimensioned by a composite, but Oracle OLAP evaluates the `$NATRIGGER` expression only for the dimension-value combinations that exist in the composite.

\$NATRIGGER Ignored by EXPORT and AGGREGATE

The AGGREGATE command and the AGGREGATE function ignore the \$NATRIGGER property setting for a variable during an aggregation operation. The statements fetch the stored value only, and do not invoke the \$NATRIGGER expression. The \$NATRIGGER property remains in effect for other operations.

In executing an EXPORT (EIF) statement, Oracle OLAP does not evaluate the \$NATRIGGER property expression on a variable when it simply exports the variable. However, Oracle OLAP does evaluate the \$NATRIGGER property expression when the variable is part of an expression that Oracle OLAP calculates during the export operation.

#### Examples

Example 4-11 Adding an \$NATRIGGER Property to a Variable

The following statements define a dimension with three values and define a variable that is dimensioned by the dimension. They add the \$NATRIGGER property to the variable, then put a value in one cell of the variable and leave the other cells empty so their values are `NA`. Finally, they report the values in the cells of the variable.

    DEFINE d1 INTEGER DIMENSION
    MAINTAIN d1 ADD 3
    DEFINE v1 DECIMAL <d1>
    PROPERTY '$NATRIGGER' '500.0'
    v1(d1 1) = 333.3
    REPORT v1

The preceding statements produce the following output.

    D1            V1
    --------- ----------
            1     333.3
            2     500.0
            3     500.0

### 4.20 \$STORETRIGGERVAL

The \$STORETRIGGERVAL property specifies whether, when a \$NATRIGGER expression executes, Oracle OLAP replaces the `NA` values in the variable with the results of the expression.

**Note:**

Applications typically use the \$VARCACHE property rather than the \$STORETRIGGERVAL property because the functionality of the \$STORETRIGGERVAL property is subsumed within the \$VARCACHE property.

See also "How Oracle OLAP Determines Whether to Store or Cache Results of \$NATRIGGER"

#### Syntax

You add or delete a \$STORETRIGGERVAL property to the most recently defined or considered object using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$STORETRIGGERVAL' value

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$ASTORETRIGGERVAL'

#### Parameters

value
A BOOLEAN expression that contains the value of the property.

#### Examples

Example 4-12 Storing an \$NATRIGGER Property Value

The following statements cause Oracle OLAP to store the \$NATRIGGER expression value in the NA cells of the v1 variable when Oracle OLAP evaluates the expression.

    TRIGGERSTOREOK = yes
    CONSIDER v1
    PROPERTY '$STORETRIGGERVAL' yes

### 4.21 \$VARCACHE

The \$VARCACHE property specifies whether Oracle OLAP stores or caches variable data that is the result of the execution of an AGGREGATE function or a \$NATRIGGER expression.

#### Syntax

You add or delete a \$VARCACHE property to the most recently defined or considered object (see [DEFINE](olap-dml-commands-a-g.md) and [CONSIDER](olap-dml-commands-a-g.md) commands) using a PROPERTY statement:

- To add the property, issue the following statement.

  PROPERTY '\$VARCACHE' value

- To delete the property, issue the following statement.

  PROPERTY DELETE '\$VARCACHE'

#### Parameters

value
One of the following TEXT expressions that indicate where Oracle OLAP should place variable data that is the result of calculations performed when the AGGREGATE function or \$NATRIGGER value executes:

- `VARIABLE` specifies that Oracle OLAP populates the variable with data that is the result of the execution of the AGGREGATE function or \$NATRIGGER property. When you specify this option, the data that is the result of the aggregation is permanently stored in the variable when the analytic workspace is updated and committed.

- `SESSION` specifies that Oracle OLAP caches data that is the result of the execution of the AGGREGATE function or \$NATRIGGER property in the session cache (See "[What is an Oracle OLAP Session Cache?](olap-dml-options.md)"). When you specify this option, the data that is the result of the execution of the AGGREGATE function or \$NATRIGGER property is ignored during updates and commits and is discarded after the session.

  **Important:**

  When SESSCACHE is set to `NO`, Oracle OLAP does not cache the data even when you specify `SESSION`. In this case, specifying `SESSION` is the same as specifying `NONE`.

- `NONE`specifies that Oracle OLAP calculates new variable data each time the AGGREGATE function or \$NATRIGGER value executes; Oracle OLAP does not store or cache the data.

- `DEFAULT` specifies that you do not want Oracle OLAP to use the \$VARCACHE property when determining what to do with data that is calculated by the AGGREGATE function. (See "How Oracle OLAP Determines Whether to Store or Cache Aggregated Data".)

#### Usage Notes

How Oracle OLAP Determines Whether to Store or Cache Results of \$NATRIGGER

When a \$NATRIGGER expression executes, what Oracle OLAP does with variable data that results from the execution of the expression is determined based on whether or not the variable that has the \$NATRIGGER property also has a \$STORETRIGGERVAL property and, if not, if the value of the \$NATRIGGER property is an AGGREGATE function.

When a \$NATRIGGER expression executes, Oracle OLAP goes through the following process:

1.  Does the variable with the \$NATRIGGER property also have a \$STORETRIGGERVAL property? If it does, then Oracle OLAP goes to step 1a. If it does not, then Oracle OLAP goes to step 2.

    1.  Is the value of the TRIGGERSTOREOK option, `YES `or `NO`? If it is YES, then Oracle OLAP goes to step 1b. If it is `NO`, then Oracle OLAP goes to step 2.

    2.  Is the value of the \$STORETRIGGERVAL property, `YES` or `NO`? If it is YES, then Oracle OLAP stores the results of the \$NATRIGGER expression and end decision-making process. If it is `NO`, then Oracle OLAP does not store the results of the \$NATRIGGER expression and end decision-making process.

2.  Is the \$NATRIGGER expression an AGGREGATE function? If it is, then Oracle OLAP follows the steps described in "How Oracle OLAP Determines Whether to Store or Cache Aggregated Data" to determine what to do with the result of \$NATRIGGER expression execution. If it is not, then Oracle OLAP goes to step 3.

3.  Does the variable with the \$NATRIGGER property also have a \$VARCACHE property? If it does, then Oracle OLAP goes to step 4. If it does not, then Oracle OLAP goes to step 5.

4.  Does the \$VARCACHE property have a value of `DEFAULT`? If it does, then go to step 5. If it does not, then Oracle OLAP uses the value of the \$VARCACHE property (that is, `STORE`, `CACHE`, or `NONE`) to determine what happens to the variable data values that are the result of \$NATRIGGER expression execution and end decision-making process.

5.  Use the current setting of the VARCACHE option to determine what happens to the variable data values that are the result of \$NATRIGGER expression execution and end decision-making process.

How Oracle OLAP Determines Whether to Store or Cache Aggregated Data

When an AGGREGATE command executes, Oracle OLAP always stores the results of the calculation directly in the variable in the same way it stores the results of an assignment statement. However, when an AGGREGATE function executes, Oracle OLAP sometimes stores the results of the calculation directly in the variable and sometimes caches it in the session cache. (See "What is an Oracle OLAP Session Cache?" in [SESSCACHE](olap-dml-options.md) for more information about the session cache.)

To determine where to place the data that is the result of AGGREGATE function execution, Oracle OLAP goes through the following process to determine whether to store or cache aggregated variable data:

1.  Is there a CACHE statement in the specification for the aggmap that is being used by the current AGGREGATE function? If there is, then Oracle OLAP goes to step 2. If there is not, then Oracle OLAP goes to step 3.

2.  Is the CACHE statement a CACHE DEFAULT statement? If it is, then Oracle OLAP goes to step 3. If it is not, then Oracle OLAP uses the CACHE statement in the aggregation specification to determine what to do with variable data that is the result of the calculation and ends the decision-making process.

3.  Does the variable being aggregated have a \$VARCACHE property? If it does, then Oracle OLAP goes to Step 4. If it does not, then Oracle OLAP goes to step 5.

4.  Does the \$VARCACHE property have a value of DEFAULT? If it does, then Oracle OLAP goes to step 5. If it does not, then Oracle OLAP uses the value of the \$VARCACHE property determines what happens to the variable data calculated using the AGGREGATE function, and ends the decision-making process.

5.  Use the current setting of the VARCACHE option to determine what happens to the variable data calculated using the AGGREGATE function. End decision-making process.

**See Also:**

- "How Oracle OLAP Determines Whether to Store or Cache Aggregated Data"

- "How Oracle OLAP Determines Whether to Store or Cache Results of \$NATRIGGER"

- "[What is an Oracle OLAP Session Cache?](olap-dml-options.md)"

- The description of the NA keyword of the [CACHE](olap-dml-commands-a-g.md) statement for information on caching NA values calculated by the AGGREGATE function

#### Examples

Example 4-13 Setting the \$VARCACHE Property

For a variable named `v1`, the following statements cause Oracle OLAP to cache the variable data that is the result of the execution of an AGGREGATE function or \$NATRIGGER expression.

    CONSIDER v1
    PROPERTY '$SVARCACHE' 'v1'
