No changes have been made to the Oracle OLAP DML or to Analytic Workspace Manager in this release. For changes in earlier releases, see the following topics.

### Changes in Oracle Database 12c Release 2 (12.2)

This release contains no changes in Analytic Workspace Manager since the previous release.

### Changes in Oracle Database 12c Release 1 (12.1)

The following are changes in Oracle Database 12c Release 1 (12.1) and for Analytic Workspace Manager in that release. Analytic Workspace Manager is the primary tool for creating, developing, and managing dimensional objects in Oracle Database.

#### New Features

The following Analytic Workspace Manager features are new in this release:

- Connecting to a database using a service name.

  See "[Defining a Database Connection](getting-started-oracle-olap.md)".

- Specifying an attachment mode when connecting an analytic workspace to an Oracle Database.

  See "[Showing the Analytic Workspace Attachment Modes](getting-started-oracle-olap.md)".

- Creating calculated measures that are based on OBIEE-compatible SQL function expressions.

  If this feature is enabled, then Analytic Workspace Manager automatically creates additional calculated measures as needed for processing a calculated measure that you create. The cube that contains the calculated measures is suitable for exporting to Oracle Business Intelligence Enterprise Edition (OBIEE). You can export a cube to OBIEE by using the Export to OBIEE Administrator plug-in.

  See "[Creating Cubes](creating-dimensions-and-cubes.md)" and "[Creating Calculated Measures](enhancing-your-database-analytic-content.md)".

- Creating a fact view with a measure dimension table.

  The fact view pivots a fact table so that the measures identify rows instead of columns.

  See "[Creating Measure Dimensions](creating-dimensions-and-cubes.md)".

- Creating a measure dimension.

  You can now create a measure dimension, which has measures as dimension members. Dimensions now have a Class type, which is either None or Measure.

  See "[Creating Measure Dimensions](creating-dimensions-and-cubes.md)".

- Saving the SQL of a mapping to the clipboard or to a file.

  See "[Mapping Cubes](creating-dimensions-and-cubes.md)"

- Specifying the aggregate functions `SUM`, `MAX`, `MIN`, `AVG`, and `COUNT` when mapping a cube to data sources.

  See "[Aggregate Functions](creating-dimensions-and-cubes.md)".

- Partitioning a cube on multiple levels of a dimension hierarchy.

  See "[Partitioning a Cube](creating-dimensions-and-cubes.md)".

- Saving an object definition to, or create an object from, a table.

  Previously, you could save an object definition as an XML template in a file. You can now save an XML template in a database table. You can use the XML template to re-create the dimensional objects.

  See "[Saving and Re-Creating Dimensional Objects with Object Definitions](creating-dimensions-and-cubes.md)".

- Copying and pasting objects.

  You can now copy objects such as an analytic workspace, a cube, a dimension, or a measure and paste that object in an appropriate location.

  See "[Copying and Pasting Dimensional Objects](creating-dimensions-and-cubes.md)".

- Joining cubes to tables and views.

  Oracle Database 12c introduces the CUBE JOIN operation. This operation improves the performance of joining a cube to a table or a view.

  See "[Joining Cubes to Tables and Views](querying-dimensional-objects.md)".

#### Desupported Features

The following features are no longer supported by Oracle. See [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for a complete list of desupported features in this release.

- Desupport of Common Warehouse Metamodel (CWM) for Oracle OLAP

#### Other Changes

The following are additional changes in the release:

- Data security policies use Oracle Real Application Security.

  When you create data security policies for cubes or dimensions, Oracle OLAP uses Oracle Real Application Security (ORAS) instead of Extensible Data Security (XDS), which it used in Oracle Database 11g releases. When you upgrade Oracle Database from an 11g release to 12c, then your XDS data security policies are automatically converted to ORAS.

  **Note:**

  Data security roles defined in an 11g Oracle Database instance are not automatically converted to ORAS. Before you upgrade an 11g database to 12c, you must delete any data security roles that are defined in the 11g database. After the upgrade, you may use Analytic Workspace Manager 12c to define the data security roles again.

  If you upgrade an 11g database to 12c without deleting the 11g data security roles, then any data security policies that include a data security role are invalid in the 12c database.

  Some differences in the data security implementation in 12c are the following:

  - Only the owner of an object can create a data security policy or OLAP data security role. In 11g, the owner and anyone who had write privileges for the object could create a data security policy or OLAP data security role.

  - You can disable the data security policy for a dimension or a cube and then enable it again.

  - You can have create more than one OLAP data security role; however, you can only add one data security role to a dimension or a cube. In 11g, you could add more than one.

  **See Also:**

  - "[Creating Data Security Policies on Dimensions and Cubes](security.md)" for information on creating data security policies in Analytic Workspace Manager

  - "[Disabling and Enabling Data Security](security.md)"

  - Oracle Database Real Application Security Administrator's and Developer's Guide for information on configuring data security in Oracle Database

- Viewing information about the partitions of a cube.

  The Partition Member Analysis subtab of the Partitioning properties of a cube displays information about the partitioning of the cube. This information replaces the Cube Partitioning Advisor of previous releases.

  **See Also:**

  - "[Analyzing Partition Members](creating-dimensions-and-cubes.md)"

- Oracle Enterprise Manager Cloud Control (Cloud Control)

  In previous releases of Oracle Database, you used Oracle Enterprise Manager Database Control (Database Control) to manage database performance tuning from a graphical user interface. In this release, you can use the Cloud Control graphical user interface.

  You must install Cloud Control separately from Oracle Database.

  **See Also:**

  - Oracle Enterprise Manager Cloud Control Basic Installation Guide for information on installing Cloud Control

  - "[Monitoring Analytic Workspaces](administering-oracle-olap.md)"
