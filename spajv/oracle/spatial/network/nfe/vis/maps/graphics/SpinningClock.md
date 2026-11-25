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

- [Prev Class](ShadowRenderer.md)
- Next Class

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

## Class SpinningClock

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.graphics.SpinningClock

<!-- -->

-

  ------------------------------------------------------------------------



      public class SpinningClock
      extends java.lang.Object

  Provides a utility to display an animated clock with spinning hour and minute hands. The size of the clock as well as individual movement speed of the hands can be customized.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `SpinningClock``()`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                                  |
    |-------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `int`                   | `getClockHeight``()`<br>Returns the clock's height                                                                      |
    | `int`                   | `getClockWidth``()`<br>Sets the clock's height                                                                          |
    | `double`                | `getHourHandSpeed``()`<br>Returns the clock´s hour hand speed                                                           |
    | `double`                | `getMinuteHandSpeed``()`<br>Returns the clock´s minute hand speed                                                       |
    | `java.awt.geom.Point2D` | `getTopLeftCorner``()`<br>Returns the top left corner position for this spinning clock.                                 |
    | `long`                  | `render``(java.awt.Graphics2D g)`                                                                                       |
    | `void`                  | `setClockSize``(int width, int height)`<br>Sets the new width and height for the indicator.                             |
    | `void`                  | `setHourHandSpeed``(double seconds)`<br>Sets the clock´s hour hand speed                                                |
    | `void`                  | `setMinuteHandSpeed``(double seconds)`<br>Sets the clock´s minute hand speed                                            |
    | `void`                  | `setTopLeftCorner``(java.awt.geom.Point2D topLeftCorner)`<br>Sets the top left corner position for this spinning clock. |
    | `void`                  | `update``(long elapsedTime)`<br>Refreshes the clock hands                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SpinningClock

          public SpinningClock()

  <!-- -->

  - ### Method Detail

    - #### update

          public void update(long elapsedTime)

      Refreshes the clock hands
      Parameters:
      `elapsedTime` -

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D g)

    <!-- -->

    - #### setClockSize

          public void setClockSize(int width,
                                   int height)

      Sets the new width and height for the indicator. The default is 32 by 32 pixels.
      Parameters:
      `width` - the new width in pixel

      `height` - the new height in pixel

    <!-- -->

    - #### setMinuteHandSpeed

          public void setMinuteHandSpeed(double seconds)

      Sets the clock´s minute hand speed
      Parameters:
      `seconds` -

    <!-- -->

    - #### getMinuteHandSpeed

          public double getMinuteHandSpeed()

      Returns the clock´s minute hand speed
      Returns:

    <!-- -->

    - #### setHourHandSpeed

          public void setHourHandSpeed(double seconds)

      Sets the clock´s hour hand speed
      Parameters:
      `seconds` -

    <!-- -->

    - #### getHourHandSpeed

          public double getHourHandSpeed()

      Returns the clock´s hour hand speed
      Returns:

    <!-- -->

    - #### getTopLeftCorner

          public java.awt.geom.Point2D getTopLeftCorner()

      Returns the top left corner position for this spinning clock.
      Returns:

    <!-- -->

    - #### setTopLeftCorner

          public void setTopLeftCorner(java.awt.geom.Point2D topLeftCorner)

      Sets the top left corner position for this spinning clock.
      Parameters:
      `topLeftCorner` -

    <!-- -->

    - #### getClockHeight

          public int getClockHeight()

      Returns the clock's height
      Returns:

    <!-- -->

    - #### getClockWidth

          public int getClockWidth()

      Sets the clock's height
      Returns:

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

- [Prev Class](ShadowRenderer.md)
- Next Class

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
