Calculation objects are OLAP DML objects that contain OLAP DML statements that specify analysis to be performed. Calculation objects include: formulas, models, aggregation specifications, allocation specifications, and programs.

This chapter contains information on the following

- Creating Calculation Objects

- OLAP DML Formulas

- OLAP DML Model Objects

- OLAP DML Aggregation Objects

- OLAP DML Allocation Objects

For information on creating OLAP DML programs, see [OLAP DML Programs](olap-dml-programs.md).

### 3.1 Creating Calculation Objects

The general process of creating a calculation specification object is the following two step process:

1.  Define the calculation object using the appropriate DEFINE statement.

2.  Add the calculation specification to the object definition. You can add the calculation specification to the definition of a calculation object in the following ways:

    - At the command line level of the OLAP Worksheet, in an input file, or as an argument to a PL/SQL function. In this case, ensure that the object is the current object (issue a CONSIDER statement, if necessary), and, then, issue the appropriate statement that includes the specification as a multiline text argument. To code the specification as a multiline text, you can use a JOINLINES function where each of the text arguments of JOINLINES is a statement that specifies the desired processing, and where the final statement is `END`.

    - In an Edit Window of the OLAP Worksheet. In this case, at the command line level of the OLAP Worksheet, issue an EDIT statement with the appropriate keyword. An EDIT statement opens an Edit Window for the specified object. You can then type each statement as an individual line in the Edit Window. Saving the specification and closing the Edit Window when you are finished.

The following table outlines the OLAP DML statements that you use to create each type of calculation specification.

Table 3-1 Commands for Defining calculation objects

| Calculations | Definition Statement | Specification Statement | For More Information                      |
|:-------------|:---------------------|:------------------------|:------------------------------------------|
| Formula      | DEFINE FORMULA       | EQ                      | "OLAP DML Formulas"                       |
| Model        | DEFINE MODEL         | MODEL                   | "OLAP DML Model Objects"                  |
| Aggregation  | DEFINE AGGMAP        | AGGMAP                  | "OLAP DML Aggregation Objects"            |
| Allocation   | DEFINE AGGMAP        | ALLOCMAP                | "OLAP DML Allocation Objects"             |
| Program      | DEFINE PROGRAM       | PROGRAM                 | [OLAP DML Programs](olap-dml-programs.md) |

### 3.2 OLAP DML Formulas

You can save an expression in a formula. Frequently, you define a formula for ease of use and to save storage space. Once you have defined a formula for an expression, you can use the name of the formula to represent the expression. Oracle OLAP does not store the data for a formula in a variable; instead it calculates the data at run time each time the data is requested.

Before you create a formula, decide whether you want to specify the expression when you first define the formula object or whether you want to specify the expression for the formula after you define the formula object:

- To specify the expression when you first define the formula object:

  1.  Issue a DEFINE FORMULA statement to define the formula object. Include the expression in the definition. Do not specify values for the `datatype` or `dimensions` arguments.

  2.  (Optional) Issue a COMPILE statement to compile the formula.

  3.  When you want the formula to be a permanent part of the analytic workspace, save the formula using an UPDATE statement followed by COMMIT.

- To specify the expression for the formula after you define the formula object:

  1.  Issue a DEFINE FORMULA statement to define the formula object. Specify values for the `datatype` or `dimensions` arguments, but do not specify a value for the expression itself.

  2.  Issue a CONSIDER statement to make the formula the current definition and then issue an EQ statement to specify the expression for the formula.

  3.  (Optional) Issue a COMPILE statement to compile the formula.

  4.  When you want the formula to be a permanent part of the analytic workspace, save the formula using an UPDATE statement followed by COMMIT.

For example, you can define a formula to calculate dollar sales, as follows.

    DEFINE dollar.sales FORMULA units * price

You can use [TRACE](olap-dml-commands-h-z.md) to help you debug a forumula.

### 3.3 OLAP DML Model Objects

This topic provides information about creating and executing OLAP DML models. It includes the following subtopics:

- What is an OLAP DML Model?

- Creating Models

- Compiling Models

- Running a Model

- Debugging a Model

#### 3.3.1 What is an OLAP DML Model?

An OLAP DML model is a set of interrelated equations that can assign results either to a variable or to a dimension value. For example, in a financial model, you can assign values to specific line items, such as `gross.margin` or `net.income`.

    gross.margin = revenue - cogs

When an assignment statement assigns data to a dimension value or refers to a dimension value in its calculations, then it is called a dimension-based equation. A dimension-based equation does not refer to the dimension itself, but only to the values of the dimension. Therefore, when the model contains any dimension-based equations, then you must specify the name of each of these dimensions in a `DIMENSION` statement at the beginning of the model.

When a model contains any dimension-based equations, then you must supply the name of a solution variable when you run the model. The solution variable is both a source of data and the assignment target of model equations. It holds the input data used in dimension-based equations, and the calculated results are stored in designated values of the solution variable. For example, when you run a financial model based on the `line` dimension, you might specify `actual` as the solution variable.

