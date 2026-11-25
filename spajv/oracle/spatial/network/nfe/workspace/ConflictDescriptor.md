Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](FeatureAttributeDescriptor.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.workspace

## Class ConflictDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.ConflictDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class ConflictDescriptor
      extends java.lang.Object

  Describes a conflict as in the conflict table.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                         |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ConflictDescriptor``()`<br>Constructor.                                                                                                                                                                                            |
    | `ConflictDescriptor``(java.util.Map<java.lang.String,java.lang.String> keyList, java.lang.String attr, java.lang.Object parValue, java.lang.Object childValue, java.lang.String parDel, java.lang.String childDel)`<br>Constructor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                     |
    |----------------------------------------------------|------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                                 | `getAttribute``()`<br>Returns the attribute in conflict.                                                   |
    | `java.lang.Object`                                 | `getChildValue``()`<br>Returns the attribute child value.                                                  |
    | `java.util.Map<java.lang.String,java.lang.String>` | `getKeyList``()`<br>Returns the key list.                                                                  |
    | `java.lang.Object`                                 | `getParentValue``()`<br>Returns the attribute parent value.                                                |
    | `boolean`                                          | `isChildRecordDeleted``()`<br>Returns true if the child record is deleted, false otherwise.                |
    | `boolean`                                          | `isParentRecordDeleted``()`<br>Returns true if the parent record is deleted, false otherwise.              |
    | `void`                                             | `setAttribute``(java.lang.String attribute)`<br>Sets the attribute in conflict.                            |
    | `void`                                             | `setChildRecordDeleted``(boolean deleted)`<br>Sets true if the child record is deleted, false otherwise.   |
    | `void`                                             | `setChildValue``(java.lang.Object value)`<br>Sets the attribute child value.                               |
    | `void`                                             | `setKeyList``(java.util.Map<java.lang.String,java.lang.String> keyList)`<br>Sets key list.                 |
    | `void`                                             | `setParentRecordDeleted``(boolean deleted)`<br>Sets true if the parent record is deleted, false otherwise. |
    | `void`                                             | `setParentValue``(java.lang.Object value)`<br>Sets the attribute parent value.                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ConflictDescriptor

          public ConflictDescriptor()

      Constructor.

    <!-- -->

    - #### ConflictDescriptor

          public ConflictDescriptor(java.util.Map<java.lang.String,java.lang.String> keyList,
                                    java.lang.String attr,
                                    java.lang.Object parValue,
                                    java.lang.Object childValue,
                                    java.lang.String parDel,
                                    java.lang.String childDel)

      Constructor.
      Parameters:
      `keyList` - key list map. The key of the map is the column name and the value is the value of the key

      `attr` - attribute

      `parValue` - parent workspace value

      `childValue` - child workspace value

      `parDel` - if parent is deleted ("YES" or "NO")

      `childDel` - if child is deleted ("YES" or "NO")

  <!-- -->

  - ### Method Detail

    - #### getKeyList

          public java.util.Map<java.lang.String,java.lang.String> getKeyList()

      Returns the key list.
      Returns:
      key list map. The key of the map is the key column name and the value is the value of the key

    <!-- -->

    - #### setKeyList

          public void setKeyList(java.util.Map<java.lang.String,java.lang.String> keyList)

      Sets key list.
      Parameters:
      `keyList` - The key of the map is the key column name and the value is the value of the key

    <!-- -->

    - #### getAttribute

          public java.lang.String getAttribute()

      Returns the attribute in conflict.
      Returns:
      attribute

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String attribute)

      Sets the attribute in conflict.
      Parameters:
      `attribute` - attribute

    <!-- -->

    - #### getParentValue

          public java.lang.Object getParentValue()

      Returns the attribute parent value.
      Returns:
      attribute parent value

    <!-- -->

    - #### setParentValue

          public void setParentValue(java.lang.Object value)

      Sets the attribute parent value.
      Parameters:
      `value` - attribute parent value

    <!-- -->

    - #### getChildValue

          public java.lang.Object getChildValue()

      Returns the attribute child value.
      Returns:
      attribute child value

    <!-- -->

    - #### setChildValue

          public void setChildValue(java.lang.Object value)

      Sets the attribute child value.
      Parameters:
      `value` - attribute child value

    <!-- -->

    - #### isParentRecordDeleted

          public boolean isParentRecordDeleted()

      Returns true if the parent record is deleted, false otherwise.
      Returns:
      true if the parent record is deleted, false otherwise

    <!-- -->

    - #### setParentRecordDeleted

          public void setParentRecordDeleted(boolean deleted)

      Sets true if the parent record is deleted, false otherwise.
      Parameters:
      `deleted` - true if the parent record is deleted, false otherwise

    <!-- -->

    - #### isChildRecordDeleted

          public boolean isChildRecordDeleted()

      Returns true if the child record is deleted, false otherwise.
      Returns:
      true if the child record is deleted, false otherwise

    <!-- -->

    - #### setChildRecordDeleted

          public void setChildRecordDeleted(boolean deleted)

      Sets true if the child record is deleted, false otherwise.
      Parameters:
      `deleted` - true if the child record is deleted, false otherwise

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](FeatureAttributeDescriptor.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
