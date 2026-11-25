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

- [Prev Class](SourceIdentifier.md)
- [Next Class](StructureUpdatedException.md)

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

oracle.olapi.data.cursor

## Class SpecificationUpdateNeededException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - oracle.olapi.data.cursor.SpecificationUpdateNeededException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class SpecificationUpdateNeededException
      extends java.lang.RuntimeException

  Indicates that the structure of the `Source` for a `CursorManager` has changed and the `CursorManager` needs a new `CursorInfoSpecification`. The application should do the following:
  1.  Get a new `CursorInfoSpecification` by calling the `createCursorInfoSpecification` method of the `DataProvider` and passing it the `Source`.
  2.  Set the specifications it wants for the `CursorInfoSpecification` object. For example, if the application wants to be able to call the `getExtent` method of a `Cursor`, then it needs to call the `setExtentCalculationSpecified` method of the `CursorSpecification` for that `Cursor`.
  3.  Update the specification by calling the `updateSpecification` method of the `CursorManager` and passing it the `CursorInfoSpecification`.
  4.  Create a new `Cursor` by calling the `createCursor` method of the `CursorManager`.

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SpecificationUpdateNeededException``()`<br>Creates a `SpecificationUpdateNeededException`.                                                    |
    | `SpecificationUpdateNeededException``(java.lang.String message)`<br>Creates a `SpecificationUpdateNeededException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SpecificationUpdateNeededException

          public SpecificationUpdateNeededException()

      Creates a `SpecificationUpdateNeededException`.

    <!-- -->

    - #### SpecificationUpdateNeededException

          public SpecificationUpdateNeededException(java.lang.String message)

      Creates a `SpecificationUpdateNeededException` with the specified message.
      Parameters:
      `message` - The message to associate with the exception.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SourceIdentifier.md)
- [Next Class](StructureUpdatedException.md)

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
