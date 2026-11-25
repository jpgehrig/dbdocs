Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](GraphicsUtilities.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.vis.maps.graphics

## Class AnimatedStroke

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.graphics.AnimatedStroke

<!-- -->

- All Implemented Interfaces:
  java.awt.Stroke

  ------------------------------------------------------------------------



      public class AnimatedStroke
      extends java.lang.Object
      implements java.awt.Stroke

  A Java2D basic stroke that also animates itself along the path of a shape it applied to. An animated stroke must have a dash pattern and a speed.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `MODE_ONEWAY`         |
    | `static int`      | `MODE_TWOWAY`         |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------|
    | `AnimatedStroke``()`                                                                                                         |
    | `AnimatedStroke``(java.awt.Color c)`<br>Creates a default 1-pixel wide stroke that animates at a default speed.              |
    | `AnimatedStroke``(java.awt.Color c, float speed)`<br>Creates a default 1-pixel wide stroke that animates at the given speed. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                               |
    |-------------------|------------------------------------------------------------------------------------------------------|
    | `java.awt.Shape`  | `createStrokedShape``(java.awt.Shape p)`                                                             |
    | `int`             | `getCap``()`                                                                                         |
    | `java.awt.Color`  | `getColor``()`                                                                                       |
    | `float[]`         | `getDash``()`                                                                                        |
    | `int`             | `getJoin``()`                                                                                        |
    | `float`           | `getMiterLimit``()`                                                                                  |
    | `int`             | `getMode``()`                                                                                        |
    | `float`           | `getPhase``()`                                                                                       |
    | `float`           | `getSpeed``()`                                                                                       |
    | `java.awt.Stroke` | `getStroke``()`                                                                                      |
    | `float`           | `getWidth``()`                                                                                       |
    | `boolean`         | `isBackwardFlag``()`                                                                                 |
    | `void`            | `setBackwardFlag``(boolean backwardFlag)`                                                            |
    | `void`            | `setCap``(int cap)`                                                                                  |
    | `void`            | `setColor``(java.awt.Color color)`                                                                   |
    | `void`            | `setDash``(float[] dash)`                                                                            |
    | `void`            | `setJoin``(int join)`                                                                                |
    | `void`            | `setMiterLimit``(float miterLimit)`                                                                  |
    | `void`            | `setMode``(int mode)`<br>sets the animation mode to either MODE_ONEWAY (the default) or MODE_TWOWAY. |
    | `void`            | `setSpeed``(float speed)`<br>Sets the speed for this stroke animation.                               |
    | `void`            | `setWidth``(float width)`                                                                            |
    | `void`            | `update``(long elapsedTime)`                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### MODE_ONEWAY

          public static final int MODE_ONEWAY

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### MODE_TWOWAY

          public static final int MODE_TWOWAY

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### AnimatedStroke

          public AnimatedStroke()

    <!-- -->

    - #### AnimatedStroke

          public AnimatedStroke(java.awt.Color c)

      Creates a default 1-pixel wide stroke that animates at a default speed. In order to get the animated effect, you must call the update() method on the AnimatedStroke instance, such as from inside a Layer's update() call.
      Parameters:
      `c` -

    <!-- -->

    - #### AnimatedStroke

          public AnimatedStroke(java.awt.Color c,
                                float speed)

      Creates a default 1-pixel wide stroke that animates at the given speed. In order to get the animated effect, you must call the update() method on the AnimatedStroke instance, such as from inside a Layer's update() call.
      Parameters:
      `c` -

      `speed` -

  <!-- -->

  - ### Method Detail

    - #### getCap

          public int getCap()

    <!-- -->

    - #### setCap

          public void setCap(int cap)

    <!-- -->

    - #### getColor

          public java.awt.Color getColor()

    <!-- -->

    - #### setColor

          public void setColor(java.awt.Color color)

    <!-- -->

    - #### getDash

          public float[] getDash()

    <!-- -->

    - #### setDash

          public void setDash(float[] dash)

    <!-- -->

    - #### getJoin

          public int getJoin()

    <!-- -->

    - #### setJoin

          public void setJoin(int join)

    <!-- -->

    - #### getMiterLimit

          public float getMiterLimit()

    <!-- -->

    - #### setMiterLimit

          public void setMiterLimit(float miterLimit)

    <!-- -->

    - #### getSpeed

          public float getSpeed()

    <!-- -->

    - #### setSpeed

          public void setSpeed(float speed)

      Sets the speed for this stroke animation. Speed is expressed as in how many pixels per second will the animation go along the path.
      Parameters:
      `speed` - specifies number of pixels the animation moves along the path.

    <!-- -->

    - #### getWidth

          public float getWidth()

    <!-- -->

    - #### setWidth

          public void setWidth(float width)

    <!-- -->

    - #### getMode

          public int getMode()

    <!-- -->

    - #### setMode

          public void setMode(int mode)

      sets the animation mode to either MODE_ONEWAY (the default) or MODE_TWOWAY.
      Parameters:
      `mode` -

    <!-- -->

    - #### update

          public void update(long elapsedTime)

    <!-- -->

    - #### getPhase

          public float getPhase()

    <!-- -->

    - #### getStroke

          public java.awt.Stroke getStroke()

    <!-- -->

    - #### createStrokedShape

          public java.awt.Shape createStrokedShape(java.awt.Shape p)

      Specified by:
      `createStrokedShape` in interface `java.awt.Stroke`

    <!-- -->

    - #### setBackwardFlag

          public void setBackwardFlag(boolean backwardFlag)

    <!-- -->

    - #### isBackwardFlag

          public boolean isBackwardFlag()

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](GraphicsUtilities.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
