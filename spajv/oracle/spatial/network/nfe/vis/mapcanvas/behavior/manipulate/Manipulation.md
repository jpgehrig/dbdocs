Skip navigation links

- [Overview](../../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../../deprecated-list.md)
- [Index](../../../../../../../../index-all.md)
- [Help](../../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](ManipulableLayer.md)
- [Next Class](ManipulationPreview.md)

<!-- -->

- [Frames](../../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate

## Class Manipulation\<V\>

- java.lang.Object

- - oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate.Manipulation\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of elements that are manipulated

  ------------------------------------------------------------------------



      public class Manipulation<V>
      extends java.lang.Object

  Contains information regarding to how an element is manipulated

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                         |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | `static byte`     | `TRANS_MOVE`<br>Flag indicating the element was moved                                         |
    | `static byte`     | `TRANS_PULL_LINE_END`<br>Flag indicating the element was pulled from its end point            |
    | `static byte`     | `TRANS_PULL_LINE_MID`<br>Flag indicating the element was pulled from one of its middle points |
    | `static byte`     | `TRANS_PULL_LINE_START`<br>Flag indicating the element was pulled from its start point        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                               |
    |-------------------------------------------------------------------------------------------|
    | `Manipulation``(V element, byte transformFlags)`<br>Allocates a new manipulation instance |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                                                 |
    |--------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                 | `addChangeFlag``(byte changeFlag)`<br>Adds a flag which represents a transformation being performed in the manipulation                                |
    | `boolean`                                              | `containsTransformFlags``(byte transformFlag)`<br>Tells whether the manipulation contains the given transform flags                                    |
    | `boolean`                                              | `equals``(java.lang.Object obj)`                                                                                                                       |
    | [`JGeometry`](../../../../../../geometry/JGeometry.md) | `getChangedGeometry``()`<br>Gets the element's geometry after the manipulation                                                                         |
    | `V`                                                    | `getElement``()`<br>Gets the manipulated element                                                                                                       |
    | `byte`                                                 | `getTransformFlags``()`<br>Gets all the transform flags of the manipulation                                                                            |
    | `void`                                                 | `setChangedGeometry``(`[`JGeometry`](../../../../../../geometry/JGeometry.md)` changedGeometry)`<br>Sets the element's geometry after the manipulation |
    | `void`                                                 | `setElement``(V element)`<br>Sets the manipulated element                                                                                              |
    | `void`                                                 | `setTransformFlags``(byte transformFlags)`<br>Overwrites the manipulation transform flags                                                              |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### TRANS_MOVE

          public static byte TRANS_MOVE

      Flag indicating the element was moved

    <!-- -->

    - #### TRANS_PULL_LINE_START

          public static byte TRANS_PULL_LINE_START

      Flag indicating the element was pulled from its start point

    <!-- -->

    - #### TRANS_PULL_LINE_END

          public static byte TRANS_PULL_LINE_END

      Flag indicating the element was pulled from its end point

    <!-- -->

    - #### TRANS_PULL_LINE_MID

          public static byte TRANS_PULL_LINE_MID

      Flag indicating the element was pulled from one of its middle points

  <!-- -->

  - ### Constructor Detail

    - #### Manipulation

          public Manipulation(V element,
                              byte transformFlags)

      Allocates a new manipulation instance
      Parameters:
      `element` - the element being manipulated

      `transformFlags` - the transform flags describing the manipulation

  <!-- -->

  - ### Method Detail

    - #### addChangeFlag

          public void addChangeFlag(byte changeFlag)

      Adds a flag which represents a transformation being performed in the manipulation
      Parameters:
      `changeFlag` - a transform flag

    <!-- -->

    - #### containsTransformFlags

          public boolean containsTransformFlags(byte transformFlag)

      Tells whether the manipulation contains the given transform flags
      Parameters:

      `transformFlag` - transform flags

      Returns:

    <!-- -->

    - #### getTransformFlags

          public byte getTransformFlags()

      Gets all the transform flags of the manipulation
      Returns:
      transform flags

    <!-- -->

    - #### setTransformFlags

          public void setTransformFlags(byte transformFlags)

      Overwrites the manipulation transform flags
      Parameters:
      `transformFlags` - transform flags

    <!-- -->

    - #### getElement

          public V getElement()

      Gets the manipulated element
      Returns:
      the manipulated element

    <!-- -->

    - #### setElement

          public void setElement(V element)

      Sets the manipulated element
      Parameters:
      `element` - the manipulated element

    <!-- -->

    - #### getChangedGeometry

          public JGeometry getChangedGeometry()

      Gets the element's geometry after the manipulation
      Returns:
      an SDO geometry

    <!-- -->

    - #### setChangedGeometry

          public void setChangedGeometry(JGeometry changedGeometry)

      Sets the element's geometry after the manipulation
      Parameters:
      `changedGeometry` - an SDO geometry

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

Skip navigation links

- [Overview](../../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../../deprecated-list.md)
- [Index](../../../../../../../../index-all.md)
- [Help](../../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](ManipulableLayer.md)
- [Next Class](ManipulationPreview.md)

<!-- -->

- [Frames](../../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../../allclasses-noframe.md)

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