Dimension-based equations provide flexibility in financial modeling. Because you do not need to specify the modeling variable until you solve a model, you can run the same model with the `actual` variable, the `budget` variable, or any other variable that is dimensioned by `line`.

Models can be quite complex. You can:

- Include one model within another model as discussed in "Nesting Models"

- Use data from different time periods as discussed in "Using Data from Past and Future Time Periods"

- Solve simultaneous equations as discussed in "Solving Simultaneous Equations"

- Create models for different scenarios as described in "Modeling for Multiple Scenarios"

#### 3.3.2 Creating Models

To create an OLAP DML model, take the following steps:

1.  Issue a [DEFINE MODEL](olap-dml-commands-a-g.md) command to define the program object.
2.  Issue a [MODEL](olap-dml-commands-h-z.md) command which adds a specification to the model to specify the processing that you want performed.
3.  Compile the model as described in "Compiling Models".
4.  (Optional) If necessary, change the settings of model options listed in "[Model Options](olap-dml-options.md)".
5.  Execute the model as described in "Running a Model".
6.  Debug the model as described in "Debugging a Model".
7.  When you want the model to be a permanent part of the analytic workspace, save the model using an UPDATE command followed by COMMIT.

For an example of creating a model, see [Example 10-57](olap-dml-commands-h-z.md).

##### 3.3.2.1 Nesting Models

You can include one model within another model by using an [INCLUDE](olap-dml-commands-h-z.md) statement within a [MODEL](olap-dml-commands-h-z.md) command. The MODEL command that contains the INCLUDE statement is referred to as the parent model. The included model is referred to as the base model. You can nest models by placing an INCLUDE statement in a base model. For example, model `myModel1` can include model `myModel2`, and model `myModel2` can include model `myModel3`. The nested models form a hierarchy. In this example, `myModel1` is at the top of the hierarchy, and `myModel3` is at the root.

When a model contains an INCLUDE statement, then it cannot contain any DIMENSION statements. A parent model inherits its dimensions, if any, from the DIMENSION statements in the root model of the included hierarchy. In the example just given, models `myModel1` and `myModel2` both inherit their dimensions from the DIMENSION statements in model `myModel3`.

The INCLUDE statement enables you to create modular models. When certain equations are common to several models, then you can place these equations in a separate model and include that model in other models as needed.

The INCLUDE statement also facilitates what-if analyses. An experimental model can draw equations from a base model and selectively replace them with new equations. To support what-if analysis, you can use equations in a model to mask previous equations. The previous equations can come from the same model or from included models. A masked equation is not executed or shown in the [MODEL.COMPRPT](olap-dml-commands-h-z.md) report for a model.

##### 3.3.2.2 Dimension Status and Model Equations

When a model contains an assignment statement to assign data to a dimension value, then the dimension is limited temporarily to that value, performs the calculation, and restores the initial status of the dimension.

For example, a model might have the following statements.

    DIMENSION line
    gross.margin = revenue - cogs

If you specify `actual` as the solution variable when you run the model, then the following code is constructed and executed.

    PUSH line
    LIMIT line TO gross.margin
    actual = actual(line revenue) - actual(line cogs)
    POP line

The fact that using a solution variable in a model causes this behind-the-scenes code construction allows you perform complex calculations with simple model equations. For example, line item data might be stored in the `actual` variable, which is dimensioned by `line`. However, detail line item data might be stored in a variable named `detail.data`, with a dimension named `detail.line`.

When your analytic workspace contains a relation between `line` and `detail.line`, which specifies the line item to which each detail item pertains, then you might write model equations such as the following ones.

    revenue = total(detail.data line)
    expenses = total(detail.data line)

The relation between `detail.line` and `line` is used automatically to aggregate the detail data into the appropriate line items. The code that is constructed when the model is run ensures that the appropriate total is assigned to each value of the `line` dimension. For example, while the equation for the `revenue` item is calculated, `line` is temporarily limited to `revenue`, and the `TOTAL` function returns the total of detail items for the `revenue` value of `line`.

##### 3.3.2.3 Using Data from Past and Future Time Periods

Several OLAP DML functions make it easy for you to use data from past or future time periods. For example, the `LAG` function returns data from a specified previous time period, and the `LEAD` function returns data from a specified future period.

When you run a model that uses past or future data in its calculations, you must ensure that your solution variable contains the necessary past or future data. For example, a model might contain an assignment statement that bases an estimate of the `revenue` line item for the current month on the `revenue` line item for the previous month.

    DIMENSION line month
    ...
    revenue = LAG(revenue, 1, month) * 1.05

When the `month` dimension is limited to `Apr2004` to `Jun2004` when you run the model, then you must ensure that the solution variable contains `revenue` data for `Mar96`.

When your model contains a `LEAD` function, then your solution variable must contain the necessary future data. For example, when you want to calculate data for the months of April through June of 2004, and when the model retrieves data from one month in the future, then the solution variable must contain data for July 2004 when you run the model.

