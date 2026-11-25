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

**Changes in Previous Releases in the OLAP Java API**

This page describes the features that the OLAP Java API introduced in Oracle Database 11*g* Release 2 (11.2) and in earlier releases. This page contains the following topics.

- Changes in 11.2
- Changes in 11.1.0.7
- Changes in 11.1

# Changes in 11.2

## Renaming Metadata Objects

Previously, you could use the `MdmObject.setName` method to specify a name for a persistent metadata object only once. You could not change the name after setting it. Now, you can use the `setName` method to rename a metadata object. The new name does not take effect until you commit the root `Transaction` of the session. Until you commit the `Transaction`, the `getName` of the object returns the old name and the `getNewName` method returns the new name.

In Oracle Database 11*g*, Release 2 (11.2), the Oracle OLAP Java API has added the following new classes and new methods to previously existing classes.

## New Classes and Methods in 11.2

### New Classes

The following classes are new additions to the Oracle OLAP Java API. The classes are listed by package.

**`oracle.olapi.metadata`**

   `InvalidMetadataObjectInfo`
   `XML11_2_ParserCallback`

**`oracle.olapi.metadata.deployment`**

   `SecondaryPartitionLevel`

**`oracle.olapi.metadata.mdm`**

   `Mdm11_2_ObjectVisitor`

**`oracle.olapi.syntax`**

   `AssignmentCommand`
   `FromClause`
   `FromClauseElement`
   `SymmetricConditionElement`
   `UnresolvedDimensionArgument`

### New Methods

The following classes have new methods. The classes are listed by package.

**`oracle.olapi.data.source`**

   `DataProvider.reserveBuildID(BuildResult buildResult)`

**`oracle.olapi.metadata`**

   `BaseMetadataObject.getContainedByObject()`
   `InvalidMetadataException.getErrorInfoList(MetadataObject object)`
   `InvalidMetadataException.getErrorInfoList(String objectID)`

**`oracle.olapi.metadata.deployment`**

   `AWCubeOrganization.addSecondaryPartitionLevel(SecondaryPartitionLevel level, int levelNumber)`
   `AWCubeOrganization.findOrCreateSecondaryPartitionLevel(java.lang.String name)`
   `AWCubeOrganization.getSecondaryPartitionLevels()`
   `AWCubeOrganization.removeSecondaryPartitionLevel(SecondaryPartitionLevel partitionLevel)`

**`oracle.olapi.metadata.mdm`**

   `MdmPrimaryDimension.getETMemberTypeColumn()`

**`oracle.olapi.syntax`**

   `SymmetricCondition(java.util.List<SymmetricConditionElement> elements)`
   `SymmetricCondition(SymmetricConditionElement[] elements)`

## Deprecated 10*g* Classes and Methods Removed

Some classes and methods from the 10*g* release of the Oracle OLAP Java API were deprecated in the 11.1 releases. For example, all of the classes in the `oracle.olapi.metadata.mtm` package were deprecated in the 11.1 release. The documentation for the 11.2 release does not contain those deprecated 10*g* classes and methods.

# Changes in 11.1.0.7

This release of the Oracle OLAP Java API includes new features that provide the ability to do the following.

- Have all forms of metadata in the same session.
- Distinguish metadata forms with namespaces.
- Specify serial or parallel processing in some build commands.
- Aggregate over specified dimension members.
- Populate lower levels in an ET view for a dimension hierarchy with the attribute values mapped at a higher level.
- Include populated lineage attributes in a rewrite MV.
- Group attributes.
- Classify objects.
- Specify a language when mapping an attribute.
- Exclude attributes when exporting a metadata object to XML.
- Specify a prefix for the ET attribute name of a materialized view.
- Track the progress of a build.

For lists of the packages, classes, fields, methods, and property settings that are new in the 11.1.0.7 release, see [Changes in 11.1.0.7](changes_11107.md).

## Having All Metadata Forms in the Same Session

