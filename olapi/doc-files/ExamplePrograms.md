Skip navigation links

<table class="oac_no_warn" data-border="0" data-cellpadding="1" data-cellspacing="0" data-summary="Layout table... probably." width="100%">
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Overview </td>
<td style="text-align: right;" data-valign="top"><em><strong>Oracle® OLAP Java API Reference<br />
19c</strong><br />
E96404-01</em></td>
</tr>
</tbody>
</table>

------------------------------------------------------------------------

# Example Oracle OLAP Java API Programs

This documentation and *Oracle OLAP Java API Developer's Guide* contain examples that demonstrate the use of OLAP Java API classes. The complete code for many of the examples is available from the Oracle Technology Network (OTN) website, as described in the [Examples of Using the Oracle OLAP Java API](../overview-summary.md) section of the Overview.

The example programs use metadata objects that are based on tables of a schema in the relational database. The schema is owned by the GLOBAL user. From the OTN website, you can also download the SQL scripts that create the GLOBAL user and install the Global schema.

You can add the example program classes to your Java development environment and compile and run them if the programs can connect to an Oracle Database instance with the OLAP option that has the Global schema installed.

The example programs are in a package organization that you can import into an integrated developement environment such as Oracle JDeveloper. Most of the programs are the complete code for the examples in *Oracle OLAP Java API Developer's Guide*. The example program classes are in a structure that indicates the package of API classes that they exemplify. Extracting the contents of the `examples.zip` file creates the following directory structure.

    examples
      src
        oracle
          olapi
            examples
              cursor
              metadata
              source
              template
              transaction

In the remainder of this document, the references to the directory structure begin with the `examples.src.oracle.olapi.examples` directory.

## Base and Utility Classes

The following table lists the classes that are in the `examples` directory. These classes are used by all of the example programs.

