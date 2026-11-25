Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](MdmMetadataProperty.md)
- [Next Class](MdmModel.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.olapi.metadata.mdm

## Class MdmMetadataProvider

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataProvider](../BaseMetadataProvider.md)

  - - oracle.olapi.metadata.mdm.MdmMetadataProvider

<!-- -->

- All Implemented Interfaces:
  [MetadataProvider](../MetadataProvider.md)

  ------------------------------------------------------------------------



      public class MdmMetadataProvider
      extends BaseMetadataProvider
      implements MetadataProvider

  An object that gives access to Oracle OLAP metadata objects. An application gets an `MdmMetadataProvider` by calling the `getMdmMetadataProvider` method of the `DataProvider` that it is using.
  Oracle OLAP metadata objects are contained by `MdmSchema` objects. The top-level, or root, schema is an instance of `MdmRootSchema`. The root schema has subschemas that are instances of `MdmDatabaseSchema`. Each database user has an associated `MdmDatabaseSchema`, which contains the metadata objects that are owned by that user.

  **Getting or Creating Metadata Objects**

  An application creates metadata objects in the context of an `MdmDatabaseSchema`. It does so by calling methods such as the `findOrCreateAW` and `findOrCreateStandardDimension` method of the `MdmDatabaseSchema`.

  To get Oracle OLAP metadata objects, an application first calls the `getRootSchema` method of the `MdmMetadataProvider`. The application can then get all of the metadata objects available by calling methods of the `MdmRootSchema` such as `getDatabaseSchemas` and `getDimensions`.

  To get the metadata objects for an individual user, an application can call the `getDatabaseSchema(String name)` method of the `MdmRootSchema`. The application can then call methods of the `MdmDatabaseSchema` to get the objects owned by it.

  When an application references metadata through an `MdmMetadataProvider`, Oracle OLAP retrieves information about the metadata and caches that information using the resources of the application. By calling the `flushDeletedObjects` method, an application can free the resources for metadata objects it has removed from an `MdmSchema`.

  **Importing and Exporting XML Definitions**

  An application can also get metadata objects by importing XML definitions of those objects with the `importXML` methods of an `MdmMetadataProvider`. It can export object definitions as XML with the `exportFullXML` and `exportIncrementalXML` methods. The `exportFullXML` methods write the XML for the objects that are specified by the `objects` parameter or the XML for the objects that the application has created or modified since the `Transaction` specified by the `sinceTxn` parameter.

  All objects that share an ancestor are grouped together in the exported XML. For any object that is not a top-level object and whose top-level container is not in the object list, the XML definition is an incremental definition to the object and a full definition below that. This supports the export of objects such as a calculated measure in a cube without having to export the whole cube.

  If an `MdmDatabaseSchema` is in the `objects` list, then the export includes all objects within the database schema. If an `AW` is in the `objects` list, then the export includes all objects that belong to the `AW`. If the `MdmRootSchema` is in the list, it is ignored.

  An `exportIncrementalXML` method records only the changes to an object. For any object, the method writes only the XML that is different than the XML for the object in the specified `Transaction` or in specified list of objects or both. The incremental XML includes the type and name of the objects in the ownership hierarchy of the changed object. For an example of using `exportFullXML` and `exportIncrementalXML` methods, see Example 1 in [Examples for MdmMetadataProvider](doc-files/mdmmpexamples.md).

  With the `renameMap` parameter of an `exportFullXML` or `exportIncrementalXML` method, you can specify a different name for an object that you export. You can then import the template in which the object has the new name. After committing the `Transaction` to save the object with the new name, you then have two instances of the object under different names.

  The `bindVariables` parameter of an `exportFullXML` or `exportIncrementalXML` method is like a SQL bind variable. With it you can specify a reference to a `BaseMetadataObject` object as a key and a bind variable as the value for the key. During the export of the XML, the Oracle OLAP XML generator replaces the name of the referenced object with the bind variable. The `bindValues` parameter of an `importXML` method specifies values that Oracle OLAP uses to replace bind variables when importing an XML string. For an example of exporting and importing XML using bind variables and values, see Example 2 in [Examples for MdmMetadataProvider](doc-files/mdmmpexamples.md).

  If an application provides a `bindVariables` parameter that is not `null`, then the XML produced by an `exportFullXML` or `exportIncrementalXML` method begins with the following declaration.


       <!DOCTYPE Metadata [
       <!ENTITY % BIND_VALUES PUBLIC "OLAP BIND VALUES" "OLAP METADATA">
       %BIND_VALUES;
       ]>

  A value specified in the `bindVariables` map appears in the exported XML in the format `"&BV;"`, where `BV` is the bind variable. The `importXML` methods import XML representations of objects that are owned by an `MdmDatabaseSchema` and either create new objects or modify existing objects. If the value of the `modifyIfExists` parameter is `true` and if the imported XML contains a full definition for an object that already exists and the object definition is different from the XML, then the method merges the new or changed elements of the object definition with the existing definition of the object. If the value of `modifyIfExists` is `false` and if the XML contains a full definition for an object that already exists and the object is different from the XML, then this method throws an exception.

  If an application provides a `bindValues` parameter that is not `null`, then the `inXML` string that it provides to an `importXML` method must include that `!DOCTYPE Metadata` declaration and the bind variables in the XML to import must be in the `"&BV;"` format.

  With the `callback` parameter, you can pass an implementation of the `XMLWriterCallback` interface to an `exportXML` method. With the `XMLWriterCallback`, you can specify whether or not to exclude an attribute or an owner name from the exported XML.

  With the `parserCallback` parameter, you can pass an implementation of the `XMLParserCallback` or `XML11_2_ParserCallback` interface to an `importXML` method. With the `XMLParserCallback`, you can specify how Oracle OLAP handles an error that might occur when importing XML. The `XML11_2_ParserCallback` interface adds methods for renaming the object being imported and for suppressing attributes of the imported object.

  With the `targetVersion` parameter of an `exportFullXML` or `exportIncrementalXML` method, you can specify the version of Oracle Database that you want the exported XML to be compatible with. The current valid values for that parameter are 11.1, 11.1.0.7, and 11.2.

  You can import any XML that has a version that is equal to or less than the version of the session that you are in. For example, you can import an 11.1.0.7 XML object definition into an 11.2 instance, but not vice versa. The version is determined by the compatibility mode of the server. For example, if you have an 11.2 installation but it is running in 11.1 compatibility mode, then you cannot import an 11.2 XML document.

  **Using Namespaces**

  An `MdmCube`, `MdmOrganizationalSchema`, or `MdmPrimaryDimension` can have a namespace associated with it. The Oracle OLAP Java API introduced namespaces in release 11.1.0.7 to allow legacy metadata objects to exist in the same session as current metadata objects.

  Legacy metadata objects are Oracle OLAP 10*g* `MdmObject` objects that were created by using classes in the `oracle.olapi.AWXML` package of the Oracle OLAP Analytic Workspace Java API or by using CWM PL/SQL packages. Before release 11.1.0.7, the Oracle OLAP metadata reader could only recognize legacy metadata objects if the `DataProvider` was in a compatible mode. For information on metadata reader modes, see the description of the `MetadataReaderMode` setting in [DataProvider Settings](../../data/source/doc-files/dpprops.md).

  Metadata objects in 11*g* do not have a namespace, so the default namespace is an empty string. The unique object identifier for an 11*g* cube, dimension, or organizational schema has the form *ownerName.objectName*. An example is `GLOBAL.PRODUCT_AW`.

  The namespace of a legacy metadata object begins with either `AWXML_` or `CWM_` and then has the type of object, such as `CUBE` or `DIMENSION`. For a legacy 10*g* metadata object, the namespace is the first part of the unique object identifier. The namespace is followed by the namespace delimiter, which is two periods. An example of the unique object ID of a 10*g* dimension is `AWXML_DIMENSION..GLOBAL.PRODUCT_AW`.

  The valid namespaces are represented by the static constant fields of this class. The `getValidNamespaces` method returns a `List` of the valid namespaces, including the default namespace. An application cannot create a new namespace.

  You can use the constant fields to get a legacy metadata object from an `MdmDatabaseSchema`. For example, the following code gets the `PRODUCT_AW` dimension. In the code, `mdmDBSchema` is the `MdmDatabaseSchema` for the GLOBAL user.

       MdmStandardDimension mdmProdAWDim =
                            mdmDBSchema.findOrCreateStandardDimension("PRODUCT_AW",
                                      MdmMetadataProvider.AWXML_DIMENSION_NAMESPACE);

  If the specified legacy object does not exist, Oracle OLAP creates a new 11*g* object.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `AWXML_CUBE_NAMESPACE`<br>A constant that represents the namespace for a cube that was created using 10*g* `oracle.olapi.AWXML` classes.             |
    | `static java.lang.String` | `AWXML_DIMENSION_NAMESPACE`<br>A constant that represents the namespace for a dimension that was created using 10*g* `oracle.olapi.AWXML` classes.   |
    | `static java.lang.String` | `AWXML_FOLDER_NAMESPACE`<br>A constant that represents the namespace for a measure folder that was created using 10*g* `oracle.olapi.AWXML` classes. |
    | `static java.lang.String` | `CWM_CUBE_NAMESPACE`<br>A constant that represents the namespace for a cube that was created using 10*g* CWM PL/SQL packages.                        |
    | `static java.lang.String` | `CWM_DIMENSION_NAMESPACE`<br>A constant that represents the namespace for a dimension that was created using 10*g* CWM PL/SQL packages.              |
    | `static java.lang.String` | `CWM_FOLDER_NAMESPACE`<br>A constant that represents the namespace for a measure folder that was created using 10*g* CWM PL/SQL packages.            |
    | `static java.lang.String` | `DEFAULT_NAMESPACE`<br>A constant that represents the default namespace.                                                                             |
    | `static java.lang.String` | `NAMESPACE_DELIMITER`<br>A constant that represents the namespace delimiter, which follows the namespace in the object ID.                           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`          | `exportFullXML``(java.util.List objects, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `String` the full XML for all of the objects listed and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `java.lang.String`          | `exportFullXML``(java.util.List objects, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `String` the full XML for all of the objects listed, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                                                                                                                                                                                            |
    | `java.lang.String`          | `exportFullXML``(java.util.List objects, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `String` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                                                                                                                                                                                                |
    | `java.lang.String`          | `exportFullXML``(java.util.List objects, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `String` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.                                                                                                                                                                           |
    | `java.lang.String`          | `exportFullXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `java.lang.String`          | `exportFullXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                                                                                               |
    | `java.lang.String`          | `exportFullXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                                                                                                   |
    | `java.lang.String`          | `exportFullXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.                                                                              |
    | `void`                      | `exportFullXML``(java.io.Writer writer, java.util.List objects, java.util.Map renameMap)`<br>Exports to a `Writer` the full XML for all of the objects listed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                      | `exportFullXML``(java.io.Writer writer, java.util.List objects, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `Writer` the full XML for all of the objects listed and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                      | `exportFullXML``(java.io.Writer writer, java.util.List objects, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `Writer` the full XML for all of the objects listed, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                      | `exportFullXML``(java.io.Writer writer, java.util.List objects, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `Writer` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                                                                                                                                                                         |
    | `void`                      | `exportFullXML``(java.io.Writer writer, java.util.List objects, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `Writer` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.                                                                                                                                                    |
    | `void`                      | `exportFullXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap)`<br>Exports to a `Writer` the full XML for all objects that have been created or modified since the specified `Transaction`.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                      | `exportFullXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `Writer` the full XML for all objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                      | `exportFullXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `Writer` the full XML for all of the objects that have been created or modified since the specified transaction, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                                                                   |
    | `void`                      | `exportFullXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `Writer` the full XML for all of the objects that have been created or modified since the specified transaction, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                                                                       |
    | `void`                      | `exportFullXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `Writer` the full XML for all of the objects that have been created or modified since the specified transaction, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.                                                  |
    | `java.lang.String`          | `exportIncrementalXML``(java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                                               |
    | `java.lang.String`          | `exportIncrementalXML``(java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                                         |
    | `java.lang.String`          | `exportIncrementalXML``(java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                                             |
    | `java.lang.String`          | `exportIncrementalXML``(java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.                        |
    | `java.lang.String`          | `exportIncrementalXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                                                                                 |
    | `java.lang.String`          | `exportIncrementalXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                                                                           |
    | `java.lang.String`          | `exportIncrementalXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                                                                               |
    | `java.lang.String`          | `exportIncrementalXML``(`[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.                                                          |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap)`<br>Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                        |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                  |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                      |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, java.util.List objects, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database. |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap)`<br>Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString)`<br>Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables)`<br>Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.                                                                                                                                                                                                                                    |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback)`<br>Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.                                                                                                        |
    | `void`                      | `exportIncrementalXML``(java.io.Writer writer, `[`Transaction`](../../transaction/Transaction.md)` sinceTxn, java.util.Map renameMap, boolean includeOwnerString, java.util.Map bindVariables, `[`XMLWriterCallback`](../XMLWriterCallback.md)` callback, java.lang.String targetVersion)`<br>Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.                                   |
    | [`MdmObject`](MdmObject.md) | `getMetadataObject``(java.lang.String id)`<br>Gets the `MdmObject` that has the specified unique object identifier.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `java.util.List`            | `getMetadataObjects``(java.lang.String[] ids)`<br>Gets a `List` that contains the specified `MdmObject` objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`MdmSchema`](MdmSchema.md) | `getRootSchema``()`<br>Gets the top-level `MdmSchema` in the data store to which this `MdmMetadataProvider` gives access.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `java.lang.String[]`        | `getValidNamespaces``()`<br>Gets the valid namespaces for metadata objects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `java.util.List`            | `importXML``(java.io.Reader in, `[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` destinationSchema, boolean modifyIfExists)`<br>Imports XML representations of objects that belong to the specified `MdmDatabaseSchema` and either creates new objects or modifies existing objects.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `java.util.List`            | `importXML``(java.io.Reader in, `[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` destinationSchema, boolean modifyIfExists, java.util.Map<java.lang.String,java.lang.String> bindValues)`<br>Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, and replaces bind variables in the XML with values.                                                                                                                                                                                                                                                                                                                                 |
    | `java.util.List`            | `importXML``(java.io.Reader in, `[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` destinationSchema, boolean modifyIfExists, java.util.Map<java.lang.String,java.lang.String> bindValues, `[`XMLParserCallback`](../XMLParserCallback.md)` parserCallback)`<br>Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, replaces bind variables in the XML with values, and specifies how to handle error conditions.                                                                                                                                                                                                                      |
    | `java.util.List`            | `importXML``(java.lang.String inXML, `[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` destinationSchema, boolean modifyIfExists)`<br>Imports XML representations of objects that belong to the specified `MdmDatabaseSchema` and either creates new objects or modifies existing objects.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.util.List`            | `importXML``(java.lang.String inXML, `[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` destinationSchema, boolean modifyIfExists, java.util.Map<java.lang.String,java.lang.String> bindValues)`<br>Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, and replaces bind variables in the XML with values.                                                                                                                                                                                                                                                                                                                            |
    | `java.util.List`            | `importXML``(java.lang.String inXML, `[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` destinationSchema, boolean modifyIfExists, java.util.Map<java.lang.String,java.lang.String> bindValues, `[`XMLParserCallback`](../XMLParserCallback.md)` parserCallback)`<br>Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, replaces bind variables in the XML with values, and specifies how to handle error conditions.                                                                                                                                                                                                                 |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataProvider](../BaseMetadataProvider.md)

      [`flushDeletedObjects`](../BaseMetadataProvider.md)`, `[`flushMetadataObjectCache`](../BaseMetadataProvider.md)`, `[`getDataProvider`](../BaseMetadataProvider.md)`, `[`getID`](../BaseMetadataProvider.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.metadata.[MetadataProvider](../MetadataProvider.md)

      [`getID`](../MetadataProvider.md)

<!-- -->

- - ### Field Detail

    - #### NAMESPACE_DELIMITER

          public static final java.lang.String NAMESPACE_DELIMITER

      A constant that represents the namespace delimiter, which follows the namespace in the object ID.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_NAMESPACE

          public static final java.lang.String DEFAULT_NAMESPACE

      A constant that represents the default namespace.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### AWXML_CUBE_NAMESPACE

          public static final java.lang.String AWXML_CUBE_NAMESPACE

      A constant that represents the namespace for a cube that was created using 10*g* `oracle.olapi.AWXML` classes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### AWXML_DIMENSION_NAMESPACE

          public static final java.lang.String AWXML_DIMENSION_NAMESPACE

      A constant that represents the namespace for a dimension that was created using 10*g* `oracle.olapi.AWXML` classes.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### AWXML_FOLDER_NAMESPACE

          public static final java.lang.String AWXML_FOLDER_NAMESPACE

      A constant that represents the namespace for a measure folder that was created using 10*g* `oracle.olapi.AWXML` classes. In 11*g*, a measure folder is an `MdmOrganizationalSchema`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CWM_CUBE_NAMESPACE

          public static final java.lang.String CWM_CUBE_NAMESPACE

      A constant that represents the namespace for a cube that was created using 10*g* CWM PL/SQL packages.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CWM_DIMENSION_NAMESPACE

          public static final java.lang.String CWM_DIMENSION_NAMESPACE

      A constant that represents the namespace for a dimension that was created using 10*g* CWM PL/SQL packages.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CWM_FOLDER_NAMESPACE

          public static final java.lang.String CWM_FOLDER_NAMESPACE

      A constant that represents the namespace for a measure folder that was created using 10*g* CWM PL/SQL packages. In 11*g*, a measure folder is an `MdmOrganizationalSchema`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getMetadataObject

          public final MdmObject getMetadataObject(java.lang.String id)
                                            throws ObjectClosedException

      Gets the `MdmObject` that has the specified unique object identifier.
      Parameters:
      `id` - A `String` that uniquely identifies an `MdmMetadataObject`.

      Returns:
      The requested `MdmObject`.

      Throws:
      [`ObjectClosedException`](../../../express/ObjectClosedException.md) - Indicates that the requested object is not available. This can occur if the `DataProvider` is no longer open.

    <!-- -->

    - #### getMetadataObjects

          public final java.util.List getMetadataObjects(java.lang.String[] ids)
                                                  throws ObjectClosedException

      Gets a `List` that contains the specified `MdmObject` objects.
      Parameters:
      `ids` - An array of `String` objects, each of which uniquely identifies an `MdmObject`.

      Returns:
      A `List` that contains an `MdmObject` for each of the specified object identifiers.

      Throws:
      [`ObjectClosedException`](../../../express/ObjectClosedException.md) - Indicates that the requested object is not available. This can occur if the `DataProvider` is no longer open.

    <!-- -->

    - #### getRootSchema

          public MdmSchema getRootSchema()

      Gets the top-level `MdmSchema` in the data store to which this `MdmMetadataProvider` gives access.
      Returns:
      The top-level `MdmSchema` in the data store.

    <!-- -->

    - #### getValidNamespaces

          public java.lang.String[] getValidNamespaces()

      Gets the valid namespaces for metadata objects. These include the default namespace and the namespaces for objects that are stored in CWM and `AWXML` formats.
      Returns:
      A `List` of `String` objects that contain the valid namespaces.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          java.util.List objects,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString,
                                          java.util.Map bindVariables,
                                          XMLWriterCallback callback,
                                          java.lang.String targetVersion)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          java.util.List objects,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString,
                                          java.util.Map bindVariables,
                                          XMLWriterCallback callback)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          java.util.List objects,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString,
                                          java.util.Map bindVariables)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects listed, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          java.util.List objects,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects listed and possibly includes the name of the owning object.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          java.util.List objects,
                                          java.util.Map renameMap)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects listed.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(java.util.List objects,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString,
                                                      java.util.Map bindVariables,
                                                      XMLWriterCallback callback,
                                                      java.lang.String targetVersion)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(java.util.List objects,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString,
                                                      java.util.Map bindVariables,
                                                      XMLWriterCallback callback)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all of the objects listed, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(java.util.List objects,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString,
                                                      java.util.Map bindVariables)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all of the objects listed, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(java.util.List objects,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all of the objects listed and possibly includes the name of the owning object.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          Transaction sinceTxn,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString,
                                          java.util.Map bindVariables,
                                          XMLWriterCallback callback,
                                          java.lang.String targetVersion)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects that have been created or modified since the specified transaction, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          Transaction sinceTxn,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString,
                                          java.util.Map bindVariables,
                                          XMLWriterCallback callback)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects that have been created or modified since the specified transaction, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          Transaction sinceTxn,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString,
                                          java.util.Map bindVariables)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all of the objects that have been created or modified since the specified transaction, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          Transaction sinceTxn,
                                          java.util.Map renameMap,
                                          boolean includeOwnerString)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final void exportFullXML(java.io.Writer writer,
                                          Transaction sinceTxn,
                                          java.util.Map renameMap)
                                   throws java.io.IOException

      Exports to a `Writer` the full XML for all objects that have been created or modified since the specified `Transaction`.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(Transaction sinceTxn,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString,
                                                      java.util.Map bindVariables,
                                                      XMLWriterCallback callback,
                                                      java.lang.String targetVersion)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(Transaction sinceTxn,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString,
                                                      java.util.Map bindVariables,
                                                      XMLWriterCallback callback)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(Transaction sinceTxn,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString,
                                                      java.util.Map bindVariables)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportFullXML

          public final java.lang.String exportFullXML(Transaction sinceTxn,
                                                      java.util.Map renameMap,
                                                      boolean includeOwnerString)
                                               throws java.io.IOException

      Exports to a `String` the full XML for all objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 java.util.List objects,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString,
                                                 java.util.Map bindVariables,
                                                 XMLWriterCallback callback,
                                                 java.lang.String targetVersion)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 java.util.List objects,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString,
                                                 java.util.Map bindVariables,
                                                 XMLWriterCallback callback)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 java.util.List objects,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString,
                                                 java.util.Map bindVariables)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 java.util.List objects,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 java.util.List objects,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(java.util.List objects,
                                                             Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString,
                                                             java.util.Map bindVariables,
                                                             XMLWriterCallback callback,
                                                             java.lang.String targetVersion)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(java.util.List objects,
                                                             Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString,
                                                             java.util.Map bindVariables,
                                                             XMLWriterCallback callback)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(java.util.List objects,
                                                             Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString,
                                                             java.util.Map bindVariables)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(java.util.List objects,
                                                             Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the specified objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.
      Parameters:
      `objects` - A `List` that contains `BaseMetadataObject` objects to export to XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString,
                                                 java.util.Map bindVariables,
                                                 XMLWriterCallback callback,
                                                 java.lang.String targetVersion)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString,
                                                 java.util.Map bindVariables,
                                                 XMLWriterCallback callback)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString,
                                                 java.util.Map bindVariables)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap,
                                                 boolean includeOwnerString)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final void exportIncrementalXML(java.io.Writer writer,
                                                 Transaction sinceTxn,
                                                 java.util.Map renameMap)
                                          throws java.io.IOException

      Exports to a `Writer` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`.
      Parameters:
      `writer` - A `Writer` that writes the XML.

      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write to the specified object.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString,
                                                             java.util.Map bindVariables,
                                                             XMLWriterCallback callback,
                                                             java.lang.String targetVersion)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, supplies an implementation of the `XMLWriterCallback` interface, and specifies a version of the database.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      `targetVersion` - A `String` that contains the Oracle Database version number that you want the exported XML to be compatible with. Valid values are 11.1, 11.1.0.7, and 11.2.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString,
                                                             java.util.Map bindVariables,
                                                             XMLWriterCallback callback)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, substitutes a bind variable for the objects specified by the `bindVariables` parameter, and supplies an implementation of the `XMLWriterCallback` interface.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      `callback` - An implementation of the `XMLWriterCallback` interface, which has methods that Oracle OLAP calls as it exports the XML definitions.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString,
                                                             java.util.Map bindVariables)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction`, possibly includes the name of the owning object, and substitutes a bind variable for the objects specified by the `bindVariables` parameter.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      `bindVariables` - A `Map` that has object references as keys and has as values `String` objects that contain bind variables.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### exportIncrementalXML

          public final java.lang.String exportIncrementalXML(Transaction sinceTxn,
                                                             java.util.Map renameMap,
                                                             boolean includeOwnerString)
                                                      throws java.io.IOException

      Exports to a `String` the XML for the attributes of the objects that have been created or modified since the specified `Transaction` and possibly includes the name of the owning object.
      Parameters:
      `sinceTxn` - The `Transaction` to compare to the one that contains the new or modified objects.

      `renameMap` - A `Map` that has object references as keys and has as values `String` objects that contain new names for the referenced objects.

      `includeOwnerString` - A `boolean` that indicates whether to include the name of the owning object in the XML.

      Returns:
      A `String` that contains the exported XML.

      Throws:
      `java.io.IOException` - Indicates that the method cannot write the XML to a `String`.

    <!-- -->

    - #### importXML

          public final java.util.List importXML(java.io.Reader in,
                                                MdmDatabaseSchema destinationSchema,
                                                boolean modifyIfExists,
                                                java.util.Map<java.lang.String,java.lang.String> bindValues,
                                                XMLParserCallback parserCallback)
                                         throws java.io.IOException,
                                                org.xml.sax.SAXException

      Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, replaces bind variables in the XML with values, and specifies how to handle error conditions.
      Parameters:
      `in` - A `Reader` that imports the XML.

      `destinationSchema` - The `MdmDatabaseSchema` to contain the new or modified objects.

      `modifyIfExists` - A `boolean` that indicates whether or not modify an existing object.

      `bindValues` - A `Map` that has keys that are bind variables and values that are `String` objects that contain the values with which to replace the bind variables.

      `parserCallback` - An `XMLParserCallback` that specifies how the XML parser should handle error conditions.

      Returns:
      A `List` that contains the objects defined by the imported XML.

      Throws:
      `java.io.IOException` - Indicates that the method encountered a problem reading in the XML.

      `org.xml.sax.SAXException` - Indicates that the method encountered a problem parsing the XML.

    <!-- -->

    - #### importXML

          public final java.util.List importXML(java.io.Reader in,
                                                MdmDatabaseSchema destinationSchema,
                                                boolean modifyIfExists,
                                                java.util.Map<java.lang.String,java.lang.String> bindValues)
                                         throws java.io.IOException,
                                                org.xml.sax.SAXException

      Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, and replaces bind variables in the XML with values.
      Parameters:
      `in` - A `Reader` that imports the XML.

      `destinationSchema` - The `MdmDatabaseSchema` to contain the new or modified objects.

      `modifyIfExists` - A `boolean` that indicates whether or not modify an existing object.

      `bindValues` - A `Map` that has keys that are bind variables and values that are `String` objects that contain the values with which to replace the bind variables.

      Returns:
      A `List` that contains the objects defined by the imported XML.

      Throws:
      `java.io.IOException` - Indicates that the method encountered a problem reading in the XML.

      `org.xml.sax.SAXException` - Indicates that the method encountered a problem parsing the XML.

    <!-- -->

    - #### importXML

          public final java.util.List importXML(java.io.Reader in,
                                                MdmDatabaseSchema destinationSchema,
                                                boolean modifyIfExists)
                                         throws java.io.IOException,
                                                org.xml.sax.SAXException

      Imports XML representations of objects that belong to the specified `MdmDatabaseSchema` and either creates new objects or modifies existing objects.
      Parameters:
      `in` - A `Reader` that imports the XML.

      `destinationSchema` - The `MdmDatabaseSchema` to contain the new or modified objects.

      `modifyIfExists` - A `boolean` that indicates whether to modify an existing object.

      Returns:
      A `List` that contains the objects defined by the imported XML.

      Throws:
      `java.io.IOException` - Indicates that the method encountered a problem importing the XML.

      `org.xml.sax.SAXException` - Indicates that the method encountered a problem parsing the XML.

    <!-- -->

    - #### importXML

          public final java.util.List importXML(java.lang.String inXML,
                                                MdmDatabaseSchema destinationSchema,
                                                boolean modifyIfExists,
                                                java.util.Map<java.lang.String,java.lang.String> bindValues,
                                                XMLParserCallback parserCallback)
                                         throws java.io.IOException,
                                                org.xml.sax.SAXException

      Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, replaces bind variables in the XML with values, and specifies how to handle error conditions.
      Parameters:
      `inXML` - A `String` that contains the XML.

      `destinationSchema` - The `MdmDatabaseSchema` to contain the new or modified objects.

      `modifyIfExists` - A `boolean` that indicates whether or not modify an existing object.

      `bindValues` - A `Map` that has keys that are bind variables and values that are `String` objects that contain the values with which to replace the bind variables.

      `parserCallback` - An `XMLParserCallback` that specifies how the XML parser should handle error conditions.

      Returns:
      A `List` that contains the objects defined by the imported XML.

      Throws:
      `java.io.IOException` - Indicates that the method encountered a problem importing the XML.

      `org.xml.sax.SAXException` - Indicates that the method encountered a problem parsing the XML.

    <!-- -->

    - #### importXML

          public final java.util.List importXML(java.lang.String inXML,
                                                MdmDatabaseSchema destinationSchema,
                                                boolean modifyIfExists,
                                                java.util.Map<java.lang.String,java.lang.String> bindValues)
                                         throws java.io.IOException,
                                                org.xml.sax.SAXException

      Imports XML representations of objects that belong to the specified `MdmDatabaseSchema`, creates new objects or modifies existing objects, and replaces bind variables in the XML with values.
      Parameters:
      `inXML` - A `String` that contains the XML.

      `destinationSchema` - The `MdmDatabaseSchema` to contain the new or modified objects.

      `modifyIfExists` - A `boolean` that indicates whether or not modify an existing object.

      `bindValues` - A `Map` that has keys that are bind variables and values that are `String` objects that contain the values with which to replace the bind variables.

      Returns:
      A `List` that contains the objects defined by the imported XML.

      Throws:
      `java.io.IOException` - Indicates that the method encountered a problem importing the XML.

      `org.xml.sax.SAXException` - Indicates that the method encountered a problem parsing the XML.

    <!-- -->

    - #### importXML

          public final java.util.List importXML(java.lang.String inXML,
                                                MdmDatabaseSchema destinationSchema,
                                                boolean modifyIfExists)
                                         throws java.io.IOException,
                                                org.xml.sax.SAXException

      Imports XML representations of objects that belong to the specified `MdmDatabaseSchema` and either creates new objects or modifies existing objects.
      Parameters:
      `inXML` - A `String` that contains the XML.

      `destinationSchema` - The `MdmDatabaseSchema` to contain the new or modified objects.

      `modifyIfExists` - A `boolean` that indicates whether to modify an existing object.

      Returns:
      A `List` that contains the objects defined by the imported XML.

      Throws:
      `java.io.IOException` - Indicates that the method encountered a problem importing the XML.

      `org.xml.sax.SAXException` - Indicates that the method encountered a problem parsing the XML.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMetadataProperty.md)
- [Next Class](MdmModel.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
