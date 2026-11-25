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

- [Prev Class](CursorSpecification.md)
- [Next Class](CustomModel.md)

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

## Class CursorSpecificationVisitor

- java.lang.Object

- - oracle.olapi.data.source.CursorSpecificationVisitor

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class CursorSpecificationVisitor
      extends java.lang.Object

  A visitor object that can execute operations on `CursorSpecification` objects. A `CursorSpecificationVisitor` can implement polymorphic behavior without having access to the internal code of the `CursorSpecification` subclasses.
  `CursorSpecificationVisitor` has a visit method for each of the classes in the `CursorSpecification` hierarchy. `CursorSpecification` and the subclasses of it have an `acceptVisitor` method. The `acceptVisitor` method takes as input parameters a `CursorSpecificationVisitor` object and an `Object`. When an application calls the `acceptVisitor` method of a `CursorSpecification`, the `acceptVisitor` method calls the corresponding visit method of the `CursorSpecificationVisitor`. The `acceptVisitor` method passes the `CursorSpecification` and the `Object` to the visit method. For example, if an application calls the `acceptVisitor` method of a `CompoundCursorSpecification` and passes it a `CursorSpecificationVisitor` and an `Object`, then the `acceptVisitor` method passes the `CompoundCursorSpecification` and the `Object` to the `visitCompoundCursorSpecification` method of the `CursorSpecificationVisitor`.

  Your `context` parameter `Object` can be anything you want it to be. A visit method of your `CursorSpecificationVisitor` can perform whatever operations you want it to on the `CursorSpecification` it receives. For example, a `visitCompoundCursorSpecification` method might call the `isExtentCalculationSpecified` method of the `CompoundCursorSpecification` to discover if the `CompoundCursorSpecification` specifies that the extent should be calculated for the `CompoundCursor`. The method might then call methods on the context `Object` to format and display the resulting information. A visit method must return a `java.lang.Object`, which can be whatever you want it to be.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                     |
    |-------------|---------------------------------------------------------------------------------|
    | `protected` | `CursorSpecificationVisitor``()`<br>Creates a new `CursorSpecificationVisitor`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                                              |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitCompoundCursorSpecification``(`[`CompoundCursorSpecification`](CompoundCursorSpecification.md)` cursorSpecification, java.lang.Object context)`<br>Executes operations on the specified `CompoundCursorSpecification`.                                                        |
    | `java.lang.Object` | `visitCursorSpecification``(`[`CursorSpecification`](CursorSpecification.md)` cursorSpecification, java.lang.Object context)`<br>Executes operations on any object that is a subclass of `CursorSpecification`, which is useful when you do not need subclass-specific information. |
    | `java.lang.Object` | `visitValueCursorSpecification``(`[`ValueCursorSpecification`](ValueCursorSpecification.md)` cursorSpecification, java.lang.Object context)`<br>Executes operations on the specified `ValueCursorSpecification`.                                                                    |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### CursorSpecificationVisitor

          protected CursorSpecificationVisitor()

      Creates a new `CursorSpecificationVisitor`.

  <!-- -->

  - ### Method Detail

    - #### visitCursorSpecification

          public java.lang.Object visitCursorSpecification(CursorSpecification cursorSpecification,
                                                           java.lang.Object context)

      Executes operations on any object that is a subclass of `CursorSpecification`, which is useful when you do not need subclass-specific information. The default implementation of this method returns `null`.
      Parameters:
      `cursorSpecification` - A `CursorSpecification`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitCompoundCursorSpecification

          public java.lang.Object visitCompoundCursorSpecification(CompoundCursorSpecification cursorSpecification,
                                                                   java.lang.Object context)

      Executes operations on the specified `CompoundCursorSpecification`. The default implementation of this method calls `visitCursorSpecification`.
      Parameters:
      `cursorSpecification` - A `CompoundCursorSpecification`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitValueCursorSpecification

          public java.lang.Object visitValueCursorSpecification(ValueCursorSpecification cursorSpecification,
                                                                java.lang.Object context)

      Executes operations on the specified `ValueCursorSpecification`. The default implementation of this method calls `visitCursorSpecification`.
      Parameters:
      `cursorSpecification` - A `ValueCursorSpecification`.

      `context` - An `Object`.

      Returns:
      An `Object`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CursorSpecification.md)
- [Next Class](CustomModel.md)

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