##### 3.3.2.4 Handling NA Values in Models

Oracle OLAP observes the NASKIP2 option when it evaluates equations in a model. NASKIP2 controls how `NA` values are handled when `+` (plus) and `-` (minus) operations are performed. The setting of NASKIP2 is important when the solution variable contains `NA` values.

The results of a calculation may be `NA` not only when the solution variable contains an `NA` value that is used as input, but also when the target of a simultaneous equation is `NA`. Values in the solution variable are used as the initial values of the targets in the first iteration over a simultaneous block. Therefore, when the solution variable contains `NA` as the initial value of a target, an `NA` result may be produced in the first iteration, and the `NA` result may be perpetuated through subsequent iterations.

To avoid obtaining `NA` for the results, you can ensure that the solution variable does not contain `NA` values or you can set NASKIP2 to `YES` before running the model.

##### 3.3.2.5 Solving Simultaneous Equations

An iterative method is used to solve the equations in a simultaneous block. In each iteration, a value is calculated for each equation. The new value is compared to the value from the previous iteration. When the comparison falls within a specified tolerance, then the equation is considered to have converged to a solution. When the comparison exceeds a specified limit, then the equation is considered to have diverged.

When all the equations in the block converge, then the block is considered solved. When any equation diverges or fails to converge within a specified number of iterations, then the solution of the block (and the model) fails and an error occurs.

You can exercise control over the solution of simultaneous equations with the OLAP DML options described in "[Model Options](olap-dml-options.md)". For example, using these options, you can specify the solution method to use, the factors to use in testing for convergence and divergence, the maximum number of iterations to perform, and the action to take when the assignment statement diverges or fails to converge.

##### 3.3.2.6 Modeling for Multiple Scenarios

Instead of calculating a single set of figures for a month and division, you might want to calculate several sets of figures, each based on different assumptions.

You can define a scenario model that calculates and stores forecast or budget figures based on different sets of input figures. For example, you might want to calculate profit based on optimistic, pessimistic, and best-guess figures.

To build a scenario model:

1.  Define a scenario dimension.

2.  Define a solution variable dimensioned by the scenario dimension.

3.  Enter input data into the solution variable.

4.  Write a model to calculate results based on the input data.

For an example of building a scenario model see, [Example 10-58](olap-dml-commands-h-z.md).

#### 3.3.3 Compiling Models

When you finish writing the statements in a model, you can use the [COMPILE](olap-dml-commands-a-g.md) command to compile the model. During compilation, COMPILE checks for format errors, so you can use COMPILE to help debug your code before running a model. When you do not use COMPILE before you run the model, then the model is compiled automatically before it is solved.You can use the OBJ function with the ISCOMPILED choice to test whether a model is compiled.

    SHOW OBJ(ISCOMPILED 'myModel')

When you compile a model, either by using a COMPILE statement or by running the model, the model compiler checks for problems that are unique to models. You receive an error message when any of the following occurs:

- The model contains any statements other than DIMENSION, INCLUDE, and assignment (SET) statements.

- The model contains both a DIMENSION statement and an INCLUDE statement.

- A DIMENSION or INCLUDE statement is placed after the first equation in the model.

- The dimension values in a single dimension-based equation refer to two or more different dimensions.

- An equation refers to a name that the compiler cannot identify as an object in any attached analytic workspace. When this error occurs, it may be because an equation refers to the value of a dimension, but you have neglected to include the dimension in a DIMENSION statement. In addition, a DIMENSION statement may appear to be missing when you are compiling a model that includes another model and the other model fails to compile. When a root model (the innermost model in a hierarchy of included models) fails to compile, the parent model cannot inherit any DIMENSION commands from the root model. In this case the compiler may report an error in the parent model when the source of the error is actually in the root model. See [INCLUDE](olap-dml-commands-h-z.md) for additional information.

##### 3.3.3.1 Resolving Names in Equations

The model compiler examines each name in an equation to determine the analytic workspace object to which the name refers. Because you can use a variable and a dimension value in the same way in a model equation (basing calculations on it or assigning results to it), a name might be the name of a variable or it might be a value of any dimension listed in a DIMENSION statement.

To resolve each name reference, the compiler searches through the dimensions listed in explicit or inherited DIMENSION statements, in the order they are listed, to determine whether the name matches a dimension value of a listed dimension. The search concludes as soon as a match is found.

Therefore, when two or more listed dimensions have a dimension value with the same name, the compiler assumes that the value belongs to the dimension named earliest in a DIMENSION statement.

Similarly, the model compiler might misinterpret the dimension to which a literal `INTEGER` value belongs. For example, the model compiler assumes that the literal value `'200'` belongs to the first dimension that contains either a value at position 200 or the literal dimension value 200.

To avoid an incorrect identification, you can specify the desired dimension and enclose the value in parentheses and single quotes. See "[SET](olap-dml-commands-h-z.md)".

