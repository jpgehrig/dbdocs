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

- [Prev Class](PositionOutOfBoundsException.md)
- [Next Class](SpecificationUpdateNeededException.md)

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

## Interface SourceIdentifier

- All Known Implementing Classes:
  [BooleanSource](../source/BooleanSource.md), [DateSource](../source/DateSource.md), [NumberSource](../source/NumberSource.md), [Source](../source/Source.md), [StringSource](../source/StringSource.md)

  ------------------------------------------------------------------------



      public interface SourceIdentifier

  An interface for an object that contains a unique identifier for a `Source` or a `MetadataProvider`.
  See Also:
  [`Source`](../source/Source.md), [`MetadataProvider`](../../metadata/MetadataProvider.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                              |
    |--------------------|---------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getID``()`<br>Gets the unique identifier for a `Source` during a specific `UserSession`.                           |
    | `java.lang.String` | `getMetadataProviderID``()`<br>Gets the unique identifier for a `MetadataProvider` during a specific `UserSession`. |

<!-- -->

- - ### Method Detail

    - #### getID

          java.lang.String getID()

      Gets the unique identifier for a `Source` during a specific `UserSession`. The identifier might not be the same for a `Source` that is created in exactly the same way in a different session.
      Returns:
      A `String` that identifies a `Source` object during a session.

    <!-- -->

    - #### getMetadataProviderID

          java.lang.String getMetadataProviderID()

      Gets the unique identifier for a `MetadataProvider` during a specific `UserSession`. The identifier might not be the same in different sessions.
      Returns:
      A `String` that identifies a `MetadataProvider` object during a session.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](PositionOutOfBoundsException.md)
- [Next Class](SpecificationUpdateNeededException.md)

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
