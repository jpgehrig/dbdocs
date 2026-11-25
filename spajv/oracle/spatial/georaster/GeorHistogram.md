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

- [Prev Class](GeorGrayscaleEntry.md)
- [Next Class](GeorHistogramEntry.md)

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

## Class GeorHistogram

- java.lang.Object

- - oracle.spatial.georaster.GeorHistogram

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorHistogram
      extends java.lang.Object

  GeorHistogram class is combined with class GeorHistogramEntry to represent a GeoRaster histogram, which contains an array of GeorHistogramEntry instances, and each GeorHistogramEntry contains a pair of cell value and count value.
  Two constructors are provided: one is the default constructor without parameters, and the other constructor allows you to specify length of GeorHistogramEntry array, in which case the constructor will create a GeorHistogramEntry array based on the length.

  In this class, methods are provided for retrieving and setting the GeorHistogramEntry array and each individual entry.

  The following two methods defined in the class SublayerInfo are used to retrieve and set histogram in the GeoRaster metadata through an instance of GeorHistogram:

           public GeorHistogram getHistogram();
           public void setHistogram(GeorHistogram histogram);


<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                       |
    |---------------------------------------------------------------------------------------------------|
    | `GeorHistogram``()`<br>Constructs a `GeorHistogram` object.                                       |
    | `GeorHistogram``(int length)`<br>Constructs a `GeorHistogram` object with the given array length. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                 |
    |---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `long[]`                                          | `getCounts``()`<br>Returns the counts array.                                                                                           |
    | [`GeorHistogramEntry`](GeorHistogramEntry.md)     | `getGeorHistogramEntry``(double value)`<br>Returns a GeorHistogramEntry entry indexed by a given value.                                |
    | [`GeorHistogramEntry`](GeorHistogramEntry.md)     | `getGeorHistogramEntry``(int entryNo)`<br>Returns a GeorHistogramEntry entry indexed by a given entry number.                          |
    | [`GeorHistogramEntry`](GeorHistogramEntry.md)`[]` | `getValueAndCount``()`<br>Returns the GeorHistogramEntry array.                                                                        |
    | `double[]`                                        | `getValues``()`<br>Returns the values array.                                                                                           |
    | `boolean`                                         | `setValueAndCount``(double[] value, long[] count)`<br>Sets the GeorHistogramEntry array by specifying two individual component arrays. |
    | `boolean`                                         | `setValueAndCount``(double value, int count)`<br>Sets a GeorHistogramEntry based on value.                                             |
    | `boolean`                                         | `setValueAndCount``(`[`GeorHistogramEntry`](GeorHistogramEntry.md)`[] entries)`<br>Sets the GeorHistogramEntry array.                  |
    | `boolean`                                         | `setValueAndCount``(int entryNo, double value, int count)`<br>Sets a GeorHistogramEntry based on entryNo.                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorHistogram

          public GeorHistogram()

      Constructs a `GeorHistogram` object.

    <!-- -->

    - #### GeorHistogram

          public GeorHistogram(int length)

      Constructs a `GeorHistogram` object with the given array length.
      Parameters:
      `length` - length of GeorHistogram array

  <!-- -->

  - ### Method Detail

    - #### getValueAndCount

          public GeorHistogramEntry[] getValueAndCount()

      Returns the GeorHistogramEntry array.
      Returns:
      GeorHistogramEntry array.

    <!-- -->

    - #### getValues

          public double[] getValues()

      Returns the values array.
      Returns:
      values array.

    <!-- -->

    - #### getCounts

          public long[] getCounts()

      Returns the counts array.
      Returns:
      counts array.

    <!-- -->

    - #### setValueAndCount

          public boolean setValueAndCount(double[] value,
                                          long[] count)

      Sets the GeorHistogramEntry array by specifying two individual component arrays. If the value array is not sorted in ascending order, then it will be sorted first.
      Parameters:
      `value` - cell value array

      `count` - count array

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setValueAndCount

          public boolean setValueAndCount(GeorHistogramEntry[] entries)

      Sets the GeorHistogramEntry array. If the value array is not sorted in ascending order, then it will be sorted first.
      Parameters:
      `entries` - GeorHistogramEntry array

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setValueAndCount

          public boolean setValueAndCount(int entryNo,
                                          double value,
                                          int count)

      Sets a GeorHistogramEntry based on entryNo.
      Parameters:
      `entryNo` - index of GeorHistogramEntry array, from 0 to (array length-1)

      `value` - cell value

      `count` - count value

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### setValueAndCount

          public boolean setValueAndCount(double value,
                                          int count)

      Sets a GeorHistogramEntry based on value.
      Parameters:
      `value` - cell value

      `count` - count value

      Returns:
      true or false to indicate if the set operation was successful.

    <!-- -->

    - #### getGeorHistogramEntry

          public GeorHistogramEntry getGeorHistogramEntry(int entryNo)

      Returns a GeorHistogramEntry entry indexed by a given entry number.
      Parameters:
      `entryNo` - entry number

      Returns:
      a GeorHistogram entry indexed by the given entry number.

    <!-- -->

    - #### getGeorHistogramEntry

          public GeorHistogramEntry getGeorHistogramEntry(double value)

      Returns a GeorHistogramEntry entry indexed by a given value.
      Parameters:
      `value` - cell value

      Returns:
      a GeorHistogram entry indexed by the given value.

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

- [Prev Class](GeorGrayscaleEntry.md)
- [Next Class](GeorHistogramEntry.md)

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
