Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Package](../../package-summary.md)
- [Next Package](../source/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Package oracle.olapi.data.cursor

Contains interfaces and classes for retrieving and accessing the result set of a query.

See: Description

- **Interface Summary**

  | Interface                                                     | Description                                                                                                                                  |
  |---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
  | [CompoundCursor](CompoundCursor.md)                           | A `Cursor` for a `Source` that has outputs.                                                                                                  |
  | [Cursor](Cursor.md)                                           | An interface for objects that provide access to the result set of a query.                                                                   |
  | [CursorManager](CursorManager.md)                             | An interface for an object that creates and manages `Cursor` objects.                                                                        |
  | [CursorManagerUpdateListener](CursorManagerUpdateListener.md) | An interface for a listener object that a `CursorManager` notifies when a change occurs to the `Source` associated with the `CursorManager`. |
  | [SourceIdentifier](SourceIdentifier.md)                       | An interface for an object that contains a unique identifier for a `Source` or a `MetadataProvider`.                                         |
  | [ValueCursor](ValueCursor.md)                                 | A `Cursor` that has a value at its current position.                                                                                         |

- **Class Summary**

  | Class                                                   | Description                                                                                          |
  |---------------------------------------------------------|------------------------------------------------------------------------------------------------------|
  | [CursorManagerUpdateEvent](CursorManagerUpdateEvent.md) | An event passed by a `CursorManager` to the `CursorManageUpdateListener` objects associated with it. |

- **Exception Summary**

  | Exception                                                                   | Description                                                                                                                                   |
  |-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
  | [IncorrectDataTypeException](IncorrectDataTypeException.md)                 | Indicates that the data type requested is not the type available or expected.                                                                 |
  | [NoDataAvailableException](NoDataAvailableException.md)                     | Indicates that the query resulted in no data for the values specified by the `Cursor`.                                                        |
  | [NotSpecifiedException](NotSpecifiedException.md)                           | Indicates that the operation cannot be performed because the application did not specify that it wanted the information.                      |
  | [PositionOutOfBoundsException](PositionOutOfBoundsException.md)             | Indicates that the specified position is not valid.                                                                                           |
  | [SpecificationUpdateNeededException](SpecificationUpdateNeededException.md) | Indicates that the structure of the `Source` for a `CursorManager` has changed and the `CursorManager` needs a new `CursorInfoSpecification`. |
  | [StructureUpdatedException](StructureUpdatedException.md)                   | Indicates that the structure of the `Source` associated with a `CursorManager` has changed.                                                   |

## Package oracle.olapi.data.cursor Description

Contains interfaces and classes for retrieving and accessing the result set of a query.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../../package-summary.md)
- [Next Package](../source/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)
