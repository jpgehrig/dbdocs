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

- [Prev Class](CustomModel.md)
- [Next Class](DataProviderMismatchException.md)

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

oracle.olapi.data.source

## Class DataProvider

- java.lang.Object

- - oracle.olapi.data.source.DataProvider

<!-- -->

-

  ------------------------------------------------------------------------



      public class DataProvider
      extends java.lang.Object

  Creates user sessions for a connection to Oracle OLAP and creates objects that an application uses in getting metadata objects, in specifying queries, and in retrieving data from a data store. A `DataProvider` is associated with a `TransactionProvider` and one or more `UserSession` objects.
  The `DataProvider` class includes methods that do the following:

  - Create a `UserSession` associated with a `oracle.jdbc.OracleConnectiown`.
  - Get the `MdmMetadataProvider` to use to get `MdmObject` metadata objects.
  - Executes a process that builds analtyic workspace objects.
  - Create `Source` objects that an application uses in producing a `Source` that defines a query.
  - Create `CursorManager` objects that an application uses in creating `Cursor` objects for retrieving the data specified by a query.
  - Create `CustomModel` objects, which are `Model` objects that an application can explicitly create.
  - Get the `FundamentalDataProvider`, which provides objects that represent the OLAP Java API data types that an application can use in defining a query.
  - Get the `TransactionProvider`, which provides `Transaction` objects. Every `Source` is associated with a specific `Transaction`.

  After creating a new `DataProvider`, an application must call a `createSession` method of the `DataProvider`. After specifying an initial `UserSession`, the application should call the `getMdmMetadataProvider` method of the `DataProvider` to get the `MdmMetadataProvider` to use.
  A `DataProvider` can create from one to many `UserSession` objects, each of which has a different connection to the Oracle Database instance. Each `UserSession` has access to a shared set of metadata objects. An application can create local metadata objects for an individual `UserSession`. The management of the `UserSession` objects is the responsibility of the application.

  For the `createList` methods, the values of the `elements` array must be unique. The array cannot contain duplicate values.

  A `DataProvider` has settings that determine certain characteristics of the `DataProvider`, By default, a `DataProvider` has the following settings:

  - It uses unique dimension hierarchy member values.
  - It recognizes all forms of metadata model objects.

  The `DataProvider` class has constructors that take a `Locale` object, or a `Locale` and either a `Properties` object or an XML `String` that specifies settings for the `DataProvider`. For a table of the property keys or setting names and the case-sensitive values for the settings, and for brief descriptions of them, see [DataProvider Settings](doc-files/dpprops.md).

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DataProvider``()`<br>Creates a `DataProvider` with the default `Locale` and the default settings.                                                              |
    | `DataProvider``(java.util.Locale defaultLocale)`<br>Creates a `DataProvider` using the specified `Locale` and the default settings.                             |
    | `DataProvider``(java.util.Locale defaultLocale, java.util.Properties defaultProperties)`<br>Creates a `DataProvider` using the specified `Locale` and settings. |
    | `DataProvider``(java.util.Locale defaultLocale, java.lang.String defaultSettings)`<br>Creates a `DataProvider` using the specified `Locale` and settings.       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                    |
    |--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                             | `close``()`<br>Closes the `DataProvider` and releases any associated resources.                                                                                                                                                                                                                                                                                                           |
    | [`BooleanSource`](BooleanSource.md)                                | `createConstantSource``(boolean element)`<br>Creates a `BooleanSource` that has only one element, which has the specified `boolean` value.                                                                                                                                                                                                                                                |
    | [`DateSource`](DateSource.md)                                      | `createConstantSource``(java.util.Date element)`<br>Creates a `DateSource` that has only one element, which has the specified `Date` value.                                                                                                                                                                                                                                               |
    | [`NumberSource`](NumberSource.md)                                  | `createConstantSource``(double element)`<br>Creates a `NumberSource` that has only one element, which has the specified `double` value.                                                                                                                                                                                                                                                   |
    | [`NumberSource`](NumberSource.md)                                  | `createConstantSource``(float element)`<br>Creates a `NumberSource` that has only one element, which has the specified `float` value.                                                                                                                                                                                                                                                     |
    | [`NumberSource`](NumberSource.md)                                  | `createConstantSource``(int element)`<br>Creates a `NumberSource` that has only one element, which has the specified `int` value.                                                                                                                                                                                                                                                         |
    | [`NumberSource`](NumberSource.md)                                  | `createConstantSource``(short element)`<br>Creates a `NumberSource` that has only one element, which has the specified `short` value.                                                                                                                                                                                                                                                     |
    | [`Source`](Source.md)                                              | `createConstantSource``(`[`Source`](Source.md)` element)`<br>Creates a `Source` that has only one element, which has the specified `Source` value.                                                                                                                                                                                                                                        |
    | [`StringSource`](StringSource.md)                                  | `createConstantSource``(java.lang.String element)`<br>Creates a `StringSource` that has only one element, which has the specified `String` value.                                                                                                                                                                                                                                         |
    | [`CursorInfoSpecification`](CursorInfoSpecification.md)            | `createCursorInfoSpecification``(`[`Source`](Source.md)` rootSource)`<br>Creates a `CursorInfoSpecification` for the specified `Source`.                                                                                                                                                                                                                                                  |
    | [`CursorManager`](../cursor/CursorManager.md)                      | `createCursorManager``(`[`Source`](Source.md)` rootSource)`<br>Creates a `CursorManager` for the specified `Source`.                                                                                                                                                                                                                                                                      |
    | [`CursorManager`](../cursor/CursorManager.md)                      | `createCursorManager``(`[`Source`](Source.md)` rootSource, int fetchSize, `[`CursorInfoSpecification`](CursorInfoSpecification.md)` cursorInfoSpec)`<br>Creates a `CursorManager` object for the specified `Source` with the specified `CursorInfoSpecification` and fetch size.                                                                                                          |
    | [`CursorManager`](../cursor/CursorManager.md)`[]`                  | `createCursorManagers``(`[`Source`](Source.md)`[] rootSources)`<br>Creates an array of `CursorManager` objects, one for each of the corresponding `Source` objects in the `rootSources` array.                                                                                                                                                                                            |
    | [`CursorManager`](../cursor/CursorManager.md)`[]`                  | `createCursorManagers``(`[`Source`](Source.md)`[] rootSource, int[] fetchSize, `[`CursorInfoSpecification`](CursorInfoSpecification.md)`[] cursorInfoSpec)`<br>Creates an array of `CursorManager` objects with the specified `CursorInfoSpecification` objects and fetch sizes.                                                                                                          |
    | [`CursorManager`](../cursor/CursorManager.md)`[]`                  | `createCursorManagers``(`[`Source`](Source.md)`[] rootSources, int[] fetchSizes, `[`CursorInfoSpecification`](CursorInfoSpecification.md)`[] cursorInfoSpecs, java.util.Properties queryProperties)`<br>Creates an array of `CursorManager` objects that can override the local or unique hierarchy value type setting of the `DataProvider`.                                             |
    | [`CursorManager`](../cursor/CursorManager.md)`[]`                  | `createCursorManagers``(`[`Source`](Source.md)`[] rootSources, int[] fetchSizes, `[`CursorInfoSpecification`](CursorInfoSpecification.md)`[] cursorInfoSpecs, java.lang.String querySettings)`<br>Creates an array of `CursorManager` objects that can override the local or unique hierarchy value type of the `DataProvider`.                                                           |
    | [`BooleanSource`](BooleanSource.md)                                | `createListSource``(boolean[] elements)`<br>Creates a `BooleanSource` with elements that have the specified `boolean` values.                                                                                                                                                                                                                                                             |
    | [`DateSource`](DateSource.md)                                      | `createListSource``(java.util.Date[] elements)`<br>Creates a `DateSource` with elements that have the specified `Date` values.                                                                                                                                                                                                                                                            |
    | [`NumberSource`](NumberSource.md)                                  | `createListSource``(double[] elements)`<br>Creates a `NumberSource` with elements that have the specified `double` values.                                                                                                                                                                                                                                                                |
    | [`NumberSource`](NumberSource.md)                                  | `createListSource``(float[] elements)`<br>Creates a `NumberSource` with elements that have the specified `float` values.                                                                                                                                                                                                                                                                  |
    | [`NumberSource`](NumberSource.md)                                  | `createListSource``(int[] elements)`<br>Creates a `NumberSource` with elements that have the specified `int` values.                                                                                                                                                                                                                                                                      |
    | [`Source`](Source.md)                                              | `createListSource``(java.lang.Object[][] tuples)`<br>Creates a `Source` that has as element values the arrays in the `tuples` array.                                                                                                                                                                                                                                                      |
    | [`NumberSource`](NumberSource.md)                                  | `createListSource``(short[] elements)`<br>Creates a `NumberSource` with elements that have the specified `short` values.                                                                                                                                                                                                                                                                  |
    | [`Source`](Source.md)                                              | `createListSource``(`[`Source`](Source.md)`[] elements)`<br>Creates a `Source` with elements that have the specified `Source` objects as values.                                                                                                                                                                                                                                          |
    | [`StringSource`](StringSource.md)                                  | `createListSource``(java.lang.String[] elements)`<br>Creates a `StringSource` with elements that have the specified `String` values.                                                                                                                                                                                                                                                      |
    | [`CustomModel`](CustomModel.md)                                    | `createModel``(`[`Source`](Source.md)` input)`<br>Creates a `CustomModel` with the specified input and a data type of Number.                                                                                                                                                                                                                                                             |
    | [`CustomModel`](CustomModel.md)                                    | `createModel``(`[`Source`](Source.md)`[] inputs)`<br>Creates a `CustomModel` with the specified inputs and a data type of Number.                                                                                                                                                                                                                                                         |
    | [`CustomModel`](CustomModel.md)                                    | `createModel``(`[`Source`](Source.md)`[] inputs, `[`Source`](Source.md)` datatype)`<br>Creates a `CustomModel` with the specified inputs and data type.                                                                                                                                                                                                                                   |
    | [`CustomModel`](CustomModel.md)                                    | `createModel``(`[`Source`](Source.md)`[] inputs, `[`Source`](Source.md)` datatype, `[`Model`](Model.md)`[] parentModels)`<br>Creates a `CustomModel` with the specified inputs, data type, and parent models.                                                                                                                                                                             |
    | [`CustomModel`](CustomModel.md)                                    | `createModel``(`[`Source`](Source.md)`[] inputs, `[`Source`](Source.md)` datatype, `[`Source`](Source.md)`[] outputs)`<br>Creates a `CustomModel` with the specified inputs, data type, and outputs.                                                                                                                                                                                      |
    | [`CustomModel`](CustomModel.md)                                    | `createModel``(`[`Source`](Source.md)`[] inputs, `[`Source`](Source.md)` datatype, `[`Source`](Source.md)`[] outputs, `[`Model`](Model.md)`[] parentModels)`<br>Creates a `CustomModel` with the specified inputs, data type, outputs, and parent models.                                                                                                                                 |
    | [`CustomModel`](CustomModel.md)                                    | `createModel``(`[`Source`](Source.md)` input, `[`Source`](Source.md)` datatype)`<br>Creates a `CustomModel` with the specified input and data type.                                                                                                                                                                                                                                       |
    | [`NumberSource`](NumberSource.md)                                  | `createRangeSource``(int bottom, int top)`<br>Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.                                                                                                                                                                                        |
    | [`NumberSource`](NumberSource.md)                                  | `createRangeSource``(int bottom, `[`NumberSource`](NumberSource.md)` top)`<br>Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.                                                                                                                                                        |
    | [`NumberSource`](NumberSource.md)                                  | `createRangeSource``(`[`NumberSource`](NumberSource.md)` bottom, int top)`<br>Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.                                                                                                                                                        |
    | [`NumberSource`](NumberSource.md)                                  | `createRangeSource``(`[`NumberSource`](NumberSource.md)` bottom, `[`NumberSource`](NumberSource.md)` top)`<br>Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.                                                                                                                        |
    | [`UserSession`](../../session/UserSession.md)                      | `createSession``(oracle.jdbc.OracleConnection newConnection)`<br>Creates a new `UserSession` that shares the `DataProvider` but that has a different `OracleConnection`.                                                                                                                                                                                                                  |
    | [`UserSession`](../../session/UserSession.md)                      | `createSession``(oracle.jdbc.OracleConnection newConnection, java.lang.String settings)`<br>Creates a new `UserSession` that shares the `DataProvider` but that has a different `OracleConnection` and has the specified settings.                                                                                                                                                        |
    | [`UserSession`](../../session/UserSession.md)                      | `createSession``(oracle.jdbc.OracleConnection newConnection, java.lang.String settings, java.util.Locale locale)`<br>Creates a new `UserSession` that shares the `DataProvider` but that has a different `OracleConnection` and has the specified settings, and language.                                                                                                                 |
    | [`SQLCursorManager`](SQLCursorManager.md)                          | `createSQLCursorManager``(`[`Source`](Source.md)` source)`<br>Creates a `SQLCursorManager` for the specified `Source`.                                                                                                                                                                                                                                                                    |
    | [`SQLCursorManager`](SQLCursorManager.md)`[]`                      | `createSQLCursorManagers``(`[`Source`](Source.md)`[] sources)`<br>Creates a `SQLCursorManager` for each `Source` in the `sources` array.                                                                                                                                                                                                                                                  |
    | [`SQLCursorManager`](SQLCursorManager.md)`[]`                      | `createSQLCursorManagers``(`[`Source`](Source.md)`[] sources, boolean createCountColumn, java.lang.String[] generatedSQLStatements)`<br>Creates a `SQLCursorManager` for each `Source` in the `sources` array and provides the SQL statements and a count column for each query.                                                                                                          |
    | [`SQLCursorManager`](SQLCursorManager.md)`[]`                      | `createSQLCursorManagers``(`[`Source`](Source.md)`[] sources, java.lang.String[] generatedSQLStatements)`<br>Creates a `SQLCursorManager` for each `Source` in the `sources` array and provides the SQL statements for each query.                                                                                                                                                        |
    | `void`                                                             | `executeBuild``(`[`BuildProcess`](../../syntax/BuildProcess.md)` buildProcess, `[`BuildProperties`](BuildProperties.md)` props)`<br>Executes the commands of a `BuildProcess` that has the specified properties.                                                                                                                                                                          |
    | `void`                                                             | `executeBuild``(`[`BuildProcess`](../../syntax/BuildProcess.md)` buildProcess, `[`BuildProperties`](BuildProperties.md)` props, `[`BuildResult`](BuildResult.md)` buildResult)`<br>Executes the commands of a `BuildProcess` that has the specified properties; the build process generates an identification number for the build and stores it in the `BuildResult`.                    |
    | `void`                                                             | `executeBuild``(`[`BuildProcess`](../../syntax/BuildProcess.md)` buildProcess, int parallelism)`<br>Executes the commands of a `BuildProcess` using the specified number of parallel processes.                                                                                                                                                                                           |
    | `void`                                                             | `executeBuild``(`[`BuildProcess`](../../syntax/BuildProcess.md)` buildProcess, int parallelism, `[`BuildResult`](BuildResult.md)` buildResult)`<br>Executes the commands of a `BuildProcess` using the specified number of parallel processes; the build process generates an identification number for the build and stores it in the `BuildResult`.                                     |
    | `void`                                                             | `executeBuild``(`[`MdmNamedBuildProcess`](../../metadata/mdm/MdmNamedBuildProcess.md)` namedBuildProcess, int parallelism)`<br>Executes the commands of an `MdmNamedBuildProcess` using the specified number of parallel processes.                                                                                                                                                       |
    | `void`                                                             | `executeBuild``(`[`MdmNamedBuildProcess`](../../metadata/mdm/MdmNamedBuildProcess.md)` namedBuildProcess, int parallelism, `[`BuildResult`](BuildResult.md)` buildResult)`<br>Executes the commands of an `MdmNamedBuildProcess` using the specified number of parallel processes; the build process generates an identification number for the build and stores it in the `BuildResult`. |
    | `oracle.jdbc.OracleConnection`                                     | `getConnection``()`<br>Gets the `oracle.jdbc.OracleConnectiown` object that represents the connection between a client application and Oracle OLAP in the Oracle Database instance.                                                                                                                                                                                                       |
    | [`MetadataProvider`](../../metadata/MetadataProvider.md)           | `getDefaultMetadataProvider``()`<br>Gets the default `MetadataProvider` that is associated with this `DataProvider`; this method provides backward compatibility with previous versions of the Oracle OLAP Java API.                                                                                                                                                                      |
    | [`UserSession`](../../session/UserSession.md)                      | `getDefaultUserSession``()`<br>Gets the default `UserSession` associated with this `DataProvider`.                                                                                                                                                                                                                                                                                        |
    | [`Source`](Source.md)                                              | `getEmptySource``()`<br>Gets the empty `Source`, which does not have any elements.                                                                                                                                                                                                                                                                                                        |
    | [`FundamentalMetadataProvider`](FundamentalMetadataProvider.md)    | `getFundamentalMetadataProvider``()`<br>Gets the `FundamentalMetadataProvider` for this `DataProvider`.                                                                                                                                                                                                                                                                                   |
    | [`MdmMetadataProvider`](../../metadata/mdm/MdmMetadataProvider.md) | `getMdmMetadataProvider``()`<br>Gets the `MdmMetadataProvider` that is associated with this `DataProvider`.                                                                                                                                                                                                                                                                               |
    | [`Transaction`](../../transaction/Transaction.md)                  | `getRootTransaction``(oracle.jdbc.OracleConnection connection)`<br>Gets the root `Transaction` for the specified `OracleConnection`.                                                                                                                                                                                                                                                      |
    | [`TransactionProvider`](../../transaction/TransactionProvider.md)  | `getTransactionProvider``()`<br>Gets the `TransactionProvider` associated with this `DataProvider`.                                                                                                                                                                                                                                                                                       |
    | [`Source`](Source.md)                                              | `getVoidSource``()`<br>Gets the void `Source` object, which has a single element that has `null` as the value.                                                                                                                                                                                                                                                                            |
    | `boolean`                                                          | `isOpen``()`<br>Indicates whether the connection to the Oracle Database instance is currently open.                                                                                                                                                                                                                                                                                       |
    | `void`                                                             | `reserveBuildID``(`[`BuildResult`](BuildResult.md)` buildResult)`<br>Reserves an identification number for the build and stores it in the `BuildResult`.                                                                                                                                                                                                                                  |
    | `void`                                                             | `setDefaultUserSession``(`[`UserSession`](../../session/UserSession.md)` defaultSession)`<br>Specifies the `UserSession` to associate with this `DataProvider` if a `UserSession` is not already associated with the active `Transaction`.                                                                                                                                                |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DataProvider

          public DataProvider()

      Creates a `DataProvider` with the default `Locale` and the default settings.

    <!-- -->

    - #### DataProvider

          public DataProvider(java.util.Locale defaultLocale)

      Creates a `DataProvider` using the specified `Locale` and the default settings.
      Parameters:
      `defaultLocale` - The `Locale` to use as the default.

    <!-- -->

    - #### DataProvider

          public DataProvider(java.util.Locale defaultLocale,
                              java.lang.String defaultSettings)
                       throws org.xml.sax.SAXException

      Creates a `DataProvider` using the specified `Locale` and settings. For the settings that you can specify, see [DataProvider Settings](doc-files/dpprops.md).
      The following is an example of creating a `DataProvider` and specifying settings with a `String` in XML format. The settings specify using local dimension member values and recognizing only 11*g* metadata objects.


           String settings = "<olapsettings>
                                <setting name = 'HierarchyValueType' value = 'local' />
                                <setting name = 'MetadataReaderMode' value = '11_ONLY' />
                              </olapsettings>";
           DataProvider dp = new DataProvider(null, settings);

      Parameters:
      `defaultLocale` - The `Locale` to use as the default for `UserSession` objects created by this `DataProvider`.

      `defaultSettings` - A `String` that contains an XML representation of the settings to use as the default values for `UserSession` objects created by this `DataProvider`.

      Throws:
      `org.xml.sax.SAXException` - Indicates a problem with the XML in the `defaultSettings` string.

    <!-- -->

    - #### DataProvider

          public DataProvider(java.util.Locale defaultLocale,
                              java.util.Properties defaultProperties)

      Creates a `DataProvider` using the specified `Locale` and settings. For the settings that you can specify, see [DataProvider Settings](doc-files/dpprops.md).
      The following is an example of creating a `DataProvider` and specifying settings with a `Properties` object. The settings specify using local dimension member values and recognizing only 10*g* analytic workspace metadata.

           Properties props = new Properties();
           props.setProperty("HierarchyValueType", "local");
           props.setProperty("MetadataReaderMode", "10103ONLY");
           DataProvider dp = new DataProvider(null, props);

      Parameters:
      `defaultLocale` - The `Locale` to use as the default.

      `defaultProperties` - A `Properties` object that contains settings to use as the default values.

  <!-- -->

  - ### Method Detail

    - #### createConstantSource

          public final NumberSource createConstantSource(double element)

      Creates a `NumberSource` that has only one element, which has the specified `double` value.
      Parameters:
      `element` - A `double` to be the value of the new `NumberSource`.

      Returns:
      A `NumberSource` that has the specified `double` value.

    <!-- -->

    - #### createConstantSource

          public final NumberSource createConstantSource(float element)

      Creates a `NumberSource` that has only one element, which has the specified `float` value.
      Parameters:
      `element` - A `float` to be the value of the new `NumberSource`.

      Returns:
      A `NumberSource` that has the specified `float` value.

    <!-- -->

    - #### createConstantSource

          public final NumberSource createConstantSource(int element)

      Creates a `NumberSource` that has only one element, which has the specified `int` value.
      Parameters:
      `element` - An `int` to be the value of the new `NumberSource`.

      Returns:
      A `NumberSource` that has the specified `int` value.

    <!-- -->

    - #### createConstantSource

          public final StringSource createConstantSource(java.lang.String element)

      Creates a `StringSource` that has only one element, which has the specified `String` value.
      Parameters:
      `element` - A `String` to be the value of the new `StringSource`.

      Returns:
      A `StringSource` that has the specified `String` value.

    <!-- -->

    - #### createConstantSource

          public final DateSource createConstantSource(java.util.Date element)

      Creates a `DateSource` that has only one element, which has the specified `Date` value.
      Parameters:
      `element` - A `Date` to be the value of the new `DateSource`.

      Returns:
      A `DateSource` that has the specified `Date` value.

    <!-- -->

    - #### createConstantSource

          public final Source createConstantSource(Source element)

      Creates a `Source` that has only one element, which has the specified `Source` value.
      Parameters:
      `element` - A `Source` to be the value of the new `Source`.

      Returns:
      A `Source` that has an element that has the specified `Source` as the value.

    <!-- -->

    - #### createConstantSource

          public final NumberSource createConstantSource(short element)

      Creates a `NumberSource` that has only one element, which has the specified `short` value.
      Parameters:
      `element` - A `short` to be the value of the new `NumberSource`.

      Returns:
      A `NumberSource` that has the specified `short` value.

    <!-- -->

    - #### createConstantSource

          public final BooleanSource createConstantSource(boolean element)

      Creates a `BooleanSource` that has only one element, which has the specified `boolean` value.
      Parameters:
      `element` - A `boolean` to be the value of the new `BooleanSource`.

      Returns:
      A `BooleanSource` that has the specified `boolean` value.

    <!-- -->

    - #### createCursorManager

          public final CursorManager createCursorManager(Source rootSource)

      Creates a `CursorManager` for the specified `Source`.
      Parameters:
      `rootSource` - The `Source` for the new `CursorManager`.

      Returns:
      The `CursorManager` for the specified `Source`.

    <!-- -->

    - #### createCursorManagers

          public final CursorManager[] createCursorManagers(Source[] rootSources)

      Creates an array of `CursorManager` objects, one for each of the corresponding `Source` objects in the `rootSources` array.
      Parameters:
      `rootSources` - The `Source` objects for the `CursorManager` objects.

      Returns:
      An array of `CursorManager` objects, one for each `Source`.

    <!-- -->

    - #### createCursorManager

          public final CursorManager createCursorManager(Source rootSource,
                                                         int fetchSize,
                                                         CursorInfoSpecification cursorInfoSpec)

      Creates a `CursorManager` object for the specified `Source` with the specified `CursorInfoSpecification` and fetch size. A fetch size of -1 specifies fetching the entire result set.
      Parameters:
      `rootSource` - The `Source` for the new `CursorManager`.

      `fetchSize` - An integer that specifies the fetch size for the `Cursor` objects created by the `CursorManager`.

      `cursorInfoSpec` - A `CursorInfoSpecification` for the `CursorManager`.

      Returns:
      A `CursorManager` for the `Source`.

    <!-- -->

    - #### createCursorManagers

          public CursorManager[] createCursorManagers(Source[] rootSource,
                                                      int[] fetchSize,
                                                      CursorInfoSpecification[] cursorInfoSpec)

      Creates an array of `CursorManager` objects with the specified `CursorInfoSpecification` objects and fetch sizes. The array contains one `CursorManager` for each `Source` in the `rootSource` array. The `fetchSize` and `cursorInfoSpec` arrays supply a fetch size and a `CursorInfoSpecification` for the `CursorManager` for the corresponding `Source` in the `rootSource` array. A fetch size of -1 specifies fetching the entire result set.
      Parameters:
      `rootSource` - An array of `Source` objects for the `CursorManager` objects.

      `fetchSize` - An array of integers that specify the fetch sizes for the `Cursor` objects created by the corresponding `CursorManager` objects.

      `cursorInfoSpec` - An array of `CursorInfoSpecification` objects for the corresponding `CursorManager` objects.

      Returns:
      An array of `CursorManager` objects for the corresponding `Source` objects.

    <!-- -->

    - #### reserveBuildID

          public void reserveBuildID(BuildResult buildResult)

      Reserves an identification number for the build and stores it in the `BuildResult`.
      Parameters:
      `buildResult` - A `BuildResult` to contain an identification number that you can use to identify a build.

    <!-- -->

    - #### executeBuild

          public final void executeBuild(BuildProcess buildProcess,
                                         BuildProperties props)

      Executes the commands of a `BuildProcess` that has the specified properties.
      Parameters:
      `buildProcess` - A `BuildProcess` that contains the build commands to execute.

      `props` - A `BuildProperties` that specifies properties for the build.

    <!-- -->

    - #### executeBuild

          public void executeBuild(BuildProcess buildProcess,
                                   BuildProperties props,
                                   BuildResult buildResult)

      Executes the commands of a `BuildProcess` that has the specified properties; the build process generates an identification number for the build and stores it in the `BuildResult`.
      Parameters:
      `buildProcess` - A `BuildProcess` that contains the build commands to execute.

      `props` - A `BuildProperties` that specifies properties for the build.

      `buildResult` - A `BuildResult` to contain an identification number that is generated by the build.

    <!-- -->

    - #### executeBuild

          public void executeBuild(BuildProcess buildProcess,
                                   int parallelism,
                                   BuildResult buildResult)

      Executes the commands of a `BuildProcess` using the specified number of parallel processes; the build process generates an identification number for the build and stores it in the `BuildResult`.
      Parameters:
      `buildProcess` - A `BuildProcess` that contains the build commands to execute.

      `parallelism` - An integer that specifies the number of processes to allocate for parallel execution of the commands. The value can be 0 (zero) or more.

      `buildResult` - A `BuildResult` to contain an identification number that is generated by the build.

    <!-- -->

    - #### executeBuild

          public void executeBuild(BuildProcess buildProcess,
                                   int parallelism)

      Executes the commands of a `BuildProcess` using the specified number of parallel processes.
      Parameters:
      `buildProcess` - A `BuildProcess` that contains the build commands to execute.

      `parallelism` - An integer that specifies the number of processes to allocate for parallel execution of the commands. The value can be 0 (zero) or more.

    <!-- -->

    - #### executeBuild

          public void executeBuild(MdmNamedBuildProcess namedBuildProcess,
                                   int parallelism,
                                   BuildResult buildResult)

      Executes the commands of an `MdmNamedBuildProcess` using the specified number of parallel processes; the build process generates an identification number for the build and stores it in the `BuildResult`.
      Parameters:
      `namedBuildProcess` - An `MdmNamedBuildProcess` with the build commands to execute.

      `parallelism` - An integer that specifies the number of processes to allocate for parallel execution of the commands. The value can be 0 (zero) or more.

      `buildResult` - A `BuildResult` to contain an identification number that is generated by the build.

    <!-- -->

    - #### executeBuild

          public void executeBuild(MdmNamedBuildProcess namedBuildProcess,
                                   int parallelism)

      Executes the commands of an `MdmNamedBuildProcess` using the specified number of parallel processes.
      Parameters:
      `namedBuildProcess` - The `MdmNamedBuildProcess` with the commands to execute.

      `parallelism` - An integer that specifies the number of processes to allocate for parallel execution of the commands. The value can be 0 (zero) or more.

    <!-- -->

    - #### createCursorInfoSpecification

          public final CursorInfoSpecification createCursorInfoSpecification(Source rootSource)
                                                                      throws TransactionalObjectInvalidException

      Creates a `CursorInfoSpecification` for the specified `Source`.
      Parameters:
      `rootSource` - The `Source` for the `CursorInfoSpecification`.

      Returns:
      The `CursorInfoSpecification` for the specified `Source`.

      Throws:
      [`TransactionalObjectInvalidException`](../../transaction/TransactionalObjectInvalidException.md) - Indicates that the `Source` is not valid in the current `Transaction`.

    <!-- -->

    - #### createListSource

          public final NumberSource createListSource(double[] elements)

      Creates a `NumberSource` with elements that have the specified `double` values.
      Parameters:
      `elements` - An array of `double` values.

      Returns:
      A `NumberSource` with elements that have the specified `double` values.

    <!-- -->

    - #### createListSource

          public final NumberSource createListSource(float[] elements)

      Creates a `NumberSource` with elements that have the specified `float` values.
      Parameters:
      `elements` - An array of `float` values.

      Returns:
      A `NumberSource` with elements that have the specified `float` values.

    <!-- -->

    - #### createListSource

          public final NumberSource createListSource(int[] elements)

      Creates a `NumberSource` with elements that have the specified `int` values.
      Parameters:
      `elements` - An array of `int` values.

      Returns:
      A `NumberSource` with elements that have the specified `int` values.

    <!-- -->

    - #### createListSource

          public final StringSource createListSource(java.lang.String[] elements)

      Creates a `StringSource` with elements that have the specified `String` values.
      Parameters:
      `elements` - An array of `String` values.

      Returns:
      A `StringSource` with elements that have the specified `String` values.

    <!-- -->

    - #### createListSource

          public final DateSource createListSource(java.util.Date[] elements)

      Creates a `DateSource` with elements that have the specified `Date` values.
      Parameters:
      `elements` - An array of `Date` values.

      Returns:
      A `DateSource` with elements that have the specified `Date` values.

    <!-- -->

    - #### createListSource

          public final Source createListSource(Source[] elements)

      Creates a `Source` with elements that have the specified `Source` objects as values.
      Parameters:
      `elements` - An array of `Source` objects.

      Returns:
      A `Source` with elements that have the specified `Source` objects as values.

    <!-- -->

    - #### createListSource

          public final NumberSource createListSource(short[] elements)

      Creates a `NumberSource` with elements that have the specified `short` values.
      Parameters:
      `elements` - An array of `short` values.

      Returns:
      A `NumberSource` with elements that have the specified `short` values.

    <!-- -->

    - #### createListSource

          public final BooleanSource createListSource(boolean[] elements)

      Creates a `BooleanSource` with elements that have the specified `boolean` values.
      Parameters:
      `elements` - An array of `boolean` values.

      Returns:
      A `BooleanSource` with elements that have the specified `boolean` values.

    <!-- -->

    - #### createListSource

          public final Source createListSource(java.lang.Object[][] tuples)

      Creates a `Source` that has as element values the arrays in the `tuples` array. Each array in the `tuples` array specifies a member for one or more `MdmSubDimension` objects or elements of `MdmAttribute` objects. `MdmSubDimension` member values are always `String` objects. An `MdmAttribute` can be of any data type; to specify a value of an element of an `MdmAttribute`, you must encapsulate the value in an appropriate `java.lang` class. For example, if you want to specify a value for the level depth attribute, then you must wrap the integer in the `java.lang.Number` class. Valid object types are `Boolean`, `Date`, `Number`, and `String`. You cannot use a `Source` object as a value of a component array.
      You typically use the `Source` returned by this method as the `comparison` parameter in a `join` method, or as the parameter for the `selectValues` method, of a `Source` that has the one of the dimensions as the type and the other dimensions as the types of the outputs. If you use the `Source` returned by this method in either those ways, then the order of the elements of the each array in the `tuples` array must match the order of the elements of the `Source` for which the arrays are providing the values.

      The data types of the corresponding elements of each component array must match. For example, if the data types of the elements of the first array are `String`, `Number`, and `Date`, in that order, then the data types of the elements of the other arrays must also be `String`, `Number`, and `Date` in the same order.

      The following example creates `custSel`, which specifies one member of a hierarchy of a Customer dimension, and `edge`, which represents hierarchies of other dimensions for an edge of a cube. Next it creates `edgeSel`, which specifies members for the hierarchies of `edge`. All of the values are `String` objects. The example then joins the dimension selections to a measure.

      In the code, `shipHier`, `prodHier`, `calHier`, and `chanHier` are `StringSource` objects for the `SHIPMENTS`, `PRODUCT`, `CALENDAR`, and `CHANNEL` hierarchies, respectively. The `dp` object is the `DataProvider`, and `units` is the `Source` for a measure of unit quantities sold.

           Source custSel = shipHier.selectValue(
                                            "SHIPMENTS::SHIP_TO::WARREN SYS NY");

           Source edge = prodHier.join(calHier).join(chanHier);

           Source edgeSel = edge.selectValues(dp.createListSource(
                                              new Object [][] {
                                              {"PRODUCT_PRIMARY::ITEM::ENVY STD",
                                               "CALENDAR_YEAR::MONTH::1998.03",
                                               "CHANNEL_PRIMARY::CHANNEL::CAT"},
                                              {"PRODUCT_PRIMARY::ITEM::ENVY STD",
                                               "CALENDAR_YEAR::MONTH::1998.04",
                                               "CHANNEL_PRIMARY::CHANNEL::CAT"},
                                              {"PRODUCT_PRIMARY::ITEM::ENVY EXE",
                                               "CALENDAR_YEAR::MONTH::1998.05",
                                               "CHANNEL_PRIMARY::CHANNEL::CAT"}}));

           Source results = units.join(custSel)
                                 .join(edgeSel);

      Parameters:
      `tuples` - An array of `Object` arrays.

      Returns:
      A `Source` with elements that have the specified arrays, and that is typically used to provide values for a set of dimensions.

    <!-- -->

    - #### createModel

          public final CustomModel createModel(Source[] inputs,
                                               Source datatype,
                                               Source[] outputs,
                                               Model[] parentModels)

      Creates a `CustomModel` with the specified inputs, data type, outputs, and parent models.
      Parameters:
      `inputs` - An array of `Source` objects that are the inputs of the `CustomModel`.

      `datatype` - A fundamental `Source` that represents the data type of the `CustomModel`.

      `outputs` - An array of `Source` objects that are the outputs of the `CustomModel`.

      `parentModels` - An array of `Model` objects that are the parent models from which the `CustomModel` inherits `Assignment` objects.

      Returns:
      A `CustomModel` that has the specified inputs, data type, outputs, and parent models.

    <!-- -->

    - #### createModel

          public final CustomModel createModel(Source[] inputs,
                                               Source datatype,
                                               Source[] outputs)

      Creates a `CustomModel` with the specified inputs, data type, and outputs.
      Parameters:
      `inputs` - An array of `Source` objects that are the inputs of the `CustomModel`.

      `datatype` - A fundamental `Source` that represents the data type of the `CustomModel`.

      `outputs` - An array of `Source` objects that are the outputs of the `CustomModel`.

      Returns:
      A `CustomModel` that has the specified inputs, data type, and outputs.

    <!-- -->

    - #### createModel

          public final CustomModel createModel(Source[] inputs,
                                               Source datatype,
                                               Model[] parentModels)

      Creates a `CustomModel` with the specified inputs, data type, and parent models.
      Parameters:
      `inputs` - An array of `Source` objects that are the inputs of the `CustomModel`.

      `datatype` - A fundamental `Source` that represents the data type of the `CustomModel`.

      `parentModels` - An array of `Model` objects that are the parent models from which the `CustomModel` inherits `Assignment` objects.

      Returns:
      A `CustomModel` that has the specified inputs, data type, and parent models.

    <!-- -->

    - #### createModel

          public final CustomModel createModel(Source[] inputs,
                                               Source datatype)

      Creates a `CustomModel` with the specified inputs and data type.
      Parameters:
      `inputs` - An array of `Source` objects that are the inputs of the `CustomModel`.

      `datatype` - A fundamental `Source` that represents the data type of the `CustomModel`.

      Returns:
      A `CustomModel` that has the specified inputs and data type.

    <!-- -->

    - #### createModel

          public final CustomModel createModel(Source[] inputs)

      Creates a `CustomModel` with the specified inputs and a data type of Number.
      Parameters:
      `inputs` - An array of `Source` objects that are the inputs of the `CustomModel`.

      Returns:
      A `CustomModel` that has the specified inputs.

    <!-- -->

    - #### createModel

          public final CustomModel createModel(Source input,
                                               Source datatype)

      Creates a `CustomModel` with the specified input and data type.
      Parameters:
      `input` - A `Source` that the input of the `CustomModel`.

      `datatype` - A fundamental `Source` that represents the data type of the `CustomModel`.

      Returns:
      A `CustomModel` that has the specified input and data type.

    <!-- -->

    - #### createModel

          public final CustomModel createModel(Source input)

      Creates a `CustomModel` with the specified input and a data type of Number.
      Parameters:
      `input` - A `Source` that the input of the `CustomModel`.

      Returns:
      A `CustomModel` that has the specified input.

    <!-- -->

    - #### createRangeSource

          public final NumberSource createRangeSource(int bottom,
                                                      int top)

      Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.
      Parameters:
      `bottom` - The lowest value for the range.

      `top` - The highest value for the range.

      Returns:
      A `NumberSource` that has the specified range of values.

    <!-- -->

    - #### createRangeSource

          public final NumberSource createRangeSource(int bottom,
                                                      NumberSource top)

      Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.
      Parameters:
      `bottom` - The lowest value for the range.

      `top` - The highest value for the range.

      Returns:
      A `NumberSource` that has the specified range of values.

    <!-- -->

    - #### createRangeSource

          public final NumberSource createRangeSource(NumberSource bottom,
                                                      int top)

      Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.
      Parameters:
      `bottom` - A `NumberSource` with a single element, which has the `int` value as the lowest value for the range.

      `top` - The highest value for the range.

      Returns:
      A `NumberSource` that has the specified range of values.

    <!-- -->

    - #### createRangeSource

          public final NumberSource createRangeSource(NumberSource bottom,
                                                      NumberSource top)

      Creates a `NumberSource` with elements that have consecutive `int` values that range from the specified lowest value to the specified highest value.
      Parameters:
      `bottom` - A `NumberSource` with a single element, which has the `int` value as the lowest value for the range.

      `top` - A `NumberSource` with a single element, which has the `int` value as the highest value for the range.

      Returns:
      A `NumberSource` that has the specified range of values.

    <!-- -->

    - #### getEmptySource

          public final Source getEmptySource()

      Gets the empty `Source`, which does not have any elements. The empty `Source` represents an empty result set.
      Returns:
      The empty `Source`.

    <!-- -->

    - #### getFundamentalMetadataProvider

          public final FundamentalMetadataProvider getFundamentalMetadataProvider()

      Gets the `FundamentalMetadataProvider` for this `DataProvider`. The `FundamentalMetadataProvider` provides `FundamentalMetadataObject` objects that represent Oracle OLAP data types. You can use `FundamentalMetadataObject` objects to create derived `Source` objects.
      Returns:
      The `FundamentalMetadataProvider` for this `DataProvider`.

    <!-- -->

    - #### getTransactionProvider

          public final TransactionProvider getTransactionProvider()

      Gets the `TransactionProvider` associated with this `DataProvider`.
      Returns:
      The `TransactionProvider` for this `DataProvider`.

    <!-- -->

    - #### getVoidSource

          public final Source getVoidSource()

      Gets the void `Source` object, which has a single element that has `null` as the value.
      Returns:
      The void `Source`.

    <!-- -->

    - #### createSQLCursorManager

          public final SQLCursorManager createSQLCursorManager(Source source)
                                                        throws TransactionalObjectInvalidException

      Creates a `SQLCursorManager` for the specified `Source`. From the `SQLCursorManager` you can obtain the SQL statement that Oracle OLAP generates for the `Source`.
      Parameters:
      `source` - A `Source` that specifies a query.

      Returns:
      A `SQLCursorManager` that has the SQL statement generated for the specified `Source`.

      Throws:
      [`TransactionalObjectInvalidException`](../../transaction/TransactionalObjectInvalidException.md)

    <!-- -->

    - #### getDefaultUserSession

          public UserSession getDefaultUserSession()

      Gets the default `UserSession` associated with this `DataProvider`.
      Returns:
      The default `UserSession` for the `DataProvider`.

    <!-- -->

    - #### setDefaultUserSession

          public void setDefaultUserSession(UserSession defaultSession)

      Specifies the `UserSession` to associate with this `DataProvider` if a `UserSession` is not already associated with the active `Transaction`.
      Parameters:
      `defaultSession` - A `UserSession` to specify as the default `UserSession` for the `DataProvider`.

    <!-- -->

    - #### createCursorManagers

          public CursorManager[] createCursorManagers(Source[] rootSources,
                                                      int[] fetchSizes,
                                                      CursorInfoSpecification[] cursorInfoSpecs,
                                                      java.util.Properties queryProperties)

      Creates an array of `CursorManager` objects that can override the local or unique hierarchy value type setting of the `DataProvider`. The array contains one `CursorManager` for each `Source` in the `rootSources` array. You use the `CursorManager` objects to create `Cursor` objects that retrieve the results of the queries.
      The `fetchSizes` and `cursorInfoSpecs` arrays supply a fetch size and a `CursorInfoSpecification` for the `CursorManager` for the corresponding `Source` in the `rootSources` array. A fetch size of -1 fetches the entire result set.

      With the `Properties` object for the `queryProperties` parameter, you can specify the use of local or unique dimension hierarchy member values for retrieving data for a query. The property setting must match the query. For example, if you use local values to specify a query, then the hierarchy value type must be set to `local` for a `Cursor` to retrieve data. To use local values, set the property as in the following:

           queryProperties.setProperty("HierarchyValueType", "local");

      To use unique values, set the property as in the following:
           queryProperties.setProperty("HierarchyValueType", "unique");

      For more information on unique and local values, see the Overview of this documentation.

      Parameters:
      `rootSources` - An array of `Source` objects for the `CursorManager` objects.

      `fetchSizes` - An array of integers that specify the fetch sizes for the `Cursor` objects created by the corresponding `CursorManager` objects.

      `cursorInfoSpecs` - An array of `CursorInfoSpecification` objects for the corresponding `CursorManager` objects.

      `queryProperties` - A `java.util.Properties` object that specifies the use of local or unique dimension hierarchy member values.

      Returns:
      An array of `CursorManager` objects for the corresponding `Source` objects.

    <!-- -->

    - #### createCursorManagers

          public CursorManager[] createCursorManagers(Source[] rootSources,
                                                      int[] fetchSizes,
                                                      CursorInfoSpecification[] cursorInfoSpecs,
                                                      java.lang.String querySettings)
                                               throws org.xml.sax.SAXException

      Creates an array of `CursorManager` objects that can override the local or unique hierarchy value type of the `DataProvider`. The array contains one `CursorManager` for each `Source` in the `rootSources` array. You use the `CursorManager` objects to create `Cursor` objects that retrieve the results of the queries.
      The `fetchSizes` and `cursorInfoSpecs` arrays supply a fetch size and a `CursorInfoSpecification` for the `CursorManager` for the corresponding `Source` in the `rootSources` array. A fetch size of -1 fetches the entire result set.

      With an XML `String` as the `querySettings` parameter you can specify the use of local or unique dimension hierarchy member values for retrieving data fora query. The setting must match the query. For example, if you use local values to specify a query, then the hierarchy value type for the `CursorManager` must be set to `local` for a `Cursor` to retrieve data.

      The following code specifies the use of local hierarchy values.

           String querySettings =  "<olapsettings> <setting name = 'HierarchyValueType'" +
                                  " value = 'local' /> </olapsettings>"

      Parameters:
      `rootSources` - An array of `Source` objects for which you want `CursorManager` objects.

      `fetchSizes` - An array of integers that specify the fetch sizes for the `Cursor` objects created by the corresponding `CursorManager` objects.

      `cursorInfoSpecs` - An array of `CursorInfoSpecification` objects for the corresponding `CursorManager` objects.

      `querySettings` - A `String` in XML format that specifies the use of local or unique hierarchy values.

      Returns:
      An array of `CursorManager` objects for the corresponding `Source` objects.

      Throws:
      `org.xml.sax.SAXException` - Indicates a problem with the XML in the `querySettings` string.

    <!-- -->

    - #### getConnection

          public oracle.jdbc.OracleConnection getConnection()

      Gets the `oracle.jdbc.OracleConnectiown` object that represents the connection between a client application and Oracle OLAP in the Oracle Database instance.
      Returns:
      The `OracleConnection` that represents the connection to the Oracle Database instance.

    <!-- -->

    - #### isOpen

          public final boolean isOpen()

      Indicates whether the connection to the Oracle Database instance is currently open. If it is closed, then no further access to the metadata or to the associated data is possible. If Oracle OLAP retrieved metadata before the connection was closed and cached it on the client, then it is still available for processing; however, the data might not be current.
      Returns:
      A `boolean` that is `true` if the connection is open or `false` if it is not.

    <!-- -->

    - #### getRootTransaction

          public Transaction getRootTransaction(oracle.jdbc.OracleConnection connection)

      Gets the root `Transaction` for the specified `OracleConnection`.
      Parameters:
      `connection` - An `oracle.jdbc.OracleConnection`.

      Returns:
      The root `Transaction` for the `OracleConnection`.

    <!-- -->

    - #### createSQLCursorManagers

          public final SQLCursorManager[] createSQLCursorManagers(Source[] sources)

      Creates a `SQLCursorManager` for each `Source` in the `sources` array. All of the `Source` objects in the array must belong to the same `Transaction`. With a `SQLCursorManager`, you can obtain the SQL statements that Oracle OLAP generates for a query.
      Parameters:
      `sources` - An array of `Source` objects for the `SQLCursorManager` objects.

      Returns:
      An array of `SQLCursorManager` for the specified `Source` objects.

    <!-- -->

    - #### createSQLCursorManagers

          public final SQLCursorManager[] createSQLCursorManagers(Source[] sources,
                                                                  java.lang.String[] generatedSQLStatements)

      Creates a `SQLCursorManager` for each `Source` in the `sources` array and provides the SQL statements for each query. This method replaces the elements of the `generatedSQLStatements` array with the SQL statements that the Oracle OLAP SQL generator produces for the `Source` in the corresponding element of the `sources` array.
      All of the `Source` objects in the `sources` array must belong to the same `Transaction`. The `generatedSQLStatements` array must be the same size as the `sources` array.

      Parameters:
      `sources` - An array of `Source` objects for the `SQLCursorManager` objects.

      `generatedSQLStatements` - An array of `String` objects that that this method replaces with the SQL statements generated for the corresponding objects in the `sources` array.

      Returns:
      An array of `SQLCursorManager` objects.

    <!-- -->

    - #### createSQLCursorManagers

          public final SQLCursorManager[] createSQLCursorManagers(Source[] sources,
                                                                  boolean createCountColumn,
                                                                  java.lang.String[] generatedSQLStatements)

      Creates a `SQLCursorManager` for each `Source` in the `sources` array and provides the SQL statements and a count column for each query. This method replaces the elements of the `generatedSQLStatements` array with the count column and the SQL statements that the Oracle OLAP SQL generator produces for the `Source` in the corresponding element of the `sources` array.
      All of the `Source` objects in the `sources` array must belong to the same `Transaction`. The `generatedSQLStatements` array must be the same size as the `sources` array.

      Parameters:
      `sources` - An array of `Source` objects for the `SQLCursorManager` objects.

      `createCountColumn` - A boolean that specifies whether to include a count column in the generated SQL.

      `generatedSQLStatements` - An array of `String` objects that that this method replaces with the count column and SQL statements generated for the corresponding objects in the `sources` array.

      Returns:
      An array of `SQLCursorManager` objects.

    <!-- -->

    - #### getDefaultMetadataProvider

          public MetadataProvider getDefaultMetadataProvider()

      Gets the default `MetadataProvider` that is associated with this `DataProvider`; this method provides backward compatibility with previous versions of the Oracle OLAP Java API.
      Returns:
      The `MetadataProvider` associated with the `DataProvider`.

    <!-- -->

    - #### getMdmMetadataProvider

          public final MdmMetadataProvider getMdmMetadataProvider()

      Gets the `MdmMetadataProvider` that is associated with this `DataProvider`.
      Returns:
      The `MdmMetadataProvider` associated with the `DataProvider`.

    <!-- -->

    - #### createSession

          public UserSession createSession(oracle.jdbc.OracleConnection newConnection)
                                    throws java.sql.SQLException

      Creates a new `UserSession` that shares the `DataProvider` but that has a different `OracleConnection`.
      Parameters:
      `newConnection` - The `OracleConnection` with which to connect to the Oracle Database instance.

      Returns:
      A `UserSession` that has the specified connection.

      Throws:
      `java.sql.SQLException` - Indicates a problem with the connection to the database instance.

    <!-- -->

    - #### createSession

          public UserSession createSession(oracle.jdbc.OracleConnection newConnection,
                                           java.lang.String settings)
                                    throws java.sql.SQLException,
                                           org.xml.sax.SAXException

      Creates a new `UserSession` that shares the `DataProvider` but that has a different `OracleConnection` and has the specified settings. For the settings that you can specify, see the class description.
      Parameters:
      `newConnection` - The `OracleConnection` with which to connect to the Oracle Database instance.

      `settings` - A `String` that contains settings in an XML format to apply to the session.

      Returns:
      A `UserSession` that has the specified connection and settings.

      Throws:
      `java.sql.SQLException` - Indicates a problem with the connection to the database instance.

      `org.xml.sax.SAXException` - Indicates a problem with the XML in the `settings` string.

    <!-- -->

    - #### createSession

          public UserSession createSession(oracle.jdbc.OracleConnection newConnection,
                                           java.lang.String settings,
                                           java.util.Locale locale)
                                    throws java.sql.SQLException,
                                           org.xml.sax.SAXException

      Creates a new `UserSession` that shares the `DataProvider` but that has a different `OracleConnection` and has the specified settings, and language. For the settings that you can specify, see the class description.
      Parameters:
      `newConnection` - The `OracleConnection` with which to connect to the Oracle Database instance.

      `settings` - A `String` that contains settings in XML format to apply to the session.

      `locale` - A `Locale` object that specifies the language to use for the session.

      Returns:
      A `UserSession` that has the specified connection, settings, and language.

      Throws:
      `java.sql.SQLException` - Indicates a problem with the connection to the database instance.

      `org.xml.sax.SAXException` - Indicates a problem with the XML in the `settings` string.

    <!-- -->

    - #### close

          public void close()

      Closes the `DataProvider` and releases any associated resources.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CustomModel.md)
- [Next Class](DataProviderMismatchException.md)

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
