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

- [Prev Class](MetadataObject.md)
- [Next Class](MetadataRenameNotSupportedException.md)

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

## Interface MetadataProvider

- All Known Implementing Classes:
  [FundamentalMetadataProvider](../data/source/FundamentalMetadataProvider.md), [MdmMetadataProvider](mdm/MdmMetadataProvider.md)

  ------------------------------------------------------------------------



      public interface MetadataProvider

  An interface for an object that provides access to OLAP metadata objects. The `MetadataProvider` interface supplies only the existence of a unique identifier.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                               |
    |--------------------|----------------------------------------------------------------------|
    | `java.lang.String` | `getID``()`<br>Gets the unique identifier of the `MetadataProvider`. |

<!-- -->

- - ### Method Detail

    - #### getID

          java.lang.String getID()

      Gets the unique identifier of the `MetadataProvider`.
      Returns:
      The unique identifier of the `MetadataProvider`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MetadataObject.md)
- [Next Class](MetadataRenameNotSupportedException.md)

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