When the compiler finds that a name is not a value of any dimension specified in a DIMENSION statement, it assumes that the name is the name of an analytic workspace variable. When a variable with that name is not defined in any attached analytic workspace, an error occurs.

##### 3.3.3.2 Code for Looping Over Dimensions

The model compiler determines the dimensions over which the statements loop. When an equation assigns results to a variable, the compiler constructs code that loops over the dimensions (or bases of a composite) of the variable.

When you run a model that contains dimension-based equations, the solution variable that you specify can be dimensioned by more dimensions than are listed in DIMENSION statements.

##### 3.3.3.3 Evaluating Program Arguments

When you specify the value of a model dimension as an argument to a user-defined program, the compiler recognizes a dependence introduced by this argument.

For example, an equation might use a program named `weight` that tests for certain conditions and then weights and returns the `Taxes` line item based on those conditions. In this example, a model equation might look like the following one.

    Net.Income = Opr.Income - weight(Taxes)

The compiler correctly recognizes that `Net.Income` depends on `Opr.Income` and `Taxes`. However, when the `weight` program refers to any dimension values or variables that are not specified as program arguments, the compiler does not detect any hidden dependencies introduced by these calculations.

##### 3.3.3.4 Dependencies Between Equations

The model compiler analyzes dependencies between the equations in the model. A dependence exists when the expression on the right-hand side of the equal sign in one equation refers to the assignment target of another equation. When an equation indirectly depends on itself as the result of the dependencies among equations, a cyclic dependence exists between the equations.

The model compiler structures the model into blocks and orders the equations within blocks and the blocks themselves to reflect dependencies. When you run the model, it is solved one block at a time. The model compiler can produce three types of solution blocks:

- Simple Solution Blocks—Simple blocks include equations that are independent of each other and equations that have dependencies on each other that are non-cyclic.

  For example, when a block contains equations that solve for values `A`, `B`, and `C`, a non-cyclic dependence can be illustrated as `A>B>C`. The arrows indicate that `A` depends on `B`, and `B` depends on `C`.

- Step Solution Blocks—Step blocks include equations that have a cyclic dependence that is a one-way dimensional dependence. A dimensional dependence occurs when the data for the current dimension value depends on data from previous or later dimension values. The dimensional dependence is one-way when the data depends on previous values only or later values only, but not both. For more information on one-way dimensional dependence, see "Ensuring One-Way Dimensional Dependence".

  Dimensional dependence typically occurs over a time dimension. For example, it is common for a line item value to depend on the value of the same line item or a different line item in a previous time period. When a block contains equations that solve for values `A` and `B`, a one-way dimensional dependence can be illustrated as `A>B>LAG(A)`. The arrows indicate that `A` depends on `B`, and `B` depends on the value of `A` from a previous time period.

- Simultaneous Solution Blocks—Simultaneous blocks include equations that have a cyclic dependence that is other than one-way dimensional. The cyclic dependence may involve no dimensional qualifiers at all, or it may be a two-way dimensional dependence. For more information on two-way dimensional dependence, see "Structures for Which the Model Compiler Assumes Two-Way Dimensional Dependence".

  When a model contains a block of simultaneous equations, COMPILE gives you a warning message. In this case, you may want to check the settings of the options that control simultaneous solutions before you run the model. "[Model Options](olap-dml-options.md)" lists these options.

  An example of a cyclic dependence that does not depend on any dimensional qualifiers can be illustrated as `A>B>C>A`. The arrows indicate that `A` depends on `B`, `B` depends on `C`, and `C` depends on `A`.

  An example of a cyclic dependence that is a two-way dimensional dependence can be illustrated as `A>LEAD(B)>LAG(A)`. The arrows indicate that `A` depends on the value of `B` from a future period, while `B` depends on the value of `A` from a previous period.

##### Order of Simultaneous Equations

The solution of a simultaneous block of equations is sensitive to the order of the equations. In general, rely on the model compiler to determine the optimal order for the equations. In some cases, however, you may be able to encourage convergence by placing the equations in a particular order.

To force the compiler to leave the simultaneous equations in each block in the order in which you place them, set the MODINPUTORDER option to `YES` before compiling the model. (MODINPUTORDER has no effect on the order of equations in simple blocks or step blocks.)

##### Structures for Which the Model Compiler Assumes Two-Way Dimensional Dependence

When dependence is introduced through any of the following structures, the model compiler assumes that two-way dimensional dependence occurs:

- A two-way dimensional dependence can occur when you use an aggregation function, such as AVERAGE, TOTAL, ANY, or COUNT.

      Opr.Income = Gross.Margin -
         (TOTAL(Marketing + Selling + R.D))
      Marketing = LAG(Opr.Income, 1, month)

<!-- -->

- A two-way dimensional dependence can occur when you use a time-series function that requires a time-period argument, such as CUMSUM, LAG, or LEAD (except for the specific functions and conditions described in "Ensuring One-Way Dimensional Dependence").

