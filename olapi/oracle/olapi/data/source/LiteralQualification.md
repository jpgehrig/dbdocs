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

- [Prev Class](IncorrectDataValueException.md)
- [Next Class](Model.md)

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

## Class LiteralQualification

- java.lang.Object

- - [oracle.olapi.data.source.Qualification](Qualification.md)

  - - oracle.olapi.data.source.LiteralQualification

<!-- -->

-

  ------------------------------------------------------------------------



      public class LiteralQualification
      extends Qualification

  A `Qualification` that specifies a literal value, such as an `Integer`, `Boolean`, or `String` literal, that identifies an element of a `Source` for an `Assignment` of a `Model`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LiteralQualification``(`[`Source`](Source.md)` qualifiedSource, java.lang.Object literal)`<br>Creates a `LiteralQualification` object that qualifies a `Source` by specifying a single element of that `Source`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                     |
    |--------------------|----------------------------------------------------------------------------|
    | `java.lang.Object` | `getLiteral``()`<br>Gets the literal value of this `LiteralQualification`. |

    - ### Methods inherited from class oracle.olapi.data.source.[Qualification](Qualification.md)

      [`getQualifiedSource`](Qualification.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LiteralQualification

          public LiteralQualification(Source qualifiedSource,
                                      java.lang.Object literal)

      Creates a `LiteralQualification` object that qualifies a `Source` by specifying a single element of that `Source`. The `Source` must be an input of the `Model` associated with the `Assignment` with which the `LiteralQualification` is associated.
      Parameters:
      `qualifiedSource` - A `Source` that has the element for which you want to assign a value.

      `literal` - The literal value of the `qualifiedSource` element for which you want to assign a value.

  <!-- -->

  - ### Method Detail

    - #### getLiteral

          public final java.lang.Object getLiteral()

      Gets the literal value of this `LiteralQualification`.
      Returns:
      An `Object` that represents the literal value of the qualified `Source` of this `LiteralQualification`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](IncorrectDataValueException.md)
- [Next Class](Model.md)

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
