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

- [Prev Class](Mdm10_1_0_3_ObjectVisitor.md)
- [Next Class](Mdm11_ObjectVisitor.md)

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

## Interface Mdm11_2_ObjectVisitor

- All Superinterfaces:
  [Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md), [Mdm11_ObjectVisitor](Mdm11_ObjectVisitor.md), [MdmObjectVisitor](MdmObjectVisitor.md)

  <!-- -->

  All Known Implementing Classes:
  [MdmBaseObjectVisitor](MdmBaseObjectVisitor.md)

  ------------------------------------------------------------------------



      public interface Mdm11_2_ObjectVisitor
      extends Mdm11_ObjectVisitor

  An extension of the `MdmObject` visitor interfaces that has methods for visiting classes that the Oracle OLAP Java API adds in Oracle 11*g*, Release 2 (11.2).

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                         |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitMdmDimensionality``(`[`MdmDimensionality`](MdmDimensionality.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimensionality`.                                                     |
    | `java.lang.Object` | `visitMdmMultiValuedDerivedAttribute``(`[`MdmMultiValuedDerivedAttribute`](MdmMultiValuedDerivedAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMultiValuedDerivedAttribute`. |

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[Mdm11_ObjectVisitor](Mdm11_ObjectVisitor.md)

      [`visitMdmAssignment`](Mdm11_ObjectVisitor.md)`, `[`visitMdmBaseAttribute`](Mdm11_ObjectVisitor.md)`, `[`visitMdmBaseMeasure`](Mdm11_ObjectVisitor.md)`, `[`visitMdmColumn`](Mdm11_ObjectVisitor.md)`, `[`visitMdmCube`](Mdm11_ObjectVisitor.md)`, `[`visitMdmCustomMember`](Mdm11_ObjectVisitor.md)`, `[`visitMdmDatabaseSchema`](Mdm11_ObjectVisitor.md)`, `[`visitMdmDerivedAttribute`](Mdm11_ObjectVisitor.md)`, `[`visitMdmDerivedMeasure`](Mdm11_ObjectVisitor.md)`, `[`visitMdmDescriptionType`](Mdm11_ObjectVisitor.md)`, `[`visitMdmDimensionLevel`](Mdm11_ObjectVisitor.md)`, `[`visitMdmHierarchyLevel`](Mdm11_ObjectVisitor.md)`, `[`visitMdmNamedBuildProcess`](Mdm11_ObjectVisitor.md)`, `[`visitMdmOrganizationalSchema`](Mdm11_ObjectVisitor.md)`, `[`visitMdmRootSchema`](Mdm11_ObjectVisitor.md)`, `[`visitMdmTable`](Mdm11_ObjectVisitor.md)

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md)

      [`visitMdmAttributeModel`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmDimensionCalculationModel`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmMeasureModel`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmStandardMember`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmTimeMember`](Mdm10_1_0_3_ObjectVisitor.md)

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmObjectVisitor](MdmObjectVisitor.md)

      [`visitMdmAttribute`](MdmObjectVisitor.md)`, `[`visitMdmLevel`](MdmObjectVisitor.md)`, `[`visitMdmLevelHierarchy`](MdmObjectVisitor.md)`, `[`visitMdmMeasure`](MdmObjectVisitor.md)`, `[`visitMdmMeasureDimension`](MdmObjectVisitor.md)`, `[`visitMdmSchema`](MdmObjectVisitor.md)`, `[`visitMdmStandardDimension`](MdmObjectVisitor.md)`, `[`visitMdmTimeDimension`](MdmObjectVisitor.md)`, `[`visitMdmValueHierarchy`](MdmObjectVisitor.md)

<!-- -->

- - ### Method Detail

    - #### visitMdmMultiValuedDerivedAttribute

          java.lang.Object visitMdmMultiValuedDerivedAttribute(MdmMultiValuedDerivedAttribute mdmObject,
                                                               java.lang.Object context)

      Executes operations on the specified `MdmMultiValuedDerivedAttribute`.
      Parameters:
      `mdmObject` - An `MdmMultiValuedDerivedAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDimensionality

          java.lang.Object visitMdmDimensionality(MdmDimensionality mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmDimensionality`.
      Parameters:
      `mdmObject` - An `MdmDimensionality`.

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

- [Prev Class](Mdm10_1_0_3_ObjectVisitor.md)
- [Next Class](Mdm11_ObjectVisitor.md)

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