- A two-way dimensional dependence also can occur when you use a financial function, such as DEPRSL or NPV.

  A cyclic dependence across a time dimension that you introduce through a loan or depreciation function may cause unexpected results. The loan functions include FINTSCHED, FPMTSCHED, VINTSCHED, and VPMTSCHED. The depreciation functions include DEPRDECL, DEPRDECLSW, DEPRSL, and DEPRSOYD.

##### Ensuring One-Way Dimensional Dependence

When dependence between equations is introduced through any of the following structures, a one-way dimensional dependence occurs:

- A one-way dimensional dependence occurs when you use a LAG or LEAD function and when the argument for the number of time periods is coded as an explicit number (either as a value or a constant) or as the result of ABS. (Otherwise, there may be a two-way dependence, involving both previous and future dimension values, and the compiler assumes that a simultaneous solution is required.) The following example illustrates this use of LAG.

      Opr.Income = Gross.Margin - (Marketing + Selling + R.D)
      Marketing = LAG(Opr.Income, 1, month)

- A one-way dimensional dependence occurs when you use a MOVINGAVERAGE, MOVINGMAX, MOVINGMIN, or MOVINGTOTAL function, when the start and stop arguments are non-zero numbers, and when both the start and top arguments are positive or both are negative. Otherwise, two-way dimensional dependence is assumed.

      Opr.Income = Gross.Margin - (Marketing + Selling + R.D)
      Marketing = MOVINGAVERAGE(Opr.Income, -4, -1, 1, month)

##### 3.3.3.5 Obtaining Analysis Results

After compiling a model, you can use the following tools to obtain information about the results of the analysis performed by the compiler:

- The MODEL.COMPRPT program produces a report that shows how model equations are grouped into blocks. For step blocks and for simultaneous blocks with a cross-dimensional dependence, the report lists the dimensions involved in the dependence.

- The MODEL.DEPRT program produces a report that lists the variables and dimension values on which each model equation depends. When a dependence is dimensional, the report gives the name of the dimension.

- The INFO function lets you obtain specific items of information about the structure of the model.

##### 3.3.3.6 Checking for Additional Problems

The compiler does not analyze the contents of any programs or formulas that are used in model equations. Therefore, you must check the programs and formulas yourself to make sure they do not do any of the following:

- Refer to the value of any variable used in the model.

- Refer to the solution variable.

- Limit any of the dimensions used in the model.

- Invoke other models.

When a model or program violates any of these restrictions, the results of the model may be incorrect.

**See Also:**

[MODTRACE](olap-dml-options.md), [TRACE](olap-dml-commands-h-z.md)

#### 3.3.4 Running a Model

When you run a model, keep these points in mind:

- Before you run a model, the input data must be available in the solution variable.

- Before running a model that contains a block of simultaneous equations, you might want to check or modify the values of some OLAP DML options that control the solution of simultaneous blocks. These options are described briefly in "[Model Options](olap-dml-options.md)".

- When your model contains any dimension-based equations, then you must provide a numeric solution variable that serves both as a source of data and as the assignment target for equation results. The solution variable is usually dimensioned by all of the dimensions on which model equations are based and also by the other dimensions of the solution variable on which you are not basing equations.

- When you run a model, a loop is performed automatically over the values in the current status list of each of the dimensions of the solution variable on which you have not based equations.

- When a model equation bases its calculations on data from previous time periods, then the solution variable must contain data for these previous periods. When it does not, or when the first value of the dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR is in status, then the results of the calculation are `NA`.

##### 3.3.4.1 Syntax for Running a Model

To run or solve a model, use the following syntax.

     model-name \[solution-variable\] \[NOWARN\]

where:

- `model-name` is the name of the model.

- `solution-variable` is the name of a numeric variable that serves as both the source and the target of data in a model that contains dimension-based equations. The solution variable is usually dimensioned by all the dimensions on which model equations are based (as specified in explicit or included DIMENSION commands). The solution-variable argument is required when the model contains any dimension-based equations. When all the model equations are based only on variables, a solution variable is not needed and an error occurs when you supply this argument. See "Dimensions of Solution Variables" for more information on dimensions of solution variables.

- `NOWARN `is an optional argument that specifies that you do not want to be warned when the model contains a block of simultaneous equations.

##### 3.3.4.2 Dimensions of Solution Variables

In a model with dimension-based equations, the solution variable is usually dimensioned by the dimensions on which model equations are based. Or, when a solution variable is dimensioned by a composite, the model equations can be based on base dimensions of the composite. The dimensions on which model equations are based are listed in explicit or inherited DIMENSION statements.

##### Special Cases of Solution Variables

The following special cases regarding the dimensions of the solution variable can occur:

