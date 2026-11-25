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

- [Prev Class](MdmObject.md)
- [Next Class](MdmOrganizationalSchema.md)

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

oracle.olapi.metadata.mdm

## Interface MdmObjectVisitor

- All Known Subinterfaces:
  [Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md), [Mdm11_2_ObjectVisitor](Mdm11_2_ObjectVisitor.md), [Mdm11_ObjectVisitor](Mdm11_ObjectVisitor.md)

  <!-- -->

  All Known Implementing Classes:
  [MdmBaseObjectVisitor](MdmBaseObjectVisitor.md)

  ------------------------------------------------------------------------



      public interface MdmObjectVisitor

  A visitor object that can execute operations on some of the classes in the `MdmObject` class hierarchy. With your visitor, you can implement polymorphic behavior without having access to the internal code of `MdmObject` or its subclasses.
  `MdmObjectVisitor` has a visit method for most of the classes in the `MdmObject` class hierarchy. `MdmObject` and its subclasses have an `acceptVisitor` method. The `acceptVisitor` method takes as its input parameters an `MdmObjectVisitor` and a `context` object. When you call the `acceptVisitor` method on an `MdmObject`, the `acceptVisitor` method calls the corresponding visit method on your `MdmObjectVisitor`. The `acceptVisitor` method passes the `MdmObject` and the `context` to the visit method. For example, you could call the `acceptVisitor` method on an `MdmSchema` and pass it your `MdmObjectVisitor` and `context` objects. The `acceptVisitor` method would then pass the `MdmSchema` and the `context` you passed it to the `visitMdmSchema` method of your `MdmObjectVisitor`.

  A visit method of your `MdmObjectVisitor` can perform whatever operations you want on the `MdmObject` it receives, and your `context` object can be anything you want it to be. For example, a `visitMdmSchema` method might call the `getSubSchemas` method on the `MdmSchema`, and then call methods on the `context` object to format and display the resulting information. A visit method must return a Java `Object`, which can be whatever you want it to be.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                 |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitMdmAttribute``(`[`MdmAttribute`](MdmAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmAttribute`.                                 |
    | `java.lang.Object` | `visitMdmLevel``(`[`MdmLevel`](MdmLevel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmLevel`.                                                 |
    | `java.lang.Object` | `visitMdmLevelHierarchy``(`[`MdmLevelHierarchy`](MdmLevelHierarchy.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmLevelHierarchy`.             |
    | `java.lang.Object` | `visitMdmMeasure``(`[`MdmMeasure`](MdmMeasure.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMeasure`.                                         |
    | `java.lang.Object` | `visitMdmMeasureDimension``(`[`MdmMeasureDimension`](MdmMeasureDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMeasureDimension`.     |
    | `java.lang.Object` | `visitMdmSchema``(`[`MdmSchema`](MdmSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmSchema`.                                             |
    | `java.lang.Object` | `visitMdmStandardDimension``(`[`MdmStandardDimension`](MdmStandardDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmStandardDimension`. |
    | `java.lang.Object` | `visitMdmTimeDimension``(`[`MdmTimeDimension`](MdmTimeDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmTimeDimension`.                 |
    | `java.lang.Object` | `visitMdmValueHierarchy``(`[`MdmValueHierarchy`](MdmValueHierarchy.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmValueHierarchy`.             |

<!-- -->

- - ### Method Detail

    - #### visitMdmAttribute

          java.lang.Object visitMdmAttribute(MdmAttribute mdmObject,
                                             java.lang.Object context)

      Executes operations on the specified `MdmAttribute`.
      Parameters:
      `mdmObject` - An `MdmAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmLevel

          java.lang.Object visitMdmLevel(MdmLevel mdmObject,
                                         java.lang.Object context)

      Executes operations on the specified `MdmLevel`.
      Parameters:
      `mdmObject` - An `MdmLevel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmLevelHierarchy

          java.lang.Object visitMdmLevelHierarchy(MdmLevelHierarchy mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmLevelHierarchy`.
      Parameters:
      `mdmObject` - An `MdmLevelHierarchy`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmMeasure

          java.lang.Object visitMdmMeasure(MdmMeasure mdmObject,
                                           java.lang.Object context)

      Executes operations on the specified `MdmMeasure`.
      Parameters:
      `mdmObject` - An `MdmMeasure`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmMeasureDimension

          java.lang.Object visitMdmMeasureDimension(MdmMeasureDimension mdmObject,
                                                    java.lang.Object context)

      Executes operations on the specified `MdmMeasureDimension`.
      Parameters:
      `mdmObject` - An `MdmMeasureDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmSchema

          java.lang.Object visitMdmSchema(MdmSchema mdmObject,
                                          java.lang.Object context)

      Executes operations on the specified `MdmSchema`.
      Parameters:
      `mdmObject` - An `MdmSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmStandardDimension

          java.lang.Object visitMdmStandardDimension(MdmStandardDimension mdmObject,
                                                     java.lang.Object context)

      Executes operations on the specified `MdmStandardDimension`.
      Parameters:
      `mdmObject` - An `MdmStandardDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmTimeDimension

          java.lang.Object visitMdmTimeDimension(MdmTimeDimension mdmObject,
                                                 java.lang.Object context)

      Executes operations on the specified `MdmTimeDimension`.
      Parameters:
      `mdmObject` - An `MdmTimeDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmValueHierarchy

          java.lang.Object visitMdmValueHierarchy(MdmValueHierarchy mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmValueHierarchy`.
      Parameters:
      `mdmObject` - An `MdmValueHierarchy`.

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

- [Prev Class](MdmObject.md)
- [Next Class](MdmOrganizationalSchema.md)

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
