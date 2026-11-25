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

- [Prev Class](Mdm11_2_ObjectVisitor.md)
- [Next Class](MdmAssignment.md)

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

## Interface Mdm11_ObjectVisitor

- All Superinterfaces:
  [Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md), [MdmObjectVisitor](MdmObjectVisitor.md)

  <!-- -->

  All Known Subinterfaces:
  [Mdm11_2_ObjectVisitor](Mdm11_2_ObjectVisitor.md)

  <!-- -->

  All Known Implementing Classes:
  [MdmBaseObjectVisitor](MdmBaseObjectVisitor.md)

  ------------------------------------------------------------------------



      public interface Mdm11_ObjectVisitor
      extends Mdm10_1_0_3_ObjectVisitor

  An extension of the `MdmObject` visitor interfaces that has methods for visiting classes that the Oracle OLAP Java API adds in Oracle 11*g*, Release 1 (11.1).

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                             |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitMdmAssignment``(`[`MdmAssignment`](MdmAssignment.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmAssignment`.                                         |
    | `java.lang.Object` | `visitMdmBaseAttribute``(`[`MdmBaseAttribute`](MdmBaseAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmBaseAttribute`.                             |
    | `java.lang.Object` | `visitMdmBaseMeasure``(`[`MdmBaseMeasure`](MdmBaseMeasure.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmBaseMeasure`.                                     |
    | `java.lang.Object` | `visitMdmColumn``(`[`MdmColumn`](MdmColumn.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmColumn`.                                                         |
    | `java.lang.Object` | `visitMdmCube``(`[`MdmCube`](MdmCube.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmCube`.                                                                 |
    | `java.lang.Object` | `visitMdmCustomMember``(`[`MdmCustomMember`](MdmCustomMember.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmCustomMember`.                                 |
    | `java.lang.Object` | `visitMdmDatabaseSchema``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDatabaseSchema`.                         |
    | `java.lang.Object` | `visitMdmDerivedAttribute``(`[`MdmDerivedAttribute`](MdmDerivedAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDerivedAttribute`.                 |
    | `java.lang.Object` | `visitMdmDerivedMeasure``(`[`MdmDerivedMeasure`](MdmDerivedMeasure.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDerivedMeasure`.                         |
    | `java.lang.Object` | `visitMdmDescriptionType``(`[`MdmDescriptionType`](MdmDescriptionType.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDescriptionType`.                     |
    | `java.lang.Object` | `visitMdmDimensionLevel``(`[`MdmDimensionLevel`](MdmDimensionLevel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimensionLevel`.                         |
    | `java.lang.Object` | `visitMdmHierarchyLevel``(`[`MdmHierarchyLevel`](MdmHierarchyLevel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmHierarchyLevel`.                         |
    | `java.lang.Object` | `visitMdmNamedBuildProcess``(`[`MdmNamedBuildProcess`](MdmNamedBuildProcess.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmNamedBuildProcess`.             |
    | `java.lang.Object` | `visitMdmOrganizationalSchema``(`[`MdmOrganizationalSchema`](MdmOrganizationalSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmOrganizationalSchema`. |
    | `java.lang.Object` | `visitMdmRootSchema``(`[`MdmRootSchema`](MdmRootSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmRootSchema`.                                         |
    | `java.lang.Object` | `visitMdmTable``(`[`MdmTable`](MdmTable.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmTable`.                                                             |

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md)

      [`visitMdmAttributeModel`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmDimensionCalculationModel`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmMeasureModel`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmStandardMember`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmTimeMember`](Mdm10_1_0_3_ObjectVisitor.md)

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmObjectVisitor](MdmObjectVisitor.md)

      [`visitMdmAttribute`](MdmObjectVisitor.md)`, `[`visitMdmLevel`](MdmObjectVisitor.md)`, `[`visitMdmLevelHierarchy`](MdmObjectVisitor.md)`, `[`visitMdmMeasure`](MdmObjectVisitor.md)`, `[`visitMdmMeasureDimension`](MdmObjectVisitor.md)`, `[`visitMdmSchema`](MdmObjectVisitor.md)`, `[`visitMdmStandardDimension`](MdmObjectVisitor.md)`, `[`visitMdmTimeDimension`](MdmObjectVisitor.md)`, `[`visitMdmValueHierarchy`](MdmObjectVisitor.md)

<!-- -->

- - ### Method Detail

    - #### visitMdmAssignment

          java.lang.Object visitMdmAssignment(MdmAssignment mdmObject,
                                              java.lang.Object context)

      Executes operations on the specified `MdmAssignment`.
      Parameters:
      `mdmObject` - An `MdmAssignment`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmHierarchyLevel

          java.lang.Object visitMdmHierarchyLevel(MdmHierarchyLevel mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmHierarchyLevel`.
      Parameters:
      `mdmObject` - An `MdmHierarchyLevel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDimensionLevel

          java.lang.Object visitMdmDimensionLevel(MdmDimensionLevel mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmDimensionLevel`.
      Parameters:
      `mdmObject` - An `MdmDimensionLevel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmCube

          java.lang.Object visitMdmCube(MdmCube mdmObject,
                                        java.lang.Object context)

      Executes operations on the specified `MdmCube`.
      Parameters:
      `mdmObject` - An `MdmCube`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmCustomMember

          java.lang.Object visitMdmCustomMember(MdmCustomMember mdmObject,
                                                java.lang.Object context)

      Executes operations on the specified `MdmCustomMember`.
      Parameters:
      `mdmObject` - An `MdmCustomMember`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmBaseMeasure

          java.lang.Object visitMdmBaseMeasure(MdmBaseMeasure mdmObject,
                                               java.lang.Object context)

      Executes operations on the specified `MdmBaseMeasure`.
      Parameters:
      `mdmObject` - An `MdmBaseMeasure`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmBaseAttribute

          java.lang.Object visitMdmBaseAttribute(MdmBaseAttribute mdmObject,
                                                 java.lang.Object context)

      Executes operations on the specified `MdmBaseAttribute`.
      Parameters:
      `mdmObject` - An `MdmBaseAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDerivedMeasure

          java.lang.Object visitMdmDerivedMeasure(MdmDerivedMeasure mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmDerivedMeasure`.
      Parameters:
      `mdmObject` - An `MdmDerivedMeasure`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDerivedAttribute

          java.lang.Object visitMdmDerivedAttribute(MdmDerivedAttribute mdmObject,
                                                    java.lang.Object context)

      Executes operations on the specified `MdmDerivedAttribute`.
      Parameters:
      `mdmObject` - An `MdmDerivedAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDescriptionType

          java.lang.Object visitMdmDescriptionType(MdmDescriptionType mdmObject,
                                                   java.lang.Object context)

      Executes operations on the specified `MdmDescriptionType`.
      Parameters:
      `mdmObject` - An `MdmDescriptionType`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmColumn

          java.lang.Object visitMdmColumn(MdmColumn mdmObject,
                                          java.lang.Object context)

      Executes operations on the specified `MdmColumn`.
      Parameters:
      `mdmObject` - An `MdmColumn`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmTable

          java.lang.Object visitMdmTable(MdmTable mdmObject,
                                         java.lang.Object context)

      Executes operations on the specified `MdmTable`.
      Parameters:
      `mdmObject` - An `MdmTable`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDatabaseSchema

          java.lang.Object visitMdmDatabaseSchema(MdmDatabaseSchema mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmDatabaseSchema`.
      Parameters:
      `mdmObject` - An `MdmDatabaseSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmRootSchema

          java.lang.Object visitMdmRootSchema(MdmRootSchema mdmObject,
                                              java.lang.Object context)

      Executes operations on the specified `MdmRootSchema`.
      Parameters:
      `mdmObject` - An `MdmRootSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmOrganizationalSchema

          java.lang.Object visitMdmOrganizationalSchema(MdmOrganizationalSchema mdmObject,
                                                        java.lang.Object context)

      Executes operations on the specified `MdmOrganizationalSchema`.
      Parameters:
      `mdmObject` - An `MdmOrganizationalSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmNamedBuildProcess

          java.lang.Object visitMdmNamedBuildProcess(MdmNamedBuildProcess mdmObject,
                                                     java.lang.Object context)

      Executes operations on the specified `MdmNamedBuildProcess`.
      Parameters:
      `mdmObject` - An `MdmNamedBuildProcess`.

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

- [Prev Class](Mdm11_2_ObjectVisitor.md)
- [Next Class](MdmAssignment.md)

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
