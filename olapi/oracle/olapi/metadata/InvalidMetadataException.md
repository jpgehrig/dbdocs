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

- [Prev Class](DuplicateMetadataIDException.md)
- [Next Class](InvalidMetadataObjectInfo.md)

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

oracle.olapi.metadata

## Class InvalidMetadataException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../OLAPIRuntimeException.md)

        - - oracle.olapi.metadata.InvalidMetadataException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class InvalidMetadataException
      extends OLAPIRuntimeException

  Indicates that one or more metadata objects are invalid. To find out which objects are invalid, use the `getInvalidObjectIds` method, which returns a `Set` of `String` objects, each of which is the unique identifier of an invalid `MetadataObject`. You can use the `getMetadataObjects` method of an `MdmMetadataProvider` to retrieve the `MetadataObject` instances that have those IDs. You can then use the methods of this class to retrieve the error messages for each `MetadataObject`.
  You can also retrieve `InvalidMetadataObjectInfo` objects for each object. An `InvalidMetadataObjectInfo` contains additional information about the error, such as the command that caused the error, and the error message prefix, and the error message number.

  If the number of errors for the object exceeds the error limit, then the `getErrorMessages` might not return all of the messages for the object. In that case, the `hasMoreErrors` method returns `true`.

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                        |
    |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List`   | `getErrorInfoList``(`[`MetadataObject`](MetadataObject.md)` object)`<br>Gets the `InvalidMetadataObjectInfo` objects for the specified `MetadataObject`.                                      |
    | `java.util.List`   | `getErrorInfoList``(java.lang.String objectID)`<br>Gets the `InvalidMetadataObjectInfo` objects for the `MetadataObject` that has the specified unique `String` identifier.                   |
    | `java.util.List`   | `getErrorMessages``(`[`MetadataObject`](MetadataObject.md)` object)`<br>Gets the error messages for the specified `MetadataObject`.                                                           |
    | `java.util.List`   | `getErrorMessages``(java.lang.String objectID)`<br>Gets the error messages for the `MetadataObject` that has the specified unique `String` identifier.                                        |
    | `java.util.Set`    | `getInvalidObjectIds``()`<br>Gets the unique `String` identifier for each invalid `MetadataObject`.                                                                                           |
    | `java.lang.String` | `getLocalizedMessage``(java.util.Locale locale)`<br>Gets a message in the language specified by the `java.util.Locale` object.                                                                |
    | `boolean`          | `hasMoreErrors``()`<br>Indicates whether the number of error messages generated for the invalid `MetadataObject` objects is greater than the limit of error messages that Oracle OLAP allows. |

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../OLAPIRuntimeException.md)`, `[`getParameters`](../OLAPIRuntimeException.md)`, `[`toString`](../OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getInvalidObjectIds

          public java.util.Set getInvalidObjectIds()

      Gets the unique `String` identifier for each invalid `MetadataObject`.
      Returns:
      A `Set` that contains the IDs of the invalid `MetadataObject` objects.

    <!-- -->

    - #### getErrorInfoList

          public java.util.List getErrorInfoList(java.lang.String objectID)

      Gets the `InvalidMetadataObjectInfo` objects for the `MetadataObject` that has the specified unique `String` identifier.
      Parameters:
      `objectID` - A `String` that contains the identifier for the `MetadataObject`.

      Returns:
      A `List` that contains the `InvalidMetadataObjectInfo` objects for the `MetadataObject` with the specified ID.

    <!-- -->

    - #### getErrorInfoList

          public java.util.List getErrorInfoList(MetadataObject object)

      Gets the `InvalidMetadataObjectInfo` objects for the specified `MetadataObject`.
      Parameters:
      `object` - The `MetadataObject` for which to retrieve `InvalidMetadataObjectInfo` objects.

      Returns:
      A `List` that contains the `InvalidMetadataObjectInfo` objects for the specified `MetadataObject`.

    <!-- -->

    - #### getErrorMessages

          public java.util.List getErrorMessages(java.lang.String objectID)

      Gets the error messages for the `MetadataObject` that has the specified unique `String` identifier.
      Parameters:
      `objectID` - A `String` that contains the identifier for the `MetadataObject`.

      Returns:
      A `List` that contains the error messages for the `MetadataObject` with the specified ID.

    <!-- -->

    - #### getErrorMessages

          public java.util.List getErrorMessages(MetadataObject object)

      Gets the error messages for the specified `MetadataObject`.
      Parameters:
      `object` - The `MetadataObject` for which to retrieve error messages.

      Returns:
      A `List` that contains the error messages for the specified `MetadataObject`.

    <!-- -->

    - #### hasMoreErrors

          public boolean hasMoreErrors()

      Indicates whether the number of error messages generated for the invalid `MetadataObject` objects is greater than the limit of error messages that Oracle OLAP allows. If this method returns `true`, then the lists returned by the methods of this class might not have all of the error messages.
      Returns:
      A `boolean` that is `true` if the number of error messages exceeds the limit and `false` otherwise.

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage(java.util.Locale locale)

      Gets a message in the language specified by the `java.util.Locale` object.
      Specified by:
      [`getLocalizedMessage`](../HasLocalizedMessage.md) in interface [`HasLocalizedMessage`](../HasLocalizedMessage.md)

      Overrides:
      [`getLocalizedMessage`](../OLAPIRuntimeException.md) in class [`OLAPIRuntimeException`](../OLAPIRuntimeException.md)

      Parameters:
      `locale` - The `Locale` object that specifies the language for the message.

      Returns:
      A `String` that has the message in the specified language.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DuplicateMetadataIDException.md)
- [Next Class](InvalidMetadataObjectInfo.md)

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