- The solution variable can have dimensions that are not listed in DIMENSION commands. Oracle OLAP automatically loops over the values in the status of the extra dimensions. For example, the model might contain a DIMENSION statement that lists the `line` and `month` dimensions, but you might specify a solution variable dimensioned by `line`, `month`, and `division`. Oracle OLAP automatically loops over the `division` dimension when you run the model. The solution variable can also be dimensioned by a composite that has one or more base dimensions that are not listed in DIMENSION commands. See "Solution Variables Dimensioned by a Composite"

- When the solution variable has dimensions that are not listed in DIMENSION commands and when any of these other dimensions are the dimension of a step or simultaneous block, an error occurs.

- Oracle OLAP loops over the values in the status of all the dimensions listed in DIMENSION commands, regardless of whether the solution variable is dimensioned by them. Therefore, Oracle OLAP does extra, unnecessary work when the solution variable is not dimensioned by all the listed dimensions. Oracle OLAP warns you of this situation before it starts solving the model.

- The inclusion of an unneeded dimension of type DAY, WEEK, MONTH, QUARTER, or YEAR in a DIMENSION statement causes incorrect results when you use a loan, depreciation, or aggregation function in a model equation. The incorrect results occur because any component of a model equation that refers to the values of a model dimension behaves as if that component has all the dimensions of the model.

##### Solution Variables Dimensioned by a Composite

When a solution variable contains a composite in its dimension list, Oracle OLAP observes the sparsity of the composite whenever possible. As it solves the model, Oracle OLAP confines its loop over the composite to the values that exist in the composite. It observes the current status of the composite's base dimensions as it loops.

However, for proper solution of the model, Oracle OLAP must treat the following base dimensions of the composite as regular dimensions:

- A base dimension that is listed in a DIMENSION statement.

- A base dimension that is implicated in a model equation created using SET (for example, an equation that assigns data to a variable dimensioned by the base dimension).

- A base dimension that is also a base dimension of a different composite that is specified in the ACROSS phrase of an equation. (See [SET](olap-dml-commands-h-z.md) for more information on assignment statements and the use of ACROSS phrase.)

When a base dimension of a solution variable's composite falls in any of the preceding three categories, Oracle OLAP treats that dimension as a regular dimension and loops over all the values that are in the current status.

When the solution variable's composite has other base dimensions that do not fall in the special three categories, Oracle OLAP creates a temporary composite of these extra base dimensions. The values of the temporary composite are the combinations that existed in the original composite. Oracle OLAP loops over the temporary composite as it solves the model.

#### 3.3.5 Debugging a Model

The following tools are available for debugging models:

- To see the order in which the equations in a model are solved, you can set the MODTRACE option to `YES` before you run the model.When you set MODTRACE to `YES`, you can use a DBGOUTFILE statement to send debugging information to a file. The file produced by DBGOUTFILE interweaves each line of your model with its corresponding output.

- You can use the MODEL.COMPRPT, MODEL.DEPRT, and MODEL.XEQRPT programs and the INFO function to obtain information about the structure of a compiled model and the solution status of a model you have run.

### 3.4 OLAP DML Aggregation Objects

This topic provides information about aggregating data using the OLAP DML.It includes the following subtopics:

- What is an OLAP DML Aggregation?

- Aggregating Data Using the OLAP DML

- Compiling Aggregation Specifications

- Executing the Aggregation

- Creating Custom Aggregates

#### 3.4.1 What is an OLAP DML Aggregation?

Historically, aggregating data was summing detail data to provide subtotals and totals. However, using OLAP DML aggmap objects you can specify more complex aggregation calculations:

- The summary data dimensioned by a hierarchical dimension can be calculated using many different types of methods (for example, first, last, average, or weighted average). For an example of this type of aggregation, see [Example 9-18](olap-dml-commands-a-g.md).

- The summary data dimensioned by a nonhierarchical dimension can be calculated using a model. Using a model to calculate summary data is useful for calculating values for dimensions, such as line items, that do not have a hierarchical structure. Instead, you create a model to calculate the values of individual line items from one or more other line items or workspace objects. For an example of this type of aggregation, see [Example 9-17](olap-dml-commands-a-g.md).

- The detail data used to calculate the summary data can be in the variable that contains the summary data or in one or more other variables. The variable that contains the summary data does not have to have the same dimensions as the variables that contain the detail data. For an examples of this type of aggregation, see [Example 9-15](olap-dml-commands-a-g.md) and [Example 9-32](olap-dml-commands-a-g.md).

- The data can be aggregated as a database maintenance procedure, in response to user requests for summarized data, or you can combine these approaches. See "Executing the Aggregation" for more information.

- Data that is aggregated in response to user requests can be calculated each time it is requested or stored or cached in the analytic workspace for future queries.

- The specification for the aggregation can be permanent or temporary as described in "Creating Custom Aggregates".

#### 3.4.2 Aggregating Data Using the OLAP DML

To aggregate data using the OLAP DML, take the following steps:

1.  Decide if you want to aggregate all of the data as a database maintenance procedure using the AGGREGATE command or on-the-fly at run time using the AGGREGATE function or the \$AGGMAP property, or if you want to combine these approaches and precalculate some values and calculate others at run time. For a discussion of the various approaches, see "Executing the Aggregation".

