Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- Prev Class
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.olapi.session

## Class UserSession

- java.lang.Object

- - oracle.olapi.session.UserSession

<!-- -->

-

  ------------------------------------------------------------------------



      public class UserSession
      extends java.lang.Object

  Associates a `DataProvider` with an `OracleConnection`. An application creates a `UserSession` with the `createSession` method of a `DataProvider`.
  An application can have many `UserSession` objects that share the same `DataProvider`. Each `UserSession` has a separate `OracleConnection`. The metadata provided by the `MdmMetadataProvider` of the `DataProvider` is the same for all of the `UserSession` objects.

  To end a `UserSession`, an application calls the `closeSession` method of the `UserSession`. Doing so closes any open `CursorManager` objects and commits or rolls back any `Transaction` objects associated with the `UserSession`. It does not, however, close the associated `OracleConnection`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                                                                          |
    |---------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                  | `closeSession``()`<br>Closes the `UserSession` but does not close the associated `OracleConnection`.                                                                                                                            |
    | `oracle.jdbc.OracleConnection`                          | `getConnection``()`<br>Gets the `OracleConnection` associated with the `UserSession`.                                                                                                                                           |
    | [`DataProvider`](../data/source/DataProvider.md)        | `getDataProvider``()`<br>Gets the `DataProvider` associated with the `UserSession`.                                                                                                                                             |
    | `java.lang.String`                                      | `getDefaultLanguage``()`<br>Gets the default language for the `UserSession`.                                                                                                                                                    |
    | [`Transaction`](../transaction/Transaction.md)          | `getRootTransaction``()`<br>Gets the root `Transaction` associated with the `UserSession`.                                                                                                                                      |
    | [`XMLParserCallback`](../metadata/XMLParserCallback.md) | `getServerXMLParserCallback``()`<br>Gets the `XMLParserCallback` implementation that is associated with this `UserSession`.                                                                                                     |
    | `java.util.Properties`                                  | `getSettings``()`<br>Get the `Properties` object that contains all of the settings used by this `UserSession`.                                                                                                                  |
    | `void`                                                  | `interrupt``()`<br>Terminates any operation that is currently executing in the `UserSession`.                                                                                                                                   |
    | `boolean`                                               | `isOpen``()`<br>Indicates whether the `OracleConnection` has an open connection to the database.                                                                                                                                |
    | `void`                                                  | `setServerXMLParserCallback``(`[`XMLParserCallback`](../metadata/XMLParserCallback.md)` callback)`<br>Specifies an `XMLParserCallback` for Oracle OLAP to use when it retrieves a metadata object that is stored on the server. |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getRootTransaction

          public Transaction getRootTransaction()

      Gets the root `Transaction` associated with the `UserSession`.
      Returns:
      The root `Transaction` associated with the `UserSession`.

    <!-- -->

    - #### getConnection

          public oracle.jdbc.OracleConnection getConnection()

      Gets the `OracleConnection` associated with the `UserSession`.
      Returns:
      The root `OracleConnection` associated with the `UserSession`.

    <!-- -->

    - #### isOpen

          public boolean isOpen()

      Indicates whether the `OracleConnection` has an open connection to the database.
      Returns:
      A `boolean` that is `true` if the `OracleConnection` is open or `false` if it is not.

    <!-- -->

    - #### closeSession

          public void closeSession()

      Closes the `UserSession` but does not close the associated `OracleConnection`.

    <!-- -->

    - #### getDataProvider

          public DataProvider getDataProvider()

      Gets the `DataProvider` associated with the `UserSession`.
      Returns:
      The `DataProvider` associated with the `UserSession`.

    <!-- -->

    - #### getSettings

          public java.util.Properties getSettings()

      Get the `Properties` object that contains all of the settings used by this `UserSession`.
      Returns:
      A `Properties` object that contains the settings used by this `UserSession`.

    <!-- -->

    - #### getDefaultLanguage

          public final java.lang.String getDefaultLanguage()

      Gets the default language for the `UserSession`. The language is the default language of the database and not that of the client application or the session.
      Returns:
      A `String` that identifies the default language for the `UserSession`.

    <!-- -->

    - #### setServerXMLParserCallback

          public void setServerXMLParserCallback(XMLParserCallback callback)

      Specifies an `XMLParserCallback` for Oracle OLAP to use when it retrieves a metadata object that is stored on the server. For example, if an application specifies an `XMLParserCallback` with this method and then calls a method like `MdmMetadataProvider.getMetadataObject(id)` or `MdmDatabaseSchema.getTopLevelObject(name)` and the requested object is invalid, then Oracle OLAP calls a method of the `XMLParserCallback`. A object stored on the server can become invalid if, for example, the column or table that the object references no longer exists in the database.
      The `XMLParserCallback.ERROR_BY_EXCEPTION` constant is not used by Oracle OLAP for an `XMLParserCallback` specified by this method. If a method of the `XMLParserCallback` returns the `ERROR_BY_EXCEPTION` constant, then Oracle OLAP uses the default constant, which is `ERROR_BY_SET_TO_NULL`.

      The `XMLParserCallback` specified by this method is not used by the `MdmMetadataProvider.importXML` or the `SyntaxObject.fromSyntax` methods. Those methods use the `XMLParserCallback` that the application passes to them.

      Parameters:
      `callback` - An implementation of the `XMLParserCallback` interface.

    <!-- -->

    - #### getServerXMLParserCallback

          public XMLParserCallback getServerXMLParserCallback()

      Gets the `XMLParserCallback` implementation that is associated with this `UserSession`.
      Returns:
      The `XMLParserCallback` associated with this `UserSession`.

    <!-- -->

    - #### interrupt

          public final void interrupt()

      Terminates any operation that is currently executing in the `UserSession`. This method has the same effect as calling the `oracle.jdbc.OracleConnection.cancel` method.
      An application must call this method in a separate thread. An application can use this method to terminate a build operation that was initiated by a `DataProvider.executeBuild` method.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
