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

- [Prev Class](GeorFunctionalFittingModel.md)
- [Next Class](GeorGrayscaleEntry.md)

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

## Class GeorGrayscale

- java.lang.Object

- - oracle.spatial.georaster.GeorGrayscale

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorGrayscale
      extends java.lang.Object

  GeorGrayscale class is combined with class GeorGrayscaleEntry to represent a GeoRaster grayscale, which contains an array of GeorGrayscaleEntry instances, and each GeorGrayscaleEntry contains a pair of cell value and gray value.
  Two constructors are provided: one is the default constructor without parameters, and the other constructor allows you to specify length of GeorGrayscaleEntry array, in which case the constructor will create a GeorGrayscaleEntry array based on the length.

  In this class, methods are provided for retrieving and setting the GeorGrayscaleEntry array and each individual entry.

  The following two methods defined in the class SublayerInfo are used to retrieve and set grayScale in the GeoRaster metadata through an instance of GeorGrayscale:

           public void setGrayscale(GeorGrayscale grayscale);
           public GeorGrayscale getGrayscale();


<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                       |
    |---------------------------------------------------------------------------------------------------|
    | `GeorGrayscale``()`<br>Constructs a `GeorGrayscale` object                                        |
    | `GeorGrayscale``(int length)`<br>Constructs a `GeorGrayscale` object with the given array length. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                          |
    |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | [`GeorGrayscaleEntry`](GeorGrayscaleEntry.md)     | `getGeorGrayscaleEntry``(double value)`<br>Returns a GeorGrayscaleEntry entry indexed by a given value.                         |
    | [`GeorGrayscaleEntry`](GeorGrayscaleEntry.md)     | `getGeorGrayscaleEntry``(int entryNo)`<br>Returns a GeorGrayscaleEntry entry indexed by a given entry number.                   |
    | [`GeorGrayscaleEntry`](GeorGrayscaleEntry.md)`[]` | `getGrayscale``()`<br>Returns the GeorGrayscaleEntry array.                                                                     |
    | `boolean`                                         | `setGrayscale``(double[] value, int[] gray)`<br>Sets the GeorColormapEntry array by specifying two individual component arrays. |
    | `boolean`                                         | `setGrayscale``(double value, int gray)`<br>Sets a GeorGrayscaleEntry based on value.                                           |
    | `boolean`                                         | `setGrayscale``(`[`GeorGrayscaleEntry`](GeorGrayscaleEntry.md)`[] entries)`<br>Sets the GeorGrayscaleEntry array.               |
    | `boolean`                                         | `setGrayscale``(int entryNo, double value, int gray)`<br>Sets a GeorColormapEntry based on entryNo.                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorGrayscale

          public GeorGrayscale()

      Constructs a `GeorGrayscale` object

    <!-- -->

    - #### GeorGrayscale

          public GeorGrayscale(int length)

      Constructs a `GeorGrayscale` object with the given array length.
      Parameters:
      `length` - length of GeorGrayscale array

  <!-- -->

  - ### Method Detail

    - #### getGrayscale

          public GeorGrayscaleEntry[] getGrayscale()

      Returns the GeorGrayscaleEntry array.
      Returns:
      GeorGrayscaleEntry array.

    <!-- -->

    - #### setGrayscale

          public boolean setGrayscale(double[] value,
                                      int[] gray)

      Sets the GeorColormapEntry array by specifying two individual component arrays. if the value array is not sorted in ascending order, then it will be sorted first.
      Parameters:
      `value` - cell value array

      `gray` - gray component array

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setGrayscale

          public boolean setGrayscale(GeorGrayscaleEntry[] entries)

      Sets the GeorGrayscaleEntry array. If the value array is not sorted in ascending order, then it will be sorted first.
      Parameters:
      `entries` - GeorGrayscaleEntry array

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setGrayscale

          public boolean setGrayscale(int entryNo,
                                      double value,
                                      int gray)

      Sets a GeorColormapEntry based on entryNo.
      Parameters:
      `entryNo` - index of GeorGrayscaleEntry array, from 0 to (array length-1)

      `value` - cell value

      `gray` - gray component

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setGrayscale

          public boolean setGrayscale(double value,
                                      int gray)

      Sets a GeorGrayscaleEntry based on value.
      Parameters:
      `value` - cell value

      `gray` - gray color component

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### getGeorGrayscaleEntry

          public GeorGrayscaleEntry getGeorGrayscaleEntry(int entryNo)

      Returns a GeorGrayscaleEntry entry indexed by a given entry number.
      Parameters:
      `entryNo` - entry number

      Returns:
      a GeorGrayscale entry indexed by the given entry number.

    <!-- -->

    - #### getGeorGrayscaleEntry

          public GeorGrayscaleEntry getGeorGrayscaleEntry(double value)

      Returns a GeorGrayscaleEntry entry indexed by a given value.
      Parameters:
      `value` - cell value

      Returns:
      a GeorGrayscale entry indexed by the given value.

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

- [Prev Class](GeorFunctionalFittingModel.md)
- [Next Class](GeorGrayscaleEntry.md)

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