Legacy Oracle OLAP metadata objects that were created in a 10*g* version of Oracle Database can now exist in the same session as 11*g* OLAP metadata objects. This is possible because some of the top-level legacy metadata objects now have a namespace. For more information on namespaces, see the Namespaces topic.

The `oracle.olapi.data.source.DataProvider` class has the new `ALL` metadata reader mode setting, which is now the default metadata reader mode. In the `ALL` mode, the Oracle OLAP metadata reader recognizes 11*g* metadata objects and the 10*g* metadata object formats in the same session. For more information on metadata reader mode settings, see [DataProvider Settings](../oracle/olapi/data/source/doc-files/dpprops.md).

## Introducing Namespaces

A namespace identifies the metadata format and the type of an OLAP metadata object that was created in a 10*g* version of Oracle Database. The metadata objects for a 10*g* cube, measure folder, and dimension are represented in 11*g* by the `oracle.olapi.metadata.mdm.MdmObject` objects `MdmCube`, `MdmOrganizationalSchema`, and `MdmPrimaryDimension`. The `getNamespace` method of those objects returns the namespace. For an 11*g* object, the namespace is null.

The namespace of a legacy 10*g* metadata object appears as a prefix in the unique object identifier. The unique object ID is returned by the `getID` method. The namespace also appears in the `Namespace` attribute in the XML representation of the 10*g* object and in other references to the object in the XML.

The `MdmDatabaseSchema` class has findOrCreate methods that take a namespace. Using such a method, an application can find a 10*g* metadata object but cannot create one. If an object of the specified name does not exist, Oracle OLAP creates an 11*g* object.

For more information on namespaces, see [Using Namespaces](../oracle/olapi/metadata/mdm/MdmMetadataProvider.md) in the class description of `MdmMetadataProvider`.

## Specifying Serial or Parallel Processing

You can now create an `oracle.olapi.syntax.LoadCommand` that specifies the use of serial or parallel processing when loading data in an analytic workspace. The `LoadCommand` also has a `PRUNE` option, which specifies that the build spawns jobs only for the partitions for which measure data exists.

The `LoadCommand` class now has constructor methods as well as static constant fields that produce `LoadCommand` objects. One of the constructors takes the name of a `CubeMap`. With that constructor, you can specify loading data from a source other than the default data source.

The `ClearCommand` and `SolveCommand` classes also have serial and parallel processing options.

## Aggregating Over Specified Dimension Members

With the `oracle.olapi.syntax.AggregationFunctionExpression` class, you can aggregate measure values over specified dimension members. You specify the dimension members with an `AggregateOverMembersClause`. You can use an `AggregationFunctionExpression` as the `Expression` for an `MdmCustomMember` of an `MdmModel`.

## Populating Hierarchy Lineage in an ET View

In an attribute column in an embedded totals (ET) view, you can now automatically populate the rows for lower levels in a dimension hierarchy with the attribute values that are mapped at a higher level. To do so, you specify `true` with the `MdmBaseAttribute.setPopulateLineage` method.

If you specify `setPopulateLineage(false)`, then the attribute values appear only in the rows for the dimension members at the level to which the attribute is mapped. For dimension members at other levels, the attribute value is null. If you specify `setPopulateLineage(true)`, then the attribute values appear in the rows for the members of the mapped level and for the dimension members of all levels that are descendants of the mapped level.

Populating the hierarchy lineage in an ET view makes the contents of the view more like the contents of a relational table in a star schema. For example, you could create a separate long description attribute on the dimension for each `MdmDimensionLevel` of the dimension. You would specify populating the lineage of those attributes by calling the `setPopulateLineage(true)` of each attribute. You would then make the attribute visible for a dimension level by adding the attribute to the `MdmDimensionLevel` with the `addAttribute` method.

The ET view for a hierarchy of the dimension would then have a column for each of the long description attributes. Those columns would contain the long description attribute values for the members of the mapped dimension level and for the dimension members of all levels that are descendants of the mapped level.

## Including Populated Lineage Attributes in a Rewrite MV