2.  Issue a DEFINE AGGMAP statement to define the aggmap object as type AGGMAP.

3.  Write the aggregation specification as described in [AGGMAP](olap-dml-commands-a-g.md).

4.  When aggregating a partitioned variable, run PARTITIONCHECK to check that the aggregation specification created in the previous step is compatible with the variable's partitioning. If it is not, either rewrite the aggregation specification or repartition the variable using CHGDFN.

5.  When some or all of the data is to be aggregated using the AGGREGATE function:

    1.  Compile the aggmap object as described in "Compiling Aggregation Specifications".

    2.  Add the triggering property, object, or event. For example, add a formula that has the AGGREGATE function as its expression and add \$NATRIGGER property to the variable to trigger the execution of that formula in response to a run-time request for data.

6.  When you want the aggmap object to be a permanent part of the analytic workspace, save the aggmap object using an UPDATE statement followed by COMMIT.

7.  For data that is to be calculated using the AGGREGATE command:

    1.  (Optional) Use the DBMS_CUBE_LOG.ENABLE procedure to log the aggregation operation.

    2.  Use the AGGREGATE command, followed by UPDATE and COMMIT to precalculate the data and store it in the analytic workspace.

#### 3.4.3 Compiling Aggregation Specifications

Compiling the aggmap object is important for aggregation performed at run-time using the AGGREGATE function. Unless the compiled version of the aggmap has been saved, the aggmap is recompiled by each session that uses it.

There are two ways you can compile an aggmap objects:

- Issue a COMPILE statement.

  A COMPILE statement is the only way to compile an aggmap object that is used by an AGGREGATE function. Explicitly compiling an aggmap is also useful for finding syntax errors in the aggmap before attempting to use it to generate data. The following statement compiles the `sales.agg` aggmap.

      COMPILE gpct.aggmap

- When you aggregate the data using an AGGREGATE command, include the FUNCDATA phrase in the statement.

  When you use the FUNCDATA phrase in an AGGREGATE command, Oracle OLAP compiles the aggmap before it aggregates the data. For example, this statement compiles and precalculates the aggregate data.

      AGGREGATE sales USING gpct.aggmap FUNCDATA

  **Note:**

  When some data is calculated on the fly, then you must compile and save the aggmap after executing the AGGREGATE command.

#### 3.4.4 Executing the Aggregation

The OLAP DML provides two ways to aggregate data:

- As a data maintenance procedure using the AGGREGATE command. To use this method of aggregating data within an aggregation specification, identify data that you want to aggregate in this manner using the PRECOMPUTE statement or PRECOMPUTE clause of the RELATION statement.

- At run-time when needed using the AGGREGATE function or adding an \$AGGMAP property to the variable.

You can choose whatever method seems appropriate: by level, individual member, member attribute, time range, data value, or other criteria. You can also combine these approaches and precalculate some values and calculate others at run time. In this case, frequently, you use the same aggmap with the AGGREGATE command and the AGGREGATE function. However, in some cases you might use different aggmaps.

One step that you can take to achieve overall good performance is to balance the amount of the data that you aggregate and store in an analytic workspace with the amount of data that you specify for calculation on the fly. You can use a PRECOMPUTE statement or clause within your aggregation specification to ask Oracle OLAP to use special functionality called the Aggregate Advisor to automatically determine what values to aggregate as a data maintenance procedure using the AGGREGATE command, or to explicitly identify the values yourself.

#### 3.4.5 Creating Custom Aggregates

The definitions for most aggregations persist from one session to another. However, you might need to create session-only aggregates at run time for forecasting or what-if analysis, or just because you want to view the data in an unforeseen way. Adding session-only aggregates is sometimes called creating custom aggregates. You can create non-persistent aggregated data without permanently changing the specification for the aggregation in the following ways:

- Using a MAINTAIN ADD SESSION statement, define temporary dimension members and include an aggregation specification as part of the definition of these members. The aggregation specification can either be a model or an aggmap. For an example of using this method to create a temporary aggregation, see [Example 10-42](olap-dml-commands-h-z.md) .

- Create a model that specifies the aggregation. Use an AGGMAP ADD statement to add the model to an aggmap at run time. After a session, Oracle OLAP automatically removes any models that you have added to an aggmap in this manner. See [AGGMAP ADD or REMOVE model](olap-dml-commands-a-g.md) for more information.

### 3.5  OLAP DML Allocation Objects

Allocating data involves creating lower-level data from summary data. This topic provides an overview of how to allocate data using OLAP DML statements. It includes the following subtopics:

- Introduction to Allocating Data Using the OLAP DML

- Features of Allocation in Oracle OLAP

- Allocating Data

- Handling NA Values When Allocating Data

#### 3.5.1 Introduction to Allocating Data Using the OLAP DML

