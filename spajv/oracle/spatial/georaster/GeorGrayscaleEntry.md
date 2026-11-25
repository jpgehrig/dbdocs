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

- [Prev Class](GeorGrayscale.md)
- [Next Class](GeorHistogram.md)

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

## Class GeorGrayscaleEntry

- java.lang.Object

- - oracle.spatial.georaster.GeorGrayscaleEntry

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorGrayscaleEntry
      extends java.lang.Object

  A GeoRaster grayscale entry, which contains two components: cellvalue and gray. It is combined with class GeorGrayscale to represent a GeoRaster grayscale.
  Two constructors are provided: one is the default constructor without parameters, and the other constructor allows you to specify a cell value and gray value.

  Methods in this class are provided for retrieving and setting the cell value and gray value.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                              |
    |------------------------------------------------------------------------------------------------------------------------------------------|
    | `GeorGrayscaleEntry``()`<br>Constructs a `GeorGrayscaleEntry` object.                                                                    |
    | `GeorGrayscaleEntry``(double cellValue, int gray)`<br>Constructs a `GeorGrayscaleEntry` object with the given cell value and gray value. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                     |
    |-------------------|------------------------------------------------------------|
    | `double`          | `getCellValue``()`<br>Returns the cell value.              |
    | `int`             | `getGray``()`<br>Returns the gray value.                   |
    | `void`            | `setCellValue``(double cellValue)`<br>Sets the cell value. |
    | `void`            | `setGray``(int gray)`<br>Sets the gray value.              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorGrayscaleEntry

          public GeorGrayscaleEntry()

      Constructs a `GeorGrayscaleEntry` object.

    <!-- -->

    - #### GeorGrayscaleEntry

          public GeorGrayscaleEntry(double cellValue,
                                    int gray)

      Constructs a `GeorGrayscaleEntry` object with the given cell value and gray value.
      Parameters:
      `cellValue` - cell value

      `gray` - gray value

  <!-- -->

  - ### Method Detail

    - #### getCellValue

          public double getCellValue()

      Returns the cell value.
      Returns:
      cell value.

    <!-- -->

    - #### setCellValue

          public void setCellValue(double cellValue)

      Sets the cell value.
      Parameters:
      `cellValue` - cell value

    <!-- -->

    - #### getGray

          public int getGray()

      Returns the gray value.
      Returns:
      gray value.

    <!-- -->

    - #### setGray

          public void setGray(int gray)

      Sets the gray value.
      Parameters:
      `gray` - gray value

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

- [Prev Class](GeorGrayscale.md)
- [Next Class](GeorHistogram.md)

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
