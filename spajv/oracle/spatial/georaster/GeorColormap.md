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

- [Prev Class](GeoRasterException.md)
- [Next Class](GeorColormapEntry.md)

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

## Class GeorColormap

- java.lang.Object

- - oracle.spatial.georaster.GeorColormap

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorColormap
      extends java.lang.Object

  GeorColormap is combined with class GeorColormapEnrty to represent a GeoRaster colormap, which contains an array of GeorColormapEnrty instances, and each GeorColormapEnrty contains four components: red, green, blue, and alpha (alpha is optional).
  The definition of GeoRaster colormap is a superset of definition of Java IndexColorModel. In a GeoRaster colormap, the data type of the value component is double and all values are not necessarily continuous as with Java IndexColorModel; all cell values falling into the range \[value1, value2) will be mapped to Red/Green/Blue/Alpha indexed by value value1.

  Two constructors are provided: one is the default constructor without parameters, and the other constructor allows you to specify the length of GeorColormapEntry array, in which case the constructor will create a GeorColormapEntry array based on the length.

  In this class, methods are provided for retrieving and setting the GeorColormapEntry array and each individual entry.

  The following two methods defined in the class SublayerInfo are used to retrieve and set colormap in the GeoRaster metadata through an instance of GeorColormap:

           public GeorColormap getColormap();
           public void setColormap(GeorColormap colormap);


<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                     |
    |-------------------------------------------------------------------------------------------------|
    | `GeorColormap``()`<br>Constructs a `GeorColormap` object.                                       |
    | `GeorColormap``(int length)`<br>Constructs a `GeorColormap` object with the given array length. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                   |
    |-------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`GeorColormapEntry`](GeorColormapEntry.md)`[]` | `getColormapEntries``()`<br>Returns the GeorColormapEntry array.                                                                                                                         |
    | [`GeorColormapEntry`](GeorColormapEntry.md)     | `getColormapEntry``(double value)`<br>Returns a GeorColormap entry indexed by a given value.                                                                                             |
    | [`GeorColormapEntry`](GeorColormapEntry.md)     | `getColormapEntry``(int entryNo)`<br>Returns a GeorColormap entry indexed by a given entry number.                                                                                       |
    | `boolean`                                       | `setColormapEntries``(double[] value, int[] red, int[] green, int[] blue, java.lang.Double[] alpha)`<br>Sets the GeorColormapEntry array by specifying five individual component arrays. |
    | `boolean`                                       | `setColormapEntries``(`[`GeorColormapEntry`](GeorColormapEntry.md)`[] colormapEntries)`<br>Sets the GeorColormapEntry array.                                                             |
    | `boolean`                                       | `setColormapEntry``(double value, int red, int green, int blue, java.lang.Double alpha)`<br>Sets a GeorColormapEntry based on value.                                                     |
    | `boolean`                                       | `setColormapEntry``(int entryNo, double value, int red, int green, int blue, java.lang.Double alpha)`<br>Sets a GeorColormapEntry based on entryNo.                                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorColormap

          public GeorColormap()

      Constructs a `GeorColormap` object.

    <!-- -->

    - #### GeorColormap

          public GeorColormap(int length)

      Constructs a `GeorColormap` object with the given array length.
      Parameters:
      `length` - length of GeorColormapEntry array

  <!-- -->

  - ### Method Detail

    - #### getColormapEntries

          public GeorColormapEntry[] getColormapEntries()

      Returns the GeorColormapEntry array.
      Returns:
      GeorColormapEntry array

    <!-- -->

    - #### setColormapEntries

          public boolean setColormapEntries(double[] value,
                                            int[] red,
                                            int[] green,
                                            int[] blue,
                                            java.lang.Double[] alpha)

      Sets the GeorColormapEntry array by specifying five individual component arrays. If the value array is not sorted in ascending order, then it will be sorted first.
      Parameters:
      `value` - cell value array

      `red` - red component array

      `green` - green component array

      `blue` - blue component array

      `alpha` - alpha component array

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setColormapEntries

          public boolean setColormapEntries(GeorColormapEntry[] colormapEntries)

      Sets the GeorColormapEntry array. If the value array is not sorted in ascending order, then it will be sorted first.
      Parameters:
      `colormapEntries` - GeorColormapEntry array

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setColormapEntry

          public boolean setColormapEntry(int entryNo,
                                          double value,
                                          int red,
                                          int green,
                                          int blue,
                                          java.lang.Double alpha)

      Sets a GeorColormapEntry based on entryNo.
      Parameters:
      `entryNo` - index of GeorColormapEntry array, from 0 to (array length-1)

      `value` - cell value

      `red` - red color component

      `green` - green color component

      `blue` - blue color component

      `alpha` - alpha color component

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setColormapEntry

          public boolean setColormapEntry(double value,
                                          int red,
                                          int green,
                                          int blue,
                                          java.lang.Double alpha)

      Sets a GeorColormapEntry based on value.
      Parameters:
      `value` - cell value

      `red` - red color component

      `green` - green color component

      `blue` - blue color component

      `alpha` - alpha color component

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### getColormapEntry

          public GeorColormapEntry getColormapEntry(int entryNo)

      Returns a GeorColormap entry indexed by a given entry number.
      Parameters:
      `entryNo` - entry number

      Returns:
      a GeorColormap entry indexed by the given entry number.

    <!-- -->

    - #### getColormapEntry

          public GeorColormapEntry getColormapEntry(double value)

      Returns a GeorColormap entry indexed by a given value.
      Parameters:
      `value` - cell value

      Returns:
      a GeorColormap entry indexed by the given value.

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

- [Prev Class](GeoRasterException.md)
- [Next Class](GeorColormapEntry.md)

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
