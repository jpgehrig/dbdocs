Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeorColormap.md)
- [Next Class](GeorFunctionalFittingModel.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.georaster

## Class GeorColormapEntry

- java.lang.Object

- - oracle.spatial.georaster.GeorColormapEntry

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorColormapEntry
      extends java.lang.Object

  A GeoRaster colormap entry, which contains five components: cellValue, red, green, blue, and alpha (alpha is optional). It is combined with class GeorColormap to represent a GeoRaster colormap.
  Two constructors are provided: one is default constructor without parameters, and the other constructor allows you to specify the cell value and four components: red, green, blue, and alpha.

  Methods in this class are provided for retrieving and setting the cell value and each component of red, green, blue, and alpha.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                         |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `GeorColormapEntry``()`<br>Constructs a `GeorColormapEntry` object.                                                                                                                                 |
    | `GeorColormapEntry``(double value, int red, int green, int blue, java.lang.Double alpha)`<br>Constructs a `GeorColormapEntry` object with the given cell value, red, green, blue, and alpha values. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                  |
    |--------------------|-------------------------------------------------------------------------|
    | `java.lang.Double` | `getAlpha``()`<br>Returns the alpha value component.                    |
    | `int`              | `getBlue``()`<br>Returns the blue color component.                      |
    | `double`           | `getCellValue``()`<br>Returns the cell value.                           |
    | `int`              | `getGreen``()`<br>Returns the green color component.                    |
    | `int`              | `getRed``()`<br>Returns the red color component.                        |
    | `void`             | `setAlpha``(java.lang.Double alpha)`<br>Sets the alpha value component. |
    | `void`             | `setBlue``(int blue)`<br>Sets the blue color component.                 |
    | `void`             | `setCellValue``(double cellValue)`<br>Sets the cell value.              |
    | `void`             | `setGreen``(int green)`<br>Sets the green color component.              |
    | `void`             | `setRed``(int red)`<br>Sets the red color component.                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorColormapEntry

          public GeorColormapEntry()

      Constructs a `GeorColormapEntry` object.

    <!-- -->

    - #### GeorColormapEntry

          public GeorColormapEntry(double value,
                                   int red,
                                   int green,
                                   int blue,
                                   java.lang.Double alpha)

      Constructs a `GeorColormapEntry` object with the given cell value, red, green, blue, and alpha values.
      Alpha value can be null.

      Parameters:
      `value` - cell value

      `red` - red color component

      `green` - green color component

      `blue` - blue color component

      `alpha` - alpha color component

  <!-- -->

  - ### Method Detail

    - #### getCellValue

          public double getCellValue()

      Returns the cell value.
      Returns:
      cell value

    <!-- -->

    - #### setCellValue

          public void setCellValue(double cellValue)

      Sets the cell value.
      Parameters:
      `cellValue` - cell value

    <!-- -->

    - #### getRed

          public int getRed()

      Returns the red color component.
      Returns:
      red color component

    <!-- -->

    - #### setRed

          public void setRed(int red)

      Sets the red color component.
      Parameters:
      `red` - red color component

    <!-- -->

    - #### getGreen

          public int getGreen()

      Returns the green color component.
      Returns:
      green color component

    <!-- -->

    - #### setGreen

          public void setGreen(int green)

      Sets the green color component.
      Parameters:
      `green` - green color component

    <!-- -->

    - #### getBlue

          public int getBlue()

      Returns the blue color component.
      Returns:
      blue color component

    <!-- -->

    - #### setBlue

          public void setBlue(int blue)

      Sets the blue color component.
      Parameters:
      `blue` - blue color component

    <!-- -->

    - #### getAlpha

          public java.lang.Double getAlpha()

      Returns the alpha value component.
      Returns:
      alpha value component

    <!-- -->

    - #### setAlpha

          public void setAlpha(java.lang.Double alpha)

      Sets the alpha value component.
      Parameters:
      `alpha` - alpha value component

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeorColormap.md)
- [Next Class](GeorFunctionalFittingModel.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
