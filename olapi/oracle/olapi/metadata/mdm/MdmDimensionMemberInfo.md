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

- [Prev Class](MdmDimensionLevel.md)
- [Next Class](MdmHierarchy.md)

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

## Class MdmDimensionMemberInfo

- java.lang.Object

- - oracle.olapi.metadata.mdm.MdmDimensionMemberInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class MdmDimensionMemberInfo
      extends java.lang.Object

  Provides information about a member of an `MdmHierarchy`. An application can use an `MdmDimensionMemberInfo` to specify a default member for an `MdmHierarchy`.
  An application can create an `MdmDimensionMemberInfo` for a dimension member that does not exist. Oracle OLAP does not automatically create a dimension member when the application creates an `MdmDimensionMemberInfo`.

  In creating an `MdmDimensionMemberInfo`, an application specifies an `MdmPrimaryDimension` and a unique dimension member value or an `MdmHierarchyLevel` and a local value.

  A unique value specifies a hierarchy, a level of the hierarchy, and a member value in that level, as in the following example from an `MdmPrimaryDimension` that represents products organized by a set of related product levels.

       PRODUCT_PRIMARY::ITEM::ENVY STD

  `PRODUCT_PRIMARY` is the name of an `MdmLevelHierarchy` component of the `MdmPrimaryDimension`, `ITEM` is the name of an `MdmHierarchyLevel` that is a component of the `MdmLevelHierarchy`, and `ENVY STD` is the local value of a member of the `MdmLevelHierarchy` and the `MdmHierarchyLevel`.
  The parts of the unique value are separated by a value separation string. The value separation string in the preceding example is `::`, the double colons.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `MdmDimensionMemberInfo``(`[`MdmLevel`](MdmLevel.md)` level, java.lang.Object localValue)`<br>Creates a new `MdmDimensionMemberInfo` that specifies the local value of a dimension member and an `MdmHierarchyLevel`.                                      |
    | `MdmDimensionMemberInfo``(`[`MdmMetadataProvider`](MdmMetadataProvider.md)` metadataProvider)`<br>Creates a new `MdmDimensionMemberInfo` that does not yet identify a dimension member.                                                                    |
    | `MdmDimensionMemberInfo``(`[`MdmMetadataProvider`](MdmMetadataProvider.md)` metadataProvider, java.lang.String uniqueValue)`<br>Creates a new `MdmDimensionMemberInfo` that specifies the unique value of a dimension member.                              |
    | `MdmDimensionMemberInfo``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` primaryDimension, java.lang.String uniqueValue)`<br>Creates a new `MdmDimensionMemberInfo` that specifies the unique value of a dimension member and an `MdmPrimaryDimension`. |
    | `MdmDimensionMemberInfo``(`[`MdmValueHierarchy`](MdmValueHierarchy.md)` valueHierarchy, java.lang.Object localValue)`<br>Creates a new `MdmDimensionMemberInfo` that specifies the local value of a dimension member and an `MdmValueHierarchy`.           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                             |
    |-------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmHierarchy`](MdmHierarchy.md)               | `getHierarchy``()`<br>Gets the `MdmHierarchy` that contains the dimension member associated with this `MdmDimensionMemberInfo`.                    |
    | [`MdmLevel`](MdmLevel.md)                       | `getLevel``()`<br>Gets the `MdmHierarchyLevel` that contains the dimension member associated with this `MdmDimensionMemberInfo`.                   |
    | `java.lang.Object`                              | `getLocalValue``()`<br>Gets the local value of the dimension member associated with this `MdmDimensionMemberInfo`.                                 |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md) | `getPrimaryDimension``()`<br>Gets the `MdmPrimaryDimension` that contains the dimension member associated with this `MdmDimensionMemberInfo`.      |
    | `java.lang.String`                              | `getUniqueValue``()`<br>Gets the unique value of the dimension member associated with this `MdmDimensionMemberInfo`.                               |
    | `void`                                          | `setHierarchy``(`[`MdmHierarchy`](MdmHierarchy.md)` hierarchy)`<br>Specifies the hierarchy for this `MdmDimensionMemberInfo`.                      |
    | `void`                                          | `setLevel``(`[`MdmLevel`](MdmLevel.md)` level)`<br>Specifies the level for this `MdmDimensionMemberInfo`.                                          |
    | `void`                                          | `setLocalValue``(java.lang.Object localValue)`<br>Specifies the local value for this `MdmDimensionMemberInfo`.                                     |
    | `void`                                          | `setPrimaryDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` dimension)`<br>Specifies the dimension for this `MdmDimensionMemberInfo`. |
    | `void`                                          | `setUniqueValue``(java.lang.String uniqueValue)`<br>Specifies the unique value for this `MdmDimensionMemberInfo`.                                  |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### MdmDimensionMemberInfo

          public MdmDimensionMemberInfo(MdmMetadataProvider metadataProvider)

      Creates a new `MdmDimensionMemberInfo` that does not yet identify a dimension member. To specify a member, call either the `setUniqueValue` method, or the `setLocalValue` and `setLevel` or `setHierarchy` methods.
      Parameters:
      `metadataProvider` - The `MdmMetadataProvider` for the current session.

    <!-- -->

    - #### MdmDimensionMemberInfo

          public MdmDimensionMemberInfo(MdmMetadataProvider metadataProvider,
                                        java.lang.String uniqueValue)

      Creates a new `MdmDimensionMemberInfo` that specifies the unique value of a dimension member.
      Parameters:
      `metadataProvider` - The `MdmMetadataProvider` for the current session.

      `uniqueValue` - A `String` that specifies a unique dimension member value, such as `PRODUCT_PRIMARY::ITEM::ENVY STD`.

    <!-- -->

    - #### MdmDimensionMemberInfo

          public MdmDimensionMemberInfo(MdmPrimaryDimension primaryDimension,
                                        java.lang.String uniqueValue)

      Creates a new `MdmDimensionMemberInfo` that specifies the unique value of a dimension member and an `MdmPrimaryDimension`. The unique value does not have to be the value of a member of the `MdmPrimaryDimension`.
      Parameters:
      `primaryDimension` - AN `MdmPrimaryDimension`.

      `uniqueValue` - A `String` that specifies a unique dimension member value.

    <!-- -->

    - #### MdmDimensionMemberInfo

          public MdmDimensionMemberInfo(MdmLevel level,
                                        java.lang.Object localValue)

      Creates a new `MdmDimensionMemberInfo` that specifies the local value of a dimension member and an `MdmHierarchyLevel`. The local value does not have to be the value of a member of the `MdmHierarchyLevel`.
      Parameters:
      `level` - An `MdmHierarchyLevel`.

      `localValue` - An `Object` that specifies the local value of a dimension member.

    <!-- -->

    - #### MdmDimensionMemberInfo

          public MdmDimensionMemberInfo(MdmValueHierarchy valueHierarchy,
                                        java.lang.Object localValue)

      Creates a new `MdmDimensionMemberInfo` that specifies the local value of a dimension member and an `MdmValueHierarchy`. Constructs an `MdmDimensionMemberInfo` based on a local value and an `MdmValueHierarchy`.
      Parameters:
      `valueHierarchy` - An `MdmValueHierarchy`.

      `localValue` - An `Object` that specifies the local value of a dimension member.

  <!-- -->

  - ### Method Detail

    - #### setUniqueValue

          public void setUniqueValue(java.lang.String uniqueValue)

      Specifies the unique value for this `MdmDimensionMemberInfo`.
      Parameters:
      `uniqueValue` - A `String` that specifies a unique dimension member value.

    <!-- -->

    - #### setLocalValue

          public void setLocalValue(java.lang.Object localValue)

      Specifies the local value for this `MdmDimensionMemberInfo`.
      Parameters:
      `localValue` - An `Object` that specifies the local value of a dimension member.

    <!-- -->

    - #### setLevel

          public void setLevel(MdmLevel level)

      Specifies the level for this `MdmDimensionMemberInfo`.
      Parameters:
      `level` - An `MdmHierarchyLevel`.

    <!-- -->

    - #### setHierarchy

          public void setHierarchy(MdmHierarchy hierarchy)

      Specifies the hierarchy for this `MdmDimensionMemberInfo`. You do not need to use this method if you use the `setLevel` method.
      Parameters:
      `hierarchy` - The `MdmHierarchy` to associate with this `MdmDimensionMemberInfo`.

    <!-- -->

    - #### setPrimaryDimension

          public void setPrimaryDimension(MdmPrimaryDimension dimension)

      Specifies the dimension for this `MdmDimensionMemberInfo`. You do not need to use this method if you use the `setHierarchy` or the `setLevel` method.
      Parameters:
      `dimension` - An `MdmPrimaryDimension` to associate with this `MdmDimensionMemberInfo`.

    <!-- -->

    - #### getLevel

          public MdmLevel getLevel()
                            throws MdmInvalidValueException,
                                   oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmHierarchyLevel` that contains the dimension member associated with this `MdmDimensionMemberInfo`.
      Returns:
      The `MdmHierarchyLevel` that has the member associated with this `MdmDimensionMemberInfo` or `null` if the member belongs to an `MdmValueHierarchy`.

      Throws:
      [`MdmInvalidValueException`](MdmInvalidValueException.md)

      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getHierarchy

          public MdmHierarchy getHierarchy()
                                    throws MdmInvalidValueException,
                                           oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmHierarchy` that contains the dimension member associated with this `MdmDimensionMemberInfo`.
      Returns:
      The `MdmHierarchy` that has the member associated with this `MdmDimensionMemberInfo`.

      Throws:
      [`MdmInvalidValueException`](MdmInvalidValueException.md)

      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getPrimaryDimension

          public MdmPrimaryDimension getPrimaryDimension()
                                                  throws MdmInvalidValueException,
                                                         oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmPrimaryDimension` that contains the dimension member associated with this `MdmDimensionMemberInfo`.
      Returns:
      The `MdmPrimaryDimension` that has the member associated with this `MdmDimensionMemberInfo`.

      Throws:
      [`MdmInvalidValueException`](MdmInvalidValueException.md)

      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getLocalValue

          public java.lang.Object getLocalValue()
                                         throws MdmInvalidValueException,
                                                oracle.express.mdm.MetadataNotFoundException

      Gets the local value of the dimension member associated with this `MdmDimensionMemberInfo`.
      Returns:
      An `Object` that contains the local value of the member associated with this `MdmDimensionMemberInfo`.

      Throws:
      [`MdmInvalidValueException`](MdmInvalidValueException.md)

      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getUniqueValue

          public java.lang.String getUniqueValue()
                                          throws MdmInvalidValueException,
                                                 oracle.express.mdm.MetadataNotFoundException

      Gets the unique value of the dimension member associated with this `MdmDimensionMemberInfo`.
      Returns:
      An `Object` that contains the unique value of the member associated with this `MdmDimensionMemberInfo`.

      Throws:
      [`MdmInvalidValueException`](MdmInvalidValueException.md)

      `oracle.express.mdm.MetadataNotFoundException`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDimensionLevel.md)
- [Next Class](MdmHierarchy.md)

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