If the `AWCubeOrganization` for a cube has a materialized view option of `REWRITE_MV_OPTION`, then Oracle OLAP creates a materialized view for the cube that can be used by the database query rewrite system. The new `REWRITE_WITH_ATTRIBUTES_MV_OPTION` of `AWCubeOrganization` enables you to include in the rewrite MV the attributes for which the `isPopulateLineage` method returns `true`.

## Grouping Attributes

With the `setAttributeGroupName` method of an `MdmBaseAttribute`, you can specify a name for an attribute group. You can specify the same group name for other attributes. For example, you could create a long description attribute for each dimension level and give each attribute the group name of "LONG_DESCRIPTION". You could use the group name to identify similar kinds of attributes.

## Classifying Objects

With the `addObjectClassification` method of an `MdmObject`, an application can add metadata to that object. The application can use the classification metadata for such purposes as identifying, grouping, or otherwise associating objects by classification.

## Specifying a Language for an Attribute

You can now specify a language when mapping an attribute by using the `findOrCreateAttributeMap(MdmBaseAttribute attribute, java.lang.String language)` method of the `oracle.olapi.metadata.mapping.DimensionMap` class.

## Excluding Attributes Through an XML Writer Callback

An implementation of the `XMLWriterCallback` interface provides Oracle OLAP the means to call back to an application while the `MdmMetadataProvider` is exporting the XML definition of an object. With an `XMLWriterCallback`, the application can specify whether or not to exclude an attribute or an owner name from the exported XML. The Oracle OLAP Java API introduced `XMLWriterCallback` in the 11.1.0.6 release.

## Specifying Column Name Prefix in a Materialized View

When Oracle OLAP creates a materialized view for a cube, it creates columns for the attributes of the dimensions of the cubes. For the name of a column, it uses the name of the attribute column from the ET view of the dimension. To insure that the column name is unique, Oracle OLAP adds a default prefix to the name. You can specify the prefix by using the `setETAttrPrefix` method of the `MdmDimensionality` object for a dimension of the cube.

## Tracking Build Results

In the 11.1.0.6 release, the Oracle OLAP Java API added the `oracle.olapi.data.source.BuildResult` class and `DataProvider.executeBuild` methods that take a `BuildResult`. With a `BuildResult`, an application can get the identification number for a build process. An analytic workspace automatically generates the identification number during a build. You can use the build number to track the progress of a build.

------------------------------------------------------------------------

# Changes in 11.1

The 11*g* release contains many changes in the Oracle OLAP Java API since the 10*g* release. The major changes are to the metadata model and the addition of the `syntax` package.

The 11*g* metadata model includes classes that an application developer can use to define metadata objects, to map the objects to database tables and views, and to deploy the objects in an analytic workspace or as relational tables and views. With other classes the developer can load data into an analytic workspace, including data that results from a series of specified calculations.

In implementing the 11*g* metadata model, the `oracle.olapi.metadata.mdm` package has many new classes and many other classes in the package have new methods. Additionally, the API includes the following new packages:

- `oracle.olapi.metadata.conversion`
- `oracle.olapi.metadata.deployment`
- `oracle.olapi.metadata.mapping`
- `oracle.olapi.session`
- `oracle.olapi.syntax`

Some aspects of the Oracle OLAP Java API are much the same as in the 10*g* releases, such as the ability to create queries with classes in the `oracle.olapi.data.source` package and to retrieve the data with classes in the `oracle.olapi.data.cursor` package. However, in Oracle OLAP 11*g* Release 1 (11.1) the API has many new features. The major new features include the abilities to do the following:

- Create and maintain persistent metadata objects.
- Restrict access to the metadata objects.
- Define and build analytic workspaces.
- Use SQL expression syntax in mapping OLAP metadata objects to relational data sources or to specify operations.
- Have multiple user sessions that share the same connection to the Oracle Database.

## Persistent Metadata Objects

The Oracle OLAP Java API now has the ability to create and maintain persistent metadata objects. The Oracle Database stores the metadata objects in the Oracle data dictionary.

