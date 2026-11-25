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

- [Prev Class](InvalidMetadataException.md)
- [Next Class](MetadataFactoryException.md)

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

## Class InvalidMetadataObjectInfo

- java.lang.Object

- - oracle.olapi.metadata.InvalidMetadataObjectInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class InvalidMetadataObjectInfo
      extends java.lang.Object

  Contains information about an invalid metadata object. You get `InvalidMetadataObjectInfo` objects with the `getErrorInfoList` methods of an `InvalidMetadataException`. Oracle error messages have the form `prefix-number: text`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                   |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getDDL``()`<br>Gets the Oracle DDL commnd whose execution caused the error or `null` if the error is not associated with DDL execution. |
    | `java.lang.String` | `getFacility``()`<br>Gets the prefix portion of the error message.                                                                       |
    | `java.lang.String` | `getMessage``()`<br>Gets the text portion of the error message.                                                                          |
    | `int`              | `getNumber``()`<br>Gets the error number portion of the error message.                                                                   |
    | `java.lang.String` | `getObjectID``()`<br>Gets a `String` that contains the unique identifier (ID) of the metadata object.                                    |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getObjectID

          public java.lang.String getObjectID()

      Gets a `String` that contains the unique identifier (ID) of the metadata object.
      Returns:
      A `String` that contains the ID of the metadata object.

    <!-- -->

    - #### getFacility

          public java.lang.String getFacility()

      Gets the prefix portion of the error message. For example, the prefix `ORA` is a general prefix for Oracle products and the prefix `XOQ` specifies the Oracle OLAP Java API component.
      Returns:
      A `String` that contains the prefix from the error message.

    <!-- -->

    - #### getNumber

          public int getNumber()

      Gets the error number portion of the error message.
      Returns:
      A `String` that contains the error number from the error message.

    <!-- -->

    - #### getMessage

          public java.lang.String getMessage()

      Gets the text portion of the error message.
      Returns:
      A `String` that contains the text from the error message.

    <!-- -->

    - #### getDDL

          public java.lang.String getDDL()

      Gets the Oracle DDL commnd whose execution caused the error or `null` if the error is not associated with DDL execution.
      Returns:
      A `String` that contains the DDL command that caused the error.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](InvalidMetadataException.md)
- [Next Class](MetadataFactoryException.md)

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