| Class                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BaseExample11g`      | The base class for all of the example programs. Some of the methods of this class do the following:<br>• Put command line arguments into a `Properties` object.<br>• Create a `CursorPrintWriter`.<br>• Execute the example program.                                                                                                                                                                                                                                                                                                            |
| `Context11g`          | An instance of this class is created by a `BaseExample11g`. This class has methods that do the following:<br>• Use the command-line properties from the `BaseExample11g` to connect to an Oracle Database instance.<br>• Create or get the MDM metadata objects that are used by most of the example programs and store some of the objects in a `HashMap`.<br>This class also has convenience methods for getting metadata objects from the `HashMap`, for creating `Cursor` objects, and for displaying the contents of the `Cursor` objects. |
| `CursorPrintWriter`   | A `PrintWriter` that has methods for displaying the values of a `Cursor` in various formats.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `Logger`              | This class encapsulates the logging of output generated by an example program.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `SQLResultSetPrinter` | This class displays the result set of a SQL query.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

## First Example Program to Run

Before running any of the other example programs, first run the `SpecifyAWValues` program. It passes values to the `CreateAndBuildAW` class, which creates metadata objects and builds an analytic workspace. Most of the other example programs use the objects created by these classes.

| Package    | Class             | Description                                                                                                                                                                                                                                                                                                                                         |
|------------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `metadata` | `SpecifyAWValues` | A program that passes values to the `CreateAndBuildAW` class. That class defines metadata objects, maps them to the Global schema, deploys them to an analytic workspace, writes the metadata object definitions to an XML file, and builds the analytic workspace. Most of the other OLAP Java API example programs query that analytic workspace. |

## Examples in Oracle OLAP Java API Reference

The following table lists the classes that have the code for examples that appear in *Oracle OLAP Java API Reference*.

| Package  | Class                               | Description                                                                                                                                                                                                                                                                    |
|----------|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `source` | `RecursiveJoinAndShortcutsExamples` | This class has the complete code for the examples in the descriptions of the full signature of the `Source.recursiveJoin` method, of other signatures of `recursiveJoin`, and of some related `Source` methods such as `selectDescendants` and `sortDescendingHierarchically`. |
| `source` | `SourceExamplesInRef`               | This class has the complete code for examples in some of the classes in the `oracle.olapi.data.source` package.                                                                                                                                                                |

## Examples in Oracle OLAP Java API Developer's Guide

The tables in this section list the classes that contain the code for the examples in *Oracle OLAP Java API Developer's Guide*. Each table lists the examples in a chapter.

### Examples in Chapter 2

The following table lists the examples that appear in Chapter 2, "Understanding OLAP Java API Metadata", and the example programs that contain the code for the examples.

| Package    | Class                    | Description                                                                                                          |
|------------|--------------------------|----------------------------------------------------------------------------------------------------------------------|
| `metadata` | `AssociateDescriptions`  | Example 2-1, Associating a Description with an MdmObject.                                                            |
| `metadata` | `ElementsOfMdmAttribute` | Creates a query that produces the results that appear in Table 2-3 in the "Representing Dimension Attributes" topic. |
| `metadata` | `BasicCubeViewQuery`     | Example 2-4, Basic Cube View Query.<br>Example 2-5, Basic Cube Query Using Source Objects.<br>                       |

### Examples in Chapter 3

The following table lists the examples that appear in Chapter 3, "Discovering Metadata", and the example program that contains the code for the examples.

| Package    | Class                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|------------|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `metadata` | `ConnectAndDiscover` | Example 3-1, Getting a JDBC OracleConnection.<br>Example 3-2, Creating a DataProvider.<br>Example 3-3, Closing the Connection.<br>Example 3-4, Creating an MdmMetadataProvider.<br>Example 3-5, Getting the MdmSchema Objects<br>Example 3-6, Getting a Single MdmDatabaseSchema.<br>Example 3-7, Getting the Dimensions and Measures of an MdmDatabaseSchema.<br>Example 3-8, Getting the Dimensions and Measures of an MdmCube.<br>Example 3-9, Getting the Hierarchies and Levels of a Dimension.<br>Example 3-10, Getting the MdmAttribute Objects of an MdmPrimaryDimension.<br>Example 3-11, Getting a Primary Source for a Metadata Object. |

### Examples in Chapter 4

The following table lists the examples that appear in Chapter 4, "Creating Metadata and Analytic Workspaces", and the example programs that contain the code for the examples. The `CreateMetadataAndAW` program, which contains the code for most of the examples, creates a subset of the objects specified by `SpecifyAWValues` and created by the `CreateAndBuildAW` program. In `CreateMetadataAndAW` the values, such as the names for the OLAP objects and the names of relational tables and columns, are hard-coded. The methods are simplified for use as examples in the documentation. The `CreateMetadataAndAW` and `SpecifyAWValues` both first delete the GLOBAL_AWJ analytic workspace if it exists and then define and build the analytic workspace.

**Note:** All of the examples from the other chapters use the analytic workspace created by the `SpecifyAWValues` program. If you run the `CreateMetadataAndAW` program, be sure to run the `SpecifyAWValues` program before running any of the other example programs.

| Package    | Class                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|------------|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `metadata` | `CreateMetadataAndAW`  | Example 4-1, Creating an AW.<br>Example 4-2, Creating and Deploying an MdmStandardDimension.<br>Example 4-3, Creating and Mapping an MdmDimensionLevel.<br>Example 4-4, Creating and Mapping MdmLevelHierarchy and MdmHierarchyLevel Objects.<br>Example 4-6, Creating an MdmBaseAttribute.<br>Example 4-7, Creating and Mapping an MdmCube.<br>Example 4-8, Creating and Mapping Measures.<br>Example 4-9, Committing Transactions.<br>Example 4-10, Exporting to an XML Template.<br>Example 4-11, Building an Analytic Workspace. |
| `metadata` | `CreateValueHierarchy` | Example 4-5, Creating an MdmValueHierarchy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

### Examples in Chapter 5

The following table lists the examples that appear in Chapter 5, "Understanding Source Objects", and the example programs that contain the code for the examples.

| Package  | Class                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|----------|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `source` | `UnderstandingSourceObjects` | The following examples, and two informal untitled examples, are implemented as methods of this class.<br>Example 5-1, Using the isSubtypeOf Method.<br>Example 5-2, A Simple Join That Produces a Source with an Output.<br>Example 5-3, A Simple Join That Selects Elements of the Joined Source.<br>Example 5-4, A Simple Join That Removes Elements of the Joined Source.<br>Example 5-5, A Simple Join That Produces a Source with Two Outputs.<br>Example 5-6, A Simple Join That Hides An Output.<br>Example 5-7, Getting an Attribute for a Dimension Member.<br>Example 5-8, Getting Measure Values.<br>Example 5-9, Using the value Method to Relate a Source to Itself.<br>Example 5-10, Using the value Method to Select Elements of a Source.<br>Example 5-11, Using Derived Source Objects to Select Measure Values.<br>Example 5-12, Extracting Elements of a Source.<br>Example 5-13, Using a Parameterized Source to Change a Dimension Selection. |

### Examples in Chapter 6

The following table lists the examples that appear in Chapter 6, "Making Queries Using Source Methods", and the example programs that contain the code for the examples.

| Package  | Class                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|----------|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `source` | `MakingQueriesExamples`            | The following examples are implemented as methods of this class.<br>Example 6-1, Controlling Input-with-Source Matching With the alias Method.<br>Example 6-2, Using the distinct Method.<br>Example 6-3, Using COMPARISON_RULE_DESCENDING.<br>Example 6-4, Selecting the First and Last Time Elements.<br>Example 6-6, Selecting a Subset of the Elements of a Source.<br>Example 6-7, Using the value Method to Reverse a Relation<br>Example 6-8, Using the extract Method<br>Example 6-11, Hierarchical Sorting by Measure Value. |
| `source` | `SortingHierarchicallyByAttribute` | Example 6-5, Sorting Products Hierarchically By Attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `source` | `CreatingCubeAndPivotingEdges`     | Example 6-9, Creating a Cube and Pivoting the Edges.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `source` | `DrillingInHierarchy`              | Example 6-10, Drilling in a Hierarchy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `source` | `GettingShareOfUnits`              | Example 6-12, Getting the Share of Units Sold.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `source` | `UsingLagMethod`                   | Example 6-13, Using the Lag Method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `source` | `UsingMovingTotalMethod`           | Example 6-14, Using the movingTotal Method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `source` | `SelectingRangeWithNumberParam`    | Example 6-15, Selecting a Range With NumberParameter Objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

### Examples in Chapter 7

The following table lists the examples that appear in Chapter 7, "Using a TransactionProvider", and the example programs that contain the code for the examples.

| Package       | Class                 | Description                                                                                                                                                   |
|---------------|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `transaction` | `TransactionExamples` | The following examples are implemented as methods of this class.<br>Example 7-2, Rolling Back a Transaction.<br>Example 7-3, Using Child Transaction Objects. |

### Examples in Chapter 8

The following table lists the examples that appear in Chapter 8, "Understanding Cursor Classes and Objects", and the example programs that contain the code for the examples.

| Package  | Class                    | Description                                                                                                                                                                                                                                                                      |
|----------|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cursor` | `CursorConceptsExamples` | The following examples, and an informal example, are implemented as methods of this class.<br>Example 8-1, Creating the querySource Query.<br>Example 8-2, Setting the CompoundCursor Position and Getting the Current Values.<br>Example 8-3, Positions in an Asymmetric Query. |

