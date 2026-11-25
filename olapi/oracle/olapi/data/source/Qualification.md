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

- [Prev Class](ParameterVisitor.md)
- [Next Class](ServerVersionException.md)

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

## Class Qualification

- java.lang.Object

- - oracle.olapi.data.source.Qualification

<!-- -->

- Direct Known Subclasses:
  [LiteralQualification](LiteralQualification.md)

  ------------------------------------------------------------------------



      public abstract class Qualification
      extends java.lang.Object

  An object that specifies a `Source` and an element of that `Source` for an `Assignment` of a `Model`. The constructor of the concrete subclass `LiteralQualification` takes a `Source` and an `Object` that qualifies the `Source` by specifying an element of it. The qualified `Source` must be an input of the `Model` associated with the `Assignment`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                          |
    |-----------------------|---------------------------------------------------------------------------------|
    | [`Source`](Source.md) | `getQualifiedSource``()`<br>Gets the qualified `Source` of the `Qualification`. |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getQualifiedSource

          public final Source getQualifiedSource()

      Gets the qualified `Source` of the `Qualification`.
      Returns:
      The qualified `Source` of the `Qualification`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ParameterVisitor.md)
- [Next Class](ServerVersionException.md)

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