You can specify data allocation in an ALLOCMAP type aggmap object. To implement the allocation, execute an ALLOCATE command for the ALLOCMAP aggmap. The target is a variable that is dimensioned by one or more hierarchical dimensions. The source data is specified by dimension values at a higher level in a hierarchical dimension than the values that specify the target cells.

ALLOCATE uses an aggmap to specify the dimensions and the values of the hierarchies to use in the allocation, the method of operation to use for a dimension, and other aspects of the allocation.

Some allocation operations are based on existing data. The object containing that data is the basis object for the allocation. In those operations, ALLOCATE distributes the data from the source based on the values of the basis object.

ALLOCATE has operations that are the inverse of the operations of the AGGREGATE command. The allocation operation methods range from simple allocations, such as copying the source data to the cells of the target variable, to very complex allocations, such as a proportional distribution of data from a source that is a formula, with the amount distributed being based on another formula, with multiple variables as targets, and with an aggmap that specifies different methods of allocation for different dimensions.

#### 3.5.2 Features of Allocation in Oracle OLAP

The Oracle OLAP allocation system is very flexible and has many features, including the following:

- The source, basis, and target objects can be the same variable or they can be different objects.

- The source and basis objects can be formulas, so you can perform computations on existing data and use the result as the source or basis of the allocation.

- You can specify the method of operation of the allocation for a dimension. The operations range from simple to very complex.

- You can specify whether the allocated value is added to or replaces the existing value of the target cell.

- You can specify an amount to add to or multiply by the allocated value before the result is assigned to the target cell.

- You can lock individual values in a dimension hierarchy so that the data of the target cells for those dimension values is not changed by the allocation. When you lock a dimension value, then the allocation system normalizes the source data, which subtracts the locked data from the source before the allocation. You can choose to not normalize the source data.

- You can specify minimum, maximum, floor, or ceiling values for certain operations.

- You can copy the allocated data to a second variable so that you can have a record of individual allocations to a cell that is the target of multiple allocations.

- You can specify ways of handling allocations when the basis has a null value.

- You can use the same aggmap in different ALLOCATE commands to use the same set of dimension hierarchy values, operations, and arguments with different source, basis, or target objects.

#### 3.5.3 Allocating Data

To allocate data using an aggmap object, use the following OLAP DML statements in the order indicated:

1.  Issue a DEFINE AGGMAP statement to define the aggmap object.
    **Note:**

    When using the OLAP Worksheet, at the command line level, immediately after the DEFINE AGGMAP statement, enter an "empty" allocation specification by coding an ALLOCMAP statement. For example:

        DEFINE myaggmap AGGMAP
        ALLOCMAP 'END'
2.  Add a specification to the aggmap object that specifies the allocation that you want performed. See [ALLOCMAP](olap-dml-commands-a-g.md) for more information.
3.  When you want the aggmap object to be a permanent part of the analytic workspace, save the aggmap object using an UPDATE statement followed by COMMIT.
4.  (Optional) Use the DBMS_CUBE_LOG.ENABLE procedure to log the allocation operation.
5.  (Optional) Redesign the allocation error log by setting the ALLOCERRLOGFORMAT and ALLOCERRLOGHEADER options to nondefault values.
6.  (Optional) Set the \$ALLOCMAP property on one or more variables to specify that the aggmap is the default allocation specification for the variables.
7.  (Recommended, but optional) Limit the variable to the target cells (that is, the cells into which you want to allocate data).
8.  Issue an ALLOCATE statement to allocate the data.

#### 3.5.4 Handling NA Values When Allocating Data

Sometimes you want to overwrite existing data when allocating values to a target variable and at other times you want to write allocated values to target cells that have an `NA` basis before the allocation. For example, when you create a product in your product dimension, then no basis exists for the new product in your budget variable. You want to allocate advertising costs for the entire product line, including the new product.

You can handle `NA` values using formulas and hierarchical operators in a RELATION statement in the following ways:

- Handling NA data with formulas—The preferred method for handling the `NA` values is to construct a basis that only describes the desired target cells. You can refine your choice of basis values by deriving the basis from a formula. The following statements define a formula that equates the values of the new product to twice the value of an existing product. You could use such a formula as the basis for allocating advertising costs to the new product.

      DEFINE formula_basis FORMULA DECIMAL <product>
      EQ IF product EQ 'NEWPRODUCT' -
         THEN 2 * product.budget(product 'EXISTINGPRODUCT') -
         ELSE product.budget

- Handling NA data with hierarchical operators—To allocate data to target cells that currently have `NA` values, use a hierarchical operator in a RELATION statement in the allocation specification. The hierarchical operators use the hierarchy of the dimension rather than existing data as the allocation basis. A danger in using hierarchical operators is the possibility of densely populating your detail level data, which can result in a much larger analytic workspace and require much more time to aggregate the data.

  To continue the example of allocating the advertising cost for the new product, you could use the hierarchical last operator HLAST to specify allocating the cost to the new (and presumably the last) product in the product dimension hierarchy.
