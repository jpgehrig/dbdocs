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

- [Prev Class](MdmBaseMeasure.md)
- [Next Class](MdmColumn.md)

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

## Class MdmBaseObjectVisitor

- java.lang.Object

- - oracle.olapi.metadata.mdm.MdmBaseObjectVisitor

<!-- -->

- All Implemented Interfaces:
  [Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md), [Mdm11_2_ObjectVisitor](Mdm11_2_ObjectVisitor.md), [Mdm11_ObjectVisitor](Mdm11_ObjectVisitor.md), [MdmObjectVisitor](MdmObjectVisitor.md)

  ------------------------------------------------------------------------



      public abstract class MdmBaseObjectVisitor
      extends java.lang.Object
      implements Mdm11_2_ObjectVisitor

  An implementation of the `MdmObjectVisitor` interface that adds methods for visiting more classes in the `MdmObject` class hierarchy. With your visitor, you can implement polymorphic behavior without having access to the internal code of `MdmObject` or its subclasses.
  `MdmBaseObjectVisitor` has a visit method for each of the classes in the `MdmObject` class hierarchy. `MdmObject` and its subclasses have an `acceptVisitor` method. The parameters of an `acceptVisitor` method are an `MdmObjectVisitor` and a `java.lang.Object`. When you call the `acceptVisitor` method of an `MdmObject`, the `acceptVisitor` method calls the corresponding visit method of your `MdmBaseObjectVisitor`. The `acceptVisitor` method passes the `MdmObject` and the `Object` to the visit method. For example, you could call the `acceptVisitor` method of an `MdmMeasure` and pass it your `MdmBaseObjectVisitor` and an `Object`. The `acceptVisitor` method would then pass the `MdmMeasure` and the `Object` to the `visitMdmMeasure` method of your `MdmObjectVisitor`.

  A visit method of your `MdmBaseObjectVisitor` can perform whatever operations you want it to on the `MdmObject` it receives. For example, a `visitMdmMeasure` method might call the `getDimensions` method of the `MdmMeasure`, and then call methods of the `Object` to format and display the resulting information. A visit method must return a `java.lang.Object`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                            |
    |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitMdmAssignment``(`[`MdmAssignment`](MdmAssignment.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmAssignment`.                                                                        |
    | `java.lang.Object` | `visitMdmAttribute``(`[`MdmAttribute`](MdmAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmAttribute`.                                                                            |
    | `java.lang.Object` | `visitMdmBaseAttribute``(`[`MdmBaseAttribute`](MdmBaseAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmBaseAttribute`.                                                            |
    | `java.lang.Object` | `visitMdmBaseMeasure``(`[`MdmBaseMeasure`](MdmBaseMeasure.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmBaseMeasure`.                                                                    |
    | `java.lang.Object` | `visitMdmColumn``(`[`MdmColumn`](MdmColumn.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmColumn`.                                                                                        |
    | `java.lang.Object` | `visitMdmCube``(`[`MdmCube`](MdmCube.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmCube`.                                                                                                |
    | `java.lang.Object` | `visitMdmCustomMember``(`[`MdmCustomMember`](MdmCustomMember.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmCustomMember`.                                                                |
    | `java.lang.Object` | `visitMdmDatabaseSchema``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDatabaseSchema`.                                                        |
    | `java.lang.Object` | `visitMdmDerivedAttribute``(`[`MdmDerivedAttribute`](MdmDerivedAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDerivedAttribute`.                                                |
    | `java.lang.Object` | `visitMdmDerivedMeasure``(`[`MdmDerivedMeasure`](MdmDerivedMeasure.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDerivedMeasure`.                                                        |
    | `java.lang.Object` | `visitMdmDescriptionType``(`[`MdmDescriptionType`](MdmDescriptionType.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDescriptionType`.                                                    |
    | `java.lang.Object` | `visitMdmDimension``(`[`MdmDimension`](MdmDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimension`.                                                                            |
    | `java.lang.Object` | `visitMdmDimensionality``(`[`MdmDimensionality`](MdmDimensionality.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimensionality`.                                                        |
    | `java.lang.Object` | `visitMdmDimensionCalculationModel``(`[`MdmDimensionCalculationModel`](MdmDimensionCalculationModel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimensionCalculationModel`.            |
    | `java.lang.Object` | `visitMdmDimensionedObject``(`[`MdmDimensionedObject`](MdmDimensionedObject.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimensionedObject`.                                            |
    | `java.lang.Object` | `visitMdmDimensionLevel``(`[`MdmDimensionLevel`](MdmDimensionLevel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmDimensionLevel`.                                                        |
    | `java.lang.Object` | `visitMdmHierarchy``(`[`MdmHierarchy`](MdmHierarchy.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmHierarchy`.                                                                            |
    | `java.lang.Object` | `visitMdmHierarchyLevel``(`[`MdmHierarchyLevel`](MdmHierarchyLevel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmHierarchyLevel`.                                                        |
    | `java.lang.Object` | `visitMdmLevel``(`[`MdmLevel`](MdmLevel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmLevel`.                                                                                            |
    | `java.lang.Object` | `visitMdmLevelHierarchy``(`[`MdmLevelHierarchy`](MdmLevelHierarchy.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmLevelHierarchy`.                                                        |
    | `java.lang.Object` | `visitMdmMeasure``(`[`MdmMeasure`](MdmMeasure.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMeasure`.                                                                                    |
    | `java.lang.Object` | `visitMdmMeasureDimension``(`[`MdmMeasureDimension`](MdmMeasureDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMeasureDimension`.                                                |
    | `java.lang.Object` | `visitMdmModel``(`[`MdmModel`](MdmModel.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmModel`.                                                                                            |
    | `java.lang.Object` | `visitMdmMultiValuedAttribute``(`[`MdmMultiValuedAttribute`](MdmMultiValuedAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMultiValuedAttribute`.                                |
    | `java.lang.Object` | `visitMdmMultiValuedDerivedAttribute``(`[`MdmMultiValuedDerivedAttribute`](MdmMultiValuedDerivedAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmMultiValuedDerivedAttribute`.    |
    | `java.lang.Object` | `visitMdmNamedBuildProcess``(`[`MdmNamedBuildProcess`](MdmNamedBuildProcess.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmNamedBuildProcess`.                                            |
    | `java.lang.Object` | `visitMdmObject``(`[`MdmObject`](MdmObject.md)` mdmObject, java.lang.Object context)`<br>Executes operations on any object that is a subclass of `MdmObject`, which is useful when you do not need subclass-specific information. |
    | `java.lang.Object` | `visitMdmOrganizationalSchema``(`[`MdmOrganizationalSchema`](MdmOrganizationalSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmOrganizationalSchema`.                                |
    | `java.lang.Object` | `visitMdmPrimaryDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmPrimaryDimension`.                                                |
    | `java.lang.Object` | `visitMdmRootSchema``(`[`MdmRootSchema`](MdmRootSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmRootSchema`.                                                                        |
    | `java.lang.Object` | `visitMdmSchema``(`[`MdmSchema`](MdmSchema.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmSchema`.                                                                                        |
    | `java.lang.Object` | `visitMdmSingleValuedAttribute``(`[`MdmSingleValuedAttribute`](MdmSingleValuedAttribute.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmSingleValuedAttribute`.                            |
    | `java.lang.Object` | `visitMdmSource``(`[`MdmSource`](MdmSource.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmSource`.                                                                                        |
    | `java.lang.Object` | `visitMdmStandardDimension``(`[`MdmStandardDimension`](MdmStandardDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmStandardDimension`.                                            |
    | `java.lang.Object` | `visitMdmStandardMember``(`[`MdmStandardMember`](MdmStandardMember.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmStandardMember`.                                                        |
    | `java.lang.Object` | `visitMdmSubDimension``(`[`MdmSubDimension`](MdmSubDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmSubDimension`.                                                                |
    | `java.lang.Object` | `visitMdmTable``(`[`MdmTable`](MdmTable.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmTable`.                                                                                            |
    | `java.lang.Object` | `visitMdmTimeDimension``(`[`MdmTimeDimension`](MdmTimeDimension.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmTimeDimension`.                                                            |
    | `java.lang.Object` | `visitMdmTimeMember``(`[`MdmTimeMember`](MdmTimeMember.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmTimeMember`.                                                                        |
    | `java.lang.Object` | `visitMdmValueHierarchy``(`[`MdmValueHierarchy`](MdmValueHierarchy.md)` mdmObject, java.lang.Object context)`<br>Executes operations on the specified `MdmValueHierarchy`.                                                        |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md)

      [`visitMdmAttributeModel`](Mdm10_1_0_3_ObjectVisitor.md)`, `[`visitMdmMeasureModel`](Mdm10_1_0_3_ObjectVisitor.md)

<!-- -->

- - ### Method Detail

    - #### visitMdmAttribute

          public java.lang.Object visitMdmAttribute(MdmAttribute mdmObject,
                                                    java.lang.Object context)

      Executes operations on the specified `MdmAttribute`. The default implementation of this method calls the `visitMdmDimensionedObject` method.
      Specified by:
      [`visitMdmAttribute`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDimension

          public java.lang.Object visitMdmDimension(MdmDimension mdmObject,
                                                    java.lang.Object context)

      Executes operations on the specified `MdmDimension`. The default implementation of this method calls the `visitMdmSource` method.
      Parameters:
      `mdmObject` - An `MdmDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDimensionedObject

          public java.lang.Object visitMdmDimensionedObject(MdmDimensionedObject mdmObject,
                                                            java.lang.Object context)

      Executes operations on the specified `MdmDimensionedObject`. The default implementation of this method calls the `visitMdmSource` method.
      Parameters:
      `mdmObject` - An `MdmDimensionedObject`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmHierarchy

          public java.lang.Object visitMdmHierarchy(MdmHierarchy mdmObject,
                                                    java.lang.Object context)

      Executes operations on the specified `MdmHierarchy`. The default implementation of this method calls `visitMdmSubDimension` method.
      Parameters:
      `mdmObject` - An `MdmHierarchy`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmLevel

          public java.lang.Object visitMdmLevel(MdmLevel mdmObject,
                                                java.lang.Object context)

      Executes operations on the specified `MdmLevel`. The default implementation of this method calls `visitMdmSubDimension` method.
      Specified by:
      [`visitMdmLevel`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmLevel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmLevelHierarchy

          public java.lang.Object visitMdmLevelHierarchy(MdmLevelHierarchy mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmLevelHierarchy`. The default implementation of this method calls the `visitMdmHierarchy` method.
      Specified by:
      [`visitMdmLevelHierarchy`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmLevelHierarchy`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmMeasure

          public java.lang.Object visitMdmMeasure(MdmMeasure mdmObject,
                                                  java.lang.Object context)

      Executes operations on the specified `MdmMeasure`. The default implementation of this method calls the `visitMdmDimensionedObject` method.
      Specified by:
      [`visitMdmMeasure`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmMeasure`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmMeasureDimension

          public java.lang.Object visitMdmMeasureDimension(MdmMeasureDimension mdmObject,
                                                           java.lang.Object context)

      Executes operations on the specified `MdmMeasureDimension`. The default implementation of this method calls the `visitMdmPrimaryDimension` method.
      Specified by:
      [`visitMdmMeasureDimension`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmMeasureDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmObject

          public java.lang.Object visitMdmObject(MdmObject mdmObject,
                                                 java.lang.Object context)

      Executes operations on any object that is a subclass of `MdmObject`, which is useful when you do not need subclass-specific information. The default implementation of this method returns `null`.
      Parameters:
      `mdmObject` - An `MdmObject`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmPrimaryDimension

          public java.lang.Object visitMdmPrimaryDimension(MdmPrimaryDimension mdmObject,
                                                           java.lang.Object context)

      Executes operations on the specified `MdmPrimaryDimension`. The default implementation of this method calls the `visitMdmDimension` method.
      Parameters:
      `mdmObject` - An `MdmPrimaryDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmSchema

          public java.lang.Object visitMdmSchema(MdmSchema mdmObject,
                                                 java.lang.Object context)

      Executes operations on the specified `MdmSchema`. The default implementation of this method calls the `visitMdmObject` method.
      Specified by:
      [`visitMdmSchema`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmSource

          public java.lang.Object visitMdmSource(MdmSource mdmObject,
                                                 java.lang.Object context)

      Executes operations on the specified `MdmSource`. The default implementation of this method calls the `visitMdmObject` method.
      Parameters:
      `mdmObject` - An `MdmSource`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmStandardDimension

          public java.lang.Object visitMdmStandardDimension(MdmStandardDimension mdmObject,
                                                            java.lang.Object context)

      Executes operations on the specified `MdmStandardDimension`. The default implementation of this method calls the `visitMdmPrimaryDimension` method.
      Specified by:
      [`visitMdmStandardDimension`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmStandardDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmSubDimension

          public java.lang.Object visitMdmSubDimension(MdmSubDimension mdmObject,
                                                       java.lang.Object context)

      Executes operations on the specified `MdmSubDimension`. The default implementation of this method calls the `visitMdmDimension` method.
      Parameters:
      `mdmObject` - An `MdmSubDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmTimeDimension

          public java.lang.Object visitMdmTimeDimension(MdmTimeDimension mdmObject,
                                                        java.lang.Object context)

      Executes operations on the specified `MdmTimeDimension`. The default implementation of this method calls the `visitMdmPrimaryDimension` method.
      Specified by:
      [`visitMdmTimeDimension`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmTimeDimension`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmValueHierarchy

          public java.lang.Object visitMdmValueHierarchy(MdmValueHierarchy mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmValueHierarchy`. The default implementation of this method calls the `visitMdmHierarchy` method.
      Specified by:
      [`visitMdmValueHierarchy`](MdmObjectVisitor.md) in interface [`MdmObjectVisitor`](MdmObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmValueHierarchy`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmModel

          public java.lang.Object visitMdmModel(MdmModel mdmObject,
                                                java.lang.Object context)

      Executes operations on the specified `MdmModel`.
      Parameters:
      `mdmObject` - An `MdmModel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDimensionCalculationModel

          public java.lang.Object visitMdmDimensionCalculationModel(MdmDimensionCalculationModel mdmObject,
                                                                    java.lang.Object context)

      Executes operations on the specified `MdmDimensionCalculationModel`.
      Specified by:
      [`visitMdmDimensionCalculationModel`](Mdm10_1_0_3_ObjectVisitor.md) in interface [`Mdm10_1_0_3_ObjectVisitor`](Mdm10_1_0_3_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmDimensionCalculationModel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmStandardMember

          public java.lang.Object visitMdmStandardMember(MdmStandardMember mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmStandardMember`.
      Specified by:
      [`visitMdmStandardMember`](Mdm10_1_0_3_ObjectVisitor.md) in interface [`Mdm10_1_0_3_ObjectVisitor`](Mdm10_1_0_3_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmStandardMember`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmTimeMember

          public java.lang.Object visitMdmTimeMember(MdmTimeMember mdmObject,
                                                     java.lang.Object context)

      Executes operations on the specified `MdmTimeMember`.
      Specified by:
      [`visitMdmTimeMember`](Mdm10_1_0_3_ObjectVisitor.md) in interface [`Mdm10_1_0_3_ObjectVisitor`](Mdm10_1_0_3_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmTimeMember`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmAssignment

          public java.lang.Object visitMdmAssignment(MdmAssignment mdmObject,
                                                     java.lang.Object context)

      Executes operations on the specified `MdmAssignment`.
      Specified by:
      [`visitMdmAssignment`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmAssignment`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmHierarchyLevel

          public java.lang.Object visitMdmHierarchyLevel(MdmHierarchyLevel mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmHierarchyLevel`.
      Specified by:
      [`visitMdmHierarchyLevel`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmHierarchyLevel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDimensionLevel

          public java.lang.Object visitMdmDimensionLevel(MdmDimensionLevel mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmDimensionLevel`.
      Specified by:
      [`visitMdmDimensionLevel`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmDimensionLevel`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmCube

          public java.lang.Object visitMdmCube(MdmCube mdmObject,
                                               java.lang.Object context)

      Executes operations on the specified `MdmCube`.
      Specified by:
      [`visitMdmCube`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmCube`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmCustomMember

          public java.lang.Object visitMdmCustomMember(MdmCustomMember mdmObject,
                                                       java.lang.Object context)

      Executes operations on the specified `MdmCustomMember`.
      Specified by:
      [`visitMdmCustomMember`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmCustomMember`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmBaseMeasure

          public java.lang.Object visitMdmBaseMeasure(MdmBaseMeasure mdmObject,
                                                      java.lang.Object context)

      Executes operations on the specified `MdmBaseMeasure`.
      Specified by:
      [`visitMdmBaseMeasure`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmBaseMeasure`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmBaseAttribute

          public java.lang.Object visitMdmBaseAttribute(MdmBaseAttribute mdmObject,
                                                        java.lang.Object context)

      Executes operations on the specified `MdmBaseAttribute`.
      Specified by:
      [`visitMdmBaseAttribute`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmBaseAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDerivedMeasure

          public java.lang.Object visitMdmDerivedMeasure(MdmDerivedMeasure mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmDerivedMeasure`.
      Specified by:
      [`visitMdmDerivedMeasure`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmDerivedMeasure`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDerivedAttribute

          public java.lang.Object visitMdmDerivedAttribute(MdmDerivedAttribute mdmObject,
                                                           java.lang.Object context)

      Executes operations on the specified `MdmDerivedAttribute`.
      Specified by:
      [`visitMdmDerivedAttribute`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmDerivedAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDescriptionType

          public java.lang.Object visitMdmDescriptionType(MdmDescriptionType mdmObject,
                                                          java.lang.Object context)

      Executes operations on the specified `MdmDescriptionType`.
      Specified by:
      [`visitMdmDescriptionType`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmDescriptionType`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmColumn

          public java.lang.Object visitMdmColumn(MdmColumn mdmObject,
                                                 java.lang.Object context)

      Executes operations on the specified `MdmColumn`.
      Specified by:
      [`visitMdmColumn`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmColumn`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmTable

          public java.lang.Object visitMdmTable(MdmTable mdmObject,
                                                java.lang.Object context)

      Executes operations on the specified `MdmTable`.
      Specified by:
      [`visitMdmTable`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmTable`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDatabaseSchema

          public java.lang.Object visitMdmDatabaseSchema(MdmDatabaseSchema mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmDatabaseSchema`.
      Specified by:
      [`visitMdmDatabaseSchema`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmDatabaseSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmRootSchema

          public java.lang.Object visitMdmRootSchema(MdmRootSchema mdmObject,
                                                     java.lang.Object context)

      Executes operations on the specified `MdmRootSchema`.
      Specified by:
      [`visitMdmRootSchema`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmRootSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmOrganizationalSchema

          public java.lang.Object visitMdmOrganizationalSchema(MdmOrganizationalSchema mdmObject,
                                                               java.lang.Object context)

      Executes operations on the specified `MdmOrganizationalSchema`.
      Specified by:
      [`visitMdmOrganizationalSchema`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmOrganizationalSchema`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmNamedBuildProcess

          public java.lang.Object visitMdmNamedBuildProcess(MdmNamedBuildProcess mdmObject,
                                                            java.lang.Object context)

      Executes operations on the specified `MdmNamedBuildProcess`.
      Specified by:
      [`visitMdmNamedBuildProcess`](Mdm11_ObjectVisitor.md) in interface [`Mdm11_ObjectVisitor`](Mdm11_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmNamedBuildProcess`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmMultiValuedDerivedAttribute

          public java.lang.Object visitMdmMultiValuedDerivedAttribute(MdmMultiValuedDerivedAttribute mdmObject,
                                                                      java.lang.Object context)

      Executes operations on the specified `MdmMultiValuedDerivedAttribute`.
      Specified by:
      [`visitMdmMultiValuedDerivedAttribute`](Mdm11_2_ObjectVisitor.md) in interface [`Mdm11_2_ObjectVisitor`](Mdm11_2_ObjectVisitor.md)

      Parameters:
      `mdmObject` - An `MdmMultiValuedDerivedAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmMultiValuedAttribute

          public java.lang.Object visitMdmMultiValuedAttribute(MdmMultiValuedAttribute mdmObject,
                                                               java.lang.Object context)

      Executes operations on the specified `MdmMultiValuedAttribute`.
      Parameters:
      `mdmObject` - An `MdmMultiValuedAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmSingleValuedAttribute

          public java.lang.Object visitMdmSingleValuedAttribute(MdmSingleValuedAttribute mdmObject,
                                                                java.lang.Object context)

      Executes operations on the specified `MdmSingleValuedAttribute`.
      Parameters:
      `mdmObject` - An `MdmSingleValuedAttribute`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitMdmDimensionality

          public java.lang.Object visitMdmDimensionality(MdmDimensionality mdmObject,
                                                         java.lang.Object context)

      Executes operations on the specified `MdmDimensionality`.
      Specified by:
      [`visitMdmDimensionality`](Mdm11_2_ObjectVisitor.md) in interface [`Mdm11_2_ObjectVisitor`](Mdm11_2_ObjectVisitor.md)

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

- [Prev Class](MdmBaseMeasure.md)
- [Next Class](MdmColumn.md)

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