### Examples in Chapter 9

The following table lists the examples that appear in Chapter 9, "Retrieving Query Results", and the example programs that contain the code for the examples.

| Package  | Class                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|----------|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `cursor` | `RetrievingQueryResults` | The following examples are implemented as methods of this class.<br>Example 9-1, Creating a Cursor.<br>Example 9-2, Getting a Single Value from a ValueCursor.<br>Example 9-3, Getting All of the Values from a ValueCursor.<br>Example 9-4, Getting ValueCursor Objects from a CompoundCursor example.<br>Example 9-5, Getting Values from a CompoundCursor with Nested Outputs example.<br>Example 9-6, Navigating For a Table View.<br>Example 9-7, Navigating For a Crosstab View Without Pages.<br>Example 9-8, Navigating For a Crosstab View With Pages.<br>Example 9-9, Getting CursorSpecification Objects for a Source.<br>Example 9-10, Specifying the Calculation of the Extent of a Cursor.<br>Example 9-11, Specifying the Calculation of Starting and Ending Positions in a Parent.<br>Example 9-12, Calculating the Span of the Positions in the Parent of a Value.<br>Example 9-13, Specifying a Fetch Size. |

### Examples in Chapter 10

The following table lists the examples that appear in Chapter 10, "Creating Dynamic Queries, and the example programs that contain the code for the examples.

| Package    | Class                     | Description                                                                                                                                                                                                               |
|------------|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `template` | `TopBottomTemplate`       | Example 10-1, Implementing a Template.<br>The following examples are implemented as inner classes of `TopBottomTemplate`.<br>Example 10-2, Implementing a MetadataState.<br>Example 10-3, Implementing a SourceGenerator. |
| `template` | `TopBottomTest`           | Example 10-4, Getting the Source Produced by the Template.                                                                                                                                                                |
| `template` | `SingleSelectionTemplate` | A `Template` that is used by `TopBottomTest`.                                                                                                                                                                             |

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
