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

- Prev Class
- [Next Class](Mdm11_2_ObjectVisitor.md)

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

## Interface Mdm10_1_0_3_ObjectVisitor

- All Superinterfaces:
  [MdmObjectVisitor](MdmObjectVisitor.md)

  <!-- -->

  All Known Subinterfaces:
  [Mdm11_2_ObjectVisitor](Mdm11_2_ObjectVisitor.md), [Mdm11_ObjectVisitor](Mdm11_ObjectVisitor.md)

  <!-- -->

  All Known Implementing Classes:
  [MdmBaseObjectVisitor](MdmBaseObjectVisitor.md)

  ------------------------------------------------------------------------



      public interface Mdm10_1_0_3_ObjectVisitor
      extends MdmObjectVisitor

  An `MdmObjectVisitor` that has methods for visiting classes that are added to the OLAP API in release 10.1.0.3 of Oracle Database.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                 |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitMdmAttributeModel``(`[`MdmAttributeModel`](MdmAttributeModel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmAttributeModel`.                                             |
    | `java.lang.Object` | `visitMdmDimensionCalculationModel``(`[`MdmDimensionCalculationModel`](MdmDimensionCalculationModel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimensionCalculationModel`. |
    | `java.lang.Object` | `visitMdmMeasureModel``(`[`MdmMeasureModel`](MdmMeasureModel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMeasureModel`.                                                     |
    | `java.lang.Object` | `visitMdmStandardMember``(`[`MdmStandardMember`](MdmStandardMember.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmStandardMember`.                                             |
    | `java.lang.Object` | `visitMdmTimeMember``(`[`MdmTimeMember`](MdmTimeMember.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmTimeMember`.                                                             |

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmObjectVisitor](MdmObjectVisitor.md)

      [`visitMdmAttribute`](MdmObjectVisitor.md)`, `[`visitMdmLevel`](MdmObjectVisitor.md)`, `[`visitMdmLevelHierarchy`](MdmObjectVisitor.md)`, `[`visitMdmMeasure`](MdmObjectVisitor.md)`, `[`visitMdmMeasureDimension`](MdmObjectVisitor.md)`, `[`visitMdmSchema`](MdmObjectVisitor.md)`, `[`visitMdmStandardDimension`](MdmObjectVisitor.md)`, `[`visitMdmTimeDimension`](MdmObjectVisitor.md)`, `[`visitMdmValueHierarchy`](MdmObjectVisitor.md)

<!-- -->

- - ### Method Detail

    - #### visitMdmDimensionCalculationModel

          java.lang.Object visitMdmDimensionCalculationModel(MdmDimensionCalculationModel mdmObject,
                                                             java.lang.Object context)

      Executes operations on the specified `MdmDimensionCalculationModel`.
      Parameters:
      `mdmObject` - An `MdmDimensionCalculationModel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmAttributeModel

          java.lang.Object visitMdmAttributeModel(MdmAttributeModel mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmAttributeModel`.
      Parameters:
      `mdmObject` - An `MdmAttributeModel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmMeasureModel

          java.lang.Object visitMdmMeasureModel(MdmMeasureModel mdmObject,
                                                java.lang.Object context)

      Executes operations on the specified `MdmMeasureModel`.
      Parameters:
      `mdmObject` - An `MdmMeasureModel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmStandardMember

          java.lang.Object visitMdmStandardMember(MdmStandardMember mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmStandardMember`.
      Parameters:
      `mdmObject` - An `MdmStandardMember`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmTimeMember

          java.lang.Object visitMdmTimeMember(MdmTimeMember mdmObject,
                                              java.lang.Object context)

      Executes operations on the specified `MdmTimeMember`.
      Parameters:
      `mdmObject` - An `MdmTimeMember`.

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

- Prev Class
- [Next Class](Mdm11_2_ObjectVisitor.md)

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