An application maps the metadata objects to relational structures in an Oracle Database instance or to expressions that provide a data source. The application can deploy the metadata as relational OLAP (ROLAP) objects or it can deploy the metadata in an analytic workspace. For information on the advantages of the deployment types, see *Oracle OLAP User's Guide*.

To provide this new functionality, the Oracle OLAP Java API substantially revises the metadata model. The new model includes several new packages and has significant changes to some existing packages. For example, the `oracle.olapi.metadata.mdm` package has many new classes. It also has many new methods added to existing classes.

An application creates most metadata objects with findOrCreate methods of the owning object. For example, the following code finds the `MdmStandardDimension` named `PRODUCTS_AWJ` or creates a standard dimension with that name if it does not already exist. The `mdmDBSchema` object is the `MdmDatabaseSchema` that owns the dimension.

    MdmStandardDimension prodDim =
                mdmDBSchema.findOrCreateStandardDimension("PRODUCTS_AWJ");

Some classes and methods are deprecated in the new model. For example, all of the classes in the `oracle.olapi.metadata.mtm` package are deprecated, and methods of other classes that use the `mtm` classes are also deprecated. Some `mtm` classes mapped transient `mdm` objects to relational database structures, such as columns in tables and views. Other `mtm` specified how Oracle OLAP performed operations such as aggregation or allocation of the values of custom measures. That functionality is replaced by classes in the `oracle.olapi.metadata` subpackages `deployment`, `mapping`, and `mdm`, and the `oracle.olapi.syntax` package. With the new classes, an application can create permanent metadata objects, map them to data sources, and specify the operations that provide values for measures.

## Restrict Access To Metatdata Objects

Because the metadata objects exist in the Oracle data dictionary, an Oracle Database DBA can restrict access to certain types of the metadata objects. A client application can set such restrictions by sending SQL commands, using the JDBC API, through the JDBC connection for the user session.

## Define and Build Analytic Workspaces

An application can now define, build, and maintain analytic workspaces. This new functionality is provided by classes in the `oracle.olapi.metadata` subpackages `deployment`, `mapping`, and `mdm`, and the `oracle.olapi.syntax` package. This functionality replaces the Oracle OLAP Analytic Workspace Java API, which is entirely deprecated in this release.

## SQL Expression Syntax

With the classes in the `oracle.olap.syntax` package, an application can create Java objects that are based on SQL expressions, functions, operators, and conditions. The `SyntaxObject` class has static methods that an application can use to convert SQL expressions into Java objects or to get the SQL syntax from a Java object.

An application can create the Java objects by using the `SyntaxObject.fromSyntax` method or by using a constructor. For example, the following example creates a `StringExpression` using a `fromSyntax` method and another `StringExpression` using a constructor method. The `mp` object is the `MdmMetadataProvider` for the session.

Note that the string in the `fromSyntax` method is enclosed in single quotation marks inside the double quotation marks because the string is a SQL string literal. The single quotation marks are not required when using the constructor for a `StringExpression`.

The example then calls the `getValue` method on both `StringExpression` objects and displays the values returned. It also calls the `toSyntax` method on one `StringExpression` and displays the result.

    StringExpression exp = (StringExpression)
                SyntaxObject.fromSyntax("'Hello world from syntax.'", mp);
    StringExpression strExp =
          new StringExpression("Hello world using constructor.");
    println(exp.getValue() + "         Output of exp.getValue().");
    println(strExp.getValue() + "   Ouput of strExp.getValue().");
    println(strExp.toSyntax()+ " Ouput of strExp.toSyntax().");

The output of the code is the following:

    Hello world from syntax.         Output of exp.getValue().
    Hello world using constructor.   Output of strExp.getValue().
    'Hello world using constructor.' Output of strExp.toSyntax().

## Multiple Sessions Sharing a Connection

Another new feature is the ability to have multiple user sessions that share the same JDBC connection to the Oracle Database instance and that share the same cache of metadata objects. This ability is provided by the `UserSession` class in the `oracle.olapi.session` package.

------------------------------------------------------------------------

Copyright © 2002, 2018, Oracle. All rights reserved.
